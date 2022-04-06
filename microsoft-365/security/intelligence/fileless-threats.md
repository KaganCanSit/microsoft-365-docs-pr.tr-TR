---
title: Dosyasız tehditler
ms.reviewer: ''
description: Karada yaşayan dosyasız tehdit ve kötü amaçlı yazılım kategorilerini öğrenin
keywords: dosyasız, dosyasız kötü amaçlı yazılım, karadan canlı, çok canlılar, amsi, davranış izleme, bellek tarama, önyükleme sektör koruması, güvenlik, kötü amaçlı yazılım, Windows Defender ATP, virüsten koruma, AV, Microsoft Defender ATP, yeni nesil koruma
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 97545714ff468c7be238585ab5d137a1ac93a5f9
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63705922"
---
# <a name="fileless-threats"></a>Dosyasız tehditler

Dosyasız tehdit tam olarak nedir? "Dosyasız" terimi, bir dosyada, örneğin yalnızca bir makinenin belleğinde can alan bir arka kapı gibi bir tehdit olmadığını önerir. Öte yandan, dosyasız kötü amaçlı yazılım için tek bir tanım yoktur. Bu terim geniş bir kitleyle kullanılır ve bazen de dosyalara güvenen kötü amaçlı yazılım ailelerini tanımlamak için kullanılır.

