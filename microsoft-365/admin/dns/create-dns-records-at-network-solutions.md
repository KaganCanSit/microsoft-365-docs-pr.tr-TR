---
title: Ağ Çözümleri'ndeki DNS kayıtlarınızı Microsoft 365'e bağlama
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
ms.assetid: 1dc55f9f-5309-450f-acc3-b2b4119c8be3
description: Etki alanınızı doğrulamayı ve e-posta, Skype Kurumsal Online ve diğer hizmetler için DNS kayıtlarını ayarlamayı Microsoft için Ağ Çözümleri sayfasından öğrenin.
ms.openlocfilehash: 6ebe81c17d02c0cc6126f75f3b6471e01a334db4
ms.sourcegitcommit: 8cd230e243eba452b27f725d66152becb6aff49b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66563285"
---
# <a name="connect-your-dns-records-at-network-solutions-to-microsoft-365"></a>Ağ Çözümleri'ndeki DNS kayıtlarınızı Microsoft 365'e bağlama

 **Aradığınızı bulamazsanız, [Etki Alanları SSS sayfasını denetleyin](../setup/domains-faq.yml)**.

DNS barındırma sağlayıcınız Network Solutions ise, bu makalede verilen adımları izleyerek etki alanınızı doğrulayın ve e-posta, Skype Kurumsal Çevrimiçi, vb. için DNS kayıtlarını ayarlayın.

Bu kayıtları Network Solutions'a ekledikten sonra, etki alanınız Microsoft hizmetleriyle çalışacak şekilde ayarlanır.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

## <a name="add-a-txt-record-for-verification"></a>Doğrulama için bir TXT kaydı ekleme

Etki alanınızı Microsoft ile kullanmadan önce, etki alanına sahip olduğunuzdan emin olmamız gerekir. Etki alanı kayıt şirketinizde hesabınızda oturum açıp DNS kaydını oluşturabilmek, Microsoft'a etki alanının sahibi olduğunuzu kanıtlar.

> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. Dilerseniz bu kaydı daha sonra silebilirsiniz.

