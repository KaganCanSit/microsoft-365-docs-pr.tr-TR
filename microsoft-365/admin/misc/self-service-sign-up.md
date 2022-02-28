---
title: Kurumda self servis kayıt kullanma
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: seemg, pablom
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- okr_SMB
- commerce_signup
search.appverid: MET150
description: Yeni self Microsoft 365 ve Microsoft Power Apps, Microsoft Power Automate ve Dynamics 365 Finans gibi self servis kayıt programları hakkında bilgi öğrenin.
ms.date: 03/17/2021
ms.openlocfilehash: 87f432be0659d03a1e8f77b682997dc32d1dc111
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985043"
---
# <a name="using-self-service-sign-up-in-your-organization"></a>Kurumda self servis kayıt kullanma

Self servis kaydolma, kurumuz kullanıcıların Microsoft'tan çevrimiçi hizmetlere kaydolmasını kolaylaştırır. Kullanıcılarınız, kendi adına işlem yapmadan aboneliğiniz tarafından ödenen hizmetleri kullanmak veya ücretsiz hizmetleri kullanmak için kaydolama işlemlerine "self servis kayıt" olarak çağrılabilirsiniz.

## <a name="how-self-service-sign-up-works"></a>Self servis kaydolma nasıl çalışır?

Aşağıdaki örnekte, bir okul için kendi kendine kaydolmanın nasıl çalıştığını açık almaktadır. Aynı işlem, kendi kiracılarında kendi kendine programları etkinleştirmiş olan tüm kuruluşlarda da çalışır.

