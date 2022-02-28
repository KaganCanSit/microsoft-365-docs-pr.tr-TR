---
title: Microsoft Uyumluluk Yöneticisi'nde değerlendirme şablonlarıyla çalışma
f1.keywords:
- NOCSH
ms.author: v-jgriffee
author: jmgriffee
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
description: Microsoft Uyumluluk Yöneticisi'nde değerlendirme oluşturmak için şablonları kullanmayı ve yönetmeyi anlıyoruz. Biçimlendirilmiş bir dosya kullanarak şablon oluşturma Excel değiştirme.
ms.openlocfilehash: 99e243e86c66babd9a983ae6df891f4094cdbb83
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2021
ms.locfileid: "62989983"
---
# <a name="learn-about-assessment-templates-in-compliance-manager"></a>Uyumluluk Yöneticisi'nde değerlendirme şablonları hakkında bilgi

**Bu makalede:** **Şablonların nasıl iş olduğunu** **ve değerlendirme şablonları sayfasından** bunları nasıl yöneteceklerini anlıyoruz. Yeni şablonlar oluşturma **,** var olan **şablonları genişletme** ve değiştirme,  şablon verilerinizi yeni şablonlarla biçimlendirme ve **Excel** raporları dışarı aktarma **yönergelerini alın**.

