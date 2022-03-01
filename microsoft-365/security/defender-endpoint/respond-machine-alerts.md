---
title: Uç Nokta için Microsoft Defender'da cihazda yanıt eylemleri gerçekleştirin
description: Cihazdan ayrılmış cihazlar, araştırma paketi toplama, etiketleri yönetme, av taraması çalıştırma ve uygulama yürütmeyi kısıtlama gibi yanıt eylemleri gerçekleştirin.
keywords: yanıt verme, ayırma, cihazı ayırma, soruşturma paketini toplama, işlem merkezi, kısıtlama, etiketleri yönetme, av taraması, uygulamayı kısıtlama
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 00347aabe38e4e74374f0b96d189051ebb56af3b
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016511"
---
# <a name="take-response-actions-on-a-device"></a>Cihazda yanıt eylemleri gerçekleştirin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-respondmachine-abovefoldlink)

Cihazları yalıtarak veya araştırma paketi toplayarak algılanan saldırılara hızlı bir şekilde yanıt verin. Cihazlar üzerinde işlemden sonra İşlem merkezi'nde etkinlik ayrıntılarını kontrol edin.

Yanıt eylemleri belirli bir cihaz sayfasının en üstünde görüntülenir ve şunları içerir:

- Etiketleri yönetme
- Otomatik Araştırmayı Başlatma
- Canlı Yanıt Oturumunu Başlatma
- Soruşturma paketini topla
- Virüsten koruma taraması çalıştırma
- Uygulama yürütmeyi kısıtla
- Cihazı yalıt
- Tehdit uzmanına danışın
- İşlem merkezi

