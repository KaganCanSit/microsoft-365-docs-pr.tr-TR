---
title: IONOS'ta 1&1'e kadar DNS kayıtlarınızı Microsoft 365'e bağlama
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
ms.assetid: 5762c3ca-1de2-4999-bfe5-4c5e25a8957e
description: Microsoft için 1&1 IONOS'ta etki alanınızı doğrulamayı ve e-posta, Skype Kurumsal Online ve diğer hizmetler için DNS kayıtlarını ayarlamayı öğrenin.
ms.openlocfilehash: b9d7474fe0c442670be961a5436558ea168626dc
ms.sourcegitcommit: 8cd230e243eba452b27f725d66152becb6aff49b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66563439"
---
# <a name="connect-your-dns-records-at-ionos-by-11-to-microsoft-365"></a>IONOS'ta 1&1'e kadar DNS kayıtlarınızı Microsoft 365'e bağlama

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**.

DNS barındırma sağlayıcınız 1&1 olan IONOS ise, etki alanınızı doğrulamak ve e-posta, Skype Kurumsal Çevrimiçi vb. için DNS kayıtlarını ayarlamak için bu makaledeki adımları izleyin.

## <a name="before-you-begin"></a>Başlamadan önce

Etki alanınız için DNS kayıtlarını ayarlamak için iki seçeneğiniz vardır:

- [**Domain Connect'i kullanma**](#use-domain-connect-to-verify-and-set-up-your-domain) Etki alanınızı başka bir e-posta hizmeti sağlayıcısıyla ayarlamadıysanız, yeni etki alanınızı otomatik olarak doğrulamak ve Microsoft 365 ile kullanmak üzere ayarlamak için Domain Connect adımlarını kullanın.

    VEYA

- [**El ile uygulanan adımları kullanma**](#create-dns-records-with-manual-setup) Aşağıdaki el ile uygulanan adımları kullanarak etki alanınızı doğrulayın ve etki alanı kayıt şirketinize ne zaman ve hangi kayıtların ekleneceğini seçin. Bu, yeni MX (posta) kayıtlarını( örneğin, uygun zamanda) ayarlamanıza olanak tanır.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Etki alanınızı doğrulamak ve ayarlamak için Domain Connect'i kullanma

Microsoft 365 ile IONOS'unuzu 1&1 etki alanına göre otomatik olarak doğrulamak ve ayarlamak için şu adımları izleyin:

1. Microsoft 365 yönetim merkezi **Ayarlar** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Etki Alanları'nı**</a> seçin ve ayarlamak istediğiniz etki alanını seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-1.png" alt-text="Microsoft 365'te etki alanınızı seçin.":::

1. Üç noktayı (diğer eylemler) seçin > **Kurulumu başlat'ı** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. Etki alanınızı nasıl bağlamak istiyorsunuz? sayfasında **Devam'ı** seçin.

1. DNS kayıtları ekle sayfasında **DNS kayıtları ekle'yi** seçin.

1. IONOS by 1&1 oturum açma sayfasında hesabınızda oturum açın ve **Bağlan** ve **İzin Ver'i** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-3.png" alt-text="Bağlan'ı ve ardından İzin Ver'i seçin.":::

    Bu işlem, Microsoft 365 için etki alanı kurulumunuzu tamamlar.

## <a name="create-dns-records-with-manual-setup"></a>El ile kurulum ile DNS kayıtları oluşturma

IONOS'ta 1&1'e kadar bu kayıtları ekledikten sonra, etki alanınız Microsoft hizmetleriyle çalışacak şekilde ayarlanır.

> [!CAUTION]
> IONOS'un 1&1'e kadar bir etki alanının hem MX kaydına hem de en üst düzey Autodiscover CNAME kaydına sahip olmasına izin vermediğini unutmayın. Bu, Microsoft için Exchange Online yapılandırma yöntemlerinizi sınırlar. Geçici bir çözüm vardır, ancak **yalnızca** IONOS'ta 1&1'e kadar alt etki alanları oluşturma deneyimine sahipseniz kullanmanızı öneririz.
> Bu [hizmet sınırlamasına](../setup/domains-faq.yml) rağmen IONOS'ta 1&1'e kadar kendi Microsoft DNS kayıtlarınızı yönetmeyi seçerseniz, bu makaledeki adımları izleyerek etki alanınızı doğrulayın ve e-posta, Skype Kurumsal Online vb. için DNS kayıtlarını ayarlayın.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışıyla veya diğer sorunlarla karşılaşıyorsanız, bkz. [Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-a-txt-record-for-verification"></a>Doğrulama için bir TXT kaydı ekleme

Etki alanınızı Microsoft ile kullanmadan önce, etki alanına sahip olduğunuzdan emin olmamız gerekir. Etki alanı kayıt şirketinizde hesabınızda oturum açıp DNS kaydını oluşturabilmek, Microsoft'a etki alanının sahibi olduğunuzu kanıtlar.

> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. Dilerseniz bu kaydı daha sonra silebilirsiniz.

1. Başlamak için [bu bağlantıyı](https://my.1and1.com/) kullanarak IONOS by 1&1'deki etki alanları sayfanıza gidin. Oturum açmanız istenir.

1. **Menü'yü** ve ardından **Etki Alanları ve SSL'yi** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Etki Alanları ve SSL'yi seçin.":::

1. Güncelleştirmek istediğiniz etki alanı için **eylemler'in** altında dişli denetimini ve ardından **DNS'yi** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Açılan listeden DNS'yi seçin.":::

1. **Kayıt ekle'yi** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Kayıt ekle'yi seçin.":::

1. **TXT** bölümünü seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-4.png" alt-text="TXT bölümünü seçin.":::

1. DNS kaydı ekle sayfasında, yeni kayıt kutularına aşağıdaki tabloda yer alan değerleri yazın veya kopyalayıp yapıştırın.

    |Ana bilgisayar adı|Değer|TTL|
    |---|---|---|
    |(Bu alanı boş bırakın)|MS=ms *XXXXXXXX*  <br/> NOT: Bu bir örnektir. Burada, tablodan belirli **Hedef veya İşaret Edilen Adres** değerinizi kullanın. [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)|1 saat|

1. **Kaydet**'i seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-5.png" alt-text="Kaydet'i seçin.":::

    Yeni oluşturduğunuz kaydın İnternet genelinde güncelleştirilebilmesi için devam etmeden önce birkaç dakika bekleyin.

Artık kaydı etki alanı kayıt şirketinizin sitesine eklediğinize göre, Microsoft 365'e geri dönüp Microsoft 365'in kaydı aramasını isteyebilirsiniz. Microsoft doğru TXT kaydını bulduğunda etki alanınız doğrulanır.

Microsoft 365'te kaydı doğrulamak için:

1. Yönetim merkezinde **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Etki Alanları'na**</a> gidin.

1. Etki Alanları sayfasında, doğrulamakta olduğunuz etki alanını seçin ve **kurulumu başlat'ı** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. **Devam**'ı seçin.

1. **Etki alanını doğrula** sayfasında **Doğrula'yı** seçin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Etki alanınız için e-postanın Microsoft'a gelmesi için bir MX kaydı ekleyin

> [!NOTE]
> 1und1.de kaydoldıysanız [burada oturum açın](https://go.microsoft.com/fwlink/?linkid=859152).

1. Başlamak için [bu bağlantıyı](https://my.1and1.com/) kullanarak IONOS by 1&1'deki etki alanları sayfanıza gidin. Oturum açmanız istenir.

1. **Menü'yü** ve ardından **Etki Alanları ve SSL'yi** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Etki Alanları ve SSL'yi seçin.":::

1. Güncelleştirmek istediğiniz etki alanı için **eylemler'in** altında dişli denetimini ve ardından **DNS'yi** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Açılan listeden DNS'yi seçin.":::

1. **Kayıt ekle'yi** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Kayıt ekle'yi seçin.":::

1. **MX** bölümünü seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-MX.png" alt-text="MX bölümünü seçin.":::

1. DNS kaydı ekle sayfasında, yeni kayıt kutularına aşağıdaki tabloda yer alan değerleri yazın veya kopyalayıp yapıştırın.

    |Ana bilgisayar adı|İşaret edilen|Öncelik|TTL|
    |---|---|---|---|
    |@|*\<domain-key\>*.mail.protection.outlook.com  <br/>  NOT: Microsoft hesabınızdan alın \<domain-key\> . [How do I find this?](../get-help-with-domains/information-for-dns-records.md)|10  <br/> Öncelik hakkında daha fazla bilgi için bkz. [MX önceliği nedir?](../setup/domains-faq.yml)|1 saat|

1. **Kaydet**'i seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-MX-Save.png" alt-text="Kaydet'i seçin.":::

1. Zaten listelenen MX kayıtları varsa, **Kayıt ekle** sayfasında **Kaydı sil** çöp kutusunu seçerek bunların her birini silin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Delete.png" alt-text="Kaydı sil'i seçin.":::

### <a name="add-the-cname-record-required-for-microsoft"></a>Microsoft için gereken CNAME kaydını ekleme

> [!NOTE]
> 1und1.de kaydoldıysanız [burada oturum açın](https://go.microsoft.com/fwlink/?linkid=859152).

1. Başlamak için [bu bağlantıyı](https://my.1and1.com/) kullanarak IONOS by 1&1'deki etki alanları sayfanıza gidin. Oturum açmanız istenir.

1. **Menü'yü** ve ardından **Etki Alanları ve SSL'yi** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Etki Alanları ve SSL'yi seçin.":::

1. Güncelleştirmek istediğiniz etki alanı için **eylemler'in** altında dişli denetimini ve ardından **DNS'yi** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Açılan listeden DNS'yi seçin.":::

   Şimdi iki alt etki alanı oluşturacak ve her birine **Diğer Ad** değeri ayarlayacaksınız.

   (1&1 IONOS yalnızca bir üst düzey CNAME kaydını desteklediği, ancak Microsoft'un birkaç CNAME kaydı gerektirdiği için bu gereklidir.)

   İlk olarak, Otomatik Bulma alt etki alanını oluşturacaksınız.

1. **Alt Etki Alanları'yı** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Alt Etki Alanı'yı seçin.":::

1. **Alt etki alanı ekle'yi** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Alt etki alanları ekle'yi seçin.":::

1. Yeni **alt etki alanı için Alt etki alanı ekle** kutusuna aşağıdaki tablodan yalnızca **Alt etki alanı ekle** değerini yazın veya kopyalayıp yapıştırın. ( **Diğer Ad** değerini sonraki adımlardan birinde ekleyeceksiniz.)

    |Alt etki alanı ekleme|Diğer ad|
    |---|---|
    |autodiscover|autodiscover.outlook.com|

1. Yeni oluşturduğunuz **otomatik bulma** alt etki alanı için **eylemler'in** altında dişli denetimini seçin ve ardından açılan listeden **DNS'yi** seçin.

1. **Kayıt ekle'yi** ve ardından **CNAME** bölümünü seçin.

1. **Diğer Ad:** kutusunda, yalnızca aşağıdaki tabloda verilen **Diğer Ad** değerini yazın veya kopyalayıp yapıştırın.

    |Alt etki alanı ekleme|Diğer ad|
    |---|---|
    |autodiscover|autodiscover.outlook.com|

1. **Kaydet**'i seçin.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa, Microsoft için yeni bir tane oluşturmayın. Bunun yerine, her iki değer kümesini içeren  *tek*  bir SPF kaydına sahip olmak için gerekli Microsoft değerlerini geçerli kayda ekleyin. Örneklere mi ihtiyacınız var? [Microsoft için bu Dış Etki Alanı Adı Sistemi kayıtlarına](../../enterprise/external-domain-name-system-records.md) göz atın. SPF kaydınızı doğrulamak için bu[SPF doğrulama araçlarından](../setup/domains-faq.yml) birini kullanabilirsiniz.

> [!NOTE]
> 1und1.de kaydoldıysanız [burada oturum açın](https://go.microsoft.com/fwlink/?linkid=859152).

1. Başlamak için [bu bağlantıyı](https://my.1and1.com/) kullanarak IONOS by 1&1'deki etki alanları sayfanıza gidin. Oturum açmanız istenir.

1. **Menü'yü** ve ardından **Etki Alanları ve SSL'yi** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Etki Alanları ve SSL'yi seçin.":::

1. Güncelleştirmek istediğiniz etki alanı için **eylemler'in** altında dişli denetimini ve ardından **DNS'yi** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Açılan listeden DNS'yi seçin.":::

1. **Kayıt ekle'yi** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Kayıt ekle'yi seçin.":::

1. **SPF (TXT)** bölümünü seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SPFTXT.png" alt-text="SPF (TXT) bölümünü seçin.":::

1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

    |Tür|Ana bilgisayar adı|Değer|TTL|
    |---|---|---|---|
    |SPF (TXT)|(Bu alanı boş bırakın.)|v=spf1 include:spf.protection.outlook.com -all  <br/> **Not:** Tüm aralıkların doğru kalması için bu girdiyi kopyalayıp yapıştırmanızı öneririz.|1 saat|

1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SPFTXT-Save.png" alt-text="Kaydet'i seçin.":::

## <a name="advanced-option-skype-for-business"></a>Gelişmiş seçenek: Skype Kurumsal

Bu seçeneği yalnızca kuruluşunuz Microsoft Teams'in yanı sıra sohbet, konferans aramaları ve görüntülü aramalar gibi çevrimiçi iletişim hizmetleri için Skype Kurumsal kullanıyorsa belirtin. Skype için 4 kayıt gerekir: Kullanıcıdan kullanıcıya iletişim için 2 SRV kaydı ve oturum açmak ve kullanıcıları hizmete bağlamak için 2 CNAME kaydı.

### <a name="add-two-additional-cname-records"></a>İki ek CNAME kaydı ekleme

1. Başlamak için [bu bağlantıyı](https://my.1and1.com/) kullanarak IONOS by 1&1'deki etki alanları sayfanıza gidin. Oturum açmanız istenir.

1. **Menü'yü** ve ardından **Etki Alanları ve SSL'yi** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Etki Alanları ve SSL'yi seçin.":::

1. Güncelleştirmek istediğiniz etki alanı için **eylemler'in** altında dişli denetimini ve ardından **DNS'yi** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Açılan listeden DNS'yi seçin.":::

   Şimdi iki alt etki alanı oluşturacak ve her birine **Diğer Ad** değeri ayarlayacaksınız.

   (1&1 IONOS yalnızca bir üst düzey CNAME kaydını desteklediği, ancak Microsoft'un birkaç CNAME kaydı gerektirdiği için bu gereklidir.)

   İlk olarak, lyncdiscover alt etki alanını oluşturacaksınız.

1. **Alt Etki Alanları'yı** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Alt Etki Alanı'yı seçin.":::

1. **Alt etki alanı ekle'yi** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Alt etki alanları ekle'yi seçin.":::

1. Yeni **alt etki alanı için Alt etki alanı ekle** kutusuna aşağıdaki tablodan yalnızca **Alt etki alanı ekle** değerini yazın veya kopyalayıp yapıştırın. ( **Diğer Ad** değerini sonraki adımlardan birinde ekleyeceksiniz.)

    |Alt etki alanı ekleme|Diğer ad|
    |---|---|
    |lyncdiscover   |webdir.online.lync.com  |

1. Yeni oluşturduğunuz **lyncdiscover** alt etki alanı için **eylemler'in** altında, dişli denetimini seçin ve ardından açılan listeden **DNS'yi** seçin.

1. **Kayıt ekle'yi** ve ardından **CNAME** bölümünü seçin.

1. **Diğer Ad:** kutusunda, yalnızca aşağıdaki tabloda verilen **Diğer Ad** değerini yazın veya kopyalayıp yapıştırın.

    |Alt Etki Alanı Oluştur|Diğer ad|
    |---|---|
    |lyncdiscover|webdir.online.lync.com|

1. Başka bir alt etki alanı (SIP) oluşturun: **Alt etki alanı ekle'yi** seçin.

1. Yeni **alt etki alanı için Alt etki alanı ekle** kutusuna aşağıdaki tablodan yalnızca **Alt etki alanı ekle** değerini yazın veya kopyalayıp yapıştırın. ( **Diğer Ad** değerini sonraki adımlardan birinde ekleyeceksiniz.)

    |Alt etki alanı ekleme|Diğer ad|
    |---|---|
    |sip|sipdir.online.lync.com|

1. Yeni oluşturduğunuz alt etki alanı için **eylemler'in** altında dişli denetimini seçin ve ardından açılan listeden **DNS'yi** seçin.

1. **Kayıt ekle'yi** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Kayıt ekle'yi seçin.":::

1. **CNAME** bölümünü seçin.

1. **Diğer Ad:** kutusunda, aşağıdaki tablodan yalnızca **Diğer Ad** değerini yazın veya kopyalayıp yapıştırın.

    |Alt Etki Alanı Oluştur|Diğer ad|
    |---|---|
    |sip|sipdir.online.lync.com|

1. **Farkındayım** bildiriminin onay kutusunu seçin ve ardından **Kaydet'i** seçin.

## <a name="add-the-two-srv-records-required-for-microsoft"></a>Microsoft için gereken iki SRV kaydını ekleme

> [!NOTE]
> 1und1.de kaydoldıysanız [burada oturum açın](https://go.microsoft.com/fwlink/?linkid=859152).

1. Başlamak için [bu bağlantıyı](https://my.1and1.com/) kullanarak IONOS by 1&1'deki etki alanları sayfanıza gidin. Oturum açmanız istenir.

1. **Menü'yü** ve ardından **Etki Alanları ve SSL'yi** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Etki Alanları ve SSL'yi seçin.":::

1. Güncelleştirmek istediğiniz etki alanı için **eylemler'in** altında dişli denetimini ve ardından **DNS'yi** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Açılan listeden DNS'yi seçin.":::

1. **Kayıt ekle'yi** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Kayıt ekle'yi seçin.":::

1. **SRV** bölümünü seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SRV.png" alt-text="SRV bölümünü seçin.":::

1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

    |Tür|Hizmet|Protokol|Ana bilgisayar adı|İşaret edilen|Öncelik|Ağırlık|Bağlantı noktası|TTL|
    |---|---|---|---|---|---|---|---|---|
    |SRV|_sip|tls|(Bu alanı boş bırakın.)|sipdir.online.lync.com|100|1|443|1 saat|
    |SRV|_sipfederationtls|tcp|(Bu alanı boş bırakın.)|sipfed.online.lync.com|100|1|5061|1 saat|

1. **Kaydet**'i seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SRV-Save.png" alt-text="Kaydet'i seçin.":::

1. Diğer SRV kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışıyla veya diğer sorunlarla karşılaşıyorsanız, bkz. [Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Gelişmiş seçenek: Microsoft 365 için Intune ve Mobil Cihaz Yönetimi

Bu hizmet, etki alanınıza bağlanan mobil cihazları güvenli ve uzaktan yönetmenize yardımcı olur. Mobil Cihaz Yönetimi, kullanıcıların cihazları hizmete kaydedebilmesi için 2 CNAME kaydına ihtiyaç duyar.

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydını ekleme

> [!IMPORTANT]
> Diğer CNAME kayıtları için kullandığınız alt etki alanı yordamını izleyin ve aşağıdaki tablodan değerleri sağlayın.

1. Başlamak için [bu bağlantıyı](https://my.1and1.com/) kullanarak IONOS by 1&1'deki etki alanları sayfanıza gidin. Oturum açmanız istenir.

1. **Menü'yü** ve ardından **Etki Alanları ve SSL'yi** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Etki Alanları ve SSL'yi seçin.":::

1. Güncelleştirmek istediğiniz etki alanı için **eylemler'in** altında dişli denetimini ve ardından **DNS'yi** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Açılan listeden DNS'yi seçin.":::

   Şimdi iki alt etki alanı oluşturacak ve her birine **Diğer Ad** değeri ayarlayacaksınız.

   (1&1 IONOS yalnızca bir üst düzey CNAME kaydını desteklediği, ancak Microsoft'un birkaç CNAME kaydı gerektirdiği için bu gereklidir.)

   İlk olarak, lyncdiscover alt etki alanını oluşturacaksınız.

1. **Alt Etki Alanları'yı** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Alt Etki Alanı'yı seçin.":::

1. **Alt etki alanı ekle'yi** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Alt etki alanları ekle'yi seçin.":::

1. Yeni **alt etki alanı için Alt etki alanı ekle** kutusuna aşağıdaki tablodan yalnızca **Alt etki alanı ekle** değerini yazın veya kopyalayıp yapıştırın. ( **Diğer Ad** değerini sonraki adımlardan birinde ekleyeceksiniz.)

    |Alt etki alanı ekleme|Diğer ad|
    |---|---|
    |enterpriseregistration|enterpriseregistration.windows.net|

1. Yeni oluşturduğunuz **enterpriseregistration** alt etki alanı için **eylemler'in** altında dişli denetimini seçin ve ardından açılan listeden **DNS'yi** seçin.

1. **Kayıt ekle'yi** ve ardından **CNAME** bölümünü seçin.

1. **Diğer Ad:** kutusunda, yalnızca aşağıdaki tabloda verilen **Diğer Ad** değerini yazın veya kopyalayıp yapıştırın.

    |Alt etki alanı ekleme|Diğer ad|
    |---|---|
    |enterpriseregistration|enterpriseregistration.windows.net|

1. Başka bir alt etki alanı oluşturun: **Alt etki alanı ekle'yi** seçin.

1. Yeni **alt etki alanı için Alt etki alanı ekle** kutusuna aşağıdaki tablodan yalnızca **Alt etki alanı ekle** değerini yazın veya kopyalayıp yapıştırın. ( **Diğer Ad** değerini sonraki adımlardan birinde ekleyeceksiniz.)

    |Alt etki alanı ekleme|Diğer ad|
    |---|---|
    |enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com|

1. Yeni oluşturduğunuz **enterpriseenrollment** alt etki alanı için **eylemler'in** altında dişli denetimini seçin ve ardından açılan listeden **DNS'yi** seçin.

1. **Kayıt ekle'yi** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Kayıt ekle'yi seçin.":::

1. **CNAME** bölümünü seçin.

1. **Diğer Ad:** kutusunda, aşağıdaki tablodan yalnızca **Diğer Ad** değerini yazın veya kopyalayıp yapıştırın.

    |Alt Etki Alanı Oluştur|Diğer ad|
    |---|---|
    |enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com|

1. **Farkındayım** bildiriminin onay kutusunu seçin ve ardından **Kaydet'i** seçin.
