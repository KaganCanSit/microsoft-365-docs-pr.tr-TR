---
title: Wix'teki DNS kayıtlarınızı Microsoft 365'e bağlama
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
ms.assetid: 7173c635-58b3-400f-95e0-97abe915565e
description: Microsoft için Wix'te etki alanınızı doğrulamayı ve e-posta, Skype Kurumsal Online ve diğer hizmetler için DNS kayıtlarını ayarlamayı öğrenin.
ms.openlocfilehash: 9ae245481173b99a9cb1221ed0650dc0b91feecd
ms.sourcegitcommit: 8cd230e243eba452b27f725d66152becb6aff49b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66563197"
---
# <a name="connect-your-dns-records-at-wix-to-microsoft-365"></a>Wix'teki DNS kayıtlarınızı Microsoft 365'e bağlama

Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**.

DNS barındırma sağlayıcınız Wix ise, etki alanınızı doğrulamak ve e-posta, Skype Kurumsal Online vb. için DNS kayıtlarını ayarlamak için bu makaledeki adımları izleyin.

Wix'te bu kayıtları ekledikten sonra, etki alanınız Microsoft hizmetleriyle çalışacak şekilde ayarlanır.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

## <a name="add-a-txt-record-for-verification"></a>Doğrulama için bir TXT kaydı ekleme

Etki alanınızı Microsoft ile kullanmadan önce, etki alanına sahip olduğunuzdan emin olmamız gerekir. Etki alanı kayıt şirketinizde hesabınızda oturum açıp DNS kaydını oluşturabilmek, Microsoft'a etki alanının sahibi olduğunuzu kanıtlar.

> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. İsterseniz daha sonra silebilirsiniz.

> [!NOTE]
> WIX, alt etki alanları için DNS girdilerini desteklemez.

1. Başlamak için [bu bağlantıyı](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account) kullanarak Wix'teki etki alanları sayfanıza gidin. Önce oturum açmanız istenir.

2. **Etki Alanları** \> **...** öğesini ve ardından açılan **listeden DNS Kayıtlarını Yönet'i** seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Açılan listeden DNS Kayıtlarını Yönet'i seçin.":::

3. DNS düzenleyicisinin **TXT (Metin)** satırında **+ Kayıt Ekle'yi** seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="Kayıt ekle'yi seçin.":::

4. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

   |Ana Bilgisayar Adı|TXT Değeri|TTL|
   |---|---|---|
   |Otomatik olarak doldurulan (boş bırakın)|MS=ms *XXXXXXXX* <br/> **Not:** Bu bir örnektir. Burada, tablodan belirli **Hedef veya İşaret Edilen Adres** değerinizi kullanın. [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)|1 Saat|

5. **Kaydet'i** seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="Kaydet'i seçin.":::

   Yeni oluşturduğunuz kaydın İnternet genelinde güncelleştirilebilmesi için devam etmeden önce birkaç dakika bekleyin.


Artık kaydı etki alanı kayıt şirketinizin sitesine eklediğinize göre, Microsoft'a geri dönüp kaydı istemeniz gerekir. Microsoft doğru TXT kaydını bulduğunda etki alanınız doğrulanır.

Microsoft 365'te kaydı doğrulamak için:

1. Yönetim merkezinde **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Etki Alanları'na**</a> gidin.

1. Etki Alanları sayfasında, doğrulamakta olduğunuz etki alanını seçin ve **kurulumu başlat'ı** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. **Devam**'ı seçin.

1. **Etki alanını doğrula** sayfasında **Doğrula'yı** seçin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Etki alanınız için e-postanın Microsoft'a gelmesi için bir MX kaydı ekleyin

1. Başlamak için [bu bağlantıyı](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account) kullanarak Wix'teki etki alanları sayfanıza gidin. Önce oturum açmanız istenir.

1. **Etki Alanları** \> **...** öğesini ve ardından açılan **listeden DNS Kayıtlarını Yönet'i** seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Açılan listeden DNS Kayıtlarını Yönet'i seçin.":::

1. **MX (Posta değişimi) altında** **MX Kayıtlarını Düzenle'yi** seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-edit-mx-records.png" alt-text="MX Kayıtlarını Düzenle'yi seçin.":::

