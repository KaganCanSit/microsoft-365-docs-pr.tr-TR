---
title: Değişiklik korumasıyla güvenlik ayarlarını koruyun
ms.reviewer: mattcall, pahuijbr, hayhov, oogunrinde
manager: dansimp
description: Kötü amaçlı uygulamaların önemli güvenlik ayarlarını değiştirmesini önlemek için kurcalama koruması kullanın.
keywords: kötü amaçlı yazılım, defender, virüsten koruma, kurcalama koruması
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
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 36aa48f26e60e2c3afb034a218c3356e27d75ffd
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873368"
---
# <a name="protect-security-settings-with-tamper-protection"></a>Değişiklik korumasıyla güvenlik ayarlarını koruyun

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Kurcalama koruması, Windows'nin aşağıdaki sürümlerinden birini çalıştıran cihazlar için kullanılabilir:

- Windows 11
- Çoklu oturum Windows 11 Enterprise 
- Windows 10
- Çoklu oturum Windows 10 Enterprise
- Windows Server 2022
- Windows Server 2019
- Windows Server, sürüm 1803 veya üzeri
- Windows Server 2016
- Windows Server 2012 R2

> [!NOTE]
> Windows Server 2012 R2'de kurcalama koruması, modern birleşik çözüm paketi kullanılarak eklenen cihazlar için kullanılabilir. Daha fazla bilgi için bkz. [Windows sunucularını Uç Nokta için Microsoft Defender hizmetine ekleme](/microsoft-365/security/defender-endpoint/configure-server-endpoints).

## <a name="overview"></a>Genel bakış

Bazı siber saldırılar sırasında kötü aktörler, makinelerinizde virüsten koruma gibi güvenlik özelliklerini devre dışı bırakmaya çalışır. Kötü aktörler verilerinize daha kolay erişim elde etmek, kötü amaçlı yazılım yüklemek veya verilerinizi, kimliğinizi ve cihazlarınızı başka bir şekilde kullanmak için güvenlik özelliklerinizi devre dışı bırakmak ister. Kurcalama koruması, bu tür şeylerin oluşmasını önlemeye yardımcı olur. Kurcalama koruması ile kötü amaçlı uygulamaların aşağıdaki gibi eylemler gerçekleştirmesi engellenir:

- Virüs ve tehdit korumasını devre dışı bırakma
- Gerçek zamanlı korumayı devre dışı bırakma
- Davranış izlemeyi kapatma
- IOfficeAntivirus (IOAV) gibi virüsten korumayı devre dışı bırakma
- Bulut tabanlı korumayı devre dışı bırakma
- Güvenlik bilgileri güncelleştirmelerini kaldırma
- Algılanan tehditlerde otomatik eylemleri devre dışı bırakma

### <a name="how-it-works"></a>Nasıl çalışır?

Kurcalama koruması temelde Microsoft Defender Virüsten Koruma güvenli ve varsayılan değerlerine kilitler ve güvenlik ayarlarınızın uygulamalar ve yöntemler aracılığıyla değiştirilmesini önler:

- Windows cihazınızda Kayıt Defteri Düzenleyicisi'nde ayarları yapılandırma
- PowerShell cmdlet'leri aracılığıyla ayarları değiştirme
- grup ilkesi aracılığıyla güvenlik ayarlarını düzenleme veya kaldırma

Kurcalama koruması, güvenlik ayarlarınızı görüntülemenizi engellemez. Ayrıca, kurcalama koruması Microsoft dışı virüsten koruma uygulamalarının Windows Güvenliği uygulamasına nasıl kaydoldığını etkilemez. Kuruluşunuz Windows 10 Enterprise E5 kullanıyorsa, tek tek kullanıcılar kurcalama koruması ayarını değiştiremez; bu gibi durumlarda, kurcalama koruması güvenlik ekibiniz tarafından yönetilir.

### <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?

