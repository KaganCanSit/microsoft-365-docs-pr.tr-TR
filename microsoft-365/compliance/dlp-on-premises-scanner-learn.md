---
title: Şirket içi Microsoft 365 önleme hakkında bilgi
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
description: Microsoft 365 kaybı önlemeye yönelik tarayıcı, bu dosyalar için dosya etkinliklerini ve koruyucu eylemleri şirket içi dosya paylaşımlarına ve dosya klasörleriyle belge kitaplıklarına SharePoint genişlettir. Dosyalar Azure Information Protection (AIP) tarayıcısı tarafından taranır ve korunur
ms.openlocfilehash: c696d4c4e8504d07ce69554c6ff52f264b8ba491
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988615"
---
# <a name="learn-about-the-microsoft-365-data-loss-prevention-on-premises-scanner"></a>Şirket içi Microsoft 365 önleme hakkında bilgi

Şirket içi tarayıcı, çeşitli hizmetler genelinde hassas öğeleri keşfetmek ve korumak için kullanabileceğiniz Microsoft 365 veri kaybını önleme (DLP) özellik paketinin bir Microsoft 365 vardır. Microsoft'un tüm DLP teklifleri hakkında daha fazla bilgi için bkz. [Veri kaybını önleme hakkında bilgi.](dlp-learn-about-dlp.md)

**DLP** şirket içi tarayıcı, sızdırılan hassas öğeler için dosya paylaşımlarında ve SharePoint belge kitaplıklarında ve klasörlerde şirket içi veri yerinde gezinerek, sızdırılan öğeler için bu risklere neden olabilir veya uyumluluk ilkesi ihlali riski oluşturur. Bu, hassas öğelerin düzgün kullanılmış ve korunarak korunmasını sağlamak ve onları tehlikeye atacak riskli davranışları önlemeye yardımcı olmak için ihtiyacınız olan görünürlük ve denetimi sağlar. DLP şirket içi tarayıcı, yerleşik veya özel hassas bilgi türlerini, duyarlılık [](sensitive-information-type-entity-definitions.md) etiketlerini veya dosya [](create-a-custom-sensitive-information-type.md) özelliklerini [kullanarak](sensitivity-labels.md) hassas bilgileri algılar. Kullanıcıların hassas öğelerle yaptıklarına ilişkin bilgiler etkinlik gezgininde görünür hale gelir [](data-classification-activity-explorer.md) ve DLP ilkeleri aracılığıyla bu öğeler üzerinde koruyucu işlemler [gerçekleştirebilirsiniz](create-test-tune-dlp-policy.md).

## <a name="the-dlp-on-premises-scanner-relies-on-azure-information-protection-scanner"></a>DLP şirket içi tarayıcı, Azure Information Protection tarayıcısını dayandırıyor

DLP şirket içi tarayıcısı, hassas öğeleri izlemek, etiketlemek ve korumak için Azure Information Protection (AIP) tarayıcının tam uygulamasına dayandır. AIP tarayıcısını iyi biliyorsanız, bu tarayıcıya kendinizi tanımanız önemle önerilir. Şu makalelere bakın:

- [Azure Information Protection nedir?](/azure/information-protection/what-is-information-protection)
- [Azure Information Protection birleşik etiketleme tarayıcısı nedir?](/azure/information-protection/deploy-aip-scanner)
- [Azure Information Protection birleşik etiketleme tarayıcısını yükleme ve dağıtma gereksinimleri](/azure/information-protection/deploy-aip-scanner-prereqs)
- [Öğretici: Azure Information Protection (AIP) birleşik etiketleme tarayıcısını yükleme](/azure/information-protection/tutorial-install-scanner)
- [Azure Information Protection birleşik etiketleme tarayıcısını yapılandırma ve yükleme](/azure/information-protection/deploy-aip-scanner-configure-install)
- [Azure Information Protection birleşik etiketleme istemcisi - Sürüm sürüm geçmişi ve destek ilkesi](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)

## <a name="dlp-on-premises-scanner-actions"></a>DLP şirket içi tarayıcı eylemleri

DLP şirket içi tarayıcı şu dört yöntemden birini kullanarak dosyaları algılar:

- hassas bilgi türleri
- duyarlılık etiketleri
- dosya uzantısı
- Yalnızca çalışma dosyalarında Office belge özellikleri 

Algılanan bir dosya sızdırılmışsa veya uyumluluk ilkesi ihlaline neden olursa olası bir risk oluşturduğunda, DLP şirket içi tarayıcısı bu dört işlemden birini gerçekleştirebilirsiniz.

