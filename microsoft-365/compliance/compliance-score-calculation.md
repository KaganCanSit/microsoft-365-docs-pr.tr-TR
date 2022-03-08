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
description: Microsoft Uyumluluk Yöneticisi'nin, risklere yönelik işlemlere dayalı olarak kişiselleştirilmiş bir puanı nasıl hesapta olduğunu an edin ve uyumluluk kalitenizi geliştirin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9c6667ad9be6164639e65e23fb136de1bc196f60
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320039"
---
# <a name="compliance-score-calculation"></a>Uyumluluk puanı hesaplaması

**Bu makalede:** Uyumluluk Yöneticisi'nin, organizasyonunız için uyumluluk puanı hesaplamayı öğrenin. Bu makalede puanınızı nasıl **yorumlayabilirsiniz**, Veri **Koruma** Temeli değerlendirmesini neler içerir, **sürekli** izleme ve farklı eylem türlerinin nasıl yönetiliyor **ve puanlandı**.

> [!IMPORTANT]
> Öneriler Yöneticisi'nin size yardımcı olması, uyumluluk garantisi olarak yorumlanmaz. Mevzuat ortamınız başına müşteri denetimlerinin ne kadar etkili olduğunu değerlendirmeniz ve doğrulamanız size göredir. Bu hizmetler Çevrimiçi Hizmet Koşullarındaki hüküm ve [şartlara bağlıdır](https://go.microsoft.com/fwlink/?linkid=2108910). Güvenlik ve [Microsoft 365 için lisanslama kılavuzuna da bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="how-to-read-your-compliance-score"></a>Uyumluluk puanınızı okuma

Uyumluluk Yöneticisi panosu, genel uyumluluk puanınızı görüntüler. Bu puan, denetimler içinde önerilen geliştirme eylemlerini tamamlamada ilerlemenizi ölçür. Puanınız geçerli uyumluluk sonrası sonrasınızı anlamanıza yardımcı olabilir. Ayrıca, riski azaltma potansiyellerine göre eylemlerin önceliklerini belirlemede size yardımcı olabilir.

Üç düzeyde bir puan değeri atanır:

1. **Geliştirme eylem puanı**: Her eylemin, söz konusu olası risklere bağlı olarak puanınız üzerinde farklı bir etkisi vardır

2. **Denetim puanı**: Bu puan, denetim içinde geliştirme eylemleri tamamlayarak kazanılan puan toplamıdır. Denetim aşağıdaki koşulların her ikisini de karşı olduğunda, bu toplam, tamamen sizin genel uyumluluk puanınıza uygulanır:
    - **Uygulama Durumu** , Uygulanan **veya Alternatif** **Uygulama'ya eşittir** ve
    - **Test Sonucu Geçirilen** **Değere eşittir**.

3. **Değerlendirme puanı**: Bu puan, denetim puanlarının toplamıdır. Eylem puanları kullanılarak hesaplanır. Bir denetimde ne sıklıkta başvuruldu olursa olsun, her Microsoft eylemi ve organizasyonu tarafından yönetilen her geliştirme eylemi bir kez sayılır.

