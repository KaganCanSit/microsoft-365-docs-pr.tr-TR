---
title: BT yöneticileri için Office belgelerinde etkin içeriği yönetme
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: tutorial
ms.localizationpriority: medium
ms.prod: m365-security
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ROBOTS: NOINDEX,NOFOLOW
description: Yöneticiler, Office belgelerde etkin içeriği engellemek için ilke oluşturmayı öğrenebilir
ms.openlocfilehash: 7a24c56bdd388f2dc9a8f408b52b2de1c6805a0a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100951"
---
# <a name="manage-active-content-in-office-documents"></a>Office belgelerinde etkin içeriği yönetme

> [!NOTE]
> Bu makalede açıklanan özellikler Önizleme aşamasındadır, herkes tarafından kullanılamaz ve değiştirilebilir.

Office belgeler _etkin içerik_ içerdiğinde otomatik olarak yenilenebilir, güncelleştirilebilir veya yürütülebilir. Etkin içeriğe örnek olarak makrolar, ActiveX denetimleri ve Office Eklentileri verilebilir. Etkin içerik kullanıcılara güçlü ve kullanışlı işlevler sağlayabilir, ancak saldırganlar kötü amaçlı yazılım sunmak için etkin içeriği de kullanabilir.

Yöneticiler, etkin içerik kullanımını belirli kullanıcı kümeleriyle sınırlayan veya etkin içeriği tamamen devre dışı bırakmak için kuruluş ilkeleri (grup ilkeleri veya bulut ilkeleri) oluşturabilir. Kullanıcılar, Office Güven Merkezi'nde kendi güvenlik ve gizlilik ayarlarını **Dosya** \> **Seçenekleri** \> **Güven Merkezi'ndeki** Office uygulamalarında yapılandırabilir.

Daha önce, kullanıcılar belgeleri güvenilir belgeler olarak tanımladığında, bir yönetici Office belgelerde etkin içeriği engellemek için ilkeler yapılandırmış olsa bile, seçimleri etkin içeriğin çalışmasına izin verecekti. Artık yöneticiler tarafından ayarlanan ilkeler, güvenilen belgelerin kullanıcı kimliğinden önceliklidir. Davranıştaki bu değişiklik kullanıcılar için sorunlara neden olabilir.

Güncelleştirilmiş Güven Merkezi mantığı aşağıdaki diyagramda açıklanmıştır:

:::image type="content" source="../media/office-trust-center-flow.png" alt-text="Microsoft 365 Defender portalında Güven merkezi Mantığını açıklayan akış grafiği" lightbox="../media/office-trust-center-flow.png":::

1. Kullanıcı etkin içerik içeren bir Office belgesi açar.

2. Belge güvenilir bir konumdan geliyorsa, belge etkin içerik etkin olarak açılır. Belge güvenilir bir konumdan değilse değerlendirme devam eder.

3. Güncelleştirilmiş davranış şu şekilde etkinleşir:
   - Daha önce değerlendirilen bir sonraki ayar, kullanıcının bu belgeyi güvenilir bir belge olarak tanımlamış olmasıydı. Bu durumda belge etkin içerik etkin olarak açılır.
   - Şimdi, kullanıcının belgeyi güvenilir bir belge olarak tanımlayıp tanımlamadığı burada (şimdi 8. adımda) dikkate alınmaz.

     Davranıştaki temel değişiklik şu şekilde açıklanmıştır: bulut ilkeleri (4. adım), grup ilkeleri (6. adım) ve yerel ayarlar (7. adım) güvenilir belgenin kullanıcı ataması dikkate _alınmadan önce_ denetlenür. Bu adımlardan herhangi biri etkin içeriğe erişimi engelliyorsa **ve** adımların hiçbiri kullanıcı geçersiz kılmalarına izin vermiyorsa, belgenin güvenilir belge olarak kullanıcı kimliği önemli değildir.

4. Bu tür etkin içeriğe izin verilip verilmediğini veya engellenip engellenmediğini görmek için bulut ilkeleri denetleniyor. Etkin içerik engellenmezse, değerlendirme 6. adıma devam eder.

   Etkin içerik ilke tarafından engellenirse, deneyim 5. adımda açıklanmıştır.

