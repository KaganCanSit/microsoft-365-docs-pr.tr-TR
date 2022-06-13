---
title: Uç Nokta için Microsoft Defender'da bir cihazda yanıt eylemleri gerçekleştirme
description: Cihazlarda yalıtma, araştırma paketi toplama, etiketleri yönetme, av taraması çalıştırma ve uygulama yürütmeyi kısıtlama gibi yanıt eylemleri gerçekleştirin.
keywords: yanıt verme, yalıtma, cihazı yalıtma, araştırma paketini toplama, işlem merkezi, etiketleri kısıtlama, yönetme, av tarama, uygulamayı kısıtlama
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
ms.openlocfilehash: c104b7fefae6ad02c9fb46b7d21522c21a2f6895
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014618"
---
# <a name="take-response-actions-on-a-device"></a>Cihazda yanıt eylemleri gerçekleştirin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1 ve 2](defender-endpoint-plan-1-2.md)
- [İş için Microsoft Defender](/microsoft-365/security/defender-business/mdb-overview)

[!INCLUDE [Prerelease information](../../includes/prerelease.md)]

Cihazları yalıtarak veya bir araştırma paketi toplayarak algılanan saldırılara hızla yanıt verin. Cihazlarda işlem yaptıktan sonra İşlem merkezinde etkinlik ayrıntılarını de kontrol edebilirsiniz.

Yanıt eylemleri belirli bir cihaz sayfasının üst kısmında çalışır ve şunları içerir:

- Etiketleri yönetin
- Otomatik Araştırma Başlatma
- Canlı Yanıt Oturumu Başlat
- Soruşturma paketini toplayın
- Antivirüs taraması başlat
- Uygulama yürütmeyi kısıtlayın
- Cihazı yalıtma
- Cihazı içer
- Tehdit uzmanına danışın
- İşlem merkezi

