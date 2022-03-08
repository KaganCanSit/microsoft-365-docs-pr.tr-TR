---
title: Etki alanınıza bağlanmak için DNS kayıtları ekleme
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
description: Bağlan etki alanını doğrulamak ve etki alanı kayıt Microsoft 365 hesapta DNS kayıtlarını güncelleştirerek, etki alanını herhangi bir DNS barındırma sağlayıcısında barındırmak için kullanabilirsiniz.
ms.custom:
- okr_smb
- AdminSurgePortfolio
- AdminTemplateSet
- business_assist
- admindeeplinkMAC
ms.openlocfilehash: 17a3a63dfb3faedb5ff213b24dd14abd57f55bb3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316933"
---
# <a name="add-dns-records-to-connect-your-domain"></a>Etki alanınıza bağlanmak için DNS kayıtları ekleme

Bir üçüncü taraf barındırma sağlayıcısından etki alanı satın aldıysanız, etki alanını Microsoft 365'a bağlamak için kayıt şirketinizin hesaplarında DNS kayıtlarını güncelleştirebilirsiniz.

Bu adımların sonunda, etki alanınız etki alanını satın aldığınız ana bilgisayarla kayıtlı kalır, ancak Microsoft 365 e-posta adresleriniz (user@yourdomain.com gibi) ve diğer hizmetleriniz için bu etki alanını kullanabilir.

Etki alanı ekley adresiniz yoksa, siz ekleyene kadar, onmicrosoft.com e-posta adresleri için etki alanınız bu etki alanını kullanır. Kullanıcıları eklemeden önce etki alanınızı eklemeniz önemlidir, böylece onları iki kez ayarlamak zorunda değildir.

[Aşağıda, ne](../setup/domains-faq.yml) arayabilirsiniz?

