---
title: Kullanıcı deneyimini yerelleştirme
description: Kullanıcılar için cihazları yerelleştirme
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: c7930215efac4e02a6a0bab484e9158ad693997a
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016517"
---
# <a name="localize-the-user-experience"></a>Kullanıcı deneyimini yerelleştirme

Microsoft Yönetilen Masaüstü cihazları kullanıcıları, kurulum işlemi sırasında ("ilk tercihi" olan deneyim) veya daha sonra tercihlerinin dilini kullanabilir.

## <a name="during-setup-the-out-of-box-experience"></a>Kurulum sırasında ("ilk deneyim yok"

Kurulum sırasında, kullanıcılar kendi tercihlerinin dilini seçer. Bu seçim şu öznitelikleri etkiler:

| Öznitelik | Açıklama |
| ------ | ------ |
| Windows 10 dil özellikleri | <ul><li>Görüntüleme dili</li><li>Klavye dili</li><li>Dille İlgili Talep Üzerine Özellikler</li><ul> |
| Microsoft 365 Uygulamaları için Enterprise özellikleri | <ul><li>Görüntüleme dili</li><li>Yazım denetleme ve yazma araçları</li></ul> |

> [!NOTE]
> Kullanıcılar yalnızca kurulum sırasında dili seçerek dille ilgili On Demand özelliğine sahip olabilir.

## <a name="after-completing-setup"></a>Kurulumu tamamladıktan sonra

Kullanıcılar kurulum işlemi tamamlandıktan sonra Windows 10 dile Microsoft 365 Uygulamaları dile Enterprise dile sahip olabilir. Özel olarak:

| Özellik | Açıklama |
| ------ | ------ |
| Windows 10 dil özellikleri | <ul><li>Görüntüleme dili</li><li>Klavye dili</li><ul> |
| Microsoft 365 Uygulamaları için Enterprise özellikleri | <ul><li>Görüntüleme dili</li><li>Yazım denetleme ve yazma araçları</li></ul> |

Kullanıcılarınızı [yüklemesi için](#supported-languages) Microsoft 365 Uygulamaları Enterprise dilinin kullanılabilir olması için, kullanıcıları **Modern Workplace-Office-Language_Packs** grubuna ekleyin. Diller aşağıdaki dillerde Intune Şirket Portalı.

## <a name="supported-languages"></a>Desteklenen diller

Yeni cihazlar için, üreticinizin size gereken dilleri içeren cihaz resimleri sağlaması gerekir. Üreticinizin resminde desteklenen diller listesine dahil olmayan diller varsa, cihaz hala hizmet tarafından de desteklemektedir.

Mevcut cihazları yeniden ediyorsanız, uygun resimleri almak için Microsoft hesap temsilciniz ile birlikte çalışmanız gerekiyor olabilir. Daha fazla bilgi için bkz. [Cihaz resimleri](../service-description/device-images.md).

Microsoft [Yönetilen Masaüstü](../service-description/device-images.md#universal-image) tarafından sağlanan evrensel resim, bu dilleri ve aşağıdaki dilleri Windows 10:

- Arapça
- Bulgarian
- Chinese Simplified
- Chinese Traditional
- Croatian
- Czech
- Danish  
- Dutch  
- İngilizce (ABD, GB, AU, CA, IN)
- Estonian
- Finnish
- Fransızca (Fransa, Kanada)
- German
- Greek
- Hebrew
- Hungarian
- Indonesian
- Italian
- Japanese
- Korean
- Latvian
- Lithuanian
- Norveççe (Bokmål)
- Polish
- Portekizce (Brezilya)
- Portekizce (Portekiz)
- Romanian
- Russian
- Sırpça (Latin alfabesi)
- Slovak
- Slovenian
- İspanyolca (İspanya, Meksika)
- Swedish
- Thai
- Turkish
- Ukrainian
- Vietnamese

> [!NOTE]
> Microsoft 365 Uygulamaları için Enterprise listesi biraz farklı bir listeyi destekleyenin.

Kullanıcılarınızı burada listelenenler dışında bir dile ihtiyaç varsa [Yönetim portalını](../working-with-managed-desktop/admin-support.md) kullanarak bir destek [isteği dosya edin](access-admin-portal.md).

## <a name="languages-for-support-and-operations"></a>Destek ve işlemler için diller

### <a name="user-support"></a>Kullanıcı desteği

Microsoft Yönetilen Masaüstü yalnızca İngilizce destek sağlar. Kullanıcılar Yardım Alın uygulamasında başka bir dil seçerse, doğrudan Microsoft Yönetilen Masaüstü'nden destek almak yerine genel Microsoft destek kanallarından destek elde ederim. Daha fazla bilgi için bkz [. Kullanıcılar için yardım alma](../working-with-managed-desktop/end-user-support.md).

Kullanıcılarınız başka dillerde de yardıma ihtiyaç destekliyorsa, bunu Microsoft dışı destek kaynakları veya kendi kuruluştan sağlamanız gerekir.

### <a name="admin-support-and-operations"></a>Yönetici desteği ve işlemleri

Microsoft Yönetilen Masaüstü yalnızca İngilizce yönetici desteği sağlar. Bu destek Yönetici portalını ve Microsoft Yönetilen Masaüstü İşlemleri ile tüm iletişimi içerir. Yönetici ile ilgili tüm etkileşimlerin ve arabirimlerin, aksi belirtilmedikçe İngilizce olduğunu varsayabilirsiniz.
