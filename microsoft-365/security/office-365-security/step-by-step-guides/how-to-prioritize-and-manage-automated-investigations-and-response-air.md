---
title: Otomatik Araştırma ve Yanıt (AIR) önceliklerini belirleme ve yönetme.
description: AIR eylemlerini doğrudan İşlem Merkezi'nden analiz etme ve onaylama adımları. Uyarılar tetiklendiğinde, Otomatik Araştırma ve Yanıt (AIR), kuruluşunuzdaki bir tehdidin etkisinin kapsamını belirler ve önerilen düzeltme eylemleri sağlar.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: 234ce1ecb486c01b95c91aa51a0c5fd6b46e7a3c
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043533"
---
# <a name="prioritize-and-manage-automated-investigations-and-response-air"></a>Otomatik Araştırmalara ve Yanıtlara Öncelik Ver ve Yönet (AIR)

Otomatik Araştırma ve Yanıt (AIR), güvenlik operasyonları ekibinize zaman ve çaba kazandırır.

- Uyarılar tetiklendiğinde, otomatik araştırma kuruluşunuzdaki bir tehdidin etkisinin kapsamını belirler ve önerilen düzeltme eylemleri sağlar.
- Güvenlik ekipleri, el ile avlanma gereksinimini azaltmak için AIR otomasyonundan yararlanarak zaman kazandırabilir.
- Bu araştırmalarda Sıfır saatlik Otomatik Temizleme (ZAP) veya başka bir düzeltme tarafından temizlenmemiş e-postalar belirlenebilir.
- AIR araştırmaları ayrıca riskli olabilecek veya güvenliği aşılmış bir posta kutusuna işaret eden posta kutusu yapılandırmalarını da tanımlar.

Araştırma eylemlerine (ve araştırmalara) Microsoft Güvenlik portalındaki çeşitli noktalardan erişilebilir: *Olaylar*, *Uyarılar* veya *İşlem Merkezi* aracılığıyla. Hangi yöneticilerin kullandığı, bir yöneticinin takip ettiği iş akışını temel alır.

## <a name="why-use-the-action-center-workflow"></a>İşlem Merkezi iş akışını neden kullanmalısınız?

*E-posta & işbirliği* içeriğiyle ilgili otomatik araştırmalar Kötü *Amaçlı* veya *Şüpheli* gibi kararlara neden olduğundan, bazı düzeltme eylemleri oluşturulur. Önerilen düzeltme eylemleri otomatik olarak gerçekleştirilmiyor. Önerilen eylemleri *onaylamak* için SecOps'un her araştırmaya gitmeleri gerekir. *İşlem Merkezi'nde* bekleyen tüm eylemler hızlı onay için toplanır.

## <a name="what-youll-need"></a>İhtiyacınız olan şey

- Office 365 için Microsoft Defender Plan 2 veya üzeri (E5 ile birlikte)
- Yeterli izinler (Güvenlik okuyucusu, güvenlik işlemleri veya güvenlik yöneticisi, ayrıca [Arama ve temizleme](../permissions-microsoft-365-security-center.md) rolü)

## <a name="steps-to-analyze-and-approve-air-actions-directly-from-the-action-center"></a>AIR eylemlerini doğrudan İşlem Merkezi'nden analiz etme ve onaylama adımları

1. [Microsoft 365 Defender portalına](https://security.microsoft.com/action-center) gidin ve oturum açın.
2. İşlem merkezi yüklendiğinde, eylemleri sıralamak için sütunlara tıklayarak filtreleyin ve öncelik belirleyin ya da *varlık türü* (belirli bir URL için) veya eylem türü (geçici silme e-postası gibi) gibi bir filtre uygulamak için **Filtreler'e** basın.
3. Eylem tıklandığında açılır öğe açılır. Gözden geçirilecek ekranın sağ tarafında görünür.
4. Bir eylemin neden isten ettiği hakkında daha fazla bilgi için, araştırma veya bu eyleme bağlı uyarılar hakkında daha fazla bilgi edinmek için açılır listede **Araştırmayı aç sayfasını** seçin. (Yöneticiler, *Bekleyen Eylemler* sekmesini seçerek araştırma sayfasında görülen eylemleri de onaylayabilir.)
5. Aksi takdirde, önerilen eylemi doğrudan İşlem Merkezi'nden yapmak için **Onayla'yı** seçin.
6. Gereksiz olduğunu belirlerseniz eylemi reddedin.

## <a name="check-air-history"></a>AIR geçmişini denetleme

1. [Microsoft 365 Defender portalına](https://security.microsoft.com) gidin ve oturum açın.
2. Sol gezinti bölmesinde **Eylem & gönderimleri'ni** genişletin ve **ardından İşlem Merkezi'ne** tıklayın.
3. İşlem Merkezi yüklendiğinde **Geçmiş** sekmesine basın.
4. Verilen kararlar, eylem kaynağı ve uygunsa kararı veren yönetici de dahil olmak üzere AIR'in geçmişini görüntüleyin.

## <a name="more-information"></a>Daha Fazla Bilgi

[otomatik araştırmanın sonuçlarını Microsoft 365 - Office 365 | Microsoft Docs](../air-view-investigation-results.md)

[Araştırma sayfasından bekleyen eylemleri onaylama ve reddetme hakkında bilgi edinin](../air-review-approve-pending-completed-actions.md)
