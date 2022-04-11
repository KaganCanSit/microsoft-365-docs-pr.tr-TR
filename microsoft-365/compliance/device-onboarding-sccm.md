---
title: Configuration Manager kullanarak Windows 10 ve Windows 11 cihazları ekleme
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Yapılandırma paketini hizmete eklenmeleri için cihazlara dağıtmak için Configuration Manager kullanın.
ms.openlocfilehash: 2cca9cc073ca08c7fabb19511a4253e4a682057a
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760723"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-configuration-manager"></a>Configuration Manager kullanarak Windows 10 ve Windows 11 cihazları ekleme

**Şunlar için geçerlidir:**

- [Microsoft 365 Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [İçeriden risk yönetimi](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

### <a name="onboard-devices-using-system-center-configuration-manager"></a>System Center Configuration Manager kullanarak cihazları ekleme

1. [Microsoft Uyumluluk merkezinden](https://compliance.microsoft.com/) yapılandırma paketini .zip dosyasını (*DeviceComplianceOnboardingPackage.zip*) alın.

2. Gezinti bölmesinde <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ayarlar**</a> >  **Cihaz EklemeOnboarding'i** >  seçin.

3. **Dağıtım yöntemi** alanında **Microsoft Endpoint Configuration Manager 2012/2012 R2/1511/1602'yi** seçin.

4. **Paketi indir'i** seçin ve .zip dosyasını kaydedin.

5. .zip dosyasının içeriğini, paketi dağıtacak ağ yöneticileri tarafından erişilebilen paylaşılan, salt okunur bir konuma ayıklayın. *DeviceComplianceOnboardingScript.cmd* adlı bir dosyanız olmalıdır.

6. [System Center 2012 R2 Configuration Manager'deki Paketler ve Programlar makalesindeki](/previous-versions/system-center/system-center-2012-R2/gg699369(v=technet.10)) adımları izleyerek paketi dağıtın.

7. Paketin dağıtılacağı önceden tanımlanmış bir cihaz koleksiyonu seçin.

> [!NOTE]
> Microsoft 365 bilgi koruması, İlk [Çalıştırma Deneyimi (OOBE)](https://answers.microsoft.com/en-us/windows/wiki/windows_10/how-to-complete-the-windows-10-out-of-box/47e3f943-f000-45e3-8c5c-9d85a1a0cf87) aşamasında ekleme işlemini desteklemez. Windows yükleme veya yükseltmeyi çalıştırdıktan sonra kullanıcıların OOBE'i tamamladığınızdan emin olun.

> [!TIP]
> Cihazı ekledikten sonra, bir cihazın hizmete düzgün şekilde eklendiğini doğrulamak için bir algılama testi çalıştırmayı seçebilirsiniz. Daha fazla bilgi için bkz. [Yeni eklenen Uç Nokta için Microsoft Defender cihazında algılama testi çalıştırma](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test).
>
> Bir cihazın eklenip eklenmediğini sürekli denetlemek için bir Configuration Manager uygulamasında algılama kuralı oluşturmanın mümkün olduğunu unutmayın. Uygulama, paket ve programdan farklı bir nesne türüdür.
> Bir cihaz henüz eklenmiyorsa (bekleyen OOBE tamamlaması veya başka bir nedenden dolayı) Configuration Manager kural durum değişikliğini algılayana kadar cihazı eklemeyi yeniden dener.
>
> Bu davranış, "OnboardingState" kayıt defteri değerinin (REG_DWORD türü) = 1 olup olmadığını denetleyerek bir algılama kuralı denetimi oluşturularak gerçekleştirilebilir.
> Bu kayıt defteri değeri "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status" altında bulunur.
Daha fazla bilgi için bkz. [System Center 2012 R2 Configuration Manager'de Algılama Yöntemlerini Yapılandırma](/previous-versions/system-center/system-center-2012-R2/gg682159(v=technet.10)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>Örnek koleksiyon ayarlarını yapılandırma

Her cihaz için, ayrıntılı analiz için bir dosya göndermek üzere Microsoft Defender Güvenlik Merkezi aracılığıyla bir istek yapıldığında cihazdan örneklerin toplanıp toplanmayacağını belirtmek için bir yapılandırma değeri ayarlayabilirsiniz.

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

Nerede:

Anahtar türü bir D-WORD'dür.

Olası değerler şunlardır:

- 0 - bu cihazdan örnek paylaşımına izin vermez
- 1 - Bu cihazdan tüm dosya türlerinin paylaşılmasına izin verir

Kayıt defteri anahtarının mevcut olmaması durumunda varsayılan değer 1'dir.

System Center Configuration Manager Uyumluluğu hakkında daha fazla bilgi için bkz. [System Center 2012 R2 Configuration Manager'da uyumluluk ayarlarına giriş](/previous-versions/system-center/system-center-2012-R2/gg682139(v=technet.10)).


## <a name="other-recommended-configuration-settings"></a>Önerilen diğer yapılandırma ayarları

Cihazları hizmete ekledikten sonra, aşağıdaki önerilen yapılandırma ayarlarıyla etkinleştirerek dahil edilen tehdit koruması özelliklerinden yararlanmak önemlidir.

### <a name="device-collection-configuration"></a>Cihaz koleksiyonu yapılandırması

Endpoint Configuration Manager, sürüm 2002 veya üzerini kullanıyorsanız, sunucuları veya alt düzey istemcileri içerecek şekilde dağıtımı genişletmeyi seçebilirsiniz.

### <a name="next-generation-protection-configuration"></a>Yeni nesil koruma yapılandırması

Aşağıdaki yapılandırma ayarları önerilir:

**Tarama**

- USB sürücüleri gibi çıkarılabilir depolama cihazlarını tara: Evet

**Gerçek Zamanlı Koruma**

- Davranış İzlemeyi Etkinleştir: Evet
- İndirme sırasında ve yükleme öncesinde İstenmeyebilecek Uygulamalara karşı korumayı etkinleştirin: Evet

**Bulut Koruma Hizmeti**

- Cloud Protection Hizmeti üyelik türü: Gelişmiş üyelik

**Saldırı yüzeyini azaltma** Denetim için tüm kullanılabilir kuralları yapılandırın.

> [!NOTE]
> Bu etkinliklerin engellenmesi meşru iş süreçlerini kesintiye uğratabilir. En iyi yaklaşım, her şeyi denetime ayarlamak, hangilerinin güvenli olduğunu belirlemek ve ardından hatalı pozitif algılamaları olmayan uç noktalarda bu ayarları etkinleştirmektir.

**Ağ koruması**

Denetim veya blok modunda ağ korumasını etkinleştirmeden önce, [destek sayfasından](https://support.microsoft.com/en-us/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing) edinilebilen kötü amaçlı yazılımdan koruma platformu güncelleştirmesini yüklediğinizden emin olun.

**Denetimli klasör erişimi**

Özelliği en az 30 gün boyunca denetim modunda etkinleştirin. Bu sürenin sonunda algılamaları gözden geçirin ve korumalı dizinlere yazmasına izin verilen uygulamaların listesini oluşturun.

Daha fazla bilgi için bkz [. Denetimli klasör erişimini değerlendirme](/windows/security/threat-protection/microsoft-defender-atp/evaluate-controlled-folder-access).

## <a name="offboard-devices-using-configuration-manager"></a>Configuration Manager kullanarak cihazları çıkarma

Güvenlik nedeniyle, cihazları kullanıma almak için kullanılan paketin süresi, indirildiği tarihten 30 gün sonra dolar. Bir cihaza gönderilen süresi dolan çıkarma paketleri reddedilir. Bir çıkarma paketini indirirken, paketlerin son kullanma tarihi size bildirilir ve paket adına da eklenir.

> [!NOTE]
> Ekleme ve çıkarma ilkeleri aynı cihazda aynı anda dağıtılmamalıdır, aksi takdirde bu öngörülemeyen çakışmalara neden olur.

### <a name="offboard-devices-using-microsoft-endpoint-configuration-manager-current-branch"></a>Geçerli dalı kullanarak cihazları Microsoft Endpoint Configuration Manager çıkarma

Geçerli dal Microsoft Endpoint Configuration Manager kullanıyorsanız bkz. [Çıkarma yapılandırma dosyası oluşturma](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file).

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>System Center 2012 R2 Configuration Manager kullanarak cihazları çıkarma

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi'dan</a> çıkarma paketini alın:

2. Gezinti bölmesinde <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ayarlar**</a> >   **Cihaz eklemeYeni**>  **ekleme'yi** seçin.

3. İşletim sistemi olarak Windows 10 seçin.

4. **Dağıtım yöntemi** alanında **Microsoft Endpoint Configuration Manager 2012/2012 R2/1511/1602'yi** seçin.

5. **Paketi indir'i** seçin ve .zip dosyasını kaydedin.

6. .zip dosyasının içeriğini, paketi dağıtacak ağ yöneticileri tarafından erişilebilen paylaşılan, salt okunur bir konuma ayıklayın. *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd* adlı bir dosyanız olmalıdır.

7. [System Center 2012 R2 Configuration Manager'deki Paketler ve Programlar makalesindeki](/previous-versions/system-center/system-center-2012-R2/gg699369(v=technet.10)) adımları izleyerek paketi dağıtın.

8. Paketin dağıtılacağı önceden tanımlanmış bir cihaz koleksiyonu seçin.

> [!IMPORTANT]
> Kullanıma alma, cihazın portala algılayıcı verileri göndermeyi durdurmasına neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere cihazdaki veriler 6 aya kadar saklanır.

## <a name="monitor-device-configuration"></a>Cihaz yapılandırmasını izleme

Geçerli Microsoft Endpoint Configuration Manager dal kullanıyorsanız, Configuration Manager konsolundaki yerleşik Uç Nokta için Microsoft Defender panosunu kullanın. Daha fazla bilgi için bkz. [Microsoft Defender Gelişmiş Tehdit Koruması - İzleyici](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

System Center 2012 R2 Configuration Manager kullanıyorsanız izleme iki bölümden oluşur:

1. Yapılandırma paketinin doğru dağıtıldığını ve ağınızdaki cihazlarda çalıştığını (veya başarıyla çalıştırıldığını) onaylayın.

2. Cihazların Microsoft 365 cihaz ekleme hizmetiyle uyumlu olup olmadığını denetleme (bu, cihazın ekleme işlemini tamamlayabilmesini ve verileri hizmete bildirmeye devam etmesini sağlar).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>Yapılandırma paketinin doğru dağıtıldığını onaylayın

1. Configuration Manager konsolunda, gezinti bölmesinin alt kısmındaki **İzleme'ye** tıklayın.

2. **Genel Bakış'ı** ve ardından **Dağıtımlar'ı** seçin.

3. Dağıtımda paket adını seçin.

4. **Tamamlanma İstatistikleri** ve **İçerik Durumu** altındaki durum göstergelerini gözden geçirin.

    Başarısız dağıtımlar varsa ( **Hata**, **Gereksinimler Karşılanmadı** veya **Başarısız durumlarına** sahip cihazlar) cihazlarda sorun gidermeniz gerekebilir. Daha fazla bilgi için bkz. [Microsoft Defender Gelişmiş Tehdit Koruması ekleme sorunlarını giderme](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding).

    ![Configuration Manager hatasız başarılı dağıtım gösteriyor.](../media/sccm-deployment.png)

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-365-endpoint-data-loss-prevention-service"></a>Cihazların Microsoft 365 Uç Nokta veri kaybı önleme hizmetiyle uyumlu olup olmadığını denetleyin

Dağıtımınızı izlemek için System Center 2012 R2 Configuration Manager yapılandırma öğesi için bir uyumluluk kuralı ayarlayabilirsiniz.

> [!NOTE]
> Bu yordam ve kayıt defteri girdisi Hem Uç Nokta DLP'sine hem de Uç Nokta için Defender'a uygulanır.

Bu kural, hedeflenen cihazlarda bir kayıt defteri anahtarının değerini izleyen *düzeltilmeyen* bir uyumluluk kuralı yapılandırma öğesi olmalıdır.

Aşağıdaki kayıt defteri anahtarı girdisini izleyin:

```text
Path: "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status"
Name: "OnboardingState"
Value: "1"
```

Daha fazla bilgi için bkz. [System Center 2012 R2 Configuration Manager'de uyumluluk ayarlarına giriş](/previous-versions/system-center/system-center-2012-R2/gg682139(v=technet.10)).

## <a name="related-topics"></a>İlgili konular

- [grup ilkesi kullanarak Windows 10 ve Windows 11 cihazları ekleme](device-onboarding-gp.md)
- [Mobil Cihaz Yönetimi araçlarını kullanan Windows 10 ve Windows 11 cihazlarının katılımı](device-onboarding-mdm.md)
- [Yerel bir komut dosyası kullanan Windows 10 ve Windows 11 cihazlarının katılımı](device-onboarding-script.md)
- [Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarının katılımı](device-onboarding-vdi.md)
- [Yeni eklenen bir Uç Nokta için Microsoft Defender cihazında algılama testi çalıştırma](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Microsoft Defender Gelişmiş Tehdit Koruması ekleme sorunlarını giderme](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
