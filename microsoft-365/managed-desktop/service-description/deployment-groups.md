---
title: Cihaz dağıtım grupları
description: Güncelleştirmeleri ve diğer değişiklikleri yönetmek için kullanılan dağıtım grupları
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 624bde84da9a0c35f5814e3b6c67c2d190683fc6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330307"
---
# <a name="device-deployment-groups"></a>Cihaz dağıtım grupları

Microsoft Yönetilen Masaüstü, cihazlara yapılan güncelleştirmeleri ve yapılandırma değişikliklerini yönetmek için dağıtım gruplarını kullanır. Cihazlar, Microsoft Yönetilen Masaüstü'ne kaydolduklarında dağıtım gruplarına ("halkalar" veya "güncelleştirme grupları") otomatik olarak eklenir. Dağıtım grupları cihazların aşamalı bir zaman çizelgesinde değişiklik allarına olanak tanır.

Bazı cihazları yalnızca test amacıyla atamak veya önce değişiklikleri alacak belirli erken benimseyen kullanıcıları atamak istiyor olabilirsiniz. Yöneticiler tarafından kullanılanlar veya iş açısından kritik işlevlere sahip olanlar gibi kritik cihazlarınız varsa, güncelleştirmeleri en yavaş şekilde alan bir grupta tutmak iyi olabilir. Microsoft Yönetilen Masaüstü, bir cihazın aşağıdaki gruplardan herhangi birini kullanarak kalmasını belirtmenize olanak sağlar.

| Grup | Açıklama |
| ----- | ----- |
| Test | Test grubu test etmek için kullanılan cihazlar veya sık yapılan değişiklikleri sık tanıyabilecek, yeni özelliklere maruz kalma ve erken geri bildirim sağlayabilecek kullanıcılar için en iyisidir.<br><br>Bu grup sık sık değişiklik alır ve bu gruptaki deneyimlerin etkisi güçlü olur. Test grubu, kurulmuş herhangi bir hizmet düzeyi sözleşmesi ve kullanıcı desteğinden muaftır. En iyisi önce yalnızca birkaç cihazı taşımak ve ardından kullanıcı deneyimini gözden geçirmektir. Microsoft Yönetilen Masaüstü bu gruba cihazları otomatik olarak atamaz. Bu grup yalnızca belirttiğiniz cihazları içerir.
| Birinci | İlk grup erken benimseyenler, gönüllü, belirlenen geçerlilik sahibi, IT Profesyonelleri veya işletme işlevlerinin temsilcileri için idealdir. Yani, değişiklikleri doğrulayan ve deneyim hakkında size geri bildirim sağlaylayan kişiler.
| Hızlı | Hızlı grubu, işletme işlevlerinin temsilcileri için idealdir. Bu kişiler, kapsamlı dağıtım öncesinde değişiklikleri doğrular.
| Geniş | Geniş grubu en son değişiklikleri alır.<br><br>Genelde çoğu kuruluş bu grupta yer alır. Bu grupta olması gereken cihazları belirtebilirsiniz. Bu cihazlar en son iş açısından kritik işlevlere sahip olduğundan veya kritik rollere sahip kullanıcılara ait olduğundan değişiklikler alsa gerek.
| Otomatik | Microsoft Yönetilen Masaüstü'nden cihazları diğer gruplardan birini otomatik olarak ataması için Otomatik'i seçin.<br><br>Cihazları otomatik olarak Test'e atamaz. Daha önce belirttiğiniz bir cihazı, otomatik olarak yeniden atanacak şekilde serbest bırakmak için bu seçeneği belirleyin.

Windows güncelleştirmelerinin gruplar halinde nasıl yönetilleri hakkında daha fazla bilgi için bkz. [Microsoft Yönetilen Masaüstü'de güncelleştirmeler nasıl yönetilir](updates.md).

## <a name="labels"></a>Etiketler

Atanan grup sütunu aşağıdaki etiketleri içerir:

| Etiket | Açıklama |
| ----- | ----- |
| Yönetici | Cihaz, belirttiğiniz bir grupta. |
| Otomatik | Gruba Microsoft Yönetilen Masaüstü atanır. |
| Beklemede | Cihaz bir gruba taşıma sürecindedir. |

Grup **sütunu** her zaman cihazın şu anda içinde olduğu grubu gösterir ve yalnızca taşıma tamamlandığında güncellemeler.

> [!IMPORTANT]
> Bu grupların üyeliğini doğrudan değiştirmeye çalışmayın. Her zaman, Cihazlar dağıtım [grubuna atama konusunda açıklanan adımları izleyin](../working-with-managed-desktop/assign-deployment-group.md).
