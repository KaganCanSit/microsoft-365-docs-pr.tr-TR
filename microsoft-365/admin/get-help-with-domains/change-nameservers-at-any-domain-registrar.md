---
title: Herhangi bir etki alanı kayıt şirketiyle Microsoft 365 ad sunucularını değiştirme
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
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- okr_smb
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEU150
- GEA150
ms.assetid: a8b487a9-2a45-4581-9dc4-5d28a47010a2
description: E-posta ve Microsoft 365 Online gibi hizmetlerinizin kendi etki alanı adınızı kullanması için, etki Skype Kurumsal etki alanı ekleme ve ayarlama hakkında bilgi alın.
ms.openlocfilehash: 2d591429d74e03eec883b524b8fa36d082cfab93
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316975"
---
# <a name="change-nameservers-to-set-up-microsoft-365-with-any-domain-registrar"></a>Herhangi bir etki alanı kayıt şirketiyle Microsoft 365 ad sunucularını değiştirme

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**.

E-posta ve Teams gibi hizmetlerinizin kendi etki alanı adınızı kullanması için, etki Microsoft 365'de etki alanınızı eklemek ve ayarlamak için bu yönergeleri izleyin. Bunu yapmak için, etki alanınızı doğrular ve sonra da etki alanı ad sunucularınızı Microsoft 365 DNS kayıtlarının sizin için ayarlansın diye değiştirebilirsiniz. Aşağıdaki deyimler sizin durumunuz açıklarsa aşağıdaki adımları izleyin:

- Kendi etki alanınız var ve bu etki alanını kendi etki alanınız ile Microsoft 365.

- DNS Microsoft 365 sizin için yönetmeye hazır olmak istiyor uz. (İsterseniz [DNS kayıtlarınızı kendiniz yönetebilirsiniz](../setup/add-domain.md).)

## <a name="add-a-txt-or-mx-record-for-verification"></a>Doğrulama için bir TXT veya MX kaydı ekleyin

> [!NOTE]
> Bu kayıtlardan yalnızca birini veya diğerini oluşturacaksınız. Tercih edilen kayıt türü TXT'dir, ancak bazı DNS barındırma hizmet sağlayıcıları bunu desteklemez. Bu durumda, bir MX kaydı oluşturabilirsiniz.

Etki alanınızı bu etki alanına Microsoft 365, bu etki alanına sahip olduğundan emin olamız. Etki alanı kayıt şirketinizin hesabında oturum açabilme ve DNS kaydı oluşturabilme özelliği, etki Microsoft 365 size ait olduğunu kanıtlar.

> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. Dilerseniz bu kaydı daha sonra silebilirsiniz.

### <a name="find-the-area-on-your-dns-hosting-providers-website-where-you-can-create-a-new-record"></a>DNS barındırma sağlayıcınızın web sitesinde yeni kayıt oluşturabilirsiniz alanı bulma

1. DNS barındırma hizmet sağlayıcınızın web sitesinde oturum açın.

2. Etki alanınızı seçin.

3. Etki alanınızla ilgili DNS kayıtlarını düzenleyebileceğiniz sayfayı bulun.

### <a name="create-the-record"></a>Kaydı oluşturma

Oluşturduğunuz kaydın TXT veya MX olmasına bağlı olarak, aşağıdakilerden birini yapın:

**TXT kaydı oluşturuyorsanız, şu değerleri kullanın:**

<br>

****

|Kayıt türü|Diğer ad veya ana bilgisayar adı|Değer|TTL|
|---|---|---|---|
|TXT|Aşağıdakilerden birini yapın: **@** yazın, alanı boş bırakın veya etki alanı adınızı yazın.  <p> **Not**: Farklı DNS ana bilgisayarlarının bu alan için farklı gereksinimleri vardır.|MS=ms *XXXXXXXX* <p> **Not:** Bu bir örnektir. Hedef veya Adres **Noktaları değerinizi burada**, hedef tablodaki Microsoft 365. [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)|Bu değeri **1 saat** veya buna eşdeğer dakika sayısına ( **60** ), saniye sayısına ( **3600** ), vb. ayarlayın.    |
|||||

**MX kaydı oluşturuyorsanız, şu değerleri kullanın:**

<br>

****

