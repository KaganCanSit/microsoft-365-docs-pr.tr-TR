---
title: Uç Nokta için Microsoft Defender için Güvenlik Yönetimi ile ilgili ekleme sorunlarını giderme
description: Uç Nokta için Microsoft Defender için Güvenlik Yönetimi'ni kullanarak cihazların eklenmesi sırasında ortaya çıkabilecek sorunları giderin.
keywords: ekleme, ekleme sorunları, olay görüntüleyicisi, veri toplama ve önizleme derlemeleri, algılayıcı verileri ve tanılama sorunlarını giderme
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: 958c58fab875ce86b0a3290450e2cf17c4b75a44
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65320507"
---
# <a name="troubleshoot-onboarding-issues-related-to-security-management-for-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender için Güvenlik Yönetimi ile ilgili ekleme sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**

- [Microsoft Endpoint Manager ile cihazlarda Uç Nokta için Microsoft Defender yönetme](/mem/intune/protect/mde-security-integration)
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Uç Nokta için Microsoft Defender için Güvenlik Yönetimi, Microsoft Endpoint Manager tarafından yönetilmeyen cihazlar için Microsoft Intune veya Uç Nokta için Microsoft Defender güvenlik yapılandırmalarını doğrudan Endpoint Manager almak için Microsoft Endpoint Configuration Manager.
Uç Nokta için Microsoft Defender için Güvenlik Yönetimi hakkında daha fazla bilgi için bkz. [Microsoft Endpoint Manager olan cihazlarda Uç Nokta için Microsoft Defender yönetme](/mem/intune/protect/mde-security-integration).

Uç Nokta için Microsoft Defender ekleme yönergeleri için Güvenlik Yönetimi için bkz. [Uç Nokta için Microsoft Defender Güvenlik Yapılandırma Yönetimi](security-config-management.md)

Bu uçtan uca ekleme, sorunsuz olacak şekilde tasarlanmıştır ve kullanıcı girişi gerektirmez. Ancak, ekleme sırasında sorunlarla karşılaşırsanız, Uç Nokta için Microsoft Defender platformundaki hataları görüntüleyebilir ve giderebilirsiniz.

