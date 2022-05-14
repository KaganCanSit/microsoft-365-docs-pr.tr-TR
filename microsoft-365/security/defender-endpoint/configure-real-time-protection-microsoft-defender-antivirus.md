---
title: Microsoft Defender Virüsten Koruma koruma özelliklerini etkinleştirme ve yapılandırma
description: Davranış izleme, buluşsal yöntemler ve makine öğrenmesi gibi Microsoft Defender Virüsten Koruma gerçek zamanlı koruma özelliklerini etkinleştirme ve yapılandırma
keywords: virüsten koruma, gerçek zamanlı koruma, rtp, makine öğrenmesi, davranış izleme, buluşsal yöntemler
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.date: 10/22/2021
manager: dansimp
ms.custom: nextgen
ms.collection: M365-security-compliance
ms.openlocfilehash: d950e69a557ccc95fe40bf300dae05f64e51032e
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416046"
---
# <a name="enable-and-configure-microsoft-defender-antivirus-always-on-protection-in-group-policy"></a> Grup İlkesinde sürekli korumayı Microsoft Defender Virüsten Koruma ile etkinleştirin ve yapılandırın

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Her zaman açık koruma, bilinen şüpheli ve kötü amaçlı etkinliklere dayalı kötü amaçlı yazılımları tanımlamak için gerçek zamanlı koruma, davranış izleme ve buluşsal yöntemlerden oluşur.

