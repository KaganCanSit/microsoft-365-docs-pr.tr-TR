---
title: Microsoft 365 Lighthouse'da Kiracılar sayfasına genel bakış
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Microsoft 365 Lighthouse kullanan Yönetilen Hizmet Sağlayıcıları (MSP) için Kiracılar sayfası hakkında bilgi edinin.
ms.openlocfilehash: 7b8e26ddbe68059a9c5ecf4d5e396fd11c49be71
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2022
ms.locfileid: "65023293"
---
# <a name="overview-of-the-tenants-page-in-microsoft-365-lighthouse"></a>Microsoft 365 Lighthouse'da Kiracılar sayfasına genel bakış

Microsoft 365 Lighthouse, kiracılar sayfasını açmak için sol gezinti bölmesinde **Kiracılar'ı** seçerek kiracı hesaplarını yönetmenize olanak tanır. Kiracılar sayfası tüm kiracılarınızın listesini içerir. Kişi ayrıntıları ve dağıtım durumu gibi ayrıntılı bilgileri görüntülemek için bir kiracı seçebilirsiniz.

Kiracılar sayfası aşağıdaki seçenekleri de içerir:

- **Ihracat:** Kiracı verilerini virgülle ayrılmış Excel değerler (.csv) dosyasına aktarmak için seçin.
- **Etiketleri Yönet:** Etiket eklemek, düzenlemek veya silmek için seçin.
- **Etiketleri Ata:** Kiracıya etiket atamak için öğesini seçin.
- **Arama:** Listede belirli bir kiracıyı hızla bulmak için anahtar sözcükler girin.

:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-page-overview.png" alt-text="Kiracı sayfasının ekran görüntüsü.":::

## <a name="tenant-list"></a>Kiracı listesi

Kiracı listesi, sözleşmeniz olan farklı kiracılara ilişkin içgörüler sağlar ve bunların kiracı Lighthouse ekleme durumu da buna dahildir. Kiracı listesi ayrıca Lighthouse genelinde farklı filtreler sağlamak için kiracıları etiketlemenize ve belirli bir kiracı ve dağıtım planının durumu hakkında daha fazla bilgi edinmek için detaya gitmenizi sağlar.

Kiracılarınız [Lighthouse ekleme gereksinimlerini karşıladıktan](m365-lighthouse-requirements.md) sonra kiracı listesinde durumu **Etkin** olarak gösterilir.

Kiracı listesi şunları yapmanızı sağlar:

- Kiracıları etkin, etkin olmayan ve uygun olmayanlara göre otomatik olarak sıralayın.
- Kiracı listesini dışarı aktarın.
- Etiketleri atama ve yönetme.
- Kiracıları ada göre arayın.
- Kiracıları duruma, temsilci yönetim ayrıcalığına (DAP) ve etiketlere göre filtreleyin.

Kiracıyı devre dışı bırakmak veya etiketleri görüntülemek ve yönetmek için kiracı adının yanındaki üç noktayı (diğer eylemler) seçin. Kiracı adını seçerek veya kiracıya atanan etiketlerden birini seçerek tek tek kiracıları görüntüleyebilirsiniz.

## <a name="tenant-status"></a>Kiracı durumu

Aşağıdaki tabloda farklı durumlar ve anlamları gösterilmektedir.<br><br>

| Durum                                   | Açıklama                                                                                             |
|------------------------------------------|---------------------------------------------------------------------------------------------------------|
| Etkin                                   | Kiracı ekleme ve veri akışı başlatıldı.                                                           |
| Etkin olmayan                                 | Kiracı, MSP'nin isteği üzerine eklendi ve artık Lighthouse'da yönetilmedi.           |
| İşlemde                               | Kiracı bulundu ancak tam olarak eklenmedi.                                                              |
| Uygun değil - DAP veya GDAP ayarlanmadı    | İş ortağının kiracıyla ayarlanmış temsilci (DAP) veya ayrıntılı temsilci (GDAP) yönetici ayrıcalıkları olmalıdır. |
| Uygun değil - Gerekli lisans eksik | Kiracı gerekli lisansa sahip değil.                                                               |
| Uygun değil - Kullanıcı sayısı aşıldı         | Kiracının izin verilenden daha fazla kullanıcısı var.                                                                     |
| Uygun değil - Coğrafi denetim başarısız oldu            | İş ortağı ve müşteri aynı coğrafi konumda bulunmalıdır.                                       |

Bir kiracıyı devre dışı bırakdıktan sonra, devre dışı bırakma işlemi tamamlanana kadar kiracı üzerinde işlem yapamazsınız. Devre dışı bırakmanın tamamlanması 48 saat kadar sürebilir. Bir kiracıyı yeniden etkinleştirmeye karar verirseniz verilerin yeniden görüntülenmesi 48 saat kadar sürebilir.

## <a name="tenant-tags"></a>Kiracı etiketleri

