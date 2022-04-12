---
title: Ağ koruması ile ilgili sorunları giderme
description: Pertahanan Microsoft untuk Titik Akhir'de Ağ koruması ile ilgili sorunları gidermek için kaynaklar ve örnek kod.
keywords: sorun giderme, hata, düzeltme, windows defender eg, asr, kurallar, kalçalar, sorun giderme, denetim, dışlama, hatalı pozitif, bozuk, engelleme, Pertahanan Microsoft untuk Titik Akhir
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
ms.openlocfilehash: fbb3a9e038dcd9f342065d538762b41c0673f7e6
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783171"
---
# <a name="troubleshoot-network-protection"></a>Ağ koruması sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Uç Nokta için Defender'ı deneyimlemek mi istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Bu makalede, [ağ koruması](network-protection.md) için aşağıdaki gibi durumlarda sorun giderme bilgileri sağlanır:

- Ağ koruması güvenli bir web sitesini engeller (hatalı pozitif)
- Ağ koruması şüpheli veya bilinen kötü amaçlı bir web sitesini engelleyemiyor (hatalı negatif)

Bu sorunları gidermenin dört adımı vardır:

1. Önkoşulları onaylama
2. Kuralı test etmek için denetim modunu kullanma
3. Belirtilen kural için dışlamalar ekleme (hatalı pozitifler için)
4. Destek günlüklerini gönderme

## <a name="confirm-prerequisites"></a>Önkoşulları onaylama

Ağ koruması yalnızca aşağıdaki koşullara sahip cihazlarda çalışır:

> [!div class="checklist"]
>
> - Uç noktalar Windows 10 Pro veya Enterprise sürümü, sürüm 1709 veya üzerini çalıştırıyor.
> - Uç noktalar, tek virüsten koruma uygulaması olarak Microsoft Defender Virüsten Koruma kullanıyor. [Microsoft dışı bir virüsten koruma çözümü kullandığınızda neler olduğunu görün](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).
> - [Gerçek zamanlı koruma](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) etkindir.
> - [Bulut tabanlı koruma](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) etkindir.
> - Denetim modu etkinleştirilmedi. Kuralı **Devre Dışı** olarak ayarlamak için [grup ilkesi](enable-network-protection.md#group-policy) kullanın (değer: **0**).

## <a name="use-audit-mode"></a>Denetim modunu kullanma

Denetim modunda ağ korumasını etkinleştirebilir ve ardından özelliğin tanıtımını yapmak için oluşturduğumuz bir web sitesini ziyaret edebilirsiniz. Tüm web sitesi bağlantılarına ağ koruması tarafından izin verilir, ancak ağ koruması etkinleştirildiğinde engellenecek herhangi bir bağlantıyı göstermek için bir olay günlüğe kaydedilir.

1. Ağ korumasını **Denetim moduna** ayarlayın.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection AuditMode
   ```

2. Soruna neden olan bağlantı etkinliğini gerçekleştirin (örneğin, siteyi ziyaret etmeye veya engellemek istediğiniz veya engellemek istemediğiniz IP adresine bağlanmaya çalışma).

3. Özelliğin **Etkin** olarak ayarlanmışsa bağlantıyı engelleyip engellemediğini görmek için [ağ koruması olay günlüklerini gözden geçirin](network-protection.md#review-network-protection-events-in-windows-event-viewer).

   Ağ koruması, engellemesini beklediğiniz bir bağlantıyı engelliyorsa özelliği etkinleştirin.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection Enabled
   ```

## <a name="report-a-false-positive-or-false-negative"></a>Hatalı pozitif veya hatalı negatifi bildirme

Özelliği tanıtım sitesiyle ve denetim moduyla test ettiyseniz ve ağ koruması önceden yapılandırılmış senaryolar üzerinde çalışıyor ancak belirli bir bağlantı için beklendiği gibi çalışmıyorsa ağ koruması için hatalı negatif veya hatalı pozitif raporlamak için [Windows Defender Güvenlik Zekası web tabanlı gönderim formunu](https://www.microsoft.com/wdsi/filesubmission) kullanın. E5 aboneliğiyle [, ilişkili uyarıların bağlantısını da sağlayabilirsiniz](alerts-queue.md).

Bkz[. Pertahanan Microsoft untuk Titik Akhir hatalı pozitif/negatifleri adresle](defender-endpoint-false-positives-negatives.md).

## <a name="add-exclusions"></a>Dışlama ekleme

Geçerli dışlama seçenekleri şunlardır:

1. Özel bir izin verme göstergesi ayarlama.
2. IP dışlamalarını kullanma: `Add-MpPreference -ExclusionIpAddress 192.168.1.1`
3. İşlemin tamamını dışlama. Daha fazla bilgi için bkz. [dışlamalar Microsoft Defender Virüsten Koruma](configure-exclusions-microsoft-defender-antivirus.md). 

## <a name="collect-diagnostic-data-for-file-submissions"></a>Dosya gönderimleri için tanılama verilerini toplama

Ağ korumasıyla ilgili bir sorun bildirdiğinizde, sorunları gidermeye yardımcı olmak için Microsoft destek ve mühendislik ekipleri tarafından kullanılabilecek tanılama verilerini toplayıp göndermeniz istenir.

1. Yükseltilmiş bir komut istemi açın ve Windows Defender dizinine geçin:

   ```console
   cd c:\program files\windows defender
   ```

2. Tanılama günlüklerini oluşturmak için şu komutu çalıştırın:

   ```console
   mpcmdrun -getfiles
   ```

3. Dosyayı gönderme formuna ekleyin. Varsayılan olarak, tanılama günlükleri konumunda `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`kaydedilir.

## <a name="resolve-connectivity-issues-with-network-protection-for-e5-customers"></a>Ağ korumasıyla ilgili bağlantı sorunlarını çözme (E5 müşterileri için)

Ağ korumasının çalıştığı ortam nedeniyle Microsoft, işletim sistemi ara sunucu ayarlarınızı göremiyor. Bazı durumlarda ağ koruma istemcileri bulut hizmetine erişemez. Ağ korumasıyla ilgili bağlantı sorunlarını çözmek için, aşağıdaki kayıt defteri anahtarlarından birini ağ korumasının ara sunucu yapılandırmasından haberdar olması için yapılandırın:

```powershell
Set-MpPreference -ProxyServer <proxy IP address: Port>
```

---OR---

```powershell
Set-MpPreference -ProxyPacUrl <Proxy PAC url>
```

Kayıt defteri anahtarını PowerShell, Microsoft Endpoint Manager veya grup ilkesi kullanarak yapılandırabilirsiniz. Yardımcı olacak bazı kaynaklar şunlardır:

- [Kayıt Defteri Anahtarları ile Çalışma](/powershell/scripting/samples/working-with-registry-keys)
- [Endpoint Protection için özel istemci ayarlarını yapılandırma](/mem/configmgr/protect/deploy-use/endpoint-protection-configure-client)
- [Endpoint Protection yönetmek için grup ilkesi ayarlarını kullanma](/mem/configmgr/protect/deploy-use/endpoint-protection-group-policies)

## <a name="see-also"></a>Ayrıca bkz.

- [Ağ koruması](network-protection.md)
- [Ağ koruması ve TCP üç yönlü el sıkışması](network-protection.md#network-protection-and-the-tcp-three-way-handshake)
- [Ağ korumasını değerlendirin](evaluate-network-protection.md)
- [Ağ korumasını etkinleştirme](enable-network-protection.md)
- [Uç Nokta için Defender'da hatalı pozitif/negatifleri giderme](defender-endpoint-false-positives-negatives.md)
