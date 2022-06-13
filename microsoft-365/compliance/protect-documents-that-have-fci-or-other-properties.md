---
title: Belgeleri korumak için DLP ilkesi oluşturma
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
- admindeeplinkSPO
description: Üçüncü taraf sistem özelliklerine sahip belgeleri korumak için veri kaybı önleme (DLP) ilkesini kullanmayı öğrenin.
ms.openlocfilehash: 1b73f1441909c49534c17cef47804021ca2824dd
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66007272"
---
# <a name="create-a-dlp-policy-to-protect-documents-with-fci-or-other-properties"></a>FCI veya diğer özellikler ile belgeleri korumak için bir DLP ilkesi oluşturma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview Veri Kaybı Önleme (DLP) ilkeleri, hassas öğeleri tanımlamak için sınıflandırma özelliklerini veya öğe özelliklerini kullanabilir. Örneğin, şunu kullanabilirsiniz:

- Windows Sunucu Dosya Sınıflandırma altyapısı (FCI) özellikleri
- Belge özelliklerini SharePoint
- üçüncü taraf sistem belge özellikleri

![Office 365 ve dış sınıflandırma sistemini gösteren diyagram.](../media/59ad0ac1-4146-4919-abd1-c74d8508d25e.png)

Örneğin, kuruluşunuz sosyal güvenlik numaraları gibi kişisel verileri olan öğeleri tanımlamak için Windows Server FCI'yi kullanabilir ve ardından **Kişisel Olarak Tanımlanabilir Bilgi** özelliğini belgede bulunan kişisel verilerin türüne ve sayısına göre **Yüksek**, **Orta**, **Düşük**, **Genel** veya **PiI değil** olarak ayarlayarak belgeyi sınıflandırabilir.

Microsoft 365'da, bu **özelliğin Yüksek** ve **Orta** gibi belirli değerlere ayarlandığı belgeleri tanımlayan ve ardından bu dosyalara erişimi engelleme gibi bir eylemde bulunan bir DLP ilkesi oluşturabilirsiniz. Özellik **Düşük** olarak ayarlanırsa, e-posta bildirimi göndermek gibi farklı bir eylemde bulunan başka bir kural aynı ilkeye sahip olabilir. Bu şekilde DLP, Windows Server FCI ile tümleşir ve Microsoft 365 Windows Sunucu tabanlı dosya sunucularından karşıya yüklenen veya paylaşılan Office belgelerin korunmasına yardımcı olabilir.

DLP ilkesi yalnızca belirli bir özellik adı/değer çiftini arar. Özelliğin SharePoint arama için ilgili yönetilen özelliği olduğu sürece herhangi bir belge özelliği kullanılabilir. Örneğin, bir SharePoint site koleksiyonu **, Müşteri** adlı gerekli bir alanla **Gezi Raporu** adlı bir içerik türü kullanabilir. Bir kişi bir seyahat raporu oluşturduğunda müşteri adını girmesi gerekir. Bu özellik adı/değer çifti bir DLP ilkesinde de kullanılabilir; örneğin, **Müşteri** alanı **Contoso** içerdiğinde konuklar için belgeye erişimi engelleyen bir kural istiyorsanız.

