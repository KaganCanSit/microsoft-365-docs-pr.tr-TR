---
title: Belgeleri FCI veya diğer özelliklerle korumak için DLP ilkesi oluşturma
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContentPropertyContainsWords
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
description: Üçüncü taraf sistem özellikleri olan belgeleri korumak için veri kaybı önleme (DLP) ilkesi kullanmayı öğrenin.
ms.openlocfilehash: fb8e1474666f016af3f6169f1a1d8d490a36f3c7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988094"
---
# <a name="create-a-dlp-policy-to-protect-documents-with-fci-or-other-properties"></a>Belgeleri FCI veya diğer özelliklerle korumak için DLP ilkesi oluşturma

Microsoft 365 kaybı önleme (DLP) ilkeleri, hassas öğeleri tanımlamak için sınıflandırma özelliklerini veya öğe özelliklerini kullanabilir. Örneğin şunları kullanabilirsiniz:

- Windows Sunucu Dosya Sınıflandırma altyapısı (FCI) özellikleri
- SharePoint özellikleri ekleme
- üçüncü taraf sistem belge özellikleri

![Dış sınıflandırma Office 365 gösteren diyagram.](../media/59ad0ac1-4146-4919-abd1-c74d8508d25e.png)

Örneğin, sosyal güvenlik numaraları gibi kişisel verileri olan öğeleri tanımlamak için Windows Server FCI kullanabilir ve ardından Kişisel Olarak Tanımlayıcı Bilgiler özelliğini Yüksek, **Orta, Düşük**, **Genel** veya **PiI** Değil  olarak ayarerek belgede bulunan kişisel verilerin türüne ve sayısına göre belgeyi sınıflandırabilirsiniz. 

Daha Microsoft 365'de, bu özelliğin yüksek ve Orta gibi belirli değerlere ayarlanmış belgelerini tanımlayan ve sonra bu dosyalara erişimi engelleme gibi bir eylemde bulunan belgeleri tanımlayan bir DLP ilkesi oluşturabilirsiniz. Aynı ilke, özellik Düşük olarak ayarlanırsa, e-posta bildirimi gönderme **gibi farklı bir** eyleme neden olan başka bir kurala sahip olabilir. Bu şekilde, DLP Windows Server FCI ile tümleştirilmiştir ve Office tabanlı dosya sunucularından Microsoft 365 veya paylaşılan Windows belgelerinin korunmasına yardımcı olabilir.

DLP ilkesi basitçe belirli bir özellik adını/değer çiftini aramaz. Özelliğin aramada ilgili yönetilen özelliği olduğu sürece, tüm belge SharePoint kullanılabilir. Örneğin, bir SharePoint koleksiyonunda Seyahat Raporu adlı bir içerik **türü ve Müşteri** adlı gerekli bir alan **kullanılabilir**. Bir kişi seyahat raporu oluşturduğunda müşteri adını girmeli. Bu özellik adı/değer çifti DLP ilkesinde de kullanılabilir; örneğin, **Müşteri alanı Contoso** içerdiğinde konuklar için belgeye erişimi engelleyen bir kural istiyorsanız.

