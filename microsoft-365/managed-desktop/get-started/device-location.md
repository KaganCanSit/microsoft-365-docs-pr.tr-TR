---
title: Windows 10 konumu hizmeti
description: Cihazlarınız için konum Windows nasıl açık olduğunu açıklar
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: b12f0d188c8347762443cc80e24cfdd7c6280acc
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63014381"
---
# <a name="windows-10-location-service"></a>Windows 10 konumu hizmeti

Microsoft Yönetilen Masaüstü'nüzde cihazlar AutoPilot Windows kullanılarak kaydedilir. Bu süreç, iş veya iş yerleriyle Azure Active Directory yönetmenize Microsoft Intune.

Varsayılan olarak, Windows 10 "hazır değil" deneyimi sırasında Gizlilik ayarlarında etkinleştirilmediği sürece, cihaz ilk kez etkinleştirildiğinde Konum Konumu hizmeti devre dışı bırakılır. Microsoft Yönetilen Masaüstü'ne AutoPilot kaydı sırasında bu ayarlar gizlenir. AutoPilot'ın nasıl ayar olduğu hakkında daha fazla bilgi için bkz. [AutoPilot ile ilk çalıştırma deneyimi ve Kayıt Durumu Sayfası](esp-first-run.md).

Bu nedenle, Microsoft Yönetilen Masaüstü cihazları cihazlarının konumlarını elde etmemektedir ve saat dilimleri gibi çeşitli Windows özelliklerinin işlevlerini sınırlar. Konum hizmeti hakkında daha fazla Windows 10 için bkz. [Windows 10 hizmeti ve gizliliği.](https://support.microsoft.com/windows/windows-10-location-service-and-privacy-3a8eee0a-5b0b-dc07-eede-2a5ca1c49088)

Microsoft Yönetilen Masaüstü'ne katılmak için konum hizmetini kullanmak zorunda değilsiniz. Kullanıcı deneyimi kısıtlanır. Örneğin, kullanıcılarınız farklı bir saat diliminde çalışmaya başladıklarında, cihazlar çalışmakta olduğu saat dilimini otomatik olarak belirleyecek.

## <a name="enable-the-location-service"></a>Konum hizmetini etkinleştirme

Şunları da s kaydettiysiniz:

- Cihazları Microsoft Yönetilen Masaüstü hizmetine kaydolarak konum hizmetini kullanmayı kabul edin veya
- Kaydın ardından hizmeti açabilirsiniz veya kapatabilirsiniz.

### <a name="opt-in-during-enrollment"></a>Kayıt sırasında katılma

Microsoft Yönetilen Masaüstü hizmetinin konum hizmetini etkinleştirmesi sebilirsiniz. Kayıt sırasında, kayıt konumu hizmetinin cihazlarda etkinleştirilmesine izin vermek Windows 10 isteyip olmadığını seçmeniz isteniyor.

### <a name="control-the-location-service-after-enrollment"></a>Kayıt sonrasında konum hizmetini denetleme

Yönetici portalı aracılığıyla bir destek isteği göndererek, istediğiniz zaman konum hizmetinin açık ( [veya](../working-with-managed-desktop/admin-support.md) kapalı) [durumda olabilirsiniz](access-admin-portal.md).

## <a name="how-microsoft-managed-desktop-configures-the-windows-10-location-service"></a>Microsoft Yönetilen Masaüstü en son Windows 10 hizmetini nasıl yapılandırıyor?

Konum hizmetini kullanmayı kabul edersiniz, kullanıcıların gizliliğini etkilemeden gerekli minimum ayarları kullanırız. Daha fazla bilgi için konum [Windows 10 ve gizlilik bilgilerine bakın](https://support.microsoft.com/windows/windows-10-location-service-and-privacy-3a8eee0a-5b0b-dc07-eede-2a5ca1c49088).

Microsoft Yönetilen Masaüstü, Kişisel **Ayarlar'daki** **Konum Windows bu cihaz** üzerinde **konuma erişime izin ver olarak ayarlar**. Kullanıcı arabirimi şöyle görünüyor:

 :::image type="content" source="../../media/MMD-location-services-UI.png" alt-text="Ayarları değiştir'Windows ayarları.":::

> [!NOTE]
> Konum hizmetini kullanmayı tercih edersiniz, bu yalnızca yakın işletim Windows için geçerlidir. Uygulamaların konum hizmetlerini kullanmasına izin verilmez. Her kullanıcı uygulamaların konumlarına erişmesine izin verip ver vermeyeceğinizi seçebilir.
