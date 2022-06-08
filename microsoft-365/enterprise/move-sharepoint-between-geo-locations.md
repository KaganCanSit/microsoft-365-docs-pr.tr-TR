---
title: SharePoint sitesini farklı bir coğrafi konuma taşıma
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: SharePoint sitesini çok coğrafi ortamınızda farklı bir coğrafi konuma taşımayı ve değişikliklerle ilgili beklentileri kullanıcılarınıza iletmeyi öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0b388b3fa869e6207c72f62aa2f50b832acab43a
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940832"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location"></a>SharePoint sitesini farklı bir coğrafi konuma taşıma

SharePoint sitesi coğrafi taşıma ile, SharePoint sitelerini çok coğrafi ortamınızdaki diğer coğrafi konumlara taşıyabilirsiniz.

Aşağıdaki site türleri coğrafi konumlar arasında taşınabilir:

- Microsoft Teams ile ilişkilendirilmiş siteler de dahil olmak üzere Microsoft 365 grup bağlantılı siteler
- Microsoft 365 grup ilişkilendirmesi olmayan modern siteler
- Klasik SharePoint siteleri
- İletişim siteleri

Bir siteyi coğrafi konumlar arasında taşımak için Genel Yönetici veya SharePoint Yöneticisi olmanız gerekir.

SharePoint sitesi coğrafi taşıma işlemi sırasında site içeriğine bağlı olarak yaklaşık 4-6 saatlik bir salt okunur pencere vardır.

## <a name="best-practices"></a>En iyi uygulamalar

- Yordam hakkında bilgi edinmek için test sitesinde SharePoint sitesi taşımayı deneyin.
- Sitenin taşımayı zamanlamadan veya gerçekleştirmeden önce taşınıp taşınamayacağını doğrulayın.
- Mümkün olduğunda coğrafi bölgeler arası siteler, kullanıcı etkisini azaltmak için iş saatleri dışında hareket eder.
- Siteler taşınmadan önce etkilenen kullanıcılarla iletişim kurun.

## <a name="communicating-to-your-users"></a>Kullanıcılarınıza iletişim kurma

SharePoint sitelerini coğrafi konumlar arasında taşırken, sitelerin kullanıcılarına (genellikle siteyi düzenleme yeteneği olan herkes) ne bekleyebileceğinizi bildirmek önemlidir. Bu, kullanıcı karışıklığını ve yardım masanıza yapılan aramaları azaltmaya yardımcı olabilir. Taşımadan önce sitelerinizin kullanıcılarına e-posta gönderin ve aşağıdaki bilgileri onlara bildirin:

- Taşıma işleminin ne zaman başlaması ve ne kadar sürmesi beklenir?
- Sitelerinin taşındığı coğrafi konum ve yeni konuma erişim URL'si
- Taşıma sırasında düzenleme yapmamaları ve dosyalarını kapatmaları gerekir.
- Taşıma nedeniyle dosya izinleri ve paylaşım değişmez.
- Çok coğrafi bir ortamda kullanıcı deneyiminden neler beklenmeli?

Taşıma işlemi başarıyla tamamlandığında sitelerinizin kullanıcılarına sitelerinde çalışmaya devam yapabileceklerini bildiren bir e-posta gönderdiğinizden emin olun.

## <a name="scheduling-sharepoint-site-moves"></a>SharePoint sitesi taşımalarını zamanlama

SharePoint sitesi taşımalarını önceden zamanlayabilirsiniz (bu makalenin ilerleyen bölümlerinde açıklanmaktadır). Taşımaları aşağıdaki gibi zamanlayabilirsiniz:

- Bir kerede en fazla 4.000 taşıma zamanlayabilirsiniz.
- Taşımalar başladığında, kuyrukta ve belirli bir zamanda bekleyen en fazla 4.000 taşıma ile daha fazla zamanlayabilirsiniz.
- Taşınabilecek SharePoint sitesinin boyutu üst sınırı 1 terabayttır (1 TB).

SharePoint sitesi coğrafi taşımasını daha sonra zamanlamak için, taşımayı başlattığınızda aşağıdaki parametrelerden birini ekleyin:

- `PreferredMoveBeginDate` – Taşıma büyük olasılıkla belirtilen zamanda başlayacaktır.
- `PreferredMoveEndDate` – Taşıma büyük olasılıkla en iyi çaba temelinde belirtilen zamana kadar tamamlanacaktır.

Saat, her iki parametre için de Eşgüdümlü Evrensel Saat (UTC) içinde belirtilmelidir.

## <a name="moving-the-site"></a>Siteyi taşıma

SharePoint sitesi coğrafi taşıma, sitenin bulunduğu coğrafi konumdaki SharePoint Yönetici URL'sine bağlanmanızı ve taşımayı gerçekleştirmenizi gerektirir.

Örneğin, site URL'si ise `https://contosohealthcare.sharepoint.com/sites/Turbines`adresinden SharePoint Yönetici URL'sine `https://contosohealthcare-admin.sharepoint.com`bağlanın:

```powershell
Connect-SPOService -Url https://contosohealthcare-admin.sharepoint.com
```

![Connect-SPOService komutunu gösteren SharePoint Online Yönetim Kabuğu penceresi.](../media/move-onedrive-between-geo-locations-image1.png)

### <a name="validating-the-environment"></a>Ortamı doğrulama

Herhangi bir site taşımasını zamanlamadan önce, sitenin taşına çalıştığından emin olmak için bir doğrulama gerçekleştirmenizi öneririz.

Sitelerin taşınmayı şu şekilde desteklemiyoruz:

- İş Bağlantı Hizmetleri
- InfoPath formları
- Uygulanan Bilgi Hakları Yönetimi (IRM) şablonları

Tüm coğrafi konumların uyumlu olduğundan emin olmak için komutunu çalıştırın `Get-SPOGeoMoveCrossCompatibilityStatus`. Bu, tüm coğrafi konumlarınızı ve ortamın hedef coğrafi konumla uyumlu olup olmadığını görüntüler.

Sitenizde yalnızca doğrulama denetimi gerçekleştirmek için parametresiyle `Start-SPOSiteContentMove` kullanarak sitenin `-ValidationOnly` taşınıp taşınamadığını doğrulayın. Örneğin:

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

Bu, site taşınmaya hazırsa *Başarılı* veya engellenen koşullardan herhangi biri varsa *Başarısız* döndürür.

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-microsoft-365-group"></a>İlişkili Microsoft 365 grubu olmayan bir site için SharePoint sitesi coğrafi taşımayı başlatma

Varsayılan olarak, sitenin ilk URL'si hedef coğrafi konumun URL'sine dönüşür. Örneğin:

`https://Contoso.sharepoint.com/sites/projectx` Hedef `https://ContosoEUR.sharepoint.com/sites/projectx`

Microsoft 365 grup ilişkilendirmesi olmayan siteler için parametresini kullanarak siteyi `-DestinationUrl` yeniden adlandırabilirsiniz. Örneğin:

<https://Contoso.sharepoint.com/sites/projectx> Hedef `https://ContosoEUR.sharepoint.com/sites/projecty`

Site taşıma işlemini başlatmak için şunu çalıştırın:

```powershell
Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>
```

