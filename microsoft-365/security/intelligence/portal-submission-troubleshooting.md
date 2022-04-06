---
title: Yönetici bloğu tarafından kaynaklanan MSI portal hatalarının sorunlarını giderme
description: MSI portal hatalarının sorunlarını giderme
ms.reviewer: ''
keywords: güvenlik, örnek gönderim yardımı, kötü amaçlı yazılım dosyası, virüs dosyası, truva dosyası, gönder, Microsoft'a gönder, örnek, virüs, truva, solucan, algılanmadı, algılanmadı, microsoft'a e-posta, kötü amaçlı yazılım e-posta gönder, Bunun kötü amaçlı yazılım olduğunu düşünüyorum, bunun bir virüs olduğunu düşünüyorum, virüs bu virüs olabilir, bu bir virüs, MSE algılanmadı, imza yok, algılama yok, şüpheli dosya,  MMPC, Microsoft Kötü Amaçlı Yazılımdan Koruma Merkezi, araştırmacı, analist, WDSI, güvenlik zekası
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: e70eb5192a1fd6171b8e515509ad336aa99a2c63
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63705782"
---
# <a name="troubleshooting-malware-submission-errors-caused-by-administrator-block"></a>Yönetici bloğu tarafından neden olan kötü amaçlı yazılım gönderimi hatalarını giderme
Bazı durumlarda, çözümleme için [Microsoft Security intelligence](https://www.microsoft.com/wdsi) web sitesine virüs bulaşmış olabilecek bir dosyayı göndermek için bir yönetici bloğu gönderim sorunlarına neden olabilir. Aşağıdaki işlem, bu sorunun nasıl çözüleceklerini gösterir.

## <a name="review-your-settings"></a>Ayarlarınızı gözden geçirme
Azure Enterprise [uygulama ayarlarınızı açın](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/). Uygulama **Enterprise** **Kullanıcıları** >  , şirket verilerine kendi adına erişen uygulamaları kabul edip Evet veya Hayır'ın seçili olup olmadığını kontrol edin.

- Hayır **seçilirse** , müşteri kiracısı için bir Azure AD yöneticisinin kuruluş için izin sağlaması gerekir. Azure AD'nin yapılandırmasına bağlı olarak, kullanıcılar aynı iletişim kutusundan hemen bir istek gönderebilirsiniz. Yönetici onayı isteme seçeneği yoksa, kullanıcıların Azure AD yöneticilerine bu izinlerin eklenmesini istemeleri gerekir. Daha fazla bilgi için aşağıdaki bölüme gidin.

- Evet **seçiliyse**, Kullanıcıların oturum açması için Windows Defender **Security** Intelligence uygulaması ayarının Azure'da Evet olarak **ayarildiğinden** [emin olun](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d).Hayır **seçiliyse** , bir Azure AD yöneticisinin etkinleştirmesi için istekte bulundurabilirsiniz. 
  
## <a name="implement-required-enterprise-application-permissions"></a>Uygulama Enterprise Uygulamak 
Bu işlem için kiracıda genel yönetici veya uygulama yöneticisi gerekir.
 1. Uygulama [Enterprise'i açın](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d). 
 2. Kuruluş **için yönetici izni ver'i seçin**.
 3. Bunu yapabilirsiniz, aşağıdaki resimde de olduğu gibi, bu uygulama için gereken API izinlerini gözden geçirebilirsiniz. Kiracı için izin alın.

    ![izin resmi ver.](../../media/security-intelligence-images/msi-grant-admin-consent.jpg)

  4. Yönetici el ile izin sağlamayı denirken bir hata alırsa, olası geçici çözüm olarak [Seçenek 1](#option-1-approve-enterprise-application-permissions-by-user-request) veya [Seçenek 2'den](#option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin) birini deneyin.
  
## <a name="option-1-approve-enterprise-application-permissions-by-user-request"></a>1. Seçenek Kurumsal uygulama izinlerini kullanıcı isteğiyle onaylama
> [!Note]
> Bu şu anda bir önizleme özelliğidir.

Azure Active Directory kullanıcıların uygulamalar için yönetici izni isteği kullanmasına izin vermeleri gerekir. Enterprise uygulamalarında **ayarın** [Evet olarak yapılandırıldığından emin Enterprise.](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/)

![Enterprise ayarlarını değiştirin.](../../media/security-intelligence-images/msi-enterprise-app-user-setting.jpg)

Yönetici izni iş akışını yapılandırma [altında daha fazla bilgi edinebilirsiniz](/azure/active-directory/manage-apps/configure-admin-consent-workflow).

Bu ayar doğrulandıktan sonra, kullanıcılar [Microsoft](https://www.microsoft.com/wdsi/filesubmission) güvenlik zekası'nda kurumsal müşteri oturum açma bilgilerine gidebilir ve gerekçelendirme de içinde olmak üzere yönetici onayı için bir istek gönderebilirsiniz.

![Contoso oturum açma akışı.](../../media/security-intelligence-images/msi-contoso-approval-required.png)

Yönetici, Azure yönetici izin isteklerini uygulama izinlerini gözden [geçirip onaylar](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AccessRequests/menuId/).

İzin verdikten sonra, kiracının tüm kullanıcıları uygulamayı kullanabilir.
  
## <a name="option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin"></a>2. Seçenek Uygulamanın yönetici olarak kimlik doğrulamasını kullanarak yönetici izni sağlama 
Bu işlem, genel yöneticilerin Microsoft güvenlik Enterprise müşteri oturum açma akışı [sırasından geçen süreci takiplemektedir](https://www.microsoft.com/wdsi/filesubmission).

![İzin oturum açma akışı.](../../media/security-intelligence-images/msi-microsoft-permission-required.jpg)

Ardından yöneticiler izinleri gözden geçirerek, organizasyonu adına İzin'i **ve ardından Kabul Et'i** **seçin**.

Kiracının tüm kullanıcıları artık bu uygulamayı kullanabilir.

## <a name="option-3-delete-and-readd-app-permissions"></a>3. Seçenek: Uygulama izinlerini silme ve okuma
Bu seçeneklerden hiçbiri sorunu çözmezse, aşağıdaki adımları deneyin (yönetici olarak):

1. Uygulamanın önceki yapılandırmalarını kaldırma. Diğer [uygulamalara Enterprise sil'i](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/982e94b2-fea9-4d1f-9fca-318cda92f90b) **seçin**.

   ![Uygulama izinlerini silme.](../../media/security-intelligence-images/msi-properties.png)

2. Özellikler'den KiracıKimlik [Yakalama](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).

3. {tenant-id} öğesini aşağıdaki URL'de bu uygulamaya izin vermek için gereken belirli kiracıyla değiştirin. Bu URL'yi tarayıcıya kopyalayın. Parametrelerin kalanları zaten tamamlanmış durumdadır. 
``https://login.microsoftonline.com/{tenant-id}/v2.0/adminconsent?client_id=f0cf43e5-8a9b-451c-b2d5-7285c785684d&state=12345&redirect_uri=https%3a%2f%2fwww.microsoft.com%2fwdsi%2ffilesubmission&scope=openid+profile+email+offline_access``

   ![İzinler gerekli.](../../media/security-intelligence-images/msi-microsoft-permission-requested-your-organization.png)

4. Uygulamanın gerekli izinlerini gözden geçirerek Kabul Et'i **seçin**. 

5. [Azure portalda uygulanan izinleri onaylayın](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/ce60a464-5fca-4819-8423-bcb46796b051).

   ![İzinlerin uygulandığını gözden geçirebilirsiniz.](../../media/security-intelligence-images/msi-permissions.jpg)
   
6. Erişiminiz olup [olduğunu görmek için yönetici](https://www.microsoft.com/wdsi/filesubmission) olmayan bir hesabı olan kurumsal bir kullanıcı olarak Microsoft güvenlik zekası'ta oturum açın.

 Bu sorun giderme adımlarını izleyin ve uyarıyı çözemezse Microsoft desteğini arayın.