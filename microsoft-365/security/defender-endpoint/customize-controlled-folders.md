---
title: Denetimli klasör erişimini özelleştirme
description: Denetimli klasör erişimiyle korunması gereken başka klasörler ekleyin veya önemli dosyalarda yapılan değişiklikleri yanlışlıkla engelleyen uygulamalara izin verin.
keywords: Denetimli klasör erişimi, windows 10, windows 11, windows defender, fidye yazılımı, koruma, dosyalar, klasörler, özelleştir, klasör ekle, uygulama ekle, yürütülebilir dosya ekleme, izin ver, yürütülebilir dosya ekleme
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
ms.openlocfilehash: 04e7617825a3e14eac541b296cbed9f4dd95e206
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469327"
---
# <a name="customize-controlled-folder-access"></a>Denetimli klasör erişimini özelleştirme

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Denetimli klasör erişimi, değerli verileri fidye yazılımı gibi kötü amaçlı uygulamalara ve tehditlere karşı korumanıza yardımcı olur. Denetimli klasör erişimi Windows Server 2019, Windows Server 2022, Windows 10 ve Windows 11 destekler. Bu makalede, denetimli klasör erişimi özelliklerini nasıl özelleştirebileceğiniz açıklanmıştır ve aşağıdaki bölümleri içerir:

- [Ek klasörleri koruma](#protect-additional-folders)
- [Korumalı klasörlere erişmesine izin verilen uygulamaları ekleme](#allow-specific-apps-to-make-changes-to-controlled-folders)
- [İmzalı yürütülebilir dosyaların korumalı klasörlere erişmesine izin ver](#allow-signed-executable-files-to-access-protected-folders)
- [Bildirimi özelleştirme](#customize-the-notification)

> [!IMPORTANT]
> Denetimli klasör erişimi, kötü amaçlı olarak algılanan etkinlikler için uygulamaları izler. Bazen, yasal uygulamaların dosyalarında değişiklik yapmaları engellenir. Denetimli klasör erişimi, kurumnizin üretkenliğini etkiliyorsa, etkiyi tam olarak değerlendirmek için bu [özelliği denetim modunda](audit-windows-defender.md) çalıştırmayı düşünebilirsiniz.

## <a name="protect-additional-folders"></a>Ek klasörleri koruma

Denetimli klasör erişimi birçok sistem klasörüne ve Belgeler, Resimler ve Filmler gibi klasörler **de dahil olmak üzere varsayılan** konumlara **uygulanır**. Korunacak başka klasörler de ekleyebilirsiniz, ancak varsayılan listede varsayılan klasörleri kaldıramazsınız.

Denetimli klasör erişimine başka klasörler eklemek, dosyaları varsayılan klasör kitaplığında depolamama veya kitaplıkların varsayılan konumunu değiştirme Windows durumlarda yararlı olabilir.

Ağ paylaşımlarını ve eşlenmiş sürücüleri de belirtebilirsiniz. Ortam değişkenleri ve joker karakterler de desteklemektedir. Joker karakter kullanma hakkında bilgi için bkz. Dosya adı ve klasör yolu veya uzantı [dışlama listelerinde joker karakter kullanma](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

Korumalı klasörler eklemek ve Windows Güvenliği için Windows Güvenliği, grup ilkesi, PowerShell cmdlet'leri veya mobil cihaz yönetimi yapılandırma hizmet sağlayıcılarını kullanabilirsiniz.

### <a name="use-the-windows-security-app-to-protect-additional-folders"></a>Ek Windows Güvenliği korumak için Windows Güvenliği uygulamasını kullanma

1. Görev Windows Güvenliği kalkan simgesini seçerek veya görev çubuğunda güvenlik için arama *Başlat menüsü*.

2. Virüs **ve &'i** seçin ve fidye yazılımı koruması **bölümüne kadar aşağı** kaydırın.

3. Fidye **yazılımı koruması bölmesini açmak için** Fidye yazılımı **korumasını yönet'i** seçin.

4. Denetimli **klasör erişimi bölümünün** altında Korumalı **klasörler'i seçin**.

5. Kullanıcı **Bilgileri** isteminde **Evet'Access Control** seçin. Korumalı **klasörler bölmesi** görüntülenir.

6. Korumalı **klasör ekle'yi** seçin ve klasör eklemek için istemleri izleyin.

### <a name="use-group-policy-to-protect-additional-folders"></a>Ek grup ilkesi korumak için diğer klasörleri kullanma

1. Bilgisayarınızdan grup ilkesi Yönetim [Konsolu'nu grup ilkesi açın](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true). 

2. Yapılandırmak istediğiniz grup ilkesi Nesne'ye sağ tıklayın ve Düzenle'yi **seçin**.

3. Sistem Grup ilkesi **Düzenleyicisi'nde** Bilgisayar yapılandırması **İlkeleri Yönetim** \>  \> **şablonları'ne gidin**.

4. **Exploit Guard** \> Denetimli **Windows erişimini Microsoft Defender Virüsten Koruma** \> **Windows Defender** \> **ağacı genişletin**. <br/>**NOT**: Windows'Windows Defender Virüsten Koruma eski **Microsoft Defender Virüsten Koruma****.**

5. Yapılandırılmış korumalı **klasörler'e çift** tıklayın ve ardından seçeneği Etkin olarak **ayarlayın**. **Göster'i** seçin ve korumak istediğiniz her klasörü belirtin.

6. Nesnenizi grup ilkesi olduğu gibi dağıtın.

### <a name="use-powershell-to-protect-additional-folders"></a>Ek klasörleri korumak için PowerShell kullanma

1. Çalışma **kutusuna PowerShell** yazın, Başlat menüsü sağ tıklayın **Windows PowerShell Yönetici olarak** **çalıştır'ı seçin.**

2. Klasörün yoluyla değiştirerek aşağıdaki `<the folder to be protected>` PowerShell cmdlet'ini yazın (örneğin `"c:\apps\"`):

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessProtectedFolders "<the folder to be protected>"
    ```
3. Korumak istediğiniz her klasör için 2. adımı yinelayın. Korunan klasörler Windows Güvenliği.

   :::image type="content" source="images/cfa-allow-folder-ps.png" alt-text="Cmdlet'in gösterildiği PowerShell penceresi" lightbox="images/cfa-allow-folder-ps.png":::

> [!IMPORTANT]
> ' `Add-MpPreference` a değil, listeye uygulama eklemek veya listeye uygulama eklemek için kullanın `Set-MpPreference`. `Set-MpPreference` Cmdlet kullanmak, var olan listenin üzerine yazmaz.

### <a name="use-mdm-csps-to-protect-additional-folders"></a>Ek klasörleri korumak için MDM CSP'leri kullanma

Uygulamaların korumalı klasörlerde değişiklik yapmalarına izin vermek için [./Vendor/MSFT/Policy/Config/Defender/GuardedFoldersList](/windows/client-management/mdm/policy-csp-defender#defender-guardedfolderslist) yapılandırma hizmet sağlayıcısını (CSP) kullanın.

## <a name="allow-specific-apps-to-make-changes-to-controlled-folders"></a>Belirli uygulamaların denetimli klasörlerde değişiklik yapmalarına izin verme

Bazı uygulamaların her zaman güvenli kabul edilirse ve korumalı klasörlerdeki dosyalara yazma erişimi verebilirsiniz. Denetimli klasör erişimi özelliği, biliyor ve güvenmiyorsanız belirli bir uygulamanın engellenmiş olması durumda uygulamalara izin verme özelliği yararlı olabilir.

> [!IMPORTANT]
> Varsayılan olarak, Windows izin verilen listeye kolay kabul edilen uygulamalar ekler. Otomatik olarak eklenen bu tür uygulamalar, Windows Güvenliği uygulamasında veya ilişkili PowerShell cmdlet'leri kullanılarak gösterilen listeye eklenmez. Çoğu uygulama eklemenize gerek yok. Ancak engellenmişse ve güvenilir olduğunu doğrularsanız uygulamalar ekleyin.

Uygulama eklerken, uygulamanın konumunu belirtmeniz gerekir. Korumalı klasörlere yalnızca bu konumdaki uygulamaya erişim izni verilir. Uygulama (adı aynı olan) farklı bir konumda ise izin listesine eklenmez ve denetimli klasör erişimi tarafından engellenmiş olabilir.

İzin verilen bir uygulama veya hizmetin, yalnızca denetimli klasör başladıktan sonra yazma erişimi vardır. Örneğin, bir güncelleştirme hizmeti durdurulana ve yeniden başlatana kadar izin verildikten sonra olayları tetiklemeye devam edecektir.

### <a name="use-the-windows-defender-security-app-to-allow-specific-apps"></a>Belirli uygulamalara Windows Defender için Güvenlik uygulamasını kullanma

1. Başlat Windows Güvenliği Güvenlik'i arayarak Windows Güvenliği uygulamasını **açın**.

2. Virüs koruması **& kutucuğunu** (veya sol menü çubuğundaki kalkan simgesini) seçin ve ardından Fidye yazılımı korumasını **yönet'i seçin**.

3. Denetimli **klasör erişimi bölümü altında** Denetimli **klasör erişimi yoluyla uygulamaya izin ver'i seçin**

4. İzin **verilen uygulama ekle'yi** seçin ve uygulama eklemek için istemleri izleyin.

   :::image type="content" source="images/cfa-allow-app.png" alt-text="İzin verilen uygulama ekle düğmesi" lightbox="images/cfa-allow-app.png":::

### <a name="use-group-policy-to-allow-specific-apps"></a>Belirli grup ilkesi izin vermek için E-bilgileri kullanma

1. Mobil grup ilkesi cihazınızın Yönetim [Konsolu'nu grup ilkesi](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true), yapılandırmak istediğiniz Grup ilkesi Nesnesine sağ tıklayın ve Düzenle'yi **seçin**.

2. Grup ilkesi **Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin ve** Yönetim **şablonları'ı seçin**.

3. **Exploit Guard** \> Denetimli **Windows erişimini Microsoft Defender Virüsten Koruma** \> **Windows Defender** \> **ağacı genişletin**.

4. İzin verilen uygulamaları yapılandır **ayarına çift** tıklayın ve seçeneği Etkin olarak **ayarlayın**. **Göster'i** seçin ve her bir uygulamayı girin.

### <a name="use-powershell-to-allow-specific-apps"></a>Belirli uygulamalara izin vermek için PowerShell kullanma

1. Çalışma **kutusuna PowerShell** yazın, Başlat menüsü sağ tıklayın **Windows PowerShell Yönetici olarak** **çalıştır'ı seçin.**
2. Aşağıdaki cmdlet'i girin:

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "<the app that should be allowed, including the path>"
    ```

    Örneğin, *C:\apps**test.exe* yürütülebilir dosya dosyasını eklemek için, cmdlet şöyle olur:

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "c:\apps\test.exe"
    ```

   Listeye daha fazla `Add-MpPreference -ControlledFolderAccessAllowedApplications` uygulama eklemek için kullanmaya devam edin. Bu cmdlet kullanılarak eklenen uygulamalar, Windows Güvenliği görünür.

   :::image type="content" source="images/cfa-allow-app-ps.png" alt-text="Uygulamaya izin vermek için PowerShell cmdlet'i" lightbox="images/cfa-allow-app-ps.png":::

> [!IMPORTANT]
> Listeye `Add-MpPreference` uygulama eklemek veya listeye uygulama eklemek için kullanın. `Set-MpPreference` Cmdlet kullanmak, var olan listenin üzerine yazmaz.

### <a name="use-mdm-csps-to-allow-specific-apps"></a>Belirli uygulamalara izin vermek için MDM CSP'lerini kullanma

Uygulamaların korumalı klasörlerde değişiklik yapmalarına izin vermek için [./Vendor/MSFT/Policy/Config/Defender/GuardedFoldersAllowedApplications](/windows/client-management/mdm/policy-csp-defender#defender-guardedfoldersallowedapplications) yapılandırma hizmet sağlayıcısını (CSP) kullanın.

## <a name="allow-signed-executable-files-to-access-protected-folders"></a>İmzalı yürütülebilir dosyaların korumalı klasörlere erişmesine izin ver

Uç Nokta için Microsoft Defender sertifikası ve dosya göstergeleri, imzalanmış yürütülebilir dosyaların korumalı klasörlere erişmesine izinebilir. Uygulama ayrıntıları için bkz [. Sertifikalara dayalı göstergeler oluşturma](indicator-certificates.md).

> [!Note]
> Bu, Powershell de içinde olmak üzere betik altyapıları için geçerli değildir

## <a name="customize-the-notification"></a>Bildirimi özelleştirme

Kural tetiklendiğinde ve uygulama veya dosyayı engellerken bildirimi özelleştirme hakkında daha fazla bilgi için bkz. Kural tetiklendiğinde bildirim [Uç Nokta için Microsoft Defender](configure-email-notifications.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Denetimli klasör erişimiyle önemli klasörleri koruma](controlled-folders.md)
- [Denetimli klasör erişimini etkinleştirme](enable-controlled-folders.md)
- [Saldırı yüzeyini azaltma kurallarını değerlendirin](evaluate-attack-surface-reduction.md)