|Eylem |Açıklama  |
|---------|---------|
|**Bu kişilerin şirket içi tarayıcıda depolanan dosyaya erişmesini engelle - Herkes** | Zorunlu kılınan bu eylem, içerik sahibi , öğeyi son değiştiren hesap ve yönetici dışındaki tüm hesaplara erişimi engeller. Bunu yapmak için dosya sahibi, depo sahibi (İçerik tarama işinde depo sahibi ayarla ayarında ayarlanmış), son değiştirici (yalnızca SharePoint'ta tanımlanır) ve yönetici dışındaki [](/azure/information-protection/deploy-aip-scanner-configure-install#use-a-data-loss-prevention-dlp-policy-public-preview) dosya düzeyinde tüm hesapları NTFS/SharePoint izinlerinden kaldırabilirsiniz. Tarayıcı hesabına dosya üzerinde FC hakları da verildi.|
|**Bu kişilerin şirket içi tarayıcıda depolanan dosyaya erişmesini engelle - kuruluş genelinde (genel) erişimi engelleme**    |Zorunlu kılınan bu eylem, dosya erişim denetim listesinden (ACL) **_Everyone_*_, _*_NT AUTHORITY\authenticated users_*_, ve _*_Domain Users_** SID'lerini kaldırır. Yalnızca dosya veya üst klasöre açıkça hak verilmiş olan kullanıcılar ve gruplar dosyaya erişim iznine sahip olabilir.|
|**Dosya üzerinde izinleri ayarlama**|Zorunlu kılınan bu eylem, dosyayı üst klasörünün izinlerini devralmaya zorlar. Varsayılan olarak, bu eylem yalnızca üst klasördeki izinler dosyada önceden var olan izinlerden daha kısıtlayıcı olursa uygulanır. Örneğin, dosyada ACL yalnızca belirli kullanıcılara_ izin verecek şekilde ayarlanmışsa ve üst klasör ***_*_Domain Users_ _ grubuna izin verecek şekilde yapılandırılmışsa, üst klasör izinleri dosya tarafından devralınmaz *. Üst izinler daha az kısıtlayıcı olsa bile _* Inherit seçeneğini seçerek bu davranışı geçersiz kılabilirsiniz**.|
|**Dosyayı uygun olmayan konumdan kaldırma**|Zorunlu kılınan bu eylem, özgün dosyayı .txt uzantısına sahip bir saplama dosyasıyla değiştirir ve özgün dosyanın bir kopyasını karantina klasörüne yapıştırır. 

## <a name="whats-different-in-the-on-premises-scanner"></a>Şirket içi tarayıcıda nelerin farklı olduğu

Şirket içi tarayıcıyı incelemeden önce dikkat etmek gereken birkaç ek kavram vardır.

### <a name="aip-repositories-and-content-scan-jobs"></a>AIP depoları ve içerik tarama işleri

Bir AIP içerik tarama işleri oluşturmanız ve DLP altyapısı tarafından değerlendirilmesini istediğiniz dosyaları barındıran depoları tanımlamalı. Oluşturulan AIP içerik tarama işsinde DLP kurallarını etkinleştirip etkinleştirmeyi sağlar.

### <a name="policy-tips"></a>İlke ipuçları

[İlke](use-notifications-and-policy-tips.md) ipuçları şirket içi tarayıcıda kullanılamaz.


### <a name="viewing-dlp-on-premises-scanner-events"></a>DLP şirket içi tarayıcı olaylarını görüntüleme

DLP şirket içi tarayıcı verilerini M365 Uyumluluk Merkezi etkinlik gezgininde [görüntülirsiniz](data-classification-activity-explorer.md). 

## <a name="next-steps"></a>Sonraki adımlar

Artık DLP şirket içi tarayıcı hakkında bilgi edin öğrendiğinize göre, sonraki adımlarınız:

1. [DLP şirket içi tarayıcısını çalışmaya başlama](dlp-on-premises-scanner-get-started.md)
2. [DLP şirket içi tarayıcısını kullanma](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft veri kaybı önlemeye şirket içi tarayıcı ile çalışmaya başlama](dlp-on-premises-scanner-get-started.md)
- [Microsoft veri kaybı önleme şirket içi tarayıcısını kullanma](dlp-on-premises-scanner-use.md)
- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
- [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)
- [Etkinlik gezgini ile çalışmaya başlama](data-classification-activity-explorer.md)