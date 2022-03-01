---
title: Şirket içi Microsoft 365 kaybı önleme ile çalışmaya başlama
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: how-to
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Şirket içi Microsoft 365 önlemeyi ayarlama
ms.openlocfilehash: 1586489389931b3df19a1c84f0ae49ac7ff9c099
ms.sourcegitcommit: d37fce3b708ea5232b4102fd0e693f4bf17a8948
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/21/2022
ms.locfileid: "63014120"
---
# <a name="get-started-with-the-data-loss-prevention-on-premises-scanner"></a>Şirket içi tarayıcıda veri kaybı önlemeye başlama

Bu makale, şirket içi tarayıcıda veri kaybı önleme Microsoft 365 önkoşullarda ve yapılandırmada size yol gösterir.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="skusubscriptions-licensing"></a>SKU/abonelik lisansı

Şirket içi tarayıcıya başlamadan önce, Microsoft 365 [aboneliğinizi ve tüm](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) eklentileri onaylamanız gerekir. DLP kurallarını ayarleyen yönetici hesabına aşağıdaki lisanslardan biri atanabilir:

- Microsoft 365 E5
- Microsoft 365 E5 Uyumluluk
- Microsoft 365 E5 Koruma ve & Yönetimi 


Tüm lisans ayrıntıları için bkz. [güvenlik Microsoft 365 uyumluluğu için lisans & kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

> [!IMPORTANT]
> Dosyalar ekleyerek veya dosyaları tüketerek taranan konuma katkıda bulunan tüm kullanıcıların, yalnızca tarayıcı kullanıcısını değil, bir lisansının da sahip olduğu gerekir.

### <a name="permissions"></a>İzinler

DLP şirket içi tarayıcıdan gelen veriler Etkinlik [Gezgini'nde görüntülenebilirsiniz](data-classification-activity-explorer.md). Etkinlik gezginine izin veren dört rol vardır ve verilere erişim için kullanmakta olduğunuz hesabın bunlardan herhangi birinin üyesi olması gerekir.

- Genel yönetici
- Uyumluluk yöneticisi
- Güvenlik yöneticisi
- Uyumluluk veri yöneticisi

#### <a name="roles-and-role-groups-in-preview"></a>Önizlemede Roller ve Rol Grupları

Önizlemede, erişim denetimlerinize ince ayar yapmak için test etmek için deney erişiminiz olan roller ve rol grupları vardır.

İşte önizlemede olan Microsoft Bilgi Koruması (MIP) rollerinin listesi. Bu roller hakkında daha fazla bilgi edinmek [için Güvenlik ve Uyumluluk Merkezi'& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Bilgi Koruması Yöneticisi
- Bilgi Koruma Analisti
- Bilgi Koruma Koruma Koruma Koruması
- Bilgi Koruma Okuyucusu

Önizlemede olan MIP rol gruplarının listesi burada ve ve şekildedir. Bu gruplar hakkında daha fazla bilgi [edinmek için Güvenlik ve Uyumluluk Merkezi'nde & bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center).

- Bilgi Koruması
- Bilgi Koruması Yöneticileri
- Bilgi Koruma Analistleri
- Bilgi Koruma Koruma KorumaLarı
- Bilgi Koruma Okuyucuları

### <a name="dlp-on-premises-scanner-prerequisites"></a>DLP şirket içi tarayıcı önkoşulları

- Azure Information Protection (AIP) tarayıcı, DLP ilkesi eşleştirmesi ve ilke zorlaması sunar. Tarayıcı AIP istemcisinin bir parçası olarak yüklenir, dolayısıyla yüklemeniz AIP'nin, AIP istemcisinin ve AIP birleşik etiket tarayıcısının tüm önkoşullarını karşılaması gerekir.
- AIP istemcisini ve tarayıcıyı dağıtın. Daha fazla bilgi [için AIP](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) birleşik etiketleme istemcisini ve [] yükleme için bkz. [Azure Information Protection birleşik etiketleme tarayıcısını yapılandırma ve yükleme](/azure/information-protection/deploy-aip-scanner-configure-install).
- Tüm algılama kurallarınız yalnızca hassas bilgi türlerini temel aldı olsa bile, kiracıda en az bir etiket ve ilke yayımlanması gerekir.

## <a name="deploy-the-dlp-on-premises-scanner"></a>DLP şirket içi tarayıcıyı dağıtma

1. [AIP birleşik etiketleme istemcisini yükleme altında yer alan yordamları izleyin](/azure/information-protection/rms-client/install-unifiedlabelingclient-app). 
2. Tarayıcı yüklemesini tamamlamak [için Azure Information Protection](/azure/information-protection/deploy-aip-scanner-configure-install) birleşik etiketleme tarayıcısını yapılandırma ve yükleme yordamlarını izleyin.
    1. Ağ bulma iş yapılandırması isteğe bağlı bir adımdır. Bunu atlayıp içerik tarama işinizin içinde taranacak belirli depolar tanımlayabilirsiniz.
    2. İçerik tarama işi oluşturmalı ve DLP altyapısı tarafından değerlendirilmesi gereken dosyaları barındıran depoları belirtebilirsiniz.
    3. Oluşturulan İçerik tarama işsinde DLP kurallarını etkinleştirin ve doğrudan DLP zorlama  aşamasına gitmek istemiyorsanız Zorla seçeneğini Kapalı olarak ayarlayın.
3. İçerik tarama işinin doğru kümeye atan olduğunu doğrulayın. Yine de içerik tarama işi oluşturmadıysanız yeni bir iş oluşturun ve bu işi tarayıcı düğümlerini içeren kümeye attayın.

4. Bağlan [Azure Portal'daki Azure Information Protection](https://portal.azure.com/#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/scannerProfilesBlade) uzantısına tıklayın ve depolarınızı taramayı gerçekleştirecek içerik tarama işine ekleyin.

5. Taramanızı çalıştırmak için aşağıdakilerden birini yapın:
    1. tarayıcı zamanlamayı ayarlama
    1. portalda el **ile Şimdi** Tara seçeneğini kullanma
    1. veya **Start-AIPScan** PowerShell cmdlet'ini çalıştırma

   > [!IMPORTANT]
   > Tarayıcının varsayılan olarak depoda değişiklikli bir tarama çalıştırıldığını ve dosya değişmedikçe veya tam bir yeniden tarama başlatmadınız sürece, önceki tarama döngüsünde zaten taranmış olan dosyaların atlanacaklarını unutmayın. Tam yeniden can, kullanıcı arabiriminde tüm dosyaları yenidencan seçeneği kullanılarak veya **Start-AIPScan-Reset çalıştırarak başlatabilirsiniz**.

6.  Uyumluluk [Merkezi'nde Veri](https://compliance.microsoft.com/datalossprevention?viewid=policies) kaybı önleme Microsoft 365 açın.

7. **İlke oluştur'a** seçin ve bir test DLP ilkesi oluşturun. [İlke oluştururken yardıma ihtiyacınız olursa bkz. Şablondan DLP](create-a-dlp-policy-from-a-template.md) ilkesi oluşturma. Bu özelliği rahat hale gelene kadar testte çalıştırmayı emin olun. İlkeniz için şu parametreleri kullanın:
    1. Gerekirse, DLP şirket içi tarayıcı kuralının kapsamını belirli konumlarda açık kullanın. Konumların kapsamını **Herkes olarak** **kullanırsanız**, tarayıcı tarafından taranan tüm dosyalar DLP kuralı eşleştirme ve zorlamaya tabi olur.
    1. Konumları belirtirken dışlama veya ekleme listesini kullanabilirsiniz. Kuralın yalnızca ekleme listesinde listelenen desenlerden birini eşleşen yollarla veya ekleme listesinde listelenen desenle eşleşen dosyalar dışında tüm dosyalarla ilgili olduğunu tanımlayabilirsiniz. Hiçbir yerel yol desteklenmiyor. Geçerli yollara bazı örnekler:
      - \\\server\share
      - \\\server\share\folder1\subfolderabc
      - \*\\klasör1
      - \*gizli\*.docx
      - \*gizlidir\*.\*
      - https:// sp2010.local/sites/HR
      - \*https:///İk 
    3. Kabul edilemez değer kullanım örneklerini aşağıda verilmiştir:
      - \*
      - \*\\a
      - Aaa
      - c:\
      - C:\test

> [!IMPORTANT]
> Dışlama listesi, eklemeler listesine göre önceliklidir.

### <a name="viewing-dlp-on-premises-scanner-alerts-in-dlp-alerts-management-dashboard"></a>DLP Uyarıları Yönetimi panosunda DLP şirket içi tarayıcı uyarılarını görüntüleme

1. Uyumluluk [Merkezi'nde Veri](https://compliance.microsoft.com/datalossprevention?viewid=policies) kaybı önleme sayfasını Microsoft 365 **Uyarılar'ı seçin**.

2. Uç Nokta DLP [ilkelerinize yönelik uyarıları görüntülemek üzere DLP](dlp-configure-view-alerts-policies.md) ilkelerinizin uyarılarını yapılandırma ve görüntüleme makalesinde yer alan yordamlara bakın.

### <a name="viewing-dlp-on-premises-scanner-in-activity-explorer-and-audit-log"></a>Etkinlik gezgininde ve denetim günlüğünde DLP şirket içi tarayıcıyı görüntüleme

> [!NOTE]
> Şirket içi tarayıcı denetimin etkinleştirilmesi gerekir. Bu Microsoft 365 denetim varsayılan olarak etkindir.

1. Uyumluluk merkezinde [etki alanınız](https://compliance.microsoft.com/dataclassification?viewid=overview) için Veri sınıflandırma sayfasını açın Microsoft 365 gezgini'ni seçin.

2. Şirket içi tarayıcı [konumlar için tüm verilere](data-classification-activity-explorer.md) erişmek ve bu konumlara filtre uygulama için Etkinlik gezgini ile çalışmaya başlama'daki yordamlara bakın.

3. Uyumluluk [merkezinde Denetim günlüğünü açın](https://security.microsoft.com/auditlogsearch). DLP kuralı eşleşmeleri Denetim günlüğü kullanıcı arabiriminde kullanılabilir veya [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) PowerShell tarafından erişilebilir 


## <a name="next-steps"></a>Sonraki adımlar
Artık şirket içi konumlar için bir test ilkesi dağıttıktan ve Etkinlik gezgininde etkinlik verilerini görüntüley uygun olduğunuz için, hassas öğelerinizi koruyan DLP ilkelerini oluşturan bir sonraki adımınıza geçebilirsiniz.

- [DLP şirket içi kullanma](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>Ayrıca bkz.

- [DLP şirket içi tarayıcı hakkında bilgi](dlp-on-premises-scanner-learn.md)
- [DLP şirket içi tarayıcıyı kullanma](dlp-on-premises-scanner-use.md)
- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
- [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)
- [Etkinlik gezgini ile çalışmaya başlama](data-classification-activity-explorer.md)
- [Microsoft 365 aboneliği](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
