---
title: Denetimli klasör erişimini etkinleştirme
keywords: Denetimli klasör erişimi, windows 10, windows 11, windows defender, fidye yazılımı, koruma, dosyalar, klasörler, etkinleştirmek, açmak, kullanmak
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
ms.collection: m365initiative-m365-defender
ms.date: ''
ms.openlocfilehash: fab57a3cb63823dcd4538f2b4bb381972d310c64
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63014274"
---
# <a name="enable-controlled-folder-access"></a>Denetimli klasör erişimini etkinleştirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Denetimli klasör erişimi](controlled-folders.md) , değerli verileri fidye yazılımı gibi kötü amaçlı uygulamalara ve tehditlere karşı korumanıza yardımcı olur. Denetimli klasör erişimi Windows 10, Windows 11 ve Windows Server 2019'a dahildir. Denetimli klasör erişimi, [Windows Server 2012R2 ve 2016 için modern, birleşik çözümün bir parçası olarak da dahil edilir](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).

Şu yöntemlerden herhangi birini kullanarak denetimli klasör erişimini etkinleştirebilirsiniz:

- [Windows Güvenliği uygulaması *](#windows-security-app)
- [Microsoft Endpoint Manager](#endpoint-manager)
- [Mobil Cihaz Yönetimi (MDM)](#mobile-device-management-mdm)
- [Microsoft Uç Noktası Yapılandırma Yöneticisi](#microsoft-endpoint-configuration-manager)
- [Grup İlkesi](#group-policy)
- [PowerShell](#powershell)

[Denetim modu](evaluate-controlled-folder-access.md) , cihazın normal kullanımını etkilemeden özelliğin nasıl çalışa çalış çalışa çalışmaya (ve olayları gözden geçirme) olanak sağlar.

Yerel yönetici listesi birleştirmeyi devre dışı bırakan Grup İlkesi ayarları, denetimli klasör erişim ayarlarını geçersiz kılar. Ayrıca, denetimli klasör erişimi aracılığıyla yerel yönetici tarafından ayarlanmış korumalı klasörleri ve izin verilen uygulamaları geçersiz kılar. Bu ilkeler şunlardır:

- Microsoft Defender Virüsten Koruma **Yönetici birleştirme davranışını yapılandırma**
- System Center Endpoint Protection **Dışlama ve geçersiz kılma eklemesine izin verme**

Yerel liste birleştirmeyi devre dışı bırakma hakkında daha fazla bilgi için bkz. Kullanıcıların [Microsoft Defender AV ilke ayarlarını yerel olarak değiştirmesini engelleme veya bu ayarlarda değişiklik olmasına izin verme](/windows/security/threat-protection/microsoft-defender-antivirus/configure-local-policy-overrides-microsoft-defender-antivirus).

## <a name="windows-security-app"></a>Windows Güvenliği uygulaması

1. Görev Windows Güvenliği kalkan simgesini seçerek görev çubuğunu açın. Başlat menüsünde arama ve arama **sonuçlarını Windows Güvenliği.**

2. Virüs koruması **& kutucuğunu** (veya sol menü çubuğundaki kalkan simgesini) seçin ve ardından Fidye Yazılımı **koruması'nda öğesini seçin**.

3. Denetimli klasör erişimi **anahtarını Açık olarak** **ayarlayın**.

> [!NOTE]
> *Bu yöntem Windows Server 2012R2 veya 2016'da kullanılamaz.
> 
> Denetimli klasör erişimi Grup İlkesi, PowerShell veya MDM CSP'lerle yapılandırılırsa, cihaz yeniden başlatıldıktan sonra Windows Güvenliği uygulamasında durum değişir.
> Bu araçlardan herhangi birini **kullanarak** özellik Denetim moduna Windows Güvenliği durum, Kapalı olarak **gösterir**.
> Kullanıcı profili verilerini koruyorsanız, kullanıcı profilinin yükleme sürücüsünde varsayılan Windows öneririz.

## <a name="endpoint-manager"></a>Endpoint Manager

1. Ağ bağlantılarında oturum [açın Endpoint Manager](https://endpoint.microsoft.com) Uç Nokta **Güvenliği'ne açın**.

2. Saldırı **Yüzeyini Azaltma İlkesi'ne** \> **gidin**.

3. **Platform'ı** seçin, **Windows 10 ve sonra da** Saldırı Yüzeyini Azaltma kuralları **Oluştur profilini** \> **seçin**.

4. İlkeyi adlama ve açıklama ekleme. **İleri**'yi seçin.

5. Ekranı en alta kaydırın, Klasör **Korumasını Etkinleştir açılan listesinden** Etkinleştir'i **seçin**.

6. Korunması **gereken ek klasörlerin listesi'ne tıklayın** ve korunması gereken klasörleri ekleyin.

7. Korumalı **klasörlere erişimi olan uygulamaların listesi'ne tıklayın** ve korumalı klasörlere erişimi olan uygulamaları ekleyin.

8. Saldırı **yüzeyini azaltma kurallarındaki dosyaları ve yolları hariç** tut'ı seçin ve saldırı yüzeyini azaltma kuralları dışında tutulacak dosyaları ve yolları ekleyin.

9. Profil **Ödevleri'ne tıklayın**, Tüm **Cihazlara Tüm &'e atayın** ve Kaydet'i **seçin**.

10. Her **açık blade'i** kaydetmek için Sonraki'yi seçin ve ardından **Oluştur'a tıklayın**.

    > [!NOTE]
    > Joker karakterler uygulamalarda destekler, ancak klasörler için desteklemez. Alt klasörler korunmaz. İzin verilen uygulamalar yeniden başlatana kadar olayları tetiklemeye devam edecektir.

## <a name="mobile-device-management-mdm"></a>Mobil Cihaz Yönetimi (MDM)

Uygulamaların korumalı klasörlerde değişiklik yapmalarına izin vermek için [./Vendor/MSFT/Policy/Config/ControlledFolderAccessProtectedFolders](/windows/client-management/mdm/policy-csp-defender) yapılandırma hizmet sağlayıcısını (CSP) kullanın.

## <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Uç Noktası Yapılandırma Yöneticisi

1. Daha Microsoft Endpoint Configuration Manager, Varlıklar ve **Uyumluluk Uyumluluğu güvenlik Endpoint Protection** \>  \> **Windows Defender Exploit Guard'a gidin**.

2.  \> Home **Create Exploit Guard Policy öğesini seçin**.

3. Bir ad ve açıklama girin, Denetimli klasör **erişimi'ne ve** ardından Sonraki'ye **tıklayın**.

4. Değişiklikleri engelleme veya denetleme, diğer uygulamalara izin verme veya başka klasörler ekleme arasında seçim yapın ve Sonraki'yi **seçin**.

   > [!NOTE]
   > Joker karakter uygulamalar için destekler, ancak klasörler için desteklemez. Alt klasörler korunmaz. İzin verilen uygulamalar yeniden başlatana kadar olayları tetiklemeye devam edecektir.

5. Ayarları gözden geçirerek **Sonraki'yi** seçerek ilkeyi oluşturun.

6. İlke oluşturulduktan sonra **Kapat'a.**

## <a name="group-policy"></a>Grup İlkesi

1. Grup İlkesi yönetim aygıtınızda, Grup İlkesi [Yönetim Konsolu'nu](https://technet.microsoft.com/library/cc731212.aspx) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'yi **seçin**.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde** Bilgisayar **yapılandırması'ne gidin ve** Yönetim **şablonları'ı seçin**.

3. Denetimli klasör erişimi **Windows Exploit Guard > Microsoft Defender Virüsten Koruma > Windows Defender bileşenleri > ağacı genişletin**.

4. Denetimli klasör erişimini **yapılandır ayarına çift** tıklayın ve seçeneği Etkin olarak **ayarlayın**. Seçenekler bölümünde, aşağıdaki seçeneklerden birini belirtebilirsiniz:
   - **Etkinleştir** - Kötü amaçlı ve şüpheli uygulamaların korumalı klasörlerdeki dosyalarda değişiklik yapmalarına izin verilmez. Etkinlik günlüğünde bir Windows sağlanır.
   - **Devre Dışı Bırak (Varsayılan)** - Denetimli klasör erişimi özelliği çalışmaz. Tüm uygulamalar korumalı klasörlerdeki dosyalarda değişiklik yapabilirsiniz.
   - **Denetim Modu** - Kötü amaçlı veya şüpheli bir uygulama korumalı klasördeki bir dosyada değişiklik yapmaya çalışırsa, değişikliklere izin verilir. Bununla birlikte, bu bilgi Windows üzerindeki etkiyi değerlendir değerlendirmeniz için bu olay günlüğüne kaydedilir.
   - **Yalnızca disk değişikliğini engelle** - Güvenilmeyen uygulamaların diske yazma denemeleri, Olay Windows kaydedilir. Bu günlükler **,** \> Microsoft \> \> Windows Windows Defender 1123'te Uygulamalar ve Hizmet Günlükleri \> \> makalesinde bulunabilir.
   - **Yalnızca denetim disk değişikliği** - Korumalı diske yazma denemeleri, Windows olay günlüğüne (  \> Uygulamalar ve Hizmet Günlükleri **Microsoft** \> **Windows Windows Defender** \>  \> \> **1124** altında) kaydedilir. Korumalı klasörlerdeki dosyaları değiştirme veya silme girişimleri kaydedilemez.

      ![Açılan gruptaki Etkin ve Denetim Modu'nda seçili grup ilkesi seçeneğinin ekran görüntüsü.](../../media/cfa-gp-enable.png)

> [!IMPORTANT]
> Denetimli klasör erişimini tümüyle etkinleştirmek için Grup İlkesi seçeneğini Etkin olarak ayarlamalı **ve seçenekler açılan** menüsünde Engelle'yi seçilmelidir.

## <a name="powershell"></a>PowerShell

1. **PowerShell yazın ve** Başlat menüsü sağ tıklayın ve **Windows PowerShell Yönetici olarak** **çalıştır'ı seçin**.

2. Aşağıdaki cmdlet'i girin:

    ```PowerShell
    Set-MpPreference -EnableControlledFolderAccess Enabled
    ```

Bunun yerine, 'ın yerine belirterek özelliği denetim modunda `AuditMode` etkinleştirebilirsiniz `Enabled`.

Özelliği `Disabled` kapatmak için kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Denetimli klasör erişimiyle önemli klasörleri koruma](controlled-folders.md)
- [Denetimli klasör erişimini özelleştirme](customize-controlled-folders.md)
- [Uç Nokta için Microsoft Defender'ı Değerlendirme](evaluate-mde.md)
