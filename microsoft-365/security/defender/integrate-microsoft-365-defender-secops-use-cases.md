---
title: Adım 5. Kullanım örneklerini geliştirme ve test edin
description: Microsoft 365 Defender güvenlik işlemlerinizle tümleştirirken kullanım örnekleri geliştirme ve test etmeyle ilgili temel bilgiler.
keywords: olaylar, uyarılar, araştırma, bağıntı, saldırı, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, Microsoft, m365, olay yanıtı, siber saldırı, secops, güvenlik işlemleri, soc
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
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
ms.openlocfilehash: 4c65943ac28315f54e6c2f4cc8b2314e810b291f
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438090"
---
# <a name="step-5-develop-and-test-use-cases"></a>Adım 5. Kullanım örneklerini geliştirme ve test edin

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- Microsoft 365 Defender

Güvenlik İşlemleri Merkezi'nde (SOC) Microsoft 365 Defender dağıtmak için önerilen yöntemler, SOC ekibinin geçerli araç, işlem ve beceri kümelerine bağlıdır. Yüzlerce güvenlik kaynağı olmasa da onlarca veriden gelen muazzam miktarda veri nedeniyle platformlar arasında siber hijyenin korunması zor olabilir.

Güvenlik araçları birbiriyle ilişkilidir. Bir güvenlik teknolojisindeki bir özelliği açmak veya bir işlemi değiştirmek başka bir özelliği bozabilir. Bu nedenle Microsoft, SOC ekibinizin kullanım örneklerini tanımlamaya ve önceliklendirmeye yönelik bir yöntemi resmileştirmesini önerir. Kullanım örnekleri, çeşitli ekiplerde SOC işlemleri için gereksinimleri ve test süreçlerini tanımlamaya yardımcı olur. Doğru rollerin ve görev karışımının doğru beceri kümeleriyle doğru takıma hizalanıp hizalanmadığını belirlemek için ölçümleri yakalamak için bir metodoloji oluşturur.

## <a name="develop-and-formalize-use-case-process"></a>Kullanım örneği sürecini geliştirme ve resmileştirme

SOC, SOC Gözetim ekibi tarafından düzenlenecek olan kullanım örnekleri geliştirmek için üst düzey bir standart ve süreç tanımlamalıdır. SOC Gözetim ekibi, SOC ekibinin runbook'larına ve playbook'larına girebilecek SOC kullanım örneklerini önceliklendirmek için işletmeniz, BT, hukuk, İk ve diğer gruplarla birlikte çalışmalıdır. Kullanım örneklerinin önceliği, uyumluluk veya gizlilik gibi hedeflere bağlıdır.

Kullanım örneği geliştirmeyle ilgili SOC Gözetim etkinlikleri şunlardır:

- Gereksinimler
- Personel veya eğitim gereksinimleri
- Yazılım lisansları
- Satıcı sözleşmesi
- Planı yönetme
- Kullanım örneği kayıt defterini koruma
- Şablonları koruma/güncelleştirme

Runbook ve playbook oluşturma işlemlerini kolaylaştırmak için bir kullanım örneği karar ağacı oluşturun. Bu şekilde bir örnek gösterilmektedir.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/use-case-decision-process.png" alt-text="Kullanım örneği karar süreci" lightbox="../../media/integrate-microsoft-365-defender-secops/use-case-decision-process.png":::

Üst düzey kullanım örneği standardı tanımlanıp onaylandıktan sonra, bir sonraki adım gerçek bir kullanım örneği oluşturup test etmektir. Aşağıdaki bölümlerde örnek olarak kimlik avı önleme ve tehdit ve güvenlik açığı tarama senaryoları kullanılır.

## <a name="use-case-example-1-new-phishing-variant"></a>Kullanım örneği 1: Yeni kimlik avı değişkeni

Kullanım örneği oluşturmanın ilk adımı, bir yazı panosu kullanarak iş akışının ana hatlarını oluşturmaktır. Burada, Tehdit Bilgileri ekibine yeni kimlik avı açıklarından yararlanma bildirimi için üst düzey bir hikaye panosu örneği verilmiş.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-phishing.png" alt-text="Kimlik avından koruma kampanyası için kullanım örneğinin iş akışı" lightbox="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-phishing.png":::

