---
title: Uç nokta tehdit analizi için Microsoft Defender'la ortaya çıkan tehditleri izleme ve yanıtlama
ms.reviewer: ''
description: Ortaya çıkan tehdit ve saldırı tekniklerini ve bunları nasıl durduracaklarını anlıyoruz. Organizasyon üzerindeki etkisini değerlendirin ve organizasyona karşı etkilerinızı değerlendirin.
keywords: tehdit analizi, risk değerlendirme, işletim sistemi azaltma, mikro kod azaltma, risk azaltma durumu
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
ms.openlocfilehash: 1c86dad2f303df149921efab87d3ffd026e0f93d
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998202"
---
# <a name="track-and-respond-to-emerging-threats-through-threat-analytics"></a>Tehdit analizleri aracılığıyla ortaya çıkan tehditleri takip edin ve yanıt verin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Sık sık ve yaygın olarak ortaya çıkan daha gelişmiş rakipler ve yeni tehditlerle, hızla devam etmek kritik öneme sahip:

- Yeni tehditlerin etkisini değerlendirme
- Tehditlere karşı olan belki de tehditlere karşı olan korumanızı gözden geçirme
- Tehditleri durdurmak veya tehditlere karşı eylemlerini belirlemek

Tehdit analizi, en ilgili tehditleri kapsayan, uzman Microsoft güvenlik araştırmacısı tarafından alınan, aşağıdakiler gibi bir dizi rapor içerir:

- Etkin tehdit tehditlerini ve onların kampanyalarını tehdit ediyor
- Popüler ve yeni saldırı teknikleri
- Kritik güvenlik açıkları
- Yaygın saldırı yüzeyleri
- Yaygın kötü amaçlı yazılım

Her rapor, bu tehdite karşı savunma konusunda kapsamlı bir tehdit ve kapsamlı bir yol gösterici analiz sağlar. Ayrıca, ağınıza gelen, tehdidin etkin olup olmadığını ve geçerli korumalara sahip olup olmadığınızı gösteren verileri de bir almaktadır.

Tehdit analizinin en son tehditleri izleme ve bunları durdurma konusunda nasıl yardımcı olduğu hakkında daha fazla bilgi edinmek için bu kısa videoyu izleyin.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bw1f]

## <a name="view-the-threat-analytics-dashboard"></a>Tehdit analiz panosuyu görüntüleme

Tehdit çözümlemesi panosu, organizasyonuyla en ilgili raporlara almak için mükemmel bir atlama noktasıdır. Aşağıdaki bölümlerdeki tehditleri özetler:

- **En son** tehdit: En son yayımlanan tehdit raporlarının yanı sıra etkin ve çözümlenmiş uyarıları olan cihazların sayısını da listeler.
- **Çok etkili tehdit:** Kuruluşta en çok etkiyi alan tehditleri listeler. Bu bölümde, etkin uyarılara sahip cihazların sayısına göre tehdit sıralarız.
- **Tehdit özeti**: Etkin ve çözümlenmiş uyarılarla birlikte tehdit sayısını göstererek, izlenmiş tehditlerin genel etkisini gösterir.

Bu tehdidin raporunu görüntülemek için panodan bir tehdit seçin.

![Tehdit analiz panosunun resmi.](images/ta_dashboard.png)

## <a name="view-a-threat-analytics-report"></a>Tehdit analizi raporunu görüntüleme

Her tehdit analizi raporu üç bölümde bilgi sağlar: **Genel Bakış**, **Analist raporu** ve **Risk Azaltmalar**.

### <a name="overview-quickly-understand-the-threat-assess-its-impact-and-review-defenses"></a>Genel bakış: Tehdidi hızlı bir şekilde anlıyoruz, etkisini değerlendirin ve savunmayı gözden geçirme

Genel **Bakış** bölümü, ayrıntılı analist raporunun bir önizlemesini sağlar. Ayrıca, hatalı ve eşleşmeyen cihazlar aracılığıyla organizasyonunız için tehdidin etkisini vurgulayan grafikler de sağlar.

![Tehdit analizi raporunun genel bakış bölümünün görüntüsü.](images/ta-overview.png)
 _Tehdit analizi raporunun genel bakış bölümü_

#### <a name="assess-the-impact-to-your-organization"></a>Organizasyonun etkisini değerlendirme

Her rapor, bir tehdidin kurumsal etkisi hakkında bilgi sağlamak için tasarlanmış grafikler içerir:

- **Uyarılı cihazlar**: Tehdit tarafından etkisi olan farklı cihazların mevcut sayısını gösterir. Bir cihaz, bu **tehditle ilişkilendirilmiş** en az bir uyarı varsa Etkin olarak kategorilere ayrılmıştır; cihaza yönelik tehditle ilişkili tüm uyarılar çözümlenmişse Çözümlendi demektir.
- **Zaman içinde uyarı alan cihazlar**: Etkin ve Zaman içinde Çözümlenmiş uyarılarının **olduğu** **farklı** cihazların sayısını gösterir. Çözülen uyarıların sayısı, kuruluşun bir tehditle ilişkilendirilmiş uyarılara ne kadar hızlı yanıt veremediklerine işaret ediyor. İdeal olan, grafiğin birkaç gün içinde çözülen uyarıları göstermesidir.

#### <a name="review-security-resilience-and-posture"></a>Güvenlik inalisini ve şuurlarını gözden geçirme

Her raporda, kuruma yönelik olarak verilen bir tehdite karşı ne kadar uygun olduğuyla ilgili genel bir bakış sağlayan grafikler yer almaktadır:

- **Güvenlik yapılandırması durumu**: Tehdidi azaltmak için yardımcı olmak için önerilen güvenlik ayarlarının uygulandığı cihazların sayısını gösterir. Tüm izleme **ayarlarını uyguladıkları** cihazlar _Güvenli_ olarak kabul edilir.
- **Güvenlik açığı düzeltme eki durumu**: Tehdit tarafından yararlanan güvenlik açıkları için güvenlik güncelleştirmeleri veya yamalar kullanan cihazların sayısını gösterir.

### <a name="analyst-report-get-expert-insight-from-microsoft-security-researchers"></a>Analist raporu: Microsoft güvenlik araştırmacısı'nın uzman içgörülerini alın

Ayrıntılı uzman **yazılarını okumak** için Analist raporu bölümüne gidin. Raporların çoğu, MITRE ATT&CK çerçevesine eşlenen taktikler ve teknikler, çok kapsamlı öneri listeleri ve güçlü tehdit arama kılavuzu dahil olmak üzere saldırı zincirleri hakkında [ayrıntılı açıklamalar sağlar](advanced-hunting-overview.md) .

[Analist raporu hakkında daha fazla bilgi](threat-analytics-analyst-reports.md)

### <a name="mitigations-review-list-of-mitigations-and-the-status-of-your-devices"></a>Azaltmalar: Risk azaltma listesini ve cihazlarınızı durumunu gözden geçirme

Azaltmalar **bölümünde** , tehditlere karşı kuruluşa karşı daha fazla özgü, eyleme geçirilebilir öneriler listesini gözden geçirebilirsiniz. İzli risk azaltmalar listesi şunları içerir:

- **Güvenlik güncelleştirmeleri**: Güvenlik güncelleştirmelerinin veya güvenlik açıkları için yamaların dağıtımı
- **Microsoft Defender Virüsten Koruma ayarları**
  - Güvenlik zekası sürümü
  - Bulut teslimi koruma
  - İstenmeyen olabilecek uygulama (PUA) koruması
  - Gerçek zamanlı koruma

Bu bölümdeki azaltma bilgileri, rapor Tehdit ve Güvenlik Açığı Yönetimi çeşitli bağlantılarından [](next-gen-threat-and-vuln-mgt.md)ayrıntılı detaya gitme bilgileri de sağlayan veri bağlantılarını içerir.

![Tehdit analizi raporunun risk azaltma bölümünün resmi.](images/ta-mitigations.png)

_Tehdit analizi raporunun Azaltmalar bölümü_

## <a name="additional-report-details-and-limitations"></a>Ek rapor ayrıntıları ve sınırlamaları

Raporları kullanırken şunları unutmayın:

- Veriler, rol tabanlı erişim denetimi (RBAC) kapsamınıza göre ele alındı. Erişebilirsiniz gruplar halinde [cihazların durumunu gösterir](machine-groups.md).
- Grafikler yalnızca izlenen risk azaltmalarını yansıttır. Grafiklerde gösterülen ek risk azaltmaları için rapora genel bakış bilgilerine bakın.
- Azaltmalar tam bir teminat garanti etmez. Sağlanan azaltmalar, performansı geliştirmek için gereken en iyi olası eylemleri yansıttır.
- Aygıtlar hizmete veri aktarmamışsa "kullanılamaz" olarak sayılır.
- Virüsten korumayla ilgili istatistikler veri Microsoft Defender Virüsten Koruma temel Microsoft Defender Virüsten Koruma temel almaktadır. Üçüncü taraf virüsten koruma çözümlerine sahip cihazlar "açık" olarak görünebilir.

## <a name="related-topics"></a>İlgili konular

- [Gelişmiş avla tehditlere karşı önceden bulma](advanced-hunting-overview.md)
- [Analist raporu bölümünü anlama](threat-analytics-analyst-reports.md)
- [Güvenlik açıklarını ve pozlama durumlarını değerlendirin ve çözüm bulun](next-gen-threat-and-vuln-mgt.md)
