---
title: Twitter verilerini arşivlemek için bağlayıcıyı dağıtma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Yöneticiler Twitter verilerini içeri aktaracak ve arşiv olarak aktaracak yerel bir bağlayıcı Microsoft 365. Bu veriler Microsoft 365'a aktarıldıktan sonra, yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kurumnizin Twitter verilerini yönetebilirsiniz.
ms.openlocfilehash: bd0885c0b9893b79d36981d52f596d1e5d6b8396
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990569"
---
# <a name="deploy-a-connector-to-archive-twitter-data"></a>Twitter verilerini arşivlemek için bağlayıcıyı dağıtma

Bu makale, Office 365 İçeri Aktarma hizmetini kullanarak kuruluş Twitter hesabından verileri kendi Twitter hesabınıza aktaran bağlayıcıyı dağıtmak için adım adım Microsoft 365. Bu işleme üst düzey bir genel bakış ve Twitter bağlayıcısı dağıtımı için gereken önkoşulların listesi için bkz. Twitter verilerini arşivlemek için [bağlayıcı ayarlama ](archive-twitter-data-with-sample-connector.md).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>1. Adım: Azure Active Directory'de uygulama oluşturma

1. Genel yönetici <https://portal.azure.com> hesabının kimlik bilgilerini kullanarak oturum açın ve gidin.

   ![Azure'da oturum açma.](../media/TCimage01.png)

2. Sol gezinti bölmesinde Ekle'ye **Azure Active Directory**.

   ![Diğer'e Azure Active Directory.](../media/TCimage02.png)

3. Sol gezinti bölmesinde Uygulama kayıtları **(Önizleme) öğesini ve ardından** Yeni kayıt'ı **tıklatın**.

   ![Yeni bir uygulama kaydı oluşturun.](../media/TCimage03.png)

4. Uygulamayı kaydettirin. **URI'yi yeniden yönlendirme (** isteğe bağlı)'nın altında, uygulama türü açılan listesinde **Web'i** `https://portal.azure.com` seçin ve URI'nin kutusuna yazın.

   ![Yönlendirme https://portal.azure.com URI'sini yazın.](../media/TCimage04.png)

5. Uygulama **(istemci) Kimliği ve** **Dizin (kiracı) kimliğini** kopyalayın ve bunları bir metin dosyasına veya başka bir güvenli konuma kaydedin. Bu kimlikleri sonraki adımlarda kullanırız.

    ![Uygulama Kimliği'ne ve Dizin Kimliği'ne kopyalayıp kaydedin.](../media/TCimage05.png)

6. Yeni **uygulamanın sertifikalar & ve İstemci** sırrı altında **Yeni istemci** **sırrı'ya tıklayın**.

   ![Yeni bir istemci sırrı oluşturun.](../media/TCimage06.png)

7. Yeni bir gizli oluşturun. Açıklama kutusuna parolayı yazın ve bir son kullanma süresi seçin.

   ![Parolayı yazın ve son kullanma süresini seçin.](../media/TCimage08.png)

8. Gizlinin değerini kopyalayın ve bir metin dosyasına veya başka bir depolama konuma kaydedin. Bu, AAD adımlarda kullanabileceğiniz en gizli uygulama sırrıdır.

   ![Kopyalayıp gizlileri kaydedin.](../media/TCimage09.png)


## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>2. Adım: Bağlayıcı web hizmetini Azure GitHub doğru dağıtma

1. Bu [siteyi ziyaret GitHub Azure'a](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet) **Dağıt'a tıklayın**.

    ![Azure giriş sayfasına gidin.](../media/FBCimage11.png)

2. **Azure'a Dağıt'a** tıklarsanız, özel şablon sayfasının olduğu bir Azure portalına yönlendirildiniz. Temel bilgiler ve **Ayrıntılar'ı** **Ayarlar** Satın Alma'ya **tıklayın**.

   ![Kaynak oluştur'a tıklayın ve depolama hesabı yazın.](../media/FBCimage12.png)

    - **Abonelik:** Twitter bağlayıcısı web hizmetini dağıtmak istediğiniz Azure aboneliğinizi seçin.

    - **Kaynak grubu:** Yeni bir kaynak grubu seçin veya oluşturun. Kaynak grubu, bir Azure çözümü için ilgili kaynakları bulunduran bir kapsayıcıdır.

    - **Konum:** Bir konum seçin.

    - **Web Uygulaması Adı:** Bağlayıcı web uygulaması için benzersiz bir ad girin. Ad, 3 ile 18 karakter arasında olmalıdır. Bu ad, Azure uygulama hizmeti URL'sini oluşturmak için kullanılır; örneğin, **twitterconnector** web uygulaması adını sağlarsanız Azure uygulama hizmeti URL'si **twitterconnector.azurewebsites.net.**

    - **tenantId:** 1. Adım'Microsoft 365 Azure Active Directory'de Facebook bağlayıcısı uygulamasını oluşturdukta kopyalanmış olan kullanıcı veya kuruluş kiracı kimliği.

   - **APISecretKey:** Gizli olarak istediğiniz değeri yazın. Bu, 5. Adımda bağlayıcı web uygulamasına erişmek için kullanılır.

3. Dağıtım başarılı olduktan sonra, sayfa aşağıdaki ekran görüntüsüne benzer:

    ![Hesap'Depolama ardından Hesap Ekle'Depolama tıklayın.](../media/FBCimage13.png)

## <a name="step-3-create-the-twitter-app"></a>3. Adım: Twitter uygulamasını oluşturma

1. 'a https://developer.twitter.comgidin, kuruma uygun geliştirici hesabının kimlik bilgilerini kullanarak oturum açın ve Uygulamalar'a **tıklayın**.

   ![Gidin ve https://developer.twitter.com oturum aç'a gidin.](../media/TCimage25-5.png)
2. Uygulama **oluştur'a tıklayın**.

   ![Uygulama oluşturmak için Uygulamalar sayfasına gidin.](../media/TCimage26.png)

3. Uygulama **ayrıntıları'nın** altında uygulama hakkında bilgi ekleyin.

   ![Uygulama hakkında bilgi girin.](../media/TCimage27.png)

4. Twitter geliştirici panosunda, yeni oluşturduğunuz uygulamayı seçin ve Ayrıntılar'a **tıklayın**.

   ![Uygulama Kimliğini kopyalayın ve kaydedin.](../media/TCimage28.png)

5. Anahtarlar ve **belirteçler sekmesinde** , Tüketici **API** anahtarları altında, hem API Anahtarı hem de API gizli anahtarı kopyalayıp bunları bir metin dosyasına veya başka bir depolama alanına kaydedin. Ardından bir erişim **belirteci** ve erişim belirteci sırrı oluşturmak ve bunları bir metin dosyasına veya başka bir depolama konuma kopyalamak için Oluştur'a tıklayın.

   ![API gizli anahtarını kopyalayın ve kaydedin.](../media/TCimage29.png)

   Ardından bir **erişim belirteci** ve erişim belirteci sırrı oluşturmak için Oluştur'a tıklayın ve bunları bir metin dosyasına veya başka bir depolama konuma kopyalayın.

6. İzinler **sekmesine** tıklayın ve aşağıdaki ekran görüntüsünde gösterildiği gibi izinleri yapılandırabilirsiniz:

   ![İzinleri yapılandırabilirsiniz.](../media/TCimage30.png)

7. İzin ayarlarını kaydeddikten sonra, Uygulama ayrıntıları **sekmesine tıklayın ve** sonra da Ayrıntıları **düzenle'ye > tıklayın**.

   ![Uygulama ayrıntılarını düzenleyin.](../media/TCimage31.png)

8. Aşağıdaki görevleri yerine kullanın:

   - Bağlayıcı uygulamasının Twitter'da oturum açmasına izin vermek için onay kutusunu seçin.

   - Şu biçimi kullanarak OAuth redirect Uri'sini ekleyin: **\<connectorserviceuri>/Views/TwitterOAuth**; burada *connectorserviceuri'nin* değeri, kuruma ilişkin Azure uygulama hizmeti URL'sinin değeridir; örneğin, https://twitterconnector.azurewebsites.net/Views/TwitterOAuth.

    ![Bağlayıcı uygulamasının Twitter'da oturum açmasına ve OAuth redirect Uri eklemesine izin ver.](../media/TCimage32.png)

Twitter geliştirici uygulaması artık kullanıma hazırdır.

## <a name="step-4-configure-the-connector-web-app"></a>4. Adım: Bağlayıcı web uygulamasını yapılandırma

1. https://\<AzureAppResourceName>.azurewebsites.net gidin (burada **AzureAppResourceName** , 4. Adımda adlandırdınız Azure uygulama kaynağınızdır). Örneğin, bu ad **twitterconnector ise**, bağlantısına gidin https://twitterconnector.azurewebsites.net. Uygulamanın giriş sayfası aşağıdaki ekran görüntüsüne benzer:

   ![Azure uygulama kaynak sayfasına gidin.](../media/FBCimage41.png)

2. Oturum **açma sayfasını** görüntülemek için Yapılandır'a tıklayın.

   ![Oturum açma sayfasını görüntülemek için Yapılandır'a tıklayın.](../media/FBCimage42.png)

3. Kiracı Kimliği kutusunda, kiracı kimliğinizi (2. Adımda edinilen) yazın veya yapıştırın. Parola kutusunda, APISecretKey'i (2. Adımda elde edilen) yazın veya yapıştırın ve sonra yapılandırma ayrıntıları sayfasını görüntülemek için **Ayarlar** YapılandırmaYı Ayarla'ya tıklayın.

   ![Kiracı Kimliği ve API gizli anahtarını kullanarak oturum açma.](../media/TCimage35.png)

4. Aşağıdaki yapılandırma ayarlarını girin

   - **Twitter Api Anahtarı:** 3. Adımda oluşturduğunuz Twitter uygulamasının API anahtarı.

   - **Twitter Api Gizli Anahtarı:** 3. Adımda oluşturduğunuz Twitter uygulaması için API gizli anahtarı.

   - **Twitter Erişim Belirteci:** 3. Adım'da oluşturduğunuz erişim belirteci.

   - **Twitter Erişim Belirteci Sırrı:** 3. Adımda oluşturduğunuz erişim belirteci sırrı.

   - **AAD Kimliği:** 1. Adımda Azure Active Directory uygulamanın uygulama kimliği

   - **AAD Sırrı:** 1. Adımda oluşturduğunuz APISecretKey sırrının değeri.

5. Bağlayıcı **ayarlarını kaydetmek** için Kaydet'e tıklayın.

## <a name="step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center"></a>5. Adım: İçerik bağlantılarında Twitter bağlayıcısı Microsoft 365 uyumluluk merkezi

1. Bağlayıcılar'a Microsoft 365 uyumluluk merkezi **ve Veri bağlayıcıları** <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank"> sayfası '<seçin.

2. **Twitter'nın altındaki Veri bağlayıcıları** sayfasında **Görüntüle'ye** **tıklayın**.

3. Twitter sayfasında **Bağlayıcı** **ekle'ye tıklayın**.

4. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

5. Bağlayıcı **uygulamanız için kimlik bilgileri ekleyin sayfasında** , aşağıdaki bilgileri girin ve Bağlantıyı doğrula'ya **tıklayın**.

   ![Bağlayıcı uygulaması kimlik bilgilerini girin.](../media/TCimage38.png)

    - Ad **kutusuna** bağlayıcı için Twitter yardım tutamacı gibi bir **ad yazın**.

    - Bağlayıcı **URL'si** kutusuna Azure uygulama hizmeti URL'sini yazın veya yapıştırın; `https://twitterconnector.azurewebsites.net`örneğin.

    - Parola **kutusunda** , 2. Adımda oluşturduğunuz APISecretKey değerini yazın veya yapıştırın.

    - **Azure Uygulama Kimliği kutusunda**, 1. Adımda edinilen Azure Uygulama Kimliği'nin (istemci kimliği olarak da *adlandırılan) değerini* yazın veya yapıştırın.

6. Bağlantı başarıyla doğrulandıktan sonra, Sonraki'ne **tıklayın**.

7. **Yetkilendir Microsoft 365 veri** içeri aktar sayfasında APISecretKey öğesini yeniden yazın veya yapıştırın ve ardından Oturum aç **web uygulaması'nı tıklatın**.

8. **Twitter ile oturum aç'a tıklayın**.

9. Twitter oturum açma sayfasında, kuruma ilişkin Twitter hesabının kimlik bilgilerini kullanarak oturum açın.

   ![Twitter hesabında oturum açın.](../media/TCimage42.png)

   Oturum olduktan sonra, Twitter sayfasında "Twitter Connector Job Successfully set up" iletisi görüntülenir.

10. Twitter **bağlayıcısı** ayarlamayı tamamlamak için Devam'a tıklayın.

11. Filtreleri **ayarla sayfasında** , başlangıçta belirli bir yaş olan öğeleri içeri aktarmaya filtre uygulayabilirsiniz. Bir yaş seçin ve Ardından Sonraki'ye **tıklayın**.

12. Depolama **konumunu seçin sayfasında**, Twitter öğelerinin aktar Microsoft 365 posta kutusunun e-posta adresini yazın ve ardından Sonraki'ye **tıklayın**.

13. Bağlayıcı **ayarlarını gözden** geçirmek için Sonraki'ne tıklayın ve sonra **da bağlayıcı kurulumunu** tamamlamak için Son'a tıklayın.

14. Uyumluluk merkezinde Veri bağlayıcıları **sayfasına gidin** ve içeri aktarma işleminin ilerlemesini **görmek için** Bağlayıcılar sekmesine tıklayın.
