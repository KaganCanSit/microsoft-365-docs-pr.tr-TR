---
title: Uygulama koruma Uç Nokta için Microsoft Defender (MAM) kullanarak risk sinyallerini yapılandırma
description: Uygulama Koruma ilkelerini kullanarak Uç Nokta için Microsoft Defender sinyallerinin nasıl yapılandırıldığından emin olun
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mde, android, yapılandırma, MAM, Uygulama Koruma İlkeleri, Yönetilen uygulama
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: shthota
author: shthota
manager: dansimp
ms.localizationpriority: medium
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5d74fd2af61ee4047dd2728c28e6093efbc58ce9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471307"
---
# <a name="configure-microsoft-defender-for-endpoint-risk-signals-using-app-protection-policies-mam"></a>Uygulama koruma Uç Nokta için Microsoft Defender (MAM) kullanarak risk sinyallerini yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



Uç Nokta için Microsoft Defender Cihaz Yönetimi (MDM) senaryolarında kurumsal kullanıcıları zaten koruyan Android'de Intune mobil cihaz yönetimi (MDM) kullanılarak kaydolmamış cihazlar için artık Mobil Uygulama Yönetimi 'ne (MAM) desteği genişletmiştir. Ayrıca bu desteği, mobil uygulama yönetimi (MAM) için Intune kullanırken diğer kurumsal hareket yönetimi çözümlerini kullanan müşterilere de genişletmektedir. Bu özellik, bir uygulama içinde kurum verilerinizi yönetmenize ve korumanıza olanak sağlar.

Uç Nokta için Microsoft Defender tehdit bilgileri, bu uygulamaları korumak Intune Uygulama Koruma İlkeleri tarafından uygulanır. Uygulama koruması (UYGULAMA) ilkeleri, kuruluşun verilerini güvende veya yönetilen bir uygulamada bulunduran kurallardır. Yönetilen uygulamaya uygulanmış uygulama koruma ilkeleri vardır ve bu ilkeler Intune.  

