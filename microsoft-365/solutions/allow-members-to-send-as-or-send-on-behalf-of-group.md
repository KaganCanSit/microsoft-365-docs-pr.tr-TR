---
title: Üyelerin grup olarak veya bir grup adına göndermesine izin verme
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
- m365solution-collabgovernance
ms.custom: admindeeplinkEXCHANGE
search.appverid:
- MET150
ms.assetid: 0ad41414-0cc6-4b97-90fb-06bec7bcf590
recommendations: false
description: Grup üyelerinin bir grup olarak e-posta göndermesine Microsoft 365 veya grup adına e-posta göndermesine Microsoft 365 öğrenin.
ms.openlocfilehash: 588008669359629f5b59498bb7dbf776112d5408
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63401014"
---
# <a name="allow-members-to-send-as-or-send-on-behalf-of-a-group"></a>Üyelerin grup olarak veya bir grup adına göndermesine izin verme

Bir Microsoft 365 olarak gönderme veya Adına gönderme izinleri olan bir grup üyesi grup  olarak veya grup  adına e-posta gönderebilir. (Gruptaki konuklara bu izinler ver kullanılamaz.)

Bu makalede, genel veya yönetici Exchange bu izinleri nasıl ayary olduğu açıklanmıştır.
  
Örneğin, Oya Bowen **Eğitim Microsoft 365 grubunda** yer aldı ve grupta Gönderme izni varsa, grup olarak bir  e-posta gönderirse, e-posta Eğitim grubunun gönderdiği gibi olur. 
  
Adına **Gönderme izni,** kullanıcının bir grup adına e-posta gönderme Microsoft 365 sağlar. Örneğin, Pazarlama **ekibi Microsoft 365 grubunun** bir parçası olan Alex Wilber, Adına Gönderme izinlerine sahipse ve grup  olarak bir e-posta gönderirse, e-posta Pazarlama adına **Alex Wilber** tarafından gönderilmiş gibi görünüyor.

> [!IMPORTANT]
> Belirli bir kullanıcı **için Olarak** Gönder **veya Gönder'i** yapılandırmış, ancak her ikisi için birden yapılandıramazsanız. Her ikisini de yapılandırsanız, varsayılan olarak Gönder **ayarında kullanılır**.

> [!NOTE]
> **Karma yönetim** **ve yapılandırmalarda**, Farklı Gönder ve adına Mac için Outlook destek Exchange desteklanmaz.
    
## <a name="allow-members-to-send-email-as-a-group"></a>Üyelerin grup olarak e-posta göndermesine izin verme

Bu bölümde, kullanıcıların aynı adreste bulunan yönetim merkezinde <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">(EAC) grup olarak e Exchange e-posta göndermesine nasıl izin</a> Exchange Online.
  
1. Exchange yönetim merkezinde Alıcılar **Grupları'ne** \> <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">**gidin**</a>.
    
2. Kullanıcıların farklı göndermesine izin vermek istediğiniz grubu seçin. 
    
3.  >  Ayarlar **Edit temsilcilerini yönet'i seçin**.
    
4. Temsilci **ekle bölümünde** , Erişim olarak gönder'i istediğiniz kullanıcının e-posta **adresini** girin.
  
5. Açılan **listeden Farklı** **Gönder olarak İzin** Türü'ne seçin.

6.  Değişiklikleri **kaydet'i seçin**.
    
    
## <a name="allow-members-to-send-email-on-behalf-of-a-group"></a>Üyelerin grup adına e-posta göndermesine izin verme

Bu bölümde, kullanıcıların yönetim merkezinde (EAC) yer alan bir grup adına e-Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">e-posta göndermelerine nasıl izin</a> Exchange Online.
  
1. Exchange yönetim merkezinde Alıcılar **Grupları'ne** \> <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">**gidin**</a>.
    
2. Kullanıcıların adına göndermesine izin vermek istediğiniz grubu seçin. 
    
3.  >  Ayarlar **Edit temsilcilerini yönet'i seçin**.
    
4. Temsilci **ekle bölümünde** , Erişim olarak gönder'i istediğiniz kullanıcının e-posta **adresini** girin.
  
5. Açılan **listeden Adına** **Gönderme olarak İzin** Türü'ne seçin.

6.  Değişiklikleri **kaydet'i seçin**.

## <a name="related-articles"></a>İlgili makaleler

[Grup üyelerinden veya bu grup adına e-Microsoft 365 gönderme](https://support.microsoft.com/office/0f4964af-aec6-484b-a65c-0434df8cdb6b)

[İşbirliği yönetim planlaması önerileri](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[İşbirliği yönetim planınızı oluşturma](collaboration-governance-first.md)

[Gruplarla ilgili daha Microsoft 365 bilgi](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

[Add-RecipientPermission](/powershell/module/exchange/add-recipientpermission)

[Set-UnifiedGroup](/powershell/module/exchange/set-unifiedgroup)
