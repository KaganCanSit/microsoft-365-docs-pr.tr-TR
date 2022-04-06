---
title: Uç Nokta için Microsoft Defender için Güvenlik Yönetimi ile ilgili ekleme sorunlarını giderme
description: Mobil cihazlar için Güvenlik Yönetimi'ni kullanarak cihazların kullanımı sırasında ortaya çıkabilecek Uç Nokta için Microsoft Defender.
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
ms.openlocfilehash: 8d18d0dd193e720f7f91ae0c3a9d384a3715be82
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467939"
---
# <a name="troubleshoot-onboarding-issues-related-to-security-management-for-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender için Güvenlik Yönetimi ile ilgili ekleme sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [Cihazlarda Uç Nokta için Microsoft Defender yönet'i Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Mobil Cihazlar Uç Nokta için Microsoft Defender Güvenlik Yönetimi, bir cihaz veya Microsoft Endpoint Manager tarafından yönetil Microsoft Intune Microsoft Endpoint Configuration Manager, doğrudan posta Uç Nokta için Microsoft Defender yapılandırmalarını almak Endpoint Manager.
Mobil cihazlar için Güvenlik Yönetimi hakkında daha fazla Uç Nokta için Microsoft Defender için bkz. [Uç Nokta için Microsoft Defender cihazları yönetme ve Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).

