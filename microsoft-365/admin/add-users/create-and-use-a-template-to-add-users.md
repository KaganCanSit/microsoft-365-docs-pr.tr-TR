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
description: Birden çok kullanıcı eklerken zaman kazanmak ve ayarları standart hale yapmak için bir şablon oluşturabilir ve kullanabilirsiniz.
ms.openlocfilehash: cacb3fc6ef2a145cbfe4c4131b2e5e38eca2c257
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983734"
---
# <a name="create-and-use-a-template-to-add-users"></a>Kullanıcıları eklemek için şablon oluşturma ve kullanma

Birden çok kullanıcı eklerken zaman kazanmak ve ayarları standartleştirmek için bir şablon oluşturabilir ve kullanabilirsiniz. Şablonlar, aynı role sahip olan ve aynı konumda çalışan kullanıcılar ve aynı yazılım gerektirenler gibi birçok ortak özelliği paylaşan kullanıcılarınız varsa özellikle kullanışlıdır. Örneğin, aynı ofiste çalışan bir destek mühendisleri ekibine sahipsiniz olabilir.  

## <a name="create-a-template"></a>Şablon oluşturma

 >  > &mdash;Şablonlar kolayca oluşturabilirsinizKullanıcılarıKullanıcı kullanıcılar'ı seçebilirsiniz ve sonra açılan listeden Şablon ekle'yi seçebilirsiniz veya yeni kullanıcı ekleyebilirsiniz ve bitirdikten sonra girdiyi şablon olarak kaydetme seçeneğiniz olur.

Kullanıcı ekledikten sonra bir şablon sanız, aşağıdaki ayarlar için seçtiğiniz değerler şablona kaydedilir:

- Etki alanı adı
- Parola ayarları seçimi: Parolaları oluşturmayı veya bunları otomatik olarak oluşturmalarını sebilirsiniz
- Tek seferlik parola seçimi: İlk oturum açmadan sonra kullanıcının yeni parola oluşturmasını gerektirmeniz gerekir
- Lisans konumu
- Lisans seçenekleri
- Uygulama seçenekleri
- Rol
- İş profili, Bölüm, **posta adresi**, **telefon** **Office** **adresi Office profil** **bilgileri** 

Aşağıdaki bilgiler kullanıcıya özeldir ve şablona kayıtlı değil:

- Ad ve soyadı
- Görünen ad
- Kullanıcı adı
- Parolayı e-postayla gönderme seçimi ve parola e-postanın kime gönderildiği
- Cep telefonu numarası

Bir bölümün içindeki bir ayar için bilgi girmeyseniz, bu değer boş olur ve bu ayar şablonda görüntülenmez. Örneğin, İş unvanını **boş** bırakırsanız, şablonu gözden geçirebilirsiniz ve şablon kullanınca **, İş** unvanı hiç görünmez. Tüm Profil bölümü ayarlarını **boş** bırakırsanız, **Profil bölümünde** son şablonunda **Sağ yok** görüntülenir.

Şablon ekle seçeneğini seçerek **bir şablon oluşturursanız** , hangi değerlerin tamamlandırıcanı seçebilirsiniz. Boş olarak kalan her şey, **şablonda Yok olarak** görünür.

## <a name="use-a-template-to-add-a-user"></a>Kullanıcı eklemek için şablon kullanma

Var olan bir şablonu kullanarak kullanıcı eklemek için:

1. Yönetim merkezinde **UsersActive** >  **users öğesini seçin**.

2. Kullanıcı **şablonları'ı** seçin ve ardından açılan listeden bir şablon seçin. (Liste, diğer yöneticilerin oluşturduğu şablonları değil yalnızca sizin oluşturduğunuz şablonları içerir.)

   > [!NOTE]
   > Ayrıca, Kullanıcı şablonları'ı  >  seçerek şablon eklemek için de şablon kullanabilirsinizSesk şablonlarınylarını seçin, bir şablon seçin ve ardından Şablonu **kullan'ı seçin**.

3. Seçtiğiniz şablondan kullanıcı oluşturmak için adımları izleyin.

   > [!NOTE]
   > Ekleyilen kullanıcı için yeterli lisansınız yoksa ve ödeme bilginiz varsa, mevcut ödeme bilgilerinizi kullanarak başka bir lisans satın almak için çalışmamız gerekir. Ödeme bilgileri kullanılamıyorsa kullanıcı lisanssız kullanıcı olarak oluşturulur.

## <a name="manage-templates"></a>Şablonları yönetme

Yalnızca artık ihtiyacınız olmadığınız şablonları silebilir ve yenilerini  eklersiniz. Şablonu silmek için:

1. Yönetim merkezinde **UsersActive** >  **users öğesini seçin**.

2. **Şablonlar'ı** seçin ve ardından **açılan listeden** Şablonları yönet'i seçin.

3. Şablonların listesi görüntülenir. Şablon silmek için şunları yapabilirsiniz:
    - Bir veya daha fazla şablon seçin ve sonra da Sil'i **seçin**. 
    - Şablon adının sağ üç noktayı seçin ve sonra da Sil'i **seçin**.
    - Şablon adını seçin. Şablon ayrıntıları ekrannizin sağ tarafında görüntü olduğunda Şablonu **sil'i seçin**.

## <a name="related-articles"></a>İlgili makaleler

[Kullanıcıları ekleme ve lisansları aynı anda atama](add-users.md)

[Eski bir çalışanı iş yerlerinden Microsoft 365](remove-former-employee.md)
  
