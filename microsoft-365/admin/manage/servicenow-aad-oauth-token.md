---
title: Azure AD Microsoft 365 Belirteci ile destek tümleştirmesi yapılandırma
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
description: ServiceNow için Kapsam Sertifikalı uygulama yükleme ve yapılandırma kılavuzu.
ms.openlocfilehash: 9f9985e07989f168f9b27dde1c1d574813c3f349
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320907"
---
# <a name="configure-microsoft-365-support-integration-with-azure-ad-auth-token"></a>Azure AD Microsoft 365 Belirteci ile destek tümleştirmesi yapılandırma

## <a name="prerequisites-azure-ad-auth-token"></a>Önkoşullar (Azure AD Kimlik Doğrulaması Belirteci)

Destek tümleştirmesi için bu önkoşullar Microsoft 365 gereklidir.

1. \[AAD Yönetici\] Kendi kiracınız altında Giden için Azure AD Microsoft 365 oluşturun.

    1. Azure Portal'da oturum açmak için Microsoft 365 kimlik bilgilerinizle oturum açın ve [yeni bir uygulama oluşturmak için](https://portal.azure.com/?Microsoft_AAD_RegisteredApps=true#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) Uygulama kayıtları sayfasına gidin.

    2. Yalnızca **bu kuruluş dizininde Hesaplar'ı (yalnızca {Microsoft-365-tenant-name} – Tek kiracı)** ve Ardından Kaydol'u **seçin**.

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image3.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image3.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. Kimlik **Doğrulaması'na gidin** ve Platform **ekle'yi seçin**. Web seçeneğini **belirleyin** ve yeniden yönlendirme URL'sini girin: `https://{your-servicenow-instance``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image4.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image4.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. Uygulama İstemci Kimliği'ne tıklayın ve bir İstemci sırrı oluşturun ve bu değeri elde oluşturun.

