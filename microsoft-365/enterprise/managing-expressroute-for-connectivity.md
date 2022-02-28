---
title: Daha fazla bağlantı için ExpressRoute Office 365 yönetme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
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
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: Ön ek filtreleme, güvenlik ve uyumluluk Office 365 ortak alanlar da dahil olmak üzere, e-posta için ExpressRoute'u yönetmeyi öğrenin.
ms.openlocfilehash: bffe82249a9d8a531ee85525f9db0eb38a344d50
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985578"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Daha fazla bağlantı için ExpressRoute Office 365 yönetme

İnternet için ExpressRoute Office 365 tüm trafiğin İnternet'e çıkışa gerek kalmadan birçok Office 365 hizmetine ulaşmak için alternatif bir yol sunar. Office 365'a İnternet bağlantısı yine gerekli olsa da, Microsoft'un ağınıza BGP aracılığıyla tanıt ettiği belirli yollar, ağ üzerinde başka yapılandırmalar olmadığı sürece doğrudan ExpressRoute devresini tercih edilen yol olur. Bu yönlendirmeyi yönetmek için yapılandırmak istemeniz gereken üç ortak alan önek filtreleme, güvenlik ve uyumluluktır.
  
> [!NOTE]
> Microsoft, Azure ExpressRoute için Microsoft Eşleme yönlendirme etki alanının gözden geçirme şeklinde değişiklik yaptı. 31 Temmuz 2017'den itibaren, tüm Azure ExpressRoute müşterileri Microsoft Eşliği'yi doğrudan Azure Yönetim konsolundan veya PowerShell aracılığıyla etkinleştirilebilir. Microsoft Eşleme'yi etkinleştirdikten sonra, herhangi bir müşteri Dynamics 365 Müşteri Katılımı uygulamalarına (Eski adıyla CRM Online) yönelik BGP yol tanıtımları almak için rota filtreleri oluşturabilir. İş için Azure ExpressRoute'a Office 365 müşterilerin, projeniz için rota filtreleri oluşturamadan önce Microsoft'tan inceleme Office 365. ExpressRoute'u etkinleştirme hakkında inceleme talep etmeyi öğrenmek için lütfen Microsoft Office 365 geçin. E-posta için rota filtreleri oluşturmaya çalışan yetkisiz Office 365, bir [hata iletisi alır](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>Önek filtreleme

Microsoft, müşterilerin Microsoft'tan tanıt verilen tüm BGP yollarını kabul etmelerini önermektedir. Sağlanan yollar, ek incelemenin tüm avantajlarını ortadan kaldıracak şekilde sıkı bir inceleme ve doğrulama sürecinden geçirilmez. ExpressRoute IP önek sahipliği, bütünlük ve ölçek (müşteri tarafında gelen yol filtrelemesi yok) gibi önerilen denetimleri yerel olarak sunar.
  
ExpressRoute genel eşliği genelinde yönlendirme sahipliğinin ek doğrulanmasına gerek ediyorsanız, tanıtan yönlendirmeleri [, Microsoft'un genel IP](https://www.microsoft.com/download/details.aspx?id=53602) aralıklarını temsil eden tüm IPv4 ve IPv6 IP ön ekleri listesine göre kontrol edin. Bu aralıklar Microsoft'un tüm adres alanını içerir ve seyrek olarak değişir ve Microsoft'a ait olmayan yolların ortamına sızdırma konusunda kaygılanılan müşterilere ek koruma sağlamak için filtreyi sağlayan güvenilir bir aralık kümesi sağlar. Değişiklik olması durumunda ayın 1'inde yapılır ve dosya her güncelleştirildiğinde sayfanın ayrıntılar bölümündeki sürüm numarası değişir.
  
Çeşitli nedenlerle, önek filtre listeleri oluşturmak için [Office 365 URL'leri ve IP](./urls-and-ip-address-ranges.md) adresi aralıklarını kullanabilirsiniz. Aşağıdakiler de dahil:
  
- Bu Office 365 IP ön ekleri sık sık birçok değişiklik yapılır.

- En Office 365 URL'ler ve IP adresi aralıkları yönlendirmeyi değil güvenlik duvarı izin listeleri ve Ara Sunucu altyapısını yönetmek için tasarlanmıştır.

- Hızlı Office 365 URL'leri ve IP adresi aralıkları, ExpressRoute bağlantı Microsoft hizmetleri kapsamına sahip olan diğer bağlantıları kapsıyor olabilir.

|**Seçenek**|**Karmaşıklık**|**Değişiklik Denetimi**|
|:-----|:-----|:-----|
|Tüm Microsoft yollarını kabul et  <br/> |**Düşük:** Müşteri, tüm yolların düzgün şekilde sahip olmasını sağlamak için Microsoft denetimlerine güvenmektedir.  <br/> |Yok  <br/> |
|Microsoft'a ait süper anet'leri filtrele  <br/> |**Orta:** Müşteri, Microsoft'a ait yollara izin vermek için özetlenmiş ön ek filtresi listeleri ekler.  <br/> |Müşteriler seyrek güncelleştirmelerin yol filtrelerine yansıtlı olduğundan emin olmalı.  <br/> |
|IP Office 365 filtreleme  <br/> [!CAUTION] Not-Recommended |**Yüksek:** Müşteri, IP ön eklerine tanımlı Office 365 göre yolları filtreler.  <br/> |Müşterilerin aylık güncelleştirmeler için güçlü bir değişiklik yönetim süreci uygulaması gerekir.  <br/> [!CAUTION] Bu çözüm için önemli ölçüde, devaman değişiklikler gerekir. Zamanında uygulanmamış olan değişiklikler hizmet kesintisi ile sonuçlanmayacaktır.   |

Azure ExpressRoute Office 365 bağlantıda, uç noktaların dağıtıldı olduğu ağları temsil eden belirli IP alt ağlarının BGP tanıtımları temel Office 365 bağlanır. Web sitelerinin genel doğası gereği Office 365 ve bunu Office 365 hizmetlerin sayısından dolayı, müşterilerin çoğunlukla ağlarında kabul edilen tanıtımları yönetmeleri gerekir. Ortamınıza tanıtacak sayıda ön ek konusunda endişeleriniz varsa, [BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) topluluk özelliği belirli bir hizmet kümesi tanıtımlarını filtrelemenize Office 365 sağlar. Bu özellik şu anda önizlemede.
  
Microsoft'tan gelen BGP yol tanıtımlarını nasıl yönetirsiniz, Office 365'a tek başına İnternet devresi üzerinden bağlanmaya göre Office 365 hizmetlerinde özel bir açıklandırma elde etmeysiniz. Microsoft, müşterinin Microsoft'a bağlanmak için kullandığı devre türüne bakılmaksızın aynı güvenlik, uyumluluk ve performans düzeylerini Office 365.
  
### <a name="security"></a>Güvenlik

Microsoft, expressRoute genel ve Microsoft eşliği arasında gidip gelen ve gelen ve gelen bağlantılarda kendi ağ ve güvenlik çevresi denetimlerinizi korumanızı önermektedir. Bu denetimler, Office 365 içerir. Hem ağınız dışından Microsoft'un ağına hem de Microsoft'un ağına giden ağ istekleri için güvenlik denetimlerinin yerinde olması gerekir.
  
#### <a name="outbound-from-customer-to-microsoft"></a>Müşteriden Microsoft'a Giden
  
Bilgisayarlar İnternet veya Office 365 bağlantı ister ExpressRoute devresi üzerinden yapılmış olsun, aynı uç nokta kümesine bağlanıyor olmalıdır. Kullanılan devreden bağımsız olarak, Microsoft hizmetleri genel İnternet hedeflerinden Office 365 daha güvenilir olarak kabul ediyorum. Açık kalma süresini azaltmak ve sürekli bakım süresini en aza indirmek için, giden güvenlik denetimleriniz bağlantı noktalarına ve protokollere odaklanın. Gerekli bağlantı noktası bilgileri, Office 365 [noktaları başvuru makalesinde](./urls-and-ip-address-ranges.md) mevcuttur.
  
Ek denetimler için, İnternet'i veya İnternet'i ya da İnternet'i veya diğer tüm istekleri kısıtlamak veya incelemek için ara sunucu altyapınız içinde FQDN düzeyi filtrelemeyi Office 365. Özellikler yayınlanır ve yeni özellikler geliştikçe FQDN'ler listesini korumak için, Office 365 teklifleri geliştikçe daha güçlü bir değişiklik yönetimi ve yayımlanan Office 365 [gerektirir](./urls-and-ip-address-ranges.md).
  
> [!CAUTION]
> Microsoft, yalnızca IP ön eklerine güvenerek, iş yerlerinden giden bağlantı güvenliğini Office 365.

|**Seçenek**|**Karmaşıklık**|**Değişiklik Denetimi**|
|:-----|:-----|:-----|
|Kısıtlama yok  <br/> |**Düşük:** Müşteri, Microsoft'a sınırsız giden bağlantı erişimine izin verir.  <br/> |Yok  <br/> |
|Bağlantı noktası kısıtlamaları  <br/> |**Düşük:** Müşteri, Microsoft'a giden bağlantı erişimini beklenen bağlantı noktalarıyla kısıtlar.  <br/> |Seyrek.  <br/> |
|FQDN kısıtlamaları  <br/> |**Yüksek:** Müşteri, posta veritabanına giden Office 365 yayımlanmış FQDN'lere dayanarak kısıtlar.  <br/> |Aylık değişiklikler.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>Microsoft'tan Müşteriye Gelen
  
Microsoft'un ağınıza bağlantı başlatması gereken, isteğe bağlı birkaç senaryo vardır.
  
- Oturum açma için parola doğrulaması sırasında ADFS.

- [Exchange Server dağıtımları yapılandırma](/exchange/exchange-hybrid).

- Bir Exchange Online kiracıdan şirket içi ana bilgisayara posta.

- SharePoint Online'dan şirket SharePoint ana bilgisayara gönderebilirsiniz.

- [SharePoint karma arama sonuçları.](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online)

- [SharePoint BCS.](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution)

- [Skype Kurumsal ve](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json)/veya karma [Skype Kurumsal olabilir](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).

- [Skype Kurumsal Cloud Connector' seçin](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

Microsoft, karmaşıklığı azaltmak için bu bağlantıları ExpressRoute devreniz yerine İnternet devreniz üzerinden kabul etmenizi öneririz. Uyumluluk veya performans ihtiyaçlarını karşılarsanız, bu gelen bağlantıların ExpressRoute devresi üzerinden kabul edilmeleri gerekir; kabul edilen bağlantıların kapsamını belirlemesi için güvenlik duvarı veya ters ara sunucu kullanılması önerilir. Doğru [FQDN'leri ve](./urls-and-ip-address-ranges.md) IP ön eklerini Office 365 uç noktalarını kullanabilirsiniz.
  
### <a name="compliance"></a>Uyumluluk

Uyumluluk denetimlerimizin hiçbiri için, hangi yönlendirme yolunu kullanıyor oluruz? ExpressRoute veya İnternet devresi üzerinden Office 365 hizmetlere bağlanmanıza bakılmaksızın, uyumluluk denetimlerimiz değişmez. Kuruluş ihtiyaçlarını en iyi şekilde karşılamak için, Office 365 uyumluluk ve güvenlik sertifikası düzeylerini gözden geçirebilirsiniz.
  
İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/manageexpressroute365]()
  
## <a name="related-topics"></a>İlgili konular

[İçerik teslim ağları](content-delivery-networks.md)
  
[Office 365 URL'leri ve IP adresi aralıkları](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Kullanıcı Office 365 yönetme](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 için Azure ExpressRoute Eğitimi](https://channel9.msdn.com/series/aer)