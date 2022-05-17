---
title: Kullanıcıları eklemek için şablon oluşturma ve kullanma
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
description: Zaman kazanmak ve Microsoft 365 yönetim merkezi birden çok kullanıcı eklediğinizde ayarları standartlaştırmak için şablon oluşturup kullanabilirsiniz.
ms.openlocfilehash: 0f0d737bcf600acb4084c5e2b85e5595c6387fee
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437001"
---
# <a name="create-and-use-a-template-to-add-users"></a>Kullanıcıları eklemek için şablon oluşturma ve kullanma

Birden çok kullanıcı eklerken zaman kazanmak ve ayarları standartlaştırmak için şablon oluşturup kullanabilirsiniz. Şablonlar özellikle aynı role sahip olan ve aynı konumda çalışan ve aynı yazılıma ihtiyaç duyan kullanıcılar gibi birçok ortak özelliği paylaşan kullanıcılarınız varsa kullanışlıdır. Örneğin, aynı ofiste çalışan bir destek mühendisleri ekibiniz olabilir.  

## <a name="create-a-template"></a>Şablon oluşturma

Şablonlar kolayca oluşturulabilir&mdash; **KullanıcılarAkullanıcılarKullanıcılarKullanıcılar'ı** >  >  seçip açılan listeden **Şablon ekle'yi** seçebilir veya yeni bir kullanıcı ekleyebilirsiniz ve işiniz bittiğinde girişi şablon olarak kaydetme seçeneğiniz olur.

Kullanıcı ekledikten sonra şablon oluşturduğunuzda, aşağıdaki ayarlar için seçtiğiniz değerler şablona kaydedilir:

- Etki alanı adı
- Parola ayarları seçimi: Parola oluşturmayı veya otomatik olarak oluşturulmasını seçebilirsiniz
- Tek seferlik parola seçimi: kullanıcının ilk oturum açma işleminden sonra yeni parola oluşturmasını zorunlu kılabilir
- Lisans konumu
- Lisans seçenekleri
- Uygulama seçenekleri
- Rol
- **İş profili**, **Departman**, **Office, Office** **telefon** ve **Sokak adresi** gibi profil bilgilerinin çoğu 

Aşağıdaki bilgiler kullanıcıya özgüdür ve şablona kaydedilmez:

- Ad ve soyadı
- Görünen ad
- Kullanıcı adı
- Parolayı e-postayla gönderme ve parola e-postasının kime gönderildiğini seçme
- Cep telefonu numarası

Bir bölümdeki bir ayarın bilgilerini girmemeyi seçerseniz, bu değer boş olur ve bu ayar şablonda görüntülenmez. Örneğin, **İş başlığını** boş bırakırsanız, şablonunuzu gözden geçirirken ve şablonunuzu kullanırken **İş başlığı** hiç görünmez. Tüm **Profil** bölümü ayarlarını boş bırakırsanız, **Profil** bölümü son şablonunuzda **Sağlanmadı** ifadesini görüntüler.

Şablon **ekle** seçeneğini belirleyerek şablon oluşturduğunuzda, hangi değerlerin tamamlanacağını seçebilirsiniz. Boş bırakılan her şey şablonda **Hiçbiri sağlandı** olarak görünür.

## <a name="use-a-template-to-add-a-user"></a>Kullanıcı eklemek için şablon kullanma

Var olan bir şablonu kullanarak kullanıcı eklemek için:

1. Yönetim merkezinde **KullanıcılarEtkin** >  kullanıcılar'ı seçin.

2. **Kullanıcı şablonları'nı** seçin ve ardından açılan listeden bir şablon seçin. (Liste, diğer yöneticiler tarafından oluşturulan şablonları değil, yalnızca sizin oluşturduğunuz şablonları içerir.)

   > [!NOTE]
   > Ayrıca, **Kullanıcı şablonları** >  Şablon yönet'i seçip bir şablon seçip Şablonu kullan'ı seçerek de **bir şablon** kullanabilirsiniz.

3. Seçtiğiniz şablondan kullanıcı oluşturmak için adımları izleyin.

   > [!NOTE]
   > Eklediğiniz bir kullanıcı için kullanılabilir lisanslarınız yetersizse ve ödeme bilgileriniz kullanılabilir durumdaysa, mevcut ödeme bilgilerinizi kullanarak başka bir lisans satın alma girişiminde bulunacağız. Ödeme bilgileriniz kullanılamıyorsa, kullanıcı lisanssız kullanıcı olarak oluşturulur.

## <a name="manage-templates"></a>Şablonları yönetme

Yalnızca artık ihtiyacınız olmayan şablonları silebilir ve yenilerini ekleyebilirsiniz. Şablonu silmek için:

1. Yönetim merkezinde **KullanıcılarEtkin** >  kullanıcılar'ı seçin.

2. **Şablonlar'ı** ve ardından açılan listeden **Şablonları yönet'i** seçin.

3. Şablonların listesi görüntülenir. Aşağıdakilerden birini yaparak şablonu silebilirsiniz:
    - Bir veya daha fazla şablon seçin ve ardından **Sil'i** seçin. 
    - Şablon adının sağındaki üç noktayı ve ardından **Sil'i** seçin.
    - Şablon adını seçin. Şablon ayrıntıları ekranınızın sağ tarafında göründüğünde **Şablonu sil'i** seçin.

## <a name="related-articles"></a>İlgili makaleler

[Aynı anda kullanıcı ekleme ve lisans atama](add-users.md)

[eski çalışanı Microsoft 365 kaldırma](remove-former-employee.md)
  
