---
title: Yüksek kullanılabilirlik federasyon kimlik doğrulaması Aşama 5 Posta için federasyon kimlik doğrulamasını Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 0f1dbf52-5bff-44cc-a264-1b48641af98f
description: "Özet: Bağlan'de Microsoft 365 için yüksek kullanılabilirlik federal kimlik Microsoft 365 Azure AD Microsoft Azure."
ms.openlocfilehash: e5a11c1b94f9a0297ccfa0a18e1963fae9898f65
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977694"
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-microsoft-365"></a>Yüksek kullanılabilirlik federasyon kimlik doğrulaması Aşama 5: Posta için federasyon kimlik doğrulamasını Microsoft 365

Azure altyapı hizmetlerde Microsoft 365 için yüksek kullanılabilirlik federasyon kimlik doğrulaması dağıtmanın bu son aşamasında, genel sertifika yetkilisi tarafından verilen bir sertifikayı alır ve yükleyebilir, yapılandırmanızı doğrularsınız ve ardından dizin eşitleme sunucusunda Azure AD Bağlan'i yükleyebilir ve çalıştırabilirsiniz. Azure AD Bağlan, federasyon Microsoft 365 için active directory aboneliğinizi, Active Directory Federasyon Hizmetleri (AD FS) ve web uygulaması ara sunucularınızı yapılandırmaktadır.
  
