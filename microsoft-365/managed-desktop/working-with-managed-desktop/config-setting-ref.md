---
title: Microsoft Yönetilen Masaüstü için yapılandırılabilir ayarlar başvurusu
description: Microsoft Yönetilen Masaüstü'de yapılandırılabilir ayarlar için kategorileri ayarlama
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 18fc51f37e66cd3212ea1e5af22ed4389d025a05
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755085"
---
# <a name="configurable-settings-reference---microsoft-managed-desktop"></a>Yapılandırılabilir ayarlar başvurusu - Microsoft Yönetilen Masaüstü

Bu makalede, müşterilerin Microsoft Yönetilen Masaüstü ile yapılandırabilir ayarlar kategorileri listelemektedir. Her ayar kategorisi gereksinimler, en iyi yöntemler ve ayar kategorisini özelleştirme hakkında bilgi içerir.

> [!NOTE]
> Bu sayfa, sık istenen ayarlarla ilgili bilgileri içerir. Eski Edge tarayıcısı için geçerlidir.

## <a name="desktop-background-picture"></a>Masaüstü arka plan resmi

Kurumdaki Microsoft Yönetilen Masaüstü cihazları için masaüstü arka plan resmini özelleştirebilirsiniz. Şirket markası veya pazarlama materyallerini uygulamak için masaüstü arka plan resmini kullanabilirsiniz.

### <a name="requirements"></a>Gereksinimler

Masaüstü arka plan resmi için bu gereksinimlerin karşılan olması gerekir:

- Resim dosyası biçimi: .jpg, jpeg veya .png
- Dosya konumu: Güvenilir bir güvenli http (https) konumda ana bilgisayar.
- İzin verilmiyor: Http ve dosya paylaşımı (unc) konumları desteklenmiyor.

### <a name="customize-and-deploy-desktop-background-picture"></a>Masaüstü arka plan resmini özelleştirme ve dağıtma

**Özel bir masaüstü arka plan resmi eklemek için:**

