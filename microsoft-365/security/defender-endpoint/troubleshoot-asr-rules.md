---
title: ASR Kurallarını Uç Nokta için Microsoft Defender ve sorunlarını giderme
description: Bu konuda, Microsoft ASR Kuralları'nın nasıl rapor Uç Nokta için Microsoft Defender sorun gidermesi açıklanmıştır
keywords: Saldırı yüzeyini azaltma kuralları, asr, hip'ler, izinsiz giriş önleme sistemi, koruma kuralları, exploit önleme, izinsiz giriş önleme, exploit, bulaşma önleme, uç nokta için Microsoft Defender
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
author: lovina-saldanha
ms.author: dansimp
ms.reviewer: ''
manager: dansimp
ms.custom:
- asr
- admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: b1a90ec887f62a3c486c30ed50b87482de451c01
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471021"
---
# <a name="report-and-troubleshoot-microsoft-defender-for-endpoint-asr-rules"></a>ASR Kurallarını Uç Nokta için Microsoft Defender ve sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Yeni <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalı</a> Microsoft kimlikleriniz, verileriniz, cihazlarınız, uygulamalarınız ve altyapınız genelinde güvenliği izlemek ve yönetmek için yeni bir arabirimdir. Burada kolayca kurumnizin güvenlik durumunu sınabilir, cihazları, kullanıcıları ve uygulamaları yapılandırabilir ve şüpheli etkinliklere karşı uyarılar alabilirsiniz. Bu Microsoft 365 Defender portalı, güvenlik yöneticilerine ve güvenlik işlemleri ekiplerine, kuruluşlarını daha iyi yönetmek ve korumak için tasarlanmıştır. Microsoft 365 Defender portalını ziyaret edin<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a>.

Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalında</a>, size şirketinizin mevcut ASR kuralları yapılandırmasına ve etkinliklerine tam bir bakış sunariz. Bu raporların doldurulması için cihazlarınızı Uç Nokta için Microsoft Defender hizmetine eklemeniz gerektiğini unutmayın.
Bu videoda, Rapor Cihazlarında Saldırı Microsoft 365 Defender  \>  \> azaltma altındaki ekran **görüntüsü.** Cihaz düzeyinde, Saldırı yüzeyini **azaltma kuralları** **bölmesinden Yapılandırma'ya** tıklayın. Belirli bir cihazı seçerek tek tek ASR kuralı yapılandırmasını denetlemeniz için aşağıdaki ekran görüntülenir.

:::image type="content" source="images/asrrulesnew.png" alt-text="ASR kuralları sayfası" lightbox="images/asrrulesnew.png":::

## <a name="microsoft-defender-for-endpoint---advanced-hunting"></a>Uç Nokta için Microsoft Defender - Gelişmiş av

Gelişmiş avlama özelliği, Uç Nokta için Microsoft Defender özelliklerinden biri. Gelişmiş ava yabancı değilsanız, gelişmiş avla tehditlere karşı önceden arama [yapılmasına yardımcı olun](advanced-hunting-overview.md).

Gelişmiş av, yakalanan (ham) verilerin en fazla 30 günü keşfetmenizi sağlayan, Uç Nokta için Defender'ın cihazlarından toplayan sorgu tabanlı (Kusto Sorgu Dili) bir tehdit arama aracıdır. Gelişmiş arama yoluyla, ilginç göstergeleri ve varlıkları bulmak için etkinlikleri önceden inceebilirsiniz. Verilere esnek erişim, hem bilinen hem de potansiyel tehditlere karşı kısıtlanmamış aramalara yardımcı olur.

Gelişmiş arama yoluyla, ASR kuralları bilgilerini ayıklamak, rapor oluşturmak ve verilen bir ASR kuralı denetimi bağlamında ayrıntılı bilgi almak veya etkinliği engellemek mümkündür.

ASR kuralları olayları, tablonun gelişmiş av bölümündeki DeviceEvents tablosundan sorgulanıyor Microsoft 365 Defender. Örneğin, aşağıdaki sorgu gibi basit bir sorgu, son 30 gün boyunca veri kaynağı olarak ASR kurallarına sahip tüm olayları bildirabilir ve bunları ActionType sayısına göre özetler; bu durumda bu, ASR kuralının gerçek kodadı olur.

:::image type="content" source="images/adv-hunt-querynew.png" alt-text="Gelişmiş av sorgusu" lightbox="images/adv-hunt-querynew.png":::

:::image type="content" source="images/adv-hunt-sc-2new.png" alt-text="Gelişmiş av sayfası" lightbox="images/adv-hunt-sc-2new.png":::

Gelişmiş avla sorguları istediğiniz gibi şekillendirebilirsiniz; böylece, ister tek bir makineye bir şey sabitlemek ister tüm ortamınız üzerinden içgörüler ayıklamak istediğinizden bağımsız olarak, neler olduğunu görebilirsiniz.

## <a name="microsoft-defender-for-endpoint-machine-timeline"></a>Uç Nokta için Microsoft Defender makinesi zaman çizelgesi

Gelişmiş avlara alternatif olarak, ancak kapsamı daha dar olan bu yöntem, Uç Nokta için Microsoft Defender çizelgesidir. Son altı ay boyunca, bir cihazın toplanan tüm olaylarını görüntülemek için, Microsoft 365 Defender listesine gidip belirli bir makineyi seçin ve Zaman Çizelgesi sekmesine tıklayın.

