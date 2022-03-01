---
title: Office 365 IP Adresi ve URL web hizmeti
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Ağ trafiğini daha iyi Office 365 tanımlamanıza ve ayırt etmeye yardımcı olmak için IP Adresi ve URL web hizmetini Office 365 öğrenin.
ms.openlocfilehash: 5af1ca60a6e7b7f28ad1d5c3268c85fb399fb926
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019507"
---
# <a name="office-365-ip-address-and-url-web-service"></a>Office 365 IP Adresi ve URL web hizmeti

Hızlı OFFICE 365 adresi ve URL web hizmeti, ağ trafiğini daha iyi tanımlamanıza ve ayırt Office 365 yardımcı olarak, değişiklikleri değerlendirmenizi, yapılandırmanızı ve güncel olarak takip edin. Bu REST tabanlı web hizmeti, 2 Ekim 2018'de aşamalı olarak zaman aşamalı olarak bulunan önceki XML indirilebilir dosyalarının yerini almaktadır.

Müşteri veya ağ çevre cihazı satıcısı olarak, IP adresi ve FQDN girdileri oluşturmak Office 365 web hizmetine karşı hazır bulabilirsiniz. Şu URL'leri kullanarak verilere doğrudan web tarayıcısında erişebilirsiniz:

- Url'leri ve IP adresi Office 365 en son sürümü için, kullanın[https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Güvenlik duvarları ve ara sunucular Office 365 URL'ler ve IP adresi aralıkları sayfasındaki veriler için, bunu kullanın[https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Web hizmeti ilk kez kullanılabilir olduğunda Temmuz 2018'den bu yana yapılan en son değişikliklerin hepsini almak için , kullanın [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

Bir müşteri olarak bu web hizmetini kullanarak şunları yapmak için kullanabilirsiniz:

- Uç nokta verilerini almak ve ağ cihazlarınız için Office 365 biçimlendirmelerini değiştirmek için PowerShell betiklerinizi güncelleştirin.
- İstemci bilgisayarlarına dağıtılan PAC dosyalarını güncelleştirmek için bu bilgileri kullanın.

Ağ çevre cihazı satıcısı olarak bu web hizmetini kullanarak şunları yapmak için kullanabilirsiniz:

- Otomatik yapılandırma için listeyi indirmek için cihaz yazılımını oluşturun ve test edin.
- Geçerli sürümü denetleme.
- Geçerli değişiklikleri almak.

> [!NOTE]
> Office 365'a bağlanmak için Azure ExpressRoute kullanıyorsanız, Azure ExpressRoute üzerinden desteklenen Office 365 Office 365 hizmetleri hakkında bilgi sahibi olmak için Office 365 Azure [ExpressRoute'u](azure-expressroute.md) gözden geçirmeniz gerekir. Ayrıca, internet bağlantısı [Office 365 ağ isteklerini anlamak için URL'ler ve IP](urls-and-ip-address-ranges.md) Office 365 aralıkları makalesini gözden geçirebilirsiniz. Bu, çevre güvenlik cihazlarınızı daha iyi yapılandırmanıza yardımcı olur.

Daha fazla bilgi için bkz.:

- [teknoloji forumunda duyuru Office 365 blog Community gönderisi](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [Office 365 hizmetlerinin Community hakkında sorular için Teknik Destek Forumu](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>Ortak parametreler

Bu parametreler tüm web hizmeti yöntemlerinde ortaktır:

- **format=\<JSON \| CSV\>** —Varsayılan olarak, JSON biçiminde veri döndürülür. Verileri virgülle ayrılmış değerler (CSV) biçiminde geri dönmek için bu isteğe bağlı parametreyi kullanın.
- **ClientRequestId=\<guid\>** —İstemci ilişkilendirmesi için oluşturulan, gerekli GUID. Web hizmetini çağıran her makine için benzersiz bir GUID üretin (bu sayfada yer alan betikler sizin için bir GUID üretir). Aşağıdaki örneklerde gösterilen GUID'leri kullanmayın çünkü bunlar gelecekte web hizmeti tarafından engellenmiş olabilir. GUID _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_ biçimindedir; burada x, onaltılık bir sayıdır.

  GUID oluşturmak için [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) PowerShell komutunu veya Çevrimiçi GUID Oluşturucu gibi bir [çevrimiçi hizmet kullanabilirsiniz](https://www.guidgenerator.com/).

## <a name="version-web-method"></a>Sürüm web yöntemi

Microsoft, Office 365 başında yeni IP adresi ve FQDN girdilerini günceller. Destek olayları, güvenlik güncelleştirmeleri veya diğer işlem gereksinimleri nedeniyle bazen bant dışında güncelleştirmeler yayımlanır.

Yayımlanan her örneğin verilerine bir sürüm numarası atanır ve sürüm web yöntemi, her bir Office 365 hizmetinin en son sürümünü denetlemenize olanak sağlar. Sürümü saatte bir kereden fazla denetlemenizi öneririz.

Sürüm web yönteminin parametreleri:

- **AllVersions=\<true \| false\>** —Varsayılan olarak, en son sürüm döndürülür. Web hizmeti ilk yayımlanır bu yana tüm yayımlanan sürümlerin isteğinde etmek için bu isteğe bağlı parametreyi dahil edin.
- **Format=\<JSON \| CSV \| RSS\>** —JSON ve CSV biçimlerine ek olarak, sürüm web yöntemi RSS'yi de destekler. Bu isteğe bağlı parametreyi _AllVersions=true_ parametresiyle birlikte kullanarak, diğer RSS okuyucularıyla veya diğer RSS okuyucularıyla Outlook RSS akışı isteyebilirsiniz.
- **Instance=\<Worldwide \| China \| Germany \| USGovDoD \| USGovGCCHigh\>** —Bu isteğe bağlı parametre, sürümün getirile örneklerini belirtir. Atlanırsa, tüm örnekler döndürülür. Geçerli örnekler: Worldwide, Çin, Almanya, USGovDoD, USGovGCCHigh.

Sürüm web yöntemi oranı sınırlı değildir ve 429 HTTP Yanıt Kodları'nın hiç bir zaman geri dönmez. Sürüm web yönteminin yanıtı, 1 saat süreyle verilerin önbelleğe alınmasını öneren bir önbellek denetimi başlığı içerir. Sürüm web yönteminden elde edilen sonuç tek bir kayıt veya bir kayıt dizisi olabilir. Her kaydın öğeleri:

- instance—En iyi hizmet Office 365 adı.
- latest—Belirtilen örneğin uç noktaları için en son sürüm.
- versions—Belirtilen örneğin önceki tüm sürümlerinin listesi. Bu öğe yalnızca _AllVersions parametresi doğruysa_ dâhil edilir.

### <a name="version-web-method-examples"></a>Sürüm web yöntemi örnekleri

Örnek 1 istek URI'si: <https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Bu URI, her bir hizmet örneğinin Office 365 sürümünü döndürür. Örnek sonuç:

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
 },
 {
  "instance": "Germany",
  "latest": "2018063000"
 }
]
```

> [!IMPORTANT]
> Bu  URL'lerde ClientRequestID parametresinin GUID değeri yalnızca örnek olarak ve vere. Web hizmeti  URL'lerini denemek için, kendi GUID değerinizi üretin. Bu örneklerde gösterilen GUID'ler, gelecekte web hizmeti tarafından engellenmiş olabilir.

Örnek 2 istek URI'si: <https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Bu URI, belirtilen hizmet örneğinin en Office 365 döndürür. Örnek sonuç:

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

Bu URI, dünya çapında bir hizmet örneğinin yayımlanmış tüm Office 365 sürümleri gösterir. Örnek sonuç:

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

Bu URI, yayımlanan sürümlerin, her sürümün değişiklik listesine bağlantılar içeren bir RSS akışı gösterir. Örnek sonuç:

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

Uç noktalar web yöntemi, en iyi hizmette yer alan IP adresi aralıkları ve URL'ler için Office 365 döndürür. Uç noktalar web yönteminden gelen en son veriler her zaman ağ cihazı yapılandırması için kullanılmalıdır. Microsoft, erişim denetim listelerini ve ara sunucu atlama listelerini güncelleştirmek için size zaman vermek için, yeni eklemeleri yayımlamadan 30 gün önce önceden bildirim sağlar. Yalnızca sürüm web yöntemi verilerin yeni bir sürümünün kullanılabilir olduğunu gösteriyor olduğunda, uç noktalar web yöntemini yeniden çağırmanız önerilir.

Uç noktalar web yönteminin parametreleri:

- **ServiceAreas=\<Common \| Exchange \| SharePoint \| Skype\>** —Hizmet alanlarının virgülle ayrılmış listesi. Geçerli _öğeler Yaygın,_ Ortak, _Exchange_, _SharePoint_ _ve Skype_. Ortak _hizmet_ alanı öğeleri diğer tüm hizmet alanlarının önkoşulları olduğundan, web hizmeti bunları her zaman içerir. Bu parametreyi dahil değilken tüm hizmet alanları döndürülür.
- **TenantName=\<tenant_name\>** —Kiracı Office 365 adınız. Web hizmeti sağlanan adını alır ve URL'lerin kiracı adını içeren bölümlerine ekler. Kiracı adı sağlayasanız bile, URL'lerin bu bölümleri joker karaktere () sahiptir\*.
- **NoIPv6=\<true \| false\>** —Ağda IPv6 _kullanmayacaksanız_ , çıktıdan IPv6 adreslerini hariç tutmak için değeri doğru olarak ayarlayın.
- **Instance=\<Worldwide \| China \| Germany \| USGovDoD \| USGovGCCHigh\>** —Bu gerekli parametre, uç noktaların hangi örnekten getir mu olduğunu belirtir. Geçerli örnekler: _Worldwide_, _Çin_, _Almanya_, _USGovDoD_ ve _USGovGCCHigh_.

Uç noktalar web yöntemini aynı istemci IP adresinden birçok kez çağırıyorsanız, HTTP yanıt kodu _429(Çok Fazla İstek) alırsınız_. Bu yanıt kodunu aldıysanız, isteğinizi yinelemeden önce 1 saat bekleyin veya istek için yeni bir GUID üretin. Genel bir en iyi uygulama olarak, yalnızca sürüm web yöntemi yeni bir sürümün kullanılabilir olduğunu gösteriyorsa uç noktalar web yöntemini çağırabilirsiniz.

Uç noktalar web yönteminden elde edilen sonuç, her kaydın belirli bir uç nokta kümesi temsil ettiği bir kayıt dizisidir. Her kaydın öğeleri:

- id—Uç nokta kümesi değişmez kimlik numarası.
- serviceArea— Bunun parçası olduğu hizmet alanı: _Ortak_, _Genel, Exchange_, _SharePoint_ veya _Skype_.
- urls—uç nokta kümesi için URL'ler. DNS kayıtlarının JSON dizisi. Boşsa atlanır.
- tcpPorts—uç nokta kümesi için TCP bağlantı noktaları. Tüm bağlantı noktası öğeleri, tire karakteriyle (-) birbirinden ayrılmış bağlantı noktalarının veya bağlantı noktası aralıklarının virgülle ayrılmış listesi olarak biçimlendirildi. Bağlantı noktaları, verilen bir kategori için uç nokta kümesinde tüm IP adreslerinde ve tüm URL'lerde geçerlidir. Boşsa atlanır.
- udpPorts—Bu uç nokta kümesinde IP adresi aralıkları için UDP bağlantı noktaları. Boşsa atlanır.
- ips —Listelenen TCP veya UDP bağlantı noktalarıyla ilişkilendirilmiş olan bu uç nokta kümesiyle ilişkilendirilmiş IP adresi aralıkları. IP adresi aralıklarının JSON dizisi. Boşsa atlanır.
- category—Uç nokta kümesi için bağlantı kategorisi. Geçerli değerler En İyi _Duruma Getirme_, _İzin Ver ve_ _Varsayılan'dır_. Belirli bir IP adresinin veya URL'nin kategorisi için uç noktalar web yöntemi çıktısını aratırsanız, sorgunuz birden çok kategori geri dönecektir. Böyle bir durumda, en yüksek öncelik kategorisi önerisini izleyin. Örneğin, uç nokta hem En İyi Duruma Getirme hem de İzin _Ver'de_ _görünüyorsa_, En İyi Duruma Getirme gereksinimlerini _izleyebilirsiniz_. Gerekli.
- expressRoute — _Bu uç_ nokta kümesi ExpressRoute üzerinden yönlendirildiyse _True, yönlendirme_ yoksa Yanlış.
- required — _Destek_ olmak için bu uç nokta kümesi bir bağlantı Office 365 doğru. _Bu_ uç nokta kümesi isteğe bağlı ise False.
- notes—İsteğe bağlı uç noktaları için, bu metin Office 365 uç nokta kümesinde IP adreslerine veya URL'lere ağ katmanında erişilenene kadar kullanılamayacak tüm veri işlevselliğini açıklar. Boşsa atlanır.

### <a name="endpoints-web-method-examples"></a>Uç noktalar web yöntemi örnekleri

Örnek 1 istek URI'si: <https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Bu URI, tüm iş yükleri için dünya çapında Office 365 için tüm uç noktaları sağlar. Çıkışta bir alıntının yer alan örnek sonuç:

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

Bu örnekteki isteğin tam çıktısı başka uç nokta kümeleri içerebilir.

Örnek 2 istek URI'si: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp; ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Bu örnekte, yalnızca kimlik ve bağımlılıklar Office 365 Dünya Çapında örneğinin Exchange Online uç noktaları elde edilir.

Örneğin 2, 1. örneğin çıkışına benzer, ancak sonuçlar SharePoint Online veya Skype Kurumsal Online uç noktalarını içermez.

## <a name="changes-web-method"></a>Değişiklikler web yöntemi

Değişiklikler web yöntemi yayımlanmış olan en son güncelleştirmeleri, ip adresi aralıkları ve URL'lerde bir önceki ayın değişikliklerini döndürür.

Uç nokta verilerinde en kritik değişiklikler yeni URL'ler ve IP adresleridir. Güvenlik duvarı erişim denetim listesine veya proxy sunucusu atlama listesine bir URL'nin eklen hatası, bu ağ aygıtının arkasında çalışan kullanıcıların Office 365 kesintiye neden olabilir. İşlem gereksinimlerine bakamasa da, yeni uç noktalar, erişim denetim listelerini ve ara sunucu atlama listelerini güncelleştirmek için size zaman vermek üzere uç noktaların sağlandık tarihten 30 gün önce web hizmetine yayımlanır.

Değişiklikler web yöntemi için gereken parametre:

- **Version=\<YYYYMMDDNN>** —Gerekli URL yönlendirme parametresi. Bu değer, şu anda uygulaymış olduğunuz sürümdür. Web hizmeti, bu sürümden itibaren değişiklikleri geri dönecektir. _YYYYAADNN_ biçimindedir; burada _NN_, tek gün içinde yayımlanacak birden çok sürüm varsa her sürümün yayımlanacak olmasıyla bir gün için _ilk güncelleştirmeyi temsil eden 00_ ile artırılır. Web hizmeti, sürüm _parametresinin tam_ olarak 10 basamak içermesini gerektirir.

Değişiklikler web yöntemi, uç noktalar web yöntemiyle aynı şekilde sınırlıdır. 429 HTTP yanıt kodu alırsanız, isteğinizi yinelemeden önce 1 saat bekleyin veya istek için yeni bir GUID üretin.

Değişiklikler web yönteminden elde edilen sonuç, her kaydın belirli bir uç nokta sürümündeki bir değişikliği temsil ettiği bir kayıt dizisidir. Her kaydın öğeleri:

- id—Değişiklik kaydının değişmez kimliği.
- endpointSetId—Değiştirilmiş olan uç nokta kümesi kaydının kimliği.
- disposition—Uç nokta kümesi kaydında yapılan değişikliği açıklar. Değerler _değişir,_ _ekler veya_ _kaldırır_.
- etki—Tüm değişiklikler her ortam için eşit derecede önemli olmaz. Bu öğe, bu değişiklik sonucunda kurumsal ağ çevre ortamı üzerindeki beklenen etkiyi açıklar. Bu öğe yalnızca sürüm ve sonraki sürümlerde **2018112800** dahildir. Etkiyi etkileyen seçenekler şunlardır: — AddedIp – IP adresi Office 365 ve kısa süre sonra hizmette yayınlanacak. Bu, bir güvenlik duvarında veya başka bir katman 3 ağ çevre cihazında almak için gereken değişikliği temsil eder. Bunu kullanmaya başlamadan önce ekleyemeyysiniz, kesintiyle karşınıza çıkabilirsiniz.
  — AddedUrl – URL Office 365 ve yakında hizmette yayınlanacak. Bu, ara sunucu veya URL'de ağ çevre cihazı ayrıştırma için gereken bir değişikliği temsil eder. Bu URL'yi kullanmaya başlamadan önce ekleyemeyebilirsiniz; kesintiyle de karşınıza çıkabilirsiniz.
  — AddedIpAndUrl—Ip adresi ve URL'nin her ikisi de eklenmiştir. Bu, güvenlik duvarı katmanı 3 cihazı veya ara sunucu ya da URL ayrıştırma cihazı üzerinde almak istediğiniz değişikliği temsil eder. Kullanmaya başlamadan önce bu IP/URL çiftini ekleyemeyebilirsiniz.
  — RemovedIpOrUrl – Siteden en az bir IP adresi veya URL Office 365. Çevre cihazlarından ağ uç noktalarını kaldırın, ancak bunu yapmak için son tarih yoktur.
  — ChangedIsExpressRoute – ExpressRoute destek özniteliği değiştirilmiştir. ExpressRoute kullanıyorsanız, yapılandırmanıza bağlı olarak bir işlem yapmak zorundaysanız.
  — MovedIpOrUrl – Bu uç nokta kümesi ile başka bir uç nokta kümesi arasında bir IP adresi veya URL taşıdık. Genelde herhangi bir işlem gerekmez.
  — RemovedDuplicateIpOrUrl – Yinelenen IP adresini veya Url'yi kaldırdık ancak hala IP adresi için Office 365. Genelde herhangi bir işlem gerekmez.
  — OtherNonPriorityChanges – Not alanının içeriği gibi diğer tüm seçeneklerden daha az kritik olan bir değişiklik yaptık.
- version—Değişikliğin tanıt olduğu yayımlanmış uç nokta kümesi sürümü. Sürüm numaraları _YYYYAADNN_ biçimindedir; burada _NN_ , aynı gün içinde birden çok sürümün yayım olması gerektiğinde her sürüm için bir artırılır doğal bir sayıdır.
- previous—Uç nokta kümesi üzerinde değiştirilmiş ögelerin önceki değerlerinin ayrıntılarına ayrıntılarıyla bir alt yapı. Yeni eklenen uç nokta kümelerine bu dâhil olmaz. _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ ve _notları içerir_.
- current—Uç nokta kümesinde değişiklik öğelerinin güncelleştirilmiş değerlerinin ayrıntılarını ayrıntılarıylaen bir alt yapı. _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ ve _notları içerir_.
- add —Uç nokta kümesi koleksiyonlarına eklenecek olan öğelerin ayrıntılarıyla ilgili bir alt yapı. Ekleme yoksa atlanır.
  — effectiveDate—Eklemelerin hizmette ne zaman canlı olacağını tanımlar.
  — ips— _ips_ dizisine eklenecek öğeler.
  — urls - _urls_ dizisine eklenecek öğeler.
- remove—Uç nokta kümesinden kaldırılacak olan öğelerin ayrıntılarıyla ilgili bir alt yapı. Kaldırma işlemi yoksa atlanır.
  — ips— _ips diziden kaldırılacak_ öğeler.
  — urls - _urls diziden kaldırılacak_ öğeler.

### <a name="changes-web-method-examples"></a>Değişiklikler web yöntemi örnekleri

Örnek 1 istek URI'si: <https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Bu, dünya çapında bir hizmet örneğinde Office 365 yapılan tüm değişiklikleri talep etmektedir. Örnek sonuç:

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

Bu, Office 365 Worldwide örneğinde belirtilen sürümden bu yana yapılan değişiklikleri talep ediyor. Bu durumda, belirtilen sürüm en son sürümüdür. Örnek sonuç:

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

Güncelleştirilmiş veriler için başka işlemler de gerçekleştirebilir ve bu eylemleri görmek için bu PowerShell betiği çalıştırabilirsiniz. Sürüm güncelleştirmesini kontrol etmek için bu betiği zamanlanmış görev olarak çalıştırebilirsiniz. Web hizmetine aşırı yük yüklemesini önlemek için betiği saatte birden çok çalıştırmamaya deneyin.

Betik şunları yapar:

- Web hizmeti REST API'sini çağırarak Office 365 Dünya Çapında örnek uç noktalarının sürüm numarasını denetler.
- Geçerli sürüm dosyasını $Env:TEMP\O365_endpoints_latestversion.txt _._ $Env **:TEMP genel değişkeninin** yolu genellikle _C:\Users\\<kullanıcıadı\>\AppData\Local\Temp yolundadır_.
- Betiği ilk kez çalıştırıyorsanız, betik geçerli sürümü ve tüm geçerli IP adreslerini ve URL'leri döndürür, _$Env:TEMP\O365_endpoints_latestversion.txt_ dosyasına uç nokta sürümünü ve _$Env:TEMP\O365_endpoints_data.txt_ dosyasına uç nokta veri çıkışı yazar. Şu satırları düzenleyerek çıkış dosyasının yolunu ve/veya adını değiştirebilirsiniz:

    ``` powershell
    $versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
    $datapath = $Env:TEMP + "\O365_endpoints_data.txt"
    ```

- Betiğin sonraki her yürütülmesinde, en son web hizmeti sürümü _O365_endpoints_latestversion.txt_ dosyasındaki sürümle aynısa, betik herhangi bir değişiklik yapmadan çıkar.
- En son web hizmeti sürümü _O365_endpoints_latestversion.txt_ dosyasının sürümünden daha yeni olduğunda, betik, izin ver ve En İyi Duruma Getir kategorisi uç noktalarının uç noktalarını  ve filtrelerini döndürür, _O365_endpoints_latestversion.txt_ dosyasındaki sürümü güncelleştirilir ve güncelleştirilmiş verileri _O365_endpoints_data.txt_ dosyasına yazar.

Betik, yürütülen bilgisayar için benzersiz bir _ClientRequestId_ üretir ve bu kimliği birden çok çağrıda yeniden verir. Bu kimlik, _O365_endpoints_latestversion.txtdepolanır._

### <a name="to-run-the-powershell-script"></a>PowerShell betiği çalıştırmak için

1. Betiği kopyalayın ve yerel sabit sürücünize veya betik konumunuzla aynı _Get-O365WebServiceUpdates.ps1_.
1. Tercih ettiğiniz betik düzenleyicisinde (PowerShell ISE veya VS Code) ya da aşağıdaki komutu kullanarak betiği bir PowerShell konsolundan yürütün:

    ``` powershell
   powershell.exe -file <path>\Get-O365WebServiceUpdates.ps1
    ```

    Betikle geçecek parametre yok.

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

Burada, güncelleştirilmiş veriler için başka eylemler gerçekleştirebilir veya çalıştırabilirsiniz; bu betik Windows 10 üzerinde Python 3.6.3 ile test edilmiş bir Python betiğidir. Bu betik, dünya çapında örnek uç noktalarının Office 365 numarasını denetler. Bir değişiklik olduğunda, uç noktaları ve İzin Ver ve En İyi Duruma Getirme kategori _uç noktalarının_ filtrelerini indirir. Ayrıca, birden çok çağrıda bulunan benzersiz ClientRequestId dosyasını kullanır ve bulunan en son sürümü geçici bir dosyaya kaydeder. Sürüm güncelleştirmesini kontrol etmek için bu betiği saatte bir çağır.

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

## <a name="web-service-interface-versioning"></a>Web Hizmeti arabirimi sürümü

Gelecekte bu web hizmeti yöntemlerinin parametrelerinde veya sonuçlarında güncelleştirmeler yapmak gerekebilir. Bu web hizmetlerinin genel kullanılabilirlik sürümü yayımlandıktan sonra, Microsoft web hizmeti için önemli güncelleştirmeleri önceden bildirim sağlamak için makul çabayı tamamlar. Microsoft bir güncelleştirmenin web hizmetini kullanan istemcilerde değişiklik yapmak gerektir olduğuna inandığında, yeni sürümün piyasaya çıkışlarından sonraki en az 12 ay boyunca web hizmetinin bir önceki sürümünü (bir sürüm geri) kullanmaya devam ettir. Bu süre içinde yükseltme yapmayan müşteriler web hizmetine ve bu hizmetin yöntemlerine erişe edemler. Web hizmeti arabirimi imzalarında aşağıdaki değişiklikler yapılırsa, müşteriler web hizmeti istemcilerinin hatasız çalışmaya devam edecektir:

- Var olan bir web yöntemine, daha eski istemciler tarafından sağlanmalıdır ve daha eski istemcilerin aldığı sonuçları etkilemeden isteğe bağlı yeni bir parametre ekleme.
- Yanıt REST öğelerinin veya diğer sütunlardan birlarına yanıt CSV'sinde yeni bir adlandırılmış öznitelik ekleme.
- Yeni bir adla, eski istemciler tarafından çağrıl yer alan yeni bir web yöntemi ekleme.

## <a name="update-notifications"></a>Bildirimleri güncelleştirme

IP adreslerinde ve URL'lerde yapılan değişiklikler web hizmetine yayımlanırken e-posta bildirimleri almak için birkaç farklı yöntem kullanabilirsiniz.

- Daha iyi bir Power Automate için bkz. IP Adreslerinde [ve URL'lerde Power Automate e-posta Office 365 e-posta alma](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).
- Azure Logic App'i bir ARM şablonu kullanarak dağıtmak için bkz. Office 365 [Bildirimi (v1.1)](https://aka.ms/ipurlws-updates-template).
- PowerShell kullanarak kendi bildirim betiğinizi yazmak için bkz. [Send-MailMessage](/powershell/module/microsoft.powershell.utility/send-mailmessage).

## <a name="exporting-a-proxy-pac-file"></a>Ara Sunucu PAC dosyasını dışarı aktarma

[Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile), Office 365 IP Adresi ve URL web hizmetinin en son ağ uç noktalarını okur ve örnek bir PAC dosyası oluşturan bir PowerShell betiğidir. Get-PacFile kullanma hakkında bilgi için önemli ve önemli trafiğin doğrudan yönlendiri [için PAC dosyası Office 365 bakın](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic).

## <a name="related-topics"></a>İlgili Konular
  
[Office 365 URL'leri ve IP adresi aralıkları](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[Kullanıcı Office 365 yönetme](managing-office-365-endpoints.md)
  
[Office 365 uç noktaları hakkında SSS](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[Office 365 Bağlantısı İlkeleri](microsoft-365-network-connectivity-principles.md)

[Office 365 ve performans ayarını yapılandırma](network-planning-and-performance.md)

[Ağ Office 365 değerlendirme](assessing-network-connectivity.md)
  
[Skype Kurumsal Online'da Medya Kalitesi ve Ağ Bağlantısı Performansı](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Skype Kurumsal Online için a Skype Kurumsal iyileştirme](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[Office 365 ve performans geçmişini kullanarak performans ayarlamayı ayarlama](performance-tuning-using-baselines-and-history.md)
  
[Destek için performans sorunlarını giderme Office 365](performance-troubleshooting-plan.md)
