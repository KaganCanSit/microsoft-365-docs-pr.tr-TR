---
title: SharePoint Online ile Office 365 Content Delivery Network (CDN) kullanma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/13/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: SharePoint Online varlıklarınızın teslimini hızlandırmak için Office 365 Content Delivery Network'ün (CDN) nasıl kullanılacağını öğrenin.
ms.openlocfilehash: 19a6ef51c73340c9f048ffa60208a5216a1959db
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66492523"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a>SharePoint Online ile Office 365 Content Delivery Network'i (CDN) kullanma

SharePoint Online sayfalarınız için daha iyi performans sağlamak üzere statik varlıkları barındırmak için yerleşik Office 365 Content Delivery Network'i (CDN) kullanabilirsiniz. Office 365 CDN, statik varlıkları isteyen tarayıcılara daha yakın önbelleğe alarak performansı artırır ve bu da indirmeleri hızlandırmaya ve gecikme süresini azaltmaya yardımcı olur. Ayrıca Office 365 CDN, geliştirilmiş sıkıştırma ve HTTP kanal oluşturma için [HTTP/2 protokollerini](https://en.wikipedia.org/wiki/HTTP/2) kullanır. Office 365 CDN hizmeti, SharePoint Online aboneliğinizin bir parçası olarak dahil edilir.

> [!NOTE]
> Office 365 CDN yalnızca **Üretim** (dünya çapında) bulutundaki kiracılar tarafından kullanılabilir. ABD Hükümeti ve Çin bulutlarındaki kiracılar şu anda Office 365 CDN'yi desteklememektedir.

Office 365 CDN, statik varlıkları birden çok konumda veya _kaynakta_ barındırmanıza ve bunları küresel yüksek hızlı ağlardan sunmanıza olanak sağlayan birden çok CDN'den oluşur. Office 365 CDN'de barındırmak istediğiniz içerik türüne bağlı olarak **genel kaynaklar,** **özel** kaynaklar veya her ikisini birden ekleyebilirsiniz. Genel ve özel kaynaklar arasındaki fark hakkında daha fazla bilgi için bkz. [Her kaynağın genel mi yoksa özel mi olacağını seçme](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) .

![CDN kavramsal diyagramını Office 365.](../media/O365-CDN/o365-cdn-flow-transparent.png "CDN kavramsal diyagramını Office 365")

CDN'lerin çalışma şeklini zaten biliyorsanız, kiracınız için Office 365 CDN'yi etkinleştirmek için yalnızca birkaç adımı tamamlamanız gerekir. Bu konuda nasıl yapılır açıklanmaktadır. Statik varlıklarınızı barındırmaya başlama hakkında bilgi için okumaya devam edin.

