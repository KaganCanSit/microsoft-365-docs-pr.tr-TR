---
title: Hatalı sitelere bağlantıları önlemeye yardımcı olmak için ağ korumasını kullanma
description: Kullanıcıların bilinen kötü amaçlı ve şüpheli ağ adreslerine erişmesini engelleyerek ağınızı koruyun
keywords: Ağ koruması, açıklardan yararlanmalar, kötü amaçlı web sitesi, ip, etki alanı, etki alanları, komut ve denetim, SmartScreen, bildirim
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: oogunrinde
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: overview
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.date: ''
ms.openlocfilehash: 6bf97490d60740b47420d352f7fb537e675678ae
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621132"
---
# <a name="protect-your-network"></a>Ağınızı koruyun

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="overview-of-network-protection"></a>Ağ korumasına genel bakış

Ağ koruması, cihazların İnternet tabanlı olaylardan korunmasına yardımcı olur. Ağ koruması bir saldırı yüzeyi azaltma özelliğidir. Çalışanların uygulamalar aracılığıyla tehlikeli etki alanlarına erişmesini önlemeye yardımcı olur. İnternette kimlik avı dolandırıcılığı, açıklardan yararlanma ve diğer kötü amaçlı içerikleri barındıran etki alanları tehlikeli olarak kabul edilir. Ağ koruması[, düşük](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) saygınlık kaynaklarına bağlanmaya çalışan tüm giden HTTP trafiğini (etki alanı veya konak adına göre) engellemek için Microsoft Defender SmartScreen kapsamını genişletir.

Ağ koruması [, Web korumasındaki](web-protection-overview.md) korumayı işletim sistemi düzeyine genişletir. Diğer desteklenen tarayıcılara ve tarayıcı olmayan uygulamalara Microsoft Edge bulunan web koruma işlevselliğini sağlar. Ağ koruması ayrıca [Uç nokta algılama ve yanıt](overview-endpoint-detection-response.md) ile kullanıldığında güvenliğin aşılmasına ilişkin göstergelerin (ICS) görünürlüğünü ve engellenmesini de sağlar. Örneğin, ağ koruması belirli etki alanlarını veya konak adlarını engellemek için kullanabileceğiniz [özel göstergelerinizle](manage-indicators.md) birlikte çalışır.

> [!TIP]
> Ağ korumasının nasıl çalıştığını görmek için [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) Uç Nokta için Microsoft Defender testground sitesine bakın.

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

Ağ korumasının cihazlarınızın saldırı yüzeyini kimlik avı dolandırıcılığı, açıklardan yararlanma ve diğer kötü amaçlı içeriklerden nasıl azaltmaya yardımcı olduğunu öğrenmek için bu videoyu izleyin.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4r4yZ]

## <a name="requirements-for-network-protection"></a>Ağ koruması gereksinimleri

Ağ koruması için Windows 10 Pro veya Enterprise ve gerçek zamanlı koruma Microsoft Defender Virüsten Koruma gerekir.

****

| Windows sürümü | Microsoft Defender Virüsten Koruma |
|:---|:---|
| Windows 10 sürüm 1709 veya üzeri <br> Windows 11 <br> Windows Server 1803 veya üzeri | [Gerçek zamanlı koruma Microsoft Defender Virüsten Koruma](configure-real-time-protection-microsoft-defender-antivirus.md) <br> ve [bulut tabanlı koruma](enable-cloud-protection-microsoft-defender-antivirus.md) etkinleştirilmelidir (etkin)|

## <a name="why-network-protection-is-important"></a>Ağ koruması neden önemlidir?

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen önceden yayımlanmış ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.
>
> Ticari olarak kullanılabilen özellikler hakkındaki bilgiler, Genel Önizleme bilgilerini izler.

Ağ koruması, Uç Nokta için Microsoft Defender'deki saldırı yüzeyi azaltma çözümleri grubunun bir parçasıdır. Ağ koruması, URL'lerin ve IP'lerin katman 3 'ün (ağ katmanı) engellenmesini sağlar. Ağ koruması, üçüncü taraf tarayıcılardan ve standart ağ bağlantılarından ERIŞilen URL'leri engelleyebilir.