Saldırılar [yürütme, kalıcılık](https://attack.mitre.org/wiki/ATT&CK_Matrix) veya bilgi hırsızlığı gibi işlevler için çeşitli evreler içerir. Saldırı zincirinin bazı bölümleri dosyasızken, diğerleri dosya sistemini bir şekilde içeriyor olabilir.

Netlik sağlamak için, dosyasız tehditler farklı kategorilere ayrılır.

![Dosyasız kötü amaçlı yazılım kapsamlı diyagramı.](../../media/security-intelligence-images/fileless-malware.png)<br>
*Şekil 1. Dosyasız kötü amaçlı yazılım kapsamlı diyagramı*

Dosyasız tehditler, dosyasız kötü amaçlı yazılımların bir makineye nasıl ulaşıla bir makineye nasıl ulaşıla bir olduğunu gösteren giriş noktasına göre sınıflandırılabilir. Bir istismar yoluyla, güvenliği ihlal edilmiş donanım aracılığıyla veya uygulama ve betiklerin düzenli olarak yürütülmesi yoluyla ulaşabilirsiniz.

Ardından, giriş noktası formlarını listelenin. Örneğin, açıklardan yararlanan dosyalar veya ağ verileri temel alınabilir, PCI çevre birimleri bir tür donanım vektörü ve betikler ve yürütülebilir dosyalar yürütme vektörü altkategorileridir.

Son olarak, bulaşma ana bilgisayarını sınıflandıryın. Örneğin, bir Flash uygulaması bir donanım cihazından istismar aracı, basit bir yürütülebilir dosya ve kötü amaçlı üretici yazılımı gibi çeşitli tehditlere sahip olabilir.

Sınıflandırıcı, çeşitli dosyasız tehditleri bölmeye ve kategorilere ayırmanıza yardımcı olur. Bazıları daha tehlikelidir, ancak uygulanması daha zordur, diğerleri ise çok gelişmiş olmalarına rağmen (veya tam olarak) daha yaygın kullanılırlar.

Bu kategoriden, virüs bulantılı makinelerde ne kadar parmak izi bırakılacağına bağlı olarak üç ana dosyasız tehdit türüne yer açabilirsiniz.

## <a name="type-i-no-file-activity-performed"></a>Tür I: Hiçbir dosya etkinliği gerçekleştirilmdi

Tam dosyasız bir kötü amaçlı yazılım, diske hiçbir zaman dosya yazmayı gerektiren bir kötü amaçlı yazılım olarak kabul edilir. Böyle bir kötü amaçlı yazılım en başta bir makineye nasıl bulaşacak? Bir örnek olarak, hedef makineDeleBlue güvenlik açığını kullanan kötü amaçlı ağ paketleri alır. Güvenlik açığı Double VeriSatır'ın yüklenmesine izin verir ve bu da yalnızca çekirdek belleğinde kullanılabilir. Bu durumda, dosyada hiçbir dosya veya veri yoktur.

Güvenliği tehlikeye atılmış bir cihazın ayrıca cihaz üretici yazılımında (MAY), BIR USB çevre birimi (BadUSB saldırısı gibi) veya ağ kartının üretici yazılımında gizlenen kötü amaçlı kodlar da olabilir. Bu örneklerin tüm bu örneklerin çalışması için diskte bir dosyanın çalışmasına gerek vardır ve bu şekilde yalnızca bellekte canlı olabilir. Kötü amaçlı kod yeniden başlatmalardan, disk yeniden biçimlerini ve işletim sistemini yeniden yüklemeden sonra da olabilir.

Virüsten koruma ürünlerinin çoğu üretici yazılımını denetleme özelliğine sahip olduğundan, bu tür bulaşmaları özellikle algılamak zor olabilir. Ürünün kötü amaçlı üretici yazılımını denetleme ve algılama özelliğine sahip olduğu durumlarda, bu düzeyde tehditlerin düzeltmesi ile ilgili önemli güçlükler devam eder. Bu dosyasız kötü amaçlı yazılım türü yüksek gelişmişlik düzeyleri gerektirir ve çoğunlukla belirli bir donanım veya yazılım yapılandırmasına bağlıdır. Bu, kolayca ve güvenilir bir şekilde istismar edilebilir bir saldırı vektörü değildir. Bu türün tehlikeli olan tehditleri yaygındır ve çoğu saldırı için pratik olmaz.

## <a name="type-ii-indirect-file-activity"></a>Tür II: Dolaylı dosya etkinliği

Bir makinede, önemli bir mühendislik çalışmasına gerek kalmadan kötü amaçlı yazılımların dosyasız varlığına ulaşmanın başka yolları da vardır. Bu tür dosyasız kötü amaçlı yazılımlar doğrudan dosya sistemine dosya yazmaz, ancak dolaylı olarak dosya kullanır. Örneğin [, Posh bir backdoor](https://www.fireeye.com/blog/threat-research/2017/03/dissecting_one_ofap.html) saldırganları, WMI deposu içinde kötü amaçlı bir PowerShell komutu yüklemiş ve komutu düzenli aralıklarla çalıştıracak şekilde bir WMI filtresi yapılandırmış olabilir.

Bu tür yüklemeleri, dosyada zaten bir backdoor olması gerekmeden komut satırı aracılığıyla gerçekleştirebilirsiniz. Kötü amaçlı yazılım, dosya sistemiyle hiç dokunmadan yüklü ve açık bir şekilde çalıştırabilir. Bununla birlikte, WMI havuzu CIM Nesne Yöneticisi tarafından yönetilen merkezi bir depolama alanında fiziksel bir dosyada depolanır ve genellikle yasal veriler içerir. Bulaşma zinciri teknik olarak fiziksel bir dosya kullanıyor olsa da, WMI havuzu algılanmayacak ve kaldırılamayacak çok amaçlı bir veri kapsayıcısı olduğundan dosyasız bir saldırı olarak kabul edilir.

## <a name="type-iii-files-required-to-operate"></a>III: Dosyaların çalışması için gereken dosyalar

Bazı kötü amaçlı yazılımlarda dosyasız kalıcılık olabilir, ancak dosyaları kullanarak çalışmadan olmaz. Bu senaryoya örnek olarak, rastgele bir dosya uzantısı için kayıt defterinde bir kabuk açık fiil işleyicisi oluşturan  Birater örneği vardır. Bu tür uzantılı bir dosyanın açılması, geçerli araç dosyasından bir betiğin yürütülmesine mshta.exe.

![Ofter'in kayıt defteri anahtarının resmi.](../../media/security-intelligence-images/kovter-reg-key.png)<br>
*Şekil 2. Ukter'in kayıt defteri anahtarı*

Açık fiil çağrıldığında, kayıt defterinden ilişkili komut başlatıldı ve küçük bir betiğin yürütülmesine neden olur. Bu betik, başka bir kayıt defteri anahtarından gelen verileri okur ve bu anahtarı yürütür; böylece son yük yüklenir. Ancak, açık fiilin ilk yerinde tetiklenmesi için,  Bir uzantının eylem tarafından hedef alan uzantısının (yukarıdaki örnekte, uzantı .bbf5590fd) olan bir dosyayı bırakması gerekir. Ayrıca makine başlatıldığında bu tür bir dosyayı açmak için yapılandırılmış bir otomatik çalıştırma anahtarı da ayarlaması gerekir.

Bire bir dosya sistemi pratik bir kullanımdan kaynaklanmayacak için dosyasız bir tehdit olarak kabul edilir. Rastgele uzantılara sahip dosyalar, tehdidin varlığını doğrulamak için kullanılabilir olmayan gereksiz veriler içerir. Kayıt defterini depolayıcı olan dosyalar, kötü amaçlı içerik varsa algılanamadı ve silinemez.

## <a name="categorizing-fileless-threats-by-infection-host"></a>Virüs ana bilgisayarı tarafından dosyasız tehditleri kategorilere ayırma

Kapsamlı kategoriler açıklanmıştır, şimdi ayrıntılarına bakabilir ve bulaşma ev sahipliği yapanların dökümünü sağlarız. Bu kapsamlı sınıflandırma, çoğunlukla dosyasız kötü amaçlı yazılım olarak adlandırılan veri panoramalarını kapsar. Saldırı sınıflarını nötrleştiren ve kötü amaçlı yazılımların kollarda en üsttekilere sahip olmasını sağlamaya yönelik yeni koruma özellikleri araştırma ve geliştirme çabalarımıza devam ediyor.

### <a name="exploits"></a>Exploits

Dosya **tabanlı (Tür** III: yürütülebilir, Flash, Java, belgeler): Bir başlangıç dosyası, kabukkodu yürütmek ve bellekte yükü teslim etmek için işletim sistemini, tarayıcıyı, Java altyapısını, Flash altyapısını vb. kullanabilir. Yük dosyasızken, ilk giriş vektörü bir dosyadır.

**Ağ tabanlı** (Type I): Hedef makinede bir güvenlik açığı nedeniyle yararlanan bir ağ iletişimi, uygulama veya çekirdek bağlamında kod yürütmeyi gerçek anlamda gerçekleştirebilir. Buna örnek olarak, kernel bellek içinde bir geri bağlantı sunmak için SMB protokolünde daha önceden sabit bir güvenlik açığının açıklarından yararlanan WannaCry örnek olarak ve almaktadır.

### <a name="hardware"></a>Donanım

**Cihaz tabanlı** (Tür I: ağ kartı, sabit disk): Sabit diskler ve ağ kartları gibi cihazlar, küme kümeleri ve özel yazılımlar gerektirir. Bir cihazın güvenliket'inde çalışan ve çalışan yazılıma üretici yazılımı adı ve verir. Karmaşık bir görev olsa da, Denklem espionage grubu iş yaparken yakandırıldı ve bellenim kötü amaçlı [yazılımdan virüs bulaşabilir](https://www.kaspersky.com/blog/equation-hdd-malware/7623/).

**CPU tabanlı** (Tür I): Modern CPU'lar karmaşıktır ve yönetim amacıyla üretici yazılımı çalıştıran alt sistemleri içerebilir. Bu üretici yazılımı saldırıya açık olabilir ve CPU'nun içinde çalışan kötü amaçlı kodun yürütülmesine izin verebilir. Aralık 2017'de, iki araştırmacı saldırganların Intel'den modern CPU'da bulunan Yönetim Altyapısı [(ME)](https://en.wikipedia.org/wiki/Intel_Management_Engine) içinde kod yürütmesine olanak sağlayan bir güvenlik açığı olduğunu bildirdi. Bu sırada, PLATINUM grubu, yüklü işletim sistemini atlayarak görünmez ağ iletişimleri gerçekleştirmek için Intel'in Etkin Yönetim Teknolojisi'ne [(AMT)](https://en.wikipedia.org/wiki/Intel_Active_Management_Technology) sahip [](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/07/platinum-continues-to-evolve-find-ways-to-maintain-invisibility/)olduğu gözlemlenir. ME ve AMT temelde CPU'nun içinde bulunan ve çok düşük bir düzeyde çalışan mikro bilgisayarları temel olarak benimsemektedir. Bu teknolojilerin amacı uzaktan yönetilebilirlik sağlamak olduğundan, donanıma doğrudan erişimi vardır, işletim sisteminden bağımsızdır ve bilgisayar kapalı olsa bile  çalışmasına izin verir.

CPUs, üretici yazılımı düzeyinde korumasız olmanın yanı sıra doğrudan donanım devre içine eklenen arka hatlarla da üretilebilir. Bu saldırı geçmişte [araştırıldı ve mümkün](https://www.emsec.rub.de/media/crypto/veroeffentlichungen/2015/03/19/beckerStealthyExtended.pdf) olduğu kanıtlandı. Bazı x86 işlemci modellerinde, normal uygulamaların ayrıcalıklı yürütmeyi sağlandığı bir [backdoor](https://www.theregister.co.uk/2018/08/10/via_c3_x86_processor_backdoor/) sağlayan, ekli bir RISC-like CPU çekirdek olduğu bildirildi.

**USB tabanlı** (Type I): Her türlü USB cihazı, farfarklı yollarla işletim sistemiyle etkileşim kurabilen kötü amaçlı üretici yazılımıyla yeniden programlandırabilirsiniz. Örneğin, [BadUSB](https://arstechnica.com/information-technology/2014/07/this-thumbdrive-hacks-computers-badusb-exploit-makes-devices-turn-evil/) tekniği yeniden programlanmış BIR USB çubuğuna tuş vuruşları yoluyla veya istediğiniz zaman trafiği yönlendiren bir ağ kartı olarak makineye komut gönderen bir klavye gibi davranmaya olanak sağlar.

**FIRMWARE tabanlı** (Tür I): YERİNAÇEPİ, bir üretici yazılımının içinde çalışan bir üretici yazılımıdır. Bir makine açık olduğunda yürütülür, donanım başlatılır ve ardından denetimi önyükleme sektörüne devreder. BU DAMİ, düşük bir düzeyde çalışan ve önyükleme sektöründen önce çalışan önemli bir bileşendir. Mebromi kök seti ile geçmişte olduğu gibi, FIRMWARE üretici yazılımını kötü amaçlı kodla yeniden [programlayabilmeniz mümkündür](https://www.webroot.com/blog/2011/09/13/mebromi-the-first-bios-rootkit-in-the-wild/).

**Hipervisor tabanlı** (Tür I): Modern CPU'lar donanım hipervisor desteği sağlayarak işletim sisteminin güçlü sanal makineler oluşturmasına olanak sağlar. Sanal bir makine yalnızca sınırlı, sanal bir ortamda çalışır ve teorisinde bu empatiyi fark eder. Bir makinenin üzerine kötü amaçlı yazılım tarafından alınan bir kötü amaçlı yazılım, kendisini çalışan işletim sisteminin değil dışında gizlemek için küçük bir hipervisor uygulayıyor olabilir. Geçmişte bu tür kötü amaçlı yazılımlar temlik edilmiştir ve geçmişte gerçek hipervisor kök setleri gözlemlenir [; ancak](http://seclists.org/fulldisclosure/2017/Jun/29) tarih olarak çok az şey bilinir.

### <a name="execution-and-injection"></a>Yürütme ve ekleme

**Dosya tabanlı** (Tür III: yürütülebilir dosyalar, DLL'ler, LNK dosyaları, zamanlanmış görevler): Bu standart yürütme vektörüdir. Basit bir yürütülebilir dosya, bellekte ek yük çalıştırmak veya başka yasal çalıştırma işlemlerine ek yük çalıştırmak için ilk aşamalı kötü amaçlı yazılım olarak başlatabilirsiniz.

**Makro tabanlı** (Tür III: Office belgeleri): [VBA](/office/vba/Library-Reference/Concepts/getting-started-with-vba-in-office) dili, düzenleme görevlerini otomatikleştirmek ve belgelere dinamik işlevler eklemek için tasarlanmış esnek ve güçlü bir araçtır. Bu nedenle, saldırganlar tarafından kod çözme, çalıştırma veya yürütülebilir bir yük ekleme, hatta [qkG](https://blog.trendmicro.com/trendlabs-security-intelligence/qkg-filecoder-self-replicating-document-encrypting-ransomware/) gibi fidye yazılımlarının tamamını uygulama gibi kötü amaçlı işlemleri yapmak için kötüye çalıştırılabilir. Makrolar, bir Office süreci bağlamında yürütülür (örneğin, Winword.exe) ve betik dilinde uygulanır. Virüsten koruma yazılımının incelebilir ikili dosyası yoktur. Bu Office belgeden makro yürütmek için kullanıcıdan açık izinler gerekir ama saldırganlar kullanıcıları makroların yürütülsine izin vermeleri için kandırmak için sosyal mühendislik tekniklerini kullanır.

**Betik tabanlı** (Type II: file, service, registry, WMI repo, shell): JavaScript, VBScript ve PowerShell betik dilleri Windows platformlarda kullanılabilir. Betikler makrolarla aynı avantajlara sahiptir; bunlar metin dosyalarıdır (ikili yürütülebilir dosyalar değildir) ve yorumlayıcının bağlamında (wscript.exe, powershell.exe gibi) temiz ve yasal bir bileşendir. Betikler çok yönlüdür ve bir dosyadan çalıştırabilirsiniz (çift tıklayarak) veya doğrudan bir yorumlayıcının komut satırı üzerinde yürütülebilir. Komut satırı üzerinde çalıştırarak kötü amaçlı betiklerin, OTOMATIK Çalıştır kayıt defteri anahtarları [](https://www.gdatasoftware.com/blog/2014/07/23947-poweliks-the-persistent-malware-without-a-file) içinde WMI olay abonelikleri olarak [WMI](https://www.fireeye.com/blog/threat-research/2017/03/dissecting_one_ofap.html) repo'dan otomatik başlangıç hizmetleri olarak kodlanmasına izin verir. Dahası, virüs bulaşmış bir makineye erişim kazanmış olan bir saldırgan komut istemine betiği yazabilir.

**Disk tabanlı** (Tür II: Önyükleme Kaydı): Önyükleme Kaydı, disk veya ses düzeyinin ilk sektörüdür ve işletim sisteminin önyükleme işlemini başlatmak için gerekli yürütülebilir kod içerir. [Petya gibi](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/27/new-ransomware-old-techniques-petya-adds-worm-capabilities/?source=mmpc) tehditler, önyükleme kaydına kötü amaçlı kodlar yazarak bulaşabilir. Makine önyüklemede, kötü amaçlı yazılım hemen denetimi kazanır. Önyükleme Kaydı, dosya sisteminin dışındadır, ancak işletim sistemi tarafından erişilebilir. Modern virüsten koruma ürünlerinin tarama ve geri yükleme özelliği vardır.

## <a name="defeating-fileless-malware"></a>Dosyasız kötü amaçlı yazılıma karşı mücadele

Microsoft'ta, yeni tehdit eğilimlerini belirlemek ve tehdit sınıflarını azaltmak için çözümler geliştirmek için güvenlik ortamını etkin bir şekilde takip ediyoruz. Çok çeşitli tehditlere karşı etkili olan dayanıklı korumalar aracımız var. Kötü Amaçlı Yazılımdan Koruma Tarama Arabirimi (AMSI), davranış izleme, bellek tarama ve önyükleme sektör koruması aracılığıyla, Uç Nokta için [Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint) yoğun obfuscation ile bile dosyasız tehditleri inceler. Buluttaki makine öğrenme teknolojileri, bu korumaları yeni ve ortaya çıkan tehditlere karşı ölçeklendirmemizi sağlar.

Daha fazla bilgi edinmek için şunları okuyun: Göz önünden çıkma ama görünmez: Davranış izleme ile dosyasız kötü amaçlı yazılımla mücadele [, AMSI ve yeni nesil AV](https://cloudblogs.microsoft.com/microsoftsecure/2018/09/27/out-of-sight-but-not-invisible-defeating-fileless-malware-with-behavior-monitoring-amsi-and-next-gen-av/)

## <a name="additional-resources-and-information"></a>Ek kaynaklar ve bilgiler

Tehdit koruması özelliklerini [farklı bir alan üzerinde dağıtmayı Microsoft 365 E5](/microsoft-365/solutions/deploy-threat-protection).
