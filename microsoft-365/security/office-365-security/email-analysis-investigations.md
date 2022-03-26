---
title: Office 365 için Microsoft Defender ile ilgili araştırmalarda e-posta Office 365
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
keywords: otomatik olay yanıtı, araştırma, düzeltme, tehdit koruması
description: Daha fazla bilgi için Microsoft Defender'da soruşturmalarda e-posta çözümlemesi Office 365.
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5c4d1be31742d21f6e7919a8db4a3d2aff75f66e
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775400"
---
# <a name="email-analysis-in-investigations-for-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender ile ilgili araştırmalarda e-posta Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Office 365 için Microsoft Defender plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Uyarıların otomatik olarak soruşturması sırasında Office 365 için Microsoft Defender orijinal e-postayı tehditlere karşı analiz eder ve özgün e-posta ile ilgili diğer e-postaları tanımlar ve saldırının bir parçası olabilir. E-posta saldırıları nadiren tek bir e-postadan oluşur, çünkü bu çözümleme önemlidir.

Otomatik araştırmanın e-posta çözümlemesi, özgün e-postadan gelen öznitelikleri kullanarak e-posta kümelerini, sizin tarafından gönderilen ve alınan e-postaları sorgulamaya tanımlar. Bu, güvenlik işlemleri analisti'nin Gezgin'de veya Gelişmiş Sındır'da ilgili e-postaları aramalarına benzer. Tipik olarak güvenlik algılamayı önlemek için e-posta parametrelerine dönüşüm uygulamalarından dolayı eşleşen e-postaları tanımlamak için çeşitli sorgular kullanılır. Kümeleme çözümlemesi, soruşturmaya dahil olan e-postaların nasıl işlenmeli olduğunu belirlemek için şu denetimleri gerçekleştirir:

- E-posta çözümlemesi, ilişkili e-postaları bulmak için özgün e-postadan (IP adresi, gönderen etki alanı) ve içeriği (konu, küme kimliği) olan öznitelikleri kullanarak e-posta sorguları (kümeler) oluşturur.
- Özgün e-postanın URL'lerinin ve dosyalarının çözümlemesi, bazılarının kötü amaçlı (başka bir ifadeyle, kötü amaçlı yazılım veya kimlik avı) olduğunu tanımlarsa, ayrıca kötü amaçlı URL veya dosya içeren sorgular veya e-posta kümeleri oluşturur.
- E-posta kümeleme çözümlemesi, e-postaların kötü amaçlı, şüpheli veya net bir tehdit olup olmadığını belirlemek için kümede eşleşen e-postalarla ilişkilendirilmiş tehditleri sayar. Sorguyla eşleşen e-posta kümesi yeterli miktarda istenmeyen postaya, normal kimlik avına, yüksek güvene sahip kimlik avına veya kötü amaçlı yazılıma yönelik tehditlere sahipse, e-posta kümesi bu tehdit türünü ona uygulanır.
- E-posta kümeleme çözümlemesi, e-postaların hala kaldırılması ya da zaten düzeltilemenin ya da engellenmenin gerek olup olduğunu belirlemek için, özgün e-postanın ve e-posta kümelerinin en son teslim konumunu da denetler. Bu çözümleme önemlidir çünkü saldırganlar kötü amaçlı içeriğe dönüşümle birlikte güvenlik ilkeleri ve koruma, posta kutuları arasında farklılık gösterebilir. Bu özellik, bir veya birden çok kötü amaçlı e-posta sıfır saatlik otomatik temizleme (ZAP) tarafından algı edilip kaldırılmış olsa bile, kötü amaçlı içeriğin posta kutularında hala bulunduğu durumlara yol açabiliyor.
- Kötü amaçlı yazılım, yüksek güven amaçlı kimlik avı, kötü amaçlı dosyalar veya kötü amaçlı URL tehditlerinden dolayı kötü amaçlı olarak kabul edilen e-posta kümeleri, hala bulut posta kutusunda (gelen kutusu veya gereksiz klasör) olduğunda e-postaları yumuşak bir şekilde silmek için bekleyen bir eylem alır. Kötü amaçlı e-postalar veya e-posta kümeleri bulut posta kutusunda yok olarak yalnızca "Posta Kutusunda Değil" (engellendi, karantinaya alındı, başarısız, yumuşak silinmiş vb.) veya "Şirket İçi/Dış" ise, bunları kaldırmak için bekleyen eylem ayarlanmaz.
- E-posta kümelerden herhangi biri kötü amaçlı olarak belirlenirse, küme tarafından tanımlanan tehdit, soruşturmada yer alan özgün e-postaya geri uygulanır. Bu davranış, eşleşen e-postalara dayalı özgün bir e-postanın kararını belirlemek için e-posta arama sonuçlarını kullanan güvenlik işlemleri analisti olan bir güvenlik işlemi analiste benzer. Bu sonuç, özgün e-postanın URL'leri, dosyaları veya kaynak e-posta göstergelerinin algılanmasına veya algılanmasına bakılmaksızın sistem kişiselleştirme, dönüşüm, selamlama veya diğer tekniklerle olası olarak kurtulma olasılığı bulunan kötü amaçlı e-postaları tanımlayabilir.
- Kullanıcı güvenliği araştırmasında, posta kutusu tarafından oluşturulan olası e-posta sorunlarını tanımlamak için ek e-posta kümeleri oluşturulur. Bu işlem, temiz bir e-posta kümesi (kullanıcıdan gelen iyi e-postalar, olası veri sızıntıları ve olası komut/denetim e-postaları), şüpheli e-posta kümelerini (istenmeyen posta veya normal kimlik avı içeren e-postalar) ve kötü amaçlı e-posta kümelerini (kötü amaçlı yazılım veya yüksek güven avı içeren e-postalar) içerir. Bu e-posta kümeleri güvenlik işlemleri analistlerine, güvenlik işlemleri analistlerine bir tehlikeye karşı çözüme yönelik diğer hangi sorunları çözmeniz gerektiğini ve özgün uyarıları tetikleyen e-postaların (örneğin, kullanıcı gönderme kısıtlamalarını tetikleyen kimlik avı/istenmeyen posta) görünürlük sağlar

