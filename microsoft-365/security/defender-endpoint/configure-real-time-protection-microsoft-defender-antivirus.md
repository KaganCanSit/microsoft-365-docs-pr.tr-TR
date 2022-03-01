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
ms.openlocfilehash: 245aad5498793d951de68e5bf4c3e91510c7d774
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019530"
---
# <a name="enable-and-configure-microsoft-defender-antivirus-always-on-protection-in-group-policy"></a>Grup İlkesi'Microsoft Defender Virüsten Koruma her zaman açık korumayı etkinleştirme ve yapılandırma


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Her zaman açık koruma, bilinen şüpheli ve kötü amaçlı etkinliklere dayalı kötü amaçlı yazılımları tanımlamak için gerçek zamanlı koruma, davranış izleme ve heuristlerden oluşur.

Bu etkinlikler arasında mevcut dosyalarda olağandışı değişiklikler yapan işlemler, otomatik başlangıç kayıt defteri anahtarları ve başlangıç konumları (otomatik başlangıç genişletilebilirlik noktaları veya ASEP'ler olarak da bilinir) ve dosya sistemi ya da dosya yapısında yapılan diğer değişiklikler gibi olaylar yer almaktadır.

## <a name="enable-and-configure-always-on-protection-in-group-policy"></a>Grup İlkesi'de her zaman açık korumayı etkinleştirme ve yapılandırma

Her zaman açık **koruma ayarlarını etkinleştirmek ve** yapılandırmak için Yerel Grup Microsoft Defender Virüsten Koruma Düzenleyicisi'ni kullanabilirsiniz.

Her zaman açık korumayı etkinleştirmek ve yapılandırmak için:

1. Yerel **Grup İlkesi Düzenleyicisi'ni** aşağıdaki gibi açın:

    1. Görev çubuğu Windows 10 veya Windows 11 görev çubuğu arama kutusuna **gpedit yazın**.

    2. En **iyi eşleşme'nin** altında Grup **İlkesini düzenle'yi seçerek** Yerel Grup **İlkesi Düzenleyicisi'ni açın**.
    
       ![GPEdit görev çubuğu arama sonucu.](images/gpedit-search.png)

2. Yerel Grup İlkesi **Düzenleyicisi'nin sol bölmesinde**, ağacı Bilgisayar **Yapılandırması** \>  \> Yönetim Şablonları ve Bileşenleri **ve Windows'Microsoft Defender Virüsten Koruma**\>.

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

6. Yerel **Grup İlkesi Düzenleyicisi'ni kapatın**.

### <a name="real-time-protection-policy-settings"></a>Gerçek zamanlı koruma ilkesi ayarları

|Ayar|Varsayılan ayar|
|---|---|
|Davranış izlemeyi açma <p> Virüsten koruma altyapısı şüpheli ve bilinen kötü amaçlı etkinlikler için uç noktalarınız üzerinde dosya işlemlerini, dosya ve kayıt defteri değişikliklerini ve diğer olayları izlemektedir.|Etkin|
|İndirilen tüm dosyaları ve ekleri tarama <p> İndirilen dosya ve ekler otomatik olarak taranır. Bu tarama, indirme öncesinde ve sırasında Windows Defender tarayın SmartScreen filtresine ek olarak çalışır.|Etkin|
|Bilgisayarınızda dosya ve program etkinliğini izleme <p> Microsoft Defender Virüsten Koruma altyapısı, dosya değişikliklerini (taşır, kopyalar veya değişiklikler gibi dosya yazma) ve genel program etkinliğini (açık veya çalışan ve başka programların çalışmasına neden olan programlar) not eder.|Etkin|
|Ham hacim yazma bildirimlerini açma <p> Ham hacim yazma hakkında bilgiler davranış izleme ile çözüm olur.|Etkin|
|Gerçek zamanlı koruma etkinleştirildiğinde süreç taramasını açma <p> Microsoft Defender Virüsten Koruma altyapısının şüpheli değişiklikler veya davranışlar için çalıştırma işlemlerini taramasını bağımsız olarak etkinleştirebilirsiniz. Gerçek zamanlı korumayı geçici olarak devre dışı bırakıyorsanız ve koruma devre dışıyken başlamış işlemleri otomatik olarak taramak istiyorsanız, bu yararlı olur.|Etkin|
|İndirilen dosya ve eklerin taranacak en büyük boyutunu tanımlama <p> Boyutu kilobayt cinsinden tanımlayabilirsiniz.|Etkin|
|Davranış izlemeyi açmak için yerel ayarı geçersiz kılmayı yapılandırma <p> Davranış izleme yapılandırması için yerel geçersiz kılmayı yapılandırma. Bu ayar yalnızca Grup İlkesi ile ayarlanabilirsiniz. Bu ayarı etkinleştirirseniz, yerel tercih ayarı Grup İlkesine göre öncelikli olacaktır. Bu ayarı devre dışı bırakır veya yapılandırmazsanız, Grup İlkesi yerel tercih ayarına göre öncelikli olur.|Etkin|
|İndirilen tüm dosyaları ve ekleri taramak için yerel ayarı geçersiz kılmayı yapılandırma <p> İndirilen tüm dosya ve ekleri tarama yapılandırması için yerel geçersiz kılmayı yapılandırabilirsiniz. Bu ayar yalnızca Grup İlkesi ile ayarlanabilirsiniz. Bu ayarı etkinleştirirseniz, yerel tercih ayarı Grup İlkesine göre öncelikli olacaktır. Bu ayarı devre dışı bırakır veya yapılandırmazsanız, Grup İlkesi yerel tercih ayarına göre öncelikli olur.|Etkin|
|Bilgisayarınızda dosyayı ve program etkinliğini izlemek için yerel ayarı geçersiz kılmayı yapılandırma <p> Bilgisayarınızda dosya ve program etkinliği için izleme yapılandırması için yerel geçersiz kılmayı yapılandırabilirsiniz. Bu ayar yalnızca Grup İlkesi ile ayarlanabilirsiniz. Bu ayarı etkinleştirirseniz, yerel tercih ayarı Grup İlkesine göre öncelikli olacaktır. Bu ayarı devre dışı bırakır veya yapılandırmazsanız, Grup İlkesi yerel tercih ayarına göre öncelikli olur.|Etkin|
|Gerçek zamanlı korumayı açmak için yerel ayarı geçersiz kılmayı yapılandırma <p> Gerçek zamanlı korumayı açmak için yapılandırma için yerel geçersiz kılmayı yapılandırma. Bu ayar yalnızca Grup İlkesi ile ayarlanabilirsiniz. Bu ayarı etkinleştirirseniz, yerel tercih ayarı Grup İlkesine göre öncelikli olacaktır. Bu ayarı devre dışı bırakır veya yapılandırmazsanız, Grup İlkesi yerel tercih ayarına göre öncelikli olur.|Etkin|
|Gelen ve giden dosya etkinliğini izlemek için yerel ayarı geçersiz kılmayı yapılandırma <p> Gelen ve giden dosya etkinliği için izleme yapılandırması için yerel geçersiz kılmayı yapılandırabilirsiniz. Bu ayar yalnızca Grup İlkesi ile ayarlanabilirsiniz. Bu ayarı etkinleştirirseniz, yerel tercih ayarı Grup İlkesine göre öncelikli olacaktır. Bu ayarı devre dışı bırakır veya yapılandırmazsanız, Grup İlkesi yerel tercih ayarına göre öncelikli olur.|Etkin|
|Gelen ve giden dosya ve program etkinliği için izlemeyi yapılandırma <p> İzlemenin gelen, giden, her iki veya her iki yönde de olup olmadığını belirtin. Bu eylem, tek bir Windows büyük miktarlarda dosya değişikliğini gören ve ağ performansını artırmak istediğiniz belirli sunucuları veya Sunucu Rollerini tanım istediğiniz Windows Server yüklemeleri için uygun bir işlemdir. Ağ üzerindeki tam olarak güncelleştirilmiş uç noktalar (ve sunucular), dosya değişikliklerinin sayısına veya yönüne bakılmaksızın performansın az olduğunu görebilir.|Etkin (her iki yol da)|

## <a name="disable-real-time-protection-in-group-policy"></a>Grup İlkesi'de gerçek zamanlı korumayı devre dışı bırakma

> [!WARNING]
> Gerçek zamanlı korumayı devre dışı bırakmak, uç noktalarınız için korumayı ciddi ölçüde azaltır ve önerilmez.

Ana gerçek zamanlı koruma özelliği varsayılan olarak etkindir, ancak Yerel Grup İlkesi Düzenleyicisi'ni kullanarak **devre dışı abilirsiniz**.

### <a name="to-disable-real-time-protection-in-group-policy"></a>Grup ilkesinde gerçek zamanlı korumayı devre dışı bırakmak için

1. Yerel **Grup İlkesi Düzenleyicisi'ni açın**.

   1. Görev çubuğu Windows 10 veya Windows 11 görev çubuğu arama kutusuna **gpedit yazın**.
   2. En **iyi eşleşme'nin** altında Grup **İlkesini düzenle'yi seçerek** Yerel Grup **İlkesi Düzenleyicisi'ni açın**.

2.  Yerel Grup İlkesi **Düzenleyicisi'nin sol bölmesinde**, ağacı Bilgisayar **Yapılandırması** \> \> Yönetim Şablonları'Windows **Ve** \>  \> ardından **Microsoft Defender Virüsten Koruma'a genişletin**.

3. Sağ **bölmede yer alan Gerçek** Zamanlı Koruma ayrıntıları bölmesinde Gerçek zamanlı korumayı **kapat'a çift tıklayın**.

4. Gerçek **zamanlı koruma ayarını kapat penceresinde** seçeneği Etkin olarak **ayarlayın**.
   
5. **Tamam**'ı seçin.

6. Yerel **Grup İlkesi Düzenleyicisi'ni kapatın**.

## <a name="see-also"></a>Ayrıca bkz.

- [Davranışsal, ikill ve gerçek zamanlı korumayı yapılandırma](configure-protection-features-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
