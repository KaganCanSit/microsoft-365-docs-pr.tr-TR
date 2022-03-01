---
title: Kullanıcı ayarları için yerel geçersiz Microsoft Defender Virüsten Koruma yapılandırma
description: Kullanıcıların Microsoft Defender AV'de ayarları yerel olarak değiştirmesini etkinleştirme veya devre dışı bırakma.
keywords: yerel geçersiz kılma, yerel ilke, grup ilkesi, gpo, kilitleme,birleştirme, listeler
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: ec916b008ddb3e0669111efe2bd493c709327296
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997547"
---
# <a name="prevent-or-allow-users-to-locally-modify-microsoft-defender-antivirus-policy-settings"></a>Kullanıcıların yerel olarak ilke ayarlarını değiştirmesini Microsoft Defender Virüsten Koruma veya izin verme


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Varsayılan olarak Microsoft Defender Virüsten Koruma Grup İlkesi Nesnesi aracılığıyla dağıtılan tüm ayarlar ağ bağlantı noktalarında kullanıcıların ayarları yerel olarak değiştirmesini engellemez. Bazı durumlarda bunu değiştirebilirsiniz.

Örneğin, bazı kullanıcı gruplarının (güvenlik araştırmacısı ve tehdit tehdit noktaları gibi) kendi kullanım uç noktaları ayarları üzerinde daha fazla denetime sahip olmasına izin vermek gerekebilir.

## <a name="configure-local-overrides-for-microsoft-defender-antivirus-settings"></a>Kullanıcı ayarları için yerel geçersiz Microsoft Defender Virüsten Koruma yapılandırma

Bu ilkeler için varsayılan ayar Devre **Dışı'dır**.

Etkin olarak ayarlanırsa **, uç** noktalardaki kullanıcılar Windows Güvenliği uygulamasıyla, yerel [Grup İlkesi](microsoft-defender-security-center-antivirus.md) ayarlarıyla ve PowerShell cmdlet'leriyle (uygun olduğunda) ilişkili ayarda değişiklik yapabilirsiniz.

Aşağıdaki tabloda her geçersiz kılma ilkesi ayarı ve ilişkili özellik veya ayar için yapılandırma yönergeleri listele.

Bu ayarları yapılandırmak için:

1. Grup İlkesi yönetim bilgisayarınızda Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin ve** Yönetim **şablonları'ne tıklayın**.

3. Bileşenleri ve bileşenleri **Windows için Microsoft Defender Virüsten Koruma** >  ayarlar tablosunda belirtilen konum'a (bu makalede)  kadar ağacı genişletin.

4. Aşağıdaki tabloda belirtilen ayar **ilkesine** çift tıklayın ve seçeneği istediğiniz yapılandırmaya ayarlayın. **Tamam'a** tıklayın ve diğer tüm ayarlar için işlemi yinelayın.

5. Grup İlkesi Nesnesini her zamanki gibi dağıtın.

## <a name="table-of-settings"></a>Ayarlar tablosu

<br/><br/>