> [!TIP]
> Özel kullanım senaryoları için Office 365 ile kullanılabilecek microsoft tarafından barındırılan başka CDN'ler de vardır, ancak Office 365 CDN kapsamının dışında olduklarından bu konuda ele alınmaz. Daha fazla bilgi için bkz. [Diğer Microsoft CDN'leri](content-delivery-networks.md#other-microsoft-cdns).

 **[Office 365 için Ağ planlama ve performans ayarlama'ya](./network-planning-and-performance.md) dönün.**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a>SharePoint Online'da Office 365 CDN ile çalışmaya genel bakış

Kuruluşunuz için Office 365 CDN'sini ayarlamak için şu temel adımları izleyin:

+ [Office 365 CDN dağıtımını planlama](use-microsoft-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  + [CDN'de hangi statik varlıkları barındırmak istediğinizi belirleyin](use-microsoft-365-cdn-with-spo.md#CDNAssets).
  + [Varlıklarınızı nerede depolamak istediğinizi belirleyin](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets). Bu konum bir SharePoint sitesi, kitaplığı veya klasörü olabilir ve _kaynak_ olarak adlandırılır.
  + [Her kaynağın genel mi yoksa özel mi olacağını seçin](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Hem genel hem de özel türlerin birden çok kaynağını ekleyebilirsiniz.

+ PowerShell veya Microsoft 365 için CLI kullanarak CDN'yi ayarlama ve yapılandırma

  + [SharePoint Online Yönetim Kabuğu'nı kullanarak CDN'yi ayarlama ve yapılandırma](use-microsoft-365-cdn-with-spo.md#CDNSetupinPShell)
  + [PnP PowerShell kullanarak CDN'yi ayarlama ve yapılandırma](use-microsoft-365-cdn-with-spo.md#CDNSetupinPnPPosh)
  + [Microsoft 365 için CLI kullanarak CDN'yi ayarlama ve yapılandırma](use-microsoft-365-cdn-with-spo.md#CDNSetupinCLI)

  Bu adımı tamamladığınızda şunları yapacaksınız:

  + Kuruluşunuz için CDN etkinleştirildi.
  + Her kaynağı genel veya özel olarak tanımlayarak kaynaklarınızı eklediniz.

Kurulumu tamamladıktan sonra [Office 365 CDN'yi zaman içinde şu şekilde yönetebilirsiniz](use-microsoft-365-cdn-with-spo.md#CDNManage):

+ Varlıkları ekleme, güncelleştirme ve kaldırma
+ Çıkış noktaları ekleme ve kaldırma
+ CDN ilkelerini yapılandırma
+ Gerekirse CDN'yi devre dışı bırakma

Son olarak, [cdn varlıklarınıza](use-microsoft-365-cdn-with-spo.md#using-your-cdn-assets) hem genel hem de özel kaynaklardan erişme hakkında bilgi edinmek için bkz. CDN varlıklarınızı kullanma.

Yaygın sorunları çözme yönergeleri için bkz. [Office 365 CDN sorunlarını giderme](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting).

## <a name="plan-for-deployment-of-the-office-365-cdn"></a>Office 365 CDN dağıtımını planlama

Office 365 kiracınız için Office 365 CDN'sini dağıtmadan önce, planlama sürecinizin bir parçası olarak aşağıdaki faktörleri göz önünde bulundurmanız gerekir.

  + [CDN'de hangi statik varlıkları barındırmak istediğinizi belirleme](use-microsoft-365-cdn-with-spo.md#CDNAssets)
  + [Varlıklarınızı nerede depolamak istediğinizi belirleme](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets)
  + [Her kaynağın genel mi yoksa özel mi olacağını seçin](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

<a name="CDNAssets"> </a>
### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a>CDN'de hangi statik varlıkları barındırmak istediğinizi belirleme

Genel olarak, CDN'ler en çok _statik varlıkları_ veya çok sık değişmeyen varlıkları barındırmak için etkilidir. İyi bir kural, bu koşulların bazılarını veya tümünü karşılayan dosyaları tanımlamaktır:

+ Sayfa yükleme süreleri üzerinde önemli bir artımlı etkiye sahip olabilecek bir sayfaya eklenmiş statik dosyalar (betikler ve resimler gibi)
+ Yürütülebilir dosyalar ve yükleme dosyaları gibi büyük dosyalar
+ İstemci tarafı kodunu destekleyen kaynak kitaplıkları

Örneğin, site görüntüleri ve betikleri gibi sürekli olarak istenen küçük dosyalar, site işleme performansını önemli ölçüde geliştirebilir ve SharePoint Online sitelerinizi CDN kaynağına eklediğinizde yükü artımlı olarak azaltabilir. Yükleme yürütülebilir dosyaları gibi daha büyük dosyalar CDN'den indirilebilir ve bu dosyalara sık erişilmese bile, sharepoint online sitenizdeki yükün olumlu bir performans etkisi ve daha sonra azaltılması sağlanır.

Dosya başına performans iyileştirmesi, istemcinin en yakın CDN uç noktasına yakınlığı, yerel ağdaki geçici koşullar vb. gibi birçok faktöre bağlıdır. Birçok statik dosya oldukça küçüktür ve Office 365 bir saniyeden kısa bir süre içinde indirilebilir. Ancak, bir web sayfası birkaç saniyelik toplu indirme süresine sahip birçok ekli dosya içerebilir. Bu dosyaların CDN'den sunulması, genel sayfa yükleme süresini önemli ölçüde azaltabilir. Bir örnek için bkz[. CDN hangi performans kazançlarını sağlar?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide)

<a name="CDNStoreAssets"> </a>
### <a name="determine-where-you-want-to-store-your-assets"></a>Varlıklarınızı nerede depolamak istediğinizi belirleme

CDN varlıklarınızı _kaynak_ olarak adlandırılan bir konumdan getirir. Kaynak, URL ile erişilebilen bir SharePoint sitesi, belge kitaplığı veya klasör olabilir. Kuruluşunuz için kaynak belirtirken büyük bir esnekliğe sahip olursunuz. Örneğin, tüm CDN varlıklarınızı yerleştirmek istediğiniz birden çok kaynak veya tek bir çıkış noktası belirtebilirsiniz. Kuruluşunuz için hem genel hem de özel kaynaklardan birini seçebilirsiniz. Çoğu kuruluş ikisinin birleşimini uygulamayı seçecektir.

Kaynaklarınız için klasörler veya belge kitaplıkları gibi yeni kapsayıcılar oluşturabilir ve CDN'den kullanılabilir hale getirmek istediğiniz dosyaları ekleyebilirsiniz. CDN'den kullanılabilir olmasını istediğiniz belirli bir varlık kümeniz varsa ve CDN varlıkları kümesini yalnızca kapsayıcıdaki dosyalarla kısıtlamak istiyorsanız bu iyi bir yaklaşımdır.

Ayrıca kaynak olarak mevcut bir site koleksiyonunu, siteyi, kitaplığı veya klasörü yapılandırabilirsiniz; bu da kapsayıcıdaki tüm uygun varlıkları CDN'den kullanılabilir hale getirir. Var olan bir kapsayıcıyı kaynak olarak eklemeden önce, varlıkları yanlışlıkla anonim erişime veya yetkisiz kullanıcılara sunmamak için içeriklerini ve izinlerini bildiğinizden emin olmanız önemlidir.

Kaynaklarınızdaki içeriği _CDN'den_ dışlamak için CDN ilkeleri tanımlayabilirsiniz. CDN ilkeleri, ortak veya özel kaynaklardaki varlıkları _dosya türü_ ve _site sınıflandırması_ gibi özniteliklere göre dışlar ve ilkede belirttiğiniz CdnType'ın (özel veya genel) tüm çıkış noktalarına uygulanır. Örneğin, birden çok alt site içeren bir siteden oluşan özel bir kaynak eklerseniz, **gizli** olarak işaretlenmiş siteleri dışlamak için bir ilke tanımlayabilirsiniz, böylece bu sınıflandırmaya sahip sitelerden içerik CDN'den sunulmaz. İlke, CDN'ye eklediğiniz _tüm_ özel kaynaklardan gelen içeriğe uygulanır.

Kaynak sayısı ne kadar fazlaysa CDN hizmetinin istekleri işleme süresi üzerindeki etkisinin de o kadar fazla olduğunu unutmayın. Kaynak sayısını mümkün olduğunca sınırlamanızı öneririz.

<a name="CDNOriginChoosePublicPrivate"> </a>
### <a name="choose-whether-each-origin-should-be-public-or-private"></a>Her kaynağın genel mi yoksa özel mi olacağını seçin

Bir kaynağı belirlediğinizde, _bunun genel_ mi yoksa _özel_ mi olacağını belirtirsiniz. Genel kaynaklarda CDN varlıklarına erişim anonimdir ve özel kaynaklardaki CDN içeriği daha fazla güvenlik için dinamik olarak oluşturulan belirteçlerle güvenli hale getirilmiştir. Hangi seçeneği seçerseniz seçin, CdN'nin yönetimi söz konusu olduğunda Microsoft sizin için tüm ağır işi yapar. Ayrıca CDN'yi ayarladıktan ve kaynaklarınızı belirledikten sonra fikrinizi daha sonra değiştirebilirsiniz.

Hem genel hem de özel seçenekler benzer performans kazançları sağlar, ancak her birinde benzersiz öznitelikler ve avantajlar vardır.

Office 365 CDN içindeki **genel** kaynaklara anonim olarak erişilebilir ve barındırılan varlıklara, varlığın URL'sine sahip olan herkes erişebilir. Genel kaynaklardaki içeriğe erişim anonim olduğundan, bunları yalnızca JavaScript dosyaları, betikler, simgeler ve görüntüler gibi hassas olmayan genel içerikleri önbelleğe almak için kullanmanız gerekir.

Office 365 CDN içindeki **özel** kaynaklar, SharePoint Online belge kitaplıkları, siteler ve özel görüntüler gibi kullanıcı içeriğine özel erişim sağlar. Özel kaynaklardaki içeriğe erişim dinamik olarak oluşturulan belirteçlerle güvenli hale getirildiğinden, içeriğe yalnızca özgün belge kitaplığı veya depolama konumu izinleri olan kullanıcılar tarafından erişilebilir. Office 365 CDN'deki özel kaynaklar yalnızca SharePoint Online içeriği için kullanılabilir ve yalnızca SharePoint Online kiracınızdan yeniden yönlendirme yoluyla özel kaynaklardaki varlıklara erişebilirsiniz.

CdN'nin özel bir kaynaktaki varlıklara erişiminin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [Varlıkları özel kaynaklarda kullanma](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins).

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a>Varlıkları genel kaynaklarda barındırmanın öznitelikleri ve avantajları

+ Genel bir kaynakta kullanıma sunulan varlıklara anonim olarak herkes erişebilir.
    > [!IMPORTANT]
    > Kullanıcı bilgilerini içeren veya kuruluşunuza duyarlı olarak kabul edilen kaynakları hiçbir zaman genel bir kaynakta yerleştirmemelisiniz.

+ Bir varlığı genel kaynaktan kaldırırsanız, varlık önbellekten 30 güne kadar kullanılabilir olmaya devam edebilir; ancak 15 dakika içinde CDN'deki varlığa bağlantıları geçersiz kılacak.

+ Stil sayfalarını (CSS dosyaları) genel bir kaynakta barındırdığınızda, kod içinde göreli yolları ve URI'leri kullanabilirsiniz. Bu, arka plan görüntülerinin ve diğer nesnelerin konumuna, onu çağıran varlığın konumuna göre başvurabileceğiniz anlamına gelir.

+ Genel bir kaynağın URL'sini oluşturabilmenize rağmen dikkatli olmalı ve sayfa bağlamı özelliğini kullandığınızdan emin olmalı ve bunu yapmak için yönergeleri izlemelisiniz. Bunun nedeni, CDN'ye erişim kullanılamaz duruma gelirse URL'nin SharePoint Online'da kuruluşunuza otomatik olarak çözümlenmemesi ve bağlantıların bozulmasına ve diğer hatalara neden olmasıdır. URL de değiştirilebilir ve bu nedenle yalnızca geçerli değerine sabit kodlanmamalıdır.

+ Genel kaynaklar için eklenen varsayılan dosya türleri .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, .woff ve .woff2'dir. Ek dosya türleri belirtebilirsiniz.

+ Bir ilkeyi, belirttiğiniz site sınıflandırmaları tarafından tanımlanan varlıkları dışlamak için yapılandırabilirsiniz. Örneğin, "gizli" veya "kısıtlanmış" olarak işaretlenen tüm varlıkları, izin verilen bir dosya türü olsalar ve genel bir kaynakta yer alıyor olsalar bile hariç tutabilirsiniz.

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a>Varlıkları özel kaynaklarda barındırmanın öznitelikleri ve avantajları

+ Özel kaynaklar yalnızca SharePoint Online varlıkları için kullanılabilir.

+ Kullanıcılar varlıklara yalnızca kapsayıcıya erişim izinleri varsa özel bir kaynaktan erişebilir. Bu varlıklara anonim erişim engellenir.

+ Özel kaynaklardaki varlıklar SharePoint Online kiracısından yönlendirilmelidir. Özel CDN varlıklarına doğrudan erişim çalışmıyor.

+ Bir varlığı özel kaynaktan kaldırırsanız, varlık önbellekten bir saate kadar kullanılabilir olmaya devam edebilir; ancak, varlığın kaldırılmasından sonra 15 dakika içinde CDN'deki varlığa bağlantıları geçersiz kılacaktır.

+ Özel kaynaklarda bulunan varsayılan dosya türleri .gif, .ico, .jpeg, .jpg, .js ve .png'dır. Ek dosya türleri belirtebilirsiniz.

+ Genel kaynaklarda olduğu gibi, klasör veya belge kitaplığındaki tüm varlıkları dahil etmek için joker karakterler kullansanız bile belirttiğiniz site sınıflandırmalarıyla tanımlanan varlıkları dışlamak için bir ilke yapılandırabilirsiniz.

Office 365 kiracınızla kullanabileceğiniz Office 365 CDN, genel CDN kavramları ve diğer Microsoft CDN'lerini kullanma hakkında daha fazla bilgi için bkz. [Content Delivery Networks](content-delivery-networks.md).

### <a name="default-cdn-origins"></a>Varsayılan CDN kaynakları

Aksini belirtmediğiniz sürece Office 365 Office 365 CDN'yi etkinleştirdiğinizde sizin için bazı varsayılan çıkış noktaları ayarlar. Başlangıçta sağlamamayı tercih ederseniz, kurulumu tamamladıktan sonra bu kaynakları ekleyebilirsiniz. Varsayılan çıkış noktalarının kurulumunu atlamanın sonuçlarını anlamadığınız ve bunu yapmak için belirli bir nedeniniz olmadığı sürece, CDN'yi etkinleştirdiğinizde bunların oluşturulmasına izin vermelisiniz.

Varsayılan özel CDN kaynakları:

+ \*/userphoto.aspx
+ \*/siteassets

Varsayılan genel CDN kaynakları:

+ \*/masterpage
+ \*/style library
+ \*/clientsideassets

> [!NOTE]
> _clientsideassets_, Aralık 2017'de Office 365 CDN hizmetine eklenen varsayılan bir genel kaynaktır. CDN'deki SharePoint Framework çözümlerinin çalışması için bu kaynağın mevcut olması gerekir. Office 365 CDN'yi Aralık 2017'den önce etkinleştirdiyseniz veya CDN'yi etkinleştirdiğinizde varsayılan kaynak ayarlarını atladıysanız, bu kaynağı el ile ekleyebilirsiniz. Daha fazla bilgi için bkz. [İstemci tarafı web bölümüm veya SharePoint Framework çözümüm çalışmıyor](use-microsoft-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).

<a name="CDNSetupinPShell"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>SharePoint Online Yönetim Kabuğu'nı kullanarak Office 365 CDN'yi ayarlama ve yapılandırma

Bu bölümdeki yordamlar, SharePoint Online'a bağlanmak için SharePoint Online Yönetim Kabuğu'nı kullanmanızı gerektirir. Yönergeler için bkz. [SharePoint Online PowerShell'e bağlanma](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

CdN'yi SharePoint Online Yönetim Kabuğu'nı kullanarak varlıklarınızı SharePoint Online'da barındıracak şekilde ayarlamak ve yapılandırmak için bu adımları tamamlayın.

<details>
  <summary>Genişletmek için tıklayın</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Kuruluşunuzun Office 365 CDN kullanmasını sağlama

Kiracı CDN ayarlarında değişiklik yapmadan önce, Office 365 kiracınızdaki özel CDN yapılandırmasının geçerli durumunu almanız gerekir. SharePoint Online Yönetim Kabuğu'nı kullanarak kiracınıza bağlanın:

```powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

Şimdi kiracıdan CDN durum ayarlarını almak için **Get-SPOTenantCdnEnabled cmdlet'ini** kullanın:

```powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

Belirtilen CdnType için CDN'nin durumu ekrana yansıtılır.

Kuruluşunuzun Office 365 CDN kullanmasını sağlamak için **Set-SPOTenantCdnEnabled cmdlet'ini** kullanın. Kuruluşunuzun ortak kaynakları, özel kaynakları veya her ikisini birden aynı anda kullanmasını sağlayabilirsiniz. CdN'yi, etkinleştirdiğinizde varsayılan çıkış noktalarının kurulumunu atlar şekilde de yapılandırabilirsiniz. Bu kaynakları daha sonra bu konuda açıklandığı gibi ekleyebilirsiniz.

SharePoint Online için Windows PowerShell:

```powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Örneğin, kuruluşunuzun hem genel hem de özel kaynakları kullanmasını sağlamak için aşağıdaki komutu yazın:

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Kuruluşunuzun hem genel hem de özel kaynak kullanmasını sağlamak ancak varsayılan çıkış noktalarını ayarlamayı atlamak için aşağıdaki komutu yazın:

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Office 365 [CDN'yi](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) etkinleştirdiğinizde varsayılan olarak sağlanan kaynaklar ve varsayılan çıkış noktalarının kurulumunu atlamanın olası etkisi hakkında bilgi için bkz. Varsayılan CDN kaynakları.

Kuruluşunuzun genel kaynakları kullanmasını sağlamak için aşağıdaki komutu yazın:

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

Kuruluşunuzun özel çıkış noktalarını kullanmasını sağlamak için aşağıdaki komutu yazın:

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

Bu cmdlet hakkında daha fazla bilgi için bkz. [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

<a name="Office365CDNforSPOFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Office 365 CDN'ye eklenecek dosya türleri listesini değiştirme (İsteğe bağlı)

> [!TIP]
> **Set-SPOTenantCdnPolicy cmdlet'ini** kullanarak dosya türlerini tanımladığınızda, şu anda tanımlanmış olan listenin üzerine yazarsınız. Listeye başka dosya türleri eklemek istiyorsanız, önce cmdlet'ini kullanarak hangi dosya türlerine zaten izin verilip bunları yeni dosya türlerinizle birlikte listeye ekleyin.

CDN'de genel ve özel kaynaklar tarafından barındırılabilir statik dosya türlerini tanımlamak için **Set-SPOTenantCdnPolicy** cmdlet'ini kullanın. Varsayılan olarak, .css, .gif, .jpg ve .js gibi ortak varlık türlerine izin verilir.

SharePoint Online için Windows PowerShell:

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Örneğin, CDN'nin .css ve .png dosyalarını barındırmasını sağlamak için şu komutu girersiniz:

```powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

CDN tarafından şu anda izin verilen dosya türlerini görmek için **Get-SPOTenantCdnPolicies** cmdlet'ini kullanın:

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Bu cmdlet'ler hakkında daha fazla bilgi için bkz. [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) ve [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Office 365 CDN'den dışlamak istediğiniz site sınıflandırmaları listesini değiştirme (İsteğe bağlı)

> [!TIP]
> **Set-SPOTenantCdnPolicy cmdlet'ini** kullanarak site sınıflandırmalarını dışladığınızda, şu anda tanımlanmış olan listenin üzerine yazarsınız. Ek site sınıflandırmalarını dışlamak istiyorsanız, önce hangi sınıflandırmaların zaten dışlandığını öğrenmek için cmdlet'ini kullanın ve ardından bunları yeni sınıflandırmalarınızla birlikte ekleyin.

CDN üzerinden kullanılabilir hale getirmek istemediğiniz site sınıflandırmalarını dışlamak için **Set-SPOTenantCdnPolicy** cmdlet'ini kullanın. Varsayılan olarak, hiçbir site sınıflandırması hariç tutulmaz.

SharePoint Online için Windows PowerShell:

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

Şu anda hangi site sınıflandırmalarının kısıtlandığını görmek için **Get-SPOTenantCdnPolicies** cmdlet'ini kullanın:

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Döndürülecek özellikler _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ ve _ExcludeIfNoScriptDisabled'dır_.

_IncludeFileExtensions_ özelliği, CDN'den sunulacak dosya uzantılarının listesini içerir.

> [!NOTE]
> Varsayılan dosya uzantıları genel ve özel arasında farklıdır.

_ExcludeRestrictedSiteClassifications_ özelliği, CDN'den dışlamak istediğiniz site sınıflandırmalarını içerir. Örneğin, **Gizli** olarak işaretlenmiş siteleri dışlayabilirsiniz, böylece bu sınıflandırmaya sahip sitelerden içerik CDN'den sunulmaz.

_ExcludeIfNoScriptDisabled_ özelliği, site düzeyi _NoScript_ öznitelik ayarlarına göre içeriği CDN'nin dışında tutar. Varsayılan olarak _, NoScript_ özniteliği _Modern_ siteler için **etkin** ve _Klasik_ siteler için **devre dışı** olarak ayarlanır. Bu, kiracı ayarlarınıza bağlıdır.

Bu cmdlet'ler hakkında daha fazla bilgi için bkz. [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) ve [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOOriginPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>Varlıklarınız için kaynak ekleme

Bir kaynak tanımlamak için **Add-SPOTenantCdnOrigin** cmdlet'ini kullanın. Birden çok kaynak tanımlayabilirsiniz. Kaynak, CDN tarafından barındırılmasını istediğiniz varlıkları içeren bir SharePoint kitaplığına veya klasörüne işaret eden bir URL'dir.

> [!IMPORTANT]
> Kullanıcı bilgilerini içeren veya kuruluşunuza duyarlı olarak kabul edilen kaynakları hiçbir zaman genel bir kaynakta yerleştirmemelisiniz.

```powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

_Yol_ değeri, varlıkları içeren kitaplığın veya klasörün göreli yoludur. Göreli yollara ek olarak joker karakterler de kullanabilirsiniz. Kaynaklar, URL'ye önceden eklenen joker karakterleri destekler. Bu, birden çok siteye yayılan kaynaklar oluşturmanıza olanak tanır. Örneğin, tüm sitelerinizin masterpages klasörüne tüm varlıkları CDN'de genel kaynak olarak eklemek için aşağıdaki komutu yazın:

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ Joker karakter değiştirici ***/** yalnızca yolun başında kullanılabilir ve belirtilen URL'nin altındaki tüm URL kesimleriyle eşleşir.
+ Yol bir belge kitaplığına, klasöre veya siteye işaret edebilir. Örneğin, _*/site1_ yolu sitenin altındaki tüm belge kitaplıkları ile eşleşir.

Belirli bir göreli yola sahip bir kaynak ekleyebilirsiniz. Tam yolu kullanarak kaynak ekleyemezsiniz.

Bu örnek, belirli bir sitedeki siteassets kitaplığının özel kaynağını ekler:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Bu örnek, site koleksiyonunun site varlıkları kitaplığına _folder1_ klasörünün özel kaynağını ekler:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

Yolda bir boşluk varsa, yolu çift tırnak içine alabilir veya alanı %20 URL kodlamasıyla değiştirebilirsiniz. Aşağıdaki örnekler, site koleksiyonunun site varlıkları kitaplığında _klasör 1_ klasörünün özel kaynağını ekler:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

Bu komut ve söz dizimi hakkında daha fazla bilgi için bkz. [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

> [!NOTE]
> Özel kaynaklarda, bir kaynaktan paylaşılan varlıkların CDN'den erişilebilmesi için önce yayımlanmış bir ana sürüme sahip olması gerekir.

Komutunu çalıştırdıktan sonra sistem yapılandırmayı veri merkezi genelinde eşitler. Bu işlem 15 dakika kadar sürebilir.

<a name="ExamplePublicOrigin"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Örnek: Ana sayfalarınız ve SharePoint Online stil kitaplığınız için genel kaynak yapılandırma

Normalde, Office 365 CDN'yi etkinleştirdiğinizde bu kaynaklar varsayılan olarak sizin için ayarlanır. Ancak, bunları el ile etkinleştirmek istiyorsanız aşağıdaki adımları izleyin.

+ Stil kitaplığını genel kaynak olarak tanımlamak için **Add-SPOTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ Ana sayfaları genel kaynak olarak tanımlamak için **Add-SPOTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Bu komut ve söz dizimi hakkında daha fazla bilgi için bkz. [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Komutunu çalıştırdıktan sonra sistem yapılandırmayı veri merkezi genelinde eşitler. Bu işlem 15 dakika kadar sürebilir.

<a name="ExamplePrivateOrigin"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Örnek: SharePoint Online için site varlıklarınız, site sayfalarınız ve yayımlama görüntüleriniz için özel bir kaynak yapılandırma

+ Site varlıkları klasörünü özel kaynak olarak tanımlamak için **Add-SPOTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ Site sayfaları klasörünü özel kaynak olarak tanımlamak için **Add-SPOTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ Yayımlama görüntüleri klasörünü özel kaynak olarak tanımlamak için **Add-SPOTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Bu komut ve söz dizimi hakkında daha fazla bilgi için bkz. [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Komutunu çalıştırdıktan sonra sistem yapılandırmayı veri merkezi genelinde eşitler. Bu işlem 15 dakika kadar sürebilir.

<a name="ExamplePrivateOriginSiteCollection"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Örnek: SharePoint Online için site koleksiyonu için özel kaynak yapılandırma

Site koleksiyonunu özel kaynak olarak tanımlamak için **Add-SPOTenantCdnOrigin** cmdlet'ini kullanın. Örneğin:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Bu komut ve söz dizimi hakkında daha fazla bilgi için bkz. [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Komutunu çalıştırdıktan sonra sistem yapılandırmayı veri merkezi genelinde eşitler. SharePoint Online kiracısı CDN hizmetine bağlanırken beklenen _bir Yapılandırma beklemede_ iletisi görebilirsiniz. Bu işlem 15 dakika kadar sürebilir.

<a name="CDNManage"> </a>
### <a name="manage-the-office-365-cdn"></a>Office 365 CDN'sini yönetme

CDN'yi ayarladıktan sonra, içeriği güncelleştirdikçe veya gereksinimleriniz değiştikçe, bu bölümde açıklandığı gibi yapılandırmanızda değişiklikler yapabilirsiniz.

<a name="Office365CDNforSPOaddremoveasset"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Office 365 CDN'sinden varlık ekleme, güncelleştirme veya kaldırma

Kurulum adımlarını tamamladıktan sonra yeni varlıklar ekleyebilir ve mevcut varlıkları istediğiniz zaman güncelleştirebilir veya kaldırabilirsiniz. Kaynak olarak tanımladığınız klasör veya SharePoint kitaplığındaki varlıklarda değişikliklerinizi yapmanız yeter. Yeni bir varlık eklerseniz, hemen CDN aracılığıyla kullanılabilir. Ancak, varlığı güncelleştirirseniz yeni kopyanın yayılması ve CDN'de kullanılabilir duruma gelmesi 15 dakika kadar sürer.

Kaynağın konumunu almanız gerekiyorsa **Get-SPOTenantCdnOrigins** cmdlet'ini kullanabilirsiniz. Bu cmdlet'in nasıl kullanılacağı hakkında bilgi için bkz. [Get-SPOTenantCdnOrigins](/powershell/module/sharepoint-online/Get-SPOTenantCdnOrigins).

<a name="Office365CDNforSPORemoveOriginPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Office 365 CDN'den bir kaynağı kaldırma

Kaynak olarak tanımladığınız bir klasöre veya SharePoint kitaplığına erişimi kaldırabilirsiniz. Bunu yapmak için **Remove-SPOTenantCdnOrigin** cmdlet'ini kullanın.

```powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Bu cmdlet'in nasıl kullanılacağı hakkında bilgi için bkz [. Remove-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Remove-SPOTenantCdnOrigin).

<a name="Office365CDNforSPOModifyOrigin"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Office 365 CDN'de bir kaynağı değiştirme

Oluşturduğunuz bir kaynağı değiştiremezsiniz. Bunun yerine, kaynağı kaldırın ve sonra yenisini ekleyin. Daha fazla bilgi için bkz. [Office 365 CDN'den bir kaynağı kaldırmak](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPosh) [için ve Varlıklarınız için kaynak eklemek için](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Office 365 CDN'yi devre dışı bırakma

Kuruluşunuzda CDN'yi devre dışı bırakmak için **Set-SPOTenantCdnEnabled cmdlet'ini** kullanın. CDN için hem genel hem de özel kaynakları etkinleştirdiyseniz, cmdlet'i aşağıdaki örneklerde gösterildiği gibi iki kez çalıştırmanız gerekir.

CDN'de genel kaynak kullanımını devre dışı bırakmak için aşağıdaki komutu girin:

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

CDN'de özel çıkış noktalarının kullanımını devre dışı bırakmak için aşağıdaki komutu girin:

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

Bu cmdlet hakkında daha fazla bilgi için bkz. [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

</details>

<a name="CDNSetupinPnPPosh"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-pnp-powershell"></a>PnP PowerShell kullanarak Office 365 CDN'yi ayarlama ve yapılandırma

Bu bölümdeki yordamlar, SharePoint Online'a bağlanmak için PnP PowerShell kullanmanızı gerektirir. Yönergeler için bkz. [PnP PowerShell'i kullanmaya başlama](https://github.com/SharePoint/PnP-PowerShell#getting-started).

CDN'yi PnP PowerShell kullanarak varlıklarınızı SharePoint Online'da barındıracak şekilde ayarlamak ve yapılandırmak için bu adımları tamamlayın.

<details>
  <summary>Genişletmek için tıklayın</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Kuruluşunuzun Office 365 CDN kullanmasını sağlama

Kiracı CDN ayarlarında değişiklik yapmadan önce, Office 365 kiracınızdaki özel CDN yapılandırmasının geçerli durumunu almanız gerekir. PnP PowerShell kullanarak kiracınıza bağlanın:

```powershell
Connect-PnPOnline -Url https://contoso-admin.sharepoint.com -UseWebLogin
```

Şimdi kiracıdan CDN durum ayarlarını almak için **Get-PnPTenantCdnEnabled cmdlet'ini** kullanın:

```powershell
Get-PnPTenantCdnEnabled -CdnType <Public | Private>
```

Belirtilen CdnType için CDN'nin durumu ekrana yansıtılır.

Kuruluşunuzun Office 365 CDN kullanmasını sağlamak için **Set-PnPTenantCdnEnabled cmdlet'ini** kullanın. Kuruluşunuzun ortak kaynakları, özel kaynakları veya her ikisini aynı anda kullanmasını sağlayabilirsiniz. CdN'yi, etkinleştirdiğinizde varsayılan çıkış noktalarının kurulumunu atlar şekilde de yapılandırabilirsiniz. Bu kaynakları daha sonra bu konuda açıklandığı gibi ekleyebilirsiniz.

PnP PowerShell'de:

```powershell
Set-PnPTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Örneğin, kuruluşunuzun hem genel hem de özel kaynakları kullanmasını sağlamak için aşağıdaki komutu yazın:

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true
```

Kuruluşunuzun hem genel hem de özel kaynak kullanmasını sağlamak ancak varsayılan çıkış noktalarını ayarlamayı atlamak için aşağıdaki komutu yazın:

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Office 365 [CDN'yi](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) etkinleştirdiğinizde varsayılan olarak sağlanan kaynaklar ve varsayılan çıkış noktalarının kurulumunu atlamanın olası etkisi hakkında bilgi için bkz. Varsayılan CDN kaynakları.

Kuruluşunuzun genel kaynakları kullanmasını sağlamak için aşağıdaki komutu yazın:

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $true
```

Kuruluşunuzun özel çıkış noktalarını kullanmasını sağlamak için aşağıdaki komutu yazın:

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $true
```

Bu cmdlet hakkında daha fazla bilgi için bkz. [Set-PnPTenantCdnEnabled](https://pnp.github.io/powershell/cmdlets/Set-PnPTenantCdnEnabled.html).

<a name="Office365CDNforPnPPoshFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Office 365 CDN'ye eklenecek dosya türleri listesini değiştirme (İsteğe bağlı)

> [!TIP]
> **Set-PnPTenantCdnPolicy cmdlet'ini** kullanarak dosya türlerini tanımladığınızda, şu anda tanımlanmış olan listenin üzerine yazarsınız. Listeye başka dosya türleri eklemek istiyorsanız, önce cmdlet'ini kullanarak hangi dosya türlerine zaten izin verilip bunları yeni dosya türlerinizle birlikte listeye ekleyin.

CDN'de genel ve özel kaynaklar tarafından barındırılabilir statik dosya türlerini tanımlamak için **Set-PnPTenantCdnPolicy** cmdlet'ini kullanın. Varsayılan olarak, .css, .gif, .jpg ve .js gibi ortak varlık türlerine izin verilir.

PnP PowerShell'de:

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Örneğin, CDN'nin .css ve .png dosyalarını barındırmasını sağlamak için şu komutu girersiniz:

```powershell
Set-PnPTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

CDN tarafından şu anda izin verilen dosya türlerini görmek için **Get-PnPTenantCdnPolicies cmdlet'ini** kullanın:

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

Bu cmdlet'ler hakkında daha fazla bilgi için bkz. [Set-PnPTenantCdnPolicy](https://pnp.github.io/powershell/cmdlets/Set-PnPTenantCdnPolicy.html) ve [Get-PnPTenantCdnPolicies](https://pnp.github.io/powershell/cmdlets/Get-PnPTenantCdnPolicies.html).

<a name="Office365CDNforPnPPoshSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Office 365 CDN'den dışlamak istediğiniz site sınıflandırmaları listesini değiştirme (İsteğe bağlı)

> [!TIP]
> **Set-PnPTenantCdnPolicy cmdlet'ini** kullanarak site sınıflandırmalarını dışladığınızda, şu anda tanımlanmış olan listenin üzerine yazarsınız. Ek site sınıflandırmalarını dışlamak istiyorsanız, önce hangi sınıflandırmaların zaten dışlandığını öğrenmek için cmdlet'ini kullanın ve ardından bunları yeni sınıflandırmalarınızla birlikte ekleyin.

CDN üzerinden kullanılabilir hale getirmek istemediğiniz site sınıflandırmalarını dışlamak için **Set-PnPTenantCdnPolicy** cmdlet'ini kullanın. Varsayılan olarak, hiçbir site sınıflandırması hariç tutulmaz.

PnP PowerShell'de:

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications>"
```

Şu anda hangi site sınıflandırmalarının kısıtlandığını görmek için **Get-PnPTenantCdnPolicies cmdlet'ini** kullanın:

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

Döndürülecek özellikler _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ ve _ExcludeIfNoScriptDisabled'dır_.

_IncludeFileExtensions_ özelliği, CDN'den sunulacak dosya uzantılarının listesini içerir.

> [!NOTE]
> Varsayılan dosya uzantıları genel ve özel arasında farklıdır.

_ExcludeRestrictedSiteClassifications_ özelliği, CDN'den dışlamak istediğiniz site sınıflandırmalarını içerir. Örneğin, **Gizli** olarak işaretlenmiş siteleri dışlayabilirsiniz, böylece bu sınıflandırmaya sahip sitelerden içerik CDN'den sunulmaz.

_ExcludeIfNoScriptDisabled_ özelliği, site düzeyi _NoScript_ öznitelik ayarlarına göre içeriği CDN'nin dışında tutar. Varsayılan olarak _, NoScript_ özniteliği _Modern_ siteler için **etkin** ve _Klasik_ siteler için **devre dışı** olarak ayarlanır. Bu, kiracı ayarlarınıza bağlıdır.

Bu cmdlet'ler hakkında daha fazla bilgi için bkz. [Set-PnPTenantCdnPolicy](https://pnp.github.io/powershell/cmdlets/Set-PnPTenantCdnPolicy.html) ve [Get-PnPTenantCdnPolicies](https://pnp.github.io/powershell/cmdlets/Get-PnPTenantCdnPolicies.html).

<a name="Office365CDNforSPOOriginPnPPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>Varlıklarınız için kaynak ekleme

Bir kaynak tanımlamak için **Add-PnPTenantCdnOrigin** cmdlet'ini kullanın. Birden çok kaynak tanımlayabilirsiniz. Kaynak, CDN tarafından barındırılmasını istediğiniz varlıkları içeren bir SharePoint kitaplığına veya klasörüne işaret eden bir URL'dir.

> [!IMPORTANT]
> Kullanıcı bilgilerini içeren veya kuruluşunuza duyarlı olarak kabul edilen kaynakları hiçbir zaman genel bir kaynakta yerleştirmemelisiniz.

```powershell
Add-PnPTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

_Yol_ değeri, varlıkları içeren kitaplığın veya klasörün göreli yoludur. Göreli yollara ek olarak joker karakterler de kullanabilirsiniz. Kaynaklar, URL'ye önceden eklenen joker karakterleri destekler. Bu, birden çok siteye yayılan kaynaklar oluşturmanıza olanak tanır. Örneğin, tüm sitelerinizin masterpages klasörüne tüm varlıkları CDN'de genel kaynak olarak eklemek için aşağıdaki komutu yazın:

```powershell
Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ Joker karakter değiştirici ***/** yalnızca yolun başında kullanılabilir ve belirtilen URL'nin altındaki tüm URL kesimleriyle eşleşir.
+ Yol bir belge kitaplığına, klasöre veya siteye işaret edebilir. Örneğin, _*/site1_ yolu sitenin altındaki tüm belge kitaplıkları ile eşleşir.

Belirli bir göreli yola sahip bir kaynak ekleyebilirsiniz. Tam yolu kullanarak kaynak ekleyemezsiniz.

Bu örnek, belirli bir sitedeki site varlıkları kitaplığının özel kaynağını ekler:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Bu örnek, site koleksiyonunun site varlıkları kitaplığına _folder1_ klasörünün özel kaynağını ekler:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

Yolda bir boşluk varsa, yolu çift tırnak içine alabilir veya alanı %20 URL kodlamasıyla değiştirebilirsiniz. Aşağıdaki örnekler, site koleksiyonunun site varlıkları kitaplığında _klasör 1_ klasörünün özel kaynağını ekler:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

Bu komut ve söz dizimi hakkında daha fazla bilgi için bkz. [Add-PnPTenantCdnOrigin](https://pnp.github.io/powershell/cmdlets/Add-PnPTenantCdnOrigin.html).

> [!NOTE]
> Özel kaynaklarda, bir kaynaktan paylaşılan varlıkların CDN'den erişilebilmesi için önce yayımlanmış bir ana sürüme sahip olması gerekir.

Komutunu çalıştırdıktan sonra sistem yapılandırmayı veri merkezi genelinde eşitler. Bu işlem 15 dakika kadar sürebilir.

<a name="ExamplePublicOriginPnPPosh"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Örnek: Ana sayfalarınız ve SharePoint Online stil kitaplığınız için genel kaynak yapılandırma

Normalde, Office 365 CDN'yi etkinleştirdiğinizde bu kaynaklar varsayılan olarak sizin için ayarlanır. Ancak, bunları el ile etkinleştirmek istiyorsanız aşağıdaki adımları izleyin.

+ Stil kitaplığını genel kaynak olarak tanımlamak için **Add-PnPTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ Ana sayfaları genel kaynak olarak tanımlamak için **Add-PnPTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Bu komut ve söz dizimi hakkında daha fazla bilgi için bkz. [Add-PnPTenantCdnOrigin](https://pnp.github.io/powershell/cmdlets/Add-PnPTenantCdnOrigin.html).

Komutunu çalıştırdıktan sonra sistem yapılandırmayı veri merkezi genelinde eşitler. Bu işlem 15 dakika kadar sürebilir.

<a name="ExamplePrivateOriginPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Örnek: SharePoint Online için site varlıklarınız, site sayfalarınız ve yayımlama görüntüleriniz için özel bir kaynak yapılandırma

+ Site varlıkları klasörünü özel kaynak olarak tanımlamak için **Add-PnPTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ Site sayfaları klasörünü özel kaynak olarak tanımlamak için **Add-PnPTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ Yayımlama görüntüleri klasörünü özel kaynak olarak tanımlamak için **Add-PnPTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Bu komut ve söz dizimi hakkında daha fazla bilgi için bkz. [Add-PnPTenantCdnOrigin](https://pnp.github.io/powershell/cmdlets/Add-PnPTenantCdnOrigin.html).

Komutunu çalıştırdıktan sonra sistem yapılandırmayı veri merkezi genelinde eşitler. Bu işlem 15 dakika kadar sürebilir.

<a name="ExamplePrivateOriginSiteCollectionPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Örnek: SharePoint Online için site koleksiyonu için özel kaynak yapılandırma

Site koleksiyonunu özel kaynak olarak tanımlamak için **Add-PnPTenantCdnOrigin** cmdlet'ini kullanın. Örneğin:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Bu komut ve söz dizimi hakkında daha fazla bilgi için bkz. [Add-PnPTenantCdnOrigin](https://pnp.github.io/powershell/cmdlets/Add-PnPTenantCdnOrigin.html).

Komutunu çalıştırdıktan sonra sistem yapılandırmayı veri merkezi genelinde eşitler. SharePoint Online kiracısı CDN hizmetine bağlanırken beklenen _bir Yapılandırma beklemede_ iletisi görebilirsiniz. Bu işlem 15 dakika kadar sürebilir.

<a name="CDNManagePnPPosh"> </a>
### <a name="manage-the-office-365-cdn"></a>Office 365 CDN'sini yönetme

CDN'yi ayarladıktan sonra, içeriği güncelleştirdikçe veya gereksinimleriniz değiştikçe, bu bölümde açıklandığı gibi yapılandırmanızda değişiklikler yapabilirsiniz.

<a name="Office365CDNforSPOaddremoveassetPnPPosh"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Office 365 CDN'sinden varlık ekleme, güncelleştirme veya kaldırma

Kurulum adımlarını tamamladıktan sonra yeni varlıklar ekleyebilir ve mevcut varlıkları istediğiniz zaman güncelleştirebilir veya kaldırabilirsiniz. Kaynak olarak tanımladığınız klasör veya SharePoint kitaplığındaki varlıklarda değişikliklerinizi yapmanız yeter. Yeni bir varlık eklerseniz, hemen CDN aracılığıyla kullanılabilir. Ancak, varlığı güncelleştirirseniz yeni kopyanın yayılması ve CDN'de kullanılabilir duruma gelmesi 15 dakika kadar sürer.

Kaynağın konumunu almanız gerekiyorsa **Get-PnPTenantCdnOrigin** cmdlet'ini kullanabilirsiniz. Bu cmdlet'in nasıl kullanılacağı hakkında bilgi için bkz. [Get-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/get-pnptenantcdnorigin).

<a name="Office365CDNforSPORemoveOriginPnPPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Office 365 CDN'den bir kaynağı kaldırma

Kaynak olarak tanımladığınız bir klasöre veya SharePoint kitaplığına erişimi kaldırabilirsiniz. Bunu yapmak için **Remove-PnPTenantCdnOrigin cmdlet'ini** kullanın.

```powershell
Remove-PnPTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Bu cmdlet'in nasıl kullanılacağı hakkında bilgi için bkz [. Remove-PnPTenantCdnOrigin](https://pnp.github.io/powershell/cmdlets/Remove-PnPTenantCdnOrigin.html).

<a name="Office365CDNforSPOModifyOriginPnPPosh"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Office 365 CDN'de bir kaynağı değiştirme

Oluşturduğunuz bir kaynağı değiştiremezsiniz. Bunun yerine, kaynağı kaldırın ve sonra yenisini ekleyin. Daha fazla bilgi için bkz. [Office 365 CDN'den bir kaynağı kaldırmak](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPnPPosh) [için ve Varlıklarınız için kaynak eklemek için](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPnPPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Office 365 CDN'yi devre dışı bırakma

Kuruluşunuzda **CDN'yi devre dışı bırakmak için Set-PnPTenantCdnEnabled cmdlet'ini** kullanın. CDN için hem genel hem de özel kaynakları etkinleştirdiyseniz, cmdlet'i aşağıdaki örneklerde gösterildiği gibi iki kez çalıştırmanız gerekir.

CDN'de genel kaynak kullanımını devre dışı bırakmak için aşağıdaki komutu girin:

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $false
```

CDN'de özel çıkış noktalarının kullanımını devre dışı bırakmak için aşağıdaki komutu girin:

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $false
```

Bu cmdlet hakkında daha fazla bilgi için bkz. [Set-PnPTenantCdnEnabled](https://pnp.github.io/powershell/cmdlets/Set-PnPTenantCdnEnabled.html).

</details>

<a name="CDNSetupinCLI"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-using-the-cli-for-microsoft-365"></a>Microsoft 365 için CLI kullanarak Office 365 CDN'yi ayarlama ve yapılandırma

Bu bölümdeki yordamlar, [Microsoft 365 için CLI'yi](https://aka.ms/cli-m365) yüklemenizi gerektirir. Ardından [oturum açma](https://pnp.github.io/cli-microsoft365/cmd/login/) komutunu kullanarak Office 365 kiracınıza bağlanın.

Microsoft 365 için CLI'yı kullanarak CDN'yi varlıklarınızı SharePoint Online'da barındıracak şekilde ayarlamak ve yapılandırmak için bu adımları tamamlayın.

<details>
  <summary>Genişletmek için tıklayın</summary>

### <a name="enable-the-office-365-cdn"></a>Office 365 CDN'yi etkinleştirme

[spo cdn set](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-set/) komutunu kullanarak kiracınızdaki Office 365 CDN'nin durumunu yönetebilirsiniz.

Kiracınızda Office 365 Genel CDN'yi etkinleştirmek için şu komutu yürütür:

```cli
spo cdn set --type Public --enabled true
```

Office 365 SharePoint CDN'sini etkinleştirmek için şunu yürütebilirsiniz:

```cli
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a>Office 365 CDN'nin geçerli durumunu görüntüleme

Belirli bir Office 365 CDN türünün etkin veya devre dışı olup olmadığını denetlemek için [spo cdn get](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-get/) komutunu kullanın.

Office 365 Genel CDN'nin etkinleştirilip etkinleştirilmediğini denetlemek için şunu yürütür:

```cli
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a>Office 365 CDN çıkış noktalarını görüntüleme

Şu anda yapılandırılmış Office 365 Genel CDN çıkış noktalarını görüntülemek için şu komutu çalıştırın:

```cli
spo cdn origin list --type Public
```

[Office 365 CDN'yi](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) etkinleştirdiğinizde varsayılan olarak sağlanan kaynaklar hakkında bilgi için bkz. Varsayılan CDN kaynakları.

### <a name="add-an-office-365-cdn-origin"></a>Office 365 CDN kaynağı ekleme

> [!IMPORTANT]
> Kuruluşunuza duyarlı olarak kabul edilen kaynakları hiçbir zaman genel kaynak olarak yapılandırılmış bir SharePoint belge kitaplığına yerleştirmemelisiniz.

CDN kaynağı tanımlamak için [spo cdn origin add](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-add/) komutunu kullanın. Birden çok kaynak tanımlayabilirsiniz. Kaynak, CDN tarafından barındırılmasını istediğiniz varlıkları içeren bir SharePoint kitaplığına veya klasörüne işaret eden bir URL'dir.

```cli
spo cdn origin add --type [Public | Private] --origin <path>
```

Burada `path` , varlıkları içeren klasörün göreli yoludur. Göreli yollara ek olarak joker karakterler de kullanabilirsiniz.

Tüm sitelerin **Ana Sayfa Galerisi'ndeki** tüm varlıkları genel kaynak olarak eklemek için şunu yürütür:

```cli
spo cdn origin add --type Public --origin */masterpage
```

Belirli bir site koleksiyonu için özel bir kaynak yapılandırmak için şunu yürütebilirsiniz:

```cli
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> CDN kaynağı ekledikten sonra, CDN hizmeti aracılığıyla dosyaları alabilmeniz 15 dakika kadar sürebilir. [Spo cdn kaynak listesi](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-list/) komutunu kullanarak belirli kaynağın zaten etkinleştirilip etkinleştirilmediğini doğrulayabilirsiniz.

### <a name="remove-an-office-365-cdn-origin"></a>Office 365 CDN kaynağını kaldırma

Belirtilen [CDN türünün CDN kaynağını kaldırmak için spo cdn origin remove](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-remove/) komutunu kullanın.

CDN yapılandırmasından genel bir kaynağı kaldırmak için şu komutu yürütür:

```cli
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> CDN kaynağının kaldırılması, herhangi bir belge kitaplığında depolanan ve bu kaynakla eşleşen dosyaları etkilemez. Bu varlıklara SharePoint URL'si kullanılarak başvurulduysa, SharePoint otomatik olarak belge kitaplığını işaret eden özgün URL'ye geri döner. Ancak varlıklara genel CDN URL'si kullanılarak başvurulduysa, kaynağın kaldırılması bağlantıyı bozar ve bunları el ile değiştirmeniz gerekir.

### <a name="modify-an-office-365-cdn-origin"></a>Office 365 CDN kaynağını değiştirme

Mevcut bir CDN kaynağını değiştirmek mümkün değildir. Bunun yerine, komutunu kullanarak `spo cdn origin remove` önceden tanımlanmış CDN kaynağını kaldırmanız ve komutunu kullanarak `spo cdn origin add` yenisini eklemeniz gerekir.

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a>Office 365 CDN'ye eklenecek dosya türlerini değiştirme

Varsayılan olarak, cdn'de aşağıdaki dosya türleri bulunur: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, .woff ve .woff2_. CDN'ye ek dosya türleri eklemeniz gerekiyorsa, [spo cdn ilke kümesi komutunu kullanarak CDN](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-set/) yapılandırmasını değiştirebilirsiniz.

> [!NOTE]
> Dosya türleri listesini değiştirirken, şu anda tanımlanmış olan listenin üzerine yazarsınız. Ek dosya türleri eklemek istiyorsanız, şu anda hangi dosya türlerinin yapılandırıldığını öğrenmek için önce [spo cdn ilke listesi](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-list/) komutunu kullanın.

_JSON_ dosya türünü genel CDN'de yer alan varsayılan dosya türleri listesine eklemek için şunu yürütür:

```cli
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>Office 365 CDN'den dışlamak istediğiniz site sınıflandırmaları listesini değiştirme

CDN üzerinden kullanılabilir hale getirmek istemediğiniz site sınıflandırmalarını dışlamak için [spo cdn ilke kümesi](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-set/) komutunu kullanın. Varsayılan olarak, hiçbir site sınıflandırması hariç tutulmaz.

> [!NOTE]
> Dışlanan site sınıflandırmaları listesini değiştirirken, şu anda tanımlanmış olan listenin üzerine yazarsınız. Ek sınıflandırmaları dışlamak istiyorsanız, şu anda hangi sınıflandırmaların yapılandırıldığını bulmak için önce [spo cdn ilke listesi](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-list/) komutunu kullanın.

_HBI_ olarak sınıflandırılan siteleri genel CDN'nin dışında tutmak için

```cli
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a>Office 365 CDN'yi devre dışı bırakma

Office 365 CDN'yi devre dışı bırakmak için komutunu kullanın`spo cdn set`, örneğin:

```cli
spo cdn set --type Public --enabled false
```

</details>

## <a name="using-your-cdn-assets"></a>CDN varlıklarınızı kullanma

CDN'yi etkinleştirdiğinize ve kaynaklarla ilkeleri yapılandırdığınıza göre, CDN varlıklarınızı kullanmaya başlayabilirsiniz.

Bu bölüm, SharePoint sayfalarınızda ve içeriğinizde CDN URL'lerini nasıl kullanacağınızı anlamanıza yardımcı olur, böylece SharePoint hem genel hem de özel kaynaklardaki varlıklara yönelik istekleri CDN'ye yönlendirir.

+ [CDN varlıklarına bağlantılar güncelleştiriliyor](use-microsoft-365-cdn-with-spo.md#updating-links-to-cdn-assets)
+ [Varlıkları genel kaynaklarda kullanma](use-microsoft-365-cdn-with-spo.md#using-assets-in-public-origins)
+ [Varlıkları özel kaynaklarda kullanma](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins)

İstemci tarafı web bölümlerini barındırmak için CDN'yi kullanma hakkında bilgi için, [Office 365 CDN'den istemci tarafı web bölümünüzü barındırma (Merhaba Dünya bölüm 4) konusuna](/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn) bakın.

> [!NOTE]
> _ClientSideAssets_ klasörünü **özel** CDN kaynak listesine eklerseniz, CDN tarafından barındırılan özel web bölümleri işlenemez. SPFX web bölümleri tarafından kullanılan dosyalar yalnızca genel CDN'yi kullanabilir ve ClientSideAssets klasörü genel CDN için varsayılan bir kaynaktır.

### <a name="updating-links-to-cdn-assets"></a>CDN varlıklarına bağlantılar güncelleştiriliyor

Kaynak öğeye eklediğiniz varlıkları kullanmak için, özgün dosyanın bağlantılarını kaynaktaki dosyanın yoluyla güncelleştirmeniz yeterlidir.

+ Bir kaynakta eklediğiniz varlıkların bağlantılarını içeren sayfayı veya içeriği düzenleyin. Ayrıca, belirli bir varlığın bağlantısını göründüğü her yerde güncelleştirmek istiyorsanız, bir enter sitesi veya site koleksiyonundaki bağlantıları genel olarak aramak ve değiştirmek için çeşitli yöntemlerden birini de kullanabilirsiniz.
+ Kaynaktaki bir varlığa yönelik her bağlantı için yolu CDN kaynağındaki dosyanın yoluyla değiştirin. Göreli yolları kullanabilirsiniz.
+ Sayfayı veya içeriği kaydedin.

Örneğin, _/site/site/CDN_origins/_ public/ belge kitaplığı klasörüne kopyaladığınız _/site/_ SiteAssets/images/image.pnggörüntüsünü göz önünde bulundurun. CDN varlığını kullanmak için, yeni URL _/site/CDN_origins/public/image.png_ yapmak için, görüntü dosyası konumunun özgün yolunu kaynağın yoluyla değiştirin.

Göreli yol yerine varlığın tam URL'sini kullanmak istiyorsanız bağlantıyı şöyle yapın:

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> Genel olarak, URL'leri doğrudan CDN'deki varlıklara sabit kodlamamalısınız. Ancak, gerekirse genel kaynaklardaki varlıklar için URL'leri el ile oluşturabilirsiniz. Daha fazla bilgi için bkz. [Ortak varlıklar için SABIT kodlama CDN URL'leri](use-microsoft-365-cdn-with-spo.md#constructing-cdn-urls-for-public-assets).

Varlıkların CDN'den sunulduğunun nasıl doğrulandığı hakkında bilgi edinmek için Office 365 [CDN sorunlarını giderme](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting) bölümünde [varlıkların CDN tarafından sunulduğundan emin Nasıl yaparım? onaylayın](use-microsoft-365-cdn-with-spo.md#CDNConfirm).

### <a name="using-assets-in-public-origins"></a>Varlıkları genel kaynaklarda kullanma

SharePoint Online'daki **Yayımlama özelliği** , ortak kaynaklarda depolanan varlıkların URL'lerini otomatik olarak CDN eşdeğerlerine yeniden yazar, böylece varlıklar SharePoint yerine CDN hizmetinden sunulur.

Kaynağınız Yayımlama özelliği etkinleştirilmiş bir sitedeyse ve CDN'ye boşaltmak istediğiniz varlıklar aşağıdaki kategorilerden birindeyse, varlığın bir CDN ilkesi tarafından dışlanmaması koşuluyla SharePoint kaynaktaki varlıklar için URL'leri otomatik olarak yeniden yazar.

Aşağıda, SharePoint Yayımlama özelliği tarafından hangi bağlantıların otomatik olarak yeniden yazıldığına genel bir bakış sağlanır:

+ Klasik yayımlama sayfası HTML yanıtlarında IMG/LINK/CSS URL'leri
  + Bu, bir sayfanın HTML içeriğine yazarlar tarafından eklenen görüntüleri içerir
+ Resim Kitaplığı Slayt Gösterisi web bölümü resim URL'leri
+ SPList REST API'sindeki görüntü alanları (RenderListDataAsStream) sonuçları
  + Alanların virgülle ayrılmış listesini sağlamak için _ImageFieldsToTryRewriteToCdnUrls_ yeni özelliğini kullanın
  + Köprü alanlarını ve PublishingImage alanlarını destekler
+ SharePoint resim işlemeleri

Aşağıdaki diyagramda, SharePoint genel bir kaynaktan varlıklar içeren bir sayfa için istek aldığında iş akışı gösterilmektedir.

![İş akışı diyagramı: Office 365 CDN varlıklarını genel bir kaynaktan alma.](../media/O365-CDN/o365-cdn-public-steps-transparent.png "İş Akışı: Genel bir kaynaktan Office 365 CDN varlıklarını alma")

> [!TIP]
> Sayfadaki belirli URL'ler için otomatik yeniden yazmayı devre dışı bırakmak istiyorsanız, sayfayı kullanıma alabilir ve sorgu dizesi parametresini ekleyebilirsiniz **? Devre dışı bırakmak istediğiniz her bağlantının sonuna doğru NoAutoReWrites=true** .

#### <a name="constructing-cdn-urls-for-public-assets"></a>Ortak varlıklar için CDN URL'leri oluşturma

_Yayımlama_ özelliği genel kaynak için etkinleştirilmemişse veya varlık CDN hizmetinin otomatik yeniden yazma özelliği tarafından desteklenen bağlantı türlerinden biri değilse, varlıkların CDN konumuna URL'leri el ile oluşturabilir ve içeriğinizde bu URL'leri kullanabilirsiniz.

> [!NOTE]
> URL'nin son bölümünü oluşturan gerekli erişim belirteci kaynağın istendiği anda oluşturulduğundan, CDN URL'lerini özel bir kaynaktaki varlıklara sabit kodlayamaz veya oluşturamazsınız. Genel CDN'nin URL'sini oluşturabilirsiniz ve değiştirilebilir olduğundan URL sabit kodlanmamalıdır.

Genel CDN varlıkları için URL biçimi aşağıdaki gibi görünür:

```http
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

**TenantHostName** değerini kiracı adınız ile değiştirin. Örneğin:

```http
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

> [!NOTE]
> "" sabit kodlamasıhttps://publiccdn.sharepointonline.com yerine ön eki oluşturmak için sayfa bağlamı özelliği kullanılmalıdır. URL değiştirilebilir ve sabit kodlanmamalıdır. Klasik SharePoint Online ile görüntüleme şablonları kullanıyorsanız, URL'nin ön eki için görüntü şablonunuzda "window._spPageContextInfo.publicCdnBaseUrl" özelliğini kullanabilirsiniz. Modern ve klasik SharePoint için SPFx web bölümleriyseniz "this.context.pageContext.legacyPageContext.publicCdnBaseUrl" özelliğini kullanabilirsiniz. Bu, değiştirildiğinde uygulamanızın onunla güncelleştirilmesi için ön eki sağlar. SPFx örneği olarak, URL "this.context.pageContext.legacyPageContext.publicCdnBaseUrl" + "/" + "host" + "/" + "öğe için relativeURL" özelliği kullanılarak oluşturulabilir. Lütfen [1. sezon performans serisinin](https://aka.ms/sppnp-perfvideos) bir parçası olan [İstemci tarafı kodunda CDN kullanma](https://youtu.be/IH1RbQlbhIA) konusuna bakın


### <a name="using-assets-in-private-origins"></a>Varlıkları özel kaynaklarda kullanma

Varlıkları özel kaynaklarda kullanmak için ek yapılandırma gerekmez. SharePoint Online, özel kaynaklardaki varlıklar için URL'leri otomatik olarak yeniden yazar, böylece bu varlıklara yönelik istekler her zaman CDN'den sunulur. Bu URL'ler, varlığın istendiği anda SharePoint Online tarafından otomatik olarak oluşturulması gereken belirteçler içerdiğinden, özel kaynaklarda CDN varlıklarına URL'leri el ile oluşturamazsınız.

Özel kaynaklardaki varlıklara erişim, aşağıdaki bölümlerde açıklanan uyarılarla, kaynak üzerindeki kullanıcı izinlerine göre dinamik olarak oluşturulan belirteçlerle korunur. Kullanıcıların cdn'nin içerik işlemesi için kaynaklara en azından **okuma** erişimine sahip olması gerekir.

Aşağıdaki diyagramda, SharePoint özel bir kaynaktan varlıklar içeren bir sayfa için istek aldığında iş akışı gösterilmektedir.

![İş akışı diyagramı: CdN varlıklarını özel bir kaynaktan Office 365 alma.](../media/O365-CDN/o365-cdn-private-steps-transparent.png "İş Akışı: Özel bir kaynaktan Office 365 CDN varlıklarını alma")

#### <a name="token-based-authorization-in-private-origins"></a>Özel kaynaklarda belirteç tabanlı yetkilendirme

Office 365 CDN'sindeki özel kaynaklardaki varlıklara erişim, SharePoint Online tarafından oluşturulan belirteçler tarafından verilir. Kaynak tarafından belirlenen klasöre veya kitaplığa erişim izni olan kullanıcılara, izin düzeyine göre kullanıcının dosyaya erişmesine izin veren belirteçler otomatik olarak verilir. Bu erişim belirteçleri, belirteç yeniden yürütme saldırılarını önlemeye yardımcı olmak için oluşturulduktan sonra 30 ile 90 dakika boyunca geçerlidir.

Erişim belirteci oluşturulduktan sonra, SharePoint Online istemciye iki yetkilendirme parametresi _eat_ (kenar yetkilendirme belirteci) ve _yulaf_ (kaynak yetkilendirme belirteci) içeren özel bir URI döndürür. Her belirtecin yapısı _,<'>__<'secure signature'>zaman biçimindeki süre sonu süresidir_. Örneğin:

```http
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> Belirteci bulunduran herkes CDN'deki kaynağa erişebilir. Ancak, bu erişim belirteçlerini içeren URL'ler yalnızca HTTPS üzerinden paylaşılır, bu nedenle belirtecin süresi dolmadan önce URL son kullanıcı tarafından açıkça paylaşılmadığı sürece, varlığa yetkisiz kullanıcılar erişemez.

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a>Özel kaynaklardaki varlıklar için öğe düzeyi izinleri desteklenmez

SharePoint Online'ın özel kaynaklardaki varlıklar için öğe düzeyinde izinleri desteklemediğini unutmayın. Örneğin, konumunda `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`bulunan bir dosya için, kullanıcılar aşağıdaki koşullar göz önünde bulundurularak dosyaya etkin erişime sahiptir:

|Kullanıcı  |İzinler  |Etkin erişim  |
|---------|---------|---------|
|Kullanıcı 1     |Klasör1'e erişimi var         |CDN'den image1.jpg erişebilir         |
|Kullanıcı 2     |Klasör1'e erişimi yok         |CDN'den image1.jpg erişilemiyor         |
|Kullanıcı 3     |klasör1'e erişimi yoktur, ancak SharePoint Online'da image1.jpg erişim için açık izin verilir         |Varlık image1.jpg doğrudan SharePoint Online'dan erişebilir, ancak CDN'den erişemez         |
|Kullanıcı 4     |Klasör1'e erişimi var, ancak SharePoint Online'da image1.jpg erişimi açıkça reddedildi         |SharePoint Online'dan varlığa erişilemiyor, ancak SharePoint Online'da dosyaya erişimi reddedilse de varlığa CDN'den erişebilir         |

<a name="CDNTroubleshooting"></a>

## <a name="troubleshooting-the-office-365-cdn"></a>Office 365 CDN sorunlarını giderme

<a name="CDNConfirm"></a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a>Varlıkların CDN tarafından sunulduğundan emin Nasıl yaparım??

Sayfaya CDN varlıklarına bağlantılar ekledikten sonra, sayfaya göz atarak, görüntü işlendikten sonra resme sağ tıklayarak ve görüntü URL'sini gözden geçirerek varlığın CDN'den sunulduğundan emin olabilirsiniz.

Ayrıca, tarayıcınızın geliştirici araçlarını kullanarak sayfadaki her bir varlığın URL'sini görüntüleyebilir veya bir üçüncü taraf ağ izleme aracı kullanabilirsiniz.

> [!NOTE]
> Varlıklarınızı sharepoint sayfasından işleme dışında test etmek için Fiddler gibi bir ağ aracı kullanıyorsanız, "Başvuran: `https://yourdomain.sharepoint.com`" başvuru başlığını, URL'nin SharePoint Online kiracınızın kök URL'si olduğu GET isteğine el ile eklemeniz gerekir.

SharePoint Online'dan gelen bir başvuru sahibi olması gerektiğinden CDN URL'lerini doğrudan bir web tarayıcısında test edemezsiniz. Ancak, CDN varlık URL'sini bir SharePoint sayfasına ekler ve ardından sayfayı tarayıcıda açarsanız, cdn varlığının sayfada işlendiğini görürsünüz.

Microsoft Edge tarayıcısında geliştirici araçlarını kullanma hakkında daha fazla bilgi için bkz. [Microsoft Edge Geliştirici Araçları](/microsoft-edge/devtools-guide).

[SharePoint Geliştirici Desenleri ve Uygulamaları YouTube kanalında](https://aka.ms/sppnp-videos) barındırılan ve CDN'nizin çalıştığını nasıl doğrulayabileceğinizi gösteren kısa bir video izlemek için bkz. [CDN kullanımınızı doğrulama ve en iyi ağ bağlantısını sağlama](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5).

### <a name="why-are-assets-from-a-new-origin-unavailable"></a>Yeni bir kaynaktan gelen varlıklar neden kullanılamıyor?
Kaydın CDN üzerinden yayılması ve varlıkların kaynaktan CDN depolamaya yüklenmesi zaman aldığından, yeni kaynaklardaki varlıklar hemen kullanılamaz. Varlıkların CDN'de kullanılabilir olması için gereken süre, kaç varlık ve dosya boyutuna bağlıdır.

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a>İstemci tarafı web bölümüm veya SharePoint Framework çözümüm çalışmıyor

Genel kaynaklar için Office 365 CDN'yi etkinleştirdiğinizde, CDN hizmeti otomatik olarak şu varsayılan kaynakları oluşturur:

+ */MASTERPAGE
+ */STYLE LIBRARY
+ */CLIENTSIDEASSETS

*/clientsideassets kaynağı eksikse, SharePoint Framework çözümler başarısız olur ve hiçbir uyarı veya hata iletisi oluşturulmaz. CDN $true olarak ayarlanmış _-NoDefaultOrigins_ parametresiyle etkinleştirildiğinden veya kaynak el ile silindiğinden **bu kaynak** eksik olabilir.

Aşağıdaki PowerShell komutuyla hangi çıkış noktalarının mevcut olduğunu kontrol edebilirsiniz:

```powershell
Get-SPOTenantCdnOrigins -CdnType Public
```

İsterseniz Office 365 CLI ile de kontrol edebilirsiniz:

```cli
spo cdn origin list
```

PowerShell'de kaynağı eklemek için:

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

kaynağı Office 365 CLI'ya eklemek için:

```cli
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a>Office 365 CDN ile çalışmak için hangi PowerShell modüllerine ve CLI kabuklarına ihtiyacım var?

**SharePoint Online Yönetim Kabuğu** PowerShell modülünü veya Office 365 **CLI'yı kullanarak Office 365** CDN ile çalışmayı seçebilirsiniz.

+ [SharePoint Online Yönetim Kabuğu'yla çalışmaya başlama](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
+ [Office 365 CLI'yi yükleme](https://pnp.github.io/cli-microsoft365/user-guide/installing-cli/)

## <a name="see-also"></a>Ayrıca bkz.

[İçerik Teslim Ağları](./content-delivery-networks.md)

[Network planning and performance tuning for Office 365](./network-planning-and-performance.md)

[SharePoint Performans Serisi - Office 365 CDN video serisi](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
