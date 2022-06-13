---
title: Kimlik sahtekarlığı analizi içgörüleri
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 978c3173-3578-4286-aaf4-8a10951978bf
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, Exchange Online Protection (EOP) içindeki kimlik sahtekarlığına ilişkin zeka içgörüleri hakkında bilgi edinebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9455ddf17d26e33ed5b2669a27ee93cf5f56b8f9
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016064"
---
# <a name="spoof-intelligence-insight-in-eop"></a>EOP'de sahte zeka içgörüleri

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutuları Exchange Online olmayan Microsoft 365 kuruluşlarda, gelen e-posta iletileri kimlik sahtekarlığına karşı otomatik olarak korunur. EOP, kuruluşunuzun kimlik avına karşı genel savunmasının bir parçası olarak kimlik **sahtekarlığı zekasını** kullanır. Daha fazla bilgi için bkz. [EOP'de kimlik sahtekarlığı koruması](anti-spoofing-protection.md).

Gönderen bir e-posta adresini sahtekarlık ettiğinde, kuruluşunuzun etki alanlarından birinde veya kuruluşunuza e-posta gönderen bir dış etki alanındaki kullanıcı olarak görünür. Gönderenleri istenmeyen posta veya kimlik avı e-postası göndermek üzere sahtekarlık yapan saldırganların engellenmesi gerekir. Ancak, yasal gönderenlerin sahtekarlık yaptığı senaryolar vardır. Örneğin:

- İç etki alanlarını sahtekarlık için geçerli senaryolar:
  - Üçüncü taraf gönderenler, şirket anketleri için kendi çalışanlarınıza toplu posta göndermek için etki alanınızı kullanır.
  - Harici bir şirket sizin yerinize reklam veya ürün güncelleştirmeleri oluşturur ve gönderir.
  - Bir yardımcının düzenli olarak kuruluşunuzdaki başka bir kişi için e-posta göndermesi gerekir.
  - İç uygulama e-posta bildirimleri gönderir.

- Dış etki alanlarını kimlik sahtekarlığına yönelik geçerli senaryolar:
  - Gönderen bir posta listesindedir (tartışma listesi olarak da bilinir) ve posta listesi, özgün gönderenden gelen e-postayı posta listesindeki tüm katılımcılara aktarır.
  - Dış şirket, başka bir şirket (örneğin, otomatik bir rapor veya hizmet olarak yazılım şirketi) adına e-posta gönderir.

Size doğrulanmamış e-posta (SPF, DKIM veya DMARC denetimlerinden geçmeyen etki alanlarından gelen iletiler) yasal olarak gönderen sahte gönderenleri hızla belirlemek ve bu gönderenlere el ile izin vermek için Microsoft 365 Defender portalındaki kimlik sahtekarlığına ilişkin bilgi sahtekarlık **içgörülerini** kullanabilirsiniz.

Bilinen gönderenlerin bilinen konumlardan sahte iletiler göndermesine izin vererek hatalı pozitif sonuçları (kötü olarak işaretlenmiş iyi e-postalar) azaltabilirsiniz. İzin verilen sahte gönderenleri izleyerek, güvenli olmayan iletilerin kuruluşunuza gelmesini önlemek için ek bir güvenlik katmanı sağlarsınız.

Benzer şekilde, kimlik sahtekarlığına izin verilen sahte gönderenleri gözden geçirebilir ve bu gönderenleri sahte zeka içgörülerinden el ile engelleyebilirsiniz.

Bu makalenin geri kalanında, Microsoft 365 Defender portalında ve PowerShell'de (Exchange Online PowerShell'de Exchange Online posta kutuları olan Microsoft 365 kuruluşlar için PowerShell; tek başına EOP PowerShell olmadan kuruluşlar için tek başına EOP PowerShell'in nasıl kullanılacağı açıklanmaktadır Exchange Online posta kutuları).

> [!NOTE]
>
> - Sahte zeka içgörülerinde yalnızca sahte zeka tarafından algılanan sahte gönderenler görünür. İçgörüde izin verme veya engelleme kararını geçersiz kıldığınızda, sahte gönderen yalnızca Kiracı İzin Ver/Engelle Listesi'ndeki **Kimlik Sahtekarı** sekmesinde görünen el ile izin verme veya engelleme girdisine dönüşür. Ayrıca sahte gönderenler için kimlik sahtekarlık zekası tarafından algılanana kadar el ile izin verme veya engelleme girdileri oluşturabilirsiniz. Daha fazla bilgi için bkz. [EOP'de Kiracı İzin Verme/Engelleme Listesini Yönetme](tenant-allow-block-list.md).
>
> - Kiracı İzin Ver/Engelle listesindeki kimlik sahtekarlığı bilgileri içgörüleri ve Kimlik **Sahtekarlığı** sekmesi, Güvenlik & Uyumluluk Merkezi'ndeki istenmeyen posta önleme ilkesi sayfasında bulunan kimlik sahtekarlığı zekası ilkesinin işlevselliğinin yerini alır.
>
>- Sahte zeka içgörüleri 7 günlük verileri gösterir. **Get-SpoofIntelligenceInsight** cmdlet'i 30 günlük verileri gösterir.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com>açarsınız. **Kiracı İzin Ver/Engelle Listesi** sayfasındaki Kimlik **Sahtekarlık** sekmesine doğrudan gitmek için kullanın<https://security.microsoft.com/tenantAllowBlockList?viewid=SpoofItem>. **Doğrudan Spoof intelligence içgörü** sayfasına gitmek için kullanın<https://security.microsoft.com/spoofintelligence>.