|Bu görevi gerçekleştirmek için...|Bu bölüme bakın...|
|---|---|
|Kiracınız genelinde kurcalama korumasını yönetme <p> Kurcalama korumasını açmak veya kapatmak için Microsoft 365 Defender portalını kullanma|[Microsoft 365 Defender kullanarak kuruluşunuz için kurcalama korumasını yönetme](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)|
|Kuruluşunuzda kurcalama koruması ayarlarına ince ayar yapma <p> Kurcalama korumasını açmak veya kapatmak için Intune (Microsoft Endpoint Manager) kullanın. Bu yöntemle bazı veya tüm kullanıcılar için kurcalama korumasını yapılandırabilirsiniz.|[Microsoft Endpoint Manager kullanarak kuruluşunuz için kurcalama korumasını yönetme](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)|
|Configuration Manager ile kuruluşunuz için kurcalama korumasını açma (veya kapatma)|[Configuration Manager, sürüm 2006 ile kiracı ekleme kullanarak kuruluşunuz için kurcalama korumasını yönetme](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)|
|Tek bir cihaz için kurcalama korumasını açma (veya kapatma)|[Tek bir cihazda kurcalama korumasını yönetme](#manage-tamper-protection-on-an-individual-device)|
|Cihazlardaki kurcalama girişimleriyle ilgili ayrıntıları görüntüleme|[Kurcalama girişimleri hakkındaki bilgileri görüntüleme](#view-information-about-tampering-attempts)|
|Güvenlik önerilerinizi gözden geçirin|[Güvenlik önerilerini gözden geçirme](#review-your-security-recommendations)|
|Sık sorulan soruların listesini gözden geçirin (SSS)|[SSS'lere göz atın](#view-information-about-tampering-attempts)|

## <a name="potential-dependency-on-cloud-protection"></a>Bulut korumasına olası bağımlılık  
  
Kurcalama korumasını etkinleştirmek için kullandığınız yönteme veya yönetim aracına bağlı olarak, [bulut tabanlı korumaya](cloud-protection-microsoft-defender-antivirus.md) bağımlılık olabilir. Bulut tabanlı koruma, bulut koruması veya Microsoft Gelişmiş Koruma Hizmeti (MAPS) olarak da adlandırılır.

Aşağıdaki tabloda yöntemler, araçlar ve bağımlılıklar hakkında ayrıntılar sağlanır.

| Kurcalama koruması nasıl etkinleştirilir? | Bulut korumasına bağımlılık |
|---|---|
|Microsoft Intune|Hayır|
|Kiracı Ekleme ile Microsoft Endpoint Configuration Manager|Hayır|
|Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com))|Evet|

## <a name="manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalını kullanarak kuruluşunuz için kurcalama korumasını yönetme

Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com) ) kullanılarak kiracınız için kurcalama koruması açılabilir veya kapatılabilir. Aklınızda bulundurmak istediğiniz birkaç nokta şunlardır:

- Şu anda, yeni dağıtımlar için Microsoft 365 Defender portalında kurcalama korumasını yönetme seçeneği varsayılan olarak açıktır. Mevcut dağıtımlar için, değişiklik koruması kabul temelinde kullanılabilir. Kabul etmek için <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalında</a> **Uç Noktalar** \> **Gelişmiş özellikler** \> **Kurcalama** **koruması'nı Ayarlar** \> seçin.
- kurcalama korumasını yönetmek için Microsoft 365 Defender portalını kullandığınızda, Intune veya kiracı ekleme yöntemini kullanmanız gerekmez.
- Microsoft 365 Defender portalında kurcalama korumasını yönettiğinizde, bu ayar kiracı genelinde uygulanır ve Windows 10 çalıştıran tüm cihazlarınızı Windows 10 Enterprise çok oturumlu, Windows 11 Windows 11 Enterprise  çok oturumlu, Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 veya Windows Server 2022. Kurcalama korumasına ince ayar yapmak (örneğin bazı cihazlarda kurcalama korumasına sahip olmak, diğerleri için kapalı olmak gibi), [kiracı eklemeli Microsoft Endpoint Manager veya Configuration Manager](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006) kullanın.[](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)
- Karma bir ortamınız varsa, Intune'de yapılandırılan kurcalama koruma ayarları, Microsoft 365 Defender portalında yapılandırılan ayarlardan önceliklidir.

### <a name="requirements-for-managing-tamper-protection-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında kurcalama korumasını yönetme gereksinimleri

- Genel yönetici, güvenlik yöneticisi veya güvenlik işlemleri gibi uygun [izinlere](/microsoft-365/security/defender-endpoint/assign-portal-access) sahip olmanız gerekir.

