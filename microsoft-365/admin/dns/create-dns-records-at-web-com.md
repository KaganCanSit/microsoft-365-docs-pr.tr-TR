---
title: dns kayıtlarınızı web.com Microsoft 365 Bağlan
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
description: Microsoft için web.com'da etki alanınızı doğrulamayı ve e-posta, Skype for Business Online ve diğer hizmetler için DNS kayıtlarını ayarlamayı öğrenin.
ms.openlocfilehash: 621364bdc0b2e9a2868084f0cb0b8eb8ef61c5b0
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780323"
---
# <a name="connect-your-dns-records-at-webcom-to-microsoft-365"></a>dns kayıtlarınızı web.com Microsoft 365 Bağlan

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**.

DNS barındırma sağlayıcınız web.com ise, etki alanınızı doğrulamak ve e-posta, Skype for Business Çevrimiçi vb. için DNS kayıtlarını ayarlamak için bu makaledeki adımları izleyin.

Bu kayıtları web.com ekledikten sonra, etki alanınız Microsoft hizmetleri ile çalışacak şekilde ayarlanır.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

## <a name="change-your-domains-nameserver-ns-records"></a>Etki alanınızın ad sunucusu (NS) kayıtlarını değiştirin

> [!IMPORTANT]
> Bu yordamı, etki alanınızı satın aldığınız ve kaydettirdiğiniz etki alanı kayıt şirketinde gerçekleştirmelisiniz.

web.com kaydolduğunda, web.com **Kurulumu** işlemini kullanarak bir etki alanı eklediniz.

Microsoft'ta etki alanınız için DNS kayıtlarını doğrulamak ve oluşturmak için, önce etki alanı kayıt şirketinizdeki ad sunucularını web.com ad sunucularını kullanacak şekilde değiştirmeniz gerekir.

Etki alanı kayıt şirketinizin web sitesinde etki alanınızın ad sunucularını kendiniz değiştirmek için şu adımları izleyin.

1. Etki alanı kayıt şirketinizin web sitesinde etki alanınızın ad sunucularını düzenleyebileceğiniz yeri bulun.

2. Aşağıdaki tablodaki değerleri kullanarak iki ad sunucusu kaydı oluşturun veya mevcut ad sunucusu kayıtlarını bu değerlerle eşleşsin diye düzenleyin.

    |Tür|Değer|
    |---|---|
    |İlk ad sunucusu|web.com tarafından sağlanan ad sunucusu değerini kullanın.|
    |İkinci ad sunucusu|web.com tarafından sağlanan ad sunucusu değerini kullanın.|

    > [!TIP]
    > En az iki ad sunucusu kaydı kullanmalısınız. Listelenen başka ad sunucuları varsa, bunları silmeniz gerekir.

3. Değişikliklerinizi kaydedin.

> [!NOTE]
> Ad sunucusu kaydı güncelleştirmelerinizin İnternet DNS sistemi genelinde güncelleştirilmesi birkaç saat sürebilir. Ardından Microsoft e-postanız ve diğer hizmetlerin tümü etki alanınızla çalışacak şekilde ayarlanır.

## <a name="add-a-txt-record-for-verification"></a>Doğrulama için bir TXT kaydı ekleme

Etki alanınızı Microsoft ile kullanmadan önce, etki alanına sahip olduğunuzdan emin olmamız gerekir. Etki alanı kayıt şirketinizde hesabınızda oturum açıp DNS kaydını oluşturabilmek, Microsoft'a etki alanının sahibi olduğunuzu kanıtlar.

> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. Dilerseniz bu kaydı daha sonra silebilirsiniz.

