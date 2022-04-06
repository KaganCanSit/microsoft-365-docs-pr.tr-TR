---
title: Configuration Manager kullanarak Windows cihazları Configuration Manager
description: Uç Configuration Manager için Defender hizmetine dahil etmek üzere yapılandırma paketini cihazlara dağıtmak üzere Kullanıcı Ayarları'nın kullanın.
keywords: sccm, cihaz yönetimi, cihazları yapılandırma ve cihazları yapılandırma Uç Nokta için Microsoft Defender cihazları ekleme
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
ms.date: 09/22/2021
ms.technology: mde
ms.openlocfilehash: d67a4ca067f16d74b15a1d7ece5c47d563f1a941
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471923"
---
# <a name="onboard-windows-devices-using-configuration-manager"></a>Configuration Manager kullanarak Windows cihazları Configuration Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Endpoint Configuration Manager dalı
- System Center 2012 R2 Configuration Manager

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointssccm-abovefoldlink)


Uç Nokta için Microsoft Defender hizmetinin uç noktalarını Configuration Manager için Uç Nokta için Microsoft Defender kullanabilirsiniz. 

Cihaz ekleme için kullanabileceğiniz çeşitli seçenekler vardır ve bu seçenekleri Configuration Manager:
- [System Center Configuration Manager kullanarak cihazları System Center Configuration Manager](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection)
- [Kiracı ekleme](/mem/configmgr/tenant-attach/)



