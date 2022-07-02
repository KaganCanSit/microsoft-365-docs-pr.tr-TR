---
title: Uç Nokta için Microsoft Defender Uyarıları kuyruğu görüntüleme ve düzenleme
description: Uç Nokta için Microsoft Defender uyarı kuyruklarının nasıl çalıştığı ve uyarı listelerini sıralama ve filtreleme hakkında bilgi edinin.
keywords: uyarılar, kuyruklar, uyarılar kuyruğu, sıralama, sıralama, filtreleme, uyarıları yönetme, yeni, devam ediyor, çözümlendi, en yeni, kuyruktaki süre, önem derecesi, zaman aralığı, Microsoft tehdit uzmanları uyarıları
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
ms.openlocfilehash: 13959666f0c44f83fcb938db010ed30d5e5056b4
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607542"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-alerts-queue"></a>Uç Nokta için Microsoft Defender Uyarıları kuyruğu görüntüleme ve düzenleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-alertsq-abovefoldlink)

**Uyarılar kuyruğu**, ağınızdaki cihazlardan bayrak eklenmiş uyarıların listesini gösterir. Varsayılan olarak, kuyruk son 30 gün içinde görülen uyarıları gruplandırılmış bir görünümde görüntüler. En son uyarılar listenin en üstünde gösterilir ve en son uyarıları ilk olarak görmenize yardımcı olur.

> [!NOTE]
> Otomatik araştırma ve düzeltme ile uyarılar önemli ölçüde azaltılarak güvenlik operasyonları uzmanlarının daha karmaşık tehditlere ve diğer yüksek değerli girişimlere odaklanmasına olanak sağlanır. Bir uyarı, otomatik araştırma için desteklenen bir varlık (örneğin, bir dosya) içerdiğinde, bu uyarı için desteklenen bir işletim sistemine sahip bir cihazda otomatik araştırma ve düzeltme başlatılabilir. Otomatik araştırmalarla ilgili daha fazla bilgi için bkz. [Otomatik araştırmalara genel bakış](automated-investigations.md).

Uyarılar görünümünü özelleştirmek için aralarından seçim yapabileceğiniz çeşitli seçenekler vardır.

Üst gezintide aşağıdakileri yapabilirsiniz:

- Sütunları eklemek veya kaldırmak için sütunları özelleştirme
- Filtre uygulama
- 1 Gün, 3 Gün, 1 Hafta, 30 Gün ve 6 Ay gibi belirli bir süre için uyarıları görüntüleme
- Uyarı listesini Excel'e aktarma
- Uyarıları Yönet

:::image type="content" source="images/alerts-queue-list.png" alt-text="Uyarılar kuyruğu sayfası" lightbox="images/alerts-queue-list.png":::

## <a name="sort-and-filter-alerts"></a>Uyarıları sıralama ve filtreleme 

Uyarı listesini sınırlamak ve uyarıların daha odaklanmış bir görünümünü elde etmek için aşağıdaki filtreleri uygulayabilirsiniz.

### <a name="severity"></a>Önem derecesi

Uyarı önem derecesi|Açıklama
---|---
Yüksek <br> (Kırmızı)|Gelişmiş kalıcı tehditlerle (APT) ilişkili olarak görülen uyarılar. Bu uyarılar, cihazlara verebilecekleri hasarın önem derecesi nedeniyle yüksek bir risk olduğunu gösterir. Bazı örnekler şunlardır: kimlik bilgisi hırsızlığı araçları etkinlikleri, herhangi bir grupla ilişkili olmayan fidye yazılımı etkinlikleri, güvenlik algılayıcılarıyla oynama veya insan saldırganı gösteren kötü amaçlı etkinlikler.
Orta <br> (Turuncu)|Gelişmiş bir kalıcı tehdidin (APT) parçası olabilecek uç nokta algılama ve yanıt ihlal sonrası davranışlardan gelen uyarılar. Bu davranışlar saldırı aşamalarında tipik gözlemlenen davranışları, anormal kayıt defteri değişikliklerini, şüpheli dosyaların yürütülmesini vb. içerir. Bazıları iç güvenlik testlerinin bir parçası olsa da, gelişmiş bir saldırının da bir parçası olabileceğinden araştırma gerektirir.
Düşük <br> (Sarı)|Yaygın kötü amaçlı yazılımlarla ilişkili tehditlerle ilgili uyarılar. Örneğin, keşif komutlarını çalıştırma, günlükleri temizleme vb. gibi hack araçları, kötü amaçlı yazılım olmayan hack araçları, genellikle kuruluşu hedefleyen gelişmiş bir tehdidi göstermez. Ayrıca kuruluşunuzdaki bir kullanıcı tarafından yapılan yalıtılmış bir güvenlik aracı testinden de gelebilir.
Bilgi <br> (Gri)|Ağa zararlı olarak kabul edilebilecek ancak olası güvenlik sorunlarına yönelik kurumsal güvenlik farkındalığını yönlendirebilen uyarılar.

#### <a name="understanding-alert-severity"></a>Uyarı önem derecesini anlama

Microsoft Defender Virüsten Koruma (Microsoft Defender AV) ve Uç Nokta için Defender uyarı önem dereceleri farklı kapsamları temsil ettiğinden farklıdır.

