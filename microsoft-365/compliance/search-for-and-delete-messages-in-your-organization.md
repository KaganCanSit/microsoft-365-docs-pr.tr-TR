---
title: Kuruluşunuzda e-posta iletilerini arama ve silme
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
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 3526fd06-b45f-445b-aed4-5ebd37b3762a
description: Kuruluşunuzdaki tüm posta kutularında e-posta iletisi aramak ve silmek için Microsoft Purview uyumluluk portalındaki arama ve temizleme özelliğini kullanın.
ms.openlocfilehash: 67a1c6758a5030897afbde07a0803cad348eca0c
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993676"
---
# <a name="search-for-and-delete-email-messages"></a>E-posta iletilerini arama ve silme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**Bu makale yöneticilere yöneliktir. Posta kutunuzda silmek istediğiniz öğeleri bulmaya mı çalışıyorsunuz? Bkz. [Hızlı Arama ile ileti veya öğe bulma](https://support.office.com/article/69748862-5976-47b9-98e8-ed179f1b9e4d)**.

Kuruluşunuzdaki tüm posta kutularında e-posta iletilerini aramak ve silmek için İçerik arama özelliğini kullanabilirsiniz. Bu, aşağıdakiler gibi zararlı veya yüksek riskli olabilecek e-postaları bulmanıza ve kaldırmanıza yardımcı olabilir:

- Tehlikeli ekler veya virüsler içeren iletiler

- Kimlik avı iletileri

- Hassas veriler içeren iletiler

