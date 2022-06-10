---
title: Saldırı yüzeyi azaltma kurallarını etkinleştirme
description: Cihazlarınızı makro, betik ve yaygın ekleme teknikleri kullanan saldırılara karşı korumak için saldırı yüzeyi azaltma (ASR) kurallarını etkinleştirin.
keywords: Saldırı yüzeyi azaltma, kalçalar, konak izinsiz giriş önleme sistemi, koruma kuralları, anti-exploit, antiexploit, exploit, enfeksiyon önleme, etkinleştirme, açma
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.date: 1/18/2022
ms.openlocfilehash: 31af082f66836ecfbe6a7cd804fd3b7bba2ed4bd
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012394"
---
# <a name="enable-attack-surface-reduction-rules"></a>Saldırı yüzeyi azaltma kurallarını etkinleştirme

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

> [!TIP]
> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Saldırı yüzeyi azaltma kuralları](attack-surface-reduction.md) (ASR kuralları), kötü amaçlı yazılımların cihazları ve ağları tehlikeye atmak için sıklıkla kötüye kullanılan eylemleri önlemeye yardımcı olur.

## <a name="requirements"></a>Gereksinimler

Windows sürümlerde saldırı yüzeyi azaltma özellikleri

aşağıdaki Windows sürümlerinden herhangi birini çalıştıran cihazlar için saldırı yüzeyi azaltma kuralları ayarlayabilirsiniz:

- [Windows 11 Pro](/windows/whats-new/windows-11-overview)
- [Windows 11 Enterprise](https://www.microsoft.com/microsoft-365/windows/windows-11-enterprise)
- Windows 10 Pro, [sürüm 1709](/windows/whats-new/whats-new-windows-10-version-1709) veya üzeri
- Windows 10 Enterprise, [sürüm 1709](/windows/whats-new/whats-new-windows-10-version-1709) veya üzeri
- Windows Sunucusu, [sürüm 1803 (Altı Aylık Kanal)](/windows-server/get-started/whats-new-in-windows-server-1803) veya üzeri
- [Windows Server 2012 R2](/windows/win32/srvnodes/what-s-new-for-windows-server-2012-r2)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2022](/windows-server/get-started/whats-new-in-windows-server-2022)

Saldırı yüzeyi azaltma kurallarının özellik kümesinin tamamını kullanmak için şunları yapmanız gerekir:

- birincil AV olarak Windows Defender Virüsten Koruma (gerçek zamanlı koruma açık)
- [Üzerinde Bulut Teslim Koruması](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) (bazı kurallar bunu gerektirir)
- E5 veya E3 Lisansını Windows 10 Enterprise

Saldırı yüzeyi azaltma kuralları [Windows E5 lisansı](/windows/deployment/deploy-enterprise-licenses) gerektirmese de, Windows E5 lisansıyla uç nokta için Defender'da sağlanan izleme, analiz ve iş akışları gibi gelişmiş yönetim özelliklerinin yanı sıra <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalında</a> raporlama ve yapılandırma özelliklerine sahip olursunuz. Bu gelişmiş özellikler E3 lisansıyla kullanılamaz, ancak saldırı yüzeyi azaltma kuralı olaylarını gözden geçirmek için Olay Görüntüleyicisi kullanabilirsiniz.

Her ASR kuralı dört ayardan birini içerir:

- **Yapılandırılmadı** |  **Devre dışı**: ASR kuralını devre dışı bırakma
- **Engelle**: ASR kuralını etkinleştirme
- **Denetim**: Etkinleştirildiğinde ASR kuralının kuruluşunuzu nasıl etkileyeceğini değerlendirme
- **Uyar**: ASR kuralını etkinleştirin ancak son kullanıcının bloğu atlamasına izin verin

Uç Nokta için Microsoft Defender 'de (Uç Nokta için Defender) sağlanan gelişmiş izleme ve raporlama özelliklerinden yararlanmak için ASR kurallarını [Windows](microsoft-defender-endpoint.md) E5 lisansıyla (veya benzer lisanslama SKU'su) kullanmanızı öneririz. Ancak, gelişmiş izleme ve raporlama özellikleri içermeyen Windows Professional veya Windows E3 gibi başka bir lisansınız varsa, ASR kuralları tetiklendiğinde her uç noktada oluşturulan olayların üzerine kendi izleme ve raporlama araçlarınızı geliştirebilirsiniz (örneğin, Olay İletme).

