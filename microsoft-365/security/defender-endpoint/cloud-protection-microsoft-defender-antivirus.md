---
title: Bulut koruması ve Microsoft Defender Virüsten Koruma
description: Bulut koruması ve güvenlik hakkında bilgi Microsoft Defender Virüsten Koruma
keywords: Microsoft Defender Virüsten Koruma, yeni nesil teknolojiler, yeni nesil av, makine öğrenimi, kötü amaçlı yazılımdan koruma, güvenlik, defender, bulut, bulut koruması
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.date: 10/18/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: 013b189dca95fc63dc8d189d020fcf3f7727cf82
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "62997023"
---
# <a name="cloud-protection-and-microsoft-defender-antivirus"></a>Bulut koruması ve Microsoft Defender Virüsten Koruma

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

Yeni nesil teknolojiler, Microsoft Defender Virüsten Koruma ortaya çıkan tehditlere karşı yakın hızlı, otomatik koruma sağlar. Yeni tehditleri dinamik olarak belirlemek için, yeni nesil teknolojiler Microsoft Akıllı Güvenlik Graph ve gelişmiş makine öğrenme modelleri tarafından yönlendirilen güçlü yapay zeka (AI) sistemlerinde birbirine bağlı büyük veri kümeleriyle çalışır. Bulut koruması doğru, Microsoft Defender Virüsten Koruma ve akıllı koruma sağlamak için bulut korumasıyla birlikte çalışır. 

[:::image type="content" source="images/mde-cloud-protection.png" alt-text="Bulut korumasının diğer çalışanlarla birlikte nasıl çalıştığını gösteren Microsoft Defender Virüsten Koruma":::](enable-cloud-protection-microsoft-defender-antivirus.md)

> [!TIP]
> Bulut korumasının açık tutmasını öneririz. Daha fazla bilgi edinmek için bkz[. Bu bağlantıda bulut korumasının neden Microsoft Defender Virüsten Koruma](why-cloud-protection-should-be-on-mdav.md). 

## <a name="how-cloud-protection-works"></a>Bulut koruması nasıl çalışır?

Microsoft Defender Virüsten Koruma, Microsoft bulut hizmetleriyle sorunsuz çalışır. Microsoft Gelişmiş Koruma Hizmeti (HARITALAR) olarak da adlandırılan bu bulut koruma hizmetleri, standart gerçek zamanlı korumayı geliştirin. Bulut korumasıyla, yeni nesil teknolojiler yeni tehditlere hızla karşı koruma sağlar ve bazen tek bir uç nokta virüs bulaşmadan önce bile olabilir. 

Aşağıdaki blog gönderileri bulut korumanın nasıl çalıştığını göstermektedir:

- [Yeni nesil uç nokta koruması için Microsoft Defender'ın temel noktası olan gelişmiş teknolojileri ile ilgili bilgi](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)

- [Microsoft Defender Virüsten Koruma kurumsalda en çok dağıtılan uygulama nedendir?](https://www.microsoft.com/security/blog/2018/03/22/why-windows-defender-antivirus-is-the-most-deployed-in-the-enterprise) 

- [Makine öğrenmesi ile birlikte davranış izlemesi büyük bir para madenciliği kampanyasında bilgi bozıyor](https://www.microsoft.com/security/blog/2018/03/07/behavior-monitoring-combined-with-machine-learning-spoils-a-massive-dofoil-coin-mining-campaign)

- [Yapay zeka "Emotet" salgınını nasıl durdurdu](https://www.microsoft.com/security/blog/2018/02/14/how-artificial-intelligence-stopped-an-emotet-outbreak)

- [Kötü bir ekiplerin içini Microsoft Defender Virüsten Koruma ve katmanlı makine eğitimi savunmaları](https://www.microsoft.com/security/blog/2017/12/11/detonating-a-bad-rabbit-windows-defender-antivirus-and-layered-machine-learning-defenses)

- [Microsoft Defender Virüsten Koruma koruma hizmeti: Önceden olmayan kötü amaçlı yazılımlara karşı gelişmiş gerçek zamanlı savunma](https://www.microsoft.com/security/blog/2017/07/18/windows-defender-antivirus-cloud-protection-service-advanced-real-time-defense-against-never-before-seen-malware) 


> [!NOTE]
> En Microsoft Defender Virüsten Koruma hizmeti, ağınıza ve uç noktalarınıza güncelleştirilmiş koruma teslim etmek için bir mekanizmadır. Bulut hizmeti olarak, yalnızca bulutta depolanan dosyaların korunması değildir; bunun yerine bulut hizmeti, geleneksel güvenlik zekası güncelleştirmelerinden çok daha hızlı olan bir oranda uç noktalarınıza koruma sunmak için dağıtılmış kaynakları ve makine öğrenimini kullanır.

## <a name="how-to-get-cloud-protection"></a>Bulut koruması nasıl edinilen 

Bulut koruması varsayılan olarak etkindir. Öte yandan, önceki kuruluş ilkelerinin bir parçası olarak devre dışı bırakıldı ise yeniden etkinleştirmeniz gerekir. Daha fazla bilgi edinmek için bkz [. Bulut korumasını açma](enable-cloud-protection-microsoft-defender-antivirus.md).

Aboneliğiniz E5'Windows 10 varsa, ortaya çıkan tehditlere karşı neredeyse gerçek zamanlı koruma sağlayan acil durum dinamik zeka güncelleştirmelerinden faydalanabilirsiniz. Bulut korumasını açıkken kötü amaçlı yazılım sorunlarının düzeltmeleri bir sonraki güncelleştirmeyi beklemek yerine dakikalar içinde bulut üzerinden teslim edilir. Bulut [hizmetimizi Microsoft Defender Virüsten Koruma temel alan yeni koruma güncelleştirmelerini otomatik olarak alacak şekilde yapılandırma.](manage-event-based-updates-microsoft-defender-antivirus.md#cloud-report-updates)

## <a name="next-steps"></a>Sonraki adımlar

Artık 2013'te bulut korumasına genel Microsoft Defender Virüsten Koruma, işte sonraki adımlar:

1. Daha [fazla bilgi için bkz. Bulut korumasının neden Microsoft Defender Virüsten Koruma](why-cloud-protection-should-be-on-mdav.md).

2. Bulut korumasını [etkinleştir'e devam edin](enable-cloud-protection-microsoft-defender-antivirus.md)