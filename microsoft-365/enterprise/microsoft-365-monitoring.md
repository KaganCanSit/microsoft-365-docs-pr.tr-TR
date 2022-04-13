---
title: Microsoft 365 izleme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: mediumn
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: admindeeplinkMAC
f1.keywords:
- NOCSH
description: Microsoft 365'daki olaylar veya öneriler hakkında bilgi için Microsoft 365 izlemeyi kullanın.
ms.openlocfilehash: 47f54859d7dd0973814a0ad9229a902bddcb8587
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824848"
---
# <a name="learn-about-microsoft-365-monitoring"></a>Microsoft 365 izleme hakkında bilgi edinin

Kuruluşunuzun Microsoft 365 aboneliğinde çeşitli [Microsoft hizmetleri](https://go.microsoft.com/fwlink/p/?linkid=2024339) durumunu izlemek için Microsoft 365 yönetim merkezi panoları kullanabilirsiniz. Bu özellik başlangıçta Exchange Online ile başlatıldı ve gelecekte Microsoft Teams, Microsoft 365 Uygulamaları ve daha fazla hizmet gibi diğer Microsoft hizmetleri genişletildi. İzleme, şu kategorilerde toplanan olaylar ve öneriler hakkında bilgi sağlar:

- **Altyapı**. Microsoft'un sahip olduğu Microsoft 365 altyapısında düzenli güncelleştirmeler sağlamak ve sorunu çözmek için sorun algılandı. Örneğin, Exchange veya diğer Microsoft 365 bulut altyapısıyla ilgili sorunlar nedeniyle kullanıcılar Exchange Online erişemiyor.

- **Üçüncü taraf altyapı**. Sorun, kuruluşunuzun bağımlılık aldığı ve çözüm için kuruluşunuzdan eylem gerektirdiği üçüncü taraf altyapıda algılanır. Örneğin, kullanıcı kimlik doğrulama işlemleri, kullanıcıların Exchange Online bağlanmasını engelleyen bir üçüncü taraf güvenlik belirteci hizmeti (STS) sağlayıcısı tarafından kısıtlanıyor.

- **Müşteri altyapısı**. Sorun kuruluşunuzun altyapısında algılanır ve çözüm için kuruluşunuzdan eylem yapılmasını gerektirir. Örneğin, süresi dolmuş bir sertifika nedeniyle kuruluşunuz tarafından barındırılan STS sağlayıcısından kimlik doğrulama belirteci alamadıkları için kullanıcılar Exchange Online erişemez.

Aşağıda, Microsoft 365 yönetim merkezi kuruluş senaryoları ve [öncelik hesabı](../admin/setup/priority-accounts.md) senaryoları için **Sistem Durumu** >  **Hizmet durumu** sayfasında bulunan **Hizmet durumu sayfasının bir** örneği verilmiştir.

![Microsoft 365 yönetim merkezi Hizmet durumu sayfası.](../media/microsoft-365-exchange-monitoring/service-health-dashboard-example.png)

**Kuruluşunuzdaki sorunlar** , kuruluş düzeyinde izleme ve öncelik hesabı izleme tarafından belirlenir ve kullanılır.

**Kuruluşunuzdaki sorunlar** altındaki **Sistem Durumu** sütununun değeri, kuruluşunuzun altyapısının veya üçüncü taraf yazılımının kuruluşunuzun kullanıcılarının ve/veya Exchange Online öncelik hesaplarının hizmet durumu deneyimini etkileyip etkilemediğini gösterir. Öneriler veya olaylar için eylemlerinizin çözümlenmesi gerekir.

**Microsoft hizmet** durumu altındaki **Sistem Durumu** sütununun değeri, hizmetin iyi durumda olduğunu veya Microsoft'un koruduğu bulut hizmetlerini temel alan önerilere veya olaylara sahip olduğunu gösterir.

Burada, Microsoft 365 yönetim merkezi'daki Exchange Online izleme sayfasının **, Health** >  **Hizmet durumu Exchange Online'da** >  sağlanan kuruluş düzeyi ve öncelik hesabı senaryolarının durumunu gösteren bir örneği verilmiştir **.**

![Exchange Online İzleme için kuruluş düzeyinde senaryolar.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-org-scenarios.png)

Senaryo listesi sayfasıyla, Microsoft hizmetinin iyi durumda olup olmadığını ve ilişkili olaylar veya öneriler olup olmadığını görebilirsiniz. Örneğin, Exchange Online izleme ile belirli e-posta senaryolarının hizmet durumuna bakabilir ve kuruluş düzeyinde senaryoya göre etkiyi belirlemek için neredeyse gerçek zamanlı sinyalleri görüntüleyebilirsiniz. Varsa, öncelik hesabı senaryolarının sistem durumunu da görebilirsiniz.

## <a name="requirements-for-monitoring"></a>İzleme gereksinimleri

Bu önizleme, aşağıdaki gereksinimleri karşılayan müşteriler için etkinleştirilir:

- Kuruluşunuzun şu ürünlerin bir veya bir birleşiminden en az 5.000 lisans sayısına sahip olması gerekir: Office 365 E3, Microsoft 365 E3, Office 365 E5 veya Microsoft 365 E5.

   Örneğin, kuruluşunuzda 3.000 Office 365 E3 lisansı ve uygun ürünlerden toplam 5.500 lisans için 2.500 Microsoft 365 E5 olabilir.

- Kuruluşunuzun Microsoft Teams, OneDrive İş, SharePoint Online, Exchange Online ve Office uygulamaları içeren bir veya daha fazla temel Microsoft 365 hizmeti için en az 50 aylık etkin kullanıcısı olmalıdır.

- Hizmet Durumu Panosu düzeyinde izinlere sahip herhangi bir rol Exchange Online İzleme'ye erişebilir. Daha fazla bilgi için bkz. [Microsoft 365 hizmet durumunu denetleme](view-service-health.md).

## <a name="additional-monitoring-for-microsoft-services"></a>Microsoft hizmetleri için ek izleme

Hizmete özgü izleme, aşağıdaki Microsoft hizmetleri için de etkinleştirilir. İlgili hizmetin izlenmesi hakkında daha fazla bilgi edinmek için ilgili bağlantıyı seçin.

- [Exchange Online](microsoft-365-exchange-monitoring.md)

- [Microsoft 365 Uygulamaları](microsoft-365-apps-monitoring.md)

- [Microsoft Teams](microsoft-365-teams-monitoring.md)

## <a name="send-us-feedback"></a>Bize geri bildirim gönderin

Geri bildirim sağlamanın iki yolu vardır:

- Microsoft 365 yönetim merkezi her sayfasında bulunan **Geri bildirim ver** seçeneğini kullanın.

- **Bu gönderi yararlı mı? bağlantısına tıklayın.

  !["Bu gönderi yararlı mı?" bağlantısına tıklayın.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-example-incident-feedback.png)

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="1-why-dont-i-see-view-link-under-organizational-monitoring-column-in-the-microsoft-365-admin-center-inside-service-health"></a>1. Hizmet Durumu'nun içindeki Microsoft 365 yönetim merkezi Kuruluş izleme sütununun altında "görüntüle" bağlantısını neden göremiyorum?

İlk olarak, [Microsoft 365 yönetim merkezi](https://go.microsoft.com/fwlink/p/?linkid=2024339) **Giriş** sayfasında yeni yönetim merkezini etkinleştirdiğinizden emin olun.

Ardından aşağıdaki gereksinimlerin ikisini de karşıladığınızdan emin olun:

- Kuruluşunuzun şu ürünlerin bir veya bir birleşiminden en az 5.000 lisans sayısına sahip olması gerekir: Office 365 E3, Microsoft 365 E3, Office 365 E5 veya Microsoft 365 E5.

- Kuruluşunuzun Microsoft Teams, OneDrive İş, SharePoint Online, Exchange Online ve Office uygulamaları içeren bir veya daha fazla temel Microsoft 365 hizmeti için en az 50 aylık etkin kullanıcısı olmalıdır.

Kuruluşunuz için lisans sayısı 5.000 kullanıcının altına düşerse ve aylık etkin kullanıcılar çekirdek hizmetlerde 50 kullanıcının altına düşerse, Exchange Online izleme bu gereksinimler karşılanana kadar etkinleştirilmez.

### <a name="2-will-there-be-other-monitoring-scenarios-for-other-services-in-future"></a>2. Gelecekte diğer hizmetler için başka izleme senaryoları olacak mı?

Evet. Genel önizlemede birkaç hizmetimiz daha var. Ayak izini diğer hizmetlere genişletmeye devam edeceğiz.

### <a name="3-what-is-the-plan-for-general-availability-of-this-experience"></a>3. Bu deneyimin genel kullanıma sunulma planı nedir?

Microsoft'un planı, önizleme deneyimiyle ilgili geri bildiriminizi toplamak ve ardından genel kullanılabilirlik planımızı tanımlamaktır.

### <a name="4-is-this-a-free-included-or-paid-extra-feature"></a>4. Bu ücretsiz (dahil) veya ücretli (ekstra) bir özellik mi?

Bu, önizleme aşamasında olan ve yalnızca söz konusu 1. gereksinimlerini karşılayan müşteriler tarafından kullanılabilen ücretsiz bir özelliktir. Bu içeriği almak için ücretli bir seçenek yoktur.

### <a name="5-how-do-i-provide-feedback"></a>5. Geri bildirim sağlamak Nasıl yaparım??

Genel geri bildirim için, izleme sayfasının sağ alt köşesindeki **Geri bildirim ver** simgesini kullanın.

Olaylar veya öneriler hakkında geri bildirim için **Bu gönderi yararlı mı? Bağlantı.

### <a name="6-are-there-any-privacy-concerns"></a>6. Gizlilikle ilgili herhangi bir endişe var mı?

İzleme, hizmet meta verilerine odaklanır ve kullanıcı içeriği izlenmez.
