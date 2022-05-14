---
title: Microsoft Defender Virüsten Koruma için bulut korumasının neden etkinleştirilmesi gerekir?
description: Microsoft Defender Virüsten Koruma için bulut korumasının neden açık olması gerektiğini görün. Uç Nokta için Microsoft Defender çalışmasında birçok güvenlik özelliğine yardımcı olur
keywords: Microsoft Defender Virüsten Koruma, bulut koruması, güvenlik özellikleri, örnek gönderim
search.product: ''
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.date: 10/22/2021
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 195e929c0de1be9ab05f2685ba60e56c13dd3629
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415238"
---
# <a name="why-cloud-protection-should-be-enabled-for-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma için bulut korumasının neden etkinleştirilmesi gerekir?

**Şunlar için geçerlidir:**

- Microsoft Defender Virüsten Koruma
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**Platform**
- Windows

Microsoft Defender Virüsten Koruma bulut koruması, uç noktalarınızdaki ve ağınızdaki kötü amaçlı yazılımlara karşı korumaya yardımcı olur. Uç Nokta için Microsoft Defender'daki bazı güvenlik özellikleri ve özellikleri yalnızca bulut koruması etkinleştirildiğinde çalıştığından bulut korumasını açık tutmanızı öneririz. 

[![alt-text="Bulut korumasına bağlı öğeleri gösteren diyagram](images/mde-cloud-protection.png#lightbox)](enable-cloud-protection-microsoft-defender-antivirus.md)

Aşağıdaki tabloda, bulut korumasına bağlı olan özellikler ve özellikler özetlenmiştir: <br/><br/>

| Özellik/Yetenek  | Abonelik gereksinimi |  Açıklama  |
|---------|---------|--------|
| Buluttaki meta verileri denetleme  | Uç Nokta için Microsoft Defender Plan 1 veya Plan 2 (Tek başına veya Microsoft 365 E3 veya E5 gibi bir plana dahil) | Microsoft Defender Virüsten Koruma bulut hizmeti, ek bir savunma katmanı olarak makine öğrenmesi modellerini kullanır. Bu makine öğrenmesi modelleri meta verileri içerir, bu nedenle şüpheli veya kötü amaçlı bir dosya algılandığında meta verileri denetlenir. <br/><br/>Daha fazla bilgi edinmek için bkz[. Blog: Yeni nesil korumanın Uç Nokta için Microsoft Defender temelindeki gelişmiş teknolojileri tanıma](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)  |
| Bulut koruması ve örnek gönderimi | Uç Nokta için Microsoft Defender Plan 1 veya Plan 2 (Tek başına veya Microsoft 365 E3 veya E5 gibi bir plana dahil) | Dosyalar ve yürütülebilir dosyalar, patlama ve analiz için Microsoft Defender Virüsten Koruma bulut hizmetine gönderilebilir. <br/><br/>Daha fazla bilgi için bkz. [Microsoft Defender Virüsten Koruma'de bulut koruması ve örnek gönderme](cloud-protection-microsoft-antivirus-sample-submission.md).<br/><br/>**NOT**: Otomatik örnek gönderimi bulut korumasına dayanır ancak tek başına bir ayar olarak da yapılandırılabilir.         |
| Kurcalama koruması | Uç Nokta için Microsoft Defender Plan 2 (Tek başına veya Microsoft 365 E5 gibi bir plana dahil) | Kurcalama koruması, kuruluşunuzun güvenlik ayarlarında istenmeyen değişikliklere karşı korumaya yardımcı olur. Microsoft 365 Defender portalında kurcalama korumasını zorunlu kılmak için bulut korumasının etkinleştirilmesi gerekir. <br/><br/>Daha fazla bilgi için bkz [. Kurcalama koruması ile güvenlik ayarlarını koruma](prevent-changes-to-security-settings-with-tamper-protection.md).        |
| İlk görüşte engelle | Uç Nokta için Microsoft Defender Plan 1 veya Plan 2 (Tek başına veya Microsoft 365 E3 veya E5 gibi bir plana dahil) | İlk bakışta engelle yeni kötü amaçlı yazılımları algılar ve saniyeler içinde engeller. Şüpheli veya kötü amaçlı bir dosya algılandığında, ilk bakışta engelleme özellikleri bulut koruma arka ucu sorgular ve dosyanın bir tehdit olup olmadığını belirlemek için buluşsal yöntemler, makine öğrenmesi ve otomatik analiz uygular.<br/><br/>Daha fazla bilgi edinmek için bkz. ["İlk bakışta engelle" nedir?](configure-block-at-first-sight-microsoft-defender-antivirus.md#what-is-block-at-first-sight)   |
| Acil durum imza güncelleştirmeleri | Uç Nokta için Microsoft Defender Plan 2 (Tek başına veya Microsoft 365 E5 gibi bir plana dahil) | Kötü amaçlı içerik algılandığında, acil durum imza güncelleştirmeleri ve düzeltmeleri dağıtılır. Bir sonraki normal güncelleştirmeyi beklemek yerine, bu düzeltmeleri ve güncelleştirmeleri dakikalar içinde alabilirsiniz.   |
| Blok modunda uç nokta algılama ve yanıt (EDR) | Uç Nokta için Microsoft Defender Plan 2 (Tek başına veya Microsoft 365 E5 gibi bir plana dahil) | Blok modundaki EDR, Microsoft Defender Virüsten Koruma bir cihazdaki birincil virüsten koruma ürünü olmadığında ek koruma sağlar. Blok modunda EDR, Microsoft olmayan birincil virüsten koruma çözümünün atlamış olabileceği EDR tarafından oluşturulan taramalar sırasında bulunan yapıtları düzeltiyor. Birincil virüsten koruma çözümü olarak Microsoft Defender Virüsten Koruma olan cihazlar için etkinleştirildiğinde, blok modundaki EDR, EDR tarafından oluşturulan taramalar sırasında tanımlanan yapıtları otomatik olarak düzeltmenin ek avantajını sağlar. <br/><br/>Daha fazla bilgi için bkz. [blok modunda EDR](edr-in-block-mode.md).|
| Saldırı yüzeyini azaltma kuralları | Uç Nokta için Microsoft Defender Plan 1 veya Plan 2 (Tek başına veya Microsoft 365 E3 veya E5 gibi bir plana dahil) | Saldırı yüzeyinin azaltılması, kuruluşunuzun uç noktalarının siber saldırılara karşı savunmasız olduğu yerleri ve yolları azaltmakla alakalıdır. Saldırı yüzeyi azaltma kuralları, kötü amaçlı yazılımları durdurmaya yardımcı olmak için yapılandırabileceğiniz akıllı kurallardır. Belirli kuralların tam olarak çalışması için bulut korumasının açık olması gerekir. Bu kurallar şunlardır: <br/>- Yaygınlık, yaş veya güvenilen liste ölçütlerini karşılamadığı sürece yürütülebilir dosyaların çalışmasını engelleyin <br/>- Fidye yazılımlara karşı gelişmiş koruma kullanın <br/>- Güvenilmeyen programların çıkarılabilir sürücülerden çalıştırılmasını engelle <br/><br/>Daha fazla bilgi edinmek için bkz. [Kötü amaçlı yazılım bulaşmasını önlemek için saldırı yüzeyi azaltma kurallarını kullanma](attack-surface-reduction.md).  |
| Güvenliğin aşılmasına ilişkin göstergeler (ICS) | Uç Nokta için Microsoft Defender Plan 2 (Tek başına veya Microsoft 365 E5 gibi bir plana dahil) | Uç Nokta için Defender'daki IoC'ler varlıkların algılanmasını, önlenmesini ve dışlanmasını tanımlayacak şekilde yapılandırılabilir. Örneğin, Uç Nokta için Defender'da taramaları ve düzeltme eylemlerini Microsoft Defender Virüsten Koruma özel durumları tanımlamak için "izin ver" göstergeleri kullanılabilir. Başka bir örnek olarak, dosyaların veya işlemlerin yürütülmesini önlemek ve bu etkinlikleri Microsoft 365 Defender portalında görüntülenebilen uyarılarla izlemek için "uyarı ve engelleme" göstergeleri kullanılabilir. <br/><br/>Daha fazla bilgi için bkz. [Gösterge oluşturma](manage-indicators.md).    |

> [!TIP]
> Uç Nokta için Defender planları hakkında daha fazla bilgi edinmek için bkz. [Plan 1 ve Plan 2 Uç Nokta için Microsoft Defender](defender-endpoint-plan-1-2.md).

## <a name="next-steps"></a>Sonraki adımlar

Bulut korumasına ve Microsoft Defender Virüsten Koruma'deki rolüne genel bir bakış elde ettiğinize göre, sonraki adımlardan bazıları şunlardır:

1. **[Bulut korumasını etkinleştirin](enable-cloud-protection-microsoft-defender-antivirus.md)**. Bulut korumasını Microsoft Endpoint Manager (artık Microsoft Endpoint Configuration Manager ve Microsoft Intune), grup ilkesi veya PowerShell cmdlet'leri ile etkinleştirebilirsiniz.

2. **[Bulut koruma düzeyini belirtin](specify-cloud-protection-level-microsoft-defender-antivirus.md)**. Microsoft Endpoint Manager veya grup ilkesi kullanarak bulut tarafından sunulan koruma düzeyini belirtebilirsiniz. Koruma düzeyi, bulutla paylaşılan bilgi miktarını ve yeni dosyaların ne kadar agresif bir şekilde engellendiğini etkiler.

3. **[Microsoft Defender Virüsten Koruma için ağ bağlantılarını yapılandırın ve doğrulayın](configure-network-connections-microsoft-defender-antivirus.md)**. Bulut korumasının etkili bir şekilde çalışması için ağınızın ve uç noktalarınızın bağlanabilmesi gereken bazı Microsoft URL'leri vardır. Bu makalede, güvenlik duvarı veya ağ filtreleme kuralları aracılığıyla izin verilmesi gereken URL'ler ve ağınızın bulut korumasına düzgün şekilde kaydedildiğini onaylama yönergeleri listelenir.

4. **["İlk bakışta engelle" özelliğini yapılandırın](configure-block-at-first-sight-microsoft-defender-antivirus.md)**. "İlk bakışta engelle" özelliği, geleneksel Güvenlik bilgileri için saatler beklemek zorunda kalmadan yeni kötü amaçlı yazılımları saniyeler içinde engelleyebilir. Microsoft Endpoint Manager veya grup ilkesi kullanarak etkinleştirebilir ve yapılandırabilirsiniz.

5. **[Bulut bloğu zaman aşımı süresini yapılandırın](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)**. Microsoft Defender Virüsten Koruma, bulut koruma hizmetimizi sorgularken şüpheli dosyaların çalışmasını engelleyebilir. Microsoft Endpoint Manager veya grup ilkesi kullanarak dosyanın çalışmasının engellenme süresini yapılandırabilirsiniz.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)