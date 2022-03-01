---
title: Saldırı yüzeyini azaltma (ASR) kuralları dağıtımı
description: Saldırı yüzeyini azaltma kuralları dağıtımınızı faaliyete geçirmek için kılavuz sağlar.
keywords: Saldırı yüzeyini azaltma kuralları dağıtımı, ASR dağıtımı, asr kurallarını etkinleştirme, ASR'yi yapılandırma, izinsiz giriş engelleme sistemi, koruma kuralları, istismardan koruma kuralları, istismardan koruma kuralları, bulaşma önleme kuralları, Uç nokta için Microsoft Defender, ASR kurallarını yapılandırma
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection: m365solution-scenario
ms.date: 1/18/2022
ms.openlocfilehash: 3229cd0a98714819009e7d50baab0872f3a67c43
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011961"
---
# <a name="step-4-operationalize-asr-rules"></a>4. Adım: ASR kurallarını işlem durumaleştirme

Saldırı yüzeyini azaltma (ASR) kurallarının tam olarak dağıtıldıktan sonra ASR ile ilgili etkinlikleri izlemek ve yanıtlamak için ilgili süreçlerinizi işlemenizi çok önemlidir.

## <a name="managing-false-positives"></a>Hatalı pozitif sonuç yönetimi

Her tehdit koruması çözümünde hatalı pozitif/negatif sonuçlar oluşabilir. Yanlış pozitif sonuçlar, bir varlık (dosya veya işlem gibi) algılandığında ve kötü amaçlı olarak tanımlandığında (varlık aslında bir tehdit değilse de) durumlardır. Buna karşılık, hatalı negatif bir varlık, tehdit olarak algılanmadı ancak kötü amaçlı bir varlıktır. Hatalı pozitif ve yanlış negatif sonuçlar hakkında daha fazla bilgi için bkz: Uç Nokta için [Microsoft Defender'da hatalı pozitif/negatifleri adresle](defender-endpoint-false-positives-negatives.md)

## <a name="keeping-up-with-reports"></a>Raporları takip edin

Raporların tutarlı, düzenli bir şekilde gözden geçirmesi, ASR kurallarının dağıtımını korumanın ve yeni ortaya çıkan tehditlere karşı temlik sağlamanın vazgeçilmez bir yönüdür. Kuruluş, ASR kurallarıyla ilgili bildirilen olaylarla güncel bir tempoda, ASR kuralları olaylarının zamanlanmış incelemelerini almalı. İncelemeler, kurum büyüklüğüne bağlı olarak günlük, saatlik veya sürekli izleme olabilir.

## <a name="hunting"></a>Avlama

Gelişmiş avlama özelliği[, Microsoft 365 Defender özelliklerinden](https://security.microsoft.com) biridir. Gelişmiş av hakkında bilgi sahibi değilsanız, bkz. Gelişmiş [avla tehditlere karşı önceden arama.](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender gelişmiş av](images/asr-defender365-advanced-hunting2.png)

Gelişmiş av, Microsoft Defender ATP Uç Nokta Algılama ve Yanıt (EDR) tarafından tüm makinelerden toplanacak yakalan (ham) verilerin 30 günü içinde keşfetmenize olanak sağlayan sorgu tabanlı bir (Kusto Sorgu Dili) tehdit arama aracıdır. Gelişmiş arama yoluyla, ilginç göstergeleri ve varlıkları bulmak için etkinlikleri önceden inceebilirsiniz. Verilere esnek erişim, hem bilinen hem de potansiyel tehditlere karşı kısıtlanmamış arama kolaylaştırır.

Gelişmiş arama yoluyla, ASR kuralları bilgilerini ayıklamak, rapor oluşturmak ve verilen bir ASR kuralı denetimi bağlamında ayrıntılı bilgi almak veya etkinliği engellemek mümkündür.

 Bu portalda, cihaz olaylarının gelişmiş av bölümündeki DeviceEvents tablosundan ASR kuralları olaylarını Microsoft 365 Defender edebilirsiniz. Örneğin, aşağıdaki sorgu gibi basit bir sorgu, son 30 gün boyunca veri kaynağı olarak ASR kurallarına sahip tüm olayları bildirabilir ve bunları ActionType sayısına göre özetler; bu durumda bu, ASR kuralının gerçek kodadı olur.

Ilerleyen av portalında gösterilen ASR etkinlikleri, saatte bir görülen benzersiz işlemlerle kısıtlandı. ASR olay zamanı, etkinliğin o saat içinde ilk kez görülme zamanıdır.

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender arama sorgusu komut satırı](images/asr-defender365-advanced-hunting3.png)

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender gelişmiş arama sorgusu sonuçları](images/asr-defender365-advanced-hunting4.png)

Yukarıdakilerde, AsrLsassCredentialTheft için 187 olay kaydedilmiştir:

- 102 For Blocked
- Denetlenenler için 85
- AsrOffice Için 2 olayYayıldız (Denetlenen için 1 ve Engelleme için 1)
- AsrPsexecWmiProcessAudited için 8 olay

AsrOfficeProcess kuralına odaklanmak ve söz konusu gerçek dosyalar ve işlemlerle ilgili ayrıntıları almak için, ActionType filtresini değiştirin ve özetleme çizgisini istediğiniz alanların projeksiyonu ile değiştirin (bu durumda, bunlar DeviceName, FileName, FolderPath, vb.).

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender gelişmiş av sorgusu odaklandı](images/asr-defender365-advanced-hunting4b.png)

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender arama sorgusu odaklanan sonuçlar](images/asr-defender365-advanced-hunting5b.png)

Gelişmiş aramanın asıl avantajı, sorguları zevke uygun şekilde şekillendirebilirsiniz. Sorguyu şekillendirerek, tek bir makineye bir şey sabitlemek ya da ortamın tamamına ilişkin öngörüler ayıklamak istediğinizden bağımsız olarak, neler olduğunu tam olarak görebilirsiniz.

Arama seçenekleri hakkında daha fazla bilgi için bkz: Saldırı yüzeyini azaltma kurallarının [yeniden ortaya çıkarımı - Bölüm 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968).

## <a name="topics-in-this-deployment-collection"></a>Bu dağıtım koleksiyonunda konular

[ASR kuralları dağıtım önkoşulları](attack-surface-reduction-rules-deployment.md)

[1. Adım: ASR kuralları dağıtımını planlama](attack-surface-reduction-rules-deployment-plan.md)

[2. Adım: ASR kurallarını test edin](attack-surface-reduction-rules-deployment-test.md)

[3. Adım: ASR kurallarını uygulama](attack-surface-reduction-rules-deployment-implement.md)
