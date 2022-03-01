---
title: Kurumsal test ortamınız için Microsoft 365 Azure AD Identity Protection
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Azure AD Identity Protection'ı yapılandırma ve kurumsal test ortamı için Microsoft 365 hesapları çözümleme.
ms.openlocfilehash: 210736e0a950d74e0cd761463e9cc27f1dc3c721
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63014386"
---
# <a name="azure-ad-identity-protection-for-your-microsoft-365-for-enterprise-test-environment"></a>Kurumsal test ortamınız için Microsoft 365 Azure AD Identity Protection

*Bu Test Laboratuvarı Kılavuzu yalnızca kurumsal test Microsoft 365 test ortamları için kullanılabilir.*

Azure Active Directory kimliklerini etkileyen, otomatik yanıtları yapılandıran ve olayları araştıran olası güvenlik açıklarını belirlemek için Azure Active Directory (Azure AD) Kimlik Koruması'nın kullanabilirsiniz. Bu makalede, test ortamı hesaplarınızı çözümlemek için Azure AD Kimlik Koruması'nın nasıl kullan kullanımı açıklanmıştır.

Kurumsal test ortamınız için Azure AD Kimlik Microsoft 365'i ayarlama iki aşama gerektirir:

- [Aşama 1: Kurumsal test Microsoft 365 yapınızı oluşturma](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Aşama 2: Azure AD Identity Protection'i kullanma](#phase-2-use-azure-ad-identity-protection)

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınına Microsoft 365 görsel bir harita için Kurumsal Test Laboratuvarı Kılavuzu Yığını [için Microsoft 365'e gidin](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Aşama 1: Kurumsal test Microsoft 365 yapınızı oluşturma

Azure AD Kimlik Koruması'nın minimum gereksinimlerle basit bir şekilde test etmek için Basit temel yapılandırma [yönergelerini izleyin](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Sanal bir kuruluşta Azure AD Identity Protection'ı test etmek için, Geçişli kimlik [doğrulama'daki yönergeleri izleyin](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Azure AD Kimlik Koruması'nın testinde, Active Directory Etki Alanı Hizmetleri (AD DS) ormanı için İnternet ve dizin eşitlemeye bağlı sanal bir intranet içeren sanal kurumsal test ortamı gerekli değildir. Burada, Azure AD Kimlik Korumasını test etmek ve normal bir kuruluşu temsil eden ortamda bu korumayla denemeler yapmak için bir seçenek olarak sağlanır.
  
## <a name="phase-2-use-azure-ad-identity-protection"></a>Aşama 2: Azure AD Identity Protection'i kullanma

1. Tarayıcınızın özel bir örneğini açın ve kurumsal test ortamı için tarayıcınızın genel yönetici hesabıyla Azure portalında [https://portal.azure.com](https://portal.azure.com) Microsoft 365 açın.
2. Azure portalında, arama **kutusuna kimlik korumasını** yazın ve Azure **AD Kimlik Koruması'ı seçin**.
3. Kimlik Koruması **- Genel Bakış** blade'inde, ne raporlaması olduğunu görmek için raporları seçin.
4. **Bildir'in** altında **, Algılanan risk altındaki uyarılar için Kullanıcılar'ı seçin**.
5. Risk altında **olan kullanıcılar uyarı bölmesinde Orta'ya** **tıklayın**.
6. **E-postalar aşağıdaki kullanıcılara gönderilirse, Dahil'i** seçin ve genel yönetici hesabınızı seçili üyeler listesinde olduğunu doğrulayın.
7. **Kaydet**'i seçin.

**Koruma'nın** altında, nasıl yapılandırılanları görmek için çeşitli güvenlik güvenliklerini seçin. Bir ilkeyi oluşturduk ve etkinleştirirseniz, bu ilkenin tüm kullanıcılar için erişimi engellemey olduğundan emin olun; yoksa oturum açmanız mümkün değildir. Bunu önlemek için, genel yöneticiler gibi belirli kullanıcı hesaplarını dahil edin.

Daha fazla test ve deneme yapmak için bkz [. Risk olaylarını simüle etme](/azure/active-directory/active-directory-identityprotection-playbook).

## <a name="next-step"></a>Sonraki adım

Test [ortamınıza](m365-enterprise-test-lab-guides.md#identity) başka kimlik özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Kimliği dağıtma](deploy-identity-solution-overview.md)

[Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar](m365-enterprise-test-lab-guides.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Microsoft 365 belgeleri için belgeler](/microsoft-365-enterprise/)