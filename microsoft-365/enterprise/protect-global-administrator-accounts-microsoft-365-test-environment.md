---
title: Kurumsal test ortamı için Microsoft 365 yönetici hesaplarını koruma
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/12/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Kurumsal test ortamınız için çalışma alanınıza genel yönetici Microsoft 365 için bu adımları kullanın.
ms.openlocfilehash: a759d4e8720216019886f33ca0df7325b5209930
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63014389"
---
# <a name="protect-global-administrator-accounts-in-your-microsoft-365-for-enterprise-test-environment"></a>Kurumsal test ortamı için Microsoft 365 yönetici hesaplarını koruma

*Bu Test Laboratuvarı Kılavuzu yalnızca kurumsal test Microsoft 365 test ortamları için kullanılabilir.*

Yönetici hesaplarının mümkün olduğunca güvenli olmasını sağlayarak, dijital saldırıların organizasyon üzerinde önüne geçebilirsiniz. 

Bu makalede, genel yönetici hesaplarını korumak Azure Active Directory (Azure AD) koşullu erişim ilkelerinin nasıl kullanımı açıklanmıştır.

Kurumsal test ortamınız için ağ Microsoft 365 genel yönetici hesaplarının korunması iki aşama içerir:
- [Aşama 1: Kurumsal test Microsoft 365 yapınızı oluşturma](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Aşama 2: Koşullu erişim ilkelerini yapılandırma](#phase-2-configure-conditional-access-policies)

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınına Microsoft 365 görsel bir harita için Kurumsal Test Laboratuvarı Kılavuzu Yığını [için Microsoft 365'e gidin](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Aşama 1: Kurumsal test Microsoft 365 yapınızı oluşturma

Genel yönetici hesap korumasını en düşük gereksinimlerle basit bir şekilde test etmek için Hafif taban yapılandırma [yönergelerini izleyin](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Sanal bir kuruluşta genel yönetici hesabı korumasını test etmek için, Geçişli kimlik [doğrulama'daki yönergeleri izleyin](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Genel yönetici hesap korumasını test etmek, active Directory Etki Alanı Hizmetleri (AD DS) için İnternet ve dizin eşitlemesi bağlantılı sanal bir intranet içeren sanal kurumsal test ortamını gerektirmez. Burada bir seçenek olarak sağlanır; böylelikle genel yönetici hesabı korumasını sınayabilirsiniz ve normal bir kuruluşu temsil eden bir ortamda bu korumayı sınabilirsiniz. 
  
## <a name="phase-2-configure-conditional-access-policies"></a>Aşama 2: Koşullu erişim ilkelerini yapılandırma

İlk olarak, adanmış bir genel yönetici olarak yeni bir kullanıcı hesabı oluşturun.

1. Ayrı bir sekmede, sayfayı [Microsoft 365 yönetim merkezi](https://admin.microsoft.com/).
2. **UsersActive** >  **users öğesini seçin** ve sonra da **Add a user öğesini seçin**.
3. Kullanıcı ekle **bölmesinde** Ad, Görünen ad ve Kullanıcı adı **kutularına** **DedicatedAdmin** **girin**.
4. **Parola'yi** seçin, **Parolayı oluşturmama izin ver'i** seçin ve güçlü bir parola girin. Bu yeni hesabın parolasını güvenli bir konuma yazın.
5. **İleri**'yi seçin.
6. Ürün **lisanslarını ata bölmesinde** Lisanslar'ı **Microsoft 365 E5** sonra da Sonraki'yi **seçin**.
7. İsteğe **bağlı ayarlar bölmesinde** **RolesAdmin** >  center **accessOtobal** >  **adminNext** >  öğesini seçin.
8. Neredeyse bitti **bölmesinde Eklemeyi bitir'i** ve **sonra Kapat'ı** **seçin**.

Ardından GlobalAdmins adlı yeni bir grup oluşturun ve DedicatedAdmin hesabını buna ekleyin.

1. Gezinti **Microsoft 365 yönetim merkezi** gezintide **Gruplar'ı** seçin ve sonra da Gruplar'ı **seçin**.
2. Grup **ekle'yi seçin**.
3. Grup **türü seçin bölmesinde Güvenlik'i** seçin ve **sonra** da Sonraki'yi **seçin**.
4. Temel **bilgileri ayarlama bölmesinde Grup oluştur'a** ve **sonra Kapat'a** **tıklayın**.
5. Gözden Geçir **ve grup eklemeyi bitir bölmesinde** **GlobalAdmins** girin ve ardından Sonraki'yi **seçin**.
7. Grup listesinde **GlobalAdmins grubunu** seçin.
8. **GlobalAdmins bölmesinde Üyeler'i** seçin ve **sonra** da Tüm üyeleri **görüntüle ve üyeleri yönet'i seçin**.
9. **GlobalAdmins bölmesinde** Üye ekle'yi **seçin,** **DedicatedAdmin** hesabını ve genel yönetici hesabını seçin ve sonra da **SaveCloseClose'yi** >  >  **seçin**.

Ardından, genel yönetici hesaplarında çok faktörlü kimlik doğrulaması gerektirecek ve oturum açma riski orta veya yüksekse kimlik doğrulamasını reddetmek için koşullu erişim ilkeleri oluşturun.

Bu ilk ilke, tüm genel yönetici hesaplarının MFA kullanmalarını gerektirir.

1. Tarayıcınızın yeni sekmesinde' gidin [https://portal.azure.com](https://portal.azure.com).
2. **Azure Active Directory** >  **SecurityConditional** >  **Access'e tıklayın**.
3. Koşullu erişim **– İlkeler bölmesinde** Temel ilke **: Yöneticiler için MFA gerektir (önizleme)'yi seçin**.
4. Temel ilke **bölmesinde İlkeyi** hemen **kullan'ı ve ardından Kaydet> seçin**.

Bu ikinci ilke, oturum açma riski orta veya yüksek olduğunda genel yönetici hesabı kimlik doğrulamasına erişimi engeller.

1. Koşullu erişim **– İlkeler bölmesinde** Yeni **ilke'yi seçin**.
2. Yeni bölmesinde **,** Ad alanına **Genel yöneticiler'i** **girin**.
3. Ödevler **bölümünde Kullanıcılar** ve **gruplar'ı seçin**.
4. Kullanıcılar ve **gruplar** bölmesinin Ekle **sekmesinde Kullanıcıları ve** grupları seçinKullanıcıları ve **grupları** >  **seçinSelect** **öğesini** >  seçin.
5. Seç **bölmesinde** **GlobalAdmins grubunu ve ardından** **SelectDone** **öğesini** >  seçin.
6. Ödevler **bölümünde Koşullar'ı** **seçin**.
7. Koşullar bölmesinde **Oturum açma** riski'ni seçin, **Yapılandır** için **Evet'i****, Yüksek** ve  Orta'ı ve ardından Seç ve **Bitti'yi** **seçin**.
8. Yeni **bölmesinin Erişim** denetimleri bölümünde **Ver'i** **seçin**.
9. Ver bölmesinde **Erişimi** **engelle'yi seçin ve** sonra da Seç'i **seçin**.
10. Yeni bölmesinde **İlkeyi** etkinleştir **için** **Aç'ı seçin ve** sonra da Oluştur'a **tıklayın**.
11. **Azure portalını kapatın** ve **Microsoft 365 yönetim merkezi** kapatın.

İlk ilkeyi test etmek için, oturum açın ve DedicatedAdmin hesabıyla oturum açın. MFA'yi yapılandırmanız istendiğinde. Bu, ilk ilkenin uygulandığını gösteriyor.

## <a name="next-step"></a>Sonraki adım

Test [ortamınıza](m365-enterprise-test-lab-guides.md#identity) başka kimlik özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Kimliği dağıtma](deploy-identity-solution-overview.md)

[Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar](m365-enterprise-test-lab-guides.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Microsoft 365 belgeleri için belgeler](/microsoft-365-enterprise/)