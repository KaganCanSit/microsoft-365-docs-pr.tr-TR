---
title: Windows Güvenliği uygulamasında Microsoft Defender Virüsten Koruma
description: Windows Güvenliği uygulamasına Microsoft Defender Virüsten Koruma eklendiğinde, sık kullanılan görevleri gözden geçirebilir, karşılaştırabilir ve gerçekleştirebilirsiniz.
keywords: wdav, virüsten koruma, güvenlik duvarı, güvenlik, windows
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: bd045ac36f1685c3bf12cedf04dd074ed6c7fc5e
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873996"
---
# <a name="microsoft-defender-antivirus-in-the-windows-security-app"></a>Windows Güvenliği uygulamasında Microsoft Defender Virüsten Koruma

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Windows 10, sürüm 1703 ve sonraki sürümlerde, Windows Defender uygulaması Windows Güvenliği bir parçasıdır.

Daha önce Windows Defender istemcisi ve ana Windows Ayarlar parçası olan Ayarlar birleştirildi ve Windows 10 sürüm 1703'ün bir parçası olarak varsayılan olarak yüklenen yeni uygulamaya taşındı.

> [!IMPORTANT]
> Windows Güvenliği uygulama hizmetini devre dışı bırakmak Microsoft Defender Virüsten Koruma veya [Windows Defender Güvenlik Duvarı](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security) devre dışı bırakmaz. Bir üçüncü taraf virüsten koruma veya güvenlik duvarı ürünü yüklendiğinde ve güncel tutulduğunda bunlar otomatik olarak devre dışı bırakılır.
> Windows Güvenliği uygulama hizmetini devre dışı bırakırsanız veya grup ilkesi ayarlarını yapılandırarak başlatılmasını veya çalışmasını engellerseniz, Windows Güvenliği uygulaması cihaza yüklediğiniz virüsten koruma veya güvenlik duvarı ürünleri hakkında eski veya yanlış bilgiler görüntüleyebilir.
> Ayrıca, eski veya güncel olmayan bir üçüncü taraf virüsten koruma yazılımınız varsa veya daha önce yüklemiş olabileceğiniz üçüncü taraf virüsten koruma ürünlerini kaldırırsanız Microsoft Defender Virüsten Koruma'ın kendisini etkinleştirmesini engelleyebilir.
> Bu, cihazınızın korumasını önemli ölçüde düşürür ve kötü amaçlı yazılım bulaşmasına yol açabilir.

Uygulamada izleyebileceğiniz diğer Windows güvenlik özellikleri hakkında daha fazla bilgi için Windows Güvenliği [makalesine](/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) bakın.

Windows Güvenliği uygulaması, Windows 10, sürüm 1703 ve sonraki sürümlerde bir istemci arabirimidir. Uç Nokta için Microsoft Defender gözden geçirmek ve yönetmek için kullanılan [Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint) web portalı değildir.

## <a name="review-virus-and-threat-protection-settings-in-the-windows-security-app"></a>Windows Güvenliği uygulamasında virüs ve tehdit koruması ayarlarını gözden geçirme

:::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Windows Güvenliği uygulamasında virüs ve tehdit koruması ayarları" lightbox="../../media/wdav-protection-settings-wdsc.png":::

1. Görev çubuğundaki kalkan simgesine tıklayarak veya başlangıç menüsünde **Windows Güvenliği arayarak Windows Güvenliği** uygulamasını açın.

2. **Virüs & tehdit koruması** kutucuğunu (veya sol menü çubuğundaki kalkan simgesini) seçin.

Aşağıdaki bölümlerde, Windows Güvenliği uygulamasındaki Microsoft Defender Virüsten Koruma tarafından sağlanan tehdit korumasını gözden geçirirken veya bunlarla etkileşim kurarken en yaygın görevlerden bazılarının nasıl gerçekleştirildiği açıklanır.