1. Açılan listeden **Diğer'i** ve **ardından + Kayıt ekle'yi** seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-other.png" alt-text="Açılan listeden Diğer'i seçin.":::

1. Yeni kaydın kutularına aşağıdaki tabloda yer alan değerleri yazın veya kopyalayıp yapıştırın:

   |Ana Bilgisayar Adı|İşaret edilen|Öncelik|TTL|
   |---|---|---|---|
   |Otomatik olarak doldurulan|*\<domain-key\>*.mail.protection.outlook.com <br/> **Not:** Microsoft hesabınızdan alın *\<domain-key\>* .  [How do I find this?](../get-help-with-domains/information-for-dns-records.md)|0 <br/> Öncelik hakkında daha fazla bilgi için bkz. [MX önceliği nedir?](../setup/domains-faq.yml)|1 Saat|

1. Listelenen başka MX kayıtları varsa bunların her birini silin.

  :::image type="content" source="../../media/dns-wix/wix-domains-mx-delete.png" alt-text="Sil'i seçin.":::

1. **Kaydet**'i seçin.

## <a name="add-the-cname-record-required-for-microsoft"></a>Microsoft için gereken CNAME kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account) kullanarak Wix'teki etki alanları sayfanıza gidin. Önce oturum açmanız istenir.

2. **Etki Alanları** \> **...** öğesini ve ardından açılan **listeden DNS Kayıtlarını Yönet'i** seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Açılan listeden DNS Kayıtlarını Yönet'i seçin.":::

3. CNAME kaydı için DNS düzenleyicisinin **CNAME (Diğer Adlar)** satırında **+ Kayıt Ekle'yi** seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="+ Kayıt Ekle'yi seçin.":::

4. Yeni kaydın kutularına aşağıdaki tabloda yer alan değerleri yazın veya kopyalayıp yapıştırın:

   |Ana Bilgisayar Adı|Değer|TTL|
   |---|---|---|
   |autodiscover|autodiscover.outlook.com|1 Saat|

5. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Kaydet'i seçin.":::

   Yeni oluşturduğunuz kaydın İnternet genelinde güncelleştirilebilmesi için devam etmeden önce birkaç dakika bekleyin.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa, Microsoft için yeni bir tane oluşturmayın. Bunun yerine, her iki değer kümesini içeren *tek* bir SPF kaydına sahip olmak için gerekli Microsoft değerlerini geçerli kayda ekleyin.

1. Başlamak için [bu bağlantıyı](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account) kullanarak Wix'teki etki alanları sayfanıza gidin. Önce oturum açmanız istenir.

2. **Etki Alanları** \> **...** öğesini ve ardından açılan **listeden DNS Kayıtlarını Yönet'i** seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Açılan listeden DNS Kayıtlarını Yönet'i seçin.":::

3. DNS düzenleyicisinin **TXT (Metin)** satırında **+ Kayıt Ekle'yi** seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="+ Kayıt ekle'yi seçin.":::

   **Not**: Wix, DNS düzenleyicisinde bir SPF satırı sağlar. Bu satırı yoksayın ve txt **(Metin)** satırını kullanarak aşağıdaki SPF değerlerini girin.

4. Yeni kaydın kutularına aşağıdaki tabloda yer alan değerleri yazın veya kopyalayıp yapıştırın:

   |Ana Bilgisayar Adı|Değer|TTL|
   |---|---|---|
   |[bunu boş bırakın]|v=spf1 include:spf.protection.outlook.com -all <br/> **Not:** Tüm aralıkların doğru kalması için bu girdiyi kopyalayıp yapıştırmanızı öneririz.|1 Saat|

5. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="Kaydet'i seçin.":::

   Yeni oluşturduğunuz kaydın İnternet genelinde güncelleştirilebilmesi için devam etmeden önce birkaç dakika bekleyin.

## <a name="advanced-option-skype-for-business"></a>Gelişmiş seçenek: Skype Kurumsal

