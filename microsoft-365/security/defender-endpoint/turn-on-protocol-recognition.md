---
title: İletişim için protokol tanımayı Microsoft Defender Virüsten Koruma
description: İletişim kuralları için protokol tanımayı Microsoft Defender Virüsten Koruma.
keywords: Microsoft Defender Virüsten Koruma, kötü amaçlı yazılımdan koruma, güvenlik, defender, protokol tanıma
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.date: 02/21/2022
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.collection: m365-security-compliance
ms.openlocfilehash: 221eff4af6bf8e77f29db84694bf3a683107fc8c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325187"
---
# <a name="turn-on-protocol-recognition"></a>Protokol tanımayı açma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bu ilke ayarı, bilinen güvenlik açıklarından yararlanmaya karşı ağ koruması için protokol tanımayı yapılandırmaya olanak sağlar. Bu ayarı etkinleştirir veya yapılandırmazsanız, protokol tanıma etkinleştirilir. Bu ayarı devre dışı bırakırsanız, protokol tanıma devre dışı bırakılır.

[!IMPORTANT]
Bu ayar artık kullanım dışıdır. 

## <a name="use-group-policy-to-configure-protocol-recognition"></a>Protokol tanımayı yapılandırmak için Grup İlkesi kullanma

1. Grup İlkesi yönetim uç noktanız üzerinde, Grup İlkesi [Yönetim Konsolu'nu açın](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Ağ İnceleme **Sistemi için** \> **Bilgisayar Yapılandırması Windows** \> **Bileşenleri** **Microsoft Defender Virüsten Koruma'e** \> \> gidin.

3. Protokol **tanımayı seçin**. Varsayılan olarak, bu ilke etkindir. Yapılandırılmadı **olarak ayarlanırsa**, tanımın emeklilik etkinleştirilir.

4. İlkeyi düzenlemek için, ilke **ayarını düzenle bağlantısını** seçin.

5. **Etkin'i** ve sonra Tamam'ı **seçin**.

6. Güncelleştirilmiş Grup İlkesi Nesnenizi dağıtın. Bkz [. Grup İlkesi Yönetim Konsolu](/windows/win32/srvnodes/group-policy).

> [!TIP]
> Şirket içinde Grup İlkesi Nesneleri mi kullanıyorsunuz? Buluttaki çevirinin nasıl olduğunu öğrenin. [Grup İlkesi çözümlemesini kullanarak şirket içi grup ilkesi nesnelerinizi Çözümleme - Microsoft Endpoint Manager.](/mem/intune/configuration/group-policy-analytics)

## <a name="related-articles"></a>İlgili makaleler

- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Bulut teslimi korumasını etkinleştirme](enable-cloud-protection-microsoft-defender-antivirus.md)
- [Kötü amaçlı yazılımlardan koruma ilkeleri oluşturma ve dağıtma: Bulut koruma hizmeti](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)
