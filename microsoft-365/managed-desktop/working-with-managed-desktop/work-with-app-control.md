---
title: Uygulama denetimi ile çalışma
description: Uygulama denetimi yönetmeyi öğrenin.
keywords: Microsoft Managed Desktop, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: 99979a08a67245d471b33ce26e4b7f35790fead5
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569919"
---
# <a name="work-with-app-control"></a>Uygulama denetimi ile çalışma

Uygulama denetimi ortamınıza dağıtıldıktan sonra, hem siz hem de Microsoft Managed Desktop devam eden sorumluluklara sahip olursiniz. Örneğin, ortamda yeni bir uygulama eklemek veya güvenilir bir imzacı eklemek (veya kaldırmak) istiyor olabilir. Güvenliği geliştirmek için, tüm uygulamaları kullanıcılara bırakmadan önce kodla imzalanmış olması gerekir. Bir uygulamanın yayıncı ayrıntılarında imzacı hakkında bilgiler yer içerir.

## <a name="add-a-new-app"></a>Yeni uygulama ekleme

**Yeni uygulama eklemek için:**

1. Uygulamayı Uygulama [Ekle'Microsoft Intune](/mem/intune/apps/apps-win32-app-management).
1. Uygulamayı Test halkası'nın herhangi bir cihazına dağıtın.
1. Uygulamalarınızı standart iş süreçlerinize göre test edin.
1. **Uygulama Olay Görüntüleyicisi Günlükleri\Microsoft\Windows\AppLocker altındaki onay kutusunu kontrol edin**. Herhangi bir **8003 veya** **8006 olaylarını** bakın. Bu olaylar uygulamanın engellenmiş olacağını gösteriyor. Uygulama Dolabı etkinlikleri ve anlamları hakkında daha fazla bilgi için bkz. [AppLocker ile Olay Görüntüleyicisi'ı kullanma](/windows/security/threat-protection/windows-defender-application-control/applocker/using-event-viewer-with-applocker).
1. Bu olaylardan herhangi birini bulursanız, İmzala İşlemleri ile bir Microsoft Managed Desktop açın.

## <a name="add-or-remove-a-trusted-signer"></a>Güvenilir imzacı ekleme (veya kaldırma)

İmzacı isteğini açarken, önce bazı önemli yayıncı ayrıntılarını sağlaytınız.

**Güvenilir imzacı eklemek (veya kaldırmak) için:**

1. [Yayıncı ayrıntılarını toplayın](#gather-publisher-details).
1. İmza kuralı talep etmek ve aşağıdaki Microsoft Managed Desktop eklemek için Kayıt İşlemleri olan bir bilet açın:  
    - Uygulama adı
    - Uygulama sürümü
    - Açıklama
    - Türü değiştirme ("ekleme" veya "kaldırma")  
    - Publisher (örneğin: `O=<publisher name>,L=<location>,S=State,C=Country`)

> [!NOTE]
> Bir uygulamanın güvenlerini kaldırmak için aynı adımları izleyin, ancak Değişiklik türünü **kaldırılacak şekilde** *ayarlayın*.

İşlemler, ilkeleri bu zamanlamayı takip eden dağıtım gruplarına aşamalı olarak dağıtır:

|Dağıtım grubu|İlke türü|Zamanlama|
|---|---|---|
|Test|Denetim|0. Gün|
|Birinci|Zorunlu|1. Gün|
|Hızlı|Zorunlu|2. Gün|
|Geniş|Zorunlu|3. Gün|

Dağıtım sırasında istediğiniz zaman dağıtımı duraklatabilir veya geri dönebilirsiniz. Duraklatmak veya geri almak için, Destek İşlemleri ile başka bir Microsoft Managed Desktop açın.

> [!NOTE]
> İmzalayan kuralın yayımlarını duraklatmak için, başka bir sürümün başlatılamadan önce bu kuralın geri yuvarlanmış veya tamamlanması gerekir.

## <a name="gather-publisher-details"></a>Yayıncı ayrıntılarını toplama

**Bir uygulamanın yayımcı verilerine erişmek için:**

1. Test Microsoft Managed Desktop denetim modu ilkesi uygulanmış bir cihaz bulun.
1. Uygulamayı cihaza yükleme girişimi.
1. O Olay Görüntüleyicisi dosyayı açın.
1. Genel Olay Görüntüleyicisi Uygulama ve Hizmet Günlükleri **\Microsoft\Windows'a** gidin ve **AppLocker'ı seçin**.
1. Herhangi bir **8003 veya** **8006** olayı bulun ve ardından etkinlikten bilgileri kopyalayın:
    - Uygulama adı
    - Uygulama sürümü
    - Açıklama
    - Publisher (örneğin: `O=<publisher name>, L=<location>, S=State, C=Country`)
