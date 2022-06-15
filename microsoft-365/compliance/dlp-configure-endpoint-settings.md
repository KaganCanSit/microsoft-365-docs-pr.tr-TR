---
title: Uç nokta DLP ayarlarını yapılandırma
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
description: Uç nokta veri kaybı önleme (DLP) merkezi ayarlarını yapılandırmayı öğrenin.
ms.openlocfilehash: edf5d42421aa9fb0c54d0121655e3a31d4a729f6
ms.sourcegitcommit: 1c8f54f9e7a7665bc10b5ef4a3d8c36e3e48f44c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/14/2022
ms.locfileid: "66078776"
---
# <a name="configure-endpoint-data-loss-prevention-settings"></a>Uç noktada veri kaybı önleme ayarlarını yapılandırma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Uç nokta veri kaybı önleme (DLP) davranışının birçok yönü merkezi olarak yapılandırılmış ayarlar tarafından denetlenmektedir. Ayarlar cihazlar için tüm DLP ilkelerine uygulanır.

![Uç nokta DLP ayarları](../media/endpoint-dlp-1-using-dlp-settings.png)

Şunları denetlemek istiyorsanız bu ayarları yapılandırmanız gerekir:

- Bulut çıkış kısıtlamaları
- Uygulama başına kullanıcı etkinlikleri üzerinde çeşitli kısıtlayıcı eylem türleri.
- Windows ve macOS cihazlar için dosya yolu dışlamaları.
- Tarayıcı ve etki alanı kısıtlamaları.
- İlkeleri geçersiz kılmaya yönelik iş gerekçeleri ilke ipuçlarında nasıl görünür?
- Office, PDF ve CSV dosyalarındaki etkinlikler otomatik olarak denetleniyorsa.

## <a name="dlp-settings"></a>DLP ayarları

Başlamadan önce DLP ayarlarınızı ayarlamanız gerekir. 

### <a name="endpoint-dlp-windows-1011-and-macos-settings"></a>Uç nokta DLP Windows 10/11 ve macOS ayarları

|Ayar |Windows 10, 1809 ve üzeri, Windows 11  |Catalina 10.15 veya üzerini macOS |Notlar  |
|---------|---------|---------|---------|
|Dosya yolu dışlamaları     |Destekleniyor         |Destekleniyor         |macOS varsayılan olarak açık olan önerilen dışlama listesini içerir          |
|Kısıtlı uygulamalar     |Destekleniyor         |Destekleniyor         |         |
|Kısıtlı uygulama grupları |Destekleniyor |Desteklenmiyor
|İzin verilmeyen Bluetooth uygulamaları    |Destekleniyor         |Desteklenmiyor         |         |
|Hassas öğelere yönelik tarayıcı ve etki alanı kısıtlamaları      |Destekleniyor         |Destekleniyor         |         |
|Uç Nokta DLP için ek ayarlar     |Destekleniyor         |Destekleniyor         |macOS cihazlar için yalnızca varsayılan iş gerekçeleri desteklenir         |
|Cihazlar için her zaman dosya etkinliğini denetleme     |Destekleniyor         |Destekleniyor         |         |
|İzin verilmeyen uygulamalardan dosyayı otomatik olarak karantinaya al | Destekleniyor | Desteklenmiyor| |
|Gelişmiş sınıflandırma | Destekleniyor | Desteklenmiyor| |
|İlke ipuçlarında iş gerekçesi | Destekleniyor | Destekleniyor| |

### <a name="advanced-classification-scanning-and-protection"></a>Gelişmiş sınıflandırma tarama ve koruma

Gelişmiş sınıflandırma tarama ve koruma, daha gelişmiş Microsoft Purview bulut tabanlı veri sınıflandırma hizmetinin öğeleri taramasına, sınıflandırmasına ve sonuçları yerel makineye döndürmesine olanak tanır. Bu, [DLP ilkelerinizde tam veri eşleştirme](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md) sınıflandırması, [adlandırılmış varlıklar](named-entities-learn.md) ve [eğitilebilir sınıflandırıcılar gibi sınıflandırma tekniklerinden](classifier-learn-about.md) yararlanabileceğiniz anlamına gelir.

