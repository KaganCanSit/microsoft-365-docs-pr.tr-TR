---
title: Facebook business sayfaları verilerini arşivleye bağlayıcı dağıtma
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
description: Yöneticiler, Facebook İş sayfalarını Microsoft 365 içeri aktarmak ve arşiv uygulamak için yerel bir bağlayıcı ayarlayabilir. Bu veriler Microsoft 365 aktarıldıktan sonra, kuruluşunuzun Facebook verilerinin idaresini yönetmek için yasal tutma, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 126b4af3887632df5c8f83eac8e20fe5d88c8608
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64949189"
---
# <a name="deploy-a-connector-to-archive-facebook-business-pages-data"></a>Facebook business sayfaları verilerini arşivleye bağlayıcı dağıtma

Bu makale, Facebook business sayfalarından Microsoft 365 verileri içeri aktarmak için Office 365 İçeri Aktarma hizmetini kullanan bir bağlayıcıyı dağıtmaya ilişkin adım adım işlemi içerir. Bu işleme üst düzey bir genel bakış ve Bir Facebook bağlayıcısını dağıtmak için gereken önkoşulların listesi için bkz. [Facebook verilerini arşiv etmek için bağlayıcı ayarlama](archive-facebook-data-with-sample-connector.md).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>1. Adım: Azure Active Directory'de uygulama oluşturma

