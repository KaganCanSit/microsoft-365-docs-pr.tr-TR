---
title: Kurumsal test ortamı çok faktörlü kimlik doğrulaması için Microsoft 365
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
- seo-marvel-apr2020
- admindeeplinkMAC
description: Kurumsal test ortamınız için Microsoft 365 akıllı telefona gönderilen kısa mesajları kullanarak çok faktörlü kimlik doğrulamasını yapılandırın.
ms.openlocfilehash: aa72375342bdf60e1fe1bc504f14b1f51a48b701
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078745"
---
# <a name="multi-factor-authentication-for-your-microsoft-365-for-enterprise-test-environment"></a>Kurumsal test ortamı için Microsoft 365 için çok faktörlü kimlik doğrulaması

*Bu Test Laboratuvarı Kılavuzu hem kurumsal hem de Office 365 Kurumsal test ortamları için Microsoft 365 için kullanılabilir.*

Microsoft 365 veya aboneliğiniz için Azure AD kiracısını kullanan herhangi bir hizmet veya uygulamada oturum açmak için ek bir güvenlik düzeyi için, bir hesabı doğrulamak için yalnızca bir kullanıcı adı ve paroladan daha fazlasını gerektiren Azure AD çok faktörlü kimlik doğrulamasını etkinleştirebilirsiniz.

Çok faktörlü kimlik doğrulaması ile kullanıcıların bir telefon aramasını onaylaması, kısa mesajla gönderilen bir doğrulama kodunu yazması veya parolalarını doğru girdikten sonra akıllı telefonlarındaki bir uygulamayla kimlik doğrulamasını doğrulaması gerekir. Yalnızca bu ikinci kimlik doğrulama faktörü karşılandıktan sonra oturum açabilirler.
  
Bu makalede, belirli bir kullanıcı hesabı için metin iletisi tabanlı kimlik doğrulamasını etkinleştirme ve test etme işlemleri açıklanmaktadır.
  
