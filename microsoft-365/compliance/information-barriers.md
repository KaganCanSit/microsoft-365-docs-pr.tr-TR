---
title: Bilgi engelleri hakkında daha fazla bilgi edinme
description: Microsoft Purview bilgi engelleri hakkında bilgi edinin.
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
ms.openlocfilehash: 214a2614b6ca7381bbded39ff5f5143236f6c001
ms.sourcegitcommit: 570c3be37b6ab1d59a4988f7de9c9fb5ca38028f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2022
ms.locfileid: "65363128"
---
# <a name="learn-about-information-barriers"></a>Bilgi engelleri hakkında daha fazla bilgi edinme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview Bilgi Engelleri (IB), Microsoft Teams, SharePoint Online ve OneDrive İş gruplarla kullanıcılar arasında iki yönlü iletişimi ve işbirliğini kısıtlamanıza olanak tanıyan bir uyumluluk çözümüdür. IB, genellikle yüksek oranda düzenlenmiş sektörlerde kullanılır ve çıkar çatışmalarını önlemeye ve kullanıcılarla kuruluş alanları arasındaki iç bilgileri korumaya yardımcı olabilir.

IB ilkeleri geçerli olduğunda, diğer belirli kullanıcılarla iletişim kurmaması veya dosya paylaşmaması gereken kullanıcılar bu kullanıcıları bulamaz, seçemez, sohbet etmez veya arayamazsınız. IB ilkeleri, tanımlı gruplar ve kullanıcılar arasındaki yetkisiz iletişimi ve işbirliğini algılamak ve önlemek için otomatik olarak denetimler gerçekleştirir. IB ilkeleri, eBulma yöneticilerinin arayabileceği kullanıcı içerik konumlarını denetleen eBulma araştırmalarına yönelik [uyumluluk sınırlarından](/microsoft-365/compliance/set-up-compliance-boundaries) bağımsızdır.

IB ilkeleri, aşağıdaki örnek senaryolar için gruplar ve kullanıcılar arasında iletişim ve işbirliğine izin verebilir veya bunları engelleyebilir:

- *Day Trader* grubundaki kullanıcılar *Pazarlama Ekibi* ile iletişim kurmamalı veya dosya paylaşmamalıdır
- Gizli şirket bilgileri üzerinde çalışan finans personeli, kuruluş içindeki belirli gruplarla iletişim kurmamalı veya dosya paylaşmamalıdır
- Ticari gizli malzeme içeren bir şirket içi ekip, kendi kuruluşundaki belirli gruplardaki kişileri aramamalı veya çevrimiçi olarak sohbet etmemelidir
- Araştırma ekibi yalnızca bir ürün geliştirme ekibiyle çevrimiçi aramalı veya sohbet etmelidir
- *Day Trader* grubu için bir SharePoint sitesi *, Day Trader* grubu dışındaki herkes tarafından paylaşılmamalı veya bu siteye erişilmemelidir

> [!IMPORTANT]
> Bilgi engelleri **yalnızca** iki yönlü iletişim ve işbirliği kısıtlamalarını destekler. Örneğin, Pazarlama'nın Day Traders ile iletişim kurabileceği ve işbirliği yaptığı ancak Day **Traders'ın** Pazarlama ile iletişim kuramadığı ve işbirliği yapamayacağı bir senaryo desteklenmez.

## <a name="information-barriers-and-microsoft-teams"></a>Bilgi engelleri ve Microsoft Teams

Microsoft Teams'de IB ilkeleri aşağıdaki yetkisiz iletişim ve işbirliği türlerini belirler ve önler:

- Kullanıcı arama
- Ekibİye üye ekleme
- Biriyle sohbet oturumu başlatma
- Grup sohbeti başlatma
- Bir kişiyi toplantıya katılmaya davet etme
- Ekran paylaşma
- Arama oluşturma
- Dosyayı başka bir kullanıcıyla paylaşma
- Bağlantı paylaşarak dosyaya erişme

