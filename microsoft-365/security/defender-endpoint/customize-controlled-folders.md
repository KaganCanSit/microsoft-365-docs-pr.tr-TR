---
title: Denetimli klasör erişimini özelleştirin
description: Denetimli klasör erişimiyle korunması gereken diğer klasörleri ekleyin veya önemli dosyalardaki değişiklikleri yanlış engelleyen uygulamalara izin verin.
keywords: Denetimli klasör erişimi, windows 10, windows 11, windows defender, fidye yazılımı, koruma, dosyalar, klasörler, özelleştirme, klasör ekleme, uygulama ekleme, izin verme, yürütülebilir dosya ekleme
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: oogunrinde, dbodorin, vladiso, nixanm, anvascon
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.date: ''
ms.openlocfilehash: 3d6f763bd2ac2c4352f1b200c05c3079bc615aaf
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139351"
---
# <a name="customize-controlled-folder-access"></a>Denetimli klasör erişimini özelleştirin

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

> [!TIP]
> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Denetimli klasör erişimi, değerli verileri fidye yazılımı gibi kötü amaçlı uygulamalardan ve tehditlerden korumanıza yardımcı olur. Windows Server 2019, Windows Server 2022, Windows 10 ve Windows 11 istemcilerinde denetimli klasör erişimi desteklenir. Bu makalede, denetimli klasör erişim özelliklerinin nasıl özelleştirileceği açıklanır ve aşağıdaki bölümler yer alır:

