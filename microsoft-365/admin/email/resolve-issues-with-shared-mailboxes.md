---
title: Paylaşılan posta kutularında sorunları çözme
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
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
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
description: Paylaşılan posta kutularını ayar yanlışlıklara neden olabilir. Paylaşılan posta kutularda sorun yaşanıyorsa bu çözümleri deneyin.
ms.openlocfilehash: 2be12810e6651da5b062afbd0a3437913b9a4d60
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973603"
---
# <a name="resolve-issues-with-shared-mailboxes"></a>Paylaşılan posta kutularında sorunları çözme

Paylaşılan posta kutusu oluştururken veya kullanırken hata iletileri görüyorsanız, şu olası çözümleri deneyin. 

## <a name="error-when-creating-shared-mailboxes"></a>Paylaşılan posta kutuları oluşturulurken hata oluştu
<a name="bkmk_Fix"> </a>

Hata iletisini görüyorsanız proxy adresleri **veya LegacyExchangeDN of "\<name>" proxy adresi "smtp:<\> paylaşılan posta kutusu adı" zaten kullanılıyordur. Lütfen başka bir ara sunucu** adresi seçin; bu, paylaşılan posta kutusuna zaten kullanmakta olan bir ad vermeye çalıştığınız anlamına gelir. Örneğin, paylaşılan posta kutularını info@domain1 ve info@domain2 olarak adlandırmak istediğinizi varsayalım. Bunu yapmanın iki yolu vardır:

  - Windows PowerShell'i kullanın. Yönergeler için bu blog gönderisi'ne bakın: [Farklı Etki Alanlarında Aynı Diğer Adlarla Paylaşılan Posta Kutuları Oluşturma](https://www.cogmotive.com/blog/office-365-tips/create-shared-mailboxes-with-same-alias-at-different-domains-in-office-365)
    
  - Hatadan kurtularak ikinci paylaşılan posta kutusuna en baştan farklı bir ad ve girin. Ardından yönetim merkezinde, paylaşılan posta kutusunu olması istediğiniz şekilde yeniden adlandırabilirsiniz.

## <a name="error-about-not-having-send-permissions-when-using-a-shared-mailbox"></a>Paylaşılan posta kutusu kullanırken izin gönderme hatası

Paylaşılan bir posta kutusu oluşturduysanız ve bu posta kutusundan ileti göndermeyi denerse, bunu alabilirsiniz:

**Bu ileti gönderilemdi. Belirtilen kullanıcı adına ileti gönderme izniniz yok.**

Bu ileti, Microsoft 365 bir yineleme gecikme sorunu yaşıyor olduğunda görüntülenir. Yeni paylaşılan posta kutunuz (veya kullanıcınız) ile ilgili bilgiler tüm veri merkezlerimizde çoğaltılırsa, bu bilgi bir saat içinde yok olur. Bir saat bekleyin ve sonra ileti göndermeyi yeniden deneyin.

## <a name="related-content"></a>İlgili içerik

[Paylaşılan posta kutuları hakkında](about-shared-mailboxes.md) (makale)\
[Paylaşılan posta kutusu oluşturma](create-a-shared-mailbox.md) (makale)\
[Paylaşılan posta kutusunu yapılandırma](configure-a-shared-mailbox.md) (makale)\
[Kullanıcı posta kutusunu paylaşılan posta kutusuna dönüştürme](convert-user-mailbox-to-shared-mailbox.md) (makale)\
[Paylaşılan posta kutusundan lisans kaldırma](remove-license-from-shared-mailbox.md) (makale)


    