Bu etkinlikleri Microsoft Teams yürüten kullanıcılar, etkinliği önlemek için bir IB ilkesine dahil edilirse devam edemeyeceklerdir. Ayrıca, bir IB ilkesine dahil edilen herkesin Microsoft Teams'daki diğer kullanıcılarla iletişim kurması engellenebilir. IB ilkelerinden etkilenen kişiler aynı ekip veya grup sohbetinin parçası olduğunda, bu sohbet oturumlarından kaldırılabilir ve grupla daha fazla iletişime izin verilmeyebilir.

Daha fazla bilgi için bkz. [Microsoft Teams bilgi engelleri](/MicrosoftTeams/information-barriers-in-teams).

## <a name="information-barriers-and-sharepoint-and-onedrive"></a>Bilgi engelleri, SharePoint ve OneDrive

SharePoint Online ve OneDrive,IB ilkeleri aşağıdaki tür yetkisiz işbirliğini algılar ve önler:

- Siteye üye ekleme
- Bir kullanıcı tarafından siteye veya içeriğe erişme
- Siteyi veya içeriği başka bir kullanıcıyla paylaşma
- Sitede arama

Daha fazla bilgi için bkz[. SharePoint'deki bilgi engelleri](/sharepoint/information-barriers) ve [OneDrive bilgi engelleri](/onedrive/information-barriers).

## <a name="information-barriers-and-exchange-online"></a>Bilgi engelleri ve Exchange Online

E-posta iletilerindeki gruplar ve kullanıcılar arasındaki iletişimi ve işbirliğini kısıtlamak için IB ilkeleri kullanılamaz. IB ilkeleri [Exchange Online Adres Defteri İlkelerini (ABP)](/exchange/address-books/address-book-policies/address-book-policies) temel alır. ABP'ler, kuruluşun genel adres defterinin (GAL) özelleştirilmiş görünümlerini sağlamak için kuruluşların kullanıcıları belirli gruplara sanal olarak atamasına olanak sağlar. IB ilkeleri oluşturulduğunda, ilkeler için ABP'ler otomatik olarak oluşturulur. Kuruluşunuza IB ilkeleri eklendikçe GAL'nizin yapısı ve davranışı IB ilkeleriyle uyumlu olacak şekilde değişir.

IB ilkelerini tanımlamadan ve uygulamadan önce, kuruluşunuzdaki tüm mevcut Exchange adres defteri ilkelerini kaldırmanız gerekir. IB ilkeleri adres defteri ilkelerini temel alır ve mevcut ABP ilkeleri IB tarafından oluşturulan ABP'lerle uyumlu değildir. Mevcut adres defteri ilkelerinizi kaldırmak için bkz. [Exchange Online'da adres defteri ilkesini kaldırma](/exchange/address-books/address-book-policies/remove-an-address-book-policy). IB ilkeleri etkinleştirildikten ve hiyerarşik adres defteri etkinleştirildiyse, IB segmentinde yer almamış tüm kullanıcılar çevrimiçi Exchange [hiyerarşik adres defterini](/exchange/address-books/hierarchical-address-books/hierarchical-address-books) görür.

Şu anda IB ilkeleri için yalnızca Exchange Online dağıtımları desteklenmektedir. Kuruluşunuzun e-posta iletişimlerini tanımlaması ve denetlemesi gerekiyorsa [Exchange posta akışı kurallarını](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) kullanmayı göz önünde bulundurun.

## <a name="ready-to-get-started"></a>Başlamaya hazır mısınız?

- [Bilgi engellerini kullanmaya başlama](information-barriers-policies.md)
- [Bilgi engeli ilkelerini yönetme](information-barriers-edit-segments-policies.md)
- [Bilgi engeli ilkeleri için kullanılabilecek özniteliklere bakın](information-barriers-attributes.md)
