---
title: İlk olayınız için güvenlik nedenlerinizi hazırlama
description: Kiracınıza Microsoft 365 ilk olayınız için güvenlik nedenini Microsoft 365 Defender.
keywords: olaylar, uyarılar, araştırma, korelasyon, saldırı, makineler, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, m365
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
ms.openlocfilehash: c3b86a133b5126029378018fdac821d5423b2761
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63321871"
---
# <a name="prepare-your-security-posture-for-your-first-incident"></a>İlk olayınız için güvenlik nedenlerinizi hazırlama

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Olay işlemeye hazırlanmak, kuruluş ağının farklı güvenlik olaylarından yeterince korunmasını gerektirir. Ulusal Standartlar ve Teknoloji Enstitüsü (NIST) güvenlik olaylarının riskini azaltmak için, risk değerlendirmeleri, ana bilgisayar güvenliğini koruma, ağları güvenli bir şekilde yapılandırma ve kötü amaçlı yazılımları önleme gibi çeşitli güvenlik uygulamaları önermektedir. 

Microsoft 365 Defender önlemenin çeşitli yönlerine yönelik olarak yardımcı olabilir: 

- Sıfır Güven [Çerçevesi](/security/zero-trust/) uygulama
- Microsoft Güvenli Puanı ile bir puan ataarak güvenlik [nedenlerinizi belirleme](microsoft-secure-score.md)
- Tehdit ve Güvenlik Açığı Yönetimi'nin güvenlik açığı [değerlendirmesi yoluyla tehditleri engelleme](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)
- Tehdit analizi ile bu tehditlere hazırlanmak için en son güvenlik [tehditlerini anlama](threat-analytics.md)

## <a name="step-1-implement-zero-trust"></a>Adım 1. Sıfır Güveni Uygulama

[Sıfır Güven](/security/zero-trust/) , mobil iş gücü ve kullanıcılar, cihazlar, uygulamalar ve veriler dahil olmak üzere nerede bulunursa olsunlar her modern ortamın karmaşık doğasını göz önünde bulunduran, tümleşik bir güvenlik stratejisidir. Tek bir cam bölmesi sağlayarak tüm algılamaları tutarlı bir şekilde yönetecek şekilde Microsoft 365 Defender, güvenlik işlemleri ekibinin Sıfır Güven'in yol gösteren ilkelerini uygulamalarını kolaylaştırabilirsiniz.[](/security/zero-trust/#guiding-principles-of-zero-trust) 

Microsoft 365 Defender bileşenleri, Uç Nokta için Microsoft Defender'dan veya diğer mobil güvenlik satıcılarından alınan verileri cihaz uyumluluğu ilkeleri ve cihaz tabanlı Koşullu Erişim ilkelerinin uygulanması için bilgi kaynağı olarak tümleştirerek Sıfır Güven için Koşullu Erişim ilkeleri kurmak için uygulanmış olan kuralların ihlallerini ebilir. 

Cihaz riski, bu cihazın kullanıcısı tarafından erişilebilen kaynakları doğrudan etkiler. Belirli ölçütlere dayalı kaynaklara erişim engellemesi, Sıfır Güven'in ana temasıdır ve Microsoft 365 Defender, güven düzeyi ölçütlerini belirlemek için gereken bilgileri sağlar. Örneğin, Microsoft 365 Defender bir cihazın yazılım sürüm düzeyini Tehdit ve Güvenlik Açığı Yönetimi sayfası aracılığıyla s alırken, Koşullu Erişim ilkeleri eski veya korumasız sürümleri olan cihazları kısıtlar.

