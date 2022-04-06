---
title: Office 365 için Dış Etki Alanı Adı Sistemi kayıtları
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
description: Office 365 dağıtımı planlarken kullanılacak dış Etki Alanı Adı Sistemi kayıtlarının başvuru listesi.
ms.openlocfilehash: d2c73094da0547fbc02a4520d4361941b829619c
ms.sourcegitcommit: a06bb81fbd727a790a8fe6a3746b8a3cf62a6b24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/05/2022
ms.locfileid: "64651355"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Office 365 için Dış Etki Alanı Adı Sistemi kayıtları

![Etki alanı.](../media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)

**Office 365 kuruluşunuz için dns kayıtlarının özelleştirilmiş bir listesini görmek mi istiyorsunuz?** Etki [alanınız için Office 365 DNS kayıtları oluşturmak için ihtiyacınız olan bilgileri](../admin/get-help-with-domains/information-for-dns-records.md) Office 365'de bulabilirsiniz.

**Bu kayıtları goDaddy veya eNom gibi etki alanınızın DNS ana bilgisayarına eklemek için adım adım yardıma mı ihtiyacınız var?** [Birçok popüler DNS ana bilgisayar için adım adım yönergelerin bağlantılarını bulun](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

**Kendi özel dağıtımınız için başvuru listesini kullanmak için mi takılıyorsunuz?** Aşağıdaki liste, özel Office 365 dağıtımınız için başvuru olarak kullanılmalıdır. Kuruluşunuza hangi kayıtların uygulanacağını seçmeniz ve uygun değerleri doldurmanız gerekir.

**Office 365** [için Ağ planlama ve performans ayarlama'ya Geri dön](./network-planning-and-performance.md).

Genellikle SPF ve MX kayıtları en zor olanıdır. Bu makalenin sonunda SPF kayıtları kılavuzumuzu güncelleştirdik. Hatırlamanız gereken önemli şey _, etki alanınız için yalnızca tek bir SPF kaydına sahip olabileceğinizdir_. Birden çok MX kaydınız olabilir; ancak bu, posta teslimi için sorunlara neden olabilir. E-postayı tek bir posta sistemine yönlendiren tek bir MX kaydına sahip olmak birçok olası sorunu ortadan kaldırır.
  
Aşağıdaki bölümler Office 365'de hizmete göre düzenlenmiştir. Etki alanınız için Office 365 DNS kayıtlarının özelleştirilmiş listesini görmek için Office 365 oturum açın ve [Office 365 DNS kayıtlarını oluşturmak için ihtiyacınız olan bilgileri toplayın](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>Office 365 için gereken dış DNS kayıtları (çekirdek hizmetler)
<a name="BKMK_ReqdCore"> </a>

TXT kaydı, etki alanının sahibi olduğunuzu kanıtlamak için gereklidir ve tüm müşteriler için gereklidir.

CNAME kaydı yalnızca [21Vianet tarafından sağlanan Office 365](/microsoft-365/admin/services-in-china/services-in-china) kullanan müşteriler için gereklidir. Office 365 uygun kimlik platformuyla kimlik doğrulaması için iş istasyonlarını yönlendirebilmesini sağlar. 


  
|**DNS kaydı** <br/> |**Amaç** <br/> |**Kullanılacak değer** <br/> |**Uygulandığı öğe**|
|----------|-----------|------------|------------|
|**TXT** <br/> **(Etki alanı doğrulaması)** <br/> |Office 365 tarafından yalnızca etki alanınızın sahibi olduğunuzu doğrulamak için kullanılır. Başka hiçbir şeyi etkilemez.  <br/> |**Ana bilgisayar:** @ (veya bazı DNS barındırma sağlayıcıları için etki alanı adınız)  <br/> **TXT Değeri:** Office 365 _tarafından sağlanan bir metin dizesi_  <br/> Office 365 **etki alanı kurulum sihirbazı**, bu kaydı oluşturmak için kullandığınız değerleri sağlar.  <br/> |Tüm müşteriler|
|**CNAME** <br/> **(Paket)** <br/> |kimlik doğrulamasını doğru kimlik platformuna yönlendirmek için Office 365 tarafından kullanılır. [Daha fazla bilgi](../admin/services-in-china/purpose-of-cname.md?viewFallbackFrom=o365-worldwide) <br/> Bu CNAME'in yalnızca 21Vianet tarafından sağlanan Office 365 için geçerli olduğunu **unutmayın**. Varsa ve Office 365 21Vianet tarafından çalıştırılmazsa, özel etki alanınızdaki kullanıcılar "*özel etki alanı* sistemimizde yok" hatası alır ve Office 365 lisanslarını etkinleştiremez. [Daha fazla bilgi](/office365/servicedescriptions/office-365-platform-service-description/office-365-operated-by-21vianet) |**Diğer ad:** msoid  <br/> **Hedef:** clientconfig.partner.microsoftonline-p.net.cn  <br/> | Yalnızca 21Vianet müşterileri|



## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Office 365 e-posta için gerekli dış DNS kayıtları (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

Office 365'da e-posta birkaç farklı kayıt gerektirir. Tüm müşterilerin kullanması gereken üç birincil kayıt Autodiscover, MX ve SPF kayıtlarıdır.
  
- **Otomatik Bulma kaydı**, istemci bilgisayarların Exchange otomatik olarak bulmasına ve istemciyi düzgün yapılandırmasına olanak tanır.

- **MX kaydı** , diğer posta sistemlerine etki alanınız için e-postanın nereye gönderileceği bildirir. **Not:** E-postanızı Office 365 olarak değiştirdiğinizde, etki alanınızın MX kaydını güncelleştirerek bu etki alanına gönderilen TÜM e-postalar Office 365 gelmeye başlar.  
Yalnızca birkaç e-posta adresini Office 365 olarak değiştirmek mi istiyorsunuz? [Özel etki alanınızda birkaç e-posta adresiyle Pilot Office 365](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7) yapabilirsiniz.

- **SPF için TXT kaydı** , alıcı e-posta sistemleri tarafından e-postanızı gönderen sunucunun sizin onayladığınız bir sunucu olduğunu doğrulamak için kullanılır. Bu, e-posta kimlik sahtekarlığı ve kimlik avı gibi sorunları önlemeye yardımcı olur. Kaydınıza nelerin dahil edileceklerini anlamanıza yardımcı olması için bu makaledeki [SPF için gereken Dış DNS kayıtlarına](external-domain-name-system-records.md#BKMK_SPFrecords) bakın.

Exchange Federasyonu kullanan e-posta müşterileri, tablonun en altında listelenen ek CNAME ve TXT kaydına da ihtiyaç duyar.
  
|**DNS kaydı** <br/> |**Amaç** <br/> |**Kullanılacak değer** <br/> |
|----------|-----------|------------|
|**CNAME** <br/> **(Exchange Online)** <br/> |Outlook istemcilerinin Otomatik Bulma hizmetini kullanarak Exchange Online hizmetine kolayca bağlanmasına yardımcı olur. Otomatik bulma doğru Exchange Server konağı otomatik olarak bulur ve kullanıcılar için Outlook yapılandırılır.  <br/> |**Diğer ad:** Autodiscover  <br/> **Target:** autodiscover.outlook.com  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |Etki alanınız için gelen postayı Office 365'deki Exchange Online hizmetine gönderir.  <br/> **Not:** E-posta Exchange Online aktarıldıktan sonra, eski sisteminize işaret eden MX kayıtlarını kaldırmanız gerekir.   |**Etki alanı:** Örneğin, contoso.com  <br/> **Hedef e-posta sunucusu:**\<MX token\>. mail.protection.outlook.com  <br/> **Yaşam Süresi (TTL) Değeri:** 3600 <br/> **Tercih/Öncelik:** Diğer MX kayıtlarından daha düşük (bu, postanın Exchange Online teslim edilmesini sağlar) - örneğin 1 veya 'düşük'  <br/>  Aşağıdaki adımları izleyerek bilgilerinizi \<MX token\> bulun:  <br/>  Office 365 oturum açın, Office 365 yönetici \> Etki Alanları'na gidin.  <br/>  Etki alanınızın Eylem sütununda Sorunları düzelt'i seçin.  <br/>  MX kayıtları bölümünde Neyi düzeltebilirim?  <br/>  MX kaydınızı güncelleştirmek için bu sayfadaki yönergeleri izleyin.  <br/> [MX önceliği nedir?](../admin/setup/domains-faq.yml) <br/> |
|**SPF (TXT)** <br/> **(Exchange Online)**  <br/> |Başkalarının istenmeyen posta veya başka kötü amaçlı e-postalar göndermek için etki alanınızı kullanmasını önlemeye yardımcı olur. Gönderen ilkesi çerçevesi (SPF) kayıtları, etki alanınızdan e-posta gönderme yetkisine sahip sunucuları tanımlayarak çalışır.  <br/> |[SPF için gereken dış DNS kayıtları](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**TXT** <br/> **(federasyon Exchange)** <br/> |Karma dağıtım için Exchange federasyon için kullanılır.  <br/> |**TXT kaydı 1:** Örneğin, contoso.com ve özel olarak oluşturulan, etki alanına dayanıklı karma metin (örneğin, Y96nu89138789315669824)  <br/> **TXT kaydı 2:** Örneğin, exchangedelegation.contoso.com ve özel olarak oluşturulan, etki alanına dayanıklı karma metin (örneğin, Y3259071352452626169)  <br/> |
|**CNAME** <br/> **(federasyon Exchange)** <br/> |şirketiniz Exchange federasyonu kullanırken otomatik bulma hizmetini kullanarak Outlook istemcilerinin Exchange Online hizmetine kolayca bağlanmasına yardımcı olur. Otomatik bulma doğru Exchange Server konağı otomatik olarak bulur ve kullanıcılarınız için Outlook yapılandırılır.  <br/> |**Diğer ad:** Örneğin, Autodiscover.service.contoso.com  <br/> **Target:** autodiscover.outlook.com  <br/> |


## <a name="external-dns-records-required-for-skype-for-business-online"></a>Skype Kurumsal Online için gereken dış DNS kayıtları
<a name="BKMK_ReqdCore"> </a>

Ağınızın doğru yapılandırıldığından emin olmak için [Office 365 URL'leri ve IP adresi aralıklarını](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO) kullanırken atılması gereken belirli adımlar vardır.

> [!NOTE]
> Bu DNS kayıtları, özellikle belirli federasyon sorunlarının ortaya çıkabileceği karma Teams ve Skype Kurumsal senaryosunda Teams için de geçerlidir.
  
|**DNS kaydı** <br/> |**Amaç** <br/> |**Kullanılacak değer** <br/> |
|----------|-----------|------------|
|**SRV** <br/> **(Skype Kurumsal Online)** <br/> |SIP federasyonunu etkinleştirerek Office 365 etki alanınızın anlık ileti (IM) özelliklerini dış istemcilerle paylaşmasına izin verir. [Office 365 URL'leri ve IP adresi aralıkları](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO) hakkında daha fazla bilgi edinin.  <br/> |**Hizmet:** sipfederationtls  <br/> **Protokolü:** TCP  <br/> **Öncelik:** 100  <br/> **Ağırlık:** 1  <br/> **Bağlantı noktası:** 5061  <br/> **Hedef:** sipfed.online.lync.com  <br/> **Not:** Güvenlik duvarı veya ara sunucu dış DNS'de SRV aramalarını engelliyorsa, bu kaydı iç DNS kaydına eklemeniz gerekir.   |
|**SRV** <br/> **(Skype Kurumsal Online)** <br/> |lync istemcileri arasındaki bilgi akışını koordine etmek için Skype Kurumsal tarafından kullanılır.  <br/> |**Hizmet:** sip  <br/> **Protokolü:** TLS  <br/> **Öncelik:** 100  <br/> **Ağırlık:** 1  <br/> **Bağlantı noktası:** 443  <br/> **Hedef:** sipdir.online.lync.com  <br/> |
|**CNAME** <br/> **(Skype Kurumsal Online)** <br/> |Skype Kurumsal Online hizmetini bulmanıza ve oturum açmanıza yardımcı olması için Lync istemcisi tarafından kullanılır.  <br/> |**Diğer ad:** sip  <br/> **Hedef:** sipdir.online.lync.com  <br/> Daha fazla bilgi için bkz. [URL'leri ve IP adresi aralıklarını Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |
|**CNAME** <br/> **(Skype Kurumsal Online)** <br/> |Skype Kurumsal Online hizmetini bulmanıza ve oturum açmanıza yardımcı olması için Lync mobil istemcisi tarafından kullanılır.  <br/> |**Diğer ad:** lyncdiscover  <br/> **Hedef:** webdir.online.lync.com  <br/> |

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Office 365 Tek Sign-On için gereken dış DNS kayıtları
<a name="BKMK_ReqdCore"> </a>

|**DNS kaydı** <br/> |**Amaç** <br/> |**Kullanılacak değer** <br/> |
|----------|-----------|------------|
|**Konak (A)** <br/> |Çoklu oturum açma (SSO) için kullanılır. Şirket içi kullanıcılarınızın (ve isterseniz şirket içi kullanıcılarınızın) Active Directory Federasyon Hizmetleri (AD FS) (AD FS) federasyon sunucusu proxy'lerinize veya yük dengeli sanal IP'nize (VIP) bağlanması için uç noktayı sağlar.  <br/> |**Hedef:** Örneğin, sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>SPF için gereken dış DNS kayıtları
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> SPF kimlik sahtekarlığını önlemeye yardımcı olmak için tasarlanmıştır, ancak SPF’nin koruma sağlayamayacağı bazı kimlik sahtekarlığı yöntemleri vardır. Bunlara karşı koruma sağlamak için SPF'yi ayarladıktan sonra DKIM ve DMARC'yi Office 365 için de yapılandırmanız gerekir. Başlamak için bkz. [Office 365'da etki alanınızdan gönderilen giden e-postayı doğrulamak için DKIM kullanma](../security/office-365-security/use-dkim-to-validate-outbound-email.md). Ardından bkz. [Office 365'da e-postayı doğrulamak için DMARC kullanma](../security/office-365-security/use-dmarc-to-validate-email.md).
  
SPF kayıtları, başkalarının istenmeyen posta veya başka kötü amaçlı e-postalar göndermek için etki alanınızı kullanmasını önlemeye yardımcı olan TXT kayıtlarıdır. Gönderen ilkesi çerçevesi (SPF) kayıtları, etki alanınızdan e-posta gönderme yetkisine sahip sunucuları tanımlayarak çalışır.
  
Etki alanınız için yalnızca bir SPF kaydınız (yani SPF'yi tanımlayan bir TXT kaydı) olabilir. Bu tek kayıt birkaç farklı eklemeye sahip olabilir, ancak sonuçta elde edilen toplam DNS araması 10'dan fazla olamaz (bu, hizmet reddi saldırılarının önlenmesine yardımcı olur). Ortamınız için doğru SPF kayıt değerlerini oluşturmanıza veya güncelleştirmenize yardımcı olması için aşağıdaki tabloya ve diğer örneklere bakın.
  
### <a name="structure-of-an-spf-record"></a>SPF kaydının yapısı

Tüm SPF kayıtları üç bölümden oluşur: bunun bir SPF kaydı olduğu bildirimi, e-posta göndermesi gereken etki alanları ve IP adresleri ve bir zorlama kuralı. Üçünü de geçerli bir SPF kaydında kullanmanız gerekir. Yalnızca Exchange Online e-posta kullandığınızda Office 365 için yaygın bir SPF kaydı örneği aşağıda verilmişti:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

Etki alanınızdan e-posta alan bir e-posta sistemi SPF kaydına bakar ve iletiyi gönderen e-posta sunucusu bir Office 365 sunucusuysa, ileti kabul edilir. İletiyi gönderen sunucu eski posta sisteminiz veya İnternet'te kötü amaçlı bir sistemse, örneğin SPF denetimi başarısız olabilir ve ileti teslim edilmeyebilir. Bu tür denetimler kimlik sahtekarlığı ve kimlik avı iletilerini önlemeye yardımcı olur.
  
### <a name="choose-the-spf-record-structure-you-need"></a>İhtiyacınız olan SPF kayıt yapısını seçin

Yalnızca Office 365 için Exchange Online e-posta kullanmadığınız senaryolar için (örneğin, SharePoint Online'dan gelen e-postayı kullandığınızda), kaydın değerine ne ekleneceğini belirlemek için aşağıdaki tabloyu kullanın.
  
> [!NOTE]
> Güvenlik duvarınız genelinde e-posta trafiğini yönetmek için uç e-posta sunucuları gibi karmaşık bir senaryonuz varsa, ayarlamanız gereken daha ayrıntılı bir SPF kaydına sahip olursunuz. Nasıl yapılacağını öğrenin: Kimlik [sahtekarlıklarını önlemeye yardımcı olmak için Office 365'da SPF kayıtlarını ayarlama](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md). Ayrıca, Office 365 [sahtekarlık önlemeye yardımcı olmak için Sender Policy Framework'ün (SPF) nasıl kullanıldığına ilişkin bilgi edinerek SPF'nin](../security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing.md) Office 365 ile nasıl çalıştığı hakkında daha fazla bilgi edinebilirsiniz.
  
| Sayı|Kullanıyorsanız...  <br/> |Amaç  <br/> |Bunları ekleyin  <br/> |
|:-----|:-----|:-----|:-----|
|1  <br/> |Tüm e-posta sistemleri (gerekli)  <br/> |Tüm SPF kayıtları bu değerle başlar  <br/> |v=spf1  <br/> |
|2  <br/> |Exchange Online (ortak)  <br/> |Yalnızca Exchange Online ile kullanın  <br/> |include:spf.protection.outlook.com  <br/> |
|3  <br/> |Üçüncü taraf e-posta sistemi (daha az yaygın)  <br/> ||Içerir:\<email system like mail.contoso.com\>  <br/> |
|4  <br/> |Şirket içi posta sistemi (daha az yaygın)  <br/> |Exchange Online Protection veya Exchange Online artı başka bir posta sistemi kullanıyorsanız kullanın  <br/> |ip4:\<0.0.0.0\>  <br/> ip6:\< : : \>  <br/> Içerir:\<mail.contoso.com\>  <br/> Köşeli ayraç\<\> () içindeki değer, etki alanınız için e-posta gönderecek diğer posta sistemleri olmalıdır.  <br/> |
|5  <br/> |Tüm e-posta sistemleri (gerekli)  <br/> ||-tümü  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>Örnek: Mevcut bir SPF kaydına ekleme
<a name="bkmk_addtospf"> </a>

Zaten bir SPF kaydınız varsa, Office 365 değerlerini eklemeniz veya güncelleştirmeniz gerekir. Örneğin, contoso.com için mevcut SPF kaydınızın şu olduğunu varsayalım:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

Şimdi Office 365 için SPF kaydınızı güncelleştiriyorsunuz. Geçerli kaydınızı düzenleyerek ihtiyacınız olan değerleri içeren bir SPF kaydına sahip olacaksınız. Office 365 için "spf.protection.outlook.com".
  
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

### <a name="more-examples-of-common-spf-values"></a>Yaygın SPF değerlerine daha fazla örnek
<a name="bkmk_addtospf"> </a>

Tam Office 365 paketini kullanıyorsanız ve sizin adınıza pazarlama e-postaları göndermek için MailChimp kullanıyorsanız, contoso.com'daki SPF kaydınız aşağıdaki gibi görünebilir ve yukarıdaki tablodan 1, 3 ve 5. satırlar kullanılır. 1 ve 5. satırların gerekli olduğunu unutmayın.
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

Alternatif olarak, hem Office 365 hem de şirket içi posta sisteminizden e-postanın gönderileceği Exchange Karma yapılandırmanız varsa, contoso.com'deki SPF kaydınız şöyle görünebilir:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

Bunlar, etki alanınızı e-posta için Office 365 eklediğinizde mevcut SPF kaydınızı uyarlamanıza yardımcı olabilecek bazı yaygın örneklerdir. Güvenlik duvarınız genelinde e-posta trafiğini yönetmek için uç e-posta sunucuları gibi karmaşık bir senaryonuz varsa, ayarlamanız gereken daha ayrıntılı bir SPF kaydına sahip olursunuz. Nasıl yapılacağını öğrenin: Kimlik [sahtekarlıklarını önlemeye yardımcı olmak için Office 365'da SPF kayıtlarını ayarlama](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md).
  
İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/o365edns]()
