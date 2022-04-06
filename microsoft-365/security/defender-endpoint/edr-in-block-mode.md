---
title: Engelleme modunda uç nokta algılama ve yanıt
description: Engelleme uç noktada algılama ve yanıtlama hakkında bilgi
keywords: Uç Nokta için Microsoft Defender, mde, EDR modunda çalışma, pasif modunu engelleme
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
ms.date: 03/18/2022
ms.collection: m365-security-compliance
ms.technology: mde
ms.openlocfilehash: 151fb8de088531b9a9f053fc2b5d3c433055e21f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473133"
---
# <a name="endpoint-detection-and-response-edr-in-block-mode"></a>Engelleme modunda uç nokta algılama EDR yanıt (EDR)

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-edr-in-block-mode"></a>Engelleme EDR nedir?

[Engelleme modunda uç nokta](overview-endpoint-detection-response.md) algılama EDR yanıt (Microsoft Defender Virüsten Koruma), birincil virüsten koruma ürünü değil de pasif modunda çalıştırılamaz ise, kötü amaçlı yapıtlara karşı ek koruma sağlar. EDR modundaki çalışma dosyaları, bu özellikler tarafından algılanan kötü amaçlı yapıları düzeltmek için arka EDR çalışır. Bu tür yapıları, Microsoft virüsten koruma ürünü olmayan birincil ürün atladı olabilir. Microsoft Defender Virüsten Koruma'i birincil virüsten koruma olarak çalıştıran cihazlar için EDR engelleme modundayken Microsoft Defender Virüsten Koruma'in ihlal sonrası, davranışsal veya algılamalarda otomatik eylemler gerçekleştirene kadar fazladan bir savunma EDR sağlar.

> [!IMPORTANT]
> EDR modundayken gerçek zamanlı koruma etkinleştirildiğinde Microsoft Defender Virüsten Koruma koruma sağlanmaz. Etkin virüsten koruma Microsoft Defender Virüsten Koruma çalışmasına bağlı olan tüm özellikler, aşağıdaki önemli örnekler de dahil olmak üzere çalışmay olacaktır:
>
> - Erişimle tarama da dahil olmak üzere gerçek zamanlı koruma, pasif Microsoft Defender Virüsten Koruma modundayken kullanılamaz. Gerçek zamanlı koruma ilkesi ayarları hakkında daha fazla bilgi edinmek için bkz. Her **[zaman açık olan Microsoft Defender Virüsten Koruma etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)**.
>
> - Ağ koruması **[ve saldırı](network-protection.md)** **[yüzeyini azaltma kuralları gibi özellikler](attack-surface-reduction.md)**, ancak Microsoft Defender Virüsten Koruma modunda çalıştır çalıştır dış olduğunda kullanılabilir.
>
> Microsoft olmayan virüsten koruma yazılımınızın bu özellikleri sağladığı tahmin ediliyor.

EDR modundaki alan, tehdit tehditleriyle [& güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md). Daha önce etkinleştirilmemişse, bu özelliği engelleme [](tvm-security-recommendation.md) modunda EDR için, kuruluş güvenlik ekibinin bir güvenlik önerisi olur.

:::image type="content" source="images/edrblockmode-TVMrecommendation.png" alt-text="Engelleme modunda EDR açma önerisi" lightbox="images/edrblockmode-TVMrecommendation.png":::

> [!TIP]
> En iyi korumayı elde etmek için, **[temelleri ve Uç Nokta için Microsoft Defender dağıtın](configure-machines-security-baseline.md)**.

## <a name="what-happens-when-something-is-detected"></a>Bir şey algılandığında ne olur?

Blok EDR modunda bir yapı açıksa ve kötü amaçlı bir yapı algılandığında, bu Uç Nokta için Microsoft Defender yapıyı engeller ve düzelter. Güvenlik işlemleri takımınız tamamlanmış eylemler olarak listelenmiş **olarak** İşlem merkezinde  Engellendi veya [Engellendi](respond-machine-alerts.md#check-activity-details-in-action-center) olarak algılama durumunu gösterir.

Aşağıdaki resimde, engelleme modundaki bir istenmeyen yazılım örneği görüntülenmiş ve EDR engellenmiştir:

:::image type="content" source="images/edr-in-block-mode-detection.png" alt-text="Engelleme modunda EDR algılama" lightbox="images/edr-in-block-mode-detection.png":::


## <a name="enable-edr-in-block-mode"></a>EDR modunda etkinleştirme

> [!IMPORTANT]
> Platform sürüm 4.18.2202.X ile başlayarak, EDR'ı EDR CSP'leri kullanarak belirli cihaz gruplarını hedefle Intune sunun. Kiracı portalında kiracı genelinde EDR modunda kiracı genelinde kiracıyı <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">ayarlamaya Microsoft 365 Defender.</a> EDR modundayken, öncelikle pasif modunda Microsoft Defender Virüsten Koruma çalıştıran cihazlar için önerilir (Microsoft dışı bir virüsten koruma çözümü yüklü ve cihazda etkindir). 

> [!TIP]
> Engelleme modunda [otomatik olarak](#requirements-for-edr-in-block-mode) açmadan önce gereksinimlerin EDR karşı olduğundan emin olun.

### <a name="security-portal"></a>Güvenlik Portalı 

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/) ) ve oturum açın.