### <a name="invoke-the-use-case-workflow-for-example-1"></a>Kullanım örneği iş akışını çağırın, örneğin 1

İçerik panosu onaylandıktan sonra, sonraki adım kullanım örneği iş akışını çağırmaktır. Kimlik avı önleme kampanyası için örnek bir süreç aşağıda verilmiştir.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-phishing.png" alt-text="Kimlik avı önleme kampanyası için ayrıntılı bir kullanım örneği iş akışı" lightbox="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-phishing.png":::

## <a name="use-case-example-2-threat-and-vulnerability-scanning"></a>Kullanım örneği 2: Tehdit ve güvenlik açığı taraması

Kullanım örneğinin kullanılabilmesi için bir diğer senaryo da tehdit ve güvenlik açığı taramasıdır. Bu örnekte SOC, varlıkların taranması da dahil olmak üzere onaylı işlemler aracılığıyla varlıklara karşı tehditlerin ve güvenlik açıklarının giderilmesini gerektirir.

Varlıkların Tehdit ve Güvenlik Açığı Yönetimi için örnek bir üst düzey görsel taslak aşağıda verilmiştir.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-tvm.png" alt-text="Tehdit ve Güvenlik Açığı Yönetimi için kullanım örneği iş akışı" lightbox="../../media/integrate-microsoft-365-defender-secops/example-use-case-workflow-storyboard-tvm.png":::

### <a name="invoke-the-use-case-workflow-for-example-2"></a>Kullanım örneği iş akışını çağırma örneğin 2

Tehdit ve güvenlik açığı taraması için örnek bir işlem aşağıda verilmiştir.

:::image type="content" source="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-tvm.png" alt-text="Tehdit ve Güvenlik Açığı Yönetimi için ayrıntılı kullanım örneği iş akışı" lightbox="../../media/integrate-microsoft-365-defender-secops/example-detailed-use-case-workflow-tvm.png":::

### <a name="analyze-the-use-case-output-and-lessons-learned"></a>Kullanım örneği çıkışını ve öğrenilen dersleri analiz etme

Bir kullanım örneği onaylandıktan ve test edildikten sonra, güvenlik ekipleriniz arasındaki boşluklar ve ilgili kişiler, süreçler ve Microsoft 365 Defender teknolojileri belirlenmelidir. Microsoft 365 Defender teknolojilerin istenen sonuçlara ulaşıp ulaşamadığını belirlemek için analiz edilmelidir. Bunlar bir denetim listesi veya matris aracılığıyla izlenebilir.

Örneğin, kimlik avına karşı koruma senaryosu örneğinde SOC ekipleri bu tabloda keşifler yapmış olabilir.

|SOC ekibi|Gereksinim|Gereksinimi karşılayacak kişiler|Gereksinimi karşılama süreci|İlgili teknoloji|Tanımlanan boşluk|Kullanım örneği değişiklik günlüğü|Muaf (Y/N)|
|---|---|---|---|---|---|---|---|
|Tehdit Analizi ve Analiz ekibi|Veri kaynakları tehdit bilgileri altyapılarını düzgün bir şekilde besliyor.|Tehdit Analizi Analisti/Mühendis|Veri akışı gereksinimleri oluşturuldu, onaylanan kaynaklardan gelen tehdit bilgileri tetikleyicileri|Kimlik için Microsoft Defender, Uç Nokta için Microsoft Defender|Tehdit Bilgileri ekibi, Microsoft 365 Defender API'sini tehdit intel altyapılarıyla bağlamak için otomasyon betiğini kullanmadı|Tehdit altyapılarına veri kaynağı olarak Microsoft 365 Defender ekleme <BR> <BR> Kullanım örneği çalıştırma kitabını güncelleştirme|N|
|İzleme ekibi|Veri kaynakları izleme panolarını düzgün şekilde besliyor|Katman 1,2 SOC Analisti-İzleme & Uyarıları|Güvenlik & Uyumluluk Merkezi Güvenli Puanını raporlamaya yönelik iş akışı|[Güvenlik & Uyumluluk Merkezi'ndeki uyarılar](/microsoft-365/security/office-365-security/alerts)  <br><br> Güvenli Puan izleme|SOC analistlerinin Güvenli Puanı geliştirmek için başarılı yeni kimlik avı değişken algılamasını bildirmesi için bir mekanizma yok <br><br> [Güvenlik & Uyumluluk Merkezi'nde raporlama](/microsoft-365/security/office-365-security/reports-and-insights-in-security-and-compliance)|Raporlama iş akışlarına Güvenli Puan iyileştirmesini izlemeye yönelik bir işlem ekleme|N|
|Mühendislik ve SecOps Ekibi|Değişiklik denetimi güncelleştirmeleri SOC ekip runbook'larında yapılır|Katman 2 SOC Mühendisi|SOC ekip runbook'ları için Denetim bildirimi yordamını değiştirme|Güvenlik cihazlarında onaylanan değişiklikler|SOC güvenlik teknolojisine Microsoft 365 Defender bağlantıda yapılan değişiklikler onay gerektirir|SOC runbook'larına Microsoft Defender for Cloud Apps, Kimlik için Defender, Uç Nokta için Defender, Güvenlik & Uyumluluk Merkezi ekleme|E|

