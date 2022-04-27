---
title: Contoso Corporation için ağ oluşturma
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Contoso ağ altyapısını ve şirketin kurumsal bulut hizmetleri için Microsoft 365 için en iyi ağ performansı için SD-WAN teknolojisini nasıl kullandığını anlayın.
ms.openlocfilehash: f8450b63bed68de414c0ea585b6f5e199c87ad90
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093953"
---
# <a name="networking-for-the-contoso-corporation"></a>Contoso Corporation için ağ oluşturma

Contoso, bulut kapsayıcı bir altyapıyı benimsemek için bulut hizmetlerine yönelik ağ trafiğinin nasıl ilerlediği konusunda temel bir değişiklik yaptı. Ofis hiyerarşisinin bir sonraki düzeyi için ağ bağlantısına ve trafiğe odaklanan bir iç merkez-uç modeli yerine, kullanıcı konumlarını yerel İnternet çıkışına ve yerel bağlantıları İnternet'te en yakın Microsoft 365 ağ konumuna eşler.

## <a name="networking-infrastructure"></a>Ağ altyapısı

Contoso ofislerini dünya genelinde birbirine bağlayan ağ öğeleri şunlardır:

- Multiprotocol Label Switching (MPLS) WAN ağı

  MPLS WAN ağı, Paris genel merkezini bölgesel ofislere ve bölgesel ofisleri bir uç ve merkez yapılandırmasındaki uydu ofislere bağlar. Ağ, kullanıcıların Paris genel merkezinde iş kolu uygulamalarını oluşturan şirket içi sunuculara erişmesini sağlar. Ayrıca tüm genel İnternet trafiğini, ağ güvenlik cihazlarının istekleri temizlediği Paris ofisine yönlendirir. Her ofiste yönlendiriciler, özel IP adresi alanını kullanan alt ağlardaki kablolu konaklara veya kablosuz erişim noktalarına trafik sağlar.

- Microsoft 365 trafiği için yerel doğrudan İnternet erişimi

  Her ofiste, bir ara sunucu üzerinden kendi internet bağlantısına sahip bir veya daha fazla yerel internet ISS ağ bağlantı hattına sahip yazılım tanımlı BIR WAN (SD-WAN) cihazı vardır. Bu genellikle genel IP adresleri ve yerel DNS sunucusu sağlayan yerel bir ISS'ye WAN bağlantısı olarak uygulanır.

- İnternet iletişim durumu

  Contosocom ortak etki alanı adının sahibi Contoso'dır\.. Ürünleri sipariş etmek için Contoso genel web sitesi, Paris kampüsündeki İnternet'e bağlı bir veri merkezinde bulunan bir sunucu kümesidir. Contoso, İnternet'te /24 genel IP adresi aralığı kullanır.

Şekil 1'de Contoso ağ altyapısı ve İnternet bağlantıları gösterilmektedir.

![Contoso ağı.](../media/contoso-networking/contoso-networking-fig1.png)
 
**Şekil 1: Contoso ağı**

## <a name="use-of-sd-wan-for-optimal-network-connectivity-to-microsoft"></a>Microsoft'a en uygun ağ bağlantısı için SD-WAN kullanımı

Contoso[, ağ bağlantısı ilkelerini Microsoft 365](microsoft-365-network-connectivity-principles.md) takip etti:

- Ağ trafiğini Microsoft 365 belirleme ve ayırt etmek
- Ağ bağlantılarını yerel olarak Egress
- Ağ saç tokalarından kaçının
- Yinelenen ağ güvenlik cihazlarını atlama

Microsoft 365 için üç ağ trafiği kategorisi vardır: *İyileştir*, *İzin Ver* ve *Varsayılan*. İyileştirme ve trafiğe izin ver, uç noktalarda şifrelenen ve güvenliği sağlanan ve Microsoft 365 ağı hedefleyen güvenilir ağ trafiğidir.

Contoso şunları yapmaya karar verdi:

- Kategori trafiğini İyileştir ve İzin Ver için doğrudan internet çıkışını kullanın ve tüm Varsayılan kategori trafiğini Paris tabanlı merkezi internet bağlantısına iletin.

- Bu ilkeleri izlemenin ve bulut tabanlı Microsoft 365 hizmetler için en iyi ağ performansını elde etmenin basit bir yolu olarak her ofiste SD-WAN cihazları dağıtın.

  SD-WAN cihazlarının yerel ofis ağı için bir LAN bağlantı noktası ve birden çok WAN bağlantı noktası vardır. Bir WAN bağlantı noktası MPLS ağına bağlanır. Başka bir yerel ISS bağlantı hattına bağlanır. SD-WAN cihazı, ISS bağlantısı üzerinden Kategori ağ trafiğini en iyi duruma getirme ve izin verme yollarını yönlendirir.

## <a name="the-contoso-line-of-business-app-infrastructure"></a>Contoso iş kolu uygulaması altyapısı

