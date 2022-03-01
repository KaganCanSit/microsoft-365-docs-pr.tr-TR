---
title: Uç nokta için Microsoft Defender'a gereken en düşük gereksinimler
description: Hizmete cihaz eklemeye için lisans gereksinimlerini ve gereksinimlerini anlama
keywords: minimum gereksinimler, lisanslama, karşılaştırma tablosu
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
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 6d4d76a45d69994c82c2027f57d5c3b045e82397
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011796"
---
# <a name="minimum-requirements-for-microsoft-defender-for-endpoint"></a>Uç nokta için Microsoft Defender'a gereken en düşük gereksinimler

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-minreqs-abovefoldlink)

Hizmete cihaz ekleme için bazı minimum gereksinimler vardır. Hizmete cihazları eklemeye lisans, donanım ve yazılım gereksinimleri ve diğer yapılandırma ayarları hakkında bilgi edinebilirsiniz.

> [!TIP]
>
> - Bu makalede, Uç Nokta Planı 2 için Microsoft Defender'a gereken en düşük gereksinimler açıklanmıştır. Uç Nokta Planı 1 için Defender hakkında bilgi arıyorsanız bkz. [Uç Nokta Planı 1 için Defender gereksinimleri](mde-p1-setup-configuration.md#review-the-requirements).
> - Uç Nokta için Defender: Uç Nokta için Defender Teknik [Sürüm'de yapılan en son iyileştirmeler hakkında Community](https://techcommunity.microsoft.com/t5/Windows-Defender-Advanced-Threat/ct-p/WindowsDefenderAdvanced).
> - Uç Nokta için Defender, son MITRE değerlendirmesinde endüstri lideri optikleri ve algılama özelliklerini gösteriyor. Okuma: [Analizler CK tabanlı değerlendirmede MITRE ATT&okuma](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

## <a name="licensing-requirements"></a>Lisans gereksinimleri
Uç nokta için Microsoft Defender lisans gereksinimleri hakkında bilgi için bkz. Uç nokta [lisans bilgileri için Microsoft Defender](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-defender-for-endpoint).


Ayrıntılı lisans bilgileri için, Ürün Koşulları [sitesine bakın ve](https://www.microsoft.com/licensing/terms/) hüküm ve koşullar hakkında daha fazla bilgi edinmek için hesap ekibimizle birlikte çalışma.

Windows sürümlerindeki özellikler dizisi hakkında daha fazla bilgi için bkz. [Windows karşılaştırma](https://www.microsoft.com/windowsforbusiness/compare).

## <a name="browser-requirements"></a>Tarayıcı gereksinimleri

Uç Nokta için Defender'a Erişim, aşağıdaki tarayıcıları desteklemeye devam eden bir tarayıcı aracılığıyla yapılır:

- Microsoft Edge
- Google Chrome

> [!NOTE]
> Diğer tarayıcılar da çalışsa da desteklenenler, sözü geçen tarayıcılardır.

## <a name="hardware-and-software-requirements"></a>Donanım ve yazılım gereksinimleri

### <a name="supported-windows-versions"></a>Desteklenen Windows sürümleri

- Windows 7 SP1 Enterprise ([Destek için ESU gerektirir](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq).)
- Windows 7 SP1 Pro ([Destek için ESU gerektirir](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq).)
- Windows 8.1 Enterprise
- Windows 8.1 Pro
- Windows 11 Enterprise
- Windows 11 Education
- Windows 11 Pro
- Windows 11 Pro Education
- Windows 10 Enterprise
- [Windows 10 Enterprise LTSC 2016 (veya sonrası)](/windows/whats-new/ltsc/)
- Windows 10 Education
- Windows 10 Pro
- Windows 10 Pro Education
- Windows sunucusu
  - Windows Server 2008 R2 SP1 ([Destek için ESU gerekir](/windows-server/get-started/extended-security-updates-deploy))
  - Windows Server 2012 R2
  - Windows Server 2016
  - Windows Server, sürüm 1803 veya sonrası
  - Windows Server 2019
  - Windows Server 2022
- Windows Masaüstü

Ağ cihazlarınız bu sürümlerden birini çalıştırıyor olmalıdır.

Cihazlar için Uç Nokta için Defender donanım gereksinimleri desteklenen sürümlerde aynıdır.

> Çekirdekler: En az 2, 4 tercih edilen Bellek: En az 1 GB, 4 tercih edilen Bellek

Bu güncelleştirmelerin desteklenen sürümleri hakkında daha fazla Windows 10 için bkz. (/windows/release-health/release-information).

> [!NOTE]
> Makine sürümlerini (Windows gibi Windows CE Windows 10 Mobile makinelerini) desteklemez.
>
> Microsoft dışı sanallaştırma Windows 10 Enterprise 2016 LTSB kullanan Sanal Makineler, performans sorunlarıyla karşılaşabilirsiniz.
>
> Sanal ortamlar için, LTSC 2019 veya Windows 10 Enterprise bir sonraki ortamlar kullanılması önerilir.

Microsoft Windows işletim sistemlerinde bileşenler güncel olduğunda, Uç nokta desteği için Microsoft Defender ilgili işletim sisteminin yaşam döngüsüne uygun olur. Daha fazla bilgi için bkz. Yaşam Döngüsü [SSS](/lifecycle/faq/general-lifecycle). Yeni özellikler veya özellikler genellikle yalnızca yaşam döngüsünün sonuna ulaşmamış olan işletim sistemleri üzerinde sağlanır. Güvenlik zekası güncelleştirmeleri (tanım ve altyapı güncelleştirmeleri) ve algılama mantığı en azından şunları yapmaya kadar sağlanacaktır:

- Destek [tarihi sonu (](/lifecycle/products/) Genişletilmiş Güvenlik Güncelleştirmeleri (ESU) programı olan işletim sistemleri için).
- [ESU tarihi sonu](/lifecycle/faq/extended-security-updates) (ESU programı olan işletim sistemleri için).



### <a name="other-supported-operating-systems"></a>Desteklenen diğer işletim sistemleri

- [Android](microsoft-defender-endpoint-android.md)
- [iOS](microsoft-defender-endpoint-ios.md)
- [Linux](microsoft-defender-endpoint-linux.md)
- [macOS](microsoft-defender-endpoint-mac.md)

> [!NOTE]
> Tümleştirmenin çalışması için Linux dağıtımlarının ve Android, iOS ve macOS sürümlerinin Uç Nokta için Defender ile uyumlu olduğunu onaylamanız gerekir.

### <a name="network-and-data-storage-and-configuration-requirements"></a>Ağ ve veri depolama ve yapılandırma gereksinimleri

Ekleme sihirbazını ilk kez çalıştıracakken, Uç nokta ile ilgili bilgiler için Microsoft Defender'ın nerede depolanmış olduğunu seçmeniz gerekir: Avrupa Birliği' nde, Birleşik Krallık'ta veya ABD veri merkezinde.

> [!NOTE]
>
> - İlk kurulumdan sonra veri depolama konumlarınızı değiştiremezsiniz.
> - Microsoft'un [verilerinizi nerede ve nasıl depola ilgili daha fazla](data-storage-privacy.md) bilgi için Uç nokta veri depolaması ve gizliliği için Microsoft Defender'ı gözden geçirebilirsiniz.

### <a name="diagnostic-data-settings"></a>Tanılama veri ayarları

> [!NOTE]
> Uç Nokta için Microsoft Defender etkin olduğu sürece belirli bir tanılama düzeyi gerektirmez.

Tanılama veri hizmetinin, kuruma bağlı tüm cihazlarda etkinleştirildiğinden emin olun.
Varsayılan olarak, bu hizmet etkindir. Bu verilerden algılayıcı verileri edin tam olarak emin olmak için kontrol etmek iyi bir yöntemdir.

#### <a name="use-the-command-line-to-check-the-windows-diagnostic-data-service-startup-type"></a>Tanılama veri hizmeti başlangıç türünü Windows için komut çizgilerini kullanın

1. Cihazda yükseltilmiş komut satırı istemini açın:
   1. **Başlat'a gidin** ve **cmd yazın**.
   2. Komut istemi'ne **sağ tıklayın ve** Yönetici olarak **çalıştır'ı seçin**.

2. Aşağıdaki komutu girin ve Enter tuşuna **basın**:

   ```console
   sc qc diagtrack
   ```

   Hizmet etkinleştirilmişse, sonuç aşağıdaki ekran görüntüsüne benzer olmalıdır:

   ![diagtrack için sc query komutunun sonucu.](images/windefatp-sc-qc-diagtrack.png)

Varsayılan ayar Otomatik Olarak Başlat'a ayar değil **START_TYPE hizmeti otomatik** olarak başlat olacak şekilde **AUTO_START**.

#### <a name="use-the-command-line-to-set-the-windows-diagnostic-data-service-to-automatically-start"></a>Varsayılan tanılama veri hizmetini otomatik olarak Windows için komut çizgilerini kullanın

1. Uç noktada yükseltilmiş bir komut satırı istemi açın:
    1. **Başlat'a gidin** ve **cmd yazın**.
    2. Komut istemi'ne **sağ tıklayın ve** Yönetici olarak **çalıştır'ı seçin**.

2. Aşağıdaki komutu girin ve Enter tuşuna **basın**:

    ```console
    sc config diagtrack start=auto
    ```

3. Bir başarı iletisi görüntülenir. Aşağıdaki komutu girerek değişikliği doğrulayın ve Enter tuşuna **basın**:

    ```console
    sc qc diagtrack
    ```

#### <a name="internet-connectivity"></a>İnternet bağlantısı

Cihazlarda İnternet bağlantısı doğrudan veya proxy aracılığıyla gereklidir.

Uç nokta algılayıcısı için Defender, Uç nokta bulut hizmeti için Defender ile iletişim kurmak ve siber verileri rapor etmek için günlük ortalama 5 MB bant genişliği kullanabilir. Dosya yüklemeleri ve araştırma paketi koleksiyonu gibi bir off etkinlikleri, bu günlük ortalama bant genişliğine dahil değildir.

Ek ara sunucu yapılandırma ayarları hakkında daha fazla bilgi için bkz. [Cihaz ara sunucusunu ve İnternet bağlantı ayarlarını yapılandırma](configure-proxy-internet.md).

Cihazları eklemeden önce tanılama veri hizmetinin etkinleştirilmesi gerekir. Windows 10 11'de Windows etkinleştirilir.

## <a name="microsoft-defender-antivirus-configuration-requirement"></a>Microsoft Defender Virüsten Koruma gereksinimini karşıla

Uç nokta aracısı için Defender, dosyaların Microsoft Defender Virüsten Koruma ve hakkında bilgi sağlayabilme özelliğine bağlıdır.

Etkin kötü amaçlı yazılımdan koruma olsa da, Uç nokta cihazları Microsoft Defender Virüsten Koruma için Defender'da Güvenlik zekası güncelleştirmelerini yapılandırabilirsiniz. Daha fazla bilgi için bkz[. Güncelleştirmeleri Microsoft Defender Virüsten Koruma ve taban çizgilerini uygulama](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus).

Bu Microsoft Defender Virüsten Koruma etkin kötü amaçlı yazılımlardan koruma değildir ve Uç Nokta için Defender hizmetini kullanırsınız, Microsoft Defender Virüsten Koruma pasif moduna geçer.

If your organization has turned off Microsoft Defender Virüsten Koruma through group policy or other methods, devices that are onboarded are excluded from this group policy.

Sunucularınızı işe alıyorsanız ve Microsoft Defender Virüsten Koruma sunucularınız etkin kötü amaçlı yazılımlardan koruma değilse, Microsoft Defender Virüsten Koruma'in pasif moduna gidecek veya kaldıracak şekilde yapılandırılması gerekir. Yapılandırma sunucu sürümüne bağlıdır. Daha fazla bilgi için uyumluluk [Microsoft Defender Virüsten Koruma bakın](microsoft-defender-antivirus-compatibility.md).

> [!NOTE]
> Normal grup ilkeniz Tamper Protection için geçerli değildir ve Değişiklik Koruması açık Microsoft Defender Virüsten Koruma değişiklikler yoksayılır.

## <a name="microsoft-defender-antivirus-early-launch-antimalware-elam-driver-is-enabled"></a>Microsoft Defender Virüsten Koruma Başlatma Kötü Amaçlı Yazılımdan Koruma (ELAM) sürücüsü etkinleştirildi

Cihazlarınız arasında birincil Microsoft Defender Virüsten Koruma koruma ürünü olarak çalıştıracaksanız Uç nokta için Defender aracısı başarılı bir şekilde kullanılır.

Üçüncü taraf bir kötü amaçlı yazılımdan koruma istemcisi kullanıyorsanız ve Mobil Cihaz Yönetimi çözümleri veya Microsoft Endpoint Manager (geçerli dalı) kullanıyorsanız, ELAM sürücüsünün Microsoft Defender Virüsten Koruma emin olun. Daha fazla bilgi için bkz[. İlke tarafından Microsoft Defender Virüsten Koruma devre dışı bırakıldıktan emin olmak.](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)

## <a name="related-topics"></a>İlgili konular

- [Uç nokta dağıtımı için Microsoft Defender'ı ayarlama](production-deployment.md)
- [Cihazları ekleme](onboard-configure.md)
