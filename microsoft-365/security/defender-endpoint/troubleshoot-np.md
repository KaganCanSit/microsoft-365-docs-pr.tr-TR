---
title: Ağ korumasıyla ilgili sorunları giderme
description: Uç Nokta için Microsoft Defender'da Ağ korumasıyla ilgili sorunları gidermek için kaynaklar ve örnek kod.
keywords: sorun giderme, hata, düzeltme, windows defender eg, asr, kurallar, hips, sorun giderme, denetim, dışlama, yanlış pozitif, bozuk, engelleme, Uç Nokta için Microsoft Defender
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: dansimp
ms.author: dansimp
ms.reviewer: oogunrinde
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 169a05fdde96ec780bf5e626d81846c9c2d37f26
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998061"
---
# <a name="troubleshoot-network-protection"></a>Ağ koruması sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Bu makale, ağ [korumasıyla ilgili sorun](network-protection.md) giderme bilgileri sağlar; örneğin:

- Ağ koruması güvenli olan bir web sitesini engeller (hatalı pozitif)
- Ağ koruması şüpheli veya bilinen kötü amaçlı web sitesini engelleyememektedir (hatalı negatif)

Bu sorunları gidermenin dört adımı vardır:

1. Önkoşulları onaylayın
2. Kuralı test etmek için denetim modunu kullanma
3. Belirtilen kural için dışlamalar ekleme (hatalı pozitif sonuçlar için)
4. Destek günlüklerini gönderme

## <a name="confirm-prerequisites"></a>Önkoşulları onaylayın

Ağ koruması yalnızca aşağıdaki koşulların yer alan cihazlarda çalışır:

> [!div class="checklist"]
>
> - Uç noktalar yeni sürüm Windows 10 Pro Enterprise, sürüm 1709 veya üzerinde çalışıyor.
> - Uç noktalar, Microsoft Defender Virüsten Koruma virüsten koruma uygulaması olarak E-posta uygulamasını kullanıyor. [Microsoft dışı bir virüsten koruma çözümü kullanırken neler olduğunu bakın](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).
> - [Gerçek zamanlı koruma](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) etkinleştirilir.
> - [Bulut teslimi koruması](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) etkinleştirilir.
> - Denetim modu etkinleştirilmedi. Kuralı [Devre Dışı olarak](enable-network-protection.md#group-policy) ayarlamak için Grup **İlkesi kullanma (** değer: **0**).

## <a name="use-audit-mode"></a>Denetim modunu kullanma

Denetim modunda ağ korumasını etkinleştirebilir ve ardından bu özelliği tanıtım için oluşturduğumız web sitesini ziyaret edebilirsiniz. Tüm web sitesi bağlantılarına ağ koruması izin verilir, ancak ağ koruması etkinleştirilmişse engellenmiş olacak tüm bağlantıları göstermek için bir olay günlüğe kaydedilir.

1. Ağ korumasını Denetim **moduna ayarlayın**.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection AuditMode
   ```

2. Soruna neden olan bağlantı etkinliğini gerçekleştirin (örneğin, siteyi ziyaret etmeye veya engellemek ya da engellemek istediğiniz IP adresine bağlanmayı).

3. [Özelliğin Etkin olarak ayarlanmışsa](network-protection.md#review-network-protection-events-in-windows-event-viewer) bağlantıyı engel bulup engellemey olurdu diye görmek için ağ koruma olay günlüklerini gözden **geçirebilirsiniz**.

   Ağ koruması engellemesi gereken bir bağlantıyı engelliyorsa, özelliği etkinleştirin.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection Enabled
   ```

## <a name="report-a-false-positive-or-false-negative"></a>Hatalı pozitif veya hatalı negatif sonuçlar bildirme

Özelliği tanıtım sitesiyle ve denetim moduyla test ettiysiniz ve ağ koruması önceden yapılandırılmış senaryolarda çalışıyor ancak belirli bir bağlantıda beklendiği gibi çalışmıyorsa, ağ koruması için hatalı negatif veya yanlış pozitif bir sonuç olduğunu rapor etmek için [Windows Defender Security Intelligence web](https://www.microsoft.com/wdsi/filesubmission) tabanlı gönderme formunu kullanın. E5 aboneliğiyle, ilgili herhangi [bir uyarının bağlantısını da sebilirsiniz](alerts-queue.md).

Bkz[. Uç nokta için Microsoft Defender'da hatalı pozitif/negatifleri adres.](defender-endpoint-false-positives-negatives.md)

## <a name="add-exclusions"></a>Dışlama ekle
Geçerli dışlama seçenekleri şunlardır:

1.  Özel bir izin göstergesi ayarlama.
2.  IP dışlamalarını kullanma: `Add-MpPreference -ExclusionIpAddress 192.168.1.1`
3.  Tüm işlemi dışlama. Daha fazla bilgi için bkz[. Microsoft Defender Virüsten Koruma dışı bırakmalar](configure-exclusions-microsoft-defender-antivirus.md). 


## <a name="collect-diagnostic-data-for-file-submissions"></a>Dosya gönderimleri için tanılama verilerini toplama

Ağ korumasıyla ilgili bir sorun bildirerek, Microsoft destek ve mühendislik ekipleri tarafından sorunların giderilmesine yardımcı olmak için kullanılmaktadır.

1. Yükseltilmiş bir komut istemi açın ve Windows Defender olarak değiştirme:

   ```console
   cd c:\program files\windows defender
   ```

2. Tanılama günlüklerini oluşturmak için bu komutu çalıştırın:

   ```console
   mpcmdrun -getfiles
   ```

3. Dosyayı gönderme formuna ekleme. Varsayılan olarak, tanılama günlükleri 'a kaydedilir `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`.

## <a name="resolve-connectivity-issues-with-network-protection-for-e5-customers"></a>Ağ korumasıyla ilgili bağlantı sorunlarını çözme (E5 müşterileri için)

Ağ korumasının çalıştır olduğu ortam nedeniyle, Microsoft işletim sistemi ara sunucu ayarlarınızı göre değildir. Bazı durumlarda, ağ koruma istemcileri bulut hizmetine ulaşamaz. Ağ korumasıyla ilgili bağlantı sorunlarını çözmek için, aşağıdaki kayıt defteri anahtarlarından birini yapılandırarak ağ korumasının ara sunucu yapılandırmasına dikkat edin:

```powershell
Set-MpPreference -ProxyServer <proxy IP address: Port>
```

---OR---

```powershell
Set-MpPreference -ProxyPacUrl <Proxy PAC url>
```

PowerShell, Microsoft Endpoint Manager veya Grup İlkesi'ni kullanarak kayıt defteri anahtarını yapılandırabilirsiniz. Size yardımcı olacak bazı kaynaklar:

- [Kayıt Defteri Anahtarları ile çalışma](/powershell/scripting/samples/working-with-registry-keys)
- [E-posta için özel istemci Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure-client)
- [Grup İlkesi ayarlarını kullanarak grup ayarlarını Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-group-policies)

## <a name="see-also"></a>Ayrıca bkz.

- [Ağ koruması](network-protection.md)
- [Ağ koruması ve TCP üç yol el sıkışması](network-protection.md#network-protection-and-the-tcp-three-way-handshake)
- [Ağ korumasını değerlendirme](evaluate-network-protection.md)
- [Ağ korumasını etkinleştirme](enable-network-protection.md)
- [Uç Nokta için Defender'da hatalı pozitif/negatifleri adres](defender-endpoint-false-positives-negatives.md)
