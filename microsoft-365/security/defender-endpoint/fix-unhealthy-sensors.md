---
title: Uç Nokta için Microsoft Defender'da uygun olmayan algılayıcıları düzeltme
description: Hizmet cihazdan veri aecek şekilde hatalı veya etkin değil olarak bildiren cihaz algılayıcılarını düzeltin.
keywords: hatalı yapılandırılmış, etkin değil, algılayıcıyı düzeltin, algılayıcı durumu, algılayıcı verisi yok, algılayıcı verileri, engelli iletişimler, iletişim
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
ms.openlocfilehash: e801776001b79bf1ae3e6e8a220c5e4c395896db
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63034248"
---
# <a name="fix-unhealthy-sensors-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'da uygun olmayan algılayıcıları düzeltme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-fixsensor-abovefoldlink)

Cihazlar çeşitli nedenler için yanlış yapılandırılmış veya etkin olmayan olarak kategorilere ayrılmış olabilir. Bu bölümde, bir cihazın etkin değil veya hatalı yapılandırılmış olarak kategorilere ayrılmış olabileceğine ilişkin bazı açıklamalar yer almaktadır.

## <a name="inactive-devices"></a>Etkin olmayan cihazlar

Etkin olmayan bir cihaz bir sorun nedeniyle bayrakla işaretlenmez. Bir cihazda aşağıdaki işlemler, cihazın etkin değil olarak kategorisine alınmasına neden olabilir:

### <a name="device-is-not-in-use"></a>Cihaz kullanımda değil

Yedi gündür kullanımda olmayan tüm cihaz portalda "Etkin Değil" durumunu korur.

### <a name="device-was-reinstalled-or-renamed"></a>Cihaz yeniden başlatıldı veya yeniden adlandırıldı
Yeniden yüklemek veya yeniden adlandırılmış cihazlar için Microsoft 365 Defender içinde yeni bir cihaz varlığı oluşturulur. Önceki cihaz varlığı portalda "Etkin Değil" durumuyla birlikte kalır. Cihazı yeniden yüklediy ve Uç Nokta için Defender paketini dağıttıysanız, cihazın normal olarak raporlanıyor olduğunu doğrulamak için yeni cihaz adını arayın.

### <a name="device-was-offboarded"></a>Cihaz çıkarıldı
Cihaz çıkarıldı ise cihazlar listesinde görünmeye devam ediyor. Yedi gün sonra, cihaz durumu devre dışı olarak değişir.

### <a name="device-is-not-sending-signals"></a>Cihaz sinyal gönder gönder gönderiyor
Cihaz herhangi bir nedenden dolayı hiçbir Microsoft Defender for Endpoint kanalına yedi gün boyunca hiç sinyal gönderenileni, cihaz devre dışı kabul olabilir; hatalı yapılandırılmış cihaz sınıflandırması koşulları da buna dahildir.

Bir cihazın "Etkin" durumunda olmasını mı bekliyorsunuz? [Destek bileti açın](https://support.microsoft.com/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=16055&ccsid=636206786382823561).

## <a name="misconfigured-devices"></a>Yanlış yapılandırılmış cihazlar
Yanlış yapılandırılmış cihazlar, aşağıdakiler için daha fazla sınıflandırılabilir:
- Engelli iletişimler
- Algılayıcı verisi yok

### <a name="impaired-communications"></a>Engelli iletişimler
Bu durum, cihazla hizmet arasında sınırlı iletişim olduğunu gösterir.

Aşağıdaki önerilen eylemler, engeli olan ve hatalı yapılandırılmış bir cihazla ilgili sorunları düzeltmeye yardımcı olabilir:

- [Cihazın İnternet bağlantısı olduğundan emin olun](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  Uç nokta algılayıcısı için Microsoft Defender, algılayıcı verilerini bildirmesi ve Uç nokta hizmeti için Microsoft Defender ile iletişim kurması için Microsoft Windows HTTP (WinHTTP) gerektirir.

- [Uç nokta hizmeti URL'leri için Microsoft Defender'a istemci bağlantısını doğrulama](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  Proxy yapılandırmasının başarıyla tamamlandıktan sonra WinHTTP'nin ortamınız içinde ara sunucu üzerinden sunucuyu keşfederek ileteni ve proxy sunucusunun Uç Nokta için Microsoft Defender hizmet URL'leri için trafiğine izin vereni doğrulayın.

Düzeltme eylemleri yaptınız ve cihaz durumu hala yanlış yapılandırılmışsa destek [bileti açın](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409).

### <a name="no-sensor-data"></a>Algılayıcı verisi yok
'Algılayıcı veri yok' durumuna sahip yanlış yapılandırılmış bir cihaz hizmetle iletişime sahiptir, ancak yalnızca kısmi algılayıcı verilerini bildirebilirsiniz.

Hatalı yapılandırılmış bir cihazla ilgili bilinen sorunları 'Algılayıcı verisi yok' durumuna sahip olarak düzeltmek için şu eylemleri izleyin:

- [Cihazın İnternet bağlantısı olduğundan emin olun](troubleshoot-onboarding.md#troubleshoot-onboarding-issues-on-the-device)</br>
  Uç nokta algılayıcısı için Microsoft Defender, algılayıcı verilerini bildirmesi ve Uç nokta hizmeti için Microsoft Defender ile iletişim kurması için Microsoft Windows HTTP (WinHTTP) gerektirir.

- [Uç nokta hizmeti URL'leri için Microsoft Defender'a istemci bağlantısını doğrulama](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls)</br>
  Proxy yapılandırmasının başarıyla tamamlandıktan sonra WinHTTP'nin ortamınız içinde ara sunucu üzerinden sunucuyu keşfederek ileteni ve proxy sunucusunun Uç Nokta için Microsoft Defender hizmet URL'leri için trafiğine izin vereni doğrulayın.

- [Tanılama veri hizmetinin etkinleştirildiğinden emin olun](troubleshoot-onboarding.md#ensure-the-diagnostics-service-is-enabled)</br>
Cihazlar düzgün bildir çalışmıyorsa tanılama veri hizmetinin otomatik olarak Windows olarak ayar olduğunu doğrulamanız gerekir. Ayrıca, tanılama Windows hizmetinin uç noktada çalıştığını doğrulayın.

- [E-Microsoft Defender Virüsten Koruma ilke tarafından devre dışı bırakıldık](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)</br>
Cihazlarınız üçüncü taraf bir kötü amaçlı yazılımdan koruma istemcisi çalıştır alıyorsa, Uç nokta aracısı için Defender Microsoft Defender Virüsten Koruma Başlatma İlk Başlatma Kötü Amaçlı Yazılımdan Koruma (ELAM) sürücüsünün etkinleştirilmesini gerektirir.

Düzeltme eylemleri yaptınız ve cihaz durumu hala yanlış yapılandırılmışsa destek [bileti açın](https://go.microsoft.com/fwlink/?LinkID=761093&clcid=0x409).

## <a name="see-also"></a>Ayrıca bkz.
- [Uç Nokta için Microsoft Defender'da algılayıcıların durumunu denetleme](check-sensor-status.md)
- [İstemci çözümleyicisi genel bakış](overview-client-analyzer.md)
- [İstemci çözümleyicisini indirme ve çalıştırma](download-client-analyzer.md)
- [İstemci çözümleyicisini çözümleyiciyi çalışma Windows](run-analyzer-windows.md)
- [macOS veya Linux'ta istemci çözümleyicisini çalıştırın](run-analyzer-macos-linux.md)
- [Windows'da gelişmiş sorun giderme için veri Windows](data-collection-analyzer.md)

