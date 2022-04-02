---
title: Destek için Microsoft Defender Office 365 ı pilot olarak kullanma, değerlendirmeyi üretim ortamınız içinde kullanma
description: Destek için Microsoft Defender'ın özelliklerini doğru şekilde test etmek amacıyla Etkin ve mevcut kullanıcı gruplarıyla Değerlendirmenizi deneme Office 365.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 05/25/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: 58d7a8acd752eda36fe8ee73989105b54e746ddf
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755567"
---
# <a name="pilot-microsoft-defender-for-office-365"></a>Destek için Microsoft Defender'ı Office 365

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Bu makale, Microsoft Defender için değerlendirme ortamını ayarlama işleminin [3/ 3](eval-defender-office-365-overview.md). adımıdır ve Office 365. Bu işlem hakkında daha fazla bilgi için genel bakış [makalesine bakın](eval-defender-office-365-overview.md).

Aşağıdaki adımları kullanarak microsoft defender için pilot uygulama ayarlarını yapın ve Office 365.

![Destek için Microsoft Defender pilotları oluşturma Office 365.](../../media/defender/m365-defender-office-pilot.png)

- [1. Adım: Pilot grupları oluşturma](#step-1-create-pilot-groups)
- [2. Adım: Korumayı yapılandırma](#step-2-configure-protection)
- [3. Adım: Özellikleri deneyin: Benzetim, izleme ve ölçümlere aşinalık elde edin](#step-3-try-out-capabilities--get-familiar-with-simulation-monitoring-and-metrics)

Microsoft Defender'ı tüm Office 365 için ilkeleri etkinleştirmeden ve zorlamadan önce belirli kullanıcıları pilot olarak değerlendirmeyi seçebilirsiniz. Dağıtım grupları oluşturmak, dağıtım işlemlerinin yönetimine yardımcı olabilir. Örneğin, Office 365 Kullanıcıları için *Defender - Standart* Koruma, Office 365 Kullanıcıları için Defender - Katı Koruma, *Office 365* Kullanıcıları için *Defender -* Özel Koruma veya Office 365 için *Defender -* Özel Durumlar gibi gruplar oluşturun.

Bu gruplarda 'Standart' ve 'Katı' terimleri neden açık değildir; ancak güvenlik önayarları için Defender hakkında daha fazla bilgi Office 365 açık olur. "Özel" ve "özel durum" gruplarını adlandırmak kendileri için konuşsa da kullanıcılarının çoğu standart ve *katı, özel* durum grupları risk yönetimiyle ilgili olarak sizin için değerli veriler toplar.

## <a name="step-1-create-pilot-groups"></a>1. Adım: Pilot grupları oluşturma

Dağıtım grupları doğrudan şirket içinde oluşturulabilir ve Exchange Online Active Directory'den eşitlenir.

1. Alıcı Yöneticisi rolüne Exchange veya grup yönetimi izinleri temsilciliği verilmiş bir hesabı kullanarak Exchange Yönetim Merkezi'nde (EAC) oturum açın.
2. Gezinti menüsünde Alıcılar'ı genişletin *ve Gruplar'ı* *seçin*.

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-pilot.png" alt-text="Grup yönetim merkezinin (hızlı Exchange) gezinti menüsü ve Gruplar'ı işaret alan bir ok. Gruplar'a tıklayın" lightbox="../../media/mdo-eval/1_mdo-eval-pilot.png":::

3. Gruplar panosundan "Grup ekle"yi seçin.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-pilot-add-group.png" alt-text="Grup portalının Gruplar panelindeki Grup ekle Microsoft 365 Defender." lightbox="../../media/mdo-eval/2_mdo-eval-pilot-add-group.png":::

4. Grup türü olarak Dağıtım'ı *seçin ve* Sonraki'yi tıklatın.

   :::image type="content" source="../../media/mdo-eval/3-mdo-eval-pilot-group-type.png" alt-text="Grup portalının Grup türü Microsoft 365 Defender sayfası" lightbox="../../media/mdo-eval/3-mdo-eval-pilot-group-type.png":::

5. Gruba bir ad ve açıklama girin, ardından Sonraki'ye tıklayın.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-pilot-set-up-basics.png" alt-text="Yeni Portal'da Temel Microsoft 365 Defender ayarlama" lightbox="../../media/mdo-eval/4_mdo-eval-pilot-set-up-basics.png":::

## <a name="step-2-configure-protection"></a>2. Adım: Korumayı yapılandırma

Office 365 için Defender'daki bazı özellikler varsayılan olarak yapılandırılır ve açıktır, ancak güvenlik işlemleri varsayılandan koruma düzeyini yükseltmek istiyor olabilir.

Bazı özellikler *henüz yapılandırılmamıştır* . Korumayı yapılandırmak için üç seçeneğiniz vardır:

- **Önceden belirlenmiş güvenlik ilkelerini otomatik** olarak [atama — Önceden](../office-365-security/preset-security-policies.md) tanımlı güvenlik ilkeleri, tüm özellikler genelinde hızlıca tek tip bir koruma düzeyi atama yöntemi olarak sağlanır. **_standard_*_ veya _strict arasında seçim* _seçebilirsiniz_**. Önceden ayarlanmış güvenlik ilkeleriyle başlamak ve ardından, özellikler ve kendi benzersiz tehdit ortamınız hakkında daha fazla bilgi ediniyorsanız, ilkelere ince ayar yapmak iyi bir yaklaşımdır. Buradaki avantajı, kullanıcı gruplarını mümkün olan en hızlı şekilde korumanız ve sonrasında korumada ufak değişiklikler yapma olanağınızdır. (Bu yöntem önerilir.)
- **Taban çizgisi korumasını el** ile yapılandırma — Ortamı kendiniz yapılandırmayı tercih ederseniz, Tehditlere karşı  koruma konusunda yer alan kılavuzu takip ederseniz, hızla bir koruma temeli [elde edebilirsiniz](../office-365-security/protect-against-threats.md). Bu yaklaşımla, yapılandırılabilir ayarlar hakkında daha fazla bilgi edinebilirsiniz. Ayrıca, kuşkusuz daha sonra ilkelere ince ayar da veebilirsiniz.
- **Özel *koruma* ilkelerini yapılandırma** — Ayrıca değerlendirmenizin bir parçası olarak özel koruma ilkeleri oluşturabilir ve at at bulundurarak da atamanız gerekir. İlkeleri özelleştirmeye başlamadan önce, bu koruma ilkelerinin uygulandığı ve zorunlu tutularak uygulandığı öncelikleri anlamak önemlidir. Güvenlik ops need to create some policies when the preset is applied, in specific to define security policies for Kasa for Links and Kasa Attachments.

> [!IMPORTANT]
> **Özel koruma ilkelerini yapılandırmaya** gerek duyuyorsanız, Standart ve Katı güvenlik tanımlarını burada incelemelisiniz:  *[Güvenlik için önerilen EOP ayarları ve Güvenlik için Microsoft Defender Office 365 gerekir](../office-365-security/recommended-settings-for-eop-and-office365.md)*. Herhangi bir yapılandırma öncesinde de görülen varsayılan değerler de listelenir. Özel yapının her ikisinde de saptanan bir elektronik tabloyu tutabilirsiniz.

### <a name="assign-preset-security-policies"></a>Önceden belirlenmiş güvenlik ilkeleri atama

MDO'yu değerlendirirken önerilen temel ilkeleriyle başlamanız ve değerlendirme döneminiz boyunca gerektiğinde geliştirmeniz önerilir.

Bu koruma ilkelerini hızla etkinleştirmek için önerilen EOP Office 365 Defender'ı etkinleştirebilirsiniz ve değerlendirmenizin bir parçası olarak bunları belirli pilot kullanıcılara veya tanımlı gruplara atabilirsiniz. Önceden belirlenmiş ilkeler temel **Standart** koruma şablonu veya bağımsız olarak atanabilir ya da bir araya getirildiğinde daha katı bir koruma şablonu sağlar.

Adımların [vurgulu olduğu EOP ve Microsoft Defender'daki Office 365](../office-365-security/preset-security-policies.md) önceden belirlenmiş güvenlik ilkeleri makalesine bakın.

1. Microsoft 365 kiracıda oturum açma. Web portalına erişimi olan, Microsoft 365 Defender'de Kuruluş Yönetimi rolüne veya Office 365'de Güvenlik Yöneticisi rolüne ekli bir Microsoft 365.
2. Gezinti menüsünden, E-posta *ve İşbirliği'nin & İlkeler* ve & seçin.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-pilot-policies.png" alt-text="Gezinti bölmesindeki &-posta Ve İşbirliği'nin altında İlkeler ve Kurallar'& tıklayın.":::

3. İlke Ve & panosunda Tehdit *İlkeleri'ne tıklayın*.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-pilot-threat-policies.png" alt-text="Microsoft 365 Defender portalında Tehdit Microsoft 365 Defender öğesi" lightbox="../../media/mdo-eval/6-mdo-eval-pilot-threat-policies.png":::

4. Güvenlik Microsoft 365 Defender gezinti menüsünde Tehdit Yönetimi'ni genişletin ve ardından alt menüden İlke'yi seçin.
5. İlke panosunda İlke güvenlik *ilkeleri'ne tıklayın*.

   :::image type="content" source="../../media/mdo-eval/7-mdo-eval-pilot-template-policies.png" alt-text="Microsoft 365 Defender portalında Tehdit Microsoft 365 Defender sayfası" lightbox="../../media/mdo-eval/7-mdo-eval-pilot-template-policies.png":::

6. Standart *ilkeyi* ve/veya Katı ilkeyi yapılandırmak ve atamak için Düzenle'ye tıklayın.

   :::image type="content" source="../../media/mdo-eval/8-mdo-eval-pilot-preset.png" alt-text="Microsoft 365 Defender portalında Önceden belirlenmiş güvenlik ilkeleri sayfası" lightbox="../../media/mdo-eval/8-mdo-eval-pilot-preset.png":::

7. Gerektiğinde, belirli pilot kullanıcılara veya kullanıcı gruplarına taban çizgisi ***EOP** _ korumaları uygulamak için koşullar ekleyin ve devam etmek için _Next* seçin.

   Örnek olarak, Office 365 için Defender pilot değerlendirme koşulu, alıcılar Office 365 Standart Koruma için tanımlı bir *Defender* grubunun üyesi olursa ve  daha sonra yalnızca hesapları ekleyerek veya gruptan hesap kaldırarak yönetiliyorsa, pilot değerlendirmeler için bir koşul uygulanabilir.

   :::image type="content" source="../../media/mdo-eval/9-mdo-eval-pilot-eop-protections.png" alt-text="EOP korumaları EOP portalının Microsoft 365 Defender uygulanır" lightbox="../../media/mdo-eval/9-mdo-eval-pilot-eop-protections.png":::

8. Gerektiğinde, belirli pilot kullanıcılara veya kullanıcı gruplarına taban çizgisi ***MDO** _ korumaları uygulamak için koşullar ekleyin. Devam etmek _Next* düğmesini tıklatın.

   Örneğin, alıcılar Office 365 Standart Koruma grubu için tanımlı bir *Defender'a* üyeyse ve daha sonra grup üzerinden hesap  ekleme / kaldırma yoluyla yönetilen bir Pilot değerlendirmeler için Office 365 Defender koşulu uygulanabilir.

   :::image type="content" source="../../media/mdo-eval/10-mdo-eval-pilot-mdo-protections.png" alt-text="Güvenlik koruması Office 365 Defender, portalda yer alan Microsoft 365 Defender uygulanır" lightbox="../../media/mdo-eval/10-mdo-eval-pilot-mdo-protections.png":::

9. Önceden ayarlanmış güvenlik ilkeleri atamayla ilgili değişikliklerinizi gözden geçirin ve onaylayın.
10. Önceden belirlenmiş koruma ilkeleri, Microsoft 365 Defender portalı > İlkeler & kurallarına dönerek ve Önceden belirlenmiş güvenlik ilkeleri kutucuğuna tıklar >> yeniden yapılandırılabilir (yeniden yapılandırılabilir, yeniden uygulanabilir, devre dışı bırakılabilir,vb.).

### <a name="configure-custom-protection-policies"></a>Özel koruma ilkelerini yapılandırma

İlke ilke şablonları *için* *önceden tanımlanmış Standart* Office 365 Katı Defender, pilot kullanıcılarınıza önerilen temel korumasını sağlar. Bununla birlikte, değerlendirmenizin bir parçası olarak özel koruma ilkeleri de oluşturabilir ve at at bulundurarak bu ilkelere atamanız gerekir.

Bu koruma *ilkelerinin* uygulandığında ve zorunlu tutularak, E-posta korumasının sırası ve sırası gibi, bu koruma ilkelerinin [Office 365 önemlidir.](../office-365-security/how-policies-and-protections-are-combined.md)

Aşağıdaki tabloda, özel koruma ilkelerini yapılandırmak ve atamak için başvurular ve ek kılavuz bilgiler verilmiştir:

<br>

****

|İlke|Açıklama|Başvuru|
|:---:|---|---|
|Bağlantı Filtreleme|İyi veya kötü kaynak e-posta sunucularını IP adreslerine göre belirleme.|[EOP'de varsayılan bağlantı filtresi ilkesi yapılandırma](../office-365-security/configure-the-connection-filter-policy.md)|
|Kötü Amaçlı Yazılımdan Koruma|Hangi eylemlerin gerçekleştir yer alacakları ve kötü amaçlı yazılım algılandığında kimlerin bildir bağlantıları da içinde olmak üzere, kullanıcıları e-posta kötü amaçlı yazılımdan koruyun.|[EOP'de kötü amaçlı yazılımdan koruma ilkelerini yapılandırma](../office-365-security/configure-anti-malware-policies.md)|
|Anti-Spoofing|Kullanıcıları, bilgi e-postalarını ve bilgi e-postalarını kullanarak onları bilgi kullanma girişimlerine karşı koruyun.|[Office 365 için Defender'da kimlik kimlik Office 365](../office-365-security/learn-about-spoof-intelligence.md)|
|İstenmeyen Posta Önleme|İstenmeyen posta algılandığında hangi eylemlerin gerçekleştir adresleri de dahil olmak üzere, kullanıcıları e-posta istenmeyen postalardan koruyun.|[Office 365 için Defender'da istenmeyen posta önleme ilkelerini Office 365](../office-365-security/configure-your-spam-filter-policies.md)|
|Kimlik Avı Önleme|Kullanıcıları kimlik avı saldırılarından koruma ve şüpheli iletilere yönelik güvenlik ipuçlarını yapılandırma|[Kimlik avı koruması ilkelerini kimlik avı için Defender'da Office 365](../office-365-security/configure-mdo-anti-phishing-policies.md)|
|Kasa Ekleri Kaydetme|Kullanıcıları e-posta ekleri ve dosyalarında, e-posta SharePoint, OneDrive içeriğinden Teams.|[Office 365 için Defender'da güvenli ek ilkelerini Office 365](../office-365-security/set-up-safe-attachments-policies.md)|
|Güvenli Bağlantılar|Kullanıcıların e-posta iletilerine veya masaüstü uygulamalarına yönelik kötü amaçlı bağlantıları Office ve paylaşmalarını koruyun.|[Güvenlik ilkeleri için Defender'da güvenli bağlantılar Office 365](../office-365-security/set-up-safe-links-policies.md)|
|

## <a name="step-3-try-out-capabilities--get-familiar-with-simulation-monitoring-and-metrics"></a>3. Adım: Özellikleri deneyin: Benzetim, izleme ve ölçümlere aşinalık elde edin

Artık pilotnuz ayarlandı ve yapılandırıldı. Artık pilot uygulama için Microsoft Defender'a özgü raporlama, izleme ve saldırı benzetim araçlarına aşina Microsoft 365.

<br>

****

|Özellik|Açıklama|Daha fazla bilgi|
|---|---|---|
|Tehdit Gezgini|Tehdit Gezgini, Güvenlik İşlemleri ekiplerinin tehditleri araştırmalarına ve yanıtlamalarına ve Office 365'ta e-posta ve dosyalarda şüpheli kötü amaçlı yazılım ve kimlik avı bilgilerine yönelik bilgilerin yanı sıra diğer güvenlik tehditlerini ve risklerini incelemelerine yardımcı olan güçlü bir gerçek zamanlı araçtır.|[Tehdit Gezgini'nde görünümler ve gerçek zamanlı algılamalar](../office-365-security/threat-explorer-views.md)|
|Attack Simulator|Gerçek bir saldırı ortamınızı etkilemeden önce, Microsoft 365 Defender'daki gerçekçi saldırı senaryolarını çalıştırmak için kuruluş portalında Saldırı Benzetimi Eğitimi'ne sahipsiniz.|[Saldırı benzetimi eğitimlerini kullanmaya başlama](../office-365-security/attack-simulation-training-get-started.md)|
|Raporlar panosu|Sol gezinti menüsünde Raporlar'a tıklayın ve E-posta Gönder ve & genişletin. E-posta & işbirliği raporları, bazıları (gönderilere git' gibi düğmeler aracılığıyla) ve Posta Akışı durum özeti, En Üst Kötü Amaçlı Yazılım, Adres Mektup Birleştirme algılamaları, Güvenliği ihlal edilmiş kullanıcılar, Posta gecikme süresi, Kasa Bağlantılar ve Kasa ek raporları gibi eğilimleri göstermenizi sağlayacak güvenlik eğilimlerini saptamayla ilgili raporlardır. Bu ölçümler otomatik olarak oluşturulur.|[Raporları Görüntüleme](../office-365-security/view-email-security-reports.md)|
|

## <a name="next-steps"></a>Sonraki adımlar

[Uç Nokta için Microsoft Defender'ı Değerlendirme](eval-defender-endpoint-overview.md)

Windows için [Microsoft Defender'ı Değerlendirme genel görünümüne Office 365](eval-defender-office-365-overview.md)

Değerlendirme ve pilot uygulama için [genel bakış Microsoft 365 Defender](eval-overview.md)
