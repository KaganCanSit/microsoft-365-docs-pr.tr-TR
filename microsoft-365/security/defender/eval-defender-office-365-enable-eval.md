---
title: Üretim ortamınıza bu Office 365 için Microsoft Defender değerlendirme ortamını etkinleştirme
description: Deneme lisansları Office 365 için Microsoft Defender MX kaydı işleme ve kabul edilen etki & gelen bağlantıların denetimini etkinleştirme adımları.
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
ms.openlocfilehash: a5a14d507f7cd10ff4f7ab62b552ab256f0e4a5e
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499011"
---
# <a name="enable-the-evaluation-environment"></a>Değerlendirme ortamını etkinleştirme

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Bu makale, [değerlendirme ortamını ayarlama sürecindeki adım 2/ 3'ü](eval-defender-office-365-overview.md) ve Office 365 için Microsoft Defender. Bu işlem hakkında daha fazla bilgi için genel bakış [makalesine bakın](eval-defender-office-365-overview.md).

Bu sorunu değerlendirmeyi etkinleştirmek için aşağıdaki Office 365 için Microsoft Defender.

:::image type="content" source="../../media/defender/m365-defender-office-eval-enable-steps.png" alt-text="Microsoft Defender değerlendirme Office 365 için Microsoft Defender bu özellikleri etkinleştirme adımları" lightbox="../../media/defender/m365-defender-office-eval-enable-steps.png":::


- [1. Adım: Deneme lisanslarını etkinleştirme](#step-1-activate-trial-licenses)
- [2. Adım: Genel MX kaydını denetleme ve doğrulama](#step-2-audit-and-verify-the-public-mx-record)
- [3. Adım: Kabul edilen etki alanlarını denetleme](#step-3-audit-accepted-domains)
- [4. Adım: Gelen bağlayıcılarını denetleme](#step-4-audit-inbound-connectors)
- [5. Adım: Değerlendirmeyi etkinleştirme](#step-5-activate-the-evaluation)

## <a name="step-1-activate-trial-licenses"></a>1. Adım: Deneme lisanslarını etkinleştirme

Mevcut yönetim ortamınıza veya Office 365 için Microsoft Defender yönetim portalınıza oturum açın.

1. Yönetim portalına gidin.
2. Hızlı başlat'tan Hizmetleri Satın Alın'ı seçin.

   :::image type="content" source="../../media/mdo-eval/1_m365-purchase-services.png" alt-text="Hizmet satın alma seçeneğine tıklamak için Microsoft 365 yönetim merkezi" lightbox="../../media/mdo-eval/1_m365-purchase-services.png":::

3. En iyi planları Add-On için sayfayı aşağı kaydırın (veya "Defender" Office 365 için Microsoft Defender bulun.
4. Değerlendirmek istediğiniz planın yanındaki Ayrıntılar'a tıklayın.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="Tıklı olacak Ayrıntılar düğmesi" lightbox="../../media/mdo-eval/2_mdo-eval-license-details.png":::

5. Ücretsiz *denemeyi başlat bağlantısına* tıklayın.

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Ücretsiz denemeyi başlat köprüsü" lightbox="../../media/mdo-eval/3-m365-purchase-button.png":::

6. İsteğinizi onaylayın ve Şimdi *deneyin düğmesine* tıklayın.

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Şimdi deneyin düğmesi" lightbox="../../media/mdo-eval/4_mdo-trial-order.png":::

## <a name="step-2-audit-and-verify-the-public-mx-record"></a>2. Adım: Genel MX kaydını denetleme ve doğrulama

Kiracınızı etkili Office 365 için Microsoft Defender için, gelen dış e-postanın kiracınıza ilişkin Exchange Online Protection (EOP) örneğinden geçişli olması önemlidir.

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

Değerlendirme değerlendirmenizi etkinleştirmeniz için buradaki Office 365 için Microsoft Defender portaldan Microsoft 365 Defender kullanın.

1. Kiracınıza erişim izni olan bir hesap ile kiracınıza Microsoft 365 Defender açın.
2. Microsoft 365 Defender portalını yönetim **için varsayılan Office 365 için Microsoft Defender** yapmak isteyip Office 365 için Microsoft Defender seçin.

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-activate-eval.png" alt-text="Merkezi ve geliştirilmiş Ayarlar yönetim portalına liderlik yapmak için Microsoft 365 Defender düğmesi" lightbox="../../media/mdo-eval/1_mdo-eval-activate-eval.png":::

3. Gezinti menüsünde, E-posta **ve & altında İlkeler** *ve Kurallar'ı & seçin*.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-activate-eval.png" alt-text="the Policies & rules menu item to clicked" lightbox="../../media/mdo-eval/2_mdo-eval-activate-eval.png":::

4. İlke *Ve & panosunda* Tehdit **İlkeleri'ne tıklayın**.

   :::image type="content" source="../../media/mdo-eval/3_mdo-eval-activate-eval.png" alt-text="Tıklı olacak Tehdit ilkeleri menü öğesi" lightbox="../../media/mdo-eval/3_mdo-eval-activate-eval.png":::

5. Sayfayı Ek *İlkeler'e* kadar aşağı **kaydırın ve Office 365 için Defender** seçin.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-activate-eval.png" alt-text="Eval Office 365 için Defender kutucuğu" lightbox="../../media/mdo-eval/4_mdo-eval-activate-eval.png":::

6. Şimdi, dış e-postanın doğrudan mı Exchange Online yoksa üçüncü taraf bir ağ geçidine mi yoksa hizmete mi yönlendireceklerini seçin ve Sonraki'ye tıklayın.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-activate-eval.png" alt-text="Office 365 için Microsoft Defender portalında Yönlendirme ayarları bölmesi" lightbox="../../media/mdo-eval/5_mdo-eval-activate-eval.png":::

7. Üçüncü taraf bir ağ geçidi kullanıyorsanız, açılan listeden satıcı adını ve bu çözümle ilişkilendirilmiş gelen bağlayıcıyı seçin. Yanıtlarınızı listeleninca, Sonraki'ye tıklayın.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png" alt-text="Office 365 için Microsoft Defender portalında Üçüncü taraf veya şirket içi ayarlar bölmesi" lightbox="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png":::

8. Ayarlarınızı gözden geçirin ve Değerlendirme **Oluştur düğmesine** tıklayın.

   |Önce|Sonra|
   |:---:|:---:|
   |:::image type="content" source="../../media/mdo-eval/7-mdo-eval-activate-review.png" alt-text="Office 365 için Microsoft Defender portalında Ayarlarınızı gözden geçirme bölmesi" lightbox="../../media/mdo-eval/7-mdo-eval-activate-review.png":::|:::image type="content" source="../../media/mdo-eval/8-mdo-eval-activate-complete.png" alt-text="Office 365 için Microsoft Defender portalında Değerlendirme Office 365 için Microsoft Defender bildirimi" lightbox="../../media/mdo-eval/8-mdo-eval-activate-complete.png":::|
   |

## <a name="next-steps"></a>Sonraki adımlar

Adım 3 / 3: Test için pilot Office 365 için Microsoft Defender

Değerlendirme görünümüne genel [bakış Office 365 için Microsoft Defender](eval-defender-office-365-overview.md)

Değerlendirme ve pilot uygulama için [genel bakış Microsoft 365 Defender](eval-overview.md)
