---
title: Adım 5. Kullanım durumlarını geliştirme ve sınama
description: Bu tür kullanım durumlarını güvenlik işlemleriyle tümleştirin Microsoft 365 Defender ve test etmeyle ilgili temel bilgiler.
keywords: olaylar, uyarılar, araştırma, korelasyon, saldırı, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, m365, olay yanıtı, siber saldırı, secops, güvenlik işlemleri, soc
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-m365dsecops
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 3019602f3b6120129243ab7a683da1d01f89bb1e
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63014178"
---
# <a name="step-5-develop-and-test-use-cases"></a>Adım 5. Kullanım durumlarını geliştirme ve sınama

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Güvenlik İşlemleri Merkezi'nde (SOC) Microsoft 365 Defender dağıtımı için önerilen yöntemler, SOC ekibinin güncel araç, süreç ve beceri kümeleri kümesine bağlıdır. Yüzlerce güvenlik kaynağı yoksa onlarcadan gelen çok büyük miktarda veri nedeniyle platformlarda siber tehditlere karşı korunması zor olabilir. 

Güvenlik araçları birbiriyle bağlantılıdır. Güvenlik teknolojisinin bir özelliğinin değiştirilmesi veya bir sürecin değiştirilmesi de başka bir özelliğin değiştirilmesine neden olabilir. Bu nedenle Microsoft, SOC ekibinin kullanım durumlarını tanımlama ve önceliklerini belirleme yöntemini resmileştirmelerini önermektedir. Vakaları kullanmak, çeşitli ekipler genelinde SOC işlemleri için gereksinimlerin ve test işlemlerinin tanımlarına yardımcı olur. Doğru rollerin ve çeşitli görevlerin doğru beceriler kümeleri ile doğru eksolojilerle uyumlu olup olmadığını belirlemek üzere ölçümleri yakalamak için bir yöntem oluşturur. 

## <a name="develop-and-formalize-use-case-process"></a>Kullanım durumu sürecini geliştirme ve resmileştirme

SOC, kullanım durumlarını geliştirmek için üst düzey bir standart ve süreç tanımlamalı ve SOC Gözetim ekibi tarafından düzenleyecektir. SOC Gözetimi ekibi, sonunda SOC ekibinin çalışma kitaplarına ve çalışma kitaplarına gelecek SOC kullanım durumlarının önceliklerini belirlemek için işletmeniz, IT, legal, İk ve diğer gruplarla birlikte çalışmalı. Kullanım durumlarının önceliği uyumluluk veya gizlilik gibi amaçları temel almaktadır.

Kullanım durumu geliştirme ile ilgili SOC Gözetim etkinlikleri şunlardır: 

- Gereksinimler
- Personel veya eğitim ihtiyaçları
- Yazılım lisansları
- Sözleşmeli satıcı
- Planı yönetme
- Kullanım durumu kayıt defterini koruma
- Şablonları koruma/güncelleştirme

Çalışma kitabı ve çalışma kitabı oluşturma işlemlerini kolaylaştırmak için kullanım durumu karar ağacı oluşturun. Bu şekilde bir örnek ve sayı 365'tir.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/use-case-decision-process.png" alt-text="Kullanım durumu karar süreci." lightbox="../../media/integrate-microsoft-365-defender-secops/use-case-decision-process.png":::

Üst düzey bir kullanım durumu standardı tanımlandıktan ve onaylandıktan sonra, bir sonraki adım gerçek kullanım durumu oluşturmak ve test etmektir. Aşağıdaki bölümlerde örnek olarak kimlik avı önleme ve tehdit ve güvenlik açığı tarama senaryoları kullanılır.

## <a name="use-case-example-1-new-phishing-variant"></a>Kullanım örneği 1: Yeni kimlik avı değişken

Kullanım durumu oluşturmanın ilk adımı, içerik panosu kullanarak iş akışının ana hatlarını oluşturmakdır. Burada, Tehdit İstihbaratı ekibine yönelik yeni kimlik avı açıkları hakkında bildirim almak için üst düzey bir hikaye panosu örneği ve bir örnek vemektedir.
 
:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-phishing.png" alt-text="Kimlik avı önleme kampanyası için örnek kullanım durumu iş akışı." lightbox="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-phishing.png":::

