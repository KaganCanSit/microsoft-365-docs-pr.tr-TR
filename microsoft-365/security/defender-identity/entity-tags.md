---
title: Kimlik için Microsoft Defender varlık etiketlerini Microsoft 365 Defender
description: Microsoft 365 Defender'de Kimlik için Microsoft Defender etiketlerin nasıl uygulanabileceklerini Microsoft 365 Defender
ms.date: 06/08/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: c960f0cc1726155e733a0e88386fa7788cfc35e0
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468071"
---
# <a name="defender-for-identity-entity-tags-in-microsoft-365-defender"></a>Microsoft 365 Defender'de Kimlik varlık etiketleri için Defender

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender
- Kimlik için Microsoft Defender

Bu makalede, [Kimlik için Microsoft Defender varlık](/defender-for-identity) etiketlerinin nasıl [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>Kimlik Doğrulama ve Doğrulama Microsoft 365 Defender bir parçası olarak, kimlik için Defender portalında yer alan konumlarından bazı seçenekler ve ayrıntılar değiştirilmiştir. Hem tanıdık hem de yeni özellikleri nerede bulamıyorum? bulmak için lütfen aşağıdaki ayrıntıları okuyun.

## <a name="entity-tags"></a>Varlık etiketleri

Daha Microsoft 365 Defender'de Kimlik varlık etiketleri için üç tür **Defender'ı ayarlayın**: Hassas **etiketler**, **Honeytoken etiketleri** ve Exchange etiketleri.

Bu etiketleri ayarlamak için, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Etiketler'Microsoft 365 Defender</a> Ardından **Kimlikler** **Ayarlar'e gidin**.

:::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Kimlikler seçeneğinin altındaki Kimlikler Ayarlar." lightbox="../../media/defender-identity/settings-identities.png":::

Etiket ayarları Varlık etiketleri altında **görüntülenir**.

:::image type="content" source="../../media/defender-identity/tag-settings.png" alt-text="Varlık etiketleri bölmesi" lightbox="../../media/defender-identity/tag-settings.png":::

Her etiket türünü ayarlamak için aşağıdaki yönergeleri izleyin.

## <a name="sensitive--tags"></a>Hassas etiketler

Hassas **etiketi,** yüksek değerli varlıkları tanımlamak için kullanılır. Lateral movement path also relies on an entity's sensitivity status. Bazı varlıklar Kimlik için Defender tarafından otomatik olarak hassas kabul edilir. Bu varlıkların listesi için bkz. Hassas [varlıklar](/defender-for-identity/manage-sensitive-honeytoken-accounts#sensitive-entities).

Ayrıca, kullanıcıları, cihazları veya grupları el ile hassas olarak etiketleyebilirsiniz.

1. **Hassas'ı seçin**. Ardından, var olan hassas Kullanıcılar, **Cihazlar** **ve** Gruplar'ı **gördüğünüzde**.

   :::image type="content" source="../../media/defender-identity/sensitive-entities.png" alt-text="Hassas varlıklar menü öğesinde Cihazlar sekmesi" lightbox="../../media/defender-identity/sensitive-entities.png":::

1. Bu tür bir varlık **etiketlemek için, her** kategorinin altında Etiket... öğesini seçin. Örneğin, **Gruplar'ın altında** Etiket **grupları'ı seçin.** Etiketlemek için seçebilirsiniz grupların olduğu bir bölme açılır. Bir grubu aramak için, arama kutusuna grubun adını girin.

   :::image type="content" source="../../media/defender-identity/add-groups.png" alt-text="Grup ekleme seçeneği" lightbox="../../media/defender-identity/add-groups.png":::

1. Grubu seçin ve Seçim **ekle'ye tıklayın.**

   :::image type="content" source="../../media/defender-identity/add-selection.png" alt-text="Seçim ekle seçeneği" lightbox="../../media/defender-identity/add-selection.png":::

## <a name="honeytoken-tags"></a>Amasya etiketleri

Amasyalı varlıklar kötü amaçlı kötü niyetli kullanıcılar için yakalama olarak kullanılır. Bu balkök varlıklarla ilişkilendirilmiş herhangi bir kimlik doğrulaması uyarıyı tetikler.

Kullanıcıları veya cihazları, hassas hesapları **etiketle ilgili olarak olduğu gibi Honeytoken** etiketiyle etiketebilirsiniz.

1. **Honeytoken'i seçin**. Ardından, var olan amamsı Kullanıcılar ve **Cihazlar'ı** **görüyorsunuz**.

    ![Balkök varlıklar.](../../media/defender-identity/honeytoken-entities.png)

1. Bu tür bir varlık **etiketlemek için, her** kategorinin altında Etiket... öğesini seçin. Örneğin, **Kullanıcılar'ın altında** Kullanıcıları **etiketle'yi seçin.** Etiketlemek için seçebilirsiniz grupların olduğu bir bölme açılır. Bir grubu aramak için, arama kutusuna grubun adını girin.

   :::image type="content" source="../../media/defender-identity/add-users.png" alt-text="Kullanıcı ekleme seçeneği" lightbox="../../media/defender-identity/add-users.png":::

1. Kullanıcınızı seçin ve Seçim **ekle'ye tıklayın.**

   :::image type="content" source="../../media/defender-identity/add-selected-user.png" alt-text="Seçili bir kullanıcı ekleme seçeneği" lightbox="../../media/defender-identity/add-selected-user.png":::

## <a name="exchange-server-tags"></a>Exchange etiketlerini yapılandırma

Identity için Defender, sunucularınızı Exchange değerli varlıklar olarak kabul eder ve bunları otomatik olarak Hassas olarak **etiketler**. Cihazları el ile de sunucu olarak Exchange.

1. Sunucu **Exchange seçin**. Ardından, Exchange **server etiketiyle etiketlenmiş var olan cihazları** göreceğiniz.

   :::image type="content" source="../../media/defender-identity/exchange-servers.png" alt-text="Exchange sunucusu menü öğesi" lightbox="../../media/defender-identity/exchange-servers.png":::

1. Cihazı sunucu olarak etiketlemek için Exchange cihazları **etiketle'yi seçin**.  Etiketlemek için seçebilirsiniz cihazlarla bir bölme açılır. Bir cihazı aramak için, arama kutusuna cihazın adını girin.

   :::image type="content" source="../../media/defender-identity/add-devices.png" alt-text="Cihaz ekleme seçeneği" lightbox="../../media/defender-identity/add-devices.png":::

1. Cihazınızı seçin ve Seçim **ekle'ye tıklayın.**

   :::image type="content" source="../../media/defender-identity/select-device.png" alt-text="Cihaz seçimi" lightbox="../../media/defender-identity/select-device.png":::

## <a name="see-also"></a>Ayrıca bkz.

- [Kimlik güvenlik uyarıları için Defender'ı yönetme](manage-security-alerts.md)
