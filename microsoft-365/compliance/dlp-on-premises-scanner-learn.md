---
title: Şirket içi tarayıcıda veri kaybını önleme hakkında bilgi edinme
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Şirket içi veri kaybını önleme tarayıcısı, bu dosyalar için dosya etkinliklerinin ve koruyucu eylemlerin izlenmesini şirket içi dosya paylaşımlarına ve SharePoint klasörlerine ve belge kitaplıklarına genişletir. Dosyalar Azure Information Protection (AIP) tarayıcısı tarafından taranır ve korunur
ms.openlocfilehash: 8edf472fe65380b708a833864ccceedadb240191
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629827"
---
# <a name="learn-about-the-data-loss-prevention-on-premises-scanner"></a>Şirket içi veri kaybı önleme tarayıcısı hakkında bilgi edinin

Şirket içi veri kaybını önleme tarayıcısı, Microsoft 365 hizmetlerindeki hassas öğeleri bulmak ve korumak için kullanabileceğiniz Microsoft Purview Veri Kaybı Önleme (DLP) özellik paketinin bir parçasıdır. Microsoft'un tüm DLP teklifleri hakkında daha fazla bilgi için bkz. [Veri kaybını önleme hakkında bilgi edinin](dlp-learn-about-dlp.md).

**DLP şirket içi tarayıcısı**, dosya paylaşımlarında ve SharePoint belge kitaplıklarında ve klasörlerde, sızdırılırsa kuruluşunuz için risk oluşturacak veya uyumluluk ilkesi ihlali riski oluşturacak hassas öğeler için bekleyen şirket içi verilerde gezinir. Bu, hassas öğelerin düzgün kullanıldığından ve korunduğundan emin olmak ve bunları tehlikeye atabilecek riskli davranışları önlemeye yardımcı olmak için ihtiyacınız olan görünürlüğü ve denetimi sağlar. DLP şirket içi tarayıcısı [, yerleşik](sensitive-information-type-entity-definitions.md) veya [özel hassas bilgi](create-a-custom-sensitive-information-type.md) türlerini, [duyarlılık etiketlerini](sensitivity-labels.md) veya dosya özelliklerini kullanarak hassas bilgileri algılar. Kullanıcıların hassas öğelerle yaptıklarıyla ilgili bilgiler [etkinlik gezgininde](data-classification-activity-explorer.md) görünür hale getirilir ve [DLP ilkeleri](create-test-tune-dlp-policy.md) aracılığıyla bu öğeler üzerinde koruyucu eylemler uygulayabilirsiniz.

## <a name="the-dlp-on-premises-scanner-relies-on-azure-information-protection-scanner"></a>DLP şirket içi tarayıcısı Azure Information Protection tarayıcısına dayanır

DLP şirket içi tarayıcısı, hassas öğeleri izlemek, etiketlemek ve korumak için Azure Information Protection (AIP) tarayıcısının tam uygulamasını temel alır. AIP tarayıcısını bilmiyorsanız, bu tarayıcıyı tanımanızı kesinlikle öneririz. Şu makalelere bakın:

- [Azure Information Protection nedir?](/azure/information-protection/what-is-information-protection)
- [Azure Information Protection birleşik etiketleme tarayıcısı nedir?](/azure/information-protection/deploy-aip-scanner)
- [Azure Information Protection birleşik etiketleme tarayıcısını yükleme ve dağıtma gereksinimleri](/azure/information-protection/deploy-aip-scanner-prereqs)
- [Öğretici: Azure Information Protection (AIP) birleşik etiketleme tarayıcısını yükleme](/azure/information-protection/tutorial-install-scanner)
- [Azure Information Protection birleşik etiketleme tarayıcısını yapılandırma ve yükleme](/azure/information-protection/deploy-aip-scanner-configure-install)
- [Azure Information Protection birleşik etiketleme istemcisi - Sürüm sürüm geçmişi ve destek ilkesi](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)

## <a name="dlp-on-premises-scanner-actions"></a>DLP şirket içi tarayıcı eylemleri

DLP şirket içi tarayıcısı dosyaları şu dört yöntemden biriyle algılar:

- hassas bilgi türleri
- duyarlılık etiketleri
- dosya uzantısı
- yalnızca Office dosyalarındaki özel belge özellikleri 

Algılanan bir dosya sızdırılırsa veya uyumluluk ilkesi ihlali durumunda olası bir risk oluşturduğunda, DLP şirket içi tarayıcısı bu dört eylemden birini gerçekleştirebilir.

