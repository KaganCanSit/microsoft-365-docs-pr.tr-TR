---
title: Web koruması
description: Uç Nokta için Microsoft Defender'da web koruması ve kuruluşunuzu nasıl koruyabileceği hakkında bilgi edinin
keywords: web koruması, web tehdit koruması, web gözatma, güvenlik, kimlik avı, kötü amaçlı yazılım, yararlanma, web siteleri, ağ koruması, Edge, Internet Explorer, Chrome, Firefox, web tarayıcısı, kötü amaçlı web siteleri
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
ms.openlocfilehash: 4184948316e683a59b45b9397aaea74260e290ee
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664182"
---
# <a name="web-protection"></a>Web koruması

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)


## <a name="about-web-protection"></a>Web koruması hakkında

Uç Nokta için Microsoft Defender'de [web koruması, Web tehdit koruması](web-threat-protection.md), [Web içeriği filtreleme](web-content-filtering.md) ve [Özel göstergelerden oluşan bir özelliktir](manage-indicators.md). Web koruması, cihazlarınızı web tehditlerine karşı korumanıza olanak tanır ve istenmeyen içeriği düzenlemenize yardımcı olur. Web koruması raporlarını Microsoft 365 Defender portalında **Raporlar > Web koruması'na** giderek bulabilirsiniz.

:::image type="content" source="images/web-protection.png" alt-text="Web koruma kartları" lightbox="images/web-protection.png":::

### <a name="web-threat-protection"></a>Web tehdit koruması

Web tehdit korumasını oluşturan kartlar **, zaman içindeki Web tehdit algılamaları** ve **Web tehdit özetidir**.

Web tehdit koruması şunları içerir:

- Kuruluşunuzu etkileyen web tehditlerine yönelik kapsamlı görünürlük.
- Uyarılar ve bu URL'lere erişen cihazların kapsamlı profilleri ve uyarılar aracılığıyla web ile ilgili tehdit etkinlikleri üzerinde araştırma özellikleri.
- Kötü amaçlı ve istenmeyen web sitelerine genel erişim eğilimlerini izleyen tam bir güvenlik özellikleri kümesi.

Daha fazla bilgi için bkz [. Web tehdit koruması](web-threat-protection.md).

### <a name="custom-indicators"></a>Özel göstergeler

Özel gösterge algılamaları, zaman içindeki Web tehdit algılamaları ve Web tehdit özeti altındaki kuruluşlarınızdaki **web tehdit raporlarında** da **özetlenir**.

Özel gösterge şunları içerir:

- Kuruluşunuzu tehditlere karşı korumak için IP ve URL tabanlı risk göstergeleri oluşturma olanağı.
- Özel IP/URL profilleriniz ve bu URL'lere erişen cihazlarla ilgili etkinlikler üzerinde araştırma özellikleri.
- IP'ler ve URL'ler için İzin Ver, Engelle ve Uyar ilkeleri oluşturma özelliği.

Daha fazla bilgi için bkz [. IP'ler ve URL'ler/etki alanları için gösterge oluşturma](indicator-ip-domain.md)

### <a name="web-content-filtering"></a>Web içeriği filtreleme

Web içeriği filtreleme **kategoriye göre Web etkinliğini**, **Web içeriği filtreleme özetini** ve **Web etkinliği özetini** içerir.

Web içeriği filtreleme şunları içerir:

- Kullanıcıların, ister şirket içinde ister dışarıda gezinirken engellenen kategorilerdeki web sitelerine erişmeleri engellenir.
- Çeşitli ilkeleri, [Uç Nokta için Microsoft Defender rol tabanlı erişim denetimi ayarlarında](/microsoft-365/security/defender-endpoint/rbac) tanımlanan cihaz gruplarını kullanarak çeşitli kullanıcı kümelerine kolayca dağıtabilirsiniz.
- Gerçek bloklar ve web kullanımı üzerinde görünürlük ile web raporlarına aynı merkezi konumdan erişebilirsiniz.

Daha fazla bilgi için bkz [. Web içeriği filtreleme](web-content-filtering.md).

## <a name="order-of-precedence"></a>Öncelik sırası

Web koruması, öncelik sırasına göre listelenen aşağıdaki bileşenlerden oluşur. Bu bileşenlerin her biri Microsoft Edge'daki SmartScreen istemcisi ve diğer tüm tarayıcılarda ve işlemlerde Ağ Koruması istemcisi tarafından zorlanır.

- Özel göstergeler (IP/URL, Microsoft Defender for Cloud Apps ilkeleri)
  - İzin ver
  - Uyarmak
  - Engelle

- Web tehditleri (kötü amaçlı yazılım, kimlik avı)
  - Exchange Online Protection (EOP) dahil olmak üzere SmartScreen Intel
  - Escalations

- Web İçeriği Filtreleme (WCF)