1. <https://portal.azure.com> Genel yönetici hesabının kimlik bilgilerini kullanarak adresine gidin ve oturum açın.

    ![AAD'de uygulama oluşturun.](../media/FBCimage1.png)

2. Sol gezinti bölmesinde **Azure Active Directory'e** tıklayın.

    ![Azure Active Directory'e tıklayın.](../media/FBCimage2.png)

3. Sol gezinti bölmesinde **Uygulama kayıtları (Önizleme)** seçeneğine ve ardından **Yeni kayıt'a** tıklayın.

    ![**Uygulama kayıtları (Önizleme)** seçeneğine ve ardından **Yeni kayıt**'a tıklayın.](../media/FBCimage3.png)

4. Uygulamayı kaydedin. Yeniden Yönlendirme URI'sinin altında, uygulama türü açılan listesinde Web'i seçin ve ardından URI kutusuna yazın <https://portal.azure.com> .

   ![Uygulamayı kaydedin.](../media/FBCimage4.png)

5. **Uygulama (istemci) kimliğini** ve **Dizin (kiracı) kimliğini** kopyalayın ve bunları bir metin dosyasına veya başka bir güvenli konuma kaydedin. Bu kimlikleri sonraki adımlarda kullanacaksınız.

   ![Uygulama Kimliği ve Dizin Kimliği'ni kopyalayıp kaydedin.](../media/FBCimage5.png)

6. **Yeni uygulama için Sertifikalar & gizli dizileri'ne gidin.**

   ![Yeni uygulama için Sertifikalar & gizli diziler'e gidin.](../media/FBCimage6.png)

7. **Yeni istemci gizli dizisi'ne** tıklayın

   ![Yeni istemci gizli dizisi'ne tıklayın.](../media/FBCimage7.png)

8. Yeni bir gizli dizi oluşturun. Açıklama kutusuna gizli diziyi yazın ve bir süre sonu seçin.

    ![Gizli diziyi yazın ve bir süre sonu seçin.](../media/FBCimage8.png)

9. Gizli dizinin değerini kopyalayın ve bir metin dosyasına veya başka bir depolama konumuna kaydedin. Bu, sonraki adımlarda kullandığınız AAD uygulama gizli dizisidir.

   ![Gizli anahtarın değerini kopyalayın ve kaydedin.](../media/FBCimage9.png)

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>2. Adım: Bağlayıcı web hizmetini GitHub Azure hesabınıza dağıtma

1. [Bu GitHub sitesine](https://github.com/microsoft/m365-sample-connector-csharp-aspnet) gidin ve **Azure'a Dağıt'a** tıklayın.

    ![Azure'a Dağıt'a tıklayın.](../media/FBCGithubApp.png)

2. **Azure'a Dağıt'a** tıkladıktan sonra özel şablon sayfası içeren bir Azure portal yönlendirilirsiniz. **Temel bilgiler** ve **Ayarlar** ayrıntılarını doldurun ve **Satın Al'a** tıklayın.

   - **Abonelik:** Facebook İş sayfaları bağlayıcısı web hizmetini dağıtmak istediğiniz Azure aboneliğinizi seçin.

   - **Kaynak grubu:** Yeni bir kaynak grubu seçin veya oluşturun. Kaynak grubu, Bir Azure çözümü için ilgili kaynakları barındıran bir kapsayıcıdır.

   - **Konum:** Bir konum seçin.

   - **Web Uygulaması Adı:** Bağlayıcı web uygulaması için benzersiz bir ad sağlayın. Adın uzunluğu 3 ile 18 karakter arasında olmalıdır. Bu ad, Azure app service URL'sini oluşturmak için kullanılır; örneğin, **fbconnector** web uygulaması adını sağlarsanız Azure uygulama hizmeti URL'si **fbconnector.azurewebsites.net**.

   - **tenantId:** 1. Adımda Azure Active Directory'da Facebook bağlayıcı uygulamasını oluşturduktan sonra kopyaladığınız Microsoft 365 kuruluşunuzun kiracı kimliği.

   - **APISecretKey:** Herhangi bir değeri gizli dizi olarak yazabilirsiniz. Bu, 5. Adımda bağlayıcı web uygulamasına erişmek için kullanılır.

     ![Kaynak oluştur'a tıklayın ve depolama hesabı yazın.](../media/FBCimage12.png)

3. Dağıtım başarılı olduktan sonra sayfa aşağıdaki ekran görüntüsüne benzer:

   ![Depolama'a tıklayın ve ardından Depolama hesabına tıklayın.](../media/FBCimage13.png)

## <a name="step-3-register-the-facebook-app"></a>3. Adım: Facebook uygulamasını kaydetme

1. adresine <https://developers.facebook.com>gidin, kuruluşunuzun Facebook business sayfalarının hesabının kimlik bilgilerini kullanarak oturum açın ve **ardından Yeni Uygulama Ekle'ye** tıklayın.

   ![Facebook işletme sayfası için yeni bir uygulama ekleyin.](../media/FBCimage25.png)

2. Yeni bir uygulama kimliği oluşturun.

   ![Yeni bir uygulama kimliği oluşturun.](../media/FBCimage26.png)

3. Sol gezinti bölmesinde **Ürün Ekle'ye** ve ardından **Facebook Oturum Açma** kutucuğunda **Ayarla'ya** tıklayın.

   ![Ürün Ekle'ye tıklayın.](../media/FBCimage27.png)

4. Facebook Oturum Açma Bilgilerini Tümleştir sayfasında **Web'e** tıklayın.

   ![Facebook Oturum Açma Bilgilerini Tümleştir sayfasında Web'e tıklayın.](../media/FBCimage28.png)

5. Azure app service URL'sini ekleyin; örneğin `https://fbconnector.azurewebsites.net`, .

   ![Azure app service URL'sini ekleyin.](../media/FBCimage29.png)

6. Facebook Oturum Açma kurulumunun Hızlı Başlangıç bölümünü tamamlayın.

   ![Hızlı Başlangıç bölümünü tamamlayın.](../media/FBCimage30.png)

7. **Facebook Oturum Açma'nın** altındaki sol gezinti bölmesinde **Ayarlar'e** tıklayın ve **Geçerli OAuth Yeniden Yönlendirme URI'leri kutusuna OAuth yeniden yönlendirme** URI'sini ekleyin. **/Views/FacebookOAuth biçimini\<connectorserviceuri>** kullanın; burada connectorserviceuri değeri kuruluşunuzun Azure uygulama hizmeti URL'sidir; örneğin, `https://fbconnector.azurewebsites.net`.

   ![OAuth yeniden yönlendirme URI'sini Geçerli OAuth Yeniden Yönlendirme URI'leri kutusuna ekleyin.](../media/FBCimage31.png)

8. Sol gezinti bölmesinde **Ürün Ekle'ye** ve ardından **Web Kancaları'na tıklayın.** **Sayfa** açılır menüsünde **Sayfa'ya** tıklayın.

   ![Ürün Ekle'ye ve ardından **Web Kancaları'ne tıklayın.](../media/FBCimage32.png)

9. Web Kancaları Geri Arama URL'si ekleyin ve doğrulama belirteci ekleyin. Geri çağırma URL'sinin biçimi biçimini kullanır `<connectorserviceuri>/api/FbPageWebhook`; burada connectorserviceuri değeri kuruluşunuzun Azure uygulama hizmeti URL'sidir; örneğin `https://fbconnector.azurewebsites.net`.

   Doğrulama belirteci güçlü bir parolaya benzer olmalıdır. Doğrulama belirtecini bir metin dosyasına veya başka bir depolama konumuna kopyalayın.

   ![Doğrulama belirtecini ekleyin.](../media/FBCimage33.png)

10. Akış için uç noktayı test edin ve abone olun.

    ![Uç noktayı test edin ve abone olun.](../media/FBCimage34.png)

11. Gizlilik URL'si, uygulama simgesi ve iş kullanımı ekleyin. Ayrıca, uygulama kimliğini ve uygulama gizli dizisini bir metin dosyasına veya başka bir depolama konumuna kopyalayın.

    ![Gizlilik URL'si, uygulama simgesi ve iş kullanımı ekleyin.](../media/FBCimage35.png)

12. Uygulamayı herkese açık hale getirin.

    ![Uygulamayı herkese açık hale getirin.](../media/FBCimage36.png)

13. Yönetici veya test eden rolüne kullanıcı ekleyin.

    ![Yönetici veya test eden rolüne kullanıcı ekleyin.](../media/FBCimage37.png)

14. **Sayfa Genel İçerik Erişimi** iznini ekleyin.

    ![Sayfa Genel İçerik Erişimi iznini dd.](../media/FBCimage38.png)

15. Sayfaları Yönet izni ekleyin.

    ![Sayfaları Yönet izni ekleyin.](../media/FBCimage39.png)

16. Uygulamayı Facebook tarafından gözden geçirmesini sağlayın.

    ![Uygulamayı Facebook tarafından gözden geçirmesini sağlayın.](../media/FBCimage40.png)

## <a name="step-4-configure-the-connector-web-app"></a>4. Adım: Bağlayıcı web uygulamasını yapılandırma

1. `https://<AzureAppResourceName>.azurewebsites.net` adresine gidin (burada AzureAppResourceName, 4. Adımda adlandırdığınız Azure uygulama kaynağınızın adıdır). Örneğin, ad **fbconnector** ise adresine gidin `https://fbconnector.azurewebsites.net`. Uygulamanın giriş sayfası aşağıdaki ekran görüntüsüne benzer:

   ![Bağlayıcı web uygulamanıza gidin.](../media/FBCimage41.png)

2. Oturum açma sayfasını görüntülemek için **Yapılandır'a** tıklayın.

   ![Oturum açma sayfasını görüntülemek için Yapılandır'a tıklayın.](../media/FBCimage42.png)

3. Kiracı Kimliği kutusuna kiracı kimliğinizi (2. Adımda edindiğiniz) yazın veya yapıştırın. Parola kutusuna APISecretKey (2. Adımda edindiğiniz) yazın veya yapıştırın ve yapılandırma ayrıntıları sayfasını görüntülemek için **Yapılandırma Ayarlar Ayarla'ya** tıklayın.

    ![Kiracı kimliğinizi ve parolanızı kullanarak oturum açın ve yapılandırma ayrıntıları sayfasına gidin.](../media/FBCimage43.png)

4. Aşağıdaki yapılandırma ayarlarını girin

   - **Facebook uygulama kimliği:** 3. Adımda aldığınız Facebook uygulamasının uygulama kimliği.

   - **Facebook uygulama gizli dizisi:** 3. Adımda edindiğiniz Facebook uygulaması için uygulama gizli dizisi.

   - **Facebook web kancaları doğrulama belirteci:** 3. Adımda oluşturduğunuz doğrulama belirteci.

   - **AAD uygulama kimliği:** 1. Adımda oluşturduğunuz Azure Active Directory uygulamasının uygulama kimliği.

   - **AAD uygulama gizli dizisi:** 1. Adımda oluşturduğunuz APISecretKey gizli dizisinin değeri.

5. Bağlayıcı ayarlarını kaydetmek için **Kaydet'e** tıklayın.

## <a name="step-5-set-up-a-facebook-connector-in-the-compliance-portal"></a>5. Adım: Uyumluluk portalında Facebook bağlayıcısı ayarlama

1. Microsoft Purview uyumluluk portalına gidin ve /a<**Veri bağlayıcıları'nı** seçin<a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">.

2. **Facebook İş sayfalarının** altındaki **Veri bağlayıcıları** sayfasında **Görüntüle'ye** tıklayın.

3. **Facebook iş sayfaları** sayfasında **Bağlayıcı ekle'ye** tıklayın.

4. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

5. **Bağlayıcı uygulamanız için kimlik bilgileri ekle** sayfasında aşağıdaki bilgileri girin ve Bağlantıyı **doğrula'ya** tıklayın.

   ![Bağlayıcı uygulaması kimlik bilgilerini girin.](../media/TCimage38.png)

   - **Ad** kutusuna bağlayıcı için **Facebook haber sayfası** gibi bir ad yazın.

   - **Bağlantı URL'si** kutusuna Azure app service URL'sini yazın veya yapıştırın; örneğin`https://fbconnector.azurewebsites.net`, .

   - **Parola** kutusuna, 2. Adımda eklediğiniz APISecretKey değerini yazın veya yapıştırın.

   - **Azure Uygulaması Kimliği** kutusuna, 1. Adımda oluşturduğunuz uygulama kimliği AAD olarak da adlandırılan Uygulama (istemci) kimliğinin değerini yazın veya yapıştırın.

6. Bağlantı başarıyla doğrulandıktan sonra **İleri'ye** tıklayın.

7. **Verileri içeri aktarmak için Microsoft 365 yetki ver** sayfasında APISecretKey'i yeniden yazın veya yapıştırın ve ardından **Oturum aç web uygulaması'na** tıklayın.

8. **Facebook bağlayıcısı uygulamasını yapılandır** sayfasında **Facebook ile oturum aç'a** tıklayın ve kuruluşunuzun Facebook İş sayfalarının hesabının kimlik bilgilerini kullanarak oturum açın. Oturum açtığınız Facebook hesabına kuruluşunuzun Facebook İş sayfaları için yönetici rolü atandığından emin olun.

   ![Facebook ile oturum açın.](../media/FBCimage50.png)

9. Oturum açtığınız Facebook hesabı tarafından yönetilen iş sayfalarının listesi görüntülenir. Arşive eklenecek sayfayı seçin ve **İleri'ye** tıklayın.

   ![Arşivlemesini istediğiniz kuruluş iş sayfasını seçin.](../media/FBCimage52.png)

10. Bağlayıcı hizmeti uygulamasının kurulumundan çıkmak için **Devam'a** tıklayın.

11. **Filtreleri ayarla** sayfasında, başlangıçta belirli bir yaştaki öğeleri içeri aktarmak için bir filtre uygulayabilirsiniz. Bir yaş seçin ve **İleri'ye** tıklayın.

12. **Depolama konumu seçin** sayfasında, Facebook öğelerinin içeri aktarılacağı Microsoft 365 posta kutusunun e-posta adresini yazın ve **İleri'ye** tıklayın.

13. Bağlayıcı ayarlarını gözden geçirmek için **İleri'ye** tıklayın ve ardından bağlayıcı kurulumunu tamamlamak için **Son'a** tıklayın.

14. Uyumluluk merkezinde **Veri bağlayıcıları** sayfasına gidin ve içeri aktarma işleminin ilerleme durumunu görmek için **Bağlayıcılar** sekmesine tıklayın.
