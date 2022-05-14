---
title: Bulut koruması ve Microsoft Defender Virüsten Koruma
description: Bulut koruması ve Microsoft Defender Virüsten Koruma hakkında bilgi edinin
keywords: Microsoft Defender Virüsten Koruma, yeni nesil teknolojiler, yeni nesil av, makine öğrenmesi, kötü amaçlı yazılımdan koruma, güvenlik, defender, bulut, bulut koruması
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
ms.openlocfilehash: d272a816b302ea0332422ff2324ca091e43cd7a4
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416002"
---
# <a name="cloud-protection-and-microsoft-defender-antivirus"></a>Bulut koruması ve Microsoft Defender Virüsten Koruma

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Microsoft Defender Virüsten Koruma'daki yeni nesil teknolojiler, yeni ve yeni ortaya çıkan tehditlere karşı neredeyse anında, otomatik koruma sağlar. Yeni tehditleri dinamik olarak tanımlamak için yeni nesil teknolojiler, Microsoft Akıllı Güvenlik Graph ve gelişmiş makine öğrenmesi modelleri tarafından yönetilen güçlü yapay zeka (AI) sistemlerindeki büyük bağlantılı veri kümeleriyle çalışır. Bulut koruması doğru, gerçek zamanlı ve akıllı koruma sağlamak için Microsoft Defender Virüsten Koruma ile birlikte çalışır. 

[:::image type="content" source="images/mde-cloud-protection.png" alt-text="Bulut korumasının Microsoft Defender Virüsten Koruma ile birlikte nasıl çalıştığını gösteren diyagram" lightbox="images/mde-cloud-protection.png":::](enable-cloud-protection-microsoft-defender-antivirus.md)

> [!TIP]
> Bulut korumasını açık tutmanızı öneririz. Daha fazla bilgi edinmek için bkz. [Microsoft Defender Virüsten Koruma için bulut korumasının neden etkinleştirilmesi gerekir](why-cloud-protection-should-be-on-mdav.md)? 

## <a name="how-cloud-protection-works"></a>Bulut koruması nasıl çalışır?

Microsoft Defender Virüsten Koruma, Microsoft bulut hizmetleriyle sorunsuz çalışır. Microsoft Gelişmiş Koruma Hizmeti (MAPS) olarak da adlandırılan bu bulut koruma hizmetleri, standart gerçek zamanlı korumayı geliştirir. Bulut koruması sayesinde yeni nesil teknolojiler, bazen tek bir uç noktaya virüs bulaşmadan önce bile yeni tehditlerin hızla tanımlanmasını sağlar. 

Aşağıdaki blog gönderileri, bulut korumasının nasıl çalıştığını göstermektedir:

- [Uç Nokta için Microsoft Defender yeni nesil korumanın temelindeki gelişmiş teknolojileri tanımaya başlayın](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)

- [Microsoft Defender Virüsten Koruma neden kuruluşta en çok dağıtılandır?](https://www.microsoft.com/security/blog/2018/03/22/why-windows-defender-antivirus-is-the-most-deployed-in-the-enterprise) 

- [Makine öğrenmesi ile birlikte davranış izleme, büyük bir madeni para madenciliği kampanyasını bozuyor](https://www.microsoft.com/security/blog/2018/03/07/behavior-monitoring-combined-with-machine-learning-spoils-a-massive-dofoil-coin-mining-campaign)

- [Yapay zeka bir "Emotet" salgınını nasıl durdurdu?](https://www.microsoft.com/security/blog/2018/02/14/how-artificial-intelligence-stopped-an-emotet-outbreak)

- [Kötü bir tavşanı patlatıyor: Microsoft Defender Virüsten Koruma ve katmanlı makine öğrenmesi savunmaları](https://www.microsoft.com/security/blog/2017/12/11/detonating-a-bad-rabbit-windows-defender-antivirus-and-layered-machine-learning-defenses)

- [Microsoft Defender Virüsten Koruma bulut koruma hizmeti: Daha önce görülmemiş kötü amaçlı yazılımlara karşı gelişmiş gerçek zamanlı savunma](https://www.microsoft.com/security/blog/2017/07/18/windows-defender-antivirus-cloud-protection-service-advanced-real-time-defense-against-never-before-seen-malware) 


> [!NOTE]
> Microsoft Defender Virüsten Koruma bulut hizmeti, ağınıza ve uç noktalarınıza güncelleştirilmiş koruma sunmaya yönelik bir mekanizmadır. Bir bulut hizmeti olarak, yalnızca bulutta depolanan dosyalar için koruma değildir; Bunun yerine bulut hizmeti, geleneksel güvenlik bilgileri güncelleştirmelerinden çok daha hızlı bir hızda uç noktalarınıza koruma sağlamak için dağıtılmış kaynakları ve makine öğrenmesini kullanır.

## <a name="how-to-get-cloud-protection"></a>Bulut korumasını alma 

Bulut koruması varsayılan olarak etkindir. Ancak, önceki kuruluş ilkelerinin bir parçası olarak devre dışı bırakılmışsa yeniden etkinleştirmeniz gerekebilir. Daha fazla bilgi için bkz. [Bulut korumasını açma](enable-cloud-protection-microsoft-defender-antivirus.md).

Aboneliğiniz Windows 10 E5 içeriyorsa, yeni ortaya çıkan tehditlere karşı neredeyse gerçek zamanlı koruma sağlayan acil durum dinamik zeka güncelleştirmelerinden yararlanabilirsiniz. Bulut korumasını açtığınızda, kötü amaçlı yazılım sorunlarının düzeltmeleri bir sonraki güncelleştirmeyi beklemek yerine birkaç dakika içinde bulut üzerinden teslim edilebilir. Bkz[. Bulut hizmetimizden gelen raporlara göre yeni koruma güncelleştirmelerini otomatik olarak almak için Microsoft Defender Virüsten Koruma yapılandırma](manage-event-based-updates-microsoft-defender-antivirus.md#cloud-report-updates).

## <a name="next-steps"></a>Sonraki adımlar

Microsoft Defender Virüsten Koruma'da bulut korumasına genel bir bakış elde ettiğinize göre, sonraki adımlardan bazıları şunlardır:

1. Bkz. [Microsoft Defender Virüsten Koruma için bulut korumasının neden etkinleştirilmesi gerektiği](why-cloud-protection-should-be-on-mdav.md).

2. [Bulut korumasını etkinleştirme](enable-cloud-protection-microsoft-defender-antivirus.md) işlemine geçin

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)