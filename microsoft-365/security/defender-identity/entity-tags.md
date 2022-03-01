---
title: Microsoft 365 Defender'de Identity varlık etiketleri için Microsoft Defender
description: Microsoft 365 Defender'de Identity entity etiketleri için Microsoft Defender'ı Microsoft 365 Defender
ms.date: 06/08/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.openlocfilehash: e53c14405d3d190715b49e58061aee8ba771180a
ms.sourcegitcommit: 542e6b5d12a8d400c3b9be44d849676845609c5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "62999599"
---
# <a name="defender-for-identity-entity-tags-in-microsoft-365-defender"></a>Microsoft 365 Defender'de Kimlik varlık etiketleri için Defender

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender
- Kimlik için Defender

Bu makalede, Microsoft Defender for [Identity entity tags for Identity etiketlerinin](/defender-for-identity) [Microsoft 365 Defender.](/microsoft-365/security/defender/overview-security-center)

>[!IMPORTANT]
>Kimlik Doğrulama ve Doğrulama Microsoft 365 Defender bir parçası olarak, kimlik için Defender portalında yer alan konumlarından bazı seçenekler ve ayrıntılar değiştirilmiştir. Hem tanıdık hem de yeni özellikleri nerede bulamıyorum? bulmak için lütfen aşağıdaki ayrıntıları okuyun.

## <a name="entity-tags"></a>Varlık etiketleri

Daha Microsoft 365 Defender'de Kimlik varlık etiketleri için üç tür **Defender'ı ayarlayın**: Hassas **etiketler**, **Honeytoken etiketleri** ve Exchange etiketleri.

Bu etiketleri ayarlamak için, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Etiketler'Microsoft 365 Defender</a> Ardından **Kimlikler** **Ayarlar'e gidin**.

![Kimlikler'Ayarlar ardından Kimlikler'e gidin.](../../media/defender-identity/settings-identities.png)

Etiket ayarları Varlık etiketleri altında **görüntülenir**.

![Etiket ayarı türleri.](../../media/defender-identity/tag-settings.png)

Her etiket türünü ayarlamak için aşağıdaki yönergeleri izleyin.

## <a name="sensitive--tags"></a>Hassas etiketler

Hassas **etiketi,** yüksek değerli varlıkları tanımlamak için kullanılır. Lateral movement path also relies on an entity's sensitivity status. Bazı varlıklar Kimlik için Defender tarafından otomatik olarak hassas kabul edilir. Bu varlıkların listesi için bkz. Hassas [varlıklar](/defender-for-identity/manage-sensitive-honeytoken-accounts#sensitive-entities).

Ayrıca, kullanıcıları, cihazları veya grupları el ile hassas olarak etiketleyebilirsiniz.

1. **Hassas'ı seçin**. Ardından, var olan hassas Kullanıcılar, **Cihazlar** **ve** Gruplar'ı **gördüğünüzde**.

    ![Hassas varlıklar.](../../media/defender-identity/sensitive-entities.png)

1. Bu tür bir varlık **etiketlemek için, her** kategorinin altında Etiket... öğesini seçin. Örneğin, **Gruplar'ın altında** Etiket **grupları'ı seçin.** Etiketlemek için seçebilirsiniz grupların olduğu bir bölme açılır. Bir grubu aramak için, arama kutusuna grubun adını girin.

    ![Grup ekleyin.](../../media/defender-identity/add-groups.png)

1. Grubu seçin ve Seçim **ekle'ye tıklayın.**

    ![Seçim ekle'yi seçin.](../../media/defender-identity/add-selection.png)

## <a name="honeytoken-tags"></a>Amasya etiketleri

Amasyalı varlıklar kötü amaçlı kötü niyetli kullanıcılar için yakalama olarak kullanılır. Bu balkök varlıklarla ilişkilendirilmiş herhangi bir kimlik doğrulaması uyarıyı tetikler.

Kullanıcıları veya cihazları, hassas hesapları **etiketle ilgili olarak olduğu gibi Honeytoken** etiketiyle etiketebilirsiniz.

1. **Honeytoken'i seçin**. Ardından, var olan amamsı Kullanıcılar ve **Cihazlar'ı** **görüyorsunuz**.

    ![Balkök varlıklar.](../../media/defender-identity/honeytoken-entities.png)

1. Bu tür bir varlık **etiketlemek için, her** kategorinin altında Etiket... öğesini seçin. Örneğin, **Kullanıcılar'ın altında** Kullanıcıları **etiketle'yi seçin.** Etiketlemek için seçebilirsiniz grupların olduğu bir bölme açılır. Bir grubu aramak için, arama kutusuna grubun adını girin.

    ![Kullanıcı ekle'yi seçin.](../../media/defender-identity/add-users.png)

1. Kullanıcınızı seçin ve Seçim **ekle'ye tıklayın.**

    ![Seçili kullanıcı ekleme.](../../media/defender-identity/add-selected-user.png)

## <a name="exchange-server-tags"></a>Exchange etiketlerini yapılandırma

Identity için Defender, sunucularınızı Exchange değerli varlıklar olarak kabul eder ve bunları otomatik olarak Hassas olarak **etiketler**. Cihazları el ile de sunucu olarak Exchange.

1. Sunucu **Exchange seçin**. Ardından, Exchange **server etiketiyle etiketlenmiş var olan cihazları** göreceğiniz.

    ![Exchange seçin.](../../media/defender-identity/exchange-servers.png)

1. Cihazı sunucu olarak etiketlemek için Exchange cihazları **etiketle'yi seçin**.  Etiketlemek için seçebilirsiniz cihazlarla bir bölme açılır. Bir cihazı aramak için, arama kutusuna cihazın adını girin.

    ![Cihaz ekleyin'i seçin.](../../media/defender-identity/add-devices.png)

1. Cihazınızı seçin ve Seçim **ekle'ye tıklayın.**

    ![Cihazı seçin.](../../media/defender-identity/select-device.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kimlik güvenlik uyarıları için Defender'ı yönetme](manage-security-alerts.md)