Gelişmiş sınıflandırma etkinleştirildiğinde, içerik yerel cihazdan tarama ve sınıflandırma için bulut hizmetlerine gönderilir. Bant genişliği kullanımıyla ilgili bir sorun varsa, 24 saatlik bir süre içinde ne kadarın kullanılabileceğini belirleyebilirsiniz. Sınır Uç Nokta DLP ayarlarında yapılandırılır ve cihaz başına uygulanır. Bant genişliği kullanım sınırını ayarlarsanız ve bu sınır aşılırsa, DLP kullanıcı içeriğini buluta göndermeyi durdurur. Bu noktada veri sınıflandırması cihazda yerel olarak devam eder ancak tam veri eşleşmesi, adlandırılmış varlıklar ve eğitilebilir sınıflandırıcılar kullanılarak sınıflandırma kullanılamaz. Toplu bant genişliği kullanımı sıralı 24 saat sınırının altına düştüğünde bulut hizmetleriyle iletişim devam eder.

Bant genişliği kullanımı önemli değilse sınırsız bant genişliği kullanımına izin vermek için **Sınır yok'a** tıklayın.

Bu Windows sürümleri gelişmiş sınıflandırma taramasını ve korumasını destekler:

- Windows 10 sürümleri 20H1/20H2/21H1 (KB 5006738)
- Windows 10 sürümleri 19H1/19H2 (KB 5007189)
- Windows 10 RS5 (KB 5006744)

> [!NOTE]
> Office (Word, Excel, PowerPoint) ve PDF dosya türleri için gelişmiş sınıflandırma desteği sağlanır.

> [!NOTE]
> DLP ilkesi değerlendirmesi, kullanıcı içeriği gönderilmese bile her zaman bulutta gerçekleşir.

### <a name="file-path-exclusions"></a>Dosya yolu dışlamaları

[Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com) >  **Veri kaybı önleme** > **Uç Noktası DLP ayarları** > **Dosya yolu dışlamalarını** açın.

Cihazlarınızda DLP izleme, DLP uyarısı ve DLP ilkesi zorlamasından belirli yolları dışlamak isteyebilirsiniz çünkü bunlar çok gürültülü veya ilgilendiğiniz dosyaları içermez. Bu konumlardaki dosyalar denetlenmeyecek ve bu konumlarda oluşturulan veya değiştirilen dosyalar DLP ilkesi uygulamasına tabi olmayacaktır. DLP ayarlarında yol dışlamalarını yapılandırabilirsiniz.

#### <a name="windows-10-devices"></a>cihazları Windows 10

Windows 10 cihazlar için dışlama yollarınızı oluşturmak için bu mantığı kullanabilirsiniz:

- ile `\`biten geçerli dosya yolu, yalnızca doğrudan klasörün altındaki dosyalar anlamına gelir. <br/>Örneğin: `C:\Temp\`

- ile `\*`biten geçerli dosya yolu, doğrudan klasörün altındaki dosyaların yanı sıra yalnızca alt klasörlerin altındaki dosyalar anlamına gelir. <br/>Örneğin: `C:\Temp\*`

- veya `\*`olmadan `\` biten geçerli dosya yolu, tüm dosyaların doğrudan klasörün altında ve tüm alt klasörlerin altında olduğu anlamına gelir. <br/>Örneğin: `C:\Temp`

- Her iki tarafından arasında `\` joker karakter bulunan bir yol. <br/>Örneğin: `C:\Users\*\Desktop\`

- Her iki tarafından ve ile arasında `\` joker karakter bulunan ve `(number)` tam alt klasör sayısını veren bir yol. <br/>Örneğin: `C:\Users\*(1)\Downloads\`

- SYSTEM ortam değişkenlerini içeren bir yol. <br/>Örneğin: `%SystemDrive%\Test\*`

- Yukarıdakilerin bir karışımı. <br/>Örneğin: `%SystemDrive%\Users\*\Documents\*(2)\Sub\`

#### <a name="macos-devices"></a>cihazları macOS

Windows 10 cihazlara benzer şekilde, macOS cihazlar için kendi dışlamalarınızı ekleyebilirsiniz.

- Dosya yolu tanımları büyük/küçük harfe duyarlı değildir, bu nedenle `User` ile `user`aynıdır.

- Joker değerler desteklenir. Bu nedenle yol tanımı, yolun ortasında veya sonunda bir `*` içerebilir. Örneğin: `/Users/*/Library/Application Support/Microsoft/Teams/*`

#####  <a name="recommended-file-path-exclusions-preview"></a>Önerilen dosya yolu dışlamaları (önizleme)

Performans nedenleriyle Endpoint DLP, macOS cihazlar için önerilen dosya yolu dışlamalarının listesini içerir. Bu dışlamalar varsayılan olarak açıktır. **Mac için önerilen dosya yolu dışlamalarını ekle iki durumlu** düğmesini açarak bunları devre dışı bırakabilirsiniz. Liste şunları içerir:

- /Applications/*
- /System/*
- /usr/*
- /Library/*
- /private/*
- /opt/*
- /Users/*/Library/Application Support/Microsoft/Teams/*

### <a name="restricted-apps-and-app-groups"></a>Kısıtlı uygulamalar ve uygulama grupları

#### <a name="restricted-apps"></a>Kısıtlı uygulamalar

**Kısıtlanmış uygulamalar** (eski **adıyla İzin verilmeyen uygulamalar**), oluşturduğunuz uygulamaların listesidir. Kullanıcı bir cihazda DLP korumalı bir dosyaya **_erişmek_** için listedeki bir uygulamayı kullandığında DLP'nin gerçekleştireceği eylemleri yapılandırabilirsiniz. Windows 10 ve macOS cihazlarda kullanılabilir.

Bir ilkede **Kısıtlı uygulamalar tarafından erişim** seçildiğinde ve kullanıcı korumalı bir dosyaya erişmek için kısıtlanmış uygulamalar listesinde yer alan bir uygulamayı kullandığında, etkinlik , `blocked`veya `blocked with override` nasıl yapılandırdığınıza bağlı olarak olur`audited`. Bu, aynı uygulama **Kısıtlı bir uygulama grubunun** üyesi olmadığı sürece, **Kısıtlı uygulama grubundaki** etkinlikler için yapılandırılan eylemler **Kısıtlı uygulamalar** listesi için erişim etkinliği için yapılandırılan eylemleri geçersiz kılar. Tüm etkinlikler denetlenip etkinlik gezgininde gözden geçirilebilir.

> [!IMPORTANT]
> Yürütülebilir dosyanın yolunu değil, yalnızca yürütülebilir adı (browser.exe gibi) eklemeyin.

> [!IMPORTANT]
> Kısıtlı uygulamalar listesinde yer alan uygulamalar için tanımlanan eylem (`audit`, `block with override`veya `block`) yalnızca kullanıcı korumalı bir öğeye ***erişmeye*** çalıştığında geçerlidir. 

#### <a name="file-activities-for-apps-in-restricted-app-groups"></a>Kısıtlı uygulama gruplarındaki uygulamalar için dosya etkinlikleri

Kısıtlı uygulama grupları, DLP ayarlarında oluşturduğunuz ve ardından ilkedeki bir kurala eklediğiniz uygulama koleksiyonlarıdır. İlkeye kısıtlı bir uygulama grubu eklediğinizde, bu tabloda tanımlanan eylemleri gerçekleştirebilirsiniz.

|Kısıtlı Uygulama grubu seçeneği  |Yapmanıza olanak sağlayan şey  |
|---------|---------|
|Dosya etkinliğini kısıtlama     |DLP'ye, kullanıcıların uygulama grubundaki uygulamaları kullanarak DLP korumalı öğelere erişmesine izin vermelerini ve kullanıcı **Panoya kopyalama**, **USB çıkarılabilir sürücüye kopyalama**, **Ağ sürücüsüne kopyalama** ve uygulamadan **yazdırma** girişimlerinde hiçbir işlem yapmamalarını bildirir.          |
|Tüm etkinliklere kısıtlama uygulama     |DLP'ye `Audit only`, `Block with override`veya `Block` kullanıcı bu uygulama grubunda yer alan bir uygulamayı kullanarak DLP korumalı bir öğeye erişmeye çalıştığında bildirir         |
|Belirli bir etkinliğe kısıtlama uygulama     |Bu ayar, bir kullanıcının uygulama grubunda yer alan bir uygulama kullanarak DLP korumalı bir öğeye erişmesine olanak tanır ve kullanıcı **Panoya Kopyalama**, **USB çıkarılabilir sürücüye kopyalama**, `Block`**Ağ sürücüsüne kopyala** ve **Yazdır'ı** denediğinde DLP'nin gerçekleştirmesi için varsayılan bir eylem (`Audit only`, , veya `Block with override`) seçmenize olanak tanır.          |

> [!IMPORTANT]
> Kısıtlı bir uygulama grubunda Ayarlar, aynı kuralda olduklarında kısıtlı uygulamalar listesinde ayarlanan kısıtlamaları geçersiz kılar. Bu nedenle, bir uygulama kısıtlı uygulamalar listesindeyse ve kısıtlı bir uygulama grubunun üyesiyse, kısıtlanmış uygulamalar grubunun ayarları uygulanır.

#### <a name="how-dlp-applies-restrictions-to-activities"></a>DLP etkinliklere kısıtlamaları nasıl uygular?

**Kısıtlı uygulama gruplarındaki uygulamalar için Dosya etkinlikleri**, **Tüm uygulamalar için Dosya etkinlikleri** ve **Kısıtlanmış uygulama etkinlikleri listesi arasındaki etkileşimler** aynı kural kapsamındadır.

##### <a name="restricted-app-groups-overrides"></a>Kısıtlanmış uygulama grupları geçersiz kılmaları

**Kısıtlı uygulama gruplarındaki uygulamalar için Dosya etkinlikleri'nde** tanımlanan yapılandırmalar **, Kısıtlanmış uygulama etkinlikleri** listesindeki yapılandırmaları ve aynı kuraldaki **tüm uygulamalar için Dosya etkinlikleri'ni** geçersiz kılar.

##### <a name="restricted-app-activities-and-file-activities-for-all-apps"></a>Tüm uygulamalar için kısıtlı uygulama etkinlikleri ve Dosya etkinlikleri

**Kısıtlı uygulama etkinlikleri** için tanımlanan eylem veya `Audit only``Block with override` aynı kuraldaysa **, tüm uygulamalar** için **Kısıtlı uygulama etkinlikleri ve Dosya etkinlikleri yapılandırmaları** aynı şekilde çalışır. Bunun nedeni **Kısıtlı uygulama etkinlikleri** için tanımlanan eylemlerin yalnızca bir kullanıcı listede yer alan bir uygulamayı kullanarak bir dosyaya eriştiğinde geçerli olmasıdır. Kullanıcı erişime sahip olduktan sonra **, tüm uygulamalar için Dosya etkinliklerindeki etkinlikler için** tanımlanan eylemler uygulanır. 

İşte bir örnek:

**Kısıtlı uygulamalar'a** Notepad.exe eklenirse ve **Tüm uygulamalar için Dosya etkinlikleri** **Belirli etkinliklere kısıtlama uygula** olarak yapılandırılırsa ve her ikisi de şu şekilde yapılandırılır:

|İlkedeki ayar  |Uygulama adı  |Kullanıcı etkinliği  |Yürütülecek DLP eylemi  |
|---------|---------|---------|---------|
|Kısıtlı uygulama etkinlikleri     |Not Defteri        |DLP korumalı bir öğeye erişme         |Yalnızca denetim         |
|Tüm uygulamalar için dosya etkinlikleri   |Tüm uygulamalar        | Panoya kopyala        |Yalnızca denetim         |
|Tüm uygulamalar için dosya etkinlikleri     |Tüm uygulamalar         |USB kaldırılabilir bir cihaza kopyalama | Engelle       |
|Tüm uygulamalar için dosya etkinlikleri     |Tüm uygulamalar         |Ağ paylaşımına kopyalama         |Yalnızca denetim         |
|Tüm uygulamalar için dosya etkinlikleri   |Tüm uygulamalar         |Yazdırma         |Engelle         |
|Tüm uygulamalar için dosya etkinlikleri     |Tüm uygulamalar         |İzin verilmeyen Bluetooth uygulamasını kullanarak kopyalama veya taşıma         |Engellenen         |
|Tüm uygulamalar için dosya etkinlikleri     |Tüm uygulamalar         |Uzak masaüstü hizmetleri         |Geçersiz kılma ile engelle         |

A kullanıcısı Not Defteri kullanarak DLP korumalı bir dosya açar. DLP, erişime izin verir ve etkinliği denetler. A kullanıcısı Not Defteri korumalı öğeden panoya kopyalamaya çalışır ve DLP etkinliği denetler. Ardından A kullanıcısı korumalı öğeyi Not Defteri yazdırmayı dener ve etkinlik engellenir.

> [!NOTE]
> **Kısıtlı uygulama etkinliklerinde** gerçekleştirilecek DLP eylemi olarak `block`ayarlandığında, tüm erişim engellenir ve kullanıcı dosya üzerinde herhangi bir etkinlik gerçekleştiremez.
   
##### <a name="file-activities-for-all-apps-only"></a>Yalnızca tüm uygulamalar için dosya etkinlikleri

Bir uygulama **kısıtlanmış uygulama gruplarındaki uygulamalar için Dosya etkinliklerinde** değilse veya **Kısıtlı uygulama etkinlikleri** listesinde değilse veya eylemiyle `Audit only`**Kısıtlanmış uygulama etkinlikleri** listesindeyse veya 'Geçersiz kılmayla engelle' durumundaysa, **tüm uygulamalar için Dosya etkinliklerinde** tanımlanan tüm kısıtlamalar aynı kuralda uygulanır.  

#### <a name="macos-devices"></a>cihazları macOS

Windows cihazlarda olduğu gibi, artık macOS uygulamaların hassas verilere erişmesini **Kısıtlanmış uygulama etkinlikleri** listesinde tanımlayarak engelleyebilirsiniz. 

> [!NOTE]
> Platformlar arası uygulamaların, üzerinde çalıştıkları işletim sistemine göre benzersiz yolları ile girilmesi gerektiğini unutmayın.

Mac uygulamalarının tam yolunu bulmak için:

1. macOS cihazda **Etkinlik İzleyicisi'ni** açın. Kısıtlamak istediğiniz işlemi bulma ve çift tıklama

2. **Dosyaları ve Bağlantı Noktalarını Aç** sekmesini seçin.
  
3. macOS uygulamalarda, uygulamanın adı da dahil olmak üzere tam yol adına ihtiyacınız vardır.

#### <a name="protect-sensitive-data-from-cloud-synchronization-apps"></a>Hassas verileri bulut eşitleme uygulamalarından koruma

onedrive.exe *gibi hassas* öğelerin bulut eşitleme uygulamaları tarafından bulutla eşitlenmesini önlemek için bulut eşitleme uygulamasını **İzin verilmeyen uygulamalar** listesine ekleyin. İzin verilmeyen bir bulut eşitleme uygulaması, engelleyici bir DLP ilkesi tarafından korunan bir öğeye erişmeye çalıştığında, DLP yinelenen bildirimler oluşturabilir. **İzin verilmeyen uygulamalar** altında **Otomatik karantinaya alma** seçeneğini etkinleştirerek bu yinelenen bildirimleri önleyebilirsiniz.  

##### <a name="auto-quarantine-preview"></a>Otomatik karantina (önizleme)

> [!NOTE]
> Otomatik karantina yalnızca Windows 10 desteklenir

Etkinleştirildiğinde, izin verilmeyen bir uygulama DLP korumalı hassas bir öğeye erişmeye çalıştığında otomatik karantina devreye giriyor. Otomatik karantina, hassas öğeyi yönetici tarafından yapılandırılmış bir klasöre taşır ve özgün klasörün yerine bir yer tutucu **.txt** dosyası bırakabilir. Yer tutucu dosyasındaki metni, kullanıcılara öğenin nereye taşındığını ve diğer ilgili bilgileri söyleyecek şekilde yapılandırabilirsiniz.  

Kullanıcı ve yöneticiler için sonsuz DLP bildirimleri zincirini önlemek için otomatik karantinayı kullanabilirsiniz. Bkz [. Senaryo 4: Otomatik karantina (önizleme) ile bulut eşitleme uygulamalarından DLP bildirimlerini döngüye almaktan kaçının](endpoint-dlp-using.md#scenario-4-avoid-looping-dlp-notifications-from-cloud-synchronization-apps-with-auto-quarantine-preview).

### <a name="unallowed-bluetooth-apps"></a>İzin verilmeyen Bluetooth uygulamaları

Kişilerin ilkeleriniz tarafından korunan dosyaları belirli Bluetooth uygulamaları aracılığıyla aktarmasını engelleyin.

### <a name="browser-and-domain-restrictions-to-sensitive-data"></a>Hassas verilere yönelik tarayıcı ve etki alanı kısıtlamaları

İlkelerinizle eşleşen hassas dosyaların sınırsız bulut hizmeti etki alanlarıyla paylaşılmasını kısıtlayın.

#### <a name="unallowed-browsers"></a>İzin verilmeyen tarayıcılar

Windows cihazlar için, bulut hizmetlerine yükleme kısıtlamasının geçersiz kılmayı engellemek veya engellemek için ayarlandığı zorunlu bir DLP ilkesinin koşullarıyla eşleşen dosyalara erişmesi engellenecek, yürütülebilir adlarıyla tanımlanan tarayıcılar eklersiniz. Bu tarayıcıların bir dosyaya erişimi engellendiğinde, son kullanıcılar dosyayı Microsoft Edge aracılığıyla açmalarını isteyen bir bildirim görür.

macOS cihazlar için tam dosya yolunu eklemeniz gerekir. Mac uygulamalarının tam yolunu bulmak için:

1. macOS cihazda **Etkinlik İzleyicisi'ni** açın. Kısıtlamak istediğiniz işlemi bulma ve çift tıklama

2. **Dosyaları ve Bağlantı Noktalarını Aç** sekmesini seçin.
  
3. macOS uygulamalarda, uygulamanın adı da dahil olmak üzere tam yol adına ihtiyacınız vardır.

#### <a name="service-domains"></a>Hizmet etki alanları

> [!NOTE]
> **Hizmet etki alanları** ayarı yalnızca Microsoft Purview [Uzantısı](dlp-chrome-learn-about.md#learn-about-the-microsoft-purview-extension) yüklü Microsoft Edge veya Google Chrome kullanılarak yüklenen dosyalar için geçerlidir.

İlkeleriniz tarafından korunan hassas dosyaların Microsoft Edge belirli hizmet etki alanlarına yüklenip yüklenemeyeceğini denetleyebilirsiniz.

Liste modu **Engelle** olarak ayarlanırsa, kullanıcı hassas öğeleri bu etki alanlarına yükleyemez. Bir öğe bir DLP ilkesiyle eşleştiği için karşıya yükleme eylemi engellendiğinde, DLP bir uyarı oluşturur veya hassas öğenin karşıya yüklenmesini engeller.

Liste modu **İzin Ver** olarak ayarlanırsa, kullanıcılar **_hassas öğeleri yalnızca_** bu etki alanlarına yükleyebilir ve diğer tüm etki alanlarına erişime izin verilmez.

> [!IMPORTANT]
> Hizmet kısıtlama modu "İzin Ver" olarak ayarlandığında, kısıtlamalar uygulanmadan önce en az bir hizmet etki alanı yapılandırmış olmanız gerekir.

Hizmet etki alanının FQDN biçimini bitiş olmadan kullanın `.` 

Örneğin:

 `www.contoso.com` 

Joker karakterler desteklenmez.

### <a name="additional-settings-for-endpoint-dlp"></a>Uç nokta DLP'leri için ek ayarlar

#### <a name="business-justification-in-policy-tips"></a>İlke ipuçlarında iş gerekçesi

DLP ilkesi ipucu bildirimlerinde kullanıcıların iş gerekçesi seçeneğiyle nasıl etkileşim kuracağını denetleyebilirsiniz. Bu seçenek, kullanıcılar bir DLP ilkesindeki **Geçersiz kılma ile engelle** ayarı tarafından korunan bir etkinlik gerçekleştirdiğinde görüntülenir. Bu genel bir ayardır. Aşağıdaki seçeneklerden birini seçebilirsiniz:

- **Varsayılan seçenekleri ve özel metin kutusunu göster**: Varsayılan olarak, kullanıcılar yerleşik bir gerekçe seçebilir veya kendi metinlerini girebilir.
- **Yalnızca varsayılan seçenekleri göster**: Kullanıcılar yalnızca yerleşik bir gerekçe seçebilir.
- **Yalnızca özel metin kutusunu göster**: Kullanıcılar yalnızca kendi gerekçelerini girebilir. Son kullanıcı ilkesi ipucu bildiriminde yalnızca metin kutusu görünür. 

##### <a name="customizing-the-options-in-the-drop-down-menu"></a>Açılan menüde seçenekleri özelleştirme

Kullanıcılar ilke bildirim ipucuyla etkileşime geçtiğinde seçenekleri **özelleştir açılan menüsünü** seçerek en fazla beş özelleştirilmiş seçenek oluşturabilirsiniz. 


|Seçeneği |Varsayılan metin  |
|---------|---------|
|seçenek 1    | **Bu, yerleşik bir iş iş akışının parçasıdır**  veya özelleştirilmiş metin girebilirsiniz        |
|seçenek 2  |**Yöneticim bu eylemi onayladı** veya özelleştirilmiş metin girebilirsiniz         |
|seçenek 3   |**Acil erişim gerekli; Yöneticimi ayrıca bilgilendireceğim** veya özelleştirilmiş metin girebilirsiniz          |
|Hatalı pozitif seçeneği göster     |**Bu dosyalardaki bilgiler hassas değil** veya özelleştirilmiş metin girebilirsiniz          |
|seçenek 5    |**Diğer** veya özelleştirilmiş metin girebilirsiniz         |

### <a name="always-audit-file-activity-for-devices"></a>Cihazlar için her zaman dosya etkinliğini denetleme

Varsayılan olarak, cihazlar eklendiğinde Office, PDF ve CSV dosyalarına yönelik etkinlik otomatik olarak denetlenip etkinlik gezgininde gözden geçirilebilir. Bu etkinliğin yalnızca eklenen cihazlar etkin bir ilkeye dahil edildiğinde denetlenmesini istiyorsanız bu özelliği kapatın.

Dosya etkinliği, etkin bir ilkeye dahil olup olmadıklarına bakılmaksızın eklenen cihazlar için her zaman denetlenecektir.

## <a name="see-also"></a>Ayrıca bkz.

- [Uç nokta veri kaybı önleme hakkında daha fazla bilgi edinme](endpoint-dlp-learn-about.md)
- [Uç noktada veri kaybı önlemeyi kullanmaya başlama](endpoint-dlp-getting-started.md)
- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md)
- [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md)
- [Etkinlik gezgini ile Kullanmaya başlayın](data-classification-activity-explorer.md)
- [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/)
- [Windows 10 ve Windows 11 cihazlarını Microsoft Purview genel bakışa ekleme](/microsoft-365/compliance/device-onboarding-overview)
- [aboneliği Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure Active Directory (AAD) katıldı](/azure/active-directory/devices/concept-azure-ad-join)
- [Chromium dayalı yeni Microsoft Edge indirme](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
- [Varsayılan DLP ilkesini kullanmaya başlama](get-started-with-the-default-dlp-policy.md)
- [Bir şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)
