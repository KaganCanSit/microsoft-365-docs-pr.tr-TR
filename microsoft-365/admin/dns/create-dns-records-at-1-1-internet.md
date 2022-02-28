---
title: Bağlan IONOS'ta DNS kayıtlarınızı 1'den&'e kadar Microsoft 365
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
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
ms.assetid: 5762c3ca-1de2-4999-bfe5-4c5e25a8957e
description: Microsoft için 1&1 IONOS'ta etki alanlarınızı doğrulamayı ve e-posta, Skype Kurumsal Online ve diğer hizmetler için DNS kayıtlarını ayarlamayı öğrenin.
ms.openlocfilehash: 8dc3a509a05e55e984d1c06e59319661a19019e7
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989881"
---
# <a name="connect-your-dns-records-at-ionos-by-11-to-microsoft-365"></a>Bağlan IONOS'ta DNS kayıtlarınızı 1'den&'e kadar Microsoft 365

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**. 

DNS barındırma sağlayıcınız IONOS 1&1 ise, bu makaledeki adımları kullanarak etki alanlarınızı doğrulayın ve e-posta, Skype Kurumsal Online, gibi dns kayıtlarını ayarlayın.

## <a name="before-you-begin"></a>Başlamadan önce

Etki alanınız için DNS kayıtlarını ayarlarken iki seçeneğiniz vardır:

- [**Etki Alanı Bağlan**](#use-domain-connect-to-verify-and-set-up-your-domain) Etki alanını başka bir e-posta hizmeti sağlayıcısıyla ayarlamadısanız, yeni etki alanınızı otomatik olarak doğrulamak ve yeni etki alanıyla birlikte kullanmak üzere ayarlamak için Etki alanı Bağlan adımlarını Microsoft 365. 

    VEYA

- [**El ile adımları kullanma**](#create-dns-records-with-manual-setup) Aşağıdaki el ile adımları kullanarak etki alanınızı doğrulayın ve etki alanı kayıt şirketine eklemek istediğiniz kayıtların ne zaman ve hangi kayıtları seçeceklerini seçin. Bu sayede, örneğin size uygun bir şekilde yeni MX (posta) kayıtları ayarlanır. 

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Etki Bağlan doğrulamak ve ayarlamak için Etki Alanı Yöneticisi'ne

IONOS'larınızı 1 ile 1 veya 1 etki alanıyla otomatik olarak doğrulamak&için bu Microsoft 365:

1. Etki Microsoft 365 yönetim merkezi Etki **Ayarlar** >  seçin ve ardından ayarlamak istediğiniz etki alanını seçin.<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-1.png" alt-text="Bu listeden etki Microsoft 365.":::

1. Üç noktayı (diğer eylemler) seçin ve **>'ı seçin**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. Etki alanınızı nasıl bağlamak istiyor musunuz? sayfasında **Devam'ı seçin**.   

1. DNS kayıtları ekle sayfasında DNS kayıtları **ekle'yi seçin**.

1. IONOS'a göre 1&1 oturum açma sayfasında, hesabınızla oturum açın, Oturum **Aç'Bağlan ve İzin Ver'i** **seçin**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-3.png" alt-text="Seç'Bağlan sonra da İzin Ver'i seçin.":::

    Bu, e-posta için etki alanı Microsoft 365. 

## <a name="create-dns-records-with-manual-setup"></a>El ile kurulumla DNS kayıtları oluşturma

IONOS'a 1 veya 1&bu kayıtları ekledikten sonra, etki alanınız etki alanınız Microsoft hizmetleri.
  
> [!CAUTION]
> 1 veya 1 ile IONOS&1 etki alanının hem MX kaydı hem de en üst düzey Otomatik Bulma CNAME kaydının olmasına izin vermemektedir. Bu, Microsoft için e-postayı yapılandırma Exchange Online sınırlar. Bu sorunun geçici bir çözümü vardır, ancak bu çözümü yalnızca  IONOS'ta 1 veya 1 adede kadar alt etki alanı oluşturma deneyimi&öneririz.
> Bu hizmet sınırlamasına rağmen IONOS'ta kendi Microsoft DNS kayıtlarınızı 1&1 olarak yönetmeyi seçerseniz, bu makaledeki adımları izleyin ve etki alanını doğrulayın ve e-posta, Skype Kurumsal Online, gibi DNS kayıtlarını ayarlayın.[](../setup/domains-faq.yml)
  
> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlar ile ilgili sorunlar için bkz. Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra [sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md).
  
### <a name="add-a-txt-record-for-verification"></a>Doğrulama için bir TXT kaydı ekleme

Etki alanınızı Microsoft ile kullanmadan önce bu etki alanına sahip olduğundan emin olarız. Etki alanı kayıt şirketinizin hesabında oturum açabilme ve DNS kaydı oluşturabilme özelliği, Microsoft'a etki alanının sahibi olduğunu kanıtlar.
  
> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. Dilerseniz bu kaydı daha sonra silebilirsiniz.
  
1. Kullanmaya devam etmek için bu bağlantıyı kullanarak IONOS'ta 1&1'de etki [alanları sayfanıza gidin](https://my.1and1.com/). Oturum açmanız istenir.

1. **Menü'yü** seçin ve ardından Etki Alanları ve **SSL'yi seçin**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Etki Alanları ve SSL'yi seçin.":::
  
1. Güncelleştirmek **istediğiniz** etki alanına yönelik Eylemler'in altında, dişli denetimine ve sonra **DNS'e seçin**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Açılan listeden DNS'yi seçin.":::

1. Kayıt **ekle'yi seçin**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Kayıt ekle'yi seçin.":::

1. **TXT bölümünü** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-4.png" alt-text="TXT bölümünü seçin.":::

1. DNS kaydı ekle sayfasında, yeni kayıt kutularına aşağıdaki tabloda yer alan değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

    |**Ana bilgisayar adı** <br/> |**Değer** <br/> | **TTL**
    |:-----|:-----|:-----|
    |(Bu alanı boş bırakın)  <br/> |MS=ms *XXXXXXXX*  <br/> NOT: Bu bir örnektir. Tablodan **, belirli Hedef veya Adres Noktaları** değerinizi burada kullanın. [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)          | 1 saat |

1. **Kaydet**'i seçin.
  
    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-5.png" alt-text="Kaydet'i seçin.":::
  
    Yeni oluşturduğunuz kaydın İnternet genelinde güncelleştirilebilmesi için devam etmeden önce birkaç dakika bekleyin.

Kaydı etki alanı kayıt şirketinizin sitesinde eklediknize göre, Microsoft 365'e geri dönüp kaydın Microsoft 365 için istekte bulundurabilirsiniz. Microsoft doğru TXT kaydını bulduğunda, etki alanınız doğrulanır.

Bir dosyada kaydı Microsoft 365:
  
1. Yönetim merkezinde Etki Alanları'nın **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**gidin**</a>.

1. Etki Alanları sayfasında, doğrulamakta olduğunuz etki alanını seçin ve sonra da Kurulumu **başlat'ı seçin**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. **Devam'ı seçin**.
  
1. Etki alanını **doğrulama sayfasında** Doğrula'ya **tıklayın**.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.
  
### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Etki alanınıza gelen e-postanın Microsoft'a göndernsin için MX kaydı ekleme
  
> [!NOTE]
> Kayıtlı kullanıcınız varsa burada 1und1.de [oturum açma](https://go.microsoft.com/fwlink/?linkid=859152). 

1. Kullanmaya devam etmek için bu bağlantıyı kullanarak IONOS'ta 1&1'de etki [alanları sayfanıza gidin](https://my.1and1.com/). Oturum açmanız istenir.

1. **Menü'yü** seçin ve ardından Etki Alanları ve **SSL'yi seçin**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Etki Alanları ve SSL'yi seçin.":::
  
1. Güncelleştirmek **istediğiniz** etki alanına yönelik Eylemler'in altında, dişli denetimine ve sonra **DNS'e seçin**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Açılan listeden DNS'yi seçin.":::

1. Kayıt **ekle'yi seçin**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Kayıt ekle'yi seçin.":::

1. **MX bölümünü** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-MX.png" alt-text="MX bölümünü seçin.":::
  
1. DNS kaydı ekle sayfasında, yeni kayıt kutularına aşağıdaki tabloda yer alan değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

    | **Ana bilgisayar adı**| **Yönlendirme** |**Öncelik**| **TTL** |
    |:-----|:-----|:-----| :-----|
    |  @  | *\<domain-key\>*  .mail.protection.outlook.com  <br/>  NOT: Microsoft hesabınızla \<domain-key\> oturum açın. [How do I find this?](../get-help-with-domains/information-for-dns-records.md)          |10  <br/> Öncelik hakkında daha fazla bilgi için bkz. [MX önceliği nedir?](../setup/domains-faq.yml) | 1 saat |
  
1. **Kaydet**'i seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-MX-Save.png" alt-text="Kaydet'i seçin.":::

1. Listede zaten başka MX kaydı varsa, Kayıt ekle sayfasında Kayıt çöp kutusu **sil'i** seçerek bunların **her birini** silin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Delete.png" alt-text="Kaydı sil'i seçin.":::

### <a name="add-the-cname-record-required-for-microsoft"></a>Microsoft için gereken CNAME kaydını ekleme

> [!NOTE]
> Kayıtlı kullanıcınız varsa burada 1und1.de [oturum açma](https://go.microsoft.com/fwlink/?linkid=859152). 
  
1. Kullanmaya devam etmek için bu bağlantıyı kullanarak IONOS'ta 1&1'de etki [alanları sayfanıza gidin](https://my.1and1.com/). Oturum açmanız istenir.

1. **Menü'yü** seçin ve ardından Etki Alanları ve **SSL'yi seçin**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Etki Alanları ve SSL'yi seçin.":::
  
1. Güncelleştirmek **istediğiniz** etki alanına yönelik Eylemler'in altında, dişli denetimine ve sonra **DNS'e seçin**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Açılan listeden DNS'yi seçin.":::

    Şimdi iki alt etki alanı oluşturacak ve her birine **Diğer Ad** değeri ayarlayacaksınız.<br/>(Bu gereklidir çünkü 1&1 IONOS yalnızca bir üst düzey CNAME kaydını destekler, ancak Microsoft için birkaç CNAME kaydı gereklidir.)<br/>İlk olarak, Otomatik Bulma alt etki alanını oluşturacaksınız.

1. Alt **Etki Alanları'ı seçin**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Alt Etki Alanı'ı seçin.":::
  
1. Alt **etki alanı ekle'yi seçin**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Alt etki alanı ekle'yi seçin.":::
  
1. Yeni **alt etki alanı için** Alt etki alanı ekle kutusunda, yalnızca aşağıdaki tabloda yer alan Add **subdomain** değerini yazın veya kopyalayıp yapıştırın. ( **Diğer Ad** değerini sonraki adımlardan birinde ekleyeceksiniz.)

    |**Alt etki alanı ekleme**| **Diğer Ad** |
    |:-----|:-----|
    |autodiscover  <br/> | autodiscover.outlook.com |

1. Az **önce** oluşturduğunuz **otomatik bulma** alt etki alanı eylemleri'nin altında dişli denetimine tıklayın ve sonra açılan listeden **DNS'yi** seçin. <br/>

1. Kayıt **ekle'yi** seçin ve ardından **CNAME bölümünü** seçin.

1. **Diğer Ad:** kutusunda, yalnızca aşağıdaki tabloda verilen **Diğer Ad** değerini yazın veya kopyalayıp yapıştırın. <br/>

    |**Alt etki alanı ekleme**| **Diğer Ad** |
    |:-----|:-----|
    |autodiscover  <br/> | autodiscover.outlook.com |
  
1. **Kaydet**'i seçin.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa Microsoft için yeni bir SPF kaydı oluşturun. Bunun yerine, her iki değer kümesi de içeren tek  *bir SPF*  kaydına sahip olmak için gerekli Microsoft değerlerini geçerli kayda ekleyin. Örneklere mi ihtiyacınız var? Microsoft için bu [Dış Etki Alanı Adı Sistemi kayıtlarına göz atabilirsiniz](../../enterprise/external-domain-name-system-records.md). SPF kaydınızı doğrulamak için şuSPF doğrulama araçlarından [birini kullanabilirsiniz](../setup/domains-faq.yml). 
  
> [!NOTE]
> Kayıtlı kullanıcınız varsa burada 1und1.de [oturum açma](https://go.microsoft.com/fwlink/?linkid=859152). 
  
1. Kullanmaya devam etmek için bu bağlantıyı kullanarak IONOS'ta 1&1'de etki [alanları sayfanıza gidin](https://my.1and1.com/). Oturum açmanız istenir.

1. **Menü'yü** seçin ve ardından Etki Alanları ve **SSL'yi seçin**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Etki Alanları ve SSL'yi seçin.":::
  
1. Güncelleştirmek **istediğiniz** etki alanına yönelik Eylemler'in altında, dişli denetimine ve sonra **DNS'e seçin**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Açılan listeden DNS'yi seçin.":::

1. Kayıt **ekle'yi seçin**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Kayıt ekle'yi seçin.":::

1. **SPF (TXT) bölümünü** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SPFTXT.png" alt-text="SPF (TXT) bölümünü seçin.":::

1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın. <br/>

    |**Tür**|**Ana bilgisayar adı**|**Değer**| **TTL** |
    |:-----|:-----|:-----|:-----|
    |SPF (TXT)  <br/> |(Bu alanı boş bırakın.)  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Not:** Tüm boşlukların doğru kalması için bu girdiyi kopyalayıp yapıştırarak bu dosyayı yapıştırın. | 1 saat |
  
1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SPFTXT-Save.png" alt-text="Kaydet'i seçin.":::

## <a name="advanced-option-skype-for-business"></a>Gelişmiş seçenek: Skype Kurumsal

Yalnızca, bu seçeneği yalnızca, Skype Kurumsal yanı sıra sohbet, konferans aramaları ve görüntülü aramalar gibi çevrimiçi iletişim hizmetleri için Microsoft Teams. Skype için 4 kayıt gerekir: Oturum açma ve kullanıcıları hizmete bağlamak için 2 kullanıcı-kullanıcı iletişim için SRV kaydı ve 2 CNAME kaydı.

### <a name="add-two-additional-cname-records"></a>İki CNAME kaydı daha ekleme
  
1. Kullanmaya devam etmek için bu bağlantıyı kullanarak IONOS'ta 1&1'de etki [alanları sayfanıza gidin](https://my.1and1.com/). Oturum açmanız istenir.

1. **Menü'yü** seçin ve ardından Etki Alanları ve **SSL'yi seçin**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Etki Alanları ve SSL'yi seçin.":::
  
1. Güncelleştirmek **istediğiniz** etki alanına yönelik Eylemler'in altında, dişli denetimine ve sonra **DNS'e seçin**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Açılan listeden DNS'yi seçin.":::

    Şimdi iki alt etki alanı oluşturacak ve her birine **Diğer Ad** değeri ayarlayacaksınız.<br/>(Bu gereklidir çünkü 1&1 IONOS yalnızca bir üst düzey CNAME kaydını destekler, ancak Microsoft için birkaç CNAME kaydı gereklidir.)<br/>İlk olarak, lyncdiscover alt etki alanı oluşturabilirsiniz.

1. Alt **Etki Alanları'ı seçin**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Alt Etki Alanı'ı seçin.":::
  
1. Alt **etki alanı ekle'yi seçin**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Alt etki alanı ekle'yi seçin.":::

1. Yeni **alt etki alanı için** Alt etki alanı ekle kutusunda, yalnızca aşağıdaki tabloda yer alan Add **subdomain** değerini yazın veya kopyalayıp yapıştırın. ( **Diğer Ad** değerini sonraki adımlardan birinde ekleyeceksiniz.)<br/> 

    |**Alt etki alanı ekleme**|**Diğer Ad**|
    |:-----|:-----|
    |lyncdiscover   |webdir.online.lync.com  |

1. Az **önce** oluşturduğunuz **lyncdiscover** alt etki alanı eylemleri'nin altında dişli denetimine tıklayın ve açılan listeden **DNS'yi** seçin. <br/>

1. Kayıt **ekle'yi** seçin ve ardından **CNAME bölümünü** seçin.

1. **Diğer Ad:** kutusunda, yalnızca aşağıdaki tabloda verilen **Diğer Ad** değerini yazın veya kopyalayıp yapıştırın. <br/>

    |**Alt Etki Alanı Oluştur**|**Diğer Ad**|
    |:-----|:-----|
    |lyncdiscover  <br/> |webdir.online.lync.com  <br/> |

1. Başka bir alt etki alanı (SIP) oluşturma: <br/>Alt **etki alanı ekle'yi seçin**.

1. Yeni **alt etki alanı için** Alt etki alanı ekle kutusunda, yalnızca aşağıdaki tabloda yer alan Add **subdomain** değerini yazın veya kopyalayıp yapıştırın. ( **Diğer Ad** değerini sonraki adımlardan birinde ekleyeceksiniz.) <br/>

    |**Alt etki alanı ekleme**|**Diğer Ad**|
    |:-----|:-----|
    |sip  <br/> |sipdir.online.lync.com  <br/> |

1. Yeni **oluşturduğunuz** alt etki alanı için Eylemler'in altında, dişli denetimi seçin ve sonra da açılan listeden **DNS'yi** seçin. <br/>

1. Kayıt **ekle'yi seçin**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Kayıt ekle'yi seçin.":::

1. **CNAME bölümünü** seçin.

1. Diğer Ad **: kutusunda** , yalnızca aşağıdaki tabloda yer alan Diğer Ad **değerini yazın** veya kopyalayıp yapıştırın. 

    |**Alt Etki Alanı Oluştur**|**Diğer Ad**|
    |:-----|:-----|
    |sip  <br/> |sipdir.online.lync.com  <br/> |

1. Farkındayım uyarı kutusunun **onay kutusunu seçin ve** sonra da Kaydet'i **seçin**.

## <a name="add-the-two-srv-records-required-for-microsoft"></a>Microsoft için gereken iki SRV kaydı ekleme
  
> [!NOTE]
> Kayıtlı kullanıcınız varsa burada 1und1.de [oturum açma](https://go.microsoft.com/fwlink/?linkid=859152). 
  
1. Kullanmaya devam etmek için bu bağlantıyı kullanarak IONOS'ta 1&1'de etki [alanları sayfanıza gidin](https://my.1and1.com/). Oturum açmanız istenir.

1. **Menü'yü** seçin ve ardından Etki Alanları ve **SSL'yi seçin**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Etki Alanları ve SSL'yi seçin.":::
  
1. Güncelleştirmek **istediğiniz** etki alanına yönelik Eylemler'in altında, dişli denetimine ve sonra **DNS'e seçin**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Açılan listeden DNS'yi seçin.":::

1. Kayıt **ekle'yi seçin**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Kayıt ekle'yi seçin.":::

1. **SRV bölümünü** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SRV.png" alt-text="SRV bölümünü seçin.":::

1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın. <br/>

    |**Tür**|**Hizmet**|**Protokol**|**Ana bilgisayar adı**|**Yönlendirme**|**Öncelik**|**Ağırlık**|**Bağlantı Noktası**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV  <br/> |_sip  <br/> |tls  <br/> |(Bu alanı boş bırakın.)  <br/> |sipdir.online.lync.com  <br/> |100  <br/> |1  <br/> |443  <br/> |1 saat  <br/> |
    |SRV  <br/> |_sipfederationtls  <br/> |tcp  <br/> |(Bu alanı boş bırakın.)  <br/> |sipfed.online.lync.com  <br/> |100  <br/> |1  <br/> |5061  <br/> |1 saat <br/> |  
  
1. **Kaydet**'i seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SRV-Save.png" alt-text="Kaydet'i seçin.":::

1. Diğer SRV kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlar ile ilgili sorunlar için bkz. Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra [sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md). 

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Gelişmiş seçenek: Mobil Cihazlar için Intune ve Mobil Microsoft 365

Bu hizmet, etki alanınıza bağlı mobil cihazların güvenliğini sağlamanıza ve uzaktan yönetmenize yardımcı olur. Mobil Cihaz Yönetimi'nin, kullanıcıların cihazları hizmete kaydedeni için 2 CNAME kaydı olması gerekir.

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydı ekleme

> [!IMPORTANT]
> Diğer CNAME kayıtları için kullanılan alt etki alanı yordamını izleyin ve değerleri aşağıdaki tablodan girin. 
  
1. Kullanmaya devam etmek için bu bağlantıyı kullanarak IONOS'ta 1&1'de etki [alanları sayfanıza gidin](https://my.1and1.com/). Oturum açmanız istenir.

1. **Menü'yü** seçin ve ardından Etki Alanları ve **SSL'yi seçin**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Etki Alanları ve SSL'yi seçin.":::
  
1. Güncelleştirmek **istediğiniz** etki alanına yönelik Eylemler'in altında, dişli denetimine ve sonra **DNS'e seçin**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Açılan listeden DNS'yi seçin.":::

    Şimdi iki alt etki alanı oluşturacak ve her birine **Diğer Ad** değeri ayarlayacaksınız.<br/>(Bu gereklidir çünkü 1&1 IONOS yalnızca bir üst düzey CNAME kaydını destekler, ancak Microsoft için birkaç CNAME kaydı gereklidir.)<br/>İlk olarak, lyncdiscover alt etki alanı oluşturabilirsiniz.

1. Alt **Etki Alanları'ı seçin**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Alt Etki Alanı'ı seçin.":::
  
1. Alt **etki alanı ekle'yi seçin**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Alt etki alanı ekle'yi seçin.":::

1. Yeni **alt etki alanı için** Alt etki alanı ekle kutusunda, yalnızca aşağıdaki tabloda yer alan Add **subdomain** değerini yazın veya kopyalayıp yapıştırın. ( **Diğer Ad** değerini sonraki adımlardan birinde ekleyeceksiniz.)<br/> 

    |**Alt etki alanı ekleme**|**Diğer Ad**|
    |:-----|:-----|
    |enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> |

1. Yeni **oluşturduğunuz** **enterpriseregistration** alt etki alanı için Eylemler'in altında, dişli denetimine tıklayın ve sonra açılan listeden **DNS'yi** seçin. <br/>

1. Kayıt **ekle'yi** seçin ve ardından **CNAME bölümünü** seçin.

1. **Diğer Ad:** kutusunda, yalnızca aşağıdaki tabloda verilen **Diğer Ad** değerini yazın veya kopyalayıp yapıştırın. <br/>

    |**Alt etki alanı ekleme**|**Diğer Ad**|
    |:-----|:-----|
    |enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> |

1. Başka bir alt etki alanı oluşturma: <br/>Alt **etki alanı ekle'yi seçin**.

1. Yeni **alt etki alanı için** Alt etki alanı ekle kutusunda, yalnızca aşağıdaki tabloda yer alan Add **subdomain** değerini yazın veya kopyalayıp yapıştırın. ( **Diğer Ad** değerini sonraki adımlardan birinde ekleyeceksiniz.) <br/>

    |**Alt etki alanı ekleme**|**Diğer Ad**|
    |:-----|:-----|
    |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |

1. Yeni **oluşturduğunuz** **enterpriseenrollment** alt etki alanı için Eylemler'in altında, dişli denetimine tıklayın ve sonra açılan listeden **DNS'yi** seçin. <br/>

1. Kayıt **ekle'yi seçin**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Kayıt ekle'yi seçin.":::

1. **CNAME bölümünü** seçin.

1. Diğer Ad **: kutusunda** , yalnızca aşağıdaki tabloda yer alan Diğer Ad **değerini yazın** veya kopyalayıp yapıştırın. 

    |**Alt Etki Alanı Oluştur**|**Diğer Ad**|
    |:-----|:-----|
    |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |

1. Farkındayım uyarı kutusunun **onay kutusunu seçin ve** sonra da Kaydet'i **seçin**.