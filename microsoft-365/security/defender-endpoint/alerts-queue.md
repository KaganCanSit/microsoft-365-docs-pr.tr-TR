---
title: Uç Nokta Uyarıları kuyruğu için Microsoft Defender'ı görüntüleme ve düzenleme
description: Uç nokta uyarıları için Microsoft Defender sıralarının nasıl çalışır ve uyarı listelerinin nasıl sıralanmış ve filtrelenmiş olduğunu öğrenin.
keywords: uyarılar, kuyruklar, uyarılar sırası, sıralama, sıralama, sıralama, filtreleme, uyarıları yönetme, yeni, sürüyor, çözümlendi, en yeni, sırada saat, önem derecesi, zaman dönemi, Microsoft tehdit uzmanları uyarıları
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
ms.date: 03/27/2020
ms.technology: mde
ms.openlocfilehash: b4606eb25f2cea9c18db8c13beba0e107d0e7950
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62974106"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-alerts-queue"></a>Uç Nokta Uyarıları kuyruğu için Microsoft Defender'ı görüntüleme ve düzenleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-alertsq-abovefoldlink)

Uyarılar **sırası,** ağ bağlantısına sahip cihazlardan bayrakla işaretlenmiş uyarıların listesini gösterir. Varsayılan olarak, kuyruk, gruplandı görünümünde son 30 gün içinde görülen uyarıları görüntüler. En son uyarılar listenin en üstünde, en son uyarıları en başta görme konusunda yardımcı olmak için gösteriler.

> [!NOTE]
> Uyarılar kuyruğu, otomatik araştırma ve düzeltme ile önemli ölçüde azaltıldı ve güvenlik işlem uzmanlarının daha gelişmiş tehditlere ve diğer yüksek değerli girişimlere odaklanmasına olanak sağlar. Bir uyarı, desteklenen bir işletim sistemi olan bir cihazda otomatik soruşturma (örneğin bir dosya) için desteklenen bir varlık içerdiğinde, otomatik bir araştırma ve düzeltme başlatabilirsiniz. Otomatik soruşturmalar hakkında daha fazla bilgi için bkz. [Otomatik soruşturmalara genel bakış](automated-investigations.md).

Uyarılar sırası görünümünü özelleştirmek için seçebileceğiniz çeşitli seçenekler vardır.

Üst gezintiden şunlarıabilirsiniz:

- Gruplamış görünümü veya liste görünümünü seçme
- Sütunları eklemek veya kaldırmak için sütunları özelleştirme
- Sayfa başına gösterecek öğeleri seçme
- Sayfalar arasında gezinme
- Filtre uygulama

![Uyarılar kuyruğu resmi.](images/alerts-queue-list.png)

## <a name="sort-filter-and-group-the-alerts-queue"></a>Uyarılar kuyruğuna göre sıralama, filtreleme ve grupla

Uyarı listesini sınırlandırarak ve uyarıları daha odaklanmış bir görünüme sahip olmak için aşağıdaki filtreleri uygulayabilirsiniz.

### <a name="severity"></a>Önem Derecesi

Önem derecesine dikkat|Açıklama
---|---
Yüksek <br> (Red)|Yaygın olarak gelişmiş kalıcı tehditlerle (APT) ilişkili uyarılar. Bu uyarılar, cihazlara zarar veren önem derecesine bağlı olarak yüksek bir risk olduğunu belirtmektedir. Bazı örnekler: kimlik bilgileri hırsızlığı araçları etkinlikleri, fidye yazılımı etkinlikleri, herhangi bir grupla ilişkili olmayan fidye yazılımı etkinlikleri, güvenlik algılayıcıları ile oynanıyor veya insan maceracıyı gösteren kötü amaçlı etkinlikler.
Orta <br> (Orange)|Gelişmiş kalıcı uç noktada algılama ve yanıtlama (APT) parçası olabileceği ihlal sonrası davranışlarda uyarılarda. Bu, tipik saldırı aşamaları, anormal kayıt defteri değişikliği, şüpheli dosyaların yürütülmesi ve benzeri gözlemlenen davranışları içerir. Bazıları iç güvenlik testinin bir parçası olsa da bunun da gelişmiş bir saldırı olabileceği için araştırma gerektiriyor.
Düşük <br> (Sarı)|Yaygın kötü amaçlı yazılımla ilişkilendirilmiş tehditlere karşı uyarılar. Örneğin, bilgi arama komutları, günlükleri temizleme gibi kötü amaçlı olmayan ve genellikle kuruluşu hedef alan gelişmiş bir tehdide işaretyen hack araçları. Ayrıca, kuruluşta bir kullanıcı tarafından yalıtılmış bir güvenlik aracı testinden de gelebilir.
Bilgilendirme <br> (Gri)|Ağa zararlı kabul edilen uyarılar; ancak olası güvenlik sorunlarına karşı kurumsal güvenlik farkındalığını ortayatabilirsiniz.

