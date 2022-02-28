---
title: En son sürümlere geniş dağıtım örneği
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
ms.date: 07/21/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
ms.custom: ''
description: En son sürümün dağıtımı yapılan bir kuruluş, uygulama ve uygulama Windows 10 kanalları Microsoft 365 kullanır.
ms.openlocfilehash: 6b0226a226742a89dc65ca0d32792db03c77e465
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985055"
---
# <a name="example-of-broad-deployment-for-the-latest-releases"></a>En son sürümlere geniş dağıtım örneği

Bu kanal yapılandırma örneği, şu işletme önceliklerine uygun olarak en son sürümler için hızlı dağıtım kullanan bir kuruluşa özeldir:

- Microsoft uygulamaları ve hizmetleri ile iş sürekliliğini sağlar.
- Microsoft'un en son özellikleri ve düzeltmeleriyle cihaz, hizmet ve veri güvenliğini en üst düzeye çıkarma.
- Microsoft'un en son özellikleriyle kullanıcı üretkenliğini en üst düzeye çıkarmak.

Bu hedefler, hızlı üretim dağıtımıyla, temsili bir kullanıcı ve cihaz alt kümesiyle genişletilen ve geniş dağıtımdan önce işlevsel olarak doğrulanması gereken hızlı dağıtım arasındaki dengeyi bulmayla ilgili IT görevine çevrilir.

Örnek kuruluşlarımızın Avrupa, Afrika, Asya ve Amerika'daki dünya genelinde binalarda 5.000 çalışan bulunuyor. Çalışanların %70'i Microsoft 365 E3 diğerleri çalışan tarafından varsayılan kullanım Microsoft 365 E5.

>[!Note]
>Bu örnek, birçok tür ve boyuttaki kuruluşlara uygun dağıtım aşamalarını ve grupları nasıl kullanabileceğiniz göstermek üzere tasarlanmıştır.
>

Bu kuruluşun IT altyapısı: 

- Yüklü tabanın %60'larından oluşan Windows, Microsoft 365 Uygulamaları ve Microsoft bulut hizmetleriyle büyük ölçüde eşgenizedir. BT altyapısını basitleştirmek ve kolaylaştırmak için yoğun, çok yıllık bir çalışmadan sonra birkaç eski sistem kalır.
- Deneyimli personel tarafından sürdürür ve sürümlerinde Microsoft'un liderlik ekibini takip eden kullanıcıların ve cihazlarının verimli ve güvenli bir şekilde korunmasıyla görev almaktadır.

## <a name="deployment-and-update-stages"></a>Dağıtım ve güncelleştirme aşamaları

Bu örnek kuruluş, en son sürümün hızlı dağıtım hedeflerine dayanarak iki adımlı bir dağıtım işlemi kullanır.

1. **Önizleme veya pilot dağıtım kullanma:** Erken benimseyenlerle, IT personeliyle, temsili yapılandırmaları olan kullanıcılarla ve eğitim personeliyle doğrulayın ve iterersiniz. 

   Yeni özellikler kuruluşun geri kalanına gitmeden önce, temsili yapılandırmaları olan kullanıcılar, erken benimseyen IT personeli diğer uygulamalarla ve cihazlarda işlevleri doğrular.

   Değişiklik yöneticilerinin yaygın olarak yaygın olarak yaygın hale gelmeden önce yeni özelliklere önceden göz atları vardır ve mesajlaşmayı ve yaygınlaşmayı plan olabilir.

   Eğitim personeli yaygın olarak yaygın hale gelmeden önce yeni iç kursları planlar veya yeni özellikler için mevcut kursları güncelleştirin.

2. **Üretim dağıtımı:** Kalan tüm kullanıcıları bölgeye, bölüme veya başka bir dağıtım yöntemine göre dağıtma.

## <a name="deployment-configuration-for-windows-10"></a>Dağıtım yapılandırması Windows 10

Genel olarak amaç, Sürüm Önizleme Kanalı değişikliklerinin doğrulanmasında en son Semi-Annual Kanalı sürümünün, temsili bir grup kullanıcı ve cihazlarının kapsamlı olarak dağıtımını yapmaktır.

Dağıtım [Windows 10 ve](/windows/deployment/) stratejiler hakkında daha fazla bilgi Windows 10 için bkz.

| Aşama | Kanal | Dağıtım grubu |
|:-------|:-------|:-----|
| Pilot |  **Sürüm Önizleme Kanalı**  <ul><li>Amaç: Temsili cihazlar ve yapılandırmalarda (diller, üçüncü taraf uygulamalar) doğrulama için, IT personeline ve erken benimsenenlere özellik güncelleştirmeleri dağıtımı. </li><li> Durum: Tamamen uyumlu ve ticari müşteriler için desteklenen ürün ve destek sözleşmelerinizi kabul desteklemez. </li></ul> | **Win10ReleasePreviewChannel** (örnek ad) <br><br> Üyeler şunları içeren gruplardır: <ul><li> Windows ve konumların en büyük tutkunları </li><li> Geçerlilik ihtiyacı olan yapılandırmaları olan personel </li><li> IT yöneticileri ve IT dağıtım personeli </li><li> Değişiklik yöneticileri </li><li> İç eğitim personeli </li></ul> |
| Üretim |  **Yarı Yıllık Kanal**  <ul><li>Amaç: En son özellik güncelleştirmelerinin kuruluşun geri kalanına geniş dağıtım. </li><li> Durum: Tam uyumlu ve desteklenen. </li></ul> | **Win10SnelAnnualChannel** (örnek ad) <br><br> Üyeler, Win10ReleasePreviewChannel grubunda yer almamış olan tüm kullanıcılardır. |
||||

