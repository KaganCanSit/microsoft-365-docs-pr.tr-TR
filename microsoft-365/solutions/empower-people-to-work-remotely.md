---
title: Karma çalışma için altyapınızı ayarlama Microsoft 365
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-overview
- M365initiative-coredeploy
ms.custom: seo-marvel-jun2020
keywords: evden çalışma, evden çalışma, karma, uzaktan çalışan, karma iş, uzak çalışanlar, karma bağlantı, uzaktan erişim, telekom, telework, teleworking, teleworking, mobil iş, uzaktan iş, her yerden çalışma, esnek çalışma
description: Karma çalışanlarının güvenli bir şekilde şirket içi kaynaklara ve kaynak kullanımına erişmesi için altyapı katmanlarında Microsoft 365 geçin.
ms.openlocfilehash: 0370d30584021ab8560a24c7e54e3a7c7aadeb1f
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2022
ms.locfileid: "63015350"
---
# <a name="set-up-your-infrastructure-for-hybrid-work-with-microsoft-365"></a>Karma çalışma için altyapınızı ayarlama Microsoft 365

Çalışanın üretkenliğini ve işbirliğini güvence altına almak ve iyileştirmek için, site içi ve uzak çalışanların kolayca ve güvenli bir şekilde kurum içi ve bulut tabanlı bilgilerine, araçlarına ve kaynaklarına erişmesine izin verebilirsiniz. Bu çözüm, çalışanlarınızı nerede olursa olsunlar en iyi çalışmalarını yapmaları için güçlendiren önemli altyapı katmanlarının dağıtımında adım adımlarını ilerler.

Karma çalışanlar çeşitli konumlarda sitede veya uzaktan çalışabiliyor. Geleneksel bir ofisten uzakta çalışanların çalışmasına izin verme, birçok kuruluşun şunları yapmak için önemlidir:

- Taşınmak istemeyen veya esnek bir çalışma ortamı gerektiren çalışanları işe alma ve işe alma.
- Çalışanların iletişimini azaltarak çalışanların üretken olmak için daha fazla zamanı olmalı ve iş dışındaki etkinlikleri stres altında azaltabilirsiniz.
- Ofis alanı tasarrufu sağlar.

Microsoft 365, karma çalışanlarınızı sitede veya uzaktan çalışma gücü veren özelliklere sahip olur.

![Karma çalışanlarınızı daha iyi Microsoft 365.](../media/empower-people-to-work-remotely/2-m365-remoteworker-solution-businessoverview.png)

> [!NOTE]
> Bu kaynaklara yeni Microsoft 365, bu [kaynaklara bakın](https://www.microsoft.com/microsoft-365).

Dağıtım sürecine genel bir bakış için bu videoyu izleyin.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4F1af]

Karma çalışan üretkenliğini etkinleştirmek için site içi ve bulut tabanlı altyapıyı yöneten BT uzmanları için, bu çözüm şu önemli özellikleri sağlar:

- Bağlı

  Dünyanın herhangi bir yerinde ve istediğiniz zaman, çalışanlarınız şunların erişimine sahip olabilir:

  - Yeni aboneliğinize bulut tabanlı Microsoft 365 verileri.

  - Şirket içi uygulama veri merkezleri tarafından sunulanlar gibi kuruluş kaynakları.

- Güvenli

  Oturum açmalar, çok faktörlü kimlik doğrulaması (MFA) ile ve Microsoft 365'nin yerleşik güvenlik özellikleriyle güvence altına alınır ve Windows 11 veya 10, kötü amaçlı yazılımlara, kötü amaçlı saldırılara ve veri kaybına karşı koruma sağlar.

- Yönetilen

  Karma çalışanın cihazları güvenlik ayarları ve izin verilen uygulamalarla buluttan yönetilebilir ve sistem durumuna uyumluluk gerektirir.