Android Uç Nokta için Microsoft Defender uygulamaları MAM'nin her iki yapılandırmalarını da destekler
- **Intune MDM + MAM**: IT yöneticileri uygulamaları yalnızca mobil cihaz yönetimi (MDM) ile Intune Cihazlarda Uygulama Koruma İlkelerini kullanarak yönetebilir.
- Cihaz **kaydı olmayan MAM**: Cihaz kaydı olmayan MAM veya MAM-WE, IT yöneticilerinin MDM ile kaydolmamış [](/mem/intune/app/app-protection-policy) cihazlarda Uygulama Koruma İlkelerini kullanarak uygulamaları yönetmelerini Intune sağlar. Bu sağlama, uygulamaların üçüncü taraf EMM sağlayıcılarıyla Intune cihazlar tarafından yönetil diğer cihazlar tarafından yönetilil diğer anlamına gelir. Yukarıdaki yapılandırmaların her ikisini de kullanarak uygulamaları yönetmek için müşterilerin Intune yönetim [merkezinde Microsoft Endpoint Manager kullanmaları gerekir](https://go.microsoft.com/fwlink/?linkid=2109431).

Bu özelliği etkinleştirmek için, yöneticinin Uç Nokta için Microsoft Defender ile Intune arasındaki bağlantıyı yapılandırması, uygulama koruma ilkesi oluşturması ve ilkeyi hedefli cihazlara ve uygulamalara uygulamasına uygulaması gerekir. 
 
Son kullanıcıların da cihazlarında yükleme adımlarını Uç Nokta için Microsoft Defender ve işe alma akışını etkinleştirmeleri gerekir.


## <a name="admin-prerequisites"></a>Yönetici önkoşulları

- **Microsoft Defender for Endpoint-Intune bağlayıcının etkinleştirildiğinden doğrulama**

  a. Devam'a security.microsoft.com. 

  b. Bağlantı **Ayarlar > Gelişmiş> Için Uç > Microsoft Intune'i** seçin.

  c. Bağlantı açık değilse, açmak için iki durumlu düğmeyi seçin ve sonra da Kaydetme **Tercihleri'ne tıklayın**.

  :::image type="content" source="images/enable-intune-connection.png" alt-text="Portalda Gelişmiş Microsoft 365 Defender bölümü" lightbox="images/enable-intune-connection.png":::

  d. Giriş (**Microsoft Endpoint Manager) ve Intune** için Microsoft Defender'ın etkin Endpoint-Intune doğrula'ya gidin.

  :::image type="content" source="images/validate-intune-connector.png" alt-text="Microsoft 365 Defender portalında intune-connector durum bölmesi" lightbox="images/validate-intune-connector.png":::

- **Uygulama Uç Nokta için Microsoft Defender için Android Connector'da Uygulamayı Etkinleştirme İlkesi (APP)**
  
  Yeni ilkeler için Intune Microsoft Endpoint Manager bağlayıcıyı Uygulama koruması yapılandırma:

  a. Kiracı Yönetimi **Bağlayıcılar ve >'ne gidin ve > Uç Nokta için Microsoft Defender**.

  b. Android için uygulama koruma ilkesi iki durumlu düğmesini açın (aşağıdaki ekran görüntüsünde olduğu gibi).

  c. **Kaydet**'i seçin.

  :::image type="content" source="images/app-settings.png" alt-text="Microsoft 365 Defender portalında uygulama Microsoft 365 Defender bölmesi" lightbox="images/app-settings.png":::

- **Uygulama koruma ilkesi oluşturma** 
 
Uygulama koruma ilkesi oluşturarak yönetilen uygulamanın erişimini engel Uç Nokta için Microsoft Defender ve risk işaretlerini temel alarak verileri silin.
Uç Nokta için Microsoft Defender koruma ilkelerde (MAM olarak da bilinen UYGULAMA) kullanılacak tehdit sinyalleri gönderecek şekilde yapılandırabilirsiniz. Bu özellik sayesinde, yönetilen uygulamaları korumak Uç Nokta için Microsoft Defender uygulamaları kullanabilirsiniz.

1. İlke oluşturma <br>
Uygulama koruması (UYGULAMA) ilkeleri, kuruluşun verilerini güvende veya yönetilen bir uygulamada bulunduran kurallardır. İlke, kullanıcı "kurumsal" verilere erişmeye veya verileri taşımaya ya da kullanıcı uygulamanın içinde olduğunda yasaklanan veya izlenen bir dizi eyleme erişmeye veya taşımaya çalışan kurallar olabilir. 

:::image type="content" source="images/create-policy.png" alt-text="İlke portalının Uygulama koruması ilkeler sayfasında İlke Microsoft 365 Defender sekmesi" lightbox="images/create-policy.png":::

2. Uygulama ekleme <br>
    a. Bu ilkeyi farklı cihazlardaki uygulamalara nasıl uygulamak istediğinize seçin. Ardından en az bir uygulama ekleyin. <br>
    Bu ilkenin, unmanaged cihazlar için geçerli olup olmadığını belirtmek için bu seçeneği kullanın. Android'de, ilkenin Android cihazlarında, Enterprise Yöneticisi veya Yönetsiz cihazlar için geçerli olduğunu belirtebilirsiniz. Ayrıca, herhangi bir yönetim durumunun cihazlarına ilkenizi hedeflemeyi de seçebilirsiniz.
Mobil uygulama yönetimi cihaz yönetimi gerektirmeyen bu nedenle, şirket verilerini hem yönetilen hem de yönetilemeyen cihazlarda koruyabilirsiniz. Yönetim kullanıcı kimliğine göre ortalandı ve cihaz yönetimi gereksinimi ortadan kaldırıldı. Şirketler aynı anda MDM ile veya MDM olmadan uygulama koruma ilkelerini kullanabilir. Örneğin, hem şirket tarafından verilen bir telefonu hem de kendi kişisel tabletini kullanan bir çalışan düşünün. Şirket telefonu MDM'ye kayıtlıdır ve kişisel cihaz yalnızca uygulama koruma ilkeleri tarafından korunarak uygulama koruma ilkeleri tarafından korunur.

    b. Uygulamalar'ı seçin<br>
    Yönetilen uygulama, uygulama koruma ilkeleri uygulanmış olan bir uygulamadır ve uygulama koruma ilkeleri tarafından Intune. [Intune SDK](/mem/intune/developer/app-sdk) ile tümleştirilmiş veya Intune App Wrapping Tool kaydırılmış tüm [uygulamalar, Intune](/mem/intune/developer/apps-prepare-mobile-application-management) koruma İlkeleri kullanılarak yönetilebilir. Bu araçlar kullanılarak [Microsoft Intune ve](/mem/intune/apps/apps-supported-intune-apps) genel kullanım için kullanılabilen korumalı uygulamaların resmi listesine bakın.

    *Örnek: Outlook uygulama olarak sırala*

  :::image type="content" source="images/managed-app.png" alt-text="Microsoft 365 Defender portalında Genel uygulamalar bölmesi" lightbox="images/managed-app.png":::


 3. Koruma ilkeniz için oturum açma güvenlik gereksinimlerini ayarlayın. <br>
Cihaz **Koşulları> izin verilen en yüksek cihaz tehdit düzeyi'ne** **ayar'ı seçin** ve bir değer girin. Ardından Eylem  **: "Erişimi Engelle" seçeneğini seçin**. Uç Nokta için Microsoft Defender Android'de diğer cihazlar bu Cihaz Tehdit Düzeyini paylaşıyor.

  :::image type="content" source="images/conditional-launch.png" alt-text="Microsoft 365 Defender portalında Cihaz Microsoft 365 Defender bölmesi" lightbox="images/conditional-launch.png":::
  
- **İlkenin uygulanması gereken kullanıcı gruplarını atatma.**<br>
  Dahil edilen **gruplar'ı seçin**. Sonra ilgili grupları ekleyin. 

    :::image type="content" source="images/assignment.png" alt-text="Yeni portalda Dahil edilen Microsoft 365 Defender bölmesi" lightbox="images/assignment.png":::


## <a name="end-user-prerequisites"></a>Son kullanıcı önkoşulları
- Aracı uygulaması yük olmalı
    - Intune Şirket Portalı
    
- Kullanıcılar yönetilen uygulama için gerekli lisanslara sahip ve uygulamanın yüklü olduğu

### <a name="end-user-onboarding"></a>Son kullanıcı ekleme 

1. Yönetilen bir uygulamada, örneğin Outlook. Cihaz kaydedilir ve uygulama koruma ilkesi cihaza eşitlenir. Uygulama koruma ilkesi cihazın durumunu tanır.  

2. **Devam'ı seçin**. Android uygulamasında mobil cihaz yüklemesini ve ayarlamayı öneren Uç Nokta için Microsoft Defender bir ekran gösterilir.

3. **İndir'i seçin**. Uygulama mağazasına yönlendirildiniz (Google play). 

4.  Uç Nokta için Microsoft Defender (Mobil) uygulamasını yükleyin ve yönetilen uygulama ekleme ekranı'nın yeniden başlatılmasını sağlar.

  :::image type="content" source="images/download-mde.png" alt-text="MDE'i indirme ve uygulama ekleme ekranına geri dönme yordamını içeren tanıtım sayfaları" lightbox="images/download-mde.png":::
  

5.  **Başlat'a > tıklayın**. Hızlı Uç Nokta için Microsoft Defender ekleme/etkinleştirme akışı başlatılır. Ekleme işlemini tamamlamak için adımları izleyin. Otomatik olarak Yeniden Yönetilen uygulama ekleme ekranına yeniden yönlendirilin; böylece cihaz iyidir.

6. Yönetilen **uygulamada** oturum açmak için Devam'ı seçin. 



## <a name="related-topics"></a>İlgili konular

- [Android'de Uç Nokta için Microsoft Defender genel bakış](microsoft-defender-endpoint-android.md)
- [Android'Uç Nokta için Microsoft Defender uygulama dağıtımı ve Microsoft Intune](android-intune.md)
