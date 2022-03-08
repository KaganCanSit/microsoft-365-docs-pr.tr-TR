---
title: Bağlan için Network Solutions'da DNS kayıtlarınızı Microsoft 365
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
ms.assetid: 1dc55f9f-5309-450f-acc3-b2b4119c8be3
description: Microsoft için Network Solutions'da etki alanlarınızı doğrulamayı ve e-posta, Skype Kurumsal Online ve diğer hizmetler için DNS kayıtlarını ayarlamayı öğrenin.
ms.openlocfilehash: a15b6ec2f06b08a32c0cf03bbc030731b91ea925
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313531"
---
# <a name="connect-your-dns-records-at-network-solutions-to-microsoft-365"></a>Bağlan için Network Solutions'da DNS kayıtlarınızı Microsoft 365

 **Aradığınızı bulamazsanız, [Etki Alanları SSS sayfasını denetleyin](../setup/domains-faq.yml)**. 
  
DNS barındırma sağlayıcınız Network Solutions ise, bu makalede verilen adımları izleyerek etki alanınızı doğrulayın ve e-posta, Skype Kurumsal Çevrimiçi, vb. için DNS kayıtlarını ayarlayın.

Network Solutions'da bu kayıtları eklemenizden sonra, etki alanınız etki alanınız otomatik olarak Microsoft hizmetleri.
  
> [!NOTE]
>  Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 
  
## <a name="add-a-txt-record-for-verification"></a>Doğrulama için bir TXT kaydı ekleme

Etki alanınızı Microsoft ile kullanmadan önce bu etki alanına sahip olduğundan emin olarız. Etki alanı kayıt şirketinizin hesabında oturum açabilme ve DNS kaydı oluşturabilme özelliği, Microsoft'a etki alanının sahibi olduğunu kanıtlar.
  
> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. Dilerseniz bu kaydı daha sonra silebilirsiniz. 
  
