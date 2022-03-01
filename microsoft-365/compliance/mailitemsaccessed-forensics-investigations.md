---
title: Güvenliği ihlal edilmiş hesapları araştırmak için Gelişmiş Denetim'i kullanma
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
description: Güvenliği ihlal edilmiş kullanıcı hesapları üzerinde araştırma yapmak için MailItemsAccessed posta kutusu denetim eylemlerini kullanın.
ms.openlocfilehash: 8bfba164bf3bfb0f4fa4bea687d0fe040cff4836
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019474"
---
# <a name="use-advanced-audit-to-investigate-compromised-accounts"></a>Güvenliği ihlal edilmiş hesapları araştırmak için Gelişmiş Denetim'i kullanma

Güvenliği tehlikeye atılmış bir kullanıcı hesabı (hesap ele alma olarak da *adlandırılan), bir* saldırgan bir kullanıcı hesabına erişim kazanır ve kullanıcı olarak çalışırsa saldırıya bir tür saldırıdır. Bu tür saldırılar bazen saldırgan hedeflenenden daha fazla hasara neden olur. Güvenliği tehlikeye atılmış e-posta hesaplarını incelerken, saldırganın gerçek iletişim durumu izleniyorsa, güvenliğin ihlal edilmiş olduğunu varsayın. E-posta iletilerinde verilerin türüne bağlı olarak, hassas bilgilerin açığa çıkar olmadığını kanıtlamak için hassas bilgilerin tehlikeye atılmış olduğunu veya mevzuatla ilgili hukuki düzenlemelere tabi olduğunu varsayabilirsiniz. Örneğin, HIPAA'ya göre düzenlemeye tabi kuruluşlar hasta durumu bilgisinin (PHI) ortaya çıkar olduğuna dair kanıt varsa önemli ince bilgilerle karşı karşıya olur. Bu gibi durumlarda, saldırganların PHI ile ilgilenmesi pek mümkün değildir, ancak kuruluşlar aksini kanıtlamak zorunda olmadıkça yine de veri ihlallerini bildirmeleri gerekir.

Güvenliğin tehlikeye e-posta hesaplarını araştırmanıza yardımcı olmak için, artık *MailItemsAccessed* posta kutusu denetim eylemiyle posta protokolleri ve istemciler yoluyla posta verileri erişimlerini denetlemektedir. Bu yeni denetimli eylem, e-posta veri ihlallerini daha iyi anlamanıza ve güvenliğin tehlikeye atılmış olduğu belirli posta öğeleri için güvenlik ihlallerinin kapsamını belirlemeye yardımcı olacaktır. Bu yeni denetim eylemlerini kullanmanın amacı, belirli bir posta veri parçasının ihlal olmadığını onaylamaya yardımcı olmak için ihlallere karşıtlıktır. Bir saldırgan belirli bir posta parçasına erişim kazandısa, Exchange Online öğenin okundu olduğuna dair bir gösterge yoktur ancak bu olayı denetimler.

## <a name="the-mailitemsaccessed-mailbox-auditing-action"></a>MailItemsAccessed posta kutusu denetim eylemi

