---
title: Şirket içi tarayıcıda veri kaybını önlemeyi kullanmaya başlama
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
description: Şirket içi tarayıcıda veri kaybı önlemeyi ayarlama
ms.openlocfilehash: a1bcebfb48a502a9d7c484d266d91fe105603f84
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625445"
---
# <a name="get-started-with-the-data-loss-prevention-on-premises-scanner"></a>Şirket içi veri kaybı önleme tarayıcısını kullanmaya başlama

Bu makalede, Şirket içi Microsoft Purview veri kaybı önleme tarayıcısının önkoşulları ve yapılandırmasında size yol gösterildi.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="skusubscriptions-licensing"></a>SKU/abonelik lisanslama

DLP şirket içi tarayıcıyı kullanmaya başlamadan önce [Microsoft 365 aboneliğinizi](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) ve tüm eklentileri onaylamanız gerekir. DLP kurallarını ayarlayan yönetici hesabına aşağıdaki lisanslardan biri atanmalıdır:

- Microsoft 365 E5
- Microsoft 365 E5 Uyumluluk
- İdareyi Microsoft 365 E5 Information Protection & 


Tam lisanslama ayrıntıları için bkz. [Güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

> [!IMPORTANT]
> Taranan konuma dosya ekleyerek veya dosya kullanarak katkıda bulunan tüm kullanıcıların yalnızca tarayıcı kullanıcısına değil lisansa sahip olması gerekir.

### <a name="permissions"></a>İzinler

DLP şirket içi tarayıcıdaki veriler [Etkinlik gezgininde](data-classification-activity-explorer.md) görüntülenebilir. Etkinlik gezginine izin veren dört rol vardır; verilere erişmek için kullandığınız hesap bunlardan herhangi birinin üyesi olmalıdır.

- Genel yönetici
- Uyumluluk yöneticisi
- Güvenlik yöneticisi
- Uyumluluk veri yöneticisi

#### <a name="roles-and-role-groups-in-preview"></a>Önizlemede Roller ve Rol Grupları

Önizlemede, erişim denetimlerinizde ince ayar yapmak için test yapabileceğiniz roller ve rol grupları vardır.

Aşağıda, önizleme aşamasında olan geçerli rollerin listesi yer alır. Bunlar hakkında daha fazla bilgi edinmek için bkz [. Güvenlik & Uyumluluk Merkezi'ndeki Roller](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Information Protection Yönetici
- Information Protection Analisti
- Information Protection Araştırmacısı
- Information Protection Okuyucu

Aşağıda, önizleme aşamasında olan geçerli rol gruplarının listesi yer alır. hakkında daha fazla bilgi edinmek için bkz [. Güvenlik & Uyumluluk Merkezi'ndeki Rol grupları](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Information Protection
- Information Protection Yöneticileri
- Information Protection Analistleri
- Information Protection Araştırmacıları
- Information Protection Okuyucular

### <a name="dlp-on-premises-scanner-prerequisites"></a>DLP şirket içi tarayıcı önkoşulları

- Azure Information Protection (AIP) tarayıcısı DLP ilke eşleştirme ve ilke zorlama uygular. Tarayıcı, AIP istemcisinin bir parçası olarak yüklenir, bu nedenle yüklemenizin AIP, AIP istemcisi ve AIP birleşik etiketleme tarayıcısı için tüm önkoşulları karşılaması gerekir.
- AIP istemcisini ve tarayıcısını dağıtın. Daha fazla bilgi için [AIP birleşik etiketleme istemcisini yükleme](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) ve [], bkz. [Azure Information Protection birleşik etiketleme tarayıcısını yapılandırma ve yükleme](/azure/information-protection/deploy-aip-scanner-configure-install).
- Tüm algılama kurallarınız yalnızca hassas bilgi türlerini temel alsa bile kiracıda en az bir etiket ve ilke yayımlanmış olmalıdır.

## <a name="deploy-the-dlp-on-premises-scanner"></a>DLP şirket içi tarayıcısını dağıtma

1. [AIP birleşik etiketleme istemcisini yükleme başlığı altında yer alan](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) yordamları izleyin. 
2. Tarayıcı yüklemesini tamamlamak için [Azure Information Protection birleşik etiketleme tarayıcısını yapılandırma ve yükleme](/azure/information-protection/deploy-aip-scanner-configure-install) başlığı altında yer alan yordamları izleyin.
    1. Ağ bulma işleri yapılandırması isteğe bağlı bir adımdır. Bunu atlayabilir ve içerik tarama işinizde taranacak belirli depoları tanımlayabilirsiniz.
    2. İçerik tarama işi oluşturmanız ve DLP altyapısı tarafından değerlendirilmesi gereken dosyaları barındıran depoları belirtmeniz gerekir.
    3. Oluşturulan İçerik tarama işinde DLP kurallarını etkinleştirin ve doğrudan DLP zorlama aşamasına geçmek istemiyorsanız **Zorla** seçeneğini **Kapalı** olarak ayarlayın.
3. İçerik tarama işinizin doğru kümeye atandığını doğrulayın. Yine de içerik tarama işi oluşturmadıysanız yeni bir tane oluşturun ve tarayıcı düğümlerini içeren kümeye atayın.

4. [Azure portal'da Azure Information Protection uzantısına](https://portal.azure.com/#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/scannerProfilesBlade) bağlanın ve depolarınızı taramayı gerçekleştirecek içerik tarama işine ekleyin.

5. Taramanızı çalıştırmak için aşağıdakilerden birini yapın:
    1. tarayıcı zamanlamasını ayarlama
    1. portalda el ile **Şimdi Tara** seçeneğini kullanma
    1. veya **Start-AIPScan** PowerShell cmdlet'ini çalıştırın

   > [!IMPORTANT]
   > Tarayıcının depoda varsayılan olarak bir delta taraması çalıştırdığını ve dosya değiştirilmediği veya tam yeniden tarama başlatmadığınız sürece önceki tarama döngüsünde zaten taranmış olan dosyaların atlandığını unutmayın. Tam yeniden tarama, kullanıcı arabirimindeki **tüm dosyaları yeniden tara** seçeneği kullanılarak veya **Start-AIPScan-Reset** çalıştırılarak başlatılabilir.

6.  Microsoft Purview uyumluluk portalı [Veri kaybı önleme sayfasını](https://compliance.microsoft.com/datalossprevention?viewid=policies) açın.

7. **İlke oluştur'u** seçin ve test DLP ilkesi oluşturun. İlke oluşturma konusunda yardıma ihtiyacınız varsa bkz. [Şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md) . Bu özelliği rahatça kullanıncaya kadar testte çalıştırdığınızdan emin olun. İlkeniz için şu parametreleri kullanın:
    1. DLP şirket içi tarayıcı kuralının kapsamını gerekirse belirli konumlara ayarlayın. **Konumları** **Tümü** olarak kapsamlarsanız, tarayıcı tarafından taranan tüm dosyalar DLP kuralı eşleştirme ve zorlamaya tabi olur.
    1. Konumları belirtirken dışlama veya ekleme listesini kullanabilirsiniz. Kuralın yalnızca ekleme listesinde listelenen desenlerden biriyle eşleşen yollara veya ekleme listesinde listelenen desenle eşleşen dosyalar dışında tüm dosyalara uygun olduğunu tanımlayabilirsiniz. Hiçbir yerel yol desteklenmez. Geçerli yollara bazı örnekler aşağıda verilmiştir:
      - \\\server\share
      - \\\server\share\folder1\subfolderabc
      - \*\\klasör1
      - \*gizli\*.docx
      - \*gizlidir\*.\*
      - sp2010.local/sites/HR https://
      - \*https:///İk 
    3. Kabul edilemez değerlerin kullanımına bazı örnekler aşağıda verilmiştir:
      - \*
      - \*\\A
      - Acar
      - c:\
      - C:\test

> [!IMPORTANT]
> Dışlama listesi, ekleme listesinden önceliklidir.

### <a name="viewing-dlp-on-premises-scanner-alerts-in-dlp-alerts-management-dashboard"></a>DLP Uyarı Yönetimi panosunda DLP şirket içi tarayıcı uyarılarını görüntüleme

1. Microsoft Purview uyumluluk portalı [Veri kaybı önleme sayfasını](https://compliance.microsoft.com/datalossprevention?viewid=policies) açın ve **Uyarılar'ı** seçin.

2. Uç Nokta [DLP ilkelerinizin uyarılarını görüntülemek için DLP ilkelerinizin uyarılarını yapılandırma ve görüntüleme](dlp-configure-view-alerts-policies.md) bölümündeki yordamlara bakın.

### <a name="viewing-dlp-on-premises-scanner-in-activity-explorer-and-audit-log"></a>Etkinlik gezgininde ve denetim günlüğünde DLP şirket içi tarayıcıyı görüntüleme

> [!NOTE]
> Şirket içi tarayıcı, denetimin etkinleştirilmesini gerektirir. Microsoft 365'te denetim varsayılan olarak etkindir.

1. Microsoft Purview uyumluluk portalı etki alanınız için [Veri sınıflandırma sayfasını](https://compliance.microsoft.com/dataclassification?viewid=overview) açın ve Etkinlik gezgini'ni seçin.

2. Şirket içi tarayıcı konumlarınızın tüm verilerine erişmek ve verileri filtrelemek için [Etkinlik gezginini kullanmaya başlama'daki](data-classification-activity-explorer.md) yordamlara bakın.

3. [Uyumluluk merkezinde Denetim günlüğünü](https://security.microsoft.com/auditlogsearch) açın. DLP kuralı eşleşmeleri Denetim günlüğü kullanıcı arabiriminde kullanılabilir veya [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) PowerShell tarafından erişilebilir 


## <a name="next-steps"></a>Sonraki adımlar
Şirket içi DLP konumları için bir test ilkesi dağıttığınız ve etkinlik verilerini Etkinlik gezgininde görüntüleyebildiğinize göre, hassas öğelerinizi koruyan DLP ilkeleri oluşturduğunuz bir sonraki adıma geçmeye hazırsınız.

- [Şirket içi DLP kullanma](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>Ayrıca bkz.

- [DLP şirket içi tarayıcısı hakkında bilgi edinin](dlp-on-premises-scanner-learn.md)
- [DLP şirket içi tarayıcıyı kullanma](dlp-on-premises-scanner-use.md)
- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md)
- [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md)
- [Etkinlik gezginini kullanmaya başlama](data-classification-activity-explorer.md)
- [Microsoft 365 aboneliği](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
