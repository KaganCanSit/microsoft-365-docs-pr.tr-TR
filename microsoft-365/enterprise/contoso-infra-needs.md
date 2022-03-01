---
title: Contoso IT altyapısı ve iş ihtiyaçları
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
description: Contoso şirket içi IT altyapısının temel yapısını ve kurumsal bir kuruluş için Kurumsal İş tarafından şirketin iş  ihtiyaçlarının nasıl karşı Microsoft 365 anlamak.
ms.openlocfilehash: 94118a66f7bb1468a8f27816151a3b4d087b5703
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006765"
---
# <a name="contoso-it-infrastructure-and-business-needs"></a>Contoso IT altyapısı ve iş ihtiyaçları

Contoso, şirket içi, merkezi bir IT altyapısından bulut tabanlı kişisel üretkenlik iş yüklerini ve uygulamalarını içeren bulut dahil kuruluma geçiş ediyor.

## <a name="existing-contoso-it-infrastructure"></a>Mevcut Contoso IT altyapısı

Contoso, Paris merkezinde uygulama veri merkezleriyle birlikte çoğunlukla merkezi bir şirket içi IT altyapısı kullanır.

Burada, uygulama veri merkezleri, DMZ ve İnternet'in yer alan genel merkez ofisi yer almaktadır.

![Mevcut Contoso IT altyapısı.](../media/contoso-infra-needs/contoso-infra-needs-fig1.png)

Şirket içi uygulama veri merkezleri ana bilgisayarı: 

- İş ve diğer Linux veritabanlarını kullanan SQL Server iş hattı uygulamaları.
- Eski ve eski SharePoint.
- Dosya depolaması için kuruluş ve ekip düzeyi sunucular.

Buna ek olarak, her bölgesel merkez ofisi benzer uygulama kümesine sahip bir sunucu kümesi destekler. Bu sunucular, bölgesel IT departmanlarının denetimi altında yer almaktadır.

Bu ayrı çok coğrafi veri merkezlerinin uygulamaları ve verileri arasında arama yapmak çok zor bir iştir.

Contoso merkez DMZ'de, farklı sunucu kümeleri şunları sağlar:

- Müşterilerin ürün, parça, malzeme ve hizmet siparişi ve hizmetine sahip olduğu Contoso genel web sitesi için barındırma.
- İş ortağı iletişimi ve işbirliği için Contoso iş ortağı extranet'ini barındırma.
- Paris merkezinde çalışanların Contoso intranet'ine ve web ara sunucusuna sanal özel ağ (VPN) tabanlı uzaktan erişim.

## <a name="contoso-business-needs"></a>Contoso iş ihtiyaçları

Contoso iş ihtiyaçları beş ana kategoriye ayrılır:

**Üretkenlik**

- İşbirliğini kolaylaştırma

  Belgelerde gerçek zamanlı değişikliklere, daha kolay çevrimiçi toplantılara ve yakalanan konuşma dizilerine olanak sağlayan çevrimiçi bir modelle e-posta ve dosya paylaşımı tabanlı işbirliğini değiştirin.
- Uzak ve mobil çalışanlar için üretkenliği artırma

  Evde veya alanda çalışan çok sayıda çalışan için, performans sorunu olan VPN çözümünü buluttaki Contoso verilerine ve kaynaklarına performans erişimiyle değiştirin.
- Yaratıcılığı ve yeniliği artırma

  Marakarak ve 3D görselleştirme de dahil olmak üzere en son görsel öğrenme ve fikir geliştirme yöntemlerinden faydalanin.

**Güvenlik**

- Kimlik ve erişim yönetimi

  Çok faktörlü ve diğer kimlik doğrulama biçimlerini zorunlu kılın ve kullanıcı ve yönetici hesabı kimlik bilgilerini koruyun.

- Tehdit koruması

  E-posta ve işletim sistemi tabanlı kötü amaçlı yazılım dahil, dış güvenlik tehditlerine karşı koruyun.

- Bilgi koruması

  Müşteri verileri, tasarım ve üretim belirtimleri ve çalışan bilgileri gibi yüksek değerli dijital varlıklara erişimi kilitleyip şifreler.

- Güvenlik yönetimi

  Güvenlik durumunu takip eder, tehditleri gerçek zamanlı olarak algılar ve yanıtlar.

**Uzak ve mobil erişim ve iş ortakları**

- Uzak çalışanların ve cep telefonu çalışanlarının güvenliğini artırma

  Güvenli erişim, doğru uygulama davranışı ve şirket veri koruması sağlamak için kendi cihazınızı (BYOD) ve şirkete ait cihaz yönetimini getirin.

