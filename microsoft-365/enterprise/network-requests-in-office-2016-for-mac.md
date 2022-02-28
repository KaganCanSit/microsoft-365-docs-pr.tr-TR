---
title: Ağ istekleri Office Mac
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/9/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365_Setup
- seo-marvel-apr2020
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: Bu makalede, uygulamaların hangi uç noktalara Office Mac url'leri ve sağlanan hizmetlere ulaşmaya çalış olduğu açıklanmıştır.
ms.openlocfilehash: 37071b0aaf9e6f172d99a10cb4a1506f1627ef03
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984439"
---
# <a name="network-requests-in-office-for-mac"></a>Ağ istekleri Office Mac

Office Mac uygulamaları macOS platformunda yerel bir uygulama deneyimi sunar. Her uygulama, ağ erişiminin mevcut olmadığını durumlarla birlikte çok çeşitli senaryolarda çalışacak şekilde tasarlanmıştır. Makine bir ağa bağlandığında, uygulamalar gelişmiş işlevsellik sağlamak için bir dizi Web tabanlı hizmetlere otomatik olarak bağlanır. Aşağıdaki bilgi, uygulamaların hangi uç noktalara ve URL'lere ulaşmaya çalışta olduğunu ve sağlanan hizmetleri açıklar. Bu bilgiler, ağ yapılandırma sorunlarını giderirken ve ağ ara sunucuları için ilkeleri ayarlarken yararlı olur. Bu makaledeki ayrıntıların, Microsoft Office 365 bilgisayarlar için uç noktaları içeren en iyi [URL](urls-and-ip-address-ranges.md) ve adres aralıkları makalesini tamamlar Windows. Bu makaledeki bilgiler, not olmadığı sürece, bir perakende satış mağazasından veya toplu lisans sözleşmesi aracılığıyla bir defalık satın alınan Mac ve Office Mac 2016 için Office 2019 için de geçerlidir. 

  
Bu makalenin büyük bölümü, o uç nokta tarafından sağlanan hizmet veya özelliğin ağ URL'lerini, türünü ve açıklamasını ayrıntılarıyla anlatan tablolardır. Her bir Office, hizmet ve uç nokta kullanımına göre farklılık gösterebilir. Aşağıdaki tablolarda aşağıdaki uygulamalar tanımlanmıştır:
  
- W: Word
- P: PowerPoint
- X: Excel
- O: Outlook
- N: OneNote
   
URL türü aşağıdaki gibi tanımlanır:
  
- ST: Statik - URL, istemci uygulamasında sabit kodludur.
    
- SS: Semi-Static - URL, bir web sayfasının veya yönlendirmesinin parçası olarak kodlanmış.
    
- CS: Yapılandırma Hizmeti - URL, yapılandırma yapılandırması hizmetinin bir Office verilir.

    
## <a name="office-for-mac-default-configuration"></a>Office Mac yapılandırmayı yapılandırma

 **Yükleme ve güncelleştirmeler**
  
Aşağıdaki ağ uç noktaları, microsoft Office Mac yükleme programını (Content Delivery Network) indirmek CDN.
  
|**URL**|**Tür**|**Açıklama**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |ST  <br/> |Microsoft 365 Yükleme Portalı ileri bağlantı hizmetini en son yükleme paketlerine iletme bağlantısı hizmetidir.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |Yükleme paketlerinin yükleme konumu Content Delivery Network.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |Yükleme paketlerinin yükleme konumu Content Delivery Network.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |ST  <br/> |Microsoft AutoUpdate için Yönetim Denetimi uç noktası  <br/> |
   
 **İlk uygulama başlatma**
  
Bir sonraki ilk başlatmada aşağıdaki ağ uç noktalarıyla Office uygulaması. Bu uç noktalar kullanıcılara Office gelişmiş kimlik özellikleri sağlar ve lisans türüne bakılmaksızın (Toplu Lisans yüklemeleri dahil) URL'lerle bağlantı kurabilirsiniz.
  
