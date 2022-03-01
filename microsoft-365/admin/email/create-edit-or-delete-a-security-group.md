---
title: Grupta güvenlik grubu oluşturma, düzenleme veya Microsoft 365 yönetim merkezi
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
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
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 55c96b32-e086-4c9e-948b-a018b44510cb
description: Güvenlik grubu oluşturma, düzenleme veya silmeyi öğrenin.
ms.openlocfilehash: 3f054842abc5111c654b8da02afc418c36f7db11
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018777"
---
# <a name="create-edit-or-delete-a-security-group-in-the-microsoft-365-admin-center"></a>Grupta güvenlik grubu oluşturma, düzenleme veya Microsoft 365 yönetim merkezi

Microsoft 365 **Grupları sayfasında**, SharePoint Online ve CRM Online'da aynı izinleri atamak için kullanabileceğiniz kullanıcı hesabı grupları oluşturabilirsiniz. Örneğin, yönetici belirli bir grup kişinin site sitelerine erişim izni vermek için bir SharePoint oluşturabilir. Yalnızca genel yöneticilerin ve kullanıcı yönetimi yöneticilerinin güvenlik gruplarını oluşturma, düzenleme veya silme izinleri vardır; Yönetici rolleri hakkında daha fazla bilgi için bkz [. Yönetici rolleri atama](../add-users/assign-admin-roles.md). 
  
