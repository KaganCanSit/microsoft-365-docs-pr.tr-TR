---
title: iOS Uç Nokta için Microsoft Defender dağıtımı
description: Kaydı olmayan iOS Uç Nokta için Microsoft Defender dağıtımı açıklandı.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, ios, yapılandırma, özellikler, ios
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
ms.openlocfilehash: b1945059147f87499d131d241c74aaca749fb6e7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474123"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-unenrolled-ios-devices"></a>Kaydı Uç Nokta için Microsoft Defender iOS cihazlarını dağıtma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> iOS'ta Uç Nokta için Defender Web Koruma özelliğini sağlamak için VPN kullanır. Bu normal bir VPN değildir ve trafiği cihazın dışına almayan yerel/kendi kendine döngülü bir VPN'tir.

## <a name="configure-microsoft-defender-for-endpoint-risk-signals-in-app-protection-policy-mam"></a>Uygulama Uç Nokta için Microsoft Defender (MAM) içinde risk işaretlerini yapılandırma

Uç Nokta için Microsoft Defender Cihaz Yönetimi (MDM) senaryolarında kurumsal kullanıcıları zaten koruyan iOS'ta Uç Nokta için Microsoft Defender, mobil cihaz yönetimi (MDM) kullanılarak kaydolmamış cihazlar için artık Mobil Uygulama Yönetimi'ne (Intune MAM) destek sunar. Ayrıca bu desteği, mobil uygulama yönetimi (MAM) için Intune kullanırken diğer kurumsal hareket yönetimi çözümlerini kullanan müşterilere de genişletmektedir. Bu özellik, bir uygulama içinde kurum verilerinizi yönetmenize ve korumanıza olanak sağlar.

Uç Nokta için Microsoft Defender iOS tehdit bilgilerine ilişkin diğer bilgiler, bu Intune için Uygulama Koruma İlkeleri tarafından da kullanılabilir. Uygulama koruması (UYGULAMA) ilkeleri, kuruluşun verilerini güvende veya yönetilen bir uygulamada bulunduran kurallardır. Yönetilen uygulamaya uygulanmış uygulama koruma ilkeleri vardır ve bu ilkeler Intune.  

