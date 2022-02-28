---
title: Contoso Corporation için ağ
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Contoso ağ altyapısını ve şirketin kurumsal bulut hizmetleriyle ilgili ağ performansını en iyi şekilde Microsoft 365 için SD-WAN teknolojisini nasıl kullandığını anlıyoruz.
ms.openlocfilehash: 94c9c43e35f0f1a3d973529aa2b107cffe608693
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985056"
---
# <a name="networking-for-the-contoso-corporation"></a>Contoso Corporation için ağ

Bulut dahil bir altyapı benimseyen Contoso, ağ trafiğinin bulut hizmetleriyle seyahatleri için temel bir geçiş yaptı. Ofis hiyerarşisinin sonraki düzeyi için ağ bağlantısını ve trafiği odaklanan iç merkez ve sözcük modeli yerine, kullanıcı konumlarını yerel İnternet çıkış ve İnternet'te en yakın Microsoft 365 bağlantılarına eşlerler.

## <a name="networking-infrastructure"></a>Ağ altyapısı

Bunlar, dünyanın her bir yerindeki Contoso ofislerini bağan ağ öğeleridir:

- Multiprotocol Label Switching (MPLS) WAN ağı

  MPLS WAN ağı, Paris merkezlerini bölgesel ofislere ve bölgesel ofislere, bağlı ve merkezi bir yapılandırmayla uydu ofislerine bağlar. Bu ağ, kullanıcıların Paris merkez merkezinde iş yeri uygulamaları sağlayan şirket içi sunuculara erişmelerine olanak sağlar. Ayrıca, genel İnternet trafiğini ağ güvenlik cihazlarının istekleri temizleyişleri için Paris'e yönlendirmektedir. Her ofis içinde yönlendiriciler, trafiği özel IP adresi alanı kullanan alt ağlarda kablolu ana bilgisayarlara veya kablosuz erişim noktalarına teslim ediyor.

- İnternet trafiği için yerel Microsoft 365 erişimi

  Her ofis, bir ara sunucu üzerinden kendi internet bağlantısı olan bir veya daha fazla yerel İnternet ISS ağ devresi olan yazılım tanımlı bir WAN (SD-WAN) cihazına sahiptir. Bu normalde genel IP adreslerini ve yerel bir DNS sunucusu da sağlayan yerel bir ISS'ye WAN bağlantısı olarak uygulanır.

- İnternet iletişim durumu

  Contosocom ortak etki alanı\. adının sahibi Contoso'dır. Ürün sipariş etmek için Contoso genel web sitesi, Paris kampüsünde, İnternet bağlantılı bir veri merkezinde bulunan bir sunucu kümesidir. Contoso, İnternet'te bir /24 genel IP adresi aralığı kullanır.

Şekil 1, Contoso ağ altyapısını ve İnternet bağlantılarını gösterir.

![Contoso ağı.](../media/contoso-networking/contoso-networking-fig1.png)
 
**Şekil 1: Contoso ağı**

## <a name="use-of-sd-wan-for-optimal-network-connectivity-to-microsoft"></a>Microsoft'a en uygun ağ bağlantısı için SD-WAN kullanımı

Contoso tarafından [takip Microsoft 365 ağ bağlantısı ilkeleri:](microsoft-365-network-connectivity-principles.md)

- Ağ trafiğini tanımlama Microsoft 365 ayırt etmek
- Egress bağlantılarını yerel olarak yapılandırma
- Ağ Apin'lerden kaçının
- Yinelenen ağ güvenlik cihazlarını atlama

Posta için üç ağ trafiği kategorisi *Microsoft 365: En* İyi Duruma *Getirme, İzin Ver* ve *Varsayılan*. Trafiği En İyi Duruma Getirme ve Trafiğine İzin Ver, uç noktalarda şifrelenmiş ve güvenli olan ve Microsoft 365 olur.

Contoso şunları yapmaya karar verdi:

- En İyi Duruma Getirmek ve İzin Ver kategori trafiği için doğrudan İnternet çıkışlarını kullanın ve tüm Varsayılan kategori trafiğini Paris tabanlı merkezi İnternet bağlantısına iletin.

- SD-WAN cihazlarını bu ilkeleri izlemenin ve bulut tabanlı hizmetlerde en iyi ağ performansını elde etmek için Microsoft 365 bir yolla her ofiste dağıtın.

  SD-WAN cihazlarının yerel ofis ağı için bir LAN bağlantı noktası ve birden çok WAN bağlantı noktası vardır. Bir WAN bağlantı noktası MPLS ağına bağlanır. Başka bir bağlantı yerel ISS devrelerine bağlanır. SD-WAN cihazı, En İyi Duruma Getirmek ve İzin Ver kategori ağ trafiğini ISS bağlantısı üzerinden yönlendirmektedir.

## <a name="the-contoso-line-of-business-app-infrastructure"></a>Contoso iş hattı uygulaması altyapısı

