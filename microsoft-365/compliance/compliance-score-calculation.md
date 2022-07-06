---
title: Uyumluluk puanı hesaplaması
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Microsoft Purview Uyumluluk Yöneticisi'nin riskleri ele almak ve uyumluluk duruşunuzu geliştirmek için gerçekleştirilen eylemlere göre kişiselleştirilmiş bir puanı nasıl hesapladığını anlayın.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a33cbe9c4ea5b12ab0fec40068ba7dcd2f561e4e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635687"
---
# <a name="compliance-score-calculation"></a>Uyumluluk puanı hesaplaması

**Bu makalede:** Uyumluluk Yöneticisi'nin kuruluşunuz için uyumluluk puanı hesaplamasını öğrenin. Bu makalede **puanınızı yorumlama**, **Veri Koruma Temeli değerlendirmesinin** neler içerdiği, **sürekli izleme** ve **farklı eylem türlerinin nasıl yönetilip puanlanmış olduğu açıklanmaktadır**.

> [!IMPORTANT]
> Uyumluluk Yöneticisi'nden gelen öneriler, uyumluluk garantisi olarak yorumlanmamalıdır. Yasal ortamınıza göre müşteri denetimlerinin etkinliğini değerlendirmek ve doğrulamak size aittir. Bu hizmetler [, Ürün Koşulları'ndaki](https://go.microsoft.com/fwlink/?linkid=2108910) hüküm ve koşullara tabidir. Ayrıca bkz. [Güvenlik ve uyumluluk için Microsoft 365 lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-compliance-manager).

## <a name="how-to-read-your-compliance-score"></a>Uyumluluk puanınızı okuma

Uyumluluk Yöneticisi panosu genel uyumluluk puanınızı görüntüler. Bu puan, denetimler içindeki önerilen iyileştirme eylemlerini tamamlama ilerlemenizi ölçer. Puanınız geçerli uyumluluk duruşunuzu anlamanıza yardımcı olabilir. Ayrıca riski azaltma potansiyeline göre eylemleri önceliklendirmenize de yardımcı olabilir.

Puan değeri üç düzeyde atanır:

1. **İyileştirme eylem puanı**: Her eylemin olası risklere bağlı olarak puanınız üzerinde farklı bir etkisi vardır

2. **Denetim puanı**: Bu puan, denetim içindeki iyileştirme eylemleri tamamlanarak kazanılan puanların toplamıdır. Bu toplam, denetim aşağıdaki koşulların ikisini de karşıladığında genel uyumluluk puanınıza tamamen uygulanır:
    - **Uygulama Durumu** , **Uygulanan** veya **Alternatif Uygulama'ya** eşittir ve
    - **Test Sonucu****, Başarılı'ya** eşittir.

3. **Değerlendirme puanı**: Bu puan, denetim puanlarınızın toplamıdır. Eylem puanları kullanılarak hesaplanır. Kuruluşunuz tarafından yönetilen her Microsoft eylemi ve her geliştirme eylemi, denetimde ne sıklıkta başvurulduğundan bağımsız olarak bir kez sayılır.

Genel uyumluluk puanı, her Microsoft eyleminin bir kez sayıldığı, yönettiğiniz her teknik eylemin bir kez ve yönettiğiniz teknik olmayan her eylemin grup başına bir kez sayıldığı eylem puanları kullanılarak hesaplanır. Bu mantık, eylemlerin kuruluşunuzda nasıl uygulandığı ve test edildiğinde en doğru muhasebeyi sağlamak için tasarlanmıştır. Bunun genel uyumluluk puanınızın değerlendirme puanlarınızın ortalamasından farklı olduğuna neden olabileceğini fark edebilirsiniz. [Eylemlerin nasıl puanlanmış olduğu](#action-types-and-points) hakkında daha fazla bilgiyi aşağıda bulabilirsiniz.

## <a name="initial-score-based-on-microsoft-365-data-protection-baseline"></a>Microsoft 365 veri koruma temeli temelinde ilk puan
  
Uyumluluk Yöneticisi, Microsoft 365 veri koruma temelini temel alan bir başlangıç puanı verir. Bu temel, veri koruma ve genel veri idaresi için temel düzenlemeleri ve standartları içeren bir dizi denetimdir. Bu temel öncelikle NIST CSF (National Institute of Standards and Technology Cybersecurity Framework) ve ISO (International Organization for Standardization) ile FedRAMP (Federal Risk ve Authorization Management Program) ve GDPR (Avrupa Birliği Genel Veri Koruma Yönetmeliği) öğelerini kullanır.

İlk puanınız, tüm kuruluşlara sağlanan varsayılan Veri Koruma Temeli değerlendirmesine göre hesaplanır. İlk ziyaretinizde Uyumluluk Yöneticisi, Microsoft 365 çözümlerinizden sinyalleri zaten topluyor. Kuruluşunuzun temel veri koruma standartlarına ve düzenlemelerine göre nasıl performans sergilediğini bir bakışta göreceksiniz ve gerçekleştirilecek önerilen iyileştirme eylemlerine göz atacaksınız.

Her kuruluşun belirli gereksinimleri olduğundan, Uyumluluk Yöneticisi riski olabildiğince kapsamlı bir şekilde en aza indirmeye ve azaltmaya yardımcı olmak için değerlendirmeleri ayarlamanıza ve yönetmenize bağlıdır.

## <a name="how-compliance-manager-continuously-assesses-controls"></a>Uyumluluk Yöneticisi denetimleri sürekli olarak nasıl değerlendirir?

Uyumluluk Yöneticisi, Microsoft 365 ortamınızda belirli yapılandırmaların iyileştirme eylemi uygulama gereksinimlerini ne zaman karşıladığını belirlemeye yardımcı olan ayarları otomatik olarak tanımlar. Uyumluluk Yöneticisi, veri yaşam döngüsü yönetimi, bilgi koruması, iletişim uyumluluğu ve iç risk yönetimi dahil olmak üzere dağıtmış olabileceğiniz diğer uyumluluk çözümlerinden gelen sinyalleri algılar ve ayrıca tamamlayıcı iyileştirme eylemlerinin Microsoft Güvenli Puan izlemesinden yararlanır.

Eylem durumunuz, değişiklik yapıldıktan sonraki 24 saat içinde panonuzda güncelleştirilir. Bir denetimi uygulamak için bir öneriyi izledikten sonra, genellikle denetim durumunun ertesi gün güncelleştirildiğini görürsünüz.

Örneğin, Azure AD portalında çok faktörlü kimlik doğrulamasını (MFA) açarsanız, Uyumluluk Yöneticisi ayarı algılar ve denetim erişim çözümü ayrıntılarına yansıtır. Buna karşılık, MFA'yı açmadıysanız, Uyumluluk Yöneticisi bunu gerçekleştirmeniz için önerilen bir eylem olarak işaretler.

[Güvenli Puan ve nasıl çalıştığı](../security/defender/microsoft-secure-score.md) hakkında daha fazla bilgi edinin.
  
## <a name="action-types-and-points"></a>Eylem türleri ve noktaları

Uyumluluk Yöneticisi iki tür eylemi izler:

1. **Geliştirme eylemleriniz**: kuruluşunuzun yönettiği eylemler.
2. **Microsoft eylemleri**: Microsoft'un yönettiği eylemler.

Her iki eylem türü de tamamlandığında toplam puanınıza doğru sayan puanlara sahiptir.

### <a name="technical-and-non-technical-actions"></a>Teknik ve teknik olmayan eylemler

Eylemler, doğası gereği teknik veya teknik olmayan eylemlere göre gruplandırılır. Her eylemin puanlama etkisi türe göre farklılık gösterir.

- **Teknik eylemler** , bir çözümün teknolojisiyle etkileşim kurarak (örneğin, yapılandırmayı değiştirerek) uygulanır. Teknik eylemlere yönelik puanlar, kaç gruba ait olduğuna bakılmaksızın eylem başına bir kez verilir.

- **Teknik olmayan eylemler** kuruluşunuz tarafından yönetilir ve çözüm teknolojisiyle çalışma dışında yöntemlerle uygulanır. İki tür teknik olmayan eylem vardır: **belgeler** ve **operasyonel**. Bu eylemlerin puanları, grup düzeyinde uyumluluk puanınıza uygulanır. Bu, birden çok grupta bir eylem varsa, bir grup içinde her uyguladığınızda eylemin nokta değerini alacağınız anlamına gelir.

**Teknik ve teknik olmayan eylemlerin nasıl puanlandıklarının örneği:**

5 grupta bulunan 3 puanlık bir teknik eyleminiz olduğunu ve aynı 5 grupta bulunan 3 puanlık teknik olmayan bir eyleminiz olduğunu varsayalım.

Teknik eylemi başarıyla uygularsanız, aldığınız toplam puan sayısı 3 olur. Bunun nedeni, eylemi kiracınız için yalnızca bir kez uygulamanız gerektiğidir. Teknik eylemin uygulama ve test durumu, bu eylemin tüm örneklerinde ve ait olduğu her grupta aynı şeyi gösterir.

5 grubun her birinde teknik olmayan eylemi başarıyla uygularsanız, aldığınız toplam puan sayısı 15'tir. Bunun nedeni eylemi her grupta uygulamanız gerektiğidir. Teknik olmayan eylemin uygulama ve test durumu gruplar arasında farklılık gösterir, çünkü eylem grupların her birinde ayrı ayrı uygulanır.

Bu puanlama mantığı, eylemlerin kuruluşunuzda nasıl uygulanıp test edildiğinden en doğru şekilde hesaplanması için tasarlanmıştır.

### <a name="how-score-values-are-determined"></a>Puan değerleri nasıl belirlenir?

Eylemlere zorunlu veya isteğe bağlı olup olmadıklarına ve önleyici, dedektif veya düzeltici olup olmadıklarına bağlı olarak bir puan değeri atanır.

### <a name="mandatory-and-discretionary-actions"></a>Zorunlu ve isteğe bağlı eylemler

- **Zorunlu eylemler** bilerek veya yanlışlıkla atlanamaz. Zorunlu eyleme örnek olarak parola uzunluğu, karmaşıklık ve süre sonu gereksinimlerini ayarlayan merkezi olarak yönetilen bir parola ilkesi gösteriliyor. Kullanıcıların sisteme erişmek için bu gereksinimlere uyması gerekir.
  
- **İsteğe bağlı eylemler** , bir ilkeyi anlamak ve ilkeye bağlı kalmak için kullanıcılara bağlıdır. Örneğin, kullanıcılardan ayrıldıklarında bilgisayarlarını kilitlemelerini gerektiren bir ilke, kullanıcıya bağlı olduğundan isteğe bağlı bir eylemdir.
  
### <a name="preventative-detective-and-corrective-actions"></a>Önleyici, dedektif ve düzeltici eylemler
  
- **Önleyici eylemler** belirli riskleri ele alır. Örneğin, bekleyen bilgileri şifreleme kullanarak korumak saldırılara ve ihlallere karşı önleyici bir eylemdir. Görev ayrımı, çıkar çatışmasını yönetmek ve sahtekarlığa karşı korunmak için önleyici bir eylemdir.
  
- **Dedektif eylemleri** , riski temsil eden ya da izinsiz girişleri veya ihlalleri algılamak için kullanılabilecek düzensiz koşulları veya davranışları belirlemek için sistemleri etkin bir şekilde izler. Örnek olarak sistem erişimi denetimi ve ayrıcalıklı yönetim eylemleri verilebilir. Mevzuat uyumluluğu denetimleri, süreç sorunlarını bulmak için kullanılan bir tür dedektif eylemidir.
  
- **Düzeltici eylemler** , bir güvenlik olayının olumsuz etkilerini en aza düşürmeye, anında etkiyi azaltmak için düzeltici eylem gerçekleştirmeye ve mümkünse zararı tersine çevirmeye çalışır. Gizlilik olayı yanıtı, hasarları sınırlamak ve sistemleri bir ihlal sonrasında işletimsel duruma geri yüklemek için yapılan düzeltici bir eylemdir.
  
Her eylemin Uyumluluk Yöneticisi'nde temsil edilen risk temelinde atanmış bir değeri vardır:

|**Tür**|**Atanan puan**|
|:-----|:-----|
| Önleyici zorunlu | 27 |
| Önleyici isteğe bağlı | 9 |
| Dedektif zorunlu | 3 |
| Dedektif isteğe bağlı | 1 |
| Düzeltici zorunlu | 3 |
| Düzeltici isteğe bağlı | 1 |
  
![Uyumluluk Yöneticisi eylem noktası değerleri.](../media/compliance-score-action-scoring.png "Uyumluluk Yöneticisi eylem noktası değerleri")
