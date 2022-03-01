---
title: Uygulama başlatıcıya özel kutucuklar ekleme
f1.keywords:
- CSH
ms.author: twerner
author: twernermsft
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
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 1136115a-75af-4497-b693-640c4ce70bc6
description: Uygulama başlatıcıya özel kutucuklar ekleyerek e-postanıza, belgelerinize, SharePoint sitenize, dış sitenize ve diğer kaynaklarınıza hızlı bağlantılar oluşturun.
ms.openlocfilehash: 31121df0e1af6b8fc2be1e61ba7e0cd0714affa2
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63016690"
---
# <a name="add-custom-tiles-to-the-app-launcher"></a>Uygulama başlatıcıya özel kutucuklar ekleme

Uygulama Microsoft 365 başlatıcıyı kullanarak e-postanıza, takvimlerinize, belgelerinize ve uygulamalarınıza hızla ve kolayca [ulaşabilirsiniz (daha fazla bilgi edinin](https://support.microsoft.com/office/79f12104-6fed-442f-96a0-eb089a3f476a)). Bunlar, office 365 Microsoft 365 yanı sıra [Mağaza veya Azure AD'den](/previous-versions/office/office-365-api/) [SharePoint özel](https://support.microsoft.com/office/dd98e50e-d3db-4ecb-9bb7-82b189822d43) uygulamaları alır.
  
Uygulama başlatıcıya, SharePoint sitelerini, dış siteleri, eski uygulamaları ve diğer uygulamaları gösteren kendi özel kutucuklarınızı ekleyebilirsiniz. Özel kutucuk, uygulama başlatıcının **Tüm uygulamalar** bölümünün altında görünür, ancak bunu **Giriş ekranına** sabitleyebilir ve kullanıcılarınızdan da aynı işlemi yapmalarını isteyebilirsiniz. Bu, işinizi yapmak için ilgili site, uygulama ve kaynakları bulmayı kolaylaştırır. Aşağıdaki örnekte, bir kuruluşun SharePoint intranet sitesine erişmek için "Contoso Portalı" adlı özel bir kutucuk kullanılmaktadır. 
  
![Uygulama başlatıcı.](../../media/7acc06cc-ac7a-4c6e-8ea7-81570a5bdbab.png)
  
## <a name="add-a-custom-tile-to-the-app-launcher"></a>Uygulama başlatıcıya özel kutucuk ekleme

1. Yönetim merkezinde Genel Yönetici olarak oturum açın,  >  Genel Yönetici Ayarlar **Gizle'Ayarlar** gidin ve Kuruluş **profili sekmesini** seçin.
    
2. Kuruluş profili **sekmesinde Özel** uygulama **başlatıcısı kutucukları'nı seçin**.
  
3. Özel **kutucuk ekle'yi seçin**. 
  
4. Yeni kutucuk için **Kutucuk adı** girin. Bu ad, kutucuk içinde görünür. 
    
5. Kutucuk için **web sitesinin URL'sini** girin. Bu, kullanıcılarınızı uygulama başlatıcıda kutucuğu seçinken gitmelerini istediğiniz konumtur. URL'de HTTPS kullanın.

    > [!TIP]
    > Bir SharePoint sitesi için kutucuk oluşturuyorsanız, bu siteye gidin, URL'yi kopyalayın ve buraya yapıştırın. Varsayılan ekip sitesinin URL'si şöyle olur: `https://<company_name>.sharepoint.com` 
  
6. Kutucuk **için resmin URL'sini** girin. Resim, Uygulamalarım sayfasında ve uygulama başlatıcısında görüntülenir.

    > [!TIP]
    > Resim 60x60 piksel olmalıdır ve kimlik doğrulamasına gerek kalmadan kuruluşta herkes tarafından kullanılabilir.

7. Kutucuk için bir **Açıklama** girin. Uygulamalarım sayfasında kutucuğu seçerek Uygulama ayrıntıları'nın seçerek bunu **görebilirsiniz**. 
  
8. Özel **kutucuğu oluşturmak** için Değişiklikleri kaydet'i seçin. 
    
    Özel kutucuğunuz sonraki 24 saat içinde, siz ve kullanıcılarınız için **Tüm** sekmesindeki uygulama başlatıcıda görünür. 

    > [!NOTE]
    > Önceki adımlarda oluşturulmuş özel kutucuğu görmüyorsanız, size atanmış bir Exchange Online posta kutunuzun olduğundan ve posta kutunuzda en az bir defa oturum açtığınızdan emin olun. Bu adımlar, veri sayfalarındaki özel kutucuklar Microsoft 365. 
  
## <a name="edit-or-delete-a-custom-tile"></a>Edit or delete a custom tile

1. Yönetim merkezinde Düzenleme Ayarlar  > **Org Ayarlar** >  **Düzenleme profili sekmesine** gidin.
    
2. Kuruluş profili **sayfasında** Özel Uygulama başlatıcı kutucukları'nı **seçin. Özel** Kutucuğun yanındaki üç noktayı ve  Özel kutucuğu **düzenle'yi seçersiniz**.

3. Özel kutucuk için **Kutucuk adı**, **URL**, **Açıklama** veya **Resim URL'si**'ni güncelleştirin ([Uygulama başlatıcıya özel kutucuk ekleme](#add-a-custom-tile-to-the-app-launcher) bakın).
    
4. Güncelleştir **Kapat'ı** \> **seçin**. 
    
Özel bir kutucuğu silmek için, Özel **kutucuklar** penceresinde kutucuğu seçin, Kutucuğu **kaldırDelete'yi** >  seçin. 
  
## <a name="next-steps"></a>Sonraki adımlar

 Tema görünümünü, Microsoft 365 markanıza göre özelleştirmek için bkz. Tema Microsoft 365 [özelleştirme](../setup/customize-your-organization-theme.md).

## <a name="related-content"></a>İlgili içerik

[Uygulamaları kullanıcılarının uygulama başlatıcısına sabitleme](pin-apps-to-app-launcher.md) (makale)\
[Kurumsal kullanıcıları Microsoft 365 son istemciye yükseltme (Office](../setup/upgrade-users-to-latest-office-client.md))\
[Yönetim merkezinde eklentileri yönetme](../manage/manage-addins-in-the-admin-center.md) (makale)
