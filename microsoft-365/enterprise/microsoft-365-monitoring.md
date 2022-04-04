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
description: Bu Microsoft 365 olaylar veya danışmanlar hakkında bilgi için izleme Microsoft 365.
ms.openlocfilehash: 2d78bcae258730e1b48c7d6cc77fa5ae2b200b07
ms.sourcegitcommit: 0ae89b71b202aceabd5061f0d5b46d030d93e931
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2022
ms.locfileid: "64520861"
---
# <a name="learn-about-microsoft-365-monitoring"></a>İzleme hakkında Microsoft 365 öğrenin

Microsoft 365 yönetim merkezi'da, [Microsoft hizmetleri](https://go.microsoft.com/fwlink/p/?linkid=2024339) aboneliğiyle ilgili çeşitli Microsoft hizmetleri için panoları Microsoft 365 kullanabilirsiniz. Bu özellik ilk başta Exchange Online Microsoft hizmetleri ile başladı ve şimdi Microsoft Teams, Microsoft 365 Uygulamaları gibi diğer hizmetlere de genişletildi. İzleme, bu kategorilerde toplanan olaylar ve tavsiyeler hakkında size bilgi sağlar:

- **Altyapı**. Sorun, Microsoft'un Microsoft 365 güncelleştirmeleri sağlamak ve sorunu çözmek için sahip olduğu yeni bir altyapıda algılandı. Örneğin, e-posta Exchange Online bulut altyapısıyla ilgili sorunlar nedeniyle Exchange kullanıcılar Microsoft 365 erişeni değildir.

- **Üçüncü taraf altyapısı**. Sorun, organizasyon tarafından bağımlılık yapılan üçüncü taraf altyapıda algılanır ve çözüm için kuruluştan işlem gerektirir. Örneğin, kullanıcı kimlik doğrulama işlemleri, kullanıcıların üçüncü taraf güvenlik belirteci hizmetine (STS) bağlanmasını engelleyen bir üçüncü taraf güvenlik belirteci hizmeti (STS) sağlayıcısı tarafından Exchange Online.

- **Müşteri altyapısı**. Sorun, kuruluş altyapıda algılanır ve çözüm için kuruluştan işlem gerektirir. Örneğin, süresi dolan bir sertifika Exchange Online, organizasyon tarafından barındırılan STS sağlayıcısından bir kimlik doğrulama belirteci alamamakta olduğundan kullanıcılar Exchange Online erişim sağ yapamazlar.

İşte, Kuruluş senaryoları Hizmet durumu öncelik hesap  senaryoları için Microsoft 365 yönetim merkezi'de  >  bulunan Hizmet durumu [sayfası örneği.](../admin/setup/priority-accounts.md)

![Sayfa Hizmet durumu Sayfa Son Microsoft 365 yönetim merkezi.](../media/microsoft-365-exchange-monitoring/service-health-dashboard-example.png)

**Organizasyonla ilgili sorunlar,** kuruluş düzeyinde izleme ve öncelik hesabı izleme tarafından tanımlanır ve kullanılır.

Kurumdaki sorunlar'ın altındaki Sistem  Durumu sütununu değeri, kuruluş altyapısının mı yoksa üçüncü taraf yazılımının kuruluş kullanıcılarının ve/veya öncelik hesaplarının hizmet durumu deneyimini etkileyeceğini Exchange Online. Danışmanlar veya olaylar için, eylemlerinizin çözümü gerekir.

**Microsoft** hizmet durumu **altındaki Sistem** Durumu sütununu değeri, hizmetin iyi olduğunu ya da Microsoft'un bakımınıta olduğu bulut hizmetlerini temel alan danışmanlara veya olaylara sahip olduğunu gösterir.

aşağıdaki örnekte, Microsoft 365 yönetim merkezi'de sistem durumu  > **Exchange Online** >  ndan kullanılabilen kuruluş düzeyi ve öncelik hesabı senaryolarının durumunu gösteren Exchange Online izleme sayfası Hizmet durumu **Exchange Online**.

![Denetim İzleme için kuruluş Exchange Online senaryoları.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-org-scenarios.png)

Senaryo listesi sayfasında, Microsoft hizmetinin iyi durumda olup olmadığını ve ilişkili olay veya danışma olup olmadığını görebilirsiniz. Örneğin, Exchange Online izleme ile belirli e-posta senaryolarının hizmet durumuna göz atabilirsiniz ve kuruluş düzeyi senaryolarına göre etkiyi belirlemek için gerçek zamanlı sinyallerin yakınına bakabilirsiniz. Ayrıca, varsa öncelik hesabı senaryolarının durumunu da öğrenebilirsiniz.

## <a name="requirements-for-monitoring"></a>İzleme gereksinimleri

Bu önizleme, aşağıdaki gereksinimleri karşıleyen müşteriler için etkinleştirilmiştir:

- Şu ürünlerin bir veya birleşiminden en az 5.000 lisans sayısına sahip olması gerekir: Office 365 E3, Microsoft 365 E3, Office 365 E5 veya Microsoft 365 E5.

   Örneğin, kuruluşta uygun ürünlerden toplam 5.500 Office 365 E3, 2.500 Microsoft 365 E5 olmak üzere 3.000 Microsoft 365 E5 lisansı olabilir.

- Bir veya birden çok temel Microsoft 365 hizmeti için, örneğin Microsoft Teams, OneDrive İş, SharePoint Online, Exchange Online ve diğer uygulamaları içeren en az 50 aylık etkin Office vardır.

- Hizmet Durumu Panosu düzeyinde izinlere sahip olan her rol, Sistem Durumu Exchange Online erişim sağlar. Daha fazla bilgi için bkz. [Microsoft 365 hizmet durumunu denetleme](view-service-health.md).

## <a name="additional-monitoring-for-microsoft-services"></a>Destek için ek Microsoft hizmetleri

Hizmete özgü izleme, aşağıdaki denetimler için de Microsoft hizmetleri. Bu hizmeti izleme hakkında daha fazla bilgi edinmek için ilgili bağlantıyı seçin.

- [Exchange Online](microsoft-365-exchange-monitoring.md)

- [Microsoft 365 Uygulamaları](microsoft-365-apps-monitoring.md)

- [Microsoft Teams](microsoft-365-teams-monitoring.md)

## <a name="send-us-feedback"></a>Bize geri bildirim gönderin

Geri bildirim sağlamanın iki yolu vardır:

- Sayfanın **her sayfasında** bulunan Geri bildirim ver seçeneğini Microsoft 365 yönetim merkezi.

- **Bu gönderi yardımcı mı? bağlantısına tıklayın.

  !["Bu gönderi yardımcı mı?" bağlantısına tıklayın.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-example-incident-feedback.png)

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="1-why-dont-i-see-view-link-under-organizational-monitoring-column-in-the-microsoft-365-admin-center-inside-service-health"></a>1. Hizmet Durumu içindeki Kuruluş izleme sütununu altında neden "görüntüle" Microsoft 365 yönetim merkezi göremiyorum?

İlk olarak, yönetim sayfasının Giriş sayfasındaki yeni yönetim **merkezini etkinleştirmiş** [Microsoft 365 yönetim merkezi.](https://go.microsoft.com/fwlink/p/?linkid=2024339)

Ardından, aşağıdaki iki gereksinimlerin ikisini de karşılamıyor olun:

- Şu ürünlerin bir veya birleşiminden en az 5.000 lisans sayısına sahip olması gerekir: Office 365 E3, Microsoft 365 E3, Office 365 E5 veya Microsoft 365 E5.

- Bir veya birden çok temel Microsoft 365 hizmeti için, örneğin Microsoft Teams, OneDrive İş, SharePoint Online, Exchange Online ve diğer uygulamaları içeren en az 50 aylık etkin Office vardır.

Kuruluş lisans sayısı 5.000'in altında ise ve temel hizmetlerde aylık etkin kullanıcılar 50'nin altına düştüğünde, bu gereksinimler karşılanana kadar Exchange Online izleme etkinleştirilmez.

### <a name="2-will-there-be-other-monitoring-scenarios-for-other-services-in-future"></a>2. Gelecekte diğer hizmetler için başka izleme senaryoları da olacak mı?

Evet. Genel önizlemede şimdi birkaç hizmetimiz daha var. Etki alanı diğer hizmetlere genişletmeye devam edeceğiz.

### <a name="3-what-is-the-plan-for-general-availability-of-this-experience"></a>3. Bu deneyimin genel olarak kullanılabilirliği planı nedir?

Microsoft'un planı, önizleme deneyimiyle ilgili geri bildirimlerinizi toplamak ve ardından genel kullanılabilirlik için planlarımızı tanımlamaktır.

### <a name="4-is-this-a-free-included-or-paid-extra-feature"></a>4. Bu ücretsiz (dahil) veya ücretli (ek) bir özellik mi?

Bu, önizlemede olan ücretsiz bir özelliktir ve yalnızca soru 1. soruda gereksinimleri karşı olan müşteriler tarafından kullanılabilir. Bu içeriği almak için ücretli bir seçenek yok.

### <a name="5-how-do-i-provide-feedback"></a>5. Geri Nasıl yaparım? sağlamak mı?

Genel geri bildirim için, **izleme** sayfasının sağ alt köşesindeki Geri bildirim ver simgesini kullanın.

Olay veya tavsiyeler hakkında geri bildirim almak için **Bu gönderi yardımcı mı? bağlantısına tıklayın.

### <a name="6-are-there-any-privacy-concerns"></a>6. Gizlilikle ilgili bir endişeniz var mı?

Hizmet meta verilerine ve kullanıcı içeriğine odaklanmayı izleme izlenz.
