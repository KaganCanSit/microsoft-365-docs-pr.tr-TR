---
title: OVH'deki DNS kayıtlarınızı Microsoft 365'e bağlama
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
ms.assetid: 5176feef-36dc-4d84-842f-1f2b5a21ba96
description: Microsoft için OVH'de etki alanınızı doğrulamayı ve e-posta, Skype Kurumsal Online ve diğer hizmetler için DNS kayıtlarını ayarlamayı öğrenin.
ms.openlocfilehash: 2f30199f2868aa4b0097186009ac5f9bcb75abce
ms.sourcegitcommit: 8cd230e243eba452b27f725d66152becb6aff49b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66563307"
---
# <a name="connect-your-dns-records-at-ovh-to-microsoft-365"></a>OVH'deki DNS kayıtlarınızı Microsoft 365'e bağlama

Aradığınızı bulamazsanız, [Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml).

DNS barındırma sağlayıcınız OVH ise, etki alanınızı doğrulamak ve e-posta, Skype Kurumsal Online vb. için DNS kayıtlarını ayarlamak için bu makaledeki adımları izleyin.

OVH'de bu kayıtları ekledikten sonra, etki alanınız Microsoft hizmetleriyle çalışacak şekilde ayarlanır.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

## <a name="add-a-txt-record-for-verification"></a>Doğrulama için bir TXT kaydı ekleme

Etki alanınızı Microsoft ile kullanmadan önce, etki alanına sahip olduğunuzdan emin olmamız gerekir. Etki alanı kayıt şirketinizde hesabınızda oturum açıp DNS kaydını oluşturabilmek, Microsoft'a etki alanının sahibi olduğunuzu kanıtlar.

> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. Dilerseniz bu kaydı daha sonra silebilirsiniz.

