---
title: Kurumsal test ortamınız için lisans ve grup Microsoft 365 otomatikleştirme
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/09/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Kurumsal test ortamınız için grup tabanlı lisanslama ve dinamik Microsoft 365 üyeliğinizi yapılandırma.
ms.openlocfilehash: cbf10436ded2fbdcbe34c2a0bfa15b0a70a30eeb
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63016451"
---
# <a name="automate-licensing-and-group-membership-for-your-microsoft-365-for-enterprise-test-environment"></a>Kurumsal test ortamınız için lisans ve grup Microsoft 365 otomatikleştirme

*Bu Test Laboratuvarı Kılavuzu yalnızca kurumsal test Microsoft 365 test ortamları için kullanılabilir.*

Grup tabanlı lisanslama, grup üyeliğine göre kullanıcı hesabına otomatik olarak lisans atar veya lisansları kaldırır. Dinamik grup üyeliği, Bölüm veya Ülke gibi kullanıcı hesabı özelliklerine bağlı olarak **gruba üye ekler** veya **kaldırır**. Bu makalede, kurumsal test ortamına projeniz için grup üyelerini ekleme ve kaldırma Microsoft 365 tanıtımları adım adım göstermektedir.

Kurumsal test ortamınız için test ortamınıza otomatik lisanslama Microsoft 365 dinamik grup üyeliğini ayarlama iki aşama içerir:

- [Aşama 1: Kurumsal test Microsoft 365 yapınızı oluşturma](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Aşama 2: Dinamik grup üyeliğini ve otomatik lisansları yapılandırma ve test edin](#phase-2-configure-and-test-dynamic-group-membership-and-automatic-licensing)

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınına Microsoft 365 görsel bir harita için Kurumsal Test Laboratuvarı Kılavuzu Yığını [için Microsoft 365'e gidin](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Aşama 1: Kurumsal test Microsoft 365 yapınızı oluşturma

En düşük gereksinimlerle yalnızca basit bir yolla otomatik lisanslama ve grup üyeliğini test etmek için Basit temel [yapılandırma'daki yönergeleri izleyin](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Sanal bir kuruluşta otomatik lisanslama ve grup üyeliğini test etmek için, Geçişli kimlik [doğrulama'daki yönergeleri izleyin](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Otomatik lisanslama ve grup üyeliğini test etmek, Active Directory Etki Alanı Hizmetleri (AD DS) ormanı için İnternet ve dizin eşitlemeye bağlı sanal bir intranet içeren sanal kurumsal test ortamını gerektirmez. Burada, otomatik lisanslama ve grup üyeliğini test etmek ve normal bir kuruluşu temsil eden bir ortamda bu üyelikle denemeler yapmak için bir seçenek olarak sağlanmıştır.
  
## <a name="phase-2-configure-and-test-dynamic-group-membership-and-automatic-licensing"></a>Aşama 2: Dinamik grup üyeliğini ve otomatik lisansları yapılandırma ve test edin

İlk olarak Satış adlı yeni bir grup oluşturun ve Departman olarak ayarlanmış kullanıcı hesaplarının otomatik olarak Satışlar grubuna katılması için dinamik  bir grup üyeliği  kuralı ekleyin.

1. İnternet tarayıcınızın özel bir örneğinde, [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) test laboratuvarı aboneliğinizin genel yönetici Microsoft 365 E5 oturum açın.
2. Tarayıcınızın ayrı bir sekmesinde, üzerinde Azure portalına gidin [https://portal.azure.com](https://portal.azure.com).
3. Azure portalında, arama **kutusuna gruplar** girin ve Ardından Gruplar'ı **seçin**.
4. Tüm gruplar **bölmesinde Yeni** **grup'a tıklayın**.
5. Grup **türü'ne** bir metin **Microsoft 365**.
6. Grup **adı alanına** **Satış girin.**
7. Üyelik **türü'ne** dinamik **kullanıcı'ya seçin**.
8. Dinamik **kullanıcı üyeleri'ne seçin**.
9. Dinamik **üyelik kuralları bölmesinde** : 
   - Bölüm **özelliğini** seçin.
   - Eşittir **işlecini** seçin.
   - Değer **kutusuna** **Satış girin.**
10. **Kaydet**'i seçin.
11. **Oluştur**’u seçin.

Ardından, Satış grubunu, üyelere otomatik olarak lisans atamaları için Microsoft 365 E5 basın.

1. Satış grubunu **seçin** ve ardından Lisanslar'ı **seçin**.
2. Lisans **atamalarını güncelleştir bölmesinde Yenile'yi** ve **Microsoft 365 E5** Kaydet'i **seçin**.
3. Tarayıcınızda Azure portal sekmesini kapatın.

Ardından, User 4 hesabında dinamik grup üyeliğini ve otomatik lisanslamayı test edin:

1. Tarayıcınızdaki **Microsoft Office Giriş** sekmesinde Yönetici'yi **seçin**.
2. Seçenekler **Microsoft 365 yönetim merkezi** Etkin **kullanıcılar'ı seçin**.
3. Etkin **kullanıcılar sayfasında** Kullanıcı **4 hesabını** seçin.
4. Kullanıcı **4 bölmesinde** Ürün **lisansları için** **Düzenle'yi seçin**.
5. Ürün **lisansları bölmesinde,** Ürün lisansını devre **Microsoft 365 E5** ardından **SaveClose'yi** >  seçin.
6. Kullanıcı 4 hesabının özelliklerinde, hiçbir ürün lisansı atanmamış ve grup üyeliği olmadığını doğrulayın.
7. Kişi **bilgileri için Düzenle'yi** **seçin**.
8. Kişi bilgilerini **düzenle bölmesinde Kişi** **bilgilerini seçin.**
9. Bölüm kutusuna **Satış'ı** **girin ve** ardından **SaveClose'yi** >  seçin.
10. Birkaç dakika bekleyin ve sonra düzenli olarak Kullanıcı 4 hesabı bölmesinin sağ üst kısmında bulunan Yenile simgesini seçin.

Zamanında şunları görüyor olur:

- **Satış grubuyla** güncelleştirilen Grup **üyelikleri** özelliği.
- **Otomatik lisansla** güncelleştirilen ürün **Microsoft 365 E5**.

Üretimde dinamik grup üyeliğini ve otomatik lisansları dağıtmak için şu makalelere bakın:

- [Web'de grup Azure Active Directory](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)
- [Azure Active Directory'da dinamik gruplar](/azure/active-directory/users-groups-roles/groups-create-rule)

## <a name="next-step"></a>Sonraki adım

Test [ortamınıza](m365-enterprise-test-lab-guides.md#identity) başka kimlik özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Kimliği dağıtma](deploy-identity-solution-overview.md)

[Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar](m365-enterprise-test-lab-guides.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Microsoft 365 belgeleri için belgeler](/microsoft-365-enterprise/)