---
title: Blok modunda uç nokta algılama ve yanıt
description: Blok modunda uç noktada algılama ve yanıtlama hakkında bilgi edinin
keywords: blok modunda Uç Nokta için Microsoft Defender, mde, EDR, pasif mod engelleme
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
ms.date: 04/04/2022
ms.collection: m365-security-compliance
ms.technology: mde
ms.openlocfilehash: c8b3016517393b473bcae664a6044098e04ebf6d
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65623588"
---
# <a name="endpoint-detection-and-response-edr-in-block-mode"></a>Blok modunda uç nokta algılama ve yanıt (EDR)

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-edr-in-block-mode"></a>Blok modunda EDR nedir?

Blok modunda [uç nokta algılama ve yanıt](overview-endpoint-detection-response.md) (EDR), Microsoft Defender Virüsten Koruma birincil virüsten koruma ürünü olmadığında ve pasif modda çalıştığında kötü amaçlı yapıtlara karşı ek koruma sağlar. Blok modundaki EDR, EDR özellikleri tarafından algılanan kötü amaçlı yapıtları düzeltmek için arka planda çalışır. Bu tür yapıtlar birincil, Microsoft dışı virüsten koruma ürünü tarafından kaçırılmış olabilir. Microsoft Defender Virüsten Koruma birincil virüsten koruma yazılımı olarak çalıştıran cihazlar için blok modundaki EDR, Microsoft Defender Virüsten Koruma ihlal sonrası, davranışsal EDR algılamalarında otomatik eylemler gerçekleştirmesine izin vererek ek bir savunma katmanı sağlar.

> [!IMPORTANT]
> Blok modunda EDR, Microsoft Defender Virüsten Koruma gerçek zamanlı koruma etkinleştirildiğinde kullanılabilen tüm korumayı sağlamaz. Microsoft Defender Virüsten Koruma etkin virüsten koruma çözümüne bağımlı olan tüm özellikler, aşağıdaki önemli örnekler de dahil olmak üzere çalışmaz:
>
> - Microsoft Defender Virüsten Koruma pasif moddayken, erişim içi tarama da dahil olmak üzere gerçek zamanlı koruma kullanılamaz. Gerçek zamanlı koruma ilkesi ayarları hakkında daha fazla bilgi edinmek için bkz. **[Microsoft Defender Virüsten Koruma her zaman açık korumayı etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)**.
>
> - **[Ağ koruması](network-protection.md)** ve **[saldırı yüzeyi azaltma kuralları](attack-surface-reduction.md)** gibi özellikler yalnızca Microsoft Defender Virüsten Koruma etkin modda çalışırken kullanılabilir.
>
> Microsoft dışı virüsten koruma çözümünüzün bu özellikleri sağlaması beklenir.

Blok modundaki EDR [tehdit & güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md) ile tümleşiktir. Kuruluşunuzun güvenlik ekibi, henüz etkinleştirilmemişse EDR blok modunda açması için bir [güvenlik önerisi](tvm-security-recommendation.md) alır.

:::image type="content" source="images/edrblockmode-TVMrecommendation.png" alt-text="Blok modunda EDR açma önerisi" lightbox="images/edrblockmode-TVMrecommendation.png":::

> [!TIP]
> En iyi korumayı elde etmek için **[Uç Nokta için Microsoft Defender taban çizgilerini dağıttığınıza](configure-machines-security-baseline.md)** emin olun.

Blok modunda uç noktada algılama ve yanıtlama (EDR) açmanın, davranış engellemeyi etkinleştirmenin ve ihlal öncesinden ihlal sonrası aşamalara kadar her aşamada engellemeyi neden ve nasıl açacağınızı öğrenmek için bu videoyu izleyin. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4HjW2]

## <a name="what-happens-when-something-is-detected"></a>Bir şey algılandığında ne olur?

