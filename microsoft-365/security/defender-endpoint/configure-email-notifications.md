---
title: Uç Nokta için Microsoft Defender'de uyarı bildirimlerini yapılandırma
description: Güvenlik uyarıları için önem derecesine ve diğer ölçütlere göre e-posta bildirim ayarlarını yapılandırmak için Uç Nokta için Microsoft Defender kullanabilirsiniz.
keywords: e-posta bildirimleri, uyarı bildirimlerini yapılandırma, Uç Nokta için Microsoft Defender, Uç Nokta için Microsoft Defender bildirimleri, Uç Nokta için Microsoft Defender uyarıları, Windows Enterprise, Windows Education
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
ms.openlocfilehash: fde5ce238a44b6722770338378ae33c54a38a450
ms.sourcegitcommit: 60970cf8a2cb451011c423d797dfb77925394f89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2022
ms.locfileid: "65587500"
---
# <a name="configure-alert-notifications-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'de uyarı bildirimlerini yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [İş için Microsoft Defender](../defender-business/mdb-overview.md)

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-emailconfig-abovefoldlink)

Uç Nokta için Defender'ı yeni uyarılar için belirtilen alıcılara e-posta bildirimleri gönderecek şekilde yapılandırabilirsiniz. Bu özellik, hemen bilgilendirilecek ve önem derecelerine göre uyarılar üzerinde işlem yapabilecek bir grup kişiyi tanımlamanızı sağlar.

[İş için Defender](../defender-business/mdb-overview.md) kullanıyorsanız, belirli kullanıcılar (roller veya gruplar için değil) için e-posta bildirimleri ayarlayabilirsiniz.

> [!NOTE]
> Yalnızca 'Güvenlik ayarlarını yönetme' izinlerine sahip kullanıcılar e-posta bildirimlerini yapılandırabilir. Temel izin yönetimini kullanmayı seçtiyseniz, Güvenlik Yöneticisi veya Genel Yönetici rollerine sahip kullanıcılar e-posta bildirimlerini yapılandırabilir.

Bildirimleri tetikleyen uyarı önem düzeylerini ayarlayabilirsiniz. E-posta bildiriminin alıcılarını da ekleyebilir veya kaldırabilirsiniz. Yeni alıcılar eklendikten sonra tetiklenen uyarılar hakkında bildirim alır. Uyarılar hakkında daha fazla bilgi için bkz. [Uyarılar sırasını görüntüleme ve düzenleme](alerts-queue.md).

Rol tabanlı erişim denetimi (RBAC) kullanıyorsanız, alıcılar yalnızca bildirim kuralında yapılandırılan cihaz gruplarına göre bildirim alır. Uygun izne sahip kullanıcılar yalnızca cihaz grubu yönetim kapsamıyla sınırlı bildirimler oluşturabilir, düzenleyebilir veya silebilir. Yalnızca Genel yönetici rolüne atanan kullanıcılar tüm cihaz grupları için yapılandırılmış bildirim kurallarını yönetebilir.

E-posta bildirimi uyarı hakkında temel bilgileri ve daha fazla araştırma yapabileceğiniz portalın bağlantısını içerir.

## <a name="create-rules-for-alert-notifications"></a>Uyarı bildirimleri için kurallar oluşturma
Ve bildirim alıcıları için e-posta bildirimleri göndermek için cihazları ve uyarı önem derecelerini belirleyen kurallar oluşturabilirsiniz.

1. Gezinti bölmesinde **Uç Noktalar** \> **Genel** \> **E-posta** **bildirimleri'ni Ayarlar** \> seçin.

2. **Öğe ekle'ye** tıklayın.

3. Genel bilgileri belirtin:
    - **Kural adı** - Bildirim kuralı için bir ad belirtin.
    - **Kuruluş adını ekle** - E-posta bildiriminde görünen müşteri adını belirtin.
    - **Kiracıya özgü portal bağlantısını ekle** - Belirli bir kiracıya erişime izin vermek için kiracı kimliğine sahip bir bağlantı ekler.
    - **Cihaz bilgilerini ekle** - Cihaz adını e-posta uyarı gövdesine ekler.

        > [!NOTE]
        > Bu bilgiler, Uç Nokta için Defender verileriniz için seçtiğiniz coğrafi konumda olmayan alıcı posta sunucuları tarafından işlenebilir.

    - **Cihazlar** - Tüm cihazlardaki (yalnızca Genel yönetici rol) veya seçili cihaz gruplarında uyarıları alıcılara bildirmeyi seçin. Daha fazla bilgi için bkz. [Cihaz gruplarını oluşturma ve yönetme](machine-groups.md). ( [İş için Defender](../defender-business/mdb-overview.md) kullanıyorsanız cihaz grupları geçerli değildir.)
    - **Uyarı önem derecesi** - Uyarı önem düzeyini seçin.

4. **İleri**'ye tıklayın.

5. Alıcının e-posta adresini girin ve **Alıcı ekle'ye** tıklayın. Birden çok e-posta adresi ekleyebilirsiniz.

6. Test e-postası gönder'i seçerek e-posta alıcılarının **e-posta** bildirimlerini alabildiğini denetleyin.

7. **Bildirim kuralını kaydet'e** tıklayın.

## <a name="edit-a-notification-rule"></a>Bildirim kuralını düzenleme

1. Düzenlemek istediğiniz bildirim kuralını seçin.

2. Genel ve Alıcı sekmesi bilgilerini güncelleştirin.

3. **Bildirim kuralını kaydet'e** tıklayın.

## <a name="delete-notification-rule"></a>Bildirim kuralını silme

1. Silmek istediğiniz bildirim kuralını seçin.

2. **Sil**'e tıklayın.

## <a name="troubleshoot-email-notifications-for-alerts"></a>Uyarılar için e-posta bildirimlerinde sorun giderme

Bu bölümde, uyarılar için e-posta bildirimlerini kullanırken karşılaşabileceğiniz çeşitli sorunlar listelenir.

**Sorun:** Hedeflenen alıcılar bildirimleri almadıklarını bildirir.

**Çözüm:** Bildirimlerin e-posta filtreleri tarafından engellenmediğinden emin olun:

1. Uç Nokta için Defender e-posta bildirimlerinin Gereksiz E-posta klasörüne gönderilmediğinden emin olun. Bunları Gereksiz değil olarak işaretleyin.
2. E-posta güvenlik ürününüzün Uç Nokta için Defender'dan gelen e-posta bildirimlerini engellemediğinden emin olun.
3. Uç Nokta için Defender e-posta bildirimlerinizi yakalayıp taşıyabilecek e-posta uygulama kurallarınızı denetleyin.

## <a name="related-topics"></a>İlgili konular

- [Veri saklama ayarlarını güncelleştirme](data-retention-settings.md)
- [Gelişmiş özellikleri yapılandırın](advanced-features.md)
- [Uç Nokta için Microsoft Defender'de güvenlik açığı e-posta bildirimlerini yapılandırma](/microsoft-365/security/defender-endpoint/configure-vulnerability-email-notifications)
