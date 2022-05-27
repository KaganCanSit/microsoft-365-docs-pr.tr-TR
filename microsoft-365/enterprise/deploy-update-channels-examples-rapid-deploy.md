---
title: En son sürümler için geniş dağıtım örneği
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
ms.date: 07/21/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
ms.custom: ''
description: En son sürümü dağıtan bir kuruluşun Windows 10 ve Microsoft 365 uygulamaları için kanalları nasıl kullandığı.
ms.openlocfilehash: 43cd5deed9801de6ff044781bebf9d96cdac7c12
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754720"
---
# <a name="example-of-broad-deployment-for-the-latest-releases"></a>En son sürümler için geniş dağıtım örneği

Bu kanal yapılandırma örneği, bu iş önceliklerine uyacak şekilde en son sürümlerin hızlı dağıtımını kullanan bir kuruluşa yöneliktir:

- Microsoft uygulamaları ve hizmetleriyle iş sürekliliğini sağlayın.
- Microsoft'un en son özellikleri ve düzeltmeleriyle cihaz, hizmet ve veri güvenliğini en üst düzeye çıkarın.
- Microsoft'un en son özellikleriyle kullanıcı üretkenliğini en üst düzeye çıkarın.

Bu hedefler, hızlı üretim dağıtımı ile erken inceleme arasındaki dengeyi bulma BT görevine çevrilir ve geniş dağıtım öncesinde işlevsel olarak doğrulanması için kullanıcıların ve cihazların temsili bir alt kümesiyle çalışır.

Örnek kuruluşumuzun Avrupa, Afrika, Asya ve Amerika'daki binalarda 5.000 çalışanı vardır. Çalışanların %70'i Microsoft 365 E3, kuruluşun geri kalanı Microsoft 365 E5 kullanıyor.

>[!Note]
>Bu örnek, dağıtım aşamalarını ve gruplarını nasıl kullanabileceğinizi gösterecek şekilde tasarlanmıştır. Bu, birçok türde ve boyuttaki kuruluşlarda kullanılabilir.
>

Bu kuruluşun BT altyapısı: 

- Yüklü tabanın %60'ını oluşturan Windows, Microsoft 365 Uygulamaları ve Microsoft bulut hizmetleriyle büyük ölçüde homojendir. BT altyapısını basitleştirmek ve kolaylaştırmak için yoğun ve çok yıllık bir çabanın ardından birkaç eski sistem kaldı.
- Son derece deneyimli personel tarafından korunur ve microsoft'un yayınlarındaki liderliğini izleyerek kullanıcıları ve cihazlarını üretken ve güvenli tutmakla görevlendirilir.

## <a name="deployment-and-update-stages"></a>Dağıtım ve güncelleştirme aşamaları

En son sürümün hızlı dağıtım hedeflerine bağlı olarak, bu örnek kuruluş iki aşamalı bir dağıtım işlemi kullanır.

1. **Önizleme veya pilot dağıtım kullanın:** Erken benimseyenler, BT personeli, temsili yapılandırmaları olan kullanıcılar ve eğitim personeli ile doğrulama ve yineleme. 

   İlk benimseyenler, BT personeli, temsili yapılandırmaları olan kullanıcılar, yeni özellikler kuruluşun geri kalanına sunulmadan önce diğer uygulamalarla ve cihazlardaki işlevleri doğrulayabilir.

   Değişiklik yöneticileri, yaygın kullanıma sunulmadan önce yeni özelliklere erken göz atar ve mesajlaşma ve dağıtım planlayabilir.

   Eğitim personeli yeni dahili kurslar planlayabilir veya yaygın kullanıma sunulmadan önce yeni özellikler için mevcut kursları güncelleştirebilir.

2. **Üretim dağıtımı:** Kalan tüm kullanıcılara bölgeye, departmana veya diğer dağıtım yöntemine göre dağıtılır.

## <a name="deployment-configuration-for-windows-10"></a>Windows 10 için dağıtım yapılandırması

Genel hedef, bir grup temsilci kullanıcı ve cihazları tarafından Sürüm Önizleme Kanalı değişiklikleri doğrulandıktan sonra en son Semi-Annual Kanalı sürümünün geniş bir dağıtımını gerçekleştirmektir.

[Windows 10 dağıtım](/windows/deployment/) yöntemleri ve stratejileri hakkında daha fazla bilgi için bkz. dağıtım Windows 10.

| Sahne | Kanal | Dağıtım grubu |
|:-------|:-------|:-----|
| Pilot |  **Sürüm Önizleme Kanalı**  <ul><li>Amaç: Özellik güncelleştirmelerinin, temsili cihazlarda ve yapılandırmalarda (diller, üçüncü taraf uygulamalar) doğrulanması için BT personeline ve erken benimseyenlere dağıtımı. </li><li> Durum: Ticari müşteriler için tam uyumlu ve desteklenir ve destek sözleşmelerinize göre sayılmaz. </li></ul> | **Win10ReleasePreviewChannel** (örnek ad) <br><br> Üyeler şunlar içeren gruplardır: <ul><li> Departmanlar ve konumlar arasında meraklıları Windows </li><li> Doğrulama gerektiren yapılandırmalara sahip personel </li><li> BT yöneticileri ve BT dağıtım personeli </li><li> Değişiklik yöneticileri </li><li> İç eğitim personeli </li></ul> |
| Üretim |  **Altı Aylık Kanal**  <ul><li>Amaç: En son özellik güncelleştirmelerinin kuruluşun geri kalanına geniş kapsamlı dağıtımı. </li><li> Durum: Tam uyumlu ve desteklenir. </li></ul> | **Win10SemiAnnualChannel** (örnek ad) <br><br> Üyeler Win10ReleasePreviewChannel grubunda olmayan tüm kullanıcılardır. |
||||