Benzerlik ve kötü amaçlı varlık sorguları aracılığıyla e-posta kümeleme çözümlemesi, saldırıdan yalnızca bir e-postanın tanımlenip temizlense bile e-posta sorunlarının tamamen tanımlenip temizlenmesini sağlar. Daha ayrıntılı çözümleme yapmak ve gerekirse sorguları değiştirmek için, e-posta kümesi ayrıntıları yan panel görünümlerinden bağlantıları kullanarak sorguları Gezgin'de veya Gelişmiş Atlar'da açabilirsiniz. Bu özellik, e-posta kümesi sorgularının çok dar veya çok geniş (ilgisiz e-postalar da içinde) olduğunu bulursanız elle iyileştirme ve düzeltmeyi sağlar.

Burada, soruşturmalarda e-posta analizine ilişkin ek geliştirmeler ve bilgiler yer almaktadır.

## <a name="air-investigation-ignores-advanced-delivery-items-secops-mailbox-and-phishedu-messages"></a>AIR soruşturması gelişmiş teslim öğelerini (SecOps posta kutusu ve PhishEDU iletileri) yoksayıyor

E-posta kümeleme çözümlemesi sırasında, tüm kümeleme sorguları Gelişmiş Teslim ilkesinde Güvenlik İşlemleri posta kutuları olarak ayarlanmış güvenlik posta kutularını yoksayar. Benzer şekilde, e-posta kümeleme sorguları, Gelişmiş Teslim ilkesinde yapılandırılmış kimlik avı benzetimini (eğitim) iletilerini yoksayar. Kümeleme özniteliklerini daha basit ve kolay okunur tutmak için sorguda SecOps veya PhishEdu dışlama değerleri gösterilmez. Bu dışlama, tehdit zekası ve işlem posta kutularının (SecOps posta kutuları) ve kimlik avı benzetimleri (PhishEdu) tehdit çözümlemesi sırasında yok sayılarak, herhangi bir düzeltme sırasında kaldırılmasını sağlar.

>[!Note]
>E-posta kümesi, e-posta kümesi ayrıntılarından Explorer'da görüntülemek için bir e-posta kümesi a açılışında, Explorer'da PhishEdu ve SecOps posta kutusu filtreleri uygulanır, ancak gösterilmez. Gezgin filtrelerini, tarihlerini değiştirir veya sorguyu sayfa içinde yenilersiniz. Bu durumda PhishEdu/SecOps filtre dışlamaları kaldırılır ve bunlara eşan e-postalar yeniden gösterilir. Tarayıcı yenileme işlevini kullanarak Explorer sayfasını yenilersiniz, özgün sorgu filtreleri (PhishEdu/SecOps filtreleri de içinde olmak üzere) yeniden yüklenir; ancak daha sonra yaptığınız tüm değişiklikler silinir.
>

