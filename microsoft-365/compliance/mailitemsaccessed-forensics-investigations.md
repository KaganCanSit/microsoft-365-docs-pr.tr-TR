---
title: Risk altındaki hesapları araştırmak için Denetimi (Premium) kullanın
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Güvenliği aşılmış kullanıcı hesaplarının adli araştırmalarını gerçekleştirmek için MailItemsAccessed posta kutusu denetim eylemini kullanın.
ms.openlocfilehash: 2256e331075074348e2a72d6528bed1944567b94
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64996206"
---
# <a name="use-microsoft-purview-audit-premium-to-investigate-compromised-accounts"></a>Güvenliği aşılmış hesapları araştırmak için Microsoft Purview Denetimi'ni (Premium) kullanma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Güvenliği aşılmış kullanıcı hesabı ( *hesap devralma* olarak da adlandırılır), bir saldırganın bir kullanıcı hesabına erişim kazanması ve kullanıcı olarak çalışması bir saldırı türüdür. Bu tür saldırılar bazen saldırganın hedefleyenden daha fazla hasara neden olur. Güvenliği aşılmış e-posta hesaplarını araştırırken, saldırganın gerçek iletişim durumunu izleyerek belirtilebilenden daha fazla posta verisinin gizliliğinin ihlal edildiği varsayılmalıdır. E-posta iletilerindeki verilerin türüne bağlı olarak, hassas bilgilerin açığa çıkmadığını kanıtlayamadığınız sürece hassas bilgilerin gizliliğinin ihlal edildiği veya yasal düzenleme cezalarıyla karşı karşıya kalındığını varsaymanız gerekir. Örneğin HIPAA tarafından düzenlenen kuruluşlar, hasta sağlığı bilgilerinin (PHI) açığa çıkarıldığına dair kanıt varsa önemli para cezalarıyla karşı karşıya kalır. Bu gibi durumlarda saldırganların PHI ile ilgilenme olasılığı düşüktür ancak aksini kanıtlayamadığı sürece kuruluşların yine de veri ihlallerini bildirmesi gerekir.

Güvenliği aşılmış e-posta hesaplarını araştırmanıza yardımcı olmak için posta protokolleri ve *mailItemsAccessed* posta kutusu denetimi eylemiyle istemciler tarafından posta verilerinin erişimlerini denetleyeceğiz. Bu yeni denetlenen eylem, araştırmacıların e-posta veri ihlallerini daha iyi anlamasına yardımcı olur ve gizliliği tehlikeye girmiş olabilecek belirli posta öğelerine yönelik güvenlik ihlallerinin kapsamını belirlemenize yardımcı olur. Bu yeni denetim eylemini kullanmanın amacı, belirli bir posta verisi parçasının gizliliğinin tehlikeye atılmadığını onaylamaya yardımcı olmak için adli incelemenin güvenilirliğidir. Bir saldırgan belirli bir posta parçasına erişim elde ettiyse, Exchange Online posta öğesinin okunduğuna dair bir gösterge olmasa bile olayı denetler.

## <a name="the-mailitemsaccessed-mailbox-auditing-action"></a>MailItemsAccessed posta kutusu denetimi eylemi