Ayrıca, bir grup kullanıcıya e-posta göndermek ve izin atamak için kullanabileceğiniz [Exchange Online ve SharePoint Online'daki gruplar](#groups-in-exchange-online-and-sharepoint-online) ve kullanıcı hakları ve siteler ile site koleksiyonlarına erişim veren [Exchange Online ve SharePoint Online'daki gruplar](#groups-in-exchange-online-and-sharepoint-online) da bulunur. 
  
> [!IMPORTANT]
>  Site posta kutularını kullanmayı mı planlıyorsunuz? SharePoint sitesine, tek tek eklenmek yerine güvenlik grubu aracılığıyla eklenen tüm kullanıcılar, posta kutusundan yalnızca site posta kutusunu SharePoint. Bu kullanıcılar site posta kutusuna posta kutusundan eriş Outlook. Daha fazla bilgi için bkz[. Site Microsoft 365 Kutuları yerine Posta Grupları Kullanma](https://support.microsoft.com/office/737d6b1f-67cc-41fe-8db8-f2d09dd1673b). 
  
## <a name="manage-security-groups-in-the-admin-center"></a>Yönetim merkezinde güvenlik gruplarını yönetme

### <a name="add-a-security-group"></a>Güvenlik grubu ekleme

1. Grup Microsoft 365 yönetim merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">GroupsGroups</a>  >  sayfasına gidin.
  
2. Gruplar **sayfasında Grup** **ekle'yi seçin**.
    
3. Grup **türü seçin sayfasında Güvenlik'i** **seçin**. 
    
4. Grup oluşturma işlemini tamamlamak için adımları izleyin. 
 
### <a name="add-members-to-a-security-group"></a>Güvenlik grubuna üye ekleme
    
1. Gruplar sayfasında güvenlik grubu adını **seçin ve Üyeler** sekmesinde **Tüm üyeleri** görüntüle ve **yönet'i seçin**. 
    
2. Grup bölmesinde Üye **ekle'yi** seçin ve listeden kişiyi seçin veya Arama kutusuna eklemek istediğiniz kişinin adını yazın ve ardından Kaydet'i **seçin**.
    
    Üyeleri kaldırmak için, adının yanındaki X'i seçin. 
  
### <a name="edit-a-security-group"></a>Güvenlik grubunu düzenleme

1. Yönetim merkezinde Gruplar Grupları **sayfasına** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">gidin.</a>
  
2. Gruplar **sayfasında** grubun adını seçin. 
    
3. Ayarlar bölmesinde, grup **ayrıntılarını veya üyeleri** **düzenlemek için Genel** sekmesini veya Üyeler sekmesini seçin.

### <a name="delete-a-security-group"></a>Güvenlik grubunu silme

1. Yönetim merkezinde <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">GroupsGroups</a>  >  sayfasına gidin.
    
2. Gruplar **sayfasında** grubun adını seçin. 
    
3. Grubu **sil'i** (wasetbin simgesi) seçin ve ardından Sil'i seçerek **onaylayın**.
    
    Grup **silindikten** sonra Kapat'ı seçin. 
    
## <a name="groups-in-exchange-online-and-sharepoint-online"></a>Exchange Online ve SharePoint Online'daki gruplar

Aynı anda tüm kullanıcılara  \>  \>  \> e-posta göndermek için kullanıcı grupları oluşturmak Exchange Yönetim Merkezi'nde Alıcı Grupları Yöneticisi'ne Exchange <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">**.**</a> Ardından NewAdd'yi ![](../../media/328ffb57-5f31-430a-b653-4a6b8e76d338.png)seçin ve oluşturmak istediğiniz grup türlerini seçin: 
  
- **Dağıtım grubu**: Bir grup kullanıcıya ileti dağıtmak için kullanılır. Buna posta özelliği etkin  *dağıtım grubu veya dağıtım* listesi de  *denir*. Daha fazla bilgi için bkz. [Dağıtım gruplarını yönetme](/exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups).
    
- **Güvenlik grubu**: Bir grup kullanıcıya ileti dağıtmak veya kaynaklara erişim izinleri vermek için kullanılabilir. Bu gruba posta etkin güvenlik *grubu da denir*. Daha fazla bilgi için bkz [. Posta etkin güvenlik gruplarını yönetme](/Exchange/recipients/mail-enabled-security-groups).
    
- **Dinamik dağıtım grubu**: Her ileti gönderken tanımladığınız filtrelere ve koşullara göre yeniden hesaplanan bir dağıtım grubu t türü. Daha fazla bilgi için bkz [. Dinamik dağıtım gruplarını yönetme](/Exchange/recipients/dynamic-distribution-groups/dynamic-distribution-groups).
    
Siz yönetim merkezinde dağıtım gruplarını ve posta etkin güvenlik <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">gruplarını Exchange</a>, bu grupların adları ve kullanıcı listeleri Güvenlik **grupları sayfasında** görüntülenir. Bu grupları iki farklı konumdan da silebilirsiniz, ancak yalnızca Exchange yönetim merkezinde düzenleyebilirsiniz. Dinamik dağıtım grupları Güvenlik grupları **sayfasında gösterlanmaz** . 
  
 SharePoint koleksiyonu oluşturulduğunda otomatik olarak grup oluşturulur. Varsayılan gruplar, kullanıcılara hak ve erişim vermek için SharePoint olarak da SharePoint görevlerdeki varsayılan izin düzeylerini kullanır. Daha fazla bilgi için bkz[. SharePoint Online'daki varsayılan SharePoint.](/sharepoint/default-sharepoint-groups)
  
## <a name="how-is-a-security-group-different-from-security-groups-i-create-in-sharepoint"></a>Güvenlik grubunun, güvenlik grubundan farklı olan gruplarla SharePoint?

Güvenlik grupları güvenlik grupları SharePoint, Exchange, MDM, Windows ve daha fazlası ile kullanılabilir. Bu sitede oluşturtuz güvenlik SharePoint yalnızca o site koleksiyonu SharePoint tanınır.
  
## <a name="do-i-have-to-use-security-groups-for-my-organization-to-be-secure"></a>Kuruluşumda güvenli olması için güvenlik gruplarını kullanmam gerekir mi?

Hayır. Bu, kurum için güvenliği yönetmek için tek bir yol sağlar. Her zaman kullanıcı izinleri ve sitelere bireysel olarak erişim ve izni veebilirsiniz. Ancak güvenlik gruplarında daha büyük kullanıcı gruplarını kolayca yönetebilirsiniz.
  
## <a name="can-i-send-email-to-a-security-group"></a>Güvenlik grubuna e-posta gönderebilir miyim?

Evet. Ancak, grupları e-posta ve işbirliği için kullanmak istemeniz halinde, bunun yerine bir Microsoft 365 [grubu oluşturmanızı](../create-groups/create-groups.md) öneririz. 

## <a name="related-content"></a>İlgili içerik

[Grup oluşturma Microsoft 365 yönetim merkezi](../create-groups/create-groups.md) (makale)\
[Kullanıcılarınıza Microsoft 365 Grupları Açıklama](../create-groups/explain-groups-knowledge-worker.md) (makale)\
[Grup yönetme Microsoft 365 yönetim merkezi](../create-groups/manage-groups.md) (makale)