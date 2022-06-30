---
title: 123-reg.co.uk'deki DNS kayıtlarınızı Microsoft 365'e bağlama
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
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
description: Microsoft için 123-reg.co.uk'da etki alanınızı doğrulamayı ve e-posta, Skype Kurumsal Online ve diğer hizmetler için DNS kayıtlarını ayarlamayı öğrenin.
ms.openlocfilehash: 97a00c046f467dd4ced4c63a4cbfc8114d06d2dd
ms.sourcegitcommit: 8cd230e243eba452b27f725d66152becb6aff49b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66563417"
---
# <a name="connect-your-dns-records-at-123-regcouk-to-microsoft-365"></a>123-reg.co.uk'deki DNS kayıtlarınızı Microsoft 365'e bağlama

 **Aradığınızı bulamazsanız, [Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**.

DNS barındırma sağlayıcınız 123-reg.co.uk ise, bu makalede verilen adımları izleyerek etki alanınızı doğrulayın ve e-posta, Skype Kurumsal Çevrimiçi Sürümü vb. için DNS kayıtlarını ayarlayın.

Bu kayıtları 123-reg.co.uk ekledikten sonra, etki alanınız Microsoft hizmetleriyle çalışacak şekilde ayarlanır.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışıyla veya diğer sorunlarla karşılaşıyorsanız, bkz. [Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Doğrulama için bir TXT kaydı ekleme

Etki alanınızı Microsoft ile kullanmadan önce, etki alanına sahip olduğunuzdan emin olmamız gerekir. Etki alanı kayıt şirketinizde hesabınızda oturum açıp DNS kaydını oluşturabilmek, Microsoft'a etki alanının sahibi olduğunuzu kanıtlar.

> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. Dilerseniz bu kaydı daha sonra silebilirsiniz.

1. Başlamak için [bu bağlantıyı](https://www.123-reg.co.uk/secure/cpanel/domain/overview) kullanarak 123-reg.co.uk adresindeki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

2. **Etki Alanları'nı** seçin ve Etki alanına genel bakış sayfasında, doğrulamak istediğiniz etki alanının adını seçin veya Denetim masasına gidin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Doğrulamak istediğiniz etki alanını seçin.":::

3. Etki alanını yönet sayfasındaki **Gelişmiş etki alanı ayarları'nın** altında **DNS'yi yönet'i** seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Açılan listeden DNS'yi yönet'i seçin.":::

4. DNS'nizi yönetin sayfasında **Gelişmiş DNS** sekmesini seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Gelişmiş DNS sekmesini seçin.":::

5. Yeni kaydın **Tür** kutusunda açılan listeden **TXT/SPF'yi** seçin ve ardından aşağıdaki tabloda yer alan diğer değerleri yazın veya kopyalayıp yapıştırın.

    |Ana Bilgisayar Adı|Tür|Hedef TXT/SPF|
    |---|---|---|
    |@|TXT/SPF|MS=ms *XXXXXXXX* <br/> **Not:** Bu bir örnektir. Burada, tablodan belirli **Hedef veya İşaret Edilen Adres** değerinizi kullanın. [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Açılan listeden TXT/SPF türünü seçin ve değerleri doldurun.":::

6. **Ekle**'yi seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="Ekle'yi seçin.":::

   Yeni oluşturduğunuz kaydın İnternet genelinde güncelleştirilebilmesi için devam etmeden önce birkaç dakika bekleyin.

Artık kaydı etki alanı kayıt şirketinizin sitesine eklediğinize göre, Microsoft'a geri dönüp kayıt için arama isteğinde bulunacaksınız. Microsoft doğru TXT kaydını bulduğunda etki alanınız doğrulanır.

Microsoft 365'te kaydı doğrulamak için:

1. Yönetim merkezinde **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Etki Alanları'na**</a> gidin.

1. Etki Alanları sayfasında, doğrulamakta olduğunuz etki alanını seçin ve **kurulumu başlat'ı** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. **Devam**'ı seçin.

1. **Etki alanını doğrula** sayfasında **Doğrula'yı** seçin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Etki alanınız için e-postanın Microsoft'a gelmesi için bir MX kaydı ekleyin

1. Başlamak için [bu bağlantıyı](https://www.123-reg.co.uk/secure/cpanel/domain/overview) kullanarak 123-reg.co.uk adresindeki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

2. Etki alanı adına genel bakış sayfasında, düzenlemek istediğiniz etki alanının adını seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Düzenlemek istediğiniz etki alanının adını seçin.":::

3. Etki alanını yönet sayfasındaki **Gelişmiş etki alanı ayarları'nın** altında **DNS'yi yönet'i** seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Açılan listeden DNS'yi yönet'i seçin.":::

4. DNS'nizi yönetin sayfasında **Gelişmiş DNS** sekmesini seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Gelişmiş DNS sekmesini seçin.":::

5. Yeni kaydın **Tür** kutusunda, açılan listeden **MX'i** seçin ve ardından aşağıdaki tabloda yer alan diğer değerleri yazın veya kopyalayıp yapıştırın.

    |Ana Bilgisayar Adı|Tür|Öncelik|Hedef MX|
    |---|---|---|---|
    |@|MX|1 <br/> Öncelik hakkında daha fazla bilgi için bkz. [MX önceliği nedir?](../setup/domains-faq.yml)|*\<domain-key\>*.mail.protection.outlook.com. <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> **Not:** Microsoft hesabınızdan alın \<domain-key\> . [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX.png" alt-text="Açılan listeden MX türünü seçin ve değerleri doldurun.":::

6. **Ekle**'yi seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-Add.png" alt-text="Ekle'yi seçin.":::

7. Başka MX kayıtları varsa, bu kaydın **Sil (çöp kutusu)** simgesini seçerek her birini kaldırın.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-delete.png" alt-text="Sil'i (çöp kutusu) seçin.":::

## <a name="add-the-cname-record-required-for-microsoft"></a>Microsoft için gereken CNAME kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://www.123-reg.co.uk/secure/cpanel/domain/overview) kullanarak 123-reg.co.uk adresindeki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

2. Etki alanı adına genel bakış sayfasında, düzenlemek istediğiniz etki alanının adını seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Düzenlemek istediğiniz etki alanının adını seçin.":::

3. Etki alanını yönet sayfasındaki **Gelişmiş etki alanı ayarları'nın** altında **DNS'yi yönet'i** seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Açılan listeden DNS'yi yönet'i seçin.":::

4. DNS'nizi yönetin sayfasında **Gelişmiş DNS** sekmesini seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Gelişmiş DNS sekmesini seçin.":::

5. CNAME kaydını ekleyin.

    Yeni kaydın **Tür** kutusunda, açılan listeden **CNAME'yi** seçin ve ardından aşağıdaki tabloda yer alan diğer değerleri yazın veya kopyalayıp yapıştırın.

    |Ana Bilgisayar Adı|Tür|Hedef CNAME|
    |---|---|---|
    |autodiscover|CNAME|autodiscover.outlook.com. <br/> **Bu değer nokta (.) ile bitmelidir.**|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Açılan listeden CNAME türünü seçin ve değerleri doldurun.":::

6. **Ekle**'yi seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Ekle'yi seçin.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa Microsfot için yeni bir tane oluşturmayın. Bunun yerine, her iki değer kümesini içeren *tek* bir SPF kaydına sahip olmak için gerekli Microsoft değerlerini geçerli kayda ekleyin. Örneklere mi ihtiyacınız var? [Microsoft için bu Dış Etki Alanı Adı Sistemi kayıtlarına](../../enterprise/external-domain-name-system-records.md) göz atın. SPF kaydınızı doğrulamak için bu [SPF doğrulama araçlarından](../setup/domains-faq.yml) birini kullanabilirsiniz.

1. Başlamak için [bu bağlantıyı](https://www.123-reg.co.uk/secure/cpanel/domain/overview) kullanarak 123-reg.co.uk adresindeki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

2. Etki alanı adına genel bakış sayfasında, düzenlemek istediğiniz etki alanının adını seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Düzenlemek istediğiniz etki alanının adını seçin.":::

3. Etki alanını yönet sayfasındaki **Gelişmiş etki alanı ayarları'nın** altında **DNS'yi yönet'i** seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Açılan listeden DNS'yi yönet'i seçin.":::

4. DNS'nizi yönetin sayfasında **Gelişmiş DNS** sekmesini seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Gelişmiş DNS sekmesini seçin.":::

5. Yeni kaydın **Tür** kutusunda açılan listeden **TXT/SPF'yi** seçin ve ardından aşağıdaki tabloda yer alan diğer değerleri yazın veya kopyalayıp yapıştırın.

    |Ana Bilgisayar Adı|Tür|Hedef TXT/SPF|
    |---|---|---|
    |@|TXT/SPF|v=spf1 include:spf.protection.outlook.com -all <br/> **Not:** Tüm aralıkların doğru kalması için bu girdiyi kopyalayıp yapıştırmanızı öneririz.|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Açılan listeden TXT/SPF türünü seçin ve değerleri doldurun.":::

6. **Ekle**'yi seçin.

## <a name="advanced-option-skype-for-business"></a>Gelişmiş seçenek: Skype Kurumsal

Bu seçeneği yalnızca kuruluşunuz Microsoft Teams'in yanı sıra sohbet, konferans aramaları ve görüntülü aramalar gibi çevrimiçi iletişim hizmetleri için Skype Kurumsal kullanıyorsa belirtin. Skype için 4 kayıt gerekir: Kullanıcıdan kullanıcıya iletişim için 2 SRV kaydı ve oturum açmak ve kullanıcıları hizmete bağlamak için 2 CNAME kaydı.

### <a name="add-the-two-required-srv-records"></a>Gerekli iki SRV kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://www.123-reg.co.uk/secure/cpanel/domain/overview) kullanarak 123-reg.co.uk adresindeki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

2. Etki alanı adına genel bakış sayfasında, düzenlemek istediğiniz etki alanının adını seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Düzenlemek istediğiniz etki alanının adını seçin.":::

3. Etki alanını yönet sayfasındaki **Gelişmiş etki alanı ayarları'nın** altında **DNS'yi yönet'i** seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Açılan listeden DNS'yi yönet'i seçin.":::

4. DNS'nizi yönetin sayfasında **Gelişmiş DNS** sekmesini seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Gelişmiş DNS sekmesini seçin.":::

5. İki SRV kaydından ilkini ekleyin:

   Yeni kaydın **Tür** kutusunda, açılan listeden **SRV'yi** seçin ve ardından aşağıdaki tabloda yer alan diğer değerleri yazın veya kopyalayıp yapıştırın.

    |Ana Bilgisayar Adı|Tür|Öncelik|TTL|Hedef SRV|
    |---|---|---|---|---|
    |_sip._tls|SRV|100|3600|1 443 sipdir.online.lync.com. **Bu değer nokta (.) ile bitmelidir.** <br/> **Not:** Tüm aralıkların doğru kalması için bu girdiyi kopyalayıp yapıştırmanızı öneririz.|
    |_sipfederationtls._tcp|SRV|100|3600|1 5061 sipfed.online.lync.com. **Bu değer nokta (.) ile bitmelidir.** <br/> **Not:** Tüm aralıkların doğru kalması için bu girdiyi kopyalayıp yapıştırmanızı öneririz.|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Açılan listeden TXT/SPF türünü seçin ve değerleri doldurun.":::

6. **Ekle**'yi seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="Ekle'yi seçin.":::

7. Diğer SRV kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışıyla veya diğer sorunlarla karşılaşıyorsanız, bkz. [Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Skype Kurumsal için gereken iki CNAME kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://www.123-reg.co.uk/secure/cpanel/domain/overview) kullanarak 123-reg.co.uk adresindeki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

1. Etki alanı adına genel bakış sayfasında, düzenlemek istediğiniz etki alanının adını seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Düzenlemek istediğiniz etki alanının adını seçin.":::

1. Etki alanını yönet sayfasındaki **Gelişmiş etki alanı ayarları'nın** altında **DNS'yi yönet'i** seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Açılan listeden DNS'yi yönet'i seçin.":::

1. DNS'nizi yönetin sayfasında **Gelişmiş DNS** sekmesini seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Gelişmiş DNS sekmesini seçin.":::

1. İlk CNAME kaydını ekleyin.

    Yeni kaydın **Tür** kutusunda, açılan listeden **CNAME'yi** seçin ve ardından aşağıdaki tabloda yer alan diğer değerleri yazın veya kopyalayıp yapıştırın.

    |Ana Bilgisayar Adı|Tür|Hedef CNAME|
    |---|---|---|
    |sip|CNAME|sipdir.online.lync.com. <br/> **Bu değer nokta (.) ile bitmelidir.**|
    |lyncdiscover|CNAME|webdir.online.lync.com. <br/> **Bu değer nokta (.) ile bitmelidir.**|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Açılan listeden CNAME türünü seçin ve değerleri doldurun.":::

1. **Ekle**'yi seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Ekle'yi seçin.":::

1. Diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Gelişmiş seçenek: Microsoft 365 için Intune ve Mobil Cihaz Yönetimi

Bu hizmet, etki alanınıza bağlanan mobil cihazları güvenli ve uzaktan yönetmenize yardımcı olur. Mobil Cihaz Yönetimi, kullanıcıların cihazları hizmete kaydedebilmesi için iki CNAME kaydına ihtiyaç duyar.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Mobile Cihaz Yönetimi için gereken iki CNAME kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://www.123-reg.co.uk/secure/cpanel/domain/overview) kullanarak 123-reg.co.uk adresindeki etki alanları sayfanıza gidin. İlk önce oturum açmanız istenir.

1. Etki alanı adına genel bakış sayfasında, düzenlemek istediğiniz etki alanının adını seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Düzenlemek istediğiniz etki alanının adını seçin.":::

1. Etki alanını yönet sayfasındaki **Gelişmiş etki alanı ayarları'nın** altında **DNS'yi yönet'i** seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Açılan listeden DNS'yi yönet'i seçin.":::

1. DNS'nizi yönetin sayfasında **Gelişmiş DNS** sekmesini seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Gelişmiş DNS sekmesini seçin.":::

1. İlk CNAME kaydını ekleyin.

    Yeni kaydın **Tür** kutusunda, açılan listeden **CNAME'yi** seçin ve ardından aşağıdaki tabloda yer alan diğer değerleri yazın veya kopyalayıp yapıştırın.

   |Ana Bilgisayar Adı|Tür|Hedef CNAME|
   |---|---|---|
   |enterpriseregistration|CNAME|enterpriseregistration.windows.net. <br/> **Bu değer nokta (.) ile bitmelidir.**|
   |enterpriseenrollment|CNAME|enterpriseenrollment.manage.microsoft.com. <br/> **Bu değer nokta (.) ile bitmelidir.**|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Açılan listeden CNAME türünü seçin ve değerleri doldurun.":::

1. **Ekle**'yi seçin.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Ekle'yi seçin.":::

1. Diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.
