---
title: Office 365 için Microsoft Defender'da otomatik araştırma ve Office 365
keywords: AIR, autoIR, Uç Nokta için Microsoft Defender, otomatik, araştırma, yanıt, düzeltme, tehdit, gelişmiş, tehdit, koruma
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 01/29/2021
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Microsoft Defender'daki otomatik araştırma ve yanıt özelliklerini otomatik araştırma ve yanıt özelliklerini Office 365.
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 469a85866f722539c35bcc0305aa1e8fc39d58be
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021797"
---
# <a name="automated-investigation-and-response-air-in-microsoft-defender-for-office-365"></a>İş için Microsoft Defender'da otomatik araştırma ve yanıt (AIR) Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Güvenlik işlemleri için Microsoft Defender Office 365](defender-for-office-365.md), güvenlik işlemlerinin ekip zamanını ve çabasını kaydeden güçlü otomatik araştırma ve yanıt (AIR) özellikleri içerir. Uyarılar tetiklendiğinden, güvenlik işlemleri ekibinin bu uyarıları incelemesi, önceliklerini belirlemesi ve yanıtlaması daha doğru olur. Gelen uyarıların hacmini takip etmek bunaltıcı olabilir. Bu görevlerden bazılarının otomatik olarak otomatik olarak gerçekleştirilirsiniz.

AIR, güvenlik işlemleri ekibimizin daha verimli ve etkili bir şekilde çalışmasına olanak sağlar. AIR özellikleri, bugün var olan iyi bilinen tehditlere yanıt olarak otomatik soruşturma süreçleri içerir. Uygun düzeltme eylemleri onay bekliyor; bu da güvenlik işlemleri ekibimizin algılanan tehditlere etkili bir şekilde yanıt vermesini sağlar. AIR ile güvenlik işlemleri ekipleriniz tetiklenen önemli uyarıları gözden kaybetmeden yüksek öncelikli görevlere odaklanabilirsiniz.

Bu makalede şu açıklanmıştır:

