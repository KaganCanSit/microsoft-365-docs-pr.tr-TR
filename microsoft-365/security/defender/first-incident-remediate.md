---
title: Adım 2. İlk olayınızı düzeltmek
description: İş yerindeki ilk olayınızı düzeltmeye Microsoft 365 Defender.
keywords: olaylar, uyarılar, araştırma, korelasyon, saldırı, makineler, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, m365, olay yanıtı, siber saldırı
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
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 2837b6009c143ea724d8c13d2548eeeca80e431d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63321327"
---
# <a name="step-2-remediate-your-first-incident"></a>Adım 2. İlk olayınızı düzeltmek

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Microsoft 365 Defender algılama ve çözümleme özellikleri sağladığı gibi, kötü amaçlı yazılımların da içermesi ve kaldırılmasını sağlar. Containment includes steps to reduce the impact of the attack while eradication ensures all traces of saldırgan activity are removed from the network. Microsoft 365 Defender, etkilenen cihazların işletim sistemine ve saldırı türüne bağlı olarak otomatik düzeltme yapmak üzere [](m365d-autoir.md) yapılandırılan çeşitli düzeltme eylemleri sunar.

Microsoft 365 Defender, analistlerin el ile başlatacakları çeşitli düzeltme eylemleri sunar. Eylemler iki kategoriye ayrılır: Cihazlardaki eylemler ve dosyalar üzerinde eylemler. Bazı eylemler tehditi hemen durdurmak için kullanılabilirken diğer eylemler daha ayrıntılı çözümleme yapmak için yardımcı olur.

## <a name="actions-on-devices"></a>Cihazlardaki eylemler

- **Cihazı yalıt** - Bu etkinlik, kötü amaçlı yazılım yayılmasını en aza indirmek için tüm ağ trafiğini (İnternet ve iç) hemen engeller ve analistlerin kötü niyetli bir oyuncu saldırıya devam etmeden analize devam olmasına izin verir. Yalnızca Identity için Microsoft Defender hizmet bulutuna izin verilir ve dolayısıyla Kimlik için Microsoft Defender cihazı izlemeye devam eder. 
- **Uygulama yürütmeyi** kısıtlama - Bir uygulamanın çalışmasına kısıtlamak için, yalnızca dosyaların Microsoft tarafından verilen bir sertifikayla imzalandıklarından çalışmasını sağlayan bir kod bütünlüğü ilkesi uygulanır. Bu kısıtlama yöntemi, güvenliği tehlikeye atılmış cihazları denetimi altına alan ve kötü amaçlı başka etkinlikler gerçekleştiren bir saldırganı önlemeye yardımcı olabilir.
- **Virüsten Koruma taraması** çalıştırma - Microsoft Defender Virüsten Koruma virüsten koruma çözümü olsun ya da değildir, diğer virüsten koruma çözümleriyle birlikte bir tarama çalıştırabilirsiniz. Birincil uç nokta koruma çözümü başka bir virüsten koruma satıcısı ürünü ise, Defender Virüsten Koruma'ı Pasif modunda çalıştırabilirsiniz.
- **Otomatik araştırma başlatma** - Cihazda yeni genel amaçlı otomatik araştırma başlatabilirsiniz. Bir araştırma çalışırken, cihazdan oluşturulan diğer tüm uyarılar, bu araştırma tamamlanana kadar devam eden otomatik bir soruşturmaya eklenir. Buna ek olarak, diğer cihazlarda da aynı tehdit görülürse, bu cihazlar araştırmaya eklenir.
- **Canlı yanıt başlatma** - Canlı yanıt, uzak kabuk bağlantısı kullanarak bir cihaza anında erişim olanağı sağlar. Bu size, gerçek zamanlı olarak tanımlanan tehditleri hemen içermek için ayrıntılı yatırım yapma ve hemen yanıt eylemleri yapma olanağı sağlar. Canlı yanıt; araştırma verilerini toplamaya, betik çalıştırmaya, çözümleme için şüpheli varlıklar göndermeye, tehditleri düzeltmeye ve ortaya çıkan tehditleri önceden ortaya çıkan tehditlere karşı önceden aramana olanak sağlayarak incelemeleri geliştirmek üzere tasarlanmıştır.
- **Soruşturma paketini topla** - Araştırma veya yanıt işleminin bir parçası olarak, bir soruşturma paketini bir cihazdan toplayabilirsiniz. Araştırma paketini toplayarak cihazın geçerli durumunu tanımlayabilir ve saldırgan tarafından kullanılan araç ve teknikleri daha iyi anabilirsiniz. 
- **Bir tehdit uzmanına** danışın (cihazlardaki ve dosyalarda bulunan eylemler) - Güvenliği tehlikeye atılmış olabilecek cihazlar veya cihazlarla ilgili daha fazla bilgi için Microsoft tehdit uzmanına başvurabilirsiniz. Microsoft tehdit uzmanları, zamanında ve doğru bir Microsoft 365 Defender müdahale etmek için doğrudan kendi iş yerlerinden meşgul olabilir. 

