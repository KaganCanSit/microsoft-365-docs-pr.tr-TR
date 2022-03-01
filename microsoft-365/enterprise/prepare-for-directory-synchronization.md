---
title: Eşitlemeye dizin eşitlemesi Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Kullanıcıları dizin eşitleme kullanarak Microsoft 365 sağlama için nasıl hazırlayacaklarını ve bu yöntemi kullanmanın uzun vadedeki avantajlarını açıklar.
ms.openlocfilehash: 5a8914091eb8df62ba71c8ddff35c3fb355fa031
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63014390"
---
# <a name="prepare-for-directory-synchronization-to-microsoft-365"></a>Eşitlemeye dizin eşitlemesi Microsoft 365

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

[2](protect-your-global-administrator-accounts.md). Adımda yönetici hesapları için karma kimlik modelini ve yapılandırılmış korumayı seçtiyseniz ve bu çözümün [3](microsoft-365-secure-sign-in.md). adımlarında kullanıcı hesaplarını yapılandırdıysanız, bir sonraki göreviniz dizin eşitlemesini dağıtmaktır. Kurum için dizin eşitlemenin avantajları şunlardır:

- Kuruluş yönetim programlarını azaltma
- İsteğe bağlı olarak çoklu oturum açma senaryosunu etkinleştirme
- E-postada hesap değişikliklerini Microsoft 365

Dizin eşitlemesini kullanmanın avantajları hakkında daha fazla bilgi için bkz. Azure Active Directory [(Azure AD) ile karma kimlik](/azure/active-directory/hybrid/whatis-hybrid-identity).

Ancak, Dizin eşitlemesi, Active Directory Etki Alanı Hizmetlerinizin (AD DS) Microsoft 365 aboneliğinizin Azure AD kiracısına en az hatayla eşitlenmesi için planlama ve hazırlık gerektirir.

En iyi sonuçları elde etmek için bu adımları izleyin.

> [!NOTE]
> ASCII olmayan karakterler AD DS kullanıcı hesabı öznitelikler için eşitlanmaz.

## <a name="ad-ds-preparation"></a>AD DS Hazırlığı

Eşitleme kullanarak E-posta Microsoft 365 sorunsuz bir geçiş sağlamak için dizin eşitleme dağıtımınıza başlamadan önce AD DS ormanınızı hazırlamanız Microsoft 365 gerekir.
  
Dizin hazırlığınız aşağıdaki görevlere odaklan olmalıdır:

- Yinelenen **proxyAddress ve** **userPrincipalName özniteliklerini** kaldırın.
- Boş ve geçersiz **userPrincipalName özniteliklerini** geçerli **userPrincipalName öznitelikleriyle** güncelleştirme.
- **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname** ve **userPrincipalName** özniteliklerinde geçersiz ve şüpheli karakterleri kaldırın. Öznitelikleri hazırlama hakkında ayrıntılı bilgi için bkz. [Eşitleme Aracı tarafından eşitlenen özniteliklerin Azure Active Directory.](https://go.microsoft.com/fwlink/p/?LinkId=396719)

    > [!NOTE]
    > Bunlar, Azure AD'nin eşitleye Bağlan öznitelikleridir. 
  
## <a name="multi-forest-deployment-considerations"></a>Çok ormanlı dağıtımda dikkate alınacak noktalar

Birden çok orman ve SSO seçeneği için Azure [AD'nin Özel Yüklemesi'Bağlan](/azure/active-directory/hybrid/how-to-connect-install-custom).
  
Kuruluşta kimlik doğrulama için birden çok orman varsa (oturum açma ormanları), şunları kesinlikle öneririz:
  
- **Ormanlarınızı birleştirmeyi düşünün.** Genel olarak, birden çok ormanın bakımını yapmak daha fazla yük getirir. Kuruluşta ayrı ormanları dikte etmek için güvenlik kısıtlamaları olmadığı sürece, şirket içi ortamınızı basitleştirmeyi göz önünde bulundurabilirsiniz.
- **Yalnızca birincil oturum açma ormanınızı kullanın.** İlk dağıtım Microsoft 365 için yalnızca birincil oturum açma ormanınıza dağıtım Microsoft 365. 

Çok ormanlı AD DS dağıtımınızı birleştiramıyorsanız veya kimlikleri yönetmek için başka dizin hizmetleri kullanıyorsanız, bunları Eşitlemek için Microsoft'un veya bir iş ortağının yardımıyla eşitlemeniz mümkün olabilir.
  
Daha [fazla bilgi için bkz. Azure AD Bağlan Topolojileri](/azure/active-directory/hybrid/plan-connect-topologies).
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a>Dizin eşitlemeye bağımlı olan özellikler
  
Aşağıdaki özellikler ve işlevler için dizin eşitlemesi gereklidir:
  
- Azure AD Sorunsuz Tek Sign-On (SSO)
- Skype birlikte var olan
- Exchange dağıtımı:
  - Şirket içi ortamınız ve şirket içi ortamınız arasında tümüyle paylaşılan genel Exchange adres listesi (GAL) Microsoft 365.
  - Farklı posta sistemlerinden GAL bilgilerini eşitleme.
  - Yeni hizmet tekliflerinden kullanıcı ekleme ve Microsoft 365 kaldırma özelliği. Bunun için aşağıdakiler gerekir:
  - Dizin eşitleme kurulumu sırasında iki yollı eşitleme yapılandırıldığından emin olun. Varsayılan olarak, dizin eşitleme araçları dizin bilgilerini yalnızca buluta yazar. İki yollu eşitlemeyi yapılandırsanız, geri yazma işlevini etkinleştirirsiniz; böylece buluttan sınırlı sayıda nesne özniteliği kopyalanır ve sonra bunlar yerel AD DS'nize geri yazılır. Geri yazma, karma moda Exchange olarak da adlandırılır. 
  - Şirket içi veya Exchange dağıtımı
  - Bazı kullanıcı posta kutularını şirket içinde saklayarak Microsoft 365 kutularını başka posta kutularına taşıma özelliği.
  - Kasa şirket içi gönderenler ve engellenen gönderenler bu iletiye Microsoft 365.
  - Temel temsilci ve adına gönderme e-posta işlevselliği.
  - Tümleşik bir şirket içi akıllı kartınız veya çok faktörlü kimlik doğrulama çözümünüz var.
- Fotoğrafları, küçük resimleri, konferans odalarını ve güvenlik gruplarını eşitleme

## <a name="1-directory-cleanup-tasks"></a>1. Dizin temizleme görevleri

AD DS'nizi Azure AD kiracınıza eşitlemeden önce AD DS'nizi temizlemeniz gerekir.

> [!IMPORTANT]
> Eşitlemeden önce AD DS temizleme işlemini gerçekleştiremeden önce bu işlemi gerçekleştirersiniz, dağıtım işleminin önemli ölçüde olumsuz etkilenmesine yol açabilirsiniz. Dizin eşitleme, hataları tanımlama ve yeniden eşitleme döngüsünün üzerinden günler, hatta haftalar sürebilir.

AD DS'niz içinde, her kullanıcı hesabına bir lisans atanmış olan kullanıcı hesapları için aşağıdaki temizleme Microsoft 365 yapın:

1. **proxyAddresses özniteliğinde geçerli ve benzersiz bir e-posta adresi olduğundan emin** olun.

2. **proxyAddresses özniteliğinde tüm yinelenen değerleri** kaldırın.

3. Mümkünse, kullanıcının kullanıcı nesnesinde **userPrincipalName** özniteliği için geçerli ve benzersiz bir **değerden emin** olun. En iyi eşitleme deneyimini sağlamak için, AD DS UPN'nin Azure AD UPN'yle eş olduğundan emin olur. Kullanıcının **userPrincipalName** özniteliği için değeri yoksa, kullanıcı nesnesinin **sAMAccountName** özniteliği  için geçerli ve benzersiz bir değer içermesi gerekir. **userPrincipalName özniteliğinde tüm yinelenen değerleri** kaldırın.

4. Genel adres listesinin (GAL) en iyi kullanımı için, AD DS kullanıcı hesabının aşağıdaki özniteliklerinde yer alan bilgilerin doğru olduğundan emin olun:

   - givenName
   - surname
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
   - Posta Kodu
   - Ülke veya Bölge

## <a name="2-directory-object-and-attribute-preparation"></a>2. Dizin nesnesi ve özniteliği hazırlama

AD DS'niz ve E-Microsoft 365 başarılı bir şekilde dizin eşitlemesi için AD DS özniteliklerinizin düzgün bir biçimde hazır olması gerekir. Örneğin, belirli karakterlerin, belirli bir ortamla eşitlenen belirli özniteliklerde kullanılmay olduğundan emin Microsoft 365 gerekir. Beklenmedik karakterler dizin eşitlemenin başarısız olmasına neden olmaz, ancak bir uyarı geri dönebilirsiniz. Geçersiz karakterler dizin eşitlemenin başarısız olmasına neden olur.

Dizin eşitleme, bazı AD DS kullanıcılarınızın bir veya birden çok yinelenen özniteliği varsa da başarısız olur. Her kullanıcının benzersiz öznitelikleri olması gerekir.

Hazırlaması gereken öznitelikler burada listelenmiştir:

- **displayName**

  - Öznitelik kullanıcı nesnesinde bulunuyorsa, öznitelik kullanıcı nesnesiyle Microsoft 365.
  - Bu öznitelik kullanıcı nesnesinde bulunuyorsa, özniteliğin bir değeri olması gerekir. Başka bir ifadeyle, öznitelik boş bırakılamaz.
  - En fazla karakter sayısı: 256

- **givenName**

  - Öznitelik kullanıcı nesnesinde bulunuyorsa, öznitelik MICROSOFT 365 ile eşitlenir, Microsoft 365 öznitelik gerektirmez veya kullanmaz.
  - En fazla karakter sayısı: 64

- **posta**

  - Öznitelik değeri dizin içinde benzersiz olmalıdır.

    > [!NOTE]
    > Yinelenen değerler varsa, bu değere sahip olan ilk kullanıcı eşitlenir. Sonraki kullanıcılar bu konuşmada Microsoft 365. Her iki kullanıcının da aynı dosyada Microsoft 365 için AD DS'de iki değeri de veya AD DS'de her iki değeri de Microsoft 365.

- **mailNickname** (Exchange diğer adı)

  - Öznitelik değeri noktayla (.) başamaz.
  - Öznitelik değeri dizin içinde benzersiz olmalıdır.

    > [!NOTE]
    > Eşitlenmiş adda alt çizgi ("_") bu özniteliğin özgün değerinin geçersiz karakterler içerdiğini belirtir. Bu öznitelik hakkında daha fazla bilgi için bkz[. Exchange özniteliğini görme](/powershell/module/exchange/set-mailbox).
    >

- **proxyAddresses**

  - Birden çok değerli öznitelik
  - Değer başına en fazla karakter sayısı: 256
  - Öznitelik değeri boşluk içermeli.
  - Öznitelik değeri dizin içinde benzersiz olmalıdır.
  - Geçersiz karakterler: \< \> ( ) ; , [ ] "
  - Aksan, aksan ve tilde gibi aksan işaretleri içeren harfler geçersiz karakterlerdir.

    Geçersiz karakterlerin, tür sınırlayıcıdan ve ":" karakterlerini (örneğin, izin verilen karakter) SMTP:User@contso.com ancak geçersiz SMTP:user:M@contoso.com olduğunu unutmayın.

    > [!IMPORTANT]
    > Tüm Basit Posta Aktarım Protokolü (SMTP) adresleri e-posta iletisi standartlarına uygun olmalıdır. Yinelenen veya istenmeyen adresleri varsa kaldırın.

- **sAMAccountName**

  - En fazla karakter sayısı: 20
  - Öznitelik değeri dizin içinde benzersiz olmalıdır.
  - Geçersiz karakterler: [ \ " | , / : \< \> + = ; ? \* ']
  - Kullanıcının geçersiz bir **sAMAccountName** özniteliği varsa, ancak geçerli bir **userPrincipalName** özniteliği varsa, kullanıcı hesabı Kullanıcı Adı özniteliğinde Microsoft 365.
  - Hem **sAMAccountName** hem **de userPrincipalName** geçersizse, AD DS **userPrincipalName** özniteliği güncelleştirilebilir.

- **sn** (surname)

  - Öznitelik kullanıcı nesnesinde bulunuyorsa, öznitelik MICROSOFT 365 ile eşitlenir, Microsoft 365 öznitelik gerektirmez veya kullanmaz.

- **targetAddress**

    Kullanıcı için doldurulan **targetAddress** özniteliğinin (örneğin, SMTP:tom@contoso.com) Microsoft 365 GAL'de görünmesi gerekir. Üçüncü taraf mesajlaşma geçişi senaryolarında, bunun için AD DS Microsoft 365 şema uzantısının ne olduğu gerekir. Varsayılan Microsoft 365 uzantısı, AD DS'den bir dizin eşitleme aracı kullanılarak doldurulan Microsoft 365 nesneleri yönetmek için başka yararlı öznitelikler de ekler. Örneğin, gizli posta kutularını veya dağıtım gruplarını yönetmek için **msExchHideFromAddressLists** özniteliği eklenir.

  - En fazla karakter sayısı: 256
  - Öznitelik değeri boşluk içermeli.
  - Öznitelik değeri dizin içinde benzersiz olmalıdır.
  - Geçersiz karakterler: \ \< \> ( ) ; , [ ] "
  - Tüm Basit Posta Aktarım Protokolü (SMTP) adresleri e-posta iletisi standartlarına uygun olmalıdır.

- **userPrincipalName**

  - **userPrincipalName** özniteliği, kullanıcı adının ardından bir @ işareti ve bir etki alanı adı olduğu İnternet stili oturum açma biçiminde olmalıdır: örneğin, user@contoso.com. Tüm Basit Posta Aktarım Protokolü (SMTP) adresleri e-posta iletisi standartlarına uygun olmalıdır.
  - **userPrincipalName** özniteliği için en fazla karakter sayısı 113'tir. İşaret işaretinin (@) öncesinde ve sonrasında belirli sayıda karaktere izin verilir:
  - İşaretten (@) önce bulunan kullanıcı adı için en fazla karakter sayısı: 64
  - İşaretden (@) sonraki etki alanı adı için en fazla karakter sayısı: 48
  - Geçersiz karakterler: \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "
  - İzin verilen karakterler: A – Z, a - z, 0 – 9, ' . - _ ! # ^ ~
  - Aksan, aksan ve tilde gibi aksan işaretleri içeren harfler geçersiz karakterlerdir.
  - @ karakteri her **userPrincipalName değerinde** gereklidir.
  - @ karakteri her **userPrincipalName değerinin ilk karakteri** olamaz.
  - Kullanıcı adı nokta (.), ve işareti (),&amp; boşluk veya @ işaretiyle sona erer.
  - Kullanıcı adı boşluk içeremez.
  - Yönlendirilebilir etki alanları kullanılmalıdır; örneğin, yerel veya iç etki alanları kullanılamaz.
  - Unicode, alt çizgi karakterlerine dönüştürülür.
  - **userPrincipalName** dizinde hiçbir yinelenen değer içeramaz.

## <a name="3-prepare-the-userprincipalname-attribute"></a>3. userPrincipalName özniteliğini hazırlama

Active Directory, kuruluşta son kullanıcıların **sAMAccountName** veya **userPrincipalName** kullanarak dizinde oturum açmasını sağlayacak şekilde tasarlanmıştır. Benzer şekilde, son kullanıcılar Microsoft 365 veya okul hesaplarının kullanıcı asıl adını (UPN) kullanarak Microsoft 365'de oturum açmalarını sağlar. Dizin eşitleme, AD DS'Azure Active Directory aynı UPN'yi kullanarak e-postada yeni kullanıcılar oluşturmayı çalışır. UPN, e-posta adresi gibi biçimlendirildi.

UpN Microsoft 365, e-posta adresini oluşturmak için kullanılan varsayılan özniteliktir. **userPrincipalName** (AD DS'de ve Azure AD'de) ve **proxyAddresses'in** birincil e-posta adresini farklı değerlere ayarlamak kolaydır. Bu değerler farklı değerlerle ayarlanırsa, yöneticiler ve son kullanıcılar için karışıklığa neden olabilir.

Karışıklığı önlemek için bu öznitelikleri hizalamak en iyisidir. Active Directory Federasyon Hizmetleri (AD FS) 2.0 ile çoklu oturum açma gereksinimlerini karşılamak için, Azure Active Directory'daki ve AD DS'nizin UPN'lerinin eş olduğundan ve geçerli bir etki alanı ad uzayı kullanıyor olduğundan emin olun.

## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a>4. AD DS'ye alternatif bir UPN soneki ekleme

Kullanıcının şirket bilgilerini aynı ortamda ilişkilendirmek için alternatif bir UPN soneki eklemeniz Microsoft 365 olabilir. UPN soneki, @ karakterinin sağ tarafı olan UPN'nin bir kısmıdır. Çoklu oturum açma için kullanılan UPN'ler harf, sayı, nokta, tire ve alt çizgi içerebilir, ancak başka karakter içeremez.

Active Directory'ye alternatif bir UPN soneki ekleme hakkında daha fazla bilgi için bkz. [Dizin eşitlemeye hazırlanma](https://go.microsoft.com/fwlink/p/?LinkId=525430).

## <a name="5-match-the-ad-ds-upn-with-the-microsoft-365-upn"></a>5. AD DS UPN'lerini Microsoft 365 UPN ile

Dizin eşitlemesini zaten ayarladıysanız, kullanıcının MICROSOFT 365 UPN'si, kullanıcının AD DS'sinde tanımlanan AD DS UPN'sini eşleşmez. Bu durum, kullanıcıya etki alanı doğrulanmadan önce bir lisans atandığı zaman ortaya çıkabilir. Bunu düzeltmek için, [PowerShell kullanarak yinelenen UPN'leri](https://go.microsoft.com/fwlink/p/?LinkId=396730) düzeltin ve kullanıcının UPN'sini güncelleştirin ve Microsoft 365 UPN'nin şirket kullanıcı adı ve etki alanıyla eşleşmesini sağlamaya yardımcı olun. AD DS'de UPN'yi güncelleştiriyorsanız ve UPN'nin AZURE ACTIVE DIRECTORY kimliğiyle eşitlemesini yapıyorsanız, AD DS'de değişiklik yapmadan önce Microsoft 365'de kullanıcının lisansını kaldırmanız gerekir.

Ayrıca bkz [. Yönlendirilebilir olmayan etki alanını (.local etki alanı gibi) dizin eşitlemesi için hazırlama](prepare-a-non-routable-domain-for-directory-synchronization.md).

## <a name="next-steps"></a>Sonraki adımlar

Yukarıda 1 ile 5 arasında bir işlemi tamamladikten sonra bkz [. Dizin eşitlemesini ayarlama](set-up-directory-synchronization.md).
