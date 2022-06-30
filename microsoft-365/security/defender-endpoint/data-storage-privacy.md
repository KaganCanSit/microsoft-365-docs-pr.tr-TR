---
title: veri depolama ve gizliliği Uç Nokta için Microsoft Defender
description: Uç Nokta için Microsoft Defender'ın topladığı gizlilik ve verileri nasıl işlediği hakkında bilgi edinin.
keywords: Uç Nokta için Microsoft Defender, veri depolama ve gizlilik, depolama, gizlilik, lisanslama, coğrafi konum, veri saklama, veriler
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: d1d8ad0a16129e909476891291c0b2c0f0d54956
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554157"
---
# <a name="microsoft-defender-for-endpoint-data-storage-and-privacy"></a>veri depolama ve gizliliği Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Bu bölümde, Uç Nokta için Defender için gizlilik ve veri işlemeyle ilgili en sık sorulan sorulardan bazıları ele alınıyor.

> [!NOTE]
> Bu belgede, Uç Nokta için Defender ile ilgili veri depolama ve gizlilik ayrıntıları açıklanmaktadır. Uç Nokta için Defender ve Microsoft Defender Virüsten Koruma ve Windows gibi diğer ürün ve hizmetlerle ilgili daha fazla bilgi için bkz. [Microsoft Gizlilik Bildirimi](https://go.microsoft.com/fwlink/?linkid=827576). Daha fazla bilgi için bkz. [Windows gizlilik hakkında SSS](https://go.microsoft.com/fwlink/?linkid=827577) .

## <a name="what-data-does-microsoft-defender-for-endpoint-collect"></a>Uç Nokta için Microsoft Defender hangi verileri toplar?

Uç Nokta için Microsoft Defender, yapılandırılmış cihazlarınızdan yönetim, izleme ve raporlama amacıyla hizmete özel ayrılmış ve ayrılmış bir kiracıda bilgileri toplar ve depolar.

Toplanan bilgiler dosya verilerini (dosya adları, boyutlar ve karmalar gibi), işlem verilerini (çalışan işlemler, karmalar), kayıt defteri verilerini, ağ bağlantı verilerini (konak IP'leri ve bağlantı noktaları) ve cihaz ayrıntılarını (cihaz tanımlayıcıları, adlar ve işletim sistemi sürümü gibi) içerir.

Microsoft bu verileri Microsoft Azure'da güvenli bir şekilde depolar ve Microsoft gizlilik uygulamalarına ve [Microsoft Güven Merkezi ilkelerine](https://go.microsoft.com/fwlink/?linkid=827578) uygun olarak saklar.

Bu veriler Uç Nokta için Defender'ın şunları etkinleştirmesini sağlar:

- Kuruluşunuzdaki saldırı göstergelerini (GÇA' lar) proaktif olarak belirleme
- Olası bir saldırı algılanırsa uyarı oluşturma
- Ağınızdan gelen tehdit sinyalleriyle ilgili cihazlara, dosyalara ve URL'lere yönelik bir görünümle güvenlik işlemlerinizi sağlayın ve ağ üzerindeki güvenlik tehditlerinin varlığını araştırmanıza ve keşfetmenize olanak tanıyın.

Microsoft, verilerinizi reklam için kullanmaz.

## <a name="data-protection-and-encryption"></a>Veri koruma ve şifreleme

Uç Nokta için Defender hizmeti, Microsoft Azure altyapısını temel alan son teknoloji veri koruma teknolojilerini kullanır.

Hizmetimizin ilgilendiği veri korumayla ilgili çeşitli yönleri vardır. Şifreleme en kritiklerden biridir ve bekleyen veri şifrelemesi, aktarım sırasında şifreleme ve Key Vault ile anahtar yönetimini içerir. Uç Nokta için Defender hizmeti tarafından kullanılan diğer teknolojiler hakkında daha fazla bilgi için bkz. [Azure şifrelemesine genel bakış](/azure/security/security-azure-encryption-overview).

Tüm senaryolarda veriler en az 256 bit [AES şifrelemesi](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) kullanılarak şifrelenir.

## <a name="data-storage-location"></a>Veri depolama konumu

Uç Nokta için Defender, Avrupa Birliği, Birleşik Krallık veya Birleşik Devletler Microsoft Azure veri merkezlerinde çalışır. Hizmet tarafından toplanan müşteri verileri şu konumda depolanabilir: (a) sağlama sırasında tanımlanan kiracının coğrafi konumu veya (b) Uç Nokta için Defender bu tür verileri işlemek için başka bir Microsoft çevrimiçi hizmeti kullanıyorsa, coğrafi konum, söz konusu diğer çevrimiçi hizmetin veri depolama kuralları tarafından tanımlandığı şekilde.

Takma adla kullanılan müşteri verileri, Birleşik Devletler merkezi depolama ve işleme sistemlerinde de depolanabilir.

Yapılandırıldıktan sonra, verilerinizin depolandığı konumu değiştiremezsiniz. Bu, verilerinizin bulunacağı coğrafi konumları etkin bir şekilde seçerek uyumluluk riskini en aza indirmek için kullanışlı bir yol sağlar.

## <a name="is-my-data-isolated-from-other-customer-data"></a>Verilerim diğer müşteri verilerinden yalıtılmış mı?

Evet, verileriniz erişim kimlik doğrulaması ve müşteri tanımlayıcısı temelinde mantıksal ayrım yoluyla yalıtılır. Her müşteri yalnızca kendi kuruluşundan toplanan verilere ve Microsoft'un sağladığı genel verilere erişebilir.

## <a name="how-does-microsoft-prevent-malicious-insider-activities-and-abuse-of-high-privilege-roles"></a>Microsoft kötü amaçlı insider etkinliklerini ve yüksek ayrıcalıklı rollerin kötüye kullanılmasını nasıl önler?

Microsoft geliştiricileri ve yöneticilerine, tasarımı gereği, hizmeti çalıştırmak ve geliştirmek için kendilerine atanan görevleri yerine getirmek için yeterli ayrıcalıklar verilmiştir. Microsoft, yetkisiz geliştirici ve/veya yönetim etkinliğine karşı korunmaya yardımcı olmak için aşağıdaki mekanizmalar da dahil olmak üzere önleyici, dedektif ve reaktif denetimlerin kombinasyonlarını dağıtır:

- Hassas verilere sıkı erişim denetimi
- Kötü amaçlı etkinliklerin bağımsız olarak algılanmasında büyük ölçüde geliştiren denetimlerin birleşimleri
- Birden çok izleme, günlüğe kaydetme ve raporlama düzeyi

Buna ek olarak, Microsoft belirli operasyon personeli için arka plan doğrulama denetimleri gerçekleştirir ve arka plan doğrulama düzeyiyle orantılı olarak uygulamalara, sistemlere ve ağ altyapısına erişimi sınırlar. Operasyon personeli, görevlerinin performansında müşterinin hesabına veya ilgili bilgilerine erişmeleri gerektiğinde resmi bir süreci izler.

Microsoft Azure Kamu veri merkezlerinde dağıtılan hizmetlere yönelik verilere erişim yalnızca FedRAMP, NIST 800.171 (DIB), ITAR, IRS 1075, DoD L4 ve CJIS gibi belirli kamu düzenlemelerine ve gereksinimlerine tabi olan verileri işlemek üzere denetlenen ve onaylanan işletim personeline verilir.

## <a name="is-data-shared-with-other-customers"></a>Veriler diğer müşterilerle paylaşılıyor mu?

Hayır. Müşteri verileri diğer müşterilerden yalıtılır ve paylaşılmaz. Ancak, Microsoft'un işlemesinden kaynaklanan ve müşteriye özgü veriler içermeyen veriler hakkında içgörüler diğer müşterilerle paylaşılabilir. Her müşteri yalnızca kendi kuruluşundan toplanan verilere ve Microsoft'un sağladığı genel verilere erişebilir.

## <a name="how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy"></a>Microsoft verilerimi ne kadar süreyle depolayacak? Microsoft'un veri saklama ilkesi nedir?

### <a name="at-service-onboarding"></a>Hizmette ekleme

Varsayılan olarak, veriler 180 gün boyunca tutulur; ancak, verileriniz için veri saklama ilkesini belirtebilirsiniz. Bu, Uç Nokta için Microsoft Defender verilerinizi ne kadar süreyle depolayacaklarını belirler. Şirketinizin mevzuat uyumluluğu gereksinimlerini karşılamak için bir ila altı ay arasında seçim esnekliği vardır.

### <a name="at-contract-termination-or-expiration"></a>Sözleşme sonlandırılma veya süre sonu

Lisans yetkisiz kullanım süresi veya askıya alınma modu altındayken verileriniz korunur ve sizin kullanımınıza sunulur. Bu sürenin sonunda bu veriler, sözleşmenin sona ermesinden veya sona ermesinden en fazla 180 gün sonra kurtarılamaz hale getirmek için Microsoft'un sistemlerinden silinecektir.

### <a name="advanced-hunting-data"></a>Gelişmiş Tehdit Avcılığı verileri

Gelişmiş avcılık, 30 güne kadar ham verileri keşfetmenizi sağlayan sorgu tabanlı bir tehdit avcılığı aracıdır.

## <a name="can-microsoft-help-us-maintain-regulatory-compliance"></a>Microsoft mevzuat uyumluluğunu korumamıza yardımcı olabilir mi?

Microsoft, müşterilerin Uç Nokta için Defender hizmetlerini kendi yasal ve mevzuat gereksinimlerine göre değerlendirmesine yardımcı olmak için müşterilere denetim raporları ve uyumluluk paketleri de dahil olmak üzere Microsoft'un güvenlik ve uyumluluk programları hakkında ayrıntılı bilgi sağlar. Uç Nokta için Defender ISO, SOC, FedRAMP High ve PCI gibi bir dizi sertifika elde etmiş ve ulusal, bölgesel ve sektöre özgü ek sertifikaları takip etmeye devam ediyor.

Microsoft, müşterilere uyumlu, bağımsız olarak doğrulanmış hizmetler sunarak müşterilerin çalıştırdıkları altyapı ve uygulamalar için uyumluluk elde etmelerini kolaylaştırır.

Uç Nokta için Defender sertifika raporları hakkında daha fazla bilgi için bkz. [Microsoft Güven Merkezi](https://servicetrust.microsoft.com/). 

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-datastorage-belowfoldlink)