## <a name="actions-on-files"></a>Dosyalarda eylemler

- **Dosyayı durdurma ve karantinaya** al - Bu eylem, işlemleri çalıştırmayı durdurmayı, dosyaları dörtte bir olarak çalıştırmayı ve tüm kayıt defteri anahtarları gibi kalıcı verileri silmeyi içerir. Bu eylem, dosyanın son 30 gün Windows 11 Windows 10, sürüm 1703 veya daha sonraki bir sürüme sahip cihazlarda geçerli olur. 
- **Dosyayı engellemek veya dosyaya izin** vermek için göstergeler ekleyin - Kötü amaçlı olabilecek dosyaları veya kötü amaçlı yazılımdan şüpheleniyorsanız yasaklamanız nedeniyle organizasyonda bir saldırının daha fazla yayılmasını önle. Bu işlem, dosyanın kuruluş cihazlarına okunma, yazma veya yürütmesini engellemeye yöneliktir.
- **Dosya indirme veya toplama** – Bu eylem analistlerin kuruluş tarafından daha fazla çözümleme yapmak için parola korumalı bir dosya .zip arşiv dosyasında dosya indirmelerine olanak sağlar.
- **Derin çözümleme** – Bu eylem, dosyayı güvenli, tam araçlı bir bulut ortamında yürütür. Derin çözümleme sonuçları, dosyanın etkinliklerini, gözlemlenen davranışları ve bırakılan dosyalar, kayıt defteri değişiklikleri ve IP adresleriyle iletişim gibi ilişkili yapıları gösterir. 

Olayı algılama [, değerlendirme ve çözümleme'de örneği](first-incident-analyze.md#analyze-your-first-incident) devam ettiren bir analist, şu eylemlerle bu olayı düzeltmek için:

1. Kullanıcı hesabı parolasını hemen sıfırlama
2. Derin analiz tamamlandıktan Microsoft 365 Defender için cihazı yakın bir cihazda yalıtmak
3. Kötü amaçlı dosyanın karantinada olduğundan emin SharePoint
4. Hangi uç noktaların kötü amaçlı yazılımdan etkilendiğini denetleme
5. Sistemleri yeniden oluşturma
6. Diğer kullanıcılara benzer Bulut Uygulamaları için Microsoft Defender uyarılarını denetleme
7. Tor IP adresini engellemek üzere Uç Nokta için Microsoft Defender'da özel bir gösterge oluşturma
8. Aşağıdaki resimde gösterilenler gibi bu tür bir uyarı için Bulut Uygulamaları için Microsoft Defender'da bir yönetim eylemi oluşturun:

   :::image type="content" source="../../media/first-incident-remediate/first-incident-mcas-governance.png" alt-text="Bulut Uygulamaları için Microsoft Defender portalında yönetim eylemleri örneği.":::

Düzeltme eylemlerinin çoğu bu işlemde uygulanabilir ve Microsoft 365 Defender.

## <a name="using-playbooks"></a>Playbooks kullanma

Buna ek olarak, playbooks kullanılarak otomatik düzeltme oluşturulabilir. Şu anda Microsoft'ta[, aşağıdaki senaryolara GitHub](https://github.com/microsoft/Microsoft-Cloud-App-Security/tree/master/Playbooks) kitaplarını sağlayan çalışma kitabı şablonları vardır:

- Kullanıcı doğrulaması isteği yaptıktan sonra hassas dosya paylaşımını kaldırma
- Sık kullanılmayan ülke uyarılarını otomatik öncele
- Hesabı devre dışı bırakmadan önce yönetici eylemi isteği
- Kötü amaçlı gelen kutusu kurallarını devre dışı bırakma

Playbooks, Power Automate ölçütlerin tetiklendiğinde belirli etkinlikleri otomatikleştirmek için özel süreç otomasyon akışları oluşturmak üzere el ile yapılan işlemleri kullanır. Kuruluşlar mevcut şablonlardan veya sıfırdan çalışma kitapları oluşturabilir. 

İşte bir örnek.
 
:::image type="content" source="../../media/first-incident-remediate/first-incident-power-automate.png" alt-text="Özel iş Power Automate otomasyon akışı örneği."::: 
 
Çalışma kitapları, çözümlenen [olaylardan düzeltme eylemleri](first-incident-post.md) oluşturmak için olay sonrası inceleme sırasında da oluşturulabilir. 

## <a name="next-step"></a>Sonraki adım

[![3. Adım: Olayın olay sonrası incelemesini nasıl gerçekleştireceklerini öğrenin.](../../media/first-incident-overview/first-incident-path-step3.png)](first-incident-post.md)

Bir olayın [olay sonrası incelemesini nasıl gerçekleştireceklerini öğrenin](first-incident-post.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Olaylara genel bakış](incidents-overview.md)
- [Olayları araştırma](investigate-incidents.md)
- [Olayları yönetme](manage-incidents.md)