[![Yanıt eylemlerinin resmi.](images/response-actions.png)](images/response-actions.png#lightbox)

 Cihaz sayfalarını aşağıdaki görünümlerden herhangi birisinde bulabilirsiniz:

- **Güvenlik işlemleri panosu** - Risk kartında Cihazlar'dan bir cihaz adı seçin.
- **Uyarıları kuyruğu** - Uyarılar kuyruğundan cihaz simgesinin yanındaki cihaz adını seçin.
- **Cihazlar listesi** - Cihazlar listesinden cihaz adının başlığı seçin.
- **Arama kutusu** - Açılan menüden Cihaz'ı seçin ve cihaz adını girin.

> [!IMPORTANT]
>
> - Bu yanıt eylemleri yalnızca Windows 10, sürüm 1703 veya sonraki sürümler, Windows 11, Windows Server 2019 ve Windows Server 2022 cihazlarında kullanılabilir.
> - Bağımsız Windows platformlarda, yanıt özellikleri (Cihaz yalıtım gibi) üçüncü taraf özelliklerine bağlıdır.
> - Microsoft birinci taraf aracıları için, minimum işletim sistemi gereksinimleri için lütfen her özelliğin altındaki "daha fazla bilgi" bağlantısına bakın.

## <a name="manage-tags"></a>Etiketleri yönetme

Mantıksal grup bağlantıları oluşturmak için etiketleri ekleyin veya yönetin. Cihaz etiketleri, ağın uygun şekilde eşlenmesini destekleyerek bağlamı yakalamak için farklı etiketler eklemenize ve bir olayın parçası olarak dinamik liste oluşturmayı etkinleştirmenizi sağlar.

Cihaz etiketleme hakkında daha fazla bilgi için bkz. [Cihaz etiketlerini oluşturma ve yönetme](machine-tags.md).

## <a name="initiate-automated-investigation"></a>Otomatik Araştırmayı Başlatma

Gerektiğinde cihazda yeni genel amaçlı otomatik araştırma başlatabilirsiniz. Bir araştırma çalışırken, cihazdan oluşturulan diğer tüm uyarılar, bu araştırma tamamlanana kadar devam eden bir Otomatik soruşturmaya eklenir. Buna ek olarak, diğer cihazlarda da aynı tehdit görülürse, bu cihazlar araştırmaya eklenir.

Otomatik soruşturmalar hakkında daha fazla bilgi için bkz. [Otomatik soruşturmalara genel bakış](automated-investigations.md).

## <a name="initiate-live-response-session"></a>Canlı yanıt oturumu başlatma

Canlı yanıt, uzak kabuk bağlantısı kullanarak bir cihaza anında erişim olanağı sağlar. Bu size, gerçek zamanlı olarak tanımlanan tehditleri hemen içermek için ayrıntılı yatırım yapma ve hemen yanıt eylemleri yapma gücü verir.

Canlı yanıt; araştırma verilerini toplamaya, betik çalıştırmaya, çözümleme için şüpheli varlıklar göndermeye, tehditleri düzeltmeye ve ortaya çıkan tehditleri önceden ortaya çıkan tehditlere karşı önceden aramana olanak sağlayarak incelemeleri geliştirmek üzere tasarlanmıştır.

Canlı yanıt hakkında daha fazla bilgi için bkz [. Canlı yanıtı kullanan cihazlarda varlıkları araştırma](live-response.md).

## <a name="collect-investigation-package-from-devices"></a>Cihazlardan araştırma paketi topla

Araştırma veya yanıt işleminin bir parçası olarak, bir cihazdan araştırma paketi toplayabilirsiniz. Araştırma paketini toplayarak cihazın geçerli durumunu tanımlayabilir ve saldırgan tarafından kullanılan araç ve teknikleri daha iyi anabilirsiniz.

> [!IMPORTANT]
>
>Bu eylemler şu anda macOS ve Linux için desteklemektedir. Eylemi çalıştırmak için canlı yanıtı kullanın. Canlı yanıt hakkında daha fazla bilgi için bkz [. Canlı yanıtı kullanan cihazlardaki varlıkları araştırma](live-response.md)

Paketi (Zip dosyası) indirmek ve cihazda  meydana gelen olayları araştırmak için

1. Cihaz **sayfasının en üstünde** yanıt eylemleri satırından Araştırma paketini topla'ya tıklayın.
2. Metin kutusunda bu eylemi neden gerçekleştirmek istediğiniz belirtin. **Onayla'ya seçin**.
3. Zip dosyası indir

Alternatif yol:

1. Cihaz **sayfasının** yanıt eylemleri bölümünden İşlem merkezi'ne tıklayın.

    ![İşlem merkezi düğmesinin resmi.](images/action-center-package-collection.png)

2. İşlem merkezi uçarak dışarı doğru, zip dosyasını **indirmek için Kullanılabilir** paket koleksiyonu paketi'ne tıklayın.

    ![Paketi indir düğmesinin resmi.](images/collect-package.png)

Paket aşağıdaki klasörleri içerir:

<br>

****

|Klasör|Açıklama|
|---|---|
|Otomatik çalıştır|Her biri, cihazda saldırganın kalıcılığını belirlemeye yardımcı olmak için bilinen bir otomatik başlangıç giriş noktasının (ASEP) kayıt defterinin içeriğini temsil eden bir dosya kümesi içerir. <p> <div class="alert"><b>NOT:</b> Kayıt defteri anahtarı bulunamazsa dosya şu iletiyi içerir: "HATA: Sistem belirtilen kayıt defteri anahtarını veya değerini bulamadı."<div>|
|Yüklü programlar|Bu .CSV, yüklü programların listesini içerir ve bu program o anda cihazda nelerin yüklü olduğunu belirlemeye yardımcı olabilir. Daha fazla bilgi için bkz[. Win32_Product.](https://go.microsoft.com/fwlink/?linkid=841509)|
|Ağ bağlantıları|Bu klasör, şüpheli URL'lere, saldırganların komut ve denetimine (C&C) altyapısına, herhangi bir  eşkenar harekete veya uzak bağlantılara yönelik bağlantıların belirlenmesinde yardımcı olan bağlantı bilgileriyle ilgili bir veri noktaları kümesi içerir. <ul><li>ActiveNetConnections.txt: Protokol istatistiklerini ve geçerli TCP/IP ağ bağlantılarını görüntüler. bir işlem tarafından yapılan şüpheli bağlantıları arama özelliği sağlar.</li><li>Arp.txt: Tüm arabirimler için geçerli adres çözümleme protokolü (ARP) önbellek tablolarını görüntüler. ARP önbelleği, ağ üzerinde güvenliği tehlikeye atılmış veya dahili bir saldırıyı çalıştırmak için kullanılmış olabileceği şüpheli sistemlere sahip ağ üzerinde diğer ana bilgisayarları ortaya çıkarır.</il><li>DnsCache.txt: Hem yerel Sistem dosyasından önceden yüklenmiş girdileri hem de bilgisayar tarafından çözümlenen ad sorguları için son alınan kaynak kayıtlarını içeren DNS istemcisi çözümleyici önbelleğinin içeriğini görüntüler. Bu, şüpheli bağlantıları belirlemede yardımcı olabilir.</li><li>IpConfig.txt: Tüm bağdaştırıcılar için tam TCP/IP yapılandırmasını görüntüler. Bağdaştırıcılar, yüklü ağ bağdaştırıcıları gibi fiziksel arabirimleri veya çevirmeli bağlantılar gibi mantıksal arabirimleri temsil eder.</li><li>FirewallExecutionLog.txt pfirewall.log</li></ul><p><div class="alert"><b>NOT:</b> Pfirewall.log dosyası %windir%\system32\logfiles\firewall\pfirewall.log içinde bulunarak araştırma paketine dahil edilecektir. Güvenlik duvarı günlük dosyasını oluşturma hakkında daha fazla bilgi için bkz. Gelişmiş [Güvenlik Windows Defender Günlüğü ile Güvenlik Duvarı'nı yapılandırma](/windows/security/threat-protection/windows-firewall/configure-the-windows-firewall-log)<div>|
|Dosyaları önceden yükleme|Windows Önceden yükleme dosyaları, uygulama başlatma işlemini hızlandırmak için tasarlanmıştır. Yakın zamanda sistemde kullanılan tüm dosyaları izlemek ve silinmiş ancak yine de önceden kullanılmış olan uygulamalara yönelik izlemeleri bulmak için kullanılabilir. <ul><li>Prefetch klasörü: 'dan gelen dosyaların bir kopyasını içerir `%SystemRoot%\Prefetch`. NOT: Önceden yapılan dosyaları görüntülemek için önceden bir dosya görüntüleyicisi indirmeniz önerilir.</li><li>PrefetchFilesList.txt: Önceden kullanılmış klasörde herhangi bir kopyalama hatası olup, izlemek için  kullanıla tüm kopyalanan dosyaların listesini içerir.</li></ul>|
|İşlemler|Çalışan .CSV listeli bir dosya içerir ve cihazda çalışan geçerli işlemleri tanımlayabilme olanağı sağlar. Bu, şüpheli bir süreci ve durumunu belirlemede yararlı olabilir.|
|Zamanlanmış görevler|Otomatik .CSV çalıştıracak şekilde ayarlanmış şüpheli kodun araması için seçilen cihazda otomatik olarak gerçekleştirilen yordamları tanımlamak için gerçekleştirilen zamanlanmış görevlerin listelandığı bir dosya içerir.|
|Güvenlik olay günlüğü|Oturum açma veya oturum açma etkinliğinin kayıtlarını veya sistemin denetim ilkesi tarafından belirtilen güvenlikle ilgili diğer olayları içeren güvenlik olayı günlüğünü içerir. <p><div class="alert"><b>NOT:</b> Olay görüntüleyicisini kullanarak olay günlüğü dosyasını açın.</div>|
|Hizmetler|Hizmetleri .CSV durumları liste içeren bir dosya içerir.|
|Windows Server İleti Bloğu (SMB) oturumları|Dosyalara, yazıcılara, seri bağlantı noktalarına ve ağ üzerinde düğümler arasındaki çeşitli iletişimlere paylaşılan erişimi listeler. Bu, veri sızıntısını veya  eşkenar hareketi belirlemeye yardımcı olabilir. <p> SMBInboundSessions ve SMBOutboundSession dosyalarını içerir. <p> <div class="alert"><b>NOT:</b> Oturum (gelen veya giden) yoksa, size hiç SMB oturumu olmadığını ifade edecek bir metin dosyası elde oluruz.</div>|
|Sistem Bilgileri|Işletim SystemInformation.txt ve ağ kartları gibi sistem bilgilerini listeen bir işletim sistemi dosyası içerir.|
|Temp Dizinleri|Sistemki her kullanıcı için %Temp% içinde yer alan dosyaların liste yer alan bir metin dosyaları kümesi içerir. <p> Bu, bir saldırgan tarafından sisteme bırakılan şüpheli dosyaları izlemede yardımcı olabilir. <p> <div class="alert"><b>NOT:</b> Dosya aşağıdaki iletiyi içeriyorsa: "Sistem belirtilen yolu bulamıyor", bu kullanıcı için geçici dizin olmadığını ve bunun nedeni kullanıcının sistemde oturum açma olması olabilir.</div>|
|Kullanıcılar ve Gruplar|Her biri bir grubu ve üyelerini temsil eden dosyaların listesini sağlar.|
|WdSupportLogs|Veri MpCmdRunLog.txt sağlar MPSupportFiles.cab  <p> <div class="alert"><b>NOT:</b> Bu klasör yalnızca Şubat 2020 güncelleştirme Windows 10 veya daha yeni yüklendikten sonra, 1709 veya sonraki sürümlerde oluşturulur: <ul><li>Win10 1709 (RS3) Derlemesi 16299.1717: [KB4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816)</li><li>Win10 1803 (RS4) Derleme 17134.1345: [KB4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795)</li><li>Win10 1809 (RS5) Derlemesi 17763.1075: [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818)</li><li>Win10 1903/1909 (19h1/19h2) Derlemeleri 18362.693 ve 18363.693: [KB4535996](https://support.microsoft.com/help/4535996/windows-10-update-kb4535996)</li></ul> </div>|
|CollectionSummaryReport.xls|Bu dosya araştırma paketi koleksiyonunun özetidir; veri noktalarının listesini, verileri ayıklamak için kullanılan komutu, yürütme durumunu ve hata varsa hata kodunu içerir. Bu raporu kullanarak paketin tüm beklenen verileri dahil olup olduğunu izleyebilir ve hata olupbizli olduğunu tanımlayabilirsiniz.|
|

## <a name="run-microsoft-defender-antivirus-scan-on-devices"></a>Cihazlarda Microsoft Defender Virüsten Koruma taramayı çalıştır

Araştırma ve yanıt işleminin bir parçası olarak, güvenliği tehlikeye atılmış bir cihazda var olan kötü amaçlı yazılımları tanımlamak ve düzeltmek için virüsten koruma taraması başlatabilirsiniz.

>[!IMPORTANT]
>- Bu eylem şu anda macOS ve Linux için desteklenmiyor. Eylemi çalıştırmak için canlı yanıtı kullanın. Canlı yanıt hakkında daha fazla bilgi için bkz [. Canlı yanıtı kullanan cihazlardaki varlıkları araştırma](live-response.md)
>- Microsoft Defender AV Microsoft Defender Virüsten Koruma etkin virüsten koruma çözümü olsun ya da değildir, diğer virüsten koruma çözümleriyle birlikte bir bilgisayar (Microsoft Defender AV) taraması da çalıştırabilirsiniz. Microsoft Defender AV Pasif modunda olabilir. Daha fazla bilgi için uyumluluk [Microsoft Defender Virüsten Koruma bakın](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-compatibility).

Virüsten **koruma taraması** çalıştır'ı seçtikten sonra, çalıştırmak istediğiniz tarama türünü seçin (hızlı veya tam) ve taramayı onaylamadan önce bir açıklama ekleyin.

![Hızlı taramayı veya tam taramayı seçerek açıklama eklemek için bildirim görüntüsü.](images/run-antivirus.png)

İşlem merkezi tarama bilgilerini gösterir ve cihaz zaman çizelgesi, cihaza bir tarama eyleminin gönderl olduğunu yansıtan yeni bir olay içerir. Microsoft Defender AV uyarıları, tarama sırasında ortaya gelen tüm algılamaları yansıtacak.

> [!NOTE]
> Uç nokta için Defender yanıt eylemi kullanılarak bir tarama tetiklenirken, Microsoft Defender virüsten koruma 'ScanAvgCPULoadFactor' değeri yine uygulanır ve taramanın CPU etkisini sınırlar.
>
> ScanAvgCPULoadFactor yapılandırılmazsa, varsayılan değer tarama sırasında %50 maksimum CPU yükü sınırıdır.
>
> Daha fazla bilgi için bkz. [configure-advanced-scan-types-microsoft-defender-antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/configure-advanced-scan-types-microsoft-defender-antivirus).

## <a name="restrict-app-execution"></a>Uygulama yürütmeyi kısıtla

Kötü amaçlı işlemleri durdurarak saldırı eklemeye ek olarak, cihazı kilitleyip kötü amaçlı olabilecek olası programların sonraki girişimlerini de önebilirsiniz.

>[!IMPORTANT]
> - Bu eylem, 11. Windows 10, sürüm 1709 veya Windows sonraki sürümler ve Windows Server 2016. 
> - Bu özellik, bu özelliğin kullanımı sizin için Microsoft Defender Virüsten Koruma.
> - Bu eylemin, Uygulama Denetimi Windows Defender ilke biçimlerini ve imzalama gereksinimlerini karşılaması gerekir. Daha fazla bilgi için bkz[. Kod bütünlüğü ilke biçimleri ve imza).](/windows/security/threat-protection/windows-defender-application-control/use-code-signing-to-simplify-application-control-for-classic-windows-applications)

Bir uygulamanın çalışmasına kısıtlamak için, yalnızca dosyaların Microsoft tarafından verilen bir sertifikayla imzalanmış olması gerekir ve bu dosyaların çalışmasına izin veren bir kod bütünlüğü ilkesi uygulanır. Bu kısıtlama yöntemi, güvenliği tehlikeye atılmış cihazları denetimi altına alan ve kötü amaçlı başka etkinlikler gerçekleştiren bir saldırganı önlemeye yardımcı olabilir.

> [!NOTE]
> Uygulamaların kısıtlamalarını geri çevirebilir ve her an çalıştırabilirsiniz. Cihaz sayfasındaki düğme, Uygulama **kısıtlamalarını kaldır** olarak değişir ve siz de uygulama yürütmeyi kısıtlamayla aynı adımları atabilirsiniz.

Cihaz sayfasında uygulama **yürütmeyi kısıtla'yi** seçtikten sonra bir açıklama yazın ve Onayla'ya **tıklayın**. İşlem merkezi tarama bilgilerini gösterir ve cihaz zaman çizelgesi yeni bir olay içerir.

![Uygulama kısıtlama bildiriminin resmi.](images/restrict-app-execution.png)

### <a name="notification-on-device-user"></a>Cihaz kullanıcısı bildirimi

Bir uygulama kısıtlanmışsa, kullanıcıya bir uygulamanın çalıştırıla kısıtlamalı olduğunu bildirmek için aşağıdaki bildirim görüntülenir:

![Uygulama kısıtlama resmi.](images/atp-app-restriction.png)

>[!NOTE]
>Bu bildirim R2'de Windows Server 2016 Windows Server 2012 kullanılamaz.

## <a name="isolate-devices-from-the-network"></a>Cihazları ağdan ayırma

Saldırının önem düzeyine ve cihazın duyarlılığına bağlı olarak, cihazı ağdan ayırmak iyi bir yol olabilir. Bu eylem, saldırganin güvenliği tehlikeye giren cihazı denetlemesini ve veri sızıntısı ve  eşkenar hareket gibi başka etkinlikler gerçekleştirmesini önlemeye yardımcı olabilir.

>[!IMPORTANT]
>- Bu eylem şu anda macOS ve Linux için desteklenmiyor. Eylemi çalıştırmak için canlı yanıtı kullanın. Canlı yanıt hakkında daha fazla bilgi için bkz [. Canlı yanıtı kullanan cihazlardaki varlıkları araştırma](live-response.md)
>- Windows 10, sürüm 1703, Windows 11, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 ve Windows Server 2022 cihazlarında tam yalıtım kullanılabilir.
>- Seçmeli yalıtım; 11. Windows 10 sürüm 1709 ve sonraki sürümlerde Windows kullanılabilir.
>- Bir cihazı yorumlarken yalnızca belirli işlemlere ve hedeflere izin verilir. Bu nedenle, tam VPN hedeflerinin arkasındaki cihazlar cihaz yalıtılmış halde uç nokta için Microsoft Defender bulut hizmetine ulaşamayabilecektir. Uç Nokta için Microsoft Defender ve bulut tabanlı korumayla ilgili Microsoft Defender Virüsten Koruma bir VPN kullanılması önerilir.

Bu cihaz yalıtım özelliği, güvenliği ihlal edilmiş cihazın ağ bağlantısını keserken, uç nokta için Defender hizmetinin bağlantısını da keser ve bu da cihazı izlemeye devam eder.

Bir Windows 10 sürüm 1709 veya sonraki bir sürümde, ağ yalıtım düzeyi üzerinde daha fazla denetime sahip oluruz. Ayrıca, bağlantı Outlook, Microsoft Teams ve Skype Kurumsal 'Seçmeli Yalıtım' gibi) etkinleştirmeyi seçebilirsiniz.

