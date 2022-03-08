---
title: Platform olmayan platformlar için Uç Nokta Windows Defender
description: Microsoft Defender for Endpoint capabilities for endpoint capabiliti for non-Windows.
keywords: non windows, mac, macos, linux, android
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-evalutatemtp
ms.topic: article
ms.technology: mde
ms.openlocfilehash: bfe40a4c183f113c92e263e48d72c6aa7020152b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322023"
---
# <a name="microsoft-defender-for-endpoint-for-non-windows-platforms"></a>Platform olmayan platformlar için Uç Nokta Windows Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Plan 1 ve Plan 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft, endüstri lideri uç nokta güvenlik özelliklerini Windows Windows Server'ın ötesine, macOS, Linux, Android ve iOS'a genişletme yolculuğu yaptı.

Kuruluşlar çeşitli platformlarda ve cihazlarda tehditlerle karşılaşıyor. Ekiplerimiz *hem Microsoft'tan* hem *de Microsoft'tan* müşterilerimizin heter bir ortamdaki ortamlarını korumalarına ve güvenliklerini sağlamalarına olanak sağlamak için güvenlik çözümleri sağlamayı taahhüt etti. Müşteri geri bildirimlerini dinliyor ve ihtiyaçlarına uygun çözümler oluşturmak için müşterilerimizle yakın bir ortak çalışma sunuyoruz.

Uç Nokta için Microsoft Defender ile müşteriler Microsoft 365 Defender portalında, Windows'te ve Windows olmayan platformlarda bulunan tüm tehditlere ve uyarılara birleşik bir görünümden faydalanarak ortamında olup neler olduğunu tam olarak anlayabileceklerini ve böylece tehditleri daha hızlı değerlendirmelerini ve yanıtlamalarını sağlar.

## <a name="microsoft-defender-for-endpoint-on-macos"></a>macOS'ta Uç Nokta için Microsoft Defender

macOS'ta Uç Nokta için Microsoft Defender, macOS'un en son yayımlanan üç sürümü için virüsten uç noktada algılama ve yanıtlama (EDR) ve güvenlik açığı yönetimi özellikleri sunar. Müşteriler, E-posta ve Jamf aracılığıyla Microsoft Endpoint Manager ve yönetebilir. MacOS'Microsoft Office diğer uygulamalarda olduğu gibi, Microsoft Otomatik Güncelleştirmesi de Mac'te Uç Nokta güncelleştirmeleri için Microsoft Defender'ı yönetmek için kullanılır. Önemli özellikler ve avantajlar hakkında bilgi için, duyurularımızı [okuyun](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/macOS).

Başlama hakkında daha fazla ayrıntı için macOS'ta Uç Nokta için Defender belgelerini ziyaret [edin](microsoft-defender-endpoint-mac.md).

> [!NOTE]
> Aşağıdaki özellikler şu anda macOS uç noktalarında desteklenmiyor:
>
> - Veri kaybını önleme
> - Canlı yanıt
> - Uç Nokta için Microsoft Defender Güvenlik Yönetimi

## <a name="microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender

Linux'ta Uç Nokta için Microsoft Defender, Linux sunucuları için engellemeli virüsten koruma (AV), uç noktada algılama ve yanıtlama (EDR) ve güvenlik açığı yönetimi özellikleri sunar. Aracıyı yapılandırmak ve yönetmek, taramaları başlatmak ve tehditleri yönetmek için tam komut satırı deneyimi de buna dahildir. En yaygın altı Linux Server dağılımının son sürümlerini destekliyoruz: RHEL 7.2+, CentOS Linux 7.2+, Ubuntu 16 LTS veya daha yüksek LTS, SLES 12+, Debian 9+ ve Oracle Linux 7.2. Linux'ta Uç Nokta için Microsoft Defender, Linux'ta Yeni, Ansible kullanılarak ya da mevcut Linux yapılandırma yönetim aracınız kullanılarak dağıtılabilir ve ya da yapılandırılabilir. Önemli özellikler ve avantajlar hakkında bilgi için, duyurularımızı [okuyun](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/Linux).

