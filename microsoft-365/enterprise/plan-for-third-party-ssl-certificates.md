---
title: E-posta için üçüncü taraf SSL sertifikalarını Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Özet: Şirket içi ve karma, AD FS Exchange, Exchange Online hizmetleri ve Diğer Web Hizmetleri kullanan SSO için gereken SSL Exchange açıklar.'
ms.openlocfilehash: 8c0bf69090abb87e71f2d51b73405ccf4e54d4bb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988148"
---
# <a name="plan-for-third-party-ssl-certificates-for-microsoft-365"></a>E-posta için üçüncü taraf SSL sertifikalarını Microsoft 365

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

İstemcileriniz ve dış ortam Microsoft 365 iletişimi şifrelemek için, altyapı sunucularınıza üçüncü taraf Güvenli Yuva Katmanı (SSL) sertifikaları yükmalıdır.

Bu makale, proje ayarları [için ağ planlaması ve performans Microsoft 365](./network-planning-and-performance.md).
   
Sertifikalar aşağıdaki veri bileşenleri Microsoft 365 gereklidir:
  
- Exchange şirket içi
    
- Çoklu oturum açma (SSO) (hem Active Directory Federasyon Hizmetleri (AD FS) federasyon sunucuları hem de AD FS federasyon sunucusu sunucuları için)
    
- Exchange Online Bulma, Her Yerden Bulma ve Outlook Web Hizmetleri Exchange hizmetleri
    
- Exchange sunucu
    
## <a name="certificates-for-exchange-on-premises"></a>Şirket İçi Exchange sertifikalar

Şirket içi kuruluşla şirket içi kuruluş arasındaki iletişimi güvenli hale Exchange dijital sertifikaların nasıl kullanmaya Exchange Online genel bakış için, TechNet'te Sertifika Gereksinimlerini Anlama [makalesine bakın](/previous-versions/exchange-server/exchange-141/gg476123(v=exchg.141)).
  
## <a name="certificates-for-single-sign-on"></a>Çoklu Oturum Açma için sertifikalar

Kullanıcılarınıza güçlü bir güvenlik içeren basitleştirilmiş bir çoklu oturum açma deneyimi sağlamak için, aşağıdaki tabloda gösterilen sertifikaların federasyon sunucularında veya federasyon sunucusu sunucularında olması gerekir. Aşağıdaki tablo Active Directory Federasyon Hizmetleri'ne (AD FS) odaklanır, ayrıca üçüncü taraf kimlik sağlayıcıları kullanma [hakkında daha fazla bilgimiz var](/azure/active-directory/hybrid/how-to-connect-fed-compatibility).
  
