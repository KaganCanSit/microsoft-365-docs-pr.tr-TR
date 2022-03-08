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
ms.openlocfilehash: fe29027dab3b3395c14729ee7e04cbe7cebf7261
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317171"
---
# <a name="device-names"></a>Cihaz adları

Microsoft Yönetilen Masaüstü Windows AutoPilot, Azure Active Directory ve Microsoft Intune kullanır.

Bu hizmetlerin sorunsuz bir şekilde birlikte çalışması için, cihazların tutarlı, standart adlara ihtiyacı vardır. Cihazlar kaydedil olduğunda Microsoft Yönetilen Masaüstü standart bir ad `MMD-%RAND11`biçimi (formun) uygular. Windows AutoPilot bu adları atar. AutoPilot hakkında daha fazla bilgi için bkz [. AutoPilot ile ilk çalıştırma deneyimi ve Kayıt Durumu Sayfası](../get-started/esp-first-run.md).

## <a name="automated-name-changes"></a>Otomatik ad değişiklikleri

Cihaz daha sonra yeniden adlandırılırsa, Microsoft Yönetilen Masaüstü bunu otomatik olarak standart biçimli yeni bir adla yeniden adlandıracaktır. Bu işlem her dört saatte bir gerçekleşir. Ad değişikliği, kullanıcının cihazı bir sonraki yeniden başlatması ile  sürer.

> [!IMPORTANT]
> Ortamınız belirli cihaz adlara bağlı ise (örneğin, belirli bir ağ yapılandırmasını desteklemeye), Microsoft Yönetilen Masaüstü'ne kaydolmadan önce bu bağımlılığı kaldırma seçeneklerini araştırmanız gerekir.<br><br>Ad bağımlılığını tutmanız gerekirse, yeniden adlama işlevini devre dışı bırakmak ve istediğiniz ad biçimini kullanmak için Yönetici [portalı](../working-with-managed-desktop/admin-support.md) aracılığıyla bir istek gönderebilirsiniz.