> [!TIP]
> Windows lisanslama hakkında daha fazla bilgi edinmek için bkz[. lisanslama Windows 10](https://www.microsoft.com/licensing/product-licensing/windows10?activetab=windows10-pivot:primaryr5) ve [Windows 10 için Toplu Lisanslama kılavuzunu](https://download.microsoft.com/download/2/D/1/2D14FE17-66C2-4D4C-AF73-E122930B60F6/Windows-10-Volume-Licensing-Guide.pdf) edinin.

Şu yöntemlerden herhangi birini kullanarak saldırı yüzeyi azaltma kurallarını etkinleştirebilirsiniz:

- [Microsoft Intune](#intune)
- [Mobil Cihaz Yönetimi (MDM)](#mdm)
- [Microsoft Uç Noktası Yapılandırma Yöneticisi](#microsoft-endpoint-configuration-manager)
- [Grup İlkesi](#group-policy)
- [PowerShell](#powershell)

Intune veya Microsoft Endpoint Manager gibi Enterprise düzeyinde yönetim önerilir. Enterprise düzeyinde yönetim, başlangıçta çakışan grup ilkesi veya PowerShell ayarlarının üzerine yazar.

## <a name="exclude-files-and-folders-from-asr-rules"></a>Dosyaları ve klasörleri ASR kurallarından dışlama

Çoğu saldırı yüzeyi azaltma kuralı tarafından değerlendirilen dosya ve klasörleri hariç tutabilirsiniz. Bu, bir ASR kuralı dosya veya klasörün kötü amaçlı davranış içerdiğini belirlese bile dosyanın çalışmasını engellemeyeceği anlamına gelir. Bu, güvenli olmayan dosyaların çalıştırılmasına ve cihazlarınıza bulaşmasına izin verebilir.

Ayrıca, belirtilen Uç Nokta için Defender dosya ve sertifika göstergelerine izin vererek ASR kurallarını sertifika ve dosya karmalarına göre tetiklemenin dışında tutabilirsiniz. (Bkz. [Göstergeleri yönetme](manage-indicators.md).)

> [!IMPORTANT]
> Dosya veya klasörlerin dışlanması ASR kuralları tarafından sağlanan korumayı ciddi ölçüde azaltabilir. Dışlanan dosyaların çalıştırılmasına izin verilir ve hiçbir rapor veya olay kaydedilmez.
> ASR kuralları algılanmaması gerektiğini inandığınız dosyaları algılarsa, [kuralı test etmek için önce denetim modunu kullanmanız](attack-surface-reduction-rules-deployment-test.md#step-1-test-asr-rules-using-audit) gerekir.

Tek tek dosyaları veya klasörleri (klasör yollarını veya tam kaynak adlarını kullanarak) belirtebilirsiniz, ancak dışlamaların hangi kurallara uygulanacağını belirtemezsiniz. Dışlama yalnızca dışlanan uygulama veya hizmet başlatıldığında uygulanır. Örneğin, zaten çalışmakta olan bir güncelleştirme hizmeti için bir dışlama eklerseniz, hizmet durdurulup yeniden başlatılana kadar güncelleştirme hizmeti olayları tetiklemeye devam eder.

ASR kuralları ortam değişkenlerini ve joker karakterleri destekler. Joker karakterleri kullanma hakkında bilgi için bkz. [Dosya adı ve klasör yolu veya uzantı dışlama listelerinde joker karakterler kullanma](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists).

## <a name="policy-conflict"></a>İlke Çakışması

1. MDM ve GP aracılığıyla çakışan bir ilke uygulanırsa, MDM'den uygulanan ayar öncelikli olur.

2. MEM tarafından yönetilen cihazlar için saldırı yüzeyi azaltma kuralları artık her cihaz için bir ilke üst kümesi oluşturmak üzere farklı ilkelerden ayarların birleştirilmesine yönelik davranışı destekliyor. Yalnızca çakışma olmayan ayarlar birleştirilirken, çakışan ayarlar kuralların üst kümesine eklenmez. Daha önce, iki ilkede tek bir ayar için çakışmalar varsa, her iki ilke de çakışıyor olarak işaretlenir ve her iki profilden hiçbir ayar dağıtılmazdı. Saldırı yüzeyi azaltma kuralı birleştirme davranışı aşağıdaki gibidir:
   - Aşağıdaki profillerden gelen saldırı yüzeyi azaltma kuralları, kuralların geçerli olduğu her cihaz için değerlendirilir:
     - Cihazlar > Yapılandırma ilkesi > Uç nokta koruma profili > **Microsoft Defender Exploit Guard** >  [Ayrı yüzey azaltma](/mem/intune/protect/endpoint-protection-windows-10#attack-surface-reduction-rules).
     - Uç nokta güvenliği > **Saldırı yüzeyi azaltma ilkesi** > [Saldırı yüzeyi azaltma kuralları](/mem/intune/protect/endpoint-security-asr-policy#devices-managed-by-intune).
     - Uç nokta güvenliği > **Microsoft Defender ATP Temel**[Saldırı Yüzeyi Azaltma Kuralları > Güvenlik temelleri](/mem/intune/protect/security-baseline-settings-defender-atp#attack-surface-reduction-rules) > .
   - Çakışması olmayan Ayarlar cihaz için bir ilke üst kümesine eklenir.
   - İki veya daha fazla ilke çakışan ayarlara sahip olduğunda, çakışan ayarlar birleştirilmiş ilkeye eklenmezken, çakışmayan ayarlar bir cihaz için geçerli olan üst küme ilkesine eklenir.
   - Yalnızca çakışan ayarlar için yapılandırmalar geri tutulur.

## <a name="configuration-methods"></a>Yapılandırma yöntemleri

Bu bölümde, aşağıdaki yapılandırma yöntemleri için yapılandırma ayrıntıları sağlanır:

- [Intune](#intune)
- [MEM](#mem)
- [MDM](#mdm)
- [Microsoft Uç Noktası Yapılandırma Yöneticisi](#microsoft-endpoint-configuration-manager)
- [Grup İlkesi](#group-policy)
- [PowerShell](#powershell)

ASR kurallarını etkinleştirmeye yönelik aşağıdaki yordamlar, dosya ve klasörleri dışlama yönergelerini içerir.

### <a name="intune"></a>Intune

#### <a name="device-configuration-profiles"></a>Cihaz Yapılandırma Profilleri

1. **Cihaz yapılandırma** \> **Profilleri'ni** seçin. Mevcut bir uç nokta koruma profili seçin veya yeni bir profil oluşturun. Yeni bir profil oluşturmak için **Profil oluştur'u** seçin ve bu profille ilgili bilgileri girin. **Profil türü** için **Uç nokta koruma'yı** seçin. Mevcut bir profili seçtiyseniz **Özellikler'i** ve ardından **Ayarlar'ı** seçin.

2. **Uç nokta koruma** bölmesinde **Exploit Guard Windows Defender** ve ardından **Saldırı Yüzeyi Azaltma'yı** seçin. Her ASR kuralı için istediğiniz ayarı seçin.

3. **Saldırı Yüzeyi Azaltma özel durumları'nın** altında tek tek dosya ve klasörleri girin. ASR kurallarının dışında tutulacak dosya ve klasörleri içeren bir CSV dosyasını içeri aktarmak için **İçeri Aktar'ı** da seçebilirsiniz. CSV dosyasındaki her satır aşağıdaki gibi biçimlendirilmelidir:

   `C:\folder`, `%ProgramFiles%\folder\file`, `C:\path`

4. Üç yapılandırma bölmesinde **Tamam'ı** seçin. Ardından yeni bir uç nokta koruma dosyası oluşturuyorsanız **Oluştur'u** veya mevcut bir dosyayı düzenliyorsanız **Kaydet'i** seçin.

#### <a name="endpoint-security-policy"></a>Uç nokta güvenlik ilkesi

1. **Endpoint Security** \> **Attack yüzey azaltma'ya** tıklayın. Var olan bir ASR kuralını seçin veya yeni bir kural oluşturun. Yeni bir profil oluşturmak için **İlke Oluştur'u** seçin ve bu profille ilgili bilgileri girin. **Profil türü için** **Saldırı yüzeyi azaltma kuralları'yı** seçin. Mevcut bir profili seçtiyseniz **Özellikler'i** ve ardından **Ayarlar'ı** seçin.

2. **Yapılandırma ayarları** bölmesinde **Saldırı Yüzeyi Azaltma'yı** seçin ve ardından her ASR kuralı için istenen ayarı seçin.

3. **Korunması gereken ek klasörlerin listesi**, **Korumalı klasörlere erişimi olan uygulamaların listesi** ve **Saldırı yüzeyi azaltma kurallarının dosya ve yollarını hariç tut** altında, tek tek dosya ve klasörler girin. ASR kurallarının dışında tutulacak dosya ve klasörleri içeren bir CSV dosyasını içeri aktarmak için **İçeri Aktar'ı** da seçebilirsiniz. CSV dosyasındaki her satır aşağıdaki gibi biçimlendirilmelidir:

   `C:\folder`, `%ProgramFiles%\folder\file`, `C:\path`

4. Üç yapılandırma bölmesinde **İleri'yi** ve ardından yeni bir ilke oluşturuyorsanız **Oluştur'u** veya mevcut bir ilkeyi düzenliyorsanız **Kaydet'i** seçin.

### <a name="mem"></a>MEM

Özel ASR kurallarını yapılandırmak için Microsoft Endpoint Manager (MEM) OMA-URI'sini kullanabilirsiniz. Aşağıdaki yordam, örnek için [kötüye kullanılan güvenlik açığı bulunan imzalı sürücülerin kötüye kullanımı engelleyin](attack-surface-reduction-rules-reference.md#block-abuse-of-exploited-vulnerable-signed-drivers) kuralını kullanır.

1. Microsoft Endpoint Manager (MEM) yönetim merkezini açın. **Giriş** menüsünde **Cihazlar'a** tıklayın, **Yapılandırma profilleri'ni** seçin ve profil **oluştur'a** tıklayın.

   > [!div class="mx-imgBorder"]
   >  :::image type="content" source="images/mem01-create-profile.png" alt-text="Microsoft Endpoint Manager yönetim merkezi portalındaki Profil oluştur sayfası" lightbox="images/mem01-create-profile.png":::

2. **Profil oluştur** bölümünde, aşağıdaki iki açılan listede aşağıdakileri seçin:

   - **Platform'da** **Windows 10 ve üzerini** seçin
   - **Profil türü'nde** **Şablonlar'ı** seçin
   - ASR kuralları zaten Uç nokta güvenliği aracılığıyla ayarlandıysa **, Profil türü'nde** **Katalog'Ayarlar** seçin.

   **Özel'i** ve ardından **Oluştur'u** seçin.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem02-profile-attributes.png" alt-text="Microsoft Endpoint Manager yönetim merkezi portalındaki kural profili öznitelikleri" lightbox="images/mem02-profile-attributes.png":::

3. Özel şablon aracı 1. Adım **Temel bilgiler'i** açar. **1 Temel Bilgiler'de****, Ad** alanına şablonunuz için bir ad yazın ve **Açıklama** alanına bir açıklama yazabilirsiniz (isteğe bağlı).

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem03-1-basics.png" alt-text="Microsoft Endpoint Manager yönetim merkezi portalındaki temel öznitelikler" lightbox="images/mem03-1-basics.png":::

4. **İleri**'ye tıklayın. **2. Adım Yapılandırma ayarları** açılır. OMA-URI Ayarlar için **Ekle'ye** tıklayın. Şimdi iki seçenek görüntülenir: **Ekle** ve **Dışarı Aktar**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem04-2-configuration-settings.png" alt-text="Microsoft Endpoint Manager yönetim merkezi portalındaki yapılandırma ayarları" lightbox="images/mem04-2-configuration-settings.png":::

5. **Yeniden Ekle'ye** tıklayın. **Satır Ekle OMA-URI Ayarlar** açılır. **Satır Ekle'de** aşağıdakileri yapın:

   - **Ad** alanına kural için bir ad yazın.
   - **Açıklama** alanına kısa bir açıklama yazın.
   - **OMA-URI'de**, eklediğiniz kural için belirli OMA-URI bağlantısını yazın veya yapıştırın. Bu örnek kuralda kullanılacak OMA-URI için bu makaledeki MDM bölümüne bakın. Saldırı yüzeyi azaltma kuralı [GUID'leri](attack-surface-reduction-rules-reference.md#per-rule-descriptions) için bkz. Saldırı yüzeyi azaltma kuralları.
   - **Veri türü'nde** **Dize'yi** seçin.
   - **Değer'de** GUID değerini, \= işareti ve State değerini boşluksuz (_GUID=StateValue_) yazın veya yapıştırın. Konum:

     - 0 : Devre dışı bırak (ASR kuralını devre dışı bırak)
     - 1 : Engelle (ASR kuralını etkinleştirme)
     - 2 : Denetim (ASR kuralının etkinleştirildiğinde kuruluşunuzu nasıl etkileyeceğini değerlendirin)
     - 6 : Uyar (ASR kuralını etkinleştirin ancak son kullanıcının bloğu atlamasına izin verin)

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem05-add-row-oma-uri.png" alt-text="Microsoft Endpoint Manager yönetim merkezi portalında OMA URI yapılandırması" lightbox="images/mem05-add-row-oma-uri.png":::

6. **Kaydet**'i seçin. **Satır ekle** kapatıyor. **Özel'de** **İleri'yi** seçin. **3. Adım Kapsam etiketlerinde** kapsam etiketleri isteğe bağlıdır. Şunlardan birini yapın:

   - **Kapsam etiketlerini seç'i** seçin, kapsam etiketini seçin (isteğe bağlı) ve ardından **İleri'yi** seçin.
   - İsterseniz **İleri'yi** de seçebilirsiniz

7. **4.** adımda, **Dahil Edilen Gruplar'da**, bu kuralın uygulanmasını istediğiniz gruplar için aşağıdaki seçeneklerden birini belirleyin:

   - **Grup ekleme**
   - **Tüm kullanıcıları ekleme**
   - **Tüm cihazları ekleme**

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem06-4-assignments.png" alt-text="Microsoft Endpoint Manager yönetim merkezi portalındaki atamalar" lightbox="images/mem06-4-assignments.png":::

8. **Dışlanan gruplar'da**, bu kuraldan dışlamak istediğiniz grupları seçin ve ardından **İleri'yi** seçin.

9. Aşağıdaki ayarlar için 5. adımda **Uygulanabilirlik Kuralları'nda** aşağıdakileri yapın:

   - **Kural'da**, **Varsa profil ata'yı** **veya**
   - **Özellik'te**, bu kuralın uygulanmasını istediğiniz özelliği seçin
   - **Değer** alanına uygun değeri veya değer aralığını girin

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem07-5-applicability-rules.png" alt-text="Microsoft Endpoint Manager yönetim merkezi portalındaki uygulanabilirlik kuralları" lightbox="images/mem07-5-applicability-rules.png":::

10. **İleri**'yi seçin. 6. Gözden **geçir ve oluştur** adımında, seçtiğiniz ve girdiğiniz ayarları ve bilgileri gözden geçirin ve **oluştur'u** seçin.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mem08-6-review-create.png" alt-text="Microsoft Endpoint Manager yönetim merkezi portalında Gözden geçir ve oluştur seçeneği" lightbox="images/mem08-6-review-create.png":::

    > [!NOTE]
    > Kurallar etkindir ve dakikalar içinde etkindir.

> [!NOTE]
> Çakışma işleme:
>
> Bir cihaza iki farklı ASR ilkesi atarsanız, çakışmanın işlenme yöntemi farklı durumlara atanan kurallardır, çakışma yönetimi yoktur ve sonuç bir hatadır.
>
> Çakışmayan kurallar hataya neden olmaz ve kural doğru şekilde uygulanır. Sonuç, ilk kuralın uygulanması ve sonraki çakışmayan kuralların ilkeyle birleştirilmesidir.

### <a name="mdm"></a>MDM

Her kuralın modunu ayrı ayrı etkinleştirmek ve ayarlamak için [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionRules](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductionrules) yapılandırma hizmeti sağlayıcısını (CSP) kullanın.

[Aşağıda, Saldırı yüzeyi azaltma kuralları başvurusu](attack-surface-reduction-rules-reference.md) için GUID değerlerinin kullanıldığı bir başvuru örneği verilmiştir.

`OMA-URI path: ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionRules`

`Value: 75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84=2|3b576869-a4ec-4529-8536-b80a7769e899=1|d4f940ab-401b-4efc-aadc-ad5f3c50688a=2|d3e037e1-3eb8-44c8-a917-57927947596d=1|5beb7efe-fd9a-4556-801d-275e5ffc04cc=0|be9ba2d9-53ea-4cdc-84e5-9b1eeee46550=1`

Denetim modunda etkinleştirme (Engelleme), devre dışı bırakma, uyarma veya etkinleştirme değerleri şunlardır:

- 0 : Devre dışı bırak (ASR kuralını devre dışı bırak)
- 1 : Engelle (ASR kuralını etkinleştirme)
- 2 : Denetim (ASR kuralının etkinleştirildiğinde kuruluşunuzu nasıl etkileyeceğini değerlendirin)
- 6 : Uyar (ASR kuralını etkinleştirin ancak son kullanıcının bloğu atlamasına izin verin). AsR kurallarının çoğu için uyarı modu kullanılabilir.

Dışlama eklemek için [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) yapılandırma hizmeti sağlayıcısını (CSP) kullanın.

Örneğin:

`OMA-URI path: ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions`

`Value: c:\path|e:\path|c:\Exclusions.exe`

> [!NOTE]
> OMA-URI değerlerini boşluk olmadan girdiğinizden emin olun.

### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Uç Noktası Yapılandırma Yöneticisi

1. Microsoft Endpoint Configuration Manager'da **Varlıklar ve Uyumluluk** \> **Uç Nokta Koruması** \> **Windows Defender Açıklardan Yararlanma Koruması**'na gidin.

2. **Giriş** \> **Açıklardan Yararlanma Koruması İlkesi Oluştur**'u seçin.

3. Bir ad ve açıklama girin, **Saldırı Yüzeyi Azaltma'yı** seçin ve **İleri'yi** seçin.

4. Hangi kuralların eylemleri engelleyip denetleyeceğini seçin ve **İleri'yi** seçin.

5. İlkeyi oluşturmak için ayarları gözden geçirin ve **İleri'yi** seçin.

6. İlke oluşturulduktan sonra **Kapat**'ı seçin.

### <a name="group-policy"></a>Grup İlkesi

> [!WARNING]
> Bilgisayarlarınızı ve cihazlarınızı Intune, Configuration Manager veya diğer kurumsal düzeydeki yönetim platformuyla yönetirseniz, yönetim yazılımı başlangıçta çakışan grup ilkesi ayarlarının üzerine yazar.

1. grup ilkesi yönetim bilgisayarınızda [grup ilkesi Yönetim Konsolu'nu](https://technet.microsoft.com/library/cc731212.aspx) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'yi** seçin.

2. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin ve **Yönetim şablonları'nı** seçin.

3. **Saldırı yüzeyini azaltma** Microsoft Defender Exploit Guard **Microsoft Defender Virüsten Koruma** \> **bileşenleri** \> **Windows** \> için ağacı genişletin.

4. **Saldırı yüzeyi azaltma kurallarını yapılandır'ı** ve **Etkin'i** seçin. Ardından seçenekler bölümünde her kural için tek tek durumu ayarlayabilirsiniz. **Göster...** öğesini seçin ve **Kural kimliğini Değer adı** sütununa ve seçtiğiniz durumu **Değer** sütununa aşağıdaki gibi girin:

   - 0 : Devre dışı bırak (ASR kuralını devre dışı bırak)
   - 1 : Engelle (ASR kuralını etkinleştirme)
   - 2 : Denetim (ASR kuralının etkinleştirildiğinde kuruluşunuzu nasıl etkileyeceğini değerlendirin)
   - 6 : Uyar (ASR kuralını etkinleştirin ancak son kullanıcının bloğu atlamasına izin verin)

   :::image type="content" source="images/asr-rules-gp.png" alt-text="grup ilkesi'da ASR kuralları" lightbox="images/asr-rules-gp.png":::

5. Dosyaları ve klasörleri ASR kurallarından dışlamak için **, Saldırı yüzeyi azaltma kurallarından dosya ve yolları dışla** ayarını seçin ve seçeneği **Etkin** olarak ayarlayın. **Göster'i** seçin ve **Değer adı** sütununa her dosyayı veya klasörü girin. Her öğe için **Değer** sütununa **0** girin.

   > [!WARNING]
   > **Değer adı** sütunu veya **Değer** sütunu için desteklenmediğinden tırnak işaretleri kullanmayın.

### <a name="powershell"></a>PowerShell

> [!WARNING]
> Bilgisayarlarınızı ve cihazlarınızı Intune, Configuration Manager veya başka bir kurumsal düzeyde yönetim platformuyla yönetirseniz, yönetim yazılımı başlangıçta çakışan PowerShell ayarlarının üzerine yazar. Kullanıcıların PowerShell kullanarak değeri tanımlamasına izin vermek için yönetim platformundaki kural için "Kullanıcı Tanımlı" seçeneğini kullanın.
> "Kullanıcı Tanımlı", yerel yönetici kullanıcının kuralı yapılandırmasına olanak tanır.
> Kullanıcı Tanımlı seçenek ayarı aşağıdaki şekilde gösterilmiştir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-user-defined.png" alt-text="Kimlik bilgisi güvenliği için Etkinleştir seçeneği" lightbox="images/asr-user-defined.png":::

1. Başlat menüsü **powershell** yazın, **Windows PowerShell** sağ tıklayın ve **Yönetici olarak çalıştır'ı** seçin.

2. Aşağıdaki cmdlet'lerden birini yazın. (Kural kimliği gibi diğer ayrıntılar için [Saldırı yüzeyi azaltma kuralları başvurusuna](attack-surface-reduction-rules-reference.md) bakın.)

    ```PowerShell
    Set-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Enabled
    ```

    DENETIM modunda ASR kurallarını etkinleştirmek için aşağıdaki cmdlet'i kullanın:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
    ```

    ASR kurallarını uyarı modunda etkinleştirmek için aşağıdaki cmdlet'i kullanın:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Warn
    ```

    Açıktan yararlanılan güvenlik açığı olan imzalı sürücülerin ASR Bloğu kötüye kullanımını etkinleştirmek için aşağıdaki cmdlet'i kullanın:

   ```PowerShell
   Add-MpPreference -AttackSurfaceReductionRules_Ids 56a863a9-875e-4185-98a7-b882c64b5ce5 -AttackSurfaceReductionRules_Actions Enabled
   ```

    ASR kurallarını kapatmak için aşağıdaki cmdlet'i kullanın:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Disabled
    ```

    > [!IMPORTANT]
    > Her kural için durumu ayrı ayrı belirtmeniz gerekir, ancak kuralları ve durumları virgülle ayrılmış bir listede birleştirebilirsiniz.
    >
    > Aşağıdaki örnekte, ilk iki kural etkinleştirilir, üçüncü kural devre dışı bırakılır ve dördüncü kural denetim modunda etkinleştirilir:
    >
    > ```PowerShell
    > Set-MpPreference -AttackSurfaceReductionRules_Ids <rule ID 1>,<rule ID 2>,<rule ID 3>,<rule ID 4> -AttackSurfaceReductionRules_Actions Enabled, Enabled, Disabled, AuditMode
    > ```

    Var olan listeye yeni kurallar eklemek için PowerShell fiilini de kullanabilirsiniz `Add-MpPreference` .

    > [!WARNING]
    > `Set-MpPreference` her zaman mevcut kural kümesinin üzerine yazar. Mevcut kümeye eklemek istiyorsanız, bunun yerine kullanın `Add-MpPreference` .
    > kullanarak `Get-MpPreference`kuralların listesini ve geçerli durumlarını alabilirsiniz.

3. Dosyaları ve klasörleri ASR kurallarının dışında tutmak için aşağıdaki cmdlet'i kullanın:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

    Listeye daha fazla dosya ve klasör eklemek için kullanmaya `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` devam edin.

    > [!IMPORTANT]
    > Listeye uygulama eklemek veya eklemek için kullanın `Add-MpPreference` . cmdlet'ini `Set-MpPreference` kullanmak varolan listenin üzerine yazılır.

## <a name="related-articles"></a>İlgili makaleler

- [Saldırı yüzeyi azaltma kuralları başvurusu](attack-surface-reduction-rules-reference.md)
- [Saldırı yüzeyini azaltmayı değerlendirme](evaluate-attack-surface-reduction.md)
- [Saldırı yüzeyini azaltma ile ilgili SSS](attack-surface-reduction.md)
