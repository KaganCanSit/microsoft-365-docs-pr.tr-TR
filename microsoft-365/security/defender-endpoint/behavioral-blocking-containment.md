---
title: Davranışsal engelleme ve engelleme
description: Uç nokta için Microsoft Defender'da davranış engelleme ve engelleme özellikleri hakkında bilgi
keywords: Uç Nokta için Microsoft Defender, EDR modunda kapalı, pasif modu engelleme
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
- admindeeplinkDEFENDER
ms.collection: m365-security-compliance
ms.technology: mde
ms.openlocfilehash: bab766fd69b9227f10ba897040faff79e65b1722
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325789"
---
# <a name="behavioral-blocking-and-containment"></a>Davranışsal engelleme ve engelleme

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>Genel bakış

Günümüzde tehdit ortamı dosyasız kötü amaçlı yazılımlar tarafından [](/windows/security/threat-protection/intelligence/fileless-threats) aşırı taşmaktadır ve topraklarda yer alan ve geleneksel çözümlere göre daha hızlı sessize alan çok polimorphic tehditler ve tehditlere uyan insan tarafından işletilen saldırılar tehditlere uyum sağlar. Geleneksel güvenlik çözümleri bu tür saldırılara engel olmak için yeterli değildir; yapay zeka (AI) ve cihaz öğrenme (ML) ile davranış engelleme ve dahil dahil, Uç Nokta için Defender ile birlikte dahil edilen yapay zekaya ve cihaz öğrenmeye (ML) [sahip olmak gerekir](/windows/security).

Davranışsal engelleme ve engelleme özellikleri, tehdit yürütmeye başlamış olsalar bile, davranışlarına ve işlem ağaçlarına dayalı olarak tehditleri belirlemeye ve durdurmaya yardımcı olabilir. Uç nokta bileşenleri ve özellikleri için yeni nesil koruma, EDR ve Defender, davranış engelleme ve içerirken birlikte çalışır.

:::image type="content" source="images/mdatp-next-gen-EDR-behavblockcontain.png" alt-text="Davranışsal engelleme ve engelleme.":::

Davranışsal engelleme ve engelleme özellikleri, birden çok bileşenle ve Uç Nokta için Defender'ın özellikleriyle birlikte çalışır ve saldırının ilerlemesini önler.

- [Yeni nesil koruma](microsoft-defender-antivirus-in-windows-10.md) (bu korumalar Microsoft Defender Virüsten Koruma) davranışları çözümlayarak tehditleri algılayarak ve çalışmaya başlayan tehditleri durdurabilir.

- [Uç nokta algılama ve yanıt](overview-endpoint-detection-response.md) (EDR), ağ, aygıtlar ve çekirdek davranışı genelinde güvenlik sinyalleri alır. Tehdit algılandığında, uyarılar oluşturulur. Aynı türe sahip birden çok uyarı olaylarda bir araya toplanmış ve bu da güvenlik işlemleri ekibimizin incelemelerini ve yanıtlamalarını kolaylaştırır.

- [Uç nokta için Defender](overview-endpoint-detection-response.md); kimlikler, e-posta, veriler ve uygulamalar genelinde optiklerin yanı sıra, uç nokta ve çekirdek davranışı sinyallerinin yanı sıra EDR. Microsoft 365 Defender, Uç [Nokta](../defender/microsoft-365-defender.md) işlemleri için Defender'ın bir bileşeni ve bu sinyalleri birbiriyle bağlantılı yapıyor, algılama uyarılarını yükselter ve olaylarda ilgili uyarıları bağlar.

Bu özellikler sayesinde, çalışmaya başlamaları bile daha fazla tehdit önlenebilir veya engellenebilir. Şüpheli davranış algılandığında, tehdit her algılandığında, uyarılar oluşturulur ve tehditlere karşı tehditler durdurulur.

Aşağıdaki resimde davranış engelleme ve engelleme özellikleri tarafından tetiklenen bir uyarı örneği yer almaktadır:

:::image type="content" alt-text="Davranış engelleme ve engelleme yoluyla uyarı örneği." source="images/blocked-behav-alert.png" lightbox="images/blocked-behav-alert.png":::

## <a name="components-of-behavioral-blocking-and-containment"></a>Davranış engelleme ve içeren bileşenleri

- **İstemci için ilke odaklı saldırı [yüzeyini azaltma kuralları](attack-surface-reduction.md)** Saldırı yüzeyini azaltma kurallarınıza göre önceden tanımlanmış yaygın saldırı davranışları yürütülmektedir. Bu tür davranışlar yürütmeye çalışırken, bu davranışlarda bilgi <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> olarak görülebilirler. Saldırı yüzeyini azaltma kuralları varsayılan olarak etkin değildir; portalda ilkelerinizi [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender).

- **[İstemci davranışı engelleme](client-behavioral-blocking.md)** Uç noktalara yönelik tehditler makine öğrenimi yoluyla algılanır ve sonra otomatik olarak engellenir ve düzeltilir. (İstemci davranışı engelleme varsayılan olarak etkindir.)

- **[Geri bildirim döngüsü engelleme](feedback-loop-blocking.md)** (hızlı koruma olarak da adlandırılır) Tehdit algılamaları davranışsal zeka aracılığıyla gözlemlenir. Tehditler durdurulur ve diğer uç noktaların üzerinde çalıştırılır. (Geri bildirim döngüsü engelleme varsayılan olarak etkindir.)

- **[Engelleme modunda uç nokta algılama EDR yanıt (EDR)](edr-in-block-mode.md)** İhlal sonrası koruma ile gözlemlenen kötü amaçlı yapılar veya davranışlar engellenir ve uygulanır. EDR modundayken e-Microsoft Defender Virüsten Koruma, birincil virüsten koruma çözümü değilse bile çalışır. (EDR modundayken varsayılan olarak etkinleştirilmez; varsayılan olarak Microsoft 365 Defender.)

