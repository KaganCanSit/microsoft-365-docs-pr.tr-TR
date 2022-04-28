---
title: Azure AD Kimlik Doğrulama Belirteci ile Microsoft 365 destek tümleştirmesi yapılandırma
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
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: ServiceNow için Kapsamlı Sertifikalı uygulama yükleme ve yapılandırma kılavuzu.
ms.openlocfilehash: d3991355779228cf1562e23ddd0e97cb37225a43
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093756"
---
# <a name="configure-microsoft-365-support-integration-with-azure-ad-auth-token"></a>Azure AD Kimlik Doğrulama Belirteci ile Microsoft 365 destek tümleştirmesi yapılandırma

## <a name="prerequisites-azure-ad-auth-token"></a>Önkoşullar (Azure AD Kimlik Doğrulama Belirteci)

Bu önkoşullar, Microsoft 365 destek tümleştirmesini ayarlamak için gereklidir.

1. \[AAD Yöneticisi\] Microsoft 365 kiracınızın altında Giden için Azure AD Uygulaması oluşturun.

    1. Microsoft 365 kiracı kimlik bilgilerinizle Azure Portal'da oturum açın ve yeni bir uygulama oluşturmak için [Uygulama kayıtları sayfasına](https://portal.azure.com/?Microsoft_AAD_RegisteredApps=true#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) gidin.

    2. **Yalnızca bu kuruluş dizinindeki Hesaplar 'ı seçin ({Microsoft-365-tenant-name} yalnızca – Tek kiracı)** ve **Kaydet'i** seçin.

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image3.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image3.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturuldu":::

1. **Kimlik doğrulaması'na** gidin ve **Platform ekle'yi** seçin. **Web** seçeneğini belirleyin ve yeniden yönlendirme URL'sini girin:`https://{your-servicenow-instance``}.service-now.com/oauth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image4.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image4.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturuldu":::

1. Uygulama İstemcisi Kimliğini alın ve bir İstemci gizli dizisi oluşturun ve bu değeri alın.