Blok modunda EDR açık olduğunda ve kötü amaçlı bir yapıt algılandığında, bu yapıtı engeller ve düzelter Uç Nokta için Microsoft Defender. Güvenlik operasyonları ekibiniz algılama durumunu [İşlem merkezinde](respond-machine-alerts.md#check-activity-details-in-action-center) **Engellendi** veya **Engellendi** olarak görür ve tamamlanmış eylemler olarak listelenir.

Aşağıdaki görüntüde, blok modunda EDR aracılığıyla algılanan ve engellenen istenmeyen yazılımların bir örneği gösterilmektedir:

:::image type="content" source="images/edr-in-block-mode-detection.png" alt-text="Blok modunda EDR algılama" lightbox="images/edr-in-block-mode-detection.png":::


## <a name="enable-edr-in-block-mode"></a>Blok modunda EDR etkinleştirme

> [!IMPORTANT]
> Platform sürümü 4.18.2202.X'den başlayarak, artık Intune CSP'leri kullanarak belirli cihaz gruplarını hedeflemek için blok modunda EDR ayarlayabilirsiniz. Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalında</a> kiracı genelinde blok modunda EDR ayarlamaya devam edebilirsiniz. Blok modunda EDR öncelikle pasif modda Microsoft Defender Virüsten Koruma çalıştıran cihazlar için önerilir (cihazda Microsoft dışı bir virüsten koruma çözümü yüklü ve etkindir). 

> [!TIP]
> Blok modunda EDR açmadan önce [gereksinimlerin karşılandığından](#requirements-for-edr-in-block-mode) emin olun.

### <a name="security-portal"></a>Güvenlik Portalı 

1. Microsoft 365 Defender portalına ([https://security.microsoft.com/](https://security.microsoft.com/)) gidin ve oturum açın.

2. **Ayarlar** \> **Uç Noktaları** \> **Genel** \> **Gelişmiş özellikler'i** seçin.

3. Ekranı aşağı kaydırın ve ardından **Blok modunda EDR etkinleştir'i** açın.

### <a name="intune"></a>Intune

Intune'da özel ilke oluşturmak için bkz. [Intune aracılığıyla csp'yi hedeflemek için OMA-URIs dağıtma ve şirket içiyle karşılaştırma](/troubleshoot/mem/intune/deploy-oma-uris-to-target-csp-via-intune).

Blok modunda EDR için kullanılan Defender CSP hakkında daha fazla bilgi için [Defender CSP'nin](/windows/client-management/mdm/defender-csp) altındaki "Yapılandırma/PassiveRemediation" bölümüne bakın.


## <a name="requirements-for-edr-in-block-mode"></a>Blok modunda EDR gereksinimleri

Aşağıdaki tabloda blok modundaki EDR gereksinimleri listeleniyor:

|Gereksinim|Ayrıntılar|
|---|---|
|İzinler|[Azure Active Directory'da](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal) Genel Yönetici veya Güvenlik Yöneticisi rolü atanmış olmalıdır. Daha fazla bilgi için bkz. [Temel izinler](basic-permissions.md).|
|İşletim sistemi|Cihazların aşağıdaki Windows sürümlerinden birini çalıştırıyor olması gerekir: <br/>- Windows 11 <br/>- Windows 10 (tüm sürümler)<br/>- Windows Server 2022 <br/>- Windows Server 2019<br/>- Windows Sunucusu, sürüm 1803 veya üzeri<br/>- R2 Windows Server 2016 ve Windows Server 2012 ([yeni birleşik istemci çözümüyle](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution))<sup>[[1](#fn1)]</sup>  |
|Uç Nokta için Microsoft Defender|Cihazların Uç Nokta için Defender'a eklenmelidir. Aşağıdaki makalelere bakın: <br/>- [Uç Nokta için Microsoft Defender için en düşük gereksinimler](minimum-requirements.md)<br/>- [Cihazları ekleme ve Uç Nokta için Microsoft Defender özelliklerini yapılandırma](onboard-configure.md)<br/>- [Uç Nokta için Defender hizmetine Windows sunucuları ekleme](configure-server-endpoints.md)<br/>- [Modern birleşik çözümde yeni Windows Server 2012 R2 ve 2016 işlevselliği (Önizleme)](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution) |
|Microsoft Defender Virüsten Koruma|Cihazların Microsoft Defender Virüsten Koruma yüklü olması ve etkin modda veya pasif modda çalıştırılması gerekir. [Microsoft Defender Virüsten Koruma etkin veya pasif modda olduğunu onaylayın](#how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode).|
|Bulut tabanlı koruma|Microsoft Defender Virüsten Koruma[, bulut tabanlı koruma etkinleştirilecek](enable-cloud-protection-microsoft-defender-antivirus.md) şekilde yapılandırılmalıdır.|
|Microsoft Defender Virüsten Koruma platformu|Cihazların güncel olması gerekir. Onaylamak için PowerShell kullanarak [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) cmdlet'ini yönetici olarak çalıştırın. **AMProductVersion** satırında **4.18.2001.10** veya üzerini görmeniz gerekir. <p> Daha fazla bilgi için [Microsoft Defender Virüsten Koruma güncelleştirmelerine bakın ve temelleri uygulayın](manage-updates-baselines-microsoft-defender-antivirus.md).|
|Microsoft Defender Virüsten Koruma altyapısı|Cihazların güncel olması gerekir. Onaylamak için PowerShell kullanarak [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) cmdlet'ini yönetici olarak çalıştırın. **AMEngineVersion** satırında **1.1.16700.2** veya üzerini görmeniz gerekir. <p> Daha fazla bilgi için [Microsoft Defender Virüsten Koruma güncelleştirmelerine bakın ve temelleri uygulayın](manage-updates-baselines-microsoft-defender-antivirus.md).|

(<a id="fn1">1</a>) Bkz. [EDR Windows Server 2016 ve Windows Server 2012 R2'de blok modunda destekleniyor mu?](#is-edr-in-block-mode-supported-on-windows-server-2016-and-windows-server-2012-r2)

> [!IMPORTANT]
> En iyi koruma değerini elde etmek için virüsten koruma çözümünüzün düzenli güncelleştirmeleri ve temel özellikleri alacak şekilde yapılandırıldığından ve [dışlamalarınızın yapılandırıldığından](configure-exclusions-microsoft-defender-antivirus.md) emin olun. blok modunda EDR, Microsoft Defender Virüsten Koruma için tanımlanan dışlamalara saygı gösterir, ancak Uç Nokta için Microsoft Defender için tanımlanan [göstergelere](manage-indicators.md) dikkat etmemektedir.

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="can-i-specify-exclusions-for-edr-in-block-mode"></a>Blok modunda EDR için dışlamalar belirtebilir miyim?

Hatalı pozitif sonuç aldığınızda, dosyayı [Microsoft Güvenlik Zekası gönderim sitesinde](https://www.microsoft.com/en-us/wdsi/filesubmission) analiz için gönderebilirsiniz.

ayrıca Microsoft Defender Virüsten Koruma için bir dışlama tanımlayabilirsiniz. Bkz[. Microsoft Defender Virüsten Koruma taramaları için dışlamaları yapılandırma ve doğrulama](configure-exclusions-microsoft-defender-antivirus.md).

### <a name="do-i-need-to-turn-edr-in-block-mode-on-if-i-have-microsoft-defender-antivirus-running-on-devices"></a>Cihazlarda çalışan Microsoft Defender Virüsten Koruma EDR blok modunda açmam gerekiyor mu?

Blok modunda EDR birincil amacı, Microsoft dışı bir virüsten koruma ürünü tarafından kaçırılan ihlal sonrası algılamaları düzeltmektir. Microsoft Defender Virüsten Koruma etkin moddayken blok modunda EDR etkinleştirmenin en düşük avantajı vardır çünkü gerçek zamanlı korumanın önce algılamaları yakalaması ve düzeltmesi beklenir. Virüsten Koruma için Microsoft Defender'ın pasif modda çalıştığı uç noktalarda blok modunda EDR etkinleştirmenizi öneririz. EDR algılamaları [PUA koruması](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) veya blok modunda [otomatik araştırma & düzeltme özellikleriyle](automated-investigations.md) otomatik olarak düzeltilebilir.

### <a name="will-edr-in-block-mode-affect-a-users-antivirus-protection"></a>Blok modundaki EDR kullanıcının virüsten korumasını etkiler mi?

Blok modundaki EDR, kullanıcıların cihazlarında çalışan üçüncü taraf virüsten korumasını etkilemez. Blok modunda EDR, birincil virüsten koruma çözümü bir şeyi kaçırırsa veya ihlal sonrası algılama varsa çalışır. Blok modundaki EDR pasif modda Microsoft Defender Virüsten Koruma gibi çalışır, ancak blok modundaki EDR algılanan kötü amaçlı yapıtları veya davranışları da engeller ve düzelter.

### <a name="why-do-i-need-to-keep-microsoft-defender-antivirus-up-to-date"></a>Microsoft Defender Virüsten Koruma neden güncel tutmam gerekiyor?

Microsoft Defender Virüsten Koruma kötü amaçlı öğeleri algılayıp düzeltdiğinden, bu öğeleri güncel tutmak önemlidir. Blok modundaki EDR etkili olması için en son cihaz öğrenme modellerini, davranış algılamalarını ve buluşsal yöntemleri kullanır. [Uç Nokta için Defender](microsoft-defender-endpoint.md) özellik yığını tümleşik bir şekilde çalışır. En iyi koruma değerini elde etmek için Microsoft Defender Virüsten Koruma güncel tutmanız gerekir. Bkz. [Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetme ve temelleri uygulama](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="why-do-we-need-cloud-protection-maps-on"></a>Neden bulut korumasına (MAPS) ihtiyacımız var?

Cihazdaki özelliği açmak için bulut koruması gerekir. Bulut koruması [, Uç Nokta için Defender'ın](microsoft-defender-endpoint.md) davranış ve cihaz öğrenmesi modellerinin yanı sıra güvenlik zekasının genişliğine ve derinliğine göre en son ve en büyük korumayı sunmasını sağlar.

### <a name="what-is-the-difference-between-active-and-passive-mode"></a>Etkin ve pasif mod arasındaki fark nedir?

Windows 10, Windows 11, Windows Server, sürüm 1803 veya üzeri, Windows Server 2019 veya Windows Server 2022 çalıştıran uç noktalar için, Microsoft Defender Virüsten Koruma etkin moddayken cihazda birincil virüsten koruma olarak kullanılır . Pasif modda çalışırken, Microsoft Defender Virüsten Koruma birincil virüsten koruma ürünü değildir. Bu durumda tehditler gerçek zamanlı olarak Microsoft Defender Virüsten Koruma tarafından düzeltilmemektedir.

> [!NOTE]
> Microsoft Defender Virüsten Koruma yalnızca cihaz Uç Nokta için Microsoft Defender eklendiğinde pasif modda çalıştırılabilir.

Daha fazla bilgi için bkz. [uyumluluk Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-compatibility.md).

### <a name="how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode"></a>Microsoft Defender Virüsten Koruma etkin veya pasif modda olduğunu onaylıyor Nasıl yaparım??

Microsoft Defender Virüsten Koruma etkin veya pasif modda çalışıp çalışmadığını onaylamak için, Windows çalıştıran bir cihazda Komut İstemi veya PowerShell kullanabilirsiniz.

|Yöntem|Yordam|
|---|---|
|PowerShell|1. Başlat menüsü seçin, yazmaya `PowerShell`başlayın ve sonuçlarda Windows PowerShell açın.<br/><br/>2. yazın `Get-MpComputerStatus`.<br/><br/>3. Sonuç listesinde, **AMRunningMode** satırında aşağıdaki değerlerden birini arayın:<br/>- `Normal`<br/>- `Passive Mode`<br/><br/>Daha fazla bilgi için bkz [. Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).|
|Komut|1. Başlat menüsü seçin, yazmaya `Command Prompt`başlayın ve ardından sonuçlarda komut istemini Windows açın.<br/><br/>2. yazın `sc query windefend`.<br/><br/>3. Sonuç listesinde, **STATE** satırında hizmetin çalıştığını onaylayın. |

### <a name="how-do-i-confirm-that-edr-in-block-mode-is-turned-on-with-microsoft-defender-antivirus-in-passive-mode"></a>Blok modundaki EDR pasif modda Microsoft Defender Virüsten Koruma açık olduğunu onaylıyor Nasıl yaparım??

PowerShell'i kullanarak pasif modda çalışan Microsoft Defender Virüsten Koruma blok modundaki EDR açık olduğunu onaylayabilirsiniz.

1. Başlat menüsü seçin, yazmaya `PowerShell`başlayın ve sonuçlarda Windows PowerShell açın.

2. `Get-MPComputerStatus|select AMRunningMode` yazın.

3. sonucunun `EDR Block Mode`görüntülendiğini onaylayın.

   > [!TIP]
   > Microsoft Defender Virüsten Koruma etkin moddaysa yerine öğesini görürsünüz `Normal` `EDR Block Mode`. Daha fazla bilgi için bkz [. Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

### <a name="is-edr-in-block-mode-supported-on-windows-server-2016-and-windows-server-2012-r2"></a>Windows Server 2016 ve Windows Server 2012 R2'de blok modunda EDR destekleniyor mu?

Microsoft Defender Virüsten Koruma etkin modda veya pasif modda çalışıyorsa, blok modunda EDR aşağıdaki Windows sürümlerinde desteklenir:

- Windows 11
- Windows 10 (tüm sürümler)
- Windows Server, sürüm 1803 veya üzeri 
- Windows Server 2022
- Windows Server 2019 
- Windows Server 2016 ve Windows Server 2012 R2 ([yeni birleşik istemci çözümüyle](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution))

Windows Server 2016 ve Windows Server 2012 R2 için [yeni birleşik istemci çözümüyle](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution), EDR pasif modda veya etkin modda blok modunda çalıştırabilirsiniz.

> [!NOTE]
> Windows Server 2016 ve Windows Server 2012 R2, bu özelliğin çalışması için [Windows sunucuları ekleme](configure-server-endpoints.md) yönergeleri kullanılarak eklenmelidir. 

### <a name="how-much-time-does-it-take-for-edr-in-block-mode-to-be-disabled"></a>Blok modundaki EDR devre dışı bırakılması ne kadar sürer?

Blok modunda EDR devre dışı bırakmayı seçerseniz, sistemin bu özelliği devre dışı bırakması 30 dakika kadar sürebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Teknik Community blogu: Blok modunda EDR tanıtma: Saldırıyı kendi izlerinde durdurma](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/introducing-edr-in-block-mode-stopping-attacks-in-their-tracks/ba-p/1596617)

- [Davranışsal engelleme ve kapsama](behavioral-blocking-containment.md)
