---
title: Bir OneDrive konumunu farklı bir coğrafi konuma taşıma
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: Site taşımanın nasıl zamanlamayı OneDrive ve beklentilerin kullanıcılara iletki iletişim kurması da dahil olmak üzere, site sitesini farklı bir coğrafi konuma taşıma hakkında bilgi bulabilirsiniz.
ms.openlocfilehash: f0a9e319d20c7b56701d776e85a0618ed30e5f78
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569611"
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>Bir OneDrive konumunu farklı bir coğrafi konuma taşıma

Coğrafi OneDrive ile, kullanıcının bilgilerini farklı OneDrive konuma taşıabilirsiniz. OneDrive coğrafi taşıma işlemi SharePoint Online yöneticisi veya Microsoft 365 yöneticisi tarafından gerçekleştirilir. Coğrafi olarak OneDrive başlamadan önce, hesabı taşınan kullanıcıya OneDrive ve taşıma süresi boyunca tüm dosyaları kapatmalarını önerin. (Kullanıcının, taşıma sırasında Office istemcisini kullanarak açık bir belgesi varsa, taşıma tamamlandığında belgenin yeni konuma kaydedilmiş olması gerekir.) Taşıma,  İstenen sonraki bir zaman için zamanlanmış olabilir.

İçerik OneDrive depolamak için Azure Blob Depolama bilgileri kullanır. Kullanıcının Depolama blob'unla ilişkilendirilmiş OneDrive, kullanıcının kullanımına açık olan hedef OneDrive sonra kaynak konumdan hedef coğrafi konuma OneDrive taşınır. Kullanıcının posta hedefine erişim OneDrive, kullanılabilir olduğu anda OneDrive yüklenir.

Coğrafi OneDrive penceresinde (yaklaşık 2-6 saat) kullanıcının OneDrive salt okunur olarak ayarlanır. Kullanıcı, dosyalarına SharePoint Online'daki OneDrive eşitleme uygulaması veya OneDrive site üzerinden SharePoint. Coğrafi OneDrive tamamlandıktan sonra kullanıcı, OneDrive uygulama başlatıcıda OneDrive'a gezindikten sonra hedef coğrafi konumdaki Microsoft 365 bağlantısında olur. Eşitleme uygulaması yeni konumdan eşitlemeye otomatik olarak başlar.

