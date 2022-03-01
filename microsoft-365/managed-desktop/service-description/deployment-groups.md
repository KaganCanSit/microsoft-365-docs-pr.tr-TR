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
ms.openlocfilehash: 59f5cd1606c6d0b48bfbc22513790a185dd5f1b1
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2022
ms.locfileid: "63010060"
---
# <a name="device-deployment-groups"></a>Cihaz dağıtım grupları

Microsoft Yönetilen Masaüstü, cihazlara yapılan güncelleştirmeleri ve yapılandırma değişikliklerini yönetmek için dağıtım gruplarını kullanır. Cihazlar, Microsoft Yönetilen Masaüstü'ne kaydolduklarında dağıtım gruplarına ("halkalar" veya "güncelleştirme grupları") otomatik olarak eklenir. Dağıtım grupları cihazların aşamalı bir zaman çizelgesinde değişiklik allarına olanak tanır.

Bazı cihazları yalnızca test amacıyla atamak veya önce değişiklikleri alacak belirli erken benimseyen kullanıcıları atamak istiyor olabilirsiniz. Yöneticiler tarafından kullanılanlar veya iş açısından kritik işlevlere sahip olanlar gibi kritik cihazlarınız varsa, güncelleştirmeleri en yavaş şekilde alan bir grupta tutmak iyi olabilir. Microsoft Yönetilen Masaüstü, bir cihazın aşağıdaki gruplardan herhangi birini kullanarak kalmasını belirtmenize olanak sağlar.

- **Test**: Test etmek için kullanılan cihazlar veya sık yapılan değişiklikleri sık kullanılan ve yeni özelliklere maruz kalma özelliğine açık olan kullanıcılar için en iyi uygulamadır ve erken geri bildirim sağlar. Bu grup sık sık değişiklik alır ve bu gruptaki deneyimlerin etkisi güçlü olur. Test grubu, kurulmuş herhangi bir hizmet düzeyi sözleşmesi ve kullanıcı desteğinden muaftır. En iyisi önce yalnızca birkaç cihazı taşımak ve ardından kullanıcı deneyimini kontrol etmektir. Microsoft Yönetilen Masaüstü cihazları bu gruba otomatik olarak atamaz; yalnızca belirttiğiniz cihazlara sahip olur.
- **İlk** olarak: erken benimseyenler, gönüllü veya belirlenen geçerli kişiler, IT Profesyonelleri veya işletme işlevlerinin temsilcileri, yani değişiklikleri doğrulayan ve size deneyim hakkında geri bildirim sağlaylayan kişiler için idealdir.
- **Hızlı**: geniş dağıtım öncesinde değişiklikleri doğrulayan kişiler olan işletme işlevlerinden temsilciler için idealdir.
- **Geniş** , en son değişiklikleri alır. Genelde çoğu kuruluş bu grupta yer alır. Ayrıca, bu grupta yer almaları gereken cihazları da belirtebilirsiniz ve yalnızca en son değişiklikleri alırlar çünkü iş açısından kritik işlevleri yerine veya kritik rollere sahip kullanıcılara aitler. 
- **Otomatik**: Microsoft Yönetilen Masaüstü'nden cihazları diğer gruplardan birini otomatik olarak ataması için bu seçeneği belirleyin. (Cihazları Otomatik olarak Test'e atamaz.) Daha önce belirttiğiniz bir cihazı, otomatik olarak yeniden atanacak şekilde serbest bırakmak için bu seçeneği belirleyin. 

Güncelleştirmelerin gruplar halinde nasıl Windows daha fazla bilgi için bkz. [Microsoft Yönetilen Masaüstünde güncelleştirmeler nasıl yönetilir](updates.md).

Belirttiğiniz bir grupta bir cihaz varsa, Atanan **grup Yönetici** olarak **belirtilir**. Microsoft Yönetilen Masaüstü gruba atadığı her şey Otomatik olarak **yorumladır**. Bir cihaz gruba taşıma sürecindeyken, cihaz Beklemede olarak **gösterir**. Grup **alanı** her zaman cihazın o anda içinde olduğu grubu gösterir ve yalnızca taşıma tamamlandığında güncellemeler.

> [!IMPORTANT]
> Bu grupların üyeliğini doğrudan değiştirmeye çalışmayın. Her zaman, Cihazlar dağıtım [grubuna atama konusunda açıklanan adımları izleyin](../working-with-managed-desktop/assign-deployment-group.md).