Bu kuruluş, Windows Update veya Windows Server Update Services gibi Semi-Annual Kanalı yayınlarını dağıtmak ve her iki kanal güncelleştirmesinde de aynı ilkeleri uygulamak için olduğu gibi, Sürüm Önizleme Kanalı yüklemesini dağıtmak için en iyi uygulamayı kullanır.

Devam eden güncelleştirme işlemi:

1. Sürüm Önizleme Kanalı değişiklikleri Win10ReleasePreviewChannel (örnek ad) dağıtım grubuna dağıtılır.
2. Win10ReleasePreviewChannel grup üyeleri, Microsoft'a geri bildirim sağlayan ve ek doğrulama için bir sonraki Sürüm Önizleme Kanalı değişikliklerini bekley isteyen IT dağıtım personeli için Sürüm Önizleme Kanalı değişikliklerinin çalıştığını onaylar.
3. Semi-Annual özellik değişiklikleri Win10SnelAnnualChannel dağıtım grubuna dağıtılır. 

>[!Note]
>Semi-Annual Kanalı önerilen kanal olduğu halde, IT departmanınız kendi yönetim araçlarını kullanmalı ve kuruluş içinde en son Semi-Annual Kanalı sürümünü ne zaman dağıtacaklarını belirlemeli ve ardından dalga olarak dağıtsalar.
>

## <a name="deployment-configuration-for-microsoft-365-apps"></a>Dağıtım yapılandırması Microsoft 365 Uygulamaları

Genel olarak amaç, Güncel Kanal (Önizleme) değişikliklerini doğrulanın ardından, bir grup temsilci kullanıcı tarafından son Güncel Kanal sürümünün kapsamlı olarak dağıtımını yapmaktır.

Dağıtım [Microsoft 365 Uygulamaları ve](/deployoffice/plan-office-365-proplus) stratejiler hakkında daha fazla bilgi Microsoft 365 Uygulamaları için bkz. Dağıtımda daha fazla bilgi.

| Aşama | Kanal | Dağıtım grubu |
|:-------|:-------|:-----|
| Pilot |  **Güncel Kanal (Önizleme)** <ul><li> Amaç: {give a group of representative users a sneak peek of new Microsoft 365 Uygulamaları features} Current Channel (Preview) kullanıcıları ile test edilir ve üretime hazır olur olmaz özellik güncelleştirmeleri dağıtımı. </li><li> Durum: Tam uyumlu ve desteklenen.</li><li> Ne sıklıkta: Her ay 2-3 kez güncelleştirme. </li></ul> | **AppsCurrentChannelPreview** (örnek ad) <br><br> Üyeler şunları içeren gruplardır: <ul><li> Office ve yerlerdeki uygulama tutkunlarına yol verin </li><li> Geçerlilik ihtiyacı olan yapılandırmaları olan personel </li><li> IT yöneticileri ve IT dağıtım personeli </li><li> Değişiklik yöneticileri </li><li> İç eğitim personeli </li></ul>|
| Üretim | **Güncel Kanal** <ul><li> Amaç: En son özellik güncelleştirmelerinin kuruluşun geri kalanına geniş dağıtım. </li><li> Durum: Tam uyumlu ve desteklenen. </li></ul> |  **AppsCurrentChannel** (örnek ad) <br><br> Üyeler, AppsCurrentChannelPreview grubunda yer almamış olan tüm kullanıcılardır. |
|||

Devam eden güncelleştirme işlemi:

1. Geçerli Kanal (Önizleme) değişiklikleri AppsCurrentChannelPreview dağıtım grubuna dağıtılır.
2. AppsCurrentChannelPreview grup üyeleri, Microsoft'a geri bildirim sağlayan ve ek doğrulama için bir sonraki Güncel Kanal (Önizleme) sürümü için beklemeleri gereken GÜNCEL Kanal (Önizleme) personeli için Geçerli Kanal (Önizleme) değişikliklerinin çalıştığını onaylar.
3. Geçerli Kanal değişiklikleri AppsCurrentChannel dağıtım grubuna dağıtılır. 

## <a name="visual-summary"></a>Görsel özet

Bu örnek kuruluş tarafından kullanılan ürünler, kanalları ve dağıtım grupları burada ve şekildedir. 

![En son sürümlere geniş dağıtım için dağıtım grupları.](../media/deploy-update-channels-examples-rapid-deploy/group-summary.png)

## <a name="see-also"></a>Ayrıca bkz.

[Dağıtım ve güncelleştirme kanalı örnek yapılandırmaları](deploy-update-channels-examples.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Test laboratuvarı kılavuzları](m365-enterprise-test-lab-guides.md)