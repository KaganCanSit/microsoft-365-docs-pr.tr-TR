---
title: Verilerin tanılama verilerini Microsoft Defender Virüsten Koruma
description: Sorunları gidermek üzere veri toplamak için bir araç Microsoft Defender Virüsten Koruma
keywords: sorun giderme, hata, düzeltme, uyumluluğu güncelleştirme, işletim sistemi, monitör, rapor, Microsoft Defender av, grup ilkesi nesnesi, ayar, tanılama verileri
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 06/29/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 73f07a7346edbaebe7e53cd4e17e29a5e6764073
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "62997000"
---
# <a name="collect-microsoft-defender-antivirus-diagnostic-data"></a>Tanılama Microsoft Defender Virüsten Koruma toplama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bu makalede, Microsoft destek ve mühendislik ekipleri tarafından kullanılmaktadır. Verileri kullanırken karşılaşabilirsiniz sorunları gidermek için kullanılmaktadır. Bu tanılama verilerini Microsoft Defender Virüsten Koruma.

> [!NOTE]
> Araştırma veya yanıt işleminin bir parçası olarak, bir cihazdan araştırma paketi toplayabilirsiniz. Şöyle: Araştırma paketini [cihazlardan toplayın](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#collect-investigation-package-from-devices).

Aynı sorunu yaşayan en az iki cihaz için aşağıdaki adımları .cab şu tanılama dosyasını alın:

1. Komut isteminin yönetici düzeyindeki bir sürümünü aşağıdaki gibi açın:

    a. Başlat **menüsünü** açın.

    b. **cmd yazın**. Komut İstemi'ne **sağ tıklayın ve** yönetici olarak **çalıştır'ı seçin**.

    c. Yönetici kimlik bilgilerini belirtin veya bilgi istemini onaylar.

2. Erişim için dizine Microsoft Defender Virüsten Koruma. Varsayılan olarak bu seçenektir `C:\Program Files\Windows Defender`.

   > [!NOTE]
   > Güncelleştirilmiş bir [Microsoft Defender kötü amaçlı yazılımdan koruma platform](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform) sürümünü çalıştırıyorsanız, lütfen şu `MpCmdRun` konumdan çalıştırın: `C:\ProgramData\Microsoft\Windows Defender\Platform\<version>`.

3. Aşağıdaki komutu yazın ve Enter tuşuna **basın**

    ```Dos
    mpcmdrun.exe -GetFiles
    ```

4. Çeşitli .cab günlükler içeren bir dosya oluşturulur. Dosyanın konumu, komut isteminde çıktıda belirtilir. Varsayılan olarak konum: `C:\ProgramData\Microsoft\Microsoft Defender\Support\MpSupportFiles.cab`.

   > [!NOTE]
   > Cab dosyasını farklı bir yola veya UNC paylaşımına yönlendirmek için aşağıdaki komutu kullanın:
   >
   > `mpcmdrun.exe -GetFiles -SupportLogLocation <path>`
   >
   > Daha fazla bilgi için bkz [. Tanılama verilerini bir UNC paylaşımına yeniden yönlendirme](#redirect-diagnostic-data-to-a-unc-share).

5. Bu .cab dosyalarını Microsoft desteği tarafından erişilebilen bir konuma kopyalayın. Örneğin, bizimle paylaşabilirsiniz OneDrive parola korumalı bir klasör olabilir.

> [!NOTE]
> Uyumluluğu güncelleştir ile ilgili bir sorun varsa, Güncelleştirme Uyumluluğu desteği e-posta <a href="mailto:ucsupport@microsoft.com?subject=WDAV assessment issue&body=I%20am%20encountering%20the%20following%20issue%20when%20using%20Windows%20Defender%20AV%20in%20Update%20Compliance%3a%20%0d%0aI%20have%20provided%20at%20least%202%20support%20.cab%20files%20at%20the%20following%20location%3a%20%3Caccessible%20share%2c%20including%20access%20details%20such%20as%20password%3E%0d%0aMy%20OMS%20workspace%20ID%20is%3a%20%0d%0aPlease%20contact%20me%20at%3a"></a>şablonunu kullanarak bir e-posta gönderin ve şablonu aşağıdaki bilgilerle doldurun:
>
> Güncelleştirme Uyumluluğu'Microsoft Defender Virüsten Koruma kullanırken aşağıdaki sorunla karşılaşıyorum:
>
> Şu konumda en az 2 .cab destek sağladım:
>
> \<accessible share, including access details such as password\>
>
> OMS çalışma alanı kimliğim:
>
> Lütfen şu bağlantıdan benimle iletişime geçin:

## <a name="redirect-diagnostic-data-to-a-unc-share"></a>Tanılama verilerini bir UNC paylaşımına yönlendirme

Tanılama verilerini merkezi bir depoda toplamak için SupportLogLocation parametresini belirtebilirsiniz.

```Dos
mpcmdrun.exe -GetFiles -SupportLogLocation <path>
```

Tanılama verilerini belirtilen yola kopyalar. Yol belirtilmezse, tanılama verileri Destek Günlüğü Konumu Yapılandırmasında belirtilen konuma kopyalanır.

SupportLogLocation parametresi kullanıldığında, hedef yolda aşağıdaki gibi bir klasör yapısı oluşturulur:

```Dos
<path>\<MMDD>\MpSupport-<hostname>-<HHMM>.cab
```

<br>

****

|alan|Açıklama|
|---|---|
|yol|Komut satırda belirtilen veya yapılandırmadan alınan yol|
|MMDD|Tanılama verilerin topladığı ay ve gün (örneğin, 0530)|
|ana bilgisayar adı|Tanılama verilerini topladığı cihazın ana bilgisayar adı|
|SSMM|Tanılama verileri toplanıyorsa saat ve dakika (örneğin, 1422)|
|

> [!NOTE]
> Dosya paylaşımı kullanırken lütfen tanılama paketini toplamak için kullanılan hesabın paylaşıma yazma erişimi olduğundan emin olun.

## <a name="specify-location-where-diagnostic-data-is-created"></a>Tanılama verilerin oluşturulacak yeri belirtme

Ayrıca, Grup İlkesi Nesnesi (GPO) .cab tanılama dosyasının oluşturulacak yeri de belirtebilirsiniz.

1. Yerel Grup İlkesi Düzenleyicisi'ni açın ve SupportLogLocation GPO'nun bulun: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\SupportLogLocation`.

2. Destek **günlük dosyalarını kopyalamak için Dizin yolunu tanımla'ya seçin**.

   ![Yerel grup ilkesi düzenleyicisinin ekran görüntüsü](images/GPO1-SupportLogLocationDefender.png)

   ![Günlük dosyaları için tanımla yolunun ekran görüntüsü ayarı](images/GPO2-SupportLogLocationGPPage.png)

    ![Yerel grup ilkesi düzenleyicisinin ekran görüntüsü.](images/GPO1-SupportLogLocationDefender.png)  
        
     ![Günlük dosyaları için tanımla yolunun ekran görüntüsü ayarı.](images/GPO2-SupportLogLocationGPPage.png)  
3. İlke düzenleyicisinin içinde Etkin'i **seçin**.

4. Seçenekler alanında destek günlük dosyalarını kopyalamak istediğiniz **dizin yolunu belirtin** .
     ![Etkin dizin yolu özel ayarının ekran görüntüsü.](images/GPO3-SupportLogLocationGPPageEnabledExample.png) 
5. **Tamam'ı veya** **Uygula'ya tıklayın**.

## <a name="see-also"></a>Ayrıca bkz.

- [Raporlama Microsoft Defender Virüsten Koruma giderme](troubleshoot-reporting.md)
