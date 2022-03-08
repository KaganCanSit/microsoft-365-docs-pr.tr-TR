---
title: Bağlan için Amazon Web Services'da (AWS) DNS kayıtlarınızı Microsoft 365
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 7a2efd75-0771-4897-ba7b-082fe5bfa9da
description: Microsoft için Amazon Web Services'de (AWS) etki alanlarınızı doğrulamayı ve e-posta, Skype Kurumsal Online ve diğer hizmetler için DNS kayıtlarını ayarlamayı öğrenin.
ms.openlocfilehash: 49b2d36c6902617238973099621b59aba7dbc58e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313573"
---
# <a name="connect-your-dns-records-at-amazon-web-services-aws-to-microsoft-365"></a>Bağlan için Amazon Web Services'da (AWS) DNS kayıtlarınızı Microsoft 365

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**. 
  
AWS sizin DNS barındırma sağlayıcınızsa, bu makaledeki adımları kullanarak etki alanlarınızı doğrulayın ve e-posta, Skype Online for Business, gibi DNS kayıtlarını ayarlayın.
  
AWS'ye bu kayıtları ekledikten sonra, etki alanınız etki alanınız etki alanınız Microsoft hizmetleri.
  
> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlar ile ilgili sorunlar için bkz. Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra [sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Doğrulama için bir TXT kaydı ekleme

Etki alanınızı Microsoft ile kullanmadan önce bu etki alanına sahip olduğundan emin olarız. Etki alanı kayıt şirketinizin hesabında oturum açabilme ve DNS kaydı oluşturabilme özelliği, Microsoft'a etki alanının sahibi olduğunu kanıtlar.
  
> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. Dilerseniz bu kaydı daha sonra silebilirsiniz. 
  
1. Başlamak için [bu bağlantıyı](https://console.aws.amazon.com/route53/home) kullanarak AWS'deki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

1. Giriş sayfasındaki Etki Alanları'nın **altında Kayıtlı** etki **alanları'na tıklayın**.

1. Etki **Alanı Adı** altında, etki alanında ayarlamak istediğiniz etki Microsoft 365.

    **Not**: Etki alanınız için barındırılan bir bölge oluşturmadısanız, Barındırılan bölge  oluştur'u seçin ve sonraki adıma ilerlemeden önce adımları tamamlayın. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Doğrulamak istediğiniz etki alanının adını seçin.":::

1. **DNS'yi Yönet'i seçin**. 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::

1. Etki **alanı adı** altında, doğrulamak istediğiniz etki alanının barındırılan bölge sürümünün etki alanı adını seçin.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Doğrulamak istediğiniz etki alanının adını seçin.":::

1. Kayıt **oluştur'a seçin**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Kayıt oluştur'a seçin.":::

1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

    (Açılır **listelerden** **Tür ve** Yönlendirme ilke değerlerini seçin.)

    > [!TIP]
    > Ekrandaki yönergeler tarafından gereken tırnak işaretleri otomatik olarak gelir. Bunları el ile yazmanız gerekmez. 
  
    ||||||
    |:-----|:-----|:-----|:-----|:-----|
    |**Kayıt adı** <br/> |**Kayıt türü** <br/> |**Değer** <br/> |**TTL (Saniye)** <br/> |**Yönlendirme ilkesi** <br/> |
    |(Bu alanı boş bırakın.)  <br/> |TXT - E-posta gönderenleri doğrulamak için kullanılır  <br/> |MS=ms *XXXXXXXX*  <br/>**Not:** Bu bir örnektir. Hedef veya Adres **Noktaları değerinizi burada**, hedef tablodaki Microsoft 365. [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md) |300  <br/> |Basit  <br/> |

1. Kayıt **oluştur'a seçin**.

   :::image type="content" source="../../media/dns-aws/aws-domains-txt-create-records.png" alt-text="Kayıt oluştur'a seçin.":::

   Yeni oluşturduğunuz kaydın İnternet genelinde güncelleştirilebilmesi için devam etmeden önce birkaç dakika bekleyin.

Kaydı etki alanı kayıt şirketinizin sitesinde eklediknize göre, Microsoft'a geri dönüp kayıt için arama isteğinde bulundurabilirsiniz. Microsoft doğru TXT kaydını bulduğunda, etki alanınız doğrulanır.

Bir dosyada kaydı Microsoft 365:
  
1. Yönetim merkezinde Etki Alanları'nın **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**gidin**</a>.

1. Etki Alanları sayfasında, doğrulamakta olduğunuz etki alanını seçin ve sonra da Kurulumu **başlat'ı seçin**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. **Devam'ı seçin**.
  
1. Etki alanını **doğrulama sayfasında** Doğrula'ya **tıklayın**.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlar ile ilgili sorunlar için bkz. Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra [sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft-365"></a>Etki alanınıza gelen e-postanın E-posta'ya gelip gelmeleri için MX kaydı Microsoft 365

1. Başlamak için [bu bağlantıyı](https://console.aws.amazon.com/route53/home) kullanarak AWS'deki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

1. Giriş sayfasındaki Etki Alanları'nın **altında Kayıtlı** etki **alanları'na tıklayın**.

1. Etki **Alanı Adı** altında, etki alanında ayarlamak istediğiniz etki Microsoft 365.

    **Not**: Etki alanınız için barındırılan bir bölge oluşturmadısanız, Barındırılan bölge  oluştur'u seçin ve sonraki adıma ilerlemeden önce adımları tamamlayın. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Etki alanının adını seçin.":::

1. **DNS'yi Yönet'i seçin**. 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::

1. Etki **alanı adı** altında, doğrulamak istediğiniz etki alanının barındırılan bölge sürümünün etki alanı adını seçin.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Etki alanının adını seçin.":::

1. Kayıt **oluştur'a seçin**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Kayıt oluştur'a seçin."::: 

1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın. 

    (Açılır **listelerden** **Tür ve** Yönlendirme ilke değerlerini seçin.) 

    > [!TIP]
    > Ekrandaki yönergeler tarafından gereken tırnak işaretleri otomatik olarak gelir. Bunları el ile yazmanız gerekmez. 

    |**Kayıt adı**|**Kayıt türü**|**Değer**|**TTL (Saniye)**|**Yönlendirme ilkesi**|
    |:-----|:-----|:-----|:-----|:-----|
    |(Bu alanı boş bırakın.)  <br/> |MX - Posta sunucularını belirtir  <br/> |0,mail.protection.outlook.com  *\<domain-key\>*  .  <br/> Burada 0, MX öncelik değeridir. Bu değeri MX değerinin başına ekleyin ve değerin kalan bölümünden bir boşlukla ayırın.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> **Not:** Hesap hesabınızdan \<*domain-key*\> Microsoft 365. [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md) | 300  <br/> | Basit yönlendirme <br/> |
  
1. Kayıt **oluştur'a seçin**.

   :::image type="content" source="../../media/dns-aws/aws-domains-mx-create-records.png" alt-text="Kayıt oluştur'a seçin.":::

1. Başka MX kayıtları varsa, kaydı seçerek ve sonra da Sil'i seçerek bunları **kaldırın**.
  
## <a name="add-the-cname-record-required-for-microsoft-365"></a>Adlar için gereken CNAME kaydını Microsoft 365

1. Başlamak için [bu bağlantıyı](https://console.aws.amazon.com/route53/home) kullanarak AWS'deki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

1. Giriş sayfasındaki Etki Alanları'nın **altında Kayıtlı** etki **alanları'na tıklayın**.

1. Etki **Alanı Adı** altında, etki alanında ayarlamak istediğiniz etki Microsoft 365.

    **Not**: Etki alanınız için barındırılan bir bölge oluşturmadısanız, Barındırılan bölge  oluştur'u seçin ve sonraki adıma ilerlemeden önce adımları tamamlayın. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Etki alanının adını seçin.":::

1. **DNS'yi Yönet'i seçin**. 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::

1. Etki **alanı adı** altında, doğrulamak istediğiniz etki alanının barındırılan bölge sürümünün etki alanı adını seçin.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Etki alanının adını seçin.":::

1. Kayıt **oluştur'a seçin**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Kayıt oluştur'a seçin.":::

1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın. 

    (Açılır **listelerden** **Tür ve** Yönlendirme ilke değerlerini seçin.) 

    |**Kayıt adı**|**Kayıt türü**|**Değer**| **TTL** |**Yönlendirme ilkesi**|
    |:-----|:-----|:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME - Trafiği başka bir etki alanı adına yollar  <br/> | autodiscover.outlook.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> | 300  <br/> |Basit  <br/> |
  
1. Kayıt **oluştur'a seçin**.

   :::image type="content" source="../../media/dns-aws/aws-domains-cname-create-records.png" alt-text="Kayıt oluştur'a seçin.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa Microsoft için yeni bir SPF kaydı oluşturun. Bunun yerine, her iki değer kümesi de içeren tek  *bir SPF*  kaydına sahip olmak için gerekli Microsoft değerlerini geçerli kayda ekleyin. Örneklere mi ihtiyacınız var? Microsoft için bu [Dış Etki Alanı Adı Sistemi kayıtlarına göz atabilirsiniz](../../enterprise/external-domain-name-system-records.md). SPF kaydınızı doğrulamak için şuSPF doğrulama araçlarından [birini kullanabilirsiniz](../setup/domains-faq.yml). 
  
1. Başlamak için [bu bağlantıyı](https://console.aws.amazon.com/route53/home) kullanarak AWS'deki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

1. Giriş sayfasındaki Etki Alanları'nın **altında Kayıtlı** etki **alanları'na tıklayın**.

1. Etki **Alanı Adı** altında, etki alanında ayarlamak istediğiniz etki Microsoft 365.

    **Not**: Etki alanınız için barındırılan bir bölge oluşturmadısanız, Barındırılan bölge  oluştur'u seçin ve sonraki adıma ilerlemeden önce adımları tamamlayın. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Etki alanının adını seçin.":::

1. **DNS'yi Yönet'i seçin**. 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::

1. Etki **alanı adı** altında, doğrulamak istediğiniz etki alanının barındırılan bölge sürümünün etki alanı adını seçin.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Etki alanının adını seçin.":::

1. Kayıt **oluştur'a seçin**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Kayıt oluştur'a seçin.":::

1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın. 

    (Açılan **listelerden** Tür değerini seçin.) 

    |**Kayıt türü** | **Değer**|
    |:-----|:-----|
    |TXT- E-posta gönderenlerini ve uygulamaya özgü değerleri doğrulamak için kullanılır |v=spf1 include:spf.protection.outlook.com -all  <br/> (Ekrandaki yönergeler için gereken tırnak işaretleri otomatik olarak gelir. Bunları el ile yazmanız gerekmez.)  <br/> **Not:** Tüm boşlukların doğru kalması için bu girdiyi kopyalayıp yapıştırarak bu dosyayı yapıştırın.   |
  
1. Kayıt **oluştur'a seçin**.

   :::image type="content" source="../../media/dns-aws/aws-domains-txt-create-records.png" alt-text="Kayıt oluştur'a seçin.":::

## <a name="advanced-option-skype-for-business"></a>Gelişmiş seçenek: Skype Kurumsal

Yalnızca, bu seçeneği yalnızca, Skype Kurumsal yanı sıra sohbet, konferans aramaları ve görüntülü aramalar gibi çevrimiçi iletişim hizmetleri için Microsoft Teams. Skype için 4 kayıt gerekir: Oturum açma ve kullanıcıları hizmete bağlamak için 2 kullanıcı-kullanıcı iletişim için SRV kaydı ve 2 CNAME kaydı.

### <a name="add-the-two-required-srv-records"></a>Gerekli iki SRV kaydı ekleme

1. Başlamak için [bu bağlantıyı](https://console.aws.amazon.com/route53/home) kullanarak AWS'deki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

1. Giriş sayfasındaki Etki Alanları'nın **altında Kayıtlı** etki **alanları'na tıklayın**.

1. Etki **Alanı Adı** altında, etki alanında ayarlamak istediğiniz etki Microsoft 365.

    **Not**: Etki alanınız için barındırılan bir bölge oluşturmadısanız, Barındırılan bölge  oluştur'u seçin ve sonraki adıma ilerlemeden önce adımları tamamlayın. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Etki alanının adını seçin.":::

1. **DNS'yi Yönet'i seçin**. 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::

1. Etki **alanı adı** altında, doğrulamak istediğiniz etki alanının barındırılan bölge sürümünün etki alanı adını seçin.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Etki alanının adını seçin.":::

1. Kayıt **oluştur'a seçin**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Kayıt oluştur'a seçin."::: 

1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın. 

    (Açılır listelerden **Tür** ve **Yönlendirme İlkesi** değerlerini seçin.) 

    |**Kayıt adı**|**Kayıt türü**|**Değer**|**TTL (Saniye)**|**Yönlendirme ilkesi**|
    |:-----|:-----|:-----|:-----|:-----|
    |_sip._tls|SRV - Kimlik sunucularının uygulamaya özgü değerleri|100 1 443 sipdir.online.lync.com. **Bu değer nokta (.) ile bitMİ OLMALı**><br> **Not:** Tüm boşlukların doğru kalması için bu girdiyi kopyalayıp yapıştırarak bu dosyayı yapıştırın. | 300 |Basit|
    |_sipfederationtls._tcp|SRV - Kimlik sunucularının uygulamaya özgü değerleri|100 1 5061 sipfed.online.lync.com. **Bu değer nokta (.) ile bitmelidir.**<br> **Not:** Tüm boşlukların doğru kalması için bu girdiyi kopyalayıp yapıştırarak bu dosyayı yapıştırın.    | 300 |Basit|
  
1. Diğer SRV kaydını eklemek için Başka bir kayıt ekle'yi **seçin,** tablonun bir sonraki satırına gelen değerleri kullanarak kaydı oluşturun ve sonra yeniden Kayıt oluştur'a **tıklayın**. 

   :::image type="content" source="../../media/dns-aws/aws-domians-srv-create-records.png" alt-text="Kayıt oluştur'a seçin.":::

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlar ile ilgili sorunlar için bkz. Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra [sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydı ekleme 

1. Başlamak için [bu bağlantıyı](https://console.aws.amazon.com/route53/home) kullanarak AWS'deki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

1. Giriş sayfasındaki Etki Alanları'nın **altında Kayıtlı** etki **alanları'na tıklayın**.

1. Etki **Alanı Adı** altında, etki alanında ayarlamak istediğiniz etki Microsoft 365.

    **Not**: Etki alanınız için barındırılan bir bölge oluşturmadısanız, Barındırılan bölge  oluştur'u seçin ve sonraki adıma ilerlemeden önce adımları tamamlayın.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Etki alanının adını seçin.":::

1. **DNS'yi Yönet'i seçin**. 

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::

1. Etki **alanı adı** altında, doğrulamak istediğiniz etki alanının barındırılan bölge sürümünün etki alanı adını seçin.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Etki alanının adını seçin.":::

1. Kayıt **oluştur'a seçin**. 

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Kayıt oluştur'a seçin.":::

1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

    (Açılır **listelerden** **Tür ve** Yönlendirme ilke değerlerini seçin.)

     |**Kayıt adı**|**Kayıt türü**|**Değer**| **TTL** |**Yönlendirme ilkesi**|
    |:-----|:-----|:-----|:-----|:-----|
    |sip  <br/> |CNAME - Kurallı ad  <br/> |sipdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |300  <br/> |Basit  <br/> |
    |lyncdiscover  <br/> |CNAME - Kurallı ad  <br/> |webdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/>  |300  <br/> ||Basit  <br/> |
  
1. Diğer CNAME kaydını eklemek için **Başka bir kayıt** ekle'yi seçin, tablonun bir sonraki satırdaki değerleri kullanarak bir kayıt oluşturun. 

1. Kayıt **oluştur'a seçin**.

   :::image type="content" source="../../media/dns-aws/aws-domains-cname-create-records.png" alt-text="Kayıt oluştur'a seçin.":::

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Gelişmiş seçenek: Mobil Cihazlar için Intune ve Mobil Microsoft 365

Bu hizmet, etki alanınıza bağlı mobil cihazların güvenliğini sağlamanıza ve uzaktan yönetmenize yardımcı olur. Mobil Cihaz Yönetimi'nin, kullanıcıların cihazları hizmete kaydedeni için iki CNAME kaydına ihtiyacı vardır.

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydı ekleme

1. Başlamak için [bu bağlantıyı](https://console.aws.amazon.com/route53/home) kullanarak AWS'deki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

1. Giriş sayfasındaki Etki Alanları'nın **altında Kayıtlı** etki **alanları'na tıklayın**.

1. Etki **Alanı Adı** altında, etki alanında ayarlamak istediğiniz etki Microsoft 365.

    **Not**: Etki alanınız için barındırılan bir bölge oluşturmadısanız, Barındırılan bölge  oluştur'u seçin ve sonraki adıma ilerlemeden önce adımları tamamlayın. 

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Etki alanının adını seçin.":::

1. **DNS'yi Yönet'i seçin**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::

1. Etki **alanı adı** altında, doğrulamak istediğiniz etki alanının barındırılan bölge sürümünün etki alanı adını seçin.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Etki alanının adını seçin.":::

1. Kayıt **oluştur'a seçin**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Kayıt oluştur'a seçin.":::

1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

    (Açılır **listelerden** **Tür ve** Yönlendirme ilke değerlerini seçin.)

    |**Kayıt adı**|**Kayıt türü**|**Değer**| **TTL** |**Yönlendirme ilkesi**|
    |:-----|:-----|:-----|:-----|:-----|
    |enterpriseregistration  <br/> |CNAME - Kurallı ad  <br/> |enterpriseregistration.windows.net.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |300  <br/> |Basit  <br/> |
    |enterpriseenrollment  <br/> |CNAME - Kurallı ad  <br/> | enterpriseenrollment-s.manage.microsoft.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/>|300  <br/> | |Basit  <br/> |
  
1. Diğer CNAME kaydını eklemek için **Başka bir kayıt** ekle'yi seçin, tablonun bir sonraki satırdaki değerleri kullanarak bir kayıt oluşturun. 

1. Kayıt **oluştur'a seçin**.

   :::image type="content" source="../../media/dns-aws/aws-domains-cname-create-records.png" alt-text="Kayıt oluştur'a seçin.":::

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.
