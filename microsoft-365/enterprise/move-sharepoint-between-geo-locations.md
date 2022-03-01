---
title: Bir SharePoint sitesini farklı bir coğrafi konuma taşıma
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
description: Bir siteyi çok SharePoint ortamınız içinde farklı bir coğrafi konuma taşımayı ve değişiklikleri kullanıcılarınıza beklentilerinizi nasıl iletebilirsiniz.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9e4132b8399cc69067d24af6c3c9ec8e3baf52bd
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019528"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location"></a>Bir SharePoint sitesini farklı bir coğrafi konuma taşıma

Birden SharePoint coğrafi olarak taşı ile, SharePoint coğrafi olarak kendi ortamınız içinde diğer coğrafi konumlara da taşımanız gerekir.

Aşağıdaki site türleri coğrafi konumlar arasında taşınabilirsiniz:

- Microsoft 365 ilişkili siteler de dahil olmak üzere, grup bağlantılı Microsoft Teams
- Grup ilişkilendirmesi olmayan modern Microsoft 365 siteler
- Klasik SharePoint siteleri
- İletişim siteleri

Bir siteyi coğrafi konumlar arasında SharePoint için Genel Yönetici veya genel yönetici siz olursunuz.

Sitenin coğrafi olarak taşınma sırasında, site SharePoint göre yaklaşık 4-6 saat arasında bir salt okunur pencere vardır.

## <a name="best-practices"></a>En iyi uygulamalar

- Yordamı SharePoint için test sitesinde sitenin taşınmasına neden olan bir yöntem deneyin.
- Sitenin zamanlamadan önce taşınıp taşına öncesinde taşınıp taşına sahnelene olmadığını doğrulama.
- Mümkün olan zamanlamada, kullanıcının etkisini azaltmak için coğrafi siteler dışında iş saatleri dışında hareket eder.
- Site taşınmadan önce etkilenen kullanıcılarla iletişim kurma.

## <a name="communicating-to-your-users"></a>Kullanıcılarınıza iletişim kurma

Bir SharePoint coğrafi konumlar arasında taşımada, sitelerin kullanıcılarına (siteyi düzenleme becerisi olan genel olarak herkes) neler beklemeleri gerekir. Bu, kullanıcının kafa karışıklığını ve yardım masasına yapılan aramaları azaltmaya yardımcı olabilir. Taşımadan önce sitelerinizi kullananlara e-posta gönderin ve onlara aşağıdaki bilgileri haber verme:

- Taşımanın ne zaman başlaması ve ne kadar süreyle başlaması beklendiği
- Sitenin hangi coğrafi konuma taşınmakta olduğu ve yeni konuma erişmek için URL
- Taşıma sırasında düzenleme yapmalarını değil dosyalarını kapatmaları gerekir.
- Taşıma nedeniyle dosya izinleri ve paylaşım değişmez.
- Çok coğrafi bir ortamda kullanıcı deneyiminden neler beklemeleri gerekir?

Taşıma başarıyla tamamlandığında, sitelerinin kullanıcılarına sitelerinde çalışmaya devam edecekleri konusunda bilgi edinen bir e-posta göndermeye emin olun.

## <a name="scheduling-sharepoint-site-moves"></a>Sitenin SharePoint taşır

Sitenin önceden SharePoint zamanlamayı zaman edebilirsiniz (bu makalenin devamsında açıklanmıştır). Hareketleri şu şekilde zamanlayabiliriz:

- Bir defada en çok 4.000 hareket zamanabilirsiniz.
- Hareketler baş ettiğinde, sırada ve belirli bir zamanda en çok 4.000 bekleyen hareket olacak şekilde daha fazla zamanlamayı zamanabilirsiniz.
- Bir sitenin taşınacak en SharePoint boyutu 1 terabayttır (1 TB).

Daha SharePoint bir süre için sitenin coğrafi olarak taşınmalarını zamanlaması için, taşımayı başlarken aşağıdaki parametrelerden birini kullanın:

- `PreferredMoveBeginDate` – Taşıma, büyük olasılıkla belirtilen zamanda başlayacaktır.
- `PreferredMoveEndDate` – Taşıma, büyük olasılıkla belirtilen zamanda, en iyi çabayla tamamlanır.

Her iki parametre için de Saat Eşgüdümli Evrensel Saat (UTC) içinde belirtilmelidir.

## <a name="moving-the-site"></a>Siteyi taşıma

SharePoint coğrafi olarak taşıma işlemi yapmak için, sitenin bulunduğu coğrafi konumda SharePoint Yönetici URL'sinde bağlantınız ve taşıma işlemini gerçekleştirmeniz gerekir.

Örneğin, site URL'si , <https://contosohealthcare.sharepoint.com/sites/Turbines>bağlantısı yönetici URL'sinin SharePoint ise<https://contosohealthcare-admin.sharepoint.com>:

