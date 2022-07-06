---
title: Microsoft Purview Uzantısını kullanmaya başlama
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
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Microsoft Purview Uzantısı'na hazırlanın ve dağıtın.
ms.openlocfilehash: 9593b75ea9bb858e9cd770ec4f40f4e6d7667a2e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622953"
---
# <a name="get-started-with-microsoft-purview-extension"></a>Microsoft Purview Uzantısı'nı kullanmaya başlama

Microsoft Purview Uzantısını dağıtmak için bu yordamları kullanın.

## <a name="before-you-begin"></a>Başlamadan önce

Microsoft Purview Uzantısı'nı kullanmak için cihazın uç nokta DLP'sine eklenmelidir. DLP veya uç nokta DLP'sini yeni kullanıyorsanız bu makaleleri gözden geçirin

- [Microsoft Purview Uzantısı hakkında bilgi edinin](dlp-chrome-learn-about.md)
- [Microsoft Purview Veri Kaybı Önleme hakkında bilgi edinin](dlp-learn-about-dlp.md)
- [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md)
- [Bir şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)
- [Uç nokta veri kaybını önleme hakkında bilgi edinin](endpoint-dlp-learn-about.md)
- [Uç noktada veri kaybı önlemeyi kullanmaya başlama](endpoint-dlp-getting-started.md)
- [Windows 10 cihazlar için ekleme araçları ve yöntemleri](device-onboarding-overview.md)
- [Information Protection için cihaz proxy ve internet bağlantısı ayarlarını yapılandırma](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection)
- [Uç noktada veri kaybı önlemeyi kullanma](endpoint-dlp-using.md)

### <a name="skusubscriptions-licensing"></a>SKU/abonelik lisanslama

Başlamadan önce [Microsoft 365 aboneliğinizi](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) ve tüm eklentileri onaylamanız gerekir. Uç Nokta DLP işlevselliğine erişmek ve bunları kullanmak için bu aboneliklerden veya eklentilerden birine sahip olmanız gerekir.

- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- Microsoft 365 E5 uyumluluğu
- Microsoft 365 A5 uyumluluğu
- Microsoft 365 E5 bilgi koruma ve idare
- Microsoft 365 A5 bilgi koruma ve idare

