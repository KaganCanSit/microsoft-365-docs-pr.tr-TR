---
title: Mobil Cihaz Yönetimi araçlarını kullanarak Windows cihazlarını ekleyin
description: Mobil Cihaz Yönetimi uç nokta için Defender hizmetine dahil etmek üzere cihazlara yapılandırma paketini dağıtmak üzere mobil cihaz araçlarını kullanın.
keywords: mdm, cihaz yönetimi, cihaz yönetimi, onboard Uç Nokta için Microsoft Defender cihazları, mdm kullanarak cihazları ekleme
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
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: f3b13df5b9368609e888b92cbba49a58a0db3008
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634767"
---
# <a name="onboard-windows-devices-using-mobile-device-management-tools"></a>Mobil Cihaz Yönetimi araçlarını kullanarak Windows cihazlarını ekleyin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsmdm-abovefoldlink)

En son cihazları yapılandırmak için mobil cihaz yönetimi (MDM) çözümlerini Windows 10 kullanabilirsiniz. Uç nokta için Defender, cihazları yönetmek için ilkeler oluşturmak OMA-URIs sağlama sağlayarak MDM'leri destekler.


Uç Nokta CSP için Defender'ı kullanma hakkında daha fazla bilgi için bkz. [WindowsAdvancedThreatProtection CSP](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) ve [WindowsAdvancedThreatProtection DDF dosyası](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx).

## <a name="before-you-begin"></a>Başlamadan önce

MDM Kaydını Microsoft Intune cihazında olması gerekir. Aksi takdirde, ayarlar başarıyla uygulanmaz.

MDM'nin birden çok cihazda etkinleştirilmesi hakkında daha fazla Microsoft Intune için bkz[. Cihaz kaydı (Microsoft Intune).](/mem/intune/enrollment/device-enrollment).

## <a name="onboard-devices-using-microsoft-intune"></a>Microsoft Intune kullanarak cihazları Microsoft Intune

Uç Nokta için [Defender'Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) çeşitli yolları görmek için PDF veya Dosya Ayarları'ne göz atabilirsiniz.[](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)

Aşağıdaki adımları takip [Intune](/mem/intune/protect/advanced-threat-protection-configure).

Uç Nokta CSP için Defender'ı kullanma hakkında daha fazla bilgi için bkz. [WindowsAdvancedThreatProtection CSP](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) ve [WindowsAdvancedThreatProtection DDF dosyası](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx).

> [!NOTE]
>
> - **Onboarded cihazlar için Durum** ilkesi salt okunur özellikleri kullanır ve düzelti değildir.
> - Tanılama veri raporlama sıklığı yapılandırması yalnızca 1703 sürümü Windows 10 cihazlarda kullanılabilir.


Dosya [dağıtımında Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) [yolları görmek](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) için PDF veya Dosya Uç Nokta için Microsoft Defender.

## <a name="run-a-detection-test-to-verify-onboarding"></a>Eklemeyi doğrulamak için bir algılama testi çalıştırma
Cihazı işe seçtikten sonra, bir cihazın hizmete düzgün bir şekilde yer olduğunu doğrulamak için bir algılama testi çalıştırmayı seçebilirsiniz. Daha fazla bilgi için bkz[. Yeni eklenen bir cihazda algılama Uç Nokta için Microsoft Defender çalıştırma](run-detection-test.md).


## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>Mobil cihazlar ve mobil cihazlar ile offboard Cihaz Yönetimi izleme

Güvenlik nedeniyle, Offboard cihazları için kullanılan paketin süresi, indirildikten 30 gün sonra sona erer. Bir cihaza gönderilen süresi dolmuş offboard paketleri reddedilir. Bir çıkartan kullanım paketi indirirken paketlerin son kullanma tarihi size bildirilecek ve paket adına bu paket de dahil edilecektir.

> [!NOTE]
> Ekleme ve çıkarma ilkeleri aynı cihazda aynı anda dağıtıldığından, öngörülemeyen zararlara neden olur.

1. Bir portaldan çıkartan <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender:</a>

   1. Gezinti bölmesinde, Uç Noktalar **Cihaz yönetimi Ayarlar** \> **Çıkar'ı** \>  \> **seçin**.

   1. İşletim Windows 10 veya Windows 11 olarak seçin.

   1. Dağıtım yöntemi **alanında,** Mobil Cihazlar **/ Cihaz Yönetimi'Microsoft Intune**.

   1. Paketi **indir'e** tıklayın ve dosyayı .zip kaydedin.

2. .zip dosyasının içeriğini, paketi dağıtacak olan ağ yöneticileri tarafından erişilebilen, paylaşılan, salt okunur bir konuma ayıklar. *WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding adlı bir dosyanız olmalıdır*.

3. Desteklenen Microsoft Intune OMA-URI ayarlarını dağıtmak için aşağıdaki özel yapılandırma ilkesine tıklayın.
   - OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
   - Tarih türü: Dize
   - Değer: [WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding dosyasının içeriğinden değeri kopyalayıp yapıştırın]

İlke ayarlarını değiştirme Microsoft Intune daha fazla bilgi için bkz[. Windows 10 ayarları ayarlarına Microsoft Intune](/mem/intune/configuration/custom-settings-windows-10).

> [!NOTE]
> Kapalı **durumdaki cihazlar için Durum** ilkesi salt okunur özellikleri kullanır ve düzelti değildir.

> [!IMPORTANT]
> Offboard, cihazın algılayıcı verilerini portala göndermeyi durdurmaya neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere cihazdan alınan veriler 6 ay süreyle korunur.

## <a name="related-topics"></a>İlgili konular
- [Windows araçlarını Grup İlkesi kullanarak ekleyin](configure-endpoints-gp.md)
- [Microsoft Endpoint Configuration Manager kullanarak Windows cihazlarını ekleyin](configure-endpoints-sccm.md)
- [Windows araçlarını yerel betik kullanarak ekleyin](configure-endpoints-script.md)
- [Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarının katılımı](configure-endpoints-vdi.md)
- [Yeni eklenen bir cihazda algılama Uç Nokta için Microsoft Defender çalıştırma](run-detection-test.md)
- [Uç Nokta için Microsoft Defender ekleme sorunlarını giderme](troubleshoot-onboarding.md)