DLP ilkenizi belirli etiketli içeriğe uygulamak Microsoft 365, buradaki adımları izlemeyebilirsiniz. Bunun yerine, [DLP ilkesinde bir bekletme etiketini koşul olarak kullanmayı öğrenin](data-loss-prevention-policies.md#using-a-retention-label-as-a-condition-in-a-dlp-policy).

## <a name="before-you-create-the-dlp-policy"></a>DLP ilkesi oluşturmadan önce

Bir DLP ilkesinde Windows Server FCI özelliğini veya başka bir özelliği kullanamadan önce, yönetim merkezinde yönetilen özellik SharePoint gerekir. İşte nedeni:

SharePoint Online ve OneDrive İş'de, arama dizini siteleriniz üzerinde içerikte gezinme özelliğiyle yerleşik olarak kullanılır. Gezgin belgelerden içeriği ve meta verileri gezinilen özellikler şeklinde seçer. Arama şeması, hangi içeriğin ve meta verilerin seçkiye sahip olduğuna gezgine yardımcı olur. Meta verilere örnek olarak belgenin yazarı ve başlığı örnek olarak verilmiştir. Bununla birlikte, belgelerden içerik ve meta verileri arama dizinine almak için, gezinilen özelliklerin yönetilen özelliklerle eşlenmiş olması gerekir. Yalnızca yönetilen özellikler dizinde tutulur. Örneğin, yazar ile ilgili gezinilen bir özellik, yazar ile ilgili yönetilen özelle eşlenmiştir.

> [!NOTE]
> Koşulu kullanarak DLP kuralları oluştururken gezinilen özellik adı yerine yönetilen özellik adı kullanmaya emin `ContentPropertyContainsWords` olun.

Bu önemlidir çünkü DLP, siteleriniz için hassas bilgileri tanımlamak ve sınıflandırmak için arama gezginini kullanır ve sonra da bu hassas bilgileri arama dizininin güvenli bir bölümünde depolar. Belgeyi Bu Belge Kitaplığı'Office 365, SharePoint özellikleri temel alan gezinilen özellikleri otomatik olarak oluşturur. Ama DLP ilkesinde FCI veya başka bir özellik kullanmak için, gezinilen özelliğin bir yönetilen özelikle eşlenmiş olması ve bu özelikle ilgili içeriğin dizinde tutulması gerekir.

Arama ve yönetilen özellikler hakkında daha fazla bilgi için bkz. [SharePoint Online'da arama şemasını yönetme](/sharepoint/manage-search-schema).

### <a name="step-1-upload-a-document-with-the-needed-property-to-office-365"></a>1. Adım: Upload özelliği olan bir belgeyi Office 365

İlk olarak, DLP ilkenize başvurarak, başvurabilirsiniz özelliği içeren bir belgeyi karşıya yükley gerekir. Microsoft 365 özelliği algılar ve bundan otomatik olarak gezinilen bir özellik oluşturulur. Sonraki adımda, bir yönetilen özellik oluşturun ve sonra yönetilen özelliği bu gezinilen özellikle eşlersiniz.

### <a name="step-2-create-a-managed-property"></a>2. Adım: Yönetilen özellik oluşturma

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetici merkezi</a>'nde oturum açın.

2. Sol gezintide Yönetim merkezleri **merkezi'ni SharePoint**\>. Artık genel yönetim SharePoint siniz.

3. Sol gezintide, arama **yönetimi sayfasında Arama** \> **Şemasını** **Yönet'i**\> seçin.

   ![yönetim merkezinde arama SharePoint sayfası.](../media/6bcd3aec-d11a-4f8c-9987-8f35da14d80b.png)

4. Yönetilen Özellikler **sayfasında Yeni** Yönetilen \> **Özellik**.

   ![Yeni Yönetilen Özellik düğmesinin vurgulu olduğu Yönetilen Özellikler sayfası.](../media/b161c764-414c-4037-83ed-503a49fb4410.png)

5. Özellik için bir ad ve açıklama girin. Bu ad, DLP ilkelerinizin içinde görünecek addır.

6. Tür **için Metin'i** **seçin**.

7. Ana **özellikler'in altında** Sorgulanabilir **ve Geri** **Alınabilir'i seçin**.

8. **Gezinilen özelliklere eşlemeler altında** \> **Eşleme ekleyin**.

9. Gezinilen **özellik** \> seçimi iletişim kutusunda, DLP ilkesi Tamam'ıcıda kullanabileceğiniz Windows Server FCI özelliğine veya başka bir özele karşılık gelen gezinilen özelliği bulun ve \> **seçin**.

   ![gezinilen özellik seçimi iletişim kutusu.](../media/aeda1dce-1342-48bf-9594-a8e4f230e8aa.png)

10. Sayfanın en altında **Tamam'ı**\> seçin.

## <a name="create-a-dlp-policy-that-uses-an-fci-property-or-other-property"></a>FCI özelliğini veya başka bir özelliği kullanan bir DLP ilkesi oluşturma

Bu örnekte, kuruluş Windows Sunucu tabanlı dosya sunucularında FCI kullanıyor; özel olarak, Yüksek, **Orta, Düşük**, Genel ve **PiI** Değil'in olası değerleriyle Kişisel  Olarak Tanımlayıcı Bilgiler adlı FCI sınıflandırma özelliğini kullanıyor.  Şimdi de varolan FCI sınıflandırmalarını kendi DLP ilkelerinde ve iş yerlerinde Office 365.

İlk olarak, yukarıdaki adımları takip eder ve SharePoint Online'da FCI özelliğinden otomatik olarak oluşturulan gezinilen özele eşlenir.

Ardından, Belge özellikleri'nin şu değerlerden herhangi birini içermesi koşullarını kullanan iki kuralı **olan bir DLP ilkesi oluşturacağız**:

- **FCI PII içeriği - Yüksek, Orta** İlk kural, FCI sınıflandırma özelliği Kişisel Olarak Tanımlanabilecek Bilgiler yüksek veya Orta'ya eşitse ve  belge kuruluş  dışındaki kişilerle paylaşılıyorsa belgeye erişimi kısıtlar.

- **FCI PII içeriği - Düşük** İkinci kural, FCI sınıflandırma özelliği Kişisel Olarak Tanımlayıcı Bilgiler Düşük'e eşitse  ve belge kuruluş dışındaki kişilerle  paylaşılıyorsa belge sahibine bir bildirim gönderir.

### <a name="create-the-dlp-policy-by-using-powershell"></a>PowerShell kullanarak DLP ilkesi oluşturma

Belge **özellikleri bu değerlerden herhangi** birini içerir koşulu &amp; Güvenlik Uyumluluk Merkezi kullanıcı arabiriminde geçici olarak kullanılamaz, ancak PowerShell'i kullanarak bu koşulu yine de kullanabilirsiniz. `New\Set\Get-DlpCompliancePolicy` Bir DLP ilkesiyle çalışmak için cmdlet'leri kullanabilir ve `New\Set\Get-DlpComplianceRule` Belge özellikleri'nin bu değerlerden herhangi birini içeren koşullarını eklemek için parametreyle birlikte cmdlet'leri `ContentPropertyContainsWords` **kullanabilirsiniz**.

Bu cmdlet'ler hakkında daha fazla bilgi için bkz. [Güvenlik &amp; Uyumluluk Merkezi cmdlet'leri](/powershell/exchange/exchange-online-powershell).

1. [Bağlan'e &amp; Uzak PowerShell kullanılarak Uyumluluk Merkezi](/powershell/exchange/connect-to-scc-powershell)

2. kullanarak ilkeyi oluşturun  `New-DlpCompliancePolicy`.

Bu PowerShell, tüm konumlara uygulanan bir DLP ilkesi oluşturur.

   ```powershell
   New-DlpCompliancePolicy -Name FCI_PII_policy -ExchangeLocation All -SharePointLocation All -OneDriveLocation All -Mode Enable
   ```

3. Yukarıda açıklanan iki kuralı oluşturmak için`New-DlpComplianceRule`: burada bir kural Düşük değer için, bir  kural da Yüksek ve **Orta değerleri** **içindir**.

   Bu iki kuralı oluşturan PowerShell örneği: Özellik adı/değer çiftleri tırnak içine alınır ve özellik adı boşluklar içinde virgülle ayrılmış birden çok değer belirtebilirsiniz.  `"<Property1>:<Value1>,<Value2>","<Property2>:<Value3>,<Value4>"....`

   ```powershell
   New-DlpComplianceRule -Name FCI_PII_content-High,Moderate -Policy FCI_PII_policy -AccessScope NotInOrganization -BlockAccess $true -ContentPropertyContainsWords "Personally Identifiable Information:High,Moderate" -Disabled $falseNew-DlpComplianceRule -Name FCI_PII_content-Low -Policy FCI_PII_policy -AccessScope NotInOrganization -BlockAccess $false -ContentPropertyContainsWords "Personally Identifiable Information:Low" -Disabled $false -NotifyUser Owner
   ```

   Windows Server FCI, bu örnekte kullanılan Kişisel Bilgileri de içinde olmak **üzere birçok** yerleşik özellik içerir. Her özellik için olası değerler her kuruluşta farklı olabilir. Burada **kullanılan** **Yüksek**, Orta **ve Düşük** değerleri yalnızca bir örnektir. Organizasyonunız için, sunucu tabanlı Windows sunucusundaki dosya Sunucu Kaynak Yöneticisi'nde olası değerleriyle birlikte Windows Server FCI sınıflandırma özelliklerini görüntüebilirsiniz. Daha fazla bilgi için bkz [. Sınıflandırma özelliği oluşturma](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759215(v=ws.11)).

Bitirseniz bile, ilkenizin, Belge özelliklerini kullanan iki yeni **kuralı olması gerekir. Bu değerler koşuldan herhangi birini** içerir. Bu koşul kullanıcı arabiriminde görünmez, ancak diğer koşullar, eylemler ve ayarlar görüntülenir.

Bir kural, Kişisel Olarak Tanımlayıcı Bilgiler özelliğinin **Yüksek veya Orta'ya** eşit olduğu **içeriğe erişimi** **engeller**. İkinci bir kural, Kişisel Olarak Tanımlayıcı Bilgiler özelliğinin Düşük **olduğu içerikle** ilgili bir bildirim **gönderir**.

![Yeni oluşturulan iki kuralı gösteren yeni DLP ilkesi iletişim kutusu.](../media/5c56c13b-62a5-4f25-8eb7-ce83a844bb12.png)

## <a name="after-you-create-the-dlp-policy"></a>DLP ilkesi oluşturduk sonra

Önceki bölümlerdeki adımların uygulayınılması, bu özelle içeriği hemen algılayan bir DLP ilkesi oluşturacağız, ancak bunun için içeriğin yeni karşıya yüklenmesi (içeriğin dizine alınan içerik için) veya içeriğin eski ancak yeni düzenli olduğu (içeriğin yeniden dizine alındı olarak) gerekmektedir.

Her yerde bu özelikle içeriği algılamak için, el ile kitaplığınız, siteniz veya site koleksiyonunuz için yeniden dizin oluşturma isteğinde bulundurabilirsiniz; böylelikle DLP ilkesi bu özelliğin tüm içeriğinin farkında olur. SharePoint Online'da, tanımlı gezinme zamanlamasına göre içerikte otomatik olarak gezinilir. Gezgin, son gezinmeden bu yana değiştirilmiş olan içeriği seçer ve dizini günceller. Bir sonraki zamanlanmış gezinmeden önce içeriği korumak için DLP ilkenize ihtiyacınız varsa, bu adımları atabilirsiniz.

> [!CAUTION]
> Sitenin yeniden dizininin yeniden dizininin yenisi, arama sisteminde muazzam bir yüke neden olabilir. Senaryonun kesinlikle gerekli olmadığı sürece, siteniz için yeniden dizin oluşturmayın.

Daha fazla bilgi için bkz. Site, kitaplık veya liste için gezinme ve yeniden dizin [oluşturma el ile isteğinde bulundurabilirsiniz](/sharepoint/crawl-site-content).

### <a name="reindex-a-site-optional"></a>Siteyi yeniden yeniden indir (isteğe bağlı)

1. Sitede, Site Ayarlar (**sağ** üstteki dişli simgesi) \> simgesini **Ayarlar**.

2. **Arama'nın** altında Arama **ve çevrimdışı kullanılabilirlik Siteyi** \> **yeniden tahsis edin'i seçin**.

## <a name="more-information"></a>Daha fazla bilgi

- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)

- [Şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)

- [Bildirim gönderme ve DLP ilkeleriyle ilgili ilke ipuçlarını gösterme](use-notifications-and-policy-tips.md)

- [DLP ilkesi şablonlarının şunları içermesi](what-the-dlp-policy-templates-include.md)

- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)