> [!NOTE]
> Bu ayarlar grup ilkesi kullanılarak yapılandırılır ve dağıtılırsa, bu bölümde açıklanan ayarlar gri görünür ve tek tek uç noktalarda kullanılamaz. grup ilkesi Nesnesi aracılığıyla yapılan değişikliklerin, ayarın Windows Ayarlar güncelleştirilmeden önce tek tek uç noktalara dağıtılması gerekir. [Microsoft Defender Virüsten Koruma ile son kullanıcı etkileşimini yapılandırma](configure-end-user-interaction-microsoft-defender-antivirus.md) konusu, yerel ilke geçersiz kılma ayarlarının nasıl yapılandırılabildiğini açıklar.

## <a name="run-a-scan-with-the-windows-security-app"></a>Windows Güvenliği uygulamasıyla tarama çalıştırma

1. Başlangıç menüsünde **Güvenlik'i** arayarak ve ardından **Windows Güvenliği'ı** seçerek Windows Güvenliği uygulamasını açın.

2. **Virüs & tehdit koruması** kutucuğunu (veya sol menü çubuğundaki kalkan simgesini) seçin.

3. **Hızlı tarama'ya** tıklayın. Tam tarama çalıştırmak için **Tarama seçenekleri'ni** ve ardından **Tam tarama** gibi bir seçenek belirleyin.

## <a name="review-the-security-intelligence-update-version-and-download-the-latest-updates-in-the-windows-security-app"></a>Güvenlik bilgileri güncelleştirme sürümünü gözden geçirin ve Windows Güvenliği uygulamasındaki en son güncelleştirmeleri indirin

:::image type="content" source="../../media/wdav-wdsc-defs.png" alt-text="Güvenlik bilgileri sürüm numarası" lightbox="../../media/wdav-wdsc-defs.png":::

1. Başlangıç menüsünde *Güvenlik'i* arayarak ve ardından **Windows Güvenliği'ı** seçerek Windows Güvenliği uygulamasını açın.

2. **Virüs & tehdit koruması** kutucuğunu (veya sol menü çubuğundaki kalkan simgesini) seçin.

3. **Virüs & tehdit koruması güncelleştirmelerini** seçin. Şu anda yüklü olan sürüm, ne zaman indirildiği hakkında bazı bilgilerle birlikte görüntülenir. Geçerli sürümü el ile indirilebilen en son sürümle karşılaştırabilir veya bu sürüm için değişiklik günlüğünü gözden geçirebilirsiniz. Bkz[. Microsoft Defender Virüsten Koruma ve diğer Microsoft kötü amaçlı yazılımdan koruma yazılımları için güvenlik bilgileri güncelleştirmeleri](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus).

4. Yeni koruma **güncelleştirmelerini indirmek için Güncelleştirmeleri denetle'yi** seçin (varsa).

## <a name="ensure-microsoft-defender-antivirus-is-enabled-in-the-windows-security-app"></a>Windows Güvenliği uygulamasında Microsoft Defender Virüsten Koruma etkinleştirildiğinden emin olun

1. Başlangıç menüsünde *Güvenlik'i* arayarak ve ardından **Windows Güvenliği'ı** seçerek Windows Güvenliği uygulamasını açın.

2. **Virüs & tehdit koruması** kutucuğunu (veya sol menü çubuğundaki kalkan simgesini) seçin.

3. **Virüs & tehdit koruması ayarlarını** seçin.

4. **Gerçek zamanlı koruma** anahtarını **Açık** olarak değiştirin.

    > [!NOTE]
    > **Gerçek zamanlı korumayı** kapatırsanız, kısa bir gecikmeden sonra otomatik olarak yeniden açılır. Bu, kötü amaçlı yazılımlardan ve tehditlerden korunduğunuzdan emin olmaktır.
    > Başka bir virüsten koruma ürünü yüklerseniz Microsoft Defender Virüsten Koruma otomatik olarak kendini devre dışı bırakır ve Windows Güvenliği uygulamasında olduğu gibi gösterilir. [Sınırlı düzenli taramayı](limited-periodic-scanning-microsoft-defender-antivirus.md) etkinleştirmenizi sağlayacak bir ayar görüntülenir.