#### <a name="understanding-alert-severity"></a>Uyarı önem derecelerini anlama

Microsoft Defender Virüsten Koruma (Microsoft Defender AV) ve Uç nokta uyarısı için Defender farklı kapsamları temsil edecek şekilde farklıdır.

Tehdit Microsoft Defender Virüsten Koruma düzeyi, algılanan tehdidin (kötü amaçlı yazılım) mutlak önem derecesine sahiptir ve virüs bulaşmışsa tek bir cihaza yönelik olası risklere bağlı olarak atanır.

Uç Nokta uyarısı önem düzeyi için Defender, algılanan davranışın önem derecesini, cihaz için gerçek riski ancak daha da önemlisi kuruluş için olası riski temsil eder.

Bu nedenle, örneğin:

- Bir Microsoft Defender Virüsten Koruma hakkında Uç Nokta için Defender uyarısının önem derecesi, cihaza tamamen engel olan ve bu şekilde etkilenmemiş bir tehdit algıladı, çünkü gerçek bir hasar yoktu.
- Yürütürken ticari kötü amaçlı yazılımla ilgili bir uyarı algılandı, ancak Microsoft Defender AV tarafından engellendi ve düzeltildi, çünkü bu uyarı cihaza biraz zarar verdiği için "Düşük" olarak kategorilere ayrılmıştır ancak kurumsal bir tehdit oluşturmaz.
- Yürütürken algılanan kötü amaçlı yazılım uyarısı tek bir cihaz için değil, daha sonra engellenmiş olup olmadığını bakılmaksızın kuruluş için değil, "Orta" veya "Yüksek" olarak derece edilebilir.
- Engellenmedi veya düzelti olmayan şüpheli davranış uyarıları, aynı kurumsal tehdit dikkate alınmasına göre "Düşük", "Orta" veya "Yüksek" olarak derecelenir.

#### <a name="understanding-alert-categories"></a>Uyarı kategorilerini anlama

