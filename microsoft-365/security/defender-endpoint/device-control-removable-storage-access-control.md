---
title: Uç Nokta Cihaz Denetimi için Microsoft Defender Çıkarılabilir Depolama Erişim Denetimi, çıkarılabilir depolama medyası
description: Uç Nokta için Microsoft Defender hakkında bir adım adım bilgi
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
ms.date: 03/09/2022
ms.openlocfilehash: 9f323d902f0e421ea73303706e0785f9bd76f3ff
ms.sourcegitcommit: a9266e4e7470e8c1e8afd31fef8d266f7849d781
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63406071"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>Uç Nokta Cihaz Denetimi Için Microsoft Defender Çıkarılabilir Depolama Denetimi

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> Bu ürünün Grup İlkesi yönetimi ve Intune OMA-URI/Özel İlke yönetimi artık genel olarak sağlanmaktadır (4.18.2106): Bkz. [Teknik Community blogu:](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protect-your-removable-storage-and-printers-with-microsoft/ba-p/2324806) Çıkarılabilir depolamanızı ve yazıcınızı Uç Nokta için Microsoft Defender ile koruma.


Access Denetimi'nin Uç Nokta Cihaz Denetimi Depolama Microsoft Defender aşağıdaki görevi yerineymanıza olanak sağlar:

- bağımsız olarak veya dışlama olmadan çıkarılabilir depolama alanına erişimi denetleme, okuma, yazma veya yürütmeye izin verme veya engelleme

|Ayrıcalık|İzin|
|---|---|
|Access|Okuma, Yazma, Yürütme|
|Eylem Modu|Denetim, İzin Ver, Engelle|
|CSP Desteği|Evet|
|GPO Desteği|Evet|
|Kullanıcı Tabanlı Destek|Evet|
|Makine Tabanlı Destek|Evet|

