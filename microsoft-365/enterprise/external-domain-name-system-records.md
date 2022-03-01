---
title: Etki Alanı için Dış Etki Alanı Adı Sistemi Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/10/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0
description: Dış Etki Alanı Adı Sistemi kayıtlarının, dağıtım planlama ve dağıtım planlarında Office 365 listesi.
ms.openlocfilehash: 39b6f093c196d8b696a8d36458d2ebc18be2a5f2
ms.sourcegitcommit: e246725b0935067aad886530d5178972c0f895d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2021
ms.locfileid: "63012866"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Etki Alanı için Dış Etki Alanı Adı Sistemi Office 365

![Etki alanı.](../media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)

**Office 365 için DNS kayıtlarının özelleştirilmiş bir listesini mi görmek Office 365 istiyor musunuz?** Kendi etki [alanınız için DNS kayıtlarını oluşturmak Office 365 bilgileri](../admin/get-help-with-domains/information-for-dns-records.md) Kendi Ayarları'Office 365.

**Bu kayıtları etki alanı DNS barındırma barındıranıza (GoDaddy veya eNom gibi) eklemek için adım adım yardıma mı ihtiyacınız var?** [Birçok popüler DNS barındırması için adım adım yönergelerin bağlantılarını bulun](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

**Kendi özel dağıtımınız için başvuru listesini mi kullanmaktasınız?** Aşağıdaki liste, özel dağıtım dağıtım için başvuru olarak Office 365 kullanılmalıdır. Organizasyonunıza hangi kayıtların geçerli olduğunu seçmeniz ve uygun değerleri doldurmanız gerekir.

**Daha fazla bilgi** [için ağ planlaması ve performans ayarı Office 365](./network-planning-and-performance.md).

SPF ve MX kayıtları çoğunlukla en zor olan kayıttır. Bu makalenin sonundaki SPF kayıtları kılavuzumızı güncelledik. Etki alanınız için yalnızca _tek bir SPF kaydına sahip olaynizi unutmamanız gerekir_. Birden çok MX kaydına sahip olabilirsiniz; Bununla birlikte, bu da posta teslim sorunlarına neden olabilir. E-postaları tek bir posta sistemine yönlendiren tek bir MX kaydınız olması birçok olası sorunu ortadan kaldırır.
  
Aşağıdaki bölümler, her bölümde hizmetlere göre Office 365. Etki alanınız için Office 365 DNS kayıtlarının özelleştirilmiş bir listesini görmek için, Office 365'de oturum açma ve DNS kayıtlarınızı oluşturmak için [Office 365 toplayın](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>Hizmetler (temel hizmetler) Office 365 dış DNS kayıtları
<a name="BKMK_ReqdCore"> </a>

Her Office 365 dış DNS'lerine iki kayıt eklemesi gerekir. İlk CNAME kaydı, uygun Office 365 platformuyla kimlik doğrulaması yapılması için iş istasyonlarına yönlendirilmalerini sağlar. İkinci gerekli kayıt, etki alanı adınızın size ait olduğunu kanıtlamaktır.
  
|**DNS kaydı** <br/> |**Amaç** <br/> |**Value to use** <br/> |
|----------|-----------|------------|
|**CNAME** <br/> **(Paket)** <br/> |Kimlik doğrulama Office 365 doğru kimlik platformuna yönlendirecek şekilde kullanıcı tarafından kullanılır. [Daha fazla bilgi](../admin/services-in-china/purpose-of-cname.md?viewFallbackFrom=o365-worldwide) <br/> **Not:** Bu CNAME yalnızca 21Vianet Office 365 için geçerlidir. Mevcut olan ve Office 365 21Vianet tarafından çalıştırnını değilse, özel etki alanınız üzerinde çalışan *kullanıcılar "özel* etki alanı sistemimizte değil" hatasını alırlar ve Office 365 lisanslarını etkinleştiremz. [Daha fazla bilgi](/office365/servicedescriptions/office-365-platform-service-description/office-365-operated-by-21vianet) |**Diğer Ad:** msoid  <br/> **Hedef:** clientconfig.partner.microsoftonline-p.net.cn  <br/> |
|**TXT** <br/> **(Etki alanı doğrulaması)** <br/> |Etki Office 365 etki alanının sahibi olduğunu doğrulamak için etki alanı tarafından kullanılır. Başka bir şeyi etkilemez.  <br/> |**Ana bilgisayar:** @ (veya bazı DNS barındırma sağlayıcıları için etki alanı adınız)  <br/> **TXT Değeri:** _Metin kutusu tarafından sağlanan_ Office 365  <br/> Bu Office 365 **oluşturmak için** kullanabileceğiniz değerleri etki alanı kurulum sihirbazı sağlar.  <br/> |


## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>e-posta için gereken dış DNS Office 365 (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

E-posta Office 365 birkaç farklı kayıt gerektirir. Tüm müşterilerin kullanmaları gereken üç birincil kayıt Otomatik Bulma, MX ve SPF kayıtlarıdır.
  
- **Otomatik Bulma kaydı, istemci bilgisayarların** otomatik olarak bağlantı bulmalarına ve Exchange şekilde yapılandırmalarına olanak sağlar.

- **MX kaydı, diğer** posta sistemlerine etki alanınız için e-postayı nereye göndereceklerini söyler. **Not:** E-postanızı E-posta Office 365, etki alanının MX kaydını güncelleştirerek bu etki alanına gönderilen TÜM e-postaların E-postası adresine Office 365.  
Yalnızca birkaç e-posta adresini başka bir adrese mi Office 365? Özel etki [Office 365 birkaç e-posta adresiyle pilot e-posta gönderebilirsiniz](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7).

- **SPF için TXT kaydı** , alıcı e-posta sistemleri tarafından e-postanızı gönderen sunucunun sizin onaylayan sunuculardan biri olduğunu doğrulamak için kullanılır. Bu, kimlik avı ve e-posta kimlik avı gibi sorunları önlemeye yardımcı olur. Kaydınıza [neleri dahil edeceklerini anlamanıza yardımcı](external-domain-name-system-records.md#BKMK_SPFrecords) olması için bu makalede SPF için gereken Dış DNS kayıtlarına bakın.

Federasyon kullanan e-Exchange e-posta müşterilerinin ayrıca tablonun altında listelenen CNAME ve TXT kayıtlarına da ihtiyacı olur.
  
|**DNS kaydı** <br/> |**Amaç** <br/> |**Value to use** <br/> |
|----------|-----------|------------|
|**CNAME** <br/> **(Exchange Online)** <br/> |Diğer Outlook Otomatik Bulma hizmetini kullanarak istemcilerin Exchange Online kolay bağlanmalarını sağlar. Otomatik Bulma, ana bilgisayar için Exchange Server doğru ana bilgisayarı otomatik olarak bulur Outlook yapılandırdı.  <br/> |**Diğer Ad:** Otomatik Bulma  <br/> **Target:** autodiscover.outlook.com  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |Posta, etki alanınız için gelen Exchange Online hizmet Office 365.  <br/> **Not:** E-posta bir Exchange Online, eski sisteminize işaret ediyor olan MX kayıtlarını kaldırmanız gerekir.   |**Etki alanı:** Örneğin, contoso.com  <br/> **Hedef e-posta sunucusu:**\<MX token\>. mail.protection.outlook.com  <br/> **Tercih/Öncelik:** Diğer tüm MX kayıtlardan daha düşük (bu sayede postanın Exchange Online) - örneğin, 1 veya 'düşük'  <br/>  Aşağıdaki adımları \<MX token\> takip edin:  <br/>  Etki Alanları'Office 365 yönetici Etki Alanları'Office 365 \> gidin.  <br/>  Etki alanınız için Eylem sütununda Sorunları düzelt'i seçin.  <br/>  MX kayıtları bölümünde Neyi düzeltmem gerekiyor? 'ı seçin.  <br/>  MX kaydınızı güncelleştirmek için bu sayfada yönergeleri izleyin.  <br/> [MX önceliği nedir?](../admin/setup/domains-faq.yml) <br/> |
|**SPF (TXT)** <br/> **(Exchange Online)**  <br/> |Diğer kişilerin istenmeyen posta veya diğer kötü amaçlı e-postaları göndermek için etki alanınızı kullanmalarını önlemeye yardımcı olur. Sender Policy Framework (SPF) kayıtları, etki alanınıza e-posta gönderme yetkisi olan sunucuları tanımarak çalışır.  <br/> |[SPF için gereken dış DNS kayıtları](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**TXT** <br/> **(Exchange federasyonu)** <br/> |Karma dağıtımda Exchange federasyonu için kullanılır.  <br/> |**TXT kaydı 1:** Örneğin, contoso.com ve ilişkili olarak oluşturulan, etki alanına karşıt karma metindir (örneğin, Y96nu89138789315669824))  <br/> **TXT kaydı 2:** Örneğin, exchangedelegation.contoso.com oluşturulan ve ilişkilendirilmiş, etki alanına karşıt karma metindir (örneğin, Y3259071352452626169)  <br/> |
|**CNAME** <br/> **(Exchange federasyonu)** <br/> |Şirket Outlook Federasyon kullanırken Otomatik Bulma hizmetini kullanarak Exchange Online hizmetine Exchange kolayca bağlanmalarını sağlar. Otomatik Bulma, otomatik olarak doğru ana Exchange Server ana bilgisayarı bulur ve Outlook için doğru ana bilgisayarı yapılandırr.  <br/> |**Diğer Ad:** Örneğin, Autodiscover.service.contoso.com  <br/> **Target:** autodiscover.outlook.com  <br/> |


## <a name="external-dns-records-required-for-skype-for-business-online"></a>Skype Kurumsal Online için gereken dış DNS kayıtları
<a name="BKMK_ReqdCore"> </a>

Ağın doğru yapılandırıldığından emin olmak [için Office 365 URL'leri ve IP](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO) adresi aralıklarını kullanarak atılması gereken belirli adımlar vardır.

> [!NOTE]
> Bu DNS kayıtları, özellikle de Teams federasyon sorunlarının ortaya çıka Teams Skype Kurumsal karma senaryolarda da geçerlidir.
  
|**DNS kaydı** <br/> |**Amaç** <br/> |**Value to use** <br/> |
|----------|-----------|------------|
|**SRV** <br/> **(Skype Kurumsal Online)** <br/> |SIP Office 365 etkinleştirerek, etki alanınız dış istemcilerle anlık ileti (IM) özelliklerini paylaşmaya olanak sağlar. DAHA fazla bilgi Office 365 [URL'ler ve IP adresi aralıkları](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |**Hizmet:** sipfederationtls  <br/> **Protokol:** TCP  <br/> **Öncelik:** 100  <br/> **Ağırlık:** 1  <br/> **Bağlantı Noktası:** 5061  <br/> **Hedef:** sipfed.online.lync.com  <br/> **Not:** Dış bir DNS'de güvenlik duvarı veya ara sunucu SRV aramalarını engellerse, bu kaydı iç DNS kaydına eklemeniz gerekir.   |
|**SRV** <br/> **(Skype Kurumsal Online)** <br/> |Diğer Skype Kurumsal Lync istemcileri arasındaki bilgi akışını eşgüdüm sağlamak için kullanılır.  <br/> |**Hizmet:** sip  <br/> **Protokol:** TLS  <br/> **Öncelik:** 100  <br/> **Ağırlık:** 1  <br/> **Bağlantı Noktası:** 443  <br/> **Hedef:** sipdir.online.lync.com  <br/> |
|**CNAME** <br/> **(Skype Kurumsal Online)** <br/> |Skype Kurumsal Online hizmetini bulmak ve oturum a Skype Kurumsal için Lync istemcisi tarafından kullanılır.  <br/> |**Diğer Ad:** sip  <br/> **Hedef:** sipdir.online.lync.com  <br/> Daha fazla bilgi için bkz[. Office 365 URL'leri ve IP adresi aralıklarını yapılandırma](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |
|**CNAME** <br/> **(Skype Kurumsal Online)** <br/> |Skype Kurumsal Online hizmetini bulmak ve oturum açmada yardımcı olmak için Lync mobil istemcisi tarafından kullanılır.  <br/> |**Diğer Ad:** lyncdiscover  <br/> **Hedef:** webdir.online.lync.com  <br/> |

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Tek Kayıt Olarak Kayıt Için Office 365 Dış DNS Sign-On
<a name="BKMK_ReqdCore"> </a>

|**DNS kaydı** <br/> |**Amaç** <br/> |**Value to use** <br/> |
|----------|-----------|------------|
|**Ana Bilgisayar (A)** <br/> |Çoklu oturum açma (SSO) için kullanılır. Active Directory Federasyon Hizmetleri (AD FS) federasyon sunucusu lisanslara veya yük dengelemeli sanal IP'nize (VIP) bağlanmaları için şirket dışı kullanıcılarınız (ve  likesanız şirket içi kullanıcılarınız) için bitiş noktası sağlar.  <br/> |**Hedef:** Örneğin, sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>SPF için gereken dış DNS kayıtları
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> SPF, ifadeyi önlemeye yardımcı olmak için tasarlanmıştır ancak SPF'nin koruyamaz olduğu sanallık tekniklerini vardır. Bunlara karşı korunmak için, SPF'yi ayarlamış olduktan sonra, SPF için DKIM ve DMARC'yi de Office 365. Kullanmaya başlamak için bkz[. DkIM kullanarak kendi etki alanınıza gönderilen giden e-postayı Office 365](../security/office-365-security/use-dkim-to-validate-outbound-email.md). Ardından, bkz. [DMARC kullanarak e-postayı doğrulamak için Office 365](../security/office-365-security/use-dmarc-to-validate-email.md).
  
SPF kayıtları, diğer kişilerin istenmeyen posta veya diğer kötü amaçlı e-postaları göndermek için etki alanınızı kullanmalarını önlemeye yardımcı olan TXT kayıtlarıdır. Sender Policy Framework (SPF) kayıtları, etki alanınıza e-posta gönderme yetkisi olan sunucuları tanımarak çalışır.
  
Etki alanınız için yalnızca bir SPF kaydı (başka bir ifadeyle, SPF'yi tanımlayan bir TXT kaydı) bulunabilir. Bu tek kayıt birkaç farklı eklemeye sahip olabilir, ancak sonuçta elde edilen toplam DNS aramaları 10'dan fazla olabilir (bu, hizmet reddi saldırılarını önlemeye yardımcı olur). Ortamınız için doğru SPF kaydı değerlerini oluşturmanıza veya güncelleştirmenize yardımcı olmak için aşağıdaki tabloya ve diğer örneklere bakın.
  
### <a name="structure-of-an-spf-record"></a>SPF kaydının yapısı

Tüm SPF kayıtları üç parça içerir: SPF kaydı olduğu bildirimi, e-postayı gönderecek etki alanları ve IP adresleri ve bir zorlama kuralı. Geçerli bir SPF kaydında bu üçüne de ihtiyacınız var. E-postayla yalnızca bu e-postayı Office 365 için yaygın bir SPF kaydının Exchange Online verilmiştir:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

Etki alanınıza gelen e-postayı alan bir e-posta sistemi SPF kaydına bakarak iletiyi gönderilen e-posta sunucusu Office 365, ileti kabul edilir. İletiyi alan sunucu eski posta sisteminizse veya İnternet'deki kötü amaçlı bir sistemse, örneğin SPF denetimi başarısız olabilir ve ileti teslim edilir olmaz. Bunun gibi denetimler kimlik avı ve kimlik avı iletilerini önlemeye yardımcı olur.
  
### <a name="choose-the-spf-record-structure-you-need"></a>Size gereken SPF kaydı yapısını seçme

Office 365 için yalnızca Exchange Online e-postası kullanmamanızın olduğu senaryolar için (örneğin, SharePoint Online'dan kaynaklanan e-postayı da kullanırken), kayıt değerine nelerin dahil olduğunu belirlemek için aşağıdaki tabloyu kullanın.
  
> [!NOTE]
> Örneğin güvenlik duvarınız üzerinden e-posta trafiğini yönetmek için kenar e-posta sunucularını da içeren karmaşık bir senaryo varsa, daha ayrıntılı bir SPF kaydı ayarlayın. Nasıl olduğunu öğrenin: [SPF kayıtlarının, Office 365 için kayıtlarda SPF ayarlama](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md). Ayrıca, SPF'nin SPF'nin Office 365 birlikte nasıl çalıştığını öğrenmek için Office 365, gönderen ilke çerçevesi [(SPF)](../security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing.md) kullanarak kimliği doğrunlamanın önlenmesine yardımcı olur.
  
| Sayı|Eğer kullanıyorsanız...  <br/> |Amaç  <br/> |Bunları ekleyin:  <br/> |
|:-----|:-----|:-----|:-----|
|1  <br/> |Tüm e-posta sistemleri (gerekli)  <br/> |Tüm SPF kayıtları bu değerle başlar  <br/> |v=spf1  <br/> |
|2  <br/> |Exchange Online (yaygın)  <br/> |Yalnızca tek bir Exchange Online  <br/> |include:spf.protection.outlook.com  <br/> |
|3  <br/> |Üçüncü taraf e-posta sistemi (daha az yaygın)  <br/> ||şunları içerir:\<email system like mail.contoso.com\>  <br/> |
|4  <br/> |Şirket içi posta sistemi (daha az yaygın)  <br/> |Başka bir posta sistemiyle birlikte Exchange Online Protection veya Exchange Online kullanıyorsanız kullanın  <br/> |ip4:\<0.0.0.0\>  <br/> ip6:\< : : \>  <br/> şunları içerir:\<mail.contoso.com\>  <br/> Köşeli ayraç () içindeki\<\> değer, etki alanınız için e-posta gönderecek diğer posta sistemleri olmalıdır.  <br/> |
|5  <br/> |Tüm e-posta sistemleri (gerekli)  <br/> ||-all  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>Örnek: Var olan bir SPF kaydına ekleme
<a name="bkmk_addtospf"> </a>

Zaten bir SPF kaydına sahipsinizse bu kaydın değerlerini eklemeniz veya güncelleştirmeniz Office 365. Örneğin, bu sizin için var olan SPF contoso.com olduğunu var:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

Şimdi de SPF kaydınızı diğer iş Office 365. Size gereken değerleri içeren bir SPF kaydınız olacak şekilde geçerli kaydınızı düzenlersiniz. Daha Office 365 için "spf.protection.outlook.com".
  
Doğru:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com include:smtp.adatum.com -all
```

Yanlış:
  
``` dns
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
Record 2:
Values: v=spf1 include:spf.protection.outlook.com -all
```

### <a name="more-examples-of-common-spf-values"></a>Diğer yaygın SPF değerleri örnekleri
<a name="bkmk_addtospf"> </a>

Tam Office 365 paketini kullanıyorsanız ve sizin adına pazarlama e-postaları göndermek için MailChimp kullanıyorsanız, contoso.com'deki SPF kaydınız yukarıdaki tablodan 1, 3 ve 5. satırları kullanan aşağıdaki gibi olabilir. 1. ve 5. satırların gerekli olduğunu unutmayın.
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

Alternatif olarak, hem Exchange hem de şirket içi posta sisteminden e-postanın gönderll olduğu bir Office 365 Exchange Karma yapılandırmanız varsa, contoso.com'deki SPF kaydınız şu şekilde olabilir:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

Bunlar, etki alanınızı e-posta için Office 365'a eklerken var olan SPF kaydınızı uyarlamanıza yardımcı Office 365 örneklerdir. Örneğin güvenlik duvarınız üzerinden e-posta trafiğini yönetmek için kenar e-posta sunucularını da içeren karmaşık bir senaryo varsa, daha ayrıntılı bir SPF kaydı ayarlayın. Nasıl olduğunu öğrenin: [SPF kayıtlarının, Office 365 için kayıtlarda SPF ayarlama](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md).
  
İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/o365edns]()
