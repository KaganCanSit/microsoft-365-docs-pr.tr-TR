---
title: Bu konuda bilgi engellerini Microsoft 365
description: Kuruluş içinde iletişim uyumluluğunu sağlamak için bilgi engellerini Microsoft Teams iletişim engellerini kullanın.
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.localizationpriority: ''
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: fc3d961b8707ba07febd95022580091618086d7f
ms.sourcegitcommit: 7e59802f251da96ec639fb09534aa96acf5d6ce7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2021
ms.locfileid: "63005437"
---
# <a name="learn-about-information-barriers-in-microsoft-365"></a>Bu konuda bilgi engellerini Microsoft 365

Microsoft bulut hizmetleri güçlü iletişim ve işbirliği özellikleri içerir. Ancak, ilgi çakışması önlemek için iki grup arasındaki iletişimi ve işbirliğini kısıtlamak istediğinizi varsayalım. Ya da iç bilgileri korumak için, kuruluş içindeki belirli kişiler arasındaki iletişimi ve işbirliğini kısıtlamak istiyor da olabilir. Microsoft 365 gruplar ve kuruluşlar arasında iletişimi ve işbirliğini sağlar, bu nedenle gerektiğinde belirli kullanıcı grupları arasında iletişimi ve işbirliğini kısıtlamanın bir yolu var mı? Bilgi engelleriyle, bunu!

Microsoft Teams, SharePoint Online'a OneDrive İş engellerini ortadan kaldırabilirsiniz. Aboneliğinizin bilgi [engellerini](#required-licenses-and-permissions), uyumluluk yöneticisini veya bilgi engellerini olduğunu varsayarak, ilgili kullanıcı grupları arasında iletişime izin verecek veya bu iletişimleri önleyen ilkeler Microsoft Teams. Bilgi engeli ilkeleri, şu gibi durumlarda kullanılabilir:

- Gün içinde trader grubunda yer alan kullanıcı pazarlama ekibiyle dosya iletişim kurması veya paylaşması gerekir
- Gizli şirket bilgileri üzerinde çalışan finans personeli, kuruluşların içindeki belirli gruplarla iletişim kurmalı veya dosya paylaşmaz
- Ticari gizli malzemelere sahip bir iç ekip, kuruluş içindeki belirli gruplarda yer alan kişilerin aramasını veya çevrimiçi sohbete sahip olması gerekir.
- Araştırma ekibi, ürün geliştirme ekibini yalnızca çevrimiçi aramalı veya çevrimiçi olarak sohbete sahip olmalı
- Gün trader grubu sitesi, gün trader grubu dışından hiç kimse tarafından paylaşılmaz veya erişilemez

> [!IMPORTANT]
> Bilgi engelleri ***yalnızca** _ iki yol kısıtlamalarını destekler. Pazarlama gibi bir yol, gün trader'larıyla iletişim kurabilir ve işbirliği kurabilir, ancak gün trader'ları pazarlama _*ile iletişim kuramaz ve işbirliği _kuramaz_** desteği yoktur.

Bu örnek senaryoların (ve daha fazlası) tüm bu örnek senaryolar için Microsoft Teams, SharePoint Online ve OneDrive'te iletişimleri ve işbirliğini engellemek veya bunlara izin vermek için bilgi engeli OneDrive. Bu tür ilkeler kişilerin, arama yapmaları gerekenleri aramalarını veya sohbet etmelerini ya da yalnızca Microsoft Teams.'de belirli gruplarla iletişim kurmalarını sağlar. Bilgi engeli ilkelerinin etkili olduğu bu ilkelerin kapsamında olan kullanıcılar Microsoft Teams'te başkalarıyla iletişim kurmaya ve işbirliği yapmaya çalışsa, SharePoint Online veya OneDrive denetimleri, iletişim ve işbirliğini (bilgi engeli ilkeleri tarafından tanımlandığı şekilde) engellemek (veya buna izin vermek) için  yapılır.

Bilgi engelleriyle kullanıcı deneyimi hakkında daha fazla bilgi edinmek için bkz:

- [Web'de bilgi Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [SharePoint Online'da bilgi engelleri](/sharepoint/information-barriers)
- [Web'de bilgi OneDrive](/onedrive/information-barriers)

> [!IMPORTANT]
> Şu anda, bilgi engelleri e-posta iletişimleri için geçerli değildir. Ayrıca, bilgi engelleri uyumluluk sınırlarından [bağımsızdır](set-up-compliance-boundaries.md).<p> Bilgi engeli ilkelerini tanımlamadan ve uygulamadan önce, kurumda adres defteri [ilkelerinin Exchange emin](/exchange/address-books/address-book-policies/address-book-policies) olun. (Bilgi engelleri adres defteri ilkelerine dayalıdır.)

## <a name="what-happens-with-information-barriers"></a>Bilgi engelleriyle neler olur?

Bilgi engeli ilkeleri kullanılırken, belirli kullanıcılarla iletişim kurması veya dosya paylaşması gereken kişiler bu kullanıcıları bulamaz, seçerek, sohbet edip arayamz. Bilgi engelleriyle, yetkisiz iletişimi ve işbirliğini önlemek için denetimler tamamlanmamıştır.

Bilgi engelleri Microsoft Teams Online ve Microsoft Teams için SharePoint engeller OneDrive. Bilgi Microsoft Teams, bilgi engeli ilkeleri aşağıdaki yetkisiz iletişim tiplerini belirler ve engeller:

- Kullanıcı arama
- Ek ekiplere üye ekleme
- Biriyle sohbet oturumu başlatma
- Grup sohbeti başlatma
- Birini toplantıya katılmaya davet etme
- Ekran paylaşma
- Arama yerleştirilmesi
- Dosyayı başka bir kullanıcıyla paylaşma
- Paylaşım bağlantısı aracılığıyla dosyaya erişim

Söz konusu kişiler etkinliği engellemeye yönelik bir bilgi engeli ilkesine dahil edilirse devam edemiyorlar. Ayrıca, potansiyel olarak, bir bilgi engeli ilkesine dahil olan herkes diğerleriyle iletişim kurması engellenmiş Microsoft Teams. Bilgi engeli ilkelerinden etkilenen kişiler aynı ekip veya grup sohbetine parçası olduğunda, bu sohbet oturumlarından kaldırılabilir ve grupla daha fazla iletişime izin verilmiyor olabilir.

Bilgi engelleriyle ilgili kullanıcı deneyimi hakkında daha fazla bilgi edinmek [için bkz.](/MicrosoftTeams/information-barriers-in-teams) Microsoft Teams.

SharePoint Online ve OneDrive'de, bilgi engeli ilkeleri aşağıdaki yetkisiz işbirliğini belirler ve engeller:

- Siteye üye ekleme
- Kullanıcı tarafından siteye veya içeriğe erişme
- Site veya içeriği başka bir kullanıcıyla paylaşma
- Bir sitede arama

Bilgi engelleriyle kullanıcı deneyimi hakkında daha fazla bilgi edinmek için bkz. [SharePoint Online](/sharepoint/information-barriers)

## <a name="required-licenses-and-permissions"></a>Gerekli lisanslar ve izinler

Insider risk yönetimine başlamadan önce, yeni aboneliğinizi [Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) eklentileri doğrulamanız gerekir. Bilgi engellerine erişmek ve bunu kullanmak için, organizasyon aşağıdaki aboneliklerden veya eklentilerden biri olabilir:

- Microsoft 365 E5/A5 aboneliği (ücretli veya deneme sürümü)
- Office 365 E5/A5/A3/A1 aboneliği (ücretli veya deneme sürümü)
- Office 365 Gelişmiş Uyumluluk eklenti (artık yeni abonelikler için kullanılamaz)
- Microsoft 365 E3/A3/A1 aboneliği + Microsoft 365 E5/A5 Uyumluluk eklentisi
- Microsoft 365 E3/A3/A1 aboneliği + Microsoft 365 E5/A5 Insider Risk Yönetimi eklentisi

Daha fazla bilgi için güvenlik [Microsoft 365 uyumluluğu için lisanslama & bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

Bilgi [engeli ilkelerini tanımlamak veya](information-barriers-policies.md) düzenlemek için, aşağıdaki rollerden biri size atanmış olmalıdır:

- Microsoft 365 yönetici
- Office 365 yönetici
- Uyumluluk yöneticisi
- IB Uyumluluk Yönetimi

(Roller ve izinler hakkında daha fazla bilgi edinmek için, Office 365 [ve Uyumluluk &'nde İzinler'e bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).)

Bilgi engeli ilkelerini tanımlamak, doğrulamak veya düzenlemek için PowerShell cmdlet'lerini biliyor olun. Nasıl kullanıldığı makalesinde PowerShell cmdlet'lerinin birkaç örneği sağlamızsa [da,](information-barriers-policies.md) kuruma ilişkin parametreler gibi diğer ayrıntıları da bilmek gerekir.

## <a name="next-steps"></a>Sonraki adımlar

- [Bu konuda bilgi engelleri hakkında daha fazla Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [SharePoint Online'daki bilgi engelleri hakkında daha fazla bilgi](/sharepoint/information-barriers)
- [Bu konuda bilgi engelleri hakkında daha fazla OneDrive](/onedrive/information-barriers)
- [Bilgi engeli ilkeleri için kullanılmaktadır.](information-barriers-attributes.md)
- [Bilgi engellerine yönelik ilkeleri tanımlama](information-barriers-policies.md)
- [Bilgi engeli ilkelerini düzenleme (veya kaldırma)](information-barriers-edit-segments-policies.md)
