---
title: GoDaddy'deki DNS kayıtlarınızı Microsoft 365'e bağlama
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
ms.custom:
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f40a9185-b6d5-4a80-bb31-aa3bb0cab48a
description: Microsoft için GoDaddy'de etki alanınızı doğrulamayı ve e-posta, Skype Kurumsal Online ve diğer hizmetler için DNS kayıtlarını ayarlamayı öğrenin.
ms.openlocfilehash: 150c97d8764247757e233934c5b2d8a3ea9f5b6c
ms.sourcegitcommit: 8cd230e243eba452b27f725d66152becb6aff49b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66563219"
---
# <a name="connect-your-dns-records-at-godaddy-to-microsoft-365"></a>GoDaddy'deki DNS kayıtlarınızı Microsoft 365'e bağlama

 **Aradığınızı bulamazsanız, [Etki Alanları SSS sayfasını denetleyin](../setup/domains-faq.yml)**.

DNS barındırma sağlayıcınız GoDaddy ise, bu makalede verilen adımları izleyerek etki alanınızı doğrulayın ve e-posta, Skype Kurumsal Çevrimiçi, vb. için DNS kayıtlarını ayarlayın.

## <a name="before-you-begin"></a>Başlamadan önce

Etki alanınız için DNS kayıtlarını ayarlamak için iki seçeneğiniz vardır:

- [**Domain Connect'i kullanma**](#use-domain-connect-to-verify-and-set-up-your-domain) Etki alanınızı başka bir e-posta hizmeti sağlayıcısıyla ayarlamadıysanız, yeni etki alanınızı otomatik olarak doğrulamak ve Microsoft 365 ile kullanmak üzere ayarlamak için Domain Connect adımlarını kullanın.

   VEYA

- [**El ile uygulanan adımları kullanma**](#create-dns-records-with-manual-setup) Aşağıdaki el ile uygulanan adımları kullanarak etki alanınızı doğrulayın ve etki alanı kayıt şirketinize ne zaman ve hangi kayıtların ekleneceğini seçin. Bu, yeni MX (posta) kayıtlarını( örneğin, uygun zamanda) ayarlamanıza olanak tanır.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Etki alanınızı doğrulamak ve ayarlamak için Domain Connect'i kullanma

Microsoft 365 ile GoDaddy etki alanınızı otomatik olarak doğrulamak ve ayarlamak için şu adımları izleyin:

1. Microsoft 365 yönetim merkezi **Ayarlar** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Etki Alanları'nı**</a> seçin ve ayarlamak istediğiniz etki alanını seçin.

1. Üç noktayı (diğer eylemler) seçin > **Kurulumu başlat'ı** seçin.

   :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. Etki alanınızı nasıl bağlamak istiyorsunuz? sayfasında **Devam'ı** seçin.

1. DNS kayıtları ekle sayfasında **DNS kayıtları ekle'yi** seçin.

1. GoDaddy oturum açma sayfasında hesabınızda oturum açın ve **Yetki ver'i** seçin.

   Bu işlem, Microsoft 365 için etki alanı kurulumunuzu tamamlar.

## <a name="create-dns-records-with-manual-setup"></a>El ile kurulum ile DNS kayıtları oluşturma

GoDaddy'de bu kayıtları ekledikten sonra, etki alanınız Microsoft hizmetleriyle çalışacak şekilde ayarlanır.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

### <a name="add-a-txt-record-for-verification"></a>Doğrulama için bir TXT kaydı ekleme

Etki alanınızı Microsoft ile kullanmadan önce, etki alanına sahip olduğunuzdan emin olmamız gerekir. Etki alanı kayıt şirketinizde hesabınızda oturum açıp DNS kaydını oluşturabilmek, Microsoft'a etki alanının sahibi olduğunuzu kanıtlar.

> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. Dilerseniz bu kaydı daha sonra silebilirsiniz.

1. Başlamak için [bu bağlantıyı](https://account.godaddy.com/products/?go_redirect=disabled) kullanarak GoDaddy'deki etki alanları sayfanıza gidin.

   Oturum açmanız istenirse oturum açma kimlik bilgilerinizi kullanın, sağ üstteki oturum açma adınızı ve ardından **Ürünlerim'i** seçin.

1. **Etki Alanları'nın** altında, doğrulamak istediğiniz etki alanının yanındaki üç noktayı seçin ve ardından **DNS'yi yönet'i** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Açılan listeden DNS'yi yönet'i seçin.":::

1. **Kayıtlar'ın** altında **EKLE'yi** seçin (aşağı kaydırmanız gerekebilir).

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="EKLE'yi seçin.":::

1. Açılan listeden **TXT'yi** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Tür açılan listesinde TXT'yi seçin.":::

1. Yeni kaydın kutularına tablodaki değerleri yazın veya kopyalayıp yapıştırın.

   |Tür|Ana Bilgisayar|TXT Değeri|TTL|
   |---|---|---|---|
   |TXT|@|MS=ms *XXXXXXXX*<br>**Not**: Bu bir örnektir. Burada, tablodan belirli **Hedef veya İşaret Edilen Adres** değerinizi kullanın. [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)|1 saat  <br>|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="TXT kaydının tablosundaki değerleri doldurun.":::

1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXTSave.png" alt-text="Kaydet'i seçin.":::

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

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Etki alanınız için e-postanın Microsoft'a gelmesi için bir MX kaydı ekleyin

1. Başlamak için [bu bağlantıyı](https://account.godaddy.com/products/?go_redirect=disabled) kullanarak GoDaddy'deki etki alanları sayfanıza gidin.

   Oturum açmanız istenirse oturum açma kimlik bilgilerinizi kullanın, sağ üstteki oturum açma adınızı ve ardından **Ürünlerim'i** seçin.

2. **Etki Alanları'nın** altında, doğrulamak istediğiniz etki alanının yanındaki üç noktayı seçin ve ardından **DNS'yi yönet'i** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Açılan listeden DNS'yi yönet'i seçin.":::

3. **Kayıtlar'ın** altında **EKLE'yi** seçin.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="EKLE'yi seçin.":::

4. Açılan listeden **MX'i** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Tür açılan listesindeN MX'i seçin.":::

5. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

   (Açılan listeden **Tür** ve **TTL** değerlerini seçin.)

   |Tür|Ana Bilgisayar|İşaret edilen|Öncelik|TTL|
   |---|---|---|---|---|
   |MX|@| *\<domain-key\>*.mail.protection.outlook.com  <br/> **Not:** Microsoft hesabınızdan alın *\<domain-key\>* . [How do I find this?](../get-help-with-domains/information-for-dns-records.md)|10  <br/> Öncelik hakkında daha fazla bilgi için bkz. [MX önceliği nedir?](../setup/domains-faq.yml)|1 saat|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="MX kaydının tablosundaki değerleri doldurun.":::

6. **Kaydet**'i seçin.

### <a name="add-the-cname-record-required-for-microsoft"></a>Microsoft için gereken CNAME kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://account.godaddy.com/products/?go_redirect=disabled) kullanarak GoDaddy'deki etki alanları sayfanıza gidin.

   Oturum açmanız istenirse oturum açma kimlik bilgilerinizi kullanın, sağ üstteki oturum açma adınızı ve ardından **Ürünlerim'i** seçin.

2. **Etki Alanları'nın** altında, doğrulamak istediğiniz etki alanının yanındaki üç noktayı seçin ve ardından **DNS'yi yönet'i** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Açılan listeden DNS'yi yönet'i seçin.":::

3. **Kayıtlar'ın** altında **EKLE'yi** seçin.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="EKLE'yi seçin.":::

4. Açılan listeden **CNAME'i** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Tür açılan listesindeN CNAME'yi seçin.":::

5. CNAME kaydını oluşturun.

   Yeni kayıt kutularına, aşağıdaki tablonun ilk satırındaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

   (Açılan listeden **TTL** değerini seçin.)

   |Tür|Ana Bilgisayar|İşaret edilen|TTL|
   |---|---|---|---|
   |CNAME|autodiscover|autodiscover.outlook.com|1 saat|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="CNAME kaydının tablosundaki değerleri doldurun.":::

6. **Kaydet**'i seçin.

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa, Microsoft için yeni bir tane oluşturmayın. Bunun yerine, her iki değer kümesini içeren  *tek*  bir SPF kaydına sahip olmak için gerekli Microsoft değerlerini geçerli kayda ekleyin.

1. Başlamak için [bu bağlantıyı](https://account.godaddy.com/products/?go_redirect=disabled) kullanarak GoDaddy'deki etki alanları sayfanıza gidin.

   Oturum açmanız istenirse oturum açma kimlik bilgilerinizi kullanın, sağ üstteki oturum açma adınızı ve ardından **Ürünlerim'i** seçin.

2. **Etki Alanları'nın** altında, doğrulamak istediğiniz etki alanının yanındaki üç noktayı seçin ve ardından **DNS'yi yönet'i** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Açılan listeden DNS'yi yönet'i seçin.":::

3. **Kayıtlar'ın** altında **EKLE'yi** seçin.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="EKLE'yi seçin.":::

4. Açılan listeden **TXT'yi** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Tür açılan listesinde TXT'yi seçin.":::

5. In the boxes for the new record, type or copy and paste the following values.

   (Açılan listelerden **TTL** değerini seçin.)

   |Tür|Ana Bilgisayar|TXT Değeri|TTL|
   |---|---|---|---|
   |TXT|@|v=spf1 include:spf.protection.outlook.com -all  <br/> **Not:** Tüm aralıkların doğru kalması için bu girdiyi kopyalayıp yapıştırmanızı öneririz.|1 saat|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="TXT kaydının tablosundaki değerleri doldurun.":::

6. **Kaydet**'i seçin.

## <a name="advanced-option-skype-for-business"></a>Gelişmiş seçenek: Skype Kurumsal

Bu seçeneği yalnızca kuruluşunuz Microsoft Teams'in yanı sıra sohbet, konferans aramaları ve görüntülü aramalar gibi çevrimiçi iletişim hizmetleri için Skype Kurumsal kullanıyorsa belirtin. Skype için 4 kayıt gerekir: Kullanıcıdan kullanıcıya iletişim için 2 SRV kaydı ve oturum açmak ve kullanıcıları hizmete bağlamak için 2 CNAME kaydı.

### <a name="add-the-two-required-srv-records"></a>Gerekli iki SRV kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://account.godaddy.com/products/?go_redirect=disabled) kullanarak GoDaddy'deki etki alanları sayfanıza gidin.

   Oturum açmanız istenirse oturum açma kimlik bilgilerinizi kullanın, sağ üstteki oturum açma adınızı ve ardından **Ürünlerim'i** seçin.

1. **Etki Alanları'nın** altında, doğrulamak istediğiniz etki alanının yanındaki üç noktayı seçin ve ardından **DNS'yi yönet'i** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Açılan listeden DNS'yi yönet'i seçin.":::

1. **Kayıtlar'ın** altında **EKLE'yi** seçin.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="EKLE'yi seçin.":::

1. Açılan listeden **SRV'yi** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Tür açılan listesindeN SRV'yi seçin.":::

1. İlk SRV kaydını oluşturun.

   Yeni kayıt kutularına, aşağıdaki tablonun ilk satırındaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

   (Açılan listelerden **Tür** ve **TTL** değerlerini seçin.)

   |Tür|Hizmet|Protokol|Name|Hedef|Öncelik|Ağırlık|Bağlantı noktası|TTL|
   |---|---|---|---|---|---|---|---|---|
   |SRV|_sip|_tls|@|sipdir.online.lync.com|100| 1|443|1 Saat|
   |SRV|_sipfederationtls|_tcp|@| sipfed.online.lync.com| 100|1|5061|1 Saat|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-SRV-values.png" alt-text="SRV kaydının tablosundaki değerleri doldurun.":::

1. **Kaydet**'i seçin.

1. Tablonun ikinci satırından değerleri seçerek diğer SRV kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Skype Kurumsal için gereken iki CNAME kaydını ekleme
  
1. Başlamak için [bu bağlantıyı](https://account.godaddy.com/products/?go_redirect=disabled) kullanarak GoDaddy'deki etki alanları sayfanıza gidin.

   Oturum açmanız istenirse oturum açma kimlik bilgilerinizi kullanın, sağ üstteki oturum açma adınızı ve ardından **Ürünlerim'i** seçin.

1. **Etki Alanları'nın** altında, doğrulamak istediğiniz etki alanının yanındaki üç noktayı seçin ve ardından **DNS'yi yönet'i** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Açılan listeden DNS'yi yönet'i seçin.":::

1. **Kayıtlar'ın** altında **EKLE'yi** seçin.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="EKLE'yi seçin.":::

1. Açılan listeden **CNAME'i** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Tür açılan listesindeN CNAME'yi seçin.":::

1. Yeni kayıtların boş kutularına, aşağıdaki tablonun ilk satırında yer alan değerleri yazın veya kopyalayıp yapıştırın.

   |Tür|Ana Bilgisayar|İşaret edilen|TTL|
   |---|---|---|---|
   |CNAME|sip|sipdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.**|1 Saat|
   |CNAME|lyncdiscover|webdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.**|1 Saat|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="CNAME kaydının tablosundaki değerleri doldurun.":::
  
1. **Kaydet**'i seçin.
  
1. Tablonun ikinci satırından değerleri seçerek diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Gelişmiş seçenek: Microsoft 365 için Intune ve Mobil Cihaz Yönetimi

Bu hizmet, etki alanınıza bağlanan mobil cihazları güvenli ve uzaktan yönetmenize yardımcı olur. Mobil Cihaz Yönetimi, kullanıcıların cihazları hizmete kaydedebilmesi için 2 CNAME kaydına ihtiyaç duyar.

### <a name="add-the-two-required-cname-records-mobile-device-management"></a>Mobil Cihaz Yönetimi gerekli iki CNAME kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://account.godaddy.com/products/?go_redirect=disabled) kullanarak GoDaddy'deki etki alanları sayfanıza gidin.

   Oturum açmanız istenirse oturum açma kimlik bilgilerinizi kullanın, sağ üstteki oturum açma adınızı ve ardından **Ürünlerim'i** seçin.

1. **Etki Alanları'nın** altında, doğrulamak istediğiniz etki alanının yanındaki üç noktayı seçin ve ardından **DNS'yi yönet'i** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Açılan listeden DNS'yi yönet'i seçin.":::

1. **Kayıtlar'ın** altında **EKLE'yi** seçin.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="EKLE'yi seçin.":::

1. Açılan listeden **CNAME'i** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Tür açılan listesindeN CNAME'yi seçin.":::

1. Yeni kayıtların boş kutularına, aşağıdaki tablonun ilk satırında yer alan değerleri yazın veya kopyalayıp yapıştırın.

   |Tür|Ana Bilgisayar|İşaret edilen|TTL|
   |---|---|---|---|
   |CNAME|enterpriseregistration|enterpriseregistration.windows.net.  <br/> **Bu değer nokta (.) ile bitmelidir.**|1 Saat|
   |CNAME|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com.  <br/> **Bu değer nokta (.) ile bitmelidir.**|1 Saat|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="CNAME kaydının tablosundaki değerleri doldurun.":::
  
1. **Kaydet**'i seçin.
  
1. Tablonun ikinci satırından değerleri seçerek diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.