Varsayılan olarak, ağ koruması, kötü amaçlı URL'leri Microsoft Edge tarayıcıdaki SmartScreen'e benzer şekilde engelleyen Akıllı Ekran akışını kullanarak bilgisayarlarınızı bilinen kötü amaçlı URL'lerden korur. Ağ koruma işlevselliği şu şekilde genişletilebilir:

- Kendi Tehdit Intel'inizden IP/URL'yi engelleme (Göstergeler)
- Microsoft Cloud App Security 'dan (MCAS) tasdik edilmemiş hizmetleri engelleme
- Siteleri kategoriye göre engelleme (Web İçeriği filtreleme)

Ağ Korumaları, Microsoft koruma ve yanıt yığınının kritik bir parçasıdır.

Windows Server, Linux, MacOS ve MTD için Ağ Koruması hakkında ayrıntılı bilgi için bkz. [Gelişmiş avcılık ile tehditleri proaktif olarak avlama](advanced-hunting-overview.md).

### <a name="block-command-and-control-c2-attacks"></a>Komut ve Denetim (C2) saldırılarını engelleme

C2 sunucu bilgisayarları kötü amaçlı kullanıcılar tarafından kötü amaçlı yazılımlar tarafından tehlikeye girmiş sistemlere komut göndermek için kullanılır ve ardından güvenliği aşılmış sistemler üzerinde bir tür denetim kullanır. C2 saldırıları genellikle dosya paylaşımı ve web posta hizmetleri gibi bulut tabanlı hizmetlerde gizlenir ve C2 sunucularının tipik trafikle karışarak algılamayı önlemesini sağlar.

C2 sunucuları, şu komutları başlatmak için kullanılabilir:

- verileri çalma (örneğin, kimlik avı yoluyla)
- botnet'te güvenliği aşılmış bilgisayarları denetleme
- meşru uygulamaları kesintiye uğratma
- fidye yazılımı gibi kötü amaçlı yazılımları yayma

Uç Nokta için Microsoft Defender Ağ Koruması bileşeni, makine öğrenmesi ve akıllı risk göstergesi (IoC) belirleme gibi teknikleri kullanarak insan tarafından çalıştırılan fidye yazılımı saldırılarında kullanılan C2 altyapılarına yönelik bağlantıları tanımlar ve engeller.

#### <a name="network-protection-new-toast-notifications"></a>Ağ koruması: Yeni bildirim bildirimleri

| Yeni eşleme  | Yanıt kategorisi  | Kaynak |
| :--- | :--- | :--- |
| Kimlik avı | Kimlik Avı | Smartscreen |
| Kötü amaçlı | Kötü amaçlı | Smartscreen |
| komut ve denetim | C2 | Smartscreen |
| komut ve denetim | COCO | Smartscreen |
| Kötü amaçlı | Güvenilmeyen | Smartscreen |
| BT yöneticiniz tarafından | CustomBlockList |   |
| BT yöneticiniz tarafından | CustomPolicy |   |

> [!NOTE]
> **customAllowList** uç noktalarda bildirim oluşturmaz.

### <a name="new-notifications-for-network-protection-determination"></a>Ağ koruması belirlemeye yönelik yeni bildirimler

Ağ korumasındaki genel kullanıma açık yeni bir özellik, kötü amaçlı komut ve denetim sitelerindeki kimlik avı etkinliklerini engellemek için SmartScreen'teki işlevleri kullanır.

Bir son kullanıcı, ağ korumasının etkinleştirildiği bir ortamda bir web sitesini ziyaret etmeye çalıştığında üç senaryo mümkündür:

- **URL'nin bilinen iyi bir üne** sahip olması - Bu durumda kullanıcıya engelleme olmadan erişim izni verilir ve uç noktada bildirim sunulmaz. Etki alanı veya URL etkin olarak _İzin Verildi_ olarak ayarlanır.
- URL **bilinmeyen veya belirsiz bir üne** sahip - Kullanıcının erişimi engellenir, ancak engeli aşma (engellemesini kaldırma) özelliğiyle. Etkin olarak, etki alanı veya URL _Denetim_ olarak ayarlanır.
- URL'nin **bilinen kötü (kötü amaçlı) bir itibarı** var- Kullanıcının erişimi engellendi. Etkin olarak, etki alanı veya URL _Engelle_ olarak ayarlanır.

#### <a name="warn-experience"></a>Deneyimi uyar

Kullanıcı bir web sitesini ziyaret eder:

- URL'nin bilinmeyen veya belirsiz bir itibarı varsa, kullanıcıya aşağıdaki seçenekleri içeren bir bildirim sunulur:

  - **Tamam** - Bildirim yayımlanır (kaldırılır) ve siteye erişim girişimi sona erer.
  - **Engellemeyi kaldırma** - Kullanıcının site erişimi kazanmak için Windows Defender Güvenlik Bilgileri (WDSI) portalına erişmesi gerekmez. Kullanıcı 24 saat boyunca siteye erişebilir; bu noktada blok 24 saat daha yeniden kullanılabilir. Kullanıcı, yönetici siteyi yasaklayana (engelleyene) kadar siteye erişmek için **Engellemeyi** Kaldır'ı kullanmaya devam edebilir ve böylece **Engellemeyi Kaldırma** seçeneğini kaldırır.
  - **Geri Bildirim** - Bildirim, kullanıcıya, siteye erişimi gerekçelendirmek amacıyla yöneticiye geri bildirim göndermek için kullanabileceği bir bilet gönderme bağlantısı sunar.

  > [!div class="mx-imgBorder"]
  > ![Ağ koruması kimlik avı içeriği uyarı bildirimini gösterir](images/network-protection-phishing-warn-2.png)

  > [NOT!] Burada uyarı deneyimi ve engelleme deneyimi için gösterilen görüntüler (aşağıda) her ikisinde de örnek yer tutucu metin olarak **"engellenen URL"** listelenir; çalışma ortamında gerçek URL veya etki alanı listelenir.  

#### <a name="block-experience"></a>Blok deneyimi

Kullanıcı bir web sitesini ziyaret eder:

- URL'nin kötü bir ünü varsa, kullanıcıya aşağıdaki seçenekleri içeren bir bildirim sunulur:
  - **Tamam** Bildirim yayımlanır (kaldırılır) ve siteye erişim girişimi sona erer.
  - **Geribildirim** Bildirimde kullanıcıya, siteye erişimi gerekçelendirmek amacıyla yöneticiye geri bildirim göndermek için kullanabileceği bir bilet gönderme bağlantısı bulunur.
  
  > [!div class="mx-imgBorder"]
  > ![ Ağ koruması bilinen kimlik avı içeriği engellendi bildirimini gösterir](images/network-protection-phishing-blocked.png)

### <a name="network-protection-c2-detection-and-remediation"></a>Ağ koruması: C2 algılama ve düzeltme

İlk biçiminde fidye yazılımı, önceden programlanmış ve sınırlı, belirli sonuçlara (örneğin, bir bilgisayarı şifrelemeye) odaklanmış bir ticari tehdittir. Ancak fidye yazılımı insan odaklı, uyarlamalı ve daha büyük ölçekli ve daha yaygın sonuçlara odaklanan gelişmiş bir tehdit haline gelmiştir; bir kuruluşun tüm varlıklarını veya verilerini fidye için tutmak gibi.

Komut ve Denetim desteği (C2), bu fidye yazılımı evriminin önemli bir parçasıdır ve bu saldırıların hedefledikleri ortama uyum sağlamasına olanak tanır. Komut ve denetim altyapısı bağlantısının kesilmesi, bir saldırının bir sonraki aşamasına ilerlemesini durdurmak anlamına gelir.

#### <a name="detecting-and-remediating-cobaltstrike-public-preview"></a>CobaltStrike'i algılama ve düzeltme (genel önizleme)

İnsan tarafından çalıştırılan fidye yazılımı saldırılarında kullanılan en yaygın sömürü sonrası çerçevelerden biri CobaltStrike'dir. Microsoft'taki Tehdit Bilgileri ekipleri, kötü amaçlı aktörler tarafından kullanılan belirli stratejilere ve tehdit vektörlerine karşı savunmak için kullanılabilecek davranış desenlerini tanımlamak için fidye yazılımı dağıtan birden çok etkinlik grubunda _Taktikler, Teknikler_ ve Yordamlar'ı (TTP) izler. Bu fidye yazılımı etkinlik gruplarının tümü, saldırı yaşam döngüsünün bir noktasında, uygulamalı klavye etkinliğini etkinleştirmek için kurbanın bilgisayarına bir CobaltStrike İşareti dağıtmayı içerir.

