---
title: Web koruması
description: Web koruması hakkında bilgi edinmek Uç Nokta için Microsoft Defender ve organizasyonlarınızı nasıl koruyasını öğrenin
keywords: web koruması, web tehdit koruması, web'e gözatma, güvenlik, kimlik avı, kötü amaçlı yazılım, açıkları kullanma, web siteleri, ağ koruması, Edge, Internet Explorer, Chrome, Firefox, web tarayıcısı, kötü amaçlı web siteleri
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 7883ef4c7bc06c08e199af871902b26d8e46ac5e
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476587"
---
# <a name="web-protection"></a>Web koruması

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)


## <a name="about-web-protection"></a>Web koruması hakkında

Web Uç Nokta için Microsoft Defender, Web tehdit koruması, [Web](web-threat-protection.md) içeriği filtreleme ve Özel [göstergelerden yararlanan](web-content-filtering.md) [bir özelliktir](manage-indicators.md). Web koruması, cihazlarınızı web tehditlerine karşı korumanızı sağlar ve istenmeyen içeriği düzenlemenize yardımcı olur. Web koruma raporlarını Web koruması için raporlar Microsoft 365 Defender Portalı'**> bulabilirsiniz**.

:::image type="content" source="images/web-protection.png" alt-text="Web koruma kartları" lightbox="images/web-protection.png":::

### <a name="web-threat-protection"></a>Web tehdit koruması

Web tehdit korumasını neden olan kartlar, **zamanla Web tehdit algılamaları ve** Web tehdit **özetidir**.

Web tehdit koruması şunları içerir:

- Web tehditlerine karşı kapsamlı görünürlük, organizasyonlarınızı etkiler.
- Web ile ilgili tehdit etkinlikleri üzerinden, URL'lerin ve bu URL'lere erişen cihazların kapsamlı profilleri yoluyla soruşturma özellikleri.
- Kötü amaçlı ve istenmeyen web sitelerine genel erişim eğilimlerini takip etmek için eksiksiz bir güvenlik özellikleri kümesi.

Daha fazla bilgi için bkz [. Web tehdit koruması](web-threat-protection.md).

### <a name="custom-indicators"></a>Özel göstergeler

Özel gösterge algılamaları, zaman içinde Web tehdit algılamaları ve **Web** tehdit özeti altında, kuruluşlarınız için web tehdit raporları da **özetlenmiştir**.

Özel gösterge şunları içerir:

- Organizasyonlarınızı tehditlere karşı korumak için IP ve URL tabanlı güvenlik göstergeleri oluşturabilme.
- Özel IP/URL profilleriniz ve bu URL'lere erişen cihazlarla ilgili etkinlikler üzerinde araştırma özellikleri.
- URL'ler ve URL'ler için İzin Ver, Engelle ve Uyar ilkeleri oluşturabilme özelliği.

Daha fazla bilgi için bkz [. IP'ler ve URL'ler/etki alanları için göstergeler oluşturma](indicator-ip-domain.md)

### <a name="web-content-filtering"></a>Web içeriği filtreleme

Web içeriği filtreleme, **kategoriye göre Web etkinliği**, **Web içeriği filtreleme özeti** ve Web etkinliği **özeti içerir**.

Web içeriği filtreleme şunları içerir:

- İster şirket içinde ister uzakta olsunlar, kullanıcıların engellenen kategorilerde web sitelerine erişimi engellenir.
- Rol tabanlı erişim denetimi ayarlarında tanımlanan cihaz gruplarını kullanarak çeşitli kullanıcı [gruplarına Uç Nokta için Microsoft Defender ilkeler dağıtabilirsiniz](/microsoft-365/security/defender-endpoint/rbac).
- Gerçek bloklar ve web kullanımıyla ilgili görünürlükle, web raporlarına aynı merkezi konumdan erişebilirsiniz.

Daha fazla bilgi için bkz [. Web içeriği filtreleme](web-content-filtering.md).

## <a name="order-of-precedence"></a>Öncelik sırası

Web koruması, öncelik sırasına göre listelenen aşağıdaki bileşenlerden oluşur. Bu bileşenlerin her biri, Microsoft Edge'de SmartScreen istemcisi ve diğer tüm tarayıcılarda ve işlemlerde Ağ Koruma istemcisi tarafından zorunlu kılındı.

- Özel göstergeler (IP/URL, Microsoft Defender for Cloud Apps ilkeleri)
  - İzin ver
  - Uyar
  - Engelle

- Web tehditleri (kötü amaçlı yazılım, kimlik avı)
  - SmartScreen Intel, Exchange Online Protection (EOP) dahil
  - Yükseltmeler

- Web İçeriği Filtreleme (WCF)

> [!NOTE]
> Microsoft Defender for Cloud Apps durumda yalnızca engellenen URL'ler için göstergeler üretir.

