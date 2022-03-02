---
title: Uç Nokta Cihazları için Defender listesinde cihazları araştırma
description: Uyarıları, ağ bağlantısı bilgilerini gözden geçirerek, cihaz etiketleri ve grupları ekleyerek ve hizmet durumunu gözden geçirerek etkilenen cihazları araştırabilirsiniz.
keywords: cihazlar, etiketler, gruplar, uç nokta, uyarılar sırası, uyarılar, cihaz adı, etki alanı, son görülen, iç IP, etkin uyarılar, tehdit kategorisi, filtre, sıralama, uyarıları gözden geçirme, ağ, bağlantı, tür, parola çalmak, fidye yazılımı, açık, tehdit, düşük önem düzeyi, hizmet durumu
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: dee6cec53ef6a3412d110837037f1de48fc6e92f
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011827"
---
# <a name="investigate-devices-in-the-microsoft-defender-for-endpoint-devices-list"></a>Uç Nokta Cihazları için Microsoft Defender listesinde cihazları araştırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatemachines-abovefoldlink)

Uyarıyla veya ihlalin olası kapsamıyla ilgili olabileceği diğer davranışları veya olayları tanımlamak için, belirli bir cihazda yükseltilmiş uyarının ayrıntılarını araştırabilirsiniz.

> [!NOTE]
> Araştırma veya yanıt işleminin bir parçası olarak, bir cihazdan araştırma paketi toplayabilirsiniz. Şöyle: Araştırma paketini [cihazlardan toplayın](/microsoft-365/security/defender-endpoint/respond-machine-alerts#collect-investigation-package-from-devices).

Etkilenen cihazları portalda her gördüğünüzde bu cihaz hakkında ayrıntılı bir rapor açabilirsiniz. Etkilenen cihazlar aşağıdaki alanlarda tanımlanır:

- [Cihazlar listesi](investigate-machines.md)
- [Uyarılar sırası](alerts-queue.md)
- [Güvenlik işlemleri panosu](security-operations-dashboard.md)
- Tek tek herhangi bir uyarı
- Tek tek dosya ayrıntıları görünümü
- Herhangi bir IP adresi veya etki alanı ayrıntıları görünümü

Belirli bir cihazı araştırsanız, şunları görmeye devam edin:

- Cihaz ayrıntıları
- Yanıt eylemleri
- Sekmeler (genel bakış, uyarılar, zaman çizelgesi, güvenlik önerileri, yazılım envanteri, güvenlik açıkları keşfetildi, eksik KB'ler)
- Kartlar (etkin uyarılar, oturum açmış kullanıcılar, güvenlik değerlendirmesi)

![Cihaz görünümünün resmi.](images/specific-device.png)

> [!NOTE]
> Ürün sınırlandırma nedeniyle, cihaz profili 'Son Görülme' zaman çerçevesini belirlerken (cihaz sayfasında da görülür) siber kanıtı göz önünde bulundurm olmaz.
> Örneğin, makine zaman çizelgesinde daha yeni uyarılar veya veriler mevcut olsa bile, Cihaz sayfasındaki 'Son görülen' değeri daha eski bir zaman dilimi gösterebilir.

## <a name="device-details"></a>Cihaz ayrıntıları

Cihaz ayrıntıları bölümünde, cihazın etki alanı, işletim sistemi ve sistem durumu gibi bilgiler yer almaktadır. Cihazda bir soruşturma paketi varsa, paketi indirmeye izin veren bir bağlantıyla karşıdan yüklemesi gerekir.

## <a name="response-actions"></a>Yanıt eylemleri

Yanıt eylemleri belirli bir cihaz sayfasının en üstünde görüntülenir ve şunları içerir:

- Etiketleri yönetme
- Cihazı yalıt
- Uygulama yürütmeyi kısıtla
- Virüsten koruma taraması çalıştırma
- Soruşturma paketini topla
- Canlı Yanıt Oturumunu Başlatma
- Otomatik araştırma başlatma
- Tehdit uzmanına danışın
- İşlem merkezi

İşlem merkezinde, belirli bir cihaz sayfasında veya belirli bir dosya sayfasında yanıt eylemleri gerçekleştirebilirsiniz.

Cihazda nasıl işlem yapmakla ilgili daha fazla bilgi için bkz [. Cihazda yanıt eylemi alma](respond-machine-alerts.md).

Daha fazla bilgi için bkz [. Kullanıcı varlıklarını araştırma](investigate-user.md).

## <a name="tabs"></a>Sekmeler

Sekmeler cihazla ilgili ilgili güvenlik ve tehdit önleme bilgilerini sağlar. Her sekmede, sütun başlıklarının üstündeki çubukta Sütunları **özelleştir'i** seçerek gösterilen sütunları özelleştirebilirsiniz.

### <a name="overview"></a>Genel bakış

Genel **Bakış** sekmesi etkin [uyarılar,](#cards) oturum açmış kullanıcılar ve güvenlik değerlendirmesi için kartları görüntüler.

![Cihaz sayfasındaki genel bakış sekmesinin görüntüsü.](images/overview-device.png)

### <a name="alerts"></a>Uyarılar

Uyarılar **sekmesi** cihazla ilişkilendirilmiş uyarıların listesini sağlar. Bu liste, Uyarılar kuyruğun filtrelenmiş bir [](alerts-queue.md)sürümüdür ve uyarı, önem düzeyi (yüksek, orta, düşük, bilgilendirme amaçlı), sırada durumu (yeni, sürüyor, çözümlendi), sınıflandırma (ayarlanmaz, yanlış uyarı, doğru uyarı), araştırma durumu, uyarı kategorisi, uyarının adresi olan kişi ve son etkinlik hakkında kısa bir açıklama gösterir. Uyarıları filtrelemek de gerekir.

![Cihazla ilgili uyarıların resmi.](images/alerts-device.png)

Uyarının sol köşesindeki daire simgesi seçiliyken bir açılır simge görüntülenir. Bu panelden uyarıyı yönetebilir ve olay numarası ve ilgili cihazlar gibi diğer ayrıntıları görüntüleyebilirsiniz. Aynı anda birden çok uyarı seçilebilir.

Olay grafiği ve işlem ağacı da içinde olmak üzere uyarının tam sayfa görünümünü görmek için uyarının başlığını seçin.

### <a name="timeline"></a>Zaman çizelgesi

Zaman **Çizelgesi** sekmesi, cihazda gözlemlenen olayların ve ilişkili uyarıların kronolojik görünümünü sağlar. Bu, tüm olayları, dosyaları ve IP adreslerini cihaza göre birbiriyle bağıntıya neden olabilir.

Zaman çizelgesi, ayrıca, verilen bir süre içinde  meydana gelen olayları seçerek detaya gitmelerine olanak sağlar. Seçilen bir zaman süresi boyunca bir cihazda  meydana gelen olayların zaman sırasını görüntüebilirsiniz. Görünümlerinizi daha fazla kontrol etmek için, olay gruplarına göre filtre uygulama veya sütunları özelleştirme.

> [!NOTE]
> Güvenlik duvarı olaylarının görüntülensi için denetim ilkesi etkinleştirmeniz gerekir. Bkz. [Denetim Filtreleme Platformu bağlantısı](/windows/security/threat-protection/auditing/audit-filtering-platform-connection).
>
> Güvenlik duvarı aşağıdaki olayları kapsar:
>
> - [5025](/windows/security/threat-protection/auditing/event-5025) - güvenlik duvarı hizmeti durduruldu
> - [5031](/windows/security/threat-protection/auditing/event-5031) - uygulamanın ağ üzerinden gelen bağlantıları kabulsi engellendi
> - [5157](/windows/security/threat-protection/auditing/event-5157) - engellenen bağlantı

![Olaylı cihaz zaman çizelgesinin resmi.](images/timeline-device.png)

İşlevlerin bazıları şunları içerir:

- Belirli olayları arama
  - Belirli zaman çizelgesi olaylarını aramak için arama çubuğunu kullanın.
- Belirli bir tarihten itibaren olayları filtreleme
  - Tablonun sol üst kısmında takvim simgesini seçerek geçmiş gün, hafta, 30 gün veya özel aralıkta etkinlikleri görüntüleniyor. Varsayılan olarak, cihaz zaman çizelgesi son 30 gün içinde olan olayları görüntülemek için ayarlanmıştır.
  - Bölümü vurgulayıp belirli bir ana atlamak için zaman çizelgesini kullanın. Zaman çizelgesinde otomatik soruşturmalar için oklar
- Ayrıntılı cihaz zaman çizelgesi olaylarını dışarı aktarma
  - Geçerli tarih veya belirtilen tarih aralığı için cihaz zaman çizelgesini yedi gün kadar dışarı aktarın.

Bazı olaylar hakkında daha fazla ayrıntı, Ek **bilgiler bölümünde** sağlanır. Bu ayrıntılar, olayın türüne bağlı olarak değişir; örneğin:

- Application Guard tarafından bulunan - web tarayıcısı olayı yalıtılmış bir kapsayıcıyla kısıtlandı
- Etkin tehdit algılandı - Tehdit çalışırken tehdit algılaması meydana geldi
- Düzeltme başarısız - algılanan tehdide düzeltme girişimi başlatıldı ancak başarısız oldu
- Düzeltme başarılı- algılanan tehdit durduruldu ve temizlendi
- Uyarı kullanıcı tarafından atlandı - Windows Defender SmartScreen uyarısı kullanıcı tarafından yok sayıldı ve geçersiz kılındı
- Şüpheli betik algılandı - kötü amaçlı olabilecek bir betiği çalışıyor olarak bulundu
- Uyarı kategorisi - olay bir uyarının yeniltirine yol açtı ise uyarı kategorisi ("örneğin, Lateral Movement" sağlanır)

#### <a name="event-details"></a>Olay ayrıntıları

Bir etkinlikle ilgili ayrıntıları görüntülemek için o etkinliği seçin. Genel etkinlik bilgilerini göstermek için bir panel görüntülenir. Uygun olduğunda ve veriler kullanılabilir olduğunda, ilgili varlıkları ve bunların ilişkilerini gösteren bir grafik de gösterilir.

Etkinlik ve ilgili etkinlikleri daha ayrıntılı incelemek için, ilgili etkinlikler için Tekin'i [seçerek](advanced-hunting-overview.md) hızla gelişmiş bir av **sorgusu çalıştırabilirsiniz**. Sorgu seçili olayı ve aynı uç noktada aynı zamanda 44 saat içinde  meydana gelen diğer olayların listesini geri döner.

![Olay ayrıntıları panelinin resmi.](images/event-details.png)

### <a name="security-recommendations"></a>Güvenlik önerileri

**Güvenlik önerileri,** Uç Nokta Tehdit Veya Güvenlik Açığı Yönetimi özelliği & Için Microsoft [Defender'dan](tvm-dashboard-insights.md) oluşturulur. Öneriyi seçerek, önerinin açıklaması ve üzerine alınmayacak riskler gibi ilgili ayrıntıları görüntüleyebilirsiniz. Ayrıntılar [için güvenlik önerisine](tvm-security-recommendation.md) bakın.

![Güvenlik önerileri sekmesinin resmi.](images/security-recommendations-device.png)

### <a name="software-inventory"></a>Yazılım envanteri

Yazılım **envanteri** sekmesi, yazılımlarla birlikte cihazda her türlü zayıflığı veya tehdityi de görüntülemenizi sağlar. Yazılımın adını seçmek, sizi güvenlik önerilerini, güvenlik açıklarını, yüklü cihazları ve sürüm dağıtımını görüntüleyebilirsiniz yazılım ayrıntıları sayfasına götürebilirsiniz. Ayrıntılar [için bkz.](tvm-software-inventory.md) Yazılım envanteri

![Yazılım envanteri sekmesinin resmi.](images/software-inventory-device.png)

### <a name="discovered-vulnerabilities"></a>Bulunan güvenlik açıkları

Bulunan **güvenlik açıkları** sekmesi, cihazla ilgili bulunan güvenlik açıklarının adını, önem derecesine ve tehdit öngörülerini gösterir. Belirli güvenlik açıklarını seçmek bir açıklama ve ayrıntılar gösterir.

![Bulunan güvenlik açıkları sekmesinin resmi.](images/discovered-vulnerabilities-device.png)

### <a name="missing-kbs"></a>Eksik KB'ler
Eksik **KBs sekmesi** , cihaz için eksik güvenlik güncelleştirmelerini listeler.

![Eksik kbs sekmesinin resmi.](images/missing-kbs-device.png)

## <a name="cards"></a>Kartlar

### <a name="active-alerts"></a>Etkin uyarılar

**Azure Gelişmiş Tehdit Koruması** kartı, Kimlik için Microsoft Defender özelliğini etkinleştirdiyseniz ve varsa cihazla ve risk düzeyiyle ilgili uyarılar için üst düzey bir genel bakış görüntüler. Daha fazla bilgiyi "Uyarılar" detaya gitme sayfalarından edinebilirsiniz.

![Etkin uyarılar kartının resmi.](images/risk-level-small.png)

> [!NOTE]
> Bu özelliği kullanmak için hem Kimlik için Microsoft Defender hem de Uç Nokta için Defender ile tümleştirmeyi etkinleştirmeniz gerekir. Uç Nokta için Defender'da, gelişmiş özelliklerde bu özelliği etkinleştirebilirsiniz. Gelişmiş özellikleri etkinleştirme hakkında daha fazla bilgi için bkz [. Gelişmiş özellikleri açma](advanced-features.md).

### <a name="logged-on-users"></a>Oturum açmış kullanıcılar

Oturum **açan kullanıcılar kartı** , son 30 gün içinde kaç kullanıcının oturum açtığını ve en sık kullanan kullanıcıları gösterir. "Tüm kullanıcıları göster" bağlantısının seçkisi, kullanıcı türü, oturum açma türü ve kullanıcının ilk ve son görülme zamanları gibi bilgilerin görüntü olduğu ayrıntılar bölmesini açar. Daha fazla bilgi için bkz [. Kullanıcı varlıklarını araştırma](investigate-user.md).

![Kullanıcı ayrıntıları bölmesinin resmi.](images/logged-on-users.png)

> [!NOTE]
> 'En sık' kullanıcı değeri yalnızca etkileşimli olarak oturum açan kullanıcıların kanıtlarına dayalı olarak hesaplanır.
> Bununla birlikte, "Tüm kullanıcılar" yan bölme her tür kullanıcı oturum açmasını hesaplar, bu nedenle bu kullanıcıların etkileşimli olmadığının var olduğu için yan bölmede daha sık kullanıcı görmeleri beklir.

### <a name="security-assessments"></a>Güvenlik değerlendirmeleri

Güvenlik **değerlendirmeleri kartı** genel açık düzeyini, güvenlik önerilerini, yüklü yazılımı ve güvenlik açıklarını gösterir. Bir cihazın etkilenme düzeyi, bekleyen güvenlik önerilerinin kümülatif etkisiyle belirlenir.

![Güvenlik değerlendirme kartının görüntüsü.](images/security-assessments.png)

## <a name="related-topics"></a>İlgili konular

- [Uç Nokta Uyarıları kuyruğu için Microsoft Defender'ı görüntüleme ve düzenleme](alerts-queue.md)
- [Uç nokta uyarıları için Microsoft Defender'ı yönetme](manage-alerts.md)
- [Uç nokta uyarıları için Microsoft Defender'ı araştırma](investigate-alerts.md)
- [Uç Nokta için Defender uyarısıyla ilişkilendirilmiş dosyayı araştırma](investigate-files.md)
- [Uç Nokta için Defender uyarısıyla ilişkilendirilmiş IP adresini araştırma](investigate-ip.md)
- [Uç nokta için Defender uyarısıyla ilişkilendirilmiş etki alanını araştırma](investigate-domain.md)
- [Uç Nokta için Defender'da kullanıcı hesabını araştırma](investigate-user.md)
- [Güvenlik önerisi](tvm-security-recommendation.md)
- [Yazılım envanteri](tvm-software-inventory.md)