---
title: Microsoft Uyumluluk Uzantısı ile çalışmaya başlama
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
description: Microsoft Uyumluluk Uzantısı için hazırlanma ve dağıtma.
ms.openlocfilehash: 1c4c0a79f65f8a58ed30a9170256ef93b2bb4cef
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681820"
---
# <a name="get-started-with-microsoft-compliance-extension"></a>Microsoft Uyumluluk Uzantısı ile çalışmaya başlama

Microsoft Uyumluluk Uzantısını almak için bu yordamları kullanın.

## <a name="before-you-begin"></a>Başlamadan önce

Microsoft Uyumluluk Uzantısını kullanmak için, cihazın uç nokta DLP'ye ekli olması gerekir. DLP veya uç nokta DLP'de yeniysanız bu makaleleri gözden geçirme

- [Microsoft Uyumluluk Uzantısı hakkında bilgi](dlp-chrome-learn-about.md)
- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
- [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)
- [Şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)
- [Uç nokta veri kaybını önleme hakkında bilgi](endpoint-dlp-learn-about.md)
- [Uç nokta veri kaybını önlemeye başlama](endpoint-dlp-getting-started.md)
- [Windows 10 cihazları için Windows 10 yöntemleri](device-onboarding-overview.md)
- [Bilgi Koruması için cihaz ara sunucusunu ve internet bağlantısı ayarlarını yapılandırma](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection)
- [Uç nokta veri kaybını önlemeyi kullanma](endpoint-dlp-using.md)

### <a name="skusubscriptions-licensing"></a>SKU/abonelik lisansı

Başlamadan önce aboneliğinizi [ve Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) onaylamanız gerekir. Uç Nokta DLP işlevselliğine erişmek ve bunları kullanmak için, bu aboneliklerden veya eklentilerden biri olmalıdır.

- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- Microsoft 365 E5 uyumluluğu
- Microsoft 365 A5 uyumluluğu
- Microsoft 365 E5 koruma ve yönetim bilgilerini koruma
- Microsoft 365 A5 koruma ve yönetim bilgilerini koruma

