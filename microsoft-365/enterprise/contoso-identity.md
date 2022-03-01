---
title: Contoso Corporation'ın kimliği
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Contoso' un Hizmet Olarak Identity'den (IDaaS) yararlanması ve çalışanları ve müşterileri için bulut tabanlı kimlik doğrulaması ve şirket genel kimlik doğrulaması gibi özellikleri nasıl sağladığını.
ms.openlocfilehash: 1e1fb2a74c3c3b491ddfda2b0b88e4ad11926a5a
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63016471"
---
# <a name="identity-for-the-contoso-corporation"></a>Contoso Corporation'ın kimliği

Microsoft, Azure Active Directory (Azure AD) aracılığıyla bulut tekliflerine Hizmet olarak Identity (IDaaS) sunar. Kuruluşta Microsoft 365 için Contoso IDaaS çözümünün şirket içi kimlik sağlayıcılarını kullanmaları ve var olan güvenilen üçüncü taraf kimlik sağlayıcılarıyla şirket içi kimlik doğrulamasını içermeleri gerekmektedir.

## <a name="the-contoso-active-directory-domain-services-forest"></a>Contoso Active Directory Etki Alanı Hizmetleri ormanı

Contoso, contosocom için bir alt etki alanı olan tek bir Active Directory Etki Alanı Hizmetleri (AD DS)\. ormanı kullanır ve bunlardan biri dünyanın her bir bölgesi için. Merkez, bölgesel merkez ve uydu ofisleri, yerel kimlik doğrulama ve yetkilendirme için etki alanı denetleyicileri içerir.

Dünyanın farklı yerlerinde bölgesel hub'lar içeren bölgesel etki alanları bulunan Contoso ormanı burada.

:::image type="content" alt-text="Contoso'nun ormanı ve etki alanları dünya çapında." source="../media/contoso-identity/contoso-identity-fig1.png" lightbox="../media/contoso-identity/contoso-identity-fig1.png":::
 
Contoso, iş yüklerinin ve hizmetlerinin kimlik doğrulaması ve yetkilendirmesi için contosocom\. ormanı içinde yer alan hesapları ve Microsoft 365 kullanmaya karar verdi.

## <a name="the-contoso-federated-authentication-infrastructure"></a>Contoso federasyon kimlik doğrulama altyapısı

Contoso şunları sağlar:

- Müşterilerin Microsoft, Facebook veya Google Mail hesaplarını kullanarak şirketin genel web sitesinde oturum açmaları gerekir.
- Satıcılar ve iş ortakları LinkedIn, Salesforce veya Google Mail hesaplarını kullanarak şirketin iş ortağı extranet'inde oturum açın.

Genel bir web sitesi, iş ortağı extranet ve bir dizi Active Directory Federasyon Hizmetleri (AD FS) sunucusu içeren Contoso DMZ'yi burada bulabilirsiniz. DMZ, müşterileri, iş ortaklarını ve İnternet hizmetlerini içeren İnternet'e bağlanır.

![Müşteriler ve iş ortakları için federasyon kimlik doğrulaması için Contoso desteği.](../media/contoso-identity/contoso-identity-fig2.png)
 
DMZ'de AD FS sunucuları, ortak web sitesine erişim için kimlik sağlayıcıları tarafından müşteri kimlik bilgilerinin ve iş ortağı extranet'ine erişim için iş ortağı kimlik bilgilerinin daha kolay kimlik doğrulamasını kolaylaştırır.

Contoso bu altyapıyı tutmaya karar verdi ve bunu müşteriye ve iş ortağı kimlik doğrulamasına adadı. Contoso kimlik mimarları bu altyapının Azure AD [B2B ve B2C](/azure/active-directory/b2b/hybrid-organizations) çözümlerine [dönüştürmesini](/azure/active-directory-b2c/solution-articles) araştırıyor.

## <a name="hybrid-identity-with-password-hash-synchronization-for-cloud-based-authentication"></a>Bulut tabanlı kimlik doğrulama için parola karma eşitlemesi ile karma kimlik

Contoso, bulut kaynaklarını kullanarak kimlik doğrulaması yapmak için şirket içi AD DS Microsoft 365 kullanmak istedi. Parola karma eşitlemesi (PHS) kullanmaya karar verdi.

PHS, şirket içi AD DS ormanı kurumsal abonelik için kullanıcı ve grup hesaplarını ve kullanıcı hesabı parolalarının karma sürümünü kopyalayıp kendi Microsoft 365 kiracılarının Azure AD kiracılarıyla eşitler.

Dizin eşitlemesi yapmak için, Contoso Azure AD Bağlan aracını Paris veri merkezinde bir sunucuda dağıtdı.

Burada, Değişiklikler için Contoso AD DS Bağlan yoklama yaparken ve bu değişiklikleri Azure AD kiracısı ile eşitleyerek Azure AD'nin çalıştır olduğu sunucu ve vardır.

![Contoso PHS dizin eşitleme altyapısı.](../media/contoso-identity/contoso-identity-fig4.png)
 
## <a name="conditional-access-policies-for-zero-trust-identity-and-device-access"></a>Sıfır Güven kimliği ve cihaz erişimi için Koşullu Erişim ilkeleri

Contoso, üç koruma düzeyi için Azure AD ve Intune [Koşullu Erişim](../security/office-365-security/identity-access-policies.md) ilkeleri kümesi oluşturdu:

- *Başlangıç noktası* korumaları tüm kullanıcı hesapları için geçerlidir.
- *Enterprise* korumaları üst düzey liderlik ekibi ve üst düzey personel için geçerlidir.
- *Özel güvenlik korumaları* , yüksek düzenlemeye tabi verilere erişimi olan finans, hukuk ve araştırma departmanlarında belirli kullanıcılar için geçerlidir.

Sonuçta elde edilen Contoso kimliği ve cihaz Koşullu Erişim ilkeleri kümesi şu şekildedir.

:::image type="content" alt-text="Contoso'nun kimliği ve cihazı Koşullu Erişim ilkeleri." source="../media/contoso-identity/contoso-identity-fig5.png" lightbox="../media/contoso-identity/contoso-identity-fig5.png":::
 
## <a name="next-step"></a>Sonraki adım

Contoso'un kuruluş genelinde geçerli Microsoft Endpoint Configuration Manager dağıtmak ve tutmak [için Contoso'Windows 10 Enterprise](contoso-win10.md) altyapısını nasıl kullandığını öğrenin.

## <a name="see-also"></a>Ayrıca bkz.

[Dağıtım kimliği Microsoft 365](deploy-identity-solution-overview.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Test laboratuvarı kılavuzları](m365-enterprise-test-lab-guides.md)