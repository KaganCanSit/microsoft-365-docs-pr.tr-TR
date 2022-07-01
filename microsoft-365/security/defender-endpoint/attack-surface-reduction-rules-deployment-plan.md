---
title: Saldırı yüzeyini azaltma (ASR) kuralları dağıtım planı
description: Saldırı yüzeyi azaltma (ASR) kuralları dağıtımınızı planlamak için rehberlik sağlar.
keywords: Saldırı yüzeyi azaltma kuralları dağıtımı, ASR dağıtımı, ASR kurallarını etkinleştirme, ASR'yi yapılandırma, konak yetkisiz erişim önleme sistemi, koruma kuralları, açıktan yararlanma önleme kuralları, kötüye kullanıma karşı koruma kuralları, kötüye kullanma kuralları, bulaşma önleme kuralları, Uç Nokta için Microsoft Defender, ASR kurallarını yapılandırma
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
ms.collection:
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 4e538a4e986ad0636c380ec2ba167249221ac3ec
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602502"
---
# <a name="plan-attack-surface-reduction-asr-rules-deployment"></a>Saldırı yüzeyini azaltma (ASR) kuralları dağıtım planı

Saldırı yüzeyi azaltma (ASR) kurallarını test ederken doğru iş birimiyle başlamak önemlidir. Belirli bir iş birimindeki küçük bir grup kişiyle başlamak istersiniz. Belirli bir iş birimi içinde, ASR kuralları hakkında gerçek dünya etkisi sağlayabilecek ve uygulamanızı ayarlamanıza yardımcı olabilecek bazı ASR şampiyonlarını tanımlayabilirsiniz.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-planning-steps.png" alt-text="ASR kuralları planlama adımları" lightbox="images/asr-rules-planning-steps.png":::

## <a name="start-with-the-right-business-unit"></a>Doğru iş birimiyle başlayın

ASR kuralları dağıtımınızı dağıtmak için iş birimini nasıl seçeceğiniz aşağıdakiler gibi faktörlere bağlıdır:

- İş biriminin boyutu
- ASR kural şampiyonlarının kullanılabilirliği  
- Dağıtımı ve kullanımı:
  - Yazılım
  - Paylaşılan klasörler
  - Betiklerin kullanımı
  - Office makroları
  - ASR kurallarından etkilenen diğer varlıklar

İş gereksinimlerinize bağlı olarak, yazılımın, paylaşılan klasörlerin, betiklerin, makroların vb. kapsamlı bir örneklemesini almak için birden çok iş birimi dahil etmeye karar vekleyebilirsiniz. Buna karşılık, ilk ASR kuralları dağıtımınızın kapsamını tek bir iş birimiyle sınırlamaya karar verebilir, ardından ASR kuralları dağıtım işleminin tamamını diğer iş birimlerinizle tek tek yinelemeye karar verebilirsiniz.

## <a name="identify-asr--rules-champions"></a>ASR kuralları şampiyonlarını belirleme

ASR kuralları şampiyonları, kuruluşunuzda ön test ve uygulama aşamalarında ilk ASR kuralları dağıtımınıza yardımcı olacak üyelerdir. Şampiyonlarınız genellikle teknik açıdan daha usta olan ve aralıklı iş akışı kesintileri tarafından raydan çıkarılmayan çalışanlardır. Şampiyonların katılımı, ASR kuralları dağıtımının kuruluşunuza daha geniş kapsamlı bir şekilde genişletilmesi boyunca devam edecektir. ASR kural şampiyonlarınız, ASR kuralları dağıtımının her düzeyini ilk kez deneyimleyecek.

ASR kurallarıyla ilgili iş kesintileri konusunda sizi uyarmak ve ASR kuralları dağıtımıyla ilgili iletişimleri almak için ASR kural şampiyonlarınız için bir geri bildirim ve yanıt kanalı sağlamak önemlidir.

## <a name="get-inventory-of-line-of-business-apps-and-understand-the-business-unit-processes"></a>İş kolu uygulamalarının envanterini alma ve iş birimi süreçlerini anlama

