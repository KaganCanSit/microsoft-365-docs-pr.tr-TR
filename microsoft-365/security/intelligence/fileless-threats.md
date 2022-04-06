---
title: Dosyasız tehditler
ms.reviewer: ''
description: Arazide yaşayan dosyasız tehditler ve kötü amaçlı yazılım kategorileri hakkında bilgi edinin
keywords: dosyasız, dosyasız kötü amaçlı yazılım, arazide yaşayan, lolbins, amsi, davranış izleme, bellek tarama, önyükleme kesimi koruması, güvenlik, kötü amaçlı yazılım, Windows Defender ATP, virüsten koruma, AV, Microsoft Defender ATP, yeni nesil koruma
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
ms.openlocfilehash: 4db82cfc20bb1e27b2ef9a75793170c451c3868a
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665348"
---
# <a name="fileless-threats"></a>Dosyasız tehditler

Dosyasız tehditler tam olarak nedir? "Dosyasız" terimi, bir tehdidin yalnızca bir makinenin belleğinde yaşayan bir arka kapı gibi bir dosyada gelmediğini gösterir. Ancak, dosyasız kötü amaçlı yazılım için tek bir tanım yoktur. Terimi geniş bir şekilde ve bazen çalışacak dosyalara güvenen kötü amaçlı yazılım ailelerini tanımlamak için kullanılır.

