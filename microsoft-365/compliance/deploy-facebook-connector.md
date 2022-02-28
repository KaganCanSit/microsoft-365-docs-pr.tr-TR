---
title: Facebook İş sayfaları verilerini arşivlemek için bağlayıcıyı dağıtma
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
description: Yöneticiler, Facebook İş sayfalarını içeri aktaracak ve arşivleyacak yerel bir bağlayıcı Microsoft 365. Bu veriler Microsoft 365'a aktarıldıktan sonra, yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak, kurumnizin Facebook verilerini yönetebilirsiniz.
ms.openlocfilehash: 0bbe7f65ef6226386911817b40bbaaa418cdabec
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990570"
---
# <a name="deploy-a-connector-to-archive-facebook-business-pages-data"></a>Facebook İş sayfaları verilerini arşivlemek için bağlayıcıyı dağıtma

Bu makale, Facebook Business sayfalarından Facebook Business sayfalarına veri içeri aktarma işlemi Office 365 Içeri Aktarma hizmetini kullanan bir bağlayıcıyı dağıtmak için adım adım Microsoft 365. Bu işleme üst düzey bir genel bakış ve Facebook bağlayıcısı dağıtımı için gereken önkoşulların listesi için bkz. Facebook verilerini arşivlemek için [bağlayıcı ayarlama](archive-facebook-data-with-sample-connector.md).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>1. Adım: Azure Active Directory'de uygulama oluşturma

1. Genel yönetici <https://portal.azure.com> hesabının kimlik bilgilerini kullanarak oturum açın ve gidin.

    ![Mobil uygulamada AAD.](../media/FBCimage1.png)

