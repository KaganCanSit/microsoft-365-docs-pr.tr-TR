---
title: Microsoft Consulting Services ile çalışma
description: Uygulamalarınızı paketlerken MCS ile çalışmak için hazırlık ve adımlar
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
ms.openlocfilehash: 5dd6bf62625d6b22a0585645abbeb24dabd6c9fd
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027554"
---
# <a name="working-with-microsoft-consulting-services"></a>Microsoft Consulting Services ile çalışma

Uygulamalarınızı Microsoft Yönetilen Masaüstü ile kullanmak üzere paketli yapmak için Microsoft Consulting Services (MCS) ile etkileşime girişebilirsiniz. Daha fazla bilgi için, hesap temsilciniz ile birlikte çalışarak BELIRLI uygulama paketleme projenizi gözden geçirmek için MCS'ye başvurun.

## <a name="roles-and-responsibilities"></a>Roller ve sorumluluklar

| Rol | Sorumluluk |
| ------ | ------ |
| Siz | MCS uygulama paketiyle çalışmak **için, aşağıdaki öğeleri sağlay gerekir**: <ul><li> Kaynak yükleyici dosyaları (örneğin, setup.exe veya .msi).</li><li>Son yüklemenin nasıl olması gerektiğiyle ilgili ayrıntıları belirten yükleme yönergeleri. Örneğin, uygulamanın bir masaüstü kısayolu olması gerekir mi? Uygulamanın görünürlüğü ne olmalı? Uygulama bir sunucuya bağlanmalı mı, bağlantı varsa hangisi? Daha fazla bilgi için, uygulama [paketleme isteği şablonuna bakın](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/app-packaging-template.docx).</li><li>Uygulamanın ortamınıza beklendiği gibi çalıştığını doğrulamak için kendi kabul testini gerçekleştirmeniz gerekir.</li><ul> |
| Microsoft Consulting Services (MCS) | **MCS aşağıdaki eylemleri gerçekleştirecek:** <ul><li>Uygulamanın Microsoft Yönetilen Masaüstü ortamında yasak mı yoksa kısıtlanmış mı olduğunu kontrol edin.</li><li>Uyumluluk sağlamak için uygulamanın yüklemeyi, başlatmayı ve kaldırmayı test Windows 10. MCS bir uyumluluk sorunu keşfederse, düzeltme için [uygulamayı App Assure](/fasttrack/products-and-capabilities#app-assure) programına sunar.</li><li>Uygulamayı belirtimlerinize göre paketler ve Microsoft Intune.</li><ul>

## <a name="app-delivery-schedule"></a>Uygulama teslim zamanlaması

Uygulama bilgilerini Microsoft Yönetilen Masaüstü portalına yükerek paketleme işlemini başlatabilirsiniz. Paketleme ekibi her Perşembe yeni gönderileri gözdener. Gözden geçirme ve paketlemenin ardından, paketli uygulamalar şu Cuma günü teslim edilir. Haftada en çok beş uygulama başlamak üzere paket kullanılabilir, ancak hizmet, ihtiyaçlarını karşılayacak şekilde ölçeklendirebilirsiniz.

![Perşembe günü (bu örnekte 21'inde), medya doğrulamasının sonraki günü, izleyen Pazartesi (25'te) paketlemeyi ve sonraki Cuma (29'da) uygulama teslimini gösteren takvim.](../../media/MCS-cal.png)

Uygulama teslim edildiktan sonra size bildirilecek. Bu noktada, Microsoft Yönetilen Masaüstü portalında kabul testlerini gerçekleştirmek ve işi onaylamak için 21 gün vardır. Kabul testi sırasında uygulamayla ilgili bir sorun keşfedersiniz, uygulamayı Microsoft Yönetilen Masaüstü portalında reddedin. Sorunu anlamak ve çözmek için bir Microsoft Consulting Services (MCS) paketleyicisi ile e-posta yoluyla bağlantınız olur.

## <a name="testing-accounts-and-environment"></a>Hesapları ve ortamı test etme

Paketleme ekibinin geçişin tamamlandıktan sonra tamamlandıktan Microsoft Intune izinler sağlamanız önerilir:

- Paketleyiciye Microsoft Intune eklemek ve atamak için paketin Uygulama Dağıtımı özelliklerine erişim.
- Paketçilerin uygulamaları test etmek için gruplarını, kullanıcı hesaplarını ve lisanslarını test edin.

MCS, aşağıdaki eylemleri gerçekleştirmek için bu izinleri kullanır:

- Uygulamanın Microsoft Yönetilen Masaüstü için yapılandırılmış sanal makinede çalışır olduğundan emin olmak.
- Upload dağıtımı Microsoft Intune için uygulamayı seçin.

Bu izinler olmadan, MCS'nin ileriye doğru ilerlemesi mümkündür, ancak uygulamaları ortamınıza yükamaz.
