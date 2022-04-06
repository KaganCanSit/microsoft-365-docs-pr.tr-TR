---
title: İlk olayınız için güvenlik duruşunuzu hazırlama
description: Microsoft 365 Defender'daki ilk olayınız için Microsoft 365 kiracınızın güvenlik duruşu ayarlayın.
keywords: olaylar, uyarılar, araştırma, bağıntı, saldırı, makineler, cihazlar, kullanıcılar, kimlik, kimlik, posta kutusu, e-posta, 365, Microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 0dbff9e88ed00dd8aa08fd64543266c3aef75d79
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664094"
---
# <a name="prepare-your-security-posture-for-your-first-incident"></a>İlk olayınız için güvenlik duruşunuzu hazırlama

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- Microsoft 365 Defender

Olay işlemeye hazırlanmak, bir kuruluşun ağının farklı güvenlik olaylarından yeterli korumasını ayarlamayı içerir. Ulusal Standartlar ve Teknoloji Enstitüsü (NIST), güvenlik olayı riskini azaltmak için risk değerlendirmeleri, konak güvenliğini sağlamlaştırma, ağları güvenli bir şekilde yapılandırma ve kötü amaçlı yazılımları önleme gibi çeşitli güvenlik uygulamaları önerir.

Microsoft 365 Defender, olay önlemenin çeşitli yönlerini ele alınmasına yardımcı olabilir:

- [Sıfır Güven](/security/zero-trust/) çerçevesi uygulama
- [Microsoft Güvenli Puanı](microsoft-secure-score.md) ile puan atayarak güvenlik duruşunuzu belirleme
- [Tehdit ve](../defender-endpoint/next-gen-threat-and-vuln-mgt.md) Güvenlik Açığı Yönetimi'nde güvenlik açığı değerlendirmeleri aracılığıyla tehditleri önleme
- Tehdit analiziyle bunlara hazırlanmak için en son güvenlik [tehditlerini](threat-analytics.md) anlama

## <a name="step-1-implement-zero-trust"></a>Adım 1. Sıfır Güven uygulama

