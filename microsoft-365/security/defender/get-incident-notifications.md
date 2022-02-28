---
title: E-posta ile olay bildirimlerini Microsoft 365 Defender
description: E-postada olaylar için e-posta bildirimleri almak için kuralları Microsoft 365 Defender
keywords: olay, e-posta, e-posta notasyonu, yapılandırma, kullanıcılar, posta kutusu, e-posta, olaylar, çözümleme, yanıt
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 600ff555762112222769fde0372716f4a89a12b9
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2021
ms.locfileid: "62989987"
---
# <a name="get-incident-notifications-by-email"></a>E-postayla olay bildirimlerini alın

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Yeni olaylar veya Microsoft 365 Defender güncelleştirmeleri içeren bir e-posta ile personelinizi bilgilendiren ekipler oluşturabilirsiniz. Şu temel bildirim bildirimlerini alırsınız:

- Olay önem derecesi.
- Cihaz grubu.
- Yalnızca olay başına ilk güncelleştirmede.

E-posta bildiriminde olay adı, önem derecesi ve kategoriler gibi olayla ilgili önemli ayrıntılar ve diğerleri yer alır. Ayrıca doğrudan olayın üzerine gidip çözümlemenizi hemen başlatabilirsiniz. Daha fazla bilgi için bkz [. Olayları araştırma](investigate-incidents.md).

E-posta bildirimlerine alıcı ekleyebilir veya alıcıları kaldırabilirsiniz. Yeni alıcılar eklendikten sonra olaylar hakkında bilgi alır. 

>[!NOTE]
>E-posta bildirim ayarlarını yapılandırmak için 'Güvenlik ayarlarını yönet' izni gerekir. Temel izin yönetimini kullanmayı seçtiyseniz, Güvenlik Yöneticisi veya Genel Yönetici rolüne sahip kullanıcılar sizin için e-posta bildirimlerini yapılandırabilirsiniz. <br> <br>
Benzer şekilde, kuruluşta rol tabanlı erişim denetimi (RBAC) kullanıyorsa, yalnızca yönetmenize izin verilen cihaz gruplarına göre bildirim oluşturabilir, düzenleyebilir, silebilir ve alabilirsiniz.

## <a name="create-a-rule-for-email-notifications"></a>E-posta bildirimleri için kural oluşturma

Yeni bir kural oluşturmak ve e-posta bildirimi ayarlarını özelleştirmek için bu adımları izleyin.

1. Gezinti bölmesinde, Olay **e-Ayarlar > Microsoft 365 Defender > e-posta bildirimlerini seçin**.
2. Öğe **ekle'yi seçin**.
3. Temel **Bilgiler sayfasında** , kural adını ve açıklamasını yazın ve Ardından Sonraki'yi **seçin**.
4. Bildirim **ayarları sayfasında** şunları yapılandırabilirsiniz:
    - **Uyarı önem derecesi** - Olay bildirimini tetikleyen uyarı önem derecelerini seçin. Örneğin, yalnızca yüksek önem derecesine sahip olaylar hakkında bilgi sahibi olmak için Yüksek'i **seçin**.
    - **Cihaz grubu kapsamı** - Tüm cihaz gruplarını belirtebilirsiniz veya kiracınız için cihaz grupları listesinden seçim edebilirsiniz.
    - **Her olay için yalnızca ilk kez bildir** - Yalnızca diğer seçimlerinizi eşleşen ilk uyarıda bildirim almak için bildirim almak için seçin. Daha sonra, olayla ilgili güncelleştirmeler veya uyarılar ek bildirim göndermez.
    - **E-postaya kuruluş adını dahil** edin - Kuruluş adının e-posta bildiriminde görünmesini istediğinizi seçin.
    - **Kiracıya özgü portal bağlantısını ekle** - Belirli bir kiracıya erişim için e-posta bildiriminde kiracı kimliğiyle bir bağlantı eklemek Microsoft 365 seçin.

    :::image type="content" source="../../media/get-incident-notifications/incidents-ss-email-notification-settings.png" alt-text="Olay e-posta bildirimleri için bildirim ayarları.":::

5. **İleri**'yi seçin. Alıcılar **sayfasında** , olay bildirimlerini alacak e-posta adreslerini ekleyin. Her yeni **e-posta** adresini yazdikten sonra Ekle'yi seçin. Bildirimleri test etmek ve alıcıların bunları gelen kutularında almalarını sağlamak için Test **e-postası gönder'i seçin**. 
6. **İleri**'yi seçin. Kuralı gözden **geçir sayfasında** , kuralın ayarlarını gözden geçirin ve Kural **oluştur'a tıklayın**. Alıcılar ayarlara göre e-posta aracılığıyla olay bildirimleri almaya başlar.

Var olan bir kuralı düzenlemek için, kural listesinden kuralı seçin. Kural adının olduğu bölmede, **Kuralı düzenle'yi** seçin ve Temel **Bilgiler, Bildirim** ayarları ve **Alıcılar** sayfalarında **değişikliklerinizi** yapın.

Bir kuralı silmek için kural listesinden seçin. Kural adının olduğu bölmede Sil'i **seçin**.

## <a name="see-also"></a>Ayrıca bkz.
- [Olaylara genel bakış](incidents-overview.md)
- [Olayları önceliklendirme](incident-queue.md)
- [Olayları araştırma](investigate-incidents.md)