1. Başlamak için, [bu bağlantıyı](https://www.networksolutions.com/manage-it) kullanarak Network Solutions'daki etki alanları sayfanıza gidin. Oturum açmanız istenir.

1. Giriş sayfasında **Etki Alanı Adları'nı** seçin.

1. Değiştirmek istediğiniz etki alanının yanındaki onay kutusunu seçin.

1. **Eylemler'in** altında üç noktayı seçin ve ardından açılan **listeden Yönet'i** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. **Gelişmiş Araçlar'ı** seçmek için ekranı aşağı kaydırın ve **Gelişmiş DNS Kayıtları'nın** yanında **YÖNET'i** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Gelişmiş DNS kayıtları'nın yanında YÖNET'i seçin.":::

   Gelişmiş DNS Kayıtlarını Yönet sayfasına ulaşmak için **Devam'ı** seçmeniz gerekebilir.

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında **+KAYIT EKLE'yi** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="+KAYIT EKLE'yi seçin.":::

1. **Tür** altında, açılan listeden **TXT'yi** seçin.

1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

   |Başvuruda bulunan|TXT Değeri|TTL|
   |---|---|---|
   |@  <br/> (Kaydı kaydettiğinizde, sistem bu değeri **@ (None)** olarak değiştirir.)|MS=ms *XXXXXXXX*  <br/> **Not:** Bu bir örnektir. Burada, tablodan belirli **Hedef veya İşaret Edilen Adres** değerinizi kullanın.  [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)|3600|

1. **EKLE'yi** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add.png" alt-text="EKLE'yi seçin.":::

   > [!NOTE]
   > Oluşturduğunuz TXT kaydını görüntülemek için sağ üstteki **Klasik Görünüm'ü** seçin.

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

1. Başlamak için, [bu bağlantıyı](https://www.networksolutions.com/manage-it) kullanarak Network Solutions'daki etki alanları sayfanıza gidin. Oturum açmanız istenir.

1. Giriş sayfasında **Etki Alanı Adları'nı** seçin.

1. Değiştirmek istediğiniz etki alanının yanındaki onay kutusunu seçin.

1. **Eylemler'in** altında üç noktayı seçin ve ardından açılan listede **Yönet'i** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. **Gelişmiş Araçlar'ı** seçmek için ekranı aşağı kaydırın ve **Gelişmiş DNS Kayıtları'nın** yanında **YÖNET'i** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Gelişmiş DNS kayıtları'nın yanında YÖNET'i seçin.":::

   Gelişmiş DNS Kayıtlarını Yönet sayfasına ulaşmak için **Devam'ı** seçmeniz gerekebilir.

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında **+KAYIT EKLE'yi** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="+KAYIT EKLE'yi seçin.":::

1. **Tür** altında, açılan listeden **MX'i** seçin.

1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın.

   |Başvuruda bulunan|Posta sunucusu|Öncelik|TTL|
   |---|---|---|---|
   |@|*\<domain-key\>*.mail.protection.outlook.com  <br/> **Bu değer nokta (.) ile bitemez** <br/> **Not:** Microsoft hesabınızdan alın *\<domain-key\>* . [How do I find this?](../get-help-with-domains/information-for-dns-records.md)|0  <br/> Öncelik hakkında daha fazla bilgi için bkz. [MX önceliği nedir?](../setup/domains-faq.yml)|1 Saat|

1. **EKLE'yi** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-MX-add.png" alt-text="EKLE'yi seçin.":::

   > [!NOTE]
   > Oluşturduğunuz TXT kaydını görüntülemek için sağ üstteki **Klasik Görünüm'ü** seçin.

1. Başka MX kayıtları varsa, düzenleme aracını seçip her kayıt için **Sil'i** seçerek bunların tümünü silin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-edit.png" alt-text="Düzenle aracını seçin.":::

## <a name="add-the-cname-record-required-for-microsoft"></a>Microsoft için gereken CNAME kaydını ekleme

1. Başlamak için, [bu bağlantıyı](https://www.networksolutions.com/manage-it) kullanarak Network Solutions'daki etki alanları sayfanıza gidin. Oturum açmanız istenir.

1. Giriş sayfasında **Etki Alanı Adları'nı** seçin.

1. Değiştirmek istediğiniz etki alanının yanındaki onay kutusunu seçin.

1. **Eylemler'in** altında üç noktayı seçin ve ardından açılan listede **Yönet'i** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. **Gelişmiş Araçlar'ı** seçin ve **Gelişmiş DNS Kayıtları'nın** yanında **YÖNET'i** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Gelişmiş DNS kayıtları'nın yanında YÖNET'i seçin.":::

   Gelişmiş DNS Kayıtlarını Yönet sayfasına ulaşmak için **Devam'ı** seçmeniz gerekebilir.

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında **+KAYIT EKLE'yi** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="+KAYIT EKLE'yi seçin.":::

1. **Tür** altında, açılan listeden **CNAME'i** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname.png" alt-text="Açılan listeden CNAME türü'nü seçin.":::

1. CNAME kaydının kutularına aşağıdaki tabloda yer alan değerleri yazın veya kopyalayıp yapıştırın.

   |Başvuruda bulunan|Ana Bilgisayar Adı|Diğer Ad|TTL|
   |---|---|---|---|
   |Diğer Konak|autodiscover|autodiscover.outlook.com **Bu değer nokta (.) ile sona eremez** <br/> 1 Saat|

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname-values.png" alt-text="Tablodaki CNAME değerlerini yazın veya kopyalayıp pencereye yapıştırın.":::

1. **EKLE'yi** seçin.

   > [!NOTE]
   > Oluşturduğunuz kaydı görüntülemek için sağ üstteki **Klasik Görünüm'ü** seçin.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa, Microsoft için yeni bir tane oluşturmayın. Bunun yerine, her iki değer kümesini içeren  *tek*  bir SPF kaydına sahip olmak için gerekli Microsoft değerlerini geçerli kayda ekleyin.

1. Başlamak için, [bu bağlantıyı](https://www.networksolutions.com/manage-it) kullanarak Network Solutions'daki etki alanları sayfanıza gidin. Oturum açmanız istenir.

1. Giriş sayfasında **Etki Alanı Adları'nı** seçin.

1. Değiştirmek istediğiniz etki alanının yanındaki onay kutusunu seçin.

1. **Eylemler'in** altında üç noktayı seçin ve ardından açılan listede **Yönet'i** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. **Gelişmiş Araçlar'ı** seçin ve **Gelişmiş DNS Kayıtları'nın** yanında **YÖNET'i** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Gelişmiş DNS kayıtları'nın yanında YÖNET'i seçin.":::

   Gelişmiş DNS Kayıtlarını Yönet sayfasına ulaşmak için **Devam'ı** seçmeniz gerekebilir.

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında **+KAYIT EKLE'yi** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="+KAYIT EKLE'yi seçin.":::

1. **Tür** altında, açılan listeden **TXT'yi** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-TXT.png" alt-text="Tür açılan listesinde TXT'yi seçin.":::

1. In the boxes for the new record, type or copy and paste the following values.

   |Başvuruda bulunan|TXT Değeri|TTL
   |---|---|---|
   |@  <br/> (Kaydı kaydettiğinizde, sistem bu değeri **@ (None)** olarak değiştirir.)|v=spf1 include:spf.protection.outlook.com -all  <br/> **Not:** Tüm aralıkların doğru kalması için bu girdiyi kopyalayıp yapıştırmanızı öneririz.|1 Saat|

1. **EKLE'yi** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add.png" alt-text="EKLE'yi seçin.":::

   > [!NOTE]
   > Oluşturduğunuz kaydı görüntülemek için sağ üstteki **Klasik Görünüm'ü** seçin.

## <a name="advanced-option-skype-for-business"></a>Gelişmiş seçenek: Skype Kurumsal

Bu seçeneği yalnızca kuruluşunuz Microsoft Teams'in yanı sıra sohbet, konferans aramaları ve görüntülü aramalar gibi çevrimiçi iletişim hizmetleri için Skype Kurumsal kullanıyorsa belirtin. Skype için 4 kayıt gerekir: Kullanıcıdan kullanıcıya iletişim için 2 SRV kaydı ve oturum açmak ve kullanıcıları hizmete bağlamak için 2 CNAME kaydı.

### <a name="add-the-two-required-srv-records"></a>Gerekli iki SRV kaydını ekleme

1. Başlamak için, [bu bağlantıyı](https://www.networksolutions.com/manage-it) kullanarak Network Solutions'daki etki alanları sayfanıza gidin. Oturum açmanız istenir.

1. Giriş sayfasında **Etki Alanı Adları'nı** seçin.

1. Değiştirmek istediğiniz etki alanının yanındaki onay kutusunu seçin.

1. **Eylemler'in** altında üç noktayı seçin ve ardından açılan listede **Yönet'i** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. **Gelişmiş Araçlar'ı** seçin ve **Gelişmiş DNS Kayıtları'nın** yanında **YÖNET'i** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Gelişmiş DNS kayıtları'nın yanında YÖNET'i seçin.":::

   Gelişmiş DNS Kayıtlarını Yönet sayfasına ulaşmak için **Devam'ı** seçmeniz gerekebilir.

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında **+KAYIT EKLE'yi** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="+KAYIT EKLE'yi seçin.":::

1. **Tür'ün** altında, açılan listeden **SRV'yi** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-srv.png" alt-text="Tür açılan listesindeN SRV'yi seçin.":::

1. İki yeni kaydın kutularına, aşağıdaki tablodaki değerleri yazın veya kopyalayıp yapıştırın.

   (Açılan listelerden **Hizmet** ve **Protokol** değerlerini seçin.)

   |Tür|Hizmet|Protokol|Ağırlık|Bağlantı noktası|Hedef|Öncelik|TTL|
   |---|---|---|---|---|---|---|---|
   |SRV|_sip|TLS|100|443|sipdir.online.lync.com  <br/> **Bu değer nokta (.) ile bitemez**|1|1 Saat|
   |SRV|_sipfederationtls|TCP|100|5061|sipfed.online.lync.com  <br/> **Bu değer nokta (.) ile bitemez**|1|1 Saat|

1. **EKLE'yi** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-srv-add.png" alt-text="EKLE'yi seçin.":::

   > [!NOTE]
   > Oluşturduğunuz kaydı görüntülemek için sağ üstteki **Klasik Görünüm'ü** seçin.

1. Tablonun ikinci satırındaki değerleri kopyalayarak diğer SRV kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışıyla veya diğer sorunlarla karşılaşıyorsanız, bkz. [Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Skype Kurumsal için gereken iki CNAME kaydını ekleme

1. Başlamak için, [bu bağlantıyı](https://www.networksolutions.com/manage-it) kullanarak Network Solutions'daki etki alanları sayfanıza gidin. Oturum açmanız istenir.

1. Giriş sayfasında **Etki Alanı Adları'nı** seçin.

1. Değiştirmek istediğiniz etki alanının yanındaki onay kutusunu seçin.

1. **Eylemler'in** altında üç noktayı seçin ve ardından açılan listede **Yönet'i** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. **Gelişmiş Araçlar'ı** seçin ve **Gelişmiş DNS Kayıtları'nın** yanında **YÖNET'i** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Gelişmiş DNS kayıtları'nın yanında YÖNET'i seçin.":::

   Gelişmiş DNS Kayıtlarını Yönet sayfasına ulaşmak için **Devam'ı** seçmeniz gerekebilir.

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında **+ KAYıT EKLE'yi** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="+KAYIT EKLE'yi seçin.":::

1. **Tür** altında, açılan listeden **CNAME'i** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname.png" alt-text="Açılan listeden CNAME türü'nü seçin.":::

1. CNAME kaydının kutularına aşağıdaki tabloda yer alan değerleri yazın veya kopyalayıp yapıştırın.

   |Tür|Başvuruda bulunan|Ana Bilgisayar Adı|Diğer Ad|TTL|
   |---|---|---|---|---|
   |CNAME|Diğer Konak|sip|sipdir.online.lync.com  <br/> **Bu değer nokta (.) ile bitemez**|1 Saat|
   |CNAME|Diğer Konak|lyncdiscover|webdir.online.lync.com  <br/> **Bu değer nokta (.) ile bitemez**|1 Saat|

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname-values.png" alt-text="Tablodaki CNAME değerlerini yazın veya kopyalayıp pencereye yapıştırın.":::

1. **EKLE'yi** seçin.

   > [!NOTE]
   > Oluşturduğunuz kaydı görüntülemek için sağ üstteki **Klasik Görünüm'ü** seçin.

1. Tablonun ikinci satırındaki değerleri kopyalayarak diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Gelişmiş seçenek: Microsoft 365 için Intune ve Mobil Cihaz Yönetimi

Bu hizmet, etki alanınıza bağlanan mobil cihazları güvenli ve uzaktan yönetmenize yardımcı olur. Mobil Cihaz Yönetimi, kullanıcıların cihazları hizmete kaydedebilmesi için 2 CNAME kaydına ihtiyaç duyar.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Mobile Cihaz Yönetimi için gereken iki CNAME kaydını ekleme

1. Başlamak için, [bu bağlantıyı](https://www.networksolutions.com/manage-it) kullanarak Network Solutions'daki etki alanları sayfanıza gidin. Oturum açmanız istenir.

1. Giriş sayfasında **Etki Alanı Adları'nı** seçin.

1. Değiştirmek istediğiniz etki alanının yanındaki onay kutusunu seçin.

1. **Eylemler'in** altında üç noktayı seçin ve ardından açılan listede **Yönet'i** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Açılan listeden Yönet'i seçin.":::

1. **Gelişmiş Araçlar'ı** seçin ve **Gelişmiş DNS Kayıtları'nın** yanında **YÖNET'i** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Gelişmiş DNS kayıtları'nın yanında YÖNET'i seçin.":::

   Gelişmiş DNS Kayıtlarını Yönet sayfasına ulaşmak için **Devam'ı** seçmeniz gerekebilir.

1. Gelişmiş DNS Kayıtlarını Yönet sayfasında **+KAYIT EKLE'yi** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="+KAYIT EKLE'yi seçin.":::

1. **Tür** altında, açılan listeden **CNAME'i** seçin.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname.png" alt-text="Açılan listeden CNAME türü'nü seçin.":::

1. CNAME kaydının kutularına aşağıdaki tabloda yer alan değerleri yazın veya kopyalayıp yapıştırın.

   |Tür|Başvuruda bulunan|Ana Bilgisayar Adı|Diğer Ad|TTL|
   |---|---|---|---|---|
   |CNAME|Diğer Konak|enterpriseregistration|enterpriseregistration.windows.net  <br/> **Bu değer nokta (.) ile bitemez**|1 Saat|
   |CNAME|Diğer Konak|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com  <br/> **Bu değer nokta (.) ile bitemez**|1 Saat|

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname-values.png" alt-text="Tablodaki CNAME değerlerini yazın veya kopyalayıp pencereye yapıştırın.":::

1. **EKLE'yi** seçin.

   > [!NOTE]
   > Oluşturduğunuz kaydı görüntülemek için sağ üstteki **Klasik Görünüm'ü** seçin.

1. Tablonun ikinci satırındaki değerleri kopyalayarak diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

