---
title: Bilgi engelleri hakkında daha fazla bilgi edinme
description: Microsoft Purview'daki bilgi engelleri hakkında bilgi edinin.
keywords: Microsoft 365, Microsoft Purview, uyumluluk, bilgi engelleri
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
ms.openlocfilehash: 72a53580222b315f86fd397e391b026937b8035b
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65287188"
---
# <a name="learn-about-information-barriers"></a>Bilgi engelleri hakkında daha fazla bilgi edinme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft bulut hizmetleri güçlü iletişim ve işbirliği özellikleri içerir. Ancak, kuruluşunuzda çıkar çatışmasının oluşmasını önlemek için iki grup arasındaki iletişimi ve işbirliğini kısıtlamak istediğinizi varsayalım. Ya da iç bilgileri korumak için kuruluşunuzdaki belirli kişiler arasındaki iletişimi ve işbirliğini kısıtlamak isteyebilirsiniz. Microsoft 365 gruplar ve kuruluşlar arasında iletişim ve işbirliği sağlar, bu nedenle gerektiğinde belirli kullanıcı grupları arasındaki iletişimi ve işbirliğini kısıtlamanın bir yolu var mı? Microsoft Purview Bilgi Engelleri (IB) ile şunları yapabilirsiniz!

Microsoft Teams, çevrimiçi SharePoint ve OneDrive İş bilgi engellerini destekler. [Aboneliğinizin](#required-licenses-and-permissions) bilgi engelleri içerdiğini varsayarsak, uyumluluk yöneticisi veya bilgi engelleri yöneticisi, Microsoft Teams'da kullanıcı grupları arasında iletişime izin veren veya bunları engelleyen ilkeler tanımlayabilir. Bilgi engeli ilkeleri aşağıdaki gibi durumlarda kullanılabilir:

- Günlük tüccar grubundaki kullanıcı pazarlama ekibiyle iletişim kurmamalı veya dosya paylaşmamalıdır
- Gizli şirket bilgileri üzerinde çalışan finans personeli, kuruluş içindeki belirli gruplarla iletişim kurmamalı veya dosya paylaşmamalıdır
- Ticari gizli malzeme içeren bir şirket içi ekip, kendi kuruluşundaki belirli gruplardaki kişileri aramamalı veya çevrimiçi sohbet etmemelidir
- Araştırma ekibi yalnızca bir ürün geliştirme ekibiyle çevrimiçi aramalı veya sohbet etmelidir
- Günlük tüccar grubu için bir site, gün tüccar grubu dışındaki herkes tarafından paylaşılmamalı veya erişilmemelidir

> [!IMPORTANT]
> Bilgi engelleri ***yalnızca destekler** _ iki yönlü kısıtlamalar. Pazarlama gibi tek yönlü kısıtlamalar günlük tüccarlarla iletişim kurabilir ve işbirliği yapabilir, ancak günlük tüccarlar pazarlama ile iletişim kuramaz ve işbirliği yapamazlar _*_desteklenmez_**.

Bu örnek senaryoların tümü (ve daha fazlası) için, Microsoft Teams, SharePoint Online ve OneDrive iletişim ve işbirliğine izin vermek için bilgi engeli ilkeleri tanımlanabilir. Bu tür ilkeler, kişilerin aramalarını veya konuşmamaları gereken kişilerle sohbet etmelerini engelleyebilir veya kişilerin yalnızca Microsoft Teams'deki belirli gruplarla iletişim kurmasını sağlayabilir. Bilgi engeli ilkeleri etkin olduğunda, bu ilkelerin kapsamına giren kullanıcılar Microsoft Teams, SharePoint Çevrimiçi veya OneDrive denetimlerinde başkalarıyla iletişim kurmaya ve işbirliği yapmaya çalıştığında iletişim ve işbirliğini (bilgi engeli ilkeleriyle tanımlandığı şekilde) önlemek (veya izin vermek) için yapılır.

Bilgi engelleriyle ilgili kullanıcı deneyimi hakkında daha fazla bilgi edinmek için bkz:

- [Microsoft Teams'da bilgi engelleri](/MicrosoftTeams/information-barriers-in-teams)
- [SharePoint Online'da bilgi engelleri](/sharepoint/information-barriers)
- [OneDrive'da bilgi engelleri](/onedrive/information-barriers)

> [!IMPORTANT]
> Şu anda, bilgi engelleri e-posta iletişimleri için geçerli değildir. Ayrıca, bilgi engelleri [uyumluluk sınırlarından](set-up-compliance-boundaries.md) bağımsızdır.<p> Bilgi engeli ilkelerini tanımlamadan ve uygulamadan önce, kuruluşunuzun [Exchange adres defteri ilkelerinin](/exchange/address-books/address-book-policies/address-book-policies) etkin olmadığından emin olun. (Bilgi engelleri adres defteri ilkelerini temel alır.)

## <a name="what-happens-with-information-barriers"></a>Bilgi engelleri ile ne olur?

Bilgi engeli ilkeleri söz konusu olduğunda, diğer belirli kullanıcılarla iletişim kurmaması veya dosya paylaşmaması gereken kişiler bu kullanıcıları bulamaz, seçemez, sohbet etmez veya arayamazsınız. Bilgi engelleriyle, yetkisiz iletişimi ve işbirliğini önlemek için denetimler yapılır.

Bilgi engelleri Microsoft Teams (sohbetler ve kanallar), SharePoint Online ve OneDrive için geçerlidir. Microsoft Teams'de, bilgi engeli ilkeleri aşağıdaki yetkisiz iletişim türlerini belirler ve önler:

- Kullanıcı arama
- Ekibİye üye ekleme
- Biriyle sohbet oturumu başlatma
- Grup sohbeti başlatma
- Bir kişiyi toplantıya katılmaya davet etme
- Ekran paylaşma
- Arama oluşturma
- Dosyayı başka bir kullanıcıyla paylaşma
- Paylaşım bağlantısı aracılığıyla dosyaya erişim

İlgili kişiler etkinliği önlemek için bir bilgi engeli ilkesine dahil edilirse devam edemeyecektir. Ayrıca, bir bilgi engeli ilkesine dahil edilen herkesin Microsoft Teams'daki diğer kişilerle iletişim kurması engellenebilir. Bilgi engeli ilkelerinden etkilenen kişiler aynı ekip veya grup sohbetinin parçası olduğunda, bu sohbet oturumlarından kaldırılabilir ve grupla daha fazla iletişime izin verilmeyebilir.

Bilgi engelleri ile kullanıcı deneyimi hakkında daha fazla bilgi edinmek için bkz. [Microsoft Teams bilgi engelleri](/MicrosoftTeams/information-barriers-in-teams).

SharePoint Online ve OneDrive'da, bilgi engeli ilkeleri aşağıdaki yetkisiz işbirliği türlerini belirler ve önler:

- Siteye üye ekleme
- Bir kullanıcı tarafından siteye veya içeriğe erişme
- Siteyi veya içeriği başka bir kullanıcıyla paylaşma
- Sitede arama

Bilgi engelleriyle kullanıcı deneyimi hakkında daha fazla bilgi edinmek için bkz. [SharePoint Online'da bilgi engelleri](/sharepoint/information-barriers)

## <a name="required-licenses-and-permissions"></a>Gerekli lisanslar ve izinler

IB'yi kullanmaya başlamadan önce [Microsoft 365 aboneliğinizi](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) ve tüm eklentileri onaylamanız gerekir. IB'ye erişmek ve bunları kullanmak için kuruluşunuzun aşağıdaki aboneliklerden veya eklentilerden birine sahip olması gerekir:

- Microsoft 365 E5/A5 aboneliği (ücretli veya deneme sürümü)
- Office 365 E5/A5/A3/A1 aboneliği (ücretli veya deneme sürümü)
- Office 365 Gelişmiş Uyumluluk eklentisi (artık yeni aboneliklerde kullanılamaz)
- Microsoft 365 E3/A3/A1 aboneliği + Microsoft 365 E5/A5 Uyumluluk eklentisi
- Microsoft 365 E3/A3/A1 aboneliği + Microsoft 365 E5/A5 Insider Risk Management eklentisi

Daha fazla bilgi için bkz[. güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

[Bilgi engeli ilkelerini tanımlamak veya düzenlemek](information-barriers-policies.md) için aşağıdaki rollerden birine atanmış olmanız gerekir:

- Genel yönetici Microsoft 365
- Genel yönetici Office 365
- Uyumluluk yöneticisi
- IB Uyumluluk Yönetimi

(Roller ve izinler hakkında daha fazla bilgi edinmek için bkz. [Office 365 Güvenlik & Uyumluluk Merkezi'ndeki İzinler](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).)

Bilgi engeli ilkelerini tanımlamak, doğrulamak veya düzenlemek için PowerShell cmdlet'lerini biliyor olmanız gerekir. [Nasıl yapılır makalesinde](information-barriers-policies.md) PowerShell cmdlet'lerinin birkaç örneğini sağlasak da, kuruluşunuz için parametreler gibi diğer ayrıntıları bilmeniz gerekir.

## <a name="next-steps"></a>Sonraki adımlar

- [Microsoft Teams bilgi engelleri hakkında daha fazla bilgi edinin](/MicrosoftTeams/information-barriers-in-teams)
- [SharePoint Online'da bilgi engelleri hakkında daha fazla bilgi edinin](/sharepoint/information-barriers)
- [OneDrive bilgi engelleri hakkında daha fazla bilgi edinin](/onedrive/information-barriers)
- [Bilgi engeli ilkeleri için kullanılabilecek özniteliklere bakın](information-barriers-attributes.md)
- [Bilgi engelleri için ilke tanımlama](information-barriers-policies.md)
- [Bilgi engeli ilkelerini düzenleme (veya kaldırma)](information-barriers-edit-segments-policies.md)
