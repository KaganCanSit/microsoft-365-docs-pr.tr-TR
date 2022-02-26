---
title: Uygulama Koruma İlkelerini (MAM) kullanarak Uç nokta risk işaretleri için Microsoft Defender'ı yapılandırma
description: Uygulama Koruma ilkelerini kullanarak Uç nokta risk işaretleri için Microsoft Defender'ın nasıl yapılandırıldığından emin olun
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
localization_priority: Normal
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 2382dc157120b34bf100cf320807e2683f64bbb8
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62974099"
---
# <a name="configure-microsoft-defender-for-endpoint-risk-signals-using-app-protection-policies-mam"></a>Uygulama Koruma İlkelerini (MAM) kullanarak Uç nokta risk işaretleri için Microsoft Defender'ı yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



Mobil Cihaz Yönetimi (MDM) senaryolarında kurumsal kullanıcıları zaten koruyan Android'de Uç Nokta için Microsoft Defender, artık Intune mobil cihaz yönetimi (MDM) kullanılarak kaydolmamış cihazlar için Mobil Uygulama Yönetimi'ne (MAM) desteği genişletmiştir. Ayrıca bu desteği, mobil uygulama yönetimi (MAM) için Intune kullanmaya devam ederken diğer kurumsal hareket yönetimi çözümlerini kullanan müşterilere de genişletmektedir. Bu özellik, bir uygulama içinde kurum verilerinizi yönetmenize ve korumanıza olanak sağlar.

Android'de Uç Nokta için Microsoft Defender tehdit bilgileri, bu uygulamaları korumak için Intune Uygulama Koruma İlkeleri tarafından kullanılabilir. Uygulama koruma ilkeleri (UYGULAMA), kuruluşun verilerini güvende veya yönetilen bir uygulamada bulunduran kurallardır. Yönetilen uygulamaya uygulama koruma ilkeleri uygulanmıştır ve Intune tarafından yönetilebilir.  

