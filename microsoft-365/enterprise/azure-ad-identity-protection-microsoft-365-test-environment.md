---
title: Kurumsal test ortamı için Microsoft 365 için Azure AD Kimlik Koruması
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Azure AD Kimlik Koruması'nı yapılandırın ve kurumsal test ortamı için Microsoft 365 geçerli hesapları analiz edin.
ms.openlocfilehash: 1f947f9b74b1909aa1e6451ec835a2ad78964f75
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078767"
---
# <a name="azure-ad-identity-protection-for-your-microsoft-365-for-enterprise-test-environment"></a>Kurumsal test ortamı için Microsoft 365 için Azure AD Kimlik Koruması

*Bu Test Laboratuvarı Kılavuzu yalnızca kurumsal test ortamları için Microsoft 365 için kullanılabilir.*

Kuruluşunuzun kimliklerini etkileyen olası güvenlik açıklarını algılamak, otomatik yanıtları yapılandırmak ve olayları araştırmak için Azure Active Directory (Azure AD) Kimlik Koruması'nı kullanabilirsiniz. Bu makalede, test ortamı hesaplarınızın analizini görüntülemek için Azure AD Kimlik Koruması'nın nasıl kullanılacağı açıklanmaktadır.

Kurumsal test ortamı için Microsoft 365 Azure AD Kimlik Koruması'nın ayarlanması iki aşamadan oluşur:

- [1. Aşama: Kurumsal test ortamı için Microsoft 365 oluşturma](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [2. Aşama: Azure AD Kimlik Koruması kullanma](#phase-2-use-azure-ad-identity-protection)

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınındaki Microsoft 365 tüm makalelere yönelik görsel bir harita için [kurumsal Test Laboratuvarı Kılavuzu Yığını için Microsoft 365](../downloads/Microsoft365EnterpriseTLGStack.pdf) bölümüne gidin.
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>1. Aşama: Kurumsal test ortamı için Microsoft 365 oluşturma

Azure AD Identity Protection'ı yalnızca minimum gereksinimlerle basit bir şekilde test etmek istiyorsanız [Basit temel yapılandırma](lightweight-base-configuration-microsoft-365-enterprise.md) yönergelerini izleyin.
  
Azure AD Identity Protection'ı sanal bir kuruluşta test etmek istiyorsanız [Doğrudan kimlik doğrulaması](pass-through-auth-m365-ent-test-environment.md) başlığı altında yer alan yönergeleri izleyin.
  
> [!NOTE]
> Azure AD Kimlik Koruması'nın testinde, İnternet'e bağlı bir sanal intranet ve bir Active Directory Domain Services (AD DS) ormanı için dizin eşitlemesi içeren sanal kurumsal test ortamı gerekmez. Burada, Azure AD Kimlik Koruması'nın test edebilmesi ve tipik bir kuruluşu temsil eden bir ortamda denemeler yapabileceğiniz bir seçenek olarak sağlanır.
  
## <a name="phase-2-use-azure-ad-identity-protection"></a>2. Aşama: Azure AD Kimlik Koruması kullanma

1. Tarayıcınızın özel bir örneğini açın ve kurumsal test ortamı için Microsoft 365 [https://portal.azure.com](https://portal.azure.com) genel yönetici hesabıyla adresinden Azure portal oturum açın.
2. Azure portal arama kutusuna **kimlik koruması** yazın ve **ardından Azure AD Kimlik Koruması'nı** seçin.
3. **Kimlik Koruması - Genel Bakış** dikey penceresinde raporun ne bildirdiğini görmek için her bir raporu seçin.
4. **Bildir'in** altında Risk **altındaki kullanıcılar algılanan uyarılar'ı** seçin.
5. **Risk altındaki kullanıcılar algılanan uyarılar** bölmesinde **Orta'yı** seçin.
6. **E-postalar aşağıdaki kullanıcılara gönderilirse****, Dahil Edilen'i** seçin ve genel yönetici hesabınızın seçili üyeler listesinde olduğunu doğrulayın.
7. **Kaydet**'i seçin.

**Koru** altında, bunları nasıl yapılandıracaklarını görmek için çeşitli ilkeleri seçin. İlke oluşturur ve etkinleştirirseniz, ilkenin tüm kullanıcılar için erişimi engellemediğinden veya oturum açamadığınızdan emin olun. Bunu önlemek için genel yöneticiler gibi belirli kullanıcı hesaplarını hariç tutun.

Daha fazla test ve deneme için bkz. [Risk olaylarını simüle etme](/azure/active-directory/active-directory-identityprotection-playbook).

## <a name="next-step"></a>Sonraki adım

Test ortamınızdaki ek [kimlik](m365-enterprise-test-lab-guides.md#identity) özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Kimliği dağıtma](deploy-identity-solution-overview.md)

[Kurumsal Test Laboratuvarı Kılavuzları için Microsoft 365](m365-enterprise-test-lab-guides.md)

[Microsoft 365 Kurumsal’a genel bakış](microsoft-365-overview.md)

[Kurumsal belgeler için Microsoft 365](/microsoft-365-enterprise/)