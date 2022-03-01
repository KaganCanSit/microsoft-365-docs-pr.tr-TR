---
title: Kötü amaçlı yazılım bulaşmasını önlemek için saldırı yüzeyini azaltma kurallarını kullanın
description: Saldırı yüzeyini azaltma kuralları, istismarların cihazlara kötü amaçlı yazılım bulaştırmak için uygulama ve betik kullanmalarını önlemeye yardımcı olabilir.
keywords: Saldırı yüzeyini azaltma kuralları, asr, hip'ler, izinsiz giriş önleme sistemi, koruma kuralları, exploit önleme, izinsiz giriş önleme, exploit, bulaşma önleme, Uç nokta için Microsoft Defender
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
ms.collection: m365initiative-m365-defender
ms.date: 1/18/2022
ms.openlocfilehash: 3f3daaa068f067c8d4ffbbf40a4d8ba1d32d04b9
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011952"
---
# <a name="attack-surface-reduction-rules-overview"></a>Saldırı yüzeyini azaltma kurallarına genel bakış

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="why-attack-surface-reduction-rules-are-important"></a>Saldırı yüzeyini azaltma kuralları neden önemlidir?

Kuruluş saldırı yüzeyi, bir saldırganın, kuruluş cihazları veya ağlarının güvenliğini tehlikeye at olduğu tüm yerleri içerir. Saldırı yüzeyinizi azaltmak, kuruluş cihazlarınızı ve ağın korunması anlamına gelir. Bu, saldırganları saldırılar için daha az yol bırakır. Uç nokta için Microsoft Defender'da saldırı yüzeyini azaltma kurallarını yapılandırma size yardımcı olabilir!

Saldırı yüzeyini azaltma kuralları, şu tür belirli yazılım davranışlarını hedefler:

- Yürütülebilir dosyaları ve dosyaları indirmeye veya çalıştırmaya çalışan betikleri başlatma
- Obfuscated veya başka türlü şüpheli betikleri çalıştırma
- Uygulamaların çoğunlukla günlük normal çalışma sırasında başlatmayacakları davranışlar gerçekleştirme

Bu tür yazılım davranışları bazen yasal uygulamalarda görülebilir. Öte yandan, bu davranışlar genellikle kötü amaçlı yazılım yoluyla saldırganlar tarafından kötüye kullanım nedeniyle riskli olarak kabul edilir. Saldırı yüzeyini azaltma kuralları yazılım tabanlı riskli davranışları kısıtlar ve organizasyonlu güvende tutmanıza yardımcı olabilir.

