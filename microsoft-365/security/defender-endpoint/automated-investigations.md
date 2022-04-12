---
title: Tehditleri araştırmak ve düzeltmek için otomatik araştırma kullanma
description: Pertahanan Microsoft untuk Titik Akhir'daki otomatik araştırma akışını anlama.
keywords: otomatik, araştırma, algılama, Pertahanan Microsoft untuk Titik Akhir
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.date: 11/24/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.custom: AIR
ms.openlocfilehash: eadf9fe7f6112d1219f085662686b2a930b3ff28
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789810"
---
# <a name="overview-of-automated-investigations"></a>Otomatik araştırmalara genel bakış

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Nasıl çalıştığını görmek ister misiniz? Aşağıdaki videoyu izleyin:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bOeh]

Otomatik araştırmadaki teknoloji çeşitli inceleme algoritmalarını kullanır ve güvenlik analistleri tarafından kullanılan süreçleri temel alır. AIR özellikleri uyarıları incelemek ve ihlalleri çözmek için anında işlem yapmak üzere tasarlanmıştır. AIR özellikleri uyarı hacmini önemli ölçüde azaltarak güvenlik işlemlerinin daha gelişmiş tehditlere ve diğer yüksek değerli girişimlere odaklanmasını sağlar. Bekleyen veya tamamlanan tüm düzeltme eylemleri [İşlem merkezinde](auto-investigation-action-center.md) izlenir. İşlem merkezinde bekleyen eylemler onaylanır (veya reddedilir) ve gerekirse tamamlanmış eylemler geri alınabilir.

Bu makale AIR'e genel bir bakış sağlar ve sonraki adımlara ve ek kaynaklara bağlantılar içerir.

> [!TIP]
> Pertahanan Microsoft untuk Titik Akhir mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automated-investigations-abovefoldlink)

## <a name="how-the-automated-investigation-starts"></a>Otomatik araştırma nasıl başlar?

Otomatik araştırma, bir uyarı tetiklendiğinde veya bir güvenlik operatörü araştırmayı başlattığında başlayabilir.

<br>

****

|Durum|Neler olur?|
|---|---|
|Bir uyarı tetikleniyor|Genel olarak, bir [uyarı](review-alerts.md) tetiklendiğinde ve bir [olay](view-incidents-queue.md) oluşturulduğunda otomatik bir araştırma başlatılır. Örneğin, kötü amaçlı bir dosyanın bir cihazda yer aldığını varsayalım. Bu dosya algılandığında bir uyarı tetikler ve olay oluşturulur. Cihazda otomatik bir araştırma işlemi başlar. Diğer cihazlarda aynı dosya nedeniyle diğer uyarılar oluşturulduğundan, bunlar ilişkili olaya ve otomatik araştırmaya eklenir.|
|El ile bir araştırma başlatılır|Otomatik araştırma, güvenlik operasyonları ekibiniz tarafından el ile başlatılabilir. Örneğin, bir güvenlik operatörünün cihazların listesini gözden geçirdiğini ve bir cihazın yüksek risk düzeyine sahip olduğunu fark ettiğini varsayalım. Güvenlik operatörü listeden cihazı seçerek açılır öğesini açabilir ve ardından **Otomatik Araştırma Başlat'ı** seçebilir.|
|

## <a name="how-an-automated-investigation-expands-its-scope"></a>Otomatik araştırma kapsamını nasıl genişletir?

Bir araştırma çalışırken, cihazdan oluşturulan diğer tüm uyarılar, araştırma tamamlanana kadar devam eden bir otomatik araştırmaya eklenir. Ayrıca, aynı tehdit diğer cihazlarda görülürse, bu cihazlar araştırmaya eklenir.

Başka bir cihazda suçlu bulunan bir varlık görülürse, otomatik araştırma işlemi kapsamı bu cihazı içerecek şekilde genişletir ve bu cihazda genel bir güvenlik playbook'u başlatılır. Bu genişletme işlemi sırasında aynı varlıktan 10 veya daha fazla cihaz bulunursa, bu genişletme eylemi onay gerektirir ve **Bekleyen eylemler** sekmesinde görünür.

## <a name="how-threats-are-remediated"></a>Tehditler nasıl düzeltilir?