|Kayıt türü|Diğer ad veya ana bilgisayar adı|Değer|Öncelik|TTL|
|---|---|---|---|---|
|MX|**@** veya etki alanı adınızı yazın. |MS=ms *XXXXXXXX* **Not:** Bu bir örnektir. Hedef veya Adres **Noktaları değerinizi burada**, hedef tablodaki Microsoft 365. [Bunu nasıl bulabilirim?](../get-help-with-domains/information-for-dns-records.md)|Öncelik **için**, posta akışında kullanılan MX kaydıyla çakışmayı önlemek için, var olan MX kayıtlarının önceliğe göre daha düşük bir öncelik kullanın. Öncelik hakkında daha fazla bilgi için bkz. [MX önceliği nedir?](../setup/domains-faq.yml)|Bu değeri **1 saat** veya buna eşdeğer dakika sayısına ( **60** ), saniye sayısına ( **3600** ), vb. ayarlayın.|
||||||

### <a name="save-the-record"></a>Kaydı kaydetme

Kaydı etki alanı kayıt şirketinizin sitesinde eklediknize göre, Microsoft 365'e geri dönüp kaydın Microsoft 365 için istekte bulundurabilirsiniz.

Yeni Microsoft 365 TXT kaydı bulduğunda, etki alanınız doğrulanır.

1. Yönetim merkezinde Etki Alanları'Ayarlar  \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>

2. Etki **Alanları** sayfasında, doğrulamakta olduğunu etki alanını seçin.

3. Kurulum sayfasında **Kurulumu** **başlat'ı seçin**.

4. Etki alanını **doğrulama sayfasında** Doğrula'ya **tıklayın**.

> [!NOTE]
> Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın.

## <a name="change-your-domains-nameserver-ns-records"></a>Etki alanınızın ad sunucusu (NS) kayıtlarını değiştirin

Bu sihirbazın etki alanları kurulum sihirbazının son adımına Microsoft 365 tek göreviniz kaldı. E-posta gibi Microsoft 365 hizmetleriyle etki alanınızı ayarlamak için, etki alanı kayıt şirketinde etki alanı ad sunucusu (veya NS) kayıtlarınızı birincil ve ikincil ad sunucularını işaret Microsoft 365 değiştirebilirsiniz. Ardından, Microsoft 365 DNS'nizi barındırıyor olması nedeniyle, hizmetleriniz için gereken DNS kayıtları sizin için otomatik olarak ayarlanır. Etki alanı kayıt şirketinizin web sitesinde sağlanıyor olabilecek adımları izleyerek ad sunucusu kayıtlarını kendiniz güncelleştirebilirsiniz. DNS hakkında bilginiz yoksa, etki alanı kayıt şirketi desteğine başvurun.

::: moniker range="o365-worldwide"

Etki alanı kayıt şirketinizin web sitesinde etki alanınızın ad sunucularını kendiniz değiştirmek için şu adımları izleyin:

1. Etki alanı kayıt şirketi web sitesinde, etki alanınız için ad sunucularını veya özel ad sunucularını kullanabileceğiniz bir alanı değiştirebilirsiniz.

2. Ad sunucusu kayıtları oluşturun veya var olan ad sunucusu kayıtlarını aşağıdaki değerlerle eş olacak şekilde düzenleyin:

    - İlk ad sunucusu: ns1.bdm.microsoftonline.com
    - İkinci ad sunucusu: ns2.bdm.microsoftonline.com
    - Üçüncü ad sunucusu: ns3.bdm.microsoftonline.com
    - Dördüncü ad sunucusu: ns4.bdm.microsoftonline.com

   > [!TIP]
   > En iyisi dört kaydı da eklemektir, ancak kayıt şirketiniz yalnızca iki kaydı destekliyorsa, **ns1.bdm.microsoftonline.com ve** **ns2.bdm.microsoftonline.com**.

3. Değişikliklerinizi kaydedin.

> [!CAUTION]
> Etki alanınıza ait NS kayıtlarını etki alanı ad sunucularını Microsoft 365 etki alanınıza bağlı olan tüm hizmetler etkilenir. Sihirbazın herhangi bir adımını, örneğin e-posta adreslerini ekleme adımını atladıysanız veya etki alanınızı bloglar, alış veriş sepetleri veya başka hizmetler için kullanıyorsanız, gereken bazı ek adımlar vardır. Bunları uygulamazsanız, bu değişiklik hizmet e-posta erişiminin kaybolması veya mevcut web sitenize erişilememesi gibi, hizmetlerde kesintilere yol açabilir.

::: moniker-end

::: moniker range="o365-21vianet"

1. Etki alanı kayıt şirketinizin web sitesinde etki alanınızın ad sunucularını düzenleyebileceğiniz yeri bulun.

2. İki ad sunucusu kaydı oluşturun veya varolan ad sunucusu kayıtlarını aşağıdaki değerlerle eşleşecek şekilde düzenleyin:

   - İlk ad sunucusu: ns1.dns.partner.microsoftonline.cn
   - İkinci ad sunucusu: ns2.dns.partner.microsoftonline.cn

   > [!TIP]
   > En az iki ad sunucusu kaydı kullanmanız gerekir. Listelenen başka ad sunucuları varsa bunları silebilir veya ad sunucusu olarak **ns3.dns.partner.microsoftonline.cn ns4.dns.partner.microsoftonline.cn.** 

