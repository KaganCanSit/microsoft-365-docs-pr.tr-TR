---
title: Ağ korumasını açın
description: grup ilkesi, PowerShell veya Mobil Cihaz Yönetimi ve Configuration Manager ile ağ korumasını etkinleştirin.
keywords: Ağ koruması, açıklardan yararlanmalar, kötü amaçlı web sitesi, ip, etki alanı, etki alanları, etkinleştirme, açma
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.date: ''
ms.openlocfilehash: e53cda0ac61bdc546e972d663bf0063b02b21ad3
ms.sourcegitcommit: 570c3be37b6ab1d59a4988f7de9c9fb5ca38028f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2022
ms.locfileid: "65363280"
---
# <a name="turn-on-network-protection"></a>Ağ korumasını açın

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

> [!TIP]
> Uç Nokta için Defender'ı deneyimlemek mi istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Ağ koruması](network-protection.md) , çalışanların internet üzerinde kimlik avı dolandırıcılığı, açıklardan yararlanma ve diğer kötü amaçlı içeriğe ev sahipliği yapabilen tehlikeli etki alanlarına erişmek için herhangi bir uygulama kullanmasını önlemeye yardımcı olur. [Ağ korumasını](evaluate-network-protection.md) etkinleştirmeden önce hangi uygulamaların engellendiğini görüntülemek için bir test ortamında ağ korumasını denetleyebilirsiniz.