Öncelik sırası, bir URL veya IP'nin değerlendirilen işlemlerin sırasıyla ilgilidir. Örneğin, web içeriği filtreleme ilkeniz varsa, özel IP/URL göstergeleri aracılığıyla dışlamalar oluşturabilirsiniz. Özel güvenlik göstergeleri (IoC) öncelik sırası WCF bloklarına göre daha yüksektir.

Benzer şekilde, göstergeler arasındaki bir çakışma sırasında her zaman bloklara göre öncelik (mantığını geçersiz kılma) izin verir. Bu, bir izin göstergesinin mevcut olan engelleme göstergelerine göre kazanılamayacak anlamına gelir.

Aşağıdaki tabloda, web koruma yığını içinde çakışmalar sunacak bazı yaygın yapılandırmalar özetlenmiştir. Ayrıca, yukarıda listelenen öncelikleri temel alarak elde edilen belirlemeleri de tanımlar.

<br>

****

|Özel Gösterge ilkesi|Web tehdit ilkesi|WCF ilkesi|Bulut için Defender Uygulamaları ilkesi|Sonuç|
|---|---|---|---|---|
|İzin ver|Engelle|Engelle|Engelle|İzin Ver (Web korumasını geçersiz kıl)|
|İzin ver|İzin ver|Engelle|Engelle|İzin Ver (WCF özel durumu)|
|Uyar|Engelle|Engelle|Engelle|Uyar (geçersiz kıl)|
|