5. Belgenin açılması, güven çubuğunda bir bildirimle engellenir. Bundan sonra ne olacağı, ilkedeki kullanıcı geçersiz kılma ayarları tarafından denetlener: a. **Kullanıcı geçersiz kılmaya izin verilmiyor**: Kullanıcı belgeyi açamıyor ve değerlendirme durduruluyor.
   b. **Kullanıcı geçersiz kılmaya izin verilir**: Kullanıcı, güven çubuğundaki bağlantıya tıklayarak belgeyi etkin içerik etkin olarak açabilir.

6. Bu tür etkin içeriğe izin verilip verilmediğini veya engellenip engellenmediğini görmek için grup ilkeleri denetleniyor. Etkin içerik engellenmezse, değerlendirme 7. adıma devam eder.

   Etkin içerik ilke tarafından engellenirse, deneyim 5. adımda açıklanmıştır.

7. Bu tür etkin içeriğe izin verilip verilmediğini veya engellenip engellenmediğini görmek için yerel ayarlar denetleniyor. Etkin içerik engellenirse, belgenin açılması güven çubuğunda bir bildirimle engellenir. Etkin içerik engellenmezse değerlendirme devam eder.

8. Kullanıcı belgeyi daha önce güvenilir bir belge olarak tanımladıysa, belge etkin içerik etkin olarak açılır. Aksi takdirde, belgenin açılması engellenir.

## <a name="what-is-a-trusted-document"></a>Güvenilir belge nedir?

Güvenilen belgeler, makrolar, ActiveX denetimleri ve belgedeki diğer etkin içerik türleri için güvenlik istemleri olmadan açılan Office belgelerdir. Korumalı Görünüm veya Application Guard belgeyi açmak için kullanılmaz. Kullanıcılar Güvenilen Belgeyi açtığında ve tüm etkin içerik etkinleştirildiğinde. Belgede yeni etkin içerik veya mevcut etkin içerik güncelleştirmeleri olsa bile, kullanıcılar belgeyi bir sonraki açışında güvenlik istemleri almaz.

Bu davranış nedeniyle, kullanıcılar belgelere yalnızca belge kaynağına güveniyorlarsa açıkça güvenmelidir.

Yönetici bir ilke kullanarak etkin içeriği engellerse veya kullanıcılar etkin içeriği engelleyen bir Güven Merkezi ayarı ayarlarsa, etkin içerik engellenmiş olarak kalır.

Daha fazla bilgi için aşağıdaki makalelere bakın:

- [Güvenilen belgeler](https://support.microsoft.com/topic/trusted-documents-cf872bd8-47ec-4c02-baa5-1fdba1a11b53)
- [Güvenilir bir konum ekleme, kaldırma veya değiştirme](https://support.microsoft.com/topic/add-remove-or-change-a-trusted-location-7ee1cdc2-483e-4cbb-bcb3-4e7c67147fb4)
- [Dosyalarınızdaki etkin içerik türleri](https://support.microsoft.com/topic/active-content-types-in-your-files-b7ff2e8a-4055-47d4-8c7d-541e19f62bea)

## <a name="configure-trusted-document-settings-in-office-policies"></a>Office ilkelerinde güvenilen belge ayarlarını yapılandırma

Yöneticilerin kuruluştaki Office yapılandırmanın birçok yolu vardır. Örneğin:

- **Office bulut ilkesi hizmeti**: Azure AD hesabıyla Office uygulamalarındaki dosyalara erişen tüm cihazlardaki bir kullanıcı için geçerli olan kullanıcı tabanlı bir ilke ayarlayın. [Office Bulut İlkesi Hizmeti'nde Office bulut ilkesi](https://config.office.com/officeSettings/officePolicies) [yapılandırması oluşturma](/DeployOffice/overview-office-cloud-policy-service) adımlarına bakın.
- **Intune'da Office ilkeleri**: HKCU ilkelerini bilgisayarlara Windows 10 dağıtmak için Intune Ayarlar kataloğunu veya Yönetim şablonlarını kullanın: **CIHAZ** \> **Yapılandırma Profilleri** altındaki [MEM yönetim merkezinde](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/configurationProfiles).
  - ***Yönetim Şablonları***: [Yönetim](/mem/intune/configuration/administrative-templates-windows) Şablonlarını yapılandırmak için Windows 10 şablonları kullanma yönergelerine bakın.
  - ***Ayarlar kataloğu (önizleme)***: [Ayarlar kataloğunu (önizleme)](/mem/intune/configuration/settings-catalog) kullanma yönergelerine bakın.
- **Grup ilkesi**: Şirket içi Active Directory'nizi kullanarak kullanıcılara ve bilgisayarlara grup ilkesi nesneleri (GPO'lar) dağıtın. Bu ayar için bir GPO oluşturmak için en son [Yönetim Şablonu dosyalarını (ADMX/ADML) ve Kurumlar için Microsoft 365 Uygulamaları, Office 2019 ve Office 2016 için Office Özelleştirme Aracı'nı](https://www.microsoft.com/download/details.aspx?id=49030) indirin.

## <a name="known-issues"></a>Bilinen sorunlar

- **İlke VBA Makro bildirimleri** (Access, PowerPoint, Visio, Word) veya **Makro bildirimleri** (Excel) **Dijital olarak imzalanan makrolar dışında tümünü devre dışı bırak** değerine ayarlandığında, beklenen güven çubuğu görüntülenmez ve backstage'daki **Güvenlik Bilgileri**, ayar beklendiği gibi çalışıyor olsa bile engellenen makroların ayrıntılarını listelemez. Office ekibi bu sorunu çözmek için çalışıyor.

## <a name="admin-options-for-restricting-active-content"></a>Etkin içeriği kısıtlamak için yönetici seçenekleri

Dahili olarak oluşturulan içerikte güven düzeyinde kullanıcıların internetten indirebilecekleri içerikle karşıtlıkta büyük bir fark vardır. İç belgelerde etkin içeriğe izin vermeyi ve genel olarak İnternet'ten gelen belgelerde etkin içeriğe izin vermemeyi göz önünde bulundurun.

Kullanıcılarınızın belirli etkin içerik türlerine ihtiyacı yoksa, en güvenli seçeneğiniz bu etkin içeriğe kullanıcı erişimini kapatmak ve gerektiğinde özel durumlara izin vermek için ilkeleri kullanmaktır.

Aşağıdaki ilkeler kullanılabilir:

- **Güvenilen Konumlar**: Kullanılabilir gruplar için özel durumları kapatın.
- **Güvenilen Belgeler**: Kullanılabilir gruplar için özel durumları kapatın.
- **Tüm etkin içeriği kapatın**: Kişiler için özel durumlar.

Aşağıdaki bölümlerde yer alan tablolarda etkin içeriği denetleyen ayarlar açıklanmaktadır. Kullanıcılara uygulanırsa bu ilkeler güvenilen belgelere uygulanır ve önceki son kullanıcı deneyimi aynı olmayabilir. Tablolar ayrıca önerilen güvenlik temelleri ayarını da içerir ve kullanıcı geçersiz kılma isteminin kullanılabilir olduğu diğer ayarları tanımlar (kullanıcının etkin içeriği etkinleştirmesine izin verir).

### <a name="hkey_current_user-settings"></a>HKEY_CURRENT_USER ayarları

<p>

****
|Kategori|Uygulama|İlke adı|Güvenlik temeli<br>ayarı (önerilir)|Kullanıcı istemiyle ayarlama<br>ve geçersiz kılabilirsiniz?|
|---|---|---|---|---|
|ActiveX|Office|denetim başlatmayı ActiveX|**6**|Aşağıdaki değerler için **Evet**: <ul><li>**3**</li><li>**4**</li><li>**5**</li><li>**6**</li></ul>|
|ActiveX|Office|Etkin X One Off Formlara İzin Ver|**Yalnızca Outlook Denetimlerini yükleme**|Hayır|
|ActiveX|Office|nesneleri ActiveX denetleme|Güvenlik temeli ayarı değil.|Hayır|
|ActiveX|Office|Tüm ActiveX Devre Dışı Bırak|Güvenlik temeli ayarı değil.|Aşağıdaki değerler için **Evet**: <ul><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|ActiveX|Office|Forms3'te Yük Denetimleri|**1**|Aşağıdaki değerler için **Evet**: <ul><li>**2**</li><li>**3**</li></ul>|
|Eklentiler & Genişletilebilirlik|Excel <p> PowerPoint <p> Project <p> Publisher <p> Visio <p> Word|İmzasız uygulama eklentileri için Güven Çubuğu Bildirimi'ni devre dışı bırakma ve bunları engelleme|**Etkin**|**Devre Dışı** değeri için **Evet**.|
|Eklentiler & Genişletilebilirlik|Excel <p> PowerPoint <p> Project <p> Publisher <p> Visio <p> Word|Uygulama eklentilerinin Güvenilen Publisher tarafından imzalandığını zorunlu Publisher|**Etkin**|Hayır|
|Eklentiler & Genişletilebilirlik|Excel|Otomatik Yeniden Yayımlama uyarısını gösterme|**Devre dışı**|Hayır|
|Eklentiler & Genişletilebilirlik|Excel|WEBHİzMETİ İşlev Bildirimi Ayarlar|**Bildirimle tümünü devre dışı bırakma**|Aşağıdaki değerler için **Evet**: <ul><li>**Bildirimle tümünü devre dışı bırakma**</li><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Eklentiler & Genişletilebilirlik|Office|yayımlanan bağlantılar için Office istemcisinin SharePoint Sunucusu'nu yoklamasını devre dışı bırakma|**Devre dışı**|Hayır|
|Eklentiler & Genişletilebilirlik|Office|Belge ve şablonlardan kullanıcı arabirimi genişletmeyi devre dışı bırakma|Word'de İzin Verme = Doğru <p> Project = Yanlış olarak izin verme <p> Excel = True'da izin verme <p> Visio= False'ta izin verme <p> PowerPoint = Doğru olarak izin verme <p> Access'te İzin Verme = Doğru <p> Outlook = True'da İzin Verme <p> Publisher = Doğru'da izin verme <p> InfoPath'te İzin Verme = Doğru|Hayır|
|Eklentiler & Genişletilebilirlik|Outlook|Adres defterine erişirken nesne modeli istemini Outlook yapılandırma|**Otomatik Olarak Reddet**|Aşağıdaki değerler için **Evet**: <ul><li>**Kullanıcıya sor**</li><li>**Kullanıcıdan bilgisayar güvenliğine göre iste**</li><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Eklentiler & Genişletilebilirlik|Outlook|UserProperty nesnesinin Formula özelliğine erişirken Outlook nesne modeli istemini yapılandırma|**Otomatik Olarak Reddet**|Aşağıdaki değerler için **Evet**: <ul><li>**Kullanıcıya sor**</li><li>**Kullanıcıdan bilgisayar güvenliğine göre iste**</li><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Eklentiler & Genişletilebilirlik|Outlook|Farklı Kaydet yürütülürken Outlook nesne modeli istemini yapılandırma|**Otomatik Olarak Reddet**|Aşağıdaki değerler için **Evet**: <ul><li>**Kullanıcıya sor**</li><li>**Kullanıcıdan bilgisayar güvenliğine göre iste**</li><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Eklentiler & Genişletilebilirlik|Outlook|Adres bilgilerini okurken Outlook nesne modeli istemini yapılandırma|**Otomatik Olarak Reddet**|Aşağıdaki değerler için **Evet**: <ul><li>**Kullanıcıya sor**</li><li>**Kullanıcıdan bilgisayar güvenliğine göre iste**</li><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Eklentiler & Genişletilebilirlik|Outlook|Toplantı ve görev isteklerine yanıt verirken nesne modeli istemini Outlook yapılandırma|**Otomatik Olarak Reddet**|Aşağıdaki değerler için **Evet**: <ul><li>**Kullanıcıya sor**</li><li>**Kullanıcıdan bilgisayar güvenliğine göre iste**</li><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Eklentiler & Genişletilebilirlik|Outlook|Posta gönderirken Outlook nesne modeli istemini yapılandırma|**Otomatik Olarak Reddet**|Aşağıdaki değerler için **Evet**: <ul><li>**Kullanıcıya sor**</li><li>**Kullanıcıdan bilgisayar güvenliğine göre iste**</li><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Eklentiler & Genişletilebilirlik|Outlook|Outlook nesne modeli özel eylemler yürütme istemi ayarlama|**Otomatik Olarak Reddet**|Aşağıdaki değerler için **Evet**: <ul><li>**Kullanıcıya sor**</li><li>**Kullanıcıdan bilgisayar güvenliğine göre iste**</li><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Eklentiler & Genişletilebilirlik|PowerPoint|Programları Çalıştırma|**devre dışı bırakma (hiçbir programı çalıştırma)**|Etkinleştir değeri için **Evet** **(çalıştırmadan önce kullanıcıya sor)**|
|Eklentiler & Genişletilebilirlik|Word <p> Excel|Akıllı Belge'nin bildirim kullanımını devre dışı bırakma|**Etkin**|Hayır|
|DDE|Excel|Excel'da Dinamik Veri Exchange (DDE) sunucusunun başlatılmasına izin verme|**Etkin**|**Yapılandırılmadı** değeri için **Evet**.|
|DDE|Excel|Excel'da Dinamik Veri Exchange (DDE) sunucu aramasına izin verme|**Etkin**|Aşağıdaki değerler için **Evet**: <ul><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|DDE|Word|Dinamik Veri Exchange|**Devre dışı**|Hayır|
|Jscript & VBScript|Outlook|Tek seferlik Outlook formlarında betiklere izin ver|**Devre dışı**|Hayır|
|Jscript & VBScript|Outlook|ortak klasörler için Outlook nesne modeli betiklerinin çalışmasına izin verme|**Etkin**|Hayır|
|Jscript & VBScript|Outlook|Paylaşılan klasörler için Outlook nesne modeli betiklerinin çalışmasına izin verme|**Etkin**|Hayır|
|Makrolar|Excel|Makro Bildirimleri|**Dijital olarak imzalanan makrolar dışında tümünü devre dışı bırakma**|Aşağıdaki değerler için **Evet**: <ul><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Makrolar|Access <p> PowerPoint <p> Project <p> Publisher <p> Visio <p> Word|VBA Makro Bildirimi Ayarlar|**Dijital olarak imzalanan makrolar dışında tümünü devre dışı bırakma** <p> ve <p> **Makroların güvenilir bir yayımcı tarafından imzalanması gerektir**|Aşağıdaki değerler için **Evet**: <ul><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Makrolar|Access <p> Excel <p> PowerPoint <p> Visio <p> Word|Makroların İnternet'ten Office dosyalarında çalışmasını engelleme|**Etkin**|Aşağıdaki değerler için **Evet**: <ul><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Makrolar|Excel|XML Çalışma Kitaplarını Açma Excel şifrelenmiş makroları tarama|**Şifrelenmiş makroları tarama (varsayılan)**|Hayır|
|Makrolar|Office|VBA'nın typelib başvurularını güvenilmeyen intranet konumlarından yola göre yüklemesine izin ver|**Devre dışı**|Hayır|
|Makrolar|Office|Otomasyon Güvenliği|**Uygulama makro güvenlik düzeyini kullanma**|Hayır|
|Makrolar|Office|Yerel makinedeki güvenli olmayan konumlara başvurabilen VBA kitaplık başvurularında diğer güvenlik denetimlerini devre dışı bırakma|**Devre dışı**|Hayır|
|Makrolar|Office|Makro Çalışma Zamanı Tarama Kapsamı|**Tüm belgeler için etkinleştir**|Hayır|
|Makrolar|Office|Yalnızca V3 imzaları kullanan VBA makrolarına güvenin|Güvenlik temeli ayarı değil.|Hayır|
|Makrolar|Outlook|Outlook Güvenlik Modu|**Outlook Güvenlik grup ilkesi kullanma**|Tüm Outlook GPO ayarlarını etkinleştirmek için gereklidir. <p> Bağımlılık olarak bahsedildi (bu ilke etkin içeriğin kendisini engellemez).|
|Makrolar|Outlook|Makrolar için güvenlik ayarı|**İmzalı için uyar, imzasızı devre dışı bırak**|Aşağıdaki değerler için **Evet**: <ul><li>**Her zaman uyar**</li><li>**İmzalı için uyar, imzasızı devre dışı bırak**</li><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Makrolar|PowerPoint|XML sunularını açma PowerPoint şifrelenmiş makroları tarama|**Şifrelenmiş makroları tarama (varsayılan)**|Hayır|
|Makrolar|Publisher|Publisher Otomasyon Güvenlik Düzeyi|**Kullanıcı arabirimine göre (istendi)**|Hayır|
|Makrolar|Word|Word Open XML belgelerinde şifrelenmiş makroları tarama|**Şifrelenmiş makroları tarama (varsayılan)**|Hayır|
|

### <a name="hkey_local_machine-settings"></a>HKEY_LOCAL_MACHINE ayarları

<p>

****
|Kategori|Uygulama|İlke adı|Güvenlik temeli<br>ayarı (önerilir)|Kullanıcı istemiyle ayarlama<br>ve geçersiz kılabilirsiniz?|
|---|---|---|---|---|
|ActiveX|Office|ActiveX Yüklemesini Kısıtla|excel.exe = Doğru <p> exprwd.exe = Doğru <p> groove.exe = Doğru <p> msaccess.exe = Doğru <p> mse7.exe = Doğru <p> mspub.exe = Doğru <p> onent.exe = Doğru <p> outlook.exe = Doğru <p> powerpnt.exe = Doğru <p> pptview.exe = Doğru <p> spDesign.exe = Doğru <p> visio.exe = Doğru <p> winproj.exe = Doğru <p> winword.exe = Doğru|Hayır|
|Eklentiler & Genişletilebilirlik|Office|Eklenti Yönetimi|excel.exe = Doğru <p> exprwd.exe = Doğru <p> groove.exe = Doğru <p> msaccess.exe = Doğru <p> mse7.exe = Doğru <p> mspub.exe = Doğru <p> onent.exe = Doğru <p> outlook.exe = Doğru <p> powerpnt.exe = Doğru <p> pptview.exe = Doğru <p> spDesign.exe = Doğru <p> visio.exe = Doğru <p> winproj.exe = Doğru <p> winword.exe = Doğru|Hayır|
|Eklentiler & Genişletilebilirlik|Office|Office belgelerde Flash etkinleştirmeyi engelleme|Microsoft 365 uygulamalarında Flash için tüm etkinleştirmeyi engellemek için COM sonlandırma bitlerinin listesi için Microsoft Güvenlik Kılavuzu ADMX/ADML dosyalarına bakın. Kurumsal Güvenlik Temelleri için ADMX/ADML dosyaları [, Güvenlik Uyumluluk Araç Seti'nde](https://www.microsoft.com/download/details.aspx?id=55319) kullanılabilir.|Hayır|
|Jscript & VBScript|Office|Office için eski JScript yürütmeyi kısıtlama|**Etkin**: <p> Erişim: 69632 <p> Excel: 69632 <p> OneNote: 69632 <p> Outlook: 69632 <p> PowerPoint: 69632 <p> Project: 69632 <p> Publisher: 69632 <p> Visio: 69632 <p> Sözcük: 69632|Hayır|
|Jscript & VBScript|Office|Betikli Pencere Güvenlik Kısıtlamaları|excel.exe = Doğru <p> exprwd.exe = Doğru <p> groove.exe = Doğru <p> msaccess.exe = Doğru <p> mse7.exe = Doğru <p> mspub.exe = Doğru <p> onent.exe = Doğru <p> outlook.exe = Doğru <p> powerpnt.exe = Doğru <p> pptview.exe = Doğru <p> spDesign.exe = Doğru <p> visio.exe = Doğru <p> winproj.exe = Doğru <p> winword.exe = Doğru|Hayır|
|