```powershell
Connect-SPOService -Url https://contosohealthcare-admin.sharepoint.com
```

![SharePoint gösteren bir Çevrimiçi Yönetim Kabuğu Connect-SPOService seçin.](../media/move-onedrive-between-geo-locations-image1.png)

### <a name="validating-the-environment"></a>Ortamı doğrulama

Site taşıma işlemini zamanlamadan önce, sitenin taşına öncesinde doğrulama gerçekleştirmenizi öneririz.

Sitelerin şu şekilde taşınmalarını desteklemez:

- İş Bağlantı Hizmetleri
- InfoPath formları
- Uygulanan Bilgi Hakları Yönetimi (IRM) şablonları

Tüm coğrafi konumların uyumlu olduğundan emin olmak için, 'i çalıştırın `Get-SPOGeoMoveCrossCompatibilityStatus`. Bu, tüm coğrafi konumlarınızı ve ortamın hedef coğrafi konumla uyumlu olup olmadığını görüntüler.

Siteniz üzerinde yalnızca doğrulama denetimi yapmak için, `Start-SPOSiteContentMove` parametreyle `-ValidationOnly` birlikte kullanarak sitenin taşınap taşınmayabileceklerini doğrulayın. Örneğin:

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

Site *taşınmaya* hazırsa Başarı ve engellenmiş *koşullardan herhangi* biri varsa Başarısız olarak geri döner.

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-microsoft-365-group"></a>İlişkili SharePoint grup taşımadan site için sitenin coğrafi olarak taşınma Microsoft 365 başlatma

Varsayılan olarak, sitenin ilk URL'si hedef coğrafi konumun URL'sinde değişir. Örneğin:

<https://Contoso.sharepoint.com/sites/projectx> Hedef <https://ContosoEUR.sharepoint.com/sites/projectx>

Grup ilişkilendirmesi Microsoft 365 siteler için, parametreyi kullanarak siteyi yeniden adlandırabilirsiniz`-DestinationUrl`. Örneğin:

<https://Contoso.sharepoint.com/sites/projectx> Hedef <https://ContosoEUR.sharepoint.com/sites/projecty>

Site taşımayı başlatmak için şu çalıştırın:

```powershell
Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>
```

