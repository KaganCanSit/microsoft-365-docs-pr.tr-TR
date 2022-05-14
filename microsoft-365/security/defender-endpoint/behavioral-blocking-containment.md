---
title: Davranışsal engelleme ve kapsama
description: davranış engelleme ve kapsama özellikleri hakkında bilgi edinmek için Uç Nokta için Microsoft Defender
keywords: Uç Nokta için Microsoft Defender, blok modunda EDR, pasif mod engelleme
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
ms.openlocfilehash: f6544a14891a98523d202c19634d0e70a3e839e2
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416804"
---
# <a name="behavioral-blocking-and-containment"></a>Davranışsal engelleme ve kapsama

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

> Uç Nokta için Defender'ı deneyimlemek mi istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>Genel bakış

Günümüzün tehdit ortamı [, dosyasız kötü amaçlı yazılımlarla](/windows/security/threat-protection/intelligence/fileless-threats) ve karada yaşayan, geleneksel çözümlerin ayak uyduramadan daha hızlı mutasyona uğrayan yüksek oranda polimorfik tehditler ve saldırganların güvenliği aşılmış cihazlarda bulduklarına uyum sağlayan insan tarafından çalıştırılan saldırılar tarafından gerçekleştirilir. Geleneksel güvenlik çözümleri bu tür saldırıları durdurmak için yeterli değildir; [Uç Nokta için Defender'a](/windows/security) dahil edilen davranış engelleme ve kapsama gibi yapay zeka (AI) ve cihaz öğrenmesi (ML) destekli özelliklere ihtiyacınız vardır.

Davranış engelleme ve kapsama özellikleri, tehdit yürütmeye başladığında bile davranışlarına ve işlem ağaçlarına bağlı olarak tehditleri tanımlamaya ve durdurmaya yardımcı olabilir. Yeni nesil koruma, EDR ve Uç Nokta için Defender bileşenleri ve özellikleri davranış engelleme ve kapsama özelliklerinde birlikte çalışır.

:::image type="content" source="images/mdatp-next-gen-EDR-behavblockcontain.png" alt-text="Microsoft Defender ATP portalındaki Davranış engelleme ve kapsama" lightbox="images/mdatp-next-gen-EDR-behavblockcontain.png":::

Davranış engelleme ve kapsama özellikleri, saldırıları hemen durdurmak ve saldırıların ilerlemesini önlemek için Uç Nokta için Defender'ın birden çok bileşeni ve özelliğiyle çalışır.

- [Yeni nesil koruma](microsoft-defender-antivirus-in-windows-10.md) (Microsoft Defender Virüsten Koruma içerir) davranışları analiz ederek tehditleri algılayabilir ve çalışmaya başlayan tehditleri durdurabilir.

- [Uç nokta algılama ve yanıt](overview-endpoint-detection-response.md) (EDR), ağınız, cihazlarınız ve çekirdek davranışınız genelinde güvenlik sinyalleri alır. Tehditler algılandıktan sonra uyarılar oluşturulur. Aynı türdeki birden çok uyarı olaylar halinde toplanır ve bu da güvenlik operasyonları ekibinizin araştırmasını ve yanıtlamasını kolaylaştırır.

- [Uç Nokta için Defender](overview-endpoint-detection-response.md), EDR aracılığıyla alınan ağ, uç nokta ve çekirdek davranışı sinyallerine ek olarak kimlikler, e-posta, veriler ve uygulamalar arasında çok çeşitli optiklere sahiptir. [Microsoft 365 Defender](../defender/microsoft-365-defender.md) bileşeni olan Uç Nokta için Defender bu sinyalleri işler ve ilişkilendirir, algılama uyarıları oluşturur ve olaylardaki ilgili uyarıları bağlar.

Bu özelliklerle, çalışmaya başlasalar bile daha fazla tehdit önlenebilir veya engellenebilir. Şüpheli davranış algılandığında, tehdit kapsanıyor, uyarılar oluşturuluyor ve tehditler kendi izlerinde durdurulur.

Aşağıdaki görüntüde davranış engelleme ve kapsama özellikleri tarafından tetiklenen bir uyarı örneği gösterilmektedir:

:::image type="content" source="images/blocked-behav-alert.png" alt-text="Davranış engelleme ve kapsama yoluyla uyarı içeren Uyarılar sayfası" lightbox="images/blocked-behav-alert.png":::

## <a name="components-of-behavioral-blocking-and-containment"></a>Davranış engelleme ve kapsama bileşenleri

- **İstemci üzerinde, ilke temelli [saldırı yüzeyi azaltma kuralları](attack-surface-reduction.md)** Saldırı yüzeyi azaltma kurallarınıza göre önceden tanımlanmış yaygın saldırı davranışlarının yürütülmesi engellenir. Bu tür davranışlar yürütülmeye çalışıldığında, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> bilgilendirici uyarılar olarak görülebilir. Saldırı yüzeyi azaltma kuralları varsayılan olarak etkin değildir; Microsoft 365 Defender [portalında](/microsoft-365/security/defender/microsoft-365-defender) ilkelerinizi yapılandırabilirsiniz.

- **[İstemci davranış engellemesi](client-behavioral-blocking.md)** Uç noktalardaki tehditler makine öğrenmesi aracılığıyla algılanıp engellenir ve otomatik olarak düzeltilir. (İstemci davranış engellemesi varsayılan olarak etkindir.)

- **[Geri bildirim döngüsü engelleme](feedback-loop-blocking.md)** (hızlı koruma olarak da adlandırılır) Tehdit algılamaları davranış zekası aracılığıyla gözlemlenir. Tehditler durdurulur ve diğer uç noktalarda çalıştırılması engellenir. (Geri bildirim döngüsü engelleme varsayılan olarak etkindir.)

- **[Blok modunda uç nokta algılama ve yanıt (EDR)](edr-in-block-mode.md)** İhlal sonrası koruma aracılığıyla gözlemlenen kötü amaçlı yapıtlar veya davranışlar engellenir ve kapsanmaktadır. Blok modundaki EDR, birincil virüsten koruma çözümü Microsoft Defender Virüsten Koruma olmasa bile çalışır. (Blok modunda EDR varsayılan olarak etkin değildir; Microsoft 365 Defender'da açarsınız.)

Microsoft tehdit koruma özelliklerini ve özelliklerini geliştirmeye devam ettiğinden davranış engelleme ve kapsama alanında daha fazlasının gelmesini bekleyin. Planlanan ve kullanıma sunulanları görmek için [Microsoft 365 yol haritasını](https://www.microsoft.com/microsoft-365/roadmap) ziyaret edin.

## <a name="examples-of-behavioral-blocking-and-containment-in-action"></a>Davranış engelleme ve kapsamanın eyleme geçme örnekleri

Davranış engelleme ve kapsama özellikleri aşağıdaki gibi saldırgan tekniklerini engelledi:

- LSASS'den kimlik bilgisi dökümü
- İşlemler arası ekleme
- İşlem içi boşlama
- Kullanıcı Hesabı Denetimi atlama
- Virüsten koruma ile oynama (devre dışı bırakma veya kötü amaçlı yazılımı dışlama olarak ekleme gibi)
- Yükleri indirmek için Komut ve Denetim 'e (C&C) başvurma
- Madeni para madenciliği
- Önyükleme kaydı değişikliği
- Karmayı geçirme saldırıları
- Kök sertifika yükleme
- Çeşitli güvenlik açıkları için yararlanma girişimi

Davranış engelleme ve kapsamanın gerçek hayattaki iki örneği aşağıda verilmiştir.

### <a name="example-1-credential-theft-attack-against-100-organizations"></a>Örnek 1: 100 kuruluşa yönelik kimlik bilgisi hırsızlığı saldırısı

Zor tehditlerin sık takip edilmesinde açıklandığı gibi [: Yapay zeka temelli davranış tabanlı engelleme, saldırıları kendi izlerinde durdurur](https://www.microsoft.com/security/blog/2019/10/08/in-hot-pursuit-of-elusive-threats-ai-driven-behavior-based-blocking-stops-attacks-in-their-tracks), davranış engelleme ve engelleme özellikleriyle dünyanın dört bir yanındaki 100 kuruluşa yönelik kimlik bilgisi hırsızlığı saldırısı durduruldu. Hedeflenen kuruluşlara yem belgesi içeren zıpkınla kimlik avı e-posta iletileri gönderildi. Bir alıcı eki açtıysa, ilgili bir uzak belge kullanıcının cihazında kod yürütebildi ve kimlik bilgilerini çalan, çalınan verileri silen ve bir komut ve denetim sunucusundan daha fazla yönerge bekleyen Lokibot kötü amaçlı yazılımını yükleyebildi.

Uç Nokta için Defender'daki davranış tabanlı cihaz öğrenmesi modelleri, saldırı zincirinin iki noktasında saldırganın tekniklerini yakaladı ve durdurdu:

- İlk koruma katmanı, yararlanma davranışını algılamıştı. Buluttaki cihaz öğrenmesi sınıflandırıcıları tehdidi doğru bir şekilde tanımladı ve istemci cihaza saldırıyı engellemesi için hemen talimat verdi.
- Saldırının ilk katmanı geçtiği, işlem boşlama algıladığı, bu işlemi durdurduğu ve karşılık gelen dosyaları (Lokibot gibi) kaldırdığı durumları durdurmaya yardımcı olan ikinci koruma katmanı.

Saldırı algılanıp durdurulurken, "ilk erişim uyarısı" gibi uyarılar tetiklendi ve [Microsoft 365 Defender portalında](/microsoft-365/security/defender/microsoft-365-defender) göründü.

:::image type="content" source="images/behavblockcontain-initialaccessalert.png" alt-text="Microsoft 365 Defender portalında ilk erişim uyarısı" lightbox="images/behavblockcontain-initialaccessalert.png":::

Bu örnekte, buluttaki davranış tabanlı cihaz öğrenmesi modellerinin çalışmaya başladıktan sonra bile saldırılara karşı nasıl yeni koruma katmanları ekledikleri gösterilmektedir.

### <a name="example-2-ntlm-relay---juicy-potato-malware-variant"></a>Örnek 2: NTLM geçişi - Sulu Patates kötü amaçlı yazılım değişkeni

Son blog gönderisinde açıklandığı gibi [Davranışsal engelleme ve kapsama: Optikleri korumaya dönüştürme](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection), Ocak 2020'de Uç Nokta için Defender kuruluştaki bir cihazda ayrıcalık yükseltme etkinliği algılamıştı. "NTLM geçişi kullanılarak olası ayrıcalık yükseltme" adlı bir uyarı tetiklendi.

:::image type="content" source="images/NTLMalertjuicypotato.png" alt-text="Sulu Patates kötü amaçlı yazılımı için NTLM uyarısı" lightbox="images/NTLMalertjuicypotato.png":::

Tehdit kötü amaçlı yazılım olduğu ortaya çıktı; saldırganlar tarafından bir cihazda ayrıcalık yükseltmesi almak için kullanılan, Sulu Patates adlı kötü bilinen bir hack aracının yeni, daha önce görülmemiş bir çeşidiydi.

Uyarı tetiklendikten dakikalar sonra dosya analiz edildi ve kötü amaçlı olduğu onaylandı. Aşağıdaki görüntüde gösterildiği gibi işlemi durduruldu ve engellendi:

:::image type="content" source="images/Artifactblockedjuicypotato.png" alt-text="Yapıt engellendi"  lightbox="images/Artifactblockedjuicypotato.png":::

Yapıt engellendikten birkaç dakika sonra aynı dosyanın birden çok örneği aynı cihazda engellendi ve daha fazla saldırganın veya diğer kötü amaçlı yazılımların cihaza dağıtılmasını engelledi.

Bu örnek, davranış engelleme ve kapsama özellikleriyle tehditlerin otomatik olarak algılandığını, kapsandığını ve engellendiğini gösterir.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)

## <a name="next-steps"></a>Sonraki adımlar

- [Uç Nokta için Defender hakkında daha fazla bilgi edinin](overview-endpoint-detection-response.md)

- [Saldırı yüzeyi azaltma kurallarınızı yapılandırma](attack-surface-reduction.md)

- [Blok modunda EDR etkinleştirme](edr-in-block-mode.md)

- [En son küresel tehdit etkinliğine bakın](https://www.microsoft.com/wdsi/threats)

- [Microsoft 365 Defender genel bakışını edinin](../defender/microsoft-365-defender.md)
