---
title: Bağlan godaddy'de DNS kayıtlarınızı Microsoft 365
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
ms.custom:
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f40a9185-b6d5-4a80-bb31-aa3bb0cab48a
description: Microsoft için GoDaddy'de etki alanlarınızı doğrulamayı ve e-posta, Skype Kurumsal Online ve diğer hizmetler için DNS kayıtlarını ayarlamayı öğrenin.
ms.openlocfilehash: 728fd6cc34517213b338e3da07e6a275a1a727d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313559"
---
# <a name="connect-your-dns-records-at-godaddy-to-microsoft-365"></a>Bağlan godaddy'de DNS kayıtlarınızı Microsoft 365

 **Aradığınızı bulamazsanız, [Etki Alanları SSS sayfasını denetleyin](../setup/domains-faq.yml)**.

DNS barındırma sağlayıcınız GoDaddy ise, bu makalede verilen adımları izleyerek etki alanınızı doğrulayın ve e-posta, Skype Kurumsal Çevrimiçi, vb. için DNS kayıtlarını ayarlayın.

## <a name="before-you-begin"></a>Başlamadan önce

Etki alanınız için DNS kayıtlarını ayarlarken iki seçeneğiniz vardır:

- [**Etki Alanı Bağlan**](#use-domain-connect-to-verify-and-set-up-your-domain) Etki alanını başka bir e-posta hizmeti sağlayıcısıyla ayarlamadısanız, yeni etki alanınızı otomatik olarak doğrulamak ve yeni etki alanıyla birlikte kullanmak üzere ayarlamak için Etki alanı Bağlan adımlarını Microsoft 365.

   VEYA

- [**El ile adımları kullanma**](#create-dns-records-with-manual-setup) Aşağıdaki el ile adımları kullanarak etki alanınızı doğrulayın ve etki alanı kayıt şirketine eklemek istediğiniz kayıtların ne zaman ve hangi kayıtları seçeceklerini seçin. Bu sayede, örneğin size uygun bir şekilde yeni MX (posta) kayıtları ayarlanır.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Etki Bağlan doğrulamak ve ayarlamak için Etki Alanı Yöneticisi'ne

GoDaddy etki alanınızı otomatik olarak doğrulamak ve bu etki alanıyla ayarlamak için şu Microsoft 365:

1. Etki Microsoft 365 yönetim merkezi Etki **Ayarlar** >  seçin ve ardından ayarlamak istediğiniz etki alanını seçin.<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>

1. Üç noktayı (diğer eylemler) seçin ve **>'ı seçin**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. Etki alanınızı nasıl bağlamak istiyor musunuz? sayfasında **Devam'ı seçin**.

1. DNS kayıtları ekle sayfasında DNS kayıtları **ekle'yi seçin**.

1. GoDaddy oturum açma sayfasında, hesabınızla oturum açın ve Yetkilendir'i **seçin**.

    Bu, e-posta için etki alanı Microsoft 365.

## <a name="create-dns-records-with-manual-setup"></a>El ile kurulumla DNS kayıtları oluşturma

GoDaddy'ye bu kayıtları ekledikten sonra, etki alanınız Microsoft hizmetleri.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

### <a name="add-a-txt-record-for-verification"></a>Doğrulama için bir TXT kaydı ekleme

Etki alanınızı Microsoft ile kullanmadan önce bu etki alanına sahip olduğundan emin olarız. Etki alanı kayıt şirketinizin hesabında oturum açabilme ve DNS kaydı oluşturabilme özelliği, Microsoft'a etki alanının sahibi olduğunu kanıtlar.

> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. Dilerseniz bu kaydı daha sonra silebilirsiniz.

1. Başlamak için [bu bağlantıyı](https://account.godaddy.com/products/?go_redirect=disabled) kullanarak GoDaddy'deki etki alanları sayfanıza gidin.

   Oturum açmanız istenirse, oturum açma kimlik bilgilerinizi kullanın, sağ üst köşedeki oturum açma adı'nızı ve ardından **Ürünlerim'i seçin**.

1. Etki **Alanları'nın** altında, doğrulamak istediğiniz etki alanının yanındaki üç noktayı seçin ve sonra da **DNS'yi Yönet'i seçin**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::

1. **Kayıtlar'ın** altında **EKLE'yi** seçin (Aşağı kaydırmak zorunda olabilirsiniz).

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="EKLE'yi seçin.":::

1. Açılan **listeden TXT'yi** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Tür açılan listesinden TXT'yi seçin.":::

1. Yeni kayıt kutularına, tablodaki değerleri yazın veya kopyalayıp yapıştırın.

   |**Tür** |**Ana Bilgisayar**|**TXT Değeri**|**TTL** |
   |:-----|:-----|:-----|:-----|
   |TXT |@|MS=ms *XXXXXXXX*<br>**Not**: Bu bir örnektir. Tablodan **, belirli Hedef veya Adres Noktaları** değerinizi burada kullanın. [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)|1 saat  <br>|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="TXT kaydı için tablodan değerleri doldurun.":::

1. **Kaydet**'i seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXTSave.png" alt-text="Kaydet'i seçin.":::

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

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Etki alanınıza gelen e-postanın Microsoft'a göndernsin için MX kaydı ekleme

1. Başlamak için [bu bağlantıyı](https://account.godaddy.com/products/?go_redirect=disabled) kullanarak GoDaddy'deki etki alanları sayfanıza gidin.

   Oturum açmanız istenirse, oturum açma kimlik bilgilerinizi kullanın, sağ üst köşedeki oturum açma adı'nızı ve ardından **Ürünlerim'i seçin**.

2. Etki **Alanları'nın** altında, doğrulamak istediğiniz etki alanının yanındaki üç noktayı seçin ve sonra da **DNS'yi Yönet'i seçin**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::

3. **Kayıtlar'ın altında** **EKLE'yi seçin**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="EKLE'yi seçin.":::

4. Açılan **listeden MX'i** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Tür açılan listesinden MX'i seçin.":::

5. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

    (Tür **ve** **TTL** değerlerini açılan listeden seçin.)

    |**Tür**|**Ana Bilgisayar**|**Yönlendirme**|**Öncelik**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|
    |MX  <br/> |@  <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Not:** Microsoft hesabınızla  *\<domain-key\>*  oturum açın.           [How do I find this?](../get-help-with-domains/information-for-dns-records.md)          |10  <br/> Öncelik hakkında daha fazla bilgi için bkz. [MX önceliği nedir?](../setup/domains-faq.yml) <br/> |1 saat  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="MX kaydı için tablodan değerleri doldurun.":::

6. **Kaydet**'i seçin.

### <a name="add-the-cname-record-required-for-microsoft"></a>Microsoft için gereken CNAME kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://account.godaddy.com/products/?go_redirect=disabled) kullanarak GoDaddy'deki etki alanları sayfanıza gidin.

   Oturum açmanız istenirse, oturum açma kimlik bilgilerinizi kullanın, sağ üst köşedeki oturum açma adı'nızı ve ardından **Ürünlerim'i seçin**.

2. Etki **Alanları'nın** altında, doğrulamak istediğiniz etki alanının yanındaki üç noktayı seçin ve sonra da **DNS'yi Yönet'i seçin**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::

3. **Kayıtlar'ın altında** **EKLE'yi seçin**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="EKLE'yi seçin.":::

4. Açılan **listeden CNAME'yi** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Tür açılan listesinden CNAME'yi seçin.":::

5. CNAME kaydını oluşturun.

    Yeni kayıt kutularına, aşağıdaki tablonun ilk satırındaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

    (Açılan **listeden TTL** değerini seçin.)

    |**Tür**|**Ana Bilgisayar**|**Yönlendirme**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |autodiscover <br/> |autodiscover.outlook.com  <br/> |1 saat  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="CNAME kaydı için tablodan değerleri doldurun.":::

6. **Kaydet**'i seçin.

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa Microsoft için yeni bir SPF kaydı oluşturun. Bunun yerine, her iki değer kümesi de içeren tek  *bir SPF*  kaydına sahip olmak için gerekli Microsoft değerlerini geçerli kayda ekleyin.

1. Başlamak için [bu bağlantıyı](https://account.godaddy.com/products/?go_redirect=disabled) kullanarak GoDaddy'deki etki alanları sayfanıza gidin.

   Oturum açmanız istenirse, oturum açma kimlik bilgilerinizi kullanın, sağ üst köşedeki oturum açma adı'nızı ve ardından **Ürünlerim'i seçin**.

2. Etki **Alanları'nın** altında, doğrulamak istediğiniz etki alanının yanındaki üç noktayı seçin ve sonra da **DNS'yi Yönet'i seçin**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::

3. **Kayıtlar'ın altında** **EKLE'yi seçin**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="EKLE'yi seçin.":::

4. Açılan **listeden TXT'yi** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Tür açılan listesinden TXT'yi seçin.":::

5. In the boxes for the new record, type or copy and paste the following values.

    (Açılan **listelerden TTL** değerini seçin.)

    |**Tür**|**Ana Bilgisayar**|**TXT Değeri**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |TXT <br/> |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Not:** Tüm boşlukların doğru kalması için bu girdiyi kopyalayıp yapıştırarak bu dosyayı yapıştırın. |1 saat  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="TXT kaydı için tablodan değerleri doldurun.":::

6. **Kaydet**'i seçin.

## <a name="advanced-option-skype-for-business"></a>Gelişmiş seçenek: Skype Kurumsal

Yalnızca, bu seçeneği yalnızca, Skype Kurumsal yanı sıra sohbet, konferans aramaları ve görüntülü aramalar gibi çevrimiçi iletişim hizmetleri için Microsoft Teams. Skype için 4 kayıt gerekir: Oturum açma ve kullanıcıları hizmete bağlamak için 2 kullanıcı-kullanıcı iletişim için SRV kaydı ve 2 CNAME kaydı.

### <a name="add-the-two-required-srv-records"></a>Gerekli iki SRV kaydı ekleme

1. Başlamak için [bu bağlantıyı](https://account.godaddy.com/products/?go_redirect=disabled) kullanarak GoDaddy'deki etki alanları sayfanıza gidin.

   Oturum açmanız istenirse, oturum açma kimlik bilgilerinizi kullanın, sağ üst köşedeki oturum açma adı'nızı ve ardından **Ürünlerim'i seçin**.

1. Etki **Alanları'nın** altında, doğrulamak istediğiniz etki alanının yanındaki üç noktayı seçin ve sonra da **DNS'yi Yönet'i seçin**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::

1. **Kayıtlar'ın altında** **EKLE'yi seçin**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="EKLE'yi seçin.":::

1. Açılan **listeden SRV'yi** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Tür açılan listesinden SRV'yi seçin.":::

1. İlk SRV kaydını oluşturun.

    Yeni kayıt kutularına, aşağıdaki tablonun ilk satırındaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

    (Açılır **listelerden** **Tür ve TTL** değerlerini seçin.)

    |**Tür**|**Hizmet**|**Protokol**| **Ad** | **Hedef**|**Öncelik**|**Ağırlık**|**Bağlantı Noktası**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV   <br/> |_sip  <br/> |_tls  <br/> |@  <br/> |sipdir.online.lync.com  <br/> |100 <br/> | 1  <br/> |443  <br/> |1 Saat  <br/> |
    |SRV  <br/> |_sipfederationtls  <br/> |_tcp  <br/> |@  <br/> | sipfed.online.lync.com  <br/> | 100  <br/> |1  <br/> |5061  <br/> |1 Saat  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-SRV-values.png" alt-text="SRV kaydı için tablodan değerleri doldurun.":::

1. **Kaydet**'i seçin.

1. Tablonun ikinci satırdan değerleri seçerek diğer SRV kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydı ekleme
  
1. Başlamak için [bu bağlantıyı](https://account.godaddy.com/products/?go_redirect=disabled) kullanarak GoDaddy'deki etki alanları sayfanıza gidin.

   Oturum açmanız istenirse, oturum açma kimlik bilgilerinizi kullanın, sağ üst köşedeki oturum açma adı'nızı ve ardından **Ürünlerim'i seçin**.

2. Etki **Alanları'nın** altında, doğrulamak istediğiniz etki alanının yanındaki üç noktayı seçin ve sonra da **DNS'yi Yönet'i seçin**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::

1. **Kayıtlar'ın altında** **EKLE'yi seçin**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="EKLE'yi seçin.":::

1. Açılan **listeden CNAME'yi** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Tür açılan listesinden CNAME'yi seçin.":::

1. Yeni kayıtların boş kutularına, aşağıdaki tablonun ilk satırdaki değerleri yazın veya kopyalayıp yapıştırın.

    |**Tür**|**Ana Bilgisayar**|**Yönlendirme**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |1 Saat  <br/> |
    |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |1 Saat  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="CNAME kaydı için tablodan değerleri doldurun.":::
  
1. **Kaydet**'i seçin.
  
1. Tablonun ikinci satırdan değerleri seçerek diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Gelişmiş seçenek: Mobil Cihazlar için Intune ve Mobil Microsoft 365

Bu hizmet, etki alanınıza bağlı mobil cihazların güvenliğini sağlamanıza ve uzaktan yönetmenize yardımcı olur. Mobil Cihaz Yönetimi'nin, kullanıcıların cihazları hizmete kaydedeni için 2 CNAME kaydı olması gerekir.

### <a name="add-the-two-required-cname-records"></a>Gerekli iki CNAME kaydı ekleme

1. Başlamak için [bu bağlantıyı](https://account.godaddy.com/products/?go_redirect=disabled) kullanarak GoDaddy'deki etki alanları sayfanıza gidin.

   Oturum açmanız istenirse, oturum açma kimlik bilgilerinizi kullanın, sağ üst köşedeki oturum açma adı'nızı ve ardından **Ürünlerim'i seçin**.

1. Etki **Alanları'nın** altında, doğrulamak istediğiniz etki alanının yanındaki üç noktayı seçin ve sonra da **DNS'yi Yönet'i seçin**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Açılan listeden DNS'yi Yönet'i seçin.":::

1. **Kayıtlar'ın altında** **EKLE'yi seçin**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="EKLE'yi seçin.":::

1. Açılan **listeden CNAME'yi** seçin.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Tür açılan listesinden CNAME'yi seçin.":::

1. Yeni kayıtların boş kutularına, aşağıdaki tablonun ilk satırdaki değerleri yazın veya kopyalayıp yapıştırın.

    |**Tür**|**Ana Bilgisayar**|**Yönlendirme**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |1 Saat  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Bu değer nokta (.) ile bitmelidir.** <br/> |1 Saat  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="CNAME kaydı için tablodan değerleri doldurun.":::
  
1. **Kaydet**'i seçin.
  
1. Tablonun ikinci satırdan değerleri seçerek diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.
