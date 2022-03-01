---
title: Uç nokta veri depolaması ve gizliliği için Microsoft Defender
description: Uç nokta için Microsoft Defender'ın gizlilik ve toplayan verileri nasıl işlemesi hakkında bilgi edinebilirsiniz.
keywords: Uç Nokta için Microsoft Defender, veri depolama ve gizlilik, depolama, gizlilik, lisans, coğrafi konum, veri bekletme, veriler
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
ms.openlocfilehash: 7e6e530406b4211c62d315f26b8f956cf6bf1bde
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998157"
---
# <a name="microsoft-defender-for-endpoint-data-storage-and-privacy"></a>Uç nokta veri depolaması ve gizliliği için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Bu bölüm, Uç Nokta için Defender'da gizlilik ve veri işlemeyle ilgili en sık sorulan soruların yanıtlarını içerir.

> [!NOTE]
> Bu belgede, Uç Nokta için Defender ile ilgili veri depolaması ve gizlilik ayrıntıları açıkları. Uç nokta için Defender ile ve Microsoft Defender Virüsten Koruma ve Windows gibi diğer ürün ve hizmetlerle ilgili daha fazla bilgi Windows [bkz. Microsoft Gizlilik Bildirimi](https://go.microsoft.com/fwlink/?linkid=827576). Daha fazla [bilgi Windows gizlilik SSS](https://go.microsoft.com/fwlink/?linkid=827577) bölümüne bakın.

## <a name="what-data-does-microsoft-defender-for-endpoint-collect"></a>Uç nokta için Microsoft Defender hangi verileri toplar?

Uç Nokta için Microsoft Defender, yapılandırılmış cihazlarınız üzerinde yönetim, izleme ve raporlama amacıyla hizmete özel olarak ayrılmış ve ayrılmış bir kiracıda bilgi toplar ve depolar.

Toplanan bilgiler arasında dosya verileri (dosya adları, boyutlar ve karmalar gibi), süreç verileri (çalışan süreçler, karmalar), kayıt defteri verileri, ağ bağlantısı verileri (ana bilgisayar KIMLIKleri ve bağlantı noktaları) ve cihaz ayrıntıları (cihaz tanımlayıcıları, adlar ve işletim sistemi sürümü gibi) yer alır.

Microsoft bu verileri Microsoft'ta Microsoft Azure, Microsoft gizlilik uygulamaları ve Microsoft Güven Merkezi ilkelerine [göre korur](https://go.microsoft.com/fwlink/?linkid=827578).

Bu veriler, Uç Nokta için Defender'ın şunları şunları sağlar:

- Kuruluşta saldırı göstergelerini (IOA) önceden belirleme
- Olası bir saldırı algılanırsa uyarı oluşturma
- Güvenlik işlemlerinizi, ağdan gelen tehdit işaretleriyle ilgili cihazlar, dosyalar ve URL'ler için bir görünüm sağlayarak, ağ üzerinde güvenlik tehditlerini araştırmanıza ve incelemenize olanak tanır.

Microsoft, verilerinizi reklam için kullanmaz.

## <a name="data-protection-and-encryption"></a>Veri koruma ve şifreleme

Uç nokta için Defender hizmeti, veri altyapısını temel alan resim veri koruma teknolojilerinin Microsoft Azure kullanır.

Hizmetimizin ilgilenmesi gereken veri korumasıyla ilgili çeşitli yönler vardır. Şifreleme en kritik öneme sahip olan şifrelemedir ve beklemede veri şifreleme, uçuşlarda şifreleme ve Anahtar Kasa ile anahtar yönetimi içerir. Uç nokta hizmeti için Defender tarafından kullanılan diğer teknolojiler hakkında daha fazla bilgi için bkz. [Azure şifrelemeye genel bakış](/azure/security/security-azure-encryption-overview).

Tüm senaryolarda, veriler en düşük 256 bit [AES şifrelemesi kullanılarak](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) şifrelenir.

## <a name="data-storage-location"></a>Veri depolama konumu

Defender for Endpoint, Microsoft Azure Ya da Amerika Birleşik Devletleri'nde ya da Avrupa Birliği'nde veri merkezlerinde çalışır. Hizmet tarafından toplanan müşteri verileri şu konumlarda depolanabilir: (a) sağlama sırasında tanımlandığı şekilde kiracının coğrafi konumu veya (b) Uç Nokta için Defender bu tür verileri işlemede başka bir Microsoft çevrimiçi hizmeti kullanıyorsa, bu diğer çevrimiçi hizmetin veri depolama kurallarına göre tanımlanan coğrafi konumdur.

Takma adla kayıtlı müşteri verileri, AMERIKA Birleşik Devletleri'nde merkezi depolama ve işleme sistemlerinde de depolanıyor olabilir.

Yapılandırıldığında, verilerinizin depolandığı konumu değiştiremezsiniz. Bu, verilerinizin bulunduğu coğrafi konumları etkin bir şekilde seçerek uyumluluk riskini en aza indirmenin kolay bir yolunu sağlar.

## <a name="is-my-data-isolated-from-other-customer-data"></a>Verilerim diğer müşteri verilerinden yalıtılmış mı?

Evet, verileriniz müşteri tanımlayıcısına dayalı olarak access kimlik doğrulaması ve mantıksal ayrım yoluyla yalıtılmış olur. Her müşteri yalnızca kendi kuruluşundan toplanan verilere ve Microsoft'un sağladığı genel verilere erişim iznine sahip olabilir.

## <a name="how-does-microsoft-prevent-malicious-insider-activities-and-abuse-of-high-privilege-roles"></a>Microsoft kötü amaçlı Insider etkinliklerini ve yüksek ayrıcalık rollerinin kötüye kullanımı nasıl önler?

Microsoft geliştiricilerin ve yöneticilerine, tasarım tarafından, hizmeti çalıştırmak ve geliştirecek şekilde atanan görevleri yerine etmek için yeterli ayrıcalıklar verilmiştir. Microsoft, yetkisiz geliştirici ve/veya yönetim etkinliklerine karşı korunmasına yardımcı olmak için aşağıdaki mekanizmalar dahil olmak üzere, koruma, güvenlik ve reaktif denetim bileşimlerini dağıtıyor:

- Hassas verilere sıkı erişim denetimi
- Kötü amaçlı etkinlik algılamadan bağımsız olarak algılamayı büyük ölçüde geliştiren denetim birleşimleri
- İzleme, günlüğe kaydetme ve raporlamanın birden çok düzeyi

Buna ek olarak, Microsoft bazı işlem personeli için arka planda doğrulama denetimleri sağlar ve arka plan doğrulaması düzeyine göre uygulamalara, sistemlere ve ağ altyapısına erişimi sınırlar. İşlem personeli, bir müşterinin hesabına veya görevleri sırasında ilgili bilgilere erişmeleri gerektiğinde resmi bir süreci takip eder.

Microsoft Azure Kamu veri merkezlerinde dağıtılan hizmetlere erişim, yalnızca FedRAMP, NIST 800.171 (DIB), ITAR, IRS 1075, DoD L4 ve CJIS gibi resmi düzenlemelere ve gerekliliklere tabi verilerin işletmesi için onaylanmış işletme personeline verilmektedir.

## <a name="is-data-shared-with-other-customers"></a>Veriler diğer müşterilerle paylaşılıyor mu?

Hayır. Müşteri verileri diğer müşterilerden yalıtılır ve paylaşılmaz. Bununla birlikte, Microsoft'un işlemesi sonucunda elde edilen ve müşteriye özgü veriler içermeen verilere yönelik içgörüler diğer müşterilerle paylaşılır. Her müşteri yalnızca kendi kuruluşundan toplanan verilere ve Microsoft'un sağladığı genel verilere erişim iznine sahip olabilir.

## <a name="how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy"></a>Microsoft verilerimi ne kadar süre depolar? Microsoft'un veri bekletme ilkesi nedir?

### <a name="at-service-onboarding"></a>Hizmet eklemede

Varsayılan olarak, veriler 180 gün süreyle korunur; bununla birlikte, verileriniz için veri bekletme ilkesi belirtebilirsiniz. Bu, uç nokta için Window Defender'ın verilerinizi ne kadar süreyle depola durumuna belirleyecek. Şirketinizin mevzuat uyumluluğu  ihtiyaçlarını karşılamak için bir ay ile altı ay arasında bir seçim esnekliği vardır.

### <a name="at-contract-termination-or-expiration"></a>Sözleşme fesih veya son kullanma tarihi

Lisansınız yetkisiz kullanım süresi veya askıya alınmış modundayken verileriniz tutulur ve verileriniz size kullanılabilir. Bu dönemin sonunda, bu veriler, sözleşmenin sona ermesi veya sona ermesi ile en geç 180 gün içinde kurtarılamaz hale gelecek şekilde Microsoft sistemleri tarafından silinir.

### <a name="advanced-hunting-data"></a>Gelişmiş Av verileri

Gelişmiş av, 30 günlük ham verileri keşfetmenizi sağlayan sorgu tabanlı bir tehdit arama aracıdır.

## <a name="can-microsoft-help-us-maintain-regulatory-compliance"></a>Microsoft yasal düzenlemelere uyumu korumamıza yardımcı olabilir mi?

Microsoft, müşterilerin Uç Nokta hizmetleri için Defender'ı kendi yasal ve mevzuat gereksinimlerine göre değerlendirmelerine yardımcı olmak için, denetim raporları ve uyumluluk paketleri gibi Microsoft'un güvenlik ve uyumluluk programları hakkında ayrıntılı bilgi sağlar. Endpoint için Defender; ISO, SOC, FedRAMP High ve PCI gibi bir dizi sertifika elde etti ve ulusal, bölgesel ve sektöre özgü ek sertifikaları takipmaya devam ediyor.

Microsoft müşterilere uyumlu ve bağımsız olarak doğrulanmış hizmetler sağlayarak, müşterilerin çalıştır çalıştıracakları altyapı ve uygulamalara uyumluluk eldelerini kolaylaştırır.

Uç nokta sertifika raporları için Defender hakkında daha fazla bilgi için bkz. [Microsoft Güven Merkezi](https://servicetrust.microsoft.com/). 

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-datastorage-belowfoldlink)