[Sıfır Güven](/security/zero-trust/), mobil iş gücü ve kullanıcılar, cihazlar, uygulamalar ve veriler dahil olmak üzere herhangi bir modern ortamın karmaşık doğasını dikkate alan tümleşik bir güvenlik felsefesi ve uçtan uca stratejidir. Tüm algılamaları tutarlı bir şekilde yönetmek için tek bir cam bölmesi sağlayarak Microsoft 365 Defender güvenlik operasyonları ekibinizin Sıfır Güven [yol gösterici ilkelerini](/security/zero-trust/#guiding-principles-of-zero-trust) uygulamasını kolaylaştırabilir.

Microsoft 365 Defender bileşenleri, Uç Nokta için Microsoft Defender verilerini tümleştirerek Sıfır Güven için Koşullu Erişim ilkeleri oluşturmak üzere uygulanan kural ihlallerini görüntüleyebilir  veya cihaz uyumluluk ilkeleri ve cihaz tabanlı Koşullu Erişim ilkelerinin uygulanması için bir bilgi kaynağı olarak diğer mobil güvenlik satıcıları.

Cihaz riski, bu cihazın kullanıcısı tarafından erişilebilecek kaynakları doğrudan etkiler. Belirli ölçütlere göre kaynaklara erişimin reddedilme şekli, Sıfır Güven ana temasıdır ve Microsoft 365 Defender güven düzeyi ölçütlerini belirlemek için gereken bilgileri sağlar. Örneğin, Microsoft 365 Defender Tehdit ve Güvenlik Açığı Yönetimi sayfası aracılığıyla bir cihazın yazılım sürümü düzeyini sağlayabilirken, Koşullu Erişim ilkeleri eski veya güvenlik açığı olan sürümleri olan cihazları kısıtlayabilir.

Otomasyon, bir Sıfır Güven ortamı uygulama ve korumanın önemli bir parçasıdır ve aynı zamanda olay yanıtı (IR) olaylarına yol açabilecek uyarı sayısını azaltır. Microsoft 365 Defender bileşenleri, [düzeltme eylemleri](m365d-autoir.md) (Microsoft 365 Defender portalındaki bir olay için araştırma olarak bilinir), bildirim eylemleri ve hatta [ServiceNow](https://microsoft.service-now.com/sp/) gibi destek biletleri oluşturma gibi otomatikleştirilebilir.

## <a name="step-2-determine-your-organizations-security-posture"></a>Adım 2. Kuruluşunuzun güvenlik duruşu belirleme

Bundan sonra kuruluşlar, geçerli güvenlik duruşunuzu belirlemek ve bunu nasıl geliştirebileceğinize ilişkin önerileri göz önünde bulundurmak için Microsoft 365 Defender'de [Microsoft Güvenli Puanını](microsoft-secure-score.md) kullanabilir. Puan ne kadar yüksek olursa, kuruluş tarafından o kadar fazla güvenlik önerisi ve iyileştirme eylemi gerçekleştirilmiştir. Farklı ürünlerde Güvenli Puan önerileri alınabilir ve kuruluşların puanlarını daha da yükseltmesine olanak tanıyabilirsiniz.

:::image type="content" source="../../media/first-incident-prepare/first-incident-secure-score.png" alt-text="Microsoft 365 Defender portalındaki Microsoft Güvenli Puan sayfası" lightbox="../../media/first-incident-prepare/first-incident-secure-score.png":::

## <a name="step-3-assess-your-organizations-vulnerability-exposure"></a>Adım 3. Kuruluşunuzun güvenlik açığına maruz kalma olasılığını değerlendirme

Olayların önlenmesi, devam eden kritik ve önemli güvenlik olaylarına odaklanmak için güvenlik operasyonları çalışmalarını kolaylaştırmaya yardımcı olabilir. Yazılım güvenlik açıkları genellikle veri hırsızlığına, veri kaybına veya iş operasyonlarının kesintiye uğramasına neden olabilecek saldırılar için önlenebilir bir giriş noktasıdır. Devam eden bir saldırı yoksa, güvenlik operasyonları kuruluşlarında kabul edilebilir bir [güvenlik açığı maruziyeti](../defender-endpoint/tvm-exposure-score.md) düzeyi elde etmek ve korumak için çaba göstermelidir.

Yazılım düzeltme eki uygulama ilerleme durumunuzu denetlemek için Uç Nokta için Defender'daki [Tehdit ve Güvenlik Açığı Yönetimi](../defender-endpoint/next-gen-threat-and-vuln-mgt.md) sayfasını ziyaret edin. Bu sayfaya **Microsoft 365 Defender Diğer kaynaklar** sekmesinden erişebilirsiniz.

:::image type="content" source="../../media/first-incident-prepare/first-incident-vulnerability.png" alt-text="Microsoft 365 Defender portalındaki Tehdit ve Güvenlik Açığı sayfası" lightbox="../../media/first-incident-prepare/first-incident-vulnerability.png":::

## <a name="4-understand-emerging-threats"></a>4. Yeni ortaya çıkan tehditleri anlama

Geçerli güvenlik tehdidi ortamını takip etmek için Microsoft 365 Defender portalında tehdit [analizini](threat-analytics.md) kullanın. Uzman Microsoft güvenlik araştırmacıları, Microsoft 365 aboneliğinizi, cihazlarınızı ve kullanıcılarınızı nasıl etkileyebileceğini anlamanız için en son siber tehditleri ayrıntılı olarak açıklayan raporlar oluşturur. Bu raporlar şunları içerebilir:

- Etkin tehdit aktörleri ve kampanyaları
- Popüler ve yeni saldırı teknikleri
- Kritik güvenlik açıkları
- Yaygın saldırı yüzeyleri
- Yaygın kötü amaçlı yazılım

Tehdit analizi ayrıca, ne kadar risk altında olduğunuzu ve bir rapor için geçerli etkin uyarılar olup olmadığını belirlemek için yapılandırmanıza ve uyarılarınıza da bakar.

Güvenlik duruşunuzu güçlendirmek ve saldırı yüzeyi alanınızı en aza indirmek için yeni ortaya çıkan bir tehdidin önerilerini uygulayabilirsiniz.

Microsoft 365 Defender portalının [Threat Analytics](threat-analytics.md) bölümünü düzenli olarak denetlemek için zaman ayırabilirsiniz. Daha fazla bilgi [için Microsoft 365 Defender için örnek güvenlik işlemlerine](incidents-overview.md#example-security-operations-for-microsoft-365-defender) bakın.

## <a name="next-step"></a>Sonraki adım

[Olayları önceliklendirmeyi ve analiz](first-incident-analyze.md) etmeyi öğrenin.

## <a name="see-also"></a>Ayrıca bkz.

- [Olaylara genel bakış](incidents-overview.md)
- [Olayları araştırın](investigate-incidents.md)
- [Olayları yönetin](manage-incidents.md)