Aşağıda, verilen bir uç noktadaki bu etkinliklerin Zaman Çizelgesi görünümünün ekran görüntüsü yer almaktadır. Bu görünümde, sağ bölme boyunca etkinlik Grupları'nın herhangi birini temel alarak olay listesini filtreleyebilirsiniz. Uyarıları görüntülerken ve geçmiş zaman çizelgesinde kaydırırken Bayraklı ve Verbose olaylarını etkinleştirebilirsiniz veya devre dışı ekleyebilirsiniz.

:::image type="content" source="images/mic-sec-def-timelinenew.png" alt-text="Zaman Microsoft 365 Defender çizelgesi" lightbox="images/mic-sec-def-timelinenew.png":::

## <a name="how-to-troubleshoot-asr-rules"></a>ASR kuralları nasıl giderilir?

İlk ve en acil yol, Windows cihazda yerel olarak denetimi yapmaktır; bu cihazda ASR kuralları etkindir (ve bu kuralların yapılandırması da PowerShell cmdlet'leri kullanılarakdır).

BURADA, ASR kurallarının etkisini ve Windows gidermek için size yardımcı olacak diğer bilgi kaynakları ve hizmetleri ve hizmetleri hakkında daha fazla bilgi ve bilgiler ve daha açık bir şekilde açıkılmıştır.

### <a name="querying-which-rules-are-active"></a>Hangi kuralların etkin olduğunu sorgulama

ASR kurallarının zaten etkinleştirildikten sonra etkinleştirilmediğini belirlemenin en kolay yollarından biri Get-MpPreference PowerShell cmdlet'idir.

İşte bir örnek:

:::image type="content" source="images/getmpreferencescriptnew.png" alt-text="Get mppreference betiği" lightbox="images/getmpreferencescriptnew.png":::

Farklı yapılandırılmış eylemlerle birlikte, etkin birden çok ASR kuralı vardır.

ASR kurallarıyla ilgili yukarıdaki bilgileri genişletmek için, asr **kurallarında AttackSurfaceReductionRules_Ids****/veya tüm** AttackSurfaceReductionRules_Actions.

Örneğin:

```powershell
Get-MPPreference | Select-Object -ExpandProperty**AttackSurfaceReductionRules_Ids
```

:::image type="content" source="images/getmpref-examplenew.png" alt-text="Get mpreference example" lightbox="images/getmpref-examplenew.png":::

Yukarıda, 0'dan farklı bir ayara sahip ASR kuralları için tüm Kimlikler (Yapılandırılmadı) görünür.

Bundan sonra, her kuralın yapılandırılan gerçek eylemlerini (Engelle veya Denetim) listelenin.

```powershell
Get-MPPreference | Select-Object -ExpandProperty**AttackSurfaceReductionRules_Actions
```

:::image type="content" source="images/getmpref-example2new.png" alt-text="Get mppreference example2" lightbox="images/getmpref-example2new.png":::

### <a name="querying-blocking-and-auditing-events"></a>Olayları engelleme ve denetleme

ASR kuralı olayları, günlük Windows Defender 2002'de 22 Windows Defender 2013'Windows Defender 2013'e tıklayın.

Buna erişmek için, Windows Olay Görüntüleyicisi'i açın ve  \> **Microsoft** \>  \> Windows **Windows Defender** \> **göz atabilirsiniz**.

:::image type="content" source="images/eventviewerscrnew.png" alt-text="Olay Görüntüleyicisi sayfası" lightbox="images/eventviewerscrnew.png":::

## <a name="microsoft-defender-antimalware-protection-logs"></a>Microsoft Defender Kötü Amaçlı Yazılımdan Koruma Günlükleri

Ayrıca, gerektiğinde görevleri yönetmek ve yapılandırmak ve otomatikleştirmek `*mpcmdrun.exe*`için kullanılmaktadır ve Microsoft Defender Virüsten Koruma da adlandırılan bu özel komut satırı aracı aracılığıyla kural olaylarını görüntüebilirsiniz.

Bu yardımcı programı *%ProgramFiles%\Windows Defender\MpCmdRun.exe'da bulabilirsiniz*. Bu komutu yükseltilmiş komut isteminden çalıştırmanız (yani Yönetici olarak çalıştırmanız) gerekir.

Destek bilgilerini oluşturmak için *-getfilesMpCmdRun.exe yazın*. Bir süre sonra, birkaç günlük bir arşive (MpSupportFiles.cab) paketlenir ve *C:\ProgramData\Microsoft\Windows Defender\Support konumunda hazır olur*.

:::image type="content" source="images/malware-prot-logsnew.png" alt-text="Kötü amaçlı yazılımdan koruma günlükleri" lightbox="images/malware-prot-logsnew.png":::

Bu arşivi ayıklarseniz, sorun giderme amacıyla birçok dosya kullanabilirsiniz.

En uygun dosyalar şunlardır:

- **MPOperationalEvents.txt**: Bu dosya, TT'nin İşlem Olay Görüntüleyicisi Windows Defender bulunan bilgi düzeyini içerir.
- **MPRegistry.txt**: Bu dosyada, destek günlükleri yakalanır Windows Defender anda tüm geçerli yapılandırmaları çözümleyebilirsiniz.
- **MPLog.txt**: Bu günlük, 2013'e ilişkin tüm eylemler/işlemler hakkında daha ayrıntılı Windows Defender.
