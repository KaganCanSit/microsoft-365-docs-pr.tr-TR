---
title: ServiceNow ile destek tümleştirmeyi yapılandırma - Temel Kimlik Doğrulama
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
ms.openlocfilehash: 23fab410b17cea9635c63b0ed0e4225d158dfdc8
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323857"
---
# <a name="configure-support-integration-with-servicenow---basic-authentication"></a>ServiceNow ile destek tümleştirmeyi yapılandırma - Temel Kimlik Doğrulama

## <a name="prerequisites-basic-authentication"></a>Önkoşullar (Temel Kimlik Doğrulaması)

Destek tümleştirmesi için bu önkoşullar **Microsoft 365 gereklidir**.

1. \[AAD Yönetici\] Kiracınız altında Azure AD Microsoft 365 oluşturun.

    1. Azure Portal'da oturum açmak için Microsoft 365 kimlik bilgilerinizle oturum açın ve [yeni bir uygulama oluşturmak için](https://portal.azure.com/?Microsoft_AAD_RegisteredApps=true#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) Uygulama kayıtları sayfasına gidin.

    1. Yalnızca **bu kuruluş dizininde Hesaplar'ı (yalnızca {Microsoft-365-tenant-name} – Tek kiracı)** ve Ardından Kaydol'u **seçin**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image3.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image3.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. Kimlik **Doğrulaması'na gidin** ve Platform **ekle'yi seçin**. Web seçeneğini **belirleyin** ve yeniden yönlendirme URL'sini girin: `https://{your-servicenow-instance``}.service-now.com/oauth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image4.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image4.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. Uygulama İstemci Kimliği'ne tıklayın ve bir İstemci sırrı oluşturun ve bu değeri elde oluşturun.

1. \[ServiceNow Yöneticisi\] ServiceNow içinde Giden OAuth Sağlayıcısını ayarlayın.

    Kapsam Genel olarak ayarlanmazsa, **Geliştirici** Uygulamaları'Ayarlar **&gt; ve &gt; Genel'e** **geçin**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, sohbet veya metin mesajı Açıklama otomatik olarak oluşturulur":::

1. **System OAuth Application Registry'ye &gt; gidin**.

1. Üçüncü taraf **OAuth Provider seçeneğine Bağlan kullanarak ve** şu değerleri girerek yeni uygulama oluşturun:

    - İstemci Kimliği: Bu, 1. adımda oluşturulan uygulamanın İstemci \#Kimliği'dir.

    - İstemci Sırrı: Bu, 1. adımda oluşturulan uygulamanın İstemci Sırrı \#değeridir.

    - Varsayılan Grant türü: İstemci Kimlik Bilgileri

    - Belirteç URL'si: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/oauth2/token`

    - Yeniden yönlendirme URL'si: `https://{service-now-instance-name``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image6.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image6.png" alt-text="Grafik kullanıcı arabirimi, uygulama açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow Admin\] Set up the Gelen OAuth Provider.

    Kapsam Genel olarak ayarlanmazsa, **bunu** Yapmak için Geliştirici Uygulamaları'Ayarlar'e **&gt; &gt;** geçin ve Genel'e **geçin**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, sohbet veya metin mesajı Açıklama otomatik olarak oluşturulur":::

1. **System OAuth Application Registry'ye &gt; gidin**.

1. Dış istemciler için **OAuth API uç noktası oluştur seçeneğini kullanarak yeni uygulama** oluşturun. Gelen OAuth sağlayıcısını bir adla yazın ve diğer tüm alanları varsayılan değerlerinde bırakın.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image7.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image7.png" alt-text="Grafik kullanıcı arabirimi, uygulama açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow Yöneticisi\] Tümleştirme kullanıcısı oluşturun.

    Bir tümleştirme kullanıcısı belirtmeniz gerekir. Mevcut tümleştirme kullanıcınız yoksa veya bu tümleştirme için özel olarak bir kullanıcı oluşturmaksanız, **&gt;** Kuruluş Kullanıcıları'nın gidin ve yeni kullanıcı oluşturun.

    Yeni bir tümleştirme kullanıcısı oluşturuyorsanız, Yalnızca **Web hizmeti erişimi seçeneğini** işaretleyin. Bu kullanıcıya **olaymanager rolü de\_ verlisiniz** .

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image8.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image8.png" alt-text="Grafik kullanıcı arabirimi, uygulama açıklaması otomatik olarak oluşturulur":::

## <a name="optional-allow-the-services-ip-addresses-to-microsoft-365-support-integration"></a>\[İsteğE\] BAĞLı Hizmetin IP adreslerinin destek tümleştirmesini Microsoft 365 izin ver