![PowerShell penceresinin cmdlet'i Start-SPOSiteContentMove ekran görüntüsü.](../media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-a-microsoft-365-group-connected-site"></a>Grup bağlantılı SharePoint site için sitenin coğrafi Microsoft 365 taşımayı başlatma

Grup bağlantılı Microsoft 365 taşımak için, önce Genel Yöneticinin veya SharePoint Yöneticisinin, grup grubu için Tercih Edilen Veri Konumu (PDL) Microsoft 365 gerekir.

Bir grupla ilgili PDL'Microsoft 365 için:

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```

PDL'leri güncellediğinde site taşımayı başlatabilirsiniz:

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a>Sitenin coğrafi SharePoint taşımayı iptal etme

Taşıma devam etme SharePoint cmdlet'i kullanarak sitenin coğrafi olarak taşınma durumuna karşı `Stop-SPOSiteContentMove` durabilirsiniz.

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a>Sitenin coğrafi olarak SharePoint belirleme

Aşağıdaki cmdlet'leri kullanarak, bağlı olduğunuz coğrafi konum dışında bir site taşımanın durumunu öğrenebilirsiniz:

- [Get-SPOSiteContentMoveState](/powershell/module/sharepoint-online/get-spositecontentmovestate) (Grup bağlantılı olmayan siteler)
- [Get-SPOUnifiedGroupMoveState](/powershell/module/sharepoint-online/get-spounifiedgroupmovestate) (Grup bağlantılı siteler)

`-SourceSiteUrl` Taşıma durumunu görmek istediğiniz siteyi belirtmek için parametreyi kullanın.

Taşıma durumları aşağıdaki tabloda açıklanmıştır.

****

|Durum|Açıklama|
|---|---|
|Tetikleye Hazır|Taşıma başlamadı.|
|Zamanlanan|Taşıma sırasına göredir, ancak henüz başlamamıştır.|
|Çıkış (n/4)|Şu eyaletlerden biri için taşıma işlemi devam etmektedir: Doğrulama (1/4), Yedekle (4/2), Geri Yükle (3/4), Temizleme (4/4).|
|Başarılı|Taşıma başarıyla tamamlandı.|
|Başarısız|Taşıma başarısız oldu.|
|

Taşıma hakkında ek bilgi `-Verbose` görmek için bu seçeneği de uygulayabilirsiniz.

## <a name="user-experience"></a>Kullanıcı deneyimi

Site kullanıcıları, sitelerinin farklı bir coğrafi konuma taşındığında çok az aksaklık olduğunu fark edeler. Taşıma sırasında kısa bir salt okunur durumunun dışında, taşıma tamamlandıktan sonra da var olan bağlantılar ve izinler beklendiği gibi çalışmaya devam eder.

### <a name="site"></a>Site

Taşıma devam ederken, site salt okunur olarak ayarlanır. Taşıma tamamlandığında, kullanıcı sitenin yer işaretlerine veya diğer bağlantılarına tıklaytıktan sonra yeni coğrafi konumdaki yeni siteye yönlendirildi.

### <a name="permissions"></a>İzinler

Site için izinleri olan kullanıcılar, taşıma işlemi sırasında ve tamamlandıktan sonra siteye erişmeye devam edecektir.

### <a name="sync-app"></a>Eşitleme uygulaması

Eşitleme uygulaması, site taşıma işlemi tamamlandığında eşitlemeyi otomatik olarak algılar ve sorunsuz bir şekilde yeni site konumuna aktaracaktır. Kullanıcının yeniden oturum açması veya başka bir işlem yapma ihtiyacı olmaz. (Eşitleme uygulamasının 17.3.6943.0625 veya daha sonraki bir sürümü gereklidir.)

Taşıma devam ederken kullanıcı dosyayı güncellerse, eşitleme uygulaması taşıma devam ederken karşıya yüklemelerin beklemede olduğunu bildirecek.

### <a name="sharing-links"></a>Paylaşım bağlantıları

Site SharePoint taşıma tamamlandığında, taşınan dosyaların var olan paylaşılan bağlantıları otomatik olarak yeni coğrafi konuma yeniden yönlendirilir.

### <a name="most-recently-used-files-in-office-mru"></a>Dosyalarda En Son Office (MRU)

MRU hizmeti, taşıma tamamlandıktan sonra site URL'si ve içerik URL'leri ile güncelleştirilir. Bu durum Word, Excel ve PowerPoint için geçerlidir.

### <a name="onenote-experience"></a>OneNote deneyimi

OneNote win32 istemcisi ve UWP (Evrensel) Uygulaması, site taşıma işlemi tamamlandıktan sonra not defterlerini otomatik olarak algılar ve sorunsuz bir şekilde yeni site konumuyla eşitler. Kullanıcının yeniden oturum açması veya başka bir işlem yapma ihtiyacı olmaz. Kullanıcının tek görünür göstergesi, site taşıma devam ediyor olduğunda not defteri eşitlemenin başarısız olmasıdır. Bu deneyim, aşağıdaki istemci OneNote kullanılabilir:

- OneNote win32 – Sürüm 16.0.8326.2096 (ve sonrası)
- OneNote UWP – Sürüm 16.0.8431.1006 (ve sonrası)
- OneNote Uygulaması – Sürüm 16.0.8431.1011 (ve sonrası)

### <a name="teams-applicable-to-microsoft-365-group-connected-sites"></a>Teams (grup bağlantılı Microsoft 365 için geçerlidir)

Site SharePoint coğrafi taşıma tamamlandığında, kullanıcılar mobil uygulamada Microsoft 365 grup sitesi dosyalarına Teams. Buna ek olarak, Teams taşınmadan önce sohbet yoluyla paylaşılan dosyalar, taşıma tamamlandıktan sonra da çalışmaya devam edecektir.

SharePoint coğrafi olarak taşıma, Özel Kanalları bir coğrafi kanaldan diğerine taşımayı desteklemez. Özel kanallar orijinal coğrafi olarak kalır.
  

### <a name="sharepoint-mobile-app-iosandroid"></a>SharePoint Uygulaması (iOS/Android)

Mobil SharePoint coğrafi olarak uyumlu olup sitenin yeni coğrafi konumunu algılanabilir.

### <a name="sharepoint-workflows"></a>SharePoint iş akışları

SharePoint 2013 iş akışlarını site taşımadan sonra yeniden yayımlamak gerekir. SharePoint 2010 iş akışları normal şekilde çalışmaya devam edecektir.

### <a name="apps"></a>Uygulamalar

Siteyi uygulamalarla taşınıyorsanız, uygulama ve onun bağlantıları hedef coğrafi konumda kullanılamıyor olabilir ve sitenin yeni coğrafi konumu içinde uygulamayı yeniden doğrulanız.

### <a name="flow"></a>Flow

Çoğu durumda, akışlar sitenin coğrafi olarak taşınmadan SharePoint devam eder. Taşıma tamamlandıktan sonra bunları test etmenizi öneririz.

### <a name="power-apps"></a>Power Apps

Power Apps konumda yeniden oluşturulması gerekir.

### <a name="data-movement-between-geo-locations"></a>Coğrafi konumlar arasındaki veri hareketi

SharePoint için Azure Blob depolaması kullanılırken, sitelerle ve dosyalarıyla ilişkilendirilmiş meta veriler site içinde SharePoint. Site kaynak coğrafi konumdan hedef coğrafi konuma taşındıktan sonra, hizmet ilişkili Blob konumunu da Depolama. Blob Depolama, yaklaşık 40 gün içinde tamamlanır.
