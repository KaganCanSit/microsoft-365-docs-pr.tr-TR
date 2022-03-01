---
title: Güvenlik denetimleri için ağ trafiği denetimi için ek tanım Microsoft Defender Virüsten Koruma
description: Güvenlik denetimleri için ağ trafiği incelemesi için ek tanım Microsoft Defender Virüsten Koruma.
keywords: Microsoft Defender Virüsten Koruma, kötü amaçlı yazılımdan koruma, güvenlik, defender, ağ trafiği incelemesi
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.date: 05/07/2021
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: f7b940604272035dc37b170eb759fa0ec45582b6
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998212"
---
# <a name="specify-additional-definition-sets-for-network-traffic-inspection"></a>Ağ trafiği incelemesi için ek tanım kümeleri belirtme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

Grup İlkesi kullanarak ağ trafiği incelemesi için ek tanım kümeleri belirtebilirsiniz.

## <a name="use-group-policy-to-specify-additional-definition-sets-for-network-traffic-inspection"></a>Ağ trafiği incelemesi için ek tanım kümeleri belirtmek üzere Grup İlkesi kullanma

1. Grup İlkesi yönetim uç noktanız üzerinde, Grup İlkesi [Yönetim Konsolu'nu açın](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Ağ **İnceleme Windows Bileşenleri** \> **Microsoft Defender Virüsten Koruma'e** \> gidin.

3. Ağ **trafiği incelemesi için ek tanım kümeleri belirtin öğesini seçin**. Varsayılan olarak, bu ilke Yapılandırılmadı **olarak ayarlanır**.

4. İlkeyi düzenlemek için, ilke **ayarını düzenle bağlantısını** seçin.

5. **Etkin'i** seçin ve sonra Seçenekler **bölümünde** Göster **... öğesini seçin**.

6. Listeye girdiler ekleyin ve tamam'ı **seçin**.

   Her girdi bir ad-değeri çifti olarak listelenmiş olmalıdır; burada ad, bir tanım kümesi GUID'sini dize gösterimidir. Örnek olarak, test güvenlik zekasına olanak sağlayacak tanım kümesi GUID aşağıdaki gibi tanımlanır: `{b54b6ac9-a737-498e-9120-6616ad3bf590}`. Değer kullanılmaz, dolayısıyla bu ayarı 'a ayarlamayı öneririz `0`.

7. **Tamam'ı** seçin ve güncelleştirilmiş Grup İlkesi Nesnenizi dağıtın. Bkz [. Grup İlkesi Yönetim Konsolu](/windows/win32/srvnodes/group-policy).

> [!TIP]
> Şirket içinde Grup İlkesi Nesneleri mi kullanıyorsunuz? Buluttaki çevirinin nasıl olduğunu öğrenin. [Grup İlkesi çözümlemesini kullanarak şirket içi grup ilkesi nesnelerinizi Çözümleme - Microsoft Endpoint Manager.](/mem/intune/configuration/group-policy-analytics)

## <a name="related-articles"></a>İlgili makaleler

- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Bulut teslimi korumasını etkinleştirme](enable-cloud-protection-microsoft-defender-antivirus.md)
- [Kötü amaçlı yazılımlardan koruma ilkeleri oluşturma ve dağıtma: Bulut koruma hizmeti](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)