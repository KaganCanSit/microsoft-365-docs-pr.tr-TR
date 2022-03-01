---
title: Uç Nokta İstemci Çözümleyicisi için Microsoft Defender'ı kullanarak algılayıcı sistem durumu sorunlarını giderme
description: Algılayıcı verilerini veya kapasitesini etkileyen olası yapılandırma, ortam, bağlantı veya telemetri sorunlarını belirlemek için cihazlarda algılayıcı sistem durumu sorunlarını giderin.
keywords: algılayıcı, algılayıcı durumu, hatalı yapılandırılmış, etkin olmayan, algılayıcı verisi yok, algılayıcı verileri, engelli iletişimler, iletişim
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 9b4363b529ce9087e640c9bfaa32c8d21f410710
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63019005"
---
# <a name="troubleshoot-sensor-health-using-microsoft-defender-for-endpoint-client-analyzer"></a>Uç Nokta İstemci Çözümleyicisi için Microsoft Defender'ı kullanarak algılayıcı sistem durumu sorunlarını giderme

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

uç nokta istemci çözümleyicisi (MDECA) için Microsoft Defender, Windows, Linux veya macOS çalıştıran yerleşik cihazlarda algılayıcı sistem durumu [](/microsoft-365/security/defender-endpoint/onboard-configure) veya güvenilirlik sorunlarını tanılamak için yararlı olabilir. Örneğin, güvenlik portalında görüntülenen algılayıcı sistem durumuna [(Etkin](/microsoft-365/security/defender-endpoint/fix-unhealthy-sensors) Değil, Algılayıcı Verisi Yok veya İletişim Bozukluğu) göre uygun olmayan bir makinede çözümleyiciyi çalıştırmanız iyi olmaz.

MDECA, belirgin algılayıcı sağlığı sorunlarının yanı sıra, karmaşık senaryoları gidermek için başka izlemeler, günlükler ve tanılama bilgileri de toplayabilirsiniz:

- Uygulama uyumluluğu (AppCompat), performans, ağ bağlantısı veya
- Uç Nokta Veri Kaybını Önleme [ile ilgili beklenmedik davranış](/microsoft-365/compliance/endpoint-dlp-learn-about).

## <a name="privacy-notice"></a>Gizlilik bildirimi

- Uç Nokta İstemci Çözümleyicisi için Microsoft Defender aracı, Microsoft Customer Support Services (CSS) tarafından Uç Nokta için Microsoft Defender ile karşılaşabilirsiniz sorunları gidermenize yardımcı olacak bilgileri toplamak için düzenli olarak kullanılır.

- Toplanan veriler IP adresleri, bilgisayar adları ve kullanıcı adları gibi (ancak bunlarla sınırlı değildir) Kişisel Kimliği Tanımlayıcı Bilgileri (PII) ve/veya hassas veriler içerebilir.

- Veri toplama tamamlandıktan sonra araç, verileri yerel olarak makineye bir alt klasör ve sıkıştırılmış zip dosyası içinde kaydeder.

- Microsoft'a herhangi bir veri otomatik olarak gönderilmez. Destek sorunu üzerinde işbirliği sırasında aracı kullanıyorsanız, sorunun araştırmalarını kolaylaştırmak için sıkıştırılmış verileri Güvenli Dosya Exchange kullanarak Microsoft CSS'ye göndermenız istenebilirsiniz.

Güvenli Dosya Değiştirme hakkında daha fazla Exchange için bkz. Microsoft Desteği ile [dosya Exchange Güvenli Dosya Kullanımı](/troubleshoot/azure/general/secure-file-exchange-transfer-files)

Gizlilik bildirimimiz hakkında daha fazla bilgi için bkz. [Microsoft Gizlilik Bildirimi](https://privacy.microsoft.com/privacystatement).

## <a name="requirements"></a>Gereksinimler

- Çözümleyiciyi çalıştırmadan önce, ara sunucu veya güvenlik duvarı yapılandırmanız için Uç nokta hizmeti URL'leri için [Microsoft Defender'a](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server) erişime izin verir.

- Çözümleyici, Uç Nokta için Microsoft [Defender'a Windows](minimum-requirements.md#supported-windows-versions) sonra desteklenen Windows, [Linux](microsoft-defender-endpoint-linux.md#system-requirements) veya [macOS](microsoft-defender-endpoint-mac.md#system-requirements) sürümlerinde çalıştırabilirsiniz.

- Diğer Windows için, çözümleyiciyi doğrudan belirli makinelerde çalıştırıyorsanız ve [Live Response](/microsoft-365/security/defender-endpoint/troubleshoot-collect-support-log) üzerinden uzaktan çalışmıyorsanız, SysInternals'ın [ ](/sysinternals/downloads/psexec)PsExec.exeçalışmasına izin verilmiyor (en azından geçici olarak) gerekir. Çözümleyici, PsExec.exe bağlantı denetimlerini Yerel Sistem olarak çalıştırmak ve SENSE hizmetinin davranışını taklit etmek için PsExec.exe aracına bağlanır.

    > [!NOTE]
    > Windows cihazlarında, [PSExec ve WMI](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands) komutlarından kaynaklanan Süreç oluşturma işlemlerini engelle saldırısını azaltma (ASR) kuralını kullanırsanız, çözümleyicinin beklendiği gibi buluta bağlantı denetimlerini çalıştırmasına izin vermek için kuralı geçici olarak devre dışı bırakmak veya [ASR](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) kuralına dışlama yapılandırmak istiyor olabilirsiniz.
