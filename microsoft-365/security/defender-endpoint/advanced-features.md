---
title: Uç Nokta için Microsoft Defender'de gelişmiş özellikleri yapılandırma
description: Uç Nokta için Microsoft Defender'da blok dosyası gibi gelişmiş özellikleri açın.
keywords: gelişmiş özellikler, ayarlar, blok dosyası, otomatik araştırma, otomatik çözüm, skype, kimlik için microsoft defender, office 365, azure information protection, intune
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: ac43b62c16cd3e1394cec7a1a75e69bf613757ef
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64934345"
---
# <a name="configure-advanced-features-in-defender-for-endpoint"></a>Uç Nokta için Defender'da gelişmiş özellikleri yapılandırma

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


> Uç Nokta için Defender'ı deneyimlemek mi istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedfeats-abovefoldlink)

Kullandığınız Microsoft güvenlik ürünlerine bağlı olarak, Uç Nokta için Defender'ı ile tümleştirmeniz için bazı gelişmiş özellikler kullanılabilir.

## <a name="enable-advanced-features"></a>Gelişmiş özellikleri etkinleştirme

1. Gezinti bölmesinde **Uç Noktalar** \> **Gelişmiş** **özellikleri'ni Ayarlar** \> seçin.
2. Yapılandırmak istediğiniz gelişmiş özelliği seçin ve ayarı **Açık** ve **Kapalı** arasında değiştirin.
3. **Tercihleri kaydet'e** tıklayın.

Kötü amaçlı olabilecek dosyalardan daha iyi korunmak ve güvenlik araştırmaları sırasında daha iyi içgörü elde etmek için aşağıdaki gelişmiş özellikleri kullanın.

## <a name="automated-investigation"></a>Otomatik araştırma

Hizmetin otomatik araştırma ve düzeltme özelliklerinden yararlanmak için bu özelliği açın. Daha fazla bilgi için bkz. [Otomatik araştırma](automated-investigations.md).

## <a name="live-response"></a>Canlı yanıt

> [!NOTE]
> Canlı yanıt, Uç Nokta için Microsoft Defender portalının gelişmiş ayarlar bölümünde etkinleştirebilmeniz için **otomatik araştırmanın** açılmasını gerektirir.

Uygun izinlere sahip kullanıcıların cihazlarda canlı yanıt oturumu başlatabilmesi için bu özelliği açın.

Rol atamaları hakkında daha fazla bilgi için bkz. [Rol oluşturma ve yönetme](user-roles.md).

## <a name="live-response-for-servers"></a>Sunucular için canlı yanıt

Uygun izinlere sahip kullanıcıların sunucularda canlı yanıt oturumu başlatabilmesi için bu özelliği açın.

Rol atamaları hakkında daha fazla bilgi için bkz. [Rol oluşturma ve yönetme](user-roles.md).

## <a name="live-response-unsigned-script-execution"></a>Canlı yanıt imzasız betik yürütme

Bu özelliği etkinleştirmek, imzalanmamış betikleri canlı yanıt oturumunda çalıştırmanıza olanak tanır.

## <a name="always-remediate-pua"></a>PUA'ya her zaman düzeltme

İstenmeyebilecek uygulamalar (PUA), makinenizin yavaş çalışmasına, beklenmeyen reklamlar görüntülemesine veya en kötü ihtimalle beklenmedik veya istenmeyen olabilecek başka yazılımlar yüklemesine neden olabilecek bir yazılım kategorisidir.

İstenmeyebilecek uygulamaların (PUA) cihazlarda PUA koruması yapılandırılmamış olsa bile kiracınızdaki tüm cihazlarda düzeltilebilmesi için bu özelliği açın. Özelliğin bu şekilde etkinleştirilmesi, kullanıcıların cihazlarına yanlışlıkla istenmeyen uygulamalar yüklemesini önlemektedir. Kapatıldığında düzeltme, cihaz yapılandırmasına bağlıdır.

## <a name="restrict-correlation-to-within-scoped-device-groups"></a>Kapsamı belirlenmiş cihaz gruplarıyla bağıntıyı kısıtlama

Bu yapılandırma, yerel SOC işlemlerinin uyarı bağıntılarını yalnızca erişebilecekleri cihaz gruplarıyla sınırlamak istedikleri senaryolar için kullanılabilir. Bu ayarı açtığınızda, cihazlar arası grupların uyarılardan oluşan bir olay artık tek bir olay olarak kabul edilmez. Yerel SOC daha sonra ilgili cihaz gruplarından birine erişimi olduğundan olay üzerinde işlem yapabilir. Ancak genel SOC, bir olay yerine cihaz grubuna göre birkaç farklı olay görür. Bunu yapmak tüm kuruluş genelinde olay bağıntısının avantajlarından daha fazla olmadığı sürece bu ayarın etkinleştirilmesini önermeyiz.

