---
title: Adım 4. Microsoft 365 Defender rollerini, sorumluluklarını ve gözetimlerini tanımlama
description: Microsoft 365 Defender güvenlik işlemlerinizle tümleştirirken rol, sorumluluk ve gözetim tanımlamanın temelleri.
keywords: olaylar, uyarılar, araştırma, bağıntı, saldırı, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, Microsoft, Microsoft 365, olay yanıtı, siber saldırı, secops, güvenlik işlemleri, soc
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
ms.openlocfilehash: 5410db413ece81a39453070985e6c744e8b684a6
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664072"
---
# <a name="step-4-define-microsoft-365-defender-roles-responsibilities-and-oversight"></a>Adım 4. Microsoft 365 Defender rollerini, sorumluluklarını ve gözetimlerini tanımlama

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- Microsoft 365 Defender

Kuruluşunuzun, işletimsel rollerin tanımlanabilmesi için önce Microsoft 365 Defender lisanslarının, yapılandırmalarının ve yönetiminin sahipliğini ve sorumluluklarını ilk görevler olarak belirlemesi gerekir. Genellikle lisansların sahipliği, abonelik maliyetleri ve Microsoft 365 ve Enterprise Security + Mobility (EMS) hizmetlerinin (Microsoft 365 Defender içerebilir) yönetimi, Güvenlik İşletim Merkezi (SOC) ekiplerinin dışında kalır. SOC ekipleri, Microsoft 365 Defender düzgün bir şekilde gözetim altında olmasını sağlamak için bu kişilerle birlikte çalışmalıdır. 

Birçok modern SOC, ekip üyelerini becerilerine ve işlevlerine göre kategorilere atar. Örneğin:

- Tehdit ve analiz işlevlerinin yaşam döngüsü yönetimiyle ilgili görevlere atanan bir tehdit bilgileri ekibi.
- Günlükleri, uyarıları, olayları ve izleme işlevlerini korumakla sorumlu SOC analistlerinden oluşan bir izleme ekibi.
- Güvenlik cihazlarını mühendislik ve iyileştirmeye atanan bir mühendislik & operasyon ekibi.

Microsoft 365 Defender için SOC ekip rolleri ve sorumlulukları bu ekiplere doğal olarak tümleştirilir.

Aşağıdaki tabloda her SOC ekibinin rolleri ve sorumlulukları ve rolleri Microsoft 365 Defender ile nasıl tümleştirildi?

| SOC ekibi | Roller ve sorumluluklar | görevleri Microsoft 365 Defender  |
|:-------|:-----|:-------|
| SOC Gözetim | <ul><li>SOC idaresi gerçekleştirir</li><li>Günlük, haftalık, aylık süreçler oluşturur</li><li>Eğitim ve farkındalık sağlar</li><li>Personeli işe alır, eş gruplarına ve toplantılara katılır</li><li>Mavi, Kırmızı, Mor takım alıştırmaları yürütür</ul>  | <ul><li>Portal erişim denetimlerini Microsoft 365 Defender</li><li>Özellik/URL ve lisans güncelleştirme kaydını korur</li><li>BT, yasal, uyumluluk ve gizlilik paydaşlarıyla iletişimi sürdürür</li><li>Yeni Microsoft 365 veya Microsoft Azure girişimleri için değişiklik denetimi toplantılarına katılır</ul> |
| Tehdit Analizi & Analizi  | <ul><li>Tehdit intel akışı yönetimi</li><li>Virüs ve kötü amaçlı yazılım atfı</li><li>Tehdit modelleme & tehdit olayı kategorileri</li><li>Insider tehdit Özniteliği geliştirme </li><li>Risk Yönetimi programıyla Tehdit Intel Tümleştirmesi</li><li>veri içgörülerini İk, hukuk, BT ve güvenlik ekiplerinde veri bilimi, BI ve analizle tümleştirir<ul> | <ul><li>Kimlik için Microsoft Defender tehdit modellemesini korur</li><li>Office 365 için Microsoft Defender tehdit modellemesini korur</li><li>Uç Nokta için Microsoft Defender tehdit modellemesini korur</ul> |
| Izleme | <ul><li>Katman 1, 2, 3 analistler</li><li>Günlük kaynağı bakımı ve mühendisliği</li><li>Veri kaynağı alımı </li><li>SIEM ayrıştırma, uyarı, bağıntı, iyileştirme</li><li>Olay ve uyarı oluşturma</li><li>Olay ve uyarı analizi</li><li>Olay ve uyarı raporlama</li><li>Bilet sistemi bakımı</ul> | Kullanır: <ul><li>Güvenlik & Uyumluluk Merkezi</li><li>Microsoft 365 Defender portalı</ul> |
| Mühendislik & SecOps | <ul><li>Uygulamalar, sistemler ve uç noktalar için güvenlik açığı yönetimi</li><li>XDR/SOAR otomasyonu</li><li>Uyumluluk testi</li><li>Kimlik avı ve DLP mühendisliği</li><li>Mühendislik</li><li>Koordinatlar değişiklik denetimi</li><li>Runbook güncelleştirmelerini koordine eder</li><li>Sızma testi<ul> | <ul><li>Bulut Uygulamaları için Microsoft Defender</li><li>Uç Nokta için Defender</li><li>Kimlik için Microsoft Defender</ul> |
| Bilgisayar Güvenlik Olayı Yanıt Ekibi (CSIRT) | <ul><li>Siber olayları araştırır ve yanıtlar</li><li>Adli tıp gerçekleştirir</li><li>**Genellikle SOC'den yalıtılmış olabilir**</ul> | olay yanıtı playbook'ları Microsoft 365 Defender işbirliği yapma ve bakımını yapma |
||||


## <a name="next-step"></a>Sonraki adım

[5. Adım. Kullanım örneklerini geliştirme ve test edin](integrate-microsoft-365-defender-secops-use-cases.md)
