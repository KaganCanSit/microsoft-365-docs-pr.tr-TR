---
title: Android veya iOS cihazlara yönelik uygulama koruma ayarlarını belirleme
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: 6f2b80b4-81c3-4714-a7bc-ae69313e8a33
description: Android veya iOS cihazlarda uygulama yönetim ilkesi oluşturma, düzenleme veya silme ve iş dosyalarını koruma hakkında bilgi edinebilirsiniz.
ms.openlocfilehash: 3c6a3401fdef42dec19b6d66f4b9fa8cd78106e5
ms.sourcegitcommit: e246725b0935067aad886530d5178972c0f895d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2021
ms.locfileid: "63012860"
---
# <a name="set-app-protection-settings-for-android-or-ios-devices"></a>Android veya iOS cihazlara yönelik uygulama koruma ayarlarını belirleme

Bu makale diğer Microsoft 365 İş Ekstra.

## <a name="watch-secure-office-apps-on-ios"></a>İzle: iOS Office uygulama güvenliğini sağlama

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FLvZ?autoplay=false]

Mobil kullanıcıların oturum açmak için PIN veya parmak izi girmelerini gerektiren ve ayrıca cihazlarında depolanan iş dosyalarını şifreleyen bir kullanıcı erişim ilkesi kurabilirsiniz.

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetici merkezi</a>'nde oturum açın.
1. **İlkeler'in** altında İlke **ekle'yi seçin**.
1. İlke **ekle bölmesinde** , İlke **adı'nın altına bir ad** girin ve İlke türü altında istediğiniz ilke **türünü seçin**.
1. Kullanıcıların mobil **cihazlardaki Office erişimini yönet'i** seçin ve aşağıdaki üç ayarın açık olduğundan emin olun:
    - **Office uygulamalarına erişirken PIN veya parmak izi iste**
    - **Cihazlar kaybolur veya çalınırsa iş dosyalarını koruma**
    - **İş dosyalarını şifrele**

1. Bu **uygulamalara sahip dosyalar korunacaktır** altında, Office cihazlarda korumak istediğiniz dosyaları seçin.
1. Varsayılan **Who bu ayarları** alımayacak mı? varsayılan olarak tüm kullanıcılar seçilidir, ancak oluşturduğunuz tüm güvenlik gruplarını seçmek  için Değiştir'i seçebilirsiniz.
1. İlkeyi oluşturmayı bitirmek için Ekle'yi **seçin**.
1. İlke **ekle sayfasında** Kapat'ı **seçin**.
1. Yönetim merkezi giriş sayfasında, yeni ilkenizin ekli olduğunu onaylamak için İlkeler'i seçin ve İlkeler sayfasında **ilkenizi gözden** geçirin.

## <a name="create-an-app-management-policy"></a>Uygulama yönetimi ilkesi oluşturma

1. yönetim merkezine gidin <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>. 
    
2. Sol gezintide Cihaz İlkeleri **Ekle'yi** \>  \> seçin.
  
3. **İlke ekle** bölmesinde bu ilke için benzersiz bir ad girin. 
    
4. **İlke türü'nin** **altında, oluşturmak** istediğiniz ilke kümesine bağlı olarak Android için Uygulama Yönetimi'ne veya **iOS** için Uygulama Yönetimi'ne tıklayın. 
    
