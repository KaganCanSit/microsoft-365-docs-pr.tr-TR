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
description: Temel Mobilite ve Güvenlik, e-posta ve belgeler Microsoft 365 kuruluşa erişimi denetleen ilkelerle mobil cihazların güvenliğini sağlamanıza ve yönetmenize yardımcı olur.
ms.openlocfilehash: 55c2a197959e55e2a74f8691b7181f8ee91b0ea9
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66010178"
---
# <a name="capabilities-of-basic-mobility-and-security"></a>Temel Hareketlilik ve Güvenlik Özellikleri

Temel Mobilite ve Güvenlik, kuruluşunuzdaki lisanslı Microsoft 365 kullanıcıları tarafından kullanılan iPhone, iPad, Android ve Windows Telefonlar gibi mobil cihazların güvenliğini sağlamanıza ve yönetmenize yardımcı olabilir. Desteklenen mobil cihazlar ve uygulamalar için kuruluşunuzun Microsoft 365 e-postasına ve belgelerine erişimi denetlemeye yardımcı olabilecek ayarlarla mobil cihaz yönetimi ilkeleri oluşturabilirsiniz. Bir cihaz kaybolur veya çalınırsa, hassas kuruluş bilgilerini kaldırmak için cihazı uzaktan silebilirsiniz.

## <a name="supported-operating-systems"></a>Desteklenen işletim sistemleri

Basic Mobility ve Security tarafından sunulan cihazlar için desteklenen en düşük işletim sistemleri için Microsoft Intune işletim sistemleri kılavuzunu izleyin. Daha fazla bilgi için bkz. [desteklenen Intune işletim sistemleri](/mem/intune/fundamentals/supported-devices-browsers).

Aşağıdaki cihazların güvenliğini sağlamak ve yönetmek için Basic Mobility ve Security'yi kullanabilirsiniz.

- iOS
- Android (Samsung Knox dahil)<sup>1</sup>
- Windows <sup>2, 3</sup>

<sup>1</sup> Haziran 2020'den sonra, 9'dan sonraki Android sürümler Samsung Knox cihazları dışında parola ayarlarını yönetemez.

<sup>2</sup> Windows 8.1 RT cihazları için erişim denetimi Exchange ActiveSync ile sınırlıdır.

<sup>3</sup> Windows 10 erişim denetimi, Azure AD Premium içeren bir abonelik gerektirir ve cihazın Azure Active Directory katılması gerekir.

> [!NOTE]
> Daha önceki işletim sistemi sürümlerine önceden kaydedilmiş cihazlar çalışmaya devam eder ancak özellikler bildirimde bulunmadan değişebilir.

