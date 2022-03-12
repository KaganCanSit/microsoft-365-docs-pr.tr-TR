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
ms.openlocfilehash: 63107c50c081eef65e0a56417845b470cc0a294a
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63449738"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-alerts-queue"></a>Uç Nokta Uyarıları kuyruğu için Microsoft Defender'ı görüntüleme ve düzenleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-alertsq-abovefoldlink)

Uyarılar **,** ağ bağlantısı olan cihazlardan bayrakla işaretlenmiş uyarıların listesini gösterir. En son uyarılar listenin en üstünde, en son uyarıları en başta görme konusunda yardımcı olmak için gösteriler.

> [!NOTE]
> Otomatik araştırma ve düzeltme sayesinde uyarılar önemli ölçüde azaltıldı ve güvenlik işlemi uzmanlarının daha gelişmiş tehditlere ve diğer yüksek değerli girişimlere odaklanmasına olanaklandı. Bir uyarı, desteklenen bir işletim sistemi olan bir cihazda otomatik soruşturma (örneğin bir dosya) için desteklenen bir varlık içerdiğinde, otomatik bir araştırma ve düzeltme başlatabilirsiniz. Otomatik soruşturmalar hakkında daha fazla bilgi için bkz. [Otomatik soruşturmalara genel bakış](automated-investigations.md).

Uyarılar görünümünü özelleştirmek için seçebileceğiniz çeşitli seçenekler vardır.

Üst gezintiden şunlarıabilirsiniz:

- Sütunları eklemek veya kaldırmak için sütunları özelleştirme
- Filtre uygulama
- 1 Gün, 3 Gün, 1 Hafta, 30 Gün ve 6 Ay gibi belirli bir süre için uyarıları görüntüleme
- Uyarılar listesini Excel'e aktarma
- Uyarıları Yönetme

:::image type="content" source="images/alerts-filters.png" alt-text="Uyarı listesinin resmi" lightbox="images/alerts-filters.png":::

## <a name="sort-and-filter-alerts"></a>Uyarıları sıralama ve filtreleme 

Uyarı listesini sınırlandırarak ve uyarıların daha odaklanmış bir görünümünü elde etmek için aşağıdaki filtreleri uygulayabilirsiniz.

### <a name="severity"></a>Önem Derecesi

Uyarıları Önem Derecesi'ne göre filtreleysiniz.  

|Önem derecesine dikkat|Açıklama|
|---|---|
|Yüksek <br> (Red)|Yaygın olarak gelişmiş kalıcı tehditlerle (APT) ilişkili uyarılar. Bu uyarılar, cihazlara zarar veren önem derecesine bağlı olarak yüksek bir risk olduğunu belirtmektedir. Bazı örnekler: kimlik bilgileri hırsızlığı araçları etkinlikleri, fidye yazılımı etkinlikleri, herhangi bir grupla ilişkili olmayan fidye yazılımı etkinlikleri, güvenlik algılayıcıları ile oynanıyor veya insan maceracıyı gösteren kötü amaçlı etkinlikler.|
|Orta <br> (Orange)|Gelişmiş kalıcı uç noktada algılama ve yanıtlama (APT) bir parçası olabileceği ihlal sonrası davranışlarda uyarılarda. Bu, tipik saldırı aşamaları, anormal kayıt defteri değişikliği, şüpheli dosyaların yürütülmesi ve benzeri gözlemlenen davranışları içerir. Bazıları iç güvenlik testinin bir parçası olsa da bunun da gelişmiş bir saldırı olabileceği için araştırma gerektiriyor.|
|Düşük <br> (Sarı)|Yaygın kötü amaçlı yazılımla ilişkilendirilmiş tehditlere karşı uyarılar. Örneğin, bilgi arama komutları, günlükleri temizleme gibi kötü amaçlı olmayan ve genellikle kuruluşu hedef alan gelişmiş bir tehdide işaretyen hack araçları. Ayrıca, kuruluşta bir kullanıcı tarafından yalıtılmış bir güvenlik aracı testinden de gelebilir.|
|Bilgilendirme <br> (Gri)|Ağa zararlı kabul edilen uyarılar; ancak olası güvenlik sorunlarına karşı kurumsal güvenlik farkındalığını ortayatabilirsiniz.|

#### <a name="understanding-alert-severity"></a>Uyarı önem derecelerini anlama

Microsoft Defender Virüsten Koruma (Microsoft Defender AV) ve Uç nokta uyarısı için Defender ayrı ayrı olduğundan farklı kapsamları temsil bunlardır.

Tehdit Microsoft Defender Virüsten Koruma düzeyi, algılanan tehdidin (kötü amaçlı yazılım) mutlak önem derecesine sahiptir ve virüs bulaşmışsa tek bir cihaza yönelik olası risklere bağlı olarak atanır.

Uç Nokta uyarısı önem düzeyi için Defender, algılanan davranışın önem derecesini, cihaz için gerçek riski ancak daha da önemlisi kuruluş için olası riski temsil eder.

