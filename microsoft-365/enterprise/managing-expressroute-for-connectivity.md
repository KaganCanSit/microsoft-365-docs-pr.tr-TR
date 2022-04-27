---
title: Office 365 bağlantısı için ExpressRoute'u yönetme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Ön ek filtreleme, güvenlik ve uyumluluk gibi yapılandırmaya yönelik ortak alanlar da dahil olmak üzere Office 365 için ExpressRoute'u yönetmeyi öğrenin.
ms.openlocfilehash: a601c047a7b8e19f02a728d00708689c795d5a64
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098328"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Office 365 bağlantısı için ExpressRoute'u yönetme

Office 365 için ExpressRoute, İnternet'e çıkış için tüm trafiğe gerek kalmadan birçok Office 365 hizmete ulaşmak için alternatif bir yönlendirme yolu sunar. Office 365 İnternet bağlantısı hala gerekli olsa da, Microsoft'un BGP aracılığıyla ağınıza tanıtdığı belirli yollar, ağınızda başka yapılandırmalar olmadığı sürece doğrudan ExpressRoute bağlantı hattını tercih eder. Bu yönlendirmeyi yönetmek için yapılandırmak isteyebileceğiniz üç ortak alan arasında ön ek filtreleme, güvenlik ve uyumluluk yer alır.
  
