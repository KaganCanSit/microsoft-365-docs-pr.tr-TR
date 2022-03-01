---
title: Gösterge oluşturma
ms.reviewer: ''
description: Varlıkları algılama, önleme ve dışlamaları tanımlayan dosya karması, IP adresi, URL'ler veya etki alanları için göstergeler oluşturun.
keywords: yönetme, izin verilen, engellendi, engelle, temiz, kötü amaçlı, dosya karma, ip adresi, url'ler, etki alanı
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
ms.openlocfilehash: c241438e2cd9a0a5bd9bb018d671340c22ef7d0d
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998024"
---
# <a name="create-indicators"></a>Gösterge oluşturma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
>
> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Güvenlik (IOC) eşleştirmesi göstergesi, her uç nokta koruma çözümünde temel öneme sahip bir özelliktir. Bu özellik SecOps'a algılama ve engelleme (önleme ve yanıt) için bir gösterge listesi ayarlama olanağı verir.

Varlıkları algılama, önleme ve dışlamaları tanımlayan göstergeler oluşturun. Hem alınacak eylemi hem de eylemin ne zaman uygulanacak sürelerini hem de uygulama için cihaz grubunun kapsamını tanımlayabilirsiniz.

Şu anda desteklenen kaynaklar Uç Nokta için Defender'ın bulut algılama altyapısı, otomatik araştırma ve düzeltme altyapısı ve uç nokta önleme altyapısı (Microsoft Defender Virüsten Koruma).

## <a name="cloud-detection-engine"></a>Bulut algılama altyapısı

Uç nokta için Defender'ın bulut algılama altyapısı toplanan verileri düzenli olarak tarar ve ayarladığı göstergelere uygun olarak çalışır. Eşleşme olduğunda, eylem IoC için belirttiğiniz ayarlara göre  alınır.

## <a name="endpoint-prevention-engine"></a>Uç nokta önleme alt yapısı

Aynı gösterge listesi önleme aracısı tarafından da onurlandırıldı. Başka bir ifadeyle, Microsoft Defender AV birincil AV yapılandırılmışsa, uyumlu göstergelerin ayarlara göre işlem gördüğü anlamına gelir. Örneğin, eylem "Uyarı ve Engelle" ise, Microsoft Defender AV dosya yürütmelerini (engelleme ve düzeltme) engelleyecek ve buna karşılık gelen bir uyarı yükseltecek. Öte yandan, Eylem "İzin Ver" olarak ayarlanırsa, Microsoft Defender AV dosyanın çalıştırılanı algılamaz veya engellemez.

## <a name="automated-investigation-and-remediation-engine"></a>Otomatik araştırma ve düzeltme altyapısı

Otomatik araştırma ve düzeltme aynı şekilde davranır. Bir gösterge "İzin Ver" olarak ayarlanırsa, Otomatik araştırma ve düzeltme bu gösterge için "kötü" kararını yoksayar. "Engelle" olarak ayarlanırsa, Otomatik araştırma ve düzeltme bunu "kötü" olarak ayarlayın.

EnableFileHashComputation ayarı, dosya taramaları sırasında sertifika ve dosya IoC için dosya karmasını hesaplama. Karmalar ve sertifikalar güvenilir uygulamalara ait IoC zorlamasını destekler. Dosya izin ver veya engelle ayarıyla eş zamanlı olarak etkinleştirilir ve devre dışı bırakılır. EnableFileHashComputation, Grup İlkesi aracılığıyla el ile etkinleştirilir ve varsayılan olarak devre dışı bırakılır.

Yeni bir gösterge (IoC) oluştururken, aşağıdaki eylemlerden biri veya birkaçı kullanılabilir:

- İzin Ver – IoC'nin cihazlarınız üzerinde çalışmasına izin verilir.
- Denetim – IoC çalıştırlendiğinde bir uyarı tetiklenir.
- Uyar – IoC kullanıcının atlay bir uyarıyla uyar (Yalnızca Bulut Uygulamaları için Defender)
- Yürütmeyi engelle - IoC'nin çalışmasına izin verilmez.
- Engelle ve düzelt - IoC'nin çalışmasına izin verilmez ve IoC'ye bir düzeltme eylemi uygulanır.

>[!NOTE]
> Uyarı modunu kullanmak, kullanıcılarınıza riskli bir uygulama açtıklarını bir uyarıyla gösterir. Komut isteminin uygulamayı kullanmalarını engellemez, ancak özel bir ileti ve uygulamanın uygun kullanımını açıklayan bir şirket sayfasına bağlantı sabilirsiniz. Kullanıcılar yine de uyarıyı atlayarak gerekirse uygulamayı kullanmaya devam eder. Daha fazla bilgi için bkz [. Uç Nokta için Microsoft Defender tarafından bulunan uygulamaları yönetme](/cloud-app-security/mde-govern).

Aşağıdakiler için bir gösterge oluşturabilirsiniz:

- [Dosyalar](indicator-file.md)
- [IP adresleri, URL'ler/etki alanları](indicator-ip-domain.md)
- [Sertifikalar](indicator-certificates.md)

Aşağıdaki tabloda, gösterge (IoC) türü başına tam olarak hangi eylemlerin kullanılabilir olduğu gösterilmiştir:

| IoC türü | Kullanılabilir eylemler |
|:---|:---|
| [Dosyalar](indicator-file.md) | İzin ver <br> Denetim <br> Engelleme ve düzeltme |
| [IP adresleri](indicator-ip-domain.md) | İzin ver <br> Denetim <br> Yürütmeyi engelle |
| [URL'ler ve etki alanları](indicator-ip-domain.md) | İzin ver <br> Denetim <br> Yürütmeyi engelle |
| [Sertifikalar](indicator-certificates.md) | İzin ver <br> Engelleme ve düzeltme |

Önceden var olan IoC'lerin işlevselliği değişmez. Bununla birlikte, göstergeler desteklenen geçerli yanıt eylemleriyle eş olacak şekilde yeniden adlandırılmıştır:

- "Yalnızca uyarı" yanıt eylemi, uyarı oluşturma ayarı etkinleştirildiğinde "denetim" olarak yeniden adlandırılmıştır.
- "Uyarı ve engelleme" yanıtı, isteğe bağlı olarak oluşturulan uyarı ayarıyla "engelle ve düzeltmek" olarak yeniden adlandırılmış.

IoC API şeması ve önceden avın tehdit kimlikleri, IoC yanıt eylemlerinin yeniden adlanmasıyla uyumlu olacak şekilde güncelleştirildi. API düzeni değişiklikleri tüm IoC Türleri için geçerlidir.

> [!Note]
> Kiracı başına 15.000 gösterge sınırı vardır. Dosya ve sertifika göstergeleri, çalışma sayfalarında tanımlanan [dışlamaları Microsoft Defender Virüsten Koruma](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus). Pasif modundayken Microsoft Defender Virüsten Koruma, çalışma sayfalarında desteklanmaz.
>
> Yeni göstergeleri (IOC) içeri aktarma biçimi, yeni güncelleştirilmiş eylemler ve uyarı ayarlarına göre değiştirilmiştir. İçeri aktarma panelinin en altında bulunan yeni CSV biçimini indirmenizi öneririz.

## <a name="related-topics"></a>İlgili konular

- [Bağlamsal IoC oluşturma](respond-file-alerts.md#add-indicator-to-block-or-allow-a-file)
- [Uç nokta göstergeleri API'si için Microsoft Defender'ı kullanma](ti-indicator.md)
- [İş ortağı tümleşik çözümlerini kullanma](partner-applications.md)