### <a name="invoke-the-use-case-workflow-for-example-1"></a>Kullanım durumu iş akışını çağırma (örneğin 1)

Anlatı panosu onaylandıktan sonra, bir sonraki adım kullanım durumu iş akışını çağırmak olur. Burada, kimlik avı önleme kampanyası için örnek bir işlem vemektedir. 
 
:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-phishing.png" alt-text="Kimlik avı önleme kampanyası için ayrıntılı kullanım durumu iş akışı örneği." lightbox="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-phishing.png":::

## <a name="use-case-example-2-threat-and-vulnerability-scanning"></a>Kullanım durumu örneği 2: Tehdit ve güvenlik açığı tarama

Bir kullanım durumu kullanıla bir diğer senaryo tehdit ve güvenlik açığı tarama için kullanılabilir. Bu örnekte SOC, tehdit ve güvenlik açıklarının, varlık tarama içeren onaylanmış işlemler aracılığıyla varlıklara yönelik olarak düzelt güncelleştirmesi gerektirmektedir. 

Burada, varlıklarının en iyi şekilde çalışma alanlarının Tehdit ve Güvenlik Açığı Yönetimi bir pano örneği vemektedir.
 
:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-tvm.png" alt-text="İş akışları için örnek kullanım durumu Tehdit ve Güvenlik Açığı Yönetimi." lightbox="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-tvm.png":::

### <a name="invoke-the-use-case-workflow-for-example-2"></a>Kullanım durumu iş akışını çağırma (örneğin 2)

Tehdit ve güvenlik açığı tarama için örnek bir süreç şu şekildedir.
 
:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-tvm.png" alt-text="İş Akışları için ayrıntılı kullanım durumu iş Tehdit ve Güvenlik Açığı Yönetimi." lightbox="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-tvm.png":::
 
### <a name="analyze-the-use-case-output-and-lessons-learned"></a>Kullanım durumu çıktısını ve öğrenilen dersleri çözümle

Kullanım durumu onaylandıktan ve test edildikten sonra, güvenlik ekipleriniz arasındaki boşluklar; kişiler, süreçler ve söz konusu Microsoft 365 Defender tanımlanır. Microsoft 365 Defender, istenen sonuçları elde etme yeteneğine sahip olup olduklarını belirlemek için bu teknolojilerin analiz olması gerekir. Bunlar bir denetim listesi veya matris aracılığıyla iz olabilir. 

Örneğin, kimlik avı önleme senaryo örneğinde, SOC ekipleri bu tabloda keşifler yapmış olabilir.


| SOC ekibi | Gereksinim | Gereksinimi karşılamak için insanlar | Gereksinimi karşılamak için işlem | İlgili teknoloji | Boşluk tanımlandı | Kullanım durumu değişiklik günlüğü | Muaf (Y/N) |
|:-------|:-----|:-------|:-------|:-------|:-----|:-------|:-------|
| Threat Intelligence and Analytics team | Veri kaynakları tehdit zekası altyapılarını düzgün bir şekilde besliyor. | Threat Intelligence Analyst/Engineer | Veri akışı gereksinimlerinin kurulması, tehdit İstihbaratı onaylı kaynaklardan tetiklenir | Kimlik için Microsoft Defender, Uç Nokta için Microsoft Defender | Threat Intelligence ekibi, yeni API'yi tehdit intel altyapıları ile Microsoft 365 Defender için otomasyon betiği kullanmadı | Tehdit Microsoft 365 Defender kaynakları olarak kullanıcı ekleme <BR> <BR> Kullanım durumu çalıştırma kitabını güncelleştir | N |
| Ekibi izleme | Veri kaynakları izleme panolarını düzgün bir şekilde besliyor | Katman 1,2 SOC Analisti–& Uyarıları | Raporlama için iş akışı & Uyumluluk Merkezi Güvenli Puanı | [Güvenlik ve Uyumluluk & Uyarılar](/microsoft-365/security/office-365-security/alerts)  <br><br> Güvenli Puan izleme  | SoC analistlerine, Güvenli Puanı geliştirmek için başarılı yeni kimlik avı değişken algılaması bildirme mekanizması yoktur <br><br> [Güvenlik ve Uyumluluk & raporlama](/microsoft-365/security/office-365-security/reports-and-insights-in-security-and-compliance)| Raporlama iş akışlarına Güvenli Puan iyileştirmesi izleme işlemi ekleme | N | 
| Mühendislik ve SecOps Ekibi | DEĞIŞIKLIK denetimi güncelleştirmeleri SOC ekip çalışma kitaplarında yapılır | Katman 2 SOC Engineer | SOC ekip çalışma kitapları için Denetim Bildirimi yordamını değiştirme | Güvenlik cihazlarında onaylanan değişiklikler | SOC güvenlik Microsoft 365 Defender bağlantısında yapılan değişiklikler onay gerektirir | Bulut Uygulamaları için Microsoft Defender, Kimlik için Defender, Uç Nokta için Defender, Güvenlik ve Uyumluluk & SOC çalışma kitaplarına ekleme | E |
|||||||||

