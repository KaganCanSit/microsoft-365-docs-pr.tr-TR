---
title: Bekletme ilkeleriniz için özel durumlar için bekletme etiketleri oluşturma
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Bilgi yönetimine yönelik bekletme ilkelerine özel durumlar için bekletme etiketleri oluşturma yönergeleri; böylelikle size gerekenleri alıkoyma ve kullanmamanızı silebilirsiniz.
ms.openlocfilehash: 40899f517c39b926cb65730956ccb310ba5a5159
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63010163"
---
# <a name="create-retention-labels-for-exceptions-to-your-retention-policies"></a>Bekletme ilkeleriniz için özel durumlar için bekletme etiketleri oluşturma

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Size gerekenleri korumak ve sahip olmadığınız öğeleri silmek için yönetim bilgi stratejinizin bir parçası olarak, bekletme ilkeleriniz için özel durumlara gerek olan öğeler için birkaç bekletme etiketi oluşturmanız gerekir. 

Bekletme ilkeleri kapsayıcı düzeyindeki tüm öğelere (SharePoint siteleri, kullanıcı posta kutuları gibi) otomatik olarak uygulanırken, bekletme etiketleri SharePoint belgesi veya e-posta iletisi gibi tek tek öğelere uygulanır.

Belirli bekletme ilkelerini, bekletme [](retention.md#the-principles-of-retention-or-what-takes-precedence) etiketlerini kullanarak belirli bekletme ilkelerini tamamlarken SharePoint, e-OneDrive veya Exchange emin olun. Normalde, bekletme etiketlerini kullanarak uygulanmış bir bekletme ilkesinden daha uzun süreyle belirli öğeleri alıkoyabilirsiniz, ancak bunlar farklı bir silme süresi uygulamak için de kullanılabilir.

Örneğin: Site sitelerinize dahil olan SharePoint çoğunluğunun üç yıl boyunca korunması gerekir ve bu bir bekletme ilkesi kapsamındadır. Ancak, yedi yıl süreyle tutulacak bazı sözleşme belgeleriniz var. Bu özel durumlar bekletme etiketleriyle ele alınabiliyor. Bekletme ilkesi tüm sitelere SharePoint sonra, bekletme etiketlerini sözleşme belgelerine uygulayabilirsiniz. Tüm SharePoint öğeleri üç yıl süreyle korunur ve yalnızca sözleşme belgeleri yedi yıl süreyle korunur.

Bekletme etiketleri, bekletme ilkelerine göre daha fazla özelliği de destekler. Daha fazla bilgi için bkz [. Bekletme ilkeleri ve bekletme etiketleri için özellikleri karşılaştırma](retention.md#compare-capabilities-for-retention-policies-and-retention-labels).

Bilgi yönetim stratejinizin bir parçası olarak bekletme ilkelerini tamamlayıcı şekilde bekletme etiketleri oluşturmanıza yardımcı olmak için aşağıdaki bilgileri kullanın.

> [!NOTE]
> kurumsal, yasal veya yasal  düzenlemelere yönelik kayıt tutma  gereksinimlerine yönelik yaşam döngüsü yönetimi için yaşam döngüsü etiketleri oluşturmanız gerekirse, bilgi yönetimi yerine Kayıt yönetimi çözümünden bekletme etiketleri oluşturun. Örneğin, olay tabanlı bir bekletme veya incelemeyi kullanmak istiyor olabiliriz. Yönergeler için bkz [. Bekletme etiketlerini oluşturmak ve yönetmek için dosya planı kullanma](file-plan-manager.md).

## <a name="before-you-begin"></a>Başlamadan önce

Kuruluşun genel yöneticisinin bekletme etiketlerini ve ilkelerini oluşturma ve düzenlemeye yönelik tam izinleri vardır. Genel yönetici olarak oturum açmadısanız bkz. Bekletme ilkeleri [ve bekletme etiketleri izinleri](get-started-with-information-governance.md#permissions-for-retention-policies-and-retention-labels).

## <a name="how-to-create-retention-labels-for-information-governance"></a>Bilgi yönetimi için bekletme etiketleri oluşturma

1. Aşağıdaki [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com/) gidin: **SolutionsInformation** >  **governanceLabels** >  tab > + **Create a label**
    
    Bilgi yönetimi çözümünü hemen **görmüyor** musunuz? Önce, Hepsini **göster'i seçin**. 

2. Bekletme etiketini oluşturmak için istemleri izleyin. Hangi adı seçtiğinize dikkat edin, çünkü etiket kaydedildikten sonra bu değiştirilemez.
    
    Bekletme ayarları hakkında daha fazla bilgi için bkz[. Ayarlar saklama ve silme hakkında daha fazla bilgi.](retention-settings.md#settings-for-retaining-and-deleting-content)

3. Etiketi oluşturduktan ve etiketi yayımlama seçeneklerini gördüğünüzde, etiketi otomatik olarak uygulama veya yalnızca etiketi kaydetme: Yalnızca şimdilik kaydet'i ve sonra Bitti'yi **seçin**.

4. Farklı bekletme ayarları için ihtiyacınız olan başka bekletme etiketleri oluşturmak için bu adımları yinele.

Mevcut bir etiketi düzenlemek için, etiketi seçin ve sonra Etiket açıklamalarını  ve uygun ayarları değiştirmenizi sağlayan Bekletme etiketini düzenle yapılandırmasını başlatmak için Etiketi düzenle seçeneğini belirleyin.

Çoğu ayar, etiket oluşturulduktan ve kaydedildikten sonra değiştirilemez; bu şunları içerir:
- Bekletme süresi dışında bekletme etiketi adı ve bekletme ayarları. Bununla birlikte, bekletme süresi öğelerin etiketli olduğu zamanların dayandır olduğu bekletme dönemini değiştiremezsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Artık bekletme etiketleri oluşturduktan sonra, bunlar etiketleri yayımarak veya otomatik olarak uygulayarak öğelere eklenmeye hazırdır:
- [Bekletme etiketlerini yayımlama ve uygulamalarda uygulama](create-apply-retention-labels.md)
- [İçeriği otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md)