Genel uyumluluk puanı, eylem puanları kullanılarak hesaplanır; burada her Microsoft eylemi bir kez sayılır, yönet her teknik eylem bir kez sayılır ve yönetilmeyen her teknik eylem grup başına bir kez sayılır. Bu mantık, eylemlerin kuruluş içinde nasıl uygulandığını ve test edildiklerinin en doğru muhasebeini sağlamak için tasarlanmıştır. Bunun, genel uyumluluk puanınıza, değerlendirme puanlarının ortalamalarından farklı bir neden olduğunu fark edin. Eylemlerin nasıl [puanlandıkları hakkında daha fazla makale okuyun](#action-types-and-points).

## <a name="initial-score-based-on-microsoft-365-data-protection-baseline"></a>Veri koruma temeli Microsoft 365 temel alınan ilk puan
  
Uyumluluk Yöneticisi size, temel veri koruma Microsoft 365 bir başlangıç puanı verir. Bu taban çizgisi, veri koruma ve genel veri idaresi için temel düzenlemeleri ve standartları içeren bir dizi denetimdir. Bu taban çizgisi öncelikle NIST CSF (Ulusal Standartlar ve Teknoloji Enstitüsü Cybersecurity Framework) ve ISO (Standartlaştırma için Uluslararası Kuruluş) ile FedRAMP (Federal Risk ve Yetkilendirme Yönetim Programı) ve GDPR (Avrupa Birliği Genel Veri Koruma Yönetmeliği) kaynaklarından gelen öğeleri çizmektedir.

İlk puanınız, tüm kuruluşlara sağlanan varsayılan Veri Koruma Temeli değerlendirmesine göre hesaplanır. İlk ziyaretin ardından, Uyumluluk Yöneticisi zaten proje çözümlerinden sinyaller Microsoft 365 bir hizmettir. Kuruluşlarının önemli veri koruma standartları ve yasal düzenlemelere göre nasıl performans gösterirken bir bakışta bakarak gerçekleştirmesi önerilen geliştirme işlemlerine bakabilirsiniz.

Her kuruluşun belirli ihtiyaçları olduğundan, Uyumluluk Yöneticisi riski mümkün olduğunca kapsamlı olarak en aza indirmeye ve en aza indirmeye yardımcı olmak için değerlendirmeleri ayarlamak ve yönetmek için size güvenmektedir.

## <a name="how-compliance-manager-continuously-assesses-controls"></a>Uyumluluk Yöneticisi denetimleri sürekli nasıl değerlendirir

Uyumluluk Yöneticisi, bazı yapılandırmaların geliştirme eylemi uygulama gereksinimlerini ne zaman Microsoft 365 yardımcı olacak, bu ayarları otomatik olarak sizin ortamınıza tanımlar. Uyumluluk Yöneticisi, bilgi yönetimi, bilgi koruma, iletişim uyumluluğu ve insider risk yönetimi dahil olmak üzere, dağıt dağıtılmış diğer uyumluluk çözümlerinden sinyaller algılar ve ayrıca tamamlayıcı geliştirme eylemlerinin Microsoft Güvenli Puanı izlemesinden faydalanr.

Eylem durumunuz, değişikliğin olduğu 24 saat içinde panoda güncelleştirilir. Bir denetim uygulama önerisinde bulunduktan sonra, normalde sonraki gün denetim durumunun güncelleştirilmiş olduğunu da edersiniz.

Örneğin, Azure AD portalında Multi-Factor Authentication'i (MFA) etkinleştirirseniz, Uyumluluk Yöneticisi ayarı algılar ve denetim erişimi çözümü ayrıntılarına yansıttır. Buna karşılık, MFA'yı açmadısanız Uyumluluk Yöneticisi bu işlemi sizin için önerilen bir işlem olarak bayrakla bayrakla işaretleri.

Güvenli Puan ve [bu puanın nasıl çalıştığını öğrenin](../security/defender/microsoft-secure-score.md).
  
## <a name="action-types-and-points"></a>Eylem türleri ve noktaları

Uyumluluk Yöneticisi iki tür eylem izler:

1. **Geliştirme eylemleriniz**: kuruluşun yönett olduğu eylemler.
2. **Microsoft eylemleri**: Microsoft'un yönett olduğu eylemler.

Her iki eylem türü de, tamamlandığında genel puanınıza doğru bir puan içerir.

### <a name="technical-and-non-technical-actions"></a>Teknik ve teknik olmayan eylemler

Eylemler, teknik mi yoksa teknik olmayan eylemler mi yoksa doğada teknik mi yoksa teknik olmayan eylemlere göre grup sağlar. Her eylemin puanlama etkisi türe göre farklılık gösterir.

- **Teknik eylemler** , çözüm teknolojisiyle etkileşim kurarak uygulanır (örneğin, bir yapılandırmayı değiştirme). Teknik eylemlerin noktaları, ne kadar gruba ait olursa olsun, her eylem için bir kez vetir.

- **Teknik olmayan eylemler** organizasyonunız tarafından yönetilir ve çözüm teknolojisiyle çalışma dışında yöntemlerle uygulanır. Teknik olmayan iki tür eylem vardır: **belgeler ve** **işlem**. Bu eylemlerin puanları, grup düzeyinde uyumluluk puanınıza uygulanır. Başka bir ifadeyle, bir eylem birden çok grupta yer alırsa, eylemi bir grup içinde her uygulayan eylemin nokta değerini alırsınız.

**Teknik ve teknik olmayan eylemlerin nasıl puanlandıklarının örneği:**

Diyelim ki, 5 grupta yer alan 3 puanlık bir teknik eyleme sahipsiniz ve aynı 5 grupta 3 puan değerinde teknik olmayan bir eyleme sahipsiniz.

Teknik eylemi başarıyla tamamlarsanız, toplam puan sayısı 3'tir. Bunun nedeni, eylemi kiracınız için tek bir kez uygulamanız gerektir. Teknik eylemin uygulama ve test durumu, bu eylemin ait olduğu her grupta tüm örneklerde aynı şekilde gösterir.

Her 5 grubun her birsinde teknik olmayan bir eylemi başarıyla tamamladıysanız, toplam puan sayısı 15'tir. Bunun nedeni, eylemi her grupta uygulamalı gerektir. Teknik olmayan eylemin uygulama ve test durumu grupları arasında farklılık gösterir, çünkü eylem grupların her biri içinde ayrı ayrı uygulanır.

Bu puanlama mantığı, eylemlerin organizasyonda nasıl uygulandığını ve test edildiklerinin en doğru muhasebeini sağlamak için tasarlanmıştır.

### <a name="how-score-values-are-determined"></a>Puan değerleri nasıl belirlenir

Eylemlere, zorunlu veya imtiyazlı olup olmadığı ve bunların engelli, tedbirli veya düzeltici olup olmadığı bağlı olarak bir puan değeri atanır.

### <a name="mandatory-and-discretionary-actions"></a>Zorunlu ve irde bağlı eylemler

- **Zorunlu eylemler** bilerek veya yanlışlıkla atlanır. Zorunlu eylem örneği, parola uzunluğu, karmaşıklığı ve süre sonu gereksinimlerini ayaran merkezi olarak yönetilen bir parola ilkesidir. Kullanıcıların sisteme erişmek için bu gereksinimleri izlemesi gerekir.
  
- **İsteğe bağlı eylemler** , kullanıcıların bir ilkeyi anması ve ilkeye bağlı kalmasını sağlar. Örneğin, kullanıcıların bilgisayarlarından ayrıldıklarında bilgisayarlarını kilitlemelerini gerektiren bir ilke, kullanıcıya dayandırılacağı için i İsteğe bağlı bir eylemdir.
  
### <a name="preventative-detective-and-corrective-actions"></a>Preventative, bire bir, bire bir düzeltme eylemleri
  
- **Belirli risklere yönelik** engelleme eylemleri. Örneğin, şifreleme kullanarak yerinde bilgileri korumak saldırılara ve ihlallere karşı önlem almaktır. Görevlerin ayrımı, faiz çakışmasını ve dolandırıcılığa karşı korumayı yönetmek için önlem önlemdir.
  
- **Eylem eylemleri** , riski temsil eden ya da izinsizleri veya ihlalleri tespit etmek için gerektirilenleri belirlemek için sistemleri etkin bir şekilde takip eder. Örnek olarak sistem erişimi denetimi ve ayrıcalıklı yönetim eylemleri örnek olarak verilmiştir. Mevzuat uyumluluğu denetimleri, süreç sorunlarını bulmak için kullanılmaktadır.
  
- **Düzeltme eylemleri,** güvenlik olaylarının olumsuz etkilerini minimum düzeyde tutmaya, anında efekti azaltmak ve mümkünse hasarları tersine çevirmek için düzeltme eylemi yapmaya çalışabilirsiniz. Gizlilik olayı yanıtı, bir ihlal sonrasında zararları sınırlandıran ve sistemleri faaliyet durumuna geri yüklemek için yapılan bir düzeltici eylemdir.
  
Her eylemin Uyumluluk Yöneticisi'nde temsil ettiği risklere göre atanmış bir değeri vardır:

|**Tür**|**Atanan puan**|
|:-----|:-----|
| Zorunlu engelleme | 27 |
| Preventative discretionary | 9 |
| Erkek için zorunlu | 3 |
| İsteğe bağlı olarak | 1 |
| Düzeltme zorunlu | 3 |
| Düzeltici imtiyazlı | 1 |
  
![Uyumluluk Yöneticisi eylem noktası değerleri.](../media/compliance-score-action-scoring.png "Uyumluluk Yöneticisi eylem noktası değerleri")