Yeni MailItemsAccessed eylemi, yeni Gelişmiş Denetim [işlevinin bir](advanced-audit.md) parçasıdır. [Bu, Exchange posta](/office365/securitycompliance/enable-mailbox-auditing#mailbox-auditing-actions) kutusu denetiminin bir bölümüdür ve Office 365 veya Microsoft 365 E5 lisansı atanan kullanıcılar için ya da Microsoft 365 E5 Uyumluluk eklenti aboneliği olan kuruluşlar için varsayılan olarak etkinleştirilir.

MailItemsAccessed posta kutusu denetim eylemi tüm posta protokollerini kapsar: POP, IMAP, MAPI, EWS, Exchange ActiveSync REST. Ayrıca postaya erişim her iki türü de kapsar: *eşitleme* ve *bağlama*.

### <a name="auditing-sync-access"></a>Eşitleme erişimini denetleme

Eşitleme işlemleri yalnızca posta kutusuna Mac veya Mac için Outlook istemcisinin masaüstü sürümü tarafından Windows kaydedilir. Eşitleme işlemi sırasında, bu istemciler genellikle buluttan büyük bir posta öğeleri kümesi yerel bilgisayara indirir. Eşitleme işlemleri için denetim hacmi çok büyük. Eşitlenen her posta öğesi için bir denetim kaydı oluşturmak yerine, eşitlenen öğelerin bulunduğu posta klasörü için bir denetim olayı oluşturur ve eşitlenen klasördeki tüm posta öğelerinin tehlikeye atılmış olduğunu varsayalım. Erişim türü denetim kaydının OperationProperties alanına kaydedilir.

Bir denetim kaydında eşitleme erişim türünü görüntüleme örneği için, Araştırma araştırmalarına ilişkin [MailItemsAccessed](#use-mailitemsaccessed-audit-records-for-forensic-investigations) denetim kayıtlarını kullanma bölümündeki 2. adıma bakın.

### <a name="auditing-bind-access"></a>Bağlama erişimini denetleme

Bağlama işlemi, e-posta iletisine tek tek erişimdir. Bağlama erişimi için, tek tek iletilerin InternetMessageId'i denetim kaydına kaydedilir. MailItemsAccessed denetim eylemi kayıtları işlemleri bağlar ve sonra tek bir denetim kaydında bir araya gönderir. 2 dakikalık bir aralıkta oluşan tüm bağlama işlemleri, AuditData özelliği içindeki Klasörler alanında tek bir denetim kaydında toplanır. Erişilen her ileti InternetMessageId tarafından tanımlanır. Kayıtta toplanan bağlama işlemlerinin sayısı DenetimVerileri özelliğinin OperationCount alanında görüntülenir.

Bir denetim kaydında bağlama erişim türünü görüntüleme örneği için, Araştırma araştırmalarında araştırmalara ilişkin [MailItemsAccessed](#use-mailitemsaccessed-audit-records-for-forensic-investigations) denetim kayıtlarını kullanma bölümündeki 4. adıma bakın.

### <a name="throttling-of-mailitemsaccessed-audit-records"></a>MailItemsAccessed denetim kayıtlarını azaltma

1.000'den fazla MailItemsAccessed denetim kaydı 24 saatten kısa sürede oluşturulursa, Exchange Online MailItemsAccessed etkinliği için denetim kayıtları oluşturmayacaktır. Posta kutusu kısıtlanmazsa, posta kutusu kısıtlandıktan sonra MailItemsAccessed etkinliği 24 saat süreyle günlüğe kaydedilmez. Posta kutusu kısıtlandı ise, bu süre boyunca posta kutusunun güvenliği ihlal edilmiş olabilir. MailItemsAccessed etkinliğinin kaydı, 24 saatlik bir süre sonra sürdürülecek.

İşte azaltma hakkında gözlerde tutmamız gereken birkaç şey:

- E-posta Exchange Online posta kutularının %1'inden daha az azaltma
- Posta kutusu azaltma olduğunda, MailItemsAccessed etkinliğinin yalnızca denetim kayıtları denetlenz. Diğer posta kutusu denetim eylemleri etkilenmez.
- Posta kutuları yalnızca Bağlama işlemleri için kısıtlandı. Eşitleme işlemlerinin denetim kayıtları kısıtlanmaz.
- Bir posta kutusu kısıtlandı ise, büyük olasılıkla denetim günlüklerine kaydedilemeyen MailItemsAccessed etkinliği olduğunu varsayabilirsiniz.

Bir denetim kaydında IsThrottled özelliğini görüntüleme örneği için, Araştırma araştırmalarında [MailItemsAccessed](#use-mailitemsaccessed-audit-records-for-forensic-investigations) denetim kayıtlarını kullanma bölümündeki 1. adıma bakın.

## <a name="use-mailitemsaccessed-audit-records-for-forensic-investigations"></a>Araştırma araştırmalarında MailItemsAccessed denetim kayıtlarını kullanma

Posta kutusu denetimi, e-posta iletilerine erişim için denetim kayıtları üretir ve böylelikle e-posta iletilerinin güvenliği ihlal edilmiş bile olabilir. Bu nedenle, bazı verilere erişilen durumlarda, tüm posta erişimi etkinliğini kaydederek bu verilere erişilemedik varsayıldı.

Ihlaller için MailItemsAccessed denetim kayıtları genellikle bir veri ihlali çözülmüş ve saldırgan çıkarıldığı zaman gerçekleştirilir. Araştırmanıza başlamak için ele geçirildikleri posta kutularını belirlemeli ve saldırganların organizasyonu posta kutularına erişimleri olduğunda zaman dilimini belirlemelisiniz. Ardından, [Exchange Online PowerShell'de](/powershell/exchange/connect-to-exchange-online-powershell) **Search-UnifiedAuditLog** veya **Search-MailboxAuditLog** cmdlet'lerini kullanarak veri ihlaline karşılık gelen denetim kayıtlarını arayabilirsiniz.

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
> Bu iki cmdlet arasındaki, bir veya birden çok kullanıcı tarafından gerçekleştirilen etkinliklere yönelik denetim kayıtlarını aramak için **Search-UnifiedAuditLog** cmdlet'ini kullanabileceğiniz en önemli fark. Bunun nedeni, *UserIds'nin* çok değerli bir parametredir. **Search-MailboxAuditLog** cmdlet'i, posta kutusu denetim günlüğünde tek bir kullanıcı arar.

Güvenliği ihlal edilmiş kullanıcı saldırılarını araştırmak için MailItemsAccessed denetim kayıtlarını kullanma adımları şu şekildedir. Her adım, **Search-UnifiedAuditLog** veya **Search-MailboxAuditLog** cmdlet'leri için komut söz dizimi gösterir.

1. Posta kutusunun kısıtsız olup olmadığını kontrol edin. Bu durumda, bu bazı posta kutusu denetim kayıtlarının günlüğe kaydedilene anlamına geliyor. Denetim kayıtlarında "IsThrottled" olması durumunda, kayıt oluşturulurken 24 saatlik bir süre için bu kaydın denetlen olmadığını ve tüm posta verilerine erişimin ihlal edilmiş olduğunu varsayın.

   Posta kutusunun kısıtlandı olduğu MailItemsAccessed kayıtlarını aramak için aşağıdaki komutu çalıştırın:

   **Birleşik denetim günlüğü**:

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"IsThrottled","Value":"True"*'} | FL
   ```

   **Posta kutusu denetim günlüğü**:

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*IsThrottled:True*"} | FL
   ```

2. Eşitleme etkinliklerini denetleme. Bir saldırgan bir e-posta istemcisi kullanarak iletileri bir posta kutusuna indirdiyse, sunucunun İnternet bağlantısını keserek ve sunucuyla etkileşim kurmadan iletilere yerel olarak erişim sağlar. Bu durumda, posta kutusu denetimi bu etkinlikleri denetlemez.

   Eşitleme işlemiyle posta öğelerine erişilen MailItemsAccessed kayıtlarını aramak için aşağıdaki komutu çalıştırın:

   **Birleşik denetim günlüğü**:

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 02/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"MailAccessType","Value":"Sync"*'} | FL
   ```

   **Posta kutusu denetim günlüğü**:

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*MailAccessType:Sync*"} | FL
   ```

3. Eşitleme etkinliklerinden herhangi birinin, saldırgan tarafından posta kutusuna erişen etkinlikle aynı bağlamda olup olmadığını belirlemek için kontrol edin. Bağlam, posta kutusuna ve posta protokolüne erişmek için kullanılan istemci bilgisayarın IP adresiyle tanımlanır ve farklı kullanılır. Daha fazla bilgi için Farklı [denetim kayıtlarının erişim bağlamlarını tanımlama bölümüne](#identifying-the-access-contexts-of-different-audit-records) bakın.

   Araştırma yapmak için aşağıda listelenen özellikleri kullanın. Bu özellikler AuditData veya OperationProperties özelliğinde yer almaktadır. Eşitlemelerden herhangi biri etkinlik etkinliğiyle aynı bağlamda gerçekleşirse, saldırganin tüm posta öğelerini istemcilerine eşitle olduğunu ve bu da büyük olasılıkla posta kutusunun tamamının ele geçirildi anlamına geldiğini varsayalım.

   <br>

   ****

   |Özellik|Açıklama|
   |---|---|
   |ClientInfoString|İstemci (sürüm içerir) protokolünü açıklar|
   |ClientIPAddress|İstemci makinenin IP adresi.|
   |SessionId|Oturum Kimliği aynı hesapta günlük kullanıcı etkinlikleriyle günlük eylemlerini ayırt etmek için yardımcı olur (güvenliği tehlikeye atılmış hesaplar için yararlıdır)|
   |UserId|İletiyi okuyan kullanıcının UPN'si.|
   |

4. Bağlama etkinliklerini denetleme. 2. ve 3. adımları gerçekleştirdikten sonra, saldırgan tarafından gönderilen e-posta iletilerine diğer tüm erişimin MailAccessType özelliği "Bind" olan MailAccessType özelliğine sahip MailItemsAccessed denetim kayıtlarında yakalanmasına güvenebilirsiniz.

   Posta öğelerine Bir Bağlama işlemiyle erişilen MailItemsAccessed kayıtlarını aramak için aşağıdaki komutu çalıştırın.

   **Birleşik denetim günlüğü**:

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"MailAccessType","Value":"Bind"*'} | FL
   ```

   **Posta kutusu denetim günlüğü**:

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*MailAccessType:Bind*"} | FL
   ```

   Erişilen e-posta iletileri, İnternet ileti kimlikleriyle tanımlanır. Ayrıca, herhangi bir denetim kayıtlarının diğer saldırgan etkinlikleriyle aynı bağlama sahip olup denetlemeyi de sabilirsiniz. Daha fazla bilgi için Farklı [denetim kayıtlarının erişim bağlamlarını tanımlama bölümüne](#identifying-the-access-contexts-of-different-audit-records) bakın.

   Bağlama işlemleri için denetim verilerini iki farklı şekilde kullanabilirsiniz:

   - Saldırgan tarafından erişilen tüm e-posta iletilerine, bunları bulmak için InternetMessageId kullanarak erişilen ve sonra bu iletilerden herhangi biri hassas bilgi içerdiğini kontrol ederek erişin veya iletileri toplayın.
   - InternetMessageId'i kullanarak, hassas olabilecek bir dizi e-posta iletiyle ilgili denetim kayıtlarını arayabilirsiniz. Yalnızca birkaç iletiyle ilgili endişeleniyorsanız, bu yararlı olur.

## <a name="filtering-of-duplicate-audit-records"></a>Yinelenen denetim kayıtlarını filtreleme

Birbirinin bir saat içinde oluşan aynı bağlama işlemleri için yinelenen denetim kayıtları, denetim gürültülerini ortadan kaldırmak için filtrelenmiş olarak filtre uygulanmıştır. Eşitleme işlemleri de bir saatlik aralıklarla filtreleniyor. Bu yineleme işleminin istisnası, aynı InternetMessageId için aşağıdaki tabloda açıklanan özelliklerden herhangi biri farklı olduğunda oluşur. Bu özelliklerden biri yinelenen bir işlemde farklı olursa, yeni bir denetim kaydı oluşturulur. Bu işlem, sonraki bölümde daha ayrıntılı olarak açıklanmıştır.

<br>

****

|Özellik|Açıklama|
|---|---|
|ClientIPAddress|İstemci bilgisayarın IP adresi.|
|ClientInfoString|Posta kutusuna erişmek için kullanılan istemci protokolüdür.|
|ParentFolder|Erişilen posta öğesinin tam klasör yolu.|
|Logon_type|Eylemi yapan kullanıcının oturum açma türü. Oturum açma türleri (ve karşılık gelen Enum değeri) Sahip (0), Yönetici (1) veya Temsilci (2) olur.|
|MailAccessType|Erişimin ister bağla ister eşitleme işlemi olsun.|
|MailboxUPN|İletinin okunan posta kutusunun UPN'si.|
|Kullanıcı|Kullanıcının iletiyi okuduğu UPN.|
|SessionId|Oturum Kimliği aynı posta kutusunda her iki günlük kullanıcı eylemlerini ve günlük kullanıcı etkinliklerini ayırt etmek için (hesabın tehlikeye at olması durumunda) oturumlar hakkında daha fazla bilgi için bkz. [Exchange Online'ta](https://techcommunity.microsoft.com/t5/exchange-team-blog/contextualizing-attacker-activity-within-sessions-in-exchange/ba-p/608801) oturumlar içinde saldırgan etkinliğini bağlamsal olarak bağlama bağlama.|
|

## <a name="identifying-the-access-contexts-of-different-audit-records"></a>Farklı denetim kayıtlarının erişim bağlamlarını tanımlama

Bir saldırgan, posta kutusu sahibi posta kutusuna erişirken aynı anda bir posta kutusuna da erişebiliyor olabilir. Saldırganla posta kutusu sahibi tarafından erişimi ayırt etmek için, erişimin bağlamını tanımlayan denetim kaydı özellikleri vardır. Daha önce de açıklanmıştır; toplama aralığında etkinlik gerçekleşirken bile bu özelliklerin değerleri farklı olduğunda, ayrı denetim kayıtları oluşturulur. Aşağıdaki örnekte üç farklı denetim kaydı var. Her biri Oturum Kimliği ve ClientIPAddress özellikleriyle birbirinden ayırt edildi. Erişilen iletiler de tanımlanır.

<br>

****

|Denetim kaydı 1|Denetim kaydı 2|Denetim kaydı 3|
|---|---|---|
|ClientIPAddress1<br/>**SessionId2**|ClientIPAddress2<br/>**SessionId2**|ClientIPAddress1<br/>**SessionId3**|
|**InternetMessageIdA**<br/>**InternetMessageIdd**<br/>**InternetMessageIdE**<br/>**InternetMessageIdF**<br/>|**InternetMessageIdA**<br/>**InternetMessageIdC**|**InternetMessageIdB**|
|

Önceki bölümde yer alan tabloda listelenen özelliklerden herhangi biri farklı [](#filtering-of-duplicate-audit-records) olursa, yeni bağlamı izlemek için ayrı bir denetim kaydı oluşturulur. Erişimler, etkinliğin tılı bir bağlama bağlı olarak ayrı denetim kayıtlarında sıralanmış olur.

Örneğin, aşağıdaki ekran görüntüsünde gösterilen denetim kayıtlarında, EWSEditor ve OWA'dan aynı anda postaya erişmemize rağmen, erişim etkinliği, erişimin gerçekleştirilme bağlamına bağlı olarak farklı denetim kayıtları arasında harmanlandı. Bu durumda, bağlam ClientInfoString özelliği için farklı değerlere göre tanımlanır.

![Bağlama göre farklı denetim kayıtları.](../media/MailItemsAccessed4.png)

Önceki ekran görüntüsünde gösterilen komutun söz dizimi şöyledir:

```powershell
Search-MailboxAuditLog -Identity admin -ShowDetails -Operations MailItemsAccessed -ResultSize 2000 | Select LastAccessed,Operation,AuditOperationsCountInAggregatedRecord,ClientInfoString
```
