---
title: Microsoft tarafından çözümleme için dosya gönderme
description: Kötü amaçlı yazılım çözümlemesi yapmak için dosyaları Microsoft'a nasıl gönderebilirsiniz, gönderilerinizi nasıl takip edin ve İhtilaf algılamaları hakkında bilgi edinebilirsiniz.
ms.reviewer: ''
keywords: güvenlik, örnek gönderim yardımı, kötü amaçlı yazılım dosyası, virüs dosyası, truva dosyası, gönder, Microsoft'a gönder, örnek, virüs, truva, solucan, algılanmadı, algılanmadı, microsoft'a e-posta, kötü amaçlı yazılım e-posta gönder, Bunun kötü amaçlı yazılım olduğunu düşünüyorum, bunun bir virüs olduğunu düşünüyorum, virüs bu virüs olabilir, bu bir virüs, MSE algılanmadı, imza yok, algılama yok, şüpheli dosya,  MMPC, Microsoft Kötü Amaçlı Yazılımdan Koruma Merkezi, araştırmacı, analist, WDSI, güvenlik zekası
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
ms.openlocfilehash: 78f1e00555d36880f24f05d213f42725f4ac0133
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63705702"
---
# <a name="submit-files-for-analysis"></a>Dosyaları analiz için gönderin

Kötü amaçlı yazılımdan şüpheleniyorsanız veya yanlış algılandığından şüpheleniyorsanız analiz için bize gönderebilirsiniz. Bu sayfada, çözümleme için dosya göndermeyle ilgili olarak sık sorulan bazı soruların yanıtları ve bulunmektedir.

## <a name="how-do-i-send-a-malware-file-to-microsoft"></a>Kötü amaçlı yazılım dosyasını Microsoft'a nasıl gönderirim?

Kötü amaçlı yazılım olabileceğini veya örnek gönderim portalı üzerinden yanlış algılanmış dosyalar olduğunu düşünüyor olabileceğiniz [dosyaları bize gönderebilirsiniz](https://www.microsoft.com/en-us/wdsi/filesubmission).

Birçok kaynaktan çok fazla sayıda örnek alanız. Çözümlememiz, dosya algılama sayısına ve gönderim türüne göre önceliklidir. Kullanmakta olduğunuz ürün ve dosyayı buken ne yapmak istediğiniz hakkında ayrıntılı bilgi sağlayarak hızlı bir çözümlemeyi tamamlamamıza yardımcı olabilirsiniz.

Oturum akten sonra gönderilerinizi izleyebilirsiniz.

## <a name="can-i-send-a-sample-by-email"></a>E-postayla örnek gönderebilir miyim?

Hayır, yalnızca örnek gönderim portalımız üzerinden [gönderileri kabul etmiş oluruz](https://www.microsoft.com/en-us/wdsi/filesubmission).

## <a name="can-i-submit-a-sample-without-signing-in"></a>Oturum açmadan bir örnek göndere miyim?

Hayır. Kurumsal müşteriysiniz, gönderinize uygun öncelikleri belirlememiz için oturum açmanız gerekir. Şu anda virüs salgını veya güvenlikle ilgili bir olay yaşıyorsanız, belirlenen Microsoft destek uzmanına başvurarak veya anında yardım için [Microsoft](https://support.microsoft.com/) Desteği'ne giterek.

## <a name="what-is-the-software-assurance-id-said"></a>Yazılım Güvencesi Kimliği (SAID) nedir?

Yazılım [Güvencesi Kimliği (SAID),](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx) kurumsal müşterilerin destek yetkilendirmelerini izlemesi için sağmaktadır. Gönderme portalı SAID bilgilerini kabul eder ve korur; müşterilerin geçerli SAID'leri olan müşterilerin yüksek öncelikli gönderimler yapmalarını sağlar.

### <a name="how-do-i-dispute-the-detection-of-my-program"></a>Programımı algılamaya nasıl itiraz  olurum?

[Söz konusu](https://www.microsoft.com/en-us/wdsi/filesubmission) dosyayı yazılım geliştiricisi olarak gönderin. Gönderimin son bir karara varıncaya kadar bekleyin.

Gönderiyi belirleme şeklimizi memnun değilseniz, Microsoft'a ulaşmak için gönderim sonuçlarıyla birlikte verilen geliştirici iletişim formunu kullanın. Sağlayılan bilgileri, gerekirse daha fazla araştırma yapmak için kullanacağız.

Tüm yazılım satıcılarını ve geliştiricilerin, Microsoft'un kötü amaçlı yazılım ve istenmeyen yazılımları [nasıl tanımları hakkında bilgi edinebilirsiniz](criteria.md).

## <a name="how-do-i-track-or-view-past-sample-submissions"></a>Geçmiş örnek gönderileri nasıl izleyebilir veya  bakabilirsiniz?

Gönderilerinizi, gönderi geçmişi [sayfasından izleyebilirsiniz](https://www.microsoft.com/en-us/wdsi/submissionhistory).

## <a name="what-does-the-submission-status-mean"></a>Gönderme durumu ne anlama geliyor?

Her gönderimin aşağıdaki durum türlerinden biri olduğu gösterilir:

* Gönderildi; dosya alındı

* Devam ediyor; bir analist dosyayı denetlemeye başladı

* Kapalı— bir analist tarafından son belirleme verildi

Bize gönderdiğiniz tüm dosyaların durumunu gönderim geçmişi [sayfasında görebilirsiniz](https://www.microsoft.com/en-us/wdsi/submissionhistory).

## <a name="how-does-microsoft-prioritize-submissions"></a>Microsoft gönderilere nasıl öncelik öncelikli olur?

Gönderileri işleme, adanmış bir analist kaynağı alır. Düzenli aralıklarla çok fazla sayıda gönderi almız olduğundan, bu gönderileri bir önceliğe göre işlemeyi tercih ediyorum. Aşağıdaki faktörler, gönderileri önceliklendirme nedenlerimizi etkiler:

* Çok fazla sayıda bilgisayarın etkilenmesi olası yaygın dosyalar öncelik sırasına sahiptir.

* Kimliği doğrulanmış müşterilere, özellikle de geçerli Yazılım [Güvencesi Kimliklerine (SAID) sahip kurumsal](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx) müşterilere öncelik verilir.

* SAID sahipleri tarafından yüksek öncelikli olarak işaretlenen gönderilere anında dikkat verilir.

Gönderiniz, bir analist vakanızı işlemeye başlamadan önce bile size en son belirlemeyi vermek için sistemlerimiz tarafından hemen taranır. Aynı dosyanın bir analist tarafından zaten işlenmiş olduğunu unutmayın. Belirleme güncelleştirmelerini kontrol etmek için, gönderme ayrıntıları sayfasında yeniden seçerek.