- İşbirliği ve üretken

  Karma çalışanlarınız, şu son derece işbirliğine dayalı bir şekilde şirket içi çalışanlar kadar üretken olabilir:

  - Çevrimiçi toplantılar ve sohbet oturumları Teams.

  - Bulut tabanlı dosya depolaması için paylaşılan çalışma alanları; genel erişilebilirlik ve erişilebilirlik özellikleriyle ve erişilebilirlik özellikleriyle gerçek SharePoint OneDrive.

  - Işi bölmek ve iş yapmak için paylaşılan görevler ve iş akışları.

Sorunsuz oturum açma deneyimi için, şirket içi Active Directory Etki Alanı Hizmetleri (AD DS) kullanıcı hesaplarınız Azure Active Directory (Azure AD) ile eşitlenmiş olmalıdır. Windows 11 veya 10 cihazla korumak için Intune'a kaydolmaları gerekir. Burada, altyapının üst düzey bir görünümü ve daha sonra yer var.

![Karma çalışanları için temel altyapıya sahip Microsoft 365.](../media/empower-people-to-work-remotely/remote-workers-basic-infrastructure.png)

Karma çalışanlarınız için Microsoft 365 özelliklerini etkinleştirmek üzere bu özellik Microsoft 365 kullanın.

|Özellik veya özellik|Açıklama|Lisanslama|
|---|---|---|
|Güvenlik varsayılanları ile zorunlu kılınan MFA|Oturum açma işlemleri için ikinci bir kimlik doğrulama biçimi gerektirerek güvenliği tehlikeye atılmış kimliklere ve cihazlara karşı koruyun. Güvenlik varsayılanları, tüm kullanıcı hesapları için MFA gerektirir.|Microsoft 365 E3 E5|
|Koşullu Erişim ile zorunlu kılınan MFA|Koşullu Erişim ilkeleriyle oturum açmanın özelliklerine bağlı olarak MFA gerektirme.|Microsoft 365 E3 E5|
|Risk tabanlı Koşullu Erişim ile zorunlu kılınan MFA|Kullanıcının Azure AD Kimlik Koruması ile oturum açma riski temel alarak MFA gerektirme.|Microsoft 365 E5 lisansları olan E3 Azure AD Premium P2 E3|
|Self-Service Sıfırlama (SSPR)|Kullanıcılarının parolalarını veya hesaplarını sıfırlamasına veya kilidini açmasına izin ver.|Microsoft 365 E3 E5|
|Azure AD Uygulama Ara Sunucusu|intranet sunucularında barındırılan web tabanlı uygulamalar için güvenli uzaktan erişim sağlar.|Ayrı ücretli Azure aboneliği gerektirir|
|Azure Noktadan Siteye VPN|Azure sanal ağı aracılığıyla uzak çalışanın cihazından intranet'inize güvenli bir bağlantı oluşturun.|Ayrı ücretli Azure aboneliği gerektirir|
|Windows 365|Yalnızca kişisel ve yönetimsiz cihazlarını 365 Bulut pc'lerle Windows uzaktan çalışanları desteklemektedir.|Ayrı ücretli Azure aboneliği gerektirir|
|Uzak Masaüstü |Çalışanların intranet'inize Windows tabanlı bilgisayarlara bağlanmasına izin ver.|Microsoft 365 E3 E5|
|Uzak Masaüstü Hizmetleri Ağ Geçidi|İletişimi şifreler ve RDS ana bilgisayarlarının doğrudan İnternet'e açık açıklarını önler.|Ayrı Windows Server lisansları gerektirir|
|Microsoft Intune|Cihazları ve uygulamaları yönetin.|Microsoft 365 E3 E5|
|Yapılandırma Yöneticisi|Cihazlarınıza yazılım yüklemelerini, güncelleştirmelerini ve ayarlarını yönetme|Ayrı Configuration Manager lisansları gerektirir|
|Endpoint Analytics|İstemcilerinizi güncelleştirme hazırlığı Windows.|Ayrı Configuration Manager lisansları gerektirir|
|AutoPilot Windows'i çalıştırın|Üretken kullanım için 11 veya 10 Windows cihazı ayarlayın ve önceden yapılandırın.|Microsoft 365 E3 E5|
|Microsoft Teams, Exchange Online, SharePoint Online ve OneDrive, Microsoft 365 Uygulamaları, Microsoft Power Platform ve Yammer|Oluşturma, iletişim kurma ve işbirliği yapma.|Microsoft 365 E3 E5|
||||

