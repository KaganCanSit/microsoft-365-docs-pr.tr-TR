---
title: Microsoft 365 için üçüncü taraf SSL sertifikalarını planlama
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: ITPro
ms.date: 05/15/2019
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 'Özet: Şirket içi ve karma Exchange, AD FS kullanarak SSO, Exchange Online hizmetleri ve Exchange Web Hizmetleri için gereken SSL sertifikalarını açıklar.'
ms.openlocfilehash: 0cd7cce2cd5f0aba8baecab7048d86d629d30427
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100313"
---
# <a name="plan-for-third-party-ssl-certificates-for-microsoft-365"></a>Microsoft 365 için üçüncü taraf SSL sertifikalarını planlama

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

İstemcilerinizle Microsoft 365 ortamı arasındaki iletişimi şifrelemek için, altyapı sunucularınıza üçüncü taraf Güvenli Yuva Katmanı (SSL) sertifikaları yüklenmelidir.

Bu makale, [Microsoft 365 için ağ planlama ve performans ayarlamanın](./network-planning-and-performance.md) bir parçasıdır.
   
Sertifikalar aşağıdaki Microsoft 365 bileşenleri için gereklidir:
  
- Şirket içi Exchange
    
- Çoklu oturum açma (SSO) (hem Active Directory Federasyon Hizmetleri (AD FS) (AD FS) federasyon sunucuları hem de AD FS federasyon sunucusu proxy'leri için)
    
- Otomatik Bulma, Outlook Her Yerde ve Exchange Web Hizmetleri gibi Exchange Online hizmetleri
    
- Karma sunucu Exchange
    
## <a name="certificates-for-exchange-on-premises"></a>şirket içi Exchange için sertifikalar

Şirket içi Exchange kuruluş ile Exchange Online arasındaki iletişimi güvenli hale getirmek için dijital sertifikaları kullanma hakkında genel bir bakış için [Sertifika Gereksinimlerini Anlama](/previous-versions/exchange-server/exchange-141/gg476123(v=exchg.141)) TechNet makalesine bakın.
  
## <a name="certificates-for-single-sign-on"></a>Çoklu Oturum Açma için sertifikalar

Kullanıcılarınıza güçlü güvenlik içeren basitleştirilmiş bir çoklu oturum açma deneyimi sağlamak için, aşağıdaki tabloda gösterilen sertifikalar federasyon sunucularında veya federasyon sunucusu proxy'lerinde gereklidir. Aşağıdaki tabloda Active Directory Federasyon Hizmetleri (AD FS) (AD FS) ele alınmaktadır; [üçüncü taraf kimlik sağlayıcılarını kullanma](/azure/active-directory/hybrid/how-to-connect-fed-compatibility) hakkında daha fazla bilgi de mevcuttur.
  
| Sertifika Türü | Açıklama | Dağıtmadan önce bilmeniz gerekenler |
|:-----|:-----|:-----|
|**SSL sertifikası (sunucu kimlik doğrulama sertifikası olarak da adlandırılır)** <br/> |Bu, federasyon sunucuları, istemciler ve federasyon sunucusu proxy bilgisayarları arasındaki iletişimi güvenli hale getirmek için kullanılan standart bir SSL sertifikasıdır.  <br/> |AD FS bir SSL sertifikası gerektirir. Varsayılan olarak AD FS, Internet Information Services(IIS) içindeki varsayılan web sitesi için yapılandırılan SSL sertifikasını kullanır.  <br/> Bu SSL sertifikasının konu adı, dağıttığınız her AD FS örneğinin Federasyon Hizmeti (FS) adını belirlemek için kullanılır. Microsoft 365 için şirketinizin veya kuruluşunuzun adını en iyi şekilde temsil eden yeni sertifika yetkilisi (CA) tarafından verilen sertifikalar için bir konu adı seçmeyi göz önünde bulundurun. Bu ad İnternet'e yönlendirilebilir olmalıdır.  <br/>**Dikkat:** AD FS, bu SSL sertifikasının noktasız (kısa ad) konu adına sahip olmamasını gerektirir.          <br/> **Öneri:** Bu sertifikanın AD FS istemcileri tarafından güvenilir olması gerektiğinden, genel (üçüncü taraf) CA veya genel olarak güvenilen bir köke bağlı bir CA tarafından verilen bir SSL sertifikası kullanmanızı öneririz; örneğin, VeriSign veya Thawte.  <br/> |
|**Belirteç imzalama sertifikası** <br/> |Bu, federasyon sunucusunun dışarı aktarıp Microsoft 365 kabul edip doğrulayan tüm belirteçleri güvenli bir şekilde imzalamak için kullanılan standart bir X.509 sertifikasıdır.  <br/> |Belirteç imzalama sertifikası, FS'de güvenilir bir köke zincirleyen özel bir anahtar içermelidir. Varsayılan olarak, AD FS otomatik olarak imzalanan bir sertifika oluşturur. Ancak, kuruluşunuzun gereksinimlerine bağlı olarak, AD FS yönetim ek bileşenini kullanarak bu sertifikayı CA tarafından verilen bir sertifikayla değiştirebilirsiniz.  <br/>**Dikkat:** Belirteç imzalama sertifikası, FS'nin kararlılığı açısından kritik öneme sahiptir. Sertifika değiştirilirse, değişiklik Microsoft 365 bildirilmelidir. Bildirim sağlanmazsa, kullanıcılar Microsoft 365 hizmet tekliflerinde oturum açamaz.<br/>**Öneri:** AD FS tarafından oluşturulan otomatik olarak imzalanan belirteç imzalama sertifikasını kullanmanızı öneririz. Bunu yaparak, bu sertifikayı varsayılan olarak sizin için yönetir. Örneğin, bu sertifikanın süresi dolmak üzereyken AD FS yeni bir otomatik olarak imzalanan sertifika oluşturur.  <br/> |
   
Federasyon sunucusu proxy'leri aşağıdaki tabloda açıklanan sertifikayı gerektirir.
  
| Sertifika Türü | Açıklama | Dağıtmadan önce bilmeniz gerekenler |
|:-----|:-----|:-----|
|SSL sertifikası  <br/> |Bu, federasyon sunucusu, federasyon sunucusu ara sunucusu ve İnternet istemci bilgisayarları arasındaki iletişimin güvenliğini sağlamak için kullanılan standart bir SSL sertifikasıdır.  <br/> |AD FS Federasyon Sunucusu Proxy Yapılandırma sihirbazını başarıyla çalıştırabilmeniz için önce bu SSL sertifikası IIS'deki varsayılan web sitesine bağlı olmalıdır.  <br/> Bu sertifika, şirket ağındaki federasyon sunucusunda yapılandırılan SSL sertifikasıyla aynı konu adına sahip olmalıdır.  <br/> **Öneri:** Bu federasyon sunucusu proxy'sinin bağlanıldığı federasyon sunucusunda yapılandırılan sunucu kimlik doğrulama sertifikasını kullanmanızı öneririz.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>Otomatik Bulma, her yerde Outlook ve Active Directory Eşitlemesi için sertifikalar

Dış kullanıma yönelik Exchange 2013, Exchange 2010, Exchange 2007 ve Exchange 2003 İstemci Erişimi sunucularınız (CAS) Otomatik Bulma, Outlook Her Yerde ve Active Directory eşitleme hizmetleri için güvenli bağlantılar için üçüncü taraf bir SSL sertifikası gerektirir. Bu sertifika şirket içi ortamınızda zaten yüklü olabilir.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Exchange Karma Sunucusu için sertifika

Dış Exchange karma sunucunuz veya sunucularınız, Exchange Online hizmetiyle güvenli bağlantı için üçüncü taraf bir SSL sertifikası gerektirir. Bu sertifikayı üçüncü taraf SSL sağlayıcınızdan almanız gerekir.
  
## <a name="microsoft-365-certificate-chains"></a>sertifika zincirlerini Microsoft 365

Bu makalede altyapınıza yüklemeniz gereken sertifikalar açıklanmaktadır. Microsoft 365 sunucularımıza yüklenen sertifikalar hakkında daha fazla bilgi için bkz. [Microsoft 365 Sertifika Zincirleri](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).
  
## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Kurumsal genel bakış](microsoft-365-overview.md)