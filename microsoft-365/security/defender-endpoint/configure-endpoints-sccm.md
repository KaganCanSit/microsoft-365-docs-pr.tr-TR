---
title: Configuration Manager kullanarak Windows cihazları ekleme
description: Uç Nokta için Defender hizmetine eklenmeleri için yapılandırma paketini cihazlara dağıtmak için Configuration Manager kullanın.
keywords: sccm kullanarak cihazları ekleme, cihaz yönetimi, Uç Nokta için Microsoft Defender cihazları yapılandırma
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
ms.openlocfilehash: d60d01bd2a77d992110f85967196390f3dceae3d
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873720"
---
# <a name="onboard-windows-devices-using-configuration-manager"></a>Configuration Manager kullanarak Windows cihazları ekleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Geçerli dalı Microsoft Endpoint Configuration Manager
- System Center 2012 R2 Configuration Manager

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointssccm-abovefoldlink)


Uç noktaları Uç Nokta için Microsoft Defender hizmetine eklemek için Configuration Manager kullanabilirsiniz. 

Configuration Manager kullanarak cihazları eklemek için kullanabileceğiniz çeşitli seçenekler vardır:
- [System Center Configuration Manager kullanarak cihazları ekleme](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection)
- [Kiracı ekleme](/mem/configmgr/tenant-attach/)