1. Öğrencilerin ve öğretim üyelerinin, kurumunuzla ilişkilendirilen okul e-posta adresleri vardır. Örneğin, posta adresinin jakob@uw.edu Washington Üniversitesi'nde bir öğrenci gösteriyor olabilir.
2. Öğrenciler ve öğretim üyeleri [web](https://go.microsoft.com/fwlink/p/?LinkId=536628) sitemize gider ve kuruluşun sunduğu hizmetlere kaydolmak için kendi e-posta adreslerini kullanırlar; örneğin, Kurumlar için Microsoft 365 Uygulamaları. Ayrıca, sunduğumuz diğer ücretsiz hizmetlere de kaydolabilirsiniz.
3. E-posta adreslerini doğrularız ve böylece e-posta Microsoft 365, Power BI diğer hizmetleri kullanmaya başlayabilirler.
4. İşletme yöneticisi olarak, lisans sayfasındaki Lisanslama sayfasında kimlerin aboneliğe **Microsoft 365 yönetim merkezi**. Bu şekilde, kiracınız için yeni veya tanınmayan hizmetler için lisansların ne zaman olduğunu görebiliriz. Kullanıcıların self servis aboneliklere kaydolup olamayup kaydolamayamak için [, Set-MsolCompanySettings](/powershell/module/msonline/set-msolcompanysettings) PowerShell cmdlet'ini **AllowAdHocSubscriptions parametresiyle** kullanın. Daha fazla bilgi için bkz [. Self servis ayarları nasıl kontrol musunuz?](/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## <a name="available-self-service-programs"></a>Kullanılabilir self servis programlar

Aşağıda, şu anda kullanılabilen self servis programlar ve hizmetler ve hizmetler yermektedir. Yeni programlar eklendikça bu liste güncelleştirilir.

| Program <br/> | Açıklama <br/> | Ek Bilgiler <br/> | Self servis kayıt web sitesi <br/> |
|:-----|:-----|:-----|:-----|
|Office 365 A1**** <br/> |Herhangi bir öğrenci veya öğretmen ücretsiz Office 365'a kaydolmak için okul e-posta adresini kullanabilir ve web için Office uygulamaları, 1 TB OneDrive bulut depolama alanı ve sınıf, ekip ve proje siteleri için SharePoint Online'dan edinebilirsiniz.  <br/> |[Office 365 Eğitim Teknik SSS](/microsoft-365/education/deploy/office-365-education-self-sign-up) <br/> |[Office 365 Eğitim](https://go.microsoft.com/fwlink/p/?linkid=140841) <br/> |
|**Office 365 A1 Plus** <br/> |Uygun öğrenciler ve öğretmenler, yukarıda adı geçen her şeyi ve Office 365 A1 Lisansları içeren Kurumlar için Microsoft 365 Uygulamaları. Kurumlar için Microsoft 365 Uygulamaları; Word, PowerPoint, Excel, Outlook, OneNote, Publisher, Access ve Skype Kurumsal , masaüstü veya dizüstü bilgisayarınıza yüklenmiş olmalıdır.  <br/> |[Office 365 Eğitim Teknik SSS](/microsoft-365/education/deploy/office-365-education-self-sign-up) <br/> |[Office 365 Eğitim](https://go.microsoft.com/fwlink/p/?linkid=140841) <br/> |
|**Power BI** <br/> |Power BI, kullanıcıların yeni ve kolay yollarla verileri görselleştirmelerini, keşifleri paylaşmalarını ve işbirliği yapmalarını sağlar. <br/> Organizasyonunız zaten abonese, kullanıcılara gelişmiş özelliklere sınırlı, ücretsiz erişim sunan "Power BI Pro Bireysel Kullanıcı Deneme Sürümü" lisanslarını da görebilirsiniz.  <br/> |[Power BI içinde daha fazla](./power-bi-in-your-organization.md) <br/> |[Microsoft Power BI](https://go.microsoft.com/fwlink/p/?LinkId=536629) <br/> |
|**Rights Management Services (RMS)** <br/> |Bireyler için RMS, kuruluşta Azure Rights Management (Azure RMS) tarafından korunan hassas dosyalar gönderilmiş olan kullanıcılar için ücretsiz bir self servis aboneliktir; ancak IT bölümü Azure Hak Yönetimi (Azure RMS) veya Active Directory Rights Management Services (AD RMS) uygulamamış olabilir.  <br/> |[Bireyler ve Azure Hak Yönetimi için RMS](/azure/information-protection/rms-for-individuals) <br/> |[Microsoft Hak Yönetimi portalı](https://portal.azure.com/) , böylelikle verilen hakları korunan bir belgeyi açıp aç olmadığınizi kontrol edebilirsiniz.  <br/> |
|**Microsoft Power Apps** <br/> |Kuruluş Power Apps oluşturduğunuz veya başka birinin oluşturduğu ve sizin ile paylaştığı bir uygulamayı çalıştırarak kuruluş verilerini yönetebilirsiniz. Uygulamalar, telefonlar gibi mobil cihazlarda çalışır veya Dynamics 365'i açarak bunları tarayıcıda çalıştırabilirsiniz. Sonsuz bir uygulama çeşiti oluşturabilirsiniz; bütün bunlar C# gibi bir programlama dili öğrenmeden kullanılabilir.  <br/> |[Self servis kayıt Power Apps](/powerapps/maker/signup-for-powerapps) <br/> |[Microsoft Power Apps](https://go.microsoft.com/fwlink/p/?linkid=841462) <br/> |
|**Finansallar için Dynamics 365** <br/> |Küçük ve orta ölçekli işletmeler için eksiksiz bir iş ve finansal yönetim çözümü elde. Finansallar için Dynamics 365, ilk günden başlayarak sıralama, satış, faturalama ve raporlamayı kolaylaştırır.  <br/> |[Finansallar için Microsoft Dynamics 365](https://go.microsoft.com/fwlink/p/?linkid=841466) <br/> |[Finansallar için Microsoft Dynamics 365](https://go.microsoft.com/fwlink/p/?linkid=841466) <br/> |
|**İşlemler için Microsoft Dynamics 365** <br/> |İş yapma hızınızı artırın. İşlemler için Dynamics 365'in eksiksiz ERP araçları, hızla büyümenize yardımcı olmak için genel ölçeklenebilirlik ve dijital zeka sağlar.  <br/> |[İşlemler için Microsoft Dynamics 365](https://go.microsoft.com/fwlink/p/?linkid=841467) <br/> |[İşlemler için Microsoft Dynamics 365](https://go.microsoft.com/fwlink/p/?linkid=841467) <br/> |
|**Microsoft AppSource** <br/> |Microsoft AppSource, Microsoft bulut platformunda yerleşik olarak yazılım ve hizmet olarak sağlanan iş uygulamaları için bir hedeftir. AppSource; Azure, Dynamics 365 ve Office 365 gibi Microsoft ürünlerinin işlevselliğini genişleten yüzlerce uygulama, eklenti ve içerik Power BI.  <br/> |[Microsoft AppSource](https://go.microsoft.com/fwlink/p/?linkid=841474) <br/> |[Microsoft AppSource](https://go.microsoft.com/fwlink/p/?linkid=841474) <br/> |
|**Microsoft İş Ortağı Teşvikleri** <br/> |Microsoft İş Ortağı Ağı üç üyelik türü sağlar. Her tür, işletmenizin büyümesine yardımcı olmak için bir dizi avantaj sağlar. Hedeflerinize ulaşmak için, daha fazla avantaja erişmek ve bizimle ve ağ'daki diğer iş ortaklarıyla ilişkilerinizi geliştirmek için, benzersiz ihtiyaçlara uygun düzeyde programa katılabilirsiniz.  <br/> |[Microsoft İş Ortağı Teşvikleri](https://go.microsoft.com/fwlink/p/?linkid=841469) <br/> |[Microsoft İş Ortağı Teşvikleri](https://go.microsoft.com/fwlink/p/?linkid=841469) <br/> |
|**Microsoft Business Center** <br/> |Microsoft Business Center, Microsoft Ürün ve Hizmet Sözleşmesi (MPSA) ile satın alma yapan müşterilerin portalıdır. <br/> |[Hızlı Başlangıç: Microsoft Business Center'a kaydolma](https://go.microsoft.com/fwlink/p/?linkid=841479) <br/> |[Microsoft Business Center](https://go.microsoft.com/fwlink/p/?linkid=841470) <br/> |
|**Microsoft Toplu Lisans Hizmet Merkezi** <br/> |Microsoft Toplu Lisans Hizmet Merkezi, Enterprise, Eğitim (Kampüs veya Okul), Open Value, Open License ve ISV Telif Sözleşmesi altında satın alınan lisansları görüntüler.  <br/> |[VLSC Eğitim ve Kaynaklar](https://www.microsoft.com/en-us/Licensing/existing-customer/vlsc-training-and-resources.aspx) <br/> |[Toplu Lisans Hizmet Merkezi](https://www.microsoft.com/Licensing/servicecenter/default.aspx) <br/> |
|**Minecraft Education Edition** <br/> |Eğitmenler Minecraft bir eğitim platformu olarak kullanarak her öğrenciyi daha fazlasını elde etmeye teşvik edebilir ve öğrenme tutkusunu teşvik edebilir. Öğrenci potansiyellerinin kilidini açmak için Minecraft kullanmayı Minecraft eğitimci topluluğuna katılın.  <br/> |[Minecraft Education Edition](https://go.microsoft.com/fwlink/p/?linkid=841480) <br/> |[Minecraft Education Edition](https://go.microsoft.com/fwlink/p/?linkid=841471) <br/> |
|**Microsoft Stream** <br/> |Upload, katılımı ve öğrenmeyi geliştirmek için tüm organizasyon genelinde video paylaşabilir ve video paylaşabilirsiniz.  <br/> |[&amp; 0. Gün deneyimine kaydol](https://go.microsoft.com/fwlink/p/?linkid=841472) <br/> |[Microsoft Stream](https://go.microsoft.com/fwlink/p/?linkid=841473) <br/> |
|**Power Automate** <br/> |Power Automate dosyaları eşitlemek, bildirim almak, veri toplamak ve daha fazlası için sık kullanılan uygulama ve hizmetleriniz arasında otomatik iş akışları ayarlamanıza yardımcı olan bir üründür.  <br/> |[Kaydolma ve e-Power Automate](/power-automate/sign-up-sign-in) <br/> |[Power Automate](https://go.microsoft.com/fwlink/p/?linkid=841465) <br/> |
|**Power Virtual Agents** <br/> |Power Virtual Agents, veri kaynağına veya geliştiricilere gerek kalmadan, rehberli, kodsuz grafik arabirim kullanarak kolayca güçlü robotlar oluşturma gücü sağlar. Power Virtual Agents, günümüzde endüstride robot yapıyla ilgili birçok önemli sorunu ele almaktadır. Bu, konuyla ilgili uzmanlarla robotları yapan geliştirme ekipleri arasındaki boşluğu ve sorunu tanıyan ekiplerle robotu güncelleştirmek arasındaki uzun gecikme süresini ortadan kaldırmaz.  <br/> |[Lisanslama ve erişim ayrıntıları](/power-virtual-agents/requirements-licensing) <br/> |[Oturum açma için Power Virtual Agents](https://aka.ms/TryPVA) <br/> |
|**Azure AD B2B** <br/> |Azure Active Directory (Azure AD) işletmeler arasındaki (B2B) işbirliği, ücretli Azure AD hizmetlerinizi kullanmak üzere Dış Kullanıcıları (veya "konuk kullanıcıları") davet etmenizi sağlar. Bazı özellikler ücretsizdir, ancak ücretli Azure AD özellikleri için kiracınıza bir çalışan veya konuk olmayan bir kullanıcı için sahip olduğunuz her Azure AD sürüm lisansı için en çok beş konuk kullanıcı davet edin. <br/> |[Azure AD B2B işbirliğine kaydolmaya yönelik self servis](/azure/active-directory/b2b/self-service-portal) <br/> |[Azure Active Directory B2B işbirliği lisanslama kılavuzu](/azure/active-directory/b2b/licensing-guidance) <br/> |
