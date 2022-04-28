---
title: Kurumsal test ortamı için Microsoft 365 genel yönetici hesaplarını koruma
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/12/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Kurumsal test ortamınız için Microsoft 365 genel yönetici hesaplarını korumak için bu adımları kullanın.
ms.openlocfilehash: bf053b9767aea4a290c5357d6309c57677a36cad
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098284"
---
# <a name="protect-global-administrator-accounts-in-your-microsoft-365-for-enterprise-test-environment"></a>Kurumsal test ortamı için Microsoft 365 genel yönetici hesaplarını koruma

*Bu Test Laboratuvarı Kılavuzu yalnızca kurumsal test ortamları için Microsoft 365 için kullanılabilir.*

Yönetici hesaplarınızın mümkün olduğunca güvenli olduğundan emin olarak kuruluşunuza yönelik dijital saldırıları önleyebilirsiniz. 

Bu makalede, genel yönetici hesaplarını korumak için Azure Active Directory (Azure AD) koşullu erişim ilkelerinin nasıl kullanılacağı açıklanmaktadır.

Kurumsal test ortamı için Microsoft 365 genel yönetici hesaplarının korunması iki aşamayı içerir:
- [1. Aşama: Kurumsal test ortamı için Microsoft 365 oluşturma](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [2. Aşama: Koşullu erişim ilkelerini yapılandırma](#phase-2-configure-conditional-access-policies)

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınındaki Microsoft 365 tüm makalelere yönelik görsel bir harita için [kurumsal Test Laboratuvarı Kılavuzu Yığını için Microsoft 365](../downloads/Microsoft365EnterpriseTLGStack.pdf) bölümüne gidin.

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>1. Aşama: Kurumsal test ortamı için Microsoft 365 oluşturma

Genel yönetici hesabı korumasını minimum gereksinimlerle basit bir şekilde test etmek istiyorsanız [Basit temel yapılandırma](lightweight-base-configuration-microsoft-365-enterprise.md) yönergelerini izleyin.
  
Sanal bir kuruluşta genel yönetici hesabı korumasını test etmek istiyorsanız Doğrudan [kimlik doğrulamasındaki](pass-through-auth-m365-ent-test-environment.md) yönergeleri izleyin.
  
> [!NOTE]
> Genel yönetici hesabı korumasını test etmek için, bir Active Directory Domain Services (AD DS) için İnternet'e bağlı bir sanal intranet ve dizin eşitlemesi içeren sanal kurumsal test ortamı gerekmez. Genel yönetici hesabı korumasını test edebilmeniz ve tipik bir kuruluşu temsil eden bir ortamda denemeler yapabilmeniz için burada bir seçenek olarak sağlanır. 
  
## <a name="phase-2-configure-conditional-access-policies"></a>2. Aşama: Koşullu erişim ilkelerini yapılandırma

İlk olarak, ayrılmış genel yönetici olarak yeni bir kullanıcı hesabı oluşturun.

1. Ayrı bir sekmede [Microsoft 365 yönetim merkezi](https://admin.microsoft.com/) açın.
2. **KullanıcılarEtkin** >  **kullanıcılar'ı** ve ardından **Kullanıcı ekle'yi** seçin.
3. **Kullanıcı ekle** bölmesinde Ad, **Görünen ad** ve **Kullanıcı adı** kutularına **DedicatedAdmin** girin.
4. **Parola'yı** seçin, **Parolayı oluşturmama izin ver'i** seçin ve ardından güçlü bir parola girin. Bu yeni hesabın parolasını güvenli bir konuma kaydedin.
5. **İleri**'yi seçin.
6. **Ürün lisansları ata** bölmesinde **Microsoft 365 E5** ve ardından **İleri'yi** seçin.
7. **İsteğe bağlı ayarlar** bölmesinde **RollerYöntem** >  merkezi **erişimiGlobal** >  **yöneticiİleri'ni** >  seçin.
8. **Neredeyse bitti** bölmesinde **Eklemeyi bitir'i** ve ardından **Kapat'ı** seçin.

Ardından GlobalAdmins adlı yeni bir grup oluşturun ve Buna DedicatedAdmin hesabını ekleyin.

1. **Microsoft 365 yönetim merkezi** sekmesinde sol gezinti bölmesinde **Gruplar'ı** ve ardından **Gruplar'ı** seçin.
2. **Grup ekle'yi** seçin.
3. **Grup türü seçin** bölmesinde **Güvenlik'i** ve ardından **İleri'yi** seçin.
4. **Temel bilgileri ayarla** bölmesinde **Grup oluştur'u** ve ardından **Kapat'ı** seçin.
5. **Grup eklemeyi gözden geçir ve bitir** bölmesinde **GlobalAdmins** yazın ve **İleri'yi** seçin.
7. Grup listesinde **GlobalAdmins** grubunu seçin.
8. **GlobalAdmins** bölmesinde **Üyeler'i** ve ardından **Tümünü görüntüle ve üyeleri yönet'i** seçin.
9. **GlobalAdmins** bölmesinde **Üye ekle'yi** seçin, **DedicatedAdmin** hesabını ve genel yönetici hesabınızı seçin ve ardından **SaveCloseClose** >  >  öğesini seçin.

Ardından, genel yönetici hesapları için çok faktörlü kimlik doğrulaması gerektirmek ve oturum açma riski orta veya yüksekse kimlik doğrulamasını reddetmek için koşullu erişim ilkeleri oluşturun.

Bu ilk ilke, tüm genel yönetici hesaplarının MFA kullanmasını gerektirir.

1. Tarayıcınızın yeni bir sekmesinde adresine [https://portal.azure.com](https://portal.azure.com)gidin.
2. **Azure Active Directory** >  **GüvenlikKonaksal** >  **Erişim'e** tıklayın.
3. **Koşullu erişim – İlkeler** bölmesinde **Temel ilke: Yöneticiler için MFA gerektir (önizleme)** seçeneğini belirleyin.
4. **Temel ilke** bölmesinde **İlkeyi hemen kullan > Kaydet'i** seçin.

Bu ikinci ilke, oturum açma riski orta veya yüksek olduğunda genel yönetici hesabı kimlik doğrulamasına erişimi engeller.

1. **Koşullu erişim – İlkeler** bölmesinde **Yeni ilke'yi** seçin.
2. **Yeni** bölmesinde **Ad** alanına **Genel yöneticiler** yazın.
3. **Atamalar** bölümünde **Kullanıcılar ve gruplar'ı** seçin.
4. **Kullanıcılar ve gruplar** bölmesinin **Ekle** sekmesinde **Kullanıcıları ve grupları** >  **seçKullanıçlar ve** **gruplarSeçim'i** >  seçin.
5. **Seç** bölmesinde **GlobalAdmins** grubunu ve ardından **SelectDone'ı** >  seçin.
6. **Atamalar** bölümünde **Koşullar'ı** seçin.
7. **Koşullar** bölmesinde **Oturum açma riski'ni** seçin, Yapılandır için **Evet'i** seçin, **Yüksek** ve **Orta'yı** seçin ve ardından Seç ve **Bitti'yi** seçin. 
8. **Yeni** bölmesinin **Erişim denetimleri** bölümünde **Ver'i** seçin.
9. **Ver** bölmesinde **Erişimi engelle'yi** ve ardından **Seç'i** seçin.
10. **Yeni** bölmesinde **İlkeyi etkinleştir** için **Açık'ı** ve ardından **Oluştur'u** seçin.
11. **Azure portal** ve **Microsoft 365 yönetim merkezi** sekmelerini kapatın.

İlk ilkeyi test etmek için oturumu kapatın ve DedicatedAdmin hesabıyla oturum açın. MFA'yi yapılandırmanız istenmelidir. Bu, ilk ilkenin uygulandığını gösterir.

## <a name="next-step"></a>Sonraki adım

Test ortamınızdaki ek [kimlik](m365-enterprise-test-lab-guides.md#identity) özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Kimliği dağıtma](deploy-identity-solution-overview.md)

[Kurumsal Test Laboratuvarı Kılavuzları için Microsoft 365](m365-enterprise-test-lab-guides.md)

[Microsoft 365 Kurumsal’a genel bakış](microsoft-365-overview.md)

[Kurumsal belgeler için Microsoft 365](/microsoft-365-enterprise/)