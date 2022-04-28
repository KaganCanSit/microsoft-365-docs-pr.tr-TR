---
title: Microsoft 365 hizmetlerinde IPv6 desteği
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Özet: Microsoft 365 bileşenlerinde ve Microsoft 365 kamu tekliflerinde IPv6 desteğini açıklar.'
ms.openlocfilehash: 6cd53b71c6e15346d4940c539eea4aff0e5a613e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096490"
---
# <a name="ipv6-support-in-microsoft-365-services"></a>Microsoft 365 hizmetlerinde IPv6 desteği

Microsoft 365 hem IPv6 hem de IPv4'i destekler; ancak tüm Microsoft 365 özellikleri IPv6 ile tam olarak etkinleştirilmez. Bu, Microsoft 365 bağlanmak için hem IPv4 hem de IPv6 kullanmanız gerektiği anlamına gelir. Giden trafiğinizi Microsoft 365 filtrelediyseniz, Microsoft 365 tarafından desteklenen IPv6 adreslerinin tam listesi [URL'ler ve IP adresi aralıkları Microsoft 365](urls-and-ip-address-ranges.md) makalesinde bulunabilir. Ağınız yapılandırıldıktan ve uygun IPv6 adreslerine izin verildikten sonra, [Microsoft 365 IPv6 test planını](https://go.microsoft.com/fwlink/?LinkId=293447) Microsoft İndirme Merkezi'nden indirebilirsiniz.

> [!NOTE]
> Müşterilerin Microsoft 365 SaaS hizmetlerini herhangi bir konumdan ve herhangi bir cihazdan deneyimlemelerini sağlamak Microsoft için bir önceliktir. Bu, müşterilerin yalnızca IPv6 etkin ve IPv6 istemcilerinden ve bilgi sistemlerinden Microsoft 365 bağlanmasına ve kullanmasına olanak sağlamayı içerir. Ayrıca kamu müşterilerinin ağlarında IPv6 taahhütlerini yerine getirmesini sağlarken Microsoft 365 üretkenlik senaryolarını kesintisiz kullanmaya devam etmelerini de içerir.  
> Bu makalede, bugün doğrudan IPv6 bağlantısına izin veren Microsoft 365 SaaS hizmetlerinin listesi sağlanır. Doğrudan IPv6 bağlantısına izin veren hizmetlerin kapsamının genişlemeye devam etmesi beklenir. doğrudan IPv6 desteği için açıkça belirtilmeyen Microsoft 365 hizmetleri, Azure Active Directory (AAD) Kimlik Doğrulama hizmetlerini dahil etmek için, yalnızca IPv6 istemcilerinden ve ortamlarından dns64/NAT64'e bağlanılmasının gerekli olduğu kabul edilmelidir.  Bu, şu anda mevcut NIST USGv6 belgelerinde belirtilen amaca uygundur: [NIST Özel Yayını 500-267A Düzeltme 1 NAT64](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.500-267Ar1.pdf) /DNS64'teki Geçiş Mekanizması Yetenek Gereksinimleri, kullanıma uygun teknolojilerdir.
> - GEÇIŞ mekanizması NAT64 [RFC6146](https://datatracker.ietf.org/doc/html/rfc6146) Durum bilgisi olan NAT64 için NAT64 desteği: IPv6 İstemcilerinden IPv4 Sunucularına Ağ Adresi ve Protokol Çevirisi
> - DNS64 geçiş mekanizması DNS64 desteği. [RFC6147](https://datatracker.ietf.org/doc/html/rfc6147) DNS64: IPv6 İstemcilerinden IPv4 Sunucusuna Ağ Adresi Çevirisi için DNS Uzantıları

  
## <a name="ipv6-support-in-microsoft-365-subscription-service"></a>Microsoft 365 abonelik hizmetinde IPv6 desteği

### <a name="exchange-online-and-ipv6"></a>Exchange Online ve IPv6

Exchange Online bağlanmak için kullandığınız program IPv6'yı destekliyorsa, hem kablolu hem de kablosuz ağlarda varsayılan olarak IPv6 kullanır. Exchange Online iletişimini denetlemek istiyorsanız, [Microsoft 365 URL'leri ve IP adresi aralıklarındaki IP adresi aralıklarını](urls-and-ip-address-ranges.md) kullanın.
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online ve IPv6

 **Microsoft 365 Kamu G1/G3/G4/K1** SharePoint Online'a bağlanmak için kullandığınız program IPv6'yı destekliyorsa, varsayılan olarak IPv6'yı kullanmayı dener.
  
 **Genel çok kiracılı bulut** Microsoft, isteğiniz üzerine SharePoint Çevrimiçi IPv6'ya olanak tanır. Kuruluşunuzun DNS altyapısı için CIDR ile belirtilen IP adreslerini sağlamanız gerekir. Kiracınızda IPv6'nın etkinleştirilmesi için bu DNS altyapısının diğer kuruluşlar tarafından paylaşılabildiğini unutmayın. IPv6 etkinleştirildikten sonra, SharePoint Online'a bağlanmak için kullandığınız program IPv6'yı destekliyorsa, varsayılan olarak IPv6 kullanır.
  
SharePoint Online'a bağlanmak için kullandığınız program IPv6'yı destekliyorsa, hem kablolu hem de kablosuz ağlarda varsayılan olarak IPv6 kullanır. SharePoint Online ile iletişimleri denetlemek istiyorsanız, [Microsoft 365 URL'leri ve IP adresi aralıklarındaki IP adresi aralıklarını](urls-and-ip-address-ranges.md) kullanın.
  
 
  
### <a name="skype-for-business-and-ipv6"></a>Skype Kurumsal ve IPv6

IPv6'nın Skype Kurumsal'da desteklenmediğini ve artık etkinleştirilemediğini unutmayın.

### <a name="microsoft-teams-sip-gateway-and-ipv6"></a>Microsoft Teams, SIP Ağ Geçidi ve IPV6

Microsoft Teams Doğrudan Yönlendirme ve SIP Ağ Geçidi yalnızca IPv4'i destekler. Microsoft Teams hizmeti ve istemcisi hem IPv4 hem de IPv6'yi destekler. Microsoft Teams iletişimini denetlemek istiyorsanız, [Microsoft 365 URL'leri ve IP adresi aralıklarındaki IP adresi aralıklarını](urls-and-ip-address-ranges.md) kullanın.
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection ve IPv6

Exchange Online Protection (EOP), aktarım Aktarım Katmanı Güvenlik Protokolü üzerinden gerçekleşirse IPv6'yi destekler. EOP aralığı için [Microsoft 365 URL'leri ve IP adresi aralıklarını](urls-and-ip-address-ranges.md) kullanın.
  
### <a name="ipv6-support-for-microsoft-365-government-offerings"></a>Microsoft 365 kamu teklifleri için IPv6 desteği

kamu tekliflerine yönelik Microsoft 365 IPv6 desteği, Yönetim ve Bütçe (OMB) Office İdari Departmanlar ve Ajanslar için Enformasyon Başkanları muhtırasının yanı sıra Federal Hükümet İnternet Protokolü Sürüm 6 (IPv6) muhtırasını benimsemektedir. [Kamu için Microsoft Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=325414), ABD kamu verilerini ayrılmış bir topluluk bulutunda depolayan çok kiracılı bir hizmettir. Diğer Microsoft 365 tekliflerinde olduğu gibi, Exchange Online, Skype Kurumsal, SharePoint Online ve Kurumlar için Microsoft 365 Uygulamaları gibi üretkenlik ve işbirliği hizmetleri sağlar. 

Microsoft Microsoft 365 kamu teklifleri yalnızca 2013 ve üzeri için geçerlidir. Microsoft 365 kamu teklifleri hakkında daha fazla bilgi için bkz. [Kamu için Microsoft 365 Duyuru: ABD Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). Uluslararası Silah Trafiği Düzenlemeleri (ITAR), [Birleşik Devletler Mühimmat Listesi'ndeki (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415) savunmayla ilgili makalelerin ve hizmetlerin ihracatını ve ithalatını kontrol eden bir dizi ABD kamu düzenlemesidir. 

Kurumlar için Microsoft Microsoft 365, Federal Bilgi Güvenliği Yönetimi (FISMA) sertifikası ve ITAR'a tabi ticari varlıklar gerektiren ABD federal kurumları için güvenlik, gizlilik ve mevzuat uyumluluğu gereksinimlerini destekleyen Microsoft üretkenlik çözümleri için ayrılmış barındırma hizmetleri sağlar.
  
## <a name="things-to-consider-when-using-ipv6-and-microsoft-365"></a>IPv6 ve Microsoft 365 kullanırken dikkat edilmesi gerekenler

IPv6'yi devre dışı bırakmamanızı öneririz. Daha fazla bilgi için bu [kılavuz makalesine](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users) bakın. Ağınızda hangi IP sürümlerinin kullanıldığını belirlemek için aşağıdakileri göz önünde bulundurun:
  
- Komut isteminde **IPConfig** komutunun görüntüsü "IPv6 Adresi" veya "Geçici IPv6 Adresi" adlı satırlar içeriyorsa, ortamınızda IPv6 vardır.

- Tüm IPv6 adresleri "fe80" ile başlıyorsa ve "Bağlantı-Yerel IPv6 Adresi" adlı satırlara karşılık geliyorsa, ortamınızda IPv6 yoktur.

Bu noktalar ağınız için geçerli olabilir:
  
- Genel abonelik hizmeti, IPv6 üzerinden kredi kartıyla satın alma işlemini desteklemez. Devletler Kurumsal Anlaşma (EA) lisansına sahip olduğundan bu durum Government Community Cloud (GCC) için geçerli değildir.

- IPv6 bazı Rights Management Services (RMS) senaryolarını desteklemez.

- IPv6, BlackBerry® Enterprise Sunucusu'nu (BES) desteklemez çünkü BlackBerry IPv6'yi desteklemez.

- Microsoft 365 ile Active Directory Federasyon Hizmetleri (AD FS) (AD FS) kullanıyorsanız, AD FS ağ uç noktanızı IPv6 kullanarak Microsoft 365 için tanıtma desteklenmez. Exchange Online kullanırken AD FS DNS girdisine AAAA kayıtlarını eklememelisiniz. 

İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/o365ip6]()

## <a name="see-also"></a>Ayrıca bkz.

[IPv6 Learning Yol Haritası](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[IPv6 Hayatta Kalma Kılavuzu](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