Android'de Uç Nokta için Microsoft Defender MAM'nin her iki yapılandırmalarını da destekler
- **Intune MDM + MAM**: IT yöneticileri uygulamaları yalnızca Intune mobil cihaz yönetimi (MDM) ile kayıtlı cihazlarda Uygulama Koruma İlkelerini kullanarak yönetebilir.
- Cihaz **kaydı olmayan** MAM: Cihaz kaydı olmayan MAM veya MAM-WE, IT yöneticilerinin Intune MDM [](/mem/intune/app/app-protection-policy) ile kaydolmamış cihazlarda Uygulama Koruma İlkelerini kullanarak uygulamaları yönetmelerini sağlar. Başka bir ifadeyle, uygulamalar üçüncü taraf EMM sağlayıcılarıyla kaydolan cihazlarda Intune tarafından yönetilebilir. Yukarıdaki yapılandırmaların her ikisini de kullanarak uygulamaları yönetmek için müşterilerin yönetim merkezinde [Intune'Microsoft Endpoint Manager gerekir](https://go.microsoft.com/fwlink/?linkid=2109431)

Bu özelliği etkinleştirmek için yöneticinin Uç Nokta için Microsoft Defender ile Intune arasındaki bağlantıyı yapılandırması, uygulama koruma ilkesi oluşturması ve ilkeyi hedefli cihazlara ve uygulamalara uygulamasına uygulaması gerekir. 
 
Son kullanıcıların ayrıca cihazına Uç Nokta için Microsoft Defender'ı yükleme adımlarını atılması ve ekleme akışının etkinleştirmesi gerekir.


## <a name="admin-prerequisites"></a>Yönetici önkoşulları

- **Microsoft Defender for Endpoint-Intune bağlayıcının etkinleştirildiğinden doğrulama**

  a. Devam'a security.microsoft.com. 

  b. Bağlantı **Ayarlar > Gelişmiş> için Uç > Microsoft Intune'ı** seçin.

  c. Bağlantı açık değilse, açmak için iki durumlu düğmeyi seçin ve sonra da Kaydetme **Tercihleri'ne tıklayın**.

  ![Endpoint -Intune bağlayıcısı için Defender görüntüsü](images/enable-intune-connection.png)

  d. Giriş (**intune) Microsoft Endpoint Manager** gidin ve Bağlayıcı için Microsoft Defender'ın Endpoint-Intune etkinleştirildikten sonra doğrula' seçin.

  ![Intune'da Endpoint-Intune Defender'ın görüntüsü](images/validate-intune-connector.png)

- **Uygulama Koruma İlkesi (APP) için Android Connector'da Uç Nokta için Microsoft Defender'ı Etkinleştirme**
  
  Uygulama koruma ilkeleri için Intune Microsoft Endpoint Manager bağlayıcıyı yapılandırma:

  a. Uç Nokta **için Microsoft Defender > Bağlayıcılar ve Belirteçler'e >'e gidin**.

  b. Android için uygulama koruma ilkesi iki durumlu düğmesini açın (aşağıdaki ekran görüntüsünde olduğu gibi).

  c. **Kaydet**'i seçin.

  ![Uygulama ayarları](images/app-settings.png)

- **Uygulama koruma ilkesi oluşturma** 
 
Bir uygulama koruma ilkesi oluşturarak, Microsoft Defender için Uç nokta risk sinyalleri için Microsoft Defender'a dayalı olarak yönetilen bir uygulamaya erişimi engelin veya verileri silin.
Uç Nokta için Microsoft Defender, uygulama koruma ilkelerde (MAM olarak da bilinen APP) kullanılacak tehdit sinyalleri gönderecek şekilde yalıtabilirsiniz. Bu özellik sayesinde, yönetilen uygulamaları korumak üzere Uç Nokta için Microsoft Defender'ı kullanabilirsiniz.

1. İlke oluşturma <br>
Uygulama koruma ilkeleri (UYGULAMA), kuruluşun verilerini güvende veya yönetilen bir uygulamada bulunduran kurallardır. İlke, kullanıcı "kurumsal" verilere erişmeye veya verileri taşımaya ya da kullanıcı uygulamanın içinde olduğunda yasaklanan veya izlenen bir dizi eyleme erişmeye veya taşımaya çalışan kurallar olabilir. 

![İlke oluşturma resmi](images/create-policy.png)

2. Uygulama ekleme <br>
    a. Bu ilkeyi farklı cihazlardaki uygulamalara nasıl uygulamak istediğinize seçin. Ardından en az bir uygulama ekleyin. <br>
    Bu ilkenin, unmanaged cihazlar için geçerli olup olmadığını belirtmek için bu seçeneği kullanın. Android kullanıcıları, Cihaz Yöneticisi veya Yönetilen cihazlar için Enterprise ilkeyi belirtebilirsiniz. Ayrıca, herhangi bir yönetim durumunun cihazlarına ilkenizi hedeflemeyi de seçebilirsiniz.
Mobil uygulama yönetimi cihaz yönetimi gerektirmeyen bu nedenle, şirket verilerini hem yönetilen hem de yönetilemeyen cihazlarda koruyabilirsiniz. Yönetim kullanıcı kimliğine göre ortalandı ve cihaz yönetimi gereksinimi ortadan kaldırıldı. Şirketler aynı anda MDM ile veya MDM olmadan uygulama koruma ilkelerini kullanabilir. Örneğin, hem şirket tarafından verilen bir telefonu hem de kendi kişisel tabletini kullanan bir çalışan düşünün. Şirket telefonu MDM'ye kayıtlıdır ve kişisel cihaz yalnızca uygulama koruma ilkeleri tarafından korunarak uygulama koruma ilkeleri tarafından korunur.

    b. Uygulamalar'ı seçin<br>
    Yönetilen uygulama, uygulama koruma ilkeleri uygulanmış olan bir uygulamadır ve Intune tarafından yönetilebilir. [Intune SDK](/mem/intune/developer/app-sdk) ile tümleştirilmiş veya [Intune](/mem/intune/developer/apps-prepare-mobile-application-management) SDK ile kaydırılmış App Wrapping Tool, Intune uygulama koruma İlkeleri kullanılarak yönetilebilir. Bu araçlar kullanılarak [Microsoft Intune ve](/mem/intune/apps/apps-supported-intune-apps) genel kullanım için kullanılabilen korumalı uygulamaların resmi listesine bakın.

    *Örnek: Outlook uygulama olarak sırala*

    ![Yönetilen Outlook olarak resim görüntüsü](images/managed-app.png)

 3. Koruma ilkeniz için oturum açma güvenlik gereksinimlerini ayarlayın. <br>
Cihaz **Koşulları> izin verilen en yüksek cihaz tehdit düzeyi'ne** **ayar'ı seçin** ve bir değer girin. Ardından Eylem  **: "Erişimi Engelle" seçeneğini seçin**. Android'de Uç Nokta için Microsoft Defender bu Cihaz Tehdit Düzeyini paylaşıyor.

    ![Koşullu başlatma resmi](images/conditional-launch.png)


- **İlkenin uygulanması gereken kullanıcı gruplarını atatma.**<br>
  Dahil edilen **gruplar'ı seçin**. Sonra ilgili grupları ekleyin. 

    ![Asilerin resmi](images/assignment.png)


## <a name="end-user-prerequisites"></a>Son kullanıcı önkoşulları
- Aracı uygulamasının yüklü olması gerekiyor
    - Intune Şirket Portalı
    
- Kullanıcılar yönetilen uygulama için gerekli lisanslara sahip ve uygulama yüklü

### <a name="end-user-onboarding"></a>Son kullanıcı ekleme 

1. Yönetilen bir uygulamada, örneğin Outlook. Cihaz kaydedilir ve uygulama koruma ilkesi cihaza eşitlenir. Uygulama koruma ilkesi cihazın durumunu tanır.  

2. **Devam'ı seçin**. Android uygulamasında Uç Nokta için Microsoft Defender'ın indirilmez ve ayar önerilir.

3. **İndir'i seçin**. Uygulama mağazasına yönlendirildiniz (Google play). 

4.  Uç Nokta (Mobil) için Microsoft Defender uygulamasını yükleyin ve yönetilen uygulama ekleme ekranına geri yükleyin.

  ![MDE yükleme ve yönetilen uygulama ekleme ekranı geri başlatma](images/download-mde.png)

5.  **Başlat'a > tıklayın**. Uç nokta uygulaması ekleme/etkinleştirme akışı için Microsoft Defender başlatılır. Ekleme işlemini tamamlamak için adımları izleyin. Otomatik olarak Yeniden Yönetilen uygulama ekleme ekranına yeniden yönlendirilin; böylece cihaz iyidir.

6. Yönetilen **uygulamada** oturum açmak için Devam'ı seçin. 



## <a name="related-topics"></a>İlgili konular

- [Android'de Uç Nokta için Microsoft Defender'a Genel Bakış](microsoft-defender-endpoint-android.md)
- [Android'de Uç Nokta için Microsoft Defender'ı Microsoft Intune](android-intune.md)