1. Başlamak için [bu bağlantıyı](https://www.ovh.com/manager/) kullanarak OVH'deki etki alanları sayfanıza gidin. Oturum açmanız istenir.

    ![OVH oturum açma.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Pano giriş sayfasındaki **Tüm etkinliğimi görüntüle'nin** altında, düzenlemek istediğiniz etki alanının adını seçin.

1. **DNS bölgesi'ne tıklayın**.

    ![OVH DNS bölgesini seçin.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. **Giriş ekle'yi** seçin.

    ![OVH Bir girdi ekleyin.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. **TXT'yi** seçin

    ![OVH, TXT girdisini seçin.](../../media/3aaa9dae-0b1d-436b-a980-b67a970f31a9.png)

1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın. TTL değeri atamak için, açılan listeden **Özel'i** seçin ve metin kutusuna değeri yazın.

   |Kayıt türü|Alt etki alanı|TTL|Değer|
   |---|---|---|---|
   |TXT|(boş bırakın)|3600 (saniye)|MS=msxxxxxxxxx  <br/> **Not:** Bu bir örnektir. Burada, tablodan belirli **Hedef veya İşaret Edilen Adres** değerinizi kullanın.  [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)|

1. **İleri**'yi seçin.

1. **Onayla'yı** seçin.

    ![OVH doğrulama için TXT'ye onaylayın.](../../media/bde45596-9a55-4634-b5e7-16d7cde6e1b8.png)

1. Yeni oluşturduğunuz kaydın İnternet genelinde güncelleştirilebilmesi için devam etmeden önce birkaç dakika bekleyin.

Artık kaydı etki alanı kayıt şirketinizin sitesine eklediğinize göre, Microsoft'a geri dönüp kaydı istemeniz gerekir. Microsoft doğru TXT kaydını bulduğunda etki alanınız doğrulanır.

Microsoft 365'te kaydı doğrulamak için:

1. Yönetim merkezinde **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Etki Alanları'na**</a> gidin.

1. Etki Alanları sayfasında, doğrulamakta olduğunuz etki alanını seçin ve **kurulumu başlat'ı** seçin.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Kurulumu başlat'ı seçin.":::

1. **Devam**'ı seçin.

1. **Etki alanını doğrula** sayfasında **Doğrula'yı** seçin.

> [!NOTE]
>  Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Etki alanınız için e-postanın Microsoft'a gelmesi için bir MX kaydı ekleyin

1. Başlamak için [bu bağlantıyı](https://www.ovh.com/manager/) kullanarak OVH'deki etki alanları sayfanıza gidin. Oturum açmanız istenir.

    ![OVH oturum açma.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Pano giriş sayfasındaki **Tüm etkinliğimi görüntüle'nin** altında, düzenlemek istediğiniz etki alanının adını seçin.

1. **DNS bölgesi'ne tıklayın**.

    ![OVH DNS bölgesini seçin.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. **Giriş ekle'yi** seçin.

    ![OVH Bir girdi ekleyin.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. **MX'i** seçin.

    ![OVH MX kayıt türü.](../../media/29b5e54e-440a-41f2-9eb9-3de573922ddf.png)

1. Yeni kayıt kutularına, aşağıdaki tablodaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın. TTL değeri atamak için, açılan listeden **Özel'i** seçin ve metin kutusuna değeri yazın.

    > [!NOTE]
    > Varsayılan olarak OVH, hedef için göreli gösterimi kullanır ve bu da etki alanı adını hedef kaydın sonuna ekler. Bunun yerine mutlak gösterimi kullanmak için, aşağıdaki tabloda gösterildiği gibi hedef kayda bir nokta ekleyin.

   |Alt etki alanı|TTL|Öncelik|Hedef|
   |---|---|---|---|
   |(boş bırakın)|3600 (saniye)|0  <br/> Öncelik hakkında daha fazla bilgi için bkz. [MX önceliği nedir?](../setup/domains-faq.yml)|\<domain-key\>.mail.protection.outlook.com.  <br/> **Not:** Microsoft hesabınızdan alın *\<domain-key\>* . [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)|

    ![Posta için OVH MX kaydı.](../../media/6e2f5655-93e2-4620-8f19-c452e7edf8f0.png)

1. **İleri**'yi seçin.

    ![OVH MX kaydı İleri'yi seçin.](../../media/4db62d07-0dc4-49f6-bd19-2b4a07fd764a.png)

1. **Onayla'yı** seçin.

    ![OVH MX kaydı Onayla'yı seçin.](../../media/090bfb11-a753-4af0-8982-582a4069a169.png)

1. **DNS bölgesi** sayfasındaki listedeki diğer MX kayıtlarını silin. Her kaydı seçin ve **Eylemler** sütununda çöp kutusu **Sil** simgesini seçin.

    ![OVH, MX kaydını siler.](../../media/892b328b-7057-4828-b8c5-fe26284dc8c2.png)

1. **Onayla'yı** seçin.

## <a name="add-the-cname-record-required-for-microsoft"></a>Microsoft için gereken CNAME kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://www.ovh.com/manager/) kullanarak OVH'deki etki alanları sayfanıza gidin. Oturum açmanız istenir.

    ![OVH oturum açma.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Pano giriş sayfasındaki **Tüm etkinliğimi görüntüle'nin** altında, düzenlemek istediğiniz etki alanının adını seçin.

1. **DNS bölgesi'ne tıklayın**.

    ![OVH DNS bölgesini seçin.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. **Giriş ekle'yi** seçin.

    ![OVH Bir girdi ekleyin.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. **CNAME'i** seçin.

    ![OVH CNAME kayıt türü ekleyin.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. Yeni kayıt kutularına, aşağıdaki tablonun ilk satırındaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın. TTL değeri atamak için, açılan listeden **Özel'i** seçin ve metin kutusuna değeri yazın.

   |Alt etki alanı|TTL|Hedef|
   |---|---|---|
   |autodiscover|3600 (saniye)|autodiscover.outlook.com.|

    ![OVH CNAME kaydı.](../../media/516938b3-0b12-4736-a631-099e12e189f5.png)

1. **İleri**'yi seçin.

    ![OVH CNAME değerleri ekleyin ve İleri'yi seçin.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)

1. **Onayla'yı** seçin.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa, Microsoft için yeni bir tane oluşturmayın. Bunun yerine, her iki değer kümesini içeren  *tek*  bir SPF kaydına sahip olmak için gerekli Microsoft değerlerini geçerli kayda ekleyin.

1. Başlamak için [bu bağlantıyı](https://www.ovh.com/manager/) kullanarak OVH'deki etki alanları sayfanıza gidin. Oturum açmanız istenir.

    ![OVH oturum açma.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Pano giriş sayfasındaki **Tüm etkinliğimi görüntüle'nin** altında, düzenlemek istediğiniz etki alanının adını seçin.

1. **DNS bölgesi'ne tıklayın**.

    ![OVH DNS bölgesini seçin.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. **Giriş ekle'yi** seçin.

    ![OVH Bir girdi ekleyin.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. **TXT'yi** seçin.

1. In the boxes for the new record, type or copy and paste the following values. TTL değeri atamak için, açılan listeden **Özel'i** seçin ve metin kutusuna değeri yazın.

   |Alt etki alanı|TTL|Değer|
   |---|---|---|
   |(boş bırakın)|3600 (saniye)|v=spf1 include:spf.protection.outlook.com -all <br/**Not:** Tüm aralıkların doğru kalması için bu girdiyi kopyalayıp yapıştırmanızı öneririz.|

    ![OVH SPF için TXT kaydı ekleyin.](../../media/f50466e9-1557-4548-8a39-e98978a5ee2e.png)

1. **İleri**'yi seçin.

    ![OVH SPF için TXT kaydı ekleyin ve İleri'yi seçin.](../../media/7937eb7c-114f-479f-a916-bcbe476d6108.png)

1. **Onayla'yı** seçin.

    ![OVH SPF ve Onayla için TXT kaydı ekleyin.](../../media/649eefeb-3227-49e3-98a0-1ce19c42fa54.png)

## <a name="advanced-option-skype-for-business"></a>Gelişmiş seçenek: Skype Kurumsal

Bu seçeneği yalnızca kuruluşunuz Microsoft Teams'in yanı sıra sohbet, konferans aramaları ve görüntülü aramalar gibi çevrimiçi iletişim hizmetleri için Skype Kurumsal kullanıyorsa belirtin. Skype için 4 kayıt gerekir: Kullanıcıdan kullanıcıya iletişim için 2 SRV kaydı ve oturum açmak ve kullanıcıları hizmete bağlamak için 2 CNAME kaydı.

### <a name="add-the-two-required-srv-records"></a>Gerekli iki SRV kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://www.ovh.com/manager/) kullanarak OVH'deki etki alanları sayfanıza gidin. Oturum açmanız istenir.

    ![OVH oturum açma.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Pano giriş sayfasındaki **Tüm etkinliğimi görüntüle'nin** altında, düzenlemek istediğiniz etki alanının adını seçin.

1. **DNS bölgesi'ne tıklayın**.

    ![OVH DNS bölgesini seçin.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. **Giriş ekle'yi** seçin.

    ![OVH Bir girdi ekleyin.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. **SRV'yi** seçin.

1. In the boxes for the new record, type or copy and paste the following values. TTL değeri atamak için, açılan listeden **Özel'i** seçin ve metin kutusuna değeri yazın.

   |Alt etki alanı|TTL (Saniye)|Öncelik|Ağırlık|Bağlantı noktası|Hedef|
   |---|---|---|---|---|---|
   |_sip._tls|3600 (s.)|100|1|443|sipdir.online.lync.com. **Bu değer nokta (.) ile bitmelidir.**><br> **Not:** Tüm aralıkların doğru kalması için bu girdiyi kopyalayıp yapıştırmanızı öneririz.|
   |_sipfederationtls._tcp|3600 (s.)|100|1|5061|sipfed.online.lync.com. **Bu değer nokta (.) ile bitmelidir.**<br> **Not:** Tüm aralıkların doğru kalması için bu girdiyi kopyalayıp yapıştırmanızı öneririz.|

1. Diğer SRV kaydını eklemek için **Başka bir kayıt ekle'yi** seçin, tablonun bir sonraki satırında yer alan değerleri kullanarak bir kayıt oluşturun ve ardından **Kayıt oluştur'u** seçin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışıyla veya diğer sorunlarla karşılaşıyorsanız, bkz. [Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra sorunları bulma ve düzeltme](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Skype Kurumsal için gereken iki CNAME kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://www.ovh.com/manager/) kullanarak OVH'deki etki alanları sayfanıza gidin. Oturum açmanız istenir.

    ![OVH oturum açma.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Pano giriş sayfasındaki **Tüm etkinliğimi görüntüle'nin** altında, düzenlemek istediğiniz etki alanının adını seçin.

1. **DNS bölgesi'ne tıklayın**.

    ![OVH DNS bölgesini seçin.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. **Giriş ekle'yi** seçin.

    ![OVH Bir girdi ekleyin.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. **CNAME'i** seçin.

    ![OVH CNAME kayıt türü ekleyin.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. Yeni kayıt kutularına, aşağıdaki tablonun ilk satırındaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın. TTL değeri atamak için, açılan listeden **Özel'i** seçin ve metin kutusuna değeri yazın.

   |Alt etki alanı|TTL|Hedef|
   |---|---|---|
   |sip|3600 (s.)|sipdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.**|
   |lyncdiscover|3600 (s.)|webdir.online.lync.com.  <br/> **Bu değer nokta (.) ile bitmelidir.**|

1. **İleri**'yi seçin.

    ![OVH CNAME değerleri ekleyin ve İleri'yi seçin.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)

1. **Onayla'yı** seçin.

1. Diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Gelişmiş seçenek: Microsoft 365 için Intune ve Mobil Cihaz Yönetimi

Bu hizmet, etki alanınıza bağlanan mobil cihazları güvenli ve uzaktan yönetmenize yardımcı olur. Mobil Cihaz Yönetimi, kullanıcıların cihazları hizmete kaydedebilmesi için iki CNAME kaydına ihtiyaç duyar.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Mobile Cihaz Yönetimi için gereken iki CNAME kaydını ekleme

1. Başlamak için [bu bağlantıyı](https://www.ovh.com/manager/) kullanarak OVH'deki etki alanları sayfanıza gidin. Oturum açmanız istenir.

    ![OVH oturum açma.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Pano giriş sayfasındaki **Tüm etkinliğimi görüntüle'nin** altında, düzenlemek istediğiniz etki alanının adını seçin.

1. **DNS bölgesi'ne tıklayın**.

    ![OVH DNS bölgesini seçin.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. **Giriş ekle'yi** seçin.

    ![OVH Bir girdi ekleyin.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. **CNAME'i** seçin.

    ![OVH CNAME kayıt türü ekleyin.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. Yeni kayıt kutularına, aşağıdaki tablonun ilk satırındaki değerleri yazın ya da bu tablodan kopyalayıp yapıştırın. TTL değeri atamak için, açılan listeden **Özel'i** seçin ve metin kutusuna değeri yazın.

   |Alt etki alanı|TTL|Hedef|
   |---|---|---|
   |enterpriseregistration  <br/>|3600 (s.)|enterpriseregistration.windows.net.  <br/> **Bu değer nokta (.) ile bitmelidir.**|
   |enterpriseenrollment|3600 (s.)|enterpriseenrollment-s.manage.microsoft.com.  <br/> **Bu değer nokta (.) ile bitmelidir.**|

1. **İleri**'yi seçin.

    ![OVH CNAME değerleri ekleyin ve İleri'yi seçin.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)

1. **Onayla'yı** seçin.

1. Diğer CNAME kaydını ekleyin.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.