---
title: Uç nokta veri kaybını önlemeyi kullanma
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
description: Uç nokta veri kaybını önleme (EPDLP) konumlarında kullanmak üzere Microsoft 365 kaybı önleme (DLP) ilkelerini yapılandırmayı öğrenin.
ms.openlocfilehash: cecd489aa5ceb5f0d5d233a4bf09caa24dee6f8b
ms.sourcegitcommit: 40f89c46032ea33de25417106f39cbeebef5a049
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2022
ms.locfileid: "63419163"
---
# <a name="using-endpoint-data-loss-prevention"></a>Uç nokta veri kaybını önlemeyi kullanma

Bu makale, cihazları konum olarak kullanan bir DLP ilkesi oluşturmanıza ve bu ilkede değişiklik de oluşturmanıza neden olan dört senaryoda size yol sunar.

## <a name="dlp-settings"></a>DLP ayarları

Başlamadan önce DLP ayarlarınızı ayarlamıştınız. Ayarlar için tüm DLP ilkelerine uygulanır. Zorunlu ilkeler oluşturmak amacına yönelikse, bunları yapılandırmalı:

- bulut çıkış kısıtlamaları
- izin verilmeyen uygulamalar kısıtlamaları

Veya

- Gürültülü dosya yollarını izlemenin dışında tutmak istemiyorsanız

  > [!div class="mx-imgBorder"]
  > ![DLP ayarlarını seçin.](../media/endpoint-dlp-1-using-dlp-settings.png)

### <a name="endpoint-dlp-windows-1011-and-macos-settings"></a>Uç nokta DLP Windows 10/11 ve macOS ayarları

|Ayar |Windows 10 1809 ve sonrası, Windows 11  |macOS Catalina 10.15 veya sonrası (önizleme)  |Notlar  |
|---------|---------|---------|---------|
|Dosya yolu dışlamaları     |Destekleniyor         |Destekleniyor         |macOS varsayılan olarak açık olan önerilen bir dışlama listesi içerir          |
|Izin Verilmeyen Uygulamalar     |Destekleniyor         |Destekleniyor         |         |
|Izin verilmeyen Bluetooth uygulamaları    |Destekleniyor         |Desteklenmiyor         |         |
|Hassas öğelere yönelik tarayıcı ve etki alanı kısıtlamaları      |Destekleniyor         |Destekleniyor         |         |
|Uç Nokta DLP için ek ayarlar     |Destekleniyor         |Destekleniyor         |MacOS cihazlarda yalnızca varsayılan iş gerekçeleri desteklenmemektedir         |
|Cihazlar için her zaman dosya etkinliğini denetleme     |Destekleniyor         |Destekleniyor         |         |
|Izin verilmeyen uygulamalardan dosyayı otomatik karantinaya alın | Destekleniyor | Desteklenmiyor| |
|Gelişmiş sınıflandırma | Destekleniyor | Desteklenmiyor| |
|İlke ipuçlarında işletme gerekçelendirmesi | Destekleniyor | Destekleniyor| |

### <a name="advanced-classification-scanning-and-protection"></a>Gelişmiş sınıflandırma tarama ve koruma

