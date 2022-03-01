---
title: Adım 1. Kurumsal Microsoft 365 için veritabanınız
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Birden çok coğrafi konum ve Microsoft 365 seçenekleriyle birden çok kiracıyı dağıtın ve yönetin.
ms.openlocfilehash: 305d7683413d5682c0dddda418e87de0a0a682b7
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027593"
---
# <a name="step-1-your-microsoft-365-for-enterprise-tenants"></a>Adım 1. Kurumsal Microsoft 365 için veritabanınız

Kiracıyla ilgili ilk kararlardan biri, bu kararların kaç tane olduğudır. Her Microsoft 365 kiracı farklı, benzersiz ve diğer tüm kiracılardan Microsoft 365 olur. Buna karşılık gelen Azure AD kiracısı da diğer tüm kiracılardan ayrı, Microsoft 365 vardır.

## <a name="single-tenant"></a>Tek kiracı
Tek bir kiracıya sahip olmak, tek kiracı kullanımınızı birçok açıdan basit Microsoft 365. Tek bir kiracı, tek bir hesap, grup ve ilke kümesi olan tek bir Azure AD kiracısı anlamına gelir. Bu merkezi kimlik sağlayıcısı aracılığıyla, kuruluş genelinde izinler ve kaynak paylaşımı yapılabilir.

Tek bir kiracı, kullanıcılarınız için en zengin özellik ve basitleştirilmiş işbirliği ve üretkenlik deneyimini sağlar.

Burada, bir kiracının varsayılan konumunu ve Azure AD kiracısı'Microsoft 365 örneği ve ardından bir Microsoft 365 ve ve bir örnek 2013'Microsoft 365 tıklayın.

![Azure AD Microsoft 365 tek bir kiracı.](../media/tenant-management-overview/tenant-management-example-tenant.png)

## <a name="multiple-tenants"></a>Birden çok kiracı

Kuruluşta birden çok kiracıya sahip nedenleri olabilir:

- Yönetime yalıtma
- 1. Yer: 12.000'
- Geçmiş kararlar
- Şirket birleşmeleri, alımlar veya şirket birleşmeleri
- Diğer kuruluşlar için markalama konusunda net ayrım
- Üretim öncesi, test veya korumalı alan kiracıları

Burada, aynı varsayılan veri merkezinde coğrafi olarak iki kiracısı (Kiracı A ve Kiracı B) olan bir kuruluş örneği ve almaktadır. Her kiracı ayrı bir Azure AD kiracısı olarak.

![Kendi Microsoft 365 Azure AD kiracıları olan birden çok kiracı.](../media/tenant-management-overview/tenant-management-example-multi-tenant.png)

Birden çok kiracınız varsa, bunları yönetme ve kullanıcılarınıza hizmet sağlama konusunda kısıtlamalar ve dikkate alınması gereken başka noktalar vardır.

### <a name="inter-tenant-collaboration"></a>Kiracılar arası işbirliği

Kullanıcılarının güvenli bir şekilde farklı Microsoft 365 kiracılarında daha etkili bir şekilde işbirliği yapmalarını sağlamak için, dosyalar ve konuşmalar için merkezi bir konum kullanma, takvimleri paylaşma, iletişim için IM, sesli/görüntülü aramalar kullanma ve kaynaklarla uygulamalara erişimi güvenlik altına alma seçenekleri yer almaktadır.

Daha fazla bilgi için bkz [Microsoft 365 kiracılar arası işbirliği.](../enterprise/microsoft-365-inter-tenant-collaboration.md)

### <a name="cross-tenant-mailbox-migration-preview"></a>Kiracılar arası posta kutusu geçişi (önizleme)

Kiracılar arası posta kutusu geçişi öncesinde (önizlemede), Exchange Online posta kutularını kiracılar arasında taşımadan önce, kullanıcı posta kutusunu geçerli kiracıdan (kaynak kiracı) şirket içinde tamamen çıkartırın ve sonra bu posta kutusunu yeni bir kiracıya (hedef kiracı) alın. Yeni kiracılar arası posta kutusu geçiş özelliğiyle, hem kaynak hem de hedef kiracılar için kiracı yöneticileri, şirket içi sistemlerinde en düşük altyapı bağımlılıkları olan kiracılar arasında posta kutularını hareket ettirebilirsiniz. Bu işlem, alan dışı posta kutuları ve ekleme ihtiyacı ortadan kaldırır.

