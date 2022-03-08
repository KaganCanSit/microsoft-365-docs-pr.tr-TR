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
description: Ürün lisanslarının atamasını iptal etmek için kullandığınız yöntem, lisans atamalarını belirli kullanıcılardan mı yoksa belirli bir üründen mi iptal ettiğine bağlıdır.
ms.date: 09/16/2021
ms.openlocfilehash: 7308888c54a30cdd11618cb07a233f8bd55f27c2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63321215"
---
# <a name="unassign-licenses-from-users"></a>Kullanıcıların lisans atamalarını kaldırma

Etkin kullanıcılar sayfasında veya Lisanslar sayfasında **kullanıcılardan lisans** **atamalarını iptal** edebilirsiniz. Kullandığınız yöntem, belirli kullanıcıların ürün lisanslarının atamasını mı almak istediğinize yoksa belirli bir üründen kullanıcı lisanslarının atamasını mı almak istediğinize bağlıdır.

> [!NOTE]
> 
> - Yönetici olarak, kurumda bir kullanıcı tarafından satın alınan self servis satın alma aboneliği için lisans atayayam veya atamalarını iptal edilemez. Self [servis satın alma aboneliğini üzerine alıp](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription) lisansları atayın veya atamalarını iptal edin.
> 
> - Bazı abonelikler için, aboneliğinizi satın alıp yeniledikten sonra yalnızca sınırlı bir süre içinde iptal edebilirsiniz. İptal etme penceresi sona ererse, süresi sonunda aboneliği iptal etmek için yinelenen faturalamayı kapatın.

## <a name="before-you-begin"></a>Başlamadan önce

- Lisans atamalarını geri almak için Genel, Lisans, Kullanıcı yöneticisi siz olmak gerekir. Daha fazla bilgi için bkz[. Microsoft 365 rolleri hakkında](../add-users/about-admin-roles.md).
- [Office 365 PowerShell ile kullanıcı hesaplarından lisansları kaldırabilirsiniz](../../enterprise/remove-licenses-from-user-accounts-with-microsoft-365-powershell.md).
- Ayrıca, [lisans atanmış kullanıcı](../add-users/delete-a-user.md) hesaplarını silebilir ve bu hesapların lisansını diğer kullanıcılara açık haleebilirsiniz. Bir kullanıcı hesabını silebilirsiniz ve bu kişinin lisansı hemen başka birine atanabilirsiniz.

## <a name="use-the-licenses-page-to-unassign-licenses"></a>Lisans atamalarını iptal etmek için Lisanslar sayfasını kullanma

Lisans atamalarını **iptal** etmek için Lisanslar sayfasını kullanırken, belirli bir ürünün lisanslarının atamasını en çok 20 kullanıcı için iptal etmiş oluruz.

::: moniker range="o365-worldwide"

1. Yönetim merkezinde Fatura Lisansları **sayfasına** \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezinde Fatura Lisansları **sayfasına** \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank"></a>

::: moniker-end

2. Lisans atamalarını iptal etmek istediğiniz ürünü seçin.

3. Lisans atamalarını iptal etmek istediğiniz kullanıcıları seçin.

4. Lisans **atamasını iptal et'i seçin**.

5. Lisans **atamasını iptal et kutusunda** Atamayı **Seç'i seçin**.

## <a name="use-the-active-users-page-to-unassign-licenses"></a>Lisans atamalarını iptal etmek için Etkin kullanıcılar sayfasını kullanma

Lisans atamalarını **iptal etmek** için Etkin kullanıcılar sayfasını kullanırken, kullanıcılardan ürün lisanslarının atamalarını iptal etmiş oluruz.

### <a name="unassign-licenses-from-one-user"></a>Bir kullanıcının lisans atamasını iptal et

::: moniker range="o365-worldwide"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

2. Lisans atamasını iptal etmek istediğiniz kullanıcının satırına seçin.

3. Sağ bölmede, **Lisanslar ve Uygulamalar**'ı seçin.

4. Lisanslar **bölümünü** genişletin, atamasını silmek istediğiniz lisansların kutularını temizleyin ve ardından Değişiklikleri **kaydet'i seçin**.

### <a name="unassign-licenses-from-multiple-users"></a>Birden çok kullanıcının lisans atamasını iptal et

::: moniker range="o365-worldwide"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

2. Lisans atamalarını iptal etmek istediğiniz kullanıcıların adlarının yanındaki daireleri seçin.

3. Üst kısmında Ürün lisanslarını **yönet'i seçin**.

4. Ürün **lisanslarını yönet bölmesinde** Tüm Kaydetme **değişikliklerinin atamasını** **aç'ı** >  seçin.

5. Bölmenin en altında Bitti'yi **seçin**.  

## <a name="what-happens-to-a-users-data-when-you-remove-their-license"></a>Lisansını kaldıran bir kullanıcının verilerine ne olur?

- Kullanıcıdan lisans kaldırıldığı zaman, Exchange hesabıyla ilişkilendirilmiş tüm çevrimiçi veriler 30 gün süreyle tutulacak. 30 günlük yetkisiz kullanım süresi sonrasında veriler silinir ve kurtarılamaz.
- Kullanıcı dosyalardan OneDrive İş Active Directory eşitlemesi aracılığıyla silinmedikçe Microsoft 365 yönetim merkezi dosyalar silinmez. Daha fazla bilgi için bkz[. bekletme OneDrive silme.](/onedrive/retention-and-deletion)
- Lisans kaldırıldığı zaman, kullanıcının posta kutusunda İçerik Arama veya İçerik Bulma gibi bir eBulma aracı kullanılarak arama Advanced eDiscovery. Daha fazla bilgi için, aynı adreste yer alan İçerik Arama'da "Bağlantısı kesik veya lisansları olmayan posta [kutularında arama" Microsoft 365](../../compliance/content-search.md).
- Enterprise E3 gibi bir Office 365 Kurumsal Enterprise aboneliğiniz varsa, Exchange Online etkin olmayan posta kutuları kullanarak silinmiş kullanıcı hesabının posta kutusu [verilerini korumanızı sağlar](../../compliance/inactive-mailboxes-in-office-365.md). Daha fazla bilgi için bkz[. Posta kutusunda etkin olmayan posta kutularını oluşturma Exchange Online](../../compliance/create-and-manage-inactive-mailboxes.md).
- Bir kullanıcının lisansı kaldırıldıktan sonra Microsoft 365 verilerine erişimini engellemeyi ve sonrasında verilere erişmeyi öğrenmek için bkz[. Eski çalışanı kaldırma](../add-users/remove-former-employee.md).
- Kullanıcının lisansını kaldırırsanız ve bu kullanıcının hala Office uygulaması yüklüyse, bu kullanıcının Office uygulamalarını kullanma sırasında Lisanssız Ürün [ve](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380) etkinleştirme hataları Office.

## <a name="next-steps"></a>Sonraki adımlar

Kullanılmayan lisansları diğer kullanıcılara yeniden atamayacaksanız[, gerekenden](../../managed-desktop/get-started/assign-licenses.md) daha fazla lisans için ödeme yapmak zorunda olmadığınız için lisansları aboneliğinden kaldırmayı göz önünde bulundurabilirsiniz.[](../../commerce/licenses/buy-licenses.md)

## <a name="related-content"></a>İlgili içerik

[Aboneliğinizin lisanslarını kaldırma](../../commerce/licenses/buy-licenses.md) (makale)\
[Kullanıcılara lisans atama](assign-licenses-to-users.md) (makale)\
[Microsoft 365 İş'te abonelikleri ve lisansları anlama](../../commerce/licenses/subscriptions-and-licenses.md) (makale)