Bu etkinlikler arasında mevcut dosyalarda olağan dışı değişiklikler yapan işlemler, otomatik başlangıç kayıt defteri anahtarlarını ve başlangıç konumlarını (otomatik başlangıç genişletilebilirlik noktaları veya ASEP'ler olarak da bilinir) değiştirme veya oluşturma gibi olaylar ve dosya sisteminde veya dosya yapısında yapılan diğer değişiklikler yer alır.

## <a name="enable-and-configure-always-on-protection-in-group-policy"></a>grup ilkesi'de her zaman açık korumayı etkinleştirme ve yapılandırma

Microsoft Defender Virüsten Koruma her zaman açık koruma ayarlarını etkinleştirmek ve yapılandırmak için **Yerel grup ilkesi Düzenleyicisi'ni** kullanabilirsiniz.

Her zaman açık korumayı etkinleştirmek ve yapılandırmak için:

1. **Yerel grup ilkesi Düzenleyicisi'ni** aşağıdaki gibi açın:

    1. Windows 10 veya Windows 11 görev çubuğu arama kutunuza **gpedit** yazın.

    2. **En iyi eşleşme'nin** altında **Grup ilkesini düzenle'yi** seçerek **Yerel grup ilkesi Düzenleyicisi'ni** başlatın.
    
       :::image type="content" source="images/gpedit-search.png" alt-text="Denetim masası'ndaki GPEdit görev çubuğu arama sonucu" lightbox="images/gpedit-search.png":::

2. **Yerel grup ilkesi Düzenleyicisi'nin** sol bölmesinde, ağacı **Bilgisayar Yapılandırması** \> **Yönetim Şablonları** \> **Windows Bileşenler** \> **Microsoft Defender Virüsten Koruma** olarak genişletin.

3. Microsoft Defender Virüsten Koruma kötü amaçlı yazılımdan koruma hizmeti ilkesi ayarını yapılandırın.

   Sağ taraftaki **Microsoft Defender Virüsten Koruma** ayrıntıları bölmesinde Kötü **amaçlı yazılımdan koruma hizmetinin normal öncelikle başlatılmasına izin ver'e** çift tıklayın ve **Etkin** olarak ayarlayın.

   Sonra **Tamam**’ı seçin.

4. Microsoft Defender Virüsten Koruma gerçek zamanlı koruma ilkesi ayarlarını aşağıdaki gibi yapılandırın:

    1. **Microsoft Defender Virüsten Koruma** ayrıntılar bölmesinde **Gerçek Zamanlı Koruma'ya** çift tıklayın. Ya da sol bölmedeki **Microsoft Defender Virüsten Koruma** **ağacından Gerçek Zamanlı Koruma'yı** seçin.

    2. Sağdaki **Gerçek Zamanlı Koruma** ayrıntıları bölmesinde, [gerçek zamanlı koruma ilkesi ayarlarında](#real-time-protection-policy-settings) belirtildiği gibi ilke ayarına çift tıklayın (bu makalenin ilerleyen bölümlerinde).

    3. Ayarı uygun şekilde yapılandırın ve **Tamam'ı** seçin.

    4. Tablodaki her ayar için önceki adımları yineleyin.

5. Microsoft Defender Virüsten Koruma tarama ilkesi ayarını aşağıdaki gibi yapılandırın:

    1. Sol bölmedeki **Microsoft Defender Virüsten Koruma** ağacında **Tara'yı** seçin.
    
   2. Sağ taraftaki **Tarama** ayrıntıları bölmesinde **Buluşsal yöntemleri aç'a** çift tıklayın ve **Etkin** olarak ayarlayın. 

   3. **Tamam**'ı seçin.

6. **Yerel grup ilkesi Düzenleyicisi'ni** kapatın.

### <a name="real-time-protection-policy-settings"></a>Gerçek zamanlı koruma ilkesi ayarları

|Ayar|Varsayılan ayar|
|---|---|
|Davranış izlemeyi açma <p> Virüsten koruma altyapısı şüpheli ve bilinen kötü amaçlı etkinlikler için uç noktalarınızdaki dosya işlemlerini, dosya ve kayıt defteri değişikliklerini ve diğer olayları izler.|Etkin|
|İndirilen tüm dosyaları ve ekleri tara <p> İndirilen dosyalar ve ekler otomatik olarak taranır. Bu tarama, indirme öncesinde ve sırasında dosyaları tarayan Windows Defender SmartScreen filtresine ek olarak çalışır.|Etkin|
|Bilgisayarınızda dosya ve program etkinliğini izleme <p> Microsoft Defender Virüsten Koruma altyapısı tüm dosya değişikliklerini (taşımalar, kopyalar veya değişiklikler gibi dosya yazma işlemleri) ve genel program etkinliğini (açılan veya çalışan ve diğer programların çalışmasına neden olan programlar) not eder.|Etkin|
|Ham birim yazma bildirimlerini açma <p> Ham birim yazma işlemleri hakkındaki bilgiler davranış izleme tarafından analiz edilir.|Etkin|
|Gerçek zamanlı koruma etkinleştirildiğinde işlem taramasını açma <p> Microsoft Defender Virüsten Koruma altyapısını, çalışan işlemleri şüpheli değişiklikler veya davranışlar için taramak üzere bağımsız olarak etkinleştirebilirsiniz. Gerçek zamanlı korumayı geçici olarak devre dışı bırakmış ve devre dışı bırakıldığı sırada başlayan işlemleri otomatik olarak taramak istiyorsanız bu yararlı olur.|Etkin|
|Taranacak indirilen dosyaların ve eklerin en büyük boyutunu tanımlama <p> Boyutu kilobayt cinsinden tanımlayabilirsiniz.|Etkin|
|Davranış izlemeyi açmak için yerel ayarı geçersiz kılmayı yapılandırma <p> Davranış izleme yapılandırması için yerel bir geçersiz kılma yapılandırın. Bu ayar yalnızca grup ilkesi tarafından ayarlanabilir. Bu ayarı etkinleştirirseniz, yerel tercih ayarı grup ilkesi öncelikli olur. Bu ayarı devre dışı bırakır veya yapılandırmazsanız, grup ilkesi yerel tercih ayarına göre öncelik alır.|Etkin|
|İndirilen tüm dosya ve ekleri taramak için yerel ayarı geçersiz kılmayı yapılandırma <p> İndirilen tüm dosyalar ve ekler için tarama yapılandırması için yerel bir geçersiz kılma yapılandırın. Bu ayar yalnızca grup ilkesi tarafından ayarlanabilir. Bu ayarı etkinleştirirseniz, yerel tercih ayarı grup ilkesi öncelikli olur. Bu ayarı devre dışı bırakır veya yapılandırmazsanız, grup ilkesi yerel tercih ayarına göre öncelik alır.|Etkin|
|Bilgisayarınızda dosya ve program etkinliğini izlemek için yerel ayarı geçersiz kılmayı yapılandırma <p> Bilgisayarınızda dosya ve program etkinliği için izleme yapılandırması için yerel bir geçersiz kılma yapılandırın. Bu ayar yalnızca grup ilkesi tarafından ayarlanabilir. Bu ayarı etkinleştirirseniz, yerel tercih ayarı grup ilkesi öncelikli olur. Bu ayarı devre dışı bırakır veya yapılandırmazsanız, grup ilkesi yerel tercih ayarına göre öncelik alır.|Etkin|
|Gerçek zamanlı korumayı açmak için yerel ayarı geçersiz kılmayı yapılandırma <p> Gerçek zamanlı korumayı açmak için yapılandırma için yerel bir geçersiz kılma yapılandırın. Bu ayar yalnızca grup ilkesi tarafından ayarlanabilir. Bu ayarı etkinleştirirseniz, yerel tercih ayarı grup ilkesi öncelikli olur. Bu ayarı devre dışı bırakır veya yapılandırmazsanız, grup ilkesi yerel tercih ayarına göre öncelik alır.|Etkin|
|Gelen ve giden dosya etkinliği için izleme için yerel ayarı geçersiz kılmayı yapılandırma <p> Gelen ve giden dosya etkinliği için izleme yapılandırması için yerel bir geçersiz kılma yapılandırın. Bu ayar yalnızca grup ilkesi tarafından ayarlanabilir. Bu ayarı etkinleştirirseniz, yerel tercih ayarı grup ilkesi öncelikli olur. Bu ayarı devre dışı bırakır veya yapılandırmazsanız, grup ilkesi yerel tercih ayarına göre öncelik alır.|Etkin|
|Gelen ve giden dosya ve program etkinliği için izlemeyi yapılandırma <p> İzlemenin gelen, giden, her iki yönde mi yoksa her iki yönde mi gerçekleşeceğini belirtin. Bu eylem, yalnızca bir yönde büyük miktarda dosya değişikliği gören ve ağ performansını geliştirmek istediğiniz belirli sunucuları veya Sunucu Rollerini tanımladığınız Windows Sunucu yüklemeleri için geçerlidir. Bir ağdaki tam olarak güncelleştirilmiş uç noktalar (ve sunucular), dosya değişikliklerinin sayısı veya yönü ne olursa olsun çok az performans etkisi görür.|Etkin (her iki yön)|

## <a name="disable-real-time-protection-in-group-policy"></a>grup ilkesi'de gerçek zamanlı korumayı devre dışı bırakma

> [!WARNING]
> Gerçek zamanlı korumayı devre dışı bırakmak uç noktalarınızdaki korumayı önemli ölçüde azaltır ve önerilmez.

Ana gerçek zamanlı koruma özelliği varsayılan olarak etkindir, ancak **Yerel grup ilkesi Düzenleyicisi'ni** kullanarak devre dışı bırakabilirsiniz.

### <a name="to-disable-real-time-protection-in-group-policy"></a>Grup ilkesinde gerçek zamanlı korumayı devre dışı bırakmak için

1. **Yerel grup ilkesi Düzenleyicisi'ni** açın.

   1. Windows 10 veya Windows 11 görev çubuğu arama kutunuza **gpedit** yazın.
   2. **En iyi eşleşme'nin** altında **Grup ilkesini düzenle'yi** seçerek **Yerel grup ilkesi Düzenleyicisi'ni** başlatın.

2. **Yerel grup ilkesi Düzenleyicisi'nin** sol bölmesinde, ağacı **Gerçek Zamanlı Koruma** **Microsoft Defender Virüsten Koruma Bileşenler** \> Windows **Bilgisayar Yapılandırması** \> **Yönetim Şablonları** \> **olarak** \> genişletin.

3. Sağdaki **Gerçek Zamanlı Koruma** ayrıntıları bölmesinde **Gerçek zamanlı korumayı kapat'a** çift tıklayın.

4. **Gerçek zamanlı koruma ayarını kapat** penceresinde seçeneği **Etkin** olarak ayarlayın.
   
5. **Tamam**'ı seçin.

6. **Yerel grup ilkesi Düzenleyicisi'ni** kapatın.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Davranışsal, buluşsal ve gerçek zamanlı korumayı yapılandırın](configure-protection-features-microsoft-defender-antivirus.md)
- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
