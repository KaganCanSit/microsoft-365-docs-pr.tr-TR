---
title: Microsoft 365 Defender MDO, MDE, MDI ve MCAS birleştirmeye genel bakış
description: Microsoft Defender Microsoft 365 Defender (MDI) ve kimlik için Microsoft Defender (MCAS) ile Office 365 için Microsoft Defender (MDO Microsoft Cloud App Security) ile Uç Nokta için Microsoft Defender'ı birleştirmenin avantajları. Bu makalede, yöneticilere Microsoft 365 Defender durumların ana hatlarıyla açıklanmıştır.
keywords: güvenlik, kötü amaçlı yazılım, Microsoft 365, M365, güvenlik merkezi, izleme, rapor, kimlikler, veriler, cihazlar, uygulamalar
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.date: 04/21/2021
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid: met150
ms.custom: seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: a0dce3a61847924043a10df4c13c963f279ea011
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2021
ms.locfileid: "62989999"
---
# <a name="microsoft-365-defender-overview"></a>Microsoft 365 Defender genel bakış

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Office 365 için Microsoft Defender](/microsoft-365/security/office-365-security/defender-for-office-365)

> Bu deneyimi Microsoft 365 Defender? Bunu bir [laboratuvar ortamında değerlendirin veya](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) [üretimde pilot projenizi çalıştırın](m365d-pilot.md?ocid=cx-evalpilot).