|Eylem |Açıklama  |
|---------|---------|
|**Bu kişilerin şirket içi tarayıcıda depolanan dosyaya erişmesini engelle - Herkes** | Bu eylem uygulandığında içerik sahibi, öğeyi değiştiren son hesap ve yönetici dışındaki tüm hesaplara erişimi engeller. Bunu, dosya sahibi, depo sahibi (içerik tarama işinde depo [sahibi](/azure/information-protection/deploy-aip-scanner-configure-install#use-a-data-loss-prevention-dlp-policy-public-preview) ayarla ayarında ayarlanır), son değiştirici (yalnızca SharePoint'te tanımlanabilir) ve yönetici dışında dosya düzeyindeki NTFS/SharePoint izinlerinden tüm hesapları kaldırarak yapar. Tarayıcı hesabına dosya üzerinde FC hakları da verilir.|
|**Bu kişilerin şirket içi tarayıcıda depolanan dosyaya erişmesini engelleme - kuruluş genelinde (genel) erişimi engelleme**    |Bu eylem zorunlu kılındığında **_Everyone_*_, _*_NT AUTHORITY\authenticated users_*_ve _*_Domain Users_** SID'lerini dosya erişim denetimi listesinden (ACL) kaldırır. Yalnızca dosya veya üst klasöre açıkça hak verilmiş kullanıcılar ve gruplar dosyaya erişebilir.|
|**Dosya üzerinde izinleri ayarlama**|Bu eylem uygulandığında, dosyayı üst klasörünün izinlerini devralmaya zorlar. Varsayılan olarak, bu eylem yalnızca üst klasördeki izinler dosyadaki izinlerden daha kısıtlayıcıysa uygulanır. Örneğin, dosyadaki ACL yalnızca **_belirli kullanıcılara_ _ izin verecek şekilde ayarlanmışsa *ve üst klasör _Domain Users_ grubuna izin verecek şekilde yapılandırılmışsa**, üst klasör izinleri dosya tarafından devralınmaz.* Üst izinler daha az kısıtlayıcı olsa bile _Devral seçeneğini belirleyerek bu davranışı geçersiz kılabilirsiniz**.|
|**Dosyayı yanlış konumdan kaldırma**|Bu eylem zorunlu kılındığında, özgün dosyayı .txt uzantılı bir saplama dosyasıyla değiştirir ve özgün dosyanın bir kopyasını karantina klasörüne yerleştirir. 

## <a name="whats-different-in-the-on-premises-scanner"></a>Şirket içi tarayıcıdaki farklar

Şirket içi tarayıcıyı incelemeden önce bilmeniz gereken birkaç ek kavram vardır.

### <a name="aip-repositories-and-content-scan-jobs"></a>AIP depoları ve içerik tarama işleri

Bir AIP içerik tarama işleri oluşturmanız ve DLP altyapısı tarafından değerlendirilmesini istediğiniz dosyaları barındıran depoları tanımlamanız gerekir. Oluşturulan AIP içerik tarama işinde DLP kurallarını etkinleştirdiğinizden emin olun.

### <a name="policy-tips"></a>İlke ipuçları

[İlke ipuçları](use-notifications-and-policy-tips.md) şirket içi tarayıcıda kullanılamaz.


### <a name="viewing-dlp-on-premises-scanner-events"></a>DLP şirket içi tarayıcı olaylarını görüntüleme

DLP şirket içi tarayıcı verilerini M365 Uyumluluk Merkezi [etkinlik gezgininde](data-classification-activity-explorer.md) görüntüleyebilirsiniz. 

## <a name="next-steps"></a>Sonraki adımlar

DLP şirket içi tarayıcı hakkında bilgi edindiğinize göre, sonraki adımlarınız şunlardır:

1. [DLP şirket içi tarayıcısını kullanmaya başlama](dlp-on-premises-scanner-get-started.md)
2. [DLP şirket içi tarayıcısını kullanma](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Şirket içi veri kaybı önleme tarayıcısını kullanmaya başlama](dlp-on-premises-scanner-get-started.md)
- [Veri kaybı önleme şirket içi tarayıcısını kullanma](dlp-on-premises-scanner-use.md)
- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md)
- [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md)
- [Etkinlik gezginini kullanmaya başlama](data-classification-activity-explorer.md)
