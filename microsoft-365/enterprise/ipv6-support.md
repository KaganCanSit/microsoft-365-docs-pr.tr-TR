---
title: Microsoft 365 hizmetlerde IPv6 desteği
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/03/2021
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'Özet: Microsoft 365 bileşenlerinde ve Microsoft 365 için IPv6 desteğini açıklar.'
ms.openlocfilehash: a6a2e11ff2e312c02f10d152fe580bdead5fa7c9
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996563"
---
# <a name="ipv6-support-in-microsoft-365-services"></a>Microsoft 365 hizmetlerde IPv6 desteği

Microsoft 365 hem IPv6'yı hem de IPv4'ü destekler; bununla birlikte, Microsoft 365 özellikleri IPv6 ile tam olarak etkinleştirilmez. Bu, aynı adrese bağlanmak için hem IPv4 hem de IPv6 Microsoft 365. Microsoft 365'a giden trafiğinizi filtre Microsoft 365, MICROSOFT 365 tarafından desteklenen IPv6 adreslerinin tam listesi, MICROSOFT 365 ve [IP adresi aralıkları makalesinde bulunabilir](urls-and-ip-address-ranges.md). Ağınız yapılandırıldığında ve uygun IPv6 adreslerine izin verildikten sonra, Microsoft İndirme [Merkezi'nden Microsoft 365 IPv6 test planını](https://go.microsoft.com/fwlink/?LinkId=293447) indirebilirsiniz.

> [!NOTE]
> Müşterilerin herhangi bir konumdan Microsoft 365 SaaS hizmetlerini deneyimleymelerini sağlamak, Microsoft için bir önceliktir. Bu, müşterilerin IPv6 etkin Microsoft 365 ve IPv6 istemcilerinden ve bilgi sistemlerinden veri bağlamasına ve bu sistemlerden tüketilmesine olanak vermeyi kapsar. Ayrıca, kamu müşterilerinin ağlarında IPv6 taahhütlerini karşılamalarını sağlarken, kesintisiz üretkenlik senaryolarını Microsoft 365 devam eder.  
> Bu makalede, bugün doğrudan IPv6 Microsoft 365 SaaS hizmetlerinin listesini bulabilirsiniz. Doğrudan IPv6 bağlantısına izin veren hizmetlerin kapsamının genişletilene kadar devam olması bekmektedir. Microsoft 365 IPv6 desteği için açıkça bahsed Azure Active Directory (AAD) Kimlik Doğrulama hizmetlerini eklemek için, DNS64/NAT64'un yalnızca IPv6 istemcilerinden ve ortamlarından bağlanmasını gerektiren kabul edilir.  Bu, şu anda var olan NIST USGv6 belgelerinde ana hatları verilen amaçla aynı hizadadır: [NIST Özel Yayını 500-267A Düzeltme 1](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.500-267Ar1.pdf) NAT64/DNS64'te Geçiş Mekanizması Özellik Gereksinimleri, değiştirilebilir teknolojilerdir.
> - Geçiş mekanizması NAT64 [RFC6146](https://datatracker.ietf.org/doc/html/rfc6146) Stateful NAT64 için NAT64 desteği: IPv6 İstemcilerinden IPv4 Sunucularına Ağ Adresi ve Protokol Çevirisi
> - Geçiş mekanizması DNS64 için DNS64 desteği. [RFC6147](https://datatracker.ietf.org/doc/html/rfc6147) DNS64: IPv6 İstemcilerinden IPv4 Server'a Ağ Adresi Çevirisi için DNS Uzantıları

  
## <a name="ipv6-support-in-microsoft-365-subscription-service"></a>Microsoft 365 aboneliği Microsoft 365 IPv6 desteği

### <a name="exchange-online-and-ipv6"></a>Exchange Online ve IPv6

Exchange Online'a bağlanmak için kullanılan program IPv6'yı destekliyorsa, hem kablolu hem kablosuz ağlarda varsayılan olarak IPv6'yı kullanır. Bu iletişimleri kontrol etmek Exchange Online, URL'ler ve IP adresi [aralıkları Microsoft 365 IP adresi aralıklarını kullanın](urls-and-ip-address-ranges.md).
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online ve IPv6

 **Microsoft 365 Kamu G1/G3/G4/K1** SharePoint Online'a bağlanmak için kullanılan program IPv6'yı destekliyorsa, varsayılan olarak IPv6'yı kullanmayı dener.
  
 **Genel çok kiracılı bulut** Microsoft, SharePoint Online IPv6'yı yeniden sağlar. Kuruluş DNS altyapısı için CIDR ile ilgili IP adreslerini sağlamış oluruz. Kiracınız için IPv6'nın etkinleştirilmesi için başka kuruluşlar tarafından bu DNS altyapısının paylaşılana olmadığını unutmayın. IPv6 etkinleştirildikten sonra, SharePoint Online'a bağlanmak için kullanılan program IPv6'yı destekliyorsa, varsayılan olarak IPv6'yı kullanır.
  
SharePoint Online'a bağlanmak için kullanılan program IPv6'yı destekliyorsa, hem kablolu hem kablosuz ağlarda varsayılan olarak IPv6'yı kullanır. SharePoint Online ile iletişimi kontrol etmek SharePoint, URL'ler ve IP adresi [aralıkları Microsoft 365 IP adresi aralıklarını kullanın](urls-and-ip-address-ranges.md).
  
 
  
### <a name="skype-for-business-and-ipv6"></a>Skype Kurumsal ve IPv6

Lütfen IPv6'nın E-Skype Kurumsal artık etkinleştirile olmadığını unutmayın.

### <a name="microsoft-teams-sip-gateway-and-ipv6"></a>Microsoft Teams, SIP Ağ Geçidi ve IPV6

Microsoft Teams Yönlendirme ve SIP Ağ Geçidi yalnızca IPv4'ü destekler. En Microsoft Teams hizmeti ve istemci hem IPv4'ü hem de IPv6'yı destekler. Bu iletişimleri kontrol etmek Microsoft Teams, URL'ler ve IP [adresi aralıkları Microsoft 365 IP adresi aralıklarını kullanın](urls-and-ip-address-ranges.md).
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection ve IPv6

Exchange Online Protection aktarım Aktarım Katmanı Güvenliği Protokolü üzerinden gerçekleşirse, bu iletim (EOP) IPv6'yı destekler. EOP aralığı için, [URL'Microsoft 365 IP adresi aralıklarını kullanın](urls-and-ip-address-ranges.md).
  
### <a name="ipv6-support-for-microsoft-365-government-offerings"></a>Kamu teklifleri için IPv6 Microsoft 365 desteği

Microsoft 365 tekliflerinin IPv6 desteği, Yönetim Departmanları ve Kuruluşları'nın Genel Bilgi Sorumluları için Office Yönetim ve Bütçe (OMB) Genel Müdürü geneline ve ayrıca Federal Yönetim İnternet Protokolü Sürüm 6'nın (IPv6) Benimsenmesi geneline uygun olur. [Microsoft Microsoft 365 Kamu için Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=325414), ABD kamu verilerini ayrı bir topluluk bulutunda depolana kadar çok kiracılı bir hizmettir. Diğer Microsoft 365 gibi, Exchange Online, Skype Kurumsal, SharePoint Online ve diğer hizmetler de dahil olmak üzere üretkenlik ve işbirliği Kurumlar için Microsoft 365 Uygulamaları. 

Microsoft Microsoft 365 teklifleri yalnızca 2013 ve sonrası için geçerlidir. Kamu teklifleri hakkında daha fazla Microsoft 365 için bkz. Kamu için [Microsoft 365: ABD'de bir Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). Uluslararası Kollarının Trafiği Düzenlemeleri (ITAR), ABD devletinin Amerika Birleşik Devletleri Birleşik Devletler [Munitions Listesi'nde (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415) savunmayla ilgili makalelerin ve hizmetlerin ihracat ve içeri aktarmasını kontrol altına alan bir dizi yasal düzenlemedir. 

Kuruluşlar için Microsoft Microsoft 365, Microsoft üretkenlik çözümleri için Federal Bilgi Güvenliği Yönetimi (FISMA) sertifikası gerektiren ABD federal kuruluşları ve ITAR'a tabi olan ticari varlıklar için güvenlik, gizlilik ve yasal düzenlemelere uyumluluk gereksinimlerini destekleyen özel barındırma hizmetleri sağlar.
  
## <a name="things-to-consider-when-using-ipv6-and-microsoft-365"></a>IPv6 ve Microsoft 365

IPv6'yı devre dışı bırakmamanızı öneririz. Daha fazla bilgi için bu kılavuz [makalesine bakın](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users). Ağ üzerinde hangi IP sürümlerinin kullanılıyor olduğunu belirlemek için, aşağıdaki göz önünde yapın:
  
- Komut isteminde **IPConfig** komutunun görüntüsü "IPv6 Address" veya "Temporary IPv6 Address" adlı satırlar içeriyorsa, ortamında IPv6 vardır.

- Tüm IPv6 adresleri "fe80" ile başlıyorsa ve "Link-Local IPv6 Address" satırlarına karşılık başlıyorsa, ortamınızı IPv6'nız yokdur.

Bu noktalar ağınız için geçerli olabilir:
  
- Genel abonelik hizmeti, IPv6 üzerinden kredi kartıyla satın alma işlevini desteklemez. Bu durum diğer iki Government Community Cloud (GCC) için geçerli değildir, çünkü devletlerin Kurumsal Anlaşma lisansı satın almaları gerektir.

- IPv6 bazı Rights Management Services (RMS) senaryolarını desteklemez.

- IPv6 BlackBerry® Enterprise Server'da (BES) desteklemez, çünkü BlackBerry IPv6'yı desteklemez.

- Microsoft 365'da Active Directory Federasyon Hizmetleri (AD FS) kullanıyorsanız, AD FS ağ uç Microsoft 365 IPv6 kullanarak reklam ekleme desteklemektedir. Bu özellikleri kullanırken AD FS DNS girişine AAAA kayıtlarını Exchange Online. 

İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/o365ip6]()

## <a name="see-also"></a>Ayrıca bkz.

[IPv6 Learning Yol Haritası](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[IPv6 Sağ Kalma Kılavuzu](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