DLP ilkenizi belirli Microsoft 365 etiketleri olan içeriğe uygulamak istiyorsanız buradaki adımları izlememelisiniz. Bunun yerine, [DLP ilkesinde bekletme etiketini koşul olarak kullanma](data-loss-prevention-policies.md#using-a-retention-label-as-a-condition-in-a-dlp-policy) hakkında bilgi edinin.

## <a name="before-you-create-the-dlp-policy"></a>DLP ilkesini oluşturmadan önce

DLP ilkesinde Windows Server FCI özelliğini veya başka bir özelliği kullanabilmeniz için <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">önce SharePoint yönetim merkezinde</a> yönetilen bir özellik oluşturmanız gerekir. İşte nedeni.

SharePoint Online ve OneDrive İş'da arama dizini, sitelerinizdeki içerikte gezinilerek oluşturulur. Gezgin, belgelerden gezinilen özellikler biçiminde içerik ve meta veriler alır. Arama şeması, gezginin hangi içeriği ve meta verileri seçeceğine karar vermesine yardımcı olur. Meta veri örnekleri, belgenin yazarı ve başlığıdır. Ancak, belgelerden içeriği ve meta verileri arama dizinine almak için gezinilen özelliklerin yönetilen özelliklerle eşlenmesi gerekir. Dizinde yalnızca yönetilen özellikler tutulur. Örneğin, yazarla ilgili gezinilen bir özellik, yazarla ilgili yönetilen bir özelliğe eşlenir.

> [!NOTE]
> Koşulu kullanarak DLP kuralları oluştururken gezinilen özellik adı değil yönetilen özellik adı kullandığınızdan `ContentPropertyContainsWords` emin olun.

Bu önemlidir çünkü DLP, sitelerinizdeki hassas bilgileri tanımlamak ve sınıflandırmak için arama gezginini kullanır ve ardından bu hassas bilgileri arama dizininin güvenli bir bölümünde depolar. Belgeyi Office 365 yüklediğinizde, SharePoint belge özelliklerine göre otomatik olarak gezinilen özellikler oluşturur. Ancak, bir DLP ilkesinde FCI veya başka bir özellik kullanmak için, bu özelliğe sahip içeriğin dizinde tutulması için gezinilen özelliğin yönetilen bir özelliğe eşlenmesi gerekir.

Arama ve yönetilen özellikler hakkında daha fazla bilgi için bkz. [SharePoint Online'da arama şemasını yönetme](/sharepoint/manage-search-schema).

### <a name="step-1-upload-a-document-with-the-needed-property-to-office-365"></a>1. Adım: Office 365 için gerekli özelliğe sahip bir belgeyi Upload

Önce DLP ilkenizde başvurmak istediğiniz özelliğe sahip bir belgeyi karşıya yüklemeniz gerekir. Microsoft 365 özelliği algılar ve bu özellikten otomatik olarak gezinilen bir özellik oluşturur. Sonraki adımda yönetilen bir özellik oluşturacak ve yönetilen özelliği bu gezinilen özelliğe eşleyeceksiniz.

### <a name="step-2-create-a-managed-property"></a>2. Adım: Yönetilen özellik oluşturma

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetici merkezi</a>'nde oturum açın.

2. Sol gezinti bölmesinde **Yönetim** **merkezleri'ni**\> SharePoint seçin. Artık <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint yönetim merkezindesiniz</a>.

3. Sol gezinti bölmesinde arama **yönetimi** sayfasında \> **Arama Şemasını Yönet'i** **seçin**\>.

   ![SharePoint yönetim merkezinde arama yönetimi sayfası.](../media/6bcd3aec-d11a-4f8c-9987-8f35da14d80b.png)

4. **Yönetilen Özellikler** sayfasında \> **Yeni Yönetilen Özellik**.

   ![Yeni Yönetilen Özellik düğmesinin vurgulandığı Yönetilen Özellikler sayfası.](../media/b161c764-414c-4037-83ed-503a49fb4410.png)

5. Özellik için bir ad ve açıklama girin. Bu ad, DLP ilkelerinizde görünecek olan addır.

6. **Tür** için **Metin'i** seçin.

7. **Ana özellikler'in** altında **Sorgulanabilir** ve **Alınabilir'i** seçin.

8. **Gezilen özelliklere** \> eşlemeler altında **Eşleme ekleyin**.

9. **Gezinilen özellik seçimi** iletişim kutusunda\>, Windows Server FCI özelliğine veya DLP ilkenizde \> kullanacağınız diğer özelliğe karşılık gelen gezinilen özelliği bulun ve seçin **.**

   ![gezinilen özellik seçimi iletişim kutusu.](../media/aeda1dce-1342-48bf-9594-a8e4f230e8aa.png)

10. Sayfanın \> en altında **Tamam'ı seçin**.

## <a name="create-a-dlp-policy-that-uses-an-fci-property-or-other-property"></a>FCI özelliğini veya başka bir özelliği kullanan bir DLP ilkesi oluşturma

Bu örnekte, bir kuruluş Windows Sunucu tabanlı dosya sunucularında FCI kullanıyor; özellikle, **Yüksek**, **Orta**, **Düşük**, **Genel** ve **PII Değil** olası değerleriyle **Kişisel Olarak Tanımlanabilir Bilgiler** adlı FCI sınıflandırma özelliğini kullanıyor. Şimdi Office 365'deki DLP ilkelerinde mevcut FCI sınıflandırmalarını kullanmak istiyorlar.

İlk olarak, SharePoint Online'da FCI özelliğinden otomatik olarak oluşturulan gezinilen özelliğe eşlenen bir yönetilen özellik oluşturmak için yukarıdaki adımları izlerler.

Ardından, **belge özellikleri şu değerlerden herhangi birini içeren** koşulunu kullanan iki kurala sahip bir DLP ilkesi oluşturur:

- **FCI PII içeriği - Yüksek, Orta** İlk kural, **FCI sınıflandırma özelliği Kişisel Bilgiler** **yüksek** veya **orta** düzeye eşitse ve belge kuruluş dışındaki kişilerle paylaşılıyorsa belgeye erişimi kısıtlar.

- **FCI PII içeriği - Düşük** İkinci kural, **FCI sınıflandırma özelliği Kişisel Olarak Tanımlanabilir Bilgiler** **düşükse** ve belge kuruluş dışındaki kişilerle paylaşılıyorsa belge sahibine bir bildirim gönderir.

### <a name="create-the-dlp-policy-by-using-security--compliance-powershell"></a>Güvenlik & Uyumluluğu PowerShell kullanarak DLP ilkesini oluşturma

**Belge özellikleri bu değerlerden herhangi birini içeren** koşul Microsoft Purview uyumluluk portalında geçici olarak kullanılamaz, ancak bu koşulu Güvenlik & Uyumluluk PowerShell'de kullanmaya devam edebilirsiniz. Bir DLP ilkesiyle çalışmak için cmdlet'leri kullanabilir `New\Set\Get-DlpCompliancePolicy` ve **Belge özellikleri bu değerlerden herhangi birini içeren** koşulunu eklemek için cmdlet'leri parametresiyle `ContentPropertyContainsWords` kullanabilirsiniz`New\Set\Get-DlpComplianceRule`.

1. [Güvenlik & Uyumluluğu PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell)

2. kullanarak `New-DlpCompliancePolicy`ilkeyi oluşturun.

   Bu PowerShell, tüm konumlar için geçerli olan bir DLP ilkesi oluşturur.

   ```powershell
   New-DlpCompliancePolicy -Name FCI_PII_policy -ExchangeLocation All -SharePointLocation All -OneDriveLocation All -Mode Enable
   ```

3. Yukarıda açıklanan iki kuralı kullanarak `New-DlpComplianceRule`oluşturun. Burada bir kural **Düşük** değer, diğer kural ise **Yüksek** ve **Orta** değerler içindir.

   Bu iki kuralı oluşturan bir PowerShell örneği aşağıda verilmiştir. Özellik adı/değer çiftleri tırnak içine alınır ve özellik adı boşluk olmadan virgülle ayrılmış birden çok değer belirtebilir, örneğin `"<Property1>:<Value1>,<Value2>","<Property2>:<Value3>,<Value4>"....`

   ```powershell
   New-DlpComplianceRule -Name FCI_PII_content-High,Moderate -Policy FCI_PII_policy -AccessScope NotInOrganization -BlockAccess $true -ContentPropertyContainsWords "Personally Identifiable Information:High,Moderate" -Disabled $falseNew-DlpComplianceRule -Name FCI_PII_content-Low -Policy FCI_PII_policy -AccessScope NotInOrganization -BlockAccess $false -ContentPropertyContainsWords "Personally Identifiable Information:Low" -Disabled $false -NotifyUser Owner
   ```

   Windows Server FCI, bu örnekte kullanılan **Kişisel Bilgiler** de dahil olmak üzere birçok yerleşik özellik içerir. Her özelliğin olası değerleri her kuruluş için farklı olabilir. Burada kullanılan **Yüksek**, **Orta** ve **Düşük** değerleri yalnızca bir örnektir. Kuruluşunuz için, Windows Server FCI sınıflandırma özelliklerini olası değerleriyle birlikte Windows Sunucu tabanlı dosya sunucusundaki Sunucu Resource Manager dosyasında görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [Sınıflandırma özelliği oluşturma](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759215(v=ws.11)).

bitirdiğinizde, ilkenizin her ikisinde de Belge özelliklerini kullanan iki yeni kural **olmalıdır ve bu değer koşulundan herhangi birini içerir** . Diğer koşullar, eylemler ve ayarlar görünse de bu koşul kullanıcı arabiriminde görünmez.

Bir kural **, Kişisel Bilgiler** özelliğinin **Yüksek** veya **Orta'ya** eşit olduğu içeriğe erişimi engeller. İkinci bir kural **, Kişisel Olarak Tanımlanabilir Bilgi** özelliğinin **Düşük** olduğu içerik hakkında bir bildirim gönderir.

![Yeni oluşturulan iki kuralı gösteren yeni DLP ilkesi iletişim kutusu.](../media/5c56c13b-62a5-4f25-8eb7-ce83a844bb12.png)

## <a name="after-you-create-the-dlp-policy"></a>DLP ilkesini oluşturduktan sonra

Önceki bölümlerdeki adımların yapılması, bu özelliğe sahip içeriği hızlı bir şekilde algılayan bir DLP ilkesi oluşturur, ancak yalnızca bu içerik yeni karşıya yüklenirse (içerik dizine alınırsa) veya bu içerik eskiyse ancak yalnızca düzenlenmişse (içeriğin yeniden dizine alınabilmesi için).

Bu özelliğe sahip içeriği her yerde algılamak için, kitaplığınızın, sitenizin veya site koleksiyonunuzun yeniden dizine alınması için el ile istekte bulunmak isteyebilirsiniz; böylece DLP ilkesi bu özelliğe sahip tüm içeriği algılar. SharePoint Online'da içerik, tanımlı gezinme zamanlamasına göre otomatik olarak gezinilir. Gezgin, son gezinmeden sonra değiştirilen içeriği alır ve dizini güncelleştirir. Bir sonraki zamanlanmış gezinmeden önce içeriği korumak için DLP ilkenize ihtiyacınız varsa, bu adımları uygulayabilirsiniz.

> [!CAUTION]
> Bir sitenin yeniden dizinlenmesi, arama sisteminde çok büyük bir yüke neden olabilir. Senaryonuz kesinlikle gerekli olmadıkça sitenizi yeniden dizine oluşturmayın.

Daha fazla bilgi için bkz. [Site, kitaplık veya liste için el ile gezinme ve yeniden dizin oluşturma isteği](/sharepoint/crawl-site-content).

### <a name="reindex-a-site-optional"></a>Siteyi yeniden dizine alma (isteğe bağlı)

1. Sitede **, Ayarlar** (sağ üstteki dişli simgesi) \> **Site Ayarlar'ı** seçin.

2. **Arama'nın** altında **Arama ve çevrimdışı kullanılabilirlik** \> **Reindex sitesi'ni** seçin.

## <a name="more-information"></a>Daha fazla bilgi

- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md)

- [Bir şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)

- [DLP ilkeleri için bildirim gönderme ve ilke ipuçlarını gösterme](use-notifications-and-policy-tips.md)

- [DLP ilke şablonları neler içerir?](what-the-dlp-policy-templates-include.md)

- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
