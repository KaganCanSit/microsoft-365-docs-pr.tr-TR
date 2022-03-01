---
title: Hatalı sitelere bağlantıları önlemeye yardımcı olmak için ağ korumasını kullanma
description: Kullanıcıların bilinen kötü amaçlı ve şüpheli ağ adreslerine erişimini engelerek ağın korunması
keywords: Ağ koruması, exploits, kötü amaçlı web sitesi, ip, etki alanı, etki alanları
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
ms.collection: m365initiative-m365-defender
ms.date: ''
ms.openlocfilehash: b94e7f959c44e44e5b61dfd0536b3c1077d0edc5
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015194"
---
# <a name="protect-your-network"></a>Ağın koruma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="overview-of-network-protection"></a>Ağ korumasına genel bakış

Ağ koruması, cihazları İnternet tabanlı etkinliklere karşı korumaya yardımcı olur. Ağ koruması bir saldırı yüzeyini azaltma özelliğidir. Çalışanların uygulamalar aracılığıyla tehlikeli etki alanlarına erişmesini önlemeye yardımcı olur. İnternet'ta kimlik avı dolandırıcılığı, açıkları açıkları ve diğer zararlı içerikleri barındıran etki alanları tehlikeli kabul edilir. Ağ koruması, düşük [itibarlı kaynaklara (etki](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) Microsoft Defender SmartScreen ana bilgisayar adını temel alarak) bağlanmaya çalışan tüm giden HTTP(ler) trafiğini engellemek için güvenlik kapsamını genişletmiştir.

Ağ koruması, Web koruması için [korumayı](web-protection-overview.md) işletim sistemi düzeyine genişlettir. Edge'de diğer desteklenen tarayıcılara ve tarayıcı olmayan uygulamalara web koruma işlevselliği sağlar. Buna ek olarak, ağ koruması Uç nokta algılama ve yanıtta kullanılırken güvenlik göstergelerinin (IOC) görünürlüğünü [ve engellemesini sağlar](overview-endpoint-detection-response.md). Örneğin, ağ koruması, belirli etki [alanlarını veya ana bilgisayar](manage-indicators.md) adlarını engellemek için kullanabileceğiniz özel göstergeleriniz ile birlikte çalışır.

> [!TIP]
> Ağ korumasının nasıl çalıştığını görmek için demo.wd.microsoft.com uç [nokta](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) test planı için Microsoft Defender sitesine bakın.

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

## <a name="requirements-for-network-protection"></a>Ağ koruması gereksinimleri

Ağ koruması için Windows 10 Pro veya Enterprise ve gerçek Microsoft Defender Virüsten Koruma koruma gerekir.

<br>

****

|Windows sürümü|Microsoft Defender Virüsten Koruma|
|---|---|
|Windows 10 1709 veya sonraki bir sürümü <p> Windows 11 <p> Windows Server 1803 veya sonrası|[Microsoft Defender Virüsten Koruma zamanlı koruma ve](configure-real-time-protection-microsoft-defender-antivirus.md) [buluta teslim edilen koruma](enable-cloud-protection-microsoft-defender-antivirus.md) etkinleştirilmelidir|
|

Hizmetleri etkinleştirdikten sonra, ağ veya güvenlik duvarınızı hizmetlerle cihazlarınız arasındaki bağlantılara izin verecek şekilde yapılandırmanız gerekebilir (uç nokta olarak da adlandırılır).

- `.smartscreen.microsoft.com`
- `.smartscreen-prod.microsoft.com`

## <a name="configuring-network-protection"></a>Ağ korumasını yapılandırma

Ağ korumasını etkinleştirme hakkında daha fazla bilgi için bkz. **[Ağ korumasını etkinleştirme](enable-network-protection.md)**. Ağ korumasını etkinleştirmek ve yönetmek için Grup İlkesi, PowerShell veya MDM CSP'leri kullanın.

## <a name="viewing-network-protection-events"></a>Ağ koruma olaylarını görüntüleme