2. Genel **Ayarlar** \> **Uç Noktaları Genel** **Özellikler'i** \> \> **seçin**.

3. Ekranı aşağı kaydırın ve Engelleme modunda **EDR etkinleştir'i etkinleştirin**.

### <a name="intune"></a>Intune

Intune'ta özel bir ilke oluşturmak için bkz. [OMA-URIs'i INTUNE aracılığıyla bir CSP'yi hedef olarak](/troubleshoot/mem/intune/deploy-oma-uris-to-target-csp-via-intune) dağıtma ve şirket içi ilke karşılaştırması.

Engelleme modunda düzeltmeler için kullanılan Defender CSP EDR, Defender CSP'nin altındaki "Yapılandırma/PasifRemediation" [ile ilgili daha fazla bilgi için bkz](/windows/client-management/mdm/defender-csp).


## <a name="requirements-for-edr-in-block-mode"></a>Blok modunda EDR gereksinimleri

Aşağıdaki tabloda, engelleme modundaki EDR gereksinimleri listelemektedir:

|Gereksinim|Ayrıntılar|
|---|---|
|İzinler|Bu kuruluşta Genel Yönetici veya Güvenlik Yöneticisi rolünün [Azure Active Directory.](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal) Daha fazla bilgi için bkz. [Temel izinler](basic-permissions.md).|
|İşletim sistemi|Cihazlar aşağıdaki sürümlerinin birini çalıştırabiliyor Windows: <br/>- Windows 11 <br/>- Windows 10 (tüm sürümler)<br/>- Windows Server 2022 <br/>- Windows Server 2019<br/>- Windows, sürüm 1803 veya daha yenisi<br/>- Windows Server 2016 ve Windows Server 2012 R2 (yeni birleşik [istemci çözümüyle](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview))<sup>[[1](#fn1)]</sup>  |
|Uç Nokta için Microsoft Defender|Cihazlar, Uç Nokta için Defender'a kabul edildi olmalıdır. Aşağıdaki makalelere bakın: <br/>- [En düşük Uç Nokta için Microsoft Defender](minimum-requirements.md)<br/>- [Cihazları ekleme ve cihaz Uç Nokta için Microsoft Defender yapılandırma](onboard-configure.md)<br/>- [Uç Windows Için Defender hizmetine yerleşik sunucu ekleme](configure-server-endpoints.md)<br/>- [Modern Windows Server 2012 (Önizleme) R2 ve 2016 işlevleriyle yeni özellikler](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview) |
|Microsoft Defender Virüsten Koruma|Cihazların etkin Microsoft Defender Virüsten Koruma edilgen modda veya pasif modunda yüklü ve çalışır durumda olması gerekir. [Etkin Microsoft Defender Virüsten Koruma edilgen modda olduğunu onaylayın](#how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode).|
|Bulut teslimi koruma|Microsoft Defender Virüsten Koruma bulut teslimi koruması etkin [olacak şekilde yapılandırılması gerekir](enable-cloud-protection-microsoft-defender-antivirus.md).|
|Microsoft Defender Virüsten Koruma platformu|Cihazlar güncel olmalıdır. Doğrulamak için, PowerShell kullanarak [Get-MpCompcompstatus](/powershell/module/defender/get-mpcomputerstatus) cmdlet'ini yönetici olarak çalıştırın. **AMProductVersion satırda** **4.18.2001.10 veya** üzerini görüyor olması gerekir. <p> Daha fazla bilgi için bkz[. Güncelleştirmeleri Microsoft Defender Virüsten Koruma ve taban çizgilerini uygulama](manage-updates-baselines-microsoft-defender-antivirus.md).|
|Microsoft Defender Virüsten Koruma altyapısı|Cihazlar güncel olmalıdır. Doğrulamak için, PowerShell kullanarak [Get-MpCompcompstatus](/powershell/module/defender/get-mpcomputerstatus) cmdlet'ini yönetici olarak çalıştırın. **AMEngineVersion satırda** **1.1.16700.2 veya üzeri bir sürüm** görüyor gerekir. <p> Daha fazla bilgi için bkz[. Güncelleştirmeleri Microsoft Defender Virüsten Koruma ve taban çizgilerini uygulama](manage-updates-baselines-microsoft-defender-antivirus.md).|

(<a id="fn1">1</a>) Bkz[. EDR ve R2'de Windows Server 2016 desteklenen Windows Server 2012 var mı?](#is-edr-in-block-mode-supported-on-windows-server-2016-and-windows-server-2012-r2)

> [!IMPORTANT]
> En iyi koruma değerini almak için, virüsten koruma çözüm eknizin düzenli güncelleştirmeleri ve temel özellikleri alacak şekilde yapılandırıldığından ve dışlamaların [yapılandırıldığından emin olun](configure-exclusions-microsoft-defender-antivirus.md). EDR modunda yapılan her iki durum, özel durum için tanımlanan dışlamalara Microsoft Defender Virüsten Koruma, ancak özel durum için tanımlanan Uç Nokta için Microsoft Defender[](manage-indicators.md).

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="can-i-specify-exclusions-for-edr-in-block-mode"></a>Engelleme modundaki EDR özel EDR özel kalmaları belirtmem mümkün mü?

Hatalı pozitif sonuç elde ediyorsanız, dosyayı gönderme sitesinde çözümleme [Microsoft Güvenlik Zekası gönderebilirsiniz](https://www.microsoft.com/en-us/wdsi/filesubmission).

Dışlama için dışlama da Microsoft Defender Virüsten Koruma. Bkz[. Taramalarda dışlamaları yapılandırma Microsoft Defender Virüsten Koruma doğrulama](configure-exclusions-microsoft-defender-antivirus.md).

### <a name="do-i-need-to-turn-edr-in-block-mode-on-if-i-have-microsoft-defender-antivirus-running-on-devices"></a>Cihazlarda çalıştırmış EDR, engelleme modundayken Microsoft Defender Virüsten Koruma gerekir mi?

Engelleme modundaki EDR, Microsoft dışı bir virüsten koruma ürünü tarafından kaçırilen ihlal sonrası algılamaları düzeltmektir. Bununla birlikte, EDR edilgen modda veya etkin modda Microsoft Defender Virüsten Koruma engelleme modundayken engelleme modunu açık tutmanızı öneririz.

- Pasif Microsoft Defender Virüsten Koruma modundayken, blok EDR modundaki bir sistem, pasif moduna sahip başka bir savunma Uç Nokta için Microsoft Defender.

- Microsoft Defender Virüsten Koruma etkin moddayken, EDR modundayken fazladan tarama işlemi sağlanmaz, ancak Microsoft Defender Virüsten Koruma ihlal sonrası, davranış ya da algılamalarda otomatik EDR olanak sağlar.

### <a name="will-edr-in-block-mode-affect-a-users-antivirus-protection"></a>Engelleme EDR bir virüsten koruma yazılımı kullanıcının virüsten korumasını etkiler mi?

EDR modundayken yapılan değişiklikler, kullanıcıların cihazlarında çalışan üçüncü taraf virüsten korumayı etkilemez. EDR modundaki çözüm, birincil virüsten koruma çözümünün bir şeyi kaçırması veya ihlal sonrası algılaması varsa çalışır. EDR modunun herhangi biri pasif modunda Microsoft Defender Virüsten Koruma gibi çalışır, ancak engelleme modundaki EDR da algılanlan kötü amaçlı yapıtları veya davranışları engeller ve düzeltmez.

### <a name="why-do-i-need-to-keep-microsoft-defender-antivirus-up-to-date"></a>Neden güncel tutmak Microsoft Defender Virüsten Koruma gerekiyor?

Yeni Microsoft Defender Virüsten Koruma kötü amaçlı öğeleri algılamak ve düzeltmesi nedeniyle, güncel tutmak önemlidir. Blok EDR etkili olması için en son cihaz öğrenme modellerini, davranış algılamalarını ve heuristleri kullanır. Uç [Nokta için Defender](microsoft-defender-endpoint.md) özellik yığını tümleşik bir şekilde çalışır. En iyi koruma değerini elde etmek için, Microsoft Defender Virüsten Koruma tutmalı. Bkz[. Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetme ve taban çizgilerini uygulama](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="why-do-we-need-cloud-protection-maps-on"></a>Neden bulut koruması (HARITALAR) açık olarak ihtiyacımız var?

Cihazda özelliği açmak için bulut koruması gereklidir. Bulut koruması, [davranışsal ve](microsoft-defender-endpoint.md) cihaz öğrenme modellerinin yanı sıra güvenlik zekası ve derinliğimizi temel alarak en yeni ve en mükemmel korumayı uç nokta için Defender'a sunar.

### <a name="what-is-the-difference-between-active-and-passive-mode"></a>Etkin ve pasif modu arasındaki fark nedir?

Microsoft Defender Virüsten Koruma etkin moddayken Windows 10, Windows 11, Windows Server, sürüm 1803 veya sonraki bir sürümü, Windows Server 2019 veya Windows Server 2022 çalıştıran uç noktalar için, cihazda birincil virüsten koruma yazılımı olarak kullanılır . Pasif modunda çalışırken, Microsoft Defender Virüsten Koruma birincil virüsten koruma ürünü değildir. Bu durumda, tehditlere gerçek zamanlı olarak Microsoft Defender Virüsten Koruma düzeltme olmaz.

> [!NOTE]
> Microsoft Defender Virüsten Koruma edilgen modda ancak cihaz pasif moduna Uç Nokta için Microsoft Defender.

Daha fazla bilgi için uyumluluk [Microsoft Defender Virüsten Koruma bakın](microsoft-defender-antivirus-compatibility.md).

### <a name="how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode"></a>Nasıl yaparım? veya pasif Microsoft Defender Virüsten Koruma modunda olduğunu doğrulamak ister misiniz?

Etkin veya Microsoft Defender Virüsten Koruma modunda çalıştırıp çalışmadıy olduğunu doğrulamak için, Komut İstemi veya PowerShell'i çalışan bir Windows.

|Yöntem|Yordam|
|---|---|
|PowerShell|1. Metni Başlat menüsü, yazmaya başlayın `PowerShell`ve sonuçlarda Windows PowerShell'yi açın.<br/><br/>2. yazın `Get-MpComputerStatus`.<br/><br/>3. Sonuç listesinde, **AMRunningMode** satırına aşağıdaki değerlerden birini bakın:<br/>- `Normal`<br/>- `Passive Mode`<br/><br/>Daha fazla bilgi edinmek için [bkz. Get-MpComp birStatus](/powershell/module/defender/get-mpcomputerstatus).|
|Komut İstemi|1. Metni seçin Başlat menüsü yazmaya başlayın `Command Prompt`ve ardından sonuçlarda Windows İstemi'ne yazın.<br/><br/>2. yazın `sc query windefend`.<br/><br/>3. Sonuç listesinde, **DURUM satırına** göre hizmetin çalışıyor olduğunu onaylayın. |

### <a name="how-do-i-confirm-that-edr-in-block-mode-is-turned-on-with-microsoft-defender-antivirus-in-passive-mode"></a>Nasıl yaparım? modundayken EDR modundayken e-postanın pasif modunda Microsoft Defender Virüsten Koruma onaylayabilir misiniz?

Engelleme modundayken engelleme modundaki EDR'nin açık olduğunu doğrulamak için PowerShell'Microsoft Defender Virüsten Koruma edilgen modunda çalışır.

1. Metni Başlat menüsü, yazmaya başlayın `PowerShell`ve ardından Windows PowerShell metni açın.

2. `Get-MPComputerStatus|select AMRunningMode` yazın.

3. sonucun görüntülendiğinden `EDR Block Mode`onaylayın.

   > [!TIP]
   > Etkin Microsoft Defender Virüsten Koruma moddayken, yerine 'i `Normal` gösterir`EDR Block Mode`. Daha fazla bilgi edinmek için [bkz. Get-MpComp birStatus](/powershell/module/defender/get-mpcomputerstatus).

### <a name="is-edr-in-block-mode-supported-on-windows-server-2016-and-windows-server-2012-r2"></a>EDR ve R2'de blok modunda Windows Server 2016 Windows Server 2012 desteklenmiş mi?

Etkin Microsoft Defender Virüsten Koruma veya pasif modunda çalışıyorsa, EDR engelleme modundaki kodlar aşağıdaki Çalışma Saatlerinin Windows:

- Windows 11
- Windows 10 (tüm sürümler)
- Windows, sürüm 1803 veya daha yenisi 
- Windows Server 2022
- Windows Server 2019 
- Windows Server 2016 ve Windows Server 2012 R2 (yeni birleşik [istemci çözümüyle](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview))

Windows Server 2016 ve [](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview) Windows Server 2012 R2 için yeni birleşik istemci çözümüyle, EDR modunda veya etkin modda engelleme modunda çalıştırabilirsiniz.

> [!NOTE]
> Windows Server 2016 için Windows Server 2012 R2'nin onboard [Windows sunucularında](configure-server-endpoints.md) verilen yönergeler kullanılarak hazır olması gerekir. 

### <a name="how-much-time-does-it-take-for-edr-in-block-mode-to-be-disabled"></a>Blok modundaki bir EDR devre dışı bırakılırken ne kadar zaman alır?

Bu özelliği engelleme EDR devre dışı bırakmayı seçerseniz, sistemin bu özelliği devre dışı bırakması 30 dakika kadar sürebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Teknik Community blogu: Engelleme EDR ile ilgili tanıtım: Parçaların saldırılarını durdurma](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/introducing-edr-in-block-mode-stopping-attacks-in-their-tracks/ba-p/1596617)

- [Davranışsal engelleme ve kapsama](behavioral-blocking-containment.md)
