---
title: Bağlan Namecheap'a DNS kayıtlarınızı Microsoft 365
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
ms.assetid: 54ae2002-b38e-43a1-82fa-3e49d78fda56
description: Microsoft için Namecheap'da etki alanlarınızı doğrulamayı ve e-posta, Skype Kurumsal Online ve diğer hizmetler için DNS kayıtlarını ayarlamayı öğrenin.
ms.openlocfilehash: 146b76ef95a725faa3457eaf1795b153133cef92
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315001"
---
# <a name="connect-your-dns-records-at-namecheap-to-microsoft-365"></a>Bağlan Namecheap'a DNS kayıtlarınızı Microsoft 365

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**. 
  
DNS barındırma sağlayıcınız Namecheap ise, bu makaledeki adımları izleyin ve etki alanınızı doğrulayın ve e-posta, Skype Kurumsal Online, gibi DNS kayıtlarını ayarlayın.
  
Namecheap'a bu kayıtları ekledikten sonra, etki alanınız etki alanınız Microsoft hizmetleri.
  
> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 
  
## <a name="add-a-txt-record-for-verification"></a>Doğrulama için bir TXT kaydı ekleme

Etki alanınızı Microsoft ile kullanmadan önce bu etki alanına sahip olduğundan emin olarız. Etki alanı kayıt şirketinizin hesabında oturum açabilme ve DNS kaydı oluşturabilme özelliği, Microsoft'a etki alanının sahibi olduğunu kanıtlar.
  
> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. Dilerseniz bu kaydı daha sonra silebilirsiniz. 
  
1. Kullanmaya devam etmek için bu bağlantıyı kullanarak Namecheap'da etki alanları [sayfanıza gidin](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Oturum açma ve Devam'a girmeniz istenir.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Namecheap'ta oturum açma.":::

1. Giriş sayfasındaki **Hesap'ın** altında, açılan **listeden** Etki Alanı Listesi'ne tıklayın. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Açılan listeden Etki Alanı Listesi'ne tıklayın.":::

1. Etki Alanı Listesi sayfasında, düzenlemek istediğiniz etki alanını seçin ve sonra da Yönet'i **seçin**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Yönet'i seçin.":::

1. Gelişmiş **DNS'yi seçin**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Gelişmiş DNS'yi seçin.":::

1. ANA BILGISAYAR **KAYıTLARı bölümünde** Yeni KAYıT **EKLE'yi seçin**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Yenİ KAYıT EKLE'yi seçin.":::

1. Tür açılan **listesinde** **TXT Kaydı'ı seçin**.
    
    > [!NOTE]
    > YENI **KAYıT** EKLE'yi seçerek Tür açılan **liste otomatik olarak görüntülenir**. 

     :::image type="content" source="../../media/a5b40973-19b5-4c32-8e1b-1521aa971836.png" alt-text="TXT Kaydı'ni seçin.":::

1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.
    
    (Açılan **listeden TTL** değerini seçin.) 
    
    |**Tür**|**Ana Bilgisayar**|**Değer**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |@  <br/> |MS=ms *XXXXXXXX*  <br/>**Not:** Bu bir örnektir. Tablodan **, belirli Hedef veya Adres Noktaları** değerinizi burada kullanın.  [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md) |30 dak.  <br/> |

     :::image type="content" source="../../media/fe75c0fd-f85c-4bef-8068-edaf9779b7f1.png" alt-text="Tablodaki değerleri kopyalayıp yapıştırın.":::

1. Değişiklikleri Kaydet ( **onay** işareti) denetimine tıklayın. 

     :::image type="content" source="../../media/b48d2c67-66b5-4aa4-8e59-0c764f236fac.png" alt-text="Değişiklikleri Kaydet denetimine tıklayın.":::

1. Yeni oluşturduğunuz kaydın İnternet genelinde güncelleştirilebilmesi için devam etmeden önce birkaç dakika bekleyin.
    
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
  
1. Kullanmaya devam etmek için bu bağlantıyı kullanarak Namecheap'da etki alanları [sayfanıza gidin](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Oturum açma ve Devam'a girmeniz istenir.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Namecheap'ta oturum açma.":::

1. Giriş sayfasındaki **Hesap'ın** altında, açılan **listeden** Etki Alanı Listesi'ne tıklayın. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Açılan listeden Etki Alanı Listesi'ne tıklayın.":::

1. Etki **Alanı Listesi sayfasında** , düzenlemek istediğiniz etki alanını seçin ve sonra da Yönet'i **seçin**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Yönet'i seçin.":::

1. Gelişmiş **DNS'yi seçin**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Gelişmiş DNS'yi seçin.":::