|Özellik|Açıklama|Intune aracılığıyla dağıtma|Grup İlkesi aracılığıyla dağıtma|
|---|---|---|---|
|Çıkarılabilir Medya Grubu Oluşturma|Yeniden kullanılabilir çıkarılabilir medya grubu oluşturmanıza olanak sağlar|1. adım ve 3. adım [OMA-URI yoluyla ilke dağıtma bölümünde](#deploying-policy-via-oma-uri) | Grup İlkesi aracılığıyla ilke dağıtma bölümündeki 1 [. adım](#deploying-policy-via-group-policy)|
|İlke Oluşturma|Çıkarılabilir her medya grubunu zorunlu olarak oluşturmak için ilke oluşturmanıza olanak sağlar|OMA-URI aracılığıyla ilkeyi dağıtma bölümündeki 2[. ve](#deploying-policy-via-oma-uri) 3. adımlar | Grup İlkesi aracılığıyla ilkeyi [dağıtma bölümündeki 2. adım](#deploying-policy-via-group-policy) |
|Varsayılan Zorlama|İlke yoksa çıkarılabilir medyaya varsayılan erişimi (Reddet veya İzin Ver) ayarlamanıza olanak sağlar|Bölümdeki 4. Adım: [OMA-URI aracılığıyla ilke dağıtma](#deploying-policy-via-oma-uri) | Grup İlkesi aracılığıyla ilke dağıtma bölümündeki 3 [. adım](#deploying-policy-via-group-policy) |
|Access Denetimi'nin Çıkarılabilir özelliğini Depolama veya Devre Dışı Bırak|Devre Dışı Bırak'ı ayarsanız, bu makinede Çıkarılabilir Depolama Access Denetimi ilkesi devre dışı bırakılabilir| Bölümdeki 5. Adım: [OMA-URI aracılığıyla ilke dağıtma](#deploying-policy-via-oma-uri) | Grup İlkesi aracılığıyla ilke dağıtma bölümündeki 4 [. adım](#deploying-policy-via-group-policy) |
|Dosya bilgilerini yakalama|Yazma erişimi gerçekleşirse dosya bilgilerini yakalamak için ilke oluşturmanıza olanak sağlar| OMA-URI aracılığıyla ilkeyi dağıtma bölümündeki 2[. ve](#deploying-policy-via-oma-uri) 6. Adım | Grup İlkesi aracılığıyla ilkeyi dağıtma bölümündeki 2 [. ve 5. adım](#deploying-policy-via-group-policy) |

## <a name="prepare-your-endpoints"></a>Uç noktalarınızı hazırlama

Kötü amaçlı yazılım Depolama **4.18.2103.3** veya sonraki bir sürümüne sahip Windows 10 ve Windows 11 cihazlarında Çıkarılabilir Veya Access Denetimi'ni dağıtın.

- **4.18.2104** veya sonrakisi: SerialNumberId, VID_PID, filepath tabanlı GPO desteği, ComputerSid ekleme

- **4.18.2105** veya sonrakisi: Belirli bir makinede belirli bir kullanıcının bileşimi olan HardwareId/DeviceId/InstancePathId/SerialNumberId için joker destek, kaldırılabilir SSD (san Extreme SSD)/USB Attached BELIRLI (UAS) desteği

- **4.18.2107** veya sonraki sürümü: Windows Taşınabilir Cihaz (WPD) desteği ekleme (tablet gibi mobil cihazlar için); gelişmiş oyunlara AccountName [ekleme](device-control-removable-storage-access-control.md#view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint)

- **4.18.2111** veya sonrakisi: PowerShell aracılığıyla 'Çıkarılabilirleri Etkinleştir veya Devre Dışı Bırak' Depolama Access Denetimi', 'Varsayılan Zorlama', istemci makinesi ilkesi güncelleştirme süresi, dosya bilgileri

- **4.18.2201** veya sonrakisi: OMA-URI aracılığıyla depolamaya izin verilen bir dosyanın kopyasını destekleme

:::image type="content" source="images/powershell.png" alt-text="PowerShell arabirimi.":::

> [!NOTE]
> Çıkarılabilir Windows Güvenliği, Access Denetimi'ni çalışma durumundan bağımsız olarak çalıştırabilirsiniz Depolama bileşenlerin hiçbiri etkin Windows Güvenliği olması gerekir.

## <a name="policy-properties"></a>İlke özellikleri

Çıkarılabilir bir depolama grubu oluşturmak için aşağıdaki özellikleri kullanabilirsiniz:

> [!NOTE]
> XML açıklama notasyonu `<!-- COMMENT -->` kullanan açıklamalar Kural ve Grup XML dosyalarında kullanılabilir, ancak XML dosyasının ilk satırı değil, ilk XML etiketinin içinde yer almaları gerekir.

### <a name="removable-storage-group"></a>Çıkarılabilir Depolama Grubu

|Özellik Adı|Açıklama|Seçenekler|
|---|---|---|
|**GroupId**|Benzersiz bir kimlik olan GUID, grubu temsil eder ve ilkede kullanılır.||
|**DescriptorIdList**|Grubun içini kapsıyorsanız kullanmak istediğiniz cihaz özelliklerini listele. Her cihaz özelliği için, daha ayrıntılı [bilgi için](device-control-removable-storage-protection.md) Cihaz Özellikleri'ne bakın. Tüm özellikler büyük/harfe duyarlıdır. |**PrimaryId**: `RemovableMediaDevices`, , `CdRomDevices``WpdDevices`<p>**BusId**: Örneğin, USB, BUTA<p>**DeviceId**<p>**HardwareId**<p>**InstancePathId**: InstancePathId, sistem içinde cihazı benzersiz olarak tanımlayan bir dizedir; örneğin, `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0`. Ucundaki sayı (örneğin, &0) kullanılabilir yuvasını temsil eder ve cihazdan cihaza değişebilir. En iyi sonuçları elde etmek için en sonunda joker karakter kullanın. Örneğin, `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*`.<p>**FriendlyNameId**<p>**SeriSayıKimlik**<p>**VID**<p>**PID**<p>**VID_PID**<p>`0751_55E0`: bu tam VID/PID çiftini eşleştirin<p>`_55E0`: herhangi bir medyayı PID=55E0 ile eşler <p>`0751_`: herhangi bir medyayı VID=0751 ile eşler|
|**MatchType**|içinde kullanılan birden çok cihaz özelliği olduğunda `DescriptorIDList`, MatchType ilişkiyi tanımlar.|**MatchAll**: Altındaki `DescriptorIdList` tüm öznitelikler **Ve** ilişkisi olur; örneğin, `DeviceID` `InstancePathID`yönetici her bağlantılı USB için ve ve , değerlerini koyarsa, sistem USB'nin her iki değere de uygun olup olmadığını kontrol eder. <p> **MatchAny**: DescriptorIdList'in altındaki öznitelikler **Veya ilişkisi** olur; örneğin, yönetici her `DeviceID` `InstancePathID`bağlantılı USB için ve ' koyarsa, USB'de aynı **DeviceID** veya InstanceID değeri olduğu sürece sistem **zorlamayı** yapar. |

### <a name="access-control-policy"></a>Erişim Denetimi İlkesi

| Özellik Adı | Açıklama | Seçenekler |
|---|---|---|
| **PolicyRuleId** | Benzersiz bir kimlik olan GUID, ilkeyi temsil eder ve raporlama ve sorun gidermede kullanılır. | |
| **IncludedIdList** | İlkenin uygulanacak olduğu grup/grup. Birden çok grup eklenirse, ilke bu grupların tüm medyalarına uygulanır.|Bu örnekte Grup Kimliği/GUID kullanılmalıdır. <p> Aşağıdaki örnekte GroupID kullanımı gösterir: <p> `<IncludedIdList> <GroupId> {EAA4CCE5-F6C9-4760-8BAD-FDCC76A2ACA1}</GroupId> </IncludedIdList>` |
| **ExcludedIDList** | İlkenin uygulanmaymayacak olan grup/gruplarda. | Bu örnekte Grup Kimliği/GUID kullanılmalıdır. |
| **Giriş Kimliği** | Bir İlkeRule'nin birden çok girdisi olabilir; Benzersiz GUID'ye sahip her girdi, Cihaz Denetimi'ne bir kısıtlama söyler.| |
| **Tür** | IncludedIDList'te çıkarılabilir depolama grupları için eylemi tanımlar. <p>Zorlama: İzin Ver veya Reddet <p>Denetim: AuditAllowed veya AuditDenied<p> | İzin ver<p>Reddet <p>AuditAllowed: Erişime izin verilirken bildirim ve etkinliği tanımlar <p>Denetim Reddedildi: Erişim reddedilirken bildirimi ve olayı tanımlar; Erişimi reddet ile birlikte **çalışması** gerekir.<p> Aynı medya için çakışma türleri olduğunda, sistem ilkede birinciyi geçerli olur. Çakışma türüne örnek olarak İzin Ver **ve Reddet** **örneği olabilir**. |
| **Sid** | Yerel kullanıcı Sid veya kullanıcı Sid grubu veya AD nesnesinin Sid grubu, bu ilkenin belirli bir kullanıcıya mı yoksa kullanıcı grubuna mı uygulan uygulanıp uygulan uygulanıla bir bütün değildir; bir giriş en çok bir Sid'e ve bir de Sid olmayan bir girdiye sahip olabilir, bu da ilkenin makineye uygulanması anlamına gelir. |  |
| **ComputerSid** | Yerel bilgisayar Sid veya bilgisayar Sid grubu ya da AD nesnesinin Sid grubu, bu ilkenin belirli bir makine veya makine grubu üzerinde uygulanıp uygulan uygulanıp uygulan uygulana bir ilke olmadığını tanımlar; bir girişin en çok bir BilgisayarSid girişi olabilir ve herhangi bir ComputerSid değeri olmadan giriş, ilkenin makine üzerinden uygulanması anlamına gelir. Belirli bir kullanıcıya ve belirli makineye bir Girdi uygulamak için, hem Sid'i hem de BilgisayarSid'i aynı Girdiye ekleyin. |  |
| **Seçenekler** | Bildirimin görüntüleniyor mu yoksa görüntülenmey mi olduğunu tanımlar |**İzin Türü seçildiğinde**: <p>0: hiçbir şey<p>4: Bu Girdi **için Denetime Izin Verilmedi** **ve Denetim Reddedildi'yi** devre dışı bırakma. İzin Ver **gerçekleşirse** ve AuditAllowed ayarı yapılandırılmış olsa bile, sistem olay göndermez. <p>8: Dosya bilgilerini yakalamak ve Yazma erişimi için kanıt olarak dosyanın bir kopyasını almak. <p>16: Yazma erişimi için dosya bilgilerini yakalama. <p>**Reddet Türü seçildiğinde**: <p>0: hiçbir şey<p>4: Bu Girdi **için Denetim Reddedildi özelliğini** devre dışı bırakma. Engelle **gerçekleşirse** ve Denetim Reddedildi ayarı yapılandırıldı olsa bile, sistem bildirimi göstermez. <p>**Type **AuditAllowed seçiliyken****: <p>0: hiçbir şey <p>1: hiçbir şey <p>2: etkinlik gönderme<p>3: etkinlik gönderme <p> **Tür Denetimi **Reddedildi seçiliyken****: <p>0: hiçbir şey <p>1: bildirimi göster <p>2: etkinlik gönderme<p>3: bildirimi gösterme ve etkinlik gönderme |
|AccessMask|Erişimi tanımlar. | **Disk düzeyi erişimi**: <p>1: Okuma <p>2: Yazma <p>4: Yürütme <p>**Dosya sistemi düzeyi erişimi**: <p>8: Dosya sistemi Okuma <p>16: Dosya sistemi Yazma <p>32: Dosya sistemi Yürütme <p><p>İkili OR işlemi yaparak birden çok erişiminiz olabilir; örneğin, Okuma ve Yazma ve Yürütme için AccessMask 7 olur; Okuma ve Yazma için AccessMask 3 olur.|

## <a name="common-removable-storage-access-control-scenarios"></a>Ortak Çıkarılabilir Depolama Access Denetimi senaryoları

Uç Nokta Çıkarılabilir veya Erişim Denetimi'Depolama Microsoft Defender'ı tanımanıza yardımcı olmak için, takip etmek için bazı yaygın senaryoları bir araya getirdik.

### <a name="scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs"></a>Senaryo 1: Tüm Kullanıcılar için Yazma ve Yürütme erişimini engelleme ancak onaylanan belirli USB'lere izin verme

1. Grup oluşturma

    1. Grup 1: Çıkarılabilir depolama alanı ve CD/DVD. Çıkarılabilir bir depolama alanı ve CD/DVD örneği: Örnek Tüm Çıkarılabilir Depolama ve [CD-DVD](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) Group.xmldosyasındaki Grup **9b28fae8-72f7-4267-a1a5-685f747a7146**.

    2. Grup 2: Cihaz özelliklerine göre onaylı USB'ler. Bu kullanım durumuna örnek olarak: Örnek Kimlik - Grup **65fa649a-a111-4912-9294-fb6337a25038** [Group.xml.](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples)

    > [!TIP]
    > Değerle `&` `&amp;` değiştirin.

2. İlke oluşturma

    1. İlke 1: Erişimi Engelleme ve Yürütme Ancak Onaylanan USB'lere izin verme. Bu kullanım durumuna örnek olarak: Örnek: Senaryo 1 Blok Yazma ve Yürütme [Erişimi'nin](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) örnek durumundaki İlkeRule **c544a991-5786-4402-949e-a032cb790d0e**. Ancak onaylanan USBs.xmlizin veriyor.

    2. İlke 2: İzin verilen USB'lere Denetim Yazma ve Yürütme erişimi. Bu kullanım durumuna örnek olarak: Senaryo 1 Denetim Yazma ve Onaylanmış [USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) üzerinde PolicyRule **36ae1037-a639-4cff-946b-b36c53089a4c**.

### <a name="scenario-2-audit-write-and-execute-access-to-all-but-block-specific-unapproved-usbs"></a>Senaryo 2: Denetim Yazma ve Tüm bu erişimi yürütme ancak belirli unapproved USB'leri engelleme

1. Grup oluşturma

    1. Grup 1: Çıkarılabilir depolama alanı ve CD/DVD. Bu kullanım durumuna örnek olarak: Örnek Olarak Çıkarılabilir Depolama ve [CD-DVD](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) Group.xmldosyasındaki Grup **9b28fae8-72f7-4267-a1a5-685f747a7146**.

    2. 2. Grup: Cihaz özelliklerine bağlı olarak, örneğin, Satıcı Kimliği / Ürün Kimliği, Kolay Ad – **Grup 65fa649a-a111-4912-9294-fb6337a25038** ve bu [Group.xml.](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples)

    > [!TIP]
    > Değerle `&` `&amp;` değiştirin.

2. İlke oluşturma

    1. İlke 1: Belirli unapproved USB'ler için engellemeler yerine Yazma ve Yürütme erişimini engelleme. Bu kullanım örneğine bir örnek: Senaryo 2 Denetim Yazma ve Tüm bunlarda erişimi yürütme ancak belirli [unapproved USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples). Örnek: PolicyRule **23b8e437-66ac-4b32-b3d7-24044637fc98**.

    2. İlke 2: Denetim Yazma ve Başkalarına erişimi yürütme. Bu kullanım durumuna örnek olarak: Senaryo 2 Denetim Yazma ve [others.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) dosyasına erişimi yürütme örneği: İlkeRule **b58ab853-9a6f-405c-a194-740e69422b48**.

## <a name="deploying-and-managing-policy-via-group-policy"></a>Grup İlkesi aracılığıyla ilke dağıtma ve yönetme

Çıkarılabilir Erişim Depolama özelliği, Grup İlkesi aracılığıyla ilkeyi kullanıcıya veya cihaza ya da her ikisinde birden uygulamanıza olanak sağlar.

### <a name="licensing"></a>Lisanslama

Çıkarılabilir Veya Erişim Denetimi Depolama başlamadan önce, Çıkarılabilir aboneliğinizi Microsoft 365 [gerekir](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Çıkarılabilir veya Çıkarılabilir Erişim Denetimi Depolama i kullanmak için Çıkarılabilir veya Microsoft 365 E3 Microsoft 365 E5.

### <a name="deploying-policy-via-group-policy"></a>Grup İlkesi aracılığıyla ilke dağıtma

1. Tek bir XML dosyasındaki `<Groups>` `</Groups>` tüm grupları birleştirin.

    Aşağıdaki resimde Senaryo 1 örneğini göstermektedir: Tüm kullanıcılara Yazma ve Yürütme erişimini engelle ancak onaylanan belirli [USB'lere izin verme](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs).

    :::image type="content" source="images/prevent-write-access-allow-usb.png" alt-text="Cihazlarda belirli onaylanmış USB'lere izin gösteren yapılandırma ayarlarını gösteren ekran.":::

2. Tüm kuralları tek bir `<PolicyRules>` `</PolicyRules>` XML dosyasında birleştirin.

    Belirli bir kullanıcıya kısıtlamak istediğiniz, SID özelliğini Girdi'de kullanın. Girdi ilkesinde SID yoksa, Makine için herkes oturum açma örneğine Girdi uygulanır.
    
    Yazma erişimi için dosya bilgilerini izlemek için doğru Seçenek(16) ile doğru AccessMask'ı kullanın; dosya yakalama bilgileri [örneğidir](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Audit%20File%20Information.xml).

    Aşağıdaki resimde SID özelliğinin kullanımı ve Senaryo 1 örneği: Tüm kullanıcılara Yazma ve Yürütme erişimini engelleme, ancak belirli onaylanmış [USB'lere izin verme örneklerini göstermektedir](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs).

    :::image type="content" source="images/usage-sid-property.png" alt-text="Ekran, SID özellik özniteliğinin kullanımını belirten kodu görüntüleniyor.":::

3. Hem kural **hem** \> de grup XML dosyalarını ağ paylaşım klasörüne kaydedin ve ağ paylaşım klasörü yolunu Grup İlkesi ayarına **girin:** \>  \> Bilgisayar Yapılandırması Yönetim Şablonları **Windows** \> Bileşenleri Microsoft Defender Virüsten Koruma **Cihaz Denetimi**: **'Cihaz denetimi** ilkesi gruplarını tanımlama' **ve 'Cihaz denetim ilkesi kurallarını tanımlayın'**.

   Grup İlkesinde ilke yapılandırması UX'sini bulamazsanız, **Raw'ı** ve ardından Farklı Kaydet'i seçerek [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) ve [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx) **dosyalarını indirebilirsiniz**.

   - İlkenin olması için hedef makinenin ağ paylaşımına erişeli olmalıdır. Bununla birlikte, ilke okunduktan sonra, makine yeniden başlatmadan sonra bile ağ paylaşım bağlantısı gerekmez.

    :::image type="content" source="images/device-control.png" alt-text="Cihaz Denetimi ekranı.":::

4. Varsayılan zorlama: ilke yoksa çıkarılabilir medyaya varsayılan erişimi (Reddet veya İzin Ver) ayarlamanıza olanak sağlar. Örneğin, RemovableMediaDevices için yalnızca ilkeye (Reddet veya İzin Ver) sahipsiniz ancak CdRomDevices veya WpdDevices ile ilgili hiçbir ilkeye sahip değildir ve varsayılan olarak Bu ilke üzerinden Reddet'i ayarlarken CdRomDevices veya WpdDevices'e Okuma/Yazma/Yürütme erişimi engellenir.

   - Bu ayarın dağıtımında Varsayılan İzin Ver veya **Varsayılan Reddet** **ayarlarını da göreceğiz**.
   - Bu ayarı yapılandırırken hem Disk düzeyi hem de Dosya sistemi düzeyinde AccessMask'ı düşünün; örneğin, Varsayılan Reddet'i kullanmak ama belirli bir depolamaya izin vermek için hem Disk düzeyi hem de Dosya sistemi düzeyi erişimine izin vermek için AccessMask'ı 63 olarak ayarlayın.

    :::image type="content" source="images/148609579-a7df650b-7792-4085-b552-500b28a35885.png" alt-text="Varsayılan powershell koduna izin ver veya varsayılan reddet":::

5. Çıkarılabilir Çıkarılabilirleri Erişim Denetimi Depolama i Etkinleştirme veya Devre Dışı Bırak: Bu değeri, Access Denetimi'nin Çıkarılabilir özelliğini geçici olarak Depolama olarak ayarlayın.

    :::image type="content" source="images/148608318-5cda043d-b996-4146-9642-14fccabcb017.png" alt-text="Cihaz Denetimi ayarları":::

   - Bu ayarı dağıttırdikten sonra Etkin veya Devre **Dışı'ya** **bakın**. Devre dışı bırak, bu makinenin Access Denetimi ilkesi Depolama Çıkarılabilir ayarına sahip olmadığını gösterir.

    :::image type="content" source="images/148609685-4c05f002-5cbe-4aab-9245-83e730c5449e.png" alt-text="PowerShell kodunda Etkin veya Devre Dışı cihaz denetimi":::

6. Dosyanın kopyasının konumunu ayarlama: Yazma erişimi gerçekleşirken dosyanın bir kopyasını almak için, sistemin kopyayı kaydedeli olduğu konumu ayarlanız gerekir.
    
    Bunu doğru AccessMask ve Option ile birlikte dağıtın. Yukarıdaki 2. adıma bakın.

    :::image type="content" source="../../media/define-device-control-policy-rules.png" alt-text="Grup İlkesi - Dosya kanıtı için locaiton ayarlama":::

## <a name="deploying-and-managing-policy-via-intune-oma-uri"></a>Intune OMA-URI aracılığıyla ilke dağıtma ve yönetme

Çıkarılabilir Dosya Depolama Erişimi Denetimi özelliği, OMA-URI aracılığıyla ilkeyi kullanıcıya veya cihaza ya da her ikisinde birden uygulamanıza olanak sağlar.

### <a name="licensing-requirements"></a>Lisans gereksinimleri

Çıkarılabilir Veya Erişim Denetimi Depolama başlamadan önce, Çıkarılabilir aboneliğinizi Microsoft 365 [gerekir](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Çıkarılabilir veya Çıkarılabilir Erişim Denetimi Depolama i kullanmak için Çıkarılabilir veya Microsoft 365 E3 Microsoft 365 E5.

### <a name="permission"></a>İzin

Intune'da ilke dağıtımı için, hesabın cihaz yapılandırma profillerini oluşturma, düzenleme, güncelleştirme veya silme izinleri olması gerekir. Bu izinlerle özel roller oluşturabilir veya yerleşik rollerden herhangi birini kullanabilirsiniz.

- İlke ve profil Yöneticisi rolü

- Cihaz Yapılandırması profilleri için Rapor Oluştur/Düzenle/Güncelleştir/Oku/Sil/Görüntüle izinleri açık olan özel rol

- Genel yönetici

### <a name="deploying-policy-via-oma-uri"></a>OMA-URI aracılığıyla ilke dağıtma

Microsoft Endpoint Manager merkezi (<https://endpoint.microsoft.com/>)  **Cihazlar** \> \> **Yapılandırma profilleri** \> \> Profil Platformu oluşturun **: Windows 10 ve sonrası & Profili: Özel**

1. Her Grup için bir OMA-URI kuralı oluşturun:

    - OMA-URI:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b**GroupGUID**%7d/GroupData`

      Örneğin, **örnekteki çıkarılabilir depolama alanı ve CD/DVD** grubu için bağlantı şöyle olmalı:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b9b28fae8-72f7-4267-a1a5-685f747a7146%7d/GroupData`

    - Veri Türü: Dize (XML dosyası)

      :::image type="content" source="images/xml-data-type-string.png" alt-text="STRING veri türünün XML dosyası.":::

2. Her ilke için bir OMA-URI da oluşturun:

    - OMA-URI:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7b**PolicyRuleGUID**%7d/RuleData`

      Örneğin, örnekteki **Yazma ve Yürütme Erişimini Engelle ancak onaylanmış USB'lere** izin ver kuralı için bağlantı şöyle olmalı:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bc544a991-5786-4402-949e-a032cb790d0e%7d/RuleData`

    - Veri Türü: Dize (XML dosyası)
       
    Yazma erişimi için dosya bilgilerini izlemek için doğru Seçenek(16) ile doğru AccessMask'ı kullanın; dosya yakalama bilgileri [örneğidir](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Audit%20File%20Information.xml).

3. Varsayılan zorlama: ilke yoksa çıkarılabilir medyaya varsayılan erişimi (Reddet veya İzin Ver) ayarlamanıza olanak sağlar. Örneğin, RemovableMediaDevices için yalnızca ilkeye (Reddet veya İzin Ver) sahipsiniz ancak CdRomDevices veya WpdDevices ile ilgili hiçbir ilkeye sahip değildir ve varsayılan olarak Bu ilke üzerinden Reddet'i ayarlarken CdRomDevices veya WpdDevices'e Okuma/Yazma/Yürütme erişimi engellenir.

    - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DefaultEnforcement`

    - Veri Türü: Int

      `DefaultEnforcementAllow = 1`
      `DefaultEnforcementDeny = 2`

    - Bu ayarın dağıtımında Varsayılan İzin Ver veya **Varsayılan Reddet** **ayarlarını görme**
    - Örneğin, bu ayarı yapılandırken hem Disk düzeyi hem de Dosya sistemi düzeyinde AccessMask'ı göz önünde bulundurabilirsiniz; örneğin, Varsayılan Reddet'i kullanmak ancak belirli bir depolamaya izin vermek için hem Disk düzeyi hem de Fiel sistem düzeyi erişimine izin vermek için AccessMask ayarını 63 olarak ayarlayın.

    :::image type="content" source="images/148609590-c67cfab8-8e2c-49f8-be2b-96444e9dfc2c.png" alt-text="PowerShell koduna varsayılan Zorlamaya İzin Ver":::

4. Çıkarılabilir Çıkarılabilirleri Erişim Denetimi Depolama i Etkinleştirme veya Devre Dışı Bırak: Bu değeri, Access Denetimi'nin Çıkarılabilir özelliğini geçici olarak Depolama olarak ayarlayın.

   - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DeviceControlEnabled`

   - Veri Türü: Int `Disable: 0`
     `Enable: 1`

   - Bu ayarın dağıtımında Etkin veya Devre **Dışı** 

    **Devre** dışı bırak, bu makinenin Access Denetimi'nin Depolama Çıkarılabilir ayarına sahip olduğu anlamına gelir

    :::image type="content" source="images/148609770-3e555883-f26f-45ab-9181-3fb1ff7a38ac.png" alt-text="PowerShell Depolama Access Denetimi'nin kaldırılabilir örneği":::

5. Dosyanın bir kopyasının konumunu ayarlama: Yazma erişimi gerçekleşirken dosyanın bir kopyasını almak için sistemin kopyayı kaydedeli olduğu konumu ayarlanız gerekir.
    
    - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DataDuplicationRemoteLocation;**username**;**password**`

    - Veri Türü: Dize
    
    Bunu doğru AccessMask ve doğru Seçenek ile birlikte dağıtmalı - yukarıdaki 2. adıma bakın.

    :::image type="content" source="../../media/device-control-oma-uri-edit-row.png" alt-text="Dosya kanıtı için locaiton ayarlama":::
    
## <a name="deploying-and-managing-policy-by-using-intune-user-interface"></a>Intune kullanıcı arabirimini kullanarak ilkeyi dağıtma ve yönetme

Bu özellik, Microsoft Endpoint Manager merkezinde kullanılabilir<https://endpoint.microsoft.com/>. **Endpoint SecurityAttack** >  **Surface ReductionCreate** >  **Policy adresine gidin**. Profil **: Windows 10 ile Platform: Tercihler** **ve daha sonraki bir adı seçin.**

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'Depolama Access Denetimi'nin çıkarılabilir verilerini görüntüleme

Varsayılan [Microsoft 365 Defender, Erişim](https://security.microsoft.com/advanced-hunting) Denetimi'nin Kaldırılabilir Cihaz Denetimi Depolama olayları gösterir. Güvenlik Microsoft 365 için aşağıdaki aboneliğe sahip olmak gerekir:

- Microsoft 365 raporlaması

```kusto
//events triggered by RemovableStoragePolicyTriggered
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

:::image type="content" source="images/block-removable-storage.png" alt-text="Çıkarılabilir depolama alanını engellemeyi gösteren ekran.":::

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="what-is-the-removable-storage-media-limitation-for-the-maximum-number-of-usbs"></a>En fazla USB sayısı için çıkarılabilir depolama alanı medya sınırlaması nedir?

Boyutu 7 MB'a kadar olan 100.000 medyaya sahip bir USB grubu doğruladık. İlke, performans sorunları olmadan hem Intune'da hem de GPO'da çalışır.

### <a name="why-does-the-policy-not-work"></a>İlke neden çalışmıyor?

Bunun en yaygın nedeni, gerekli kötü amaçlı [yazılımdan koruma istemci sürümünün yüklü olmasıdır](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control#prepare-your-endpoints).

Diğer bir neden ise XML dosyasının doğru biçimlendirimeilmiş olması (örneğin, XML dosyasındaki "&" karakteri için doğru markdown biçimlendirmesi kullanmama veya metin düzenleyicisi dosyaların başına bir byte order mark (TABLO) 0xEF 0xBB 0xBF eklemesi ve BU da XML ayrıştırmanın çalışmamalarına neden olabilir. Basit bir çözüm de örnek dosyayı indirmek ( [Ham'i](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) **ve ardından** Farklı **Kaydet'i seçin) ve** ardından güncelleştirin.

İlkeyi Grup İlkesi aracılığıyla dağıtıyor ve yönetiyorsanız, lütfen Tüm İlkeYili tek bir XML dosyasında, PolicyRules ve tüm Group olarak adlandırılan bir üst düğümde Groups adlı bir üst düğümde tek bir XML dosyasında birleştirin; Intune aracılığıyla yönetseniz, tek bir İlkeRule XML dosyası olarak tutabilirsiniz; aynı şey, bir Grup bir XML dosyası.

### <a name="there-is-no-configuration-ux-for-define-device-control-policy-groups-and-define-device-control-policy-rules-on-my-group-policy"></a>Grup İlkemde 'Cihaz denetim ilkesi gruplarını tanımla' ve 'Cihaz denetim ilkesi kurallarını tanımla' için yapılandırma UX'si yoktur

Grup İlkesi yapılandırması UX'larını yeniden teslim etmeseniz de, [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) ve [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx) dosyalarında 'Raw' ve 'Farklı Kaydet'e tıklayarak ilgili adml ve admx dosyalarını almaya devam edebilirsiniz.

### <a name="how-can-i-know-whether-the-latest-policy-has-been-deployed-to-the-target-machine"></a>En son ilkenin hedef makineye dağıtıldığından nasıl emin olabilirim?

PowerShell'de Yönetici olarak 'Get-MpCompstatus' çalıştırabilirsiniz. Aşağıdaki değer, hedef makineye en son ilkenin uygulanıp uygulanmadı gösterir.

:::image type="icon" source="images/148609885-bea388a9-c07d-47ef-b848-999d794d24b8.png" border="false":::

### <a name="how-can-i-know-which-machine-is-using-out-of-date-antimalware-client-version-in-the-organization"></a>Kuruluşta hangi makinenin eski kötü amaçlı yazılımdan koruma istemci sürümünü kullanıyor olduğunu nasıl bilim?

Güvenlik portalında kötü amaçlı yazılımlardan koruma istemci sürümünü almak için aşağıdaki Microsoft 365 kullanabilirsiniz:

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