> [!NOTE]
> Yeni cihazlar için ekleme akışıyla ilgili sorun yaşıyorsanız[, Uç Nokta için Microsoft Defender önkoşullarını](/mem/intune/protect/mde-security-integration#prerequisites) gözden geçirin ve ekleme yönergelerinin izlendiğinden emin olun.

İstemci çözümleyicisi hakkında daha fazla bilgi için bkz[. Uç Nokta için Microsoft Defender İstemci Çözümleyicisi kullanarak algılayıcı sistem durumu sorunlarını giderme](/microsoft-365/security/defender-endpoint/overview-client-analyzer).

## <a name="registering-domain-joined-computers-with-azure-active-directory"></a>Etki alanına katılmış bilgisayarları Azure Active Directory kaydetme

Cihazları Azure Active Directory başarıyla kaydetmek için aşağıdakilerden emin olmanız gerekir:

- Bilgisayarlar etki alanı denetleyicisiyle kimlik doğrulaması yapabilir
- Bilgisayarlar, kuruluşunuzun ağı içinden aşağıdaki Microsoft kaynaklarına erişebilir:
  - https://enterpriseregistration.windows.net
  - https://login.microsoftonline.com
  - https://device.login.microsoftonline.com
- Azure AD bağlantısı, bilgisayar nesnelerini eşitlemek için yapılandırılır. Varsayılan olarak, bilgisayar OU'ları Azure AD bağlanma eşitleme kapsamındadır. Bilgisayar nesneleri belirli kuruluş birimlerine (OU) aitse, OU'ları Azure AD Bağlan eşitlenecek şekilde yapılandırın. Azure AD Bağlan kullanarak bilgisayar nesnelerini eşitleme hakkında daha fazla bilgi edinmek için bkz[. Kuruluş birimi tabanlı filtreleme](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering#organizational-unitbased-filtering).

> [!IMPORTANT]
> Azure AD connect Windows Server 2012 R2 bilgisayar nesnelerini eşitlemez. Bunları Uç Nokta için Microsoft Defender için Güvenlik Yönetimi için Azure AD kaydetmeniz gerekiyorsa, eşitleme kapsamına bu bilgisayar nesnelerini dahil etmek Azure AD eşitleme kuralını özelleştirmeniz gerekir. Bkz. [Azure Active Directory Bağlan'da Bilgisayar Birleştirme kuralı uygulama yönergeleri]().

> [!NOTE]
> Ekleme akışını başarıyla tamamlamak ve cihazın İşletim Sisteminden bağımsız olarak cihazın Azure Active Directory durumu, cihazların ilk durumuna bağlı olarak değişebilir:
>
> <br>
>
>|Cihaz Durumu Başlatılıyor|Yeni Cihaz Durumu|
>|---|---|
>|Zaten AADJ veya HAADJ|Olduğu gibi kalır|
>|AADJ veya Karma Azure Active Directory Katılma (HAADJ) + Etki alanına katılma|Cihaz HAADJ'd|
>|AADJ veya HAADJ + Etki alanına katılma değil|Cihaz AADJ'd|
>
> Burada AADJ Azure Active Directory Katılmış'ı, HAADJ ise Karma Azure Active Directory Katılmış'ı temsil eder.

## <a name="troubleshoot-errors-from-the-microsoft-defender-for-endpoint-portal"></a>Uç Nokta için Microsoft Defender portalındaki hataları giderme

Uç Nokta için Microsoft Defender portalı aracılığıyla, güvenlik yöneticileri artık Uç Nokta için Microsoft Defender ekleme için Güvenlik Yönetimi sorunlarını giderebilir.

**Uç Noktalar** \> **Cihaz envanterinde****, Yönetim** kanalına göre filtrelemek için Yönetilen sütunu eklenmiştir (örneğin, MEM).

:::image type="content" source="./images/device-inventory-mde-error.png" alt-text="Cihaz envanter sayfası" lightbox="./images/device-inventory-mde-error.png":::

Uç Nokta için Microsoft Defender ekleme işlemi için Güvenlik Yönetimi'nde başarısız olan tüm cihazların listesini görmek için tabloyu **MDE-Error** ölçütüne göre filtreleyin.

Listede, yan panelde hatanın kök nedenini ve ilgili belgeleri gösteren sorun giderme ayrıntılarını görmek için belirli bir cihazı seçin.


:::image type="content" source="./images/secconfig-mde-error.png" alt-text="Cihaz envanteri sayfasına uygulanan filtre ölçütleri" lightbox="./images/secconfig-mde-error.png":::

## <a name="run-microsoft-defender-for-endpoint-client-analyzer-on-windows"></a>Windows Uç Nokta için Microsoft Defender İstemci Çözümleyicisi'ni çalıştırma

Uç Nokta için Microsoft Defender ekleme akışı için Güvenlik Yönetimi'ni tamamlayamayan uç noktalarda İstemci Çözümleyicisi'ni çalıştırmayı göz önünde bulundurun. İstemci çözümleyicisi hakkında daha fazla bilgi için bkz[. Uç Nokta için Microsoft Defender İstemci Çözümleyicisi kullanarak algılayıcı sistem durumu sorunlarını giderme](overview-client-analyzer.md).

İstemci Çözümleyicisi çıkış dosyası (MDE İstemci Çözümleyicisi Results.htm) önemli sorun giderme bilgileri sağlayabilir:

- **Genel Cihaz Ayrıntıları** bölümünde cihaz işletim sisteminin Uç Nokta için Microsoft Defender ekleme akışı için Güvenlik Yönetimi kapsamında olduğunu doğrulayın
- Cihazın **Cihaz Yapılandırma Yönetimi Ayrıntıları'ndaki** Azure Active Directory başarıyla kaydedildiğini doğrulayın

  :::image type="content" source="images/client-analyzer-results.png" alt-text="İstemci çözümleyicisi sonuçları" lightbox="images/client-analyzer-results.png":::

Raporun **Ayrıntılı Sonuçlar** bölümünde İstemci Çözümleyicisi de eyleme dönüştürülebilir yönergeler sağlar.

> [!TIP]
> Raporun Ayrıntılı Sonuçlar bölümünde "Hatalar" olmadığından emin olun ve tüm "Uyarı" iletilerini gözden geçirmeyi unutmayın.

Örneğin, Güvenlik Yönetimi ekleme akışının bir parçası olarak, Uç Nokta için Microsoft Defender Kiracınızdaki Azure Active Directory Kiracı Kimliğinin raporların **Cihaz Yapılandırma Yönetimi Ayrıntıları** bölümünde görünen SCP Kiracı Kimliği ile eşleşmesi gerekir. Uygunsa, rapor çıktısı bu doğrulamayı gerçekleştirmenizi önerir.

:::image type="content" source="images/detailed-results.png" alt-text="Ayrıntılı sonuçları görüntüleyen sayfa" lightbox="images/detailed-results.png"

## <a name="general-troubleshooting"></a>Genel sorun giderme

AAD veya MEM'de eklenen cihazı belirleyemediyseniz ve kayıt sırasında bir hata almadıysanız kayıt defteri anahtarının `Computer\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\SenseCM\\EnrollmentStatus` denetlenmesi ek sorun giderme bilgileri sağlayabilir.

:::image type="content" source="images/enrollment-status.png" alt-text="Kayıt durumunu gösteren sayfa" lightbox="images/enrollment-status.png":::

Aşağıdaki tabloda, hatayı gidermek için nelerin denenmesi/iade edilmesi gerektiğiyle ilgili hatalar ve yönergeler listelemektedir. Hata listesinin tamamlanmadığını ve geçmişte müşterilerin karşılaştığı tipik/yaygın hataları temel aldığına dikkat edin:

<br>

****

|Hata Kodu|Kayıt Durumu|Yönetici Eylemleri|
|---|---|---|
|`5-7`, `9`, `11-12`, `26-33`|Genel hata|Cihaz başarıyla Uç Nokta için Microsoft Defender eklendi. Ancak, güvenlik yapılandırması yönetim akışında bir hata oluştu. Bunun nedeni cihazın [Uç Nokta için Microsoft Defender yönetim kanalı önkoşullarını](security-config-management.md) karşılamaması olabilir. [İstemci Çözümleyicisi'nin](https://aka.ms/BetaMDEAnalyzer) cihazda çalıştırılması sorunun kök nedenini belirlemeye yardımcı olabilir. Bu işe yaramazsa lütfen desteğe başvurun.|
| `8`, `44` | Microsoft Endpoint Manager Yapılandırması sorunu | Cihaz başarıyla Uç Nokta için Microsoft Defender eklendi. Ancak Microsoft Endpoint Manager yönetim merkezi aracılığıyla Uç Nokta için Microsoft Defender Güvenlik Yapılandırmasına izin verecek şekilde yapılandırılmamıştır. [Microsoft Endpoint Manager kiracısının yapılandırıldığından ve özelliğin açık olduğundan](/mem/intune/protect/mde-security-integration#configure-your-tenant-to-support-microsoft-defender-for-endpoint-security-configuration-management) emin olun.|
|`13-14`,`20`,`24`,`25`|Bağlantı sorunu|Cihaz başarıyla Uç Nokta için Microsoft Defender eklendi. Ancak, güvenlik yapılandırması yönetim akışında bir bağlantı sorunundan kaynaklanabilecek bir hata oluştu. [Azure Active Directory ve Microsoft Endpoint Manager uç noktalarının](security-config-management.md#connectivity-requirements) güvenlik duvarınızda açıldığını doğrulayın.|
|`10`,`42`|Genel Karma birleştirme hatası|Cihaz başarıyla Uç Nokta için Microsoft Defender eklendi. Ancak, güvenlik yapılandırma yönetimi akışında bir hata oluştu ve işletim sistemi karma birleştirme gerçekleştiremedi. İşletim sistemi düzeyinde karma birleştirme hatalarını gidermek için [karma Azure Active Directory katılmış cihazlarda](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-current) sorun giderme'yi kullanın.|
|`15`|Kiracı uyuşmazlığı|Cihaz başarıyla Uç Nokta için Microsoft Defender eklendi. Ancak, Uç Nokta için Microsoft Defender kiracı kimliğiniz Azure Active Directory kiracı kimliğiniz ile eşleşmediğinden güvenlik yapılandırma yönetimi akışında bir hata oluştu. Uç Nokta için Defender kiracınızdaki Azure Active Directory kiracı kimliğinin, etki alanınızın SCP girişindeki kiracı kimliğiyle eşleştiğinden emin olun. Daha fazla ayrıntı için Uç Nokta için Microsoft Defender [için Güvenlik Yönetimi ile ilgili ekleme sorunlarını giderin](troubleshoot-security-config-mgt.md).|
|`16`,`17`|Karma hata - Hizmet Bağlantı Noktası|Cihaz başarıyla Uç Nokta için Microsoft Defender eklendi. Ancak Hizmet Bağlantı Noktası (SCP) kaydı doğru yapılandırılmadı ve cihaz Azure AD birleştirilemedi. Bunun nedeni SCP'nin Enterprise DRS'ye katılmak üzere yapılandırılması olabilir. SCP kaydının AAD ve SCP'ye işaret etmelerinin en iyi yöntemlere göre yapılandırıldığından emin olun. Daha fazla bilgi için bkz. [Hizmet bağlantı noktası yapılandırma](/azure/active-directory/devices/hybrid-azuread-join-manual#configure-a-service-connection-point).|
|`18`|Sertifika hatası|Cihaz başarıyla Uç Nokta için Microsoft Defender eklendi. Ancak, bir cihaz sertifikası hatası nedeniyle güvenlik yapılandırma yönetimi akışında bir hata oluştu. Cihaz sertifikası farklı bir kiracıya ait. [Güvenilen sertifika profilleri](/mem/intune/protect/certificates-trusted-root#create-trusted-certificate-profiles) oluşturulurken en iyi yöntemlerin izlendiğini doğrulayın.|
|`36` , `37`| AAD Bağlan yanlış yapılandırma |Cihaz başarıyla Uç Nokta için Microsoft Defender eklendi. Ancak, AAD Bağlan yanlış yapılandırma nedeniyle güvenlik yapılandırma yönetimi akışında bir hata oluştu. Cihazın AAD'ye kaydolmasını engelleyen şeyi belirlemek için [Cihaz Kaydı Sorun Giderici Aracı'nı](/samples/azure-samples/dsregtool/dsregtool) çalıştırmayı göz önünde bulundurun. Windows Server 2012 R2 için [özel sorun giderme yönergelerini](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-legacy) çalıştırın.  |
|`38`,`41`|DNS hatası|Cihaz başarıyla Uç Nokta için Microsoft Defender eklendi. Ancak, bir DNS hatası nedeniyle güvenlik yapılandırması yönetim akışında bir hata oluştu. Cihazdaki İnternet bağlantısını ve/veya DNS ayarlarını denetleyin. Geçersiz DNS ayarları iş istasyonu tarafında olabilir. Active Directory, düzgün çalışmak için (yönlendiricinin adresini değil) etki alanı DNS'sini kullanmanızı gerektirir. Daha fazla bilgi için bkz[. Uç Nokta için Microsoft Defender için Güvenlik Yönetimi ile ilgili ekleme sorunlarını giderme](troubleshoot-security-config-mgt.md).|
|`40`|Saat eşitleme sorunu|Cihaz başarıyla Uç Nokta için Microsoft Defender eklendi. Ancak, güvenlik yapılandırması yönetim akışında bir hata oluştu. Saatin doğru ayarlandığını ve hatanın oluştuğu cihazda eşitlendiğini doğrulayın.|

## <a name="azure-active-directory-runtime-troubleshooting"></a>Azure Active Directory Çalışma Zamanı sorunlarını giderme

### <a name="azure-active-directory-runtime"></a>Azure Active Directory Çalışma Zamanı

Azure Active Directory Çalışma Zamanı (AADRT) sorunlarını gidermenin ana mekanizması hata ayıklama izlemelerini toplamaktır. Windows'da Azure Active Directory Çalışma Zamanı **, bd67e65c-9cc2-51d8-7399-0bb9899e75c1 kimliğine sahip ETW sağlayıcısını** kullanır. ETW izlemelerinin, hatanın yeniden üretilmesiyle birlikte yakalanması gerekir (örneğin, birleştirme hatası oluşursa, birleştirmeyi gerçekleştirmek için AADRT API'lerine yapılan çağrıları kapsayan süre boyunca izlemelerin etkinleştirilmesi gerekir).

AADRT günlüğünde tipik bir hata ve nasıl okunduğu için aşağıya bakın:

:::image type="content" source="images/event-properties.png" alt-text="Olay özellikleri sayfası" lightbox="images/event-properties.png":::

İletideki bilgilerden, çoğu durumda hangi hatayla karşılaşıldığını, hangi Win32 API'sinin hatayı döndürdiğini (varsa), hangi URL'nin (varsa) kullanıldığını ve hangi AAD Çalışma Zamanı API'si hatasıyla karşılaşıldığını anlamak mümkündür.

## <a name="instructions-for-applying-computer-join-rule-in-aad-connect"></a>AAD Bağlan'de Bilgisayar Birleştirme kuralı uygulama yönergeleri

R2 etki alanına katılmış Windows Server 2012 bilgisayarlarda Uç Nokta için Microsoft Defender için Güvenlik Yönetimi için , "AD-Computer Katılmadan Gelen" Azure AD Bağlan eşitleme kuralına yönelik bir güncelleştirme gerekir. Bu, özgün "AD'den Gelen - Bilgisayara Katılma" kuralını devre dışı bırakacak şekilde kuralı kopyalayıp değiştirerek gerçekleştirilebilir. Azure AD Bağlan, yerleşik kurallarda değişiklik yapmak için varsayılan olarak bu deneyimi sunar.

> [!NOTE]
>Bu değişikliklerin AAD Bağlan çalıştığı sunucuya uygulanması gerekir. Dağıtılan birden çok AAD Bağlan örneğiniz varsa, bu değişikliklerin tüm örneklere uygulanması gerekir.

1. Başlat menüsünden Eşitleme Kuralları Düzenleyicisi uygulamasını açın. Kural listesinde **AD – Bilgisayar Katılımı'ndan In** adlı kuralı bulun. **Bu kural için 'Öncelik' sütunundaki değeri not alın.**

   :::image type="content" source="images/57ea94e2913562abaf93749d306dd6cf.png" alt-text="Eşitleme kuralları düzenleyicisi" lightbox="images/57ea94e2913562abaf93749d306dd6cf.png":::

2. **AD'den Gelen – Bilgisayara Katılma** kuralı vurgulanmışken **Düzenle'yi** seçin. **Ayrılmış Kuralı Düzenle Onayı** iletişim kutusunda **Evet'i** seçin.

   :::image type="content" source="images/8854440d6180a5580efda24110551c68.png" alt-text="Ayrılmış kuralı düzenleme onay sayfası" lightbox="images/8854440d6180a5580efda24110551c68.png":::

3. **Gelen eşitleme kuralını düzenle** penceresi gösterilir. Windows Server 2012R2'nin bu kural kullanılarak eşitleneceğini not etmek için kural açıklamasını güncelleştirin. Öncelik değeri dışında diğer tüm seçenekleri değiştirmeden bırakın. Öncelik için özgün kuraldaki değerden daha yüksek bir değer girin (kural listesinde görüldüğü gibi).

   :::image type="content" source="images/ee0f29162bc3f2fbe666c22f14614c45.png" alt-text="Değerleri girdiğiniz Gelen eşitleme kuralını düzenle sayfası" lightbox="images/ee0f29162bc3f2fbe666c22f14614c45.png":::

4. **Üç kez İleri'yi** seçin. Bu, kuralın 'Dönüşümler' bölümüne gider. Kuralın 'Kapsam filtresi' ve 'Kuralları birleştirme' bölümlerinde değişiklik yapmayın. 'Dönüşümler' bölümü artık gösterilmelidir.

   :::image type="content" source="images/296f2c2a705e41233631c3784373bc23.png" alt-text="Gelen eşitleme kuralı" lightbox="images/296f2c2a705e41233631c3784373bc23.png":::

5. Dönüşüm listesinin en altına kaydırın. **cloudFiltered** özniteliği için dönüştürmeyi bulun. **Kaynak** sütunundaki metin kutusunda tüm metni (Control-A) seçin ve silin. Metin kutusu artık boş olmalıdır.

6. Yeni kuralın içeriğini metin kutusuna yapıştırın.

    ```command
    IIF(
      IsNullOrEmpty([userCertificate])
      ||
      (
        (InStr(UCase([operatingSystem]),"WINDOWS") > 0)
        &&
        (Left([operatingSystemVersion],2) = "6.")
        &&
        (Left([operatingSystemVersion],3) <> "6.3")
      )
      ||
      (
        (Left([operatingSystemVersion],3) = "6.3")
        &&
        (InStr(UCase([operatingSystem]),"WINDOWS") > 0)
        &&
        With(
          $validCerts,
          Where(
            $c,
            [userCertificate],
            IsCert($c) && CertNotAfter($c) > Now() && RegexIsMatch(CertSubject($c), "CN=[{]*" & StringFromGuid([objectGUID]) & "[}]*", "IgnoreCase")),
          Count($validCerts) = 0)
      ),
      True,
      NULL
    )
    ```

7. Yeni kuralı kaydetmek için **Kaydet'i** seçin.

> [!NOTE]
> Bu kural değişikliği gerçekleştirildikten sonra Active Directory'nizin tam eşitlemesi gerekir. Büyük ortamlarda, şirket içi Active Directory sessiz dönemlerinde bu kural değişikliğini ve tam eşitlemeyi zamanlamak önerilir.

## <a name="related-topic"></a>İlgili konu

- [Microsoft Endpoint Manager ile cihazlarda Uç Nokta için Microsoft Defender yönetme](/mem/intune/protect/mde-security-integration)
