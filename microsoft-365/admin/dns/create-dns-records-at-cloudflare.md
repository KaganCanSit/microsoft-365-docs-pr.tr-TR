---
title: Bağlan Cloudflare'da DNS kayıtlarınızı Microsoft 365
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
ms.assetid: 84acd4fc-6eec-4d00-8bed-568f036ae2af
description: Microsoft için Cloudflare'de etki alanlarınızı doğrulamayı ve e-posta, Skype Kurumsal Online ve diğer hizmetler için DNS kayıtlarını ayarlamayı öğrenin.
ms.openlocfilehash: 5cf6483c7f560f5ab3ed2074dbaebf6c893dca3e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314931"
---
# <a name="connect-your-dns-records-at-cloudflare-to-microsoft-365"></a>Bağlan Cloudflare'da DNS kayıtlarınızı Microsoft 365

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**. 

DNS barındırma sağlayıcınız Cloudflare ise, bu makaledeki adımları kullanarak etki alanlarınızı doğrulayın ve e-posta, Skype Kurumsal Online, gibi DNS kayıtlarını ayarlayın.

## <a name="before-you-begin"></a>Başlamadan önce

Etki alanınız için DNS kayıtlarını ayarlarken iki seçeneğiniz vardır:

- [**Etki Alanı Bağlan**](#use-domain-connect-to-verify-and-set-up-your-domain) Etki alanını başka bir e-posta hizmeti sağlayıcısıyla ayarlamadısanız, yeni etki alanınızı otomatik olarak doğrulamak ve yeni etki alanıyla birlikte kullanmak üzere ayarlamak için Etki alanı Bağlan adımlarını Microsoft 365. 

    VEYA

- [**El ile adımları kullanma**](#create-dns-records-with-manual-setup) Aşağıdaki el ile adımları kullanarak etki alanınızı doğrulayın ve etki alanı kayıt şirketine eklemek istediğiniz kayıtların ne zaman ve hangi kayıtları seçeceklerini seçin. Bu sayede, örneğin size uygun bir şekilde yeni MX (posta) kayıtları ayarlanır. 

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Etki Bağlan doğrulamak ve ayarlamak için Etki Alanı Yöneticisi'ne

Cloudflare etki alanınızı otomatik olarak doğrulamak ve bu etki alanıyla ayarlamak için şu Microsoft 365:

1. Etki Microsoft 365 yönetim merkezi Etki **Ayarlar** >  seçin ve ardından ayarlamak istediğiniz etki alanını seçin.<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>

1. Üç noktayı (diğer eylemler) seçin ve **>'ı seçin**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. Etki alanınızı nasıl bağlamak istiyor musunuz? sayfasında **Devam'ı seçin**.

1. DNS kayıtları ekle sayfasında DNS kayıtları **ekle'yi seçin**.

1. Cloudflare oturum açma sayfasında, hesabınızla oturum açın ve Yetkilendir'i **seçin**.

    Bu, e-posta için etki alanı Microsoft 365. 

## <a name="create-dns-records-with-manual-setup"></a>El ile kurulumla DNS kayıtları oluşturma

Cloudflare'da bu kayıtları ekledikten sonra, etki alanınız Etki alanınız Microsoft 365 ayarlanır.

> [!NOTE]
>  Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 
  
### <a name="change-your-domains-nameserver-ns-records"></a>Etki alanınızın ad sunucusu (NS) kayıtlarını değiştirin

> [!IMPORTANT]
> Bu yordamı, etki alanınızı satın aldığınız ve kaydettirdiğiniz etki alanı kayıt şirketinde gerçekleştirmelisiniz. 
  
Cloudflare için kayıt olurken, Cloudflare Kurulumu işlemini kullanarak bir etki alanı eklediniz. 
  
Ekley istediğiniz etki alanı Cloudflare'dan veya ayrı bir etki alanı kayıt şirketinden satın alındı. Microsoft 365'te etki alanınız için DNS kayıtlarını doğrulamak ve oluşturmak için, ilk olarak etki alanı kayıt şirketinizin ad sunucularını Cloudflare ad sunucularını kullanmak üzere değiştirmalısınız.
  
Etki alanı kayıt şirketinizin web sitesinde etki alanınızın ad sunucularını kendiniz değiştirmek için şu adımları izleyin.
  
1. Etki alanı kayıt şirketinizin web sitesinde etki alanınızın ad sunucularını düzenleyebileceğiniz yeri bulun.

2. Aşağıdaki tabloda yer alan değerleri kullanarak iki ad sunucusu kaydı oluşturun veya var olan ad sunucusu kayıtlarını bu değerlerle eş olacak şekilde düzenleyin.

    ||
    |:-----|:-----|
    |İlk ad sunucusu  <br/> |Cloudflare tarafından sağlanan ad sunucusu değerini kullanın.  <br/> |
    |İkinci ad sunucusu  <br/> |Cloudflare tarafından sağlanan ad sunucusu değerini kullanın.  <br/> |

    > [!TIP]
    > En az iki ad sunucu kaydı kullanabilirsiniz. Listelenen başka ad sunucuları varsa bunları silmeniz gerekir. 
  
3. Değişikliklerinizi kaydedin.

> [!NOTE]
> Ad sunucusu kaydı güncelleştirmelerinizin İnternet DNS sistemi genelinde güncelleştirilmesi birkaç saat sürebilir. Ardından, Microsoft e-posta ve diğer hizmetlerinizin hepsi etki alanınız ile çalışacak şekilde ayarlanır. 
  
### <a name="add-a-txt-record-for-verification"></a>Doğrulama için bir TXT kaydı ekleme

Etki alanınızı Microsoft ile kullanmadan önce bu etki alanına sahip olduğundan emin olarız. Etki alanı kayıt şirketinizin hesabında oturum açabilme ve DNS kaydı oluşturabilme özelliği, Microsoft'a etki alanının sahibi olduğunu kanıtlar.
  
> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. Dilerseniz bu kaydı daha sonra silebilirsiniz. 
  
1. Kullanmaya devam etmek için bu bağlantıyı kullanarak Cloudflare'da etki alanları [sayfanıza gidin](https://www.cloudflare.com/a/login). Önce oturum açmanız istenir.
  
1. Giriş sayfasında, güncelleştirmek istediğiniz etki alanını seçin. 

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Güncelleştirmek istediğiniz etki alanını seçin.":::

1. Etki alanınıza genel bakış sayfasında DNS'yi **seçin**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="DNS'yi seçin.":::
  
1. DNS yönetimi sayfasında +Kayıt **ekle'yi seçin**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Kayıt ekle'yi seçin.":::

1. Açılan listeden TXT türünü seçin ve bu tablodaki değerleri yazın veya kopyalayıp yapıştırın. 

    | **Tür** | **Ad** | **TTL** | **İçerik** |
    |:-----|:-----|:-----|:----|
    |TXT  <br/> |@  <br/> |30 dakika  <br/> |MS=ms *XXXXXXXX*  <br/> **Not:** Bu bir örnektir. Tablodan **, belirli Hedef veya Adres Noktaları** değerinizi burada kullanın. [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)    |

1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="Kayıt ekle'yi seçin.":::

   Yeni oluşturduğunuz kaydın İnternet genelinde güncelleştirilebilmesi için devam etmeden önce birkaç dakika bekleyin.

Kaydı etki alanı kayıt şirketinizin sitesinde eklediknize göre, Microsoft'a geri dönüp kaydı arayabilirsiniz. Microsoft doğru TXT kaydını bulduğunda, etki alanınız doğrulanır.
  
Bir dosyada kaydı Microsoft 365:
  
1. Yönetim merkezinde Etki Alanları'nın **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**gidin**</a>.

1. Etki Alanları sayfasında, doğrulamakta olduğunuz etki alanını seçin ve sonra da Kurulumu **başlat'ı seçin**. 

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. **Devam'ı seçin**.
  
1. Etki alanını **doğrulama sayfasında** Doğrula'ya **tıklayın**.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Etki alanınıza gelen e-postanın Microsoft'a göndernsin için MX kaydı ekleme

1. Kullanmaya devam etmek için bu bağlantıyı kullanarak Cloudflare'da etki alanları [sayfanıza gidin](https://www.cloudflare.com/a/login). Önce oturum açmanız istenir.
  
1. Giriş sayfasında, güncelleştirmek istediğiniz etki alanını seçin. 

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Güncelleştirmek istediğiniz etki alanını seçin.":::

1. Etki alanınıza genel bakış sayfasında DNS'yi **seçin**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="DNS'yi seçin.":::

1. DNS yönetimi sayfasında +Kayıt **ekle'yi seçin**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Kayıt ekle'yi seçin.":::

1. Açılan listeden MX türünü seçin ve bu tablodaki değerleri yazın veya kopyalayıp yapıştırın. 

   | **Tür** | **Ad** | **Posta sunucusu** |  **TTL** | **Öncelik** |
   |:-----|:-----|:-----|:-----|:-----|
   |MX  <br/> |@  <br/> |*\<domain-key\>*  .mail.protection.outlook.com  <br/> **Not:** Hesap hesabınızdan *\<domain-key\>* Microsoft 365.   [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md) |30 dakika  <br/> | 1  <br/> Öncelik hakkında daha fazla bilgi için bkz. [MX önceliği nedir?](../setup/domains-faq.yml) <br/>|

1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-save.png" alt-text="Kayıt ekle'yi seçin."::: 

1. MX Kayıtları bölümünde listelenen başka **MX kayıtları** varsa, Düzenle'yi ve ardından **Sil'i** seçerek bunları **silin**. 

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-delete.png" alt-text="Sil'i seçin.":::  

1. Onay iletişim kutusunda, değişikliklerinizi onaylamak **için Sil'i** seçin. 

### <a name="add-the-cname-record-required-for-microsoft"></a>Microsoft için gereken CNAME kaydını ekleme

1. Kullanmaya devam etmek için bu bağlantıyı kullanarak Cloudflare'da etki alanları [sayfanıza gidin](https://www.cloudflare.com/a/login). Önce oturum açmanız istenir.

1. Giriş sayfasında, güncelleştirmek istediğiniz etki alanını seçin. 

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Güncelleştirmek istediğiniz etki alanını seçin.":::

1. Etki alanınıza genel bakış sayfasında DNS'yi **seçin**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="DNS'yi seçin.":::

1. DNS yönetimi **sayfasında +** Kayıt **ekle'yi seçin**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Kayıt ekle'yi seçin.":::

1. Açılan listeden CNAME türünü seçin ve bu tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın. 

    | Tür | Name | Hedef | TTL |
    |:-----|:-----|:-----|:-----|
    | CNAME  <br/> | autodiscover  <br/> | autodiscover.outlook.com  <br/> | Otomatik <br/> |
  
1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Kaydet'i seçin."::: 

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa, etki alanınız için yeni bir SPF Microsoft 365. Bunun yerine, Microsoft 365 her iki değer kümesi de içeren tek *bir SPF* kaydına sahip olmak için gerekli veri değerlerini geçerli kayda ekleyin. 
  
1. Kullanmaya devam etmek için bu bağlantıyı kullanarak Cloudflare'da etki alanları [sayfanıza gidin](https://www.cloudflare.com/a/login). Önce oturum açmanız istenir.  
  
1. Giriş sayfasında, güncelleştirmek istediğiniz etki alanını seçin. 

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Güncelleştirmek istediğiniz etki alanını seçin.":::

1. Etki alanınıza genel bakış sayfasında DNS'yi **seçin**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="DNS'yi seçin.":::

1. DNS yönetimi sayfasında +Kayıt **ekle'yi seçin**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Kayıt ekle'yi seçin.":::

1. Açılan listeden TXT türünü seçin ve bu tablodaki değerleri yazın veya kopyalayıp yapıştırın. 

    | Tür | Name | TTL | İçerik |
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |@  <br/> |30 dakika  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Not:** Tüm boşlukların doğru kalması için bu girdiyi kopyalayıp yapıştırarak bu dosyayı yapıştırın.   |

1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="Kaydet'i seçin."::: 

## <a name="advanced-option-skype-for-business"></a>Gelişmiş seçenek: Skype Kurumsal

Yalnızca, bu seçeneği yalnızca, Skype Kurumsal yanı sıra sohbet, konferans aramaları ve görüntülü aramalar gibi çevrimiçi iletişim hizmetleri için Microsoft Teams. Skype için 4 kayıt gerekir: Oturum açma ve kullanıcıları hizmete bağlamak için 2 kullanıcı-kullanıcı iletişim için SRV kaydı ve 2 CNAME kaydı.

### <a name="add-the-two-required-srv-records"></a>Gerekli iki SRV kaydı ekleme

> [!IMPORTANT]
> Bu işlevselliğin cloudflare tarafından kullanılabilir halellnden sorumlu olduğunu unutmayın. Aşağıdaki adımlarla geçerli Cloudflare GUI (Grafik Kullanıcı Arabirimi) arasında farklar görüyorsanız, [Cloudflare Kullanıcı Arabirimi'Community](https://community.cloudflare.com/). 

1. Kullanmaya devam etmek için bu bağlantıyı kullanarak Cloudflare'da etki alanları [sayfanıza gidin](https://www.cloudflare.com/a/login). Önce oturum açmanız istenir.

1. Giriş sayfasında, güncelleştirmek istediğiniz etki alanını seçin. 

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Güncelleştirmek istediğiniz etki alanını seçin.":::
  
1. Etki alanınıza genel bakış sayfasında DNS'yi **seçin**.
  
    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="DNS'yi seçin.":::

1. DNS yönetimi sayfasında +Kayıt **ekle'yi seçin**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Kayıt ekle'yi seçin.":::

1. Açılan listeden SRV türünü seçin ve bu tablodaki değerleri yazın veya kopyalayıp yapıştırın.

    | **Tür** | **Ad** | **Hizmet** | **Protokol** |  **TTL** | **Öncelik** | **Ağırlık** | **Bağlantı Noktası** | **Hedef** |
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV| *E-domain_name*; örneğin, contoso.com | _sip |TLS |30 dakika | 100|1 |443 |sipfed.online.lync.com  |
    |SRV|_sipfederationtls | TCP|*E-domain_name*; örneğin, contoso.com   |30 dakika |100 |1 |5061 | sipfed.online.lync.com |
  
1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-srv-save.png" alt-text="Kaydet'i seçin."::: 

1. Tablonun ikinci satırına değerleri kopyalayıp diğer SRV kaydını ekleyin. 

> [!NOTE]
>  Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydı ekleme
  
1. Kullanmaya devam etmek için bu bağlantıyı kullanarak Cloudflare'da etki alanları [sayfanıza gidin](https://www.cloudflare.com/a/login). Önce oturum açmanız istenir.

1. Giriş sayfasında, güncelleştirmek istediğiniz etki alanını seçin. 

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Güncelleştirmek istediğiniz etki alanını seçin.":::

1. Etki alanınıza genel bakış sayfasında DNS'yi **seçin**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="DNS'yi seçin.":::

1. DNS yönetimi sayfasında +Kayıt **ekle'yi seçin**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Kayıt ekle'yi seçin.":::

1. Açılan listeden CNAME türünü seçin ve bu tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

    |**Tür**|**Ad**|**Hedef**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |1 Saat  <br/> |
    |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |1 Saat  <br/> |
  
1. **Kaydet'i seçin**. 

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Kaydet'i seçin.":::  

1. Tablonun ikinci satırına değerleri kopyalayıp diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Gelişmiş seçenek: Mobil Cihazlar için Intune ve Mobil Microsoft 365

Bu hizmet, etki alanınıza bağlı mobil cihazların güvenliğini sağlamanıza ve uzaktan yönetmenize yardımcı olur. Mobil Cihaz Yönetimi'nin, kullanıcıların cihazları hizmete kaydedeni için 2 CNAME kaydı olması gerekir.

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydı ekleme

1. Kullanmaya devam etmek için bu bağlantıyı kullanarak Cloudflare'da etki alanları [sayfanıza gidin](https://www.cloudflare.com/a/login). Önce oturum açmanız istenir.

1. Giriş sayfasında, güncelleştirmek istediğiniz etki alanını seçin. 

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Güncelleştirmek istediğiniz etki alanını seçin.":::

1. Etki alanınıza genel bakış sayfasında DNS'yi **seçin**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="DNS'yi seçin.":::

1. DNS yönetimi sayfasında +Kayıt **ekle'yi seçin**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Kayıt ekle'yi seçin.":::

1. Açılan listeden CNAME türünü seçin ve bu tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

    |**Tür**|**Ad**|**Hedef**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |1 Saat  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |1 Saat  <br/> |
  
1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Kaydet'i seçin."::: 

1. Tablonun ikinci satırına değerleri kopyalayıp diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.