---
title: Office 365 için Microsoft Defender'da düzeltme Office 365
keywords: AIR, autoIR, Uç Nokta için Microsoft Defender, otomatik, araştırma, yanıt, düzeltme, tehdit, gelişmiş, tehdit, koruma
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Microsoft Defender'daki otomatik soruşturmayı takip eden düzeltme eylemleri hakkında bilgi Office 365.
ms.date: 04/30/2021
ms.custom:
- air
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5435c063234c2b803e172d6cdc06ff0b9bf417b2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312327"
---
# <a name="remediation-actions-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'da düzeltme Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Office 365 için Microsoft Defender plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="remediation-actions"></a>Düzeltme eylemleri

Microsoft [Defender'daki Tehdit koruması Office 365](defender-for-office-365.md) bazı düzeltme eylemleri içerir. Bu düzeltme eylemleri şunları içerebilir:

- E-posta iletilerini veya kümelerini yumuşak silme
- URL'yi engelleme (tıklama zamanı)
- Dış posta iletmeyi kapatma
- Temsilci seçmeyi kapatma

Düzeltme eylemleri Microsoft Office 365'de düzeltme eylemleri otomatik olarak gerçekleştirlanmaz. Bunun yerine, düzeltme işlemleri yalnızca kuruluşun güvenlik işlemleri ekibinin onayıyla  alınır.

## <a name="threats-and-remediation-actions"></a>Tehditler ve düzeltme eylemleri

Microsoft Defender For Office 365 çeşitli tehditlere yönelik düzeltme eylemleri içerir. Otomatik soruşturmalar genellikle gözden geçirip onaylamanız gereken bir veya birden çok düzeltme eylemiyle sonuçlanmaz. Bazı durumlarda, otomatik bir araştırma belirli bir düzeltme eylemiyle sonuçlanmaz. Daha fazla araştırma yapmak ve uygun eylemleri yapmak için aşağıdaki tabloda yer alan kılavuzu kullanın.

|Kategori|Tehdit/risk|Düzeltme eylemi|
|:---|:---|:---|
|E-posta|Kötü amaçlı yazılım|E-postayı/kümeyi yumuşak silme <p> Kümede bulunan birkaç e-posta iletisinde kötü amaçlı yazılım varsa, kümenin kötü amaçlı olduğu kabul edilir.|
|E-posta|Kötü amaçlı URL <br> (Bağlantılar arasında kötü amaçlı bir URL [Kasa algılandı](safe-links.md).)|E-postayı/kümeyi yumuşak silme <br> URL'yi engelleme (tıklama süresi doğrulama) <p> Kötü amaçlı URL içeren e-postaların kötü amaçlı olduğu kabul edilir.|
|E-posta|Kimlik avı|E-postayı/kümeyi yumuşak silme <p> Kümede yer alan birkaç e-posta iletisinde kimlik avı girişimleri varsa, tüm küme bir kimlik avı girişimi olarak kabul edilir.|
|E-posta|Zapped phish <br> (E-posta iletileri teslim edildi ve [ardından zapped.](zero-hour-auto-purge.md))|E-postayı/kümeyi yumuşak silme <p> Raporlar, zapped iletileri görüntülemek için kullanılabilir. [ZAP'ın bir iletiyi ve SSS'yi taşınana bakın](zero-hour-auto-purge.md#how-to-see-if-zap-moved-your-message).|
|E-posta|Kullanıcı tarafından bildirilen [cevapsız kimlik](enable-the-report-message-add-in.md) avı e-postası|[Kullanıcının raporu tarafından tetiklenen otomatik soruşturma](automated-investigation-response-office.md#example-a-user-reported-phish-message-launches-an-investigation-playbook)|
|E-posta|Hacimli anormal <br> (Son e-posta miktarları eşleşen ölçütler için önceki 7-10 günü aşıyor.)|Otomatik soruşturma belirli bir bekleyen eylemle sonuçlanmaz. <p>Hacim anormalliği net bir tehdit değildir, ancak son 7-10 günlere göre son zamanlarda daha büyük e-posta hacimlerinin göstergesidir. <p>E-postanın yüksek hacimli olması olası sorunları gösteriyor olsa da, kötü amaçlı kararlardan veya e-posta iletilerinin/kümelerinin el ile gözden geçirmesi açısından onay gerekir. Bkz [. Teslim edilen şüpheli e-postaları bulma](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered).|
|E-posta|Tehdit bulunamadı <br> (Sistem dosyalara, URL'lere veya e-posta kümesi kararlarının çözümlemelerine dayalı herhangi bir tehdit bulamadı.)|Otomatik soruşturma belirli bir bekleyen eylemle sonuçlanmaz. <p>Bir soruşturma [tamamlandıktan sonra](zero-hour-auto-purge.md) bulunan ve eşlenen tehditlere, araştırmanın sayısal bulgularına yansıtılmaz, ancak tehditlere [Tehdit Gezgini'nde bakılabilir](threat-explorer.md).|
|Kullanıcı|Kullanıcı kötü amaçlı bir URL'ye tıkladı <br> (Bir kullanıcı daha sonra kötü amaçlı olduğu bulunan bir sayfaya giti veya bir kullanıcı kötü amaçlı bir sayfaya gitmek için [Kasa](safe-links.md#warning-pages-from-safe-links) Bağlantılar uyarı sayfasını atlar.)|Otomatik soruşturma belirli bir bekleyen eylemle sonuçlanmaz. <p> URL'yi engelleme (tıklama zamanı) <p> Tehdit Gezgini'ni [kullanarak URL'ler ile ilgili verileri görüntüleyin ve kararlara tıklayın](threat-explorer.md#view-phishing-url-and-click-verdict-data). <p> Organizasyonunız Uç Nokta için [Microsoft Defender'ı kullanıyorsa](/windows/security/threat-protection/), hesabın güvenliği ihlal edilmiş olup olmadığını belirlemek için kullanıcıyı incelemeniz iyi olabilir.[](/microsoft-365/security/defender-endpoint/investigate-user)|
|Kullanıcı|Kullanıcı kötü amaçlı yazılım/kimlik avı gönderiyor|Otomatik soruşturma belirli bir bekleyen eylemle sonuçlanmaz. <p> Kullanıcı kötü amaçlı yazılım/kimlik avı bildiriyor veya bir [saldırının parçası olarak kullanıcıya](anti-spoofing-protection.md) kimlik sahtesi bildiriyor olabilir. Kötü [amaçlı yazılım veya kimlik](threat-explorer.md) avı içeren e-postaları görüntülemek ve işlemek için [Tehdit Gezgini'ni](threat-explorer-views.md#email--malware) [kullanın](threat-explorer-views.md#email--phish).|
|Kullanıcı|E-posta iletme <br> (Posta kutusu iletme kuralları yapılandırılmıştır, veri kaynağında chch kullanılabilir.)|Yönlendirme kuralını kaldırma <p> [İletili e-posta](mail-flow-insights-v2.md) hakkında daha [ayrıntılı bilgi görüntülemek için Otomatik İletiler](mfi-auto-forwarded-messages-report.md) iletileri raporu da dahil olmak üzere posta akışı içgörülerini kullanın.|
|Kullanıcı|E-posta temsilcisi kuralları <br> (Kullanıcının hesabında temsilciler ayarlanmıştır.)|Temsilci kuralını kaldırma <p> Organizasyonunız Uç Nokta için [Microsoft Defender'ı kullanıyorsa](/windows/security/threat-protection/), temsilci [izni](/microsoft-365/security/defender-endpoint/investigate-user) alan kullanıcıyı incelemeniz iyi olabilir.|
|Kullanıcı|Veri filtreleme <br> (Bir kullanıcı e-postayı veya dosya paylaşımı [DLP ilkelerini ihlal etti](../../compliance/dlp-learn-about-dlp.md) |Otomatik soruşturma belirli bir bekleyen eylemle sonuçlanmaz. <p> [DLP raporlarını görüntüleme ve önlem alma](../../compliance/view-the-dlp-reports.md).|
|Kullanıcı|Anormal e-posta gönderme <br> (Bir kullanıcı yakın zamanda önceki 7-10 günlere göre daha fazla e-posta gönderdi.)|Otomatik soruşturma belirli bir bekleyen eylemle sonuçlanmaz. <p> Büyük miktarda e-posta göndermek tek başına kötü amaçlı değildir; Kullanıcı yalnızca etkinlik için büyük bir alıcı grubuna e-posta gönderi olabilir. Neler olup olmadığını belirlemek [ve önlem almak](mail-flow-insights-v2.md) için posta [akış](mfi-mail-flow-map-report.md) haritası raporu dahil olmak üzere posta akışı içgörülerini kullanın.|

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'da otomatik bir soruşturmanın ayrıntılarını ve sonuçlarını Office 365](air-view-investigation-results.md)
- [İş için Microsoft Defender'da otomatik bir incelemeden sonra bekleyen veya tamamlanmış düzeltme eylemlerini Office 365](air-review-approve-pending-completed-actions.md)

## <a name="related-articles"></a>İlgili makaleler

- [Uç Nokta için Microsoft Defender'da otomatik araştırma hakkında bilgi](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)
- [E-Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)
