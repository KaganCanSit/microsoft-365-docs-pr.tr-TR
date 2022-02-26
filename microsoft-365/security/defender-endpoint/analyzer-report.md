---
title: İstemci çözümleyiciSI HTML raporunu anlama
description: Uç Nokta İstemci Çözümleyicisi HTML raporu için Microsoft Defender'ı çözümlemeyi öğrenin
keywords: istemci çözümleyici raporu, html raporu, istemci çözümleyicisi
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 6b345eb898b84de9f15772e11fdc92e1af5dde6a
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62974105"
---
# <a name="understand-the-client-analyzer-html-report"></a>İstemci çözümleyiciSI HTML raporunu anlama

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

İstemci çözümleyicisi, html biçiminde bir rapor üretir. Olası algılayıcı sorunlarını tespit etmek ve bu sorunları giderebilirsiniz.

Raporu anlamak için aşağıdaki örneği kullanın.

 Süresi dolmuş Kuruluş Kimliği'ne ekli bir makinede çözümleyicinin örnek çıktısı ve Uç Nokta URL'leri için gerekli Microsoft Defender'dan bire ulaşamamalıdır:

![İstemci çözümleyicisi sonucu görüntüsü.](images/147cbcf0f7b6f0ff65d200bf3e4674cb.png)

- En üstte, başvuru için betik sürümü ve betik çalışma zamanı listelenir
- Cihaz **Bilgileri bölümünde** , çözümleyicinin çalıştır çalıştır olduğu cihazı benzersiz bir şekilde tanımlamak için temel işletim sistemi ve cihaz tanımlayıcıları gösterilir.
- Uç **Nokta Güvenlik Ayrıntıları**, uç nokta ve algılayıcı işleme dahil uç nokta ile ilgili süreçler Microsoft Defender Virüsten Koruma Microsoft Defender hakkında genel bilgiler sağlar. Önemli işlemler beklendiği gibi çevrimiçi yoksa renk kırmızıya değiştirir.

  ![Ayrıntılı istemci çözümleyicisi sonucu görüntüsü](images/85f56004dc6bd1679c3d2c063e36cb80.png)

-   Uç **Nokta Güvenlik Ayrıntıları**, uç nokta ve algılayıcı işleme dahil uç nokta ile ilgili süreçler Microsoft Defender Virüsten Koruma Microsoft Defender hakkında genel bilgiler sağlar. Önemli işlemler beklendiği gibi çevrimiçi yoksa renk kırmızıya değiştirir.

  ![Ayrıntılı istemci çözümleyicisi ayrıntılı sonucu görüntüsü.](images/85f56004dc6bd1679c3d2c063e36cb80.png)

-   Sonuçları **Denetleme Özeti'nin** altında, çözümleyici tarafından algılanan hata, uyarı veya bilgilendirme olayları için bir toplam sayınız olur.

-   Ayrıntılı **Sonuçlar'da** , sonuçlarla birlikte (önem düzeyine göre sıralanmış) bir liste ve çözümleyici tarafından yapılan gözlemlere dayalı kılavuzluk gösterilir.

## <a name="open-a-support-ticket-to-microsoft-and-include-the-analyzer-results"></a>Microsoft'a bir destek bileti açın ve Çözümleyici sonuçlarını dahil

Destek bileti a [açılışında çözümleyici sonuç dosyalarını eklemek](contact-support.md#open-a-service-request) için Ekler bölümünü kullanmaya **ve dosyayı** eklemeye emin `MDEClientAnalyzerResult.zip` olun:

![Ek isteminin resmi.](images/508c189656c3deb3b239daf811e33741.png)

> [!NOTE]
> Dosya boyutu 25 MB'den büyükse, davanıza atanan destek mühendisi, çözümleme için büyük dosyaları karşıya yüklemek için özel bir güvenli çalışma alanı sağlar.
