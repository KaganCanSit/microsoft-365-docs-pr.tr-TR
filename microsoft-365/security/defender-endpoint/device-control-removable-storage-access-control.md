---
title: Uç Nokta için Microsoft Defender Aygıt Denetimi Çıkarılabilir Depolama birimi Access Control, çıkarılabilir depolama medyası
description: Uç Nokta için Microsoft Defender hakkında kılavuz
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.date: 06/24/2022
ms.openlocfilehash: d9ff97aa50a03c1a75f073328a250a9acc3faf54
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490763"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>Uç Nokta için Microsoft Defender Cihaz Denetimi Çıkarılabilir Depolama birimi Access Control

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> Bu ürünün grup ilkesi yönetimi ve Intune OMA-URI/Özel İlke yönetimi genel kullanıma sunuldu (4.18.2106): [Teknik Topluluk blogu: Çıkarılabilir depolama alanınızı ve yazıcınızı Uç Nokta için Microsoft Defender ile koruma](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protect-your-removable-storage-and-printers-with-microsoft/ba-p/2324806).

## <a name="device-control-removable-storage-access-control-overview"></a>Cihaz Denetimi Çıkarılabilir Depolama birimi Access Control Genel Bakış

Uç Nokta için Microsoft Defender Cihaz Denetimi Çıkarılabilir Depolama Birimi Access Control özelliği, dışlamayla veya dışlamadan çıkarılabilir depolama birimine okuma, yazma veya yürütme erişimini denetlemenizi, izin vermenizi veya engellemenizi sağlar.

|Ayrıcalık|Izni|
|---|---|
|Access|Okuma, Yazma, Yürütme|
|Eylem Modu|Denetim, İzin Ver, Engelle|
|CSP Desteği|Evet|
|GPO Desteği|Evet|
|Kullanıcı Tabanlı Destek|Evet|
|Makine Tabanlı Destek|Evet|

Uç Nokta için Microsoft Defender Cihaz Denetimi Çıkarılabilir Depolama Birimi Access Control özelliği size aşağıdaki özellikleri sağlar:

