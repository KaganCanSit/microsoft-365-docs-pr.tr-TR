---
title: Web'de gelişmiş özellikleri Uç Nokta için Microsoft Defender
description: Dosya engelleme gibi gelişmiş özellikleri Uç Nokta için Microsoft Defender.
keywords: gelişmiş özellikler, ayarlar, dosya engelleme, otomatik soruşturma, otomatik çözümleme, skype, kimlik için Microsoft Defender, Office 365, azure information protection, intune
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
ms.openlocfilehash: 94e5b18ab1090f6fb76cb7734e90411b93b444e7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465465"
---
# <a name="configure-advanced-features-in-defender-for-endpoint"></a>Uç Nokta için Defender'da gelişmiş özellikleri yapılandırma

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedfeats-abovefoldlink)

Kullandığınız Microsoft güvenlik ürünlerine bağlı olarak, Uç Nokta için Defender'ı tümleşik olarak kullanabileceğiniz bazı gelişmiş özellikler kullanılabilir.

## <a name="enable-advanced-features"></a>Gelişmiş özellikleri etkinleştirme

1. Gezinti bölmesinde, Uç Noktaları **Gelişmiş** **Ayarlar'ı** \> \> **seçin**.
2. Yapılandırmak istediğiniz gelişmiş özelliği seçin ve ayarı Açık ile Kapalı **arasında** **geçişin.**
3. Kaydetme **tercihleri'ne tıklayın**.

Kötü amaçlı olabilecek dosyalardan daha iyi korunacak ve güvenlik soruşturmaları sırasında daha iyi fikir edinebilecek aşağıdaki gelişmiş özellikleri kullanın.

## <a name="automated-investigation"></a>Otomatik araştırma

Hizmetin otomatik araştırma ve düzeltme özelliklerinden yararlanmak için bu özelliği kullanın. Daha fazla bilgi için bkz [. Otomatik araştırma](automated-investigations.md).

## <a name="live-response"></a>Canlı yanıt

> [!NOTE]
> Canlı yanıt için **, hızlı araştırmanın** portalında yer alan gelişmiş ayarlar bölümünde etkinleştiremeden önce otomatik Uç Nokta için Microsoft Defender gerekir.

Uygun izinlere sahip kullanıcıların cihazlarda canlı yanıt oturumu başlat olması için bu özelliği kullanın.

Rol atamaları hakkında daha fazla bilgi için bkz. [Rol oluşturma ve yönetme](user-roles.md).

## <a name="live-response-for-servers"></a>Sunucular için canlı yanıt

Uygun izinlere sahip kullanıcıların sunucularda canlı yanıt oturumu başlatması için bu özelliği kullanın.

Rol atamaları hakkında daha fazla bilgi için bkz. [Rol oluşturma ve yönetme](user-roles.md).

## <a name="live-response-unsigned-script-execution"></a>Canlı yanıt imzalanmamış betik yürütme

Bu özelliğin etkinleştirilmesi, imzasız betikleri canlı yanıt oturumunda çalıştırmaya olanak sağlar.

## <a name="always-remediate-pua"></a>PUA'yı her zaman düzeltmek

İstenmeyen olabilecek uygulamalar (PUA), makinenizin yavaş çalışmasına, beklenmeyen reklamlar görüntülemesine veya en kötü de kötü de, beklenmedik veya istenmeyen başka bir yazılım yüklemesine neden olabilecek bir yazılım kategorisidir.

İstenmeyen olabilecek uygulamaların (PUA) cihazlarında PUA koruması yapılandırılmasa bile kiracınız dahil tüm cihazlarda düzeltilesini açmak için bu özelliği kullanın. Bu özelliğin etkinleştirilmesi, kullanıcıların cihazlarında istemeden istenmeyen uygulamalar yüklemelerini korumanıza yardımcı olur. Kapalı olduğunda, düzeltme cihaz yapılandırmasına bağlıdır.

## <a name="restrict-correlation-to-within-scoped-device-groups"></a>Kapsamı olan cihaz grupları içinde bağıntıyı kısıtlama

