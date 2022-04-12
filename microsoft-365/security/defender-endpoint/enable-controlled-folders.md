---
title: Denetimli klasör erişimini etkinleştirin
keywords: Denetimli klasör erişimi, windows 10, windows 11, windows defender, fidye yazılımı, koruma, dosyalar, klasörler, etkinleştirme, açma, kullanma
description: Denetimli klasör erişimini etkinleştirerek önemli dosyalarınızı korumayı öğrenin
ms.prod: m365-security
ms.topic: article
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: dansimp
ms.author: dansimp
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.date: ''
ms.openlocfilehash: 4854ca235790cc8400f3f5a962e4bff203f86f98
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788138"
---
# <a name="enable-controlled-folder-access"></a>Denetimli klasör erişimini etkinleştirin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

> Uç Nokta için Defender'ı deneyimlemek mi istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Denetimli klasör erişimi](controlled-folders.md) , değerli verileri fidye yazılımı gibi kötü amaçlı uygulamalardan ve tehditlerden korumanıza yardımcı olur. Denetimli klasör erişimi Windows 10, Windows 11 ve Windows Server 2019'a dahildir. Denetimli klasör erişimi, [Windows Server 2012R2 ve 2016 için modern, birleşik çözümün](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview) bir parçası olarak da bulunur.

Şu yöntemlerden herhangi birini kullanarak denetimli klasör erişimini etkinleştirebilirsiniz:

- [Windows Güvenliği uygulaması *](#windows-security-app)
- [Microsoft Endpoint Manager](#endpoint-manager)
- [Mobil Cihaz Yönetimi (MDM)](#mobile-device-management-mdm)
- [Microsoft Uç Noktası Yapılandırma Yöneticisi](#microsoft-endpoint-configuration-manager)
- [Grup İlkesi](#group-policy)
- [PowerShell](#powershell)

[Denetim modu](evaluate-controlled-folder-access.md) , cihazın normal kullanımını etkilemeden özelliğin nasıl çalışacağını test etmenizi (ve olayları gözden geçirmenizi) sağlar.

Yerel yönetici listesi birleştirmeyi devre dışı bırakmayan grup ilkesi ayarları, denetimli klasör erişim ayarlarını geçersiz kılar. Ayrıca korumalı klasörleri ve denetimli klasör erişimi aracılığıyla yerel yönetici tarafından ayarlanan izin verilen uygulamaları geçersiz kılar. Bu ilkeler şunlardır:

- Microsoft Defender Virüsten Koruma **Listeler için yerel yönetici birleştirme davranışını yapılandırma**
- System Center Endpoint Protection **Kullanıcıların dışlamalar ve geçersiz kılmalar eklemesine izin ver**

Yerel liste birleştirmeyi devre dışı bırakma hakkında daha fazla bilgi için bkz. [Kullanıcıların Microsoft Defender AV ilke ayarlarını yerel olarak değiştirmesini engelleme veya izin verme](/windows/security/threat-protection/microsoft-defender-antivirus/configure-local-policy-overrides-microsoft-defender-antivirus).

## <a name="windows-security-app"></a>Windows Güvenliği uygulaması

1. Görev çubuğunda kalkan simgesini seçerek Windows Güvenliği uygulamasını açın. Başlangıç menüsünde **Windows Güvenliği** için de arama yapabilirsiniz.

2. **Virüs & tehdit koruması** kutucuğunu (veya sol menü çubuğundaki kalkan simgesini) ve ardından **Fidye yazılımı koruması'nı** seçin.

3. **Denetimli klasör erişimi** anahtarını **Açık** olarak ayarlayın.

> [!NOTE]
> *Bu yöntem Windows Server 2012R2 veya 2016'da kullanılamaz.
> 
> Denetimli klasör erişimi grup ilkesi, PowerShell veya MDM CSP'leriyle yapılandırılırsa, cihaz yeniden başlatıldıktan sonra Windows Güvenliği uygulamasında durum değişir.
> Özellik bu araçlardan herhangi biriyle **Denetim moduna** ayarlanırsa, Windows Güvenliği uygulaması durumu **Kapalı** olarak gösterir.
> Kullanıcı profili verilerini koruyorsanız, kullanıcı profilinin varsayılan Windows yükleme sürücüsünde olması önerilir.

## <a name="endpoint-manager"></a>Endpoint Manager

1. [Endpoint Manager](https://endpoint.microsoft.com) oturum açın ve **Endpoint Security'yi** açın.

2. **Saldırı Yüzeyi Azaltma** \> **İlkesi'ne** gidin.

3. **Platform'u** seçin, **Windows 10 ve üzerini** seçin ve **ardından Saldırı Yüzeyi Azaltma kuralları** \> **Oluştur** profilini seçin.

4. İlkeyi adlandırın ve bir açıklama ekleyin. **İleri**'yi seçin.

5. Aşağı kaydırarak en alta gelin, **Klasör Korumasını Etkinleştir** açılan listesini seçin ve **Etkinleştir'i** seçin.

6. **Korunması gereken ek klasörlerin listesi'ni** seçin ve korunması gereken klasörleri ekleyin.

7. **Korumalı klasörlere erişimi olan uygulamaların listesi'ni seçin ve korumalı klasörlere** erişimi olan uygulamaları ekleyin.

8. **Saldırı yüzeyi azaltma kurallarındaki dosyaları ve yolları dışla'yı** seçin ve saldırı yüzeyi azaltma kurallarının dışında tutulması gereken dosyaları ve yolları ekleyin.

9. Profil **Atamaları'nı** seçin, **Tüm Kullanıcılar & Tüm Cihazlar'a** atayın ve **Kaydet'i** seçin.

10. Her açık dikey pencereyi kaydetmek için **İleri'yi** ve ardından **Oluştur'u** seçin.

    > [!NOTE]
    > Joker karakterler uygulamalar için desteklenir, ancak klasörler için desteklenmez. Alt klasörler korunmaz. İzin verilen uygulamalar yeniden başlatılana kadar olayları tetiklemeye devam eder.

## <a name="mobile-device-management-mdm"></a>Mobil Cihaz Yönetimi (MDM)

Uygulamaların korumalı klasörlerde değişiklik yapmasına izin vermek için [./Vendor/MSFT/Policy/Config/ControlledFolderAccessProtectedFolders](/windows/client-management/mdm/policy-csp-defender) yapılandırma hizmeti sağlayıcısını (CSP) kullanın.

## <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Uç Noktası Yapılandırma Yöneticisi

1. Microsoft Endpoint Configuration Manager'da **Varlıklar ve Uyumluluk** \> **Endpoint Protection** \> **Windows Defender Exploit Guard'a** gidin.

2. **Giriş** \> **Oluşturma Exploit Guard İlkesi'ni** seçin.

3. Bir ad ve açıklama girin, **Denetimli klasör erişimi'ni** ve **ardından İleri'yi** seçin.

4. Değişiklikleri engellemeyi veya denetlemeyi, diğer uygulamalara izin vermeyi veya başka klasörler eklemeyi seçin ve **İleri'yi** seçin.

   > [!NOTE]
   > Joker karakter uygulamalar için desteklenir, ancak klasörler için desteklenmez. Alt klasörler korunmaz. İzin verilen uygulamalar yeniden başlatılana kadar olayları tetiklemeye devam eder.

5. İlkeyi oluşturmak için ayarları gözden geçirin ve **İleri'yi** seçin.

6. İlke oluşturulduktan sonra **Kapat'ı seçin**.

## <a name="group-policy"></a>Grup İlkesi

1. grup ilkesi yönetim cihazınızda [grup ilkesi Yönetim Konsolu'nu](https://technet.microsoft.com/library/cc731212.aspx) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'yi** seçin.

2. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin ve **Yönetim şablonları'nı** seçin.

3. **Exploit Guard > Denetimli klasör erişimi > Microsoft Defender Virüsten Koruma > Windows Defender bileşenleri Windows** için ağacı genişletin.

4. **Denetimli klasör erişimini yapılandır** ayarına çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. Seçenekler bölümünde aşağıdaki seçeneklerden birini belirtmeniz gerekir:
   - **Etkinleştir** - Kötü amaçlı ve şüpheli uygulamaların korumalı klasörlerdeki dosyalarda değişiklik yapmasına izin verilmez. Windows olay günlüğünde bir bildirim sağlanır.
   - **Devre dışı bırak (Varsayılan)** - Denetimli klasör erişimi özelliği çalışmaz. Tüm uygulamalar korumalı klasörlerdeki dosyalarda değişiklik yapabilir.
   - **Denetim Modu** - Kötü amaçlı veya şüpheli bir uygulama korumalı klasördeki bir dosyada değişiklik yapmaya çalışırsa değişikliklere izin verilir. Ancak, kuruluşunuz üzerindeki etkisini değerlendirebileceğiniz Windows olay günlüğüne kaydedilir.
   - **Yalnızca disk değişikliğini engelle** - Güvenilmeyen uygulamaların disk kesimlerine yazma denemeleri Olay günlüğü Windows günlüğe kaydedilir. Bu günlükler, Microsoft \> Windows Windows Defender \> \> İşlem \> Kimliği 1123'te **bulunan Uygulama ve Hizmet Günlükleri'nde** \> bulunabilir.
   - **Yalnızca disk değişikliğini denetle** - Yalnızca korumalı disk kesimlerine yazma girişimleri Windows olay günlüğüne kaydedilir (**Uygulama ve Hizmet Günlükleri** \> **Altında Microsoft** \> **Windows Windows Defender** \>  \> **İşletim Kimliği** \> **1124**). Korumalı klasörlerdeki dosyaları değiştirme veya silme girişimleri kaydedilmez.

    :::image type="content" source="../../media/cfa-gp-enable.png" alt-text="Grup ilkesi seçeneği Etkin ve Denetim Modu seçili" lightbox="../../media/cfa-gp-enable.png":::

> [!IMPORTANT]
> Denetimli klasör erişimini tam olarak etkinleştirmek için, grup ilkesi seçeneğini **Etkin** olarak ayarlamanız ve seçenekler açılan menüsünde **Engelle'yi** seçmeniz gerekir.

## <a name="powershell"></a>PowerShell

1. Başlat menüsü **powershell** yazın, **Windows PowerShell** sağ tıklayın ve **Yönetici olarak çalıştır'ı** seçin.

2. Aşağıdaki cmdlet'i girin:

    ```PowerShell
    Set-MpPreference -EnableControlledFolderAccess Enabled
    ```

yerine belirterek `AuditMode` `Enabled`özelliği denetim modunda etkinleştirebilirsiniz.

Özelliği kapatmak için kullanın `Disabled` .

## <a name="see-also"></a>Ayrıca bkz.

- [Denetimli klasör erişimiyle önemli klasörleri koruma](controlled-folders.md)
- [Denetimli klasör erişimini özelleştirin](customize-controlled-folders.md)
- [Uç Nokta için Microsoft Defender'ı Değerlendirme](evaluate-mde.md)
