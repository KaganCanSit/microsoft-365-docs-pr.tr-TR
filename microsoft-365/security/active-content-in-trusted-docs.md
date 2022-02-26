---
title: IT yöneticileri için Office belgelerde etkin içeriği yönetme
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: tutorial
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ROBOTS: NOINDEX,NOFOLOW
description: Yöneticiler, iş yerlerinde veya belgelerde etkin içeriği engellemek için Office öğrenebilir
ms.openlocfilehash: 5bc187caaeac2fb83cb7d5a8026af2e1548c5622
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "62973874"
---
# <a name="manage-active-content-in-office-documents"></a>Belgelerde etkin Office yönetme

> [!NOTE]
> Bu makalede açıklanan özellikler Önizleme'dedir, herkes tarafından kullanılamaz ve  değişiklik olabilir.

Office içeriği olduğunda otomatik olarak yenilenebilir, güncelleştirilebilir veya _yürütülebilir_. Etkin içeriğe örnek olarak makrolar, ActiveX denetimleri ve Office eklentileri yer almaktadır. Etkin içerik kullanıcılara güçlü ve yararlı işlevler sağlar, ancak saldırganlar kötü amaçlı yazılım teslim etmek için etkin içeriği de kullanabilir.

Yöneticiler, etkin içeriğin kullanımını belirli kullanıcı gruplarıyla sınırlandıran veya etkin içeriği tamamen devre dışı bırakmak için kuruluş ilkeleri (grup ilkeleri veya bulut ilkeleri) oluşturabilir. Kullanıcılar, Dosya Seçenekleri Güven Merkezi'nde bulunan Office Güven Merkezi'nde kendi güvenlik Office **gizlilik** \>  \> **ayarlarını yapılandırabilirsiniz**.

Daha önce, kullanıcılar belgeleri güvenilir belge olarak tanımlarında, yöneticilerin kendi belgelerinde etkin içeriği engellemek üzere yapılandırmış ilkeleri yapılandırmış olsalar bile, etkin içeriğin Office olanak sağlardı. Artık, yöneticiler tarafından ayarlanmış ilkeler güvenilen belgelerin kullanıcı kimliğine göre öncelikli. Bu davranış değişikliği kullanıcılar için soruna neden olabilir.

Güncelleştirilmiş Güven Merkezi mantığı aşağıdaki diyagramda açıklanmıştır:

:::image type="content" source="../media/office-trust-center-flow.png" alt-text="Microsoft 365 Defender portalında Güven merkezi Mantığının açık olduğu akış Microsoft 365 Defender örneği" lightbox="../media/office-trust-center-flow.png":::

1. Bir kullanıcı, Office içeren bir belge açar.

2. Belge güvenilir bir konumdansa, etkin içerik etkin olarak açılır. Belge güvenilir bir konumdan değilse, değerlendirme devam eder.

3. Güncelleştirilmiş davranış bu noktada yürürlüğe girecektir:
   - Daha önce, kullanıcı bu belgeyi güvenilir belge olarak tanım olsaydı sonraki değerlendirilen ayar vardı. Varsa, belge etkin içerik etkin olarak açılır.
   - Artık, kullanıcının belgeyi güvenilir belge olarak tanım isteyip eklemediği burada dikkate alınmaz (şimdi 8. adım).

     Bu, davranışın temel değişikliğidir: Güvenilir belgenin kullanıcı ataması dikkate alınmadan önce bulut ilkeleri (4. adım), grup ilkeleri (6. adım) ve  yerel ayarlar (7. adım) denetlenir. Bu adımlardan herhangi biri etkin içeriğe erişimi engellese ve adımlardan hiçbiri kullanıcının geçersiz kılmasına izin vermiyorsa, belgenin güvenilir belge olarak kullanıcı kimliği temel olarak önemli değildir.

4. Bulut ilkeleri, bu etkin içerik türüne izin verili olup İzin verilmiyor veya engellenmiş olup değildir. Etkin içerik engellenmiş durumda değil, değerlendirme 6. adıma devam eder.

   Etkin içerik ilke tarafından engellendiyseniz, deneyim 5. adımda açıklanmıştır.

