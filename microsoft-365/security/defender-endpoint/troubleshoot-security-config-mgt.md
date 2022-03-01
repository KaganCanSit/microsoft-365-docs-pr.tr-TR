---
title: Uç Nokta için Microsoft Defender Güvenlik Yönetimi ile ilgili ekleme sorunlarını giderme
description: Uç Nokta için Microsoft Defender Için Güvenlik Yönetimi'ni kullanarak cihazların kullanımı sırasında ortaya çıkabilecek sorunları giderin.
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
ms.openlocfilehash: d6c3beb5a33a6d2323159917944e0f069b02035e
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "63014032"
---
# <a name="troubleshoot-onboarding-issues-related-to-security-management-for-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender Güvenlik Yönetimi ile ilgili ekleme sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [Farklı cihazlar için Uç Nokta için Microsoft Defender'ı Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Uç Nokta için Microsoft Defender Güvenlik Yönetimi, cihaz ya da posta sistemi Microsoft Endpoint Manager tarafından yönetil Microsoft Intune bir Microsoft Endpoint Configuration Manager , doğrudan Güvenlik 2013'den Uç Nokta için Microsoft Defender için güvenlik Endpoint Manager.
Uç Nokta için Microsoft Defender Güvenlik Yönetimi hakkında daha fazla bilgi için bkz. Uç Nokta ile cihazlar için [Microsoft Defender Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).

Uç nokta ekleme yönergeleri için Microsoft Defender Güvenlik Yönetimi için bkz. Uç Nokta [Güvenlik Yapılandırması Yönetimi için Microsoft Defender](security-config-management.md)

Ender 2010 ekleme, kusursuz şekilde tasarlanmıştır ve kullanıcı girişi gerektirmez. Bununla birlikte, ekleme sırasında sorunlarla karşılaşırsanız, Uç nokta için Microsoft Defender platformunda hataları  görüntüp giderebilirsiniz.

