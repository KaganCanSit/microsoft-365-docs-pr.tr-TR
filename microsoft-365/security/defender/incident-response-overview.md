---
title: Yanıtlarla araştırma ve Microsoft 365 Defender
description: Olayları, özellikleriyle ve özellikleriyle Microsoft 365 Defender.
keywords: olaylar, uyarılar, araştırma, çözümleme, yanıt, korelasyon, saldırı, makineler, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, m365, olay yanıtı, siber saldırı
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- m365solution-incidentresponse
- m365solution-scenario
- m365solution-overview
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: c54d2989941d5c91cc2626941af36cf6cdf205ce
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329565"
---
# <a name="investigate-and-respond-with-microsoft-365-defender"></a>Yanıtlarla araştırma ve Microsoft 365 Defender

Aşağıdaki birincil inceleme ve yanıt görevleri şu Microsoft 365 Defender:

- [Olayları yanıtlama](#incident-response)
- [Otomatik düzeltme eylemlerini gözden geçirme ve onaylama](#automated-investigation-and-remediation)
- [Verilerinizde bilinen tehditlere karşı arama](#proactive-search-for-threats-with-advanced-hunting)
- [En son siber saldırıları anlama](#get-ahead-of-emerging-threats-with-threat-analytics)
- [Yardım alın](#collaborate-with-microsoft-experts)

## <a name="incident-response"></a>Olay yanıtı

Microsoft 365 ve uygulamalar, şüpheli veya kötü amaçlı bir etkinlik algılayana kadar uyarılar oluşturabilir. Tek tek uyarılar tamamlanmış veya devam eden bir saldırı hakkında değerli ipuçları sağlar. Öte yandan, saldırılar genellikle cihazlar, kullanıcılar ve posta kutuları gibi farklı varlık türlerine karşı çeşitli teknikler kullanır. Sonuç, kiracınız içinde birden çok varlık için birden çok uyarıdır. Tek tek uyarıları bir saldırı hakkında fikir edinmek için bir araya toplamak zor ve zaman alıcı olduğundan, Microsoft 365 Defender uyarıları ve ilgili bilgilerini otomatik olarak bir olayda bir araya toplar.

Sürekli olarak, olay sırasında analiz ve çözüm için en yüksek öncelikli olayları tanımlamalı ve onları yanıt için hazır hale çıkarabilirsiniz. Bu, şunların bir bileşimidir:

- [En yüksek öncelikli](incident-queue.md) olayları, olay sırasına filtre uygulama ve sıralama yoluyla belirleme önceliklerini belirleme. Bu, eskitme olarak da bilinir.
- [Olayları yönetmek](manage-incidents.md) için başlıklarını değiştirme, bunları bir analiste atama, etiketler ve açıklamalar ekleme ve çözümlense bunları sınıflandırma.

Her olayda, olayı analiz etmek, bunun uyarılarını ve verilerini analiz etmek, tehdidi yok etmek, saldırıdan kurtarmak ve saldırıdan bilgi edinmek için olay müdahale iş akışınızı kullanın. Bu [örnek için](incidents-overview.md#example-incident-response-workflow-for-microsoft-365-defender) bkz. Microsoft 365 Defender.

## <a name="automated-investigation-and-remediation"></a>Otomatik araştırma ve düzeltme

Bu uygulama, Microsoft 365 Defender veya şüpheli bir etkinlik algılandığında güvenlik işlemleri Microsoft 365 Defender portalında bir uyarı alır. Karşı karşıya gelebilir ve hiç bitmeyen tehdit akışı sözlerine göre, güvenlik ekipleri genellikle yüksek hacimli uyarıların zorlukla karşı karşıya olduğu bir durumla karşılaşıyor. Neyse ki Microsoft 365 Defender güvenlik işlemlerinin tehditlere daha etkili ve etkili bir biçimde müdahale edebilirim.

Otomatik bir araştırma tamamlandığında, bir olayın her kanıtı için bir karara varıldı. Karara bağlı olarak düzeltme eylemleri tanımlanır. Bazı durumlarda düzeltme eylemleri otomatik olarak yapılır; Diğer durumlarda, düzeltme eylemleri İşlem Merkezi'nde onay Microsoft 365 Defender bekler. 

Daha [fazla bilgi için bkz. Microsoft 365 Defender](m365d-autoir.md) ve yanıt.

## <a name="proactive-search-for-threats-with-advanced-hunting"></a>Gelişmiş avla tehditlere karşı proaktif arama

Saldırılara meydana gelen saldırılara yanıt vermek yeterli olmaz. Fidye yazılımı gibi genişletilmiş, çok aşamalı saldırılar için, bir saldırının kanıtını önceden aramalı ve tamamlandıktan önce bunu durdurmak için bir eyleme gerek vardır.

Gelişmiş av, 30 günlük ham verileri keşfetmenizi sağlayan Microsoft 365 Defender tabanlı bir tehdit arama aracıdır. Tehdit göstergelerini ve varlıklarını bulmak için ağ'daki olayları önceden inceebilirsiniz. Bu yeni veriye esnek Microsoft 365 Defender hem bilinen hem de potansiyel tehditlere karşı kısıtlanmamış arama sağlar.

Aynı tehdit arama sorgularını kullanarak özel algılama kuralları oluşturabilirsiniz. Bu kurallar ihlal şüphesi olan etkinlikleri, hatalı yapılandırılmış makineleri ve diğer bulguları denetlemek ve sonra bu kurallara yanıt vermek için otomatik olarak çalışır.

Daha [fazla bilgi için bkz. E-Microsoft 365 Defender](advanced-hunting-overview.md) tehdit arama.

## <a name="get-ahead-of-emerging-threats-with-threat-analytics"></a>Tehdit analizi ile yeni ortaya çıkan tehditlerden hemen önce

Tehdit analizi, güvenlik Microsoft 365 Defender ortaya çıkan tehditlerle karşı karşıyayken mümkün olduğunca verimli olması için yardımcı olmak üzere tasarlanmış bir tehdit zeka özelliğidir. Aşağıdakiler hakkında ayrıntılı çözümleme ve bilgi içerir:

- Etkin tehdit tehditlerini ve onların kampanyalarını tehdit ediyor
- Popüler ve yeni saldırı teknikleri
- Kritik güvenlik açıkları
- Yaygın saldırı yüzeyleri
- Yaygın kötü amaçlı yazılım

Tehdit analizleri, her tanımlanan tehdit için kiracınız içindeki ilgili olaylar ve Microsoft 365 varlıklar hakkında da bilgi içerir.

Tanımlanan her tehdit, siber güvenlik algılama ve çözümlemenin ön planda olan Microsoft güvenlik araştırmacısı tarafından yazılan tehdidin kapsamlı bir çözümlemesi olan bir analist raporu içerir. Bu raporlar ayrıca, saldırının her ikisinde de nasıl olduğu hakkında bilgi Microsoft 365 Defender.

Daha fazla bilgi için bkz[. Microsoft 365 Defender](threat-analytics.md).

## <a name="collaborate-with-microsoft-experts"></a>Microsoft uzmanlarıyla işbirliği yapma

Microsoft Tehdit Uzmanları - Hedefli Saldırı Bildirimleri yönetilen bir tehdit arama hizmetidir. Başvurduktan ve kabul edildiktan sonra, Microsoft tehdit uzmanlarından hedefli saldırı bildirimleri alırsınız ve böylelikle ortamınıza yönelik kritik tehditleri kaçırmazsınız. Bu bildirimler, kuruluşun uç noktalarını, e-postalarını ve kimliklerini korumanıza yardımcı olur. Microsoft Tehdit Uzmanları : Talep Üzerine Çalışan Uzmanlar, kuruma yönelik tehditlerle ilgili uzman öneriler amanıza olanak sağlar ve kuruluşun karşılaştığı tehditlere karşı yardım almak için size yardımcı olabilir. Ek abonelik hizmeti olarak kullanılabilir.

Daha fazla bilgi için bkz[. Microsoft Tehdit Uzmanları genel Microsoft 365 bakın](/security/mtp/microsoft-threat-experts.md).