|Yeteneği|Açıklama|Intune aracılığıyla dağıtma|grup ilkesi aracılığıyla dağıtma|
|---|---|---|---|
|Çıkarılabilir Medya Grubu Oluşturma|Yeniden kullanılabilir çıkarılabilir medya grubu oluşturmanıza olanak tanır|Intune [OMA-URI kullanarak Çıkarılabilir Depolama Birimi Access Control Dağıtma](#deploying-removable-storage-access-control-by-using-intune-oma-uri) bölümündeki 4. ve 6. adım| Grup ilkesi [kullanarak Çıkarılabilir Depolama Birimi Dağıtma bölümünde](#deploying-removable-storage-access-control-by-using-group-policy) 4. ve 6. adım Access Control|
|İlke Oluşturma|Her çıkarılabilir medya grubunu zorunlu kılmak için ilke oluşturmanıza olanak tanır|Intune [OMA-URI kullanarak Çıkarılabilir Depolama Birimi Access Control Dağıtma](#deploying-removable-storage-access-control-by-using-intune-oma-uri) bölümündeki 5. ve 7. adım| Grup ilkesi [kullanarak Çıkarılabilir Depolama Birimi dağıtma Access Control](#deploying-removable-storage-access-control-by-using-group-policy) bölümündeki 5. ve 7. adımlar|
|Varsayılan Zorlama|İlke yoksa çıkarılabilir medyaya varsayılan erişimi (Reddet veya İzin Ver) ayarlamanıza izin verir|Intune [OMA-URI kullanarak Çıkarılabilir Depolama Birimi Access Control Dağıtma](#deploying-removable-storage-access-control-by-using-intune-oma-uri) bölümündeki 2. adım | Grup ilkesi [kullanarak Çıkarılabilir Depolama Birimi dağıtma Access Control](#deploying-removable-storage-access-control-by-using-group-policy) bölümündeki 2. adım|
|Çıkarılabilir Depolama birimi Access Control etkinleştirme veya devre dışı bırakma|Devre Dışı Bırak'ı ayarlarsanız, bu makinede Çıkarılabilir Depolama Birimi Access Control ilkesini devre dışı bırakır| Intune [OMA-URI kullanarak Çıkarılabilir Depolama Birimi Access Control Dağıtma](#deploying-removable-storage-access-control-by-using-intune-oma-uri) bölümündeki 1. adım| Grup ilkesi [kullanarak Çıkarılabilir Depolama Birimi dağıtma Access Control](#deploying-removable-storage-access-control-by-using-group-policy) bölümündeki 1. adım|
|Dosya bilgilerini yakalama|Yazma erişimi gerçekleştiğinde dosya bilgilerini yakalamak için ilke oluşturmanıza olanak tanır|  | Grup ilkesi [kullanarak Çıkarılabilir Depolama Birimi Access Control Dağıtma](#deploying-removable-storage-access-control-by-using-group-policy) bölümündeki 10. adım |

### <a name="prepare-your-endpoints"></a>Uç noktalarınızı hazırlama

Kötü amaçlı yazılımdan koruma istemcisi sürümü **4.18.2103.3 veya** üzeri olan Windows 10 ve Windows 11 cihazlarda Çıkarılabilir Depolama Birimi Access Control dağıtın.

- **4.18.2104 veya üzeri**: , , `VID_PID`dosya yolu tabanlı GPO desteği ve `SerialNumberId``ComputerSid`

- **4.18.2105 veya üzeri**: için `HardwareId/DeviceId/InstancePathId/FriendlyNameId/SerialNumberId`joker karakter desteği ekleyin, belirli makinedeki belirli kullanıcının birleşimi, kaldırılabilir SSD (SanDisk Extreme SSD)/USB Bağlı SCSI (UAS) desteği

- **4.18.2107 veya üzeri**: Windows Taşınabilir Cihaz (WPD) desteği ekleme (tabletler gibi mobil cihazlar için); [gelişmiş avlanmaya](device-control-removable-storage-access-control.md#view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint) ekleme `AccountName`

- **4.18.2205 veya üzeri**: Varsayılan zorlamayı **Yazıcı** olarak genişletin. **Bunu Reddet** olarak ayarlarsanız, Yazıcı da engellenir, bu nedenle yalnızca depolama alanını yönetmek istiyorsanız Yazıcı'ya izin vermek için özel bir ilke oluşturduğunuzdan emin olun.

:::image type="content" source="images/powershell.png" alt-text="PowerShell arabirimi" lightbox="images/powershell.png":::

> [!NOTE]
> Windows Güvenliği durumundan bağımsız olarak Çıkarılabilir Depolama Birimi Access Control çalıştırabildiğiniz için Windows Güvenliği bileşenlerin hiçbirinin etkin olmaması gerekir.

## <a name="device-control-removable-storage-access-control-policies"></a>Cihaz Denetimi Çıkarılabilir Depolama Access Control İlkeleri

Çıkarılabilir bir depolama grubu oluşturmak için aşağıdaki özellikleri kullanabilirsiniz:

> [!NOTE]
> XML açıklama gösterimini `<!-- COMMENT -->` kullanan açıklamalar Kural ve Grup XML dosyalarında kullanılabilir, ancak XML dosyasının ilk satırının değil ilk XML etiketinin içinde olmalıdır.

### <a name="removable-storage-group"></a>Çıkarılabilir Depolama Birimi Grubu

|Özellik Adı|Açıklama|Seçenekler|
|---|---|---|
|**Groupıd**|Benzersiz bir kimlik olan GUID, grubu temsil eder ve ilkede kullanılır.||
|**DescriptorIdList**|Grupta ele almak için kullanmak istediğiniz cihaz özelliklerini listeleyin. Her cihaz özelliği için daha fazla ayrıntı için bkz [. Cihaz Özellikleri](device-control-removable-storage-protection.md) . Tüm özellikler büyük/küçük harfe duyarlıdır. |**PrimaryId**: `RemovableMediaDevices`, `CdRomDevices`, `WpdDevices`<p>**BusId**: Örneğin, USB, SCSI<p>**Deviceıd**<p>**HardwareId**<p>**InstancePathId**: InstancePathId, sistemdeki cihazı benzersiz olarak tanımlayan bir dizedir; örneğin, `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0`. Sonundaki sayı (örneğin &0) kullanılabilir yuvayı temsil eder ve cihazdan cihaza değişebilir. En iyi sonuçları elde için sonunda joker karakter kullanın. Örneğin, `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*`.<p>**FriendlyNameId**<p>**SerialNumberId**<p>**VİD**<p>**PID**<p>**VID_PID**<p>`0751_55E0`: bu tam VID/PID çifti eşleştir<p>`_55E0`: HERHANGI bir medyayı PID=55E0 ile eşleştirme <p>`0751_`: VID=0751 ile herhangi bir medyayı eşleştirme|
|**Matchtype**|içinde `DescriptorIDList`kullanılan birden çok cihaz özelliği olduğunda, MatchType ilişkiyi tanımlar.|**MatchAll**: altındaki `DescriptorIdList` tüm öznitelikler **And** ilişkisi olur; örneğin, yönetici bağlı her USB için ve `InstancePathID`eklerse `DeviceID` sistem USB'nin her iki değeri de karşılayıp karşılamadığını denetler. <p> **MatchAny**: DescriptorIdList altındaki öznitelikler **Or** ilişkisi olacaktır; örneğin, yönetici bağlı her USB için ve `InstancePathID`koyarsa`DeviceID`, USB'de aynı **DeviceID** veya **InstanceID** değeri olduğu sürece sistem uygulamayı yapar.|

### <a name="access-control-policy"></a>Access Control İlkesi
Erişim denetimi ilkesini oluşturmak için aşağıdaki özellikleri kullanabilirsiniz:

| Özellik Adı | Açıklama | Seçenekler |
|---|---|---|
| **PolicyRule Kimliği** | Benzersiz bir kimlik olan GUID, ilkeyi temsil eder ve raporlama ve sorun giderme işlemlerinde kullanılır. | |
| **IncludedIdList** | İlkenin uygulanacağı gruplar. Birden çok grup eklenirse, ilke tüm bu gruplardaki herhangi bir medyaya uygulanır.|Bu örnekte Grup Kimliği/GUID kullanılmalıdır. <p> Aşağıdaki örnekte GroupID kullanımı gösterilmektedir: <p> `<IncludedIdList> <GroupId> {EAA4CCE5-F6C9-4760-8BAD-FDCC76A2ACA1}</GroupId> </IncludedIdList>` |
| **ExcludedIDList** | İlkenin uygulanacağı gruplar. | Bu örnekte Grup Kimliği/GUID kullanılmalıdır. |
| **Giriş Kimliği** | Bir PolicyRule birden çok girdiye sahip olabilir; benzersiz GUID'ye sahip her giriş, Cihaz Denetimi'ne bir kısıtlama bildirir.| |
| **Tür** | IncludedIDList içindeki çıkarılabilir depolama grupları için eylemi tanımlar. <p>Zorlama: İzin Ver veya Reddet <p>Denetim: AuditAllowed veya AuditDenied<p> | İzin ver<p>Inkar <p>AuditAllowed: Erişime izin verildiğinde bildirim ve olayı tanımlar <p>AuditDenied: Erişim reddedildiğinde bildirimi ve olayı tanımlar; **Deny** girdisiyle birlikte çalışması gerekir.<p> Aynı medya için çakışma türleri olduğunda, sistem ilkedeki ilki uygular. Çakışma türüne örnek olarak **İzin Ver** ve **Reddet** yer alır. |
| **Sid** | Yerel kullanıcı Sid veya kullanıcı Sid grubu veya AD nesnesinin Sid'i, bu ilkenin belirli bir kullanıcı veya kullanıcı grubuna uygulanıp uygulanmayacağını tanımlar; bir girdi en fazla bir Sid'ye ve Sid içermeyen bir girdi ise ilkenin makineye uygulanması anlamına gelir. |  |
| **ComputerSid** | Yerel bilgisayar Sid veya bilgisayar Sid grubu veya AD nesnesinin Sid'si, bu ilkenin belirli bir makine veya makine grubuna uygulanıp uygulanmayacağını tanımlar; Bir girdi en fazla bir ComputerSid'e ve ComputerSid içermeyen bir girişe sahip olabilir, bu da ilkenin makineye uygulanması anlamına gelir. Belirli bir kullanıcıya ve belirli bir makineye bir Girdi uygulamak istiyorsanız, aynı Girdiye hem Sid hem de ComputerSid ekleyin. |  |
| **Seçenekler** | Bildirimin görüntülenip görüntülenmeyeceğini tanımlar |**İzin Ver Türü seçildiğinde**: <p>0: hiçbir şey<p>4: Bu Giriş için **AuditAllowed** ve **AuditDenied'i** devre dışı bırakın. **Allow** gerçekleşse ve AuditAllowed ayarı yapılandırılmış olsa bile sistem olay göndermez. <p>8: Dosya bilgilerini yakalayın ve Yazma erişimi için kanıt olarak dosyanın bir kopyasını alın. <p>16: Yazma erişimi için dosya bilgilerini yakalayın. <p>**Tür Reddetme seçildiğinde**: <p>0: hiçbir şey<p>4: Bu Giriş için **AuditDenied'i** devre dışı bırakın. **Engelle** gerçekleşse ve AuditDenied ayarı yapılandırılmış olsa bile sistem bildirim göstermez. <p>****AuditAllowed** Türü seçildiğinde**: <p>0: hiçbir şey <p>1: hiçbir şey <p>2: olay gönderme<p> ****AuditDenied** Türü seçildiğinde**: <p>0: hiçbir şey <p>1: bildirimi göster <p>2: olay gönderme<p>3: bildirim gösterme ve olay gönderme |
|Accessmask|Erişimi tanımlar. | **Disk düzeyinde erişim**: <p>1: Okuma <p>2: Yazma <p>4: Yürütme <p>**Dosya sistemi düzeyinde erişim**: <p>8: Dosya sistemi Okuma <p>16: Dosya sistemi Yazma <p>32: Dosya sistemi yürütme <p><p>İkili VEYA işlemi gerçekleştirerek birden çok erişiminiz olabilir; örneğin Okuma ve Yazma ve Yürütme için AccessMask değeri 7 olur; Okuma ve Yazma için AccessMask 3 olacaktır.|

## <a name="device-control-removable-storage-access-control-scenarios"></a>Cihaz Denetimi Çıkarılabilir Depolama Access Control Senaryoları

Çıkarılabilir Depolama Access Control Uç Nokta için Microsoft Defender hakkında bilgi sahibi olmanıza yardımcı olmak için izlemeniz gereken bazı yaygın senaryoları bir araya topladık.

### <a name="scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs"></a>Senaryo 1: Belirli onaylı USB'lere izin vermek dışında tümüne Yazma ve Yürütme erişimini engelleme

1. Grup oluşturma

    1. Grup 1: Herhangi bir çıkarılabilir depolama birimi ve CD/DVD. Çıkarılabilir depolama birimine ve CD/DVD'ye örnek olarak: Grup **9b28fae8-72f7-4267-a1a5-685f747a7146** tüm [Çıkarılabilir Depolama Birimleri ve CD-DVD Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) dosyası.

    2. Grup 2: Cihaz özelliklerine göre onaylı USB'ler. Bu kullanım örneğine örnek: Örnek [Onaylı USB'ler Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) dosyasında Örnek Kimliği - Grup **65fa649a-a111-4912-9294-fb6337a25038**.

    > [!TIP]
    > değerini ile `&amp;` değiştirin`&`.

2. İlke oluşturma

    1. İlke 1: Yazma ve Yürütme Erişimini engelleyin ancak onaylı USB'lere izin verin. Bu kullanım örneğine örnek olarak: Örnek [Senaryo 1 Yazma ve Yürütme Erişiminde](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) PolicyRule **c544a991-5786-4402-949e-a032cb790d0e** ancak onaylı USBs.xmldosyasına izin verir.

    2. İlke 2: İzin verilen USB'lere Yazma ve Yürütme erişimini denetleme. Bu kullanım örneğine örnek olarak: Örnek [Senaryo 1 Denetim Yazma ve Onaylanan USBs.xmldosyasına erişimi yürütme](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) bölümünde PolicyRule **36ae1037-a639-4cff-946b-b36c53089a4c**.

### <a name="scenario-2-audit-write-and-execute-access-to-all-but-block-specific-unapproved-usbs"></a>Senaryo 2: Onaylanmamış belirli USB'leri engellemek dışında tümüne Yazma ve Yürütme erişimini denetleme

1. Grup oluşturma

    1. Grup 1: Herhangi bir çıkarılabilir depolama birimi ve CD/DVD. Bu kullanım örneğine örnek olarak: Grup **9b28fae8-72f7-4267-a1a5-685f747a7146** [örnekteki Herhangi bir Çıkarılabilir Depolama Birimi ve CD-DVD Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) dosyası.

    2. Grup 2: Örnek [Onaylanmamış USB'ler Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) dosyasındaki Cihaz özelliklerine göre onaylanmamış USB'ler, örneğin Satıcı Kimliği / Ürün Kimliği, Kolay Ad - Grup **65fa649a-a111-4912-9294-fb6337a25038**.

    > [!TIP]
    > değerini ile `&amp;` değiştirin`&`.

2. İlke oluşturma

    1. İlke 1: Onaylanmamış belirli USB'ler dışında tümüne Yazma ve Yürütme erişimini engelleyin. Bu kullanım örneğine örnek olarak: Örnek Senaryo 2'de PolicyRule **23b8e437-66ac-4b32-b3d7-24044637fc98** Denetim [Yazma ve Belirli onaylanmamış belirli USBs.xmldosyasını engelleme dışında tümüne erişimi yürütme](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    2. İlke 2: Yazma ve Yürütme erişimini denetleme. Bu kullanım örneğine örnek olarak: Örnek [Senaryo 2 Denetim Yazma ve others.xmldosyasına erişimi yürütme](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) bölümünde PolicyRule **b58ab853-9a6f-405c-a194-740e69422b48**.

## <a name="deploying-and-managing-removable-storage-access-control-by-using-intune-oma-uri"></a>Intune OMA-URI kullanarak Çıkarılabilir Depolama Access Control dağıtma ve yönetme

Çıkarılabilir Depolama Birimi Access Control özelliği, kullanıcıya veya cihaza ya da her ikisine de OMA-URI kullanarak ilke uygulamanızı sağlar.

### <a name="licensing-requirements"></a>Lisans gereksinimleri

Çıkarılabilir Depolama birimi Access Control kullanmaya başlamadan önce [Microsoft 365 aboneliğinizi](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2) onaylamanız gerekir. Çıkarılabilir Depolama birimi Access Control erişmek ve kullanmak için Microsoft 365 E3 veya Microsoft 365 E5 sahip olmanız gerekir.

### <a name="permission"></a>Izni

Intune'da ilke dağıtımı için hesabın cihaz yapılandırma profillerini oluşturma, düzenleme, güncelleştirme veya silme izinleri olmalıdır. Bu izinlerle özel roller oluşturabilir veya yerleşik rollerden herhangi birini kullanabilirsiniz.

- İlke ve profil Yöneticisi rolü
- Cihaz Yapılandırma profilleri için Raporları Oluşturma/Düzenleme/Güncelleştirme/Okuma/Silme/Görüntüleme izinlerinin açık olduğu özel rol
- Genel yönetici

### <a name="deploying-removable-storage-access-control-by-using-intune-oma-uri"></a>Intune OMA-URI kullanarak Çıkarılabilir Depolama birimi Access Control dağıtma

Microsoft Endpoint Manager yönetim merkezine (<https://endpoint.microsoft.com/>) **> Cihazlar'a gidin > Platform: Windows 10 ve üzeri profil oluşturma >, Profil türü: Şablonlar > Özel**

1. Cihaz denetimini aşağıdaki gibi etkinleştirin veya devre dışı bırakın:

   - **Özel > Yapılandırma ayarları'nın** altında **Ekle'ye** tıklayın.
   - **Satır Ekle** bölmesine şunu girin:
     - **Cihaz Denetimini Etkinleştir** olarak **adlandır**
     - **OMA-URI** olarak `./Vendor/MSFT/Defender/Configuration/DeviceControlEnabled`
     - **Tamsayı** Olarak **Veri Türü**
     - **1** olarak **değer**

       `Disable: 0`
       `Enable: 1`

     - **Kaydet**'e tıklayın.

   :::image type="content" source="images/enable-rsac.png" alt-text="Çıkarılabilir Depolama Birimi Access Control ilkesini etkinleştirme işleminin ekran görüntüsü" lightbox="images/enable-rsac.png":::

2. Varsayılan Zorlamayı Ayarla:

   Tüm Cihaz Denetimi özellikleri (, `CdRomDevices`, , `PrinterDevices``WpdDevices`) için varsayılan erişimi (`RemovableMediaDevices`Reddet veya İzin Ver) ayarlayabilirsiniz.

   Örneğin, için `RemovableMediaDevices`**bir Reddet** veya **İzin Ver** ilkeniz vardır, ancak veya `WpdDevices`için `CdRomDevices` bir ilkeniz yoktur. Bu ilke aracılığıyla **Varsayılan Reddetme'yi** ayarlayabilirsiniz, ardından Okuma/Yazma/Yürütme erişimi `CdRomDevices` engellenir veya `WpdDevices` engellenir. Yalnızca depolama alanını yönetmek istiyorsanız yazıcınız için **bir İzin Ver** ilkesi oluşturduğunuzdan emin olun; aksi takdirde, bu varsayılan zorlama yazıcılara da uygulanır.

   - **Satır Ekle** bölmesine şunu girin:
     - **Varsayılan Reddetme** Olarak **Adlandır**
     - **OMA-URI** olarak `./Vendor/MSFT/Defender/Configuration/DefaultEnforcement`
     - **Tamsayı** Olarak **Veri Türü**
     - **1** veya **2** olarak **değer**

       `DefaultEnforcementAllow = 1`
       `DefaultEnforcementDeny = 2`

     - **Kaydet**'e tıklayın.

   :::image type="content" source="images/default-deny.png" alt-text="Varsayılan Zorlama'nın Reddet olarak ayarlanmasının ekran görüntüsü" lightbox="images/default-deny.png":::

3. Varsayılan Reddetmeyi Denetle:

   Varsayılan Reddetme için aşağıdaki gibi bir Denetim ilkesi oluşturabilirsiniz:

   - **Satır Ekle** bölmesine şunu girin:
     - **Varsayılan ReddetmeYi Denetle** Olarak **Adlandır**
     - **OMA-URI** olarak `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bf3520ea7-fd1b-4237-8ebc-96911db44f8e%7d/RuleData`

       :::image type="content" source="images/audit-default-deny-1.png" alt-text="Varsayılan Denetim Reddetme ilkesini oluşturma işleminin ekran görüntüsü" lightbox="images/audit-default-deny-1.png":::

     - **Dize Olarak Veri Türü** **(XML dosyası)**
     - **Denetim Varsayılanı Deny.xml** dosyası olarak **özel XML**.

       XML dosya yolu: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Audit%20Default%20Deny.xml>

       Varsayılan Reddetme için Denetim ilkenizi oluşturmak için aşağıdaki XML verilerini kullanın:

       :::image type="content" source="images/audit-default-deny-xml-file-1.png" alt-text="Varsayılan reddetme xml dosyasını denetle ekran görüntüsü":::

4. ReadOnly - Grup:

   ReadOnly erişimi ile aşağıdaki gibi çıkarılabilir bir depolama grubu oluşturabilirsiniz:

   - **Satır Ekle** bölmesine şunu girin:
     - **Herhangi Bir Çıkarılabilir Depolama Grubu** Olarak **Adlandır**
     - **OMA-URI** olarak `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b9b28fae8-72f7-4267-a1a5-685f747a7146%7d/GroupData`

       :::image type="content" source="images/any-removable-storage-group.png" alt-text="Çıkarılabilir Depolama Birimi Grubu oluşturma işleminin ekran görüntüsü" lightbox="images/any-removable-storage-group.png":::

     - **Dize Olarak Veri Türü** **(XML dosyası)**
       - **Herhangi Bir Çıkarılabilir Depolama Birimi ve CD-DVD ve WPD Group.xml** dosyası olarak **Özel XML**

         XML dosya yolu: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Any%20Removable%20Storage%20and%20CD-DVD%20and%20WPD%20Group.xml>

         ReadOnly erişimiyle 'Herhangi bir Çıkarılabilir Depolama Birimi ve CD-DVD ve WPD Grubu' oluşturmak için aşağıdaki XML verilerini kullanın:

         :::image type="content" source="images/read-only-group-xml-file.png" alt-text="Salt okunur grup xml dosyasının ekran görüntüsü":::

5. ReadOnly - İlke:

   ReadOnly ilkesi oluşturabilir ve okuma etkinliğine izin vermek için bunu ReadOnly çıkarılabilir depolama grubuna aşağıdaki gibi uygulayabilirsiniz:

   - **Satır Ekle** bölmesine şunu girin:
     - **Okuma Etkinliğine İzin Ver** Olarak **Adlandır**
     - **OMA-URI** olarak `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bf7e75634-7eec-4e67-bec5-5e7750cb9e02%7d/RuleData`

       :::image type="content" source="images/allow-read-activity.png" alt-text="Okuma Etkinliğine İzin Ver ilkesinin ekran görüntüsü" lightbox= "images/allow-read-activity.png":::

     - **Dize Olarak Veri Türü** **(XML dosyası)**
     - **Read.xmldosyasına İzin Ver** olarak **Özel XML**

       XML dosya yolu: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Allow%20Read.xml>

       ReadOnly ilkesi oluşturmak ve ReadOnly çıkarılabilir depolama grubuna uygulamak için aşağıdaki XML verilerini kullanın:

       :::image type="content" source="images/read-only-policy-xml-file.png" alt-text="Salt okunur ilke xml dosyasının ekran görüntüsü":::

6. İzin Verilen Medya için Grup Oluşturma: İzin verilen medya grubunuzu aşağıdaki gibi oluşturabilirsiniz:
   - **Satır Ekle** bölmesine şunu girin:
     - **Onaylı USBs Grubu** Olarak **Adlandır**
     - **OMA-URI** olarak `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b65fa649a-a111-4912-9294-fb6337a25038%7d/GroupData`

       :::image type="content" source="images/create-group-allowed-medias.png" alt-text="Onaylı USB'ler grubu oluşturma işleminin ekran görüntüsü" lightbox="images/create-group-allowed-medias.png":::

     - **Dize Olarak Veri Türü** **(XML dosyası)**
     - **Onaylı USB'ler Group.xml** dosyası olarak **özel XML**

       XML dosya yolu: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Approved%20USBs%20Group.xml>

       İzin verilen medya grubu oluşturmak için aşağıdaki XML verilerini kullanın:

       :::image type="content" source="images/create-group-allowed-medias-xml-file.png" alt-text="İzin verilen medias xml dosyası için grup oluşturma işleminin ekran görüntüsü":::

7. Onaylanan USB Grubuna izin vermek için bir ilke oluşturun: Onaylanan USB grubuna aşağıdaki gibi izin vermek için bir ilke oluşturabilirsiniz:
   - **Satır Ekle** bölmesine şunu girin:
     - **Erişime izin ver ve Dosya bilgilerini denetle** olarak **adlandır**
     - **OMA-URI** olarak `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bb2061588-029e-427d-8404-6dfec096a571%7d/RuleData`

       :::image type="content" source="images/allow-access-audit-file-information-1.png" alt-text="Erişim ve denetim dosyası bilgilerine izin ver ekran görüntüsü" lightbox= "images/allow-access-audit-file-information-1.png":::

     - **Dize Olarak Veri Türü** **(XML dosyası)**
     - **Tam erişime ve denetim file.xmldosyasına izin ver** olarak **özel XML**

       XML dosya yolu: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Allow%20full%20access%20and%20audit%20file.xml>

       Onaylanan USB grubuna izin vermek üzere ilke oluşturmak için aşağıdaki XML verilerini kullanın:

       :::image type="content" source="images/create-policy-allow-approved-usb-group-xml-intune.png" alt-text="Onaylanan USB Grubu XML dosyasına izin vermek için ilke oluşturma işleminin ekran görüntüsü":::

       İlkedeki '47' ne anlama geliyor? 9 + 2 + 36 = 47' dır:

       - Okuma erişimi: 1 + 8 = 9.
       - Yazma erişimi: disk düzeyi 2.
       - Yürütme: 4 + 32 = 36.

## <a name="deploying-and-managing-policy-by-using-intune-user-interface"></a>Intune kullanıcı arabirimini kullanarak ilkeyi dağıtma ve yönetme

Bu özellik Microsoft Endpoint Manager yönetim merkezinde (<https://endpoint.microsoft.com/>) kullanılabilir. **Endpoint Security** > **Attack Surface Azaltma** > **Oluşturma İlkesi'ne** gidin. **Profil: Cihaz Denetimi** ile **Platform: Windows 10 ve üzerini** seçin.

## <a name="deploying-and-managing-removable-storage-access-control-by-using-group-policy"></a>Grup ilkesi kullanarak Çıkarılabilir Depolama Access Control dağıtma ve yönetme

Çıkarılabilir Depolama Birimi Access Control özelliği, kullanıcıya veya cihaza ya da her ikisine de grup ilkesi kullanarak bir ilke uygulamanızı sağlar.

### <a name="licensing"></a>Lisanslama

Çıkarılabilir Depolama birimi Access Control kullanmaya başlamadan önce [Microsoft 365 aboneliğinizi](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2) onaylamanız gerekir. Çıkarılabilir Depolama birimi Access Control erişmek ve kullanmak için Microsoft 365 E3 veya Microsoft 365 E5 sahip olmanız gerekir.

### <a name="deploying-removable-storage-access-control-by-using-group-policy"></a>grup ilkesi kullanarak Çıkarılabilir Depolama Birimi Access Control dağıtma

1. Çıkarılabilir Depolama birimi Access Control etkinleştirme veya devre dışı bırakma:

   Cihaz denetimini aşağıdaki gibi etkinleştirebilirsiniz:

   - **Microsoft Defender Virüsten Koruma > Özellikleri > Cihaz Denetimi > Windows Bileşenleri > Bilgisayar Yapılandırması > Yönetim Şablonları'na** gidin
   - **Cihaz Denetimi** penceresinde **Etkin'i** seçin.

   :::image type="content" source="images/enable-rsac-gp.png" alt-text="grup ilkesi kullanarak RSAC'yi etkinleştirme işleminin ekran görüntüsü " lightbox="images/enable-rsac-gp.png":::

2. Varsayılan Zorlamayı Ayarla:

   Tüm Cihaz Denetimi özellikleri (RemovableMediaDevices, CdRomDevices, WpdDevices, PrinterDevices) için varsayılan erişimi (Reddet veya İzin Ver) ayarlayabilirsiniz.

   Örneğin, RemovableMediaDevices için Reddet veya İzin Ver ilkeniz vardır, ancak CdRomDevices veya WpdDevices için herhangi bir ilkeniz yoktur. Bu ilke aracılığıyla Varsayılan Reddetme'yi ayarlarsınız, ardından CdRomDevices veya WpdDevices'e Okuma/Yazma/Yürütme erişimi engellenir. Yalnızca depolamayı yönetmek istiyorsanız, Yazıcı için İzin Ver ilkesi oluşturduğunuzdan emin olun; aksi takdirde, bu Varsayılan Zorlama Yazıcı'ya da uygulanır.

   - **Windows Bileşenleri > Microsoft Defender Virüsten Koruma > Özellikleri > Cihaz Denetimi > Bilgisayar Yapılandırması > Yönetim Şablonları'na gidin > Cihaz Denetimi Varsayılan Zorlama**'>

   - **Cihaz Denetimi Varsayılan Zorlamayı Seç** penceresinde **Varsayılan Reddet'i** seçin:

   :::image type="content" source="images/set-default-enforcement-deny-gp.png" alt-text="Varsayılan Zorlama = grup ilkesi kullanarak reddet ayarının ekran görüntüsü" lightbox="images/set-default-enforcement-deny-gp.png":::

3. Varsayılan Reddetmeyi Denetle:

   Varsayılan Reddetme için Denetim ilkesi oluşturmak için aşağıdaki XML verilerini kullanın:

   :::image type="content" source="images/audit-default-deny-gp.png" alt-text="Varsayılan reddetme xml verilerini denetleme ekran görüntüsü":::

4. ReadOnly - Grup:

   ReadOnly erişimiyle çıkarılabilir depolama grubu oluşturmak için aşağıdaki XML verilerini kullanın:

   :::image type="content" source="images/read-only-group-gp.png" alt-text="Salt okunur çıkarılabilir depolama grubu xml verilerinin ekran görüntüsü":::

5. ReadOnly - İlke:

   ReadOnly ilkesi oluşturmak ve okuma etkinliğine izin vermek için ReadOnly çıkarılabilir depolama grubuna uygulamak için aşağıdaki XML verilerini kullanın:

    :::image type="content" source="images/read-only-policy-gp.png" alt-text="Salt okunur ilke xml verilerinin ekran görüntüsü" lightbox="images/read-only-policy-gp.png":::

6. İzin Verilen Medyalar için Grup Oluştur:

   Çıkarılabilir depolama izin verilen medya grubu oluşturmak için aşağıdaki XML verilerini kullanın:

   :::image type="content" source="images/create-group-allowed-medias-gp.png" alt-text="İzin verilen medyalar için grup oluşturmaya yönelik xml verilerinin ekran görüntüsü" lightbox="images/create-group-allowed-medias-gp.png":::

7. Onaylanan USB Grubuna izin vermek için İlke oluşturun:

   Onaylanan USB grubuna izin verecek bir ilke oluşturmak için aşağıdaki XML verilerini kullanın:

   :::image type="content" source="images/create-policy-allow-approved-usb-group-xml.png" alt-text="onaylanan USB Grubuna grup ilkesi kullanarak izin vermek için ilke oluşturmaya ilişkin XML verilerinin ekran görüntüsü" lightbox="images/create-policy-allow-approved-usb-group-xml.png":::

   İlkedeki '47' ne anlama geliyor? 9 + 2 + 36 = 47' dır:

   - Okuma erişimi: 1+8 = 9.
   - Yazma erişimi: disk düzeyi 2.
   - Yürütme: 4 + 32 = 36.

8. Grupları tek bir XML dosyasında birleştirin:

   Cihaz denetim ilkesi gruplarını tek bir XML dosyasında aşağıdaki gibi birleştirebilirsiniz:

   - **Bilgisayar Yapılandırması** \> **Yönetim Şablonları** \> **Windows Bileşenleri** \> **Microsoft Defender Virüsten Koruma** \> **Cihaz Denetimi** \> **Cihaz denetimi ilke gruplarını tanımlama'ya** gidin.

    :::image type="content" source="images/define-device-control-policy-grps-gp.png" alt-text="Cihaz denetimi ilke gruplarını tanımlama ekran görüntüsü" lightbox="images/define-device-control-policy-grps-gp.png":::

   - **Cihaz denetim ilkesi gruplarını tanımla** penceresinde, XML grupları verilerini içeren dosya yolunu girin.

     XML dosya yolu: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Demo_Groups.xml>

     Cihaz denetim ilkesi grupları xml şeması aşağıdadır:

     :::image type="content" source="images/combine-grps-xml-file-gp.png" alt-text="Grupları tek bir XML dosyasında birleştirme ekran görüntüsü":::

9. İlkeleri tek bir XML dosyasında birleştirin:

   Cihaz denetim ilkesi kurallarını tek bir XML dosyasında aşağıdaki gibi birleştirebilirsiniz:

   - **Microsoft Defender Virüsten Koruma > Cihaz Denetimi > Cihaz denetimi ilke kurallarını tanımlama > Windows Bileşenleri > Bilgisayar Yapılandırması > Yönetim Şablonları'na** gidin

     :::image type="content" source="images/define-device-cntrl-policy-rules-gp.png" alt-text="Cihaz denetimi ilkesi kurallarını tanımlama ekran görüntüsü" lightbox="images/define-device-cntrl-policy-rules-gp.png":::

   - **Cihaz denetimi ilkesi kurallarını tanımla** penceresinde **Etkin'i** seçin ve XML kuralları verilerini içeren dosya yolunu girin.

     XML dosya yolu: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Demo_Policies.xml>

     Cihaz denetim ilkesi kuralları xml şeması aşağıdadır:

    :::image type="content" source="images/combine-policies-xml-gp.png" alt-text="İlkeleri tek bir XML dosyasında birleştirme ekran görüntüsü":::

10. Dosyanın bir kopyası için konum ayarlayın (kanıt):

    Yazma erişimi gerçekleştiğinde dosyanın bir kopyasına (kanıt) sahip olmak istiyorsanız, sistemin kopyayı kaydedebileceği konumu ayarlamanız gerekir.

    - **Microsoft Defender Virüsten Koruma > Cihaz Denetimi > Cihaz Denetimi kanıt verilerini uzak konumu tanımlama > Windows Bileşenleri > Bilgisayar Yapılandırması > Yönetim Şablonları'na** gidin.

    - **Cihaz Denetimi kanıt verilerini uzak konumu tanımla** penceresinde **Etkin'i** seçin ve yerel veya ağ paylaşımı klasör yolunu girin.

      :::image type="content" source="images/evidence-data-remote-location-gp.png" alt-text="Cihaz Denetimi kanıt verilerini uzak konumu tanımlama ekran görüntüsü" lightbox="images/evidence-data-remote-location-gp.png":::

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Cihaz Denetimi Çıkarılabilir Depolama Birimi Access Control verilerini Uç Nokta için Microsoft Defender

[Microsoft 365 Defender portalı](https://security.microsoft.com/advanced-hunting), Cihaz Denetimi Çıkarılabilir Depolama Birimi Access Control tarafından tetiklenen olayları gösterir. Microsoft 365 güvenliğine erişmek için aşağıdaki aboneliğe sahip olmanız gerekir:

- E5 için Microsoft 365 raporlama

```kusto
//RemovableStoragePolicyTriggered: event triggered by Disk level enforcement
DeviceEvents
| where ActionType == "RemovableStoragePolicyTriggered"
| extend parsed=parse_json(AdditionalFields)
| extend RemovableStorageAccess = tostring(parsed.RemovableStorageAccess)
| extend RemovableStoragePolicyVerdict = tostring(parsed.RemovableStoragePolicyVerdict)
| extend MediaBusType = tostring(parsed.BusType)
| extend MediaClassGuid = tostring(parsed.ClassGuid)
| extend MediaClassName = tostring(parsed.ClassName)
| extend MediaDeviceId = tostring(parsed.DeviceId)
| extend MediaInstanceId = tostring(parsed.DeviceInstanceId)
| extend MediaName = tostring(parsed.MediaName)
| extend RemovableStoragePolicy = tostring(parsed.RemovableStoragePolicy)
| extend MediaProductId = tostring(parsed.ProductId)
| extend MediaVendorId = tostring(parsed.VendorId)
| extend MediaSerialNumber = tostring(parsed.SerialNumber)
|project Timestamp, DeviceId, DeviceName, InitiatingProcessAccountName, ActionType, RemovableStorageAccess, RemovableStoragePolicyVerdict, MediaBusType, MediaClassGuid, MediaClassName, MediaDeviceId, MediaInstanceId, MediaName, RemovableStoragePolicy, MediaProductId, MediaVendorId, MediaSerialNumber
| order by Timestamp desc
```

```kusto
//information of file written to removable storage
DeviceEvents
| where ActionType contains "RemovableStorageFileEvent"
| extend parsed=parse_json(AdditionalFields)
| extend Policy = tostring(parsed.Policy)
| extend PolicyRuleId = tostring(parsed.PolicyRuleId)
| extend MediaClassName = tostring(parsed.ClassName)
| extend MediaInstanceId = tostring(parsed.InstanceId)
| extend MediaName = tostring(parsed.MediaName)
| extend MediaProductId = tostring(parsed.ProductId)
| extend MediaVendorId = tostring(parsed.VendorId)
| extend MediaSerialNumber = tostring(parsed.SerialNumber)
| extend FileInformationOperation = tostring(parsed.DuplicatedOperation)
| extend FileEvidenceLocation = tostring(parsed.TargetFileLocation)
| project Timestamp, DeviceId, DeviceName, InitiatingProcessAccountName, ActionType, Policy, PolicyRuleId, FileInformationOperation, MediaClassName, MediaInstanceId, MediaName, MediaProductId, MediaVendorId, MediaSerialNumber, FileName, FolderPath, FileSize, FileEvidenceLocation, AdditionalFields
| order by Timestamp desc
```

:::image type="content" source="images/block-removable-storage.png" alt-text="Çıkarılabilir depolama biriminin engelini gösteren ekran.":::

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="how-to-generate-guid-for-group-idpolicyrule-identry-id"></a>Grup Kimliği/PolicyRule Kimliği/Giriş Kimliği için GUID nasıl oluşturulur?

GUID'yi çevrimiçi açık kaynak veya PowerShell aracılığıyla oluşturabilirsiniz - [PowerShell aracılığıyla GUID oluşturma](/powershell/module/microsoft.powershell.utility/new-guid)

![Görüntü](https://user-images.githubusercontent.com/81826151/159046476-26ea0a21-8087-4f01-b8ae-5aa73b392d8f.png)

### <a name="what-are-the-removable-storage-media-and-policy-limitations"></a>Çıkarılabilir depolama ortamı ve ilke sınırlamaları nelerdir?

Microsoft Endpoint Manager yönetim merkezinden (Intune) veya Microsoft Graph API aracılığıyla arka uç çağrısı OMA-URI (OKUNACAK GET veya GÜNCELLEME YAMASı) aracılığıyla yapılır ve bu nedenle sınırlama, Microsoft'taki XML dosyaları için resmi olarak 350.000 karakter olan OMA-URI özel yapılandırma profiliyle aynıdır.

Örneğin, kullanıcı SID'sinde belirli kullanıcıları "İzin Ver"/"Denetime izin verildi" olarak iki giriş bloğuna ve sonunda "Reddet" tümüne iki giriş bloğuna ihtiyacınız varsa, 2.276 kullanıcıyı yönetebilirsiniz.

### <a name="why-does-the-policy-not-work"></a>İlke neden çalışmıyor?

1. En yaygın neden, gerekli kötü [amaçlı yazılımdan koruma istemcisi sürümü](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control#prepare-your-endpoints) olmamasıdır.

2. Bir diğer neden de XML dosyasının doğru biçimlendirilmemiş olması, örneğin XML dosyasındaki "&" karakteri için doğru markdown biçimlendirmesinin kullanılmaması veya metin düzenleyicisinin dosyaların başına bayt sırası işareti (BOM) 0xEF 0xBB 0xBF eklemesi ve bu da XML ayrıştırma işleminin çalışmaması olabilir. Basit bir çözüm, [örnek dosyayı](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) indirmek ( **Raw'ı** ve sonra **Farklı kaydet'i** seçin) ve ardından güncelleştirmektir.

3. İlkeyi grup ilkesi kullanarak dağıtıp yönetiyorsanız, lütfen tüm PolicyRule'u PolicyRules adlı bir üst düğümdeki tek bir XML dosyasında ve tüm Grup'u Gruplar adlı bir üst düğümde tek bir XML dosyasında birleştirdiğinizden emin olun; Intune aracılığıyla yönetiyorsanız, bir PolicyRule tek XML dosyası, aynı şey, bir Grup bir XML dosyası tutun.

Yine de işe yaramazsa, yöneticiyle cmd çalıştırarak bizimle iletişime geçip destek kabini paylaşmak isteyebilirsiniz: "%programfiles%\Windows Defender\MpCmdRun.exe" -GetFiles

### <a name="there-is-no-configuration-ux-for-define-device-control-policy-groups-and-define-device-control-policy-rules-on-my-group-policy"></a>grup ilkesi 'Cihaz denetim ilkesi gruplarını tanımla' ve 'Cihaz denetim ilkesi kurallarını tanımla' için yapılandırma UX'si yok

grup ilkesi yapılandırma UX'sini geri aktarmayız, ancak [WindowsDefender.adml ve WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) dosyalarında 'Raw' ve 'Farklı Kaydet' öğesine tıklayarak ilgili adml ve [admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx) dosyalarını almaya devam edebilirsiniz.

### <a name="how-can-i-know-whether-the-latest-policy-has-been-deployed-to-the-target-machine"></a>En son ilkenin hedef makineye dağıtılıp dağıtılmadığını nasıl bilebilirim?

PowerShell'de Yönetici olarak "Get-MpComputerStatus" komutunu çalıştırabilirsiniz. Aşağıdaki değer, en son ilkenin hedef makineye uygulanıp uygulanmadığını gösterir.

:::image type="icon" source="images/148609885-bea388a9-c07d-47ef-b848-999d794d24b8.png" border="false":::

### <a name="how-can-i-know-which-machine-is-using-out-of-date-antimalware-client-version-in-the-organization"></a>Kuruluşta hangi makinenin eski kötü amaçlı yazılımdan koruma istemcisi sürümünü kullandığını nasıl öğrenebilirim?

Microsoft 365 güvenlik portalında kötü amaçlı yazılımdan koruma istemcisi sürümünü almak için aşağıdaki sorguyu kullanabilirsiniz:

```kusto
//check the antimalware client version
DeviceFileEvents
|where FileName == "MsMpEng.exe"
|where FolderPath contains @"C:\ProgramData\Microsoft\Windows Defender\Platform\"
|extend PlatformVersion=tostring(split(FolderPath, "\\", 5))
//|project DeviceName, PlatformVersion // check which machine is using legacy platformVersion
|summarize dcount(DeviceName) by PlatformVersion // check how many machines are using which platformVersion
|order by PlatformVersion desc
```