Bu kuruluş, Windows Update veya Windows Server Update Services gibi Semi-Annual Kanal sürümlerini dağıttığı ve her iki kanal güncelleştirmesi için de aynı ilkeleri uyguladığı şekilde Yayın Önizleme Kanalı yükünü dağıtmanın en iyi uygulamasını kullanır.

Devam eden güncelleştirmeler işlemi:

1. Sürüm Önizleme Kanalı değişiklikleri Win10ReleasePreviewChannel (örnek ad) dağıtım grubuna dağıtılır.
2. Win10ReleasePreviewChannel grup üyeleri, Microsoft'a geri bildirim sağlayabilen ve ek doğrulama için sonraki Sürüm Önizleme Kanalı değişikliklerini bekleyebilen Release Preview Kanalı değişikliklerinin BT dağıtım personeline çalıştığını onaylar.
3. Semi-Annual Kanal özelliği değişiklikleri Win10SemiAnnualChannel dağıtım grubuna dağıtılır. 

>[!Note]
>önerilen kanal Semi-Annual Kanal olsa da, BT departmanınızın yönetim araçlarını kullanması ve en son Semi-Annual Kanal sürümünün ne zaman kuruluş içinde dağıtılacağına karar vermesi ve ardından dalgalar halinde kullanıma sunması gerekir.
>

## <a name="deployment-configuration-for-microsoft-365-apps"></a>Microsoft 365 Uygulamaları için dağıtım yapılandırması

Genel hedef, bir grup temsilci kullanıcı tarafından Geçerli Kanal (Önizleme) değişiklikleri doğrulandıktan sonra en son Güncel Kanal sürümünün geniş bir dağıtımını gerçekleştirmektir.

[Microsoft 365 Uygulamaları dağıtım](/deployoffice/plan-office-365-proplus) yöntemleri ve stratejileri hakkında daha fazla bilgi için bkz. Microsoft 365 Uygulamaları dağıtımı.

| Sahne | Kanal | Dağıtım grubu |
|:-------|:-------|:-----|
| Pilot |  **Geçerli Kanal (Önizleme)** <ul><li> Amaç: {bir grup temsilci kullanıcıya yeni Microsoft 365 Uygulamaları özelliklere göz atın} Özellik güncelleştirmelerinin Güncel Kanal (Önizleme) kullanıcıları ile test edilir ve üretime hazır oldukları anda dağıtımı. </li><li> Durum: Tam uyumlu ve desteklenir.</li><li> Ne sıklıkta: Her ay 2-3 kez güncelleştirir. </li></ul> | **AppsCurrentChannelPreview** (örnek ad) <br><br> Üyeler şunlar içeren gruplardır: <ul><li> Departmanlar ve konumlar arasında uygulama meraklılarını Office </li><li> Doğrulama gerektiren yapılandırmalara sahip personel </li><li> BT yöneticileri ve BT dağıtım personeli </li><li> Değişiklik yöneticileri </li><li> İç eğitim personeli </li></ul>|
| Üretim | **Geçerli Kanal** <ul><li> Amaç: En son özellik güncelleştirmelerinin kuruluşun geri kalanına geniş kapsamlı dağıtımı. </li><li> Durum: Tam uyumlu ve desteklenir. </li></ul> |  **AppsCurrentChannel** (örnek ad) <br><br> Üyeler, AppsCurrentChannelPreview grubunda olmayan tüm kullanıcılardır. |
|||

Devam eden güncelleştirmeler işlemi:

1. Geçerli Kanal (Önizleme) değişiklikleri AppsCurrentChannelPreview dağıtım grubuna dağıtılır.
2. AppsCurrentChannelPreview grup üyeleri, Microsoft'a geri bildirim sağlayabilen ve ek doğrulama için bir sonraki Geçerli Kanal (Önizleme) sürümünü bekleyebilen Geçerli Kanal (Önizleme) değişikliklerinin BT dağıtım personeline çalıştığını onaylar.
3. Geçerli Kanal değişiklikleri AppsCurrentChannel dağıtım grubuna dağıtılır. 

## <a name="visual-summary"></a>Görsel özet

Bu örnek kuruluş tarafından kullanılan ürünler, kanalları ve dağıtım grupları aşağıda verilmiştir. 

![En son sürümlerin geniş dağıtımı için dağıtım grupları.](../media/deploy-update-channels-examples-rapid-deploy/group-summary.png)

## <a name="see-also"></a>Ayrıca bkz.

[Dağıtım ve güncelleştirme kanalı örnek yapılandırmaları](deploy-update-channels-examples.md)

[Microsoft 365 Kurumsal’a genel bakış](microsoft-365-overview.md)

[Test laboratuvarı kılavuzları](m365-enterprise-test-lab-guides.md)