---
title: Bağlan OVH'de DNS kayıtlarınızı Microsoft 365
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
ms.assetid: 5176feef-36dc-4d84-842f-1f2b5a21ba96
description: Microsoft için OVH'de etki alanlarınızı doğrulamayı ve e-posta, Skype Kurumsal Online ve diğer hizmetler için DNS kayıtlarını ayarlamayı öğrenin.
ms.openlocfilehash: 9c181536c418baebd3ba8eb1929095ac2d828ef6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314987"
---
# <a name="connect-your-dns-records-at-ovh-to-microsoft-365"></a>Bağlan OVH'de DNS kayıtlarınızı Microsoft 365

Aradığınızı bulamazsanız, [Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml).
  
DNS barındırma sağlayıcınız OVH ise, bu makaledeki adımları izleyin ve etki alanınızı doğrulayın ve e-posta, Skype Kurumsal Online, gibi DNS kayıtlarını ayarlayın.

OVH'de bu kayıtları eklemenizden sonra, etki alanınız Microsoft hizmetleri.

> [!NOTE]
>  Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 
  
## <a name="add-a-txt-record-for-verification"></a>Doğrulama için bir TXT kaydı ekleme

Etki alanınızı Microsoft ile kullanmadan önce bu etki alanına sahip olduğundan emin olarız. Etki alanı kayıt şirketinizin hesabında oturum açabilme ve DNS kaydı oluşturabilme özelliği, Microsoft'a etki alanının sahibi olduğunu kanıtlar.
  
> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. Dilerseniz bu kaydı daha sonra silebilirsiniz. 
  