- Windows cihazlarınız aşağıdaki Windows sürümlerinden birini çalıştırıyor olmalıdır:
  
  - Windows 11
  - Çoklu oturum Windows 11 Enterprise 
  - Windows 10
  - Çoklu oturum Windows 10 Enterprise
  - Windows Server 2022
  - Windows Server 2019
  - Windows Server, sürüm 1803 veya üzeri
  - Windows Server 2016
  - Windows Server 2012 R2

Sürümler hakkında daha fazla bilgi için bkz. [Windows 10 sürüm bilgileri](/windows/release-health/release-information).

- Cihazlarınız [Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/onboarding) eklenmelidir.
- Cihazlarınız kötü amaçlı yazılımdan koruma platformu sürümünü `4.18.2010.7` (veya üzeri) ve kötü amaçlı yazılımdan koruma altyapısı sürümünü `1.1.17600.5` (veya üzerini) kullanıyor olmalıdır. ([Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetin ve temelleri uygulayın](manage-updates-baselines-microsoft-defender-antivirus.md).)
- [Bulut tabanlı koruma](enable-cloud-protection-microsoft-defender-antivirus.md) açık olmalıdır.

> [!NOTE]
> Microsoft 365 Defender portalı aracılığıyla kurcalama koruması etkinleştirildiğinde, kurcalama korumasının etkin durumunun denetlenebilmesi için bulut tabanlı koruma gerekir.  
> Kasım 2021 güncelleştirmesi (platform sürümü`4.18.2111.5`) ile başlayarak, bir cihaz için bulut tabanlı koruma açık değilse ve Microsoft 365 Defender portalında kurcalama koruması açıksa, bu cihaz için üzerinde değişiklik korumasının yanı sıra bulut tabanlı koruma da otomatik olarak açılır.   

### <a name="turn-tamper-protection-on-or-off-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında kurcalama korumasını açma (veya kapatma)

:::image type="content" source="../../media/mde-turn-tamperprotectionon.png" alt-text="Microsoft 365 Defender portalında kurcalama korumasını açma" lightbox="../../media/mde-turn-tamperprotectionon.png":::

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

2. **Ayarlar** \> **Uç Noktaları'nı** seçin.

3. **Genel** \> **Gelişmiş özellikler'e** gidin ve kurcalama korumasını açın.

## <a name="manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager"></a>Microsoft Endpoint Manager kullanarak kuruluşunuz için kurcalama korumasını yönetme

Kuruluşunuz Microsoft Endpoint Manager (MEM) kullanıyorsa, Microsoft Endpoint Manager yönetim merkezinde ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) kuruluşunuz için kurcalama korumasını açabilir (veya kapatabilirsiniz). Kurcalama koruması ayarlarına ince ayar yapmak istediğinizde Intune kullanın. Örneğin, tüm cihazlarda değil bazı cihazlarda kurcalama korumasını etkinleştirmek istiyorsanız Intune kullanın.

### <a name="requirements-for-managing-tamper-protection-in-endpoint-manager"></a>Endpoint Manager'de kurcalama korumasını yönetme gereksinimleri

