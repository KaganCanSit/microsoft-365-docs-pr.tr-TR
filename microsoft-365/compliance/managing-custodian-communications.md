---
title: eBulma'da iletişimlerle çalışma (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: eKeşif (Premium), yasal araştırmalarda koruyuculara bildirimde bulunarak yasal tutma bildirimi iş akışını yönetmeyi kolaylaştırır.
ms.openlocfilehash: 9ee915cc9955b343d76ae1314c27a86421d37332
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944667"
---
# <a name="work-with-communications-in-ediscovery-premium"></a>eBulma'da iletişimlerle çalışma (Premium)

Microsoft Purview eKeşif (Premium), yasal departmanların yasal tutma bildirimlerini izleme ve dağıtma süreçlerini basitleştirmesine olanak tanır. Koruyucu iletişim aracı, yasal departmanların ilk bildirimlerden anımsatıcılara ve yükseltmelere kadar tüm yasal saklama sürecini tek bir konumda yönetmesine ve otomatikleştirmesine olanak tanır.

## <a name="what-is-a-legal-hold-notification"></a>Yasal saklama bildirimi nedir?

Yasal tutma ( *dava tutma* olarak da bilinir) bildirimi, bir kuruluşun hukuk departmanından çalışanlara, bağlı personele veya yasal soruşturmayla ilgili olabilecek verilerin koruyucularına gönderilen bir bildirimdir. Bu bildirimler, koruyuculara elektronik olarak depolanan bilgileri ve etkin veya yaklaşan bir yasal konuyla ilgili olabilecek tüm içerikleri korumalarını emredmektedir. Hukuk ekipleri, her koruyucunun verilen yönergelere uyduğunu, okuduğunu, anladığını ve uymayı kabul ettiğini bilmelidir.

## <a name="the-legal-hold-notification-process"></a>Yasal saklama bildirim süreci

Bir kuruluş, yaklaşan bir dava veya mevzuat araştırması hakkında bilgi edindiğinde ilgili bilgileri koruma görevine sahiptir. Bir soruşturmanın koruma gereksinimlerine uymak için kuruluş, ilgili bilgileri korumak için potansiyel koruyucuları derhal bilgilendirmelidir.

eKeşif (Premium) ile hukuk ekipleri yasal tutma bildirimi iş akışını oluşturabilir ve özelleştirebilir. Koruyucu iletişim aracı, yasal ekiplerin aşağıdaki bildirimleri ve iş akışlarını yapılandırmasına olanak tanır:

1. **Verme bildirimi:** Yasal tutma bildirimi, hukuk departmanından konuyla ilgili bilgilere sahip olabilecek koruyuculara yapılan bir bildirimle verilir (veya başlatılır). Bu bildirim, koruyuculara bulma için gerekli olabilecek tüm bilgileri korumalarını emredmektedir.

2. **Yeniden Verme bildirimi:** Bir olay sırasında, koruyucuların daha önce istenenden daha fazla içerik (veya daha az içerik) koruması gerekebilir. Bu senaryo için mevcut ayrı tutma bildirimini güncelleştirebilir ve koruyuculara yeniden sağlayabilirsiniz.

3. **Sürüm bildirimi:** Bir mesele çözüldükten ve koruyucu artık bir koruma gereksinimine tabi olmadığında, koruyucu davadan serbest bırakılabilir. Buna ek olarak, koruyucuya içeriği korumak için artık gerekli olmadığını bildirebilir ve normal çalışma etkinliklerini ve verilerini nasıl sürdüreceklerine ilişkin yönergeler sağlayabilirsiniz.

4. **Anımsatıcılar ve yükseltmeler:** Bazı durumlarda, yasal bulma gereksinimlerini karşılamak için yalnızca bir bildirim vermek yeterli değildir. Her bildirimle, yasal ekipler yanıt vermeyen koruyucularla otomatik olarak takip etmek için bir anımsatıcı ve yükseltme iş akışları kümesi zamanlayabilir.

   - **Hatırlatmalar:** Yasal bir saklama bildirimi verildikten veya bir dizi koruyucuya yeniden verildikten sonra, kuruluş yanıt vermeyen koruyucuları uyarmak için anımsatıcılar ayarlayabilir.

   - **Escalations:** Bazı durumlarda, bir koruyucu belirli bir süre boyunca bir dizi anımsatıcıdan sonra bile yanıt vermiyorsa, hukuk ekibi yanıt vermeyen koruyucuları ve yöneticilerini bilgilendirmek için bir yükseltme iş akışı ayarlayabilir.

Koruyucu iletişim sürecini yönetme hakkında daha fazla bilgi için aşağıdakilere bakın: 

- [Yasal tutma bildirimi oluşturma](create-hold-notification.md)

- [İletişim düzenleyicisini kullanma](using-communications-editor.md)

- [Bekletme bildirimlerini yönetme](manage-hold-notification.md)

- [Bekletme bildirimini onaylama](acknowledge-hold-notification.md)