> [!NOTE]
> Microsoft, Microsoft Eşleme yönlendirme etki alanının Azure ExpressRoute için gözden geçirme şeklini değiştirdi. 31 Temmuz 2017'den itibaren tüm Azure ExpressRoute müşterileri Microsoft Eşleme'yi doğrudan Azure Yönetim konsolundan veya PowerShell aracılığıyla etkinleştirebilir. Microsoft Eşleme'yi etkinleştirdikten sonra, tüm müşteriler Dynamics 365 Customer Engagement uygulamaları (eski adı CRM Online) için BGP yol tanıtımlarını almak için rota filtreleri oluşturabilir. Office 365 için Azure ExpressRoute'a ihtiyaç duyan müşterilerin Office 365 için yol filtreleri oluşturabilmesi için önce Microsoft'tan gözden geçirmeleri gerekir. Office 365 ExpressRoute'u etkinleştirmek için gözden geçirme isteğinde bulunma hakkında bilgi edinmek için lütfen Microsoft Hesabı ekibinize başvurun. Office 365 için yol filtreleri oluşturmaya çalışan yetkisiz abonelikler [hata iletisi](https://support.microsoft.com/kb/3181709) alır
  
## <a name="prefix-filtering"></a>Ön ek filtreleme

Microsoft, müşterilerin Microsoft'tan tanıtıldığı gibi tüm BGP yollarını kabul etmelerini önerir. Sağlanan yollar ayrıntılı bir gözden geçirme ve doğrulama işleminden geçirilerek ek incelemenin tüm avantajları kaldırılır. ExpressRoute IP ön ek sahipliği, bütünlük ve ölçek gibi önerilen denetimleri yerel olarak sunar ve müşteri tarafında gelen yol filtrelemesi yoktur.
  
ExpressRoute genel eşlemesi genelinde yol sahipliğinin ek doğrulamasına ihtiyacınız varsa, tanıtılan yolları [Microsoft'un genel IP aralıklarını](https://www.microsoft.com/download/details.aspx?id=53602) temsil eden tüm IPv4 ve IPv6 IP ön ekleri listesinden de kontrol edebilirsiniz. Bu aralıklar, Microsoft'a ait olmayan yolların ortamlarına sızmasından endişe duyan müşterilere ek koruma sağlayan güvenilir bir filtre aralığı kümesi sağlayarak tam Microsoft adres alanını kapsar ve seyrek olarak değişir. Bir değişiklik olması durumunda ayın 1'inde yapılır ve dosyanın her güncelleştirilişinde sayfanın **ayrıntılar** bölümündeki sürüm numarası değişir.
  
Ön ek filtresi listeleri oluşturmak için [Office 365 URL'lerinin ve IP adresi aralıklarının](./urls-and-ip-address-ranges.md) kullanılmasını önlemenin çeşitli nedenleri vardır. Aşağıdakiler dahil:
  
- Office 365 IP ön ekleri sık sık birçok değişikliğe uğrar.

- Office 365 URL'leri ve IP adresi aralıkları, yönlendirmeyi değil güvenlik duvarı izin veren listeleri ve Ara Sunucu altyapısını yönetmek için tasarlanmıştır.

- Office 365 URL'leri ve IP adresi aralıkları, ExpressRoute bağlantılarınızın kapsamında olabilecek diğer Microsoft hizmetleri kapsamaz.

|**Seçeneği**|**Karmaşık -lığı**|**Denetimi Değiştir**|
|:-----|:-----|:-----|
|Tüm Microsoft yollarını kabul etme  <br/> |**Düşük:** Müşteri, tüm yolların düzgün bir şekilde sahip olduğundan emin olmak için Microsoft denetimlerine güvenir.  <br/> |Yok  <br/> |
|Microsoft'un sahip olduğu süper ağları filtreleme  <br/> |**Orta:** Müşteri yalnızca Microsoft'a ait yollara izin vermek için özetlenmiş ön ek filtre listeleri uygular.  <br/> |Müşteriler seyrek güncelleştirmelerin yol filtrelerine yansıtıldığından emin olmalıdır.  <br/> |
|Office 365 IP aralıklarını filtreleme  <br/> [!CAUTION] Not-Recommended |**Yüksek:** Müşteri, tanımlı Office 365 IP ön eklerine göre yolları filtreler.  <br/> |Müşterilerin aylık güncelleştirmeler için güçlü bir değişiklik yönetimi süreci uygulaması gerekir.  <br/> [!CAUTION] Bu çözüm, devam eden önemli değişiklikler gerektirir. Zamanında uygulanmayan değişiklikler büyük olasılıkla hizmet kesintisine neden olur.   |

Azure ExpressRoute kullanarak Office 365 bağlanmak, Office 365 uç noktalarının dağıtıldığı ağları temsil eden belirli IP alt ağlarının BGP tanıtımlarını temel alır. Office 365 küresel yapısı ve Office 365 oluşturan hizmetlerin sayısı nedeniyle, müşterilerin genellikle ağlarında kabul ettikleri reklamları yönetmeleri gerekir. Ortamınıza tanıtılan ön ek sayısıyla ilgileniyorsanız [BGP topluluk](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) özelliği, reklamları belirli bir Office 365 hizmetleri kümesine göre filtrelemenize olanak tanır. Bu özellik artık önizleme aşamasındadır.
  
Microsoft'tan gelen BGP yol tanıtımlarını nasıl yönettiğinizden bağımsız olarak, yalnızca İnternet bağlantı hattı üzerinden Office 365 bağlanmaya kıyasla Office 365 hizmetlerine özel bir şekilde maruz kalmazsınız. Microsoft, müşterinin Office 365 bağlanmak için kullandığı bağlantı hattının türüne bakılmaksızın aynı güvenlik, uyumluluk ve performans düzeylerini korur.
  
### <a name="security"></a>Güvenlik

Microsoft, ExpressRoute genel ve Microsoft eşlemesine giden ve giden bağlantılar için kendi ağ ve güvenlik çevre denetimlerinizi korumanızı önerir. Bu denetimler, Office 365 hizmetlerine giden ve bu hizmetlerden gelen bağlantıları içerir. Ağınızdan Microsoft'un ağına giden ve Microsoft'un ağından ağınıza gelen ağ istekleri için güvenlik denetimleri yerinde olmalıdır.
  
#### <a name="outbound-from-customer-to-microsoft"></a>Müşteriden Microsoft'a giden
  
Bilgisayarlar Office 365 bağlandığında, bağlantının İnternet üzerinden mi yoksa ExpressRoute bağlantı hattı üzerinden mi yapıldığına bakılmaksızın aynı uç nokta kümesine bağlanır. Kullanılan bağlantı hattından bağımsız olarak Microsoft, Office 365 hizmetleri genel İnternet hedeflerinden daha güvenilir olarak ele kullanmanızı önerir. Giden güvenlik denetimleriniz, maruziyeti azaltmak ve devam eden bakımı en aza indirmek için bağlantı noktalarına ve protokollere odaklanmalıdır. Gerekli bağlantı noktası bilgileri[, Office 365 uç noktaları](./urls-and-ip-address-ranges.md) başvuru makalesinde bulunabilir.
  
Ek denetimler için, İnternet veya Office 365 hedefleyen ağ isteklerinin bazılarını veya tümünü kısıtlamak veya incelemek için ara sunucu altyapınızda FQDN düzeyi filtrelemeyi kullanabilirsiniz. Özellikler yayımlandıkça ve Office 365 teklifleri geliştikçe FQDN'lerin listesini korumak için daha güçlü bir değişiklik yönetimi ve yayımlanan [Office 365 uç noktalarındaki](./urls-and-ip-address-ranges.md) değişikliklerin izlenmesi gerekir.
  
> [!CAUTION]
> Microsoft, Office 365 giden güvenliği yönetmek için yalnızca IP ön eklerine güvenmenizi önermez.

|**Seçeneği**|**Karmaşık -lığı**|**Denetimi Değiştir**|
|:-----|:-----|:-----|
|Kısıtlama yok  <br/> |**Düşük:** Müşteri, Microsoft'a sınırsız giden erişime izin verir.  <br/> |Yok  <br/> |
|Bağlantı noktası kısıtlamaları  <br/> |**Düşük:** Müşteri, Microsoft'a giden erişimi beklenen bağlantı noktalarıyla kısıtlar.  <br/> |Seyrek.  <br/> |
|FQDN kısıtlamaları  <br/> |**Yüksek:** Müşteri, yayımlanan FQDN'lere bağlı olarak Office 365 giden erişimi kısıtlar.  <br/> |Aylık değişiklikler.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>Microsoft'tan Müşteriye Gelen
  
Microsoft'un ağınıza bağlantı başlatmasını gerektiren birkaç isteğe bağlı senaryo vardır.
  
- Oturum açma için parola doğrulaması sırasında ADFS.

- [Karma dağıtımları Exchange Server](/exchange/exchange-hybrid).

- Exchange Online kiracıdan şirket içi konağa posta.

- SharePoint Online'dan şirket içi konağa SharePoint Çevrimiçi Posta gönderin.

- [Federasyon karma arama SharePoint](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online).

- [karma BCS SharePoint](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution).

- [Karma](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) ve/veya [Skype Kurumsal federasyonu Skype Kurumsal](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).

- [Bulut Bağlayıcısı'nı Skype Kurumsal](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

Microsoft, karmaşıklığı azaltmak için bu bağlantıları ExpressRoute bağlantı hattınız yerine İnternet bağlantı hattınız üzerinden kabul etmenizi önerir. Uyumluluk veya performans gereksinimleriniz bu gelen bağlantıların bir ExpressRoute bağlantı hattı üzerinden kabul edilmesi gerektiğini belirtirse, kabul edilen bağlantıların kapsamını kapsamak için bir güvenlik duvarı veya ters ara sunucu kullanılması önerilir. Doğru FQDN'leri ve IP ön [eklerini bulmak için Office 365 uç noktalarını](./urls-and-ip-address-ranges.md) kullanabilirsiniz.
  
### <a name="compliance"></a>Uyumluluk

Uyumluluk denetimlerimizin hiçbirinde kullandığınız yönlendirme yoluna güvenmeyiz. ExpressRoute veya İnternet bağlantı hattı üzerinden Office 365 hizmetlerine bağlandığınızdan bağımsız olarak uyumluluk denetimlerimiz değişmez. Kuruluşunuzun gereksinimlerini karşılamak için en iyi seçeneği bulmak üzere Office 365 için farklı uyumluluk ve güvenlik sertifika düzeylerini gözden geçirmeniz gerekir.
  
İşte geri dönmek için kullanabileceğiniz kısa bir bağlantı: [https://aka.ms/manageexpressroute365]()
  
## <a name="related-topics"></a>İlgili konular

[İçerik teslim ağları](content-delivery-networks.md)
  
[Office 365 URL'leri ve IP adresi aralıkları](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 uç noktalarını yönetme](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 Eğitimi için Azure ExpressRoute](https://channel9.msdn.com/series/aer)