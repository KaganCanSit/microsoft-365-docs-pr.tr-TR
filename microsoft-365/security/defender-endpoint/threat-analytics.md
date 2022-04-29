---
title: Uç Nokta için Microsoft Defender tehdit analiziyle yeni ortaya çıkan tehditleri izleme ve yanıtlama
ms.reviewer: ''
description: Yeni ortaya çıkan tehditleri ve saldırı tekniklerini ve bunların nasıl durdurulacağını anlayın. Kuruluşunuz üzerindeki etkilerini değerlendirin ve kuruluşunuzun dayanıklılığını değerlendirin.
keywords: tehdit analizi, risk değerlendirmesi, işletim sistemi azaltma, mikro kod azaltma, azaltma durumu
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 455b80f590edf255362c7bb047c7aa1b23916666
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128576"
---
# <a name="track-and-respond-to-emerging-threats-through-threat-analytics"></a>Tehdit analizi aracılığıyla yeni ortaya çıkan tehditleri izleme ve yanıtlama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Daha karmaşık saldırganlar ve yaygın olarak ortaya çıkan yeni tehditler sayesinde, hızlı bir şekilde şunları yapabilmek çok önemlidir:

- Yeni tehditlerin etkisini değerlendirme
- Tehditlere karşı dayanıklılığınızı veya tehditlere maruz kalma durumunuzu gözden geçirin
- Tehditleri durdurmak veya içermek için gerçekleştirebileceğiniz eylemleri belirleyin

Tehdit analizi, uzman Microsoft güvenlik araştırmacılarının aşağıdakiler dahil olmak üzere en ilgili tehditleri kapsayan bir dizi raporudur:

- Etkin tehdit aktörleri ve kampanyaları
- Popüler ve yeni saldırı teknikleri
- Kritik güvenlik açıkları
- Yaygın saldırı yüzeyleri
- Yaygın kötü amaçlı yazılım

Her rapor, bir tehdidin ayrıntılı analizini ve bu tehdide karşı savunma konusunda kapsamlı rehberlik sağlar. Ayrıca ağınızdaki verileri de içerir ve tehdidin etkin olup olmadığını ve geçerli korumalarınız olup olmadığını belirtir.

Tehdit analizinin en son tehditleri izlemenize ve durdurmanıza nasıl yardımcı olabileceği hakkında daha fazla bilgi edinmek için bu kısa videoyu izleyin.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bw1f]

## <a name="required-roles-and-permissions"></a>Gerekli roller ve izinler
Aşağıdaki tabloda, Threat Analytics'e erişmek için gereken roller ve izinler özetlenmiştir. Aşağıdaki tabloda tanımlanan roller, tek tek portallardaki özel rollere başvurur ve benzer şekilde adlandırılmış olsa bile Azure AD'deki genel rollere bağlı değildir.

| **Microsoft 365 Defender için aşağıdaki rollerden biri gereklidir**  | **Uç Nokta için Defender için aşağıdaki rollerden biri gereklidir**  | **Office 365 için Defender için aşağıdaki rollerden biri gereklidir** | **Bulut için Defender Uygulamaları için aşağıdaki rollerden biri gereklidir** | 
|---------|---------|---------|---------|
| Tehdit Analizi | Uyarılar ve olay verileri: <ul><li>Veri görüntüleme- güvenlik işlemleri</li></ul>TVM risk azaltmaları:<ul><li>Verileri görüntüleme - Tehdit ve güvenlik açığı yönetimi</li></ul> | Uyarılar ve olay verileri:<ul> <li>Uyarıları yalnızca görüntüleme yönetimi</li> <li>Uyarıları yönetin</li> <li>Kuruluş yapılandırması</li><li>Denetim günlükleri</li> <li>Yalnızca görüntüleme denetim günlükleri</li><li>Güvenlik gözetmeni</li> <li>Güvenlik yöneticisi</li><li>Yalnızca görüntüleme alıcıları</li> </ul> Engellenen e-posta girişimleri: <ul><li>Güvenlik gözetmeni</li> <li>Güvenlik yöneticisi</li><li>Yalnızca görüntüleme alıcıları</li> | Bulut için Defender Uygulamaları veya MDI kullanıcıları için kullanılamaz |

