---
title: Ekibiniz için saldırı simülasyonlarını çalıştırma
description: Eğitim için ekibiniz veya kuruluşunuz için hedef kullanıcılarınıza Saldırı Benzetimi yükü gönderme adımları. Sanal saldırılar, kuruluşunuzu gerçek bir saldırı etkilemeden önce savunmasız kullanıcıları, ilkeleri ve uygulamaları belirlemenize ve bulmanıza yardımcı olabilir.
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
ms.topic: article
ms.technology: mdo
ms.openlocfilehash: 96b1d512f89cafb782b348a0692fbf5c19902ebf
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842514"
---
# <a name="how-to-run-attack-simulations-for-your-team"></a>Ekibiniz için saldırı simülasyonlarını çalıştırma

Saldırı simülasyonu eğitimi, kuruluşunuzda gerçekçi ama zararsız siber saldırı senaryoları çalıştırmanızı sağlar. Sanal saldırılar, kuruluşunuzu gerçek bir saldırı etkilemeden önce savunmasız kullanıcıları, ilkeleri ve uygulamaları belirlemenize ve bulmanıza yardımcı olabilir, riski azaltmak ve son kullanıcıları tehditler hakkında daha iyi eğitmek için oluşturulmuş veya özel eğitimden yararlanabilir.

## <a name="what-youll-need"></a>İhtiyacınız olan şey

- Office 365 için Microsoft Defender Plan 2 (E5'in bir parçası olarak dahil)
- Yeterli izinler (Güvenlik Yöneticisi rolü)
- Aşağıdaki adımları gerçekleştirmek için 5-10 dakika.

## <a name="send-a-payload-to-target-users"></a>Hedef kullanıcılara yük gönderme

1. Aboneliğinizde [Saldırı Benzetimi Eğitimi'ne](https://security.microsoft.com/attacksimulator ) gidin.
1. Üst gezinti çubuğundan **Simülasyonlar'ı** seçin.
1. **Benzetimi başlat'ı** seçin.
1. Açılır listeden kullanmak istediğiniz tekniği seçin ve **İleri'ye** basın.
1. Simülasyonu ilgili /akılda kalıcı bir şeyle adlandırın ve **İleri'ye** basın.
1. Sihirbazdan ilgili bir yük seçin, ayrıntıları gözden geçirin ve uygunsa özelleştirin. Seçimden memnun olduğunuzda **İleri'ye** basın.
1. Yükle hedeflenen kişiyi seçin. Kuruluşun tamamını seçerken radyo düğmesini vurgulayın ve **İleri'ye** basın.
1. Aksi takdirde, **Kullanıcı Ekle'yi** seçin ve sihirbazla kullanıcıları arayın veya filtreleyin. Kullanıcı Ekle'yi ve ardından **İleri'yi** seçin.
1. **Eğitim içeriği tercihini seçin** bölümünde varsayılan *Microsoft eğitim deneyimini (Önerilen)* bırakın veya *özel URL'yi kullanmak istiyorsanız Özel URL'ye yeniden yönlendir'i* seçin. Herhangi bir eğitim atamak istemiyorsanız Eğitim *yok'a* tıklayın.
    - Microsoft'un *benim için eğitim ata'yı* seçerek eğitim kursları atamasına izin verebilir veya Eğitim *kursları ve modülleri kendim seç ile belirli modülleri seçebilirsiniz*
    - Açılan menüden bir Son Tarih (30, 15 veya 7 gün) seçin.
    - Devam etmek için **İleri'ye** tıklayın.
1. Uygunsa bir kullanıcı kimlik avına ulandığında görüntülenen giriş sayfasını özelleştirin veya Microsoft Varsayılan'ı başka bir şekilde bırakın.
    1. **Yük göstergeleri'nin** altında, e-postaya yük göstergeleri eklemek için kutuyu işaretleyin. Yük eklemek, kullanıcıların kimlik avı e-postasını tanımlamayı öğrenmesine yardımcı olur. İletiyi görüntülemek için *Önizleme panelini aç'ı* seçin.
    1. Devam etmek için **İleri'ye** tıklayın.
1. Son kullanıcı bildirimlerini isteyip istemiyorsanız teslim tercihlerini seçin ve gerektiğinde özelleştirin.
    1. Varsayılan dili seç açılan menüsünde bildirim için *varsayılan dili* de seçebileceğinize  dikkat edin.
1. Simülasyonu başlatmayı ve ne kadar süreyle geçerli olacağını seçin. Ayrıca *bölgeye duyarlı saat dilimi teslimi* de etkinleştirebilirsiniz. Bu seçenek, çalışanlarınıza *bölgelerine göre çalışma saatleri* içinde sanal saldırı iletileri teslim eder. **İleri**'yi seçin.
1. Hazırsanız bir test gönderin. Seçeneklerin özetini gözden geçirin. **Gönder'e** tıklayın.

### <a name="further-reading"></a>Daha fazla okuma

Saldırı Benzetimi'nin nasıl çalıştığını öğrenmek için bkz. [Saldırı simülasyonu eğitimi ile kimlik avı saldırısı simülasyonu - Office 365 | Microsoft Docs](../../office-365-security/attack-simulation-training.md)