1. Kullanmaya başlamak için, bu bağlantıyı kullanarak OVH'daki etki alanları [sayfanıza gidin](https://www.ovh.com/manager/). Oturum açmanız istenir.

    ![OVH oturumu açma.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Pano giriş sayfasında, Tüm **etkinliklerimi görüntüle'nin** altında, düzenlemek istediğiniz etki alanının adını seçin.
  
1. **DNS bölgesi'ni seçin**.

    ![OVH DNS bölgesi'ni seçin.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Girdi **ekle'yi seçin**.

    ![OVH Girdi ekleme.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. **TXT'yi seçin**

    ![OVH, TXT girdisini seçin.](../../media/3aaa9dae-0b1d-436b-a980-b67a970f31a9.png)
  
1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın. TTL değeri atamak için, **açılan** listeden Özel'i seçin ve ardından metin kutusuna değeri yazın. 

    |**Kayıt türü**|**Alt etki alanı**|**TTL**|**Değer**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |(boş bırakın)  <br/> |3600 (saniye)  <br/> |MS=msxxxxxxxx  <br/> **Not:** Bu bir örnektir. Tablodan **, belirli Hedef veya Adres Noktaları** değerinizi burada kullanın.  [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)          |

1. **İleri**'yi seçin.

1. **Onayla'ya seçin**.

    ![OVH doğrulama için TXT'yi onaylayın.](../../media/bde45596-9a55-4634-b5e7-16d7cde6e1b8.png)
  
1. Yeni oluşturduğunuz kaydın İnternet genelinde güncelleştirilebilmesi için devam etmeden önce birkaç dakika bekleyin.

Kaydı etki alanı kayıt şirketinizin sitesinde eklediknize göre, Microsoft'a geri dönüp kayıt isteğinde bulundurabilirsiniz. Microsoft doğru TXT kaydını bulduğunda, etki alanınız doğrulanır.

Bir dosyada kaydı Microsoft 365:
  
1. Yönetim merkezinde Etki Alanları'nın **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**gidin**</a>.

1. Etki Alanları sayfasında, doğrulamakta olduğunuz etki alanını seçin ve sonra da Kurulumu **başlat'ı seçin**. 

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. **Devam'ı seçin**.
  
1. Etki alanını **doğrulama sayfasında** Doğrula'ya **tıklayın**.

> [!NOTE]
>  Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Etki alanınıza gelen e-postanın Microsoft'a göndernsin için MX kaydı ekleme

1. Kullanmaya başlamak için, bu bağlantıyı kullanarak OVH'daki etki alanları [sayfanıza gidin](https://www.ovh.com/manager/). Oturum açmanız istenir.

    ![OVH oturumu açma.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Pano giriş sayfasında, Tüm **etkinliklerimi görüntüle'nin** altında, düzenlemek istediğiniz etki alanının adını seçin.
  
1. **DNS bölgesi'ni seçin**.

    ![OVH DNS bölgesi'ni seçin.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Girdi **ekle'yi seçin**.

    ![OVH Girdi ekleme.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. **MX'i seçin**.

    ![OVH MX kayıt türü.](../../media/29b5e54e-440a-41f2-9eb9-3de573922ddf.png)
  
1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın. TTL değeri atamak için, **açılan** listeden Özel'i seçin ve ardından metin kutusuna değeri yazın. 

    > [!NOTE]
    > Varsayılan olarak OVH hedef için göreli notasyonu kullanır ve bu da hedef kaydın sonuna etki alanı adını ekler. Bunun yerine mutlak notasyonu kullanmak için, aşağıdaki tabloda gösterildiği gibi hedef kayda bir nokta ekleyin. 
  
    |**Alt etki alanı**|**TTL**|**Öncelik**|**Hedef**|
    |:-----|:-----|:-----|:-----|
    |(boş bırakın)  <br/> |3600 (saniye)  <br/> |0  <br/> Öncelik hakkında daha fazla bilgi için bkz. [MX önceliği nedir?](../setup/domains-faq.yml) <br/> |\<domain-key\>.mail.protection.outlook.com.  <br/> **Not:** Microsoft hesabınızla  *\<domain-key\>*  oturum açın.  [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)  |

    ![Posta için OVH MX kaydı.](../../media/6e2f5655-93e2-4620-8f19-c452e7edf8f0.png)
  
1. **İleri**'yi seçin.

    ![OVH MX kaydı için Sonraki'yi seçin.](../../media/4db62d07-0dc4-49f6-bd19-2b4a07fd764a.png)
  
1. **Onayla'ya seçin**.

    ![OVH MX kaydı Için Onayla'ya seçin.](../../media/090bfb11-a753-4af0-8982-582a4069a169.png)

1. DNS bölgesi sayfasındaki listede diğer tüm MX **kayıtlarını** silin. Her kaydı seçin ve Eylemler **sütununda** Sil çöp **kutusu simgesini seçin** .

    ![OVH, MX kaydını siler.](../../media/892b328b-7057-4828-b8c5-fe26284dc8c2.png)
  
1. **Onayla'ya seçin**.

## <a name="add-the-cname-record-required-for-microsoft"></a>Microsoft için gereken CNAME kaydını ekleme

1. Kullanmaya başlamak için, bu bağlantıyı kullanarak OVH'daki etki alanları [sayfanıza gidin](https://www.ovh.com/manager/). Oturum açmanız istenir.

    ![OVH oturumu açma.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Pano giriş sayfasında, Tüm **etkinliklerimi görüntüle'nin** altında, düzenlemek istediğiniz etki alanının adını seçin.
  
1. **DNS bölgesi'ni seçin**.

    ![OVH DNS bölgesi'ni seçin.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Girdi **ekle'yi seçin**.

    ![OVH Girdi ekleme.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. **CNAME'yi seçin**.

    ![OVH Add CNAME kayıt türü.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. Yeni kayıt kutularına, aşağıdaki tablonun ilk satırındaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın. TTL değeri atamak için, **açılan** listeden Özel'i seçin ve ardından metin kutusuna değeri yazın. 

    |**Alt etki alanı**|**TTL**|**Hedef**|
    |:-----|:-----|:-----|
    |autodiscover  <br/> |3600 (saniye)  <br/> |autodiscover.outlook.com.  <br/> |

    ![OVH CNAME kaydı.](../../media/516938b3-0b12-4736-a631-099e12e189f5.png)
  
1. **İleri**'yi seçin.

    ![OVH CNAME değerleri ekleyin ve Sonraki'yi seçin.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)
  
1. **Onayla'ya seçin**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa Microsoft için yeni bir SPF kaydı oluşturun. Bunun yerine, her iki değer kümesi de içeren tek  *bir SPF*  kaydına sahip olmak için gerekli Microsoft değerlerini geçerli kayda ekleyin. 
  
1. Kullanmaya başlamak için, bu bağlantıyı kullanarak OVH'daki etki alanları [sayfanıza gidin](https://www.ovh.com/manager/). Oturum açmanız istenir.

    ![OVH oturumu açma.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Pano giriş sayfasında, Tüm **etkinliklerimi görüntüle'nin** altında, düzenlemek istediğiniz etki alanının adını seçin.
  
1. **DNS bölgesi'ni seçin**.

    ![OVH DNS bölgesi'ni seçin.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Girdi **ekle'yi seçin**.

    ![OVH Girdi ekleme.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. **TXT'yi seçin**.

1. In the boxes for the new record, type or copy and paste the following values. TTL değeri atamak için, **açılan** listeden Özel'i seçin ve ardından metin kutusuna değeri yazın. 

    |**Alt etki alanı**|**TTL**|**Değer**|
    |:-----|:-----|:-----|
    |(boş bırakın)  <br/> |3600 (saniye)  <br/> |v=spf1 include:spf.protection.outlook.com -all <br/**Note:** Tüm boşlukların doğru kalması için bu girdiyi kopyalayıp kopyalamanız önerilir.           |

    ![OVH SPF için TXT kaydı ekleme.](../../media/f50466e9-1557-4548-8a39-e98978a5ee2e.png)
  
1. **İleri**'yi seçin.

    ![SPF için OVH TXT kaydı ekleyin ve Sonraki'yi seçin.](../../media/7937eb7c-114f-479f-a916-bcbe476d6108.png)
  
1. **Onayla'ya seçin**.

    ![OVH SPF için TXT kaydı ekleyin ve Onayla'ya tıklayın.](../../media/649eefeb-3227-49e3-98a0-1ce19c42fa54.png)
  
## <a name="advanced-option-skype-for-business"></a>Gelişmiş seçenek: Skype Kurumsal

Yalnızca, bu seçeneği yalnızca, Skype Kurumsal yanı sıra sohbet, konferans aramaları ve görüntülü aramalar gibi çevrimiçi iletişim hizmetleri için Microsoft Teams. Skype için 4 kayıt gerekir: Oturum açma ve kullanıcıları hizmete bağlamak için 2 kullanıcı-kullanıcı iletişim için SRV kaydı ve 2 CNAME kaydı.

### <a name="add-the-two-required-srv-records"></a>Gerekli iki SRV kaydı ekleme

1. Kullanmaya başlamak için, bu bağlantıyı kullanarak OVH'daki etki alanları [sayfanıza gidin](https://www.ovh.com/manager/). Oturum açmanız istenir.

    ![OVH oturumu açma.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Pano giriş sayfasında, Tüm **etkinliklerimi görüntüle'nin** altında, düzenlemek istediğiniz etki alanının adını seçin.
  
1. **DNS bölgesi'ni seçin**.

    ![OVH DNS bölgesi'ni seçin.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Girdi **ekle'yi seçin**.

    ![OVH Girdi ekleme.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. **SRV'yi seçin**.

1. In the boxes for the new record, type or copy and paste the following values. TTL değeri atamak için, **açılan** listeden Özel'i seçin ve ardından metin kutusuna değeri yazın. 

    |**Alt etki alanı**|**TTL (Saniye)**| **Öncelik** | **Ağırlık** | **Bağlantı Noktası**|**Hedef**|
    |:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip._tls|3600 (s.) |100 |  1  | 443 |sipdir.online.lync.com. **Bu değer nokta (.) ile bitMİ OLMALı**><br> **Not:** Tüm boşlukların doğru kalması için bu girdiyi kopyalayıp yapıştırarak bu dosyayı yapıştırın. | 
    |_sipfederationtls._tcp| 3600 (s.)|100 | 1 | 5061 | sipfed.online.lync.com. **Bu değer nokta (.) ile bitmelidir.**<br> **Not:** Tüm boşlukların doğru kalması için bu girdiyi kopyalayıp yapıştırarak bu dosyayı yapıştırın.    | 
  
1. Diğer SRV kaydını eklemek için Başka bir kayıt ekle'yi **seçin,** tablonun bir sonraki satırına gelen değerleri kullanarak kaydı oluşturun ve ardından Kayıt oluştur'a **tıklayın**.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlar ile ilgili sorunlar için bkz. Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra [sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydı ekleme 

1. Kullanmaya başlamak için, bu bağlantıyı kullanarak OVH'daki etki alanları [sayfanıza gidin](https://www.ovh.com/manager/). Oturum açmanız istenir.

    ![OVH oturumu açma.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Pano giriş sayfasında, Tüm **etkinliklerimi görüntüle'nin** altında, düzenlemek istediğiniz etki alanının adını seçin.
  
1. **DNS bölgesi'ni seçin**.

    ![OVH DNS bölgesi'ni seçin.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Girdi **ekle'yi seçin**.

    ![OVH Girdi ekleme.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. **CNAME'yi seçin**.

    ![OVH Add CNAME kayıt türü.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. Yeni kayıt kutularına, aşağıdaki tablonun ilk satırındaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın. TTL değeri atamak için, **açılan** listeden Özel'i seçin ve ardından metin kutusuna değeri yazın. 

    |**Alt etki alanı**| **TTL** | **Hedef** | 
    |:-----|:-----|:-----|
    |sip  <br/> | 3600 (s.)  <br/> |sipdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |
    |lyncdiscover  <br/> |3600 (s.) |webdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/>  |
  
1. **İleri**'yi seçin.

    ![OVH CNAME değerleri ekleyin ve Sonraki'yi seçin.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)
  
1. **Onayla'ya seçin**.

1. Diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Gelişmiş seçenek: Mobil Cihazlar için Intune ve Mobil Microsoft 365

Bu hizmet, etki alanınıza bağlı mobil cihazların güvenliğini sağlamanıza ve uzaktan yönetmenize yardımcı olur. Mobil Cihaz Yönetimi'nin, kullanıcıların cihazları hizmete kaydedeni için iki CNAME kaydına ihtiyacı vardır.

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydı ekleme

1. Kullanmaya başlamak için, bu bağlantıyı kullanarak OVH'daki etki alanları [sayfanıza gidin](https://www.ovh.com/manager/). Oturum açmanız istenir.

    ![OVH oturumu açma.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Pano giriş sayfasında, Tüm **etkinliklerimi görüntüle'nin** altında, düzenlemek istediğiniz etki alanının adını seçin.
  
1. **DNS bölgesi'ni seçin**.

    ![OVH DNS bölgesi'ni seçin.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Girdi **ekle'yi seçin**.

    ![OVH Girdi ekleme.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. **CNAME'yi seçin**.

    ![OVH Add CNAME kayıt türü.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. Yeni kayıt kutularına, aşağıdaki tablonun ilk satırındaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın. TTL değeri atamak için, **açılan** listeden Özel'i seçin ve ardından metin kutusuna değeri yazın. 
  
    |**Alt etki alanı**| **TTL** | **Hedef** | 
    |:-----|:-----|:-----|
    |enterpriseregistration  <br/>| 3600 (s.)  <br/> |enterpriseregistration.windows.net.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |
    |enterpriseenrollment  <br/>  |3600 (s.) |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/>|

1. **İleri**'yi seçin.

    ![OVH CNAME değerleri ekleyin ve Sonraki'yi seçin.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)
  
1. **Onayla'ya seçin**.

1. Diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.