Bu yapılandırma, yerel SOC işlemlerinin uyarı korelasyonlarını yalnızca eriştikleri cihaz gruplarıyla sınırlandırmak kullandığı senaryolarda kullanılabilir. Bu ayarın açmasıyla, cihaz arası grupların uyarılardan oluşan bir olay artık tek bir olay olarak kabul edilir. Bundan sonra yerel SOC ilgili cihaz gruplarından birinin erişimi olduğundan olay üzerinde eyleme geçebilirsiniz. Bununla birlikte, genel SOC tek bir olay yerine cihaz grubuna göre birkaç farklı olayı görebilir. Bu ayarın, kuruluş genelinde olay korelasyon avantajlarının üzerinde bir öte öteye geçediği sürece, bu ayarı açmama öneririz.

> [!NOTE]
> Bu ayarın değiştirilmesi yalnızca gelecekteki uyarı korelasyonlarını etkiler.

## <a name="enable-edr-in-block-mode"></a>EDR modunda etkinleştirme

Engelleme modunda uç nokta EDR (uç nokta) ve yanıt, pasif modunda çalışan Microsoft Defender Virüsten Koruma kötü amaçlı yapılardan koruma sağlar. Açık olduğunda, EDR modundaki kodlar bir cihazda algılanan kötü amaçlı yapıları veya davranışları engeller. EDR modundaki düzeltmeler, ihlal sonrası algılanan kötü amaçlı yapıları düzeltmek için perde arkasında çalışır.

## <a name="autoresolve-remediated-alerts"></a>Düzelten otomatik düzeltme uyarıları

Windows 10, sürüm 1809'ta veya sonrasında oluşturulan kiracılar için, otomatik araştırma ve düzeltme özelliği varsayılan olarak otomatik çözümleme sonucu durumunun "Tehdit bulunamadı" veya "Düzeltildi" olduğu uyarıları çözümlemek üzere yapılandırılır. Uyarıların otomatik olarak çözümlenmiş olarak çözülmesini istemiyorsanız, özelliği el ile kapatmanız gerekir.

