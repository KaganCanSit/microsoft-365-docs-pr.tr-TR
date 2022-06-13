---
title: Kullanıcıların lisans atamalarını kaldırma
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: sinakassaw, nicholak
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
- okr_smb
- manage_licenses
- AdminTemplateSet
search.appverid: MET150
description: Ürün lisanslarının atamasını kaldırmak için kullandığınız yöntem, lisansları belirli kullanıcılardan mı yoksa belirli bir üründen mi kaldırdığınıza bağlıdır.
ms.date: 04/22/2022
ms.openlocfilehash: 23fc9ea04f45cdeb50acb0ec2d62d584974d6499
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043252"
---
# <a name="unassign-microsoft-365-licenses-from-users"></a>Kullanıcılardan Microsoft 365 lisanslarının atamasını kaldırma

Kullanıcılardan lisans atamalarını **Etkin kullanıcılar** sayfasından veya **Lisanslar** sayfasından kaldırabilirsiniz. Kullandığınız yöntem, belirli kullanıcıların ürün lisanslarını kaldırmak mı yoksa belirli bir üründen kullanıcı lisanslarının atamasını kaldırmak mı istediğinize bağlıdır.

> [!NOTE]
> 
> - Yönetici olarak, kuruluşunuzdaki bir kullanıcı tarafından satın alınan self servis satın alma aboneliği için lisans atayamaz veya lisansı kaldıramazsınız. [Self servis satın alma aboneliğini devralabilir](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription) ve lisansları atayabilir veya atamasını kaldırabilirsiniz.
> 
> - Bazı abonelikler için yalnızca aboneliğinizi satın aldıktan veya yeniledikten sonra sınırlı bir süre içinde iptal edebilirsiniz. İptal penceresi geçtiyse, süresi sonunda aboneliği iptal etmek için yinelenen ödemeyi kapatın.

## <a name="before-you-begin"></a>Başlamadan önce

- Lisansların atamasını kaldırabilmek için Genel, Lisans, Kullanıcı yöneticisi olmanız gerekir. Daha fazla bilgi için bkz. [Microsoft 365 yönetici rolleri hakkında](../add-users/about-admin-roles.md).
- [Office 365 PowerShell ile kullanıcı hesaplarından lisansları kaldırabilirsiniz](../../enterprise/remove-licenses-from-user-accounts-with-microsoft-365-powershell.md).
- Ayrıca, lisans atanmış [kullanıcı hesaplarını silip](../add-users/delete-a-user.md) lisanslarını diğer kullanıcıların kullanımına sunabilirsiniz. Bir kullanıcı hesabını sildiğinizde, lisansı hemen başka birine atanmaya hazırdır.

## <a name="use-the-licenses-page-to-unassign-licenses"></a>Lisans atamalarını silmek için Lisanslar sayfasını kullanma

**Lisans atamalarını silmek için Lisanslar** sayfasını kullandığınızda, belirli bir ürünün lisanslarını en fazla 20 kullanıcının atamasını kaldırmış olursunuz.

::: moniker range="o365-worldwide"

1. Yönetim merkezinde **Faturalama** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Lisansları</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezinde **Faturalama** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">Lisansları</a> sayfasına gidin.

::: moniker-end

2. Lisans atamasını silmek istediğiniz ürünü seçin.

3. Lisans atamalarını silmek istediğiniz kullanıcıları seçin.

4. **Lisansların atamasını kaldır'ı** seçin.

5. **Lisansların Atamasını Kaldır** kutusunda Atamayı **Kaldır'ı** seçin.

## <a name="use-the-active-users-page-to-unassign-licenses"></a>Lisans atamalarını silmek için Etkin kullanıcılar sayfasını kullanma

Lisansları kaldırmak için **Etkin kullanıcılar** sayfasını kullandığınızda, kullanıcılardan ürün lisanslarının atamasını kaldırırsınız.

### <a name="unassign-licenses-from-one-user"></a>Bir kullanıcıdan lisans atamasını kaldırma

::: moniker range="o365-worldwide"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

