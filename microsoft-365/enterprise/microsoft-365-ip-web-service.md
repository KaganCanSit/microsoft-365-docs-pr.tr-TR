---
title: OFFICE 365 IP Adresi ve URL web hizmeti
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 8/6/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: Ağ trafiğini daha iyi tanımlamanıza ve ayırt Office 365 yardımcı olmak için Office 365 IP Adresi ve URL web hizmetini kullanmayı öğrenin.
ms.openlocfilehash: b13377c6230c869231b7cecda8375f663cbcd33b
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100643"
---
# <a name="office-365-ip-address-and-url-web-service"></a>OFFICE 365 IP Adresi ve URL web hizmeti

Office 365 IP Adresi ve URL web hizmeti, Office 365 ağ trafiğini daha iyi tanımlamanıza ve ayırt etmenize yardımcı olur, böylece değişiklikleri değerlendirmenizi, yapılandırmanızı ve güncel kalmanızı kolaylaştırır. Bu REST tabanlı web hizmeti, 2 Ekim 2018'de kullanıma sunulan önceki XML indirilebilir dosyalarının yerini alır.

Müşteri veya ağ çevre cihazı satıcısı olarak, Office 365 IP adresi ve FQDN girişleri için web hizmetine göre derleme yapabilirsiniz. Şu URL'leri kullanarak verilere doğrudan bir web tarayıcısında erişebilirsiniz:

- Office 365 URL'lerinin ve IP adresi aralıklarının en son sürümü için kullanın[https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Güvenlik duvarları ve ara sunucuların Office 365 URL'leri ve IP adresi aralıkları sayfasındaki veriler için kullanın[https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Web hizmetinin ilk kullanıma sunulduğu Temmuz 2018'den bu yana yapılan en son değişiklikleri almak için kullanın [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

Müşteri olarak bu web hizmetini kullanarak şunları yapabilirsiniz:

- PowerShell betiklerinizi güncelleştirerek Office 365 uç nokta verilerini alın ve ağ cihazlarınız için tüm biçimlendirmeleri değiştirin.
- İstemci bilgisayarlara dağıtılan PAC dosyalarını güncelleştirmek için bu bilgileri kullanın.

Ağ çevre cihazı satıcısı olarak bu web hizmetini kullanarak şunları yapabilirsiniz:

- Otomatik yapılandırma listesini indirmek için cihaz yazılımı oluşturun ve test edin.
- Geçerli sürümü denetleyin.
- Geçerli değişiklikleri alın.

> [!NOTE]
> Office 365 bağlanmak için Azure ExpressRoute kullanıyorsanız, Azure ExpressRoute üzerinden desteklenen Office 365 hizmetleri hakkında bilgi edinmek [için lütfen Office 365 için Azure ExpressRoute'u](azure-expressroute.md) gözden geçirin. Ayrıca, Office 365 uygulamaları için hangi ağ isteklerinin İnternet bağlantısı gerektirdiğini anlamak için [URL'ler ve IP adresi aralıkları](urls-and-ip-address-ranges.md) Office 365 makalesini gözden geçirin. Bu, çevre güvenlik cihazlarınızı daha iyi yapılandırmanıza yardımcı olur.

Daha fazla bilgi için bkz.:

- [Office 365 Tech Community Forumu'ndaki duyuru blog gönderisi](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [web hizmetlerinin kullanımıyla ilgili sorular için Office 365 Tech Community Forumu](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>Ortak parametreler

Bu parametreler tüm web hizmeti yöntemlerinde ortaktır:

- **format=\<JSON \| CSV\>** —Varsayılan olarak, döndürülen veri biçimi JSON'dır. Verileri virgülle ayrılmış değerler (CSV) biçiminde döndürmek için bu isteğe bağlı parametreyi kullanın.
- **ClientRequestId=\<guid\>** —İstemci ilişkilendirmesi için oluşturduğunuz gerekli bir GUID. Web hizmetini çağıran her makine için benzersiz bir GUID oluşturun (bu sayfadaki betikler sizin için bir GUID oluşturur). Gelecekte web hizmeti tarafından engellenebileceği için aşağıdaki örneklerde gösterilen GUID'leri kullanmayın. GUID biçimi _xxxxxxxx-xxxx-xxxx-xxxx-xxxxx_ biçimindedir; burada x onaltılık bir sayıyı temsil eder.

  GUID oluşturmak için [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) PowerShell komutunu veya [Çevrimiçi GUID Oluşturucu](https://www.guidgenerator.com/) gibi çevrimiçi bir hizmeti kullanabilirsiniz.

## <a name="version-web-method"></a>Sürüm web yöntemi

Microsoft, her ayın başında Office 365 IP adresini ve FQDN girdilerini güncelleştirir. Destek olayları, güvenlik güncelleştirmeleri veya diğer operasyonel gereksinimler nedeniyle bant dışı güncelleştirmeler bazen yayımlanır.

Yayımlanan her örneğin verilerine bir sürüm numarası atanır ve sürüm web yöntemi, her Office 365 hizmet örneğinin en son sürümünü denetlemenize olanak tanır. Sürümü saatte bir kereden fazla denetlemenizi öneririz.

Sürüm web yönteminin parametreleri şunlardır:

- **AllVersions=\<true \| false\>** —Varsayılan olarak, döndürülen sürüm en son sürümdür. Web hizmeti ilk kez yayımlandıktan sonra yayımlanan tüm sürümleri istemek için bu isteğe bağlı parametreyi ekleyin.
- **Format=\<JSON \| CSV \| RSS\>** —JSON ve CSV biçimlerine ek olarak, sürüm web yöntemi RSS'yi de destekler. bu isteğe bağlı parametreyi _AllVersions=true_ parametresiyle birlikte kullanarak Outlook veya diğer RSS okuyucularla kullanılabilecek bir RSS akışı isteyebilirsiniz.
- **Örnek=\<Worldwide \| China \| USGovDoD \| USGovGCCHigh\>** —Bu isteğe bağlı parametre sürümü döndürülecek örneği belirtir. Atlanırsa, tüm örnekler döndürülür. Geçerli örnekler şunlardır: Dünya çapında, Çin, USGovDoD, USGovGCCHigh.

Sürüm web yöntemi hız sınırlı değildir ve hiçbir zaman 429 HTTP Yanıt Kodları döndürmez. Sürüm web yöntemine verilen yanıt, verilerin 1 saat önbelleğe alınmasını öneren bir önbellek denetimi üst bilgisi içerir. Sürüm web yönteminin sonucu tek bir kayıt veya bir kayıt dizisi olabilir. Her kaydın öğeleri şunlardır:

- instance—Office 365 hizmet örneğinin kısa adı.
- latest—Belirtilen örneğin uç noktaları için en son sürüm.
- versions—Belirtilen örnek için tüm önceki sürümlerin listesi. Bu öğe yalnızca _AllVersions_ parametresi true olduğunda eklenir.

### <a name="version-web-method-examples"></a>Sürüm web yöntemi örnekleri

Örnek 1 istek URI'si: <https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Bu URI, her Office 365 hizmet örneğinin en son sürümünü döndürür. Örnek sonuç:

```json
[
 {
  "instance": "Worldwide",
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD",
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 }
]
```

> [!IMPORTANT]
> Bu URI'lerdeki ClientRequestID parametresinin GUID değeri yalnızca bir örnektir. Web hizmeti URI'lerini denemek için kendi GUID'nizi oluşturun. Bu örneklerde gösterilen GUID'ler gelecekte web hizmeti tarafından engellenebilir.

Örnek 2 istek URI'si: <https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Bu URI, belirtilen Office 365 hizmet örneğinin en son sürümünü döndürür. Örnek sonuç:

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

Örnek 3 istek URI'si: <https://endpoints.office.com/version/Worldwide?Format=CSV&ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Bu URI, çıkışı CSV biçiminde gösterir. Örnek sonuç:

```csv
instance,latest
Worldwide,2018063000
```

Örnek 4 istek URI'si: <https://endpoints.office.com/version/Worldwide?AllVersions=true&ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Bu URI, dünya çapındaki Office 365 hizmet örneği için yayımlanmış olan önceki tüm sürümleri gösterir. Örnek sonuç:

```json
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

Örnek 5 RSS Akışı URI'si: <https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS>

Bu URI, her sürüm için değişiklik listesine bağlantılar içeren yayımlanmış sürümlerin RSS akışını gösterir. Örnek sonuç:

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<rss version="2.0" xmlns:a10="https://www.w3.org/2005/Atom">
<channel>
<link>https://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
```

## <a name="endpoints-web-method"></a>Uç noktalar web yöntemi

Uç noktalar web yöntemi, Office 365 hizmetini oluşturan IP adresi aralıkları ve URL'ler için tüm kayıtları döndürür. Uç noktalar web yönteminden en son veriler her zaman ağ cihazı yapılandırması için kullanılmalıdır. Microsoft, erişim denetimi listelerini ve ara sunucu atlama listelerini güncelleştirmeniz için size zaman vermek üzere yeni eklemeleri yayımlamadan 30 gün önce önceden bildirimde bulunur. Endpoints web yöntemini yalnızca sürüm web yöntemi verilerin yeni bir sürümünün kullanılabilir olduğunu gösterdiğinde yeniden çağırmanızı öneririz.

Uç nokta web yönteminin parametreleri şunlardır:

- **ServiceAreas=\<Common \| Exchange \| SharePoint \| Skype\>** —Hizmet alanlarının virgülle ayrılmış listesi. Geçerli öğeler _Ortak_, _Exchange_, _SharePoint_ ve _Skype_' dır. _Ortak_ hizmet alanı öğeleri diğer tüm hizmet alanları için bir önkoşul olduğundan, web hizmeti bunları her zaman içerir. Bu parametreyi eklemezseniz, tüm hizmet alanları döndürülür.
- **TenantName=\<tenant_name\>** —Office 365 kiracı adınız. Web hizmeti, sağlanan adınızı alır ve kiracı adını içeren URL'lerin bölümlerine ekler. Kiracı adı sağlamazsanız, URL'lerin bu bölümleri joker karaktere (\* ) sahiptir.
- **NoIPv6=\<true \| false\>** —Ağınızda IPv6 kullanmıyorsanız IPv6 adreslerini çıkıştan dışlamak için değeri _true_ olarak ayarlayın.
- **Örnek=\<Worldwide \| China \| USGovDoD \| USGovGCCHigh\>** —Bu gerekli parametre, uç noktaların döndürüleceği örneği belirtir. Geçerli örnekler şunlardır: _Dünya çapında_, _Çin_, _USGovDoD_ ve _USGovGCCHigh_.

Uç noktalar web yöntemini aynı istemci IP adresinden çok fazla çağırırsanız, HTTP yanıt kodu _429 (Çok Fazla İstek)_ alabilirsiniz. Bu yanıt kodunu alırsanız, isteğinizi yinelemeden önce 1 saat bekleyin veya istek için yeni bir GUID oluşturun. Genel bir en iyi yöntem olarak, yalnızca sürüm web yöntemi yeni bir sürümün kullanılabilir olduğunu gösterdiğinde endpoints web yöntemini çağırın.

Endpoints web yönteminden elde edilen sonuç, her kaydın belirli bir uç nokta kümesini temsil ettiği bir kayıt dizisidir. Her kaydın öğeleri şunlardır:

- id—Uç nokta kümesinin sabit kimlik numarası.
- serviceArea—Bunun parçası olduğu hizmet alanı: _Ortak_, _Exchange_, _SharePoint_ veya _Skype_.
- url'ler—uç nokta kümesinin URL'leri. DNS kayıtlarının JSON dizisi. Boşsa atlanır.
- tcpPorts—Uç nokta kümesi için TCP bağlantı noktaları. Tüm bağlantı noktaları öğeleri, bir tire karakteri (-) ile ayrılmış bağlantı noktalarının veya bağlantı noktası aralıklarının virgülle ayrılmış bir listesi olarak biçimlendirilir. Bağlantı noktaları, belirli bir kategori için uç nokta kümesindeki tüm IP adreslerine ve tüm URL'lere uygulanır. Boşsa atlanır.
- udpPorts—Bu uç nokta kümesindeki IP adresi aralıkları için UDP bağlantı noktaları. Boşsa atlanır.
- ips —Listelenen TCP veya UDP bağlantı noktalarıyla ilişkili olarak bu uç nokta kümesiyle ilişkilendirilmiş IP adresi aralıkları. IP adresi aralıklarından oluşan bir JSON dizisi. Boşsa atlanır.
- category—Uç nokta kümesinin bağlantı kategorisi. Geçerli değerler _İyileştir_, _İzin Ver_ ve _Varsayılan'dır_. Belirli bir IP adresinin veya URL'nin kategorisi için uç noktalar web yöntemi çıkışında arama yaparsanız, sorgunuz birden çok kategori döndürecektir. Böyle bir durumda, en yüksek öncelikli kategori için öneriyi izleyin. Örneğin, uç nokta hem _İyileştir_ hem de _İzin Ver'de_ görünüyorsa _İyileştir_ gereksinimlerini izlemeniz gerekir. Gerekli.
- expressRoute — Bu uç nokta kümesi ExpressRoute üzerinden yönlendiriliyorsa _True_ , yönlendirilmediyse _False_ .
- gerekli — Bu uç nokta kümesinin Office 365 desteklenmesi için bağlantıya sahip olması gerekiyorsa _true_. Bu uç nokta kümesi isteğe bağlıysa _False_.
- notlar—İsteğe bağlı uç noktalar için bu metinde, bu uç nokta kümesindeki IP adreslerine veya URL'lere ağ katmanından erişilemediğinde kullanılamayacak Office 365 işlev açıklanır. Boşsa atlanır.

### <a name="endpoints-web-method-examples"></a>Uç noktalar web yöntemi örnekleri

Örnek 1 istek URI'si: <https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Bu URI, tüm iş yükleri için dünya çapındaki Office 365 örneğinin tüm uç noktalarını alır. Çıktının bir alıntısını gösteren örnek sonuç:

```json
[
 {
  "id": 1,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.protection.outlook.com"
   ],
  "ips":
   [
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32"
   ],
  "tcpPorts": "443",
  "expressRoute": true,
  "category": "Allow"
 },
 {
  "id": 2,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.mail.protection.outlook.com"
   ],
```

Bu örnekteki isteğin tam çıkışı diğer uç nokta kümelerini içerir.

Örnek 2 istek URI'si: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp; ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Bu örnek yalnızca Exchange Online ve bağımlılıklar için Office 365 Worldwide örneğinin uç noktalarını alır.

Örneğin, 2, örnek 1'e benzer, ancak sonuçlar SharePoint Online veya Skype Kurumsal Online için uç noktaları içermeyecektir.

## <a name="changes-web-method"></a>Web yöntemini değiştirir

Değişiklik web yöntemi, yayımlanan en son güncelleştirmeleri( genellikle önceki ayın IP adresi aralıklarında ve URL'lerinde yapılan değişiklikleri) döndürür.

Uç nokta verilerinde yapılan en önemli değişiklikler yeni URL'ler ve IP adresleridir. Bir güvenlik duvarı erişim denetim listesine IP adresi veya ara sunucu atlama listesine URL eklenememesi, bu ağ cihazının arkasındaki Office 365 kullanıcılar için kesintiye neden olabilir. İşletimsel gereksinimlere bakılmaksızın, yeni uç noktalar, erişim denetim listelerini ve ara sunucu atlama listelerini güncelleştirmeniz için size zaman vermek üzere uç noktaların sağlandığı tarihten 30 gün önce web hizmetinde yayımlanır.

Changes web yöntemi için gerekli parametre:

- **Sürüm=\<YYYYMMDDNN>** —Gerekli URL yol parametresi. Bu değer, şu anda uyguladığınız sürümdür. Web hizmeti, bu sürümden bu yana yapılan değişiklikleri döndürür. Biçim _YYYYMMDDNN'dir_; burada tek bir günde yayımlanması gereken birden çok sürüm varsa _NN_ doğal bir sayı artırılır ve belirli bir gün için ilk güncelleştirmeyi temsil eden _00_ olur. Web hizmeti _sürüm parametresinin_ tam olarak 10 basamak içermesini gerektirir.

Değişiklik web yöntemi, uç noktalar web yöntemiyle aynı şekilde hız sınırına sahiptir. 429 HTTP yanıt kodu alırsanız, isteğinizi yinelemeden önce 1 saat bekleyin veya istek için yeni bir GUID oluşturun.

Değişiklik web yönteminden elde edilen sonuç, her kaydın uç noktaların belirli bir sürümündeki değişikliği temsil ettiği bir kayıt dizisidir. Her kaydın öğeleri şunlardır:

- id—Değişiklik kaydının sabit kimliği.
- endpointSetId—Değiştirilen uç nokta kümesi kaydının kimliği.
- disposition—Uç nokta kümesi kaydında yapılan değişikliği açıklar. Değerler _değişiklik_, _ekleme_ veya _kaldırma işlemleridir_.
- etki— Tüm değişiklikler her ortam için eşit derecede önemli olmayacaktır. Bu öğe, bu değişikliğin bir sonucu olarak kurumsal ağ çevre ortamına beklenen etkiyi açıklar. Bu öğe yalnızca **sürüm 2018112800** ve sonraki sürümlerin değişiklik kayıtlarına eklenir. Etki seçenekleri şunlardır: — AddedIp – Office 365 bir IP adresi eklendi ve yakında hizmette yayınlanacak. Bu, bir güvenlik duvarında veya 3. katmandaki başka bir ağ çevre cihazında yapmanız gereken bir değişikliği temsil eder. Bunu kullanmaya başlamadan önce eklemezseniz bir kesintiyle karşılaşabilirsiniz.
  — AddedUrl – Office 365'a bir URL eklendi ve yakında hizmette yayınlanacak. Bu, bir ara sunucu veya URL ayrıştırma ağ çevre cihazında yapmanız gereken bir değişikliği temsil eder. Bu URL'yi kullanmaya başlamadan önce eklemezseniz bir kesintiyle karşılaşabilirsiniz.
  — AddedIpAndUrl—Hem IP adresi hem de URL eklendi. Bu, güvenlik duvarı katman 3 cihazında ya da ara sunucu ya da URL ayrıştırma cihazında yapmanız gereken bir değişikliği temsil eder. Bu IP/URL çifti kullanmaya başlamadan önce eklemezseniz bir kesintiyle karşılaşabilirsiniz.
  — RemovedIpOrUrl – Office 365 en az bir IP adresi veya URL kaldırıldı. Çevre cihazlarınızdan ağ uç noktalarını kaldırın, ancak bunu yapmanız için son tarih yoktur.
  — ChangedIsExpressRoute – ExpressRoute destek özniteliği değiştirildi. ExpressRoute kullanıyorsanız, yapılandırmanıza bağlı olarak işlem yapmanız gerekebilir.
  — MovedIpOrUrl – Bir IP adresini veya Url'yi bu uç nokta kümesi ile başka bir uç nokta kümesi arasında taşıdık. Genellikle hiçbir eylem gerekmez.
  — RemovedDuplicateIpOrUrl – Yinelenen bir IP adresini veya Url'yi kaldırdık ancak Office 365 için yayımlanmaya devam ediyor. Genellikle hiçbir eylem gerekmez.
  — OtherNonPriorityChanges – Not alanının içeriği gibi diğer tüm seçeneklerden daha az kritik bir şeyi değiştirdik.
- version—Değişikliğin sunulduğu yayımlanmış uç nokta kümesinin sürümü. Sürüm numaraları _YYYYMMDDNN_ biçimindedir; burada _NN_ , tek bir günde yayımlanması gereken birden çok sürüm varsa doğal bir sayı artırılır.
- previous—Uç nokta kümesindeki değiştirilen öğelerin önceki değerlerinin ayrıntılarını veren bir alt yapı. Bu, yeni eklenen uç nokta kümelerine dahil edilmeyecektir. _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ ve _notları_ içerir.
- current—Uç nokta kümesindeki değişiklik öğelerinin güncelleştirilmiş değerlerinin ayrıntılarını veren bir alt yapı. _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ ve _notları_ içerir.
- add —Uç nokta kümesi koleksiyonlarına eklenecek öğeleri ayrıntılarıyla belirten bir alt yapı. Ekleme yoksa atlanır.
  — effectiveDate—Eklemelerin hizmette ne zaman canlı olacağını tanımlar.
  — ips— _ips_ dizisine eklenecek öğeler.
  — urls- _urls_ dizisine eklenecek öğeler.
- remove—Uç nokta kümesinden kaldırılacak öğelerin ayrıntılarını içeren bir alt yapı. Kaldırma yoksa atlanır.
  — ips— _ips_ dizisinden kaldırılacak öğeler.
  — urls- _Urls_ dizisinden kaldırılacak öğeler.

### <a name="changes-web-method-examples"></a>Web yöntemi örneklerini değiştirir

Örnek 1 istek URI'si: <https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Bu, dünya çapındaki Office 365 hizmet örneğinde önceki tüm değişiklikleri istemektedir. Örnek sonuç:

```json
[
 {
  "id": 424,
  "endpointSetId": 32,
  "disposition": "Change",
  "version": "2018062700",
  "remove":
   {
    "urls":
     [
      "*.api.skype.com", "skypegraph.skype.com"
     ]
   }
 },
 {
  "id": 426,
  "endpointSetId": 31,
  "disposition": "Change",
  "version": "2018062700",
  "add":
   {
    "effectiveDate": "20180609",
    "ips":
     [
      "51.140.203.190/32"
     ]
   },
  "remove":
   {
    "ips":
     [
```

Örnek 2 istek URI'si: <https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Bu, belirtilen sürümden bu yana Office 365 Worldwide örneğine değişiklik isteğinde bulunur. Bu durumda, belirtilen sürüm en son sürümdür. Örnek sonuç:

```json
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]
```

## <a name="example-powershell-script"></a>Örnek PowerShell betiği

Güncelleştirilmiş veriler için gerçekleştirmeniz gereken eylemler olup olmadığını görmek için bu PowerShell betiğini çalıştırabilirsiniz. Sürüm güncelleştirmesini denetlemek için bu betiği zamanlanmış bir görev olarak çalıştırabilirsiniz. Web hizmetinde aşırı yük oluşmasını önlemek için betiği saatte bir kereden fazla çalıştırmamaya çalışın.

Betik aşağıdakileri yapar:

- Web hizmeti REST API'sini çağırarak geçerli Office 365 Dünya çapında örnek uç noktalarının sürüm numarasını denetler.
- _$Env:TEMP\O365_endpoints_latestversion.txt_ konumundaki geçerli bir sürüm dosyasını denetler. **$Env:TEMP** genel değişkeninin yolu genellikle _C:\Users\\<username\>\AppData\Local\Temp şeklindedir_.
- Betik ilk kez çalıştırılıyorsa, betik geçerli sürümü ve tüm geçerli IP adreslerini ve URL'lerini döndürür, uç nokta sürümünü _$Env:TEMP\O365_endpoints_latestversion.txt_ dosyasına ve uç nokta veri çıkışını _$Env:TEMP\O365_endpoints_data.txt_ dosyasına yazar. Şu satırları düzenleyerek çıkış dosyasının yolunu ve/veya adını değiştirebilirsiniz:

    ``` powershell
    $versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
    $datapath = $Env:TEMP + "\O365_endpoints_data.txt"
    ```

- Betiğin sonraki her yürütmesinde, en son web hizmeti sürümü _O365_endpoints_latestversion.txt_ dosyasındaki sürümle aynıysa, betik herhangi bir değişiklik yapmadan çıkar.
- En son web hizmeti sürümü _O365_endpoints_latestversion.txt_ dosyasındaki sürümden daha yeni olduğunda betik, **İzin Ver** ve **İyileştir** kategori uç noktaları için uç noktaları ve filtreleri döndürür, _O365_endpoints_latestversion.txt_ dosyasındaki sürümü güncelleştirir ve güncelleştirilmiş verileri _O365_endpoints_data.txt_ dosyasına yazar.

Betik, yürütülür bilgisayar için benzersiz bir _ClientRequestId_ oluşturur ve bu kimliği birden çok çağrıda yeniden kullanılır. Bu kimlik _O365_endpoints_latestversion.txt_ dosyasında depolanır.

### <a name="to-run-the-powershell-script"></a>PowerShell betiğini çalıştırmak için

1. Betiği kopyalayın ve yerel sabit sürücünüze veya betik konumunuza _Get-O365WebServiceUpdates.ps1_ olarak kaydedin.
1. Betiği PowerShell ISE veya VS Code gibi tercih ettiğiniz betik düzenleyicisinde veya aşağıdaki komutu kullanarak bir PowerShell konsolundan yürütür:

    ``` powershell
   powershell.exe -file <path>\Get-O365WebServiceUpdates.ps1
    ```

    Betike geçirecek parametre yok.

```powershell
<# Get-O365WebServiceUpdates.ps1
From https://aka.ms/ipurlws
v1.1 8/6/2019

DESCRIPTION
This script calls the REST API of the Office 365 IP and URL Web Service (Worldwide instance)
and checks to see if there has been a new update since the version stored in an existing
$Env:TEMP\O365_endpoints_latestversion.txt file in your user directory's temp folder
(usually C:\Users\<username>\AppData\Local\Temp).
If the file doesn't exist, or the latest version is newer than the current version in the
file, the script returns IPs and/or URLs that have been changed, added or removed in the latest
update and writes the new version and data to the output file $Env:TEMP\O365_endpoints_data.txt.

USAGE
Run as a scheduled task every 60 minutes.

PARAMETERS
n/a

PREREQUISITES
PS script execution policy: Bypass
PowerShell 3.0 or later
Does not require elevation
#>

#Requires -Version 3.0

# web service root URL
$ws = "https://endpoints.office.com"
# path where output files will be stored
$versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
$datapath = $Env:TEMP + "\O365_endpoints_data.txt"

# fetch client ID and version if version file exists; otherwise create new file and client ID
if (Test-Path $versionpath) {
    $content = Get-Content $versionpath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
    Write-Output ("Version file exists! Current version: " + $lastVersion)
}
else {
    Write-Output ("First run! Creating version file at " + $versionpath + ".")
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $versionpath
}

# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"
    # write the new version number to the version file
    @($clientRequestId, $version.latest) | Out-File $versionpath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    # URL results
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    # IPv4 results
    $flatIp4s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings contain dots
        $ip4s = $ips | Where-Object { $_ -like '*.*' }
        $ip4CustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ip4CustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip4CustomObjects
    }
    # IPv6 results
    $flatIp6s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv6 strings contain colons
        $ip6s = $ips | Where-Object { $_ -like '*:*' }
        $ip6CustomObjects = @()
        if ($endpointSet.category -in ("Optimize")) {
            $ip6CustomObjects = $ip6s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip6CustomObjects
    }

    # write output to screen
    Write-Output ("Client Request ID: " + $clientRequestId)
    Write-Output ("Last Version: " + $lastVersion)
    Write-Output ("New Version: " + $version.latest)
    Write-Output ""
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "IPv6 Firewall IP Address Ranges"
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    Write-Output ("IP and URL data written to " + $datapath)

    # write output to data file
    Write-Output "Office 365 IP and UL Web Service data" | Out-File $datapath
    Write-Output "Worldwide instance" | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output ("Version: " + $version.latest) | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv4 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv6 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "URLs for Proxy Server" | Out-File $datapath -Append
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-File $datapath -Append
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date."
}
```

## <a name="example-python-script"></a>Örnek Python Betiği

Windows 10 üzerinde Python 3.6.3 ile test edilen ve güncelleştirilmiş veriler için yapmanız gereken eylemler olup olmadığını görmek için çalıştırabileceğiniz bir Python betiği aşağıdadır. Bu betik, Office 365 Worldwide örnek uç noktalarının sürüm numarasını denetler. Bir değişiklik olduğunda, _İzin Ver_ ve _İyileştir_ kategori uç noktaları için uç noktaları ve filtreleri indirir. Ayrıca birden çok çağrıda benzersiz bir ClientRequestId kullanır ve geçici bir dosyada bulunan en son sürümü kaydeder. Sürüm güncelleştirmesini denetlemek için bu betiği saatte bir kez çağır.

```python
import json
import tempfile
from pathlib import Path
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = Path(tempfile.gettempdir() + '/endpoints_clientid_latestversion.txt')
# fetch client ID and version if data exists; otherwise create new file
if datapath.exists():
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))

    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

## <a name="web-service-interface-versioning"></a>Web Hizmeti arabirimi sürüm oluşturma

Gelecekte bu web hizmeti yöntemleri için parametrelerde veya sonuçlarda güncelleştirme yapılması gerekebilir. Bu web hizmetlerinin genel kullanılabilirlik sürümü yayımlandıktan sonra, Microsoft web hizmetine malzeme güncelleştirmeleri için önceden bildirim sağlamak için makul çaba gösterecektir. Microsoft bir güncelleştirmenin web hizmetini kullanan istemcilerde değişiklik gerektirdiğine inandığında, Microsoft web hizmetinin önceki sürümünü (bir sürüm geri) yeni sürümün yayımlanmasından sonra en az 12 ay boyunca kullanılabilir durumda tutar. Bu süre boyunca yükseltme yapmayan müşteriler web hizmetine ve yöntemlerine erişemeyebilir. Web hizmeti arabirimi imzasına aşağıdaki değişiklikler yapılırsa müşteriler web hizmeti istemcilerinin hatasız çalışmaya devam ettiğinden emin olmalıdır:

- Eski istemciler tarafından sağlanması gerekmeyen ve eski bir istemcinin aldığı sonucu etkilemeyen mevcut bir web yöntemine yeni bir isteğe bağlı parametre ekleme.
- Yanıt REST öğelerinden birine veya diğer sütunlardan birine yanıt CSV'sine yeni bir adlandırılmış öznitelik ekleme.
- Eski istemciler tarafından çağrılmayan yeni bir ada sahip yeni bir web yöntemi ekleme.

## <a name="update-notifications"></a>Bildirimleri güncelleştirme

IP adreslerinde ve URL'lerde yapılan değişiklikler web hizmetinde yayımlandığında e-posta bildirimleri almak için birkaç farklı yöntem kullanabilirsiniz.

- Power Automate çözümü kullanmak için bkz. [Office 365 IP Adresleri ve URL'lerinde yapılan değişiklikler için e-posta almak için Power Automate kullanma](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).
- ARM şablonu kullanarak Azure Logic App dağıtmak için bkz. [Office 365 Güncelleştirme Bildirimi (v1.1)](https://aka.ms/ipurlws-updates-template).
- PowerShell kullanarak kendi bildirim betiğinizi yazmak için bkz. [Send-MailMessage](/powershell/module/microsoft.powershell.utility/send-mailmessage).

## <a name="exporting-a-proxy-pac-file"></a>Proxy PAC dosyasını dışarı aktarma

[Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile), Office 365 IP Adresi ve URL web hizmetinden en son ağ uç noktalarını okuyan ve örnek bir PAC dosyası oluşturan bir PowerShell betiğidir. Get-PacFile kullanma hakkında bilgi için bkz. [Önemli Office 365 trafiğinin doğrudan yönlendirilmesi için PAC dosyası kullanma](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic).

## <a name="related-topics"></a>İlgili Konular
  
[Office 365 URL'leri ve IP adresi aralıkları](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[Office 365 uç noktalarını yönetme](managing-office-365-endpoints.md)
  
[Office 365 uç noktaları hakkında SSS](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[Office 365 Ağ Bağlantı İlkeleri](microsoft-365-network-connectivity-principles.md)

[ağ ve performans ayarlamayı Office 365](network-planning-and-performance.md)

[Office 365 ağ bağlantısını değerlendirme](assessing-network-connectivity.md)
  
[Skype Kurumsal Online'da Medya Kalitesi ve Ağ Bağlantısı Performansı](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Ağınızı Skype Kurumsal Online için iyileştirme](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[Temelleri ve performans geçmişini kullanarak performans ayarlamayı Office 365](performance-tuning-using-baselines-and-history.md)
  
[Office 365 için performans sorunlarını giderme planı](performance-troubleshooting-plan.md)