Kiracılar arası posta kutusu geçişi öncesinde iki örnek kiracı ve onların posta kutuları burada ve ve daha sonra bu kiracıların posta kutuları yer almaktadır.

![Birden Microsoft 365 kiracıları ve onların posta kutuları.](../media/tenant-management-overview/tenant-management-cross-tenant-mailbox-before.png)

Bu çizimde, iki ayrı kiracının kendi etki alanları ve posta kutuları Exchange vardır.

Kiracılar arası posta kutusu geçişi sonrasında hedef kiracı (Kiracı A) buradadır.

![Kiracılar arası posta kutusu geçişini sonrasında hedef kiracı.](../media/tenant-management-overview/tenant-management-cross-tenant-mailbox-after.png)

Bu çizimde, tek bir kiracının hem etki alanları hem de her iki grup Exchange vardır.

Daha fazla bilgi için bkz [. Kiracılar arası posta kutusu geçişi](../enterprise/cross-tenant-mailbox-migration.md).

### <a name="tenant-to-tenant-migrations"></a>Kiracıdan kiracıya geçişler

Birleşmeler, alımlar, ayrımlar ve mevcut bir Microsoft 365 kiracıyı yeni bir kiracıya geçirmeniz için size yol açmayacak diğer senaryolar için çeşitli mimari yaklaşımlar vardır. 

Ayrıntılı bilgi için bkz [Microsoft 365 kiracıdan kiracıya geçişleri taşıma](../enterprise/microsoft-365-tenant-to-tenant-migrations.md).

## <a name="multi-geo-for-a-tenant"></a>Kiracı için Multi-Geo

Microsoft 365 Multi-Geo ile, veri yerleşim gereksinimlerini karşılamayı seçtiğiniz diğer veri merkezi coğrafi konumlarında verilerin sağlanmasına ve depo gereksinimlerinin sağlanmasına ve aynı zamanda çalışanlarınıza küresel modern üretkenlik deneyimlerinin global olarak sağlanmasına olanak sunun.

Multi-Geo ortamında, Microsoft 365 kiracınız Microsoft 365 aboneliğinizin ilk olarak oluşturulmuş olduğu varsayılan veya merkezi bir konumdan ve bir veya birden çok uydu konumdan oluşur. Çok coğrafi kiracıda, coğrafi konumlar, gruplar ve kullanıcı bilgileriyle ilgili bilgiler genel Azure AD kiracılarında ustalık sahibi olur. Kiracı bilginiz merkezi bir konumda hakimdir ve her coğrafi konumla eşitlenmiş olduğundan, şirketiniz dahil herkes tarafından yapılan işbirliği deneyimleri konumlar arasında paylaşılır.

Burada, Avrupa'da varsayılan konumu olan bir kuruluş ve Kuzey Amerika'da bir uydu konumu olan bir örnek vemektedir. Her iki konum da tek bir kiracı için aynı genel Azure AD Microsoft 365 paylaşır.

![Multi-geo Microsoft 365 örneği.](../media/tenant-management-overview/tenant-management-example-multi-geo.png)

Daha fazla bilgi için bkz[. Microsoft 365 Multi-Geo](../enterprise/microsoft-365-multi-geo.md).

## <a name="moving-core-data-to-a-new-datacenter-geo"></a>Temel verileri yeni bir veri merkezi coğrafi olarak taşıma

Microsoft, yeni veri merkezi coğrafi verilerini Microsoft 365 devam ediyor. Bu yeni veri merkezi, sürekli müşteri talebi ve kullanım büyümemizi desteklemek için kapasite ve bilgi işlem kaynakları ekler. Buna ek olarak, yeni veri merkezi coğrafi konum, çekirdek müşteri verileri için coğrafi olarak yer sağlar.

Yeni bir veri merkezi açmak sizi ve zaten var olan bir veri merkezinde depolanan çekirdek verilerinizi coğrafi olarak etkilemese de Microsoft, geri kalan temel müşteri verilerini yeni bir veri merkezi coğrafi olarak erken geçiş isteğinde bulundurmanıza olanak sağlar.

