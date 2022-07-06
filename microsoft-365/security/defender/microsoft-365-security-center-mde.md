---
title: Microsoft 365 Defender'da Uç Nokta için Microsoft Defender
description: Microsoft Defender Güvenlik Merkezi Microsoft 365 Defender değişiklikleri hakkında bilgi edinin
keywords: Microsoft 365 Defender, Office 365 için Microsoft Defender, Uç Nokta için Microsoft Defender, MDO, MDE, güvenlik portalı, defender güvenlik portalı ile çalışmaya başlama
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
ms.openlocfilehash: dd8721bd8c62a99180f9e8cf34b05c5ec6c8b4c8
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617204"
---
# <a name="microsoft-defender-for-endpoint-in-microsoft-365-defender"></a>Microsoft 365 Defender'da Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="quick-reference"></a>Hızlı başvuru

Aşağıdaki resimde ve tabloda, Microsoft Defender Güvenlik Merkezi ile Microsoft 365 Defender arasındaki gezinti değişiklikleri listelenmiştir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/mde-m3d-security-center.png" alt-text="Microsoft 365 Defender portalındaki yeni konumlar" lightbox="../../media/mde-m3d-security-center.png":::

| Microsoft Defender Güvenlik Merkezi | Microsoft 365 Defender |
|---------|---------|
| Pano <ul><li>Güvenlik İşlemleri</li><li>Tehdit Analizi</li></ul>  |Home <ul><li>Tehdit analizi</li></ul>   |
| Olaylar | Olaylar & uyarıları |
| Cihaz envanteri | Cihaz envanteri |
| Uyarı sırası | Olaylar & uyarıları |
| Otomatik araştırma | İşlem merkezi |
| Gelişmiş avcılık örneği | Avcı -lık |
| Raporlar | Raporlar |
| İş ortakları & API'leri | İş ortakları & API'leri |
| Tehdit & Güvenlik Açığı Yönetimi | Güvenlik açığı yönetimi |
| Değerlendirme ve öğreticiler | Değerlendirme & öğreticileri |
| Yapılandırma yönetimi | Yapılandırma yönetimi |
| Ayarlar | Ayarlar | 

'daki <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a> geliştirilmiş [Microsoft 365 Defender](microsoft-365-defender-portal.md), e-posta, işbirliği, kimlik ve cihaz tehditlerini koruyan, algılayan, araştıran ve yanıt veren güvenlik özelliklerini birleştirir. Bu, Microsoft Defender Güvenlik Merkezi ve Office 365 Güvenlik & Uyumluluk merkezi de dahil olmak üzere mevcut Microsoft güvenlik portallarından işlevleri bir araya getirir.

Microsoft Defender Güvenlik Merkezi hakkında bilgi sahibiyseniz, bu makale Microsoft 365 Defender bazı değişiklikleri ve geliştirmeleri açıklamaya yardımcı olur. Ancak, dikkat etmeniz gereken bazı yeni ve güncelleştirilmiş öğeler vardır.

Tarihsel olarak[, Microsoft Defender Güvenlik Merkezi](/windows/security/threat-protection/microsoft-defender-atp/portal-overview) Uç Nokta için Microsoft Defender için ev olmuştur. Kurumsal güvenlik ekipleri bunu, olası gelişmiş kalıcı tehdit etkinliği veya veri ihlalleri uyarılarını izlemek ve yanıtlamaya yardımcı olmak için kullanmıştı. Portal sayısını azaltmaya yardımcı olmak için Microsoft 365 Defender Microsoft kimlikleriniz, verileriniz, cihazlarınız, uygulamalarınız ve altyapınız genelinde güvenliği izlemek ve yönetmek için bir ev olacaktır.

Microsoft 365 Defender'daki Uç Nokta için Microsoft Defender, [yönetilen güvenlik hizmeti sağlayıcılarına (MSSP) Microsoft Defender Güvenlik Merkezi](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) [aynı şekilde erişim verilmesini](mssp-access.md) destekler.

> [!IMPORTANT]
> Microsoft 365 Defender'da gördükleriniz geçerli aboneliklerinize bağlıdır. Örneğin, Office 365 için Microsoft Defender lisansınız yoksa E-posta & İşbirliği bölümü gösterilmez.

> [!Note]
> Microsoft 365 Defender şu şekilde kullanılamaz:
>- US Government Community Cloud (GCC)
>- US Government Community Cloud High (GCC High)
>- ABD Savunma Bakanlığı
>- Ticari lisansa sahip tüm ABD kamu kurumları

