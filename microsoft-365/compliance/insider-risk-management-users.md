---
title: Insider risk yönetimi Kullanıcılar panosu
description: Microsoft Purview'da insider risk yönetimi Kullanıcılar panosu hakkında bilgi edinin
keywords: Microsoft 365, Microsoft Purview, insider riski, risk yönetimi, uyumluluk
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 05adeb86c5e4da5119a5aae184721ec667564b49
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629497"
---
# <a name="insider-risk-management-users-dashboard"></a>Insider risk yönetimi Kullanıcılar panosu

**Kullanıcılar panosu**, insider risk yönetimi iş akışında önemli bir araçtır ve araştırmacıların ve analistlerin risk etkinliklerini daha eksiksiz bir şekilde anlamalarına yardımcı olur. Bu pano, iç risk yönetimi ilkeleri oluşturma ve insider risk yönetimi olaylarını yönetme arasında yönetim gereksinimlerini karşılamak için görünümler ve yönetim özellikleri sunar.

Kullanıcılar insider risk yönetimi ilkelerine eklendikten sonra, arka plan işlemleri [gösterge tetikleme](insider-risk-management-settings.md#indicators) için kullanıcı etkinliklerini otomatik olarak değerlendirir. Tetikleme göstergeleri mevcut olduktan sonra, kullanıcı etkinliklerine risk puanları atanır. Bu etkinliklerden bazıları içeriden risk uyarısına neden olabilir, ancak bazı etkinlikler minimum risk puanı düzeyini karşılamayabilir ve insider risk uyarısı oluşturulmaz. **Kullanıcılar panosu**, bu tür göstergelere ve risk puanlarına sahip kullanıcıların yanı sıra etkin insider risk uyarılarına sahip kullanıcıları görüntülemenizi sağlar.

Aşağıdaki senaryolarda Kullanıcılar panosunun kullanıcıları nasıl görüntülediği hakkında daha fazla bilgi edinin:

- Etkin insider risk ilkesi uyarıları olan kullanıcılar
- Olayları tetikleyen kullanıcılar
- İlkelere geçici olarak eklenen kullanıcılar

## <a name="users-with-active-insider-risk-policy-alerts"></a>Etkin insider risk ilkesi uyarıları olan kullanıcılar

**Kullanıcılar panosu**, etkin insider risk ilkesi uyarılarına sahip tüm kullanıcıları otomatik olarak görüntüler. Uyarıları olan bu kullanıcıların hem tetikleyici göstergesi hem de insider risk uyarısı oluşturma gereksinimlerini karşılayan bir etkinlik riski puanı vardır. Bu kullanıcılar için etkinlikler, **Kullanıcılar panosunda** kullanıcı seçilerek ve **Kullanıcı etkinliği** sekmesine giderek görüntülenir.

## <a name="users-with-triggering-events"></a>Olayları tetikleyen kullanıcılar

**Kullanıcılar panosu** olayları tetikleyen tüm kullanıcıları otomatik olarak görüntüler, ancak bu, içeriden risk uyarısı oluşturacak bir etkinlik riski puanına sahip değildir. Örneğin, bildirilen bir istifa tarihi olan bir kullanıcı görüntülenir çünkü bu etkinlik tetikleyici bir olaydır ancak risk puanı olan bir etkinlik değildir. Bu kullanıcılar için etkinlikler, **Kullanıcılar panosunda** kullanıcı seçilerek ve **Kullanıcı etkinliği** sekmesine giderek görüntülenir.

## <a name="users-added-temporarily-to-policies"></a>İlkelere geçici olarak eklenen kullanıcılar

**Kullanıcılar panosu**, insider risk yönetimi iş akışının dışında olağan dışı bir olay sonrasında insider risk yönetimi ilkelerine eklenen kullanıcıları içerir. Kullanıcıları geçici olarak eklemek (İlkeler panosundan), gerekli bağlayıcı yapılandırılmamış olsa bile ilkeyi test etmek için bir iç risk yönetimi ilkesi için kullanıcı etkinliğini puanlamaya başlamanın bir yoludur.

Kullanıcı bir ilkeye el ile eklendiğinde, önceki 90 güne ilişkin kullanıcı etkinlikleri puanlanır ve **Kullanıcı etkinliği** zaman çizelgesine eklenir. Örneğin, şu anda bir iç risk ilkesi için risk puanları atanmayan bir kullanıcınız var ve kullanıcının kuruluşunuzdaki hukuk departmanına bildirilen veri sızıntısı etkinlikleri var. Hukuk departmanı, kullanıcı için yeni kısa vadeli izleme gereksinimlerini yapılandırmanızı önerir. Kullanıcıyı belirlenen bir süre boyunca (etkinleştirme penceresi) *Veri sızıntıları* ilkenize geçici olarak atayabilirsiniz. Olay gereksinimleri tetiklendiğinden geçici olarak eklenen tüm kullanıcılar **Kullanıcılar panosunda** görüntülenir.

> [!NOTE]
> El ile eklenen yeni kullanıcıların **Kullanıcılar panosunda** görünmesi birkaç saat sürebilir. Bu kullanıcılar için önceki 90 güne ilişkin etkinliklerin görüntülenmesi 24 saat kadar sürebilir. El ile eklenen kullanıcıların etkinliklerini görüntülemek için **Kullanıcılar panosunda** kullanıcıyı seçin ve ayrıntılar bölmesindeki **Kullanıcı etkinliği** sekmesini açın.

Kullanıcı Kullanıcılar **panosundan** otomatik olarak kaldırılır ve **Aşağıdaki durumlarda Etkinleştirme penceresinde** tanımlanan süre dolduğunda puanlama durur:

- kullanıcının ek tetikleyici olayları veya insider risk ilkesi uyarıları yoktur ve
- el ile tanımlanan **Etkinleştirme penceresi** süresi genel ilke **Etkinleştirme penceresi** süresinden uzunsa.

En uzun süreye sahip **Etkinleştirme penceresi** ayarı her zaman **Etkinleştirme penceresi** ayarını daha kısa bir süreyle geçersiz kılar. Örneğin, insider risk yönetimi genel ayarlarındaki genel **İlke zaman çerçeveleri** sekmesindeki **Etkinleştirme penceresini** 15 gün boyunca yapılandırmış ve bu pencere tüm insider risk ilkelerinize otomatik olarak uygulanır.

*Veri sızıntıları* insider risk ilkenize geçici olarak bir kullanıcı ekler ve bu kullanıcı için **Etkinleştirme penceresi** olarak 30 gün tanımlarsınız. Geçici olarak eklenen kullanıcı için 30 günlük **Etkinleştirme penceresi** ayarı tanımlanarak 15 günlük genel Etkinleştirme **penceresi** ayarı geçersiz kılınmış olur. Geçici olarak eklenen kullanıcı **Kullanıcılar panosunda** kalır ve ilke kapsamında 30 gün boyunca kalır.

Genel **Etkinleştirme penceresi** ayarının geçici olarak eklenen bir kullanıcı için tanımlanan **Etkinleştirme penceresi** ayarından daha uzun olduğu ters senaryoda, genel **Etkinleştirme penceresi** ayarı geçici olarak eklenen kullanıcının **Etkinleştirme penceresi** ayarını geçersiz kılar. Geçici olarak eklenen kullanıcı **Kullanıcılar panosunda** kalır ve genel **Etkinleştirme penceresi** ayarlarında tanımlanan gün sayısı için ilke kapsamında olur.

## <a name="view-user-information-on-the-users-dashboard"></a>Kullanıcılar panosunda kullanıcı bilgilerini görüntüleme

**Kullanıcılar panosunda** görüntülenen her kullanıcı aşağıdaki bilgilere sahiptir:

- **Kullanıcılar**: Kullanıcının kullanıcı adı. Insider risk yönetimi için genel anonimleştirme ayarı etkinse bu alan anonimleştirilir.
- **Risk düzeyi**: Kullanıcının geçerli hesaplanan risk düzeyi. Bu puan her 24 saatte bir hesaplanır ve kullanıcıyla ilişkili tüm etkin uyarılardan alınan uyarı riski puanlarını kullanır. Yalnızca tetikleyici göstergeleri olan kullanıcılar için risk düzeyi sıfırdır.
- **Etkin uyarılar**: Tüm ilkeler için etkin uyarıların sayısı.
- **Onaylanan ihlaller**: Kullanıcı için *onaylanan ilke ihlali olarak çözümlenen* servis talebi sayısı.
- **Büyük/küçük harf**: Kullanıcı için geçerli etkin durum.

Belirli bir kullanıcıyı hızla bulmak için Kullanıcı panosunun sağ üst kısmındaki **Ara'yı** kullanın. Kullanıcıları ararken kullanıcı asıl adını (UPN) kullanmanız gerekir. Örneğin, kuruluşunuzda UPN'si 'thidayah' olan 'Tiara Hidayah' adlı bir kullanıcıyı ararken, **Arama'ya** 'thidayah' veya UPN'nin bir bölümünü girersiniz.

![Insider risk yönetimi kullanıcıları panosu.](../media/insider-risk-users-dashboard.png)

> [!NOTE]
> **Kullanıcılar panosunda** görüntülenen kullanıcı sayısı, etkin uyarıların hacmine ve eşleşen ilkelere bağlı olarak bazı durumlarda sınırlı olabilir. Etkin uyarıları olan kullanıcılar, uyarılar oluşturulurken **Kullanıcılar panosunda** görüntülenir ve görüntülenen kullanıcı sayısı üst sınırına ulaşıldığında nadir durumlar olabilir. Bu sınır gerçekleşirse, mevcut kullanıcı uyarıları önceliklendirildikçe etkin uyarıları görüntülenmeyen kullanıcılar **Kullanıcılar panosuna** eklenir.

## <a name="view-user-details"></a>Kullanıcı ayrıntılarını görüntüleme

Bir kullanıcının risk etkinliği hakkında daha fazla ayrıntı görüntülemek için Kullanıcılar **panosunda** bir kullanıcıya çift tıklayarak kullanıcı ayrıntıları bölmesini açın. Ayrıntılar bölmesinde aşağıdaki bilgileri görüntüleyebilirsiniz:

- **Kullanıcı profili** sekmesi
  - **Ad ve başlık**: Azure Active Directory'den kullanıcının adı ve konum başlığı. Insider risk yönetimi için genel anonimleştirme ayarı etkinse bu kullanıcı alanları anonimleştirilir veya boş olur.
  - **Kullanıcı e-postası**: Kullanıcının e-posta adresi.
  - **Diğer ad**: Kullanıcının ağ diğer adı.
  - **Kuruluş veya departman**: Kullanıcının kuruluşu veya bölümü.

- **Kullanıcı etkinliği** sekmesi
  - **Son kullanıcı etkinliğinin geçmişi**: Son 180 güne kadar olan kullanıcı etkinlikleri için hem tetikleme göstergelerini hem de iç risk göstergelerini listeler. Insider risk göstergeleriyle ilgili tüm etkinlikler de puanlanmıştır, ancak etkinlikler insider risk uyarısı oluşturmuş veya oluşturmamış olabilir. Gösterge örneklerini tetikleme, bir istifa tarihi veya kullanıcının son zamanlanmış çalışma tarihi olabilir. Insider risk göstergeleri, bir risk öğesine sahip olduğu belirlenen etkinliklerdir ve kullanıcının dahil olduğu ilkelerde tanımlanır. Olay ve risk etkinlikleri, en son öğe listelenmiş olarak listelenir.

## <a name="remove-users-from-in-scope-assignment-to-policies"></a>Kullanıcıları kapsam içi ilke atamasından kaldırma

Bir kullanıcının insider risk yönetimi ilkelerindeki etkinliğine risk puanları atamayı durdurmanız gereken senaryolar olabilir. Şu anda kapsam içinde oldukları tüm şirket içi risk yönetimi ilkelerinden bir veya daha fazla kullanıcıya risk puanı atamayı durdurmak için **Kullanıcılar panosu** sayfasında **Kullanıcıları kaldır'ı** kullanın. Bu eylem, kullanıcıları genel ilke atamasından kaldırmaz (bir ilke yapılandırmasına kullanıcı veya grup eklediğinizde), yalnızca geçerli tetikleyici olaylarından sonra kullanıcıları ilkeler tarafından etkin işlemeden kaldırır. Gelecekte kullanıcıların başka bir tetikleyici olayı varsa, ilkelerden alınan risk puanları otomatik olarak kullanıcılara yeniden atanmaya başlar. Bu kullanıcı için mevcut uyarılar veya servis talepleri kaldırılmaz.

> [!NOTE]
> Bir kullanıcının ilkeden kaldırılması birkaç dakika sürebilir. İşlem tamamlandıktan sonra kullanıcı artık Kullanıcılar sayfasında listelenmez. Kaldırılan kullanıcının etkin uyarıları veya durumları varsa, kullanıcı Kullanıcılar sayfasında kalır ve kullanıcının ayrıntıları artık bir ilke kapsamında olmadığını gösterir.

Tüm insider risk yönetimi ilkelerinde kullanıcıları kapsam içi durumdan el ile kaldırmak için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **Kullanıcılar** sekmesini seçin.
2. **Kullanıcılar panosunda**, şirket içi risk yönetimi ilkeleri kapsamından kaldırmak istediğiniz kullanıcıyı veya kullanıcıları seçin.
3. **Kullanıcıları kaldır'ı** seçin.
4. **Kullanıcı kaldır** bölmesinde **Kaldır'ı** veya **İptal'i** seçerek değişiklikleri atıp iletişim kutusunu kapatın.
5. Kullanıcıyı kaldırmak için onay bölmesinde **Kaldır'ı** seçin.

## <a name="run-automated-tasks-with-power-automate-flows-for-a-user"></a>Kullanıcı için Power Automate akışlarıyla otomatik görevleri çalıştırma

Önerilen Power Automate akışlarını kullanarak risk araştırmacıları ve analistler aşağıdaki işlemleri hızla gerçekleştirebilir:

- Insider risk ilkesine eklendiklerinde kullanıcılara bildirme

Insider risk yönetimi kullanıcısı için Power Automate akışlarını çalıştırmak, yönetmek veya oluşturmak için:

1. Kullanıcı eylem araç çubuğunda **Otomatikleştir'i** seçin.
2. Çalıştırılacak Power Automate akışını ve ardından **Akışı çalıştır'ı** seçin.
3. Akış tamamlandıktan sonra **Bitti'yi** seçin.

Insider risk yönetimi için Power Automate akışları hakkında daha fazla bilgi edinmek için bkz. [Insider risk yönetimi ayarlarını kullanmaya başlama](insider-risk-management-settings.md#power-automate-flows-preview).
