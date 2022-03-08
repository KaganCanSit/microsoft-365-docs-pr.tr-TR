---
title: Temel Hareketlilik ve Güvenlik Özellikleri
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: Temel Mobil Kullanım ve Güvenlik, mobil cihazlarınızı güvenli hale yönetmenize yardımcı olabilir.
ms.openlocfilehash: 04ee7e7dfbc4937d4add2e4c27e7f686b596fadb
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314889"
---
# <a name="capabilities-of-basic-mobility-and-security"></a>Temel Hareketlilik ve Güvenlik Özellikleri

Temel Mobil Kullanım ve Güvenlik, iPhone, iPad, Android ve Windows Gibi mobil cihazları, Microsoft 365 lisanslı kullanıcılar tarafından kullanılan telefonları güvenli Microsoft 365 yardımcı olabilir. Desteklenen mobil cihazlar ve uygulamalar için e-posta ve belgelere erişim Microsoft 365 ayarlarla mobil cihaz yönetimi ilkeleri oluşturabilirsiniz. Bir cihaz kaybolur veya çalınırsa hassas kuruluş bilgilerini kaldırmak için cihazı uzaktan silebilirsiniz.

## <a name="supported-operating-systems"></a>Desteklenen işletim sistemleri

Temel Microsoft Intune ve Güvenlik ile cihazlar için minimum desteklenen işletim sistemleri kılavuzuna bakın. Daha fazla bilgi için [bkz. Intune'da desteklenen işletim sistemleri](/mem/intune/fundamentals/supported-devices-browsers).

Aşağıdaki cihazları güvenlik altına almak ve yönetmek için Temel Mobil Kullanım ve Güvenlik'i kullanabilirsiniz.

- iOS
- Android (Samsung Knox dahil)<sup>1</sup>
- Windows <sup>2, 3</sup>

<sup>1</sup> Haziran 2020'den sonra, 9'dan sonraki Android sürümleri Samsung Knox cihazları dışında parola ayarlarını yönetemedi.

<sup>2</sup> RT cihazları için Windows 8.1 denetimi diğer cihazlarla Exchange ActiveSync.

<sup>3</sup> Erişim denetimi Windows 10, aboneliği içeren bir Azure AD Premium ve cihazın e-posta hizmetine katılmış Azure Active Directory.

> [!NOTE]
> Özellikler önceden önceden işletim sistemi sürümleriyle kaydolan cihazlar çalışmaya devam eder, ancak bu özellikler önceden uyarılmadan değişebilir.

Kuruluşta kişiler Temel Mobil Kullanım ve Güvenlik tarafından desteklenen mobil cihazlar kullanıyorsa, bu cihazlarda Exchange ActiveSync uygulamasının Microsoft 365 e-posta erişimine engel olarak, kuruluş verilerinizin daha güvenli hale gelen şekilde erişmelerini engelleyebilirsiniz. Güvenliği engelleme adımları için Exchange ActiveSync Temel Mobil [Kullanım ve Güvenlik'te cihaz erişimi ayarlarını yönetme.](manage-device-access-settings.md)

## <a name="access-control-for-microsoft-365-email-and-documents"></a>E-postayı ve Microsoft 365 için erişim denetimi

Aşağıdaki tabloda yer alan farklı mobil cihaz türleri için desteklenen uygulamalar, kullanıcılardan, kullanıcının cihazı için geçerli olan ve daha önce cihazı kaydetmemiş yeni bir mobil cihaz yönetim ilkesi olan Basic Mobility ve Security'e kaydolmalarını istenir. Bir kullanıcının cihazı bir ilkeye uymazsa, sizin ilkeyi nasıl ayarlaymanıza bağlı olarak, kullanıcının bu uygulamalarda Microsoft 365 kaynaklarına erişimi engellenmiş olabilir veya bu kullanıcının erişimi olabilir ancak Microsoft 365 bir ilke ihlalsini raporlar.

|**Ürün**|**iOS**|**Android**|
|:-----|:-----|:-----|
|**Exchange** Exchange ActiveSync Sürüm 14.1 veya sonraki bir sürümü kullanan yerleşik e-posta ve TouchDown Exchange ActiveSync üçüncü taraf uygulamaları içerir. |Posta |E-posta |
| Office ve  **OneDrive İş** |Outlook </br>OneDrive </br>Word </br>Excel </br>PowerPoint|**Telefonlarda ve tabletlerde**:<br/>Outlook <br/> OneDrive <br/> Word <br/> Excel <br/> PowerPoint <br/> **Yalnızca telefonlarda:** <br/> Office Mobile |

> [!NOTE]
>
> - iOS 10.0 ve sonraki sürümleri için destek, iPhone ve iPad içerir.
> - BlackBerry işletim sistemi cihazlarının yönetimi Temel Güvenlik ve Mobil Kullanım tarafından desteklenmmektedir. BlackBerry OS cihazlarını yönetmek için BlackBerry Business Cloud Services'i (BBCS) BlackBerry'den kullanın. Android OS çalıştıran Blackberry cihazlar standart Android cihazları olarak de desteklemektedir
> - Kullanıcılardan kaydolmaları istenmeyecek ve mobil tarayıcıyı kullanarak Microsoft 365 SharePoint sitelerine, Office Online'daki belgelere veya Outlook Web App'te e-postaya erişimleri için mobil tarayıcıyı kullanmaları istenir.

Aşağıdaki diyagramda, yeni cihazı olan bir kullanıcı Temel Mobil Kullanım ve Güvenlik ile erişim denetimlerini destekleyen bir uygulamada oturum açınca neler olduğu görünür. Kullanıcının cihazı kaydolana kadar Microsoft 365 kaynakları erişimi engellenir.

:::image type="content" source="../../media/basic-mobility-security/bms-1-access-control.png" alt-text="Temel Hareketlilik ve Güvenlik erişim denetimi.":::

> [!NOTE]
> Microsoft 365 İş Standart için Temel Mobil Kullanım ve Güvenlik ile Exchange ActiveSync ilkeler ve erişim kuralları, Exchange yönetim merkezinde oluşturulmuş mobil cihaz posta kutusu ilkelerini ve cihaz erişim kurallarını geçersiz kılar. Cihaz Microsoft 365 İş Standart için Temel Mobil Kullanım ve Güvenlik'e Exchange ActiveSync, cihaza uygulanan tüm mobil cihaz posta kutusu ilkesi veya cihaz erişim kuralları yoksayılır. Bu konuda daha fazla Exchange ActiveSync için bkz [. Exchange ActiveSync'da Exchange Online](/exchange/clients-and-mobile-in-exchange-online/exchange-activesync/exchange-activesync).

## <a name="policy-settings-for-mobile-devices"></a>Mobil cihazlar için ilke ayarları

Belirli ayarlar açıkken erişimi engellemek için bir ilke oluşturmanız, kullanıcıların [Microsoft 365](capabilities.md) e-posta ve belgeleri için Access denetiminde listelenen desteklenen bir uygulama kullanırken Microsoft 365 kaynaklarına erişimi engellenir.

Kullanıcıların kaynak e-postalara erişimini engel Microsoft 365 ayarlar şu bölümlerde yerlanmıştır:

- Güvenlik

- Şifreleme

- Bir gün önce bir gün içinde iş için

- Yönetilen e-posta profili

Örneğin, aşağıdaki diyagramda, kayıtlı cihazı olan bir kullanıcı, cihazına uygulanan mobil cihaz yönetim ilkesinde yer alan bir güvenlik ayarıyla uyumlu değilse neler olduğu görünür. Kullanıcı, Temel Mobil Kullanım ve Güvenlik ile erişim denetimlerini destekleyen bir uygulamada oturum a giriş bilgileri sağlar. Cihaz güvenlik ayarına uygun Microsoft 365 uygulama kaynaklarına erişmeleri engellenir.

:::image type="content" source="../../media/basic-mobility-security/bms-2-device-not-compliant.png" alt-text="Temel Mobil Kullanım ve Güvenlik uyumluluk iletisi.":::

Aşağıdaki bölümlerde, kullanıcı ve kuruluş kaynaklarınıza bağlanan mobil cihazların güvenliğini sağlamada ve yönetmede yardımcı olmak için Microsoft 365 ayarları listelemektedir.

## <a name="security-settings"></a>Güvenlik ayarları

|**Ayar adı**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Parola gerektirme|Evet|Evet|Evet|
|Basit parolayı engelleme|Evet|Hayır|Hayır|
|Alfasayısal parola gerektirme|Evet|Hayır|Hayır|
|Minimum parola uzunluğu |Evet|Evet|Evet|
|Cihaz silinmeden önce oturum açma hatası sayısı |Evet|Evet|Evet|
|Cihaz kilitlenmeden önce dakikalar içinde etkileşimde olunma |Evet|Evet|Evet|
|Parola süre sonu (gün) |Evet|Evet|Evet|
|Parola geçmişini anımsama ve yeniden kullanımı engelleme |Evet|Evet|Evet|

## <a name="encryption-settings"></a>Şifreleme ayarları

|**Ayar adı**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Cihazlarda veri şifrelemesi <sup>gerektirme1</sup> |Hayır|Evet|Evet|

<sup>1</sup> Samsung Knox ile depolama kartlarında şifreleme de gerekli olabilir.

## <a name="jail-broken-setting"></a>Güvenlik 2013 ayarları bozuk

|**Ayar adı**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Cihaz bozuk veya kök olarak girilenem |Evet|Evet|Evet|

## <a name="managed-email-profile-option"></a>Yönetilen e-posta profili seçeneği

Aşağıdaki seçenek, kullanıcıların el ile oluşturulan bir e-Microsoft 365 profili kullanıyorsa e-postalarına erişmelerini engelleyebilir. iOS cihazlarında kullanıcılar e-postalarına erişmek için önce el ile oluşturulan e-posta profillerini silmeleri gerekir. Profili sildikten sonra cihazda otomatik olarak yeni bir profil oluşturulur. Son kullanıcıların uyumlu hale nasıl geldiyle ilgili yönergeler için bkz [. Var olan bir e-posta hesabı bulundu](/intune-user-help/existing-company-email-account-found).

|**Ayar adı**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|E-posta profili yönetiliyor |Evet|Hayır|Hayır|

## <a name="cloud-settings"></a>Bulut ayarları

|**Ayar adı**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Şifreli yedekleme gerektir |Evet|Hayır|Hayır|
|Bulut yedeklemeyi engelle |Evet|Hayır|Hayır|
|Belge eşitlemesini engelleme |Evet|Hayır|Hayır|
|Fotoğraf eşitlemeyi engelleme  |Evet|Hayır|Hayır|
|Google yedeklemesine izin ver  |Yok|Hayır|Evet|
|Google hesabı otomatik eşitlemesine izin ver  |Yok|Hayır|Evet|

## <a name="system-settings"></a>Sistem ayarları

|**Ayar adı**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Ekran yakalamayı engelle |Evet|Hayır|Evet|
|Cihazdan tanılama verileri göndermeyi engelleme |Evet|Hayır|Evet|

## <a name="application-settings"></a>Uygulama ayarları

|**Ayar adı**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Cihazda görüntülü konferansları engelleme |Evet|Hayır|Hayır|
|Uygulama deposuna erişimi engelleme |Evet|Hayır|Evet|
|Uygulama mağazasına erişirken parola gerektir |Hayır|Evet|Evet|

## <a name="device-capabilities-settings"></a>Cihaz özellikleri ayarları

|**Ayar adı**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Çıkarılabilir depolama alanıyla bağlantıyı engelleme |Evet|Evet|Hayır|
|Bağlantı Bluetooth engelleme |Evet|Evet|Hayır|

## <a name="additional-settings"></a>Ek ayarlar

Güvenlik ayarları ve Uyumluluk Merkezi PowerShell cmdlet'lerini & ek ilke ayarlarını değiştirebilirsiniz. Daha fazla bilgi için bkz [. Güvenlik & Uyumluluk Merkezi PowerShell](/powershell/exchange/scc-powershell).

|**Ayar adı**|**iOS** |**Android**|
|:-----|:-----|:-----|
|CameraEnabled|Evet|Evet|
|RegionRatings|Evet|Hayır|
|MoviesRatings|Evet|Hayır|
|TVShowsRating |Evet|Hayır|
|AppsRatings |Evet|Hayır|
|AllowVoiceDialing |Evet|Hayır|
|AllowVoiceAssistant |Evet|Hayır|
|AllowAssistantWhileLocked  |Evet|Hayır|
|AllowPassbookWhileLocked |Evet|Hayır|
|MaxPasswordGracePeriod |Evet|Hayır|
|PasswordQuality |Hayır|Evet|
|SystemSecurityTLS  |Evet|Hayır|
|WLANEnabled  |Hayır|Hayır|

## <a name="settings-supported-by-windows"></a>Ayarlar tarafından desteklenen Windows

Farklı cihazları Windows 10 cihaz olarak kaydederek yönetebilirsiniz. Geçerli bir ilke dağıtıldıktan sonra, Windows 10 cihazı olan kullanıcıların Microsoft 365 e-postalarına erişmek için yerleşik e-posta uygulamasını ilk kez kullanan Temel Mobil Kullanım ve Güvenlik'e kaydolmaları gerekir (Azure AD premium aboneliği gerektirir).

Mobil cihaz olarak Windows 10 cihazlar için aşağıdaki ayarlar desteklemektedir. Bu ayar kullanıcıların kaynak kaynakları erişimi Microsoft 365 engellemez.

### <a name="security-settings"></a>Güvenlik ayarları

- Alfasayısal parola gerektirme

- Minimum parola uzunluğu

- Cihaz silinmeden önce oturum açma hatası sayısı

- Cihaz kilitlenmeden önce dakikalar içinde etkileşimde olunma

- Parola süre sonu (gün)

- Parola geçmişini anımsama ve yeniden kullanımı engelleme

> [!NOTE]
> Aşağıdaki ayarlar parolaları yeniden düzenlemede yalnızca yerel Windows denetimine sahip olur. Windows etki alanına veya hesaba katılma aracılığıyla sağlanan Azure Active Directory hesapları bu ayarlardan etkilenmez.

### <a name="system-settings"></a>Sistem ayarları

Cihazdan tanılama verileri gönderilmesini engelin.

### <a name="additional-settings"></a>Ek ayarlar

PowerShell cmdlet'lerini kullanarak bu ek ilke ayarlarını değiştirebilirsiniz:

- AllowConvenienceLogon

- UserAccountControlStatus

- FirewallStatus

- AutoUpdateStatus

- AntiVirusStatus

- AntiVirusSignatureStatus

- SmartScreenEnabled

- WorkFoldersSyncUrl

## <a name="remotely-wipe-a-mobile-device"></a>Mobil cihazı uzaktan temizleme

Bir cihaz kaybolur veya çalınırsa, hassas kuruluş verilerini kaldırabilir ve Güvenlik ve Uyumluluk Merkezi'nde Veri kaybı önlemeDevice yönetimi'Microsoft 365 temizleme yaparak & kaynaklarınıza erişimi >  >  yardımcı **olabilir**. Bir cihazdan tüm bilgileri silip fabrika ayarlarına geri yüklemek için seçmeli temizleme işlemi, yalnızca kuruluş verilerini veya tam temizleme özelliğini kaldırabilirsiniz.

Daha fazla bilgi için bkz [. Temel Mobil Kullanım ve Güvenlik'te mobil cihazwipe](wipe-mobile-device.md).

## <a name="related-content"></a>İlgili içerik

[Kişiler için Temel Hareketlilik ve Güvenlik'e Microsoft 365](overview.md) (makale)\
[Temel Hareketlilik ve Güvenlik makalesinde cihaz güvenliği](create-device-security-policies.md) ilkeleri oluşturma (makale)