Microsoft 365 Defender bir <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a>göz atın.

Avantajlar hakkında daha fazla bilgi edinin: [Microsoft 365 Defender genel bakış](microsoft-365-defender.md)

## <a name="whats-changed"></a>Değişenler

Bu tablo, Microsoft Defender Güvenlik Merkezi ile Microsoft 365 Defender arasındaki değişikliklerin hızlı bir başvurusudur.

### <a name="alerts-and-actions"></a>Uyarılar ve eylemler

| Alan | Değişikliğin açıklaması |
|---------|---------|
| [Olaylar & uyarıları](incidents-overview.md)  | Microsoft 365 Defender tüm uç noktalarınızda, e-postanızda ve kimliklerinizde olayları ve uyarıları yönetebilirsiniz. İlgili olayları daha kolay bulmanıza yardımcı olmak için bu deneyimi yakınsamamızı sağladık. Daha fazla bilgi için bkz [. Olaylara Genel Bakış](incidents-overview.md).   |
| [Avcı -lık](advanced-hunting-overview.md)  |  Uç Nokta için Microsoft Defender'de oluşturulan özel algılama kurallarını kimlik ve e-posta tablolarını içerecek şekilde değiştirmek, bunları otomatik olarak Microsoft 365 Defender taşır. İlgili uyarılar Microsoft 365 Defender'da da görünür. Bu değişiklikler hakkında daha fazla ayrıntı için [Bkz. Özel algılama kurallarını geçirme](advanced-hunting-migrate-from-mde.md#migrate-custom-detection-rules). <br><br>Gelişmiş `DeviceAlertEvents` avcılık tablosu Microsoft 365 Defender'de kullanılamaz. Microsoft 365 Defender'da cihaza özgü uyarı bilgilerini sorgulamak için ve `AlertEvidence` tablolarını kullanarak `AlertInfo` çeşitli kaynak kümelerinden daha fazla bilgi alabilirsiniz. [DeviceAlertEvents olmadan Yazma sorgularını](advanced-hunting-migrate-from-mde.md#write-queries-without-devicealertevents) izleyerek cihazla ilgili bir sonraki sorgunuzu oluşturma.|
|[İşlem merkezi](m365d-action-center.md)    | Otomatik araştırmalardan ve düzeltme eylemlerinden sonra gerçekleştirilen bekleyen ve tamamlanan eylemleri listeler. Daha önce, Microsoft Defender Güvenlik Merkezi İşlem merkezi yalnızca cihazlarda gerçekleştirilen düzeltme eylemleri için bekleyen ve tamamlanan eylemler listelenirken Otomatik araştırmalarda uyarılar ve durum listelenir. geliştirilmiş Microsoft 365 Defender İşlem merkezi, e-posta, cihazlar ve kullanıcılar genelinde düzeltme eylemlerini ve araştırmalarını tek bir konumda bir araya getirir.  |
| [Tehdit analizi](threat-analytics.md) |  Daha kolay bulma ve kullanım için gezinti çubuğunun en üstüne taşındı. Şimdi hem uç noktalar hem de e-posta ve işbirliği için tehdit bilgilerini içerir.    |

### <a name="endpoints"></a> Uç Noktaları

| Alan | Değişikliğin açıklaması |
|---------|---------|
|Arama   |  Arama çubuğu sayfanın en üstünde yer alır. Siz yazarken öneriler sağlanır. Uç Nokta için Defender ve Kimlik için Defender'da aşağıdaki varlıklar arasında arama yapabilirsiniz: <br><br> - **Cihazlar** - Hem Uç Nokta için Defender hem de Kimlik için Defender için desteklenir. Hatta arama işleçlerini de kullanabilirsiniz. Örneğin, bir konak adının bir bölümünü aramak için "contains" kullanabilirsiniz. <br><br> - **Kullanıcılar** - Hem Uç Nokta için Defender hem de Kimlik için Defender için desteklenir. <br><br> - **Dosyalar, IP'ler ve URL'ler** - Uç Nokta için Defender'daki özelliklerle aynıdır. <br> NOT: *IP ve URL aramaları tam olarak eşleşir ve arama sonuçları sayfasında görünmez; doğrudan varlık sayfasına yönlendirir.  <br><br> - **TVM** - Uç Nokta için Defender ile aynı özellikler (güvenlik açıkları, yazılımlar ve öneriler). <br><br>  Gelişmiş arama sonuçları sayfası, tüm varlıklardaki sonuçları merkezileştirir.  |
|[Pano](/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)   |  Bu, güvenlik işlemleri panonuzdur. Kaç etkin uyarının tetiklendiğine, hangi cihazların risk altında olduğunu, hangi kullanıcıların risk altında olduğunu ve uyarılar, cihazlar ve kullanıcılar için önem derecesine genel bakış bölümüne bakın. Ayrıca herhangi bir cihazda algılayıcı sorunları olup olmadığını, genel hizmet durumunuzu ve çözümlenmemiş uyarıların nasıl algılandığını da görebilirsiniz. |
|Cihaz envanteri | Değişiklik yok. |
|[Güvenlik açığı yönetimi](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)    |    Ad, gezinti bölmesine sığacak şekilde kısaltıldı. Tüm sayfaların altında olduğu Tehdit ve Güvenlik Açığı Yönetimi bölümüyle aynıdır.     |
| İş ortakları ve API'ler | Değişiklik yok. |
| Değerlendirmeler & öğreticileri    |     Yeni test ve öğrenme özellikleri.     |
| Yapılandırma yönetimi   |  Değişiklik yok.  |

> [!NOTE]
> **Otomatik araştırma ve düzeltme** artık olayların bir parçasıdır. Otomatik araştırma ve düzeltme olaylarını **Olay > Araştırma** sekmesinde görebilirsiniz.

> [!TIP]
> Cihaz araması Uç Noktalar > Arama'dan yapılır.

### <a name="access-and-reporting"></a>Erişim ve raporlama

| Alan | Değişikliğin açıklaması |
|---------|---------|
| Raporlar  | Tehdit koruması, Cihaz durumu ve uyumluluğu ve Güvenlik açığı bulunan cihazlar dahil olmak üzere uç noktalar ve e-posta & işbirliği raporlarına bakın. |
| Hizmet Durumu  |  Şu anda [Microsoft 365 yönetim merkezi](https://admin.microsoft.com/) "Hizmet durumu" sayfasına bağlanır. |
| Ayarlar |  Microsoft 365 Defender, Uç Noktalar, E-posta & işbirliği, Kimlikler ve Cihaz bulma ayarlarınızı yönetin.   |

## <a name="microsoft-365-security-navigation-and-capabilities"></a>Microsoft 365 güvenlik gezintisi ve özellikleri

Sol gezinti veya hızlı başlatma çubuğu tanıdık görünecektir. Ancak, Microsoft 365 Defender portalında bazı yeni ve güncelleştirilmiş öğeler vardır. 

### <a name="incidents-and-alerts"></a>Olaylar ve uyarılar

Olay ve uyarı yönetimini e-postanız, cihazlarınız ve kimlikleriniz arasında bir araya getirir. Uyarı sayfası, ayrıntılı bir hikaye oluşturmak için saldırı sinyallerini birleştirerek uyarıya tam bağlam sağlar. Yeni, birleşik bir deneyim, iş yükleri genelinde uyarıların tutarlı bir görünümünü bir araya getiriyor. Hızlı bir şekilde önceliklendirme yapabilir, araştırabilir ve etkili eylemler gerçekleştirebilirsiniz.

- [Olaylar hakkında daha fazla bilgi edinin](incidents-overview.md)
- [Uyarıları yönetme hakkında daha fazla bilgi edinin](investigate-alerts.md)

:::image type="content" source="../../media/converge-1-alerts-and-actions.png" alt-text="Microsoft 365 Defender portalındaki Uyarılar ve Eylemler hızlı başlatma çubuğu" lightbox="../../media/converge-1-alerts-and-actions.png":::

### <a name="hunting"></a>Avcı -lık

[Gelişmiş tehdit avcılığı sorgularını](advanced-hunting-overview.md) kullanarak uç noktalarınızdaki tehditleri, kötü amaçlı yazılımları ve kötü amaçlı etkinlikleri, Office 365 posta kutularını ve daha fazlasını proaktif olarak arayın. Bu güçlü sorgular, hem bilinen hem de olası tehditler için tehdit göstergelerini ve varlıkları bulmak ve gözden geçirmek için kullanılabilir.

[Özel algılama kuralları](custom-detection-rules.md) , ihlal etkinliğinin ve yanlış yapılandırılmış cihazların göstergesi olabilecek olayları proaktif olarak izlemenize yardımcı olmak için gelişmiş tehdit avcılığı sorgularından oluşturulabilir.


### <a name="action-center"></a>İşlem merkezi

İşlem merkezi, otomatik araştırma ve yanıt özellikleri tarafından oluşturulan araştırmaları gösterir. Microsoft 365 Defender'da otomatik ve kendi kendini iyileştiren bu özellik, belirli olaylara otomatik olarak yanıt vererek güvenlik ekiplerine yardımcı olabilir.

[İşlem merkezi hakkında daha fazla bilgi edinin](m365d-action-center.md).

### <a name="threat-analytics"></a>Tehdit Analizi

Uzman Microsoft güvenlik araştırmacılarından tehdit bilgileri alın. Tehdit Analizi, güvenlik ekiplerinin yeni ortaya çıkan tehditlerle karşılaştığında daha verimli olmasını sağlar. Tehdit Analizi şunları içerir:

- Office 365 için Microsoft Defender e-postayla ilgili algılamalar ve azaltmalar. Bu, Uç Nokta için Microsoft Defender'dan sağlanan uç nokta verilerine ek olarak sağlanır.
- Tehditlerle ilgili olaylar görünümü.
- Raporlarda eyleme dönüştürülebilir bilgileri hızla tanımlamak ve kullanmak için gelişmiş deneyim.

Tehdit analizine Microsoft 365 Defender sol üst gezinti çubuğundan veya kuruluşunuz için en önemli tehditleri gösteren ayrılmış bir pano kartından erişebilirsiniz.

[Tehdit analiziyle yeni ortaya çıkan tehditleri izleme ve yanıtlama](./threat-analytics.md) hakkında daha fazla bilgi edinin.

### <a name="endpoints-section"></a>Uç noktalar bölümü

Kuruluşunuzdaki uç noktaların güvenliğini görüntüleyin ve yönetin. Microsoft Defender Güvenlik Merkezi kullandıysanız tanıdık görünecektir.

:::image type="content" source="../../media/converge-2-endpoints.png" alt-text="Microsoft 365 Defender portalındaki Uç Noktalar hızlı başlatma çubuğu" lightbox="../../media/converge-2-endpoints.png":::

### <a name="access-and-reports"></a>Erişim ve raporlar

Raporları görüntüleyin, ayarlarınızı değiştirin ve kullanıcı rollerini değiştirin.

:::image type="content" source="../../media/converge-4-access-and-reporting-new.png" alt-text="Microsoft 365 Defender portalındaki Erişim ve Raporlama hızlı oluşturma çubuğu" lightbox="../../media/converge-4-access-and-reporting-new.png":::

### <a name="siem-api-connections"></a>SIEM API bağlantıları

[Uç Nokta için Defender SIEM API'sini](../defender-endpoint/enable-siem-integration.md) kullanıyorsanız, bunu yapmaya devam edebilirsiniz. API yüküne Uyarı sayfasına veya Microsoft 365 güvenlik portalındaki olay sayfasına işaret eden yeni bağlantılar ekledik. Yeni API alanları LinkToMTP ve IncidentLinkToMTP'i içerir. Daha fazla bilgi için bkz. [Hesapları Uç Nokta için Microsoft Defender Microsoft 365 Defender yeniden yönlendirme](./microsoft-365-security-mde-redirection.md).

### <a name="email-alerts"></a>E-posta uyarıları

Uç Nokta için Defender için e-posta uyarılarını kullanmaya devam edebilirsiniz. E-postalara uyarı sayfasına veya Microsoft 365 Defender'daki olay sayfasına işaret eden yeni bağlantılar ekledik. Daha fazla bilgi için bkz. [Hesapları Uç Nokta için Microsoft Defender Microsoft 365 Defender yeniden yönlendirme](./microsoft-365-security-mde-redirection.md).

### <a name="managed-security-service-providers-mssp"></a>Yönetilen Güvenlik Hizmeti Sağlayıcıları (MSSP)

Aynı gözatma oturumunda aynı anda birden çok kiracıda oturum açmak şu anda birleşik portalda desteklenmemektedir. Sorun çözülene kadar bu işlevselliği korumak [için eski Uç Nokta için Microsoft Defender portalına geri dönerek](microsoft-365-security-mde-redirection.md#can-i-go-back-to-using-the-former-portal) otomatik yeniden yönlendirmeyi geri çevirebilirsiniz.

## <a name="related-information"></a>İlgili bilgiler

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft 365 Defender'da Uç Nokta için Microsoft Defender](microsoft-365-security-center-mde.md)
- [Hesapları Uç Nokta için Microsoft Defender'dan Microsoft 365 Defender'a yönlendirme](microsoft-365-security-mde-redirection.md)
