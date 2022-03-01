---
title: Microsoft Yönetilen Masaüstü için yapılandırılabilir ayarlar
description: Microsoft Yönetilen Masaüstü ile yapılandırılabilir ayarlar hakkında bilgi
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belge, ayarlar, yapılandırılabilir ayarlar
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 910bd8d37853ce70acb6379599b0259446b0752e
ms.sourcegitcommit: 2c3b737e71038f843ef9e9ff4d5b99d6110b8ec5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2022
ms.locfileid: "63010032"
---
# <a name="configurable-settings---microsoft-managed-desktop"></a>Yapılandırılabilir ayarlar - Microsoft Yönetilen Masaüstü

Microsoft Yönetilen Masaüstü, Microsoft Yönetilen Masaüstü tarafından yönetilen tüm cihazlara uygulanan ayarları ve ilkeleri dağıtır. Daha fazla bilgi için bkz. [Cihaz yapılandırması](../service-description/device-policies.md).

Microsoft Yönetilen Masaüstü'nden yapılandırılabilir ayarlar, IT yöneticilerine kendi kuruluşlarının ve iş gereksinimlerine özgü ayarları özelleştirmeleri ve dağıtmaları için bir yol sağlar. Bu ayarlar, Microsoft Yönetilen Masaüstü tarafından yönetilen cihaz yapılandırma ayarlarına ve ilkelerin yanı sıra kullanılır.  

Yapılandırılabilir ayar değişiklikleri bulutta yapılır. Bunlar, tanımlı dağıtım gruplarında Microsoft Yönetilen Masaüstü cihazlarınıza uygulanır. Bu işlem, Microsoft Yönetilen Masaüstü'nin cihaz yapılandırma ayarları ve hizmet tarafından tanımlanan ve yönetilen ilkelerde yapılan değişiklikleri yönetmesi ile benzer. Microsoft Yönetilen Masaüstü'nin değişiklikleri dağıtmak için kullandığı işlemle, modern IT yönetim uygulamalarını kullanarak organizasyonlarınızı ileriye taşımaya devam edersiniz.

## <a name="when-to-use-configurable-settings"></a>Yapılandırılabilir ayarlar ne zaman kullanılır?

Aşağıdaki senaryolarda yapılandırılabilir ayarları kullanın:

| Senaryo | Açıklama |
| ------ | ------ |
| Ekleme işlemi | Microsoft Yönetilen Masaüstü, Microsoft Yönetilen Masaüstü hizmetine ek olarak yapılandırılabilir ayarları özelleştirmenizi veya çok sayıda cihaz (20 veya daha fazla) eklemenizi öneririz. <br><br>Kategorileri ayarlama, Microsoft Yönetilen Masaüstü yönetici portalında yapılandırılır. Yönetim portalına katıldıktan ve bu portala erişiminiz olduktan sonra, sizin için hangi ayar kategorilerini özelleştirmek istediğinize karar veabilirsiniz. Ardından değişiklikleri yapın, dağıtımı aşamalı halein ve sonra değişikliklerinizi dağıtın. |
| Ayarları koruma | Ayarlarınızı düzenli olarak gözden geçirin ve gerekli güncelleştirmeleri yapın. İşletmenizin bir değişikliğini desteklemek için değişiklik yapabilirsiniz. |

## <a name="setting-categories"></a>Kategorileri ayarlama

Aşağıdakiler, özelleştirebileceğiniz yapılandırılabilir ayarlar kategorileridir:

| Kategori | Açıklama |
| ------ | ------ |
| [Masaüstü arka plan resmi](config-setting-ref.md#desktop-background-picture) | Microsoft Yönetilen Masaüstü cihazları için masaüstü arka plan resmini özelleştirin. |
| [Tarayıcı başlangıç sayfaları](config-setting-ref.md#browser-start-pages) | Diğerleriyle birlikte kullanmak üzere başlangıç Microsoft Edge. |
| [Enterprise modu site listesi](config-setting-ref.md#enterprise-mode-site-list-location) | Siteleri ve bunların uyumluluk modunu ekleyin. Listede siteler Internet Explorer'da başlar. |
| [Güvenilen siteler](config-setting-ref.md#trusted-sites) | Güvenilen siteler ekleyin ve her site için güvenlik bölgelerini ayarlayın. |
| [Proxy sitesi özel durumları](config-setting-ref.md#proxy) | Proxy sunucu adres numaranız ile bağlantı noktası numaranız ayarlayın ve proxy sitesi özel durumları ekleyin. |

Her ayar kategorisi özelleştirilebilir ve kendi başına dağıtılabilir. Değişiklikleri birden çok ayar kategorisine aynı anda dağıtabilirsiniz. Bununla birlikte, bir ayar kategorisine bir defada yalnızca bir değişikliği dağıtabilirsiniz.

Örneğin:

- Masaüstü arka plan resmi ve güvenilen sitelerde yapılan değişiklikleri, her biri kendi dağıtımları olarak aynı anda dağıtabilirsiniz.
- Tarayıcının başlangıç sayfalarına aynı anda iki dağıtım dağıtamazsınız. En son dağıtım, devam eden önceki dağıtımları durduracak.

## <a name="configurable-setting-process"></a>Yapılandırılabilir ayar işlemi

Microsoft Yönetilen Masaüstü, sizin için yapılandırılabilir ayarları kullanırken aşağıdakine benzer bir işlem uygulamanızı öneririz:

| Adım  | İşlem |
| ------ | ------ |
| **1. Adım: Planlama** | <ol type="1"><li>Yapılandırılabilir ayarlar hakkında bilgi edinmek ve organizasyonu için hangi ayar kategorilerini yapılandırmak istediğinize karar verin.</li> <li>Her grupta değişiklik dağıtmayı beklediğiniz zaman çizelgesi oluşturun.</li> <li>İç değişiklik yönetim süreçlerinizi karşılayacak kullanıcılarınız ile iletişimi planla. Örneğin, tarayıcı başlangıç sayfaları ekliyorsanız, kullanıcılarınıza dağıtımdan sonra tarayıcılarında yeni bir başlangıç sayfaları kümesi olacaklarını haber yapın.</li></ol> |
| **2. Adım: Dağıtımı yapılandırma ve aşamalı olarak yapılandırma** | <ol type="1"><li>Microsoft Yönetilen Masaüstü yönetici portalında yapılandırılabilir ayarlarda değişiklik yapın.</li><li>Dağıtıma hazır olmak için değişiklikleri aşamalı olarak hazırlayın.</li> <li>Değişiklikleri ve değişikliklerin cihaz deneyimini nasıl değiştireceklerini kullanıcılarınıza bildirmeyi unutmayın.</li><li>Microsoft Yönetilen Masaüstü yönetici portalında değişiklikleri yapılandırarak aşamalı olarak yapabilirsiniz. Daha fazla bilgi için bkz [. Yapılandırılabilir ayarları özelleştirme](config-setting-ref.md).</li></ol>|
| **3. Adım: Değişiklikleri iletişim kurma** | <ol type="1"><li>Yaklaşan değişiklikler hakkında kullanıcılarınıza bilgi aktarabilirsiniz.</li> <li>Her dağıtım için, değişiklik yönetimi süreçlerinizin bir parçası olan iletişimi tamamlamalısınız. Kullanıcının çalışma ve cihazlarında ne göreceğini etkileyen herhangi bir değişikliği açıkça ifade edin.</li></ol> |
| **4. Adım: Değişiklikleri dağıtma** | Test grubundan başlayarak değişikliklerinizi dağıtın. Test grubu, değişiklikleri daha büyük cihaz gruplarına dağıtmadan önce, daha az cihazla bir gruptaki sorunları doğrulamanızı ve gidermenize olanak tanır. <br><br>Herhangi bir sorunla olursa, değişikliği geri döndürebilirsiniz, ayarı güncelleştirebilirsiniz ve yeni bir dağıtım aşamasına dönüştürebilirsiniz. Microsoft Yönetilen Masaüstü, yapılandırılmış yaklaşımı izlemenizi ve gruplara şu sırayla dağıtım uygulamanızı önerir: Test Edin, İlk, Hızlı ve sonra da Geniş. <br><br>Tüm yapılandırılabilir ayarlar Microsoft Yönetilen Masaüstü yönetim portalı kullanılarak yönetilir. Daha fazla bilgi için bkz [. Değişiklikleri dağıtma](config-setting-deploy.md). |
| **5. Adım: Değişiklikleri izleme** | Dağıtım durumu bölümünde değişikliklerinizin ilerleme durumunu izleyebilirsiniz. Her ayar için şunlarıabilirsiniz: <ul><li>**İlerlemeyi izleme:**  Değişikliği dağıtdikten sonra durumu izleme. Durum, Sürüyor olarak **ve sonra Tamamlandı** veya **Başarısız olarak** **değişir**. Bir dağıtım başarısız olursa, sorunu araştırılması için Microsoft Yönetilen Masaüstü İşlemleri için otomatik olarak bir destek isteği açılır.</li> <li>**Bkz. dağıtılan sürüm:** Dağıtılan her değişikliğin bir sürüm numarası vardır.</li><li>**Değişiklikleri geri döndürme:** Bir değişikliği geri döndürerek geçerli dağıtımı durdurabilirsiniz. Tüm gruplara dağıtılan son değişikliklere geri döner. Bilinen en son iyi ayar değerine geri dönüyoruz.</li><li>**Değişiklikleri doğrulama:** Dağıtım tamamlandıktan sonra, değişikliklerin beklendiği gibi uygulandığını onaylar.</li></ul> |

Bir dağıtım başarısız olursa veya bir değişikliği geri alasanız [, Microsoft](admin-support.md) Tarafından Yönetilen Masaüstü İşlemleri ile bir destek isteği açın.

Daha fazla bilgi için bkz [. Yapılandırılabilir ayarları dağıtma ve izleme](config-setting-deploy.md).

## <a name="additional-resources"></a>Ek kaynaklar

- [Yapılandırılabilir ayarlar başvurusu](config-setting-ref.md)
- [Yapılandırılabilir ayarları dağıtma](config-setting-deploy.md)