2. Lisansının atamasını silmek istediğiniz kullanıcının satırını seçin.

3. Sağ bölmede, **Lisanslar ve Uygulamalar**'ı seçin.

4. **Lisanslar** bölümünü genişletin, atamasını kaldırmasını istediğiniz lisansların kutularını temizleyin ve **ardından Değişiklikleri kaydet'i** seçin.

### <a name="unassign-licenses-from-multiple-users"></a>Birden çok kullanıcının lisans atamasını kaldırma

::: moniker range="o365-worldwide"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

2. Lisans atamasını kaldırmasını istediğiniz kullanıcıların adlarının yanındaki daireleri seçin.

3. Üst kısımda **Ürün lisanslarını yönet'i** seçin.

4. **Ürün lisanslarını yönet** bölmesinde Tüm  > **Kaydet değişikliklerinin** **atamasını kaldır'ı** seçin.

5. Bölmenin alt kısmında **Bitti'yi** seçin.  

## <a name="what-happens-to-a-users-data-when-you-remove-their-license"></a>Lisansını kaldırdığınızda kullanıcının verilerine ne olur?

- Kullanıcıdan lisans kaldırıldığında, bu hesapla ilişkili Exchange Online veriler 30 gün boyunca tutulur. 30 günlük yetkisiz kullanım süresinden sonra veriler silinir ve kurtarılamaz. Ancak, bekletme ilkesine bağlanır ve bekletme etiketleriyle eşleşen içerik bulma için korunur.
- OneDrive İş kaydedilen dosyalar, kullanıcı Microsoft 365 yönetim merkezi silinmediği veya Active Directory eşitlemesi aracılığıyla kaldırılmadığı sürece silinmez. Daha fazla bilgi için bkz. [OneDrive saklama ve silme](/onedrive/retention-and-deletion).
- Lisans kaldırıldığında, kullanıcının posta kutusu artık İçerik Arama veya eBulma (Premium) gibi bir eBulma aracı kullanılarak aranamaz. Daha fazla bilgi için, [Microsoft 365'de İçerik Arama'da](../../compliance/content-search.md) "Bağlantısı kesilmiş veya lisanslı olmayan posta kutularını arama" bölümüne bakın.
- Office 365 Kurumsal E3 gibi bir Enterprise aboneliğiniz varsa, Exchange Online etkin olmayan posta kutularını kullanarak silinen bir kullanıcı hesabının [posta kutusu](../../compliance/inactive-mailboxes-in-office-365.md) verilerini korumanıza olanak tanır. Daha fazla bilgi için bkz. [Exchange Online'da etkin olmayan posta kutuları oluşturma ve yönetme](../../compliance/create-and-manage-inactive-mailboxes.md).
- Lisansı kaldırıldıktan sonra kullanıcının Microsoft 365 verilerine erişimini engellemeyi ve daha sonra verilere erişmeyi öğrenmek için bkz. [Eski çalışanı kaldırma](../add-users/remove-former-employee.md).
- Kullanıcının lisansını kaldırırsanız ve hala Office uygulamaları yüklüyse, Office uygulamaları [kullandıklarında Office Lisanssız Ürün ve etkinleştirme hataları](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380) görür.

## <a name="next-steps"></a>Sonraki adımlar

[Kullanılmayan lisansları diğer kullanıcılara yeniden atamayacaksanız](../../managed-desktop/get-started/assign-licenses.md), ihtiyacınız olandan daha fazla lisans için ödeme yapmanıza gerek kalmaması için [lisansları aboneliğinizden kaldırmayı](../../commerce/licenses/buy-licenses.md) göz önünde bulundurun.

## <a name="related-content"></a>İlgili içerik

[Aboneliğinizden lisansları kaldırma](../../commerce/licenses/buy-licenses.md) (makale)\
[Kullanıcılara lisans atama](assign-licenses-to-users.md) (makale)\
[İş için Microsoft 365'teki abonelikleri ve lisansları anlama](../../commerce/licenses/subscriptions-and-licenses.md) (makale)