- Cihazlarınız [Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/onboarding) eklenmelidir.
- Genel yönetici, güvenlik yöneticisi veya güvenlik işlemleri gibi uygun [izinlere](/microsoft-365/security/defender-endpoint/assign-portal-access) sahip olmanız gerekir.
- Kuruluşunuz [cihazları yönetmek için Microsoft Endpoint Manager](/mem/endpoint-manager-getting-started) kullanır. (Microsoft Endpoint Manager (MEM) lisansları gereklidir; MEM Microsoft 365 E3/E5, Enterprise Mobility + Security E3/E5, Microsoft 365 İş Ekstra, Microsoft 365 F1/F3, Microsoft 365 Kamu G3/G5 ve karşılık gelen eğitim lisansları.)
- Windows cihazlarınız Windows 11 veya Windows 10 [1709, 1803](/lifecycle/announcements/revised-end-of-service-windows-10-1709), [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) veya üzerini [](/lifecycle/announcements/windows-server-1803-end-of-servicing)çalıştırıyor olmalıdır. (Sürümler hakkında daha fazla bilgi için bkz. [Windows 10 sürüm bilgileri](/windows/release-health/release-information).)
- Güvenlik bilgileri 1.287.60.0 (veya üzeri) sürümüne güncelleştirilmiş Windows [güvenliği](https://www.microsoft.com/wdsi/definitions) kullanıyor olmanız gerekir.
- Cihazlarınız kötü amaçlı yazılımdan koruma platformu sürüm 4.18.1906.3 (veya üzeri) ve kötü amaçlı yazılımdan koruma altyapısı sürümünü `1.1.15500.X` (veya üzeri) kullanıyor olmalıdır. ([Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetin ve temelleri uygulayın](manage-updates-baselines-microsoft-defender-antivirus.md).)

### <a name="turn-tamper-protection-on-or-off-in-microsoft-endpoint-manager"></a>Microsoft Endpoint Manager'da kurcalama korumasını açma (veya kapatma)

:::image type="content" source="images/turnontamperprotectinmem.png" alt-text="Intune ile kurcalama korumasını açma" lightbox="images/turnontamperprotectinmem.png":::

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **Endpoint security** \> **Virüsten Koruma'ya** gidin ve **+ İlke Oluştur'u** seçin.

   - **Platform** listesinde **Windows 10 ve üzerini** seçin.
   - **Profil** listesinde **Windows Güvenliği deneyim'i** seçin.

2. Aşağıdaki ayarı içeren bir profil oluşturun:

    - **Microsoft Defender'ın devre dışı bırakılmasını önlemek için kurcalama korumasını etkinleştirme: Etkinleştir**

3. Profili bir veya daha fazla gruba atayın.
 
### <a name="manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006"></a>Configuration Manager, sürüm 2006 ile kuruluşunuz için kurcalama korumasını yönetme

[Configuration Manager 2006 sürümünü](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2006) kullanıyorsanız çoklu oturum, Windows 11 Windows 11 Enterprise çoklu oturum Windows 10 Enterprise Windows 10 üzerinde kurcalama koruma ayarlarını yönetebilirsiniz. *Kiracı ekleme* adlı bir yöntem kullanarak R2, Windows Server 2016, Windows Server 2019 ve Windows Server 2022'yi Windows Server 2012. Kiracı ekleme, yalnızca şirket içi Configuration Manager cihazlarınızı Microsoft Endpoint Manager yönetim merkezine eşitlemenizi ve ardından uç nokta güvenlik yapılandırma ilkelerini şirket içi koleksiyonlara & cihazlara teslim etmenizi sağlar.

> [!NOTE]
> Bu yordam, Windows 10, çok oturumlu, Windows 11 Windows 10 Enterprise, çok oturumlu Windows 11 Enterprise, Windows Server 2019 ve Windows Server 2022 çalıştıran cihazlara kurcalama korumasını genişletmek için kullanılabilir. Bu yordamda belirtilen kaynaklarda yer alan önkoşulları ve diğer bilgileri gözden geçirmeyi unutmayın. Windows Server 2012 R2 için Configuration Manager'nin modern, birleşik çözüm [sürümü 2203](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2203) gereklidir.

1. Kiracı eklemeyi ayarlayın. Daha fazla bilgi için bkz[. Kullanmaya başlayın: Yönetim merkezinden uç nokta güvenlik ilkeleri oluşturma ve dağıtma](/mem/configmgr/tenant-attach/endpoint-security-get-started).

2. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **Endpoint security** \> **Virüsten Koruma'ya** gidin ve **+ İlke Oluştur'u** seçin.

   - **Platform** listesinde **Windows 10, Windows 11 ve Windows Server (ConfigMgr)** öğesini seçin.
   - **Profil** listesinde **Windows Güvenliği deneyimi (önizleme)** seçeneğini belirleyin.

3. İlkeyi cihaz koleksiyonunuz için dağıtın.

#### <a name="need-help-with-this-method"></a>Bu yöntemle ilgili yardıma mı ihtiyacınız var?

Aşağıdaki kaynaklara bakın:

- [Microsoft Intune'daki Windows Güvenliği deneyimi profili için Ayarlar](/mem/intune/protect/antivirus-security-experience-windows-settings)
- [Teknik Community Blogu: Configuration Manager Kiracı Ekleme istemcileri için Kurcalama Koruması Duyuruları](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

## <a name="manage-tamper-protection-on-an-individual-device"></a>Tek bir cihazda kurcalama korumasını yönetme

> [!NOTE]
> Kurcalama koruması, kayıt defteri aracılığıyla Microsoft Defender Virüsten Koruma ayarlarını değiştirme girişimlerini engeller.
> Kurcalama korumasının Microsoft dışı güvenlik ürünlerini veya bu ayarları değiştiren kurumsal yükleme betiklerini engellemediğinden emin olmak için **Windows Güvenliği** gidin ve **Güvenlik zekasını** 1.287.60.0 veya sonraki bir sürüme güncelleştirin. (Bkz [. Güvenlik bilgileri güncelleştirmeleri](https://www.microsoft.com/wdsi/definitions).) Bu güncelleştirmeyi yaptıktan sonra, kurcalama koruması kayıt defteri ayarlarınızı korumaya devam eder ve hataları döndürmeden bunları değiştirmeye çalışır.

Ev kullanıcısıysanız veya güvenlik ekibi tarafından yönetilen ayarlara tabi değilseniz, kurcalama korumasını yönetmek için Windows Güvenliği uygulamasını kullanabilirsiniz. Kurcalama koruması gibi güvenlik ayarlarını değiştirmek için cihazınızda uygun yönetici izinlerine sahip olmanız gerekir.

Windows Güvenliği uygulamasında şunları görürsünüz:

:::image type="content" source="images/tamperprotectionturnedon.png" alt-text="Windows 10 Home'de kurcalama korumasını açma" lightbox="images/tamperprotectionturnedon.png":::

1. **Başlat'ı** seçin ve *Güvenlik* yazmaya başlayın. Arama sonuçlarında **Windows Güvenliği'ı** seçin.

2. **Virüs & tehdit koruması** \> **Virüs & tehdit koruması ayarlarını** seçin.

3. **Kurcalama Koruması'na** **Açık** veya **Kapalı** olarak ayarlayın.

## <a name="are-you-using-windows-server-2012-r2-2016-or-windows-version-1709-1803-or-1809"></a>Windows Server 2012 R2, 2016 veya Windows sürüm 1709, 1803 veya 1809 mu kullanıyorsunuz?

Windows Server 2012 R2'yi modern birleşik çözüm Windows Server 2016 Windows 10 sürüm 1709, 1803 veya [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) kullanarak kullanıyorsanız, Windows Güvenliği uygulamasında **Kurcalama Koruması'nı** görmezsiniz. Bunun yerine, kurcalama korumasının etkinleştirilip etkinleştirilmediğini belirlemek için PowerShell'i kullanabilirsiniz.

Windows Server 2016 Ayarlar uygulaması, kurcalama koruması etkinleştirildiğinde gerçek zamanlı korumanın durumunu doğru yansıtmaz.

#### <a name="use-powershell-to-determine-whether-tamper-protection-and-real-time-protection-are-turned-on"></a>Kurcalama korumasının ve gerçek zamanlı korumanın açık olup olmadığını belirlemek için PowerShell kullanma

1. Windows PowerShell uygulamasını açın.

2. [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus?preserve-view=true&view=win10-ps) PowerShell cmdlet'ini kullanın.

3. Sonuç listesinde veya `RealTimeProtectionEnabled`öğesini arayın`IsTamperProtected`. ( *True* değeri, kurcalama korumasının etkinleştirildiği anlamına gelir.)

## <a name="view-information-about-tampering-attempts"></a>Kurcalama girişimleri hakkındaki bilgileri görüntüleme

Kurcalama girişimleri genellikle daha büyük siber saldırılara işaret eder. Kötü aktörler, kalıcı hale getirmek ve algılanmamış kalmak için güvenlik ayarlarını değiştirmeye çalışır. Kuruluşunuzun güvenlik ekibinin bir parçasıysanız, bu tür girişimlerle ilgili bilgileri görüntüleyebilir ve ardından tehditleri azaltmak için uygun eylemleri gerçekleştirebilirsiniz.

Kurcalama girişimi algılandığında, [Microsoft 365 Defender portalında](/microsoft-365/security/defender-endpoint/portal-overview) ([https://security.microsoft.com](https://security.microsoft.com)) bir uyarı oluşturulur.

[Uç Nokta için Microsoft Defender'da uç noktada algılama ve yanıtlama](overview-endpoint-detection-response.md) ve [gelişmiş avcılık](advanced-hunting-overview.md) özelliklerini kullanarak güvenlik operasyonları ekibiniz bu tür girişimleri araştırabilir ve ele alabilir.

## <a name="review-your-security-recommendations"></a>Güvenlik önerilerinizi gözden geçirin

Kurcalama koruması [, Tehdit & Güvenlik Açığı Yönetimi](next-gen-threat-and-vuln-mgt.md) özellikleriyle tümleştirilir. [Kurcalama](tvm-security-recommendation.md) korumasının açık olduğundan emin olmak güvenlik önerileridir. Örneğin, *kurcalama* sırasında arama yapabilirsiniz. Sonuçlarda, Daha fazla bilgi edinmek ve açmak için **Kurcalama Koruması'nı** aç'ı seçebilirsiniz.

Tehdit & Güvenlik Açığı Yönetimi hakkında daha fazla bilgi edinmek için bkz. [Pano içgörüleri - Tehdit ve Güvenlik Açığı Yönetimi](tvm-dashboard-insights.md#dashboard-insights---threat-and-vulnerability-management).

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="on-which-versions-of-windows-can-i-configure-tamper-protection"></a>Windows hangi sürümlerinde kurcalama korumasını yapılandırabilirim?

- Windows 11
- Çoklu oturum Windows 11 Enterprise
- Uç Nokta için Microsoft Defender ile birlikte işletim sistemi [1709](/lifecycle/announcements/revised-end-of-service-windows-10-1709), [1803](/lifecycle/announcements/windows-server-1803-end-of-servicing), [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) veya [üzerini Windows 10](/microsoft-365/security/defender-endpoint).
- Çoklu oturum Windows 10 Enterprise
  
Kiracı eklemeli Configuration Manager, sürüm 2006 kullanıyorsanız, kurcalama koruması Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 ve Windows Server 2022'ye genişletilebilir. Bkz [. Kiracı ekleme: Yönetim merkezinden uç nokta güvenliği Virüsten koruma ilkesi oluşturma ve dağıtma (önizleme)](/mem/configmgr/tenant-attach/deploy-antivirus-policy).

### <a name="will-tamper-protection-affect-non-microsoft-antivirus-registration-in-the-windows-security-app"></a>Kurcalama koruması, Windows Güvenliği uygulamasında Microsoft dışı virüsten koruma kaydını etkiler mi?

Hayır. Microsoft dışı virüsten koruma teklifleri Windows Güvenliği uygulamasına kaydolmaya devam eder.

### <a name="what-happens-if-microsoft-defender-antivirus-is-not-active-on-a-device"></a>Microsoft Defender Virüsten Koruma bir cihazda etkin değilse ne olur?

Uç Nokta için Microsoft Defender eklenen cihazlarda pasif modda çalışan Microsoft Defender Virüsten Koruma olacaktır. Bu durumlarda, kurcalama koruması hizmeti ve özelliklerini korumaya devam eder.

### <a name="how-do-i-turn-tamper-protection-on-or-off"></a>Kurcalama korumasını açmak veya kapatmak Nasıl yaparım??

Ev kullanıcısıysanız, bkz. [Tek bir cihazda kurcalama korumasını yönetme](#manage-tamper-protection-on-an-individual-device).

[Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint) kullanan bir kuruluşsanız, diğer uç nokta koruma özelliklerini yönetme yönteminize benzer şekilde Intune'de kurcalama korumasını yönetebilirsiniz. Bu makalenin aşağıdaki bölümlerine bakın:

- [Microsoft Endpoint Manager kullanarak kurcalama korumasını yönetme](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)
- [Microsoft 365 Defender portalını kullanarak kurcalama korumasını yönetme](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)

### <a name="how-does-configuring-tamper-protection-in-intune-affect-how-i-manage-microsoft-defender-antivirus-with-group-policy"></a>Intune'de kurcalama korumasını yapılandırmak, grup ilkesi ile Microsoft Defender Virüsten Koruma yönetme şeklimi nasıl etkiler?

Şu anda kurcalama korumasını yapılandırmak ve yönetmek için Intune kullanıyorsanız, Intune kullanmaya devam etmelisiniz. 

Grup ilkesi kurcalama koruması için geçerli değildir. grup ilkesi kullanılarak Microsoft Defender Virüsten Koruma ayarlarında yapılan değişiklikler, kurcalama koruması açık olduğunda veya Intune ile kurcalama koruması yapılandırıldığında yoksayılır.

### <a name="if-we-use-microsoft-intune-to-configure-tamper-protection-does-it-apply-only-to-the-entire-organization"></a>Kurcalama korumasını yapılandırmak için Microsoft Intune kullanırsak, bu yalnızca kuruluşun tamamı için geçerli mi?

Intune ile kurcalama korumasını yapılandırma esnekliğine sahipsiniz. Kuruluşunuzun tamamını hedefleyebilir veya belirli cihazları ve kullanıcı gruplarını seçebilirsiniz.

### <a name="can-i-configure-tamper-protection-with-microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager ile kurcalama korumasını yapılandırabilir miyim?

Kiracı ekleme kullanıyorsanız Microsoft Endpoint Configuration Manager kullanabilirsiniz. Aşağıdaki kaynaklara bakın:

- [Configuration Manager, sürüm 2006 ile kuruluşunuz için kurcalama korumasını yönetme](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)
- [Teknik Community blogu: Configuration Manager Kiracı Ekleme istemcileri için Kurcalama Koruması Duyuruları](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

### <a name="i-have-the-windows-e3-enrollment-can-i-use-configuring-tamper-protection-in-intune"></a>Windows E3 kaydım var. Intune'de kurcalama korumasını yapılandırmayı kullanabilir miyim?

Şu anda, Intune'de kurcalama korumasını yapılandırmak yalnızca [Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint) sahip müşteriler tarafından kullanılabilir.

### <a name="im-an-enterprise-customer-can-local-admins-change-tamper-protection-on-their-devices"></a>Kurumsal bir müşteriyim. Yerel yöneticiler cihazlarında kurcalama korumasını değiştirebilir mi?

Hayır. Yerel yöneticiler kurcalama koruması ayarlarını değiştiremez veya değiştiremez.

### <a name="what-happens-if-my-device-is-onboarded-with-microsoft-defender-for-endpoint-and-then-goes-into-an-off-boarded-state"></a>Cihazım Uç Nokta için Microsoft Defender eklendiğinde ve ardından kapalı duruma geçerse ne olur?

Bir cihaz Uç Nokta için Microsoft Defender kapalıysa, yönetilmeyen cihazlar için varsayılan durum olan kurcalama koruması açılır.

### <a name="if-the-status-of-tamper-protection-changes-are-alerts-shown-in-the-microsoft-365-defender-portal"></a>Kurcalama korumasının durumu değişirse uyarılar Microsoft 365 Defender portalında gösteriliyor mu?

Evet. Uyarı, **Uyarılar** altında gösterilir [https://security.microsoft.com](https://security.microsoft.com).

Güvenlik operasyonları ekibiniz, aşağıdaki örnek gibi avcılık sorgularını da kullanabilir:

`AlertInfo|where Title == "Tamper Protection bypass"`

[Kurcalama girişimleri hakkındaki bilgileri görüntüleyin](#view-information-about-tampering-attempts).

> [!TIP]
> Diğer platformlar için Antivirüs ile ilgili bilgi arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Intune için Endpoint Protection ile Windows bilgisayarların güvenliğini sağlamaya yardımcı olun](/intune/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)
- [Uç Nokta için Microsoft Defender genel bakışını edinin](/microsoft-365/security/defender-endpoint)
- [Birlikte daha iyi: Microsoft Defender Virüsten Koruma ve Uç Nokta için Microsoft Defender](why-use-microsoft-defender-antivirus.md)
- [Sorun giderme modunu etkinleştirme](enable-troubleshooting-mode.md)
- [Sorun giderme modu senaryoları](troubleshooting-mode-scenarios.md)
