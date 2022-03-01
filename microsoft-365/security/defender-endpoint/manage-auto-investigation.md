---
title: Otomatik soruşturmaları takip eden düzeltme eylemlerini gözden geçirme
description: Otomatik bir incelemeden sonra düzeltme eylemlerini gözden geçirme ve onaylama (veya reddetme).
keywords: otomatik, otomatik, araştırma, algılama, düzeltme, eylem, beklemede, onaylandı
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: JoeDavies-MSFT
ms.author: josephd
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: how-to
ms.date: 01/29/2021
ms.technology: mde
ms.openlocfilehash: f6886cd109e8727dd05c7de0b4055f839b847de2
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998154"
---
# <a name="review-remediation-actions-following-an-automated-investigation"></a>Otomatik bir soruşturmayı takip eden düzeltme eylemlerini gözden geçirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="remediation-actions"></a>Düzeltme eylemleri

Otomatik [bir araştırma çalıştırıldığı](automated-investigations.md) zaman, araştırılan her kanıt parçası için bir karar oluşturulur. Kararlara Kötü *Amaçlı*, Şüpheli *veya* Tehdit *bulunamadı denmektedir*.

Buna bağlı olarak

- tehdit türü,
- karar ve
- kuruluş cihaz [gruplarının nasıl](/microsoft-365/security/defender-endpoint/machine-groups) yapılandırıldı,

düzeltme eylemleri otomatik olarak veya yalnızca kuruluşun güvenlik işlemleri ekibinin onayı üzerine gerçekleşir.

İşte birkaç örnek:

- **Örnek 1**: Fabrikam'ın cihaz grupları Tam olarak ayarlanır **- tehditleri otomatik olarak düzeltmek** (önerilen ayar). Bu durumda, otomatik bir soruşturmadan sonra kötü amaçlı olduğu kabul edilen yapılar için düzeltme eylemleri otomatik olarak yapılır (bkz. [Tamamlanmış eylemleri gözden geçirme](#review-completed-actions)).