Daha Windows Server 2012 R2 ve Windows Server 2016 için, ekleme adımlarını tamamladıktan sonra istemcilerini yapılandırmalı ve [System Center Endpoint Protection gerekir](onboard-downlevel.md#configure-and-update-system-center-endpoint-protection-clients).

> [!NOTE]
> Uç Nokta için Defender Hazır Deneyim [(OOBE) aşamasında eklemeyi desteklemez](https://answers.microsoft.com/windows/wiki/windows_10/how-to-complete-the-windows-10-out-of-box/47e3f943-f000-45e3-8c5c-9d85a1a0cf87) . Kullanıcıların yükleme veya yükseltme sonrasında OOBE'Windows tamamlandığından emin olun.
>
> Bir cihazın yerleşik olarak olup olduğunu sürekli kontrol etmek için Configuration Manager bir Configuration Manager kural oluşturmanın mümkün olduğunu unutmayın. Uygulama, paket ve programdan farklı türde bir nesnedir.
> Cihaz henüz eklememişse (bekleyen OOBE tamamlanma nedeniyle veya başka bir nedenle), kural durum değişikliğini algılayana kadar Configuration Manager cihazı eklemeye yeniden deneyin.
>
> Bu davranış, "OnboardingState" kayıt defteri değerinin (REG_DWORD türü) = 1 olup REG_DWORD bir kural denetimi oluşturarak gerçek olabilir.
> Bu kayıt defteri değeri, "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status" altında yer almaktadır.
Daha fazla bilgi için bkz. [System Center 2012 R2'de Algılama Yöntemlerini Yapılandırma Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682159\(v=technet.10\)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>Örnek koleksiyon ayarlarını yapılandırma

Her cihaz için, bir yapılandırma değeri ayarp, derin çözümleme için bir dosya göndermek için bir istek Microsoft 365 Defender cihazdan örnek toplanabilir olup olmadığını ifade edebilirsiniz.

> [!NOTE]
> Bu yapılandırma ayarları normalde tüm sistem Configuration Manager.

Bir cihazda örnek paylaşım ayarını değiştirmek için, Configuration Manager yapılandırma öğesi için bir uyumluluk kuralı değiştirebilirsiniz.

Bu kural, *hedefli cihazlarda kayıt* defteri anahtarının değerini şikayet olduğundan emin olmak için ayaran bir uyumluluk kuralı yapılandırma öğesidir.

Yapılandırma aşağıdaki kayıt defteri anahtarı girdisi aracılığıyla ayarlanır:

```text
Path: "HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection"
Name: "AllowSampleCollection"
Value: 0 or 1
```

Burada Anahtar türü bir D-WORD'tür. Olası değerler:

- 0: Bu cihazdan örnek paylaşıma izin vermiyor
- 1: Bu cihazdan tüm dosya türlerinin paylaşımına izin verir

Kayıt defteri anahtarının mevcut olması durumunda varsayılan değer 1'tir.

Uyumluluk Ayarlarını Değiştirme hakkında System Center Configuration Manager için bkz. [Uyumluluk Ayarları 2012 R2'de System Center giriş Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="other-recommended-configuration-settings"></a>Önerilen diğer yapılandırma ayarları

Cihazları hizmete verdikten sonra, aşağıdaki önerilen yapılandırma ayarlarıyla etkinleştirerek, dahil edilen tehdit koruması yeteneklerine sahip olmak önemlidir.

### <a name="device-collection-configuration"></a>Cihaz koleksiyonu yapılandırması

Endpoint Configuration Manager sürüm 2002 veya sonraki bir sürümünü kullanıyorsanız, dağıtımı sunucuları veya alt düzey istemcileri içerecek şekilde genişletmeyi seçebilirsiniz.

### <a name="next-generation-protection-configuration"></a>Yeni nesil koruma yapılandırması

Aşağıdaki yapılandırma ayarları önerilir:

#### <a name="scan"></a>Tarama

- USB sürücü gibi çıkarılabilir depolama cihazlarını tarama: Evet

#### <a name="real-time-protection"></a>Gerçek Zamanlı Koruma

- Davranış İzlemeyi Etkinleştir: Evet
- İndirme sırasında ve yükleme öncesinde İstenmeyen Olabilecek Uygulamalara karşı korumayı etkinleştir: Evet

#### <a name="cloud-protection-service"></a>Bulut Koruma Hizmeti

- Bulut Koruma Hizmeti üyelik türü: Gelişmiş üyelik

#### <a name="attack-surface-reduction"></a>Saldırı yüzeyini azaltma

Denetlenecek tüm kullanılabilir kuralları yapılandırma.

> [!NOTE]
> Bu etkinliklerin engellenmesi, yasal iş işlemlerini kesintiye uğratmaya neden olabilir. Her şeyi denetlemeye, hangilerinin güvenli olduğunu belirlemek ve ardından hatalı pozitif algılamaları olan uç noktalarda bu ayarları etkinleştirmek en iyi yaklaşımdır.

#### <a name="network-protection"></a>Ağ koruması

Denetim veya engelleme modunda ağ korumasını etkinleştirmeden önce, destek sayfasından edinilen kötü amaçlı yazılımdan koruma platform güncelleştirmesini [yüklemişsinizdir](https://support.microsoft.com/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing).

#### <a name="controlled-folder-access"></a>Denetimli klasör erişimi

Özelliği en az 30 gün boyunca denetim modunda etkinleştirin. Bu sürenin ardından algılamaları gözden geçirin ve korumalı dizinlere yazmasına izin verilen uygulamaların listesini oluşturun.

Daha fazla bilgi için Denetimli [klasör erişimini değerlendirme.](evaluate-controlled-folder-access.md)

## <a name="run-a-detection-test-to-verify-onboarding"></a>Eklemeyi doğrulamak için bir algılama testi çalıştırma

Cihazı işe seçtikten sonra, bir cihazın hizmete düzgün bir şekilde yer olduğunu doğrulamak için bir algılama testi çalıştırmayı seçebilirsiniz. Daha fazla bilgi için bkz[. Yeni eklenen bir cihazda algılama Uç Nokta için Microsoft Defender çalıştırma](run-detection-test.md).

## <a name="offboard-devices-using-configuration-manager"></a>Configuration Manager kullanan offboard Configuration Manager

Güvenlik nedeniyle, Offboard cihazları için kullanılan paketin süresi, indirildikten 30 gün sonra sona erer. Bir cihaza gönderilen süresi dolmuş offboard paketleri reddedilir. Bir çıkartan kullanım paketini indirirken, paketlerin son kullanma tarihi size bildirilecek ve paket adına bu paket de dahil edilecektir.

> [!NOTE]
> Ekleme ve çıkarma ilkeleri aynı cihazda aynı anda dağıtıldığından, öngörülemeyen zararlara neden olur.

### <a name="offboard-devices-using-microsoft-endpoint-manager-current-branch"></a>Geçerli dalı kullanan Microsoft Endpoint Manager cihazlar

Geçerli dalı Microsoft Endpoint Manager kullanıyorsanız bkz[. Çıkara bir yapılandırma dosyası oluşturma](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file).

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>System Center 2012 R2 Configuration Manager

1. Bir portaldan çıkartan <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender:</a>
    1. Gezinti bölmesinde, Uç  Noktalar **Cihaz yönetimi Ayarlar** \> **Çıkar'ı** \> \>**seçin**.  
    1. İşletim Windows 10 veya Windows 11 olarak seçin.
    1. Dağıtım yöntemi **alanında**, **2012/2012 System Center Configuration Manager 1511/1602 R2'yi seçin**.
    1. Paketi **indir'i** seçin ve dosyayı .zip kaydedin.

2. .zip dosyasının içeriğini, paketi dağıtacak olan ağ yöneticileri tarafından erişilebilen, paylaşılan, salt okunur bir konuma ayıklar. *WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd adlı bir dosyanız olmalıdır*.

3. Microsoft [2012 R2'de](/previous-versions/system-center/system-center-2012-R2/gg699369\(v=technet.10\)) Paketler ve Programlar makalesinde System Center Configuration Manager dağıtın.

   Paketin dağıtımı için önceden tanımlanmış bir cihaz koleksiyonu seçin.

> [!IMPORTANT]
> Offboard, cihazın algılayıcı verilerini portala göndermeyi durdurmaya neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere cihazdan alınan veriler 6 ay süreyle korunur.

## <a name="monitor-device-configuration"></a>Cihaz yapılandırmasını izleme

Geçerli dalı kullanıyorsanız Microsoft Endpoint Manager konsolundaki Uç Nokta için Defender yerleşik Defender Configuration Manager kullanın. Daha fazla bilgi için bkz. [Uç Nokta için Defender - Monitör](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

System Center 2012 R2 Configuration Manager, izleme iki bölümden oluşur:

1. Yapılandırma paketinin doğru dağıtıldığından ve ağ ağınız kapsamındaki cihazlarda çalıştırıldığından (veya başarıyla çalıştırıldığından) emin olun.

2. Cihazların Uç Nokta için Defender hizmetiyle uyumlu olup değildir (bu, cihazın ekleme işlemini tamamlayasını sağlar ve verileri hizmete bildirmeye devam eder).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>Yapılandırma paketinin doğru dağıtıldığından emin olun

1. Gezinti Configuration Manager gezinti **bölmesinin altındaki** İzleme'ye tıklayın.

2. Genel **Bakış'ı** ve ardından **Dağıtımlar'ı seçin**.

3. Paket adını içeren dağıtımı seçin.

4. Tamamlama İstatistikleri ve İçerik Durumu **altında durum göstergelerini** **gözden geçirebilirsiniz**.

    Başarısız dağıtımlar (Hata olan **cihazlar, Gereksinimleri** Karşılamıyor veya Başarısız durumları) **varsa, cihaz** sorunlarını gidermeniz gerekir. Daha fazla bilgi için bkz[. Ekleme Uç Nokta için Microsoft Defender sorunları giderme](troubleshoot-onboarding.md).

    :::image type="content" source="images/sccm-deployment.png" alt-text="Hatasız Configuration Manager dağıtımı gösteren en iyi uygulama" lightbox="images/sccm-deployment.png":::

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-defender-for-endpoint-service"></a>Cihazların Uç Nokta için Microsoft Defender hizmetiyle uyumlu olup Uç Nokta için Microsoft Defender denetleme

System Center 2012 R2'de dağıtımınızı izlemek için Configuration Manager için bir uyumluluk kuralı kurabilirsiniz.

Bu kural, *hedefli cihazlarda kayıt* defteri anahtarının değerini izleyen, düzeltilmeyen bir uyumluluk kuralı yapılandırma öğesidir.

Aşağıdaki kayıt defteri anahtarı girdisini izleme:

```console
Path: "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status"
Name: "OnboardingState"
Value: "1"
```

Daha fazla bilgi için bkz[. System Center 2012 R2 Uyumluluk ayarlarına giriş Configuration Manager](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="related-topics"></a>İlgili konular
- [Windows kullanarak diğer cihazları grup ilkesi](configure-endpoints-gp.md)
- [Mobil Windows araçlarını kullanarak diğer Cihaz Yönetimi cihaza ekleme](configure-endpoints-mdm.md)
- [Yerel Windows kullanarak cihazları ekleme](configure-endpoints-script.md)
- [Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarının katılımı](configure-endpoints-vdi.md)
- [Yeni eklenen bir cihazda algılama Uç Nokta için Microsoft Defender çalıştırma](run-detection-test.md)
- [Uç Nokta için Microsoft Defender ekleme sorunlarını giderme](troubleshoot-onboarding.md)
