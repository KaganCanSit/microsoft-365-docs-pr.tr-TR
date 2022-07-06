---
title: Twitter verilerini arşivleye bağlayıcı dağıtma
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ROBOTS: NOINDEX, NOFOLLOW
description: Yöneticiler, Twitter verilerini Microsoft 365'e aktarmak ve arşiv etmek için yerel bir bağlayıcı ayarlayabilir. Bu veriler Microsoft 365'e aktarıldıktan sonra, kuruluşunuzun Twitter verilerinin idaresini yönetmek için yasal tutma, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: bdc678fe1240b4b82a47d5cd091ee309a8153daa
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627767"
---
# <a name="deploy-a-connector-to-archive-twitter-data"></a>Twitter verilerini arşivleye bağlayıcı dağıtma

Bu makale, kuruluşunuzun Twitter hesabından Microsoft 365'e veri aktarmak için Office 365 İçeri Aktarma hizmetini kullanan bir bağlayıcıyı dağıtmaya yönelik adım adım işlemi içerir. Bu işleme üst düzey bir genel bakış ve Twitter bağlayıcısı dağıtmak için gereken önkoşulların listesi için bkz. [Twitter verilerini arşivleye bağlayıcı ayarlama ](archive-twitter-data-with-sample-connector.md).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>1. Adım: Azure Active Directory'de uygulama oluşturma