Tüm [aşamalar için Bkz. Azure'da Microsoft 365](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) için yüksek kullanılabilirlik federal kimlik doğrulamasını dağıtma.
  
## <a name="get-a-public-certificate-and-copy-it-to-the-directory-synchronization-server"></a>Ortak bir sertifikayı almak ve bunu dizin eşitleme sunucusuna kopyalamak için

Aşağıdaki özelliklere sahip bir ortak sertifika yetkiliden dijital sertifika alın:
  
- SSL bağlantıları oluşturmaya uygun bir X.509 sertifikası.
    
- Konu Alternatif Adı (SAN) genişletilmiş özelliği federasyon hizmeti FQDN'nize ayarlanır (örneğin: fs.contoso.com).
    
- Sertifikanın özel anahtarı olması ve PFX biçiminde depolanmış olması gerekir.
    
Buna ek olarak, kuruluş bilgisayarlarının ve cihazlarının dijital sertifikayı alan genel sertifika yetkilisine güvenmesi gerekir. Bu güven, bilgisayar ve cihazlarınız arasında bulunan güvenilir kök sertifika yetkililerine yüklenmiş olan ortak sertifika yetkililerinden bir kök sertifikaya sahip olarak kurulmuş olur. Microsoft Windows bilgisayarlar genellikle yaygın olarak kullanılan sertifika yetkililerinden yüklenmiş bu tür sertifikalara sahiptir. Ortak sertifika yetkilinizin kök sertifikası henüz yüklenmemişse, bunu kuruluşun bilgisayarlarına ve cihazlarına dağıtmanız gerekir.
  
Federasyon kimlik doğrulamasına ilişkin sertifika gereksinimleri hakkında daha fazla bilgi için bkz. Federasyon [yüklemesi ve yapılandırmasının önkoşulları](/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).
  
Sertifikayı alırsanız, dizin eşitleme sunucusunun C: sürücüsüne kopyalayın. Örneğin, dosyayı SSL.pfx olarak adlandırarak dizin eşitleme sunucusundaki C:\\Certs klasöründe depolamalısınız.
  
## <a name="verify-your-configuration"></a>Yapılandırmanızı doğrulama

Artık sizin için Azure AD kimlik doğrulamasını ve Bağlan federasyon kimlik doğrulamasını yapılandırmaya Microsoft 365. Bu denetim listesinden emin olmak için:
  
- Genel etki alanı, Microsoft 365 aboneliğinize eklenir.
    
- Kuruluş kullanıcı Microsoft 365 hesapları, kuruluşun ortak etki alanı adına göre yapılandırılır ve başarıyla oturum açın.
    
- Ortak etki alanı adınıza göre bir federasyon hizmeti FQDN'si belirlediniz.
    
- Federasyon hizmeti FQDN'niz için genel DNS A kaydı, web uygulaması ara sunucuları için İnternet'e yönelik Azure yük dengeleyicinin genel IP adresini belirtir.
    
- Federasyon hizmeti FQDN'niz için özel bir DNS A kaydı, AD FS sunucularının iç Azure yük dengeleyicisi özel IP adresini kullanır.
    
- Federasyon hizmeti FQDN'nize ayarlanmış SAN kümesiyle SSL bağlantıları için uygun, sertifika yetkilisi tarafından düzenlenen ortak sertifika, dizin eşitleme sunucunuzda depolanan bir PFX dosyasıdır.
    
- Ortak sertifika yetkilisinin kök sertifikası bilgisayar ve cihazlarınıza Güvenilen Kök Sertifika Yetkilileri deposuna yüklenir.
    
İşte Contoso kuruluşu için bir örnek:
  
**Azure'da yüksek kullanılabilirlik federal kimlik doğrulama altyapısı için örnek yapılandırma**

![Azure'daki federasyon kimlik doğrulama Microsoft 365 için örnek bir yapılandırma.](../media/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a>Federasyon kimlik Bağlan yapılandırmak için Azure AD Bağlan'i çalıştırma

Azure AD Bağlan aracı, aşağıdaki adımlar ile AD FS sunucularını, web uygulaması ara sunucularını ve Microsoft 365 federasyon kimlik doğrulaması için gereken adımları yapılandırmaktadır:
  
1. Yerel yönetici ayrıcalıklarına sahip bir etki alanı hesabıyla dizin eşitleme sunucunuza bir uzak masaüstü bağlantısı oluşturun.
    
2. Dizin eşitleme sunucusunun masaüstünden Internet Explorer'ı açın ve bağlantısına gidin [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
3. Çalışma Sayfası **Microsoft Azure Active Directory Bağlan** **İndir'e tıklayın ve** sonra da Çalıştır'a **tıklayın**.
    
4. **Azure AD'ye Hoş Geldiniz Bağlan** Kabul **ediyorum'a ve** ardından Devam'a **tıklayın.**
    
5. Hızlı Tıklama **Ayarlar** Özelleştir'e **tıklayın**.
    
6. Gerekli bileşenleri **yükle sayfasında Yükle'ye** **tıklayın**.
    
7. Kullanıcı oturum **açma sayfasında,** **AD FS ile Federasyon'a tıklayın ve** sonra da Sonraki'ye **tıklayın**.
    
8. **Bağlan Azure AD'ye** Ekle sayfasında, Microsoft 365 aboneliğiniz için **Azure AD DC** yöneticisinin adını ve parolasını veya Genel yönetici  hesabını yazın ve ardından Sonraki'ye **tıklayın**.
    
9. Dizinlerinizi **Bağlan**, Orman'da şirket içi Active Directory Etki Alanı Hizmetleri (AD DS) ormanının seçili olduğundan emin **olun, etki** alanı yönetici hesabının adını ve parolasını yazın, Dizin Ekle'ye tıklayın ve sonra da Sonraki'ne **tıklayın.**
    
10. **Azure AD oturum açma yapılandırması sayfasında, Sonraki'ne** **tıklayın**.
    
11. Etki Alanı **ve OU filtreleme sayfasında,** Sonraki'yi **tıklatın**.
    
12. Kullanıcılarınızı **benzersiz olarak tanımlama sayfasında** , Sonraki'yi **tıklatın**.
    
13. Kullanıcıları ve **cihazları filtrele sayfasında** , Sonraki'yi **tıklatın**.
    
14. İsteğe **bağlı özellikler sayfasında** , Sonraki'ne **tıklayın**.
    
15. **AD FS sunucu grubu sayfasında**, Yeni bir **AD FS grubu yapılandır'ı tıklatın**.
    
16. **Gözat'a** tıklayın ve ortak sertifika yetkilisinde yer alan SSL sertifikasının konumunu ve adını belirtin.
    
17. Sorulsa, sertifika parolasını yazın ve Tamam'a **tıklayın**.
    
18. Konu Adı ve **Federasyon Hizmeti** **Adı'nın federasyon** hizmeti FQDN'nize ayar olduğunu doğrulayın ve ardından Sonraki'ye **tıklayın**.
    
19. **AD FS sunucuları sayfasında**, ilk AD FS sunucusunun adını (Tablo M - Öğe 4 - Sanal makine adı sütunu) yazın ve Ekle'ye **tıklayın**.
    
20. İkinci AD FS sunucu adını yazın (Tablo M - Öğe 5 - Sanal makine adı sütunu), Ekle'ye tıklayın ve sonra da Sonraki'ye **tıklayın**.
    
21. **Web Uygulaması Proxy sunucuları sayfasında**, ilk web uygulaması proxy sunucu adını (Tablo M - Öğe 6 - Sanal makine adı sütunu) yazın ve Ekle'ye **tıklayın**.
    
22. İkinci web uygulaması proxy sunucu adını yazın (Tablo M - Öğe 7 - Sanal makine adı sütunu), Ekle'ye tıklayın ve sonra da Sonraki'ye **tıklayın**.
    
23. Etki Alanı **Yöneticisi kimlik bilgileri sayfasında** , etki alanı yöneticisi hesabının kullanıcı adını ve parolasını yazın ve ardından Sonraki'ye **tıklayın**.
    
24. **AD FS hizmet hesabı sayfasında**, kuruluş yöneticisi hesabının kullanıcı adını ve parolasını yazın ve ardından Sonraki'ye **tıklayın**.
    
25. **Azure AD Etki Alanı sayfasındaki** Etki **Alanı'nın** altında, kuruluş dns etki alanı adını seçin ve ardından Sonraki'ye **tıklayın**.
    
26. Yapılandırmaya **hazır sayfasında Yükle'ye** **tıklayın**.
    
27. Yükleme tamamlandı **sayfasında Doğrula'ya** **tıklayın**. Hem intranet hem de İnternet yapılandırmasının başarıyla doğrulanmış olduğunu belirten iki ileti görüyorsanız.
    
  - Intranet iletisi, AD FS sunucularında Azure iç yük dengeleyicinizin özel IP adresini listelesin.
    
  - İnternet iletisi, web uygulaması ara sunucularına yönelik Azure İnternet'e yönelik yük dengeleyicinizin genel IP adresini listelemektedir.
    
28. Yükleme tamamlandı **sayfasında Çıkış'a** **tıklayın**.
    
Burada, sunucuların yer tutucu adlarının yer tutucularının yer tutucularının yer tutucus olduğu son yapılandırma yer alıyor.
  
**Aşama 5: Azure'da yüksek kullanılabilirlik federal kimlik doğrulama altyapısının son yapılandırması**

![Azure'da yüksek kullanılabilirlik Microsoft 365 federasyon kimlik doğrulama altyapısının son yapılandırması.](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Azure'da iş için yüksek kullanılabilirlik Microsoft 365 federasyon kimlik doğrulama altyapınız tamamlanmıştır.
  
## <a name="see-also"></a>Ayrıca Bkz

[Azure'da şirket için yüksek kullanılabilirlik Microsoft 365 federasyon kimlik doğrulamasını dağıtma](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Microsoft 365/test ortamınız için federasyon kimliği](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 çözüm ve mimari merkezi](../solutions/index.yml)

[Federasyon kimliği Microsoft 365](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)
