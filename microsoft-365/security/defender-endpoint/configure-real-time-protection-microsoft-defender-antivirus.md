---
title: Veri koruma Microsoft Defender Virüsten Koruma etkinleştirme ve yapılandırma
description: Davranış izleme Microsoft Defender Virüsten Koruma heuristics ve makine öğrenimi gibi gerçek zamanlı koruma özelliklerini etkinleştirme ve yapılandırma
keywords: virüsten koruma, gerçek zamanlı koruma, rtp, makine öğrenimi, davranış izleme, heuristics
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
ms.openlocfilehash: 9af87907c476b637ddc484bbb3357b143219107e
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473221"
---
# <a name="enable-and-configure-microsoft-defender-antivirus-always-on-protection-in-group-policy"></a>Her zaman açık Microsoft Defender Virüsten Koruma etkinleştirme ve grup ilkesi yapılandırma


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Her zaman açık koruma, bilinen şüpheli ve kötü amaçlı etkinliklere dayalı kötü amaçlı yazılımları tanımlamak için gerçek zamanlı koruma, davranış izleme ve heuristlerden oluşur.

Bu etkinlikler arasında mevcut dosyalarda olağandışı değişiklikler yapan işlemler, otomatik başlangıç kayıt defteri anahtarları ve başlangıç konumları (otomatik başlangıç genişletilebilirlik noktaları veya ASEP'ler olarak da bilinir) ve dosya sistemi ya da dosya yapısında yapılan diğer değişiklikler gibi olaylar yer almaktadır.

## <a name="enable-and-configure-always-on-protection-in-group-policy"></a>Her zaman açık korumayı tek bir dosyada etkinleştirme grup ilkesi

Her zaman açık **koruma grup ilkesi etkinleştirmek ve** yapılandırmak için Yerel Microsoft Defender Virüsten Koruma Düzenleyicisi'ni kullanabilirsiniz.

Her zaman açık korumayı etkinleştirmek ve yapılandırmak için:

1. Yerel **Grup ilkesi Düzenleyicisi'ni** aşağıdaki gibi açın:

    1. Görev çubuğu Windows 10 veya Windows 11 kutusuna **gpedit yazın**.

    2. En **iyi eşleşme'nin** altında **Grup İlkesini düzenle'yi seçerek** **Yerel grup ilkesi'ni açın**.
    
       :::image type="content" source="images/gpedit-search.png" alt-text="Denetim Masası'nda GPEdit görev çubuğu arama sonucu" lightbox="images/gpedit-search.png":::

2. Yerel Posta  **Düzenleyicisi'nin sol grup ilkesi,** ağacı Bilgisayar **Yapılandırması** \> \> Yönetim Şablonları ve Bileşenleri **Windows'Microsoft Defender Virüsten Koruma**\>.

3. Kötü amaçlı Microsoft Defender Virüsten Koruma koruma hizmet ilkesi ayarını yapılandırma.

   Yazılım **Microsoft Defender Virüsten Koruma** bölmesinde Kötü amaçlı yazılımdan koruma **hizmetinin normal** önceliğe sahip başlamasına izin ver'e çift tıklayın ve bunu Etkin olarak **ayarlayın**.

   Sonra **Tamam**’ı seçin.

4. Gerçek zamanlı Microsoft Defender Virüsten Koruma ilke ayarlarını aşağıdaki gibi yapılandırın:

    1. Ayrıntılar **Microsoft Defender Virüsten Koruma**, Gerçek Zamanlı **Koruma'ya çift tıklayın**. Ya da sol **Microsoft Defender Virüsten Koruma** Bölmesindeki Yeni Ağaç'dan **Gerçek Zamanlı Koruma'ya tıklayın**.

    2. Sağki **Gerçek Zamanlı Koruma** ayrıntıları bölmesinde, Gerçek zamanlı koruma ilkesi [ayarlarında (bu](#real-time-protection-policy-settings) makalenin devamlarında) belirtilen ilke ayarına çift tıklayın.

    3. Ayarı uygun şekilde yapılandırarak Tamam'ı **seçin**.

    4. Tablodaki her ayar için önceki adımları yineler.

5. Tarama Microsoft Defender Virüsten Koruma ayarını aşağıdaki gibi yapılandırabilirsiniz:

    1. Sol bölme **Microsoft Defender Virüsten Koruma** Tarama'ya **tıklayın**.
    
   2. Sağdan **Tarama** ayrıntıları bölmesinde, Üç çıtayı **aç'a çift tıklayın** ve bunu Etkin olarak **ayarlayın**. 

   3. **Tamam**'ı seçin.

6. Yerel **Düzenleyici'grup ilkesi kapatın**.

### <a name="real-time-protection-policy-settings"></a>Gerçek zamanlı koruma ilkesi ayarları

|Ayar|Varsayılan ayar|
|---|---|
|Davranış izlemeyi açma <p> Virüsten koruma altyapısı şüpheli ve bilinen kötü amaçlı etkinlikler için uç noktalarınız üzerinde dosya işlemlerini, dosya ve kayıt defteri değişikliklerini ve diğer olayları izlemektedir.|Etkin|
|İndirilen tüm dosyaları ve ekleri tarama <p> İndirilen dosya ve ekler otomatik olarak taranır. Bu tarama, indirme öncesinde ve sırasında Windows Defender tarayın SmartScreen filtresine ek olarak çalışır.|Etkin|
|Bilgisayarınızda dosya ve program etkinliğini izleme <p> Microsoft Defender Virüsten Koruma altyapısı, dosya değişikliklerini (taşır, kopyalar veya değişiklikler gibi dosya yazma) ve genel program etkinliğini (açık veya çalışan ve başka programların çalışmasına neden olan programlar) not eder.|Etkin|
|Ham hacim yazma bildirimlerini açma <p> Ham hacim yazma hakkında bilgiler davranış izleme ile çözüm olur.|Etkin|
|Gerçek zamanlı koruma etkinleştirildiğinde süreç taramasını açma <p> Microsoft Defender Virüsten Koruma altyapısının şüpheli değişiklikler veya davranışlar için çalıştırma işlemlerini taramasını bağımsız olarak etkinleştirebilirsiniz. Gerçek zamanlı korumayı geçici olarak devre dışı bırakıyorsanız ve koruma devre dışıyken başlamış işlemleri otomatik olarak taramak istiyorsanız, bu yararlı olur.|Etkin|
|İndirilen dosya ve eklerin taranacak en büyük boyutunu tanımlama <p> Boyutu kilobayt cinsinden tanımlayabilirsiniz.|Etkin|
|Davranış izlemeyi açmak için yerel ayarı geçersiz kılmayı yapılandırma <p> Davranış izleme yapılandırması için yerel geçersiz kılmayı yapılandırma. Bu ayar yalnızca başka bir grup ilkesi. Bu ayarı etkinleştirirseniz, yerel tercih ayarı tercih tercihlerinize göre grup ilkesi. Bu ayarı devre dışı bırakır veya yapılandırmazsanız, grup ilkesi tercih ayarına göre öncelikli olacaktır.|Etkin|
|İndirilen tüm dosyaları ve ekleri taramak için yerel ayarı geçersiz kılmayı yapılandırma <p> İndirilen tüm dosya ve ekleri tarama yapılandırması için yerel geçersiz kılmayı yapılandırabilirsiniz. Bu ayar yalnızca başka bir grup ilkesi. Bu ayarı etkinleştirirseniz, yerel tercih ayarı tercih tercihlerinize göre grup ilkesi. Bu ayarı devre dışı bırakır veya yapılandırmazsanız, grup ilkesi tercih ayarına göre öncelikli olacaktır.|Etkin|
|Bilgisayarınızda dosyayı ve program etkinliğini izlemek için yerel ayarı geçersiz kılmayı yapılandırma <p> Bilgisayarınızda dosya ve program etkinliği için izleme yapılandırması için yerel geçersiz kılmayı yapılandırabilirsiniz. Bu ayar yalnızca başka bir grup ilkesi. Bu ayarı etkinleştirirseniz, yerel tercih ayarı tercih tercihlerinize göre grup ilkesi. Bu ayarı devre dışı bırakır veya yapılandırmazsanız, grup ilkesi tercih ayarına göre öncelikli olacaktır.|Etkin|
|Gerçek zamanlı korumayı açmak için yerel ayarı geçersiz kılmayı yapılandırma <p> Gerçek zamanlı korumayı açmak için yapılandırma için yerel geçersiz kılmayı yapılandırma. Bu ayar yalnızca başka bir grup ilkesi. Bu ayarı etkinleştirirseniz, yerel tercih ayarı tercih tercihlerinize göre grup ilkesi. Bu ayarı devre dışı bırakır veya yapılandırmazsanız, grup ilkesi tercih ayarına göre öncelikli olacaktır.|Etkin|
|Gelen ve giden dosya etkinliğini izlemek için yerel ayarı geçersiz kılmayı yapılandırma <p> Gelen ve giden dosya etkinliği için izleme yapılandırması için yerel geçersiz kılmayı yapılandırabilirsiniz. Bu ayar yalnızca başka bir grup ilkesi. Bu ayarı etkinleştirirseniz, yerel tercih ayarı tercih tercihlerinize göre grup ilkesi. Bu ayarı devre dışı bırakır veya yapılandırmazsanız, grup ilkesi tercih ayarına göre öncelikli olacaktır.|Etkin|
|Gelen ve giden dosya ve program etkinliği için izlemeyi yapılandırma <p> İzlemenin gelen, giden, her iki veya her iki yönde de olup olmadığını belirtin. Bu eylem, tek bir Windows büyük miktarlarda dosya değişikliğini gören ve ağ performansını artırmak istediğiniz belirli sunucuları veya Sunucu Rollerini tanım istediğiniz Windows Server yüklemeleri için uygun bir işlemdir. Ağ üzerindeki tam olarak güncelleştirilmiş uç noktalar (ve sunucular), dosya değişikliklerinin sayısına veya yönüne bakılmaksızın performansın az olduğunu görebilir.|Etkin (her iki yol da)|

## <a name="disable-real-time-protection-in-group-policy"></a>E-postada gerçek zamanlı korumayı grup ilkesi

> [!WARNING]
> Gerçek zamanlı korumayı devre dışı bırakmak, uç noktalarınız için korumayı ciddi ölçüde azaltır ve önerilmez.

Ana gerçek zamanlı koruma özelliği varsayılan olarak etkindir, ancak Yerel Koruma Düzenleyicisi'ni kullanarak bu özelliği **grup ilkesi değiştirebilirsiniz**.

### <a name="to-disable-real-time-protection-in-group-policy"></a>Grup ilkesinde gerçek zamanlı korumayı devre dışı bırakmak için

1. Yerel **Düzenleyici grup ilkesi açın**.

   1. Görev çubuğu Windows 10 veya Windows 11 kutusuna **gpedit yazın**.
   2. En **iyi eşleşme'nin** altında **Grup İlkesini düzenle'yi seçerek** **Yerel grup ilkesi'ni açın**.

2. Yerel Sistem  Düzenleyicisi'nin **sol grup ilkesi,** \> \> ağacı Bilgisayar Yapılandırması Yönetim Şablonları'Windows **Ve** \> Bileşenler **Microsoft Defender Virüsten Koruma'e** \> genişletin.

3. Sağ **bölmede yer alan Gerçek** Zamanlı Koruma ayrıntıları bölmesinde Gerçek zamanlı korumayı **kapat'a çift tıklayın**.

4. Gerçek **zamanlı koruma ayarını kapat penceresinde** seçeneği Etkin olarak **ayarlayın**.
   
5. **Tamam**'ı seçin.

6. Yerel **Düzenleyici'grup ilkesi kapatın**.

## <a name="see-also"></a>Ayrıca bkz.

- [Davranışsal, ikill ve gerçek zamanlı korumayı yapılandırma](configure-protection-features-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