Bu nedenle, örneğin:

- Bir Microsoft Defender Virüsten Koruma için Uç Nokta Için Defender uyarısının önem derecesi, cihaza tamamen engel olan ve bu şekilde etkilenmemiş bir tehdit algıladı, çünkü gerçek bir hasar yoktu, "Bilgilendirme" olarak kategorize edilir.
- Yürütürken ticari kötü amaçlı yazılımla ilgili bir uyarı algılandı, ancak Microsoft Defender AV tarafından engellendi ve düzeltildi, çünkü bu uyarı cihaza biraz zarar verdiği için "Düşük" olarak kategorilere ayrılmıştır ancak kurumsal bir tehdit oluşturmaz.
- Yürütürken algılanan kötü amaçlı yazılım uyarısı tek bir cihaz için değil, daha sonra engellenmiş olup olmadığını bakılmaksızın kuruluş için değil, "Orta" veya "Yüksek" olarak derece edilebilir.
- Engellenmedi veya düzelti olmayan şüpheli davranış uyarıları, aynı kurumsal tehdit dikkate alınmasına göre "Düşük", "Orta" veya "Yüksek" olarak derecelenir.

### <a name="status"></a>Durum

Uyarılar listesini Durumlarına göre filtrelemeyi seçebilirsiniz.

### <a name="categories"></a>Kategoriler

[MITRE ATT ve CK](https://attack.mitre.org/) matrisinde kurumsal saldırı taktiklerini hizalamak [](https://attack.mitre.org/tactics/enterprise/) için uyarı kategorilerini&belirlendi. Yeni kategori adları tüm yeni uyarılara uygulanır. Var olan uyarılar önceki kategori adlarını gizli tutacak.

### <a name="service-sources"></a>Hizmet kaynakları

Microsoft Tehdit Uzmanları önizleme katılımcıları artık tehdit uzmanları tarafından yönetilen yeni arama hizmetinin algılamalarını filtreleye ve görebilir.

Aşağıdaki Hizmet kaynakları temel alarak uyarıları filtrele:

- Kimlik için Microsoft Defender
- Bulut Uygulamaları için Microsoft Defender
- Uç Nokta için Microsoft Defender
- Microsoft 365 Defender
- Office 365 için Microsoft Defender
- Uygulama Yönetimi
- AAD Koruma

> [!NOTE]
> Virüsten Koruma filtresi, yalnızca cihazlar yazılımdan Microsoft Defender Virüsten Koruma için varsayılan gerçek zamanlı koruma ürünü olarak Yazılım'ı kullanıyorsa görüntülenir.

### <a name="tags"></a>Etiketler

Uyarıları, uyarılara atanan Etiketlere göre filtreleebilirsiniz.

### <a name="policy"></a>İlke 

Aşağıdaki ilkelere göre uyarıları filtre yapabilirsiniz:

- Sık kullanılmayan ülkenin etkinliği
- Yönetici Gönderimi Sonucu Tamamlandı
- Yönetici e-postanın el ile soruşturmasını tetikledi
- Yönetici, kullanıcının güvenliği tehlikeye atarak araştırmayı tetikledi
- Anormal Belirteç 
- Atipik seyahat
- Yönlendirme/yeniden yönlendirme kuralı oluşturma
- Teslimden sonra kötü amaçlı URL içeren e-posta iletileri kaldırıldı
- Teslimden sonra kötü amaçlı dosya içeren e-posta iletileri kaldırıldı
- Kullanıcı tarafından kötü amaçlı yazılım veya kimlik avı olarak bildirilen e-posta
- Parola Parolaları
- Yönetici tarafından e-postalarda veya URL'de veya gönderende yapılan düzeltme eylemi
- Şüpheli hizmet oluşturma 
- Yabancı oturum açma özellikleri

### <a name="entities"></a>Varlıklar

Uyarıları, Varlık adı veya kimliğine göre filtreleebilirsiniz. 

### <a name="automated-investigation-state"></a>Otomatik soruşturma durumu

Uyarıları otomatik soruşturma durumlarına göre filtrelemeyi seçebilirsiniz.



## <a name="related-topics"></a>İlgili konular

- [Uç nokta uyarıları için Microsoft Defender'ı yönetme](manage-alerts.md)
- [Uç nokta uyarıları için Microsoft Defender'ı araştırma](investigate-alerts.md)
- [Uç nokta için Microsoft Defender uyarısıyla ilişkilendirilmiş dosyayı araştırma](investigate-files.md)
- [Uç Nokta Cihazları için Microsoft Defender listesinde cihazları araştırma](investigate-machines.md)
- [Uç nokta için Microsoft Defender uyarısıyla ilişkilendirilmiş IP adresini araştırma](investigate-ip.md)
- [Uç nokta için Microsoft Defender uyarısıyla ilişkilendirilmiş etki alanını araştırma](investigate-domain.md)
- [Uç Nokta için Microsoft Defender'da kullanıcı hesabını araştırma](investigate-user.md)
