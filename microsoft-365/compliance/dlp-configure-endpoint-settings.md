---
title: Uç nokta veri kaybı önleme ayarlarını yapılandırma
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
ms.openlocfilehash: ebe995512769275999e7ec4837e16542ffce7100
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63705692"
---
# <a name="configure-endpoint-data-loss-prevention-settings"></a>Uç nokta veri kaybı önleme ayarlarını yapılandırma

Uç nokta veri kaybını önleme (DLP) davranışının birçok yönü, merkezi olarak yapılandırılmış ayarlarla denetlenmektedir. Ayarlar için tüm DLP ilkelerine uygulanır.

![Uç nokta DLP ayarları](../media/endpoint-dlp-1-using-dlp-settings.png)

Aşağıdaki ayarları denetlemeyi biliyorsanız, bu ayarları yapılandırabilirsiniz:

- Bulut çıkış kısıtlamaları
- Uygulama başına kullanıcı etkinlikleri üzerinde çeşitli kısıtlayıcı eylemler.
- Windows macOS cihazları için dosya yolu dışlamaları.
- Tarayıcı ve etki alanı kısıtlamaları.
- İlke ipuçlarında, ilkeleri geçersiz kılmaya yönelik işletme gerekçeleri nasıl görünür.
- Pdf ve CSV dosyalarında Office otomatik olarak denetlenebilir.

## <a name="dlp-settings"></a>DLP ayarları

Başlamadan önce DLP ayarlarınızı ayarlamıştınız. 

### <a name="endpoint-dlp-windows-1011-and-macos-settings"></a>Uç nokta DLP Windows 10/11 ve macOS ayarları

|Ayar |Windows 10 1809 ve sonrası, Windows 11  |macOS Catalina 10.15 veya sonrası (önizleme)  |Notlar  |
|---------|---------|---------|---------|
|Dosya yolu dışlamaları     |Destekleniyor         |Destekleniyor         |macOS varsayılan olarak açık olan önerilen bir dışlama listesi içerir          |
|Kısıtlanmış uygulamalar     |Destekleniyor         |Destekleniyor         |         |
|Kısıtlanmış uygulama grupları |Destekleniyor |Desteklenmiyor
|Izin verilmeyen Bluetooth uygulamaları    |Destekleniyor         |Desteklenmiyor         |         |
|Hassas öğelere yönelik tarayıcı ve etki alanı kısıtlamaları      |Destekleniyor         |Destekleniyor         |         |
|Uç Nokta DLP için ek ayarlar     |Destekleniyor         |Destekleniyor         |MacOS cihazlarda yalnızca varsayılan iş gerekçeleri desteklenmemektedir         |
|Cihazlar için her zaman dosya etkinliğini denetleme     |Destekleniyor         |Destekleniyor         |         |
|Izin verilmeyen uygulamalardan dosyayı otomatik karantinaya alın | Destekleniyor | Desteklenmiyor| |
|Gelişmiş sınıflandırma | Destekleniyor | Desteklenmiyor| |
|İlke ipuçlarında işletme gerekçelendirmesi | Destekleniyor | Destekleniyor| |

### <a name="advanced-classification-scanning-and-protection"></a>Gelişmiş sınıflandırma tarama ve koruma

