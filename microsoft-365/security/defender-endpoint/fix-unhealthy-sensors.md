---
title: Uç Nokta için Microsoft Defender'de iyi durumda olmayan algılayıcıları düzeltme
description: Hizmetin cihazdan veri alması için yanlış yapılandırılmış veya devre dışı olarak bildiren cihaz algılayıcılarını düzeltin.
keywords: yanlış yapılandırılmış, etkin değil, algılayıcıyı düzeltin, algılayıcı durumu, algılayıcı verileri yok, algılayıcı verileri, bozuk iletişimler, iletişim
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 11/23/2020
ms.technology: mde
ms.openlocfilehash: cc88fa877c0c284555f1702a5fa3190a06e7e47e
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490885"
---
# <a name="fix-unhealthy-sensors-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'de iyi durumda olmayan algılayıcıları düzeltme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-fixsensor-abovefoldlink)

Cihazlar, çeşitli nedenlerle yanlış yapılandırılmış veya etkin olmayan olarak işaretlendiği için kategorilere ayırılabilir. Bu bölümde, bir cihazın etkin olmayan veya yanlış yapılandırılmış olarak kategorilere ayrılmasına neyin neden olabileceğine ilişkin bazı açıklamalar sağlanmaktadır.

## <a name="inactive-devices"></a>Etkin olmayan cihazlar

Bir sorun nedeniyle etkin olmayan bir cihaza bayrak eklenmiş olması gerekmez. Bir cihazda gerçekleştirilen aşağıdaki eylemler, cihazın etkin olmayan olarak kategorilere ayrılmasına neden olabilir:

- Cihaz kullanımda değil
- Cihaz yeniden yüklendi veya yeniden adlandırıldı
- Cihaz kapalıydı
- Cihaz sinyal göndermiyor


### <a name="device-isnt-in-use"></a>Cihaz kullanımda değil

Yedi günden uzun süredir kullanımda olmayan tüm cihazlar portalda 'Etkin Değil' durumunu korur.

### <a name="device-was-reinstalled-or-renamed"></a>Cihaz yeniden yüklendi veya yeniden adlandırıldı
Yeniden yüklenen veya yeniden adlandırılmış cihazlar için Microsoft 365 Defender yeni bir cihaz varlığı oluşturulur. Portalda 'Etkin Değil' durumuyla birlikte önceki cihaz varlığı kalır. Bir cihazı yeniden yüklediyseniz ve Uç Nokta için Defender paketini dağıttıysanız, cihazın normal şekilde raporlandığını doğrulamak için yeni cihaz adını arayın.

### <a name="device-was-offboarded"></a>Cihaz kapalıydı
Cihaz kapalıysa, cihaz listesinde görünmeye devam eder. Yedi gün sonra cihaz sistem durumu devre dışı olarak değiştirilmelidir.

### <a name="device-isnt-sending-signals"></a>Cihaz sinyal göndermiyor
Cihaz herhangi bir nedenle yedi günden uzun bir süre boyunca Uç Nokta için Microsoft Defender kanallarına sinyal göndermiyorsa, cihaz devre dışı olarak kabul edilebilir; bu, yanlış yapılandırılmış cihaz sınıflandırması kapsamındaki koşulları içerir.

