---
title: Cihaz adları
description: Microsoft Yönetilen Masaüstü cihaz adlarını nasıl yönetir?
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
ms.openlocfilehash: 2ba44974fa2181ccf0b1d4ef0a5705d630aff0d3
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2022
ms.locfileid: "63016257"
---
# <a name="device-names"></a>Cihaz adları

Microsoft Yönetilen Masaüstü autopilot Windows AutoPilot, Azure Active Directory ve Microsoft Intune. Bu hizmetlerin sorunsuz bir şekilde birlikte çalışması için, cihazların tutarlı, standart adlara ihtiyacı vardır. Microsoft Yönetilen Masaüstü, cihazlar kaydedilsinken standart bir ad biçimi ( *MMD-%RAND11* formunun) uygular. Windows AutoPilot bu adları atar. AutoPilot hakkında daha fazla bilgi için bkz [. AutoPilot ile ilk çalıştırma deneyimi ve Kayıt Durumu Sayfası](../get-started/esp-first-run.md).

## <a name="automated-name-changes"></a>Otomatik ad değişiklikleri

Daha sonra bir cihaz yeniden adlandırılırsa Microsoft Yönetilen Masaüstü bunu otomatik olarak standart biçimli yeni bir adla yeniden adlandıracaktır. Bu işlem her dört saatte bir gerçekleşir. Ad değişikliği, kullanıcının cihazı bir sonraki yeniden başlatması ile  sürer.

> [!IMPORTANT]
> Ortamınız belirli cihaz adlara bağlı ise (örneğin, belirli bir ağ yapılandırmasını desteklemeye), Microsoft Yönetilen Masaüstü'ne kaydolmadan önce bu bağımlılığı kaldırma seçeneklerini araştırmanız gerekir. Ad bağımlılığını tutmanız gerekirse, yeniden adlama işlevini devre dışı bırakmak ve istediğiniz ad biçimini kullanmak için Yönetici [portalı](../working-with-managed-desktop/admin-support.md) aracılığıyla bir istek gönderebilirsiniz.