1. \[AAD Yöneticisi\] Microsoft 365 kiracınızın altında Rest API için Azure AD Uygulaması oluşturun.

    1. Microsoft 365 kiracı kimlik bilgilerinizle [Azure Portalı'nda](https://portal.azure.com/) oturum açın ve yeni bir uygulama oluşturmak için Uygulama kayıtları sayfasına gidin.

    1. **Yalnızca {(Microsoft-365-tenant-name} yalnızca – Tek kiracı) kuruluş dizinindeki Hesaplar'ı** seçin.

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image22.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image22.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturuldu":::

1. Uygulama İstemcisi Kimliğini alın ve bir İstemci gizli dizisi oluşturun ve bu değeri alın.

1. \[AAD Yöneticisi\] Microsoft 365 kiracınızın altında Rest User için bir Azure AD Uygulaması oluşturun.

    1. Microsoft 365 kiracı kimlik bilgilerinizle [Azure Portalı'nda](https://portal.azure.com/) oturum açın ve yeni bir uygulama oluşturmak için Uygulama kayıtları sayfasına gidin.

    1. **Yalnızca {(Microsoft-365-tenant-name} yalnızca – Tek kiracı) kuruluş dizinindeki Hesaplar'ı** seçin.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" lightbox="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturuldu":::

1. Uygulama İstemcisi Kimliğini alın ve bir İstemci gizli dizisi oluşturun ve bu değeri alın.

1. \[ServiceNow Yöneticisi\] ServiceNow'da Giden OAuth Sağlayıcısını ayarlayın.

    Kapsam **Genel** olarak ayarlanmadıysa, Ayarlar **Geliştirici &gt; Uygulamaları'na gidip Genel'e &gt;** geçerek bunu yapın.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, sohbet veya kısa mesaj Açıklama otomatik olarak oluşturuldu":::

1. **Sistem OAuth &gt; Uygulama Kayıt Defteri'ne** gidin.

1. **Üçüncü taraf OAuth Sağlayıcısına Bağlan** seçeneğini kullanarak ve şu değerleri girerek yeni bir uygulama oluşturun:

    - İstemci Kimliği: Bu, Önkoşullar (Azure AD Kimlik Doğrulama Belirteci) 1. adımda \#oluşturulan uygulamanın İstemci Kimliğidir.

    - İstemci Gizli Anahtarı: Bu, Önkoşullar (Azure AD Kimlik Doğrulama Belirteci) 1. adımda \#oluşturulan uygulamanın İstemci Gizli Anahtarı değeridir.

    - Varsayılan Verme türü: İstemci Kimlik Bilgileri

    - Belirteç URL'si: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/oauth2/token`

    - Yeniden yönlendirme URL'si: `https://{service-now-instance-name``}.service-now.com/oauth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image6.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image6.png" alt-text="Grafik kullanıcı arabirimi, uygulama açıklaması otomatik olarak oluşturuldu":::

1. \[ServiceNow Yöneticisi\] ServiceNow'da OIDC sağlayıcısını yapılandırmak için [çevrimiçi belgelere bakın](https://docs.servicenow.com/bundle/quebec-platform-administration/page/administer/security/task/add-OIDC-entity.html).

    Kapsam **Genel** olarak ayarlanmadıysa Geliştirici **Uygulamaları'nı Ayarlar &gt; &gt;** gidin ve **Genel'e** geçin.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, sohbet veya kısa mesaj Açıklama otomatik olarak oluşturuldu":::

1. **Sistem OAuth &gt; Uygulama Kayıt Defteri'ne** gidin.

1. **Yeni'yi** ve ardından **Yeni Açık Kimlik Bağlan Sağlayıcı oluştur'u** seçin.

1. **OAuth OIDC Sağlayıcısı Yapılandırması'nda** **Ara'yı** seçin ve **oidcproviderconfiguration.list\_\_** altında şu değerlerle yeni bir OIDC sağlayıcı yapılandırması oluşturun:

    - OIDC Sağlayıcısı: **{TenantName\_} Azure** (örnek: Contoso Azure)

    - OIDC Meta Veri URL'si: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/.well-known/openid-configuration`

    - UserClaim: **appid**

    - UserField: **Kullanıcı Kimliği**

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image24.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image24.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama Açıklaması otomatik olarak oluşturuldu":::

1. **Kimlik belirteçlerini şu değerlerle doğrulamak için OIDC sağlayıcısı yapılandır'ı** seçerek yeni bir uygulama oluşturun:

    - Ad: **{TenantName\_}\_applicationinboundapi\_\_** (örnek: contosoapplicationinboundapi\_\_\_)

    - İstemci Kimliği: Önkoşullar (Azure AD Kimlik Doğrulama Belirteci) 3. adımda \#oluşturulan uygulamanın İstemci Kimliği.

    - İstemci Gizli Anahtarı: Önkoşullar (Azure AD Kimlik Doğrulama Belirteci) 3. adımda \#oluşturulan uygulamanın Uygulama Gizli Anahtarı.

    - OAuth OIDC Sağlayıcısı Yapılandırması: Önceki adımda oluşturulan OIDC sağlayıcısı

    - Yeniden yönlendirme URL'si: `https://{service-now-instance-name}.service-now.com/oauth\_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image25.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image25.png" alt-text="Grafik kullanıcı arabirimi, uygulama açıklaması otomatik olarak oluşturuldu":::

1. \[ServiceNow Yöneticisi\] Tümleştirme Kullanıcıları Oluşturun.

    Bir tümleştirme kullanıcısı belirtmeniz gerekir. Mevcut bir tümleştirme kullanıcınız yoksa veya bu tümleştirme için özel olarak bir tümleştirme oluşturmak istiyorsanız Kuruluş **Kullanıcıları'na &gt;** giderek yeni bir kullanıcı oluşturun. **Kullanıcı Kimliği** değeri [, Önkoşullar (Azure AD Kimlik Doğrulama Belirteci)](#prerequisites-azure-ad-auth-token) içinde oluşturulan uygulama İstemci Kimliği'dir.

    Yeni bir tümleştirme kullanıcısı oluşturuyorsanız **Yalnızca Web hizmeti erişimi** seçeneğini işaretleyin. Ayrıca bu kullanıcıya **incidentmanager\_** rolünü de vermelisiniz.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image26.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image26.png" alt-text="Grafik kullanıcı arabirimi, uygulama açıklaması otomatik olarak oluşturuldu":::

## <a name="optional-allow-the-services-ip-addresses-to-microsoft-365-support-integration"></a>\[İsteğE BAĞLI\] Hizmetin IP adreslerinin destek tümleştirmesini Microsoft 365 izin ver

Şirketiniz İnternet erişimini kendi ilkelerinizle sınırlandırıyorsa, hem gelen hem de giden API erişimi için aşağıdaki IP adreslerine izin vererek Microsoft 365 destek tümleştirmesi hizmeti için ağ erişimini etkinleştirin.

- 52.149.152.32

- 40.83.232.243

- 40.83.114.39

- 13.76.138.31

- 13.79.229.170

- 20.105.151.142

> [!NOTE]
> Bu terminal komutu, Microsoft 365 destek tümleştirmesi için hizmetin tüm etkin IP'lerini listeler:`nslookup`` connector.rave.microsoft.com`

## <a name="configure-the-microsoft-365-support-integration-application"></a>Microsoft 365 desteği tümleştirme Uygulamasını yapılandırma

Microsoft 365 destek tümleştirme uygulaması Microsoft 365 desteği altında ayarlanabilir.

ServiceNow örneğin ve Microsoft 365 desteği arasındaki tümleştirmeyi ayarlamak için bu adımlar gereklidir.

1. \[ServiceNow Yöneticisi\] Kapsamı **destek tümleştirmesi Microsoft 365** olarak değiştirin.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image9.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image9.png" alt-text="Grafik kullanıcı arabirimi, tablo Açıklaması otomatik olarak oluşturuldu":::

1. \[ServiceNow Yöneticisi\] Tümleştirme iş akışını açmak için **Microsoft 365 Destek &gt; Kurulumu'na** gidin.

    > [!NOTE]
    > "Tablonun kapsamlar arası erişim ilkesi nedeniyle 'xmiomsm365assis\_\_\_' kapsamındaki 'oauthentity'ye\_ karşı okuma işlemi reddedildi" hatasını görürseniz, bunun nedeni tablo erişim ilkenizdir. Tablo kimlik doğrulaması\_ için **Tüm uygulama kapsamları &gt; Okunabilir'in** işaretli olduğundan emin olmanız gerekir.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image27.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image27.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturuldu":::

1. \[ServiceNow Yöneticisi\] Devam etmek için onay istemini **kabul et'i** seçin.

    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-1.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-1.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturuldu":::

1. \[ServiceNow Yöneticisi\] Ortamı ve kurulum türünü yapılandırın.
    Bu yükleme bir test ortamındaysa Bu bir test ortamıdır seçeneğini belirleyin. Kurulumdan sonra ve tüm testleriniz daha sonra tamamlandıktan sonra bu seçeneği hızla devre dışı bırakabileceksiniz.
    Örneğiniz gelen bağlantılar için Temel Kimlik Doğrulaması'na izin veriyorsa Evet'i seçin ve [Temel Kimlik Doğrulaması kurulum işlemine](servicenow-basic-authentication.md) bakın. Aksi takdirde **Hayır'ı** seçin ve **Kurulumu başlat'a** tıklayın. 
      :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-2.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-2.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturuldu":::

1. \[ServiceNow Yöneticisi\] Microsoft 365 kiracı etki alanınızı girin.
     :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-3.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-3.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturuldu":::

1. \[ServiceNow Yöneticisi\] Giden OAuth sağlayıcısını yapılandırın.
    1. Giden OAuth sağlayıcısını yapılandırın.
    1. Önkoşullar bölümündeki yönergeleri tamamladıktan sonra Bitti'ye tıklayın. Aksi takdirde, AAD gerekli uygulama kaydını oluşturmak için sihirbazdaki yönergeleri izleyin.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-4.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-4.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturuldu":::
    1. ServiceNow OAuth Uygulamasını kaydedin.
    1. Önkoşullar bölümündeki yönergeleri tamamladıktan sonra, yeni oluşturulan OAuth uygulama kaydını seçin ve İleri'ye tıklayın. Aksi takdirde, ServiceNow'da varlığı oluşturmak için yönergeleri izleyin ve ardından yeni uygulama kaydını seçin.
     :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-5.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-5.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturuldu":::

1. \[ServiceNow Yöneticisi\] Gelen ayarlarını yapılandırın.
    1. Gelen AAD Uygulamasını yapılandırın.
    1. Önkoşullar bölümündeki yönergeleri tamamladıktan sonra, sonraki adıma geçmek için Bitti'ye tıklayın. Aksi takdirde, gelen bağlantı için AAD Uygulama Kaydı oluşturmak için yönergeleri izleyin.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-6.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-6.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturuldu":::
    1. ServiceNow Dış OpenID Bağlan Sağlayıcısını (OIDC Sağlayıcısı) yapılandırın.
    1. Önkoşullar bölümündeki yönergeleri tamamladıktan sonra yeni oluşturulan varlığı seçin ve Bitti'ye tıklayın. Aksi takdirde, ServiceNow'da varlığı oluşturmak için yönergeleri izleyin ve ardından yeni Dış OIDC Sağlayıcısı uygulama kaydını seçin.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-7.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-7.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturuldu":::
    1. Gelen Tümleştirme Kullanıcısı için AAD Uygulama Kaydını yapılandırın.
    1. Önkoşullar bölümündeki yönergeleri tamamladıktan sonra, sonraki adıma geçmek için Bitti'ye tıklayın. Aksi takdirde, yönergeleri izleyerek gelen REST kullanıcısı (tümleştirme kullanıcısı) için AAD Uygulama Kaydı oluşturun.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-8.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-8.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturuldu":::
    1. Tümleştirme Kullanıcısını yapılandırın.
    1. Önkoşullar bölümündeki yönergeleri tamamladıktan sonra yeni oluşturulan varlığı seçin ve İleri'ye tıklayın. Aksi takdirde ServiceNow'da tümleştirme kullanıcısı oluşturmak için yönergeleri izleyin ve varlığı seçin.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-9.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-9.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturuldu":::

1. \[kiracı yöneticisini\] Microsoft 365 Tümleştirmeyi tamamlayın.

    Aşağıdaki bilgilerin doğru olduğunu doğrulayın. Şu anda **İleri'yi** SEÇMEYİN.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image40.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image40.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturuldu":::

    1. **Microsoft 365 Yönetici Portal &gt; Ayarlar &gt; Kuruluş ayarları &gt; Kuruluş profilleri'ne** gidin.

    1. Destek tümleştirme ayarlarını yapılandırın:

    **İç destek** **aracıServiceNow** >  > **Temel bilgiler** sekmesini seçin ve **Kimlik Doğrulama Belirteci vermek için Uygulama Kimliği** alanına **Giden Uygulama** Kimliği değerini girin. Bu Giden Uygulama Kimliği, [Önkoşullar (Azure AD Kimlik Doğrulama Belirteci)](#prerequisites-azure-ad-auth-token) içinde oluşturulan 6. Adım – Tümleştirmeyi Tamamlama'dadır.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image18.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image18.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturuldu":::

    1. **Depolar** sekmesinde **Yeni depo'yu** seçin ve aşağıdaki ayarlarla güncelleştirin:

    - Depo: "6. Adım – Tümleştirmeyi Tamamlama" bölümünde yer alan **Depo Kimliği** değeri.

    - Uç Nokta: "6. Adım – Tümleştirmeyi Tamamlama" adlı **uç nokta** değeri.

    - Kimlik doğrulama türü: **kimlik doğrulaması AAD** seçin.

    - İstemci Kimliği: 6. Adım – Tümleştirmeyi Tamamla'dan **İstemci Kimliği** değeri.

    - İstemci gizli anahtarı: Önkoşullar (Azure AD Kimlik Doğrulama Belirteci) 2. adımda oluşturulan gelen OAuth sağlayıcısının gizli dizisi \#.

    - Rest kullanıcı adı: 6. Adım – Tümleştirmeyi Tamamla'daki **Kullanıcı Adı** değeri, Önkoşullar (Azure AD Kimlik Doğrulama Belirteci) 3. adımda \#oluşturulan uygulamanın **İstemci Kimliğidir**.

    - Rest kullanıcı parolası: Önkoşullar (Azure AD Kimlik Doğrulama Belirteci) 3. adımda \#oluşturulan uygulamanın Uygulama Gizli Anahtarı.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image31.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image31.png" alt-text="Grafik kullanıcı arabirimi, uygulama açıklaması otomatik olarak oluşturuldu":::

    1. ServiceNow'a Geri dön.

    1. Tümleştirmeyi tamamlamak için **İleri'yi** seçin.

   :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-10.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-10.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturuldu":::
    Microsoft 365 destek tümleştirme uygulaması, tümleştirmenin çalıştığından emin olmak için testler yürütür. Yapılandırmayla ilgili bir sorun varsa, nelerin düzeltilmesi gerektiğini açıklayan bir hata iletisi görüntülenir. Aksi takdirde uygulama hazırdır.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-11.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-11.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturuldu":::

1. \[ServiceNow Yöneticisi\] Var olan bir kullanıcı için Microsoft destek tümleştirmesini etkinleştirin.

    Microsoft 365 destek tümleştirmesi şu rollerden birine sahip kullanıcı için etkinleştirilir:

    - xmiomsm365assis.insightsuser\_\_\_\_

    - xmiomsm365assis.administrator\_\_\_

1. \[İsteğE BAĞLI\] \[xmiomsm365assis.administrator\_\_\_ rolüne sahip kullanıcı Microsoft 365 yönetici hesabı bağlantısı\].

    Herhangi bir kullanıcı xmiomsm365assis.administrator\_\_\_ rolüne sahipse ve bir Microsoft 365 destek olayını yönetmek için farklı Microsoft 365 hesapları kullanıyorsa, Microsoft 365 yönetici e-postasını ayarlamak için Microsoft 365 destek &gt; Bağlantısı Hesabı'na gitmesi gerekir.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image21.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image21.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama Açıklaması otomatik olarak oluşturuldu":::
