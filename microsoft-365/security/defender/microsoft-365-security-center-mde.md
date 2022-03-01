---
title: Microsoft 365 Defender'ta Uç Nokta için Microsoft Defender
description: Yeni gelen ve Microsoft Defender Güvenlik Merkezi hakkında bilgi Microsoft 365 Defender
keywords: Microsoft 365 Defender, Office 365 için Microsoft Defender, Uç Nokta için Microsoft Defender, MDO, MDE, güvenlik portalı, Defender güvenlik portalı ile çalışmaya başlama
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: 04/21/2021
audience: ITPro
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: 0a8ec594f59285f1b4e861ec464bbbeb6083f001
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010747"
---
# <a name="microsoft-defender-for-endpoint-in-microsoft-365-defender"></a>Microsoft 365 Defender'ta Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="quick-reference"></a>Hızlı başvuru

Resimde ve aşağıdaki tabloda, tablo arasında gezinti bölmesindeki Microsoft Defender Güvenlik Merkezi Microsoft 365 Defender.

> [!div class="mx-imgBorder"]
> ![Buraya taşınanların resmi.](../../media/mde-m3d-security-center.png)

| Microsoft Defender Güvenlik Merkezi | Microsoft 365 Defender |
|---------|---------|
| Panolar <ul><li>Güvenlik İşlemleri</li><li>Threat Analytics</li></ul>  |Home <ul><li>Tehdit analizleri</li></ul>   |
| Olaylar | Olaylar & uyarıları |
| Cihaz envanteri | Cihaz envanteri |
| Uyarılar sırası | Olaylar & uyarıları |
| Otomatik soruşturmalar | İşlem merkezi |
| Gelişmiş av | Avlama |
| Raporlar | Raporlar |
| API'& ortakları | API'& ortakları |
| Tehdit & Güvenlik Açığı Yönetimi | Güvenlik açığı yönetimi |
| Değerlendirme ve öğreticiler | Değerlendirme & öğreticileri |
| Yapılandırma yönetimi | Yapılandırma yönetimi |
| Ayarlar | Ayarlar | 