Saldırılar yürütme, kalıcılık veya bilgi hırsızlığı gibi işlevler için [çeşitli aşamalar](https://attack.mitre.org/wiki/ATT&CK_Matrix) içerir. Saldırı zincirinin bazı bölümleri dosyasız olabilirken, diğerleri dosya sistemini bir biçimde içerebilir.

Netlik sağlamak için dosyasız tehditler farklı kategoriler halinde gruplandırılır.

![Dosyasız kötü amaçlı yazılımların kapsamlı diyagramı.](../../media/security-intelligence-images/fileless-malware.png)<br>
*Şekil 1. Dosyasız kötü amaçlı yazılımların kapsamlı diyagramı*

Dosyasız tehditler, dosyasız kötü amaçlı yazılımların bir makineye nasıl ulaşabileceğini gösteren giriş noktalarına göre sınıflandırılabilir. Güvenlik açığından yararlanma yoluyla, güvenliği aşılmış donanım aracılığıyla veya uygulamaların ve betiklerin düzenli olarak yürütülmesi yoluyla ulaşabilirler.

Ardından, giriş noktası biçimini listeleyin. Örneğin, açıklardan yararlanma işlemleri dosyalara veya ağ verilerine dayalı olabilir, PCI çevre birimleri bir tür donanım vektörleridir ve betikler ve yürütülebilir dosyalar yürütme vektörünün alt kategorileridir.

Son olarak, enfeksiyonun konasını sınıflandırın. Örneğin, bir Flash uygulaması bir donanım cihazından yararlanma, basit bir yürütülebilir dosya ve kötü amaçlı üretici yazılımı gibi çeşitli tehditler içerebilir.

Sınıflandırma, çeşitli dosyasız tehdit türlerini bölmenize ve kategorilere ayırmanıza yardımcı olur. Bazıları daha tehlikelidir, ancak uygulanması daha zordur, diğerleri ise çok gelişmiş olmasalar da (veya kesin olarak) daha yaygın olarak kullanılır.

Bu kategoriden, virüslü makinelerde ne kadar parmak izi bırakabileceklerine bağlı olarak üç ana dosyasız tehdit türü oluşturabilirsiniz.

## <a name="type-i-no-file-activity-performed"></a>Tür I: Hiçbir dosya etkinliği gerçekleştirilmez

Tamamen dosyasız bir kötü amaçlı yazılım, diske hiçbir zaman dosya yazmayı gerektirmeyen bir kötü amaçlı yazılım olarak kabul edilebilir. Bu tür kötü amaçlı yazılımlar ilk etapta bir makineye nasıl bulaşır? Bir örnek, hedef makinenin EternalBlue güvenlik açığından yararlanan kötü amaçlı ağ paketlerini aldığı yerdir. Bu güvenlik açığı DoublePulsar arka kapı yüklemesine izin verir ve bu da yalnızca çekirdek belleğinde kalır. Bu durumda, dosya veya dosyaya yazılan veri yoktur.

Güvenliği aşılmış bir cihazda, cihaz üretici yazılımında (BIOS gibi), USB çevre birimine (BadUSB saldırısı gibi) veya ağ kartının belleniminde gizlenen kötü amaçlı kodlar da olabilir. Tüm bu örneklerin çalışması için diskte bir dosya gerekmez ve teorik olarak yalnızca bellekte bulunabilir. Kötü amaçlı kod yeniden başlatmalardan, disk yeniden biçimlendirmelerinden ve işletim sistemi yeniden yüklemelerinden kurtulacak.

Virüsten koruma ürünlerinin çoğu üretici yazılımını inceleme özelliğine sahip olmadığından bu türdeki bulaşmaların algılanması özellikle zor olabilir. Bir ürünün kötü amaçlı üretici yazılımını inceleme ve algılama özelliğine sahip olduğu durumlarda, bu düzeyde tehditlerin düzeltilmesiyle ilgili önemli zorluklar hala vardır. Bu tür dosyasız kötü amaçlı yazılımlar yüksek düzeyde karmaşıklık gerektirir ve genellikle belirli donanım veya yazılım yapılandırmasına bağlıdır. Bu, kolay ve güvenilir bir şekilde kötüye kullanılabilecek bir saldırı vektörüne sahip değildir. Tehlikeli olsa da, bu tür tehditler nadirdir ve çoğu saldırı için pratik değildir.

## <a name="type-ii-indirect-file-activity"></a>Tür II: Dolaylı dosya etkinliği

Kötü amaçlı yazılımların önemli mühendislik eforu gerektirmeden bir makinede dosyasız varlığına ulaşmanın başka yolları da vardır. Bu türdeki dosyasız kötü amaçlı yazılımlar dosya sistemine doğrudan dosya yazmaz, ancak dolaylı olarak dosyaları kullanabilir. Örneğin, [Poshspy arka kapı](https://www.fireeye.com/blog/threat-research/2017/03/dissecting_one_ofap.html) saldırganları WMI deposuna kötü amaçlı bir PowerShell komutu yüklemiş ve komutu düzenli aralıklarla çalıştıracak bir WMI filtresi yapılandırmış olabilir.

Dosyada zaten bir arka kapı olması gerekmeden komut satırı aracılığıyla bu tür bir yükleme gerçekleştirilebilir. Kötü amaçlı yazılım, dosya sistemine hiç dokunmadan yüklenebilir ve teorik olarak çalıştırılabilir. Ancak WMI deposu, CIM Nesne Yöneticisi tarafından yönetilen merkezi bir depolama alanındaki fiziksel bir dosyada depolanır ve genellikle meşru veriler içerir. Enfeksiyon zinciri teknik olarak fiziksel bir dosya kullansa da, WMI deposu algılanıp kaldırılamayacak çok amaçlı bir veri kapsayıcısı olduğundan dosyasız bir saldırı olarak kabul edilir.

## <a name="type-iii-files-required-to-operate"></a>Tür III: Çalışmak için gereken dosyalar

Bazı kötü amaçlı yazılımlar bir tür dosyasız kalıcılığa sahip olabilir, ancak çalışmak için dosyaları kullanmadan olmaz. Bu senaryoya örnek olarak, kayıt defterinde rastgele bir dosya uzantısı için bir kabuk açık fiil işleyicisi oluşturan Kovter örnektir. Bu uzantıya sahip bir dosyanın açılması, geçerli araç mshta.exe aracılığıyla bir betiğin yürütülmesine neden olur.

![Kovter'ın kayıt defteri anahtarının görüntüsü.](../../media/security-intelligence-images/kovter-reg-key.png)<br>
*Şekil 2. Kovter'ın kayıt defteri anahtarı*

Açık fiil çağrıldığında, kayıt defterinden ilişkili komut başlatılır ve bu da küçük bir betiğin yürütülmesiyle sonuçlanır. Bu betik, daha fazla kayıt defteri anahtarındaki verileri okur ve yürütür ve bu da son yükün yüklenmesine neden olur. Ancak, açık fiili ilk etapta tetikleyebilmek için Kovter'ın fiil tarafından hedeflenen aynı uzantıya sahip bir dosyayı bırakması gerekir (yukarıdaki örnekte uzantı .bbf5590fd'dir). Ayrıca makine başlatıldığında bu dosyayı açmak için yapılandırılmış bir otomatik çalıştırma anahtarı ayarlaması gerekir.

Dosya sistemi pratik kullanımda olmadığından Kovter dosyasız bir tehdit olarak kabul edilir. Rastgele uzantılara sahip dosyalar, tehdidin varlığını doğrulamada kullanılamayabilecek gereksiz veriler içerir. Kayıt defterini depolayan dosyalar, kötü amaçlı içerik varsa algılanamaz ve silinemez kapsayıcılardır.

## <a name="categorizing-fileless-threats-by-infection-host"></a>Enfeksiyon konağı tarafından dosyasız tehditleri kategorilere ayırma

Geniş kategorileri tanımladıktan sonra, artık ayrıntıları inceleyebilir ve enfeksiyon konaklarının dökümünü sağlayabiliriz. Bu kapsamlı sınıflandırma genellikle dosyasız kötü amaçlı yazılım olarak adlandırılan şeyin panoramasını kapsar. Saldırı sınıflarını etkisiz hale getiren ve kötü amaçlı yazılımların silah yarışında üstünlük sağlamamasını sağlayan yeni koruma özellikleri araştırma ve geliştirme çabalarımızı yönlendiriyor.

### <a name="exploits"></a>Patla -tır

**Dosya tabanlı** (Tür III: yürütülebilir, Flash, Java, belgeler): İlk dosya, bir kabuk kodu yürütmek ve bellekte bir yük teslim etmek için işletim sisteminden, tarayıcıdan, Java altyapısından, Flash altyapısından vb. yararlanabilir. Yük dosyasız olsa da, ilk giriş vektör bir dosyadır.

**Ağ tabanlı** (Tür I): Hedef makinedeki bir güvenlik açığından yararlanan bir ağ iletişimi, uygulama veya çekirdek bağlamında kod yürütme gerçekleştirebilir. Örnek olarak, çekirdek belleği içinde bir arka kapı teslim etmek için SMB protokolünde daha önce düzeltilen bir güvenlik açığından yararlanan WannaCry örnek olarak verilmiştir.

### <a name="hardware"></a>Donanım

**Cihaz tabanlı** (Tür I: ağ kartı, sabit disk): Sabit diskler ve ağ kartları gibi cihazların çalışması için yonga kümeleri ve ayrılmış yazılım gerekir. Bir cihazın yonga kümesinde bulunan ve çalışan yazılıma üretici yazılımı denir. Karmaşık bir görev olsa da, [Denklem casusluk grubu tarafından yakalandığından](https://www.kaspersky.com/blog/equation-hdd-malware/7623/) üretici yazılımı kötü amaçlı yazılımdan etkilenebilir.

**CPU tabanlı** (Tür I): Modern CPU'lar karmaşıktır ve yönetim amacıyla üretici yazılımı çalıştıran alt sistemleri içerebilir. Bu tür üretici yazılımları ele geçirilmeye açık olabilir ve CPU'nun içinden çalışacak kötü amaçlı kodların yürütülmesine izin verebilir. Aralık 2017'de iki araştırmacı, saldırganların Intel'den gelen herhangi bir modern CPU'da bulunan [Yönetim Altyapısı (ME)](https://en.wikipedia.org/wiki/Intel_Management_Engine) içinde kod yürütmesine izin verebilen bir güvenlik açığı bildirdi. Bu arada, PLATINUM saldırgan grubunun yüklü işletim sistemini atlayarak [görünmez ağ iletişimleri](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/07/platinum-continues-to-evolve-find-ways-to-maintain-invisibility/) gerçekleştirmek için [Intel'in Etkin Yönetim Teknolojisini (AMT)](https://en.wikipedia.org/wiki/Intel_Active_Management_Technology) kullanma yeteneğine sahip olduğu gözlemlenmiştir. ME ve AMT temelde CPU içinde yaşayan ve çok düşük düzeyde çalışan otonom mikro bilgisayarlardır. Bu teknolojilerin amacı uzaktan yönetilebilirlik sağlamak olduğundan, donanıma doğrudan erişimleri vardır, işletim sisteminden bağımsızdır ve bilgisayar kapalı olsa bile çalışabilir.

ÜRETICI yazılımı düzeyinde güvenlik açığı olmasının yanı sıra CPU'lar doğrudan donanım devresine takılmış arka kapılarla üretilebilir. Bu saldırı [araştırıldı ve geçmişte mümkün olduğu kanıtlandı](https://www.emsec.rub.de/media/crypto/veroeffentlichungen/2015/03/19/beckerStealthyExtended.pdf) . Belirli x86 işlemci modellerinin, normal uygulamaların ayrıcalıklı yürütme kazanabileceği [bir arka kapı sağlayabilecek ikincil bir](https://www.theregister.co.uk/2018/08/10/via_c3_x86_processor_backdoor/) RISC benzeri CPU çekirdeği içerdiği bildirilmiştir.

**USB tabanlı** (Tip I): Her türlü USB cihazları, işletim sistemiyle kötü amaçlı yollarla etkileşim kurabilen kötü amaçlı bellenim ile yeniden programlanabilir. Örneğin [BadUSB tekniği](https://arstechnica.com/information-technology/2014/07/this-thumbdrive-hacks-computers-badusb-exploit-makes-devices-turn-evil/) , yeniden programlanmış bir USB çubuğunun tuş vuruşları aracılığıyla makinelere komut gönderen bir klavye veya trafiği istediğiniz zaman yeniden yönlendirebilen bir ağ kartı olarak davranmasına olanak tanır.

**BIOS tabanlı** (Tür I): BIOS, yonga kümesi içinde çalışan bir üretici yazılımıdır. Bir makine açık olduğunda yürütülür, donanımı başlatır ve ardından denetimi önyükleme kesimine aktarır. BIOS, düşük düzeyde çalışan ve önyükleme kesiminden önce yürütülen önemli bir bileşendir. Geçmişte [Mebromi rootkit'te](https://www.webroot.com/blog/2011/09/13/mebromi-the-first-bios-rootkit-in-the-wild/) olduğu gibi BIOS üretici yazılımını kötü amaçlı kodla yeniden programlamak mümkündür.

**Hiper yönetici tabanlı** (Tür I): Modern CPU'lar donanım hiper yöneticisi desteği sağlayarak işletim sisteminin sağlam sanal makineler oluşturmasına olanak sağlar. Sanal makine sınırlı, simülasyon ortamında çalışır ve öykünmeden habersiz teoridedir. Bir makineyi devralan bir kötü amaçlı yazılım, kendisini çalışan işletim sisteminin alanının dışında gizlemek için küçük bir hiper yönetici uygulayabilir. Bu tür kötü amaçlı yazılımlar geçmişte kuramsallaştırılmıştır ve son olarak gerçek hiper yönetici rootkit'leri [gözlemlenmiştir](http://seclists.org/fulldisclosure/2017/Jun/29), ancak bugüne kadar çok azı bilinmektedir.

### <a name="execution-and-injection"></a>Yürütme ve ekleme

**Dosya tabanlı** (Tür III: yürütülebilir dosyalar, DLL'ler, LNK dosyaları, zamanlanmış görevler): Bu standart yürütme vektördür. Basit bir yürütülebilir dosya, bellekte ek yük çalıştırmak için birinci aşama kötü amaçlı yazılım olarak başlatılabilir veya diğer meşru çalışan işlemlere eklenebilir.

**Makro tabanlı** (Tür III: Office belgeler): [VBA dili](/office/vba/Library-Reference/Concepts/getting-started-with-vba-in-office), düzenleme görevlerini otomatikleştirmek ve belgelere dinamik işlevsellik eklemek için tasarlanmış esnek ve güçlü bir araçtır. Bu nedenle, şifre çözme, çalıştırma veya yürütülebilir yük ekleme gibi kötü amaçlı işlemleri gerçekleştirmek, hatta [qkG örneğinde](https://blog.trendmicro.com/trendlabs-security-intelligence/qkg-filecoder-self-replicating-document-encrypting-ransomware/) olduğu gibi fidye yazılımının tamamını uygulamak saldırganlar tarafından kötüye kullanılabilir. Makrolar bir Office işlemi (örneğin, Winword.exe) bağlamında yürütülür ve bir betik dilinde uygulanır. Virüsten koruma yazılımının inceleyebilecek ikili yürütülebilir dosyası yoktur. Office uygulamalar bir belgedeki makroları yürütmek için kullanıcıdan açık onay isterken, saldırganlar kullanıcıları makroların yürütülmesine izin verecek şekilde kandırmak için sosyal mühendislik tekniklerini kullanır.

**Betik tabanlı** (Tür II: dosya, hizmet, kayıt defteri, WMI deposu, kabuk): JavaScript, VBScript ve PowerShell betik oluşturma dilleri varsayılan olarak Windows platformlarda kullanılabilir. Betikler makrolarla aynı avantajlara sahiptir; bunlar metinsel dosyalardır (ikili yürütülebilir dosyalar değildir) ve temiz ve meşru bir bileşen olan yorumlayıcı bağlamında (wscript.exe, powershell.exe gibi) çalışır. Betikler çok yönlü bir özelliktir ve bir dosyadan (çift tıklayarak) çalıştırılabilir veya doğrudan yorumlayıcının komut satırında yürütülebilir. Komut satırında çalıştırmak, kötü amaçlı yazılımların kötü amaçlı betikleri wmi deposundan [WMI olay abonelikleri](https://www.fireeye.com/blog/threat-research/2017/03/dissecting_one_ofap.html) olarak [otomatik çalıştırma kayıt defteri anahtarları içinde otomatik](https://www.gdatasoftware.com/blog/2014/07/23947-poweliks-the-persistent-malware-without-a-file) başlangıç hizmetleri olarak kodlamasına olanak tanır. Ayrıca, virüslü bir makineye erişim elde eden bir saldırgan komut istemine betiği giriş yapabilir.

**Disk tabanlı** (Tür II: Önyükleme Kaydı): Önyükleme Kaydı bir diskin veya birimin ilk kesimidir ve işletim sisteminin önyükleme işlemini başlatmak için gereken yürütülebilir kodu içerir. [Petya](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/27/new-ransomware-old-techniques-petya-adds-worm-capabilities/?source=mmpc) gibi tehditler, önyükleme kaydının üzerine kötü amaçlı kod yazarak bulaşabilir. Makine önyüklendiğinde, kötü amaçlı yazılım hemen denetime geçer. Önyükleme Kaydı dosya sisteminin dışında yer alır, ancak işletim sistemi tarafından erişilebilir. Modern virüsten koruma ürünleri tarama ve geri yükleme özelliğine sahiptir.

## <a name="defeating-fileless-malware"></a>Dosyasız kötü amaçlı yazılımları yeniyor

Microsoft olarak, yeni tehdit eğilimlerini belirlemek ve tehdit sınıflarını azaltmak için çözümler geliştirmek için güvenlik ortamını etkin bir şekilde izliyoruz. Çok çeşitli tehditlere karşı etkili olan dayanıklı korumaları kullanıyoruz. Kötü Amaçlı Yazılımdan Koruma Tarama Arabirimi (AMSI), davranış izleme, bellek taraması ve önyükleme kesimi koruması [aracılığıyla Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint), ağır karartma ile bile dosyasız tehditleri inceleyebilir. Buluttaki makine öğrenmesi teknolojileri, bu korumaları yeni ve yeni ortaya çıkan tehditlere karşı ölçeklendirmemize olanak sağlar.

Daha fazla bilgi edinmek için şunu okuyun: [Gözlerden uzak ama görünmez değil: Davranış izleme, AMSI ve yeni nesil AV ile dosyasız kötü amaçlı yazılımları yenmek](https://cloudblogs.microsoft.com/microsoftsecure/2018/09/27/out-of-sight-but-not-invisible-defeating-fileless-malware-with-behavior-monitoring-amsi-and-next-gen-av/)

## <a name="additional-resources-and-information"></a>Ek kaynaklar ve bilgiler

[Tehdit koruması özelliklerini Microsoft 365 E5 dağıtmayı](/microsoft-365/solutions/deploy-threat-protection) öğrenin.
