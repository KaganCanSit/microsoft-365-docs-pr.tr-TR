---
title: Kurulum sınırlamaları olan etki alanı kayıtcılar
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- MET150
ROBOTS: NOINDEX
description: Bazı etki alanı kayıt şirketi sınırlı hizmetler sunar, bu da Microsoft özelliklerinin her etki alanıyla çalışmaymayacak olduğu anlamına gelir.
ms.openlocfilehash: 2d192f03c5a586e4355c1f9a08d312a07af3d501
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973597"
---
# <a name="domain-registrars-with-setup-limitations"></a>Kurulum sınırlamaları olan etki alanı kayıtcılar

[Microsoft için DNSMadeEasy'de DNS kayıtları oluşturma](#create-dns-records-at-dnsmadeeasy-for-microsoft)\
[Microsoft için easyDNS'de DNS kayıtları oluşturma](#create-dns-records-at-easydns-for-microsoft)\
[Microsoft için Freenom'da DNS kayıtları oluşturma](#create-dns-records-at-freenom-for-microsoft)\
[Microsoft için MyDomain'de DNS kayıtları oluşturma](#create-dns-records-at-mydomain-for-microsoft)\
[Microsoft için DNS kayıtları oluşturma Windows DNS'yi kullanma](#create-dns-records-for-microsoft-using-windows-based-dns)\
[Etki alanınız Google (eNom) tarafından yönetiliyorken DNS kayıtları oluşturma](#create-dns-records-when-your-domain-is-managed-by-google-enom)\
[Microsoft için 1&IONOS'ta DNS kayıtları oluşturma](#create-dns-records-at-11-ionos-for-microsoft)

Bazı etki alanı kayıt kullanıcılarında önemli hizmet sınırlamaları vardır ve bu da Microsoft özelliklerinin her etki alanıyla çalışmaymayacak olduğu anlamına gelir. Bazıgirdiricilerin belirli sınırlamaları bu makalede açıklanmıştır. 

## <a name="create-dns-records-at-dnsmadeeasy-for-microsoft"></a>Microsoft için DNSMadeEasy'de DNS kayıtları oluşturma

DNSMadeEasy hesapları için, eklediğiniz etki alanı ayrı bir etki alanı kayıt şirketinden satın alınmıştır. DNSMadeEasy etki alanı kayıt hizmetleri sağlamaz. DNSMadeEasy'de oturum açabilmeniz ve DNS kaydı oluşturabilmeniz, sahipliği kanıtlamak için yeterli olur.

## <a name="create-dns-records-at-easydns-for-microsoft"></a>Microsoft için easyDNS'de DNS kayıtları oluşturma

SRV Kayıtları şu anda herhangi bir easyDNS hizmet paketinde kullanılamaz. SRV kayıtlarını eklemek için kolayDN'lerle daha yüksek bir hizmet düzeyine yükseltmeniz gerekebilir. Bu kayıtların özel olarak Teams.

## <a name="create-dns-records-at-freenom-for-microsoft"></a>Microsoft için Freenom'da DNS kayıtları oluşturma

Freenom web sitesi SRV kayıtlarının eklemeyi desteklemez; bu da, çeşitli posta Teams E-posta özelliklerinin çalışmaymayacak olduğu anlamına gelir. Hangi Microsoft planını kullanırsa kullanın, önemli hizmet sınırlamaları vardır ve farklı bir DNS barındırma sağlayıcısına geçmek gerekebilir.

## <a name="create-dns-records-at-mydomain-for-microsoft"></a>Microsoft için MyDomain'de DNS kayıtları oluşturma

MyDomain web sitesi SRV kayıtlarını desteklemez; bu da, çeşitli Teams E-posta özellikleri çalışmaymayacak anlamına gelir. Hangi Microsoft planını kullanırsanız kullanın, DNS kayıtlarınızı MyDomain'de yönetirken önemli hizmet sınırlamaları vardır ve başka bir DNS barındırma sağlayıcısına geçmek de istemeniz gerekebilir.

## <a name="create-dns-records-for-microsoft-using-windows-based-dns"></a>Microsoft için DNS kayıtları oluşturma Windows DNS'yi kullanma

Etki alanınızın DNS kayıtlarını içeren sayfaya gidin. Windows Server 2008'de çalışıyorsanız, Başlat, **Çalıştır'a** **gidin**. Başka bir çalışma Windows Server 2012, Windows **ve r tuşuna** **basın**. **dnsmgmnt.msc yazın ve** Tamam'ı **seçin**. DNS Yöneticisi'nde, **DNS sunucu adı olan İleri**  **Arama Bölgeleri'ni genişletin**. Etki alanınızı seçin. Artık DNS kayıtlarını oluşturmaya hazırsınız.

## <a name="create-dns-records-when-your-domain-is-managed-by-google-enom"></a>Etki alanınız Google (eNom) tarafından yönetiliyorken DNS kayıtları oluşturma

Etki alanınızı Google Apps for Work hesabınıza kaydolarak Google aracılığıyla satın aldıysanız, DNS kayıtlarınız Google tarafından yönetilir, ancak eNom ile kaydedilir. Google Etki Alanları sayfası aracılığıyla eNom'a erişerek DNS oluşturabilirsiniz.

## <a name="create-dns-records-at-11-ionos-for-microsoft"></a>Microsoft için 1&1 IONOS'ta DNS kayıtları oluşturma

1&1 IONOS, etki alanının hem MX kaydı hem de en üst düzey Otomatik Bulma CNAME kaydının olmasına izin vermez. Bu, Microsoft için güvenlik ayarlarını yapılandırma Exchange Online sınırlar. Bu sorunun geçici bir çözümü vardır, ancak bu çözümü yalnızca 1 veya 1 IONOS'ta alt etki alanı oluşturma deneyimi&öneririz.

Bu hizmet sınırlamasına rağmen kendi Microsoft DNS kayıtlarınızı 1&1 IONOS'ta yönetmeyi seçerseniz, bu makaledeki adımları izleyin ve etki alanını doğrulayın ve e-posta, Skype Kurumsal Online, gibi dns kayıtlarını ayarlayın.

1&1 IONOS için geçici bir çözüm gerekir, böylece Microsoft e-posta hizmetleri için gereken CNAME kayıtlarıyla birlikte bir MX kaydı kullanabilirsiniz. Bu geçici çözüm için 1 ile 1 IONOS arasında bir dizi alt etki&ve bunları CNAME kayıtlarına atamanızı gerekir.

> [!NOTE]
> Bu yordama başlamadan önce kullanılabilir en az iki alt etki alanınızın olduğundan emin olun. Yalnızca 1 veya 1 IONOS'ta alt etki alanı oluşturma deneyimine sahip&öneririz.

### <a name="basic-cname-records"></a>Temel CNAME kayıtları

1.  Çalışmaya devam etmek için 1 veya 1 IONOS&etki alanları sayfanıza gidin. Oturum açmanız istenir.

1.  Etki alanlarını **yönet'i seçin**.

1.  Etki Alanı Merkezi sayfasında, güncelleştirmek istediğiniz etki alanını bulun ve ardından Alt Etki Alanları **Yönet'i seçin**. Şimdi iki alt etki alanı oluştur olacak ve her biri için diğer ad değeri  ayarasınız (Bu gereklidir çünkü 1&1 IONOS tek bir üst düzey CNAME kaydını destekler, ancak Microsoft için birkaç CNAME kaydı gereklidir.)

1.  İlk olarak, Otomatik Bulma alt etki alanını oluşturacaksınız. Alt Etki **Alanı'ne Genel Bakış** bölümünde Alt **Etki Alanı Oluştur'a tıklayın**.

1.  Yeni alt etki alanının **Alt Etki Alanı Oluştur** kutusunda, yalnızca aşağıdaki tablodan **Alt Etki Alanı Oluştur** değerini yazın veya kopyalayıp yapıştırın. (Diğer Ad değerini **daha sonraki** bir adımda ekleyeceğiz.)

    |Alt Etki Alanı Oluştur|Diğer Ad|
    |:----|:----|
    |autodiscover|autodiscover.outlook.com|

1.  Alt **Etki Alanı Oluştur'a seçin**.

1.  Alt Etki **Alanı Genel Görünümü** bölümünde, yeni oluşturduğunuz otomatik bulma alt etki öğesini bulun ve bu alt etki alanı için Panel (v) denetimi seçin.

1.  Alt Etki **Alanı Etki Alanı Ayarlar** DNS Etki Alanı **Düzenle'yi Ayarlar**.

1.  **A/AAAA Kayıtları (IP Adresleri)** bölümündeki **IP adresi (A Kaydı)** alanında **CNAME'yi seçin**.

1. **Diğer Ad:** kutusunda, yalnızca aşağıdaki tabloda verilen **Diğer Ad** değerini yazın veya kopyalayıp yapıştırın.

    |Alt Etki Alanı Oluştur|Diğer Ad|
    |:----|:----|
    |autodiscover|autodiscover.outlook.com|

1. **Farkındayım** bildiriminin onay kutusunu seçin.

1. **Kaydet**'i seçin.

### <a name="additional-cname-records"></a>Ek CNAME kayıtları

Aşağıdaki yordamda yer alan ek CNAME kayıtları Skype Kurumsal etkinleştirir. Önceden oluşturduğunuz iki CNAME kaydı için de aynı adımları kullanın.

**Üçüncü alt etki alanı oluşturma (Lyncdiscover)**

1.  Alt Etki **Alanı Genel Görünümü bölümünde** Alt Etki **Alanı Oluştur'a tıklayın**.

1.  Yeni alt etki alanının **Alt Etki Alanı Oluştur** kutusunda, yalnızca aşağıdaki tablodan **Alt Etki Alanı Oluştur** değerini yazın veya kopyalayıp yapıştırın. (Diğer Ad değerini **daha sonraki** bir adımda ekleyeceğiz.)

    |Alt Etki Alanı Oluştur|Diğer Ad|
    |:----|:----|
    |lyncdiscover|webdir.online.lync.com|

1.  Alt **Etki Alanı Oluştur'a seçin**.

1.  Etki Alanı Merkezi sayfasında Alt Etki **Alanları Yönet'i seçin**.

1.  Alt Etki **Alanı'na Genel** Bakış bölümünde, yeni oluşturduğunuz lyncdiscover alt etki alanı'nı bulun ve bu alt etki alanı için Panel (v) denetimi seçin. Alt Etki **Alanı Etki Alanı Ayarlar** DNS Etki Alanı **Düzenle'yi Ayarlar**.

1.  **A/AAAA Kayıtları (IP Adresleri)** bölümündeki **IP adresi (A Kaydı)** alanında **CNAME'yi seçin**.

1.  **Diğer Ad:** kutusunda, yalnızca aşağıdaki tabloda verilen **Diğer Ad** değerini yazın veya kopyalayıp yapıştırın.

    |Alt Etki Alanı Oluştur|Diğer Ad|
    |:----|:----|
    |lyncdiscover|webdir.online.lync.com|

1.  Farkındayım uyarı kutusunun **onay kutusunu seçin ve** sonra da Kaydet'i **seçin**.

1.  **DNS kayıtlarını düzenle Ayarlar** kutusunda Evet'i **seçin**.

**Dördüncü alt etki alanı (SIP) oluşturma**

1.  Alt Etki **Alanı'ne Genel Bakış** bölümünde Alt **Etki Alanı Oluştur'a tıklayın**.

1.  Yeni alt etki alanının **Alt Etki Alanı Oluştur** kutusunda, yalnızca aşağıdaki tablodan **Alt Etki Alanı Oluştur** değerini yazın veya kopyalayıp yapıştırın. (Diğer Ad değerini sonraki **bir** adıma eklersiniz.)

    |Alt Etki Alanı Oluştur|Diğer Ad|
    |:----|:----|
    |sip|sipdir.online.lync.com|  

1.  Alt **Etki Alanı Oluştur'a seçin**.

1.  Etki Alanı Merkezi sayfasında Alt Etki **Alanları Yönet'i seçin**.

1.  Alt **Etki Alanı Genel Görünümü** bölümünde, yeni oluşturduğunuz sip alt etki öğesini bulun ve bu alt etki alanı için Panel (v) denetimi seçin. <br/> Alt Etki **Alanı Etki Alanı Ayarlar** DNS Etki Alanı **Düzenle'yi Ayarlar**.

1.  **A/AAAA Kayıtları (IP Adresleri)** bölümündeki **IP adresi (A Kaydı)** alanında **CNAME'yi seçin**.

1.  **Diğer Ad:** kutusunda, yalnızca aşağıdaki tabloda verilen **Diğer Ad** değerini yazın veya kopyalayıp yapıştırın.

    |Alt Etki Alanı Oluştur|Diğer Ad|
    |:----|:----|
    |sip|sipdir.online.lync.com|

1.  Farkındayım uyarı kutusunun **onay kutusunu seçin ve** sonra da Kaydet'i **seçin**.

1.  **DNS kayıtlarını düzenle Ayarlar** kutusunda Evet'i **seçin**.

### <a name="cname-records-needed-for-mdm"></a>MDM için gereken CNAME kayıtları

Diğer dört CNAME kaydı için kullanılan yordamı izleyin ancak şu değerleri girin:

|Alt Etki Alanı Oluştur|Diğer Ad|
|:----|:----|
|enterpriseregistration|enterpriseregistration.windows.net|
|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com|