Buna ek olarak, SOC ekipleri yukarıda açıklanan senaryoyla ilgili olarak aşağıdaki tabloda ana hatları Tehdit ve Güvenlik Açığı Yönetimi keşifler yapmış olabilir:

| SOC ekibi | Gereksinim | Gereksinimi karşılamak için insanlar | Gereksinimi karşılamak için işlem | İlgili teknoloji | Boşluk tanımlandı | Kullanım durumu değişiklik günlüğü | Muaf (Y/N) |
|:-------|:-----|:-------|:-------|:-------|:-----|:-------|:-------|
| SOC Oversight | Onaylanmış ağlara bağlı tüm varlıklar tanımlanır ve kategorilere ayrılmıştır | SOC Oversight, BU sahipleri, uygulama sahipleri, IT varlık sahipleri, vb. | Risklere dayalı varlık kategorisini ve özniteliklerini bulmak ve listeley etmek için merkezi varlık yönetim sistemi. | ServiceNow veya diğer varlıklar. <br><br>[Microsoft 365 Stoku](/security/defender-endpoint/device-discovery) | Varlıkların yalnızca %70'i bulundu. Microsoft 365 Defender düzeltme izleme yalnızca bilinen varlıklar için etkilidir | %100 kapsama sahip Microsoft 365 Defender için olgun varlık yaşam döngüsü yönetim hizmetleri | N |
| Mühendislik & SecOps Teams | Varlıklar üzerindeki yüksek etki ve kritik güvenlik açıkları ilkeye göre düzeltildi | SecOps engineers, SOC analistleri: Güvenlik & Güvenlik Mühendisliği Güvenlik Açığı | Yüksek Riskli ve Kritik Güvenlik Açıklarını kategorilere ayırmaya yönelik tanımlı işlem | [Tehdit ve Güvenlik Açığı Yönetim Panoları](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) | Uç Nokta için Defender, Microsoft'un önerilen etkinliklerini düzeltme planı veya uygulaması yoksa yüksek etkiyi olan yüksek uyarı cihazları belirledi | İlke başına 30 gün içinde düzeltme etkinliğinin gerekli olduğu varlık sahiplerini bildirmek için iş akışı ekleyin; Varlık sahiplerine düzeltme adımlarını bildirmek için bir bilet sistemi uygulayın. | N |
| İzleme Teams | Tehdit ve güvenlik açığı durumu şirket intranet portalı aracılığıyla bildiriliyor | Katman 2 SOC analisti | Raporlardan otomatik olarak oluşturulan Microsoft 365 Defender, varlıkların düzeltme ilerlemesini gösterir | [Güvenlik ve Uyumluluk & Uyarılar](/microsoft-365/security/office-365-security/alerts) <br><br> Güvenli Puan izleme | Varlıklara yönelik tehdit ve güvenlik açığı durumuyla ilgili olarak varlık sahiplerine herhangi bir görünüm veya pano raporu aktar aktar aktarnmz. | Kuruluşa yüksek riskli veya kritik varlık güvenlik açığının düzeltme durumunu doldurmak için otomasyon betiği oluşturun. | N |
|||||||||