Saldırı yüzeyini azaltma kurallarını yapılandırma hakkında daha fazla bilgi için saldırı yüzeyini [azaltma kurallarını etkinleştirme'ye bakın](enable-attack-surface-reduction.md).

## <a name="assess-rule-impact-before-deployment"></a>Dağıtımdan önce kuralın etkisini değerlendirme

Saldırı yüzeyini azaltma kuralının, ilgili kuralla ilgili güvenlik önerisini Bu kuralın güvenlik önerisini [Tehdit ve Güvenlik Açığı Yönetimi.](/windows/security/threat-protection/#tvm)

:::image type="content" source="images/asrrecommendation.png" alt-text="Saldırı yüzeyini azaltma kuralı için güvenlik reco.":::

Öneri ayrıntıları bölmesinde, kullanıcı etkisini kontrol edin ve cihazlarınızı yüzde kaçının, üretkenliği olumsuz etkilemeden engelleme modunda kuralı etkinleştiren yeni bir ilke kabul edileyeceğini belirler.

Desteklenen [işletim](enable-attack-surface-reduction.md#requirements) sistemleri ve ek gereksinim bilgileri hakkında bilgi için "Saldırı yüzeyini azaltma kurallarını etkinleştir" makalesinde Gereksinimler'e bakın.

## <a name="audit-mode-for-evaluation"></a>Değerlendirme için denetim modu

Saldırı [yüzeyini azaltma](audit-windows-defender.md) kurallarının etkinleştirildiyse kurumlarınızı nasıl etkileyeceğini değerlendirmek için denetim modunu kullanın. İş hattı uygulamalarınızı nasıl etkileyeceğini anlamak için önce tüm kuralları denetim modunda çalıştırın. Birçok iş hattı uygulaması sınırlı güvenlik kaygıları ile yazılmıştır ve bunlar, kötü amaçlı yazılıma benzeyen yollarla görevler gerçekleştirebilir. Denetim verilerini izleme ve gerekli [uygulamalar için dışlamalar](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) ekleyerek üretkenliği azaltmadan saldırı yüzeyini azaltma kurallarını dağıtabilirsiniz.

## <a name="warn-mode-for-users"></a>Kullanıcılar için Uyarı modu

(**Yenİ**!) Uyarı modu özellikleri önceden etkinleştirilen saldırı yüzeyini azaltma kuralları denetim modu veya engelleme modu olarak ayarlanmsıyor olabilir. Yeni uyarı moduyla, içerik saldırı yüzeyini azaltma kuralı tarafından her engellenmiş olduğunda, kullanıcılar içeriğin engellenmiş olduğunu belirten bir iletişim kutusu görebilir. İletişim kutusu, kullanıcıya içeriğin engellemesini kaldırma seçeneği de sunar. Kullanıcı bundan sonra eylemlerini yeniden sınr ve işlem tamamlanır. Kullanıcı içeriği engelini kaldırmışsa, içerik 24 saat boyunca engelsiz kalır ve ardından özgeçmişleri engeller.

Uyarı modu, kullanıcıların görevlerini yerine çekmek zorunda olduğu içeriğe erişmelerini engellemeden kuruluşa saldırı yüzeyini azaltma kuralları uygulamanıza yardımcı olur.

### <a name="requirements-for-warn-mode-to-work"></a>Uyarı modunun çalışması için gereksinimler

Uyarı modu, uygulamanın aşağıdaki sürümlerini çalıştıran Windows:

- [Windows 10, sürüm 1809](/windows/whats-new/whats-new-windows-10-version-1809) veya sonrası
- Windows 11
- [Windows Server, sürüm 1809](/windows-server/get-started/whats-new-in-windows-server-1809) veya sonrası

Microsoft Defender Virüsten Koruma modunda gerçek zamanlı korumayla çalışıyor [olması gerekir](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility#functionality-and-features-available-in-each-state).

Ayrıca, yeni ve [Microsoft Defender Virüsten Koruma yazılımdan koruma güncelleştirmelerinin yüklü](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions) olduğundan da emin olun.

- En düşük platform sürüm gereksinimi: `4.18.2008.9`
- En düşük altyapı sürüm gereksinimi: `1.1.17400.5`

Daha fazla bilgi almak ve güncelleştirmelerinizi almak için bkz. [Microsoft Defender kötü amaçlı yazılımdan koruma platformu için güncelleştirme](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform).

### <a name="cases-where-warn-mode-is-not-supported"></a>Uyarı modunun desteklen desteklemesi gereken durumlar

Uyarı modu, yeni bir uygulama içinde yapılandırıldığında üç saldırı yüzeyini azaltma kuralı Microsoft Endpoint Manager. (Saldırı yüzeyini azaltma kurallarınızı yapılandırmak için Grup İlkesi kullanırsanız uyarı modu de kullanılabilir.) Bu modda yapılandırıldığında uyarı modunu desteklemeen üç Microsoft Endpoint Manager aşağıdaki gibidir:

- [JavaScript veya VBScript'in indirilen yürütülebilir içeriği](attack-surface-reduction-rules-reference.md#block-javascript-or-vbscript-from-launching-downloaded-executable-content) (GUID) başlatmalarını `d3e037e1-3eb8-44c8-a917-57927947596d`engelleme
- [WMI olay aboneliği (GUID) aracılığıyla](attack-surface-reduction-rules-reference.md#block-persistence-through-wmi-event-subscription) kalıcılığı engelleme `e6db77e5-3df2-4cf1-b95a-636979351e5b`
- [Fidye yazılımlarına karşı gelişmiş koruma](attack-surface-reduction-rules-reference.md#use-advanced-protection-against-ransomware) (GUID) kullanın `c1db55ab-c21a-4637-bb3f-a12568109d35`

Ayrıca, bu modun daha eski sürümlerini çalıştıran cihazlarda uyarı modu Windows. Böyle durumlarda, uyarı modunda çalıştıracak şekilde yapılandırılan saldırı yüzeyini azaltma kuralları engelleme modunda çalışır.

## <a name="notifications-and-alerts"></a>Bildirimler ve uyarılar

Saldırı yüzeyini azaltma kuralı tetiklendiğinde cihazda bir bildirim görüntülenir. Bildirimi [şirket ayrıntılarınız](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) ve iletişim bilgileriyle özelleştirebilirsiniz.

Ayrıca, bazı saldırı yüzeyini azaltma kuralları tetiklendiğinde uyarılar oluşturulur.

Bildirimler ve oluşturulan tüm uyarılar portalda Microsoft 365 Defender<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">.</a>

Bildirim ve uyarı işlevselliği hakkında belirli ayrıntılar için bkz. [Kural](attack-surface-reduction-rules-reference.md#per-rule-alert-and-notification-details) başına uyarı ve bildirim ayrıntıları için Saldırı yüzeyini azaltma kuralları başvurusu **makalesinde bulabilirsiniz**.

## <a name="advanced-hunting-and-attack-surface-reduction-events"></a>Gelişmiş av ve saldırı yüzeyini azaltma etkinlikleri

Saldırı yüzeyini azaltma etkinliklerini görüntülemek için gelişmiş avı kullanabilirsiniz. Gelen verilerin hacmini basit hale getirmek için, gelişmiş arama özelliğiyle her saat için yalnızca benzersiz işlemler değiştirilebilir. Saldırı yüzeyini azaltma etkinliği, etkinliğin bir saat içinde ilk kez görülebilir olduğu zamandır.

Örneğin, 10 cihaz üzerinde saat 2:00 boyunca saldırı yüzeyini azaltma etkinliği olduğunu varsayalım. İlk olayın 2:15'te ve son olayın da 2:45'te olduğunu varsayalım. Gelişmiş avla bu etkinliğin bir örneğini (aslında 10 cihaz üzerinde olsa bile) ve zaman damgası 14:15'te yapılacaktır.

Gelişmiş arama hakkında daha fazla bilgi için bkz. Gelişmiş [avla tehditlere karşı önceden arama.](advanced-hunting-overview.md)

## <a name="attack-surface-reduction-features-across-windows-versions"></a>Farklı sürümlerde saldırı yüzeyini azaltma Windows özellikleri

Şu sürümlerden herhangi birini çalıştıran cihazlar için saldırı yüzeyini azaltma kuralları Windows:

- Windows 10 Pro, [sürüm 1709](/windows/whats-new/whats-new-windows-10-version-1709) veya sonrası
- Windows 10 Enterprise, [sürüm 1709](/windows/whats-new/whats-new-windows-10-version-1709) veya sonrası
- Windows, [sürüm 1803 (Yarı Yıllık Kanal) veya](/windows-server/get-started/whats-new-in-windows-server-1803) sonraki sürümler
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2012 R2](/win32/srvnodes/what-s-new-for-windows-server-2012-r2)

  >[!NOTE]
  >Windows Server 2016 ve Windows Server 2012 R2 için, bu özelliğin çalışması için [onboard Windows sunucularında](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) verilen yönergeler kullanılarak ekleme gerekiyor.

Saldırı yüzeyini azaltma kuralları için Windows E5 lisansı gerekmese de, [E5](/windows/deployment/deploy-enterprise-licenses) lisansınız Windows, gelişmiş yönetim özelliklerine sahip olursanız. Yalnızca E5'te kullanılabilen gelişmiş Windows - şunlardır:

- Uç Nokta için Defender'da bulunan izleme, çözümleme [ve iş akışları](microsoft-defender-endpoint.md)
- Raporlama ve yapılandırma özellikleri [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

Bu gelişmiş özellikler Windows Professional veya Windows E3 lisansı ile kullanılamaz. Ancak bu lisanslara sahipsinizse saldırı yüzeyini azaltma kuralı etkinliklerinizi gözden geçirmek için Olay Görüntüleyicisi'ni ve Microsoft Defender Virüsten Koruma günlüklerini kullanabilirsiniz.

## <a name="review-attack-surface-reduction-events-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında saldırı yüzeyini azaltma etkinliklerini gözden geçirme

Uç Nokta için Defender, uyarı soruşturma senaryolarının bir parçası olarak olaylar ve bloklar için ayrıntılı raporlama sağlar.

Gelişmiş av kullanarak Gelişmiş koruma kullanarak Microsoft 365 Defender [Defender'da](microsoft-defender-endpoint.md) Uç nokta verileri [için sorgu kullanabilirsiniz](/microsoft-365/security/defender/advanced-hunting-query-language). 

İşte örnek bir sorgu:

```kusto
DeviceEvents
| where ActionType startswith 'Asr'
```

## <a name="review-attack-surface-reduction-events-in-windows-event-viewer"></a>Olay Görüntüleyicisi'nde saldırı yüzeyini azaltma Windows olaylarını gözden geçirme

Saldırı yüzeyini azaltma Windows oluşturulan olayları görüntülemek için etkinlik günlüğünü gözden geçirerek:

1. Değerlendirme [Paketi'i](https://aka.ms/mp7z2w) indirin ve *cfa-events.xml* cihazda kolayca erişilebilir bir konuma ulaşacak şekilde dosyayı ayıklayabilirsiniz.

2. Olay *Görüntüleyicisi'ni açmak* için Başlat menüsü Görüntüleyicisi Windows girin.

3. **Eylemler'in** altında Özel **görünümü içeri aktar... seçeneğini seçin**.

4. Ayıklanan *cfa-events.xml* istediğiniz dosyayı seçin. Alternatif olarak, [XML'yi doğrudan kopyalayın](event-views.md).

5. **Tamam**'ı seçin.

Yalnızca aşağıdaki olayları gösterecek şekilde, bunların hepsi denetimli klasör erişimiyle ilgili olan olayları filtreleyen özel bir görünüm oluşturabilirsiniz:

|Olay Kimliği|Açıklama|
|---|---|
|5007|Ayarların değiştir olduğu olay|
|1121|Engelleme modunda kural geldiğinde olay|
|1122|Denetim modunda kural geldiğinde olay|

Olay günlüğünde saldırı yüzeyini azaltma olayları için listelenen "altyapı sürümü", işletim sistemi tarafından değil Uç Nokta için Defender tarafından oluşturulur. Uç Nokta için Defender Windows 10 ve Windows 11 ile tümleşiktir, dolayısıyla bu özellik Windows 10 veya Windows 11 yüklü tüm cihazlarda çalışır.