Otomasyon, Sıfır Güven ortamını uygulamanın ve korumanın çok önemli bir parçasıyken, aynı zamanda olay yanıtı (IR) olaylarına yol açabilecek uyarı sayısını da azaltmaktır. Microsoft 365 Defender bileşenleri düzeltme [eylemleri (Microsoft 365 Defender](m365d-autoir.md) portalında bir olay için soruşturmalar olarak bilinir), bildirim eylemleri ve hatta [ServiceNow](https://microsoft.service-now.com/sp/) gibi destek biletleri oluşturma gibi otomatik hale kullanılabilir.

## <a name="step-2-determine-your-organizations-security-posture"></a>Adım 2. Kuruluş güvenlik nedenini belirleme

Kuruluşlar bundan sonra, geçerli güvenlik Microsoft 365 Defender [](microsoft-secure-score.md) belirlemek ve bunu nasıl geliştirecek önerileri göz önünde bulundurarak, Güvenlik Puanı'nın kullanımına açık hale geldi. Puan ne kadar yüksek olduğu, kuruluş tarafından o kadar fazla güvenlik önerisi ve iyileştirme eylemi gerçekleştirildi. Güvenli Puan önerileri farklı ürünler arasında alınarak kuruluşların puanlarını daha da yükseltmesine olanak sağlar. 

:::image type="content" source="../../media/first-incident-prepare/first-incident-secure-score.png" alt-text="Microsoft güvenlik merkezinde Microsoft Güvenli Puanı örneği.":::
 
## <a name="step-3-assess-your-organizations-vulnerability-exposure"></a>Adım 3. Kuruluş güvenlik açığının etkilenmeye açık olduğunu değerlendirin

Olayları engellemek, devam edecek kritik ve önemli güvenlik olaylarına odaklanmaya yönelik güvenlik işlemleri çabalarının kolaylaştırmalarına yardımcı olabilir. Yazılım açıkları çoğunlukla veri hırsızlığına, veri kaybına veya iş işlemlerinin kesintiye neden olduğu saldırılar için önlenebilir bir giriş noktasıdır. Devam eden bir saldırı yoksa, güvenlik işlemlerinin kuruluşlarında kabul edilebilir bir güvenlik açığı seviyesine ulaşmak ve bunu korumak [için](../defender-endpoint/tvm-exposure-score.md) çabalaması gerekir.

Yazılım düzeltme eki uygulama ilerlemenizi kontrol etmek için, [](../defender-endpoint/next-gen-threat-and-vuln-mgt.md) Diğer kaynaklar sekmesi aracılığıyla Microsoft 365 Defender'den erişebilirsiniz, Uç Nokta için Defender'daki Tehdit ve Güvenlik Açığı Yönetimi **sayfasını ziyaret** edin.

:::image type="content" source="../../media/first-incident-prepare/first-incident-vulnerability.png" alt-text="Microsoft güvenlik merkezinde Tehdit ve Güvenlik Açığı sayfası örneği."::: 
 
## <a name="4-understand-emerging-threats"></a>4. Ortaya çıkan tehditleri anlama

Mevcut [güvenlik](threat-analytics.md) tehdit Microsoft 365 Defender güncel tutmak için portalda tehdit çözümlemelerini kullanın. Uzman Microsoft güvenlik uzmanı en son siber tehditleri ayrıntılı olarak açıklayan raporlar oluşturabilir ve böylece bunların Microsoft 365, cihaz ve kullanıcılarınızı nasıl etkileyebileceklerini anlıyoruz. Bu raporlar şunları içerebilir:

- Etkin tehdit tehditlerini ve onların kampanyalarını tehdit ediyor
- Popüler ve yeni saldırı teknikleri
- Kritik güvenlik açıkları
- Yaygın saldırı yüzeyleri
- Yaygın kötü amaçlı yazılım

Tehdit çözümlemeleri aynı zamanda yapılandırmanıza ve ne kadar risk altında olduğunu ve rapor için geçerli etkin uyarılar olup olmadığını belirlemek için uyarıları da okur.

Güvenliğinizi güçlendirmek ve saldırı alanınızı en aza indirmek için ortaya çıkan bir tehdit önerilerinin önerilerini gerçekleştirabilirsiniz.

Zamanlamanıza göre zaman çizelgenizin Tehdit Çözümlemesi [bölümünü](threat-analytics.md) düzenli olarak kontrol etmek Microsoft 365 Defender edinin. Daha fazla [bilgi için güvenlik Microsoft 365 Defender](incidents-overview.md#example-security-operations-for-microsoft-365-defender) örnek güvenlik işlemlerine bakın.

## <a name="next-step"></a>Sonraki adım

[![1. Adım: Olayları değerlendirmeyi ve çözümlemeyi öğrenin.](../../media/first-incident-overview/first-incident-path-step1.png)](first-incident-analyze.md)

Olayları değerlendirmeyi [ve çözümlemeyi öğrenin](first-incident-analyze.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Olaylara genel bakış](incidents-overview.md)
- [Olayları araştırma](investigate-incidents.md)
- [Olayları yönetme](manage-incidents.md)