Contoso, aşağıdakiler için iş hattı uygulaması ve sunucu intranet altyapısını hazırlar:

- Uydu ofisleri, sık erişilen belgeleri ve iç web sitelerini depolamak için yerel önbellek sunucularını kullanır.
- Bölgesel merkezler, bölgesel ve uydu ofisleri için bölgesel uygulama sunucuları kullanır. Bu sunucular, Paris merkez merkezinde yer alan sunucularla eşitlenir.
- Paris kampüs veri merkezleri, tüm kuruluşa hizmet eden merkezi uygulama sunucuları içerir.

Şekil 2, Contoso intraneti üzerinden sunuculara erişirken kullanılan ağ trafiği kapasitesinin yüzdesini gösterir.

![İç uygulamalar için Contoso altyapısı.](../media/contoso-networking/contoso-networking-fig2.png)
 
**Şekil 2: İç uygulamalar için Contoso altyapısı**

Uydu veya bölgesel merkez ofislerinde, çalışanlar tarafından gereken kaynakların yüzde 60'ı uydu ve bölgesel merkez ofis sunucularına hizmet kullanılabilir. Kaynak isteklerinin ek yüzde 40'ı, WAN bağlantısının Paris kampüsüne üzerinden olması gerekir.

## <a name="network-analysis-and-preparation-for-microsoft-365-for-enterprise"></a>Kurumsal ağ çözümlemesi ve Microsoft 365 hazırlığı

Contoso kullanıcıları tarafından Microsoft 365 kurumsal hizmetler için başarılı bir şekilde benimsenmesi, İnternet bağlantısında veya doğrudan Microsoft bulut hizmetlerinin yüksek düzeyde kullanılabilir ve performansına bağlıdır. Contoso, kurumsal bulut hizmetleri için kurumsal bulut hizmetlerini planlamak ve bunlara Microsoft 365 için şu adımları gerçekleştirdi:

1. Planlamaya yardımcı olmak için şirket WAN ağ diyagramı oluşturma

   Contoso, ağ planlamasını başlatmak için ofis konumlarını, var olan ağ bağlantısını, var olan ağ çevre cihazlarını ve ağ üzerinde yönetilen hizmet sınıflarını gösteren bir diyagram oluşturdu. Bu diyagram, ağ bağlantısını planlama ve uygulamanın sonraki her adımı için kullanılır.

2. Kurumsal ağ bağlantısı Microsoft 365 planı oluşturma

   Contoso, SD-WAN [Microsoft 365](microsoft-365-network-connectivity-principles.md) tercih ettiği topoloji olarak bu ağ bağlantısı ilkelerini ve örnek başvuru ağ mimarilerini kullanarak, Microsoft 365 kullanmıştır.

3. Her ofiste İnternet bağlantısı kullanımını ve MPLS-WAN bant genişliğini çözümleme ve gerektiğinde bant genişliğini artırma

   Her office'in geçerli kullanımı çözümlendi ve devreler artırıldı; dolayısıyla bulut tabanlı Microsoft 365 trafiğin ortalama yüzde 20 kullanılmayan kapasiteyle çalışması öngörüldüğü için devreler artırıldı.

4. Performansı Microsoft ağ hizmetleri için en iyi duruma getirme

   Contoso en iyi performans için Office 365, Intune ve Azure uç noktaları kümesiyle İnternet yolu üzerinde yapılandırılmış güvenlik duvarları, güvenlik cihazları ve diğer sistemler kümesine karar verdi. IsS devresi Office 365 için SD-WAN cihazlarında En İyi Duruma Getirme ve İzin Ver kategori trafiğinin uç noktaları yapılandırılmıştır.

5. İç DNS'yi yapılandırma

   DNS'nin işlevsel olması ve trafikte yerel olarak Microsoft 365 gerekir.

6. Ağ uç noktasını ve bağlantı noktası bağlantısını doğrulama

   Contoso tarafından, kurumsal bulut hizmetleri için E-posta için bağlantı Microsoft 365 Microsoft ağ bağlantısı test araçları çalışır.

7. Çalışan bilgisayarları ağ bağlantısı için en iyi duruma getirme

   En son işletim sistemi güncelleştirmelerinin yüklendiğinden ve uç nokta güvenliği izlemenin tüm istemcilerde etkin olduğundan emin olmak için tek tek bilgisayarlar denetlenir.

## <a name="next-step"></a>Sonraki adım

Contoso'un çalışanlar [için buluttaki şirket içi Active Directory Etki Alanı Hizmetleri'den](contoso-identity.md) nasıl yararlanarak müşteriler ve iş ortakları için federal kimlik doğrulamasını nasıl kaldırıyor hakkında bilgi edinebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

[Web siteleri için ağ Microsoft 365](networking-roadmap-microsoft-365.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Test laboratuvarı kılavuzları](m365-enterprise-test-lab-guides.md)
