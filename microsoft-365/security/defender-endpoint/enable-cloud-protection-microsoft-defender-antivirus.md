---
title: Bulutta bulut korumasını Microsoft Defender Virüsten Koruma
description: Hızlı ve gelişmiş koruma özelliklerinden yararlanmak için bulut korumasını açabilirsiniz.
keywords: Microsoft Defender Virüsten Koruma, kötü amaçlı yazılımlardan koruma, güvenlik, bulut, ilk görüşte engelle
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.date: 02/03/2022
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 95abb603983ea16192d93b12757cde6fba026047
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63016452"
---
# <a name="turn-on-cloud-protection-in-microsoft-defender-antivirus"></a>Bulutta bulut korumasını Microsoft Defender Virüsten Koruma

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

[Buluttan koruma Microsoft Defender Virüsten Koruma](cloud-protection-microsoft-defender-antivirus.md) doğru, gerçek zamanlı ve akıllı koruma sağlar. Bulut koruması varsayılan olarak etkinleştirilmelidir; ancak, bulut korumasını kuruluşun ihtiyaçlarına uyacak şekilde yapılandırabilirsiniz.

## <a name="methods-to-configure-cloud-protection"></a>Bulut korumasını yapılandırma yöntemleri

Bulut koruması Microsoft Defender Virüsten Koruma birini kullanarak bu korumayı açabilirsiniz veya kapatabilirsiniz:

- Microsoft Endpoint Manager Yapılandırma Yöneticisi'ni Microsoft Intune teknik bilgiler
- Grup İlkesi
- PowerShell cmdlet'leri

Ayrıca, Windows Güvenliği uygulamasını kullanarak bulut korumasını tek tek uç noktalar üzerinde Windows Güvenliği kapatabilirsiniz. 

Uç noktaların bulut koruma hizmetine bağlana olduğundan emin olmak üzere belirli ağ bağlantısı gereksinimleri hakkında daha fazla bilgi için bkz. [Ağ bağlantılarını yapılandırma ve doğrulama](configure-network-connections-microsoft-defender-antivirus.md).

> [!NOTE]
> 11 Windows 10 Windows 11'de, bu makalede açıklanan Temel ve **Gelişmiş** raporlama seçenekleri arasında fark  yoktur. Bu eski bir farktır ve iki ayardan birini seçmek aynı bulut koruma düzeyine neden olur. Paylaşılan bilgilerin türü veya miktarında fark yoktur. Topladığımız bilgiler hakkında daha fazla bilgi için [Microsoft Gizlilik Bildirimi'ne bakın](https://go.microsoft.com/fwlink/?linkid=521839).

## <a name="use-intune-to-turn-on-cloud-protection"></a>Intune kullanarak bulut korumasını açma

1. Yönetim merkezine Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) ve oturum açma.

2. Giriş bölmesinde **Cihaz** yapılandırması ve **Profilleri> seçin**.

3. Yapılandırmak **istediğiniz Cihaz kısıtlamaları** profil türünü seçin. Yeni bir Cihaz kısıtlamaları profil türü **oluşturmanız gerekirse**, aşağıdaki Bağlantı bağlantılarında [cihaz kısıtlama ayarlarını Microsoft Intune](/intune/device-restrictions-configure).

4. Özellikler **Yapılandırma ayarları** \> **: Özellikleri düzenle'yi** \> **Microsoft Defender Virüsten Koruma**.

5. Bulut **teslimi koruma anahtarında** Etkinleştir'i **seçin**.

6. Örnek **göndermeden önce kullanıcılara sor açılan listesinde** Tüm verileri otomatik **olarak gönder'i seçin**.

Intune cihaz profilleri hakkında daha fazla bilgi ve ayarlarını oluşturma ve yapılandırma gibi daha fazla bilgi için bkz. [Cihaz Microsoft Intune nedir?](/intune/device-profiles)

## <a name="use-microsoft-endpoint-manager-to-turn-on-cloud-protection"></a>Bulut Microsoft Endpoint Manager açmak için E-depolamayı kullanma

1. Yönetim merkezine Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) ve oturum açma.

2. Uç nokta **güvenliği Virüsten Koruma'ya** \> **seçin**.

