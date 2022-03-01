---
title: Microsoft 365 test ortamı çok faktörlü kimlik doğrulaması için kimlik doğrulaması
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
- seo-marvel-apr2020
- admindeeplinkMAC
description: Kurumsal test ortamınız için uygulama uygulamanıza akıllı telefona gönderilen metin iletilerini kullanarak çok Microsoft 365 kimlik doğrulamasını yapılandırabilirsiniz.
ms.openlocfilehash: d3207db4d8537e78ecc83ae18f8539f0e4f56106
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63014382"
---
# <a name="multi-factor-authentication-for-your-microsoft-365-for-enterprise-test-environment"></a>Kurumsal test ortamınız için Microsoft 365 çok faktörlü kimlik doğrulaması

*Bu Test Laboratuvarı Kılavuzu, hem kurumsal hem de Microsoft 365 test ortamları için Office 365 Kurumsal kullanılabilir.*

Microsoft 365'de ya da aboneliğiniz için Azure AD kiracısını kullanan herhangi bir hizmet veya uygulamada oturum açmanın ek güvenlik düzeyi için, hesabı doğrulamak için bir kullanıcı adı ve paroladan fazlasını gerektiren Azure AD çok faktörlü kimlik doğrulamasını etkinleştirebilirsiniz.

Çok faktörlü kimlik doğrulamasıyla, kullanıcıların parolalarını doğru girdikten sonra telefon aramasını onaylamaları, SMS ile gönderilen bir doğrulama kodunu girmeleri veya akıllı telefonlarında bir uygulama ile kimlik doğrulamasını doğrulamaları gerekir. Ancak bu ikinci kimlik doğrulama faktörü karşılandıktan sonra oturum açmaları gerekir.
  
Bu makalede, belirli bir kullanıcı hesabı için ileti tabanlı metin kimlik doğrulamasını etkinleştirme ve sınama işlemi açıklanmıştır.
  
