---
title: Microsoft Teams
description: Nasıl Teams cihazlara yüklenir ve daha sonra güncelleştirilir
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler, uygulamalar, iş hattı uygulamaları, LOB uygulamaları
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: ITPro
ms.openlocfilehash: 3dfdd9f5187fba9a1e19e56a4df24cf1f7eff44b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322443"
---
# <a name="microsoft-teams"></a>Microsoft Teams

[Teams](https://www.microsoft.com/microsoft-365/microsoft-teams/group-chat-software), [gerçek zamanlı işbirliği ve iletişim](https://support.microsoft.com/office/microsoft-teams-basics-6d5f52e6-5306-4096-ac24-c3082b79eaf0), toplantılar, dosya ve uygulama paylaşımı için bir çalışma alanı da sağlayan bir mesajlaşma uygulamasıdır.

## <a name="initial-deployment"></a>İlk dağıtım

Çoğu donanım satıcı, henüz Teams parçası olarak resim parçası olarak güvenlik kameralarını dahil etmemektedir. Microsoft Yönetilen Masaüstü, Teams uygulamaları kullanarak cihazlarınıza Microsoft Intune. Tüm yönetilen cihazlar, [Teams .msi paketine](/MicrosoftTeams/msi-deployment#how-the-microsoft-teams-msi-package-works) sahip. Bu .msi paketi, cihazda oturum alan tüm kullanıcıların kullanıma hazır Microsoft Teams hazır olur. Paket yüklemeyi ilk kez tamamlarsa, Teams başlatılır ve masaüstüne bir kısayol eklenir.

### <a name="microsoft-intune-changes"></a>Microsoft Intune değişiklikleri

Microsoft Yönetilen Masaüstü, destek olmak için Azure AD Microsoft Teams. Cihaza uygun olarak 64 bit veya 32 bit istemcilere dağıtılır:  

- Modern Çalışma Alanı - Teams Machine Wide Installer x64  
- Modern Çalışma Alanı - Teams Machine Wide Installer x32

## <a name="updates"></a>Güncelleştirmeler

Teams, dosyadan ayrı bir güncelleştirme yolu Kurumlar için Microsoft 365 Uygulamaları. Masaüstü istemcisi kendisini otomatik olarak ler. Teams birkaç saatte bir denetler, bunları indirir ve sonra güncelleştirmeyi sessiz yüklemeden önce bilgisayarın boşta beklemesini bekler.  

Bu Teams grubu yöneticilerin güncelleştirmeleri denetlemesine izin vermemektedir, dolayısıyla Microsoft Yönetilen Masaüstü standart [otomatik güncelleştirme kanalını kullanır](/microsoftteams/teams-client-update#can-admins-deploy-updates-instead-of-teams-auto-updating).

### <a name="manually-updating-teams"></a>El ile güncelleştirme Teams

Tek tek kullanıcılar da güncelleştirmeleri indirebilir. Uygulamanın sağ üst kısmında, Profil açılan listesinde Güncelleştirmeleri kontrol **edin'i seçin**. Bir güncelleştirme varsa, bilgisayar boşta olduğunda indirilir ve sessizce yüklenir.

## <a name="delivery-optimization-of-updates"></a>Güncelleştirmeleri teslim iyileştirme

Güncelleştirmeler için Teams iyileştirme varsayılan olarak açıktır ve yöneticiler veya kullanıcılardan herhangi bir işleme gerek yoktur.