Ayrıntılı lisanslama kılavuzu için, [güvenlik Microsoft 365 uyumluluğu için lisanslama & bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

- Kuruluş, Uç Nokta DLP lisansına sahip olmalıdır
- Cihazlarınız x64 Windows 10 1809 veya sonraki bir derlemede çalışıyor olmalı.
- Cihazda Kötü Amaçlı Yazılımdan Koruma İstemci Sürümü 4.18.2101.9 veya daha yeni bir sürüm yüklü olmalı. Windows Güvenliği uygulamasını **açarak Ayarlar** sürümünizi **kontrol** edin, Ayarlar Hakkında'ya **tıklayın**.


### <a name="permissions"></a>İzinler

Uç Nokta DLP'den veriler Etkinlik [gezgininde 2.](data-classification-activity-explorer.md) Etkinlik gezginine izin verilen yedi rol vardır ve verilere erişim için kullanabileceğiniz hesap bunlardan herhangi birinin üyesi olabilir.

- Genel yönetici
- Uyumluluk yöneticisi
- Güvenlik yöneticisi
- Uyumluluk verileri yöneticisi
- Genel okuyucu
- Güvenlik gözetmeni
- Rapor gözetmeni

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

### <a name="overall-installation-workflow"></a>Genel yükleme iş akışı

Microsoft Uyumluluk Uzantısını dağıtmak, çok aşamalı bir işlemdir. Bir makineye aynı anda tek bir makineye yükleyebilir ya da Microsoft Endpoint Manager dağıtımları için Grup İlkesi'ne veya Grup İlkesi'ne kullanabilirsiniz.

1. [Cihazlarınızı hazırlayın](#prepare-your-devices).
2. [Temel Kurulum Tek Makine Selfhost](#basic-setup-single-machine-selfhost)
3. [E-posta Microsoft Endpoint Manager](#deploy-using-microsoft-endpoint-manager)
4. [Grup İlkesi kullanarak dağıtma](#deploy-using-group-policy)
5. [Uzantıyı Test](#test-the-extension)
6. [Chrome DLP uyarılarını görüntülemek için Uyarılar Yönetim Panosu'u kullanma](#use-the-alerts-management-dashboard-to-viewing-chrome-dlp-alerts)
7. [Etkinlik gezgininde Chrome DLP verilerini görüntüleme](#viewing-chrome-dlp-data-in-activity-explorer)

### <a name="prepare-infrastructure"></a>Altyapı hazırlama

Microsoft Uyumluluk Uzantısını izlenen tüm cihazlarınıza ve cihazlarınıza Windows 10, Google Chrome'u izin verilmeyen uygulamadan ve izin verilmeyen tarayıcı listelerinden kaldırmanız gerekir. Daha fazla bilgi için bkz [. Izin verilmeyen tarayıcılar](dlp-configure-endpoint-settings.md#unallowed-browsers). Yalnızca birkaç cihaza sunarken Chrome'u izin verilmeyen tarayıcıda veya izin verilmeyen uygulama listelerinde  bırakın. Microsoft Uyumluluk Uzantısı, yüklü olduğu bu bilgisayarlarda her iki listenin kısıtlamalarını atlar.

### <a name="prepare-your-devices"></a>Cihazlarınızı hazırlama

1. Cihazlarınızı onboard olarak kullanmak için bu konu başlıklarında yer alan yordamları kullanın:
    1. [Uç nokta veri kaybını önlemeye başlama](endpoint-dlp-getting-started.md)
    1. [11 Windows 10 ve Windows cihazları ekleme](device-onboarding-overview.md)
    1. [Bilgi Koruması için cihaz ara sunucusunu ve internet bağlantısı ayarlarını yapılandırma](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection)

### <a name="basic-setup-single-machine-selfhost"></a>Temel Kurulum Tek Makine Selfhost

Bu önerilen yöntemdir.

1. Microsoft Uyumluluk Windows 10 yüklemek istediğiniz bilgisayarda oturum açın ve bu PowerShell betiği yönetici olarak çalıştırın.

   ```powershell
   Get-Item -path "HKLM:\SOFTWARE\Microsoft\Windows Defender\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
   ```

2. Microsoft Uyumluluk [Uzantısı - Uyumluluk Chrome Web Mağazası (google.com)](https://chrome.google.com/webstore/detail/microsoft-compliance-exte/echcggldkblhodogklpincgchnpgcdco).

3. Uzantıyı, Sayfa Son sayfasındaki Chrome Web Mağazası yükleyin.

### <a name="deploy-using-microsoft-endpoint-manager"></a>E-posta Microsoft Endpoint Manager

Kuruluş genelindeki dağıtımlar için bu kurulum yöntemini kullanın.

##### <a name="enabling-required-registry-value-via-microsoft-endpoint-manager"></a>Kayıt Defteri Aracılığıyla Gerekli Kayıt Defteri Microsoft Endpoint Manager

1. Aşağıdaki içeriği kullanarak bir PowerShell betiği oluşturun:

    ```powershell
    Get-Item -path "HKLM:\SOFTWARE\Microsoft\Windows Defender\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
    ```

2. Microsoft Endpoint Manager [Yönetim Merkezi'nde oturum açma](https://endpoint.microsoft.com).

3. **CihazlarScript'e** >  **gidin ve Ekle'yi** **seçin**.

4. Sorularak oluşturulan betiğin bulunduğu konuma gidin.

5. Aşağıdaki ayarları seçin:
    1. Oturum açma kimlik bilgilerini kullanarak bu betiği çalıştırın: NO
    1. Betik imzasını zorunlu kılın denetimi: HAYıR
    1. Betiği 64 bit PowerShell Ana Bilgisayarı'ta çalıştırma: YES

6. Uygun cihaz gruplarını seçin ve ilkeyi uygulama.

#### <a name="microsoft-endpoint-manager-force-install-steps"></a>Microsoft Endpoint Manager Zorla Yükleme Adımları

Microsoft Uyumluluk Uzantısını zorla yüklenmiş uzantılar listesine eklemeden önce Chrome ADMX'i eklemek önemlidir. Microsoft Endpoint Manager'de bu işleme Microsoft Endpoint Manager: Microsoft Intune ile Chrome Tarayıcıyı Yönet [- Google Chrome Enterprise Yardımı](https://support.google.com/chrome/a/answer/9102677?hl=en#zippy=%2Cstep-ingest-the-chrome-admx-file-into-intune).

 ADMX'i kullandıktan sonra, bu uzantı için bir yapılandırma profili oluşturmak için aşağıdaki adımlar takip edilecektir.

1. Microsoft Endpoint Manager Yönetim Merkezi'nde (https://endpoint.microsoft.com).

2. Yapılandırma Profilleri'ne gidin.

3. Profil **Oluştur'a tıklayın**.

4. Platform **olarak Windows 10'ı** seçin.

5. Profil **türü olarak** özel'i seçin.

6. Sekme **Ayarlar** seçin.

7. **Ekle**'yi seçin.

8. Aşağıdaki ilke bilgilerini girin.

    OMA-URI: `./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~Extensions/ExtensionInstallForcelist`<br/>
    Veri türü: `String`<br/>
    Değer: `<enabled/><data id="ExtensionInstallForcelistDesc" value="1&#xF000; echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx"/>`

9. Oluştur'a tıklayın.

### <a name="deploy-using-group-policy"></a>Grup İlkesi kullanarak dağıtma

Microsoft Endpoint Manager'i kullanmak istemiyorsanız, grup ilkelerini kullanarak Microsoft Uyumluluk Uzantısı'nın tüm kuruluşlarıyla birlikte dağıtın

1. Cihazlarınız Grup İlkesi aracılığıyla yönetilebilir olmalı ve tüm Chrome ADMX'leri Grup İlkesi Merkezi Mağazası'na aktarmanız gerekir. Daha fazla bilgi için bkz[.](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) Merkezi Grup İlkesi Yönetim Şablonları için Merkezi Mağaza oluşturma ve Windows.

2. Bu PowerShell komutunu kullanarak bir PowerShell betiği oluşturun:

    ```powershell
    Get-Item -path "HKLM:\SOFTWARE\Microsoft\Windows Defender\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
    ```

3. Grup İlkesi **Yönetim Konsolu'nu açın** ve kuruluş biriminize (OU) gidin.

4. Sağ tıklayın ve Bu etki alanında **GPO oluştur'u seçin ve Buraya bın**. İstendiğinde, bu grup ilkesi nesnesine (GPO) açıklayıcı bir ad verin ve oluşturmayı bitirin.

5. GPO'ya sağ tıklayın ve Düzenle'yi **seçin**.

6. Bilgisayar **YapılandırmasıPreferencesControl** >  **Panel'e** >  Ayarlar  > **Scheduled Görevler'e gidin**.

7. Sağ tık tıklatıp YeniMmediate Görevi'yi (En  >  az 7) seçerek yeni **Windows oluşturun**.

8. Göreve bir ad ve &.

9. Acil görevi çalıştırmak için ilgili hesabı (örneğin, NT Yetkili) seçin

10. En yüksek **ayrıcalıklarla çalıştır'ı seçin**.

11. Varsayılan ilkeyi Windows 10.

12. Eylemler **sekmesinde** Program başlat **eylemlerini seçin**.

13. 1. Adımda oluşturulan Program/Betik'in yolunu girin.

14. **Uygula'ya seçin**.

#### <a name="adding-the-chrome-extension-to-the-forceinstall-list"></a>ForceInstall Listesine Chrome Uzantısı ekleme

1. Grup İlkesi Yönetim Düzenleyicisi'nde, OU'nize gidin.

2. Aşağıdaki yolu genişletin **Bilgisayar/Kullanıcı** **yapılandırmasıPoliciesAdministrative** >  >  **şablonlarClassic administrative** templatesGoogleGoogle >  >  >  **ChromeExtensions** > . Bu yol yapılandırmanıza bağlı olarak farklılık gösterebilir.

3. Zorla **yüklenmiş uzantılar listesini yapılandır'ı seçin**.

4. Sağ tıklayın ve Düzenle'yi **seçin**.

5. **Etkin'i seçin**.

6. **Göster'i seçin**.

7. **Değer'in** altına aşağıdaki girdiyi ekleyin:`echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx`

8. **Tamam'ı ve** ardından **Uygula'ya tıklayın**.

### <a name="test-the-extension"></a>Uzantıyı Test

#### <a name="upload-to-cloud-service-or-access-by-unallowed-browsers-cloud-egress"></a>Upload hizmetine erişme veya izin verilmeyen tarayıcılar tarafından erişim izni ver Bulut Egress

1. Hassas bir öğe oluşturun veya almak ve bir dosyayı, kuruluşun sınırlı hizmet etki alanlarından birini karşıya yüklemeye deneyin. Hassas veriler yerleşik Hassas Bilgi Türlerimizin veya kuruluşun hassas bilgi [](sensitive-information-type-entity-definitions.md)türlerinden birinin eşleşmesi gerekir. Dosya açıkken bu eyleme izin verilmiyor uyarılarını gösteren, test kaynak cihazda bir DLP bildirimi alırsınız.

#### <a name="testing-other-dlp-scenarios-in-chrome"></a>Chrome'da diğer DLP senaryolarını test etme

Artık Chrome'u izin verilmeyen tarayıcılar/uygulamalar listesinden kaldırıldığına göre, aşağıdaki senaryoları test edebilirsiniz ve davranışın kurum gereksinimlerine uygun olduğunu onaylayın:

- Pano'da hassas bir öğeden başka bir belgeye veri kopyalama
  - Test etmek için Chrome tarayıcısında pano eylemlerine kopyalamaya karşı korunan bir dosyayı açın ve dosyadan veri kopyalamayı deneyin.
  - Beklenen Sonuç: Dosya açıkken bu eyleme izin verilme olmadığını gösteren bir DLP bildirimi.
- Belge yazdırma
  - Test etmek için Chrome tarayıcıda yazdırma eylemlerine karşı korunan bir dosyayı açın ve dosyayı yazdırmayı deneyin.
  - Beklenen Sonuç: Dosya açıkken bu eyleme izin verilme olmadığını gösteren bir DLP bildirimi.
- USB Kaldırılabilir Medyaya Kopyala
  - Test etmek için, dosyayı kaldırılabilir bir medya depolama alanına kaydetmeyi deneyin.
  - Beklenen Sonuç: Dosya açıkken bu eyleme izin verilme olmadığını gösteren bir DLP bildirimi.
- Ağ Paylaşımına Kopyala
  - Test etmek için dosyayı bir ağ paylaşımına kaydetmeyi deneyin.
  - Beklenen Sonuç: Dosya açıkken bu eyleme izin verilme olmadığını gösteren bir DLP bildirimi.

### <a name="use-the-alerts-management-dashboard-to-viewing-chrome-dlp-alerts"></a>Chrome DLP uyarılarını görüntülemek için Uyarılar Yönetim Panosu'u kullanma

1. Çalışma sayfasında **Veri kaybı önleme** sayfasını <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">açın ve</a> **Microsoft 365 uyumluluk merkezi'ı seçin**.

2. Uç Nokta DLP [ilkelerinize yönelik uyarıları görüntülemek üzere DLP](dlp-configure-view-alerts-policies.md) ilkelerinizin uyarılarını yapılandırma ve görüntüleme makalesinde yer alan yordamlara bakın.

### <a name="viewing-chrome-dlp-data-in-activity-explorer"></a>Etkinlik gezgininde Chrome DLP verilerini görüntüleme

1. Etkinlik sayfasında [etki alanınız](https://compliance.microsoft.com/dataclassification?viewid=overview) için Veri sınıflandırma sayfasını <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">açın Microsoft 365 uyumluluk merkezi</a> **Gezgini'ni seçin**.

2. Uç nokta cihazlarınız için [tüm verilere erişmek ve](data-classification-activity-explorer.md) bu verilere filtre uygulama için Etkinlik gezginiyle çalışmaya başlama'daki yordamlara bakın.

   > [!div class="mx-imgBorder"]
   > ![uç nokta cihazları için etkinlik gezgini filtresi.](../media/endpoint-dlp-4-getting-started-activity-explorer.png)

### <a name="known-issues-and-limitations"></a>Bilinen Sorunlar ve Sınırlamalar

1. Gizli modu desteklenmiyor ve devre dışı bırakılamaz.

## <a name="next-steps"></a>Sonraki adımlar

Kullanıma alındıklarınızı ve etkinlik verilerini Etkinlik Gezgini'nde görüntüleyebilirsiniz; artık hassas öğelerinizi koruyan DLP ilkelerini oluşturan bir sonraki adımınıza geçebilirsiniz.

- [Uç nokta veri kaybını önlemeyi kullanma](endpoint-dlp-using.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Uç nokta veri kaybını önleme hakkında bilgi](endpoint-dlp-learn-about.md)
- [Uç nokta veri kaybını önlemeyi kullanma](endpoint-dlp-using.md)
- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
- [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)
- [Etkinlik gezgini ile çalışmaya başlama](data-classification-activity-explorer.md)
- [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/)
- [Makine makineniz için ekleme araçları Windows 10 yöntemleri](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [Microsoft 365 aboneliği](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure AD'ye katılan cihazlar](/azure/active-directory/devices/concept-azure-ad-join)
- [Temel Microsoft Edge yeni Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