1. <https://portal.azure.com> Genel yönetici hesabının kimlik bilgilerini kullanarak adresine gidin ve oturum açın.

   ![Azure'da oturum açın.](../media/TCimage01.png)

2. Sol gezinti bölmesinde **Azure Active Directory'ye** tıklayın.

   ![Azure Active Directory'ye gidin.](../media/TCimage02.png)

3. Sol gezinti bölmesinde **Uygulama kayıtları (Önizleme)** seçeneğine ve ardından **Yeni kayıt'a** tıklayın.

   ![Yeni bir uygulama kaydı oluşturun.](../media/TCimage03.png)

4. Uygulamayı kaydedin. **Yeniden Yönlendirme URI'sinin (isteğe bağlı)** altında, uygulama türü açılan listesinde **Web'i** seçin ve URI'nin kutusuna yazın`https://portal.azure.com`.

   ![Yeniden yönlendirme URI'sini yazın https://portal.azure.com .](../media/TCimage04.png)

5. **Uygulama (istemci) kimliğini** ve **Dizin (kiracı) kimliğini** kopyalayın ve bunları bir metin dosyasına veya başka bir güvenli konuma kaydedin. Bu kimlikleri sonraki adımlarda kullanacaksınız.

    ![Uygulama Kimliği ve Dizin Kimliği'ni kopyalayıp kaydedin.](../media/TCimage05.png)

6. **Yeni uygulama için Sertifikalar & gizli dizileri'ne** gidin ve **İstemci gizli dizileri'nin** altında **Yeni istemci gizli dizisi'ne** tıklayın.

   ![Yeni bir istemci gizli dizisi oluşturun.](../media/TCimage06.png)

7. Yeni bir gizli dizi oluşturun. Açıklama kutusuna gizli diziyi yazın ve bir süre sonu seçin.

   ![Gizli diziyi yazın ve süre sonu seçin.](../media/TCimage08.png)

8. Gizli dizinin değerini kopyalayın ve bir metin dosyasına veya başka bir depolama konumuna kaydedin. Bu, sonraki adımlarda kullanacağınız AAD uygulama gizli dizisidir.

   ![Gizli diziyi kopyalayıp kaydedin.](../media/TCimage09.png)


## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>2. Adım: Bağlayıcı web hizmetini GitHub'dan Azure hesabınıza dağıtma

1. [Bu GitHub sitesine](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet) gidin ve **Azure'a Dağıt'a** tıklayın.

    ![Azure giriş sayfasına gidin.](../media/FBCimage11.png)

2. **Azure'a Dağıt'a** tıkladıktan sonra özel şablon sayfası içeren bir Azure portal yönlendirilirsiniz. **Temel Bilgiler** ve **Ayarlar** ayrıntılarını doldurun ve **satın al'a** tıklayın.

   ![Kaynak oluştur'a tıklayın ve depolama hesabı yazın.](../media/FBCimage12.png)

    - **Abonelik:** Twitter bağlayıcısı web hizmetini dağıtmak istediğiniz Azure aboneliğinizi seçin.

    - **Kaynak grubu:** Yeni bir kaynak grubu seçin veya oluşturun. Kaynak grubu, Bir Azure çözümü için ilgili kaynakları barındıran bir kapsayıcıdır.

    - **Konum:** Bir konum seçin.

    - **Web Uygulaması Adı:** Bağlayıcı web uygulaması için benzersiz bir ad sağlayın. Adın uzunluğu 3 ile 18 karakter arasında olmalıdır. Bu ad, Azure app service URL'sini oluşturmak için kullanılır; örneğin, **twitterconnector** web uygulaması adını sağlarsanız Azure uygulama hizmeti URL'si **twitterconnector.azurewebsites.net**.

    - **tenantId:** 1. Adımda Azure Active Directory'de Facebook bağlayıcı uygulamasını oluşturduktan sonra kopyaladığınız Microsoft 365 kuruluşunuzun kiracı kimliği.

   - **APISecretKey:** Herhangi bir değeri gizli dizi olarak yazabilirsiniz. Bu, 5. Adımda bağlayıcı web uygulamasına erişmek için kullanılır.

3. Dağıtım başarılı olduktan sonra sayfa aşağıdaki ekran görüntüsüne benzer:

    ![Depolama'ya ve ardından Depolama hesabı'ne tıklayın.](../media/FBCimage13.png)

## <a name="step-3-create-the-twitter-app"></a>3. Adım: Twitter uygulamasını oluşturma

1. adresine https://developer.twitter.comgidin, kuruluşunuzun geliştirici hesabının kimlik bilgilerini kullanarak oturum açın ve **ardından Uygulamalar'a** tıklayın.

   ![adresine https://developer.twitter.com gidin ve oturum açın.](../media/TCimage25-5.png)
2. **Uygulama oluştur'a** tıklayın.

   ![Uygulama oluşturmak için Uygulamalar sayfasına gidin.](../media/TCimage26.png)

3. **Uygulama ayrıntıları'nın** altında uygulama hakkında bilgi ekleyin.

   ![Uygulama hakkında bilgi girin.](../media/TCimage27.png)

4. Twitter geliştirici panosunda, yeni oluşturduğunuz uygulamayı seçin ve **ayrıntılar'a** tıklayın.

   ![Uygulama Kimliğini kopyalayın ve kaydedin.](../media/TCimage28.png)

5. **Anahtarlar ve belirteçler** sekmesindeki **Tüketici API'si anahtarları** altında hem API Anahtarını hem de API gizli anahtarı kopyalayın ve bunları bir metin dosyasına veya başka bir depolama konumuna kaydedin. Ardından **Oluştur'a** tıklayarak erişim belirteci ve erişim belirteci gizli dizisi oluşturun ve bunları bir metin dosyasına veya başka bir depolama konumuna kopyalayın.

   ![API gizli anahtarına kopyalayın ve kaydedin.](../media/TCimage29.png)

   Ardından **Oluştur'a** tıklayarak erişim belirteci ve erişim belirteci gizli dizisi oluşturun ve bunları bir metin dosyasına veya başka bir depolama konumuna kopyalayın.

6. **İzinler** sekmesine tıklayın ve aşağıdaki ekran görüntüsünde gösterildiği gibi izinleri yapılandırın:

   ![İzinleri yapılandırın.](../media/TCimage30.png)

7. İzin ayarlarını kaydettikten sonra **Uygulama ayrıntıları** sekmesine tıklayın ve ardından **Düzenle > Ayrıntıları düzenle'ye** tıklayın.

   ![Uygulama ayrıntılarını düzenleyin.](../media/TCimage31.png)

8. Aşağıdaki görevleri gerçekleştirin:

   - Bağlayıcı uygulamasının Twitter'da oturum açmasına izin vermek için onay kutusunu seçin.

   - Şu biçimi kullanarak OAuth yeniden yönlendirme Uri'sini ekleyin: **\<connectorserviceuri>/Views/TwitterOAuth**; *burada connectorserviceuri* değeri, kuruluşunuzun Azure uygulama hizmeti URL'sidir; örneğin, https://twitterconnector.azurewebsites.net/Views/TwitterOAuth.

    ![Bağlayıcı uygulamasının Twitter'da oturum açmasına ve OAuth yeniden yönlendirme Uri'sini eklemesine izin verin.](../media/TCimage32.png)

Twitter geliştirici uygulaması artık kullanıma hazırdır.

## <a name="step-4-configure-the-connector-web-app"></a>4. Adım: Bağlayıcı web uygulamasını yapılandırma

1. https://\<AzureAppResourceName>.azurewebsites.net (burada **AzureAppResourceName** , 4. Adımda adlandırdığınız Azure uygulama kaynağınızın adıdır). Örneğin, ad **twitterconnector** ise adresine gidin https://twitterconnector.azurewebsites.net. Uygulamanın giriş sayfası aşağıdaki ekran görüntüsüne benzer:

   ![Azure uygulama kaynağı sayfasına gidin.](../media/FBCimage41.png)

2. Oturum açma sayfasını görüntülemek için **Yapılandır'a** tıklayın.

   ![Oturum açma sayfasını görüntülemek için Yapılandır'a tıklayın.](../media/FBCimage42.png)

3. Kiracı Kimliği kutusuna kiracı kimliğinizi (2. Adımda edindiğiniz) yazın veya yapıştırın. Parola kutusuna APISecretKey (2. Adımda edindiğiniz) yazın veya yapıştırın ve yapılandırma ayrıntıları sayfasını görüntülemek için **Yapılandırma Ayarlarını Ayarla'ya** tıklayın.

   ![Kiracı kimliği ve API gizli anahtarı kullanarak oturum açın.](../media/TCimage35.png)

4. Aşağıdaki yapılandırma ayarlarını girin

   - **Twitter Api Anahtarı:** 3. Adımda oluşturduğunuz Twitter uygulamasının API anahtarı.

   - **Twitter Api Gizli Anahtarı:** 3. Adımda oluşturduğunuz Twitter uygulamasının API gizli anahtarı.

   - **Twitter Erişim Belirteci:** 3. Adımda oluşturduğunuz erişim belirteci.

   - **Twitter Erişim Belirteci Gizli Anahtarı:** 3. Adımda oluşturduğunuz erişim belirteci gizli dizisi.

   - **AAD Uygulama Kimliği:** 1. Adımda oluşturduğunuz Azure Active Directory uygulamasının uygulama kimliği

   - **AAD Uygulama Gizli Anahtarı:** 1. Adımda oluşturduğunuz APISecretKey gizli dizisinin değeri.

5. Bağlayıcı ayarlarını kaydetmek için **Kaydet'e** tıklayın.

## <a name="step-5-set-up-a-twitter-connector-in-the-compliance-portal"></a>5. Adım: Uyumluluk portalında Twitter bağlayıcısı ayarlama

1. Microsoft Purview uyumluluk portalı gidin ve /a<**Veri bağlayıcıları** sayfasını seçin<a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">.

2. **Twitter'ın** altındaki **Veri bağlayıcıları** sayfasında **Görüntüle'ye** tıklayın.

3. **Twitter** sayfasında **Bağlayıcı ekle'ye** tıklayın.

4. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

5. **Bağlayıcı uygulamanız için kimlik bilgileri ekle** sayfasında aşağıdaki bilgileri girin ve Bağlantıyı **doğrula'ya** tıklayın.

   ![Bağlayıcı uygulaması kimlik bilgilerini girin.](../media/TCimage38.png)

    - **Ad** kutusuna bağlayıcı için **Twitter yardım işleme** gibi bir ad yazın.

    - **Bağlayıcı URL'si** kutusuna Azure app service URL'sini yazın veya yapıştırın; örneğin`https://twitterconnector.azurewebsites.net`, .

    - **Parola** kutusuna, 2. Adımda oluşturduğunuz APISecretKey değerini yazın veya yapıştırın.

    - **Azure Uygulaması Kimliği** kutusuna, 1. Adımda aldığınız Azure Uygulaması Uygulama Kimliğinin (*istemci kimliği* olarak da adlandırılır) değerini yazın veya yapıştırın.

6. Bağlantı başarıyla doğrulandıktan sonra **İleri'ye** tıklayın.

7. **Microsoft 365'i veri içeri aktarma yetkisi ver** sayfasında APISecretKey'i yeniden yazın veya yapıştırın ve ardından **Web uygulamasını oturum aç'a** tıklayın.

8. **Twitter ile oturum aç'a** tıklayın.

9. Twitter oturum açma sayfasında, kuruluşunuzun Twitter hesabının kimlik bilgilerini kullanarak oturum açın.

   ![Twitter hesabında oturum açın.](../media/TCimage42.png)

   Oturum açıldıktan sonra Twitter sayfasında şu ileti görüntülenir: "Twitter Bağlayıcı İşi Başarıyla ayarlandı."

10. Twitter bağlayıcısını ayarlamayı tamamlamak için **Devam'a** tıklayın.

11. **Filtreleri ayarla** sayfasında, başlangıçta belirli bir yaştaki öğeleri içeri aktarmak için bir filtre uygulayabilirsiniz. Bir yaş seçin ve **İleri'ye** tıklayın.

12. **Depolama konumu seçin** sayfasında, Twitter öğelerinin içeri aktarılacağı Microsoft 365 posta kutusunun e-posta adresini yazın ve **İleri'ye** tıklayın.

13. Bağlayıcı ayarlarını gözden geçirmek için **İleri'ye** tıklayın ve ardından bağlayıcı kurulumunu tamamlamak için **Son'a** tıklayın.

14. Uyumluluk merkezinde **Veri bağlayıcıları** sayfasına gidin ve içeri aktarma işleminin ilerleme durumunu görmek için **Bağlayıcılar** sekmesine tıklayın.
