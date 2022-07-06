---
title: Yasal tutma bildirimi oluşturma
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Yasal saklama bildirimleri göndermek, toplamak ve izlemek için eBulma (Premium) durumunda İletişim aracını kullanın.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: e97630c75c05412e22afa17daaa1897f8627adf1
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634687"
---
# <a name="create-a-legal-hold-notice"></a>Yasal tutma bildirimi oluşturma

Kuruluşlar, eKeşif (Premium) koruyucu iletişimlerini kullanarak, koruyucularla iletişim kurma konusunda iş akışlarını yönetebilir. İletişim aracı aracılığıyla, yasal ekipler yasal saklama bildirimlerini sistematik olarak gönderebilir, toplayabilir ve izleyebilir. Esnek oluşturma işlemi, ekiplerin saklama bildirimi iş akışını ve koruyuculara gönderilen bildirimlerdeki içeriği özelleştirmesine de olanak tanır.

![İletişim Sayfası.](../media/CommunicationPage.PNG)

Makalede, ayrı tutma bildirimi iş akışındaki adımlar özetlenmiştir.

## <a name="step-1-specify-communication-details"></a>1. Adım: İletişim ayrıntılarını belirtme

İlk adım, yasal tutma bildirimleri veya diğer koruyucu iletişimler için uygun ayrıntıları belirtmektir.

![İletişimi Adlandır sayfası.](../media/NameCommunication.PNG)

1. Microsoft Purview uyumluluk portalı, kuruluşunuzdaki servis taleplerinin listesini görüntülemek için **eBulma > Gelişmiş'e** gidin.

2. Bir servis talebi seçin, **İletişimler** sekmesine ve ardından **Yeni iletişim'e** tıklayın.

3. **İletişimi adlandır** sayfasında aşağıdaki iletişim ayarlarını belirtin.

    - **Ad**: İletişimin adıdır.

    - **Veren memur**: Açılan liste, kuruluşunuzda iletişim için veren memur olarak seçilebilen kullanıcıları görüntüler. Bekçilere gönderilen her iletişim, seçilen veren memur adına gönderilir. Açılan listede yer alan kullanıcıların listesi, davanın üyelerinden ve kuruluş genelindeki veren memurlardan oluşur. Bu veren memurlar bir eBulma Yöneticisi tarafından eklenir ve kuruluşunuzdaki tüm eBulma (Premium) olaylarında kullanılabilir. Daha fazla bilgi için bkz. [Veren memurları yönetme](advanced-ediscovery-issuing-officers.md).

    - **İletişim şablonunu seçin**: Açılan listede, eBulma (Premium) ayarları sayfasındaki İletişim kitaplığındaki şablonlar görüntülenir. Bir şablon seçerseniz, oluşturduğunuz bildirimin metni için başlangıç noktası olarak **portal içeriğini tanımla** bölümünde görüntülenir. Şablon seçmezseniz, bildirimi sıfırdan kendiniz oluşturmanız gerekir. İletişim şablonları hakkında daha fazla bilgi için bkz. [Koruyucu iletişim şablonlarını yönetme](advanced-ediscovery-communications-library.md).

4. **İleri**'ye tıklayın.

## <a name="step-2-define-the-portal-content"></a>2. Adım: Portal içeriğini tanımlama

Ardından, ayrı tutma bildiriminin içeriğini oluşturabilir ve ekleyebilirsiniz. **İletişim oluşturma** sihirbazının **Portal içeriğini tanımla** sayfasında, ayrı tutma bildiriminin içeriğini belirtin. Bu içerik, Verme, Yeniden Sorun, Anımsatıcı ve Yükseltme bildirimlerine otomatik olarak eklenir. Ayrıca bu içerik, koruyucunun Uyumluluk Portalı'nda görünür. İletişim kitaplığından bir şablon seçtiyseniz, bu şablon görüntülenir ve oluşturduğunuz bildirim için bir başlangıç noktası sağlar.

![Portal İçeriği sayfası.](../media/PortalContent.PNG)

Portal içeriğini oluşturmak için:

1. Portal içeriğinin metin kutusuna ayrı tutma bildiriminizi yazın (veya başka bir belgeden kesip yapıştırın). Önceki sihirbaz sayfasında bir iletişim şablonu seçtiyseniz, şablon görüntülenir. Şablon içeriğini gerektiği gibi düzenleyebilirsiniz.

2. Bildirimi özelleştirmek ve Koruyucu Uyumluluk Portalı'nı paylaşmak için bildiriminize birleştirme değişkenleri ekleyin.