Gelişmiş sınıflandırma tarama ve koruma, daha gelişmiş Microsoft 365 bulut tabanlı veri sınıflandırma hizmetinin öğeleri taramasını, sınıflandırmasını ve sonuçları yerel makineye geri geri dönmesini sağlar. Bu da DLP ilkelerinize tam olarak adını [alan](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md) varlıklar [(önizleme)](named-entities-learn.md#learn-about-named-entities-preview) sınıflandırma tekniklerinden tam olarak yararlan İlkeler olarak sınıflandırmadan yararlan yararlan İlkeler anlamına gelir.

Gelişmiş sınıflandırmada, içerik tarama ve sınıflandırma için yerel cihazdan bulut hizmetlerine gönderilir. Bant genişliği kullanımı önemli bir sorunsa, cihaz başına uygulanan bu genel ayarda, kullanıla 24 saatlik bir süre için ne kadar kullanılamayacak konusunda bir sınır atabilirsiniz. Bant genişliği kullanım sınırını belirler ve bu sınır aşılırsa, DLP kullanıcı içeriğini buluta göndermeyi durdurursa ve veri sınıflandırması cihazda yerel olarak devam eder. Toplam bant genişliği kullanımı yaklaşık 24 saat sınırının altına düştüğünde, bulut hizmetleriyle iletişim sürdürür.

Bant genişliği kullanımı önemli bir sorun yoksa, bir sınır ayarlanmaz ve sınırsız kullanıma izin ve vermezsiniz.

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

Cihazlarında çok gürültülü olduğundan veya ilgilendiğiniz dosyaları içermelerinden dolayı bazı yolları DLP izleme, DLP uyarısı ve DLP ilkesi zorlamalarının dışında tutmak istiyorabilirsiniz. Bu konumlarda bulunan dosyalar denetlenmekle birlikte bu konumlarda oluşturulan veya değiştirilen dosyalar DLP ilke zorlaması kapsamında olmaz. DLP ayarlarında yol dışlamalarını yapılandırabilirsiniz.

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

### <a name="unallowed-apps"></a>Izin verilmeyen uygulamalar

İzin verilmeyen uygulamalar, sizin oluşturarak DLP korumalı bir dosyaya erişmesine izin verilmeyen uygulamaların listesidir. MacOS ve macOS Windows 10 (önizleme) için kullanılabilir.

bir ilkenin İzin verilmeyen uygulamalar tarafından **Access** ayarı açıksa ve izin verilmeyen listede yer alan bir uygulama korumalı bir dosyaya erişmeye çalışırsa, etkinliklere izin verilir, engellenir veya engellenir, ancak kullanıcılar kısıtlamayı geçersiz k kullanabilir. Tüm etkinlikler denetlenmektedir ve etkinlik gezgininde gözden geçirilebilir.

> [!IMPORTANT]
> Yürütülebilir dosyanın yolunu değil, yalnızca yürütülebilir adı (yürütülebilir dosya gibi) browser.exe.

#### <a name="macos-devices-preview"></a>macOS cihazlar (önizleme)

Diğer cihazlarda Windows gibi macOS uygulamalarının Izin Verilmeyen uygulamalar listesinde tanımlayarak hassas verilere **erişmesini de önabileceksiniz**. 

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

Kullanıcı ve yöneticiler için sonsuz bir DLP bildirimleri zincirini önlemek için otomatik karantina kullanabilirsiniz. Bkz. Senaryo [4: Bulut](#scenario-4-avoid-looping-dlp-notifications-from-cloud-synchronization-apps-with-auto-quarantine-preview) eşitleme uygulamalarına gelen DLP bildirimlerini otomatik karantina (önizleme) ile döngüye almaktan kaçının.

### <a name="unallowed-bluetooth-apps"></a>Izin verilmeyen Bluetooth uygulamaları

Kişilerin, ilkeleriniz tarafından korunan dosyaları belirli uygulama uygulamaları aracılığıyla aktarmasını Bluetooth engel olun.

### <a name="browser-and-domain-restrictions-to-sensitive-data"></a>Hassas verilere yönelik tarayıcı ve etki alanı kısıtlamaları

İlkelerinize göre hassas dosyaların kısıtlanmamış bulut hizmeti etki alanlarıyla paylaşılmalarını kısıtla.

#### <a name="unallowed-browsers"></a>Izin verilmeyen tarayıcılar

Daha Windows dosyaları için, yürütülebilir adları ile tanımlanan ve bulut hizmetleri kısıtlaması engellemeye veya engellemeye ayarlanmış olan, zorunlu bir DLP ilkesi koşullarına uygun dosyalara erişimi engellenir. Bu tarayıcıların bir dosyaya erişimi engellenmişse, son kullanıcılar bir bildirim görerek dosyayı Microsoft Edge üzerinden açmalarını veya yapılandırılmışsa özelleştirilmiş bir ileti görüntülemelerini ister.

macOS cihazlarda, tam dosya yolunu eklemeniz gerekir. Mac uygulamalarının tam yolunu bulmak için:

1. macOS cihazında Etkinlik **İzleyicisi'ne açın**. Kısıtlamak istediğiniz işlemi bulun ve çift tıklayın

2. Dosyaları **ve Bağlantı Noktalarını Aç sekmesini** seçin.
  
3. macOS uygulamaları için, uygulamanın adı dahil olmak üzere tam yol adına ihtiyacınız vardır.

#### <a name="service-domains"></a>Hizmet etki alanları

> [!NOTE]
> Hizmet **etki alanları** ayarı yalnızca Microsoft Uyumluluk Uzantısı yüklü olan Microsoft Edge Veya Google Chrome kullanılarak karşıya [yüklenen dosyalara](dlp-chrome-learn-about.md#learn-about-the-microsoft-compliance-extension) uygulanır.

İlkeleriniz tarafından korunan hassas dosyaların, ilkeleriniz tarafından bilgisayarınızdan belirli hizmet etki alanlarına yük isteyip Microsoft Edge.

Liste modu Engelle olarak **ayarlanırsa**, kullanıcı bu etki alanlarına hassas öğeleri yükleyemz. Bir öğe bir DLP ilkesiyle eş olduğundan karşıya yükleme eylemi engellenmiş olduğunda, DLP bir uyarı üretir veya hassas öğenin karşıya yüklemesi engellenir.

Liste modu İzin Ver olarak ayarlanırsa **, kullanıcılar** yalnızca bu etki alanlarına hassas öğeleri yükleyebilir ve **** diğer tüm etki alanlarına erişim izni verilmez.

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

<!--See [Scenario 5: Configure a policy to use the customized business justification](#scenario-5-configure-a-policy-to-use-the-customized-business-justification)-->

### <a name="always-audit-file-activity-for-devices"></a>Cihazlar için her zaman dosya etkinliğini denetleme

Varsayılan olarak, cihazlar ekli olduğunda, Office, PDF ve CSV dosyalarıyla ilgili etkinlikler otomatik olarak denetlenr ve etkinlik gezgininde gözden geçirilebilir. Bu etkinliğin yalnızca, ekli cihazlar etkin bir ilkeye ekli olduğunda denetlenleni istemiyorsanız bu özelliği kapatın.

Etkin bir ilkeye dahil olup olmadığına bakılmaksızın, dosya etkinliği her zaman ekli cihazlar için denetlenır.

## <a name="tying-dlp-settings-together"></a>DLP ayarlarını birlikte yapılandırma

Uç Nokta DLP ve Edge Chromium Web tarayıcısıyla, hassas öğelerin izin verilmemiş bulut uygulamaları ve hizmetleriyle istediğiniz zaman paylaşımını kısıtlayabilirsiniz. Edge Chromium bir öğenin Uç Nokta DLP ilkesiyle sınırlandırılmış olduğunu ve erişim kısıtlamalarını zorlar.

Uç Nokta DLP'yi doğru yapılandırılmış bir DLP ilkesinde ve Microsoft Edge tarayıcısında konum olarak kullanırsanız, bu ayarlarda tanımmış olduğunuz izin verilmeyen tarayıcıların DLP ilkesi denetimlerinize uygun olan hassas öğelere erişimi engel olur. Bunun yerine, kullanıcılar DLP'nin dayatılan kısıtlamaları anlayan Microsoft Edge, DLP ilkesi koşullarına uygun olduğunda etkinlikleri engelleyebilir veya kısıtlayan ELP'i kullanmaya yeniden yönlendireceğiz.

Bu kısıtlamayı kullanmak için üç önemli parça yapılandırmanız gerekir:

1. Hassas öğelerin paylaşılmasını engellemek istediğiniz yerleri (hizmetler, etki alanları, IP adresleri) belirtin.

2. Bir DLP ilkesi eşleşmesi olduğunda belirli hassas öğelere erişmesine izin verilmiyor tarayıcıları ekleyin.

3. E-postayı bulut hizmetleri ve izin verilmeyen tarayıcıdan Access'i dönüştürerek, **yüklemenin bu alanlarla** sınırlandırılmış olması gereken hassas öğe türleri tanımlamak Upload DLP **ilkelerini yapılandırabilirsiniz**.

Yeni hizmetler, uygulamalar ve ilkeler eklemeye devam eder ve iş ihtiyaçlarına göre kısıtlamalarınızı genişletebilirsiniz ve hassas verileri koruyabilirsiniz. 

Bu yapılandırma, verilerinizin güvenli kalmasını sağlarken aynı zamanda kullanıcıların hassas olmayan öğelere erişmesini ve bu öğeleri paylaşmasını engelleyen veya kısıtlayan gereksiz kısıtlamaları önlemeye de yardımcı olur.

## <a name="endpoint-dlp-policy-scenarios"></a>Uç nokta DLP ilkesi senaryoları

Uç Nokta DLP özelliklerini ve bunların DLP ilkeleriyle nasıl ortaya çıkar olduklarını tanımanıza yardımcı olmak için, takip etmek için bazı senaryoları bir araya getirdik.

> [!IMPORTANT]
> Bu Uç Nokta DLP senaryoları, DLP ilkelerini oluşturmaya ve ayarlamaya yönelik resmi yordamlar değildir. Genel durumlarda DLP ilkeleriyle çalışman gerekirken aşağıdaki konulara bakın:
>
>- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
>- [Varsayılan DLP ilkesiyle çalışmaya başlama](get-started-with-the-default-dlp-policy.md)
>- [Şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)
>- [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)

### <a name="scenario-1-create-a-policy-from-a-template-audit-only"></a>Senaryo 1: Şablondan ilke oluşturma, yalnızca denetleme

Bu senaryolar için etkinlik gezginine önceden cihaz ekleme ve raporlama cihazlarınız gerekir. Henüz cihaz eklemedıysanız bkz. Uç nokta [veri kaybı önleme ile çalışmaya başlama](endpoint-dlp-getting-started.md).

1. Veri kaybını [önleme sayfasını açın](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. İlke **oluştur'a seçin**.

3. Bu senaryo için **Gizlilik'i** ve ardından **ABD Kişisel Bilgileri (PII)** Verileri'ne ve ardından Sonraki'yi **seçin**.

4. Cihazlar dışındaki **tüm** konumlar için Durum alanını kapalı konuma **kapatın**. **İleri**'yi seçin.

5. Varsayılan Gözden Geçir **ve ayarları şablon seçiminden özelleştirin ve Ardından** Sonraki'yi **seçin**.

6. Varsayılan Koruma eylemleri **değerlerini kabul et** ve Sonraki'yi **seçin**.

7. Bu **cihazlarda etkinlikleri denetle veya kısıtla Windows ve** eylemleri Yalnızca denetim olarak **bırakın**. **İleri**'yi seçin.

8. İlk değeri **sınamak istiyorum varsayılan değerini kabul edin ve** test modundayken **ilke ipuçlarını göster'i seçin**. **İleri**'yi seçin.

9. Ayarlarınızı gözden geçirin ve Gönder'i **seçin**.

10. Yeni DLP ilkesi ilke listesinde görünür.

11. Etkinlik gezgininde izlenen uç noktalardan gelen verileri denetleme. Cihazlar için konum filtresini ayarlayın ve ilkeyi ekleyin, ardından bu ilkenin etkisini görmek için ilke adına göre filtre uygulama; Gerekirse [bkz. Etkinlik gezginiyle](data-classification-activity-explorer.md) çalışmaya başlama.

12. ABD'nin Kişisel Olarak Tanınmaya Neden Olacak Bilgiler (PII) Verileri koşullarını tetikleyen içerikler içeren bir testi, kuruluş dışındaki biriyle paylaşmaya çalışabilirsiniz. Bu, ilkeyi tetikler.

13. Etkinlik gezgininde olay olup denetleme.

### <a name="scenario-2-modify-the-existing-policy-set-an-alert"></a>Senaryo 2: Var olan ilkeyi değiştirme, uyarı ayarlama

1. Veri kaybını [önleme sayfasını açın](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Senaryo **1'de oluşturduğunuz ABD Kişisel Bilgileri (PII)** Veri politikasını seçin.

3. **İlkeyi düzenle'yi seçin**.

4. Gelişmiş **DLP kuralları sayfasına gidin** ve ABD'de algılanan Düşük hacimli içerik için Kişisel Olarak **Tanımlanabilen Inf'ı düzenleyin**.

5. Sayfayı Olay **raporları bölümüne kadar** aşağı kaydırın ve Kural eşleşmesi olduğunda **yöneticilere uyarı gönder'i Açık olarak** **ayarlayın**. E-posta uyarıları otomatik olarak yöneticiye ve alıcı listesine ekley istediğiniz herkese gönderilir. 

   > [!div class="mx-imgBorder"]
   > ![turn-on-incident-reports.](../media/endpoint-dlp-2-using-dlp-incident-reports.png)
   
6. Bu senaryonun amaçları doğrultusunda, bir **etkinlik kuralla her eşleşmesinde Uyarı gönder'i seçin**.

7. **Kaydet**'i seçin.

8. Önceki tüm ayarlarınızı korumak için, **Sonraki'ye ve** ardından **İlke değişikliklerini** gönder'e tıklayın.

9. ABD'nin Kişisel Olarak Tanınmaya Neden Olacak Bilgiler (PII) Verileri koşullarını tetikleyen içerikler içeren bir testi, kuruluş dışındaki biriyle paylaşmaya çalışabilirsiniz. Bu, ilkeyi tetikler.

10. Etkinlik gezgininde olay olup denetleme.

### <a name="scenario-3-modify-the-existing-policy-block-the-action-with-allow-override"></a>Senaryo 3: Var olan ilkeyi değiştirme, geçersiz kılmaya izin ver ile eylemi engelleme

1. Veri kaybını [önleme sayfasını açın](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Senaryo **1'de oluşturduğunuz ABD Kişisel Bilgileri (PII)** Veri politikasını seçin.

3. **İlkeyi düzenle'yi seçin**.

4. Gelişmiş **DLP kuralları sayfasına gidin** ve ABD'de algılanan Düşük hacimli içerik için Kişisel Olarak **Tanımlanabilen Inf'ı düzenleyin**.

5. Sayfayı Cihaz üzerinde **etkinlikleri denetleme veya kısıtlama bölümüne Windows** ve her etkinlik için ilgili eylemi Geçersiz kılma ile engelle **olarak ayarlayın**.

   > [!div class="mx-imgBorder"]
   > ![engellemeyi geçersiz kılma eylemiyle ayarlayın.](../media/endpoint-dlp-6-using-dlp-set-blocked-with-override.png)
   
6. **Kaydet**'i seçin.

7. ABD'de Kişisel Kimliği Belirlenebilir Inf algılanan yüksek hacimli içerik için 4-7 **arasındaki adımları yinelayın**.

8. Önceki tüm ayarlarınızı korumak için, **Sonraki'ye ve** ardından **İlke değişikliklerini** gönder'e tıklayın.

9. ABD'nin Kişisel Olarak Tanınmaya Neden Olacak Bilgiler (PII) Verileri koşullarını tetikleyen içerikler içeren bir testi, kuruluş dışındaki biriyle paylaşmaya çalışabilirsiniz. Bu, ilkeyi tetikler.

   İstemci cihazında bunun gibi bir açılır pencere görüyorsunuz:

   > [!div class="mx-imgBorder"]
   > ![uç nokta dlp istemcisi bildirimi geçersiz kılmayı engelledi.](../media/endpoint-dlp-3-using-dlp-client-blocked-override-notification.png)

10. Etkinlik gezgininde olay olup denetleme.

### <a name="scenario-4-avoid-looping-dlp-notifications-from-cloud-synchronization-apps-with-auto-quarantine-preview"></a>Senaryo 4: Bulut eşitleme uygulamalarına gelen DLP bildirimlerini otomatik karantina (önizleme) ile döngüye almaktan kaçının

#### <a name="before-you-begin"></a>Başlamadan önce

Bu senaryoda, dosyaları Çok Gizli duyarlılık **etiketiyle** eşitlemek OneDrive engellenmiş olur. Bu, birden çok bileşeni ve yordamları olan karmaşık bir senaryodur. Gerekenler:

- Hedef AAD ve zaten yerel bir Windows 10 klasörle OneDrive bulut depolaması eşitlene bir OneDrive kullanıcı hesabı.
- Microsoft Word bilgisayarda Windows 10 yüklü
- Yapılandırılmış ve yayımlanmış duyarlılık etiketleri— bkz [. Duyarlılık](get-started-with-sensitivity-labels.md#get-started-with-sensitivity-labels) etiketleriyle çalışmaya başlama ve Duyarlılık [etiketlerini ve ilkelerini oluşturma ve yapılandırma](create-sensitivity-labels.md#create-and-configure-sensitivity-labels-and-their-policies).

Üç yordam vardır.

1. Uç Nokta DLP Otomatik karantina ayarlarını yapılandırma.
2. Çok Gizli duyarlılık etiketine sahip hassas öğeleri **engelleyen bir** ilke oluşturun.
3. İlkenin hedef Windows 10 cihazda bir Word belgesi oluşturun, etiketi ekleyin ve eşitlenen yerel OneDrive kullanıcı hesaplarına kopyalayın.  

#### <a name="configure-endpoint-dlp-unallowed-app-and-auto-quarantine-settings"></a>Uç Nokta DLP izin verilmeyen uygulamayı ve Otomatik karantina ayarlarını yapılandırma

1. Uç [Nokta DLP ayarlarını açma](https://compliance.microsoft.com/datalossprevention?viewid=globalsettings)

2. Izin **verilmeyen uygulamalar'a genişletin**.

3. **Çok Gizli** etiketinin öğelerine erişmesini engellemek için, *Izin verilmeyen* uygulamaları ekle veya düzenle'yi OneDrive bir ** görünen ad ve yürütülebilir ad onedrive.exeonedrive.exeyürütülebilir dosya adı ekleyin.

4. Otomatik **karantinaya alın ve** **Kaydet'i seçin**.

5. Otomatik **karantina ayarları'nın altında Otomatik** karantina **ayarlarını düzenle'yi seçin**.

6. Izin **verilmeyen uygulamalar için Otomatik karantinayı etkinleştir**.

7. Yerel makinelerde özgün hassas dosyaların taşınmalarını istediğiniz klasörün yolunu girin. Örneğin:
   
    *Isaiah langer* kullanıcı adı için **'%homedrive%%homepath%\Microsoft DLP\Quarantine'** klasörü taşınan öğeleri şu adlı klasöre alır:  

    *C:\Users\IsaiahLanger\Microsoft DLP\Karantina\OneDrive*

    yazın ve özgün dosya adına bir tarih ve saat damgası ekler.
    
    > [!NOTE]
    > DLP Otomatik karantinası, izin verilmeyen her uygulama için dosyalar için alt klasörler oluşturur. Dolayısıyla, izin verilmeyen *uygulamalar listesinde Not Defteri* *OneDrive* uygulamalarınız varsa, **\OneDrive** için bir alt klasör ve **\Not Defteri** için başka bir alt klasör oluşturulur.

8. Dosyaları **aşağıdaki metni içeren .txt bir dosyayla değiştir'i seçin** ve yer tutucu dosyaya istediğiniz metni girin. Örneğin, otomatik dörtte *bir olarak adlandırılmış bir 1.docx*:
    
    > %%FileName%% kuruluşun veri kaybı önleme (DLP) ilkesi %%PolicyName%% ile koruduğu ve karantina klasörüne taşındığı hassas bilgileri içerir: %%KarantinaPath%%
    
    bu iletiyi içeren bir metin dosyası bırakır:
    
    > otomatik dörtte 1.docx, kurumnizin veri kaybı önleme (DLP) ilkesiyle koruduğu ve karantina klasörüne taşındığı hassas bilgileri içerir: C:\Users\IsaiahLanger\Microsoft DLP\Karantina\OneDrive\otomatik 1_20210728_151541.docx.

9. **Kaydet'i seçin**

#### <a name="configure-a-policy-to-block-onedrive-synchronization-of-files-with-the-sensitivity-label-highly-confidential"></a>Dosyaların Yüksek Gizli duyarlılık OneDrive eşitlenmiş olarak eşitlenmiş olarak eşitlemeyi engellemek için bir ilke yapılandırma

1. Veri kaybını [önleme sayfasını açın](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. İlke **oluştur'a seçin**.

3. Bu senaryo için Özel'i, **Özel** **ilke'yi ve sonra da Sonraki'yi** **seçin**.

4. Ad ve Açıklama **alanlarını** doldurun **ve** Sonraki'yi **seçin**.

5. Cihazlar dışındaki **tüm** konumlar için Durum alanını kapalı konuma **kapatın**. Bunu test etmek istediğiniz belirli bir son kullanıcı hesabınız varsa, bu hesabı kapsamda seçmeye emin olun. **İleri**'yi seçin.

6. Varsayılan Gelişmiş **DLP kuralları oluştur veya özelleştir seçimini kabul et ve** İleri'yi **seçin**.

7. Şu değerlerle kural oluşturun:
    1. **Ad** >  *Senaryo 4 Otomatik karantinaya alın*.
    1. **Koşullar** >  **İçerik içeriği** >  **Duyarlılık etiketleri** >  **Çok Gizli**.
    1.  **Eylemler** >  **Tüm cihazlarda etkinlikleri denetleme veya Windows Eriştirilmeyen** >  **uygulamalarBlock ile** >  **erişin**. Bu senaryonun amacı doğrultusunda, diğer tüm etkinlikleri temizleyin.
    1. **Kullanıcı bildirimleri** >  **On.**
    1. **Uç nokta** cihazları > **Etkin değilken kullanıcılara ilke ipucu bildirimi göster'i** seçin.
    
8. **Kaydet'i ve** ardından **Sonraki'yi seçin**.

9. Hemen **aç'ı seçin**. **İleri**'yi seçin.

10. Ayarlarınızı gözden geçirin ve Gönder'i **seçin**.

    > [!NOTE]
    > Yeni ilkenin çoğaltılması ve hedef bilgisayara uygulanması için en az bir saat Windows 10 izin ver.

11. Yeni DLP ilkesi ilke listesinde görünür.

#### <a name="test-auto-quarantine-on-the-windows-10-device"></a>Windows 10 cihazında Otomatik karantinaya Windows 10 sınama

1. Dosyaların duyarlılık Windows 10 fazla gizli adım 5 ile eşitlesini engellemek üzere bir ilke yapılandırma altında belirttiğiniz kullanıcı hesabıyla OneDrive [bilgisayarda oturum açın](#configure-a-policy-to-block-onedrive-synchronization-of-files-with-the-sensitivity-label-highly-confidential).

2. İçeriği bu klasörle eşitlenmayacak bir OneDrive. Örneğin:

    *C:\otomatik karantina kaynak klasörü*

3. Otomatik Microsoft Word'i açın ve kaynak klasörde bir dosya oluşturun. Çok **gizli duyarlılık** etiketini uygulama; bkz [. Office'da dosyalarınıza ve e-postanıza duyarlılık Office](https://support.microsoft.com/topic/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).

4. Yeni oluşturduğunuz dosyayı eşitleme klasörünüze OneDrive kopyalayın. Eyleme izin verilmiyor ve dosyanın karantinaya alınmayacaklarını söyleyen bir kullanıcı bildirimi bildirimi görünmektedir. Örneğin, kullanıcı adı *Isaiah Langer* ve Belgeyi otomatik karantinaya *1.docxbaşlıklı bir* belge için şu iletiyi alırsınız:

    ![Belirtilen dosya için eşitleme eylemine izin verilmiyor OneDrive dosyanın karantinaya alın olacağını belirten veri kaybı önleme kullanıcı bildirimi açılır menüsü.](../media/auto-quarantine-user-notification-toast.png)
    
    İleti şu şekilde okunur:
    
    > Bu uygulamayla otomatik belge 1.docx açılmasına izin verilmez. Dosya 'C:\Users\IsaiahLanger\Microsoft DLP\OneDrive' klasörüne karantinaya alınır.

5. **Yok'a seçin**.

6. Yer tutucu metin dosyasını açın. Belge, belgeye **otomatik karantina 1.docx_ *date_time.txt***. 

7. Karantina klasörünü açın ve özgün dosyanın orada olduğunu onaylayın.
 
8. Etkinlik gezgininde izlenen uç noktalardan gelen verileri denetleme. Cihazlar için konum filtresini ayarlayın ve ilkeyi ekleyin, ardından bu ilkenin etkisini görmek için ilke adına göre filtre uygulama; Gerekirse [bkz. Etkinlik gezginiyle](data-classification-activity-explorer.md) çalışmaya başlama.

9. Etkinlik gezgininde olay olup denetleme.

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