1. \[AAD Yönetici\] Kiracınız altında Rest API'si için bir Azure AD Microsoft 365 oluşturun.

    1. Azure [Portal'da oturum](https://portal.azure.com/) açmak için Microsoft 365 kimlik bilgilerinizle oturum açın ve yeni bir uygulama oluşturmak için Uygulama kayıtları sayfasına gidin.

    1. Yalnızca **bu kuruluş dizininde hesaplar {(Microsoft-365-tenant-name} yalnızca – Tek kiracı)'ı seçin**.

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image22.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image22.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. Uygulama İstemci Kimliği'ne tıklayın ve bir İstemci sırrı oluşturun ve bu değeri elde oluşturun.

1. \[AAD Yönetici\] Kullanıcı Kiracınız altında Rest User için bir Azure AD Microsoft 365 oluşturun.

    1. Azure [Portal'da oturum](https://portal.azure.com/) açmak için Microsoft 365 kimlik bilgilerinizle oturum açın ve yeni bir uygulama oluşturmak için Uygulama kayıtları sayfasına gidin.

    1. Yalnızca **bu kuruluş dizininde hesaplar {(Microsoft-365-tenant-name} yalnızca – Tek kiracı)'ı seçin**.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" lightbox="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. Uygulama İstemci Kimliği'ne tıklayın ve bir İstemci sırrı oluşturun ve bu değeri elde oluşturun.

1. \[ServiceNow Yöneticisi\] ServiceNow içinde Giden OAuth Sağlayıcısını ayarlayın.

    Kapsam Genel olarak ayarlanmazsa, **bunu** yapmak için **&gt; Geliştirici Uygulamaları'na Ayarlar Genel'e &gt;** **geçin**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, sohbet veya metin mesajı Açıklama otomatik olarak oluşturulur":::

1. **System OAuth Application Registry'ye &gt; gidin**.

1. Üçüncü taraf **OAuth Provider seçeneğine Bağlan kullanarak yeni** bir uygulama oluşturun ve şu değerleri girin:

    - İstemci Kimliği: Bu, Önkoşullar (Azure AD Kimlik Belirteci) adım 1'de oluşturulan uygulamanın İstemci \#Kimliği'dir.

    - İstemci Sırrı: Bu, Önkoşullar (Azure AD Kimlik Doğrulaması Belirteci) \#adım 1'de oluşturulan uygulamanın İstemci Sırrı değeridir.

    - Varsayılan Grant türü: İstemci Kimlik Bilgileri

    - Belirteç URL'si: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/oauth2/token`

    - Yeniden yönlendirme URL'si: `https://{service-now-instance-name``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image6.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image6.png" alt-text="Grafik kullanıcı arabirimi, uygulama açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow Yönetici\] ServiceNow'da OIDC sağlayıcısını yapılandırmak için çevrimiçi [belgelere bakın](https://docs.servicenow.com/bundle/quebec-platform-administration/page/administer/security/task/add-OIDC-entity.html).

    Kapsam Genel olarak ayarlanmazsa, **Geliştirici** Uygulamaları'Ayarlar **&gt; ve &gt; Genel'e** **geçin**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, sohbet veya metin mesajı Açıklama otomatik olarak oluşturulur":::

1. **System OAuth Application Registry'ye &gt; gidin**.

1. **Yeni'yi** seçin ve sonra **Sağlayıcı'da Yeni Açık Kimlik Bağlan seçin**.

1. **OAuth OIDC Sağlayıcısı Yapılandırması'nın** altında Ara'ya tıklayın ve şu değerlerle  **oidcproviderconfiguration.list\_\_** altında yeni bir OIDC sağlayıcısı yapılandırması oluşturun:

    - OIDC Sağlayıcısı: **{TenantName\_} Azure** (örnek: Contoso Azure)

    - OIDC Meta Veri URL'si: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/.well-known/openid-configuration`

    - UserClaim: **appid**

    - UserField: **Kullanıcı Kimliği**

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image24.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image24.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama Açıklaması otomatik olarak oluşturulur":::

1. Kimlik belirteçlerini şu değerlerle doğrulamak **için OIDC sağlayıcısını yapılandır'ı seçerek yeni** bir uygulama oluşturun:

    - Ad: **{TenantName\_}\_applicationinboundapi\_\_** (örnek: contosoapplicationinboundapi\_\_\_)

    - İstemci Kimliği: Önkoşullar (Azure AD Kimlik Belirteci) adım 2'de oluşturulan uygulamanın İstemci \#Kimliği.

    - İstemci Sırrı: Önkoşullar (Azure AD Kimlik Doğrulaması Belirteci) adım 2'de oluşturulan uygulamanın Uygulama \#Sırrı.

    - OAuth OIDC Sağlayıcısı Yapılandırması: Önceki adımda oluşturulan OIDC sağlayıcısı

    - Yeniden yönlendirme URL'si: `https://{service-now-instance-name}.service-now.com/oauth\_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image25.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image25.png" alt-text="Grafik kullanıcı arabirimi, uygulama açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow Yöneticisi Tümleştirme\] Kullanıcıları Oluşturun.

    Bir tümleştirme kullanıcısı belirtmeniz gerekir. Mevcut tümleştirme kullanıcınız yoksa veya bu tümleştirme için özel olarak bir kullanıcı oluşturmaksanız, **&gt;** Kuruluş Kullanıcıları'nın gidin ve yeni kullanıcı oluşturun. Kullanıcı Kimliğinin değeri **,** Önkoşullar'da [(Azure AD Kimlik](#prerequisites-azure-ad-auth-token) Belirteci) oluşturulmuş uygulama İstemci Kimliğidir.

    Yeni bir tümleştirme kullanıcısı oluşturuyorsanız, Yalnızca **Web hizmeti erişimi seçeneğini** işaretleyin. Bu kullanıcıya **olaymanager rolü de\_ verlisiniz** .

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image26.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image26.png" alt-text="Grafik kullanıcı arabirimi, uygulama açıklaması otomatik olarak oluşturulur":::

## <a name="optional-allow-the-services-ip-addresses-to-microsoft-365-support-integration"></a>\[İsteğE\] BAĞLı Hizmetin IP adreslerinin destek tümleştirmesini Microsoft 365 izin ver

Şirketiniz kendi ilkeleriniz ile İnternet erişimini sınırlandırıyorsa, hem gelen hem de giden API erişimi için aşağıdaki IP adreslerine izin vererek, Microsoft 365 desteği tümleştirme hizmeti için ağ erişimini etkinleştirin.

- 52.149.152.32

- 40.83.232.243

- 40.83.114.39

- 13.76.138.31

- 13.79.229.170

- 20.105.151.142

> [!NOTE]
> Bu terminal komutu, destek tümleştirmesi için hizmetin tüm etkin MICROSOFT 365 listeler:`nslookup`` connector.rave.microsoft.com`

## <a name="configure-the-microsoft-365-support-integration-application"></a>Microsoft 365 desteği tümleştirme uygulamasını yapılandırma

Microsoft 365 desteği tümleştirme uygulaması, Destek Hizmetleri altında Microsoft 365 ayarlanır.

Bu adımlar, ServiceNow örneğiniz ve destek hizmetleriniz arasında tümleştirmeyi Microsoft 365 gerekir.

1. \[ServiceNow Yönetici\] Desteği tümleştirmeyi destekleme **Microsoft 365 kapsamını değiştirme**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image9.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image9.png" alt-text="Grafik kullanıcı arabirimi, tablo Açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow Yönetici\] Tümleştirme iş **Microsoft 365 için Destek &gt; Kurulumu'ne** gidin.

    > [!NOTE]
    > 'xmiomsm365assis\_\_\_' kapsamından "'oauthentity\_' hatasına karşı okuma işlemi tablonun çapraz kapsam erişim ilkesinden dolayı reddedildi" hatasını görüyorsanız, bunun nedeni tablo erişim ilkenizdir. Tablo kimlik doğrulaması **için Tüm uygulama kapsamları &gt; Okunabilir'in** işaretli olduğundan emin\_ olun.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image27.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image27.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow Admin Select\] **Agree** to the consent prompt to continue.

    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-1.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-1.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow Yönetici\] Ortamı ve kurulum türünü yapılandır.
    Bu yükleme bir test ortamında ise, Bu bir test ortamıdır seçeneğini belirtin. Kurulum ve tüm testlerinizi daha sonra tamamlandıktan sonra bu seçeneği hızla devre dışı abileceksiniz.
    Örneğiniz gelen bağlantılarda Temel Kimlik Doğrulamasına izin verdiyse, Evet'i seçin ve [Temel Kimlik Doğrulaması kurulum sürecine bakın](servicenow-basic-authentication.md). Aksi takdirde **Hayır'ı seçin** ve Kurulumu **başlat'a tıklayın**. 
      :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-2.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-2.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow YöneticiDiyata\] kiracı Microsoft 365 etkinızı girin.
     :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-3.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-3.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow Admin\] Configure Outbound OAuth sağlayıcısı.
    1. Giden OAuth sağlayıcısını yapılandırma.
    1. Önkoşullar bölümündeki yönergeleri tamamladıktan sonra Bitti'ye tıklayın. Aksi takdirde, sihirbazda gerekli uygulama kaydını oluşturmak için sihirbazda verilen AAD.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-4.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-4.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::
    1. ServiceNow OAuth Uygulamasını kaydettirin.
    1. Önkoşullar bölümündeki yönergeleri tamamladıktan sonra, yeni oluşturulan OAuth uygulaması kaydını seçin ve Sonraki'ye tıklayın. Aksi takdirde, ServiceNow'da varlık oluşturmak için yönergeleri izleyin ve ardından yeni uygulama kaydını seçin.
     :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-5.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-5.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow Yönetici\] Gelen ayarlarını yapılandır.
    1. Gelen Posta Uygulaması'AAD yapılandırma.
    1. Önkoşullar bölümündeki yönergeleri tamamladıktan sonra, bir sonraki adıma gitmek için Bitti'ye tıklayın. Aksi takdirde, gelen bağlantısı için AAD Kaydı oluşturmak için yönergeleri izleyin.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-6.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-6.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::
    1. ServiceNow External OpenID veya Bağlan Sağlayıcısı'nın (OIDC Sağlayıcısı) yapılandırma.
    1. Önkoşullar bölümündeki yönergeleri tamamladıktan sonra, yeni oluşturulan varlığı seçin ve Bitti'ye tıklayın. Aksi takdirde, ServiceNow'da varlık oluşturmak için yönergeleri izleyin ve ardından yeni Dış OIDC Sağlayıcısı uygulama kaydını seçin.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-7.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-7.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::
    1. Gelen Tümleştirme AAD için Uygulama Kaydı'nın ayarlarını yapılandırma.
    1. Önkoşullar bölümündeki yönergeleri tamamladıktan sonra, bir sonraki adıma gitmek için Bitti'ye tıklayın. Aksi takdirde, gelen REST kullanıcısı için AAD Kaydı (tümleştirme kullanıcısı) oluşturmak üzere yönergeleri izleyin.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-8.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-8.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::
    1. Tümleştirme Kullanıcısı'nın ayarlarını yapılandırma.
    1. Önkoşullar bölümündeki yönergeleri tamamladıktan sonra, yeni oluşturulan varlığı seçin ve Sonraki'ye tıklayın. Aksi takdirde, ServiceNow ile tümleştirme kullanıcısı oluşturmak için yönergeleri izleyin ve ardından varlığı seçin.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-9.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-9.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. \[Microsoft 365 Kiracı Yöneticisi\] Tümleştirmeyi tamamlama.

    Aşağıdaki bilgilerin doğru olduğunu doğrulayın. Şu anda **Sonraki'yi** SEÇMEYİN.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image40.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image40.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

    1. Kuruluş ayarları **Microsoft 365 Yönetici Portal &gt; Ayarlar &gt; Kuruluş profilleri'ne &gt; gidin**.

    1. Destek tümleştirme ayarlarını yapılandırma:

    Temel bilgiler **sekmesini seçin** > **İç** >  destek **aracıServiceNow'ı** seçin ve Kimlik Doğrulaması Belirteci'ne sorun için Uygulama **Kimliği'ne Giden Uygulama Kimliği değerini** girin. Bu Giden Uygulama Kimliği, 6. Adımdadır ; Önkoşullar'da (Azure AD Kimlik Doğrulaması Belirteci) oluşturulmuş [tümleştirmeyi tamamlama.](#prerequisites-azure-ad-auth-token)

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image18.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image18.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

    1. Depolar **sekmesinde** Yeni **depo'ya tıklayın** ve aşağıdaki ayarlarla güncelleştirin:

    - Depo: "6 **. Adım** – Tümleştirmeyi Tamamlama" değerinden gelen Depo Kimliği değeri.

    - Uç nokta **: "6** . Adım – Tümleştirmeyi Tamamlama" değerinden uç nokta değeri.

    - Kimlik doğrulama türü: Kimlik **AAD seçin**.

    - İstemci Kimliği: **6. Adımdan** itibaren İstemci Kimliği değeri – Tümleştirmeyi tamamlama.

    - İstemci sırrı: Önkoşullar (Azure AD Kimlik Doğrulaması Belirteci) adım 2'de oluşturulmuş gelen OAuth sağlayıcısının \#sırrı.

    - Rest kullanıcı adı:  6. Adımdan Itibaren Kullanıcı Adı değeri – Önkoşullar'da oluşturulan uygulamanın İstemci Kimliği (Azure AD Kimlik Belirteci)  \#adım 3'ü olan Tümleştirmeyi tamamlama.

    - Rest kullanıcı parolası: Önkoşullar (Azure AD Kimlik Doğrulaması Belirteci) adım 3'te oluşturulmuş olan uygulamanın Uygulama \#Sırrı.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image31.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image31.png" alt-text="Grafik kullanıcı arabirimi, uygulama açıklaması otomatik olarak oluşturulur":::

    1. ServiceNow'a geri dönme.

    1. **Tümleştirmeyi tamamlamak** için Sonraki'yi seçin.

   :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-10.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-10.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::
    En Microsoft 365 tümleştirme uygulaması, tümleştirmenin çalıştığını sağlamak için testler yürütür. Yapılandırmayla ilgili bir sorun varsa, neyin düzeltilecek şekilde olması gerektiğini bir hata iletisiyle açıklar. Aksi takdirde, uygulama hazır olur.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-11.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-11.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow Yönetici\] Var olan bir kullanıcı için Microsoft desteği tümleştirmesini etkinleştirin.

    Microsoft 365 rollerinden biri olan kullanıcı için destek tümleştirmesi etkinleştirilmiştir:

    - xmiomsm365assis.insightsuser\_\_\_\_

    - xmiomsm365assis.administrator\_\_\_

1. \[İsteğE\] \[BAĞLı Rol xmiomsm365assis.administrator\_\_\_ bağlantısı olan kullanıcı\] Microsoft 365 hesabıyla oturum açın.

    Herhangi bir kullanıcı xmiomsm365assis.administrator\_\_\_ rolüne sahipse ve bir Microsoft 365 destek vakasını yönetmek için farklı Microsoft 365 hesapları kullanıyorsa, Microsoft 365 yönetici e-postasını ayarlamak için Microsoft 365 &gt; destek Bağlantı Hesabı'Microsoft 365 gitmeleri gerekir.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image21.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image21.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama Açıklaması otomatik olarak oluşturulur":::