Bu örnek kullanım durumlarında, bu test SOC ekibinin gereksinimlerinde, her ekibin sorumluluklarının temeli olarak temel olarak ortaya koyan bazı boşluklar ortaya çıkar. SOC ekibinin yeni veya mevcut SOC gereksinimleriyle tümleştirmeye hazır olduğundan emin olmak için, kullanım durumu denetim listesi Microsoft 365 Defender kapsamlı olabilir. Bu iteratif bir işlem olacağınından, kullanım durumu geliştirme süreci ve kullanım durumu çıktısı içeriği soc'un çalışma kitaplarını öğrenme ile güncelleştirmeye ve olgunlaştıracak şekilde doğal bir şekilde hizmet edecek.

## <a name="update-production-runbooks-and-playbooks"></a>Üretim çalışma kitaplarını ve çalışma kitaplarını güncelleştirme

Tüm boşluklar için kullanım durumu testi düzeltilenin, bu boşluklar için öğrenilen dersler ve bunlarda toplanan ölçümler SOC ekibinin üretim çalışma kitaplarına (işletim süreçleri) ve çalışma kitaplarına (olay yanıtları ve yükseltme yordamları) birikabilir. 

SOC ekip çalışma kitaplarının ve çalışma kitaplarının bakımı çok sayıda şekilde düzenleniyor. Her SOC ekibi kendi sorumluluğunda olabilir veya tüm ekiplerin merkezi bir depoda paylaşması için tek bir merkezi sürüm olabilir. Tek tek kuruluşlar için çalışma kitabı ve çalışma kitabı yönetimi, boyut, beceriler, roller ve görevlerin ayrımlarına dayalıdır. Çalışma kitabı güncelleştirildiğinde, çalışma kitabı güncelleştirme işleminin izlemesi gerekir. 

## <a name="use-a-standard-framework-for-escalation"></a>Yükseltme için standart çerçeve kullanma

Playbooks, başarılı bir tümleştirme ve kullanım durumu sınamasına dayalı olarak, gerçek bir etkinlik gerçekleşirken SOC ekiplerinin izlemesi gereken adımlardır. Bu nedenle SOC'nin, olay yanıtı için en önde gelen endüstri standartlarından biri haline gelen [NIST](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf) Olay Yanıt Standardı gibi, olay yanıtı için resmi bir yaklaşım benimser.

NIST dört adımlı olay yanıt süreci dört aşama içerir:

1.  Hazırlık
2.  Algılama ve çözümleme
3.  Içeren, s silme ve kurtarma
4.  Olay sonrası etkinlik

### <a name="example-tracking-preparation-phase-activity"></a>Örnek: İzleme hazırlık aşaması etkinliği

Yükseltme çalışma kitabının temel temellerinden biri, her SOC ekibinin bir olay veya olaydan önce, olay sırasında ve sonrasında ne yapması gerektiğinin biraz açıklığı olmamasını sağlamaktır. Bu nedenle, adım adım yönergeleri listeli yapmak iyi bir yöntemdir. 

Örneğin, Hazırlık aşaması görevlerin bir if/then veya XoR matrisini içerebilir. Yeni kimlik avı değişken örneğinde kullanım durumu söz konusu olduğu durumlarda, böyle bir matris aşağıdakine benzer olabilir:

| Yükseltme Neden Garanti Edildi? | Sonraki Adım |
|:-------|:-----|
| SOC İzlemesinde 500/saat için > **olarak derecelendirilen uyarı** | Çalışma Kitabı A, Bölüm 2, Etkinlik 5'e gidin (çalışma kitabı bölümüne bağlantı içeren) |
| eCommerce olası DDoS saldırılarını bildirdi | Invoke Playbook B-Section C, Activity 19 (çalışma kitabı bölümüne bağlantı içeren) |
| Yönetici kimlik avı girişimi olarak şüpheli bir e-posta bildirdi | Playbook 5, Bölüm 2, Etkinlik 5'e gidin (çalışma kitabı bölümüne bağlantı içeren) |
|||

Hazırlık aşamasını yürüttkten sonra, kuruluşlar NIST tarafından ana hatlarıyla belirtilen kalan aşamaları çağıracak şekilde çağırmaları gerekir:

- Algılama ve çözümleme
- Içeren, s silme ve kurtarma
- Olay sonrası etkinlik 

## <a name="next-step"></a>Sonraki adım

[6. Adım. SOC bakım görevlerini tanımlama](integrate-microsoft-365-defender-secops-tasks.md)
