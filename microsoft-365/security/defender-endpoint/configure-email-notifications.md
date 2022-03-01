---
title: Uç Nokta için Microsoft Defender'da uyarı bildirimlerini yapılandırma
description: Önem derecesi ve diğer ölçütlere göre güvenlik uyarıları için e-posta bildirimi ayarlarını yapılandırmak üzere Uç Nokta için Microsoft Defender'ı kullanabilirsiniz.
keywords: e-posta bildirimleri, uyarı bildirimlerini yapılandırma, Uç Nokta için Microsoft Defender, Uç nokta bildirimleri için Microsoft Defender, Uç nokta uyarıları için Microsoft Defender, windows enterprise, windows eğitimi
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
ms.openlocfilehash: f2e4cc2db64a01605a0003561ceda27409b16cf5
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998181"
---
# <a name="configure-alert-notifications-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'da uyarı bildirimlerini yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-emailconfig-abovefoldlink)

Belirtilen alıcılara yeni uyarılar için e-posta bildirimleri göndermek üzere Uç Nokta için Defender'ı yapılandırabilirsiniz. Bu özellik, hemen bilgi alınan ve önem derecelerine göre uyarılara göre işlem gören bir grup bireyler tanımlamanıza olanak sağlar.

> [!NOTE]
> Yalnızca 'Güvenlik ayarlarını yönetme' izinleri olan kullanıcılar e-posta bildirimlerini yapılandırabilirsiniz. Temel izin yönetimini kullanmayı seçtiyseniz, Güvenlik Yöneticisi veya Genel Yönetici rolüne sahip kullanıcılar e-posta bildirimlerini yapılandırabilirsiniz.

Bildirimleri tetikleyen uyarı önem düzeyi düzeylerini ayarlayın. Ayrıca, e-posta bildiriminin alıcılarını ekleyebilir veya kaldırabilirsiniz. Yeni alıcılar, eklendikten sonra tetiklenen uyarılar hakkında bilgi alır. Uyarılar hakkında daha fazla bilgi için Bkz [. Uyarılar kuyruğu görüntüleme ve düzenleme](alerts-queue.md).

Rol tabanlı erişim denetimi (RBAC) kullanıyorsanız, alıcılar yalnızca bildirim kuralında yapılandırılan cihaz gruplarına bağlı olarak bildirimler alır.
Uygun izinlere sahip kullanıcılar yalnızca cihaz grubu yönetim kapsamıyla sınırlı olan bildirimleri oluşturabilir, düzenleyebilir veya silebilir.
Yalnızca Genel yönetici rolüne atanan kullanıcılar, tüm cihaz grupları için yapılandırılmış bildirim kurallarını yönetebilir.

E-posta bildirimi, uyarıyla ilgili temel bilgileri ve daha fazla araştırma yapmak istediğiniz portalın bağlantısını içerir.

## <a name="create-rules-for-alert-notifications"></a>Uyarı bildirimleri için kurallar oluşturma
E-posta bildirimlerinin gönderilmesiyle ilgili cihazları ve bildirim alıcılarını uyaran kurallar oluşturabilirsiniz.


1. Gezinti bölmesinde Genel **E-posta Ayarlar** \> **Uç Noktaları** **Seç'i** \> \> **seçin**.

2. Öğe **ekle'ye tıklayın**.

3. Genel bilgileri belirtin:
    - **Kural adı** - Bildirim kuralı için bir ad belirtin.
    - **Kuruluş adını dahil** edin - E-posta bildirimide görünen müşteri adını belirtin.
    - **Kiracıya özgü portal bağlantısını ekle** - Belirli bir kiracıya erişim izni vermek için kiracı kimliğine sahip bir bağlantı ekler.
    - **Cihaz bilgilerini dahil** edin - E-posta uyarısı gövdesine cihaz adını içerir.

        > [!NOTE]
        > Bu bilgiler, Uç nokta verileri için Defender'nız için seçtiğiniz coğrafi konumda yer alan alıcı posta sunucuları tarafından işlenebilir.

    - **Cihazlar** - Alıcıları tüm cihazlardaki (yalnızca genel yönetici rolü) veya seçili cihaz gruplarında uyarılar için bilgilendirmeyi seçin. Daha fazla bilgi için bkz [. Cihaz grupları oluşturma ve yönetme](machine-groups.md).
    - **Uyarı önem derecesi** - Uyarı önem düzeyi seçin.

4. **İleri**'ye tıklayın.

5. Alıcının e-posta adresini girin ve Alıcı **ekle'ye tıklayın**. Birden çok e-posta adresi ebilirsiniz.

6. Test e-postası gönder'i seçerek e-posta alıcılarını **e-posta alıcılarını alanın.**

7. Bildirim kuralını **kaydet'e tıklayın**.

## <a name="edit-a-notification-rule"></a>Bildirim kuralını düzenleme

1. Düzenlemek istediğiniz bildirim kuralını seçin.

2. Genel ve Alıcı sekmesi bilgilerini güncelleştirin.

3. Bildirim kuralını **kaydet'e tıklayın**.

## <a name="delete-notification-rule"></a>Bildirim kuralını silme

1. Silmek istediğiniz bildirim kuralını seçin.

2. **Sil**'e tıklayın.

## <a name="troubleshoot-email-notifications-for-alerts"></a>Uyarılar için e-posta bildirimlerini sorunlarını giderme

Bu bölümde, uyarılar için e-posta bildirimlerini kullanırken karşılaşabilirsiniz çeşitli sorunlar liste almaktadır.

**Sorun:** Hedeflenen alıcılar, bildirimleri almamalarını bildirler.

**Çözüm:** Bildirimlerin e-posta filtreleri tarafından engellenmiş olduğundan emin olun:

1. Uç nokta için Defender e-posta bildirimlerinin Gereksiz E-posta klasörüne gönderilmey olup olmadığını kontrol edin. Bunları Gereksiz değil olarak işaretleme.
2. E-posta güvenlik ürünü, Uç Nokta için Defender'dan gelen e-posta bildirimlerini engellemez.
3. Uç nokta e-posta bildirimleri için Defender'nızı yakalayacak ve hareket ettiren e-posta uygulaması kurallarınızı kontrol edin.

## <a name="related-topics"></a>İlgili konular

- [Veri bekletme ayarlarını güncelleştirme](data-retention-settings.md)
- [Gelişmiş özellikleri yapılandırma](advanced-features.md)
- [Uç Nokta için Microsoft Defender'da güvenlik açığı e-posta bildirimlerini yapılandırma](/microsoft-365/security/defender-endpoint/configure-vulnerability-email-notifications)
