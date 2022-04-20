---
title: Microsoft 365 Defender'da Office 365 için Microsoft Defender
description: Güvenlik & Uyumluluk Merkezi'nden Microsoft 365 Defender değişiklikleri hakkında bilgi edinin.
keywords: Microsoft 365 güvenlik, Microsoft 365 Defender, Office 365 için Microsoft Defender, Uç Nokta için Microsoft Defender, MDO, MDE ile çalışmaya başlama, tek bölmeli cam, yeni güvenlik portalı, yeni defender güvenlik portalı
ms.date: 02/21/2021
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.prod: m365-security
ms.technology: m365d
ms.openlocfilehash: 84fed53ec1f12ebe7e52d0b789dc9db57360cf4f
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945571"
---
# <a name="microsoft-defender-for-office-365-in-microsoft-365-defender"></a>Microsoft 365 Defender'da Office 365 için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Office 365 için Microsoft Defender](/microsoft-365/security/office-365-security/defender-for-office-365)

## <a name="quick-reference"></a>Hızlı başvuru

Aşağıdaki tabloda Güvenlik & Uyumluluk Merkezi ile Microsoft 365 Defender arasındaki gezinti değişiklikleri listelenmiştir.

<br>

****

|[Güvenlik & Uyumluluk Merkezi](https://protection.office.com)|[Microsoft 365 Defender](https://security.microsoft.com)|[Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/homepage)|[Exchange yönetim merkezi](https://admin.exchange.microsoft.com)|
|---|---|---|---|
|Uyarılar|<ul><li>[Uyarı İlkeleri](https://security.microsoft.com/alertpolicies)</li><li>[Olaylar & uyarıları](https://security.microsoft.com/alerts)</li></ul>|[Uyarılar sayfası](https://compliance.microsoft.com/homepage)||
|Sınıflandırma||Bkz. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/homepage)||
|Veri kaybı önleme||Bkz. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/homepage)||
|Kayıt yönetimi||Bkz. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/homepage)||
|Bilgi Yönetişimi||Bkz. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/homepage)||
|Tehdit yönetimi|[E-posta & İşbirliği](https://security.microsoft.com/homepage)|||
|İzinler|[İzinler & rolleri](https://security.microsoft.com/emailandcollabpermissions)|Bkz. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/homepage)||
|Posta akışı|||Bkz[. Exchange yönetim merkezi](https://admin.exchange.microsoft.com/#/)|
|Veri gizliliği||Bkz. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/homepage)||
|Arama|[Denetim](https://security.microsoft.com/auditlogsearch?viewid=Async%20Search)|Arama (içerik araması)||
|Raporlar|[Rapor](https://security.microsoft.com/emailandcollabreport)|||
|Hizmet güvencesi||Bkz. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/homepage)||
|Gözetim||Bkz. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/homepage)||
|Ediscovery||Bkz. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/homepage)||
|||||

<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a> [adresinde Microsoft 365 Defender](./microsoft-365-defender.md), Güvenlik & Uyumluluk Merkezi de dahil olmak üzere mevcut Microsoft güvenlik portallarının güvenlik özelliklerini birleştirir. Bu geliştirilmiş merkez, güvenlik ekiplerinin kuruluşlarını tehditlere karşı daha etkili ve verimli bir şekilde korumasına yardımcı olur.

Güvenlik & Uyumluluk Merkezi'ni (protection.office.com) biliyorsanız, bu makalede Microsoft 365 Defender bazı değişiklikler ve geliştirmeler açıklanmaktadır.

Avantajlar hakkında daha fazla bilgi edinin: [Microsoft 365 Defender genel bakış](microsoft-365-defender.md)

Uyumlulukla ilgili öğeleri arıyorsanız <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalını</a> ziyaret edin.

## <a name="new-and-improved-capabilities"></a>Yeni ve geliştirilmiş özellikler

Sol gezinti veya hızlı başlatma çubuğu tanıdık görünecektir. Ancak, bu Bulut için Defender bazı yeni ve güncelleştirilmiş öğeler vardır.

Birleşik Microsoft 365 Defender çözümüyle tehdit sinyallerini bir araya getirerek tehdidin tam kapsamını ve etkisini ve şu anda kuruluşu nasıl etkilediğini belirleyebilirsiniz.

:::image type="content" source="../../media/M365-defender-converge-experience.png" alt-text="yakınsanmış Microsoft 365 Defender deneyimi" lightbox="../../media/M365-defender-converge-experience.png":::

Office 365 için Defender, kuruluşunuzu e-posta iletileri, bağlantılar (URL'ler) ve işbirliği araçlarının oluşturduğu kötü amaçlı tehditlere karşı korur.

:::image type="content" source="../../media/Defender-for-O365.png" alt-text="Office 365 için Defender portalı" lightbox="../../media/Defender-for-O365.png":::

### <a name="incidents-and-alerts"></a>Olaylar ve uyarılar

Olay ve uyarı yönetimini e-postanız, cihazlarınız ve kimlikleriniz arasında bir araya getirir. Uyarılar artık Araştırma düğümü altında kullanılabilir ve bir saldırının daha geniş bir görünümünü sağlamaya yardımcı olur. Uyarı sayfası, ayrıntılı bir hikaye oluşturmak için saldırı sinyallerini birleştirerek uyarıya tam bağlam sağlar. Daha önce uyarılar farklı iş yüklerine özeldi. Yeni, birleşik bir deneyim, iş yükleri genelinde uyarıların tutarlı bir görünümünü bir araya getiriyor. Hızlı bir şekilde önceliklendirme yapabilir, araştırabilir ve etkili eylemler gerçekleştirebilirsiniz.

- [Araştırma hakkında daha fazla bilgi edinin](incidents-overview.md)
- [Uyarıları yönetme hakkında daha fazla bilgi edinin](/windows/security/threat-protection/microsoft-defender-atp/review-alerts)

:::image type="content" source="../../media/converge-1-alerts-and-actions.png" alt-text="Microsoft 365 Defender portalında Uyarılar ve Eylemler hızlı başlatma çubuğu" lightbox="../../media/converge-1-alerts-and-actions.png":::

### <a name="hunting"></a>Avcı -lık

[Gelişmiş tehdit avcılığı sorgularını](advanced-hunting-overview.md) kullanarak uç noktalarınızdaki tehditleri, kötü amaçlı yazılımları ve kötü amaçlı etkinlikleri, Office 365 posta kutularını ve daha fazlasını proaktif olarak arayın. Bu güçlü sorgular, hem bilinen hem de olası tehditler için tehdit göstergelerini ve varlıkları bulmak ve gözden geçirmek için kullanılabilir.

[Özel algılama kuralları](/windows/security/threat-protection/microsoft-defender-atp/custom-detection-rules) , ihlal etkinliğinin ve yanlış yapılandırılmış cihazların göstergesi olabilecek olayları proaktif olarak izlemenize yardımcı olmak için gelişmiş tehdit avcılığı sorgularından oluşturulabilir.

[Office 365 için Microsoft Defender'da gelişmiş avcılık örneği](advanced-hunting-example.md) aşağıda verilmiştir.

### <a name="action-center"></a>İşlem merkezi

İşlem merkezi, otomatik araştırma ve yanıt özellikleri tarafından oluşturulan araştırmaları gösterir. Microsoft 365 Defender'da otomatik ve kendi kendini iyileştiren bu özellik, belirli olaylara otomatik olarak yanıt vererek güvenlik ekiplerine yardımcı olabilir.

[İşlem merkezi](m365d-action-center.md) hakkında daha fazla bilgi edinin.

#### <a name="threat-analytics"></a>Tehdit Analizi

Uzman Microsoft güvenlik araştırmacılarından tehdit bilgileri alın. Tehdit Analizi, güvenlik ekiplerinin yeni ortaya çıkan tehditlerle karşılaştığında daha verimli olmasını sağlar. Tehdit Analizi şunları içerir:

- Office 365 için Microsoft Defender e-postayla ilgili algılamalar ve azaltmalar. Bu, Uç Nokta için Microsoft Defender'dan sağlanan uç nokta verilerine ek olarak sağlanır.
- Tehditlerle ilgili olaylar görünümü.
- Raporlarda eyleme dönüştürülebilir bilgileri hızla tanımlamak ve kullanmak için gelişmiş deneyim.

Tehdit analizine Microsoft 365 Defender sol üst gezinti çubuğundan veya kuruluşunuz için en önemli tehditleri gösteren ayrılmış bir pano kartından erişebilirsiniz.

[Tehdit analiziyle yeni ortaya çıkan tehditleri izleme ve yanıtlama](./threat-analytics.md) hakkında daha fazla bilgi edinin.

### <a name="email--collaboration"></a>E-posta & işbirliği

Kullanıcılarınızın e-postasına yönelik tehditleri izleyin ve araştırın, kampanyaları izleyin ve daha fazlasını yapın. Güvenlik & Uyumluluk Merkezi'ni kullandıysanız, bu tanıdık olacaktır.

:::image type="content" source="../../media/converge-3-email-and-collab-new.png" alt-text="Microsoft 365 Defender portalının sol gezinti bölmesindeki E-posta & Collab (veya MSDO) için hızlı başlatma menüsü" lightbox="../../media/converge-3-email-and-collab-new.png":::

#### <a name="email-entity-page"></a>E-posta varlık sayfası

[E-posta varlığı sayfası](../office-365-security/mdo-email-entity-page.md), geçmişte farklı *sayfalara veya görünümlere* dağılmış e-posta bilgilerini birlandırır. Tehditler ve eğilimler için e-postayı *araştırmak merkezidir*. Üst bilgi bilgilerine ve e-posta önizlemesine, e-postayla ilgili diğer yararlı bilgilerin yanı sıra aynı e-posta sayfasından erişilebilir. Benzer şekilde, kötü amaçlı dosya ekleri veya URL'ler için de patlama durumu aynı sayfanın bir sekmesinde bulunabilir. E-posta varlık sayfası, yöneticilerin ve güvenlik operasyonları ekiplerinin bir e-posta tehdidini ve durumunu anlamasını ve işlemeyi hızlı bir şekilde belirlemesini sağlar.

### <a name="access-and-reports"></a>Erişim ve Raporlar

Raporları görüntüleyin, ayarlarınızı değiştirin ve kullanıcı rollerini değiştirin.

:::image type="content" source="../../media/converge-4-access-and-reporting-new.png" alt-text="Microsoft 365 Defender portalının sol gezinti bölmesindeki Microsoft 365 Defender izinler ve raporlama için hızlı başlatma menüsü" lightbox="../../media/converge-4-access-and-reporting-new.png":::

> [!NOTE]
> DomainKeys Identified Mail (DKIM), hedef e-posta sistemlerinin özel etki alanınızdan giden iletilere güvenmesini sağlar.
> Office 365 için Defender kullanıcılar için artık Microsoft 365 Defender aracılığıyla <https://security.microsoft.com/threatpolicy>DKIM anahtarlarını *yönetebilir ve döndürebilir* veya **İlke & kuralları** \> **Tehdit ilkeleri** \> \> **Kuralları** bölümü **DKIM'e**\> gidebilirsiniz.
>
> Daha fazla bilgi için bkz. [Özel etki alanınızdan gönderilen giden e-postayı doğrulamak için DKIM kullanma](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email).

## <a name="whats-changed"></a>Değişenler

Bu tablo, Güvenlik & Uyumluluk merkezi ile Microsoft 365 Defender portalı arasında değişiklik yapılan Tehdit yönetiminin hızlı bir başvurusudur. Bu alanlar hakkında daha fazla bilgi edinmek için bağlantılara tıklayın.

<br>

****

|Alan|Değişikliğin açıklaması|
|---|---|
|[Soruşturma](../office-365-security/office-365-air.md#changes-are-coming-soon-in-your-microsoft-365-defender-portal)|[Office 365 için Defender](/microsoft-365/security/office-365-security/defender-for-office-365) ve [Uç Nokta için Defender'da](../defender-endpoint/automated-investigations.md) AIR özelliklerini bir araya getirir. Bu güncelleştirmeler ve geliştirmelerle, güvenlik operasyonları ekibiniz e-postanız, işbirliği içeriğiniz, kullanıcı hesaplarınız ve cihazlarınız genelinde otomatik araştırma ve düzeltme eylemleri hakkındaki ayrıntıları tek bir yerden görüntüleyebilir.|
|[Uyarı kuyruğu](../../compliance/alert-policies.md)|Güvenlik & Uyumluluk Merkezi'ndeki **Uyarıları görüntüle** açılır bölmesi artık Microsoft 365 Defender bağlantılarını içerir. **Uyarı Sayfasını Aç** bağlantısına tıklayın ve Microsoft 365 Defender açılır. Uyarılar kuyruğundaki herhangi bir Office 365 uyarıya tıklayarak Uyarıları **görüntüle** sayfasına erişebilirsiniz.|
|[Saldırı Simülasyonu eğitimi](../office-365-security/attack-simulation-training-insights.md)|Kuruluşunuzda gerçekçi saldırı senaryoları çalıştırmak için Saldırı Simülasyonu eğitimini kullanın. Bu sanal saldırılar, kuruluşunuzu gerçek bir saldırı etkilemeden önce iş gücünüzü eğitmek için yardımcı olabilir. Saldırı simülasyonu eğitimi, daha fazla seçenek, gelişmiş raporlar ve geliştirilmiş eğitim akışları, saldırı simülasyonunuzun ve eğitim senaryolarınızın teslimini ve yönetimini kolaylaştırmaya yardımcı olur.|
|

Bu alanlarda değişiklik yapılmaz:

- [Explorer](../office-365-security/threat-explorer.md)
- [İlkeler & Kuralları](../../compliance/alert-policies.md)
- [Kampanya](../office-365-security/campaigns.md)
- [Gönderi](../office-365-security/admin-submission.md)
- [Gözden geçirin](./m365d-action-center.md)
- [Tehdit İzleyicisi](../office-365-security/threat-trackers.md)

Ayrıca, bu makalenin altındaki **İlgili Bilgiler** bölümüne bakın.

> [!IMPORTANT]
> <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalı</a>, ve <https://protection.office.com>içindeki <https://securitycenter.windows.com>güvenlik özelliklerini birleştirir. Ancak, gördükleriniz aboneliğinize bağlıdır. Tek başına abonelikler olarak yalnızca Office 365 için Microsoft Defender Plan 1 veya 2'niz varsa Uç Noktalar için Güvenlik ve Office Plan 1 için Defender müşterileri Tehdit Analizi gibi öğeleri görmez.

> [!TIP]
> EOP, Office 365 için Defender temel öğesi olduğundan tüm Exchange Online Protection (EOP) işlevleri Microsoft 365 Defender dahil edilir.

## <a name="microsoft-365-defender-home-page"></a>Microsoft 365 Defender Giriş sayfası

Portalın Giriş sayfası, Microsoft 365 ortamınızın güvenlik durumu hakkında önemli özet bilgileri gösterir.

**Kılavuzlu turu** kullanarak Uç Nokta veya E-posta & işbirliği sayfalarında hızlı bir tura gidebilirsiniz. Burada gördükleriniz, Office 365 için Defender ve/veya Uç Nokta için Defender lisansınız olup olmadığınıza bağlıdır.

Ayrıca karşılaştırma için Güvenlik & Uyumluluk Merkezi'nin bağlantısı da bulunur. Son bağlantı, son güncelleştirmeleri açıklayan **Yenilikler** sayfasının bağlantısıdır.

## <a name="related-information"></a>İlgili bilgiler

- [Güvenlik & Uyumluluk Merkezi'nin Microsoft 365 Defender yeniden yönlendirilmesi](microsoft-365-security-mdo-redirection.md)
- [İşlem merkezi](./m365d-action-center.md)
- [E-posta & işbirliği uyarıları](../../compliance/alert-policies.md#default-alert-policies)
- [Özel algılama kuralları](/microsoft-365/security/defender-endpoint/custom-detection-rules)
- [Kimlik avı saldırısı simülasyonu oluşturma](../office-365-security/attack-simulation-training.md) ve [kişilerinizi eğitme yükü oluşturma](../office-365-security/attack-simulation-training-payloads.md)
