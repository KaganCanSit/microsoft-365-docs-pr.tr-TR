---
title: Microsoft Defender Virüsten Koruma Windows Güvenliği seçin
description: Artık Microsoft Defender Virüsten Koruma uygulamana dahil olan Windows Güvenliği, sık kullanılan görevleri gözden geçirebilir, karşılaştırebilir ve gerçekleştirebilirsiniz.
keywords: wdav, virüsten koruma, güvenlik duvarı, güvenlik, pencereler
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
ms.openlocfilehash: 1c5177946ff3d54ab64c78e9013a8e0c07b0fd11
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468137"
---
# <a name="microsoft-defender-antivirus-in-the-windows-security-app"></a>Microsoft Defender Virüsten Koruma Windows Güvenliği seçin

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Sürüm Windows 10 1703 ve sonraki sürümlerde, Windows Defender uygulaması diğer Windows Güvenliği.

Ayarlar Windows Defender istemcisinin ve ana Windows Ayarlar parçası olan tüm sürümler birleştirildi ve Windows 10 sürüm 1703'in parçası olarak varsayılan olarak yüklenmiş olan yeni uygulamaya taşındı.

> [!IMPORTANT]
> Uygulama hizmeti devre Windows Güvenliği devre dışı bırak, Güvenlik Duvarı'Microsoft Defender Virüsten Koruma [Windows Defender devre dışı bırakmaz](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). Üçüncü taraf virüsten koruma yazılımı veya güvenlik duvarı ürünü yük olduğunda bunlar otomatik olarak devre dışı bırakılır ve güncel tutulur.
>
> Windows Güvenliği uygulama hizmetini devre dışı bırakır veya uygulamayı başlatmasını veya çalıştırmasını önlemek üzere ilişkili grup ilkesi ayarlarını yapılandırdısanız, Windows Güvenliği uygulaması cihaza yüklemiş olabileceğiniz virüsten koruma yazılımı veya güvenlik duvarı ürünleri hakkında eski veya yanlış bilgiler lişkilendirilmiş olabilir.
> Ayrıca, eski Microsoft Defender Virüsten Koruma veya güncel olmayan bir üçüncü taraf virüsten koruma yazılımınız varsa veya daha önce yüklemiş olabileceğiniz üçüncü taraf virüsten koruma ürünlerini kaldırırsanız, bu özelliğin kendi kendine etkinleştirilmesini de engellenebilir.
> Bu, cihazınızın korumasını önemli ölçüde azaltır ve kötü amaçlı yazılım bulaşmaya yol açabilir.

Uygulamada [Windows Güvenliği diğer](/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) güvenlik özellikleri Windows daha fazla bilgi için bu makaleye bakın.

Uygulama Windows Güvenliği sürüm 1703 ve Windows 10 üzerinde bir istemci arabirimidir. Bu, posta Microsoft 365 Defender yönetmek ve gözden geçirmek için kullanılan bir web [Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint).

## <a name="review-virus-and-threat-protection-settings-in-the-windows-security-app"></a>Windows Güvenliği uygulamasında virüs ve tehdit koruması ayarlarını gözden geçirme

:::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Windows Güvenliği uygulamasında virüs ve tehdit koruması ayarları" lightbox="../../media/wdav-protection-settings-wdsc.png":::

1. Görev Windows Güvenliği kalkan simgesine tıklayarak veya görev çubuğu için başlangıç menüsünde arama **Windows Güvenliği.**

2. Virüs koruması **& kutucuğunu** (veya sol menü çubuğundaki kalkan simgesini) seçin.

Aşağıdaki bölümlerde, Microsoft Defender Virüsten Koruma uygulamasındaki Microsoft Defender Virüsten Koruma tarafından sağlanan tehdit korumasını gözden geçirme veya bu tehdit korumasıyla etkileşim kurmada en Windows Güvenliği açıklanmaktadır.

> [!NOTE]
> Bu ayarlar tek tek uç noktalar kullanılarak grup ilkesi yapılandırılmış ve dağıtılmışsa, bu bölümde açıklanan ayarlar gri olur ve uç noktaların tek tek kullanımı için kullanılamaz. Nesnede yapılan grup ilkesi, ayar Tek tek güncelleştirilmeden önce nesnenin tek tek uç noktalara dağıtılması Windows Ayarlar. Kullanıcı [profiliyle son kullanıcı etkileşimi Microsoft Defender Virüsten Koruma](configure-end-user-interaction-microsoft-defender-antivirus.md) konuda, yerel ilke geçersiz kılma ayarlarının nasıl yapılandırıl olduğu açıklanmıştır.

## <a name="run-a-scan-with-the-windows-security-app"></a>Windows Güvenliği uygulamasıyla tarama çalıştırma

1. Başlat Windows Güvenliği Güvenlik'i arayarak ve sonra **Güvenlik'i** seçerek **Windows Güvenliği.**

2. Virüs koruması **& kutucuğunu** (veya sol menü çubuğundaki kalkan simgesini) seçin.

3. Hızlı **tarama'ya seçin**. Tam taramayı çalıştırmak için Tarama **seçenekleri'ne ve** sonra Tam tarama gibi bir **seçenek belirleyin**.

## <a name="review-the-security-intelligence-update-version-and-download-the-latest-updates-in-the-windows-security-app"></a>Windows Güvenliği uygulamasında güvenlik zekası güncelleştirme sürümünü gözden geçirme ve en son Windows Güvenliği indirme

:::image type="content" source="../../media/wdav-wdsc-defs.png" alt-text="Güvenlik zekası sürüm numarası" lightbox="../../media/wdav-wdsc-defs.png":::

1. Başlat Windows Güvenliği Güvenlik'i arayarak ve sonra *Güvenlik'i* seçerek **Windows Güvenliği.**

