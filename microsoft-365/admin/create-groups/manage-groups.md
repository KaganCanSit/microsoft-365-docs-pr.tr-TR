---
title: Yönetim merkezinde grubu yönetme
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 74a1ef8b-3844-4d08-9980-9f8f7a36000f
description: Grup üyelerini Microsoft 365 kaldırma, e-posta adresini, grup adını veya açıklamayı düzenleme ve grubun çalışma nasıl çalıştığını özelleştirme gibi Grupları yönetmeyi öğrenin.
ms.openlocfilehash: e04d91219f1bfd51b609b9be749bd98c2798a52a
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016480"
---
# <a name="manage-a-group-in-the-microsoft-365-admin-center"></a>Grup içinde bir grubu Microsoft 365 yönetim merkezi

Grup [üyelerini oluşturduktan Microsoft 365 üyeleri](create-groups.md) ekledikten sonra, grubunızı yapılandırarak. Grup adını veya açıklamasını düzenleyebilir, sahipleri veya üyeleri yönetebilir ve dış gönderenlerin gruba e-posta gönderip göndereyeyeceklerini ve grup konuşmalarının kopyalarının üyelere gönderip gönderemezseniz belirtebilirsiniz.

Microsoft 365 yönetim merkezi gidin[https://admin.microsoft.com](https://admin.microsoft.com).

## <a name="edit-the-group-name-or-description"></a>Grup adını veya açıklamasını düzenleme

1. Yönetim merkezinde Gruplar'ı **genişletin ve** Gruplar'a <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**tıklayın**</a>.

2. Düzenlemek istediğiniz grubu seçin ve ardından Ad ve açıklamayı **düzenle'ye tıklayın**.

3. Adı ve açıklamayı güncelleştirin ve ardından Kaydet'i **seçin**.

## <a name="manage-group-owners-and-members"></a>Grup sahiplerini ve üyeleri yönetme

1. Yönetim merkezinde Gruplar'ı **genişletin ve** Gruplar'a <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**tıklayın**</a>.

2. Ayarlar bölmesini açmak için yönetmek istediğiniz grubun adına tıklayın.

3. Üyeler **sekmesinde,** sahipleri veya üyeleri yönetmek mi istediğinize tıklayın.

4. Birini **eklemek için** Ekle'yi seçin veya **birini kaldırmak için X'i** tıklatın.

5. **Kapat**'a tıklayın.

## <a name="send-copies-of-conversations-to-group-members-inboxes"></a>Konuşmaların kopyalarını grup üyelerinin gelen kutularına gönderme
  
Yönetim merkezini grup oluşturmak için kullanırsanız, varsayılan olarak kullanıcılar gelen kutularına gönderilen grup e-postalarının kopyalarını almak yerine, grup toplantı davetlerinin kopyalarını kendi gelen kutularına gönderilir. Konuşmaları görmek için gruba gitmeleri gerekir. Bu ayarı yönetim merkezinden değiştirebilirsiniz.

Bu ayarı etkinleştirirseniz, grup üyeleri kendi posta kutularına gönderilen grup e-postalarının ve toplantı davetlerinin bir kopyasını Outlook gönderilir. E-postanın bu kopyasını okuyup silebilirler ve diğer kullanıcılar bundan etkilenmez. E-postanın bir kopyası Grup gelen kutusunda kalır.

Grup üyeleri, grup içinde grubu takip etmeyi durdur'a seçerek bu e-postaları Outlook.

1. Yönetim merkezinde Gruplar'ı **genişletin ve** Gruplar'a <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**tıklayın**</a>.

2. Ayarlar bölmesini açmak için yönetmek istediğiniz grubun adına tıklayın.

3. Grup **Ayarlar**, üyelerin grup iletilerinin  ve takvim öğelerinin kopyalarını kendi gelen kutularına almalarını istemiyorsanız, Grup konuşmalarının ve olaylarının kopyalarını grup üyelerine gönder'i seçin.

4. **Kaydet**'i seçin.

## <a name="let-people-outside-the-organization-email-the-group"></a>Kuruluş dışındaki kişilerin gruba e-posta göndermesine izin verme

E-posta adresi gibi bir şirket e-posta adresine sahip olmak info@contoso.com.
 
1. Yönetim merkezinde Gruplar'ı **genişletin ve** Gruplar'a <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**tıklayın**</a>.

2. Ayarlar bölmesini açmak için yönetmek istediğiniz grubun adına tıklayın.

3. Yönetim merkezi grupları listesinde, değiştirmek istediğiniz grubun adını seçin ve sonra Ayarlar sekmesinde Dış gönderenlerin bu gruba **e-posta** göndermesine izin **ver'i seçin**.
    
4. **Kaydet**'i seçin.

> [!NOTE]
> Kuruluş dışındaki kullanıcıların gruba e-posta göndermesi 30 dakika kadar sürebilir.

## <a name="permanently-delete-a-microsoft-365-group"></a>Yeni Grup grubunu Microsoft 365 silme

Bazen, 30 günlük geçici silme süresini beklemeden bir grubu kalıcı olarak temizlemek istiyor olabilir. Bunu yapmak için PowerShell'i başlatın ve şu komutu çalıştırarak grubun nesne kimliğini alın:
 
 ```powershell
Get-AzureADMSDeletedGroup
```

Kalıcı olarak silmek istediğiniz grubun veya grupların nesne kimliğini not alma.
  
> [!CAUTION]
> Grubun temizlenmesi, grubu ve verilerini sonsuza kadar kaldırır. 
  
Grubu temizlemek için PowerShell'de şu komutu çalıştırın:

```powershell
Remove-AzureADMSDeletedDirectoryObject -Id <objectId>
```

Grubun başarıyla temizlendiğini onaylamak için,  *Get-AzureADMSDeletedGroup*  cmdlet'ini yeniden çalıştırarak grubun artık geçici silinmiş gruplar listesinde gösterilmediğini onaylayın. Bazı durumlarda grubun ve tüm verilerinin kalıcı olarak silinmesi 24 saat kadar sürebilir. 
  
## <a name="related-articles"></a>İlgili makaleler

[Grup Microsoft 365 oluşturma](create-groups.md)

[Gruplarda konuk erişimini Microsoft 365 yönetme](https://support.microsoft.com/office/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Grup oluştururken kullanmak istediğiniz etki Microsoft 365 seçin](../../solutions/choose-domain-to-create-groups.md)

[Üyelerin grup olarak veya bir grup adına göndermesine Microsoft 365 verme](../../solutions/allow-members-to-send-as-or-send-on-behalf-of-group.md)

[Dağıtım listelerini Gruplara Microsoft 365 yükseltme](../manage/upgrade-distribution-lists.md)

[PowerShell Microsoft 365 Grupları Yönetme](../../enterprise/manage-microsoft-365-groups-with-powershell.md)