MITRE ATT&CK matrisinde kurumsal saldırı taktiklerini hizalamak [](https://attack.mitre.org/tactics/enterprise/) [için uyarı kategorilerini yeniden tanımladık](https://attack.mitre.org/). Yeni kategori adları tüm yeni uyarılara uygulanır. Var olan uyarılar önceki kategori adlarını gizli tutacak.

Aşağıdaki tabloda geçerli kategoriler ve bunların genel olarak önceki kategorilere nasıl eşli olduğu listelenmiştir.

|Yeni kategori|API kategori adı|Algılanan tehdit etkinliği veya bileşeni|
|---|---|---|
|Koleksiyon|Koleksiyon|Filtreleme için verileri bulma ve toplama.|
|Komut ve denetim|CommandAndControl|Veri geçişi yapmak veya komutları almak için saldırgan denetimli ağ altyapısına bağlanma.|
|Kimlik bilgileri erişimi|CredentialAccess|Ağ'daki cihazlar ve diğer kaynaklar üzerinde denetimi genişletmek için geçerli kimlik bilgileri alma.|
|Savunmayı kaçırma|DefenseEvasion|Örneğin güvenlik uygulamalarını kapatarak, aramaların silinmesini ve kök setleri çalıştırarak güvenlik denetimlerini önlemek.|
|Keşif|Keşif|Yönetici bilgisayarlar, etki alanı denetleyicileri ve dosya sunucuları gibi önemli cihazlar ve kaynaklar hakkında bilgi toplama.|
|Yürütme|Yürütme|RA'lar ve arka kullanıcılar da dahil olmak üzere saldırgan araçlarını ve kötü amaçlı kodu başlatma.|
|Exfiltration|Exfiltration|Ağdan, saldırgan tarafından denetlenen bir konuma veri ayıklanıyor.|
|Exploit|Exploit|Exploit code and possible exploitation activity.|
|İlk erişim|InitialAccess|Hedef ağa ilk giriş elde etmek, genellikle parola tahminleri, açıkları açıkları veya kimlik avı e-postaları ile olur.|
|Lateral movement|LateralMovement|Kritik kaynaklara ulaşmak veya ağ kalıcılığı kazanmak için hedef ağ içerisinde cihazlar arasında geçiş.|
|Kötü amaçlı yazılım|Kötü amaçlı yazılım|Backdoors, truva atı ve diğer kötü amaçlı kod türleri.|
|Kalıcılık|Kalıcılık|Etkin kalmak ve sistem yeniden başlatmalarını sağ kalmak için otomatik başlangıç genişletilebilirlik noktaları (ASEP) oluşturma.|
|Ayrıcalık yükseltme|Ayrıcalıklar Çıkartması|Ayrıcalıklı bir işlem veya hesap bağlamında kodu çalıştırarak daha yüksek izin düzeyleri elde etmek.|
|Fidye yazılımı|Fidye yazılımı|Dosyaları şifre eden ve erişimi geri yüklemek için ödemesi yapılan kötü amaçlı yazılım.|
|Şüpheli etkinlik|SuspiciousActivity|Kötü amaçlı yazılım etkinliği veya bir saldırının parçası olabilir ya da atipik etkinlik.|
|İstenmeyen yazılım|UnwantedSoftware|Üretkenliği ve kullanıcı deneyimini etkileyen düşük itibarlı uygulamalar ve uygulamalar; istenmeyen uygulamalar (PUA) olarak algılandı.|

### <a name="status"></a>Durum

Uyarı listesini durumlarına göre sınırlandırabilirsiniz.

### <a name="investigation-state"></a>İnceleme durumu

Otomatik araştırma durumuna karşılık gelen durum.

### <a name="category"></a>Kategori

Belirli türde kötü amaçlı etkinlikleri görüntülemek için sıraya filtre uygulamayı seçebilirsiniz.

### <a name="assigned-to"></a>Atanan

Size atanmış uyarıları göstermeyi veya otomasyonu seçebilirsiniz.

### <a name="detection-source"></a>Algılama kaynağı

Uyarı algılamayı tetikleyen kaynağı seçin. Microsoft Tehdit Uzmanları önizleme katılımcıları artık tehdit uzmanları tarafından yönetilen yeni arama hizmetinin algılamalarını filtreley ve görebilir.

> [!NOTE]
> Virüsten Koruma filtresi yalnızca cihazlar yazılımdan koruma Microsoft Defender Virüsten Koruma varsayılan gerçek zamanlı koruma ürünü olarak Yazılım'ı kullanıyorsa görüntülenir.

|Algılama kaynağı|API değeri|
|---|---|
|3. taraf algılayıcılar|ThirdPartySensors|
|Virüsten koruma|WindowsDefenderAv|
|Otomatik araştırma|AutomatedInvestigation|
|Özel algılama|CustomDetection|
|Özel TI|CustomerTI|
|EDR|WindowsDefenderAtp|
|Microsoft 365 Defender|MTP|
|Office 365 için Microsoft Defender|OfficeATP|
|Microsoft Tehdit Uzmanları|ThreatExperts|
|SmartScreen|WindowsDefender SmartScreen|

### <a name="os-platform"></a>işletim sistemi platformu

Araştırırken ilgilendiğin işletim sistemi platformunu seçerek uyarılar kuyruğu görünümünü sınırlandırabilirsiniz.

### <a name="device-group"></a>Cihaz grubu

Denetlenen belirli cihaz gruplarınız varsa, uyarıların kuyruğu görünümünü sınırlamak için grupları seçin.

### <a name="associated-threat"></a>İlişkili tehdit

Bu filtreyi kullanarak yüksek profil tehditleri ile ilgili uyarılara odaklanın. Tehdit analizinde yüksek profilli tehditlerin tam [listesini görüyoruz](threat-analytics.md).

## <a name="related-topics"></a>İlgili konular

- [Uç nokta uyarıları için Microsoft Defender'ı yönetme](manage-alerts.md)
- [Uç nokta uyarıları için Microsoft Defender'ı araştırma](investigate-alerts.md)
- [Uç nokta için Microsoft Defender uyarısıyla ilişkilendirilmiş dosyayı araştırma](investigate-files.md)
- [Uç Nokta Cihazları için Microsoft Defender listesinde cihazları araştırma](investigate-machines.md)
- [Uç nokta için Microsoft Defender uyarısıyla ilişkilendirilmiş IP adresini araştırma](investigate-ip.md)
- [Uç nokta için Microsoft Defender uyarısıyla ilişkilendirilmiş etki alanını araştırma](investigate-domain.md)
- [Uç Nokta için Microsoft Defender'da kullanıcı hesabını araştırma](investigate-user.md)