Microsoft tehdit koruması özelliklerini ve özelliklerini geliştirmeye devam ederken davranış engelleme ve engelleme alanında daha fazla şey olmasını bekler. Planla ilgili ve şimdi nelerin planlandığına bakın, yol [haritası Microsoft 365 ziyaret edin](https://www.microsoft.com/microsoft-365/roadmap).

## <a name="examples-of-behavioral-blocking-and-containment-in-action"></a>Davranış engelleme ve eyleme müdahale örnekleri

Davranışsal engelleme ve engelleme özellikleri, aşağıdakiler gibi tekniklere engellenmiş olur:

- LSASS'dan kimlik bilgileri dökümü
- Çapraz işlem ekleme
- İşlem boş
- Kullanıcı Hesabı Denetimi atlama
- Virüsten koruma yazılımıyla oynama (devre dışı bırakma veya kötü amaçlı yazılımı dışlama olarak ekleme gibi)
- Yüklerini indirmek için Komut ve Denetim (C&C) ile bağlantı kurma
- Para madenciliği
- Önyükleme kaydı değişikliği
- Karma saldırılarını geç
- Kök sertifikanın yüklenmesi
- Çeşitli güvenlik açıkları için exploitation attempt

Aşağıda, davranışsal engelleme ve önlemi engellemeye örnek olarak iki gerçek yaşam örneği verilmiştir.

### <a name="example-1-credential-theft-attack-against-100-organizations"></a>Örnek 1: 100 kuruluşa yönelik kimlik bilgileri hırsızlığı saldırısı

Bu makale de açıklanmıştır [: AI](https://www.microsoft.com/security/blog/2019/10/08/in-hot-pursuit-of-elusive-threats-ai-driven-behavior-based-blocking-stops-attacks-in-their-tracks) tabanlı davranış tabanlı engelleme saldırılarını durdurarak saldırılara son verdi. Dünya'daki 100 kuruluşa yönelik kimlik bilgileri hırsızlığı saldırısı, davranış engelleme ve engelleme özellikleri tarafından durduruldu. Hedefli kuruluşlara, bir kimlik avı belgesi içeren kimlik avı e-posta iletileri gönderildi. Bir alıcı eki açtısa, ilgili uzak belge kullanıcının cihazında kod yürütüp Kimlik bilgilerini çaldıran, çalınmış verileri çaldıran ve komut ve denetim sunucusundan başka yönergeler için bekleyen Lokibot kötü amaçlı yazılımını yükleyemedi.

Uç nokta için Defender'daki davranış tabanlı cihaz öğrenme modelleri, saldırı zincirinde iki noktada saldırgan tekniklerini durdurdu:

- İlk koruma katmanı, exploit davranışını algıladı. Buluttaki cihaz öğrenme sınıflayıcıları tehdidi doğru bir şekilde tanımlandı ve ardından istemci cihazdan saldırıyı engellemesini hemen istedi.
- Saldırının ilk katmanı geçmiş, boş işlem algılandı, bu işlemi durdurmanıza ve ilgili dosyaları (Lokibot gibi) kaldıran ikinci koruma katmanı.

Saldırı algılandığında ve durdurulurken " ilk erişim uyarısı" gibi uyarılar tetiklendi ve [Microsoft 365 Defender portalda görüldü](/microsoft-365/security/defender/microsoft-365-defender).

:::image type="content" source="images/behavblockcontain-initialaccessalert.png" alt-text="Portalda ilk Microsoft 365 Defender uyarısı.":::

Bu örnekte, buluttaki davranış tabanlı cihaz öğrenme modellerinin çalışmaya başladıktan sonra bile saldırılara karşı yeni koruma katmanlarını nasıl ekleyeceği açıklandı.

### <a name="example-2-ntlm-relay---juicy-potato-malware-variant"></a>Örnek 2: NTLM geçişi - Kötü amaçlı Patates kötü amaçlı yazılım değişken

Son blog gönderisinde de açıklandığı gibi Davranışsal engelleme ve engelleme: Optikleri korumaya dönüştürme [Ocak](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection) 2020'de, Uç Nokta için Defender, kuruluşta bir cihazda ayrıcalık yükseltme etkinliği algıladı. "NTLM geçişi kullanılarak olası ayrıcalık yükseltmesi" adlı bir uyarı tetiklenir.

:::image type="content" alt-text="Edinen Patates kötü amaçlı yazılımı için NTLM uyarısı." source="images/NTLMalertjuicypotato.png" lightbox="images/NTLMalertjuicypotato.png":::

Tehdit kötü amaçlı yazılım olduğu ortaya çıktı; bu, saldırganlar tarafından bir cihazda ayrıcalık yükseltmesi elde etmek için kullanılan Veli Patates adlı, kötümser bir korsan aracının önceden görülen olmayan yeni bir çeşitlecidir.

Uyarının tetiklendiğinden dakikalar sonra dosya çözümlendi ve kötü amaçlı olarak onaylandı. Aşağıdaki resimde gösterildiği gibi, işlemi durduruldu ve engellendi:

:::image type="content" alt-text="Yapı engellendi." source="images/Artifactblockedjuicypotato.png" lightbox="images/Artifactblockedjuicypotato.png":::

Yapı engellendikten birkaç dakika sonra, aynı dosyanın birden çok örneği aynı cihazda engellenmiş ve bu da cihaza daha fazla saldırgan veya başka kötü amaçlı yazılım dağıtmasını önler.

Bu örnekte, davranış engelleme ve engelleme özellikleriyle, tehdit algılandığında, engellenmiş ve otomatik olarak engellenmiş olarak gösterir.

## <a name="next-steps"></a>Sonraki adımlar

- [Uç Nokta için Defender hakkında daha fazla bilgi](overview-endpoint-detection-response.md)

- [Saldırı yüzeyini azaltma kurallarınızı yapılandırma](attack-surface-reduction.md)

- [EDR modunda etkinleştirme](edr-in-block-mode.md)

- [Son küresel tehdit etkinliklerine bakın](https://www.microsoft.com/wdsi/threats)

- [Nasıl olduğunu genel Microsoft 365 Defender](../defender/microsoft-365-defender.md)
