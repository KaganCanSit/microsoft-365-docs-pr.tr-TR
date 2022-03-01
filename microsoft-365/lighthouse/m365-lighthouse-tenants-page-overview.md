---
title: Microsoft 365 Lighthouse Kiracılar sayfasına genel bakış
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
description: Yönetilen Hizmet Sağlayıcıları (MSP) Microsoft 365 Lighthouse Kiracılar sayfası hakkında bilgi edinebilirsiniz.
ms.openlocfilehash: 7cddf67bce3a568ea0b5259b7012a7263012d18b
ms.sourcegitcommit: 2ea2105d40b60a87fc9aa30f392a73a3a9db6d99
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2021
ms.locfileid: "63007222"
---
# <a name="microsoft-365-lighthouse-tenants-page-overview"></a>Microsoft 365 Lighthouse Kiracılar sayfasına genel bakış

> [!NOTE]
> Bu makalede açıklanan özellikler Önizleme'dedir, değişebilir ve yalnızca gereksinimleri karşılayacak iş ortakları tarafından [kullanılabilir](m365-lighthouse-requirements.md). Henüz oturum açmadıysanız Microsoft 365 Lighthouse için [kaydolma'ya Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse, sol gezinti bölmesinde Kiracılar'ı seçerek Kiracılar  sayfasını açarak kiracı hesaplarını yönetmenizi sağlar. Kiracılar sayfası tüm kiracıların listesini içerir. Kişi ayrıntıları ve dağıtım durumu gibi ayrıntılı bilgileri görüntülemek için kiracıyı seçin.

Kiracılar sayfası aşağıdaki seçenekleri de içerir:

- **Dışarı aktar:** Kiracı verilerini virgülle ayrılmış değerler (Excel) dosyasına dışarı .csv seçin.
- **Etiketleri Yönet:** Etiket eklemek, düzenlemek veya silmek için öğesini seçin.
- **Etiket Atama:** Bir kiracıya etiket atamak için seçin.
- **Arama:** Listede belirli bir kiracıyı hızla bulmak için anahtar sözcükleri girin.


:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-page-overview.png" alt-text="Kiracı sayfasının ekran görüntüsü.":::

## <a name="tenant-list"></a>Kiracı listesi

Kiracı listesi, kiracı Deniz Feneri ekleme durumları dahil olmak üzere, sözleşmeli olarak sözleşmeli olarak sahip olduğunuz farklı kiracılara öngörüler sağlar. Kiracı listesi ayrıca Deniz Feneri genelinde farklı filtreler sağlamak için kiracıları etiketlemenizi ve belirli bir kiracı ve dağıtım planının durumu hakkında daha fazla bilgi edinmek için detaya gitmenizi sağlar.

Kiracınız Deniz Feneri ekleme [gereksinimlerini](m365-lighthouse-requirements.md) karşıladikten sonra, kiracı listesinde durumu **Etkin** olarak görünür.

Kiracı listesi şunları sağlar:

- Kiracıları etkin, etkin değil ve uygun olmayana göre otomatik olarak sırala.
- Kiracı listesini dışarı aktarma
- Etiketleri atama ve yönetme
- Kiracıları adına göre arama
- Kiracıları durum, temsilcili yönetim ayrıcalığı (DAP) ve etiketlere göre filtrele.

Kiracıyı etkinleştirmek veya etiketleri görüntülemek ve yönetmek için kiracı adının yanındaki üç noktayı seçin. Kiracı adını seçerek veya kiracıya atanmış etiketlerden birini seçerek kiracıları tek tek görüntüebilirsiniz.

## <a name="tenant-status"></a>Kiracı durumu

Aşağıdaki tabloda farklı durumları ve anlamları gösterir.

| Durum                                | Açıklama                                         |
|---------------------------------------|-----------------------------------------------------|
| Etkin                                | Ekleme ve veri akışı başlatıldı.               |
| Etkin değil                              | Kiracı artık etkin değil.                         |
| İşlemde                            | Kiracı bulundu, ancak tam olarak eklemedi.         |
| Uygun değil, Temsilci erişimi gerekiyor | Temsili Yönetici Ayrıcalıkları (DAP) kurulumu gereklidir. |
| Uygun değil, Eksik gerekli lisans  | Kiracının gerekli lisansı yoktur.              |
| Uygun değil, Kullanıcı sayısı aşıldı       | Kiracıda izin verilenden daha fazla kullanıcı var.                 |
| Uygun değil, Sözleşme türü             | Kiracının bir sözleşmesi yok.                    |

Kiracıyı devre dışı bırakıncaya kadar, devre dışı bırakma işlemi tamamlandıktan sonra kiracı üzerinde eyleme geçesiniz. Devre dışı bırakmanın tamamlanması 48 saat kadar sürebilir. Kiracıyı yeniden etkinleştirmeye karar verirsiniz, verilerin yeniden 48 saat kadar sürebilir.

## <a name="tenant-tags"></a>Kiracı etiketleri

