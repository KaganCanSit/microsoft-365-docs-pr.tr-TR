---
title: Uç Nokta için Microsoft Defender'da yanlış pozitifleri/negatifleri ele alın
description: Uç Nokta için Microsoft Defender'da hatalı pozitifleri veya hatalı negatifleri işlemeyi öğrenin.
keywords: virüsten koruma, özel durum, dışlama, Uç Nokta için Microsoft Defender, hatalı pozitif, yanlış negatif, engellenen dosya, engellenen URL
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
- m365solution-overview
- m365solution-fpfn
ms.topic: how-to
ms.date: 12/02/2021
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs, yonghree, jcedola
ms.custom:
- FPFN
- admindeeplinkDEFENDER
ms.openlocfilehash: 5cae5a4b305846617130ecdf7c267ffc4ca13037
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603978"
---
# <a name="address-false-positivesnegatives-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'da yanlış pozitifleri/negatifleri ele alın

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Uç nokta koruma çözümlerinde hatalı pozitif, varlık aslında bir tehdit olmasa da algılanan ve kötü amaçlı olarak tanımlanan bir dosya veya işlem gibi bir varlıktır. Hatalı negatif, aslında kötü amaçlı olsa da tehdit olarak algılanmayan bir varlıktır. [Uç Nokta için Microsoft Defender](microsoft-defender-endpoint.md) dahil olmak üzere herhangi bir tehdit koruması çözümünde hatalı pozitif/negatifler oluşabilir.

:::image type="content" source="images/false-positives-overview.png" alt-text="Uç Nokta için Microsoft Defender portalında hatalı pozitif ve negatiflerin tanımı" lightbox="images/false-positives-overview.png":::

Neyse ki bu tür sorunları çözmek ve azaltmak için adımlar atılabilir. [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender) hatalı pozitif/negatifler görüyorsanız, güvenlik işlemleriniz aşağıdaki işlemi kullanarak bunları ele almak için adımlar atabilir:

1. [Uyarıları gözden geçirme ve sınıflandırma](#part-1-review-and-classify-alerts)
2. [Gerçekleştirilen düzeltme eylemlerini gözden geçirin](#part-2-review-remediation-actions)
3. [Dışlamaları gözden geçirme ve tanımlama](#part-3-review-or-define-exclusions)
4. [Analiz için varlık gönderme](#part-4-submit-a-file-for-analysis)
5. [Tehdit koruması ayarlarınızı gözden geçirin ve ayarlayın](#part-5-review-and-adjust-your-threat-protection-settings)

Bu makalede açıklanan görevleri gerçekleştirdikten sonra hatalı pozitif/negatiflerle ilgili sorun yaşamaya devam ediyorsanız yardım alabilirsiniz. [Bkz. Hala yardıma mı ihtiyacınız var?](#still-need-help)

:::image type="content" source="images/false-positives-step-diagram.png" alt-text="Hatalı pozitif ve negatifleri giderme adımları" lightbox="images/false-positives-step-diagram.png":::

> [!NOTE]
> Bu makale, [Uç Nokta için Microsoft Defender](microsoft-defender-endpoint.md) kullanan güvenlik operatörleri ve güvenlik yöneticileri için rehberlik olarak tasarlanmıştır.

## <a name="part-1-review-and-classify-alerts"></a>1. Bölüm: Uyarıları gözden geçirme ve sınıflandırma

Kötü amaçlı veya şüpheli olarak algılanan ve olmaması gereken bir [uyarı](alerts.md) görürseniz bu varlık için uyarıyı gizleyebilirsiniz. Hatalı pozitif olması gerekmeyen ancak önemli olmayan uyarıları da gizleyebilirsiniz. Uyarıları da sınıflandırmanızı öneririz.

Uyarılarınızı yönetmek ve doğru/yanlış pozitifleri sınıflandırmak, tehdit koruma çözümünüzü eğitmeye yardımcı olur ve zaman içinde hatalı pozitif veya hatalı negatiflerin sayısını azaltabilir. Bu adımların izlenmesi, güvenlik ekibinizin daha yüksek öncelikli iş öğelerine odaklanması için güvenlik operasyonları panonuzdaki kirliliği azaltmaya da yardımcı olur.

### <a name="determine-whether-an-alert-is-accurate"></a>Uyarının doğru olup olmadığını belirleme

Bir uyarıyı sınıflandırmadan veya gizlemeden önce, uyarının doğru mu, hatalı pozitif mi yoksa zararsız mı olduğunu belirleyin.

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

2. Gezinti bölmesinde **Uyarılar kuyruğu'na** tıklayın.

3. Uyarı hakkında daha fazla ayrıntı için bir uyarı seçin. (Bkz[. Uç Nokta için Microsoft Defender uyarıları gözden geçirme](review-alerts.md).)

4. Uyarı durumuna bağlı olarak, aşağıdaki tabloda açıklanan adımları izleyin:

   |Uyarı durumu|Yapılması gerekenler|
   |---|---|
   |Uyarı doğru|Uyarıyı atayın ve daha fazla [araştırın](investigate-alerts.md) .|
   |Uyarı hatalı pozitif|1. Uyarıyı hatalı pozitif olarak [sınıflandırın](#classify-an-alert) .<br/><br/>2. [Uyarıyı bastırın](#suppress-an-alert).<br/><br/>3. Uç Nokta için Microsoft Defender için [bir gösterge oluşturun](#indicators-for-microsoft-defender-for-endpoint).<br/><br/>4. [Analiz için Microsoft'a bir dosya gönderin](#part-4-submit-a-file-for-analysis).|
   |Uyarı doğru, ancak zararsız (önemsiz)|Uyarıyı gerçek pozitif olarak [sınıflandırın](#classify-an-alert) ve ardından [uyarıyı bastırın](#suppress-an-alert).|

### <a name="classify-an-alert"></a>Uyarıyı sınıflandırma

Uyarılar, Microsoft 365 Defender hatalı pozitifler veya gerçek pozitifler olarak sınıflandırılabilir. Uyarıları sınıflandırmak, Uç Nokta için Microsoft Defender eğitilmesine yardımcı olur ve böylece zaman içinde daha doğru uyarılar ve daha az yanlış uyarı görürsünüz.

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

2. **Uyarılar kuyruğu'nı** ve ardından bir uyarı seçin.

3. Seçili uyarı için **Eylemler** \> **Uyarıyı yönet'i** seçin. Açılır pencere bölmesi açılır.

4. **Uyarıyı yönet** bölümünde **Doğru uyarı** veya **Yanlış uyarı'yı** seçin. ( **Hatalı pozitifi** sınıflandırmak için Yanlış uyarı kullanın.)

> [!TIP]
> Uyarıları gizleme hakkında daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender uyarılarını yönetme](/microsoft-365/security/defender-endpoint/manage-alerts). Kuruluşunuz bir güvenlik bilgileri ve olay yönetimi (SIEM) sunucusu kullanıyorsa, orada da bir engelleme kuralı tanımladığınızdan emin olun.

### <a name="suppress-an-alert"></a>Uyarıyı gizleme

Hatalı pozitif veya gerçek pozitif olan ancak önemli olmayan olaylar için uyarılarınız varsa, bu uyarıları Microsoft 365 Defender'da gizleyebilirsiniz. Uyarıların gizlenmesi, güvenlik işlemleri panonuzdaki gürültüyü azaltmaya yardımcı olur.

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

2. Gezinti bölmesinde **Uyarılar kuyruğu'na** tıklayın.

3. **Ayrıntılar** bölmesini açmak için gizlemesini istediğiniz bir uyarı seçin.

4. **Ayrıntılar** bölmesinde üç noktayı (**...**) ve ardından **Gizleme kuralı oluştur'u** seçin.

5. Gizleme kuralınızın tüm ayarlarını belirtin ve **kaydet'i** seçin.

> [!TIP]
> Gizleme kurallarıyla ilgili yardıma mı ihtiyacınız var? Bkz [. Uyarıyı gizleme ve yeni bir gizleme kuralı oluşturma](/microsoft-365/security/defender-endpoint/manage-alerts#suppress-an-alert-and-create-a-new-suppression-rule).

## <a name="part-2-review-remediation-actions"></a>2. Bölüm: Düzeltme eylemlerini gözden geçirme

Dosyayı karantinaya alma veya işlemi durdurma gibi [düzeltme eylemleri](manage-auto-investigation.md#remediation-actions), tehdit olarak algılanan varlıklarda (dosyalar gibi) gerçekleştirilir. Otomatik araştırma ve Microsoft Defender Virüsten Koruma aracılığıyla çeşitli düzeltme eylemleri otomatik olarak gerçekleştirilir:

- Dosyayı karantinaya al
- Kayıt defteri anahtarını kaldırma
- İşlemi sonlandırma
- Hizmeti durdurma
- Sürücüyü devre dışı bırakma
- Zamanlanmış görevi kaldırma

Virüsten koruma taraması başlatma veya araştırma paketi toplama gibi diğer eylemler el ile veya [Canlı Yanıt](live-response.md) aracılığıyla gerçekleştirilir. Canlı Yanıt aracılığıyla gerçekleştirilen eylemler geri alınamaz.

Uyarılarınızı gözden geçirdikten sonra, sonraki adımınız [düzeltme eylemlerini gözden geçirmektir](manage-auto-investigation.md). Hatalı pozitif sonuçlar sonucunda herhangi bir eylem yapıldıysa, çoğu düzeltme eylemini geri alabilirsiniz. Özellikle şunları yapabilirsiniz:

- [karantinaya alınmış bir dosyayı İşlem Merkezi'nden geri yükleme](#restore-a-quarantined-file-from-the-action-center)
- [Aynı anda birden çok eylemi geri alma](#undo-multiple-actions-at-one-time)
- [Bir dosyayı birden çok cihazda karantinadan kaldırma](#remove-a-file-from-quarantine-across-multiple-devices). ve
- [Dosyayı karantinadan geri yükleyin](#restore-file-from-quarantine)

Hatalı pozitif sonuçlar sonucunda gerçekleştirilen eylemleri gözden geçirmeyi ve geri almayı bitirdiğinizde [, dışlamaları gözden geçirmeye veya tanımlamaya](#part-3-review-or-define-exclusions) devam edin.

### <a name="review-completed-actions"></a>Tamamlanan eylemleri gözden geçirme

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalının</a> sol gezinti bölmesinde **İşlem merkezi'ne** tıklayın.

2. Gerçekleştirilen eylemlerin listesini görüntülemek için **Geçmiş** sekmesini seçin.

3. Gerçekleştirilen düzeltme eylemi hakkında daha fazla ayrıntı görüntülemek için bir öğe seçin.

### <a name="restore-a-quarantined-file-from-the-action-center"></a>karantinaya alınmış bir dosyayı İşlem Merkezi'nden geri yükleme

1. Microsoft 365 Defender portalının sol gezinti bölmesinde **İşlem merkezi'ne** tıklayın.

2. **Geçmiş** sekmesinde, geri almak istediğiniz eylemi seçin.

3. Açılır bölmede **Geri Al'ı** seçin. Bu yöntemle eylem geri alınamazsa **Geri Al** düğmesini görmezsiniz. (Daha fazla bilgi için bkz. [Tamamlanan eylemleri geri alma](manage-auto-investigation.md#undo-completed-actions).)

### <a name="undo-multiple-actions-at-one-time"></a>Aynı anda birden çok eylemi geri alma

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalının</a> sol gezinti bölmesinde **İşlem merkezi'ne** tıklayın.

2. **Geçmiş** sekmesinde, geri almak istediğiniz eylemleri seçin.

3. Ekranın sağ tarafındaki bölmede **Geri Al'ı** seçin.

### <a name="remove-a-file-from-quarantine-across-multiple-devices"></a>Bir dosyayı birden çok cihazda karantinadan kaldırma

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/autoir-quarantine-file-1.png" alt-text="Karantina dosyası" lightbox="images/autoir-quarantine-file-1.png":::

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalının</a> sol gezinti bölmesinde **İşlem merkezi'ne** tıklayın.

2. **Geçmiş** sekmesinde, Eylem türü Karantina dosyası olan bir **dosya** seçin.

3. Ekranın sağ tarafındaki bölmede **Bu dosyanın X daha fazla örneğine uygula'yı** ve ardından **Geri Al'ı** seçin.

### <a name="restore-file-from-quarantine"></a>Dosyayı karantinadan geri yükleyin

Bir araştırmadan sonra temiz olduğunu belirlediyseniz dosyayı geri alabilir ve karantinadan kaldırabilirsiniz. Dosyanın karantinaya alındığı her cihazda aşağıdaki komutu çalıştırın.

1. Cihazda yükseltilmiş bir komut satırı istemi açın:

   1. **Başlangıç'a** gidin ve _cmd_ yazın.
   2. **Komut istemi'ne** sağ tıklayın ve **Yönetici olarak çalıştır'ı** seçin.

2. Aşağıdaki komutu girin ve **Enter tuşuna** basın:

    ```console
    "%ProgramFiles%\Windows Defender\MpCmdRun.exe" -Restore -Name EUS:Win32/CustomEnterpriseBlock -All
    ```

    > [!IMPORTANT]
    > Bazı senaryolarda **ThreatName** olarak `EUS:Win32/CustomEnterpriseBlock!cl`görünebilir. Uç Nokta için Defender, son 30 gün içinde bu cihazda karantinaya alınan tüm özel engellenen dosyaları geri yükler.
    >
    > Olası bir ağ tehdidi olarak karantinaya alınan bir dosya kurtarılamayabilir. Kullanıcı karantinadan sonra dosyayı geri yüklemeyi denerse, bu dosyaya erişilemiyor olabilir. Bunun nedeni sistemin artık dosyaya erişmek için ağ kimlik bilgilerine sahip olmaması olabilir. Genellikle bu, bir sistemde veya paylaşılan klasörde geçici oturum açmanın ve erişim belirteçlerinin süresinin dolmasının bir sonucudur.

3. Ekranın sağ tarafındaki bölmede **Bu dosyanın X daha fazla örneğine uygula'yı** ve ardından **Geri Al'ı** seçin.

## <a name="part-3-review-or-define-exclusions"></a>3. Bölüm: Dışlamaları gözden geçirme veya tanımlama

Dışlama, düzeltme eylemleri için özel durum olarak belirttiğiniz dosya veya URL gibi bir varlıktır. Dışlanan varlık yine algılanabilir, ancak bu varlık üzerinde hiçbir düzeltme eylemi yapılmaz. Başka bir ifadeyle, algılanan dosya veya işlem durdurulamaz, karantinaya gönderilmez, kaldırılmaz veya Uç Nokta için Microsoft Defender tarafından başka bir şekilde değiştirilmez.

Uç Nokta için Microsoft Defender genelinde dışlamaları tanımlamak için aşağıdaki görevleri gerçekleştirin:

- [Microsoft Defender Virüsten Koruma için dışlamaları tanımlama](#exclusions-for-microsoft-defender-antivirus)
- [Uç Nokta için Microsoft Defender için "izin ver" göstergeleri oluşturma](#indicators-for-microsoft-defender-for-endpoint)

> [!NOTE]
> Microsoft Defender Virüsten Koruma dışlamaları yalnızca virüsten koruma için geçerlidir, diğer Uç Nokta için Microsoft Defender özellikleri için geçerli değildir. Dosyaları geniş kapsamlı bir şekilde dışlamak için Microsoft Defender Virüsten Koruma için dışlamaları ve Uç Nokta için Microsoft Defender [için özel göstergeleri](/microsoft-365/security/defender-endpoint/manage-indicators) kullanın.

Bu bölümdeki yordamlarda dışlamaların ve göstergelerin nasıl tanımlanacağı açıklanmaktadır.

### <a name="exclusions-for-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma için Dışlamalar

Genel olarak, Microsoft Defender Virüsten Koruma için dışlamalar tanımlamanız gerekmez. Dışlamaları düzenli olarak tanımladığınızdan ve yalnızca hatalı pozitif sonuçlara neden olan dosyaları, klasörleri, işlemleri ve işlem tarafından açılan dosyaları eklediğinizden emin olun. Ayrıca, tanımlı dışlamalarınızı düzenli olarak gözden geçirmeyi unutmayın. Virüsten koruma dışlamalarınızı tanımlamak veya düzenlemek için [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) kullanmanızı öneririz; ancak [grup ilkesi](/azure/active-directory-domain-services/manage-group-policy) gibi diğer yöntemleri kullanabilirsiniz (bkz. [Uç Nokta için Microsoft Defender yönetme](manage-mde-post-migration.md).

> [!TIP]
> Virüsten koruma dışlamalarıyla ilgili yardıma mı ihtiyacınız var? Bkz [. Microsoft Defender Virüsten Koruma taramaları için dışlamaları yapılandırma ve doğrulama](configure-exclusions-microsoft-defender-antivirus.md).

#### <a name="use-microsoft-endpoint-manager-to-manage-antivirus-exclusions-for-existing-policies"></a>Virüsten koruma dışlamalarını yönetmek için Microsoft Endpoint Manager kullanma (mevcut ilkeler için)

1. Microsoft Endpoint Manager yönetim merkezine (<https://endpoint.microsoft.com>) gidin ve oturum açın.

2. **Endpoint security** \> **Virüsten Koruma'yı** seçin ve ardından mevcut bir ilkeyi seçin. (Mevcut bir ilkeniz yoksa veya yeni bir ilke oluşturmak istiyorsanız, [sonraki yordama](#use-microsoft-endpoint-manager-to-create-a-new-antivirus-policy-with-exclusions) atlayın).

3. **Özellikler'i** seçin ve **Yapılandırma ayarları'nın** yanında **Düzenle'yi** seçin.

4. **Microsoft Defender Virüsten Koruma Dışlamaları'nın** kapsamını genişletin ve dışlamalarınızı belirtin.

5. **Gözden Geçir + kaydet'i** ve ardından **Kaydet'i** seçin.

#### <a name="use-microsoft-endpoint-manager-to-create-a-new-antivirus-policy-with-exclusions"></a>Dışlamalarla yeni bir virüsten koruma ilkesi oluşturmak için Microsoft Endpoint Manager kullanma

1. Microsoft Endpoint Manager yönetim merkezine (<https://endpoint.microsoft.com>) gidin ve oturum açın.

2. **Uç nokta güvenliği** \> **Virüsten Koruma** \> **+ İlke Oluştur'u** seçin.

3. Bir platform seçin (**Windows 10 ve üzeri**, **macOS** veya **Windows 10 ve Windows Server** gibi).

4. **Profil** için **Microsoft Defender Virüsten Koruma dışlamaları'nı** ve ardından **Oluştur'u** seçin.

5. Profil için bir ad ve açıklama belirtin ve ardından **İleri'yi** seçin.

6. **Yapılandırma ayarları** sekmesinde virüsten koruma dışlamalarınızı belirtin ve **İleri'yi** seçin.

7. **Kapsam etiketleri** sekmesinde, kuruluşunuzda kapsam etiketleri kullanıyorsanız, oluşturduğunuz ilke için kapsam etiketlerini belirtin. (Bkz [. Kapsam etiketleri](/mem/intune/fundamentals/scope-tags).)

8. **Atamalar** sekmesinde, ilkenizin uygulanacağı kullanıcıları ve grupları belirtin ve ardından **İleri'yi** seçin. (Atamalarla ilgili yardıma ihtiyacınız varsa bkz. [Microsoft Intune'de kullanıcı ve cihaz profilleri atama](/mem/intune/configuration/device-profile-assign).)

9. **Gözden Geçir + oluştur** sekmesinde ayarları gözden geçirin ve **oluştur'u** seçin.

### <a name="indicators-for-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender göstergeleri

[Göstergeler](/microsoft-365/security/defender-endpoint/manage-indicators) (özellikle, güvenliği ihlal göstergeleri veya IC'ler), güvenlik operasyonları ekibinizin varlıkların algılanmasını, önlenmesini ve dışlanmasını tanımlamasını sağlar. Örneğin, Uç Nokta için Microsoft Defender'deki taramalardan ve düzeltme eylemlerinden atlanacak belirli dosyaları belirtebilirsiniz. Ya da göstergeler belirli dosyalar, IP adresleri veya URL'ler için uyarı oluşturmak için kullanılabilir.

Varlıkları Uç Nokta için Microsoft Defender için dışlamalar olarak belirtmek için, bu varlıklar için "izin ver" göstergeleri oluşturun. Uç Nokta için Microsoft Defender bu tür "izin ver" göstergeleri [yeni nesil koruma](microsoft-defender-antivirus-in-windows-10.md), [uç nokta algılama ve yanıt ve](overview-endpoint-detection-response.md) [otomatik araştırma & düzeltme](/microsoft-365/security/defender-endpoint/automated-investigations) için geçerlidir.

"İzin ver" göstergeleri şu için oluşturulabilir:

- [Dosyalar](#indicators-for-files)
- [IP adresleri, URL'ler ve etki alanları](#indicators-for-ip-addresses-urls-or-domains)
- [Uygulama sertifikaları](#indicators-for-application-certificates)

:::image type="content" source="images/false-positives-indicators.png" alt-text="Gösterge türleri" lightbox="images/false-positives-indicators.png":::

#### <a name="indicators-for-files"></a>Dosyalar için göstergeler

[Yürütülebilir dosya gibi bir dosya için "izin ver" göstergesi oluşturduğunuzda](/microsoft-365/security/defender-endpoint/indicator-file), kuruluşunuzun kullandığı dosyaların engellenmesini önlemeye yardımcı olur. Dosyalar ve gibi `.exe` `.dll` taşınabilir yürütülebilir (PE) dosyaları içerebilir.

Dosyalar için göstergeler oluşturmadan önce aşağıdaki gereksinimlerin karşılandığından emin olun:

- Microsoft Defender Virüsten Koruma, bulut tabanlı koruma etkin olarak yapılandırıldı (bkz. [Bulut tabanlı korumayı yönetme](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus))
- Kötü amaçlı yazılımdan koruma istemcisi sürümü 4.18.1901.x veya üzeridir
- Cihazlar Windows 10, sürüm 1703 veya üzeri veya Windows 11 çalıştırıyor; Windows Server 2016, Windows Server 2019 veya Windows Server 2022
- [Engelle veya izin ver özelliği açık](/microsoft-365/security/defender-endpoint/advanced-features)

#### <a name="indicators-for-ip-addresses-urls-or-domains"></a>IP adresleri, URL'ler veya etki alanları göstergeleri

[Bir IP adresi, URL veya etki alanı için "izin ver" göstergesi oluşturduğunuzda](/microsoft-365/security/defender-endpoint/indicator-ip-domain), kuruluşunuzun kullandığı sitelerin veya IP adreslerinin engellenmesini önlemeye yardımcı olur.

IP adresleri, URL'ler veya etki alanları için göstergeler oluşturmadan önce aşağıdaki gereksinimlerin karşılandığından emin olun:

- Uç Nokta için Defender'da ağ koruması blok modunda etkinleştirilir (bkz [. Ağ korumasını etkinleştirme](/microsoft-365/security/defender-endpoint/enable-network-protection))
- Kötü amaçlı yazılımdan koruma istemcisi sürümü 4.18.1906.x veya üzeridir
- Cihazlar Windows 10, sürüm 1709 veya üzeri ya da Windows 11 çalıştırıyor

özel ağ göstergeleri [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender) açılır. Daha fazla bilgi edinmek için bkz [. Gelişmiş özellikler](/microsoft-365/security/defender-endpoint/advanced-features).

#### <a name="indicators-for-application-certificates"></a>Uygulama sertifikaları için göstergeler

[Bir uygulama sertifikası için "izin ver" göstergesi](/microsoft-365/security/defender-endpoint/indicator-certificates) oluşturduğunuzda, kuruluşunuzun kullandığı dahili olarak geliştirilmiş uygulamalar gibi uygulamaların engellenmesini önlemeye yardımcı olur. `.CER` veya `.PEM` dosya uzantıları desteklenir.

Uygulama sertifikaları için göstergeler oluşturmadan önce aşağıdaki gereksinimlerin karşılandığından emin olun:

- Microsoft Defender Virüsten Koruma, bulut tabanlı koruma etkin olarak yapılandırıldı (bkz. [Bulut tabanlı korumayı yönetme](deploy-manage-report-microsoft-defender-antivirus.md)
- Kötü amaçlı yazılımdan koruma istemcisi sürümü 4.18.1901.x veya üzeridir
- Cihazlar Windows 10, sürüm 1703 veya üzeri veya Windows 11 çalıştırıyor; Windows Server 2016, Windows Server 2019 veya Windows Server 2022
- Virüs ve tehdit koruması tanımları güncel

> [!TIP]
> Gösterge oluşturduğunuzda, bunları tek tek tanımlayabilir veya aynı anda birden çok öğeyi içeri aktarabilirsiniz. Tek bir kiracı için 15.000 gösterge sınırı olduğunu unutmayın. Ayrıca, önce dosya karması bilgileri gibi belirli ayrıntıları toplamanız gerekebilir. [Göstergeler oluşturmadan](manage-indicators.md) önce önkoşulları gözden geçirmeyi unutmayın.

## <a name="part-4-submit-a-file-for-analysis"></a>Bölüm 4: Analiz için bir dosya gönderme

Dosyalar ve dosyasız algılamalar gibi varlıkları analiz için Microsoft'a gönderebilirsiniz. Microsoft güvenlik araştırmacıları tüm gönderileri analiz eder ve sonuçları Uç Nokta için Microsoft Defender tehdit koruma özelliklerini bilgilendirmeye yardımcı olur. Gönderim sitesinde oturum açtığınızda, gönderimlerinizi izleyebilirsiniz.

### <a name="submit-a-file-for-analysis"></a>Analiz için dosya gönderme

Hatalı bir şekilde kötü amaçlı olarak algılanmış veya yanıtsız bir dosyanız varsa, dosyayı analize göndermek için bu adımları izleyin.

1. Buradaki yönergeleri gözden geçirin: [Dosyaları analiz için gönderin](/windows/security/threat-protection/intelligence/submission-guide).

2. [Microsoft Güvenlik Zekası gönderim sitesini](https://www.microsoft.com/wdsi/filesubmission) ziyaret edin (https://www.microsoft.com/wdsi/filesubmission)ve dosyalarınızı gönderin).

### <a name="submit-a-fileless-detection-for-analysis"></a>Analiz için dosyasız algılama gönderme

Davranışa göre kötü amaçlı yazılım olarak bir şey algılandıysa ve dosyanız yoksa, dosyanızı `Mpsupport.cab` analiz için gönderebilirsiniz. .cabdosyasını, *Windows 10* veya Windows 11 üzerinde Microsoft Kötü Amaçlı Yazılımdan Koruma Command-Line Yardımcı Programı (MPCmdRun.exe) aracını kullanarak alabilirsiniz.

1. adresine ` C:\ProgramData\Microsoft\Windows Defender\Platform\<version>`gidin ve yönetici olarak çalıştırın `MpCmdRun.exe` .

2. `mpcmdrun.exe -GetFiles` yazın ve ardından **Enter**'a basın.

   Çeşitli tanılama günlüklerini içeren bir .cab dosyası oluşturulur. Dosyanın konumu komut isteminin çıkışında belirtilir. Varsayılan olarak, konumu şeklindedir `C:\ProgramData\Microsoft\Microsoft Defender\Support\MpSupportFiles.cab`.

3. Buradaki yönergeleri gözden geçirin: [Dosyaları analiz için gönderin](/windows/security/threat-protection/intelligence/submission-guide).

4. [Microsoft Güvenlik Zekası gönderim sitesini](https://www.microsoft.com/wdsi/filesubmission) ziyaret edin (https://www.microsoft.com/wdsi/filesubmission)ve .cab dosyalarınızı gönderin.

### <a name="what-happens-after-a-file-is-submitted"></a>Dosya gönderildikten sonra ne olur?

Gönderiniz, bir analist davanızı işlemeye başlamadan önce bile size en son belirlemeyi sağlamak için sistemlerimiz tarafından hemen taranır. Bir dosya zaten bir analist tarafından gönderilmiş ve işlenmiş olabilir. Bu gibi durumlarda, hızlı bir şekilde bir belirleme yapılır.

Henüz işlenmemiş gönderimler için, analiz için aşağıdaki gibi öncelikleri belirlenir:

- Çok sayıda bilgisayarı etkileme olasılığı olan yaygın dosyalara daha yüksek öncelik verilir.
- Kimliği doğrulanmış müşterilere, özellikle de geçerli [Yazılım Güvencesi Kimliklerine (SAID)](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx) sahip kurumsal müşterilere daha yüksek öncelik verilir.
- SAID sahipleri tarafından yüksek öncelikli olarak işaretlenmiş gönderimlere hemen dikkat edilir.

Gönderiminizle ilgili güncelleştirmeleri denetlemek için [Microsoft Güvenlik Zekası gönderim sitesinde](https://www.microsoft.com/wdsi/filesubmission) oturum açın.

> [!TIP]
> Daha fazla bilgi edinmek için bkz. [Dosyaları analiz için gönderme](/windows/security/threat-protection/intelligence/submission-guide#how-does-microsoft-prioritize-submissions).

## <a name="part-5-review-and-adjust-your-threat-protection-settings"></a>5. Bölüm: Tehdit koruması ayarlarınızı gözden geçirin ve ayarlayın

Uç Nokta için Microsoft Defender, çeşitli özellikler ve özellikler için ayarlara ince ayar yapma da dahil olmak üzere çok çeşitli seçenekler sunar. Çok sayıda hatalı pozitif sonuç alıyorsanız kuruluşunuzun tehdit koruması ayarlarını gözden geçirmeyi unutmayın. Aşağıdakiler için bazı ayarlamalar yapmanız gerekebilir:

- [Bulut tabanlı koruma](#cloud-delivered-protection)
- [İstenmeyebilecek uygulamalar için düzeltme](#remediation-for-potentially-unwanted-applications)
- [Otomatik araştırma ve düzeltme](#automated-investigation-and-remediation)

### <a name="cloud-delivered-protection"></a>Bulut tabanlı koruma

Microsoft Defender Virüsten Koruma için bulut tabanlı koruma düzeyinizi denetleyin. Varsayılan olarak, bulut tabanlı koruma **Yapılandırılmadı** olarak ayarlanır ve bu da çoğu kuruluş için normal bir koruma düzeyine karşılık gelir. Bulut tabanlı korumanız **Yüksek**, **Yüksek +** veya **Sıfır tolerans** olarak ayarlandıysa, daha fazla sayıda hatalı pozitifle karşılaşabilirsiniz.

> [!TIP]
> Bulut tabanlı korumanızı yapılandırma hakkında daha fazla bilgi edinmek için bkz. [Bulut tabanlı koruma düzeyini belirtme](/windows/security/threat-protection/microsoft-defender-antivirus/specify-cloud-protection-level-microsoft-defender-antivirus).

Bulut tabanlı koruma ayarlarınızı düzenlemek veya ayarlamak için [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) kullanmanızı öneririz; ancak [grup ilkesi](/azure/active-directory-domain-services/manage-group-policy) gibi diğer yöntemleri kullanabilirsiniz (bkz. [Uç Nokta için Microsoft Defender yönetme](manage-mde-post-migration.md).

#### <a name="use-microsoft-endpoint-manager-to-review-and-edit-cloud-delivered-protection-settings-for-existing-policies"></a>Bulut tabanlı koruma ayarlarını gözden geçirmek ve düzenlemek için Microsoft Endpoint Manager kullanma (mevcut ilkeler için)

1. Microsoft Endpoint Manager yönetim merkezine (<https://endpoint.microsoft.com>) gidin ve oturum açın.

2. **Endpoint security** \> **Virüsten Koruma'yı** ve ardından mevcut bir ilkeyi seçin. (Mevcut bir ilkeniz yoksa veya yeni bir ilke oluşturmak istiyorsanız, [sonraki yordama](#use-microsoft-endpoint-manager-to-set-cloud-delivered-protection-settings-for-a-new-policy) atlayın).

3. **Yönet'in** altında **Özellikler'i** seçin. Ardından **Yapılandırma ayarları'nın** yanındaki **Düzenle'yi** seçin.

4. **Bulut koruması'nı** genişletin ve **Bulut tabanlı koruma düzeyi** satırında geçerli ayarınızı gözden geçirin. Hatalı pozitif sonuç alma olasılığını azaltırken güçlü koruma sağlayan bulut tabanlı korumayı **Yapılandırılmadı olarak** ayarlamanızı öneririz.

5. **Gözden Geçir + kaydet'i** ve ardından **Kaydet'i** seçin.

#### <a name="use-microsoft-endpoint-manager-to-set-cloud-delivered-protection-settings-for-a-new-policy"></a>Bulut tabanlı koruma ayarlarını ayarlamak için Microsoft Endpoint Manager kullanma (yeni bir ilke için)

1. Microsoft Endpoint Manager yönetim merkezine (<https://endpoint.microsoft.com>) gidin ve oturum açın.

2. **Uç nokta güvenliği** \> **Virüsten Koruma** \> **+ İlke oluştur'u** seçin.

3. **Platform** için bir seçenek belirleyin ve **profil için** **Virüsten Koruma'yı** veya **Microsoft Defender Virüsten Koruma'yı** seçin (belirli bir seçenek **Platform** için ne seçtiğinize bağlıdır.) Ardından **Oluştur'u** seçin.

4. **Temel Bilgiler** sekmesinde, ilke için bir ad ve açıklama belirtin. Ardından **İleri'yi** seçin.

5. **Yapılandırma ayarları** sekmesinde **Bulut koruması'nı** genişletin ve aşağıdaki ayarları belirtin:

   - **Bulut tabanlı korumayı aç** seçeneğini **Evet** olarak ayarlayın.
   - **Bulut tabanlı koruma düzeyini** **Yapılandırılmadı olarak** ayarlayın. (Bu düzey varsayılan olarak güçlü bir koruma düzeyi sağlarken hatalı pozitif sonuç alma olasılığını azaltır.)

6. **Kapsam etiketleri** sekmesinde, kuruluşunuzda kapsam etiketleri kullanıyorsanız ilke için kapsam etiketlerini belirtin. (Bkz [. Kapsam etiketleri](/mem/intune/fundamentals/scope-tags).)

7. **Atamalar** sekmesinde, ilkenizin uygulanacağı kullanıcıları ve grupları belirtin ve ardından **İleri'yi** seçin. (Atamalarla ilgili yardıma ihtiyacınız varsa bkz. [Microsoft Intune'de kullanıcı ve cihaz profilleri atama](/mem/intune/configuration/device-profile-assign).)

8. **Gözden Geçir + oluştur** sekmesinde ayarları gözden geçirin ve **oluştur'u** seçin.

### <a name="remediation-for-potentially-unwanted-applications"></a>İstenmeyebilecek uygulamalar için düzeltme

İstenmeyebilecek uygulamalar (PUA), cihazların yavaş çalışmasına, beklenmeyen reklamlar görüntülemesine veya beklenmeyen veya istenmeyen olabilecek başka yazılımlar yüklemesine neden olabilen bir yazılım kategorisidir. PUA'ya örnek olarak reklam yazılımları, paketleme yazılımları ve güvenlik ürünleriyle farklı davranan kaçış yazılımları verilebilir. PUA kötü amaçlı yazılım olarak kabul edilmese de, bazı yazılım türleri davranışlarına ve itibarına göre PUA'dır.

> [!TIP]
> PUA hakkında daha fazla bilgi edinmek için bkz. [İstenmeyebilecek uygulamaları algılama ve engelleme](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).

Kuruluşunuzun kullandığı uygulamalara bağlı olarak, PUA koruma ayarlarınızın bir sonucu olarak hatalı pozitif sonuçlar alıyor olabilirsiniz. Gerekirse, PUA korumasını bir süre denetim modunda çalıştırmayı veya kuruluşunuzdaki cihazların bir alt kümesine PUA koruması uygulamayı göz önünde bulundurun. PUA koruması, Microsoft Edge tarayıcısı ve Microsoft Defender Virüsten Koruma için yapılandırılabilir.

PUA koruma ayarlarını düzenlemek veya ayarlamak için [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) kullanmanızı öneririz; ancak [grup ilkesi](/azure/active-directory-domain-services/manage-group-policy) gibi diğer yöntemleri kullanabilirsiniz (bkz. [Uç Nokta için Microsoft Defender yönetme](manage-mde-post-migration.md).

#### <a name="use-microsoft-endpoint-manager-to-edit-pua-protection-for-existing-configuration-profiles"></a>PUA korumasını düzenlemek için Microsoft Endpoint Manager kullanma (mevcut yapılandırma profilleri için)

1. Microsoft Endpoint Manager yönetim merkezine (<https://endpoint.microsoft.com>) gidin ve oturum açın.

2. **Cihazlar** \> **Yapılandırma profilleri'ni** ve ardından mevcut bir ilkeyi seçin. (Mevcut bir ilkeniz yoksa veya yeni bir ilke oluşturmak istiyorsanız sonraki [yordama](#use-microsoft-endpoint-manager-to-set-pua-protection-for-a-new-configuration-profile) atlayın.)

3. **Yönet'in** altında **Özellikler'i** seçin ve yapılandırma **ayarları'nın** yanındaki **Düzenle'yi** seçin.

4. **Yapılandırma ayarları** sekmesinde ekranı aşağı kaydırın ve **Microsoft Defender Virüsten Koruma'yı** genişletin.

5. **İstenmeyebilecek uygulamaları algıla** ayarını **Denetim** olarak ayarlayın. (Bunu kapatabilirsiniz, ancak denetim modunu kullanarak algılamaları görebilirsiniz.)

6. **Gözden Geçir + kaydet'i** ve ardından **Kaydet'i** seçin.

#### <a name="use-microsoft-endpoint-manager-to-set-pua-protection-for-a-new-configuration-profile"></a>PUA korumasını ayarlamak için Microsoft Endpoint Manager kullanma (yeni bir yapılandırma profili için)

1. Microsoft Endpoint Manager yönetim merkezine (<https://endpoint.microsoft.com>) gidin ve oturum açın.

2. **Cihazlar** \> **Yapılandırma profilleri** \> **+ Profil oluştur'u** seçin.

3. **Platform** için **Windows 10 ve üzerini** seçin ve **Profil** için **Cihaz kısıtlamaları'nı** seçin.

4. **Temel Bilgiler** sekmesinde, ilkeniz için bir ad ve açıklama belirtin. Ardından **İleri'yi** seçin.

5. **Yapılandırma ayarları** sekmesinde ekranı aşağı kaydırın ve **Microsoft Defender Virüsten Koruma'yı** genişletin.

6. **İstenmeyebilecek uygulamaları algıla'yı** **Denetim** olarak ayarlayın ve **İleri'yi** seçin. (PUA korumasını kapatabilirsiniz, ancak denetim modunu kullanarak algılamaları görebilirsiniz.)

7. **Atamalar** sekmesinde, ilkenizin uygulanacağı kullanıcıları ve grupları belirtin ve ardından **İleri'yi** seçin. (Atamalarla ilgili yardıma ihtiyacınız varsa bkz. [Microsoft Intune'de kullanıcı ve cihaz profilleri atama](/mem/intune/configuration/device-profile-assign).)

8. **Uygulanabilirlik Kuralları** sekmesinde, ilkeye dahil etmek veya ilkeden dışlamak için işletim sistemi sürümlerini veya sürümlerini belirtin. Örneğin, ilkeyi tüm cihazlara belirli Windows 10 sürümlerine uygulanacak şekilde ayarlayabilirsiniz. Ardından **İleri'yi** seçin.

9. **Gözden Geçir + oluştur** sekmesinde ayarlarınızı gözden geçirin ve **oluştur'u** seçin.

### <a name="automated-investigation-and-remediation"></a>Otomatik araştırma ve düzeltme

[Otomatik araştırma ve düzeltme](automated-investigations.md) (AIR) özellikleri, uyarıları incelemek ve ihlalleri çözmek için anında işlem yapmak üzere tasarlanmıştır. Uyarılar tetiklendikçe ve otomatik bir araştırma çalıştırıldığında, araştırılan her kanıt parçası için bir karar oluşturulur. Kararlarda *Kötü Amaçlı*, *Şüpheli* veya *Tehdit bulunamadı* olabilir.

Kuruluşunuz için ayarlanan [otomasyon düzeyine](/microsoft-365/security/defender-endpoint/automation-levels) ve diğer güvenlik ayarlarına bağlı olarak, *Kötü Amaçlı* veya *Şüpheli* olarak kabul edilen yapıtlarda düzeltme eylemleri yapılır. Bazı durumlarda düzeltme eylemleri otomatik olarak gerçekleşir; diğer durumlarda düzeltme eylemleri el ile veya yalnızca güvenlik operasyonları ekibinizin onayıyla gerçekleştirilen işlemlerdir.

- [Otomasyon düzeyleri hakkında daha fazla bilgi edinin](/microsoft-365/security/defender-endpoint/automation-levels); ve ardından
- [Uç Nokta için Defender'da AIR özelliklerini yapılandırın](/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation).

> [!IMPORTANT]
> Otomatik araştırma ve düzeltme için *Tam otomasyon* kullanmanızı öneririz. Hatalı pozitif sonuç nedeniyle bu özellikleri kapatmayın. Bunun yerine, [özel durumları tanımlamak için "izin ver" göstergelerini](#indicators-for-microsoft-defender-for-endpoint) kullanın ve otomatik araştırma ve düzeltmeyi uygun eylemleri otomatik olarak gerçekleştirecek şekilde ayarlayın. [Bu kılavuzun](automation-levels.md#levels-of-automation) takip etmesi, güvenlik operasyonları ekibinizin işlemesi gereken uyarı sayısını azaltmaya yardımcı olur.

## <a name="still-need-help"></a>Yine de yardım mı gerekiyor?

Bu makaledeki tüm adımlarda çalıştıysanız ve hala yardıma ihtiyacınız varsa teknik desteğe başvurun.

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> gidin ve oturum açın.

2. Sağ üst köşede soru işaretini (**?**) ve ardından **Microsoft desteği'ni** seçin.

3. **Destek Yardımcısı** penceresinde sorununuzu açıklayın ve iletinizi gönderin. Buradan bir hizmet isteği açabilirsiniz.

> [!TIP]
> Diğer platformlar için Antivirüs ile ilgili bilgi arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md) 

## <a name="see-also"></a>Ayrıca bkz.

[Uç Nokta için Microsoft Defender yönetme](manage-mde-post-migration.md)

[Microsoft 365 Defender portalına genel bakış](/microsoft-365/security/defender-endpoint/use)
