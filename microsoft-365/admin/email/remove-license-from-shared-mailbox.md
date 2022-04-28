---
title: Paylaşılan posta kutusundan lisans kaldırma
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
ms.reviewer: sinakassaw, nicholak
manager: scotv
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
search.appverid:
- BCS160
- MET150
- MOE150
description: 'Paylaşılan bir posta kutusundan lisansı kaldırarak başka bir kullanıcıya atayın veya lisansı iade edin; böylece bu lisansı ödemezsiniz. '
ms.date: 04/22/2022
ms.openlocfilehash: 4445163281e403505612066285192b31adc44979
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091929"
---
# <a name="remove-a-license-from-a-shared-mailbox"></a>Paylaşılan posta kutusundan lisans kaldırma

Paylaşılan posta kutuları genellikle lisans gerektirmez. Paylaşılan posta kutusundan lisansı kaldırmak için bu yönergeleri izleyin; böylece kullanıcıya atayabilir veya ihtiyacınız olmayan bir lisans için ödeme yapmamak için lisansı iade edebilirsiniz.

> [!NOTE]
>
> Aşağıdaki senaryolarda Exchange Online Plan 2 lisansı gereklidir:
>
> - Paylaşılan posta kutusunda 50 GB'tan fazla depolama alanı kullanılıyor.
> - Paylaşılan posta kutusu yerinde arşivleme kullanır.
> - Paylaşılan posta kutusu, dava beklemeye alınır.
> - Paylaşılan posta kutusuna atanmış bir Microsoft 365 Defender lisansı vardır.
> 
> Lisans atama hakkında adım adım yönergeler için bkz. [Kullanıcılara lisans atama](/microsoft-365/admin/manage/assign-licenses-to-users). 


## <a name="remove-the-license"></a>Lisansı kaldırma

::: moniker range="o365-worldwide"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

 1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

   > [!NOTE]
   > Lisansı Etkin kullanıcılar sayfasından kaldırmanız gerekir. Lisanslar kullanıcı ayarları olduğundan, paylaşılan posta kutusu sayfasından lisansı kaldıramazsınız.
  
2. Paylaşılan posta kutusunu seçin.

3. **Lisanslar ve Uygulamalar** **sekmesinden Lisanslar'ı** genişletin ve kaldırmak istediğiniz lisansın kutusunun işaretini kaldırın.

4. **Değişiklikleri kaydet'i** seçin.

5. **Etkin kullanıcılar** sayfasına döndüğünüzde, paylaşılan posta kutusunun durumu **Lisanssız** olur.

6. Hala lisans için ödeme yapıyorsun. Bunun için ödeme yapmayı durdurmak için [lisansı aboneliğinizden kaldırın](../../commerce/licenses/buy-licenses.md).

## <a name="related-content"></a>İlgili içerik

[Paylaşılan posta kutuları hakkında](about-shared-mailboxes.md) (makale)\
[Paylaşılan posta kutusu oluşturma](create-a-shared-mailbox.md) (makale)\
[Paylaşılan posta kutusunu yapılandırma](configure-a-shared-mailbox.md) (makale)\
[Kullanıcı posta kutusunu paylaşılan posta kutusuna dönüştürme](convert-user-mailbox-to-shared-mailbox.md) (makale)\
[Paylaşılan posta kutularıyla ilgili sorunları çözme](resolve-issues-with-shared-mailboxes.md) (makale)