**Microsoft 365 Defender** ([https://security.microsoft.com](https://security.microsoft.com)) merkezi bir portalda e-postaya, işbirliğine *, kimlike* ve cihaz tehditlerine karşı *koruma, algılama*, soruşturma ve yanıt verir.

Microsoft 365 Defender, var olan Microsoft güvenlik portallarından (Microsoft Defender Güvenlik Merkezi ve Office 365 Güvenlik ve Uyumluluk merkezi gibi& bir araya getirir. Güvenlik merkezi bilgilere hızlı erişimi, daha basit düzenleri vurgular ve daha kolay kullanım için ilgili bilgileri bir araya getirir. Bu merkez şunları içerir:

- Office 365 **[için Microsoft Defender Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)**, e-postayı korumak ve kaynakları korumak için bir dizi engelleme, algılama, araştırma ve arama özelliğiyle kuruluşların kuruluşlarının güvenliğini Office 365 yardımcı olur.
- **[Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-advanced-threat-protection)** , koruma, ihlal sonrası algılama, otomatik araştırma ve organizasyon cihazları için yanıt sağlar.
- **[Microsoft 365 Defender](microsoft-365-defender.md)**, Microsoft'un etki alanları genelinde tehdit verilerini otomatik olarak çözümlemek ve tek bir panoya saldırının resmini oluşturmak için Microsoft 365 güvenlik portföyünü yararlanan Genişletilmiş Algılama ve *Yanıt (* XDR) çözümünün bir parçasıdır.

Güvenlik ve Uyumluluk Merkezi veya Güvenlik Merkezi'Office 365 ilgili & hakkında bilgi Microsoft Defender Güvenlik Merkezi:

- [Office 365'da Microsoft 365 Defender için Defender](microsoft-365-security-center-mdo.md)
- [Microsoft 365 Defender'ta Uç Nokta için Defender](microsoft-365-security-center-mde.md)

> [!NOTE]
> Bu Microsoft 365 portalı, rol tabanlı var olan erişimi kullanır ve zorunlu eder ve her güvenlik modelini birleşik portala taşıtır. Birbirine yakınan her iş yükünün kendi rol tabanlı erişimi vardır. Zaten ürünlerde yer alan roller otomatik olarak bu Microsoft 365 portalına yakınsaacaktır. Bununla birlikte, MCAS'de roller ve izinler yine MCAS'da ele ele aecek.

## <a name="what-to-expect"></a>Neler olabilir?

Office 365 Güvenlik ve Uyumluluk Merkezi'nde (protection.office.com) ve Microsoft Defender güvenlik merkezinde (securitycenter.microsoft.com) kullanabileceğiniz tüm güvenlik *içeriği*, güvenlik Microsoft 365 Defender.

Microsoft 365 Defender, farklı iş yüklerinden gelen sinyalleri bir dizi birleşik deneyime getirerek güvenlik ekiplerinin saldırılarını araştırmalarına ve yanıtlamalarına yardımcı olur:

- Olaylar & uyarıları
- Avlama
- İşlem merkezi
- Tehdit analizleri

Microsoft 365 Defender için Microsoft Defender ile Uç  Nokta için Microsoft Defender'ı birleştirken Office 365 netlik ve ortak hedefleri vurgular. Birleştirme, aşağıda listelenen önceliklere dayalıdır ve her güvenlik paketinin şu özelliklerle bir araya getirdiği özelliklerden ödün vermeden yapılır:

- Ortak yapı taşları
- Yaygın terminoloji
- Ortak varlıklar
- Diğer iş yükleriyle birlikte özellik eşlik

> [!NOTE]
> Microsoft 365 Defender, müşterilerin geçiş adımlarını at düzenlemesi veya yeni bir lisans satın almaları gerekmeden erişilebilir hale gelecektir. Örneğin, bu yeni portala E3 aboneliği olan yöneticiler de aynı Office 365 Plan 1 ve Plan 2 için Microsoft Defender'a sahip olduğu gibi erişilebilir; bununla birlikte, Exchange Online Protection veya Office 365 Plan 1 müşterileri için Defender yalnızca abonelik lisanslarının desteklediği güvenlik özelliklerini görebilirler. Yeni merkezin amacı güvenliği merkezileştirmektir.

## <a name="unified-investigations"></a>Birleşik soruşturmalar

Biran iki güvenlik merkezi, farklı yer genelindeki güvenlik olaylarını araştıracak tek bir Microsoft 365. Birincil örnek olarak Olaylar **altındaki** **olaylar ve & başlatma uyarılarının** yer Microsoft 365 Defender.

:::image type="content" source="../../media/converged-incidents-2.png.png" alt-text="Microsoft 365 Defender'de Olaylar Microsoft 365 Defender.":::

Olay adı seçiliyorse, biran iki güvenlik merkezi değerini gösteren bir sayfa görüntülenir.

:::image type="content" source="../../media/converged-incident-info-3.png" alt-text="Başka bir olay için Özet Microsoft 365 Defender":::

<!--
![Example of the Summary page for an incident in Microsoft 365 Defender.](../../media/converged-incident-info-3.png)
--> 

Olay sayfasının üst kısmında Özet, **Uyarılar, Cihazlar****,** **Kullanıcılar****, Posta** **Kutuları, Soruşturmalar** ve Kanıt **sekmelerini** görebilirsiniz. Daha ayrıntılı bilgi için bu sekmeleri seçin. Örneğin, Kullanıcılar sekmesi  yakınsatan iş yüklerinden (Uç Nokta için Microsoft Defender, Kimlik için Microsoft Defender ve Microsoft Cloud App Security) ve şirket içi Active Directory Etki Alanı Hizmetleri (AD DS), Azure Active Directory (Azure AD) ve üçüncü taraf kimlik sağlayıcıları gibi çeşitli kaynaklardan gelen bilgileri görüntüler. Daha fazla bilgi için bkz [. kullanıcıları araştırma](investigate-users.md).

Zaman alıp ortamınız içinde bulunan olayları gözden geçirin, bu sekmelerin detaya inin ve farklı tehdit türlerine karşı olaylarda sağlanan bilgilere nasıl erişin, bunu anlamak için alıştırma yapın.

Daha fazla bilgi için bkz[. Microsoft 365 Defender](incidents-overview.md).

## <a name="improved-processes"></a>Geliştirilmiş işlemler

Ortak denetimler ve içerik aynı yerde görünür ya da tek bir veri akışında daha kolay bulunacaktır. Örneğin, birleştirilmiş ayarlar.

### <a name="unified-settings"></a>Birleştirilmiş ayarlar

!['Roller'e tıklandı ve Genel Ayarlar, İzinler, API'ler ve Kurallar'ı içeren Yeni Sayfa sayfasını açtınız. İzinler'i ve sonra Roller'i açın. Tüm rolleri gösterir.](../../media/converged-add-role-9.png)

### <a name="permissions--roles"></a>İzinler & rolleri

![gruplar&, Roller ve Cihaz gruplarında uç & gösteren İzinler Rolleri sayfası.](../../media/converged-roles-5.png)

 Access Microsoft 365 Defender, genel roller Azure Active Directory özel roller kullanılarak yapılandırılır. Uç Nokta için Defender için bkz[. Microsoft Defender Güvenlik Merkezi](/microsoft-365/security/defender-endpoint/assign-portal-access). Yeni kullanıcı Office 365 Defender için bkz. [Aşağıdaki Microsoft 365 uyumluluk merkezi ve Microsoft 365 Defender](../office-365-security/permissions-microsoft-365-compliance-security.md).

- E-postanıza erişimi [yönetme hakkında daha fazla Microsoft 365 Defender](m365d-permissions.md)
- Aynı dosyada özel [roller oluşturma hakkında daha](custom-roles.md) fazla Microsoft 365 Defender

> [!NOTE]
> Microsoft 365 Defender'daki Uç Nokta için Microsoft [Defender, Aynı Microsoft Defender](./mssp-access.md) güvenlik merkezinde erişim verilen şekilde yönetilen güvenlik hizmeti [sağlayıcılarına (MSSP)](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) erişim iznini destekler.

### <a name="integrated-reports"></a>Tümleşik raporlar

Raporlar aynı zamanda tek bir Microsoft 365 Defender. Yöneticiler genel bir güvenlik raporuyla başlayabilir ve uç noktalar, e-posta ve işbirliği hakkında belirli raporlara & olabilir. Buradaki bağlantılar iş yükü yapılandırmasına göre dinamik olarak oluşturulur.

### <a name="quickly-view-your-microsoft-365-environment"></a>Çalışma ortamınızı Microsoft 365 görüntüleme

Giriş **sayfasında** , güvenlik ekiplerinin ihtiyacı olan yaygın kartların birçoğu görünür. Kart ve veri oluşturma, kullanıcı rolüne bağlıdır. Bu Microsoft 365 Defender rol tabanlı erişim denetimi kullandığı için, farklı roller günlük işleri için daha anlamlı kartlar görebilir.  

Bu bir bakışta bu bilgiler, kuruluşta en son etkinlikleri takip etmek için yardımcı olur. Microsoft 365 Defender, kaynak ortamınız için holist bir görünüm sunmak için farklı kaynaklardan gelen sinyalleri Microsoft 365 getirir.

Kartlar şu kategorilere ayrılır:

- **Kimlikler**- Kuruluş kimliklerini takip etmek ve şüpheli veya riskli davranışları izlemek. [Kimlik koruması hakkında daha fazla bilgi edinmek için:](/azure/active-directory/identity-protection/overview-identity-protection)
- **Veriler** - Yetkisiz veri açıklamaya neden olan kullanıcı etkinliğini takip etmeye yardımcı olur.
- **Cihazlar** - Cihazlarınız için uyarılar, ihlal etkinliği ve diğer tehditlerle ilgili güncel bilgiler edinebilirsiniz.
- **Uygulamalar** - Bulut uygulamalarının organizasyonda nasıl kullanıldıklarına dair fikir edinin. [Keşfedilen uygulamalar hakkında daha Bulut Uygulamaları Güvenliği fazla bilgi edinin](/cloud-app-security/discovered-apps).

## <a name="threat-analytics-with-better-data-coverage"></a>Daha iyi veri kapsamına sahip tehdit analizleri
Tehdit analizi tümleşik deneyimi için aşağıdaki yeni ortaya çıkan tehditleri Microsoft 365 Defender ve yanıt verin:

- Uç nokta için Microsoft Defender ile Office 365 için Microsoft Defender arasında daha iyi veri kapsamı; birleştirilmiş olay yönetimi, otomatik soruşturma, düzeltme ve etki alanı genelinde önceden önlem almaya ve yeniden aktif tehdit aramasını mümkün hale getirilmesine yardımcı olur. 
- Uç nokta için Microsoft Defender'dan mevcut uç nokta verilerine ek olarak Office 365 için Microsoft Defender'dan gelen e-postayla ilgili algılamalar ve risk azaltmalar.
- Tehditle ilgili olaylar görünümü, hem iş sıranızı azaltmak hem de araştırmanızı kolaylaştırmak ve hızlandırmak için uç nokta için Microsoft Defender ve Office 365 için Microsoft Defender genelinde  end-uç saldırı öyküleri olarak uyarıları toplar.
- Diğer çözümler tarafından algılanan ve engellenen saldırı Microsoft 365 Defender. Ayrıca, daha fazla maruz kalma riskini azaltan ve daha fazla güvenlik önlemi almak için kullanabileceğiniz veriler de vardır. 
- Raporlara acil şekilde odaklanmak, araştırmak ve raporlardan yararlanacak verileri hızla tanımlamanıza yardımcı olmak için işlemılabilir bilgileri öne çıkanlara koyan geliştirilmiş tasarım.

## <a name="a-centralized-learning-hub"></a>Merkezi bir Learning Merkezi

Microsoft 365 Defender portalı, Microsoft güvenlik blogu, YouTube'daki Microsoft güvenlik topluluğu ve docs.microsoft.com'daki resmi belgeler gibi kaynaklardan gelen resmi rehberlikten bilgi edinen bir docs.microsoft.com.

Öğrenme merkezi içinde E-posta & İşbirliği (Office 365 için Microsoft Defender) kılavuzu Uç Nokta (Uç Nokta için Microsoft Defender) ve diğer Microsoft 365 Defender yan yanadır.

Öğrenme merkezi açılır ve "Learning Kullanarak Araştır" gibi konuların çevresinde düzenlenmiş Microsoft 365 Defender. ve "En İyi Uygulamalar Office 365 için Microsoft Defender". Bu bölüm şu anda Microsoft'un içindeki güvenlik Ürün Grubu tarafından hazır bulunduruldu. Her Learning yolu, kavramlar üzerinden geçen bir yansıtıldı süreyi yansıtmaktadır. Örneğin ' Microsoft Defender for Office 365 account is compromiseded olduğunda atılması gereken adımlar' 8 dakika sürecek şekilde projelidir ve çalışmanız çok değerlidir.

İçeriğin üzerine tık olduktan sonra, bu siteye yer işareti eklemek ve yer işaretlerini 'Güvenlik' veya 'Kritik' klasörüne düzenlemek yararlı olabilir. Tüm yol Learning görmek için, ana panelde Tüm bağlantıyı göster'e tıklayın.

> [!NOTE]
> Microsoft 365 Defender öğrenme merkezi'nin üst kısmında, ürünler (şu anda Microsoft 365 Defender, Uç Nokta için Microsoft Defender ve Office 365 için Microsoft Defender) arasında seçim Office 365. Her bölümün eğitim kaynağı sayısının listelenmiş olduğunu unutmayın. Bu da, öğrenme ve eğitim için kaç kaynağı olduğunu öğrenmenin önemli bir yolu olarak bu kaynak sayısını takip etmeye yardımcı olabilir.
>
> Ürün filtresiyle birlikte, geçerli konular, kaynak türleri (videolardan web seminerlerine), güvenlik alanları, güvenlik rolleri ve ürün özellikleriyle ilgili bilgi ve deneyim düzeyleri listelenir.

> [!TIP]
> [Microsoft Learn'de](/learn/) birçok başka öğrenme fırsatı vardır. Kurs [MS-500T02-A:](/learn/certifications/courses/ms-500t02) Tehdit Koruması'nın Uygulanması gibi sertifika Microsoft 365 bulabilirsiniz.

## <a name="send-us-your-feedback"></a>Geri bildiriminizi bize gönderin

Geri bildiriminize ihtiyacımız var. Her zaman geliştirmek için arıyoruz, bu nedenle görmek istediğim bir şey varsa bize geri bildirim [Microsoft 365 Defender](https://www.microsoft.com/videoplayer/embed/RE4K5Ci).

Bu makaleden de geri bildirim abilirsiniz. 'Geri bildirim' bölümünün sonundaki 'Geri bildirimi gönder ve görüntüle' bölümünde, *seçenekler Bu ürün* veya Bu *sayfa'dır*.

Ürün geri **bildirimleri için** Bu ürün *düğmesini* kullanın:

1. *Makalenin en* altında Bu ürün'e seçin.
    1. Bu yönergeleri okumaya devam etmek için düğmeye sağ tıklayın ve "Yeni sekmede aç" seçeneğini kullanın.
2. Bu, **UserVoice forumuna gidin**.
3. 2 seçenek vardır:
    1. Metin kutusunu aşağı kaydırarak Uyumluluk *ve* korumayı nasıl daha iyi bir şekilde Office 365? ve metin *kutusuna Microsoft 365 Defender*. Sonuçları sizinki gibi bir fikir için arayabilir ve oylamada kullanabilir ya da Yeni bir fikir postala **düğmesini kullanabilirsiniz**.
    1. Bu sorunun zaten raporlandığına eminsanız ve profilini oylarla (veya oylarla) yükseltmek istediğiniz durumlarda, UserVoice'ın sağ tarafındaki Geri Bildirim Ver kutusunu kullanın. Durumu *Microsoft 365 Defender* için **arama bulun, sorunu bulun ve oy** düğmesini kullanarak durumu yükseltin.

*Makalenin kendisine yönelik* geri bildirim için Bu sayfayı kullanın. Geri bildiriminiz için teşekkürler. Sesiniz ürünlerimizi geliştirmemıza yardımcı olur.

### <a name="explore-what-the-security-center-has-to-offer"></a>Güvenlik merkezinin neler sun sun yaptığını keşfedin

Özellikleri ve özellikleri keşfetmeye devam etmek için Microsoft 365 Defender:

- [Olayları ve uyarıları yönetme](manage-incidents.md)
- [Tehdit analizi ile ortaya çıkan tehditleri takip edin ve yanıt verin](threat-analytics.md)
- [İşlem merkezi](m365d-action-center.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında tehdit avı](./advanced-hunting-query-emails-devices.md)
- [Özel algılama kuralları](./custom-detection-rules.md)
- [E-& ve işbirliği uyarıları](../../compliance/alert-policies.md#default-alert-policies)
- [Ekiplerinize eğitim için kimlik avı](../office-365-security/attack-simulation-training.md) [saldırı benzetimi oluşturma ve yükleme oluşturma](/microsoft-365/security/office-365-security/attack-simulation-training-payloads)
 
### <a name="related-information"></a>İlgili bilgiler
- [Microsoft 365 Defender'da Office 365 için Microsoft Defender](microsoft-365-security-center-mdo.md)
- [Microsoft 365 Defender'ta Uç Nokta için Microsoft Defender](microsoft-365-security-center-mde.md)
- [Hesapları Uç Nokta için Microsoft Defender'dan Microsoft 365 Defender](microsoft-365-security-mde-redirection.md)