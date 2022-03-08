---
title: Çift Anahtar Şifrelemesi (DKE)
description: DKE, çok hassas verileri koruyarak anahtarın tam kontrolünü korumanıza olanak sağlar.
author: kccross
ms.author: krowley
manager: laurawi
ms.date: 02/28/2022
ms.topic: conceptual
ms.service: information-protection
audience: Admin
ms.reviewer: esaggese
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: b16733a1d42ca245f096038f567be6fbd0c3fb2a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320613"
---
# <a name="double-key-encryption-for-microsoft-365"></a>Double Key Encryption for Microsoft 365

> *Şu özellikler için geçerlidir: Uyumluluk Microsoft 365 Çift Anahtar [Microsoft 365,](https://www.microsoft.com/microsoft-365/business/compliance-management) [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Yönergeler: [Windows için Azure Information Protection birleşik Windows](/azure/information-protection/faqs#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*


> *Hizmet açıklaması: [Microsoft 365 Uyumluluğu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Çift Anahtar Şifrelemesi (DKE), korunan içeriğe erişmek için birlikte iki anahtar kullanır. Microsoft posta Microsoft Azure bir anahtar depolar ve siz de diğer anahtarı tutarken. Çift Anahtar Şifreleme hizmetini kullanarak anahtarlardan birinin tam denetimine sahip olursanız. Son derece hassas içeriğinize Azure Information Protection birleşik etiketleme istemcisini kullanarak koruma uygulayabilirsiniz.

Çift Anahtar Şifrelemesi hem bulut hem de şirket içi dağıtımları destekler. Bu dağıtımlar, korumalı verileri depolarken şifrelenmiş verilerin opak kalmasını sağlamaya yardımcı olur.

Varsayılan, bulut tabanlı kiracı kök anahtarları hakkında daha fazla bilgi için bkz [. Azure Information Protection kiracı anahtarınızı planlama ve uygulama](/azure/information-protection/plan-implement-tenant-key).

## <a name="when-your-organization-should-adopt-dke"></a>Organizasyon ne zaman DKE'yi benimsemeli?

Çift Anahtar Şifrelemesi, en sıkı koruma gereksinimlerine tabi olan en hassas verilerinize yöneliktir. DKE, tüm verilere yönelik değildir. Genel olarak, genel verilerinizin yalnızca küçük bir bölümünü korumak için Çift Anahtar Şifrelemesi kullanırsanız. Dağıtmadan önce, bu çözümün kapsıyor olduğu doğru verileri belirlemek için son dili incelemelisiniz. Bazı durumlarda, kapsamınızı daraltmanız ve verilerinizin çoğu için Microsoft tarafından yönetilen anahtarlar veya BYOK Microsoft Bilgi Koruması başka çözümler kullanmanız gerekiyor olabilir. Gelişmiş koruma ve mevzuat gereksinimlerine tabi olmayan belgeler için bu çözümler yeterlidir. Ayrıca bu çözümler, en güçlü Office 365 hizmetlerini, DKE şifreli içerikle kullany olmadığınız hizmetleri de kullanabilirsiniz. Örneğin:

- Ekin görünürlüğünü gerektiren kötü amaçlı yazılımdan koruma ve istenmeyen posta içeren aktarım kuralları
- Microsoft Delve
- eKbulma
- İçerik arama ve dizin oluşturma
- Office birlikte kimlik doğrulaması işlevselliği de içinde olmak üzere web uygulamaları

MICROSOFT BILGI KORUMASı (MIP) SDK aracılığıyla DKE ile tümleştirilmiş olmayan tüm dış uygulamalar veya hizmetler, şifrelenmiş veriler üzerinde eylem gerçekleştiramaz.

Microsoft Bilgi Koruması SDK 1.7+ çift Anahtar Şifrelemesi'i destekler. SDK'miz ile tümleştiren uygulamalar, bu veriler üzerinde yeterli izinlere ve tümleştirmelere neden olabilir.

Hassas verilerinizin çoğunu korumak için Microsoft Bilgi koruma özelliklerini (sınıflandırma ve etiketleme) kullanın ve DKE'yi yalnızca görev açısından kritik verileriniz için kullanın. Çift Anahtar Şifrelemesi, Finansal hizmetler ve Sağlık gibi son derece düzenlemeye tabi olan sektörlerde hassas veriler için uygundur.

Kuruluşlarının aşağıdaki gereksinimleri varsa, içeriğinizin güvenliğini sağlamak için DKE kullanabilirsiniz:

- Her koşulda, *korumalı içeriğin şifresini yalnızca* siz çözesiniz diye emin olmak istiyor olun.
- Microsoft'un korumalı verilere kendi kendine erişmesini istemiyoruz.
- Coğrafi sınırlar içinde anahtar tutmak için yasal düzenleme gereksinimlerine sahipsiniz. Veri şifreleme ve şifre çözme için basılı tutarken tüm anahtarlar veri merkezinize korunur.

## <a name="system-and-licensing-requirements-for-dke"></a>DKE için sistem ve lisans gereksinimleri

**Double Key Encryption for Microsoft 365** Encryption with Microsoft 365 E5. Microsoft 365 E5 lisansınız yoksa, deneme sürümüne [kaydolarak kaydol.](https://aka.ms/M365E5ComplianceTrial) Bu lisanslar hakkında daha fazla bilgi için güvenlik [Microsoft 365 uyumluluğu için lisanslama & bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

**Azure Information Protection.** DKE duyarlılık etiketleriyle çalışır ve Azure Information Protection gerektirir.

DKE duyarlılık etiketleri, Office Masaüstü Uygulamaları'nın AIP Birleşik Etiketleme istemcisinde bulunan duyarlılık düğmesi üzerinden son kullanıcılarına sunulmaktadır. Korumalı belgeleri korumak ve tüketmek istediğiniz her istemci bilgisayara bu önkoşulları yükleyin.

**Microsoft Office sürüm** 2009 veya sonraki sürümleri (Word, PowerPoint ve Excel'un masaüstü sürümleri) için Windows.

**Azure Information Protection Birleşik Etiketleme İstemcisi** sürüm 2.7.93.0 veya sonrası. Microsoft indirme merkezinden Birleşik Etiket istemcisini [indirin ve yükleyin](https://www.microsoft.com/download/details.aspx?id=53018).

## <a name="supported-environments-for-storing-and-viewing-dke-protected-content"></a>DKE korumalı içeriği depolamak ve görüntülemek için desteklenen ortamlar

**Desteklenen uygulamalar**. [Kurumlar için Microsoft 365 Uygulamaları](https://www.microsoft.com/microsoft-365/business/microsoft-365-apps-for-enterprise-product) Word Windows, Excel ve diğer PowerPoint.

**Çevrimiçi içerik desteği**. Çevrimiçi Çift Anahtar Şifrelemesi ile korunan belgeleri ve dosyaları hem Microsoft SharePoint hem de İş OneDrive İş. Bu konumlara yüklemeden önce, belgeleri ve dosyaları desteklenen uygulamalarla DKE ile etiketlemeniz ve korumaniz gerekir. Şifrelenmiş içeriği e-postayla paylaşabilirsiniz, ancak şifrelenmiş belgeleri ve dosyaları çevrimiçi görüntüye sahip değildir. Bunun yerine, korumalı içeriği yerel bilgisayarınızda desteklenen masaüstü uygulamalarını ve istemcilerini kullanarak görüntülemeniz gerekir.

## <a name="overview-of-deploying-dke"></a>DKE dağıtımına genel bakış

DKE'yi ayarlamak için bu genel adımları takip edersiniz. Bu adımları tamamlandıktan sonra, son kullanıcılarınız çok hassas verilerinizi Çift Anahtar Şifrelemesi ile koruyabilir.

1. DKE hizmetini bu makalede açıklandığı gibi dağıtın.

2. Çift Anahtar Şifrelemesi ile etiket oluşturun. Aşağıdaki Microsoft 365 uyumluluk merkezi korumasına **gidin ve Çift** Anahtar Şifrelemesi ile yeni bir etiket oluşturun. Bkz [. Şifreleme uygulamak için duyarlılık etiketlerini kullanarak içeriğe erişimi kısıtlama](./encryption-sensitivity-labels.md).

3. Çift Anahtar Şifrelemesi etiketlerini kullanın. Verileri korumak için, şeritteki Duyarlılık şeridinden Çift Anahtar şifreli etiketi Microsoft Office.

Çift Anahtar Şifrelemesi'nin bazı adımlarını tamamlamanın çeşitli yolları vardır. Bu makalede, daha az deneyimli yöneticinin hizmeti başarılı bir şekilde dağıtması için ayrıntılı yönergeler ve sağlar. Bunu daha rahat yapıyorsanız, kendi yöntemlerinizi kullanmayı seçebilirsiniz.

## <a name="deploy-dke"></a>DKE'yi dağıtma

Bu makale ve dağıtım videosunda DKE hizmetinin dağıtım hedefi olarak Azure'un kullanımı yer alır. Başka bir konuma dağıtıyorsanız, kendi değerlerinizi sağlaymanız gerekir.

Bu makalede [kavramlara adım adım](https://youtu.be/vDWfHN_kygg) genel bakış için Çift Anahtar Şifreleme dağıtım videosunu izleyin. Videonun tamamlanması yaklaşık 18 dakika sürer.

Bu genel adımları takip edecek ve kurum için Çift Anahtar Şifrelemesi'ne ayaracağız.

1. [DKE hizmetinin yazılım önkoşullarını yükleme](#install-software-prerequisites-for-the-dke-service)
1. [Çift Anahtar Şifrelemesi veri GitHub kopyalama](#clone-the-dke-github-repository)
1. [Uygulama ayarlarını değiştirme](#modify-application-settings)
1. [Test tuşları oluşturma](#generate-test-keys)
1. [Projeyi oluşturma](#build-the-project)
1. [DKE hizmetini dağıtma ve anahtar depolarını yayımlama](#deploy-the-dke-service-and-publish-the-key-store)
1. [Dağıtımınızı doğrulama](#validate-your-deployment)
1. [Anahtar mağazanızı kaydettirin](#register-your-key-store)
1. [DKE kullanarak duyarlılık etiketleri oluşturma](#create-sensitivity-labels-using-dke)
1. [İstemciniz içinde DKE'yi etkinleştirme](#enable-dke-in-your-client)
1. [Korumalı dosyaları HYOK etiketlerinden DKE etiketlerine geçirme](#migrate-protected-files-from-hyok-labels-to-dke-labels)

Bitirebilirsiniz, belgeleri ve dosyaları DKE kullanarak şifrelersiniz. Bilgi için bkz. [Dosya ve e-postanıza duyarlılık etiketleri Office](https://support.microsoft.com/office/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).

### <a name="install-software-prerequisites-for-the-dke-service"></a>DKE hizmetinin yazılım önkoşullarını yükleme

DKE hizmetini yüklemek istediğiniz bilgisayara bu önkoşulları yükleyin.

**.NET Core 3.1 SDK**. DOWNLOAD [.NET Core 3.1'den SDK'yı indirin ve yükleyin](https://dotnet.microsoft.com/download/dotnet-core/3.1).

**Visual Studio Code**. 'dan Visual Studio Code indirin[https://code.visualstudio.com/](https://code.visualstudio.com). Yüklendikten sonra Uzantılar'Visual Studio Code'ı **çalıştırın ve Uzantıları Görüntüle'yi** \> **seçin**. Bu uzantıları yükleyin.

- C# Visual Studio Code

- NuGet Paket Yöneticisi

**Kaynakları git'i kullanın**. Aşağıdakilerden birini indirin ve yükleyin.

- [Git](https://git-scm.com/downloads)

- [GitHub Masaüstü](https://desktop.github.com/)

- [GitHub Enterprise](https://github.com/enterprise)

**OpenSSL** DKE'yi dağıttıktan sonra test anahtarları [oluşturmak için](#generate-test-keys) [OpenSSL'i](https://slproweb.com/products/Win32OpenSSL.html) yüklemişsinizdir. Ortamı değişken yollarından bunu doğru bir şekilde iptal edin. Örneğin, ayrıntılar için bkz. "Yükleme dizinini PATH'e [https://www.osradar.com/install-openssl-windows/](https://www.osradar.com/install-openssl-windows/) ekleme".

### <a name="clone-the-dke-github-repository"></a>DKE veri GitHub klonlama

Microsoft, DKE kaynak dosyalarını bir depolama GitHub sağlar. Projeyi, kurum kullanımının yerel olarak oluşturmak için depoyu klonlarsunuz. DKE GitHub deposu, üzerindedir[https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService).

Aşağıdaki yönergeler deneyimsiz git veya Visual Studio Code yöneliktir:

1. Tarayıcınızda, şu gidin: [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService).

2. Ekranın sağ tarafına doğru Kod'a **tıklayın**. Kullanıcı arabirimi sürümünüz Clone veya **download düğmesi gösteriyor** olabilir. Ardından, görüntülenen açılan listeden kopyala simgesini seçerek URL'yi panoya kopyalayın.

    Örneğin:

   > [!div class="mx-imgBorder"]
   > ![Double Key Encryption hizmet deposunu bir veri GitHub.](../media/dke-clone.png)

3. Görünüm Visual Studio Code Komut Paletini **Görüntüle'yi** \> **ve ardından** **Git: Clone'ı seçin**. Listede bu seçenge atlamak için, yazmaya `git: clone` başlayıp girdileri filtrelenin ve sonra açılan listeden bunu seçin. Örneğin:

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Code GIT:Clone seçeneği.](../media/dke-vscode-clone.png)

4. Metin kutusuna Git'den kopyalanan URL'yi yapıştırın ve Kopyala'dan **Kopyala'GitHub**.

5. Görüntülenen **Klasör Seç** iletişim kutusunda deponun depo depolu olduğu konuma göz atabilir ve bu konumu seçebilirsiniz. Komut isteminde Aç'ı **seçin**.

    Depolama Visual Studio Code açılır ve sol altta geçerli Git dalı görüntülenir. Örneğin, Dal ana **dal olmalı**. Örneğin:

   ![Ana dalı görüntüleyen bir Visual Studio Code DKE veripo nun ekran görüntüsü.](../media/dke-vscode-main-branch.jpg)

6. Ana dalda değilken seçmeniz gerekir. Ana Visual Studio Code dalı seçin ve **sonra dalı** gösteren dal listesinden ana'yi seçin.

   > [!IMPORTANT]
   > Ana dalı seçerek, projeyi oluşturmak için doğru dosyalara sahip oluruz. Doğru dalı seçmezsiniz, dağıtımınız başarısız olur.

Artık DKE kaynak deponuz yerel olarak ayarlanmış. Ardından, [kurum için uygulama](#modify-application-settings) ayarlarını değiştirin.

### <a name="modify-application-settings"></a>Uygulama ayarlarını değiştirme

DKE hizmetinin dağıtımı için, aşağıdaki uygulama ayarları türlerini değiştirmeniz gerekir:

- [Anahtar erişim ayarları](#key-access-settings)
- [Kiracı ve anahtar ayarları](#tenant-and-key-settings)

appsettings.json dosyasında uygulama ayarlarını değiştirin. Bu dosya, DoubleKeyEncryptionService repo olarak DoubleKeyEncryptionService\src\customer-key-store altında yerel olarak kopyalamış olduğunuz DoubleKeyEncryptionService repo içinde yer almaktadır. Örneğin, Visual Studio Code resimde gösterildiği gibi dosyaya göz atabilirsiniz.

![DKE için appsettings.json dosyasını bulma.](../media/dke-appsettingsjson.png)

#### <a name="key-access-settings"></a>Anahtar erişim ayarları

E-postayı mı yoksa rol yetkilendirmeyi mi kullanabileceğinizi seçin. DKE, aynı anda bu kimlik doğrulama yöntemlerinden yalnızca birini destekler.

- **E-posta yetkilendirme**. Kuruluşlarının anahtarlara erişimi yalnızca e-posta adreslerine göre yetkilendirmelerine olanak sağlar.

- **Rol yetkilendirme**. Kuruluş, Active Directory gruplarına dayalı olarak anahtarlar için erişim yetkisi vermesini sağlar ve web hizmetinin LDAP'ye sorgu gerçekleştirmesini gerektirir.

##### <a name="to-set-key-access-settings-for-dke-using-email-authorization"></a>E-posta yetkilendirmeyi kullanarak DKE için anahtar erişim ayarlarını ayarlamak için

1. **appsettings.json dosyasını** açın ve ayarı `AuthorizedEmailAddress` bulun.

2. Yetkilendirmek istediğiniz e-posta adresini veya adresleri ekleyin. Birden çok e-posta adresini çift tırnak ve virgülle birbirinden ayırabilirsiniz. Örneğin:

   ```json
   "AuthorizedEmailAddress": ["email1@company.com", "email2@company.com ", "email3@company.com"]
   ```

3. `LDAPPath` Ayarı bulun ve çift tırnak arasındaki `If you use role authorization (AuthorizedRoles) then this is the LDAP path.` metni kaldırın. Çift tırnakları olduğu gibi bırakın. Bitirdikten sonra, ayar aşağıdakine benzer bir görünümde olur.

   ```json
   "LDAPPath": ""
   ```

4. Ayarı bulun `AuthorizedRoles` ve satırın tamamını silin.

Bu resimde, **appsettings.json dosyası** e-posta yetkilendirme için doğru biçimlendirilmiş olarak görüntülenir.

   ![E-posta yetkilendirme yöntemini gösteren appsettings.json dosyası.](../media/dke-email-accesssetting.png)

##### <a name="to-set-key-access-settings-for-dke-using-role-authorization"></a>Rol yetkilendirmeyi kullanarak DKE için anahtar erişim ayarlarını ayarlamak için

1. **appsettings.json dosyasını** açın ve ayarı `AuthorizedRoles` bulun.

2. Yetkilendirmek istediğiniz Active Directory grup adlarını ekleyin. Birden çok grup adlarını çift tırnak ve virgülle birbirinden ayırabilirsiniz. Örneğin:

   ```json
   "AuthorizedRoles": ["group1", "group2", "group3"]
   ```

3. Ayarı bulun `LDAPPath` ve Active Directory etki alanını ekleyin. Örneğin:

   ```json
   "LDAPPath": "contoso.com"
   ```

4. Ayarı bulun `AuthorizedEmailAddress` ve satırın tamamını silin.

Bu resimde, **rol yetkilendirme için appsettings.json** dosyası doğru biçimlendirilmiş olarak görüntülenir.

   ![rol yetkilendirme yöntemini gösteren appsettings.json dosyası.](../media/dke-role-accesssetting.png)

#### <a name="tenant-and-key-settings"></a>Kiracı ve anahtar ayarları

DKE kiracısı ve anahtar ayarları **appsettings.json dosyasında** bulunur.

##### <a name="to-configure-tenant-and-key-settings-for-dke"></a>DKE için kiracı ve anahtar ayarlarını yapılandırmak için

1. **appsettings.json dosyasını** açın.

2. Ayarı bulun `ValidIssuers` ve kiracı `<tenantid>` kimliğiyle değiştirin. Azure portalına gidip kiracı özelliklerini görüntüerek kiracı [kimliğinizi bulabilirsiniz](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties). Örneğin:

   ```json
   "ValidIssuers": [
     "https://sts.windows.net/9c99431e-b513-44be-a7d9-e7b500002d4b/"
   ]
   ```

> [!NOTE]
> Anahtar mağazanıza dış B2B erişimini etkinleştirmek için, bu dış kiracıları geçerli sorun sağlayanlar listesinin bir parçası olarak da dahil edin.

'ı bulun `JwtAudience`. DKE `<yourhostname>` hizmetinin çalıştır yer alacak olduğu makinenin ana bilgisayar adı ile değiştirin. Örneğin:

  > [!IMPORTANT]
  > değeri, ana `JwtAudience` nizin adıyla tam olarak *eşleşmeli*. Hata ayıklama sırasında **localhost:5001** kullanabilirsiniz. Bununla birlikte, hata ayıklamayı bitirin, bu değeri sunucunun ana bilgisayaradına güncelleştirin.

- `TestKeys:Name`. Anahtarınız için bir ad girin. Örneğin: `TestKey1`
- `TestKeys:Id`. GUID oluşturun ve değer olarak `TestKeys:ID` bunu girin. Örneğin, `DCE1CC21-FF9B-4424-8FF4-9914BD19A1BE`. Rastgele bir GUID oluşturmak için [Çevrimiçi GUID Oluşturucu](https://guidgenerator.com/) gibi bir site kullanabilirsiniz.

Bu resim **, appsettings.json'da kiracı ve anahtar ayarları için doğru biçimi gösterir**. `LDAPPath` rol yetkilendirme için yapılandırıldı.

![appsettings.json dosyasında DKE için doğru kiracı ve anahtar ayarlarını gösterir.](../media/dke-appsettingsjson-tenantkeysettings.png)

### <a name="generate-test-keys"></a>Test tuşları oluşturma

Uygulama ayarlarınız tanımlanmamışsa, genel ve özel test anahtarları oluşturmak için hazır oluruz.

Anahtar oluşturmak için:

1. Komut Windows Başlat menüsü, OpenSSL Komut İstemi'ne çalıştırın.

1. Test tuşlarını kaydetmek istediğiniz klasöre gidin. Bu görevdeki adımları tamamlayarak oluştursanız da dosyalar aynı klasörde depolanır.

1. Yeni test anahtarını oluştur.

   ```console
   openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365
   ```

1. Özel anahtarı oluşturma.

   OpenSSL sürüm 3 veya sonraki bir sürümünü yüklemişsiniz, aşağıdaki komutu çalıştırın:
  
  ```console
  openssl rsa -in key.pem -out privkeynopass.pem -outform PEM -traditional
  ```
  
>  Aksi takdirde aşağıdaki komutu çalıştırın:
>  ```console
>  openssl rsa -in key.pem -out privkeynopass.pem -outform PEM
>  ```

1. Ortak anahtarı oluşturma.

   ```console
   openssl rsa -in key.pem -pubout > pubkeyonly.pem
   ```

1. Metin düzenleyicisinde **pubkeyonly.pem'yi açın**. **pubkeyonly.pem** dosyasındaki ilk ve son satırlar dışında tüm `PublicPem` içeriği **appsettings.json dosyasının bölümüne** kopyalayın.

1. Metin düzenleyicisinde **privkeynopass.pem'yi açın**. **privkeynopass.pem** `PrivatePem` dosyasındaki ilk ve son satırlar hariç tüm içeriği **appsettings.json dosyasının bölümüne** kopyalayın.

1. Hem hem de bölümlerdeki tüm boş boşlukları ve yeni `PublicPem` çizgileri `PrivatePem` kaldırın.

    > [!IMPORTANT]
    > Bu içeriği kopyalarıken, PEM verilerini silmeyin.

1. Yeni Visual Studio Code, **Startup.cs dosyasına** göz atabilirsiniz. Bu dosya, DoubleKeyEncryptionService\src\customer-key-store\ altında yerel olarak kopyalamış olduğunuz DoubleKeyEncryptionService repo içinde yer almaktadır.

1. Aşağıdaki satırları bulun:

    ```csharp
        #if USE_TEST_KEYS
        #error !!!!!!!!!!!!!!!!!!!!!! Use of test keys is only supported for testing,
        DO NOT USE FOR PRODUCTION !!!!!!!!!!!!!!!!!!!!!!!!!!!!!
        services.AddSingleton<ippw.IKeyStore, ippw.TestKeyStore>();
        #endif
    ```

1. Bu satırları aşağıdaki metinle değiştirin:

    ```csharp
    services.AddSingleton<ippw.IKeyStore, ippw.TestKeyStore>();
    ```

    Bitiş sonuçları aşağıdakine benzer şekilde sonuç verir.

    ![genel önizleme için startup.cs dosyası.](../media/dke-startupcs-usetestkeys.png)

Artık [DKE projenizi oluşturmak için hazır mısınız](#build-the-project)?

### <a name="build-the-project"></a>Projeyi oluşturma

DKE projesini yerel olarak oluşturmak için aşağıdaki yönergeleri kullanın:

1. Veri Visual Studio Code DKE hizmet deposundaKimlik Paletini  \> Görüntüle'yi seçin ve bilgi **istemine derleme** yazın.

2. Listeden Görevler: Derleme **görevini çalıştır'ı seçin**.

   Bulunan derleme görevleri yoksa, Yapı Görevi **Yapılandır'ı seçin ve** .NET core için aşağıdaki gibi bir görev oluşturun.

   ![.NET için eksik derleme görevini yapılandır.](../media/dke-configurebuildtask.png)

   1. **Şablondan görevler.json oluştur'u seçin**.

      ![DKE için şablondan tasks.json dosyası oluşturun.](../media/dke-createtasksjsonfromtemplate.png)

   2. Şablon türleri listesinden **.NET Core öğesini seçin**.

      ![DKE için doğru şablonu seçin.](../media/dke-tasksjsontemplate.png)

   3. Derleme bölümünde **customerkeystore.csproj dosyasının yolunu** bulun. Listede yoksa, aşağıdaki satırı ekleyin:

      ```json
      "${workspaceFolder}/src/customer-key-store/customerkeystore.csproj",
      ```

   4. Derlemeyi yeniden çalıştırın.

3. Çıkış penceresinde kırmızı hata olmadığını doğrulayın.

   Kırmızı hatalar varsa konsol çıkışını kontrol edin. Önceki tüm adımları doğru şekilde tamamla hazır bulundurarak doğru derleme sürümlerinin mevcut olduğundan emin olun.

4. İşleme **hata** \> **ayıklamak için Başlatma Hata** Ayıklamayı Çalıştır'ı seçin. Bir ortam seçmeniz istenirse **,.NET core öğesini seçin**.

   .NET çekirdek hata ayıklayıcı normalde olarak ' a başlatıyor `https://localhost:5001`. Test anahtarınızı görüntülemek için, eğik `https://localhost:5001` çizgi (/) işaretine gidip anahtarın adına gidin. Örneğin:

   ```https
   https://localhost:5001/TestKey1
   ```

   Anahtar JSON biçiminde görüntüleniyor olmalıdır.

Kurulumunuz tamamlanmıştır. JwtAudience ayarı için appsettings.json adlı anahtar mağazayı yayımlamadan önce, ana bilgisayar adının değerinin Uygulama Hizmeti ana bilgisayar adınızla tam eş olduğundan emin olur. Derlemenin sorunlarını gidermek için bunu localhost olarak değiştirmiş olabilirsiniz.

### <a name="deploy-the-dke-service-and-publish-the-key-store"></a>DKE hizmetini dağıtma ve anahtar depolarını yayımlama

Üretim dağıtımlarında, hizmeti üçüncü taraf bir bulutta dağıtın [veya şirket içi bir sistemde yayımlayın](/aspnet/core/tutorials/publish-to-iis?preserve-view=true&tabs=netcore-cli&view=aspnetcore-3.1).

Anahtarlarınızı dağıtmak için başka yöntemler de kullanabilirsiniz. Organizasyonunıza en uygun yöntemi seçin.

Pilot dağıtımlarda, Azure'da dağıtarak hemen çalışmaya başlamanız da gerekir.

#### <a name="to-create-an-azure-web-app-instance-to-host-your-dke-deployment"></a>DKE dağıtımınızı barındırmak için bir Azure Web App örneği oluşturmak için

Anahtar mağazayı yayımlamak için, DKE dağıtımınızı barındırmak için bir Azure Uygulama Hizmeti örneği oluşturacağız. Ardından, oluşturulan anahtarlarınızı Azure'da yayımlarsiniz.

1. Tarayıcınızda Uygulama Portalı'Microsoft Azure [açın](https://ms.portal.azure.com) ve **App** **ServicesAdd'ye** >  gidin.

2. Aboneliğinizi ve kaynak grubunızı seçin ve örnek ayrıntılarınızı tanımlayın.

   - DKE hizmetini yüklemek istediğiniz bilgisayarın ana bilgisayar adını girin. [**Bunun appsettings.json**](#tenant-and-key-settings) dosyasındaki JwtAudience ayarı için tanımlanan adla aynı olduğundan emin olun. Ad için sağlanmayan değer aynı zamanda WebAppInstanceName değeridir.

   - **Yayımla için** kod **seçin ve** Çalışma Zamanı **yığını için** **.NET Core 3.1'i seçin**.

   Örneğin:

   > [!div class="mx-imgBorder"]
   > ![Uygulama Hizmetinizi ekleyin.](../media/dke-azure-add-app-service.png)

3. Sayfanın alt kısmında Gözden Geçir **+ oluştur'a ve sonra** Ekle'ye **tıklayın**.

4. Oluşturulan anahtarlarınızı yayımlamak için aşağıdakilerden birini yapın:

   - [ZipDeployUI yoluyla yayımlama](#publish-via-zipdeployui)
   - [FTP yoluyla yayımlama](#publish-via-ftp)
   - [Visual Studio 2019 veya sonraki bir yıl ile yayımlama](/aspnet/core/tutorials/)

#### <a name="publish-via-zipdeployui"></a>ZipDeployUI yoluyla yayımlama

1. `https://<WebAppInstanceName>.scm.azurewebsites.net/ZipDeployUI` adresine gidin.

   Örneğin: `https://dkeservice.scm.azurewebsites.net/ZipDeployUI`

2. Anahtar deposuna ait kod tabanında **, customer-key-store\src\customer-key-store** klasörüne gidin ve bu klasörün **customerkeystore.csproj** dosyasını içerdiğini doğrulayın.

3. Çalıştır: **dotnet yayımlama**

   Çıkış penceresi, yayımlamanın dağıtıldı olduğu dizini görüntüler.

   Örneğin: `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

4. Yayımlama dizininde yer alan tüm dosyaları bir .zip gönderin. .zip oluştururken, dizinde yer alan tüm dosyaların dosya dosyasının kök düzeyinde .zip.

5. Kendi .zip zipDeployUI sitesinde açtığınız posta dosyasını sürükleyip bırakın. Örneğin: `https://dkeservice.scm.azurewebsites.net/ZipDeployUI`

DKE dağıtılır ve oluşturduğunuz test anahtarlarına göz atabilir. Aşağıdaki [Dağıtımınızı doğrulamaya devam](#validate-your-deployment) edin.

#### <a name="publish-via-ftp"></a>FTP yoluyla yayımlama

1. Bağlan oluşturduğunuz Uygulama Hizmeti'ne [özel olarak oluşturulduğunda](#deploy-the-dke-service-and-publish-the-key-store).

   Tarayıcınızda şu gidin: **Azure portalApp** >  **ServiceDeployment** >  **CenterManual** >  **DeploymentFTPDashboard** >  > .

2. Görüntülenen bağlantı dizelerini yerel bir dosyaya kopyalayın. Bu dizeleri Web App Hizmeti'ne bağlanmak ve FTP yoluyla dosyaları karşıya yüklemek için kullanacağız.

   Örneğin:

   ![FTP panosundan bağlantı dizelerini kopyalayın.](../media/dke-ftp-dashboard.png)

3. Anahtar depolaması için kod tabanında **customer-key-store\src\customer-key-store dizinine gidin**.

4. Bu dizinin **customerkeystore.csproj dosyasını içerdiğini doğrulayın** .

5. Çalıştır: **dotnet yayımlama**

   Çıkış, yayımlamanın dağıtıldı olduğu dizini içerir.

   Örneğin: `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

6. Yayımlama dizininde yer alan tüm dosyaları bir zip dosyasına gönderin. .zip oluştururken, dizinde yer alan tüm dosyaların dosya dosyasının kök düzeyinde .zip.

7. FTP istemcinizin Uygulama Hizmetinize bağlanmak için kopyalanmış olan bağlantı bilgilerini kullanın. Upload .zip oluşturduğunuz dosyanın kök dizinine web app.

DKE dağıtılır ve oluşturduğunuz test anahtarlarına göz atabilir. Ardından, [dağıtımınızı doğrula'dır](#validate-your-deployment).

### <a name="validate-your-deployment"></a>Dağıtımınızı doğrulama

Yukarıda açıklanan yöntemlerden birini kullanarak DKE'yi dağıttıktan sonra, dağıtımı ve anahtar deposu ayarlarını doğrulamalısınız.

Çalıştır:

```powershell
src\customer-key-store\scripts\key_store_tester.ps1 dkeserviceurl/mykey
```

Örneğin:

```powershell
key_store_tester.ps1 https://mydkeservice.com/mykey
```

Çıktıda hata görünmey olduğundan emin olun. Hazır olduğunda anahtar [mağazanızı kaydettirin](#register-your-key-store).

Anahtar, büyük/harfe duyarlıdır. appsettings.json dosyasında göründüğü şekilde anahtar adını girin.

## <a name="register-your-key-store"></a>Anahtar mağazanızı kaydettirin

Aşağıdaki adımlar DKE hizmetinizi kaydetmenizi sağlar. DKE hizmetinizi kaydetmek, etiket oluşturmaya başlamadan önce DKE'yi dağıtmanın son adımıdır.

DKE hizmetini kaydetmek için:

1. Tarayıcınızda Kayıt Portalı'Microsoft Azure [ve](https://ms.portal.azure.com/) Tüm Hizmetler **Kimlik Uygulaması** **Kayıtları'ne** \> \> **gidin**.

2. Yeni **kayıt'ı** seçin ve anlamlı bir ad girin.

3. Görüntülenen seçeneklerden bir hesap türü seçin.

   Microsoft Azure gibi özel olmayan bir etki alanıyla kullanıyorsanız, **onmicrosoft.com** bu kuruluş dizininde hesaplar 'ı seçin **(yalnızca Microsoft - Tek kiracı).**

   Örneğin:

   > [!div class="mx-imgBorder"]
   > ![Yeni Uygulama Kaydı.](../media/dke-app-registration.png)

4. Yeni Uygulama Kaydı oluşturmak için sayfanın **en altında** Kaydol'a tıklayın.

5. Yeni Uygulama Kaydınız'da, sol bölmede Yönet'in altında **Kimlik** Doğrulama'ya **tıklayın**.

6. Platform **ekle'yi seçin**.

7. Platformları **yapılandır açılır** menüsünde Web'i **seçin**.

8. Yeniden **Yönlendirme URI'leri** altında, çift anahtar şifreleme hizmetinizin URI'sini girin. Hem ana bilgisayar adı hem de etki alanıyla birlikte Uygulama Hizmeti URL'sini girin.

   Örneğin: `https://mydkeservicetest.com`

   - Girdiğiniz URL, DKE hizmetinizin dağıtıldı olduğu ana bilgisayar adı ile eşleşmeli.
   - Etki alanı, doğrulanmış bir etki [alanı olmalıdır](/azure/active-directory/develop/reference-breaking-changes#appid-uri-in-single-tenant-applications-will-require-use-of-default-scheme-or-verified-domains).
   - Yerel olarak test etmek için Visual Studio kullanın`https://localhost:5001`.
   - Her durumda, düzen **https olması gerekir**.

   Ana bilgisayar adını, Uygulama Hizmeti ana bilgisayaradınıza tam olarak eşleyene kadar kullanın. Derlemenin sorunlarını gidermek için `localhost` onu değiştirmiş olabilirsiniz. **Appsettings.json içinde**, bu değer için ayarlayarak ana bilgisayar adıdır`JwtAudience`.

9. Örtülü **grant altında**, Kimlik **belirteçleri onay** kutusunu seçin.

10. **Değişikliklerinizi kaydetmek** için Kaydet'i seçin.

11. Sol bölmede API'yi göster'i **seçin, Uygulama** Kimliği URI'si'nin yanındaki Uygulama Hizmeti URL'nizi hem ana bilgisayar adı hem de etki alanı ile birlikte girin ve ardından Ayarla'ya **tıklayın**.

12. Yine **API'yi açığa** çıkarma sayfasında, Bu **API alanı** tarafından tanımlanan Kapsamlar'da Kapsam **ekle'yi seçin**. Yeni kapsamda:

    1. Kapsam adını önemli olarak **user_impersonation**.

    2. İzin ve izni olan yöneticileri ve kullanıcıları seçin.

    3. Gerekli kalan değerleri tanımlayın.

    4. Kapsam **ekle'yi seçin**.

    5. **Değişikliklerinizi** kaydetmek için üst kısmından Kaydet'i seçin.

13. Yine **API'yi ortaya** çıkarma sayfasındaki **Yetkili istemci uygulamaları alanında** İstemci uygulaması **ekle'yi seçin**.

    Yeni istemci uygulamasında:

    1. İstemci Kimliğini farklı tanımlayın `d3590ed6-52b3-4102-aeff-aad2292ab01c`. Bu değer, Microsoft Office kimliğidir ve Office anahtarınız için bir erişim belirteci almalarına olanak sağlar.

    2. Yetkili **kapsamlar'ın** altında uygun **user_impersonation** seçin.

    3. Uygulama **ekle'yi seçin**.

    4. **Değişikliklerinizi** kaydetmek için üst kısmından Kaydet'i seçin.

    5. Bu adımları yinele, ancak bu kez istemci kimliğini ' olarak tanımlayın `c00e9d32-3c8d-4a7d-832b-029040e7db99`. Bu değer, Azure Information Protection birleşik etiketleme istemci kimliğidir.

DKE hizmetiniz artık kayıtlıdır. [DKE kullanarak etiketler oluşturarak devam edin](#create-sensitivity-labels-using-dke).

## <a name="create-sensitivity-labels-using-dke"></a>DKE kullanarak duyarlılık etiketleri oluşturma

Daha fazla Microsoft 365 uyumluluk merkezi şekilde yeni bir duyarlılık etiketi oluşturun ve şifrelemeyi her zaman olduğu gibi uygulayabilirsiniz. Çift **Anahtar Şifrelemesi Kullan'ı** seçin ve anahtarınız için uç nokta URL'sini girin. Url'ye appsettings.json dosyasının "TestKeys" bölümüne, sağlanan anahtar adını dahil edin.

Örneğin: `https://testingdke1.azurewebsites.net/KEYNAME`

> [!div class="mx-imgBorder"]
> ![Kayıtta Çift Anahtar Şifrelemesi Kullan'Microsoft 365 uyumluluk merkezi.](../media/dke-use-dke.png)

Tüm DKE etiketleri, kullanıcılarının son sürümlerinde görünmeye başlar ve Kurumlar için Microsoft 365 Uygulamaları.

> [!NOTE]
> İstemcilerin yeni etiketlerle yenilenmesi 24 saat kadar sürebilir.

### <a name="enable-dke-in-your-client"></a>İstemciniz içinde DKE'yi etkinleştirme

Insider'da Office, DKE sizin için etkinleştirilir. Aksi takdirde, aşağıdaki kayıt defteri anahtarlarını ekleyerek DKE'yi istemciniz için etkinleştirin:

```console
   [HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\flighting]
   "DoubleKeyProtection"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\flighting]
   "DoubleKeyProtection"=dword:00000001
```

## <a name="migrate-protected-files-from-hyok-labels-to-dke-labels"></a>Korumalı dosyaları HYOK etiketlerinden DKE etiketlerine geçirme

DKE'yi ayarlamayı bitirdikten sonra, HYOK etiketlerini kullanarak koruma altına alan içeriği DKE etiketlerine geçirebilirsiniz. Geçiş yapmak için AIP tarayıcısını kullan kullanırsiniz. Tarayıcıyı kullanmaya başlamak için bkz. [Azure Information Protection birleşik etiketleme tarayıcısı nedir?](/azure/information-protection/deploy-aip-scanner).

İçeriği geçirilmezse, HYOK korumalı içeriğiniz etkilenmeden kalır.

## <a name="other-deployment-options"></a>Diğer dağıtım seçenekleri

Son derece düzenlemeye tabi endüstrilerde yer alan bazı müşteriler için, yazılım tabanlı anahtarlar kullanan bu standart başvuru uygulamasının gelişmiş uyumluluk yükümlülükleri ve müşterilerimizin yerine getirilene kadar yeterli olmadığını fark ediyoruz. DKE hizmetsinde aşağıdakiler gibi gelişmiş anahtar yönetimi seçeneklerini desteklemek için üçüncü taraf donanım güvenlik modülü (HSM) satıcılarla ortaklıkdık:

- [Güven](https://www.entrust.com/digital-security/hsm/services/packaged-services/double-key-encryption-integration#:~:text=Entrust%20Double%20Key%20Encryption%20for%20Microsoft%20AIP%2C%20offered,trust%20for%20the%20protection%20of%20sensitive%20cryptographic%20keys.)

- [Thales](https://cpl.thalesgroup.com/cloud-security/encryption/double-key-encryption)

Pazar için DKE HSM çözümleri hakkında daha fazla bilgi ve rehberlik için bu satıcılara doğrudan ulaşabilirsiniz.
