---
title: Bağlan wix'te DNS kayıtlarınızı Microsoft 365
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
ms.assetid: 7173c635-58b3-400f-95e0-97abe915565e
description: Microsoft için Wix'te etki alanlarınızı doğrulamayı ve e-posta, Skype Kurumsal Online ve diğer hizmetler için DNS kayıtlarını ayarlamayı öğrenin.
ms.openlocfilehash: 9a9e230a46967ab6c012199e7f4fc6426fdc67bf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314861"
---
# <a name="connect-your-dns-records-at-wix-to-microsoft-365"></a>Bağlan wix'te DNS kayıtlarınızı Microsoft 365

Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**. 
  
DNS barındırma sağlayıcınız Wix ise, bu makaledeki adımları izleyin ve etki alanını doğrulayın ve e-posta, Skype Kurumsal Online, gibi dns kayıtlarını ayarlayın.

Wix'e bu kayıtları ekledikten sonra, etki alanınız Microsoft hizmetleri.
  
> [!NOTE]
>  Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 

## <a name="add-a-txt-record-for-verification"></a>Doğrulama için bir TXT kaydı ekleme

Etki alanınızı Microsoft ile kullanmadan önce bu etki alanının size ait olduğundan emin olarız. Etki alanı kayıt şirketinizin hesabında oturum açabilme ve DNS kaydı oluşturabilme özelliği, Microsoft'a etki alanının sahibi olduğunu kanıtlar.
  
> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. Silmeyi daha sonra  silmeniz de gerekir. 

> [!NOTE]
> WIX, alt etki alanları için DNS girdilerini desteklemez.
  
1. Kullanmaya başlamak için bu bağlantıyı kullanarak Wix'te etki alanları [sayfanıza gidin](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Önce oturum açmanız istenir.

2. Etki **Alanları** > **... öğesini** seçin ve ardından **açılan listeden DNS** Kayıtlarını Yönet'i seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Açılan listeden DNS Kayıtlarını Yönet'i seçin.":::

3. DNS **düzenleyicisinin** **TXT (Metin) satırına** + Kayıt Ekle'yi seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="Kayıt ekle'yi seçin.":::

4. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

   ||||
   |:-----|:-----|:-----|
   | **Ana Bilgisayar Adı **<br/> | **TXT Değeri** <br/> | **TTL** <br/> |
   |Otomatik olarak doldurulur (boş bırakın)  <br/> |MS=ms *XXXXXXXX*  <br/> **Not:** Bu bir örnektir. Tablodan **, belirli Hedef veya Adres Noktaları** değerinizi burada kullanın.  [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)|1 Saat <br/> |          |

5. **Kaydetme'yi seçin**.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="Kaydet'i seçin.":::

   Yeni oluşturduğunuz kaydın İnternet genelinde güncelleştirilebilmesi için devam etmeden önce birkaç dakika bekleyin.


Kaydı etki alanı kayıt şirketinizin sitesinde eklediknize göre, Microsoft'a geri dönüp kayıt isteğinde bulundurabilirsiniz. Microsoft doğru TXT kaydını bulduğunda, etki alanınız doğrulanır. 

Bir dosyada kaydı Microsoft 365:
  
1. Yönetim merkezinde Etki Alanları'nın **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**gidin**</a>.

1. Etki Alanları sayfasında, doğrulamakta olduğunuz etki alanını seçin ve sonra da Kurulumu **başlat'ı seçin**. 

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. **Devam'ı seçin**.
  
1. Etki alanını **doğrulama sayfasında** Doğrula'ya **tıklayın**.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Etki alanınıza gelen e-postanın Microsoft'a göndernsin için MX kaydı ekleme

1. Kullanmaya başlamak için bu bağlantıyı kullanarak Wix'te etki alanları [sayfanıza gidin](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Önce oturum açmanız istenir.

1. Etki **Alanları** > **... öğesini** seçin ve ardından **açılan listeden DNS** Kayıtlarını Yönet'i seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Açılan listeden DNS Kayıtlarını Yönet'i seçin.":::

1. **MX (Posta değişimi)'nin** altında **MX Kayıtlarını Düzenle'yi seçin**. 

   :::image type="content" source="../../media/dns-wix/wix-domains-edit-mx-records.png" alt-text="MX Kayıtlarını Düzenle'yi seçin.":::

