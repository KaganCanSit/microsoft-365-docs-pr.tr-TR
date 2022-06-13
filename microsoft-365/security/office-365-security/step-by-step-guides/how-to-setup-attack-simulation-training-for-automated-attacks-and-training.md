---
title: Saldırı simülasyon eğitiminde otomatik saldırılar ve eğitim nasıl kurulur?
description: Saldırı Benzetimi eğitimini otomatikleştirme ve hedef kullanıcılara yük gönderme adımları. Bu kılavuzu izleyerek, belirli tekniklere ve yüklere sahip otomatik saldırı akışları oluşturmayı öğreneceksiniz.
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
ms.openlocfilehash: ccf4222878777789fb7f89b6382c858eaad9f0c2
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66042146"
---
# <a name="how-to-setup-automated-attacks-and-training-within-attack-simulation-training"></a>Saldırı simülasyon eğitiminde otomatik saldırılar ve eğitim nasıl kurulur?

Saldırı simülasyonu eğitimi, kimlik avı riskinizi değerlendirmek ve kullanıcılarınıza kimlik avı saldırılarından nasıl daha iyi kaçınabileceğinizi öğretmek için kuruluşunuzda zararsız saldırı simülasyonları çalıştırmanıza olanak tanır. Bu kılavuzu izleyerek, otomatik akışları belirli tekniklerle ve belirtilen koşullar karşılandığında çalıştırılan yüklerle yapılandıracak ve kuruluşunuzda simülasyonlar başlatacaksınız.

## <a name="what-youll-need"></a>İhtiyacınız olan şey

- Office 365 için Microsoft Defender Plan 2 (E5'in bir parçası olarak dahildir).
- Yeterli izinler (Güvenlik Yöneticisi rolü).
- Aşağıdaki adımları gerçekleştirmek için 5-10 dakika.

## <a name="send-a-payload-to-target-users"></a>Hedef kullanıcılara yük gönderme

1. [Saldırı benzetimi eğitimi'ne](https://security.microsoft.com/attacksimulator) gidin.
1. Üst gezinti çubuğundan **Simülasyon otomasyonları'nı** seçin.
1. **Otomasyon oluştur'a** basın.
1. Simülasyon otomasyonunu ilgili ve akılda kalıcı bir adla adlandırın. *İleri'yi seçin*.
1. Açılır menüden kullanmak istediğiniz teknikleri seçin. *İleri'yi seçin*.
1. Bu otomasyon için kullanmak istediğiniz en fazla 20 yükü el ile seçin veya alternatif olarak Rastgele Seç'i seçin. *İleri'yi seçin*.
1. OAuth'u Yük olarak seçtiyseniz, uygulamanın simülasyonda kullanıldığında sahip olmasını istediğiniz adı, logoyu ve kapsamı (izinler) girmeniz gerekir. *İleri'yi seçin*.
1. Kuruluşun tamamını seçerken radyo düğmesini vurguluyorsanız yükle hedeflenen kişiyi seçin. *İleri'yi seçin*.
1. Aksi takdirde, **Kullanıcı Ekle'yi** seçin ve sihirbazla kullanıcıları arayın veya filtreleyin, Kullanıcı Ekle'ye basın. *İleri'yi seçin*.
1. Uygunsa eğitimi özelleştirin, aksi takdirde Eğitimi benim için ata (önerilen) seçeneğini belirleyin. *İleri'yi seçin*.
1. Uygunsa bir kullanıcı kimlik avına katıldığında görüntülenen giriş sayfasını özelleştirin, aksi takdirde Microsoft Varsayılanı olarak bırakın. *İleri'yi seçin*.
1. Son kullanıcı bildirimlerini isteyip istemiyorsanız, teslim tercihlerini seçin ve uygun yerlerde özelleştirin. *İleri'yi seçin*.
1. Simülasyon zamanlaması için **Rastgele** veya **Sabit'i** seçebilirsiniz. Önerilen seçenek Rastgele'dir ve seçildikten sonra *İleri'yi* seçin.
1. Rastgele veya Sabit seçiminize bağlı olarak zamanlama ayrıntıları farklılık gösterebilir, ancak otomasyonun başlangıç ve bitiş tarihleri de dahil olmak üzere tercihleri seçebilirsiniz. *İleri'yi seçin*.
1. **Başlatma Ayrıntıları** için, benzersiz yükleri kullanma veya yinelenen suçluları hedefleme gibi istediğiniz son seçenekleri belirleyin ve ardından *İleri'yi* seçin.
1. **Gönderin** ve Simülasyon otomasyonu ayarlanır.

## <a name="learn-more"></a>Daha Fazla Bilgi Edinin

[Saldırı simülasyonu eğitimi için simülasyon otomasyonları - Office 365 | Microsoft Docs](../../office-365-security/attack-simulation-training-simulation-automations.md).
