---
title: Microsoft 365 için dizin eşitlemesine hazırlanma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Dizin eşitlemesini kullanarak kullanıcıları Microsoft 365 sağlamaya hazırlanmayı ve bu yöntemi kullanmanın uzun vadeli avantajlarını açıklar.
ms.openlocfilehash: 03182d4cb0e9ed1da2687ab23ffae11369f3765a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090783"
---
# <a name="prepare-for-directory-synchronization-to-microsoft-365"></a>Microsoft 365 için dizin eşitlemesine hazırlanma

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Karma kimlik modelini seçtiyseniz ve [2. Adımda](protect-your-global-administrator-accounts.md) yönetici hesapları ve bu çözümün [3. Adımındaki](microsoft-365-secure-sign-in.md) kullanıcı hesapları için koruma yapılandırdıysanız, sonraki göreviniz dizin eşitlemesini dağıtmaktır. Kuruluşunuz için dizin eşitlemesinin avantajları şunlardır:

- Kuruluşunuzdaki yönetim programlarını azaltma
- İsteğe bağlı olarak çoklu oturum açma senaryosını etkinleştirme
- Microsoft 365'de hesap değişikliklerini otomatikleştirme

Dizin eşitlemesini kullanmanın avantajları hakkında daha fazla bilgi için bkz. [Azure Active Directory (Azure AD) ile karma kimlik](/azure/active-directory/hybrid/whatis-hybrid-identity).

Ancak dizin eşitlemesi, Active Directory Domain Services (AD DS) aboneliğinizin Microsoft 365 aboneliğinizin Azure AD kiracısıyla eşitlenmesini en az hatayla sağlamak için planlama ve hazırlık gerektirir.

En iyi sonuçları elde etmek için bu adımları izleyin.

> [!NOTE]
> ASCII olmayan karakterler AD DS kullanıcı hesabındaki öznitelikler için eşitlenmez.

## <a name="ad-ds-preparation"></a>AD DS Hazırlığı

Eşitleme kullanarak Microsoft 365 sorunsuz geçiş sağlamaya yardımcı olmak için, Microsoft 365 dizin eşitleme dağıtımınıza başlamadan önce AD DS ormanınızı hazırlamanız gerekir.
  
Dizin hazırlama işleminiz aşağıdaki görevlere odaklanmalıdır:

- Yinelenen **proxyAddress** ve **userPrincipalName** özniteliklerini kaldırın.
- Boş ve geçersiz **userPrincipalName** özniteliklerini geçerli **userPrincipalName** öznitelikleriyle güncelleştirin.
- **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname** ve **userPrincipalName** özniteliklerindeki geçersiz ve sorgulanabilir karakterleri kaldırın. Öznitelikleri hazırlama hakkında ayrıntılı bilgi için bkz. [Azure Active Directory Eşitleme Aracı tarafından eşitlenen özniteliklerin listesi](https://go.microsoft.com/fwlink/p/?LinkId=396719).

    > [!NOTE]
    > Bunlar, Azure AD Bağlan eşitlenen özniteliklerle aynıdır. 
  
## <a name="multi-forest-deployment-considerations"></a>Çok ormanlı dağıtımla ilgili dikkat edilmesi gerekenler

Birden çok orman ve SSO seçeneği için [Azure AD Bağlan Özel Yüklemesi'ni](/azure/active-directory/hybrid/how-to-connect-install-custom) kullanın.
  
Kuruluşunuzun kimlik doğrulaması için birden çok ormanı varsa (oturum açma ormanları), aşağıdakileri kesinlikle öneririz:
  
- **Ormanlarınızı birleştirmeyi düşünün.** Genel olarak, birden çok ormanı korumak için daha fazla ek yük vardır. Kuruluşunuzda ayrı ormanlar gereksinimini belirleyen güvenlik kısıtlamaları yoksa, şirket içi ortamınızı basitleştirmeyi göz önünde bulundurun.
- **Yalnızca birincil oturum açma ormanınızda kullanın.** Microsoft 365 ilk dağıtımınız için yalnızca birincil oturum açma ormanınızda Microsoft 365 dağıtmayı göz önünde bulundurun. 

Çok ormanlı AD DS dağıtımınızı birleştiremiyorsanız veya kimlikleri yönetmek için başka dizin hizmetleri kullanıyorsanız, bunları Microsoft'un veya iş ortağının yardımıyla eşitleyebilirsiniz.
  
Daha fazla bilgi için bkz. [Azure AD Bağlan topolojileri](/azure/active-directory/hybrid/plan-connect-topologies).
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a>Dizin eşitlemeye bağımlı özellikler
  
Dizin eşitlemesi aşağıdaki özellikler ve işlevler için gereklidir:
  
- Azure AD Sorunsuz Tek Sign-On (SSO)
- bir arada bulunmayı Skype
- Karma dağıtımı Exchange, örneğin:
  - Şirket içi Exchange ortamınız ile Microsoft 365 arasında tam olarak paylaşılan genel adres listesi (GAL).
  - Gal bilgilerini farklı posta sistemlerinden eşitleme.
  - kullanıcıları Microsoft 365 hizmet tekliflerine ekleme ve hizmet tekliflerinden kaldırma özelliği. Bunun için şunlar gerekir:
  - Dizin eşitleme kurulumu sırasında iki yönlü eşitleme yapılandırılmalıdır. Varsayılan olarak, dizin eşitleme araçları dizin bilgilerini yalnızca buluta yazar. İki yönlü eşitlemeyi yapılandırdığınızda, sınırlı sayıda nesne özniteliğinin buluttan kopyalanıp yerel AD DS'nize geri yazılabilmesi için geri yazma işlevini etkinleştirirsiniz. Geri yazma, Exchange karma mod olarak da adlandırılır. 
  - Şirket içi Exchange karma dağıtım
  - Bazı kullanıcı posta kutularını şirket içinde tutarken bazı kullanıcı posta kutularını Microsoft 365 taşıma özelliği.
  - şirket içi Kasa gönderenler ve engellenen gönderenler Microsoft 365 çoğaltılır.
  - Temel temsilci seçme ve e-posta adına gönderme işlevselliği.
  - Tümleşik bir şirket içi akıllı kartınız veya çok faktörlü kimlik doğrulama çözümünüz var.
- Fotoğrafların, küçük resimlerin, konferans odalarının ve güvenlik gruplarının eşitlenmesi

## <a name="1-directory-cleanup-tasks"></a>1. Dizin temizleme görevleri

AD DS'nizi Azure AD kiracınızla eşitlemeden önce AD DS'nizi temizlemeniz gerekir.

> [!IMPORTANT]
> Eşitlemeden önce AD DS temizlemesi yapmazsanız, dağıtım işlemi üzerinde önemli bir olumsuz etkiye yol açabilir. Dizin eşitlemesi, hataları tanımlama ve yeniden eşitleme döngüsünden geçmek günler, hatta haftalar sürebilir.

AD DS'nizde, Microsoft 365 lisansı atanacak her kullanıcı hesabı için aşağıdaki temizleme görevlerini tamamlayın:

1. **proxyAddresses** özniteliğinde geçerli ve benzersiz bir e-posta adresi olduğundan emin olun.

2. **proxyAddresses** özniteliğindeki yinelenen değerleri kaldırın.

3. Mümkünse, kullanıcının kullanıcı **nesnesindeki** **userPrincipalName** özniteliği için geçerli ve benzersiz bir değer olduğundan emin olun. En iyi eşitleme deneyimi için AD DS UPN'nin Azure AD UPN ile eşleştiğinden emin olun. Bir kullanıcının **userPrincipalName** özniteliği için bir değeri yoksa, **kullanıcı** nesnesi **sAMAccountName** özniteliği için geçerli ve benzersiz bir değer içermelidir. **userPrincipalName** özniteliğindeki yinelenen değerleri kaldırın.

4. Genel adres listesinin (GAL) en iyi şekilde kullanılması için AD DS kullanıcı hesabının aşağıdaki özniteliklerindeki bilgilerin doğru olduğundan emin olun:

   - Givenname
   - Soyadı
   - displayName
   - İş Unvanı
   - Bölüm
   - Office
   - Ofis Telefonu
   - Cep Telefonu
   - Faks Numarası
   - Sokak Adresi
   - Şehir
   - Eyalet veya İl
   - Posta Kodu veya Posta Kodu
   - Ülke veya Bölge

## <a name="2-directory-object-and-attribute-preparation"></a>2. Dizin nesnesi ve öznitelik hazırlığı

AD DS'niz ile Microsoft 365 arasında başarılı dizin eşitlemesi için AD DS özniteliklerinizin düzgün hazırlanması gerekir. Örneğin, belirli karakterlerin Microsoft 365 ortamıyla eşitlenen belirli özniteliklerde kullanılmadığından emin olmanız gerekir. Beklenmeyen karakterler dizin eşitlemenin başarısız olmasına neden olmaz, ancak bir uyarı döndürebilir. Geçersiz karakterler dizin eşitlemenin başarısız olmasına neden olur.

Bazı AD DS kullanıcılarınızın bir veya daha fazla yinelenen özniteliği varsa dizin eşitlemesi de başarısız olur. Her kullanıcının benzersiz öznitelikleri olmalıdır.

Hazırlamanız gereken öznitelikler burada listelenmiştir:

- **displayName**

  - Kullanıcı nesnesinde öznitelik varsa, Microsoft 365 ile eşitlenir.
  - Bu öznitelik kullanıcı nesnesinde varsa, bunun için bir değer olmalıdır. Başka bir ifadeyle özniteliğin boş olmaması gerekir.
  - En fazla karakter sayısı: 256

- **Givenname**

  - Kullanıcı nesnesinde öznitelik varsa, Microsoft 365 ile eşitlenir, ancak Microsoft 365 bunu gerektirmez veya kullanmaz.
  - En fazla karakter sayısı: 64

- **posta**

  - Öznitelik değeri dizin içinde benzersiz olmalıdır.

    > [!NOTE]
    > Yinelenen değerler varsa, değere sahip ilk kullanıcı eşitlenir. Sonraki kullanıcılar Microsoft 365 görünmez. her iki kullanıcının da Microsoft 365 görünmesi için Microsoft 365 değerini değiştirmeniz veya AD DS'deki her iki değeri de değiştirmeniz gerekir.

- **mailNickname** (Exchange diğer ad)

  - Öznitelik değeri nokta (.) ile başlayamaz.
  - Öznitelik değeri dizin içinde benzersiz olmalıdır.

    > [!NOTE]
    > Eşitlenen addaki alt çizgi ("_") bu özniteliğin özgün değerinin geçersiz karakterler içerdiğini gösterir. Bu öznitelik hakkında daha fazla bilgi için bkz. [Exchange diğer ad özniteliği](/powershell/module/exchange/set-mailbox).
    >

- **Proxyaddresses**

  - Çok değerli öznitelik
  - Değer başına karakter sayısı üst sınırı: 256
  - Öznitelik değeri boşluk içermemelidir.
  - Öznitelik değeri dizin içinde benzersiz olmalıdır.
  - Geçersiz karakterler: \< \> ( ) ; , [ ] "
  - Aksan, vurgu ve tilde gibi aksan işaretlerine sahip harfler geçersiz karakterlerdir.

    Geçersiz karakterlerin tür sınırlayıcısı ve ":" karakterlerini izleyen karakterlere uygulandığını, SMTP:User@contso.com izin verilip SMTP:user:M@contoso.com uygulanmadığını unutmayın.

    > [!IMPORTANT]
    > Tüm Basit Posta Aktarım Protokolü (SMTP) adresleri e-posta ileti standartlarına uygun olmalıdır. Varsa yinelenen veya istenmeyen adresleri kaldırın.

- **Samaccountname**

  - En fazla karakter sayısı: 20
  - Öznitelik değeri dizin içinde benzersiz olmalıdır.
  - Geçersiz karakterler: [ \ " | , / : \< \> + = ; ? \* ']
  - Kullanıcının geçersiz bir **sAMAccountName** özniteliği varsa ancak geçerli bir **userPrincipalName** özniteliği varsa, kullanıcı hesabı Microsoft 365 oluşturulur.
  - **Hem sAMAccountName** hem de **userPrincipalName** geçersizse, AD DS **userPrincipalName** özniteliği güncelleştirilmelidir.

- **sn** (soyadı)

  - Kullanıcı nesnesinde öznitelik varsa, Microsoft 365 ile eşitlenir, ancak Microsoft 365 bunu gerektirmez veya kullanmaz.

- **Targetaddress**

    Kullanıcı için doldurulan **targetAddress** özniteliğinin (örneğin, SMTP:tom@contoso.com) Microsoft 365 GAL'de görünmesi gerekir. Üçüncü taraf mesajlaşma geçiş senaryolarında bunun için AD DS için Microsoft 365 şema uzantısı gerekir. Microsoft 365 şema uzantısı, AD DS'den bir dizin eşitleme aracı kullanılarak doldurulan Microsoft 365 nesnelerini yönetmek için başka yararlı öznitelikler de ekler. Örneğin, gizli posta kutularını veya dağıtım gruplarını yönetmek için **msExchHideFromAddressLists** özniteliği eklenir.

  - En fazla karakter sayısı: 256
  - Öznitelik değeri boşluk içermemelidir.
  - Öznitelik değeri dizin içinde benzersiz olmalıdır.
  - Geçersiz karakterler: \ \< \> ( ) ; , [ ] "
  - Tüm Basit Posta Aktarım Protokolü (SMTP) adresleri e-posta ileti standartlarına uygun olmalıdır.

- **Userprincipalname**

  - **userPrincipalName** özniteliği, kullanıcı adının ardından at işareti (@) ve bir etki alanı adı (örneğin, user@contoso.com) bulunduğu İnternet stili oturum açma biçiminde olmalıdır. Tüm Basit Posta Aktarım Protokolü (SMTP) adresleri e-posta ileti standartlarına uygun olmalıdır.
  - **userPrincipalName** özniteliği için karakter sayısı üst sınırı 113'tür. İşaret işaretinden (@) önce ve sonra belirli sayıda karaktere aşağıdaki gibi izin verilir:
  - At işaretinin (@) önünde yer alan kullanıcı adı için karakter sayısı üst sınırı: 64
  - Etki alanı adının at işaretinden (@) sonra gelen karakter sayısı üst sınırı: 48
  - Geçersiz karakterler: \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "
  - İzin verilen karakterler: A – Z, a - z, 0 – 9, ' . - _ ! # ^ ~
  - Aksan, vurgu ve tilde gibi aksan işaretlerine sahip harfler geçersiz karakterlerdir.
  - Her **userPrincipalName** değerinde @ karakteri gereklidir.
  - @ karakteri her **userPrincipalName** değerindeki ilk karakter olamaz.
  - Kullanıcı adı nokta (.), ve işareti (&amp; ), boşluk veya at işareti (@) ile bitemez.
  - Kullanıcı adı boşluk içeremez.
  - Yönlendirilebilir etki alanları kullanılmalıdır; örneğin, yerel veya iç etki alanları kullanılamaz.
  - Unicode alt çizgi karakterlerine dönüştürülür.
  - **userPrincipalName** dizininde yinelenen değer içeremez.

## <a name="3-prepare-the-userprincipalname-attribute"></a>3. userPrincipalName özniteliğini hazırlama

Active Directory, kuruluşunuzdaki son kullanıcıların **sAMAccountName** veya **userPrincipalName** kullanarak dizininizde oturum açmasına izin verecek şekilde tasarlanmıştır. Benzer şekilde, son kullanıcılar iş veya okul hesaplarındaki kullanıcı asıl adını (UPN) kullanarak Microsoft 365 oturum açabilir. Dizin eşitlemesi, AD DS'nizde bulunan UPN'yi kullanarak Azure Active Directory'da yeni kullanıcılar oluşturmaya çalışır. UPN, e-posta adresi gibi biçimlendirilir.

Microsoft 365'de UPN, e-posta adresini oluşturmak için kullanılan varsayılan özniteliktir. **userPrincipalName** (AD DS'de ve Azure AD'de) ve **proxyAddresses** içindeki birincil e-posta adresinin farklı değerlere ayarlanması kolaydır. Bunlar farklı değerlere ayarlandığında, yöneticiler ve son kullanıcılar için karışıklık olabilir.

Karışıklığı azaltmak için bu öznitelikleri hizalamak en iyisidir. Active Directory Federasyon Hizmetleri (AD FS) (AD FS) 2.0 ile çoklu oturum açma gereksinimlerini karşılamak için, Azure Active Directory ve AD DS'nizdeki UPN'lerin eşleştiğinden ve geçerli bir etki alanı ad alanı kullandığından emin olmanız gerekir.

## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a>4. AD DS'ye alternatif bir UPN soneki ekleyin

Kullanıcının kurumsal kimlik bilgilerini Microsoft 365 ortamıyla ilişkilendirmek için alternatif bir UPN soneki eklemeniz gerekebilir. UPN soneki, @ karakterinin sağındaki BIR UPN'nin bölümüdür. Çoklu oturum açma için kullanılan UPN'ler harf, sayı, nokta, kısa çizgi ve alt çizgi içerebilir ancak başka karakter türü içeremez.

Active Directory'ye alternatif bir UPN soneki ekleme hakkında daha fazla bilgi için bkz. [Dizin eşitlemesi için hazırlanma](https://go.microsoft.com/fwlink/p/?LinkId=525430).

## <a name="5-match-the-ad-ds-upn-with-the-microsoft-365-upn"></a>5. AD DS UPN'sini Microsoft 365 UPN ile eşleştirin

Dizin eşitlemesini önceden ayarladıysanız, kullanıcının Microsoft 365 IÇIN UPN'i, kullanıcının AD DS'nizde tanımlanan AD DS UPN'sine uymayabilir. Etki alanı doğrulanmadan önce kullanıcıya lisans atandığında bu durum oluşabilir. Bunu düzeltmek için [PowerShell kullanarak yinelenen UPN'yi düzelterek kullanıcının UPN'sini](https://go.microsoft.com/fwlink/p/?LinkId=396730) güncelleştirerek Microsoft 365 UPN'nin şirket kullanıcı adı ve etki alanıyla eşleştiğinden emin olun. AD DS'de UPN'yi güncelleştiriyorsanız ve Azure Active Directory kimliğiyle eşitlemesini istiyorsanız, AD DS'de değişiklik yapmadan önce kullanıcının Microsoft 365 lisansını kaldırmanız gerekir.

Ayrıca bkz. [Yönlendirilemeyen bir etki alanını (.local etki alanı gibi) dizin eşitlemesi için hazırlama](prepare-a-non-routable-domain-for-directory-synchronization.md).

## <a name="next-steps"></a>Sonraki adımlar

Yukarıda 1 ile 5 arasında bir işlem yaptıktan sonra bkz. [Dizin eşitlemesini ayarlama](set-up-directory-synchronization.md).