Güvenlik ve uyumluluk ölçütleri için bkz [. Uzak çalışanlar için güvenlik ve uyumluluğu dağıtma](empower-people-to-work-remotely-security-compliance.md).

<a name="poster"></a> Bu çözümün 2 sayfalık bir özeti için Karma çalışanları [güçlendir posterini bakın](https://download.microsoft.com/download/9/b/b/9bb5fa79-74e9-497b-87c5-4021e53d9fc2/hybrid-worker-infrastructure.pdf).

[![Karma çalışanların posterini güçlendirin.](../media/empower-people-to-work-remotely/empower-remote-workers-poster.png)](https://download.microsoft.com/download/9/b/b/9bb5fa79-74e9-497b-87c5-4021e53d9fc2/hybrid-worker-infrastructure.pdf)

## <a name="provide-hybrid-working-for-all-of-your-workers"></a>Tüm çalışanlarınız için karma çalışma sağlama

Bu cihazlarla tüm çalışanlarınızı üretken bir şekilde her yerde üretken hale etkinleştirebilirsiniz:

- Surface dizüstü bilgisayar ve Windows 11 veya 10 gibi, web üzerinden Microsoft 365 bulut uygulamalarına ve hizmetlere erişmeye yönelik özelliklere, güvenlik ve performansa sahip modern bir cihaz.

- Evden kullanılan eski dizüstü ve masaüstleri dahil olmak üzere herhangi bir cihaz Microsoft 365 365 Bulut Bilgisayarı aracılığıyla dolaylı olarak Windows bulut uygulamalarına ve [hizmetlere erişim sağlar](empower-people-to-work-remotely-remote-access.md#deploy-windows-365-to-provide-remote-access-for-remote-workers-using-personal-devices). Bu seçenek yüksek performans, güçlü güvenlik ve basitleştirilmiş bir IT yönetimi sağlar.

## <a name="next-steps"></a>Sonraki adımlar

Bu adımları kullanarak, kurumnizin sunucularına ve bulut hizmetlerine güvenli ve en iyi şekilde erişimi en iyi duruma getirmek ve karma çalışma çalışanlarının üretkenliğini en üst düzeye çıkarmak için bu adımları kullanın.

1. [MFA ile oturum açma güvenliğini artırma](empower-people-to-work-remotely-secure-sign-in.md)
2. [Şirket içi uygulama ve hizmetlere uzaktan erişim sağlama](empower-people-to-work-remotely-remote-access.md)
3. [Güvenlik ve uyumluluk hizmetlerini dağıtma](empower-people-to-work-remotely-security-compliance.md)
4. [Cihazlarınız, bilgisayarlarınız ve diğer uç noktalarınız için uç nokta yönetimini dağıtma](empower-people-to-work-remotely-manage-endpoints.md)
5. [Karma çalışan üretkenlik uygulamalarını ve hizmetlerini dağıtma](empower-people-to-work-remotely-teams-productivity-apps.md)
6. [Çalışanlarınızı eğitin ve kullanım geri bildirimlerini bildirin](empower-people-to-work-remotely-train-monitor-usage.md)

[![Karma çalışmayla karma çalışma için altyapınızı ayarlama adımları Microsoft 365.](../media/empower-people-to-work-remotely/remote-workers-step-grid.png)](empower-people-to-work-remotely-secure-sign-in.md)

Kurgusal ama temsili çok uluslu bir kuruluşun karma çalışma için altyapısını nasıl ayarladı hakkında bilgi için bkz. [Contoso'nun COVID-19 yanıtı ve altyapısı karma çalışma için](contoso-remote-onsite-work.md).