> [!NOTE]
> Bu ayarın değiştirilmesi yalnızca gelecekteki uyarı bağıntılarını etkiler.

## <a name="enable-edr-in-block-mode"></a>Blok modunda EDR etkinleştirme

Blok modunda uç nokta algılama ve yanıt (EDR), Microsoft Defender Virüsten Koruma pasif modda çalışırken bile kötü amaçlı yapıtlara karşı koruma sağlar. Blok modundaki EDR açıldığında, bir cihazda algılanan kötü amaçlı yapıtları veya davranışları engeller. Blok modundaki EDR, ihlal sonrasında algılanan kötü amaçlı yapıtları düzeltmek için arka planda çalışır.

## <a name="autoresolve-remediated-alerts"></a>Düzeltilmiş uyarıları otomatik olarak çözümleme

Windows 10, sürüm 1809 üzerinde veya sonrasında oluşturulan kiracılar için otomatik araştırma ve düzeltme özelliği, otomatik çözümleme sonucu durumunun "Tehdit bulunamadı" veya "Düzeltildi" olduğu uyarıları çözümlemek için varsayılan olarak yapılandırılır. Uyarıların otomatik olarak çözülmesini istemiyorsanız özelliği el ile kapatmanız gerekir.

> [!TIP]
> Bu sürümden önce oluşturulan kiracılar için bu özelliği [Gelişmiş özellikler](https://security.microsoft.com//preferences2/integration) sayfasından el ile açmanız gerekir.

> [!NOTE]
>
> - Otomatik çözüm eyleminin sonucu, cihazda bulunan etkin uyarıları temel alan Cihaz risk düzeyi hesaplamasını etkileyebilir.
> - Güvenlik işlemleri analisti bir uyarının durumunu el ile "Sürüyor" veya "Çözüldü" olarak ayarlarsa, otomatik çözümleme özelliği bunun üzerine yazılmaz.

## <a name="allow-or-block-file"></a>Dosyaya izin ver veya dosyayı engelle

Engelleme yalnızca kuruluşunuz şu gereksinimleri karşılıyorsa kullanılabilir:

- Etkin kötü amaçlı yazılımdan koruma çözümü olarak Microsoft Defender Virüsten Koruma kullanır ve
- Bulut tabanlı koruma özelliği etkinleştirildi

Bu özellik ağınızdaki kötü amaçlı olabilecek dosyaları engellemenizi sağlar. Bir dosyanın engellenmesi, dosyanın kuruluşunuzdaki cihazlarda okunmasını, yazılmasını veya yürütülmesini engeller.

Dosyalara **izin ver veya dosyaları engelle** seçeneğini açmak için:

1. Gezinti bölmesinde Uç **Noktalar** \> **Genel** \> **Gelişmiş özellikler** \> **dosyaya izin ver veya dosyayı** **engelle'yi Ayarlar** \> seçin.

1. Ayarı **Açık** ve **Kapalı arasında değiştirin**.
 
    :::image type="content" source="../../media/alloworblockfile.png" alt-text="Uç Noktalar ekranı" lightbox="../../media/alloworblockfile.png":::

1. Sayfanın alt kısmındaki **Tercihleri kaydet'i** seçin.

Bu özelliği açtıktan sonra, bir dosyanın profil sayfasındaki **Gösterge Ekle** sekmesi aracılığıyla [dosyaları engelleyebilirsiniz](respond-file-alerts.md#allow-or-block-file).

## <a name="custom-network-indicators"></a>Özel ağ göstergeleri

Bu özelliği açmak IP adresleri, etki alanları veya URL'ler için göstergeler oluşturmanıza olanak tanır. Bu göstergeler, özel gösterge listenize göre izin verilip verilmeyeceğini belirler.

Bu özelliği kullanmak için cihazların Windows 10 sürüm 1709 veya sonraki bir sürümünü veya Windows 11 çalıştırıyor olması gerekir. Ayrıca blok modunda ağ korumasına ve kötü amaçlı yazılımdan koruma platformunun 4.18.1906.3 veya sonraki bir sürümüne [sahip olmaları gerekir. Bkz. KB 4052623](https://go.microsoft.com/fwlink/?linkid=2099834).

Daha fazla bilgi için bkz. [Göstergeleri yönetme](manage-indicators.md).

> [!NOTE]
> Ağ koruması, uç nokta için Defender verileriniz için seçtiğiniz konumun dışında olabilecek konumlarda istekleri işleyen saygınlık hizmetlerinden yararlanıyor.

## <a name="tamper-protection"></a>Kurcalama koruması
Bazı siber saldırılar sırasında kötü aktörler, makinelerinizde virüsten koruma gibi güvenlik özelliklerini devre dışı bırakmaya çalışır. Kötü aktörler verilerinize daha kolay erişim elde etmek, kötü amaçlı yazılım yüklemek veya verilerinizi, kimliğinizi ve cihazlarınızı başka bir şekilde kullanmak için güvenlik özelliklerinizi devre dışı bırakmak ister.

Kurcalama koruması temelde Microsoft Defender Virüsten Koruma kilitler ve güvenlik ayarlarınızın uygulamalar ve yöntemler aracılığıyla değiştirilmesini engeller.

Kuruluşunuz Microsoft Defender Virüsten Koruma kullanıyorsa ve Bulut tabanlı koruma etkinleştirildiyse bu özellik kullanılabilir. Daha fazla bilgi için bkz. [Bulut tabanlı koruma aracılığıyla Microsoft Defender Virüsten Koruma yeni nesil teknolojileri kullanma](cloud-protection-microsoft-defender-antivirus.md).

Güvenlik çözümünüzde ve temel özelliklerinde istenmeyen değişiklikleri önlemek için kurcalama korumasını açık tutun.

## <a name="show-user-details"></a>Kullanıcı ayrıntılarını göster

Azure Active Directory'de depolanan kullanıcı ayrıntılarını görebilmek için bu özelliği açın. Ayrıntılar, kullanıcı hesabı varlıklarını araştırırken kullanıcının resmi, adı, başlığı ve departman bilgilerini içerir. Kullanıcı hesabı bilgilerini aşağıdaki görünümlerde bulabilirsiniz:

- Güvenlik işlemleri panosu
- Uyarı kuyruğu
- Cihaz ayrıntıları sayfası

Daha fazla bilgi için bkz [. Kullanıcı hesabını araştırma](investigate-user.md).

## <a name="skype-for-business-integration"></a>Skype Kurumsal tümleştirmesi

Skype Kurumsal tümleştirmesini etkinleştirmek, kullanıcılarla Skype Kurumsal, e-posta veya telefon kullanarak iletişim kurmanızı sağlar. Bu etkinleştirme, kullanıcıyla iletişim kurmanız ve riskleri azaltmanız gerektiğinde kullanışlı olabilir.

> [!NOTE]
> Bir cihaz ağdan yalıtılırken, Outlook ve Skype iletişimlerini etkinleştirmeyi seçebileceğiniz bir açılır pencere vardır ve bu da ağ bağlantısı kesildiği sırada kullanıcıyla iletişim kurmasına olanak tanır. Bu ayar, cihazlar yalıtım modundayken Skype ve Outlook iletişim için geçerlidir.

## <a name="microsoft-defender-for-identity-integration"></a>Kimlik için Microsoft Defender tümleştirmesi

Kimlik için Microsoft Defender ile tümleştirme, doğrudan başka bir Microsoft Identity güvenlik ürününe özetlemenizi sağlar. Kimlik için Microsoft Defender, güvenliği aşılmış olduğundan şüphelenilen bir hesap ve ilgili kaynaklar hakkında daha fazla içgörüyle bir araştırmayı genişletmektedir. Bu özelliği etkinleştirerek, ağ genelinde tanımlama açısından özetleyerek cihaz tabanlı araştırma özelliğini zenginleştireceksiniz.

> [!NOTE]
> Bu özelliği etkinleştirmek için uygun lisansa sahip olmanız gerekir.

## <a name="office-365-threat-intelligence-connection"></a>Office 365 Tehdit Bilgileri bağlantısı

Bu özellik yalnızca etkin bir Office 365 E5 veya Tehdit Bilgileri eklentiniz varsa kullanılabilir. Daha fazla bilgi için Office 365 Kurumsal E5 ürün sayfasına bakın.

Bu özelliği açtığınızda, Office 365 posta kutuları ve Windows cihazları arasında kapsamlı bir güvenlik araştırması yürütmek için Office 365 için Microsoft Defender verileri Microsoft 365 Defender birleştirebileceksiniz.

> [!NOTE]
> Bu özelliği etkinleştirmek için uygun lisansa sahip olmanız gerekir.

Office 365 Tehdit Bilgileri'nde bağlamsal cihaz tümleştirmesi almak için Güvenlik & Uyumluluğu panosunda Uç Nokta için Defender ayarlarını etkinleştirmeniz gerekir. Daha fazla bilgi için bkz [. Tehdit araştırması ve yanıtı](/microsoft-365/security/office-365-security/office-365-ti).

## <a name="microsoft-threat-experts---targeted-attack-notifications"></a>Microsoft Tehdit Uzmanları - Hedefli Saldırı Bildirimleri

İki Microsoft Tehdit Uzmanı bileşeninden hedeflenen saldırı bildirimi genel kullanıma hazır durumdadır. İsteğe bağlı uzmanlar özelliği hala önizleme aşamasındadır. İsteğe bağlı uzmanlar özelliğini yalnızca önizleme için başvurduysanız ve uygulamanız onaylandıysa kullanabilirsiniz. Hedeflenen saldırı bildirimlerini Microsoft Tehdit Uzmanları Uç Nokta için Defender portalınızın uyarılar panosu aracılığıyla ve yapılandırdığınızda e-posta yoluyla alabilirsiniz.

> [!NOTE]
> Uç Nokta için Defender'daki Microsoft Tehdit Uzmanları özelliği, [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) için E5 lisansıyla kullanılabilir.

## <a name="microsoft-defender-for-cloud-apps"></a>Bulut Uygulamaları için Microsoft Defender

Bu ayarın etkinleştirilmesi, bulut uygulaması kullanımına daha ayrıntılı görünürlük sağlamak için Uç Nokta için Defender sinyallerini Microsoft Defender for Cloud Apps iletir. İletilen veriler, Bulut için Defender Uygulamaları verilerinizle aynı konumda depolanır ve işlenir.

> [!NOTE]
> Bu özellik[, Windows 10](https://www.microsoft.com/cloud-platform/enterprise-mobility-security), sürüm 1709 (KB4493441 ile İs Derlemesi 16299.1085), Windows 10, sürüm 1803 ([KB4493464](https://support.microsoft.com/help/4493441) ile İs Derlemesi 17134.704), Windows 10, sürüm 1809 çalıştıran cihazlarda Enterprise Mobility + Security için bir E5 lisansı ile kullanılabilir [](https://support.microsoft.com/help/4493464)  ([KB4489899](https://support.microsoft.com/help/4489899) ile İs Derlemesi 17763.379), sonraki Windows 10 sürümleri veya Windows 11.

### <a name="enable-the-microsoft-defender-for-endpoint-integration-from-the-microsoft-defender-for-identity-portal"></a>Kimlik için Microsoft Defender portalından Uç Nokta için Microsoft Defender tümleştirmesini etkinleştirme

Kimlik için Microsoft Defender'da bağlamsal cihaz tümleştirmesi almak için özelliği Kimlik için Microsoft Defender portalında da etkinleştirmeniz gerekir.

1. [Kimlik için Microsoft Defender portalında](https://portal.atp.azure.com/) Genel Yönetici veya Güvenlik Yöneticisi rolüyle oturum açın.

2. **Örneğinizi oluşturun'a** tıklayın.

3. Tümleştirme ayarını **Açık** olarak değiştirin ve **Kaydet'e** tıklayın.

Her iki portaldaki tümleştirme adımlarını tamamladıktan sonra cihaz ayrıntıları veya kullanıcı ayrıntıları sayfasında ilgili uyarıları görebilirsiniz.

## <a name="web-content-filtering"></a>Web içeriği filtreleme

İstenmeyen içerik içeren web sitelerine erişimi engelleyin ve tüm etki alanlarındaki web etkinliğini izleyin. Engellemek istediğiniz web içeriği kategorilerini belirtmek için bir [web içeriği filtreleme ilkesi](https://security.microsoft.com/preferences2/web_content_filtering_policy) oluşturun. [Uç Nokta için Microsoft Defender güvenlik temelini](https://devicemanagement.microsoft.com/#blade/Microsoft_Intune_Workflows/SecurityBaselineSummaryMenu/overview/templateType/2) dağıtırken blok modunda ağ korumasına sahip olduğunuzdan emin olun.

## <a name="share-endpoint-alerts-with-microsoft-purview-compliance-portal"></a>Microsoft Purview uyumluluk portalı ile uç nokta uyarılarını paylaşma

Uç nokta güvenlik uyarılarını ve öncelik durumlarını Microsoft Purview uyumluluk portalına ileterek iç risk yönetimi ilkelerini uyarılarla geliştirmenize ve iç riskleri zarara neden olmadan önce düzeltmenize olanak sağlar. İletilen veriler işlenir ve Office 365 verilerinizle aynı konumda depolanır.

Insider risk yönetimi ayarlarında [Güvenlik ilkesi ihlal göstergeleri](/microsoft-365/compliance/insider-risk-management-settings#indicators) yapılandırıldıktan sonra, Uç Nokta için Defender uyarıları ilgili kullanıcılar için iç risk yönetimiyle paylaşılır.

## <a name="microsoft-intune-connection"></a>Microsoft Intune bağlantısı

Uç Nokta için Defender, [cihaz risk tabanlı koşullu erişimi etkinleştirmek](/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune) için [Microsoft Intune](/intune/what-is-intune) ile tümleştirilebilir. [Bu özelliği açtığınızda](configure-conditional-access.md), uç nokta için Defender cihaz bilgilerini Intune paylaşarak ilke zorlamasını geliştirebilirsiniz.

> [!IMPORTANT]
> Bu özelliği kullanmak için hem Intune hem de Uç Nokta için Defender'da tümleştirmeyi etkinleştirmeniz gerekir. Belirli adımlar hakkında daha fazla bilgi için bkz. [Uç Nokta için Defender'da Koşullu Erişimi Yapılandırma](configure-conditional-access.md).

Bu özellik yalnızca aşağıdaki önkoşullara ihtiyacınız varsa kullanılabilir:

- Enterprise Mobility + Security E3 ve Windows E5 (veya Microsoft 365 Kurumsal E5) için lisanslı kiracı
- [Azure AD'ye katılmış](/azure/active-directory/devices/concept-azure-ad-join/) Intune yönetilen Windows cihazlarıyla etkin bir Microsoft Intune ortamı.

### <a name="conditional-access-policy"></a>Koşullu Erişim ilkesi

Intune tümleştirmeyi etkinleştirdiğinizde, Intune otomatik olarak bir klasik Koşullu Erişim (CA) ilkesi oluşturur. Bu klasik CA ilkesi, durum raporlarını Intune olarak ayarlamak için bir önkoşuldur. Silinmemelidir.

> [!NOTE]
> Intune tarafından oluşturulan klasik CA ilkesi, uç noktaları yapılandırmak için kullanılan modern [Koşullu Erişim ilkelerinden](/azure/active-directory/conditional-access/overview/) farklıdır.

## <a name="device-discovery"></a>cihaz keşfi

Ek gereçlere veya hantal işlem değişikliklerine gerek kalmadan kurumsal ağınıza bağlı yönetilmeyen cihazları bulmanıza yardımcı olur. Eklenen cihazları kullanarak ağınızda yönetilmeyen cihazları bulabilir, güvenlik açıklarını ve riskleri değerlendirebilirsiniz. Daha fazla bilgi için bkz [. Cihaz bulma](device-discovery.md).

> [!NOTE]
> Yönetilmeyen cihazları cihaz envanter listesinden dışlamak için istediğiniz zaman filtre uygulayabilirsiniz. Yönetilmeyen cihazları filtrelemek için API sorgularında ekleme durumu sütununu da kullanabilirsiniz.

## <a name="preview-features"></a>Özellikleri önizleyin

Uç Nokta için Defender önizleme sürümündeki yeni özellikler hakkında bilgi edinin. Önizleme deneyimini açarak yaklaşan özellikleri deneyin.

Özellikler genel kullanıma sunulmadan önce genel deneyimi iyileştirmeye yardımcı olmak için geri bildirim sağlayabileceğiniz yaklaşan özelliklere erişebilirsiniz.

## <a name="download-quarantined-files"></a>Karantinaya alınan dosyaları indirme

Karantinaya alınan dosyaları doğrudan karantinadan indirilebilmeleri için güvenli ve uyumlu bir konumda yedekleyin. **Dosyayı indir** düğmesi her zaman dosya sayfasında kullanılabilir. Bu ayar varsayılan olarak açıktır. [Gereksinimler hakkında daha fazla bilgi edinin](respond-file-alerts.md#download-quarantined-files)

## <a name="related-topics"></a>İlgili konular

- [Veri saklama ayarlarını güncelleştirme](data-retention-settings.md)
- [Uyarı bildirimlerini yapılandırın](configure-email-notifications.md)
