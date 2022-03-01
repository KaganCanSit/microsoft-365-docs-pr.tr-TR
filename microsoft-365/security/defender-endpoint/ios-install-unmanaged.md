---
title: iOS'ta Uç Nokta için Microsoft Defender'ı Dağıtma
description: Kaydı olmayan iOS cihazlarda Uç Nokta için Microsoft Defender'ın nasıl dağıtıılı?
keywords: microsoft, defender, Endpoint için Microsoft Defender, ios, configure, features, ios
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: sunasing
author: sunasing
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 082e03100c366294a193d5fc7eb3cf0dd868caa6
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63014401"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-unenrolled-ios-devices"></a>Kaydı olmayan iOS cihazlarda Uç Nokta için Microsoft Defender'ı dağıtma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> iOS'ta Uç Nokta için Defender Web Koruma özelliğini sağlamak için VPN kullanır. Bu normal bir VPN değildir ve trafiği cihazın dışına almayan yerel/kendi kendine döngülü bir VPN'tir.

## <a name="configure-microsoft-defender-for-endpoint-risk-signals-in-app-protection-policy-mam"></a>Uygulama koruma ilkesinde (MAM) Uç nokta risk işaretleri için Microsoft Defender'ı yapılandırma

Mobil Cihaz Yönetimi (MDM) senaryolarında kurumsal kullanıcıları zaten koruyan iOS'ta Uç Nokta için Microsoft Defender, Intune mobil cihaz yönetimi (MDM) kullanılarak kaydolmamış cihazlar için artık Mobil Uygulama Yönetimi'ne (MAM) destek sunar. Ayrıca bu desteği, mobil uygulama yönetimi (MAM) için Intune kullanmaya devam ederken diğer kurumsal hareket yönetimi çözümlerini kullanan müşterilere de genişletmektedir. Bu özellik, bir uygulama içinde kurum verilerinizi yönetmenize ve korumanıza olanak sağlar.

iOS'ta Uç Nokta için Microsoft Defender tehdit bilgileri, bu uygulamaları korumak için Intune Uygulama Koruma İlkeleri tarafından kullanılabilir. Uygulama koruma ilkeleri (UYGULAMA), kuruluşun verilerini güvende veya yönetilen bir uygulamada bulunduran kurallardır. Yönetilen uygulamaya uygulama koruma ilkeleri uygulanmıştır ve Intune tarafından yönetilebilir.  

