---
title: IP Adresi ve URL Web hizmeti Office 365 diğer uç noktalar bu adrese dahil değil
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
description: 'Özet: Yeni uç nokta Web hizmeti, belirli senaryolar için birkaç uç noktası içermemektedir.'
hideEdit: true
ms.openlocfilehash: 0453efbea7957c3cf859c59da7a2cff7db04b4f0
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2022
ms.locfileid: "63010130"
---
# <a name="other-endpoints-not-included-in-the-office-365-ip-address-and-url-web-service"></a>IP Adresi ve URL Web hizmeti Office 365 diğer uç noktalar bu adrese dahil değil

Bazı ağ uç noktaları daha önce yayımlanmıştır ve ilk kez IP [Adresi Office 365 URL Web Hizmeti'ne ekli değildir](microsoft-365-ip-web-service.md). Web hizmeti, kurumsal çevre ağı genelinde İnternet bağlantısının Office 365 ağ uç noktalarını yayımlar. Şu anda bu kapsam şunları içermez:

1. Microsoft veri merkezinden müşteri ağına (gelen karma sunucu ağ trafiği) gerekli olan ağ bağlantısı.
2. Kurumsal çevre genelinde bir müşteri ağının sunucularından ağ bağlantısı (giden sunucu ağ trafiği).
3. Kullanıcıdan gelen ağ bağlantısı gereksinimleri için sık karşılaşılan senaryolar.
4. DNS çözümleme bağlantı gereksinimi (aşağıda listelenmiyor)
5. Internet Explorer veya Microsoft Edge Siteleri Kullanma.

DNS'den farklı olarak, açıklanan belirli bir senaryoya ihtiyacınız yoksa bu örneklerin çoğu müşteri için isteğe bağlıdır.

<br>

****

|Satır|Amaç|Hedef|Tür|
|---|---|---|---|
|1|**PST [ve](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) dosya alımı için İçeri Aktarma Hizmeti**|Daha fazla gereksinimler [için İçeri Aktarma](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) Hizmeti'ne bakın.|Seyrek giden senaryo|
|2|**[Destek ve Kurtarma Yardımcısı için Microsoft Office 365](https://diagnostics.office.com/#/)**|<https://autodiscover.outlook.com> <br> <https://officecdn.microsoft.com> <br> <https://api.diagnostics.office.com> <br> <https://apibasic.diagnostics.office.com> <br> <https://autodiscover-s.outlook.com> <br> <https://cloudcheckenabler.azurewebsites.net> <br> <https://login.live.com> <br> <https://login.microsoftonline.com> <br> <https://login.windows.net> <br> <https://o365diagtelemetry.trafficmanager.net> <br> <https://odc.officeapps.live.com> <br> <https://offcatedge.azureedge.net> <br> <https://officeapps.live.com> <br> <https://outlook.office365.com> <br> <https://outlookdiagnostics.azureedge.net>|Giden sunucu trafiği|
|3|**Azure AD Bağlan (SSO seçeneği yok)** <p> Uzak PowerShell & WinRM|Müşteri STS ortamı (AD FS Sunucusu ve AD FS Proxy'si) \| TCP bağlantı noktaları 80 & 443|Gelen sunucu trafiği|
|4|**AD FS** Proxy sunucuları gibi STS (yalnızca federasyon müşterileri için)|ClientTLS ile Müşteri STS'si (AD FS Proxy'si gibi) \| Bağlantı Noktaları TCP 443 veya TCP 49443|Gelen sunucu trafiği|
|5|**[Exchange Online Birleşik Mesajlaşma/SBC tümleştirmesi](/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/configuration-notes-for-session-border-controllers)**|Şirket içi Oturum Sınırı Denetleyicisi ile \*.um.outlook.com|Giden sunucuya yalnızca trafik|
|6|**Posta Kutusu Geçişi**<p>Posta kutusu geçişi şirket içi Exchange [Karma'dan](/exchange/exchange-deployment-assistant) Office 365'a Office 365 yayımlanmış Exchange Web Hizmetleri (EWS)/Mailbox Replication Services (MRS) sunucunuza bağlanacak. Belirli kaynak IP aralıklarından gelen bağlantıları kısıtlamak için Exchange Online sunucuları tarafından kullanılan NAT IP adreslerine ihtiyacınız varsa, bunlar Office 365 URL veya &" hizmet alanı altında [IP](urls-and-ip-address-ranges.md) Exchange Online listelenir. <p> OWA gibi yayımlanan EWS uç noktalarına erişimin, belirli kaynak IP aralıklarından TCP 443 bağlantılarını kısıtlamadan önce MRS proxy'nizin ayrı bir FQDN ve genel IP adresine çözüme çözüme çözüm olduğundan emin olmak için dikkat edin.|Müşteri şirket içi EWS/MRS Proxy <br> TCP bağlantı noktası 443|Gelen sunucu trafiği|
|7|**[Exchange](/exchange/exchange-deployment-assistant)/Meşgul paylaşımı gibi Karma** birlikte kullanılabilirlik işlevlerini içerir.|Müşteri şirket içi Exchange sunucusu|Gelen sunucu trafiği|
|8|**[Exchange Ara Sunucu Kimlik](/exchange/exchange-deployment-assistant) Doğrulaması**|Müşteri şirket içi STS|Gelen sunucu trafiği|
|9|Karma Yapılandırma Sihirbazı [Exchange kullanılarak](/exchange/exchange-deployment-assistant) **[Karma'Exchange için kullanılır](/exchange/hybrid-configuration-wizard)** <p> Not: Bu uç noktalar yalnızca karma yapılandırma için Exchange gerekir|domains.live.com 2010 SP3 Karma Yapılandırma Sihirbazı & 443 tcp Exchange üzerinde bağlantı noktaları <p> GCC Yüksek, DoD IP adresleri: 40.118.209.192/32; 168.62.190.41/32 <p> Dünya Çapında ticari & GCC: \*.store.core.windows.net; asl.configure.office.com; tds.configure.office.com; mshybridservice.trafficmanager.net ; <br> aka.ms/hybridwizard; <br> \*shcwreleaseprod.blob.core.windows.net/shcw/;|Giden sunucuya yalnızca trafik|
|10|Otomatik **Algılama hizmeti,** iOS ve Android [Exchange](/exchange/exchange-deployment-assistant) Karma Modern Kimlik Doğrulaması ile karma Outlook [senaryolarda kullanılır](/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) <p> `*.acompli.net` <br> `*.outlookmobile.com` <br> `*.outlookmobile.us` <br> `52.125.128.0/20` <br> `52.127.96.0/23`|TCP 443'Exchange müşteri şirket içi kimlik sunucusu|Gelen sunucu trafiği|
|11|**Exchange Azure AD kimlik doğrulamasını yapılandırma**|*.msappproxy.net|TCP giden sunucuya yalnızca trafik|
|12|Skype Kurumsal 2016'Office, UDP bağlantı noktalarını **kullanan video** tabanlı ekran paylaşımı içerir. Daha Skype Kurumsal 2013'Office daha önceki sürümlerde TCP bağlantı noktası 443 üzerinden RDP kullanılıyordu.|TCP bağlantı noktası 443, 52.112.0.0/14 olarak açılır|Skype Kurumsal 2013 ve önceki Office daha eski istemci sürümleri|
|13|**Skype Kurumsal Online'a karma şirket içi sunucu** Skype Kurumsal bağlantı sağlar|13.107.64.0/18, 52.112.0.0/14 <br> UDP bağlantı noktaları 50.000-59.999 <br> TCP bağlantı noktaları 50.000-59.999; 5061|Skype Kurumsal sunucu giden bağlantı sorunlarını yapılandırma|
|14|**Şirket içi karma** bağlantısı olan bulut PSTN, şirket içi ana bilgisayarlarına açık ağ bağlantısı gerektirir. Çevrimiçi karma yapılandırmaları hakkında daha Skype Kurumsal fazla bilgi için|Bkz[. Iki alan arasında karma Skype Kurumsal Sunucu planlama Office 365](/skypeforbusiness/hybrid/plan-hybrid-connectivity)|Skype Kurumsal karma gelen|
|15|**Kimlik doğrulama ve kimlik FQDN'leri** <p> FQDN'nin `secure.aadcdn.microsoftonline-p.com` çalışması için istemcinizin Internet Explorer (IE) veya Edge Güvenilen Siteler Bölgesi'nde olması gerekir.||Güvenilen Siteler|
|16|**Microsoft Teams FQDN'leri** <p> Internet Explorer veya Microsoft Edge kullanıyorsanız, birinci ve üçüncü taraf tanımlama bilgilerini etkinleştirmeniz ve güvenilen siteleriniz için FQDN'leri Teams eklemeniz gerekir. Bu, satır 14'te listelenen paket genelindeki FQDN'ler, CDN'ler ve telemetriye ek olarak bulunmaktadır. Daha [fazla bilgi için Microsoft Teams](/microsoftteams/known-issues) sorunları'ne bakın.||Güvenilen Siteler|
|17|**SharePoint Online ve OneDrive İş FQDN'leri** <p> FQDN'sharepoint.com\<tenant\> '' olan tüm '.sharepoint.com' FQDN'lerinin çalışması için istemcinizin IE'sinde veya Edge Güvenilen Siteler Bölgesi'nde olması gerekir. Satır 14'te listelenen paket genelindeki FQDN2ler, CDN'ler ve telemetriye ek olarak bu uç noktaları da eklemeniz gerekir.||Güvenilen Siteler|
|18|**Yammer**  <br> Yammer tarayıcıda kullanılabilir ve kimliği doğrulanmış kullanıcının bir proxy aracılığıyla geçirileni gerektirir. Tüm Yammer FQDN'lerinin çalışması için istemcinizin IE'sinde veya Edge Güvenilen Siteler Bölgesi'nde olması gerekir.||Güvenilen Siteler|
|19|Şirket **[içi kullanıcı Bağlan](/azure/active-directory/hybrid/)** Azure AD'ye eşitlemek için Azure AD Bağlan'i kullanın.|Karma [Kimlik Gerekli Bağlantı Noktaları ve Protokoller,](/azure/active-directory/hybrid/reference-connect-ports) [Azure AD bağlantısı sorunlarını](/azure/active-directory/hybrid/tshoot-connect-connectivity) giderme ve [Azure AD kimlik Bağlan Yüklemesi'ne bakın](/azure/active-directory/hybrid/how-to-connect-health-agent-install#outbound-connectivity-to-the-azure-service-endpoints).|Giden sunucuya yalnızca trafik|
|20|**[Şirket içi Bağlan](/azure/active-directory/hybrid/)** Azure AD ile eşitlemek için Azure AD, Çin'de 21 ViaNet ile birlikte kullanılabilir.|\*.digicert.com:80 <BR> \*.entrust.net:80 <BR> \*.chinacloudapi.cn:443 <br> secure.aadcdn.partner.microsoftonline-p.cn:443 <br> \*.partner.microsoftonline.cn:443 <p> Ayrıca bkz [. Azure AD bağlantı sorunlarını giderme](https://docs.azure.cn/zh-cn/active-directory/hybrid/tshoot-connect-connectivity).|Giden sunucuya yalnızca trafik|
|21|**Microsoft Stream** (Azure AD kullanıcı belirteci gerekir). <br> Office 365 Dünya Çapında (GCC)|\*.cloudapp.net <br> \*.api.microsoftstream.com <br> \*.notification.api.microsoftstream.com <br> amp.azure.net <br> api.microsoftstream.com <br> az416426.vo.msecnd.net <br> s0.assets-yammer.com <br> vortex.data.microsoft.com <br> web.microsoftstream.com <br> TCP bağlantı noktası 443|Gelen sunucu trafiği|
|22|Çok **faktörlü kimlik doğrulama** istekleri için, hem sunucunun yeni yüklemeleri hem de Active Directory Etki Alanı Hizmetleri (AD DS) ile kurulumu için MFA sunucusunu kullanın.|Bkz [. Azure AD Multi-Factor Authentication Server'la çalışmaya başlama](/azure/active-directory/authentication/howto-mfaserver-deploy#plan-your-deployment).|Giden sunucuya yalnızca trafik|
|23|**Microsoft Graph BildirimLerini Değiştir** <p> Geliştiriciler, Microsoft [Web Sitesinde etkinliklere](/graph/webhooks?context=graph%2fapi%2f1.0&view=graph-rest-1.0) abone olmak için değişiklik bildirimlerini Graph.|Public Cloud: 52.159.23.209, 52.159.17.84, 52.147.213.251, 52.147.213.181, 13.85.192.59, 13.85.192.123, 13.89.108.233, 13.89.104.147, 20.96.21.67, 20.69.245.215, 137.135.11.161, 137.135.11.116, 52.159.107.50, 52.159.107.4, 52.229.38.131, 52.183.67.212, 52.142.114.29, 52.142.115.31, 51.124.75.43, 51.124.73.177, 20.44.210.83, 20.44.210.146, 40.80.232.177, 40.80.232.118, 20.48.12.75, 20.48.11.201, 104.215.13.23, 104.215.6.169, 52.148.24.136, 52.148.27.39, 40.76.162.99, 40.76.162.42 , 40.74.203.28, 40.74.203.27, 13.86.37.15, 52.154.246.238, 20.96.21.98, 20.96.21.115, 137.135.11.222, 137.135.11.250, 52.159.109.205, 52.159.102.72, 52.151.30.78, 52.191.173.85, 51.104.159.213, 51.104.159.181, 51.138.90.7, 51.138.90.52, 52.148.115.48, 52.148.114.238, 40.80.233.14, 40.80.239.196, 20.48.14.35, 20.48.15.147, 104.215.18.55, 104.215.12.254, 20.199.102.157, 20.199.102.73, 13.87.81.123, 13.87.81.35, 20.111.9.46, 20.111.9.77, 13.87.81.133, 13.87.81.141 <p> Microsoft Cloud for US Government: 52.244.33.45, 52.244.35.174, 52.243.157.104, 52.243.157.105, 52.182.25.254, 52.182.25.110, 52.181.25.67, 52.181.25.66, 52.244.111.156, 52.244.111.170, 52.243.147.249, 52.243.148.19, 52.182.32.51, 52.182.32.143, 52.181.24.199, 52.181.24.220 <p> 21Vianet tarafından işletilen Microsoft Bulut Çin: 42.159.72.35, 42.159.72.47, 42.159.180.55, 42.159.180.56, 40.125.138.23, 40.125.136.69, 40.72.155.199, 40.72.155.216 <br> TCP bağlantı noktası 443 <p> Not: Geliştiriciler abonelikleri oluştururken farklı bağlantı noktaları belirtebilirsiniz.|Gelen sunucu trafiği|
|24|**Ağ Bağlantısı Durum Göstergesi**<p>Windows 10 ve 11 tarafından, bilgisayarın İnternet'e bağlı olup olmadığını belirlemek için kullanılır (İnternet'e bağlı olmayan Windows değildir). Bu URL'ye ulaşılamadıktan sonra, Windows İnternet'e bağlı olmadığını varsayacak ve Enterprise için M365 Uygulamaları etkinleştirme durumunu doğrulamaya çalışmayacak, bu nedenle Exchange ve diğer hizmetlere bağlantıların başarısız olmasına neden olur.|www.mstfconnecttest.com <br> 13.107.4.52<p>Ayrıca bkz[. Windows 11](/windows/privacy/manage-windows-11-endpoints) için bağlantı uç Enterprise ve [Windows 10 Enterprise 21H2 için bağlantı uç noktalarını yönetme](/windows/privacy/manage-windows-21h2-endpoints).|Giden sunucuya yalnızca trafik|
|

## <a name="related-topics"></a>İlgili Konular

[Kullanıcı Office 365 yönetme](managing-office-365-endpoints.md)
  
[Ekran Microsoft 365 izleme](./monitor-connectivity.md)
  
[İstemci bağlantısı](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[İçerik teslim ağları](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Azure IP Aralıkları ve Hizmet Etiketleri – Genel Bulut](https://www.microsoft.com/download/details.aspx?id=56519)

[Azure IP Aralıkları ve Hizmet Etiketleri – ABD Kamu Bulutu](https://www.microsoft.com/download/details.aspx?id=57063)

[Azure IP Aralıkları ve Hizmet Etiketleri – Almanya Bulut](https://www.microsoft.com/download/details.aspx?id=57064)

[Azure IP Aralıkları ve Hizmet Etiketleri – Çin Bulutu](https://www.microsoft.com/download/details.aspx?id=57062)
  
[Microsoft Genel IP Alanı](https://www.microsoft.com/download/details.aspx?id=53602)