5. Belgenin açılması, güven çubuğunda bir bildirimle engellenir. Bundan sonra ne olacak, ilkede kullanıcı geçersiz kılma ayarları tarafından denetlendi: a. **Kullanıcı geçersiz kılmaya izin** verilmiyor: Kullanıcı belgeyi açabilirsiniz ve değerlendirme durur.
   b. **Kullanıcı geçersiz kılma izni** verildi: Kullanıcı güven çubuğundaki bağlantıya tıklayarak belgeyi etkin içerik etkin durumda açabilir.

6. Grup ilkeleri, bu etkin içerik türüne izin verili olup İzin verilmiyor veya engellenmiş olup değildir. Etkin içerik engellenmiş durumda değil, değerlendirme 7. adıma devam eder.

   Etkin içerik ilke tarafından engellendiyseniz, deneyim 5. adımda açıklanmıştır.

7. Yerel ayarlar, bu etkin içerik türüne izin verili olup İzin verilmiyor veya engellenmiş olup değildir. Etkin içerik engellenirse, belgenin açılması güven çubuğunda bir bildirimle engellenir. Etkin içerik engellenmiş durumda değil, değerlendirme devam eder.

8. Kullanıcı daha önce belgeyi güvenilir belge olarak tanımdiyse, etkin içerik etkin olarak açılır. Engellenmişse, belgenin açılması engellenir.

## <a name="what-is-a-trusted-document"></a>Güvenilen belge nedir?

Güvenilen belgeler Office, belgeye güvenlik istemi, denetim ve diğer etkin içerik türleri sorulmadan ActiveX belgeler olarak açılır. Belgeyi açmak için Korumalı Görünüm veya Application Guard kullanılır. Kullanıcılar güvenilen belgeyi açtıklerinde ve tüm etkin içerik etkin olduğunda. Belgede yeni etkin içerik veya var olan etkin içerikte güncelleştirmeler olsa bile, kullanıcılar belgeyi bir sonraki açişlerinde güvenlik istemlerini almazlar.

Bu davranış nedeniyle, kullanıcılar yalnızca belge kaynağına güvenseler belgelere güvenebilirler.

Yönetici etkin içeriği bir ilke kullanarak engellerse veya kullanıcılar etkin içeriği engelleyen bir Güven Merkezi ayarı ayarlarsa, etkin içerik engellenmiş olarak kalır.

Daha fazla bilgi için aşağıdaki makalelere bakın:

- [Güvenilen belgeler](https://support.microsoft.com/topic/trusted-documents-cf872bd8-47ec-4c02-baa5-1fdba1a11b53)
- [Güvenilen bir konum ekleme, kaldırma veya değiştirme](https://support.microsoft.com/topic/add-remove-or-change-a-trusted-location-7ee1cdc2-483e-4cbb-bcb3-4e7c67147fb4)
- [Dosyalarınıza etkin içerik türleri](https://support.microsoft.com/topic/active-content-types-in-your-files-b7ff2e8a-4055-47d4-8c7d-541e19f62bea)

## <a name="configure-trusted-document-settings-in-office-policies"></a>İlkelere göre güvenilen Office yapılandırma

Yöneticilerin, kuruluşta kimlik Office birçok yolu vardır. Örneğin:

- **Office ilke** hizmeti: Azure AD hesabıyla Office uygulamalarına erişen tüm cihazlarında kullanıcılara uygulanan kullanıcı tabanlı bir ilke ayarlayın. İlke Bulut [İlkesi Hizmeti'Office bulut ilkesi yapılandırması](/DeployOffice/overview-office-cloud-policy-service) [oluşturma Office adımlara bakın](https://config.office.com/officeSettings/officePolicies).
- **Intune'da** Office ilkeleri: HKCU ilkelerini Ayarlar PC'lere dağıtmak için Intune Ayarlar kataloğunu veya Yönetim şablonlarını kullanın: Windows 10 CIHAZLAR Yapılandırma Profilleri altındaki [MEM yönetim](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/configurationProfiles)  \> **merkezinde.**
  - ***Yönetim Şablonları***: Yönetim Şablonlarını yapılandırmak Windows 10 [yönergelere bakın](/mem/intune/configuration/administrative-templates-windows).
  - ***Ayarlar kataloğu (önizleme)***: Önizleme kataloğunu [(Ayarlar) kullanma yönergelerine bakın](/mem/intune/configuration/settings-catalog).
- **Grup ilkesi**: Grup ilkesi nesnelerini (GPOS) kullanıcılara ve bilgisayarlara dağıtmak için şirket içi Active Directory'nizi kullanın. Bu ayara yönelik bir GPO oluşturmak için, en son Yönetim Şablonu dosyalarını [(ADMX/ADML) ve Office Kurumlar için Microsoft 365 Uygulamaları, Office 2019 ve Office 2016 için Office'i](https://www.microsoft.com/download/details.aspx?id=49030) indirin.

## <a name="known-issues"></a>Bilinen sorunlar

- **VBA** Makro bildirimleri (Access, PowerPoint, Visio, Word) veya Makro **bildirimleri (Excel**) değerine Devre dışı bırak değerine ayarlendiğinde **, beklenen** güven çubuğu görüntülenmez ve ayar beklendiği gibi çalışsa da Backstage'de Güvenlik Bilgileri engellenen makroların ayrıntılarını listelemiyor. Ekibin Office sorunu çözmek için çalışıyor.

## <a name="admin-options-for-restricting-active-content"></a>Etkin içeriği kısıtlamak için yönetici seçenekleri

Güven düzeyinde, dahili olarak oluşturulan içerikle kullanıcıların İnternet'te indir olduğu içerik arasında büyük bir fark vardır. İç belgelerde etkin içeriğe izin verme ve İnternet'in belgelerinde etkin içeriğe genel olarak izin verme gibi düşünebilirsiniz.

Kullanıcılarınızı belirli türlerde etkin içeriklere gerek yoksa, en güvenli seçeneğiniz, ilkeleri kullanarak bu etkin içeriğe kullanıcı erişimini kapatmak ve gerektiğinde özel durumlara izin vermektir.

Aşağıdaki ilkeler kullanılabilir:

- **Güvenilen Konumlar: Kullanılabilir** gruplar için özel durumlar'i kapatın.
- **Güvenilen Belgeler: Kullanılabilir** gruplar için özel durumlar'i kapatın.
- **Tüm etkin içeriği kapatma**: Kişiler için özel durumlar.

Aşağıdaki bölümlerdeki tablolarda etkin içeriği denetleme ayarları açıklanmaktadır. Kullanıcılara uygulanan bu ilkeler güvenilen belgeler üzerinde zorunlu kılınacak ve önceki son kullanıcı deneyimi aynı olmayacaktır. Tablolarda önerilen güvenlik taban çizgisi ayarı da yer alır ve kullanıcı geçersiz kılma isteminin kullanılabilir olduğu diğer ayarları da tanımlayabilirsiniz (kullanıcının etkin içeriği etkinleştirmesini sağlar).

### <a name="hkey_current_user-settings"></a>HKEY_CURRENT_USER ayarları

<p>

****
|Kategori|Uygulama|İlke adı|Güvenlik temeli<br>ayar (önerilir)|Kullanıcı istemiyle ayar<br>ve geçersiz kılma kullanılabilir mi?|
|---|---|---|---|---|
|ActiveX|Office|ActiveX Denetimi Başlatma|**6**|**Evet** , aşağıdaki değerler için: <ul><li>**3**</li><li>**4**</li><li>**5**</li><li>**6**</li></ul>|
|ActiveX|Office|Active X Bir Kapatma Formlarına İzin Ver|**Yalnızca Yükleme Outlook Denetimleri**|Hayır|
|ActiveX|Office|Nesneleri ActiveX denetleme|Güvenlik temeli ayarı değil.|Hayır|
|ActiveX|Office|Tüm Güncelleştirmeleri Devre Dışı ActiveX|Güvenlik temeli ayarı değil.|**Evet** , aşağıdaki değerler için: <ul><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|ActiveX|Office|Forms3'te Denetimleri Yükleme|**1**|**Evet** , aşağıdaki değerler için: <ul><li>**2**</li><li>**3**</li></ul>|
|Eklentiler & Genişletilebilirlik|Excel <p> PowerPoint <p> Project <p> Publisher <p> Visio <p> Word|Imzalanmamış uygulama eklentileri için Güven Çubuğu Bildirimi'yi devre dışı bırakma ve bunları engelleme|**Etkin**|**Devre** Dışı değeri için **Evet**.|
|Eklentiler & Genişletilebilirlik|Excel <p> PowerPoint <p> Project <p> Publisher <p> Visio <p> Word|Uygulama eklentilerinin Güvenilen kişi tarafından imza at Publisher|**Etkin**|Hayır|
|Eklentiler & Genişletilebilirlik|Excel|Otomatik Yayımla uyarıyı gösterme|**Devre dışı**|Hayır|
|Eklentiler & Genişletilebilirlik|Excel|WEBSERVICE İşlevi Bildirim Ayarlar|**Tüm bildirimleri devre dışı bırak**|**Evet** , aşağıdaki değerler için: <ul><li>**Tüm bildirimleri devre dışı bırak**</li><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Eklentiler & Genişletilebilirlik|Office|Yayımlanan Office için SharePoint Server'da yoklama istemcisini devre dışı bırakma|**Devre dışı**|Hayır|
|Eklentiler & Genişletilebilirlik|Office|Belgelerden ve şablonlardan kullanıcı arabirimi genişletmeyi devre dışı bırakma|Word'de izin yok = True <p> Project = False <p> Excel = True izin yok <p> Visio= False Visio izin yok <p> PowerPoint = True'de izin yok <p> Access'te izin yok = True <p> Outlook = True Outlook izin yok <p> Publisher = True'de izin yok <p> InfoPath'te izin yok = True|Hayır|
|Eklentiler & Genişletilebilirlik|Outlook|Adres Outlook erişirken nesne modeli istemini yapılandırma|**Otomatik Olarak Reddet**|**Evet** , aşağıdaki değerler için: <ul><li>**Kullanıcıya sor**</li><li>**Bilgisayar güvenliğine dayalı olarak kullanıcıya sor**</li><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Eklentiler & Genişletilebilirlik|Outlook|UserProperty Outlook Formül özelliğine erişirken nesne modeli istemini yapılandırma|**Otomatik Olarak Reddet**|**Evet** , aşağıdaki değerler için: <ul><li>**Kullanıcıya sor**</li><li>**Bilgisayar güvenliğine dayalı olarak kullanıcıya sor**</li><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Eklentiler & Genişletilebilirlik|Outlook|Farklı Outlook yürütürken nesne modeli istemini yapılandırma|**Otomatik Olarak Reddet**|**Evet** , aşağıdaki değerler için: <ul><li>**Kullanıcıya sor**</li><li>**Bilgisayar güvenliğine dayalı olarak kullanıcıya sor**</li><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Eklentiler & Genişletilebilirlik|Outlook|Adres Outlook okurken nesne modeli istemini yapılandırma|**Otomatik Olarak Reddet**|**Evet** , aşağıdaki değerler için: <ul><li>**Kullanıcıya sor**</li><li>**Bilgisayar güvenliğine dayalı olarak kullanıcıya sor**</li><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Eklentiler & Genişletilebilirlik|Outlook|Toplantı Outlook görev isteklerine yanıt veremiyorken nesne modeli istemini yapılandırma|**Otomatik Olarak Reddet**|**Evet** , aşağıdaki değerler için: <ul><li>**Kullanıcıya sor**</li><li>**Bilgisayar güvenliğine dayalı olarak kullanıcıya sor**</li><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Eklentiler & Genişletilebilirlik|Outlook|Posta Outlook nesne modeli istemini yapılandırma|**Otomatik Olarak Reddet**|**Evet** , aşağıdaki değerler için: <ul><li>**Kullanıcıya sor**</li><li>**Bilgisayar güvenliğine dayalı olarak kullanıcıya sor**</li><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Eklentiler & Genişletilebilirlik|Outlook|Nesne Outlook özel eylemler yürütme istemini ayarlama|**Otomatik Olarak Reddet**|**Evet** , aşağıdaki değerler için: <ul><li>**Kullanıcıya sor**</li><li>**Bilgisayar güvenliğine dayalı olarak kullanıcıya sor**</li><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Eklentiler & Genişletilebilirlik|PowerPoint|Programları Çalıştırma|**devre dışı bırak (hiçbir program çalıştırma)**|**Etkinleştir** değeri için **Evet (çalıştırmadan önce kullanıcıya sor)**|
|Eklentiler & Genişletilebilirlik|Word <p> Excel|Akıllı Belgenin bildirim kullanımını devre dışı bırakma|**Etkin**|Hayır|
|DDE|Excel|Sunucuda Dinamik Veri Kaynağı (DDE) Exchange başlatmasına izin Excel|**Etkin**|**Yapılandırılmadı** **değeri için Evet**.|
|DDE|Excel|Herhangi bir aralıkta Dinamik Exchange (DDE) sunucu aramasına izin Excel|**Etkin**|**Evet** , aşağıdaki değerler için: <ul><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|DDE|Word|Dinamik Veri Exchange|**Devre dışı**|Hayır|
|Jscript & VBScript|Outlook|Bire bir formlarda betiklere Outlook verme|**Devre dışı**|Hayır|
|Jscript & VBScript|Outlook|Ortak klasörler için Outlook modeli betiklerini çalıştırmaya izin verme|**Etkin**|Hayır|
|Jscript & VBScript|Outlook|Paylaşılan klasörlerde Outlook modeli betiklerini çalıştırmasına izin verme|**Etkin**|Hayır|
|Makrolar|Excel|Makro Bildirimleri|**Dijital olarak imzalanmış makrolar dışında tüm makroları devre dışı bırak**|**Evet** , aşağıdaki değerler için: <ul><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Makrolar|Access <p> PowerPoint <p> Project <p> Publisher <p> Visio <p> Word|VBA Makro Bildirim Ayarlar|**Dijital olarak imzalanmış makrolar dışında tüm makroları devre dışı bırak** <p> ve <p> **Makroların güvenilen bir yayıncı tarafından imzalanacak şekilde imza attır**|**Evet** , aşağıdaki değerler için: <ul><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Makrolar|Access <p> Excel <p> PowerPoint <p> Visio <p> Word|İnternet'te makroların Office dosyaları çalıştırmalarını engelleme|**Etkin**|**Evet** , aşağıdaki değerler için: <ul><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Makrolar|Excel|Open XML çalışma kitaplarında Excel makroları tarama|**Şifreli makroları tarama (varsayılan)**|Hayır|
|Makrolar|Office|VBA'nın başvuru türü başvurularını güvenilmeyen intranet konumlarından bir yola göre yüklemesine izin verme|**Devre dışı**|Hayır|
|Makrolar|Office|Otomasyon Güvenliği|**Uygulama makrosu güvenlik düzeyini kullanma**|Hayır|
|Makrolar|Office|Yerel makinedeki güvenli olmayan konumlara başvurabilecek VBA kitaplığı başvurularına ek güvenlik denetimlerini devre dışı bırakma|**Devre dışı**|Hayır|
|Makrolar|Office|Makro Çalışma Zamanı Tarama Kapsamı|**Tüm belgeler için etkinleştirme**|Hayır|
|Makrolar|Office|Yalnızca V3 imzaları kullanan VBA makrolara güven|Güvenlik temeli ayarı değil.|Hayır|
|Makrolar|Outlook|Outlook Modu|**Güvenlik Outlook İlkesi kullanma**|Tüm yeni GPO ayarlarını Outlook için gereklidir. <p> Bağımlılık olarak bahsedilen (bu ilke etkin içeriğin kendisini engellemez).|
|Makrolar|Outlook|Makrolar için güvenlik ayarı|**İmzalı için uyar, imzasızları devre dışı bırak**|**Evet** , aşağıdaki değerler için: <ul><li>**Her zaman uyar**</li><li>**İmzalı için uyar, imzasızları devre dışı bırak**</li><li>**Devre dışı**</li><li>**Yapılandırılmadı**</li></ul>|
|Makrolar|PowerPoint|Open XML sunularında şifrelenmiş PowerPoint tarama|**Şifreli makroları tarama (varsayılan)**|Hayır|
|Makrolar|Publisher|Publisher Otomasyon Güvenlik Düzeyi|**Kullanıcı arabirimine göre (istenir)**|Hayır|
|Makrolar|Word|Word Open XML belgesinde şifreli makroları tarama|**Şifreli makroları tarama (varsayılan)**|Hayır|
|

### <a name="hkey_local_machine-settings"></a>HKEY_LOCAL_MACHINE ayarlarını değiştirme

<p>

****
|Kategori|Uygulama|İlke adı|Güvenlik temeli<br>ayar (önerilir)|Kullanıcı istemiyle ayar<br>ve geçersiz kılma kullanılabilir mi?|
|---|---|---|---|---|
|ActiveX|Office|ActiveX Kısıtlama|excel.exe = True <p> exprwd.exe = True <p> groove.exe = True <p> msaccess.exe = True <p> mse7.exe = True <p> mspub.exe = True <p> onent.exe = True <p> outlook.exe = True <p> powerpnt.exe = True <p> pptview.exe = True <p> spDesign.exe = True <p> visio.exe = True <p> winproj.exe = True <p> winword.exe = True|Hayır|
|Eklentiler & Genişletilebilirlik|Office|Eklenti Yönetimi|excel.exe = True <p> exprwd.exe = True <p> groove.exe = True <p> msaccess.exe = True <p> mse7.exe = True <p> mspub.exe = True <p> onent.exe = True <p> outlook.exe = True <p> powerpnt.exe = True <p> pptview.exe = True <p> spDesign.exe = True <p> visio.exe = True <p> winproj.exe = True <p> winword.exe = True|Hayır|
|Eklentiler & Genişletilebilirlik|Office|Belgelerde Flash etkinleştirmeyi Office engelleme|Bu uygulamalarda Flash için tüm etkinleştirmeyi engellemek için COM killbitlerinin listesi için Microsoft Güvenlik Kılavuzu ADMX/ADML Microsoft 365 bakın. Kurumsal Güvenlik Taban Çizgilerine yönelik ADMX/ADML dosyaları, Güvenlik Uyumluluğu [Araç Seti'ne mevcuttur](https://www.microsoft.com/download/details.aspx?id=55319).|Hayır|
|Jscript & VBScript|Office|Erişim için JScript yürütmeyi Office|**Etkin**: <p> Access: 69632 <p> Excel: 69632 <p> OneNote: 69632 <p> Outlook: 69632 <p> PowerPoint: 69632 <p> Project: 69632 <p> Publisher: 69632 <p> Visio: 69632 <p> Word: 69632|Hayır|
|Jscript & VBScript|Office|Komut Dosyası Pencere Güvenlik Kısıtlamaları|excel.exe = True <p> exprwd.exe = True <p> groove.exe = True <p> msaccess.exe = True <p> mse7.exe = True <p> mspub.exe = True <p> onent.exe = True <p> outlook.exe = True <p> powerpnt.exe = True <p> pptview.exe = True <p> spDesign.exe = True <p> visio.exe = True <p> winproj.exe = True <p> winword.exe = True|Hayır|
|