Uyarılar tetiklendikçe ve otomatik bir araştırma çalıştırıldığında, araştırılan her kanıt parçası için bir karar oluşturulur. Hükümler:

- *Kötü Amaçlı*;
- *Şüpheli*; Veya
- *Tehdit bulunamadı*.

Kararlara ulaşıldığında otomatik araştırmalarda bir veya daha fazla düzeltme eylemine neden olabilir. Karantinaya dosya gönderme, hizmeti durdurma, zamanlanmış görevi kaldırma ve daha birçok düzeltme eylemine örnek olarak verilebilir. Daha fazla bilgi edinmek için bkz [. Düzeltme eylemleri](manage-auto-investigation.md#remediation-actions).

Kuruluşunuz için ayarlanan [otomasyon düzeyine](automation-levels.md) ve diğer güvenlik ayarlarına bağlı olarak, düzeltme eylemleri otomatik olarak veya yalnızca güvenlik operasyonları ekibinizin onayıyla gerçekleşebilir. Otomatik düzeltmeyi etkileyebilecek ek güvenlik ayarları, [istenmeyebilecek uygulamalardan](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) (PUA) korumayı içerir.

Bekleyen veya tamamlanan tüm düzeltme eylemleri [İşlem merkezinde](auto-investigation-action-center.md) izlenir. Gerekirse, güvenlik operasyonları ekibiniz bir düzeltme eylemini geri alabilir. Daha fazla bilgi edinmek için bkz. [Otomatik araştırmanın ardından düzeltme eylemlerini gözden geçirme ve onaylama](/microsoft-365/security/defender-endpoint/manage-auto-investigation).

> [!TIP]
> Microsoft 365 Defender portalındaki yeni, birleşik araştırma sayfasına göz atın. Daha fazla bilgi edinmek için bkz. [(YENİ!) Birleşik araştırma sayfası](/microsoft-365/security/defender/m365d-autoir-results#new-unified-investigation-page).

## <a name="requirements-for-air"></a>AIR gereksinimleri

Kuruluşunuzda Uç Nokta için Defender olmalıdır (bkz. [Pertahanan Microsoft untuk Titik Akhir için en düşük gereksinimler](minimum-requirements.md)).

> [!NOTE]
> Otomatik araştırma ve yanıt, pasif modda veya etkin modda çalışmak için Microsoft Defender Virüsten Koruma gerektirir. Microsoft Defender Virüsten Koruma devre dışı bırakılırsa veya kaldırılırsa, Otomatik Araştırma ve Yanıt düzgün çalışmaz.

Şu anda AIR yalnızca aşağıdaki işletim sistemi sürümlerini destekler:

- Windows Server 2012 R2 (Önizleme)
- Windows Server 2016 (Önizleme)
- Windows Server 2019
- Windows Server 2022
- Windows 10, sürüm 1709 ([KB4493441](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441) ile İs Derlemesi 16299.1085) veya üzeri
- Windows 10, sürüm 1803 ([KB4493464](https://support.microsoft.com/help/4493464/windows-10-update-kb4493464) ile İs Derlemesi 17134.704) veya üzeri
- Windows 10, sürüm [1803](/windows/release-information/status-windows-10-1809-and-windows-server-2019) veya üzeri
- Windows 11

## <a name="next-steps"></a>Sonraki adımlar

- [Otomasyon düzeyleri hakkında daha fazla bilgi edinin](automation-levels.md)
- [Etkileşimli kılavuza bakın: Pertahanan Microsoft untuk Titik Akhir ile tehditleri araştırma ve düzeltme](https://aka.ms/MDATP-IR-Interactive-Guide)
- [Pertahanan Microsoft untuk Titik Akhir'de otomatik araştırma ve düzeltme özelliklerini yapılandırma](configure-automated-investigations-remediation.md)

## <a name="see-also"></a>Ayrıca bkz.

- [PUA koruması](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [Pertahanan Microsoft untuk Office 365'de otomatik araştırma ve yanıt](/microsoft-365/security/office-365-security/office-365-air)
- [Microsoft 365 Defender'de otomatik araştırma ve yanıt](/microsoft-365/security/defender/m365d-autoir)