Şirketiniz kendi ilkeleriniz ile İnternet erişimini sınırlandırıyorsa, hem gelen hem de giden API erişimi için aşağıdaki IP adreslerine izin vererek, Microsoft 365 desteği tümleştirmesi hizmeti için ağ erişimini etkinleştirin:

- 52.149.152.32

- 40.83.232.243

- 40.83.114.39

- 13.76.138.31

- 13.79.229.170

- 20.105.151.142

> [!NOTE]
> Bu terminal komutu, destek tümleştirmesi için hizmetin tüm etkin MICROSOFT 365 listeler:`nslookup`` connector.rave.microsoft.com`

## <a name="configure-the-microsoft-365-support-integration-application"></a>Microsoft 365 Desteği Tümleştirme Uygulamasını yapılandırma

Microsoft 365 desteği tümleştirme uygulaması, Destek Hizmetleri altında Microsoft 365 ayarlanır.

Bu adımlar, ServiceNow örneğiniz ve destek hizmetleriniz arasında tümleştirmeyi Microsoft 365 gerekir.

1. \[ServiceNow Yönetici\] Desteği tümleştirmeyi destekleme **Microsoft 365 kapsamını değiştirme**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image9.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image9.png" alt-text="Grafik kullanıcı arabirimi, tablo Açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow Yönetici\] Tümleştirme iş **Microsoft 365 için Destek &gt; Kurulumu'ne** gidin.

    > [!NOTE]
    > 'xmiomsm365assis\_\_\_' kapsamından "'oauthentity\_' hatasına karşı okuma işlemi tablonun çapraz kapsam erişim ilkesinden dolayı reddedildi" hatasını görüyorsanız, bunun nedeni tablo erişim ilkenizdir. Tablo kimlik doğrulaması **için Tüm uygulama kapsamları &gt; Okunabilir'in** işaretli olduğundan emin\_ olun.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image10.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image10.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow Admin Select\] **Agree** to continue.

    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-1.png" lightbox="../../media/ServiceNow-guide/snowbasic-1.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow Yönetici\] Ortamı ve kurulum türünü yapılandır.

    Bu yükleme bir test ortamında ise, Bu bir test ortamıdır seçeneğini belirtin. Kurulum ve tüm testlerinizi daha sonra tamamlandıktan sonra bu seçeneği hızla devre dışı abileceksiniz.
    Örneğin, gelen bağlantılar için Temel Kimlik Doğrulamasına izin verdiyse Evet'i seçin, aksi takdirde lütfen Gelişmiş Kurulum ve Güvenlik [AAD.](servicenow-aad-oauth-token.md) :::image type="content" source="../../media/ServiceNow-guide/snowbasic-2.png" lightbox="../../media/ServiceNow-guide/snowbasic-2.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow YöneticiDiyata\] kiracı Microsoft 365 etkinızı girin.

    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-3.png" lightbox="../../media/ServiceNow-guide/snowbasic-3.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow Yönetici\] Giden ayarlarını yapılandır.
    1. Azure Active Directory (AAD) uygulamasını kaydettirin.
    1. Önkoşullar bölümündeki yönergeleri tamamladıktan sonra Bitti'ye **tıklayın**. Aksi takdirde, sihirbazda gerekli uygulama kaydını oluşturmak için sihirbazda verilen AAD.
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-4.png" lightbox="../../media/ServiceNow-guide/snowbasic-4.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

    1. ServiceNow OAuth Uygulamasını kaydettirin.
    1. Önkoşullar bölümündeki yönergeleri tamamladıktan sonra, yeni oluşturulan OAuth uygulaması kaydını seçin ve Sonraki'ye tıklayın. Aksi takdirde, ServiceNow'da varlık oluşturmak için yönergeleri izleyin ve ardından yeni uygulama kaydını seçin.
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-5.png" lightbox="../../media/ServiceNow-guide/snowbasic-5.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow Yönetici\] Gelen ayarlarını yapılandır.
    1. Gelen OAuth API uç noktasını yapılandırma.
    1. Önkoşullar bölümündeki yönergeleri tamamladıktan sonra, yeni oluşturulan OAuth uygulaması kaydını seçin ve Bitti'ye tıklayın. Aksi takdirde, yönergeleri izleyerek yeni REST uç noktası kaydını seçin.
     
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-6.png" lightbox="../../media/ServiceNow-guide/snowbasic-6.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

    1. Tümleştirme Kullanıcısı'nın ayarlarını yapılandırma.
    1. Önkoşullar bölümündeki yönergeleri tamamladıktan sonra, yeni oluşturulan tümleştirme kullanıcılarını seçin ve Sonraki'ye tıklayın. Aksi takdirde, ServiceNow'da varlık oluşturmak için yönergeleri izleyin ve yeni tümleştirme kullanıcınızı seçin.
    
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-7.png" lightbox="../../media/ServiceNow-guide/snowbasic-7.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::


