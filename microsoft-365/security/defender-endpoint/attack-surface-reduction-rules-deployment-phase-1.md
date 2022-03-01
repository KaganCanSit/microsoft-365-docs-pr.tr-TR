---
title: ASR kuralları dağıtım aşaması 1 - plan
description: Saldırı yüzeyini azaltma kuralları dağıtımınızı planlamaya yönelik kılavuz sağlar.
keywords: Saldırı yüzeyini azaltma kuralları dağıtımı, ASR dağıtımı, asr kurallarını etkinleştirme, ASR'yi yapılandırma, izinsiz giriş engelleme sistemi, koruma kuralları, istismardan koruma kuralları, istismardan koruma kuralları, bulaşma önleme kuralları, Uç nokta için Microsoft Defender, ASR kurallarını yapılandırma
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection: m365solution-scenario
ms.date: 1/18/2022
ms.openlocfilehash: ecd582f99dd0dfa9df51ce50651904144dcc8ff8
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63010165"
---
# <a name="asr-rules-deployment-phase-1-plan"></a>ASR kuralları dağıtım aşaması 1: plan

ASR kurallarını sınamak için başlayarak, doğru iş birimiyle başlama gerekir. Belirli bir iş birimine bağlı küçük bir grup insanla başlamak istiyor oluruz. Belirli bir iş birimi içinde, ASR kuralları üzerinde gerçek etki sağlayacak ve uygulamanızı ayarlamanıza yardımcı olacak bazı ASR şampiyonlarını tanımlayabilirsiniz.

> [!div class="mx-imgBorder"]
> ![ASR kuralları planlama adımları](images/asr-rules-planning-steps.png)

## <a name="start-with-the-right-business-unit"></a>Doğru iş birimiyle çalışmaya başlama

ASR kuralları dağıtımı için iş birimini nasıl seçki, aşağıdaki gibi faktörlere bağlıdır:

- İş biriminin boyutu
- ASR kuralları şampiyonlarının kullanılabilirliği  
- Dağılımı ve kullanımı:
  - Yazılım
  - Paylaşılan klasörler
  - Betiklerin kullanımı
  - Office oluşturma
  - ASR kuralları tarafından etkilenen diğer varlıklar

İş gereksinimlerinize bağlı olarak, çeşitli yazılım, paylaşılan klasörler, betikler, makrolar gibi çeşitli özellikler elde etmek için birden çok iş birimini içermeye karar veabilirsiniz. Buna karşılık, ilk ASR kurallarının kapsamını tek bir iş birimiyle sınırlamaya karar ve ardından ASR kuralları uygulama işleminin tamamını diğer iş birimlerinize bire bir yinelersiniz.

## <a name="identify-asr--rules-champions"></a>ASR kuralları şampiyonlarını belirleme

ASR kuralları destekçileri, ilk test ve uygulama aşamasında ilk ASR kurallarının uygulanmasında size yardımcı olacak organizasyon üyeleridir. Şampiyonlarımız normalde daha teknik açıdan daha teknik olan ve aralıklı iş akışı kesintileri nedeniyle rayından çık çalışmayan çalışanlardandır. Şampiyonların katılımı, asr kurallarının organizasyonunıza dağıtımının daha geniş bir genişletilmesi boyunca devam edecek. ASR kurallarının her düzeyinde birinci olarak ASR kuralları birinci olur.

ASR kuralları destekçileri için, ASR kurallarıyla ilgili çalışma kesintileri hakkında sizi uyaran ve ASR kurallarına uygun iletişimleri alan bir geri bildirim ve yanıt kanalı sağlamak önemlidir.

## <a name="get-inventory-of-line-of-business-apps-and-understand-the-business-unit-processes"></a>İş hattı uygulamalarının envanterini edinin ve iş birimi işlemlerini anlama

Organizasyonu genelinde kullanılan uygulamaları ve iş birimi başına işlemleri tam olarak anlamak, başarılı bir ASR kuralları dağıtımı için çok önemlidir. Buna ek olarak, bu uygulamaların kuruluş içindeki çeşitli iş birimleri içinde nasıl kullanıldıklarını anlamanız da gerekir.
İlk olarak, kuruluş genelinde kullanım onayı alan uygulamaların envanterini elde edinebilirsiniz. Stok yazılım uygulamalarınıza yardımcı olmak Microsoft 365 Uygulamaları Yönetim Merkezi gibi araçları kullanabilirsiniz. Bkz. [Yönetim merkezinde stok Microsoft 365 Uygulamaları genel bakış](/deployoffice/admincenter/inventory).

## <a name="define-reporting-and-response-team--roles-and-responsibilities"></a>Ekip rollerini ve sorumluluklarını raporlama ve yanıtlama

ASR kurallarının durumunu ve etkinliğini izlemek ve bunlardan sorumlu olan kişilerin rollerini ve sorumluluklarını açıkça ortaya ortaya açıklaması, ASR bakımının temel etkinliklerindendir. Bu nedenle, şunları belirlemek önemlidir:

- Rapor toplamakla sorumlu kişi veya ekip
- Raporların nasıl ve kimlerle paylaşılıyor
- ASR kuralları tarafından neden olan yeni tanımlanan tehditlere veya istenmeyen engellemelere yönelik yükseltme nasıl ele alınır

Genel roller ve sorumluluklar şunlardır:

- IT yöneticileri: ASR kuralları uygulama, dışlamaları yönetme. Uygulamalar ve süreçlerde farklı iş birimleriyle çalışabilirsiniz. Proje katılımcıları için raporları bir araya getirerek paylaşma
- Sertifikalı güvenlik işlemleri merkezi (CSOC) analisti: Tehditnin geçerli olup olmadığını belirlemek için yüksek öncelikli, engellenen süreçler yatırım yapmakla sorumlu
- Baş bilgi güvenliği görevlisi (CISO): Kuruluşun genel güvenlik sorumlusundan ve sağlığından sorumlu

## <a name="ring-deployment"></a>Halka dağıtımı

Büyük kuruluşlar için Microsoft, ASR kurallarını "halkalar" içinde dağıtmayı önermektedir. Halkalar, örtüşmeyen ağaç halkaları gibi dışarı doğru yayılan, görsel olarak kesişen matris daireleri olarak temsil edilen cihaz gruplarıdır. En içteki halka başarıyla dağıtıldığında, bir sonraki halkayı test aşamasına geçsiniz. İş birimlerinizin kapsamlı değerlendirmesi, ASR kuralları şampiyonları, uygulamaları ve süreçlerinizi tanımlamanız gerekir.
Çoğu durumda, kuruluş bu güncelleştirmelerin aşamalı dağıtımları için dağıtım halkaları Windows tasarlanmıştır. ASR kurallarını uygulamak için var olan halka tasarımınızı kullanabilirsiniz.
Bkz. [Dağıtım planı oluşturma Windows](/windows/deployment/update/create-deployment-plan)

## <a name="additional-topics-in-this-deployment-collection"></a>Bu dağıtım koleksiyonunda yer alan ek konular

[ASR kuralları dağıtımına genel bakış](attack-surface-reduction-rules-deployment.md)

[Aşama 2: Test](attack-surface-reduction-rules-deployment-phase-2.md)

[Aşama 3: Uygulama](attack-surface-reduction-rules-deployment-phase-3.md)

[Aşama 4: İşlemsellik](attack-surface-reduction-rules-deployment-phase-4.md)
