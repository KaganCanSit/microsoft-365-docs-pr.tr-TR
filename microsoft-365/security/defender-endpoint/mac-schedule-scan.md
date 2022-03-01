---
title: macOS'ta Uç Nokta için Microsoft Defender ile taramaları zamanlama
description: Kuruluş varlıklarını daha iyi korumak için macOS'ta Uç Nokta için Microsoft Defender için otomatik tarama zamanı zamanlamayı öğrenin.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, taramalar, virüsten koruma
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 629db5fc343d100913d631f59a680fc9160713ed
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011879"
---
# <a name="schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>macOS'ta Uç Nokta için Microsoft Defender ile taramaları zamanlama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Uç Nokta için Microsoft Defender ile tehdit taramasına başlayabilirsiniz, ancak zamanlanmış veya zamanlanmış taramalar, kuruluş tarafından faydalı olabilir. Örneğin, taramayı her iş günü veya haftanın başında çalıştıracak şekilde zaman zamanlarız. 

## <a name="schedule-a-scan-with-launchd"></a>Başlatarak tarama *zamanlama*

bir macOS cihazında *başlatan* daemon'u kullanarak bir tarama zamanlaması oluşturabilirsiniz.

Burada kullanılan *.plist dosya biçimi hakkında* daha fazla bilgi için resmi Apple geliştirici web [sitesinde Bilgi Özellik](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html) Listesi Dosyaları Hakkında'ya bakın.

### <a name="schedule-a-quick-scan"></a>Hızlı tarama zamanlama

Aşağıdaki kodda, hızlı tarama zamanlaması için ihtiyacınız olan şema gösterilmektedir. 

1. Bir metin düzenleyicisi açın ve kendi zamanlanmış tarama dosyanız için kılavuz olarak bu örneği kullanın.

    ```XML
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
      "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
    <dict>
        <key>Label</key>
        <string>com.microsoft.wdav.schedquickscan</string>
        <key>ProgramArguments</key>
        <array>
            <string>sh</string>
            <string>-c</string>
            <string>/usr/local/bin/mdatp scan quick</string>
        </array>
        <key>RunAtLoad</key>
        <true/>
        <key>StartCalendarInterval</key>
        <dict>
            <key>Day</key>
            <integer>3</integer>
            <key>Hour</key>
            <integer>2</integer>
            <key>Minute</key>
            <integer>0</integer>
            <key>Weekday</key>
            <integer>5</integer>
        </dict>
        <key>WorkingDirectory</key>
        <string>/usr/local/bin/</string>
    </dict>
    </plist>
     ```

2. Dosyayı *com.microsoft.wdav.schedquickscan.plist olarak kaydedin*.

### <a name="schedule-a-full-scan"></a>Tam tarama zamanlama

1. Bir metin düzenleyicisi açın ve tam tarama için bu örneği kullanın.

    ```XML
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
      "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1.0">
    <dict>
        <key>Label</key>
        <string>com.microsoft.wdav.schedfullscan</string>
        <key>ProgramArguments</key>
        <array>
            <string>sh</string>
            <string>-c</string>
            <string>/usr/local/bin/mdatp scan full</string>
        </array>
        <key>RunAtLoad</key>
        <true/>
        <key>StartCalendarInterval</key>
        <dict>
            <key>Day</key>
            <integer>3</integer>
            <key>Hour</key>
            <integer>2</integer>
            <key>Minute</key>
            <integer>50</integer>
            <key>Weekday</key>
            <integer>5</integer>
        </dict>
        <key>WorkingDirectory</key>
        <string>/usr/local/bin/</string>
    </dict>
    </plist>
     ```

2. Dosyayı *com.microsoft.wdav.schedfullscan.plist olarak kaydedin*.
 
### <a name="load-your-file"></a>Dosyanızı yükleme

1. **Terminal'i açın**.
2. Dosyanızı yüklemek için aşağıdaki komutları girin:

    ```bash
    launchctl load /Library/LaunchDaemons/<your file name.plist>
    launchctl start <your file name>
    ```

3. Zamanlanmış taramanız, p-listesinde tanımlandığı tarih, saat ve sıklıkta görüntülenir. Önceki örneklerde, tarama her Cuma için 02:50'de çalışır. 

    - Değeri `Weekday` , `StartCalendarInterval` haftanın beşinci günü veya Cuma'sı göstermek için bir tamsayı kullanır. Aralık 0 ile 7 arasındadır ve Pazar'ı temsil eden 7'dir.
    - Değeri `Day` , `StartCalendarInterval` ayın üçüncü günü göstermek için bir tamsayı kullanır. Aralık 1 ile 31 arasındadır.
    - Değeri `Hour` , `StartCalendarInterval` günün ikinci saatlerini göstermek için bir tamsayı kullanır. Aralık 0 ile 24 arasındadır.
    Değeri `Minute` , saati `StartCalendarInterval` elli dakika göstermek için bir tamsayı kullanır. Aralık 0 ile 59 arasındadır.
    
    
 > [!IMPORTANT]
 > Başlatma ile yürütülen *aracılar* , cihaz uyku sırasında zamanlanan zamanda çalıştırlanmaz. Bunun yerine, cihaz uyku modundan kaldığında çalışır.
 >
 > Cihaz kapalı olursa, tarama bir sonraki zamanlanmış tarama zamanında  çalışmasına izin verir.

## <a name="schedule-a-scan-with-intune"></a>Intune ile tarama zamanlama

Ayrıca, diğer programlarla tarama Microsoft Intune. Cihaz [runMDATPQuickScan.sh](https://github.com/microsoft/shell-intune-samples/tree/master/Misc/MDATP#runmdatpquickscansh) modundan kaldığında, Uç Nokta için [Microsoft Defender](https://github.com/microsoft/shell-intune-samples/tree/master/Misc/MDATP) Için Betikler'de bulunan komut kabuğu betiği kalıcı olur. 

Bu [betiği kurumda nasıl kullanabileceğinize ilişkin daha ayrıntılı yönergeler için bkz. Intune'daki macOS](/mem/intune/apps/macos-shell-scripts) cihazlarında kabuk betikleri kullanma.
