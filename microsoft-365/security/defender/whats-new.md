---
title: Microsoft 365 Defender'daki yenilikler
description: Microsoft 365 Defender'daki yeni özellikleri ve işlevleri Microsoft 365 Defender
keywords: Microsoft 365 Defender, ga, genel olarak kullanılabilir, özellikler, kullanılabilir, yeni
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
ms.openlocfilehash: aebf7a82a886540374176c06535e9f0097e73a03
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499825"
---
# <a name="whats-new-in-microsoft-365-defender"></a>Microsoft 365 Defender'daki yenilikler

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

> Bu deneyimi Microsoft 365 Defender? Bunu bir [laboratuvar ortamında değerlendirin veya](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) [üretimde pilot projenizi çalıştırın](m365d-pilot.md?ocid=cx-evalpilot).

Aşağıdaki özellikler, Microsoft 365 Defender'in en son sürümüne önizlemede veya genel olarak (GA) Microsoft 365 Defender.

RSS akışı: Bu sayfa güncelleştirildiğinde, akış okuyucuya aşağıdaki URL'yi kopyalayıp yapıştırarak bilgi alın:

```http
https://docs.microsoft.com/api/search/rss?search=%22Lists+the+new+features+and+functionality+in+Microsoft+365+defender%22&locale=en-us
```

Diğer Microsoft Defender güvenlik ürünleriyle ilgili yeniliklerle ilgili daha fazla bilgi için bkz:

- [Office 365 için Microsoft Defender’daki yenilikler](../office-365-security/whats-new-in-defender-for-office-365.md)
- [Uç Nokta için Microsoft Defender’daki yenilikler](../defender-endpoint/whats-new-in-microsoft-defender-endpoint.md)
- [Kimlik için Microsoft Defender'daki Kimlik için Microsoft Defender](/defender-for-identity/whats-new)
- [Microsoft Defender for Cloud Apps'daki Microsoft Defender for Cloud Apps](/cloud-app-security/release-notes)

Ayrıca ürün güncelleştirmelerini ve önemli bildirimleri ileti merkezi aracılığıyla [da alabilirsiniz](https://admin.microsoft.com/Adminportal/Home#/MessageCenter). 



## <a name="march-2022"></a>Mart 2022

- (Önizleme) Olay sırası, araştırmanıza yardımcı olmak için tasarlanmış çeşitli özelliklerle geliştirilmiştir. Geliştirmeler arasında kimliğine veya adına göre olayları arama, özel bir zaman aralığı belirtme gibi özellikler yer almaktadır.

## <a name="december-2021"></a>Aralık 2021

- (GA) Tablo `DeviceTvmSoftwareEvidenceBeta` , belirli bir yazılımın cihazda nerede algılandığından dair kanıtı görüntülemeniz için gelişmiş aramada kısa vadeli olarak eklenmiştir.

## <a name="november-2021"></a>Kasım 2021

- (Önizleme) Uygulamaları otomatik olarak kullanmak için Bulut için Defender yönetimi eklenti özelliği artık tüm Microsoft 365 Defender. Uygulama yönetimi, Microsoft kimlik doğrulama API'leri aracılığıyla microsoft veri erişim izni Microsoft 365 OAuth özelliği Graph sağlar. Uygulama yönetimi, bu uygulamaların ve kullanıcılarının Microsoft 365'te depolanan hassas verilerinize nasıl erişerek, bunları kullanma ve paylaşma konusunda eyleme  edilebilir içgörüler ve otomatik ilke uyarıları ve eylemleri aracılığıyla tam görünürlük, düzeltme ve yönetim sağlar. [Uygulama yönetimi hakkında daha fazla bilgi öğrenin](/cloud-app-security/app-governance-manage-app-governance).
- (Önizleme) Gelişmiş [av sayfası](advanced-hunting-overview.md) artık çok sekmeli destek, akıllı kaydırma, akıcı şema sekmeleri, sorgular için hızlı düzenleme seçenekleri, sorgu kaynak kullanım göstergesi ve sorguyu daha sorunsuz ve ince ayar kolaylaştırmak için diğer iyileştirmeler içerir.
- (Önizleme) Artık araştırmanız gereken [yeni veya](advanced-hunting-link-to-incident.md) mevcut bir olayda gelişmiş arama sorgusu sonuçlarından etkinlikleri veya kayıtları eklemek için olay özelliği bağlantısını kullanabilirsiniz.

## <a name="october-2021"></a>Ekim 2021

- (GA) Gelişmiş avlarda [CloudAppEvents tablosuna daha fazla sütun](advanced-hunting-cloudappevents-table.md) eklenmiştir. Artık , `AccountType`, `IsExternalUser`, `IsImpersonated`ve `IPTags`sorgularınızı `IPCategory``UserAgentTags` dahil etmek için kullanabilirsiniz.

## <a name="september-2021"></a>Eylül 2021

- (GA) Office 365 için Microsoft Defender verilerini veri akışı API'sinde Microsoft 365 Defender veri akışı API'sinde kullanılabilir. Akış API'sinde desteklenen etkinlik türleri'nin Microsoft 365 Defender [ve durumlarını görebilirler](supported-event-types.md).
- (GA) Office 365 için Microsoft Defender gelişmiş avda kullanılabilen veriler artık genel olarak kullanılabilir.
- (GA) Kullanıcı hesaplarına olay ve uyarı atama

  Bir olayı ve bu olayla ilişkili tüm uyarıları, Ata **:** hesabından bir olayın Olayları yönet bölmesinde veya uyarının Yönet uyarı bölmesindeki kullanıcı hesabına atekleyebilirsiniz. 

## <a name="august-2021"></a>Ağustos 2021

- (Önizleme) Office 365 için Microsoft Defender avda kullanılabilen veri

  E-posta tablolarında yer alan yeni sütunlar, gelişmiş arama kullanarak daha kapsamlı soruşturmalar için e-posta tabanlı tehditlerle ilgili daha fazla içgörü sağlar. Artık E-posta `AuthenticationDetails` Olayları'na, [](./advanced-hunting-emailevents-table.md)`FileSize` [EmailAttachmentInfo](./advanced-hunting-emailattachmentinfo-table.md)`ThreatTypes` `DetectionMethods` ve [EmailPostDeliveryEvents tablolarına sütun](./advanced-hunting-emailpostdeliveryevents-table.md) olabilirsiniz.

- (Önizleme) Olay grafiği

  Bir **Graph** Özet sekmesindeki yeni sekmede saldırının tüm kapsamı, saldırının zaman içinde ağınıza nasıl yay başladığı, ilk kez nasıl başladığı ve saldırgan nereye gittiğini görebilirsiniz.

## <a name="july-2021"></a>Temmuz 2021

- [Professional hizmetleri kataloğu](https://sip.security.microsoft.com/interoperability/professional_services)

  Desteklenen iş ortağı bağlantılarıyla platformun algılama, soruşturma ve tehdit zekası özelliklerini geliştirin.

## <a name="june-2021"></a>Haziran 2021

- (Önizleme) [Tehdit etiketleri başına raporları görüntüleme](threat-analytics.md#view-reports-per-threat-tags)

  Tehdit etiketleri belirli tehdit kategorilerine odaklanmanıza ve en uygun raporları gözden geçirmenıza yardımcı olur.

- (Önizleme) [Akış API'si](../defender-endpoint/raw-data-export.md)

  Microsoft 365 Defender Gelişmiş Arama aracılığıyla etkinlik Hub'ları ve/veya Azure depolama hesabına tüm etkinliklerin akışını destekler.

- (Önizleme) [Gelişmiş avda harekete geç](advanced-hunting-take-action.md)

  Gelişmiş aramalarda bulunan tehditlere veya tehditlere karşı hızlı bir şekilde [tehdit veya tehditlere karşı koruma sağlar](advanced-hunting-overview.md).

- (Önizleme) [Portal içinde şema başvurusu](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)

  Doğrudan güvenlik merkezinde gelişmiş av şeması tabloları hakkında bilgi edinebilirsiniz. Tablo ve sütun açıklamalarına ek olarak, bu başvuru desteklenen olay türlerini (`ActionType` değerleri) ve örnek sorguları da içerir.

- (Önizleme) [DeviceFromIP() işlevi](advanced-hunting-devicefromip-function.md)

  Belirli bir zaman aralığında belirli bir IP adresine veya adresine hangi cihazlara atanmış olduğu hakkında bilgi edinebilirsiniz.

## <a name="may-2021"></a>Mayıs 2021

- [Portalda yeni Microsoft 365 Defender sayfası](https://techcommunity.microsoft.com/t5/microsoft-365-defender/easily-find-anomalies-in-incidents-and-alerts/ba-p/2339243)

  Saldırıya ilişkin bağlam için gelişmiş bilgiler sağlar. Hangi diğer tetiklenen uyarının geçerli uyarıya ve dosyalar, kullanıcılar ve posta kutuları da dahil olmak üzere saldırıya katılan tüm etkilenen varlıklara ve etkinliklere neden olduğunuabilirsiniz. Daha [fazla bilgi için Uyarıları](/microsoft-365/security/defender/investigate-alerts) araştırma'ya bakın.

- [Yeni portalda olaylar ve uyarılar için Microsoft 365 Defender grafiği](https://techcommunity.microsoft.com/t5/microsoft-365-defender/new-alert-page-for-microsoft-365-defender-incident-detections/ba-p/2350425)

  Tek bir olay için birden fazla uyarı olup olmadığını veya kuruluş birkaç farklı olayla saldırıya karşı saldırıda olup olmadığını belirler. Daha [fazla bilgi için bkz. Olayları](/microsoft-365/security/defender/incident-queue) önceliklendirme.

## <a name="april-2021"></a>Nisan 2021

- Microsoft 365 Defender

  Gelişmiş [Microsoft 365 Defender portalı](https://security.microsoft.com) kullanılabilir. Bu yeni deneyim, tek bir portalda Uç nokta, Office 365 için Defender Defender for Identity ve daha fazlası için Defender'ı bir araya getirir. Burası, güvenlik denetimlerinizi yönetmek için yeni bir evdir. [Nelerin yeni olduğunu öğrenin](./microsoft-365-defender.md#the-microsoft-365-defender-portal).

- [Microsoft 365 Defender çözümleme raporu](threat-analytics.md)

  Tehdit analizleri, etkin saldırılara yanıt verme ve etkisini en aza indirmeye yardımcı olur. Ayrıca, yeni çözümler tarafından engellenmiş saldırı Microsoft 365 Defender ve daha fazla maruz kalma riskini azaltan ve onları daha fazla güvenlik için önleyen eylemler gerçekleştirin. Birleşik güvenlik deneyiminin bir parçası olarak tehdit çözümlemeleri, Uç Nokta için Microsoft Defender E5 lisans sahipleri için Office Microsoft Defender'da kullanılabilir.

## <a name="march-2021"></a>Mart 2021

- [CloudAppEvents tablosu](advanced-hunting-cloudappevents-table.md)

  Bulut uygulamaları ve hizmetleriyle ilgili çeşitli bulut uygulamaları ve hizmetlerinde yer alan olaylar hakkında bilgi Microsoft Cloud App Security. Bu tablo, daha önce tabloda kullanılabilen bilgileri de `AppFileEvents` içerir.

