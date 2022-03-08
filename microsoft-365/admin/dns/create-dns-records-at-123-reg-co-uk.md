---
title: Bağlan DNS kayıtlarınızı 123-reg.co.uk Microsoft 365
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
ms.assetid: 1f2d08c9-2a88-4d2f-ae1f-e39f9e358b17
description: Microsoft için Microsoft'un Web Sitesinde etki alanlarınızı doğrulamayı ve e-posta, Skype Kurumsal Online ve diğer 123-reg.co.uk ayarlamayı öğrenin.
ms.openlocfilehash: 050aad4ca3e0e768b160a7ba210a93e163d72fe7
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314945"
---
# <a name="connect-your-dns-records-at-123-regcouk-to-microsoft-365"></a>Bağlan DNS kayıtlarınızı 123-reg.co.uk Microsoft 365

 **Aradığınızı bulamazsanız, [Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**. 
  
DNS barındırma sağlayıcınız 123-reg.co.uk ise, bu makalede verilen adımları izleyerek etki alanınızı doğrulayın ve e-posta, Skype Kurumsal Çevrimiçi Sürümü vb. için DNS kayıtlarını ayarlayın.
  
İş yerinde bu kayıtları 123-reg.co.uk, etki alanınız diğerleriyle birlikte çalışacak şekilde Microsoft hizmetleri. 
  
> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlar ile ilgili sorunlar için bkz. Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra [sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Doğrulama için bir TXT kaydı ekleme

Etki alanınızı Microsoft ile kullanmadan önce bu etki alanına sahip olduğundan emin olarız. Etki alanı kayıt şirketinizin hesabında oturum açabilme ve DNS kaydı oluşturabilme özelliği, Microsoft'a etki alanının sahibi olduğunu kanıtlar.
  
> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. Dilerseniz bu kaydı daha sonra silebilirsiniz. 
  
1. Başlamak için [bu bağlantıyı](https://www.123-reg.co.uk/secure/cpanel/domain/overview) kullanarak 123-reg.co.uk adresindeki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

2. Etki **Alanları'nı** seçin ve Etki alanı adına genel bakış sayfasında, doğrulamak istediğiniz etki alanının adını seçin veya Denetim Masası'nı tıklatın.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Doğrulamak istediğiniz etki alanını seçin.":::

3. Etki alanını yönet sayfasındaki Gelişmiş etki alanı **ayarları'nın altında** **DNS'yi Yönet'i seçin**.
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::
  
4. DNS'nizi yönetin sayfasında Gelişmiş **DNS sekmesini** seçin. 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Gelişmiş DNS sekmesini seçin.":::
  
5. Yeni **kaydın** Tür kutusunda, açılan listeden **TXT/SPF'yi** seçin ve ardından aşağıdaki tabloda yer alan diğer değerleri yazın veya kopyalayıp yapıştırın. 

    ||||
    |:-----|:-----|:-----|
    |**Ana Bilgisayar Adı** <br/> |**Tür** <br/> |**Hedef TXT/SPF** <br/> |
    |@  <br/> |TXT/SPF  <br/> |MS=ms *XXXXXXXX*  <br/> **Not:** Bu bir örnektir. Tablodan **, belirli Hedef veya Adres Noktaları** değerinizi burada kullanın. [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)          |
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Açılan listeden TXT/SPF türünü seçin ve değerleri doldurun.":::

6. **Ekle**'yi seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="Ekle'yi seçin.":::

   Yeni oluşturduğunuz kaydın İnternet genelinde güncelleştirilebilmesi için devam etmeden önce birkaç dakika bekleyin.

Kaydı etki alanı kayıt şirketinizin sitesinde eklediknize göre, Microsoft'a geri dönüp kayıt için arama isteğinde bulundurabilirsiniz. Microsoft doğru TXT kaydını bulduğunda, etki alanınız doğrulanır.
  
Bir dosyada kaydı Microsoft 365:
  
1. Yönetim merkezinde Etki Alanları'nın **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**gidin**</a>.

1. Etki Alanları sayfasında, doğrulamakta olduğunuz etki alanını seçin ve sonra da Kurulumu **başlat'ı seçin**. 

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. **Devam'ı seçin**.
  
1. Etki alanını **doğrulama sayfasında** Doğrula'ya **tıklayın**.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Etki alanınıza gelen e-postanın Microsoft'a göndernsin için MX kaydı ekleme

1. Başlamak için [bu bağlantıyı](https://www.123-reg.co.uk/secure/cpanel/domain/overview) kullanarak 123-reg.co.uk adresindeki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

2. Etki alanı adına genel bakış sayfasında, düzenlemek istediğiniz etki alanının adını seçin. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Düzenlemek istediğiniz etki alanının adını seçin.":::

3. Etki alanını yönet sayfasındaki Gelişmiş etki alanı **ayarları'nın altında** **DNS'yi Yönet'i seçin**.
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::
  
4. DNS'nizi yönetin sayfasında Gelişmiş **DNS sekmesini** seçin. 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Gelişmiş DNS sekmesini seçin.":::

5. Yeni **kaydın** Tür kutusunda, açılan listeden **MX'i** seçin ve ardından aşağıdaki tabloda yer alan diğer değerleri yazın veya kopyalayıp yapıştırın.

    |**Ana Bilgisayar Adı**|**Tür**|**Öncelik**|**Hedef MX**|
    |:-----|:-----|:-----|:-----|
    |@  <br/> |MX  <br/> |1  <br/> Öncelik hakkında daha fazla bilgi için bkz. [MX önceliği nedir?](../setup/domains-faq.yml) <br/> | *\<domain-key\>*  .mail.protection.outlook.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> **Not:** Microsoft hesabınızla \<domain-key\> oturum açın. [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)          |

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX.png" alt-text="Açılan listeden MX türünü seçin ve değerleri doldurun.":::

6. **Ekle**'yi seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-Add.png" alt-text="Ekle'yi seçin.":::

7. Başka MX kayıtları varsa, bu kayıt için Sil (çöp kutusu **)** simgesini seçerek bunlardan her birini kaldırın.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-delete.png" alt-text="Sil'i (çöp kutusu) seçin.":::
  
## <a name="add-the-cname-record-required-for-microsoft"></a>Microsoft için gereken CNAME kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://www.123-reg.co.uk/secure/cpanel/domain/overview) kullanarak 123-reg.co.uk adresindeki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

2. Etki alanı adına genel bakış sayfasında, düzenlemek istediğiniz etki alanının adını seçin. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Düzenlemek istediğiniz etki alanının adını seçin.":::

3. Etki alanını yönet sayfasındaki Gelişmiş etki alanı **ayarları'nın altında** **DNS'yi Yönet'i seçin**.
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::
  
4. DNS'nizi yönetin sayfasında Gelişmiş **DNS sekmesini** seçin. 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Gelişmiş DNS sekmesini seçin.":::

5. CNAME kaydını ekleyin.

    Yeni **kaydın** Tür kutusunda, açılan listeden **CNAME'yi** seçin ve ardından aşağıdaki tabloda yer alan diğer değerleri yazın veya kopyalayıp yapıştırın.

    |**Ana Bilgisayar Adı**|**Tür**|**Hedef CNAME**|
    |:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME  <br/> |autodiscover.outlook.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Açılan listeden CNAME türünü seçin ve değerleri doldurun.":::

6. **Ekle**'yi seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Ekle'yi seçin.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa, Microsfot için yeni bir SPF kaydı oluşturun. Bunun yerine, her iki değer kümesi de içeren tek  *bir SPF*  kaydına sahip olmak için gerekli Microsoft değerlerini geçerli kayda ekleyin. Örneklere mi ihtiyacınız var? Microsoft için bu [Dış Etki Alanı Adı Sistemi kayıtlarına göz atabilirsiniz](../../enterprise/external-domain-name-system-records.md). SPF kaydınızı doğrulamak için bu [SPF doğrulama araçlarından birini kullanabilirsiniz](../setup/domains-faq.yml). 
  
1. Başlamak için [bu bağlantıyı](https://www.123-reg.co.uk/secure/cpanel/domain/overview) kullanarak 123-reg.co.uk adresindeki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

2. Etki alanı adına genel bakış sayfasında, düzenlemek istediğiniz etki alanının adını seçin. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Düzenlemek istediğiniz etki alanının adını seçin.":::

3. Etki alanını yönet sayfasındaki Gelişmiş etki alanı **ayarları'nın altında** **DNS'yi Yönet'i seçin**.
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::
  
4. DNS'nizi yönetin sayfasında Gelişmiş **DNS sekmesini** seçin. 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Gelişmiş DNS sekmesini seçin.":::

5. Yeni **kaydın** Tür kutusunda, açılan listeden **TXT/SPF'yi** seçin ve ardından aşağıdaki tabloda yer alan diğer değerleri yazın veya kopyalayıp yapıştırın.

    |**Ana Bilgisayar Adı**|**Tür**|**Hedef TXT/SPF**|
    |:-----|:-----|:-----|
    |@  <br/> |TXT/SPF  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Not:** Tüm boşlukların doğru kalması için bu girdiyi kopyalayıp yapıştırarak bu dosyayı yapıştırın.           |

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Açılan listeden TXT/SPF türünü seçin ve değerleri doldurun.":::
  
6. **Ekle**'yi seçin.

## <a name="advanced-option-skype-for-business"></a>Gelişmiş seçenek: Skype Kurumsal

Yalnızca, bu seçeneği yalnızca, Skype Kurumsal yanı sıra sohbet, konferans aramaları ve görüntülü aramalar gibi çevrimiçi iletişim hizmetleri için Microsoft Teams. Skype için 4 kayıt gerekir: Oturum açma ve kullanıcıları hizmete bağlamak için 2 kullanıcı-kullanıcı iletişim için SRV kaydı ve 2 CNAME kaydı.

### <a name="add-the-two-required-srv-records"></a>Gerekli iki SRV kaydı ekleme

1. Başlamak için [bu bağlantıyı](https://www.123-reg.co.uk/secure/cpanel/domain/overview) kullanarak 123-reg.co.uk adresindeki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

2. Etki alanı adına genel bakış sayfasında, düzenlemek istediğiniz etki alanının adını seçin. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Düzenlemek istediğiniz etki alanının adını seçin.":::

3. Etki alanını yönet sayfasındaki Gelişmiş etki alanı **ayarları'nın altında** **DNS'yi Yönet'i seçin**.
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::
  
4. DNS'nizi yönetin sayfasında Gelişmiş **DNS sekmesini** seçin. 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Gelişmiş DNS sekmesini seçin.":::

5. İki SRV kaydından ilkini ekleyin:

   Yeni **kaydın** Tür kutusunda, açılan listeden **SRV'yi** seçin ve ardından aşağıdaki tabloda yer alan diğer değerleri yazın veya kopyalayıp yapıştırın.

    ||||||
    |:-----|:-----|:-----|:-----|:-----|
    |**Ana Bilgisayar Adı**|**Tür**|**Öncelik**|**TTL**|**Hedef SRV**|
    |_sip._tls|SRV|100|3600|1 443 sipdir.online.lync.com. **Bu değer nokta (.) ile bitmelidir.**<br> **Not:** Tüm boşlukların doğru kalması için bu girdiyi kopyalayıp yapıştırarak bu dosyayı yapıştırın.           |
    |_sipfederationtls._tcp|SRV|100|3600|1 5061 sipfed.online.lync.com. **Bu değer nokta (.) ile bitmelidir.** <br> **Not:** Tüm boşlukların doğru kalması için bu girdiyi kopyalayıp yapıştırarak bu dosyayı yapıştırın.           |
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Açılan listeden TXT/SPF türünü seçin ve değerleri doldurun.":::

6. **Ekle**'yi seçin.
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="Ekle'yi seçin.":::

7. Diğer SRV kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlar ile ilgili sorunlar için bkz. Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra [sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydı ekleme 

1. Başlamak için [bu bağlantıyı](https://www.123-reg.co.uk/secure/cpanel/domain/overview) kullanarak 123-reg.co.uk adresindeki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

1. Etki alanı adına genel bakış sayfasında, düzenlemek istediğiniz etki alanının adını seçin. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Düzenlemek istediğiniz etki alanının adını seçin.":::

1. Etki alanını yönet sayfasındaki Gelişmiş etki alanı **ayarları'nın altında** **DNS'yi Yönet'i seçin**.
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::
  
1. DNS'nizi yönetin sayfasında Gelişmiş **DNS sekmesini** seçin. 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Gelişmiş DNS sekmesini seçin.":::

1. İlk CNAME kaydını ekleyin.

    Yeni **kaydın** Tür kutusunda, açılan listeden **CNAME'yi** seçin ve ardından aşağıdaki tabloda yer alan diğer değerleri yazın veya kopyalayıp yapıştırın.

    | **Ana Bilgisayar Adı** |**Tür**|**Hedef CNAME**|
    |:-----|:-----|:-----|
    |sip  <br/>|CNAME  <br/> |sipdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |
    |lyncdiscover  <br/>|CNAME  <br/> |webdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Açılan listeden CNAME türünü seçin ve değerleri doldurun.":::

1. **Ekle**'yi seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Ekle'yi seçin.":::
  
1. Diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Gelişmiş seçenek: Mobil Cihazlar için Intune ve Mobil Microsoft 365

Bu hizmet, etki alanınıza bağlı mobil cihazların güvenliğini sağlamanıza ve uzaktan yönetmenize yardımcı olur. Mobil Cihaz Yönetimi'nin, kullanıcıların cihazları hizmete kaydedeni için iki CNAME kaydına ihtiyacı vardır.

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydı ekleme

1. Başlamak için [bu bağlantıyı](https://www.123-reg.co.uk/secure/cpanel/domain/overview) kullanarak 123-reg.co.uk adresindeki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

1. Etki alanı adına genel bakış sayfasında, düzenlemek istediğiniz etki alanının adını seçin. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Düzenlemek istediğiniz etki alanının adını seçin.":::

1. Etki alanını yönet sayfasındaki Gelişmiş etki alanı **ayarları'nın altında** **DNS'yi Yönet'i seçin**.
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::
  
1. DNS'nizi yönetin sayfasında Gelişmiş **DNS sekmesini** seçin. 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Gelişmiş DNS sekmesini seçin.":::

1. İlk CNAME kaydını ekleyin.

    Yeni **kaydın** Tür kutusunda, açılan listeden **CNAME'yi** seçin ve ardından aşağıdaki tabloda yer alan diğer değerleri yazın veya kopyalayıp yapıştırın.

   | **Ana Bilgisayar Adı**|**Tür**|**Hedef CNAME**|
   |:-----|:-----|:-----|
   | enterpriseregistration <br/> | CNAME  <br/> |enterpriseregistration.windows.net.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |
   |enterpriseenrollment  <br/> | CNAME  <br/> |enterpriseenrollment.manage.microsoft.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Açılan listeden CNAME türünü seçin ve değerleri doldurun.":::

1. **Ekle**'yi seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Ekle'yi seçin.":::

1. Diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.