1. E-Microsoft Endpoint Manager [açın](https://endpoint.microsoft.com/) ve Cihazlar **menüsüne** gidin.
2. Microsoft Yönetilen Masaüstü bölümünde Yönet'i **Ayarlar**.
3. Çalışma **Ayarlar Masaüstü** arka plan **resmi'ne tıklayın**.
4. Kullanmak istediğiniz resmin konumunu girin.
5. **Değişikliklerinizi kaydetmek ve** Test grubuna dağıtmak için Dağıtımı aşamalı olarak dağıt'ı seçin.

## <a name="browser-start-pages"></a>Tarayıcı başlangıç sayfaları

Kullanıcılarınız tarayıcı başlatmayı açtıklarında tarayıcı başlangıç sayfaları tek Microsoft Edge. Kullanıcılarınızı sık kullanılan bir dizi siteyi açmayı daha kolay hale başlatmak için her site için bir tarayıcı başlangıç sayfası ekleyin.

### <a name="requirements"></a>Gereksinimler

Tarayıcınızın başlangıç sayfaları için intranet veya İnternet siteleri için tam etki alanı adını (FQDN) sağlay gerekir. İç siteler yapılandırılmışsa, kullanıcılara erişime yalnızca iç ağa bağlı olduğunda veya VPN aracılığıyla bağlanıldığında izin verilmiyor konusunda bilgi edinebilirsiniz.

### <a name="customize-and-deploy-browser-start-pages"></a>Tarayıcı başlangıç sayfalarını özelleştirme ve dağıtma

**Tarayıcı başlangıç sayfası eklemek için:**

1. E-Microsoft Endpoint Manager [açın](https://endpoint.microsoft.com/) ve Cihazlar **menüsüne** gidin.
2. Microsoft Yönetilen Masaüstü bölümünde Yönet'i **Ayarlar**.
3. Çalışma **Ayarlar Tarayıcı** başlangıç **sayfaları'ı seçin**.
4. Başlangıç sayfası **ekle'yi seçin**.
5. Tarayıcı **başlangıç sayfası ekle'de**, kullanmak istediğiniz sitenin URL'sini girin ve Başlangıç sayfası **ekle'yi seçin**.
6. Daha fazla tarayıcı başlangıç sayfası eklemek için 1-5 adımlarını yineleyin.
7. **Değişikliklerinizi kaydetmek ve** Test grubuna dağıtmak için Dağıtımı aşamalı olarak dağıt'ı seçin.

## <a name="enterprise-mode-site-list-location"></a>Enterprise modunda site listesi konumu

Web siteleriyle ilgili uyumluluk sorunları olan belirli web siteleriniz ve uygulamalarınız Microsoft Edge varsa, Enterprise Modu site listesini kullanarak web sitelerini Otomatik Olarak Internet Explorer 11'de açabilirsiniz. Ayrıca intranet sitelerinin Internet Explorer 11'de Microsoft Edge düzgün çalışmadıysa, tüm intranet sitelerini otomatik olarak Internet Explorer 11'de açılacak şekilde ayarlayın.

Mobil Enterprise modunu kullanmak, Microsoft Edge olarak varsayılan tarayıcınız olarak kullanmaya devam ederken uygulamalarınızı da Internet Explorer 11'de çalışmaya devam edecek şekilde emin olmak anlamına gelir. Kurumsal modda site listeleri hakkında daha fazla bilgi için bkz. [Enterprise Modu'Enterprise Site Listeleri'ne bakın](/internet-explorer/ie11-deploy-guide/what-is-enterprise-mode).

Bir konum veya `https://` kurumsal mod site listenizi barındırmış olduğunuz bir iç paylaşım için konum belirtebilirsiniz.

### <a name="requirements"></a>Gereksinimler

Kurumsal mod site listesi dosyası için bu gereksinimlerin karşılan olması gerekir:

- Dosya biçimi: Dosya gereksinimlerini karşılayacak XML [dosyası](/internet-explorer/ie11-deploy-guide/what-is-enterprise-mode#site-list-xml-file).
- Dosya konumu: Bir iç https konumdaki ana bilgisayar dosyası.
- İzin verilmiyor: gibi bir iç dosya paylaşımında `//sharename`barındırmaya izin verilmez.

### <a name="best-practices"></a>En iyi uygulamalar

Müşterilerin, IT altyapılarını modernleştirmek için karar almalarına yardımcı olmak için bu en iyi yöntemler sunulmaktadır:

| Alıştırma | Açıklama |
| ------ | ------ |
| Sınırlı sayıda site seçin | Microsoft Yönetilen Masaüstü, Microsoft Edge açısından genel güvenliği ve kullanıcılarınız açısından kullanılabilirliği geliştirmek için tercih edilen tarayıcı olarak Microsoft Edge'ı kullanır. Bu listede çoğu site, tarayıcının eski bir sürümüne ihtiyaç ihtiyacı olan eski web uygulamalarına göre hazır bulunmaktadır. Bu, çok fazla güvenlik özelliği içermez. |
| Alternatif olarak düşünün | Daha eski bir tarayıcı gerektirmeyen farklı bir siteyi veya web uygulamasını düşünün. Güncelleştirmeyi de düşünebilirsiniz; böylece daha yeni tarayıcılar da kullanabilir. Daha yeni tarayıcılar en son teknolojiyi kullanır ve güvenliği geliştirmeye yardımcı olur. |

### <a name="customize-and-deploy-enterprise-site-mode-list-location"></a>Site modu Enterprise konumunu özelleştirme ve dağıtma

**Kurumsal site modu liste konumu eklemek için:**

1. E-Microsoft Endpoint Manager [açın](https://endpoint.microsoft.com/) ve Cihazlar **menüsüne** gidin.
2. Microsoft Yönetilen Masaüstü bölümünde Yönet'i **Ayarlar**.
3. Çalışma **Ayarlar**, Site **modu Enterprise konumunu seçin**.
4. Site listeniz için https konumunu girin.
5. **Değişikliklerinizi kaydetmek ve** Test grubuna dağıtmak için Dağıtımı aşamalı olarak dağıt'ı seçin.

## <a name="trusted-sites"></a>Güvenilen siteler

Güvenilen siteler, farklı siteler için güvenlik bölgelerini özelleştirmenize veya sitenin kullanıldiği yerleri özelleştirmenize olanak sağlar. Güvenlik bölgeleri şunlardır:

- Bölge 1: Yerel Intranet bölgesi
- Bölge 2: Güvenilen siteler bölgesi
- Bölge 3: İnternet bölgesi
- Bölge 4: Kısıtlanmış Siteler bölgesi

### <a name="requirements"></a>Gereksinimler

Güvenilen her site için intranet veya İnternet siteleri için tam etki alanı adını (FQDN) sağlar.

### <a name="customize-and-deploy-trusted-sites"></a>Güvenilen siteleri özelleştirme ve dağıtma

**Güvenilir site eklemek için:**

1. E-Microsoft Endpoint Manager [açın](https://endpoint.microsoft.com/) ve Cihazlar **menüsüne** gidin.
2. Microsoft Yönetilen Masaüstü bölümünde Yönet'i **Ayarlar**.
3. Güvenilir **Ayarlar'yi** seçin ve **sonra da** Güvenilen site **ekle'yi seçin**.
4. Güvenilen **site ekle'ye** URL'yi girin, bir güvenlik bölgesi seçin ve sonra da Güvenilen site **ekle'yi seçin**.
5. Eklemek istediğiniz her güvenilen site için 1-4 adımlarını yinelayın.
6. **Değişikliklerinizi kaydetmek ve** Test grubuna dağıtmak için Dağıtımı aşamalı olarak dağıt'ı seçin.

**Güvenilen siteyi kaldırmak için:**

1. E-Microsoft Endpoint Manager [açın](https://endpoint.microsoft.com/) ve Cihazlar **menüsüne** gidin.
2. Microsoft Yönetilen Masaüstü bölümünde Yönet'i **Ayarlar**.
3. Çalışma **Ayarlar** Güvenilen **siteler'i seçin**.
4. Silmek istediğiniz siteyi seçin ve ardından Sil'i **seçin**.
5. Silmek istediğiniz her güvenilen site için 1-4 adımlarını yinelayın.
6. **Değişikliklerinizi kaydetmek ve** Test grubuna dağıtmak için Dağıtımı aşamalı olarak dağıt'ı seçin.

## <a name="proxy"></a>Proxy

Ağ ara sunucusu ayarlarını, kurum için yönetebilirsiniz. Proxy sunucu ve bağlantı noktası numaranız ile proxy sitesi özel durumlarınızı ekleyin.

Microsoft Yönetilen Masaüstü, hizmetin çalışması için gereken bir dizi varsayılan ara sunucu özel durumu içerir. Varsayılan dışlama listesi yalnızca Microsoft Yönetilen Masaüstü hizmeti tarafından değiştirilebilir. Daha fazla bilgi için bkz [. Microsoft Yönetilen Masaüstü için ağ yapılandırması](../get-ready/network.md).

Microsoft Yönetilen Masaüstü portalına eklenen ara sunucu sitesi özel durumları, Microsoft Yönetilen Masaüstü hizmetinin varsayılan ara sunucu özel durumlarına eklenir.

> [!NOTE]
> Varsayılan ara sunucu özel durumu listesini güncelleştirmek her zaman müşteri dağıtımları üzerinden önceliklidir. Başka bir ifadeyle, varsayılan ara sunucu özel durum listesi için bir dağıtım varsa aşamalı dağıtımınız duraklatılır.  

### <a name="requirements"></a>Gereksinimler

Ara sunucu ve proxy sitesi özel durumları için bu gereksinimler karşılan bir durumdur:

- Geçerli bir sunucu adresi ve bağlantı noktası numarası olmalıdır.
- URL'ler geçerli bir http sitesi olmalıdır.
- Ara sunucu özel durumları en çok 2064 karakterle sınırlı olmalıdır. Bu, Microsoft Yönetilen Masaüstü adreslerini de içerir.

### <a name="customize-and-deploy-proxies"></a>Sunucu sunucularını özelleştirme ve dağıtma

**Tek bir ara sunucu sitesi özel durumu eklemek için:**

1. E-Microsoft Endpoint Manager [açın](https://endpoint.microsoft.com/) ve Cihazlar **menüsüne** gidin.
2. Microsoft Yönetilen Masaüstü bölümünde Yönet'i **Ayarlar**.
3. Çalışma **Ayarlar** Proxy'yi **seçin**.
4. Proxy sunucunuz **için Adres** **ve Bağlantı Noktası** numarasını girin ve sonra Proxy özel durumu **ekle'yi seçin**.
5. Geçerli bir http sitesinin URL'sini girin ve sonra Proxy özel durumu **ekle'yi seçin**.
6. Eklemek istediğiniz her güvenilir site için 1-5 adımlarını yinelayın.
7. **Değişikliklerinizi kaydetmek ve** Test grubuna dağıtmak için Dağıtımı aşamalı olarak dağıt'ı seçin.

## <a name="additional-resources"></a>Ek kaynaklar

- [Yapılandırılabilir ayarlara genel bakış](config-setting-overview.md)
- [Yapılandırılabilir ayarları dağıtma](config-setting-deploy.md)