> [!IMPORTANT]
> Organizasyonda kullanılabilen değerlendirme şablonları lisans sözleşmenize bağlıdır. [Ayrıntıları gözden geçirebilirsiniz](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="templates-overview"></a>Şablonlara genel bakış

Şablon, Uyumluluk Yöneticisi'nde değerlendirme oluşturmaya ilişkin denetimlerin çerçevesidir. Kapsamlı şablon kümemiz, kuruluşta verilerin toplanması ve kullanımının geçerli olduğu ulusal, bölgesel ve sektöre özgü gereksinimlere uyum içinde yer almaktadır.

Şablonlara, EU GDPR şablonu ve ISO/IEC 27701:2019 şablonu gibi temel sertifika veya düzenlemeleriyle aynı adı kullanarak başvururuz. Uyumluluk Yönetimi farklı ürün türlerini değerlendirmek için kullanalir, her şablon iki sürümde gelir: biri Microsoft 365 gibi önceden tanımlanmış bir ürün için geçerli olan ve seçtiğiniz ürüne uyacak şekilde uyarlanmış evrensel sürüm.

ABD Kamu Community (GCC) Orta, GCC Yüksek ve Savunma Bölümü (DoD) müşterilerinin şu anda evrensel şablonları kullanamamaktadır.

## <a name="template-availability-and-licensing"></a>Şablon kullanılabilirliği ve lisanslama

Uyumluluk Yöneticisi'nde iki şablon kategorisi vardır: dahil ve premium.

1. **Şablonlar, Uyumluluk** Yöneticisi lisansınız tarafından verilen şablonlarla önemli düzenlemeleri ve gereksinimleri içerir. Lisans sözleşmeniz kapsamındaki şablonlar hakkında daha fazla bilgi edinmek için lisans [ayrıntılarına bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager).
2. **Premium 2013'e** kadar olan lisanslar, satın alma şablonu lisansları ile edinilen diğer ihtiyaçları ve senaryoları kapsıyor.

Değerlendirme oluşturmaya başsanız, Uyumluluk Yöneticisi kaç şablonun etkin olduğunu izleyebilir ve böylece kullanımınızı izleyebilirsiniz. Daha fazla bilgi edinmek için [bkz. Etkin ve etkin olmayan şablonlar](compliance-manager-templates.md#active-and-inactive-templates).

Uyumluluk [Yöneticisi'nde bulunan şablonların](compliance-manager-templates-list.md) tam listesini görüntüleme.

### <a name="purchase-premium-template-licenses"></a>Premium şablon lisansları satın alma

Uyumluluk Yöneticisi lisans sözleşmenize bağlı olarak, şablon lisansları bu yöntemlerden biri veya birden fazlası ile elde edilir. Satın alma siparişiniz sonuçlaştırıldıktan sonra şablonların 48 saat içinde kiracıda kullanılabilir olması gerekir.

**Ticari ve GCC Orta**

Ticari GCC Hesapları Yönetim merkezinden şablon lisansları satın alabilirsiniz (abonelikler, lisanslar ve faturalama hakkında daha fazla [bilgi edinin](/microsoft-365/commerce/)). Satın almak istediğiniz lisans miktarını ve ödeme planınızı seçin.

Satın alma bağlantıları:

- [Ticari](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/46E9BF2A-3C8D-4A69-A7E7-3DA04687636D)
- [GCC Orta](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/3129986d-5f4b-413b-a34b-b706db5a7669)

Ayrıca, lisansları lisans programına katılımınız veya [toplu Bulut Çözümü Sağlayıcısı](https://partner.microsoft.com/membership/cloud-solution-provider) [lisanslama yoluyla da edinabilirsiniz](https://www.microsoft.com/licensing/licensing-programs/licensing-programs).

**GCC yüksek ve DOD hesapları**

GCC ve DOD hesaplarının toplu lisans aracılığıyla şablon [lisansları satın almaları gerekir](https://www.microsoft.com/licensing/licensing-programs/licensing-programs).

### <a name="try-out-premium-templates"></a>Premium şablonları deneyin

Premium şablonları satın almadan önce denemek için lisansların deneme sürümlerini de edinebilirsiniz. Deneme lisansları, 90 gün boyunca en çok 25 şablon kullanılabilir. Deneme lisansınızı elde ettiyken şablonların 48 saat içinde kiracıda kullanılabilir olması gerekir.

Kuruluşta Uyumluluk Yöneticisi için ticari bir lisans varsa, Microsoft Compliance Manager premium değerlendirmeleri için ücretsiz deneme sürümü hakkında'da denemenizi nasıl [başlatabileceksiniz?](compliance-easy-trials-compliance-manager-assessments.md)

If your organization is under a GCC dod license, choose the appropriate trial link for your organization:

- [GCC Orta](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/87ed2908-0a8d-430a-9635-558ed42b581f)
- [GCC Yüksek](https://portal.office365.us/SubscriptionDetails?OfferId=e14362d7-2c11-4a43-9c92-59f1b499b96a)
- [DOD](https://portal.apps.mil/Commerce/Trial.aspx?OfferId=17e28290-7de6-41a9-af30-f6497396ab2e)

#### <a name="active-and-inactive-templates"></a>Etkin ve etkin olmayan şablonlar

Şablonlar etkinleştirme durumunu etkin veya etkin değil olarak görüntüler:

- Şablon, bu **şablondan** değerlendirme oluşturduktan sonra etkin olarak kabul edilir.
- Bir şablon, **değerlendirme için** kullan değilse devre dışı olarak kabul edilir.

Herhangi bir değerlendirmeyi satın alınan premium şablonuna bağlarsanız, bu şablon bir yıl boyunca etkin olur. Siz iptal etmedikçe alışveriş otomatik olarak yenilenir.

#### <a name="activated-templates-counter"></a>Etkinleştirilmiş şablonlar sayaçları

Değerlendirme sayfanız ve değerlendirme şablonları sayfanız, üst **kısmında etkinleştirilmiş** şablonlar sayaçları içerir. Sayaç, lisans sözleşmenize göre kullanmaya uygun kişi sayısının dışında kullanım şablonlarının sayısını gösterir. Şablon kullanımı sertifika düzeyinde sayılır.

Örneğin, sayaçda 2/5 varsa, bu da, kurumuz tarafından 5 şablondan 2'si etkinleştirildiğinden 5'ini etkinleştir olduğu anlamına gelir.

Sayaçda 5/2 değeri görüntü varsa, bu durum kurum sınırı aşıyorsa ve kullanımda olan premium şablonlardan 3'ü satın almaları gerektiğini gösterir.

Şablon gibi önceden tanımlanmış bir ürün için Microsoft 365, aynı şablonun evrensel sürümleriyle ortak lisanslama içerirler. Bu, aynı temel sertifikayı birden çok üründe kullanmana olanak sağlar. Aynı şablonun iki sürümünün birini veya her ikisini de kullanmak, tek bir etkinleştirilmiş şablon olarak sayılır.

Diğer ayrıntılar için uyumluluk [yöneticisi lisanslama kılavuzuna bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager).

## <a name="view-and-manage-templates"></a>Şablonları görüntüleme ve yönetme

Uyumluluk Yöneticisi'nde değerlendirme şablonları sayfası, şablon listesini ve bu şablonlarla ilgili önemli ayrıntıları görüntüler. Bu liste Uyumluluk Yöneticisi tarafından sağlanan şablonların yanı sıra, kurum tarafından değiştirilen veya oluşturulan tüm şablonları da içerir. Bir şablonu sertifikaya, ürün kapsamına, ülkeye, sektöre, bu şablonu oluşturana ve değerlendirme oluşturma için etkinleştirip etkinleştirilmediyse bu şablona filtre uygulayabilirsiniz.

Ayrıntıları sayfasını getirmek için satırından bir şablon seçin. Bu sayfa şablonun açıklamasını ve sertifika, kapsam ve denetim ayrıntıları hakkında daha fazla bilgi içerir. Bu sayfadan değerlendirme oluşturmak, şablon verilerini kendi verilerinize dışarı aktararak veya şablonu Excel için uygun düğmeleri seçin.

## <a name="create-an-assessment-template"></a>Değerlendirme şablonu oluşturma

Uyumluluk Yöneticisi'nde özel değerlendirmeler için kendi yeni şablonnuzu oluşturmak üzere, gerekli denetim verilerini bir araya Excel özel olarak biçimlendirilmiş bir elektronik tablo kullanırsınız. Elektronik tabloyu tamamladıktan sonra Uyumluluk Yöneticisi'ne aktarabilirsiniz. Daha fazla bilgi edinmek için bkz [. Değerlendirme şablonu oluşturma](compliance-manager-templates-create.md).

## <a name="modify-an-assessment-template"></a>Değerlendirme şablonunu değiştirme

Uyumluluk Yöneticisi'nde değerlendirmelerle çalışırken, oluşturduğunuz bir değerlendirme şablonunu değiştirmek istiyor olabilirsiniz. bu işlem, şablon verilerinizle biçimlendirilmiş bir Excel karşıya yüklediğiniz şablon oluşturma sürecine benzer. Değişiklik yapma ve yine de korumak istediğiniz verileri koruma hakkında daha fazla bilgi edinmek için bkz. [Değerlendirme şablonunu değiştirme](compliance-manager-templates-modify.md).

## <a name="extend-an-assessment-template"></a>Değerlendirme şablonunu genişletme

Uyumluluk Yöneticisi, mevcut bir şablona kendi denetimlerinizi ve geliştirme eylemlerinizi ekleme seçeneği sunar. Bu işlem şablon genişletme olarak adlandırılan bir işlemdir. Şablonu genişletmek için, Microsoft değerlendirme şablonlarını veya evrensel değerlendirme şablonlarını genişletip genişletmenize bağlı olarak, şablon verilerine eklemek için özel yönergeler kullanırsınız. Daha fazla bilgi edinmek için bkz [. Değerlendirme şablonunu genişletme](compliance-manager-templates-extend.md).

## <a name="format-assessment-template-data-in-excel"></a>Excel'de değerlendirme şablonu verilerini biçimlendirme

Uyumluluk Yöneticisi'nde değerlendirme şablonlarını oluştururken, değiştirirken veya genişletken, belirli bir Excel ve şema kullanan elektronik tablolarla çalışacaksınız. Dosyaların doğru içeri aktar olması için bu belirtimlere karşıt olması gerekir. Daha fazla bilgi edinmek için bkz[. Değerlendirme şablonu verilerini kendi Excel](compliance-manager-templates-format-excel.md).

## <a name="export-a-template"></a>Şablonu dışarı aktarma

Şablonun tüm Excel içeren bir dosya dışarı aktarabilirsiniz. Değişiklik yapmak için bir şablonu dışarı aktarmanız gerekir, çünkü bu, değişiklik Excel düzenleyemez ve karşıya yüklediğiniz dosya [olur](compliance-manager-templates-modify.md). Ayrıca, yeni bir özel şablon oluştururken şablonun verilerini kullanmak istediğiniz bir şablonu başvuru için dışarı aktarabilirsiniz.

Şablonlarınızı dışarı aktarma için, şablon ayrıntıları sayfanıza gidin ve Bu sayfaya **aktar Excel** seçin.

Uyumluluk Yöneticisi şablonundan genişletilen bir şablonu dışarı aktaracaksanız, dışarı aktarılmış dosyanın yalnızca şablona eklemış olduğunu unutmayın. Dışarı aktarıldı dosyası Microsoft tarafından sağlanan özgün şablon verilerini içermez. Böyle bir rapor almak için değerlendirme raporunu dışarı [aktarma yönergelerine bakın](compliance-manager-assessments.md#export-an-assessment-report).