## <a name="add-exclusions-for-microsoft-defender-antivirus-in-the-windows-security-app"></a>Windows Güvenliği uygulamasında Microsoft Defender Virüsten Koruma için dışlamalar ekleme

1. Başlangıç menüsünde *Güvenlik'i* arayarak ve ardından **Windows Güvenliği'ı** seçerek Windows Güvenliği uygulamasını açın.

2. **Virüs & tehdit koruması** kutucuğunu (veya sol menü çubuğundaki kalkan simgesini) seçin.

3. **Virüs & tehdit koruması ayarları'nın** altında **Ayarları yönet'i** seçin.

4. **Dışlamalar'ın** altında **Dışlama ekle veya kaldır'ı** seçin.

5. Türü seçmek ve her dışlama için seçenekleri ayarlamak için artı simgesini (**+**) seçin.

Aşağıdaki tabloda dışlama türleri ve ne olacağı özetlenmiştir:

|Dışlama türü|Tanımlandığı yer|Neler olur?|
|---|---|---|
|**Dosya**|Konum <br/>Örnek: `c:\sample\sample.test`|Belirli bir dosya Microsoft Defender Virüsten Koruma tarafından atlanır.|
|**Klasör**|Konum <br/>Örnek: `c:\test\sample`|Belirtilen klasördeki tüm öğeler Microsoft Defender Virüsten Koruma tarafından atlanır.|
|**Dosya türü**|Dosya uzantısı <br/>Örnek: `.test`|Cihazınızda herhangi bir yerde uzantıya `.test` sahip tüm dosyalar Microsoft Defender Virüsten Koruma tarafından atlanır.|
|**Işlem**|Yürütülebilir dosya yolu <br>Örnek: `c:\test\process.exe`|Belirli işlem ve bu işlem tarafından açılan tüm dosyalar Microsoft Defender Virüsten Koruma tarafından atlanır.|

Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Dosya uzantısına ve klasör konumuna göre dışlamaları yapılandırma ve doğrulama](./configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [İşlemler tarafından açılan dosyalar için dışlamaları yapılandırma](./configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="review-threat-detection-history-in-the-windows-defender-for-cloud-app"></a>Bulut uygulaması için Windows Defender tehdit algılama geçmişini gözden geçirin

1. Başlangıç menüsünde *Güvenlik'i* arayarak ve ardından **Windows Güvenliği'ı** seçerek Windows Güvenliği uygulamasını açın.

2. **Virüs & tehdit koruması** kutucuğunu (veya sol menü çubuğundaki kalkan simgesini) seçin.

3. **Koruma geçmişi'ne tıklayın**. Son kullanılan öğeler listelenir.

## <a name="set-ransomware-protection-and-recovery-options"></a>Fidye yazılımı koruma ve kurtarma seçeneklerini ayarlama

1. Başlangıç menüsünde *Güvenlik'i* arayarak ve ardından **Windows Güvenliği'ı** seçerek Windows Güvenliği uygulamasını açın.

2. **Virüs & tehdit koruması** kutucuğunu (veya sol menü çubuğundaki kalkan simgesini) seçin.

3. **Fidye yazılımı koruması'nın** altında **Fidye yazılımı korumasını yönet'i** seçin.

4. **Denetimli klasör erişimi** ayarlarını değiştirmek için bkz. [Denetimli klasör erişimi ile önemli klasörleri koruma](/microsoft-365/security/defender-endpoint/controlled-folders).

5. Fidye yazılımı kurtarma seçeneklerini ayarlamak için **Fidye yazılımı veri kurtarma** altında **Ayarla'yı** seçin ve fidye yazılımı saldırısından kolayca kurtarabilmek için OneDrive hesabınızı bağlama veya ayarlama yönergelerini izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
