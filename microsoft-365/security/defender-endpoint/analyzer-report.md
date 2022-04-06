---
title: İstemci çözümleyiciSI HTML raporunu anlama
description: Yeni İstemci Çözümleyicisi HTML Uç Nokta için Microsoft Defender çözümlemeyi öğrenin
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
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 1f843c62d44ed7c25f07568cc0ee92709fb080a7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468909"
---
# <a name="understand-the-client-analyzer-html-report"></a>İstemci çözümleyiciSI HTML raporunu anlama

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

İstemci çözümleyicisi, html biçiminde bir rapor üretir. Olası algılayıcı sorunlarını tespit etmek ve bu sorunları giderebilirsiniz.

Raporu anlamak için aşağıdaki örneği kullanın.

 Son kullanma tarihi geçen Kuruluş Kimliği'ne ekli bir makinede çözümleyicinin örnek çıktısı ve gerekli kullanıcı URL'lerinden Uç Nokta için Microsoft Defender başarısız:

:::image type="content" source="images/147cbcf0f7b6f0ff65d200bf3e4674cb.png" alt-text="MDE İstemci Çözümleyicisi Sonuçları sayfası" lightbox="images/147cbcf0f7b6f0ff65d200bf3e4674cb.png":::

- En üstte, başvuru için betik sürümü ve betik çalışma zamanı listelenir
- Cihaz **Bilgileri bölümünde** , çözümleyicinin çalıştır çalıştır olduğu cihazı benzersiz bir şekilde tanımlamak için temel işletim sistemi ve cihaz tanımlayıcıları gösterilir.
- Uç **Nokta Güvenlik Ayrıntıları**, algılayıcı Uç Nokta için Microsoft Defender de dahil olmak üzere konuyla ilgili Microsoft Defender Virüsten Koruma genel bilgiler sağlar. Önemli işlemler beklendiği gibi çevrimiçi yoksa renk kırmızıya değiştirir.
  
-   Uç **Nokta Güvenlik Ayrıntıları**, algılayıcı Uç Nokta için Microsoft Defender de dahil olmak üzere konuyla ilgili Microsoft Defender Virüsten Koruma genel bilgiler sağlar. Önemli işlemler beklendiği gibi çevrimiçi yoksa renk kırmızıya değiştirir.

    :::image type="content" source="images/85f56004dc6bd1679c3d2c063e36cb80.png" alt-text="Sonuçları Denetleme Özeti sayfası" lightbox="images/85f56004dc6bd1679c3d2c063e36cb80.png":::

-   Sonuçları **Denetleme Özeti'nin** altında, çözümleyici tarafından algılanan hata, uyarı veya bilgisel olaylar için birleştirilmiş bir sayınız olur.

-   Ayrıntılı **Sonuçlar'da**, sonuçların ve çözümleyicinin yaptığı gözlemlere dayalı rehberlikle birlikte bir liste (önem derecesine göre sıralanmış) gösterilir.

## <a name="open-a-support-ticket-to-microsoft-and-include-the-analyzer-results"></a>Microsoft'a bir destek bileti açın ve Çözümleyici sonuçlarını dahil

Destek bileti a [açılışında çözümleyici sonuç dosyalarını eklemek](contact-support.md#open-a-service-request) için Ekler bölümünü kullanmaya **ve dosyayı** eklemeye emin `MDEClientAnalyzerResult.zip` olun:

:::image type="content" source="images/508c189656c3deb3b239daf811e33741.png" alt-text="Ek istemi" lightbox="images/508c189656c3deb3b239daf811e33741.png":::

> [!NOTE]
> Dosya boyutu 25 MB'den büyükse, davanıza atanan destek mühendisi, çözümleme için büyük dosyaları karşıya yüklemek için özel bir güvenli çalışma alanı sağlar.
