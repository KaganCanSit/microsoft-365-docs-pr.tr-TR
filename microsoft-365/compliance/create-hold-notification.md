---
title: Yasal tutma bildirimi oluşturma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Yasal tutma bildirimlerini göndermek, Advanced eDiscovery ve izlemek için İletişim aracını bir olayda kullanın.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 5c0bda35ffe2547e1c30b4bbf0a6c7d0d0563b7b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315671"
---
# <a name="create-a-legal-hold-notice"></a>Yasal tutma bildirimi oluşturma

Kuruluşlar Advanced eDiscovery custo custodians ile iletişim kurma çevresinde iş akışlarını yönetebilir. İletişim aracı aracılığıyla, yasal ekipler yasal tutma bildirimlerini sistematik olarak gönderebilir, toplayabilirsiniz ve izleyebilir. Esnek oluşturma işlemi, ekiplerin tutma bildirimi iş akışını ve koruyuculara gönderilen bildirimlerde yer alan içeriği özelleştirmelerine de olanak sağlar.

![İletişim Sayfası.](../media/CommunicationPage.PNG)

Bu makalede, bildirim iş akışında tutma adımları ana hatlarıyla açıklanmıştır.

## <a name="step-1-specify-communication-details"></a>1. Adım: İletişim ayrıntılarını belirtme

İlk adım, yasal tutma bildirimlerini veya diğer koruyucu iletişimleri için uygun ayrıntıları belirtmektir.

![Ad İletişimi sayfası.](../media/NameCommunication.PNG)

1. Gelişmiş Microsoft 365 uyumluluk merkezi, **eBulma > Gelişmiş'e** gidip kurum durumdaki vakaların listesini görüntüleniyor.

2. Bir vaka seçin, İletişim **sekmesine tıklayın** ve sonra da Yeni **iletişim'e tıklayın**.

3. Ad **iletişim sayfasında** aşağıdaki iletişim ayarlarını belirtin.

    - **Ad**: Bu, iletişimin adıdır.

    - **Çalışan:** Açılan listede, kuruluşta iletişim için yardımcı olacak kişi olarak seçilecek kullanıcılar görüntülenir. Özel kişi adına gönderilen her iletişim, seçtiğiniz sorumlu kişi adına gönderilir. Açılan liste kullanıcıların listesi, davanın üyelerinden ve kuruluş genelindeki çalışanlardan oluşur. Bu teslim görevlileri eBulma Yöneticisi tarafından eklenir ve Advanced eDiscovery her durumda kullanılabilir. Daha fazla bilgi için bkz [. Görevlileri yönetme](advanced-ediscovery-issuing-officers.md).

    - **İletişim şablonunu seçin**: Açılan listede, iletişim kitaplığında yer alan şablonlar, iletişim Advanced eDiscovery görüntülenir. Bir şablon seçmeniz, portal içeriğini oluşturmakta olduğunu bildirimin metni  için bir başlangıç noktası olarak tanımlansın'da görüntülenir. Bir şablon seçerek, bu bildirimi sıfırdan kendiniz oluşturmanız gerekir. İletişim şablonları hakkında daha fazla bilgi için bkz. [Özel iletişim şablonlarını yönetme](advanced-ediscovery-communications-library.md).

4. **İleri**'ye tıklayın.

## <a name="step-2-define-the-portal-content"></a>2. Adım: Portal içeriğini tanımlama

Ardından, tutma bildirimini oluşturabilir ve içeriğini  eklersiniz. İletişim **oluştur sihirbazının Portal** **içeriğini tanımla sayfasında** , tutma bildiriminin içeriğini belirtin. Bu içerik, Otomatik olarak Verme, Yeniden Sorun, Anımsatıcı ve İlerlama bildirimlerini ekler. Ayrıca, bu içerik özel uygulamanın Uyumluluk Portalı'nda görünür. İletişim kitaplığından bir şablon seçtiysiniz, bu şablon görüntülenir ve oluşturmakta olduğunuz bildirim için bir başlangıç noktası sağlar.

