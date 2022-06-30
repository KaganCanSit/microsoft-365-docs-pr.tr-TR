---
title: Cloudflare'daki DNS kayıtlarınızı Microsoft 365'e bağlama
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
ms.assetid: 84acd4fc-6eec-4d00-8bed-568f036ae2af
description: Microsoft için Cloudflare'da etki alanınızı doğrulamayı ve e-posta, Skype Kurumsal Online ve diğer hizmetler için DNS kayıtlarını ayarlamayı öğrenin.
ms.openlocfilehash: 50dbee0ab2ca587ee628a40fdc9c032ec9c8820d
ms.sourcegitcommit: 8cd230e243eba452b27f725d66152becb6aff49b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66563329"
---
# <a name="connect-your-dns-records-at-cloudflare-to-microsoft-365"></a>Cloudflare'daki DNS kayıtlarınızı Microsoft 365'e bağlama

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**.

DNS barındırma sağlayıcınız Cloudflare ise, etki alanınızı doğrulamak ve e-posta, Skype Kurumsal Online vb. için DNS kayıtlarını ayarlamak için bu makaledeki adımları izleyin.

## <a name="before-you-begin"></a>Başlamadan önce

Etki alanınız için DNS kayıtlarını ayarlamak için iki seçeneğiniz vardır:

