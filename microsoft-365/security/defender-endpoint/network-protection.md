---
title: Hatalı sitelere bağlantıları önlemeye yardımcı olmak için ağ korumasını kullanma
description: Kullanıcıların bilinen kötü amaçlı ve şüpheli ağ adreslerine erişmesini engelleyerek ağınızı koruyun
keywords: Ağ koruması, açıklardan yararlanmalar, kötü amaçlı web sitesi, ip, etki alanı, etki alanları
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: oogunrinde
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: overview
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.date: ''
ms.openlocfilehash: f58c7afe9c6f532f7f6420d58bcd681778483680
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789348"
---
# <a name="protect-your-network"></a>Ağınızı koruyun

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

> Pertahanan Microsoft untuk Titik Akhir mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="overview-of-network-protection"></a>Ağ korumasına genel bakış

Ağ koruması, cihazların İnternet tabanlı olaylardan korunmasına yardımcı olur. Ağ koruması bir saldırı yüzeyi azaltma özelliğidir. Çalışanların uygulamalar aracılığıyla tehlikeli etki alanlarına erişmesini önlemeye yardımcı olur. İnternette kimlik avı dolandırıcılığı, açıklardan yararlanma ve diğer kötü amaçlı içerikleri barındıran etki alanları tehlikeli olarak kabul edilir. Ağ koruması[, düşük](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) saygınlık kaynaklarına bağlanmaya çalışan tüm giden HTTP trafiğini (etki alanı veya konak adına göre) engellemek için Microsoft Defender SmartScreen kapsamını genişletir.

Ağ koruması [, Web korumasındaki](web-protection-overview.md) korumayı işletim sistemi düzeyine genişletir. Edge'de desteklenen diğer tarayıcılara ve tarayıcı olmayan uygulamalara web koruma işlevselliği sağlar. Buna ek olarak, ağ koruması [Uç nokta algılama ve yanıt](overview-endpoint-detection-response.md) ile kullanıldığında güvenliğin aşılmasına ilişkin göstergelerin (ICS) görünürlüğünü ve engellenmesini sağlar. Örneğin, ağ koruması belirli etki alanlarını veya konak adlarını engellemek için kullanabileceğiniz [özel göstergelerinizle](manage-indicators.md) birlikte çalışır.

> [!TIP]
> Ağ korumasının nasıl çalıştığını görmek için [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) Pertahanan Microsoft untuk Titik Akhir testground sitesine bakın.

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

## <a name="requirements-for-network-protection"></a>Ağ koruması gereksinimleri

Ağ koruması için Windows 10 Pro veya Enterprise ve gerçek zamanlı koruma Microsoft Defender Virüsten Koruma gerekir.

<br>

****

|Windows sürümü|Microsoft Defender Virüsten Koruma|
|---|---|
|Windows 10 sürüm 1709 veya üzeri <p> Windows 11 <p> Windows Server 1803 veya üzeri|[Microsoft Defender Virüsten Koruma gerçek zamanlı koruma](configure-real-time-protection-microsoft-defender-antivirus.md) ve [bulut tabanlı koruma](enable-cloud-protection-microsoft-defender-antivirus.md) etkinleştirilmelidir|
|

Hizmetleri etkinleştirdikten sonra, ağ veya güvenlik duvarınızı hizmetler ve cihazlarınız arasındaki bağlantılara izin verecek şekilde yapılandırmanız gerekebilir (uç noktalar olarak da adlandırılır).

- `.smartscreen.microsoft.com`
- `.smartscreen-prod.microsoft.com`

## <a name="configuring-network-protection"></a>Ağ korumasını yapılandırma

Ağ korumasını etkinleştirme hakkında daha fazla bilgi için bkz. **[Ağ korumasını etkinleştirme](enable-network-protection.md)**. Ağınızda ağ korumasını etkinleştirmek ve yönetmek için grup ilkesi, PowerShell veya MDM CSP'lerini kullanın.

## <a name="viewing-network-protection-events"></a>Ağ koruma olaylarını görüntüleme