Ağ koruması, en iyi şekilde [Uç Nokta için Microsoft Defender](microsoft-defender-endpoint.md) ile çalışır ve size uyarı soruşturma senaryolarının bir parçası olarak exploit protection olayları ve blokları hakkında ayrıntılı [raporlama sağlar](investigate-alerts.md).

Ağ koruması bağlantıyı engellerse, İşlem Merkezi'nde bir bildirim görüntülenir. Güvenlik işlemleri ekipleriniz [, bildirimi, kuruluşun](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) ayrıntıları ve iletişim bilgileriyle özelleştirilebilir. Buna ek olarak, her bir saldırı yüzeyini azaltma kuralları etkinleştirilebilir ve izlenmesi gereken belirli tekniklere uygun olarak özelleştirilebilir.

Ayrıca, ağ [korumasının etkinleştirilmişse](audit-windows-defender.md) kurumlarınızı nasıl etkiley olacağını değerlendirmek için de denetim modunu kullanabilirsiniz.

## <a name="review-network-protection-events-in-the-microsoft-365-defender-portal"></a>Web portalında ağ koruma Microsoft 365 Defender gözden geçirme

Uç Nokta için Microsoft Defender, uyarı soruşturma senaryolarının bir parçası olarak olaylara ve [bloklara ayrıntılı raporlama sağlar](investigate-alerts.md). Bu ayrıntıları uyarı kuyruğunda Microsoft 365 Defender portalda ([https://security.microsoft.com](https://security.microsoft.com)) veya [gelişmiş](review-alerts.md) avı kullanarak [görüntüebilirsiniz](advanced-hunting-overview.md). Denetim modunu [kullanıyorsanız, ağ](audit-windows-defender.md) koruma ayarlarının etkinleştirilmişse ortamınızı nasıl etkileyeceğini görmek için gelişmiş arama kullanabilirsiniz.

İşte gelişmiş av için örnek bir sorgu:

```kusto
DeviceNetworkEvents
|where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked', 'ConnectionSuccess')
```

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Olay Görüntüleyicisi'nde ağ Windows olaylarını gözden geçirme

Ağ koruma blokları (Windows denetimler) kötü amaçlı IP veya etki alanına erişimi sırasında oluşturulan olayları görmek için bu olay günlüğünü gözden geçirebilirsiniz:

1. [XML'yi doğrudan kopyalayın](event-views.md).

2. **Tamam**'ı seçin.

Bu yordam, yalnızca ağ korumasıyla ilgili aşağıdaki olayları gösterecek şekilde filtreleyen özel bir görünüm oluşturur:

<br>

****

|Olay Kimliği|Açıklama|
|---|---|
|5007|Ayarların değiştir olduğu olay|
|1125|Denetim modunda ağ korumasının çalışma olduğu olay|
|1126|Engelleme modunda ağ koruması geldiğinde olay|
|

## <a name="network-protection-and-the-tcp-three-way-handshake"></a>Ağ koruması ve TCP üç yol el sıkışması

Ağ korumasıyla, [TCP/IP](/troubleshoot/windows-server/networking/three-way-handshake-via-tcpip) aracılığıyla üç yolluk el sıkışması tamamlandıktan sonra siteye erişime izin verme veya erişimi engelleme belirleme işlemi yapılır. Dolayısıyla, site ağ koruması tarafından engellenmişse, site aslında engellenmiş olsa bile, `ConnectionSuccess` `NetworkConnectionEvents` Microsoft 365 Defender portalında bunun altında bir eylem türüyle sonuç bulabilirsiniz. `NetworkConnectionEvents` ağ korumasına değil TCP katmanından bildiriliyor. Üç yolluk el sıkışması tamamlandıktan sonra, ağ korumasıyla siteye erişime izin verilir veya engellenir.

İşte bunun nasıl çalıştığının bir örneği:

1. Bir kullanıcının kendi cihazından bir web sitesine erişmeye denemesi olduğunu varsayalım. Sitenin tehlikeli bir etki alanında barındırıyor olması ve ağ korumasıyla engellenmiş olması gerekir.  

2. TCP/IP aracılığıyla üç yol el sıkışması başlar. İşlem tamamlandıktan sonra bir `NetworkConnectionEvents` eylem günlüğe kaydedilir ve bu eylem `ActionType` olarak listelenir `ConnectionSuccess`. Bununla birlikte, üç yollı el sıkışması işlemi tamamlandıktan hemen sonra, ağ koruması siteye erişimi engeller. Bunların hepsi çok hızlı gerçekleşir. Üç yol el [sıkışması Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) benzer bir işlem gerçekleşir; bunun için üç yolluk el sıkışması yapılır ve siteye erişim engellenmiş veya izin verilir.

3. Microsoft 365 Defender portalda, uyarılar kuyruğunda [bir uyarı listelenir](alerts-queue.md). Bu uyarının ayrıntıları hem hem de `NetworkConnectionEvents` içerir `AlertEvents`. ActionType of 'sine sahip bir öğeniz `NetworkConnectionEvents` de olsa, sitenin engellenmiş olduğunu görüyorsunuz `ConnectionSuccess`.

## <a name="considerations-for-windows-virtual-desktop-running-windows-10-enterprise-multi-session"></a>Çok Oturumlu Windows çalıştıran sanal masaüstü Windows 10 Enterprise ilgili noktalar

Çok kullanıcılı yapısı nedeniyle, Windows 10 Enterprise noktaları unutmayın:

1. Ağ koruması, cihaz genelindeki bir özelliktir ve belirli kullanıcı oturumlarına hedef olamaz.

2. Web içeriği filtreleme ilkeleri de cihaz genişliğindedir.

3. Kullanıcı gruplarını birbirinden ayırt etmek için, ayrı havuzlar oluşturmayı Windows Sanal Masaüstü ana bilgisayar havuzlarını ve atamalarını kullanın.

4. Çalışmadan önce davranışını değerlendirmek için ağ korumasını denetim modunda test edin.

5. Çok fazla sayıda kullanıcınız veya çok sayıda çok kullanıcılı oturum varsa dağıtımınızı yeniden boyutlandırmayı göz önünde bulundurabilirsiniz.

### <a name="alternative-option-for-network-protection"></a>Ağ koruması için alternatif seçenek

Azure'Windows 10 Enterprise Sanal Masaüstü'Windows'de kullanılan Çoklu Oturum 1909 ve sonraki bölümlerde Microsoft Edge için ağ koruması aşağıdaki yöntem kullanılarak etkinleştirilebilir:

1. Ağ [korumasını aç'a](enable-network-protection.md) ve ilkenizi uygulamak için yönergeleri izleyin.

2. Aşağıdaki PowerShell komutunu yürütme: `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`

## <a name="network-protection-troubleshooting"></a>Ağ koruma sorunlarını giderme

Ağ korumasının çalıştır olduğu ortam nedeniyle, Microsoft işletim sistemi ara sunucu ayarlarını algılayemeyebilirsiniz. Bazı durumlarda, ağ koruma istemcileri Bulut Hizmeti'ne ulaşamaz. Bağlantı sorununu çözmek için, E5 lisansı olan müşteriler aşağıdaki kayıt defteri anahtarlarından birini yapılandırabilir:

```console
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyServer /d "<proxy IP address: Port>" /f
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyPacUrl /d "<Proxy PAC url>" /f

```

## <a name="see-also"></a>Ayrıca bkz.

- [Ağ koruma güvenlik güvenlik](evaluate-network-protection.md) | Özelliğin nasıl çalıştığını ve tipik olarak hangi olayların oluşturul olacağını gösteren hızlı bir senaryoya taahhütte bulundurabilirsiniz.
- [Ağ koruma güvenlik olanaklarını](enable-network-protection.md) | Ağ korumasını etkinleştirmek ve yönetmek için Grup İlkesi, PowerShell veya MDM CSP'leri kullanın.
- [Saldırı yüzeyini azaltma özelliklerini Microsoft Intune](/mem/intune/protect/endpoint-security-asr-policy)
