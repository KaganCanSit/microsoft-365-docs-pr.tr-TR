---
title: Saldırı yüzeyini azaltma kurallarını etkinleştirin
description: Cihazlarınızı makroları, betikleri ve yaygın ekleme tekniklerini kullanan saldırılardan korumak için saldırı yüzeyini azaltma (ASR) kurallarını etkinleştirin.
keywords: Saldırı yüzeyini azaltma, hip'ler, izinsiz giriş önleme sistemi, koruma kuralları, istismardan koruma, izinsiz giriş önleme, açıktan koruma, bulaşma önleme, etkinleştirme, açma
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
ms.openlocfilehash: 929ecd109d110c9a4578b39fbc69ed65c0b7d116
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682625"
---
# <a name="enable-attack-surface-reduction-rules"></a>Saldırı yüzeyini azaltma kurallarını etkinleştirin

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Saldırı yüzeyini azaltma kuralları](attack-surface-reduction.md) (ASR kuralları), cihazları ve ağları tehlikeye atarak kötü amaçlı yazılımlar tarafından sıklıkla kötüye kullanımlara neden olan eylemleri önlemeye yardımcı olur.

## <a name="requirements"></a>Gereksinimler

Farklı sürümlerde saldırı yüzeyini azaltma Windows özellikleri

Şu sürümlerden herhangi birini çalıştıran cihazlar için saldırı yüzeyini azaltma kuralları Windows:

- Windows 10 Pro, [sürüm 1709](/windows/whats-new/whats-new-windows-10-version-1709) veya sonrası
- Windows 10 Enterprise, [sürüm 1709](/windows/whats-new/whats-new-windows-10-version-1709) veya sonrası
- Windows, [sürüm 1803 (Yarı Yıllık Kanal) veya](/windows-server/get-started/whats-new-in-windows-server-1803) sonraki sürümler
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2012 R2](/windows/win32/srvnodes/what-s-new-for-windows-server-2012-r2)
- Windows Server 2022

Tüm özellik kümesi saldırı yüzeyini azaltma kurallarını kullanmak için gerekenler:

- Windows Defender Virüsten Koruma AV olarak çalışma (gerçek zamanlı koruma açık)
- [Bulut Teslim Koruması açık](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) (bazı kurallar için bu gerekli olabilir)
- Windows 10 Enterprise E5 veya E3 Lisansı

Saldırı yüzeyini azaltma kuralları [Windows E5](/windows/deployment/deploy-enterprise-licenses) lisansı gerektirmese de, Windows E5 lisansına sahip olarak, Uç Nokta için Defender'da izleme, analiz ve iş akışları gibi gelişmiş yönetim özellikleriyle birlikte <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalında</a> raporlama ve yapılandırma özelliklerini elde edersiniz. Bu gelişmiş özellikler E3 lisansıyla kullanılamaz ancak saldırı yüzeyini azaltma kuralı olaylarını gözden geçirmek için Etkinlik Görüntüleyicisi'ni kullanmaya devam edersiniz.

Her ASR kuralı dört ayardan birini içerir:

- **Yapılandırılmadı** |  **Devre Dışı**: ASR kuralını devre dışı bırakma
- **Engelle**: ASR kuralını etkinleştirme
- **Denetim**: Etkinleştirildiğinde ASR kuralının organizasyonlarınızı nasıl etkiley olacağını değerlendirme
- **Uyar**: ASR kuralını etkinleştirin ancak son kullanıcının engellemeyi at olmasına izin verme

> [!IMPORTANT]
> Şu anda, Microsoft Endpoint Manager'de (MEM) ASR kurallarını yapılandırarak, uyarı modu Microsoft Endpoint Manager desteklenmiyor. Daha fazla bilgi edinmek için [bkz. Uyarı modunun destek destekleme destekleme olduğu durumlar](attack-surface-reduction.md#cases-where-warn-mode-is-not-supported).

Uç Nokta için [Microsoft Defender'da](microsoft-defender-endpoint.md) (Uç Nokta için Defender) bulunan gelişmiş izleme ve raporlama yetenekleriden yararlanmak için, bir Windows E5 lisansıyla (veya benzer lisans SKU'ları) ASR kuralları kullanılması önerilir. Öte yandan, gelişmiş izleme ve raporlama özelliklerini içermemiş Windows Professional veya Windows E3 gibi başka bir lisansınız varsa, ASR kuralları tetiklendiğinde her uç noktada oluşturulan olayların üzerine kendi izleme ve raporlama araçlarınızı geliştirebilirsiniz (örneğin, Olay İ iletme).