Bu örnekte, bir Microsoft 365 kiracı Avrupa Birliği (AB) veri merkezinden Birleşik Krallık'ta (İngiltere) bulunana coğrafi olarak taşınmıştır.

![Veri merkezi coğrafi Microsoft 365 bir kiracı taşıma örneği.](../media/tenant-management-overview/tenant-management-example-tenant-move.png)

Daha fazla bilgi için bkz[. Temel verileri yeni veri Microsoft 365 coğrafilere taşıma](../enterprise/moving-data-to-new-datacenter-geos.md).

## <a name="products-and-licenses-for-a-tenant"></a>Kiracı için ürünler ve lisanslar

Kiracınız Microsoft 365 satın aldığınız zaman oluşturulur (örneğin, kiracınız Microsoft 365 E3. Ürünle birlikte, aylık veya yıllık ücret tahsil olan lisanslar da vardır. Ardından bir yönetici, ürünlerinizin biri üzerinden, doğrudan veya grup üyeliği aracılığıyla bir kullanıcı hesabına kullanılabilir bir lisans atar. Kuruluşlarının iş gereksinimlerine bağlı olarak, her biri kendi lisans havuzlarına sahip bir ürün kümeniz olabilir. 

Ürün kümelerini ve lisans sayısını belirlemek için bazı planlamalar yapmak gerekir:

- Gelişmiş özelliklere ihtiyaç olan kullanıcı hesapları için yeterli lisansa sahip olduğundan emin olun.
- Kurum kurum personelinde yapılan değişikliklere bağlı olarak lisansları çalışmamanızı veya çok fazla atanmamış lisans sahibi kalmanızı engelin.


## <a name="results-of-step-1"></a>Adım 1'in sonuçları

Kurumsal kiracılar Microsoft 365 için kararlarınızı şu şekilde belirlediniz:

- Kaç kiracınız var veya buna ihtiyacınız var.
- Her kiracı için, hangi ürün ve lisansların satın alımı gerekir.
- Veri ikamet gereksinimlerini karşılamak için kiracının Multi-Geo olması gerekip gerekip gerek olmadığı.
- Kiracılar arası işbirliğini ayarlamanız gerekip gerekip gerek olmadığı.
- Bir kiracıyı diğerine geçirmeniz gerekip gerekip gerek olmadığı.
- Temel verileri bir veri merkezinden coğrafi olarak yeni bir veri merkezine taşımaya gerek olup olmadığı.

Yeni bir kiracı örneği burada ve açık bir şekilde ve şekilde açık ve açık bir

![Yeni kiracı örneği.](../media/tenant-management-overview/tenant-management-tenant-build-step1.png)

Bu çizimde, kiracının sahip olduğu:

- Veri merkezi coğrafi olarak Microsoft 365 varsayılan konum.
- Ürün ve lisans kümesi.
- Bazıları ürünlere özel bulut üretkenlik uygulamaları kümesidir.
- Genel yönetici hesaplarını ve ilk DNS etki alanı adını içeren bir Azure AD kiracısı.

Bu çözümün ek adımlarını ilerlerken bu şekilde bir adım atacağız.

## <a name="ongoing-maintenance-for-tenants"></a>Kiracılar için sürekli bakım

Sürekli olarak şunları yapmak zorundayabilirsiniz:

- Yeni kiracı ekleyin.
- Kiracıya, başlangıç lisans sayısına sahip yeni ürünler ekleyin.
- Kiracıda bir ürünün lisans kümelerini değiştirerek personel gereksinimlerini değiştirebilirsiniz.
- Temel verilerinizi kiracıdan yeni bir veri merkezi coğrafi konuma taşıma.
- Veri ikamet gereksinimleri için Multi-Geo ekleyin.
- Kiracılar arası işbirliğini ayarlayın.

## <a name="next-step"></a>Sonraki adım

[![2. Adım. Kiracınızı erişim için ağ için en iyi duruma getirme.](../media/tenant-management-overview/tenant-management-step-grid-networking.png)](tenant-management-networking.md)

Çalışanlardan [bulut](tenant-management-networking.md) hizmetlerini en iyi şekilde sunmak için ağ Microsoft 365 devam edin.