| Sertifika Türü | Açıklama | Dağıtım öncesinde neleri bilmek gerekir? |
|:-----|:-----|:-----|
|**SSL sertifikası (sunucu kimlik doğrulama sertifikası olarak da adlandırılan)** <br/> |Bu, federasyon sunucuları, istemciler ve federasyon sunucusu ara sunucu bilgisayarları arasındaki iletişimi güvenli hale etmek için kullanılan standart bir SSL sertifikasıdır.  <br/> |AD FS için bir SSL sertifikası gerekir. Varsayılan olarak AD FS, Internet Information Services'de (IIS) varsayılan web sitesi için yapılandırılmış SSL Internet Information Services kullanır.  <br/> Bu SSL sertifikasının konu adı, dağıtan her AD FS örneğinin Federasyon Hizmeti (FS) adını belirlemek için kullanılır. Sertifika yetkilisi (CA) tarafından verilen tüm yeni sertifikalar için, bu sertifikalara sahip olmak istediğiniz şirketin veya kuruluşun adını en iyi şekilde temsil eden bir konu Microsoft 365. Bu adın İnternet'e yönlendirilebilir olması gerekir.  <br/>**Dikkat:** AD FS, bu SSL sertifikasının konu adı noktasız (kısa ad) olmadığını gerektirir.          <br/> **Öneri:** Bu sertifikaya AD FS istemcileri tarafından güveni olması gerekir, çünkü ortak (üçüncü taraf) CA veya genel olarak güvenilen bir kökün alt adı olan bir CA tarafından verilen SSL sertifikasını öneririz; örneğin, VeriSign veya Thawte.  <br/> |
|**Belirteç imzalama sertifikası** <br/> |Bu, federasyon sunucusunun sorun kullandığı ve sunucu tarafından kabul edilen ve doğrulayan tüm belirteçleri güvenli bir şekilde imzalamak için Microsoft 365 standart bir X.509 sertifikasıdır.  <br/> |Belirteç imzalama sertifikası, FS'de güvenilir bir köke zincirler olan bir özel anahtar içeriyor olabilir. Varsayılan olarak, AD FS otomatik olarak imzalanan bir sertifika oluşturur. Bununla birlikte, kurumnizin gereksinimlerine bağlı olarak, AD FS yönetim ek bileşenini kullanarak bu sertifikayı CA tarafından verilen bir sertifikaya değiştirebilirsiniz.  <br/>**Dikkat:** Belirteç imzalama sertifikası, FS kararlılığı açısından çok önemlidir. Sertifika değiştirilirse, Microsoft 365 hakkında bu değişikliğin bildirmiş olması gerekir. Bildirim sağlanmazsa, kullanıcılar kendi müşteri hizmetleri tekliflerinde Microsoft 365 oturum açmaz.<br/>**Öneri:** AD FS tarafından oluşturulan otomatik olarak imzalanan belirteç imzalama sertifikasını öneririz. Bunu yaparak, bu sertifikayı sizin için varsayılan olarak yönetir. Örneğin, bu sertifikanın süresinin dolmak üzere olduğu zaman, AD FS yeni bir otomatik olarak imzalanan sertifika oluşturacak.  <br/> |
   
Federasyon sunucusu sunucu sunucularında, aşağıdaki tabloda açıklanan sertifika gerekir.
  
| Sertifika Türü | Açıklama | Dağıtım öncesinde neleri bilmek gerekir? |
|:-----|:-----|:-----|
|SSL sertifikası  <br/> |Bu, federasyon sunucusu, federasyon sunucusu ara sunucu ve İnternet istemci bilgisayarları arasındaki iletişimin güvenliğini sağlamak için kullanılan standart bir SSL sertifikasıdır.  <br/> |AD FS Federasyon Sunucusu Ara Sunucu Yapılandırması sihirbazını başarıyla çalıştıramadan önce bu SSL sertifikasının IIS'de varsayılan web sitesine bağlı olması gerekir.  <br/> Bu sertifikanın konu adı, şirket ağının federasyon sunucusunda yapılandırılmış olan SSL sertifikasıyla aynı olmalıdır.  <br/> **Öneri:** Bu federasyon sunucusu ara sunucusunun bağlandığı federasyon sunucusunda yapılandırılan aynı sunucu kimlik doğrulama sertifikasını öneririz.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>Otomatik Bulma, Her Yerden Outlook Active Directory Eşitlemesi için sertifikalar

Dış dış Exchange 2013, Exchange 2010, Exchange 2007 ve Exchange 2003 İstemci Erişimi sunucularınıza (CASs), Otomatik Bulma, Outlook Her Yerden ve Active Directory eşitleme hizmetlerinin güvenli bağlantıları için bir üçüncü taraf SSL sertifikası gerekir. Bu sertifikayı şirket içi ortamınıza zaten yüklemişsiniz olabilir.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Karma Sunucu Exchange sertifikası

Dış hizmete Exchange karma sunucunuza veya sunucularınıza, Exchange Online hizmetiyle güvenli bağlantı için bir üçüncü taraf SSL sertifikası gerekir. Bu sertifikayı üçüncü taraf SSL sağlayıcınızdan alımalısınız.
  
## <a name="microsoft-365-certificate-chains"></a>Microsoft 365 Zincirleri

Bu makalede, altyapınıza yüklemeniz gereksinsin tüm sertifikalar açıklanmıştır. Birden fazla sunucumuza yüklenmiş olan sertifikalar hakkında daha fazla Microsoft 365 bkz. [Sertifika Zincirleri Microsoft 365 e bakın](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).
  
## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Kurumsal genel bakış](microsoft-365-overview.md)