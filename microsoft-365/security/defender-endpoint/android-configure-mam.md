---
title: Uygulama Koruma İlkelerini (MAM) kullanarak Uç Nokta için Microsoft Defender risk sinyallerini yapılandırma
description: App Protection ilkelerini kullanarak Uç Nokta için Microsoft Defender risk sinyallerinin nasıl yapılandırıldığı açıklanır
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
ms.openlocfilehash: 48a128e32e949ecad6c34c4dfc96f6246780d0db
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2022
ms.locfileid: "65670190"
---
# <a name="configure-microsoft-defender-for-endpoint-risk-signals-using-app-protection-policies-mam"></a>Uygulama Koruma İlkelerini (MAM) kullanarak Uç Nokta için Microsoft Defender risk sinyallerini yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



Mobil Cihaz Yönetimi (MDM) senaryolarında kurumsal kullanıcıları zaten koruyan Android'da Uç Nokta için Microsoft Defender, artık Intune mobil cihaz yönetimi (MDM) kullanılarak kaydedilmemiş cihazlar için Desteği Mobil Uygulama Yönetimi'ne (MAM) genişletiyor. Ayrıca bu destek, mobil uygulama yönetimi (MAM) için Intune kullanırken diğer kurumsal mobil yönetim çözümlerini kullanan müşterilere de genişletir. Bu özellik, bir uygulama içindeki kuruluşunuzun verilerini yönetmenize ve korumanıza olanak tanır.

Android tehdit bilgilerine Uç Nokta için Microsoft Defender, bu uygulamaları korumak için Intune Uygulama Koruma İlkeleri tarafından uygulanır. Uygulama koruması ilkeleri (APP), kuruluşun verilerinin güvenli kalmasını veya yönetilen bir uygulamada yer almamasını sağlayan kurallardır. Yönetilen bir uygulamada uygulama koruma ilkeleri uygulanır ve Intune tarafından yönetilebilir.  