- [Ek klasörleri koruma](#protect-additional-folders)
- [Korumalı klasörlere erişmesine izin verilmesi gereken uygulamalar ekleme](#allow-specific-apps-to-make-changes-to-controlled-folders)
- [İmzalı yürütülebilir dosyaların korumalı klasörlere erişmesine izin ver](#allow-signed-executable-files-to-access-protected-folders)
- [Bildirimi özelleştirme](#customize-the-notification)

> [!IMPORTANT]
> Denetimli klasör erişimi, kötü amaçlı olarak algılanan etkinlikler için uygulamaları izler. Bazı durumlarda, yasal uygulamaların dosyalarınızda değişiklik yapması engellenir. Denetimli klasör erişimi kuruluşunuzun üretkenliğini etkiliyorsa, etkiyi tam olarak değerlendirmek için bu özelliği [denetim modunda](audit-windows-defender.md) çalıştırmayı düşünebilirsiniz.

## <a name="protect-additional-folders"></a>Ek klasörleri koruma

Denetimli klasör erişimi Belgeler, **Resimler** ve **Filmler** gibi klasörler de dahil olmak üzere birçok sistem klasörü ve varsayılan **konumlar** için geçerlidir. Korunacak başka klasörler ekleyebilirsiniz, ancak varsayılan listedeki varsayılan klasörleri kaldıramazsınız.

Diğer klasörleri denetimli klasör erişimine eklemek, dosyaları varsayılan Windows kitaplıklarında depolamadığınız veya kitaplıklarınızın varsayılan konumunu değiştirdiğiniz durumlar için yararlı olabilir.

Ağ paylaşımlarını ve eşlenmiş sürücüleri de belirtebilirsiniz. Ortam değişkenleri ve joker karakterler desteklenir. Joker karakterleri kullanma hakkında bilgi için bkz. [Dosya adı ve klasör yolu veya uzantı dışlama listelerinde joker karakterler kullanma](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

Korumalı klasörleri eklemek ve kaldırmak için Windows Güvenliği uygulamasını, grup ilkesi, PowerShell cmdlet'lerini veya mobil cihaz yönetimi yapılandırma hizmet sağlayıcılarını kullanabilirsiniz.

### <a name="use-the-windows-security-app-to-protect-additional-folders"></a>Ek klasörleri korumak için Windows Güvenliği uygulamasını kullanma

1. Görev çubuğunda kalkan simgesini seçerek veya Başlat menüsü *güvenlik* arayarak Windows Güvenliği uygulamasını açın.

2. **Virüs & tehdit koruması'nı** seçin ve **fidye yazılımı koruması** bölümüne gidin.

3. **Fidye yazılımı koruması bölmesini açmak için Fidye yazılımı korumasını yönet'i** seçin.

4. **Denetimli klasör erişimi** bölümünde **Korumalı klasörler'i** seçin.

5. **Kullanıcı Access Control** isteminde **Evet'i** seçin. **Korumalı klasörler** bölmesi görüntülenir.

6. **Korumalı klasör ekle'yi** seçin ve klasörleri eklemek için istemleri izleyin.

### <a name="use-group-policy-to-protect-additional-folders"></a>Ek klasörleri korumak için grup ilkesi kullanma

1. grup ilkesi yönetim bilgisayarınızda [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true) açın. 

2. Yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **düzenle'yi** seçin.

3. **grup ilkesi Yönetim Düzenleyicinizde** **Bilgisayar yapılandırma** \> **İlkeleri** \> **Yönetim şablonları'na** gidin.

4. **Exploit Guard** \> **Denetimli klasör erişimi** **Windows Defender Microsoft Defender Virüsten Koruma** \> **bileşenleri** \> Windows için ağacı genişletin. <br/>**NOT**: Windows'ın eski sürümlerinde **Microsoft Defender Virüsten Koruma** yerine **Windows Defender Virüsten Koruma** görebilirsiniz.

5. **Yapılandırılmış korumalı klasörler'e** çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. **Göster'i** seçin ve korumak istediğiniz her klasörü belirtin.

6. grup ilkesi Nesnenizi genellikle yaptığınız gibi dağıtın.

### <a name="use-powershell-to-protect-additional-folders"></a>Ek klasörleri korumak için PowerShell kullanma

1. Başlat menüsü **PowerShell** yazın, **Windows PowerShell** sağ tıklayın ve **Yönetici olarak çalıştır'ı** seçin

2. aşağıdaki PowerShell cmdlet'ini yazın ve yerine `<the folder to be protected>` klasörün yolunu yazın (örneğin `"c:\apps\"`):

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessProtectedFolders "<the folder to be protected>"
    ```
3. Korumak istediğiniz her klasör için 2. adımı yineleyin. Korunan klasörler Windows Güvenliği uygulamasında görünür.

   :::image type="content" source="images/cfa-allow-folder-ps.png" alt-text="Cmdlet'in gösterildiği PowerShell penceresi" lightbox="images/cfa-allow-folder-ps.png":::

> [!IMPORTANT]
> öğesini değil`Set-MpPreference`, listeye uygulama eklemek veya eklemek için kullanın`Add-MpPreference`. cmdlet'ini `Set-MpPreference` kullanmak varolan listenin üzerine yazılır.

### <a name="use-mdm-csps-to-protect-additional-folders"></a>Ek klasörleri korumak için MDM CSP'lerini kullanma

Uygulamaların korumalı klasörlerde değişiklik yapmasına izin vermek için [./Vendor/MSFT/Policy/Config/Defender/GuardedFoldersList](/windows/client-management/mdm/policy-csp-defender#defender-guardedfolderslist) yapılandırma hizmeti sağlayıcısını (CSP) kullanın.

## <a name="allow-specific-apps-to-make-changes-to-controlled-folders"></a>Belirli uygulamaların denetimli klasörlerde değişiklik yapmasına izin ver

Belirli uygulamaların her zaman güvenli kabul edilip değerlendirilmediğini belirtebilir ve korumalı klasörlerdeki dosyalara yazma erişimi verebilirsiniz. Tanıdığınız ve güvendiğiniz belirli bir uygulama denetimli klasör erişimi özelliği tarafından engelleniyorsa uygulamalara izin vermek yararlı olabilir.

> [!IMPORTANT]
> varsayılan olarak, Windows izin verilenler listesine kolay olarak kabul edilen uygulamalar ekler. Otomatik olarak eklenen bu tür uygulamalar, Windows Güvenliği uygulamasında gösterilen listeye veya ilişkili PowerShell cmdlet'leri kullanılarak kaydedilmez. Çoğu uygulamayı eklemeniz gerekmez. Uygulamaları yalnızca engelleniyorsa ekleyin ve bunların güvenilirliğini doğrulayabilirsiniz.

Bir uygulama eklediğinizde, uygulamanın konumunu belirtmeniz gerekir. Korumalı klasörlere yalnızca o konumdaki uygulamaya erişim izni verilir. Uygulama (aynı ada sahip) farklı bir konumdaysa, izin verilenler listesine eklenmez ve denetimli klasör erişimi tarafından engellenebilir.

İzin verilen bir uygulama veya hizmet yalnızca başlatıldıktan sonra denetimli bir klasöre yazma erişimine sahiptir. Örneğin, bir güncelleştirme hizmeti durdurulup yeniden başlatılana kadar izin verildikten sonra olayları tetiklemeye devam eder.

### <a name="use-the-windows-defender-security-app-to-allow-specific-apps"></a>Belirli uygulamalara izin vermek için Windows Defender Güvenlik uygulamasını kullanma

1. Başlangıç menüsünde **Güvenlik** araması yaparak Windows Güvenliği uygulamasını açın.

2. **Virüs & tehdit koruması** kutucuğunu (veya sol menü çubuğundaki kalkan simgesini) ve ardından **Fidye yazılımı korumasını yönet'i** seçin.

3. **Denetimli klasör erişimi** bölümünde, **Denetimli klasör erişimi aracılığıyla bir uygulamaya izin ver'i** seçin

4. **İzin verilen uygulama ekle'yi** seçin ve uygulama eklemek için istemleri izleyin.

   :::image type="content" source="images/cfa-allow-app.png" alt-text="İzin verilen uygulama ekle düğmesi" lightbox="images/cfa-allow-app.png":::

### <a name="use-group-policy-to-allow-specific-apps"></a>Belirli uygulamalara izin vermek için grup ilkesi kullanma

1. grup ilkesi yönetim cihazınızda [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'yi** seçin.

2. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin ve **Yönetim şablonları'nı** seçin.

3. **Exploit Guard** \> **Denetimli klasör erişimi** **Windows Defender Microsoft Defender Virüsten Koruma** \> **bileşenleri** \> Windows için ağacı genişletin.

4. **İzin verilen uygulamaları yapılandır** ayarına çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. **Göster'i** seçin ve her uygulamayı girin.

### <a name="use-powershell-to-allow-specific-apps"></a>Belirli uygulamalara izin vermek için PowerShell kullanma

1. Başlat menüsü **PowerShell** yazın, **Windows PowerShell** sağ tıklayın ve **Yönetici olarak çalıştır'ı** seçin
2. Aşağıdaki cmdlet'i girin:

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "<the app that should be allowed, including the path>"
    ```

    Örneğin, *C:\apps* klasöründe bulunan yürütülebilir *test.exe* eklemek için cmdlet aşağıdaki gibi olacaktır:

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "c:\apps\test.exe"
    ```

   Listeye daha fazla uygulama eklemek için kullanmaya `Add-MpPreference -ControlledFolderAccessAllowedApplications` devam edin. Bu cmdlet kullanılarak eklenen uygulamalar Windows Güvenliği uygulamasında görünür.

   :::image type="content" source="images/cfa-allow-app-ps.png" alt-text="Uygulamaya izin vermek için PowerShell cmdlet'i" lightbox="images/cfa-allow-app-ps.png":::

> [!IMPORTANT]
> Listeye uygulama eklemek veya eklemek için kullanın `Add-MpPreference` . cmdlet'ini `Set-MpPreference` kullanmak varolan listenin üzerine yazılır.

### <a name="use-mdm-csps-to-allow-specific-apps"></a>Belirli uygulamalara izin vermek için MDM CSP'lerini kullanma

Uygulamaların korumalı klasörlerde değişiklik yapmasına izin vermek için [./Vendor/MSFT/Policy/Config/Defender/ControlledFolderAccessAllowedApplications](/windows/client-management/mdm/policy-csp-defender#defender-guardedfoldersallowedapplications) yapılandırma hizmeti sağlayıcısını (CSP) kullanın.

## <a name="allow-signed-executable-files-to-access-protected-folders"></a>İmzalı yürütülebilir dosyaların korumalı klasörlere erişmesine izin ver

Uç Nokta için Microsoft Defender sertifika ve dosya göstergeleri, imzalı yürütülebilir dosyaların korumalı klasörlere erişmesine izin verebilir. Uygulama ayrıntıları için bkz. [Sertifikaları temel alan göstergeler oluşturma](indicator-certificates.md).

> [!Note]
> Bu, PowerShell dahil olmak üzere betik altyapıları için geçerli değildir

## <a name="customize-the-notification"></a>Bildirimi özelleştirme

Bir kural tetiklendiğinde ve bir uygulama veya dosyayı engellediğinde bildirimi özelleştirme hakkında daha fazla bilgi için bkz[. Uç Nokta için Microsoft Defender'de uyarı bildirimlerini yapılandırma](configure-email-notifications.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Denetimli klasör erişimiyle önemli klasörleri koruma](controlled-folders.md)
- [Denetimli klasör erişimini etkinleştirin](enable-controlled-folders.md)
- [Saldırı yüzeyi azaltma kurallarını etkinleştirme](enable-attack-surface-reduction.md)
