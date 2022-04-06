---
title: Pilot Office 365 için Microsoft Defender, değerlendirmeyi üretim ortamınız içinde kullanın
description: Değerlendirmenizin özelliklerini doğru şekilde test etmek için Etkin ve mevcut kullanıcı gruplarıyla Değerlendirmenizi pilot Office 365 için Microsoft Defender.
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
ms.openlocfilehash: d8cd0132c8b02ae29cf49c9a700a868fa3a93554
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64501365"
---
# <a name="pilot-microsoft-defender-for-office-365"></a>Pilot Office 365 için Microsoft Defender

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Bu makale, [değerlendirme ortamını ayarlama](eval-defender-office-365-overview.md) sürecindeki 3/ 3. Adımdır ve Office 365 için Microsoft Defender. Bu işlem hakkında daha fazla bilgi için genel bakış [makalesine bakın](eval-defender-office-365-overview.md).

Pilot uygulama ayarlarını yapmak ve yapılandırmak için aşağıdaki Office 365 için Microsoft Defender.

:::image type="content" source="../../media/defender/m365-defender-office-pilot.png" alt-text="Pilot uygulama portalında pilot Office 365 için Microsoft Defender adımları" lightbox="../../media/defender/m365-defender-office-pilot.png":::

- [1. Adım: Pilot grupları oluşturma](#step-1-create-pilot-groups)
- [2. Adım: Korumayı yapılandırma](#step-2-configure-protection)
- [3. Adım: Özellikleri deneyin: Benzetim, izleme ve ölçümlere aşinalık elde edin](#step-3-try-out-capabilities-and-get-familiar-with-simulation-monitoring-and-metrics)

İlkeleri Office 365 için Microsoft Defender için ilkeleri etkinleştirmeden ve zorlamadan önce belirli kullanıcıları pilot olarak başlatmayı seçebilirsiniz. Dağıtım grupları oluşturmak, dağıtım işlemlerinin yönetimine yardımcı olabilir. Örneğin, Kullanıcı Grupları - Standart Office 365 için Defender, *Office 365 için Defender* *Kullanıcılar -* Katı Koruma, Office 365 için Defender- Özel Koruma gibi *gruplar* *oluşturun veya Office 365 için Defender- Özel Durumlar*.

Bu gruplarda 'Standart' ve 'Katı' terimleri neden açık değildir; ancak bu durum, güvenlik önayarları hakkında daha fazla bilgi Office 365 için Defender açık hale gelecektir. "Özel" ve "özel durum" gruplarını adlandırmak kendileri için konuşsa da kullanıcılarının çoğu standart ve *katı, özel* durum grupları risk yönetimiyle ilgili olarak sizin için değerli veriler toplar.

## <a name="step-1-create-pilot-groups"></a>1. Adım: Pilot grupları oluşturma

Dağıtım grupları doğrudan kendi içinde oluşturulabilir ve Exchange Online kendi dağıtım gruplarından şirket içi Active Directory.

1. Alıcı Yöneticisi rolüne Exchange veya grup yönetimi izinleri temsilciliği verilmiş bir hesabı kullanarak Exchange Yönetim Merkezi'nde (EAC) oturum açın.
2. Gezinti menüsünde Alıcılar'ı genişletin *ve Gruplar'ı* *seçin*.

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-pilot.png" alt-text=" Tık tıklan olacak Gruplar menü öğesi" lightbox="../../media/mdo-eval/1_mdo-eval-pilot.png":::

3. Gruplar panosundan "Grup ekle"yi seçin.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-pilot-add-group.png" alt-text="Tıklı olmak için Grup ekle seçeneği" lightbox="../../media/mdo-eval/2_mdo-eval-pilot-add-group.png":::

4. Grup türü olarak Dağıtım'ı *seçin ve* Sonraki'yi tıklatın.

   :::image type="content" source="../../media/mdo-eval/3-mdo-eval-pilot-group-type.png" alt-text=" Grup türü seçin bölümü" lightbox="../../media/mdo-eval/3-mdo-eval-pilot-group-type.png":::

5. Gruba bir ad ve açıklama girin, ardından Sonraki'ye tıklayın.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-pilot-set-up-basics.png" alt-text="Temel bilgileri ayarlama bölümü" lightbox="../../media/mdo-eval/4_mdo-eval-pilot-set-up-basics.png":::

## <a name="step-2-configure-protection"></a>2. Adım: Korumayı yapılandırma

Bu Office 365 için Defender özellikleri varsayılan olarak yapılandırılır ve açıktır, ancak güvenlik işlemleri koruma düzeyini varsayılandan yükseltmek istiyor olabilir.

Bazı özellikler *henüz yapılandırılmamıştır* . Korumayı yapılandırmak için üç seçeneğiniz vardır:

- **Önceden belirlenmiş güvenlik ilkelerini otomatik** olarak [atama—Önceden](../office-365-security/preset-security-policies.md) ayarlanmış güvenlik ilkeleri, tüm özellikler genelinde hızlıca tek tip bir koruma düzeyi atamak için bir yöntem olarak sağlanır. **_standard_*_ veya _strict arasında seçim* _seçebilirsiniz_**. Önceden ayarlanmış güvenlik ilkeleriyle başlamak ve ardından, özellikler ve kendi benzersiz tehdit ortamınız hakkında daha fazla bilgi ediniyorsanız, ilkelere ince ayar yapmak iyi bir yaklaşımdır. Buradaki avantajı, kullanıcı gruplarını mümkün olan en hızlı şekilde korumanız ve sonrasında korumada ufak değişiklikler yapma olanağınızdır. (Bu yöntem önerilir.)
- **Taban çizgisi korumasını el** ile yapılandırma—Ortamı kendiniz yapılandırmayı tercih ederseniz, Tehditlere karşı  koruma konusunda yer alan kılavuzu takip ederseniz, hızla bir koruma temeli [elde edebilirsiniz](../office-365-security/protect-against-threats.md). Bu yaklaşımla, yapılandırılabilir ayarlar hakkında daha fazla bilgi edinebilirsiniz. Ayrıca, daha sonra ilkelere ince ayar da ebilirsiniz.
- **Özel *koruma* ilkelerini yapılandırma**— Ayrıca değerlendirmenizin bir parçası olarak özel koruma ilkeleri oluşturabilir ve at at bulundurarak da atamanız gerekir. İlkeleri özelleştirmeye başlamadan önce, bu koruma ilkelerinin uygulandığı ve zorunlu tutularak uygulandığı öncelikleri anlamak önemlidir. Güvenlik ops need to create some policies when the preset is applied, in specific to define security policies for Kasa for Links and Kasa Attachments.
> [!IMPORTANT]
> **Özel koruma ilkelerini yapılandırmaya** gerek duyuyorsanız, Standart ve Katı güvenlik tanımlarını burada ifade edilen  değerleri incelemelisiniz: EOP için önerilen ayarlar *[ve güvenlik Office 365 için Microsoft Defender gerekir](../office-365-security/recommended-settings-for-eop-and-office365.md)*. Herhangi bir yapılandırma öncesinde de görülen varsayılan değerler de listelenir. Özel yapının her ikisinde de saptanan bir elektronik tabloyu tutabilirsiniz.

### <a name="assign-preset-security-policies"></a>Önceden belirlenmiş güvenlik ilkeleri atama

MDO'yu değerlendirirken önerilen temel ilkeleriyle başlamanız ve değerlendirme döneminiz boyunca gerektiğinde geliştirmeniz önerilir.

Önerilen EOP ve koruma ilkelerini Office 365 için Defender etkinleştirebilirsiniz ve değerlendirmenizin bir parçası olarak bunları belirli pilot kullanıcılara veya tanımlı gruplara atabilirsiniz. Önceden belirlenmiş ilkeler, bağımsız **olarak** atanabilir veya bir araya  getirildiğinde temel Standart koruma şablonu veya daha katı bir Katı koruma şablonu sağlar.

[EOP'de önceden belirlenmiş güvenlik ilkeleri ve adımların Office 365 için Microsoft Defender](../office-365-security/preset-security-policies.md) bu makalede açıklanmıştır.

1. Microsoft 365 kiracıda oturum açma. Web portalına erişimi olan, Microsoft 365 Defender'de Kuruluş Yönetimi rolüne veya Office 365'de Güvenlik Yöneticisi rolüne ekli bir Microsoft 365.
2. Gezinti menüsünden, E-posta *ve İşbirliği'nin & İlkeler* ve & seçin.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-pilot-policies.png" alt-text=" the Policies & rules menu item to clicked" lightbox="../../media/mdo-eval/5_mdo-eval-pilot-policies.png":::

3. İlke Ve & panosunda Tehdit *İlkeleri'ne tıklayın*.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-pilot-threat-policies.png" alt-text=" Tıklı olacak Tehdit ilkeleri menü öğesi" lightbox="../../media/mdo-eval/6-mdo-eval-pilot-threat-policies.png":::

4. Güvenlik Microsoft 365 Defender gezinti menüsünde Tehdit Yönetimi'ni genişletin ve ardından alt menüden İlke'yi seçin.
5. İlke panosunda İlke güvenlik *ilkeleri'ne tıklayın*.

   :::image type="content" source="../../media/mdo-eval/7-mdo-eval-pilot-template-policies.png" alt-text="Tehdit ilkelerinin türleri" lightbox="../../media/mdo-eval/7-mdo-eval-pilot-template-policies.png":::

6. Standart *ilkeyi* ve/veya Katı ilkeyi yapılandırmak ve atamak için Düzenle'ye tıklayın.

   :::image type="content" source="../../media/mdo-eval/8-mdo-eval-pilot-preset.png" alt-text="Önceden belirlenmiş güvenlik ilkeleri sayfasındaki çeşitli ilkelere uygulanan çeşitli ayarlar" lightbox="../../media/mdo-eval/8-mdo-eval-pilot-preset.png":::

7. Gerektiğinde, belirli pilot kullanıcılara veya kullanıcı gruplarına taban çizgisi ***EOP** _ korumaları uygulamak için koşullar ekleyin ve devam etmek için _Next* seçin.

   Örnek Office 365 için Defender, alıcılar tanımlı bir *Office 365 için Defender Standart* Koruma grubuna üye ise ve daha sonra hesapları ekleyerek veya gruptan  hesap kaldırarak yönetiliyorsa, pilot değerlendirmeler için bir örnek koşul uygulanabilir.

   :::image type="content" source="../../media/mdo-eval/9-mdo-eval-pilot-eop-protections.png" alt-text="EOP koruması olarak kabul edilen ilkeler" lightbox="../../media/mdo-eval/9-mdo-eval-pilot-eop-protections.png":::

8. Gerektiğinde, belirli pilot kullanıcılara veya kullanıcı gruplarına taban çizgisi ***MDO** _ korumaları uygulamak için koşullar ekleyin. Devam etmek _Next* düğmesini tıklatın.

   Örneğin, Office 365 için Defender tanımlı bir Standart Koruma grubunun üyeleri olan ve daha sonra grup üzerinden hesap ekleme / kaldırma yoluyla yönetilen  bir *Office 365 için Defender* pilot değerlendirme koşulu uygulanabilir.

   :::image type="content" source="../../media/mdo-eval/10-mdo-eval-pilot-mdo-protections.png" alt-text="İlkeler korumanın korunması olarak Office 365 düşünülmektedir" lightbox="../../media/mdo-eval/10-mdo-eval-pilot-mdo-protections.png":::

9. Önceden ayarlanmış güvenlik ilkeleri atamayla ilgili değişikliklerinizi gözden geçirin ve onaylayın.
10. Önceden belirlenmiş koruma ilkeleri, Microsoft 365 Defender portalına > İlkeler & kurallarına dönerek ve Önceden belirlenmiş güvenlik ilkeleri kutucuğuna > Tehdit İlkeleri > tıklatarak yönetilebilir (yeniden yapılandırılabilir, yeniden uygulanır, devre dışı bırakılır, vb.).

### <a name="configure-custom-protection-policies"></a>Özel koruma ilkelerini yapılandırma

Önceden tanımlanmış Standart *veya* *Katı* Office 365 için Defender ilke şablonları pilot kullanıcılarınıza önerilen temel korumasını sağlar. Bununla birlikte, değerlendirmenizin bir parçası olarak özel koruma ilkeleri de oluşturabilir ve at at bulundurarak bu ilkelere atamanız gerekir.

Bu koruma *ilkelerinin* uygulandığında ve zorunlu tutularak, E-posta korumasının sırası ve sırası gibi, bu koruma ilkelerinin [Office 365 önemlidir.](../office-365-security/how-policies-and-protections-are-combined.md)

Aşağıdaki tabloda, özel koruma ilkelerini yapılandırma ve atamayla ilgili başvurular ve daha fazla kılavuz verilmiştir:

<br>

****

|İlke|Açıklama|Başvuru|
|:---:|---|---|
|Bağlantı Filtreleme|İyi veya kötü kaynak e-posta sunucularını IP adreslerine göre belirleme.|[EOP'de varsayılan bağlantı filtresi ilkesi yapılandırma](../office-365-security/configure-the-connection-filter-policy.md)|
|Kötü Amaçlı Yazılımdan Koruma|Hangi eylemlerin gerçekleştir yer alacakları ve kötü amaçlı yazılım algılandığında kimlerin bildir bağlantıları da içinde olmak üzere, kullanıcıları e-posta kötü amaçlı yazılımdan koruyun.|[EOP'de kötü amaçlı yazılımdan koruma ilkelerini yapılandırma](../office-365-security/configure-anti-malware-policies.md)|
|Anti-Spoofing|Kullanıcıları, bilgi e-postalarını ve bilgi e-postalarını kullanarak onları bilgi kullanma girişimlerine karşı koruyun.|[Kimlik bilgisinde kimlik Office 365 için Defender](../office-365-security/learn-about-spoof-intelligence.md)|
|İstenmeyen Posta Önleme|İstenmeyen posta algılandığında hangi eylemlerin gerçekleştir adresleri de dahil olmak üzere, kullanıcıları e-posta istenmeyen postalardan koruyun.|[E-postada istenmeyen posta önleme ilkelerini Office 365 için Defender](../office-365-security/configure-your-spam-filter-policies.md)|
|Kimlik Avı Önleme|Kullanıcıları kimlik avı saldırılarından koruma ve şüpheli iletilere yönelik güvenlik ipuçlarını yapılandırma|[E-postada kimlik avı önleme ilkelerini Office 365 için Defender](../office-365-security/configure-mdo-anti-phishing-policies.md)|
|Kasa Ekleri Kaydetme|Kullanıcıları e-posta ekleri ve dosyalarında, e-posta SharePoint, OneDrive içeriğinden Teams.|[E-postada güvenli ek Office 365 için Defender](../office-365-security/set-up-safe-attachments-policies.md)|
|Güvenli Bağlantılar|Kullanıcıların e-posta iletilerine veya masaüstü uygulamalarına yönelik kötü amaçlı bağlantıları Office ve paylaşmalarını koruyun.|[Web'de güvenli bağlantı ilkeleri Office 365 için Defender](../office-365-security/set-up-safe-links-policies.md)|
|

## <a name="step-3-try-out-capabilities-and-get-familiar-with-simulation-monitoring-and-metrics"></a>3. Adım: Özellikleri deneyin ve benzetim, izleme ve ölçümlerle ilgili bilgi sahibi olur

Artık pilotnuz ayarlandı ve yapılandırıldı. Artık pilot uygulama için Microsoft Defender'a özgü raporlama, izleme ve saldırı benzetim araçlarına aşina Microsoft 365.

<br>

****

|Özellik|Açıklama|Daha fazla bilgi|
|---|---|---|
|Tehdit Gezgini|Tehdit Gezgini, Güvenlik İşlemleri ekiplerinin tehditleri araştırmalarına ve yanıtlamalarına ve Office 365'ta e-posta ve dosyalarda şüpheli kötü amaçlı yazılım ve kimlik avı bilgilerine yönelik bilgilerin yanı sıra diğer güvenlik tehditlerini ve risklerini incelemelerine yardımcı olan güçlü bir gerçek zamanlı araçtır.|[Tehdit Gezgini'nde görünümler ve gerçek zamanlı algılamalar](../office-365-security/threat-explorer-views.md)|
|Attack Simulator|Gerçek bir saldırı ortamınızı etkilemeden önce savunmasız kullanıcıları tanımlamanıza ve bu kullanıcılara yardımcı olan gerçekçi saldırı senaryoları çalıştırmak için Microsoft 365 Defender portalında Saldırı Benzetimi Eğitimi'ne sahipsiniz.|[Kullanmaya başlayın benzetimi eğitimlerini kullanma](../office-365-security/attack-simulation-training-get-started.md)|
|Raporlar panosu|Sol gezinti menüsünde Raporlar'a tıklayın ve E-posta Gönder ve & genişletin. E-posta & işbirliği raporları, bazıları (gönderilere git' gibi düğmeler aracılığıyla) ve Posta Akışı durum özeti, En Yüksek Kötü Amaçlı Yazılım, Adres Mektup Birleştirme algılamaları, Güvenliği ihlal edilmiş kullanıcılar, Posta gecikme süresi, Kasa Bağlantıları ve Kasa ek raporları gibi eğilimleri göstermenizi sağlayacak güvenlik eğilimlerini saptamayla ilgili raporlardır. Bu ölçümler otomatik olarak oluşturulur.|[Raporları Görüntüleme](../office-365-security/view-email-security-reports.md)|
|

## <a name="next-steps"></a>Sonraki adımlar

[Uç Nokta için Microsoft Defender'ı Değerlendirme](eval-defender-endpoint-overview.md)

Değerlendirme görünümüne genel [bakış Office 365 için Microsoft Defender](eval-defender-office-365-overview.md)

Değerlendirme ve pilot uygulama için [genel bakış Microsoft 365 Defender](eval-overview.md)
