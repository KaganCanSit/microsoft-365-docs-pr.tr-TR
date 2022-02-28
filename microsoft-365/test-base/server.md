---
title: Windows Server uygulama testi
description: Windows Server uygulama testiyle doğrulama
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 99868e53e98bded9139ecedea9c9d62e9d48fd2f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988758"
---
# <a name="windows-server-application-testing"></a>Windows Sunucusu Uygulama Testi

Temel Sınaması'Microsoft 365, artık sunucu çekirdek de içinde olmak üzere uygulamalarınızı Windows Server 2016 ve 2019'a göre doğrulayabilirsiniz!

Microsoft 365 Test Base'de Windows Server 2016 ve 2019 işletim sistemlerinin yayın öncesi güncelleştirmeleriyle karşıya yüklediğiniz uygulamaları doğrulamaya Microsoft 365 için aşağıdaki adımlara uymanız gerekir:

1. Self servis ekleme portalımızda oturum açın. Sol gezinti menüsünden, Test ayrıntılarının `Upload new package` `Package catalogue` altında öğesini seçin ve doldurun.

2. Işletim `Security updates` sistemi güncelleştirme türünü seçin:

   ![Güvenlik güncelleştirmelerini seçin.](Media/selecting-security-updates.png)

3. Test etmek için işletim sistemi sürümleri'nin altında, uygun işletim sistemi sürümlerini seçin. Windows Server OS sürümlerini veya sunucu ve istemci işletim sistemi sürümlerinin bir bileşimini seçin.

   ![Işletim sistemi sürümünü seçin.](Media/selecting-OS-versions.png)

4. Diğer gerekli bilgileri sağlama, sağlanan ayrıntıları gözden geçirme ve uygulama paketinizi karşıya yükleme. Karşıya yükledikten sonra, Paketi yönet menü sekmesinde paket durumunu görüntüleyebilirsiniz.

5. Windows Server 2016 ve 2019'a yönelik sürüm öncesi güvenlik güncelleştirmelerine karşı uygulamanın doğrulamasından elde edecekleri test sonuçlarını ve içgörüleri görüntülemek için, Test özeti sayfasına veya Güvenlik güncelleştirmesi sonuçları sayfasına gidin.

   ![Test sonuçlarını görüntüleme.](Media/access-test-results.png)

İşlevsel test ile çalışmaya başlamak için sonraki **makaleye ilerleyin**
> [!div class="nextstepaction"]
> [Sonraki adım](functional.md)
