---
title: Otomatik araştırmalardan sonra düzeltme eylemlerini gözden geçirin
description: Otomatik bir araştırmanın ardından düzeltme eylemlerini gözden geçirin ve onaylayın (veya reddedin).
keywords: autoir, otomatik, araştırma, algılama, düzeltme, eylem, beklemede, onaylandı
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: how-to
ms.technology: mde
ms.openlocfilehash: 06e2c6c5269b32b29be87f44635d65b9c610c344
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535878"
---
# <a name="review-remediation-actions-following-an-automated-investigation"></a>Otomatik bir araştırmanın ardından düzeltme eylemlerini gözden geçirin

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [İş için Microsoft Defender](../defender-business/mdb-overview.md)

## <a name="remediation-actions"></a>Düzeltme eylemleri

Otomatik bir [araştırma](automated-investigations.md) çalıştırıldığında, araştırılan her kanıt parçası için bir karar oluşturulur. Kararlarda *Kötü Amaçlı*, *Şüpheli* veya *Tehdit bulunamadı* olabilir.

Bağlı olarak

- tehdit türü,
- sonuç kararı ve
- kuruluşunuzun [cihaz gruplarının](/microsoft-365/security/defender-endpoint/machine-groups) nasıl yapılandırıldığı,

düzeltme eylemleri otomatik olarak veya yalnızca kuruluşunuzun güvenlik operasyonları ekibi tarafından onaylanarak gerçekleşiyor olabilir.

Aşağıda birkaç örnek verilmiştir:

- **Örnek 1**: Fabrikam'ın cihaz grupları **Tam - tehditleri otomatik olarak düzelt** (önerilen ayar) olarak ayarlanır. Bu durumda, otomatik bir araştırmadan sonra kötü amaçlı olarak kabul edilen yapıtlar için düzeltme eylemleri otomatik olarak gerçekleştirilen işlemlerdir (bkz. [Tamamlanan eylemleri gözden geçirme](#review-completed-actions)).

- **Örnek 2**: Contoso'nun cihazları, Yarı olarak ayarlanmış bir cihaz grubuna dahil edilir **ve herhangi bir düzeltme için onay gerektirir**. Bu durumda Contoso'nun güvenlik operasyonları ekibinin otomatik bir araştırmadan sonra tüm düzeltme eylemlerini gözden geçirmesi ve onaylaması gerekir (bkz [. Bekleyen eylemleri gözden geçirme](#review-pending-actions)).

- **Örnek 3**: Tailspin Toys'un cihaz grupları **Otomatik yanıt yok** (önerilmez) olarak ayarlanmıştır. Bu durumda otomatik araştırma gerçekleşmez. Hiçbir düzeltme eylemi gerçekleştirilmedi veya beklemede değil ve cihazları için [İşlem merkezinde](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center) hiçbir eylem günlüğe kaydedilmez (bkz. [Cihaz gruplarını yönetme](/microsoft-365/security/defender-endpoint/machine-groups#manage-device-groups)).

İster otomatik olarak ister onay üzerine alınsın, otomatik bir araştırma bir veya daha fazla düzeltme eylemine neden olabilir:

- Dosyayı karantinaya al
- Kayıt defteri anahtarını kaldırma
- İşlemi sonlandırma
- Hizmeti durdurma
- Sürücüyü devre dışı bırakma
- Zamanlanmış görevi kaldırma

## <a name="review-pending-actions"></a>Bekleyen eylemleri gözden geçirme

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalına</a> gidin ve oturum açın.

2. Gezinti bölmesinde **İşlem merkezi'ni** seçin.

3. **Bekleyen** sekmesindeki öğeleri gözden geçirin.

4. Açılır pencere bölmesini açmak için bir eylem seçin.

5. Açılır bölmede bilgileri gözden geçirin ve aşağıdaki adımlardan birini uygulayın:

   - Araştırma hakkında daha fazla ayrıntı görüntülemek için **Araştırma sayfasını aç'ı** seçin.
   - Bekleyen bir eylem başlatmak için **Onayla'yı** seçin.
   - Bekleyen bir eylemin gerçekleştirilmesini önlemek için **Reddet'i** seçin.
   - [Gelişmiş avcılığa](advanced-hunting-overview.md) gitmek için **Avlanmaya git'i** seçin.

## <a name="review-completed-actions"></a>Tamamlanan eylemleri gözden geçirme

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalına</a> gidin ve oturum açın.

2. Gezinti bölmesinde **İşlem merkezi'ni** seçin.

3. **Geçmiş** sekmesindeki öğeleri gözden geçirin.

4. Bu düzeltme eylemi hakkında daha fazla ayrıntı görüntülemek için bir öğe seçin.

## <a name="undo-completed-actions"></a>Tamamlanan eylemleri geri alma

Bir cihazın veya dosyanın bir tehdit olmadığını belirlediyseniz, bu eylemlerin otomatik olarak veya el ile gerçekleştirilip gerçekleştirilmediğine bakılmaksızın, gerçekleştirilen düzeltme eylemlerini geri alabilirsiniz. İşlem merkezindeki **Geçmiş** sekmesinde aşağıdaki eylemlerden herhangi birini geri alabilirsiniz:

|Eylem kaynağı|Desteklenen Eylemler|
|---|---|
|<ul><li>Otomatik araştırma</li><li>El ile yanıt eylemleri (aşağıdaki nota bakın)</li><li>Microsoft Defender Virüsten Koruma</li></ul>|<ul><li>Sürücüyü devre dışı bırakma</li><li>Cihazı yalıtma</li><li>Dosyayı karantinaya al</li><li>Kayıt defteri anahtarını kaldırma</li><li>Zamanlanmış görevi kaldırma</li><li>Kod yürütmeyi kısıtlama</li><li>Hizmeti durdurma</li></ul>|

> [!NOTE]
> [Uç Nokta Planı 1](defender-endpoint-plan-1.md) ve [İş için Microsoft Defender](../defender-business/mdb-overview.md) için Defender yalnızca aşağıdaki el ile yanıt eylemlerini içerir:
>
> - Antivirüs taraması başlat
> - Cihazı yalıtma
> - Dosyayı durdurma ve karantinaya al
> - Bir dosyayı engellemek veya dosyaya izin vermek için gösterge ekleme
>
> Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender planlarını karşılaştırma](defender-endpoint-plan-1-2.md) ve [Küçük ve orta ölçekli işletmeler için Microsoft 365 planlarında güvenlik özelliklerini karşılaştırma](../defender-business/compare-mdb-m365-plans.md).

### <a name="to-undo-multiple-actions-at-one-time"></a>Aynı anda birden çok eylemi geri almak için

1. İşlem merkezine ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) gidin ve oturum açın.