Yeni MailItemsAccessed eylemi, yeni [Denetim (Premium)](advanced-audit.md) işlevinin bir parçasıdır. [Exchange posta kutusu denetiminin](/office365/securitycompliance/enable-mailbox-auditing#mailbox-auditing-actions) bir parçasıdır ve Office 365 veya Microsoft 365 E5 lisansı atanmış kullanıcılar ya da Microsoft 365 E5 Uyumluluk eklenti aboneliği olan kuruluşlar için varsayılan olarak etkinleştirilir.

MailItemsAccessed posta kutusu denetimi eylemi tüm posta protokollerini kapsar: POP, IMAP, MAPI, EWS, Exchange ActiveSync ve REST. Ayrıca, postaya erişmenin her iki türünü de kapsar: *eşitleme* ve *bağlama*.

### <a name="auditing-sync-access"></a>Eşitleme erişimini denetleme

Eşitleme işlemleri yalnızca posta kutusuna Windows veya Mac için Outlook istemcisinin masaüstü sürümü tarafından erişildiğinde kaydedilir. Eşitleme işlemi sırasında bu istemciler genellikle buluttan yerel bir bilgisayara büyük bir posta öğeleri kümesi indirir. Eşitleme işlemleri için denetim hacmi çok büyük. Bu nedenle, eşitlenen her posta öğesi için bir denetim kaydı oluşturmak yerine, eşitlenmiş öğeleri içeren posta klasörü için bir denetim olayı oluşturur ve eşitlenen klasördeki *tüm* posta öğelerinin güvenliğinin aşıldığını varsayarız. Erişim türü, denetim kaydının OperationProperties alanına kaydedilir.

Eşitleme erişim türünü bir denetim kaydında görüntüleme örneği [için, MailItemsAccessed audit records for forensic investigations](#use-mailitemsaccessed-audit-records-for-forensic-investigations) bölümündeki 2. adıma bakın.

### <a name="auditing-bind-access"></a>Bağlama erişimini denetleme

Bağlama işlemi, e-posta iletisine tek tek erişimdir. Bağlama erişimi için, tek tek iletilerin InternetMessageId değeri denetim kaydına kaydedilir. MailItemsAccessed denetim eylemi, bağlama işlemlerini kaydeder ve ardından tek bir denetim kaydında toplanır. 2 dakikalık bir aralık içinde gerçekleşen tüm bağlama işlemleri, AuditData özelliğindeki Klasörler alanındaki tek bir denetim kaydında toplanır. Erişilen her ileti kendi InternetMessageId değeriyle tanımlanır. Kayıtta toplanan bağlama işlemlerinin sayısı, AuditData özelliğinin OperationCount alanında görüntülenir.

Bağlama erişim türünü bir denetim kaydında görüntüleme örneği [için, MailItemsAccessed audit records for forensic investigations](#use-mailitemsaccessed-audit-records-for-forensic-investigations) bölümündeki 4. adıma bakın.

### <a name="throttling-of-mailitemsaccessed-audit-records"></a>MailItemsAccessed denetim kayıtlarının azaltması

24 saatten kısa bir süre içinde 1.000'den fazla MailItemsAccessed denetim kaydı oluşturulursa, Exchange Online MailItemsAccessed etkinliği için denetim kayıtlarının oluşturulmasını durdurur. Posta kutusu kısıtlandığında MailItemsAccessed etkinliği, posta kutusu kısıtlandıktan sonra 24 saat boyunca günlüğe kaydedilmez. Posta kutusu kısıtlandıysa, bu süre boyunca posta kutusunun güvenliği aşılmış olabilir. MailItemsAccessed etkinliğinin kaydı 24 saatlik bir süre sonra sürdürülür.

Azaltma hakkında göz önünde bulundurmanız gereken birkaç şey şunlardır:

- Exchange Online içindeki tüm posta kutularının %1'inden azı kısıtlandı
- Posta kutusu azaltıldığında, yalnızca MailItemsAccessed etkinliği için denetim kayıtları denetlenmiyor. Diğer posta kutusu denetim eylemleri etkilenmez.
- Posta kutuları yalnızca Bağlama işlemleri için kısıtlanmıştır. Eşitleme işlemleri için denetim kayıtları kısıtlanmaz.
- Bir posta kutusu kısıtlanırsa, büyük olasılıkla denetim günlüklerine kaydedilmemiş MailItemsAccessed etkinliği olduğunu varsayabilirsiniz.

Bir denetim kaydında IsThrottled özelliğini görüntüleme örneği [için, Adli araştırmalar için MailItemsAccessed denetim kayıtlarını kullanma](#use-mailitemsaccessed-audit-records-for-forensic-investigations) bölümündeki 1. adıma bakın.

## <a name="use-mailitemsaccessed-audit-records-for-forensic-investigations"></a>Adli araştırmalar için MailItemsAccessed denetim kayıtlarını kullanma

Posta kutusu denetimi, e-posta iletilerinin gizliliğinin ihlal edilmediğinden emin olabilmeniz için e-posta iletilerine erişim için denetim kayıtları oluşturur. Bu nedenle, bazı verilere erişildiğinden emin olmadığımız durumlarda, tüm posta erişim etkinliklerini kaydederek olduğunu varsayarız.

MailItemsAccessed denetim kayıtlarının adli amaçlarla kullanılması genellikle bir veri ihlali çözüldükten ve saldırgan çıkarıldıktan sonra gerçekleştirilir. Araştırmanıza başlamak için ele geçirilen posta kutuları kümesini belirlemeniz ve saldırganın kuruluşunuzdaki posta kutularına ne zaman eriştiğine ilişkin zaman dilimini belirlemeniz gerekir. Ardından, veri ihlaline karşılık gelen denetim kayıtlarında arama yapmak için [Exchange Online PowerShell'deki](/powershell/exchange/connect-to-exchange-online-powershell) **Search-UnifiedAuditLog** veya **Search-MailboxAuditLog** cmdlet'lerini kullanabilirsiniz.

MailItemsAccessed denetim kayıtlarını aramak için aşağıdaki komutlardan birini çalıştırabilirsiniz:

**Birleşik denetim günlüğü**:

```powershell
Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000
```

**Posta kutusu denetim günlüğü**:

```powershell
Search-MailboxAuditLog -Identity <user> -StartDate 01/06/2020 -EndDate 01/20/2020 -Operations MailItemsAccessed -ResultSize 1000 -ShowDetails
```

> [!TIP]
> Bu iki cmdlet arasındaki birincil farklardan biri, bir veya daha fazla kullanıcı tarafından gerçekleştirilen etkinliğin denetim kayıtlarını aramak için **Search-UnifiedAuditLog** cmdlet'ini kullanabilmenizdir. Bunun nedeni *UserIds'in* çok değerli bir parametre olmasıdır. **Search-MailboxAuditLog** cmdlet'i, posta kutusu denetim günlüğünde tek bir kullanıcı arar.

Güvenliği aşılmış bir kullanıcı saldırısını araştırmak için MailItemsAccessed denetim kayıtlarını kullanma adımları aşağıdadır. Her adım **Search-UnifiedAuditLog** veya **Search-MailboxAuditLog** cmdlet'leri için komut söz dizimini gösterir.

1. Posta kutusunun kısıtlanıp kısıtlanmamış olduğunu denetleyin. Bu durumda, bu bazı posta kutusu denetim kayıtlarının günlüğe kaydedilmeyeceği anlamına gelir. Herhangi bir denetim kaydının "IsThrottled" değeri "True" olduğunda, bu kaydın oluşturulmasından sonra 24 saatlik bir süre boyunca posta kutusuna erişimin denetlenmediğini ve tüm posta verilerinin gizliliğinin ihlal edildiğini varsaymalısınız.

   Posta kutusunun kısıtlandığı MailItemsAccessed kayıtlarını aramak için aşağıdaki komutu çalıştırın:

   **Birleşik denetim günlüğü**:

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"IsThrottled","Value":"True"*'} | FL
   ```

   **Posta kutusu denetim günlüğü**:

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*IsThrottled:True*"} | FL
   ```

2. Eşitleme etkinliklerini denetleyin. Bir saldırgan, posta kutusuna ileti yüklemek için e-posta istemcisi kullanıyorsa, bilgisayarın İnternet bağlantısını kesebilir ve sunucuyla etkileşim kurmadan iletilere yerel olarak erişebilir. Bu durumda, posta kutusu denetimi bu etkinlikleri denetleyemez.

   Posta öğelerine bir eşitleme işlemi tarafından erişilen MailItemsAccessed kayıtlarını aramak için aşağıdaki komutu çalıştırın:

   **Birleşik denetim günlüğü**:

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 02/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"MailAccessType","Value":"Sync"*'} | FL
   ```

   **Posta kutusu denetim günlüğü**:

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*MailAccessType:Sync*"} | FL
   ```

3. Eşitleme etkinliklerinden herhangi birinde saldırganın posta kutusuna eriştiğiyle aynı bağlamda gerçekleştiğini belirlemek için eşitleme etkinliklerini denetleyin. Bağlam, posta kutusuna ve posta protokolüne erişmek için kullanılan istemci bilgisayarın IP adresiyle tanımlanır ve ayırt edilir. Daha fazla bilgi için [Farklı denetim kayıtlarının erişim bağlamlarını tanımlama](#identifying-the-access-contexts-of-different-audit-records) bölümüne bakın.

   Araştırmak için aşağıda listelenen özellikleri kullanın. Bu özellikler AuditData veya OperationProperties özelliğinde bulunur. Eşitlemelerden herhangi biri saldırgan etkinliğiyle aynı bağlamda gerçekleşirse, saldırganın tüm posta öğelerini istemcileriyle eşitlediğini varsayalım; bu da büyük olasılıkla posta kutusunun tamamının gizliliğinin ihlal edildiği anlamına gelir.

   <br>

   ****

   |Özellik|Açıklama|
   |---|---|
   |ClientInfoString|Protokolü, istemciyi (sürümü içerir) açıklar|
   |ClientIPAddress|İstemci makinesinin IP adresi.|
   |Sessionıd|Oturum Kimliği, saldırgan eylemlerini aynı hesapta günlük kullanıcı etkinlikleriyle ayırt etmeye yardımcı olur (güvenliği aşılmış hesaplar için kullanışlıdır)|
   |Userıd|İletiyi okuyan kullanıcının UPN'i.|
   |

4. Bağlama etkinliklerini denetleyin. 2. ve 3. adım adımlarını gerçekleştirdikten sonra, saldırganın e-posta iletilerine diğer tüm erişiminin, "Bind" değerine sahip bir MailAccessType özelliğine sahip MailItemsAccessed denetim kayıtlarında yakalanacağından emin olabilirsiniz.

   Posta öğelerine bağlama işlemi tarafından erişilen MailItemsAccessed kayıtlarını aramak için aşağıdaki komutu çalıştırın.

   **Birleşik denetim günlüğü**:

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"MailAccessType","Value":"Bind"*'} | FL
   ```

   **Posta kutusu denetim günlüğü**:

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*MailAccessType:Bind*"} | FL
   ```

   Erişilen e-posta iletileri, internet ileti kimlikleriyle tanımlanır. Ayrıca herhangi bir denetim kaydının diğer saldırgan etkinlikleriyle aynı bağlama sahip olup olmadığını denetleyebilirsiniz. Daha fazla bilgi için [Farklı denetim kayıtlarının erişim bağlamlarını tanımlama](#identifying-the-access-contexts-of-different-audit-records) bölümüne bakın.

   Bağlama işlemleri için denetim verilerini iki farklı yolla kullanabilirsiniz:

   - Saldırgana internetmessageid kullanarak erişilen tüm e-posta iletilerine erişin veya bunları bulun ve ardından bu iletilerden herhangi birinin hassas bilgiler içerip içermediğini denetleyin.
   - Hassas olabilecek bir dizi e-posta iletisiyle ilgili denetim kayıtlarını aramak için InternetMessageId'yi kullanın. Yalnızca birkaç iletiyle ilgileniyorsanız bu yararlı olur.

## <a name="filtering-of-duplicate-audit-records"></a>Yinelenen denetim kayıtlarını filtreleme

Bir saat içinde gerçekleşen aynı bağlama işlemleri için yinelenen denetim kayıtları, denetim gürültüsünü gidermek için filtrelenir. Eşitleme işlemleri de bir saatlik aralıklarla filtrelenir. Bu yinelenenleri kaldırma işleminin istisnası, aynı InternetMessageId için aşağıdaki tabloda açıklanan özelliklerden herhangi biri farklıysa oluşur. Bu özelliklerden biri yinelenen bir işlemde farklıysa yeni bir denetim kaydı oluşturulur. Bu işlem sonraki bölümde daha ayrıntılı olarak açıklanmıştır.

<br>

****

|Özellik|Açıklama|
|---|---|
|ClientIPAddress|İstemci bilgisayarın IP adresi.|
|ClientInfoString|İstemci protokolü, posta kutusuna erişmek için kullanılan istemci.|
|ParentFolder|Erişilen posta öğesinin tam klasör yolu.|
|Logon_type|Eylemi gerçekleştiren kullanıcının oturum açma türü. Oturum açma türleri (ve karşılık gelen Enum değerleri) Sahip (0), Yönetici (1) veya Temsilci (2) olur.|
|MailAccessType|Erişimin bir bağlama veya eşitleme işlemi olup olmadığı.|
|Posta KutusuUPN|Okunan iletinin bulunduğu posta kutusunun UPN'i.|
|Kullanıcı|İletiyi okuyan kullanıcının UPN'i.|
|Sessionıd|Oturum Kimliği, aynı posta kutusunda saldırgan eylemlerini ve günlük kullanıcı etkinliklerini ayırt etmeye yardımcı olur (hesap güvenliğinin aşılmasına neden olur) Oturumlar hakkında daha fazla bilgi için bkz. [Exchange Online oturumlar içinde saldırgan etkinliğini bağlamsallaştırma](https://techcommunity.microsoft.com/t5/exchange-team-blog/contextualizing-attacker-activity-within-sessions-in-exchange/ba-p/608801).|
|

## <a name="identifying-the-access-contexts-of-different-audit-records"></a>Farklı denetim kayıtlarının erişim bağlamlarını tanımlama

Bir saldırganın posta kutusuna, posta kutusu sahibinin eriştiği aynı anda erişmesi yaygın bir durumdur. Saldırgan ile posta kutusu sahibi arasındaki erişimi ayırt etmek için, erişimin bağlamını tanımlayan denetim kaydı özellikleri vardır. Daha önce açıklandığı gibi, bu özelliklerin değerleri farklı olduğunda, etkinlik toplama aralığında gerçekleştiğinde bile ayrı denetim kayıtları oluşturulur. Aşağıdaki örnekte üç farklı denetim kaydı vardır. Her biri Oturum Kimliği ve ClientIPAddress özelliklerine göre ayırt edilir. Erişilen iletiler de tanımlanır.

<br>

****

|Denetim kaydı 1|Denetim kaydı 2|Denetim kaydı 3|
|---|---|---|
|ClientIPAddress1<br/>**SessionId2**|ClientIPAddress2<br/>**SessionId2**|ClientIPAddress1<br/>**SessionId3**|
|**InternetMessageIdA**<br/>**InternetMessageIdD**<br/>**InternetMessageIdE**<br/>**InternetMessageIdF**<br/>|**InternetMessageIdA**<br/>**InternetMessageIdC**|**InternetMessageIdB**|
|

[Önceki bölümde](#filtering-of-duplicate-audit-records) tabloda listelenen özelliklerden herhangi biri farklıysa, yeni bağlamı izlemek için ayrı bir denetim kaydı oluşturulur. Erişimler, etkinliğin gerçekleştiği bağlama bağlı olarak ayrı denetim kayıtlarına sıralanır.

Örneğin, aşağıdaki ekran görüntüsünde gösterilen denetim kayıtlarında, aynı anda EWSEditor ve OWA'dan gelen postalara erişiyor olsak da, erişim etkinliği, erişimin gerçekleştiği bağlama bağlı olarak farklı denetim kayıtlarında harmanlanır. Bu durumda, bağlam ClientInfoString özelliği için farklı değerler tarafından tanımlanır.

![Bağlama göre farklı denetim kayıtları.](../media/MailItemsAccessed4.png)

Önceki ekran görüntüsünde gösterilen komutun söz dizimi aşağıdadır:

```powershell
Search-MailboxAuditLog -Identity admin -ShowDetails -Operations MailItemsAccessed -ResultSize 2000 | Select LastAccessed,Operation,AuditOperationsCountInAggregatedRecord,ClientInfoString
```