> [!TIP]
> Bu konudaki adımlarda yardıma ihtiyacınız varsa, [Microsoft küçük işletme uzmanıyla çalışmayı göz önünde bulundurabilirsiniz](https://go.microsoft.com/fwlink/?linkid=2186871). İş Yardımı ile, işe alımtan günlük kullanıma kadar işlerinizi büyüttükçe siz ve çalışanlarınız küçük işletme uzmanlarına 24 saat erişim elde ediyor.

## <a name="step-1-add-a-txt-or-mx-record-to-verify-you-own-the-domain"></a>1. Adım: Etki alanının sahibi olduğunu doğrulamak için TXT veya MX kaydı ekleme

### <a name="recommended-verify-with-a-txt-record"></a>Önerilen: TXT kaydıyla doğrulama

İlk olarak, belgenize eklemek istediğiniz etki alanının sahibi olduğunu kanıtlamanız Microsoft 365.

1. Etki alanı için oturum Microsoft 365 yönetim merkezi ve **Tüm etki alanları'Ayarlar** >  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**seçin**</a>.
2. Yeni bir tarayıcı sekmesinde veya penceresinde DNS barındırma sağlayıcınızda oturum açın ve ardından DNS ayarlarınızı yönetmek istediğiniz yeri (örneğin, Bölge Dosyası Ayarlar, Etki Alanlarını Yönet, Etki Alanı Yöneticisi, DNS Yöneticisi) bulun.
3. Sağlayıcınızın DNS Yöneticisi sayfasına gidin ve yönetim merkezinde gösterilen TXT kaydını etki alanınıza ekleyin.

   Bu kaydı eklemek var olan e-posta veya diğer hizmetlerinizi etkilemez ve etki alanınız başka hizmetlere bağlandıktan sonra bu kaydı Microsoft 365.

   Örneğin:

   - TXT Adı: `@`
   - TXT Değeri: MS=ms######## (yönetim merkezinden benzersiz kimlik)
   - TTL: `3600` (veya varsayılan sağlayıcınız)

4. Kaydı kaydedin, yönetim merkezine geri gidin ve Doğrula'ya **tıklayın**. Kayıt değişikliklerinin kaydedili genellikle 15 dakika kadar sürer, ancak bazen daha uzun da sürebilir. Biraz zaman ver ve değişikliği almaya birkaç kez çalışsın.

Microsoft doğru TXT kaydını bulduğunda, etki alanınız doğrulanır.

### <a name="verify-with-an-mx-record"></a>MX kaydıyla doğrulama

Kayıt şirketiniz TXT kayıtlarını eklemeyi desteklenmiyorsa, MX kaydı ekleyerek bunu doğruabilirsiniz.

1. Etki alanı için oturum Microsoft 365 yönetim merkezi ve **Tüm etki alanları'Ayarlar** >  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**seçin**</a>.
2. Yeni bir tarayıcı sekmesinde veya penceresinde DNS barındırma sağlayıcınızda oturum açın ve ardından DNS ayarlarınızı yönetmek istediğiniz yeri (örneğin, Bölge Dosyası Ayarlar, Etki Alanlarını Yönet, Etki Alanı Yöneticisi, DNS Yöneticisi) bulun.
3. Sağlayıcınızın DNS Yöneticisi sayfasına gidin ve yönetim merkezinde gösterilen MX kaydını etki alanınıza ekleyin.

Bu MX kaydının **Önceliği,** etki alanı için var olan tüm MX kayıtlarının en yüksek olması gerekir. Aksi takdirde, e-posta göndererek almak bu soruna neden olabilir. Etki alanı doğrulama tamamlandıktan sonra bu kayıtları silebilirsiniz.

Alanların aşağıdaki değerlere ayarlanmış olduğundan emin olun:

- Kayıt Türü: `MX`
- Öncelik: Önceden kullanılmamış olan büyük değere ayarlayın.
- Ana Bilgisayar Adı: `@`
- Points to address: Değeri yönetim merkezinden kopyalayıp buraya yapıştırın.
- TTL: `3600` (veya varsayılan sağlayıcınız)

Microsoft doğru MX kaydını bulduğunda, etki alanınız doğrulanır.

## <a name="step-2-add-dns-records-to-connect-microsoft-services"></a>2. Adım: Bağlantı kurarak bağlanmak için DNS Microsoft hizmetleri

Yeni bir tarayıcı sekmesinde veya penceresinde DNS barındırma sağlayıcınızda oturum açın ve DNS ayarlarınızı yönetebilirsiniz (örneğin, Bölge Dosyası Ayarlar, Etki Alanlarını Yönet, Etki Alanı Yöneticisi, DNS Yöneticisi).

Etkinleştirmek istediğiniz hizmetlere bağlı olarak, birkaç farklı türde DNS kaydı ekliyor oluruz.

### <a name="add-an-mx-record-for-email-outlook-exchange-online"></a>E-posta için MX kaydı ekleme (Outlook, Exchange Online)

**Başlamadan önce:** Etki alanınız ile zaten e-postanız varsa (user@yourdomain.com gibi), MX kayıtlarınızı ayarlamadan önce bu kullanıcıların hesaplarını yönetim merkezinde oluşturun. Bu şekilde, e-posta almaya devam eder. Etki alanınız MX kaydını güncelleştirin, etki alanını kullanan herkese gönderilecek tüm yeni e-Microsoft 365. E-postayı ve kişileri başka bir e-postaya geçirmeye karar vermedikçe, sahip olduğunuz tüm [e-postalar geçerli e-posta Microsoft 365.](../setup/migrate-email-and-contacts-admin.md)

Yönetim merkezi etki alanı kurulum sihirbazından MX kaydıyla ilgili bilgileri edinebilirsiniz.

Barındırma sağlayıcınızın web sitesinde yeni bir MX kaydı ekleyin.
Alanların aşağıdaki değerlere ayarlanmış olduğundan emin olun:

- Kayıt Türü: `MX`
- Öncelik: Normalde, kullanılabilen en yüksek değere ayarlanır `0`.
- Ana Bilgisayar Adı: `@`
- Points to address: Değeri yönetim merkezinden kopyalayıp buraya yapıştırın.
- TTL: `3600` (veya varsayılan sağlayıcınız)

Kaydı kaydedin ve sonra tüm diğer MX kayıtlarını kaldırın.

### <a name="add-cname-records-to-connect-other-services-teams-exchange-online-aad-mdm"></a>Diğer hizmetleri (Teams, Exchange Online, MDM) bağlamak AAD CNAME kayıtları ekleme

CNAME kayıtlarıyla ilgili bilgileri yönetim merkezi etki alanı kurulum sihirbazından edinebilirsiniz.

Barındırma sağlayıcınızın web sitesinde, bağlanmak istediğiniz her hizmet için CNAME kayıtlarını ekleyin.
Alanların her biri için aşağıdaki değerlere ayarlanmış olduğundan emin olun:

- Kayıt Türü: `CNAME (Alias)`
- Ana Bilgisayar: Kopyalayıp yönetim merkezinden değerleri buraya yapıştırın.
- Points to address: Değeri yönetim merkezinden kopyalayıp buraya yapıştırın.
- TTL: `3600` (veya varsayılan sağlayıcınız)

### <a name="add-or-edit-an-spf-txt-record-to-help-prevent-email-spam-outlook-exchange-online"></a>İstenmeyen e-postaları önlemeye yardımcı olmak için SPF TXT kaydı ekleyin veya düzenleyin (Outlook, Exchange Online)

**Başlamadan önce:** Etki alanınız için zaten bir SPF kaydınız varsa, etki alanınız için yeni bir SPF Microsoft 365. Bunun yerine, Microsoft 365 her iki değer kümesi de içeren tek *bir SPF* kaydına sahip olmak için gerekli kayıt değerlerini barındırma sağlayıcıları web sitenize ekleyin.

Barındırma sağlayıcınızın web sitesinde, var olan SPF kaydını düzenleyin veya bir SPF kaydı oluşturun.
Alanların aşağıdaki değerlere ayarlanmış olduğundan emin olun:

- Kayıt Türü: `TXT (Text)`
- Ana Bilgisayar: `@`
- TXT Değeri: `v=spf1 include:spf.protection.outlook.com -all`
- TTL: `3600` (veya varsayılan sağlayıcınız)

Kaydı kaydedin.

Bu SPF doğrulama araçlarından birini kullanarak [SPF kaydınızı doğrulama](/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain)

SPF, ifadeyi önlemeye yardımcı olmak için tasarlanmıştır ancak SPF'nin koruyamaz olduğu sanallık tekniklerini vardır. Bunlara karşı korunmak için, SPF'yi bir kez ayar verdiktan sonra bu alan için DKIM ve DMARC'yi de Microsoft 365.

Kullanmaya başlamak için bkz[. MICROSOFT 365'ta](../../security/office-365-security/use-dkim-to-validate-outbound-email.md) etki alanınıza gönderilen giden e-postayı doğrulamak için DKIM kullanma ve [DMARC](../../security/office-365-security/use-dmarc-to-validate-email.md) kullanarak e-postayı Microsoft 365.

### <a name="add-srv-records-for-communications-services-teams-skype-for-business"></a>İletişim hizmetleri için SRV kayıtları ekleme (Teams, Skype Kurumsal)

Barındırma sağlayıcınızın web sitesinde, bağlanmak istediğiniz her hizmet için SRV kayıtlarını ekleyin.
Alanların her biri için aşağıdaki değerlere ayarlanmış olduğundan emin olun:

- Kayıt Türü: `SRV (Service)`
- Ad: `@`
- Hedef: Yönetim merkezinden değeri kopyalayıp buraya yapıştırın.
- Protokol: Yönetim merkezinden değeri kopyalayıp buraya yapıştırın.
- Hizmet: Yönetim merkezinden değeri kopyalayıp buraya yapıştırın.
- Öncelik: `100`
- Ağırlık: `1`
- Bağlantı noktası: Yönetim merkezinden değeri kopyalayıp buraya yapıştırın.
- TTL: `3600` (veya varsayılan sağlayıcınız)

Kaydı kaydedin.

#### <a name="srv-record-field-restrictions-and-workarounds"></a>SRV kaydı alan kısıtlamaları ve geçici çözümleri

Bazı barındırma sağlayıcıları SRV kayıtları içindeki alan değerlerine kısıtlamalar dayatmaktadır. Bu kısıtlamalar için bazı yaygın geçici çözümler burada ve almaktadırsınız.

##### <a name="name"></a>Name

Barındırma sağlayıcınız bu alanın ayarına izin vermiyorsa **@**, alanı boş bırakın. Bu yaklaşımı yalnızca *barındırma sağlayıcınızda* Hizmet ve Protokol değerleri için ayrı alanlar olduğunda kullanın. Aksi takdirde, aşağıdaki Hizmet ve Protokol notlarına bakın.

##### <a name="service-and-protocol"></a>Hizmet ve Protokol

Barındırma sağlayıcınız SRV kayıtları için bu alanları sağlayamıyorsa, kaydın Ad alanında Hizmet  ve **Protokol değerlerini belirtmeniz** gerekir. (Not: Barındırma sağlayıcınıza bağlı olarak, Ad alanı  başka bir adı olabilir, örneğin: **Ana** **bilgisayar, Ana** bilgisayar adı veya **Alt etki alanı**.) Bu değerleri eklemek için, tek bir dize oluşturun ve değerleri birbirinden noktayla ayırarak.

Örnek: `_sip._tls`

##### <a name="priority-weight-and-port"></a>Öncelik, Ağırlık ve Bağlantı Noktası

Barındırma sağlayıcınız SRV kayıtları için bu alanları sağlayamıyorsa, bunları kaydın Hedef alanında **belirtebilirsiniz** . (Not: Barındırma sağlayıcınıza bağlı olarak, **Hedef** alanın adı farklı olabilir, örneğin: **İçerik**, **IP Adresi** veya **Hedef Ana Bilgisayar**.)

Bu değerleri eklemek için, değerleri birbirinden boşluklarla ayırarak ve bazen de bir noktayla *biten (emin* değilseniz sağlayıcınıza danışın) tek bir dize oluşturun. Değerler şu sırayla ek olmalıdır: Öncelik, Ağırlık, Bağlantı Noktası, Hedef.

- Örnek 1: `100 1 443 sipdir.online.lync.com.`
- Örnek 2: `100 1 443 sipdir.online.lync.com`

## <a name="related-content"></a>İlgili içerik

[Herhangi bir etki alanı kayıt şirketiyle etki Microsoft 365 ad sunucularını değiştir](change-nameservers-at-any-domain-registrar.md) (makale)\
[Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra sorunları bulma](find-and-fix-issues.md) ve düzeltme (makale)\
[Etki alanlarını yönetme](/admin) (bağlantı sayfası)