Kullanıcı ekleme yönergelerini Uç Nokta için Microsoft Defender için bkz. [Güvenlik Uç Nokta için Microsoft Defender Yönetimi'ne bakın.](security-config-management.md)

Ender 2010 ekleme, kusursuz şekilde tasarlanmıştır ve kullanıcı girişi gerektirmez. Ancak, ekleme sırasında sorunlarla karşılaşırsanız bu platformda hataları  görüntüp Uç Nokta için Microsoft Defender.

> [!NOTE]
> Yeni cihazlar için ekleme akışıyla ilgili sorunlar ediyorsanız, [önkoşulları Uç Nokta için Microsoft Defender](/mem/intune/protect/mde-security-integration#prerequisites) ve ekleme yönergelerinin uyul olduğundan emin olun.

İstemci çözümleyicisi hakkında daha fazla bilgi için bkz[. Uç Nokta için Microsoft Defender Çözümleyicisi'ni kullanarak algılayıcı durumu sorunlarını giderme](/microsoft-365/security/defender-endpoint/overview-client-analyzer).

## <a name="registering-domain-joined-computers-with-azure-active-directory"></a>Etki alanına katılmış bilgisayarları Azure Active Directory

Cihazları başarıyla Azure Active Directory için, aşağıdakilerin sağlanması gerekir:

- Bilgisayarlar, etki alanı denetleyicisiyle kimlik doğrulaması
- Bilgisayarlar, aşağıdaki Microsoft kaynaklarına kuruluş ağının içinden erişim sağlar:
  - https://enterpriseregistration.windows.net
  - https://login.microsoftonline.com
  - https://device.login.microsoftonline.com
- Azure AD Connect, bilgisayar nesnelerini eşitlerken yapılandırılır. Varsayılan olarak, bilgisayar OU'ları Azure AD connect eşitleme kapsamı içindedir. Bilgisayar nesneleri belirli kuruluş birimlerine (OU'lar) aitse, OU'ları Azure AD'de eşitlemek üzere Bağlan. Azure AD nesnelerini kullanarak bilgisayar nesnelerini eşitleme hakkında daha fazla bilgi Bağlan bkz[. Kuruluş birimi tabanlı filtreleme](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering#organizational-unitbased-filtering).

> [!IMPORTANT]
> Azure AD Connect, R2 Windows Server 2012 nesnelerini eşitlemez. Bu bilgisayar nesnelerini eşitleme kapsamına eklemek için Uç Nokta için Microsoft Defender için Azure AD Güvenlik Yönetimi'ne kaydetmeniz gerekirse, Azure AD connect eşitleme kuralını bu bilgisayar nesnelerini eşitleme kapsamına dahil etmek için özelleştirmeniz gerekir. Bkz[. Azure Active Directory Bağlan'de Bilgisayar Birleştirme kuralını uygulama Azure Active Directory Bağlan]().

> [!NOTE]
> Ekleme akışını başarıyla tamamlamak ve cihazın İşletim Sisteminden bağımsız olarak, Azure Active Directory durumu, cihazların ilk durumuna bağlı olarak değişebilir:
>
> <br>
>
>|Başlangıç Cihazı Durumu|Yeni Cihaz Durumu|
>|---|---|
>|Zaten AADJ veya HAADJ|Olduğu gibi kalır|
>|Not AADJ veya Karma Azure Active Directory Join (HAADJ) + Domain joined|Cihaz HAADJ'd|
>|Not AADJ veya HAADJ + Not domain joined|Cihaz AADJ'd|
>
> Burada AADJ, Katılma Azure Active Directory HAADJ de Karma Değer'i Azure Active Directory temsil eder.

## <a name="troubleshoot-errors-from-the-microsoft-defender-for-endpoint-portal"></a>Portaldan gelen Uç Nokta için Microsoft Defender giderme

Güvenlik yöneticileri Uç Nokta için Microsoft Defender portal aracılığıyla, kullanıcı ekleme için Güvenlik Yönetimi Uç Nokta için Microsoft Defender sorunlarını giderebilirsiniz.

Uç **noktalar Cihaz** \> **envanteri** içinde, **Yönetim kanalına** (örneğin MEM) göre filtrelemek için Yönetilen sütunu eklenmiştir.

:::image type="content" source="./images/device-inventory-mde-error.png" alt-text="Cihaz stoku sayfası" lightbox="./images/device-inventory-mde-error.png":::

Kullanıcı ekleme işlemi için Güvenlik Yönetimi'ne geçemeyen tüm cihazların Uç Nokta için Microsoft Defender için, tabloya **MDE-Error koduna göre filtre uygulama**.

Yan panelde sorun giderme ayrıntılarını görmek için listede belirli bir cihazı seçin; hatanın temel nedenini ve ilgili belgeleri işaret edin.


:::image type="content" source="./images/secconfig-mde-error.png" alt-text="Cihaz envanteri sayfasında uygulanan filtre ölçütleri" lightbox="./images/secconfig-mde-error.png":::

## <a name="run-microsoft-defender-for-endpoint-client-analyzer-on-windows"></a>Çözümleyici Uç Nokta için Microsoft Defender Çözümleyicisi'Windows

İstemci Çözümleyicisi'nin, kullanıcı ekleme akışı için Güvenlik Yönetimi'ne tamamlanamayan uç Uç Nokta için Microsoft Defender çalıştırmayı göz önünde bulundurarak. İstemci çözümleyicisi hakkında daha fazla bilgi için bkz[. Uç Nokta için Microsoft Defender Çözümleyicisi'ni kullanarak algılayıcı durumu sorunlarını giderme](overview-client-analyzer.md).

İstemci Çözümleyicisi çıkış dosyası (MDE İstemci Çözümleyicisi Results.htm) önemli sorun giderme bilgileri sağlar:

- Cihaz işletim sistemi, Genel Cihaz Ayrıntıları bölümünde Güvenlik Yönetimi Uç Nokta için Microsoft Defender kapsamında **olduğunu** doğrulayın
- Cihazın Cihaz Yapılandırma Yönetimi Ayrıntıları'Azure Active Directory başarıyla **kayded olduğunu doğrulayın**

  :::image type="content" source="images/client-analyzer-results.png" alt-text="İstemci çözümleyicisi sonuçları" lightbox="images/client-analyzer-results.png":::

Raporun **Ayrıntılı Sonuçları** bölümünde, İstemci Çözümleyicisi eyleme değiştirilebilir kılavuz da sağlar.

> [!TIP]
> Raporun Ayrıntılı Sonuçlar bölümünde "Hata" olmadığını denetleyin ve tüm "Uyarı" iletilerini gözden geçirmeyi denetleyin.

Örneğin, Güvenlik Yönetimi ekleme akışının bir parçası olarak, Uç Nokta için Microsoft Defender Kiracısı'nıza ilişkin Azure Active Directory Kiracı **Kimliği'nin** raporların Cihaz Yapılandırma Yönetimi Ayrıntıları bölümünde görünen SCP Kiracı Kimliği ile eşleşmesi gerekir. Uygunsa, rapor çıktısı bu doğrulamayı gerçekleştirmenizi önerecek.

:::image type="content" source="images/detailed-results.png" alt-text="The page displaying the detailed results" lightbox="images/detailed-results.png"

## <a name="general-troubleshooting"></a>Genel sorun giderme

AAD veya MEM'de ekli cihazı belirleyemediyseniz ve kayıt sırasında bir hata almadıysanız, `Computer\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\SenseCM\\EnrollmentStatus` kayıt defteri anahtarının denetlen size ek sorun giderme bilgileri sağlar.

:::image type="content" source="images/enrollment-status.png" alt-text="Kayıt durumunu gösteren sayfa" lightbox="images/enrollment-status.png":::

Aşağıdaki tabloda, hatayı düzeltmek için deneyecekleri/denetlemeniz gereken hata ve yol tarifleri listele. Hata listesinin tamam olmadığını ve geçmişte müşterilerin karşılaştığı genel/yaygın hataları temel alıyor olduğunu unutmayın:

<br>

****

|Hata Kodu|Kayıt Durumu|Yönetici Eylemleri|
|---|---|---|
|`5-9`,`11-12`, `26-33`|Genel hata|Cihaz Başarıyla Başarıyla Uç Nokta için Microsoft Defender. Bununla birlikte, güvenlik yapılandırması yönetim akışında bir hata oluştu. Bunun nedeni, cihazın yönetim kanalının [önkoşullarını Uç Nokta için Microsoft Defender olabilir](security-config-management.md). Cihazda İstemci [Çözümleyicisi'nin](https://aka.ms/BetaMDEAnalyzer) çalışıyor olması sorunun temel nedenini belirlemeye yardımcı olabilir. Bu işe yardımcı olmazsa lütfen destek ile iletişime geçin.|
|`13-14`,`20`,`24`,`25`|Bağlantı sorunu|Cihaz Başarıyla Başarıyla Uç Nokta için Microsoft Defender. Bununla birlikte, güvenlik yapılandırması yönetim akışında bir bağlantı sorunundan dolayı söz konusu olabilir. Güvenlik duvarında [Azure Active Directory Microsoft Endpoint Manager uç noktalarının](security-config-management.md#connectivity-requirements) açık olduğunu doğrulayın.|
|`10`,`42`|Genel Karma katılma hatası|Cihaz Başarıyla Başarıyla Uç Nokta için Microsoft Defender. Bununla birlikte, güvenlik yapılandırma yönetim akışında bir hata oluştu ve işletim sistemi karma birleştirmeyi gerçekleştiremedi. [OS düzeyindeki Azure Active Directory katılma hatalarını gidermek](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-current) için Karma veya karma cihazla birlikte katılan cihazlarda sorun gidermeyi kullanın.|
|`15`|Kiracı eşleşmeyenleri|Cihaz Başarıyla Başarıyla Uç Nokta için Microsoft Defender. Bununla birlikte, güvenlik yapılandırma yönetimi akışında bir hata oluştu çünkü Uç Nokta için Microsoft Defender kiracı kimliğiniz kiracı kimliğiniz Azure Active Directory eşleşmedi. Uç nokta kiracısı Azure Active Directory Defender'daki kiracı kimliğinin, etki alanınız SCP girdisinde yer alan kiracı kimliğiyle eş olduğundan emin olun. Daha fazla ayrıntı için[, Uç Nokta için Microsoft Defender için Güvenlik Yönetimi ile ilgili ekleme Uç Nokta için Microsoft Defender](troubleshoot-security-config-mgt.md).|
|`16`,`17`|Karma hata - Hizmet Bağlantı Noktası|Cihaz Başarıyla Başarıyla Uç Nokta için Microsoft Defender. Bununla birlikte, Hizmet Bağlantı Noktası (SCP) kaydı doğru yapılandırılmadı ve cihaz Azure AD'ye birleştiriemedi. Bunun nedeni SCP'nin SCP'nin DRS'ye Enterprise olabilir. SCP kaydının en iyi yöntemleri AAD ve SCP'nin yapılandırılmış olduğundan emin olun. Daha fazla bilgi için bkz [. Hizmet bağlantı noktasını yapılandırma](/azure/active-directory/devices/hybrid-azuread-join-manual#configure-a-service-connection-point).|
|`18`|Sertifika hatası|Cihaz Başarıyla Başarıyla Uç Nokta için Microsoft Defender. Bununla birlikte, cihaz sertifikası hatası nedeniyle güvenlik yapılandırma yönetim akışında bir hata oluştu. Cihaz sertifikası farklı bir kiracıya aittir. Güvenilir sertifika profilleri oluştururken en iyi yöntemlerin [izlendiğini doğrulayın](/mem/intune/protect/certificates-trusted-root#create-trusted-certificate-profiles).|
|`36`|LDAP API hatası|Cihaz Başarıyla Başarıyla Uç Nokta için Microsoft Defender. Bununla birlikte, güvenlik yapılandırması yönetim akışında bir hata oluştu. Ağ topolojisini doğrulayın ve karma birleştirme isteklerini tamamlamak için LDAP API'nin kullanılabilir olduğundan emin olun.|
|`37`|Şirket içi eşitleme sorunu|Cihaz Başarıyla Başarıyla Uç Nokta için Microsoft Defender. Bununla birlikte, güvenlik yapılandırması yönetim akışında bir hata oluştu. Daha sonra yeniden deneyin. Bu işe yardımcı olursa bkz. [Azure AD ile nesne eşitlemesi sorunlarını giderme Bağlan.](/azure/active-directory/hybrid/tshoot-connect-objectsync)|
|`38`,`41`|DNS hatası|Cihaz Başarıyla Başarıyla Uç Nokta için Microsoft Defender. Bununla birlikte, bir DNS hatası nedeniyle güvenlik yapılandırma yönetim akışında bir hata oluştu. Cihazda İnternet bağlantısını ve/veya DNS ayarlarını kontrol edin. Geçersiz DNS ayarları iş istasyonu tarafında olabilir. Active Directory, düzgün çalışmak için etki alanı DNS'lerini (yönlendiricinin adresini değil) kullanmasını gerektirir. Daha fazla bilgi için bkz[. Güvenlik Yönetimi ile ilgili ekleme sorunlarını giderme Uç Nokta için Microsoft Defender](troubleshoot-security-config-mgt.md).|
|`40`|Saat eşitleme sorunu|Cihaz Başarıyla Başarıyla Uç Nokta için Microsoft Defender. Bununla birlikte, güvenlik yapılandırması yönetim akışında bir hata oluştu. Saatin doğru ayar olduğunu ve hatanın oluştuğu cihazda eşit olduğunu doğrulayın.|

## <a name="azure-active-directory-runtime-troubleshooting"></a>Azure Active Directory Çalışma Zamanı sorunlarını giderme

### <a name="azure-active-directory-runtime"></a>Azure Active Directory Çalışma Zamanı

Çalışma Zamanı'nın (AADRT) Azure Active Directory sorunlarını gidermek için ana mekanizma hata ayıklama izlemelerini toplamaktır. Azure Active Directory Çalışma Zamanı Windows **kimlik bd67e65c-9cc2-51d8-7399-0bb9899e75c1 ile ETW** sağlayıcısı kullanır. ETW izlemelerinin, hatanın yeniden çoğaltılmasıyla yakalanması gerekir (örneğin katılma hatası oluşursa, birleştirmenin gerçekleştirilmesi için AADRT API'lerine yapılan çağrıları kapsayan süre boyunca izlemenin etkinleştirilmesi gerekir).

AADRT günlüğünde tipik bir hata ve nasıl okundu hatası için aşağıya bakın:

:::image type="content" source="images/event-properties.png" alt-text="Olay özellikleri sayfası" lightbox="images/event-properties.png":::

İletide yer alan bilgilerden, hangi hatayla karşılaşıldı, Win32 API'sinin hatayı hangi hataya döndürüleni (varsa), hangi URL'nin (varsa) kullanılmış olduğunu ve hangi AAD Runtime API hatasıyla karşılaştığını anlamak mümkündür.

## <a name="instructions-for-applying-computer-join-rule-in-aad-connect"></a>AAD Bağlan'da Bilgisayar Birleştirme kuralını uygulama AAD Bağlan

R2 etki alanına Uç Nokta için Microsoft Defender katılmış Windows Server 2012 üzerinde Güvenlik Yönetimi için Azure AD Bağlan eşitleme kuralı "AD-Computer'den katıl" güncelleştirmesi gerekir. Bu, kuralın kopyasını değiştirerek ve değiştirerek elde edilebilir; bu da özgün "In from AD - Bilgisayar Birleştirmesi" kuralını devre dışı bırakacak. Azure AD Bağlan varsayılan olarak yerleşik kurallarda değişiklik yapmaya yönelik bu deneyimi sunar.

> [!NOTE]
>Bu değişikliklerin, çalışma olan sunucuya uygulanması AAD Bağlan gerekir. Dağıtılmış birden çok AAD Bağlan varsa, bu değişikliklerin tüm örneklere uygulanması gerekir.

1. Başlat menüsünden Eşitleme Kuralları Düzenleyicisi uygulamasını açın. Kural listesinde, **Ad – Bilgisayar Birleştirmesi'nde adlı kuralı bulun**. **Bu kuralın 'Öncelik' sütunundaki değeri not alma.**

   :::image type="content" source="images/57ea94e2913562abaf93749d306dd6cf.png" alt-text="Eşitleme kuralları düzenleyicisi" lightbox="images/57ea94e2913562abaf93749d306dd6cf.png":::

2. In **from AD – Computer Join kuralı vurgulanmış** olarak Düzenle'yi **seçin**. Özel Kullanım **Kuralı Onayı Düzenle iletişim** kutusunda Evet'i **seçin**.

   :::image type="content" source="images/8854440d6180a5580efda24110551c68.png" alt-text="Düzenleme özel kullanım kuralı onay sayfası" lightbox="images/8854440d6180a5580efda24110551c68.png":::

3. Gelen **eşitleme kuralını düzenle** penceresi görüntülenir. Sunucu 2012R2'Windows bu kural kullanılarak eşitlen olacağını unutmayın, kural açıklamasını güncelleştirin. Öncelik değeri dışında diğer tüm seçenekleri değiştirmeden bırakın. Özgün kuraldan daha yüksek öncelik için bir değer girin (kural listesinde de görülür).

   :::image type="content" source="images/ee0f29162bc3f2fbe666c22f14614c45.png" alt-text="Değerleri girerek gelen eşitleme kuralını düzenle sayfası" lightbox="images/ee0f29162bc3f2fbe666c22f14614c45.png":::

4. Üç **kez Sonraki'yi** seçin. Bu, kuralın 'Dönüşümler' bölümüne gidin. Kuralın 'Coping filtresi' ve 'Birleşim kuralları' bölümlerinde hiçbir değişiklik yapmamak. 'Dönüştürmeler' bölümü artık gösteriliyor olmalı.

   :::image type="content" source="images/296f2c2a705e41233631c3784373bc23.png" alt-text="Gelen eşitleme kuralı" lightbox="images/296f2c2a705e41233631c3784373bc23.png":::

5. Dönüştürme listesinin en altına kaydırın. bulutFiltreli **özniteliğine dönüştürmeyi** bulun. Kaynak sütunundaki metin **kutusunda** , tüm metni seçin (Control-A) ve silin. Artık metin kutusu boş olacaktır.

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

7. Yeni **kuralı kaydetmek** için Kaydet'i seçin.

> [!NOTE]
> Bu kural değişikliği gerçekleştirildikten sonra Active Directory'nizin tam eşitlemesi gerekir. Büyük ortamlar için, şirket içi Active Directory sessiz dönemlerinde bu kural değişikliğini ve tam eşitlemeyi zamanlamanız önerilir.

## <a name="related-topic"></a>İlgili konu

- [Cihazlarda Uç Nokta için Microsoft Defender yönet'i Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