- [**Domain Connect'i kullanma**](#use-domain-connect-to-verify-and-set-up-your-domain) Etki alanınızı başka bir e-posta hizmeti sağlayıcısıyla ayarlamadıysanız, yeni etki alanınızı otomatik olarak doğrulamak ve Microsoft 365 ile kullanmak üzere ayarlamak için Domain Connect adımlarını kullanın.

    VEYA

- [**El ile uygulanan adımları kullanma**](#create-dns-records-with-manual-setup) Aşağıdaki el ile uygulanan adımları kullanarak etki alanınızı doğrulayın ve etki alanı kayıt şirketinize ne zaman ve hangi kayıtların ekleneceğini seçin. Bu, yeni MX (posta) kayıtlarını( örneğin, uygun zamanda) ayarlamanıza olanak tanır.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Etki alanınızı doğrulamak ve ayarlamak için Domain Connect'i kullanma

Cloudflare etki alanınızı Microsoft 365 ile otomatik olarak doğrulamak ve ayarlamak için şu adımları izleyin:

1. Microsoft 365 yönetim merkezi **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Etki Alanları'nı**</a> seçin ve ayarlamak istediğiniz etki alanını seçin.

1. Üç noktayı seçin (diğer eylemler) \> **Kurulumu başlat'ı** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. Etki alanınızı nasıl bağlamak istiyorsunuz? sayfasında **Devam'ı** seçin.

1. DNS kayıtları ekle sayfasında **DNS kayıtları ekle'yi** seçin.

1. Cloudflare oturum açma sayfasında hesabınızda oturum açın ve **Yetkilendir'i** seçin.

    Bu işlem, Microsoft 365 için etki alanı kurulumunuzu tamamlar.

## <a name="create-dns-records-with-manual-setup"></a>El ile kurulum ile DNS kayıtları oluşturma

Bu kayıtları Cloudflare'a ekledikten sonra, etki alanınız Microsoft 365 hizmetleriyle çalışacak şekilde ayarlanır.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

### <a name="change-your-domains-nameserver-ns-records"></a>Etki alanınızın ad sunucusu (NS) kayıtlarını değiştirin

> [!IMPORTANT]
> Bu yordamı, etki alanınızı satın aldığınız ve kaydettirdiğiniz etki alanı kayıt şirketinde gerçekleştirmelisiniz.

Cloudflare'a kaydolduğunda, Cloudflare Kurulum işlemini kullanarak bir etki alanı eklediniz.

Eklediğiniz etki alanı Cloudflare veya ayrı bir etki alanı kayıt şirketi tarafından satın alındı. Microsoft 365'te etki alanınız için DNS kayıtlarını doğrulamak ve oluşturmak için öncelikle etki alanı kayıt şirketinizdeki ad sunucularını Cloudflare ad sunucularını kullanacak şekilde değiştirmeniz gerekir.

Etki alanı kayıt şirketinizin web sitesinde etki alanınızın ad sunucularını kendiniz değiştirmek için şu adımları izleyin.

1. Etki alanı kayıt şirketinizin web sitesinde etki alanınızın ad sunucularını düzenleyebileceğiniz yeri bulun.

2. Aşağıdaki tablodaki değerleri kullanarak iki ad sunucusu kaydı oluşturun veya mevcut ad sunucusu kayıtlarını bu değerlerle eşleşsin diye düzenleyin.

    |Tür|Değer|
    |---|---|
    |İlk ad sunucusu|Cloudflare tarafından sağlanan ad sunucusu değerini kullanın.|
    |İkinci ad sunucusu|Cloudflare tarafından sağlanan ad sunucusu değerini kullanın.|

    > [!TIP]
    > En az iki ad sunucusu kaydı kullanmalısınız. Listelenen başka ad sunucuları varsa, bunları silmeniz gerekir.

3. Değişikliklerinizi kaydedin.

> [!NOTE]
> Ad sunucusu kaydı güncelleştirmelerinizin İnternet DNS sistemi genelinde güncelleştirilmesi birkaç saat sürebilir. Ardından Microsoft e-postanız ve diğer hizmetlerin tümü etki alanınızla çalışacak şekilde ayarlanır.

### <a name="add-a-txt-record-for-verification"></a>Doğrulama için bir TXT kaydı ekleme

Etki alanınızı Microsoft ile kullanmadan önce, etki alanına sahip olduğunuzdan emin olmamız gerekir. Etki alanı kayıt şirketinizde hesabınızda oturum açıp DNS kaydını oluşturabilmek, Microsoft'a etki alanının sahibi olduğunuzu kanıtlar.

> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. Dilerseniz bu kaydı daha sonra silebilirsiniz.

1. Başlamak için [bu bağlantıyı](https://www.cloudflare.com/a/login) kullanarak Cloudflare'daki etki alanları sayfanıza gidin. Önce oturum açmanız istenir.

1. Giriş sayfasında, güncelleştirmek istediğiniz etki alanını seçin.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Güncelleştirmek istediğiniz etki alanını seçin.":::

1. Etki alanınızın Genel Bakış sayfasında **DNS'yi** seçin.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="DNS'yi seçin.":::

1. DNS yönetimi sayfasında **+Kayıt ekle'yi** seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Kayıt ekle'yi seçin.":::

1. Açılan listeden TXT türünü seçin ve bu tablodaki değerleri yazın veya kopyalayıp yapıştırın.

    |Tür|Name|TTL|İçerik|
    |---|---|---|:----|
    |TXT|@|30 dakika|MS=ms *XXXXXXXX* <br/> **Not:** Bu bir örnektir. Burada, tablodan belirli **Hedef veya İşaret Edilen Adres** değerinizi kullanın. [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)|

1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="Kayıt ekle'yi seçin.":::

   Yeni oluşturduğunuz kaydın İnternet genelinde güncelleştirilebilmesi için devam etmeden önce birkaç dakika bekleyin.

Artık kaydı etki alanı kayıt şirketinizin sitesine eklediğinize göre, Microsoft'a geri dönüp kaydı arayacaksınız. Microsoft doğru TXT kaydını bulduğunda etki alanınız doğrulanır.

Microsoft 365'te kaydı doğrulamak için:

1. Yönetim merkezinde **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Etki Alanları'na**</a> gidin.

1. Etki Alanları sayfasında, doğrulamakta olduğunuz etki alanını seçin ve **kurulumu başlat'ı** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. **Devam**'ı seçin.

1. **Etki alanını doğrula** sayfasında **Doğrula'yı** seçin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Etki alanınız için e-postanın Microsoft'a gelmesi için bir MX kaydı ekleyin

1. Başlamak için [bu bağlantıyı](https://www.cloudflare.com/a/login) kullanarak Cloudflare'daki etki alanları sayfanıza gidin. Önce oturum açmanız istenir.

1. Giriş sayfasında, güncelleştirmek istediğiniz etki alanını seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Güncelleştirmek istediğiniz etki alanını seçin.":::

1. Etki alanınızın Genel Bakış sayfasında **DNS'yi** seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="DNS'yi seçin.":::

1. DNS yönetimi sayfasında **+Kayıt ekle'yi** seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Kayıt ekle'yi seçin.":::

1. Açılan listeden MX türünü seçin ve bu tablodaki değerleri yazın veya kopyalayıp yapıştırın.

   |Tür|Name|Posta sunucusu|TTL|Öncelik|
   |---|---|---|---|---|
   |MX|@|*\<domain-key\>*.mail.protection.outlook.com <br/> **Not:** Microsoft 365 hesabınızdan alın *\<domain-key\>* . [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)|30 dakika|1 <br/> Öncelik hakkında daha fazla bilgi için bkz. [MX önceliği nedir?](../setup/domains-faq.yml) <br/>|

1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-save.png" alt-text="Kayıt ekle'yi seçin.":::

1. **MX Kayıtları** bölümünde listelenen başka MX kayıtları varsa **, Düzenle'yi** seçip **Sil'i** seçerek bunları silin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-delete.png" alt-text="Sil'i seçin.":::

1. Onay iletişim kutusunda **Sil'i** seçerek değişikliklerinizi onaylayın.

### <a name="add-the-cname-record-required-for-microsoft"></a>Microsoft için gereken CNAME kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://www.cloudflare.com/a/login) kullanarak Cloudflare'daki etki alanları sayfanıza gidin. Önce oturum açmanız istenir.

1. Giriş sayfasında, güncelleştirmek istediğiniz etki alanını seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Güncelleştirmek istediğiniz etki alanını seçin.":::

1. Etki alanınızın Genel Bakış sayfasında **DNS'yi** seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="DNS'yi seçin.":::

1. **DNS yönetimi** sayfasında **+Kayıt ekle'yi** seçin

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Kayıt ekle'yi seçin.":::

1. Açılan listeden CNAME türünü seçin ve bu tablodaki değerleri yazın veya kopyalayıp yapıştırın.

    |Tür|Name|Hedef|TTL|
    |---|---|---|---|
    |CNAME|autodiscover|autodiscover.outlook.com|Otomatik|

1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Kaydet'i seçin.":::

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa, Microsoft 365 için yeni bir tane oluşturmayın. Bunun yerine, gerekli Microsoft 365 değerlerini geçerli kayda ekleyerek her iki değer kümesini de içeren *tek* bir SPF kaydına sahip olmanız gerekir.

1. Başlamak için [bu bağlantıyı](https://www.cloudflare.com/a/login) kullanarak Cloudflare'daki etki alanları sayfanıza gidin. Önce oturum açmanız istenir.

1. Giriş sayfasında, güncelleştirmek istediğiniz etki alanını seçin.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Güncelleştirmek istediğiniz etki alanını seçin.":::

1. Etki alanınızın Genel Bakış sayfasında **DNS'yi** seçin.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="DNS'yi seçin.":::

1. DNS yönetimi sayfasında **+Kayıt ekle'yi** seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Kayıt ekle'yi seçin.":::

1. Açılan listeden TXT türünü seçin ve bu tablodaki değerleri yazın veya kopyalayıp yapıştırın.

    |Tür|Name|TTL|İçerik|
    |---|---|---|---|
    |TXT|@|30 dakika|v=spf1 include:spf.protection.outlook.com -all <br/> **Not:** Tüm aralıkların doğru kalması için bu girdiyi kopyalayıp yapıştırmanızı öneririz.|

1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="Kaydet'i seçin.":::

## <a name="advanced-option-skype-for-business"></a>Gelişmiş seçenek: Skype Kurumsal

Bu seçeneği yalnızca kuruluşunuz Microsoft Teams'in yanı sıra sohbet, konferans aramaları ve görüntülü aramalar gibi çevrimiçi iletişim hizmetleri için Skype Kurumsal kullanıyorsa belirtin. Skype için 4 kayıt gerekir: Kullanıcıdan kullanıcıya iletişim için 2 SRV kaydı ve oturum açmak ve kullanıcıları hizmete bağlamak için 2 CNAME kaydı.

### <a name="add-the-two-required-srv-records"></a>Gerekli iki SRV kaydını ekleme

> [!IMPORTANT]
> Bu işlevselliğin kullanılabilir hale getirilmesinden Cloudflare'ın sorumlu olduğunu unutmayın. Aşağıdaki adımlar ile geçerli Cloudflare GUI (Grafik Kullanıcı Arabirimi) arasında tutarsızlıklar görüyorsanız [Cloudflare Topluluğu'na](https://community.cloudflare.com/) başvurun.

1. Başlamak için [bu bağlantıyı](https://www.cloudflare.com/a/login) kullanarak Cloudflare'daki etki alanları sayfanıza gidin. Önce oturum açmanız istenir.

1. Giriş sayfasında, güncelleştirmek istediğiniz etki alanını seçin.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Güncelleştirmek istediğiniz etki alanını seçin.":::

1. Etki alanınızın Genel Bakış sayfasında **DNS'yi** seçin.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="DNS'yi seçin.":::

1. DNS yönetimi sayfasında **+Kayıt ekle'yi** seçin

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Kayıt ekle'yi seçin.":::

1. Açılan listeden SRV türünü seçin ve bu tablodaki değerleri yazın veya kopyalayıp yapıştırın.

    |Tür|Name|Hizmet|Protokol|TTL|Öncelik|Ağırlık|Bağlantı noktası|Hedef|
    |---|---|---|---|---|---|---|---|---|
    |SRV|*domain_name* kullanın; örneğin, contoso.com|_sip|TLS|30 dakika|100|1|443|sipfed.online.lync.com|
    |SRV|_sipfederationtls|TCP|*domain_name* kullanın; örneğin, contoso.com|30 dakika|100|1|5061|sipfed.online.lync.com|

1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-srv-save.png" alt-text="Kaydet'i seçin.":::

1. Tablonun ikinci satırındaki değerleri kopyalayarak diğer SRV kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Skype Kurumsal için gereken iki CNAME kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://www.cloudflare.com/a/login) kullanarak Cloudflare'daki etki alanları sayfanıza gidin. Önce oturum açmanız istenir.

1. Giriş sayfasında, güncelleştirmek istediğiniz etki alanını seçin.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Güncelleştirmek istediğiniz etki alanını seçin.":::

1. Etki alanınızın Genel Bakış sayfasında **DNS'yi** seçin.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="DNS'yi seçin.":::

1. DNS yönetimi sayfasında **+Kayıt ekle'yi** seçin

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Kayıt ekle'yi seçin.":::

1. Açılan listeden CNAME türünü seçin ve bu tablodaki değerleri yazın veya kopyalayıp yapıştırın.

    |Tür|Name|Hedef|TTL|
    |---|---|---|---|
    |CNAME|sip|sipdir.online.lync.com. <br/> **Bu değer nokta (.) ile bitmelidir.**|1 Saat|
    |CNAME|lyncdiscover|webdir.online.lync.com. <br/> **Bu değer nokta (.) ile bitmelidir.**|1 Saat|

1. **Kaydet'i** seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Kaydet'i seçin.":::

1. Tablonun ikinci satırındaki değerleri kopyalayarak diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Gelişmiş seçenek: Microsoft 365 için Intune ve Mobil Cihaz Yönetimi

Bu hizmet, etki alanınıza bağlanan mobil cihazları güvenli ve uzaktan yönetmenize yardımcı olur. Mobil Cihaz Yönetimi, kullanıcıların cihazları hizmete kaydedebilmesi için 2 CNAME kaydına ihtiyaç duyar.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Mobile Cihaz Yönetimi için gereken iki CNAME kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://www.cloudflare.com/a/login) kullanarak Cloudflare'daki etki alanları sayfanıza gidin. Önce oturum açmanız istenir.

1. Giriş sayfasında, güncelleştirmek istediğiniz etki alanını seçin.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Güncelleştirmek istediğiniz etki alanını seçin.":::

1. Etki alanınızın Genel Bakış sayfasında **DNS'yi** seçin.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="DNS'yi seçin.":::

1. DNS yönetimi sayfasında **+Kayıt ekle'yi** seçin

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Kayıt ekle'yi seçin.":::

1. Açılan listeden CNAME türünü seçin ve bu tablodaki değerleri yazın veya kopyalayıp yapıştırın.

    |Tür|Name|Hedef|TTL|
    |---|---|---|---|
    |CNAME|enterpriseregistration|enterpriseregistration.windows.net. <br/> **Bu değer nokta (.) ile bitmelidir.**|1 Saat|
    |CNAME|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com. <br/> **Bu değer nokta (.) ile bitmelidir.**|1 Saat|

1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Kaydet'i seçin.":::

1. Tablonun ikinci satırındaki değerleri kopyalayarak diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.