> [!TIP]
> Lisanslama hakkında daha fazla Windows için [Lisanslama](https://www.microsoft.com/licensing/product-licensing/windows10?activetab=windows10-pivot:primaryr5) Windows 10'ne bakın ve Lisanslama Hakkında [Toplu Lisanslama Windows 10](https://download.microsoft.com/download/2/D/1/2D14FE17-66C2-4D4C-AF73-E122930B60F6/Windows-10-Volume-Licensing-Guide.pdf).

Şu yöntemlerden herhangi birini kullanarak saldırı yüzeyini azaltma kurallarını etkinleştirebilirsiniz:

- [Microsoft Intune](#intune)
- [Mobil Cihaz Yönetimi (MDM)](#mdm)
- [Microsoft Uç Noktası Yapılandırma Yöneticisi](#microsoft-endpoint-configuration-manager)
- [Grup İlkesi](#group-policy)
- [PowerShell](#powershell)

Enterprise intune veya posta Microsoft Endpoint Manager düzey yönetimi önerilir. Enterprise yönetimi, başlangıçta çakışan Tüm Grup İlkesi veya PowerShell ayarlarının üzerine yazacak.

## <a name="exclude-files-and-folders-from-asr-rules"></a>Dosya ve klasörleri ASR kurallarından çıkar

Saldırı yüzeyini azaltma kurallarının çoğu tarafından dosya ve klasörlerin değerlendirilmesini çıkarabilirsiniz. Başka bir ifadeyle, ASR kuralı dosya veya klasörün kötü amaçlı davranışlar içerdiğini belirlerse bile dosyanın çalışmalarını engellemez. Bu, güvenli olmayabilecek dosyaların cihazlarınızı çalıştırmasına ve bulaşarak bulaşarak devamını vermesine olanak tanır.

Ayrıca, belirtilen Uç nokta dosyası ve sertifika göstergeleri için Defender'a izin vererek, sertifika ve dosya karmalarına dayalı olarak ASR kurallarını tetikleyemlerini dış tutabilirsiniz. (Bkz [. Göstergeleri yönetme](manage-indicators.md).)

> [!IMPORTANT]
> Dosya veya klasörlerin dışlama, ASR kuralları tarafından sağlanan korumayı ciddi ölçüde azaltır. Dışarıda bırakılan dosyaların çalışmasına izin verilir ve hiçbir rapor veya etkinlik kaydedlanmaz.
> ASR kuralları algı olmaması gerektiğini bildiğiniz dosyaları algılarsa, kuralı test etmek için [önce denetim modunu kullansanız gerekir](evaluate-attack-surface-reduction.md).

Tek tek dosyaları veya klasörleri (klasör yollarını veya tam kaynak adlarını kullanarak) belirtebilirsiniz, ancak dışlamaların geçerli olduğu kuralları belirtemezseniz. Dışlama, yalnızca dışlanan uygulama veya hizmet başlatıldığında uygulanır. Örneğin, zaten çalışan bir güncelleştirme hizmeti için dışlama eklersiniz, hizmet durdurulana ve yeniden başlatana kadar güncelleştirme hizmeti olayları tetiklemeye devam eder.

ASR kuralları, ortam değişkenlerini ve joker karakterleri destekler. Joker karakter kullanma hakkında bilgi için bkz. Dosya adı ve klasör yolu veya uzantı [dışlama listelerinde joker karakter kullanma](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists).

## <a name="policy-conflict"></a>İlke Çakışması

1. Çakışan bir ilke MDM ve GP aracılığıyla uygulanırsa, MDM'den uygulanan ayar öncelikli olur.

2. MEM tarafından yönetilen cihazlar için saldırı yüzeyini azaltma kuralları artık ayarların farklı ilkelerden birleşmesine yönelik davranışı desteklemektedir ve her cihaz için bir ilke kümesi oluşturabilir. Yalnızca çakışması olan ayarlar birleştirilirken, çakışan ayarlar üst kural kümesine eklenmez. Daha önce, iki ilke tek bir ayarda çakışmalar varsa, her iki ilke de çakışmış olarak işaretlendi ve iki profilden herhangi bir ayar dağıtılamdı. Saldırı yüzeyini azaltma kuralı birleştirme davranışı aşağıdaki gibidir:
   - Kuralların geçerli olduğu her cihaz için aşağıdaki profillerden saldırı yüzeyini azaltma kuralları değerlendirilir:
     - Cihazlar > İlke ve Uç > Koruma profili için Yapılandırma ilkesi > **Microsoft Defender Exploit Guard** >  [Tack Surface Azaltma kullanır](/mem/intune/protect/endpoint-protection-windows-10#attack-surface-reduction-rules).
     - Uç nokta güvenliği > **Saldırı yüzeyini azaltma ilkesiEkli** >  [yüzey azaltma kuralları](/mem/intune/protect/endpoint-security-asr-policy#devices-managed-by-intune).
     - Uç nokta > **Microsoft Defender > AtP BaselineAttack** >  [Surface Azaltma Kuralları için güvenlik taban çizgisi.](/mem/intune/protect/security-baseline-settings-defender-atp#attack-surface-reduction-rules)
   - Ayarlar çakışması olan ekipler, cihaz için bir üst ilke kümesine eklenir.
   - İki veya daha fazla ilkenin çakışan ayarları olduğunda, çakışan ayarlar birleştirilmiş ilkeye eklenmez ve çakışmaz ayarlar cihaz için geçerli olan üst küme ilkesine eklenir.
   - Yalnızca çakışan ayarların yapılandırmaları geri çıkar.

## <a name="configuration-methods"></a>Yapılandırma yöntemleri

Bu bölümde aşağıdaki yapılandırma yöntemleri için yapılandırma ayrıntıları ve bilgileri yer almaktadır:

- [Intune](#intune)
- [MEM](#mem)
- [MDM](#mdm)
- [Microsoft Uç Noktası Yapılandırma Yöneticisi](#microsoft-endpoint-configuration-manager)
- [Grup İlkesi](#group-policy)
- [PowerShell](#powershell)

ASR kurallarını etkinleştirmeye ilişkin aşağıdaki yordamlar, dosyaları ve klasörleri dışarıda tutmak için yönergeler içerir.

### <a name="intune"></a>Intune

#### <a name="device-configuration-profiles"></a>Cihaz Yapılandırma Profilleri

1. Cihaz **yapılandırma Profilleri'ne** \> **tıklayın**. Mevcut uç nokta koruma profilini seçin veya yeni bir profil oluşturun. Yeni profil oluşturmak için Profil **oluştur'a** tıklayın ve bu profille ilgili bilgileri girin. Profil **türü olarak Uç** nokta **koruması'ı seçin**. Mevcut bir profili seçtiysiniz, Özellikler'i **ve sonra Profil'i** **Ayarlar**.

2. Uç nokta **koruma bölmesinde Koruma** korumasını seçin **Windows Defender Ve ardından** Saldırı Yüzeyini **Azaltma'ya tıklayın**. Her ASR kuralı için istediğiniz ayarı seçin.

3. Saldırı **Yüzeyini Azaltma özel durumları'nın** altında tek tek dosyaları ve klasörleri girin. AsR kuralları dışında **tutulacak** dosyalar ve klasörler içeren bir CSV dosyasını içeri aktarmayı da seçmek için İçeri Aktar'ı da seçin. CSV dosyasındaki her satır aşağıdaki gibi biçimlendirilmiş olmalıdır:

   `C:\folder`, `%ProgramFiles%\folder\file`, `C:\path`

4. Üç **yapılandırma** bölmesinde Tamam'ı seçin. Ardından, **yeni** bir uç nokta koruma dosyası oluşturuyorsanız Oluştur'a veya **var olan bir** dosyayı düzenliyorsanız Kaydet'e tıklayın.

#### <a name="endpoint-security-policy"></a>Uç nokta güvenlik ilkesi**

1. Uç **Nokta Güvenliği Saldırı** \> **yüzeyini azaltma'yi seçin**. Mevcut ASR kuralını seçin veya yeni bir kural oluşturun. Yeni ilke oluşturmak için İlke **Oluştur'a** tıklayın ve bu profille ilgili bilgileri girin. Profil **türü olarak Saldırı** yüzeyini **azaltma kuralları'ı seçin**. Mevcut bir profili seçtiysiniz, Özellikler'i **ve sonra Profil'i** **Ayarlar**.

2. Yapılandırma ayarları **bölmesinde Saldırı** Yüzeyini **Azaltma'ya tıklayın** ve ardından her ASR kuralı için istediğiniz ayarı seçin.

3. Korunması **gereken ek klasörlerin** **listesi, Korumalı** klasörlere erişimi olan uygulamaların listesi ve Saldırı alanı azaltma kurallarındaki dosyaları ve yolları dışla'nın **altında tek tek** dosyaları ve klasörleri girin. AsR kuralları dışında **tutulacak** dosyalar ve klasörler içeren bir CSV dosyasını içeri aktarmayı da seçmek için İçeri Aktar'ı da seçin. CSV dosyasındaki her satır aşağıdaki gibi biçimlendirilmiş olmalıdır:

   `C:\folder`, `%ProgramFiles%\folder\file`, `C:\path`

4. Üç **yapılandırma** bölmesinde Sonraki'yi seçin, ardından yeni **bir ilke oluşturuyorsanız** Oluştur'a veya var olan bir  ilkeyi düzenliyorsanız Kaydet'e tıklayın.

### <a name="mem"></a>MEM

Özel ASR Microsoft Endpoint Manager yapılandırmak için OMA-URI (MEM) OMA-URI'yi kullanabilirsiniz. Aşağıdaki yordamda, bu örnekte [açıklardan yararlanan açıklardan yararlanan imzalı sürücülerin kötüye kullanımına](attack-surface-reduction-rules-reference.md#block-abuse-of-exploited-vulnerable-signed-drivers) izin ve kullanımı engelle kuralı lanmıştır.

1. MICROSOFT ENDPOINT MANAGER (MEM) yönetim merkezini açın. Giriş menüsünde **Cihazlar'a** tıklayın,  **Yapılandırma** **profilleri'ne tıklayın** ve ardından Profil oluştur'a **tıklayın**.

   > [!div class="mx-imgBorder"]
   > ![MEM Profil Oluştur.](images/mem01-create-profile.png)

2. Profil **oluştur'da**, aşağıdaki iki açılan listede, şunları seçin:

   - **Platformda,** Sonraki **Windows 10 seçin**
   - Profil **türü olarak** **Şablonlar'ı seçin**
   - ASR kuralları zaten Uç nokta güvenliği üzerinden ayarlanmışsa, **Profil türü'ne Göre Ayarlar** **seçin**.

   **Özel'i** ve ardından Oluştur'a **seçin**.

   > [!div class="mx-imgBorder"]
   > ![MEM kuralı profil öznitelikleri.](images/mem02-profile-attributes.png)

3. Özel şablon aracı **1. adıma açılır**. **1 Temel Bilgi'de**, **Ad** kutusuna şablonunuz için bir ad yazın ve Açıklama'ya  bir açıklama (isteğe bağlı) yazın.

   > [!div class="mx-imgBorder"]
   > ![MEM temel öznitelikleri.](images/mem03-1-basics.png)

4. **İleri**'ye tıklayın. **2. Adım Yapılandırma ayarları** açılır. OMA URI'leri Ayarlar Ekle'ye **tıklayın**. şimdi iki seçenek görüntülenir: **Ekle ve** Dışarı **Aktar**.

   > [!div class="mx-imgBorder"]
   > ![MEM Yapılandırması ayarları.](images/mem04-2-configuration-settings.png)

5. Yeniden **Ekle'ye** tıklayın. Satır **OMA-URI Ekle Ayarlar** açılır. Satır **Ekle'de** şunları yapın:

   - Ad **kutusuna** kural için bir ad yazın.
   - Açıklama **kutusuna** kısa bir açıklama yazın.
   - **OMA-URI'de**, eklemektesiniz kuralın belirli OMA-URI bağlantısını yazın veya yapıştırın. Bu örnek kuralda OMA-URI için bu makaledeki MDM bölümüne bakın. Saldırı yüzeyini azaltma kuralı GUID'leri için Kural başına [açıklamaları](attack-surface-reduction-rules-reference.md#per-rule-descriptions) için şu konuda bakın: Saldırı yüzeyini azaltma kuralları.
   - Veri **türü'ne** **Dize'yi seçin**.
   - **Değer'de**, GUID değerini, \= işareti ve Boşluklar yok durum değerini (_GUID=Durum_ Değeri) yazın veya yapıştırın. Burada:

     - 0 : Devre dışı bırakma (ASR kuralını devre dışı bırakma)
     - 1 : Engelle (ASR kuralını etkinleştirme)
     - 2 : Denetim (ETKINLEŞTIRILIRSE ASR kuralının organizasyonu nasıl etkiley olacağını değerlendirin)
     - 6 : Uyarı (ASR kuralını etkinleştirin ancak son kullanıcının engellemeyi at olmasına izin verme)

   > [!div class="mx-imgBorder"]
   > ![MEM OMA URI yapılandırması.](images/mem05-add-row-oma-uri.png)

6. **Kaydet**'i seçin. **Satır Ekle** kapanır. **Özel'de** Sonraki'yi **seçin**. 3. **adımda Kapsam etiketleri** isteğe bağlıdır. Şunlardan birini yapın:

   - Kapsam **Etiketlerini Seç'i** seçin, kapsam etiketini seçin (isteğe bağlı) ve sonra da Sonraki'yi **seçin**.
   - Veya Sonraki'yi **seçin**

7. **4. Adım Ödevler'de****,** Dahil Edilen Gruplar'da, bu kuralın uygulamalarını istediğiniz gruplar için aşağıdaki seçeneklerden birini belirleyin:

   - **Grup ekleme**
   - **Tüm kullanıcıları ekleme**
   - **Tüm cihazları ekle**

   > [!div class="mx-imgBorder"]
   > ![MEM ödevleri.](images/mem06-4-assignments.png)

8. **Dışlanan gruplar'da**, bu kuralın dışında tutmak istediğiniz grupları seçin ve sonra da Sonraki'yi **seçin**.

9. **5. adımda Aşağıdaki ayarlar** için Uygulanabilirlik Kuralları'nın adımlarında şunları yapın:

   - **Kural'da** Profil **ata veya** Eğer profil atama 
   - **Özellik'te**, bu kuralın uygulamalarını istediğiniz özelliği seçin
   - Değer **alanına**, geçerli değeri veya değer aralığını girin

   > [!div class="mx-imgBorder"]
   > ![MEM Uygulanabilirlik kuralları.](images/mem07-5-applicability-rules.png)

10. **İleri**'yi seçin. 6. **adımda Gözden Geçir + oluştur** adımını, seçtiğiniz ve girdiğiniz ayarları ve bilgileri gözden geçirerek Oluştur'a **tıklayın**.

    > [!div class="mx-imgBorder"]
    > ![MEM Gözden Geçir ve oluştur.](images/mem08-6-review-create.png)

    > [!NOTE]
    > Kurallar dakikalar içinde etkindir ve canlıdır.

> [!NOTE]
> Çakışmayı işleme:
>
> Cihaza iki farklı ASR ilkeleri atarsanız, çakışmanın iş çalışma yolu farklı durumlara atanan kurallardır; bir çakışma yönetimi yoktur ve sonuç hata olur.
>
> Çakışmayan kurallar hataya neden olmaz ve kural doğru şekilde uygulanır. Sonuç olarak, ilk kural uygulanır ve izleyen çakışmayan kurallar ilkeyle birleştirilir.

### <a name="mdm"></a>MDM

Her kural için modu tek tek etkinleştirmek ve ayarlamak için [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionRules](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductionrules) yapılandırma hizmet sağlayıcısını (CSP) kullanın.

Aşağıda, Saldırı yüzeyini azaltma kuralları başvurusu için GUID değerleri kullanılarak başvuru için [bir örnek veılmıştır](attack-surface-reduction-rules-reference.md).

`OMA-URI path: ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionRules`

`Value: 75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84=2|3b576869-a4ec-4529-8536-b80a7769e899=1|d4f940ab-401b-4efc-aadc-ad5f3c50688a=2|d3e037e1-3eb8-44c8-a917-57927947596d=1|5beb7efe-fd9a-4556-801d-275e5ffc04cc=0|be9ba2d9-53ea-4cdc-84e5-9b1eeee46550=1`

Denetim modunda etkinleştirme (Engelle), devre dışı bırak, uyar veya etkinleştir değerleri:

- 0 : Devre dışı bırakma (ASR kuralını devre dışı bırakma)
- 1 : Engelle (ASR kuralını etkinleştirme)
- 2 : Denetim (ETKINLEŞTIRILIRSE ASR kuralının organizasyonu nasıl etkiley olacağını değerlendirin)
- 6 : Uyarı (ASR kuralını etkinleştirin ancak son kullanıcının engellemeyi at olmasına izin verme). ASR kurallarının çoğunda Uyarı modu kullanılabilir.

Dışlama [eklemek için ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) yapılandırma servis sağlayıcısını (CSP) kullanın.

Örneğin:

`OMA-URI path: ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions`

`Value: c:\path|e:\path|c:\Exclusions.exe`

> [!NOTE]
> Boşluksuz OMA-URI değerlerini girmeye emin olun.

### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Uç Noktası Yapılandırma Yöneticisi

1. Daha Microsoft Endpoint Configuration Manager, Varlıklar ve **Uyumluluk Uyumluluğu güvenlik Endpoint Protection** \>  \> **Windows Defender Exploit Guard'a gidin**.

2.  \> Home **Create Exploit Guard Policy öğesini seçin**.

3. Bir ad ve açıklama girin, Saldırı Yüzeyini **Azaltma'ya ve** sonra Sonraki'yi **seçin**.

4. Hangi kuralların eylemleri engelley genel veya denetimle gerçekleştireceklerini seçin ve sonra da Sonraki'yi **seçin**.

5. Ayarları gözden geçirerek **Sonraki'yi** seçerek ilkeyi oluşturun.

6. İlke oluşturulduktan sonra Kapat'ı **seçin**.

### <a name="group-policy"></a>Grup İlkesi

> [!WARNING]
> Bilgisayarlarınızı ve cihazlarınızı Intune, Configuration Manager veya başka bir kurumsal düzey yönetim platformuyla yönetirseniz, yönetim yazılımı başlangıçta çakışan Grup İlkesi ayarlarının üzerine yazacak.

1. Grup İlkesi yönetim bilgisayarınızda Grup İlkesi Yönetim [Konsolu'nu](https://technet.microsoft.com/library/cc731212.aspx) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'yi **seçin**.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde** Bilgisayar **yapılandırması'ne gidin ve** Yönetim **şablonları'ı seçin**.

3. Saldırı yüzeyini **azaltmayı Windows bileşenleri Microsoft Defender Virüsten Koruma** \> **Microsoft Defender Exploit Guard** \>  \> **ağacı genişletin**.

4. Saldırı **yüzeyini azaltma kurallarını yapılandır'ı ve sonra** Etkin'i **seçin**. Bundan sonra, seçenekler bölümündeki her kural için ayrı durum ayarlayın. Göster **...'** i seçin ve Değer adı sütununa kural **kimliğini** ve Değer sütununa da seçtiğiniz **durumu aşağıdaki** gibi girin:

   - 0 : Devre dışı bırakma (ASR kuralını devre dışı bırakma)
   - 1 : Engelle (ASR kuralını etkinleştirme)
   - 2 : Denetim (ETKINLEŞTIRILIRSE ASR kuralının organizasyonu nasıl etkiley olacağını değerlendirin)
   - 6 : Uyarı (ASR kuralını etkinleştirin ancak son kullanıcının engellemeyi at olmasına izin verme)

   :::image type="content" source="images/asr-rules-gp.png" alt-text="Grup İlkesi'de ASR kuralları.":::

5. Dosyaları ve klasörleri ASR kurallarından dışlamak için Saldırı yüzeyi azaltma  kuralları ayarının dışında tutmak istediğiniz dosyaları ve yolları dışla ayarını seçin ve seçeneği Etkin olarak **ayarlayın**. **Göster'i** seçin ve Değer adı sütununa her **dosya veya klasörü** girin. Her **öğe için** Değer **sütununa** 0 girin.

   > [!WARNING]
   > Değer adı sütunu veya Değer sütunu için destek **sağlanmazken tırnak** içine **alın** .

### <a name="powershell"></a>PowerShell

> [!WARNING]
> Bilgisayarlarınızı ve cihazlarınızı Intune, Configuration Manager veya başka bir kurumsal düzey yönetim platformuyla yönetirsanız, yönetim yazılımı başlangıçta çakışan Tüm PowerShell ayarlarının üzerine yazmaz. Kullanıcıların PowerShell kullanarak değeri tanımlamasına izin vermek için, yönetim platformunda kural için "Kullanıcı Tanımlı" seçeneğini kullanın.
> "Kullanıcı Tanımlı", yerel yönetici kullanıcısını kuralı yapılandırmaya olanak sağlar.
> Kullanıcı Tanımlı seçenek ayarı aşağıdaki şekilde gösterilmektedir.

> [!div class="mx-imgBorder"]
> ![ASR "Kullanıcı Tanımlı" ayarını etkinleştirme](images/asr-user-defined.png)

1. **PowerShell yazın ve** Başlat menüsü sağ tıklayın ve **Windows PowerShell Yönetici olarak** **çalıştır'ı seçin**.

2. Aşağıdaki cmdlet'lerden birini yazın. (Kural kimliği [gibi daha fazla ayrıntı için](attack-surface-reduction-rules-reference.md) Saldırı yüzeyini azaltma kuralları başvurusu'ne bakın.)

    ```PowerShell
    Set-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Enabled
    ```

    Denetim modunda ASR kurallarını etkinleştirmek için aşağıdaki cmdlet'i kullanın:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
    ```

    Uyarı modunda ASR kurallarını etkinleştirmek için aşağıdaki cmdlet'i kullanın:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Warn
    ```

    AsR'nin açıklardan yararlanan imzalı sürücüler için kötüye kullanımı engellemeyi etkinleştirmek için aşağıdaki cmdlet'i kullanın:

   ```PowerShell
   Add-MpPreference -AttackSurfaceReductionRules_Ids 56a863a9-875e-4185-98a7-b882c64b5ce5 -AttackSurfaceReductionRules_Actions Enabled
   ```

    ASR kurallarını kapatmak için aşağıdaki cmdlet'i kullanın:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Disabled
    ```

    > [!IMPORTANT]
    > Her kural için eyaleti ayrı ayrı belirtmeniz gerekir, ancak kuralları ve durumları virgülle ayrılmış bir listede birleştirebilirsiniz.
    >
    > Aşağıdaki örnekte, ilk iki kural etkinleştirilir, üçüncü kural devre dışı bırakılır ve dördüncü kural denetim modunda etkinleştirilir:
    >
    > ```PowerShell
    > Set-MpPreference -AttackSurfaceReductionRules_Ids <rule ID 1>,<rule ID 2>,<rule ID 3>,<rule ID 4> -AttackSurfaceReductionRules_Actions Enabled, Enabled, Disabled, AuditMode
    > ```

    Var olan listeye yeni `Add-MpPreference` kurallar eklemek için PowerShell fiilsini de kullanabilirsiniz.

    > [!WARNING]
    > `Set-MpPreference` her zaman var olan kural kümesi üzerine yazacak. Var olan kümeye eklemek için bunun yerine kullanın `Add-MpPreference` .
    > 'ı kullanarak kuralların listesini ve geçerli durumlarını elde edinebilirsiniz `Get-MpPreference`.

3. Dosyaları ve klasörleri ASR kurallarından dışlamak için aşağıdaki cmdlet'i kullanın:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

    Listeye daha fazla `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` dosya ve klasör eklemek için kullanmaya devam edin.

    > [!IMPORTANT]
    > Listeye `Add-MpPreference` uygulama eklemek veya listeye uygulama eklemek için kullanın. `Set-MpPreference` Cmdlet kullanmak, var olan listenin üzerine yazmaz.

## <a name="related-articles"></a>İlgili makaleler

- [Saldırı yüzeyini azaltma kuralları başvurusu](attack-surface-reduction-rules-reference.md)
- [Saldırı yüzeyini azaltmayı değerlendir](evaluate-attack-surface-reduction.md)
- [Saldırı yüzeyini azaltma hakkında SSS](attack-surface-reduction.md)
