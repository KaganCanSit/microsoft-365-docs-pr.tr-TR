---
title: Güncelleştirme Uyumluluğu ve Uyumluluğu için tanılama verilerini Microsoft Defender Virüsten Koruma
description: Değerlendirme Eklentisini kullanırken Güncelleştirme Uyumluluğu sorunlarını gidermek üzere veri Microsoft Defender Virüsten Koruma kullanın.
keywords: sorun giderme, hata, düzeltme, uyumluluğu güncelleştirme, işletim sistemi, monitör, rapor, Microsoft Defender AV
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 9e368f2cb3cecf9359c4aed5e727aef2ee21c02b
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "62997021"
---
# <a name="collect-update-compliance-diagnostic-data-for-microsoft-defender-antivirus-assessment"></a>Değerlendirme değerlendirme için güncelleştirme uyumluluğu tanılama Microsoft Defender Virüsten Koruma toplama


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bu makalede, Microsoft destek ve mühendislik ekipleri tarafından, Güncelleştirme Uyumluluğu eklentisinde Yer Alan Değerlendirme bölümünü kullanırken karşılaşabilirsiniz sorunları gidermek için Microsoft Defender Virüsten Koruma kullanılmaktadır.

Bu işlemi denemeden önce, Raporlama sorunlarını giderme, [önkoşulların](troubleshoot-reporting.md) Microsoft Defender Virüsten Koruma karşılanması ve önerilen diğer sorun giderme adımlarını okuduğu salt okunur.

Raporlama veya Güncelleştirme Uyumluluğu'nda göstermeyen en az iki cihaz için aşağıdaki .cab bu tanılama dosyasını alın:

1. Komut isteminin yönetici düzeyindeki bir sürümünü aşağıdaki gibi açın:

    a. Başlat **menüsünü** açın.

    b. **cmd yazın**. Komut İstemi'ne **sağ tıklayın ve** yönetici olarak **çalıştır'ı seçin**.

    c. Yönetici kimlik bilgilerini belirtin veya bilgi istemini onaylar.

2. Windows Defender gidin. Varsayılan olarak bu seçenektir `C:\Program Files\Windows Defender`.

3. Aşağıdaki komutu yazın ve Enter tuşuna **basın**

    ```Dos
    mpcmdrun -getfiles
    ```

4. Çeşitli .cab günlükler içeren bir dosya oluşturulur. Dosyanın konumu, komut isteminde çıktıda belirtilir. Varsayılan olarak konum: `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`.

5. Bu .cab dosyalarını Microsoft desteği tarafından erişilebilen bir konuma kopyalayın. Örneğin, bizimle paylaşabilirsiniz OneDrive parola korumalı bir klasör olabilir.

6. Güncelleştirme uyumluluğu desteği <a href="mailto:ucsupport@microsoft.com?subject=MDAV assessment issue&body=I%20am%20encountering%20the%20following%20issue%20when%20using%20Windows%20Defender%20AV%20in%20Update%20Compliance%3a%20%0d%0aI%20have%20provided%20at%20least%202%20support%20.cab%20files%20at%20the%20following%20location%3a%20%3Caccessible%20share%2c%20including%20access%20details%20such%20as%20password%3E%0d%0aMy%20OMS%20workspace%20ID%20is%3a%20%0d%0aPlease%20contact%20me%20at%3a">e-posta şablonunu kullanarak bir e-posta</a> gönderin ve şablonu aşağıdaki bilgilerle doldurun:

    ```text
    I am encountering the following issue when using Microsoft Defender Antivirus in Update Compliance:

    I have provided at least 2 support .cab files at the following location: <accessible share, including access details such as password>

    My OMS workspace ID is:

    Please contact me at:
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Raporlama Microsoft Defender Virüsten Koruma giderme](troubleshoot-reporting.md)