## <a name="air-updates-pending-email-action-status"></a>AIR güncelleştirmeleri bekleyen e-posta eylem durumu

Araştırma e-postası çözümlemesi, soruşturma kanıtı ve eylemlerini oluşturmak için araştırmanın zamanında e-posta tehditlerini ve konumlarını hesaplar. Araştırmanın dışındaki eylemler soruşturmaya katılan e-postaları etkileyenin, bu veriler eski ve eskimiş olabilir. Örneğin, güvenlik işlemlerinin el ile avı ve düzeltmesi, soruşturma kapsamındaki e-postaları temizl olabilir. Benzer biçimde, paralel araştırmalarda onaylanan silme eylemleri veya Sıfır saatlik otomatik temizleme (ZAP) otomatik karantina eylemleri e-postaları kaldırılmış olabilir. Buna ek olarak, e-posta teslimi sonrasında gecikmiş tehdit algılamaları, incelemenin e-posta sorgularına/kümelerine dahil edilen tehdit sayısını da değiştirebilir.

Soruşturma eylemlerinin güncel olmasını sağlamak için, bekleyen eylemleri olan tüm soruşturmalar e-posta konumlarını ve tehditlerini güncelleştirmek üzere düzenli aralıklarla e-posta çözümleme sorgularını yeniden çalıştıracak.

- E-posta kümesi verileri değiştiklarında, tehdit ve en son teslim konumu sayılarını güncelleştirecek.
- Artık posta kutusunda bekleyen eylemlerin olduğu e-postalar veya e-posta kümesi yoksa, bekleyen eylem iptal edilir ve kötü amaçlı e-posta/küme düzeltme olarak kabul edilir.
- Araştırmanın tüm tehditleri yukarıda belirtildiği gibi düzeltilir veya iptal edilirse, araştırma düzeltilen bir durumla ve özgün uyarının çözümlenmiş durumuna geçilir.

## <a name="the-display-of-incident-evidence-for-email-and-email-clusters"></a>E-posta ve e-posta kümeleri için olay kanıtının görüntüsü

Bir olayın Kanıt ve Yanıt **sekmesinde e-posta** tabanlı kanıt şimdi aşağıdaki bilgileri görüntüler.

:::image type="content" source="../../media/email-analysis-investigations/email-analysis-evidence-example.png" alt-text="Kanıt ve Yanıt'ta e-posta çözümleme bilgileri örneği." lightbox="../../media/email-analysis-investigations/email-analysis-evidence-example.png":::

Şekilde numaralı açıklamalı açıklamalardan:

1. İşlem Merkezi'nin yanı sıra düzeltme eylemleri de **gerçekleştirabilirsiniz**.
2. Kötü amaçlı bir kararla (Şüpheli değil) e-posta **kümeleri** için düzeltme işlemi **atabilirsiniz**.
3. İstenmeyen e-posta kararının kimlik avı, yüksek güven güveni ve normal kimlik avına ayrılır.

   Kötü amaçlı bir karar için tehdit kategorileri kötü amaçlı yazılım, yüksek güvenlikli kimlik avı, kötü amaçlı URL ve kötü amaçlı dosyadır.

   Şüpheli karar için tehdit kategorileri istenmeyen posta ve normal kimlik avıdır.

4. E-posta sayısına göre en son teslim konumu temel alınarak, posta kutularında ve şirket içinde değil, posta kutularında yer alan e-posta için sayaçlar bulunmaktadır.
5. Sorgunun, en son veriler için güncelleştirilebilir olan tarih ve saati içerir.

Bir olayın Varlıklar sekmesindeki e-posta  veya e-posta kümeleri **için,** Engellenmiş iletisi, posta kutusunda bu öğe için kötü amaçlı e-posta (posta veya küme) olmadığını gösterir. İşte bir örnek.

:::image type="content" source="../../media/email-analysis-investigations/email-analysis-evidence-example-prevented.png" alt-text="Engelli e-posta örneği." lightbox="../../media/email-analysis-investigations/email-analysis-evidence-example-prevented.png":::

Bu örnekte, e-posta kötü amaçlıdır ancak posta kutusunda değildir.

## <a name="next-steps"></a>Sonraki adımlar

- [Bekleyen veya tamamlanmış düzeltme eylemlerini görüntüleme](air-review-approve-pending-completed-actions.md)