Uç Nokta için Microsoft Defender iOS'ta ana sistem, MAM
- **Intune MDM + MAM**: IT yöneticileri uygulamaları yalnızca mobil cihaz yönetimi (MDM) ile Intune Cihazlarda Uygulama Koruma İlkelerini kullanarak yönetebilir.
- Cihaz **kaydı olmayan MAM**: Cihaz kaydı olmayan MAM veya MAM-WE, IT yöneticilerinin MDM ile kaydolmamış [](/mem/intune/app/app-protection-policy) cihazlarda Uygulama Koruma İlkelerini kullanarak uygulamaları yönetmelerini Intune sağlar. Başka bir ifadeyle, uygulamalar Intune üçüncü taraf EMM sağlayıcılarıyla kaydolan cihazlar tarafından yönetilebilir. Yukarıdaki yapılandırmaların her ikisini de kullanarak uygulamaları yönetmek için müşterilerin Intune yönetim [merkezinde Microsoft Endpoint Manager kullanmaları gerekir](https://go.microsoft.com/fwlink/?linkid=2109431).

Bu özelliği etkinleştirmek için, yöneticinin Uç Nokta için Microsoft Defender ile Intune arasındaki bağlantıyı yapılandırması, uygulama koruma ilkesi oluşturması ve ilkeyi hedefli cihazlara ve uygulamalara uygulamasına uygulaması gerekir. 
 
Son kullanıcıların da cihazlarında yükleme adımlarını Uç Nokta için Microsoft Defender ve işe alma akışını etkinleştirmeleri gerekir.

### <a name="pre-requisites"></a>Önkoşullar

1. **Bağlayıcının etkinleştirildiğinden emin olun**. <br> Birleşik güvenlik [konsolunda Ayarlar](https://security.microsoft.com) >  **EndpointsAdvanced** >  Özellikleri'ne gidin ve bağlantının **Microsoft Intune emin** olun.

  :::image type="content" source="images/enable-intune-connection.png" alt-text="Uç Nokta için Defender - Intune bağlayıcısı" lightbox="images/enable-intune-connection.png":::

  
2. **Bağlayıcının portalda etkinleştirildiğinden emin Intune.** <br> [Microsoft Endpoint manager admin centernde Endpoint](https://go.microsoft.com/fwlink/?linkid=2109431) Security (Uç Nokta **Uç Nokta için Microsoft Defender** > ) bağlantısına gidin ve Bağlantı durumunun etkin olduğundan emin olun.

  :::image type="content" source="images/app-settings.png" alt-text="Uygulama ayarları" lightbox="images/app-settings.png":::

### <a name="create-an-app-protection-policy"></a>Uygulama koruma ilkesi oluşturma
 
Uygulama koruma ilkesi oluşturarak yönetilen uygulamanın erişimini engel Uç Nokta için Microsoft Defender ve risk işaretlerini temel alarak verileri silin.
Uç Nokta için Microsoft Defender koruma ilkelerde (MAM olarak da bilinen UYGULAMA) kullanılacak tehdit sinyalleri gönderecek şekilde yapılandırabilirsiniz. Bu özellik sayesinde, yönetilen uygulamaları korumak Uç Nokta için Microsoft Defender uygulamaları kullanabilirsiniz.

1. İlke oluşturma <br>
Uygulama koruması (UYGULAMA) ilkeleri, kuruluşun verilerini güvende veya yönetilen bir uygulamada bulunduran kurallardır. İlke, kullanıcı "kurumsal" verilere erişmeye veya verileri taşımaya ya da kullanıcı uygulamanın içinde olduğunda yasaklanan veya izlenen bir dizi eyleme erişmeye veya taşımaya çalışan kurallar olabilir. 

:::image type="content" source="images/create-policy.png" alt-text="İlkeler menü öğesi Uygulama koruması Oluştur sekmesi" lightbox="images/create-policy.png":::

2. Uygulama ekleme <br>
    a. Bu ilkeyi farklı cihazlardaki uygulamalara nasıl uygulamak istediğinize seçin. Ardından en az bir uygulama ekleyin. <br>
    Bu ilkenin, unmanaged cihazlar için geçerli olup olmadığını belirtmek için bu seçeneği kullanın. Ayrıca, herhangi bir yönetim durumunun cihazlarına ilkenizi hedeflemeyi de seçebilirsiniz.
Mobil uygulama yönetimi cihaz yönetimi gerektirmeyen bu nedenle, şirket verilerini hem yönetilen hem de yönetilemeyen cihazlarda koruyabilirsiniz. Yönetim kullanıcı kimliğine göre ortalandı ve cihaz yönetimi gereksinimi ortadan kaldırıldı. Şirketler aynı anda MDM ile veya MDM olmadan uygulama koruma ilkelerini kullanabilir. Örneğin, hem şirket tarafından verilen bir telefonu hem de kendi kişisel tabletini kullanan bir çalışan düşünün. Şirket telefonu MDM'ye kayıtlıdır ve kişisel cihaz yalnızca uygulama koruma ilkeleri tarafından korunarak uygulama koruma ilkeleri tarafından korunur.

    b. Uygulamalar'ı seçin<br>
    Yönetilen uygulama, uygulama koruma ilkeleri uygulanmış olan bir uygulamadır ve uygulama koruma ilkeleri tarafından Intune. [Intune SDK](/mem/intune/developer/app-sdk) ile tümleştirilmiş veya Intune App Wrapping Tool kaydırılmış tüm [uygulamalar, Intune](/mem/intune/developer/apps-prepare-mobile-application-management) koruma İlkeleri kullanılarak yönetilebilir. Bu araçlar kullanılarak [Microsoft Intune ve](/mem/intune/apps/apps-supported-intune-apps) genel kullanım için kullanılabilen korumalı uygulamaların resmi listesine bakın.

    *Örnek: Outlook uygulama olarak sırala*

     :::image type="content" source="images/managed-app.png" alt-text="Sol Outlook Microsoft Web Bölümü menü öğesi" lightbox="images/managed-app.png":::
  

 3. Koruma ilkeniz için oturum açma güvenlik gereksinimlerini ayarlayın. <br>
Cihaz **Koşulları> izin verilen en yüksek cihaz tehdit düzeyi'ne** **ayar'ı seçin** ve bir değer girin. Ardından Eylem  **: "Erişimi Engelle" seçeneğini seçin**. Uç Nokta için Microsoft Defender, bu Cihaz Tehdit Düzeyi'nin paylaşımını sağlar.

    
   :::image type="content" source="images/conditional-launch.png" alt-text="Cihaz koşulları bölmesi" lightbox="images/conditional-launch.png":::

4. İlkenin uygulanması gereken kullanıcı gruplarını atatma.<br>
  Dahil edilen **gruplar'ı seçin**. Sonra ilgili grupları ekleyin. 


MAM veya uygulama koruma ilkesi hakkında daha fazla bilgi için bkz. [iOS uygulama koruma ilkesi ayarları](/mem/intune/apps/app-protection-policy-settings-ios).

## <a name="deploy-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>KAYDı Uç Nokta için Microsoft Defender MAM veya kaydı olmayan cihazlarda uygulama dağıtma

Uç Nokta için Microsoft Defender iOS'ta güvenlik ilkesi senaryosu etkinleştirir ve Apple App Store'da kullanılabilir.

Uygulama koruma ilkeleri, Uç Nokta için Microsoft Defender'tan cihaz risk sinyallerini içerecek şekilde yapılandırıldığında, bu tür uygulamaları kullanırken Uç Nokta için Microsoft Defender uygulamaları yüklemeleri için yönlendiriliyor. Alternatif olarak, kullanıcılar uygulamanın en son sürümünü doğrudan Apple App Store'dan da yükleyebilirler.