Android'da Uç Nokta için Microsoft Defender, MAM'ın her iki yapılandırmasını da destekler
- **MDM + MAM Intune**: BT yöneticileri yalnızca Intune mobil cihaz yönetimi (MDM) ile kaydedilen cihazlarda Uygulama Koruma İlkelerini kullanarak uygulamaları yönetebilir.
- **Cihaz kaydı olmadan MAM: Cihaz** kaydı olmayan MAM veya MAM-WE, BT yöneticilerinin Intune MDM'ye kayıtlı olmayan cihazlarda [Uygulama Koruma İlkeleri'ni](/mem/intune/apps/app-protection-policy) kullanarak uygulamaları yönetmesine olanak tanır. Bu sağlama, uygulamaların üçüncü taraf EMM sağlayıcılarıyla kaydedilen cihazlarda Intune tarafından yönetilebileceği anlamına gelir. Bu yapılandırmalardaki uygulamaları yönetmek için müşterilerin [Microsoft Endpoint Manager yönetim merkezinde Intune](https://go.microsoft.com/fwlink/?linkid=2109431) kullanması gerekir.

Bu özelliği etkinleştirmek için bir yöneticinin Uç Nokta için Microsoft Defender ile Intune arasındaki bağlantıyı yapılandırması, uygulama koruma ilkesini oluşturması ve ilkeyi hedeflenen cihazlara ve uygulamalara uygulaması gerekir. 
 
Son kullanıcıların Uç Nokta için Microsoft Defender cihazlarına yüklemek ve ekleme akışını etkinleştirmek için de adımlar atması gerekir.


## <a name="admin-prerequisites"></a>Yönetici önkoşulları

- **Endpoint-Intune için Microsoft Defender bağlayıcısının etkinleştirildiğini doğrulama**

  a. security.microsoft.com gidin. 

  b. **Bağlantının açık > Microsoft Intune Gelişmiş Özellikler> Ayarlar > Uç Noktaları'nı** seçin.

  c. Bağlantı açık değilse açmak için iki durumlu düğmeyi seçin ve ardından **Tercihleri Kaydet'i** seçin.

  :::image type="content" source="images/enable-intune-connection.png" alt-text="Microsoft 365 Defender portalındaki Gelişmiş özellikler bölümü" lightbox="images/enable-intune-connection.png":::

  d. **Microsoft Endpoint Manager (Intune)** bölümüne gidin ve Endpoint-Intune için Microsoft Defender bağlayıcının etkinleştirilip etkinleştirilmediğini doğrulayın.

  :::image type="content" source="images/validate-intune-connector.png" alt-text="Microsoft 365 Defender portalındaki intune bağlayıcısı durum bölmesi" lightbox="images/validate-intune-connector.png":::

- **Uygulama Koruma İlkesi (APP) için Android Bağlayıcısı'nda Uç Nokta için Microsoft Defender etkinleştirme**
  
  bağlayıcıyı Uygulama koruması ilkeleri için Intune Microsoft Endpoint Manager yapılandırın:

  a. **Kiracı Yönetimi > Bağlayıcılar ve Belirteçler > Uç Nokta için Microsoft Defender** gidin.

  b. Android için uygulama koruma ilkesinin iki durumlu düğmesini açın (aşağıdaki ekran görüntüsünde görüldüğü gibi).

  c. **Kaydet**'i seçin.

  :::image type="content" source="images/app-settings.png" alt-text="Microsoft 365 Defender portalındaki uygulama ayarları bölmesi" lightbox="images/app-settings.png":::

- **Uygulama koruma ilkesi oluşturma** 
 
Bir uygulama koruma ilkesi oluşturarak Uç Nokta için Microsoft Defender risk sinyallerine göre yönetilen bir uygulamanın erişimini engelleyin veya verileri silin.
Uç Nokta için Microsoft Defender, uygulama koruma ilkelerinde (MAM olarak da bilinir) kullanılacak tehdit sinyalleri gönderecek şekilde yapılandırılabilir. Bu özellik sayesinde yönetilen uygulamaları korumak için Uç Nokta için Microsoft Defender kullanabilirsiniz.

1. İlke oluşturma <br>
Uygulama koruması ilkeleri (APP), kuruluşun verilerinin güvenli kalmasını veya yönetilen bir uygulamada yer almamasını sağlayan kurallardır. İlke, kullanıcı "şirket" verilerine erişmeye veya verileri taşımaya çalıştığında uygulanan bir kural ya da kullanıcı uygulamanın içindeyken yasaklanan veya izlenen bir dizi eylem olabilir. 

:::image type="content" source="images/create-policy.png" alt-text="Microsoft 365 Defender portalındaki Uygulama koruması ilkeleri sayfasındaki İlke oluştur sekmesi" lightbox="images/create-policy.png":::

2. Uygulama ekleme <br>
    a. Bu ilkeyi farklı cihazlardaki uygulamalara nasıl uygulamak istediğinizi seçin. Ardından en az bir uygulama ekleyin. <br>
    Bu ilkenin yönetilmeyen cihazlar için geçerli olup olmadığını belirtmek için bu seçeneği kullanın. Android ilkenin Android Enterprise, Cihaz Yönetici veya Yönetilmeyen cihazlar için geçerli olduğunu belirtebilirsiniz. ayrıca, ilkenizi herhangi bir yönetim durumundaki cihazlardaki uygulamalara hedeflemeyi de seçebilirsiniz.
Mobil uygulama yönetimi cihaz yönetimi gerektirmediğinden, şirket verilerini hem yönetilen hem de yönetilmeyen cihazlarda koruyabilirsiniz. Yönetim, cihaz yönetimi gereksinimini ortadan kaldıran kullanıcı kimliğine göre ortalanır. Şirketler, uygulama koruma ilkelerini aynı anda MDM ile veya MDM olmadan kullanabilir. Örneğin, hem şirket tarafından verilen bir telefonu hem de kendi kişisel tabletini kullanan bir çalışanı düşünün. Şirket telefonu MDM'ye kaydedilir ve uygulama koruma ilkeleriyle korunurken, kişisel cihaz yalnızca uygulama koruma ilkeleriyle korunur.

    b. Uygulamalar'ı seçin<br>
    Yönetilen uygulama, uygulama koruma ilkelerinin uygulandığı ve Intune tarafından yönetilebilen bir uygulamadır. [Intune SDK](/mem/intune/developer/app-sdk) ile tümleştirilmiş veya Intune App Wrapping Tool tarafından sarmalanmış tüm uygulamalar Intune uygulama koruma İlkeleri kullanılarak [yönetilebilir.](/mem/intune/developer/apps-prepare-mobile-application-management) Bu araçlar kullanılarak oluşturulmuş ve genel kullanıma açık [Microsoft Intune korumalı uygulamaların](/mem/intune/apps/apps-supported-intune-apps) resmi listesine bakın.

    *Örnek: yönetilen uygulama olarak Outlook*

  :::image type="content" source="images/managed-app.png" alt-text="Microsoft 365 Defender portalındaki Genel uygulamalar bölmesi" lightbox="images/managed-app.png":::


 3. Koruma ilkeniz için oturum açma güvenlik gereksinimlerini ayarlayın. <br>
**Cihaz Koşulları'nda** **İzin verilen en yüksek cihaz tehdit düzeyi > Ayar'ı** seçin ve bir değer girin. Ardından  **Eylem: "Erişimi Engelle" seçeneğini** belirleyin. Android'da Uç Nokta için Microsoft Defender bu Cihaz Tehdit Düzeyini paylaşır.

  :::image type="content" source="images/conditional-launch.png" alt-text="Microsoft 365 Defender portalındaki Cihaz koşulları bölmesi" lightbox="images/conditional-launch.png":::
  
- **İlkenin uygulanması gereken kullanıcı gruplarını atayın.**<br>
  **Dahil edilen gruplar'ı** seçin. Ardından ilgili grupları ekleyin. 

    :::image type="content" source="images/assignment.png" alt-text="Microsoft 365 Defender portalındaki Dahil edilen gruplar bölmesi" lightbox="images/assignment.png":::


## <a name="end-user-prerequisites"></a>Son kullanıcı önkoşulları
- Aracı uygulamasının yüklü olması gerekir
    - Intune Şirket Portalı
    
- Kullanıcılar yönetilen uygulama için gerekli lisanslara sahip ve uygulamanın yüklü olduğu

### <a name="end-user-onboarding"></a>Son kullanıcı ekleme 

1. Yönetilen bir uygulamada oturum açın, örneğin Outlook. Cihaz kaydedilir ve uygulama koruma ilkesi cihazla eşitlenir. Uygulama koruma ilkesi cihazın sistem durumunu tanır.  

2. **Devam**'ı seçin. Uç Nokta için Microsoft Defender Android uygulamasına indirilmesini ve ayarlanmasını öneren bir ekran gösterilir.

3. **İndir'i** seçin. Uygulama mağazasına (Google play) yönlendirilirsiniz. 

4.  Uç Nokta için Microsoft Defender (Mobil) uygulamasını yükleyin ve Yönetilen uygulama ekleme ekranını yeniden başlatın.

  :::image type="content" source="images/download-mde.png" alt-text="MDE'yi indirme ve uygulama ekleme ekranını yeniden başlatma yordamını içeren gösterim sayfaları" lightbox="images/download-mde.png":::
  

5.  **Başlat > Devam'a** tıklayın. Uç Nokta için Microsoft Defender uygulaması ekleme/etkinleştirme akışı başlatılır. Ekleme işlemini tamamlamak için adımları izleyin. Otomatik olarak Yönetilen uygulama ekleme ekranına geri yönlendirilirsiniz ve bu da cihazın iyi durumda olduğunu gösterir.

6. Yönetilen uygulamada oturum açmak için **Devam'ı** seçin. 



## <a name="related-topics"></a>İlgili konular

- [Android'de Uç Nokta için Microsoft Defender’a genel bakış](microsoft-defender-endpoint-android.md)
- [Android’de Uç Nokta için Defender’ı Microsoft Intune ile dağıtın](android-intune.md)
