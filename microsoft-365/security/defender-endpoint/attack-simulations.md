---
title: Sanal saldırılar aracılığıyla Uç Nokta için Microsoft Defender'ı deneyimle
description: Sağlanan saldırı senaryosu benzetimlerini çalıştırarak, Uç Nokta için Microsoft Defender'ın ihlalleri algılay nasıl algılayasını, araştırsını ve yanıt vermesini deneyimlenin.
keywords: test, senaryo, saldırı, benzetim, benzetim, sanal, kendi, Uç Nokta için Microsoft Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 11/20/2018
ms.technology: mde
ms.openlocfilehash: da02e1391b7624dc3e091ca1024a68c5756227a2
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "62997009"
---
# <a name="experience-microsoft-defender-for-endpoint-through-simulated-attacks"></a>Sanal saldırılar aracılığıyla Uç Nokta için Microsoft Defender'ı deneyimle 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-attacksimulations-abovefoldlink)

> [!TIP]
>
> - Uç nokta için Microsoft Defender'daki en son iyileştirmeler hakkında bilgi: Uç nokta için [Defender'daki yenilikleri öğrenin](https://cloudblogs.microsoft.com/microsoftsecure/2018/11/15/whats-new-in-windows-defender-atp/).
> - Uç Nokta için Defender, son MITRE değerlendirmesinde endüstri lideri optikleri ve algılama özelliklerini gösteriyor. Okuma: [Analizler CK tabanlı değerlendirmede MITRE ATT&okuma](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

Hizmete birkaçtan fazla cihaz eklemeden önce Uç Nokta için Defender'ı deneyimleyebilirsiniz. Bunu yapmak için birkaç test cihazına denetimli saldırı benzetimleri çalıştırabilirsiniz. Benzetimi yapılan saldırıyı çalıştırdikten sonra, Uç Nokta için Defender'ın kötü amaçlı etkinliği nasıl ortaya çıkarıyor olduğunu gözden geçirebilirsiniz ve verimli bir yanıta nasıl olanak olduğunu keşfedebilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

Sağlanan benzetimleri çalıştırmak için, en az bir yerleşik [cihaza ihtiyacınız vardır](onboard-configure.md).

Her saldırı senaryosuyla birlikte sağlanan adım adım belgeyi okuyun. Her belgede işletim sistemi ve uygulama gereksinimlerinin yanı sıra saldırı senaryosuna özgü ayrıntılı yönergeler de yer almaktadır.

## <a name="run-a-simulation"></a>Benzetim çalıştırma

1. Uç **Noktalar Değerlendirme** \> **& öğreticileri** \> **Öğreticiler &** benzetimleri için kullanılabilir saldırı senaryolarının hangilerini benzetim yapmak istediğiniz seçin:
   - **Senaryo 1: Belge geri dönmez- sosyal** olarak mühendislik yapılan bir belge teslimini benzetimler. Belge, saldırganlara denetim veren özel olarak hazırlanmış bir arka kapı başlatıyor.
   - **Senaryo 2:** Dosyasız saldırıdaki PowerShell betiği, PowerShell'e dayanan dosyasız bir saldırının benzetimini yaptı, saldırı yüzeyini azaltmayı ve kötü amaçlı bellek etkinliğini algıla ile ilgili cihaz öğrenmeyi gösterir.
   - **Senaryo 3: Otomatik olay** yanıtı - Olay yanıt kapasitenizi ölçeklendirmek için ihlal yapıtlarını otomatik olarak uyaran otomatik soruşturmayı tetikler.

2. Seçtiğiniz senaryoyla birlikte verilen ilgili adım adım belgeyi indirin ve okuyun.

3. Benzetim dosyasını indirin veya Benzetim betiği kopyalamak için Değerlendirme ve & **Öğreticiler'e** \> & kopyalayın. Dosyayı veya betiği test cihazına indirmeyi seçebilirsiniz, ancak bu zorunlu değildir.

4. Benzetim dosyasını veya betiği, adım adım belgede anlatımlı olarak test cihazında çalıştırın.

> [!NOTE]
> Benzetim dosyaları veya betikler saldırı etkinliğini taklit ediyor ancak aslında bu, test cihazına zarar vermeyecek veya tehlikeye atmayacak.
>
> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-attacksimulations-belowfoldlink)

## <a name="related-topics"></a>İlgili konular

- [Cihazları ekleme](onboard-configure.md)
- [Cihaz Windows ekleme](configure-endpoints.md)
