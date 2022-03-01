---
title: Microsoft Defender'da Kimlik için Dizin Hizmetleri hesabını yapılandırma
description: Aynı hesapta Identity Directory Services için Microsoft Defender'ı yapılandırmayı Microsoft 365 Defender
ms.date: 08/15/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.openlocfilehash: 8928441e27215e75dc4456116c9a0e7890073852
ms.sourcegitcommit: 542e6b5d12a8d400c3b9be44d849676845609c5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "62999594"
---
# <a name="microsoft-defender-for-identity-directory-services-account-in-microsoft-365-defender"></a>Microsoft 365 Defender'da Identity Directory Services hesabı için Microsoft Defender

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender
- Kimlik için Defender

Bu makalede, Microsoft Defender for Identity Directory Services [hesabını aynı](/defender-for-identity) dosyada nasıl [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>Kimlik Doğrulama ve Doğrulama Microsoft 365 Defender bir parçası olarak, kimlik için Defender portalında yer alan konumlarından bazı seçenekler ve ayrıntılar değiştirilmiştir. Hem tanıdık hem de yeni özellikleri nerede bulamıyorum? bulmak için lütfen aşağıdaki ayrıntıları okuyun.

## <a name="configure-directory-services-account"></a>Dizin Hizmetleri hesabını yapılandırma

Algılayıcıyı [Active](sensor-health.md#add-a-sensor) Directory etki alanlarınıza bağlamak için Dizin Hizmetleri hesaplarını yapılandırmanız gerekir.

1. Daha <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, Kimlikler'Ayarlar'e **gidin**.

    ![Kimlikler'Ayarlar ardından Kimlikler'e gidin.](../../media/defender-identity/settings-identities.png)

1. Dizin **Hizmeti hesapları'ı seçin**. Hangi hesapların hangi etki alanlarıyla ilişkilendiril olduğunu yakında göreceğiz.

    ![Dizin Hizmeti hesapları.](../../media/defender-identity/directory-service-accounts.png)

1. Bir hesap seçmeniz, o hesabın ayarlarının yer alan bir bölme açar.

    ![Hesap ayarları'dır.](../../media/defender-identity/account-settings.png)

1. Yeni bir Dizin Hizmetleri hesabı eklemek için, Yeni hesap **oluştur'a** tıklayın ve **Hesap adı,** **Etki Alanı ve Parola'nın** alanını **doldurun**. Bunun bir Grup tarafından yönetilen hizmet **hesabı (** gMSA) olup olmadığını ve Tek etiketli bir etki alanına ait **olup olmadığını da seçebilirsiniz**.

    ![Yeni Dizin Hizmeti hesabı.](../../media/defender-identity/new-directory-service-account.png)

1. **Kaydet**'i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kimlik algılayıcısı durumu ve ayarları için Microsoft Defender](sensor-health.md)