Contoso, iş kolu uygulaması ve sunucu intranet altyapısını aşağıdakiler için tasarlamıştır:

- Uydu ofisleri, sık erişilen belgeleri ve iç web sitelerini depolamak için yerel önbelleğe alma sunucularını kullanır.
- Bölgesel merkezler, bölgesel ve uydu ofisleri için bölgesel uygulama sunucularını kullanır. Bu sunucular Paris merkezindeki sunucularla eşitlenir.
- Paris kampüs veri merkezleri, tüm kuruluşa hizmet veren merkezi uygulama sunucuları içerir.

Şekil 2'de Contoso intraneti genelindeki sunuculara erişirken kullanılan ağ trafiği kapasitesinin yüzdesi gösterilmektedir.

![İç uygulamalar için Contoso altyapısı.](../media/contoso-networking/contoso-networking-fig2.png)
 
**Şekil 2: İç uygulamalar için Contoso altyapısı**

Uydu veya bölgesel merkez ofisleri için çalışanların ihtiyaç duyduğu kaynakların yüzde 60'ı uydu ve bölgesel merkez ofis sunucuları tarafından servis edilebilir. Kaynak isteklerinin ek yüzde 40'ının Paris kampüsüne giden WAN bağlantısı üzerinden gitmesi gerekir.

## <a name="network-analysis-and-preparation-for-microsoft-365-for-enterprise"></a>Kuruluş için Microsoft 365 için ağ analizi ve hazırlığı

Contoso kullanıcıları kurumsal hizmetler için Microsoft 365 başarılı bir şekilde benimsenmesi, İnternet'e veya doğrudan Microsoft bulut hizmetlerine yüksek oranda kullanılabilir ve yüksek performanslı bağlantıya bağlıdır. Contoso, kurumsal bulut hizmetleri için Microsoft 365 için iyileştirilmiş bağlantı planlamak ve uygulamak için şu adımları gerçekleştirdi:

1. Planlamaya yardımcı olacak bir şirket WAN ağ diyagramı oluşturma

   Contoso, ağ planlamasını başlatmak için ofis konumlarını, mevcut ağ bağlantısını, mevcut ağ çevre cihazlarını ve ağda yönetilen hizmet sınıflarını gösteren bir diyagram oluşturdu. Ağ bağlantısını planlama ve uygulama adımlarının her biri için bu diyagramı kullandılar.

2. Kurumsal ağ bağlantısı için Microsoft 365 planı oluşturma

   Contoso[, Microsoft 365 ağ bağlantı ilkelerini](microsoft-365-network-connectivity-principles.md) ve örnek başvuru ağ mimarilerini kullanarak SD-WAN'ı Microsoft 365 bağlantısı için tercih ettikleri topoloji olarak tanımladı.

3. Her ofiste İnternet bağlantısı kullanımını ve MPLS-WAN bant genişliğini analiz edin ve gerektiğinde bant genişliğini artırın

   Her ofisin geçerli kullanımı analiz edildi ve bulut tabanlı trafiğin tahmin edilen Microsoft 365 ortalama yüzde 20 kullanılmayan kapasiteyle çalışması için devreler artırıldı.

4. Performansı Microsoft ağ hizmetlerine en iyi duruma getirme

   Contoso, en iyi performans için Office 365, Intune ve Azure uç noktaları kümesini belirledi ve İnternet yolunda güvenlik duvarlarını, güvenlik cihazlarını ve diğer sistemleri yapılandırdı. Office 365 İyileştirme ve İzin Ver kategori trafiği uç noktaları, ISS devresi üzerinden yönlendirme için SD-WAN cihazlarına yapılandırıldı.

5. İç DNS'yi yapılandırma

   DNS'nin işlevsel olması ve Microsoft 365 trafiği için yerel olarak aranmış olması gerekir.

6. Ağ uç noktasını ve bağlantı noktası bağlantısını doğrulama

   Contoso, kurumsal bulut hizmetleri için Microsoft 365 bağlantısını doğrulamak için Microsoft ağ bağlantısı test araçlarını çalıştırmıştı.

7. Çalışan bilgisayarları ağ bağlantısı için iyileştirme

   En son işletim sistemi güncelleştirmelerinin yüklendiğinden ve uç nokta güvenlik izlemesinin tüm istemcilerde etkin olduğundan emin olmak için tek tek bilgisayarlar denetlendi.

## <a name="next-step"></a>Sonraki adım

Contoso'nın çalışanlar için [bulutta şirket içi Active Directory Domain Services'dan nasıl yararlanıp](contoso-identity.md) müşteriler ve iş ortakları için kimlik doğrulamasını nasıl bir araya getirmesi hakkında bilgi edinin.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 için ağ yol haritası](networking-roadmap-microsoft-365.md)

[Microsoft 365 Kurumsal’a genel bakış](microsoft-365-overview.md)

[Test laboratuvarı kılavuzları](m365-enterprise-test-lab-guides.md)