2. Sol gezinti bölmesinde Ekle'ye **Azure Active Directory**.

    ![Ekle'Azure Active Directory.](../media/FBCimage2.png)

3. Sol gezinti bölmesinde Uygulama kayıtları **(Önizleme) öğesini ve ardından** Yeni kayıt'ı **tıklatın**.

    ![**Uygulama kayıtları (Önizleme)** öğesini ve ardından **Yeni kayıt**'a tıklayın.](../media/FBCimage3.png)

4. Uygulamayı kaydettirin. Yeniden yönlendirme URI'si altında, uygulama türü açılan <https://portal.azure.com> listesinde Web'i seçin ve URI'nin kutusuna yazın.

   ![Uygulamayı kaydettirin.](../media/FBCimage4.png)

5. Uygulama **(istemci) Kimliği ve** **Dizin (kiracı) kimliğini** kopyalayın ve bunları bir metin dosyasına veya başka bir güvenli konuma kaydedin. Bu kimlikleri sonraki adımlarda kullanırız.

   ![Uygulama Kimliği'ne ve Dizin Kimliği'ne kopyalayıp kaydedin.](../media/FBCimage5.png)

6. Yeni uygulama **için & sırrı sertifikalar'a gidin.**

   ![Yeni uygulama için & sırrı sertifikalar'a gidin.](../media/FBCimage6.png)

7. Yeni istemci **sırrı'ne tıklayın**

   ![Yeni istemci sırrı'ya tıklayın.](../media/FBCimage7.png)

8. Yeni bir gizli oluşturun. Açıklama kutusuna parolayı yazın ve bir son kullanma süresi seçin.

    ![Parolayı yazın ve bir son kullanma süresi seçin.](../media/FBCimage8.png)

9. Gizlinin değerini kopyalayın ve bir metin dosyasına veya başka bir depolama konuma kaydedin. Bu, AAD adımlarda kullanabileceğiniz en gizli uygulama sırrıdır.

   ![Gizli değeri kopyalayın ve kaydedin.](../media/FBCimage9.png)

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>2. Adım: Bağlayıcı web hizmetini Azure GitHub doğru dağıtma

1. Bu [siteyi ziyaret GitHub Azure'a](https://github.com/microsoft/m365-sample-connector-csharp-aspnet) **Dağıt'a tıklayın**.

    ![Azure'a Dağıt'a tıklayın.](../media/FBCGithubApp.png)

2. **Azure'a Dağıt'a** tıklarsanız, özel şablon sayfasının olduğu bir Azure portalına yönlendirildiniz. Temel bilgiler ve **Ayrıntılar'ı** **Ayarlar** Satın Alma'ya **tıklayın**.

   - **Abonelik:** Facebook İş sayfaları bağlayıcısı web hizmetini dağıtmak istediğiniz Azure aboneliğinizi seçin.

   - **Kaynak grubu:** Yeni bir kaynak grubu seçin veya oluşturun. Kaynak grubu, bir Azure çözümü için ilgili kaynakları bulunduran bir kapsayıcıdır.

   - **Konum:** Bir konum seçin.

   - **Web Uygulaması Adı:** Bağlayıcı web uygulaması için benzersiz bir ad girin. Ad, 3 ile 18 karakter arasında olmalıdır. Bu ad, Azure uygulama hizmeti URL'sini oluşturmak için kullanılır; örneğin, **fbconnector** web uygulaması adını sağlarsanız, Azure uygulama hizmeti URL'si **fbconnector.azurewebsites.net.**

   - **tenantId:** 1. Adımda Microsoft 365 Facebook bağlayıcısı uygulamasını oluşturdukta kopyalanmış olan Azure Active Directory kiracı kimliği.

   - **APISecretKey:** Gizli olarak istediğiniz değeri yazın. Bu, 5. Adımda bağlayıcı web uygulamasına erişmek için kullanılır.

     ![Kaynak oluştur'a tıklayın ve depolama hesabı yazın.](../media/FBCimage12.png)

3. Dağıtım başarılı olduktan sonra, sayfa aşağıdaki ekran görüntüsüne benzer:

   ![Hesap'Depolama ardından Hesap Ekle'Depolama tıklayın.](../media/FBCimage13.png)

## <a name="step-3-register-the-facebook-app"></a>3. Adım: Facebook uygulamasını kaydetme

1. 'a <https://developers.facebook.com>gidin, kuruluşun Facebook İş sayfalarının hesabı için kimlik bilgilerini kullanarak oturum açın ve ardından Yeni Uygulama **Ekle'ye tıklayın**.

   ![Facebook işletme sayfası için yeni bir uygulama ekleyin.](../media/FBCimage25.png)

2. Yeni bir uygulama kimliği oluşturun.

   ![Yeni bir uygulama kimliği oluşturun.](../media/FBCimage26.png)

3. Sol gezinti bölmesinde Ürün **Ekle'ye tıklayın ve ardından** Facebook Oturum Açma **kutucuğunun** **Ayarla'ya** tıklayın.

   ![Ürün Ekle'ye tıklayın.](../media/FBCimage27.png)

4. Facebook Oturum Açma'yı Tümleştir sayfasında **Web'e tıklayın**.

   ![Facebook Oturum Açma'yı Tümleştir sayfasında Web'e tıklayın.](../media/FBCimage28.png)

5. Azure uygulama hizmeti URL'sini ekleyin; `https://fbconnector.azurewebsites.net`örneğin.

   ![Azure uygulama hizmeti URL'sini ekleyin.](../media/FBCimage29.png)

6. Facebook Oturum Açma kurulumunun Hızlı Başlangıç bölümünü tamamlama.

   ![Hızlı Başlangıç bölümünü tamamlama.](../media/FBCimage30.png)

7. Sol gezinti bölmesinde **Facebook** Oturumu Aç altında, Ayarlar'e tıklayın ve Geçerli **OAuth Redirect URI'leri kutusuna OAuth Redirect URI'sini** ekleyin. Connectorserviceuri değeri, kurum için Azure uygulama hizmeti URL'si olduğu **/Views/FacebookOAuth biçimini kullanın; örneğin, .\<connectorserviceuri>**`https://fbconnector.azurewebsites.net`

   ![OAuth redirect URI'sini Geçerli OAuth Redirect URI'leri kutusuna ekleyin.](../media/FBCimage31.png)

8. Sol gezinti bölmesinde Ürün **Ekle'ye ve ardından** **Web'ler'e tıklayın.** Sayfa **açılır** menüsünde Sayfa'ya **tıklayın**.

   ![Ürün Ekle'ye ve ardından **Web'ler'e tıklayın.](../media/FBCimage32.png)

9. Web Sertifikalarını Geri Çağır URL'si ekleyin ve bir doğrulama belirteci ekleyin. Geri arama URL'sinin biçimi, biçimini kullanın; `<connectorserviceuri>/api/FbPageWebhook`burada connectorserviceuri değeri, kurum için Azure uygulama hizmeti URL'si'dir; örneğin `https://fbconnector.azurewebsites.net`.

   Doğrulama belirteci, güçlü bir parolaya benzer. Belirteci bir metin dosyasına veya başka bir depolama konuma kopyalayın.

   ![Doğrulama belirteci ekleyin.](../media/FBCimage33.png)

10. Akış için uç noktayı test etmek ve abone olmak.

    ![Uç noktayı test etmek ve uç noktaya abone olmak.](../media/FBCimage34.png)

11. Gizlilik URL'si, uygulama simgesi ve iş kullanımı ekleyin. Ayrıca, uygulama kimliğini ve uygulama sırrını bir metin dosyasına veya başka bir depolama alanına kopyalayın.

    ![Gizlilik URL'si, uygulama simgesi ve iş kullanımı ekleyin.](../media/FBCimage35.png)

12. Uygulamayı genel yapma.

    ![Uygulamayı genel yapma.](../media/FBCimage36.png)

13. Yönetici veya testci rolüne kullanıcı ekleyin.

    ![Yönetici veya testci rolüne kullanıcı ekleyin.](../media/FBCimage37.png)

14. Sayfa Genel **İçerik Erişimi iznini** ekleyin.

    ![dd Sayfa Genel İçerik Erişimi izni.](../media/FBCimage38.png)

15. Sayfaları Yönetme izni ekleyin.

    ![Sayfaları Yönetme izni ekleyin.](../media/FBCimage39.png)

16. Uygulamayı Facebook tarafından gözden geçirmeyi sağlar.

    ![Uygulamayı Facebook tarafından gözden geçirmeyi sağlar.](../media/FBCimage40.png)

## <a name="step-4-configure-the-connector-web-app"></a>4. Adım: Bağlayıcı web uygulamasını yapılandırma

1. `https://<AzureAppResourceName>.azurewebsites.net` Git (burada AzureAppResourceName, 4. Adımda adlandır adlandırdınız Azure uygulama kaynağı adının adıdır). Örneğin, bu ad **fbconnector ise**, bağlantısına gidin `https://fbconnector.azurewebsites.net`. Uygulamanın giriş sayfası aşağıdaki ekran görüntüsüne benzer:

   ![Bağlayıcı web uygulaması'nız'a gidin.](../media/FBCimage41.png)

2. Oturum **açma sayfasını** görüntülemek için Yapılandır'a tıklayın.

   ![Oturum açma sayfasını görüntülemek için Yapılandır'a tıklayın.](../media/FBCimage42.png)

3. Kiracı Kimliği kutusunda, kiracı kimliğinizi (2. Adımda edinilen) yazın veya yapıştırın. Parola kutusunda, APISecretKey'i (2. Adımda elde edilen) yazın veya yapıştırın ve sonra yapılandırma ayrıntıları sayfasını görüntülemek için **Ayarlar** YapılandırmaYı Ayarla'ya tıklayın.

    ![Kiracı kimliğiniz ve parolanızı kullanarak oturum açma ve yapılandırma ayrıntıları sayfasına gidin.](../media/FBCimage43.png)

4. Aşağıdaki yapılandırma ayarlarını girin

   - **Facebook uygulama kimliği:** 3. Adımda edinilen Facebook uygulamasının uygulama kimliği.

   - **Facebook uygulaması sırrı:** 3. Adımda edinilen Facebook uygulamasının uygulama sırrı.

   - **Facebook web sertifikalarını doğrulama belirteci:** 3. Adımda oluşturduğunuz doğrulama belirteci.

   - **AAD kimliği:** 1. Adımda Azure Active Directory uygulamanın uygulama kimliği.

   - **AAD gizlidir:** 1. Adımda oluşturduğunuz APISecretKey sırrının değeri.

5. Bağlayıcı **ayarlarını kaydetmek** için Kaydet'e tıklayın.

## <a name="step-5-set-up-a-facebook-connector-in-the-microsoft-365-compliance-center"></a>5. Adım: Bağlantıda Facebook bağlayıcısı Microsoft 365 uyumluluk merkezi

1. Bağlantı'ya Microsoft 365 uyumluluk merkezi ve sonra Veri **bağlayıcıları** <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank"> /a<seçin.

2. Facebook İş **sayfalarının altındaki** Veri **bağlayıcıları sayfasında Görünüm'e** **tıklayın**.

3. Facebook iş **sayfaları sayfasında Bağlayıcı** **ekle'ye tıklayın**.

4. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

5. Bağlayıcı **uygulamanız için kimlik bilgileri ekleyin sayfasında** , aşağıdaki bilgileri girin ve Bağlantıyı doğrula'ya **tıklayın**.

   ![Bağlayıcı uygulaması kimlik bilgilerini girin.](../media/TCimage38.png)

   - Ad **kutusuna** bağlayıcı için Facebook haber sayfası gibi bir **ad yazın**.

   - Bağlantı **URL'si** kutusuna Azure uygulama hizmeti URL'sini yazın veya yapıştırın; `https://fbconnector.azurewebsites.net`örneğin.

   - Parola **kutusunda** , 2. Adımda ekley istediğiniz APISecretKey değerini yazın veya yapıştırın.

   - **Azure Uygulama Kimliği kutusunda**, 1. Adımda oluşturduğunuz Uygulama Kimliği AAD Uygulama Kimliği olarak da adlandırılan Uygulama (istemci) kimliğini yazın veya yapıştırın.

6. Bağlantı başarıyla doğrulandıktan sonra, Sonraki'ne **tıklayın**.

7. **Yetkilendir Microsoft 365 veri** içeri aktar sayfasında APISecretKey öğesini yeniden yazın veya yapıştırın ve ardından Oturum aç **web uygulaması'nı tıklatın**.

8. **Facebook bağlayıcısı uygulamasını yapılandır sayfasında** **Facebook** ile oturum aç'a tıklayın ve kuruluşun Facebook İş sayfalarının hesap bilgilerini kullanarak oturum açın. Oturum açtığınız Facebook hesabına, kurumnizin Facebook İş sayfaları için yönetici rolü atan olduğundan emin olun.

   ![Facebook ile oturum açma.](../media/FBCimage50.png)

9. Oturum açtığınız Facebook hesabı tarafından yönetilen iş sayfalarının listesi görüntülenir. Arşivlemek istediğiniz sayfayı seçin ve ardından Sonraki'ye **tıklayın**.

   ![Arşivlemek istediğiniz kuruluş iş sayfasını seçin.](../media/FBCimage52.png)

10. Bağlayıcı **hizmet** uygulamasının kurulumundan çıkmak için Devam'a tıklayın.

11. Filtreleri **ayarla sayfasında** , başlangıçta belirli bir yaş olan öğeleri içeri aktarmaya filtre uygulayabilirsiniz. Bir yaş seçin ve Ardından Sonraki'ye **tıklayın**.

12. Depolama **konumunu seçin sayfasında**, Facebook öğelerinin aktar Microsoft 365 posta kutusunun e-posta adresini yazın ve ardından Sonraki'ye **tıklayın**.

13. Bağlayıcı **ayarlarını gözden** geçirmek için Sonraki'ne tıklayın ve sonra **da bağlayıcı kurulumunu** tamamlamak için Son'a tıklayın.

14. Uyumluluk merkezinde Veri bağlayıcıları **sayfasına gidin** ve içeri aktarma işleminin ilerlemesini **görmek için** Bağlayıcılar sekmesine tıklayın.