Bu seçeneği yalnızca kuruluşunuz Microsoft Teams'in yanı sıra sohbet, konferans aramaları ve görüntülü aramalar gibi çevrimiçi iletişim hizmetleri için Skype Kurumsal kullanıyorsa belirtin. Skype için dört kayıt gerekir: kullanıcıdan kullanıcıya iletişim için iki SRV kaydı ve oturum açmak ve kullanıcıları hizmete bağlamak için iki CNAME kaydı.

### <a name="add-the-two-required-srv-records"></a>Gerekli iki SRV kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account) kullanarak Wix'teki etki alanları sayfanıza gidin. Önce oturum açmanız istenir.

1. **Etki Alanları** \> **...** öğesini ve ardından açılan **listeden DNS Kayıtlarını Yönet'i** seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Açılan listeden DNS Kayıtlarını Yönet'i seçin.":::

1. DNS düzenleyicisinin **SRV** satırında **+ Kayıt Ekle'yi** seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-srv-add-record.png" alt-text="+ Kayıt Ekle'yi seçin.":::

1. Yeni kaydın kutularına, tablonun ilk satırındaki değerleri yazın veya kopyalayıp yapıştırın:

   |Hizmet|Protokol|Ana bilgisayar adı|Ağırlık|Bağlantı noktası|Hedef|Öncelik|TTL|
   |---|---|---|---|---|---|---|---|
   |sip|tls|Otomatik olarak doldurulan|1|443|sipdir.online.lync.com|100|1 Saat|
   |sipfed|tcp|Otomatik olarak doldurulan|1|5061|sipfed.online.lync.com|100|1 Saat|

1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-srv-save.png" alt-text="Kaydet'i seçin.":::

1. Tablonun ikinci satırındaki değerleri kopyalayarak diğer SRV kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışıyla veya diğer sorunlarla karşılaşıyorsanız, bkz. [Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Skype Kurumsal için gereken iki CNAME kaydını ekleme

1. DNS düzenleyicisinin **CNAME (Diğer Adlar)** satırında **+ Ekle'yi** seçin ve aşağıdaki tablonun ilk satırında yer alan değerleri girin.

   |Tür|Ana Bilgisayar|Değer|TTL|
   |---|---|---|---|
   |CNAME|sip|sipdir.online.lync.com. <br/> **Bu değer nokta (.) ile bitmelidir.**|1 Saat|
   |CNAME|lyncdiscover|webdir.online.lync.com. <br/> **Bu değer nokta (.) ile bitmelidir.**|1 Saat|

1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Kaydet'i seçin.":::

1. Tablonun ikinci satırındaki değerleri kopyalayarak diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Gelişmiş seçenek: Microsoft 365 için Intune ve Mobil Cihaz Yönetimi

Bu hizmet, etki alanınıza bağlanan mobil cihazları güvenli ve uzaktan yönetmenize yardımcı olur. Mobil Cihaz Yönetimi, kullanıcıların cihazları hizmete kaydedebilmesi için iki CNAME kaydına ihtiyaç duyar.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Mobile Cihaz Yönetimi için gereken iki CNAME kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account) kullanarak Wix'teki etki alanları sayfanıza gidin. Önce oturum açmanız istenir.

1. **Etki Alanları** \> **...** öğesini ve ardından açılan **listeden DNS Kayıtlarını Yönet'i** seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Açılan listeden DNS Kayıtlarını Yönet'i seçin.":::

1. CNAME kaydı için DNS düzenleyicisinin **CNAME (Diğer Adlar)** satırında **+ Kayıt Ekle'yi** seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="+ Kayıt Ekle'yi seçin.":::

1. Aşağıdaki tablodaki ilk satırdaki değerleri girin.

    |Tür|Ana Bilgisayar|Değer|TTL|
    |---|---|---|---|
    |CNAME|enterpriseregistration|enterpriseregistration.windows.net. <br/> **Bu değer nokta (.) ile bitmelidir.**|1 Saat|
    |CNAME|enterpriseenrollment|enterpriseenrollment.manage.microsoft.com. <br/> **Bu değer nokta (.) ile bitmelidir.**|1 Saat|

1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Kaydet'i seçin.":::

1. Tablonun ikinci satırındaki değerleri kopyalayarak diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.
