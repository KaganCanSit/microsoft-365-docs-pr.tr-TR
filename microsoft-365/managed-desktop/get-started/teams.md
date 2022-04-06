---
title: Microsoft Teams
description: Nasıl Teams cihazlara yüklenir ve daha sonra güncelleştirilir
keywords: Microsoft Managed Desktop, Microsoft 365, belge, uygulama, iş hattı uygulamaları, LOB uygulamaları
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: ITPro
ms.openlocfilehash: 469edf3e8ae856ea6e94bada8ffb9d6c97ba8b66
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634481"
---
# <a name="microsoft-teams"></a>Microsoft Teams

[Teams](https://www.microsoft.com/microsoft-365/microsoft-teams/group-chat-software), [gerçek zamanlı işbirliği ve iletişim](https://support.microsoft.com/office/microsoft-teams-basics-6d5f52e6-5306-4096-ac24-c3082b79eaf0), toplantılar, dosya ve uygulama paylaşımı için bir çalışma alanı da sağlayan bir mesajlaşma uygulamasıdır.

## <a name="initial-deployment"></a>İlk dağıtım

Çoğu donanım satıcı, henüz Teams parçası olarak resim parçası olarak güvenlik kameralarını dahil etmemektedir. Microsoft Managed Desktop, Teams kullanarak cihazlarınıza e-posta Microsoft Intune. Tüm yönetilen cihazlar, [Teams .msi paketine](/MicrosoftTeams/msi-deployment#how-the-microsoft-teams-msi-package-works) sahip. Bu .msi paketi, cihazda oturum alan tüm kullanıcıların kullanıma hazır Microsoft Teams hazır olur. Paket yüklemeyi ilk kez tamamlarsa, Teams başlatılır ve masaüstüne bir kısayol eklenir.

### <a name="microsoft-intune-changes"></a>Microsoft Intune değişiklikleri

Microsoft Managed Desktop kiracınıza Microsoft Teams ekler: Modern Çalışma Alanı - Teams Machine Wide Installer x64  

## <a name="updates"></a>Güncelleştirmeler

Teams, dosyadan ayrı bir güncelleştirme yolu Kurumlar için Microsoft 365 Uygulamaları. Masaüstü istemcisi kendisini otomatik olarak ler. Teams birkaç saatte bir denetler, bunları indirir ve sonra güncelleştirmeyi sessiz yüklemeden önce bilgisayarın boşta beklemesini bekler.  

Ürün Teams grubu yöneticilerin güncelleştirmeleri denetlemesine izin vermez; dolayısıyla Microsoft Managed Desktop standart [otomatik güncelleştirme kanalını kullanır](/microsoftteams/teams-client-update#can-admins-deploy-updates-instead-of-teams-auto-updating).

### <a name="manually-updating-teams"></a>El ile güncelleştirme Teams

Tek tek kullanıcılar da güncelleştirmeleri indirebilir. Uygulamanın sağ üst kısmında, Profil açılan listesinde Güncelleştirmeleri kontrol **edin'i seçin**. Bir güncelleştirme varsa, bilgisayar boşta olduğunda indirilir ve sessizce yüklenir.

## <a name="delivery-optimization-of-updates"></a>Güncelleştirmeleri teslim iyileştirme

Güncelleştirmeler için Teams iyileştirme varsayılan olarak açıktır ve yöneticiler veya kullanıcılardan herhangi bir işleme gerek yoktur.