| Konum | Ayar | Makale |
|---|---|---|---|
| HARITALAR |Microsoft MAPS'a raporlama için yerel ayarı geçersiz kılmayı yapılandırma|[Bulut teslimi korumasını etkinleştirme](enable-cloud-protection-microsoft-defender-antivirus.md) |
| Karantina|Öğeleri Karantina klasöründen kaldırma işlemi için yerel ayarı geçersiz kılmayı yapılandırma|[Taramalar için düzeltmeyi yapılandırma](configure-remediation-microsoft-defender-antivirus.md) |
| Gerçek zamanlı koruma|Bilgisayarınızda dosyayı ve program etkinliğini izlemek için yerel ayarı geçersiz kılmayı yapılandırma|[Her zaman açık koruma Microsoft Defender Virüsten Koruma izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Gerçek zamanlı koruma|Gelen ve giden dosya etkinliğini izlemek için yerel ayarı geçersiz kılmayı yapılandırma | [Her zaman açık koruma Microsoft Defender Virüsten Koruma izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Gerçek zamanlı koruma|İndirilen tüm dosyaları ve ekleri taramak için yerel ayarı geçersiz kılmayı yapılandırma|[Her zaman açık koruma Microsoft Defender Virüsten Koruma izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Gerçek zamanlı koruma|Davranış izlemeyi açmak için yerel ayarı geçersiz kılmayı yapılandırma|[Her zaman açık koruma Microsoft Defender Virüsten Koruma izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Gerçek zamanlı koruma|Gerçek zamanlı korumayı açmak için yerel ayarı geçersiz kılmayı yapılandırma|[Her zaman açık koruma Microsoft Defender Virüsten Koruma izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md) |
| Düzeltme|Düzeltmeyi tamamlamak üzere zamanlanmış bir tam tarama çalıştırmak için günün saati için yerel ayarı geçersiz kılmayı yapılandırma|[Taramalar için düzeltmeyi yapılandırma](configure-remediation-microsoft-defender-antivirus.md) |
| Tarama|CPU kullanımının en yüksek yüzdesi için yerel ayarı geçersiz kılmayı yapılandırma|[Taramaları yapılandırma ve çalıştırma](run-scan-microsoft-defender-antivirus.md) |
| Tarama|Zamanlama tarama günü için yerel ayarı geçersiz kılmayı yapılandırma|[Zamanlanmış taramaları yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Tarama|Zamanlanan hızlı tarama zamanı için yerel ayarı geçersiz kılmayı yapılandırma|[Zamanlanmış taramaları yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Tarama|Zamanlanan tarama zamanı için yerel ayarı geçersiz kılmayı yapılandırma|[Zamanlanmış taramaları yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |
| Tarama|Zamanlanmış taramada kullanmak üzere tarama türü için yerel ayarı geçersiz kılmayı yapılandırma|[Zamanlanmış taramaları yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md) |

<a id="merge-lists"></a>

## <a name="configure-how-locally-and-globally-defined-threat-remediation-and-exclusions-lists-are-merged"></a>Yerel olarak ve genel olarak tanımlanan tehdit düzeltmesi ve dışlama listelerinin nasıl birleştirileceklerini yapılandırma

Ayrıca, yerel olarak tanımlanan listelerin genel tanımlı listelerle nasıl birleştirilecek veya bir araya birleştirileceklerini de yapılandırabilir. Bu ayar dışlama [listeleri](configure-exclusions-microsoft-defender-antivirus.md), belirtilen [düzeltme listeleri ve saldırı](configure-remediation-microsoft-defender-antivirus.md) yüzeyini azaltma [için geçerlidir](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction).

Varsayılan olarak, yerel grup ilkesinde yapılandırılmış listeler ve Windows Güvenliği uygulaması, ağ üzerinde dağıtmış olduğunuz uygun Grup İlkesi Nesnesi tarafından tanımlanan listelerle birleştirilir. Çakışmaların olduğu yerde, genel olarak tanımlanan liste öncelikli olur.

Yalnızca genel olarak tanımlanmış listelerin (dağıtılmış GPOS'lardan olanlar gibi) kullanıldıklarından emin olmak için bu ayarı devre dışı abilirsiniz.

### <a name="use-group-policy-to-disable-local-list-merging"></a>Yerel liste birleştirmeyi devre dışı bırakmak için Grup İlkesi kullanma

1. Grup İlkesi yönetim bilgisayarınızda Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin ve** Yönetim **şablonları'ne tıklayın**.

3. Bileşenleri ve bileşenleri Windows **için > Microsoft Defender Virüsten Koruma**.

4. Listeler için yerel **yönetici birleştirme davranışını yapılandır'a çift tıklayın** ve seçeneği Devre Dışı olarak **ayarlayın**. **Tamam**'a tıklayın.

> [!NOTE]
> Yerel liste birleştirmeyi devre dışı bıraksanız, denetimli klasör erişim ayarları geçersiz kılınacak. Ayrıca, yerel yönetici tarafından ayarlanmış tüm korumalı klasörleri veya izin verilen uygulamaları geçersiz kılar. Denetimli klasör erişimi ayarları hakkında daha fazla bilgi için bkz. [Denetimdeki engellenen uygulamaya izin Windows Güvenliği](https://support.microsoft.com/help/4046851/windows-10-allow-blocked-app-windows-security).

## <a name="related-topics"></a>İlgili konular

- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Kullanıcı profiliyle son kullanıcı etkileşimi Microsoft Defender Virüsten Koruma](configure-end-user-interaction-microsoft-defender-antivirus.md)
