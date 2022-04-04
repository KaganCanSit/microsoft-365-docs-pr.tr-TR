---
title: Bağlan'de DNS web.com Microsoft 365
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
description: Microsoft için Microsoft'un Web Sitesinde etki alanlarınızı doğrulamayı ve e-posta, Skype Kurumsal Online ve diğer web.com ayarlamayı öğrenin.
ms.openlocfilehash: 612c22b518402fccaf9ced76b2506aa15c0e89f6
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568422"
---
# <a name="connect-your-dns-records-at-webcom-to-microsoft-365"></a>Bağlan'de DNS web.com Microsoft 365

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**.

DNS web.com sağlayıcınız dns barındırma sağlayıcınızsa, bu makaledeki adımları izleyin ve etki alanınızı doğrulayın ve e-posta, Skype Kurumsal Online, gibi DNS kayıtlarını ayarlayın.

Bir çalışma alanına bu web.com, etki alanınız diğerleriyle birlikte çalışacak şekilde Microsoft hizmetleri.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

## <a name="change-your-domains-nameserver-ns-records"></a>Etki alanınızın ad sunucusu (NS) kayıtlarını değiştirin

> [!IMPORTANT]
> Bu yordamı, etki alanınızı satın aldığınız ve kaydettirdiğiniz etki alanı kayıt şirketinde gerçekleştirmelisiniz.

Web.com için kayıt web.com, Kurulum işleminin web.com **eklediniz** .

Microsoft'ta etki alanınız için DNS kayıtlarını doğrulamak ve oluşturmak için, önce etki alanı kayıt şirketinizin ad sunucularını, ad sunucularını ve diğer ad sunucularını web.com gerekir.

Etki alanı kayıt şirketinizin web sitesinde etki alanınızın ad sunucularını kendiniz değiştirmek için şu adımları izleyin.

1. Etki alanı kayıt şirketinizin web sitesinde etki alanınızın ad sunucularını düzenleyebileceğiniz yeri bulun.

2. Aşağıdaki tabloda yer alan değerleri kullanarak iki ad sunucusu kaydı oluşturun veya var olan ad sunucusu kayıtlarını bu değerlerle eş olacak şekilde düzenleyin.

    |Tür|Değer|
    |---|---|
    |İlk ad sunucusu|Etki alanı tarafından sağlanan ad sunucusu web.com.|
    |İkinci ad sunucusu|Etki alanı tarafından sağlanan ad sunucusu web.com.|

    > [!TIP]
    > En az iki ad sunucu kaydı kullanabilirsiniz. Listelenen başka ad sunucuları varsa bunları silmeniz gerekir.

3. Değişikliklerinizi kaydedin.

> [!NOTE]
> Ad sunucusu kaydı güncelleştirmelerinizin İnternet DNS sistemi genelinde güncelleştirilmesi birkaç saat sürebilir. Ardından, Microsoft e-posta ve diğer hizmetlerinizin hepsi etki alanınız ile çalışacak şekilde ayarlanır.

## <a name="add-a-txt-record-for-verification"></a>Doğrulama için bir TXT kaydı ekleme

Etki alanınızı Microsoft ile kullanmadan önce bu etki alanına sahip olduğundan emin olarız. Etki alanı kayıt şirketinizin hesabında oturum açabilme ve DNS kaydı oluşturabilme özelliği, Microsoft'a etki alanının sahibi olduğunu kanıtlar.

> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. Dilerseniz bu kaydı daha sonra silebilirsiniz.