3. Virüsten koruma profili seçin. (Henüz profiliniz yoksa veya yeni bir profil oluşturmak için, aşağıdaki Bağlantı sayfasında cihaz kısıtlama [ayarlarını yapılandırma Microsoft Intune](/intune/device-restrictions-configure).

4. **Özellikler'i seçin**. Ardından, Yapılandırma **ayarları'nın yanında** Düzenle'yi **seçin**.

5. Bulut **koruması'nın** kapsamını genişletin ve **Bulut teslimi koruma düzeyi** listesinde, aşağıdaki seçeneklerden birini seçin:
   - **Yüksek**: Güçlü bir algılama düzeyi uygular.
   - **Yüksek artı**: Yüksek **düzeyi kullanır** ve daha fazla koruma önlemi uygular (istemci performansını etkileyebilir).
   - **Sıfır dayanıklılık**: Tüm bilinmeyen yürütülebilir dosyaları engeller.

6. Gözden Geçir **+ kaydet'i** ve sonra Kaydet'i **seçin**.

İlkeleri yapılandırma hakkında daha fazla Microsoft Endpoint Configuration Manager için bkz. Kötü amaçlı yazılımdan koruma ilkeleri oluşturma ve dağıtma[: Bulut koruma hizmeti](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service).

## <a name="use-group-policy-to-turn-on-cloud-protection"></a>Bulut korumasını açmak için Grup İlkesi kullanma

1. Grup İlkesi yönetim aygıtınızda, Grup İlkesi [Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'yi **seçin**.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde** Bilgisayar **yapılandırması'ne gidin**.

3. Yönetim **şablonları'ı seçin**.

4. Bileşenleri ve bileşenleri Windows **ağacı genişletin** >  **Microsoft Defender Virüsten Koruma > HARITALAR**

    > [!NOTE]
    > HARITALAR ayarları buluta teslim edilen korumayla eşittir.

5. Microsoft HARITALAR'a **Katıl'a çift tıklayın**. Seçeneğin açık olduğundan ve Temel HARITALAR veya Gelişmiş **HARITALAR'a ayar** **olduğundan emin olun**. **Tamam**'ı seçin.

    Algılanan yazılım hakkında temel veya ek bilgiler göndermeyi seçebilirsiniz:

    - Temel HARITALAR: Temel üyelik, Microsoft'a kötü amaçlı yazılım ve aygıtınızda algılanan olası istenmeyen yazılım hakkında temel bilgiler gönderir. Bu bilgiler yazılımın nereden geldiğini (URL'ler ve kısmi yollar gibi), tehditi çözmek için  alınan eylemleri ve eylemlerin başarılı olup olmadığını içerir.

    - Gelişmiş HARITALAR: Temel bilgilerin yanı sıra, gelişmiş üyelik kötü amaçlı yazılım ve istenmeyen olabilecek yazılımlar hakkında ayrıntılı bilgiler, yazılımın tam yolu ve yazılımın cihazınızı nasıl etkile ilgili ayrıntılı bilgiler gönderir.

6. Daha fazla çözümleme **yapmak gerektiğinde Dosya örnekleri gönder'e çift tıklayın**. İlk seçeneğin Etkin olarak ve **diğer** seçeneklerden biri olarak ayarildiğinden emin olun:

   - **Güvenli örnekler gönderme** (1)
   - **Tüm örnekleri gönderme** (3)

   >[!NOTE]
   > Güvenli **örnekler gönder** (1) seçeneği, örneklerin çoğunun otomatik olarak gönder anlamına gelir. Kişisel bilgi içerme olasılığı bulunan dosyalar yine de istenir ve ek onay gerektirir.
   > Her Zaman **Sor (0** ) seçeneğinin ayarı cihazın koruma durumunu düşürecek. Bunu Hiçbir zaman **gönderme** (2) olarak ayar yapmak, Uç [](configure-block-at-first-sight-microsoft-defender-antivirus.md) Nokta için Microsoft Defender'ın İlk Görüşte Engelle özelliğinin çalışmay anlamına gelir.

7. **Tamam**'ı seçin.

## <a name="use-powershell-cmdlets-to-turn-on-cloud-protection"></a>Bulut korumasını açmak için PowerShell cmdlet'lerini kullanma

Aşağıdaki cmdlet'ler bulut korumasını açabilirsiniz:

```PowerShell
Set-MpPreference -MAPSReporting Advanced
Set-MpPreference -SubmitSamplesConsent SendAllSamples
```

Microsoft Defender Virüsten Koruma ile PowerShell'i kullanma hakkında daha fazla bilgi için bkz. Microsoft Defender Virüsten Koruma [ve Microsoft Defender Virüsten Koruma cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) yapılandırmak ve çalıştırmak için PowerShell [cmdlet'lerini kullanma](/powershell/module/defender/) . [İlke CSP - Defender,özel](/windows/client-management/mdm/policy-csp-defender) olarak [-SubmitSamplesConsent hakkında daha fazla bilgiye de sahip olur](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent).

