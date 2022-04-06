---
title: Değişiklik korumasıyla güvenlik ayarlarını koruma
ms.reviewer: mattcall, pahuijbr, hayhov, oogunrinde
manager: dansimp
description: Kötü amaçlı uygulamaların önemli güvenlik ayarlarını değiştirmesini önlemek için değişiklik koruması kullanın.
keywords: kötü amaçlı yazılım, defender, virüsten koruma, izinsiz yazılıma karşı koruma
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom:
- nextgen
- admindeeplinkDEFENDER
ms.technology: mde
ms.date: 01/18/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 4413704981343a067ab5923ce644f62c62b034c8
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476829"
---
# <a name="protect-security-settings-with-tamper-protection"></a>Değişiklik korumasıyla güvenlik ayarlarını koruma

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Değişiklik koruması, aşağıdaki Sürümlerin birini çalıştıran cihazlar için Windows:

- Windows 10
- Windows 11
- Windows 10 Enterprise oturumda
- Windows 11 Enterprise oturumda 
- Windows Server 2019
- Windows Server 2022
- Windows Server, sürüm 1803 veya sonrası
- Windows Server 2016
- Windows Server 2012 R2

> [!NOTE]
> R2'de Windows Server 2012 koruma, modern birleşik çözüm paketi kullanılarak ekli cihazlar için kullanılabilir. Daha fazla bilgi için bkz[. R2 ve 2016 Preview'da kullanmak için modern birleşik Windows Server 2012 yeni işlevler](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).

## <a name="overview"></a>Genel bakış

Bazı siber saldırı türleri sırasında, kötü saldırılar makinelerde virüsten koruma gibi güvenlik özelliklerini devre dışı bırakmayı dener. Verilerinize daha kolay erişim elde etmek, kötü amaçlı yazılım yüklemek veya verilerinizden, kimliklerinize ve cihazlarınıza başka bir şekilde istismar etmek için güvenlik özelliklerinizi devre dışı bırakmak gibi kötü bir şey. Tamper protection, bu tür şeyleri önlemeye yardımcı olur.

Değiştirilme korumasıyla, kötü amaçlı uygulamaların şu tür eylemler gerçekleştireni engel olur:

- Virüs ve tehdit korumasını devre dışı bırakma
- Gerçek zamanlı korumayı devre dışı bırakma
- Davranış izlemeyi kapatma
- Virüsten koruma yazılımını devre dışı bırakma (IOfficeAntivirus (IOAV)gibi)
- Bulut teslimi korumasını devre dışı bırakma
- Güvenlik zekası güncelleştirmelerini kaldırma
- Algılanan tehditlere yönelik otomatik eylemleri devre dışı bırakma

### <a name="how-it-works"></a>Nasıl çalışır?

Tamper protection temelde Microsoft Defender Virüsten Koruma ve varsayılan değerlerini kilitler ve güvenlik ayarlarınızın, uygulamalar ve yöntemler aracılığıyla değiştirilebilir. Örneğin:

- Windows aygıtınızda Kayıt Defteri Düzenleyicisi'nde ayarları yapılandırma
- PowerShell cmdlet'leri aracılığıyla ayarları değiştirme
- Ayarlar aracılığıyla güvenlik ayarlarını düzenleme grup ilkesi

Tamper protection, güvenlik ayarlarınızı görüntülemenizi engellemez. Ayrıca, microsoft olmayan virüsten koruma uygulamalarının Windows Güvenliği uygulamasına kaydolmasını da etkilemez. Kuruluşta Windows 10 Enterprise E5 kullanıyorsa, tek tek kullanıcılar değiştirilme koruması ayarını değiştiremez; bu gibi durumlarda, koruma güvenlik ekipleri tarafından yönetilir.

### <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?

<br/><br/>

