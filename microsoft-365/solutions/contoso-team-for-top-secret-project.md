---
title: Contoso Corporation'ın çok gizli bir projesi için yalıtılmış ekip
f1.keywords:
- NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.date: 08/14/2020
audience: ITPro
ms.topic: overview
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: Ent_Architecture
description: 'Özet: Contoso,yeni bir ürün ve hizmet paketi geliştirmek için çok gizli bir proje için güvenlik yalıtımlı bir ekibi nasıl kullandı.'
ms.openlocfilehash: 5b6bc72a6476301cf3239aeb7f68486f15ebbac8
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027590"
---
# <a name="isolated-team-for-a-top-secret-project-of-the-contoso-corporation"></a>Contoso Corporation'ın çok gizli bir projesi için yalıtılmış ekip

Yönetici şirket dışından bir şirket dışından sonra, Contoso'nun CEO'su önümüzdeki beş yıl içinde Contoso'nun karını iki katına çıkaracak yeni bir ürün ve hizmet paketi geliştirmeyi sipariş etti. İşletmeyi, mühendislikyi ve pazar planını geliştirmek için en gizli proje **Project 2X** olarak adlandırılmıştır ve şirket genelindeki önemli personel işe alın olmuştur. 

Araştırma ve geliştirme için zaman çizelgeleri sıkıydı, bu da işbirliğinin verimli olması ve güvenli toplantılar, devam eden konuşmalar ve dosya depolaması için olanak sağlamak zorunda olduğu anlamına geliyor.

Project 2X için sonuç olarak teslim edilebilirler; word, Excel ve PowerPoint dosyaları şeklinde iş planları, ürün ve mühendislik belirtimleri, pazarlama malzemeleri ve zamanlamalardır. 

Hassas doğası gereği, bu dosyalara erişim şöyledir:

- 2X ekip Project üst düzey liderlik ekibiyle sınırlı.
- Şifrelenmiş ve izinlerle korunarak, dosyalar güvenli klasörlerinin dışında dağıtılsa bile yalnızca 2X ekip üyelerine ve üst düzey lidere Project izinler ile korunur.

Contoso IT personeli, [2X'te güvenlik Project](secure-teams-security-isolation.md) bu adımları olan bir ekip kullandı.

## <a name="step-1-created-a-private-team"></a>1. Adım: Özel ekip oluşturma

İlk olarak, ekibin temel SharePoint erişimini korumak için Contoso IT yöneticileri önerilen güvenlik ve erişim [SharePoint yapılandırdı](../security/office-365-security/sharepoint-file-access-policies.md).

Ardından, Contoso IT yöneticisi Project 2X adlı yeni bir özel ekip oluşturdu ve 2X personelinin kullanıcı hesaplarını üye Project olarak ekledi. Ayrıca, ekibi yalnızca 2X'Project özel kanallar oluşturacağı şekilde yapılandırdı.

Yapılandırma ayrıntıları için bkz. [Özel ekip oluşturma](secure-teams-security-isolation.md#create-a-private-team).

## <a name="step-2-created-a-sensitivity-label-for-the-project-2x-team"></a>2. Adım: 2X ekibi için Project etiketi oluşturuldu

Contoso yöneticileri, şu ifadeyi alan **2X'e Project duyarlılık etiketi oluşturdu**:

- Şifreleme etkinleştirildi.
- Co-Author 2X grup için izin Project izin Microsoft 365 verilir.
- Üst Düzey Liderlik grubu için İzin Verilen Görüntüleyici izinleri.
- Unmaned access to unmaned devices.

Sitenin **temel** 2X Project Belgeler SharePoint dosyalar:

- Yalnızca 2X grup üyelerine tam izinler sağlayan ve Üst Düzey Liderlik Project 2X Microsoft 365 izinlerini okuma izni sağlayan site izinleri.
- Site Project veya kopyalanan dosyayla birlikte gelen şifreleme ve izinlerle birlikte en iyi 2X duyarlılık etiketini içerir.

Yapılandırma ayrıntıları için bkz [. Duyarlılık etiketi oluşturma](secure-teams-security-isolation.md#create-a-sensitivity-label).

## <a name="step-3-configured-the-underlying-sharepoint-site"></a>3. Adım: Temel SharePoint yapılandırıldı

İlk olarak, ekibin temel SharePoint erişimini korumak için Contoso IT yöneticileri önerilen güvenlik ve erişim [SharePoint yapılandırdı](../security/office-365-security/sharepoint-file-access-policies.md).

Ardından, site için ek izin ayarlarını yapılandırdı:

- 2X Project erişimini engellemek için. Yapılandırma ayrıntıları için bkz. [SharePoint için güvenlik yalıtımlı bir ekibin ayarlarını değiştirme](secure-teams-security-isolation.md#sharepoint-settings).
- Üst Düzey Liderlik grubunun Okuma izinleri için.

Ardından, 2X grup üyelerinin siteye erişimini paylaşmalarını engellemek Project ek izin ayarlarını yapılandırdı. 

Grup 2X için özel Project kanalları oluşturulurken, grup sahibi konuk paylaşımını devre dışı bırakarak varsayılan paylaşım bağlantısını Belirli kişiler **değerine** ayarlar.

İşte, güvenlik yalıtlığı olan Project 2X ekibinin sonuç yapılandırması.

![Sonuçta 2X ekibinin Project yapılandırması.](../media/contoso-team-for-top-secret-project.png)

 ## <a name="step-4-trained-project-2x-team-members"></a>4. Adım: 2X ekip Project eğitilmiş

Contoso güvenlik personeli, Project bir kursta 2X ekip üyelerini eğitmiş:

- 2X'te yeni Project, toplantıları ve sohbetleri kullanma ve ekip dosyaları üzerinde işbirliği yapma.
- Ekipte yeni dosyalar oluşturma ve yerel olarak oluşturulan yeni dosyaları karşıya yükleme.
- Dosyaları 2X duyarlılık Project etikete sahip olarak etiketleme.
- Bu 2X Project, ekipten ayrıldığında bile bir dosyayı nasıl koruma şeklinde bir gösteri.

Sonuçta, 2X ekip üyelerinin sohbetler, Project ve dosyalar için güvenli bir ortamda işbirliği yaptıkları güvenli bir ortam elde edildi.

Burada, temel alınan Project 2X duyarlılık etiketinin atandığı Project bir dosya örneği yer almaktadır.

![Temel 2X sitesinde depolanan bir Project.](../media/contoso-team-for-top-secret-project-example.png)

Birkaç örnekte, 2X Project üyeleri Project 2X etiketiyle korunan dosyaları çevrimdışı çalışma için yerel bir sürücüye indirdiler. 

Ancak, açılan kimlik bilgileri istendikten sonra, hatalarının farkına vararak bunları siliyorlar.

Teams'Teams birlikte çalışma ortamı ve Microsoft 365'nin güvenlik özellikleri nedeniyle, Project 2X'in ayrıntıları projenin süresi boyunca gizli tutulmaktadır. Contoso planlarını duyurur ve yeni ürün ve hizmetleri müşterilerinin ve yatırımcılardan ve rakiplerinin bu akdini memnun etmek için sunmak için bir sürecindedir.

## <a name="next-step"></a>Sonraki adım

[Kuruluşta güvenlik yalıtlığı olan](secure-teams-security-isolation.md) bir ekibi dağıtın.