CobaltStrike, farklı protokollere yanıt veren birden çok dinleyici barındırma özelliğinden ana istemci tarafı bileşeninin (Beacon) kod ekleme ve yararlanma sonrası işleri çalıştırma şekline kadar saldırının birden çok yönünün özelleştirilmesini sağlar. Microsoft Defender CobaltStrike'i algıladığında, önemli risk göstergelerini (IoC) akıllı bir şekilde bulabilir ve toplayabilir. Yakalanan bu göstergeler, algılama ve koruma amacıyla Microsoft'un ürün yığınında paylaşılır.

Microsoft Defender'ın komut ve denetim algılaması CobaltStrike ile sınırlı değildir. Microsoft Defender, birden çok kötü amaçlı yazılım ailesinin önemli ICS'lerini yakalayabilir. Göstergeler, müşterileri korumak ve bir risk söz konusu olduğunda onları uyarmak için Microsoft koruma yığınında paylaşılır.

Komut ve denetim iletişiminin engellenmesi, hedefli bir saldırıyı ciddi şekilde engelleyerek, savunmacılara ilk giriş vektörlerini bulmaları ve başka bir saldırı girişiminden önce kapatmaları için zaman verebilir.

<!-- Hide {this intro with no subsequent list items}
[For additional details about Microsoft Defender's command and control detection, see **ADD LINK TO BLOG**.]
-->

## <a name="smart-screen-unblock"></a>Akıllı Ekran Engellemesini Kaldır

Uç Nokta için Microsoft Defender Göstergeleri'ndeki yeni bir özellik, yöneticilerin son kullanıcıların bazı URL'ler ve IP'ler için oluşturulan "Uyarıları" atlamasına olanak tanır. URL'nin neden engellendiğine bağlı olarak, bir Akıllı Ekran bloğuyla karşılaşıldığında yöneticilere sitenin engellemesini 24 saate kadar kaldırma olanağı sunabilir. Bu gibi durumlarda, son kullanıcının tanımlı süre boyunca URL veya IP **engelini kaldırmasına** izin verecek bir Windows Güvenliği bildirim görüntülenir.  

 > [!div class="mx-imgBorder"]
 > ![Ağ koruması için Windows Güvenliği bildirimi](images/network-protection-smart-screen-block-notification.png)

Uç Nokta için Microsoft Defender Yöneticiler, aşağıdaki yapılandırma aracını kullanarak [Microsoft 365 Defender](https://security.microsoft.com/) akıllı ekran engellemesini kaldırma işlevini yapılandırabilir. Microsoft 365 Defender portalından ConfigToolName yoluna gidin.

<!-- Hide {this intro with no subsequent list items}
[Line 171: Delete the colon and the right angle-brackets. The resulting sentence will be "From the [MS365 Defender] portal, navigate to path to ConfigToolName." Delete "to" and add "the" before path unless a specific description is available. Would a screenshot help? Normally angle brackets or arrows are used in place of certain text rather than in addition.]
-->

 > [!div class="mx-imgBorder"]
 > ![Ağ koruması akıllı ekran bloğu yapılandırması ULR ve IP formu](images/network-protection-smart-screen-block-configuration.png)

## <a name="using-network-protection"></a>Ağ korumasını kullanma

Ağ koruması cihaz başına etkinleştirilir ve bu genellikle yönetim altyapınız kullanılarak gerçekleştirilir. Desteklenen yöntemler için bkz [. Ağ korumasını açma](enable-network-protection.md).

> [!NOTE]
> ağ korumasını etkinleştirmek için Microsoft Defender Virüsten Koruma etkin olmalıdır.

Ağ Koruması'nı **Denetim** modunda veya **Blok** modunda etkinleştirebilirsiniz. IP'leri veya URL'leri engellemeden önce Ağ Koruması'nı etkinleştirmenin etkisini değerlendirmek istiyorsanız, engellenecek veriler hakkında veri toplamak için bir süre denetim modunda etkinleştirebilirsiniz. Son kullanıcılar ağ koruması tarafından engellenecek bir adrese veya siteye bağlandığında denetim modu günlükleri.

## <a name="advanced-hunting"></a>Gelişmiş avcılık

Denetim olaylarını tanımlamak için Gelişmiş Avcılık kullanıyorsanız konsoldan 30 güne kadar geçmişe sahip olursunuz. Bkz. [Gelişmiş Avcılık](advanced-hunting-overview.md).

Denetim verilerini Uç Nokta için Microsoft Defender portalında **Gelişmiş avcılık** bölümünde bulabilirsiniz.  

Olaylar, ExploitGuardNetworkProtectionAudited ActionType ile DeviceEvents'tedir. Bloklar ExploitGuardNetworkProtectionBlocked tarafından gösterilir.  

Aşağıdaki örnek engellenen eylemleri içerir:

DeviceEvents

- Where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked')

 > [!div class="mx-imgBorder"]
 > ![Olayları denetlemek ve tanımlamak için Gelişmiş Avcılık](images/network-protection-advanced-hunting.png)

> [!TIP]
> Bu girdilerin AdditionalFields sütunundaki veriler, eylemle ilgili harika bilgiler sağlar. AdditionalFields'i genişletirseniz **IsAudit**, **ResponseCategory** ve **DisplayName** alanlarını da alabilirsiniz.

DeviceEvents:

- Burada ActionType "ExploitGuardNetworkProtection" içeriyor
- extend ParsedFields=parse_json(AdditionalFields)
- project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, IsAudit=tostring(ParsedFields.IsAudit), ResponseCategory=tostring(ParsedFields.ResponseCategory), DisplayName=tostring(ParsedFields.DisplayName)
- Timestamp desc'ye göre sıralama

Yanıt kategorisi, olaya neyin neden olduğunu söyler, örneğin:

| ResponseCategory | Olaydan sorumlu özellik |
|:---|:---|
| CustomPolicy |  WCF  |
| CustomBlockList  |   Özel göstergeler   |
| CasbPolicy   |   Bulut Uygulamaları için Defender   |
| Kötü amaçlı   |   Web tehditleri  |
| Kimlik Avı  |   Web tehditleri  |

Daha fazla bilgi için bkz. [Uç nokta blokları sorunlarını giderme](web-protection-overview.md#troubleshoot-endpoint-blocks).

Cihazın blok modunda olması durumunda nelerin engelleneceğini ve hangi özelliğin engellendiğini belirlemek için sonuçta elde edilen URL'ler ve IP'ler listesini kullanabilirsiniz. Ortamınız için gerekli olup olmadığını belirlemek için listedeki her öğeyi gözden geçirin. Denetlenen ve ortamınız için kritik olan girdiler bulursanız, ağınızda bunlara izin vermek için bir Gösterge oluşturun. URL/IP göstergelerine izin ver, herhangi bir blok üzerinde önceliklidir.

Bir Gösterge oluşturduktan sonra temel alınan sorunu çözmeye bakabilirsiniz:

- Akıllı ekran – gözden geçirme isteği
- Gösterge – var olan göstergeyi değiştirme
- MCA – tasdik edilmemiş UYGULAMAYı gözden geçirme
- WCF – yeniden kategorilere ayırma isteği

Bu verileri kullanarak, Ağ korumasını Engelleme modunda etkinleştirme konusunda bilinçli bir karar vekleyebilirsiniz. Bkz [. Ağ koruma blokları için öncelik sırası](web-protection-overview.md#order-of-precedence).

> [!NOTE]
> Bu cihaz başına bir ayar olduğundan, Engelleme moduna geçemeyen cihazlar varsa, sınamayı düzeltene ve denetim olaylarını almaya devam edene kadar bunları denetimde bırakmanız yeterlidir.

Hatalı pozitifleri bildirme hakkında bilgi için bkz. [Hatalı pozitifleri raporlama](web-protection-overview.md#report-false-positives).

Kendi Power BI raporlarınızı oluşturma hakkında ayrıntılı bilgi için bkz. [Power BI kullanarak özel raporlar oluşturma](api-power-bi.md).

## <a name="configuring-network-protection"></a>Ağ korumasını yapılandırma

Ağ korumasını etkinleştirme hakkında daha fazla bilgi için bkz. **[Ağ korumasını etkinleştirme](enable-network-protection.md)**. Ağınızda ağ korumasını etkinleştirmek ve yönetmek için grup ilkesi, PowerShell veya MDM CSP'lerini kullanın.

Hizmetleri etkinleştirdikten sonra, ağınızı veya güvenlik duvarınızı hizmetlerle cihazlarınız (uç noktalar olarak da adlandırılır) arasındaki bağlantılara izin verecek şekilde yapılandırmanız gerekebilir.

- `.smartscreen.microsoft.com`
- `.smartscreen-prod.microsoft.com`

## <a name="viewing-network-protection-events"></a>Ağ koruma olaylarını görüntüleme

Ağ koruması en iyi [Uç Nokta için Microsoft Defender](microsoft-defender-endpoint.md) ile çalışır ve [bu da uyarı araştırma senaryolarının](investigate-alerts.md) bir parçası olarak açıklardan yararlanma koruma olayları ve blokları hakkında ayrıntılı raporlama sağlar.

Ağ koruması bir bağlantıyı engellediğinde, İşlem Merkezi'nden bir bildirim görüntülenir. Güvenlik operasyonları ekibiniz, kuruluşunuzun ayrıntıları ve iletişim bilgileriyle [bildirimi özelleştirebilir](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) . Ayrıca, tek tek saldırı yüzeyi azaltma kuralları etkinleştirilebilir ve izlemek için belirli tekniklere uyacak şekilde özelleştirilebilir.

Ağ korumasının etkinleştirildiğinde kuruluşunuzu nasıl etkileyeceğini değerlendirmek için [denetim modunu](audit-windows-defender.md) da kullanabilirsiniz.

## <a name="review-network-protection-events-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında ağ koruma olaylarını gözden geçirme

Uç Nokta için Microsoft Defender[, uyarı araştırma senaryolarının](investigate-alerts.md) bir parçası olarak olaylara ve bloklara ayrıntılı raporlama sağlar. Bu ayrıntıları [uyarı kuyruğundaki](review-alerts.md) Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com)) veya [gelişmiş avcılığı](advanced-hunting-overview.md) kullanarak görüntüleyebilirsiniz. [Denetim modunu](audit-windows-defender.md) kullanıyorsanız, ağ koruma ayarlarının etkinleştirildiyse ortamınızı nasıl etkileyeceğini görmek için gelişmiş avcılığı kullanabilirsiniz.

Gelişmiş avcılık için örnek bir sorgu aşağıda verilmişti:

```kusto
DeviceNetworkEvents
|where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked', 'ConnectionSuccess')
```

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Windows Olay Görüntüleyicisi'da ağ koruma olaylarını gözden geçirme

Ağ koruması kötü amaçlı bir IP'ye veya etki alanına erişimi engellediğinde (veya denetlediğinde) oluşturulan olayları görmek için Windows olay günlüğünü gözden geçirebilirsiniz:

1. [XML'yi doğrudan kopyalayın](event-views.md).

2. **Tamam**'ı seçin.

Bu yordam, yalnızca ağ korumasıyla ilgili aşağıdaki olayları gösterecek şekilde filtreleyen özel bir görünüm oluşturur:

****

|Olay Kimliği|Açıklama|
|---|---|
|5007|Ayarlar değiştirildiğinde gerçekleşen olay|
|1125|Ağ koruması denetim modunda tetiklendiğinde gerçekleşen olay|
|1126|Ağ koruması blok modunda tetiklendiğinde gerçekleşen olay|
|

## <a name="network-protection-and-the-tcp-three-way-handshake"></a>Ağ koruması ve TCP üç yönlü el sıkışması

Ağ koruması ile, [TCP/IP aracılığıyla üç yönlü el sıkışması](/troubleshoot/windows-server/networking/three-way-handshake-via-tcpip) tamamlandıktan sonra siteye erişime izin verilip verilmeyeceğinin veya engellenip engellenmeyeceğinin belirlenmesi yapılır. Bu nedenle, bir site ağ koruması tarafından engellendiğinde, site gerçekten engellenmiş olsa bile Microsoft 365 Defender portalında altında `NetworkConnectionEvents` bir eylem türü `ConnectionSuccess` görebilirsiniz. `NetworkConnectionEvents` ağ korumasından değil TCP katmanından bildirilir. Üç yönlü el sıkışması tamamlandıktan sonra siteye erişime izin verilir veya ağ koruması tarafından engellenir.

Bunun nasıl çalıştığına dair bir örnek aşağıda verilmişti:

1. Bir kullanıcının cihazında bir web sitesine erişmeye çalıştığı varsayılmaktadır. Site tehlikeli bir etki alanında barındırılacak ve ağ koruması tarafından engellenmelidir.  

2. TCP/IP aracılığıyla üç yönlü el sıkışması başlar. İşlem tamamlanmadan önce bir `NetworkConnectionEvents` eylem günlüğe kaydedilir ve eylemi `ActionType` olarak `ConnectionSuccess`listelenir. Ancak, üç yönlü el sıkışma işlemi tamamlandığında ağ koruması siteye erişimi engeller. Tüm bunlar çok hızlı gerçekleşir. Benzer bir işlem [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) gerçekleşir; üç yönlü el sıkışması tamamlandığında belirleme yapılır ve siteye erişim engellenir veya siteye erişime izin verilir.

3. Microsoft 365 Defender portalında, [uyarılar kuyruğunda bir uyarı](alerts-queue.md) listelenir. Bu uyarının ayrıntıları hem hem `AlertEvents`de `NetworkConnectionEvents` içerir. ActionType içeren bir `NetworkConnectionEvents` öğeniz de olsa, sitenin `ConnectionSuccess`engellendiğini görebilirsiniz.

## <a name="considerations-for-windows-virtual-desktop-running-windows-10-enterprise-multi-session"></a>Çoklu Oturum Windows 10 Enterprise çalışan Windows sanal masaüstü için dikkat edilmesi gerekenler

Windows 10 Enterprise çok kullanıcılı yapısı nedeniyle aşağıdaki noktaları göz önünde bulundurun:

1. Ağ koruması cihaz genelindeki bir özelliktir ve belirli kullanıcı oturumlarına hedeflenemez.

2. Web içeriği filtreleme ilkeleri de cihaz genelindedir.

3. Kullanıcı grupları arasında ayrım yapmanız gerekiyorsa, sanal masaüstü konak havuzları ve atamaları Windows ayrı ayrı oluşturmayı göz önünde bulundurun.

4. Dağıtımdan önce davranışını değerlendirmek için ağ korumasını denetim modunda test edin.

5. Çok fazla sayıda kullanıcınız veya çok sayıda çok kullanıcılı oturumunuz varsa dağıtımınızı yeniden boyutlandırmayı göz önünde bulundurun.

### <a name="alternative-option-for-network-protection"></a>Ağ koruması için alternatif seçenek

Azure'da Windows Sanal Masaüstü'nde kullanılan Windows 10 Enterprise Çoklu Oturum 1909 ve üstü için, Microsoft Edge için ağ koruması aşağıdaki yöntem kullanılarak etkinleştirilebilir:

1. [Ağ korumasını aç'ı](enable-network-protection.md) kullanın ve ilkenizi uygulamak için yönergeleri izleyin.

2. Aşağıdaki PowerShell komutlarını yürütür:
  - `Set-MpPreference -EnableNetworkProtection Enabled`
  - `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`
  - `Set-MpPreference -AllowNetworkProtectionDownLevel 1`
  - `Set-MpPreference -AllowDatagramProcessingOnWinServer 1`

## <a name="network-protection-troubleshooting"></a>Ağ koruması sorunlarını giderme

Ağ korumasının çalıştığı ortam nedeniyle Microsoft, işletim sistemi proxy ayarlarını algılayamayabilir. Bazı durumlarda ağ koruma istemcileri Bulut Hizmeti'ne ulaşamaz. Bağlantı sorununu çözmek için E5 lisansı olan müşterilerin aşağıdaki kayıt defteri anahtarlarından birini yapılandırması gerekir:

```console
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyServer /d "<proxy IP address: Port>" /f
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyPacUrl /d "<Proxy PAC url>" /f

```

## <a name="see-also"></a>Ayrıca bkz.

- [Ağ koruma | değerlendirme](evaluate-network-protection.md) Özelliğin nasıl çalıştığını ve genellikle hangi olayların oluşturulacağını gösteren hızlı bir senaryoyu üstlenin.
- [Ağ korumasını etkinleştirme](enable-network-protection.md) | Ağınızda ağ korumasını etkinleştirmek ve yönetmek için grup ilkesi, PowerShell veya MDM CSP'lerini kullanın.
- [Microsoft Intune'de saldırı yüzeyi azaltma özelliklerini yapılandırma](/mem/intune/protect/endpoint-security-asr-policy)
