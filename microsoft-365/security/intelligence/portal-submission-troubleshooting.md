---
title: Yönetici bloğunun neden olduğu MSI portalı hatalarını giderme
description: MSI portalı hatalarını giderme
ms.reviewer: ''
keywords: güvenlik, örnek gönderim yardımı, kötü amaçlı yazılım dosyası, virüs dosyası, truva atı dosyası, gönder, Microsoft'a gönder, örnek gönder, virüs, truva atı, solucan, algılanmadı, algılanmadı, e-posta microsoft, e-posta kötü amaçlı yazılım, Bu kötü amaçlı yazılım, ben bir virüs olduğunu düşünüyorum, nerede virüs gönderebilirim, bu bir virüs, MSE, algılamaz, imza yok, algılama yok, şüpheli dosya,  MMPC, Microsoft Kötü Amaçlı Yazılımdan Koruma Merkezi, araştırmacılar, analist, WDSI, güvenlik zekası
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
ms.openlocfilehash: 544e96bd0a3985856f47bc8df424a2c2932f3c7e
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665678"
---
# <a name="troubleshooting-malware-submission-errors-caused-by-administrator-block"></a>Yönetici bloğunun neden olduğu kötü amaçlı yazılım gönderme hatalarını giderme

Bazı durumlarda, analiz için [Microsoft Güvenlik bilgileri web sitesine](https://www.microsoft.com/wdsi) virüs bulaşmış olabilecek bir dosya göndermeye çalıştığınızda yönetici bloğu gönderme sorunlarına neden olabilir. Aşağıdaki işlem bu sorunun nasıl çözüleceğini gösterir.

## <a name="review-your-settings"></a>Ayarlarınızı gözden geçirin

Azure [Enterprise uygulama ayarlarınızı](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/) açın. **uygulamalarKullanıcılar, şirket verilerine kendi adına erişen uygulamalara onay Enterprise** altında Evet veya Hayır'ın seçili olup olmadığını denetleyin. >  

- **Hayır** seçilirse, müşteri kiracısının Azure AD yöneticisinin kuruluş için onay sağlaması gerekir. Azure AD yapılandırmasına bağlı olarak, kullanıcılar doğrudan aynı iletişim kutusundan istek gönderebilir. Yönetici onayı isteme seçeneği yoksa, kullanıcıların bu izinlerin Azure AD yöneticilerine eklenmesini istemesi gerekir. Daha fazla bilgi için aşağıdaki bölüme gidin.

- **Evet** seçiliyse, Azure'da **kullanıcıların oturum açması için etkinleştirildi mi?** Windows Defender Güvenlik Zekası uygulama ayarının **Evet** olarak [ayarlandığından](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d) emin olun. **Hayır** seçiliyse bir Azure AD yöneticisinin etkinleştirmesini istemeniz gerekir.

## <a name="implement-required-enterprise-application-permissions"></a>Gerekli Enterprise Uygulama izinlerini uygulama

Bu işlem için kiracıda genel yönetici veya uygulama yöneticisi gerekir.

1. [Uygulama ayarlarını Enterprise](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d) açın.
2. **Kuruluş için yönetici onayı ver'i** seçin.
3. Bunu yapabiliyorsanız, aşağıdaki görüntüde gösterildiği gibi bu uygulama için gereken API izinlerini gözden geçirin. Kiracı için onay verin.

    ![onay görüntüsü verme.](../../media/security-intelligence-images/msi-grant-admin-consent.jpg)

4. Yönetici el ile onay vermeyi denerken bir hata alırsa, olası geçici çözümler olarak [Seçenek 1](#option-1-approve-enterprise-application-permissions-by-user-request) veya [Seçenek 2'yi](#option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin) deneyin.

## <a name="option-1-approve-enterprise-application-permissions-by-user-request"></a>Seçenek 1 Kullanıcı isteğine göre kurumsal uygulama izinlerini onaylama

> [!NOTE]
> Bu, şu anda bir önizleme özelliğidir.

Azure Active Directory yöneticilerin kullanıcıların uygulamalara yönetici onayı istemesine izin vermeleri gerekir. Ayarın [Enterprise uygulamalarda](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/) **Evet** olarak yapılandırıldığını doğrulayın.

![uygulama kullanıcı ayarlarını Enterprise.](../../media/security-intelligence-images/msi-enterprise-app-user-setting.jpg)

[Yönetici onayı iş akışını yapılandırma](/azure/active-directory/manage-apps/configure-admin-consent-workflow) bölümünde daha fazla bilgi bulabilirsiniz.

Bu ayar doğrulandıktan sonra, kullanıcılar [Microsoft güvenlik zekası'nda](https://www.microsoft.com/wdsi/filesubmission) kurumsal müşteri oturum açma işlemini yapabilir ve gerekçe dahil olmak üzere yönetici onayı için bir istek gönderebilir.

![Contoso oturum açma akışı.](../../media/security-intelligence-images/msi-contoso-approval-required.png)

Yönetici, [Azure yönetici onayı isteklerinin](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AccessRequests/menuId/) uygulama izinlerini gözden geçirebilir ve onaylayabilir.

Onay sağlandıktan sonra kiracıdaki tüm kullanıcılar uygulamayı kullanabilir.

## <a name="option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin"></a>Seçenek 2 Uygulamanın kimliğini yönetici olarak doğrulayarak yönetici onayı sağlama

Bu işlem, genel yöneticilerin [Microsoft güvenlik bilgilerindeki](https://www.microsoft.com/wdsi/filesubmission) Enterprise müşteri oturum açma akışından geçmelerini gerektirir.

![Onay oturum açma akışı.](../../media/security-intelligence-images/msi-microsoft-permission-required.jpg)

Ardından, yöneticiler izinleri gözden geçirir ve **kuruluşunuz adına Onay'ı** seçip **Kabul Et'i** seçtiğinizden emin olur.

Kiracıdaki tüm kullanıcılar artık bu uygulamayı kullanabilir.

## <a name="option-3-delete-and-readd-app-permissions"></a>Seçenek 3: Uygulama izinlerini silme ve okuma

Bu seçeneklerden hiçbiri sorunu çözmezse aşağıdaki adımları deneyin (yönetici olarak):

1. Uygulama için önceki yapılandırmaları kaldırın. [Enterprise uygulamalarına](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/982e94b2-fea9-4d1f-9fca-318cda92f90b) gidin ve **sil'i** seçin.

   ![Uygulama izinlerini silin.](../../media/security-intelligence-images/msi-properties.png)

2. [Özelliklerden TenantID'yi](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties) yakalayın.

3. {tenant-id} öğesini aşağıdaki URL'de bu uygulamaya onay vermesi gereken belirli bir kiracıyla değiştirin. Bu URL'yi tarayıcıya kopyalayın. Parametrelerin geri kalanı zaten tamamlandı.
``https://login.microsoftonline.com/{tenant-id}/v2.0/adminconsent?client_id=f0cf43e5-8a9b-451c-b2d5-7285c785684d&state=12345&redirect_uri=https%3a%2f%2fwww.microsoft.com%2fwdsi%2ffilesubmission&scope=openid+profile+email+offline_access``

   ![gerekli izinler.](../../media/security-intelligence-images/msi-microsoft-permission-requested-your-organization.png)

4. Uygulamanın gerektirdiği izinleri gözden geçirin ve **kabul et'i** seçin.

5. İzinlerin [Azure portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/ce60a464-5fca-4819-8423-bcb46796b051) uygulandığını onaylayın.

   ![İzinlerin uygulandığını gözden geçirin.](../../media/security-intelligence-images/msi-permissions.jpg)

6. Erişiminiz olup olmadığını görmek için [Microsoft güvenlik bilgileri'nde](https://www.microsoft.com/wdsi/filesubmission) yönetici olmayan bir hesapla kurumsal kullanıcı olarak oturum açın.

 Bu sorun giderme adımları izlendikten sonra uyarı çözümlenmezse Microsoft desteğini arayın.