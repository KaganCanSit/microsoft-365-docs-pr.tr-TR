---
title: multi-geo Microsoft 365 için planlama
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
description: Multi-Geo Microsoft 365, çok coğrafi konumun nasıl çalıştığı ve veri depolama için hangi coğrafi konumların kullanılabilir olduğu hakkında bilgi edinin.
ms.openlocfilehash: bda48f14b14840eed03d456ef66e7d86df890619
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64822804"
---
# <a name="plan-for-microsoft-365-multi-geo"></a>multi-geo Microsoft 365 için planlama

Bu kılavuz, Microsoft 365 kiracılarını, veri yerleşimi gereksinimlerini karşılamak üzere şirketin varlığına uygun olarak ek coğrafyalara genişletilecek şekilde hazırlayan çok uluslu şirketlerin (MNC) yöneticileri için tasarlanmıştır.

Çok coğrafi bir yapılandırmada, Microsoft 365 kiracınız merkezi bir konumdan ve bir veya daha fazla uydu konumundan oluşur. Bu, birden çok coğrafi konuma yayılan tek bir kiracıdır. Coğrafi konumlar da dahil olmak üzere kiracı bilgileriniz Azure Active Directory (Azure AD) içinde ana kaynak olarak bulunur.

Yapılandırmanın temel kavramlarını anlamanıza yardımcı olacak çok coğrafi terimlerden bazıları şunlardır:

- **Kiracı**: Bir kuruluşun Microsoft 365'da temsilidir ve genellikle kendisiyle ilişkilendirilmiş bir veya daha fazla etki alanı vardır (örneğin, https://contoso.sharepoint.com).

- **Coğrafi konumlar** : Verileri Microsoft 365 kiracıda barındırmak için kullanılabilen coğrafi konumlar.

- **Uydu konumları** – verileri Microsoft 365 kiracınızda barındıracak şekilde yapılandırdığınız ek coğrafi konumlar. Çok coğrafi kiracılar, Kuzey Amerika ve Avrupa gibi birden fazla coğrafi konuma yayılmıştır.

- **Tercih Edilen Veri Konumu (PDL)** – Tek bir kullanıcının Exchange ve OneDrive verilerinin depolandığı coğrafi konum. Bu, yönetici tarafından kiracı için yapılandırılmış coğrafi konumlardan herhangi birine ayarlanabilir. Zaten bir OneDrive sitesi olan bir kullanıcının PDL'sini değiştirirseniz, OneDrive verilerinin otomatik olarak yeni coğrafi konuma taşınmadığını unutmayın. Daha fazla bilgi için bkz. [OneDrive kitaplığını farklı bir coğrafi konuma taşıma](move-onedrive-between-geo-locations.md). Exchange posta kutuları varsa, posta kutusu otomatik olarak yeni tercih edilen veri konumuna taşınır.

Multi-Geo'ya olanak sağlamak için dört temel adım gerekir:

1. Microsoft 365 hizmet planında _Multi-Geo Özelliklerini_ eklemek için hesap ekibinizle birlikte çalışın.

2. İstediğiniz uydu konumlarını seçin ve bunları kiracınıza ekleyin.

3. Kullanıcılarınızın tercih edilen veri konumunu istenen uydu konumuna ayarlayın. Bir kullanıcı için yeni bir OneDrive sitesi veya Exchange posta kutusu sağlandığında, bu site PDL'sine sağlanır.

