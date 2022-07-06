---
title: Uyumluluk merkezindeki özel hassas bilgi türlerini yönetme
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Uyumluluk Merkezi'nde özel hassas bilgi türlerini değiştirmeyi ve kaldırmayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5e0b1b91fd19a5e0705ad95affe888a87847caf8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621983"
---
# <a name="manage-custom-sensitive-information-types-in-the-compliance-center"></a>Uyumluluk merkezinde özel hassas bilgi türlerini yönetme

Bu makalede, Uyumluluk merkezinde mevcut bir özel hassas bilgi türünü değiştirme ve kaldırma adımlarında size yol gösterilir.

## <a name="modify-custom-sensitive-information-types-in-the-compliance-center"></a>Uyumluluk Merkezi'nde özel hassas bilgi türlerini değiştirme

1. Uyumluluk Merkezi'nde **Veri sınıflandırması** \> **Hassas bilgi türleri'ne** gidin ve değiştirmek istediğiniz listeden hassas bilgi türünü seçin **Düzenle'yi** seçin.

2. Benzersiz birincil ve destekleyici öğeler, güvenilirlik düzeyleri, karakter yakınlığı ve [**ek denetimler içeren başka desenler**](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks) ekleyebilir veya var olanları düzenleyebilir/kaldırabilirsiniz.

## <a name="remove-custom-sensitive-information-types-in-the-compliance-center"></a>Uyumluluk Merkezi'nde özel hassas bilgi türlerini kaldırma 

> [!NOTE]
> Yalnızca özel hassas bilgi türlerini kaldırabilirsiniz; yerleşik hassas bilgi türlerini kaldıramazsınız.

> [!IMPORTANT]
> Özel bir hassas bilgi türünü kaldırmadan önce, DLP ilkelerinin veya Exchange posta akışı kurallarının (aktarım kuralları olarak da bilinir) hala hassas bilgi türüne başvurmadığını doğrulayın.

1. Uyumluluk Merkezi'nde **Veri sınıflandırması** \> **Hassas bilgi türleri'ne** gidin ve kaldırmak istediğiniz listeden hassas bilgi türünü seçin.

2. Açılan açılır öğede **Sil'i** seçin.
