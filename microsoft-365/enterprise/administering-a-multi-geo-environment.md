---
title: Çok coğrafi ortamı yönetme
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: Yöneticiler, çok coğrafi bir ortamda SharePoint ve OneDrive yönetmeyi öğrenebilir.
ms.openlocfilehash: 31d361b2936c3d7bceca7137499c659030717eba
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010816"
---
# <a name="administering-a-multi-geo-environment"></a>Çok coğrafi ortamı yönetme

Burada, hizmetlerin çok coğrafi Microsoft 365 nasıl çalışmaktadır?

## <a name="administrator-experience"></a>Yönetici deneyimi

Bu [SharePoint yönetim](https://admin.microsoft.com/sharepoint) merkezinde, sol gezinti bölmesinde coğrafi  konumlar sekmesinin yer alan ve coğrafi konumlarınızı görüntüleyebilirsiniz ve yönetebilirsiniz. Kiracınız için coğrafi konum eklemek veya silmek üzere bu sayfayı kullanın.

## <a name="audit-log-search"></a>Denetim günlüğü araması

Tüm uydu [konumlar](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) için birleşik bir Denetim günlüğü, denetim günlüğü Microsoft 365 sayfasından kullanılabilir. Coğrafi konumlar genelinde tüm denetim günlüğü girdilerini bulabilirsiniz, örneğin NAM & EUR kullanıcılarının etkinlikleri tek bir kuruluş görünümünde gösterilir ve sonra belirli kullanıcıların etkinliklerini görmek için mevcut filtreleri uygulayabilirsiniz.

> [!NOTE]
> Exchange denetim olayları yalnızca varsayılan konum için kullanılabilir.

## <a name="bcs-secure-store-apps"></a>BCS, Güvenli Depolama, Uygulamalar

BCS, Güvenli Depolama ve Uygulamaların her uydu konumu için ayrı örnekleri vardır; dolayısıyla SharePoint Online yöneticisi bu hizmetleri her uydu konumdan ayrı olarak yönetmeli ve yapılandırmalıdır.

## <a name="compliance-admin-center"></a>Uyumluluk yönetim merkezi

Çok coğrafi kiracı için tek bir merkezi uyumluluk merkezi bulunmaktadır: [Uyumluluk Microsoft 365 merkezi.](https://compliance.microsoft.com/)

## <a name="ediscovery"></a>eKbulma

Varsayılan olarak, çok coğrafi bir kiracının eBulma Yöneticisi veya Yöneticisi, eBulma'ı yalnızca bu kiracının merkezi konumda yürütebilirsiniz. Office 365 genel yöneticisinin, diğer kullanıcıların eBulma gerçekleştirmesine izin vermek ve eBulma'nın uydu konumu olarak gerçekleştirecek bölgeyi belirtmek üzere geçerli Uyumluluk Güvenlik Filtrelerinde bir "Bölge" parametresi ataması gerekir, aksi takdirde uydu konumu için eKbulma yapılmaz. Bir Bölgenin Uyumluluk Güvenlik Filtresini yapılandırmak için bkz. [Multi-Geo eKbulma Office 365'ı yapılandırma](multi-geo-ediscovery-configuration.md).

## <a name="exchange-mailboxes"></a>Exchange kutularını geri alın

Kullanıcıların Exchange posta kutuları PDL'leri değiştirilirse otomatik olarak taşınır. Yeni posta kutusu oluşturulduğunda, kullanıcının PDL'sinde değer ayarlanmamışsa kullanıcının PDL'sinde veya merkezi konumda hazır olur.

## <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>Bilgi Koruma (IP) Veri Kaybı Önleme (DLP) ilkesi

Güvenlik ve Uyumluluk Merkezi'nde OneDrive İş, SharePoint ve Exchange için IP DLP ilkelerinizi ayarladığı gibi, ilkelerin tamamını kiracıya veya geçerli kullanıcılara da filtreleyebilirsiniz. Örneğin: Uydu konumdaki bir kullanıcı için bir ilke seçmek isterseniz, ilkeyi belirli bir uydu OneDrive uygulamak için seçin ve kullanıcının URL'sini OneDrive girin. DLP [ilkeleri oluşturma konusunda yol gösterici genel bilgiler](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) için bkz. Veri kaybı önleme ilkelerine genel bakış.

DLP ilkeleri, her coğrafi konuma uygulanlıklarına göre otomatik olarak eşitlenir.

Coğrafi konumdaki tüm kullanıcılara Bilgi Koruma ve Veri Kaybı önleme ilkeleri uygulamak kullanıcı arabiriminde kullanılabilen bir seçenek değildir; bunun yerine, ilke için geçerli hesapları seçmeniz veya ilkeyi tüm hesaplara genel olarak uygulamanız gerekir.

## <a name="microsoft-power-apps"></a>Microsoft Power Apps

Power Apps uydu konumu için oluşturulduğunda, kiracının merkezi konumda yer alan uç noktasını kullanır. Microsoft Power Apps, Multi-Geo hizmeti değildir. 

## <a name="power-automate"></a>Power Automate

Uydu konumu için oluşturulan akışlar, kiracının varsayılan coğrafi konumda yer alan uç noktasını kullanır.  Power Automate, Multi-Geo hizmeti değildir. 

## <a name="sharepoint-storage-quota"></a>SharePoint kotasını atama

Varsayılan olarak, çok coğrafi ortamın tüm coğrafi konumları kullanılabilir kiracı depolama kotasını paylaşır.  Ayrıca, belirli bir coğrafi konum için belirli bir kotayı ayarak depolama kotasını yönetebilirsiniz. Daha fazla bilgi için bkz [SharePoint coğrafi ortamlarda depolama kotalarını atama](sharepoint-multi-geo-storage-quota.md).

## <a name="sharing"></a>Paylaşım

Yöneticiler konumlarının her biri için paylaşım ilkeleri ayarp yönetebilir. Her OneDrive coğrafi SharePoint ilgili sitelerle ilgili paylaşım ayarlarına uygun olur. (Örneğin, merkezi konumunuz için [dış](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) paylaşıma izin veebilirsiniz, ancak uydu konumunuz için (veya tersine) izin ve vermez.) Paylaşım ayarlarının coğrafi konumlar arasında paylaşım sınırlamalarını yapılandırmaya izin verme olmadığını unutmayın.

## <a name="stream"></a>Stream

Bire bir sohbette Stream'e yüklenen videolar, OneDrive ilgili sohbette depolanır. Toplantı kayıtları, toplantıyı OneDrive her katılımcının her bir kaydında depolanır.

## <a name="taxonomy"></a>Taksonomi

Coğrafi konumlarda [kurumsal olarak yönetilen](/sharepoint/managed-metadata) meta veriler için birleşik bir taksonomiyi destekleriz ve bu taksonomi şirketin merkezi konumda barındırıldı. Genel taksonominizi merkezi konumdan yönetmenizi ve uydu konumunun Taksonomisi'ne yalnızca konuma özgü terimleri eklemenizi öneririz. Küresel taksonomi koşulları uydu konumlarını eşitler.

Ek [ayrıntılar ve geliştirici kılavuzu için bkz.](/sharepoint/dev/solution-guidance/multigeo-managedmetadata) Çok coğrafi bir kiracıda meta verileri yönetme.

## <a name="user-profile-application"></a>Kullanıcı Profili Uygulaması

Her coğrafi [konumda bir kullanıcı](/sharepoint/manage-user-profiles) profili uygulaması vardır. Her kullanıcının profil bilgileri kendi coğrafi konumlarında barındırıldı ve ilgili coğrafi konum için yönetici tarafından kullanılabilir.

Özel profil özellikleriniz varsa, coğrafyalarda aynı profil şemasını kullanmanızı ve özel profil özelliklerinizi tüm coğrafi konumlarda veya gereken yerlerde göstermenizi öneririz. Kullanıcı profili verilerini programatik olarak nasıl doldurmakla ilgili kılavuz için lütfen Toplu Kullanıcı Profili Güncelleştirme [API'sini kullanın](/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).

Ek [ayrıntılar ve geliştirici kılavuzu için bkz. Çok coğrafi](/sharepoint/dev/solution-guidance/multigeo-userprofileexperience) bir kiracıda kullanıcı profilleriyle çalışma.

## <a name="yammer"></a>Yammer

Yammer, Multi-Geo iş yükü değildir. Yammer depolanan Yammer iş parçacığı kiracının merkezi yerine yerleştirilir. Yammer, dosya depolama alanı değişikliği sunar ve bu değişiklik dosyaları Yammer depolama alanı SharePoint. Yammer depolanan tüm SharePoint, SharePoint siteyle ilişkilendirilmiş olan Yammer yerleştirilir. SharePoint siteleri, Siteler ve Gruplar'da özetlenen PDL [SharePoint temel almaktadır](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md#sharepoint-sites-and-groups).