2. Virüs koruması **& kutucuğunu** (veya sol menü çubuğundaki kalkan simgesini) seçin.

3. Virüs ve **tehdit &'i seçin**. Şu anda yüklü olan sürüm, indirildikten sonra bazı bilgilerle birlikte görüntülenir. Geçerli sürümü el ile indirilebilir en son sürüme göre kontrol edin veya bu sürümün değişiklik günlüğünü gözden geçirin. Güvenlik [zekası güncelleştirmeleri ve Microsoft Defender Virüsten Koruma Microsoft kötü amaçlı yazılımlardan koruma makalelerine bakın](https://www.microsoft.com/wdsi/defenderupdates).

4. Yeni **koruma güncelleştirmelerini (varsa** ) indirmek için Güncelleştirmeleri kontrol edin'i seçin.

## <a name="ensure-microsoft-defender-antivirus-is-enabled-in-the-windows-security-app"></a>Microsoft Defender Virüsten Koruma Windows Güvenliği uygulamasında mobil Windows Güvenliği emin olun

1. Başlat Windows Güvenliği Güvenlik'i arayarak ve sonra *Güvenlik'i* seçerek **Windows Güvenliği.**

2. Virüs koruması **& kutucuğunu** (veya sol menü çubuğundaki kalkan simgesini) seçin.

3. Virüs **ve tehdit & ayarlarını seçin**.

4. Gerçek zamanlı **koruma anahtarını Açık** olarak **değiştirme**.

    > [!NOTE]
    > Gerçek zamanlı **korumayı kapatsanız** , kısa bir gecikmeden sonra otomatik olarak yeniden açılır. Bunun amacı kötü amaçlı yazılımlara ve tehditlere karşı korunmaktır.
    > Başka bir virüsten koruma ürünü Microsoft Defender Virüsten Koruma, otomatik olarak kendisini devre dışı bırakacaktır ve Windows Güvenliği gerekir. Sınırlı düzenli taramayı etkinleştirmeniz için bir [ayar görüntülenir](limited-periodic-scanning-microsoft-defender-antivirus.md).

## <a name="add-exclusions-for-microsoft-defender-antivirus-in-the-windows-security-app"></a>Windows Güvenliği uygulamasında Microsoft Defender Virüsten Koruma için dışlamalar ekleme

1. Başlat Windows Güvenliği Güvenlik'i arayarak ve sonra *Güvenlik'i* seçerek **Windows Güvenliği.**

2. Virüs koruması **& kutucuğunu** (veya sol menü çubuğundaki kalkan simgesini) seçin.

3. Virüs **koruması & ayarları'nın altında** Ayarları **yönet'i seçin**.

4. **Dışlamalar'ın** altında **Dışlama ekle veya kaldır'ı seçin**.

5. Türü seçmek ve her dışlama için seçenekleri ayarlamak için artı simgesini (**+**) seçin.

Aşağıdaki tabloda dışlama türleri ve neler olduğu özetlenmiştir:

<br>

****
|Dışlama türü|Tanımlandığı yer|Ne olur?|
|---|---|---|
|**Dosya**|Konum <br/>Örnek: `c:\sample\sample.test`|Belirli dosya Dosya Atla tarafından Microsoft Defender Virüsten Koruma.|
|**Klasör**|Konum <br/>Örnek: `c:\test\sample`|Belirtilen klasördeki tüm öğeler, Posta'ya Microsoft Defender Virüsten Koruma.|
|**Dosya türü**|Dosya uzantısı <br/>Örnek: `.test`|Uzantıya sahip tüm `.test` dosyalar, cihazınızın herhangi bir yerindeki her yerden Microsoft Defender Virüsten Koruma.|
|**İşlem**|Yürütülebilir dosya yolu <br>Örnek: `c:\test\process.exe`|Belirli işlem ve bu işlem tarafından açılan tüm dosyalar dosya tarafından Microsoft Defender Virüsten Koruma.|
|

Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Dosya uzantısını ve klasör konumunu temel alarak dışlamaları yapılandırma ve doğrulama](./configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [İşlemler tarafından açılan dosyalar için dışlamaları yapılandırma](./configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="review-threat-detection-history-in-the-windows-defender-for-cloud-app"></a>Bulut uygulaması için Windows Defender'de tehdit algılama geçmişini gözden geçirme

1. Başlat Windows Güvenliği Güvenlik'i arayarak ve sonra *Güvenlik'i* seçerek **Windows Güvenliği.**

2. Virüs koruması **& kutucuğunu** (veya sol menü çubuğundaki kalkan simgesini) seçin.

3. Koruma **geçmişi'ne seçin**. Son öğeler listelenir.

## <a name="set-ransomware-protection-and-recovery-options"></a>Fidye yazılımı koruması ve kurtarma seçeneklerini ayarlama

1. Başlat Windows Güvenliği Güvenlik'i arayarak ve sonra *Güvenlik'i* seçerek **Windows Güvenliği.**

2. Virüs koruması **& kutucuğunu** (veya sol menü çubuğundaki kalkan simgesini) seçin.

3. Fidye **yazılımı koruması'nın** altında Fidye yazılımı **korumasını yönet'i seçin**.

4. Denetimli **klasör erişimi ayarlarını değiştirmek** için bkz [. Denetimli klasör erişimiyle önemli klasörleri koruma](/microsoft-365/security/defender-endpoint/controlled-folders).

5. Fidye yazılımı kurtarma seçeneklerini ayarlamak için Fidye yazılımı  verisi kurtarma  altında Ayarla'ya tıklayın ve fidye yazılımı saldırılarından kolayca kurtarmak için OneDrive hesabınıza bağlantı kurma veya bu hesabı ayarlama yönergelerini izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
