---
title: Ağ korumasını açma
description: Grup İlkesi, PowerShell veya Mobil Cihaz Yönetimi ve Yapılandırma Yöneticisi ile ağ korumasını etkinleştirin.
keywords: ANetwork protection, exploits, malicious website, ip, domain, domains, enable, turn on
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.date: ''
ms.openlocfilehash: acf474f472450456014a581366c8860d87607a79
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322653"
---
# <a name="turn-on-network-protection"></a>Ağ korumasını açma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Ağ koruması,](network-protection.md) çalışanların kimlik avı dolandırıcılığı, açıklardan yararlanma ve diğer zararlı içerikleri barındırmak için herhangi bir uygulamayı kullanarak kimlik avı dolandırıcılığı, açıkları kullanma ve diğer zararlı içeriklere erişmesini önlemeye yardımcı olur. Bir [test ortamında, etkinleştirmeden](evaluate-network-protection.md) önce engellenmiş olan uygulamaları görüntülemek için ağ korumasını denetleyebilirsiniz.

[Ağ filtreleme yapılandırma seçenekleri hakkında daha fazla bilgi edinmek için:](/mem/intune/protect/endpoint-protection-windows-10#network-filtering)

## <a name="check-if-network-protection-is-enabled"></a>Ağ korumasının etkin olup olduğunu denetleme

Kayıt Defteri Düzenleyicisi'ni kullanarak yerel bir cihazda ağ korumasının etkinleştirildikten sonrasını kontrol edin.

1. Görev çubuğunda **Başlat** düğmesini seçin ve kayıt defteri düzenleyicisini **açmak için regedit** yazın.

2. Yan **HKEY_LOCAL_MACHINE** Seçenekler'i seçin.

3. İç içe menülerde,  \> **MICROSOFT** \>  \> Windows Defender **Windows Defender** \> **Exploit Guard** \> **Ağ Koruması'na gidin**.

Anahtar yoksa, SOFTWARE **Microsoft** \> Windows Defender  \> **Windows Defender** \> **Exploit Guard** **Network Protection'a**\> gidin.

4. Cihazda **ağ korumasının geçerli durumunu görmek için EnableNetworkProtection** öğesini seçin:

   - 0 veya **Kapalı**
   - 1 veya **Açık**
   - 2 veya **Denetim** modu

    :::image type="content" alt-text="Ağ Koruması kayıt defteri anahtarı." source="../../media/95341270-b738b280-08d3-11eb-84a0-16abb140c9fd.png" lightbox="../../media/95341270-b738b280-08d3-11eb-84a0-16abb140c9fd.png":::

## <a name="enable-network-protection"></a>Ağ korumasını etkinleştirme

Şu yöntemlerden herhangi birini kullanarak ağ korumasını etkinleştirin:

- [PowerShell](#powershell)
- [Mobil Cihaz Yönetimi (MDM)](#mobile-device-management-mdm)
- [Microsoft Endpoint Manager](#microsoft-endpoint-manager)
- [Grup İlkesi](#group-policy)
- [Microsoft Uç Noktası Yapılandırma Yöneticisi](#microsoft-endpoint-configuration-manager)

### <a name="powershell"></a>PowerShell

1. **PowerShell yazın ve** Başlat menüsü sağ tıklayın ve **Windows PowerShell Yönetici olarak** **çalıştır'ı seçin**.

2. Aşağıdaki cmdlet'i girin:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection Enabled
    ```

3. İsteğe Bağlı: Aşağıdaki cmdlet'i kullanarak bu özelliği denetim modunda etkinleştirin:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

    Özelliği `Disabled` kapatmak `AuditMode` yerine `Enabled` veya kapatmak için kullanın.

### <a name="mobile-device-management-mdm"></a>Mobil cihaz yönetimi (MDM)

Ağ korumasını etkinleştirmek veya devre dışı bırakmak veya denetim modunu etkinleştirmek için [./Vendor/MSFT/Policy/Config/Defender/EnableNetworkProtection](/windows/client-management/mdm/policy-csp-defender) yapılandırma hizmet sağlayıcısını (CSP) kullanın.

### <a name="microsoft-endpoint-manager"></a>Microsoft Endpoint Manager

1. Microsoft Endpoint Manager yönetim merkezinde ( oturum açmahttps://endpoint.microsoft.com).

2. Cihazlar **Yapılandırma** **profilleriCreate** >  **profili'ne** >  gidin.

3. Profil **oluştur uç menüsünde** **Platform'ı seçin** ve sonra da Şablon **Olarak Profil** **Türü'ne tıklayın**.

4. Şablon **adı'nın** altında, **şablon listesinden** Uç Nokta korumasını seçin ve sonra da Oluştur'a **tıklayın**.

4. Uç nokta **korumasıBasics** >  **seçeneğine** gidin, profiliniz için bir ad girin ve ardından Sonraki'yi **seçin**.

5. Yapılandırma ayarları **bölümünde,** Microsoft Defender Exploit Guard  > **Network filteringNetwork** >  **protectionEnable** >  veya Audit bölümüne gidin. **İleri**'yi seçin.

6. Kurum için **gereken uygun** **Kapsam etiketlerini**, **Ödevler ve** Uygulanabilirlik kurallarını seçin. Yöneticiler daha fazla gereksinimler ayarlamıyor olabilir.

7. Tüm bilgileri gözden geçirerek Oluştur'a **seçin**.

### <a name="group-policy"></a>Grup İlkesi

Etki alanına katılmış bilgisayarlarda veya tek başına bir bilgisayarda ağ korumasını etkinleştirmek için aşağıdaki yordamı kullanın.

1. Tek başına bir bilgisayarda Başlat'a **gidin** ve ardından Grup ilkesi **düzenle'yi seçin**.

    *-Veya-*

    Etki alanına katılmış bir Grup İlkesi yönetim bilgisayarda, Grup İlkesi Yönetim Konsolu'nu [açın, yapılandırmak](https://technet.microsoft.com/library/cc731212.aspx) istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'yi **seçin**.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde** Bilgisayar **yapılandırması'ne gidin ve** Yönetim **şablonları'ı seçin**.

3. **Exploit Guard** \> Ağ **koruması Windows bileşenleri** \> **Microsoft Defender Virüsten Koruma Windows Defender** \> **ağacı genişletin**.

   > [!NOTE]
   > Grup ilkesi yolunun Windows, "grup ilkesi" yerine "Windows Defender Virüsten Koruma" Microsoft Defender Virüsten Koruma.

4. Kullanıcıların ve uygulamaların tehlikeli **web sitelerine erişmesini engelle ayarına çift tıklayın** ve Seçeneği Etkin olarak **ayarlayın**. Seçenekler bölümünde, aşağıdaki seçeneklerden birini belirtebilirsiniz:
    - **Engelle** - Kullanıcılar kötü amaçlı IP adreslerine ve etki alanlarına erişebilirsiniz.
    - **Devre Dışı Bırak (Varsayılan)** - Ağ koruma özelliği çalışmaz. Kullanıcıların kötü amaçlı etki alanlarına erişimi engel olmayacaktır.
    - **Denetim Modu** - Kullanıcı kötü amaçlı bir IP adresini veya etki alanını ziyaret ettiyse, olay günlüğüne Windows kaydedilir. Bununla birlikte, kullanıcının adresi ziyaret etmeleri engel olmayacaktır.

   > [!IMPORTANT]
   > Ağ korumasını tümüyle etkinleştirmek için Grup İlkesi seçeneğini Etkin olarak ayarlamalı ve  ayrıca seçenekler açılan menüsünde  Engelle'yi seçilmelidir.

Kayıt Defteri düzenleyicisini kullanarak yerel bir bilgisayarda ağ korumasının etkinleştirildiğinden onaylayın:

1. Kayıt **Defteri Düzenleyicisi'ni** açmak için **Başlat'ı seçin ve regedit** **yazın**.

2. Gezintiye **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\Windows Defender Exploit Guard\Network Protection\EnableNetworkProtection**

3. **EnableNetworkProtection öğesini seçin** ve değeri onaylayın:
   - 0=Kapalı
   - 1=Açık
   - 2=Denetim

### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Uç Noktası Yapılandırma Yöneticisi

1. Configuration Manager konsolunu açın.

2. Varlıklar ve **Uyumluluk Endpoint Protection** >  **Windows Defender** >  **Exploit Guard'a gidin**. 

3. Yeni **bir ilke oluşturmak için şeritten Exploit Guard** İlkesi Oluştur'a tıklayın.
   - Var olan bir ilkeyi düzenlemek için, ilkeyi seçin ve ardından **şeritten** veya sağ tıklama menüsünden Özellikler'i seçin. Ağ Koruması **sekmesinden** Ağ korumasını yapılandır **seçeneğini** düzenleyin.  

4. Genel **sayfasında** , yeni ilke için bir ad belirtin ve Ağ koruma **seçeneğinin etkinleştirildiğinden** emin olun. 

5. Ağ **koruması sayfasında** , Ağ korumasını yapılandır seçeneği için aşağıdaki **ayarlardan birini** seçin:
   - **Engelle**
   - **Denetim**
   - **Devre dışı**
   
6. Kalan adımları tamamlayın ve ilkeyi kaydedin. 

7. İlkeyi koleksiyona **dağıtmak için** şeritten Dağıt'ı seçin.

> [!IMPORTANT]
> Configuration Manager'dan bir Exploit Guard ilkesi dağıtın, dağıtımı kaldırsanız bile Exploit Guard ayarları istemcilerden kaldırılamaz. `Delete not supported` , istemcinin Exploit Guard dağıtımını kaldırırsanız Configuration Manager istemcisinin ExploitGuardHandler.log dosyasına kaydedilir. <!--CMADO8538577-->
> Bu ayarları kaldırmak için SYSTEM bağlamı altında aşağıdaki PowerShell betiği çalıştırabilirsiniz:<!--CMADO9907132-->
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

- [Ağ koruması ve TCP üç yol el sıkışması](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [Ağ korumasını değerlendirme](evaluate-network-protection.md)

- [Ağ koruması sorunlarını giderme](troubleshoot-np.md)