Kiracılarınızı düzenlemeye ve mevcut görünümleri kolayca filtrelemeye yardımcı olmak için, kiracılarınıza etiketler oluşturabilir ve atayabilirsiniz. Daha fazla bilgi için bkz. [Microsoft 365 Lighthouse'da kiracı listenizi yönetme](m365-lighthouse-manage-tenant-list.md).

> [!NOTE]
> Tüm kiracılarda en fazla 30 etiket oluşturabilirsiniz.

## <a name="tenant-details-page"></a>Kiracı ayrıntıları sayfası

Ayrıntılı kiracı bilgilerini görüntülemek için kiracı listesinden bir kiracı seçin. Kiracı ayrıntıları sayfası kişi bilgilerini ve dağıtım planı durumunu içerir.

:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-details-page.png" alt-text="Kiracı ayrıntıları sayfasının ekran görüntüsü.":::

### <a name="overview-tab"></a>Genel Bakış sekmesi

Genel Bakış sekmesinde kiracıya genel bakış, kişi bilgileri ve Microsoft 365 hizmet kullanımını görüntüleyebilirsiniz.

#### <a name="tenant-overview-card"></a>Kiracıya genel bakış kartı

Kiracıya genel bakış kartı, Microsoft 365 hesabından kiracı hakkında bilgi sağlar.<br><br>

| Kiracı Bilgileri    | Açıklama|
|-----------------------|------------------|
| Genel Müdürlük    | Kiracının bulunduğu yer.|
| Sanayi    |Kuruluşun sektörü.|
| Web sitesi    |Kuruluşun web sitesi. Veri sağlanmazsa bu alanı düzenleyebilirsiniz.|
| Müşteri etki alanı    |Kuruluşun etki alanı.|
| Toplam kullanıcı sayısı    |Kiracıda atanan kullanıcı sayısı. Bu kiracının Kullanıcılar sayfasını açmak için bu numarayı seçebilirsiniz.|
| Toplam cihaz sayısı|Kiracıya kaydedilen cihaz sayısı. Bu kiracının Cihazlar sayfasını açmak için bu numarayı seçebilirsiniz.|

#### <a name="contacts-card"></a>Kişiler kartı

Kişiler kartı, yönettiğiniz kiracıların içindeki önemli kişilerin bilgilerini girmenize olanak tanır; örneğin:

- Name
- Başlık
- Phone
- E-posta
- Notlar

Notlar bölümü, kiracının görevlendirme tercihleri, konum, saat dilimi ve kuruluştaki rolüyle ilgili ayrıntılar gibi önemli bilgileri kaydetmek için kullanabileceğiniz bir metin alanıdır.

Ayrıntıları düzenlemek veya mevcut bir kişiyi silmek için listeden kişi adını seçin. **Kişiyi düzenle** bölmesinde, kişiyi düzenleyin veya silin. Başka bir kişi eklemek için **+Kişi ekle'yi** seçin.

#### <a name="microsoft-365-usage-card"></a>Microsoft 365 kullanım kartı

Lighthouse, kiracı içindeki kaç kullanıcının lisanslı olduğu ve her hizmeti etkin bir şekilde kullandığı da dahil olmak üzere Microsoft 365 hizmet kullanımıyla ilgili içgörüler sağlar. Etkin, son 28 gün içinde hizmette en az bir kez oturum açmış olan kullanıcı veya cihaz sayısını gösterir. Değişiklik, geçen aydan bu yana etkin kullanıcı ve cihazlardaki değişikliği gösterir.

Microsoft 365 Kullanımı kartı iki bölüm içerir:

- **Microsoft 365 Lighthouse etkin hizmetler:** Lighthouse portalında yönetilebilen hizmetler.
- **Ek Microsoft 365 hizmetleri:** Microsoft 365 paketine dahil edilen ancak şu anda Microsoft 365 Lighthouse portalında yönetilebilen hizmetler.

### <a name="deployment-plans-tab"></a>Dağıtım Planları sekmesi

Dağıtım Planları sekmesi, kiracının dağıtım planında durum sağlar. Listedeki dağıtım adımları, kiracıya uygulanan temeli temel alır. Dağıtım adımı ayrıntılarını görmek için listeden bir dağıtım adımı seçin.

Dağıtım Planları sekmesi aşağıdaki seçenekleri de içerir:

- **Ihracat:** Dağıtım adımı verilerini virgülle ayrılmış Excel değerler (.csv) dosyasına aktarmak için seçin.
- **Yenileme:** En güncel dağıtım adımı verilerini almak için öğesini seçin.
- **Arama:** Listede belirli bir dağıtım adımını hızla bulmak için anahtar sözcükler girin.

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 Lighthouse gereksinimleri](m365-lighthouse-requirements.md) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)\
[kiracı listenizi Microsoft 365 Lighthouse 'de yönetme](m365-lighthouse-manage-tenant-list.md) (makale)\
[Standart kiracı yapılandırmalarını dağıtmak için Microsoft 365 Lighthouse temellerini kullanmaya genel bakış](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (makale)\
[Microsoft 365 Lighthouse temellerini dağıtma](m365-lighthouse-deploy-baselines.md) (makale)
