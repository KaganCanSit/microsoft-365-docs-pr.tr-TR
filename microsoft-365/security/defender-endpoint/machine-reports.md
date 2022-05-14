---
title: Uç Nokta için Microsoft Defender'da cihaz durumu ve uyumluluk raporu
description: Cihaz sistem durumu algılamalarını, virüsten koruma durumunu, işletim sistemi platformunu ve Windows 10 sürümlerini cihaz durumu ve uyumluluk raporunu kullanarak izleme
keywords: sistem durumu, virüsten koruma, işletim sistemi platformu, windows 10 sürümü, sürüm, sistem durumu, uyumluluk, durum
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
ms.openlocfilehash: 50c7a6a4563e8231d28b11144347ca0fb1de46a9
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418214"
---
# <a name="device-health-and-compliance-report-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'da cihaz durumu ve uyumluluk raporu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Virüsten Koruma 

**Platform**
- Windows
- Mac OS
- Linux
- iOS
- Android

Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Cihazlar durum raporu, kuruluşunuzdaki cihazlar hakkında üst düzey bilgiler sağlar. Rapor algılayıcı sistem durumu, virüsten koruma durumu, işletim sistemi platformları ve Windows 10 (ve Windows 11) sürümlerini gösteren popüler bilgiler içerir.

Pano iki bölümde yapılandırılmıştır:

:::image type="content" source="images/device-reports.png" alt-text="Cihaz raporu" lightbox="images/device-reports.png":::


<br>

****

|Bölüm|Açıklama|
|---|---|
|1|Cihaz eğilimleri|
|2|Cihaz özeti (geçerli gün)|
|||

## <a name="device-trends"></a>Cihaz eğilimleri

Varsayılan olarak, cihaz eğilimleri en son tam gün ile biten 30 günlük dönemdeki cihaz bilgilerini görüntüler. Kuruluşunuzda gerçekleşen eğilimlere daha iyi bir bakış açısı elde etmek için, gösterilen zaman aralığını ayarlayarak raporlama dönemine ince ayar yapabilirsiniz. Zaman aralığını ayarlamak için açılan seçeneklerden bir zaman aralığı seçin:

- 30 gün
- Üç ay
- Altı ay
- Özel

> [!NOTE]
> Bu filtreler yalnızca cihaz eğilimleri bölümüne uygulanır. Cihaz özeti bölümünü etkilemez.

## <a name="device-summary"></a>Cihaz özeti

Cihaz eğilimleri popüler cihaz bilgilerini gösterirken, cihaz özetinde cihaz bilgilerinin kapsamı geçerli güne göre belirlenmiş olarak gösterilir.

> [!NOTE]
> Özet bölümüne yansıtılan verilerin kapsamı geçerli tarihten 180 gün öncesine kadar belirlenmiştir. Örneğin bugünün tarihi 27 Mart 2019 ise, özet bölümündeki veriler 28 Eylül 2018 ile 27 Mart 2019 arasında başlayan sayıları yansıtır.
>
> Eğilimler bölümüne uygulanan filtre özet bölümüne uygulanmaz.

Cihaz eğilimleri bölümü, ilgili filtrenin uygulandığı cihazlar listesinde detaya gitmenizi sağlar. Örneğin, Algılayıcı sistem durumu kartındaki Etkin Değil çubuğuna tıklandığında, yalnızca algılayıcı durumu etkin olmayan cihazları gösteren sonuçların yer aldığı cihazlar listesi görüntülenir.

## <a name="device-attributes"></a>Cihaz öznitelikleri

Rapor, aşağıdaki cihaz özniteliklerini görüntüleyen kartlardan oluşur:

- **Sistem durumu**: Etkin, iletişim bozukluğu yaşayan, etkin olmayan veya algılayıcı verilerinin görülmediği cihazların toplu bir görünümünü sağlayarak cihazlardaki algılayıcı durumu hakkındaki bilgileri gösterir.
- **Etkin Windows 10 cihazları için virüsten koruma durumu**: Cihaz sayısını ve Microsoft Defender Virüsten Koruma durumunu gösterir.
- **İşletim sistemi platformları**: Kuruluşunuzda var olan işletim sistemi platformlarının dağıtımını gösterir.
- **Windows 10 sürümleri**: Windows 10 cihazların ve bunların kuruluşunuzdaki sürümlerinin dağıtımını gösterir.

## <a name="filter-data"></a>Verileri filtreleme

Belirli özniteliklere sahip cihazları dahil etmek veya hariç tutmak için sağlanan filtreleri kullanın.

Cihaz özniteliklerinden uygulanacak birden çok filtre seçebilirsiniz.

> [!NOTE]
> Bu filtreler rapordaki **tüm** kartlar için geçerlidir.

Örneğin, Etkin algılayıcı sistem durumu olan Windows 10 cihazlar hakkındaki verileri göstermek için:

1. **Filtreler > Algılayıcı sistem durumu > Etkin** altında.
2. Ardından **> Windows 10 işletim sistemi platformlarını** seçin.
3. **Uygula'yı** seçin.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)

## <a name="related-topic"></a>İlgili konu

- [Tehdit koruma raporu](threat-protection-reports.md)
