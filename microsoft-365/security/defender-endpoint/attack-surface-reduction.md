---
title: Kötü amaçlı yazılım bulaşmasını önlemek için saldırı yüzeyi azaltma kurallarını kullanma
description: Saldırı yüzeyi azaltma kuralları, uygulamalara ve betiklere kötü amaçlı yazılım bulaştırmak için açıklardan yararlanmanın önlenmesine yardımcı olabilir.
keywords: Saldırı yüzeyi azaltma kuralları, asr, kalçalar, konak izinsiz giriş önleme sistemi, koruma kuralları, anti-exploit, antiexploit, exploit, enfeksiyon önleme, Uç Nokta için Microsoft Defender
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
ms.custom:
- asr
- admindeeplinkDEFENDER
ms.technology: mde
ms.topic: article
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.openlocfilehash: a5ca2613028e892229da1888c6176cb729e0cf1b
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65469590"
---
# <a name="attack-surface-reduction-rules-overview"></a>Saldırı yüzeyi azaltma kurallarına genel bakış

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

## <a name="why-attack-surface-reduction-rules-are-important"></a>Saldırı yüzeyi azaltma kuralları neden önemlidir?

Kuruluşunuzun saldırı yüzeyi, bir saldırganın kuruluşunuzun cihazlarını veya ağlarını tehlikeye atabileceği tüm yerleri içerir. Saldırı yüzeyinizi azaltmak, kuruluşunuzun cihazlarını ve ağını korumak anlamına gelir ve bu da saldırganlara saldırı gerçekleştirmenin daha az yolunu bırakır. Uç Nokta için Microsoft Defender'de saldırı yüzeyi azaltma kurallarının yapılandırılması yardımcı olabilir!

Saldırı yüzeyi azaltma kuralları aşağıdakiler gibi belirli yazılım davranışlarını hedefler:

- Dosyaları indirmeye veya çalıştırmaya çalışan yürütülebilir dosyaları ve betikleri başlatma
- Karartılmış veya başka bir şekilde şüpheli betikleri çalıştırma
- Uygulamaların genellikle normal gündelik iş sırasında başlatmayabilecekleri davranışlar gerçekleştirme

Bu tür yazılım davranışları bazen meşru uygulamalarda görülür. Ancak bu davranışlar genellikle kötü amaçlı yazılım aracılığıyla saldırganlar tarafından yaygın olarak kötüye kullanıldıklarından riskli olarak kabul edilir. Saldırı yüzeyi azaltma kuralları yazılım tabanlı riskli davranışları kısıtlayabilir ve kuruluşunuzun güvende kalmasına yardımcı olabilir.

Saldırı yüzeyi azaltma kurallarını yapılandırma hakkında daha fazla bilgi için bkz. [Saldırı yüzeyi azaltma kurallarını etkinleştirme](enable-attack-surface-reduction.md).

## <a name="assess-rule-impact-before-deployment"></a>Dağıtımdan önce kural etkisini değerlendirme