Nasıl başla ilgili daha fazla ayrıntı için Linux'ta Uç Nokta için Microsoft Defender belgelerini ziyaret [edin](microsoft-defender-endpoint-linux.md).


> [!NOTE]
> Aşağıdaki özellikler şu anda Linux uç noktalarında desteklemektedir:
>
> - Veri kaybını önleme
> - Canlı yanıt
> - Uç Nokta için Microsoft Defender Güvenlik Yönetimi

## <a name="microsoft-defender-for-endpoint-on-android"></a>Android'de Uç Nokta için Microsoft Defender

Android'de Uç Nokta için Microsoft Defender, Android 6.0 ve daha yüksek işletim sistemi çalıştıran cihazlar için mobil tehdit savunma çözümüdür. Hem Android Enterprise (İş Profili) hem de Cihaz Yöneticisi modları destekler. Android cihazlarda kimlik avı önleme, güvenli olmayan bağlantıları engelleme ve özel göstergelerin ayarını içeren web koruması sunuyoruz. Çözüm, kötü amaçlı yazılım ve istenmeyen olabilecek uygulamaları (PUA) tarar ve YAZıLıM VE Koşullu Erişim ile tümleştirme yoluyla ek ihlal Microsoft Endpoint Manager özellikleri sunar. Önemli özellikler ve avantajlar hakkında bilgi için, duyurularımızı [okuyun](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/Android).

Nasıl başla ilgili daha fazla ayrıntı için Android'de Uç Nokta için Microsoft Defender belgelerini ziyaret [edin](microsoft-defender-endpoint-android.md).

## <a name="microsoft-defender-for-endpoint-on-ios"></a>iOS'ta Uç Nokta için Microsoft Defender

iOS'ta Uç Nokta için Microsoft Defender, iOS 11.0 ve daha yüksek sürümü çalıştıran cihazlar için mobil tehdit savunma çözümüdür. Müşterinin kiracısı içinde kayıtlı olan (kayıtlı veya kaydı olmayan) cihazlar de desteklemektedir. Hem denetlenen hem de denetlenemeyen kayıtlı cihazlar desteklemektedir. iOS'ta kimlik avı önleme, güvenli olmayan bağlantıları engelleme, özel göstergeleri ayarlama ve jailbreak algılamayı içeren web koruması sunuyoruz. Önemli özellikler ve avantajlar hakkında daha fazla bilgi için, duyurularımızı [okuyun](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/bg-p/MicrosoftDefenderATPBlog/label-name/iOS).

Nasıl başla ilgili daha fazla ayrıntı için iOS belgelerine ilişkin Uç Nokta için Microsoft Defender'ı ziyaret [edin](microsoft-defender-endpoint-ios.md).

## <a name="licensing-requirements"></a>Lisans gereksinimleri

Uygun Lisanslı Kullanıcılar, uç nokta için Microsoft Defender'ı en fazla beş eşzamanlı cihaz üzerinde kullanabilir. Uç Nokta için Microsoft Defender bir müşteriden (CSP) Bulut Çözümü Sağlayıcısı satın alınabilir.

Müşteriler, Microsoft 365 A5/E5 veya Microsoft 365 Security kapsamında tek başına bir Uç Nokta için Microsoft Defender lisansı aracılığıyla macOS üzerinde Uç Nokta için Microsoft Defender'Microsoft 365 edinebilirsiniz.

Yakın zamanda duyurulan Android ve iOS'ta Uç Nokta için Microsoft Defender özellikleri, yukarıda belirtilen tekliflere uygun lisanslı kullanıcılar için uygun beş cihaz kapsamında dahil edilir.

Linux'ta Uç Nokta için Defender, hem ticari hem de eğitim müşterilerine yönelik olarak kullanılabilen Endpoint Server SKU için Defender aracılığıyla kullanılabilir.

Fiyatlandırma ve ek uygunluk gereksinimleri için lütfen hesap ekibinize veya CSP'ye ulaşın.