- Çalışanlar için uzaktan erişim altyapısını azaltma

  Sık erişilen kaynakları buluta taşımayla, bakım ve destek maliyetlerini düşürebilir ve uzaktan erişim çözümünün performansını geliştirebilirsiniz.

- İşletmeler arasında (B2B) işlemler için daha iyi bağlantı ve daha düşük yük sağlama

  Eskimiş ve pahalı iş ortağı extranet'ini, federasyon kimlik doğrulaması kullanan bulut tabanlı bir çözümle değiştirin.

**Uyumluluk**

- Bölgesel mevzuat gereksinimlerine bağlı kalın

  Avrupa Birliği'ne ilişkin Genel Veri Koruma Yönetmeliği (GDPR) gibi veri depolama, şifreleme, veri gizliliği ve kişisel veri düzenlemelerine ilişkin endüstri ve bölgesel düzenlemelere uygun uyumluluğu sağlayın.

**Yönetim**

- İstemci PC'lerde ve cihazlarda çalışan yazılımları yönetmek için daha düşük IT yükü

  Yeni işletim sistemine ve kuruluş Windows güncelleştirmelerinin Kurumlar için Microsoft 365 Uygulamaları otomatikleştirin.

## <a name="mapping-contoso-business-needs-to-microsoft-365-for-enterprise"></a>Contoso işletmesi için eşlemenin Microsoft 365 olması gerekiyor

Contoso IT bölümü, işle ilgili aşağıdaki eşlemenin dağıtım öncesinde Microsoft 365 E5 gerektirmektedir:


| Kategori | İş ihtiyacı | Microsoft 365 ürünler veya özellikler için özelliklerle ilgili özellikler |
|:-------|:-----|:-----|
| Üretkenlik |  |  |
|  | İşbirliğini kolaylaştırma | Microsoft Teams, SharePoint, OneDrive |
|  | Uzak ve mobil çalışanlar için üretkenliği artırma | Microsoft 365 yüklerini ve bulut tabanlı verileri depolama |
|  | Yaratıcılığı ve yeniliği artırma | Windows Ink, Cortana'da, tamamla'PowerPoint |
| Güvenlik |  |  |
|  | Kimlik & yönetimi | Azure AD Multi-Factor Authentication (MFA) ve Azure AD Etki Alanı (PIM) ile ayrılmış Privileged Identity Management hesapları <br> Tüm kullanıcı hesapları için MFA <br> Koşullu Erişim <br> Güvenlik Okuyucu <br> Windows Hello <br> Windows Credential Guard |
|  | Tehdit koruması | Gelişmiş Tehdit Analizi <br> Windows Defender <br> Office 365 için Defender <br> Office 365 için Microsoft Defender <br> Microsoft 365 soruşturma ve yanıtını geri ala <br> |
|  | Bilgi koruması | Azure Information Protection <br> Veri Kaybı Önleme (DLP) <br> Windows Koruması (WIP) <br> Bulut Uygulamaları için Microsoft Defender <br> Microsoft Intune |
|  | Güvenlik yönetimi | Bulut için Microsoft Defender  <br> Windows Defender Merkezi |
| Uzak ve mobil erişim ve iş ortakları |  |  |
|  | Uzak çalışanlar ve cep telefonu çalışanları için daha iyi güvenlik | Microsoft Intune |
|  | Çalışanlar için uzaktan erişim altyapısını azaltma | Microsoft 365 yüklerini ve bulut tabanlı verileri depolama |
|  | B2B işlemleri için bağlantı ve daha düşük yük geliştirme | Federasyon kimlik doğrulaması ve bulut tabanlı kaynaklar |
| Uyumluluk |  |  |
|  | Bölgesel mevzuat gereksinimlerine bağlı kalın | MICROSOFT 365'de GDPR özellikleri |
| Yönetim |  |  |
|  | İstemci güncelleştirmelerini yüklemek için daha düşük IT yükü | Windows 10 Enterprise güncelleştirmeleri yükleme <br> Kurumlar için Microsoft 365 Uygulamaları güncelleştirmeleri yükleme |
||||

## <a name="next-step"></a>Sonraki adım

Contoso Corporation şirket içi [ağı,](contoso-networking.md) bulut tabanlı kaynaklara erişim ve gecikme süresi için nasıl en Microsoft 365 hakkında bilgi edinebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Test laboratuvarı kılavuzları](m365-enterprise-test-lab-guides.md)
