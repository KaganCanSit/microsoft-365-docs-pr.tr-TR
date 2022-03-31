---
title: Etki alanınızı bağlamak için DNS kayıtları ekleme
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
search.appverid:
- MET150
description: Herhangi bir DNS barındırma sağlayıcısındaki etki alanınızı doğrulayarak ve kayıt şirketinizin hesabında DNS kayıtlarını güncelleştirerek etki alanınızı Microsoft 365’e bağlayın.
ms.custom:
- okr_smb
- AdminSurgePortfolio
- AdminTemplateSet
- business_assist
- admindeeplinkMAC
ms.openlocfilehash: 17a3a63dfb3faedb5ff213b24dd14abd57f55bb3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316933"
---
# <a name="add-dns-records-to-connect-your-domain"></a>Etki alanınızı bağlamak için DNS kayıtları ekleme

Üçüncü taraf barındırma sağlayıcısından bir etki alanı satın aldıysanız, kayıt şirketinizin hesabında DNS kayıtlarını güncelleştirerek bu etki alanını Microsoft 365’e bağlayabilirsiniz.

Bu adımların sonunda, etki alanınız onu satın aldığınız barındırma sağlayıcısında kayıtlı durumda kalır ancak Microsoft 365 bunu e-posta adresleriniz (kullanıcı@etkialanınız.com gibi) ve diğer hizmetler için kullanabilir.

Etki alanı eklemezseniz, siz ekleyene kadar kuruluşunuzdaki kişiler e-posta adresleri için onmicrosoft.com etki alanını kullanır. Kullanıcıları eklemeden önce etki alanınızı eklemek önemlidir; böylelikle onları iki kez ayarlamanız gerekmez.

Aradığınızı aşağıda bulamazsanız, [Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml).

