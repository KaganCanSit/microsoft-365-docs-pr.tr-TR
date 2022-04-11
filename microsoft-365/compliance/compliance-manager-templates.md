---
title: Microsoft Compliance Manager'da değerlendirme şablonlarıyla çalışma
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.custom: admindeeplinkMAC
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Microsoft Uyumluluk Yöneticisi'nde değerlendirme oluşturmak için şablonların nasıl kullanılacağını ve yönetileceğini anlayın. Biçimlendirilmiş bir Excel dosyası kullanarak şablonlar oluşturun ve değiştirin.
ms.openlocfilehash: 0dc28eb3058e3b929da47d947b29c7ba7be41111
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759003"
---
# <a name="learn-about-assessment-templates-in-compliance-manager"></a>Uyumluluk Yöneticisi'nde değerlendirme şablonları hakkında bilgi edinin

**Bu makalede:** **Şablonların nasıl çalıştığını** ve değerlendirme şablonları sayfanızdan **nasıl yönetileceğini** anlayın. Yeni şablonlar **oluşturma**, mevcut şablonları **genişletme** ve **değiştirme**, **şablon verilerinizi Excel ile biçimlendirme** ve şablon **raporlarını** dışarı aktarma yönergelerini alın.

> [!IMPORTANT]
> Kuruluşunuzun kullanabileceği değerlendirme şablonları lisans sözleşmenize bağlıdır. [Ayrıntıları gözden geçirin](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="templates-overview"></a>Şablonlara genel bakış

Şablon, Uyumluluk Yöneticisi'nde değerlendirme oluşturmaya yönelik denetimlerin bir çerçevesidir. Kapsamlı şablon kümemiz, kuruluşunuzun verilerin toplanması ve kullanımını yöneten ulusal, bölgesel ve sektöre özgü gereksinimlere uymasına yardımcı olabilir.

## <a name="template-versions-microsoft-and-universal"></a>Şablon sürümleri: Microsoft ve evrensel

Şablonları, AB GDPR şablonu ve ISO/IEC 27701:2019 şablonu gibi temel sertifikasyon veya düzenlemeleriyle aynı ada göre adlandırıyoruz.

Uyumluluk Yöneticisi, farklı ürün türlerini değerlendirmek için kullanılabilir. Temel dışındaki tüm şablonlar, Microsoft 365 gibi önceden tanımlanmış bir ürün için geçerli olan en az bir sürüm ve diğer ürünlere uyacak şekilde uyarlanabilir evrensel bir sürümde sunulur. Evrensel şablonlardan yapılan değerlendirmeler daha genelleştirilmiştir ancak kuruluşunuzun uyumluluğunu birden çok üründe kolayca izlemenize yardımcı olabileceğinden genişletilmiş çok yönlülük sunar.

US Government Community (GCC) Moderate, GCC High ve Department of Defense (DoD) müşterilerinin şu anda evrensel şablonları kullanamayacağını unutmayın.

## <a name="template-availability-and-licensing"></a>Şablon kullanılabilirliği ve lisanslama

Uyumluluk Yöneticisi'nde iki şablon kategorisi vardır: dahil ve premium.

1. **Dahil edilen şablonlar** , Uyumluluk Yöneticisi lisansınız tarafından verilir ve temel düzenleme ve gereksinimleri kapsar. Lisans sözleşmeniz kapsamında hangi şablonların kullanılabilir olduğu hakkında daha fazla bilgi edinmek için lisans [ayrıntılarına](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager) bakın.
2. ek gereksinimleri ve senaryoları kapsayan **Premium şablonları** şablon lisansları satın alınarak elde edilebilir.

Değerlendirme oluşturmaya başladığınızda Uyumluluk Yöneticisi, kullanımınızı izleyebilebilmeniz için kaç şablonun etkin olduğunu izler. Daha fazla bilgi için bkz [. Etkin ve etkin olmayan şablonlar](compliance-manager-templates.md#active-and-inactive-templates).

Uyumluluk Yöneticisi'nde kullanılabilen [şablonların tam listesini](compliance-manager-templates-list.md) görüntüleyin.

### <a name="purchase-premium-template-licenses"></a>Premium şablon lisansları satın alma

Şablon lisansları, Uyumluluk Yöneticisi lisans sözleşmenize bağlı olarak bu yöntemlerden biri veya daha fazlası tarafından alınabilir. Satın alma işleminiz tamamlandıktan sonra şablonlar 48 saat içinde kiracınızda kullanılabilir duruma gelir.

**Ticari ve GCC Orta**

Ticari ve GCC Moderate hesapları yönetim merkezinden şablon lisansları satın alabilir ([abonelikler, lisanslar ve faturalama hakkında daha fazla bilgi edinin](/microsoft-365/commerce/)). Satın almak istediğiniz lisans miktarını ve ödeme planınızı seçin.

Satın alma bağlantıları:

- [Ticari](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/46E9BF2A-3C8D-4A69-A7E7-3DA04687636D)
- [orta GCC](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/3129986d-5f4b-413b-a34b-b706db5a7669)

Ayrıca[, Bulut Çözümü Sağlayıcısı programına](https://partner.microsoft.com/membership/cloud-solution-provider) veya [toplu lisanslamaya](https://www.microsoft.com/licensing/licensing-programs/licensing-programs) katılarak lisans alabilirsiniz.

**Yüksek ve DOD hesaplarını GCC**

GCC Yüksek ve DOD hesapları [toplu lisanslama](https://www.microsoft.com/licensing/licensing-programs/licensing-programs) aracılığıyla şablon lisansları satın almalıdır.

### <a name="try-out-premium-templates"></a>Premium şablonları deneyin

Satın alma işlemi yapmadan önce premium şablonları denemek için lisansların deneme sürümlerini de alabilirsiniz. Deneme lisansları, 90 gün boyunca 25 şablona kadar kullanılabilir. Deneme lisansınızı aldıktan sonra şablonlar 48 saat içinde kiracınızda kullanılabilir duruma gelir.

Kuruluşunuzun Uyumluluk Yöneticisi için ticari lisansı varsa, [Microsoft Compliance Manager premium değerlendirmeleri için ücretsiz deneme sürümü hakkında](compliance-easy-trials-compliance-manager-assessments.md) makalesinde denemenizi nasıl başlatacağınızı öğrenebilirsiniz.

Kuruluşunuz GCC veya DOD lisansı altındaysa, kuruluşunuz için uygun deneme bağlantısını seçin:

- [orta GCC](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/87ed2908-0a8d-430a-9635-558ed42b581f)
- [yüksek GCC](https://portal.office365.us/SubscriptionDetails?OfferId=e14362d7-2c11-4a43-9c92-59f1b499b96a)
- [DOD](https://portal.apps.mil/Commerce/Trial.aspx?OfferId=17e28290-7de6-41a9-af30-f6497396ab2e)

#### <a name="active-and-inactive-templates"></a>Etkin ve etkin olmayan şablonlar

Şablonlar etkinleştirme durumunu etkin veya etkin değil olarak görüntüler:

- Bu şablondan bir değerlendirme oluşturduktan sonra şablon **etkin** olarak kabul edilir.
- Kuruluşunuz bir değerlendirme için kullanmıyorsa şablon **etkin** değil olarak kabul edilir.

Değerlendirmeleri satın alınan bir premium şablona bağlarsanız, bu şablon bir yıl boyunca etkin olur. İptal etmediğiniz sürece satın alma işleminiz otomatik olarak yenilenir.

#### <a name="activated-templates-counter"></a>Etkinleştirilmiş şablonlar sayacı

Değerlendirme sayfanızın ve değerlendirme şablonları sayfanızın üst kısmına yakın bir **etkinleştirilmiş şablonlar** sayacı vardır. Sayaç, lisans sözleşmenize göre kullanmaya uygun olduğunuz sayıda kullanımdaki şablonların sayısını görüntüler. Şablon kullanımı sertifika düzeyinde sayılır.

Örneğin, sayacınız 5/2 gösteriyorsa bu, kuruluşunuzun 5 şablondan 2'sini etkinleştirdiği ve kullanılabilecek 5 şablonu etkinleştirdiği anlamına gelir.

Sayacınız 5/2 gösteriyorsa, bu durum kuruluşunuzun sınırlarını aştığını ve kullanımda olan premium şablonlardan 3'ünü satın alması gerektiğini gösterir.

Microsoft 365 gibi önceden tanımlanmış bir ürün için şablonlar, aynı şablonun evrensel sürümleriyle ortak lisanslamaya sahiptir. Bu, birden fazla üründe aynı temel sertifikayı kullanmanıza olanak tanır. Aynı şablonun ya da her iki sürümünün kullanılması yalnızca bir etkinleştirilmiş şablon olarak sayılır.

Diğer ayrıntılar için bkz [. Uyumluluk Yöneticisi lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager).

## <a name="view-and-manage-templates"></a>Şablonları görüntüleme ve yönetme

Uyumluluk Yöneticisi'ndeki değerlendirme şablonları sayfasında şablonların listesi ve bunlar hakkındaki önemli ayrıntılar görüntülenir. Liste, Uyumluluk Yöneticisi tarafından sağlanan şablonların yanı sıra kuruluşunuzun değiştirdiği veya oluşturduğu şablonları içerir. Sertifikasyon, ürün kapsamı, ülke, sektör, şablonu oluşturan kişi ve şablonun değerlendirme oluşturma için etkinleştirilip etkinleştirilmediğini temel alan bir şablon bulmak için filtreler uygulayabilirsiniz.

Ayrıntılar sayfasını açmak için satırından bir şablon seçin. Bu sayfa şablonun açıklamasını ve sertifikasyon, kapsam ve denetim ayrıntıları hakkında daha fazla bilgi içerir. Bu sayfadan değerlendirme oluşturmak için uygun düğmeleri seçebilir, şablon verilerini Excel dışarı aktarabilir veya şablonu değiştirebilirsiniz.

## <a name="create-an-assessment-template"></a>Değerlendirme şablonu oluşturma

Compliance Manager'da özel değerlendirmeler için kendi yeni şablonunuzu oluşturmak için, gerekli denetim verilerini bir araya getirmek üzere özel olarak biçimlendirilmiş bir Excel elektronik tablosu kullanacaksınız. Elektronik tabloyu tamamladıktan sonra Uyumluluk Yöneticisi'ne aktaracaksınız. Daha fazla bilgi için bkz. [Değerlendirme şablonu oluşturma](compliance-manager-templates-create.md).

## <a name="modify-an-assessment-template"></a>Değerlendirme şablonunu değiştirme

Uyumluluk Yöneticisi'nde değerlendirmelerle çalışırken, oluşturduğunuz bir değerlendirme şablonunu değiştirmek isteyebilirsiniz. bu işlem, şablon verilerinizi içeren biçimlendirilmiş bir Excel dosyasını karşıya yükleyebilmek için şablon oluşturma işlemine benzer. Değişiklik yapma ve hala korumak istediğiniz verileri koruma hakkında daha fazla bilgi edinmek için bkz. [Değerlendirme şablonunu değiştirme](compliance-manager-templates-modify.md).

## <a name="extend-an-assessment-template"></a>Değerlendirme şablonunu genişletme

Uyumluluk Yöneticisi, mevcut bir şablona kendi denetimlerinizi ve iyileştirme eylemlerinizi ekleme seçeneği sunar. Bu işleme şablonu genişletme denir. Şablonu genişletmek için, Microsoft değerlendirme şablonlarını veya evrensel değerlendirme şablonlarını genişletip genişletmediğinize bağlı olarak şablon verilerine eklemeye yönelik özel yönergeleri kullanacaksınız. Daha fazla bilgi için bkz. [Değerlendirme şablonunu genişletme](compliance-manager-templates-extend.md).

## <a name="format-assessment-template-data-in-excel"></a>Excel'de değerlendirme şablonu verilerini biçimlendirme

Uyumluluk Yöneticisi'nde değerlendirme şablonları oluştururken, değiştirirken veya genişletirken, belirli bir biçim ve şema kullanan Excel elektronik tablolarla çalışırsınız. Dosyaların doğru içeri aktarılması için bu belirtimlere uyulmalıdır. Daha fazla bilgi için bkz. [Excel'de değerlendirme şablonu verilerini biçimlendirme](compliance-manager-templates-format-excel.md).

## <a name="export-a-template"></a>Şablonu dışarı aktarma

Şablonun tüm verilerini içeren bir Excel dosyasını dışarı aktarabilirsiniz. Değiştirmek için bir şablonu dışarı aktarmanız gerekir çünkü bu, [düzenleme ve değiştirme işleminde](compliance-manager-templates-modify.md) karşıya yüklediğiniz Excel dosyası olacaktır. Ayrıca, yeni bir özel şablon oluştururken şablonun verilerini kullanmak istiyorsanız başvuru için şablonu dışarı aktarabilirsiniz.

Şablonunuzu dışarı aktarmak için şablon ayrıntıları sayfanıza gidin ve **Excel dışarı aktar** düğmesini seçin.

Uyumluluk Yöneticisi şablonundan genişlettiğiniz bir şablonu dışarı aktarırken, dışarı aktarılan dosyanın yalnızca şablona eklediğiniz öznitelikleri içereceğini unutmayın. Dışarı aktarılan dosya, Microsoft tarafından sağlanan özgün şablon verilerini içermez. Böyle bir rapor almak için [değerlendirme raporunu dışarı aktarma](compliance-manager-assessments.md#export-an-assessment-report) yönergelerine bakın.