1. \[Microsoft 365 Kiracı Yöneticisi\] Portalda tümleştirmeyi Microsoft 365 Yönetici.

    Aşağıdaki bilgilerin doğru olduğunu doğrulayın. Şu anda **Sonraki'yi** SEÇMEYİN.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image17.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image17.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama Açıklaması otomatik olarak oluşturulur":::

1. Kuruluş ayarları **Microsoft 365 Yönetici Portal &gt; Ayarlar &gt; Kuruluş profilleri'ne &gt; gidin**.

1. Destek tümleştirme ayarlarını yapılandırma:

    Temel bilgiler **sekmesini seçin** > **İç** >  destek **aracıServiceNow'ı** seçin ve Kimlik Doğrulaması Belirteci'ne sorun için Uygulama **Kimliği'ne Giden Uygulama Kimliği değerini** girin. Bu Giden Uygulama Kimliği, 6. Adım'dadır ve Önkoşul [(Temel Kimlik Doğrulama) adım 1'de oluşturulmuş olan Tümleştirmeyi \#Tamamlama'dır](#prerequisites-basic-authentication).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image18.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image18.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. Depolar **sekmesinde** Yeni **depo'ya tıklayın** ve aşağıdaki ayarlarla güncelleştirin:

    - Depo: 6 **. Adımdan** Gelen Depo Kimliği değeri – Tümleştirmeyi Tamamlama.

    - Uç nokta: **6.** Adımdan Bitiş Noktası değeri – Tümleştirmeyi Tamamlama.

    - Kimlik doğrulama türü: Temel Kimlik **Doğrulaması'ı seçin**.

    - İstemci Kimliği: **6. Adımdan** itibaren İstemci Kimliği değeri – Tümleştirmeyi tamamlama.

    - İstemci sırrı: Önkoşullar (Temel Kimlik Doğrulama) adım 3'te oluşturulmuş gelen OAuth sağlayıcısının \#sırrı.

    - Yenileme belirteci son kullanma tarihi: 864000

    - Rest kullanıcı adı: 6 **. Adımdan** itibaren Kullanıcı Adı değeri – Tümleştirmeyi tamamlama.

    - Kalan kullanıcı parolası: Önkoşullar (Temel Kimlik Doğrulama [) adım 4'te oluşturulan tümleştirme kullanıcılarının \#parolası](#prerequisites-basic-authentication).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image19.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image19.png" alt-text="Grafik kullanıcı arabirimi, uygulama açıklaması otomatik olarak oluşturulur":::

1. ServiceNow'a geri dönme.

1. **Tümleştirmeyi tamamlamak** için Sonraki'yi seçin.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image20.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image20.png" alt-text="Grafik kullanıcı arabirimi, uygulama, web sitesi Açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow Admin\] Test the connection Önceki adımı tamamladıktan sonra, Bağlantıyı **sına'ya tıklayın**.
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-8.png" lightbox="../../media/ServiceNow-guide/snowbasic-8.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::
    En Microsoft 365 tümleştirme uygulaması, tümleştirmenin çalıştığını sağlamak için testler yürütür. Yapılandırmayla ilgili bir sorun varsa, neyin düzeltilecek şekilde olması gerektiğini bir hata iletisiyle açıklar. Aksi takdirde, uygulama hazır olur.
     :::image type="content" source="../../media/ServiceNow-guide/snowbasic-9.png" lightbox="../../media/ServiceNow-guide/snowbasic-9.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama, e-posta Açıklaması otomatik olarak oluşturulur":::

1. \[ServiceNow Yönetici\] Var olan bir kullanıcı için Microsoft desteği tümleştirmesini etkinleştirin.

    Microsoft 365 rollerinden biri olan kullanıcı için destek tümleştirmesi etkinleştirilmiştir:

    - xmiomsm365assis.insightsuser\_\_\_\_

    - xmiomsm365assis.administrator\_\_\_

1. \[İsteğE\] BAĞLı [Role sahip x_mioms_m365_assis.administrator bağlantısı] Hesabı Microsoft 365 Yönetici.

    Herhangi bir kullanıcı x_mioms_m365_assis.administrator rolüne sahipse ve bir Microsoft 365 destek vakasını yönetmek için farklı Microsoft 365 hesapları kullanıyorsa, bu kullanıcının Microsoft 365 yönetici e-postasını ayarlamak için Microsoft 365 > Bağlantı Hesabı Microsoft 365 e gitmeleri gerekir.
    
    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image21.png" alt-text="Grafik kullanıcı arabirimi, metin, uygulama Açıklaması otomatik olarak oluşturulur":::