Kurumsal test ortamı için Microsoft 365 bir hesap için çok faktörlü kimlik doğrulamasını ayarlamak için iki aşama ve isteğe bağlı üçüncü aşama gerekir:
- [1. Aşama: Kurumsal test ortamı için Microsoft 365 oluşturma](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [2. Aşama: Kullanıcı 2 hesabı için çok faktörlü kimlik doğrulamasını etkinleştirme ve test edin](#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account)
- [3. Aşama: Koşullu erişim ilkesiyle çok faktörlü kimlik doğrulamasını etkinleştirme ve test edin](#phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy)

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınındaki Microsoft 365 tüm makalelere yönelik görsel bir harita için [kurumsal Test Laboratuvarı Kılavuzu Yığını için Microsoft 365](../downloads/Microsoft365EnterpriseTLGStack.pdf) bölümüne gidin.
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>1. Aşama: Kurumsal test ortamı için Microsoft 365 oluşturma

Çok faktörlü kimlik doğrulamasını minimum gereksinimlerle basit bir şekilde test etmek istiyorsanız [Basit temel yapılandırma](lightweight-base-configuration-microsoft-365-enterprise.md) yönergelerini izleyin.
  
Simülasyon kuruluşunda çok faktörlü kimlik doğrulamasını test etmek istiyorsanız Doğrudan [kimlik doğrulaması](pass-through-auth-m365-ent-test-environment.md) yönergelerini izleyin.
  
> [!NOTE]
> Çok faktörlü kimlik doğrulamasını test etmek, bir Active Directory Domain Services (AD DS) ormanı için İnternet'e bağlı bir intranet ve dizin eşitlemesi içeren sanal kurumsal test ortamını gerektirmez. Burada, çok faktörlü kimlik doğrulamasını test edebilmeniz ve tipik bir kuruluşu temsil eden bir ortamda denemeler yapabileceğiniz bir seçenek olarak sağlanır.
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>2. Aşama: Kullanıcı 2 hesabı için çok faktörlü kimlik doğrulamasını etkinleştirme ve test edin

Aşağıdaki adımlarla Kullanıcı 2 hesabı için çok faktörlü kimlik doğrulamasını etkinleştirin:
  
1. Tarayıcınızın ayrı ve özel bir örneğini açın, Microsoft 365 yönetim merkezi ()[https://portal.microsoft.com](https://portal.microsoft.com) gidin ve genel yönetici hesabınızla oturum açın.
    
2. Sol gezinti bölmesinde <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**KullanıcılarEtkin**</a> >  kullanıcılar'ı seçin.
    
3. Etkin kullanıcılar bölmesinde **Çok faktörlü kimlik doğrulaması'nı** seçin.
    
4. Listede **Kullanıcı 2** hesabını seçin.
    
5. **Kullanıcı 2** bölümündeki **Hızlı adımlar'ın** altında **Etkinleştir'i** seçin.
    
6. **Çok faktörlü kimlik doğrulamasını etkinleştirme hakkında** iletişim kutusunda **Çok faktörlü kimlik doğrulamasını etkinleştir'i** seçin.
    
7. **Güncelleştirmeler başarılı** iletişim kutusunda **Kapat'ı** seçin.
    
8. **Microsoft 365 yönetim merkezi** sekmesinde, sağ üstteki kullanıcı hesabı simgesini ve ardından **Oturumu kapat'ı** seçin.
    
9. Tarayıcı örneğinizi kapatın.
   
Kullanıcı 2 hesabının yapılandırmasını tamamlayarak doğrulama için bir kısa mesaj kullanın ve bu iletiyi şu adımlarla test edin:
  
1. Tarayıcınızın yeni, özel bir örneğini açın.
    
2. [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) gidin ve Kullanıcı 2 hesap adı ve parolası ile oturum açın.
    
3. Oturum açtıktan sonra, daha fazla bilgi için hesabı ayarlamanız istenir. **İleri**'yi seçin.
    
4. **Ek güvenlik doğrulama** sayfasında:
    
   - Ülkenizi veya bölgenizi seçin.
    
   - Kısa mesaj alacak akıllı telefonun telefon numarasını girin.
    
   - **Yöntem'de** **Bana kısa mesajla kod gönder'i** seçin.
    
5. **İleri**'yi seçin.
    
6. Akıllı telefonunuzda alınan kısa mesajdan doğrulama kodunu girin ve **Doğrula'yı** seçin.
    
7. **3. Adım: Mevcut uygulamalarınızı koruyun** sayfasında **Bitti'yi** seçin.
    
8. Kullanıcı 2 hesabıyla ilk kez oturum açtıysanız parolayı değiştirmeniz istenir. Özgün parolayı ve yeni parolayı iki kez girin, ardından **Parolayı güncelleştir'i seçip oturum açın**. Yeni parolayı güvenli bir konuma kaydedin.
    
    Tarayıcınızın Microsoft Office Giriş sekmesinde Kullanıcı 2 için **Office** portalını görmeniz gerekir.

## <a name="phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy"></a>3. Aşama: Koşullu erişim ilkesiyle çok faktörlü kimlik doğrulamasını etkinleştirme ve test edin

*Bu aşama yalnızca kurumsal test ortamına yönelik bir Microsoft 365 için kullanılabilir.*

Bu aşamada, bir grup ve koşullu erişim ilkesi kullanarak Kullanıcı 3 hesabı için çok faktörlü kimlik doğrulamasını etkinleştirirsiniz.

Ardından, MFAUsers adlı yeni bir grup oluşturun ve kullanıcı 3 hesabını ekleyin.

1. **Microsoft 365 yönetim merkezi** sekmesinde sol gezinti bölmesinde **Gruplar'ı** ve ardından <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Gruplar'ı**</a> seçin.
2. **Grup ekle'yi** seçin.
3. **Grup türü seçin** bölmesinde **Güvenlik'i** ve ardından **İleri'yi** seçin.
4. **Temel bilgileri ayarla** bölmesinde **Grup oluştur'u** ve ardından **Kapat'ı** seçin.
5. **Grup eklemeyi gözden geçir ve bitir** bölmesinde **MFAUsers** yazın ve **İleri'yi** seçin.
6. Grup listesinde **MFAUsers** grubunu seçin.
7. **MFAKullanııcıları** bölmesinde **Üyeler'i** ve ardından **Tümünü görüntüle ve üyeleri yönet'i** seçin.
8. **MFAKullanııcıları** bölmesinde **Üye ekle'yi** seçin, **Kullanıcı 3** hesabını ve ardından **SaveCloseClose** >  >  öğesini seçin.

Ardından, MFAUsers grubunun üyeleri için çok faktörlü kimlik doğrulamasını gerektirecek bir koşullu erişim ilkesi oluşturun.

1. Tarayıcınızın yeni bir sekmesinde adresine [https://portal.azure.com](https://portal.azure.com)gidin.
2. **Azure Active Directory** >  **GüvenlikKonaksal** >  **Erişim'i** seçin.
3. **Koşullu erişim – İlkeler** bölmesinde **Yeni ilke'yi** seçin.
4. **Yeni** bölmesinde, **Ad** kutusuna **kullanıcı hesapları için MFA** girin.
5. **Atamalar** bölümünde **Kullanıcılar ve gruplar'ı** seçin.
6. **Kullanıcılar ve gruplar** bölmesinin **Ekle** sekmesinde **Kullanıcıları ve grupları** >  **seçKullanıçlar ve** **gruplarSeçim'i** >  seçin.
7. **Seç** bölmesinde **MFAUsers** grubunu ve ardından **SelectDone'ı** >  seçin.
8. **Yeni** bölmesinin **Erişim denetimleri** bölümünde **Ver'i** seçin.
9. **Ver** bölmesinde **Çok faktörlü kimlik doğrulaması gerektir'i** ve ardından **Seç'i** seçin.
10. **Yeni** bölmesinde **İlkeyi etkinleştir** için **Açık'ı** ve ardından **Oluştur'u** seçin.
11. **Azure portal** ve **Microsoft 365 yönetim merkezi** sekmelerini kapatın.

Bu ilkeyi test etmek için oturumu kapatın ve Kullanıcı 3 hesabıyla oturum açın. MFA'yi yapılandırmanız istenmelidir. Bu, MFAUsers ilkesinin uygulandığını gösterir.

## <a name="next-step"></a>Sonraki adım

Test ortamınızdaki ek [kimlik](m365-enterprise-test-lab-guides.md#identity) özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Kimliği dağıtma](deploy-identity-solution-overview.md)

[Kurumsal Test Laboratuvarı Kılavuzları için Microsoft 365](m365-enterprise-test-lab-guides.md)

[Microsoft 365 Kurumsal’a genel bakış](microsoft-365-overview.md)

[Kurumsal belgeler için Microsoft 365](/microsoft-365-enterprise/)