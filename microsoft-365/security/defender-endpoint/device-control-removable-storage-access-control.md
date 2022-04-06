---
title: Uç Nokta için Microsoft Defender Cihaz Denetimi Çıkarılabilir Depolama Access Control, çıkarılabilir depolama medyası
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
ms.date: 03/18/2022
ms.openlocfilehash: 03efd5f8681824b5625611e0c8c871bfc7fd03a6
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665150"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>Uç Nokta için Microsoft Defender Cihaz Denetimi Çıkarılabilir Depolama Access Control

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> Bu ürünün grup ilkesi yönetimi ve Intune OMA-URI/Özel İlke yönetimi artık genel kullanıma sunuldu (4.18.2106): [Teknik Community blogu: Çıkarılabilir depolama alanınızı ve yazıcınızı Uç Nokta için Microsoft Defender ile koruma](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protect-your-removable-storage-and-printers-with-microsoft/ba-p/2324806).

Uç Nokta için Microsoft Defender Cihaz Denetimi Çıkarılabilir Depolama Access Control aşağıdaki görevi gerçekleştirmenizi sağlar:

- dışlama ile veya hariç tutmadan çıkarılabilir depolama birimine okuma, yazma veya yürütme erişimine izin verme veya erişimi engelleme

|Ayrıcalık|Izni|
|---|---|
|Access|Okuma, Yazma, Yürütme|
|Eylem Modu|Denetim, İzin Ver, Engelle|
|CSP Desteği|Evet|
|GPO Desteği|Evet|
|Kullanıcı Tabanlı Destek|Evet|
|Makine Tabanlı Destek|Evet|