1. POSTA **AYARLARI bölümünde** , **E-posta Yönlendirme** açılan **listesinden Özel** MX'i seçin. 
    
    (Sayfayı aşağı kaydırmanız gerekebilir.)

     :::image type="content" source="../../media/40199e2c-42cf-4c3f-9936-3cbe5d4e81a4.png" alt-text="Özel MX'i seçin."::: 

1. Yeni **Kayıt Ekle'yi seçin**.

     :::image type="content" source="../../media/8d169b81-ba48-4d51-84ea-a08fa1616457.png" alt-text="YENI KAYıT EKLE'YI SEÇIN.":::

1. Yeni kayıt kutularına, aşağıdaki tabloda yer alan değerleri yazın veya kopyalayıp yapıştırın.
    
    ( **Öncelik** kutusu, Değer kutusunun sağ tıklayını olan adlandırlanmamış **kutu** olur. Açılan **listeden TTL** değerini seçin.) 
    
    |**Tür**|**Ana Bilgisayar**|**Değer**|**Öncelik**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|
    |MX Kaydı  <br/> |@  <br/> |\<*domain-key*\>.mail.protection.outlook.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> **Not:** Microsoft hesabınızla  *\<domain-key\>*  oturum açın.  [How do I find this?](../get-help-with-domains/information-for-dns-records.md)          |0  <br/> Öncelik hakkında daha fazla bilgi için bkz. [MX önceliği nedir?](../setup/domains-faq.yml) <br/> |30 dak.  <br/> |

     :::image type="content" source="../../media/f3b76d62-5022-48c1-901b-8615a8571309.png" alt-text="Tablodaki değerleri kopyalayıp yapıştırın.":::

1. Değişiklikleri Kaydet ( **onay** işareti) denetimine tıklayın. 

     :::image type="content" source="../../media/ef4e3112-36d2-47c8-a478-136a565dd71d.png" alt-text="Değişiklikleri Kaydet denetimine tıklayın.":::

1. Başka MX kayıtları varsa, aşağıdaki iki adımlık işlemi kullanarak bunların her birini kaldırın:
    
    İlk olarak, **kaldırmak** istediğiniz kayıt için Sil 'i (çöp kutusu) seçin. 

     :::image type="content" source="../../media/7a7a751f-29c2-495f-8f55-98ca37ce555a.png" alt-text="Sil'i seçin.":::

    İkincisi, silme **işlemini onaylamak** için Evet'i seçin. 

     :::image type="content" source="../../media/85ebc0c7-8787-43ee-9e7b-647375b3345c.png" alt-text="Evet'i seçin.":::

    Bu yordamda daha önce eklediklerinden başka tüm MX kayıtlarını kaldırın.
  
## <a name="add-the-cname-record-required-for-microsoft"></a>Microsoft için gereken CNAME kaydını ekleme

1. Kullanmaya devam etmek için bu bağlantıyı kullanarak Namecheap'da etki alanları [sayfanıza gidin](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Oturum açma ve Devam'a girmeniz istenir.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Namecheap'ta oturum açma.":::

1. Giriş sayfasındaki **Hesap'ın** altında, açılan **listeden** Etki Alanı Listesi'ne tıklayın. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Etki Alanı Listesi'ne tıklayın.":::

1. Etki **Alanı Listesi sayfasında** , düzenlemek istediğiniz etki alanını seçin ve sonra da Yönet'i **seçin**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Yönet'i seçin.":::

1. Gelişmiş **DNS'yi seçin**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Gelişmiş DNS'yi seçin.":::

1. ANA BILGISAYAR **KAYıTLARı bölümünde** Yeni KAYıT **EKLE'yi seçin**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Yenİ KAYıT EKLE'yi seçin.":::

1. Tür açılan **listesinde** **CNAME Kaydı'ı seçin**.
    
    > [!NOTE]
    > YENI **KAYıT** EKLE'yi seçerek Tür açılan **liste otomatik olarak görüntülenir**. 

     :::image type="content" source="../../media/0898f3b2-06ab-4364-a86a-a603a25b39f4.png" alt-text="CNAME Kaydı'ı seçin.":::

1. Yeni kaydın boş kutularında, **Kayıt Türü** için **CNAME**'yi seçin ve ardından aşağıdaki tablonun ilk satırında yer alan değerleri yazın ya da kopyalayıp yapıştırın.
    
    |**Tür**|**Ana Bilgisayar**|**Değer**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |autodiscover  <br/> |autodiscover.outlook.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |Otomatik  <br/> |

     :::image type="content" source="../../media/f79c5679-34eb-4544-8517-caa2e8a4111a.png" alt-text="Tablodaki değerleri kopyalayıp yapıştırın.":::