|**URL**|**Uygulamalar**|**Tür**|**Açıklama**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting' Yapılandırması - Özelliğin aydınlatması ve denemelere olanak sağlar.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting' Ağ Yapılandırma Testi  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |'Flighting' Ağ Yapılandırma Testi  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office Yapılandırma Hizmeti - Hizmet uç noktalarının ana listesi.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office Telemetrisi indirme - İstemciyi telemetri hizmetine hangi verilerin ve olayların yük durumuyla ilgili bilgi sağlar.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |OneNote Telemetri Hizmeti  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office Telemetri Upload Raporlama - İstemcide oluşan "Heartbeart" ve hata olayları telemetri hizmetine yüklendi.  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Office Şablonu Hizmeti - Kullanıcılara çevrimiçi belge şablonları sağlar.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |CS  <br/> |Office yüklemeleri - PNG Depolama resimlerini içerir.  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Uygulama yapılandırmalarını Office depolar.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Office Tümleştirme Hizmetleri Kataloğu (hizmetlerin ve uç noktaların listesi) ve Ana Realm Bulma'ya tıklayın.  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Ana Realm Keşif v2 (15.40 ve sonrası) için kaynaklar  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft AutoUpdate Bildirimleri - Güncelleştirme olup olduğunu denetler  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |Microsoft Ajax JavaScript Kitaplığı  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Daha fazla yapılandırma ve Office için Wikipedia uygulaması.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing kaynakları ve yapılandırma için Office Map uygulamasını kullanın.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Kişiler Graph yapılandırma ve Office için uygulama kullanır.  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |ST  <br/> |Yeni içerikler hakkında OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |ST  <br/> |Yeni içerikler: OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |Fotoğraflar için Yeni resimler OneNote.  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ST  <br/> |Uygulama içinde Destek Hizmeti.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |ST  <br/> |E-posta Hesabı Algılama Hizmeti.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook Bulma  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook hizmeti için Microsoft 365 uç noktası.  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |ST  <br/> |Eklenti Outlook simgeler.  <br/> |
   
> [!NOTE]
> Hızlı Office Hizmeti, yalnızca Mac için değil, tüm Microsoft Office için otomatik bulma hizmeti olarak davranır. Yanıtta döndürülen uç noktalar yarı statiktir ve bu değişiklik çok seyrek olabilir ama yine de mümkündür. 
  
 **Oturum aç**
  
Aşağıdaki ağ uç noktaları, bulut tabanlı depolamada oturum aken bağlantı kurabilirsiniz. Hesap türünüze bağlı olarak, farklı hizmetlerle bağlantı kurabilirsiniz. Örneğin:
  
- **MSA: Microsoft Hesabı** - normalde tüketici ve perakende senaryolarında kullanılır 
    
- **OrgID: Kuruluş Hesabı** - normalde ticari senaryolarda kullanılır 
    
