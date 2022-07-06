---
title: Office 365 için Microsoft Defender'de otomatik araştırma ve yanıt
keywords: AIR, autoIR, Uç Nokta için Microsoft Defender, otomatik, araştırma, yanıt, düzeltme, tehditler, gelişmiş, tehdit, koruma
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
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
description: Office 365 için Microsoft Defender'de otomatik araştırma ve yanıt özelliklerini kullanmaya başlayın.
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0fda154f8eb52ddab024a7f5bb02f980c9a05894
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617162"
---
# <a name="automated-investigation-and-response-air-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'de otomatik araştırma ve yanıt (AIR)

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Office 365 için Microsoft Defender](defender-for-office-365.md), güvenlik operasyonları ekibinize zaman ve çaba kazandırabilecek güçlü otomatik araştırma ve yanıt (AIR) özellikleri içerir. Uyarılar tetiklendiğinde, bu uyarıları gözden geçirmek, önceliklendirmek ve yanıtlamak güvenlik operasyonları ekibinize bağlı olur. Gelen uyarıların hacmine ayak uydurmak zor olabilir. Bu görevlerden bazılarını otomatikleştirmek yardımcı olabilir.

AIR, güvenlik operasyonları ekibinizin daha verimli ve etkili bir şekilde çalışmasını sağlar. AIR özellikleri, günümüzde mevcut olan iyi bilinen tehditlere yanıt olarak otomatik araştırma süreçlerini içerir. Uygun düzeltme eylemleri onay bekler ve güvenlik operasyonları ekibinizin algılanan tehditlere etkili bir şekilde yanıt vermesini sağlar. AIR ile güvenlik operasyonları ekibiniz, tetiklenen önemli uyarıları görmeden daha yüksek öncelikli görevlere odaklanabilir.

Bu makalede şunlar açıklanmaktadır:

- [AIR'in genel akışı](#the-overall-flow-of-air);
- [AIR nasıl elde edersiniz](#how-to-get-air); Ve
- AIR özelliklerini yapılandırmak veya kullanmak için [gerekli izinler](#required-permissions-to-use-air-capabilities) .
- Microsoft 365 Defender portalınıza yakında eklenecek değişiklikler

Bu makale ayrıca [sonraki adımları](#next-steps) ve daha fazla bilgi edinmek için kaynakları içerir.

## <a name="the-overall-flow-of-air"></a>AIR'in genel akışı

Bir uyarı tetikler ve güvenlik playbook'u otomatik bir araştırma başlatır ve bu da bulgular ve önerilen eylemlerle sonuçlanır. Air'in genel akışı aşağıdadır, adım adım:

1. Otomatik araştırma aşağıdaki yollardan biriyle başlatılır:
   - Bir uyarı e-postadaki şüpheli bir şey (ileti, ek, URL veya güvenliği aşılmış kullanıcı hesabı gibi) tarafından [tetikleniyor](#which-alert-policies-trigger-automated-investigations) . Bir olay oluşturulur ve otomatik bir araştırma başlar; Veya
   - Güvenlik analisti[, Explorer'ı](threat-explorer.md) kullanırken [otomatik bir araştırma başlatır](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).
2. Otomatik bir araştırma çalıştırılırken söz konusu e-posta ve bu e-postayla ilgili varlıklar hakkında veri toplar. Bu tür varlıklar dosyalar, URL'ler ve alıcılar içerebilir. Yeni ve ilgili uyarılar tetiklendiğinde araştırmanın kapsamı artabilir.
3. Otomatik araştırma sırasında ve sonrasında [, ayrıntılar ve sonuçlar](air-view-investigation-results.md) görüntülenebilir. Sonuçlar, bulunan tehditleri yanıtlamak ve düzeltmek için gerçekleştirilebilecek [önerilen eylemleri](air-remediation-actions.md) içerir.
4. Güvenlik operasyonları ekibiniz [araştırma sonuçlarını ve önerilerini inceler](air-view-investigation-results.md) ve [düzeltme eylemlerini onaylar veya reddeder](air-review-approve-pending-completed-actions.md).
5. Bekleyen düzeltme eylemleri onaylandığından (veya reddedildiğinde), otomatik araştırma tamamlanmıştır.

Office 365 için Microsoft Defender otomatik olarak hiçbir düzeltme eylemi yapılmaz. Düzeltme eylemleri yalnızca kuruluşunuzun güvenlik ekibi tarafından onaylandığında gerçekleştirilen işlemlerdir. AIR özellikleri, düzeltme eylemlerini belirleyerek ve bilinçli bir karar vermek için gereken ayrıntıları sağlayarak güvenlik operasyonları ekibinize zaman kazandırır.

Her otomatik araştırma sırasında ve sonrasında güvenlik operasyonları ekibiniz şunları yapabilir:

- [Araştırmayla ilgili uyarıyla ilgili ayrıntıları görüntüleme](air-view-investigation-results.md#view-details-about-an-alert-related-to-an-investigation)
- [Araştırmanın sonuç ayrıntılarını görüntüleme](air-view-investigation-results.md#view-details-of-an-investigation)
- [Araştırma sonucunda eylemleri gözden geçirme ve onaylama](air-review-approve-pending-completed-actions.md)

> [!TIP]
> Daha ayrıntılı bir genel bakış için bkz. [AIR nasıl çalışır](automated-investigation-response-office.md)?

## <a name="how-to-get-air"></a>AIR nasıl elde edersiniz?

İlkeleriniz ve uyarılarınız yapılandırılmışsa AIR özellikleri [Office 365 için Microsoft Defender](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) dahil edilir. Yardıma mı ihtiyacınız var? Aşağıdaki koruma ayarlarını ayarlamak veya yapılandırmak için [Tehditlere karşı koruma'daki](protect-against-threats.md) yönergeleri izleyin:

- [Denetim günlüğü](../../compliance/turn-audit-log-search-on-or-off.md) (açık olmalıdır)
- [Kötü amaçlı yazılımdan koruma](protect-against-threats.md#part-1---anti-malware-protection-in-eop)
- [Kimlik avından koruma](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
- [İstenmeyen posta önleme koruma](protect-against-threats.md#part-3---anti-spam-protection-in-eop)
- [Güvenli Bağlantılar ve Güvenli Ekler](protect-against-threats.md#part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365)

Ayrıca, [kuruluşunuzun uyarı ilkelerini](../../compliance/alert-policies.md), özellikle [de Tehdit yönetimi kategorisindeki varsayılan ilkeleri gözden geçirmeyi](../../compliance/alert-policies.md#default-alert-policies) unutmayın.

## <a name="which-alert-policies-trigger-automated-investigations"></a>Hangi uyarı ilkeleri otomatik araştırmayı tetikler?

Microsoft 365, Exchange yönetici izinlerinin kötüye kullanımı, kötü amaçlı yazılım etkinliği, olası dış ve iç tehditler ve bilgi idaresi risklerini belirlemeye yardımcı olan birçok yerleşik uyarı ilkesi sağlar. [Varsayılan uyarı ilkelerinin](../../compliance/alert-policies.md#default-alert-policies) bazıları otomatik araştırma tetikleyebilir. Aşağıdaki tabloda otomatik araştırma tetikleyen uyarılar, Microsoft 365 Defender portalındaki önem dereceleri ve bunların nasıl oluşturulduğu açıklanmaktadır:

|Uyarı|Önem derecesi|Uyarı nasıl oluşturulur?|
|---|---|---|
|Kötü amaçlı olabilecek bir URL tıklaması algılandı|**Yüksek**|Aşağıdakilerden herhangi biri gerçekleştiğinde bu uyarı oluşturulur: <ul><li>Kuruluşunuzdaki [Güvenli Bağlantılar](safe-links.md) tarafından korunan bir kullanıcı kötü amaçlı bir bağlantıya tıklar</li><li>URL'ler için karar değişiklikleri Office 365 için Microsoft Defender</li><li>Kullanıcılar Güvenli Bağlantılar uyarı sayfalarını (kuruluşunuzun [Güvenli Bağlantılar ilkesine](set-up-safe-links-policies.md) göre) geçersiz kılar.</li></ul> <p> Bu uyarıyı tetikleyen olaylar hakkında daha fazla bilgi için bkz. [Güvenli Bağlantılar ilkelerini ayarlama](set-up-safe-links-policies.md).|
|E-posta iletisi bir kullanıcı tarafından kötü amaçlı yazılım veya kimlik avı olarak bildirilir|**Bilgi**|Kuruluşunuzdaki kullanıcılar, [Rapor İletisi eklentisini veya Rapor](enable-the-report-message-add-in.md) Kimlik [Avı](enable-the-report-phish-add-in.md) eklentisini kullanarak iletileri kimlik avı e-postası olarak bildirdiğinde bu uyarı oluşturulur.|
|Kötü amaçlı yazılım içeren e-posta iletileri teslimden sonra kaldırılır|**Bilgi**|Kötü amaçlı yazılım içeren tüm e-posta iletileri kuruluşunuzdaki posta kutularına teslim edildiğinde bu uyarı oluşturulur. Bu olay oluşursa, Microsoft [sıfır saatlik otomatik temizleme (ZAP)](zero-hour-auto-purge.md) kullanarak virüslü iletileri Exchange Online posta kutularından kaldırır.|
|Kimlik avı URL'lerini içeren e-posta iletileri teslimden sonra kaldırılır|**Bilgi**|Bu uyarı, kimlik avı içeren iletiler kuruluşunuzdaki posta kutularına teslim edildiğinde oluşturulur. Bu olay oluşursa, Microsoft [zap](zero-hour-auto-purge.md) kullanarak Exchange Online posta kutularından virüslü iletileri kaldırır.|
|Şüpheli e-posta gönderme desenleri algılandı|**Orta**|Bu uyarı, kuruluşunuzdaki biri şüpheli e-posta gönderdiğinde ve e-posta göndermesi kısıtlanma riskiyle karşılandığında oluşturulur. Uyarı, hesabın gizliliğinin ihlal edilmiş olduğunu ancak kullanıcıyı kısıtlayabilecek kadar ciddi olmadığını gösteren davranışlar için erken uyarıdır. <p> Nadir olsa da, bu ilke tarafından oluşturulan bir uyarı bir anomali olabilir. Ancak [, kullanıcı hesabının gizliliğinin ihlal edilip edilmediğini denetlemek iyi bir fikirdir](responding-to-a-compromised-email-account.md).|
|Kullanıcının e-posta göndermesi kısıtlandı|**Yüksek**|Kuruluşunuzdaki birinin giden posta göndermesi kısıtlandığında bu uyarı oluşturulur. Bu uyarı genellikle [bir e-posta hesabının güvenliği aşıldığında sonuçlanır](responding-to-a-compromised-email-account.md). <p> Kısıtlı kullanıcılar hakkında daha fazla bilgi için bkz. [Microsoft 365'teki Kısıtlı Kullanıcılar portalından engellenen kullanıcıları kaldırma](removing-user-from-restricted-users-portal-after-spam.md).|

> [!TIP]
> Uyarı ilkeleri hakkında daha fazla bilgi edinmek veya varsayılan ayarları düzenlemek için [Microsoft Purview uyumluluk portalı uyarı ilkeleri bölümüne](../../compliance/alert-policies.md) bakın.

## <a name="required-permissions-to-use-air-capabilities"></a>AIR özelliklerini kullanmak için gerekli izinler

İzinler, aşağıdaki tabloda açıklanan roller gibi belirli roller aracılığıyla verilir:

|Görev|Gerekli rol veya rol|
|---|---|
|AIR özelliklerini ayarlama|Aşağıdaki rollerden biri: <ul><li>Genel Yönetici</li><li>Güvenlik Yöneticisi</li></ul> <p> Bu roller [Azure Active Directory'de](/azure/active-directory/roles/permissions-reference) veya [Microsoft 365 Defender portalında](permissions-microsoft-365-security-center.md) atanabilir.|
|Otomatik araştırma başlatın <p> --- veya --- <p> Önerilen eylemleri onaylama veya reddetme|[Azure Active Directory'de](/azure/active-directory/roles/permissions-reference) veya [Microsoft 365 Defender portalında](permissions-microsoft-365-security-center.md) atanan aşağıdaki rollerden biri: <ul><li>Genel Yönetici</li><li>Güvenlik Yöneticisi</li><li>Güvenlik İşleci</li><li>Güvenlik Okuyucusu <br> --- ve --- </li><li>Arama ve Temizleme (bu rol yalnızca [Microsoft 365 Defender portalında](permissions-microsoft-365-security-center.md) atanır. Orada yeni bir **E-posta & işbirliği** rol grubu oluşturmanız ve arama ve temizleme rolünü bu yeni rol grubuna eklemeniz gerekebilir.</li></ul>|

## <a name="required-licenses"></a>Gerekli lisanslar

[Office 365 için Microsoft Defender Plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) lisansları şu lisanslara atanmalıdır:

- Güvenlik yöneticileri (genel yöneticiler dahil)
- Kuruluşunuzun güvenlik operasyonları ekibi (güvenlik okuyucuları ve **Arama ve Temizleme** rolüne sahip olanlar dahil)
- Son kullanıcılar

## <a name="changes-are-coming-soon-in-your-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalınızda yakında değişiklikler geliyor

Office 365 için Microsoft Defender'da ZATEN AIR özelliklerini kullanıyorsanız[, geliştirilmiş Microsoft 365 Defender portalında](../defender/microsoft-365-defender-portal.md) bazı değişiklikler görmek üzeresiniz.

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Birleşik İşlem merkezi" lightbox="../../media/m3d-action-center-unified.png":::

Yeni ve geliştirilmiş Microsoft 365 Defender portalı<https://security.microsoft.com>, AIR özelliklerini Office 365 için Microsoft Defender ve [Uç Nokta için Microsoft Defender'da](../defender-endpoint/automated-investigations.md) bir [](defender-for-office-365.md) araya getirir. Bu güncelleştirmeler ve geliştirmelerle, güvenlik operasyonları ekibiniz e-postanız, işbirliği içeriğiniz, kullanıcı hesaplarınız ve cihazlarınız genelinde otomatik araştırma ve düzeltme eylemleri hakkındaki ayrıntıları tek bir yerden görüntüleyebilir.

> [!TIP]
> Yeni Microsoft 365 Defender portalı aşağıdaki yönetim merkezlerinin yerini alır:
>
> - Güvenlik & Uyumluluk Merkezi (<https://protection.office.com>)
> - Microsoft 365 Defender (<https://security.microsoft.com>)
>
> URL'nin değiştirilmesine ek olarak, güvenlik ekibinize daha kolay bir deneyim sunmak ve tek bir yerde daha fazla tehdit algılaması için görünürlük sağlamak üzere tasarlanmış yeni bir görünüm ve his vardır.

### <a name="what-to-expect"></a>Bekleyebileceğiniz şeyler

Aşağıdaki tabloda, Office 365 için Microsoft Defender'de AIR'e gelen değişiklikler ve geliştirmeler listelendir.

|Öğe|Ne değişiyor?|
|---|---|
|**Araştırma sayfası**|Güncelleştirilmiş **Araştırma sayfası**[, Uç Nokta için Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations) gördüklerinizle daha tutarlıdır. Yeni, birleşik **Araştırma görünümüyle** uyumlu bazı genel biçim ve stil değişiklikleri görürsünüz. Örneğin, araştırma grafiği daha birleşik bir biçime sahiptir.|
|**Kullanıcılar** sekmesi|**Kullanıcılar** sekmesi artık **Posta Kutuları** sekmesidir. Kullanıcılarla ilgili ayrıntılar **Posta Kutusu** sekmesinde listelenir.|
|**E-posta** sekmesi|**E-posta** sekmesi kaldırıldı; e-posta ve e-posta kümesi öğelerinin listesini görmek için **Varlıklar** sekmesini ziyaret edin.|
|**Varlıklar** sekmesi|**Varlıklar** sekmesi, tüm özet görünümünü ve varlık türüne göre filtreleme özelliğini içeren bir sekme içinde sekme stiline sahiptir. **Varlıklar** sekmesi artık **Gezginde Aç** seçeneğine ek olarak bir **Go avcılığı** seçeneği de içerir. Artık varlıkları ve tehditleri bulmak ve sonuçları filtrelemek için [Gezgin'i](threat-explorer.md) veya [gelişmiş avcılığı](../defender-endpoint/advanced-hunting-overview.md) kullanabilirsiniz.|
|**Eylemler** sekmesi|Güncelleştirilmiş **Eylemler** sekmesi artık **Bekleyen eylemler** sekmesi ve **Eylemler geçmişi** sekmesi içerir. Eylemler, bekleyen bir eylemi seçtiğinizde açılan bir yan bölmede onaylanabilir (veya reddedilebilir).|
|**Kanıt** sekmesi|Yeni **bir Kanıt** sekmesi, eylemlerle ilgili temel varlık bulgularını gösterir. Her kanıt parçasıyla ilgili eylemler, bekleyen bir eylemi seçtiğinizde açılan bir yan bölmede onaylanabilir (veya reddedilebilir).|
|**İşlem merkezi**|Güncelleştirilmiş **İşlem merkezi** (<https://security.microsoft.com/action-center>), e-posta, cihazlar ve kimlikler arasında bekleyen ve tamamlanan eylemleri bir araya getirir. Daha fazla bilgi için bkz. İşlem merkezi. (Daha fazla bilgi için bkz [. İşlem merkezi](../defender/m365d-action-center.md).)|
|**Olaylar** sayfası|**Olaylar** sayfası artık birden çok araştırmayı ilişkilendirerek araştırmaların daha iyi birleştirilmiş bir görünümünü sağlar. ([Olaylar hakkında daha fazla bilgi edinin](../defender/incidents-overview.md).)|

## <a name="next-steps"></a>Sonraki adımlar

- [Otomatik araştırmanın ayrıntılarını ve sonuçlarını görme](air-view-investigation-results.md#view-details-of-an-investigation)
- [Bekleyen eylemleri gözden geçirme ve onaylama](air-remediation-actions.md)
