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
description: SharePoint Online varlıklarınızın teslimini hızlandırmak için Office 365 Content Delivery Network (CDN) kullanmayı öğrenin.
ms.openlocfilehash: 8b106840133f5c690fd0df80700fdb79a3590d92
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139573"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a>SharePoint Online ile Office 365 Content Delivery Network (CDN) kullanma

SharePoint Online sayfalarınız için daha iyi performans sağlamak amacıyla statik varlıkları barındırmak için yerleşik Office 365 Content Delivery Network (CDN) kullanabilirsiniz. Office 365 CDN statik varlıkları isteyen tarayıcılara daha yakın önbelleğe alarak performansı artırır ve bu da indirmeleri hızlandırmaya ve gecikme süresini azaltmaya yardımcı olur. Ayrıca, Office 365 CDN gelişmiş sıkıştırma ve HTTP kanal oluşturma için HTTP[/2 protokollerini](https://en.wikipedia.org/wiki/HTTP/2) kullanır. Office 365 CDN hizmeti, SharePoint Online aboneliğinizin bir parçası olarak dahil edilir.

> [!NOTE]
> Office 365 CDN yalnızca **Üretim** (dünya çapında) buluttaki kiracılar tarafından kullanılabilir. ABD Hükümeti, Çin ve Almanya bulutlarındaki kiracılar şu anda Office 365 CDN desteklememektedir.

Office 365 CDN, statik varlıkları birden çok konumda veya _kaynakta_ barındırmanıza ve bunları genel yüksek hızlı ağlardan sunmanıza olanak sağlayan birden çok CDN'den oluşur. Office 365 CDN barındırmak istediğiniz içerik türüne bağlı olarak **genel kaynaklar,** **özel** kaynaklar veya her ikisini birden ekleyebilirsiniz. Genel ve özel kaynaklar arasındaki fark hakkında daha fazla bilgi için bkz. [Her kaynağın genel mi yoksa özel mi olacağını seçme](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) .

![kavramsal diyagramı Office 365 CDN.](../media/O365-CDN/o365-cdn-flow-transparent.png "kavramsal diyagramı Office 365 CDN")

CDN'lerin çalışma şeklini zaten biliyorsanız, kiracınız için Office 365 CDN etkinleştirmek için yalnızca birkaç adımı tamamlamanız yeterlidir. Bu konuda nasıl yapılır açıklanmaktadır. Statik varlıklarınızı barındırmaya başlama hakkında bilgi için okumaya devam edin.

> [!TIP]
> Özel kullanım senaryoları için Office 365 ile kullanılabilecek, ancak Office 365 CDN kapsamının dışında olduklarından bu konuda tartışılmayan başka Microsoft tarafından barındırılan CDN'ler de vardır. Daha fazla bilgi için bkz. [Diğer Microsoft CDN'leri](content-delivery-networks.md#other-microsoft-cdns).

 **[Office 365 için Ağ planlama ve performans ayarlama'ya](./network-planning-and-performance.md) dönün.**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a>SharePoint Online'da Office 365 CDN ile çalışmaya genel bakış

Kuruluşunuz için Office 365 CDN ayarlamak için şu temel adımları izleyin:

+ [Office 365 CDN dağıtımını planlama](use-microsoft-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  + [CDN hangi statik varlıkları barındırmak istediğinizi belirleyin](use-microsoft-365-cdn-with-spo.md#CDNAssets).
  + [Varlıklarınızı nerede depolamak istediğinizi belirleyin](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets). Bu konum bir SharePoint site, kitaplık veya klasör olabilir ve _kaynak_ olarak adlandırılır.
  + [Her kaynağın genel mi yoksa özel mi olacağını seçin](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Hem genel hem de özel türlerin birden çok kaynağını ekleyebilirsiniz.

+ Microsoft 365 için PowerShell veya CLI kullanarak CDN ayarlama ve yapılandırma

  + [SharePoint Online Management Shell kullanarak CDN ayarlama ve yapılandırma](use-microsoft-365-cdn-with-spo.md#CDNSetupinPShell)
  + [PnP PowerShell kullanarak CDN ayarlama ve yapılandırma](use-microsoft-365-cdn-with-spo.md#CDNSetupinPnPPosh)
  + [Microsoft 365 için CLI kullanarak CDN ayarlama ve yapılandırma](use-microsoft-365-cdn-with-spo.md#CDNSetupinCLI)

  Bu adımı tamamladığınızda şunları yapacaksınız:

  + Kuruluşunuz için CDN etkinleştirildi.
  + Her kaynağı genel veya özel olarak tanımlayarak kaynaklarınızı eklediniz.

Kurulumu tamamladıktan sonra, [zaman içinde Office 365 CDN şu şekilde yönetebilirsiniz](use-microsoft-365-cdn-with-spo.md#CDNManage):

+ Varlıkları ekleme, güncelleştirme ve kaldırma
+ Çıkış noktaları ekleme ve kaldırma
+ CDN ilkelerini yapılandırma
+ Gerekirse, CDN devre dışı bırakma

Son olarak, [CDN varlıklarınıza](use-microsoft-365-cdn-with-spo.md#using-your-cdn-assets) hem genel hem de özel kaynaklardan erişme hakkında bilgi edinmek için bkz. CDN varlıklarınızı kullanma.

Yaygın sorunları çözme yönergeleri için bkz. [Office 365 CDN sorunlarını giderme](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting).

## <a name="plan-for-deployment-of-the-office-365-cdn"></a>Office 365 CDN dağıtımını planlama

Office 365 kiracınız için Office 365 CDN dağıtmadan önce, planlama sürecinizin bir parçası olarak aşağıdaki faktörleri dikkate almanız gerekir.

  + [CDN hangi statik varlıkları barındırmak istediğinizi belirleme](use-microsoft-365-cdn-with-spo.md#CDNAssets)
  + [Varlıklarınızı nerede depolamak istediğinizi belirleme](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets)
  + [Her kaynağın genel mi yoksa özel mi olacağını seçin](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

<a name="CDNAssets"> </a>
### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a>CDN hangi statik varlıkları barındırmak istediğinizi belirleme

Genel olarak, CDN'ler en çok _statik varlıkları_ veya çok sık değişmeyen varlıkları barındırmak için etkilidir. İyi bir kural, bu koşulların bazılarını veya tümünü karşılayan dosyaları tanımlamaktır:

+ Sayfa yükleme süreleri üzerinde önemli bir artımlı etkiye sahip olabilecek bir sayfaya eklenmiş statik dosyalar (betikler ve resimler gibi)
+ Yürütülebilir dosyalar ve yükleme dosyaları gibi büyük dosyalar
+ İstemci tarafı kodunu destekleyen kaynak kitaplıkları

Örneğin, site görüntüleri ve betikleri gibi sürekli olarak istenen küçük dosyalar, site işleme performansını önemli ölçüde artırabilir ve CDN bir kaynak alanına eklediğinizde SharePoint Çevrimiçi sitelerinizdeki yükü artımlı olarak azaltabilir. Yükleme yürütülebilir dosyaları gibi daha büyük dosyalar CDN indirilebilir ve bu dosyalara sık erişilmese bile SharePoint Online sitenizdeki yükün olumlu bir performans etkisi ve daha sonra azaltılması sağlanır.

Dosya başına performans iyileştirmesi, istemcinin en yakın CDN uç noktasına yakınlığı, yerel ağdaki geçici koşullar vb. gibi birçok faktöre bağlıdır. Birçok statik dosya oldukça küçüktür ve Office 365 bir saniyeden kısa bir süre içinde indirilebilir. Ancak, bir web sayfası birkaç saniyelik toplu indirme süresine sahip birçok ekli dosya içerebilir. Bu dosyaları CDN sunma, genel sayfa yükleme süresini önemli ölçüde azaltabilir. Örnek olarak bkz[. CDN hangi performans kazançlarını sağlar?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide)

<a name="CDNStoreAssets"> </a>
### <a name="determine-where-you-want-to-store-your-assets"></a>Varlıklarınızı nerede depolamak istediğinizi belirleme

CDN varlıklarınızı _kaynak_ olarak adlandırılan bir konumdan getirir. Kaynak, URL tarafından erişilebilen bir SharePoint sitesi, belge kitaplığı veya klasör olabilir. Kuruluşunuz için kaynak belirtirken büyük bir esnekliğe sahip olursunuz. Örneğin, tüm CDN varlıklarınızı yerleştirmek istediğiniz birden çok kaynak veya tek bir çıkış noktası belirtebilirsiniz. Kuruluşunuz için hem genel hem de özel kaynaklardan birini seçebilirsiniz. Çoğu kuruluş ikisinin birleşimini uygulamayı seçecektir.

Kaynaklarınız için klasörler veya belge kitaplıkları gibi yeni kapsayıcılar oluşturabilir ve CDN kullanılabilir hale getirmek istediğiniz dosyaları ekleyebilirsiniz. CDN kullanılabilir olmasını istediğiniz belirli bir varlık kümeniz varsa ve CDN varlık kümesini yalnızca kapsayıcıdaki dosyalarla kısıtlamak istiyorsanız bu iyi bir yaklaşımdır.

Ayrıca kaynak olarak mevcut bir site koleksiyonunu, siteyi, kitaplığı veya klasörü yapılandırabilirsiniz; bu da kapsayıcıdaki tüm uygun varlıkların CDN kullanılabilir olmasını sağlar. Var olan bir kapsayıcıyı kaynak olarak eklemeden önce, varlıkları yanlışlıkla anonim erişime veya yetkisiz kullanıcılara sunmamak için içeriklerini ve izinlerini bildiğinizden emin olmanız önemlidir.

Kaynaklarınızdaki içeriği _CDN_ dışında tutmak için CDN ilkeleri tanımlayabilirsiniz. CDN ilkeleri, ortak veya özel kaynaklardaki varlıkları _dosya türü_ ve _site sınıflandırması_ gibi özniteliklere göre dışlar ve ilkede belirttiğiniz CdnType'ın (özel veya genel) tüm çıkış noktalarına uygulanır. Örneğin, birden çok alt site içeren bir siteden oluşan özel bir kaynak eklerseniz, **gizli** olarak işaretlenmiş siteleri dışlamak için bir ilke tanımlayabilirsiniz, böylece bu sınıflandırmaya sahip sitelerden içerik CDN sunulmaz. İlke, CDN eklediğiniz _tüm_ özel kaynaklardan gelen içeriğe uygulanır.

Kaynak sayısı ne kadar fazlaysa, CDN hizmetinin istekleri işleme süresi üzerindeki etkisinin de o kadar fazla olduğunu unutmayın. Kaynak sayısını mümkün olduğunca sınırlamanızı öneririz.

<a name="CDNOriginChoosePublicPrivate"> </a>
### <a name="choose-whether-each-origin-should-be-public-or-private"></a>Her kaynağın genel mi yoksa özel mi olacağını seçin

Bir kaynağı belirlediğinizde, _bunun genel_ mi yoksa _özel_ mi olacağını belirtirsiniz. Genel kaynaklarda CDN varlıklara erişim anonimdir ve özel kaynaklardaki CDN içerik daha fazla güvenlik için dinamik olarak oluşturulan belirteçlerle güvenli hale getirilmiştir. Hangi seçeneği belirlediğinizden bağımsız olarak, CDN yönetimi söz konusu olduğunda Microsoft sizin için tüm ağır işi yapar. Ayrıca, CDN ayarladıktan ve kaynaklarınızı belirledikten sonra fikrinizi daha sonra değiştirebilirsiniz.

Hem genel hem de özel seçenekler benzer performans kazançları sağlar, ancak her birinde benzersiz öznitelikler ve avantajlar vardır.

Office 365 CDN içindeki **genel** kaynaklara anonim olarak erişilebilir ve barındırılan varlıklara, varlığın URL'sine sahip olan herkes erişebilir. Genel kaynaklardaki içeriğe erişim anonim olduğundan, bunları yalnızca JavaScript dosyaları, betikler, simgeler ve görüntüler gibi hassas olmayan genel içerikleri önbelleğe almak için kullanmanız gerekir.

Office 365 CDN içindeki **özel** kaynaklar, SharePoint Çevrimiçi belge kitaplıkları, siteler ve özel görüntüler gibi kullanıcı içeriğine özel erişim sağlar. Özel kaynaklardaki içeriğe erişim dinamik olarak oluşturulan belirteçlerle güvenli hale getirildiğinden, içeriğe yalnızca özgün belge kitaplığı veya depolama konumu izinleri olan kullanıcılar tarafından erişilebilir. Office 365 CDN özel kaynaklar yalnızca çevrimiçi SharePoint içerik için kullanılabilir ve yalnızca SharePoint Online kiracınızdan yeniden yönlendirme yoluyla özel kaynaklardaki varlıklara erişebilirsiniz.

Özel bir kaynaktaki varlıklara CDN erişimin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [Varlıkları özel kaynaklarda kullanma](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins).

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a>Varlıkları genel kaynaklarda barındırmanın öznitelikleri ve avantajları

+ Genel bir kaynakta kullanıma sunulan varlıklara anonim olarak herkes erişebilir.
    > [!IMPORTANT]
    > Kullanıcı bilgilerini içeren veya kuruluşunuza duyarlı olarak kabul edilen kaynakları hiçbir zaman genel bir kaynakta yerleştirmemelisiniz.

+ Bir varlığı genel kaynaktan kaldırırsanız, varlık önbellekten 30 güne kadar kullanılabilir olmaya devam edebilir; ancak, 15 dakika içinde CDN varlığın bağlantılarını geçersiz kılacaktır.

+ Stil sayfalarını (CSS dosyaları) genel bir kaynakta barındırdığınızda, kod içinde göreli yolları ve URI'leri kullanabilirsiniz. Bu, arka plan görüntülerinin ve diğer nesnelerin konumuna, onu çağıran varlığın konumuna göre başvurabileceğiniz anlamına gelir.

+ Genel bir kaynağın URL'sini oluşturabilmenize rağmen dikkatli olmalı ve sayfa bağlamı özelliğini kullandığınızdan emin olmalı ve bunu yapmak için yönergeleri izlemelisiniz. Bunun nedeni, CDN erişim kullanılamaz duruma gelirse URL'nin SharePoint Online'da kuruluşunuza otomatik olarak çözümlenmeyecek olması ve bağlantıların bozulmasına ve diğer hatalara neden olmasıdır. URL de değiştirilebilir ve bu nedenle yalnızca geçerli değerine sabit kodlanmamalıdır.

+ Genel kaynaklar için eklenen varsayılan dosya türleri .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, .woff ve .woff2'dir. Ek dosya türleri belirtebilirsiniz.

+ Bir ilkeyi, belirttiğiniz site sınıflandırmaları tarafından tanımlanan varlıkları dışlamak için yapılandırabilirsiniz. Örneğin, "gizli" veya "kısıtlanmış" olarak işaretlenen tüm varlıkları, izin verilen bir dosya türü olsalar ve genel bir kaynakta yer alıyor olsalar bile hariç tutabilirsiniz.

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a>Varlıkları özel kaynaklarda barındırmanın öznitelikleri ve avantajları

+ Özel kaynaklar yalnızca SharePoint Çevrimiçi varlıklar için kullanılabilir.

+ Kullanıcılar varlıklara yalnızca kapsayıcıya erişim izinleri varsa özel bir kaynaktan erişebilir. Bu varlıklara anonim erişim engellenir.

+ Özel kaynaklardaki varlıklar SharePoint Online kiracısından yönlendirilmelidir. Özel CDN varlıklarına doğrudan erişim çalışmaz.

+ Bir varlığı özel kaynaktan kaldırırsanız, varlık önbellekten bir saate kadar kullanılabilir olmaya devam edebilir; ancak, varlığın kaldırılmasından sonra 15 dakika içinde CDN varlık bağlantılarını geçersiz kılacaktır.

+ Özel kaynaklarda bulunan varsayılan dosya türleri .gif, .ico, .jpeg, .jpg, .js ve .png'dır. Ek dosya türleri belirtebilirsiniz.

+ Genel kaynaklarda olduğu gibi, klasör veya belge kitaplığındaki tüm varlıkları dahil etmek için joker karakterler kullansanız bile belirttiğiniz site sınıflandırmalarıyla tanımlanan varlıkları dışlamak için bir ilke yapılandırabilirsiniz.

Office 365 CDN, genel CDN kavramlarını ve Office 365 kiracınızla kullanabileceğiniz diğer Microsoft CDN'lerini kullanma hakkında daha fazla bilgi için bkz. [Content Delivery Networks](content-delivery-networks.md).

### <a name="default-cdn-origins"></a>Varsayılan CDN çıkış noktaları

Aksini belirtmediğiniz sürece, Office 365 Office 365 CDN etkinleştirdiğinizde sizin için bazı varsayılan çıkış noktaları ayarlar. Başlangıçta sağlamamayı tercih ederseniz, kurulumu tamamladıktan sonra bu kaynakları ekleyebilirsiniz. Varsayılan çıkış noktalarının kurulumunu atlamanın sonuçlarını anlamadığınız ve bunu yapmak için belirli bir nedeniniz olmadığı sürece, CDN etkinleştirdiğinizde bunların oluşturulmasına izin vermelisiniz.

Varsayılan özel CDN çıkış noktaları:

+ \*/userphoto.aspx
+ \*/siteassets

Varsayılan genel CDN çıkış noktaları:

+ \*/masterpage
+ \*/style library
+ \*/clientsideassets

> [!NOTE]
> _clientsideassets_, Aralık 2017'de Office 365 CDN hizmetine eklenen varsayılan bir genel kaynaktır. CDN SharePoint Framework çözümlerinin çalışması için bu kaynağın mevcut olması gerekir. Office 365 CDN Aralık 2017'ye kadar etkinleştirdiyseniz veya CDN etkinleştirdiğinizde varsayılan çıkış noktalarının kurulumunu atladıysanız, bu kaynağı el ile ekleyebilirsiniz. Daha fazla bilgi için bkz. [İstemci tarafı web bölümüm veya SharePoint Framework çözümüm çalışmıyor](use-microsoft-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).

<a name="CDNSetupinPShell"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>SharePoint Online Management Shell kullanarak Office 365 CDN ayarlama ve yapılandırma

Bu bölümdeki yordamlar, SharePoint Online'a bağlanmak için SharePoint Çevrimiçi Yönetim Kabuğu'nı kullanmanızı gerektirir. Yönergeler için bkz. [Çevrimiçi PowerShell'i SharePoint için Bağlan](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

SharePoint Online Management Shell'i kullanarak varlıklarınızı SharePoint Online'da barındıracak CDN ayarlamak ve yapılandırmak için bu adımları tamamlayın.

<details>
  <summary>Genişletmek için tıklayın</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Kuruluşunuzun Office 365 CDN kullanmasını sağlama

Kiracı CDN ayarlarında değişiklik yapmadan önce, Office 365 kiracınızdaki özel CDN yapılandırmasının geçerli durumunu almanız gerekir. SharePoint Çevrimiçi Yönetim Kabuğu'nı kullanarak kiracınıza Bağlan:

```powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

Şimdi kiracıdan CDN durum ayarlarını almak için **Get-SPOTenantCdnEnabled cmdlet'ini** kullanın:

```powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

Belirtilen CdnType için CDN durumu ekrana yansıtılır.

Kuruluşunuzun Office 365 CDN kullanmasını sağlamak için **Set-SPOTenantCdnEnabled cmdlet'ini** kullanın. Kuruluşunuzun ortak kaynakları, özel kaynakları veya her ikisini birden aynı anda kullanmasını sağlayabilirsiniz. Ayrıca, etkinleştirdiğinizde varsayılan çıkış noktalarının kurulumunu atlamak için CDN yapılandırabilirsiniz. Bu kaynakları daha sonra bu konuda açıklandığı gibi ekleyebilirsiniz.

SharePoint Online için Windows PowerShell'da:

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

Office 365 CDN etkinleştirdiğinizde varsayılan olarak sağlanan kaynaklar ve varsayılan [çıkış](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) noktalarının kurulumunu atlamanın olası etkisi hakkında bilgi için bkz. Varsayılan CDN çıkış noktaları.

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
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Dosya türlerinin listesini Office 365 CDN eklenecek şekilde değiştirme (İsteğe bağlı)

> [!TIP]
> **Set-SPOTenantCdnPolicy cmdlet'ini** kullanarak dosya türlerini tanımladığınızda, şu anda tanımlanmış olan listenin üzerine yazarsınız. Listeye başka dosya türleri eklemek istiyorsanız, önce cmdlet'ini kullanarak hangi dosya türlerine zaten izin verilip bunları yeni dosya türlerinizle birlikte listeye ekleyin.

CDN genel ve özel kaynaklar tarafından barındırılabilir statik dosya türlerini tanımlamak için **Set-SPOTenantCdnPolicy** cmdlet'ini kullanın. Varsayılan olarak, .css, .gif, .jpg ve .js gibi ortak varlık türlerine izin verilir.

SharePoint Online için Windows PowerShell'da:

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Örneğin, .css ve .png dosyalarını barındırmak için CDN etkinleştirmek için komutunu girersiniz:

```powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

CDN tarafından şu anda hangi dosya türlerine izin verıldığını görmek için **Get-SPOTenantCdnPolicies** cmdlet'ini kullanın:

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Bu cmdlet'ler hakkında daha fazla bilgi için bkz. [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) ve [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Office 365 CDN dışında tutmak istediğiniz site sınıflandırmaları listesini değiştirme (İsteğe bağlı)

> [!TIP]
> **Set-SPOTenantCdnPolicy cmdlet'ini** kullanarak site sınıflandırmalarını dışladığınızda, şu anda tanımlanmış olan listenin üzerine yazarsınız. Ek site sınıflandırmalarını dışlamak istiyorsanız, önce hangi sınıflandırmaların zaten dışlandığını öğrenmek için cmdlet'ini kullanın ve ardından bunları yeni sınıflandırmalarınızla birlikte ekleyin.

CDN üzerinde kullanılabilir hale getirmek istemediğiniz site sınıflandırmalarını dışlamak için **Set-SPOTenantCdnPolicy** cmdlet'ini kullanın. Varsayılan olarak, hiçbir site sınıflandırması hariç tutulmaz.

SharePoint Online için Windows PowerShell'da:

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

Şu anda hangi site sınıflandırmalarının kısıtlandığını görmek için **Get-SPOTenantCdnPolicies** cmdlet'ini kullanın:

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Döndürülecek özellikler _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ ve _ExcludeIfNoScriptDisabled'dır_.

_IncludeFileExtensions_ özelliği, CDN sunulacak dosya uzantılarının listesini içerir.

> [!NOTE]
> Varsayılan dosya uzantıları genel ve özel arasında farklıdır.

_ExcludeRestrictedSiteClassifications_ özelliği, CDN dışında tutmak istediğiniz site sınıflandırmalarını içerir. Örneğin, **Gizli** olarak işaretlenen siteleri dışlayabilirsiniz, böylece bu sınıflandırmaya sahip sitelerdeki içerikler CDN sunulmaz.

_ExcludeIfNoScriptDisabled_ özelliği, site düzeyi _NoScript_ öznitelik ayarlarına göre içeriği CDN dışında tutar. Varsayılan olarak _, NoScript_ özniteliği _Modern_ siteler için **etkin** ve _Klasik_ siteler için **devre dışı** olarak ayarlanır. Bu, kiracı ayarlarınıza bağlıdır.

Bu cmdlet'ler hakkında daha fazla bilgi için bkz. [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) ve [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOOriginPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>Varlıklarınız için kaynak ekleme

Bir kaynak tanımlamak için **Add-SPOTenantCdnOrigin** cmdlet'ini kullanın. Birden çok kaynak tanımlayabilirsiniz. Kaynak, CDN tarafından barındırılmasını istediğiniz varlıkları içeren bir SharePoint kitaplığına veya klasöre işaret eden bir URL'dir.

> [!IMPORTANT]
> Kullanıcı bilgilerini içeren veya kuruluşunuza duyarlı olarak kabul edilen kaynakları hiçbir zaman genel bir kaynakta yerleştirmemelisiniz.

```powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

_Yol_ değeri, varlıkları içeren kitaplığın veya klasörün göreli yoludur. Göreli yollara ek olarak joker karakterler de kullanabilirsiniz. Kaynaklar, URL'ye önceden eklenen joker karakterleri destekler. Bu, birden çok siteye yayılan kaynaklar oluşturmanıza olanak tanır. Örneğin, tüm sitelerinizin masterpages klasörüne tüm varlıkları CDN genel kaynak olarak eklemek için aşağıdaki komutu yazın:

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
> Özel kaynaklarda, bir kaynaktan paylaşılan varlıkların CDN erişilebilmesi için önce yayımlanmış bir ana sürüme sahip olması gerekir.

Komutunu çalıştırdıktan sonra sistem yapılandırmayı veri merkezi genelinde eşitler. Bu işlem 15 dakika kadar sürebilir.

<a name="ExamplePublicOrigin"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Örnek: SharePoint Online için ana sayfalarınız ve stil kitaplığınız için genel kaynak yapılandırma

Normalde, Office 365 CDN etkinleştirdiğinizde bu kaynaklar varsayılan olarak sizin için ayarlanır. Ancak, bunları el ile etkinleştirmek istiyorsanız aşağıdaki adımları izleyin.

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
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Örnek: SharePoint Online için site koleksiyonu için özel çıkış noktası yapılandırma

Site koleksiyonunu özel kaynak olarak tanımlamak için **Add-SPOTenantCdnOrigin** cmdlet'ini kullanın. Örneğin:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Bu komut ve söz dizimi hakkında daha fazla bilgi için bkz. [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Komutunu çalıştırdıktan sonra sistem yapılandırmayı veri merkezi genelinde eşitler. SharePoint Online kiracısı CDN hizmetine bağlandığından beklenen yapılandırma _beklemede_ iletisi görebilirsiniz. Bu işlem 15 dakika kadar sürebilir.

<a name="CDNManage"> </a>
### <a name="manage-the-office-365-cdn"></a>Office 365 CDN yönetme

CDN ayarladıktan sonra, bu bölümde açıklandığı gibi içeriği güncelleştirdikçe veya gereksinimleriniz değiştikçe yapılandırmanızda değişiklikler yapabilirsiniz.

<a name="Office365CDNforSPOaddremoveasset"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Office 365 CDN varlık ekleme, güncelleştirme veya kaldırma

Kurulum adımlarını tamamladıktan sonra yeni varlıklar ekleyebilir ve mevcut varlıkları istediğiniz zaman güncelleştirebilir veya kaldırabilirsiniz. Kaynak olarak tanımladığınız klasör veya SharePoint kitaplığındaki varlıklarda yaptığınız değişiklikleri yapmanız yeter. Yeni bir varlık eklerseniz, bu varlık CDN hemen kullanılabilir. Ancak, varlığı güncelleştirirseniz yeni kopyanın yayılması ve CDN kullanılabilir duruma gelmesi 15 dakika kadar sürer.

Kaynağın konumunu almanız gerekiyorsa **Get-SPOTenantCdnOrigins** cmdlet'ini kullanabilirsiniz. Bu cmdlet'in nasıl kullanılacağı hakkında bilgi için bkz. [Get-SPOTenantCdnOrigins](/powershell/module/sharepoint-online/Get-SPOTenantCdnOrigins).

<a name="Office365CDNforSPORemoveOriginPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Office 365 CDN kaynağı kaldırma

Kaynak olarak tanımladığınız bir klasöre veya SharePoint kitaplığına erişimi kaldırabilirsiniz. Bunu yapmak için **Remove-SPOTenantCdnOrigin** cmdlet'ini kullanın.

```powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Bu cmdlet'in nasıl kullanılacağı hakkında bilgi için bkz [. Remove-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Remove-SPOTenantCdnOrigin).

<a name="Office365CDNforSPOModifyOrigin"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Office 365 CDN kaynağı değiştirme

Oluşturduğunuz bir kaynağı değiştiremezsiniz. Bunun yerine, kaynağı kaldırın ve sonra yenisini ekleyin. Daha fazla bilgi için bkz. [Office 365 CDN kaynağı kaldırmak](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPosh) [için ve Varlıklarınız için kaynak eklemek için](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Office 365 CDN devre dışı bırakma

Kuruluşunuzda CDN devre dışı bırakmak için **Set-SPOTenantCdnEnabled cmdlet'ini** kullanın. CDN için hem genel hem de özel kaynakları etkinleştirdiyseniz, cmdlet'i aşağıdaki örneklerde gösterildiği gibi iki kez çalıştırmanız gerekir.

CDN genel kaynak kullanımını devre dışı bırakmak için aşağıdaki komutu girin:

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

CDN özel çıkış noktalarının kullanımını devre dışı bırakmak için aşağıdaki komutu girin:

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

Bu cmdlet hakkında daha fazla bilgi için bkz. [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

</details>

<a name="CDNSetupinPnPPosh"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-pnp-powershell"></a>PnP PowerShell kullanarak Office 365 CDN ayarlama ve yapılandırma

Bu bölümdeki yordamlar, SharePoint Online'a bağlanmak için PnP PowerShell kullanmanızı gerektirir. Yönergeler için bkz. [PnP PowerShell'i kullanmaya başlama](https://github.com/SharePoint/PnP-PowerShell#getting-started).

PnP PowerShell kullanarak varlıklarınızı SharePoint Online'da barındıracak CDN ayarlamak ve yapılandırmak için bu adımları tamamlayın.

<details>
  <summary>Genişletmek için tıklayın</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Kuruluşunuzun Office 365 CDN kullanmasını sağlama

Kiracı CDN ayarlarında değişiklik yapmadan önce, Office 365 kiracınızdaki özel CDN yapılandırmasının geçerli durumunu almanız gerekir. PnP PowerShell kullanarak kiracınıza Bağlan:

```powershell
Connect-PnPOnline -Url https://contoso-admin.sharepoint.com -UseWebLogin
```

Şimdi kiracıdan CDN durum ayarlarını almak için **Get-PnPTenantCdnEnabled cmdlet'ini** kullanın:

```powershell
Get-PnPTenantCdnEnabled -CdnType <Public | Private>
```

Belirtilen CdnType için CDN durumu ekrana yansıtılır.

Kuruluşunuzun Office 365 CDN kullanmasını sağlamak için **Set-PnPTenantCdnEnabled cmdlet'ini** kullanın. Kuruluşunuzun ortak kaynakları, özel kaynakları veya her ikisini aynı anda kullanmasını sağlayabilirsiniz. Ayrıca, etkinleştirdiğinizde varsayılan çıkış noktalarının kurulumunu atlamak için CDN yapılandırabilirsiniz. Bu kaynakları daha sonra bu konuda açıklandığı gibi ekleyebilirsiniz.

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

Office 365 CDN etkinleştirdiğinizde varsayılan olarak sağlanan kaynaklar ve varsayılan [çıkış](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) noktalarının kurulumunu atlamanın olası etkisi hakkında bilgi için bkz. Varsayılan CDN çıkış noktaları.

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
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Dosya türlerinin listesini Office 365 CDN eklenecek şekilde değiştirme (İsteğe bağlı)

> [!TIP]
> **Set-PnPTenantCdnPolicy cmdlet'ini** kullanarak dosya türlerini tanımladığınızda, şu anda tanımlanmış olan listenin üzerine yazarsınız. Listeye başka dosya türleri eklemek istiyorsanız, önce cmdlet'ini kullanarak hangi dosya türlerine zaten izin verilip bunları yeni dosya türlerinizle birlikte listeye ekleyin.

CDN genel ve özel kaynaklar tarafından barındırılabilir statik dosya türlerini tanımlamak için **Set-PnPTenantCdnPolicy** cmdlet'ini kullanın. Varsayılan olarak, .css, .gif, .jpg ve .js gibi ortak varlık türlerine izin verilir.

PnP PowerShell'de:

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Örneğin, .css ve .png dosyalarını barındırmak için CDN etkinleştirmek için komutunu girersiniz:

```powershell
Set-PnPTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

CDN tarafından şu anda hangi dosya türlerine izin verıldığını görmek için **Get-PnPTenantCdnPolicies** cmdlet'ini kullanın:

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

Bu cmdlet'ler hakkında daha fazla bilgi için bkz. [Set-PnPTenantCdnPolicy](https://pnp.github.io/powershell/cmdlets/Set-PnPTenantCdnPolicy.html) ve [Get-PnPTenantCdnPolicies](https://pnp.github.io/powershell/cmdlets/Get-PnPTenantCdnPolicies.html).

<a name="Office365CDNforPnPPoshSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Office 365 CDN dışında tutmak istediğiniz site sınıflandırmaları listesini değiştirme (İsteğe bağlı)

> [!TIP]
> **Set-PnPTenantCdnPolicy cmdlet'ini** kullanarak site sınıflandırmalarını dışladığınızda, şu anda tanımlanmış olan listenin üzerine yazarsınız. Ek site sınıflandırmalarını dışlamak istiyorsanız, önce hangi sınıflandırmaların zaten dışlandığını öğrenmek için cmdlet'ini kullanın ve ardından bunları yeni sınıflandırmalarınızla birlikte ekleyin.

CDN üzerinde kullanılabilir hale getirmek istemediğiniz site sınıflandırmalarını dışlamak için **Set-PnPTenantCdnPolicy** cmdlet'ini kullanın. Varsayılan olarak, hiçbir site sınıflandırması hariç tutulmaz.

PnP PowerShell'de:

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications>"
```

Şu anda hangi site sınıflandırmalarının kısıtlandığını görmek için **Get-PnPTenantCdnPolicies cmdlet'ini** kullanın:

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

Döndürülecek özellikler _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ ve _ExcludeIfNoScriptDisabled'dır_.

_IncludeFileExtensions_ özelliği, CDN sunulacak dosya uzantılarının listesini içerir.

> [!NOTE]
> Varsayılan dosya uzantıları genel ve özel arasında farklıdır.

_ExcludeRestrictedSiteClassifications_ özelliği, CDN dışında tutmak istediğiniz site sınıflandırmalarını içerir. Örneğin, **Gizli** olarak işaretlenen siteleri dışlayabilirsiniz, böylece bu sınıflandırmaya sahip sitelerdeki içerikler CDN sunulmaz.

_ExcludeIfNoScriptDisabled_ özelliği, site düzeyi _NoScript_ öznitelik ayarlarına göre içeriği CDN dışında tutar. Varsayılan olarak _, NoScript_ özniteliği _Modern_ siteler için **etkin** ve _Klasik_ siteler için **devre dışı** olarak ayarlanır. Bu, kiracı ayarlarınıza bağlıdır.

Bu cmdlet'ler hakkında daha fazla bilgi için bkz. [Set-PnPTenantCdnPolicy](https://pnp.github.io/powershell/cmdlets/Set-PnPTenantCdnPolicy.html) ve [Get-PnPTenantCdnPolicies](https://pnp.github.io/powershell/cmdlets/Get-PnPTenantCdnPolicies.html).

<a name="Office365CDNforSPOOriginPnPPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>Varlıklarınız için kaynak ekleme

Bir kaynak tanımlamak için **Add-PnPTenantCdnOrigin** cmdlet'ini kullanın. Birden çok kaynak tanımlayabilirsiniz. Kaynak, CDN tarafından barındırılmasını istediğiniz varlıkları içeren bir SharePoint kitaplığına veya klasöre işaret eden bir URL'dir.

> [!IMPORTANT]
> Kullanıcı bilgilerini içeren veya kuruluşunuza duyarlı olarak kabul edilen kaynakları hiçbir zaman genel bir kaynakta yerleştirmemelisiniz.

```powershell
Add-PnPTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

_Yol_ değeri, varlıkları içeren kitaplığın veya klasörün göreli yoludur. Göreli yollara ek olarak joker karakterler de kullanabilirsiniz. Kaynaklar, URL'ye önceden eklenen joker karakterleri destekler. Bu, birden çok siteye yayılan kaynaklar oluşturmanıza olanak tanır. Örneğin, tüm sitelerinizin masterpages klasörüne tüm varlıkları CDN genel kaynak olarak eklemek için aşağıdaki komutu yazın:

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
> Özel kaynaklarda, bir kaynaktan paylaşılan varlıkların CDN erişilebilmesi için önce yayımlanmış bir ana sürüme sahip olması gerekir.

Komutunu çalıştırdıktan sonra sistem yapılandırmayı veri merkezi genelinde eşitler. Bu işlem 15 dakika kadar sürebilir.

<a name="ExamplePublicOriginPnPPosh"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Örnek: SharePoint Online için ana sayfalarınız ve stil kitaplığınız için genel kaynak yapılandırma

Normalde, Office 365 CDN etkinleştirdiğinizde bu kaynaklar varsayılan olarak sizin için ayarlanır. Ancak, bunları el ile etkinleştirmek istiyorsanız aşağıdaki adımları izleyin.

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
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Örnek: SharePoint Online için site koleksiyonu için özel çıkış noktası yapılandırma

Site koleksiyonunu özel kaynak olarak tanımlamak için **Add-PnPTenantCdnOrigin** cmdlet'ini kullanın. Örneğin:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Bu komut ve söz dizimi hakkında daha fazla bilgi için bkz. [Add-PnPTenantCdnOrigin](https://pnp.github.io/powershell/cmdlets/Add-PnPTenantCdnOrigin.html).

Komutunu çalıştırdıktan sonra sistem yapılandırmayı veri merkezi genelinde eşitler. SharePoint Online kiracısı CDN hizmetine bağlandığından beklenen yapılandırma _beklemede_ iletisi görebilirsiniz. Bu işlem 15 dakika kadar sürebilir.

<a name="CDNManagePnPPosh"> </a>
### <a name="manage-the-office-365-cdn"></a>Office 365 CDN yönetme

CDN ayarladıktan sonra, bu bölümde açıklandığı gibi içeriği güncelleştirdikçe veya gereksinimleriniz değiştikçe yapılandırmanızda değişiklikler yapabilirsiniz.

<a name="Office365CDNforSPOaddremoveassetPnPPosh"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Office 365 CDN varlık ekleme, güncelleştirme veya kaldırma

Kurulum adımlarını tamamladıktan sonra yeni varlıklar ekleyebilir ve mevcut varlıkları istediğiniz zaman güncelleştirebilir veya kaldırabilirsiniz. Kaynak olarak tanımladığınız klasör veya SharePoint kitaplığındaki varlıklarda yaptığınız değişiklikleri yapmanız yeter. Yeni bir varlık eklerseniz, bu varlık CDN hemen kullanılabilir. Ancak, varlığı güncelleştirirseniz yeni kopyanın yayılması ve CDN kullanılabilir duruma gelmesi 15 dakika kadar sürer.

Kaynağın konumunu almanız gerekiyorsa **Get-PnPTenantCdnOrigin** cmdlet'ini kullanabilirsiniz. Bu cmdlet'in nasıl kullanılacağı hakkında bilgi için bkz. [Get-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/get-pnptenantcdnorigin).

<a name="Office365CDNforSPORemoveOriginPnPPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Office 365 CDN kaynağı kaldırma

Kaynak olarak tanımladığınız bir klasöre veya SharePoint kitaplığına erişimi kaldırabilirsiniz. Bunu yapmak için **Remove-PnPTenantCdnOrigin cmdlet'ini** kullanın.

```powershell
Remove-PnPTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Bu cmdlet'in nasıl kullanılacağı hakkında bilgi için bkz [. Remove-PnPTenantCdnOrigin](https://pnp.github.io/powershell/cmdlets/Remove-PnPTenantCdnOrigin.html).

<a name="Office365CDNforSPOModifyOriginPnPPosh"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Office 365 CDN kaynağı değiştirme

Oluşturduğunuz bir kaynağı değiştiremezsiniz. Bunun yerine, kaynağı kaldırın ve sonra yenisini ekleyin. Daha fazla bilgi için bkz. [Office 365 CDN kaynağı kaldırmak](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPnPPosh) [için ve Varlıklarınız için kaynak eklemek için](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPnPPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Office 365 CDN devre dışı bırakma

Kuruluşunuzda CDN devre dışı bırakmak için **Set-PnPTenantCdnEnabled cmdlet'ini** kullanın. CDN için hem genel hem de özel kaynakları etkinleştirdiyseniz, cmdlet'i aşağıdaki örneklerde gösterildiği gibi iki kez çalıştırmanız gerekir.

CDN genel kaynak kullanımını devre dışı bırakmak için aşağıdaki komutu girin:

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $false
```

CDN özel çıkış noktalarının kullanımını devre dışı bırakmak için aşağıdaki komutu girin:

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $false
```

Bu cmdlet hakkında daha fazla bilgi için bkz. [Set-PnPTenantCdnEnabled](https://pnp.github.io/powershell/cmdlets/Set-PnPTenantCdnEnabled.html).

</details>

<a name="CDNSetupinCLI"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-using-the-cli-for-microsoft-365"></a>Microsoft 365 için CLI kullanarak Office 365 CDN ayarlama ve yapılandırma

Bu bölümdeki yordamlar[, Microsoft 365 için CLI'yi](https://aka.ms/cli-m365) yüklemenizi gerektirir. Ardından [oturum açma](https://pnp.github.io/cli-microsoft365/cmd/login/) komutunu kullanarak Office 365 kiracınıza bağlanın.

Microsoft 365 için CLI kullanarak varlıklarınızı SharePoint Online'da barındırmak üzere CDN ayarlamak ve yapılandırmak için bu adımları tamamlayın.

<details>
  <summary>Genişletmek için tıklayın</summary>

### <a name="enable-the-office-365-cdn"></a>Office 365 CDN etkinleştirme

[spo cdn set](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-set/) komutunu kullanarak kiracınızdaki Office 365 CDN durumunu yönetebilirsiniz.

Kiracınızda genel CDN Office 365 etkinleştirmek için şu komutu yürütür:

```cli
spo cdn set --type Public --enabled true
```

Office 365 SharePoint CDN etkinleştirmek için şunu yürütebilirsiniz:

```cli
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a>Office 365 CDN geçerli durumunu görüntüleme

Belirli bir Office 365 CDN türünün etkin veya devre dışı olup olmadığını denetlemek için [spo cdn get](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-get/) komutunu kullanın.

Office 365 Genel CDN etkinleştirilip etkinleştirilmediğini denetlemek için şunu yürütür:

```cli
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a>Office 365 CDN çıkış noktalarını görüntüleme

Şu anda yapılandırılmış Office 365 Genel CDN çıkış noktalarını görüntülemek için:

```cli
spo cdn origin list --type Public
```

Office 365 CDN etkinleştirdiğinizde varsayılan olarak sağlanan [kaynaklarla](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) ilgili bilgi için bkz. Varsayılan CDN çıkış noktaları.

### <a name="add-an-office-365-cdn-origin"></a>Office 365 CDN kaynağı ekleme

> [!IMPORTANT]
> Kuruluşunuza duyarlı olarak kabul edilen kaynakları hiçbir zaman genel kaynak olarak yapılandırılmış bir SharePoint belge kitaplığına yerleştirmemelisiniz.

CDN kaynağı tanımlamak için [spo cdn origin add](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-add/) komutunu kullanın. Birden çok kaynak tanımlayabilirsiniz. Kaynak, CDN tarafından barındırılmasını istediğiniz varlıkları içeren bir SharePoint kitaplığına veya klasöre işaret eden bir URL'dir.

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
> CDN kaynağı ekledikten sonra, dosyaları CDN hizmeti aracılığıyla almanız 15 dakika kadar sürebilir. [Spo cdn kaynak listesi](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-list/) komutunu kullanarak belirli kaynağın zaten etkinleştirilip etkinleştirilmediğini doğrulayabilirsiniz.

### <a name="remove-an-office-365-cdn-origin"></a>Office 365 CDN kaynağını kaldırma

Belirtilen CDN türü için CDN kaynağını kaldırmak için [spo cdn origin remove](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-remove/) komutunu kullanın.

CDN yapılandırmasından genel bir kaynağı kaldırmak için şunu yürütür:

```cli
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> CDN kaynağının kaldırılması, bu kaynakla eşleşen herhangi bir belge kitaplığında depolanan dosyaları etkilemez. Bu varlıklara SharePoint URL'si kullanılarak başvurulduysa, SharePoint otomatik olarak belge kitaplığına işaret eden özgün URL'ye geri döner. Ancak varlıklara genel CDN URL'si kullanılarak başvurulduysa, kaynağın kaldırılması bağlantıyı bozar ve bunları el ile değiştirmeniz gerekir.

### <a name="modify-an-office-365-cdn-origin"></a>Office 365 CDN kaynağını değiştirme

Mevcut bir CDN kaynağını değiştirmek mümkün değildir. Bunun yerine, komutunu kullanarak `spo cdn origin remove` önceden tanımlanmış CDN kaynağını kaldırmanız ve komutunu kullanarak `spo cdn origin add` yenisini eklemeniz gerekir.

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a>Office 365 CDN eklenecek dosya türlerini değiştirme

Varsayılan olarak, şu dosya türleri CDN eklenir: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, .woff ve .woff2_. CDN ek dosya türleri eklemeniz gerekiyorsa, [spo cdn ilke kümesi](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-set/) komutunu kullanarak CDN yapılandırmasını değiştirebilirsiniz.

> [!NOTE]
> Dosya türleri listesini değiştirirken, şu anda tanımlanmış olan listenin üzerine yazarsınız. Ek dosya türleri eklemek istiyorsanız, şu anda hangi dosya türlerinin yapılandırıldığını öğrenmek için önce [spo cdn ilke listesi](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-list/) komutunu kullanın.

_JSON_ dosya türünü genel CDN dahil edilen varsayılan dosya türleri listesine eklemek için şunu yürütür:

```cli
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>Office 365 CDN dışında tutmak istediğiniz site sınıflandırmaları listesini değiştirme

CDN üzerinde kullanılabilir hale getirmek istemediğiniz site sınıflandırmalarını dışlamak için [spo cdn ilke kümesi](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-set/) komutunu kullanın. Varsayılan olarak, hiçbir site sınıflandırması hariç tutulmaz.

> [!NOTE]
> Dışlanan site sınıflandırmaları listesini değiştirirken, şu anda tanımlanmış olan listenin üzerine yazarsınız. Ek sınıflandırmaları dışlamak istiyorsanız, şu anda hangi sınıflandırmaların yapılandırıldığını bulmak için önce [spo cdn ilke listesi](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-list/) komutunu kullanın.

_HBI_ olarak sınıflandırılan siteleri genel CDN dışında tutmak için

```cli
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a>Office 365 CDN devre dışı bırakma

Office 365 CDN devre dışı bırakmak için komutunu kullanın`spo cdn set`, örneğin:

```cli
spo cdn set --type Public --enabled false
```

</details>

## <a name="using-your-cdn-assets"></a>CDN varlıklarınızı kullanma

artık CDN etkinleştirdiğinize ve kaynaklarla ilkeleri yapılandırdığınıza göre, CDN varlıklarınızı kullanmaya başlayabilirsiniz.

Bu bölüm, SharePoint sayfalarınızda ve içeriğinizde CDN URL'leri nasıl kullanacağınızı anlamanıza yardımcı olur, böylece SharePoint hem genel hem de özel kaynaklardaki varlıklara yönelik istekleri CDN yönlendirir.

+ [CDN varlıkların bağlantılarını güncelleştirme](use-microsoft-365-cdn-with-spo.md#updating-links-to-cdn-assets)
+ [Varlıkları genel kaynaklarda kullanma](use-microsoft-365-cdn-with-spo.md#using-assets-in-public-origins)
+ [Varlıkları özel kaynaklarda kullanma](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins)

İstemci tarafı web bölümlerini barındırmak için CDN kullanma hakkında bilgi için, Office 365 CDN [istemci tarafı web bölümünüzü barındırma (Merhaba Dünya bölüm 4)](/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn) konusuna bakın.

> [!NOTE]
> _ClientSideAssets_ klasörünü **özel** CDN kaynak listesine eklerseniz, CDN barındırılan özel web bölümleri işlenemez. SPFX web bölümleri tarafından kullanılan dosyalar yalnızca genel CDN kullanabilir ve ClientSideAssets klasörü genel CDN için varsayılan bir kaynaktır.

### <a name="updating-links-to-cdn-assets"></a>CDN varlıkların bağlantılarını güncelleştirme

Kaynak öğeye eklediğiniz varlıkları kullanmak için, özgün dosyanın bağlantılarını kaynaktaki dosyanın yoluyla güncelleştirmeniz yeterlidir.

+ Bir kaynakta eklediğiniz varlıkların bağlantılarını içeren sayfayı veya içeriği düzenleyin. Ayrıca, belirli bir varlığın bağlantısını göründüğü her yerde güncelleştirmek istiyorsanız, bir enter sitesi veya site koleksiyonundaki bağlantıları genel olarak aramak ve değiştirmek için çeşitli yöntemlerden birini de kullanabilirsiniz.
+ Kaynaktaki bir varlığın her bağlantısı için, yolu CDN kaynağındaki dosyanın yoluyla değiştirin. Göreli yolları kullanabilirsiniz.
+ Sayfayı veya içeriği kaydedin.

Örneğin, _/site/site/CDN_origins/_ public/ belge kitaplığı klasörüne kopyaladığınız _/site/_ SiteAssets/images/image.pnggörüntüsünü göz önünde bulundurun. CDN varlığını kullanmak için, yeni _URL'yi /site/CDN_origins/public/image.png_ yapmak için görüntü dosyası konumunun özgün yolunu kaynağın yoluyla değiştirin.

Göreli yol yerine varlığın tam URL'sini kullanmak istiyorsanız bağlantıyı şöyle yapın:

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> Genel olarak, URL'leri doğrudan CDN varlıklara sabit kodlamamalısınız. Ancak, gerekirse genel kaynaklardaki varlıklar için URL'leri el ile oluşturabilirsiniz. Daha fazla bilgi için bkz. [Ortak varlıklar için sabit kodlama CDN URL'leri](use-microsoft-365-cdn-with-spo.md#constructing-cdn-urls-for-public-assets).

Varlıkların CDN sunulduğunun nasıl doğrulandığını öğrenmek için, Office 365 CDN [sorunlarını giderme](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting) bölümünde [varlıkların CDN tarafından sunulduğundan emin Nasıl yaparım? onaylayın](use-microsoft-365-cdn-with-spo.md#CDNConfirm)? bölümüne bakın.

### <a name="using-assets-in-public-origins"></a>Varlıkları genel kaynaklarda kullanma

SharePoint Online'daki **Yayımlama özelliği**, genel kaynaklarda depolanan varlıkların URL'lerini otomatik olarak CDN eşdeğerlerine yeniden yazar, böylece varlıklar SharePoint yerine CDN hizmetinden sunulur.

Kaynağınız Yayımlama özelliği etkinleştirilmiş bir sitedeyse ve CDN boşaltmak istediğiniz varlıklar aşağıdaki kategorilerden birindeyse, SharePoint varlığın bir CDN ilkesi tarafından dışlanmaması koşuluyla kaynaktaki varlıklar için URL'leri otomatik olarak yeniden yazar.

Aşağıda, SharePoint Yayımlama özelliği tarafından bağlantıların otomatik olarak yeniden yazıldığına genel bir bakış sağlanır:

+ Klasik yayımlama sayfası HTML yanıtlarında IMG/LINK/CSS URL'leri
  + Bu, bir sayfanın HTML içeriğine yazarlar tarafından eklenen görüntüleri içerir
+ Resim Kitaplığı Slayt Gösterisi web bölümü resim URL'leri
+ SPList REST API'sindeki görüntü alanları (RenderListDataAsStream) sonuçları
  + Alanların virgülle ayrılmış listesini sağlamak için _ImageFieldsToTryRewriteToCdnUrls_ yeni özelliğini kullanın
  + Köprü alanlarını ve PublishingImage alanlarını destekler
+ görüntü işlemelerini SharePoint

Aşağıdaki diyagramda, SharePoint ortak bir kaynaktan varlıklar içeren bir sayfa için istek aldığında iş akışı gösterilmektedir.

![İş akışı diyagramı: Genel bir kaynaktan Office 365 CDN varlıkları alma.](../media/O365-CDN/o365-cdn-public-steps-transparent.png "İş Akışı: Genel bir kaynaktan Office 365 CDN varlıkları alma")

> [!TIP]
> Sayfadaki belirli URL'ler için otomatik yeniden yazmayı devre dışı bırakmak istiyorsanız, sayfayı kullanıma alabilir ve sorgu dizesi parametresini ekleyebilirsiniz **? Devre dışı bırakmak istediğiniz her bağlantının sonuna doğru NoAutoReWrites=true** .

#### <a name="constructing-cdn-urls-for-public-assets"></a>Genel varlıklar için CDN URL'leri oluşturma

_Yayımlama_ özelliği genel kaynak için etkinleştirilmemişse veya varlık, CDN hizmetinin otomatik yeniden yazma özelliği tarafından desteklenen bağlantı türlerinden biri değilse, varlıkların CDN konumuna URL'leri el ile oluşturabilir ve içeriğinizde bu URL'leri kullanabilirsiniz.

> [!NOTE]
> URL'nin son bölümünü oluşturan gerekli erişim belirteci kaynağın istendiği anda oluşturulduğundan, url'leri özel bir kaynaktaki varlıklara sabit kodlayamaz veya CDN URL'leri oluşturamazsınız. Genel CDN URL'sini oluşturabilirsiniz ve url değiştirilebilir olduğundan sabit kodlanmamalıdır.

Genel CDN varlıkları için URL biçimi aşağıdaki gibi görünür:

```http
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

**TenantHostName** değerini kiracı adınız ile değiştirin. Örneğin:

```http
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

> [!NOTE]
> "" sabit kodlamasıhttps://publiccdn.sharepointonline.com yerine ön eki oluşturmak için sayfa bağlamı özelliği kullanılmalıdır. URL değiştirilebilir ve sabit kodlanmamalıdır. Klasik SharePoint Online ile görüntüleme şablonları kullanıyorsanız, URL'nin ön eki için görüntü şablonunuzda "window._spPageContextInfo.publicCdnBaseUrl" özelliğini kullanabilirsiniz. Modern ve klasik SharePoint için web bölümleri SPFx "this.context.pageContext.legacyPageContext.publicCdnBaseUrl" özelliğini kullanabilirsiniz. Bu, değiştirildiğinde uygulamanızın onunla güncelleştirilmesi için ön eki sağlar. SPFx örneği olarak, URL "this.context.pageContext.legacyPageContext.publicCdnBaseUrl" + "/" + "host" + "/" + "öğe için relativeURL" özelliği kullanılarak oluşturulabilir. Lütfen [1. sezon performans serisinin](https://aka.ms/sppnp-perfvideos) bir parçası olan [İstemci tarafı kodunda CDN kullanma](https://youtu.be/IH1RbQlbhIA) bölümüne bakın


### <a name="using-assets-in-private-origins"></a>Varlıkları özel kaynaklarda kullanma

Varlıkları özel kaynaklarda kullanmak için ek yapılandırma gerekmez. SharePoint Online, özel kaynaklardaki varlıklar için URL'leri otomatik olarak yeniden yazar, böylece bu varlıklara yönelik istekler her zaman CDN sunulur. Bu URL'ler, varlığın istendiği sırada SharePoint Online tarafından otomatik olarak oluşturulması gereken belirteçler içerdiğinden, varlıkları özel kaynaklarda CDN için URL'leri el ile oluşturamazsınız.

Özel kaynaklardaki varlıklara erişim, aşağıdaki bölümlerde açıklanan uyarılarla, kaynak üzerindeki kullanıcı izinlerine göre dinamik olarak oluşturulan belirteçlerle korunur. Kullanıcıların içeriği işlemek için CDN kaynaklarına en azından **okuma** erişimi olmalıdır.

Aşağıdaki diyagramda, SharePoint özel bir kaynaktan varlıklar içeren bir sayfa için istek aldığında iş akışı gösterilmektedir.

![İş akışı diyagramı: Özel bir kaynaktan Office 365 CDN varlıkları alma.](../media/O365-CDN/o365-cdn-private-steps-transparent.png "İş Akışı: Özel bir kaynaktan Office 365 CDN varlıkları alma")

#### <a name="token-based-authorization-in-private-origins"></a>Özel kaynaklarda belirteç tabanlı yetkilendirme

Office 365 CDN özel çıkış noktalarındaki varlıklara erişim, SharePoint Online tarafından oluşturulan belirteçler tarafından verilir. Kaynak tarafından belirlenen klasöre veya kitaplığa erişim izni olan kullanıcılara, izin düzeyine göre kullanıcının dosyaya erişmesine izin veren belirteçler otomatik olarak verilir. Bu erişim belirteçleri, belirteç yeniden yürütme saldırılarını önlemeye yardımcı olmak için oluşturulduktan sonra 30 ile 90 dakika boyunca geçerlidir.

Erişim belirteci oluşturulduktan sonra, SharePoint Online iki yetkilendirme parametresi _(_ uç yetkilendirme belirteci) ve _yulaf_ (kaynak yetkilendirme belirteci) içeren istemciye özel bir URI döndürür. Her belirtecin yapısı _,<'>__<'secure signature'>zaman biçimindeki süre sonu süresidir_. Örneğin:

```http
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> Belirtecin sahibi olan herkes CDN kaynağa erişebilir. Ancak, bu erişim belirteçlerini içeren URL'ler yalnızca HTTPS üzerinden paylaşılır, bu nedenle belirtecin süresi dolmadan önce URL son kullanıcı tarafından açıkça paylaşılmadığı sürece, varlığa yetkisiz kullanıcılar erişemez.

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a>Özel kaynaklardaki varlıklar için öğe düzeyi izinleri desteklenmez

SharePoint Online'ın özel kaynaklardaki varlıklar için öğe düzeyinde izinleri desteklemediğini unutmayın. Örneğin, konumunda `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`bulunan bir dosya için, kullanıcılar aşağıdaki koşullar göz önünde bulundurularak dosyaya etkin erişime sahiptir:

|Kullanıcı  |İzinler  |Etkin erişim  |
|---------|---------|---------|
|Kullanıcı 1     |Klasör1'e erişimi var         |CDN image1.jpg erişebilir         |
|Kullanıcı 2     |Klasör1'e erişimi yok         |CDN image1.jpg erişilemiyor         |
|Kullanıcı 3     |klasör1'e erişimi yoktur, ancak SharePoint Online'da image1.jpg erişim için açık izin verilir         |Varlık image1.jpg doğrudan SharePoint Online'dan erişebilir, ancak CDN         |
|Kullanıcı 4     |klasör1'e erişimi var, ancak SharePoint Online'da image1.jpg erişimi açıkça reddedildi         |SharePoint Online'dan varlığa erişilemiyor, ancak SharePoint Online'da dosyaya erişimi reddedilse de varlığa CDN erişebilir         |

<a name="CDNTroubleshooting"></a>

## <a name="troubleshooting-the-office-365-cdn"></a>Office 365 CDN sorunlarını giderme

<a name="CDNConfirm"></a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a>Varlıkların CDN tarafından sunulduğundan emin Nasıl yaparım??

Bir sayfaya CDN varlıkların bağlantılarını ekledikten sonra, sayfaya göz atarak, görüntü işlendikten sonra resme sağ tıklayarak ve görüntü URL'sini gözden geçirerek varlığın CDN sunulduğundan emin olabilirsiniz.

Ayrıca, tarayıcınızın geliştirici araçlarını kullanarak sayfadaki her bir varlığın URL'sini görüntüleyebilir veya bir üçüncü taraf ağ izleme aracı kullanabilirsiniz.

> [!NOTE]
> Varlıklarınızı bir SharePoint sayfasından işleme dışında test etmek için Fiddler gibi bir ağ aracı kullanıyorsanız, URL'nin SharePoint Online kiracınızın kök URL'si olduğu GET isteğine "Başvuran: `https://yourdomain.sharepoint.com`" başvuran üst bilgisini el ile eklemeniz gerekir.

CDN URL'lerini doğrudan web tarayıcısında test edemezsiniz çünkü SharePoint Online'dan gelen bir başvuru sahibiniz olmalıdır. Ancak, CDN varlık URL'sini bir SharePoint sayfasına ekler ve sonra sayfayı tarayıcıda açarsanız, sayfada CDN varlığının işlendiğini görürsünüz.

Microsoft Edge tarayıcısında geliştirici araçlarını kullanma hakkında daha fazla bilgi için bkz. [Geliştirici Araçları Microsoft Edge](/microsoft-edge/devtools-guide).

CDN çalıştığınızı doğrulamayı gösteren [SharePoint Geliştirici Desenleri ve Uygulamaları YouTube kanalında](https://aka.ms/sppnp-videos) barındırılan kısa bir videoyu izlemek için bkz. [CDN kullanımınızı doğrulama ve en iyi ağ bağlantısını sağlama](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5).

### <a name="why-are-assets-from-a-new-origin-unavailable"></a>Yeni bir kaynaktan gelen varlıklar neden kullanılamıyor?
Kaydın CDN yayılması ve varlıkların kaynaktan CDN depolama alanına yüklenmesi zaman aldığından, yeni kaynaklardaki varlıklar hemen kullanılamaz. Varlıkların CDN kullanılabilir olması için gereken süre, kaç varlık ve dosya boyutuna bağlıdır.

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a>İstemci tarafı web bölümüm veya SharePoint Framework çözümüm çalışmıyor

Genel kaynaklar için Office 365 CDN etkinleştirdiğinizde, CDN hizmeti otomatik olarak şu varsayılan kaynakları oluşturur:

+ */MASTERPAGE
+ */STYLE LIBRARY
+ */CLIENTSIDEASSETS

*/clientsideassets kaynağı eksikse, SharePoint Framework çözümler başarısız olur ve hiçbir uyarı veya hata iletisi oluşturulmaz. CDN _-NoDefaultOrigins_ parametresi **$true** olarak ayarlandığından veya kaynak el ile silindiğinden bu kaynak eksik olabilir.

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

**SharePoint Çevrimiçi Yönetim Kabuğu** PowerShell modülünü veya Office 365 **CLI'yı kullanarak Office 365 CDN** ile çalışmayı seçebilirsiniz.

+ [SharePoint Online Management Shell'i kullanmaya başlama](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
+ [Office 365 CLI'yi yükleme](https://pnp.github.io/cli-microsoft365/user-guide/installing-cli/)

## <a name="see-also"></a>Ayrıca bkz.

[İçerik Teslim Ağları](./content-delivery-networks.md)

[Network planning and performance tuning for Office 365](./network-planning-and-performance.md)

[SharePoint Performans Serisi - Office 365 CDN video serisi](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