Gelişmiş sınıflandırma tarama ve koruma, daha gelişmiş Microsoft 365 bulut tabanlı veri sınıflandırma hizmetinin öğeleri taramasını, sınıflandırmasını ve sonuçları yerel makineye geri geri dönmesini sağlar. Bu da, DLP ilkeleriniz içinde tam veri [](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md) eşleşme sınıflandırması, adlandırılmış varlıklar [(önizleme)](named-entities-learn.md#learn-about-named-entities-preview) ve eğitilebilir [](classifier-learn-about.md#learn-about-trainable-classifiers) sınıflayıcılar gibi sınıflandırma tekniklerinden yararlan İlkeleri anlamına gelir.

Gelişmiş sınıflandırma özelliği açık olduğunda, içerik tarama ve sınıflandırma için yerel cihazdan bulut hizmetlerine gönderilir. Bant genişliği kullanımı önemli bir konu ise, kullanıla 24 saatlik bir dönemde ne kadar kullanıla olacağını sınırlayın. Sınır Uç Nokta DLP ayarlarında yapılandırılır ve cihaz başına uygulanır. Bir bant genişliği kullanım sınırı ayarsanız ve bu sınır aşılırsa, DLP kullanıcı içeriğini buluta göndermeyi durdurur. Bu noktada veri sınıflandırması cihazda yerel olarak devam eder, ancak tam veri eşleşmesi kullanılarak sınıflandırma özelliği, adlandırılmış varlıklar (önizleme) ve eğitilebilir sınıflayıcılar kullanılamaz. Toplam bant genişliği kullanımı yaklaşık 24 saat sınırının altına düştüğünde, bulut hizmetleriyle iletişim sürdürür.

Bant genişliği kullanımı önemli değilse, sınırsız bant genişliği kullanımına **izin vermek için** Sınır yok'ı seçin.

Bu Windows sürümleri gelişmiş sınıflandırma tarama ve korumayı destekler:

- Windows 10 20H1/20H2/21H1 (KB 5006738)
- Windows 10 19H1/19H2 (KB 5007189)
- Windows 10 RS5 (KB 5006744)

> [!NOTE]
> Gelişmiş sınıflandırma desteği, sınıf (Word Office, Excel, PowerPoint) ve PDF dosya türlerinde kullanılabilir.

> [!NOTE]
> DLP ilkesi değerlendirmesi, kullanıcı içeriği gönderilmese bile her zaman bulutta gerçekleşir.

### <a name="file-path-exclusions"></a>Dosya yolu dışlamaları

Uyumluluk [merkezini açmaVeri](https://compliance.microsoft.com) >  **kaybı önlemeEndpoint** >  **DLP ayarlarıDosya** >  **yolu dışlamaları**.

Cihazlarınız çok gürültülü olduğundan veya ilgilendiğiniz dosyaları içermelerinden dolayı bazı yolları DLP izleme, DLP uyarısı ve DLP ilkesi zorlamalarının dışında tutmak istiyorabilirsiniz. Bu konumlarda bulunan dosyalar denetlenmek zorunda değildir ve bu konumlarda oluşturulan veya değiştirilen hiçbir dosya DLP ilke zorlaması'ne tabi olmayacaktır. DLP ayarlarında yol dışlamalarını yapılandırabilirsiniz.

#### <a name="windows-10-devices"></a>Windows 10 cihazları

Bu mantığı kullanarak, diğer cihazlarınız için dışlama yollarınızı Windows 10 kullanabilirsiniz:

- ile sona eren geçerli dosya yolu `\`, yalnızca doğrudan klasör altındaki dosyalar anlamına gelir. <br/>Örneğin: `C:\Temp\`

- ile sona eren geçerli dosya `\*`yolu, doğrudan klasörün altındaki dosyaların yanı sıra yalnızca alt klasörler altındaki dosyalar anlamına gelir. <br/>Örneğin: `C:\Temp\*`

- veya olmadan sona eren geçerli dosya `\` yolu `\*`, tüm dosyaların doğrudan klasör ve tüm alt klasörler altında olduğu anlamına gelir. <br/>Örneğin: `C:\Temp`

- Her iki tarafı arasında joker karakterli `\` bir yol. <br/>Örneğin: `C:\Users\*\Desktop\`

- Her iki tarafından arasında joker `\` karakterli bir yol ve `(number)` tam sayıda alt klasör vermek için. <br/>Örneğin: `C:\Users\*(1)\Downloads\`

- SYSTEM ortam değişkenlerinin olduğu bir yol. <br/>Örneğin: `%SystemDrive%\Test\*`

- Yukarıdakilerin hepsi bir karışımı. <br/>Örneğin: `%SystemDrive%\Users\*\Documents\*(2)\Sub\`

#### <a name="macos-devices-preview"></a>macOS cihazlar (önizleme)

Diğer Windows 10 macOS cihazlar için kendi özel durumlarınızı  ekleyebilirsiniz.

- Dosya yolu tanımları büyük/harfe duyarlı değildir, `User` dolayısıyla ile aynıdır `user`.

- Joker değerler de desteklenen bir değerdir. Dolayısıyla, yol tanımı yolun `*` ortasında veya sonunda bir yol içerebilir. Örneğin: `/Users/*/Library/Application Support/Microsoft/Teams/*`

#####  <a name="recommended-file-path-exclusions-preview"></a>Önerilen dosya yolu dışlamaları (önizleme)

Performans nedenleriyle, Uç Nokta DLP'de macOS cihazları için önerilen dosya yolu dışlamalarının listesi vardır. Bu dışlamalar varsayılan olarak açıktır. Mac için önerilen dosya yolu dışlamalarını dahiled iki **durumlu düğmesini değiştirerek bu seçenekleri devre dışı** abilirsiniz. Bu liste şunları içerir:

- /Applications/*
- /System/*
- /usr/*
- /Library/*
- /private/*
- /opt/*
- /Users/*/Library/Application Support/Microsoft/Teams/*

### <a name="restricted-apps-and-app-groups"></a>Kısıtlanmış uygulamalar ve uygulama grupları

#### <a name="restricted-apps"></a>Kısıtlanmış uygulamalar

**Sınırlı uygulamalar** (önceki adı **Izin verilmeyen uygulamalar**) sizin oluşturmiş olduğunuz uygulamaların listesidir. Kullanıcının listede bir uygulamayı kullanarak cihazda DLP korumalı bir dosyaya erişmek için hangi DLP eylemlerini **** gerçekleştireceklerini yapılandırabilirsiniz. MacOS ve macOS Windows 10 (önizleme) için kullanılabilir.

Sınırlanmış uygulamalarla **Access** bir ilkede seçildiğinde ve kullanıcı korunan bir dosyaya erişmek için kısıtlanmış uygulamalar listesinde yer alan bir uygulamayı kullandığında, `audited`etkinlik , `blocked``blocked with override` veya bunu nasıl yapılandırdınıza bağlı olarak etkinliğiniz olur. Başka bir ifadeyle, aynı uygulama bir Kısıtlanmış uygulama grubunun üyesi **değilse, Kısıtlanmış** uygulama grubunda etkinlikler için yapılandırılan eylemler, Kısıtlanmış uygulamalar listesi için erişim etkinliği için yapılandırılan **eylemleri geçersiz** kılar. Tüm etkinlikler denetlenmektedir ve etkinlik gezgininde gözden geçirilebilir.

> [!IMPORTANT]
> Yürütülebilir dosyanın yolunu değil, yalnızca yürütülebilir adı (yürütülebilir dosya gibi) browser.exe.

> [!IMPORTANT]
> Kısıtlanmış uygulamalar listesinde yer `block`alan uygulamalar için tanımlanan eylem (`audit`, `block with override`veya ) yalnızca kullanıcı korunan bir öğeye ***erişmeye*** geldiğinde geçerlidir. 

#### <a name="file-activities-for-apps-in-restricted-app-groups-preview"></a>Kısıtlı uygulama gruplarında uygulamalar için dosya etkinlikleri (önizleme)

Kısıtlanmış uygulama grupları, DLP ayarlarından ve ardından bir ilkede kurala ekley koleksiyonlarıdır. İlkeye kısıtlanmış bir uygulama grubu eklerken, bu tabloda tanımlanan eylemleri gerçekleştirebilirsiniz.

|Kısıtlanmış Uygulama grup seçeneği  |Bu işlem size neyi sağlar?  |
|---------|---------|
|Dosya etkinliğini kısıtlama     |DLP'ye kullanıcıların uygulama grubunda uygulamaları kullanarak DLP korumalı öğelere erişmelerine izin vermelerini ve panoya **kopyalama,** **USB** çıkarılabilir sürücüye kopyala, Ağ sürücüsüne kopyala ve Uygulamada yazdır'ı denemeleri için herhangi bir işlem uygulamamalarını söyler.          |
|Tüm etkinliklere kısıtlama uygulama     |DLP'ye `Audit only`, `Block with override`veya bir `Block` kullanıcı bu uygulama grubunda yer alan bir uygulama kullanarak DLP korumalı bir öğeye erişmeyi denemesi ile ilgili bilgi sağlar         |
|Belirli bir etkinlik için kısıtlama uygulama     |Bu ayar kullanıcının uygulama grubunda yer alan bir uygulamayı kullanarak DLP korumalı bir öğeye erişmesine olanak sağlar ve kullanıcı Panoya kopyala, `Block``Block with override`**USB** çıkarılabilir sürücüye **kopyala, Ağ** sürücüsüne kopyala ve Yazdır eylemlerini gerçekleştir girişiminde bulunan DLP için varsayılan eylemi (`Audit only`, veya ) seçmenizi **sağlar.**          |

> [!IMPORTANT]
> Ayarlar bir uygulama grubunda yer alan kullanıcı, aynı kuralda yer alan kısıtlanmış uygulamalar listesinde ayarlanmış tüm kısıtlamaları geçersiz kılar. Dolayısıyla, bir uygulama kısıtlanmış uygulamalar listesinde yer alıyorsa ve bir kısıtlı uygulamalar grubuna üye ise, kısıtlanmış uygulamalar grubunun ayarları uygulanır.

#### <a name="how-dlp-applies-restrictions-to-activities"></a>DLP'nin etkinliklere kısıtlamalar nasıl uygulanır?

Kısıtlı uygulama **gruplarında (önizleme)** uygulamalar için Dosya **etkinlikleri, tüm** uygulamalar için dosya etkinlikleri ve Kısıtlanmış uygulama etkinlikleri listesi arasındaki etkileşimler aynı kural kapsamındadır.

##### <a name="restricted-app-groups-overrides"></a>Kısıtlanmış uygulama grupları geçersiz kılar

Kısıtlı uygulama **gruplarında uygulamalar** için dosya etkinlikleri (önizleme) içinde tanımlanan yapılandırmalar, aynı kuralda yer alan  Kısıtlanmış uygulama etkinlikleri listesinde ve Dosya  etkinlikleri'nin yapılandırmalarını geçersiz kılar.

##### <a name="restricted-app-activities-and-file-activities-for-all-apps"></a>Tüm uygulamalar için kısıtlanmış uygulama etkinlikleri ve Dosya etkinlikleri

Kısıtlı uygulama etkinlikleri **için**   `Audit only``Block with override` tanımlanan eylem ya da aynı kuralda ise, Tüm uygulamalar için Kısıtlanmış uygulama etkinlikleri ve Dosya etkinliklerinin yapılandırmaları uygun şekilde çalışır. Bunun nedeni, Kısıtlanmış uygulama **etkinlikleri için** tanımlanan eylemlerin yalnızca kullanıcı listede olan bir uygulamayı kullanarak bir dosyaya eriş başvurmasıdır. Kullanıcının erişimi olduktan sonra, Tüm uygulamalar için Dosya **etkinliklerinde etkinlikler için tanımlanan eylemler** uygulanır. 

İşte bir örnek:

Kısıtlı Notepad.exe ve Tüm uygulamalar için Dosya etkinlikleri'ne bir e-posta eklenirse, belirli etkinliklere kısıtlama uygulamak üzere  yapılandırılır ve her ikisi de aşağıdaki gibi yapılandırılır: 

|İlkede ayar  |Uygulama adı  |Kullanıcı etkinliği  |DLP eylemi  |
|---------|---------|---------|---------|
|Kısıtlanmış uygulama etkinlikleri     |Not Defteri        |DLP korumalı bir öğeye erişme         |Yalnızca denetleme         |
|Tüm uygulamalar için dosya etkinlikleri   |Tüm uygulamalar        | Panoya kopyala        |Yalnızca denetleme         |
|Tüm uygulamalar için dosya etkinlikleri     |Tüm uygulamalar         |USB ile kaldırılabilir bir cihaza kopyalama | Engelle       |
|Tüm uygulamalar için dosya etkinlikleri     |Tüm uygulamalar         |Ağ paylaşımına kopyalama         |Yalnızca denetleme         |
|Tüm uygulamalar için dosya etkinlikleri   |Tüm uygulamalar         |Yazdır         |Engelle         |
|Tüm uygulamalar için dosya etkinlikleri     |Tüm uygulamalar         |Aynı uygulamada izin verilmeyen dosyaları kullanarak kopyalama Bluetooth taşıma         |Engellendi         |
|Tüm uygulamalar için dosya etkinlikleri     |Tüm uygulamalar         |Uzak masaüstü hizmetleri         |Geçersiz kılmayla engelleme         |

Kullanıcı A, kimlik bilgilerini kullanarak DLP korumalı bir Not Defteri. DLP, etkinliğin erişimine ve denetimine izin verir. Kullanıcı A Not Defteri da korumalı öğeden panoya kopyalamayı deniyor, bu da çalışır ve DLP etkinliği denetimler. Kullanıcı A, korumalı öğeyi iş yerlerinden yazdırmayı Not Defteri ve etkinlik engellenir.

> [!NOTE]
> Kısıtlanmış uygulama  `block`etkinlikleri için gerçekleştirecek DLP eylemi olarak ayarlanmamışsa, tüm erişim engellenir ve kullanıcı dosya üzerinde hiçbir etkinlik gerçekleştiramaz.
   
##### <a name="file-activities-for-all-apps-only"></a>Yalnızca tüm uygulamalar için dosya etkinlikleri

Bir uygulama, kısıtlı uygulama gruplarında **(önizleme)** uygulamalar için Dosya etkinlikleri içinde yer alıyorsa veya Kısıtlanmış uygulama etkinlikleri listesinde  yer alıyorsa ya da 'Geçersiz kılma ile engelle' `Audit only`eylemiyle Kısıtlanmış uygulama etkinlikleri listesinde yer alıyorsa, Tüm uygulamalar için Dosya etkinliklerinde tanımlanan tüm kısıtlamalar aynı kuralda  uygulanır.  

#### <a name="macos-devices-preview"></a>macOS cihazlar (önizleme)

Diğer Windows gibi macOS uygulamalarının Hassas uygulama etkinlikleri listesinde tanımlayarak hassas verilere erişmesini **de önabileceksiniz**. 

> [!NOTE]
> Platformlar arası uygulamaların, çalıştır yaptıkları işletim sistemi ile ilgili benzersiz yolları ile girilleri gerektiğini unutmayın.

Mac uygulamalarının tam yolunu bulmak için:

1. macOS cihazında Etkinlik **İzleyicisi'ne açın**. Kısıtlamak istediğiniz işlemi bulun ve çift tıklayın

2. Dosyaları **ve Bağlantı Noktalarını Aç sekmesini** seçin.
  
3. macOS uygulamaları için, uygulamanın adı dahil olmak üzere tam yol adına ihtiyacınız vardır.

#### <a name="protect-sensitive-data-from-cloud-synchronization-apps"></a>Hassas verileri bulut eşitleme uygulamalarına karşı koruma

Hassas öğelerin buluta bulut eşitleme uygulamaları (onedrive.exegibi) tarafından eşitlenesini önlemek *için, bulut* eşitleme uygulamasını Izin Verilmeyen **uygulamalar listesine** ekleyin. Izin verilmeyen bir bulut eşitleme uygulaması, engelleme bir DLP ilkesiyle korunan bir öğeye erişmeye çalıştığında, DLP yinelenen bildirimler oluşturabilirsiniz. Izin verilmemiş uygulamalar altında Otomatik karantinaya alma **seçeneğini etkinleştirerek** bu yinelenen **bildirimleri önebilirsiniz**.  

##### <a name="auto-quarantine-preview"></a>Otomatik karantina (önizleme)

> [!NOTE]
> Otomatik karantina yalnızca bu Windows 10 de destekler

Etkinleştirildiğinde, izin verilmeyen bir uygulama DLP korumalı hassas bir öğeye erişmeyi denildiğinde Otomatik karantinaya çalışır. Otomatik karantinaya alın, hassas öğeyi yönetici tarafından yapılandırılmış bir klasöre taşır ve özgün **.txt** bir yer tutucu dosya olarak bırakın. Kullanıcılara öğenin nereye taşındığını ve diğer ilgili bilgileri söylemek için yer tutucu dosyanın metnini yapılandırabilirsiniz.  

Kullanıcı ve yöneticiler için sonsuz bir DLP bildirimleri zincirini önlemek için otomatik karantina kullanabilirsiniz. Bkz. Senaryo [4: Bulut](endpoint-dlp-using.md#scenario-4-avoid-looping-dlp-notifications-from-cloud-synchronization-apps-with-auto-quarantine-preview) eşitleme uygulamalarına gelen DLP bildirimlerini otomatik karantina (önizleme) ile döngüye almaktan kaçının.

### <a name="unallowed-bluetooth-apps"></a>Izin verilmeyen Bluetooth uygulamaları

Kişilerin, ilkeleriniz tarafından korunan dosyaları belirli uygulama uygulamaları aracılığıyla aktarmasını Bluetooth engel olun.

### <a name="browser-and-domain-restrictions-to-sensitive-data"></a>Hassas verilere yönelik tarayıcı ve etki alanı kısıtlamaları

İlkelerinize göre hassas dosyaların kısıtlanmamış bulut hizmeti etki alanlarıyla paylaşılmalarını kısıtla.

#### <a name="unallowed-browsers"></a>Izin verilmeyen tarayıcılar

Daha Windows dosyaları için, yürütülebilir adları ile tanımlanan ve bulut hizmetleri kısıtlaması engellemeye veya engellemeye ayarlanmış olan, zorunlu bir DLP ilkesi koşullarına uygun dosyalara erişimi engellenir. Bu tarayıcıların bir dosyaya erişimi engellenmiş olduğunda, son kullanıcılar kendi tarayıcıları aracılığıyla dosyayı açmalarını isteyen bir bildirim Microsoft Edge.

macOS cihazlarda, tam dosya yolunu eklemeniz gerekir. Mac uygulamalarının tam yolunu bulmak için:

1. macOS cihazında Etkinlik **İzleyicisi'ne açın**. Kısıtlamak istediğiniz işlemi bulun ve çift tıklayın

2. Dosyaları **ve Bağlantı Noktalarını Aç sekmesini** seçin.
  
3. macOS uygulamaları için, uygulamanın adı dahil olmak üzere tam yol adına ihtiyacınız vardır.

#### <a name="service-domains"></a>Hizmet etki alanları

> [!NOTE]
> Hizmet **etki alanları** ayarı yalnızca Microsoft Uyumluluk Uzantısı yüklü olan Microsoft Edge Veya Google Chrome kullanılarak karşıya [yüklenen dosyalara](dlp-chrome-learn-about.md#learn-about-the-microsoft-compliance-extension) uygulanır.

İlkeleriniz tarafından korunan hassas dosyaların, ilkeleriniz tarafından bilgisayarınızdan belirli hizmet etki alanlarına yük isteyip Microsoft Edge.

Liste modu Engelle olarak **ayarlanırsa**, kullanıcı bu etki alanlarına hassas öğeleri yükleyemz. Bir öğe bir DLP ilkesiyle eş olduğundan karşıya yükleme eylemi engellenmiş olduğunda, DLP bir uyarı üretir veya hassas öğenin karşıya yüklemesi engellenir.

Liste modu İzin Ver olarak ayarlanırsa **, kullanıcılar** yalnızca bu etki alanlarına hassas öğeleri yükleyebilir ve **** diğer tüm etki alanlarına erişime izin verilmez.

> [!IMPORTANT]
> Hizmet kısıtlama modu "İzin Ver" olarak ayarlanmışsa, kısıtlamalar zorunlu kılınmadan önce en az bir hizmet etki alanı yapılandırılmış olmalıdır.

Hizmet etki alanının FQDN biçimini bitiş tarihi olmadan kullanın `.` 

Örneğin:

 `www.contoso.com` 

Joker karakterler desteklenmiyor.

### <a name="additional-settings-for-endpoint-dlp"></a>Uç nokta DLP için ek ayarlar

#### <a name="business-justification-in-policy-tips"></a>İlke ipuçlarında işletme gerekçelendirmesi

Kullanıcıların DLP ilkesi ipucu bildirimlerini kullanarak iş gerekçelendirme seçeneğiyle nasıl etkileşim kurarak etkileşimde bulunarak etkileşimde bulunarak etkileşime geçmelerini sabilirsiniz. Bu seçenek, kullanıcılar bir DLP ilkesinde Geçersiz kılmaya karşı engelleme ayarıyla **korunan bir etkinlik** gerçekleştire olduğunda görüntülenir. Bu genel bir ayardır. Aşağıdaki seçeneklerden birini seçebilirsiniz:

- **Varsayılan seçenekleri ve özel metin kutusunu göster**: Varsayılan olarak, kullanıcılar yerleşik bir gerekçelendirmeyi seçerek veya kendi metinlerini girebilirsiniz.
- **Yalnızca varsayılan seçenekleri göster**: Kullanıcılar yalnızca yerleşik bir gerekçelendirmeyi seçebilirsiniz.
- **Yalnızca özel metin kutusunu göster**: Kullanıcılar yalnızca kendi gerekçelerini girebilirsiniz. Son kullanıcı ilkesi ipucu bildiriminde yalnızca metin kutusu görüntülenir. 

##### <a name="customizing-the-options-in-the-drop-down-menu"></a>Açılan menüyü kullanarak seçenekleri özelleştirme

Kullanıcıların İlke bildirimi ipucuyla etkileşimli çalışmalarında görünecek, En çok beş özelleştirilmiş seçenek oluşturmak için, **Seçenekleri özelleştir açılan menüsünü seçebilirsiniz**. 


|Seçenek |Varsayılan metin  |
|---------|---------|
|1. seçenek    | **Bu, kurulmuş bir iş iş akışının bir parçasıdır**  veya özelleştirilmiş metin girebilirsiniz        |
|2. seçenek  |**Yöneticim bu eylemi onayladı** veya özelleştirilmiş metin girebilirsiniz         |
|3. seçenek   |**Acil erişim gerekiyor; Yöneticimi ayrıca bilgilendireceğiz veya** siz özelleştirilmiş bir metin girebilirsiniz          |
|Hatalı pozitif sonuç seçeneğini göster     |**Bu dosyalarda yer alan bilgiler hassas değildir** veya özelleştirilmiş metin girebilirsiniz          |
|5. seçenek    |**Diğer** veya özelleştirilmiş metin girebilirsiniz         |

### <a name="always-audit-file-activity-for-devices"></a>Cihazlar için her zaman dosya etkinliğini denetleme

Varsayılan olarak, cihazlar ekli olduğunda, Office, PDF ve CSV dosyalarıyla ilgili etkinlikler otomatik olarak denetlenr ve etkinlik gezgininde gözden geçirilebilir. Bu etkinliğin yalnızca, ekli cihazlar etkin bir ilkeye ekli olduğunda denetlenleni istemiyorsanız bu özelliği kapatın.

Etkin bir ilkeye dahil olup olmadığına bakılmaksızın, dosya etkinliği her zaman ekli cihazlar için denetlenır.

## <a name="see-also"></a>Ayrıca bkz.

- [Uç nokta veri kaybını önleme hakkında bilgi](endpoint-dlp-learn-about.md)
- [Uç nokta veri kaybını önlemeye başlama](endpoint-dlp-getting-started.md)
- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
- [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)
- [Etkinlik gezgini ile çalışmaya başlama](data-classification-activity-explorer.md)
- [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/)
- [11 Windows 10 cihaz Windows cihaz ekleme ve cihaz ekleme Microsoft 365 genel bakış](/microsoft-365/compliance/device-onboarding-overview)
- [Microsoft 365 aboneliği](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure Active Directory (AAD) bir araya](/azure/active-directory/devices/concept-azure-ad-join)
- [Temel Microsoft Edge yeni Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
- [Varsayılan DLP ilkesiyle çalışmaya başlama](get-started-with-the-default-dlp-policy.md)
- [Şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)