2. **Geçmiş** sekmesinde, geri almak istediğiniz eylemleri seçin. Aynı Eylem türüne sahip öğeleri seçtiğinizden emin olun. Açılır pencere bölmesi açılır.

3. Açılır bölmede **Geri Al'ı** seçin.

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Bir dosyayı birden çok cihazda karantinadan kaldırmak için

1. İşlem merkezine ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) gidin ve oturum açın.

2. **Geçmiş** sekmesinde, Eylem türü **Karantina dosyası** olan bir öğe seçin.

3. Açılır bölmede **Bu dosyanın X daha fazla örneğine uygula'yı** ve ardından **Geri Al'ı** seçin.

## <a name="automation-levels-automated-investigation-results-and-resulting-actions"></a>Otomasyon düzeyleri, otomatik araştırma sonuçları ve sonuçta elde edilen eylemler

Otomasyon düzeyleri, belirli düzeltme eylemlerinin otomatik olarak mı yoksa yalnızca onay üzerine mi gerçekleştirildiğini etkiler. Bazen güvenlik operasyonları ekibinizin otomatik araştırmanın sonuçlarına bağlı olarak atılması gereken daha fazla adım vardır. Aşağıdaki tabloda otomasyon düzeyleri, otomatik araştırma sonuçları ve her durumda yapılması gerekenler özetlenmektedir.