[Ağ filtreleme yapılandırma seçenekleri hakkında daha fazla bilgi edinin.](/mem/intune/protect/endpoint-protection-windows-10#network-filtering)

## <a name="check-if-network-protection-is-enabled"></a>Ağ korumasının etkinleştirilip etkinleştirilmediğini denetleme

Kayıt defteri düzenleyicisini kullanarak yerel bir cihazda ağ korumasının etkinleştirilip etkinleştirilmediğini denetleyin.

1. Görev çubuğunda **Başlangıç** düğmesini seçin ve kayıt defteri düzenleyicisini açmak için **regedit** yazın.

2. Yan **menüden HKEY_LOCAL_MACHINE** seçin.

3. İç içe menülerde **YAZıLıM** \> **İlkeleri** \> **Microsoft** \> **Windows Defender Windows Defender** \> **Exploit Guard** **Ağ Koruması'na**\> gidin.

Anahtar eksikse **SOFTWARE** \> **Microsoft** \> **Windows Defender Windows Defender** \> **Exploit Guard** **Ağ Koruması'na**\> gidin.

4. Cihazdaki ağ korumasının geçerli durumunu görmek için **EnableNetworkProtection** öğesini seçin:

   - 0 veya **Kapalı**
   - 1 veya **Açık**
   - 2 veya **Denetim** modu

    :::image type="content" source="../../media/95341270-b738b280-08d3-11eb-84a0-16abb140c9fd.png" alt-text="Ağ Koruması kayıt defteri anahtarı" lightbox="../../media/95341270-b738b280-08d3-11eb-84a0-16abb140c9fd.png":::

## <a name="enable-network-protection"></a>Ağ korumasını etkinleştirme

Aşağıdaki yöntemlerden herhangi birini kullanarak ağ korumasını etkinleştirin:

- [PowerShell](#powershell)
- [Mobil Cihaz Yönetimi (MDM)](#mobile-device-management-mdm)
- [Microsoft Endpoint Manager](#microsoft-endpoint-manager)
- [Grup İlkesi](#group-policy)
- [Microsoft Uç Noktası Yapılandırma Yöneticisi](#microsoft-endpoint-configuration-manager)

### <a name="powershell"></a>PowerShell

1. Başlat menüsü **powershell** yazın, **Windows PowerShell** sağ tıklayın ve **Yönetici olarak çalıştır'ı** seçin.

2. Aşağıdaki cmdlet'i girin:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection Enabled
    ```

3. İsteğe bağlı: Aşağıdaki cmdlet'i kullanarak özelliği denetim modunda etkinleştirin:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

    Özelliği kapatmak için veya `Enabled` yerine `AuditMode` kullanın`Disabled`.

### <a name="mobile-device-management-mdm"></a>Mobil cihaz yönetimi (MDM)

Ağ korumasını etkinleştirmek veya devre dışı bırakmak ya da denetim modunu etkinleştirmek için [./Vendor/MSFT/Policy/Config/Defender/EnableNetworkProtection](/windows/client-management/mdm/policy-csp-defender) yapılandırma hizmet sağlayıcısını (CSP) kullanın.

Ağ korumasını etkinleştirmeden veya devre dışı bırakmadan veya denetim modunu etkinleştirmeden önce [Microsoft Defender kötü amaçlı yazılımdan koruma platformunu en son sürüme güncelleştirin](https://support.microsoft.com/topic/update-for-microsoft-defender-antimalware-platform-92e21611-8cf1-8e0e-56d6-561a07d144cc).


### <a name="microsoft-endpoint-manager"></a>Microsoft Endpoint Manager

1. Microsoft Endpoint Manager yönetim merkezinde (https://endpoint.microsoft.com).

2. **CihazlarYapılandırma** >  **profilleriProfil** >  oluştur'a gidin.

3. **Profil oluştur** açılır penceresinde **Platform'u** ve ardından **Profil Türü'nü** **Şablon** olarak seçin.

4. **Şablon adında**, şablon listesinden **Uç nokta koruması'nı** seçin ve ardından **Oluştur'u** seçin.

4. **Endpoint** **protectionBasics'e** >  gidin, profiliniz için bir ad sağlayın ve **İleri'yi** seçin.

5. **Yapılandırma ayarları** bölümünde **Microsoft Defender Exploit Guard** >  **Network filtrelemeSiyaz** >  **korumasıEnable** >  veya **Audit'e** gidin. **İleri**'yi seçin.

6. Kuruluşunuzun gerektirdiği uygun **Kapsam etiketlerini**, **Atamaları** ve **Uygulanabilirlik kurallarını** seçin. Yöneticiler daha fazla gereksinim ayarlayabilir.

7. Tüm bilgileri gözden geçirin ve **oluştur'u** seçin.

### <a name="group-policy"></a>Grup İlkesi

Etki alanına katılmış bilgisayarlarda veya tek başına bir bilgisayarda ağ korumasını etkinleştirmek için aşağıdaki yordamı kullanın.

1. Tek başına bir bilgisayarda **Başlat'a** gidin ve **grup ilkesini düzenle** yazın ve seçin.

    *-Veya-*

    Etki alanına katılmış bir grup ilkesi yönetim bilgisayarında [grup ilkesi Yönetim Konsolu'nu](https://technet.microsoft.com/library/cc731212.aspx) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'yi** seçin.

2. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin ve **Yönetim şablonları'nı** seçin.

3. **Exploit Guard** \> **Ağ koruması** **Windows Defender Microsoft Defender Virüsten Koruma bileşenleri** \> **Windows** \> için ağacı genişletin.

   > [!NOTE]
   > Windows'ın eski sürümlerinde, grup ilkesi yolu "Microsoft Defender Virüsten Koruma" yerine "Windows Defender Virüsten Koruma" diyebilir.

4. **Kullanıcıların ve uygulamaların tehlikeli web sitelerine erişmesini engelle** ayarına çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. Seçenekler bölümünde aşağıdaki seçeneklerden birini belirtmeniz gerekir:
    - **Engelle** - Kullanıcılar kötü amaçlı IP adreslerine ve etki alanlarına erişemez.
    - **Devre dışı bırak (Varsayılan)** - Ağ koruma özelliği çalışmaz. Kullanıcıların kötü amaçlı etki alanlarına erişimi engellenmez.
    - **Denetim Modu** - Kullanıcı kötü amaçlı bir IP adresini veya etki alanını ziyaret ederse, olay Windows olay günlüğüne kaydedilir. Ancak, kullanıcının adresi ziyaret etme engellenmez.

   > [!IMPORTANT]
   > Ağ korumasını tam olarak etkinleştirmek için, grup ilkesi seçeneğini **Etkin** olarak ayarlamanız ve ayrıca seçenekler açılan menüsünde **Engelle'yi** seçmeniz gerekir.

   > [!NOTE]
   > İsteğe bağlı: grup ilkesi ayarlarınızın doğru olduğunu doğrulamak için [Ağ korumasının etkinleştirilip etkinleştirilmediğini denetleme'deki](#check-if-network-protection-is-enabled) adımları izleyin.

### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Uç Noktası Yapılandırma Yöneticisi

1. Configuration Manager konsolunu açın.

2. **Varlıklar ve Uyumluluk** >  **Endpoint Protection Windows Defender** >  **Exploit Guard'a** gidin.

3. Yeni bir ilke oluşturmak için şeritten **Exploit Guard İlkesi Oluştur'u** seçin.
   - Var olan bir ilkeyi düzenlemek için ilkeyi seçin, ardından şeritten veya sağ tıklama menüsünden **Özellikler'i** seçin. **Ağ Koruması sekmesinden Ağ korumasını yapılandır** seçeneğini düzenleyin.  

4. **Genel** sayfasında, yeni ilke için bir ad belirtin ve **Ağ koruması** seçeneğinin etkinleştirildiğini doğrulayın.

5. **Ağ koruması** sayfasında Ağ **korumasını yapılandır** seçeneği için aşağıdaki ayarlardan birini seçin:
   - **Engelle**
   - **Denetim**
   - **Devre dışı**
   
6. Kalan adımları tamamlayın ve ilkeyi kaydedin. 

7. İlkeyi bir koleksiyona dağıtmak için şeritten **Dağıt'ı** seçin.


> [!IMPORTANT]
> bir Exploit Guard ilkesini Configuration Manager dağıttığınızda, dağıtımı kaldırırsanız Exploit Guard ayarları istemcilerden kaldırılmaz. `Delete not supported`, istemcinin Exploit Guard dağıtımını kaldırırsanız Configuration Manager istemcisinin ExploitGuardHandler.log dosyasına kaydedilir. <!--CMADO8538577-->
> Aşağıdaki PowerShell betiği, bu ayarları kaldırmak için SİSTEM bağlamı altında çalıştırılabilir:<!--CMADO9907132-->
>
> ```powershell
> $defenderObject = Get-WmiObject -Namespace "root/cimv2/mdm/dmmap" -Class "MDM_Policy_Config01_Defender02" -Filter "InstanceID='Defender' and ParentID='./Vendor/MSFT/Policy/Config'"
> $defenderObject.AttackSurfaceReductionRules = $null
> $defenderObject.AttackSurfaceReductionOnlyExclusions = $null
> $defenderObject.EnableControlledFolderAccess = $null
> $defenderObject.ControlledFolderAccessAllowedApplications = $null
> $defenderObject.ControlledFolderAccessProtectedFolders = $null
> $defenderObject.EnableNetworkProtection = $null
> $defenderObject.Put()
>
> $exploitGuardObject = Get-WmiObject -Namespace "root/cimv2/mdm/dmmap" -Class "MDM_Policy_Config01_ExploitGuard02" -Filter "InstanceID='ExploitGuard' and ParentID='./Vendor/MSFT/Policy/Config'"
> $exploitGuardObject.ExploitProtectionSettings = $null
> $exploitGuardObject.Put()
>```  

## <a name="see-also"></a>Ayrıca bkz.

- [Ağ koruması](network-protection.md)

- [Ağ koruması ve TCP üç yönlü el sıkışması](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [Ağ korumasını değerlendirin](evaluate-network-protection.md)

- [Ağ koruması sorunlarını giderme](troubleshoot-np.md)
