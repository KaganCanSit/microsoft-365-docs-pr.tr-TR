---
title: Microsoft Purview Uyumluluk Yöneticisi uyarıları ve uyarı ilkeleri
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
description: Microsoft Purview Uyumluluk Yöneticisi'nde uyumluluk puanınızı etkileyebilecek etkinlikler için uyarılar oluşturmayı öğrenin.
ms.openlocfilehash: 499d1f005b67b2a9583d7138ce784b2e7ae1c8ad
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66642250"
---
# <a name="microsoft-purview-compliance-manager-alerts-and-alert-policies"></a>Microsoft Purview Uyumluluk Yöneticisi uyarıları ve uyarı ilkeleri

**Bu makalede:** Uyumluluk Yöneticisi'nde belirli etkinlikler için **uyarı ayarlamayı** , uyarıları yönetmeyi ve uyarı koşullarını tanımlamak için **uyarı ilkeleri oluşturmayı** öğrenin.

## <a name="overview"></a>Genel Bakış
Uyumluluk Manger, uyumluluk hedeflerinizi takip edebilmeniz için değişiklikler gerçekleşir gerçekleşmez sizi uyarabilir. Örneğin, kiracınızdaki bir yapılandırma değişikliği nedeniyle bir iyileştirme eyleminin puan değeri arttığında veya azaldığında ya da bir kullanıcıya uygulama veya test çalışması yapması için bir iyileştirme eylemi atandığında sizi bilgilendirecek uyarılar ayarlayabilirsiniz. Uyarı oluşturabileceğiniz [olay türlerini](#create-an-alert-policy) görüntüleyin.

Uyarı oluşturmak için, önce bir uyarıyı tetikleyen koşulları ve bildirimlerin sıklığını ana hatlarıyla belirlemek için bir uyarı ilkesi ayarlarsınız. İlke koşullarınızla bir eşleşme algıladığımızda ayrıntıları içeren bir e-posta bildirimi alırsınız; böylece araştırmanız veya başka işlemler yapmanız gerekip gerekmediğini belirleyebilirsiniz.

Tüm uyarılar Uyumluluk Günlüğü'ndeki **Uyarılar** sekmesinde, tüm uyarı ilkeleri ise **Uyarı İlkeleri sekmesinde** listelenir.  Tüm kuruluşlar için [önceden ayarlanmış bir varsayılan puan değiştirme ilkesi](#default-score-change-policy) vardır.

## <a name="understanding-the-alerts-and-alert-policies-pages"></a>Uyarılar ve Uyarı ilkeleri sayfalarını anlama

> [!IMPORTANT]
> Uyumluluk Yöneticisi'ndeki **Uyarılar** ve **Uyarı ilkeleri** sayfalarına erişmek için kullanıcıların Azure Active Directory'de (AD) **Güvenlik okuyucusu** rolüne sahip olması gerekir. Uyarılar ve uyarı ilkeleriyle çalışmak için ek güvenlik ve Uyumluluk Yöneticisi rolleri gerekir. [Uyarı ilkesi izinleri](#alert-policy-permissions) bölümünde ayrıntıları aşağıda bulabilirsiniz.

### <a name="alert-policies-page"></a>Uyarı ilkeleri sayfası

**Uyarı ilkelerinizi** görüntülemek ve yönetmek için Uyumluluk Yöneticisi'nde Uyarı ilkeleri sekmesini seçin. **Uyarı ilkeleri** sayfası, kuruluşunuz tarafından oluşturulan tüm ilkeleri listeleyen bir tablo içerir. Bu sayfadan yeni ilkeler oluşturabilir, mevcut ilkeleri düzenleyebilir, etkinleştirme durumunu değiştirebilir ve ilkeleri silebilirsiniz.

**Durum sütununda** **Etkin**, ilkenin etkin olduğu ve koşullar karşılandığında uyarıları tetiklediğinde olduğu anlamına gelir. **Etkin değil** , ilkenin var olduğu ancak uyarı oluşturmayolduğu anlamına gelir. İlkeler tablosu, ilkenin önem derecesini ve ilkenin son değiştirilme tarihini de gösterir.

Tek bir ilkenin ayrıntılarını görüntülemek için tablodaki satırını seçin. Tüm ayrıntıları gösteren bir açılır pencere bölmesi görüntülenir. Bölmenin alt kısmındaki **Eylem** düğmesini seçin ve ilkeyi düzenlemek, uyarılarını görüntülemek veya silmek için seçenekler arasından seçim yapın. Ekleme, düzenleme, silme, etkinleştirme ve devre dışı bırakma komutları, filtrelerin üzerinde tablonun üst kısmında da kullanılabilir.

Uyarı ilkesi oluşturmaya başlamak için bkz. [Uyarı ilkesi oluşturma](#create-an-alert-policy).

### <a name="alerts-page"></a>Uyarılar sayfası

**Uyarılarınızı** görüntülemek ve yönetmek için Uyumluluk Yöneticisi'nde Uyarılar sekmesini seçin. **Uyarılar** sayfasında, bir uyarı ilkesi tarafından oluşturulan her uyarının yanı sıra önem derecesi ve tetikleme olayı (örneğin, bir eylemin puan değişikliği) ve uyarının tarihi listelendiği bir tablo bulunur.

Tek bir uyarıyı görüntülemek için tablodaki satırını seçin. Bölmenin **Genel Bakış** sekmesinde tüm ayrıntıları gösteren bir açılır pencere görüntülenir. **Olaylar günlüğü** sekmesinde, uyarıyı tetikleyen kullanıcılar tarafından gerçekleştirilen eylemler görüntülenir.

Bölmenin altındaki **Eylem** düğmesi, uyarıyı izleme için kullanıcıya atama, eylemleri uyarıyı oluşturan kullanıcıya e-posta gönderme veya uyarıyı oluşturan ilkenin ayrıntılarını görüntüleme seçenekleri sağlar. Ayrıca, satırının üzerine geldiğinizde uyarı adının solunda görünen yuvarlak düğmeyi seçip filtrelerin üstündeki tablonun üst kısmındaki düğmelerden birini seçerek de aynı eylemleri gerçekleştirebilirsiniz.

Uyarılarla çalışmaya başlamak için bkz. [Uyarıları görüntüleme ve yönetme](#viewing-and-managing-alerts).

## <a name="alert-policy-permissions"></a>Uyarı ilkesi izinleri

Aşağıdaki tabloda, hangi kullanıcıların rol türlerine göre uyarılar ve uyarı ilkeleri oluşturup düzenleyebileceği özetlenmiştir. Uyumluluk Yöneticisi rolüne ek olarak, kullanıcıların aşağıdaki gibi bir Azure AD rolüne de ihtiyacı vardır:

- Uyarıları ve uyarı ilkelerini görüntülemek için: Azure AD'da **Güvenlik okuyucusu** rolü
- Uyarı ilkeleri oluşturmak veya güncelleştirmek için: **Azure AD'de Uyumluluk yöneticisi, Uyumluluk veri yöneticisi**, **Güvenlik yöneticisi** veya **Güvenlik işleci** rolü 
 
[Microsoft Purview uyumluluk portalı Azure rolleri](microsoft-365-compliance-center-permissions.md#azure-roles-in-the-compliance-portal) hakkında daha fazla bilgi edinin.


| Rol | İlkeler oluşturabilir ve düzenleyebilir | Uyarıları düzenleyebilir | 
| :------------- | :-------------: | :------------: |
| **Uyumluluk Yöneticisi Yönetimi**| Evet  | Evet | 
| **Uyumluluk Yöneticisi Değerlendiricisi**| Evet | Evet | 
| **Uyumluluk Yöneticisi Katkıda Bulunanı**| Evet | Evet | 
| **Uyumluluk Yöneticisi Okuyucusu**| Hayır | Hayır | 
| **Genel yönetici**| Evet | Evet | 

[Kullanıcı izinlerini ayarlamayı ve Uyumluluk Yöneticisi için roller atamayı](compliance-manager-setup.md#set-user-permissions-and-assign-roles) öğrenin.

## <a name="create-an-alert-policy"></a>Uyarı ilkesi oluşturma

İyileştirme eylemleriyle ilgili bazı değişiklikler veya olaylar gerçekleştiğinde sizi uyarmak için ilkeler oluşturabilirsiniz. Olay türleri aşağıda listelenmiştir.

### <a name="alert-event-types"></a>Uyarı olay türleri

- **Puan değişikliği**: Kuruluşunuzdaki birinin yaptığı yapılandırma değişiklikleri nedeniyle iyileştirme eylemi için verilen puan artış veya düşüş. Örneğin, kuruluşunuz bir iç risk yönetimi ilkesi oluşturursa bu, belirli bir eylem için puanlarınızı belirli bir miktar artırabilir.
- **Atama değişikliği**: Kullanıcıya bir iyileştirme eylemi atandı, farklı bir kullanıcıya yeniden atandı veya kullanıcıdan atanmadı.
- **Uygulama durumu değişikliği**: Kullanıcı, geliştirme eyleminin uygulama durumunu değiştirdi.
- **Test durumu değişikliği**: Kullanıcı, geliştirme eyleminin test durumunu değiştirdi.
- **Kanıt değişikliği**: Kullanıcı, geliştirme eyleminin **Belgeler** sekmesindeki bir kanıt belgesini karşıya yüklemiş veya silmiştir.

#### <a name="default-score-change-policy"></a>Varsayılan puan değiştirme ilkesi

Uyumluluk Yöneticisi, iyileştirme eylemlerindeki puan değişikliklerini izlemek için varsayılan bir uyarı ilkesi ayarlar. Bir iyileştirme eyleminin puanı değiştiğinde varsayılan ilke bir uyarı oluşturur. Varsayılan ilke ayarlarının çoğu düzenlenemez, ancak bildirimler için ek alıcılar ekleyebilirsiniz.

Varsayılan ilkenin ayarları şunlardır:

- 60 dakikalık bir süre içinde algılanan tüm eşleşmeler, aşırı bildirimleri azaltmak için tek bir uyarıda gruplandırılır. Örneğin, beş geliştirme eylemi bir saat içinde bir puan değişikliğiyle karşılaşırsa, bir uyarı oluşturulur.

- Bu uyarıların önem düzeyi **orta** düzeydedir.

- Kuruluşunuz için Genel Yönetici, uyarı bildirimlerinin varsayılan alıcısıdır.

- Aşağıdaki adımları izleyerek daha fazla uyarı alıcısı ekleyebilirsiniz:
    - **Uyarı ilkeleri** sayfasında **, Uyumluluk Yöneticisi varsayılan uyarı ilkesini** bulun.
    - Adının sol tarafındaki kutuyu işaretleyin ve filtrelerin üst kısmındaki **Düzenle** düğmesini seçin.
    - **Uyarı alıcıları** sayfasına gelene kadar **İleri** düğmesini seçin.
    - **+Alıcıları seç'i** seçin ve e-posta bildirimini almak istediğiniz açılır bölmede her kullanıcı adının yanındaki kutuları işaretleyin. İşiniz bittiğinde **Alıcı ekle'yi** ve ardından **İleri'yi** seçin.
    - **Değişikliklerinizi kaydetmek için Gözden geçir ve bitir** sayfasında **Güncelleştir'i** seçin.

- Varsayılan ilke silinemez, ancak [aşağıda açıklanan adımları izleyerek ilkeyi](#activate-or-inactivate-a-policy) devre dışı bırakabilirsiniz.


### <a name="policy-creation-steps"></a>İlke oluşturma adımları

Bir veya daha fazla olayı temel alan uyarılar oluşturmak üzere bir ilke oluşturmak için aşağıdaki adımları izleyin:

1. **Uyumluluk Yöneticisi'nde** **Uyarı ilkeleri** sayfasına gidin ve **+Ekle'yi** seçerek ilke oluşturma sihirbazını başlatın.

2. **Ad ve açıklama** sayfasında, ilke için bir ad ve isteğe bağlı bir açıklama girin ve **ardından İleri'yi** seçin.

3. **Koşullar** sayfasında, uyarı tetikleyecek bir veya daha fazla olayı seçin. **İyileştirme eylem etkinliği** üst bilgisi altında **Alt koşullar ekle'yi** seçin ve her koşul adının soluna geldiğinizde görüntülenen kutuyu işaretleyin. İlke için bir veya daha fazla koşul seçebilirsiniz: atama değişikliği, kanıt değişikliği, uygulama durumu değişikliği, puan değişikliği, test durumu değişikliği. İşiniz bittiğinde **İleri'yi** seçin.

4. **Sonuçlar** sayfasında, bir ilke eşleşmesi algılandığında ne olacağını seçin:
      - Eşleşme algılandığında uyarı için bir önem derecesi seçin: düşük, orta veya yüksek.
      - Eşleşme algılandığında ne sıklıkta e-postayla bildirim almak istediğinizi seçin. Her eşleşmede bildirim almayı seçebilir veya üç eşleşmenin üzerindeki belirli sayıda eşleşmenin eşiğini seçebilirsiniz.
      - Üç veya daha fazla eşleşmeden sonra bildirim almayı seçerseniz, bu eşiğe ulaşılması gereken dakika sayısını belirlersiniz (örneğin, 90 dakika içinde 4 eşleşme).
  
    İşiniz bittiğinde **İleri'yi** seçin.

5. **Uyarı alıcısı** sayfasında, ilke koşulları karşılandığında e-posta almak için kuruluşunuzdaki ek kullanıcıları seçin. İlkeyi oluşturan kullanıcı varsayılan alıcıdır. **+Alıcıları seç'i** seçin ve e-posta bildirimini almak istediğiniz açılır bölmede her kullanıcı adının yanındaki kutuları işaretleyin. İşiniz bittiğinde **Alıcı ekle'yi** ve ardından **İleri'yi** seçin.

6. Tüm seçimleri gözden geçirin ve öğesini seçip **İleri'yi** seçerek her bölümde değişiklik yapın. gözden geçirmeyi bitirdiğinizde **İlke oluştur'u** seçin.

7. İlkeniz oluşturulduğunda **Bitti'yi** seçin. Az önce oluşturduğunuz ilkenin açılır pencere bölmesinin açık olduğu **Uyarı ilkeleri** sayfanıza ulaşırsınız.

İlkenizi oluşturduktan sonra etkin hale gelir; bu da eşleşmeleri algılamaya ve uyarılar oluşturmaya başlayacağı anlamına gelir. **İlkeleri devre** dışı bırakma veya silme hakkında bilgi için aşağıdaki İlkeleri yönetme bölümüne bakın.

İlke oluşturulduktan veya güncelleştirildikten sonra, uyarılar bu ilke tarafından oluşturulmadan önce 24 saat kadar sürebilir. Olayları tetikleme ve uyarı toplama hakkında bilgi edinmek için aşağıdaki Uyarı [ayrıntılarını görüntüleme](#view-alert-details) bölümüne bakın.

## <a name="managing-policies"></a>İlkeleri yönetme

Uyarı ilkeleri sayfası, tüm **ilkelerinizin** bir tablo listesini içerir. Bu sayfayı daha fazla anlamak için [Uyarı ilkeleri sayfasına](#alert-policies-page) bakın. Kuruluşunuzdaki herhangi bir kullanıcı ilkeleri görüntüleyebilir, ancak bazı eylemler belirli rollerle sınırlıdır; Bkz [. Uyarı ilkesi izinleri](#alert-policy-permissions).

### <a name="view-policy-details"></a>İlke ayrıntılarını görüntüleme

**Uyarı ilkeleri** sayfasındaki satırından bir ilke seçerek eşleşme koşulları, uyarı bildirimlerinin gönderilip gönderilmediği ve kime gönderileceği ve önem derecesi düzeyi dahil olmak üzere ilkenin ayrıntılarını gösteren bir açılır panel açın.

Panelin alt kısmındaki **Eylemler** düğmesi, ilkeyi düzenleme, ilkeyi silme veya uyarıları görüntüleme seçenekleri sunar.

### <a name="view-a-policys-alerts"></a>İlke uyarılarını görüntüleme

İlkenin açılır panelinde **Eylemler'i** ve ardından **Uyarıları görüntüle'yi** seçin. Bu ilke tarafından oluşturulan tüm uyarıların filtrelenmiş bir görünümüyle doğrudan Uyarılar sayfasına yönlendirilirsiniz. [Uyarılarla çalışmayı](#viewing-and-managing-alerts) öğrenin.

### <a name="edit-a-policy"></a>İlkeyi düzenleme

İlkenin adı dışında herhangi bir yönünü düzenleyebilirsiniz. Adını değiştirmek istiyorsanız, yeni bir adla yeni bir ilke oluşturmanız gerekir.

İlkeyi düzenlemek için **Uyarı ilkeleri** sayfasında satırının üzerine geldiğinizde adının solunda görünen yuvarlak düğmeyi seçin ve filtrelerin üst kısmındaki **Düzenle** düğmesini seçin.

İlke oluşturma sihirbazına yönlendirilirsiniz. Burada ilkenizde değişiklik yapabilir ve değişiklikleri kaydedebilirsiniz.  Ayrıca, ayrıntılar panelini açmak için ilkeyi seçebilir ve **Eylemler** düğmesinden **İlkeyi düzenle'yi** seçebilirsiniz. Sihirbazda yeniden çalıştıktan sonra seçimlerinizi gözden geçirin ve son adımda **Güncelleştir'i** seçerek değişikliklerinizi kaydedin.

Uyarıların güncelleştirilmiş ilke tarafından oluşturulması 24 saat kadar sürebilir.

### <a name="activate-or-inactivate-a-policy"></a>İlkeyi etkinleştirme veya devre dışı bırakma

İlkeler oluşturulur oluşturulmaz varsayılan olarak etkinleştirilir. Etkin olduğunda, ilke koşullar karşılandığında bir uyarı oluşturur ( **Uyarılar** sayfasında gösterilir) ve belirlenen alıcılara bir bildirim e-postası gönderir.

İlkeyi **etkin olmayan** bir duruma değiştirmek için ( yani uyarı oluşturmaz), satırının üzerine geldiğinizde ilke adının solunda görünen yuvarlak düğmeyi seçin. Ardından tablonun üst kısmındaki **Devre Dışı Bırak** komutunu seçin. İlkenizin durumu artık Etkin Değil olarak okunur. İlkeyi yeniden etkinleştirmek için aynı işlemi izleyin ve filtrelerin üstündeki **Etkinleştir** düğmesini seçin.

### <a name="delete-a-policy"></a>İlke silme

İlkeyi silmek için **Uyarı ilkeleri** sayfasında adının yanındaki düğmeyi ve sayfanın üst kısmındaki **Sil'i** seçebilirsiniz. Ayrıca ilkeyi seçerek ayrıntılar panelini açabilir ve **Eylemler** düğmesinden **İlkeyi sil'i** seçebilirsiniz.

Silme kalıcıdır. Bir ilkeyi sildiğinizde, artık uyarılar veya e-posta bildirimleri oluşturmaz. [Silinen ilkelere bağlı uyarılar](#when-policies-are-deleted) hakkında daha fazla bilgi edinin.

## <a name="viewing-and-managing-alerts"></a>Uyarıları görüntüleme ve yönetme

**Uyarılar** sayfasında, tüm ilkeleriniz tarafından oluşturulan tüm uyarıları içeren bir tablo gösterilir. Uyarılar, ilkenin koşullarıyla eşleşen bir olay gerçekleştikten hemen sonra oluşturulur. Uyarı adı, uyarıyı oluşturan ilkeyle aynı addır.

Uyarı yalnızca etkin bir ilkeden oluşturulabilir. Bir uyarı oluşturulduktan sonra, ilkenin etkin veya etkin olmaması fark etmeksizin **Uyarılar** sayfasında listelenir.

### <a name="filter-your-view-of-alerts"></a>Uyarı görünümünüzü filtreleme
**Uyarılar** sayfanızdaki tablonun üstündeki **Filtre** komutunu seçerek uyarı görünümünüzü filtreleyebilirsiniz. **Filtre** açılır listesinden şu filtre seçenekleri arasından seçim yapın:

- Olay türü
- Önem derecesi
- Durum
- Atanan kullanıcı
- Algılama tarihi
- İlke adı

Seçimlerinizi yaptıktan sonra **Uygula'yı** seçin. Açılır pencere bölmesi kapatılır ve güncelleştirilmiş **Uyarılar** sayfanız filtrelenmiş görünümünüzü gösterir. Filtreleriniz tablonun en üstünde görüntülenir, ancak tüm filtre sütunları tabloda gösterilmeyebilir.

### <a name="view-alert-details"></a>Uyarı ayrıntılarını görüntüleme

Uyarıyı tetikleyen olaylar da dahil olmak üzere uyarıyla ilgili tüm ayrıntıları görüntülemek için tablodaki satırını seçin. Açılır bölme, panelin **Genel Bakış** sekmesinde uyarının ayrıntılarını gösterir.

Açılır bölmenin **Olaylar günlüğü** sekmesinde, uyarıyı oluşturan puan değişikliği veya atama değişikliği gibi etkinliklerin yanı sıra her eylemle ilişkili kullanıcının adı ve algılanan tarih listelenir.

### <a name="alert-events"></a>Uyarı olayları

**Uyarılar** sayfasındaki **Olaylar** sütunu, algılanan bir ilkenin koşullarını gösterir; başka bir deyişle, uyarıyı oluşturan etkinlik. Uyarının ayrıntılar panelindeki **Olaylar günlüğü** sekmesi bir olayın her örneğini, ilişkili kullanıcıyı ve algılanan tarihi listeler. Olay değerleri aşağıda listelenmiştir:

- **Puan değişikliği**: Puan artış veya düşüş sayısını gösterir
- **Atama değişikliği**: Kullanıcıya bir iyileştirme eylemi atandı, farklı bir kullanıcıya yeniden atandı veya kullanıcıdan atanmadı
- **Uygulama durumu değişikliği**: Kullanıcı geliştirme eyleminin uygulama durumunu değiştirdi
- **Test durumu değişikliği**: Kullanıcı, geliştirme eyleminin test durumunu değiştirdi.
- **Kanıt değişikliği**: Bir kullanıcı, geliştirme eyleminin Belgeler sekmesindeki bir kanıt belgesini karşıya yüklemiş veya silmiş
- **Çok olaylı**: Aynı olay türünün birden çok örneği algılandı; örneğin, birden çok kez yeniden atanan tek bir iyileştirme eylemi
- **Çok koşullu**: Tek bir ilke içinde birden çok koşul algılandı

#### <a name="alert-aggregation-for-multiple-events-within-one-minute"></a>Bir dakika içinde birden çok olay için uyarı toplama

Bir uyarı ilkesinin koşullarıyla eşleşen birden çok olay bir dakika içinde gerçekleştiğinde, bunlar uyarı toplama adlı bir işlem tarafından var olan bir uyarıya eklenir.

Örneğin, bir ilkeyle eşleşen bir olay gerçekleştiğinde, **Uyarılar** sayfasında bir uyarı oluşturulur ve görüntülenir ve bir bildirim gönderilir. İlk olayın bir dakika içinde aynı ilkeyle eşleşen başka bir olay oluşursa, Uyumluluk Yöneticisi yeni bir uyarı tetikleme yerine mevcut uyarının **Olaylar günlüğü** sekmesinde ek olayla ilgili ayrıntıları ekler. Uyarı toplamanın amacı, uyarı "yorgunluğunu" azaltmaya yardımcı olmak ve daha az uyarıya odaklanmanızı ve eylem gerçekleştirmenizi sağlamaktır.

### <a name="taking-action-on-alerts"></a>Uyarılarda eylem gerçekleştirme

İlkelerinizden biri uyarı oluşturduğunda, uyarıya neden olan olayları görüntüleyebilir ve olayları doğrulamanız mı yoksa daha fazla araştırmanız mı gerektiğini belirleyebilirsiniz.

Bir uyarı üzerinde işlem yapmak için **Uyarılar** sayfasındaki satırını seçerek açılır paneli ayrıntılarıyla birlikte getirin, **Eylemler** düğmesini seçin ve aşağıda listelenen seçenekler arasından seçim yapın. Ayrıca, satırının üzerine geldiğinizde uyarı adının solunda görünen yuvarlak düğmeyi seçerek ve filtrelerin üstündeki sayfanın üst kısmındaki eylem düğmelerinden birini seçerek de eylemler gerçekleştirebilirsiniz.

**Uyarı atama**: Uyarıya neden olan olayları araştırmak veya doğrulamak için uyarıyı kullanıcıya atamak isteyebilirsiniz. Bu seçeneği belirlediğinizde, kuruluşunuzdaki bir kullanıcıyı seçebileceğiniz ve uyarıyı ona atayabileceğiniz bir panel açılır. Uyarılar sayfasında **Filtreler'i** seçip **Atanan** alanına kullanıcının adını girerek **uyarı** görünümünüzü filtreleyebilirsiniz.

**E-posta uyarısı**: Eylemin gerçekleştiğini onaylamak için uyarının etkinliğiyle ilişkili kullanıcıya bir e-posta göndermek isteyebilirsiniz. Bu seçeneği belirttiğinizde uyarıyla ilgili temel bilgileri içeren bir e-posta şablonu açar. Bu şablonu daha fazla yönergeyle özelleştirebilir ve kullanıcıya gönderebilirsiniz.

**İlke ayrıntılarını görüntüleme**: Uyarıyı tetikleyen ilkenin ayarlarını gözden geçirmek isteyebilirsiniz. Bu seçeneği belirlediğinizde, ilke ayrıntıları panelinin zaten açık olduğu **Uyarı ilkeleri** sayfasına doğrudan yönlendirilirsiniz. İlke ayrıntıları panelini kapattığınızda artık **Uyarılar** sayfanızda olmayacaksınız.

**Değişiklik durumu**: Uyarınızın etkisini gözden geçirmenize ve araştırılması gerekip gerekmediğine bağlı olarak uyarınızın durumunu güncelleştirebilirsiniz. Sonraki bölümde uyarı durumları hakkında daha fazla bilgi edinin.

### <a name="alert-status"></a>Uyarı durumu

Bir uyarı oluşturulduğunda, durumu **Etkin** olur. Her uyarının ayrıntılarını gözden geçirirken, uyarının durumunu aşağıda listelenen durumlardan herhangi birine güncelleştirebilirsiniz:

- **Etkin**: Durumu değiştirilene kadar uyarının varsayılan durumu
- **Araştırma**: uyarı araştırılıyor
- **Çözüldü**: Uyarı daha fazla araştırma veya takip gerektirmez
- **Kapatıldı**: Uyarı ilgili değil veya araştırılma ihtiyacı yok

Uyarının durumunu atamak veya değiştirmek için, tablodaki satırından bir uyarı seçin, sayfanın üst kısmındaki filtrelerin üstündeki **Durumu değiştir'i** seçin. Uyarı durumunu güncelleştir açılır penceresinden açılan menüden bir durum seçin ve ardından **Uyarıyı güncelleştir'i** seçin.

Bir uyarı oluşturulduktan sonra, durumu uyarıyı oluşturan ilkenin durumundan bağımsızdır. Örneğin, **etkin olmayan** bir ilkeyle ilişkilendirilmiş **etkin** bir uyarı olabilir ve daha sonra devre dışı bırakılmış veya silinmiş bir ilke tarafından oluşturulan bir uyarıda **araştırma** durumu olması mümkündür.

### <a name="when-policies-are-deleted"></a>İlkeler silindiğinde

İlke silindiğinde, bu ilke tarafından oluşturulan tüm uyarılar **Uyarılar** sayfanızda kalır, ancak yeni uyarı oluşturulmaz.

## <a name="email-notifications-of-alerts"></a>Uyarıların e-posta bildirimleri

İlke oluşturduğunuzda, ilkeyi oluşturan kullanıcıya bir eşleşme algılandığını belirten bir e-posta gönderilir. Bu e-posta bildirimlerini kuruluşunuzdaki diğer kullanıcılara göndermeyi seçebilirsiniz. Uyarılar neredeyse gerçek zamanlı olarak gerçekleşir ve bir uyarı oluşturulur oluşturulmaz e-posta bildirimleri gönderilir. E-posta olay adını, önem derecesini, algılanan zamanı ve uyarıyı Uyumluluk Yöneticisi'nde görüntüleme bağlantısını içerir.

### <a name="remove-users-from-receiving-alerts"></a>Kullanıcıların uyarı almasını kaldırma

Uyarı alıcılarını belirler ve daha sonra kaldırmaya karar verirseniz aşağıdaki adımları izleyin. İlke eşleşmeleri algılandığında ilkeyi oluşturanın e-posta bildirimleri almaya devam edeceğine dikkat edin.

1. [İlkenizi düzenleme adımlarını](#edit-a-policy) başlatın.
2. **Uyarı alıcıları** ekranına geldiğinizde **+Alıcıları seç'i** seçin.
3. **Alıcıları seçin** açılır panelinde, bildirimlerden kaldırmak istediğiniz kullanıcıyı bulun ve adının solundaki kutunun işaretini kaldırın, ardından **Alıcı ekle** düğmesini seçin (seçiminizi kaydetme etkisi olur).
4. Sihirbaz aracılığıyla devam edin ve kullanıcının Gözden Geçir ve bitir sayfasındaki **Alıcılar** altında görünmediğini onaylayın. Ayarlarınızı kaydetmek ve bitirmek için **Güncelleştir'i** seçin.
