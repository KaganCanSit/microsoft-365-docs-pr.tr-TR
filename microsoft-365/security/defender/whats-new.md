---
title: Microsoft 365 Defender'daki yenilikler
description: Microsoft 365 Defender'deki yeni özellikleri ve işlevleri listeler
keywords: Microsoft 365 Defender, ga, genel kullanıma sunulan, özellikler, kullanılabilir, yeni sürümündeki yenilikler
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: ed3d06e1719b51d0914c89e6283c8b53c2ab0812
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530526"
---
# <a name="whats-new-in-microsoft-365-defender"></a>Microsoft 365 Defender'daki yenilikler

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft 365 Defender'deki yeni özellikleri ve işlevleri listeler. 

RSS akışı: Aşağıdaki URL'yi kopyalayıp akış okuyucunuza yapıştırarak bu sayfa güncelleştirildiğinde bildirim alın:

```http
https://docs.microsoft.com/api/search/rss?search=%22Lists+the+new+features+and+functionality+in+Microsoft+365+defender%22&locale=en-us
```

Diğer Microsoft Defender güvenlik ürünleriyle ilgili yenilikler hakkında daha fazla bilgi için bkz:

- [Office 365 için Microsoft Defender’daki yenilikler](../office-365-security/whats-new-in-defender-for-office-365.md)
- [Uç Nokta için Microsoft Defender'deki yenilikler](../defender-endpoint/whats-new-in-microsoft-defender-endpoint.md)
- [Kimlik için Microsoft Defender'deki yenilikler](/defender-for-identity/whats-new)
- [Microsoft Defender for Cloud Apps'deki yenilikler](/cloud-app-security/release-notes)

Ayrıca, ürün güncelleştirmelerini ve önemli bildirimleri [ileti merkezi](https://admin.microsoft.com/Adminportal/Home#/MessageCenter) üzerinden de alabilirsiniz. 

## <a name="june-2022"></a>Haziran 2022
- (Önizleme) [DeviceTvmInfoGathering](advanced-hunting-devicetvminfogathering-table.md) ve [DeviceTvmInfoGatheringKB](advanced-hunting-devicetvminfogatheringkb-table.md) tabloları artık gelişmiş tehdit avcılığı şemasında kullanılabilir. Çeşitli yapılandırmaların durumu ve cihazların saldırı yüzeyi alanı durumları dahil olmak üzere Defender Güvenlik Açığı Yönetimi'ndeki değerlendirme olaylarını aramak için bu tabloları kullanın.

## <a name="may-2022"></a>Mayıs 2022
- (Önizleme) Yakın zamanda duyurulan [Microsoft Güvenlik Uzmanları](https://aka.ms/MicrosoftSecurityExperts) adlı yeni bir hizmet kategorisine genişletilmesine uygun olarak, genel önizleme [için Microsoft Defender Experts for Hunting (Avcılık](defenderexpertsforhuntingprev.md) için Defender Uzmanları) kullanıma sunulmuştur. Tehdit Avcılığı için Defender Uzmanları, güçlü bir güvenlik operasyonları merkezine sahip olan ancak Microsoft'un uç noktalar, Office 365, bulut uygulamaları ve kimlik gibi Microsoft Defender verilerinde tehditleri proaktif olarak avlamalarına yardımcı olmasını isteyen müşterilere yöneliktir. 

## <a name="april-2022"></a>Nisan 2022
- (Önizleme) Artık doğrudan tehdit avcılığı sorgu sonuçlarından e-posta iletilerinde [eylemler](advanced-hunting-take-action.md) yapılabilir. E-postalar diğer klasörlere taşınabilir veya kalıcı olarak silinebilir. 
- (Önizleme) Gelişmiş tehdit avcılığındaki yeni [`UrlClickEvents` tablo](advanced-hunting-urlclickevents-table.md), e-posta iletilerindeki Güvenli Bağlantılar tıklamaları, Microsoft Teams ve Office 365 uygulamalarından gelen bilgilere dayanarak kimlik avı kampanyaları ve şüpheli bağlantılar gibi tehditleri aramak için kullanılabilir.

## <a name="march-2022"></a>Mart 2022

- (Önizleme) Olay kuyruğu, araştırmalarınıza yardımcı olmak için tasarlanmış çeşitli özelliklerle geliştirilmiştir. Geliştirmeler, olayları kimliğe veya ada göre arama, özel bir zaman aralığı belirtme ve diğerleri gibi özellikleri içerir.


## <a name="december-2021"></a>Aralık 2021

- (GA) Tablo, `DeviceTvmSoftwareEvidenceBeta` belirli bir yazılımın bir cihazda nerede algılandığının kanıtını görüntülemenizi sağlamak için gelişmiş avcılıkta kısa vadeli olarak eklenmiştir.

## <a name="november-2021"></a>Kasım 2021

- (Önizleme) Cloud Apps için Defender'a uygulama idaresi eklentisi özelliği artık Microsoft 365 Defender'de kullanılabilir. Uygulama idaresi, Microsoft Graph API'leri aracılığıyla Microsoft 365 verilerine erişen OAuth özellikli uygulamalar için tasarlanmış bir güvenlik ve ilke yönetimi özelliği sağlar. Uygulama idaresi, bu uygulamaların ve kullanıcılarının, eyleme dönüştürülebilir içgörüler ve otomatik ilke uyarıları ve eylemleri aracılığıyla Microsoft 365'te depolanan hassas verilerinize erişme, bunları kullanma ve paylaşma konusunda tam görünürlük, düzeltme ve idare sağlar. [Uygulama idaresi hakkında daha fazla bilgi edinin](/cloud-app-security/app-governance-manage-app-governance).
- (Önizleme) [Gelişmiş tehdit avcılığı](advanced-hunting-overview.md) sayfasında artık çok sekmeli destek, akıllı kaydırma, kolaylaştırılmış şema sekmeleri, sorgular için hızlı düzenleme seçenekleri, sorgu kaynağı kullanım göstergesi ve sorgulamayı daha sorunsuz ve hassas hale getirmek için diğer geliştirmeler yer alır.
- (Önizleme) Artık [olay bağlantısını](advanced-hunting-link-to-incident.md) kullanarak gelişmiş tehdit avcılığı sorgu sonuçlarından olayları veya kayıtları araştırdığınız yeni veya var olan bir olaya ekleyebilirsiniz.

## <a name="october-2021"></a>Ekim 2021

- (GA) Gelişmiş avcılıkta [CloudAppEvents](advanced-hunting-cloudappevents-table.md) tablosuna daha fazla sütun eklendi. Artık `AccountType`sorgularınıza , `IsExternalUser`, `IsImpersonated`, `IPTags`, `IPCategory`ve `UserAgentTags` ekleyebilirsiniz.

## <a name="september-2021"></a>Eylül 2021

- (GA) Office 365 için Microsoft Defender olay verileri Microsoft 365 Defender olay akışı API'sinde kullanılabilir. [Akış API'sinde Desteklenen Microsoft 365 Defender olay türlerinde olay türlerinin](supported-event-types.md) kullanılabilirliğini ve durumunu görebilirsiniz.
- (GA) Gelişmiş avcılıkta kullanılabilen Office 365 için Microsoft Defender verileri artık genel kullanıma sunulmuştur.
- (GA) Kullanıcı hesaplarına olay ve uyarı atama

  Bir olayı ve onunla ilişkili tüm uyarıları, bir olayın **Olay yönetme** bölmesinde veya uyarının **Uyarıyı yönet** **bölmesindeki Ata:** öğesinden bir kullanıcı hesabına atayabilirsiniz.

## <a name="august-2021"></a>Ağustos 2021

- (Önizleme) Office 365 için Microsoft Defender verileri gelişmiş avcılıkta kullanılabilir

  E-posta tablolarındaki yeni sütunlar, gelişmiş tehdit avcılığı kullanarak daha kapsamlı araştırmalara yönelik e-posta tabanlı tehditler hakkında daha fazla içgörü sağlayabilir. Artık sütunu [EmailEvents'e](./advanced-hunting-emailevents-table.md), `FileSize` [EmailAttachmentInfo'ya](./advanced-hunting-emailattachmentinfo-table.md) ve `ThreatTypes` `DetectionMethods` [EmailPostDeliveryEvents tablolarına](./advanced-hunting-emailpostdeliveryevents-table.md) ekleyebilirsiniz`AuthenticationDetails`.

- (Önizleme) Olay grafiği

  Bir olayın **Özet** sekmesindeki yeni **Bir Grafik** sekmesi, saldırının tam kapsamını, saldırının ağınızda zaman içinde nasıl yayıldığını, nereden başladığını ve saldırganın ne kadar ileri gittiğini gösterir.

## <a name="july-2021"></a>Temmuz 2021

- [Profesyonel hizmetler kataloğu](https://sip.security.microsoft.com/interoperability/professional_services)

  Desteklenen iş ortağı bağlantıları ile platformun algılama, araştırma ve tehdit bilgileri özelliklerini geliştirin.

## <a name="june-2021"></a>Haziran 2021

- (Önizleme) [Tehdit etiketleri başına raporları görüntüleme](threat-analytics.md#view-reports-per-threat-tags)

  Tehdit etiketleri belirli tehdit kategorilerine odaklanmanıza ve en ilgili raporları gözden geçirmenize yardımcı olur.

- (Önizleme) [Akış API'si](../defender-endpoint/raw-data-export.md)

  Microsoft 365 Defender, Gelişmiş Tehdit Avcılığı aracılığıyla bir Event Hubs ve/veya Azure depolama hesabına sağlanan tüm olayların akışını destekler.

- (Önizleme) [Gelişmiş avcılıkta harekete geçme](advanced-hunting-take-action.md)

  Tehditleri hızla içerir veya [gelişmiş avcılıkta](advanced-hunting-overview.md) bulduğunuz güvenliği aşılmış varlıkları ele alır.

- (Önizleme) [Portal içi şema başvurusu](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)

  Gelişmiş tehdit avcılığı şema tabloları hakkında doğrudan güvenlik merkezinden bilgi edinin. Tablo ve sütun açıklamalarına ek olarak, bu başvuru desteklenen olay türlerini (`ActionType` değerleri) ve örnek sorguları içerir.

- (Önizleme) [DeviceFromIP() işlevi](advanced-hunting-devicefromip-function.md)

  Belirli bir zaman aralığında belirli bir IP adresine veya adreslerine atanmış cihazlar hakkında bilgi edinin.

## <a name="may-2021"></a>Mayıs 2021

- [Microsoft 365 Defender portalındaki yeni uyarı sayfası](https://techcommunity.microsoft.com/t5/microsoft-365-defender/easily-find-anomalies-in-incidents-and-alerts/ba-p/2339243)

  Bir saldırının bağlamı için gelişmiş bilgiler sağlar. Geçerli uyarıya başka hangi tetiklenen uyarının neden olduğunu ve saldırıda dosyalar, kullanıcılar ve posta kutuları dahil olmak üzere etkilenen tüm varlıkları ve etkinlikleri görebilirsiniz. Daha fazla bilgi için bkz [. Uyarıları araştırma](/microsoft-365/security/defender/investigate-alerts) .

- [Microsoft 365 Defender portalında olaylar ve uyarılar için eğilim grafiği](https://techcommunity.microsoft.com/t5/microsoft-365-defender/new-alert-page-for-microsoft-365-defender-incident-detections/ba-p/2350425)

  Tek bir olay için birkaç uyarı olup olmadığını veya kuruluşunuzun birkaç farklı olayla saldırı altında olduğunu belirleyin. Daha fazla bilgi için bkz. [Olayları önceliklendirme](/microsoft-365/security/defender/incident-queue) .

## <a name="april-2021"></a>Nisan 2021

- Microsoft 365 Defender

  Geliştirilmiş [Microsoft 365 Defender](https://security.microsoft.com) portalı artık kullanılabilir. Bu yeni deneyim, Uç Nokta için Defender, Office 365 için Defender, Kimlik için Defender ve daha fazlasını tek bir portalda bir araya getirir. Burası, güvenlik denetimlerinizi yönetmek için yeni bir evdir. [Yeni olanları öğrenin](./microsoft-365-defender.md#the-microsoft-365-defender-portal).

- [Microsoft 365 Defender tehdit analizi raporu](threat-analytics.md)

  Tehdit analizi, etkin saldırıların etkisini yanıtlamanıza ve en aza indirmenize yardımcı olur. Ayrıca Microsoft 365 Defender çözümleri tarafından engellenen saldırı girişimleri hakkında bilgi edinebilir ve daha fazla maruz kalma riskini azaltan ve dayanıklılığı artıran önleyici eylemler gerçekleştirebilirsiniz. Birleşik güvenlik deneyiminin bir parçası olarak tehdit analizi artık Uç Nokta için Microsoft Defender ve Office E5 için Microsoft Defender lisans sahipleri tarafından kullanılabilir.

## <a name="march-2021"></a>Mart 2021

- [CloudAppEvents tablosu](advanced-hunting-cloudappevents-table.md)

  Microsoft Cloud App Security kapsamındaki çeşitli bulut uygulamaları ve hizmetlerindeki olaylar hakkında bilgi edinin. Bu tablo, daha önce tabloda bulunan `AppFileEvents` bilgileri de içerir.

