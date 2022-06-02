---
title: Office 365 için Microsoft Defender Plan 2'de c-suite'inizi Öncelik hesabı koruması ile koruma
description: C paketinizi öncelikli hesap korumasıyla koruma adımları. Bir hesabın Öncelik hesabı olarak etiketlenmesi, şirket yöneticilerini hedefleyen posta akışı düzenleri için ayarlanmış ek korumanın yanı sıra raporlarda, uyarılarda ve araştırmalarda ek görünürlük sağlar.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: article
ms.technology: mdo
ms.openlocfilehash: 3670d4c1c55cbaaab739a8de2df359f06b53ae80
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842486"
---
# <a name="protect-your-c-suite-with-priority-account-protection"></a>C-suite'inizi öncelikli hesap korumasıyla koruma

Öncelikli hesap koruması, BT ve güvenlik ekiplerinin kuruluşunuzdaki kritik kişiler için yüksek hizmet kalitesi ve koruma sağlamasına yardımcı olur. Bir hesabın öncelik hesabı olarak etiketlenmesi, şirket yöneticilerini hedefleyen posta akışı düzenleri için ayarlanmış ek korumanın yanı sıra raporlarda, uyarılarda ve araştırmalarda ek görünürlük sağlar.

## <a name="what-youll-need"></a>İhtiyacınız olan şey
- Office 365 için Microsoft Defender Plan 2 (E5 planlarının bir parçası olarak dahildir)
- Yeterli izinler (Güvenlik Yöneticisi rolü)
- Aşağıdaki adımları gerçekleştirmek için 5 dakika.

## <a name="tag-priority-users"></a>Etiket Önceliği kullanıcıları
1. Öncelik hesapları olarak etiketlemek istediğiniz kullanıcıları, grupları veya etki alanlarını belirleyin.
1. [Microsoft Güvenlik Portalı'nda](https://security.microsoft.com/) oturum açın ve sol gezinti çubuğundaki Ayarlar gidin.
1. Yüklenen sayfada e-posta & işbirliği'ni seçin ve ardından Kullanıcı etiketleri'ne tıklayın
1. Kullanıcı etiketleri sayfasında Öncelik hesabı etiketini seçin ve Etiketi düzenle'ye basın
1. Görüntülenen açılır öğede Üye ekle'yi seçin
1. Etiketlemek istediğiniz kullanıcıları arayın, bir veya daha fazla kullanıcı seçin ve Ekle'ye basın
1. Seçtiğiniz üyeleri gözden geçirin ve İleri'ye basın
1. Değişiklikleri onaylamak için Gönder'e basın

Hangi öncelik hesabı etiketlerinin olduğunu öğrenmek için bkz. [Öncelik hesaplarını yönetme ve izleme - yönetici Microsoft 365 | Microsoft Docs](../../../admin/setup/priority-accounts.md).

## <a name="next-steps"></a>Sonraki Adımlar
[Öncelik hesapları olarak etiketlenen kullanıcılar için farklı korumayı gözden geçirin](../../office-365-security/configure-review-priority-account.md).

## <a name="powershell-configuration"></a>PowerShell yapılandırması
Bu adımları PowerShell aracılığıyla gerçekleştirmek istiyorsanız, bunu aşağıdaki cmdlet'leri kullanarak yapabilirsiniz:
1. Öncelik hesaplarının listesini görüntüleme: **Get-User -IsVIP | Kimlik'i seçin**
1. Öncelik hesapları listesine kullanıcı ekleme: **Set-User -VIP:$true -Identity \<Identity\>**
1. Kullanıcıyı öncelik hesapları listesinden kaldırma: **Set-User -VIP:$false -Identity \<Identity\>**
