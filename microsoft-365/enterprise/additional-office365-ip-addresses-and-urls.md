---
title: Office 365 IP Adresi ve URL Web hizmetine dahil olmayan diğer uç noktalar
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 01/31/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: ''
description: 'Özet: Yeni uç nokta Web hizmeti belirli senaryolar için birkaç uç nokta içermez.'
hideEdit: true
ms.openlocfilehash: 1592ea49cc33edf7e75998136975433bd764c432
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64915895"
---
# <a name="other-endpoints-not-included-in-the-office-365-ip-address-and-url-web-service"></a>Office 365 IP Adresi ve URL Web hizmetine dahil olmayan diğer uç noktalar

Bazı ağ uç noktaları daha önce yayımlanmıştı ve [Office 365 IP Adresi ve URL Web Hizmeti'ne](microsoft-365-ip-web-service.md) dahil değildi. Web hizmeti, kurumsal çevre ağı genelinde Office 365 bağlantısı için gereken ağ uç noktalarını yayımlar. Bu kapsam şu anda şunları içermez:

1. Microsoft veri merkezinden müşteri ağına (gelen karma sunucu ağ trafiği) gerekebilecek ağ bağlantısı.
2. Kurumsal çevre genelinde bir müşteri ağındaki sunuculardan ağ bağlantısı (giden sunucu ağ trafiği).
3. Kullanıcıdan gelen ağ bağlantısı gereksinimleri için sık rastlanmayan senaryolar.
4. DNS çözümleme bağlantısı gereksinimi (aşağıda listelenmemektedir).
5. Internet Explorer veya güvenilen siteler Microsoft Edge.

DNS dışında, açıklanan belirli bir senaryoya ihtiyacınız olmadığı sürece bu örneklerin tümü çoğu müşteri için isteğe bağlıdır.

<br>

****

|Satır|Amaç|Hedef|Tür|
|---|---|---|---|
|1|**PST ve dosya alımı için [İçeri Aktarma Hizmeti](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6)**|Daha fazla gereksinim için [İçeri Aktarma Hizmeti'ne](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) bakın.|Sık rastlanmayan giden senaryo|
|2|**[Office 365 için Microsoft Desteği ve Kurtarma Yardımcısı](https://diagnostics.office.com/#/)**|<https://autodiscover.outlook.com> <br> <https://officecdn.microsoft.com> <br> <https://api.diagnostics.office.com> <br> <https://apibasic.diagnostics.office.com> <br> <https://autodiscover-s.outlook.com> <br> <https://cloudcheckenabler.azurewebsites.net> <br> <https://login.live.com> <br> <https://login.microsoftonline.com> <br> <https://login.windows.net> <br> <https://o365diagtelemetry.trafficmanager.net> <br> <https://odc.officeapps.live.com> <br> <https://offcatedge.azureedge.net> <br> <https://officeapps.live.com> <br> <https://outlook.office365.com> <br> <https://outlookdiagnostics.azureedge.net>|Giden sunucu trafiği|
|3|**Azure AD Bağlan (SSO seçeneği)** <p> Uzak PowerShell & WinRM|Müşteri STS ortamı (AD FS Sunucusu ve AD FS Ara Sunucusu) \| TCP bağlantı noktaları 80 & 443|Gelen sunucu trafiği|
|4|AD FS Proxy sunucuları gibi **STS** (yalnızca federasyon müşterileri için)|Customer STS (AD FS Proxy gibi) \| Tcp 443 veya TCP 49443 bağlantı noktaları w/ClientTLS|Gelen sunucu trafiği|
|5|**[Birleşik Mesajlaşma/SBC tümleştirmesini Exchange Online](/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/configuration-notes-for-session-border-controllers)**|Şirket içi Oturum Sınır Denetleyicisi ile \*.um.outlook.com arasında çift yönlü|Yalnızca sunucuya giden trafik|
|6|**Posta Kutusu Geçişi**<p>Posta kutusu geçişi şirket içi [Exchange Karma'dan Office 365'a](/exchange/exchange-deployment-assistant) başlatıldığında, Office 365 yayımlanmış Exchange Web Hizmetleri (EWS)/Posta Kutusu Çoğaltma Hizmetleri (MRS) sunucunuza bağlanır. Belirli kaynak IP aralıklarından gelen bağlantıları kısıtlamak için Exchange Online sunucuları tarafından kullanılan NAT IP adreslerine ihtiyacınız varsa, bunlar "Exchange Online" hizmet alanı altında [OFFICE 365 URL & IP aralıklarında](urls-and-ip-address-ranges.md) listelenir. <p> BELIRLI kaynak IP aralıklarından TCP 443 bağlantılarını kısıtlamadan önce MRS proxy'sinin ayrı bir FQDN ve genel IP adresine çözümlendiğinden emin olarak OWA gibi yayımlanmış EWS uç noktalarına erişimin etkilenmediğinden emin olmak için dikkatli olunmalıdır.|Müşteri şirket içi EWS/MRS Proxy <br> TCP bağlantı noktası 443|Gelen sunucu trafiği|
|7|Exchange Serbest/Meşgul paylaşımı gibi **[Karma](/exchange/exchange-deployment-assistant) birlikte kullanım işlevleri**.|Müşteri şirket içi Exchange sunucusu|Gelen sunucu trafiği|
|8|**Karma proxy kimlik [doğrulamasını Exchange](/exchange/exchange-deployment-assistant)**|Müşteri şirket içi STS|Gelen sunucu trafiği|
|9|[karma Exchange](/exchange/exchange-deployment-assistant) yapılandırmak için Exchange **[Karma Yapılandırma Sihirbazı'nı](/exchange/hybrid-configuration-wizard)** kullanarak kullanılır <p> Not: Bu uç noktalar yalnızca karma Exchange yapılandırmak için gereklidir|80 & 443 numaralı TCP bağlantı noktalarında domains.live.com, yalnızca Exchange 2010 SP3 Karma Yapılandırma Sihirbazı için gereklidir <p> GCC Yüksek, DoD IP adresleri: 40.118.209.192/32; 168.62.190.41/32 <p> Dünya Çapında Ticari & GCC: \*.store.core.windows.net; asl.configure.office.com; tds.configure.office.com; mshybridservice.trafficmanager.net; <br> aka.ms/hybridwizard; <br> \*shcwreleaseprod.blob.core.windows.net/shcw/;|Yalnızca sunucuya giden trafik|
|10|**AutoDetect hizmeti**, [iOS ve Android için Outlook ile Karma Modern Kimlik Doğrulaması ile karma Exchange](/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) senaryolarında kullanılır [](/exchange/exchange-deployment-assistant) <p> `*.acompli.net` <br> `*.outlookmobile.com` <br> `*.outlookmobile.us` <br> `52.125.128.0/20` <br> `52.127.96.0/23`|TCP 443'te müşteri şirket içi Exchange sunucusu|Gelen sunucu trafiği|
|11|**Karma Azure AD kimlik doğrulaması Exchange**|*.msappproxy.net|Yalnızca tcp giden sunucu trafiği|
|12|Office 2016'daki Skype Kurumsal, UDP bağlantı noktalarını kullanan **video tabanlı ekran paylaşımını** içerir. Office 2013 ve önceki sürümlerdeki önceki Skype Kurumsal istemcileri 443 numaralı TCP bağlantı noktası üzerinden RDP kullanıyordu.|443 numaralı TCP bağlantı noktası 52.112.0.0/14'e açılır|Office 2013 ve önceki sürümlerinde eski istemci sürümlerini Skype Kurumsal|
|13|Skype Kurumsal Online'a **karma şirket içi sunucu bağlantısı** Skype Kurumsal|13.107.64.0/18, 52.112.0.0/14 <br> UDP bağlantı noktaları 50.000-59.999 <br> TCP bağlantı noktaları 50.000-59.999; 5061|Şirket içi sunucu giden bağlantısını Skype Kurumsal|
|14|Şirket içi karma bağlantısı olan **bulut PSTN'leri**, şirket içi konaklara açık ağ bağlantısı gerektirir. Skype Kurumsal Çevrimiçi karma yapılandırmaları hakkında daha fazla ayrıntı için|Bkz[. Skype Kurumsal Sunucu ile Office 365 arasında karma bağlantı planlama](/skypeforbusiness/hybrid/plan-hybrid-connectivity)|Şirket içi karma gelen Skype Kurumsal|
|15|**Kimlik doğrulaması ve kimlik FQDN'leri** <p> FQDN'nin `secure.aadcdn.microsoftonline-p.com` çalışması için istemcinizin Internet Explorer (IE) veya Edge Güvenilen Siteler Bölgesi'nde olması gerekir.||Güvenilen Siteler|
|16|**FQDN'leri Microsoft Teams** <p> Internet Explorer veya Microsoft Edge kullanıyorsanız, birinci ve üçüncü taraf tanımlama bilgilerini etkinleştirmeniz ve Teams için FQDN'leri Güvenilen Sitelerinize eklemeniz gerekir. Bu, 14. satırda listelenen paket genelindeki FQDN'lere, CDN'lere ve telemetriye ek olarak sağlanır. Daha fazla bilgi için bkz. [Microsoft Teams için bilinen sorunlar](/microsoftteams/known-issues).||Güvenilen Siteler|
|17|**Çevrimiçi SharePoint ve FQDN'leri OneDrive İş** <p> FQDN'de '' bulunan tüm '\<tenant\>.sharepoint.com' FQDN'lerinin çalışması için istemcinizin IE veya Edge Güvenilen Siteler Bölgesi'nde olması gerekir. 14. satırda listelenen paket genelindeki FQDN'lere, CDN'lere ve telemetriye ek olarak, bu uç noktaları da eklemeniz gerekir.||Güvenilen Siteler|
|18|**Yammer**  <br> Yammer yalnızca tarayıcıda kullanılabilir ve kimliği doğrulanmış kullanıcının bir ara sunucu üzerinden geçirilmesini gerektirir. tüm Yammer FQDN'lerin çalışması için istemcinizin IE veya Edge Güvenilen Siteler Bölgesi'nde olması gerekir.||Güvenilen Siteler|
|19|Şirket içi kullanıcı hesaplarını **[Azure AD](/azure/active-directory/hybrid/)** ile eşitlemek için Azure AD Bağlan kullanın.|Bkz[. Karma Kimlik Gerekli Bağlantı Noktaları ve Protokolleri](/azure/active-directory/hybrid/reference-connect-ports), [Azure AD bağlantısı sorunlarını giderme](/azure/active-directory/hybrid/tshoot-connect-connectivity) ve [Azure AD Bağlan Sistem Durumu Aracısı Yükleme](/azure/active-directory/hybrid/how-to-connect-health-agent-install#outbound-connectivity-to-the-azure-service-endpoints).|Yalnızca sunucuya giden trafik|
|20|**[Azure AD,](/azure/active-directory/hybrid/)** şirket içi kullanıcı hesaplarını Azure AD ile eşitlemek için Çin'de 21 ViaNet ile Bağlan.|\*.digicert.com:80 <BR> \*.entrust.net:80 <BR> \*.chinacloudapi.cn:443 <br> secure.aadcdn.partner.microsoftonline-p.cn:443 <br> \*.partner.microsoftonline.cn:443 <p> Ayrıca bkz. [Azure AD bağlantı sorunlarını giderme](https://docs.azure.cn/zh-cn/active-directory/hybrid/tshoot-connect-connectivity).|Yalnızca sunucuya giden trafik|
|21|**Microsoft Stream** (Azure AD kullanıcı belirteci gerekir). <br> Office 365 Worldwide (GCC dahil)|\*.cloudapp.net <br> \*.api.microsoftstream.com <br> \*.notification.api.microsoftstream.com <br> amp.azure.net <br> api.microsoftstream.com <br> az416426.vo.msecnd.net <br> s0.assets-yammer.com <br> vortex.data.microsoft.com <br> web.microsoftstream.com <br> TCP bağlantı noktası 443|Gelen sunucu trafiği|
|22|Hem sunucunun yeni yüklemeleri hem de Active Directory Domain Services (AD DS) ile ayarlanması gibi çok faktörlü kimlik doğrulama istekleri için **MFA sunucusunu** kullanın.|Bkz [. Azure AD çok faktörlü kimlik doğrulama sunucusunu kullanmaya başlama](/azure/active-directory/authentication/howto-mfaserver-deploy#plan-your-deployment).|Yalnızca sunucuya giden trafik|
|23|**Microsoft Graph Değişiklik Bildirimleri** <p> Geliştiriciler, Microsoft Graph'daki olaylara abone olmak için [değişiklik bildirimlerini](/graph/webhooks?context=graph%2fapi%2f1.0&view=graph-rest-1.0) kullanabilir.|Public Cloud: 52.159.23.209, 52.159.17.84, 52.147.213.251, 52.147.213.181, 13.85.192.59, 13.85.192.123, 13.89.108.233, 13.89.104.147, 20.96.21.67, 20.69.245.215, 137.135.11.161, 137.135.11.116, 52.159.107.50, 52.159.107.4, 52.229.38.131, 52.183.67.212, 52.142.114.29, 52.142.115.31, 51.124.75.43, 51.124.73.177, 20.44.210.83, 20.44.210.146, 40.80.232.177, 40.80.232.118, 20.48.12.75, 20.48.11.201, 104.215.13.23, 104.215.6.169, 52.148.24.136, 52.148.27.39, 40.76.162.99, 40.76.162.42 , 40.74.203.28, 40.74.203.27, 13.86.37.15, 52.154.246.238, 20.96.21.98, 20.96.21.115, 137.135.11.222, 137.135.11.250, 52.159.109.205, 52.159.102.72, 52.151.30.78, 52.191.173.85, 51.104.159.213, 51.104.159.181, 51.138.90.7, 51.138.90.52, 52.148.115.48, 52.148.114.238, 40.80.233.14, 40.80.239.196, 20.48.14.35, 20.48.15.147, 104.215.18.55, 104.215.12.254, 20.199.102.157, 20.199.102.73, 13.87.81.123, 13.87.81.35, 20.111.9.46, 20.111.9.77, 13.87.81.133, 13.87.81.141 <p> Microsoft Cloud for US Government: 52.244.33.45, 52.244.35.174, 52.243.157.104, 52.243.157.105, 52.182.25.254, 52.182.25.110, 52.181.25.67, 52.181.25.66, 52.244.111.156, 52.244.111.170, 52.243.147.249, 52.243.148.1 9, 52.182.32.51, 52.182.32.143, 52.181.24.199, 52.181.24.220 <p> 21Vianet tarafından sağlanan Microsoft Bulut Çin: 42.159.72.35, 42.159.72.47, 42.159.180.55, 42.159.180.56, 40.125.138.23, 40.125.136.69, 40.72.155.199, 40.72.155.216 <br> TCP bağlantı noktası 443 <p> Not: Geliştiriciler abonelikleri oluştururken farklı bağlantı noktaları belirtebilir.|Gelen sunucu trafiği|
|24|**Ağ Bağlantısı Durum Göstergesi**<p>Windows 10 ve 11 tarafından bilgisayarın İnternet'e bağlı olup olmadığını belirlemek için kullanılır (Windows olmayan istemciler için geçerli değildir). Bu URL'ye ulaşılamadığında Windows İnternet'e bağlı olmadığını varsayar ve Enterprise için M365 Uygulamaları etkinleştirme durumunu doğrulamayı denemez ve Exchange ve diğer hizmetlere yönelik bağlantıların başarısız olmasına neden olur.|www.msftconnecttest.com <br> 13.107.4.52<p>Ayrıca bkz. [Windows 11 Enterprise için bağlantı uç noktalarını yönetme](/windows/privacy/manage-windows-11-endpoints) ve [Windows 10 Enterprise, sürüm 21H2 için bağlantı uç noktalarını yönetme](/windows/privacy/manage-windows-21h2-endpoints).|Yalnızca sunucuya giden trafik|
|

## <a name="related-topics"></a>İlgili Konular

[Office 365 uç noktalarını yönetme](managing-office-365-endpoints.md)
  
[Microsoft 365 bağlantısını izleyin](./monitor-connectivity.md)
  
[İstemci bağlantısı](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[İçerik teslim ağları](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Azure IP Aralıkları ve Hizmet Etiketleri – Genel Bulut](https://www.microsoft.com/download/details.aspx?id=56519)

[Azure IP Aralıkları ve Hizmet Etiketleri – ABD Kamu Bulutu](https://www.microsoft.com/download/details.aspx?id=57063)

[Azure IP Aralıkları ve Hizmet Etiketleri – Almanya Bulutu](https://www.microsoft.com/download/details.aspx?id=57064)

[Azure IP Aralıkları ve Hizmet Etiketleri – Çin Bulutu](https://www.microsoft.com/download/details.aspx?id=57062)
  
[Microsoft Genel IP Alanı](https://www.microsoft.com/download/details.aspx?id=53602)