> [!NOTE]
> Cihazı ağa yeniden her zaman yeniden bağlanabilirsiniz. Cihaz sayfasındaki düğme, Yalıtımdan çıkar **olarak değişir ve** siz de cihazı ayırmayla aynı adımları alırsınız.

Cihaz sayfasında Cihazı **yalıt'ı** seçtikten sonra bir açıklama yazın ve Onayla'ya **tıklayın**. İşlem merkezi tarama bilgilerini gösterir ve cihaz zaman çizelgesi yeni bir olay içerir.

![Cihazı yalıtmak resmi.](images/isolate-device.png)

> [!NOTE]
> Cihaz ağdan yalıtılmış olsa bile Uç Nokta için Defender hizmetine bağlı kalır. Outlook ve Skype Kurumsal iletişimini etkinleştirmeyi seçtiysanız, cihaz yalıtılmışken kullanıcıya iletişim kurabilirsiniz.

### <a name="notification-on-device-user"></a>Cihaz kullanıcısı bildirimi

Cihaz yalıtılmış olduğunda, kullanıcıya cihazın ağdan yalıtılmış olduğunu bildirmek için aşağıdaki bildirim görüntülenir:

![Ağ bağlantısı yok resmi.](images/atp-notification-isolate.png)

## <a name="consult-a-threat-expert"></a>Tehdit uzmanına danışın