|Yeteneği|Açıklama|Intune aracılığıyla dağıtma|grup ilkesi aracılığıyla dağıtma|
|---|---|---|---|
|Çıkarılabilir Medya Grubu Oluşturma|Yeniden kullanılabilir çıkarılabilir medya grubu oluşturmanıza olanak tanır|[OMA-URI aracılığıyla ilke dağıtma](#deploying-policy-via-oma-uri) bölümündeki 1. adım | grup ilkesi [aracılığıyla ilke dağıtma](#deploying-policy-via-group-policy) bölümündeki 1. adım|
|İlke Oluşturma|Her çıkarılabilir medya grubunu zorunlu kılmak için ilke oluşturmanıza olanak tanır|[OMA-URI aracılığıyla ilke dağıtma](#deploying-policy-via-oma-uri) bölümündeki 2. adım | grup ilkesi [aracılığıyla ilke dağıtma](#deploying-policy-via-group-policy) bölümündeki 2. ve 3. adımlar |
|Varsayılan Zorlama|İlke yoksa çıkarılabilir medyaya varsayılan erişimi (Reddet veya İzin Ver) ayarlamanıza izin verir|[OMA-URI aracılığıyla ilke dağıtma](#deploying-policy-via-oma-uri) bölümündeki 3. adım | grup ilkesi [aracılığıyla ilke dağıtma](#deploying-policy-via-group-policy) bölümünde 4. adım |
|Çıkarılabilir Depolama Access Control Etkinleştirme veya Devre Dışı Bırakma|Devre dışı bırak'ı ayarlarsanız, bu makinede Çıkarılabilir Depolama Access Control ilkesini devre dışı bırakır| [OMA-URI aracılığıyla ilke dağıtma](#deploying-policy-via-oma-uri) bölümünde 4. adım | grup ilkesi [aracılığıyla ilke dağıtma](#deploying-policy-via-group-policy) bölümündeki 5. adım |
|Dosya bilgilerini yakalama|Yazma erişimi gerçekleştiğinde dosya bilgilerini yakalamak için ilke oluşturmanıza olanak tanır| [OMA-URI aracılığıyla ilke dağıtma](#deploying-policy-via-oma-uri) bölümündeki 2. ve 5. adımlar | grup ilkesi [aracılığıyla ilke dağıtma](#deploying-policy-via-group-policy) bölümünde 2. ve 6. adım |

## <a name="prepare-your-endpoints"></a>Uç noktalarınızı hazırlama

Kötü amaçlı yazılımdan koruma istemcisi sürümü **4.18.2103.3 veya** üzeri olan Windows 10 ve Windows 11 cihazlarda Çıkarılabilir Depolama Access Control dağıtın.

- **4.18.2104 veya üzeri**: SerialNumberId, VID_PID, dosya yolu tabanlı GPO desteği, ComputerSid ekleme

- **4.18.2105 veya üzeri**: HardwareId/DeviceId/InstancePathId/FriendlyNameId/SerialNumberId için joker karakter desteği ekleme, belirli makinedeki belirli bir kullanıcının birleşimi, kaldırılabilir SSD (SanDisk Extreme SSD)/USB Bağlı SCSI (UAS) desteği

- **4.18.2107 veya üzeri**: Windows Taşınabilir Cihaz (WPD) desteği ekleyin (tabletler gibi mobil cihazlar için); [AccountName'i gelişmiş avlanmaya](device-control-removable-storage-access-control.md#view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint) ekleyin

:::image type="content" source="images/powershell.png" alt-text="PowerShell arabirimi" lightbox="images/powershell.png":::

> [!NOTE]
> Windows Güvenliği durumundan bağımsız olarak Çıkarılabilir Depolama Access Control çalıştırabildiğiniz için Windows Güvenliği bileşenlerin hiçbirinin etkin olmaması gerekir.

## <a name="policy-properties"></a>İlke özellikleri

Çıkarılabilir bir depolama grubu oluşturmak için aşağıdaki özellikleri kullanabilirsiniz:

> [!NOTE]
> XML açıklama gösterimini `<!-- COMMENT -->` kullanan açıklamalar Kural ve Grup XML dosyalarında kullanılabilir, ancak XML dosyasının ilk satırının değil ilk XML etiketinin içinde olmalıdır.

### <a name="removable-storage-group"></a>Çıkarılabilir Depolama Grubu

|Özellik Adı|Açıklama|Seçenekler|
|---|---|---|
|**Grup Kimliği**|Benzersiz bir kimlik olan GUID, grubu temsil eder ve ilkede GroupId olarak kullanılır||
|**DescriptorIdList**|Grupta ele almak için kullanmak istediğiniz cihaz özelliklerini listeleyin. Her cihaz özelliği için daha fazla ayrıntı için bkz [. Cihaz Özellikleri](device-control-removable-storage-protection.md) . Tüm özellikler büyük/küçük harfe duyarlıdır. |**PrimaryId**: `RemovableMediaDevices`, `CdRomDevices`, `WpdDevices`<p>**BusId**: Örneğin, USB, SCSI<p>**Deviceıd**<p>**HardwareId**<p>**InstancePathId**: InstancePathId, sistemdeki cihazı benzersiz olarak tanımlayan bir dizedir; örneğin, `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0`. Sonundaki sayı (örneğin &0) kullanılabilir yuvayı temsil eder ve cihazdan cihaza değişebilir. En iyi sonuçları elde için sonunda joker karakter kullanın. Örneğin, `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*`.<p>**FriendlyNameId**<p>**SerialNumberId**<p>**VİD**<p>**PID**<p>**VID_PID**<p>`0751_55E0`: bu tam VID/PID çifti eşleştir<p>`_55E0`: HERHANGI bir medyayı PID=55E0 ile eşleştirme <p>`0751_`: VID=0751 ile herhangi bir medyayı eşleştirme|
|**Matchtype**|içinde `DescriptorIDList`kullanılan birden çok cihaz özelliği olduğunda, MatchType ilişkiyi tanımlar.|**MatchAll**: altındaki `DescriptorIdList` tüm öznitelikler **And** ilişkisi olur; örneğin, yönetici bağlı her USB için ve `InstancePathID`eklerse `DeviceID` sistem USB'nin her iki değeri de karşılayıp karşılamadığını denetler. <p> **MatchAny**: DescriptorIdList altındaki öznitelikler **Or** ilişkisi olacaktır; örneğin, yönetici bağlı her USB için ve `InstancePathID`koyarsa`DeviceID`, USB'de aynı **DeviceID** veya **InstanceID** değeri olduğu sürece sistem uygulamayı yapar. |

### <a name="access-control-policy"></a>Access Control İlkesi

| Özellik Adı | Açıklama | Seçenekler |
|---|---|---|
| **PolicyRule Kimliği** | Benzersiz bir kimlik olan GUID, ilkeyi temsil eder ve raporlama ve sorun giderme işlemlerinde kullanılır. | |
| **IncludedIdList** | İlkenin uygulanacağı gruplar. Birden çok grup eklenirse, ilke tüm bu gruplardaki herhangi bir medyaya uygulanır.|Bu örnekte Grup Kimliği/GUID kullanılmalıdır. <p> Aşağıdaki örnekte GroupID kullanımı gösterilmektedir: <p> `<IncludedIdList> <GroupId> {EAA4CCE5-F6C9-4760-8BAD-FDCC76A2ACA1}</GroupId> </IncludedIdList>` |
| **ExcludedIDList** | İlkenin uygulanacağı gruplar. | Bu örnekte Grup Kimliği/GUID kullanılmalıdır. |
| **Giriş Kimliği** | Bir PolicyRule birden çok girdiye sahip olabilir; benzersiz GUID'ye sahip her giriş, Cihaz Denetimi'ne bir kısıtlama bildirir.| |
| **Tür** | IncludedIDList içindeki çıkarılabilir depolama grupları için eylemi tanımlar. <p>Zorlama: İzin Ver veya Reddet <p>Denetim: AuditAllowed veya AuditDenied<p> | İzin ver<p>Inkar <p>AuditAllowed: Erişime izin verildiğinde bildirim ve olayı tanımlar <p>AuditDenied: Erişim reddedildiğinde bildirimi ve olayı tanımlar; **Deny** girdisiyle birlikte çalışması gerekir.<p> Aynı medya için çakışma türleri olduğunda, sistem ilkedeki ilki uygular. Çakışma türüne örnek olarak **İzin Ver** ve **Reddet** yer alır. |
| **Sid** | Yerel kullanıcı Sid veya kullanıcı Sid grubu veya AD nesnesinin Sid'i, bu ilkenin belirli bir kullanıcı veya kullanıcı grubuna uygulanıp uygulanmayacağını tanımlar; bir girdi en fazla bir Sid'ye ve Sid içermeyen bir girdi ise ilkenin makineye uygulanması anlamına gelir. |  |
| **ComputerSid** | Yerel bilgisayar Sid veya bilgisayar Sid grubu veya AD nesnesinin Sid'si, bu ilkenin belirli bir makine veya makine grubuna uygulanıp uygulanmayacağını tanımlar; Bir girdi en fazla bir ComputerSid'e ve ComputerSid içermeyen bir girişe sahip olabilir, bu da ilkenin makineye uygulanması anlamına gelir. Belirli bir kullanıcıya ve belirli bir makineye bir Girdi uygulamak istiyorsanız, aynı Girdiye hem Sid hem de ComputerSid ekleyin. |  |
| **Seçenekler** | Bildirimin görüntülenip görüntülenmeyeceğini tanımlar |**İzin Ver Türü seçildiğinde**: <p>0: hiçbir şey<p>4: Bu Giriş için **AuditAllowed** ve **AuditDenied'i** devre dışı bırakın. **Allow** gerçekleşse ve AuditAllowed ayarı yapılandırılmış olsa bile sistem olay göndermez. <p>8: Dosya bilgilerini yakalayın ve Yazma erişimi için kanıt olarak dosyanın bir kopyasını alın. <p>16: Yazma erişimi için dosya bilgilerini yakalayın. <p>**Tür Reddetme seçildiğinde**: <p>0: hiçbir şey<p>4: Bu Giriş için **AuditDenied'i** devre dışı bırakın. **Engelle** gerçekleşse ve AuditDenied ayarı yapılandırılmış olsa bile sistem bildirim göstermez. <p>****AuditAllowed** Türü seçildiğinde**: <p>0: hiçbir şey <p>1: hiçbir şey <p>2: olay gönderme<p>3: olay gönderme <p> ****AuditDenied** Türü seçildiğinde**: <p>0: hiçbir şey <p>1: bildirimi göster <p>2: olay gönderme<p>3: bildirim gösterme ve olay gönderme |
|Accessmask|Erişimi tanımlar. | **Disk düzeyinde erişim**: <p>1: Okuma <p>2: Yazma <p>4: Yürütme <p>**Dosya sistemi düzeyinde erişim**: <p>8: Dosya sistemi Okuma <p>16: Dosya sistemi Yazma <p>32: Dosya sistemi yürütme <p><p>İkili VEYA işlemi gerçekleştirerek birden çok erişiminiz olabilir; örneğin Okuma ve Yazma ve Yürütme için AccessMask değeri 7 olur; Okuma ve Yazma için AccessMask 3 olacaktır.|

## <a name="common-removable-storage-access-control-scenarios"></a>Yaygın Çıkarılabilir Depolama Access Control senaryoları

Çıkarılabilir Depolama Access Control Uç Nokta için Microsoft Defender hakkında bilgi sahibi olmanıza yardımcı olmak için izlemeniz gereken bazı yaygın senaryoları bir araya topladık.

### <a name="scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs"></a>Senaryo 1: Belirli onaylı USB'lere izin vermek dışında tümüne Yazma ve Yürütme erişimini engelleme

1. Grup oluşturma

    1. Grup 1: Herhangi bir çıkarılabilir depolama birimi ve CD/DVD. Çıkarılabilir depolama birimi ve CD/DVD örneği: Grup **9b28fae8-72f7-4267-a1a5-685f747a7146** [örnekteki Tüm Çıkarılabilir Depolama ve CD-DVD Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) dosyası.

    2. Grup 2: Cihaz özelliklerine göre onaylı USB'ler. Bu kullanım örneğine örnek: Örnek [Onaylı USB'ler Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) dosyasında Örnek Kimliği - Grup **65fa649a-a111-4912-9294-fb6337a25038**.

    > [!TIP]
    > değerini ile `&amp;` değiştirin`&`.

2. İlke oluşturma

    1. İlke 1: Yazma ve Yürütme Erişimini engelleyin ancak onaylı USB'lere izin verin. Bu kullanım örneğine örnek olarak: Örnek [Senaryo 1 Yazma ve Yürütme Erişiminde](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) PolicyRule **c544a991-5786-4402-949e-a032cb790d0e** ancak onaylı USBs.xmldosyasına izin verir.

    2. İlke 2: İzin verilen USB'lere Yazma ve Yürütme erişimini denetleme. Bu kullanım örneğine örnek olarak: Örnek [Senaryo 1 Denetim Yazma ve Onaylanan USBs.xmldosyasına erişimi yürütme](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) bölümünde PolicyRule **36ae1037-a639-4cff-946b-b36c53089a4c**.

### <a name="scenario-2-audit-write-and-execute-access-to-all-but-block-specific-unapproved-usbs"></a>Senaryo 2: Onaylanmamış belirli USB'leri engellemek dışında tümüne Yazma ve Yürütme erişimini denetleme

1. Grup oluşturma

    1. Grup 1: Herhangi bir çıkarılabilir depolama birimi ve CD/DVD. Bu kullanım örneğine örnek olarak: Grup **9b28fae8-72f7-4267-a1a5-685f747a7146** [örnekteki Tüm Çıkarılabilir Depolama ve CD-DVD Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) dosyası.

    2. Grup 2: Örnek [Onaylanmamış USB'ler Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) dosyasındaki Cihaz özelliklerine göre onaylanmamış USB'ler, örneğin Satıcı Kimliği / Ürün Kimliği, Kolay Ad – Grup **65fa649a-a111-4912-9294-fb6337a25038**.

    > [!TIP]
    > değerini ile `&amp;` değiştirin`&`.

2. İlke oluşturma

    1. İlke 1: Onaylanmamış belirli USB'ler dışında tümüne Yazma ve Yürütme erişimini engelleyin. Bu kullanım örneğine örnek olarak: Örnek Senaryo 2'de PolicyRule **23b8e437-66ac-4b32-b3d7-24044637fc98** Denetim [Yazma ve Belirli onaylanmamış belirli USBs.xmldosyasını engelleme dışında tümüne erişimi yürütme](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    2. İlke 2: Yazma ve Yürütme erişimini denetleme. Bu kullanım örneğine örnek olarak: Örnek [Senaryo 2 Denetim Yazma ve others.xmldosyasına erişimi yürütme](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) bölümünde PolicyRule **b58ab853-9a6f-405c-a194-740e69422b48**.

## <a name="deploying-and-managing-policy-via-group-policy"></a>grup ilkesi aracılığıyla ilke dağıtma ve yönetme

Çıkarılabilir Depolama Access Control özelliği, ilkeyi grup ilkesi aracılığıyla kullanıcıya veya cihaza ya da her ikisine de uygulamanızı sağlar.

### <a name="licensing"></a>Lisanslama

Çıkarılabilir Depolama Access Control kullanmaya başlamadan önce [Microsoft 365 aboneliğinizi](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2) onaylamanız gerekir. Çıkarılabilir Depolama Access Control erişmek ve kullanmak için Microsoft 365 E3 veya Microsoft 365 E5 sahip olmanız gerekir.

### <a name="deploying-policy-via-group-policy"></a>grup ilkesi aracılığıyla ilke dağıtma

1. İçindeki `<Groups>` `</Groups>` tüm grupları tek bir xml dosyasında birleştirin.

    Aşağıdaki görüntüde [Senaryo 1: Belirli onaylı USB'lere izin vermek dışında tümüne Yazma ve Yürütme erişimini engelleme örneği gösterilmektedir](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs).

    :::image type="content" source="images/prevent-write-access-allow-usb.png" alt-text="Cihazlarda belirli onaylı USB'lere izin veren yapılandırma ayarları" lightbox="images/prevent-write-access-allow-usb.png":::

2. İçindeki `<PolicyRules>` `</PolicyRules>` tüm kuralları tek bir xml dosyasında birleştirin.

    Belirli bir kullanıcıyı kısıtlamak istiyorsanız, Girdide SID özelliğini kullanın. İlke Girdisinde SID yoksa, Giriş makine için herkes oturum açma örneğine uygulanır.

    Yazma erişimi için dosya bilgilerini izlemek istiyorsanız, doğru Seçenek (16) ile doğru AccessMask'i kullanın; Burada [Yakalama dosyası bilgileri](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Audit%20File%20Information.xml) örneği verilmiştir.

    Aşağıdaki görüntüde SID özelliğinin kullanımı ve [Senaryo 1:Yazma ve Yürütme erişimini engelleme ancak onaylanan belirli USB'lere izin verme örneği gösterilmektedir](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs).

    :::image type="content" source="images/usage-sid-property.png" alt-text="SID özellik özniteliğinin kullanımını gösteren kod" lightbox="images/usage-sid-property.png":::

3. Hem kural hem de grup XML dosyalarını ağ paylaşımı klasörüne kaydedin ve ağ paylaşımı klasör yolunu grup ilkesi ayarına yerleştirin: **Bilgisayar Yapılandırması** \> **Yönetim Şablonları** \> **Windows Bileşenler** \> **Microsoft Defender Virüsten Koruma** \> **Cihaz Denetimi**: **'Cihaz denetim ilkesi gruplarını tanımla'** ve **'Cihaz denetimi ilkesi kurallarını tanımla'**.

   İlke yapılandırması UX'sini grup ilkesi bulamazsanız Ham'ı seçip  Farklı **kaydet'i** seçerek [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) ve [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx) dosyalarını indirebilirsiniz.

   - İlkeye sahip olmak için hedef makinenin ağ paylaşımına erişebilmesi gerekir. Ancak, ilke okunduktan sonra, makine yeniden başlatıldıktan sonra bile ağ paylaşımı bağlantısı gerekmez.

    :::image type="content" source="images/device-control.png" alt-text="Cihaz Denetimi ekranı" lightbox="images/device-control.png":::

4. Varsayılan zorlama: İlke yoksa çıkarılabilir medyaya varsayılan erişimi (Reddet veya İzin Ver) ayarlamanıza olanak tanır. Örneğin, Yalnızca RemovableMediaDevices için ilkeniz (Reddet veya İzin Ver) vardır, ancak CdRomDevices veya WpdDevices için herhangi bir ilkeniz yoktur ve bu ilke aracılığıyla varsayılan Reddet'i ayarlarsınız; CdRomDevices veya WpdDevices'e Okuma/Yazma/Yürütme erişimi engellenir.

   - Bu ayarı dağıttığınızda **Varsayılan İzin Ver** veya **Varsayılan Reddetme** seçeneğini görürsünüz.
   - Bu ayarı yapılandırırken hem Disk düzeyi hem de Dosya sistemi düzeyi AccessMask'i göz önünde bulundurun. Örneğin, Varsayılan Reddetme'yi istiyor ancak belirli bir depolamaya izin vermek istiyorsanız, hem Disk düzeyinde hem de Dosya sistemi düzeyinde erişime izin vermelisiniz; AccessMask'i 63 olarak ayarlamanız gerekir.

    :::image type="content" source="images/148609579-a7df650b-7792-4085-b552-500b28a35885.png" alt-text="Varsayılan İzin Ver veya Varsayılan PowerShell kodunu reddet":::

5. Çıkarılabilir Depolama Access Control Etkinleştir veya Devre Dışı Bırak: Bu değeri Çıkarılabilir Depolama Access Control geçici olarak devre dışı bırakacak şekilde ayarlayabilirsiniz.

    :::image type="content" source="images/148608318-5cda043d-b996-4146-9642-14fccabcb017.png" alt-text="Cihaz Denetimi ayarları":::

   - Bu ayarı dağıttığınızda **Etkin** veya **Devre Dışı** ifadesini görürsünüz. Devre dışı, bu makinenin Çıkarılabilir Depolama Access Control ilkesinin çalışmadığı anlamına gelir.

    :::image type="content" source="images/148609685-4c05f002-5cbe-4aab-9245-83e730c5449e.png" alt-text="PowerShell kodunda etkin veya Devre dışı cihaz denetimi":::

6. Dosyanın bir kopyasının konumunu ayarlayın: Yazma erişimi gerçekleştiğinde dosyanın bir kopyasına sahip olmak istiyorsanız, sistemin kopyayı kaydedebileceği konumu ayarlamanız gerekir.

    Bunu doğru AccessMask ve Option ile birlikte dağıtın. Yukarıdaki 2. adıma bakın.

    :::image type="content" source="../../media/define-device-control-policy-rules.png" alt-text="grup ilkesi - Dosya kanıtı için locaiton ayarlama":::

## <a name="deploying-and-managing-policy-via-intune-oma-uri"></a>Intune OMA-URI aracılığıyla ilke dağıtma ve yönetme

Çıkarılabilir Depolama Access Control özelliği, kullanıcıya veya cihaza ya da her ikisine de OMA-URI aracılığıyla ilke uygulamanızı sağlar.

### <a name="licensing-requirements"></a>Lisans gereksinimleri

Çıkarılabilir Depolama Access Control kullanmaya başlamadan önce [Microsoft 365 aboneliğinizi](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2) onaylamanız gerekir. Çıkarılabilir Depolama Access Control erişmek ve kullanmak için Microsoft 365 E3 veya Microsoft 365 E5 sahip olmanız gerekir.

### <a name="permission"></a>Izni

Intune'da ilke dağıtımı için hesabın cihaz yapılandırma profillerini oluşturma, düzenleme, güncelleştirme veya silme izinleri olmalıdır. Bu izinlerle özel roller oluşturabilir veya yerleşik rollerden herhangi birini kullanabilirsiniz.

- İlke ve profil Yöneticisi rolü

- Cihaz Yapılandırma profilleri için Raporları Oluşturma/Düzenleme/Güncelleştirme/Okuma/Silme/Görüntüleme izinlerinin açık olduğu özel rol

- Genel yönetici

### <a name="deploying-policy-via-oma-uri"></a>OMA-URI aracılığıyla ilke dağıtma

Microsoft Endpoint Manager yönetim merkezi (<https://endpoint.microsoft.com/>) \> **Cihaz** \> **Yapılandırma profilleri** \> **Profil** \> **platformu oluşturma: Windows 10 ve üzeri & Profili: Özel**

1. Her Grup için bir OMA-URI kuralı oluşturun:

    - OMA-URI:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b**GroupGUID**%7d/GroupData`

      Örneğin, **örnekteki çıkarılabilir depolama birimleri ve CD/DVD** grupları için bağlantı şu şekilde olmalıdır:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b9b28fae8-72f7-4267-a1a5-685f747a7146%7d/GroupData`

    - Veri Türü: Dize (XML dosyası)

      :::image type="content" source="images/xml-data-type-string.png" alt-text="Satır Ekle sayfasındaki Veri türü alanı" lightbox="images/xml-data-type-string.png":::

2. Her ilke için bir OMA-URI de oluşturun:

    - OMA-URI:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7b**PolicyRuleGUID**%7d/RuleData`

      Örneğin, **Yazma ve Yürütme Erişimini Engelle ancak örnekte onaylanan USB'lere izin ver** kuralı için bağlantı şu şekilde olmalıdır:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bc544a991-5786-4402-949e-a032cb790d0e%7d/RuleData`

    - Veri Türü: Dize (XML dosyası)

    Yazma erişimi için dosya bilgilerini izlemek istiyorsanız, doğru Seçenek (16) ile doğru AccessMask'i kullanın; Burada [Yakalama dosyası bilgileri](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Audit%20File%20Information.xml) örneği verilmiştir.

3. Varsayılan zorlama: İlke yoksa çıkarılabilir medyaya varsayılan erişimi (Reddet veya İzin Ver) ayarlamanıza olanak tanır. Örneğin, Yalnızca RemovableMediaDevices için ilkeniz (Reddet veya İzin Ver) vardır, ancak CdRomDevices veya WpdDevices için herhangi bir ilkeniz yoktur ve bu ilke aracılığıyla varsayılan Reddet'i ayarlarsınız; CdRomDevices veya WpdDevices'e Okuma/Yazma/Yürütme erişimi engellenir.

    - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DefaultEnforcement`

    - Veri Türü: Int

      `DefaultEnforcementAllow = 1`
      `DefaultEnforcementDeny = 2`

    - Bu ayarı dağıttığınızda **Varsayılan İzin Ver** veya **Varsayılan Reddetme'yi** görürsünüz
    - Bu ayarı yapılandırırken hem Disk düzeyi hem de Dosya sistemi düzeyi AccessMask'i göz önünde bulundurun. Örneğin, Varsayılan Reddetme'yi istiyor ancak belirli bir depolamaya izin vermek istiyorsanız, hem Disk düzeyinde hem de Dosya sistemi düzeyinde erişime izin vermelisiniz; AccessMask'i 63 olarak ayarlamanız gerekir.

    :::image type="content" source="images/148609590-c67cfab8-8e2c-49f8-be2b-96444e9dfc2c.png" alt-text="Varsayılan Zorlama PowerShell koduna izin ver":::

4. Çıkarılabilir Depolama Access Control Etkinleştir veya Devre Dışı Bırak: Bu değeri Çıkarılabilir Depolama Access Control geçici olarak devre dışı bırakacak şekilde ayarlayabilirsiniz.

   - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DeviceControlEnabled`

   - Veri Türü: Int `Disable: 0`
     `Enable: 1`

   - Bu ayarı dağıttığınızda **Etkin** veya **Devre Dışı** ifadesini görürsünüz

    **Devre dışı,** bu makinenin Çalıştırılan Çıkarılabilir Depolama Access Control ilkesi olmadığı anlamına gelir

    :::image type="content" source="images/148609770-3e555883-f26f-45ab-9181-3fb1ff7a38ac.png" alt-text="PowerShell kodunda kaldırılabilir Depolama Access Control":::

5. Dosyanın bir kopyasının konumunu ayarlayın: Yazma erişimi gerçekleştiğinde dosyanın bir kopyasına sahip olmak istiyorsanız, sistemin kopyayı kaydedebileceği konumu ayarlamanız gerekir.

    - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DataDuplicationRemoteLocation;**username**;**password**`

    - Veri Türü: Dize

    Bunu doğru AccessMask ve doğru Seçenek ile birlikte dağıtmanız gerekir. Yukarıdaki 2. adıma bakın.

    :::image type="content" source="../../media/device-control-oma-uri-edit-row.png" alt-text="Dosya kanıtı için locaiton ayarlama":::

## <a name="deploying-and-managing-policy-by-using-intune-user-interface"></a>Intune kullanıcı arabirimini kullanarak ilkeyi dağıtma ve yönetme

(*Çok yakında!*) Bu özellik Microsoft Endpoint Manager yönetim merkezinde (<https://endpoint.microsoft.com/>) kullanılabilir. **Endpoint SecurityAttack** >  **Surface ReductionCreate** >  **policy (İlke Oluştur) seçeneğine** gidin. **Profil: Cihaz Denetimi** ile **Platform: Windows 10 ve üzerini** seçin.

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Cihaz Denetimi Çıkarılabilir Depolama Access Control verilerini Uç Nokta için Microsoft Defender'da görüntüleme

[Microsoft 365 Defender portalı](https://security.microsoft.com/advanced-hunting), Cihaz Denetimi Çıkarılabilir Depolama Access Control tarafından tetiklenen olayları gösterir. Microsoft 365 güvenliğine erişmek için aşağıdaki aboneliğe sahip olmanız gerekir:

- E5 raporlama için Microsoft 365

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

### <a name="what-is-the-removable-storage-media-limitation-for-the-maximum-number-of-usbs"></a>Maksimum USB sayısı için çıkarılabilir depolama medyası sınırlaması nedir?

Boyutu 7 MB'a kadar olan 100.000 medya içeren bir USB grubu doğrulandı. İlke hem Intune hem de GPO'da performans sorunları olmadan çalışır.

### <a name="why-does-the-policy-not-work"></a>İlke neden çalışmıyor?

1. En yaygın neden, gerekli kötü [amaçlı yazılımdan koruma istemcisi sürümü](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control#prepare-your-endpoints) olmamasıdır.

2. Bir diğer neden de XML dosyasının doğru biçimlendirilmemiş olması, örneğin XML dosyasındaki "&" karakteri için doğru markdown biçimlendirmesinin kullanılmaması veya metin düzenleyicisinin dosyaların başına bayt sırası işareti (BOM) 0xEF 0xBB 0xBF eklemesi ve bu da XML ayrıştırma işleminin çalışmaması olabilir. Basit bir çözüm, [örnek dosyayı](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) indirmek ( **Raw'ı** ve sonra **Farklı kaydet'i** seçin) ve ardından güncelleştirmektir.

3. İlkeyi grup ilkesi aracılığıyla dağıtıyor ve yönetiyorsanız, lütfen tüm PolicyRule'u PolicyRules adlı bir üst düğümdeki tek bir XML dosyasında ve tüm Grup'u Gruplar adlı bir üst düğümde tek bir XML dosyasında birleştirdiğinizden emin olun; Intune aracılığıyla yönetiyorsanız, bir PolicyRule tek XML dosyası, aynı şey, bir Grup bir XML dosyası tutun.

Hala çalışmıyorsa, yöneticiyle cmd çalıştırarak bizimle iletişime geçip destek kabini paylaşmak isteyebilirsiniz: "%programfiles%\Windows Defender\MpCmdRun.exe" -GetFiles

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