Bir cihazın 'Etkin' durumunda olmasını bekliyor musunuz? [Bir destek bileti açın](https://support.microsoft.com/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=16055&ccsid=636206786382823561).

## <a name="misconfigured-devices"></a>Hatalı yapılandırılmış cihazlar
Yanlış yapılandırılmış cihazlar şu şekilde sınıflandırılabilir:
- Bozuk iletişimler
- Algılayıcı verileri yok

### <a name="impaired-communications"></a>Bozuk iletişimler
Bu durum, cihaz ve hizmet arasında sınırlı iletişim olduğunu gösterir.

Aşağıdaki önerilen eylemler, iletişim bozukluğu olan yanlış yapılandırılmış bir cihazla ilgili sorunları gidermeye yardımcı olabilir:

- [Cihazın İnternet bağlantısı olduğundan emin olun](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  Uç Nokta için Microsoft Defender algılayıcısı, algılayıcı verilerini raporlamak ve Uç Nokta için Microsoft Defender hizmetiyle iletişim kurmak için Microsoft Windows HTTP (WinHTTP) gerektirir.

- [Uç Nokta için Microsoft Defender hizmet URL'lerine istemci bağlantısını doğrulama](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  Proxy yapılandırmasının başarıyla tamamlandığını, WinHTTP'nin ortamınızdaki proxy sunucusunu bulup iletişim kurabildiğini ve ara sunucunun Uç Nokta için Microsoft Defender hizmet URL'lerine trafiğe izin verdiğinden emin olun.

Düzeltici eylemler gerçekleştirdiyseniz ve cihaz durumu hala yanlış yapılandırılmışsa [bir destek bileti açın](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409).

### <a name="no-sensor-data"></a>Algılayıcı verileri yok
'Algılayıcı verileri yok' durumuyla yanlış yapılandırılmış bir cihazın hizmetle iletişimi vardır ancak yalnızca kısmi algılayıcı verilerini bildirebilir.

'Algılayıcı verileri yok' durumuyla yanlış yapılandırılmış bir cihazla ilgili bilinen sorunları düzeltmek için bu eylemleri izleyin:

- [Cihazın İnternet bağlantısı olduğundan emin olun](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  Uç Nokta için Microsoft Defender algılayıcısı, algılayıcı verilerini raporlamak ve Uç Nokta için Microsoft Defender hizmetiyle iletişim kurmak için Microsoft Windows HTTP (WinHTTP) gerektirir.

- [Uç Nokta için Microsoft Defender hizmet URL'lerine istemci bağlantısını doğrulama](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  Proxy yapılandırmasının başarıyla tamamlandığını, WinHTTP'nin ortamınızdaki proxy sunucusunu bulup iletişim kurabildiğini ve ara sunucunun Uç Nokta için Microsoft Defender hizmet URL'lerine trafiğe izin verdiğinden emin olun.

- [Tanılama veri hizmetinin etkinleştirildiğinden emin olun](troubleshoot-onboarding.md#ensure-the-diagnostics-service-is-enabled)</br>
Cihazlar doğru bildirmiyorsa, Windows tanılama veri hizmetinin otomatik olarak başlayacak şekilde ayarlandığını doğrulamanız gerekir. Ayrıca Windows tanılama veri hizmetinin uç noktada çalıştığını doğrulayın.

- [Microsoft Defender Virüsten Koruma'nın ilke tarafından devre dışı bırakılmadığından emin olun](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)</br>
Cihazlarınız üçüncü taraf kötü amaçlı yazılımdan koruma istemcisi çalıştırıyorsa, Uç Nokta için Defender aracısının Microsoft Defender Virüsten Koruma Erken Başlatma Kötü Amaçlı Yazılımdan Koruma (ELAM) sürücüsünün etkinleştirilmesi gerekir.

Düzeltici eylemler gerçekleştirdiyseniz ve cihaz durumu hala yanlış yapılandırılmışsa [bir destek bileti açın](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409).

## <a name="see-also"></a>Ayrıca bkz.
- [Uç Nokta için Microsoft Defender algılayıcı durumunu denetleme](check-sensor-status.md)
- [İstemci çözümleyicisine genel bakış](overview-client-analyzer.md)
- [İstemci çözümleyicisini indirin ve çalıştırın](download-client-analyzer.md)
- [İstemci çözümleyicisini Windows’da çalıştırın](run-analyzer-windows.md)
- [İstemci çözümleyicisini macOS veya Linux'ta çalıştırın](run-analyzer-macos-linux.md)
- [Windows'da gelişmiş sorun giderme için veri toplama](data-collection-analyzer.md)

