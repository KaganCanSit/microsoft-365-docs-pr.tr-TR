---
title: Dizin'de Dizin Hizmetleri Kimlik için Microsoft Defender
description: Microsoft 365 Defender'de Kimlik için Microsoft Defender Directory Services hesabını yapılandırmayı Microsoft 365 Defender
ms.date: 08/15/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: e31c226037d5d9e945350ba73e1df9abc79571e9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470009"
---
# <a name="microsoft-defender-for-identity-directory-services-account-in-microsoft-365-defender"></a>Kimlik için Microsoft Defender'da Dizin Hizmetleri Microsoft 365 Defender

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender
- Kimlik için Microsoft Defender

Bu makalede, aynı hesapta [Kimlik için Microsoft Defender](/defender-for-identity) Dizin Hizmetleri hesabının nasıl [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>Kimlik Doğrulama ve Doğrulama Microsoft 365 Defender bir parçası olarak, kimlik için Defender portalında yer alan konumlarından bazı seçenekler ve ayrıntılar değiştirilmiştir. Hem tanıdık hem de yeni özellikleri nerede bulamıyorum? bulmak için lütfen aşağıdaki ayrıntıları okuyun.

## <a name="configure-directory-services-account"></a>Dizin Hizmetleri hesabını yapılandırma

Algılayıcıyı [Active](sensor-health.md#add-a-sensor) Directory etki alanlarınıza bağlamak için Dizin Hizmetleri hesaplarını yapılandırmanız gerekir.

1. Daha <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, Kimlikler'Ayarlar'e **gidin**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Kimlikler sayfasındaki Ayarlar seçeneği" lightbox="../../media/defender-identity/settings-identities.png":::


1. Dizin **Hizmeti hesapları'ı seçin**. Hangi hesapların hangi etki alanlarıyla ilişkilendiril olduğunu yakında göreceğiz.

   :::image type="content" source="../../media/defender-identity/directory-service-accounts.png" alt-text="Dizin Hizmeti hesapları menü öğesi" lightbox="../../media/defender-identity/directory-service-accounts.png":::

1. Bir hesap seçmeniz, o hesabın ayarlarının yer alan bir bölme açar.

   :::image type="content" source="../../media/defender-identity/account-settings.png" alt-text="Hesap ayarları sayfası" lightbox="../../media/defender-identity/account-settings.png":::

1. Yeni bir Dizin Hizmetleri hesabı eklemek için, Yeni hesap **oluştur'a** tıklayın ve **Hesap adı,** **Etki Alanı ve Parola'nın** alanını **doldurun**. Bunun bir Grup tarafından yönetilen hizmet **hesabı (** gMSA) olup olmadığını ve Tek etiketli bir etki alanına ait **olup olmadığını da seçebilirsiniz**.

   :::image type="content" source="../../media/defender-identity/new-directory-service-account.png" alt-text="Yeni hesap oluştur seçeneği" lightbox="../../media/defender-identity/new-directory-service-account.png":::

1. **Kaydet**'i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kimlik için Microsoft Defender algılayıcı sağlığı ve ayarlarını değiştirme](sensor-health.md)