- **Örnek 2**: Contoso'nun cihazları Yarı olarak ayarlanmış bir cihaz grubuna **eklidir; herhangi bir düzeltme için onay gerektirir**. Bu durumda, Contoso'nun güvenlik işlemleri ekibinin otomatik bir soruşturmadan sonraki tüm düzeltme eylemlerini gözden geçirmesi ve onaylaması gerekir (bkz. Bekleyen [eylemleri gözden geçirme](#review-pending-actions)).

- **Örnek 3**: Tailspin Toys'un cihaz grupları **Otomatik yanıt yok** (önerilmez) olarak ayarlanmıştır. Bu durumda, otomatik soruşturmalar oluşmaz. Hiçbir düzeltme eylemi gerçekleştir alınmaz veya beklemededir ve cihazları için İşlem merkezine hiçbir eylem kaydedilmez (bkz. [Cihaz gruplarını yönetme](/microsoft-365/security/defender-endpoint/machine-groups#manage-device-groups)).[](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)

İster otomatik olarak ister onaylansın, otomatik bir soruşturma düzeltme eylemlerinden birini veya birden fazlasını oluşturabilir:

- Dosyayı karantinaya alın
- Kayıt defteri anahtarını kaldırma
- Süreci kill
- Hizmeti durdurma
- Sürücüyü devre dışı bırakma
- Zamanlanmış görevi kaldırma

## <a name="review-pending-actions"></a>Bekleyen eylemleri gözden geçirme

1. Oturum açma <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender gidin</a>.
2. Gezinti bölmesinde İşlem **merkezi'ni seçin**.
3. Bekleyen sekmesindeki öğeleri **gözden** geçirme.
4. Açılır bölmesini açmak için bir eylem seçin.
5. Uçarak çıkış bölmesinde bilgileri gözden geçirin ve sonra aşağıdaki adımlardan birini uygulayın:
   - Araştırma **hakkında daha fazla ayrıntı** görüntülemek için Araştırma sayfasını aç'ı seçin.
   - Bekleyen **bir eylemi** başlatmak için Onayla'ya seçin.
   - Bekleyen **bir eylemin** askıya alınmasını önlemek için Reddet'i seçin.
   - Gelişmiş **ava gitmek** için Avına [git'i seçin](advanced-hunting-overview.md).

## <a name="review-completed-actions"></a>Tamamlanan eylemleri gözden geçirme

1. Oturum açma <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender gidin</a>.
2. Gezinti bölmesinde İşlem **merkezi'ni seçin**.
3. Geçmiş sekmesindeki öğeleri **gözden** geçirme.
4. Düzeltme eylemi hakkında daha fazla ayrıntı görüntülemek için bir öğe seçin.

## <a name="undo-completed-actions"></a>Tamamlanmış eylemleri geri alma

Bir cihaz veya dosyanın bir tehdit olmadığını belirlediysanız, yapılan düzeltme eylemlerini geri alabilirsiniz (bu eylemlerin otomatik olarak veya el ile gerçekleştirileme). İşlem merkezi'nin Geçmiş **sekmesinde** , aşağıdaki eylemlerden herhangi birini geri alabilirsiniz:

<br>

****

|Eylem kaynağı|Desteklenen Eylemler|
|---|---|
|<ul><li>Otomatik araştırma</li><li>Microsoft Defender Virüsten Koruma</li><li>El ile yanıt eylemleri</li></ul>|<ul><li>Cihazı yalıt</li><li>Kod yürütmeyi kısıtlama</li><li>Dosyayı karantinaya alın</li><li>Kayıt defteri anahtarını kaldırma</li><li>Hizmeti durdurma</li><li>Sürücüyü devre dışı bırakma</li><li>Zamanlanmış görevi kaldırma</li></ul>|
|

### <a name="to-undo-multiple-actions-at-one-time"></a>Bir defada birden çok eylemi geri almak için

1. İşlem merkezi'ne ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) gidin ve oturum açma.
2. Geçmiş **sekmesinde** , geri almak istediğiniz eylemleri seçin. Aynı Eylem türüne sahip öğeleri seçmeye emin olun. Açılır bölme açılır.
3. Uçarak çıkış bölmesinde Geri Al'ı **seçin**.

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Dosyayı birden çok cihaz genelinde karantinadan kaldırmak için

1. İşlem merkezi'ne ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) gidin ve oturum açma.
2. Geçmiş **sekmesinde** , Eylem türü Karantina dosyası olan bir **öğeyi seçin**.
3. Uçarak çıkış bölmesinde Bu dosyanın **daha fazla X örneğine uygula'ya tıklayın ve sonra** da Geri Al'ı **seçin**.

## <a name="automation-levels-automated-investigation-results-and-resulting-actions"></a>Otomasyon düzeyleri, otomatik soruşturma sonuçları ve sonuçta elde edilen eylemler

Otomasyon düzeyleri, bazı düzeltme eylemlerinin otomatik olarak veya yalnızca onay üzerine alınıp alınmayacaklarını etkiler. Bazen güvenlik işlemleri ekibinin, otomatik bir soruşturmanın sonuçlarına bağlı olarak atılması gereken daha fazla adım olabilir. Aşağıdaki tabloda otomasyon düzeyleri, otomatik soruşturmaların sonuçları ve bu durumlarda nelerin gerçekleştirıldığı özetlenmiştir.

<br>

****

|Cihaz grubu ayarı|Otomatik soruşturma sonuçları|Ne yapmalı?|
|---|---|---|
|**Tam - tehditleri otomatik olarak düzeltme** (önerilen ayar)|Bir kanıt *için Kötü* Amaçlı bir karara ulaşıldı. <p> Uygun düzeltme eylemleri otomatik olarak  alınır.|[Tamamlanan eylemleri gözden geçirme](#review-completed-actions)|
|**Tam - tehditleri otomatik olarak düzeltme**|Bir kanıt *için* Kuşkulu bir karara ulaşıldı. <p> Düzeltme eylemleri devam etmek için onay bekliyor.|[Bekleyen eylemleri onaylama (veya reddetme)](#review-pending-actions)|
|**Yarı - herhangi bir düzeltme için onay gerektir**|Bir kanıt için *Kötü* Amaçlı *veya Şüpheli* karara varıldı. <p> Düzeltme eylemleri devam etmek için onay bekliyor.|[Bekleyen eylemleri onaylama (veya reddetme)](#review-pending-actions)|
|**Yarı - temel klasörlerin düzeltmesi için onay gerektir**|Bir kanıt *için Kötü* Amaçlı bir karara ulaşıldı. <p> Yapı bir dosya veya yürütülebilir bir dosya ise ve Windows klasörü veya Program dosyaları klasörü gibi bir işletim sistemi dizinindeyse, düzeltme eylemleri onay bekliyor olur. <p> Yapı bir işletim *sistemi* dizininde değil de, düzeltme eylemleri otomatik olarak yapılır.|<ol><li>[Bekleyen eylemleri onaylama (veya reddetme)](#review-pending-actions)</li><li>[Tamamlanan eylemleri gözden geçirme](#review-completed-actions)</li></ol>|
|**Yarı - temel klasörlerin düzeltmesi için onay gerektir**|Bir kanıt *için* Kuşkulu bir karara ulaşıldı. <p> Düzeltme eylemleri onay bekliyor.|[Bekleyen eylemleri onaylayın (veya reddedin](#review-pending-actions)).|
|**Yarı - geçici olmayan klasörlerin düzeltmesi için onay gerekiyor**|Bir kanıt *için Kötü* Amaçlı bir karara ulaşıldı. <p> Yapı, kullanıcının indirilenler klasörü veya geçici klasör gibi geçici bir klasörde yer alan bir dosya veya yürütülebilir dosyadansa, düzeltme eylemleri onay bekliyordur. <p> Yapı, geçici bir klasörde yer alan *bir dosya* veya yürütülebilir dosya ise, düzeltme eylemleri otomatik olarak çalıştırılabilir.|<ol><li>[Bekleyen eylemleri onaylama (veya reddetme)](#review-pending-actions)</li><li>[Tamamlanan eylemleri gözden geçirme](#review-completed-actions)</li></ol>|
|**Yarı - geçici olmayan klasörlerin düzeltmesi için onay gerekiyor**|Bir kanıt *için* Kuşkulu bir karara ulaşıldı. <p> Düzeltme eylemleri onay bekliyor.|[Bekleyen eylemleri onaylama (veya reddetme)](#review-pending-actions)|
|Tüm Tam **veya Yarı** **otomasyon** düzeyleri|Bulunan hiçbir *tehdit yok kararının* bir kanıtına ulaşıldı. <p> Düzeltme eylemi gerçekleştir alınmaz ve onay için hiçbir işlem beklemez.|[Otomatik soruşturmaların ayrıntılarını ve sonuçlarını görüntüleme](/microsoft-365/security/defender-endpoint/auto-investigation-action-center)|
|**Otomatik yanıt yok** (önerilmez)|Otomatik bir araştırma çalıştırıldığı için kararlara ulaşıldığı ve hiçbir düzeltme işlemi gerçekleştirilemez ya da onay bekliyor.|[Tam veya Yarı otomasyon kullanmak için cihaz gruplarınızı **ayarlamayı veya** **değiştirmeyi düşünebilirsiniz**](/microsoft-365/security/defender-endpoint/machine-groups)|
|

Uç Nokta için Microsoft Defender'da tüm kararlara İşlem [merkezinden bakıldı](auto-investigation-action-center.md#new-a-unified-action-center).

## <a name="next-steps"></a>Sonraki adımlar

- [Canlı yanıt özellikleri hakkında bilgi](live-response.md)
- [Gelişmiş avla tehditlere karşı önceden arama](advanced-hunting-overview.md)
- [Uç nokta için Microsoft Defender'da hatalı pozitif/negatifleri adresle](defender-endpoint-false-positives-negatives.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik soruşturmalara genel bakış](automated-investigations.md)