Gelişmiş özellik[, Microsoft 365 Defender](microsoft-365-defender.md#the-microsoft-365-defender-portal) e-posta<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a>, işbirliği, kimlik ve cihaz tehditlerini koruyan, algılayan, araştıran ve yanıtlayan güvenlik özelliklerini bir araya gösterir. Bu, uyumluluk merkezi ve Güvenlik ve Uyumluluk Merkezi gibi mevcut Microsoft güvenlik portallarından Microsoft Defender Güvenlik Merkezi Office 365 bir araya & getirir.

Bu makale, bu makalede Microsoft Defender Güvenlik Merkezi bazı değişiklikler ve iyileştirmeler açıklanmıştır Microsoft 365 Defender. Bununla birlikte, dikkatlenmesi gereken bazı yeni ve güncelleştirilmiş öğeler vardır.

Daha önce bu [Microsoft Defender Güvenlik Merkezi](/windows/security/threat-protection/microsoft-defender-atp/portal-overview), Uç Nokta için Microsoft Defender'ın evidir. Enterprise ekiplerinin olası gelişmiş kalıcı tehdit etkinlikleri veya veri ihlalleri uyarılarını izlemek ve buna yardımcı olmak için bu sistemi kullandığına dikkat edin. Portal sayısını azaltmaya yardımcı olmak için, Microsoft 365 Defender Microsoft kimlikleriniz, verileriniz, cihazlarınız, uygulamalarınız ve altyapınız genelinde güvenliği izleme ve yönetmeye de ev olacaktır.

Microsoft 365 Defender'ta Uç Nokta için Microsoft Defender, aynı aynı İnternet sitesinde erişim veriliş gibi yönetilen güvenlik hizmeti sağlayıcılarına [(MSSP)](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) [erişim Microsoft Defender Güvenlik Merkezi](mssp-access.md).

> [!IMPORTANT]
> Yeni abonelikte ne Microsoft 365 Defender geçerli aboneliklerinize bağlıdır. Örneğin, microsoft Defender for Office 365 lisansınız yoksa E-posta & işbirliği bölümü gösterilmez.

> [!Note]
> Microsoft 365 Defender şu için kullanılamaz:
>- ABD Government Community Cloud (GCC)
>- ABD Government Community Cloud Yüksek (GCC Yüksek)
>- ABD Savunma Bölümü
>- Ticari lisanslara sahip tüm ABD kamu kurumları

Microsoft 365 Defender'Microsoft 365 Defender bakın<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a>.

Avantajlar hakkında daha fazla bilgi edinmek için: [Avantajlara genel Microsoft 365 Defender](microsoft-365-defender.md)

## <a name="whats-changed"></a>Neler değişti

Bu tablo, iki tablo arasındaki değişikliklerin hızlı bir Microsoft Defender Güvenlik Merkezi Microsoft 365 Defender.

### <a name="alerts-and-actions"></a>Uyarılar ve eylemler

| Alan | Değişiklik açıklaması |
|---------|---------|
| [Olaylar & uyarıları](incidents-overview.md)  | Daha Microsoft 365 Defender, uç noktalarınız, e-postanız ve kimlikleriniz genelinde olayları ve uyarıları yönetebilirsiniz. İlgili olayları daha kolay bulamanıza yardımcı olmak için deneyimi yakınsa kullandık. Daha fazla bilgi için bkz. [Olaylara Genel Bakış](incidents-overview.md).   |
| [Avlama](advanced-hunting-overview.md)  |  Kimlik eklemek üzere Uç Nokta için Microsoft Defender'da oluşturulan özel algılama kurallarını değiştirmek, e-posta tablolarını otomatik olarak Başka bir Microsoft 365 Defender. İlgili uyarılar aynı zamanda son Microsoft 365 Defender. Bu değişiklikler hakkında daha fazla ayrıntı için Özel algılama [kurallarını geçirme makalesi'ne bakın](advanced-hunting-migrate-from-mde.md#migrate-custom-detection-rules). <br><br>Gelişmiş `DeviceAlertEvents` av tablosu şu anda Microsoft 365 Defender. E-postada cihaza özgü uyarı Microsoft 365 Defender sorgulamak için, `AlertInfo` `AlertEvidence` ve tabloları kullanarak farklı bir kaynak kümesinden daha fazla bilgi barındırabilirsiniz. [DeviceAlertEvents olmadan Yazma sorgularını takip edin ve cihazla ilgili bir sonraki sorguyu oluşturun](advanced-hunting-migrate-from-mde.md#write-queries-without-devicealertevents).|
|[İşlem merkezi](m365d-action-center.md)    | Otomatik soruşturma ve düzeltme eylemlerini takip eden bekleyen ve tamamlanmış eylemleri listeler. Önceden, İşlem merkezi yalnızca cihazlarda Microsoft Defender Güvenlik Merkezi düzeltme eylemleri için bekleyen ve tamamlanmış eylemler listelenirken, Otomatik soruşturmalar uyarıları ve durumu listeledi. Geliştirilmiş Microsoft 365 Defender Merkezi e-posta, cihazlar ve kullanıcılar genelinde düzeltme eylemlerini ve soruşturmalarını tek bir konumda bir araya getirir.  |
| [Tehdit analizleri](threat-analytics.md) |  Daha kolay bulma ve kullanma için gezinti çubuğunun en üstüne taşındı. Şimdi hem uç noktalar hem de e-posta ve işbirliği için tehdit bilgilerini de içerir.    |

### <a name="endpoints"></a> Uç Noktaları

| Alan | Değişiklik açıklaması |
|---------|---------|
|Arama   |  Arama çubuğu sayfanın en üstünde yer alıyor. Siz yazarak öneriler sağlanır. Uç Nokta için Defender ve Kimlik için Defender'da aşağıdaki varlıklar arasında arama yapabilirsiniz: <br><br> - **Cihazlar** - Hem Uç Nokta için Defender hem de Kimlik için Defender için de destekler. Hatta, örneğin "içerir" kullanarak ana bilgisayar adının bir bölümünü aramak için arama işleçlerini bile kullanabilirsiniz. <br><br> - **Kullanıcılar** - Hem Uç Nokta için Defender hem de Kimlik için Defender için de destekler. <br><br> - **Dosyalar, IP'ler ve URL'ler** - Uç Nokta için Defender'dakiyle aynı özelliklerdir. <br> NOT: *IP ve URL aramaları tam olarak eştir ve arama sonuçları sayfasında görünmez; doğrudan varlık sayfasına doğru iler.  <br><br> - **TVM** - Uç Nokta için Defender'dakiyle aynı özelliklerdir (güvenlik açıkları, yazılım ve öneriler). <br><br>  İyileştirilmiş arama sonuçları sayfası, tüm varlıklardan sonuçları merkezi hale gösterir.  |
|[Pano](/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)   |  Bu, güvenlik işlemleri panonuz. Kaç etkin uyarının tetiklenen, hangi cihazların risk altında olduğu, hangi kullanıcıların risk altında olduğu ve uyarılar, cihazlar ve kullanıcılar için önem düzeyi hakkında genel bir bakışa bakın. Ayrıca herhangi bir aygıtlarda algılayıcı sorunu olup kontrol edilemedi, genel hizmet durumunuz ve çözümlenmemiş uyarıların nasıl algılandığından emin olun. |
|Cihaz envanteri | Değişiklik yok. |
|[Güvenlik açığı yönetimi](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)    |    Ad, gezinti bölmesine sığacak şekilde kısaltıldı. Tüm sayfalar altta olacak şekilde Tehdit ve Güvenlik Açığı Yönetimi bölümle aynıdır.     |
| İş ortakları ve API'ler | Değişiklik yok. |
| Değerlendirmeler & öğreticileri    |     Yeni test ve öğrenme özellikleri.     |
| Yapılandırma yönetimi   |  Değişiklik yok.  |

> [!NOTE]
> **Otomatik soruşturma ve düzeltme artık** olayın bir parçası. Olay Araştırma sekmesinde Otomatik araştırma ve düzeltme **olaylarını** > görebilirsiniz.

> [!TIP]
> Cihaz araması Uç Noktalar ve Arama'dan > yapılır.

### <a name="access-and-reporting"></a>Erişim ve raporlama

| Alan | Değişiklik açıklaması |
|---------|---------|
| Raporlar  | Tehdit koruması, Cihaz durumu ve uyumluluğu & Korumasız cihazlar da dahil olmak üzere uç noktalar ve e-postaya yönelik raporlara bakın. |
| Hizmet Durumu  |  Şu anda, çalışma sayfasındaki "Hizmet durumu" [sayfasına Microsoft 365 yönetim merkezi](https://admin.microsoft.com/). |
| Ayarlar |  Daha fazla bilgi, uç Microsoft 365 Defender, E-posta ve &, Kimlikler ve Cihaz bulma ayarlarınızı yönetin.   |

## <a name="microsoft-365-security-navigation-and-capabilities"></a>Microsoft 365 gezintisi ve özellikleri hakkında

Sol gezinti veya hızlı başlatma çubuğu tanıdık gelecek. Bununla birlikte, portalda bazı yeni ve güncelleştirilmiş Microsoft 365 Defender vardır. 

### <a name="incidents-and-alerts"></a>Olaylar ve uyarılar

E-postanız, cihazlarınız ve kimlikleriniz arasında olay ve uyarı yönetimini bir araya getirir. Uyarı sayfası, ayrıntılı bir hikaye oluşturmak için saldırı sinyallerini birleştirerek uyarının tam bağlamını sağlar. Yeni, birleşik bir deneyim, artık iş yükleri genelinde uyarıların tutarlı bir görünümünü bir araya getirir. Hızlı bir şekilde triyaksıt atabilirsiniz, araştırabilirsiniz ve etkili bir işlem atabilirsiniz.

- [Olaylar hakkında daha fazla bilgi](incidents-overview.md)
- [Uyarıları yönetme hakkında daha fazla bilgi](investigate-alerts.md)

![Uyarılar ve Eylemler hızlı başlatma çubuğu.](../../media/converge-1-alerts-and-actions.png)

### <a name="hunting"></a>Avlama

Gelişmiş av sorgularını kullanarak uç noktalarınız genelinde tehdit, kötü amaçlı yazılım ve kötü amaçlı Office 365 önceden arama, posta kutuları ve daha fazlasını [Office 365 arama.](advanced-hunting-overview.md) Bu güçlü sorgular, hem bilinen hem de potansiyel tehditlere yönelik tehdit göstergelerini ve varlıkları bulmak ve gözden geçirmek için kullanılabilir.

[İhlal](custom-detection-rules.md) etkinliğine ve hatalı yapılandırılmış cihazlara işaret eden olayları önceden izlemenizi yardımcı olmak için gelişmiş arama sorgularından özel algılama kuralları oluşturabilirsiniz.


### <a name="action-center"></a>İşlem merkezi

İşlem merkezi, otomatik soruşturma ve yanıt özellikleri tarafından oluşturulan incelemeleri gösterir. Bu otomatik, kendi kendine yardım eden Microsoft 365 Defender ekiplere, belirli olayları otomatik olarak yanıt vermede yardımcı olabilir.

[İşlem merkezi hakkında daha fazla bilgi edin.](m365d-action-center.md)

### <a name="threat-analytics"></a>Threat Analytics

Uzman Microsoft güvenlik araştırmacılarından tehdit zekası elde edin. Threat Analytics, ortaya çıkan tehditlere karşı güvenlik ekiplerinin daha verimli çalışmalarına yardımcı olur. Threat Analytics şunları içerir:

- İş için Microsoft Defender'dan e-postayla ilgili algılamalar ve Office 365. Bu, uç nokta için Microsoft Defender'da zaten mevcut olan uç nokta verilerine ektir.
- Tehditlerle ilgili olaylar görünümü.
- Raporlarda işlemlenebilir bilgileri hızla tanımlamak ve kullanmak için gelişmiş deneyim.

Tehdit çözümlemelerine, Microsoft 365 Defender'ta sol üst gezinti çubuğundan veya kuruluş için en çok tehdit gösteren ayrılmış bir pano kartından erişebilirsiniz.

Tehdit analizi ile ortaya çıkan [tehditleri izleme ve yanıtlama hakkında daha fazla bilgi edinin](./threat-analytics.md).

### <a name="endpoints-section"></a>Uç noktalar bölümü

Kuruluşta uç noktaların güvenliğini görüntüleme ve yönetme. Bu e-Microsoft Defender Güvenlik Merkezi, tanıdık gelecek.

![Uç noktalar hızlı başlatma çubuğu.](../../media/converge-2-endpoints.png)

### <a name="access-and-reports"></a>Erişim ve raporlar

Raporları görüntüleme, ayarlarınızı değiştirme ve kullanıcı rollerini değiştirme.

![Access ve Raporlama hızlı erişim çubuğu.](../../media/converge-4-access-and-reporting-new.png)

### <a name="siem-api-connections"></a>SIEM API bağlantıları

Uç Nokta [SIEM API'si için Defender'ı kullanıyorsanız](../defender-endpoint/enable-siem-integration.md), bunu yapmaya devamabilirsiniz. API yüklemesinde, güvenlik portalında uyarı sayfasına veya olay sayfasına işaret alan yeni Microsoft 365 ekledik. Yeni API alanları LinkToMTP ve IncidentLinkToMTP'yi içerir. Daha fazla bilgi için bkz[. Hesapları Uç Nokta için Microsoft Defender'dan Yeniden Yönlendirme'Microsoft 365 Defender](./microsoft-365-security-mde-redirection.md).

### <a name="email-alerts"></a>E-posta uyarıları

Uç Nokta için Defender için e-posta uyarılarını kullanmaya devam edin. Uyarı sayfasına veya posta sayfasındaki olay sayfasına işaret alan e-postalara yeni bağlantılar Microsoft 365 Defender. Daha fazla bilgi için bkz[. Hesapları Uç Nokta için Microsoft Defender'dan Yeniden Yönlendirme'Microsoft 365 Defender](./microsoft-365-security-mde-redirection.md).

### <a name="managed-security-service-providers-mssp"></a>Yönetilen Güvenlik Hizmeti Sağlayıcıları (MSSP)

Aynı gözatma oturumunda aynı anda birden çok kiracıda oturum açma şu anda birleşik portalda desteklenemli değildir. Otomatik yeniden yönlendirmeyi geri dönerek, sorun çözülene kadar bu işlevselliği korumak için eski Uç Nokta için [Microsoft Defender portalına](microsoft-365-security-mde-redirection.md#can-i-go-back-to-using-the-former-portal) geri dönebilirsiniz.

## <a name="related-information"></a>İlgili bilgiler

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft 365 Defender'ta Uç Nokta için Microsoft Defender](microsoft-365-security-center-mde.md)
- [Hesapları Uç Nokta için Microsoft Defender'dan Microsoft 365 Defender](microsoft-365-security-mde-redirection.md)