Ağ koruması en iyi [Pertahanan Microsoft untuk Titik Akhir](microsoft-defender-endpoint.md) ile çalışır ve [bu da uyarı araştırma senaryolarının](investigate-alerts.md) bir parçası olarak açıklardan yararlanma koruma olayları ve blokları hakkında ayrıntılı raporlama sağlar.

Ağ koruması bir bağlantıyı engellediğinde, İşlem Merkezi'nden bir bildirim görüntülenir. Güvenlik operasyonları ekibiniz, kuruluşunuzun ayrıntıları ve iletişim bilgileriyle [bildirimi özelleştirebilir](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) . Ayrıca, tek tek saldırı yüzeyi azaltma kuralları etkinleştirilebilir ve izlemek için belirli tekniklere uyacak şekilde özelleştirilebilir.

Ağ korumasının etkinleştirildiğinde kuruluşunuzu nasıl etkileyeceğini değerlendirmek için [denetim modunu](audit-windows-defender.md) da kullanabilirsiniz.

## <a name="review-network-protection-events-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında ağ koruma olaylarını gözden geçirme

Pertahanan Microsoft untuk Titik Akhir[, uyarı araştırma senaryolarının](investigate-alerts.md) bir parçası olarak olaylara ve bloklara ayrıntılı raporlama sağlar. Bu ayrıntıları [uyarı kuyruğundaki](review-alerts.md) Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com)) veya [gelişmiş avcılığı](advanced-hunting-overview.md) kullanarak görüntüleyebilirsiniz. [Denetim modunu](audit-windows-defender.md) kullanıyorsanız, ağ koruma ayarlarının etkinleştirildiyse ortamınızı nasıl etkileyeceğini görmek için gelişmiş avcılığı kullanabilirsiniz.

Gelişmiş avcılık için örnek bir sorgu aşağıda verilmiştir:

```kusto
DeviceNetworkEvents
|where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked', 'ConnectionSuccess')
```

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Windows Olay Görüntüleyicisi'da ağ koruma olaylarını gözden geçirme

Ağ koruması kötü amaçlı bir IP'ye veya etki alanına erişimi engellediğinde (veya denetlediğinde) oluşturulan olayları görmek için Windows olay günlüğünü gözden geçirebilirsiniz:

1. [XML'yi doğrudan kopyalayın](event-views.md).

2. **Tamam**'ı seçin.

Bu yordam, yalnızca ağ korumasıyla ilgili aşağıdaki olayları gösterecek şekilde filtreleyen özel bir görünüm oluşturur:

<br>

****

|Olay Kimliği|Açıklama|
|---|---|
|5007|Ayarlar değiştirildiğinde gerçekleşen olay|
|1125|Ağ koruması denetim modunda tetiklendiğinde gerçekleşen olay|
|1126|Ağ koruması blok modunda tetiklendiğinde gerçekleşen olay|
|

## <a name="network-protection-and-the-tcp-three-way-handshake"></a>Ağ koruması ve TCP üç yönlü el sıkışması

Ağ koruması ile, [TCP/IP aracılığıyla üç yönlü el sıkışması](/troubleshoot/windows-server/networking/three-way-handshake-via-tcpip) tamamlandıktan sonra siteye erişime izin verilip verilmeyeceğinin veya engellenip engellenmeyeceğinin belirlenmesi yapılır. Bu nedenle, bir site ağ koruması tarafından engellendiğinde, site gerçekten engellenmiş olsa bile Microsoft 365 Defender portalında altında `NetworkConnectionEvents` bir eylem türü `ConnectionSuccess` görebilirsiniz. `NetworkConnectionEvents` ağ korumasından değil TCP katmanından bildirilir. Üç yönlü el sıkışması tamamlandıktan sonra siteye erişime izin verilir veya ağ koruması tarafından engellenir.

Bunun nasıl çalıştığına dair bir örnek aşağıda verilmişti:

1. Bir kullanıcının cihazında bir web sitesine erişmeye çalıştığı varsayılmaktadır. Site tehlikeli bir etki alanında barındırılacak ve ağ koruması tarafından engellenmelidir.  

2. TCP/IP aracılığıyla üç yönlü el sıkışması başlar. İşlem tamamlanmadan önce bir `NetworkConnectionEvents` eylem günlüğe kaydedilir ve eylemi `ActionType` olarak `ConnectionSuccess`listelenir. Ancak, üç yönlü el sıkışma işlemi tamamlandığında ağ koruması siteye erişimi engeller. Tüm bunlar çok hızlı gerçekleşir. Benzer bir işlem [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) gerçekleşir; üç yönlü el sıkışması tamamlandığında belirleme yapılır ve siteye erişim engellenir veya siteye erişime izin verilir.

3. Microsoft 365 Defender portalında, [uyarılar kuyruğunda bir uyarı](alerts-queue.md) listelenir. Bu uyarının ayrıntıları hem hem `AlertEvents`de `NetworkConnectionEvents` içerir. ActionType içeren bir `NetworkConnectionEvents` öğeniz de olsa, sitenin `ConnectionSuccess`engellendiğini görebilirsiniz.

## <a name="considerations-for-windows-virtual-desktop-running-windows-10-enterprise-multi-session"></a>Çoklu Oturum Windows 10 Enterprise çalışan Windows sanal masaüstü için dikkat edilmesi gerekenler

Windows 10 Enterprise çok kullanıcılı yapısı nedeniyle aşağıdaki noktaları göz önünde bulundurun:

1. Ağ koruması cihaz genelindeki bir özelliktir ve belirli kullanıcı oturumlarına hedeflenemez.

2. Web içeriği filtreleme ilkeleri de cihaz genelindedir.

3. Kullanıcı grupları arasında ayrım yapmanız gerekiyorsa, sanal masaüstü konak havuzları ve atamaları Windows ayrı ayrı oluşturmayı göz önünde bulundurun.

4. Dağıtımdan önce davranışını değerlendirmek için ağ korumasını denetim modunda test edin.

5. Çok fazla sayıda kullanıcınız veya çok sayıda çok kullanıcılı oturumunuz varsa dağıtımınızı yeniden boyutlandırmayı göz önünde bulundurun.

### <a name="alternative-option-for-network-protection"></a>Ağ koruması için alternatif seçenek

Azure'da Windows Sanal Masaüstü'nde kullanılan Windows 10 Enterprise Çoklu Oturum 1909 ve üstü için, Microsoft Edge için ağ koruması aşağıdaki yöntem kullanılarak etkinleştirilebilir:

1. [Ağ korumasını aç'ı](enable-network-protection.md) kullanın ve ilkenizi uygulamak için yönergeleri izleyin.

2. Aşağıdaki PowerShell komutlarını yürütür:
  - `Set-MpPreference -EnableNetworkProtection Enabled`
  - `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`
  - `Set-MpPreference -AllowNetworkProtectionDownLevel 1`
  - `Set-MpPreference -AllowDatagramProcessingOnWinServer 1`

## <a name="network-protection-troubleshooting"></a>Ağ koruması sorunlarını giderme

Ağ korumasının çalıştığı ortam nedeniyle Microsoft, işletim sistemi proxy ayarlarını algılayamayabilir. Bazı durumlarda ağ koruma istemcileri Bulut Hizmeti'ne ulaşamaz. Bağlantı sorununu çözmek için E5 lisansı olan müşterilerin aşağıdaki kayıt defteri anahtarlarından birini yapılandırması gerekir:

```console
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyServer /d "<proxy IP address: Port>" /f
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyPacUrl /d "<Proxy PAC url>" /f

```

## <a name="see-also"></a>Ayrıca bkz.

- [Ağ koruma | değerlendirme](evaluate-network-protection.md) Özelliğin nasıl çalıştığını ve genellikle hangi olayların oluşturulacağını gösteren hızlı bir senaryoyu üstlenin.
- [Ağ korumasını etkinleştirme](enable-network-protection.md) | Ağınızda ağ korumasını etkinleştirmek ve yönetmek için grup ilkesi, PowerShell veya MDM CSP'lerini kullanın.
- [Microsoft Intune'de saldırı yüzeyi azaltma özelliklerini yapılandırma](/mem/intune/protect/endpoint-security-asr-policy)