Ayrıntılı lisanslama kılavuzu için bkz. [Güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

- Kuruluşunuzun Endpoint DLP lisansına sahip olması gerekir
- Cihazlarınız Windows 10 x64 derleme 1809 veya üzerini çalıştırıyor olmalıdır.
- Cihazın Kötü Amaçlı Yazılımdan Koruma İstemci Sürümü 4.18.2202.x veya üzeri olmalıdır. **Windows Güvenliği** uygulamasını açarak geçerli sürümünüzü denetleyin, **Ayarlar** simgesini ve ardından **Hakkında'yı** seçin.


### <a name="permissions"></a>İzinler

Uç Nokta DLP'sindeki veriler [Etkinlik gezgininde](data-classification-activity-explorer.md) görüntülenebilir. Etkinlik gezginine izin veren yedi rol vardır; verilere erişmek için kullandığınız hesap bunlardan herhangi birinin üyesi olmalıdır.

- Genel yönetici
- Uyumluluk yöneticisi
- Güvenlik yöneticisi
- Uyumluluk verileri yöneticisi
- Genel gözetmen
- Güvenlik gözetmeni
- Rapor gözetmeni

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

### <a name="overall-installation-workflow"></a>Genel yükleme iş akışı

Uzantının dağıtılması çok aşamalı bir işlemdir. Tek seferde bir makineye yüklemeyi seçebilir veya kuruluş genelinde dağıtımlar için Microsoft Endpoint Manager veya grup ilkesi kullanabilirsiniz.

1. [Cihazlarınızı hazırlayın](#prepare-your-devices).
2. [Temel Kurulum Tek Makine selfhost](#basic-setup-single-machine-selfhost)
3. [Microsoft Endpoint Manager kullanarak dağıtma](#deploy-using-microsoft-endpoint-manager)
4. [grup ilkesi kullanarak dağıtma](#deploy-using-group-policy)
5. [Uzantıyı test edin](#test-the-extension)
6. [Chrome DLP uyarılarını görüntülemek için Uyarı Yönetimi Panosu'nu kullanma](#use-the-alerts-management-dashboard-to-viewing-chrome-dlp-alerts)
7. [Etkinlik gezgininde Chrome DLP verilerini görüntüleme](#viewing-chrome-dlp-data-in-activity-explorer)

### <a name="prepare-infrastructure"></a>Altyapıyı hazırlama

Uzantıyı tüm izlenen Windows 10 cihazlarınıza dağıtıyorsanız, Google Chrome'un izin verilmeyen uygulama ve izin verilmeyen tarayıcı listelerinden kaldırılması gerekir. Daha fazla bilgi için bkz. [İzin verilmeyen tarayıcılar](dlp-configure-endpoint-settings.md#unallowed-browsers). Yalnızca birkaç cihaza dağıtıyorsanız, Chrome'un izin verilmeyen tarayıcıda veya izin verilmeyen uygulama listelerinde bırakabilirsiniz. Uzantı, yüklü olduğu bilgisayarlar için her iki liste kısıtlamasını atlar.

### <a name="prepare-your-devices"></a>Cihazlarınızı hazırlama

1. Cihazlarınızı eklemek için bu konulardaki yordamları kullanın:
    1. [Uç noktada veri kaybı önlemeyi kullanmaya başlama](endpoint-dlp-getting-started.md)
    1. [Windows 10 ve Windows 11 cihazları ekleme](device-onboarding-overview.md)
    1. [Information Protection için cihaz proxy ve internet bağlantısı ayarlarını yapılandırma](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection)

### <a name="basic-setup-single-machine-selfhost"></a>Temel Kurulum Tek Makine selfhost

Önerilen yöntem budur.

1. [Microsoft Purview Uzantısı - Chrome Web Mağazası'na (google.com)](https://chrome.google.com/webstore/detail/microsoft-compliance-exte/echcggldkblhodogklpincgchnpgcdco) gidin.

2. Chrome Web Mağazası sayfasındaki yönergeleri kullanarak uzantıyı yükleyin.

### <a name="deploy-using-microsoft-endpoint-manager"></a>Microsoft Endpoint Manager kullanarak dağıtma

Kuruluş genelindeki dağıtımlar için bu kurulum yöntemini kullanın.

#### <a name="microsoft-endpoint-manager-force-install-steps"></a>Microsoft Endpoint Manager Zorla Yükleme Adımları

Uzantıyı zorla yüklenen uzantılar listesine eklemeden önce Chrome ADMX'i almak önemlidir. Microsoft Endpoint Manager'da bu işlemin adımları Google tarafından belgelenmiştir: [Microsoft Intune ile Chrome Tarayıcısını Yönetme - Google Chrome Kurumsal Yardımı](https://support.google.com/chrome/a/answer/9102677?hl=en#zippy=%2Cstep-ingest-the-chrome-admx-file-into-intune).

 ADMX alındıktan sonra, bu uzantı için bir yapılandırma profili oluşturmak için aşağıdaki adımlar izlenebilir.

1. Microsoft Endpoint Manager Yönetici Merkezi'nde (https://endpoint.microsoft.com).

2. Yapılandırma Profilleri'ne gidin.

3. **Profil Oluştur'u** seçin.

4. Platform olarak **Windows 10'ı** seçin.

5. Profil türü olarak **Özel'i** seçin.

6. **Ayarlar** sekmesini seçin.

7. **Ekle**'yi seçin.

8. Aşağıdaki ilke bilgilerini girin.

    OMA-URI: `./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~Extensions/ExtensionInstallForcelist`<br/>
    Veri türü: `String`<br/>
    Değer: `<enabled/><data id="ExtensionInstallForcelistDesc" value="1&#xF000; echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx"/>`

9. Oluştur'a tıklayın.

### <a name="deploy-using-group-policy"></a>grup ilkesi kullanarak dağıtma

Microsoft Endpoint Manager kullanmak istemiyorsanız, uzantıyı kuruluşunuza dağıtmak için grup ilkelerini kullanabilirsiniz.

#### <a name="adding-the-chrome-extension-to-the-forceinstall-list"></a>Chrome Uzantısını ForceInstall Listesine Ekleme

1. grup ilkesi Yönetim Düzenleyicisi'nde OU'nuza gidin.

2. Aşağıdaki yolu genişletin **Bilgisayar/Kullanıcı yapılandırma** > **İlkeleri** > **Yönetim şablonları** > **Klasik yönetim şablonları** > **Google** > **Google Chrome** > **Uzantıları**. Bu yol, yapılandırmanıza bağlı olarak değişebilir.

3. **Zorla yüklenen uzantıların listesini yapılandır'ı** seçin.

4. Sağ tıklayın ve **Düzenle'yi** seçin.

5. **Etkin'i** seçin.

6. **Göster'i** seçin.

7. **Değer'in** altında aşağıdaki girdiyi ekleyin:`echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx`

8. **Tamam'ı** ve ardından **Uygula'yı** seçin.

### <a name="test-the-extension"></a>Uzantıyı Test Edin

#### <a name="upload-to-cloud-service-or-access-by-unallowed-browsers-cloud-egress"></a>Bulut hizmetine yükleme veya izin verilmeyen tarayıcılar ile erişim Bulut Çıkışı

1. Hassas bir öğe oluşturun veya alın ve kuruluşunuzun kısıtlı hizmet etki alanlarından birine dosya yüklemeyi deneyin. Hassas verilerin yerleşik [Hassas Bilgi Türlerimizden](sensitive-information-type-entity-definitions.md) biriyle veya kuruluşunuzun hassas bilgi türlerinden biriyle eşleşmesi gerekir. Test ettiğiniz cihazda, dosya açıkken bu eyleme izin verilmediğini gösteren bir DLP bildirim almalısınız.

#### <a name="testing-other-dlp-scenarios-in-chrome"></a>Chrome'da diğer DLP senaryolarını test etme

Chrome'ı izin verilmeyen tarayıcılar/uygulamalar listesinden kaldırdığınıza göre, davranışın kuruluşunuzun gereksinimlerini karşıladığını onaylamak için aşağıdaki senaryoları test edebilirsiniz:

- Pano kullanarak hassas bir öğeden başka bir belgeye veri kopyalama
  - Test etmek için, Chrome tarayıcısında panoya kopyalama eylemlerine karşı korumalı bir dosya açın ve dosyadan veri kopyalamayı deneme.
  - Beklenen Sonuç: Dosya açıkken bu eyleme izin verilmediğini gösteren bir DLP bildirim.
- Belgeyi yazdırma
  - Test etmek için, Chrome tarayıcısında yazdırma eylemlerine karşı korumalı bir dosya açın ve dosyayı yazdırmayı dene.
  - Beklenen Sonuç: Dosya açıkken bu eyleme izin verilmediğini gösteren bir DLP bildirim.
- USB Kaldırılabilir Medyaya Kopyala
  - Test etmek için dosyayı kaldırılabilir bir medya depolama alanına kaydetmeyi deneyin.
  - Beklenen Sonuç: Dosya açıkken bu eyleme izin verilmediğini gösteren bir DLP bildirim.
- Ağ Paylaşımına Kopyala
  - Test etmek için dosyayı bir ağ paylaşımına kaydetmeyi deneyin.
  - Beklenen Sonuç: Dosya açıkken bu eyleme izin verilmediğini gösteren bir DLP bildirim.

### <a name="use-the-alerts-management-dashboard-to-viewing-chrome-dlp-alerts"></a>Chrome DLP uyarılarını görüntülemek için Uyarı Yönetimi Panosu'nu kullanma

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a> **Veri kaybı önleme** sayfasını açın ve **Uyarılar'ı** seçin.

2. Uç Nokta [DLP ilkelerinizin uyarılarını görüntülemek için DLP ilkelerinizin uyarılarını yapılandırma ve görüntüleme](dlp-configure-view-alerts-policies.md) bölümündeki yordamlara bakın.

### <a name="viewing-chrome-dlp-data-in-activity-explorer"></a>Etkinlik gezgininde Chrome DLP verilerini görüntüleme

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a> etki alanınız için [Veri sınıflandırma sayfasını](https://compliance.microsoft.com/dataclassification?viewid=overview) açın ve **Etkinlik gezgini'ni** seçin.

2. Uç Nokta cihazlarınızın tüm verilerine erişmek ve bunları filtrelemek için [Etkinlik gezginini kullanmaya başlama'daki](data-classification-activity-explorer.md) yordamlara bakın.

   > [!div class="mx-imgBorder"]
   > ![uç nokta cihazları için etkinlik gezgini filtresi.](../media/endpoint-dlp-4-getting-started-activity-explorer.png)

### <a name="known-issues-and-limitations"></a>Bilinen Sorunlar ve Sınırlamalar

1. Gizli mod desteklenmez ve devre dışı bırakılmalıdır.

## <a name="next-steps"></a>Sonraki adımlar

Artık cihazları eklediğinize ve etkinlik verilerini Etkinlik Gezgini'nde görüntüleyebildiğinize göre, hassas öğelerinizi koruyan DLP ilkeleri oluşturduğunuz bir sonraki adıma geçmeye hazırsınız.

- [Uç noktada veri kaybı önlemeyi kullanma](endpoint-dlp-using.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Uç nokta veri kaybı önleme hakkında daha fazla bilgi edinme](endpoint-dlp-learn-about.md)
- [Uç noktada veri kaybı önlemeyi kullanma](endpoint-dlp-using.md)
- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md)
- [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md)
- [Etkinlik gezginini kullanmaya başlama](data-classification-activity-explorer.md)
- [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/)
- [Windows 10 makineleri için ekleme araçları ve yöntemleri](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [Microsoft 365 aboneliği](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Birleştirilmiş cihazları Azure AD](/azure/active-directory/devices/concept-azure-ad-join)
- [Chromium tabanlı yeni Microsoft Edge'i indirin](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
