---
title: Otomasyon dosyası yüklemelerini yönetme
description: Çözümleme için gönderilen dosya uzantısını ve e-posta eki uzantılarını içerik çözümlemeyi etkinleştirme ve yapılandırma
keywords: otomasyon, dosya, karşıya yüklemeler, içerik, çözümleme, dosya, uzantı, e-posta, ek
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 21e7eb17759ff6127f3d91137023c058abe2715e
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998228"
---
# <a name="manage-automation-file-uploads"></a>Otomasyon dosyası yüklemelerini yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automationefileuploads-abovefoldlink)

Otomatik soruşturma'daki ek inceleme için bazı dosya ve e-posta eklerinin otomatik olarak buluta yüklen eklen yüklenişinin içerik çözümleme özelliğini etkinleştirin.

Dosya uzantısı adlarını ve e-posta eki uzantı adlarını belirterek dosyaları ve e-posta eklerini tanımlama.

Örneğin, dosya veya ek uzantısı adları olarak *exe* ve *bat* eklersiniz, otomatik soruşturma sırasında ek denetim için bu uzantılara sahip tüm dosyalar veya ekler otomatik olarak buluta gönderilir.

## <a name="add-file-extension-names-and-attachment-extension-names"></a>Dosya uzantısı adları ve ek uzantısı adları ekleyin.

1. Gezinti bölmesinde, Uç Nokta **Ayarlar** \> **Otomasyon yüklemelerini** \> **gerçekleştir'i** \> seçin.

2. İçerik çözümleme ayarını Açık ve Kapalı **arasında** **geçiş.**

3. Aşağıdaki uzantı adlarını ve ayrı uzantı adlarını virgülle yapılandırma:
   - **Dosya uzantısı adları** - E-posta ekleri dışında şüpheli dosyalar ek denetim için gönderilir

## <a name="related-topics"></a>İlgili konular

- [Otomasyon klasörü dışlamalarını yönetme](manage-automation-folder-exclusions.md)