1. Açılan **listeden** Diğer'i seçin ve **+ Kayıt ekle'yi seçin**.

   :::image type="content" source="../../media/dns-wix/wix-domains-other.png" alt-text="Açılan listeden Diğer'i seçin.":::

1. Yeni kayıt kutularına, aşağıdaki tabloda yer alan değerleri yazın ya da bu tablodan kopyalayıp yapıştırın:

   | **Ana Bilgisayar Adı** | **Yönlendirme** | **Öncelik** | **TTL** |
   |:-----|:-----|:-----|:-----|
   |Otomatik olarak doldurulur <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Not:** Microsoft hesabınızla  *\<domain-key\>*  oturum açın.   [How do I find this?](../get-help-with-domains/information-for-dns-records.md) |0  <br/> Öncelik hakkında daha fazla bilgi için bkz. [MX önceliği nedir?](../setup/domains-faq.yml) | 1 Saat|

1. Listelenen başka MX kayıtları varsa, bunların her birini silin.

   :::image type="content" source="../../media/dns-wix/wix-domains-mx-delete.png" alt-text="Sil'i seçin.":::

1. **Kaydet**'i seçin.

## <a name="add-the-cname-record-required-for-microsoft"></a>Microsoft için gereken CNAME kaydını ekleme

1. Kullanmaya başlamak için bu bağlantıyı kullanarak Wix'te etki alanları [sayfanıza gidin](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Önce oturum açmanız istenir.

2. Etki **Alanları** > **... öğesini** seçin ve ardından **açılan listeden DNS** Kayıtlarını Yönet'i seçin. 

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Açılan listeden DNS Kayıtlarını Yönet'i seçin.":::

3. CNAME **kaydının** DNS **düzenleyicisinin CNAME (Diğer Adlar)** satırına + Kayıt Ekle'yi seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="+ Kayıt Ekle'yi seçin.":::

4. Yeni kayıt kutularına, aşağıdaki tabloda yer alan değerleri yazın ya da bu tablodan kopyalayıp yapıştırın:

   | **Ana Bilgisayar Adı** | **Değer** | **TTL** |
   |:-----|:-----|:-----|
   |autodiscover  <br/> |autodiscover.outlook.com  <br/> |1 Saat  <br/> |

5. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Kaydet'i seçin.":::

   Yeni oluşturduğunuz kaydın İnternet genelinde güncelleştirilebilmesi için devam etmeden önce birkaç dakika bekleyin.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa Microsoft için yeni bir SPF kaydı oluşturun. Bunun yerine, her iki değer kümesi de içeren tek  *bir SPF*  kaydına sahip olmak için gerekli Microsoft değerlerini geçerli kayda ekleyin.  
  
1. Kullanmaya başlamak için bu bağlantıyı kullanarak Wix'te etki alanları [sayfanıza gidin](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Önce oturum açmanız istenir.

2. Etki **Alanları** > **... öğesini** seçin ve ardından **açılan listeden DNS** Kayıtlarını Yönet'i seçin. 

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Açılan listeden DNS Kayıtlarını Yönet'i seçin.":::

3. DNS **düzenleyicisinin** **TXT (Metin) satırına** + Kayıt Ekle'yi seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="+ Kayıt ekle'yi seçin.":::

   **Not**: Wix, DNS düzenleyicisinde bir SPF satırı sağlar. Bu satırı yoksayın ve **SPF değerlerini aşağıya girmek için TXT (Metin)** satırı kullanın. 

4. Yeni kayıt kutularına, aşağıdaki tabloda yer alan değerleri yazın ya da bu tablodan kopyalayıp yapıştırın:

   | **Ana Bilgisayar Adı** | **Değer** | **TTL** |
   |:-----|:-----|:-----|
   |[Bunu boş bırakın]  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Not:** Tüm boşlukların doğru kalması için bu girdiyi kopyalayıp yapıştırarak bu dosyayı yapıştırın.<br/> | 1 Saat |

5. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="Kaydet'i seçin.":::

   Yeni oluşturduğunuz kaydın İnternet genelinde güncelleştirilebilmesi için devam etmeden önce birkaç dakika bekleyin.