|Bu görevi gerçekleştirmek için...|Bu bölüme bakın...|
|---|---|
|Kiracınız genelinde değişiklik korumasını yönetme <p> Değişiklik korumasını Microsoft 365 Defender veya kapatmak için alan portalını kullanma|[Dış müdahale korumasını kullanarak organizasyon için Microsoft 365 Defender](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)|
|Kuruluşta değişiklik koruma ayarlarına ince ayar yapın <p> Dış Intune (Microsoft Endpoint Manager) kullanarak değişiklik korumasını açma veya kapatma. Bu yöntemle, bazı kullanıcılar veya tüm kullanıcılar için değişiklik korumasını yapılandırabilirsiniz.|[Dış müdahale korumasını kullanarak organizasyon için Microsoft Endpoint Manager](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)|
|Dış müdahale korumasını, bu şekilde açmak veya kapatmak Configuration Manager|[Configuration Manager sürüm 2006'da kiracı ekleme kullanarak Configuration Manager korumasını yönetme](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)|
|Tek bir cihaz için değişiklik korumasını açma (veya kapatma)|[Tek bir cihazda oynanma korumasını yönetme](#manage-tamper-protection-on-an-individual-device)|
|Cihazlarda değiştirilme girişimleriyle ilgili ayrıntıları görüntüleme|[Değiştirilme girişimleri hakkında bilgi görüntüleme](#view-information-about-tampering-attempts)|
|Güvenlik önerilerinizi gözden geçirme|[Güvenlik önerilerini gözden geçirme](#review-your-security-recommendations)|
|Sık sorulan sorular listesini gözden geçirme (SSS)|[SSS'lere göz atma](#view-information-about-tampering-attempts)|

Değişiklik korumasını etkinleştirmek için kullandığınız yönteme veya yönetim aracına bağlı olarak, bulut teslimi koruması üzerinde bağımlılık olabilir.

Aşağıdaki tablo yöntemler, araçlar ve bağımlılıklar hakkında ayrıntılar sağlar.

<br/><br/>

|Değişiklik koruması nasıl etkinleştirilir?|Buluta teslim edilen korumaya bağımlılık (HARITALAR)|
|---|---|
|Microsoft Intune|Hayır|
|Microsoft Endpoint Configuration Manager + Kiracı Ekleme|Hayır|
|Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com))|Evet|

## <a name="manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalını kullanarak, Microsoft 365 Defender yönetme

Dış müdahale koruması, kiracınız için Sayfa Koruma portalı () Microsoft 365 Defender veya kapatabilirsiniz[https://security.microsoft.com](https://security.microsoft.com). İşte gözlerde tutma gereken birkaç nokta:

- Şu anda, yeni dağıtımlarda portalda Microsoft 365 Defender korumayı yönetme seçeneği varsayılan olarak açıktır. Mevcut dağıtımlarda, üzerine oynanmaya karşı koruma ima göre kullanılabilir. Kabul etmek için, Gelişmiş <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Uç Microsoft 365 Defender Gelişmiş</a> Özellikler  \> **Ayarlar'i** \>  \> **seçin**.

- Üzerinde değişiklik Microsoft 365 Defender yönetmek için Dış Alan Portalı'Intune veya kiracı ekleme yöntemini kullanmazsınız.

- Microsoft 365 Defender portalında değişiklik korumasını yönetirken, bu ayar kiracı genelinde uygulanır ve bu durum Windows 10, Windows 10 Enterprise oturumu, birden çok oturum Windows 11 veya başka bir Windows 11 Enterprise  multi-session, Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 veya Windows Server 2022. Değişiklik korumasına ince ayar yapmak (bazı cihazlarda değişiklik korumasının bazı cihazlarda kapalı olması gibi) için, kiracı eklemeli [](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager) Microsoft Endpoint Manager veya [Configuration Manager'i kullanın](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006).

- Karma bir ortamınız varsa, bu ortamda yapılandırılmış olan Intune, geçiş portalında yapılandırılan ayarlardan Microsoft 365 Defender alır.

### <a name="requirements-for-managing-tamper-protection-in-the-microsoft-365-defender-portal"></a>Dış portalda değişiklik korumasını yönetme Microsoft 365 Defender gereksinimleri

- Genel yönetici, [güvenlik](/microsoft-365/security/defender-endpoint/assign-portal-access) yöneticisi veya güvenlik işlemleri gibi uygun izinlere atanmış olması gerekir.

- Windows cihazlarınız aşağıdaki Windows sürümlerinden birini çalıştırabiliyor Windows:
  
  - Windows 10
  - Windows 11
  - Windows 10 Enterprise oturumda
  - Windows 11 Enterprise oturumda 
  - Windows Server 2019
  - Windows Server 2022
  - Windows Server, sürüm 1803 veya sonrası
  - Windows Server 2016
  - Windows Server 2012 R2

Sürümler hakkında daha fazla bilgi için bkz[. Windows 10 bilgi.](/windows/release-health/release-information)

- Cihazlarınızı mobil [cihaza Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/onboarding).

- Cihazlarınız kötü amaçlı yazılımdan koruma platform sürümü (veya `4.18.2010.7` üzeri) ve kötü amaçlı yazılımdan koruma altyapısı sürümü (veya `1.1.17600.5` üzeri) kullanıyor olmalı. ([Geçerli Microsoft Defender Virüsten Koruma yönetme ve taban çizgilerini uygulama](manage-updates-baselines-microsoft-defender-antivirus.md).)

- [Bulut teslimi korumasının](enable-cloud-protection-microsoft-defender-antivirus.md) açık olması gerekir.

### <a name="turn-tamper-protection-on-or-off-in-the-microsoft-365-defender-portal"></a>Dış müdahale korumasını portalda açma (Microsoft 365 Defender kapatma

:::image type="content" source="../../media/mde-turn-tamperprotectionon.png" alt-text="Dış dış korumayı portalda Microsoft 365 Defender açma" lightbox="../../media/mde-turn-tamperprotectionon.png":::

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. Uç **Ayarlar** \> **seçin**.

3. Genel Gelişmiş **özellikler'e** \> gidin ve korumayı açma.

## <a name="manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager"></a>Dış müdahale korumasını kullanarak organizasyon için Microsoft Endpoint Manager

If your organization uses Microsoft Endpoint Manager (MEM), you can turn turn tamper protection on (or off) for your organization in the Microsoft Endpoint Manager center ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Üzerinde Intune ayarlarına ince ayar yapmak istediğiniz zaman Ayarları Değiştir'i kullanın. Örneğin, tüm cihazlarda değil de, üzerinde değişiklik korumasını etkinleştirmek istediğiniz Intune.

### <a name="requirements-for-managing-tamper-protection-in-endpoint-manager"></a>Dış müdahaleye karşı korumayı yönetme Endpoint Manager

- Cihazlarınızı mobil [cihaza Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/onboarding).

- Genel yönetici, [güvenlik](/microsoft-365/security/defender-endpoint/assign-portal-access) yöneticisi veya güvenlik işlemleri gibi uygun izinlere atanmış olması gerekir.

- Organizasyonunız cihazları [yönetmek Microsoft Endpoint Manager e-posta kullanıyor](/mem/endpoint-manager-getting-started). (Microsoft Endpoint Manager (MEM) lisansları gereklidir; MEM; Microsoft 365 E3/E5, Enterprise Mobility + Security E3/E5, Microsoft 365 İş Ekstra, Microsoft 365 F1/F3, Microsoft 365 Kamu G3/G5 ve ilgili eğitim lisansları.)

- Windows cihazlarınız [1709](/windows/release-health/status-windows-10-1709), Windows 11 Windows 10 [1803, 1809](/windows/release-health/status-windows-10-1803) veya üzerinde çalışıyor olabilir. [](/windows/release-health/status-windows-10-1809-and-windows-server-2019) (Sürümler hakkında daha fazla bilgi için bkz[. Windows 10 bilgi.](/windows/release-health/release-information)

- 1.287.60.0 [](https://www.microsoft.com/wdsi/definitions) (Windows veya üzeri) olarak güncelleştirilmiş güvenlik zekası ile Windows güvenliği kullanıyorsanız gerekir.

- Cihazlarınız kötü amaçlı yazılımdan koruma platform sürümü 4.18.1906.3 (veya üzeri) ve kötü amaçlı yazılımdan koruma altyapısı sürümünü (veya üzeri) `1.1.15500.X` kullanıyor olmalı. ([Geçerli Microsoft Defender Virüsten Koruma yönetme ve taban çizgilerini uygulama](manage-updates-baselines-microsoft-defender-antivirus.md).)

### <a name="turn-tamper-protection-on-or-off-in-microsoft-endpoint-manager"></a>Dış korumayı açma (veya kapatma) Microsoft Endpoint Manager

:::image type="content" source="images/turnontamperprotectinmem.png" alt-text="Dışla değiştirilme korumasının açık Intune" lightbox="images/turnontamperprotectinmem.png":::

1. Genel yönetim [Microsoft Endpoint Manager Uç nokta](https://go.microsoft.com/fwlink/?linkid=2109431) güvenliği Virüsten **Koruma'ya gidin** \> ve + İlke **Oluştur'a gidin**.

   - **Platform listesinden Ekle** ve **Windows 10'yi seçin**.
   - Profil **listesinde Kullanıcı** deneyimini **Windows Güvenliği seçin**.

2. Aşağıdaki ayarı içeren bir profil oluşturun:

    - **Microsoft Defender'ın devre dışı bırak masını engellemek için değişiklik korumasını etkinleştirme: Etkinleştirme**

3. Profili bir veya birden çok gruba attayabilirsiniz.
 
### <a name="manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006"></a>Configuration Manager, sürüm 2006 ile Configuration Manager değişiklik korumasını yönetme

[Configuration Manager'in 2006](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2006) sürümünü kullanıyorsanız, Windows 10, Windows 10 Enterprise, Windows 11 veya çoklu oturumlarda Windows 11 Enterprise koruma ayarlarını yönetebilirsiniz. Windows Server 2012 ekleme adlı bir yöntem kullanarak R2, Windows Server 2016, Windows Server 2019 ve Windows Server *2022'yi tıklatın*. Kiracı ekleme, yalnızca şirket içi Configuration Manager cihazlarınızı Microsoft Endpoint Manager yönetim merkezine eşitlemenize ve ardından uç nokta güvenlik yapılandırma ilkelerini şirket içi koleksiyonlara ve cihazlara & sağlar.

> [!NOTE]
> Bu yordam, Windows 10, Windows 10 Enterprise çoklu oturum, Windows 11, Windows 11 Enterprise çoklu oturum, Windows Server 2019 ve Windows Server 2022 çalıştıran cihazlara değişiklik korumasının süresini uzatmak için kullanılabilir. Bu yordamda sözü geçen kaynaklara ilişkin önkoşulları ve diğer bilgileri gözden geçirmeyi sağlar.

1. Kiracı ekleme ayarlama. Daha fazla bilgi için bkz. [Kullanmaya başlayın: Yönetim merkezinden uç nokta güvenlik ilkelerini oluşturma ve dağıtma](/mem/configmgr/tenant-attach/endpoint-security-get-started).

2. Genel yönetim [Microsoft Endpoint Manager Uç nokta](https://go.microsoft.com/fwlink/?linkid=2109431) güvenliği Virüsten **Koruma'ya gidin** \> ve + İlke **Oluştur'a gidin**.

   - Platform listesinde **,** Platform, **Windows 10, Windows 11 ve Windows (ConfigMgr)'i seçin**.
   - Profil listesinde **,** En iyi **Windows Güvenliği (önizleme)'yi seçin**.

3. İlkeyi cihaz koleksiyonunuza dağıtın.

#### <a name="need-help-with-this-method"></a>Bu yöntemle ilgili yardıma mı ihtiyacınız var?

Aşağıdaki kaynaklara bakın:

- [Ayarlar'Windows Güvenliği deneyimi profili için Microsoft Intune](/mem/intune/protect/antivirus-security-experience-windows-settings)
- [Teknik Community Blogu: Kiracı Ekleme istemcilerini Configuration Manager Üzerinde Değişiklik Koruması'nın açıklanması](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

## <a name="manage-tamper-protection-on-an-individual-device"></a>Tek bir cihazda oynanma korumasını yönetme

> [!NOTE]
> Tamper protection blocks, kayıt defteri Microsoft Defender Virüsten Koruma ayarlarını değiştirmeye çalışır.
>
> Bu ayarları değiştiren Microsoft olmayan güvenlik ürünleri veya kurumsal yükleme betikleriyle oynanmamasını sağlamaya yardımcı olmak için, **Windows Güvenliği'e** gidin ve **Security Intelligence'i** 1.287.60.0 veya sonraki bir sürüme güncelleştirin. (Bkz [. Güvenlik zekası güncelleştirmeleri](https://www.microsoft.com/wdsi/definitions).)
>
> Bu güncelleştirme yapıldıktan sonra, koruma koruma kayıt defteri ayarlarınızı korumaya devam eder ve günlükler hata döndürmeden bunları değiştirmeye çalışır.

Ev kullanıcısıysanız veya güvenlik ekibi tarafından yönetilen ayarlara tabi değilsanız, değişiklik korumasını yönetmek için Windows Güvenliği uygulamasını kullanabilirsiniz. Cihazınıza müdahale koruması gibi güvenlik ayarlarını değiştirmek için uygun yönetici izinlerine sahip olmak gerekir.

Windows Güvenliği uygulamasında şunları görüyorsunuz:

:::image type="content" source="images/tamperprotectionturnedon.png" alt-text="Dış müdahale korumasının açık olduğu Windows 10 Home" lightbox="images/tamperprotectionturnedon.png":::

1. **Başlat'ı** seçin ve Güvenlik yazmaya *başlayın*. Arama sonuçlarında **Seçenekler'i Windows Güvenliği**.

2. Virüs **ve tehdit & Virüs ve tehdit** \> **&'i seçin**.

3. Tamper **Protection'i** Kapalı **veya Kapalı** olarak **ayarlayın**.

## <a name="are-you-using-windows-server-2016-or-windows-version-1709-1803-or-1809"></a>Windows Server 2016 ya da Windows 1709, 1803 veya 1809 sürümünü mü kullanıyorsunuz?

Windows Server 2016, Windows 10 sürüm 1709, 1803 veya [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) kullanıyorsanız, Windows Güvenliği uygulamasında Üzerinde Değişiklik Koruması'Windows Güvenliği görmüyorsanız. Bunun yerine, Üzerinde değişiklik korumasının etkin olup olmadığını belirlemek için PowerShell kullanabilirsiniz.

Değişiklik Windows Server 2016, Ayarlar koruma etkinleştirildiğinde uygulama gerçek zamanlı korumanın durumunu doğru şekilde yansıtmaz.

#### <a name="use-powershell-to-determine-whether-tamper-protection-and-real-time-protection-are-turned-on"></a>Üzerinde değişiklik korumasının ve gerçek zamanlı korumanın açık olup olmadığını belirlemek için PowerShell kullanma

1. Windows PowerShell açın.

2. [Get-MpCompstatus](/powershell/module/defender/get-mpcomputerstatus?preserve-view=true&view=win10-ps) PowerShell cmdlet'ini kullanın.

3. Sonuç listesinde, veya .`IsTamperProtected` `RealTimeProtectionEnabled` (Doğru değerinin *değeri,* değişiklik korumasının etkin olduğu anlamına gelir.)

## <a name="view-information-about-tampering-attempts"></a>Değiştirilme girişimleri hakkında bilgi görüntüleme

Değiştirilme girişimleri normalde daha büyük siber saldırıların olduğunu gösteriyor. Kötü denemeler, kalıcı ve algılanmamış kalmanın bir yolu olarak güvenlik ayarlarını değiştirmeye çalışsın. Kuruluş güvenlik ekibinin bir parçasıysanız, söz konusu girişimler hakkında bilgileri  görüntüp ardından tehditleri azaltmak için uygun eylemleri gerçekleştirebilirsiniz.

Değiştirilme girişimi algılandığında, portalda () üzerinde [bir Microsoft 365 Defender yükseltilmiştir](/microsoft-365/security/defender-endpoint/portal-overview)[https://security.microsoft.com](https://security.microsoft.com).

:::image type="content" source="images/tamperattemptalert.png" alt-text="Microsoft 365 Defender portalı" lightbox="images/tamperattemptalert.png":::

Bu [uç noktada algılama ve yanıtlama](overview-endpoint-detection-response.md) [gelişmiş arama](advanced-hunting-overview.md) özelliklerini ve gelişmiş Uç Nokta için Microsoft Defender kullanarak, güvenlik işlemleri takımınız bu denemeleri araştırarak bu girişimlere karşı adrese sahip olabilir.

## <a name="review-your-security-recommendations"></a>Güvenlik önerilerinizi gözden geçirme

Tamper protection, Tehdit Güvenlik [& Özellikleri ile tümleştirilmiştir](next-gen-threat-and-vuln-mgt.md) . [Güvenlik önerileri, üzerinde](tvm-security-recommendation.md) değişiklik korumasının açık olduğundan emin olmaktır. Örneğin, üzerinde oynanmaya göre arama *.* Sonuçlarda, daha fazla bilgi **edinmek ve açmak için** Korumayı Aç'ı seçin.

:::image type="content" source="images/tamperprotectsecurityrecos.png" alt-text="Dış portalda değişiklik Microsoft Defender Güvenlik Merkezi açma" lightbox="images/tamperprotectsecurityrecos.png":::

Tehdit Güvenlik Açığı Yönetimi hakkında daha fazla & için Bkz. [Pano Öngörüleri - güvenlik Tehdit ve Güvenlik Açığı Yönetimi](tvm-dashboard-insights.md#dashboard-insights---threat-and-vulnerability-management).

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="on-which-versions-of-windows-can-i-configure-tamper-protection"></a>Dış müdahale korumasını Windows sürümlerim nasıl yapılandırılır?

Windows 10 birlikte işletim [sistemi 1709](/windows/release-health/status-windows-10-1709), [1803](/windows/release-health/status-windows-10-1803), [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) veya [Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint).
  
Windows 10 Enterprise oturumda

Windows 11

Windows 11 Enterprise oturumda
  
kiracı eklemeli Configuration Manager sürüm 2006 kullanıyorsanız, değişiklik koruması Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 ve Windows Server 2022'ye kadar uzatılabilir. Bkz [. Kiracı ekleme: Yönetim merkezinden (önizleme) uç nokta güvenliği Virüsten Koruma ilkesi oluşturma ve dağıtma](/mem/configmgr/tenant-attach/deploy-antivirus-policy).

### <a name="will-tamper-protection-affect-non-microsoft-antivirus-registration-in-the-windows-security-app"></a>Tamper protection, Windows Güvenliği uygulamasında Microsoft olmayan virüsten koruma kayıtlarını etkiler mi?

Hayır. Microsoft dışı virüsten koruma teklifleri, bu Windows Güvenliği devam edecektir.

### <a name="what-happens-if-microsoft-defender-antivirus-is-not-active-on-a-device"></a>Bir Microsoft Defender Virüsten Koruma etkin değilken ne olur?

Başka bir cihaza Uç Nokta için Microsoft Defender, pasif Microsoft Defender Virüsten Koruma çalışmadan çalışır. Böyle durumlarda, koruma hizmeti ve özelliklerini korumaya devam eder.

### <a name="how-do-i-turn-tamper-protection-on-or-off"></a>Nasıl yaparım? korumayı açmak mı yoksa kapatmak mı?

Ev kullanıcısıysanız bkz. Tek [bir cihazda değişiklik korumasını yönetme](#manage-tamper-protection-on-an-individual-device).

[Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint) kullanan bir kuruluşsanız, diğer uç nokta koruma özelliklerini yönetirken Intune dış müdahale korumasını yönetebilirsiniz. Bu makalenin aşağıdaki bölümlerine bakın:

- [Dış müdahaleye karşı korumayı Microsoft Endpoint Manager](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)
- [Dış müdahale korumasını portalını Microsoft 365 Defender yönetme](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)

### <a name="how-does-configuring-tamper-protection-in-intune-affect-how-i-manage-microsoft-defender-antivirus-with-group-policy"></a>Dış müdahaleye karşı korumayı Intune, dış müdahale korumasını Microsoft Defender Virüsten Koruma yönetme grup ilkesi?

Grup ilkesi, değişiklik koruması için geçerli değildir. Değişiklik koruması Microsoft Defender Virüsten Koruma ilgili ayarlarda yapılan değişiklikler yoksayılır.

### <a name="if-we-use-microsoft-intune-to-configure-tamper-protection-does-it-apply-only-to-the-entire-organization"></a>Korumayı yapılandırmak Microsoft Intune dış koruma kullanıyoruz, bu yalnızca kuruluşun tamamı için geçerli mi?

Dış müdahaleye karşı korumayı yapılandırma konusunda esnek Intune. Tüm kuruluşun hedefini oluşturabilir veya belirli cihazları ve kullanıcı gruplarını seçin.

### <a name="can-i-configure-tamper-protection-with-microsoft-endpoint-configuration-manager"></a>Dış Müdahale Koruması'nın ayarlarını Microsoft Endpoint Configuration Manager?

Kiracı ekleme kullanıyorsanız, Kiracı Ekleme'Microsoft Endpoint Configuration Manager. Aşağıdaki kaynaklara bakın:

- [Configuration Manager, sürüm 2006 ile Configuration Manager değişiklik korumasını yönetme](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)
- [Teknik Community blogu: Kiracı Ekleme istemcileri için Değişiklik Koruması Configuration Manager Açıklaması](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

### <a name="i-have-the-windows-e3-enrollment-can-i-use-configuring-tamper-protection-in-intune"></a>Windows E3 kaydım var. Dış müdahaleye karşı yapılandırma korumasını Intune?

Şu anda, Dış Intune'de değişiklik korumasını yapılandırma, yalnızca dış müdahale koruması [Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint).

### <a name="what-happens-if-i-try-to-change-microsoft-defender-for-endpoint-settings-in-intune-microsoft-endpoint-configuration-manager-and-windows-management-instrumentation-when-tamper-protection-is-enabled-on-a-device"></a>Bir cihazda Tamper Protection etkinleştirildiğinde Uç Nokta için Microsoft Defender, Intune Microsoft Endpoint Configuration Manager ve Windows Yönetim Aracı'Windows ayarları değiştirmeye çalışırsanız ne olur?

Koruma korumasıyla korunan özellikleri değiştiremezsiniz; bu tür değişiklik istekleri yoksayılır.

### <a name="im-an-enterprise-customer-can-local-admins-change-tamper-protection-on-their-devices"></a>Ben kurumsal bir müşteriyim. Yerel yöneticiler cihazlarında değişiklik korumasını değiştirebilir mi?

Hayır. Yerel yöneticiler, değişiklik koruma ayarlarını değiştiremez veya değiştiremez.

### <a name="what-happens-if-my-device-is-onboarded-with-microsoft-defender-for-endpoint-and-then-goes-into-an-off-boarded-state"></a>Cihazım şu postayla birlikte Uç Nokta için Microsoft Defender sonra yönetim kurulu olmayan bir durumla olursa ne olur?

Cihaz dış bağlantıdan çıkarıldı Uç Nokta için Microsoft Defender, yani yönetimi kaldıran cihazlar için varsayılan durum olan üzerinde değişiklik koruması açıktır.

### <a name="if-the-status-of-tamper-protection-changes-are-alerts-shown-in-the-microsoft-365-defender-portal"></a>Değişiklik yapılmış koruma değişikliklerinin durumu, değişiklik portalında Microsoft 365 Defender gösterilir mi?

Evet. Uyarı, Uyarılar altında [https://security.microsoft.com](https://security.microsoft.com) **gösterilir**.

Güvenlik işlemleri ekipleriniz aşağıdaki örnekte olduğu gibi, arama sorgularını da kullanabilir:

`AlertInfo|where Title == "Tamper Protection bypass"`

[Değiştirilme girişimleriyle ilgili bilgileri görüntüleme](#view-information-about-tampering-attempts).

## <a name="see-also"></a>Ayrıca bkz.

[Diğer bilgisayarlara Windows için Endpoint Protection ile güvenli Microsoft Intune](/intune/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

[Nasıl olduğunu genel Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint)

[Birlikte daha iyi: Microsoft Defender Virüsten Koruma ve Uç Nokta için Microsoft Defender](why-use-microsoft-defender-antivirus.md)