Microsoft Defender Virüsten Koruma tehdit önem derecesi, algılanan tehdidin (kötü amaçlı yazılım) mutlak önem derecesini temsil eder ve virüs bulaşmışsa tek bir cihaz için olası risk temelinde atanır.

Uç Nokta için Defender uyarı önem derecesi, algılanan davranışın önem derecesini, cihaz için gerçek riski ancak daha da önemlisi kuruluş için olası riski temsil eder.

Bu nedenle, örneğin:

- Microsoft Defender Virüsten Koruma tarafından algılanan ve cihaza bulaşmayan bir tehdit algılanan bir Uç Nokta için Defender uyarısının önem derecesi, gerçek bir hasar olmadığından "Bilgilendirici" olarak kategorilere ayrılmıştır.
- Yürütülürken ticari bir kötü amaçlı yazılım algılandı, ancak Microsoft Defender AV tarafından engellendi ve düzeltildi, çünkü cihaz tek tek zarara neden olmuş olabilir ancak kurumsal bir tehdit oluşturmaz.
- Yürütülürken algılanan ve yalnızca tek bir cihaz için değil, kuruluş için de tehdit oluşturabilen ve sonunda engellenip engellenmediğine bakılmaksızın kötü amaçlı yazılımla ilgili bir uyarı "Orta" veya "Yüksek" olarak derecelenebilir.
- Engellenmeyen veya düzeltilmemiş şüpheli davranış uyarıları, aynı kurumsal tehdit dikkate alınarak "Düşük", "Orta" veya "Yüksek" olarak sıralanır.

### <a name="status"></a>Durum

Uyarı listesini Durumlarına göre filtrelemeyi seçebilirsiniz.

> [!NOTE]
> *Desteklenmeyen uyarı türü* uyarı durumu görüyorsanız, bu otomatik araştırma özelliklerinin otomatik araştırma çalıştırmak için bu uyarıyı alamayacağı anlamına gelir. Ancak [, bu uyarıları el ile araştırabilirsiniz](../defender/investigate-incidents.md#alerts).

### <a name="categories"></a>Kategori

[MITRE ATT&CK matrisindeki](https://attack.mitre.org/) [kurumsal saldırı taktiklerine](https://attack.mitre.org/tactics/enterprise/) uyum sağlamak için uyarı kategorilerini yeniden tanımladık. Yeni kategori adları tüm yeni uyarılar için geçerlidir. Mevcut uyarılar önceki kategori adlarını tutar.

### <a name="service-sources"></a>Hizmet kaynakları

Microsoft Tehdit Uzmanları önizleme katılımcıları artık yeni tehdit uzmanları tarafından yönetilen tehdit avcılığı hizmetinden gelen algılamaları filtreleyebilir ve görebilir.

Uyarıları aşağıdaki Hizmet kaynaklarına göre filtreleyin:

- Kimlik için Microsoft Defender
- Bulut Uygulamaları için Microsoft Defender
- Uç Nokta için Microsoft Defender
- Microsoft 365 Defender
- Office 365 için Microsoft Defender
- Uygulama İdaresi
- AAD Kimlik Koruması

> [!NOTE]
> Virüsten Koruma filtresi yalnızca cihazlar varsayılan gerçek zamanlı koruma kötü amaçlı yazılımdan koruma ürünü olarak Microsoft Defender Virüsten Koruma kullanıyorsa görünür.

### <a name="tags"></a>Etiketler

Uyarılara atanan etiketlere göre uyarıları filtreleyebilirsiniz.

### <a name="policy"></a>Ilkesi 

Uyarıları aşağıdaki ilkelere göre filtreleyebilirsiniz:

|Algılama kaynağı|API değeri|
|---|---|
|Üçüncü taraf algılayıcılar|ThirdPartySensors|
|Antivirus|WindowsDefenderAv|
|Otomatik araştırma|AutomatedInvestigation|
|Özel algılama|CustomDetection|
|Özel TI|CustomerTI|
|EDR|WindowsDefenderAtp|
|Microsoft 365 Defender|MTP|
|Office 365 için Microsoft Defender|OfficeATP|
|Microsoft Tehdit Uzmanları|ThreatExperts|
|Smartscreen|WindowsDefenderSmartScreen|

### <a name="entities"></a>Varlık

Uyarıları Varlık adına veya kimliğine göre filtreleyebilirsiniz. 

### <a name="automated-investigation-state"></a>Otomatik araştırma durumu

Uyarıları Otomatik araştırma durumlarına göre filtrelemeyi seçebilirsiniz.



## <a name="related-topics"></a>İlgili konular

- [Uç Nokta için Microsoft Defender uyarılarını yönetme](manage-alerts.md)
- [Uç Nokta için Microsoft Defender uyarılarını araştırma](investigate-alerts.md)
- [Uç Nokta için Microsoft Defender uyarısıyla ilişkili bir dosyayı araştırma](investigate-files.md)
- [Uç Nokta için Microsoft Defender Cihazlar listesindeki cihazları araştırma](investigate-machines.md)
- [Uç Nokta için Microsoft Defender uyarısıyla ilişkili IP adresini araştırma](investigate-ip.md)
- [Uç Nokta için Microsoft Defender uyarısıyla ilişkili bir etki alanını araştırma](investigate-domain.md)
- [Uç Nokta için Microsoft Defender'de kullanıcı hesabını araştırma](investigate-user.md)
