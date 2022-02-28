---
title: Microsoft için DNS kayıtları oluşturma Windows DNS'yi kullanma
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
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
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9eec911d-5773-422c-9593-40e1147ffbde
description: Microsoft'un kendi tabanlı DNS sitesinde etki alanlarınızı doğrulamayı ve e-posta, Skype Kurumsal Online ve diğer Windows DNS kayıtlarını ayarlamayı öğrenin.
ms.openlocfilehash: 43cc3679f33a929545ed3d9deec388126aec853c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983840"
---
# <a name="create-dns-records-for-microsoft-using-windows-based-dns"></a>Microsoft için DNS kayıtları oluşturma Windows DNS'yi kullanma

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**. 
   
Windows tabanlı DNS kullanarak DNS kayıtlarınızı kendiniz barındırıyorsanız, bu makalede verilen adımları izleyerek e-posta, Skype Kurumsal Çevrimiçi, vb. için kayıtlarınızı ayarlayın.
  
Çalışmaya başlamanız için DNS [kayıtlarınızı güncelleştirmeniz Windows DNS'de](#find-your-dns-records-in-windows-based-dns) bulmanız gerekir. Ayrıca, şirket içi Active Directory'nizi Microsoft ile eşitlemeyi planlıyorsanız, bkz. Şirket içi Active Directory'niz içinde UPN olarak kullanılan yönlendirilebilir olmayan [e-posta adresi](#non-routable-email-address-used-as-a-upn-in-your-on-prem-active-directory).
  
DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla ilgili sorunlar, bkz. Etki [alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="find-your-dns-records-in-windows-based-dns"></a>Windows tabanlı DNS'te DNS raporlarınızı bulun
<a name="BKMK_find_your_dns_1"> </a> Etki alanınız için DNS kayıtlarının olduğu sayfaya gidin. Windows Server 2008'de çalışıyorsanız, **StartRun'a** >  **gidin**. Başka bir çalışma Windows Server 2012, Windows ve r tuşuna **basın**. **dnsmgmnt.msc yazın ve** Tamam'ı **seçin**. DNS Yöneticisi'nde İleri Arama **Bölgeleri'ni\<DNS server name\>\> genişletin**. Etki alanınızı seçin. Artık DNS kayıtlarını oluşturmaya hazırsınız.
   
## <a name="add-mx-record"></a>MX kaydını ekleme
<a name="BKMK_add_MX"> </a>

Etki alanınıza gelen e-postanın Microsoft'a gelsin için bir MX kaydı ekleyin.
- Ekley istediğiniz MX kaydı bir değer (Points **to address** value) içerir ve bu değer şöyle olur: \<MX token\>.mail.protection.outlook.com, \<MX token\> burada MSxxxxxxx gibi bir değerdir. 
- Microsoft'ta DNS kayıtları ekle sayfasının Exchange Online MX satırına gidip, Points to address altında listelenen değeri kopyalayın. Bu görevde oluşturmakta olduğunu kayıtta bu değeri kullansın. 
- DNS Yöneticisi sayfasında etki alanına karşılık **ActionMail** >  Exchanger (MX) adresine gidin. Etki alanına bu sayfayı bulmak için bkz[. Kendi tabanlı DNS'Windows DNS kayıtlarınızı bulma](#find-your-dns-records-in-windows-based-dns).  
- Yeni **Kaynak Kaydı iletişim** kutusunda, alanların tam olarak aşağıdaki değerlere ayarlanmış olduğundan emin olun: 
    - Ana Bilgisayar Adı: 
    - @Address: Microsoft'tan kopyalayıp az önce burada Hedef adres değerini yapıştırın.  
    - Pref: 
- **Değişiklikleri Kaydet**'i seçin.
- Geçersiz MX kayıtlarını kaldırın. Bu etki alanı için, e-postaları başka bir yere yönlendiren eski MX kayıtlarınız varsa, her eski kaydın yanındaki onay kutusunu seçin ve sonra **da DeleteOK'u** >  **seçin**. 
   
## <a name="add-cname-records"></a>CNAME kayıtlarını ekleme
<a name="BKMK_add_CNAME"> </a>

Microsoft için gereken CNAME kayıtlarını ekleyin. Microsoft'ta ek CNAME kayıtları listelenirse, burada gösterilen genel adımların aynısını kullanarak bu kayıtları ekleyin.
  
> [!IMPORTANT]
> Microsoft için Mobil Cihaz Yönetimi (MDM) varsa, iki CNAME kaydı daha oluşturmanız gerekir. Diğer dört CNAME kaydı için kullandığınız yordamı uygulayın ancak değerleri aşağıdaki tablodan sağlayın. (MDM'miz yoksa bu adımı atlayabilirsiniz.) 

- DNS Yöneticisi sayfasında etki alanına göre, **ActionCNAME** >  **(CNAME)'ye gidin**.
- Yeni **Kaynak Kaydı iletişim** kutusunda, alanların tam olarak aşağıdaki değerlere ayarlanmış olduğundan emin olun:  
    - Ana Bilgisayar Adı: autodiscover
    - Tür: 
    - CNAMEAddress: autodiscover.outlook.com
- **OK'yi** seçin.

SIP CNAME kaydını ekleyin. 
- DNS Yöneticisi sayfasında etki alanına göre Eylem  \> **CNAME (CNAME)'ye gidin**. 
- Yeni **Kaynak Kaydı iletişim** kutusunda, alanların tam olarak aşağıdaki değerlere ayarlanmış olduğundan emin olun:  
    - Ana Bilgisayar Adı: sip
    - Tür: CNAME
    - Adres: sipdir.online.lync.com
- **Tamam**'ı seçin.

Skype Kurumsal Çevrimiçi Otomatik Bulma CNAME kaydını ekleyin.  
- DNS Yöneticisi sayfasında etki alanına göre Eylem  \> **CNAME (CNAME)'ye gidin**. Yeni **Kaynak Kaydı iletişim** kutusunda, alanların tam olarak aşağıdaki değerlere ayarlanmış olduğundan emin olun:  
    - Ana Bilgisayar Adı: lyncdiscover
    - Tür: CNAME
    - Adres: webdir.online.lync.com
- **Tamam**'ı seçin.
   
### <a name="add-two-cname-records-for-mobile-device-management-mdm-for-microsoft"></a>Microsoft için Mobil Cihaz Yönetimi'ne (MDM) iki CNAME kaydı ekleme

> [!IMPORTANT]
> Microsoft için Mobil Cihaz Yönetimi (MDM) varsa, iki CNAME kaydı daha oluşturmanız gerekir. Diğer dört CNAME kaydı için kullandığınız yordamı uygulayın ancak değerleri aşağıdaki tablodan sağlayın. >(MDM'miz yoksa, bu adımı atlayabilirsiniz.) 
  

MDM Enterpriseregistration CNAME kaydını ekleyin.  
- DNS Yöneticisi sayfasında etki alanına göre Eylem  \> **CNAME (CNAME)'ye gidin**. 
- Yeni **Kaynak Kaydı iletişim** kutusunda, alanların tam olarak aşağıdaki değerlere ayarlanmış olduğundan emin olun:  
- Ana Bilgisayar Adı: enterpriseregistration
- Tür: CNAME
- Adres: enterpriseregistration.windows.net
- **Tamam**'ı seçin. 

MDM Enterpriseenrollment CNAME kaydını ekleyin. 
-  DNS Yöneticisi sayfasında etki alanına göre Eylem  \> **CNAME (CNAME)'ye gidin**. 
-  Yeni **Kaynak Kaydı iletişim** kutusunda, alanların tam olarak aşağıdaki değerlere ayarlanmış olduğundan emin olun:  
    - Ana Bilgisayar Adı: enterpriseenrollment
    - Tür: CNAME
    - Adres: enterpriseenrollment-s.manage.microsoft.com
- **Tamam**'ı seçin.
   
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>SPF'nin gereksiz e-postaları önlemesine yardımcı olmak için TXT kaydı ekleme
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> Bir etki alanına yönelik SPF için birden fazla TXT kaydına sahip olamazsınız. Etki alanınızda birden fazla SPF kaydı varsa bu durum, e-posta hatalarının yanı sıra teslimat ve istenmeyen posta sınıflandırma sorunlarına neden olabilir. Etki alanınız için zaten bir SPF kaydınız varsa Microsoft için yeni bir SPF kaydı oluşturun. Bunun yerine, her iki değer kümesi de içeren tek  *bir SPF*  kaydına sahip olmak için gerekli Microsoft değerlerini geçerli kayda ekleyin. 
  
Gereksiz e-postayı engellemeye yardımcı olmak üzere etki alanınız için SPF TXT kaydını ekleyin.
  
- Bu kaydın TXT değerinde zaten başka dizeler (örneğin, pazarlama e-postaları için dizeler) bulunabilir ve bu sorun yaratmaz. Söz konusu dizeleri olduğu gibi bırakın ve bunu da ekleyin. Dizeleri birbirinden ayırmak için her birini çift tırnak içine alın. 
- DNS Yöneticisi sayfasında etki alanınıza göre Eylem Metni  \> **(TXT)'ye gidin**. 
-  Yeni **Kaynak Kaydı iletişim** kutusunda, alanların tam olarak aşağıdaki değerlere ayarlanmış olduğundan emin olun. 
 > [!IMPORTANT]
> DNS Yöneticisi'Windows bazı sürümlerinde etki alanı, bir txt kaydı ekleyebilirsiniz ve bu şekilde, ana bilgisayar adı varsayılan olarak üst etki alanına ayarlanmış olabilir. Bu durumda, TXT kaydı eklerken ana bilgisayar adını @ veya etki alanı adına ayarlamak yerine boş olarak ayarlayın (değer eklemeyin). 

-  Ana bilgisayar türü: @
-  Kayıt Türü: TXT
-  Adres: v=spf1 include:spf.protection.outlook.com -all 
         
-  **Tamam**'ı seçin.
   
## <a name="add-srv-records"></a>SRV kayıtlarını ekleme
<a name="BKMK_add_SRV"> </a>

Microsoft için gereken iki SRV kaydı ekleyin.

Skype Kurumsal Çevrimiçi web konferansı için SIP SRV kaydını ekleyin.  <br/> 
-  DNS Yöneticisi sayfasında etki alanınıza uygun olarak Eylem Diğer Yeni **Kayıtlar'a** \> gidin. 
-   Kaynak Kayıt **Türü penceresinde Hizmet** Konumu **(SRV) öğesini seçin ve sonra** da Kayıt Oluştur'a **tıklayın**. 
-   Yeni **Kaynak Kaydı iletişim** kutusunda, alanların tam olarak aşağıdaki değerlere ayarlanmış olduğundan emin olun:  
    -  Hizmet: _sip
    -  Protokol: _tls
    -  Öncelik: 100
    -  Ağırlık: 1
    -  Bağlantı Noktası: 443
    -  Hedef (Ana Bilgisayar Adı): sipdir.online.lync.com
-  **Tamam**'ı seçin. 


Skype Kurumsal Çevrimiçi federasyonu için SIP SRV kaydını ekleyin.  
-  DNS Yöneticisi sayfasında etki alanınıza uygun olarak Eylem Diğer Yeni **Kayıtlar'a** \> gidin.  
-  Kaynak Kayıt **Türü penceresinde Hizmet** Konumu **(SRV) öğesini seçin ve sonra** da Kayıt Oluştur'a **tıklayın**. 
-   Yeni **Kaynak Kaydı iletişim** kutusunda, alanların tam olarak aşağıdaki değerlere ayarlanmış olduğundan emin olun:  
    -  Hizmet: _sipfederationtls
    -  Protokol: _tcp
    -  Öncelik: 100
    -  Ağırlık: 1
    -  Bağlantı Noktası: 5061
    -  Hedef (Ana Bilgisayar Adı): sipfed.online.lync.com
-  **Tamam**'ı seçin. 
   
## <a name="add-a-record-to-verify-that-you-own-the-domain-if-you-havent-already"></a>Henüz eklemediyseniz, etki alanına sahip olduğunuzu doğrulamak için kayıt ekleme
<a name="BKMK_verify"> </a>

Etki alanı adınızı ayarlamak için DNS kayıtlarını eklemeden Microsoft hizmetleri, Microsoft'un eklemekte olduğu etki alanının sahibi olduğunu onaylaması gerekir. Bunu yapmak için, aşağıdaki adımları izleyerek bir kayıt eklersiniz.
  
> [!NOTE]
> Bu kayıt yalnızca etki alanının sahibi olduğunuzu doğrulamak için kullanılır; başka hiçbir şeyi etkilemez. 
  

1. Microsoft'tan bilgi toplayın.  <br/> 
2. Yönetim merkezinde Etki Alanları'Ayarlar  \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a> 
3. Etki **Alanları** sayfasında, **doğrulamakta olduğunuz** etki alanının Eylemler sütununda Kurulumu başlat'ı **seçin**. 
4. **Microsoft'a etki alanı ekleme sayfasında** **1. adımı başlat'ı seçin**. 
5. Etki alanının **size ait olduğunu onaylayın** sayfasındaki Bu adımı şu  şekilde gerçekleştirme yönergelerine bakın açılır listesinde Genel **yönergeler'i seçin**. 
6. Tablodan, Hedef veya Hedef Noktaları Adresi değerini kopyalayın. Bir sonraki adımda buna ihtiyacınız olacak. Tüm boşlukların doğru kalması için bu değeri kopyalayıp yapıştırarak yeniden yapıştırın.

TXT kaydı ekleyin. 
-  DNS Yöneticisi sayfasında etki alanınıza göre Eylem Metni  \> **(TXT)'ye gidin**. 
-   Yeni Kaynak **Kaydı iletişim kutusunda** Düzenle'yi **seçin**.  
-  Yeni **Kaynak Kaydı iletişim** kutusunun Özel **Ana** Bilgisayar Adları alanında, alanların tam olarak aşağıdaki değerlere ayarlanmış olduğundan emin olun. 

> [!IMPORTANT] 
> DNS Yöneticisi'Windows bazı sürümlerinde etki alanı, bir txt kaydı ekleyebilirsiniz ve bu şekilde, ana bilgisayar adı varsayılan olarak üst etki alanına ayarlanmış olabilir. Bu durumda, TXT kaydı eklerken ana bilgisayar adını @ veya etki alanı adına ayarlamak yerine boş olarak ayarlayın (değer eklemeyin). 

- Ana Bilgisayar Adı: @
- Tür: TXT
- Adres: Microsoft'tan az önce kopyalayıp hedef veya Hedef Adres Noktaları değerini buraya yapıştırın.  
- **OKDone'i** >  seçin.

Microsoft'ta etki alanınızı doğrulayın.  
> [!IMPORTANT]
> Bunu yapmak için 15 dakika kadar bekleyin, böylece yeni oluşturduğunuz kayıt İnternet genelinde güncelleştirilsin.       

- Microsoft'a geri gidin ve doğrulama denetimi talep etmek için aşağıdaki adımları izleyin. Denetimde, önceki adımda eklediğiniz TXT kaydı aranır. Doğru TXT kaydı bulunduğunda, etki alanı doğrulanır.  
1. Yönetim merkezinde Kurulum Etki Alanları **sayfasına** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">gidin.</a>
2. Etki **Alanları sayfasında** , doğrulamakta **olduğunuz** etki alanının Eylem sütununda Kurulumu başlat'ı **seçin**. 
3. Etki alanının **sahibi olduğunu doğrulayın sayfasında Bitti** , şimdi **doğrula'ya** tıklayın ve ardından onay iletişim kutusunda Son'a **tıklayın**. 
   
> [!NOTE]
>  Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 
  
## <a name="non-routable-email-address-used-as-a-upn-in-your-on-prem-active-directory"></a>Şirket içi Active Directory'nizde UPN olarak kullanılan yönlendirilemeyen e-posta adresi
<a name="BKMK_ADNote"> </a>

Şirket içi Active Directory'nizi Microsoft ile eşitlemeyi planlıyorsanız, Active Directory kullanıcı asıl adı (UPN) son ekinin @contoso.local gibi desteklenmeyen bir etki alanı son eki değil geçerli bir etki alanı son eki olduğundan emin olun. UPN sonekinizi değiştirmeniz gerekirse bkz. Yönlendirilebilir olmayan etki alanını [dizin eşitlemesi için hazırlama](../../enterprise/prepare-a-non-routable-domain-for-directory-synchronization.md).
  
> [!NOTE]
>  Genellikle, DNS değişikliklerinin etkili olması yaklaşık 15 dakika sürer. Bununla birlikte, yaptığınız değişikliğin İnternet'in DNS sistemi genelinde güncelleştirilmesi bazen daha uzun sürebilir. DNS kayıtlarını ekledikten sonra posta akışı sorunlarıyla veya başka sorunlarla karşılaşırsanız, [Etki alanı adınızı veya DNS kayıtlarınızı değiştirdikten sonra sorunları giderme](../get-help-with-domains/find-and-fix-issues.md) konusuna bakın. 

## <a name="related-content"></a>İlgili içerik

[Etki alanını Micrsoft 365'den başka bir ana bilgisayara aktarma](../get-help-with-domains/transfer-a-domain-from-microsoft-to-another-host.md) (makale)\
[Özel Microsoft 365 alanımdan pilot uygulama](../misc/pilot-microsoft-365-from-my-custom-domain.md) (makale)\
[Etki Alanları SSS](../setup/domains-faq.yml) (makale)