## <a name="advanced-option-skype-for-business"></a>Gelişmiş seçenek: Skype Kurumsal

Yalnızca, bu seçeneği yalnızca, Skype Kurumsal yanı sıra sohbet, konferans aramaları ve görüntülü aramalar gibi çevrimiçi iletişim hizmetleri için Microsoft Teams. Skype şu şekilde dört kayıt gerekir: kullanıcı-kullanıcı iletişimi için iki SRV kaydı ve oturum açma ve kullanıcıları hizmete bağlamak için iki CNAME kaydı.

### <a name="add-the-two-required-srv-records"></a>Gerekli iki SRV kaydı ekleme

1. Kullanmaya başlamak için bu bağlantıyı kullanarak Wix'te etki alanları [sayfanıza gidin](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Önce oturum açmanız istenir.

1. Etki **Alanları** > **... öğesini** seçin ve ardından **açılan listeden DNS** Kayıtlarını Yönet'i seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Açılan listeden DNS Kayıtlarını Yönet'i seçin.":::

1. DNS **düzenleyicisinin** **SRV satırda** + Kayıt Ekle'yi seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-srv-add-record.png" alt-text="+ Kayıt Ekle'yi seçin.":::

1. Yeni kayıt kutularına, tablonun ilk satırdaki değerleri yazın veya kopyalayıp yapıştırın:

   | **Hizmet** | **Protokol** | **Ana bilgisayar adı** | **Ağırlık** | **Bağlantı Noktası** | **Hedef** | **Öncelik** | **TTL** |
   |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
   |sip  |tls  |Otomatik olarak doldurulur |1  |443   |sipdir.online.lync.com |100 |1 Saat |
   |sipfed|tcp |Otomatik olarak doldurulur|1 |5061 |sipfed.online.lync.com|100 | 1 Saat |

1. **Kaydet**'i seçin.
  
   :::image type="content" source="../../media/dns-wix/wix-domains-srv-save.png" alt-text="Kaydet'i seçin.":::

1. Tablonun ikinci satırına değerleri kopyalayıp diğer SRV kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlar ile ilgili sorunlar için bkz. Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra [sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydı ekleme

1. DNS **düzenleyicisinin** **CNAME (Diğer Adlar)** satırına + Başka bir ad ekle'yi seçin ve aşağıdaki tablonun ilk satırına değerleri girin.

   |**Tür**|**Ana Bilgisayar**|**Değer**|**TTL**|
   |:-----|:-----|:-----|:-----|
   |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |1 Saat  <br/> |
   |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |1 Saat  <br/> |
  
1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Kaydet'i seçin.":::
  
1. Tablonun ikinci satırına değerleri kopyalayıp diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Gelişmiş seçenek: Mobil Cihazlar için Intune ve Mobil Microsoft 365

Bu hizmet, etki alanınıza bağlı mobil cihazların güvenliğini sağlamanıza ve uzaktan yönetmenize yardımcı olur. Mobil Cihaz Yönetimi'nin, kullanıcıların cihazları hizmete kaydedeni için iki CNAME kaydına ihtiyacı vardır.

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydı ekleme

1. Kullanmaya başlamak için bu bağlantıyı kullanarak Wix'te etki alanları [sayfanıza gidin](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Önce oturum açmanız istenir.

1. Etki **Alanları** > **... öğesini** seçin ve ardından **açılan listeden DNS** Kayıtlarını Yönet'i seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Açılan listeden DNS Kayıtlarını Yönet'i seçin.":::

1. CNAME **kaydının** DNS **düzenleyicisinin CNAME (Diğer Adlar)** satırına + Kayıt Ekle'yi seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="+ Kayıt Ekle'yi seçin.":::

1. Aşağıdaki tablonun ilk satırına değerleri girin.

    |**Tür**|**Ana Bilgisayar**|**Değer**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |enterpriseregistration <br/> |enterpriseregistration.windows.net.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |1 Saat  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment.manage.microsoft.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |1 Saat  <br/> |
  
1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Kaydet'i seçin.":::
  
1. Tablonun ikinci satırına değerleri kopyalayıp diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.