[![Yanıt eylemlerinin görüntüsü.](images/response-actions.png)](images/response-actions.png#lightbox)

> [!IMPORTANT]
> [Uç Nokta Planı 1](defender-endpoint-plan-1.md) ve [İş için Microsoft Defender](../defender-business/mdb-overview.md) için Defender yalnızca aşağıdaki el ile yanıt eylemlerini içerir:
> - Antivirüs taraması başlat
> - Cihazı yalıtma
> - Dosyayı durdurma ve karantinaya al
> - Bir dosyayı engellemek veya dosyaya izin vermek için bir gösterge ekleyin Aboneliğinizin bu makalede açıklanan tüm yanıt eylemlerine sahip olması için Uç Nokta için Defender Plan 2'yi içermesi gerekir.

 Cihaz sayfalarını aşağıdaki görünümlerden herhangi birinden bulabilirsiniz:

- **Güvenlik işlemleri panosu** - Risk altındaki cihazlar kartından bir cihaz adı seçin.
- **Uyarıları kuyruğu** - Uyarılar kuyruğundan cihaz simgesinin yanındaki cihaz adını seçin.
- **Cihazlar listesi - Cihaz** listesinden cihaz adının başlığını seçin.
- **Arama kutusu** - Açılan menüden Cihaz'ı seçin ve cihaz adını girin.

> [!IMPORTANT]
> - Bu yanıt eylemleri yalnızca Windows 10, sürüm 1703 veya üzeri, Windows 11, Windows Server 2019 ve Windows Server 2022'de bulunan cihazlarda kullanılabilir.
> - Windows olmayan platformlar için yanıt özellikleri (Cihaz yalıtımı gibi) üçüncü taraf özelliklerine bağlıdır.
> - Microsoft birinci taraf aracıları için, en düşük işletim sistemi gereksinimleri için her bir özelliğin altındaki "daha fazla bilgi" bağlantısına bakın.

## <a name="manage-tags"></a>Etiketleri yönetin

Mantıksal grup ilişkisi oluşturmak için etiketleri ekleyin veya yönetin. Cihaz etiketleri, ağın uygun şekilde eşlenmesini destekleyerek bağlamı yakalamak için farklı etiketler eklemenize ve bir olayın parçası olarak dinamik liste oluşturmayı etkinleştirmenizi sağlar.

Cihaz etiketleme hakkında daha fazla bilgi için bkz. [Cihaz etiketlerini oluşturma ve yönetme](machine-tags.md).

## <a name="initiate-automated-investigation"></a>Otomatik Araştırma Başlatma

Gerekirse cihazda yeni bir genel amaçlı otomatik araştırma başlatabilirsiniz. Bir araştırma çalışırken, bu araştırma tamamlanana kadar cihazdan oluşturulan diğer tüm uyarılar devam eden otomatik araştırmaya eklenir. Ayrıca, aynı tehdit diğer cihazlarda görülürse, bu cihazlar araştırmaya eklenir.

Otomatik araştırmalarla ilgili daha fazla bilgi için bkz. [Otomatik araştırmalara genel bakış](automated-investigations.md).

## <a name="initiate-live-response-session"></a>Canlı yanıt başlatma Oturumu

Canlı yanıt, uzak kabuk bağlantısı kullanarak bir cihaza anında erişmenizi sağlayan bir özelliktir. Bu size ayrıntılı araştırma çalışmaları yapma ve belirlenen tehditleri anında gerçek zamanlı olarak içermesi için anında yanıt eylemleri gerçekleştirme gücü verir.

Canlı yanıt, adli veri toplamanıza, betik çalıştırmanıza, analiz için şüpheli varlıklar göndermenize, tehditleri düzeltmenize ve yeni ortaya çıkan tehditleri proaktif olarak avlamanıza olanak tanıyarak araştırmalarını geliştirmek için tasarlanmıştır.

Canlı yanıt hakkında daha fazla bilgi için bkz [. Canlı yanıt kullanarak cihazlarda varlıkları araştırma](live-response.md).

## <a name="collect-investigation-package-from-devices"></a>Cihazlardan araştırma paketi toplama

Araştırma veya yanıt sürecinin bir parçası olarak bir cihazdan araştırma paketi toplayabilirsiniz. Araştırma paketini toplayarak cihazın geçerli durumunu belirleyebilir ve saldırgan tarafından kullanılan araç ve teknikleri daha iyi anlayabilirsiniz.

> [!IMPORTANT]
> Bu eylemler şu anda macOS veya Linux çalıştıran cihazlar için desteklenmiyor. Eylemi çalıştırmak için canlı yanıtı kullanın. Canlı yanıt hakkında daha fazla bilgi için bkz [. Canlı yanıt kullanarak cihazlarda varlıkları araştırma](live-response.md)

Paketi indirmek (Zip dosyası) ve bir cihazda gerçekleşen olayları araştırmak için

1. Cihaz sayfasının üst kısmındaki yanıt eylemleri satırından **Araştırma paketini topla'ya** tıklayın.

2. Metin kutusunda bu eylemi neden gerçekleştirmek istediğinizi belirtin. **Onayla'yı** seçin.

3. Zip dosyası indirilecek

Alternatif yol:

1. Cihaz sayfasının yanıt eylemleri bölümünden **İşlem merkezi'ni** seçin.

   :::image type="content" source="images/action-center-package-collection.png" alt-text="İşlem merkezi seçeneği" lightbox="images/action-center-package-collection.png":::

2. İşlem merkezi açılır penceresinde Zip dosyasını indirmek için **Paket koleksiyonu paketi kullanılabilir'i** seçin.

   :::image type="content" source="images/collect-package.png" alt-text="Paket indirme seçeneği" lightbox="images/collect-package.png":::

Paket aşağıdaki klasörleri içerir:

|Klasör|Açıklama|
|---|---|
|Autoruns|Her biri, saldırganın cihazdaki kalıcılığını belirlemeye yardımcı olmak için bilinen bir otomatik başlatma giriş noktasının (ASEP) kayıt defterinin içeriğini temsil eden bir dosya kümesi içerir. <p> <div class="alert"><b>NOT:</b> Kayıt defteri anahtarı bulunmazsa, dosya şu iletiyi içerir: "HATA: Sistem belirtilen kayıt defteri anahtarını veya değerini bulamadı."<div>|
|Yüklü programlar|Bu .CSV dosyası, cihazda şu anda yüklü olanları tanımlamaya yardımcı olabilecek yüklü programların listesini içerir. Daha fazla bilgi için bkz. [Win32_Product sınıfı](https://go.microsoft.com/fwlink/?linkid=841509).|
|Ağ bağlantıları|Bu klasör şüpheli URL'lere bağlantıyı, saldırganın komut ve denetimi (C&C) altyapısını, yanal hareketleri veya uzak bağlantıları tanımlamaya yardımcı olabilecek bağlantı bilgileriyle ilgili bir dizi veri noktası içerir. <ul><li>ActiveNetConnections.txt: Protokol istatistiklerini ve geçerli TCP/IP ağ bağlantılarını görüntüler. Bir işlem tarafından yapılan şüpheli bağlantıyı arama olanağı sağlar.</li><li>Arp.txt: Tüm arabirimler için geçerli adres çözümleme protokolü (ARP) önbellek tablolarını görüntüler. ARP önbelleği, ağdaki güvenliği aşılmış veya ağdaki bir iç saldırı çalıştırmak için kullanılmış olabilecek şüpheli sistemlere sahip diğer konakları gösterebilir.</il><li>DnsCache.txt: Yerel Hosts dosyasından önceden yüklenmiş girişleri ve bilgisayar tarafından çözümlenen ad sorguları için yakın zamanda alınan kaynak kayıtlarını içeren DNS istemci çözümleyici önbelleğinin içeriğini görüntüler. Bu, şüpheli bağlantıları tanımlamaya yardımcı olabilir.</li><li>IpConfig.txt: Tüm bağdaştırıcılar için tam TCP/IP yapılandırmasını görüntüler. Bağdaştırıcılar, yüklü ağ bağdaştırıcıları gibi fiziksel arabirimleri veya çevirmeli bağlantılar gibi mantıksal arabirimleri temsil edebilir.</li><li>FirewallExecutionLog.txt ve pfirewall.log</li></ul><p><div class="alert"><b>NOT:</b> pfirewall.log dosyası %windir%\system32\logfiles\firewall\pfirewall.log içinde bulunmalıdır, bu nedenle araştırma paketine eklenecektir. Güvenlik duvarı günlük dosyasını oluşturma hakkında daha fazla bilgi için bkz[. Gelişmiş Güvenlik Günlüğü ile Windows Defender Güvenlik Duvarı yapılandırma](/windows/security/threat-protection/windows-firewall/configure-the-windows-firewall-log)<div>|
|Dosyaları önceden yükleme|Windows Prefetch dosyaları, uygulama başlatma işlemini hızlandırmak için tasarlanmıştır. Bu, sistemde son kullanılan tüm dosyaları izlemek ve silinmiş olsa da önceden dosya listesinde bulunabilen uygulamaların izlemelerini bulmak için kullanılabilir. <ul><li>Prefetch klasörü: dosyasından `%SystemRoot%\Prefetch`ön yükleme dosyalarının bir kopyasını içerir. NOT: Prefetch dosyalarını görüntülemek için bir prefetch dosya görüntüleyicisi indirmeniz önerilir.</li><li>PrefetchFilesList.txt: Prefetch klasöründe kopyalama hatası olup olmadığını izlemek için kullanılabilecek tüm kopyalanan dosyaların listesini içerir.</li></ul>|
|Süreç|Çalışan işlemleri listeleyen bir .CSV dosyası içerir ve cihazda çalışan geçerli işlemleri tanımlama olanağı sağlar. Bu, şüpheli bir işlemi ve durumunu tanımlarken yararlı olabilir.|
|Zamanlanmış görevler|Otomatik olarak çalışacak şekilde ayarlanmış şüpheli kodu aramak üzere seçilen bir cihazda otomatik olarak gerçekleştirilen yordamları tanımlamak için kullanılabilen zamanlanmış görevlerin listelendiği .CSV bir dosya içerir.|
|Güvenlik olay günlüğü|Oturum açma veya oturumu kapatma etkinliğinin kayıtlarını veya sistemin denetim ilkesi tarafından belirtilen güvenlikle ilgili diğer olayları içeren güvenlik olay günlüğünü içerir. <p><div class="alert"><b>NOT:</b> Olay görüntüleyicisini kullanarak olay günlüğü dosyasını açın.</div>|
|Hizmetleri|Hizmetleri ve durumlarını listeleyen bir .CSV dosyası içerir.|
|Windows Sunucu İleti Bloğu (SMB) oturumları|Dosyalara, yazıcılara ve seri bağlantı noktalarına paylaşılan erişimi ve ağdaki düğümler arasındaki çeşitli iletişimleri listeler. Bu, veri sızdırmayı veya yanal hareketi tanımlamaya yardımcı olabilir. <p> SMBInboundSessions ve SMBOutboundSession dosyalarını içerir. <p> <div class="alert"><b>NOT:</b> Hiçbir oturum (gelen veya giden) yoksa, hiçbir SMB oturumu bulunamadığını belirten bir metin dosyası alırsınız.</div>|
|Sistem Bilgileri|İşletim sistemi sürümü ve ağ kartları gibi sistem bilgilerini listeleyen bir SystemInformation.txt dosyası içerir.|
|Geçici Dizinler|Sistemdeki her kullanıcı için %Temp% içinde bulunan dosyaları listeleyen bir dizi metin dosyası içerir. <p> Bu, saldırganın sisteme düşürmüş olabileceği şüpheli dosyaları izlemeye yardımcı olabilir. <p> <div class="alert"><b>NOT:</b> Dosya şu iletiyi içeriyorsa: "Sistem belirtilen yolu bulamıyor", bu kullanıcı için geçici dizin olmadığı anlamına gelir ve bunun nedeni kullanıcının sistemde oturum açmamış olması olabilir.</div>|
|Kullanıcılar ve Gruplar|Her birinin bir grubu ve üyelerini temsil eden dosyaların listesini sağlar.|
|WdSupportLogs|MpCmdRunLog.txt ve MPSupportFiles.cab sağlar  <p> <div class="alert"><b>NOT:</b> Bu klasör yalnızca şubat 2020 güncelleştirme paketi veya daha yeni yüklenmiş Windows 10, sürüm 1709 veya sonraki sürümlerde oluşturulur: <ul><li>Win10 1709 (RS3) Derlemesi 16299.1717: [KB4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816)</li><li>Win10 1803 (RS4) Derlemesi 17134.1345: [KB4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795)</li><li>Win10 1809 (RS5) Derlemesi 17763.1075: [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818)</li><li>Win10 1903/1909 (19h1/19h2) Derlemeleri 18362.693 ve 18363.693: [KB4535996](https://support.microsoft.com/help/4535996/windows-10-update-kb4535996)</li></ul> </div>|
|CollectionSummaryReport.xls|Bu dosya araştırma paketi koleksiyonunun bir özetidir, veri noktalarının listesini, verileri ayıklamak için kullanılan komutu, yürütme durumunu ve hata varsa hata kodunu içerir. Paketin beklenen tüm verileri içerip içermediğini izlemek ve herhangi bir hata olup olmadığını belirlemek için bu raporu kullanabilirsiniz.|
|

## <a name="run-microsoft-defender-antivirus-scan-on-devices"></a>Cihazlarda Microsoft Defender Virüsten Koruma taraması çalıştırma

Araştırma veya yanıt sürecinin bir parçası olarak, güvenliği aşılmış bir cihazda bulunabilecek kötü amaçlı yazılımları tanımlamaya ve düzeltmeye yardımcı olmak için uzaktan bir virüsten koruma taraması başlatabilirsiniz.

> [!IMPORTANT]
> - Bu eylem şu anda macOS ve Linux için desteklenmiyor. Eylemi çalıştırmak için canlı yanıtı kullanın. Canlı yanıt hakkında daha fazla bilgi için bkz [. Canlı yanıt kullanarak cihazlarda varlıkları araştırma](live-response.md)
> - Microsoft Defender Virüsten Koruma (Microsoft Defender AV) taraması, Microsoft Defender AV'nin etkin virüsten koruma çözümü olup olmadığı fark etmeksizin diğer virüsten koruma çözümleriyle birlikte çalıştırılabilir. Microsoft Defender AV Pasif modda olabilir. Daha fazla bilgi için bkz. [uyumluluk Microsoft Defender Virüsten Koruma](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-compatibility).

**Virüsten koruma taraması çalıştır'ı** seçtikten sonra, çalıştırmak istediğiniz tarama türünü seçin (hızlı veya tam) ve taramayı onaylamadan önce bir açıklama ekleyin.

:::image type="content" source="images/run-antivirus.png" alt-text="Hızlı tarama veya tam tarama seçme ve açıklama ekleme bildirimi" lightbox="images/run-antivirus.png":::

İşlem merkezi tarama bilgilerini gösterir ve cihaz zaman çizelgesinde cihazda bir tarama eylemi gönderildiğini yansıtan yeni bir olay yer alır. Microsoft Defender AV uyarıları, tarama sırasında ortaya çıkacak tüm algılamaları yansıtır.

> [!NOTE]
> Uç Nokta için Defender yanıt eylemini kullanarak tarama tetiklerken, Microsoft Defender virüsten koruma 'ScanAvgCPULoadFactor' değeri yine de geçerli olur ve taramanın CPU etkisini sınırlar.
> ScanAvgCPULoadFactor yapılandırılmamışsa, varsayılan değer tarama sırasında %50 maksimum CPU yükü sınırıdır.
> Daha fazla bilgi için bkz. [configure-advanced-scan-types-microsoft-defender-antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/configure-advanced-scan-types-microsoft-defender-antivirus).

## <a name="restrict-app-execution"></a>Uygulama yürütmeyi kısıtlayın

Kötü amaçlı işlemleri durdurarak bir saldırı içermenin yanı sıra, bir cihazı kilitleyebilir ve kötü amaçlı olabilecek programların sonraki denemelerinin çalışmasını engelleyebilirsiniz.

> [!IMPORTANT]
> - Bu eylem Windows 10, sürüm 1709 veya üzeri, Windows 11 ve Windows Server 2019 veya sonraki sürümlerde bulunan cihazlarda kullanılabilir. 
> - Kuruluşunuz Microsoft Defender Virüsten Koruma kullanıyorsa bu özellik kullanılabilir.
> - Bu eylemin Windows Defender Uygulama Denetimi kod bütünlüğü ilkesi biçimlerini ve imzalama gereksinimlerini karşılaması gerekir. Daha fazla bilgi için bkz [. Kod bütünlüğü ilkesi biçimleri ve imzalama](/windows/security/threat-protection/windows-defender-application-control/use-code-signing-to-simplify-application-control-for-classic-windows-applications)).

Bir uygulamanın çalışmasını kısıtlamak için, yalnızca Microsoft tarafından verilen bir sertifika tarafından imzalanan dosyaların çalışmasına izin veren bir kod bütünlüğü ilkesi uygulanır. Bu kısıtlama yöntemi, saldırganın güvenliği aşılmış cihazları denetlemesini ve daha fazla kötü amaçlı etkinlik gerçekleştirmesini önlemeye yardımcı olabilir.

> [!NOTE]
> Uygulamaların çalışmasının kısıtlamasını istediğiniz zaman tersine çevirebilirsiniz. Cihaz sayfasındaki düğme, **Uygulama kısıtlamalarını kaldır** olarak değişir ve uygulama yürütmeyi kısıtlamakla aynı adımları uygularsınız.

Cihaz sayfasında **Uygulama yürütmeyi kısıtla'yı** seçtikten sonra bir açıklama yazın ve **Onayla'yı** seçin. İşlem merkezi tarama bilgilerini gösterir ve cihaz zaman çizelgesi yeni bir olay içerir.

:::image type="content" source="images/restrict-app-execution.png" alt-text="Uygulama kısıtlama bildirimi" lightbox="images/restrict-app-execution.png":::

### <a name="notification-on-device-user"></a>Cihaz kullanıcıda bildirim

Bir uygulama kısıtlandığında, kullanıcıya bir uygulamanın çalışmasının kısıtlandığını bildirmek için aşağıdaki bildirim görüntülenir:

:::image type="content" source="images/atp-app-restriction.png" alt-text="Uygulama kısıtlama iletisi" lightbox="images/atp-app-restriction.png":::

> [!NOTE]
> Bildirim Windows Server 2016 ve Windows Server 2012 R2'de kullanılamaz.

## <a name="isolate-devices-from-the-network"></a>Cihazları ağdan ayırın

Saldırının önem derecesine ve cihazın duyarlılığına bağlı olarak, cihazı ağdan yalıtmak isteyebilirsiniz. Bu eylem, saldırganın güvenliği aşılmış cihazı denetlemesini ve veri sızdırma ve yanal hareket gibi başka etkinlikler gerçekleştirmesini önlemeye yardımcı olabilir.

> [!IMPORTANT]
> - Cihazları ağdan yalıtma şu anda macOS veya Linux çalıştıran cihazlar için desteklenmiyor. Eylemi çalıştırmak için canlı yanıtı kullanın. Canlı yanıt hakkında daha fazla bilgi için bkz [. Canlı yanıt kullanarak cihazlarda varlıkları araştırma](live-response.md).
> - Windows 11, Windows 10, sürüm 1703 veya üzeri, Windows Server 2022, Windows Server 2019 ve Windows Server 2016 çalıştıran cihazlarda tam yalıtım kullanılabilir.
> - Seçmeli yalıtım, Windows 10, sürüm 1709 veya üzeri ve Windows 11 çalıştıran cihazlar için kullanılabilir.
> - Bir cihazı yalıtırken yalnızca belirli işlemlere ve hedeflere izin verilir. Bu nedenle, tam VPN tünelinin arkasındaki cihazlar, cihaz yalıtıldıktan sonra Uç Nokta için Microsoft Defender bulut hizmetine erişemez. bulut tabanlı korumayla ilgili trafiği Uç Nokta için Microsoft Defender ve Microsoft Defender Virüsten Koruma için bölünmüş tünel VPN kullanmanızı öneririz.

Bu cihaz yalıtımı özelliği, cihazı izlemeye devam eden Uç Nokta için Defender hizmetine bağlantıyı korurken güvenliği aşılmış cihazın ağ bağlantısını keser.

Windows 10, sürüm 1709 veya sonraki sürümlerde ağ yalıtım düzeyi üzerinde daha fazla denetime sahip olursunuz. Ayrıca Outlook, Microsoft Teams ve Skype Kurumsal bağlantısını (yani 'Seçmeli Yalıtım' olarak) etkinleştirmeyi de seçebilirsiniz.

> [!NOTE]
> İstediğiniz zaman cihazı ağa yeniden bağlayabilirsiniz. Cihaz sayfasındaki düğme **Yalıtımdan çıkar** olarak değişir ve ardından cihazı yalıtma ile aynı adımları uygularsınız.

**Cihaz sayfasında Cihazı yalıt'ı** seçtikten sonra bir açıklama yazın ve **Onayla'yı** seçin. İşlem merkezi tarama bilgilerini gösterir ve cihaz zaman çizelgesi yeni bir olay içerir.

:::image type="content" source="images/isolate-device.png" alt-text="Yalıtılmış cihaz ayrıntıları sayfası" lightbox="images/isolate-device.png":::

> [!NOTE]
> Cihaz ağdan yalıtılmış olsa bile Uç Nokta için Defender hizmetine bağlı kalır. Outlook ve Skype Kurumsal iletişimi etkinleştirmeyi seçtiyseniz cihaz yalıtılmış durumdayken kullanıcıyla iletişim kurabilirsiniz.

### <a name="notification-on-device-user"></a>Cihaz kullanıcıda bildirim

Bir cihaz yalıtılırken, kullanıcıya cihazın ağdan yalıtıldığını bildirmek için aşağıdaki bildirim görüntülenir:

:::image type="content" source="images/atp-notification-isolate.png" alt-text="Ağ bağlantısı yok iletisi" lightbox="images/atp-notification-isolate.png":::

## <a name="contain-devices-from-the-network"></a>Ağdaki cihazları içerin

Gizliliği tehlikeye girmiş veya risk altında olabilecek yönetilmeyen bir cihaz tanımladığınızda, bu cihazı ağdan içermek isteyebilirsiniz. Bir cihaz içerdiğinizde eklenen Uç Nokta için Microsoft Defender cihaz, bu cihazla gelen ve giden iletişimi engeller. Bu eylem, güvenlik operasyonları analisti güvenliği aşılmış cihazdaki tehdidi bulur, tanımlar ve düzeltirken komşu cihazların gizliliğinin tehlikeye girmesini önlemeye yardımcı olabilir.

> [!NOTE]
> Eklenen Uç Nokta için Microsoft Defender Windows 10 ve Windows Server 2019+ cihazlarda 'kapsanan' bir cihazla gelen ve giden iletişimi engelleme desteklenir.

### <a name="how-to-contain-a-device"></a>Cihaz içerme

1. **Cihaz envanteri** sayfasına gidin ve içerecek cihazı seçin.

2. Cihaz açılır öğesindeki eylemler menüsünden Cihazı **içer'i** seçin.

:::image type="content" alt-text="Cihaz içer açılan iletisinin ekran görüntüsü." source="../../media/defender-endpoint/contain_device.png" lightbox="../../media/defender-endpoint/contain_device.png":::

3. Cihazı içer açılan penceresinde bir açıklama yazın ve **Onayla'yı** seçin.

:::image type="content" alt-text="Cihaz içer menü öğesinin ekran görüntüsü." source="../../media/defender-endpoint/contain_device_popup.png" lightbox="../../media/defender-endpoint/contain_device_popup.png":::

### <a name="contain-a-device-from-the-device-page"></a>Cihaz sayfasından bir cihaz içerme

Bir cihaz, eylem çubuğundan **Cihazı içer'i** seçerek cihaz sayfasından da bulunabilir:

:::image type="content" alt-text="Cihaz sayfasındaki cihaz içer menü öğesinin ekran görüntüsü." source="../../media/defender-endpoint/contain_device_page.png" lightbox="../../media/defender-endpoint/contain_device_page.png":::

> [!NOTE]
> Yeni eklenen bir cihazla ilgili ayrıntıların eklenen Uç Nokta için Microsoft Defender cihaza ulaşması 5 dakika kadar sürebilir.

> [!IMPORTANT]
> - Kapsanan bir cihaz IP adresini değiştirirse, eklenen tüm Uç Nokta için Microsoft Defender cihazlar bunu tanır ve yeni IP adresiyle iletişimi engellemeye başlar. Özgün IP adresi artık engellenmez (Bu değişiklikleri görmek 5 dakika kadar sürebilir).  
> - Kapsanan cihazın IP'sinin ağdaki başka bir cihaz tarafından kullanıldığı durumlarda, cihazı içerirken gelişmiş avcılık bağlantısıyla (önceden doldurulmuş sorgu ile) bir uyarı olacaktır. Bu, cihazı içermeye devam etmek istiyorsanız bilinçli bir karar vermenize yardımcı olmak için aynı IP'yi kullanan diğer cihazlara görünürlük sağlar.
> - Kapsanan cihazın bir ağ cihazı olduğu durumlarda, bunun ağ bağlantısı sorunlarına (örneğin, varsayılan ağ geçidi olarak davranan bir yönlendirici içeren) neden olabileceğini belirten bir iletiyle birlikte bir uyarı görüntülenir. Bu noktada, cihazı içerip içermemeyi seçebilirsiniz.

Bir cihaz içerdikten sonra, davranış beklendiği gibi değilse Uç Nokta için Defender eklenen cihazlarda Temel Filtreleme Altyapısı (BFE) hizmetinin etkinleştirildiğini doğrulayın.

### <a name="stop-containing-a-device"></a>Cihaz içermeyi durdurma

İstediğiniz zaman cihaz içermeyi durdurabilirsiniz.

1. **Cihaz envanterinden** cihazı seçin veya cihaz sayfasını açın.

2. Eylem **menüsünden Kapsamadan serbest bırak'ı** seçin. Bu eylem, bu cihazın ağ bağlantısını geri yükler.

## <a name="consult-a-threat-expert"></a>Tehdit uzmanına danışın

Güvenliği aşılmış olabilecek bir cihaz veya zaten güvenliği aşılmış cihazlarla ilgili daha fazla içgörü için bir Microsoft tehdit uzmanına başvurabilirsiniz. Microsoft Tehdit Uzmanları, zamanında ve doğru yanıt için doğrudan Microsoft 365 Defender içinden devreye alınabilir. Uzmanlar yalnızca güvenliği aşılmış olabilecek bir cihazla ilgili değil, aynı zamanda karmaşık tehditleri, aldığınız hedefli saldırı bildirimlerini veya uyarılar hakkında daha fazla bilgiye ihtiyacınız varsa veya portal panonuzda gördüğünüz tehdit bilgileri bağlamını daha iyi anlamak için içgörüler sağlar.

Ayrıntılar için bkz. [Microsoft Tehdit Uzmanına Başvurun](/microsoft-365/security/defender-endpoint/configure-microsoft-threat-experts#consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization) .

## <a name="check-activity-details-in-action-center"></a>İşlem merkezinde etkinlik ayrıntılarını denetleyin

**İşlem merkezi**, bir cihazda veya dosyada gerçekleştirilen eylemler hakkında bilgi sağlar. Aşağıdaki ayrıntıları görüntüleyebileceksiniz:

- Araştırma paketi koleksiyonu
- Virüsten koruma taraması
- Uygulama kısıtlaması
- Cihaz yalıtımı

Gönderme tarihi/saati, kullanıcı gönderme ve eylemin başarılı veya başarısız olup olmadığını gibi diğer tüm ilgili ayrıntılar da gösterilir.

:::image type="content" source="images/action-center-details.png" alt-text="Bilgi içeren işlem merkezi" lightbox="images/action-center-details.png":::


## <a name="see-also"></a>Ayrıca bkz.

- [Dosyada yanıt eylemleri gerçekleştirin](respond-file-alerts.md)
- [Uç Nokta için Microsoft Defender Plan 1'de el ile yanıt eylemleri](defender-endpoint-plan-1.md#manual-response-actions)
- [Rapor yanlışlığı](/microsoft-365/security/defender-endpoint/tvm-security-recommendation#report-inaccuracy)