![Start-SPOSiteContentMove cmdlet'ini gösteren PowerShell penceresinin ekran görüntüsü.](../media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-a-microsoft-365-group-connected-site"></a>Microsoft 365 grubuna bağlı bir site için SharePoint sitesi coğrafi taşımayı başlatma

Microsoft 365 grubuna bağlı bir siteyi taşımak için, Genel Yönetici veya SharePoint Yöneticisinin önce Microsoft 365 grubunun Tercih Edilen Veri Konumu (PDL) özniteliğini değiştirmesi gerekir.

Bir Microsoft 365 grubunun PDL'sini ayarlamak için:

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```

PDL'yi güncelleştirdikten sonra site taşıma işlemini başlatabilirsiniz:

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a>SharePoint sitesi coğrafi taşımayı iptal etme

Taşıma işlemi devam etmemesi veya cmdlet'ini kullanarak tamamlanması koşuluyla, SharePoint sitesi coğrafi taşımasını `Stop-SPOSiteContentMove` durdurabilirsiniz.

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a>SharePoint sitesi coğrafi taşıma durumunu belirleme

Aşağıdaki cmdlet'leri kullanarak bağlı olduğunuz coğrafi bölge dışında bir site taşımasının durumunu belirleyebilirsiniz:

- [Get-SPOSiteContentMoveState](/powershell/module/sharepoint-online/get-spositecontentmovestate) (Gruba bağlı olmayan siteler)
- [Get-SPOUnifiedGroupMoveState](/powershell/module/sharepoint-online/get-spounifiedgroupmovestate) (Gruba bağlı siteler)

`-SourceSiteUrl` Taşıma durumunu görmek istediğiniz siteyi belirtmek için parametresini kullanın.

Taşıma durumları aşağıdaki tabloda açıklanmıştır.

****

|Durum|Açıklama|
|---|---|
|Tetikleme için Hazır|Taşıma başlatılmadı.|
|Planlanan|Taşıma işlemi kuyrukta ancak henüz başlamadı.|
|InProgress (n/4)|Taşıma işlemi şu durumlardan birinde sürüyor: Doğrulama (1/4), Yedekleme (2/4), Geri Yükleme (3/4), Temizleme (4/4).|
|Başarı|Taşıma işlemi başarıyla tamamlandı.|
|Başarısız|Taşıma başarısız oldu.|
|

Taşıma hakkında ek bilgi görmek için seçeneğini de uygulayabilirsiniz `-Verbose` .

## <a name="user-experience"></a>Kullanıcı deneyimi

Site kullanıcıları, site farklı bir coğrafi konuma taşındığında en düşük kesintiyi fark etmelidir. Taşıma sırasında kısa bir salt okunur durum dışında, taşıma tamamlandıktan sonra mevcut bağlantılar ve izinler beklendiği gibi çalışmaya devam eder.

### <a name="site"></a>Site

Taşıma işlemi devam ederken site salt okunur olarak ayarlanır. Taşıma tamamlandıktan sonra, yer işaretlerine veya sitenin diğer bağlantılarına tıkladığında kullanıcı yeni coğrafi konumdaki yeni siteye yönlendirilir.

### <a name="permissions"></a>İzinler

Site izinleri olan kullanıcılar, taşıma sırasında ve tamamlandıktan sonra siteye erişmeye devam eder.

### <a name="sync-app"></a>Uygulamayı eşitleme

Eşitleme uygulaması, site taşıma işlemi tamamlandıktan sonra eşitlemeyi otomatik olarak algılar ve yeni site konumuna sorunsuz bir şekilde aktarır. Kullanıcının yeniden oturum açması veya başka bir işlem gerçekleştirmesi gerekmez. (Eşitleme uygulamasının sürüm 17.3.6943.0625 veya üzeri gereklidir.)

Taşıma işlemi devam ederken kullanıcı bir dosyayı güncelleştirirse, eşitleme uygulaması taşıma işlemi devam ederken dosya yüklemelerinin beklemede olduğunu bildirir.

### <a name="sharing-links"></a>Paylaşım bağlantıları

SharePoint sitesi coğrafi taşıma işlemi tamamlandığında, taşınan dosyaların mevcut paylaşılan bağlantıları otomatik olarak yeni coğrafi konuma yönlendirilir.

### <a name="most-recently-used-files-in-office-mru"></a>Office'te (MRU) En Son Kullanılan dosyalar

MRU hizmeti, taşıma tamamlandıktan sonra site URL'si ve içerik URL'leriyle güncelleştirilir. Bu, Word, Excel ve PowerPoint için geçerlidir.

### <a name="onenote-experience"></a>OneNote deneyimi

OneNote win32 istemcisi ve UWP (Evrensel) Uygulaması, site taşıma işlemi tamamlandıktan sonra not defterlerini otomatik olarak algılar ve yeni site konumuna sorunsuz bir şekilde eşitler. Kullanıcının yeniden oturum açması veya başka bir işlem gerçekleştirmesi gerekmez. Kullanıcıya görünen tek gösterge, site taşıma işlemi devam ederken not defteri eşitlemesinin başarısız olmasıdır. Bu deneyim aşağıdaki OneNote istemci sürümlerinde kullanılabilir:

- OneNote win32 – Sürüm 16.0.8326.2096 (ve üzeri)
- OneNote UWP – Sürüm 16.0.8431.1006 (ve üzeri)
- OneNote Mobil Uygulaması – Sürüm 16.0.8431.1011 (ve üzeri)

### <a name="teams-applicable-to-microsoft-365-group-connected-sites"></a>Teams (Microsoft 365 grup bağlı siteleri için geçerlidir)

SharePoint sitesi coğrafi taşıma işlemi tamamlandığında, kullanıcılar Teams uygulamasında Microsoft 365 grup sitesi dosyalarına erişebilir. Ayrıca, coğrafi taşıma öncesinde teams sohbeti aracılığıyla sitelerinden paylaşılan dosyalar taşıma tamamlandıktan sonra çalışmaya devam eder.

SharePoint sitesi coğrafi taşıma özelliği, Özel Kanalların bir coğrafi bölgeden diğerine taşınmasını desteklemez. Özel kanallar özgün coğrafi bölgede kalır.
  

### <a name="sharepoint-mobile-app-iosandroid"></a>SharePoint Mobile Uygulaması (iOS/Android)

SharePoint Mobile Uygulaması coğrafi olarak uyumludur ve sitenin yeni coğrafi konumunu algılayabilir.

### <a name="sharepoint-workflows"></a>SharePoint iş akışları

Site taşındıktan sonra SharePoint 2013 iş akışlarının yeniden yayımlanması gerekir. SharePoint 2010 iş akışları normal çalışmaya devam etmelidir.

### <a name="apps"></a>Apps

Uygulamaları olan bir siteyi taşıyorsanız, uygulama ve bağlantıları hedef coğrafi konumda kullanılamayabileceği için uygulamayı sitenin yeni coğrafi konumuna yeniden doğrulamalısınız.

### <a name="flow"></a>Akışı

Çoğu durumda, SharePoint sitesi coğrafi olarak taşındıktan sonra Akışlar çalışmaya devam eder. Taşıma tamamlandıktan sonra bunları test etmenizi öneririz.

### <a name="power-apps"></a>Power Apps

Power Apps'in hedef konumda yeniden oluşturulması gerekir.

### <a name="data-movement-between-geo-locations"></a>Coğrafi konumlar arasında veri taşıma

SharePoint içeriği için Azure Blob depolamayı kullanırken, sitelerle ve dosyalarıyla ilişkili meta veriler SharePoint'in içinde depolanır. Site kaynak coğrafi konumundan hedef coğrafi konumuna taşındıktan sonra, hizmet ilişkili Blob Depolama alanını da taşır. Blob Depolama yaklaşık 40 gün içinde tamamlar.
