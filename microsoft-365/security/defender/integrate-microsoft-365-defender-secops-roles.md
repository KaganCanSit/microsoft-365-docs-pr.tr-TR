---
title: Adım 4. Farklı Microsoft 365 Defender, sorumluluklar ve gözetim tanımlayın
description: Görevlerinizi güvenlik işlemleriyle tümleştirinken rolleri, sorumlulukları ve gözetimi Microsoft 365 Defender tanımlamanın temelleri.
keywords: olaylar, uyarılar, araştırma, korelasyon, saldırı, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, Microsoft 365, olay yanıtı, siber saldırı, secops, güvenlik işlemleri, soc
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
ms.openlocfilehash: 7562eca50b905bf70f17844cf8fe3079fbf3fc14
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314287"
---
# <a name="step-4-define-microsoft-365-defender-roles-responsibilities-and-oversight"></a>Adım 4. Farklı Microsoft 365 Defender, sorumluluklar ve gözetim tanımlayın

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Herhangi bir işlem rolleri tanımlanmadan önce Microsoft 365 Defender lisansların, yapılandırmaların ve yönetimin sahipliğini ve sorumluluklarını belirlemesi gerekir. Normalde, Microsoft 365 ve Enterprise Security + Mobility (EMS) hizmetlerinin (Microsoft 365 Defender dahil olabilir) lisanslarının, abonelik maliyetlerinin ve yönetiminin sahipliği Güvenlik İşlemleri Merkezi (SOC) ekiplerinin dışında olur. SOC ekiplerinin, her iki ekipte düzgün gözetim sağlamak için bu Microsoft 365 Defender. 

Birçok modern SOC, ekip üyelerini kendi beceri kümeleri ve işlevlerine göre kategorilere atar. Örneğin:

- Tehdit ve analiz işlevlerinin yaşam döngüsü yönetimiyle ilgili görevlere atanmış bir tehdit zekası ekibi.
- Günlükleri, uyarıları, olayları ve izleme işlevlerini korumakla sorumlu SOC analistlerinden oluşan bir izleme ekibi.
- Bir mühendislik & ve güvenlik cihazlarını en iyi duruma getirmek için atanmış bir mühendislik ekibi.

SOC ekip rolleri ve sorumluluklar bu Microsoft 365 Defender doğal bir şekilde tümleştirildi.

Aşağıdaki tabloda, her SOC ekibinin rolleri ve sorumlulukları ve rollerinin ekiple tümleştirileri Microsoft 365 Defender.

| SOC ekibi | Roller ve sorumluluklar | Microsoft 365 Defender görevleri gerçekleştirme  |
|:-------|:-----|:-------|
| SOC Oversight | <ul><li>SOC idaresi yapar</li><li>Günlük, haftalık, aylık süreçler sağlar</li><li>Eğitim ve farkındalık sağlar</li><li>Personel olarak işe alma, eşler arası gruplara ve toplantılara katılma</li><li>Mavi, Kırmızı, Mor takım alıştırmaları yapıyor</ul>  | <ul><li>Microsoft 365 Defender portalı erişim denetimleri</li><li>Özellik/URL ve lisans güncelleştirme kaydını bulundurr</li><li>IT, yasal, uyumluluk ve gizlilik paydaşları ile iletişimi sürdürür</li><li>Yeni toplantı veya toplantı düzenleme girişimleri için Microsoft 365 denetim Microsoft Azure katılma</ul> |
| Threat Intelligence & Analytics  | <ul><li>Tehdit intel akış yönetimi</li><li>Virüs ve kötü amaçlı yazılım attribution</li><li>Tehdit modelleme & olay sınıflandırmaları</li><li>Insider tehdit öznitelik geliştirme </li><li>Threat Intel Integration with Risk Management program</li><li>İk, yasal, IT ve güvenlik ekipleri genelinde veri bilimi, BI ve analizlerle veri içgörülerini tümleştirin<ul> | <ul><li>Kimlik tehdit modellemesi için Microsoft Defender'ın bakımı</li><li>Tehdit modelleme için Microsoft Defender Office 365 koruma altındadır</li><li>Uç nokta tehdit modellemesi için Microsoft Defender'ın bakımı</ul> |
| İzleme | <ul><li>Katman 1, 2, 3 analistler</li><li>Günlük kaynağı bakımı ve mühendislik</li><li>Veri kaynağı alımı </li><li>SIEM ayrıştırma, uyarı, korelasyon, iyileştirme</li><li>Etkinlik ve uyarı oluşturma</li><li>Olay ve uyarı çözümlemesi</li><li>Olay ve uyarı bildirimi</li><li>Bilet sistemi bakımı</ul> | Kullanım alanları: <ul><li>Güvenlik & Uyumluluk Merkezi</li><li>Microsoft 365 Defender portalı</ul> |
| Mühendislik & SecOps | <ul><li>Uygulamalar, sistemler ve uç noktalar için Güvenlik Açığı Yönetimi</li><li>XDR/SOAR otomasyonu</li><li>Uyumluluk testi</li><li>Kimlik avı ve DLP mühendislik</li><li>Mühendislik</li><li>Koordinatlar değişiklik denetimi</li><li>Koordinatlar çalışma kitabı güncelleştirmeleri</li><li>Deneme testi<ul> | <ul><li>Bulut Uygulamaları için Microsoft Defender</li><li>Uç Nokta için Defender</li><li>Kimlik için Defender</ul> |
| Bilgisayar Güvenliği Olay Yanıt Ekibi (CSIRT) | <ul><li>Siber olayları araştırıyor ve yanıtlaıyor</li><li>Adli incelemeler yapar</li><li>**GENELLIKLE SOC'dan yalıtılmış olabilir**</ul> | Olay yanıtı Microsoft 365 Defender kitaplarını işbirliği yapma ve koruma |
||||


## <a name="next-step"></a>Sonraki adım

[5. Adım. Kullanım durumlarını geliştirme ve sınama](integrate-microsoft-365-defender-secops-use-cases.md)