Ayrıca SOC ekipleri, yukarıda özetlenen Tehdit ve Güvenlik Açığı Yönetimi senaryosuyla ilgili olarak aşağıdaki tabloda özetlenen keşifleri yapmış olabilir:

|SOC ekibi|Gereksinim|Gereksinimi karşılayacak kişiler|Gereksinimi karşılama süreci|İlgili teknoloji|Tanımlanan boşluk|Kullanım örneği değişiklik günlüğü|Muaf (Y/N)|
|---|---|---|---|---|---|---|---|
|SOC Gözetim|Onaylanan ağlara bağlı tüm varlıklar tanımlanır ve kategorilere ayrılmıştır|SOC Gözetim, BU sahipleri, uygulama sahipleri, BT varlık sahipleri vb.|Risk temelinde varlık kategorisini ve özniteliklerini bulmak ve listelemek için merkezi varlık yönetim sistemi.|ServiceNow veya diğer varlıklar. <br><br>[cihaz envanteri Microsoft 365](/microsoft-365/security/defender-endpoint/device-discovery)|Varlıkların yalnızca %70'i bulundu. Microsoft 365 Defender düzeltme izlemesi yalnızca bilinen varlıklar için geçerlidir|Microsoft 365 Defender %100 kapsama sahip olduğundan emin olmak için olgun varlık yaşam döngüsü yönetim hizmetleri|N|
|Mühendislik & SecOps Teams|Varlıklardaki yüksek etki ve kritik güvenlik açıkları ilkeye göre düzeltilir|SecOps mühendisleri, SOC analistleri: Güvenlik açığı & Uyumluluğu, Güvenlik Mühendisliği|Yüksek Risk ve Kritik Güvenlik Açıklarını kategorilere ayırmak için tanımlanan işlem|[Tehdit ve Güvenlik Açığı Yönetimi Panoları](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)|Uç Nokta için Defender, microsoft tarafından önerilen etkinliğin düzeltme planı veya uygulaması olmayan yüksek etki, yüksek uyarı cihazları tanımladı|İlke başına 30 gün içinde düzeltme etkinliği gerektiğinde varlık sahiplerini bilgilendirmek için bir iş akışı ekleyin; Varlık sahiplerine düzeltme adımlarını bildirmek için bir bilet sistemi uygulayın.|N|
|İzleme Teams|Tehdit ve güvenlik açığı durumu şirket intranet portalı aracılığıyla bildirilir|Katman 2 SOC analisti|Varlıkların düzeltme ilerleme durumunu gösteren Microsoft 365 Defender otomatik olarak oluşturulan raporlar|[Güvenlik & Uyumluluk Merkezi'ndeki uyarılar](/microsoft-365/security/office-365-security/alerts) <br><br> Güvenli Puan izleme|Varlıkların tehdit ve güvenlik açığı durumuyla ilgili olarak varlık sahiplerine hiçbir görünüm veya pano raporu iletilmeyen.|Kuruluş için yüksek riskli ve kritik varlık güvenlik açığı düzeltme durumunu doldurmak için otomasyon betiği oluşturun.|N|

Bu örnek kullanım örneklerinde test, SOC ekibinin gereksinimlerinde her ekibin sorumlulukları için temel olarak oluşturulmuş çeşitli boşluklar ortaya çıkardı. SOC ekibinin yeni veya mevcut SOC gereksinimleriyle Microsoft 365 Defender tümleştirmeye hazır olduğundan emin olmak için kullanım örneği denetim listesi gerektiği kadar kapsamlı olabilir. Bu yinelemeli bir süreç olacağından, kullanım örneği geliştirme süreci ve kullanım örneği çıktı içeriği doğal olarak SOC'nin runbook'larını öğrenilen derslerle güncelleştirmeye ve olgun etmeye yarar.

## <a name="update-production-runbooks-and-playbooks"></a>Üretim runbook'larını ve playbook'larını güncelleştirme

Kullanım örneği testi tüm boşluklar için düzeltildikten sonra, öğrenilen dersler ve bunlarda toplanan ölçümler SOC ekibinizin üretim runbook'larına (işletim süreçleri) ve playbook'larına (olay yanıtları ve yükseltme yordamları) eklenebilir.

SOC ekibi runbook'larının ve playbook'larının bakımı birçok yolla düzenlenebilir. Her SOC ekibi kendilerinden sorumlu olabilir veya tüm ekiplerin merkezi bir depoda paylaşabileceği tek bir merkezi sürüm olabilir. Tek tek kuruluşlar için runbook ve playbook yönetimi, görevlerin boyutunu, beceri kümelerini, rollerini ve ayrımını temel alır. Bir runbook güncelleştirildikten sonra playbook güncelleştirme işlemi izlenmelidir.

## <a name="use-a-standard-framework-for-escalation"></a>Yükseltme için standart çerçeve kullanma

Playbook'lar, kullanım örneğinin başarılı tümleştirmesine ve testine bağlı olarak gerçek bir olay gerçekleştiğinde SOC ekiplerinin izlemesi gereken adımlardır. Bu nedenle, SOC'nin olay yanıtı için önde gelen endüstri standartlarından biri haline gelen [NIST Olay Yanıtı Standardı](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf) gibi olay yanıtına yönelik resmi bir yaklaşım izlemesi zorunludur.

NIST dört adımlı olay yanıtı işlemi dört aşama içerir:

1. Hazırlık
2. Algılama ve analiz
3. Kapsama, silme ve kurtarma
4. Olay sonrası etkinlik

### <a name="example-tracking-preparation-phase-activity"></a>Örnek: Hazırlık aşaması etkinliğini izleme

Yükseltme playbook'unun temel temellerinden biri, her SOC ekibinin bir etkinlik veya olaydan önce, olay sırasında ve sonrasında ne yapması gerektiğiyle ilgili çok az belirsizlik olduğundan emin olmaktır. Bu nedenle, adım adım yönergeleri listelemek iyi bir uygulamadır.

Örneğin, Hazırlık aşaması bir if/then veya XoR görev matrisi içerebilir. Yeni kimlik avı değişken örneği kullanım örneği söz konusu olduğunda, böyle bir matris aşağıdaki gibi görünebilir:

|Yükseltme Neden Garanti Edilir?|Sonraki Adım|
|---|---|
|SoC İzleme'de uyarı, **500/saat** > **kritik** olarak tetiklenmiş olarak derecelendirilmiştir|Playbook A, Bölüm 2, Etkinlik 5'e gidin (playbook bölümünün bağlantısıyla)|
|e-Ticaret olası DDoS saldırısı bildirdi|Playbook B-Section C, Etkinlik 19'u çağırma (playbook bölümünün bağlantısıyla)|
|Yönetici şüpheli bir e-postayı zıpkınla kimlik avı girişimi olarak bildirdi|Playbook 5, Bölüm 2, Etkinlik 5'e gidin (playbook bölümünün bağlantısıyla)|

Hazırlık aşamasını yürüten kuruluşlar, NIST tarafından özetlenen kalan aşamaları çağırmalıdır:

- Algılama ve analiz
- Kapsama, silme ve kurtarma
- Olay sonrası etkinlik

## <a name="next-step"></a>Sonraki adım

[6. Adım. SOC bakım görevlerini tanımlama](integrate-microsoft-365-defender-secops-tasks.md)