Windows Server 2012 R2 ve Windows Server 2016 için, ekleme adımlarını tamamladıktan sonra[, System Center Endpoint Protection istemcilerini yapılandırmanız ve güncelleştirmeniz](onboard-downlevel.md#configure-and-update-system-center-endpoint-protection-clients) gerekir.

> [!NOTE]
> Uç Nokta için Defender, İlk [Çalıştırma Deneyimi (OOBE)](/windows-hardware/test/assessments/out-of-box-experience) aşamasında ekleme işlemini desteklemez. Windows yükleme veya yükseltmeyi çalıştırdıktan sonra kullanıcıların OOBE'i tamamladığınızdan emin olun.
>
> Bir cihazın eklenip eklenmediğini sürekli denetlemek için bir Configuration Manager uygulamasında algılama kuralı oluşturmanın mümkün olduğunu unutmayın. Uygulama, paket ve programdan farklı bir nesne türüdür.
> Bir cihaz henüz eklenmiyorsa (bekleyen OOBE tamamlaması veya başka bir nedenden dolayı) Configuration Manager kural durum değişikliğini algılayana kadar cihazı eklemeyi yeniden dener.
>
> Bu davranış, "OnboardingState" kayıt defteri değerinin (REG_DWORD türü) = 1 olup olmadığını denetleyerek bir algılama kuralı denetimi oluşturularak gerçekleştirilebilir.
> Bu kayıt defteri değeri "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status" altında bulunur.
Daha fazla bilgi için bkz. [System Center 2012 R2 Configuration Manager'de Algılama Yöntemlerini Yapılandırma](/previous-versions/system-center/system-center-2012-R2/gg682159\(v=technet.10\)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>Örnek koleksiyon ayarlarını yapılandırma

Her cihaz için, ayrıntılı analiz için bir dosya göndermek üzere Microsoft 365 Defender aracılığıyla bir istek yapıldığında cihazdan örneklerin toplanıp toplanmayacağını belirtmek için bir yapılandırma değeri ayarlayabilirsiniz.

> [!NOTE]
> Bu yapılandırma ayarları genellikle Configuration Manager aracılığıyla yapılır.

Bir cihazdaki örnek paylaşım ayarını değiştirmek için Configuration Manager'da yapılandırma öğesi için bir uyumluluk kuralı ayarlayabilirsiniz.

Bu kural, şikayette olduklarından emin olmak için hedeflenen cihazlarda bir kayıt defteri anahtarının değerini ayarlayan *düzeltici* bir uyumluluk kuralı yapılandırma öğesi olmalıdır.

Yapılandırma aşağıdaki kayıt defteri anahtarı girdisi aracılığıyla ayarlanır:

```text
Path: "HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection"
Name: "AllowSampleCollection"
Value: 0 or 1
```

Burada Anahtar türü bir D-WORD'dür. Olası değerler şunlardır:

- 0: Bu cihazdan örnek paylaşımına izin vermez
- 1: Bu cihazdan tüm dosya türlerinin paylaşılmasına izin verir

Kayıt defteri anahtarının mevcut olmaması durumunda varsayılan değer 1'dir.

System Center Configuration Manager Uyumluluğu hakkında daha fazla bilgi için bkz. [System Center 2012 R2 Configuration Manager'da uyumluluk ayarlarına giriş](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="other-recommended-configuration-settings"></a>Önerilen diğer yapılandırma ayarları

Cihazları hizmete ekledikten sonra, aşağıdaki önerilen yapılandırma ayarlarıyla etkinleştirerek dahil edilen tehdit koruması özelliklerinden yararlanmak önemlidir.

### <a name="device-collection-configuration"></a>Cihaz koleksiyonu yapılandırması

Endpoint Configuration Manager, sürüm 2002 veya üzerini kullanıyorsanız, sunucuları veya alt düzey istemcileri içerecek şekilde dağıtımı genişletmeyi seçebilirsiniz.

### <a name="next-generation-protection-configuration"></a>Yeni nesil koruma yapılandırması

Aşağıdaki yapılandırma ayarları önerilir:

#### <a name="scan"></a>Tarama

- USB sürücüleri gibi çıkarılabilir depolama cihazlarını tara: Evet

#### <a name="real-time-protection"></a>Gerçek Zamanlı Koruma

- Davranış İzlemeyi Etkinleştir: Evet
- İndirme sırasında ve yükleme öncesinde İstenmeyebilecek Uygulamalara karşı korumayı etkinleştirin: Evet

#### <a name="cloud-protection-service"></a>Bulut Koruma Hizmeti

- Cloud Protection Hizmeti üyelik türü: Gelişmiş üyelik

#### <a name="attack-surface-reduction"></a>Saldırı yüzeyini azaltma

Denetim için tüm kullanılabilir kuralları yapılandırın.

> [!NOTE]
> Bu etkinliklerin engellenmesi meşru iş süreçlerini kesintiye uğratabilir. En iyi yaklaşım, her şeyi denetime ayarlamak, hangilerinin güvenli olduğunu belirlemek ve ardından hatalı pozitif algılamaları olmayan uç noktalarda bu ayarları etkinleştirmektir.

#### <a name="network-protection"></a>Ağ koruması

Denetim veya blok modunda ağ korumasını etkinleştirmeden önce, [destek sayfasından](https://support.microsoft.com/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing) edinilebilen kötü amaçlı yazılımdan koruma platformu güncelleştirmesini yüklediğinizden emin olun.

#### <a name="controlled-folder-access"></a>Denetimli klasör erişimi

Özelliği en az 30 gün boyunca denetim modunda etkinleştirin. Bu sürenin sonunda algılamaları gözden geçirin ve korumalı dizinlere yazmasına izin verilen uygulamaların listesini oluşturun.

Daha fazla bilgi için bkz [. Denetimli klasör erişimini değerlendirme](evaluate-controlled-folder-access.md).

## <a name="run-a-detection-test-to-verify-onboarding"></a>Ekleme işlemini doğrulamak için algılama testi çalıştırma

Cihazı ekledikten sonra, bir cihazın hizmete düzgün şekilde eklendiğini doğrulamak için bir algılama testi çalıştırmayı seçebilirsiniz. Daha fazla bilgi için bkz. [Yeni eklenen Uç Nokta için Microsoft Defender cihazında algılama testi çalıştırma](run-detection-test.md).

## <a name="offboard-devices-using-configuration-manager"></a>Configuration Manager kullanarak cihazları çıkarma

Güvenlik nedeniyle, cihazları kullanıma almak için kullanılan paketin süresi, indirildiği tarihten 30 gün sonra dolar. Bir cihaza gönderilen süresi dolan çıkarma paketleri reddedilir. Bir çıkarma paketini indirirken, paketlerin son kullanma tarihi size bildirilir ve paket adına da eklenir.

> [!NOTE]
> Ekleme ve çıkarma ilkeleri aynı cihazda aynı anda dağıtılmamalıdır, aksi takdirde bu öngörülemeyen çakışmalara neden olur.

### <a name="offboard-devices-using-microsoft-endpoint-manager-current-branch"></a>Geçerli dalı kullanarak cihazları Microsoft Endpoint Manager çıkarma

Geçerli dal Microsoft Endpoint Manager kullanıyorsanız bkz. [Çıkarma yapılandırma dosyası oluşturma](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file).

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>System Center 2012 R2 Configuration Manager kullanarak cihazları çıkarma

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalından</a> çıkarma paketini alın:
    1. Gezinti bölmesinde **Uç Noktalar** \> **Cihaz yönetimi** \>**Çıkarma'yı Ayarlar** \> seçin.  
    1. İşletim sistemi olarak Windows 10 veya Windows 11 seçin.
    1. **Dağıtım yöntemi** alanında **System Center Configuration Manager 2012/2012 R2/1511/1602'yi** seçin.
    1. **Paketi indir'i** seçin ve .zip dosyasını kaydedin.

2. .zip dosyasının içeriğini, paketi dağıtacak ağ yöneticileri tarafından erişilebilen paylaşılan, salt okunur bir konuma ayıklayın. *WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd* adlı bir dosyanız olmalıdır.

3. [System Center 2012 R2 Configuration Manager'deki Paketler ve Programlar makalesindeki](/previous-versions/system-center/system-center-2012-R2/gg699369\(v=technet.10\)) adımları izleyerek paketi dağıtın.

   Paketin dağıtılacağı önceden tanımlanmış bir cihaz koleksiyonu seçin.

> [!IMPORTANT]
> Kullanıma alma, cihazın portala algılayıcı verileri göndermeyi durdurmasına neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere cihazdaki veriler 6 aya kadar saklanır.

## <a name="monitor-device-configuration"></a>Cihaz yapılandırmasını izleme

Geçerli Microsoft Endpoint Manager dal kullanıyorsanız, Configuration Manager konsolundaki yerleşik Uç Nokta için Defender panosunu kullanın. Daha fazla bilgi için bkz [. Uç Nokta için Defender - İzleyici](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

System Center 2012 R2 Configuration Manager kullanıyorsanız izleme iki bölümden oluşur:

1. Yapılandırma paketinin doğru dağıtıldığını ve ağınızdaki cihazlarda çalıştığını (veya başarıyla çalıştırıldığını) onaylayın.

2. Cihazların Uç Nokta için Defender hizmetiyle uyumlu olup olmadığını denetleme (bu, cihazın ekleme işlemini tamamlayabilmesini ve verileri hizmete bildirmeye devam etmesini sağlar).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>Yapılandırma paketinin doğru dağıtıldığını onaylayın

1. Configuration Manager konsolunda, gezinti bölmesinin alt kısmındaki **İzleme'ye** tıklayın.

2. **Genel Bakış'ı** ve ardından **Dağıtımlar'ı** seçin.

3. Dağıtımda paket adını seçin.

4. **Tamamlanma İstatistikleri** ve **İçerik Durumu** altındaki durum göstergelerini gözden geçirin.

    Başarısız dağıtımlar varsa ( **Hata**, **Gereksinimler Karşılanmadı** veya **Başarısız durumlarına** sahip cihazlar) cihazlarda sorun gidermeniz gerekebilir. Daha fazla bilgi için bkz[. Uç Nokta için Microsoft Defender ekleme sorunlarını giderme](troubleshoot-onboarding.md).

    :::image type="content" source="images/sccm-deployment.png" alt-text="Hatasız başarılı dağıtımı gösteren Configuration Manager" lightbox="images/sccm-deployment.png":::

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-defender-for-endpoint-service"></a>Cihazların Uç Nokta için Microsoft Defender hizmetiyle uyumlu olup olmadığını denetleyin

Dağıtımınızı izlemek için System Center 2012 R2 Configuration Manager yapılandırma öğesi için bir uyumluluk kuralı ayarlayabilirsiniz.

Bu kural, hedeflenen cihazlarda bir kayıt defteri anahtarının değerini izleyen *düzeltilmeyen* bir uyumluluk kuralı yapılandırma öğesi olmalıdır.

Aşağıdaki kayıt defteri anahtarı girdisini izleyin:

```console
Path: "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status"
Name: "OnboardingState"
Value: "1"
```

Daha fazla bilgi için bkz. [System Center 2012 R2 Configuration Manager'de uyumluluk ayarlarına giriş](/previous-versions/system-center/system-center-2012-R2/gg682139\(v=technet.10\)).

## <a name="related-topics"></a>İlgili konular
- [Windows araçlarını Grup İlkesi kullanarak ekleyin](configure-endpoints-gp.md)
- [Mobil Cihaz Yönetimi araçlarını kullanarak Windows cihazlarını ekleyin](configure-endpoints-mdm.md)
- [Windows araçlarını yerel betik kullanarak ekleyin](configure-endpoints-script.md)
- [Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarının katılımı](configure-endpoints-vdi.md)
- [Yeni eklenen bir Uç Nokta için Microsoft Defender cihazında algılama testi çalıştırma](run-detection-test.md)
- [Uç Nokta için Microsoft Defender ekleme sorunlarını giderme](troubleshoot-onboarding.md)