|**URL**|**Uygulamalar**|**Tür**|**Açıklama**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |ST  <br/> |Windows Yetkilendirme Hizmeti  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft 365 Açma Hizmeti (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft Hesabı Oturum Açma Hizmeti (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |Microsoft Hesabı Oturum Açma Hizmeti Yardımcısı (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |Microsoft 365 Oturum Açma Markalama (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Konum Belirleyicisi'Depolama ve Yerler  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |En Son Kullanılan (MRU) belge hizmeti  <br/> |
   
> [!NOTE]
> Abonelik tabanlı lisanslar ve perakende lisansları için, oturum açma özelliği hem ürünü etkinleştirir hem de Faturalar gibi bulut kaynaklarına OneDrive. Toplu Lisans yüklemeleri için, kullanıcılardan yine oturum açması istenir (varsayılan olarak) ancak ürün zaten etkinleştirildiğinden bu yalnızca bulut kaynaklarına erişim için gereklidir. 
  
 **Ürün etkinleştirme**
  
Aşağıdaki ağ uç noktaları, abonelik Microsoft 365 Perakende Lisansı etkinleştirmeleri için geçerlidir. Özel olarak, Toplu Lisans yüklemeleri için geçerli OLMAZ.
  
|**URL**|**Uygulamalar**|**Tür**|**Açıklama**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Office Lisans Hizmeti  <br/> |
   
 **What's New content**
  
Aşağıdaki ağ uç noktaları yalnızca Microsoft 365 için geçerlidir.
  
|**URL**|**Uygulamalar**|**Tür**|**Açıklama**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |What's New JSON page content.  <br/> |
   
 **Araştırmacı**
  
Aşağıdaki ağ uç noktaları yalnızca Microsoft 365 için geçerlidir.
  
|**URL**|**Uygulamalar**|**Tür**|**Açıklama**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Araştırmacı Web Hizmeti  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |Araştırmacı Statik İçeriği  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |CS  <br/> |Araştırmacı İçerik Sağlayıcısı  <br/> |
   
 **Akıllı Arama**
  
Aşağıdaki ağ uç noktaları hem Abonelik hem Microsoft 365 Perakende/Toplu Lisans etkinleştirmeleri için geçerlidir.
  
|**URL**|**Uygulamalar**|**Tür**|**Açıklama**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Analizler Web Hizmeti  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |JQuery Kitaplığı  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |JavaScript Kitaplığını destekleme  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |Analizler Sağlayıcısı  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |Analizler Sağlayıcısı  <br/> |
   
 **PowerPoint Tasarımcısı**
  
Aşağıdaki ağ uç noktaları yalnızca Microsoft 365 için geçerlidir.
  
|**URL**|**Uygulamalar**|**Tür**|**Açıklama**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint Tasarımcısı web hizmeti  <br/> |
   
 **PowerPoint Hızlı Başlangıç**
  
Aşağıdaki ağ uç noktaları yalnızca Microsoft 365 için geçerlidir.
  
|**URL**|**Uygulamalar**|**Tür**|**Açıklama**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint Hızlı Başlangıç web hizmeti  <br/> |
   
 **Gülümseme/Kaş Çatma gönderme**
  
Aşağıdaki ağ uç noktaları hem Abonelik hem Microsoft 365 Perakende/Toplu Lisans etkinleştirmeleri için geçerlidir.
  
|**URL**|**Uygulamalar**|**Tür**|**Açıklama**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |'Send a Smile' Hizmeti  <br/> |
   
 **Desteğe Başvurun**
  
Aşağıdaki ağ uç noktaları hem Abonelik hem Microsoft 365 Perakende/Toplu Lisans etkinleştirmeleri için geçerlidir.
  
|**URL**|**Uygulamalar**|**Tür**|**Açıklama**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |CS  <br/> |Destek Hizmetine Başvurun  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |CS  <br/> |Uygulama içinde Destek Hizmeti  <br/> |
   
 **PDF Olarak Kaydet**
  
Aşağıdaki ağ uç noktaları hem Abonelik hem Microsoft 365 Perakende/Toplu Lisans etkinleştirmeleri için geçerlidir.
  
|**URL**|**Uygulamalar**|**Tür**|**Açıklama**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |CS  <br/> |Word belge dönüştürme hizmeti (PDF)  <br/> |
   
 **Office Uygulamaları (diğer adıyla eklentiler)**
  
Aşağıdaki ağ uç noktaları, Microsoft 365 eklentilerine güveni olduğunda hem Microsoft 365 Hem de Office Perakende/Toplu Lisans etkinleştirmeleri için geçerlidir.
  
|**URL**|**Uygulamalar**|**Tür**|**Açıklama**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |Office uygulaması depolama yapılandırmasını yapılandırma  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia uygulama kaynakları  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing Map uygulama kaynakları  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |Kişiler Graph kaynakları  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |Office Yeniden Yönlendirme Hizmeti  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SS  <br/> |Office JavaScript Kitaplıkları  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |Office uygulamaları için Telemetri ve Raporlama Hizmeti  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |SS  <br/> |Microsoft Ajax JavaScript Kitaplığı  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |Microsoft Ajax JavaScript Kitaplığı  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Office JavaScript Kitaplıkları  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Destek kaynakları  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Destek kaynakları  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |Destek kaynakları  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |JavaScript kitaplığı  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |Hata raporlama  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |Yazı tipi kaynakları  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |Telemetri Hizmeti  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Telemetri Raporlama  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |Microsoft Store Varlık Kitaplığı  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |SS  <br/> |Wikipedia sayfa kaynakları  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |SS  <br/> |Wikipedia medya kaynakları  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |SS  <br/> |Wikipedia korumalı alan çerçevesi  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |Harita şablonları  <br/> |
   
 **Güvenli Bağlantılar**
  
Aşağıdaki ağ uç noktası, yalnızca Office abonelik için tüm Microsoft 365 için geçerlidir.
  
|**URL**|**Tür**|**Açıklama**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |Microsoft Kasa Bağlantı Hizmeti  <br/> |
   
 **Kilitlenme raporlaması**
  
Aşağıdaki ağ uç noktası, hem Office hem de Perakende Microsoft 365 Toplu Lisans etkinleştirmeleri için tüm etki alan uygulamaları için geçerlidir. İşlem beklenmedik bir şekilde kilitleniyorsa, bir rapor oluşturulur ve Watson hizmetine gönderilir.
  
|**URL**|**Tür**|**Açıklama**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |ST  <br/> |Microsoft Hata Raporlama Hizmeti  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |ST  <br/> |Office İşbirliğine Analizler Hizmeti  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>Ağ isteklerini ve trafiğini azaltma seçenekleri

Varsayılan varsayılan Office Mac hem işlevsellik hem de makinenin güncelliği açısından en iyi kullanıcı deneyimini sağlar. Bazı senaryolarda, uygulamaların ağ uç noktalarıyla bağlantı kurmasını engellemek isterseniz. Bu bölümde, bunu yapma seçenekleri ele almaktadır.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>Bulut Bulut Bağlantı Sign-In devre dışı Office Add-Ins
  
Toplu Lisans müşterilerinin belgeleri bulut tabanlı depolamaya kaydetmeyle ilgili sıkı ilkeleri olabilir. Aşağıdaki uygulama başına tercih, MSA/OrgID Oturum açma özelliğini devre dışı bırakmak ve eklentilere erişim Office için ayarlanmış olabilir.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

Kullanıcılar Sign-In erişmeye denerse, ağ bağlantısının olmadığını hata ileleri görebilirler. Bu tercih çevrimiçi ürün etkinleştirmesini de engellemesi nedeniyle, yalnızca Toplu Lisans yüklemelerinde kullanılmalıdır. Özel olarak, bu tercihin Office uygulamaların aşağıdaki uç noktalara erişmesini engellemektedir:
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- Yukarıdaki 'Oturum Açma' bölümünde listelenen tüm uç noktalar.
    
- Yukarıdaki 'Akıllı Arama' bölümünde listelenen tüm uç noktalar.
    
- Yukarıdaki 'Ürün Etkinleştirme' bölümünde listelenen tüm uç noktalar.
    
- Yukarıdaki 'En Son Uygulamalar (diğer Office)' bölümünde listelenen tüm uç noktalar.
    
Kullanıcıya tüm işlevselliği yeniden oluşturmak için tercihi '2' olarak ayarlayın veya kaldırın.
  
> [!NOTE]
> Bu tercih, Office Mac 15.25 [160726] veya sonraki bir derleme gerektirir. 
  
### <a name="telemetry"></a>Telemetri 
  
Office Mac aralıklarla telemetri bilgilerini Microsoft'a geri gönderir. Veriler 'Nexus' uç noktasına karşıya yüklendi. Telemetri verileri mühendislik ekibinin her bir veri kaynağında durumu ve beklenmedik davranışları değerlendirmesine yardımcı Office uygulaması. Telemetriye iki kategori vardır:
  
- **Sinyal** , sürüm ve lisans bilgilerini içerir. Bu veriler uygulama başlatma sırasında hemen gönderilir. 
    
- **Kullanım** , uygulamaların nasıl kullanıldıklarına ilişkin bilgileri ve önemli olmayan hataları içerir. Bu veriler her 60 dakikada bir gönderilir. 
    
Microsoft gizliliğinizi çok ciddiye alır. Microsoft'un veri toplama ilkesi hakkında bilgi için: [https://privacy.microsoft.com](https://privacy.microsoft.com). Uygulamaların 'Kullanım' telemetrisi göndermesini önlemek için **, SendAllTelemetryEnabled** tercihi ayarlanabilir. Tercih uygulama başına yöneliktir ve macOS Yapılandırma Profilleri üzerinden veya el ile Terminal'den ayarlanabilir: 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

Sinyal telemetrisi her zaman gönderilir ve devre dışı bırakılamaz.
  
### <a name="crash-reporting"></a>Kilitlenme raporlaması
  
Önemli bir uygulama hatası oluştuğunda, uygulama beklenmedik bir şekilde sonlandırılır ve 'Watson' hizmetine kilitlenme raporu yükler. Kilitlenme raporu, uygulamanın kilitlenmeye yol aken adımlarının listesi olan bir çağrı yığınını oluşur. Bu adımlar, mühendislik ekibinin başarısız olan işlevi ve başarısız olan işlevi tam olarak belirlemelerini sağlar.
  
Bazı durumlarda, belgenin içeriği uygulamanın kilitlenmeye neden olabilir. Uygulama bu nedenle belgeyi tanımlarsa, kullanıcıya çağrı yığınıyla birlikte belgeyi de göndermeyi onay verip göndermeyeceklerini sorar. Kullanıcılar bu soruya bilinçli bir seçim yapmak için kullanılabilir. IT yöneticileri belgelerin aktarımı konusunda sıkı gereksinimlere sahip olabilir ve kullanıcı adına belgeleri hiçbir zaman gönderme kararına sahip olabilir. Belgelerin gönderilmesini önlemek ve kullanıcıya sorulması engellemek için aşağıdaki tercih ayarlanmış olabilir:
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> **SendAllTelemetryEnabled** **FALSE olarak ayarlanırsa**, bu işlem için tüm kilitlenme raporlaması devre dışı bırakılır. Kullanım telemetrisi göndermeden kilitlenme bildirimini etkinleştirmek için aşağıdaki tercih kullanılabilir: ```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>Güncelleştirmeler
  
Microsoft, düzenli Office Mac (normalde ayda bir) güncelleştirmeler yayımlar. En son güvenlik düzeltmelerini yüklemek için, kullanıcıların ve IT yöneticilerinin makinelerini güncel tutmalarını kesinlikle tavsiye etmekz. MAKINE yöneticilerinin makine güncelleştirmelerini yakından kontrol etmek ve yönetmek istediğiniz durumlarda, Otomatik Güncelleştirme işleminin ürün güncelleştirmelerini otomatik olarak algılamasını ve sunması engellemek için aşağıdaki tercih kullanılabilir:
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>Güvenlik Duvarı/Ara Sunucu ile İstekleri Engelleme
  
Kuruluş bir güvenlik duvarı veya ara sunucu aracılığıyla URL'lere yönelik istekleri engellerse, bu belgede listelenen URL'leri izin verilen veya 40X yanıtıyla (örneğin 403 veya 404) listelenen engellemeyi yapılandırmış olun. 40X yanıtı, Office uygulamalarının kaynağa erişimemelerini zarif bir şekilde kabul etmelerine olanak sağlar ve yalnızca bağlantıyı bırakmaktansa daha hızlı bir kullanıcı deneyimi sağlar; bu da istemcinin yeniden denemesine neden olur.
  
Ara sunucunuz kimlik doğrulaması gerektiriyorsa, istemciye 407 yanıtı döndürülür. En iyi deneyimi yaşamak için, NTLM ve Kerberos sunucularıyla çalışmak için belirli düzeltmeler içeren Office Mac derlemeleri Office Mac veya daha yeni bir sürüm kullanırsanız, bu derlemeleri kullanmaya devam edin.
  
  
## <a name="see-also"></a>Ayrıca bkz.

[Office 365 URL’leri ve IP adresi aralıkları](urls-and-ip-address-ranges.md)