Kurumsal test ortamınıza bir hesap için çok faktörlü kimlik doğrulamasını Microsoft 365 iki aşama ve üçüncü bir isteğe bağlı aşama içerir:
- [Aşama 1: Kurumsal test Microsoft 365 yapınızı oluşturma](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Aşama 2: Kullanıcı 2 hesabı için çok faktörlü kimlik doğrulamasını etkinleştirme ve test et](#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account)
- [Aşama 3: Koşullu erişim ilkesiyle çok faktörlü kimlik doğrulamasını etkinleştirme ve test et](#phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy)

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınına Microsoft 365 görsel bir harita için Kurumsal Test Laboratuvarı Kılavuzu Yığını [için Microsoft 365'e gidin](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Aşama 1: Kurumsal test Microsoft 365 yapınızı oluşturma

Çok faktörlü kimlik doğrulamasını minimum gereksinimlerle basit bir şekilde test etmek istiyorsanız, Hafif taban yapılandırma [yönergelerini izleyin](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Sanal bir kuruluşta çok faktörlü kimlik doğrulamasını test etmek için, Geçişli kimlik [doğrulama'daki yönergeleri izleyin](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Çok faktörlü kimlik doğrulamasını test etmek, Active Directory Etki Alanı Hizmetleri (AD DS) ormanı için İnternet ve dizin eşitlemeye bağlı sanal bir intranet içeren sanal kurumsal test ortamını gerektirmez. Burada, çok faktörlü kimlik doğrulamasını test etmek ve tipik bir kuruluşu temsil eden bir ortamda bu kimlik doğrulamasını deneyip denemek için bir seçenek olarak sağlanır.
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Aşama 2: Kullanıcı 2 hesabı için çok faktörlü kimlik doğrulamasını etkinleştirme ve test et

Şu adımlarla Kullanıcı 2 hesabı için çok faktörlü kimlik doğrulamasını etkinleştirin:
  
1. Tarayıcınızın ayrı ve özel bir örneğini açın, Microsoft 365 yönetim merkezi ()[https://portal.microsoft.com](https://portal.microsoft.com) gidin ve genel yönetici hesabınızla oturum açın.
    
2. Sol gezintide **UsersActive** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**users öğesini seçin**</a>.
    
3. Etkin kullanıcılar bölmesinde **Multi-factor authentication öğesini seçin**.
    
4. Listede Kullanıcı **2 hesabını** seçin.
    
5. Kullanıcı **2 bölümünde,** Hızlı adımlar'ın **altında Etkinleştir'i** **seçin**.
    
6. **Multi-factor auth'larını etkinleştirme hakkında iletişim** kutusunda **Multi-factor auth'ı etkinleştir'i seçin**.
    
7. Güncelleştirmeler **başarılı iletişim** kutusunda Kapat'ı **seçin**.
    
8. Oturum **Microsoft 365 yönetim merkezi**, sağ üst köşedeki kullanıcı hesabı simgesini seçin ve sonra da Oturumdan **çık'ı seçin**.
    
9. Tarayıcı örneğinizi kapatın.
   
Doğrulama için bir metin iletisi kullanmak ve bu adımları kullanarak test etmek üzere Kullanıcı 2 hesabının yapılandırmasını tamamlayın:
  
1. Tarayıcınızın yeni ve özel bir örneğini açın.
    
2. Oturum [açma Microsoft 365 yönetim merkezi ve](https://admin.microsoft.com) Kullanıcı 2 hesap adı ve parolasıyla oturum açın.
    
3. Oturum açından sonra, daha fazla bilgi için hesabı ayarlamak istenir. **İleri**'yi seçin.
    
4. Ek **güvenlik doğrulaması sayfasında** :
    
   - Ülkenizi veya bölgenizi seçin.
    
   - Kısa mesaj alacak akıllı telefonun telefon numarasını girin.
    
   - **Yöntem'de**, **Bana kısa mesajla kod gönder'i seçin**.
    
5. **İleri**'yi seçin.
    
6. Akıllı telefonunuza gelen kısa mesajdan doğrulama kodunu girin ve ardından Doğrula'ya **seçin**.
    
7. **3. Adım: Var olan uygulamalarınızı tutma sayfasında** Bitti'yi **seçin**.
    
8. Kullanıcı 2 hesabıyla ilk kez oturum atıysanız, parolayı değiştirmeniz istenir. Özgün parolayı ve yeni parolayı iki kez girin, ardından Parolayı **güncelleştir'i seçin ve oturum açma**. Yeni parolayı güvenli bir konuma kaydetme.
    
    Tarayıcınızın Giriş Office Giriş sekmesinde Kullanıcı 2 için **Microsoft Office Portalını** görüyor olun.

## <a name="phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy"></a>Aşama 3: Koşullu erişim ilkesiyle çok faktörlü kimlik doğrulamasını etkinleştirme ve test et

*Bu aşama yalnızca kurumsal test Microsoft 365 bir çalışma ortamı için kullanılabilir.*

Bu aşamada, grup ve koşullu erişim ilkesi kullanarak Kullanıcı 3 hesabı için çok faktörlü kimlik doğrulamasını etkinleştirirsiniz.

Ardından, MFAUsers adlı yeni bir grup oluşturun ve Kullanıcı 3 hesabını buna ekleyin.

1. Gezinti **Microsoft 365 yönetim merkezi** gezintide **Gruplar'ı** seçin ve sonra da Gruplar'ı <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**seçin**</a>.
2. Grup **ekle'yi seçin**.
3. Grup **türü seçin bölmesinde Güvenlik'i** seçin ve **sonra** da Sonraki'yi **seçin**.
4. Temel **bilgileri ayarlama bölmesinde Grup oluştur'a** ve **sonra Kapat'a** **tıklayın**.
5. Gözden Geçir **ve grup eklemeyi bitir bölmesinde** **MFAUsers girin** ve Ardından Sonraki'yi **seçin**.
6. Gruplar listesinde **MFAUsers grubunu** seçin.
7. **MFAUsers bölmesinde Üyeler'i** seçin **ve sonra** da Tüm üyeleri **görüntüle ve yönet'i seçin**.
8. **MFAUsers bölmesinde** Üye ekle'yi **seçin,** Kullanıcı 3 hesabını **seçin** ve sonra da **SaveCloseClose'yi** >  >  **seçin**.

Ardından, MFAUsers grubunun üyeleri için çok faktörlü kimlik doğrulaması gerektiren bir koşullu erişim ilkesi oluşturun.

1. Tarayıcınızın yeni sekmesinde' gidin [https://portal.azure.com](https://portal.azure.com).
2. **Azure Active Directory** >  **SecurityConditional** >  **Access'i seçin**.
3. Koşullu erişim **– İlkeler bölmesinde** Yeni **ilke'yi seçin**.
4. Yeni **bölmesinde**, Ad **kutusuna kullanıcı hesapları için MFA** **girin.**
5. Ödevler **bölümünde Kullanıcılar** ve **gruplar'ı seçin**.
6. Kullanıcılar ve **gruplar** bölmesinin Ekle **sekmesinde Kullanıcıları ve** grupları seçinKullanıcıları ve **grupları** >  **seçinSelect** **öğesini** >  seçin.
7. Seç bölmesinde  **MFAUsers grubunu seçin ve sonra** da **SelectDone öğesini** >  seçin.
8. Yeni **bölmesinin Erişim** denetimleri bölümünde **Ver'i** **seçin**.
9. Ver bölmesinde **Çok** faktörlü kimlik **doğrulaması gerektir'i seçin ve** sonra da Seç'i **seçin**.
10. Yeni bölmesinde **İlkeyi** etkinleştir **için** **Aç'ı seçin ve** sonra da Oluştur'a **tıklayın**.
11. **Azure portalını kapatın** ve **Microsoft 365 yönetim merkezi** kapatın.

Bu ilkeyi test etmek için, oturum açın ve Kullanıcı 3 hesabıyla oturum açın. MFA'yi yapılandırmanız istendiğinde. Bu, MFAUsers ilkesi uygulandığını gösteriyor.

## <a name="next-step"></a>Sonraki adım

Test [ortamınıza](m365-enterprise-test-lab-guides.md#identity) başka kimlik özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Kimliği dağıtma](deploy-identity-solution-overview.md)

[Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar](m365-enterprise-test-lab-guides.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Microsoft 365 belgeleri için belgeler](/microsoft-365-enterprise/)