1. Başlamak için, [bu bağlantıyı](https://www.networksolutions.com/manage-it) kullanarak Network Solutions'daki etki alanları sayfanıza gidin. Oturum açmanız istenir.
  
1. Giriş sayfasında Etki Alanı **Adları'na tıklayın**.

1. Değiştirmek istediğiniz etki alanının yanındaki onay kutusunu seçin.
  
1. **Eylemler'in** altında üç noktayı seçin ve sonra **da açılan listeden** Yönet'i seçin.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::
  
1. Ekranı aşağı kaydırarak Gelişmiş **Araçlar'ı** seçin ve Gelişmiş **DNS Kayıtları'nın yanında YÖNET'i** **seçin**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Gelişmiş DNS kayıtlarının yanında YÖNET'i seçin.":::

    Gelişmiş DNS Kayıtlarını Yönet **sayfasına devam** etmek için Devam'ı seçmeniz gerekir.
  
1. Gelişmiş DNS Kayıtlarını Yönet sayfasında +ADD **RECORD öğesini seçin**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="+ADD RECORD öğesini seçin.":::

1. Tür **altında**, açılan listeden **TXT'yi** seçin.
  
1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.
    
    | Başvuru | TXT Değeri | TTL |
    |:-----|:-----|:-----|
    |@  <br/> (Kaydı kaydettiğinizde, sistem bu değeri **@ (None)** olarak değiştirir.)  |MS=ms *XXXXXXXX*  <br/> **Not:** Bu bir örnektir. Tablodan **, belirli Hedef veya Adres Noktaları** değerinizi burada kullanın.  [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md) |3600  <br/>    | 

1. **EKLE'yi seçin**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add.png" alt-text="EKLE'yi seçin.":::

    > [!NOTE]
    > Oluşturduğunuz TXT **kaydını** görüntülemek için sağ üst kısımda Klasik Görünüm'i seçin.   
  
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
  
1. Başlamak için, [bu bağlantıyı](https://www.networksolutions.com/manage-it) kullanarak Network Solutions'daki etki alanları sayfanıza gidin. Oturum açmanız istenir.
  
1. Giriş sayfasında Etki Alanı **Adları'na tıklayın**.

1. Değiştirmek istediğiniz etki alanının yanındaki onay kutusunu seçin.
  
1. **Eylemler'in** altında üç noktayı seçin ve **ardından açılan listeden** Yönet'i seçin.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::
  
1. Ekranı aşağı kaydırarak Gelişmiş **Araçlar'ı** seçin ve Gelişmiş **DNS Kayıtları'nın yanında YÖNET'i** **seçin**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Gelişmiş DNS kayıtlarının yanında YÖNET'i seçin.":::

    Gelişmiş DNS Kayıtlarını Yönet **sayfasına devam** etmek için Devam'ı seçmeniz gerekir.

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında +ADD **RECORD öğesini seçin**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="+ADD RECORD öğesini seçin.":::

1. Tür **altında**, **açılan listeden MX'i** seçin.
  


1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.
    
    | Başvuru | Posta sunucusu | Öncelik | TTL |
    |:-----|:-----|:-----|:-----|
    | @ | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Bu değer nokta (.) ile sona ERER.** <br/> **Not:** Microsoft hesabınızla  *\<domain-key\>*  oturum açın. [How do I find this?](../get-help-with-domains/information-for-dns-records.md) | 0  <br/> Öncelik hakkında daha fazla bilgi için bkz. [MX önceliği nedir?](../setup/domains-faq.yml) | 1 Saat  |  
  
1. **EKLE'yi seçin**.
  
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-MX-add.png" alt-text="EKLE'yi seçin.":::

    > [!NOTE]
    > Oluşturduğunuz TXT **kaydını** görüntülemek için sağ üst kısımda Klasik Görünüm'i seçin.  

1. Başka MX kayıtları varsa, düzenleme aracını seçerek bunların hepsini silin ve ardından her kayıt için **Sil'i** seçin.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-edit.png" alt-text="Düzenle aracını seçin.":::
  
## <a name="add-the-cname-record-required-for-microsoft"></a>Microsoft için gereken CNAME kaydını ekleme

1. Başlamak için, [bu bağlantıyı](https://www.networksolutions.com/manage-it) kullanarak Network Solutions'daki etki alanları sayfanıza gidin. Oturum açmanız istenir.
  
1. Giriş sayfasında Etki Alanı **Adları'na tıklayın**.

1. Değiştirmek istediğiniz etki alanının yanındaki onay kutusunu seçin.
  
1. **Eylemler'in** altında üç noktayı seçin ve **ardından açılan listeden** Yönet'i seçin.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::
  
1. Gelişmiş **Araçlar'ı** seçin ve Gelişmiş **DNS Kayıtları'nın yanında YÖNET'i** **seçin**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Gelişmiş DNS kayıtlarının yanında YÖNET'i seçin.":::

    Gelişmiş DNS Kayıtlarını Yönet **sayfasına devam** etmek için Devam'ı seçmeniz gerekir.

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında +ADD **RECORD öğesini seçin**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="+ADD RECORD öğesini seçin.":::

1. Tür **altında**, açılan **listeden CNAME'yi** seçin.
 
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname.png" alt-text="Açılan listeden CNAME türü öğesini seçin.":::
 
1. CNAME kaydı kutularına, aşağıdaki tabloda yer alan değerleri yazın veya kopyalayıp yapıştırın.
    
    | Başvuru | Ana Bilgisayar Adı | Diğer Ad | TTL |
    |:-----|:-----|:-----|:-----|
    |Diğer Ana Bilgisayar| autodiscover  | autodiscover.outlook.com **Bu değer noktayla (.)** <br/> 1 Saat  |

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname-values.png" alt-text="Tablodaki CNAME değerlerini yazın veya kopyalayıp pencereye yapıştırın.":::
  
1. **EKLE'yi seçin**.

    > [!NOTE]
    > Oluşturduğunuz **kaydı görüntülemek** için sağ üst kısımda Klasik Görünüm'e tıklayın.  
  
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa Microsoft için yeni bir SPF kaydı oluşturun. Bunun yerine, her iki değer kümesi de içeren tek  *bir SPF*  kaydına sahip olmak için gerekli Microsoft değerlerini geçerli kayda ekleyin. 
  
1. Başlamak için, [bu bağlantıyı](https://www.networksolutions.com/manage-it) kullanarak Network Solutions'daki etki alanları sayfanıza gidin. Oturum açmanız istenir.
  
1. Giriş sayfasında Etki Alanı **Adları'na tıklayın**.

1. Değiştirmek istediğiniz etki alanının yanındaki onay kutusunu seçin.

1. **Eylemler'in** altında üç noktayı seçin ve **ardından açılan listeden** Yönet'i seçin.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. Gelişmiş **Araçlar'ı** seçin ve Gelişmiş **DNS Kayıtları'nın yanında YÖNET'i** **seçin**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Gelişmiş DNS kayıtlarının yanında YÖNET'i seçin.":::

    Gelişmiş DNS Kayıtlarını Yönet **sayfasına devam** etmek için Devam'ı seçmeniz gerekir.

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında +ADD **RECORD öğesini seçin**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="+ADD RECORD öğesini seçin.":::

1. Tür **altında**, açılan listeden **TXT'yi** seçin.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-TXT.png" alt-text="Tür açılan listesinden TXT'yi seçin.":::

1. In the boxes for the new record, type or copy and paste the following values.
    
    | Başvuru | TXT Değeri | TTL
    |:-----|:-----|:-----|
    |@  <br/> (Kaydı kaydettiğinizde, sistem bu değeri **@ (None)** olarak değiştirir.)  |v=spf1 include:spf.protection.outlook.com -all  <br/> **Not:** Tüm boşlukların doğru kalması için bu girdiyi kopyalayıp yapıştırarak bu dosyayı yapıştırın. | 1 Saat  |
       
1. **EKLE'yi seçin**.
  
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add.png" alt-text="EKLE'yi seçin.":::

    > [!NOTE]
    > Oluşturduğunuz **kaydı görüntülemek** için sağ üst kısımda Klasik Görünüm'e tıklayın.  
  
## <a name="advanced-option-skype-for-business"></a>Gelişmiş seçenek: Skype Kurumsal

Yalnızca, bu seçeneği yalnızca, Skype Kurumsal yanı sıra sohbet, konferans aramaları ve görüntülü aramalar gibi çevrimiçi iletişim hizmetleri için Microsoft Teams. Skype için 4 kayıt gerekir: Oturum açma ve kullanıcıları hizmete bağlamak için 2 kullanıcı-kullanıcı iletişim için SRV kaydı ve 2 CNAME kaydı.

### <a name="add-the-two-required-srv-records"></a>Gerekli iki SRV kaydı ekleme

1. Başlamak için, [bu bağlantıyı](https://www.networksolutions.com/manage-it) kullanarak Network Solutions'daki etki alanları sayfanıza gidin. Oturum açmanız istenir.
  
1. Giriş sayfasında Etki Alanı **Adları'na tıklayın**.

1. Değiştirmek istediğiniz etki alanının yanındaki onay kutusunu seçin.

1. **Eylemler'in** altında üç noktayı seçin ve **ardından açılan listeden** Yönet'i seçin.
  
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. Gelişmiş **Araçlar'ı** seçin ve Gelişmiş **DNS Kayıtları'nın yanında YÖNET'i** **seçin**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Gelişmiş DNS kayıtlarının yanında YÖNET'i seçin.":::

    Gelişmiş DNS Kayıtlarını Yönet **sayfasına devam** etmek için Devam'ı seçmeniz gerekir.

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında +ADD **RECORD öğesini seçin**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="+ADD RECORD öğesini seçin.":::

1. Tür **altında**, açılan **listeden SRV'yi** seçin.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-srv.png" alt-text="Tür açılan listesinden SRV'yi seçin.":::

1. İki yeni kaydın kutularına, aşağıdaki tablodaki değerleri yazın veya kopyalayıp yapıştırın.

    (Açılan listelerden **Hizmet** ve **Protokol** değerlerini seçin.) 
    
    | Tür | Hizmet | Protokol | Ağırlık | Bağlantı noktası | Hedef | Öncelik | TTL |
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    | SRV |_sip  |TLS  |100  |443  |sipdir.online.lync.com  <br/> **Bu değer nokta (.) ile sona ERER.** | 1  | 1 Saat  |
    | SRV |_sipfederationtls  |TCP  |100  |5061  |sipfed.online.lync.com  <br/> **Bu değer nokta (.) ile sona ERER.** |1  | 1 Saat  |
  
1. **EKLE'yi seçin**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-srv-add.png" alt-text="EKLE'yi seçin.":::

    > [!NOTE]
    > Oluşturduğunuz **kaydı görüntülemek** için sağ üst kısımda Klasik Görünüm'e tıklayın.  

1. Tablonun ikinci satırına değerleri kopyalayıp diğer SRV kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlar ile ilgili sorunlar için bkz. Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra [sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydı ekleme

1. Başlamak için, [bu bağlantıyı](https://www.networksolutions.com/manage-it) kullanarak Network Solutions'daki etki alanları sayfanıza gidin. Oturum açmanız istenir.
  
1. Giriş sayfasında Etki Alanı **Adları'na tıklayın**.

1. Değiştirmek istediğiniz etki alanının yanındaki onay kutusunu seçin.

1. **Eylemler'in** altında üç noktayı seçin ve **ardından açılan listeden** Yönet'i seçin.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. Gelişmiş **Araçlar'ı** seçin ve Gelişmiş **DNS Kayıtları'nın yanında YÖNET'i** **seçin**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Gelişmiş DNS kayıtlarının yanında YÖNET'i seçin.":::

    Gelişmiş DNS Kayıtlarını Yönet **sayfasına devam** etmek için Devam'ı seçmeniz gerekir.

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında + KAYıT **EKLE'yi seçin**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="+ADD RECORD öğesini seçin.":::

1. Tür **altında**, açılan **listeden CNAME'yi** seçin.
 
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname.png" alt-text="Açılan listeden CNAME türü öğesini seçin.":::
 
1. CNAME kaydı kutularına, aşağıdaki tabloda yer alan değerleri yazın veya kopyalayıp yapıştırın.

    | Tür | Başvuru | Ana Bilgisayar Adı | Diğer Ad | TTL |
    |:-----|:-----|:-----|:-----|:-----|
    | CNAME | Diğer Ana Bilgisayar | sip  <br/> |sipdir.online.lync.com  <br/> **Bu değer nokta (.) ile sona ERER.** |1 Saat |
    | CNAME| Diğer Ana Bilgisayar | lyncdiscover  <br/> |webdir.online.lync.com  <br/> **Bu değer nokta (.) ile sona ERER.** | 1 Saat |

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname-values.png" alt-text="Tablodaki CNAME değerlerini yazın veya kopyalayıp pencereye yapıştırın.":::

1. **EKLE'yi seçin**.

    > [!NOTE]
    > Oluşturduğunuz **kaydı görüntülemek** için sağ üst kısımda Klasik Görünüm'e tıklayın.  

1. Tablonun ikinci satırına değerleri kopyalayıp diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Gelişmiş seçenek: Mobil Cihazlar için Intune ve Mobil Microsoft 365

Bu hizmet, etki alanınıza bağlı mobil cihazların güvenliğini sağlamanıza ve uzaktan yönetmenize yardımcı olur. Mobil Cihaz Yönetimi'nin, kullanıcıların cihazları hizmete kaydedeni için 2 CNAME kaydı olması gerekir.

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydı ekleme

1. Başlamak için, [bu bağlantıyı](https://www.networksolutions.com/manage-it) kullanarak Network Solutions'daki etki alanları sayfanıza gidin. Oturum açmanız istenir.
  
1. Giriş sayfasında Etki Alanı **Adları'na tıklayın**.

1. Değiştirmek istediğiniz etki alanının yanındaki onay kutusunu seçin.

1. **Eylemler'in** altında üç noktayı seçin ve **ardından açılan listeden** Yönet'i seçin.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. Gelişmiş **Araçlar'ı** seçin ve Gelişmiş **DNS Kayıtları'nın yanında YÖNET'i** **seçin**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Gelişmiş DNS kayıtlarının yanında YÖNET'i seçin.":::

    Gelişmiş DNS Kayıtlarını Yönet **sayfasına devam** etmek için Devam'ı seçmeniz gerekir.

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında +ADD **RECORD öğesini seçin**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="+ADD RECORD öğesini seçin.":::
  
1. Tür **altında**, açılan **listeden CNAME'yi** seçin.
 
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname.png" alt-text="Açılan listeden CNAME türü öğesini seçin.":::
 
1. CNAME kaydı kutularına, aşağıdaki tabloda yer alan değerleri yazın veya kopyalayıp yapıştırın.

    | Tür | Başvuru | Ana Bilgisayar Adı | Diğer Ad | TTL |
    |:-----|:-----|:-----|:-----|:-----|
    | CNAME | Diğer Ana Bilgisayar | enterpriseregistration |enterpriseregistration.windows.net  <br/> **Bu değer nokta (.) ile sona ERER.** | 1 Saat |
    | CNAME | Diğer Ana Bilgisayar |enterpriseenrollment |enterpriseenrollment-s.manage.microsoft.com  <br/> **Bu değer nokta (.) ile sona ERER.** | 1 Saat |

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname-values.png" alt-text="Tablodaki CNAME değerlerini yazın veya kopyalayıp pencereye yapıştırın.":::

1. **EKLE'yi seçin**.

    > [!NOTE]
    > Oluşturduğunuz **kaydı görüntülemek** için sağ üst kısımda Klasik Görünüm'e tıklayın.  

1. Tablonun ikinci satırına değerleri kopyalayıp diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

