---
title: Üretim ortamınız içinde yer alan Office 365 için Microsoft Defender değerlendirme ortamını etkinleştirme
description: Deneme lisansları, MX Office 365 ve kabul edilen etki alanlarının ve gelen bağlantıların denetimini & için Microsoft Defender'ı etkinleştirme adımları.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 07/01/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: 4d2f77b41dccd5620b96d816869d7d7b6458a798
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63014208"
---
# <a name="enable-the-evaluation-environment"></a>Değerlendirme ortamını etkinleştirme

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Bu makale, Microsoft Defender için değerlendirme ortamını ayarlama işleminin [2/ 3](eval-defender-office-365-overview.md). adımıdır ve Office 365. Bu işlem hakkında daha fazla bilgi için genel bakış [makalesine bakın](eval-defender-office-365-overview.md).

Aşağıdaki adımları kullanarak bu destek için Microsoft Defender değerlendirmesini Office 365.

![Microsoft Defender değerlendirme ortamında Office 365 için Microsoft Defender'ı etkinleştirme adımları.](../../media/defender/m365-defender-office-eval-enable-steps.png)

- [1. Adım: Deneme lisanslarını etkinleştirme](#step-1-activate-trial-licenses)
- [2. Adım: Genel MX kaydını denetleme ve doğrulama](#step-2-audit-and-verify-the-public-mx-record)
- [3. Adım: Kabul edilen etki alanlarını denetleme](#step-3-audit-accepted-domains)
- [4. Adım: Gelen bağlayıcılarını denetleme](#step-4-audit-inbound-connectors)
- [5. Adım: Değerlendirmeyi etkinleştirme](#step-5-activate-the-evaluation)

## <a name="step-1-activate-trial-licenses"></a>1. Adım: Deneme lisanslarını etkinleştirme

Çevrimiçi ortamda veya kiracı yönetim portalında Office 365 Microsoft Defender'ında oturum açın.

1. Yönetim portalına gidin.
2. Hızlı başlat'tan Hizmetleri Satın Alın'ı seçin.

   :::image type="content" source="../../media/mdo-eval/1_m365-purchase-services.png" alt-text="Gezinti bölmesinde Hizmetleri satın alın'a Office 365.":::

3. Uygulama planları Add-On Microsoft Defender'ı bulmak için sayfayı aşağı kaydırın (veya "Defender" Office 365 bulun.
4. Değerlendirmek istediğiniz planın yanındaki Ayrıntılar'a tıklayın.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="Ayrıntılar düğmesini ve ardından tıklayın.":::

5. Ücretsiz *denemeyi başlat bağlantısına* tıklayın.

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Bu panelde Ücretsiz denemeyi *köprüyü* başlat'a tıklayın.":::

6. İsteğinizi onaylayın ve Şimdi *deneyin düğmesine* tıklayın.

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Şimdi Şimdi deneyin *düğmesine* tıklayın.":::

## <a name="step-2-audit-and-verify-the-public-mx-record"></a>2. Adım: Genel MX kaydını denetleme ve doğrulama

Office 365 için Microsoft Defender'ı etkili bir şekilde değerlendirmek için, gelen dış e-postanın kiracınıza ilişkin Exchange Online Protection (EOP) örneğinden geçişli olması önemlidir.

1. M365 Yönetim Portalı'ta oturum açın, Etki Alanları'Ayarlar'ı seçin.
2. Doğrulanmış e-posta etki alanınızı seçin ve DNS'yi Yönet'e tıklayın.
3. Oluşturulan ve EOP kiracınıza atanmış MX kaydını notun.
4. Dış (genel) DNS bölgenize erişin ve e-posta etki alanıyla ilişkilendirilmiş birincil MX kaydını kontrol edin.
    - *Genel MX kaydınız şu anda atanmış EOP adresiyle eş değişiyorsa (örneğin, tenant-com.mail.protection.outlook.com) başka yönlendirme değişikliğine gerek yoktur*.
    - Genel MX kaydınız şu anda üçüncü taraf veya şirket içi SMTP ağ geçidine çözüm çözüme sahipse, ek yönlendirme yapılandırmaları gerekebilir.
    - Genel MX kaydınız şu anda şirket içi posta Exchange, bazı alıcı posta kutularının EXO'ye geçirilemezse hala karma bir modeldeyebilirsiniz.

## <a name="step-3-audit-accepted-domains"></a>3. Adım: Kabul edilen etki alanlarını denetleme

1. Yönetim Portalı'Exchange Online açın, Posta Posta'yı Flow kabul edilen Etki Alanları'ne tıklayın.
2. Kiracınıza eklenmiş ve doğrulanmış kabul edilen etki alanları listesinden, birincil e-posta etki **alanınız için etki** alanı türünü not alın.
    - Etki alanı türü Yetkili ***olarak ayarlanırsa***, o anda kuruluş için tüm alıcı posta kutularının Yetkili olarak Exchange Online.
    - Etki alanı türü İç Geçiş olarak ***ayarlanırsa*** , bazı alıcı posta kutularının hala şirket içinde bulunduğu karma bir modelde olabilirsiniz.

## <a name="step-4-audit-inbound-connectors"></a>4. Adım: Gelen bağlayıcılarını denetleme

1. Yönetici Portalı'Exchange Online açın, Posta Posta'yı Flow Bağlayıcılar'a tıklayın.
2. Yapılandırılmış bağlayıcılar listesinde, İş Ortağı Kuruluş'tan gelen ve üçüncü taraf bir SMTP ağ geçidiyle ilişkili olan tüm girdileri not olun.
3. Yapılandırılmış bağlayıcılar listesinden, Kuruluş e-posta sunucusundan etiketlenmiş olan ve hala  karma senaryoda olduğunuz belirten tüm girdileri not alın.

## <a name="step-5-activate-the-evaluation"></a>5. Adım: Değerlendirmeyi etkinleştirme

Microsoft Defender for Office 365 değerlendirmesini etkinleştirmek için buradaki yönergeleri Microsoft 365 Defender kullanın.

1. Kiracınıza erişim izni olan bir hesap ile kiracınıza Microsoft 365 Defender açın.
2. Microsoft 365 Defender portalını, **Office 365** için Microsoft Defender için varsayılan arabiriminiz yapmak isteyip Office 365 seçin.

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-activate-eval.png" alt-text="Merkezi ve gelişmiş yönetim portalını kullanmak için Ayarları Microsoft 365 Defender düğmesine tıklayın.":::

3. Gezinti menüsünde, E-posta **ve & altında İlkeler** *ve Kurallar'ı & seçin*.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-activate-eval.png" alt-text="Burada, İlkeler ve &'a işaret alan bir E-posta Ve İşbirliği & resmi yer alır. Tıklayın!":::

4. İlke *Ve & panosunda* Tehdit **İlkeleri'ne tıklayın**.

   :::image type="content" source="../../media/mdo-eval/3_mdo-eval-activate-eval.png" alt-text="İlke Ve Kurallar & ve Tehdit ilkelerine işaret ediyor bir ok resmi. Bu sonrakine tıklayın!":::

5. Sayfayı Ek *İlkeler'e* kadar aşağı kaydırın **ve İlkeler için Defender'ı Office 365** seçin.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-activate-eval.png" alt-text="Bunun e-posta Office 365 30 günlük bir deneme olduğunu söyleyen ve işbirliği vektörleri için Eval Defender & kutucuğu. Üzerinden geç'e tıklayın.":::

6. Şimdi, dış e-postanın doğrudan mı Exchange Online yoksa üçüncü taraf bir ağ geçidine mi yoksa hizmete mi yönlendireceklerini seçin ve Sonraki'ye tıklayın.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-activate-eval.png" alt-text="Posta Office 365 Defender, posta kutunuza gelen Exchange Online değerlendirir. Postanızı postanıza yönlendiren giden bağlayıcının adı da dahil olmak üzere, postanın nasıl yönlendirildiklerinin ayrıntılarını iletin. Yalnızca başka Exchange Online Protection (EOP) kullanıyorsanız bağlayıcıniz olmayacak. Üçüncü taraf sağlayıcı veya şirket içi sağlayıcıdan birini veya yalnızca EOP'yi kullanıyorum'ı seçin.":::

7. Üçüncü taraf bir ağ geçidi kullanıyorsanız, açılan listeden satıcı adını ve bu çözümle ilişkilendirilmiş gelen bağlayıcıyı seçin. Yanıtlarınızı listeleninca, Sonraki'ye tıklayın.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png" alt-text="Bu iletişim kutusunda, kuruma göre üçüncü taraf satıcı hizmetini seçersiniz veya *Diğer* seçeneğini belirleyebilirsiniz. Sonraki iletişim kutusunda gelen bağlayıcıyı seçin. Ardından, Sonraki'ne tıklayın.":::

8. Ayarlarınızı gözden geçirin ve Değerlendirme **Oluştur düğmesine** tıklayın.

   |Önce|Sonra|
   |:---:|:---:|
   |:::image type="content" source="../../media/mdo-eval/7-mdo-eval-activate-review.png" alt-text="Bu bölmede ayarlarınızı gözden geçirmek için bir açılan liste vardır. Ayrıca, gerekirse Yönlendirme türlerinizi düzenlemeniz için tıklanabilir bir bağlantısı da vardır. Hazırken büyük mavi Değerlendirme Oluştur düğmesine tıklayın.":::|:::image type="content" source="../../media/mdo-eval/8-mdo-eval-activate-complete.png" alt-text="Artık ayarlama tamamlanmıştır. Bu sayfada mavi düğme &quot;Değerlendirmeye Git&quot; yazıyor.":::|
   |

## <a name="next-steps"></a>Sonraki adımlar

Adım 3 / 3: Microsoft Defender için pilot ayarlama hakkında daha fazla Office 365

Windows için [Microsoft Defender'ı Değerlendirme genel görünümüne Office 365](eval-defender-office-365-overview.md)

Değerlendirme ve pilot uygulama için [genel bakış Microsoft 365 Defender](eval-overview.md)
