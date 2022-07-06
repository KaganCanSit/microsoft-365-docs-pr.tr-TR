---
title: DLP uyarıları panosu hakkında bilgi edinin
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
description: Veri kaybı önleme uyarıları ve uyarılar panosu hakkında bilgi edinin.
ms.openlocfilehash: 1551b247e3302af6dc8ed9af62a88f2c24415122
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636171"
---
# <a name="learn-about-the-data-loss-prevention-alerts-dashboard"></a>Veri kaybı önleme Uyarılar panosu hakkında daha fazla bilgi edinme

Microsoft Purview Veri Kaybı Önleme (DLP) ilkesindeki ölçütler, kullanıcının hassas bir öğe üzerinde yaptığı eylemlerle eşleştiğinde, ilke uyarı oluşturabilir. Bu durum yüksek miktarda uyarıya neden olabilir. DLP uyarıları uyarılar panosunda toplanır. Uyarılar panosu, ilke eşleşmesi hakkındaki tüm ayrıntıları ayrıntılı olarak araştırmak için tek bir yer sağlar.  

<!-- [Microsoft Purview compliance portal](https://compliance.microsoft.com/)-->

## <a name="workloads"></a>İş yükleri

[DLP uyarı yönetimi panosu](https://compliance.microsoft.com/datalossprevention?viewid=dlpalerts), <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a> aşağıdaki iş yüklerindeki DLP ilkelerine yönelik uyarıları gösterir:

- Exchange
- SharePoint
- OneDrive
- Teams
- cihazları Windows 10 

> [!TIP]
> [Teams DLP'ye uygun Olan Uç Nokta DLP](endpoint-dlp-learn-about.md) kullanan müşteriler, DLP uyarı yönetimi panosunda uç nokta DLP ilkesi uyarılarını ve Teams DLP ilkesi uyarılarını görür.[](dlp-microsoft-teams.md)

## <a name="single-alert-and-aggregate-alert"></a>Tek uyarı ve toplu uyarı

DLP ilkelerinde yapılandırılabilir iki tür uyarı vardır.

**Tek olaylı uyarılar** genellikle kuruluşunuzun dışına gönderilen 10 veya daha fazla müşteri kredi kartı numarası içeren tek bir e-posta gibi düşük hacimli gerçekleşen son derece hassas olayları izleyen ilkelerde kullanılır.

**Toplama olayı uyarıları** genellikle belirli bir süre boyunca daha yüksek bir birimde gerçekleşen olayları izleyen ilkelerde kullanılır. Örneğin, her biri bir müşteri kredi kartı numarasına sahip 10 ayrı e-posta 48 saat içinde kuruluşunuzun dışına gönderildiğinde toplu bir uyarı tetiklenebilir.

## <a name="types-of-events"></a>Olay türleri

Bir uyarıyla ilişkili olaylardan bazıları aşağıdadır. Kullanıcı arabiriminde, ayrıntılarını görüntülemek için belirli bir olayı seçebilirsiniz. 

### <a name="event-details"></a>Olay ayrıntıları

|Özellik adı  |Açıklama  |Olay türleri  |
|---------|---------|---------|
|Kimlik |olayla ilişkili benzersiz kimlik |tüm olaylar |
|Konum |olayın algılandığı iş yükü|tüm olaylar |
|etkinlik zamanı     |DLP ilkesinin ölçütlerine uyan kullanıcı etkinliğinin zamanı |

### <a name="affected-entities"></a>Etkilenen varlıklar

|Özellik adı |Açıklama| Olay türleri|
|---------|---------|---------|
|Kullanıcı | ilke eşleşmesine neden olan eylemi gerçekleştiren kullanıcı | tüm olaylar|
|Hostname | DLP ilkesi eşleşmesinin gerçekleştiği bilgisayarın ana bilgisayar adı | cihaz olayları|
|IP adresi | DLP ilkesi eşleşmesinin gerçekleştiği bilgisayarın IP adresi | cihaz olayları|
|sha1 |Dosyanın SHA-1 karması | cihaz olayları|
|sha256 | Dosyanın SHA-256 karması | cihaz olayları|
|MDATP cihaz kimliği | uç nokta cihazı MDATP kimliği|
|dosya boyutu | dosyanın boyutu| SharePoint, OneDrive ve cihaz olayları|
|dosya yolu | DLP ilkesi eşleşmesiyle ilgili öğenin mutlak yolu | SharePoint, OneDrive ve cihazlar olayları|
|e-posta alıcıları |E-posta DLP ilkesiyle eşleşen hassas öğeyse, bu alan söz konusu e-postanın alıcılarını içerir| Exchange olayları|
|e-posta konusu |DLP ilkesiyle eşleşen e-postanın konusu |Exchange olayları|
|e-posta ekleri | E-postadaki DLP ilkesiyle eşleşen eklerin adları| Exchange olayları|
|site sahibi |site sahibinin adı| SharePoint ve OneDrive olayları|
|site URL'si |DLP ilkesi eşleşmesinin gerçekleştiği SharePoint veya OneDrive sitesinin URL'si ile dolu |SharePoint ve OneDrive olayları|
|dosya oluşturuldu |DLP ilkesiyle eşleşen dosyanın oluşturulma zamanı |SharePoint ve OneDrive olayları|
|dosya son değiştirme | DLP ilkesiyle eşleşen dosyanın son değiştirildiği zaman | SharePoint ve OneDrive olayları|
|dosya boyutu | DLP ilkesiyle eşleşen dosyanın boyutu |SharePoint ve OneDrive olayları|
|dosya sahibi |DLP ilkesiyle eşleşen dosyanın sahibi |SharePoint ve OneDrive olayları|  

### <a name="policy-details"></a>İlke ayrıntıları

|Özellik adı |Açıklama |Olay türleri |
|---------|---------|---------|
|DLP ilkesi eşleştirildi |eşleşen DLP ilkesinin adı |tüm olaylar|
|kural eşleştirildi |eşleşen DLP ilke kuralının adı |tüm olaylar|
|hassas bilgi türleri (SIT) algılandı|DLP ilkesi eşleşmesinin bir parçası olarak algılanan SID'ler |tüm olaylar|
|gerçekleştirilen eylemler |DLP ilkesi eşleşmesine neden olan eylemler| tüm olaylar|
|ihlal eylemi | DLP uyarısını tetikleyen uç nokta cihazında eylem| cihaz olayları | 
|kullanıcı overrode ilkesi |kullanıcı ilkeyi bir ilke ipucu aracılığıyla geçersiz k oldu mu? | tüm olaylar|
|geçersiz kılma gerekçesini kullanma |geçersiz kılma için kullanıcı tarafından sağlanan nedenin metni | tüm olaylar|   

## <a name="see-also"></a>Ayrıca Bkz

- [Veri kaybı önleme uyarı panosunu kullanmaya başlama](dlp-alerts-dashboard-get-started.md)
- [Veri kaybı önleme ile nereden başlanmalıdır?](create-test-tune-dlp-policy.md#where-to-start-with-data-loss-prevention)