Kiracılarınızı düzenlemeye ve var olan görünümleri kolayca filtrelemeye yardımcı olmak için, kiracılarınızı etiketler oluşturabilir ve atabilirsiniz. Daha fazla bilgi edinmek için bkz [. Kiracı listenizi yönetme](m365-lighthouse-manage-tenant-list.md).

> [!NOTE]
> Tüm kiracılarda en çok 30 etiket oluşturabilirsiniz.


## <a name="tenant-details-page"></a>Kiracı ayrıntıları sayfası

Ayrıntılı kiracı bilgilerini görüntülemek için kiracı listesinden bir kiracı seçin. Kiracı ayrıntıları sayfası kişi bilgilerini ve dağıtım planı durumunu içerir.


:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-details-page.png" alt-text="Kiracı ayrıntıları sayfasının ekran görüntüsü.":::

### <a name="overview-tab"></a>Genel Bakış sekmesi

Genel Bakış sekmesinde kiracıya genel bakış, iletişim bilgileri ve hizmet Microsoft 365 görüntüleyebilirsiniz.

#### <a name="tenant-overview-card"></a>Kiracı genel bakış kartı

Kiracıya genel bakış kartı kiracı hakkında kendi hesaplarından bilgi Microsoft 365 sağlar.

| Kiracı Bilgileri    | Açıklama|
|-----------------------|------------------|
| Genel Müdürlük    | Kiracının bulunduğu yer.|
| Endüstri    |Kuruluşun sektörü.|
| Web sitesi    |Kuruluşun web sitesi. Veri sağlanamıyorsa bu alanı düzenleyebilirsiniz.|
| Müşteri etki alanı    |Kuruluşun etki alanı.|
| Toplam kullanıcı    |Kiracıya atanan kullanıcı sayısı. Bu numarayı seçerek o kiracının Kullanıcılar sayfasını açabilirsiniz.|
| Toplam cihaz sayısı|Kiracıya kayıtlı cihaz sayısıdır. Bu numarayı seçerek ilgili kiracının Cihazlar sayfasını açabilirsiniz.|

#### <a name="contacts-card"></a>Kişi kartı

Kişi kartı, yönetmekte olduğu kiracılar içindeki önemli kişiler için aşağıdakiler gibi bilgileri girmenize olanak sağlar:

- Name
- Başlık
- Phone
- E-posta
- Notlar

Notlar bölümü, kiracının görev atama tercihleri, konum, saat dilimi ve kuruluş içindeki rolüyle ilgili ayrıntılar gibi önemli bilgileri kaydetmek için kullanabileceğiniz bir metin alanıdır.

Ayrıntıları düzenlemek veya mevcut bir kişinin adını silmek için, listeden kişi adını seçin. Kişi **düzenle bölmesinde** , kişi düzenleyin veya silin. Başka bir kişi eklemek için **+Kişi ekle'yi seçin**.

#### <a name="microsoft-365-usage-card"></a>Microsoft 365 kartı

Deniz Feneri, bir Microsoft 365 dahil olmak üzere her bir hizmetin lisanslı ve etkin kullanımı dahil olmak üzere çeşitli hizmetler kullanımına genel bakış sağlar. Etkin, son 28 günde hizmette en az bir kez oturum alan kullanıcı veya cihaz sayısını gösterir. Değişiklik, etkin kullanıcılar ve cihazlarda geçen aydan bu yana yapılan değişikliği gösterir.

Sayfa Microsoft 365 kartı iki bölümden oluşur:

- Microsoft 365 Lighthouse etkin hizmetler – Deniz Feneri portalı içinde yönetillayabilecek hizmetler.
- Ek Microsoft 365 Hizmetleri – Microsoft 365 paketine dahil olan, ancak şu anda Microsoft 365 Lighthouse portalında yönetil Microsoft 365 Lighthouse Hizmetler.


### <a name="deployment-plans-tab"></a>Dağıtım Planları sekmesi

Dağıtım Planları sekmesi kiracının dağıtım planında durum sağlar. Listede yer alan dağıtım adımları, kiracıya uygulanan taban çizgisine göre uygulanır. Dağıtım adımı ayrıntılarını görmek için, listeden bir dağıtım adımı seçin.

Dağıtım Planları sekmesi aşağıdaki seçenekleri de içerir:

- **Dışarı aktar:** Dağıtım adımı verilerini virgülle ayrılmış değerler (Excel) dosyasına dışarı .csv seçin.
- **Yenile:** En güncel dağıtım adımı verilerini almak için bunu seçin.
- **Arama:** Listede belirli bir dağıtım adımını hızla bulmak için anahtar sözcükleri girin.

## <a name="related-content"></a>İlgili içerik

[Sistem Gereksinimleri Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)\
[Kiracı listenizi yönetme](m365-lighthouse-manage-tenant-list.md) (makale)\
[Standart kiracı yapılandırmalarını dağıtmak için taban çizgilerini kullanmaya genel bakış](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (makale)\
[Temel Microsoft 365 Lighthouse dağıtma](m365-lighthouse-deploy-baselines.md) (makale)