- [AIR'in genel akışı](#the-overall-flow-of-air);
- [AIR'i nasıl elde olur](#how-to-get-air)? ve
- AIR [özelliklerini yapılandırmak](#required-permissions-to-use-air-capabilities) veya kullanmak için gerekli izinler.
- Çok yakında portalında gelecek Microsoft 365 Defender değişiklikler

Bu makale sonraki adımları [ve daha](#next-steps) fazla bilgi edinmek için kaynakları da içerir.

## <a name="the-overall-flow-of-air"></a>AIR'in genel akışı

Uyarı tetiklenir ve bir güvenlik çalışma kitabı otomatik bir araştırma başlatır ve bu da bulguların ve önerilen eylemlerle sonuç verir. İşte AIR'in genel akışı, adım adım:

1. Otomatik bir araştırma aşağıdaki yöntemlerden biri ile başlatılır:
   - [E-postada şüpheli bir şey](#which-alert-policies-trigger-automated-investigations) (ileti, ek, URL veya güvenliği tehlikeye kullanıcı hesabı gibi) bir uyarı tetiklenir. Bir olay oluşturulur ve otomatik bir soruşturma başlar; veya
   - Güvenlik analisti [, Explorer'ı kullanırken otomatik](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) bir araştırma [başlatır](threat-explorer.md).
2. Otomatik bir araştırma çalıştırıldığı sırada, söz konusu e-postayla ilgili e-posta ve varlıklar hakkında veri toplar. Bu tür varlıklar dosyaları, URL'leri ve alıcıları içerebilir. Yeni ve ilgili uyarılar tetiklendiğinde araştırmanın kapsamı artabilir.
3. Otomatik bir araştırma sırasında ve sonrasında, [ayrıntılar ve sonuçlar](air-view-investigation-results.md) görüntülemek için kullanılabilir. Sonuçlar, [bulunan tüm tehditlere](air-remediation-actions.md) yanıt vermek ve düzeltmek için gereksinen önerilen eylemleri içerir.
4. Güvenlik işlemleri ekipleriniz araştırma [sonuçlarını ve önerilerini inceler](air-view-investigation-results.md), düzeltme eylemlerini [onaylar veya reddeder](air-review-approve-pending-completed-actions.md).
5. Bekleyen düzeltme eylemleri onaylanır (veya reddedilir) gibi otomatik soruşturma tamamlanır.

Düzeltme için Microsoft Defender Office 365 düzeltme eylemleri otomatik olarak gerçekleştirnmedi. Düzeltme eylemleri yalnızca kuruluşun güvenlik ekibinin onayıyla  alınır. AIR özellikleri, düzeltme eylemlerini tanımarak ve bilinçli bir karar verecek ayrıntıları sağlayarak güvenlik işlemleri ekip sürenizi tasarrufu sağlar.

Her otomatik araştırma sırasında ve sonrasında, güvenlik işlemleri ekipleriniz şunları şunları tamamlar:

- [Bir soruşturmayla ilgili uyarının ayrıntılarını görüntüleme](air-view-investigation-results.md#view-details-about-an-alert-related-to-an-investigation)
- [Bir soruşturmanın sonuç ayrıntılarını görüntüleme](air-view-investigation-results.md#view-details-of-an-investigation)
- [Bir soruşturma sonucunda eylemleri gözden geçirme ve onaylama](air-review-approve-pending-completed-actions.md)

> [!TIP]
> Daha ayrıntılı bir genel bakış için bkz [. AIR nasıl çalışır](automated-investigation-response-office.md).

## <a name="how-to-get-air"></a>AIR'i nasıl almak için?

İlke ve uyarılarınız [yapılandırılmışsa AIR Office 365 Microsoft Defender](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) for Microsoft Defender'a dahildir. Yardıma mı ihtiyacınız var? Aşağıdaki koruma ayarlarını ayarlamak [veya yapılandırmak](protect-against-threats.md) için Tehditlere karşı koruma yönergelerini izleyin:

- [Denetim günlüğü](../../compliance/turn-audit-log-search-on-or-off.md) (açık olması gerekir)
- [Kötü amaçlı yazılımdan koruma](protect-against-threats.md#part-1---anti-malware-protection-in-eop)
- [Kimlik avı koruması](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
- [İstenmeyen posta önleme koruması](protect-against-threats.md#part-3---anti-spam-protection-in-eop)
- [Kasa ve Ekleri Kasa Kaydetme](protect-against-threats.md#part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365)

Buna ek olarak, özellikle [de Tehdit yönetimi kategorisindeki varsayılan ilkeler](../../compliance/alert-policies.md) olmak üzere, kuruluş uyarı [ilkelerini gözden geçirmeyi unutmayın](../../compliance/alert-policies.md#default-alert-policies).

## <a name="which-alert-policies-trigger-automated-investigations"></a>Hangi uyarı ilkeleri otomatik soruşturmaları tetikler?

Microsoft 365, yönetici izinlerinin kötüye kullanımı, kötü amaçlı yazılım etkinliği, olası dış ve iç tehditlere Exchange bilgi yönetimi risklerini belirlemeye yardımcı olan birçok yerleşik uyarı ilkeleri sağlar. Varsayılan uyarı [ilkelerinin birkaçı otomatik](../../compliance/alert-policies.md#default-alert-policies) soruşturmaları tetikler. Aşağıdaki tabloda otomatik soruşturmaları tetikleyen uyarılar, Microsoft 365 Defender portalında önem derecesi ve bunların nasıl oluşturulacakları açık almaktadır:

<br>

****

|Uyarı|Önem Derecesi|Uyarı nasıl oluşturulur?|
|---|---|---|
|Kötü amaçlı olabilecek bir URL tıklaması algılandı|**Yüksek**|Bu uyarı, aşağıdaki uyarılardan biri ortaya çıkar: <ul><li>E-posta bağlantıları [Kasa tarafından](safe-links.md) korunan bir kullanıcı kötü amaçlı bir bağlantıya tıklar</li><li>URL'ler için karar değişiklikleri Microsoft Defender tarafından Office 365</li><li>Kullanıcılar Bağlantılar Kasa sayfalarını geçersiz kılar (kuruluşun Bağlantılar ilkesine [Kasa göre](set-up-safe-links-policies.md)).</li></ul> <p> Bu uyarıyı tetikleyen olaylar hakkında daha fazla bilgi için bkz[. Kasa ayarlama](set-up-safe-links-policies.md).|
|Kullanıcı bir e-posta iletisi kötü amaçlı yazılım veya kimlik avı olarak bildiriliyor|**Bilgilendirme**|Bu uyarı, kuruluş kullanıcılarının Rapor İletisi eklentiyi veya Rapor Kimlik Avını Bildir eklentiyi kullanarak kimlik avı [e-postası](enable-the-report-message-add-in.md) olarak raporlalarına [geldiğinde oluşturulur](enable-the-report-phish-add-in.md).|
|Kötü amaçlı yazılım içeren e-posta iletileri teslimden sonra kaldırılır|**Bilgilendirme**|Bu uyarı, kötü amaçlı yazılım içeren tüm e-posta iletileri organizasyonu içeren posta kutularına teslim edilirken oluşturulur. Bu olay oluşursa, Microsoft sıfır saatlik otomatik temizleme (ZAP) Exchange Online posta kutularından etkilenen [iletileri kaldırır](zero-hour-auto-purge.md).|
|Kimlik avı URL'lerini içeren e-posta iletileri teslimden sonra kaldırılır|**Bilgilendirme**|Bu uyarı, kimlik avı içeren tüm iletiler kuruluş posta kutularına teslim edilirken oluşturulur. Bu olay oluşursa, Microsoft ZAP kullanan posta kutularına Exchange Online iletileri [kaldırır](zero-hour-auto-purge.md).|
|Şüpheli e-posta gönderme desenleri algılandı|**Orta**|Bu uyarı, kurumdan biri şüpheli e-posta gönderdiğinde ve e-posta göndermesi kısıtlanmışsa oluşturulur. Uyarı, hesabın güvenliği ihlal edilmiş ancak kullanıcının kısıtlanmaları için yeterince ciddi olmadığını belirten erken bir uyarıdır. <p> Nadiren de olsa, bu ilke tarafından oluşturulan bir uyarı anormal olabilir. Bununla birlikte, kullanıcı hesabının güvenliği ihlal [edilmiş olup olmadığını denetlemeyi de göz atabilirsiniz](responding-to-a-compromised-email-account.md).|
|Kullanıcının e-posta göndermesi kısıtlandı|**Yüksek**|Bu uyarı, kurumdan bir kişinin giden posta göndermesi kısıtlanmışsa oluşturulur. Bu uyarı normalde bir e-posta [hesabının güvenliği ihlal edilmiş durumda olur](responding-to-a-compromised-email-account.md). <p> Kısıtlanmış kullanıcılar hakkında daha fazla bilgi için bkz. Microsoft 365'da Engellenen [kullanıcıları Kısıtlanmış Kullanıcılar Microsoft 365](removing-user-from-restricted-users-portal-after-spam.md).|
|

> [!TIP]
> Uyarı ilkeleri hakkında daha fazla bilgi edinmek veya varsayılan ayarları düzenlemek için bkz[.](../../compliance/alert-policies.md) İlke Microsoft 365 uyumluluk merkezi.

## <a name="required-permissions-to-use-air-capabilities"></a>AIR özelliklerini kullanmak için gerekli izinler

İzinler, aşağıdaki tabloda açıklananlar gibi belirli roller aracılığıyla vetir:

<br>

****

|Görev|Gerekli rol(ler)|
|---|---|
|AIR özelliklerini ayarlama|Aşağıdaki rollerden biri: <ul><li>Genel Yönetici</li><li>Güvenlik Yöneticisi</li></ul> <p> Bu roller portalda veya [Azure Active Directory](/azure/active-directory/roles/permissions-reference) [portalında Microsoft 365 Defender atanabilir](permissions-microsoft-365-security-center.md).|
|Otomatik araştırma başlatma <p> --- veya --- <p> Önerilen eylemleri onaylama veya reddetme|Azure Active Directory portalında veya [Microsoft 365 Defender](/azure/active-directory/roles/permissions-reference)[:](permissions-microsoft-365-security-center.md) <ul><li>Genel Yönetici</li><li>Güvenlik Yöneticisi</li><li>Güvenlik İşleci</li><li>Güvenlik Okuyucu <br> --- ve --- </li><li>Arama ve Temizleme (bu rol yalnızca ilgili [portalda Microsoft 365 Defender atanır](permissions-microsoft-365-security-center.md). Burada yeni bir E-posta **& işbirliği** rol grubu oluşturmanız ve Bu yeni rol grubuna Ara ve Temizle rolünü eklemeniz gerekir.</li></ul>|

## <a name="required-licenses"></a>Gerekli lisanslar

[Plan 2 Office 365 için Microsoft Defender](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) lisansları şu kişilere atanabilir:

- Güvenlik yöneticileri (genel yöneticiler dahil)
- Kuruluş güvenlik işlemleri ekibi (güvenlik okuyucuları ve Arama ve Temizleme **rolüne sahip olanlar dahil** )
- Son kullanıcılar

## <a name="changes-are-coming-soon-in-your-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında değişiklikler Microsoft 365 Defender geliyor

Air özelliklerini Office 365 için Microsoft Defender'da zaten kullanıyorsanız, gelişmiş Hava Microsoft 365 Defender [portalında bazı değişiklikler görmek Microsoft 365 Defender vardır](../defender/microsoft-365-defender.md#the-microsoft-365-defender-portal).

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Birleşik İşlem merkezi.":::

Yeni ve geliştirilmiş Microsoft 365 Defender portalı<https://security.microsoft.com>, Office 365 için [Microsoft Defender'da](defender-for-office-365.md) ve Uç Nokta için [Microsoft Defender'da AIR özelliklerini bir araya getirir](../defender-endpoint/automated-investigations.md). Bu güncelleştirme ve geliştirmelerle, güvenlik işlemleri ekibinin tüm e-postanız, işbirliği içeriğiniz, kullanıcı hesaplarınız ve cihazlarınız genelindeki otomatik soruşturmalar ve düzeltme eylemleriyle ilgili ayrıntıları tek bir yerde görüntüleyebilirsiniz.

> [!TIP]
> Yeni yönetim Microsoft 365 Defender, aşağıdaki yönetim merkezlerinin yerini almaktadır:
>
> - Güvenlik & Uyumluluk Merkezi (<https://protection.office.com>)
> - Microsoft 365 Defender (<https://security.microsoft.com>)
>
> Değişen URL'nin yanı sıra, güvenlik ekibimize tek bir yerde daha fazla tehdit algılaması için görünürlük sağlayan daha rahat bir deneyim vermek üzere tasarlanmış yeni bir genel görünüm vardır.

### <a name="what-to-expect"></a>Neler olabilir?

Aşağıdaki tabloda, Microsoft Defender'daki Air'te gelecek değişiklikler ve iyileştirmeler Office 365.

<br>

****

|Öğe|Neler değişti?|
|---|---|
|**İncelemeler** sayfası|Güncelleştirilmiş **Araştırma sayfası** , Uç Nokta için [Microsoft Defender'da gördüğünüzle daha tutarlıdır](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations). Yeni, birleşik Araştırma görünümüyle uyumlu olan bazı genel biçim ve stil **değişiklikleri** göreceğiniz gibi. Örneğin, araştırma grafiği daha birleşik bir biçime sahip.|
|**Kullanıcılar** sekmesi|Kullanıcılar **sekmesi** artık Posta Kutuları **sekmesidir** . Kullanıcılar hakkında ayrıntılar Posta Kutusu **sekmesinde listelenir** .|
|**E-posta** sekmesi|**E-posta** sekmesi kaldırıldı; **e-posta** ve e-posta kümesi öğelerinin listesini görmek için Varlıklar sekmesini ziyaret edin.|
|**Varlıklar** sekmesi|Varlıklar **sekmesinde** , tüm özet görünümünü ve varlık türüne göre filtre uygulama olanağını içeren sekme içinde sekme stili vardır. Varlıklar **sekmesinde** artık Explorer'da **Aç seçeneğine** ek olarak bir Git **avı seçeneği** de vardır. Artık varlıkları ve tehditleri bulmak [ve](threat-explorer.md) [sonuçlara göre](../defender-endpoint/advanced-hunting-overview.md) filtrelemek için Explorer'ı veya gelişmiş atlığı kullanabilirsiniz.|
|**Eylemler** sekmesi|Güncelleştirilmiş **Eylemler** sekmesi artık Bekleyen **eylemler sekmesini ve** Eylemler geçmişi **sekmesini içerir** . Eylemler, bekleyen bir eylemi seçmenizle açılan yan bölmede onaylanır (veya reddedilir) olabilir.|
|**Kanıt** sekmesi|Yeni Kanıt **sekmesi** eylemlerle ilgili bulguların temellerini gösterir. Her kanıt parçasıyla ilgili eylemler, bekleyen bir eylemi seçerek açılan yan bölmede onaylanır (veya reddedilir).|
|**İşlem merkezi**|Güncelleştirilmiş **İşlem Merkezi** (<https://security.microsoft.com/action-center>), e-posta, cihazlar ve kimlikler genelinde bekleyen ve tamamlanmış eylemleri bir araya getirir. Daha fazla bilgi edinmek için bkz. İşlem merkezi. (Daha fazla bilgi edinmek için bkz [. İşlem merkezi](../defender/m365d-action-center.md).)|
|**Olaylar** sayfası|Olaylar **sayfası,** soruşturmaların daha iyi birleştirilmiş bir görünümünü sağlamak için artık birden çok soruşturmayı bir arada ilişkili yapıyor. ([Olaylar hakkında daha fazla bilgi öğrenin](../defender/incidents-overview.md).)|
|

## <a name="next-steps"></a>Sonraki adımlar

- [Otomatik bir incelemenin ayrıntılarını ve sonuçlarını görme](air-view-investigation-results.md#view-details-of-an-investigation)
- [Bekleyen eylemleri gözden geçirme ve onaylama](air-remediation-actions.md)
