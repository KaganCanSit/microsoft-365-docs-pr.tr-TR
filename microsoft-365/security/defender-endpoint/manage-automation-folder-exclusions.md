---
title: Otomasyon klasörü dışlamalarını yönetme
description: Otomatik bir incelemenin dışında bırakılan dosyaları kontrol etmek için otomasyon klasörü dışlamaları ekleyin.
keywords: yönetme, otomasyon, dışlama, blok, temiz, kötü amaçlı
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
ms.openlocfilehash: 54c0f7f67b62216eae4264c8e7a55c0e34c82fb0
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998227"
---
# <a name="manage-automation-folder-exclusions"></a>Otomasyon klasörü dışlamalarını yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automationexclusionfolder-abovefoldlink)

Otomasyon klasörü dışlamaları, Otomatik araştırmanın atlay klasörünü belirtmenize olanak sağlar.

Atlanmalarını istediğiniz klasör hakkında aşağıdaki öznitelikleri kontrol edin:

- **Klasörler**: Atlanacak klasörü ve alt klasörlerini belirtebilirsiniz.

  > [!NOTE]
  > Şu anda, dizin altındaki dosyaları hariç tutmak için joker karakter kullanımı henüz desteklenemektedir.

- **Dosyaların uzantıları: Belirli** bir dizine hariç tutulacak uzantıları belirtebilirsiniz. Uzantılar, bir saldırganı, istismarı gizlemek için dışarıda bırakılan bir klasörü kullanmasını önlemenin bir yoludür. Uzantılar hangi dosyaların yoksaymak üzere olduğunu açıkça tanımlar.

- **Dosya adları**: Belirli bir dizinde dışlamak istediğiniz dosya adlarını belirtebilirsiniz. Adlar, bir saldırganin, istismarı gizlemek için dışlanmış bir klasör kullanmasını önlemenin bir yoludür. Adlar, hangi dosyaların yoksay önemli olduğunu açıkça tanımlar.

## <a name="add-an-automation-folder-exclusion"></a>Otomasyon klasörü dışlama ekleme

1. Gezinti bölmesinde, Uç Nokta **Ayarlar** \> **Otomasyon klasörü** **dışlamalarını** \> \> seçin.

2. Yeni klasör **dışlama'ya tıklayın**.

3. Klasör ayrıntılarını girin:

    - Klasör
    - Uzantılar
    - Dosya adları
    - Açıklama

4. **Kaydet**'e tıklayın.

> [!NOTE]
> Dışarıda bırakılan dosyaları toplama veya incelemeye yönelik Canlı Yanıt komutları hatayla başarısız olur: "Dosya dışarıda bırakıldı". Buna ek olarak, otomatik araştırmalarda dışlanan öğeler yoksayılacaktır.

## <a name="edit-an-automation-folder-exclusion"></a>Otomasyon klasörü dışlamalarını düzenleme

1. Gezinti bölmesinde, Uç Nokta **Ayarlar** \> **Otomasyon klasörü** **dışlamalarını** \> \> seçin.
2. Klasör **dışlamada** Düzenle'ye tıklayın.
3. Kuralın ayrıntılarını güncelleştirin ve Kaydet'e **tıklayın**.

## <a name="remove-an-automation-folder-exclusion"></a>Otomasyon klasörü dışlamalarını kaldırma

1. Gezinti bölmesinde, Uç Nokta **Ayarlar** \> **Otomasyon klasörü** **dışlamalarını** \> \> seçin.
2. **Dışlamayı kaldır'a tıklayın**.

## <a name="related-topics"></a>İlgili konular

- [İzin verilen/engellenen otomasyon listelerini yönetme](manage-indicators.md)
- [Otomasyon dosyası yüklemelerini yönetme](manage-automation-file-uploads.md)
