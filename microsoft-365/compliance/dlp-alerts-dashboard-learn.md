---
title: Veri kaybı önleme Uyarılar panosu hakkında bilgi
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
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Veri kaybı önleme uyarıları ve uyarılar panosu hakkında bilgi edinebilirsiniz.
ms.openlocfilehash: 375b16a3072f40ef8f366f7c1c4e8f714f195d63
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990021"
---
# <a name="learn-about-the-data-loss-prevention-alerts-dashboard"></a>Veri kaybı önleme Uyarılar panosu hakkında bilgi

Veri kaybı önleme (DLP) ilkesinde yer alan ölçütler, kullanıcının hassas bir öğeyi üzerinde edte olduğu eylemlerle eşlenince, ilke bir uyarıya neden olabilir. Bu durum yüksek düzeyde uyarılara neden olabilir. DLP uyarıları, uyarılar panosunda toplanır. Uyarılar panosu, ilke eşleşmesi hakkında tüm ayrıntılar için ayrıntılı inceleme yapmak için size tek bir yer sağlar.  

<!-- [Microsoft 365 compliance center](https://compliance.microsoft.com/)-->

## <a name="workloads"></a>İş Yükleri

[DLP uyarı yönetimi panosu](https://compliance.microsoft.com/datalossprevention?viewid=dlpalerts), aşağıdaki <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a> iş yüklerinde DLP ilkelerine yönelik uyarıları gösterir:

- Exchange
- SharePoint
- OneDrive
- Teams
- Windows 10 cihazları 

> [!TIP]
> Uç Nokta [DLP'sini](endpoint-dlp-learn-about.md) kullanan ve [Teams DLP](dlp-microsoft-teams.md) için uygun olan müşteriler, uç nokta DLP ilkesi uyarılarını ve DLP uyarı yönetim panosunda Teams DLP ilkesi uyarılarını görebilirler.

## <a name="single-alert-and-aggregate-alert"></a>Tek uyarı ve toplam uyarı

DLP ilkelerinde yapılandırılan iki tür uyarı vardır.

**Tek olaylı** uyarılar genellikle, kurum dışına 10 veya daha fazla müşteri kredi kartı numarası gönderilen tek bir e-posta gibi düşük hacimli çok hassas etkinlikleri izlemek için kullanılan ilkelerde kullanılır.

**Toplama olayı uyarıları** normalde belirli bir süre boyunca daha yüksek hacimde oluşan olayları izleyenin ilkelerde kullanılır. Örneğin, her biri bir müşteri kredi kartı numarasına sahip 10 ayrı e-posta 48 saat içinde kuruluş dışında gönderlendiğinde bir toplam uyarı tetiklenir.

## <a name="types-of-events"></a>Etkinlik türleri

Uyarıyla ilişkilendirilmiş olaylardan bazıları burada ve şekildedir. Kullanıcı arabiriminde, ayrıntılarını görüntülemek için belirli bir olayı seçebilirsiniz. 

### <a name="event-details"></a>Olay ayrıntıları

|Özellik adı  |Açıklama  |Olay türleri  |
|---------|---------|---------|
|Kimlik |olayla ilişkilendirilmiş benzersiz kimlik |tüm etkinlikler |
|Konum |olayın algılandığında iş yükü|tüm etkinlikler |
|etkinlik zamanı     |DLP ilkesi ölçütlerine uyan kullanıcı etkinliğinin zamanı |

### <a name="affected-entities"></a>Etkilenen varlıklar

|Özellik adı |Açıklama| Olay türleri|
|---------|---------|---------|
|kullanıcı | ilkenin eşleşmesına neden olan eylemi yapan kullanıcı | tüm etkinlikler|
|ana bilgisayar adı | DLP ilkesi eşleşmesi yapılan bilgisayarın ana bilgisayar adı | cihaz olayları|
|IP adresi | DLP ilkesi eşleşmesi yapılan bilgisayarın IP adresi | cihaz olayları|
|sha1 |Dosyanın SHA-1 karması | cihaz olayları|
|sha256 | Dosyanın SHA-256 karması | cihaz olayları|
|MDATP cihaz kimliği | uç nokta cihazı MDATP Kimliği|
|dosya boyutu | dosyanın boyutu| SharePoint, OneDrive olaylarını ve cihaz olaylarını gösterir|
|dosya yolu | DLP ilkesi eşleşmesine dahil olan öğenin mutlak yolu | SharePoint, OneDrive ve cihaz olaylarını geri|
|alıcıları e-postayla gönderme |E-posta, DLP ilkesiyle eşleşmeye duyarlı bir öğe ise, bu alan o e-postanın alıcılarını içerir| Exchange etkinlikleri|
|e-posta konusu |DLP ilkesiyle eşleşmeye neden olan e-postanın konusu |Exchange etkinlikleri|
|e-posta ekleri | E-postada yer alan ve DLP ilkesiyle eşleşmeye neden olan eklerin adları| Exchange etkinlikleri|
|site sahibi |site sahibinin adı| SharePoint ve OneDrive hakkında|
|site URL'si |DLP ilkesi eşleşmesinin bulunduğu SharePoint veya OneDrive sitesinin URL'si ile dolu |SharePoint ve OneDrive hakkında|
|oluşturulan dosya |DLP ilkesiyle eşleşmeye neden olan dosyanın oluşturulma zamanı |SharePoint ve OneDrive hakkında|
|son değiştirilen dosya | DLP ilkesiyle eşleşmeye neden olan dosyanın en son değiştirii | SharePoint ve OneDrive hakkında|
|dosya boyutu | DLP ilkesiyle eşleşmeye uygun dosyanın boyutu |SharePoint ve OneDrive hakkında|
|dosya sahibi |DLP ilkesiyle eşleşmeye sahip dosyanın sahibi |SharePoint ve OneDrive hakkında|  

### <a name="policy-details"></a>İlke ayrıntıları

|Özellik adı |Açıklama |Olay türleri |
|---------|---------|---------|
|DLP ilkesi eşleşmeli |eşleşmeli DLP ilkesi adı |tüm etkinlikler|
|eşanlı kural |eşanlı DLP ilke kuralının adı |tüm etkinlikler|
|hassas bilgi türleri (SIT) algılandı|DLP ilkesi eşleşmesi kapsamında algılanan SITS'ler |tüm etkinlikler|
|yapılan eylemler |DLP ilkesiyle eşleşmeye neden olan eylemler| tüm etkinlikler|
|ihlal eden eylem | DLP uyarılarını yükselten uç nokta cihazı eylemi| cihaz olayları | 
|kullanıcı overrode policy |kullanıcı ilkeyi bir ilke ipucu aracılığıyla geçersiz k oldu mu | tüm etkinlikler|
|geçersiz kılma yaslama kullanma |Geçersiz kılma için kullanıcı tarafından sağlanan neden metni | tüm etkinlikler|   

## <a name="see-also"></a>Ayrıca Bkz

- [Veri kaybı önleme uyarı panosuna başlama](dlp-alerts-dashboard-get-started.md)
- [Veri kaybını önleme ile başlama](create-test-tune-dlp-policy.md#where-to-start-with-data-loss-prevention)