1. Değişiklikleri Kaydet ( **onay** işareti) denetimine tıklayın. 

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Değişiklikleri Kaydet denetimine tıklayın.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa Microsoft için yeni bir SPF kaydı oluşturun. Bunun yerine, her iki değer kümesi de içeren tek *bir SPF*  kaydına sahip olmak için gerekli Microsoft değerlerini geçerli kayda ekleyin. 

1. Kullanmaya devam etmek için bu bağlantıyı kullanarak Namecheap'da etki alanları [sayfanıza gidin](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Oturum açma ve Devam'a girmeniz istenir.
    
1. Giriş sayfasındaki **Hesap'ın** altında, açılan **listeden** Etki Alanı Listesi'ne tıklayın. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Etki Alanı Listesi'ne tıklayın.":::

1. Etki **Alanı Listesi sayfasında** , düzenlemek istediğiniz etki alanını seçin ve sonra da Yönet'i **seçin**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Yönet'i seçin.":::

1. Gelişmiş **DNS'yi seçin**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Gelişmiş DNS'yi seçin.":::

1. ANA BILGISAYAR **KAYıTLARı bölümünde** Yeni KAYıT **EKLE'yi seçin**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Yenİ KAYıT EKLE'yi seçin.":::

1. Tür açılan **listesinde** **TXT Kaydı'ı seçin**.
    
    > [!NOTE]
    > YENI **KAYıT** EKLE'yi seçerek Tür açılan **liste otomatik olarak görüntülenir**. 

     :::image type="content" source="../../media/c5d1fddb-28b5-48ec-91c9-3e5d3955ac80.png" alt-text="TXT Kaydı'ni seçin.":::

1. Yeni kayıt kutularına, aşağıdaki tabloda yer alan aşağıdaki değerleri yazın veya kopyalayıp yapıştırın.
    
    (Açılan **listeden TTL** değerini seçin.) 
    
    |**Tür**|**Ana Bilgisayar**|**Değer**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Not:** Tüm boşlukların doğru kalması için bu girdiyi kopyalayıp yapıştırarak bu dosyayı yapıştırın. |30 dak.  <br/> |

     :::image type="content" source="../../media/ea0829f1-990b-424b-b26e-9859468318dd.png" alt-text="Tablodaki değerleri kopyalayıp yapıştırın.":::

1. Değişiklikleri Kaydet ( **onay** işareti) denetimine tıklayın. 

     :::image type="content" source="../../media/f2846c36-ace3-43d8-be5d-a65e2c267619.png" alt-text="Değişiklikleri Kaydet denetimine tıklayın.":::

## <a name="advanced-option-skype-for-business"></a>Gelişmiş seçenek: Skype Kurumsal

Yalnızca, bu seçeneği yalnızca, Skype Kurumsal yanı sıra sohbet, konferans aramaları ve görüntülü aramalar gibi çevrimiçi iletişim hizmetleri için Microsoft Teams. Skype için 4 kayıt gerekir: Oturum açma ve kullanıcıları hizmete bağlamak için 2 kullanıcı-kullanıcı iletişim için SRV kaydı ve 2 CNAME kaydı.

### <a name="add-the-two-required-srv-records"></a>Gerekli iki SRV kaydı ekleme

1. Kullanmaya devam etmek için bu bağlantıyı kullanarak Namecheap'da etki alanları [sayfanıza gidin](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Oturum açmanız istenir.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Namecheap'ta oturum açma.":::

1. Giriş sayfasındaki **Hesap'ın** altında, açılan **listeden** Etki Alanı Listesi'ne tıklayın. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Etki Alanı Listesi'ne tıklayın.":::

1. Etki **Alanı Listesi sayfasında** , düzenlemek istediğiniz etki alanını seçin ve sonra da Yönet'i **seçin**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Yönet'i seçin.":::

1. Gelişmiş **DNS'yi seçin**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Gelişmiş DNS'yi seçin.":::

1. ANA BILGISAYAR **KAYıTLARı bölümünde** Yeni KAYıT **EKLE'yi seçin**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Yenİ KAYıT EKLE'yi seçin.":::

1. Tür açılan **listesinde** **SRV Kaydı'yı seçin**.
    
    > [!NOTE]
    > YENI **KAYıT** EKLE'yi seçerek Tür açılan **liste otomatik olarak görüntülenir**. 

     :::image type="content" source="../../media/fd55cd7c-2243-4de1-8d39-2c3f7ea3ae51.png" alt-text="SRV Kaydı türünü seçin.":::