> [!NOTE]
> Microsoft Defender for Cloud Apps şu anda yalnızca engellenen URL'ler için göstergeler oluşturur.

Öncelik sırası, URL veya IP'nin değerlendirildiği işlemlerin sırasıyla ilgilidir. Örneğin, bir web içeriği filtreleme ilkeniz varsa özel IP/URL göstergeleri aracılığıyla dışlamalar oluşturabilirsiniz. Özel Risk Göstergeleri (IoC), öncelik sırasına göre WCF bloklarından daha yüksektir.

Benzer şekilde, göstergeler arasındaki bir çakışma sırasında bloklardan (geçersiz kılma mantığı) her zaman öncelikli olmasına izin verir. Bu, bir izin göstergesinin mevcut olan tüm blok göstergelerini kazanacağı anlamına gelir.

Aşağıdaki tabloda, web koruma yığını içinde çakışmalar ortaya koyabilecek bazı yaygın yapılandırmalar özetlenmiştir. Ayrıca, yukarıda listelenen önceliğe göre elde edilen belirlemeleri tanımlar.

<br>

****

|Özel Gösterge ilkesi|Web tehdit ilkesi|WCF ilkesi|Bulut için Defender Uygulamaları ilkesi|Sonuç|
|---|---|---|---|---|
|İzin ver|Engelle|Engelle|Engelle|İzin Ver (Web koruması geçersiz kılma)|
|İzin ver|İzin ver|Engelle|Engelle|İzin Ver (WCF özel durumu)|
|Uyarmak|Engelle|Engelle|Engelle|Uyar (geçersiz kıl)|
|