İç IP adresleri özel göstergeler tarafından desteklenmiyor. Son kullanıcı tarafından atlayan bir uyarı ilkesi için, site varsayılan olarak bu kullanıcı için 24 saat boyunca engeli kaldırır. Bu zaman dilimi Yönetici tarafından değiştirilebilir ve SmartScreen bulut hizmeti tarafından geçirir. Web tehdit blokları (kötü amaçlı yazılım/kimlik avı) için CSP kullanılarak uyarı Microsoft Edge atlanma özelliği de devre dışı bırakılabilir. Daha fazla bilgi için [SmartScreen Microsoft Edge'ya Ayarlar](/DeployEdge/microsoft-edge-policies#smartscreen-settings-policies).

## <a name="protect-browsers"></a>Tarayıcıları koruma

Tüm web koruma senaryolarında, hem birinci hem de üçüncü taraf tarayıcılarda ve süreçlerde koruma sağlamak için SmartScreen ve Ağ Koruması birlikte kullanılabilir. SmartScreen doğrudan Web üzerinde yerleşik Microsoft Edge, Ağ Koruması ise üçüncü taraf tarayıcılarda ve işlemlerde trafiği izler. Aşağıdaki diyagramda bu kavram gösterilmiştir. Birden çok tarayıcı/uygulama kapsamı sağlamak için birlikte çalışan iki istemcinin bu diyagramı, Web Koruma'nın tüm özellikleri (Göstergeler, Web Tehditleri, İçerik Filtreleme) için doğrudur.

:::image type="content" source="../../media/web-protection-protect-browsers.png" alt-text="SmartScreen ve Ağ Koruması'nın birlikte kullanımı" lightbox="../../media/web-protection-protect-browsers.png":::

## <a name="troubleshoot-endpoint-blocks"></a>Uç nokta bloklarının sorunlarını giderme

SmartScreen bulutundan gelen yanıtlar standartlaştırıldı. Fiddler gibi araçlar, bloğun kaynağını belirlemeye yardımcı olan bulut hizmetinin yanıtını incelemek için kullanılabilir.

SmartScreen bulut hizmeti yanıt verme, engelleme veya uyarı yanıtı ile yanıt verdiği zaman, yanıt kategorisi ve sunucu bağlamı istemciye geri döner. Daha Microsoft Edge kategorisi, gösterecek uygun blok sayfasını (kötü amaçlı, kimlik avı, kuruluş ilkesi) belirlemek için kullanılan yanıt kategorisidir.

Aşağıdaki tabloda yanıtlar ve onun ilişkili özellikleri gösterilmiştir.

<br>

****

|ResponseCategory|Engelden sorumlu olan özellik|
|---|---|
|CustomPolicy|WCF|
|CustomBlockList|Özel göstergeler|
|CasbPolicy|Bulut Uygulamaları için Defender|
|Kötü Amaçlı|Web tehditleri|
|Kimlik Avı|Web tehditleri|
|||

## <a name="advanced-hunting-for-web-protection"></a>Web koruması için gelişmiş av

Kusto 30 gün boyunca gelişmiş aramalarda web koruma bloklarını özetlemek için kullanılabilir. Bu sorgular, çeşitli bloklar kaynaklarını ayırt etmek ve bunları kullanıcı dostu bir şekilde özetlemek için yukarıda listelenen bilgileri kullanır. Örneğin, aşağıdaki sorguda bu kayıttan kaynaklanan tüm WCF Microsoft Edge.

```kusto
DeviceEvents
| where ActionType == "SmartScreenUrlWarning"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, Experience=tostring(ParsedFields.Experience)
| where Experience == "CustomBlockList"
```

Benzer şekilde, Ağ Koruması'dan (örneğin, üçüncü taraf bir tarayıcıda WCF bloğu) kaynaklanan tüm WCF bloklarını liste için aşağıdaki sorguyu kullanabilirsiniz. ActionType'ın güncelleştirildiğini ve 'Deneyim'in 'ResponseCategory' olarak değiştirdiğini unutmayın.

```kusto
DeviceEvents
| where ActionType == "ExploitGuardNetworkProtectionBlocked"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, ResponseCategory=tostring(ParsedFields.ResponseCategory)
| where ResponseCategory == "CustomPolicy"
```

Diğer özelliklerden (Özel Göstergeler gibi) dolayı olan bloklar listesi oluşturmak için, her özelliğin ve bunların ilgili yanıt kategorisinin vurgularını oluşturmada yukarıdaki tabloya bakın. Bu sorgular, aynı zamanda organizasyonlu belirli makinelerle ilgili telemetri aramak için de değiştirilebilir. Yukarıdaki her sorguda gösterilen ActionType türü yalnızca Web Koruma özelliği tarafından engellenen bağlantıları gösterir; tüm ağ trafiğini değil.

## <a name="user-experience"></a>Kullanıcı deneyimi

Kullanıcı kötü amaçlı yazılım, kimlik avı veya diğer web tehditlerine neden olan bir web sayfasını ziyaret ettiyse, Microsoft Edge 'Bu site güvenli değil olarak bildirildi' ifadesinin bulunduğu bir blok sayfası ve tehditle ilgili bilgileri tetikler.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/web-protection-malicious-block.png" alt-text="Sayfa Microsoft Edge" lightbox="../../media/web-protection-malicious-block.png":::

WCF tarafından veya özel bir göstergeyle engellenirse, Microsoft Edge kullanıcıya bu sitenin kendi kuruluşu tarafından engellenmiş olduğunu söyleyen bir blok sayfası görüntülenir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/web-protection-indicator-blockpage.png" alt-text="Kuruluş tarafından engellenen sayfa" lightbox="../../media/web-protection-indicator-blockpage.png":::

Her durumda, üçüncü taraf tarayıcılarda hiçbir engelleme sayfası gösterilmez ve kullanıcı bir uyarı bildirimiyle birlikte 'Güvenli Bağlantı Başarısız' sayfasını görür. Engellemeden sorumlu olan ilkeye bağlı olarak, kullanıcı bildirim bildiriminde farklı bir ileti görebilir. Örneğin, web içeriği filtreleme 'Bu içerik engellendi' iletisi görüntülenir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/web-protection-np-block.png" alt-text="WCF tarafından engellenen sayfa" lightbox="../../media/web-protection-np-block.png":::

## <a name="report-false-positives"></a>Hatalı pozitif sonuç bildir

SmartScreen tarafından tehlikeli olduğu kabulilen siteler için hatalı pozitif bir sonuç rapor etmek için, smartScreen'de blok sayfasında (yukarıda gösterildiği gibi) Microsoft Edge bağlantıyı kullanın.

WCF'de, bir etki alanının kategorisine itirazabilirsiniz. WCF **raporlarının** Etki Alanları sekmesine gidin ve ardından **Rapor Inaccuracy'ye tıklayın**. Açılır bir açılır. Olayın önceliğini ayarlayın ve önerilen kategori gibi bazı ek ayrıntılar sağlar. WCF'nin nasıl aç haberleri ve ihtilaf kategorileri hakkında daha fazla bilgi için bkz [. Web içeriği filtreleme](web-content-filtering.md).

Hatalı pozitif/negatifleri gönderme hakkında daha fazla bilgi için bkz. Hatalı pozitif[/negatifleri](defender-endpoint-false-positives-negatives.md) Uç Nokta için Microsoft Defender.

## <a name="related-information"></a>İlgili bilgiler

<br>

****

|Konu|Açıklama|
|---|---|
|[Web tehdit koruması](web-threat-protection.md) | Kimlik avı sitelerine, kötü amaçlı yazılım vektörlerine, açıklarından yararlanma sitelerine, güvenilmeyen veya itibarsız sitelere ve engellemiş olduğunuz sitelere erişimi durdurun.|
|[Web içeriği filtreleme](web-content-filtering.md) | Web sitelerine erişimi içerik kategorilerine göre izleyebilir ve düzenler.|
|