> [!IMPORTANT]
> **-SubmitSamplesConsent** `SendSafeSamples` ayarını (varsayılan, önerilen ayar) veya `NeverSend`olarak değiştirebilirsiniz`AlwaysPrompt`. Bu `SendSafeSamples` ayar, örneklerin çoğunun otomatik olarak gönder anlamına gelir. Büyük olasılıkla kişisel bilgi içeren dosyalar devam istemiyle sonuçlandıracak ve onay gerektirecektir.
> Ve `NeverSend` ayarlar `AlwaysPrompt` cihazın koruma düzeyini düşürer. Buna ek olarak `NeverSend` , bu ayar Uç nokta [için Microsoft Defender'ın](configure-block-at-first-sight-microsoft-defender-antivirus.md) İlk Görüşte Engelle özelliğinin çalışmay anlamına gelir.

## <a name="use-windows-management-instruction-wmi-to-turn-on-cloud-protection"></a>Bulut Windows açmak için YÖNETIM Yönergesi'ne (WMI) sahip komutlar kullanma

Aşağıdaki [**özellikler** için sınıf **MSFT_MpPreference**](/previous-versions/windows/desktop/defender/set-msft-mppreference) Set yöntemini kullanın:

```WMI
MAPSReporting
SubmitSamplesConsent
```

İzin verilen parametreler hakkında daha fazla bilgi için [WMIv2 API'leri Windows Defender bkz.](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="turn-on-cloud-protection-on-individual-clients-with-the-windows-security-app"></a>Windows Güvenliği uygulamasıyla tek tek Windows Güvenliği açma

> [!NOTE]
> **Microsoft MAPS** Grup İlkesini raporlama için yerel ayarı geçersiz kıl ayarı Devre Dışı olarak  ayarlanırsa **,** Windows Ayarlar'daki Bulut tabanlı koruma ayarı gri olur ve kullanılamaz. Grup İlkesi Nesnesi aracılığıyla yapılan değişikliklerin, ayarın Grup İlkesi Nesnesinde güncelleştirilmeden önce tek tek uç noktalara dağıtılması Windows Ayarlar.

1. Görev Windows Güvenliği kalkan simgesini seçerek veya görev çubuğu için başlangıç menüsünü arayarak görev çubuğunu **Windows Güvenliği**.

2. Virüs koruması **& kutucuğunu** (veya sol menü çubuğundaki kalkan simgesini) seçin ve ardından Ayarları yönet'in altında Virüs  koruması & **ayarlarını seçin**.

3. Bulut Tabanlı **Koruma ve Otomatik örnek gönderimin** **her ikisinin de** Açık olarak değiştir olduğunu **onaylayın**.

   > [!NOTE]
   > Otomatik örnek gönderim Grup İlkesi ile yapılandırılmışsa, ayar gri olur ve kullanılamaz.

## <a name="see-also"></a>Ayrıca bkz.

- [E-postada Microsoft bulut korumasını Microsoft Defender Virüsten Koruma](cloud-protection-microsoft-defender-antivirus.md)

- [Kötü amaçlı yazılımlardan koruma ilkeleri oluşturma ve dağıtma: Bulut koruma hizmeti](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)

- [PowerShell cmdlet'lerini kullanarak Microsoft Defender Virüsten Koruma](use-powershell-cmdlets-microsoft-defender-antivirus.md)