4. Kullanıcılarınızın mevcut OneDrive sitelerini merkezi konumdan tercih ettikleri veri konumuna gerektiği gibi geçirin. (Exchange posta kutuları, kullanıcının PDL'sini ayarladığınızda otomatik olarak geçirilir.)

Bu adımların her biri hakkında ayrıntılı bilgi için bkz[. Multi-Geo Microsoft 365 yapılandırma](multi-geo-tenant-configuration.md).

> [!IMPORTANT]
> multi-geo Microsoft 365 performans iyileştirme için tasarlanmamıştır, veri yerleşimi gereksinimlerini karşılamak için tasarlanmıştır. Microsoft 365 için performans iyileştirmesi hakkında bilgi için bkz. [Microsoft 365 için ağ planlaması ve performans ayarlaması](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) veya destek grubunuzla iletişime geçin.

Aşağıdaki konumlardan herhangi birini, OneDrive ve SharePoint siteleri barındırabileceğiniz ve posta kutularını Exchange uydu konumları olacak şekilde yapılandırabilirsiniz. Çok coğrafi alanı planladığınızda, Microsoft 365 kiracınıza eklemek istediğiniz konumların listesini yapın. Bir veya iki uydu konumuyla başlamanızı ve gerekirse kademeli olarak daha fazla coğrafi konuma genişletmenizi öneririz.

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

Multi-geo'yı yapılandırırken, Microsoft 365 geçiş yaparken şirket içi altyapınızı birleştirme fırsatını değerlendirin. Örneğin, Singapur ve Malezya'da şirket içi çiftlikleriniz varsa, veri yerleşimi gereksinimlerinin bunu yapmanıza olanak sağlaması koşuluyla bunları APC uydu konumunda birleştirebilirsiniz.

## <a name="best-practices"></a>En iyi uygulamalar

bazı ilk testleri yapmak için Microsoft 365'de bir test kullanıcısı oluşturmanızı öneririz. Üretim kullanıcılarını Microsoft 365 Multi-Geo'ya eklemeye devam etmeden önce bu kullanıcıyla bazı test ve doğrulama adımlarını inceleyeceğiz.

Test kullanıcısıyla testi tamamladıktan sonra, yeni bir coğrafi konumda OneDrive ve Exchange ilk kullanan olmak için bt departmanınızdan bir pilot grup seçin. Bu ilk grup için, henüz OneDrive olmayan kullanıcıları seçin. Bu ilk grupta beşten fazla kişi olmamasını ve toplu dağıtım yaklaşımını izleyerek aşamalı olarak genişletmenizi öneririz.

Microsoft 365 OneDrive hangi coğrafi konumda sağlandığını belirleyebilmesi için her kullanıcının *tercih edilen bir veri* konumu (PDL) ayarlanmış olmalıdır. Kullanıcının tercih ettiği veri konumu seçtiğiniz uydu konumlarından biriyle veya merkezi konumunuzla eşleşmelidir. PDL alanı zorunlu olmasa da, tüm kullanıcılar için bir PDL'nin ayarlanmasını öneririz. PDL olmayan bir kullanıcının iş yükleri merkezi konumda sağlanır.

Kullanıcılarınızın listesini oluşturun ve kullanıcı asıl adlarını (UPN) ve tercih edilen uygun veri konumu için konum kodunu ekleyin. Başlamak için test kullanıcınızı ve ilk pilot grubunuzu ekleyin. Yapılandırma yordamları için bu listeye ihtiyacınız olacaktır.

Kullanıcılarınız bir şirket içi Active Directory sisteminden Azure Active Directory eşitlenmişse, tercih edilen veri konumunu Active Directory özniteliği olarak ayarlamanız ve Azure Active Directory Bağlan kullanarak eşitlemeniz gerekir. Azure AD PowerShell kullanarak eşitlenmiş kullanıcılar için tercih edilen veri konumunu doğrudan yapılandıramazsınız. Active Directory'de PDL'yi ayarlama ve Eşitleme adımları [Azure Active Directory Bağlan eşitleme: Microsoft 365 kaynaklar için tercih edilen veri konumunu yapılandırma bölümünde ele alınmıştır](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

Çok coğrafi kiracının yönetimi, çok coğrafi olmayan bir kiracıdan farklı olabilir, SharePoint ve OneDrive ayarlarının ve hizmetlerinin çoğu çok coğrafi kullanıma duyarlıdır. Yapılandırmanıza devam etmeden önce [Çok coğrafi ortamı yönetme'yi](administering-a-multi-geo-environment.md) gözden geçirmenizi öneririz.

Son kullanıcılarınızın [çok coğrafi ortamdaki](multi-geo-user-experience.md) deneyimi hakkında ayrıntılı bilgi için Çok coğrafi ortamda kullanıcı deneyimi makalesini okuyun.

Microsoft 365 Multi-Geo'Microsoft 365 yapılandırmaya başlamak için bkz. [Multi-Geo'Microsoft 365 yapılandırma](multi-geo-tenant-configuration.md).

Yapılandırmayı tamamladıktan sonra, kullanıcılarınızın tercih ettikleri veri konumlarından çalışmasını sağlamak için [kullanıcılarınızın OneDrive kitaplıklarını gerektiği gibi geçirmeyi](move-onedrive-between-geo-locations.md) unutmayın.

## <a name="related-topics"></a>İlgili konular

[Multi-Geo eBulma yapılandırması Microsoft 365](./multi-geo-ediscovery-configuration.md)
