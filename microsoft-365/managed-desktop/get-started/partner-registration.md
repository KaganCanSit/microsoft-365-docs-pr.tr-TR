---
title: İş ortağı kaydı
description: İş ortakları cihazları Microsoft Yönetilen Masaüstü tarafından yönetil olmak için kaydedene kadar
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
ms.openlocfilehash: af1e187c77acde257fa3458709fae50616cf810d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704842"
---
# <a name="partner-registration"></a>İş ortağı kaydı

Bu makalede, İş Ortakları'nın cihazları kaydetme adımları açıklanmıştır. Cihazları kendiniz kaydetme işlemi El ile kayıt [işlemiyle belgelenmiş olarak belgelenmiştir](manual-registration.md).

## <a name="prepare-for-registration"></a>Kayıt için hazırlanma

Müşteri için kayıt işlemini tamamlamadan önce İş Ortağı Merkezi'nde onlarla bir ilişki [kurmanız gerekir](https://partner.microsoft.com/dashboard). Bu işlem hakkında daha fazla bilgi için, izin [belgelerine bakın](/windows/deployment/windows-autopilot/registration-auth#csp-authorization). Herhangi bir CSP iş ortağı, müşteri onayları olduğu sürece herhangi bir müşteri adına cihaz ekleyebilir. Ayrıca, İş Ortağı Merkezi yardımı'nda, iş ortağı ilişkileri ve AutoPilot izinleri hakkında [daha fazla bilgi edinebilirsiniz](/partner-center/customers_revoke_admin_privileges#windows-autopilot).

> [!NOTE]
> Bu belge yalnızca İş Ortakları ve OEM'ler içindir. Kendi kendine kayıt işlemi, El ile kayıt altında [belgelenmiş olarak yapılır](manual-registration.md).

## <a name="register-devices-using-the-partner-center"></a>İş Ortağı Merkezi'nde cihazları kaydetme

Müşterilerinizle ilişki kurduğuktan sonra, müşterilerin herhangi biri için AutoPilot'a cihaz eklemek üzere İş Ortağı Merkezi'nde bağlantı kurabilirsiniz.

**Cihazları İş Ortağı Merkezi'nde kaydetmek için:**

1. İş Ortağı [Merkezi'ne gidin](https://partner.microsoft.com/dashboard).
2. İş **Ortağı** Merkezi menüsünden Müşteriler'i seçin ve ardından cihazlarını yönetmek istediğiniz müşteriyi seçin.
3. Müşterinin ayrıntı sayfasında Cihazlar'ı **seçin**.
4. Profilleri **cihazlara uygula'nın** altında Cihaz **ekle'yi seçin**.
5. Seçtiğiniz cihaz profili için uygun Grup Etiketini girin (aşağıdaki tabloda gösterildiği gibi) ve ardından gözat'ı seçerek müşteri listesini (.csv biçiminde) İş Ortağı Merkezi'ne yükleyin.

| [Cihaz profili](../service-description/profiles.md) | Grup Etiketi |
| ----- | -----|
| Hassas veriler | **Microsoft365ManagedSensitiveData\_** |
| Güçlü kullanıcı | **Microsoft365ManagedPowerUser\_** |
| Standard | **Microsoft365ManagedStandard\_** |

> [!IMPORTANT]
> Grup Adı, büyük harfe ve özel karakterler de dahil olmak üzere tabloda listelenenlerle tam olarak eşleşmesi gerekir. Bu, yeni kaydedilen cihazların Microsoft Yönetilen Masaüstü AutoPilot profiliyle atanmalarına olanak tanır.

>[!NOTE]
> Bu cihaz satın alma .csv bu dosyayı almış olması gerekir. [OnePilot'a](/windows/deployment/windows-autopilot/add-devices#collecting-the-hardware-id-from-existing-devices-using-powershell) .csv ekleme'de adımları takip eden bir dosya Windows. Gereksinimler: <ul><li>Ek sütunlar desteklenmiyor.</li> <li>Teklifler desteklenmiyor.</li> <li>Yalnızca ANSI biçimindeki metin dosyaları kullanılabilir (Unicode değil).</li> <li>Üst bilgiler büyük/harfe duyarlıdır.</li></ul> Bu gereksinimler nedeniyle Excel dosyanın CSV dosyası olarak düzenlenmesi kullanılabilir bir dosya oluşturmaz. Cihaz seri numarasında baştaki sıfırları korumayı sağlar. İş ortakları, [İş Ortağı Merkezi'nde Microsoft Yönetilen Masaüstü cihazları için cihazları kaydetmek üzere Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) kullansın.

Dosyanızı karşıya yüklemeye çalışırken bir hata iletisi .csv, dosyanın biçimini kontrol edin. Sütun siparişlerinin, müşterinin ilk kullanım [deneyiminde Windows AutoPilot](/partner-center/autopilot#add-devices-to-a-customers-account) profillerini yeni cihazlarda kullanma başlığı altında açıklananlarla eş olduğundan emin olun. Cihaz listesi oluşturmak için cihaz .csv yanındaki bağlantıda **sağlanan örnek dosya** dosyasını da kullanabilirsiniz.

İş ortağı senaryoları altında AutoPilot hakkında daha fazla bilgi için bkz [. Müşterinin hesabına cihaz ekleme](/partner-center/autopilot#add-devices-to-a-customers-account).

## <a name="register-devices-by-using-the-oem-api"></a>OEM API'sini kullanarak cihazları kaydetme

Müşteri için kayıt işlemini tamamlamadan önce bu müşteriyle bir ilişki kurmanız gerekir. İlgili müşterilerinize sağlamak için benzersiz bir bağlantınız olmalıdır. Bkz [. OEM ilişkisi kurma](/windows/deployment/windows-autopilot/registration-auth#oem-authorization).

İlişkiyi kurduğuktan sonra, seçtikleri her cihaz profili için uygun Grup Etiketini kullanarak cihazları müşterilere kaydetmeye başlayabilirsiniz:

| Cihaz profili | Grup Etiketi |
| ----- | ----- |
| Hassas veriler | **Microsoft365ManagedSensitiveData\_** |
| Güçlü kullanıcı | **Microsoft365ManagedPowerUser\_** |
| Standard | **Microsoft365ManagedStandard\_** |

> [!IMPORTANT]
> Grup Etiketleri, büyük harfe ve özel karakterler de dahil olmak üzere tabloda listelenenleri tam olarak eşleşmesi gerekir. Bu, yeni kaydedilen cihazların Microsoft Yönetilen Masaüstü AutoPilot profiliyle atanmalarına olanak tanır.
