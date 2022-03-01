---
title: Bulut bloğu Microsoft Defender Virüsten Koruma zaman aşımı dönemini yapılandırma
description: Bir bulut belirlemesi beklerken Microsoft Defender Virüsten Koruma ne kadar süreyle çalıştırılamayacaklarını yapılandırabilirsiniz.
keywords: Microsoft Defender Virüsten Koruma, kötü amaçlı yazılımdan koruma, güvenlik, defender, bulut, zaman aşımı, blok, nokta, saniye
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 10/18/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: 1acd1a95ddc3aa679f0e5f1295e14cf33b4f97a0
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997548"
---
# <a name="configure-the-cloud-block-timeout-period"></a>Bulut engelleme zaman aşımı dönemini yapılandırma

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bu Microsoft Defender Virüsten Koruma şüpheli bir dosya bulduğunda, dosyanın bulut hizmeti tarafından sorgu yaparken [Microsoft Defender Virüsten Koruma önlenebilir](cloud-protection-microsoft-defender-antivirus.md).

Dosyanın engellenmiş olduğu varsayılan [süre](configure-block-at-first-sight-microsoft-defender-antivirus.md) 10 saniyedir. Güvenlik yöneticisiyseniz, dosyanın çalışmasına izin verilmeden önce beklemek için daha fazla süre belirtebilirsiniz. Bulut engelleme zaman aşımı süresini uzatmak, en son bulut hizmetlerinden doğru bir karar almak için yeterli Microsoft Defender Virüsten Koruma yardımcı olabilir.

## <a name="prerequisites-to-use-the-extended-cloud-block-timeout"></a>Genişletilmiş bulut engelleme zaman aşımını kullanmak için önkoşullar

[Uzatılmış bir zaman](configure-block-at-first-sight-microsoft-defender-antivirus.md) aşımı süresi belirtemeden önce engelin ve önkoşulların etkinleştirilmesi gerekir.

## <a name="specify-the-extended-timeout-period-using-microsoft-endpoint-manager"></a>Zaman Aşımı'nın kullanarak genişletilmiş zaman aşımı Microsoft Endpoint Manager

Bulut engelleme zaman aşımı dönemini, zaman aşımı süresi içinde bir [uç nokta güvenlik ilkesiyle Microsoft Endpoint Manager](/mem/intune/protect/endpoint-security-policy).

1. Yönetim merkezine Endpoint Manager ([https://endpoint.microsoft.com/](https://endpoint.microsoft.com/)) ve oturum açma.

2. Uç **nokta güvenliği'ne** ve sonra Yönet'in **altında Virüsten** **Koruma'ya seçin**.

3. Virüsten koruma ilkesi seçin (veya oluşturun).

4. Yapılandırma ayarları **bölümünde Bulut** **koruması'nın kapsamını genişletin**. Ardından **, Microsoft Defender Virüsten Koruma Saniye** olarak Uzatılmış Zaman Aşımı kutusunda, saniye olarak 1 saniye ile 50 saniye arasında daha uzun süre belirtin. Belirttiğiniz her şey varsayılan 10 saniyeye eklenir.

5. (Bu adım isteğe bağlıdır) Virüsten koruma ilkeniz üzerinde diğer değişiklikleri yapın. (Yardım mı gerekiyor? Bkz[. Ayarlar Microsoft Defender Virüsten Koruma ilke için Microsoft Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-windows).)

6. **Sonraki'yi** seçin ve ilkenizi yapılandırmayı bitirin.

## <a name="specify-the-extended-timeout-period-using-group-policy"></a>Grup İlkesini kullanarak genişletilmiş zaman aşımı dönemini belirtme

Bulut denetimleri için uzatılmış bir zaman aşımı belirtmek için Grup İlkesi'ne kullanabilirsiniz.

1. Grup İlkesi yönetim bilgisayarınızda, Grup İlkesi [Yönetim Konsolu'nu açın](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))

2. Yapılandırmak istediğiniz Grup İlkesi Nesnesi'ne sağ tıklayın ve Düzenle'yi **seçin**.

3. Grup İlkesi **Yönetim Düzenleyicisi'nde** Bilgisayar **yapılandırması'nda, ardından** Yönetim **şablonları'nın öğesini seçin**.

3. **MpEngine'in** **Windows için** \> **Microsoft Defender Virüsten Koruma** \> genişletin.

4. Genişletilmiş bulut denetimi **yapılandır'a çift tıklayın** ve seçeneğin etkinleştirildiğinden emin olun. 

   Bulut belirleme için beklerken dosyanın çalışıyor olması için ek süre belirtin. Saniye olarak, 1 saniye ile 50 saniye arasında ek süre belirtin. Belirttiğiniz her şey varsayılan 10 saniyeye eklenir.

5. **Tamam**'ı seçin.

 
