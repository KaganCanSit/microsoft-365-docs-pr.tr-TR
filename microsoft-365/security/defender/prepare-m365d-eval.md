---
title: Microsoft 365 Defender deneme laboratuvarı ortamınızı hazırlama
description: Deneme laboratuvarınızı veya pilot ortamınızı ayarlarken paydaş oturum açma, zaman çizelgeleri, ortamla ilgili dikkate alınacak noktalar ve benimseme Microsoft 365 Defender hazırlama
keywords: Microsoft 365 Defender hazırlığı, pilot Microsoft 365 Defender için hazırlık, pilot proje Microsoft 365 Defender hazırlamak için bir pilot çalışma Microsoft 365 Defender  proje, dağıtma, hazırlama, paydaş, zaman çizelgesi, ortam, uç nokta, sunucu, yönetim, benimseme
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 7ebb7074b0e06eda96d21142044bd8b9997e094b
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2021
ms.locfileid: "62959680"
---
# <a name="prepare-your-microsoft-365-defender-trial-lab-or-pilot-environment"></a>Microsoft 365 Defender test laboratuvarınızı veya pilot ortamınızı hazırlama

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Deneme Microsoft 365 Defender pilot ortamı oluşturmak ve bu ortamı dağıtmak üç aşamalı bir işlemdir:

|![Aşama 1: Hazırlama](../../media/phase-diagrams/prepare.png)<br/>Aşama 1: Hazırlama |[![Aşama 2: Ayarlama](../../media/phase-diagrams/setup.png)](setup-m365deval.md)<br/>[Aşama 2: Ayarlama](setup-m365deval.md) |[![Aşama 3: Ekleme](../../media/phase-diagrams/onboard.png)](config-m365d-eval.md)<br/>[Aşama 3: Ekleme](config-m365d-eval.md) | [![Pilot'a geri dön](../../media/phase-diagrams/backtopilot.png)](m365d-pilot.md)<br/>[Pilot playbook'a geri dön](m365d-pilot.md) |
|--|--|--|--|
|*Buradasınız!* | || |

Şu anda hazırlık aşamasındayız.


Hazırlık, başarılı bir dağıtım için çok önemli. Bu bölüm, test laboratuvarı veya pilot ortamı oluşturmak üzere test laboratuvarı veya test ortamı oluşturmak üzere göz önünde bulundurmalısınız Microsoft 365 Defender.

## <a name="prerequisites"></a>Önkoşullar
Lisans, donanım ve yazılım gereksinimleri ve diğer yapılandırma ayarları hakkında bilgi edinmek ve bu özellikleri Microsoft 365 Defender. Kimlik için Microsoft Defender, [Microsoft 365 Defender](/microsoft-365/security/defender/prerequisites) [için Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements), kimlik için [Microsoft Defender, Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) için Microsoft Defender, Kimlik için [Microsoft Defender](/azure-advanced-threat-protection/atp-prerequisites) ile ilgili en [Microsoft Cloud App Security](/azure-advanced-threat-protection/atp-prerequisites).

## <a name="stakeholders-and-sign-off"></a>Paydaşlar ve oturum kapatma
Projede yer alan tüm paydaşları ve değerlendirme ya da pilot proje çalıştırma için kimlerin oturum açması, gözden geçirmesi veya bilgi sahibi olması gerekip gerek bekleyeceğini belirleme.

>[!NOTE]
>Tüm kuruluşlar, bu tür rollere sahip olmak için güvenlik kuruluşu vadesine sahip olabilir. Böyle bir durumda, liderlik ekibinin gözden geçirme ve onay hesapabiliteleriyle ilgili danışması gerekir.

Aşağıdaki tabloya organizasyonunıza uygun olarak proje katılımcıları ekleyin.

-   SO = Bu projede oturum açma

-   R = Bu projeyi gözden geçirme ve girdi sağlama

-   I = Bu proje hakkında bilgi verildi

| Name                 | Rol                                                                                                                                                                                                          | Eylem |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------|
| Ad ve e-posta girin | **Baş Bilgi Güvenliği Görevlisi (CISO)** *Yeni teknoloji dağıtımı için kuruluş içinde sponsor olarak hizmet veren bir yönetim temsilcisi.*                                                  | SO     |
| Ad ve e-posta girin | **Siber Savunma Operasyon Merkezi (CDOC)** Genel Müdürü BU değişikliğin müşteriler güvenlik işlemleri ekibinde bulunan süreçlerle nasıl hizalı olduğunu tanımlamaktan sorumlu *CDOC ekibinden bir temsilci.*       | SO     |
| Ad ve e-posta girin | **Güvenlik** *Mimarı Bu değişikliğin kuruluşta temel* Güvenlik mimarisiyle nasıl uyumlu olduğunu tanımlamaktan sorumlu Güvenlik ekibinden bir temsilci.                         | R      |
| Ad ve e-posta girin | **workplace Architect** *A representative from IT team of defining how of the this change is aligned with the core workplace architecture in organization.*                             | R      |
| Ad ve e-posta girin | **Güvenlik Analisti** CDOC ekibinin algılama özellikleri, kullanıcı deneyimi ve bu değişikliğin genel kullanışlılığıyla ilgili geri bildirim sağlayabilmek için güvenlik işlemleri perspektifinden *bir temsilci.* | I      |

## <a name="prepare-your-azure-active-directory"></a>Çalışmanızı Azure Active Directory
Active Directory ile şirket içi eşitleme arasında eşitlemeyi zaten etkinleştirdiyseniz bu Azure Active Directory atlayabilirsiniz. Çalışma sayfalarındaki mevcut en iyi yöntemler belgelerini Azure Active Directory. Aşağıdaki adımlar, projeyle ilgili değerlendirme yapmak veya çalıştırmak için Microsoft 365 Defender en iyi duruma getirilmiş.

1. Azure AD [Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade) > **portala Bağlan**. 
![Portal Azure Active Directory resmi](../../media/mtp-eval-1.png) <br> 

2. **Siteden indir'Microsoft Azure Active Directory Bağlan** ve Etki Alanı Denetleyicinize aktar'ı tıklatın.
![Azure Active Directoru Bağlan sayfasının resmi](../../media/mtp-eval-2.png) <br>

3. Etki alanı denetleyicisinde Kayıt Sihirbazı'Azure Active Directory Bağlan izleyin. Lisans koşullarını ve gizlilik bildirimini okuyun ve kabul ediyorsanız onay kutusunu seçin. **Devam**'ı tıklatın.
![Azure AD Bağlan sayfasının görüntüsü](../../media/mtp-eval-3.png) <br>

4. **Express Ayarlar'a gidin**.
![Express Ayarlar sayfasının görüntüsü](../../media/mtp-eval-4.png) <br>

5. Genel yönetici kimlik bilgilerinizi girin. **İleri**'ye tıklayın.
![Genel Bağlan kimlik bilgilerinizi girmeniz gereken Azure AD'ye giriş sayfasının resmi](../../media/mtp-eval-5.png) <br>

6. Active Directory Etki Alanı Hizmetleri kuruluş yöneticisi kimlik bilgilerinizi girin. **İleri**'ye tıklayın.
![Kimlik Bağlan girmeniz gereken AD DS'ye Giriş sayfası resmi](../../media/mtp-eval-6.png) <br>

7. **Yapılandırmayı onaylamak** için Yükle'ye tıklayın.
![Yapılandırma onay sayfasının görüntüsü](../../media/mtp-eval-7.png) <br>

8. Tebrikler, başarıyla yapılandırdınız ve Azure Active Directory Bağlan.
![Başarıyla yapılandırılan bir sayfa Azure Active Directory Bağlan görüntüsü](../../media/mtp-eval-8.png) <br>

Artık [Active Directory'ye kullanıcı ve grup ekleyebilir](/azure-advanced-threat-protection/atp-playbook-setup-lab#bkmk_hydrate) ve [SAM-R ilkesi yapılandırabilirsiniz](/azure-advanced-threat-protection/atp-playbook-setup-lab#configure-sam-r-capabilities-from-contosodc).  


## <a name="configuration-order"></a>Yapılandırma sırası
Aşağıdaki tablo, Microsoft'un deneme laboratuvarı veya pilot ortam dağıtımınız Microsoft 365 Defender bileşenleri yapılandırmak için öner olduğu sırayı gösterir.

| Bileşen                               | Açıklama                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Yapılandırma sırası sırası |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
|Office 365 için Microsoft Defender|Microsoft Defender For Office 365, e-posta iletileri, bağlantılar (URL'ler) ve işbirliği araçları tarafından tehditlere karşı organizasyonlarınızı korur. <br> [Daha fazla bilgi edinin.](/microsoft-365/security/office-365-security/defender-for-office-365)                                                                                                                                                                                                                                             | 1                   |
|Kimlik için Microsoft Defender|Identity için Microsoft Defender, Active Directory sinyallerini kullanarak gelişmiş tehditleri, güvenliği tehlikeye atılmış kimlikleri ve kuruluşa yönlendirilen kötü amaçlı insider eylemlerini tanımlar, algılar ve araştırr. <br> [Daha fazla bilgi edinin](/azure-advanced-threat-protection/).| 2 |
|Microsoft Cloud App Security| Microsoft Cloud App Security bulut üzerinde çalışan bir Bulut Erişimi Güvenlik Aracısı (CASB) aracıdır. Tüm bulut hizmetleriniz genelinde siber tehditleri tespit etmek ve buna karşı mücadele etmek için zengin görünürlük, veri seyahati üzerinde denetim ve gelişmiş analiz sağlar. <br> [Daha fazla bilgi edinin](/cloud-app-security/).                                                                                                                                                                                                                                                                                                                                                                       |3                   |
|Uç Nokta için Microsoft Defender | Uç Nokta ve uç noktada algılama ve yanıtlama için Microsoft Defender, gerçek zamanlı olarak yakın olan ve işlem için değiştirilebilir gelişmiş saldırı algılamaları sağlar. Güvenlik analistleri uyarıları etkili bir şekilde önceliklendirmek, ihlallerin tam kapsamı için görünürlük kazanmak ve tehditleri düzeltmek için yanıt eylemleri gerçekleştirmektedir. <br> [Daha fazla bilgi edinin.](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)                                     |4                   |                                                                                                                                                                                                                                    

## <a name="next-step"></a>Sonraki adım
|![Aşama 2: Kurulum](../../media/setup.png) <br>[Aşama 2: Kurulum](setup-m365deval.md) | Test laboratuvarınızı Microsoft 365 Defender pilot ortamınızı ayarlama
|:-------|:-----|
