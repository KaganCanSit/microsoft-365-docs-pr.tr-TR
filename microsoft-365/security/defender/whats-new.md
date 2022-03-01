---
title: Microsoft 365 Defender'daki Microsoft 365 Defender
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
ms.openlocfilehash: edaa7398b8d3213479c9b81af248b928f7b3f3e0
ms.sourcegitcommit: f8267a0860de62dbd53ebb8a151a8e71a8ccda6a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2022
ms.locfileid: "63016627"
---
# <a name="whats-new-in-microsoft-365-defender"></a>Microsoft 365 Defender'daki Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

> Bu deneyimi Microsoft 365 Defender? Bunu bir [laboratuvar ortamında değerlendirin veya](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) [üretimde pilot projenizi çalıştırın](m365d-pilot.md?ocid=cx-evalpilot).

Aşağıdaki özellikler, Microsoft 365 Defender'in en son sürümüne önizlemede veya genel olarak (GA) Microsoft 365 Defender.

RSS akışı: Bu sayfa güncelleştirildiğinde, akış okuyucuya aşağıdaki URL'yi kopyalayıp yapıştırarak bilgi alın:

```http
https://docs.microsoft.com/api/search/rss?search=%22Lists+the+new+features+and+functionality+in+Microsoft+365+defender%22&locale=en-us
```

Diğer Microsoft Defender güvenlik ürünleriyle ilgili yeniliklerle ilgili daha fazla bilgi için bkz:

- [Office 365 için Microsoft Defender'daki Office 365](../office-365-security/whats-new-in-defender-for-office-365.md)
- [Uç Nokta için Microsoft Defender'daki güncelleştirmeler](../defender-endpoint/whats-new-in-microsoft-defender-endpoint.md)
- [Identity için Microsoft Defender'daki güncelleştirmeler](/defender-for-identity/whats-new)
- [Bulut Uygulamaları için Microsoft Defender'daki güncelleştirmeler](/cloud-app-security/release-notes)

Ayrıca ürün güncelleştirmelerini ve önemli bildirimleri ileti merkezi aracılığıyla [da alabilirsiniz](https://admin.microsoft.com/Adminportal/Home#/MessageCenter). 

## <a name="december-2021"></a>Aralık 2021

- (GA) Tablo `DeviceTvmSoftwareEvidenceBeta` , belirli bir yazılımın cihazda nerede algılandığından dair kanıtı görüntülemeniz için gelişmiş aramada kısa vadeli olarak eklenmiştir.

## <a name="november-2021"></a>Kasım 2021

- (Önizleme) Bulut Uygulamaları için Defender'a uygulama yönetimi eklenti özelliği şu anda Microsoft 365 Defender. Uygulama yönetimi, Microsoft kimlik doğrulama API'leri aracılığıyla microsoft veri erişim izni Microsoft 365 OAuth özelliği Graph sağlar. Uygulama yönetimi, bu uygulamaların ve kullanıcılarının Microsoft 365'te depolanan hassas verilerinize nasıl erişerek, bunları kullanma ve paylaşma konusunda eyleme  edilebilir içgörüler ve otomatik ilke uyarıları ve eylemleri aracılığıyla tam görünürlük, düzeltme ve yönetim sağlar. [Uygulama yönetimi hakkında daha fazla bilgi öğrenin](/cloud-app-security/app-governance-manage-app-governance).
- (Önizleme) Gelişmiş [av sayfası](advanced-hunting-overview.md) artık çok sekmeli destek, akıllı kaydırma, akıcı şema sekmeleri, sorgular için hızlı düzenleme seçenekleri, sorgu kaynak kullanım göstergesi ve sorguyu daha sorunsuz ve ince ayar kolaylaştırmak için diğer iyileştirmeler içerir.
- (Önizleme) Artık araştırmanız gereken [yeni veya](advanced-hunting-link-to-incident.md) mevcut bir olayda gelişmiş arama sorgusu sonuçlarından etkinlikleri veya kayıtları eklemek için olay özelliği bağlantısını kullanabilirsiniz.

## <a name="october-2021"></a>Ekim 2021

- (GA) Gelişmiş avlarda [CloudAppEvents tablosuna daha fazla sütun](advanced-hunting-cloudappevents-table.md) eklenmiştir. Artık , `AccountType`, `IsExternalUser`, `IsImpersonated`ve `IPTags`sorgularınızı `IPCategory``UserAgentTags` dahil etmek için kullanabilirsiniz.

## <a name="september-2021"></a>Eylül 2021

- (GA) Microsoft Defender for Office 365 event data is available in the Microsoft 365 Defender streaming API. Akış API'sinde desteklenen etkinlik türleri'nin Microsoft 365 Defender [ve durumlarını görebilirler](supported-event-types.md).
- (GA) Gelişmiş av Office 365 için Microsoft Defender artık genel olarak kullanılabilir.
- (GA) Kullanıcı hesaplarına olay ve uyarı atama

  Bir olayı ve bu olayla ilişkili tüm uyarıları, Ata **:** hesabından bir olayın Olayları yönet bölmesinde veya uyarının Yönet uyarı bölmesindeki kullanıcı hesabına atekleyebilirsiniz. 

## <a name="august-2021"></a>Ağustos 2021

- (Önizleme) Gelişmiş avlarda Office 365 için Microsoft Defender

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

  Gelişmiş [Microsoft 365 Defender portalı](https://security.microsoft.com) kullanılabilir. Bu yeni deneyim, tek bir portalda Uç Nokta için Defender, Office 365 Için Defender, Kimlik için Defender ve daha fazlasını bir araya getirir. Burası, güvenlik denetimlerinizi yönetmek için yeni bir evdir. [Nelerin yeni olduğunu öğrenin](./microsoft-365-defender.md#the-microsoft-365-defender-portal).

- [Microsoft 365 Defender çözümleme raporu](threat-analytics.md)

  Tehdit analizleri, etkin saldırılara yanıt verme ve etkisini en aza indirmeye yardımcı olur. Ayrıca, yeni çözümler tarafından engellenmiş saldırı Microsoft 365 Defender ve daha fazla maruz kalma riskini azaltan ve onları daha fazla güvenlik için önleyen eylemler gerçekleştirin. Birleşik güvenlik deneyiminin bir parçası olarak tehdit çözümlemeleri, artık Diğer E5 lisans sahiplerine Yönelik Uç Nokta için Microsoft Defender ve Office için Microsoft Defender'da kullanılabilir.

## <a name="march-2021"></a>Mart 2021

- [CloudAppEvents tablosu](advanced-hunting-cloudappevents-table.md)

  Bulut uygulamaları ve hizmetleriyle ilgili çeşitli bulut uygulamaları ve hizmetlerinde yer alan olaylar hakkında bilgi Microsoft Cloud App Security. Bu tablo, daha önce tabloda kullanılabilen bilgileri de `AppFileEvents` içerir.

## <a name="february-2021"></a>Şubat 2021

- (Önizleme) İyileştirilmiş [Microsoft 365 Defender portalı ( artıkhttps://security.microsoft.com)](https://security.microsoft.com) genel önizlemede kullanılabilir. Bu yeni deneyim, 2013 için Uç Nokta ve Office 365 Defender'ı da merkeze getirir. [Neler değişti hakkında daha fazla bilgi edinmek için](microsoft-365-defender.md#the-microsoft-365-defender-portal):

- **[(Önizleme) Microsoft 365 Defender API'ler](api-overview.md)** - En üst düzey MICROSOFT 365 DEFENDER API'ler paylaşılan olay ve gelişmiş tablolara dayalı olarak iş akışlarını otomatikleştirmenize olanak sağlar.
