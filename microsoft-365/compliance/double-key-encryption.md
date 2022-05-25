---
title: Çift Anahtarlı Şifreleme (DKE)
description: DKE, anahtarınızın tam denetimini korurken yüksek oranda hassas verileri korumanıza olanak tanır.
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
ms.openlocfilehash: 74194d4bca71350c180799e071936b75044a6b4e
ms.sourcegitcommit: 612ce4d15d8a2fdbf7795393b50af477d81b6139
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65663700"
---
# <a name="double-key-encryption"></a>Çift Anahtarlı Şifreleme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> *Şunlar için geçerlidir: Microsoft Purview Çift Anahtar Şifrelemesi, [Microsoft Purview](https://www.microsoft.com/microsoft-365/business/compliance-management), [Azure Information Protection](https://azure.microsoft.com/pricing/)*
>
> *Yönergeler: [Windows için Azure Information Protection birleşik etiketleme istemcisi](/azure/information-protection/faqs#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

> *Hizmet açıklaması: [Microsoft Purview](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Çift Anahtar Şifrelemesi (DKE), korumalı içeriğe erişmek için iki anahtarı birlikte kullanır. Microsoft bir anahtarı Microsoft Azure depolar ve siz diğer anahtarı tutarsınız. Anahtarlarınızdan birinin tam denetimini Çift Anahtar Şifrelemesi hizmetini kullanarak sürdürebilirsiniz. Son derece hassas içeriğinize Azure Information Protection birleşik etiketleme istemcisini kullanarak koruma uygularsınız.

Çift Anahtarlı Şifreleme hem bulut hem de şirket içi dağıtımları destekler. Bu dağıtımlar, korumalı verileri depoladığınız her yerde şifrelenmiş verilerin donuk kalmasını sağlamaya yardımcı olur.

Varsayılan, bulut tabanlı kiracı kök anahtarları hakkında daha fazla bilgi için bkz. [Azure Information Protection kiracı anahtarınızı planlama ve uygulama](/azure/information-protection/plan-implement-tenant-key).

## <a name="when-your-organization-should-adopt-dke"></a>Kuruluşunuzun DKE'ye ne zaman sahip olması gerekir?

Çift Anahtarlı Şifreleme, en katı koruma gereksinimlerine tabi olan en hassas verilerinize yöneliktir. DKE tüm veriler için tasarlanmamıştır. Genel olarak, genel verilerinizin yalnızca küçük bir bölümünü korumak için Çift Anahtar Şifrelemesi kullanacaksınız. Dağıtmadan önce bu çözümle ilgili olarak doğru verileri tanımlamak için gereken özeni göstermelisiniz. Bazı durumlarda kapsamınızı daraltmanız ve verilerinizin çoğu için Microsoft tarafından yönetilen anahtarlarla Microsoft Purview Bilgi Koruması veya BYOK gibi diğer çözümleri kullanmanız gerekebilir. Bu çözümler, gelişmiş korumalara ve mevzuat gereksinimlerine tabi olmayan belgeler için yeterlidir. Ayrıca, bu çözümler en güçlü Office 365 hizmetlerini( DKE şifreli içerikle kullanamazsınız) kullanmanıza olanak tanır. Örneğin:

- Kötü amaçlı yazılımdan koruma ve ekte görünürlük gerektiren istenmeyen postalar da dahil olmak üzere aktarım kuralları
- Microsoft Delve
- Ediscovery
- İçerik arama ve dizin oluşturma
- birlikte yazma işlevselliği dahil Office Web Apps

Microsoft Bilgi Koruması (MIP) SDK'sı aracılığıyla DKE ile tümleştirilmemiş tüm dış uygulamalar veya hizmetler şifrelenmiş veriler üzerinde eylem gerçekleştiremez.

Microsoft Bilgi Koruması SDK 1.7+ çift anahtarlı şifrelemeyi destekler. SDK'mızla tümleşen uygulamalar, yeterli izinlere ve tümleştirmelere sahip bu veriler üzerinde neden olabilir.

Hassas verilerinizin çoğunu korumak için Microsoft Purview Bilgi Koruması özelliklerini (sınıflandırma ve etiketleme) kullanın ve yalnızca görev açısından kritik verileriniz için DKE kullanın. Çift Anahtarlı Şifreleme, Finansal hizmetler ve Sağlık hizmetleri gibi yüksek düzeyde düzenlenmiş sektörlerdeki hassas veriler için geçerlidir.

Kuruluşunuz aşağıdaki gereksinimlerden herhangi birine sahipse, içeriğinizin güvenliğini sağlamaya yardımcı olması için DKE'yi kullanabilirsiniz:

- Korumalı içeriğin şifresini her koşulda *yalnızca sizin* çözebileceğinizden emin olmak istiyorsunuz.
- Microsoft'un korumalı verilere kendi başına erişmesini istemezsiniz.
- Anahtarları coğrafi sınır içinde tutmak için yasal gereksinimlere sahipsiniz. Veri şifreleme ve şifre çözme için tuttuğunuz tüm anahtarlar veri merkezinizde tutulur.

## <a name="system-and-licensing-requirements-for-dke"></a>DKE için sistem ve lisans gereksinimleri

**Çift Anahtar şifrelemesi** Microsoft 365 E5 ile birlikte gelir. Microsoft 365 E5 lisansınız yoksa [deneme](https://aka.ms/M365E5ComplianceTrial) sürümüne kaydolabilirsiniz. Bu lisanslar hakkında daha fazla bilgi için bkz. [Microsoft 365 güvenlik & uyumluluğu için lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

**Azure Information Protection**. DKE duyarlılık etiketleriyle çalışır ve Azure Information Protection gerektirir.

DKE duyarlılık etiketleri, Office Masaüstü Uygulamaları'ndaki AIP Birleşik Etiketleme istemcisindeki duyarlılık düğmesi aracılığıyla son kullanıcıların kullanımına sunulur. Korumalı belgeleri korumak ve kullanmak istediğiniz her istemci bilgisayara bu önkoşulları yükleyin.

**Windows kurumsal** sürüm 2009 veya üzeri (Word, PowerPoint ve Excel'nin masaüstü sürümleri) için Microsoft Office Uygulamalar.

**Azure Information Protection Birleşik Etiketleme İstemcisi** sürüm 2.7.93.0 veya üzeri. Birleşik Etiketleme istemcisini [Microsoft indirme merkezinden](https://www.microsoft.com/download/details.aspx?id=53018) indirin ve yükleyin.

## <a name="supported-environments-for-storing-and-viewing-dke-protected-content"></a>DKE korumalı içeriği depolamak ve görüntülemek için desteklenen ortamlar

**Desteklenen uygulamalar**. [word, Excel](https://www.microsoft.com/microsoft-365/business/microsoft-365-apps-for-enterprise-product) ve PowerPoint dahil olmak üzere Windows istemciler Kurumlar için Microsoft 365 Uygulamaları.

**Çevrimiçi içerik desteği**. Çift Anahtar Şifrelemesi ile korunan belgeleri ve dosyaları hem Microsoft SharePoint hem de OneDrive İş çevrimiçi olarak depolayabilirsiniz. Bu konumlara yüklemeden önce DKE ile belgeleri ve dosyaları desteklenen uygulamalar tarafından etiketlemeniz ve korumanız gerekir. Şifrelenmiş içeriği e-postayla paylaşabilirsiniz, ancak şifrelenmiş belgeleri ve dosyaları çevrimiçi görüntüleyemezsiniz. Bunun yerine, yerel bilgisayarınızda desteklenen masaüstü uygulamalarını ve istemcilerini kullanarak korumalı içeriği görüntülemeniz gerekir.

## <a name="overview-of-deploying-dke"></a>DKE dağıtımına genel bakış

DKE'yi ayarlamak için bu genel adımları izleyeceksiniz. Bu adımları tamamladıktan sonra, son kullanıcılarınız Çift Anahtar Şifrelemesi ile son derece hassas verilerinizi koruyabilir.

1. DKE hizmetini bu makalede açıklandığı gibi dağıtın.

2. Çift Anahtar Şifrelemesi ile bir etiket oluşturun. Microsoft Purview uyumluluk portalı **Bilgi koruması'na** gidin ve Çift AnahtarLı Şifreleme ile yeni bir etiket oluşturun. Bkz. [Şifreleme uygulamak için duyarlılık etiketlerini kullanarak içeriğe erişimi kısıtlama](./encryption-sensitivity-labels.md).

3. Çift Anahtarlı Şifreleme etiketlerini kullanın. Microsoft Office Duyarlılık şeridinden Çift Tuşla Şifrelenmiş etiketini seçerek verileri koruyun.

Çift AnahtarLı Şifreleme dağıtma adımlarından bazılarını tamamlamanın birkaç yolu vardır. Bu makalede, daha az deneyimli yöneticilerin hizmeti başarıyla dağıtabilmesi için ayrıntılı yönergeler sağlanır. Bunu rahatça yapabilirseniz kendi yöntemlerinizi kullanmayı seçebilirsiniz.

## <a name="deploy-dke"></a>DKE dağıtma

Bu makalede ve dağıtım videosunda DKE hizmetinin dağıtım hedefi olarak Azure kullanılır. Başka bir konuma dağıtıyorsanız, kendi değerlerinizi sağlamanız gerekir.

Bu makaledeki kavramlara adım adım genel bakış görmek için [Çift Anahtar Şifrelemesi dağıtım videosunu](https://youtu.be/vDWfHN_kygg) izleyin. Videonun tamamlanması yaklaşık 18 dakika sürer.

Kuruluşunuz için Çift Anahtar şifrelemesi ayarlamak için bu genel adımları izleyeceksiniz.

1. [DKE hizmeti için yazılım önkoşullarını yükleme](#install-software-prerequisites-for-the-dke-service)
1. [Çift Anahtar şifreleme GitHub deposunu kopyalama](#clone-the-dke-github-repository)
1. [Uygulama ayarlarını değiştirme](#modify-application-settings)
1. [Test anahtarları oluşturma](#generate-test-keys)
1. [Projeyi oluşturma](#build-the-project)
1. [DKE hizmetini dağıtma ve anahtar deposunu yayımlama](#deploy-the-dke-service-and-publish-the-key-store)
1. [Dağıtımınızı doğrulama](#validate-your-deployment)
1. [Anahtar deponuzu kaydetme](#register-your-key-store)
1. [DKE kullanarak duyarlılık etiketleri oluşturma](#create-sensitivity-labels-using-dke)
1. [İstemcinizde DKE'yi etkinleştirme](#enable-dke-in-your-client)
1. [Korumalı dosyaları HYOK etiketlerinden DKE etiketlerine geçirme](#migrate-protected-files-from-hyok-labels-to-dke-labels)

İşiniz bittiğinde, belgeleri ve dosyaları DKE kullanarak şifreleyebilirsiniz. Bilgi için bkz. [Office dosyalarınıza ve e-postalarınıza duyarlılık etiketleri uygulama](https://support.microsoft.com/office/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).

### <a name="install-software-prerequisites-for-the-dke-service"></a>DKE hizmeti için yazılım önkoşullarını yükleme

Bu önkoşulları DKE hizmetini yüklemek istediğiniz bilgisayara yükleyin.

**.NET Core 3.1 SDK**. [.NET Core 3.1'i İndir'den](https://dotnet.microsoft.com/download/dotnet-core/3.1) SDK'yi indirin ve yükleyin.

**Visual Studio Code**. adresinden [https://code.visualstudio.com/](https://code.visualstudio.com)Visual Studio Code indirin. Yüklendikten sonra Visual Studio Code çalıştırın ve **Uzantıları** **Görüntüle'yi** \> seçin. Bu uzantıları yükleyin.

- Visual Studio Code için C#

- NuGet Paket Yöneticisi

**Git kaynakları**. Aşağıdakilerden birini indirip yükleyin.

- [Git](https://git-scm.com/downloads)

- [GitHub Masaüstü](https://desktop.github.com/)

- [GitHub Enterprise](https://github.com/enterprise)

**Openssl** DKE dağıtıldıktan sonra [test anahtarları oluşturmak](#generate-test-keys) için [OpenSSL](https://slproweb.com/products/Win32OpenSSL.html) yüklü olmalıdır. Ortam değişkenleri yolunuzdan doğru şekilde çağırdığınızdan emin olun. Örneğin, ayrıntılar için adresinde [https://www.osradar.com/install-openssl-windows/](https://www.osradar.com/install-openssl-windows/) "Yükleme dizinini PATH'e ekleme" bölümüne bakın.

### <a name="clone-the-dke-github-repository"></a>DKE GitHub deposunu kopyalama

Microsoft, DKE kaynak dosyalarını bir GitHub deposunda sağlar. Projeyi kuruluşunuzun kullanımı için yerel olarak oluşturmak üzere depoyu klonlarsınız. DKE GitHub deposu konumunda [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService)bulunur.

Aşağıdaki yönergeler deneyimsiz git veya Visual Studio Code kullanıcılarına yöneliktir:

1. Tarayıcınızda adresine gidin: [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService).

2. Ekranın sağ tarafında **Kod'a** tıklayın. Kullanıcı arabirimi sürümünüz bir **Kopyala veya indir** düğmesi gösterebilir. Ardından görüntülenen açılan listede kopyala simgesini seçerek URL'yi panonuza kopyalayın.

    Örneğin:

   > [!div class="mx-imgBorder"]
   > ![GitHub'den Çift Anahtar şifreleme hizmeti deposunu kopyalayın.](../media/dke-clone.png)

3. Visual Studio Code **Komut Paleti** **Görüntüle'yi** \> ve **git: Kopyala'yı** seçin. Listedeki seçeneğe atlamak için, girdileri filtrelemek için yazmaya `git: clone` başlayın ve açılan listeden seçin. Örneğin:

   > [!div class="mx-imgBorder"]
   > ![GIT:Clone seçeneğini Visual Studio Code.](../media/dke-vscode-clone.png)

4. Metin kutusuna Git'ten kopyaladığınız URL'yi yapıştırın ve **GitHub Kopyala'yı** seçin.

5. Görüntülenen **Klasör Seç** iletişim kutusunda, depoyu depolamak için konumu bulun ve seçin. İstemde **Aç'ı** seçin.

    Depo Visual Studio Code açılır ve sol altta geçerli Git dalını görüntüler. Örneğin, dal **ana** olmalıdır. Örneğin:

   ![Ana dalı görüntüleyen Visual Studio Code DKE deposunun ekran görüntüsü.](../media/dke-vscode-main-branch.jpg)

6. Ana dalda değilseniz, bunu seçmeniz gerekir. Visual Studio Code'da dalı seçin ve görüntülenen dallar listesinden **main** öğesini seçin.

   > [!IMPORTANT]
   > Ana dalı seçtiğinizde projeyi oluşturmak için doğru dosyalara sahip olmanız sağlanır. Doğru dalı seçmezseniz dağıtımınız başarısız olur.

Artık DKE kaynak deponuzu yerel olarak ayarladınız. Ardından, kuruluşunuzun [uygulama ayarlarını değiştirin](#modify-application-settings) .

### <a name="modify-application-settings"></a>Uygulama ayarlarını değiştirme

DKE hizmetini dağıtmak için aşağıdaki uygulama ayarları türlerini değiştirmeniz gerekir:

- [Anahtar erişim ayarları](#key-access-settings)
- [Kiracı ve anahtar ayarları](#tenant-and-key-settings)

uygulama ayarlarını appsettings.json dosyasında değiştirirsiniz. Bu dosya, DoubleKeyEncryptionService\src\customer-key-store altında yerel olarak kopyaladığınız DoubleKeyEncryptionService deposunda bulunur. Örneğin, Visual Studio Code aşağıdaki resimde gösterildiği gibi dosyaya göz atabilirsiniz.

![DKE için appsettings.json dosyasını bulma.](../media/dke-appsettingsjson.png)

#### <a name="key-access-settings"></a>Anahtar erişim ayarları

E-postanın mı yoksa rol yetkilendirmenin mi kullanılacağını seçin. DKE aynı anda bu kimlik doğrulama yöntemlerinden yalnızca birini destekler.

- **E-posta yetkilendirmesi**. Kuruluşunuzun anahtarlara erişimi yalnızca e-posta adreslerine göre yetkilendirmesine izin verir.

- **Rol yetkilendirme**. Kuruluşunuzun Active Directory gruplarına göre anahtarlara erişim yetkisi vermesine izin verir ve web hizmetinin LDAP'yi sorgulamasını gerektirir.

##### <a name="to-set-key-access-settings-for-dke-using-email-authorization"></a>E-posta yetkilendirmesini kullanarak DKE için anahtar erişim ayarlarını ayarlamak için

1. **appsettings.json** dosyasını açın ve ayarı bulun`AuthorizedEmailAddress`.

2. Yetkilendirmek istediğiniz e-posta adresini veya adresleri ekleyin. Birden çok e-posta adresini çift tırnak ve virgülle ayırın. Örneğin:

   ```json
   "AuthorizedEmailAddress": ["email1@company.com", "email2@company.com ", "email3@company.com"]
   ```

3. `LDAPPath` Ayarı bulun ve çift tırnak arasındaki metni `If you use role authorization (AuthorizedRoles) then this is the LDAP path.` kaldırın. Çift tırnakları yerinde bırakın. İşiniz bittiğinde ayar şöyle görünmelidir.

   ```json
   "LDAPPath": ""
   ```

4. `AuthorizedRoles` Ayarı bulun ve satırın tamamını silin.

Bu görüntüde **appsettings.json** dosyasının e-posta yetkilendirmesi için doğru biçimlendirilmiş olduğu gösterilmektedir.

   ![E-posta yetkilendirme yöntemini gösteren appsettings.json dosyası.](../media/dke-email-accesssetting.png)

##### <a name="to-set-key-access-settings-for-dke-using-role-authorization"></a>Rol yetkilendirmesini kullanarak DKE için anahtar erişim ayarlarını ayarlamak için

1. **appsettings.json** dosyasını açın ve ayarı bulun`AuthorizedRoles`.

2. Yetkilendirmek istediğiniz Active Directory grup adlarını ekleyin. Birden çok grup adını çift tırnak ve virgülle ayırın. Örneğin:

   ```json
   "AuthorizedRoles": ["group1", "group2", "group3"]
   ```

3. `LDAPPath` Ayarı bulun ve Active Directory etki alanını ekleyin. Örneğin:

   ```json
   "LDAPPath": "contoso.com"
   ```

4. `AuthorizedEmailAddress` Ayarı bulun ve satırın tamamını silin.

Bu görüntüde rol yetkilendirmesi için **appsettings.json** dosyasının doğru biçimlendirilmiş olduğu gösterilmektedir.

   ![rol yetkilendirme yöntemini gösteren appsettings.json dosyası.](../media/dke-role-accesssetting.png)

#### <a name="tenant-and-key-settings"></a>Kiracı ve anahtar ayarları

DKE kiracısı ve anahtar ayarları **appsettings.json** dosyasında bulunur.

##### <a name="to-configure-tenant-and-key-settings-for-dke"></a>DKE için kiracı ve anahtar ayarlarını yapılandırmak için

1. **appsettings.json** dosyasını açın.

2. `ValidIssuers` Ayarı bulun ve değerini kiracı kimliğiniz ile değiştirin`<tenantid>`. Azure portal gidip kiracı özelliklerini görüntüleyerek [kiracı](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties) kimliğinizi bulabilirsiniz. Örneğin:

   ```json
   "ValidIssuers": [
     "https://sts.windows.net/9c99431e-b513-44be-a7d9-e7b500002d4b/"
   ]
   ```

> [!NOTE]
> Anahtar deponuza dış B2B erişimini etkinleştirmek istiyorsanız, bu dış kiracıları da geçerli verenler listesinin bir parçası olarak eklemeniz gerekir.

öğesini `JwtAudience`bulun. değerini DKE hizmetinin çalıştırılacağı makinenin ana bilgisayar adıyla değiştirin `<yourhostname>` . Örneğin:

  > [!IMPORTANT]
  > değerinin `JwtAudience` konağınızın adıyla *tam olarak* eşleşmesi gerekir. Hata ayıklama sırasında **localhost:5001** kullanabilirsiniz. Ancak hata ayıklamayı bitirdiğinizde bu değeri sunucunun ana bilgisayar adına güncelleştirdiğinizden emin olun.

- `TestKeys:Name`. Anahtarınız için bir ad girin. Örneğin: `TestKey1`
- `TestKeys:Id`. Bir GUID oluşturun ve değer olarak `TestKeys:ID` girin. Örneğin, `DCE1CC21-FF9B-4424-8FF4-9914BD19A1BE`. Rastgele bir GUID oluşturmak için [Çevrimiçi GUID Oluşturucu](https://guidgenerator.com/) gibi bir site kullanabilirsiniz.

Bu resimde **appsettings.json** dosyasındaki kiracı ve anahtar ayarları için doğru biçim gösterilmektedir. `LDAPPath` rol yetkilendirmesi için yapılandırıldı.

![appsettings.json dosyasında DKE için doğru kiracı ve anahtar ayarlarını gösterir.](../media/dke-appsettingsjson-tenantkeysettings.png)

### <a name="generate-test-keys"></a>Test anahtarları oluşturma

Uygulama ayarlarınızı tanımladıktan sonra genel ve özel test anahtarları oluşturmaya hazırsınız demektir.

Anahtar oluşturmak için:

1. Windows Başlat menüsü OpenSSL Komut İstemi'ni çalıştırın.

1. Test anahtarlarını kaydetmek istediğiniz klasöre geçin. Bu görevdeki adımları tamamlayarak oluşturduğunuz dosyalar aynı klasörde depolanır.

1. Yeni test anahtarını oluşturun.

   ```console
   openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365
   ```

1. Özel anahtarı oluşturun.

   OpenSSL sürüm 3 veya üstünü yüklediyseniz aşağıdaki komutu çalıştırın:
  
  ```console
  openssl rsa -in key.pem -out privkeynopass.pem -outform PEM -traditional
  ```
  
>  Aksi takdirde aşağıdaki komutu çalıştırın:
>  ```console
>  openssl rsa -in key.pem -out privkeynopass.pem -outform PEM
>  ```

1. Ortak anahtarı oluşturun.

   ```console
   openssl rsa -in key.pem -pubout > pubkeyonly.pem
   ```

1. Metin düzenleyicisinde **pubkeyonly.pem** dosyasını açın. **pubkeyonly.pem** dosyasındaki ilk ve son satırlar `PublicPem` dışındaki tüm içeriği **appsettings.json** dosyasının bölümüne kopyalayın.

1. Metin düzenleyicisinde **privkeynopass.pem** dosyasını açın. **privkeynopass.pem** dosyasındaki ilk ve son satırlar `PrivatePem` dışındaki tüm içeriği **appsettings.json** dosyasının bölümüne kopyalayın.

1. Hem hem de `PublicPem` bölümlerindeki tüm boş alanları ve `PrivatePem` yeni çizgileri kaldırın.

    > [!IMPORTANT]
    > Bu içeriği kopyaladığınızda PEM verilerinin hiçbirini silmeyin.

1. Visual Studio Code'da **Startup.cs** dosyasına göz atın. Bu dosya, DoubleKeyEncryptionService\src\customer-key-store\ altında yerel olarak kopyaladığınız DoubleKeyEncryptionService deposunda bulunur.

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

    Bitiş sonuçları aşağıdakine benzer olmalıdır.

    ![genel önizleme için startup.cs dosyası.](../media/dke-startupcs-usetestkeys.png)

Artık [DKE projenizi oluşturmaya](#build-the-project) hazırsınız.

### <a name="build-the-project"></a>Projeyi oluşturma

DKE projesini yerel olarak oluşturmak için aşağıdaki yönergeleri kullanın:

1. Visual Studio Code DKE hizmet deposunda **Komut Paletini** **Görüntüle'yi** \> seçin ve istemine **build** yazın.

2. Listeden **Görevler: Derleme görevini çalıştır'ı** seçin.

   Herhangi bir derleme görevi bulunamadıysa **, Derleme Görevini Yapılandır'ı** seçin ve aşağıdaki gibi .NET core için bir görev oluşturun.

   ![.NET için eksik derleme görevini yapılandırın.](../media/dke-configurebuildtask.png)

   1. **Şablondan tasks.json oluştur'u** seçin.

      ![DKE şablonundan tasks.json dosyası oluşturun.](../media/dke-createtasksjsonfromtemplate.png)

   2. Şablon türleri listesinden **.NET Core'ı** seçin.

      ![DKE için doğru şablonu seçin.](../media/dke-tasksjsontemplate.png)

   3. Derleme bölümünde **customerkeystore.csproj** dosyasının yolunu bulun. Orada değilse aşağıdaki satırı ekleyin:

      ```json
      "${workspaceFolder}/src/customer-key-store/customerkeystore.csproj",
      ```

   4. Derlemeyi yeniden çalıştırın.

3. Çıkış penceresinde kırmızı hata olmadığını doğrulayın.

   Kırmızı hatalar varsa konsol çıkışını denetleyin. Önceki tüm adımları doğru bir şekilde tamamladığınızdan ve doğru derleme sürümlerinin mevcut olduğundan emin olun.

4. İşlemde hata ayıklamak için **Hata Ayıklamayı Başlat'ı** **çalıştır'ı** \> seçin. Bir ortam seçmeniz istenirse **.NET core'u** seçin.

   .NET core hata ayıklayıcısı genellikle için `https://localhost:5001`başlatılır. Test anahtarınızı görüntülemek için adresine gidin `https://localhost:5001` ve bir eğik çizgi (/) ve anahtarınızın adını ekleyin. Örneğin:

   ```https
   https://localhost:5001/TestKey1
   ```

   Anahtar JSON biçiminde görüntülenmelidir.

Kurulumunuz artık tamamlandı. JwtAudience ayarı için appsettings.json dosyasında keystore'u yayımlamadan önce konak adı değerinin App Service ana bilgisayar adınızla tam olarak eşleştiğinden emin olun. Derleme sorunlarını gidermek için localhost olarak değiştirmiş olabilirsiniz.

### <a name="deploy-the-dke-service-and-publish-the-key-store"></a>DKE hizmetini dağıtma ve anahtar deposunu yayımlama

Üretim dağıtımları için hizmeti üçüncü taraf buluta dağıtın veya [şirket içi bir sistemde yayımlayın](/aspnet/core/tutorials/publish-to-iis?preserve-view=true&tabs=netcore-cli&view=aspnetcore-3.1).

Anahtarlarınızı dağıtmak için diğer yöntemleri tercih edebilirsiniz. Kuruluşunuz için en uygun yöntemi seçin.

Pilot dağıtımlar için Azure'da dağıtım yapabilir ve hemen kullanmaya başlayabilirsiniz.

#### <a name="to-create-an-azure-web-app-instance-to-host-your-dke-deployment"></a>DKE dağıtımınızı barındıracak bir Azure Web App örneği oluşturmak için

Anahtar depoyu yayımlamak için DKE dağıtımınızı barındırmak için bir Azure App Service örneği oluşturacaksınız. Ardından, oluşturulan anahtarlarınızı Azure'da yayımlayacaksınız.

1. Tarayıcınızda [Microsoft Azure portalında](https://ms.portal.azure.com) oturum açın ve **Uygulama Hizmetleri** > **Ekle'ye** gidin.

2. Aboneliğinizi ve kaynak grubunuzu seçin ve örnek ayrıntılarınızı tanımlayın.

   - DKE hizmetini yüklemek istediğiniz bilgisayarın ana bilgisayar adını girin. [**Bunun appsettings.json**](#tenant-and-key-settings) dosyasındaki JwtAudience ayarı için tanımlanan adla aynı olduğundan emin olun. Ad için sağladığınız değer aynı zamanda WebAppInstanceName değeridir.

   - **Yayımla** için **kod** seçin ve **Çalışma zamanı yığını** için **.NET Core 3.1'i** seçin.

   Örneğin:

   > [!div class="mx-imgBorder"]
   > ![App Service ekleyin.](../media/dke-azure-add-app-service.png)

3. Sayfanın alt kısmında **Gözden geçir + oluştur'u** ve ardından **Ekle'yi** seçin.

4. Oluşturulan anahtarlarınızı yayımlamak için aşağıdakilerden birini yapın:

   - [ZipDeployUI aracılığıyla yayımlama](#publish-via-zipdeployui)
   - [FTP aracılığıyla yayımlama](#publish-via-ftp)
   - [Visual Studio 2019 veya üzeri aracılığıyla yayımlama](/aspnet/core/tutorials/)

#### <a name="publish-via-zipdeployui"></a>ZipDeployUI aracılığıyla yayımlama

1. `https://<WebAppInstanceName>.scm.azurewebsites.net/ZipDeployUI` adresine gidin.

   Örneğin: `https://dkeservice.scm.azurewebsites.net/ZipDeployUI`

2. Anahtar deposunun kod tabanında **customer-key-store\src\customer-key-store** klasörüne gidin ve bu klasörün **customerkeystore.csproj** dosyasını içerdiğini doğrulayın.

3. Çalıştır: **dotnet publish**

   Çıkış penceresinde yayımlamanın dağıtıldığı dizin görüntülenir.

   Örneğin: `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

4. Yayımlama dizinindeki tüm dosyaları bir .zip dosyasına gönderin. .zip dosyasını oluştururken, dizindeki tüm dosyaların .zip dosyasının kök düzeyinde olduğundan emin olun.

5. Oluşturduğunuz .zip dosyasını yukarıda açtığınız ZipDeployUI sitesine sürükleyip bırakın. Örneğin: `https://dkeservice.scm.azurewebsites.net/ZipDeployUI`

DKE dağıtılır ve oluşturduğunuz test anahtarlarına göz atabilirsiniz. Aşağıda [Dağıtımınızı doğrulamaya](#validate-your-deployment) devam edin.

#### <a name="publish-via-ftp"></a>FTP aracılığıyla yayımlama

1. [Yukarıda](#deploy-the-dke-service-and-publish-the-key-store) oluşturduğunuz App Service Bağlan.

   Tarayıcınızda: **Azure portal** >  **App Service** >  **Deployment Center** > **El ile Dağıtım** > **FTP** > **Panosu'na** gidin.

2. Görüntülenen bağlantı dizelerini yerel bir dosyaya kopyalayın. Web App Service bağlanmak ve FTP aracılığıyla dosyaları karşıya yüklemek için bu dizeleri kullanacaksınız.

   Örneğin:

   ![FTP panosundan bağlantı dizelerini kopyalayın.](../media/dke-ftp-dashboard.png)

3. Anahtar depolama için kod tabanında **customer-key-store\src\customer-key-store dizinine** gidin.

4. Bu dizinin **customerkeystore.csproj dosyasını içerdiğini** doğrulayın.

5. Çalıştır: **dotnet publish**

   Çıkış, yayımlamanın dağıtıldığı dizini içerir.

   Örneğin: `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

6. Yayımlama dizinindeki tüm dosyaları zip dosyasına gönderin. .zip dosyasını oluştururken, dizindeki tüm dosyaların .zip dosyasının kök düzeyinde olduğundan emin olun.

7. FTP istemcinizden, App Service bağlanmak için kopyaladığınız bağlantı bilgilerini kullanın. Önceki adımda oluşturduğunuz .zip dosyasını Web Uygulamanızın kök dizinine Upload.

DKE dağıtılır ve oluşturduğunuz test anahtarlarına göz atabilirsiniz. Ardından [Dağıtımınızı doğrulayın](#validate-your-deployment).

### <a name="validate-your-deployment"></a>Dağıtımınızı doğrulama

DKE'yi yukarıda açıklanan yöntemlerden birini kullanarak dağıttığınızda dağıtımı ve anahtar deposu ayarlarını doğrulayın.

Çalıştırmak:

```powershell
src\customer-key-store\scripts\key_store_tester.ps1 dkeserviceurl/mykey
```

Örneğin:

```powershell
key_store_tester.ps1 https://mydkeservice.com/mykey
```

Çıkışta hata görünmediğinden emin olun. Hazır olduğunuzda [anahtar deponuzu kaydedin](#register-your-key-store).

Anahtar adı büyük/küçük harfe duyarlıdır. anahtar adını appsettings.json dosyasında göründüğü şekilde girin.

## <a name="register-your-key-store"></a>Anahtar deponuzu kaydetme

Aşağıdaki adımlar DKE hizmetinizi kaydetmenizi sağlar. DKE hizmetinizi kaydetmek, etiket oluşturmaya başlamadan önce DKE'yi dağıtmanın son adımıdır.

DKE hizmetini kaydetmek için:

1. Tarayıcınızda [Microsoft Azure portalını](https://ms.portal.azure.com/) açın ve **Tüm Hizmetler** \> **Kimlik** \> **Uygulaması Kayıtları'na** gidin.

2. **Yeni kayıt'ı** seçin ve anlamlı bir ad girin.

3. Görüntülenen seçeneklerden bir hesap türü seçin.

   onmicrosoft.com gibi özel olmayan bir etki alanıyla **Microsoft Azure** kullanıyorsanız Yalnızca **bu kuruluş dizinindeki hesaplar (yalnızca Microsoft - Tek kiracı)** seçeneğini belirleyin.

   Örneğin:

   > [!div class="mx-imgBorder"]
   > ![Yeni Uygulama Kaydı.](../media/dke-app-registration.png)

4. Sayfanın alt kısmında **Kaydet'i** seçerek yeni Uygulama Kaydı'nı oluşturun.

5. Yeni Uygulama Kaydınızda, sol bölmedeki **Yönet'in** altında **Kimlik Doğrulaması'nı** seçin.

6. **Platform ekle'yi** seçin.

7. **Platformları yapılandır** açılır penceresinde **Web'i** seçin.

8. **Yeniden yönlendirme URI'leri'nin** altında çift anahtarlı şifreleme hizmetinizin URI'sini girin. Hem konak adı hem de etki alanı dahil olmak üzere App Service URL'sini girin.

   Örneğin: `https://mydkeservicetest.com`

   - Girdiğiniz URL, DKE hizmetinizin dağıtıldığı ana bilgisayar adıyla eşleşmelidir.
   - Etki alanı [doğrulanmış bir etki alanı](/azure/active-directory/develop/reference-breaking-changes#appid-uri-in-single-tenant-applications-will-require-use-of-default-scheme-or-verified-domains) olmalıdır.
   - Visual Studio ile yerel olarak test ediyorsanız kullanın`https://localhost:5001`.
   - Her durumda, şema **https** olmalıdır.

   Konak adının App Service ana bilgisayar adınızla tam olarak eşleştiğinden emin olun. Derlemeyle ilgili sorunları gidermek için bunu `localhost` olarak değiştirmiş olabilirsiniz. **appsettings.json** dosyasında bu değer için `JwtAudience`ayarladığınız konak adıdır.

9. **Örtük izin'in** altında **Kimlik belirteçleri** onay kutusunu seçin.

10. Değişikliklerinizi kaydetmek için **Kaydet'i** seçin.

11. Sol bölmede, Uygulama Kimliği URI'si'nin yanındaki **Bir API'yi kullanıma sunma'yı** seçin, hem konak adı hem de etki alanı da dahil olmak üzere App Service URL'nizi girin ve **ardından Ayarla'yı** seçin.

12. Yine **API'yi kullanıma sunma** sayfasında, **bu API tarafından tanımlanan Kapsamlar** alanında **Kapsam ekle'yi** seçin. Yeni kapsamda:

    1. Kapsam adını **user_impersonation** olarak tanımlayın.

    2. Onay verebilen yöneticileri ve kullanıcıları seçin.

    3. Gereken kalan değerleri tanımlayın.

    4. **Kapsam ekle'yi** seçin.

    5. Değişikliklerinizi kaydetmek için üst kısımdaki **Kaydet'i** seçin.

13. Yine **API'yi kullanıma sunma** sayfasındaki **Yetkili istemci uygulamaları** alanında **İstemci uygulaması ekle'yi** seçin.

    Yeni istemci uygulamasında:

    1. İstemci Kimliğini olarak `d3590ed6-52b3-4102-aeff-aad2292ab01c`tanımlayın. Bu değer Microsoft Office istemci kimliğidir ve Office anahtar deponuz için erişim belirteci almasını sağlar.

    2. **Yetkili kapsamlar'ın** altında **user_impersonation** kapsamını seçin.

    3. **Uygulama ekle'yi** seçin.

    4. Değişikliklerinizi kaydetmek için üst kısımdaki **Kaydet'i** seçin.

    5. Bu adımları yineleyin, ancak bu kez istemci kimliğini olarak `c00e9d32-3c8d-4a7d-832b-029040e7db99`tanımlayın. Bu değer, Azure Information Protection birleşik etiketleme istemci kimliğidir.

DKE hizmetiniz artık kayıtlı. [DKE kullanarak etiketler oluşturarak](#create-sensitivity-labels-using-dke) devam edin.

## <a name="create-sensitivity-labels-using-dke"></a>DKE kullanarak duyarlılık etiketleri oluşturma

Microsoft Purview uyumluluk portalı yeni bir duyarlılık etiketi oluşturun ve şifrelemeyi başka türlü yaptığınız gibi uygulayın. **Çift Anahtar Şifrelemesi Kullan'ı** seçin ve anahtarınızın uç nokta URL'sini girin. Sağladığınız anahtar adını appsettings.json dosyasının "TestKeys" bölümüne URL'ye eklemeniz gerekir.

Örneğin: `https://testingdke1.azurewebsites.net/KEYNAME`

> [!div class="mx-imgBorder"]
> ![Microsoft Purview uyumluluk portalı Çift Anahtar Şifrelemesi Kullan'ı seçin.](../media/dke-use-dke.png)

Eklediğiniz tüm DKE etiketleri, Kurumlar için Microsoft 365 Uygulamaları en son sürümlerinde kullanıcılar için görünmeye başlar.

> [!NOTE]
> İstemcilerin yeni etiketlerle yenilenmesi 24 saat kadar sürebilir.

### <a name="enable-dke-in-your-client"></a>İstemcinizde DKE'yi etkinleştirme

Office Insider'sanız DKE sizin için etkinleştirilir. Aksi takdirde, aşağıdaki kayıt defteri anahtarlarını ekleyerek istemciniz için DKE'yi etkinleştirin:

```console
   [HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\flighting]
   "DoubleKeyProtection"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\flighting]
   "DoubleKeyProtection"=dword:00000001
```

## <a name="migrate-protected-files-from-hyok-labels-to-dke-labels"></a>Korumalı dosyaları HYOK etiketlerinden DKE etiketlerine geçirme

İsterseniz, DKE kurulumunu tamamladıktan sonra HYOK etiketlerini kullanarak koruduğun içeriği DKE etiketlerine geçirebilirsiniz. Geçiş yapmak için AIP tarayıcısını kullanacaksınız. Tarayıcıyı kullanmaya başlamak için bkz. [Azure Information Protection birleşik etiketleme tarayıcısı nedir?](/azure/information-protection/deploy-aip-scanner).

İçerik geçirmezseniz, HYOK korumalı içeriğiniz etkilenmez.

## <a name="other-deployment-options"></a>Diğer dağıtım seçenekleri

Yüksek düzeyde düzenlenmiş sektörlerdeki bazı müşteriler için yazılım tabanlı anahtarları kullanan bu standart başvuru uygulamasının, gelişmiş uyumluluk yükümlülüklerini ve gereksinimlerini karşılamak için yeterli olmayabileceğinin farkındayız. DKE hizmetindeki gelişmiş anahtar yönetimi seçeneklerini desteklemek için aşağıdakiler dahil olmak üzere üçüncü taraf donanım güvenlik modülü (HSM) satıcılarıyla iş ortaklığı yaptık:

- [Emanet](https://www.entrust.com/digital-security/hsm/services/packaged-services/double-key-encryption-integration#:~:text=Entrust%20Double%20Key%20Encryption%20for%20Microsoft%20AIP%2C%20offered,trust%20for%20the%20protection%20of%20sensitive%20cryptographic%20keys.)

- [Thales](https://cpl.thalesgroup.com/cloud-security/encryption/double-key-encryption)

Pazar içi DKE HSM çözümleri hakkında daha fazla bilgi ve rehberlik için doğrudan bu satıcılara ulaşın.