## <a name="view-the-threat-analytics-dashboard"></a>Tehdit analizi panosunu görüntüleme

Tehdit analizi panosu, kuruluşunuzla en ilgili raporları almak için harika bir atlama noktasıdır. Aşağıdaki bölümlerde tehditleri özetler:

- **En son tehditler**: En son yayımlanan tehdit raporlarının yanı sıra etkin ve çözümlenmiş uyarılara sahip cihaz sayısını listeler.
- **Yüksek etkili tehditler**: Kuruluş üzerinde en yüksek etkiye sahip tehditleri listeler. Bu bölüm, tehditleri etkin uyarıları olan cihaz sayısına göre sıralar.
- **Tehdit özeti**: Etkin ve çözümlenmiş uyarılarla tehdit sayısını göstererek izlenen tehditlerin genel etkisini gösterir.

Bu tehdidin raporunu görüntülemek için panodan bir tehdit seçin.

:::image type="content" source="images/ta_dashboard.png" alt-text="Tehdit analizi panosu" lightbox="images/ta_dashboard.png":::

## <a name="view-a-threat-analytics-report"></a>Tehdit analizi raporunu görüntüleme

Her tehdit analizi raporu üç bölümde bilgi sağlar: **Genel Bakış**, **Analist raporu** ve **Risk Azaltmalar**.

### <a name="overview-quickly-understand-the-threat-assess-its-impact-and-review-defenses"></a>Genel bakış: Tehdidi hızla anlayın, etkisini değerlendirin ve savunmaları gözden geçirin

**Genel Bakış** bölümünde ayrıntılı analist raporunun önizlemesi sağlanır. Ayrıca, yanlış yapılandırılmış ve eşleşmeyen cihazlar aracılığıyla kuruluşunuza yönelik tehdidin etkisini ve açığa çıkarmanızı vurgulayan grafikler de sağlar.

:::image type="content" source="images/ta-overview.png" alt-text="Tehdit analizi raporunun Genel Bakış bölümü" lightbox="images/ta-overview.png":::
_Tehdit analizi raporunun genel bakış bölümü_

#### <a name="assess-the-impact-to-your-organization"></a>Kuruluşunuz üzerindeki etkiyi değerlendirme

Her rapor, bir tehdidin kurumsal etkisi hakkında bilgi sağlamak için tasarlanmış grafikler içerir:

- **Uyarı içeren cihazlar**: Tehdit tarafından etkilenen geçerli farklı cihaz sayısını gösterir. Bir cihaz, bu tehditle ilişkili en az bir uyarı varsa **Etkin** ve cihazdaki tehditle ilişkili *tüm* uyarılar çözümlendiyse **Çözümlendi** olarak kategorilere ayrılmıştır.
- **Zaman içinde uyarı içeren cihazlar: Zaman içinde** **Etkin** ve **Çözümlenmiş** uyarılara sahip farklı cihazların sayısını gösterir. Çözümlenen uyarı sayısı, kuruluşunuzun bir tehditle ilişkili uyarılara ne kadar hızlı yanıt verdiğini gösterir. İdeal olan grafikte birkaç gün içinde çözümlenen uyarıların gösterilmesi gerekir.

#### <a name="review-security-resilience-and-posture"></a>Güvenlik dayanıklılığını ve duruşu gözden geçirme

Her rapor, kuruluşunuzun belirli bir tehdide karşı ne kadar dayanıklı olduğuna ilişkin bir genel bakış sağlayan grafikler içerir:

- **Güvenlik yapılandırması durumu**: Tehdidin azaltılmasına yardımcı olabilecek önerilen güvenlik ayarlarını uygulayan cihaz sayısını gösterir. İzlenen _tüm_ ayarları uygulamış olan cihazlar **Güvenli** olarak kabul edilir.
- **Güvenlik açığı düzeltme eki uygulama durumu**: Tehdit tarafından yararlanılan güvenlik açıklarını gideren güvenlik güncelleştirmeleri veya düzeltme ekleri uygulayan cihazların sayısını gösterir.

### <a name="analyst-report-get-expert-insight-from-microsoft-security-researchers"></a>Analist raporu: Microsoft güvenlik araştırmacılarından uzman içgörüleri alma

Ayrıntılı uzman yazma işlemini okumak için **Analist raporu** bölümüne gidin. Çoğu rapor, MITRE ATT&CK çerçevesine eşlenen taktikler ve teknikler, kapsamlı öneri listeleri ve güçlü [tehdit avcılığı](advanced-hunting-overview.md) yönergeleri dahil olmak üzere saldırı zincirlerinin ayrıntılı açıklamalarını sağlar.

[Analist raporu hakkında daha fazla bilgi edinin](threat-analytics-analyst-reports.md)

### <a name="mitigations-review-list-of-mitigations-and-the-status-of-your-devices"></a>Azaltmalar: Risk azaltmaların listesini ve cihazlarınızın durumunu gözden geçirin

**Risk Azaltmalar** bölümünde, tehditlere karşı kurumsal dayanıklılığınızı artırmanıza yardımcı olabilecek belirli eyleme dönüştürülebilir önerilerin listesini gözden geçirin. İzlenen azaltmalar listesi şunları içerir:

- **Güvenlik güncelleştirmeleri: Güvenlik** açıkları için güvenlik güncelleştirmelerinin veya düzeltme eklerinin dağıtımı
- **Microsoft Defender Virüsten Koruma ayarları**
  - Güvenlik zekası sürümü
  - Bulut tabanlı koruma
  - İstenmeyebilecek uygulama (PUA) koruması
  - Gerçek zamanlı koruma

Bu bölümdeki azaltma bilgileri[, rapordaki](next-gen-threat-and-vuln-mgt.md) çeşitli bağlantılardan ayrıntılı detaya gitme bilgileri de sağlayan Tehdit ve Güvenlik Açığı Yönetimi verilerini içerir.

:::image type="content" source="images/ta-mitigations.png" alt-text="Tehdit analizi raporunun Risk Azaltmalar bölümü" lightbox="images/ta-mitigations.png":::


_Tehdit analizi raporunun Azaltmalar bölümü_

## <a name="additional-report-details-and-limitations"></a>Ek rapor ayrıntıları ve sınırlamaları

Raporları kullanırken aşağıdakileri göz önünde bulundurun:

- Verilerin kapsamı rol tabanlı erişim denetimi (RBAC) kapsamınıza göre belirlenmiştir. [Erişebileceğiniz gruplarda](machine-groups.md) cihazların durumunu görürsünüz.
- Grafikler yalnızca izlenen azaltmaları yansıtır. Grafiklerde gösterilmeyen ek risk azaltmaları için rapora genel bakış'a bakın.
- Risk azaltmalar tam dayanıklılığı garanti etmez. Sağlanan azaltmalar, dayanıklılığı artırmak için gereken mümkün olan en iyi eylemleri yansıtır.
- Cihazlar hizmete veri iletmediyse "kullanılamaz" olarak sayılır.
- Virüsten korumayla ilgili istatistikler Microsoft Defender Virüsten Koruma ayarlarına bağlıdır. Üçüncü taraf virüsten koruma çözümlerine sahip cihazlar "kullanıma sunuldu" olarak görünebilir.

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş avcılık ile tehditleri proaktif olarak bulma](advanced-hunting-overview.md)
- [Analist raporu bölümünü anlama](threat-analytics-analyst-reports.md)
- [Güvenlik zayıflıklarını ve açığa çıkarmaları değerlendirme ve çözme](next-gen-threat-and-vuln-mgt.md)