İç IP adresleri özel göstergeler tarafından desteklenmez. Son kullanıcı tarafından atlanan bir uyarı ilkesi için sitenin engeli varsayılan olarak 24 saat boyunca kaldırılır. Bu zaman dilimi Yönetici tarafından değiştirilebilir ve SmartScreen bulut hizmeti tarafından geçirilir. Web tehdit blokları (kötü amaçlı yazılım/kimlik avı) için CSP kullanılarak Microsoft Edge bir uyarıyı atlama özelliği de devre dışı bırakılabilir. Daha fazla bilgi için bkz. [SmartScreen Ayarlar Microsoft Edge](/DeployEdge/microsoft-edge-policies#smartscreen-settings-policies).

## <a name="protect-browsers"></a>Tarayıcıları koruma

Tüm web koruma senaryolarında, SmartScreen ve Ağ Koruması hem birinci hem de üçüncü taraf tarayıcılarda ve işlemlerde koruma sağlamak için birlikte kullanılabilir. SmartScreen doğrudan Microsoft Edge yerleşik olarak bulunurken, Ağ Koruması üçüncü taraf tarayıcılarda ve işlemlerde trafiği izler. Aşağıdaki diyagramda bu kavram gösterilmektedir. Birden çok tarayıcı/uygulama kapsamı sağlamak için birlikte çalışan iki istemcinin bu diyagramı, Web Koruması'nın tüm özellikleri (Göstergeler, Web Tehditleri, İçerik Filtreleme) için doğrudur.

:::image type="content" source="../../media/web-protection-protect-browsers.png" alt-text="smartScreen ve Ağ Koruması'nın birlikte kullanımı" lightbox="../../media/web-protection-protect-browsers.png":::

## <a name="troubleshoot-endpoint-blocks"></a>Uç nokta blokları sorunlarını giderme

SmartScreen bulutundan gelen yanıtlar standartlaştırılmıştır. Fiddler gibi araçlar bulut hizmetinden gelen yanıtı incelemek için kullanılabilir ve bu da bloğun kaynağını belirlemeye yardımcı olur.

SmartScreen bulut hizmeti bir izin verme, engelleme veya uyarı yanıtıyla yanıt verdiği zaman, yanıt kategorisi ve sunucu bağlamı istemciye geri iletilir. Microsoft Edge'da yanıt kategorisi, gösterilecek uygun blok sayfasını belirlemek için kullanılan kategoridir (kötü amaçlı, kimlik avı, kuruluş ilkesi).

Aşağıdaki tabloda yanıtlar ve bunların bağıntılı özellikleri gösterilmektedir.

<br>

****

|ResponseCategory|Blok için sorumlu özellik|
|---|---|
|CustomPolicy|WCF|
|CustomBlockList|Özel göstergeler|
|CasbPolicy|Bulut Uygulamaları için Defender|
|Kötü amaçlı|Web tehditleri|
|Kimlik Avı|Web tehditleri|
|||

## <a name="advanced-hunting-for-web-protection"></a>Web koruması için gelişmiş avcılık

Gelişmiş avcılıktaki Kusto sorguları, kuruluşunuzdaki web koruma bloklarını 30 güne kadar özetlemek için kullanılabilir. Bu sorgular, çeşitli blok kaynaklarını ayırt etmek ve bunları kullanıcı dostu bir şekilde özetlemek için yukarıda listelenen bilgileri kullanır. Örneğin, aşağıdaki sorguda Microsoft Edge kaynaklı tüm WCF blokları listelenmiştir.

```kusto
DeviceEvents
| where ActionType == "SmartScreenUrlWarning"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, Experience=tostring(ParsedFields.Experience)
| where Experience == "CustomBlockList"
```

Benzer şekilde, Ağ Koruması'ndan kaynaklanan tüm WCF bloklarını listelemek için aşağıdaki sorguyu kullanabilirsiniz (örneğin, üçüncü taraf tarayıcıdaki bir WCF bloğu). ActionType'ın güncelleştirildiğini ve 'Experience' öğesinin 'ResponseCategory' olarak değiştirildiğini unutmayın.

```kusto
DeviceEvents
| where ActionType == "ExploitGuardNetworkProtectionBlocked"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, ResponseCategory=tostring(ParsedFields.ResponseCategory)
| where ResponseCategory == "CustomPolicy"
```

Diğer özelliklerden (Özel Göstergeler gibi) kaynaklanan blokları listelemek için yukarıdaki her özelliğin ve ilgili yanıt kategorilerinin ana hatlarını oluşturan tabloya bakın. Bu sorgular, kuruluşunuzdaki belirli makinelerle ilgili telemetriyi aramak için de değiştirilebilir. Yukarıdaki her sorguda gösterilen ActionType'ın yalnızca Bir Web Koruması özelliği tarafından engellenen bağlantıları göstereceğini ve tüm ağ trafiğini göstermeyeceğini unutmayın.

## <a name="user-experience"></a>Kullanıcı deneyimi

Kullanıcı kötü amaçlı yazılım, kimlik avı veya diğer web tehditleri riski olan bir web sayfasını ziyaret ederse, Microsoft Edge tehditle ilgili bilgilerle birlikte "Bu site güvenli değil olarak bildirildi" yazan bir blok sayfası tetikler.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/web-protection-malicious-block.png" alt-text="Microsoft Edge tarafından engellenen sayfa" lightbox="../../media/web-protection-malicious-block.png":::

WCF veya özel bir gösterge tarafından engellenirse, Microsoft Edge kullanıcıya bu sitenin kendi kuruluşu tarafından engellendiğini bildiren bir blok sayfası gösterilir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/web-protection-indicator-blockpage.png" alt-text="Kuruluşunuz tarafından engellenen sayfa" lightbox="../../media/web-protection-indicator-blockpage.png":::

Her durumda, üçüncü taraf tarayıcılarda hiçbir blok sayfası gösterilmez ve kullanıcı bir bildirimle birlikte "Güvenli Bağlantı Başarısız Oldu" sayfasını görür. Engellemeden sorumlu ilkeye bağlı olarak, bir kullanıcı bildirimde farklı bir ileti görür. Örneğin, web içeriği filtrelemesi 'Bu içerik engellendi' iletisini görüntüler.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/web-protection-np-block.png" alt-text="WCF tarafından engellenen sayfa" lightbox="../../media/web-protection-np-block.png":::

## <a name="report-false-positives"></a>Hatalı pozitif sonuçları bildirme

SmartScreen tarafından tehlikeli kabul edilen sitelerde hatalı pozitif rapor vermek için, Microsoft Edge'deki blok sayfasında görünen bağlantıyı kullanın (yukarıda gösterildiği gibi).

WCF için, bir etki alanının kategorisine itiraz edebilirsiniz. WCF raporlarının **Etki Alanları** sekmesine gidin ve Rapor **Yanlışlığı'na** tıklayın. Açılır öğe açılır. Olayın önceliğini ayarlayın ve önerilen kategori gibi bazı ek ayrıntıları sağlayın. WCF'yi açma ve anlaşmazlık kategorileri hakkında daha fazla bilgi için bkz. [Web içeriği filtreleme](web-content-filtering.md).

Hatalı pozitif/negatifleri gönderme hakkında daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender'de hatalı pozitif/negatifleri adresle](defender-endpoint-false-positives-negatives.md).

## <a name="related-information"></a>İlgili bilgiler

<br>

****

|Konu|Açıklama|
|---|---|
|[Web tehdit koruması](web-threat-protection.md) | Kimlik avı sitelerine, kötü amaçlı yazılım vektörlerine, güvenlik açığından yararlanma sitelerine, güvenilmeyen veya saygınlığı düşük sitelere ve engellediğiniz sitelere erişimi durdurun.|
|[Web içeriği filtreleme](web-content-filtering.md) | Web sitelerine erişimi içerik kategorilerine göre izleyin ve düzenleyin.|
|