> [!NOTE]
> Yeni cihazlar için ekleme akışıyla ilgili sorunlar ediyorsanız, Uç nokta önkoşulları için [Microsoft Defender'ı](/mem/intune/protect/mde-security-integration#prerequisites) gözden geçirerek ekleme yönergelerinin uyul olduğundan emin olun.

İstemci çözümleyicisi hakkında daha fazla bilgi için bkz [. Uç Nokta İstemci Çözümleyicisi için Microsoft Defender'ı kullanarak algılayıcı durumu sorunlarını giderme](/microsoft-365/security/defender-endpoint/overview-client-analyzer).

## <a name="registering-domain-joined-computers-with-azure-active-directory"></a>Etki alanına katılmış bilgisayarları Azure Active Directory

Cihazları başarıyla Azure Active Directory için, aşağıdakilerin sağlanması gerekir:

- Bilgisayarlar, etki alanı denetleyicisiyle kimlik doğrulaması
- Bilgisayarlar, aşağıdaki Microsoft kaynaklarına kuruluş ağının içinden erişim sağlar:
  - https://enterpriseregistration.windows.net
  - https://login.microsoftonline.com
  - https://device.login.microsoftonline.com
- Azure AD Connect, bilgisayar nesnelerini eşitlerken yapılandırılır. Varsayılan olarak, bilgisayar OU'ları Azure AD connect eşitleme kapsamı içindedir. Bilgisayar nesneleri belirli kuruluş birimlerine (OU'lar) aitse, OU'ları Azure AD'de eşitlemek üzere Bağlan. Azure AD nesnelerini kullanarak bilgisayar nesnelerini eşitleme hakkında daha fazla bilgi Bağlan bkz[. Kuruluş birimi tabanlı filtreleme](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering#organizational-unitbased-filtering).

> [!IMPORTANT]
> Azure AD Connect, R2 Windows Server 2012 nesnelerini eşitlemez. Bunları Uç Nokta için Microsoft Defender Güvenlik Yönetimi için Azure AD'ye kaydetmeniz gerekirse, bu bilgisayar nesnelerini eşitleme kapsamına eklemek için Azure AD connect eşitleme kuralını özelleştirmeniz gerekir. Bkz[. Azure Active Directory Bağlan'de Bilgisayar Birleştirme kuralını uygulama Azure Active Directory Bağlan]().

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

## <a name="troubleshoot-errors-from-the-microsoft-defender-for-endpoint-portal"></a>Uç nokta için Microsoft Defender portalında hataları giderme

Güvenlik yöneticileri artık Uç Nokta için Microsoft Defender portalı üzerinden Uç Nokta ekleme için Microsoft Defender Güvenlik Yönetimi sorunlarını giderin.

Uç **noktalar Cihaz** \> **envanteri** içinde, **Yönetim kanalına** (örneğin MEM) göre filtrelemek için Yönetilen sütunu eklenmiştir.

:::image type="content" alt-text="Cihaz stoku sayfası resmi" source="./images/device-inventory-mde-error.png":::

Uç nokta ekleme işlemi için Microsoft Defender Güvenlik Yönetimi'ne geçemeyen tüm cihazların listesini görmek için, tabloya **MDE-Error ile filtre ekleyin**.

Yan panelde sorun giderme ayrıntılarını görmek için listede belirli bir cihazı seçin; hatanın temel nedenini ve ilgili belgeleri işaret edin.

:::image type="content" alt-text="Cihaz stoku sayfası filtrelenmiş resmi" source="./images/secconfig-mde-error.png":::

## <a name="run-microsoft-defender-for-endpoint-client-analyzer-on-windows"></a>Microsoft Defender for Endpoint Client Analyzer for Endpoint Analyzer on Windows

Uç nokta ekleme akışı için Microsoft Defender Güvenlik Yönetimi'nin tamamılamamayan uç noktalarda İstemci Çözümleyicisi'nin çalışır. İstemci çözümleyicisi hakkında daha fazla bilgi için bkz [. Uç Nokta İstemci Çözümleyicisi için Microsoft Defender'ı kullanarak algılayıcı durumu sorunlarını giderme](overview-client-analyzer.md).

İstemci Çözümleyicisi çıkış dosyası (MDE İstemci Çözümleyicisi Results.htm) önemli sorun giderme bilgileri sağlar:

- Cihaz işletim sistemi, Genel Cihaz Ayrıntıları bölümündeki Uç Nokta ekleme akışı için Microsoft Defender için Güvenlik Yönetimi kapsamında **olduğunu** doğrulama
- Cihazın Cihaz Yapılandırma Yönetimi Ayrıntıları'Azure Active Directory başarıyla **kayded olduğunu doğrulayın**

    ![İstemci çözümleyicisi sonuçları görüntüsü](images/client-analyzer-results.png)

Raporun **Ayrıntılı Sonuçları** bölümünde, İstemci Çözümleyicisi eyleme değiştirilebilir kılavuz da sağlar.

> [!TIP]
> Raporun Ayrıntılı Sonuçlar bölümünde "Hata" olmadığını denetleyin ve tüm "Uyarı" iletilerini gözden geçirmeyi denetleyin.

Örneğin, Güvenlik Yönetimi ekleme akışının bir parçası olarak, Uç Nokta Kiracısı için Microsoft Defender'daki Azure Active Directory Kiracı **Kimliği'nin** raporların Cihaz Yapılandırma Yönetimi Ayrıntıları bölümünde görünen SCP Kiracı Kimliği ile eşleşmesi gerekir. Uygunsa, rapor çıktısı bu doğrulamayı gerçekleştirmenizi önerecek.

![Ayrıntılı sonuçların resmi](images/detailed-results.png)

## <a name="general-troubleshooting"></a>Genel sorun giderme

AAD veya MEM'de ekli cihazı belirleyemediyseniz ve kayıt sırasında bir hata almadıysanız, `Computer\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\SenseCM\\EnrollmentStatus` kayıt defteri anahtarının denetlen size ek sorun giderme bilgileri sağlar.

:::image type="content" alt-text="Kayıt durumunun resmi." source="images/enrollment-status.png":::

Aşağıdaki tabloda, hatayı düzeltmek için deneyecekleri/denetlemeniz gereken hata ve yol tarifleri listele. Hata listesinin tamam olmadığını ve geçmişte müşterilerin karşılaştığı genel/yaygın hataları temel alıyor olduğunu unutmayın:

<br>

****

|Hata Kodu|Kayıt Durumu|Yönetici Eylemleri|
|---|---|---|
|`5-9`,`11-12`, `26-33`|Genel hata|Cihaz Uç Nokta için Microsoft Defender'a başarıyla eklendi. Bununla birlikte, güvenlik yapılandırması yönetim akışında bir hata oluştu. Bunun nedeni cihazda Uç nokta yönetim kanalı için [Microsoft Defender'ın önkoşullarının karşılanmaz olması olabilir](security-config-management.md). Cihazda İstemci [Çözümleyicisi'nin](https://aka.ms/BetaMDEAnalyzer) çalışıyor olması sorunun temel nedenini belirlemeye yardımcı olabilir. Bu işe yardımcı olmazsa lütfen destek ile iletişime geçin.|
|`13-14`,`20`,`24`,`25`|Bağlantı sorunu|Cihaz Uç Nokta için Microsoft Defender'a başarıyla eklendi. Bununla birlikte, güvenlik yapılandırması yönetim akışında bir bağlantı sorunundan dolayı söz konusu olabilir. Güvenlik duvarında [Azure Active Directory Microsoft Endpoint Manager uç noktalarının](security-config-management.md#connectivity-requirements) açık olduğunu doğrulayın.|
|`10`,`42`|Genel Karma katılma hatası|Cihaz Uç Nokta için Microsoft Defender'a başarıyla eklendi. Bununla birlikte, güvenlik yapılandırma yönetim akışında bir hata oluştu ve işletim sistemi karma birleştirmeyi gerçekleştiremedi. [OS düzeyindeki Azure Active Directory katılma hatalarını gidermek](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-current) için Karma veya karma cihazla birlikte katılan cihazlarda sorun gidermeyi kullanın.|
|`15`|Kiracı eşleşmeyenleri|Cihaz Uç Nokta için Microsoft Defender'a başarıyla eklendi. Bununla birlikte, güvenlik yapılandırma yönetimi akışında bir hata oluştu çünkü Uç Nokta için Microsoft Defender kiracı kimliğiniz bu Azure Active Directory eşleşmez. Uç nokta kiracısı Azure Active Directory Defender'daki kiracı kimliğinin, etki alanınız SCP girdisinde yer alan kiracı kimliğiyle eş olduğundan emin olun. Daha fazla ayrıntı için [, Uç Nokta için Microsoft Defender Güvenlik Yönetimi ile ilgili ekleme sorunlarını giderme](troubleshoot-security-config-mgt.md).|
|`16`,`17`|Karma hata - Hizmet Bağlantı Noktası|Cihaz Uç Nokta için Microsoft Defender'a başarıyla eklendi. Bununla birlikte, Hizmet Bağlantı Noktası (SCP) kaydı doğru yapılandırılmadı ve cihaz Azure AD'ye birleştiriemedi. Bunun nedeni SCP'nin SCP'nin DRS'ye Enterprise olabilir. SCP kaydının en iyi yöntemleri AAD ve SCP'nin yapılandırılmış olduğundan emin olun. Daha fazla bilgi için bkz [. Hizmet bağlantı noktasını yapılandırma](/azure/active-directory/devices/hybrid-azuread-join-manual#configure-a-service-connection-point).|
|`18`|Sertifika hatası|Cihaz Uç Nokta için Microsoft Defender'a başarıyla eklendi. Bununla birlikte, cihaz sertifikası hatası nedeniyle güvenlik yapılandırma yönetim akışında bir hata oluştu. Cihaz sertifikası farklı bir kiracıya aittir. Güvenilir sertifika profilleri oluştururken en iyi yöntemlerin [izlendiğini doğrulayın](/mem/intune/protect/certificates-trusted-root#create-trusted-certificate-profiles).|
|`36`|LDAP API hatası|Cihaz Uç Nokta için Microsoft Defender'a başarıyla eklendi. Bununla birlikte, güvenlik yapılandırması yönetim akışında bir hata oluştu. Ağ topolojisini doğrulayın ve karma birleştirme isteklerini tamamlamak için LDAP API'nin kullanılabilir olduğundan emin olun.|
|`37`|Şirket içi eşitleme sorunu|Cihaz Uç Nokta için Microsoft Defender'a başarıyla eklendi. Bununla birlikte, güvenlik yapılandırması yönetim akışında bir hata oluştu. Daha sonra yeniden deneyin. Bu işe yardımcı olursa bkz. [Azure AD ile nesne eşitlemesi sorunlarını giderme Bağlan.](/azure/active-directory/hybrid/tshoot-connect-objectsync)|
|`38`,`41`|DNS hatası|Cihaz Uç Nokta için Microsoft Defender'a başarıyla eklendi. Bununla birlikte, bir DNS hatası nedeniyle güvenlik yapılandırma yönetim akışında bir hata oluştu. Cihazda İnternet bağlantısını ve/veya DNS ayarlarını kontrol edin. Geçersiz DNS ayarları iş istasyonu tarafında olabilir. Active Directory, düzgün çalışmak için etki alanı DNS'lerini (yönlendiricinin adresini değil) kullanmasını gerektirir. Daha fazla bilgi için bkz [. Uç Nokta için Microsoft Defender Güvenlik Yönetimi ile ilgili ekleme sorunlarını giderme](troubleshoot-security-config-mgt.md).|
|`40`|Saat eşitleme sorunu|Cihaz Uç Nokta için Microsoft Defender'a başarıyla eklendi. Bununla birlikte, güvenlik yapılandırması yönetim akışında bir hata oluştu. Saatin doğru ayar olduğunu ve hatanın oluştuğu cihazda eşit olduğunu doğrulayın.|

## <a name="azure-active-directory-runtime-troubleshooting"></a>Azure Active Directory Çalışma Zamanı sorunlarını giderme

### <a name="azure-active-directory-runtime"></a>Azure Active Directory Çalışma Zamanı

Çalışma Zamanı'nın (AADRT) Azure Active Directory sorunlarını gidermek için ana mekanizma hata ayıklama izlemelerini toplamaktır. Azure Active Directory Çalışma Zamanı Windows **kimlik bd67e65c-9cc2-51d8-7399-0bb9899e75c1 ile ETW** sağlayıcısı kullanır. ETW izlemelerinin, hatanın yeniden çoğaltılmasıyla yakalanması gerekir (örneğin katılma hatası oluşursa, birleştirmenin gerçekleştirilmesi için AADRT API'lerine yapılan çağrıları kapsayan süre boyunca izlemenin etkinleştirilmesi gerekir).

AADRT günlüğünde tipik bir hata ve nasıl okundu hatası için aşağıya bakın:

![Olay özellikleri görüntüsü](images/event-properties.png)

İletide yer alan bilgilerden, hangi hatayla karşılaşıldı, Win32 API'sinin hatayı hangi hataya döndürüleni (varsa), hangi URL'nin (varsa) kullanılmış olduğunu ve hangi AAD Runtime API hatasıyla karşılaştığını anlamak mümkündür.

## <a name="instructions-for-applying-computer-join-rule-in-aad-connect"></a>AAD Bağlan'da Bilgisayar Birleştirme kuralını uygulama AAD Bağlan

Windows Server 2012 R2 etki alanına katılmış bilgisayarlarda Uç Nokta için Microsoft Defender Güvenlik Yönetimi için Azure AD Bağlan eşitleme kuralı "AD-Computer'den katıl" güncelleştirmesi gerekir. Bu, kuralın kopyasını değiştirerek ve değiştirerek elde edilebilir; bu da özgün "In from AD - Bilgisayar Birleştirmesi" kuralını devre dışı bırakacak. Azure AD Bağlan varsayılan olarak yerleşik kurallarda değişiklik yapmaya yönelik bu deneyimi sunar.

> [!NOTE]
>Bu değişikliklerin, çalışma olan sunucuya uygulanması AAD Bağlan gerekir. Dağıtılmış birden çok AAD Bağlan varsa, bu değişikliklerin tüm örneklere uygulanması gerekir.

1. Başlat menüsünden Eşitleme Kuralları Düzenleyicisi uygulamasını açın. Kural listesinde, **Ad – Bilgisayar Birleştirmesi'nde adlı kuralı bulun**. **Bu kuralın 'Öncelik' sütunundaki değeri not alma.**

    ![Eşitleme kuralları düzenleyicisinin görüntüsü](images/57ea94e2913562abaf93749d306dd6cf.png)

2. In **from AD – Computer Join kuralı vurgulanmış** olarak Düzenle'yi **seçin**. Özel Kullanım **Kuralı Onayı Düzenle iletişim** kutusunda Evet'i **seçin**.

   ![Düzenleme özel kullanım kuralı onay görüntüsü](images/8854440d6180a5580efda24110551c68.png)

3. Gelen **eşitleme kuralını düzenle** penceresi görüntülenir. Sunucu 2012R2'Windows bu kural kullanılarak eşitlen olacağını unutmayın, kural açıklamasını güncelleştirin. Öncelik değeri dışında diğer tüm seçenekleri değiştirmeden bırakın. Özgün kuraldan daha yüksek öncelik için bir değer girin (kural listesinde de görülür).

   ![Onay görüntüsü](images/ee0f29162bc3f2fbe666c22f14614c45.png)

4. Üç **kez Sonraki'yi** seçin. Bu, kuralın 'Dönüşümler' bölümüne gidin. Kuralın 'Coping filtresi' ve 'Birleşim kuralları' bölümlerinde hiçbir değişiklik yapmamak. 'Dönüştürmeler' bölümü artık gösteriliyor olmalı.

    ![Gelen eşitleme kuralının resmi](images/296f2c2a705e41233631c3784373bc23.png)

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

- [Farklı cihazlar için Uç Nokta için Microsoft Defender'ı Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
