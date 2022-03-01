---
title: Insider risk yönetimi Kullanıcılar panosu
description: Microsoft'ta Insider risk yönetimi Kullanıcılar panosu hakkında Microsoft 365
keywords: Microsoft 365, insider risk yönetimi, risk yönetimi, uyumluluk
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
ms.openlocfilehash: a690f007b05709b094edd0c9d72417715875dfaf
ms.sourcegitcommit: efb333ce0772265da91632110acba39acfbe0bde
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2021
ms.locfileid: "62997091"
---
# <a name="insider-risk-management-users-dashboard"></a>Insider risk yönetimi Kullanıcılar panosu

Kullanıcılar **panosu,** Insider risk yönetimi iş akışında önemli bir araçtır ve güvenlikçilerin ve analistlerin risk etkinliklerinin daha eksiksiz bir şekilde anlaşılmasına yardımcı olur. Bu panoda, insider risk yönetimi ilkeleri oluşturma ile Insider risk yönetimi durumlarını yönetme arasında yönetim  ihtiyaçlarını karşılamaya yönelik görünümler ve yönetim özellikleri bulunmaktadır.

Kullanıcılar Insider risk yönetimi ilkelerine eklendikten sonra, arka plan süreçleri otomatik olarak göstergeleri tetikleyen kullanıcı [etkinliklerini değerlendirir](insider-risk-management-settings.md#indicators). Göstergeleri tetikledikten sonra, kullanıcı etkinliklerine risk puanları atanır. Bu etkinliklerin bazıları insider risk uyarısına neden olabilir, ancak bazı etkinlikler en düşük risk puanı düzeyine karşılamaz ve insider risk uyarısı oluşturulmaz. Kullanıcılar **panosu,** bu tür göstergelere ve risk notlarına sahip kullanıcıların yanı sıra etkin insider risk uyarılarına sahip kullanıcıları görüntülemeye olanak sağlar.

Kullanıcılar panosunun kullanıcıları aşağıdaki senaryolarda nasıl görüntüle ilgili daha fazla bilgi edinebilirsiniz:

- Etkin Insider risk ilkesi uyarılarını olan kullanıcılar
- Olayları tetikleyen kullanıcılar
- Kullanıcılar ilkelere geçici olarak eklendi

## <a name="users-with-active-insider-risk-policy-alerts"></a>Etkin Insider risk ilkesi uyarılarını olan kullanıcılar

Kullanıcılar **panosu,** etkin Insider risk ilkesi uyarılarını olan tüm kullanıcıları otomatik olarak görüntüler. Uyarılara sahip bu kullanıcıların hem bir tetikleyici göstergesi hem de insider risk uyarısı oluşturma gereksinimlerini karşılayacak etkinlik riski puanı vardır. Bu kullanıcıların etkinlikleri, Kullanıcılar panosunda kullanıcı seçerek ve Kullanıcı etkinliği **sekmesine giderek** görüntülenir.

## <a name="users-with-triggering-events"></a>Olayları tetikleyen kullanıcılar

Kullanıcılar **panosunda** otomatik olarak, olayları tetikleyen tüm kullanıcılar görüntülenir, ancak bunun içinde bir insider risk uyarısı oluşturan bir etkinlik risk puanı yok. Örneğin, bu etkinlik tetikleyen bir etkinlik olduğu, ancak risk puanına sahip bir etkinlik olmadığını bildirdi. Bu kullanıcıların etkinlikleri, Kullanıcılar panosunda kullanıcı seçerek ve Kullanıcı etkinliği **sekmesine giderek** görüntülenir.

## <a name="users-added-temporarily-to-policies"></a>Kullanıcılar ilkelere geçici olarak eklendi

Kullanıcılar **panosu,** insider risk yönetimi iş akışının dışında sıra dışı bir etkinlik sonrasında Insider risk yönetimi ilkelerine eklenen kullanıcıları içerir. Kullanıcıları geçici olarak eklemek (İlkeler panosundan), gerekli bir bağlayıcı yapılandırılmasa bile, insider risk yönetimi ilkesi için kullanıcı etkinliğini puanlamaya başlamanın da bir yoludur.

Kullanıcı bir ilkeye el ile ekli olduğunda, önceki 90 gün için kullanıcı etkinlikleri puanlandı ve Kullanıcı etkinliği zaman **çizelgesine** eklenir. Örneğin, şu anda bir Insider risk ilkesine yönelik risk puanları atanmamış bir kullanıcınız var ve kullanıcının, kurum içinde hukuk departmanına bildirilen veri sızıntı etkinlikleri var. Hukuk departmanı, kullanıcı için yeni kısa vadeli izleme gereksinimlerini yapılandırmanizi önermektedir. Belirli bir süre boyunca (etkinleştirme penceresi *) Veri* sızıntıları ilkenize geçici olarak kullanıcı at atabilirsiniz. Olay gereksinimlerini tetikleyen kullanıcılardan feragati nedeniyle **,** geçici olarak eklenen tüm kullanıcılar Kullanıcılar panosunda görüntülenir.

> [!NOTE]
> El ile eklenen yeni kullanıcıların Kullanıcılar panosunda görünmesi birkaç **saat sürebilir**. Bu kullanıcıların önceki 90 günlük etkinliklerinin 24 saate kadar görüntülemesi daha sürebilir. El ile eklenen kullanıcıların etkinliklerini görüntülemek için, Kullanıcılar panosunda kullanıcı seçin  ve ayrıntılar **bölmesindeki** Kullanıcı etkinliği sekmesini açın.

Kullanıcı, Kullanıcılar panosundan otomatik **olarak kaldırılır** ve Etkinleştirme penceresinde tanımlanan süre sona erdiğinde puanlama sona  erer:

- Kullanıcı, ek tetikleyici olay veya Insider risk ilkesi uyarısına sahip değildir ve
- elle tanımlanmış Etkinleştirme **penceresi süresi genel** ilke Etkinleştirme penceresi süresinden **uzunsa** .

En **uzun süreli** Etkinleştirme penceresi ayarı, her zaman daha kısa **süreli Etkinleştirme penceresi** ayarını geçersiz kılar. Örneğin, etkinleştirme penceresini, tüm insider risk  ilkelerinize otomatik olarak uygulanan  insider risk yönetimi genel ayarlarının genel ilkeler sekmesindeki genel İlke zaman çerçeveleri sekmesinde yapılandırdınız.

Veri sızıntıları insider risk ilkenize  geçici olarak bir kullanıcı ekler ve bu kullanıcı için Etkinleştirme penceresi olarak 30 gün  tanımlarsınız. 15 **günlük** genel Etkinleştirme penceresi ayarı, geçici olarak eklenen kullanıcı için 30 günlük Etkinleştirme  penceresi ayarını tanımlayarak geçersiz kılınır. Geçici olarak eklenen kullanıcı Kullanıcılar **panosunda kalır** ve 30 gün boyunca ilkenin kapsamı içinde kalır.

Genel Etkinleştirme penceresi ayarının geçici olarak  eklenmiş bir kullanıcı için tanımlanan Etkinleştirme penceresi  ayarından daha uzun olduğu karşıt senaryoda **, genel Etkinleştirme** penceresi ayarı geçici olarak eklenen kullanıcının Etkinleştirme penceresi  ayarını geçersiz kılar. Geçici olarak eklenen kullanıcı Kullanıcılar panosunda kalır ve  genel Etkinleştirme penceresi ayarlarında tanımlanan gün sayısıyla ilgili **ilkenin kapsamı içinde** olur.

## <a name="view-user-information-on-the-users-dashboard"></a>Kullanıcılar panosunda kullanıcı bilgilerini görüntüleme

Kullanıcılar panosunda görüntülenen **her kullanıcıda** aşağıdaki bilgiler vardır:

- **Kullanıcılar**: Kullanıcının kullanıcı adı. Insider risk yönetimi için genel anonimleştirme ayarı etkinleştirildiyse, bu alan anonimleştirilmiştir.
- **Risk düzeyi**: Kullanıcının geçerli hesaplanan risk düzeyidir. Bu puan her 24 saatte bir hesaplanır ve kullanıcıyla ilişkili tüm etkin uyarılardan uyarı riski puanlarını kullanır. Yalnızca tetikleyen göstergeleri olan kullanıcılar için risk düzeyi sıfırdır.
- **Etkin uyarılar**: Tüm ilkeler için etkin uyarı sayısı.
- **Onaylandı ihlalleri**: Olay sayısı, kullanıcı için *onaylandı ilke ihlali* olarak çözülür.
- **Büyük**/harf: Kullanıcı için geçerli etkin durum.

Belirli bir kullanıcıyı hızla **bulmak için,** Kullanıcı panosunun sağ üst kısmında Ara'ya bakabilirsiniz. Kullanıcıları ararken, kullanıcı asıl adını (UPN) kullanabilirsiniz. Örneğin, kuruluşunda UPN'sı 'thidayah' olan 'Tiara Hidayah' adlı bir kullanıcı için arama geldiğinde, Arama'ya UPN'nin bir bölümünü veya 'bugün' girmeniz **gerekir**.

![Insider risk yönetimi kullanıcıları panosu.](../media/insider-risk-users-dashboard.png)

> [!NOTE]
> Kullanıcılar panosunda görüntülenen kullanıcı **sayısı, etkin** uyarıların hacmine ve eşleşen ilkelere bağlı olarak bazı durumlarda sınırlı olabilir. Etkin uyarıya sahip kullanıcılar **,** uyarılar oluşturulurken Kullanıcılar panosunda görüntülenir ve görüntülenen kullanıcı sayısı üst sayısına ulaşıldıklarında ender durumlarda da olabilir. Bu sınır gerçekleşirse, etkin uyarı alan ve görüntülenmeen kullanıcılar, mevcut kullanıcı uyarıları önceye göre sıralandı olarak Kullanıcılar panosuna eklenir.

## <a name="view-user-details"></a>Kullanıcı ayrıntılarını görüntüleme

Kullanıcının risk etkinliği hakkında daha fazla ayrıntı görüntülemek için, Kullanıcılar panosunda bir kullanıcıya çift tıklayarak kullanıcı ayrıntıları **bölmesini açın**. Ayrıntılar bölmesinde aşağıdaki bilgileri görüntüleyebilirsiniz:

- **Kullanıcı profili** sekmesi
  - **Ad ve başlık**: İlk oturumdan kullanıcının ad ve konum Azure Active Directory. Insider risk yönetimine yönelik genel anonimleştirme ayarı etkinleştirildiyse, bu kullanıcı alanları anonimleştirilir veya boş olur.
  - **Kullanıcı e-postası**: Kullanıcının e-posta adresi.
  - **Diğer** Ad: Kullanıcının ağ diğer adı.
  - **Kuruluş veya bölüm**: Kullanıcının kuruluş veya bölümü.

- **Kullanıcı etkinliği** sekmesi
  - **Son kullanıcı etkinliğinin** geçmişi: Son 180 gün içindeki kullanıcı etkinlikleri için hem tetikleyen göstergeleri hem de insider risk göstergelerini listeler. Insider risk göstergeleri ile ilgili tüm etkinlikler de puanlandı. Ancak etkinlikler, insider risk uyarısı oluştursa da oluşturmasa da bu durumla ilgili olarak puanlandırıldı. Gösterge örneklerini tetiklemek, kullanıcı için tarihin tarihi veya son zamanlanan çalışma tarihi olabilir. Insider risk göstergeleri, bir risk öğesine sahip olmak için belirlenen etkinliklerdir ve kullanıcının dahil olduğu ilkelerde tanımlanırlar. Etkinlik ve risk etkinlikleri, en son öğe en başta listelenmiş olarak listelenir.

## <a name="remove-users-from-in-scope-assignment-to-policies"></a>Kullanıcıları kapsam içinde atamadan ilkelere kaldırma

Insider risk yönetimi ilkelerde kullanıcının etkinliğine risk puanları atamayı durdurmanız gereken senaryolar olabilir. Kullanıcılar **pano sayfasındaki** **Kullanıcıları** kaldır'ı kullanarak, şu anda kapsamı açık olan tüm Insider risk yönetimi ilkelerinden bir veya daha fazla kullanıcının risk puanlarını atamayı durdurun. Bu eylem kullanıcıları genel ilke atamalarından (ilke yapılandırmasına kullanıcıları veya grupları eklerken) kaldırmaz, ancak yalnızca geçerli tetiklenen olayları tetikleyen ilkeler tarafından etkin işlemeden kullanıcıları kaldırır. Gelecekte kullanıcıların başka bir tetik olayı varsa, ilkelerden risk puanları otomatik olarak kullanıcılara yeniden atanacaktır. Bu kullanıcıyla ilgili mevcut uyarı veya durumlar kaldırılamaz.

> [!NOTE]
> Kullanıcının ilkeden kaldırılması birkaç dakika sürebilir. Tamamlandığında, kullanıcı artık Kullanıcılar sayfasında listelenmiyor olur. Kaldırılan kullanıcının etkin uyarıları veya örnekleri varsa, kullanıcı Kullanıcılar sayfasında kalır ve kullanıcının ayrıntıları, artık bir ilke kapsamında olmadığını gösterir.

Tüm Insider risk yönetimi ilkelarında kullanıcıları kapsam içi durumundan el ile kaldırmak için, aşağıdaki adımları tamamlayın:

1. Giriş [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin ve** Kullanıcılar **sekmesini** seçin.
2. Kullanıcılar **panosunda**, Insider risk yönetimi ilkeleri kapsamından kaldırmak istediğiniz kullanıcı veya kullanıcıları seçin.
3. Kullanıcıları **kaldır'ı seçin**.
4. Kullanıcı kaldır **bölmesinde Kaldır'ı** veya **İptal'i** **seçerek** değişiklikleri atabilirsiniz ve iletişim kutusunu kapatabilirsiniz.
5. Kullanıcı **kaldırmak** için onay bölmesinde Kaldır'ı seçin.

## <a name="run-automated-tasks-with-power-automate-flows-for-a-user"></a>Kullanıcı için otomatik görevleri Power Automate akışlarla çalıştırma

Önerilen güvenlik Power Automate kullanarak risk tahminleri ve analistleri şunları yapmak için hızlı bir şekilde işlem tamamlar:

- Insider risk ilkesine eklenen kullanıcıları bilgilendirme

Insider risk yönetimi kullanıcısı için Power Automate akışlarını çalıştırmak, yönetmek veya oluşturmak için:

1. Kullanıcı **eylemi araç** çubuğunda Otomatikleştir'i seçin.
2. Çalıştıracak Power Automate seçin ve ardından Akışı **çalıştır'ı seçin**.
3. Akış tamamlandıktan sonra Bitti'yi **seçin**.

Insider risk yönetimine Power Automate hakkında daha fazla bilgi edinmek için bkz[. Insider risk yönetimi ayarlarıyla çalışmaya başlama](insider-risk-management-settings.md#power-automate-flows-preview).