1. Yeni kayıtların boş kutularına, aşağıdaki tablonun ilk satırdaki değerleri yazın veya kopyalayıp yapıştırın.
    
    |**Hizmet**|**Protokol**|**Öncelik**|**Ağırlık**|**Bağlantı Noktası**|**Hedef**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip  <br/> |_tls  <br/> |100  <br/> |1  <br/> |443  <br/> |sipdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |Otomatik  <br/> |
    |_sipfederationtls  <br/> |_tcp  <br/> |100  <br/> |1  <br/> |5061  <br/> |sipfed.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |Otomatik  <br/> |
       
     :::image type="content" source="../../media/ff9566ea-0096-4b7f-873c-027080a23b56.png" alt-text="Tablodaki değerleri kopyalayıp yapıştırın.":::

1. Değişiklikleri Kaydet ( **onay** işareti) denetimine tıklayın. 

     :::image type="content" source="../../media/48a8dee4-c66d-449d-8759-9e9784c82b13.png" alt-text="Değişiklikleri Kaydet denetimine tıklayın.":::

1. Tablonun ikinci satırdan değerleri seçerek diğer SRV kaydını ekleyin.
    
> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydı ekleme 
  
1. ANA BILGISAYAR **KAYıTLARı bölümünde** Yeni KAYıT **EKLE'yi seçin**.
    
     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Yenİ AD EKLE'yi seçin.":::

1. Tür açılan **listesinde** **CNAME'yi seçin**.
    
    > [!NOTE]
    > YENI **KAYıT** EKLE'yi seçerek Tür açılan **liste otomatik olarak görüntülenir**. 

     :::image type="content" source="../../media/fd55cd7c-2243-4de1-8d39-2c3f7ea3ae51.png" alt-text="CNAME'yi seçin.":::

1. Yeni kayıtların boş kutularına, tablonun ilk satırdaki değerleri yazın veya kopyalayıp yapıştırın.
    
    |**Tür**|**Ana Bilgisayar**|**Değer**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |Otomatik  <br/> |
    |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |Otomatik  <br/> |

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Tablodaki CNAME değerlerini kopyalayıp yapıştırın.":::

1. Değişiklikleri Kaydet ( **onay** işareti) denetimine tıklayın. 

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Değişiklikleri Kaydet denetimine tıklayın.":::

1. Tablonun ikinci satırdan değerleri seçerek diğer CNAME kaydını ekleyin.
    
> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Gelişmiş seçenek: Mobil Cihazlar için Intune ve Mobil Microsoft 365

Bu hizmet, etki alanınıza bağlı mobil cihazların güvenliğini sağlamanıza ve uzaktan yönetmenize yardımcı olur. Mobil Cihaz Yönetimi'nin, kullanıcıların cihazları hizmete kaydedeni için iki CNAME kaydına ihtiyacı vardır.

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydı ekleme

1. Kullanmaya devam etmek için bu bağlantıyı kullanarak Namecheap'da etki alanları [sayfanıza gidin](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Oturum açmanız istenir.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Namecheap'ta oturum açma.":::

1. Giriş sayfasındaki **Hesap'ın** altında, açılan **listeden** Etki Alanı Listesi'ne tıklayın. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Etki Alanı Listesi'ne tıklayın.":::

1. Etki **Alanı Listesi sayfasında** , düzenlemek istediğiniz etki alanını seçin ve sonra da Yönet'i **seçin**.
    
     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Yönet'i seçin.":::

1. Gelişmiş **DNS'yi seçin**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Açılan listeden DNS Kayıtlarını Yönet'i seçin.":::

1. ANA BILGISAYAR **KAYıTLARı bölümünde** Yeni KAYıT **EKLE'yi seçin**.
    
     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Yenİ KAYıT EKLE'yi seçin.":::

1. Tür açılan **listesinde** **CNAME Kaydı'ı seçin**.
    
    > [!NOTE]
    > YENI **KAYıT** EKLE'yi seçerek Tür açılan **liste otomatik olarak görüntülenir**. 
  
     :::image type="content" source="../../media/0898f3b2-06ab-4364-a86a-a603a25b39f4.png" alt-text="CNAME Kaydı'ı seçin.":::

1. Yeni kayıtların boş kutularına, tablonun ilk satırdaki değerleri yazın veya kopyalayıp yapıştırın.
    
    |**Tür**|**Ana Bilgisayar**|**Değer**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |Otomatik  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |Otomatik  <br/> |
       
     :::image type="content" source="../../media/f79c5679-34eb-4544-8517-caa2e8a4111a.png" alt-text="Tablodaki değerleri kopyalayıp yapıştırın.":::

1. Değişiklikleri Kaydet **denetimine** tıklayın. 

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Değişiklikleri Kaydet denetimine tıklayın.":::

1. Tablonun ikinci satırdan değerleri seçerek diğer CNAME kaydını ekleyin.
    
> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 