![Portal İçeriği sayfası.](../media/PortalContent.PNG)

Portal içeriğini oluşturmak için:

1. Portal içeriğine yönelik metin kutusuna basılı tutma bildiriminizi yazın (veya başka bir belgeden kesip yapıştırın). Önceki sihirbaz sayfasında bir iletişim şablonu seçtiysiniz, şablon görüntülenir. Şablon içeriğini gereken şekilde düzenleyebilirsiniz.

2. Bildirimi özelleştirmek ve Custo bir Uyumluluk Portalı'nın paylaşımı için bildiriminize birleştirme değişkenleri  eklersiniz.

3. **İleri**'ye tıklayın.

  > [!TIP]
  > Portal içeriğinin içeriğini ve biçimini özelleştirme hakkında daha fazla bilgi edinmek için bkz [. İletişim Düzenleyicisi'ni kullanma](using-communications-editor.md).

## <a name="step-3-set-the-required-notifications"></a>3. Adım: Gerekli bildirimleri ayarlama

Tutma bildiriminin içeriğini tanımdikten sonra, bildirim işlemini gönderme ve yönetme işlemleriyle ilgili iş akışlarını kurabilirsiniz. Bildirimler, koruyucuları bildirmek ve takip etmek için gönderilen e-posta iletileridir. İletişime eklenen her custoomi aynı bildirimi alır.

Bir basılı tutma bildirimi ayarlamak ve göndermek için Yayınla, Yeniden Verme ve Sürüm bildirimlerini de dahil etmek gerekir.

### <a name="issuance-notification"></a>Verme bildirimi

İletişim oluşturulduktan sonra, **Uyarı Bildirimi** belirtilen Uyarı Görevlisi tarafından başlatılır. Verme bildirimi, koruyucuların saklama yükümlülükleri konusunda bilgilendirilmesi için koruyucuya gönderilen ilk iletişimdir.

Bir verme bildirimi oluşturmak için:

1. Verme **kutucuğunun** altında Düzenle'ye **tıklayın**.

2. Gerekirse Bilgi ve Gizli alanlarına ek vaka üyeleri **veya** **personeli** ekleyin. Bu alanlara birden çok kullanıcı eklemek için, e-posta adreslerini noktalı virgülle birbirinden ayırabilirsiniz.

3. Bildirim **için Konu** belirtin (gerekli).

4. Özel belgeye sağlamak istediğiniz içeriği veya ek yönergeleri belirtin (gerekli). 2. Adımda tanımlandığı portal içeriği, yayın bildiriminin sonuna eklenir.

5. **Kaydet**'e tıklayın.

### <a name="re-issuance-notification"></a>Re-Issuance bildirimi

Durum ilerledikçe, daha önce belirtildiği gibi ek veya az verinin korunması için koruyucular gerekebilir. Portal içeriğini güncelleştirdikten sonra, yeniden verme bildirimi gönderilir ve yasal yükümlülüklerinde yapılan değişiklikler konusunda koruyucuları uyararak bu konuda uyarabilirsiniz.

Yeniden verme bildirimi oluşturmak için:

1. Yeniden **Yayınla kutucuğunun** altında Düzenle'ye **tıklayın**.

2. Gerekirse Bilgi ve Gizli alanlarına ek vaka üyeleri **veya** **personeli** ekleyin. Bu alanlara birden çok kullanıcı eklemek için, e-posta adreslerini noktalı virgülle birbirinden ayırabilirsiniz.

3. Bildirim **için Konu** belirtin (gerekli).

4. Özel belgeye sağlamak istediğiniz içeriği veya ek yönergeleri belirtin (gerekli). 2. Adımda tanımlandığı portal içeriği, yeniden verme bildiriminin sonuna eklenir.

5. **Kaydet**'e tıklayın.

> [!NOTE]
> Portal içeriği değiştirilirse (İletişimi düzenle sihirbazının **Portal** İçeriğini Tanımla sayfasında), yeniden gönderme bildirimi bildirime atanan tüm koruyuculara otomatik olarak gönderilir. Bildirim gönderildikten sonra, koruyucuların tutma bildirimlerini yeniden kabulleri istenecek. Herhangi bir anımsatıcı veya yükseltme iş akışı ayardınız, bunlar da yeniden başlar. Diğer olay yönetimi olaylarını tetikleyen iletişimler hakkında daha fazla bilgi için bkz. [Bildirimleri tetikleyen olaylar](#events-that-trigger-notifications).

### <a name="release-notification"></a>Sürüm bildirimi

Bir sorun çözüldükten sonra veya custo custo custo bir vakadan çıkarabilirsiniz. Custo custo her zaman bir tutma bildirimi verildiyse, sürüm bildirimi koruyucuları yükümlülüklerinden çıkarıldıklarına karşı uyarı vermek için kullanılabilir.

Sürüm bildirimi oluşturmak için:

1. Sürüm **kutucuğunun** altında Düzenle'ye **tıklayın**.

2. Gerekirse Bilgi ve Gizli alanlarına ek vaka üyeleri **veya** **personeli** ekleyin. Bu alanlara birden çok kullanıcı eklemek için, e-posta adreslerini noktalı virgülle birbirinden ayırabilirsiniz.

3. Bildirim **için Konu** belirtin (gerekli).

4. Özel belgeye sağlamak istediğiniz içeriği veya ek yönergeleri belirtin (gerekli).

5. **Kaydet'e** tıklayın ve bir sonraki adıma geçin.

## <a name="optional-step-4-set-the-optional-notifications"></a>(İsteğe bağlı) 4. Adım: İsteğe bağlı bildirimleri ayarlama

İsteğe bağlı olarak, otomatik anımsatıcı ve yükseltme bildirimleri oluşturarak ve zamanlayarak yanıtsız koruyucularla takip süreci için iş akışını basitleştirebilirsiniz.

![Anımsatıcı/İlerlama sayfası.](../media/ReminderEscalations.PNG)

### <a name="reminders"></a>Anımsatıcılar

Bir tutma bildirimi gönderdikten sonra, bir anımsatıcı iş akışı tanımlayarak yanıt vermeyen koruyucularla devam edebilirsiniz.

Anımsatıcıları zaman yapmak için:

1. **Anımsatıcı kutucuğunun** içinde Düzenle'ye **tıklayın**.

2. Durum iki **durumlu** düğmeyi (gerekli **) etkinleştirerek Anımsatıcı** iş akışını etkinleştirin.

3. **Anımsatıcı aralığını (gün olarak)** (gerekli) belirtin. Bu, ilk ve takip anımsatıcı bildirimlerini göndermeden önce beklemenin gün sayısıdır. Örneğin, anımsatıcı aralığını yedi gün olarak ayarsanız, ilk anımsatıcı, tutma bildirimi gönderildikten yedi gün sonra gönderilir. Bunu izleyen tüm anımsatıcılar her yedi günde bir gönderilir.

4. **Anımsatıcı sayısını belirtin** (gerekli). Bu alanda, yanıtsız koruyuculara kaç anımsatıcı gönder göndericisi olduğu belirtir. Örneğin, anımsatıcı sayısını 3 olarak ayarsanız, koruyucu en çok üç anımsatıcı alır. Bir koruyucu tutma bildirimini kabul edildikten sonra, anımsatıcılar artık o kullanıcıya gönderilmez.

5. Bildirim **için Konu** belirtin (gerekli).

6. Özel belgeye sağlamak istediğiniz içeriği veya ek yönergeleri belirtin (gerekli). 2. Adımda tanımlandığı portal içeriği, anımsatıcı bildiriminin sonuna eklenir.

7. **Kaydet'e** tıklayın ve bir sonraki adıma geçin.

### <a name="escalations"></a>Yükseltmeler

Bazı durumlarda, yanıt vermeyen koruyucularla devam etmek için ek yöntemlere ihtiyacınız olabilir. Özel kişi, belirtilen sayıda anımsatıcı aldıktan sonra tutma bildirimini kabul etmezse, hukuk ekibi, özel kişi ve bunların yöneticisine otomatik olarak bir yükseltme bildirimi göndermek için bir iş akışı belirtilebilir.

Yükseltmeleri zamanmak için:

1. İlerletir **kutucuğunun** içinde Düzenle'ye **tıklayın**.

2. Durum iki **durumlu düğmeyi** etkinleştirerek İlerlesyon **iş akışını** etkinleştirin.

3. **İlerleç aralığını (gün olarak)** (gerekli) belirtin.

4. Yükseltme **sayısını belirtin** (gerekli). Bu alanda, yanıtsız koruyuculara kaç yükseltme gönder göndericisi olduğu belirtir. Örneğin, yükseltme sayısını 3 olarak ayarsanız, bilgili kişi ve bunların yöneticisine en çok üç kez yükseltme bildirimi gönderilir. Bir koruyucu tutma bildirimini kabul edildikten sonra, yükseltmeler artık gönderilmez.

5. Bildirim **için Konu** belirtin (gerekli).

6. Özel belgeye sağlamak istediğiniz içeriği veya ek yönergeleri belirtin (gerekli). 2. Adımda tanımlandığı portal içeriği, yükseltme bildiriminin sonuna eklenir.

7. **Kaydet'e** tıklayın ve bir sonraki adıma geçin.

## <a name="step-5-assign-custodians-to-receive-notifications"></a>5. Adım: Bildirimleri almak için koruyucuları atama

Bildirimlerin içeriğini sonuç olarak verdikten sonra, bildirimleri göndermek istediğiniz koruyucuları seçin.

![Özel renkçiler sayfası'ı seçin.](../media/SelectCustodians.PNG)

Koruyucu eklemek için:

1. İletişime koruyucular atamak için adının yanındaki onay kutusuna tıklayın.

    İletişim oluşturulduktan sonra, bildirim iş akışı otomatik olarak seçili koruyuculara uygulanır.

2. İletişim **ayarlarını ve** ayrıntılarını gözden geçirmek için Sonraki'ne tıklayın.

> [!NOTE]
> Yalnızca vakaya ekli olan ve bu durum içinde başka bir bildirim gönderilmeyen koruyucular  eklersiniz.

## <a name="step-6-review-settings"></a>6. Adım: Ayarları gözden geçirme

Ayarları gözden geçirdikten ve iletişimi **tamamlamak için** Gönder'e tıklarsanız, sistem yayın bildirimini göndererek iletişim iş akışını otomatik olarak başlatılır.

## <a name="events-that-trigger-notifications"></a>Bildirimleri tetikleyen olaylar

Aşağıdaki tabloda, farklı türlerde bildirimlerin koruyuculara gönderilmesinde tetiklenen olay yönetimi süreci açıkmektedir.

|İletişim türü|Tetikleyici |
|:---------|:---------|
|Yayınla ile ilgili bildirimler|Bildirimin ilk oluşturulması. Ayrıca,  tutma bildirimini el ile de yeniden postaleyebilirsiniz. |
|Yeniden verme bildirimlerini|İletişimi düzenle sihirbazının **Portal İçeriğini** Tanımla sayfasındaki portal **içeriğini** güncelleştirme.|
|Sürüm duyuruları|Custoando, bu vakadan çıkar.|
|Anımsatıcılar|Anımsatıcı için yapılandırılan anımsatıcı aralığı ve sayısıdır.|
|Yükseltmeler|Yükseltme için yapılandırılmış anımsatıcı aralığı ve sayısı.|
|||
