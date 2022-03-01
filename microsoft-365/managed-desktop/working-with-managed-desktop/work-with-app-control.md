---
title: Uygulama denetimi ile çalışma
description: ''
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: b87da099ace71b13b03bb9d9247bc4cbfe420dc4
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63014284"
---
# <a name="work-with-app-control"></a>Uygulama denetimi ile çalışma

Uygulama denetimi ortamınıza dağıtıldıktan sonra, hem sizin hem de Microsoft Tarafından Yönetilen Masaüstü İşlemlerinin sorumlulukları devam eder. Örneğin, ortamda yeni bir uygulama eklemek veya güvenilir bir imzacı eklemek (veya kaldırmak) istiyor olabilir. Güvenliği geliştirmek için, tüm uygulamaları kullanıcılara bırakmadan önce kodla imzalanmış olması gerekir. Bir uygulamanın yayıncı ayrıntılarında imzacı hakkında bilgiler yer içerir.

## <a name="add-a-new-app"></a>Yeni uygulama ekleme

**Yeni uygulama eklemek için:**

1. Uygulamayı Uygulama [Ekle'Microsoft Intune](/mem/intune/apps/apps-win32-app-management).
1. Uygulamayı Test halkası'nın herhangi bir cihazına dağıtın.
1. Uygulamalarınızı standart iş süreçlerinize göre test edin.
1. Uygulama ve Hizmet Günlükleri **\Microsoft\Windows\AppLocker altında Olay Görüntüleyicisi'ni kontrol edin**. Herhangi bir **8003 veya** **8006 olaylarını** bakın. Bu olaylar uygulamanın engellenmiş olacağını gösteriyor. Uygulama Dolabı etkinlikleri ve anlamları hakkında daha fazla bilgi için bkz. [AppLocker ile Olay Görüntüleyicisi'ni kullanma](/windows/security/threat-protection/windows-defender-application-control/applocker/using-event-viewer-with-applocker).
1. Bu olaylardan herhangi birini bulursanız, Microsoft Tarafından Yönetilen Masaüstü İşlemleri ile bir imzacı isteği açın.

## <a name="add-or-remove-a-trusted-signer"></a>Güvenilir imzacı ekleme (veya kaldırma)

İmzacı isteğini açarken, önce bazı önemli yayıncı ayrıntılarını sağlaytınız.

**Güvenilir imzacı eklemek (veya kaldırmak) için:**

1. [Yayıncı ayrıntılarını toplayın](#gather-publisher-details).
1. İmzacı kuralını talep etmek ve aşağıdaki ayrıntıları eklemek için Microsoft Yönetilen Masaüstü İşlemleri'nin olduğu bir bilet açın:  
    - Uygulama adı
    - Uygulama sürümü
    - Açıklama
    - Türü değiştirme ("ekleme" veya "kaldırma")  
    - Publisher (örneğin: "O=<publisher name>,L=<location>,S=Eyalet,C=Ülke")

> [!NOTE]
> Bir uygulamanın güvenlerini kaldırmak için aynı adımları izleyin, ancak Değişiklik türünü **kaldırılacak şekilde** *ayarlayın*.

İşlemler, ilkeleri bu zamanlamayı takip eden dağıtım gruplarına aşamalı olarak dağıtır:

|Dağıtım grubu  |İlke türü  |Zamanlama  |
|---------|---------|---------|
|Test     |  Denetim       |  0. Gün       |
|Birinci     | Zorunlu        | 1. Gün        |
|Hızlı     | Zorunlu        |  2. Gün       |
|Geniş     | Zorunlu        |  3. Gün       |

Dağıtım sırasında istediğiniz zaman dağıtımı duraklatabilir veya geri dönebilirsiniz. Duraklatmak veya geri almak için Microsoft Tarafından Yönetilen Masaüstü İşlemleri ile başka bir destek isteği açın.

> [!NOTE]
> İmzalayan kuralın yayımlarını duraklatmak için, başka bir sürümün başlatılamadan önce bu kuralın geri yuvarlanmış veya tamamlanması gerekir.

## <a name="gather-publisher-details"></a>Yayıncı ayrıntılarını toplama

**Bir uygulamanın yayımcı verilerine erişmek için:**

1. Denetim Modu ilkesi uygulanmış bir Test halkası içinde Microsoft Yönetilen Masaüstü cihazı bulun.
1. Uygulamayı cihaza yükleme girişimi.
1. Bu cihazda Olay Görüntüleyicisi'ni açın.
1. Olay Görüntüleyicisi'nde Uygulama ve Hizmet **Günlükleri\Microsoft\Windows'a gidin** ve **AppLocker'ı seçin**.
1. Herhangi bir **8003 veya** **8006** olayı bulun ve ardından etkinlikten bilgileri kopyalayın:
    - Uygulama adı
    - Uygulama sürümü
    - Açıklama
    - Publisher (örneğin: "O=<publisher name>, L=<location>, S=Eyalet, C=Ülke")