3. Değişikliklerinizi kaydedin.

> [!CAUTION]
> Etki alanınıza ait NS kayıtlarını 21Vianet ad sunucuları tarafından Office 365 kullanıcı adına işaret etmek için değiştirerek, etki alanınıza bağlı olan tüm hizmetler etkilenir. Sihirbazın herhangi bir adımını, örneğin e-posta adreslerini ekleme adımını atladıysanız veya etki alanınızı bloglar, alış veriş sepetleri veya başka hizmetler için kullanıyorsanız, gereken bazı ek adımlar vardır. Bunları uygulamazsanız, bu değişiklik hizmet e-posta erişiminin kaybolması veya mevcut web sitenize erişilememesi gibi, hizmetlerde kesintilere yol açabilir.

::: moniker-end

Örneğin, e-posta ve web sitesi barındırma için gerekli olabilecek bazı ek adımlar şunlardır:

- NS kayıtlarınızı değiştirmeden önce, etki Microsoft 365 kullanan tüm e-posta adreslerini bu adreslere taşıma.

- Şu anda bir web sitesi adresiyle kullanılan bir etki alanını eklemek istiyor musunuz `https://www.fourthcoffee.com`? Etki alanını eklerken, web sitesini şu anda barındırılan yerde tutmak ve böylece siz etki alanının NS kayıtlarını siteyi doğru işaret edecek şekilde değiştirdikten sonra insanların web sitesine yine var Microsoft 365.

1. Yönetim merkezinde Etki Alanları'Ayarlar  \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>

2. **Etki Alanları** sayfasında bir etki alanı seçin.

3. Etki alanı ayrıntıları sayfasında DNS kayıtları **sekmesini** seçin.

4. Kayıt **ekle'yi seçin**.

5. Özel **DNS kaydı ekle bölmesindeki** Tür açılan **listesindeN** (Adres) **öğesini seçin**.

6. Ana bilgisayar **adı veya Diğer ad** kutusuna yazın **@**.

7. **IP Adresi kutusuna**, web sitesinin şu anda barındır bulunduğu statik IP adresini yazın. Örneğin, 172.16.140.1.

   > [!IMPORTANT]
   > Bu adres web _sitesinin statik_ IP adresi olmalıdır, dinamik IP _adresi_ değil. Genel web siteniz için statik IP adresi alabiliyorken web sitenizi barındıran siteyi kontrol edin.

8. Kaydın TTL ayarını değiştirmek için, **TTL** açılan listesinden yeni bir süre seçin. Aksi takdirde, 9. adıma geçin.

9. **Kaydet** 'i seçin.

Buna ek olarak, müşterilerin web sitenizi bulmalarına yardım etmek için bir CNAME kaydı da oluşturabilirsiniz.

1. Kayıt **ekle'yi seçin**.
2. Özel **DNS kaydı ekle bölmesindeki** Tür açılan listesinde **CNAME** (Diğer Ad **) öğesini seçin**.
3. Ana bilgisayar **adı veya Diğer ad kutusuna** **www yazın**.
4. Işaret **adresi kutusuna,** web sitenizin tam etki alanı adını (FQDN) yazın. Örneğin, **contoso.5om**.
5. Kaydın TTL ayarını değiştirmek için, **TTL** açılan listesinden yeni bir süre seçin. Aksi takdirde, 6. adıma geçin.
6. **Kaydet**'i seçin.

Ad sunucusu kayıtları Microsoft'a işaret etmek üzere güncelleştirildikten sonra, etki alanı kurulumunuz tamamlanır. E-posta Microsoft'a yönlendirildi ve web sitenizin adresine giden trafik geçerli web sitesi barındırma barındırma hizmetinize devam ediyor.'

> [!NOTE]
> Ad sunucusu kaydı güncelleştirmelerinizin İnternet DNS sistemi genelinde güncelleştirilmesi birkaç saat sürebilir. Ardından, Microsoft e-posta ve diğer hizmetlerinizin hepsi etki alanınız ile çalışacak şekilde ayarlanır.

## <a name="related-content"></a>İlgili içerik

[Etki alanınıza bağlanmak için DNS kayıtları ekleme](create-dns-records-at-any-dns-hosting-provider.md) (makale)\
[Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra sorunları bulma](find-and-fix-issues.md) ve düzeltme (makale)\
[Etki alanlarını yönetme](/admin) (bağlantı sayfası)
