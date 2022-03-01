---
title: Office 365 Content Delivery Network (CDN) Hızlı Başlangıç
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 01/13/2022
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
- m365initiative-coredeploy
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
description: Office 365 Content Delivery Network (CDN) Hızlı Başlangıç
ms.openlocfilehash: b0684fdfd8583ae6780cb23d47dc697582ae133b
ms.sourcegitcommit: af73b93a904ce8604be319e8dc7cadaf65d50534
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "63010086"
---
# <a name="office-365-content-delivery-network-cdn-quickstart"></a>Office 365 Content Delivery Network (CDN) Hızlı Başlangıç

SharePoint Online sayfalarınıza daha iyi performans sağlamak üzere statik varlıkları (resimler, JavaScript, Stil Sayfaları, WOFF dosyaları) barındırmak için yerleşik Office 365 Content Delivery Network **(** CDN) kullanabilirsiniz. Bu Office 365 CDN, statik varlıkları istekte bulunan tarayıcılara yaklaştırarak performansı geliştirmektedir ve bu da indirmeleri hızlandırmak ve gecikme süresini azaltmaya yardımcı olur. Ayrıca, Office 365 CDN http/2 protokolünü, geliştirilmiş sıkıştırma ve HTTP pipelining için kullanır. Office 365 CDN Hizmeti, SharePoint Online aboneliğinizin bir parçası olarak dahil edilir.

Daha ayrıntılı bilgi için bkz[. Office 365 Content Delivery Network Online ile CDN (SharePoint) kullanma](use-microsoft-365-cdn-with-spo.md).

>[!NOTE]
>Bu Office 365 CDN yalnızca üretim (dünya çapında) buluttaki kiracılar tarafından kullanılabilir. ABD Kamu, Çin ve Almanya bulutlarında yer alan kiracılar şu anda bu Office 365 CDN.

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-identify-items-not-in-cdn"></a>Farklı veri bağlantılarında yer SharePoint tanımlamak için Sayfa Tanılama aracını CDN

SharePoint Online **sayfalarınıza bir kaynakta** eklenebilir varlıkları kolayca listeleyebilirsiniz. SharePoint Için Sayfa Tanılama araç tarayıcı uzantısını CDN kullanabilirsiniz.

**SharePoint** için Sayfa Tanılama aracı, hem SharePoint Online modern portalı hem de klasik yayımlama sitesi sayfalarını analizen yeni Microsoft Edge (<https://www.microsoft.com/edge>) ve Chrome tarayıcıları için tarayıcı uzantısıdır. Bu araç, sayfanın tanımlanmış bir performans ölçütleri kümesine karşı nasıl bir performans performansına sahip olduğunu gösteren, analize tabi her sayfa için bir rapor sağlar. Yeni uygulama için Sayfa Tanılama aracını yüklemek ve SharePoint için, SharePoint [Online'da Sayfa Tanılama aracını kullanma sayfasını ziyaret edin](./page-diagnostics-for-spo.md).

SharePoint Online sayfasında SharePoint Için Sayfa Tanılama aracını çalıştırarak, tanılama testleri sekmesine tıklar ve kullanıcı tarafından barındır CDN. Bu varlıklar, aşağıdaki ekran görüntüsünde **Content Delivery Network (CDN)** denetimi başlığı altında listelenir.

![Sayfa tanılama'yı seçin.](../media/page-diagnostics-for-spo/pagediag-results-general.PNG)

>[!NOTE]
>Sayfa Tanılama aracı yalnızca SharePoint Online için çalışır ve SharePoint sistem sayfasında kullanılamaz.

## <a name="cdn-overview"></a>CDN Genel Bakış

Office 365 CDN, yüksek hızlı bir genel ağ üzerinden resimler ve javascript dosyaları gibi sık erişilen nesneleri dağıtarak, sayfa yükleme süresini azaltarak ve barındırılan nesnelere kullanıcıya mümkün olduğunca yakın erişim sağlayarak, kullanıcılar için performansı en iyi duruma getirmek üzere tasarlanmıştır. Kaynak CDN, varlıklarınızı kaynak olarak adlandırılan bir konumdan _getirir_. Köken, URL SharePoint erişilebilen bir site, belge kitaplığı veya klasör olabilir.

ana Office 365 CDN iki temel türe ayrılır:

- **Genel CDN**, JS (JavaScript), CSS (Stil Sayfaları), Web Yazı Tipi Dosyası (WOFF, WOFF2) ve şirket logosu gibi özel olmayan resimler için kullanılacak şekilde tasarlanmıştır.
- **Özel CDN** resimler (PNG, JPG, JPEG, vb.) için kullanılacak şekilde tasarlanmıştır.

Hem genel hem de özel kaynaklarda yer a seçebilirsiniz. Çoğu kuruluş bu ikisi için bir birleşim uygulamayı seçer. Hem genel hem de özel seçenekler benzer performans kazançları sağlar, ancak her seçeneğin benzersiz öznitelikleri ve avantajları vardır. Genel ve özel kaynak bilgileri hakkında daha fazla CDN için bkz[. Her kaynağın genel mi yoksa özel mi olacağını seçme](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).

## <a name="how-to-enable-public-and-private-cdn-with-the-default-configuration"></a>Ortak ve Özel CDN varsayılan yapılandırmayla etkinleştirme
Kiracının ayarlarını değiştirmeden önce CDN uyumluluk, güvenlik ve gizlilik ilkelerini karşıladığı doğru olmalıdır.

Daha ayrıntılı yapılandırma ayarları için veya CDN'yi zaten etkinleştirdiyseniz ve başka konumlar (kaynak) eklemek istiyorsanız, SharePoint Online Yönetim Kabuğu'Office 365 CDN ayarlama ve [yapılandırma bölümüne bakın](use-microsoft-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell).

Bağlan Çevrimiçi Yönetim Kabuğu'SharePoint kiracınıza geri alın:

```PowerShell
Connect-SPOService -Url https://<YourTenantName>-admin.sharepoint.com
```

Varsayılan yapılandırmada hem genel hem de özel kaynak kullanımına olanak sağlamak için, aşağıdaki komutu yazın:

```PowerShell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Bu cmdlet'lerin çıkışı aşağıdaki gibi olmalıdır:

![Set-SPOTenantCdnEnabled çıktısı.](../media/O365-CDN/o365-cdn-enable-output.png)

## <a name="see-also"></a>Ayrıca bkz.

[SharePoint Online için Sayfa Tanılama aracını kullanma](./page-diagnostics-for-spo.md)

[CDN Online ile Office 365 Content Delivery Network (CDN) SharePoint kullanma](use-microsoft-365-cdn-with-spo.md)

[İçerik Teslim Ağları](./content-delivery-networks.md)

[Network planning and performance tuning for Office 365](./network-planning-and-performance.md)

[SharePoint Serisi - Office 365 CDN video serisi](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