Güvenliği tehlikeye atılmış veya zaten tehlikeye atılmış bir cihazla ilgili daha fazla içgörü için Microsoft tehdit uzmanına başvurabilirsiniz. Microsoft Tehdit Uzmanları ve doğru yanıt için e-Microsoft 365 Defender doğrudan e-postanın içinde meşgul olabilir. Uzmanlar yalnızca güvenliği tehlikeye atabilecek bir cihazla ilgili içgörüler sağlamakla birlikte karmaşık tehditleri, size alınan hedefli saldırı bildirimlerini daha iyi anlamak veya uyarılar hakkında daha fazla bilgiye veya portal panonda gördüğünüz bir tehdit zekası bağlamına ihtiyacınız olup olmadığını daha iyi anlamak için sağlar.

Ayrıntılar [için Bkz. Microsoft Tehdit Uzmanına](/microsoft-365/security/defender-endpoint/configure-microsoft-threat-experts#consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization) Danışma.

## <a name="check-activity-details-in-action-center"></a>İşlem merkezinde etkinlik ayrıntılarını denetleme

İşlem **merkezi** , bir cihaz veya dosya üzerinde yapılan işlemlerle ilgili bilgi sağlar. Aşağıdaki ayrıntıları görüntüebilirsiniz:

- Araştırma paketi koleksiyonu
- Virüsten koruma taraması
- Uygulama kısıtlaması
- Cihaz yalıtlığı

Gönderme tarihi/saati, gönderilen kullanıcı ve eylem başarılı olursa ya da başarısız olursa, diğer tüm ilgili ayrıntılar da gösterilir.

![Bilgili işlem merkezi görüntüsü.](images/action-center-details.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Dosyada yanıt eylemleri gerçekleştirin](respond-file-alerts.md)
- [Uç Nokta Planı 1 için Microsoft Defender'da el ile yanıt eylemleri](defender-endpoint-plan-1.md#manual-response-actions)
- [Rapor yanlışlığı](/microsoft-365/security/defender-endpoint/tvm-security-recommendation#report-inaccuracy)
