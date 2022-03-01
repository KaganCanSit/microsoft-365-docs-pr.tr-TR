---
title: Configuration Manager Windows 10 11 Windows cihaz ekleme ve kullanma
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
description: Yapılandırma paketini hizmete dahil etmek üzere cihazlara dağıtmak için Configuration Manager'i kullanın.
ms.openlocfilehash: 9f9edc9543a446f98622ff80d8cceec406a2658a
ms.sourcegitcommit: 8eca41cd21280ffcb1f50cafce7a934e5544f302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2021
ms.locfileid: "62999582"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-configuration-manager"></a>Configuration Manager Windows 10 11 Windows cihaz ekleme ve kullanma

**Aşağıdakiler için geçerlidir:**

- [Microsoft 365 Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [Insider risk yönetimi](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

### <a name="onboard-devices-using-system-center-configuration-manager"></a>System Center Configuration Manager kullanarak cihazları System Center Configuration Manager

1. Microsoft Uyumluluk Merkezi'.zip (*DeviceComplianceOnboardingPackage.zip*) [yapılandırma paketini edin.](https://compliance.microsoft.com/)

2. Gezinti bölmesinde,Device <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank"></a> > **OnboardingOnboarding** >  **Ayarlar'ı seçin**.

3. Dağıtım yöntemi **alanında**, **2012/2012 R2/1511/1602 Microsoft Endpoint Configuration Manager'yi seçin**.

4. Paketi **indir'i** seçin ve dosyayı .zip kaydedin.

5. .zip dosyasının içeriğini, paketi dağıtacak olan ağ yöneticileri tarafından erişilebilen, paylaşılan, salt okunur bir konuma ayıklar. *DeviceComplianceOnboardingScript.cmd adlı bir dosyanız olmalıdır*.

6. [2012 R2 Configuration Manager'da](/previous-versions/system-center/system-center-2012-R2/gg699369(v=technet.10)) Paketler ve Programlar makalesinde System Center dağıtın.

7. Paketin dağıtımı için önceden tanımlanmış bir cihaz koleksiyonu seçin.

> [!NOTE]
> Microsoft 365 koruması, kutuda Olmayan Deneyim [(OOBE) aşamasında eklemeyi desteklemez](https://answers.microsoft.com/en-us/windows/wiki/windows_10/how-to-complete-the-windows-10-out-of-box/47e3f943-f000-45e3-8c5c-9d85a1a0cf87). Kullanıcıların yükleme veya yükseltme sonrasında OOBE'Windows tamamlandığından emin olun.

> [!TIP]
> Cihazı işe seçtikten sonra, bir cihazın hizmete düzgün bir şekilde yer olduğunu doğrulamak için bir algılama testi çalıştırmayı seçebilirsiniz. Daha fazla bilgi için bkz [. Yeni eklenen Uç nokta cihazı için Microsoft Defender'da algılama testi çalıştırma](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test).
>
> Bir cihazın yerleşik olup olduğunu sürekli olarak kontrol etmek için Configuration Manager uygulamasında bir algılama kuralı oluşturanın mümkün olduğunu unutmayın. Uygulama, paket ve programdan farklı türde bir nesnedir.
> Cihaz henüz eklememişse (bekleyen OOBE tamamlanma nedeniyle veya başka bir nedenle), kural durum değişikliğini algılayana kadar Configuration Manager cihazı eklemeyi yeniden denetir.
>
> Bu davranış, "OnboardingState" kayıt defteri değerinin (REG_DWORD türü) = 1 olup REG_DWORD bir kural denetimi oluşturarak gerçek olabilir.
> Bu kayıt defteri değeri, "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status" altında yer almaktadır.
Daha fazla bilgi için bkz. [R2 Yapılandırma Yöneticisi'System Center Algılama Yöntemlerini Yapılandırma](/previous-versions/system-center/system-center-2012-R2/gg682159(v=technet.10)#step-4-configure-detection-methods-to-indicate-the-presence-of-the-deployment-type).

### <a name="configure-sample-collection-settings"></a>Örnek koleksiyon ayarlarını yapılandırma

Her cihaz için, derin çözümleme için bir dosya göndermek için bir istek göndererek, Microsoft Defender Güvenlik Merkezi örneklerin cihazdan toplanabilir olup olmadığını ifade etmek için bir yapılandırma değeri ayarlayın.

> [!NOTE]
> Bu yapılandırma ayarları genellikle Configuration Manager aracılığıyla yapılır.

Bir cihaza örnek paylaşım ayarını değiştirmek için Configuration Manager'da yapılandırma öğesi için bir uyumluluk kuralı değiştirebilirsiniz.

Bu kural, *hedefli cihazlarda kayıt* defteri anahtarının değerini şikayet olduğundan emin olmak için ayaran bir uyumluluk kuralı yapılandırma öğesidir.

Yapılandırma aşağıdaki kayıt defteri anahtarı girdisi aracılığıyla ayarlanır:

```
Path: “HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection”
Name: "AllowSampleCollection"
Value: 0 or 1
```
Burada:<br>
Anahtar türü bir D-WORD'tür. <br>
Olası değerler:
- 0 - Bu cihazdan örnek paylaşıma izin vermiyor
- 1 - Bu cihazdan tüm dosya türlerinin paylaşımına izin verir

Kayıt defteri anahtarının mevcut olması durumunda varsayılan değer 1'tir.

Uyumluluk Yönetimi hakkında daha System Center Configuration Manager için bkz. [2012 R2 Configuration Manager'da System Center ayarlarına giriş](/previous-versions/system-center/system-center-2012-R2/gg682139(v=technet.10)).


## <a name="other-recommended-configuration-settings"></a>Önerilen diğer yapılandırma ayarları
Cihazları hizmete verdikten sonra, aşağıdaki önerilen yapılandırma ayarlarıyla etkinleştirerek, dahil edilen tehdit koruması yeteneklerine sahip olmak önemlidir.

### <a name="device-collection-configuration"></a>Cihaz koleksiyonu yapılandırması
Uç Nokta Yapılandırma Yöneticisi (2002 veya sonraki bir sürüm) kullanıyorsanız, sunucuları veya alt düzey istemcileri içerecek şekilde dağıtımı genişletmeyi seçebilirsiniz.


### <a name="next-generation-protection-configuration"></a>Yeni nesil koruma yapılandırması

Aşağıdaki yapılandırma ayarları önerilir:

**Tarama**

- USB sürücü gibi çıkarılabilir depolama cihazlarını tarama: Evet

**Gerçek Zamanlı Koruma**

- Davranış İzlemeyi Etkinleştir: Evet
- İndirme sırasında ve yükleme öncesinde İstenmeyen Olabilecek Uygulamalara karşı korumayı etkinleştir: Evet

**Bulut Koruma Hizmeti**

- Bulut Koruma Hizmeti üyelik türü: Gelişmiş üyelik

**Saldırı yüzeyini azaltma** Denetlenecek tüm kullanılabilir kuralları yapılandırma.

> [!NOTE]
> Bu etkinliklerin engellenmesi, yasal iş işlemlerini kesintiye uğratmaya neden olabilir. Her şeyi denetlemeye, hangilerinin güvenli olduğunu belirlemek ve ardından hatalı pozitif algılamaları olan uç noktalarda bu ayarları etkinleştirmek en iyi yaklaşımdır.

**Ağ koruması**

Denetim veya engelleme modunda ağ korumasını etkinleştirmeden önce, destek sayfasından edinilen kötü amaçlı yazılımdan koruma platform güncelleştirmesini [yüklemişsinizdir](https://support.microsoft.com/en-us/help/4560203/windows-defender-anti-malware-platform-binaries-are-missing).


**Denetimli klasör erişimi**

Özelliği en az 30 gün boyunca denetim modunda etkinleştirin. Bu sürenin ardından algılamaları gözden geçirin ve korumalı dizinlere yazmasına izin verilen uygulamaların listesini oluşturun.

Daha fazla bilgi için Denetimli [klasör erişimini değerlendirme.](/windows/security/threat-protection/microsoft-defender-atp/evaluate-controlled-folder-access)


## <a name="offboard-devices-using-configuration-manager"></a>Configuration Manager kullanan offboard cihazları

Güvenlik nedeniyle, Offboard cihazları için kullanılan paketin süresi, indirildikten 30 gün sonra sona erer. Bir cihaza gönderilen süresi dolmuş offboard paketleri reddedilir. Bir çıkartan kullanım paketini indirirken, paketlerin son kullanma tarihi size bildirilecek ve paket adına bu paket de dahil edilecektir.

> [!NOTE]
> Ekleme ve çıkarma ilkeleri aynı cihazda aynı anda dağıtıldığından, öngörülemeyen zararlara neden olur.

### <a name="offboard-devices-using-microsoft-endpoint-configuration-manager-current-branch"></a>Geçerli dalı kullanan Microsoft Endpoint Configuration Manager cihazlar

Geçerli dalınız Microsoft Endpoint Configuration Manager bkz[. Çıkara bir yapılandırma dosyası oluşturma](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#create-an-offboarding-configuration-file).

### <a name="offboard-devices-using-system-center-2012-r2-configuration-manager"></a>System Center 2012 R2 Configuration Manager kullanan offboard cihazları

1. Bir panodan çıkar <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">paketine Microsoft 365 uyumluluk merkezi</a>:

2. Gezinti bölmesinde,Device <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank"></a> >  **onboardingOffboarding Ayarlar'ı**>  **seçin**.

3. İşletim Windows 10 olarak iş'i seçin.

4. Dağıtım yöntemi **alanında**, **2012/2012 R2/1511/1602 Microsoft Endpoint Configuration Manager'yi seçin**.

5. Paketi **indir'i** seçin ve dosyayı .zip kaydedin.

6. .zip dosyasının içeriğini, paketi dağıtacak olan ağ yöneticileri tarafından erişilebilen, paylaşılan, salt okunur bir konuma ayıklar. *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd adlı bir dosyanız olmalıdır*.

7. [2012 R2 Configuration Manager'da](/previous-versions/system-center/system-center-2012-R2/gg699369(v=technet.10)) Paketler ve Programlar makalesinde System Center dağıtın.

8. Paketin dağıtımı için önceden tanımlanmış bir cihaz koleksiyonu seçin.

> [!IMPORTANT]
> Offboard, cihazın algılayıcı verilerini portala göndermeyi durdurmaya neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere cihazdan alınan veriler 6 ay süreyle korunur.


## <a name="monitor-device-configuration"></a>Cihaz yapılandırmasını izleme

Geçerli dalı kullanıyorsanız, Configuration Manager Microsoft Endpoint Configuration Manager uç nokta için yerleşik Microsoft Defender panosunun kullanın. Daha fazla bilgi için bkz [. Microsoft Defender Gelişmiş Tehdit Koruması - Monitör](/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection#monitor).

System Center 2012 R2 Configuration Manager kullanıyorsanız izleme iki bölümden oluşur:

1. Yapılandırma paketinin doğru dağıtıldığından ve ağ ağınız kapsamındaki cihazlarda çalıştırıldığından (veya başarıyla çalıştırıldığından) emin olun.

2. Cihazların Microsoft 365 cihaz ekleme hizmetiyle uyumlu olup değildir (bu, cihazın ekleme işlemini tamamlayasını sağlar ve verileri hizmete bildirmeye devam eder).

### <a name="confirm-the-configuration-package-has-been-correctly-deployed"></a>Yapılandırma paketinin doğru dağıtıldığından emin olun

1. Yapılandırma Yöneticisi konsolunda, gezinti **bölmesinin** en altındaki İzleme'ye tıklayın.

2. Genel **Bakış'ı** ve ardından **Dağıtımlar'ı seçin**.

3. Paket adını içeren dağıtımı seçin.

4. Tamamlama İstatistikleri ve İçerik Durumu **altında durum göstergelerini** **gözden geçirebilirsiniz**.

    Başarısız dağıtımlar (Hata olan **cihazlar, Gereksinimleri** Karşılamıyor veya Başarısız durumları) **varsa, cihaz** sorunlarını gidermeniz gerekir. Daha fazla bilgi için bkz. [Microsoft Defender Gelişmiş Tehdit Koruması ekleme sorunlarını giderme](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding).

    ![Hatasız başarılı bir dağıtım gösteren Configuration Manager.](../media/sccm-deployment.png)

### <a name="check-that-the-devices-are-compliant-with-the-microsoft-365-endpoint-data-loss-prevention-service"></a>Cihazların Microsoft 365 Uç nokta veri kaybı önleme hizmetiyle uyumlu olup değildir

System Center 2012 R2 Configuration Manager'da dağıtımınızı izlemek için yapılandırma öğesi için bir uyumluluk kuralı kurabilirsiniz.

> [!NOTE]
> Bu yordam ve kayıt defteri girdisi, Uç Nokta için Defender'ın yanı sıra Uç Nokta DLP için de geçerlidir.

Bu kural, *hedefli cihazlarda kayıt* defteri anahtarının değerini izleyen, düzeltilmeyen bir uyumluluk kuralı yapılandırma öğesidir.

Aşağıdaki kayıt defteri anahtarı girdisini izleme:
```
Path: “HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status”
Name: “OnboardingState”
Value: “1”
```
Daha fazla bilgi için bkz[. 2012 R2 Configuration Manager'da System Center ayarlarına giriş](/previous-versions/system-center/system-center-2012-R2/gg682139(v=technet.10)).

## <a name="related-topics"></a>İlgili konular
- [Grup Windows 10 kullanarak Windows 11 cihazı ekleme ve kullanma](device-onboarding-gp.md)
- [Mobil Windows 10 araçları Windows 11 cihaza ekleme ve kullanma](device-onboarding-mdm.md)
- [Yerel bir Windows 10 kullanarak Windows 10 ve 11 Windows cihaz kullanın](device-onboarding-script.md)
- [Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarını ekleme](device-onboarding-vdi.md)
- [Yeni eklenen Uç nokta cihazı için Microsoft Defender'da bir algılama testi çalıştırma](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Microsoft Defender Gelişmiş Tehdit Koruması'nın ekleme sorunlarını giderme](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)