> [!TIP]
> Kuruluşunuzun Office 365 için Defender Plan 2 aboneliği varsa, bu makalede açıklanan yordamı takip etmek yerine [Office 365'da sunulan kötü amaçlı e-postayı düzeltme](/microsoft-365/security/office-365-security/remediate-malicious-email-delivered-office-365) başlığı altında açıklanan yordamı kullanmanızı öneririz.

## <a name="before-you-begin"></a>Başlamadan önce

- Bu makalede açıklanan arama ve temizleme iş akışı, sohbet iletilerini veya diğer içeriği Microsoft Teams silmez. 2. Adımda oluşturduğunuz İçerik araması Microsoft Teams öğeleri döndürürse, 3. Adımda öğeleri temizlediğinizde bu öğeler silinmez. Sohbet iletilerini aramak ve silmek için bkz[. Teams sohbet iletilerini arama ve temizleme](search-and-delete-Teams-chat-messages.md).

- İçerik araması oluşturmak ve çalıştırmak için **eBulma Yöneticisi** rol grubunun üyesi olmanız veya Microsoft Purview uyumluluk portalında **Uyumluluk Araması** rolüne atanmış olmanız gerekir. İletileri silmek için **Kuruluş Yönetimi** rol grubunun üyesi olmanız veya uyumluluk merkezinde **Arama ve Temizleme** rolüne atanmış olmanız gerekir Rol grubuna kullanıcı ekleme hakkında bilgi için bkz. [eBulma izinleri atama](assign-ediscovery-permissions.md).

  > [!NOTE]
  > **Kuruluş Yönetimi** rol grubu hem Exchange Online hem de uyumluluk portalında bulunur. Bunlar, farklı izinler veren ayrı rol gruplarıdır. Exchange Online'da **Kuruluş Yönetimi** üyesi olmak, e-posta iletilerini silmek için gerekli izinleri vermez. Uyumluluk merkezinde (doğrudan veya **Kuruluş Yönetimi** gibi bir rol grubu aracılığıyla) **Arama ve Temizleme** rolü size atanmazsa, 3. Adım'da **New-ComplianceSearchAction** cmdlet'ini çalıştırdığınızda "Parametre adı 'Purge' ile eşleşen bir parametre bulunamıyor" iletisiyle bir hata alırsınız.

- İletileri silmek için Güvenlik & Uyumluluk Merkezi PowerShell'i kullanmanız gerekir. Bağlanma hakkında yönergeler için [bkz. 1. Adım](#step-1-connect-to-security--compliance-center-powershell) .

- Posta kutusu başına bir kerede en fazla 10 öğe kaldırılabilir. İletileri arama ve kaldırma özelliği bir olay yanıtı aracı olması amaçlandığından, bu sınır iletilerin posta kutularından hızla kaldırılmasına yardımcı olur. Bu özellik, kullanıcı posta kutularını temizlemeye yönelik değildir.

- İçerik aramasında, arama ve temizleme eylemi yaparak öğeleri silmek için kullanabileceğiniz en fazla posta kutusu sayısı 50.000'dir. [2. Adımda](#step-2-create-a-content-search-to-find-the-message-to-delete) oluşturduğunuz arama (50.000'den fazla posta kutusunda arama yaparsanız, temizleme eylemi (3. Adımda oluşturduğunuz) başarısız olur. Tek bir aramada 50.000'den fazla posta kutusunda arama yapmak genellikle aramayı kuruluşunuzdaki tüm posta kutularını içerecek şekilde yapılandırdığınızda gerçekleşebilir. Bu kısıtlama, 50.000'den az posta kutusu arama sorgusuyla eşleşen öğeler içerdiğinde bile geçerlidir. 50.000'den fazla posta kutusundan öğe aramak ve temizlemek için arama izinleri filtrelerini kullanma hakkında yönergeler için [Daha fazla bilgi](#more-information) bölümüne bakın.

- Bu makaledeki yordam yalnızca Exchange Online posta kutularındaki ve ortak klasörlerdeki öğeleri silmek için kullanılabilir. SharePoint veya OneDrive İş sitelerden içerik silmek için kullanamazsınız.

- eBulma (Premium) durumundaki bir gözden geçirme kümesindeki e-posta öğeleri bu makaledeki yordamlar kullanılarak silinemez. Bunun nedeni, bir gözden geçirme kümesindeki öğelerin canlı hizmette değil Azure Depolama konumunda depolanmasıdır. Bu, 1. Adımda oluşturduğunuz içerik araması tarafından döndürülmeyecekleri anlamına gelir. Gözden geçirme kümesindeki öğeleri silmek için, gözden geçirme kümesini içeren eBulma (Premium) servis talebini silmeniz gerekir. Daha fazla bilgi için bkz. [eBulma (Premium) servis talebini kapatma veya silme](close-or-delete-case.md).

## <a name="step-1-connect-to-security--compliance-center-powershell"></a>1. Adım: Güvenlik & Uyumluluk Merkezi PowerShell'e Bağlan

İlk adım, kuruluşunuz için Güvenlik & Uyumluluk Merkezi PowerShell'e bağlanmaktır. Adım adım yönergeler için bkz[. Güvenlik & Uyumluluk Merkezi PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-2-create-a-content-search-to-find-the-message-to-delete"></a>2. Adım: Silinecek iletiyi bulmak için İçerik Araması oluşturma

İkinci adım, kuruluşunuzdaki posta kutularından kaldırmak istediğiniz iletiyi bulmak için bir İçerik araması oluşturmak ve çalıştırmaktır. Uyumluluk portalını kullanarak veya Güvenlik & Uyumluluk PowerShell'de **New-ComplianceSearch** ve **Start-ComplianceSearch** cmdlet'lerini çalıştırarak arama oluşturabilirsiniz. Bu aramanın sorgusuyla eşleşen iletiler [, 3. Adımda](#step-3-delete-the-message) **New-ComplianceSearchAction -Purge** komutu çalıştırılarak silinir. İçerik araması oluşturma ve arama sorgularını yapılandırma hakkında bilgi için aşağıdaki konulara bakın:

- [Office 365'de içerik arama](content-search.md)

- [İçerik araması için anahtar sözcük sorguları](keyword-queries-and-search-conditions.md)

- [New-ComplianceSearch](/powershell/module/exchange/New-ComplianceSearch)

- [Start-ComplianceSearch](/powershell/module/exchange/Start-ComplianceSearch)

> [!NOTE]
> Bu adımda oluşturduğunuz İçerik aramasında arama yapılan içerik konumları, SharePoint veya OneDrive İş siteleri içeremez. İletileri e-postayla göndermek için kullanılacak bir İçerik aramasına yalnızca posta kutularını ve ortak klasörleri ekleyebilirsiniz. İçerik araması siteleri içeriyorsa, 3. Adımda **New-ComplianceSearchAction** cmdlet'ini çalıştırdığınızda bir hata alırsınız.

### <a name="tips-for-finding-messages-to-remove"></a>Kaldırılacak iletileri bulmak için İpuçları

Arama sorgusunun amacı, arama sonuçlarını yalnızca kaldırmak istediğiniz ileti veya iletilere daraltmaktır. Bazı ipuçları şunlardır:

- İletinin konu satırında kullanılan metin veya tümceciği tam olarak biliyorsanız, arama sorgusundaki **Subject** özelliğini kullanın.

- İletinin tam tarihini (veya tarih aralığını) biliyorsanız, arama sorgusuna **Received** özelliğini ekleyin.

- İletiyi kimin gönderdiğini biliyorsanız, arama sorgusuna **From** özelliğini ekleyin.

- Aramanın yalnızca silmek istediğiniz iletiyi (veya iletileri) döndürdüğünü doğrulamak için arama sonuçlarının önizlemesini görüntüleyin.

- Toplam sonuç sayısını almak için arama tahmini istatistiklerini kullanın (uyumluluk portalında veya [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch) cmdlet'ini kullanarak aramanın ayrıntılar bölmesinde görüntülenir).

Şüpheli e-posta iletilerini bulmak için iki sorgu örneği aşağıda verilmiştir.

- Bu sorgu, kullanıcılar tarafından 13 Nisan 2016 ile 14 Nisan 2016 arasında alınan ve konu satırında "eylem" ve "gerekli" sözcüklerini içeren iletileri döndürür.

  ```powershell
  (Received:4/13/2016..4/14/2016) AND (Subject:'Action required')
  ```

- Bu sorgu, chatsuwloginsset12345@outlook.com tarafından gönderilen ve konu satırında "Hesap bilgilerinizi güncelleştirin" tam tümceciği içeren iletileri döndürür.

  ```powershell
  (From:chatsuwloginsset12345@outlook.com) AND (Subject:"Update your account information")
  ```

Kuruluştaki tüm posta kutularında arama yapmak için **New-ComplianceSearch** ve **Start-ComplianceSearch** cmdlet'lerini çalıştırarak arama oluşturmak ve başlatmak için bir sorgu kullanma örneği aşağıda verilmiştir:

```powershell
$Search=New-ComplianceSearch -Name "Remove Phishing Message" -ExchangeLocation All -ContentMatchQuery '(Received:4/13/2016..4/14/2016) AND (Subject:"Action required")'
Start-ComplianceSearch -Identity $Search.Identity
```

## <a name="step-3-delete-the-message"></a>3. Adım: İletiyi silme

Kaldırmak istediğiniz iletileri döndürmek için bir İçerik araması oluşturup geliştirdikten sonra, son adım iletiyi silmek için Güvenlik & Uyumluluk PowerShell'de **New-ComplianceSearchAction -Purge** komutunu çalıştırmaktır. İletiyi geçici veya sabit olarak silebilirsiniz. Geçici olarak silinen bir ileti kullanıcının Kurtarılabilir Öğeler klasörüne taşınır ve silinen öğe saklama süresi dolana kadar korunur. Sabit silinen iletiler posta kutusundan kalıcı olarak kaldırılmak üzere işaretlenir ve posta kutusu Yönetilen Klasör Yardımcısı tarafından bir sonraki işlendiğinde kalıcı olarak kaldırılır. Posta kutusu için tek öğe kurtarma etkinleştirilirse, silinmiş öğe saklama süresi dolduktan sonra sabit silinen öğeler kalıcı olarak kaldırılır. Bir posta kutusu beklemeye alınırsa, öğenin saklama süresi dolana kadar veya saklama posta kutusundan kaldırılana kadar silinen iletiler korunur.

> [!NOTE]
> Daha önce belirtildiği gibi, Microsoft Teams İçerik araması tarafından döndürülen öğeler **New-ComplianceSearchAction -Purge** komutunu çalıştırdığınızda silinmez.

İletileri silmek üzere aşağıdaki komutları çalıştırmak için [Güvenlik & Uyumluluk Merkezi PowerShell'e bağlı olduğunuzdan](/powershell/exchange/connect-to-scc-powershell) emin olun.

### <a name="soft-delete-messages"></a>geçici silme iletileri

Aşağıdaki örnekte, komutu "Kimlik Avı İletisini Kaldır" adlı bir İçerik araması tarafından döndürülen arama sonuçlarını geçici olarak siler.

```powershell
New-ComplianceSearchAction -SearchName "Remove Phishing Message" -Purge -PurgeType SoftDelete
```

### <a name="hard-delete-messages"></a>İletileri kesin silme

"Kimlik Avı İletisini Kaldır" içerik araması tarafından döndürülen öğeleri sert bir şekilde silmek için şu komutu çalıştırırsınız:

```powershell
New-ComplianceSearchAction -SearchName "Remove Phishing Message" -Purge -PurgeType HardDelete
```

Önceki komutları geçici veya sabit silme iletileri için çalıştırdığınızda,  *SearchName*  parametresi tarafından belirtilen arama, 1. Adımda oluşturduğunuz İçerik aramasıdır.

Daha fazla bilgi için bkz. [New-ComplianceSearchAction](/powershell/module/exchange/New-ComplianceSearchAction).

## <a name="more-information"></a>Daha fazla bilgi

- **Arama ve kaldırma işleminin durumunu nasıl alırsınız?**

  Silme işleminin durumunu almak için **Get-ComplianceSearchAction** komutunu çalıştırın. **New-ComplianceSearchAction** cmdlet'ini çalıştırdığınızda oluşturulan nesne şu biçim kullanılarak adlandırılır: `<name of Content Search>_Purge`.

- **Bir iletiyi sildikten sonra ne olur?**

  komutuyla  `New-ComplianceSearchAction -Purge -PurgeType HardDelete` silinen bir ileti Temizleme klasörüne taşınır ve kullanıcı tarafından erişilemiyor. İleti Temizlemeler klasörüne taşındıktan sonra, posta kutusu için tek öğe kurtarma etkinleştirildiyse, ileti silinmiş öğe saklama süresi boyunca korunur. (Microsoft 365'da, yeni bir posta kutusu oluşturulduğunda varsayılan olarak tek öğe kurtarma etkinleştirilir.) Silinen öğe saklama süresi dolduktan sonra, ileti kalıcı silme için işaretlenir ve posta kutusu Yönetilen Klasör yardımcısı tarafından bir sonraki işlendiğinde Microsoft 365 temizlenir.

  komutunu kullanırsanız `New-ComplianceSearchAction -Purge -PurgeType SoftDelete` , iletiler kullanıcının Kurtarılabilir Öğeler klasöründeki Silmeler klasörüne taşınır. Microsoft 365 hemen temizlenmez. Kullanıcı, silinmiş öğeler klasöründeki iletileri, posta kutusu için yapılandırılan silinmiş öğe saklama süresine göre süre boyunca kurtarabilir. Bu saklama süresi dolduktan sonra (veya kullanıcı iletiyi süresi dolmadan önce temizlerse), ileti Temizleme klasörüne taşınır ve artık kullanıcı tarafından erişilemiyor. Temizlemeler klasörüne girdikten sonra, posta kutusu için tek öğe kurtarma etkinleştirildiyse ileti, posta kutusu için yapılandırılan silinmiş öğe saklama süresine göre süre boyunca saklanır. (Microsoft 365'da, yeni bir posta kutusu oluşturulduğunda varsayılan olarak tek öğe kurtarma etkinleştirilir.) Silinen öğe saklama süresi sona erdikten sonra, ileti kalıcı silme için işaretlenir ve posta kutusu Yönetilen Klasör yardımcısı tarafından bir sonraki işlendiğinde Microsoft 365 temizlenir.

- **50.000'den fazla posta kutusundan bir iletiyi silmeniz gerekiyorsa ne olur?**

  Daha önce belirtildiği gibi, en fazla 50.000 posta kutusunda (50.000'den azı arama sorgusuyla eşleşen öğeler içerse bile) bir arama ve temizleme işlemi gerçekleştirebilirsiniz. 50.000'den fazla posta kutusunda arama ve temizleme işlemi yapmanız gerekiyorsa, aranacak posta kutularının sayısını 50.000'den az posta kutusuna indiren geçici arama izinleri filtreleri oluşturmayı göz önünde bulundurun. Örneğin, kuruluşunuz farklı departmanlarda, eyaletlerde veya ülkelerde posta kutuları içeriyorsa, kuruluşunuzdaki posta kutularının bir alt kümesini aramak için bu posta kutusu özelliklerinden birini temel alan bir posta kutusu arama izinleri filtresi oluşturabilirsiniz. Arama izinleri filtresini oluşturduktan sonra, aramayı oluşturursunuz (1. Adımda açıklanmıştır) ve ardından iletiyi silersiniz (3. Adımda açıklanmıştır). Ardından filtreyi düzenleyerek farklı bir posta kutusu kümesindeki iletileri arayabilir ve temizleyebilirsiniz. Arama izinleri filtreleri oluşturma hakkında daha fazla bilgi için bkz. [İçerik Arama için izin filtrelemeyi yapılandırma](permissions-filtering-for-content-search.md).

- **Arama sonuçlarına dahil edilen dizine alınmamış öğeler silinecek mi?**

  Hayır, 'New-ComplianceSearchAction -Purge komutu dizine alınmamış öğeleri silmez.

- **In-Place Ayrı Tutma veya Dava Tutma'ya yerleştirilmiş veya Microsoft 365 saklama ilkesine atanmış bir posta kutusundan ileti silinirse ne olur?**

  İleti temizlendikten ve Temizleme klasörüne taşındıktan sonra, saklama süresi dolana kadar ileti korunur. Ayrı tutma süresi sınırsızsa, ayrı tutma kaldırılana veya saklama süresi değiştirilene kadar öğeler korunur.

- **Arama ve kaldırma iş akışı neden farklı güvenlik ve uyumluluk merkezi rol grupları arasında bölünür?**

  Daha önce açıklandığı gibi, bir kişinin eBulma Yöneticisi rol grubunun üyesi olması veya posta kutularını aramak için Uyumluluk Araması yönetim rolüne atanması gerekir. İletileri silmek için, bir kişinin Kuruluş Yönetimi rol grubunun üyesi olması veya Arama Ve Temizleme yönetimi rolüne atanmış olması gerekir. Bu, kuruluştaki posta kutularını kimlerin arayabileceğini ve iletileri kimlerin silebileceğini denetlemeyi mümkün kılar.