- Exchange Online PowerShell'e bağlanmak için bkz. [PowerShell'Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak için bkz. [PowerShell'i Exchange Online Protection için Bağlan](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları gerçekleştirebilmeniz için **önce Exchange Online'de** izinlerin atanmış olması gerekir:
  - Kimlik sahtekarlık zekası ilkesini değiştirmek veya kimlik sahtekarlık zekasını etkinleştirmek veya devre dışı bırakmak için 
    -   **Kuruluş Yönetimi**
    -   **Güvenlik Yöneticisi** <u>ve</u> **Yalnızca Görüntüleme Yapılandırması** veya **Yalnızca Görüntüleme Kuruluş Yönetimi**.
  - Kimlik sahtekarı zeka ilkesine salt okunur erişim için **Genel Okuyucu** veya **Güvenlik Okuyucusu** rol gruplarının üyesi olmanız gerekir.

  Daha fazla bilgi için bkz. [Exchange Online'de İzinler](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - kullanıcıları Microsoft 365 yönetim merkezi karşılık gelen Azure Active Directory rolüne eklemek, kullanıcılara Microsoft 365'deki diğer özellikler için gerekli izinleri _ve_ izinleri verir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  > - [Exchange Online'daki](/Exchange/permissions-exo/permissions-exo#role-groups) **Yalnızca Görüntüleme Kuruluş Yönetimi** rol grubu da özelliğe salt okunur erişim sağlar.

- EOP ve Office 365 için Microsoft Defender kimlik avı önleme ilkelerinde kimlik sahtekarlığı zekasını etkinleştirir ve devre dışı bırakırsınız. Kimlik sahtekarlık zekası varsayılan olarak etkindir. Daha fazla bilgi için bkz. [EOP'de kimlik avı önleme ilkelerini yapılandırma](configure-anti-phishing-policies-eop.md) veya [Office 365 için Microsoft Defender'de kimlik avı önleme ilkelerini yapılandırma](configure-mdo-anti-phishing-policies.md).

- Kimlik sahtekarlığı zekası için önerilen ayarlarımız için bkz. [EOP kimlik avı önleme ilkesi ayarları](recommended-settings-for-eop-and-office365-atp.md#eop-anti-phishing-policy-settings).

## <a name="open-the-spoof-intelligence-insight-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında sahte zeka içgörülerini açma

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **Kurallar** bölümündeki **E-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kiracı İzin Ver/Engelle Listeleri'ne** gidin. **Kiracı İzin Ver/Engelle Listesi** sayfasındaki Kimlik **Sahtekarlık** sekmesine doğrudan gitmek için kullanın<https://security.microsoft.com/tenantAllowBlockList?viewid=SpoofItem>.

2. **Kiracı İzin Ver/Engelle Listeleri** sayfasında kimlik sahtekarlığına ilişkin bilgi sahtekarlık içgörüleri şöyle görünür:

   :::image type="content" source="../../media/m365-sc-spoof-intelligence-insight.png" alt-text="Kimlik avı önleme ilkesi sayfasındaki Kimlik sahtekarlığı zekası içgörüleri" lightbox="../../media/m365-sc-spoof-intelligence-insight.png":::

   İçgörü iki moda sahiptir:

   - **İçgörü modu**: Kimlik sahtekarlık zekası etkinleştirildiyse, içgörü size son yedi gün içinde kimlik sahtekarı zekası tarafından kaç ileti algılandığını gösterir.
   - **Durum modu**: Kimlik sahtekarı zekası devre dışı bırakılırsa, içgörü size son yedi gün içinde kimlik sahtekarı zekası tarafından kaç ileti *algılandığını* gösterir.

Kimlik sahtekarı zekası algılamalarıyla ilgili bilgileri görüntülemek için, kimlik sahtekarlık zekası içgörülerinde Kimlik **sahtekarlık etkinliğini görüntüle'ye** tıklayın.

### <a name="view-information-about-spoofed-messages"></a>Sahte iletiler hakkındaki bilgileri görüntüleme

> [!NOTE]
> Unutmayın, bu sayfada yalnızca kimlik sahtekarı zekası tarafından algılanan sahte gönderenler görünür. İçgörüde izin verme veya engelleme kararını geçersiz kıldığınızda, sahte gönderen yalnızca Kiracı İzin Ver/Engelle Listesi'ndeki **Kimlik Sahtekarı** sekmesinde görünen el ile izin verme veya engelleme girdisine dönüşür.

**Sahte zeka içgörülerinde** Kimlik sahtekarlık **etkinliğini görüntüle'ye** tıkladıktan sonra görüntülenen Kimlik sahtekarı zekası içgörü sayfasında, sayfa aşağıdaki bilgileri içerir:

- **Kimlik sahtekarlığına sahip kullanıcı**: E-posta istemcilerindeki **Kimden** kutusunda görüntülenen sahte kullanıcının **etki alanı**. Kimden adresi, adres olarak `5322.From` da bilinir.
- **Altyapı gönderme**: _Altyapı_ olarak da bilinir. Gönderen altyapı aşağıdaki değerlerden biri olacaktır:
  - Kaynak e-posta sunucusunun IP adresinin ters DNS aramasında (PTR kaydı) bulunan etki alanı.
  - Kaynak IP adresinin PTR kaydı yoksa, gönderen altyapı /24 olarak \<source IP\>tanımlanır (örneğin, 192.168.100.100/24).
- **İleti sayısı**: Son 7 gün içinde sahte etki alanı _ile_ kuruluşunuza gönderilen altyapının birleşiminden gelen iletilerin sayısı.
- **Son görülen**: Sahte etki alanını içeren gönderen altyapıdan iletinin alındığı son tarih.
- **Kimlik sahtekarı türü**: Aşağıdaki değerlerden biri:
  - **İç**: Sahte gönderen, kuruluşunuza ait bir etki alanındadır ( [kabul edilen bir etki alanı](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
  - **Dış**: Sahte gönderen bir dış etki alanında.
- **Eylem**: Bu değer **İzin Verildi** veya **Engellendi**:
  - **İzin verildi**: Etki alanı başarısız olan açık e-posta kimlik doğrulaması [SPF](how-office-365-uses-spf-to-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) ve [DMARC'yi](use-dmarc-to-validate-email.md) denetler. Ancak, etki alanı örtük e-posta kimlik doğrulaması denetimlerimizi ([bileşik kimlik doğrulaması](email-validation-and-authentication.md#composite-authentication)) geçti. Sonuç olarak, iletide kimlik sahtekarlığı önleme eylemi yapılmadı.
  - **Engellendi**: Kimlik sahtekarlığına neden olan etki alanı _ile_ gönderme altyapısının birleşiminden gelen iletiler, kimlik sahtekarı zekası tarafından hatalı olarak işaretlenir. Kimlik sahtekarlığı yapılan iletilerde gerçekleştirilen eylem, varsayılan kimlik avı önleme ilkesi veya özel kimlik avı önleme ilkeleri tarafından denetlenmektedir (varsayılan değer, **İletiyi Gereksiz E-posta klasörüne taşı'dır**). Daha fazla bilgi için bkz. [Office 365 için Microsoft Defender'de kimlik avı önleme ilkelerini yapılandırma](configure-mdo-anti-phishing-policies.md).

Sonuçları sıralamak için seçili sütun başlıklarına tıklayabilirsiniz.

Sonuçları filtrelemek için aşağıdaki seçeneklere sahipsiniz:

- **Filtre** düğmesine tıklayın. Görüntülenen **Filtre** açılır öğesinde sonuçları şu şekilde filtreleyebilirsiniz:
  - **Kimlik sahtekarı türü**
  - **Eylem**
- Sahte etki alanı değerlerinin virgülle ayrılmış bir listesini girmek veya sonuçları filtrelemek için altyapı değerleri göndermek için **Arama** kutusunu kullanın.

### <a name="view-details-about-spoofed-messages"></a>Sahte iletiler hakkındaki ayrıntıları görüntüleme

Listeden bir girdi seçtiğinizde, aşağıdaki bilgileri ve özellikleri içeren bir ayrıntılar açılır öğesi görüntülenir:

- **Kimlik sahtekarlığına izin ver** veya Kimlik **sahtekarlığına engel olmak** için: Özgün kimlik sahtekarlık zekası kararını geçersiz kılmak için bu değerlerden birini seçin ve kimlik sahtekarlığına yönelik bir izin veya engelleme girdisi olarak sahte zeka içgörüsünden girdiyi Kiracı İzin Ver/Engelle Listesi'ne taşıyın.
- Bunu neden yakaladığımızı.
- Yapmanız gerekenler.
- Ana kimlik sahtekarı zeka sayfasındaki bilgilerin çoğunu içeren bir etki alanı özeti.
- WhoIs verileri gönderen hakkında.
- Office 365 için Microsoft Defender'de **Kimlik Avı** **Görüntüle** \> bölümünde gönderen hakkında ek ayrıntıları görmek için [Tehdit Gezgini'ni](threat-explorer.md) açma bağlantısı.
- Kiracınızda aynı gönderenden gelen benzer iletiler.

### <a name="about-allowed-spoofed-senders"></a>İzin verilen sahte gönderenler hakkında

Sahte zeka içgörülerinde izin verilen sahte bir gönderen veya sahtekarlık için el ile **İzin Ver** olarak değiştirdiğiniz engellenmiş sahte gönderen, yalnızca kimlik sahtekarı etki alanı _ile_ gönderen altyapının birleşiminden gelen iletilere izin verir. Herhangi bir kaynaktan kimlik sahtekarı etki alanından gelen e-postaya izin vermez veya herhangi bir etki alanı için gönderen altyapıdan gelen e-postaya izin vermez.

Örneğin, aşağıdaki sahte gönderenin kimlik sahtekarlığına izin verilir:

- **Etki alanı**: gmail.com
- **Altyapı**: tms.mx.com

Yalnızca bu etki alanından/gönderen altyapı çiftinden gelen e-postaların kimlik sahtekarlığına izin verilir. gmail.com sahtekarlık yapmaya çalışan diğer gönderenlere otomatik olarak izin verilmez. Tms.mx.com kaynaklı diğer etki alanlarındaki gönderenlerden gelen iletiler yine kimlik sahtekarlığına göre denetleniyor ve engellenebilir.

## <a name="use-the-spoof-intelligence-insight-in-exchange-online-powershell-or-standalone-eop-powershell"></a>Exchange Online PowerShell veya tek başına EOP PowerShell'de sahte zeka içgörülerini kullanma

PowerShell'de, sahte zeka tarafından algılanan izin verilen ve engellenen sahte gönderenleri **görüntülemek** için **Get-SpoofIntelligenceInsight** cmdlet'ini kullanırsınız. Sahte gönderenlere el ile izin vermek veya engellemek için **New-TenantAllowBlockListSpoofItems** cmdlet'ini kullanmanız gerekir. Daha fazla bilgi için bkz. [Kiracı İzin Ver/Engelle Listesi'ne sahte gönderen girdilerini yönetmek için PowerShell kullanma](tenant-allow-block-list.md).

Bilgi sahtekarlığı içgörülerindeki bilgileri görüntülemek için aşağıdaki komutu çalıştırın:

```powershell
Get-SpoofIntelligenceInsight
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-SpoofIntelligenceInsight](/powershell/module/exchange/get-spoofintelligenceinsight).

## <a name="other-ways-to-manage-spoofing-and-phishing"></a>Kimlik sahtekarlığı ve kimlik avı yönetiminin diğer yolları

Kimlik sahtekarlığı ve kimlik avı koruması konusunda dikkatli olun. Etki alanınızı sahtekarlık yapan gönderenleri denetlemenin ve kuruluşunuza zarar vermelerini önlemeye yardımcı olmanın ilgili yolları şunlardır:

- **Kimlik Sahtekarı Posta Raporu'na bakın**. Sahte gönderenleri görüntülemek ve yönetmeye yardımcı olmak için bu raporu sık sık kullanabilirsiniz. Bilgi için bkz. [Kimlik Sahtekarlık Algılamaları raporu](view-email-security-reports.md#spoof-detections-report).

- Sender Policy Framework (SPF) yapılandırmanızı gözden geçirin. SPF'ye hızlı bir giriş yapmak ve hızla yapılandırılmasını sağlamak için, kimlik [sahtekarlıklarını önlemeye yardımcı olmak için bkz. Microsoft 365'de SPF'yi ayarlama](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Office 365 SPF'yi nasıl kullandığı hakkında daha ayrıntılı bilgi edinmek veya karma dağıtımlar gibi sorun giderme veya standart olmayan dağıtımlar için Office 365 kimlik [sahtekarlığına engel olmak için Sender Policy Framework'ün (SPF) nasıl kullanıldığı](how-office-365-uses-spf-to-prevent-spoofing.md) konusuyla başlayın.

- DomainKeys Identified Mail (DKIM) yapılandırmanızı gözden geçirin. Saldırganların etki alanınızdan geliyormuş gibi görünen iletiler göndermesini önlemeye yardımcı olmak için SPF ve DMARC'ye ek olarak DKIM kullanmalısınız. DKIM, ileti üst bilgisindeki e-posta iletilerine dijital imza eklemenizi sağlar. Bilgi için bkz. [Office 365'da özel etki alanınızdan gönderilen giden e-postayı doğrulamak için DKIM kullanma](use-dkim-to-validate-outbound-email.md).

- Etki Alanı Tabanlı İleti Kimlik Doğrulaması, Raporlama ve Uyumluluk (DMARC) yapılandırmanızı gözden geçirin. SPF ve DKIM ile DMARC uygulamak, kimlik sahtekarlığına ve kimlik avı e-postalarına karşı ek koruma sağlar. DMARC, posta sistemlerinin SPF veya DKIM denetimleri başarısız olan etki alanınızdan gönderilen iletilerle ne yapacağını belirlemesine yardımcı olur. Bilgi için bkz. [Office 365'da e-postayı doğrulamak için DMARC kullanma](use-dmarc-to-validate-email.md).
