---
title: Microsoft Defender for Identity için değerlendirme ortamını etkinleştirme
description: Algılayıcıyı yapılandırarak ve diğer Microsoft 365 Defender bilgisayarlardaki yerel yöneticileri keşfederek deneme laboratuvarında veya pilot ortamında Kimlik için Microsoft Defender'ı & ayarlayın.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 6910336dea0559ad241c240cde09d3929fe2e422
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63014136"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-identity"></a>Microsoft Defender for Identity için değerlendirme ortamını etkinleştirme

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Bu makale [, Kimlik için](eval-defender-identity-overview.md) Microsoft Defender değerlendirme ortamını ayarlama işleminin 2. adımıdır. Bu işlem hakkında daha fazla bilgi için genel bakış [makalesine bakın](eval-defender-identity-overview.md).

Kimlik için Microsoft Defender ortamınızı ayarlamak üzere aşağıdaki adımları kullanın. 

![Microsoft Defender değerlendirme ortamında Kimlik için Microsoft Defender'ı etkinleştirme adımları.](../../media/defender/m365-defender-identity-eval-enable-steps.png)

- [1. Adım. Kimlik Örneği için Defender'ı ayarlama](#step-1-set-up-the-defender-for-identity-instance)
- [2. Adım. Algılayıcıyı yükleyin ve yapılandıryın](#step-2-install-and-configure-the-sensor)
- [3. Adım. Makinelerde algılayıcıya göre olay günlüğü ve ara sunucu ayarlarını yapılandırma](#step-3-configure-event-log-and-proxy-settings-on-machines-with-the-sensor)
- [Adım 4. Diğer bilgisayarlardaki yerel yöneticilerin Kimlik için Defender'a izin verme](#step-4-allow-defender-for-identity-to-identify-local-admins-on-other-computers)

## <a name="step-1-set-up-the-defender-for-identity-instance"></a>Adım 1. Kimlik Örneği için Defender'ı ayarlama

Örneğinizi oluşturmak ve ardından bu örneği Active Directory ortamınıza bağlamak için Kimlik için Defender portalında oturum açın. 

|  |Adım     |Daha fazla bilgi  |
|---------|---------|---------|
|1     | Identity için Defender örneğini oluşturma        | [Hızlı Başlangıç: Kimlik örneği için Microsoft Defender'nızı oluşturma](/defender-for-identity/install-step1)        |
|2     | Bağlan için Defender örneğini Active Directory ormanınıza geri yükleme   | [Hızlı Başlangıç: Bağlan Ormanınıza göz atabilirsiniz](/defender-for-identity/install-step2)  |
| | |

## <a name="step-2-install-and-configure-the-sensor"></a>Adım 2. Algılayıcıyı yükleyin ve yapılandıryın

Ardından, şirket içi ortamınıza etki alanı denetleyicilerinde ve AD FS sunucularında Identity algılayıcısı için Defender'ı indirin, yükleyin ve yapılandırın.

|  |Adım     |Daha fazla bilgi  |
|---------|---------|---------|
|1     | Identity algılayıcıları için kaç Microsoft Defender'a ihtiyacınız olduğunu tespit edin.        | [Kimlik için Microsoft Defender kapasitesini planlama](/defender-for-identity/capacity-planning)   |
|2     | Algılayıcı kurulum paketini indirin  |  [Hızlı Başlangıç: Kimlik algılayıcısı kurulum paketi için Microsoft Defender'ı indirin](/defender-for-identity/install-step3)   |
|3     | Kimlik algılayıcısı için Defender'ı yükleme    |  [Hızlı Başlangıç: Kimlik algılayıcısı için Microsoft Defender'ı yükleme](/defender-for-identity/install-step4)       |
|4     | Algılayıcıyı yapılandırma       |  [Kimlik algılayıcısı ayarları için Microsoft Defender'ı yapılandırma ](/defender-for-identity/install-step5)   |
|   |         |         |

## <a name="step-3-configure-event-log-and-proxy-settings-on-machines-with-the-sensor"></a>Adım 3. Makinelerde algılayıcıya göre olay günlüğü ve ara sunucu ayarlarını yapılandırma

Algılayıcıyı yüklemiş olduğunuz makinelerde, algılama Windows etkinleştirmek ve geliştirmek için etkinlik günlüğü koleksiyonu ve İnternet ara sunucusu ayarlarını yapılandırabilirsiniz.

|  |Adım     |Daha fazla bilgi  |
|---------|---------|---------|
|1     | Olay Windows koleksiyonunu yapılandırma         | [Etkinlik Windows yapılandırma](/defender-for-identity/configure-windows-event-collection)        |
|2     | İnternet ara sunucusu ayarlarını yapılandırma        | [Kimlik Algılayıcısı için Microsoft Defender'nız için uç nokta ara sunucu ve İnternet bağlantı ayarlarını yapılandırma](/defender-for-identity/configure-proxy)        |
|   |         |         |

## <a name="step-4-allow-defender-for-identity-to-identify-local-admins-on-other-computers"></a>Adım 4. Diğer bilgisayarlardaki yerel yöneticilerin Kimlik için Defender'a izin verme

Identity lateral movement path algılaması için Microsoft Defender, belirli makinelerde yerel yöneticilerin tanımlanmasında yapılan sorguları kullanır. Bu sorgular, Kimlik Hizmeti hesabı için Defender kullanılarak SAM-R protokolüyle gerçekleştirilir. 

Bu Windows ve sunucuların Identity için Defender hesabının SAM-R gerçekleştirmesine izin olduğundan emin olmak için, Ağ erişim ilkesinde listelenen yapılandırılmış hesapların yanı sıra Kimlik için Defender hizmet hesabını eklemek için Grup İlkesinde değişiklik yapılması gerekir. Etki alanı denetleyicileri dışında tüm bilgisayarlara grup ilkeleri **uygulamayı unutmayın**.

Bunun nasıl yapılır yönergeleri için bkz. [SAM'ye uzaktan arama yapmak üzere Identity için Microsoft Defender'ı yapılandırma](/defender-for-identity/install-step8-samr). 

## <a name="next-steps"></a>Sonraki adımlar

Adım 3/ 3: [Kimlik için Pilot Microsoft Defender](eval-defender-identity-pilot.md)

Kimlik için [Microsoft Defender'ı Değerlendirme'ye genel bakış](eval-defender-identity-overview.md)

Değerlendirme ve pilot uygulama için [genel bakış Microsoft 365 Defender](eval-overview.md)