|Cihaz grubu ayarı|Otomatik araştırma sonuçları|Yapılması gerekenler|
|---|---|---|
|**Tam - tehditleri otomatik olarak düzeltme**<br/>(önerilir)|Bir kanıt parçası için *Kötü Amaçlı* kararına ulaşıldı. <p> Uygun düzeltme eylemleri otomatik olarak gerçekleştirilen.|[Tamamlanan eylemleri gözden geçirme](#review-completed-actions)|
|**Tam - tehditleri otomatik olarak düzeltme**|Bir kanıt için *Şüpheli* kararına ulaşıldı. <p> Düzeltme eylemleri devam etmek için onay bekliyor.|[Bekleyen eylemleri onaylama (veya reddetme)](#review-pending-actions)|
|**Yarı - herhangi bir düzeltme için onay gerektir**|Bir kanıt parçası için *Kötü Amaçlı* veya *Şüpheli* kararına ulaşılır. <p> Düzeltme eylemleri devam etmek için onay bekliyor.|[Bekleyen eylemleri onaylama (veya reddetme)](#review-pending-actions)|
|**Yarı - çekirdek klasörlerin düzeltilmesi için onay gerektir**|Bir kanıt parçası için *Kötü Amaçlı* kararına ulaşıldı. <p> Yapıt bir dosya veya yürütülebilir dosyaysa ve Windows klasörü veya Program dosyaları klasörü gibi bir işletim sistemi dizinindeyse, düzeltme eylemleri onay bekliyor demektir. <p> Yapıt bir işletim sistemi dizininde *değilse* , düzeltme eylemleri otomatik olarak gerçekleştirilen işlemlerdir.|<ol><li>[Bekleyen eylemleri onaylama (veya reddetme)](#review-pending-actions)</li><li>[Tamamlanan eylemleri gözden geçirme](#review-completed-actions)</li></ol>|
|**Yarı - çekirdek klasörlerin düzeltilmesi için onay gerektir**|Bir kanıt için *Şüpheli* kararına ulaşıldı. <p> Düzeltme eylemleri onay bekliyor.|[Bekleyen eylemleri onaylayın (veya reddedin](#review-pending-actions)).|
|**Yarı - geçici olmayan klasörlerin düzeltilmesi için onay gerektir**|Bir kanıt parçası için *Kötü Amaçlı* kararına ulaşıldı. <p> Yapıt, kullanıcının indirmeleri klasörü veya geçici klasörü gibi geçici bir klasörde olmayan bir dosya veya yürütülebilir dosyaysa, düzeltme eylemleri onay bekliyor demektir. <p> Yapıt geçici bir *klasörde bulunan bir* dosya veya yürütülebilir dosyaysa, düzeltme eylemleri otomatik olarak gerçekleştirilen işlemlerdir.|<ol><li>[Bekleyen eylemleri onaylama (veya reddetme)](#review-pending-actions)</li><li>[Tamamlanan eylemleri gözden geçirme](#review-completed-actions)</li></ol>|
|**Yarı - geçici olmayan klasörlerin düzeltilmesi için onay gerektir**|Bir kanıt için *Şüpheli* kararına ulaşıldı. <p> Düzeltme eylemleri onay bekliyor.|[Bekleyen eylemleri onaylama (veya reddetme)](#review-pending-actions)|
|**Tam** veya **Yarı** otomasyon düzeylerinden herhangi biri|Bir kanıt için *Tehdit bulunamadı* kararına ulaşıldı. <p> Hiçbir düzeltme eylemi yapılmaz ve onay bekleyen eylem yoktur.|[Otomatik soruşturmaların ayrıntılarını ve sonuçlarını görüntüleyin](/microsoft-365/security/defender-endpoint/auto-investigation-action-center)|
|**Otomatik yanıt yok** (önerilmez)|Hiçbir otomatik araştırma çalıştırılır, bu nedenle hiçbir karara ulaşılır ve hiçbir düzeltme eylemi yapılmaz veya onay beklenmez.|[**Tam** veya **Yarı** otomasyonu kullanmak için cihaz gruplarınızı ayarlamayı veya değiştirmeyi göz önünde bulundurun](/microsoft-365/security/defender-endpoint/machine-groups)|

Tüm hükümler [İşlem merkezinde](auto-investigation-action-center.md#the-unified-action-center) izlenir.

> [!NOTE]
> [İş için Defender'da](../defender-business/mdb-overview.md) otomatik araştırma ve düzeltme özellikleri **, Tehditleri otomatik olarak düzeltmek için Tam olarak** kullanılır. Bu özellikler varsayılan olarak tüm cihazlara uygulanır.

## <a name="next-steps"></a>Sonraki adımlar

- [Canlı yanıt özellikleri hakkında bilgi edinin](live-response.md)
- [Gelişmiş avcılık ile tehditleri proaktif olarak avlama](advanced-hunting-overview.md)
- [Uç Nokta için Microsoft Defender'da yanlış pozitifleri/negatifleri ele alın](defender-endpoint-false-positives-negatives.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik araştırmalara genel bakış](automated-investigations.md)