1. Başlamak için [bu bağlantıyı](https://checkout.web.com/manage-it/index.jsp) kullanarak web.com'deki etki alanları sayfanıza gidin. Önce oturum açın.

1. Giriş sayfasında **Etki Alanı Adları'nı** seçin.

1. **Eylemler'in** altında üç noktayı seçin ve ardından açılan listede **Yönet'i** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. **Gelişmiş Araçlar'ı** seçmek için ekranı aşağı kaydırın ve **Gelişmiş DNS Kayıtları'nın** yanında **YÖNET'i** seçin.

    Gelişmiş DNS Kayıtlarını Yönet sayfasına ulaşmak için **Devam'ı** seçmeniz gerekebilir.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Gelişmiş DNS kayıtları'nın yanında YÖNET'i seçin.":::

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında **+ KAYıT EKLE'yi** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="+ KAYıT EKLE'yi seçin.":::

1. **Tür** altında, açılan listeden **TXT'yi** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="Tür açılan listesinde TXT'yi seçin.":::

1. Aşağıdaki tabloda yer alan değerleri seçin veya kopyalayıp yapıştırın.

    |Anlamına gelir|TXT değeri|TTL|
    |---|---|:----|
    |@|MS=*msXXXXXXXXX* <br/> **Not:** Bu bir örnektir. Burada, tablodan belirli **Hedef veya İşaret Edilen Adres** değerinizi kullanın. [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)|1 Saat|

1. **EKLE'yi** seçin.

    Yeni TXT kaydınızı doğrulamadan önce birkaç dakika bekleyin; böylece yeni oluşturduğunuz kayıt İnternet üzerinden güncelleştirilebilir.

Artık kaydı etki alanı kayıt şirketinizin sitesine eklediğinize göre, Microsoft'a geri dönüp kaydı istemeniz gerekir. Microsoft doğru TXT kaydını bulduğunda etki alanınız doğrulanır.

Microsoft 365 kaydı doğrulamak için:

1. Yönetim merkezinde **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Etki Alanları'na**</a> gidin.

1. Etki Alanları sayfasında, doğrulamakta olduğunuz etki alanını seçin ve **kurulumu başlat'ı** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. **Devam'ı** seçin.

1. **Etki alanını doğrula** sayfasında **Doğrula'yı** seçin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Etki alanınız için e-postanın Microsoft'a gelmesi için bir MX kaydı ekleyin

1. Başlamak için [bu bağlantıyı](https://checkout.web.com/manage-it/index.jsp) kullanarak web.com'deki etki alanları sayfanıza gidin. Önce oturum açın.

1. Giriş sayfasında **Etki Alanı Adları'nı** seçin.

1. **Eylemler'in** altında üç noktayı seçin ve ardından açılan listede **Yönet'i** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. **Gelişmiş Araçlar'ı** seçmek için ekranı aşağı kaydırın ve **Gelişmiş DNS Kayıtları'nın** yanında **YÖNET'i** seçin.

    Gelişmiş DNS Kayıtlarını Yönet sayfasına ulaşmak için **Devam'ı** seçmeniz gerekebilir.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Gelişmiş DNS kayıtları'nın yanında YÖNET'i seçin.":::

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında **+ KAYıT EKLE'yi** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="+ KAYıT EKLE'yi seçin.":::

1. **Tür** altında, açılan listeden **MX'i** seçin.

1. Aşağıdaki tabloda yer alan değerleri seçin veya kopyalayıp yapıştırın.

    |Başvuruda bulunan|Posta sunucusu|Öncelik|TTL|
    |---|---|---|---|
    |@|*\<domain-key\>*.mail.protection.outlook.com <br/> **Not:** Microsoft yönetim merkezinden alın *\<domain-key\>* . [How do I find this?](../get-help-with-domains/information-for-dns-records.md)|For more information about priority, see [What is MX priority?](../setup/domains-faq.yml) <br/> 1|1 Saat|

1. **EKLE'yi** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-mx-add.png" alt-text="EKLE'yi seçin.":::

1. Başka MX kayıtları varsa, düzenleme aracını seçip her kayıt için **Sil'i** seçerek bunların tümünü silin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-edit.png" alt-text="Düzenle'yi seçin.":::

## <a name="add-the-cname-record-required-for-microsoft"></a>Microsoft için gereken CNAME kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://checkout.web.com/manage-it/index.jsp) kullanarak web.com'deki etki alanları sayfanıza gidin. Önce oturum açın.

1. Giriş sayfasında **Etki Alanı Adları'nı** seçin.

1. **Eylemler'in** altında üç noktayı seçin ve ardından açılan listede **Yönet'i** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. **Gelişmiş Araçlar'ı** seçmek için ekranı aşağı kaydırın ve **Gelişmiş DNS Kayıtları'nın** yanında **YÖNET'i** seçin.

    Gelişmiş DNS Kayıtlarını Yönet sayfasına ulaşmak için **Devam'ı** seçmeniz gerekebilir.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Gelişmiş DNS kayıtları'nın yanında YÖNET'i seçin.":::

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında **+ KAYıT EKLE'yi** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="+ KAYıT EKLE'yi seçin.":::

1. **Tür** altında, açılan listeden **CNAME'i** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Tür açılan listesindeN CNAME'yi seçin.":::

1. Aşağıdaki tabloda yer alan değerleri seçin veya kopyalayıp yapıştırın.

    |Başvuruda bulunan|Ana bilgisayar adı|Diğer Ad|TTL|
    |---|---|---|---|
    |Diğer Konak|autodiscover|autodiscover.outlook.com|1 Saat|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="CNAME değerlerini yazın veya kopyalayıp pencereye yapıştırın.":::

1. **EKLE'yi** seçin.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa, Microsoft için yeni bir tane oluşturmayın. Bunun yerine, her iki değer kümesini içeren *tek* bir SPF kaydına sahip olmak için gerekli Microsoft değerlerini geçerli kayda ekleyin.

1. Başlamak için [bu bağlantıyı](https://checkout.web.com/manage-it/index.jsp) kullanarak web.com'deki etki alanları sayfanıza gidin. Önce oturum açın.

1. Giriş sayfasında **Etki Alanı Adları'nı** seçin.

1. **Eylemler'in** altında üç noktayı seçin ve ardından açılan listede **Yönet'i** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. **Gelişmiş Araçlar'ı** seçmek için ekranı aşağı kaydırın ve **Gelişmiş DNS Kayıtları'nın** yanında **YÖNET'i** seçin.

    Gelişmiş DNS Kayıtlarını Yönet sayfasına ulaşmak için **Devam'ı** seçmeniz gerekebilir.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Gelişmiş DNS kayıtları'nın yanında YÖNET'i seçin.":::

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında **+ KAYıT EKLE'yi** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="+ KAYıT EKLE'yi seçin.":::

1. **Tür** altında, açılan listeden **TXT'yi** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="Tür açılan listesinde TXT'yi seçin.":::

1. Aşağıdaki tabloda yer alan değerleri seçin veya kopyalayıp yapıştırın.

    |Başvuruda bulunan|TXT değeri|TTL|
    |---|---|---|
    |@|v=spf1 include:spf.protection.outlook.com -all <br/> **Not:** Tüm aralıkların doğru kalması için bu girdiyi kopyalayıp yapıştırmanızı öneririz.|1 Saat|

1. **EKLE'yi** seçin.

## <a name="advanced-option-skype-for-business"></a>Gelişmiş seçenek: Skype for Business

Yalnızca kuruluşunuz Microsoft Teams ek olarak sohbet, konferans aramaları ve görüntülü aramalar gibi çevrimiçi iletişim hizmetleri için Skype for Business kullanıyorsa bu seçeneği belirleyin. Skype 4 kayıt gerekir: Kullanıcıdan kullanıcıya iletişim için 2 SRV kaydı ve oturum açıp kullanıcıları hizmete bağlamak için 2 CNAME kaydı.

### <a name="add-the-two-required-srv-records"></a>Gerekli iki SRV kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://checkout.web.com/manage-it/index.jsp) kullanarak web.com'deki etki alanları sayfanıza gidin. Önce oturum açın.

1. Giriş sayfasında **Etki Alanı Adları'nı** seçin.

1. **Eylemler'in** altında üç noktayı seçin ve ardından açılan listede **Yönet'i** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. **Gelişmiş Araçlar'ı** seçmek için ekranı aşağı kaydırın ve **Gelişmiş DNS Kayıtları'nın** yanında **YÖNET'i** seçin.

    Gelişmiş DNS Kayıtlarını Yönet sayfasına ulaşmak için **Devam'ı** seçmeniz gerekebilir.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Gelişmiş DNS kayıtları'nın yanında YÖNET'i seçin.":::

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında **+ KAYıT EKLE'yi** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="+ KAYıT EKLE'yi seçin.":::

1. **Tür'ün** altında, açılan listeden **SRV'yi** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv.png" alt-text="Tür açılan listesindeN SRV'yi seçin.":::

1. Aşağıdaki tabloda yer alan değerleri seçin veya kopyalayıp yapıştırın.

    |Tür|Hizmet|Protokol|Ağırlık|Bağlantı noktası|Hedef|Öncelik|TTL|
    |---|---|---|---|---|---|---|---|
    |SRV|_sip|TLS|100|443|sipdir.online.lync.com <br/> **Bu değer nokta (.) ile bitemez**|1|1 Saat|
    |SRV|_sipfederationtls|TCP|100|5061|sipfed.online.lync.com <br/> **Bu değer nokta (.) ile bitemez**|1|1 Saat|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv-add.png" alt-text="Tablodaki değerleri yazın veya kopyalayıp SRV kayıt penceresine yapıştırın.":::

1. **EKLE'yi** seçin.

1. Tablonun ikinci satırındaki değerleri kopyalayarak diğer SRV kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışıyla veya diğer sorunlarla karşılaşıyorsanız, bkz. [Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Skype for Business için gereken iki CNAME kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://checkout.web.com/manage-it/index.jsp) kullanarak web.com'deki etki alanları sayfanıza gidin. Önce oturum açın.

1. Giriş sayfasında **Etki Alanı Adları'nı** seçin.

1. **Eylemler'in** altında üç noktayı seçin ve ardından açılan listede **Yönet'i** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. **Gelişmiş Araçlar'ı** seçmek için ekranı aşağı kaydırın ve **Gelişmiş DNS Kayıtları'nın** yanında **YÖNET'i** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Gelişmiş DNS kayıtları'nın yanında YÖNET'i seçin.":::

    Gelişmiş DNS Kayıtlarını Yönet sayfasına ulaşmak için **Devam'ı** seçmeniz gerekebilir.

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında **+ KAYıT EKLE'yi** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="+ KAYıT EKLE'yi seçin.":::

1. **Tür** altında, açılan listeden **CNAME'i** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Tür açılan listesindeN CNAME'yi seçin.":::

1. Aşağıdaki tabloda yer alan değerleri seçin veya kopyalayıp yapıştırın.

    |Tür|Başvuruda bulunan|Ana Bilgisayar Adı|Diğer Ad|TTL|
    |---|---|---|---|---|
    |CNAME|Diğer Konak|sip|sipdir.online.lync.com <br/> **Bu değer nokta (.) ile bitemez**|1 Saat|
    |CNAME|Diğer Konak|lyncdiscover|webdir.online.lync.com <br/> **Bu değer nokta (.) ile bitemez**|1 Saat|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="CNAME değerlerini yazın veya kopyalayıp pencereye yapıştırın.":::

1. **EKLE'yi** seçin.

1. Tablonun ikinci satırındaki değerleri kopyalayarak diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Gelişmiş seçenek: Microsoft 365 için Intune ve Mobil Cihaz Yönetimi

Bu hizmet, etki alanınıza bağlanan mobil cihazları güvenli ve uzaktan yönetmenize yardımcı olur. Mobil Cihaz Yönetimi, kullanıcıların cihazları hizmete kaydedebilmesi için 2 CNAME kaydına ihtiyaç duyar.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Mobile Cihaz Yönetimi için gereken iki CNAME kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://checkout.web.com/manage-it/index.jsp) kullanarak web.com'deki etki alanları sayfanıza gidin. Önce oturum açın.

1. Giriş sayfasında **Etki Alanı Adları'nı** seçin.

1. **Eylemler'in** altında üç noktayı seçin ve ardından açılan listede **Yönet'i** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. **Gelişmiş Araçlar'ı** seçmek için ekranı aşağı kaydırın ve **Gelişmiş DNS Kayıtları'nın** yanında **YÖNET'i** seçin.

    Gelişmiş DNS Kayıtlarını Yönet sayfasına ulaşmak için **Devam'ı** seçmeniz gerekebilir.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Gelişmiş DNS kayıtları'nın yanında YÖNET'i seçin.":::

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında **+ KAYıT EKLE'yi** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="+ KAYıT EKLE'yi seçin.":::

1. **Tür** altında, açılan listeden **CNAME'i** seçin.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Tür açılan listesindeN CNAME'yi seçin.":::

1. Aşağıdaki tabloda yer alan değerleri seçin veya kopyalayıp yapıştırın.

    |Tür|Başvuruda bulunan|Ana Bilgisayar Adı|Diğer Ad|TTL|
    |---|---|---|---|---|
    |CNAME|Diğer Konak|enterpriseregistration|enterpriseregistration.windows.net <br/> **Bu değer nokta (.) ile bitemez**|1 Saat|
    |CNAME|Diğer Konak|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com <br/> **Bu değer nokta (.) ile bitemez**|1 Saat|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Tablodaki CNAME değerlerini yazın veya kopyalayıp pencereye yapıştırın.":::

1. **EKLE'yi** seçin.

1. Tablonun ikinci satırındaki değerleri kopyalayarak diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.
