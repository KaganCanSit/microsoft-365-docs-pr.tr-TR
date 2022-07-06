---
title: Microsoft 365 Defender'de Microsoft Defender for Cloud Apps (Önizleme)
description: Microsoft Defender for Cloud Apps Microsoft 365 Defender değişiklikleri hakkında bilgi edinin
keywords: Microsoft 365 Defender kullanmaya başlama, Microsoft Defender for Cloud Apps
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dacurwin
author: dcurwin
manager: dansimp
ms.date: 05/03/2022
audience: ITPro
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: 9113e3f06ba0f9c8cbec0da6d738cc170a215771
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617040"
---
# <a name="microsoft-defender-for-cloud-apps-in-microsoft-365-defender-preview"></a>Microsoft 365 Defender'de Microsoft Defender for Cloud Apps (Önizleme)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Bulut Uygulamaları için Microsoft Defender](/defender-cloud-apps/)

Microsoft Defender for Cloud Apps artık Microsoft 365 Defender bir parçasıdır. Microsoft 365 Defender portalı, güvenlik yöneticilerinin güvenlik görevlerini tek bir konumda gerçekleştirmesine olanak tanır. Bu, iş akışlarını basitleştirir ve diğer Microsoft 365 Defender hizmetlerinin işlevselliğini ekler. Microsoft 365 Defender Microsoft kimlikleriniz, verileriniz, cihazlarınız, uygulamalarınız ve altyapınız genelinde güvenliği izlemeye ve yönetmeye ev sahipliği yapacaktır.

SOC analistleri bulut uygulamaları da dahil olmak üzere tüm Microsoft 365 Defender iş yüklerini önceliklendirme, araştırma ve avlayabilme olanağına sahiptir.
Cloud Apps için Defender uyarıları Microsoft 365 Defender'ın olay kuyruğunda ve uyarılar kuyruğunda görünmeye devam edecektir, ancak artık Microsoft 365 Defender portalında bulunan uyarı sayfalarının içindeki ilgili içerik, her uyarı türüne uygun uyarlamalarla birleşik bir biçimde görünür.

Microsoft 365 Defender bir <https://security.microsoft.com>göz atın.

Avantajlar hakkında daha fazla bilgi edinin: [Microsoft 365 Defender genel bakış](microsoft-365-defender.md).

## <a name="quick-reference"></a>Hızlı başvuru

Aşağıdaki resimde ve tabloda Microsoft Defender for Cloud Apps ile Microsoft 365 Defender arasındaki gezinti değişiklikleri listelenmiştir.

> [!NOTE]
> Bazı sayfalar henüz geçirilmemiş ve Bulut Uygulamaları için Defender portalından erişilmelidir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/defender-cloud-apps-m365-defender.png" alt-text="Microsoft 365 Defender portalındaki yeni konumlar" lightbox="../../media/defender-cloud-apps-m365-defender.png":::

| Bulut Uygulamaları için Defender | Microsoft 365 Defender |
|---------|---------|
| Cloud Discover panosu | Bulut uygulamaları -> Bulut bulma |
| Bulunan Uygulamalar | Cloud Discovery sayfasındaki sekme |
| Bulunan kaynaklar | Cloud Discovery sayfasındaki sekme |
| IP adresleri | Cloud Discovery sayfasındaki sekme |
| Kullanıcılar | Cloud Discovery sayfasındaki sekme |
| Aygıtları | Cloud Discovery sayfasındaki sekme |
| Bulut uygulaması kataloğu |  Bulut uygulamaları -> Bulut uygulaması kataloğu |
| Cloud Discovery anlık görüntü raporu oluşturma | Cloud Discovery sayfasındaki Eylemler'in altında |
| Etkinlik günlüğü | Bulut uygulamaları -> Etkinlik günlüğü |
| Dosyalar | Cloud Apps için Defender portalında kalan |
| Kullanıcılar ve hesaplar | Varlıklar -> Kimlikleri |
| Güvenlik yapılandırması | Cloud Apps için Defender portalında kalan |
| Kimlik güvenliği duruşu | [Kimlik için Microsoft Defender kimlik güvenliği duruş değerlendirmeleri](/defender-for-identity/isp-overview) |
| OAuth uygulamaları | Bulut uygulamaları -> OAuth uygulamaları |
| Bağlı uygulamalar | Cloud Apps için Defender portalında kalan |

> [!NOTE]
> Microsoft 365 Defender portalındaki yeni Cloud Apps için Defender deneyimi, şu anda [Yönetici erişimini yönetme](/defender-cloud-apps/manage-admins) bölümünde ayrıntılı olarak belirtilen tüm kullanıcılar tarafından kullanılabilir:
> * Cloud [Apps için Defender'daki Yerleşik yönetici rollerinde](/defender-cloud-apps/manage-admins#built-in-admin-roles-in-defender-for-cloud-apps) tanımlandığı gibi **Uygulama/Örnek yöneticisi**, **Kullanıcı grubu yöneticisi**, Cloud **Discovery genel** yöneticisi ve Cloud **Discovery rapor yöneticisi**.
> * Etkinlik gizliliği bölümünde tanımlanan kullanıcı [gizlilik](/defender-cloud-apps/activity-privacy) grupları

## <a name="whats-changed"></a>Değişenler

Cloud Apps için Defender ve Microsoft 365 Defender tümleştirmesiyle birlikte gelen değişiklikler hakkında bilgi edinin.

### <a name="global-search"></a>Genel arama

Microsoft 365 Defender'da genel arama (sayfanın üst kısmındaki arama çubuğunu kullanarak) artık ek bir aranabilir varlık içerir: Cloud Apps için Defender'da bağlı uygulamaları aramanıza olanak tanır.

:::image type="content" source="../../media/global-search-apps.png" alt-text="Bağlı uygulamaları arayın.":::

### <a name="assets-and-identities"></a>Varlıklar ve kimlikler

Microsoft 365 Defender deneyiminin tamamına yayılan ayrılmış **varlıklar** bölümünün oluşturulması kapsamında, Bulut Uygulamaları için Defender'ın **Kullanıcılar ve Hesaplar** bölümü **Kimlikler** bölümü olarak yeniden adlandırılır. İşlevlerde değişiklik beklenmiyor.

## <a name="related-information"></a>İlgili bilgiler

- [Microsoft 365 Defender](microsoft-365-defender.md)
