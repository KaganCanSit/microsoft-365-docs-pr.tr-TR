---
title: Microsoft tarafından analiz için dosya gönderme
description: Kötü amaçlı yazılım analizi için dosyaları Microsoft'a göndermeyi, gönderimlerinizi izlemeyi ve uyuşmazlık algılamalarını öğrenin.
ms.reviewer: ''
keywords: güvenlik, örnek gönderim yardımı, kötü amaçlı yazılım dosyası, virüs dosyası, truva atı dosyası, gönder, Microsoft'a gönder, örnek gönder, virüs, truva atı, solucan, algılanmadı, algılanmadı, e-posta microsoft, e-posta kötü amaçlı yazılım, Bu kötü amaçlı yazılım, ben bir virüs olduğunu düşünüyorum, nerede virüs gönderebilirim, bu bir virüs, MSE, algılamaz, imza yok, algılama yok, şüpheli dosya,  MMPC, Microsoft Kötü Amaçlı Yazılımdan Koruma Merkezi, araştırmacılar, analist, WDSI, güvenlik zekası
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: df2ab2b2019bb76af49f00d2751cdc76848705d1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663610"
---
# <a name="submit-files-for-analysis"></a>Dosyaları analiz için gönderin

Kötü amaçlı yazılım olabileceği veya yanlış algılandığından şüphelendiğiniz bir dosyanız varsa, dosyayı analiz için bize gönderebilirsiniz. Bu sayfada analiz için dosya göndermeyle ilgili bazı yaygın soruların yanıtları bulunur.

## <a name="how-do-i-send-a-malware-file-to-microsoft"></a>Microsoft'a kötü amaçlı yazılım dosyası Nasıl yaparım? gönderebilirsiniz?

Kötü amaçlı yazılım olabileceğini düşündüğünüz dosyaları veya hatalı algılanmış dosyaları [bize örnek gönderim portalı](https://www.microsoft.com/wdsi/filesubmission) üzerinden gönderebilirsiniz.

Birçok kaynaktan çok sayıda örnek alırız. Analizimiz, dosya algılama sayısı ve gönderim türüne göre önceliklendirilir. Kullandığınız ürün ve dosyayı bulduğunuzda ne yaptığınız hakkında ayrıntılı bilgi vererek hızlı bir analizi tamamlamamıza yardımcı olabilirsiniz.

Oturum açtığınızda gönderimlerinizi izleyebilirsiniz.

## <a name="can-i-send-a-sample-by-email"></a>E-postayla örnek gönderebilir miyim?

Hayır, yalnızca [örnek gönderim portalımız aracılığıyla gönderimleri](https://www.microsoft.com/wdsi/filesubmission) kabul ederiz.

## <a name="can-i-submit-a-sample-without-signing-in"></a>Oturum açmadan örnek gönderebilir miyim?

Hayır. Kurumsal müşteriyseniz gönderiminizin önceliklerini uygun şekilde belirlememiz için oturum açmanız gerekir. Şu anda bir virüs salgını veya güvenlikle ilgili bir olay yaşıyorsanız, belirlenen Microsoft destek uzmanınıza başvurmanız veya acil yardım için [Microsoft Desteği](https://support.microsoft.com/) gitmeniz gerekir.

## <a name="what-is-the-software-assurance-id-said"></a>Yazılım Güvencesi Kimliği (SAID) nedir?

[Yazılım Güvencesi Kimliği (SAID),](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx) kurumsal müşterilerin destek yetkilendirmelerini izlemesine yöneliktir. Gönderim portalı SAID bilgilerini kabul eder ve saklar ve geçerli SAID'leri olan müşterilerin daha yüksek öncelikli gönderimler yapmasına olanak tanır.

### <a name="how-do-i-dispute-the-detection-of-my-program"></a>Programımın algılanması konusunda Nasıl yaparım? anlaşmazlık var?

Söz konusu dosyayı yazılım geliştiricisi olarak [gönderin](https://www.microsoft.com/wdsi/filesubmission). Gönderiminizin son bir belirlemesi olana kadar bekleyin.

Gönderimin belirlenmesinden memnun değilseniz, Microsoft'a ulaşmak için gönderim sonuçlarıyla birlikte sağlanan geliştirici iletişim formunu kullanın. Gerekirse daha fazla araştırma yapmak için sağladığınız bilgileri kullanacağız.

Tüm yazılım satıcılarının ve geliştiricilerin [Microsoft'un kötü amaçlı yazılımları ve istenmeyen yazılımları nasıl tanımlamış olduğunu okumalarını](criteria.md) öneririz.

## <a name="how-do-i-track-or-view-past-sample-submissions"></a>Geçmiş örnek gönderimleri izlemek veya görüntülemek Nasıl yaparım??

Gönderimlerinizi [gönderim geçmişi sayfasından](https://www.microsoft.com/wdsi/submissionhistory) izleyebilirsiniz.

## <a name="what-does-the-submission-status-mean"></a>Gönderim durumu ne anlama geliyor?

Her gönderim aşağıdaki durum türlerinden birinde gösterilir:

* Gönderildi— dosya alındı

* Devam ediyor— bir analist dosyayı denetlemeye başladı

* Kapatıldı— bir analist tarafından kesin bir belirleme yapıldı

Bize gönderdiğiniz dosyaların durumunu [gönderim geçmişi sayfasında](https://www.microsoft.com/wdsi/submissionhistory) görebilirsiniz.

## <a name="how-does-microsoft-prioritize-submissions"></a>Microsoft gönderilerin önceliklerini nasıl belirlemeli?

Gönderimlerin işlenmesi için ayrılmış analist kaynağı gerekir. Düzenli olarak çok sayıda gönderim aldığımızdan, bunları bir önceliğe göre ele alırız. Aşağıdaki faktörler gönderimlere öncelik verme şeklimizi etkiler:

* Çok sayıda bilgisayarı etkileme olasılığı olan yaygın dosyalara öncelik verebilirsiniz.

* Kimliği doğrulanmış müşterilere, özellikle de geçerli [Yazılım Güvencesi Kimliklerine (SAID)](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx) sahip kurumsal müşterilere öncelik verilir.

* SAID sahipleri tarafından yüksek öncelikli olarak işaretlenmiş gönderimlere hemen dikkat edilir.

Gönderiniz, bir analist davanızı işlemeye başlamadan önce bile size en son belirlemeyi sağlamak için sistemlerimiz tarafından hemen taranır. Aynı dosyanın bir analist tarafından zaten işlenmiş olabileceğini unutmayın. Belirleme güncelleştirmelerini denetlemek için gönderim ayrıntıları sayfasında yeniden tara'yı seçin.