Bir saldırı yüzeyi azaltma kuralının ağınızı nasıl etkileyebileceğini değerlendirmek için bu kuralın güvenlik önerisini [Tehdit ve Güvenlik Açığı Yönetimi](/windows/security/threat-protection/#tvm) açabilirsiniz.

:::image type="content" source="images/asrrecommendation.png" alt-text="ASR önerisi" lightbox="images/asrrecommendation.png":::

Öneri ayrıntıları bölmesinde, cihazlarınızın hangi yüzdesinin üretkenliği olumsuz etkilemeden engelleme modunda kuralı etkinleştiren yeni bir ilkeyi kabul edebildiğini belirlemek için kullanıcı etkisini denetleyin.

Desteklenen işletim sistemleri ve ek gereksinim bilgileri hakkında bilgi için "Saldırı yüzeyi azaltma kurallarını etkinleştirme" makalesindeki [Gereksinimler](enable-attack-surface-reduction.md#requirements) bölümüne bakın.

## <a name="audit-mode-for-evaluation"></a>Değerlendirme için denetim modu

Saldırı yüzeyi azaltma kurallarının etkinse kuruluşunuzu nasıl etkileyeceğini değerlendirmek için [denetim modunu](audit-windows-defender.md) kullanın. İlk olarak tüm kuralları denetim modunda çalıştırarak bunların iş kolu uygulamalarınızı nasıl etkilediğini anlayabilirsiniz. Birçok iş kolu uygulaması sınırlı güvenlik kaygılarıyla yazılır ve kötü amaçlı yazılımlara benzer şekilde görevler gerçekleştirebilir. Denetim verilerini izleyerek ve gerekli uygulamalar için [dışlamalar ekleyerek](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) , üretkenliği azaltmadan saldırı yüzeyi azaltma kurallarını dağıtabilirsiniz.

## <a name="warn-mode-for-users"></a>Kullanıcılar için uyarı modu

(**YENİ**!) Uyarı modu özelliklerinden önce, etkinleştirilen saldırı yüzeyi azaltma kuralları denetim moduna veya blok moduna ayarlanabilir. Yeni uyarı moduyla, içerik bir saldırı yüzeyi azaltma kuralı tarafından her engellendiğinde, kullanıcılar içeriğin engellendiğini belirten bir iletişim kutusu görür. İletişim kutusu ayrıca kullanıcıya içeriğin engellemesini kaldırma seçeneği sunar. Kullanıcı daha sonra eylemini yeniden deneyebilir ve işlem tamamlar. Kullanıcı içeriğin engellemesini kaldırdığında, içerik 24 saat boyunca engellenmemiş olarak kalır ve ardından engelleme özgeçmişleri devam eder.

Uyarı modu, kuruluşunuzun kullanıcıların görevlerini gerçekleştirmek için ihtiyaç duydukları içeriğe erişmesini engellemeden saldırı yüzeyi azaltma kurallarının mevcut olmasını sağlar.

### <a name="requirements-for-warn-mode-to-work"></a>Uyarı modunun çalışması için gereksinimler

Uyarı modu, aşağıdaki Windows sürümlerini çalıştıran cihazlarda desteklenir:

- [Windows 10, sürüm 1809](/windows/whats-new/whats-new-windows-10-version-1809) veya üzeri
- Windows 11
- [Windows Server, sürüm 1809](/windows-server/get-started/whats-new-in-windows-server-1809) veya üzeri

Microsoft Defender Virüsten Koruma [Etkin modda](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility#functionality-and-features-available-in-each-state) gerçek zamanlı koruma ile çalışıyor olmalıdır.

Ayrıca[, Microsoft Defender Virüsten Koruma ve kötü amaçlı yazılımdan koruma güncelleştirmelerinin](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions) yüklendiğinden emin olun.

- En düşük platform sürümü gereksinimi: `4.18.2008.9`
- En düşük altyapı sürümü gereksinimi: `1.1.17400.5`

Daha fazla bilgi edinmek ve güncelleştirmelerinizi almak için bkz. [Microsoft Defender kötü amaçlı yazılımdan koruma platformu için güncelleştirme](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform).

### <a name="cases-where-warn-mode-is-not-supported"></a>Uyarı modunun desteklenmediği durumlar

Uyarı modu, Microsoft Endpoint Manager'da yapılandırdığınızda üç saldırı yüzeyi azaltma kuralı için desteklenmez. (Saldırı yüzeyi azaltma kurallarınızı yapılandırmak için grup ilkesi kullanıyorsanız uyarı modu desteklenir.) uyarı modunu Microsoft Endpoint Manager yapılandırırken desteklemeyen üç kural şunlardır:

- [JavaScript veya VBScript'in indirilen yürütülebilir içeriği](attack-surface-reduction-rules-reference.md#block-javascript-or-vbscript-from-launching-downloaded-executable-content) (GUID `d3e037e1-3eb8-44c8-a917-57927947596d`) başlatmasını engelleme
- WMI olay aboneliği (GUID`e6db77e5-3df2-4cf1-b95a-636979351e5b`) [aracılığıyla kalıcılığı engelleme](attack-surface-reduction-rules-reference.md#block-persistence-through-wmi-event-subscription)
- [Fidye yazılımına karşı gelişmiş koruma kullanma](attack-surface-reduction-rules-reference.md#use-advanced-protection-against-ransomware) (GUID `c1db55ab-c21a-4637-bb3f-a12568109d35`)

Ayrıca uyarı modu, Windows eski sürümlerini çalıştıran cihazlarda desteklenmez. Bu gibi durumlarda, uyarı modunda çalışacak şekilde yapılandırılmış saldırı yüzeyi azaltma kuralları blok modunda çalışır.

## <a name="notifications-and-alerts"></a>Bildirimler ve uyarılar

Bir saldırı yüzeyi azaltma kuralı tetiklendiğinde cihazda bir bildirim görüntülenir. Bildirimi şirketinizin ayrıntıları ve iletişim bilgileriyle [özelleştirebilirsiniz](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) .

Ayrıca, belirli saldırı yüzeyi azaltma kuralları tetiklendiğinde uyarılar oluşturulur.

Bildirimler ve oluşturulan tüm uyarılar <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalında</a> görüntülenebilir.

Bildirim ve uyarı işlevselliği hakkında belirli ayrıntılar için **bkz. Saldırı yüzeyi azaltma kuralları başvurusu** makalesindeki [Kural uyarı ve bildirim ayrıntılarına](attack-surface-reduction-rules-reference.md#per-rule-alert-and-notification-details) göre.

## <a name="advanced-hunting-and-attack-surface-reduction-events"></a>Gelişmiş avcılık ve saldırı yüzeyi azaltma olayları

Saldırı yüzeyi azaltma olaylarını görüntülemek için gelişmiş avcılığı kullanabilirsiniz. Gelen verilerin hacmini kolaylaştırmak için gelişmiş avcılık ile yalnızca her saat için benzersiz işlemler görüntülenebilir. Saldırı yüzeyini azaltma olayının zamanı, olay bir saat içinde ilk kez görülür.

Örneğin, saat 14:00 sırasında 10 cihazda bir saldırı yüzeyi azaltma olayının gerçekleştiğini varsayalım. İlk olayın 2:15 ve sonuncunun 2:45'te gerçekleştiğini varsayalım. Gelişmiş avcılık sayesinde bu olayın bir örneğini görürsünüz (aslında 10 cihazda gerçekleşse de) ve zaman damgası 14:15 olacaktır.

Gelişmiş avcılık hakkında daha fazla bilgi için bkz. [Gelişmiş avcılık ile tehditleri proaktif olarak avlama](advanced-hunting-overview.md).

## <a name="attack-surface-reduction-features-across-windows-versions"></a>Windows sürümlerde saldırı yüzeyi azaltma özellikleri

aşağıdaki Windows sürümlerinden herhangi birini çalıştıran cihazlar için saldırı yüzeyi azaltma kuralları ayarlayabilirsiniz:

- Windows 10 Pro, [sürüm 1709](/windows/whats-new/whats-new-windows-10-version-1709) veya üzeri
- Windows 10 Enterprise, [sürüm 1709](/windows/whats-new/whats-new-windows-10-version-1709) veya üzeri
- Windows Sunucusu, [sürüm 1803 (Altı Aylık Kanal)](/windows-server/get-started/whats-new-in-windows-server-1803) veya üzeri
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh801901(v=ws.11))

  >[!NOTE]
  >Windows Server 2016 ve Windows Server 2012 R2'nin bu özelliğin çalışması için [Windows sunucularında ekleme](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) yönergeleri kullanılarak eklenmelidir.

Saldırı yüzeyi azaltma kuralları [Windows E5 lisansı](/windows/deployment/deploy-enterprise-licenses) gerektirmese de, E5 Windows sahipseniz gelişmiş yönetim özelliklerine sahip olursunuz. Yalnızca Windows E5'te kullanılabilen gelişmiş özellikler şunlardır:

- [Uç Nokta için Defender'da](microsoft-defender-endpoint.md) kullanılabilen izleme, analiz ve iş akışları
- [Microsoft 365 Defender'deki](/microsoft-365/security/defender/overview-security-center) raporlama ve yapılandırma özellikleri.

Bu gelişmiş özellikler Windows Professional veya Windows E3 lisansıyla kullanılamaz. Ancak, bu lisanslara sahipseniz saldırı yüzeyi azaltma kuralı olaylarınızı gözden geçirmek için Olay Görüntüleyicisi ve Microsoft Defender Virüsten Koruma günlüklerini kullanabilirsiniz.

## <a name="review-attack-surface-reduction-events-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında saldırı yüzeyi azaltma olaylarını gözden geçirme

Uç Nokta için Defender, uyarı araştırma senaryolarının bir parçası olarak olaylar ve bloklar için ayrıntılı raporlama sağlar.

[Gelişmiş avcılığı](/microsoft-365/security/defender/advanced-hunting-query-language) kullanarak [Microsoft 365 Defender'da](microsoft-defender-endpoint.md) Uç Nokta için Defender verilerini sorgulayabilirsiniz. 

Aşağıda örnek bir sorgu verilmiştir:

```kusto
DeviceEvents
| where ActionType startswith 'Asr'
```

## <a name="review-attack-surface-reduction-events-in-windows-event-viewer"></a>Windows Olay Görüntüleyicisi'da saldırı yüzeyi azaltma olaylarını gözden geçirme

Saldırı yüzeyi azaltma kuralları tarafından oluşturulan olayları görüntülemek için Windows olay günlüğünü gözden geçirebilirsiniz:

1. [Değerlendirme Paketi'ni](https://aka.ms/mp7z2w) indirin *vecfa-events.xmldosyayı* cihazda kolayca erişilebilen bir konuma ayıklayın.

2. Windows Olay Görüntüleyicisi açmak için *Başlat menüsü* Olay Görüntüleyicisi sözcükleri girin.

3. **Eylemler'in** altında **Özel görünümü içeri aktar...** öğesini seçin.

4. Ayıklandığı konumdan *cfa-events.xml* dosyayı seçin. Alternatif olarak [, XML'yi doğrudan kopyalayın](event-views.md).

5. **Tamam**'ı seçin.

Olayları yalnızca denetimli klasör erişimiyle ilgili olan aşağıdaki olayları gösterecek şekilde filtreleyen özel bir görünüm oluşturabilirsiniz:

|Olay Kimliği|Açıklama|
|---|---|
|5007|Ayarlar değiştirildiğinde gerçekleşen olay|
|1121|Kuralın Blok modunda tetiklenmesi olayı|
|1122|Denetim modunda kural tetiklendiğinde gerçekleşen olay|

Olay günlüğünde saldırı yüzeyi azaltma olayları için listelenen "altyapı sürümü", işletim sistemi tarafından değil Uç Nokta için Defender tarafından oluşturulur. Uç Nokta için Defender Windows 10 ve Windows 11 ile tümleşiktir, bu nedenle bu özellik Windows 10 veya Windows 11 yüklü tüm cihazlarda çalışır.

> [!TIP]
> Diğer platformlar için Antivirüs ile ilgili bilgi arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)