1. Kullanmaya başlamak için, bu bağlantıyı kullanarak web.com etki alanları [sayfanıza gidin](https://checkout.web.com/manage-it/index.jsp). İlk önce oturum aç'a.

1. Giriş sayfasında Etki Alanı **Adları'na tıklayın**.

1. **Eylemler'in** altında üç noktayı seçin ve **ardından açılan listeden** Yönet'i seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. Ekranı aşağı kaydırarak Gelişmiş **Araçlar'ı** seçin ve Gelişmiş **DNS Kayıtları'nın yanında YÖNET'i** **seçin**.

    Gelişmiş DNS Kayıtlarını Yönet **sayfasına devam** etmek için Devam'ı seçmeniz gerekir.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Gelişmiş DNS kayıtlarının yanında YÖNET'i seçin.":::

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında + KAYıT **EKLE'yi seçin**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="+ ADD RECORD öğesini seçin.":::

1. Tür **altında**, açılan listeden **TXT'yi** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="Tür açılan listesinden TXT'yi seçin.":::

1. Aşağıdaki tabloda yer alan değerleri seçin veya kopyalayıp yapıştırın.

    |Başvurular|TXT değeri|TTL|
    |---|---|:----|
    |@|MS=*msXXXXXXXX* <br/> **Not:** Bu bir örnektir. Tablodan **, belirli Hedef veya Adres Noktaları** değerinizi burada kullanın. [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)|1 Saat|

1. **EKLE'yi seçin**.

    Yeni TXT kaydınızı doğrulamadan önce, yeni oluşturduğunuz kaydın İnternet genelinde güncelleştirilsini için birkaç dakika bekleyin.

Kaydı etki alanı kayıt şirketinizin sitesinde eklediknize göre, Microsoft'a geri dönüp kayıt isteğinde bulundurabilirsiniz. Microsoft doğru TXT kaydını bulduğunda etki alanınız doğrulanır.

Bir dosyada kaydı Microsoft 365:

1. Yönetim merkezinde Etki Alanları'nın **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**gidin**</a>.

1. Etki Alanları sayfasında, doğrulamakta olduğunuz etki alanını seçin ve sonra da Kurulumu **başlat'ı seçin**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. **Devam'ı seçin**.

1. Etki alanını **doğrulama sayfasında** Doğrula'ya **tıklayın**.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Etki alanınıza gelen e-postanın Microsoft'a göndernsin için MX kaydı ekleme

1. Kullanmaya başlamak için, bu bağlantıyı kullanarak web.com etki alanları [sayfanıza gidin](https://checkout.web.com/manage-it/index.jsp). İlk önce oturum aç'a.

1. Giriş sayfasında Etki Alanı **Adları'na tıklayın**.

1. **Eylemler'in** altında üç noktayı seçin ve **ardından açılan listeden** Yönet'i seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. Ekranı aşağı kaydırarak Gelişmiş **Araçlar'ı** seçin ve Gelişmiş **DNS Kayıtları'nın yanında YÖNET'i** **seçin**.

    Gelişmiş DNS Kayıtlarını Yönet **sayfasına devam** etmek için Devam'ı seçmeniz gerekir.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Gelişmiş DNS kayıtlarının yanında YÖNET'i seçin.":::

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında + KAYıT **EKLE'yi seçin**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="+ ADD RECORD öğesini seçin.":::

1. Tür **altında**, **açılan listeden MX'i** seçin.

1. Aşağıdaki tabloda yer alan değerleri seçin veya kopyalayıp yapıştırın.

    |Başvuru|Posta sunucusu|Öncelik|TTL|
    |---|---|---|---|
    |@|*\<domain-key\>*.mail.protection.outlook.com <br/> **Not:** Microsoft yönetim *\<domain-key\>* merkezinden kendi sürümünizi edinin. [How do I find this?](../get-help-with-domains/information-for-dns-records.md)|For more information about priority, see [What is MX priority?](../setup/domains-faq.yml) <br/> 1|1 Saat|

1. **EKLE'yi seçin**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-mx-add.png" alt-text="EKLE'yi seçin.":::

1. Başka MX kayıtları varsa, düzenleme aracını seçerek bunların hepsini silin ve ardından her kayıt için **Sil'i** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-edit.png" alt-text="Düzenle'yi seçin.":::

## <a name="add-the-cname-record-required-for-microsoft"></a>Microsoft için gereken CNAME kaydını ekleme

1. Kullanmaya başlamak için, bu bağlantıyı kullanarak web.com etki alanları [sayfanıza gidin](https://checkout.web.com/manage-it/index.jsp). İlk önce oturum aç'a.

1. Giriş sayfasında Etki Alanı **Adları'na tıklayın**.

1. **Eylemler'in** altında üç noktayı seçin ve **ardından açılan listeden** Yönet'i seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. Ekranı aşağı kaydırarak Gelişmiş **Araçlar'ı** seçin ve Gelişmiş **DNS Kayıtları'nın yanında YÖNET'i** **seçin**.

    Gelişmiş DNS Kayıtlarını Yönet **sayfasına devam** etmek için Devam'ı seçmeniz gerekir.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Gelişmiş DNS kayıtlarının yanında YÖNET'i seçin.":::

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında + KAYıT **EKLE'yi seçin**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="+ ADD RECORD öğesini seçin.":::

1. Tür **altında**, açılan **listeden CNAME'yi** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Tür açılan listesinden CNAME'yi seçin.":::

1. Aşağıdaki tabloda yer alan değerleri seçin veya kopyalayıp yapıştırın.

    |Başvuru|Ana bilgisayar adı|Diğer Ad|TTL|
    |---|---|---|---|
    |Diğer Ana Bilgisayar|autodiscover|autodiscover.outlook.com|1 Saat|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="CNAME değerlerini yazın veya kopyalayıp pencereye yapıştırın.":::

1. **EKLE'yi seçin**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa Microsoft için yeni bir SPF kaydı oluşturun. Bunun yerine, her iki değer kümesi de içeren tek *bir SPF* kaydına sahip olmak için gerekli Microsoft değerlerini geçerli kayda ekleyin.

1. Kullanmaya başlamak için, bu bağlantıyı kullanarak web.com etki alanları [sayfanıza gidin](https://checkout.web.com/manage-it/index.jsp). İlk önce oturum aç'a.

1. Giriş sayfasında Etki Alanı **Adları'na tıklayın**.

1. **Eylemler'in** altında üç noktayı seçin ve **ardından açılan listeden** Yönet'i seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. Ekranı aşağı kaydırarak Gelişmiş **Araçlar'ı** seçin ve Gelişmiş **DNS Kayıtları'nın yanında YÖNET'i** **seçin**.

    Gelişmiş DNS Kayıtlarını Yönet **sayfasına devam** etmek için Devam'ı seçmeniz gerekir.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Gelişmiş DNS kayıtlarının yanında YÖNET'i seçin.":::

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında + KAYıT **EKLE'yi seçin**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="+ ADD RECORD öğesini seçin.":::

1. Tür **altında**, açılan listeden **TXT'yi** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="Tür açılan listesinden TXT'yi seçin.":::

1. Aşağıdaki tabloda yer alan değerleri seçin veya kopyalayıp yapıştırın.

    |Başvuru|TXT değeri|TTL|
    |---|---|---|
    |@|v=spf1 include:spf.protection.outlook.com -all <br/> **Not:** Tüm boşlukların doğru kalması için bu girdiyi kopyalayıp yapıştırarak bu dosyayı yapıştırın.|1 Saat|

1. **EKLE'yi seçin**.

## <a name="advanced-option-skype-for-business"></a>Gelişmiş seçenek: Skype Kurumsal

Yalnızca, bu seçeneği yalnızca, Skype Kurumsal yanı sıra sohbet, konferans aramaları ve görüntülü aramalar gibi çevrimiçi iletişim hizmetleri için Microsoft Teams. Skype için 4 kayıt gerekir: Oturum açma ve kullanıcıları hizmete bağlamak için 2 kullanıcı-kullanıcı iletişim için SRV kaydı ve 2 CNAME kaydı.

### <a name="add-the-two-required-srv-records"></a>Gerekli iki SRV kaydı ekleme

1. Kullanmaya başlamak için, bu bağlantıyı kullanarak web.com etki alanları [sayfanıza gidin](https://checkout.web.com/manage-it/index.jsp). İlk önce oturum aç'a.

1. Giriş sayfasında Etki Alanı **Adları'na tıklayın**.

1. **Eylemler'in** altında üç noktayı seçin ve **ardından açılan listeden** Yönet'i seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. Ekranı aşağı kaydırarak Gelişmiş **Araçlar'ı** seçin ve Gelişmiş **DNS Kayıtları'nın yanında YÖNET'i** **seçin**.

    Gelişmiş DNS Kayıtlarını Yönet **sayfasına devam** etmek için Devam'ı seçmeniz gerekir.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Gelişmiş DNS kayıtlarının yanında YÖNET'i seçin.":::

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında + KAYıT **EKLE'yi seçin**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="+ ADD RECORD öğesini seçin.":::

1. Tür **altında**, açılan **listeden SRV'yi** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv.png" alt-text="Tür açılan listesinden SRV'yi seçin.":::

1. Aşağıdaki tabloda yer alan değerleri seçin veya kopyalayıp yapıştırın.

    |Tür|Hizmet|Protokol|Ağırlık|Bağlantı noktası|Hedef|Öncelik|TTL|
    |---|---|---|---|---|---|---|---|
    |SRV|_sip|TLS|100|443|sipdir.online.lync.com <br/> **Bu değer nokta (.) ile sona ERER.**|1|1 Saat|
    |SRV|_sipfederationtls|TCP|100|5061|sipfed.online.lync.com <br/> **Bu değer nokta (.) ile sona ERER.**|1|1 Saat|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv-add.png" alt-text="Tablodaki değerleri yazın veya kopyalayıp SRV kayıt penceresine yapıştırın.":::

1. **EKLE'yi seçin**.

1. Tablonun ikinci satırına değerleri kopyalayıp diğer SRV kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlar ile ilgili sorunlar için bkz. Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra [sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydı ekleme

1. Kullanmaya başlamak için, bu bağlantıyı kullanarak web.com etki alanları [sayfanıza gidin](https://checkout.web.com/manage-it/index.jsp). İlk önce oturum aç'a.

1. Giriş sayfasında Etki Alanı **Adları'na tıklayın**.

1. **Eylemler'in** altında üç noktayı seçin ve **ardından açılan listeden** Yönet'i seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. Ekranı aşağı kaydırarak Gelişmiş **Araçlar'ı** seçin ve Gelişmiş **DNS Kayıtları'nın yanında YÖNET'i** **seçin**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Gelişmiş DNS kayıtlarının yanında YÖNET'i seçin.":::

    Gelişmiş DNS Kayıtlarını Yönet **sayfasına devam** etmek için Devam'ı seçmeniz gerekir.

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında + KAYıT **EKLE'yi seçin**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="+ ADD RECORD öğesini seçin.":::

1. Tür **altında**, açılan **listeden CNAME'yi** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Tür açılan listesinden CNAME'yi seçin.":::

1. Aşağıdaki tabloda yer alan değerleri seçin veya kopyalayıp yapıştırın.

    |Tür|Başvuru|Ana Bilgisayar Adı|Diğer Ad|TTL|
    |---|---|---|---|---|
    |CNAME|Diğer Ana Bilgisayar|sip|sipdir.online.lync.com <br/> **Bu değer nokta (.) ile sona ERER.**|1 Saat|
    |CNAME|Diğer Ana Bilgisayar|lyncdiscover|webdir.online.lync.com <br/> **Bu değer nokta (.) ile sona ERER.**|1 Saat|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="CNAME değerlerini yazın veya kopyalayıp pencereye yapıştırın.":::

1. **EKLE'yi seçin**.

1. Tablonun ikinci satırına değerleri kopyalayıp diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Gelişmiş seçenek: Intune için Mobil Cihaz Yönetimi ve mobil Microsoft 365

Bu hizmet, etki alanınıza bağlı mobil cihazların güvenliğini sağlamanıza ve uzaktan yönetmenize yardımcı olur. Mobil Cihaz Yönetimi, kullanıcıların cihazları hizmete kaydedeni için 2 CNAME kaydına ihtiyaç vardır.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Mobil Cihazlar için gerekli iki CNAME Cihaz Yönetimi

1. Kullanmaya başlamak için, bu bağlantıyı kullanarak web.com etki alanları [sayfanıza gidin](https://checkout.web.com/manage-it/index.jsp). İlk önce oturum aç'a.

1. Giriş sayfasında Etki Alanı **Adları'na tıklayın**.

1. **Eylemler'in** altında üç noktayı seçin ve **ardından açılan listeden** Yönet'i seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. Ekranı aşağı kaydırarak Gelişmiş **Araçlar'ı** seçin ve Gelişmiş **DNS Kayıtları'nın yanında YÖNET'i** **seçin**.

    Gelişmiş DNS Kayıtlarını Yönet **sayfasına devam** etmek için Devam'ı seçmeniz gerekir.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Gelişmiş DNS kayıtlarının yanında YÖNET'i seçin.":::

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında + KAYıT **EKLE'yi seçin**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="+ ADD RECORD öğesini seçin.":::

1. Tür **altında**, açılan **listeden CNAME'yi** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Tür açılan listesinden CNAME'yi seçin.":::

1. Aşağıdaki tabloda yer alan değerleri seçin veya kopyalayıp yapıştırın.

    |Tür|Başvuru|Ana Bilgisayar Adı|Diğer Ad|TTL|
    |---|---|---|---|---|
    |CNAME|Diğer Ana Bilgisayar|enterpriseregistration|enterpriseregistration.windows.net <br/> **Bu değer nokta (.) ile sona ERER.**|1 Saat|
    |CNAME|Diğer Ana Bilgisayar|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com <br/> **Bu değer nokta (.) ile sona ERER.**|1 Saat|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Tablodaki CNAME değerlerini yazın veya kopyalayıp pencereye yapıştırın.":::

1. **EKLE'yi seçin**.

1. Tablonun ikinci satırına değerleri kopyalayıp diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.