Bu makaledeki yordamlar için [PowerShell Microsoft Office SharePoint Online gerekir](https://www.microsoft.com/download/details.aspx?id=35588).

## <a name="communicating-to-your-users"></a>Kullanıcılarınıza iletişim kurma

Site OneDrive coğrafi konumlar arasında hareket ettirilen sitelerde, kullanıcılarınızı neler beklemeleri gerekenleri haberimiz önemlidir. Bu, kullanıcının kafa karışıklığını ve yardım masasına yapılan aramaları azaltmaya yardımcı olabilir. Taşımadan önce kullanıcılarınıza e-posta gönderin ve aşağıdaki bilgileri haber verme:

- Taşımanın ne zaman başlaması ve ne kadar süreyle başlaması beklendiği
- Bu konumun OneDrive coğrafi konum ve yeni konuma erişmek için URL
- Taşıma sırasında düzenleme yapmalarını değil dosyalarını kapatmaları gerekir.
- Taşıma sonucunda dosya izinleri ve paylaşım değişmez.
- Çok coğrafi bir [ortamda kullanıcı deneyiminden neler beklemeleri gerekir?](multi-geo-user-experience.md)

Taşıma başarıyla tamamlandığında kullanıcılarınıza bir e-posta göndermeyi, bu kullanıcılara proje içinde çalışmaya devam edeceklerini haber OneDrive.

## <a name="scheduling-onedrive-site-moves"></a>Site OneDrive zamanlaması taşınır

Sitenin önceden OneDrive zamanlamayı zaman edebilirsiniz (bu makalenin devamsında açıklanmıştır). İş akışlarınızı ve iletişim stratejilerinizi doğrulamak için az sayıda kullanıcıyla başlamanızı öneririz. İşleme rahat bir şekilde başladıktan sonra, aşağıdaki gibi hareket zamanlamanız da mümkün olur:

- Bir defada en çok 4.000 hareket zamanabilirsiniz.
- Hareketler baş ettiğinde, sırada ve belirli bir zamanda en çok 4.000 bekleyen hareket olacak şekilde daha fazla zamanlamayı zamanabilirsiniz.
- Taşınacak en büyük OneDrive 1 terabayt (1 TB) olur.

## <a name="moving-a-onedrive-site"></a>Site OneDrive taşıma

Coğrafi olarak OneDrive için, önce kiracı yöneticisinin kullanıcının Tercih Edilen Veri Konumu'nun (PDL) uygun coğrafi konumu olarak ayarlaması gerekir. PDL ayarlanarak, PDF'nin coğrafi olarak taşınmaya başlamadan önce PDL güncelleştirmesini coğrafi konumlar arasında eşitlemesi için OneDrive bekleyin.

Geo move cmdlet'lerini kullanırken, aşağıdaki söz dizimlerini kullanarak kullanıcının geçerli OneDrive SPO Hizmeti'ne bağlanabilirsiniz:

```powershell
Connect-SPOService -url https://<tenantName>-admin.sharepoint.com
```

Örneğin: 'OneDrive' kullanıcısını taşımak için, kullanıcının hesabı EURO coğrafi Matt@contosoenergy.onmicrosoft.com olduğu için EURO SharePoint OneDrive Yönetim merkezine bağlanin:

```powershell
Connect-SPOService -url https://contosoenergyeur-admin.sharepoint.com
```

![Connect-sposervice cmdlet'ini gösteren PowerShell penceresinin ekran görüntüsü.](../media/move-onedrive-between-geo-locations-image1.png)

## <a name="validating-the-environment"></a>Ortamı doğrulama

Coğrafi olarak taşımaya OneDrive, ortamı doğrulamanızı öneririz.

Tüm coğrafi konumların uyumlu olduğundan emin olmak için şunları çalıştırın:

```powershell
Get-SPOGeoMoveCrossCompatibilityStatus
```

Coğrafi konumlarınızı ve içeriğin taşınıp taşınmayacaklarını liste olarak "Uyumlu" olarak ifade ettiysiniz. Komut "Uyumsuz" döndürürse, lütfen daha sonraki bir tarihte durumu doğrulamayı yeniden deneyin.

Örneğin OneDrive site içeren bir site varsa, bu site taşınamaz. OneDrive taşınanın Start-SPOUserAndContentMove doğrulamak için OneDrive -ValidationOnly parametresiyle kullanabilirsiniz:

```powershell
Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly
```

Taşımayı önleyen yasal bir OneDrive bir engelleme veya alt site varsa, Çalışma Alanı taşınmaya hazırsa Başarılı'ya veya Başarısız'a döner. Dosyanın taşınmaya hazır OneDrive doğrulandıktan sonra, taşımaya başlayabilirsiniz.

## <a name="start-a-onedrive-geo-move"></a>Coğrafi olarak OneDrive başlatma

Taşımayı başlatmak için şu çalıştırın:

```powershell
Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>
```

Şu parametreleri kullanarak:

- _UserPrincipalName_ – Kimlik bilgileri taşınan kullanıcının OneDrive UPN'i.
- _DestinationDataLocation_ – Geo-Location olması OneDrive yere taşınır. Bu, kullanıcının tercih ettiği veri konumuyla aynı olması gerekir.

Örneğin, euro olan OneDrive euro matt@contosoenergy.onmicrosoft.com AUS'a taşımak için şu çalıştırın:

```powershell
Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS
```

![PowerShell penceresinin cmdlet'i Start-SPOUserAndContentMove ekran görüntüsü.](../media/move-onedrive-between-geo-locations-image2.png)

Coğrafi taşımayı daha sonraki bir zaman için zaman yapmak için, aşağıdaki parametrelerden birini kullanın:

- _PreferredMoveBeginDate_ – Taşıma, büyük olasılıkla belirtilen zamanda başlayacaktır. Saat, Eşgüdümli Evrensel Saat (UTC) içinde belirtilmelidir.
- _PreferredMoveEndDate_ – Taşıma büyük olasılıkla belirtilen zamanda, en iyi çabayla tamamlanır. Saat, Eşgüdümli Evrensel Saat (UTC) içinde belirtilmelidir.

## <a name="cancel-a-onedrive-geo-move"></a>Coğrafi olarak OneDrive iptal etme

Şu cmdlet'i kullanarak, OneDrive veya tamamlanmadı ise, kullanıcının kullanıcı postalarının coğrafi olarak taşınmalarını durdursanız:

```powershell
Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>
```

Burada _UserPrincipalName_, adı taşımak istediğiniz kullanıcının OneDrive UPN'dir.

## <a name="determining-current-status"></a>Geçerli durumu belirleme

OneDrive Get-SPOUserAndContentMoveState cmdlet'ini kullanarak, bağlı olduğunu coğrafi olarak hareket ettiren veya dışarı doğru hareket ettiren bir Get-SPOUserAndContentMoveState kontrol edin.

Taşıma durumları aşağıdaki tabloda açıklanmıştır.

|Durum|Açıklama|
|---|---|
|NotStarted|Taşıma başlamadı|
|Çıkış (*n*/4)|Aşağıdaki eyaletlerden biri için taşıma devam etmektedir: <ul><li>Doğrulama (1/4)</li><li>Yedekleme (2/4)</li><li>Geri Yükleme (3/4)</li><li>Temizleme (4/4)</li></ul>|
|Başarılı|Taşıma başarıyla tamamlandı.|
|Başarısız|Taşıma başarısız oldu.|

Belirli bir kullanıcının taşıma durumunu bulmak için *UserPrincipalName parametresini* kullanın:

```powershell
Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>
```

Bağlı olduğunu coğrafi konuma taşıma veya taşımanın tüm durumlarını bulmak için *MoveState* parametresini şu değerlerden birini kullanarak kullanın: NotStarted, InProgress, Success, Failed, All.

```powershell
Get-SPOUserAndContentMoveState -MoveState <value>
```

Ayrıca, taşıma *durumunun ayrıntılı açıklamaları için Verbose* parametresini de ekleyebilirsiniz.

## <a name="user-experience"></a>Kullanıcı Deneyimi

Farklı OneDrive konumlarına taşınan kullanıcıların, OneDrive aksaklıkları çok az fark olması gerekir. Taşıma sırasında kısa bir salt okunur durumunun dışında, taşıma tamamlandıktan sonra da var olan bağlantılar ve izinler beklendiği gibi çalışmaya devam eder.

### <a name="users-onedrive"></a>Kullanıcının OneDrive

Taşıma devam ederken kullanıcının OneDrive salt okunur olarak ayarlanır. Taşıma tamamlandıktan sonra OneDrive, kullanıcı Microsoft 365 uygulama başlatıcısında veya web tarayıcısında OneDrive coğrafi konumdaki Microsoft 365 kullanıcısına yönlendirildi.

### <a name="permissions-on-onedrive-content"></a>İçerik OneDrive izinleri

İçerik üzerinde izin OneDrive kullanıcılar, taşıma sırasında ve tamamlandıktan sonra içeriğe erişmeye devam eder.

### <a name="onedrive-sync-app"></a>OneDrive eşitleme uygulaması

Mobil OneDrive eşitleme, coğrafi taşıma tamamlandıktan sonra eşitlemeyi otomatik olarak algılar OneDrive yeni OneDrive konuma sorunsuz bir şekilde aktaracaktır. Kullanıcının yeniden oturum açması veya başka bir işlem yapma ihtiyacı olmaz.  (Eşitleme uygulamasının 17.3.6943.0625 veya daha sonraki bir sürümü gereklidir.)

Kullanıcı coğrafi olarak taşıma devam ederken OneDrive dosyayı güncellerse, eşitleme uygulaması taşıma devam ederken dosya karşıya yüklemelerinin beklemede olduğunu bildirecek.

### <a name="sharing-links"></a>Paylaşım bağlantıları

Coğrafi OneDrive tamamlandığında, taşınan dosyaların var olan paylaşılan bağlantıları otomatik olarak yeni coğrafi konuma yeniden yönlendirilir.

### <a name="onenote-experience"></a>OneNote Deneyimi

OneNote win32 istemcisi ve UWP (Evrensel) Uygulaması coğrafi taşıma tamamlandıktan sonra not defterlerini otomatik olarak yeni OneDrive konuma otomatik olarak OneDrive eşitler. Kullanıcının yeniden oturum açması veya başka bir işlem yapma ihtiyacı olmaz. Kullanıcının tek görünür göstergesi, coğrafi olarak taşıma devam eden bir OneDrive not defteri eşitlemenin başarısız olmasıdır. Bu deneyim, aşağıdaki istemci OneNote kullanılabilir:

- OneNote win32 – Sürüm 16.0.8326.2096 (ve sonrası)
- OneNote UWP – Sürüm 16.0.8431.1006 (ve sonrası)
- OneNote Uygulaması – Sürüm 16.0.8431.1011 (ve sonrası)

### <a name="teams-app"></a>Teams uygulaması

Coğrafi OneDrive tamamlandığında, kullanıcılar mobil uygulamada OneDrive dosyalarına Teams sahip olur. Buna ek olarak, Teams coğrafi taşıma öncesinde sohbet OneDrive dosyaları taşıma işlemi tamamlandıktan sonra da çalışmaya devam edecektir.

### <a name="onedrive-mobile-app-ios"></a>OneDrive Uygulaması (iOS)

Coğrafi OneDrive tamamlandıktan sonra, kullanıcının yeni mobil konuma eşitlemek için iOS Mobil Uygulamasında oturum açması ve yeniden OneDrive gerekir.

### <a name="existing-followed-groups-and-sites"></a>Var olan takip edilen gruplar ve siteler

Takip edilen siteler ve gruplar coğrafi konumlarından bağımsız OneDrive kullanıcının posta bilgisinde gösterilemez. Başka bir coğrafi konumda barındırılan siteler ve gruplar ayrı bir sekmede açılır.

### <a name="delve-geo-url-updates"></a>Delve URL güncelleştirmelerini güncelleştirme

Kullanıcılar, PDL'lerine Delve coğrafi olarak GÖNDERILEN ONEDRIVE yeni coğrafi bölgeye taşındıktan sonra.