5. Cihazlar **kaybolursa veya çalınırsa iş dosyalarını koru ve** Kullanıcıların mobil **cihazlardan iş dosyalarına Office nasıl erişeceklerini yönet'i genişletin**. Ayarları istediğiniz gibi yapılandırabilirsiniz. **Kullanıcıların mobil cihazlardaki Office erişimini** yönetme varsayılan olarak Kapalıdır,  ancak bu ayarı Aç'a açmanız **ve varsayılan değerleri** kabul etmenizi öneririz. Daha fazla bilgi için bkz [. Kullanılabilir ayarlar](#available-settings). 
    
    Varsayılan ayarlara dönmek için istediğiniz zaman **Varsayılan ayarlara sıfırla** bağlantısını kullanabilirsiniz. 
    
    ![Android için uygulama yönetimi'nin seçili olduğu İlke oluşturma'nın ekran görüntüsü.](../../media/eabbe06d-ac0a-4f3a-8630-68c808b1e662.png)
  
6. Next decide **Who will get these settings?** Varsayılan Tüm Kullanıcılar güvenlik grubunu **kullanmak istemiyorsanız** Değiştir'i **seçin, bu** ayarları alan güvenlik gruplarını \> seçin Öğesini **seçin**.
    
7. Son olarak, **Bitti**'yi seçerek ilkeyi kaydedin ve cihazlarınıza atayın. 
    
## <a name="edit-an-app-management-policy"></a>Uygulama yönetimi ilkesini düzenleme

1. **İlkeler kartında** İlkeyi **düzenle'yi seçin**.
    
2. **İlkeyi düzenle** bölmesinde değiştirmek istediğiniz ilkeyi seçin. 
    
3. İlkedeki değerleri değiştirmek için her ayarın yanında bulunan **Düzenle**'yi seçin. Değiştiriyseniz, değer otomatik olarak ilkeye kaydedilir.
    
4. Bitirdikten sonra İlkeyi düzenle **bölmesini** kapatın. 
    
## <a name="delete-an-app-management-policy"></a>Uygulama yönetimi ilkesini silme

1. **İlkeler sayfasında** bir ilke seçin ve sonra da **Sil'i seçin**.
    
2. **İlkeyi sil bölmesinde**, seçtiğiniz **ilkeyi veya** ilkeleri silmek için Onayla'yı seçin. 
    
## <a name="available-settings"></a>Kullanılabilir ayarlar

Aşağıdaki tablolarda, cihazlardaki iş dosyalarını korumak için kullanılabilen ayarlar ve kullanıcıların mobil cihazlarından bu dosyalara Office ilgili ayarlar hakkında ayrıntılı bilgi sağlanmaktadır.
  
 Daha fazla bilgi için bkz[. Koruma özellikleri nasıl Microsoft 365 İş Ekstra Intune ayarlarıyla eşler](map-protection-features-to-intune-settings.md). 
  
### <a name="settings-that-protect-work-files"></a>İş dosyalarını koruyan ayarlar

Bir kullanıcının cihazı kaybolursa veya çalınırsa, iş dosyalarını korumak için aşağıdaki ayarlar kullanılabilir:


|Ayar  <br/> |Açıklama  <br/> |
|:-----|:-----|
|İş dosyalarını şu kadar gün sonra etkin olmayan cihazdan sil  <br/> |Bir cihaz burada belirttiğiniz gün sayısı boyunca kullanılmazsa, cihazda depolanan tüm iş dosyaları otomatik olarak silinir.  <br/> |
|Tüm kullanıcıları iş dosyalarını OneDrive İş üzerine kaydetmeye zorla  <br/> |Bu ayar Açık **durumda ise**, iş dosyaları için kullanılabilen tek kaydetme konumu OneDrive İş.  <br/> |
|İş dosyalarını şifrele  <br/> |İş dosyalarınızın şifreleme ile korunması için bu ayarı **Açık** tutun. Cihaz kaybolsa veya çalınsa bile hiç kimse şirket verilerinizi okumaz.  <br/> |
   
### <a name="settings-that-control-how-users-access-office-files-on-mobile-devices"></a>Kullanıcıların Office dosyalarına mobil cihazlardan erişimini denetleyen ayarlar

Kullanıcıların Office iş dosyalarına erişimini yönetmek için şu ayarlar kullanılabilir:


|Ayar  <br/> |Açıklama  <br/> |
|:-----|:-----|
|Office uygulamalarına erişirken PIN veya parmak izi iste  <br/> |Bu **ayar Kullanıcılarının** Mobil cihazlarında kendi kullanıcı adı ve parolalarının yanı sıra başka bir kimlik doğrulama biçimi daha sağlamaları gerekir. Bu ayar, Office uygulamalarını mobil cihazlarında kullanmaları gerekir.<br/> |
|Belirli sayıda başarısız oturum açma girişimi yapıldığında PIN'i sıfırla  <br/> |Yetkisiz bir kullanıcının PIN'i rastgele tahmin etmesini engellemek için belirlediğiniz sayıda yanlış giriş yapılırsa PIN sıfırlanır.  <br/> |
|Office uygulamaları belirli bir süre boyunca boşta kalırsa kullanıcıların yeniden oturum açmasını iste  <br/> |Bu ayar, bir kullanıcının ne kadar süre boşta kaldıktan sonra yeniden oturum açması istendiğinde belirler.  <br/> |
|Jailbreak uygulanmış veya kök erişim izni verilmiş cihazlardan iş dosyalarına erişilmesini engelle  <br/> |Akıllı kullanıcılar, bir cihaza jailbreak uygulamış veya kök erişim izni sağlamış olabilir. Bu, işletim sisteminin kullanıcı tarafından değiştirilebileceği ve dolayısıyla, cihazın kötü amaçlı yazılımlara karşı daha savunmasız hale gelebileceği anlamına gelir. Bu ayar **Açık** olduğunda böyle cihazlar engellenir.  <br/> |
|Kullanıcıların kişisel uygulamalara veya kişisel uygulamalara Office izin verme  <br/> |Bu duruma varsayılan olarak izin verilir, ancak bu ayar **Açık** olduğunda kullanıcı bir iş dosyasındaki bilgileri kişisel bir dosyaya aktarabilir. Ayar **Kapalı** durumdaysa, kullanıcı iş hesabındaki bilgileri kişisel bir uygulamaya veya kişisel hesaba kopyalayamaz.  <br/> |
