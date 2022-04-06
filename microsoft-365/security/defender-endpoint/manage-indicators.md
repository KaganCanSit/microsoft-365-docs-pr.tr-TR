---
title: Göstergeleri oluşturun
ms.reviewer: ''
description: Varlıkların algılanmasını, önlenmesini ve dışlanmasını tanımlayan dosya karması, IP adresi, URL'ler veya etki alanları için göstergeler oluşturun.
keywords: yönet, izin verildi, engellendi, engelle, temiz, kötü amaçlı, dosya karması, IP adresi, URL'ler, etki alanı
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 55f9529d511435eb66f2791fe8a177a9fa35a8a5
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666338"
---
# <a name="create-indicators"></a>Göstergeleri oluşturun

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
>
> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Risk (ICS) eşleştirmesinin göstergesi, her uç nokta koruma çözümünde önemli bir özelliktir. Bu özellik SecOps'a algılama ve engelleme (önleme ve yanıt) için göstergelerin listesini ayarlama olanağı verir.

Varlıkların algılanmasını, önlenmesini ve dışlanmasını tanımlayan göstergeler oluşturun. Gerçekleştirilecek eylemin yanı sıra eylemin ne zaman uygulanacağının süresini ve uygulanacağı cihaz grubunun kapsamını tanımlayabilirsiniz.

Şu anda desteklenen kaynaklar Uç Nokta için Defender'ın bulut algılama altyapısı, otomatik araştırma ve düzeltme altyapısı ve uç nokta önleme altyapısıdır (Microsoft Defender Virüsten Koruma).

## <a name="cloud-detection-engine"></a>Bulut algılama altyapısı

Uç Nokta için Defender'ın bulut algılama altyapısı, toplanan verileri düzenli olarak tarar ve ayarladığınız göstergelerle eşleşmeye çalışır. Eşleşme olduğunda IoC için belirttiğiniz ayarlara göre işlem yapılır.

## <a name="endpoint-prevention-engine"></a>Uç nokta önleme altyapısı

Aynı gösterge listesi önleme aracısı tarafından kabul edilir. Başka bir deyişle, yapılandırılan birincil AV Microsoft Defender AV ise, eşleşen göstergeler ayarlara göre değerlendirilir. Örneğin, eylem "Uyarı ve Engelle" ise, Microsoft Defender AV dosya yürütmelerini engeller (engelleme ve düzeltme) ve buna karşılık gelen bir uyarı tetiklenir. Öte yandan, Eylem "İzin Ver" olarak ayarlanırsa, Microsoft Defender AV dosyanın çalıştırılmasını algılamaz veya engellemez.

## <a name="automated-investigation-and-remediation-engine"></a>Otomatik araştırma ve düzeltme altyapısı

Otomatik araştırma ve düzeltme aynı şekilde davranır. Bir gösterge "İzin Ver" olarak ayarlanırsa, Otomatik araştırma ve düzeltme bunun için "hatalı" bir kararı yoksayar. "Engelle" olarak ayarlanırsa, otomatik araştırma ve düzeltme bunu "hatalı" olarak ele alır.

EnableFileHashComputation ayarı, dosya taramaları sırasında sertifika ve dosya IoC için dosya karmasını hesaplar. Karmaların ve sertifikaların güvenilen uygulamalara ait olduğu IoC zorlamasını destekler. Dosyaya izin ver veya engelle ayarıyla eşzamanlı olarak etkinleştirilir ve devre dışı bırakılır. EnableFileHashComputation grup ilkesi aracılığıyla el ile etkinleştirilir ve varsayılan olarak devre dışı bırakılır.

Yeni bir gösterge (IoC) oluştururken aşağıdaki eylemlerden biri veya daha fazlası kullanılabilir:

- İzin ver – IoC'nin cihazlarınızda çalışmasına izin verilir.
- Denetim– IoC çalıştırıldığında bir uyarı tetiklenir.
- Uyar – IoC kullanıcının atlayabileceğinizi belirten bir uyarı ister 
- Yürütmeyi engelle - IoC'nin çalışmasına izin verilmez.
- Engelle ve düzelt - IoC'nin çalışmasına izin verilmez ve IoC'ye bir düzeltme eylemi uygulanır.

>[!NOTE]
> Uyarı modunu kullanmak, kullanıcılarınıza riskli bir uygulama açmaları durumunda bir uyarı sorar. İstem, uygulamayı kullanmalarını engellemez, ancak özel bir ileti ve uygulamanın uygun kullanımını açıklayan bir şirket sayfasına bağlantılar sağlayabilirsiniz. Kullanıcılar yine de uyarıyı atlayabilir ve gerekirse uygulamayı kullanmaya devam edebilir. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender tarafından bulunan uygulamaları yönetme](/cloud-app-security/mde-govern).

Şunun için bir gösterge oluşturabilirsiniz:

- [Dosyaları](indicator-file.md)
- [IP adresleri, URL'ler/etki alanları](indicator-ip-domain.md)
- [Sertifika](indicator-certificates.md)

Aşağıdaki tabloda, gösterge türü (IoC) başına tam olarak hangi eylemlerin kullanılabilir olduğu gösterilmektedir:

| IoC türü | Kullanılabilir eylemler |
|:---|:---|
| [Dosyaları](indicator-file.md) | İzin ver <br> Denetim <br> Engelleme ve düzeltme |
| [IP adresleri](indicator-ip-domain.md) | İzin ver <br> Denetim <br> Yürütmeyi engelle <br> Uyarmak |
| [URL'ler ve etki alanları](indicator-ip-domain.md) | İzin ver <br> Denetim <br> Yürütmeyi engelle<br> Uyarmak |
| [Sertifika](indicator-certificates.md) | İzin ver <br> Engelleme ve düzeltme |

Önceden var olan ICS'lerin işlevselliği değişmez. Ancak göstergeler, desteklenen geçerli yanıt eylemleriyle eşleşecek şekilde yeniden adlandırıldı:

- "Yalnızca uyarı" yanıt eylemi, uyarı oluştur ayarı etkinken "denetim" olarak yeniden adlandırıldı.
- "Uyarı ve engelleme" yanıtı, isteğe bağlı uyarı oluşturma ayarıyla "engelle ve düzelt" olarak yeniden adlandırıldı.

IoC API şeması ve tehdit kimlikleri önceden tehdit avcılığı, IoC yanıt eylemlerinin yeniden adlandırılmasıyla uyumlu olacak şekilde güncelleştirildi. API düzeni değişiklikleri tüm IoC Türleri için geçerlidir.

> [!Note]
> Kiracı başına 15.000 gösterge sınırı vardır. Dosya ve sertifika göstergeleri[, Microsoft Defender Virüsten Koruma için tanımlanan dışlamaları](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus) engellemez. Göstergeler pasif moddayken Microsoft Defender Virüsten Koruma desteklenmez.
>
> Yeni göstergeleri (ICS) içeri aktarma biçimi, yeni güncelleştirilmiş eylemler ve uyarı ayarlarına göre değişti. İçeri aktarma panelinin en altında bulunan yeni CSV biçimini indirmenizi öneririz.

## <a name="related-topics"></a>İlgili konular

- [Bağlamsal IoC oluşturma](respond-file-alerts.md#add-indicator-to-block-or-allow-a-file)
- [Uç Nokta için Microsoft Defender göstergeleri API'sini kullanma](ti-indicator.md)
- [İş ortağıyla tümleşik çözümleri kullanma](partner-applications.md)