Kuruluşunuzdaki kişiler Basic Mobility ve Security tarafından desteklenmeyen mobil cihazlar kullanıyorsa, kuruluşunuzun verilerini daha güvenli hale getirmek için bu cihazlar için Microsoft 365 e-postaya Exchange ActiveSync uygulama erişimini engellemek isteyebilirsiniz. Exchange ActiveSync engelleme adımları için bkz. [Temel Mobilite ve Güvenlik'te cihaz erişim ayarlarını yönetme](manage-device-access-settings.md).

## <a name="access-control-for-microsoft-365-email-and-documents"></a>Microsoft 365 e-posta ve belgeler için erişim denetimi

Aşağıdaki tabloda yer alan farklı mobil cihaz türleri için desteklenen uygulamalar, kullanıcıların bir kullanıcının cihazı için geçerli olan yeni bir mobil cihaz yönetimi ilkesi olduğu ve daha önce cihazı kaydetmediği Basic Mobility and Security'ye kaydolmalarını ister. Kullanıcının cihazı ilkeyi nasıl ayarladığınıza bağlı olarak bir ilkeyle uyumlu değilse, kullanıcının bu uygulamalardaki Microsoft 365 kaynaklara erişmesi engellenebilir veya erişimi olabilir ancak Microsoft 365 ilke ihlali bildiriyor olabilir.

|Ürün|iOS|Android|
|---|---|---|
|**Exchange** Exchange ActiveSync, Exchange ActiveSync Sürüm 14.1 veya üzerini kullanan yerleşik e-posta ve TouchDown gibi üçüncü taraf uygulamaları içerir.|Posta|E-posta|
|**Office** ve **OneDrive İş**|Outlook </br>OneDrive </br>Word </br>Excel </br>PowerPoint|**Telefonlarda ve tabletlerde**:<br/>Outlook <br/> OneDrive <br/> Word <br/> Excel <br/> PowerPoint <br/> **Yalnızca telefonlarda:** <br/> Office Mobile|

> [!NOTE]
>
> - iOS 10.0 ve üzeri sürümler için destek, iPhone ve iPad cihazları içerir.
> - BlackBerry işletim sistemi cihazlarının yönetimi Basic Security ve Mobility tarafından desteklenmez. BlackBerry işletim sistemi cihazlarını yönetmek için BlackBerry'den BlackBerry Business Cloud Services (BBCS) kullanın. Android işletim sistemi çalıştıran Blackberry cihazları standart Android cihazlar olarak desteklenir
> - Kullanıcılardan kaydolmaları istenmez ve mobil tarayıcıyı kullanarak Microsoft 365 SharePoint sitelere, Office Online'daki belgelere veya Outlook Web App'daki e-postalara erişim sağlamaları durumunda ilke ihlali nedeniyle engellenmez veya bildirilmez.

Aşağıdaki diyagramda, yeni cihazı olan bir kullanıcı Temel Mobilite ve Güvenlik ile erişim denetimini destekleyen bir uygulamada oturum açtığında ne olacağı gösterilmektedir. Kullanıcının cihazını kaydedene kadar uygulamadaki Microsoft 365 kaynaklarına erişmesi engellenir.

:::image type="content" source="../../media/basic-mobility-security/bms-1-access-control.png" alt-text="Temel Mobilite ve Güvenlik erişim denetimi.":::

> [!NOTE]
> Microsoft 365 İş Standart için Basic Mobility ve Security'de oluşturulan ilkeler ve erişim kuralları, Exchange yönetim merkezinde oluşturulan Exchange ActiveSync mobil cihaz posta kutusu ilkelerini ve cihaz erişim kurallarını geçersiz kılar. Bir cihaz Microsoft 365 İş Standart için Basic Mobility ve Security'ye kaydedildikten sonra, cihaza uygulanan tüm Exchange ActiveSync mobil cihaz posta kutusu ilkesi veya cihaz erişim kuralı yoksayılır. Exchange ActiveSync hakkında daha fazla bilgi edinmek için bkz. [Exchange Online'da Exchange ActiveSync](/exchange/clients-and-mobile-in-exchange-online/exchange-activesync/exchange-activesync).

## <a name="policy-settings-for-mobile-devices"></a>Mobil cihazlar için ilke ayarları

Belirli ayarlar açıkken erişimi engellemek için bir ilke oluşturursanız, kullanıcıların Microsoft 365 [e-posta ve belgeler için Erişim denetiminde](capabilities.md) listelenen desteklenen bir uygulamayı kullanırken Microsoft 365 kaynaklarına erişmesi engellenir.

Kullanıcıların Microsoft 365 kaynaklarına erişmesini engelleyebilecek ayarlar şu bölümlerdedir:

- Güvenlik

- Şifreleme

- Jail broken

- Yönetilen e-posta profili

Örneğin, aşağıdaki diyagramda kayıtlı cihazı olan bir kullanıcı, cihazı için geçerli olan mobil cihaz yönetim ilkesindeki bir güvenlik ayarıyla uyumlu olmadığında ne olacağı gösterilmektedir. Kullanıcı, Basic Mobility ve Security ile erişim denetimini destekleyen bir uygulamada oturum açar. Cihazları güvenlik ayarına uygun hale gelene kadar uygulamadaki Microsoft 365 kaynaklarına erişmeleri engellenir.

:::image type="content" source="../../media/basic-mobility-security/bms-2-device-not-compliant.png" alt-text="Temel Mobilite ve Güvenlik uyumluluk iletisi.":::

Aşağıdaki bölümlerde, Microsoft 365 kuruluş kaynaklarınıza bağlanan mobil cihazların güvenliğini sağlamaya ve yönetmeye yardımcı olmak için kullanabileceğiniz ilke ayarları listelenmektedir.

## <a name="security-settings"></a>Güvenlik ayarları

|Ayar adı|iOS|Android|Samsung Knox|
|---|---|---|---|
|Parola iste|Evet|Evet|Evet|
|Basit parolayı önleme|Evet|Hayır|Hayır|
|Alfasayısal parola iste|Evet|Hayır|Hayır|
|Minimum parola uzunluğu|Evet|Evet|Evet|
|Cihaz silinmeden önce oturum açma hatası sayısı|Evet|Evet|Evet|
|Cihaz kilitlenmeden önce işlem yapılmadan geçen dakika sayısı|Evet|Evet|Evet|
|Parola süre sonu (gün)|Evet|Evet|Evet|
|Parola geçmişini anımsama ve yeniden kullanılmasını önleme|Evet|Evet|Evet|

## <a name="encryption-settings"></a>Şifreleme ayarları

|Ayar adı|iOS|Android|Samsung Knox|
|---|---|---|---|
|Cihazlarda veri şifrelemesi gerektir<sup>1</sup>|Hayır|Evet|Evet|

<sup>1</sup> Samsung Knox ile depolama kartlarında şifreleme de gerektirebilirsiniz.

## <a name="jail-broken-setting"></a>Jail broken ayarı

|Ayar adı|iOS|Android|Samsung Knox|
|---|---|---|---|
|Cihaz jailbreak yapılamaz veya kök erişim izni verilemez|Evet|Evet|Evet|

## <a name="managed-email-profile-option"></a>Yönetilen e-posta profili seçeneği

Aşağıdaki seçenek, el ile oluşturulmuş bir e-posta profili kullanan kullanıcıların Microsoft 365 e-postalarına erişmesini engelleyebilir. iOS cihazlardaki kullanıcıların e-postalarına erişebilmeleri için önce el ile oluşturulan e-posta profillerini silmeleri gerekir. Profil silindikten sonra cihazda otomatik olarak yeni bir profil oluşturulur. Son kullanıcıların nasıl uyumlu olabileceğine ilişkin yönergeler için bkz. [Mevcut bir e-posta hesabı bulundu](/intune-user-help/existing-company-email-account-found).

|Ayar adı|iOS|Android|Samsung Knox|
|---|---|---|---|
|E-posta profili yönetiliyor|Evet|Hayır|Hayır|

## <a name="cloud-settings"></a>Bulut ayarları

|Ayar adı|iOS|Android|Samsung Knox|
|---|---|---|---|
|Şifrelenmiş yedekleme gerektir|Evet|Hayır|Hayır|
|Bulut yedeklemesini engelleme|Evet|Hayır|Hayır|
|Belge eşitlemesini engelle|Evet|Hayır|Hayır|
|Fotoğraf eşitlemeyi engelle|Evet|Hayır|Hayır|
|Google yedeklemesine izin ver|Yok|Hayır|Evet|
|Google hesabı otomatik eşitlemesine izin ver|Yok|Hayır|Evet|

## <a name="system-settings"></a>Sistem ayarları

|Ayar adı|iOS|Android|Samsung Knox|
|---|---|---|---|
|Ekran yakalamayı engelle|Evet|Hayır|Evet|
|Cihazdan tanılama verilerinin gönderilmesini engelleme|Evet|Hayır|Evet|

## <a name="application-settings"></a>Uygulama ayarları

|Ayar adı|iOS|Android|Samsung Knox|
|---|---|---|---|
|Cihazda görüntülü konferansları engelleme|Evet|Hayır|Hayır|
|Uygulama deposuna erişimi engelleme|Evet|Hayır|Evet|
|Uygulama deposuna erişirken parola gerektir|Hayır|Evet|Evet|

## <a name="device-capabilities-settings"></a>Cihaz özellikleri ayarları

|Ayar adı|iOS|Android|Samsung Knox|
|---|---|---|---|
|Çıkarılabilir depolama birimiyle bağlantıyı engelleme|Evet|Evet|Hayır|
|Bluetooth bağlantısını engelle|Evet|Evet|Hayır|

## <a name="additional-settings"></a>Ek ayarlar

Güvenlik & Uyumluluğu PowerShell cmdlet'lerini kullanarak aşağıdaki ek ilke ayarlarını yapabilirsiniz. Daha fazla bilgi için bkz [. Güvenlik & Uyumluluk PowerShell](/powershell/exchange/scc-powershell).

|Ayar adı|iOS|Android|
|---|---|---|
|CameraEnabled|Evet|Evet|
|RegionRatings|Evet|Hayır|
|FilmlerAyrılamalar|Evet|Hayır|
|TVShowsRating|Evet|Hayır|
|UygulamalarAyrılamalar|Evet|Hayır|
|AllowVoiceDialing|Evet|Hayır|
|AllowVoiceAssistant|Evet|Hayır|
|AllowAssistantWhileLocked|Evet|Hayır|
|AllowPassbookWhileLocked|Evet|Hayır|
|MaxPasswordGracePeriod|Evet|Hayır|
|PasswordQuality|Hayır|Evet|
|SystemSecurityTLS|Evet|Hayır|
|WLANEnabled|Hayır|Hayır|

## <a name="settings-supported-by-windows"></a>Windows tarafından desteklenen Ayarlar

Windows 10 cihazları mobil cihaz olarak kaydederek yönetebilirsiniz. Geçerli bir ilke dağıtıldıktan sonra, Windows 10 cihazları olan kullanıcıların Microsoft 365 e-postalarına erişmek için yerleşik e-posta uygulamasını ilk kez kullandıklarında Basic Mobility ve Security'ye kaydolmaları gerekir (Azure AD premium abonelik gerektirir).

Mobil cihaz olarak kaydedilen Windows 10 cihazlar için aşağıdaki ayarlar desteklenir. Bu ayar kullanıcıların Microsoft 365 kaynaklarına erişmesini engellemez.

### <a name="security-settings"></a>Güvenlik ayarları

- Alfasayısal parola iste

- Minimum parola uzunluğu

- Cihaz silinmeden önce oturum açma hatası sayısı

- Cihaz kilitlenmeden önce işlem yapılmadan geçen dakika sayısı

- Parola süre sonu (gün)

- Parola geçmişini anımsama ve yeniden kullanılmasını önleme

> [!NOTE]
> Parolaları düzenleyen aşağıdaki ayarlar yalnızca yerel Windows hesaplarını denetler. Bir etki alanına veya Azure Active Directory katılma yoluyla sağlanan Windows hesapları bu ayarlardan etkilenmez.

### <a name="system-settings"></a>Sistem ayarları

Cihazdan tanılama verilerinin gönderilmesini engelleyin.

### <a name="additional-settings"></a>Ek ayarlar

PowerShell cmdlet'lerini kullanarak bu ek ilke ayarlarını yapabilirsiniz:

- AllowConvenienceLogon

- UserAccountControlStatus

- FirewallStatus

- AutoUpdateStatus

- AntiVirusStatus

- AntiVirusSignatureStatus

- SmartScreenEnabled

- WorkFoldersSyncUrl

## <a name="remotely-wipe-a-mobile-device"></a>Mobil cihazı uzaktan silme

Bir cihaz kaybolur veya çalınırsa, **Microsoft Purview uyumluluk portalı** > **Veri kaybı önleme** > **Cihaz yönetimi'nden** temizleme yaparak hassas kuruluş verilerini kaldırabilir ve Microsoft 365 kuruluş kaynaklarınıza erişimi engellemeye yardımcı olabilirsiniz. Bir cihazdan tüm bilgileri silip fabrika ayarlarına geri yüklemek için yalnızca kuruluş verilerini kaldırmak için seçmeli silme veya tam silme işlemi yapabilirsiniz.

Daha fazla bilgi için bkz [. Basic Mobility and Security'de mobil cihazı temizleme](wipe-mobile-device.md).

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 için Temel Mobilite ve Güvenliğe Genel Bakış](overview.md) (makale)\
[Temel Mobilite ve Güvenlik'te cihaz güvenlik ilkeleri oluşturma](create-device-security-policies.md) (makale)
