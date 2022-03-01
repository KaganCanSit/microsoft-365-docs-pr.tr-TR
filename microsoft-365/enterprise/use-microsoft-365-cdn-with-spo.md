---
title: SharePoint Online ile Office 365 Content Delivery Network (CDN) kullanma
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: SharePoint Online varlıklarınızı Office 365 Content Delivery Network için CDN (SharePoint) kullanma hakkında bilgi alın.
ms.openlocfilehash: ad4eb1df63e201e49ba0b4c56c9123a04e37c184
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63005477"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a>CDN Online ile Office 365 Content Delivery Network (CDN) SharePoint kullanma

SharePoint Online sayfalarınıza daha iyi performans sağlamak üzere statik varlıkları barındırmak için Office 365 Content Delivery Network (CDN) yerleşik SharePoint kullanabilirsiniz. Bu Office 365 CDN, statik varlıkları istekte bulunan tarayıcılara yaklaştırarak performansı geliştirmektedir ve bu da indirmeleri hızlandırmak ve gecikme süresini azaltmaya yardımcı olur. Ayrıca, Office 365 CDN [http/2 protokolünü](https://en.wikipedia.org/wiki/HTTP/2), geliştirilmiş sıkıştırma ve HTTP pipelining için kullanır. Office 365 CDN Hizmeti, SharePoint Online aboneliğinizin bir parçası olarak dahil edilir.

> [!NOTE]
> Ürün Office 365 CDN yalnızca Üretim (dünya çapında) **bulutunda** bulunan kiracılar tarafından kullanılabilir. ABD Kamu, Çin ve Almanya bulutlarında yer alan kiracılar şu anda bu Office 365 CDN.

Kaynak Office 365 CDN birden çok konumda veya kaynakta statik varlıkları barındırmana ve bunları genel yüksek hızlı ağlardan hizmet vermesine olanak sağlayan birden çok CDN'den oluşur. Kaynak 2013'te barındırmak istediğiniz içeriğin türüne Office 365 CDN, özel kökenleri veya **her ikisini birden** ebilirsiniz. Genel [ve özel kaynak arasındaki fark hakkında daha fazla bilgi için bkz.](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) Her kaynağın genel mi yoksa özel mi olacağını seçme.

![Office 365 CDN diyagramı oluşturma.](../media/O365-CDN/o365-cdn-flow-transparent.png "Office 365 CDN kavramsal diyagramı")

CDNs'lerin çalışma yolunu zaten biliyorsanız, kiracınız için Office 365 CDN yalnızca birkaç adımı tamamlamanız gerekir. Bu konuda nasıl olduğu açıklanmıştır. Statik varlıklarınızı barındırmaya başlama hakkında bilgi için okumaya devam edin.

> [!TIP]
> Microsoft tarafından barındırılan ve özel kullanım senaryoları için Office 365 ile kullanılmaktadır ancak bu konuda ele alınmayacak başka Microsoft tarafından barındırılan CDN'ler de vardır, çünkü bunlar Office 365 CDN. Daha fazla bilgi için bkz. [Diğer Microsoft CDN'leri](content-delivery-networks.md#other-microsoft-cdns).

 **Daha fazla bilgi [için ağ planlaması ve performans ayarı Office 365](./network-planning-and-performance.md).**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a>SharePoint Online'da Office 365 CDN ile çalışmaya genel bakış

E-Office 365 CDN ayarlamak için şu temel adımları izleyin:

+ [Dağıtım planı için Office 365 CDN](use-microsoft-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  + [Kaynakta hangi statik varlıkları barındırmak istediğiniz CDN](use-microsoft-365-cdn-with-spo.md#CDNAssets).
  + [Varlıklarınızı nerede depolamak istediğinize karar verenin](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets). Bu konum, SharePoint, kitaplık veya klasör olabilir ve kaynak _olarak adlandırılan bir konum olabilir_.
  + [Her kaynağın genel mi yoksa özel mi olacağını seçin](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Hem genel hem de özel türlerin birden çok kaynağını  eklersiniz.

+ PowerShell veya CDN Online CLI kullanarak SharePoint ayarlayın ve yapılandırın

  + [Çevrimiçi Yönetim Kabuğu'CDN kullanarak varsayılan SharePoint ayarlama ve yapılandırma](use-microsoft-365-cdn-with-spo.md#CDNSetupinPShell)
  + [PnP PowerShell CDN ayarlama ve yapılandırma](use-microsoft-365-cdn-with-spo.md#CDNSetupinPnPPosh)
  + [OFFICE 365 CLI kullanarak CDN ayarlama ve yapılandırma](use-microsoft-365-cdn-with-spo.md#CDNSetupinCLI)

  Bu adımı tamamlarken şunları edin:

  + Varsayılan CDN etkinleştirildi.
  + Kaynaklarınızı eklenmiştir ve her bir kaynak genel veya özel olarak tanımlenmiştir.

Kurulum tamam olduktan sonra Zaman [içinde Office 365 CDN](use-microsoft-365-cdn-with-spo.md#CDNManage) yönetebilirsiniz:

+ Varlıkları ekleme, güncelleştirme ve kaldırma
+ Kaynak ekleme ve kaldırma
+ İlkeleri CDN yapılandırma
+ Gerekirse, devre dışı bırakma CDN

Son olarak, [hem genel CDN özel](use-microsoft-365-cdn-with-spo.md#using-your-cdn-assets) kaynaklardan CDN için Kaynak varlıklarınızı kullanma'ya bakın.

Sık [karşılaşılan Office 365 CDN](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting) ilgili yol gösterici bilgi için bkz. Yardım konularına bakın.

## <a name="plan-for-deployment-of-the-office-365-cdn"></a>Dağıtım planı için Office 365 CDN

Kiracınız için Office 365 CDN dağıtmadan Office 365 planlama sürecinizin bir parçası olarak aşağıdaki faktörleri göz önünde bulundurarak değerlendirmeniz gerekir.

  + [Kaynakta hangi statik varlıkları barındırmak istediğiniz CDN](use-microsoft-365-cdn-with-spo.md#CDNAssets)
  + [Varlıklarınızı nerede depolamak istediğinize karar belirleme](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets)
  + [Her kaynağın genel mi yoksa özel mi olacağını seçme](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

<a name="CDNAssets"> </a>
### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a>Kaynakta hangi statik varlıkları barındırmak istediğiniz CDN

Genel olarak, CDN'ler statik varlıkları veya çok sık değişmeen varlıkları barındırmak için etkilidir. Şu koşulların bir veya birkaçı ile karşılaşan dosyaları tanımlamak iyi bir kuraldır:

+ Sayfaya eklenmiş statik dosyalar (betikler ve resimler gibi), sayfa yükleme sürelerini önemli ölçüde artımlı olarak etkileyebilir
+ Yürütülebilir dosyalar ve yükleme dosyaları gibi büyük dosyalar
+ İstemci tarafı kodunu destekleyen kaynak kitaplıkları

Örneğin, site resimleri ve betikler gibi sürekli olarak istenen küçük dosyalar, site işleme performansını önemli ölçüde geliştirebilir ve bunları bir kaynak kaynağına eklerken SharePoint Online sitelerinin yükü artımlı olarak CDN azaltır. Yükleme yürütülebilir dosyaları gibi daha büyük dosyalar CDN'den indirilebilir ve bu da çok sık erişilmese bile olumlu bir performans etkisi sağlar ve SharePoint Online siteniz üzerindeki yükü daha sonra azaltmaya yardımcı olur.

Dosya başına performans iyileştirme, istemcinin en yakın CDN uç noktasına yakınlığı, yerel ağda geçici koşullar vb. gibi birçok etmene bağlıdır. Birçok statik dosya oldukça küçüktür ve dosyalardan Office 365 saniye içinde indirilebilir. Bununla birlikte, bir web sayfasında, bir kaç saniyelik bir indirme süresi olan birçok ekli dosya olabilir. Bu dosyaların ilk sayfadan CDN, toplam sayfa yükleme süresini önemli ölçüde azaltır. Örneğin[, Bir e-CDN ne performans](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) kazançları sağlar? örneğin bkz.

<a name="CDNStoreAssets"> </a>
### <a name="determine-where-you-want-to-store-your-assets"></a>Varlıklarınızı nerede depolamak istediğinize karar belirleme

Kaynak CDN, varlıklarınızı kaynak olarak adlandırılan bir konumdan _getirir_. Köken, URL SharePoint erişilebilen bir site, belge kitaplığı veya klasör olabilir. Kuruluşun kaynaklarını belirtirken büyük bir esnekliğiniz olur. Örneğin, birden çok kaynağı veya kaynak olarak tüm kaynaklarınızı koymak istediğiniz CDN belirtsiniz. Hem genel hem de özel kaynaklarda yer a seçebilirsiniz. Çoğu kuruluş bu ikisi için bir birleşim uygulamayı seçer.

Kaynak olarak klasörler veya belge kitaplıkları gibi yeni kapsayıcılar oluşturabilir ve ilk kapsayıcıda kullanılabilir hale gelen dosyalar CDN. CDN'de kullanılabilir durumda olmak istediğiniz belirli bir varlık kümeniz varsa ve CDN varlık kümelerini kapsayıcıda yalnızca bu dosyalar ile kısıtlamak istiyorsanız, bu yaklaşım iyi bir yaklaşımdır.

Var olan bir site koleksiyonunu, siteyi, kitaplığı veya klasörü kaynak olarak yapılandırabilirsiniz ve kapsayıcıda bulunan tüm uygun varlıklar kaynak klasörden CDN. Var olan bir kapsayıcıyı kaynak olarak eklemeden önce, bu kapsayıcının içeriğini ve izinlerini bildiğinizden emin olun, böylece varlıkları istemeden anonim erişime veya yetkisiz kullanıcılara açık hale gelirsiniz.

Kaynak içeriği _CDN için_ farklı ilkeler CDN. CDN ilkeleri, dosya türü ve _site_ sınıflandırması gibi özniteliklere göre genel veya özel kaynaklarda bulunan varlıkları dışlar ve ilkede belirttiğiniz CdnType (özel veya genel) tüm kaynaklarında uygulanır. Örneğin, birden çok alt site içeren bir siteden oluşan bir özel kaynak eklerseniz, Gizli olarak işaretlenmiş siteleri dışarıda tutmak için bir ilke tanımlayabilirsiniz; bu sınıflandırma  uygulanmış olan sitelerden içerik servis CDN. İlke, ekli _kaynaklarda yer_ alan tüm özel kaynaklarda yer alan içeriğe CDN.

Kaynak sayısını ne kadar büyük olursa, istekleri işlemesi için kaynak hizmet CDN zaman içinde o kadar büyük bir etki olduğunu unutmayın. Kaynak sayısını mümkün olduğunca fazla sınırlandırmanizi öneririz.

<a name="CDNOriginChoosePublicPrivate"> </a>
### <a name="choose-whether-each-origin-should-be-public-or-private"></a>Her kaynağın genel mi yoksa özel mi olacağını seçme

Bir kaynağı tanımlığında, genel mi yoksa özel mi _olacağını belirtirsiniz_. Ortak kaynaklarda CDN erişim anonimdir ve özel CDN içeriklerin güvenliği daha yüksek güvenlik için dinamik olarak oluşturulan belirteçler tarafından güvence altına alınır. Hangi seçeneği tercih ederseniz belirtin, söz konusu yönetim söz konusu olduğunda Microsoft tüm ağır CDN yapar. Ayrıca, daha sonra kaynaklarınızı ayardikten ve kaynaklarınızı belirledikten CDN fikir değiştirebilirsiniz.

Hem genel hem de özel seçenekler benzer performans kazançları sağlar, ancak her seçeneğin benzersiz öznitelikleri ve avantajları vardır.

**Kaynakta** yer alan Office 365 CDN anonim olarak erişilebilir ve barındırılan varlıklara, varlığın URL'si olan herkes tarafından erişilebilir. Genel kaynaklarda içeriğe erişim anonim olduğundan, bunları yalnızca JavaScript dosyaları, betikler, simgeler ve resimler gibi hassas olmayan genel içeriği önbelleğe alırsiniz.

**Site** içindeki özel Office 365 CDN, SharePoint Online belge kitaplıkları, siteler ve özel resimler gibi kullanıcı içeriğine özel erişim sağlar. Özel kaynaklarda içeriğe erişim dinamik olarak oluşturulan belirteçler tarafından güvence altına alınır, dolayısıyla bu içeriğe yalnızca özgün belge kitaplığı veya depolama konumu izinleri olan kullanıcılar tarafından erişilebilir. Office 365 CDN'daki özel varlıklar yalnızca SharePoint Online içeriği için kullanılabilir ve SharePoint Online kiracınızı yeniden yönlendirme yoluyla özel kaynaklarda yer alan varlıklara erişebilirsiniz.

Özel kaynakta yer alan varlıklara CDN nasıl eriş erişilen hakkında daha fazla bilgi için Özel kaynaklarda varlıkları [kullanma makalesinde okuyabilirsiniz](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins).

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a>Varlıkları genel kaynaklarda barındırmanın öznitelikleri ve avantajları

+ Genel kökende açığa açığa çıkaran varlıklara herkes anonim olarak erişmektedir.
    > [!IMPORTANT]
    > Hiçbir zaman kullanıcı bilgileri içeren veya genel olarak organizasyona duyarlı kabul edilen kaynakları değerlendirmeniz gerekir.

+ Bir varlığı genel kaynaktan kaldırırsanız, mal önbellekten 30 gün boyunca kullanılabilir olmaya devam eder; ancak 15 dakika içinde e-postada CDN geçersiz kılınacak.

+ Genel kaynak olarak stil sayfalarını (CSS dosyaları) barındırıyorken, kod içindeki göreli yolları ve  URL'leri kullanabilirsiniz. Bu, adı geçen varlığın konumuyla ilgili olarak arka plan resimleri ve diğer nesnelerin konumlarını başvurabilirsiniz.

+ Genel bir kaynağın URL'sini hazır bulundurabilirsiniz, ancak dikkatli olmalı ve sayfa bağlam özelliğinden faydalanmalı ve bunu yapmak için yönergeleri takip etlisiniz. Bunun nedeni, URL'nin CDN Veritabanına erişimin kullanılamaz hale gelirse, SharePoint Online'da url'nin otomatik olarak çözülmezse bağlantılarının koparak başka hatalara neden olabileceğidir. URL de değişebilir ve bu nedenle geçerli değerine sabit kodlu olarak kodlanmayacaktır.

+ Genel kökenler için dahil edilen varsayılan dosya türleri .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, .woff ve .woff2'tir. Ek dosya türleri belirtebilirsiniz.

+ Belirttiğiniz site sınıflandırmalarına göre tanımlanan varlıkları dışarıda tutmak için bir ilke yapılandırabilirsiniz. Örneğin, izin verilen dosya türünde olsalar ve genel kaynakta yer alıyor olsalar bile "gizli" veya "kısıtlanmış" olarak işaretlenmiş tüm varlıkları hariç tutabilirsiniz.

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a>Varlıkları özel kaynaklarda barındırmanın öznitelikleri ve avantajları

+ Özel varlıklar yalnızca çevrimiçi varlıklar için SharePoint kullanılabilir.

+ Kullanıcılar özel kökenden varlıklara ancak kapsayıcıya erişim izinleri varsa erişim sağlar. Bu varlıklara anonim erişim engellenebilir.

+ Özel kaynaklarda yer alan varlıklar çevrimiçi kiracıdan SharePoint gerekir. Özel veya özel CDN doğrudan erişim çalışmaz.

+ Bir varlığı özel kaynaktan kaldırırsanız, önbellekten bir saate kadar kullanılabilir olmaya devam eder; ancak, varlık kaldırma işlemi CDN 15 dakika içinde var olan varlık bağlantılarını geçersiz kılınz.

+ Özel kökenler için varsayılan dosya türleri .gif, .ico, .jpeg, .jpg, .js ve .png. Ek dosya türleri belirtebilirsiniz.

+ Genel kaynaklarda olduğu gibi, bir klasör veya belge kitaplığı içindeki tüm varlıkları eklemek için joker karakterler kullansanız bile, belirttiğiniz site sınıflandırmaları tarafından tanımlanan varlıkları dışarıda tutmak için bir ilke yapılandırabilirsiniz.

Office 365 kiracınız ile kullanabileceğiniz Office 365 CDN, genel CDN kavramlarını ve diğer Microsoft CDN'lerini neden kullanabileceğiniz hakkında daha fazla bilgi için bkz. İçerik Teslim [Ağları](content-delivery-networks.md).

### <a name="default-cdn-origins"></a>Varsayılan CDN kaynak

Aksini belirtmedikçe, Office 365 etkinleştirmeniz bazı varsayılan kaynak ayarlarını Office 365 CDN. Başlangıçta sağlamamayı tercih ediyorsanız, kurulumu tamamladikten sonra bu kökenleri  eklersiniz. Varsayılan kaynak kurulumunu atlamanın sonuçlarını anlamadıysanız ve bunun belirli bir nedeni yoksa, varsayılan ayarı etkinleştirirken onların oluşturulmalarına izin CDN.

Varsayılan özel CDN kaynaktır:

+ \*/userphoto.aspx
+ \*/siteassets

Varsayılan genel CDN kaynaktır:

+ \*/masterpage
+ \*/style library
+ \*/clientsideassets

> [!NOTE]
> _clientsideassets_, aralık 2017'de Office 365 CDN hizmetine eklenen varsayılan genel kaynaktır. Çalışma 2013'te çözüm SharePoint Framework için bu CDN olması gerekir. İlk ayarı Office 365 CDN Aralık 2017'den önce etkinleştirdiyseniz veya kaynağı etkinleştirdikten sonra varsayılan kaynak kurulumunu CDN, bu kaynağı el ile ekleyebilirsiniz. Daha fazla bilgi [için bkz. İstemci tarafı web bölümüm veya SharePoint Framework çözüm çalışmıyor](use-microsoft-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).

<a name="CDNSetupinPShell"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>SharePoint Online Yönetim Kabuğu'Office 365 CDN ayarlama ve yapılandırma

Bu bölümdeki yordamlar için, SharePoint Online'a bağlanmak için SharePoint gerekir. Yönergeler için bkz. [Bağlan Online PowerShell SharePoint e yükleme](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

çevrimiçi Yönetim Kabuğu'CDN kullanarak SharePoint Online'da varlıklarınızı barındırmak üzere SharePoint adımları tamamlayın.

<details>
  <summary>Genişletmek için tıklayın</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Kuruluşun diğer özellikleri kullanmalarını Office 365 CDN

Kiracının son ayarlarını değiştirmeden CDN, kiracınız için özel güvenlik CDN durumunu Office 365 gerekir. Bağlan Çevrimiçi Yönetim Kabuğu'SharePoint kiracınıza geri alın:

```powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

Şimdi, **Get-SPOTenantCdnEnabled** cmdlet'ini kullanarak kiracıdan CDN ayarları alın:

```powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

Belirtilen CdnType CDN dosyanın durumu ekrana çıktısı olarak gelir.

**Set-SPOTenantCdnEnabled** cmdlet'ini kullanarak kuruluş bu cmdlet'i Office 365 CDN. Kuruluş genel kaynaklarınızı, özel kaynaklarınızı veya her ikisini de aynı anda kullanmalarını s sağlar. Ayrıca, ayarları CDN varsayılan kaynak ayarlarını atlayıp atlamayı da yapılandırabilirsiniz. Bu kökenleri daha sonra bu konuda açıklandığı gibi daha sonra istediğiniz zaman  eklersiniz.

Windows PowerShell Online için SharePoint'de:

```powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Örneğin, kuruluşun hem genel hem de özel kaynak kullanımına izin vermek için aşağıdaki komutu yazın:

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Kuruluşta hem genel hem de özel kökenleri kullanmalarını sağlamak, ancak varsayılan kaynak ayarlarını atlamak için aşağıdaki komutu yazın:

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Varsayılan [CDN etkinleştirme sırasında](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) varsayılan olarak sağlanan kaynaklarla ilgili bilgiler için varsayılan kaynak Office 365 CDN ve varsayılan kaynak kurulumlarını atlamanın olası etkileri hakkında bilgi için bkz.

Kuruluş genel kaynak kullanımına olanak sağlamak için aşağıdaki komutu yazın:

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

Kuruluşta özel kökenleri kullanmalarını sağlamak için, aşağıdaki komutu yazın:

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

Bu cmdlet hakkında daha fazla bilgi için bkz. [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

<a name="Office365CDNforSPOFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Dosya türleri listesini dosyaya eklemek için değiştirme (Office 365 CDN)

> [!TIP]
> **Set-SPOTenantCdnPolicy** cmdlet'ini kullanarak dosya türlerini tanımladığınız zaman, o anda tanımlanmış olan listenin üzerine yazmanız gerekir. Listeye başka dosya türleri eklemek için önce cmdlet'i kullanarak hangi dosya türlerine zaten izin verilmiyor ve yeni dosya türleriyle birlikte bu türler de listeye dahil edildi.

Küme içinde genel ve özel kökenler tarafından barındırılan statik dosya türlerini tanımlamak için **Set-SPOTenantCdnPolicy** cmdlet'ini CDN. Varsayılan olarak, yaygın varlık türlerine izin verilir (.css, .gif, .jpg, ve .js.

Windows PowerShell Online için SharePoint'de:

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Örneğin, .css CDN dosyaları barındırmak .png etkinleştirmek için şu komutu girmeniz gerekir:

```powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

O anda hangi dosya türlerine izin verilmiyor? CDN **Get-SPOTenantCdnPolicies** cmdlet'ini kullanın:

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Bu cmdlet'ler hakkında daha fazla bilgi için bkz. [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) ve [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Sınıflandırmaların dışında tutmak istediğiniz site sınıflandırmalarının listesini değiştirme (Office 365 CDN)

> [!TIP]
> **Set-SPOTenantCdnPolicy** cmdlet'ini kullanarak site sınıflandırmalarını dışarıda bıraksanız bile, o anda tanımlanmış olan listenin üzerine yazmazsanız. Ek site sınıflandırmalarını dışarıda tutmak için önce cmdlet'i kullanarak hangi sınıflandırmaların zaten hariç tutuldiğini bulun ve yeni sınıflandırmalarla birlikte ekleyin.

Küme üzerinde kullanılabilir yapmak istediğiniz site sınıflandırmalarını dışarıda tutmak için **Set-SPOTenantCdnPolicy** cmdlet'ini CDN. Varsayılan olarak, site sınıflandırmaları dahil değildir.

Windows PowerShell Online için SharePoint'de:

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

Şu anda kısıtlanmış site sınıflandırmalarını görmek için **Get-SPOTenantCdnPolicies** cmdlet'ini kullanın:

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Döndürülen özellikler _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications ve_ _ExcludeIfNoScriptDisabled'dır_.

_IncludeFileExtensions_ özelliği, hizmet dosyasından gelen dosya uzantılarının listesini CDN.

> [!NOTE]
> Varsayılan dosya uzantıları ortak ve özel arasında farklıdır.

_ExcludeRestrictedSiteClassifications özelliği_, sınıflandırmaların dışında tutmak istediğiniz site sınıflandırmalarını CDN. Örneğin, Gizli olarak işaretlenmiş siteleri hariç **tutabilirsiniz**; böylece sınıflandırma uygulanmış olan sitelerde bu sınıflandırmaya hizmet CDN.

_ExcludeIfNoScriptDisabled özelliği_, site CDN _NoScript_ öznitelik ayarlarına bağlı olarak içeriği dışlar. Varsayılan olarak, _NoScript özniteliği_ Modern siteler için **Etkin ve** _Klasik siteler_ için **Devre Dışı** _olarak_ ayarlanır. Bu, kiracı ayarlarınıza bağlıdır.

Bu cmdlet'ler hakkında daha fazla bilgi için bkz. [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) ve [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOOriginPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>Varlıklarınız için kaynak ekleme

Bir kaynak **tanımlamak için Add-SPOTenantCdnOrigin** cmdlet'ini kullanın. Birden çok kaynak tanımlayabilirsiniz. Kaynak, ana bilgisayar tarafından barındır SharePoint istediğiniz varlıkları içeren bir kitaplık veya klasöre CDN.

> [!IMPORTANT]
> Hiçbir zaman kullanıcı bilgileri içeren veya genel olarak organizasyona duyarlı kabul edilen kaynakları değerlendirmeniz gerekir.

```powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

Yol değeri _,_ varlıkları içeren kitaplık veya klasörün göreli yoludur. Göreli yollara ek olarak joker karakterler de kullanabilirsiniz. Kökenler, URL'ye hazır joker karakterleri destekler. Bu, birden çok siteyi kapsayan kökenler oluşturmanıza olanak sağlar. Örneğin, tüm sitelerinizi ana sayfalar klasöründe bulunan varlıkları kaynak bilgisinde genel kaynak olarak CDN, aşağıdaki komutu yazın:

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ * joker karakter değiştiricisi ***/** yalnızca yolun başında kullanılabilir ve belirtilen URL'nin altındaki tüm URL kesimlerini eşler.
+ Yol bir belge kitaplığına, klasöre veya siteye işaret ediyor olabilir. Örneğin, _*/site1 yolu sitenin_ altındaki tüm belge kitaplıklarını eşler.

Belirli bir göreli yol ile bir kaynak  eklersiniz. Tam yolu kullanarak bir kaynak ekamazsiniz.

Bu örnekte, belirli bir sitede site parçaları kitaplığının özel kaynağı ek açıklama yer almaktadır:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Bu örnek, site koleksiyonunun site _varlıkları kitaplığında klasör1_ klasörünün özel kaynağını ekler:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

Yolda boşluk varsa, yolu çift tırnak içine veya %20 URL kodlaması ile değiştirebilirsiniz. Aşağıdaki örnekler, site koleksiyonunun site varlıkları _kitaplığında yer alan klasör 1_ klasörünün özel kaynağını ekler:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

Bu komut ve söz dizimi hakkında daha fazla bilgi için bkz [. Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

> [!NOTE]
> Özel kaynaklarda, bir kaynaktan paylaşılan varlıklara kaynak olarak erişilmeden önce yayımlanan ana sürümlerden biri CDN.

Siz komutu çalıştırarak, sistem yapılandırmayı veri merkezi genelinde eşitler. Bu, 15 dakika kadar sürebilir.

<a name="ExamplePublicOrigin"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Örnek: Ana sayfalarınız için ve SharePoint Online için stil kitaplığınız için genel SharePoint yapılandırma

Normalde, varsayılan ayarı etkinleştirerek bu kökenler sizin için Office 365 CDN. Bununla birlikte, bunları el ile etkinleştirmek için aşağıdaki adımları izleyin.

+ Stil **kitaplığını genel kaynak olarak tanımlamak için Add-SPOTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ Ana sayfaları **genel kaynak olarak tanımlamak için Add-SPOTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Bu komut ve söz dizimi hakkında daha fazla bilgi için bkz [. Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Siz komutu çalıştırarak, sistem yapılandırmayı veri merkezi genelinde eşitler. Bu, 15 dakika kadar sürebilir.

<a name="ExamplePrivateOrigin"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Örnek: SharePoint Online için site varlıklarınız, site sayfalarınız ve yayımlama resimleriniz için özel SharePoint yapılandırma

+ Site varlıkları **klasörünü özel kaynak olarak tanımlamak için Add-SPOTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ Site sayfaları **klasörünü özel bir kaynak olarak tanımlamak için Add-SPOTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ Yayımlama resimleri **klasörünü özel bir kaynak olarak tanımlamak için Add-SPOTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Bu komut ve söz dizimi hakkında daha fazla bilgi için bkz [. Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Siz komutu çalıştırarak, sistem yapılandırmayı veri merkezi genelinde eşitler. Bu, 15 dakika kadar sürebilir.

<a name="ExamplePrivateOriginSiteCollection"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Örnek: SharePoint Online için site koleksiyonu için özel SharePoint yapılandırma

Bir site **koleksiyonunu özel kaynak olarak tanımlamak için Add-SPOTenantCdnOrigin** cmdlet'ini kullanın. Örneğin:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Bu komut ve söz dizimi hakkında daha fazla bilgi için bkz [. Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Siz komutu çalıştırarak, sistem yapılandırmayı veri merkezi genelinde eşitler. SharePoint Online _kiracısı_ CDN hizmetine bağlandığından, Yapılandırma beklemede iletisiyle CDN alabilirsiniz. Bu, 15 dakika kadar sürebilir.

<a name="CDNManage"> </a>
### <a name="manage-the-office-365-cdn"></a>Posta Office 365 CDN

Yapılandırmayı bir kez CDN, içeriği güncelleştirken veya ihtiyaçlar değiştiksinde, bu bölümde açıklandığı gibi yapılandırmanız üzerinde değişiklikler yapabilirsiniz.

<a name="Office365CDNforSPOaddremoveasset"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Varlıklar ekleme, güncelleştirme veya kaldırma Office 365 CDN

Kurulum adımlarını tamamlandıktan sonra, istediğiniz zaman yeni varlıklar ekleyebilir, var olan varlıkları güncelleştirebilirsiniz veya kaldırabilirsiniz. Kaynak olarak tanım istediğiniz klasör veya kitaplıkta SharePoint değişikliklerinizi yapın. Yeni bir varlık eklersiniz, bu varlık e-CDN kullanılabilir. Ancak, varlığı güncellersanız, yeni kopyanın yayılması ve bu kopyanın kullanılabilir olması 15 dakika CDN.

Kaynağın konumunu geri almak için **Get-SPOTenantCdnOrigins** cmdlet'ini kullanabilirsiniz. Bu cmdlet'in nasıl kullanımı hakkında bilgi için bkz. [Get-SPOTenantCdnOrigins](/powershell/module/sharepoint-online/Get-SPOTenantCdnOrigins).

<a name="Office365CDNforSPORemoveOriginPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Kaynak kaynak Office 365 CDN

Kaynak olarak tanım istediğiniz klasöre veya SharePoint erişimini kaldırabilirsiniz. Bunu yapmak için **Remove-SPOTenantCdnOrigin** cmdlet'ini kullanın.

```powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Bu cmdlet'in nasıl kullanımı hakkında bilgi için bkz. [Remove-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Remove-SPOTenantCdnOrigin).

<a name="Office365CDNforSPOModifyOrigin"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Kaynakta bir kaynağı Office 365 CDN

Oluşturduğunuz bir kaynağı değiştiremezsiniz. Bunun yerine, kaynağı kaldırın ve yeni bir tane ekleyin. Daha fazla bilgi için bkz[. Kaynak kaynak Office 365 CDN](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPosh) [Kaynak eklemek için ve Varlıklarınızı kaynak eklemek için](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Seçeneği devre dışı Office 365 CDN

**Set-SPOTenantCdnEnabled cmdlet'ini** kullanarak, CDN için bu cmdlet'i kullanın. Kaynak etkinleştirilmiş hem genel hem de özel CDN varsa, aşağıdaki örneklerde gösterildiği gibi cmdlet'i iki kez çalıştırmalısiniz.

Kaynakta genel kaynak kullanımını devre dışı CDN için, aşağıdaki komutu girin:

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

Kaynak 2013'te özel kaynak kullanımını CDN için aşağıdaki komutu girin:

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

Bu cmdlet hakkında daha fazla bilgi için bkz. [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

</details>

<a name="CDNSetupinPnPPosh"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-pnp-powershell"></a>PnP PowerShell Office 365 CDN ayarları ve yapılandırma

Bu bölümdeki yordamlarda, SharePoint Online'a bağlanmak için PnP PowerShell SharePoint gerekir. Yönergeler için bkz [. PnP PowerShell ile çalışmaya başlama](https://github.com/SharePoint/PnP-PowerShell#getting-started).

PnP PowerShell kullanarak SharePoint Online'da varlıklarınızı barındırmak üzere CDN ayarlamak ve yapılandırmak için bu adımları tamamlayın.

<details>
  <summary>Genişletmek için tıklayın</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Kuruluşun diğer özellikleri kullanmalarını Office 365 CDN

Kiracının son ayarlarını değiştirmeden CDN, kiracınız için özel güvenlik CDN durumunu Office 365 gerekir. Bağlan PnP PowerShell kullanarak kiracınıza şunları  olur:

```powershell
Connect-PnPOnline -Url https://contoso-admin.sharepoint.com -UseWebLogin
```

Şimdi, **Get-PnPTenantCdnEnabled** cmdlet'ini kullanarak kiracıdan CDN ayarları alın:

```powershell
Get-PnPTenantCdnEnabled -CdnType <Public | Private>
```

Belirtilen CdnType CDN dosyanın durumu ekrana çıktısı olarak gelir.

Kuruluş bu **cmdlet'ini**, yalnızca bu cmdlet'i kullanarak Office 365 CDN. Kuruluş genel kaynaklarınızı, özel kaynaklarınızı veya her ikisini aynı anda kullanmalarını sabilirsiniz. Ayrıca, ayarları CDN varsayılan kaynak ayarlarını atlayıp atlamayı da yapılandırabilirsiniz. Bu kökenleri daha sonra bu konuda açıklandığı gibi daha sonra istediğiniz zaman  eklersiniz.

PnP PowerShell'de:

```powershell
Set-PnPTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Örneğin, kuruluşun hem genel hem de özel kaynak kullanımına izin vermek için aşağıdaki komutu yazın:

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true
```

Kuruluşta hem genel hem de özel kökenleri kullanmalarını sağlamak, ancak varsayılan kaynak ayarlarını atlamak için aşağıdaki komutu yazın:

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Varsayılan [CDN etkinleştirme sırasında](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) varsayılan olarak sağlanan kaynaklarla ilgili bilgiler için varsayılan kaynak Office 365 CDN ve varsayılan kaynak kurulumlarını atlamanın olası etkileri hakkında bilgi için bkz.

Kuruluş genel kaynak kullanımına olanak sağlamak için aşağıdaki komutu yazın:

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $true
```

Kuruluşta özel kökenleri kullanmalarını sağlamak için, aşağıdaki komutu yazın:

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $true
```

Bu cmdlet hakkında daha fazla bilgi için bkz. [Set-PnPTenantCdnEnabled](/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled).

<a name="Office365CDNforPnPPoshFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Dosya türleri listesini dosyaya eklemek için değiştirme (Office 365 CDN)

> [!TIP]
> **Dosya türlerini Set-PnPTenantCdnPolicy** cmdlet'ini kullanarak tanımladığınız zaman, o anda tanımlanmış olan listenin üzerine yazmanız gerekir. Listeye başka dosya türleri eklemek için önce cmdlet'i kullanarak hangi dosya türlerine zaten izin verilmiyor ve yeni dosya türleriyle birlikte bu türler de listeye dahil edildi.

Küme içinde genel ve özel kaynaklarla barındırılan statik dosya türlerini tanımlamak için **Set-PnPTenantCdnPolicy** cmdlet'ini CDN. Varsayılan olarak, yaygın varlık türlerine izin verilir (.css, .gif, .jpg, ve .js.

PnP PowerShell'de:

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Örneğin, .css CDN dosyaları barındırmak .png etkinleştirmek için şu komutu girmeniz gerekir:

```powershell
Set-PnPTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

O anda hangi dosya türlerine izin verilmiyor? CDN **Get-PnPTenantCdnPolicies** cmdlet'ini kullanın:

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

Bu cmdlet'ler hakkında daha fazla bilgi için bkz. [Set-PnPTenantCdnPolicy](/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy) ve [Get-PnPTenantCdnPolicies](/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies).

<a name="Office365CDNforPnPPoshSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Sınıflandırmaların dışında tutmak istediğiniz site sınıflandırmalarının listesini değiştirme (Office 365 CDN)

> [!TIP]
> **Set-PnPTenantCdnPolicy** cmdlet'ini kullanarak site sınıflandırmalarını dışarıda bıraksanız bile, o anda tanımlanmış olan listenin üzerine yazmazsanız. Ek site sınıflandırmalarını dışarıda tutmak için önce cmdlet'i kullanarak hangi sınıflandırmaların zaten hariç tutuldiğini bulun ve yeni sınıflandırmalarla birlikte ekleyin.

Küme üzerinde kullanılabilir yapmak istediğiniz site sınıflandırmalarını dışarıda tutmak için **Set-PnPTenantCdnPolicy** cmdlet'ini CDN. Varsayılan olarak, site sınıflandırmaları dahil değildir.

PnP PowerShell'de:

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications>"
```

Şu anda hangi site sınıflandırmaların kısıtlanmış olduğunu görmek için **Get-PnPTenantCdnPolicies** cmdlet'ini kullanın:

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

Döndürülen özellikler _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications ve_ _ExcludeIfNoScriptDisabled'dır_.

_IncludeFileExtensions_ özelliği, hizmet dosyasından gelen dosya uzantılarının listesini CDN.

> [!NOTE]
> Varsayılan dosya uzantıları ortak ve özel arasında farklıdır.

_ExcludeRestrictedSiteClassifications özelliği_, sınıflandırmaların dışında tutmak istediğiniz site sınıflandırmalarını CDN. Örneğin, Gizli olarak işaretlenmiş siteleri hariç **tutabilirsiniz**; böylece sınıflandırma uygulanmış olan sitelerde bu sınıflandırmaya hizmet CDN.

_ExcludeIfNoScriptDisabled özelliği_, site CDN _NoScript_ öznitelik ayarlarına bağlı olarak içeriği dışlar. Varsayılan olarak, _NoScript özniteliği_ Modern siteler için **Etkin ve** _Klasik siteler_ için **Devre Dışı** _olarak_ ayarlanır. Bu, kiracı ayarlarınıza bağlıdır.

Bu cmdlet'ler hakkında daha fazla bilgi için bkz. [Set-PnPTenantCdnPolicy](/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy) ve [Get-PnPTenantCdnPolicies](/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies).

<a name="Office365CDNforSPOOriginPnPPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>Varlıklarınız için kaynak ekleme

Bir kaynak **tanımlamak için Add-PnPTenantCdnOrigin** cmdlet'ini kullanın. Birden çok kaynak tanımlayabilirsiniz. Kaynak, ana bilgisayar tarafından barındır SharePoint istediğiniz varlıkları içeren bir kitaplık veya klasöre CDN.

> [!IMPORTANT]
> Hiçbir zaman kullanıcı bilgileri içeren veya genel olarak organizasyona duyarlı kabul edilen kaynakları değerlendirmeniz gerekir.

```powershell
Add-PnPTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

Yol değeri _,_ varlıkları içeren kitaplık veya klasörün göreli yoludur. Göreli yollara ek olarak joker karakterler de kullanabilirsiniz. Kökenler, URL'ye hazır joker karakterleri destekler. Bu, birden çok siteyi kapsayan kökenler oluşturmanıza olanak sağlar. Örneğin, tüm sitelerinizi ana sayfalar klasöründe bulunan varlıkları kaynak bilgisinde genel kaynak olarak CDN, aşağıdaki komutu yazın:

```powershell
Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ * joker karakter değiştiricisi ***/** yalnızca yolun başında kullanılabilir ve belirtilen URL'nin altındaki tüm URL kesimlerini eşler.
+ Yol bir belge kitaplığına, klasöre veya siteye işaret ediyor olabilir. Örneğin, _*/site1 yolu sitenin_ altındaki tüm belge kitaplıklarını eşler.

Belirli bir göreli yol ile bir kaynak  eklersiniz. Tam yolu kullanarak bir kaynak ekamazsiniz.

Bu örnek, belirli bir siteki site varlıkları kitaplığının özel kaynağını ekler:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Bu örnek, site koleksiyonunun site _varlıkları kitaplığında klasör1_ klasörünün özel kaynağını ekler:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

Yolda boşluk varsa, yolu çift tırnak içine veya %20 URL kodlaması ile değiştirebilirsiniz. Aşağıdaki örnekler, site koleksiyonunun site varlıkları _kitaplığında yer alan klasör 1_ klasörünün özel kaynağını ekler:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

Bu komut ve söz dizimi hakkında daha fazla bilgi için bkz. [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

> [!NOTE]
> Özel kaynaklarda, bir kaynaktan paylaşılan varlıklara kaynak olarak erişilmeden önce yayımlanan ana sürümlerden biri CDN.

Siz komutu çalıştırarak, sistem yapılandırmayı veri merkezi genelinde eşitler. Bu, 15 dakika kadar sürebilir.

<a name="ExamplePublicOriginPnPPosh"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Örnek: Ana sayfalarınız için ve SharePoint Online için stil kitaplığınız için genel SharePoint yapılandırma

Normalde, varsayılan ayarı etkinleştirerek bu kökenler sizin için Office 365 CDN. Bununla birlikte, bunları el ile etkinleştirmek için aşağıdaki adımları izleyin.

+ Stil **kitaplığını genel kaynak olarak tanımlamak için Add-PnPTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ Ana sayfaları **genel kaynak olarak tanımlamak için Add-PnPTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Bu komut ve söz dizimi hakkında daha fazla bilgi için bkz. [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

Siz komutu çalıştırarak, sistem yapılandırmayı veri merkezi genelinde eşitler. Bu, 15 dakika kadar sürebilir.

<a name="ExamplePrivateOriginPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Örnek: SharePoint Online için site varlıklarınız, site sayfalarınız ve yayımlama resimleriniz için özel SharePoint yapılandırma

+ Site varlıkları **klasörünü özel kaynak olarak tanımlamak için Add-PnPTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ Site sayfaları **klasörünü özel bir kaynak olarak tanımlamak için Add-PnPTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ Yayımlama resimleri **klasörünü özel bir kaynak olarak tanımlamak için Add-PnPTenantCdnOrigin** cmdlet'ini kullanın.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Bu komut ve söz dizimi hakkında daha fazla bilgi için bkz. [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

Siz komutu çalıştırarak, sistem yapılandırmayı veri merkezi genelinde eşitler. Bu, 15 dakika kadar sürebilir.

<a name="ExamplePrivateOriginSiteCollectionPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Örnek: SharePoint Online için site koleksiyonu için özel SharePoint yapılandırma

Site koleksiyonunu **özel kaynak olarak tanımlamak için Add-PnPTenantCdnOrigin** cmdlet'ini kullanın. Örneğin:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Bu komut ve söz dizimi hakkında daha fazla bilgi için bkz. [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

Siz komutu çalıştırarak, sistem yapılandırmayı veri merkezi genelinde eşitler. SharePoint Online _kiracısı_ CDN hizmetine bağlandığından, Yapılandırma beklemede iletisiyle CDN alabilirsiniz. Bu, 15 dakika kadar sürebilir.

<a name="CDNManagePnPPosh"> </a>
### <a name="manage-the-office-365-cdn"></a>Posta Office 365 CDN

Yapılandırmayı bir kez CDN, içeriği güncelleştirken veya ihtiyaçlar değiştiksinde, bu bölümde açıklandığı gibi yapılandırmanız üzerinde değişiklikler yapabilirsiniz.

<a name="Office365CDNforSPOaddremoveassetPnPPosh"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Varlıklar ekleme, güncelleştirme veya kaldırma Office 365 CDN

Kurulum adımlarını tamamlandıktan sonra, istediğiniz zaman yeni varlıklar ekleyebilir, var olan varlıkları güncelleştirebilirsiniz veya kaldırabilirsiniz. Kaynak olarak tanım istediğiniz klasör veya kitaplıkta SharePoint değişikliklerinizi yapın. Yeni bir varlık eklersiniz, bu varlık e-CDN kullanılabilir. Ancak, varlığı güncellersanız, yeni kopyanın yayılması ve bu kopyanın kullanılabilir olması 15 dakika CDN.

Kaynağın konumunu geri almak için **, Get-PnPTenantCdnOrigin** cmdlet'ini kullanabilirsiniz. Bu cmdlet'in nasıl kullanımı hakkında bilgi için bkz. [Get-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/get-pnptenantcdnorigin).

<a name="Office365CDNforSPORemoveOriginPnPPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Kaynak kaynak Office 365 CDN

Kaynak olarak tanım istediğiniz klasöre veya SharePoint erişimini kaldırabilirsiniz. Bunu yapmak için **Remove-PnPTenantCdnOrigin** cmdlet'ini kullanın.

```powershell
Remove-PnPTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Bu cmdlet'in nasıl kullanımı hakkında bilgi için bkz. [Remove-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/remove-pnptenantcdnorigin).

<a name="Office365CDNforSPOModifyOriginPnPPosh"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Kaynakta bir kaynağı Office 365 CDN

Oluşturduğunuz bir kaynağı değiştiremezsiniz. Bunun yerine, kaynağı kaldırın ve yeni bir tane ekleyin. Daha fazla bilgi için bkz[. Kaynak kaynak Office 365 CDN](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPnPPosh) [Kaynak eklemek için ve Varlıklarınızı kaynak eklemek için](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPnPPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Seçeneği devre dışı Office 365 CDN

**Set-PnPTenantCdnEnabled cmdlet'ini** kullanarak, CDN için bu cmdlet'i kullanın. Kaynak etkinleştirilmiş hem genel hem de özel CDN varsa, aşağıdaki örneklerde gösterildiği gibi cmdlet'i iki kez çalıştırmalısiniz.

Kaynakta genel kaynak kullanımını devre dışı CDN için, aşağıdaki komutu girin:

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $false
```

Kaynak 2013'te özel kaynak kullanımını CDN için aşağıdaki komutu girin:

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $false
```

Bu cmdlet hakkında daha fazla bilgi için bkz. [Set-PnPTenantCdnEnabled](/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled).

</details>

<a name="CDNSetupinCLI"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a>kullanarak Office 365 CDN ayarlama ve Office 365

Bu bölümdeki yordamlar için [CLI'ya Office 365 gerekir](https://aka.ms/o365cli). Ardından oturum aç komutunu Office 365 [kiracınıza](https://pnp.github.io/office365-cli/cmd/login/) bağlanabilirsiniz.

CLI kullanarak varlıklarınızı CDN Online'da barındırmak üzere SharePoint ayarlamak ve yapılandırmak için Office 365 tamamlayın.

<details>
  <summary>Genişletmek için tıklayın</summary>

### <a name="enable-the-office-365-cdn"></a>Ayarı Office 365 CDN

Spo cdn kümesi komutunu Office 365 CDN kiracınız içinde yer alan [cdn'nin durumunu yönetebilirsiniz](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/).

Kiracı yürütülecek Office 365 Genel CDN etkinleştirmek için:

```cli
spo cdn set --type Public --enabled true
```

Bu özelliği etkinleştirmek Office 365 SharePoint CDN yürütün:

```cli
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a>Tsppnin geçerli durumunu Office 365 CDN

Belirli bir dosya türünün etkin veya Office 365 CDN olduğunu kontrol etmek için [spo cdn get komutunu](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) kullanın.

Ortak Office 365 etkinleştirildiğinden CDN için yürütün:

```cli
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a>Kaynak Office 365 CDN görüntüleme

Şu anda yapılandırılmış olan genel Office 365 kaynak CDN görüntülemek için:

```cli
spo cdn origin list --type Public
```

Varsayılan [CDN, varsayılan](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) olarak sağlanan kaynaklarla ilgili bilgi için varsayılan kaynak Office 365 CDN.

### <a name="add-an-office-365-cdn-origin"></a>Kaynak Office 365 CDN ekleme

> [!IMPORTANT]
> Genel kaynak olarak yapılandırılan bir belge kitaplığında, SharePoint olarak kabul edilen kaynakları hiçbir zaman bir yere eklemeyebilirsiniz.

Bir [kaynak tanımlamak için spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) komutunu CDN kullanın. Birden çok kaynak tanımlayabilirsiniz. Kaynak, ana bilgisayar tarafından barındır SharePoint istediğiniz varlıkları içeren bir kitaplık veya klasöre CDN.

```cli
spo cdn origin add --type [Public | Private] --origin <path>
```

Burada `path` , varlıkları içeren klasörün göreli yolu vardır. Göreli yollara ek olarak joker karakterler de kullanabilirsiniz.

Tüm sitelerin Ana Sayfa **Galerisi'nde yer alan tüm** varlıkları genel kaynak olarak dahil etmek için, yürütme:

```cli
spo cdn origin add --type Public --origin */masterpage
```

Belirli bir site koleksiyonu için özel kaynak yapılandırmak için yürütme:

```cli
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> Kaynak CDN ekledikten sonra, dosyaları kaynak hizmeti aracılığıyla geri alayabilirsiniz ve bu 15 CDN sürebilir. Spo CDn kaynak listesi komutunu kullanarak belirli kaynağın zaten [etkinleştirildiğinden emin](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) olun.

### <a name="remove-an-office-365-cdn-origin"></a>Kaynak Office 365 CDN kaldırma

Belirtilen [kaynak türüne bir kaynak CDN için spo cdn](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) kaynağını kaldır komutunu CDN kullanın.

Kaynak yapılandırmadan genel CDN kaldırmak için yürütme:

```cli
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> Kaynak CDN kaldırılması, o kaynakla eşleşen herhangi bir belge kitaplığında depolanan dosyaları etkilemez. Bu varlıklara en son URL'leri kullanılarak SharePoint, SharePoint otomatik olarak belge kitaplığına işaret eder ve özgün URL'ye döner. Öte yandan, varlıklara genel kullanıcı URL'si kullanılarak başvuruldu CDN, kaynağın kaldırılması bağlantıyı bozacak ve bunları el ile değiştirmelisiniz.

### <a name="modify-an-office-365-cdn-origin"></a>Kaynak Office 365 CDN değiştirme

Varolan bir kaynakta değişiklik CDN. Bunun yerine, komutu kullanarak önceden CDN tanımlı kaynağı `spo cdn origin remove` kaldırmanız ve komutu kullanarak yeni bir tane eklemeniz `spo cdn origin add` gerekir.

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a>Dosya türlerini klasöre dahil etmek Office 365 CDN

Varsayılan olarak aşağıdaki dosya türleri CDN'a dahildir: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, .woff ve .woff2_. Dosyaya başka dosya türleri de eklemek CDN, [spo CDN ilke kümesi komutunu CDN dosya yapılandırmasını değiştirebilirsiniz](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/).

> [!NOTE]
> Dosya türleri listesini değiştirirken, şu anda tanımlanmış olan listenin üzerine yazmanız gerekir. Başka dosya türleri de eklemek için, ilk olarak [spo CDN](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) ilke listesi komutunu kullanarak hangi dosya türlerinin yapılandırılmış olduğunu bulun.

_Genel dosya türlerine dahil_ edilen varsayılan dosya türleri listesine JSON dosya türünü eklemek için CDN yürütün:

```cli
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>Site sınıflandırmalarının dışında tutmak istediğiniz sınıflandırmaların listesini Office 365 CDN

Varsayılan ayar [üzerinde kullanılabilir yapmak istediğiniz](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) site sınıflandırmalarını dışarıda tutmak için spo cdn ilke kümesi komutunu CDN. Varsayılan olarak, site sınıflandırmaları dahil değildir.

> [!NOTE]
> Dışarıda bırakılan site sınıflandırmaları listesini değiştirirken, şu anda tanımlanmış olan listenin üzerine yazmaz. Ek sınıflandırmaları dahil etmek istemiyorsanız, şu anda hangi sınıflandırmaların yapılandırılmış olduğunu bulmak için ilk olarak [spo CDN](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) ilke listesi komutunu kullanın.

Genel kuruluştan _HBI olarak sınıflandırılmış_ siteleri CDN, yürütme

```cli
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a>Seçeneği devre dışı Office 365 CDN

Bu komutu Office 365 CDN için `spo cdn set` komutu kullanın; örneğin:

```cli
spo cdn set --type Public --enabled false
```

</details>

## <a name="using-your-cdn-assets"></a>CDN varlıklarınızı kullanma

Kaynak ve ilkeleri etkinleştirdikten CDN kaynak ve ilkeleri etkinleştirdikten sonra, kaynak varlıklarınızı ve CDN başlayabilirsiniz.

Bu bölüm, SharePoint sayfaları ve içeriğinde CDN URL'lerini nasıl kullanabileceğinizi anlamanıza yardımcı olur ve böylece SharePoint hem genel hem özel kaynaklarda yer alan varlıklarla ilgili istekleri CDN.

+ [CDN varlıklarının bağlantılarını güncelleştirme](use-microsoft-365-cdn-with-spo.md#updating-links-to-cdn-assets)
+ [Ortak kaynaklarda varlıkları kullanma](use-microsoft-365-cdn-with-spo.md#using-assets-in-public-origins)
+ [Özel kaynaklarda varlıkları kullanma](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins)

CDN'de istemci tarafı web bölümlerini barındırmak için nasıl kullanabileceğiniz hakkında bilgi için, [Office 365 CDN(Hello World part 4)](/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)) başlığına bakın.

> [!NOTE]
> _ClientSideAssets_ klasörünü özel kaynak **listesine CDN,** CDN barındırılan özel web bölümleri iş devretmez. SPFX web bölümleri tarafından kullanılan dosyalar yalnızca genel kaynak CDN ve genel kaynak olarak ClientSideAssets klasörü CDN.

### <a name="updating-links-to-cdn-assets"></a>CDN varlıklarının bağlantılarını güncelleştirme

Kaynak olarak ekleytniz varlıkları kullanmak için, özgün dosyanın bağlantılarını kaynak dosyanın yoluyla güncelleştirmeniz basit olur.

+ Bir kaynakta yer alan varlıklara bağlantılar içeren sayfayı veya içeriği düzenleyin. Görüntülenen her yerde belirli bir varlığın bağlantısını güncelleştirmek istediğiniz bir site veya site koleksiyonu genelinde bağlantıları genel olarak aramak ve değiştirmek için de çeşitli yöntemlerden birini kullanabilirsiniz.
+ Bir kaynakta yer alan bir varlıkla ilgili her bağlantı için bu yolu kaynak dosyanın CDN değiştirin. Göreli yollar kullanabilirsiniz.
+ Sayfayı veya içeriği kaydedin.

Örneğin, belge kitaplığı klasörüne _/site/CDN_origins/public/ kopyalanmış olan /site/SiteAssets/images/image.png_/ görüntüsünü düşünün. Kaynak CDN kullanmak için, yeni _URL'yi /site/CDN_origins/public/image.png_ yapmak için özgün yolu resim dosyası konumuyla başlangıç yoluyla değiştirin.

Varlığın göreli yol yerine tam URL'sini kullanmak için, bağlantıyı şöyle oluşturun:

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> Genel olarak, URL'leri doğrudan bağlı varlıklara zor CDN. Bununla birlikte, gerekirse genel kaynaklarda yer alan varlıklar için URL'leri el ile kurabilirsiniz. Daha fazla bilgi için bkz[. Ortak varlıklar için CDN url'leri sabit şekilde koruma](use-microsoft-365-cdn-with-spo.md#constructing-cdn-urls-for-public-assets).

CDN hizmetlerinden varlıklara hizmet verili olduğunu doğrulama hakkında bilgi edinmek için Aşağıdaki sorun giderme konusunda CDN[](use-microsoft-365-cdn-with-spo.md#CDNConfirm). Varlıklara hizmet [Office 365 CDN.](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting)

### <a name="using-assets-in-public-origins"></a>Ortak kaynaklarda varlıkları kullanma

SharePoint  Online'daki Yayımlama özelliği, genel kaynaklarda depolanan varlıkların URL'lerini CDN eşdeğerlerine otomatik olarak yeniden yazarak, varlıklara posta yerine CDN hizmetine SharePoint.

Kaynağınız Yayımlama özelliğinin etkin olduğu bir sitedeyseniz ve CDN'e devredmek istediğiniz varlıklar aşağıdaki kategorilerden birini içerirse, SharePoint, varlığın bir CDN ilkesi tarafından dışlamamış olması şartıyla, kaynakta bulunan varlıklara ait URL'leri otomatik olarak yeniden yazmaz.

Aşağıda, Yayımlama özelliği tarafından hangi bağlantıların otomatik olarak yeniden SharePoint genel bir bakış yer almaktadır:

+ Klasik yayımlama sayfası HTML yanıtlarında IMG/LINK/CSS URL'leri
  + Bunlar, yazarların sayfanın HTML içeriğinde ekli resimleri içerir
+ Resim Kitaplığı Slayt Gösterisi web bölümü resmi URL'leri
+ SPList REST API'de resim alanları (RenderListDataAsStream) sonuçları
  + Virgülle ayrılmış alan _listesi sağlamak için ImageFieldsToTryRewriteToCdnUrls_ özelliğini kullanın
  + Köprü alanlarını ve PublishingImage alanlarını destekler
+ SharePoint görüntüditionları

Aşağıdaki diyagramda, kullanıcı genel SharePoint varlıklarını içeren bir sayfa isteği aldığında iş akışını gösterir.

![İş akışı diyagramı: Office 365 CDN kaynak olan varlıklar geri alınıyor.](../media/O365-CDN/o365-cdn-public-steps-transparent.png "İş Akışı: Office 365 CDN kaynaktan Office 365 CDN varlıklarını alma")

> [!TIP]
> Bir sayfada belirli URL'ler için otomatik yeniden yazma özelliğini devre dışı bırakmak için sayfayı kontrol edin ve sorgu dizesi parametresini ekleyin **? Devre dışı bırakmak istediğiniz her bağlantının sonuna NoAutoReWrites=true** tıklayın.

#### <a name="constructing-cdn-urls-for-public-assets"></a>Ortak CDN URL'lerini oluşturma

Yayımlama özelliği  genel kaynak için etkinleştirilmediyse veya varlık CDN hizmetinin otomatik yeniden yazma özelliği tarafından desteklenen bağlantı türlerinden biri yoksa, varlıkların CDN konumu için URL'leri el ile oluşturmak ve bu URL'leri içeriğiniz içinde kullanmak için kullanabilirsiniz.

> [!NOTE]
> Url'nin son bölümünü oluşturan CDN bir erişim belirteci, kaynak istenen zamanda oluşturulacak şekilde gerekli erişim belirteci olduğundan, özel kaynak olan varlıklara yönelik URL'leri zor kod olarak oluşturamaz veya oluşturamazsiniz. Genel Posta için URL'yi CDN ve değişiklike tabi olduğu için URL'nin sabit kodlu olması gerekir.

Ortak CDN varlıkları için, URL biçimi aşağıdakine benzer olur:

```http
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

**TenantHostName'i** kiracı adınızla değiştirin. Örneğin:

```http
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

> [!NOTE]
> Sayfa bağlam özelliği, "" zor kodlama yerine ön eki oluşturmak içinhttps://publiccdn.sharepointonline.com kullanılmalıdır. URL değişebilir ve sabit kodlu olmalı. Klasik SharePoint Online ile görüntüleme şablonları kullanıyorsanız, görüntü şablonlarında URL'nin ön eki için "window._spPageContextInfo.publicCdnBaseUrl" özelliğini kullanabilirsiniz. Modern ve klasik SPFx web bölümleriniz varsa SharePoint "this.context.pageContext.legacyPageContext.publicCdnBaseUrl" özelliğinden faydalanabilirsiniz. Bu, ön eki sağlar; bu şekilde değiştirilirse, uygulamanız bu ön ekle güncelleştirmeyi sağlar. SPFx örneğinde olduğu gibi, URL "bu.context.pageContext.legacyPageContext.publicCdnBaseUrl" + "/" + "host" + "/" + "öğe için göreliURL" özelliği kullanılarak oluşturulur. Lütfen 1[. CDN performans serisinin](https://youtu.be/IH1RbQlbhIA) parçası olan İstemci tarafı kodunda [CDN'i kullanma'ya bakın](https://aka.ms/sppnp-perfvideos).


### <a name="using-assets-in-private-origins"></a>Özel kaynaklarda varlıkları kullanma

Özel kaynaklarda varlıkları kullanmak için ek yapılandırma gerekmez. SharePoint Online özel kaynaklarda bulunan varlıklarla ilgili URL'leri otomatik olarak yeniden yazarak bu varlıklara yapılan isteklere her zaman servis CDN. Özel kaynaklarda yer alan CDN için URL'leri el ile oluşturamazsınız, çünkü bu URL'ler, varlık istenen zamanda SharePoint Online tarafından otomatik olarak oluşturulacak belirteçler içerir.

Özel kaynaklarda varlıklara erişim, aşağıdaki bölümlerde açıklanan uyarılarla birlikte, kaynak kullanıcı izinlerine dayalı olarak dinamik olarak oluşturulan belirteçlerle korunur. Kullanıcıların, içeriğin işlemesi **için** kaynak bilgilere en az CDN erişimi olması gerekir.

Aşağıdaki diyagramda, İş Akışı'SharePoint özel kaynak varlıkları içeren bir sayfa için istek geldiğinde ortaya çıktı.

![İş akışı diyagramı: Özel Office 365 CDN kaynak olan varlıklar geri alınıyor.](../media/O365-CDN/o365-cdn-private-steps-transparent.png "İş Akışı: Office 365 CDN kaynak olan varlıklar geri alınıyor")

#### <a name="token-based-authorization-in-private-origins"></a>Özel kaynaklarda belirteç tabanlı yetkilendirme

kaynaklarda özel kaynaklarda yer alan varlıklara Office 365 CDN, SharePoint Online tarafından oluşturulan belirteçler tarafından verilmesini sağlar. Kaynak tarafından belirlenen klasör veya kitaplara erişim iznine zaten sahip olan kullanıcılara, kullanıcının izin düzeyine göre dosyaya erişme izni veren belirteçler otomatik olarak atanır. Bu erişim belirteçleri, belirteç yeniden yürütme saldırılarını önlemeye yardımcı olmak için, oluşturulan 30 - 90 dakika için geçerlidir.

Erişim belirteci oluşturulduktan sonra, SharePoint Online iki yetkilendirme parametresi (kenar yetkilendirme belirteci) ve _oat_ _(kaynak_ yetkilendirme belirteci) içeren istemciye özel bir URI döndürür. Her belirtecin yapısı _,< süresi Epoch saat biçimindedir ve >__< imzanın güvenli bir şekilde >_. Örneğin:

```http
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> Belirteç sahibi olan herkes kaynakta olan herkes kaynakta CDN. Bununla birlikte, bu erişim belirteçlerini içeren URL'ler yalnızca HTTPS üzerinden paylaşılır, dolayısıyla belirteç süresi sona ermeden önce URL son kullanıcı tarafından açıkça paylaşılmadıkça, varlık yetkisiz kullanıcılar için erişilebilir olmayacaktır.

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a>Özel kaynaklarda öğe düzeyinde izinler desteklenmiyor

SharePoint Online'ın özel varlıklar için öğe düzeyinde izinleri destekleme olmadığını unutmayın. Örneğin, 'da bulunan bir dosya `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`için, kullanıcılar aşağıdaki koşullar altında verilen dosyaya etkili bir şekilde erişim sağlar:

|Kullanıcı  |İzinler  |Etkin erişim  |
|---------|---------|---------|
|Kullanıcı 1     |Klasör1'e erişimi var         |E-image1.jpg bağlantılara doğrudan CDN         |
|Kullanıcı 2     |Klasöre erişimi yok1         |Dosyadan image1.jpg erişe CDN         |
|Kullanıcı 3     |Klasör1'e erişimi yok, ancak image1.jpg Online'da image1.jpg için açık izin SharePoint.         |Varlık bilgilerine doğrudan image1.jpg SharePoint Online'dan erişebilirsiniz, ancak doğrudan CDN         |
|Kullanıcı 4     |Klasör1'e erişimi vardır, ancak SharePoint Online'da image1.jpg açıkça SharePoint reddedildi         |SharePoint Online'dan varlıkla bağlantınız bulunamaz, ancak CDN Online'da dosyaya erişimi reddedilmiş olmasına rağmen varlıktan SharePoint.         |

<a name="CDNTroubleshooting"></a>

## <a name="troubleshooting-the-office-365-cdn"></a>Sorun giderme Office 365 CDN

<a name="CDNConfirm"></a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a>Varlıklara hizmet olarak diğer varlıklara hizmet CDN?

CDN varlıklarının bağlantılarını bir sayfaya ekledikten sonra, sayfaya göz atarak ve görüntü URL'sini gözden geçirerek, görüntüye sağ tıklayarak CDN'den hizmet sağ tıklatarak varlığınız size hizmet edilir.

Ayrıca tarayıcınızın geliştirici araçlarını kullanarak bir sayfa üzerinde her varlığın URL'sini  görüntüleyebilirsiniz veya bir üçüncü taraf ağ izleme aracı kullanabilirsiniz.

> [!NOTE]
> Varlıklarınızı bir SharePoint sayfasından işleme dışında test etmek için Fiddler gibi bir ağ aracı kullanırsanız, URL'nin SharePoint Online kiracının kök URL'si olduğu GET isteğine başvuru sahibi üst bilgisini "Başvuran: `https://yourdomain.sharepoint.com`" el ile eklemeniz gerekir.

Web tarayıcısında CDN URL'leri test SharePoint çünkü. Bununla birlikte, CDN varlık URL'sini SharePoint sayfayı tarayıcıda açarsanız, sayfada işlenen CDN varlık olduğunu görebilirsiniz.

Geliştirici araçlarını tarayıcıda kullanma hakkında daha fazla bilgi Microsoft Edge Geliştirici [Araçları'Microsoft Edge bkz](/microsoft-edge/devtools-guide).

[CDN'nizin çalıştığını doğrulamayı gösteren SharePoint](https://aka.ms/sppnp-videos) Geliştirici Desenleri ve Uygulamaları kanalında barındırılan kısa bir video izlemek için lütfen CDN kullanımınızı doğrulama ve en iyi ağ bağlantısını sağlama CDN [bakın.](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5)

### <a name="why-are-assets-from-a-new-origin-unavailable"></a>Yeni bir kaynakta yer alan varlıklar neden kullanılamıyor?
Kayıt işleminin CDN aracılığıyla yayılması ve kaynaktan varlıkların depolama alanına yüklenmeleri için kayıt, yeni kaynaklarda bulunan varlıklar hemen CDN. Varlıklar için gereken süre, CDN ve dosyaların boyutlarına bağlıdır.

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a>İstemci tarafı web bölümüm veya SharePoint Framework çözümüm çalışmıyor

Kaynak ayarlarını etkinleştir Office 365 CDN kaynak olarak, CDN aşağıdaki varsayılan kökenleri otomatik olarak oluşturur:

+ */MASTERPAGE
+ */STYLE LIBRARY
+ */CLIENTSIDEASSETS

*/clientsideassets kaynağı yoksa, SharePoint Framework çözümleri başarısız olur ve uyarı veya hata iletisi oluşturulmaz. kaynak, -_NoDefaultOrigins_ parametresi CDN olarak ayarlanmış olduğundan veya kaynak el ile silindiğinde $true eksik olabilir.

Aşağıdaki PowerShell komutuyla hangi kökenlerin mevcut olduğunu kontrol edin:

```powershell
Get-SPOTenantCdnOrigins -CdnType Public
```

Ya da CLI'ya Office 365 kontrol edin:

```cli
spo cdn origin list
```

PowerShell'de kaynağı eklemek için:

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

KÖKENİ CLI'ya Office 365 için:

```cli
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a>Yeni modüllerle çalışmam gereken PowerShell modülleri ve CLI kabukları Office 365 CDN?

SharePoint Online Management Shell PowerShell modülünü veya **CLI'Office 365 CDN** kullanarak ana **bilgisayarla Office 365 seçebilirsiniz**.

+ [SharePoint Online Yönetim Kabuğu ile çalışmaya başlama](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
+ [Office 365 CLI'yi yükleme](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a>Ayrıca bkz.

[İçerik Teslim Ağları](./content-delivery-networks.md)

[Network planning and performance tuning for Office 365](./network-planning-and-performance.md)

[SharePoint Serisi - Office 365 CDN video serisi](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