3. **İleri**'ye tıklayın.

  > [!TIP]
  > Portal içeriğinin içeriğini ve biçimini özelleştirme hakkında daha fazla bilgi edinmek için bkz. [İletişim Düzenleyicisi'ni kullanma](using-communications-editor.md).

## <a name="step-3-set-the-required-notifications"></a>3. Adım: Gerekli bildirimleri ayarlama

Ayrı tutma bildiriminin içeriğini tanımladıktan sonra, bildirim işlemini gönderme ve yönetme ile ilgili iş akışlarını ayarlayabilirsiniz. Bildirimler, bildirim almak ve koruyucularla birlikte izlemek için gönderilen e-posta iletileridir. İletişime eklenen her koruyucu aynı bildirimi alır.

Ayrı tutma bildirimi ayarlamak ve göndermek için Verme, Yeniden Verme ve Yayın bildirimlerini eklemeniz gerekir.

### <a name="issuance-notification"></a>Verme bildirimi

İletişim oluşturulduktan sonra, Verme **Bildirimi** belirtilen Veren Yetkili tarafından başlatılır. Verme bildirimi, koruyucuya koruma yükümlülükleri hakkında bilgi vermek için gönderilen ilk iletişimdir.

Verme bildirimi oluşturmak için:

1. **Verme** kutucuğunda **Düzenle'ye** tıklayın.

2. Gerekirse **Bilgi** ve **Gizli** alanlarına başka servis talebi üyeleri veya personel ekleyin. Bu alanlara birden çok kullanıcı eklemek için, e-posta adreslerini noktalı virgülle ayırın.

3. Bildirim için **Konu** belirtin (gerekli).

4. Koruyucuya sağlamak istediğiniz içeriği veya ek yönergeleri belirtin (gerekli). 2. Adımda tanımladığınız portal içeriği verme bildiriminin sonuna eklenir.

5. **Kaydet**'e tıklayın.

### <a name="re-issuance-notification"></a>Re-Issuance bildirimi

Olay ilerledikçe, koruyucuların daha önce belirtilenden daha fazla veya daha az veriyi korumaları gerekebilir. Portal içeriğini güncelleştirdikten sonra, yeniden sağlama bildirimi gönderilir ve koruma yükümlülüklerinde yapılan değişiklikler konusunda koruyucuları uyarır.

Reissuance bildirimi oluşturmak için:

1. **Yeniden Gönder** kutucuğunda **Düzenle'ye** tıklayın.

2. Gerekirse **Bilgi** ve **Gizli** alanlarına başka servis talebi üyeleri veya personel ekleyin. Bu alanlara birden çok kullanıcı eklemek için, e-posta adreslerini noktalı virgülle ayırın.

3. Bildirim için **Konu** belirtin (gerekli).

4. Koruyucuya sağlamak istediğiniz içeriği veya ek yönergeleri belirtin (gerekli). 2. Adımda tanımladığınız portal içeriği, yeniden verme bildiriminin sonuna eklenir.

5. **Kaydet**'e tıklayın.

> [!NOTE]
> Portal içeriği değiştirilirse (**İletişimi düzenle** sihirbazının **Portal İçeriğini Tanımla** sayfasında), yeniden verme bildirimi bildirime atanan tüm koruyuculara otomatik olarak gönderilir. Bildirim gönderildikten sonra, koruyuculardan ayrı tutma bildirimini yeniden onaylamaları istenir. Herhangi bir anımsatıcı veya yükseltme iş akışı ayarladıysanız bunlar da yeniden başlatılır. Diğer olay yönetimi olaylarının iletişimleri tetiklediğini hakkında daha fazla bilgi için bkz. [Bildirimleri tetikleyen olaylar](#events-that-trigger-notifications).

### <a name="release-notification"></a>Yayın bildirimi

Bir sorun çözüldükten sonra veya bir koruyucu artık içeriğin korunmasına tabi değilse, koruyucuyu bir davadan serbest bırakabilirsiniz. Koruyucuya daha önce bir ayrı tutma bildirimi verildiyse, yayın bildirimi, koruyucuları yükümlülüklerinden serbest bırakıldıklarını bildirmek için kullanılabilir.

Yayın bildirimi oluşturmak için:

1. **Yayın** kutucuğunda **Düzenle'ye** tıklayın.

2. Gerekirse **Bilgi** ve **Gizli** alanlarına başka servis talebi üyeleri veya personel ekleyin. Bu alanlara birden çok kullanıcı eklemek için, e-posta adreslerini noktalı virgülle ayırın.

3. Bildirim için **Konu** belirtin (gerekli).

4. Koruyucuya sağlamak istediğiniz içeriği veya ek yönergeleri belirtin (gerekli).

5. **Kaydet'e** tıklayın ve sonraki adıma geçin.

## <a name="optional-step-4-set-the-optional-notifications"></a>(İsteğe bağlı) 4. Adım: İsteğe bağlı bildirimleri ayarlama

İsteğe bağlı olarak, otomatik anımsatıcı ve yükseltme bildirimleri oluşturup zamanlayarak yanıt vermeyen koruyucularla takip için iş akışını basitleştirebilirsiniz.

![Anımsatıcı/Yükseltme sayfası.](../media/ReminderEscalations.PNG)

### <a name="reminders"></a>Hatırlatmalar

Ayrı tutma bildirimi gönderdikten sonra, anımsatıcı iş akışı tanımlayarak yanıt vermeyen koruyucularla takip edebilirsiniz.

Anımsatıcıları zamanlamak için:

1. **Anımsatıcı** kutucuğunda **Düzenle'ye** tıklayın.

2. **Durum** iki durumlu düğmesini (gerekli) açarak **Anımsatıcı** iş akışını etkinleştirin.

3. **Anımsatıcı aralığını belirtin (gün cinsinden)** (gerekli). Bu, ilk ve takip anımsatıcı bildirimlerini göndermeden önce bekleyebileceğiniz gün sayısıdır. Örneğin, anımsatıcı aralığını yedi gün olarak ayarlarsanız, ilk anımsatıcı bekletme bildirimi ilk kez verildikten yedi gün sonra gönderilir. Sonraki tüm anımsatıcılar da yedi günde bir gönderilir.

4. **Anımsatıcı sayısını** (gerekli) belirtin. Bu alan, yanıt vermeyen koruyuculara gönderilecek anımsatıcı sayısını belirtir. Örneğin, anımsatıcı sayısını 3 olarak ayarlarsanız, bir koruyucu en fazla üç anımsatıcı alır. Bir koruyucu saklama bildirimini kabul ettikten sonra, anımsatıcılar artık söz konusu kullanıcıya gönderilmez.

5. Bildirim için **Konu** belirtin (gerekli).

6. Koruyucuya sağlamak istediğiniz içeriği veya ek yönergeleri belirtin (gerekli). 2. Adımda tanımladığınız portal içeriği anımsatıcı bildiriminin sonuna eklenir.

7. **Kaydet'e** tıklayın ve sonraki adıma geçin.

### <a name="escalations"></a>Escalations

Bazı durumlarda yanıt vermeyen koruyucularla takip etmek için ek yöntemlere ihtiyacınız olabilir. Bir koruyucu, belirtilen sayıda anımsatıcı aldıktan sonra ayrı tutma bildirimini kabul etmezse, yasal ekip koruyucuya ve yöneticisine otomatik olarak bir yükseltme bildirimi göndermek için bir iş akışı belirtebilir.

Yükseltmeleri zamanlamak için:

1. **Yükseltme** kutucuğunda **Düzenle'ye** tıklayın.

2. **Durum** iki durumlu düğmesini açarak **Yükseltme** iş akışını etkinleştirin.

3. **İlerletme aralığını belirtin (gün cinsinden)** (gerekli).

4. **Yükseltme sayısını** (gerekli) belirtin. Bu alan, yanıt vermeyen koruyuculara gönderilecek yükseltme sayısını belirtir. Örneğin, yükseltme sayısını 3 olarak ayarlarsanız, koruyucuya ve yöneticisine en fazla üç kez bir yükseltme bildirimi gönderilir. Bir koruyucu bekletme bildirimini kabul ettikten sonra, yükseltmeler artık gönderilmez.

5. Bildirim için **Konu** belirtin (gerekli).

6. Koruyucuya sağlamak istediğiniz içeriği veya ek yönergeleri belirtin (gerekli). 2. Adımda tanımladığınız portal içeriği, yükseltme bildiriminin sonuna eklenir.

7. **Kaydet'e** tıklayın ve sonraki adıma geçin.

## <a name="step-5-assign-custodians-to-receive-notifications"></a>5. Adım: Bildirim almak için koruyucu atama

Bildirimlerin içeriğini sonlandırdıktan sonra bildirim göndermek istediğiniz koruyucuları seçin.

![Koruyucular sayfasını seçin.](../media/SelectCustodians.PNG)

Koruyucu eklemek için:

1. Adlarının yanındaki onay kutusuna tıklayarak iletişim için koruyucuları atayın.

    İletişim oluşturulduktan sonra, bildirim iş akışı seçilen koruyuculara otomatik olarak uygulanır.

2. İletişim ayarlarını ve ayrıntılarını gözden geçirmek için **İleri'ye** tıklayın.

> [!NOTE]
> Yalnızca servis talebine eklenmiş ve servis talebi içinde başka bir bildirim gönderilmemiş olan koruyucuları ekleyebilirsiniz.

## <a name="step-6-review-settings"></a>6. Adım: Ayarları gözden geçirme

İletişimi tamamlamak için ayarları gözden geçirip **Gönder'e** tıkladıktan sonra, sistem verme bildirimini göndererek iletişim iş akışını otomatik olarak başlatır.

## <a name="events-that-trigger-notifications"></a>Bildirimleri tetikleyen olaylar

Aşağıdaki tabloda, olay yönetimi sürecinde, koruyuculara farklı bildirim türleri gönderildiğinde tetiklenen olaylar açıklanmaktadır.

|İletişim türü|Tetikleyici |
|:---------|:---------|
|Verme bildirimleri|Bildirimin ilk oluşturulması. Ayrı tutma bildirimini el ile de yeniden gönderebilirsiniz. |
|Yeniden verme bildirimleri|**İletişimi düzenle** sihirbazının **Portal İçeriğini Tanımla sayfasındaki portal** içeriğini güncelleştirme.|
|Sürüm bildirimleri|Koruyucu davadan serbest bırakıldı.|
|Hatırlatmalar|Anımsatıcı için yapılandırılan anımsatıcı aralığı ve sayısı.|
|Escalations|Yükseltme için yapılandırılan anımsatıcıların aralığı ve sayısı.|
|||