Kuruluşunuz genelinde kullanılan uygulamaları ve iş birimi başına işlemleri tam olarak anlamak, başarılı bir ASR kuralları dağıtımı için kritik öneme sahiptir. Ayrıca, bu uygulamaların kuruluşunuzdaki çeşitli iş birimlerinde nasıl kullanıldığını anlamanız şarttır.
Başlamak için, kuruluşun genelinde kullanım için onaylanan uygulamaların bir envanterini almanız gerekir. Yazılım uygulamalarının envanterini oluşturmanıza yardımcı olması için Microsoft 365 Uygulamaları yönetim merkezi gibi araçları kullanabilirsiniz. Bkz. [Microsoft 365 Uygulamaları yönetim merkezinde envantere genel bakış](/deployoffice/admincenter/inventory).

## <a name="define-reporting-and-response-team-roles-and-responsibilities"></a>Raporlama ve yanıt ekibi rollerini ve sorumluluklarını tanımlama

ASR kurallarının durumunu ve etkinliğini izlemek ve iletmekle sorumlu kişilerin rollerini ve sorumluluklarını açıkça ifade etmek ASR bakımının temel etkinliğidir. Bu nedenle, şunları belirlemek önemlidir:

- Rapor toplamadan sorumlu kişi veya ekip
- Raporların nasıl ve kimlerle paylaşıldığı
- ASR kurallarının neden olduğu yeni tanımlanan tehditler veya istenmeyen engellemeler için yükseltme nasıl giderilir?

Tipik roller ve sorumluluklar şunlardır:

- BT yöneticileri: ASR kurallarını uygulayın, dışlamaları yönetin. Uygulamalar ve süreçler üzerinde farklı iş birimleriyle çalışın. Raporların toplanması ve paydaşlara paylaşılması
- Sertifikalı güvenlik operasyonları merkezi (CSOC) analisti: Tehdidin geçerli olup olmadığını belirlemek için yüksek öncelikli, engellenen süreçlere yatırım yapmaktan sorumludur
- Bilgi güvenliği müdürü (CISO): Kuruluşun genel güvenlik duruşu ve sağlığından sorumludur

## <a name="ring-deployment"></a>Halka dağıtımı

Microsoft, büyük kuruluşlar için ASR kurallarının "halkalar" içinde dağıtılması önerilir. Halkalar, çakışmayan ağaç halkaları gibi dışa doğru yayılan eşmerkezli daireler olarak görsel olarak temsil edilen cihaz gruplarıdır. En içteki halka başarıyla dağıtıldığında, bir sonraki halkayı test aşamasına geçirebilirsiniz. İş birimlerinizin, ASR kuralları şampiyonlarınızın, uygulamalarınızın ve süreçlerinizin kapsamlı bir şekilde değerlendirilmesi halkalarınızı tanımlamak için zorunludur.
Çoğu durumda, kuruluşunuz Windows güncelleştirmelerinin aşamalı dağıtımları için dağıtım halkaları tasarlayacaktır. ASR kurallarını uygulamak için mevcut halka tasarımınızı kullanabilirsiniz.
Bkz. [Windows için dağıtım planı oluşturma](/windows/deployment/update/create-deployment-plan)

## <a name="additional-topics-in-this-deployment-collection"></a>Bu dağıtım koleksiyonundaki ek konular

[Saldırı yüzeyini azaltma (ASR) kuralları dağıtımına genel bakış](attack-surface-reduction-rules-deployment.md)

[Saldırı yüzeyini azaltma (ASR) kuralları testi](attack-surface-reduction-rules-deployment-test.md)

[Saldırı yüzeyini azaltma (ASR) kurallarını etkinleştirme](attack-surface-reduction-rules-deployment-implement.md)

[Saldırı yüzeyini azaltma (ASR) kurallarını kullanıma hazır hale getirme](attack-surface-reduction-rules-deployment-operationalize.md)

[Saldırı yüzeyini azaltma (ASR) kuralları başvurusu](attack-surface-reduction-rules-reference.md)