iOS'ta Uç Nokta için Microsoft Defender, MAM'nin her iki yapılandırmalarını da destekler
- **Intune MDM + MAM**: IT yöneticileri uygulamaları yalnızca Intune mobil cihaz yönetimi (MDM) ile kayıtlı cihazlarda Uygulama Koruma İlkelerini kullanarak yönetebilir.
- Cihaz **kaydı olmayan** MAM: Cihaz kaydı olmayan MAM veya MAM-WE, IT yöneticilerinin Intune MDM [](/mem/intune/app/app-protection-policy) ile kaydolmamış cihazlarda Uygulama Koruma İlkelerini kullanarak uygulamaları yönetmelerini sağlar. Başka bir ifadeyle, uygulamalar üçüncü taraf EMM sağlayıcılarıyla kaydolan cihazlarda Intune tarafından yönetilebilir. Yukarıdaki yapılandırmaların her ikisini de kullanarak uygulamaları yönetmek için müşterilerin yönetim merkezinde Intune [Microsoft Endpoint Manager gerekir](https://go.microsoft.com/fwlink/?linkid=2109431)

Bu özelliği etkinleştirmek için yöneticinin Uç Nokta için Microsoft Defender ile Intune arasındaki bağlantıyı yapılandırması, uygulama koruma ilkesi oluşturması ve ilkeyi hedefli cihazlara ve uygulamalara uygulamasına uygulaması gerekir. 
 
Son kullanıcıların ayrıca cihazına Uç Nokta için Microsoft Defender'ı yükleme adımlarını atılması ve ekleme akışının etkinleştirmesi gerekir.

### <a name="pre-requisites"></a>Önkoşullar

1. **Bağlayıcının etkinleştirildiğinden emin olun**. <br> Birleşik güvenlik [konsolunda Ayarlar](https://security.microsoft.com) >  **EndpointsAdvanced** >  Özellikleri'ne gidin ve bağlantının **Microsoft Intune emin** olun.

  ![Endpoint -Intune bağlayıcısı için Defender görüntüsü](images/enable-intune-connection.png)
  
2. **Intune portalında bağlayıcının etkinleştirildiğinden emin olun**. <br> [Microsoft Endpoint manager yönetim merkezinde Endpoint](https://go.microsoft.com/fwlink/?linkid=2109431) **SecurityMicrosoft**  >  Defender for Endpoint (Uç Nokta) bağlantısına gidin ve Bağlantı durumunun etkin olduğundan emin olun.

  ![Uygulama ayarları](images/app-settings.png)

### <a name="create-an-app-protection-policy"></a>Uygulama koruma ilkesi oluşturma
 
Bir uygulama koruma ilkesi oluşturarak, Microsoft Defender için Uç nokta risk sinyalleri için Microsoft Defender'a dayalı olarak yönetilen bir uygulamaya erişimi engelin veya verileri silin.
Uç Nokta için Microsoft Defender, uygulama koruma ilkelerde (MAM olarak da bilinen APP) kullanılacak tehdit sinyalleri gönderecek şekilde yalıtabilirsiniz. Bu özellik sayesinde, yönetilen uygulamaları korumak üzere Uç Nokta için Microsoft Defender'ı kullanabilirsiniz.

1. İlke oluşturma <br>
Uygulama koruma ilkeleri (UYGULAMA), kuruluşun verilerini güvende veya yönetilen bir uygulamada bulunduran kurallardır. İlke, kullanıcı "kurumsal" verilere erişmeye veya verileri taşımaya ya da kullanıcı uygulamanın içinde olduğunda yasaklanan veya izlenen bir dizi eyleme erişmeye veya taşımaya çalışan kurallar olabilir. 

![İlke oluşturma resmi](images/create-policy.png)

2. Uygulama ekleme <br>
    a. Bu ilkeyi farklı cihazlardaki uygulamalara nasıl uygulamak istediğinize seçin. Ardından en az bir uygulama ekleyin. <br>
    Bu ilkenin, unmanaged cihazlar için geçerli olup olmadığını belirtmek için bu seçeneği kullanın. Ayrıca, herhangi bir yönetim durumunun cihazlarına ilkenizi hedeflemeyi de seçebilirsiniz.
Mobil uygulama yönetimi cihaz yönetimi gerektirmeyen bu nedenle, şirket verilerini hem yönetilen hem de yönetilemeyen cihazlarda koruyabilirsiniz. Yönetim kullanıcı kimliğine göre ortalandı ve cihaz yönetimi gereksinimi ortadan kaldırıldı. Şirketler aynı anda MDM ile veya MDM olmadan uygulama koruma ilkelerini kullanabilir. Örneğin, hem şirket tarafından verilen bir telefonu hem de kendi kişisel tabletini kullanan bir çalışan düşünün. Şirket telefonu MDM'ye kayıtlıdır ve kişisel cihaz yalnızca uygulama koruma ilkeleri tarafından korunarak uygulama koruma ilkeleri tarafından korunur.

    b. Uygulamalar'ı seçin<br>
    Yönetilen uygulama, uygulama koruma ilkeleri uygulanmış olan bir uygulamadır ve Intune tarafından yönetilebilir. [Intune SDK ile tümleştirilmiş veya Intune SDK](/mem/intune/developer/app-sdk) ile kaydırılmış App Wrapping Tool[, Intune](/mem/intune/developer/apps-prepare-mobile-application-management) uygulama koruma İlkeleri kullanılarak yönetilebilir. Bu araçlar kullanılarak [Microsoft Intune ve](/mem/intune/apps/apps-supported-intune-apps) genel kullanım için kullanılabilen korumalı uygulamaların resmi listesine bakın.

    *Örnek: Outlook uygulama olarak sırala*

    ![Yönetilen Outlook olarak resim görüntüsü](images/managed-app.png)

 3. Koruma ilkeniz için oturum açma güvenlik gereksinimlerini ayarlayın. <br>
Cihaz **Koşulları> izin verilen en yüksek cihaz tehdit düzeyi'ne** **ayar'ı seçin** ve bir değer girin. Ardından Eylem  **: "Erişimi Engelle" seçeneğini seçin**. iOS'ta Uç Nokta için Microsoft Defender bu Cihaz Tehdit Düzeyini paylaşıyor.

    ![Koşullu başlatma resmi](images/conditional-launch.png)

4. İlkenin uygulanması gereken kullanıcı gruplarını atatma.<br>
  Dahil edilen **gruplar'ı seçin**. Sonra ilgili grupları ekleyin. 


MAM veya uygulama koruma ilkesi hakkında daha fazla bilgi için bkz. [iOS uygulama koruma ilkesi ayarları](/mem/intune/apps/app-protection-policy-settings-ios).

## <a name="deploy-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>MAM için Uç Nokta veya kaydı olmayan cihazlarda Microsoft Defender'ı dağıtma

iOS'ta Uç Nokta için Microsoft Defender uygulama koruma ilkesi senaryosunu etkinleştirir ve Apple uygulama mağazasında kullanılabilir.

Uygulama koruma ilkeleri, uygulamalar için Uç Nokta için Microsoft Defender'dan cihaz riski sinyallerini içerecek şekilde yapılandırıldığında, kullanıcılar söz konusu uygulamaları kullanırken Uç Nokta için Microsoft Defender'ı yüklemeleri için yeniden yönlendiriliyor. Alternatif olarak, kullanıcılar uygulamanın en son sürümünü doğrudan Apple App Store'dan da yükleyebilirler.
