---
title: Özel durumlar için bekletme etiketleri oluşturma
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
description: İhtiyaç duyduklarınızı koruyabilmeniz ve tutmadığınız şeyleri silebilmeniz için veri yaşam döngüsü yönetimi için bekletme ilkelerine yönelik özel durumlar için bekletme etiketleri oluşturma yönergeleri.
ms.openlocfilehash: 0951ce1fea2f9324c19ec0bf17451d458b4914d1
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632585"
---
# <a name="create-retention-labels-for-exceptions-to-your-retention-policies"></a>Bekletme ilkelerinizin özel durumları için bekletme etiketleri oluşturma

>*[Güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

İhtiyacınız olanı korumak ve istemediğinizi silmek için veri idaresi stratejinizin bir parçası olarak, bekletme ilkelerinizde özel durumlara ihtiyaç duyan öğeler için birkaç bekletme etiketi oluşturmanız gerekebilir.

Bekletme ilkeleri kapsayıcı düzeyindeki tüm öğelere (SharePoint siteleri, kullanıcı posta kutuları vb.) otomatik olarak uygulanırken, bekletme etiketleri SharePoint belgesi veya e-posta iletisi gibi tek tek öğelere uygulanır.

Belirli SharePoint, OneDrive veya Exchange öğeleri için bekletme ilkesini tamamlamak üzere bekletme etiketlerini kullanmadan önce bekletme [ilkelerini](retention.md#the-principles-of-retention-or-what-takes-precedence) anladığınızdan emin olun. Genellikle, belirli öğeleri uygulanan bekletme ilkesinden daha uzun süre saklamak için bekletme etiketlerini kullanırsınız, ancak bekletme süresinin sonunda otomatik silmeyi geçersiz kılmak veya farklı bir silme süresi uygulamak için de kullanılabilirler.

Tipik bir örnek olarak: SharePoint sitelerinizdeki içeriğin büyük bölümü, saklama ilkesi kapsamında olan üç yıl boyunca saklanmalıdır. Ama yedi yıl boyunca saklanması gereken bazı sözleşme belgeleriniz var. Bu özel durumlar bekletme etiketleriyle giderilebilir. Bekletme ilkesini tüm SharePoint sitelerine atadıktan sonra, bekletme etiketlerini sözleşme belgelerine uygularsınız. Tüm SharePoint öğeleri üç yıl boyunca saklanır ve yalnızca sözleşme belgeleri yedi yıl boyunca saklanır.

Bekletme etiketlerinin bekletme ilkelerinin özel durumları olarak nasıl kullanılabileceğini gösteren daha fazla örnek için bkz. [Bekletme ilkelerini ve bekletme etiketlerini birleştirme](retention.md#combining-retention-policies-and-retention-labels).

Bekletme etiketleri, bekletme ilkelerine göre daha fazla özelliği de destekler. Daha fazla bilgi için bkz. [Bekletme ilkeleri ve bekletme etiketleri için özellikleri karşılaştırma](retention.md#compare-capabilities-for-retention-policies-and-retention-labels).

Veri yaşam döngüsü yönetim stratejinizin bir parçası olarak bekletme ilkelerini desteklemek üzere bekletme etiketleri oluşturmanıza yardımcı olması için aşağıdaki bilgileri kullanın.

> [!NOTE]
> İşletme, yasal veya mevzuat kaydı tutma gereksinimleri için yüksek değerli öğeleri yönetmek için bekletme etiketleri kullanmanız gerekiyorsa, **Veri yaşam döngüsü yönetimi** yerine **Kayıtlar yönetimi** çözümünden bekletme etiketleri oluşturun. Örneğin, olay tabanlı saklama veya değerlendirme değerlendirmesini kullanmak istiyorsunuz. Yönergeler için bkz. [Bekletme etiketleri oluşturmak ve yönetmek için dosya planını kullanma](file-plan-manager.md).

## <a name="before-you-begin"></a>Başlamadan önce

Kuruluşunuzun genel yöneticisi, bekletme etiketleri ve ilkelerini oluşturmak ve düzenlemek için tam izinlere sahiptir. Genel yönetici olarak oturum açmadıysanız bkz. [Bekletme ilkeleri ve bekletme etiketleri için izinler](get-started-with-data-lifecycle-management.md#permissions-for-retention-policies-and-retention-labels).

## <a name="how-to-create-retention-labels-for-data-lifecycle-management"></a>Veri yaşam döngüsü yönetimi için bekletme etiketleri oluşturma

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/) şu sayfaya gidin: **Çözümler** > **Veri yaşam döngüsü yönetimi** > **Etiketleri** sekmesi > + **Etiket oluşturma**
    
    **Veri yaşam döngüsü yönetimi** çözümünü hemen görmüyor musunuz? İlk olarak **Tümünü göster'i** seçin. 

2. Bekletme etiketini oluşturmak için istemleri izleyin. Etiket kaydedildikten sonra değiştirilemediğinden, hangi adı seçtiğinize dikkat edin.
    
    Bekletme ayarları hakkında daha fazla bilgi için bkz. [İçeriği saklama ve silme ayarları](retention-settings.md#settings-for-retaining-and-deleting-content).

3. Etiketi oluşturduktan ve etiketi yayımlama seçeneklerini gördükten sonra etiketi otomatik olarak uygulayın veya yalnızca etiketi kaydedin: **Yalnızca şimdilik etiketi kaydet'i** ve ardından **Bitti'yi** seçin.

4. Farklı bekletme ayarları için ihtiyacınız olan daha fazla bekletme etiketi oluşturmak için bu adımları yineleyin.

Var olan bir etiketi düzenlemek için etiketi seçin ve ardından **Etiketi düzenle** seçeneğini belirleyerek etiket açıklamalarını ve uygun ayarları değiştirmenize olanak tanıyan Bekletme etiketini düzenle yapılandırmasını başlatın.

Etiket oluşturulduktan ve kaydedildikten sonra ayarların çoğu değiştirilemez; bunlar şunlardır:
- Bekletme süresi dışında bekletme etiketi adı ve bekletme ayarları. Ancak, bekletme süresinin öğelerin etiketlendiği zamanlara göre olduğu saklama süresini değiştiremezsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Artık bekletme etiketleri oluşturdunuz, etiketleri yayımlayarak veya otomatik olarak uygulayarak öğelere eklenmeye hazırlar:
- [Bekletme etiketlerini yayımlama ve uygulamalarda uygulama](create-apply-retention-labels.md)
- [İçeriğe otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md)