> [!TIP]
> Bu sürümden önce oluşturulan kiracılar için, Gelişmiş özellikler sayfasından bu özelliği el ile [açmalısınız](https://security.microsoft.com//preferences2/integration) .

> [!NOTE]
>
> - Otomatik çözme eyleminin sonucu, cihazda bulunan etkin uyarıları temel alan Cihaz risk düzeyi hesaplamasına etki ediyor olabilir.
> - Güvenlik işlemleri analisti uyarının durumunu "Sürüyor" veya "Çözümlendi" olarak el ile ayarlarsa, otomatik çözme özelliği üzerine yazmaz.

## <a name="allow-or-block-file"></a>Dosyaya izin verme veya dosyayı engelleme

Engelleme, yalnızca kuruluş şu gereksinimleri karşılarsa kullanılabilir:

- Microsoft Defender Virüsten Koruma kötü amaçlı yazılımdan koruma çözümü olarak bu çözümü kullanır ve
- Bulut tabanlı koruma özelliği etkin

Bu özellik, ağda olabilecek kötü amaçlı dosyaları engellemenize olanak sağlar. Bir dosyayı engellemek, okunmalarını, yazıldıklarını veya kuruluşta yürütülürler.

Dosyalara izin **ver veya engelle'ye izin** ver veya engelle'ye açmak için:

1. Gezinti bölmesinde, Genel Gelişmiş **Ayarlar** \> **dosyaya izin ver** \> **veya** \> **engelle'yi** \> **seçin**.

1. Ayarı Açık ve Kapalı **arasında** **geçiş yapmak.**
 
    :::image type="content" source="../../media/alloworblockfile.png" alt-text="Uç noktalar ekranı" lightbox="../../media/alloworblockfile.png":::

1. Sayfanın **en altındaki** Kaydetme tercihleri'ne tıklayın.

Bu özelliği verdikten sonra, [dosyanın](respond-file-alerts.md#allow-or-block-file) profil sayfasındaki **Gösterge** Ekle sekmesi aracılığıyla dosyaları engelleyebilirsiniz.

## <a name="custom-network-indicators"></a>Özel ağ göstergeleri

Bu özelliğin gerçekleştirilebilir olması, özel gösterge listeniz üzerinden IP adresleri, etki alanları veya URL'ler için göstergeler oluşturmanıza olanak sağlar.

Bu özelliği kullanmak için cihazların 1709 veya Windows 10 sonraki bir sürümde veya daha sonraki bir sürümde Windows 11. Ayrıca, engelleme modunda ve kötü amaçlı yazılım önleme platformunun 4.18.1906.3 veya daha sonraki bir sürümünde ağ korumasına sahip [olması gerekir, bkz. KB 4052623](https://go.microsoft.com/fwlink/?linkid=2099834).

Daha fazla bilgi için bkz [. Göstergeleri yönetme](manage-indicators.md).

> [!NOTE]
> Ağ koruması, Uç nokta verileri için Defender'nız için seçtiğiniz konumun dışında yer alan konumlarda istekleri işlemeye devam ediyor olan saygın hizmetlerden faydalanan bir hizmettir.

## <a name="tamper-protection"></a>Tamper protection
Bazı siber saldırı türleri sırasında, kötü saldırılar makinelerde virüsten koruma gibi güvenlik özelliklerini devre dışı bırakmayı dener. Verilerinize daha kolay erişim elde etmek, kötü amaçlı yazılım yüklemek veya verilerinizden, kimliklerinize ve cihazlarınıza başka bir şekilde istismar etmek için güvenlik özelliklerinizi devre dışı bırakmak gibi kötü bir şey.

Tamper protection temelde dış Microsoft Defender Virüsten Koruma kilitler ve güvenlik ayarlarınızın uygulamalar ve yöntemler aracılığıyla değiştirilmesini önlemeye yardımcı olur.

Bu özellik, bulut tabanlı koruma Microsoft Defender Virüsten Koruma etkinleştirildiğinde kullanılabilir. Daha fazla bilgi için bkz[. Bulut teslimi koruma Microsoft Defender Virüsten Koruma yeni nesil teknolojileri kullanma](cloud-protection-microsoft-defender-antivirus.md).

Güvenlik çözümünüzde ve önemli özelliklerinde istenmeyen değişiklikleri önlemek için değiştirilme korumasının açık kalsın.

## <a name="show-user-details"></a>Kullanıcı ayrıntılarını göster

Dosyada depolanan kullanıcı ayrıntılarını görmek için bu özelliği Azure Active Directory. Ayrıntılar kullanıcının hesap varlıklarını incelerken resmi, adı, unvanı ve bölüm bilgilerini içerir. Kullanıcı hesabı bilgilerini aşağıdaki görünümlerde bulabilirsiniz:

- Güvenlik işlemleri panosu
- Uyarı sırası
- Cihaz ayrıntıları sayfası

Daha fazla bilgi için bkz [. Kullanıcı hesabını araştırma](investigate-user.md).

## <a name="skype-for-business-integration"></a>Skype Kurumsal tümleştirmesi

Skype Kurumsal tümleştirmeyi etkinleştirmek, e-posta, telefon veya telefon Skype Kurumsal kullanıcılarla iletişim kurma olanağı sağlar. Bu etkinleştirme, kullanıcıyla iletişim kurmanız ve riskleri azaltmak için kullanışlıdır.

> [!NOTE]
> Cihaz ağdan yalıtılmış durumdayken, Outlook ve Skype iletişimlerini etkinleştirmeyi seçebilirsiniz ve bu da ağ bağlantısı kesildiğinde kullanıcıyla iletişimleri sağlar. Bu ayar, Skype yalıtım Outlook olduğunda iletişimi otomatik olarak yapmak için geçerlidir.

## <a name="microsoft-defender-for-identity-integration"></a>Kimlik için Microsoft Defender tümleştirmesi

Microsoft Hesabı ile Kimlik için Microsoft Defender, doğrudan başka bir Microsoft Identity güvenlik ürününe özetlemenizi sağlar. Kimlik için Microsoft Defender ele geçirildikleri hesap ve ilgili kaynaklar hakkında daha fazla içgörü elde edilen bir soruşturmayı geliştirler. Bu özelliği etkinleştirerek, ağı tanımlama açısından bir bakış açısından özetleerek cihaz tabanlı soruşturma özelliğini zenginleştirirsiniz.

> [!NOTE]
> Bu özelliği etkinleştirmek için uygun lisansa sahip olmak gerekir.

## <a name="office-365-threat-intelligence-connection"></a>Office 365 Tehdit İstihbaratı bağlantısı

Bu özelliğin kullanılabilir olması için, etkin bir Office 365 E5 veya Tehdit İstihbaratı eklentisinde olması gerekir. Daha fazla bilgi için, Office 365 Kurumsal E5 ürün sayfasına bakın.

Bu özelliği kapatarak, posta kutuları ve diğer cihazlarınız arasında kapsamlı bir güvenlik Office 365 için Microsoft Defender yapmak için Microsoft 365 Defender'den Office 365 verileri Windows.

> [!NOTE]
> Bu özelliği etkinleştirmek için uygun lisansa sahip olmak gerekir.

Threat Intelligence içinde bağlamsal cihaz tümleştirmesi Office 365 için Güvenlik ve Uyumluluk panosunda Uç Nokta için Defender ayarlarını etkinleştirmeniz & gerekir. Daha fazla bilgi için bkz [. Tehdit soruşturması ve yanıtı](/microsoft-365/security/office-365-security/office-365-ti).

## <a name="microsoft-threat-experts---targeted-attack-notifications"></a>Microsoft Tehdit Uzmanları - Hedefli Saldırı Bildirimleri

İki Microsoft Tehdit Uzmanı bileşeninden biri, hedefli saldırı bildirimi genel olarak kullanılabilir. Uzmanlara özel isteğe bağlı özellik hala önizlemede. Uzman isteğe bağlı özelliğini, yalnızca önizleme için uyguladınız ve başvurunız onaylandı ise kullanabilirsiniz. Hedefli saldırı bildirimlerini, Microsoft Tehdit Uzmanları portalının uyarılar için Defender panosu üzerinden ve yapılandırdıysanız e-posta yoluyla alırsınız.

> [!NOTE]
> Uç Microsoft Tehdit Uzmanları için Defender'daki diğer özellik, E5 lisansı ile kullanılabilir [ve Enterprise Mobility + Security.](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)

## <a name="microsoft-defender-for-cloud-apps"></a>Bulut Uygulamaları için Microsoft Defender

Bu ayarın etkinleştirilmesi, bulut uygulama kullanımında daha derin bir görünürlük Microsoft Defender for Cloud Apps için Uç nokta işaretleri için Defender'ı iletin. Forwarded data is stored and processed in the location as your Bulut için Defender data.

> [!NOTE]
> Bu özellik [KB4493441](https://support.microsoft.com/help/4493441)), [Windows 10](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) sürüm 1803 (KB4493464 ile birlikte işletim sistemi derlemesi 17134.704 ile Windows 10 sürüm 17134.704) ile çalışan cihazlarda Enterprise Mobility + Security için E5 lisansıyla birlikte Windows 10, sürüm 1809 [](https://support.microsoft.com/help/4493464)  ([KB4489899](https://support.microsoft.com/help/4489899) ile birlikte işletim sistemi derlemesi 17763.379), daha sonraki Windows 10 sürümleri veya Windows 11.

### <a name="enable-the-microsoft-defender-for-endpoint-integration-from-the-microsoft-defender-for-identity-portal"></a>Uç Nokta için Microsoft Defender Kimlik için Microsoft Defender portaldan Kimlik için Microsoft Defender tümleştirmeyi etkinleştirme

Kimlik için Microsoft Defender'da bağlamsal cihaz tümleştirmesi almak için, bu özelliği etkinleştirmeniz için portalda da Kimlik için Microsoft Defender gerekir.

1. Portalda Genel [Kimlik için Microsoft Defender veya](https://portal.atp.azure.com/) Güvenlik Yöneticisi rolüyle oturum açın.

2. **Örneğinizi oluşturun'a tıklayın**.

3. Tümleştirme ayarını Açık olarak açıp **Kaydet'e** **tıklayın**.

Her iki portalda tümleştirme adımlarını tamamladıktan sonra, cihaz ayrıntılarında veya kullanıcı ayrıntıları sayfasında ilgili uyarıları görebilirsiniz.

## <a name="web-content-filtering"></a>Web içeriği filtreleme

İstenmeyen içerik içeren web sitelerine erişimi engelin ve tüm etki alanları genelinde web etkinliğini takip edin. Engellemek istediğiniz web içeriği kategorilerini belirtmek için, web içeriği filtreleme [ilkesi oluşturun](https://security.microsoft.com/preferences2/web_content_filtering_policy). Bu güvenlik temeli dağıtımında engelleme modunda ağ Uç Nokta için Microsoft Defender [emin olun](https://devicemanagement.microsoft.com/#blade/Microsoft_Intune_Workflows/SecurityBaselineSummaryMenu/overview/templateType/2).

## <a name="share-endpoint-alerts-with-microsoft-compliance-center"></a>Uç nokta uyarılarını Microsoft Uyumluluk Merkezi ile paylaşma

Uç nokta güvenlik uyarılarını ve bunların üç durumlarını Microsoft Uyumluluk Merkezi'ne iletir, uyarılarla insider risk yönetimi ilkelerini geliştirmenizi ve zarara neden olmadan önce iç riskleri düzeltmenizi sağlar. Forwarded data is processed and stored in the location as your Office 365.

Insider risk yönetimi ayarlarında Güvenlik ilkesi [ihlal](/microsoft-365/compliance/insider-risk-management-settings#indicators) göstergelerini yapılandırdikten sonra, Uç Nokta uyarıları için Defender, ilgili kullanıcılar için Insider risk yönetimiyle paylaşılır.

## <a name="microsoft-intune-connection"></a>Microsoft Intune bağlantı

Cihaz risk tabanlı koşullu erişimi etkinleştirmek için [Microsoft Intune](/intune/what-is-intune) için Defender [ile Uç Nokta için Defender tümleştirildi](/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune). Bu [özelliği etkinleştirirken, ilke zorlamayı](configure-conditional-access.md) geliştirmek için Uç nokta cihaz bilgileri için Defender'ı Intune bilgileri paylaşabilirsiniz.

> [!IMPORTANT]
> Bu özelliği kullanmak için hem Uç Nokta için Intune Defender'da tümleştirmeyi etkinleştirmeniz gerekir. Belirli adımlar hakkında daha fazla bilgi için bkz. [Uç Nokta için Defender'da Koşullu Erişimi Yapılandırma](configure-conditional-access.md).

Bu özellik yalnızca aşağıdaki önkoşullara sahipsanız kullanılabilir:

- E5 ve E5 için Enterprise Mobility + Security E3 kiracı Windows (veya Microsoft 365 Kurumsal E5)
- Azure AD Microsoft Intune tarafından yönetilen veya Intune cihaz Windows etkin [bir etki alanı ortamı](/azure/active-directory/devices/concept-azure-ad-join/).

### <a name="conditional-access-policy"></a>Koşullu Erişim ilkesi

Dış tümleştirmeyi etkinleştir Intune, Intune otomatik olarak klasik bir Koşullu Erişim (CA) ilkesi oluşturulur. Bu klasik CA ilkesi, bu ilkeye durum raporlarını ayarlamanın önkoşul Intune. Silinmemelidir.

> [!NOTE]
> Intune tarafından oluşturulan klasik CA ilkesi, uç noktaları yapılandırmak [için](/azure/active-directory/conditional-access/overview/) kullanılan modern Koşullu Erişim ilkelerinden farklıdır.

## <a name="device-discovery"></a>Cihaz bulma

Ek cihazlara veya zahmetli süreç değişikliklerine gerek kalmadan şirket ağınıza bağlı, yönetimsiz cihazları bu şekilde bulmanızı sağlar. Yerleşik cihazları kullanarak ağ bağlantınız için yönelik olmayan cihazları bulabilir, güvenlik açıklarını ve riskleri değerlendirebilirsiniz. Daha fazla bilgi için bkz. [Cihaz bulma](device-discovery.md).

> [!NOTE]
> Yönetimi olmayan cihazları cihaz stok listesinden dışarıda tutmak için her zaman filtre uygulayabilirsiniz. Ayrıca, yönetimi olmayan cihazları filtrelemek için API sorgularında ekleme durumu sütununu da kullanabilirsiniz.

## <a name="preview-features"></a>Önizleme özellikleri

Uç nokta için Defender önizleme sürümüne sahip yeni özellikler hakkında bilgi öğrenin. Önizleme deneyimini yükerek yaklaşan özellikleri deneyin.

Yaklaşan özelliklere erişebilirsiniz ve bu erişimde, özellikler genel kullanıma başlamadan önce genel deneyimi iyileştirmeye yardımcı olmak için geri bildirim sebilirsiniz.

## <a name="download-quarantined-files"></a>Karantinaya alınmış dosyaları indirme

Karantinaya alınan dosyaları güvenli ve uyumlu bir konuma yedekler, böylece bunlar doğrudan karantinadan indirilebilir. Dosyayı **indir** düğmesi her zaman dosya sayfasında kullanılabilir. Bu ayar varsayılan olarak açıktır. [Gereksinimler hakkında daha fazla bilgi](respond-file-alerts.md#download-quarantined-files)

## <a name="related-topics"></a>İlgili konular

- [Veri bekletme ayarlarını güncelleştirme](data-retention-settings.md)
- [Uyarı bildirimlerini yapılandırma](configure-email-notifications.md)
