---
title: Microsoft Uyumluluk Yöneticisi uyarıları ve uyarı ilkeleri
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Microsoft Uyumluluk Yöneticisi'nde uyumluluk puanınızı etki etkileyene etkinlikler için nasıl uyarı oluştur oluğunu öğrenin.
ms.openlocfilehash: bb81588be31b2c13113953c585112ee2f5a56875
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704692"
---
# <a name="microsoft-compliance-manager-alerts-and-alert-policies"></a>Microsoft Uyumluluk Yöneticisi uyarıları ve uyarı ilkeleri

**Bu makalede:** Uyumluluk **Yöneticisi'nde belirli** etkinlikler için uyarı ayarlamayı, uyarıları yönetmeyi ve uyarı koşulları tanımlamak için **uyarı** ilkeleri oluşturmayı öğrenin.

## <a name="overview"></a>Genel bakış
Uyumluluk Yönetimi, değişiklik olur olmaz sizi uyararak uyumluluk hedeflerinize bağlı kalmanızı sağlar. Örneğin, kiracınız yapılandırma değişikliği nedeniyle bir geliştirme eyleminin puanının ne zaman artmış veya azaldığını ya da uygulama veya test çalışması yapmak üzere kullanıcıya bir geliştirme eylemi atandığı konusunda sizi bilgilendirmek için uyarılar kurabilirsiniz. Uyarı [oluşturabilirsiniz](#create-an-alert-policy) .

Uyarı oluşturmak için, önce bir uyarıyı tetikleyen koşulları ve bildirim sıklığını tetikleyen koşulların ana hatlarını oluşturmak için bir uyarı ilkesi ayarlaytısınız. İlke koşullarınıza uygun bir eşleşme algılarsanız, ayrıntıları içeren bir e-posta bildirimi alırsınız ve bu nedenle incelemeniz veya başka bir işlem yapmak isteyip istemeyebilirsiniz.


Tüm uyarılar, Uyumluluk **Yönetimi'nin** Uyarılar sekmesinde ve tüm uyarı ilkeleri de Uyarı İlkeleri **sekmesinde listelenir**.

## <a name="understanding-the-alerts-and-alert-policies-pages"></a>Uyarılar ve Uyarı ilkeleri sayfalarını anlama

> [!IMPORTANT]
> Uyumluluk   **Yöneticisi'nde Uyarılar** ve Uyarı ilkeleri sayfalarına Azure Active Directory için, kullanıcıların Uyumluluk Yönetimi'nde (AD) Güvenlik okuyucusu rolünü tutmaları gerekir. Uyarılarla ve uyarı ilkeleriyle çalışmak için ek güvenlik ve Uyumluluk Yöneticisi rolleri gereklidir. Aşağıda, Uyarı ilkesi [izinleri'nin ayrıntılarını bulabilirsiniz](#alert-policy-permissions).

### <a name="alert-policies-page"></a>Uyarı ilkeleri sayfası

Uyarı **ilkelerinizi görüntülemek** ve yönetmek için Uyumluluk Yönetimi'nin Uyarı ilkeleri sekmesini seçin. Uyarı **ilkeleri sayfası** , kurum tarafından oluşturulan tüm ilkelerin liste listesini içeren bir tablo içerir. Bu sayfadan yeni ilkeler oluşturabilir, var olan ilkeleri düzenleyebilir, etkinleştirme durumunu değiştirebilir ve ilkeleri silebilirsiniz.

Durum sütununda **Etkin ayarı****,** ilkenin etkin olduğu ve koşullar karşılendiğinde uyarıları tetikley olduğu anlamına gelir. **Etkin değil** , ilkenin var olduğu ancak uyarı oluşturma olduğu anlamına gelir. İlkeler tablosu ayrıca, ilkenin önem derecesine ve ilkenin en son değiştirilma tarihini de gösterir.

Tek tek ilkenin ayrıntılarını görüntülemek için, tabloda o ilkenin satırına tıklayın. Tüm ayrıntıları gösteren bir uçarak çıkış bölmesi görüntülenir. Bölmenin  en altındaki Eylem düğmesini seçin ve ilkeyi düzenleme, uyarılarını görüntüleme veya silme seçeneklerinden birini belirleyin. Ekleme, düzenleme, silme, etkinleştirme ve devre dışı bırakma komutları tablonun üst kısmında filtrelerin üzerinde de kullanılabilir.

Uyarı ilkesi oluşturmaya başlama için bkz. [Uyarı ilkesi oluşturma](#create-an-alert-policy).

### <a name="alerts-page"></a>Uyarılar sayfası

Uyarılarınızı **görüntülemek** ve yönetmek için Uyumluluk Yöneticisi'nde Uyarılar sekmesini seçin. Uyarılar **sayfası** , bir uyarı ilkesi tarafından oluşturulan her uyarının önem derecesi ve tetikleyen olay (örneğin, bir eylemin puanı değişikliği) ve uyarının tarihini içeren bir tablo içerir.

Tek bir uyarıyı görüntülemek için tabloda bu uyarıyı seçin. Bölmenin Genel Bakış sekmesinde tüm ayrıntıları gösteren bir **açılır** bölme görüntülenir. Olaylar **günlüğü sekmesi** , uyarıyı tetikleyen kullanıcıların dim eylemleri görüntüler.

**Bölmenin** en altındaki Eylem düğmesi, bu uyarıyı izleme için bir kullanıcıya atama, eylemleri uyarıyı oluşturan kullanıcıya e-posta gönderme veya uyarıyı oluşturan ilkenin ayrıntılarını görüntüleme seçenekleri sağlar. Uyarı adının sol tarafından görüntülenen yuvarlak düğmeyi seçerek, satırın üzerine gelin ve tablonun üst kısmında, filtrelerin üstündeki düğmelerden birini seçerek de aynı işlemleri gerçekleştirebilirsiniz.

Uyarılarla çalışmaya başlamak için bkz [. Uyarıları görüntüleme ve yönetme](#viewing-and-managing-alerts).

## <a name="alert-policy-permissions"></a>İlke izinlerini uyarın

Aşağıdaki tabloda, kullanıcıların rol türüne göre uyarı ve uyarı ilkeleri oluştur ve düzenleyemezsiniz. Uyumluluk Yöneticisi rolünün yanı sıra, kullanıcıların aşağıdaki gibi bir Azure AD rolüne de ihtiyacı vardır:

- Uyarıları **ve uyarı** ilkelerini görüntülemek için Azure AD'de Güvenlik okuyucu rolü
- Uyarı **ilkelerini oluşturmak** veya güncelleştirmek için Azure AD'de Güvenlik yöneticisi rolü
 
Aşağıdaki ağdan [Azure rolleri hakkında daha fazla Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#azure-roles-in-the-microsoft-365-compliance-center).


| Rol | İlkeleri oluşturabilir ve düzenleyebilir | Uyarıları düzenleyebilir | 
| :------------- | :-------------: | :------------: |
| **Uyumluluk Yöneticisi Yönetimi**| Evet  | Evet | 
| **Uyumluluk Yöneticisi Değerlendiren**| Evet | Evet | 
| **Uyumluluk Yöneticisi Katkı**| Evet | Evet | 
| **Genel Yönetici**| Hayır | Hayır  | 
| **Uyumluluk Yöneticisi Okuyucu**| Hayır | Hayır | 

Uyumluluk Yöneticisi için [kullanıcı izinlerini ayarlamayı ve roller atamayı öğrenin](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

## <a name="create-an-alert-policy"></a>Uyarı ilkesi oluşturma

Geliştirme eylemleriyle ilgili bazı değişiklikler veya olaylar olduğunda sizi uyaran ilkeler oluşturabilirsiniz. Olay türleri aşağıda listelenmiştir.

### <a name="alert-event-types"></a>Uyarı olay türleri

- **Puan değişikliği**: Kuruluşta birinin yaptığı yapılandırma değişiklikleri nedeniyle geliştirme eylemi olarak verilen puan artışı veya düşüş. Örneğin, organizasyonunız bir Insider risk yönetimi ilkesi oluşturursa, bu ilke belirli bir işlem için puanlarınızı belirli bir miktarda artırabilir.
- **Atama değişikliği**: Bir kullanıcıya geliştirme eylemi atanmış, farklı bir kullanıcıya yeniden atanmış veya kullanıcıdan atanmamış bir eylemdir.
- **Uygulama durumu değişikliği**: Kullanıcı, geliştirme eyleminin uygulama durumunu değiştirdi.
- **Test durumu değişikliği**: Kullanıcı bir geliştirme eyleminin test durumunu değiştirdi.
- **Kanıt değişikliği**: Kullanıcı geliştirme eyleminin Belgeler sekmesinde bir kanıt **belgesi** yükledi veya sildi.

### <a name="policy-creation-steps"></a>İlke oluşturma adımları

Bir veya birden çok olay temel alarak uyarı oluşturmak için, aşağıdaki adımları izleyin:

1. Uyumluluk **Yöneticisi'nde**, Uyarı ilkeleri **sayfasına gidin** ve **+Ekle'yi seçerek** ilke oluşturma sihirbazını başlatın.

2. Ad ve **açıklama sayfasında** , ilke için bir ad ve isteğe bağlı olarak bir açıklama girin, sonra da Sonraki'yi **seçin**.

3. Koşullar **sayfasında** , uyarıyı tetikleyen bir veya birden çok olay seçin. Geliştirme **eylemi etkinliği üst** bilgisinde Alt **koşul ekle'yi** seçin ve her koşul adının sol üzerine gelindiğinde görüntülenen kutuyu işaretleyin. Bir ilke için bir veya daha fazla koşullar seçebilirsiniz: atama değişikliği, kanıt değişikliği, uygulama durumu değişikliği, puan değişikliği, test durumu değişikliği. Bitirdikten sonra, Sonraki'yi **seçin**.

4. Sonuçlar **sayfasında** , bir ilke eşleşmesi algılandığında ne olacağını seçin:
      - Bir eşleşme algılandığında uyarı için önem düzeyi seçin: düşük, orta veya yüksek.
      - Bir eşleşme algılandığında e-postayla ne sıklıkta bildirileceklerini seçin. Her eşleşmeyle ilgili olarak bildirilecek değeri seçebilir veya üç eşleşmenin üzerindeki belirli bir eşleşme sayısının eşiğini seçebilirsiniz.
      - Üç veya daha fazla eşleşmeden sonra size bildirilecekse, bu eşiğin ulaş olması gereken dakika sayısını (örneğin, 90 dakika içinde 4 eşleşme) siz seçersiniz.
  
    Bitirerek, Sonraki'yi **seçin**.

5. Alıcıyı **uyarın** sayfasında, ilke koşulları karşı olduğunda e-posta almak için kuruluşta diğer kullanıcıları seçin. İlkeyi oluşturan kullanıcı varsayılan alıcıdır. **+Alıcıları seç'i** seçin ve e-posta bildirimini almak istediğiniz çıkış bölmesinde her kullanıcı adının yanındaki kutuları işaretleyin. Bitirerek Alıcı **ekle'yi ve ardından** Sonraki'yi **seçin**.

6. Tüm seçimleri gözden geçirerek ve öğesini seçerek her bölümde değişiklik yapın, ardından Sonraki'yi **seçin**. Gözden geçirmeyi bitirdikten sonra İlke **oluştur'a seçin**.

7. İlkeniz oluşturulduğunda Bitti'yi **seçin**. Uyarı ilkeleri sayfanıza **, yeni oluşturduğunuz** ilkenin açılır pencere bölmesiyle birlikte gelirsiniz.

İlkeniz bir kez oluşturdukta etkin hale gelir, bu da eşleşmeleri algılamaya ve uyarılar oluşturmaya başlayacağı anlamına gelir. **İlkeleri devre dışı bırakma** veya silme için aşağıdaki İlkeleri yönetme bölümüne bakın.

İlke oluşturduk veya güncelleştirildikten sonra, bu ilkenin uyarıları oluşturması 24 saate kadar sürebilir. Olayları [tetikleme ve toplama](#view-alert-details) uyarısı hakkında bilgi edinmek için aşağıdaki Uyarı ayrıntılarını görüntüleme'ye bakın.

## <a name="managing-policies"></a>İlkeleri yönetme

Uyarı **ilkeleri sayfası** , tüm ilkelerinizin bir tablo listesini içerir. Bu [sayfayı daha fazla anlamak](#alert-policies-page) için bkz. Uyarı ilkeleri sayfası. Bazı eylemler belirli rollerle kısıtlıdır; bkz [. Uyarı ilkesi izinleri](#alert-policy-permissions).

### <a name="view-policy-details"></a>İlke ayrıntılarını görüntüleme

Uyarı ilkeleri sayfasındaki satırdan bir ilke  seçerek, ilkenin eşleşme koşulları, uyarı bildirimlerinin gönderip gönderilmesi, kimin ve ne zaman ve önem düzeyi de içinde olmak üzere ilkenin ayrıntılarını gösteren bir çıkış paneli açın.

**Panelin** en altındaki Eylemler düğmesi size ilkeyi düzenleme, ilkeyi silme veya uyarıları görüntüleme seçenekleri sağlar.

### <a name="view-a-policys-alerts"></a>İlke uyarılarını görüntüleme

İlkenin çıkış panelinde Eylemler'i ve **ardından** Uyarıları **görüntüle'yi seçin**. Doğrudan, bu ilke tarafından oluşturulan tüm uyarıların filtre uygulanmış görünümünün yer olduğu Uyarılar sayfasına gelirsiniz. Uyarılarla [nasıl çalış öğrenin](#viewing-and-managing-alerts).

### <a name="edit-a-policy"></a>İlkeyi düzenleme

İlkenin adı dışında herhangi bir yönünü düzenleyebilirsiniz. Adını değiştirmek için yeni bir adla yeni bir ilke oluşturmanız gerekir.

Bir ilkeyi düzenlemek için, Uyarı ilkeleri sayfasındaki satırın üzerine gelerek adının sol kısmında görünen yuvarlak düğmeyi seçin ve filtrelerin  üst kısmında bulunan Düzenle düğmesini seçin.

İlke oluşturma sihirbazına alınırsınız ve burada ilkeniz üzerinde değişiklikler yapabilirsiniz ve değişiklikleri kaydedebilirsiniz.  Ayrıca, ayrıntıları paneline getirmek için ilkeyi ve Eylemler düğmesinden **İlkeyi** **düzenle'yi de seçin**. Sihirbazın üzerinde yeniden çalışmaya başladıktan sonra, seçimlerinizi gözden geçirin ve son adımda **Güncelleştir'i** seçerek değişikliklerinizi kaydedin.

Uyarıların güncelleştirilmiş ilke tarafından oluşturulmaları 24 saate kadar sürebilir.

### <a name="activate-or-inactivate-a-policy"></a>İlkeyi etkinleştirme veya devre dışı bırakma

İlkeler oluşturulduktan hemen sonra varsayılan olarak etkinleştirilir. Etkin olduğunda, koşullar karşı olduğunda bir ilke uyarı (Uyarılar sayfasında gösterilir) oluşturabilir ve belirlenen alıcılara bir bildirim e-postası gönderir.

İlkeyi etkin olmayan durum  olarak değiştirmek (yani uyarı oluşturmaz) için, satırın üzerine geldiğinde ilke adının sol tarafından görüntülenen yuvarlak düğmeyi seçin. Sonra tablonun **üstündeki** Devre dışı bırak komutunu seçin. İlkenizin durumu artık Etkin Değil olarak okunacak. İlkeyi yeniden etkinleştirmek için, aynı işlemi izleyin **ve filtrelerin** üstündeki Etkinleştir düğmesini seçin.

### <a name="delete-a-policy"></a>İlkeyi silme

bir ilkeyi silmek için, Uyarı ilkeleri sayfasında ilke adının yanındaki **düğmeyi seçin** ve sayfanın üst **kısmında Sil'i** seçin. Ayrıca, ayrıntıları paneline getirmek için ilkeyi ve Eylemler düğmesinden **İlkeyi** **sil'i de seçin**.

Silme işlemi kalıcıdır. Bir ilkeyi silseniz, artık uyarı veya e-posta bildirimi oluşturmaz. Silinmiş ilkelere bağlı [uyarılar hakkında daha fazla bilgi öğrenin](#when-policies-are-deleted).

## <a name="viewing-and-managing-alerts"></a>Uyarıları görüntüleme ve yönetme

Uyarılar **sayfasında** , tüm ilkeleriniz tarafından oluşturulan tüm uyarıların yer olduğu bir tablo görüntülenir. İlkenin koşullarıyla eşleşen bir olay hemen sonra uyarı oluşturulur. Uyarı adı, uyarıyı oluşturan ilkeyle aynıdır.

Uyarı yalnızca etkin bir ilkeden uyarı oluşturularak oluşturul sağlar. Uyarı bir kez oluşturulsa da, ilkenin etkin olup olmadığı önemli  değildir ve Uyarılar sayfasında listelenir.

### <a name="filter-your-view-of-alerts"></a>Uyarı görünümlerinizi filtreleme
Uyarılar sayfanız üzerinde yer alan tablonun üstündeki **Filtre komutunu** seçerek uyarıların görünümünü **filtreleyebilirsiniz** . Filtre **uç bölmesinde** , şu filtre seçeneklerinden birini belirleyin:

- Olay türü
- Önem Derecesi
- Durum
- Atanan kullanıcı
- Algılama tarihi
- İlke adı

Seçimlerinizi yaparak Uygula'ya **seçin**. Uçarak giriş bölmesi kapanır ve güncelleştirilmiş **Uyarılar sayfanız** filtrelenmiş görünümlerinizi gösterir. Filtreleriniz tablonun en üstünde görüntülenir, ancak tabloda tüm filtre sütunları görüntülenmez.

### <a name="view-alert-details"></a>Uyarı ayrıntılarını görüntüleme

Uyarıyı tetikleyen olaylar da dahil olmak üzere uyarıyla ilgili tüm ayrıntıları görüntülemek için, tabloda bu uyarıyı seçin. Açılır bölmede, bölmenin Genel Bakış sekmesinde **uyarının** ayrıntıları gösterilir.

**Açılır** panelin Olaylar günlüğü sekmesi, uyarıyı oluşturan etkinlikleri (not değişikliği veya ödev değişikliği gibi) ve her eylemle ilişkilendirilmiş kullanıcının adı ve algılanan tarihle birlikte listeler.

### <a name="alert-events"></a>Olayları uyarın

**Uyarılar** sayfasındaki **Olaylar sütunu** algılanan bir ilkenin koşullarını gösterir; başka bir deyişle, uyarıyı oluşturan etkinlik. **Uyarının** ayrıntılar panelindeki Olaylar günlüğü sekmesinde olayın her örneğinin, ilişkili kullanıcının ve algılanan tarihin listesi yerlanır. Olay değerleri aşağıda listelenmiştir:

- **Puan değişikliği**: puan artış veya azaltma sayısını gösterir
- **Atama değişikliği**: Bir kullanıcıya geliştirme eylemi atanmış, farklı bir kullanıcıya yeniden atanmış veya kullanıcıdan atanmamış bir eylem
- **Uygulama durumu değişikliği**: Kullanıcı geliştirme eyleminin uygulama durumunu değiştirdi
- **Test durumu değişikliği**: Kullanıcı bir geliştirme eyleminin test durumunu değiştirdi.
- **Kanıt değişikliği**: Kullanıcı geliştirme eyleminin Belgeler sekmesinde bir kanıt belgesi yükledi veya sildi
- **Birden çok olay**: Aynı olay türünün birden çok örneği algılandı; örneğin, birden çok kez yeniden atanmış tek bir geliştirme eylemi
- **Birden çok koşul**: Tek bir ilke içinde birden çok koşul algılandı

#### <a name="alert-aggregation-for-multiple-events-within-one-minute"></a>Bir dakika içinde birden çok olay için toplamayı uyarın

Bir dakikayla uyarı ilkesi koşullarına uygun birden çok olay gerçekleşirken, bunlar uyarı toplama adı verilen işlem tarafından var olan uyarıya eklenir.

Örneğin, bir ilkeyle eşleşen bir olay olduğunda, Uyarılar sayfasında bir uyarı oluşturulur, görüntülenir ve bir bildirim gönderilir. Aynı ilkeyle eşleşen başka bir olay ilk olayın bir dakika içinde gerçekleşirse, Uyumluluk Yöneticisi yeni uyarıyı tetiklemek yerine var olan uyarının Olay  günlüğü sekmesine ek olayla ilgili ayrıntıları ekler. Uyarı toplamanın amacı, uyarıyı "yorgunluğu" azaltmaya yardımcı olmak ve daha az uyarıya odaklanmak ve önlem almaktır.

### <a name="taking-action-on-alerts"></a>Uyarılar üzerinde eylemde bulundurma

İlkelerden biri uyarıyı  oluşturmazsa, uyarıya neden olan olayları sınar ve olayları doğrulamanız mı yoksa daha fazla araştırmanız mı gerekiyor?

Uyarı üzerinde eylem yapmak için, Uyarılar sayfasındaki satırı seçerek ayrıntılarıyla birlikte çıkış panelini açın, Eylemler düğmesini seçin ve aşağıda listelenen seçeneklerden birini  belirleyin. Ayrıca, satırın üzerine gelerek uyarı adının sol tarafından görüntülenen yuvarlak düğmeyi seçerek ve filtrelerin üstünde, sayfanın üst kısmında bulunan eylem düğmelerinden birini seçerek de işlem gerçekleştirebilirsiniz.

**Uyarı ata**: Uyarıya neden olan olayları araştırması veya doğrulaması için bu uyarıyı bir kullanıcıya atamak istiyor olabilirsiniz. Bu seçeneği tercih ettiyseniz, kurumdan bir kullanıcı seçerek uyarıyı bu kullanıcıya atayabilirsiniz. Uyarılar sayfasında Filtreler'i seçerek ve Atanan alanına  kullanıcının adını girerek  uyarılar **görünümünüze filtreleyebilirsiniz**.

**E-posta** uyarısı: Eylemin olduğunu onaylamak için uyarının etkinliğiyle ilişkilendirilmiş kullanıcıya bir e-posta göndermek istiyor olabilir. Bu seçeneği tercih ettiyseniz, uyarı hakkında temel bilgileri içeren bir e-posta şablonu açılır. Bu şablonu diğer yönergelerle özelleştirilebilir ve kullanıcıya gönderebilirsiniz.

**İlke ayrıntılarını** görüntüleme: Uyarıyı tetikleyen ilkenin ayarlarını gözden geçirmek gerekebilir. Bu seçeneği belirttiyseniz, ilke ayrıntıları paneli zaten açık durumdayken doğrudan Uyarı ilkeleri  sayfasına alınırsanız bunu unutmayın. Artık ilke ayrıntıları panelini **kapatan** Uyarılarınız sayfasında olmayacaktır.

**Durumu değiştirme**: Uyarının etkisini gözden geçirmenize ve incelemeniz gerekip gerekmiyorlarına bağlı olarak uyarının durumunu güncelleştirebilirsiniz. Sonraki bölümde uyarı durumları hakkında daha fazla bilgi edinebilirsiniz.

### <a name="alert-status"></a>Uyarı durumu

Uyarı oluşturulduğunda, bu uyarının durumu **Etkin'tir**. Her uyarının ayrıntılarını gözden geçirebilirsiniz ve bunun durumunu aşağıda listelenen eyaletlerden herhangi biri ile güncelleştirebilirsiniz:

- **Etkin**: Durumu değiştirilene kadar uyarının varsayılan durumu
- **Araştırılıyor**: uyarı araştırılıyor
- **Çözümlendi**: Uyarı için daha fazla araştırma veya takip gerekli değil
- **Reddedildi**: Uyarı ilgili değil veya araştırmaya gerek yok

Uyarının durumunu atamak veya değiştirmek için tablodaki satırından bir uyarı seçin, sayfanın üst kısmında, filtrelerin  üstündeki Durumu değiştir'i seçin. Uyarı durumunu güncelleştir açılır bölmesinde, açılan menüden bir durum seçin ve ardından Uyarıyı **güncelleştir'i seçin**.

Uyarı bir kez  oluşturulana kadar, bu uyarının durumu uyarıyı oluşturan ilkenin durumundan bağımsız olur. Örneğin, etkin olmayan bir ilkeyle ilişkilendirilmiş etkin bir uyarının olması ve  daha sonra devre dışı bırakılıyor veya silinmiş bir ilke tarafından oluşturulan  uyarıda araştırılıyor durumlarının araştırılıyor olması mümkündür.

### <a name="when-policies-are-deleted"></a>İlkeler silindiğinde

İlke silindiğinde, bu ilke tarafından oluşturulan tüm uyarılar Uyarılar sayfasında kalır, ancak yeni uyarı oluşturulmaz.

## <a name="email-notifications-of-alerts"></a>Uyarıların e-posta bildirimleri

İlke oluşturulduğunda, ilkeyi oluşturan kullanıcıya bir eşleşme algılandığından emin olmak için bir e-posta gönderilir. Bu e-posta bildirimlerini, organizasyon ek kullanıcılara göndermeyi seçebilirsiniz. Uyarılar yakın zamanda gerçek zamanlı olarak gerçekleşir ve bir uyarı oluşturulur oluşturulmaz e-posta bildirimleri gönderilir. E-posta olay adını, önem derecenizi, algılanan zamanı ve Uyumluluk Yöneticisi'nde uyarıyı görüntülemek için bir bağlantı içerir.

### <a name="remove-users-from-receiving-alerts"></a>Kullanıcıların uyarı almalarını kaldırma

Alıcıları uyarıyor ve sonra da kaldırmaya karar veriyorsanız, aşağıdaki adımları izleyin. İlke eşleşmeleri algılandığında ilkeyi oluşturanın yine de e-posta bildirimleri almayacaklarını unutmayın.

1. İlkenizi düzenleme [adımlarını izleyin](#edit-a-policy).
2. Alıcıları uyar ekranına **ulaşabilirsiniz,** +Alıcıları **seç'i seçin**.
3. Alıcıları seçin  uç noktası panelinde, bildirimlerden kaldırmak istediğiniz kullanıcıyı bulun ve adının sol ödül kutusunun işaretini kaldırın, ardından Alıcı ekle düğmesini seçin (seçiminizi kaydetme etkisi vardır).
4. Sihirbazın üzerinden devam edin ve kullanıcının Gözden Geçir ve bitir sayfasında **Alıcılar'ın** altında görünme olmadığını onaylayın. Ayarlarınızı **kaydedip** bitirmek için Güncelleştir'i seçin.