> [!TIP]
> Bu konuda verilen adımlarla ilgili yardıma ihtiyacınız varsa, [bir Microsoft küçük işletme uzmanıyla çalışmayı](https://go.microsoft.com/fwlink/?linkid=2186871) göz önünde bulundurun. İşletme Yardımı ile, işletmenizi büyütürken katılımdan gündelik kullanıma kadar her aşamada siz ve çalışanlarınız günün 24 saati küçük işletme uzmanlarına erişebilirsiniz.

## <a name="step-1-add-a-txt-or-mx-record-to-verify-you-own-the-domain"></a>1. Adım: Kendi etki alanınızı doğrulamak için TXT veya MX kaydı ekleme

### <a name="recommended-verify-with-a-txt-record"></a>Önerilen: TXT kaydıyla doğrulama

İlk olarak, Microsoft 365’e eklemek istediğiniz etki alanının sahibi olduğunuzu kanıtlamanız gerekir.

1. Microsoft 365 yönetim merkezinde oturum açın ve **Tümünü göster** > **Ayarlar** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Etki Alanları**</a> öğesini seçin.
2. Yeni bir tarayıcı sekmesi veya penceresinde DNS barındırma sağlayıcınızda oturum açın ve ardından DNS ayarlarınızı yönettiğiniz yeri bulun (örneğin, Bölge Dosyası Ayarları, Etki Alanlarını Yönet, Etki Alanı Yöneticisi, DNS Yöneticisi).
3. Sağlayıcınızın DNS Yöneticisi sayfasına gidin ve yönetim merkezinde belirtilen TXT kaydını etki alanınıza ekleyin.

   Bu kaydın eklenmesi mevcut e-postanızı veya diğer hizmetlerinizi etkilemez ve etki alanınız Microsoft 365’e bağlandıktan sonra kaydı güvenle kaldırabilirsiniz.

   Örneğin:

   - TXT Adı: `@`
   - TXT Değeri: MS=ms######## (yönetim merkezinden benzersiz bir kimlik)
   - TTL: `3600` (veya varsayılan sağlayıcınız)

4. Kaydı kaydedin, yönetim merkezine dönün ve ardından **Doğrula**’yı seçin. Kayıt değişikliklerinin kaydedilmesi genellikle 15 dakika kadar sürer ancak bazen daha uzun sürebilir. Değişikliğin alınması için birkaç denemeye biraz zaman tanıyın.

Microsoft doğru TXT kaydını bulduğunda etki alanınız doğrulanır.

### <a name="verify-with-an-mx-record"></a>MX kaydıyla doğrulama

Kayıt şirketiniz TXT kayıtlarının eklenmesini desteklemiyorsa, MX kaydı ekleyerek doğrulayabilirsiniz.

1. Microsoft 365 yönetim merkezinde oturum açın ve **Tümünü göster** > **Ayarlar** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Etki Alanları**</a> öğesini seçin.
2. Yeni bir tarayıcı sekmesi veya penceresinde DNS barındırma sağlayıcınızda oturum açın ve ardından DNS ayarlarınızı yönettiğiniz yeri bulun (örneğin, Bölge Dosyası Ayarları, Etki Alanlarını Yönet, Etki Alanı Yöneticisi, DNS Yöneticisi).
3. Sağlayıcınızın DNS Yöneticisi sayfasına gidin ve yönetim merkezinde belirtilen MX kaydını etki alanınıza ekleyin.

MX kaydının **Öncelik** değeri, etki alanı için tüm mevcut MX kayıtlarındaki en yüksek değer olmalıdır. Aksi takdirde e-posta gönderme ve alma işlemini engelleyebilir. Etki alanı doğrulaması tamamlandıktan hemen sonra bu kayıtları silmelisiniz.

Alanların aşağıdaki değerlere ayarlandığından emin olun:

- Kayıt Türü: `MX`
- Öncelik: Henüz kullanılmamış herhangi bir büyük değere ayarlayın.
- Ana Bilgisayar Adı: `@`
- İşaret edilen adres: Yönetim merkezindeki değeri kopyalayın ve buraya yapıştırın.
- TTL: `3600` (veya varsayılan sağlayıcınız)

Microsoft doğru MX kaydını bulduğunda etki alanınız doğrulanır.

## <a name="step-2-add-dns-records-to-connect-microsoft-services"></a>2. Adım: Microsoft hizmetlerine bağlanmak için DNS kayıtlarını ekleme

Yeni bir tarayıcı sekmesi veya penceresinde DNS barındırma sağlayıcınızda oturum açın ve DNS ayarlarınızı yönettiğiniz yeri bulun (örneğin, Bölge Dosyası Ayarları, Etki Alanlarını Yönet, Etki Alanı Yöneticisi, DNS Yöneticisi).

Etkinleştirmek istediğiniz hizmetlere bağlı olarak farklı türlerde çeşitli DNS kayıtları eklersiniz.

### <a name="add-an-mx-record-for-email-outlook-exchange-online"></a>E-posta için MX kaydı ekleme (Outlook, Exchange Online)

**Başlamadan önce:** Kullanıcıların sizin etki alanınızda zaten e-postaları varsa (kullanıcı@etkialanınız.com gibi), MX kayıtlarınızı ayarlamadan önce yönetim merkezinde hesaplarını oluşturun. Bu şekilde e-posta almaya devam ederler. Etki alanınızın MX kaydını güncelleştirdiğinizde etki alanınızı kullanan herkese gönderilen tüm yeni e-postalar artık Microsoft 365’e gider. Önceden almış olduğunuz e-postalar, [e-postaları ve kişileri Microsoft 365’e geçirmeye](../setup/migrate-email-and-contacts-admin.md) karar vermediğiniz sürece geçerli e-posta barındırıcınızda kalır.

MX kaydına yönelik bilgileri, yönetim merkezi etki alanı kurulum sihirbazından alırsınız.

Barındırma sağlayıcınızın web sitesinde yeni bir MX kaydı ekleyin.
Alanların aşağıdaki değerlere ayarlandığından emin olun:

- Kayıt Türü: `MX`
- Öncelik: Kullanılabilir en yüksek değere ayarlayın; genellikle `0` olur.
- Ana Bilgisayar Adı: `@`
- İşaret edilen adres: Yönetim merkezindeki değeri kopyalayın ve buraya yapıştırın.
- TTL: `3600` (veya varsayılan sağlayıcınız)

Kaydı kaydedin ve ardından diğer tüm MX kayıtlarını kaldırın.

### <a name="add-cname-records-to-connect-other-services-teams-exchange-online-aad-mdm"></a>Diğer hizmetlere bağlanmak için CNAME kayıtları ekleme (Teams, Exchange Online, AAD, MDM)

CNAME kayıtlarına yönelik bilgileri, yönetim merkezi etki alanı kurulum sihirbazından alırsınız.

Barındırma sağlayıcınızın web sitesinde, bağlanmak istediğiniz her hizmet için CNAME kayıtları ekleyin.
Her birinde alanların aşağıdaki değerlere ayarlandığından emin olun:

- Kayıt Türü: `CNAME (Alias)`
- Ana Bilgisayar: Yönetim merkezinden kopyaladığınız değerleri buraya yapıştırın.
- İşaret edilen adres: Yönetim merkezindeki değeri kopyalayın ve buraya yapıştırın.
- TTL: `3600` (veya varsayılan sağlayıcınız)

### <a name="add-or-edit-an-spf-txt-record-to-help-prevent-email-spam-outlook-exchange-online"></a>İstenmeyen e-postayı önlemeye yardımcı olmak için SPF TXT kaydını ekleme veya düzenleme (Outlook, Exchange Online)

**Başlamadan önce:** Etki alanınız için zaten bir SPF kaydınız varsa Microsoft 365 için yeni SPF kaydı oluşturmayın. Bunun yerine, her iki değer kümesini de içeren *tek bir* SPF kaydınız olacak şekilde gerekli Microsoft 365 değerlerini barındırma sağlayıcılarınızın web sitesindeki geçerli kayda ekleyin.

Barındırma sağlayıcınızın web sitesinde, mevcut SPF kaydını düzenleyin veya bir SPF kaydı oluşturun.
Alanların aşağıdaki değerlere ayarlandığından emin olun:

- Kayıt Türü: `TXT (Text)`
- Ana Bilgisayar: `@`
- TXT Değeri: `v=spf1 include:spf.protection.outlook.com -all`
- TTL: `3600` (veya varsayılan sağlayıcınız)

Kaydı kaydedin.

Şu [SPF doğrulama araçlarından](/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain) birini kullanarak SPF kaydınızı doğrulayın.

SPF kimlik sahtekarlığını önlemeye yardımcı olmak için tasarlanmıştır, ancak SPF’nin koruma sağlayamayacağı bazı kimlik sahtekarlığı yöntemleri vardır. Bunlara karşı korunmak için, SPF’yi ayarladıktan sonra Microsoft 365 için DKIM ve DMARC’yi de ayarlamanız gerekir.

Başlamak için bkz. [Microsoft 365’te etki alanınızdan gönderilen giden e-postayı doğrulamak için DKIM kullanma](../../security/office-365-security/use-dkim-to-validate-outbound-email.md) ve [Microsoft 365’te e-postayı doğrulamak için DMARC kullanma](../../security/office-365-security/use-dmarc-to-validate-email.md).

### <a name="add-srv-records-for-communications-services-teams-skype-for-business"></a>İletişim hizmetleri için SRV kayıtları ekleme (Teams, Skype Kurumsal)

Barındırma sağlayıcınızın web sitesinde, bağlanmak istediğiniz her hizmet için SRV kayıtları ekleyin.
Her birinde alanların aşağıdaki değerlere ayarlandığından emin olun:

- Kayıt Türü: `SRV (Service)`
- Ad: `@`
- Hedef: Yönetim merkezindeki değeri kopyalayın ve buraya yapıştırın.
- Protokol: Yönetim merkezindeki değeri kopyalayın ve buraya yapıştırın.
- Hizmet: Yönetim merkezindeki değeri kopyalayın ve buraya yapıştırın.
- Öncelik: `100`
- Ağırlık: `1`
- Bağlantı Noktası: Yönetim merkezindeki değeri kopyalayın ve buraya yapıştırın.
- TTL: `3600` (veya varsayılan sağlayıcınız)

Kaydı kaydedin.

#### <a name="srv-record-field-restrictions-and-workarounds"></a>SRV kaydı alanının kısıtlamaları ve geçici çözümleri

Bazı barındırma sağlayıcıları SRV kayıtlarının içindeki alan değerlerine bazı kısıtlamalar getirir. Bu kısıtlamalara yönelik yaygın geçici çözümlerden bazıları aşağıda verilmiştir.

##### <a name="name"></a>Name

Barındırma sağlayıcınız bu alanın **@** olarak ayarlanmasına izin vermiyorsa, alanı boş bırakın. Bu yaklaşımı *yalnızca* barındırma sağlayıcınızda Hizmet ve Protokol değerleri için ayrı alanlar varsa kullanın. Aksi takdirde, aşağıdaki Hizmet ve Protokol notlarına bakın.

##### <a name="service-and-protocol"></a>Hizmet ve Protokol

Barındırma sağlayıcınız SRV kayıtları için bu alanları sağlamıyorsa, kaydın **Ad** alanında **Hizmet** ve **Protokol** değerlerini belirtmelisiniz. (Not: Barındırma sağlayıcınıza bağlı olarak **Ad** alanının adı farklı olabilir. Örneğin, **Ana Bilgisayar**, **Ana Bilgisayar Adı** veya **Alt Etki Alanı**.) Bu değerleri eklemek için, tek bir dize oluşturur ve değerleri nokta ile birbirinden ayırırsınız.

Örnek: `_sip._tls`

##### <a name="priority-weight-and-port"></a>Öncelik, Ağırlık ve Bağlantı Noktası

Barındırma sağlayıcınız SRV kayıtları için bu alanları sağlamıyorsa, bunları kaydın **Hedef** alanında belirtmeniz gerekir. (Not: Barındırma sağlayıcınıza bağlı olarak **Hedef** alanının adı farklı olabilir. Örneğin, **İçerik**, **IP Adresi** veya **Hedef Ana Bilgisayar**.)

Bu değerleri eklemek için tek bir dize oluşturup değerleri boşluklarla ayırın ve *bazı durumlarda sonuna bir nokta koyun* (emin değilseniz sağlayıcınıza danışın). Değerler şu sırayla eklenmelidir: Öncelik, Ağırlık, Bağlantı Noktası, Hedef.

- 1. Örnek: `100 1 443 sipdir.online.lync.com.`
- 2. Örnek: `100 1 443 sipdir.online.lync.com`

## <a name="related-content"></a>İlgili içerik

[Herhangi bir etki alanı kayıt şirketiyle Microsoft 365’i ayarlamak için ad sunucularını değiştirme](change-nameservers-at-any-domain-registrar.md) (makale)\
[Kendi etki alanınızı veya DNS kayıtlarınızı ekledikten sonra sorunları bulma ve düzeltme](find-and-fix-issues.md) (makale)\
[Etki alanlarını yönetme](/admin) (sayfa bağlantısı)
