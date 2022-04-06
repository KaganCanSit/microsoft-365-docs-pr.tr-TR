---
title: Uç Nokta için Microsoft Defender'da yanlış pozitifleri/negatifleri ele alın
description: Negatif sonuçlarda hatalı pozitif veya yanlış negatiflerin nasıl Uç Nokta için Microsoft Defender.
keywords: virüsten koruma, özel durum, dışlama, Uç Nokta için Microsoft Defender, hatalı pozitif, hatalı negatif, engellenen dosya, engellenen URL
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
- m365solution-scenario
- m365scenario-fpfn
ms.topic: how-to
ms.date: 12/02/2021
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs, yonghree, jcedola
ms.custom:
- FPFN
- admindeeplinkDEFENDER
ms.openlocfilehash: 160108e123f5ba38a7c7af8c36ebb17431e860ad
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472979"
---
# <a name="address-false-positivesnegatives-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'da yanlış pozitifleri/negatifleri ele alın

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Uç nokta koruma çözümsinde hatalı pozitif sonuç, varlık aslında bir tehdit olmadığını olsa da, algılanan ve kötü amaçlı olarak tanımlanan dosya veya işlem gibi bir varlıktır. Hatalı negatiflik, aslında kötü amaçlı olsa bile tehdit olarak algılanmadı bir varlıktır. Hatalı pozitif/negatif sonuçlar, güvenlik dahil herhangi bir tehdit çözümünde [Uç Nokta için Microsoft Defender](microsoft-defender-endpoint.md).

:::image type="content" source="images/false-positives-overview.png" alt-text="Doğru portalda hatalı pozitif ve negatif Uç Nokta için Microsoft Defender tanımı" lightbox="images/false-positives-overview.png":::

Neyse ki bu tür sorunları ele alan ve azaltan adımlar atabilirsiniz. Negatif değerlerde hatalı pozitif/negatif sonuçlar [görüyorsanız](/microsoft-365/security/defender/microsoft-365-defender) Microsoft 365 Defender işlemleriniz aşağıdaki işlemi kullanarak bu sorunu ele almaya yönelik adımlar atabilirsiniz:

1. [Uyarıları gözden geçirme ve sınıflandırma](#part-1-review-and-classify-alerts)
2. [Yapılan düzeltme eylemlerini gözden geçirme](#part-2-review-remediation-actions)
3. [Dışlamaları gözden geçirme ve tanımlama](#part-3-review-or-define-exclusions)
4. [Çözümleme için varlık gönderme](#part-4-submit-a-file-for-analysis)
5. [Tehdit koruması ayarlarınızı gözden geçirme ve ayarlama](#part-5-review-and-adjust-your-threat-protection-settings)

Bu makalede açıklanan görevleri gerçekleştirdikten sonra da hatalı pozitif/negatif sonuçlarla ilgili sorun yaşıyorsanız yardım bulabilirsiniz. Daha fazla [yardım mı gerekiyor?](#still-need-help)

:::image type="content" source="images/false-positives-step-diagram.png" alt-text="Hatalı pozitif ve negatif sonuçlarla ilgili adımlar" lightbox="images/false-positives-step-diagram.png":::

> [!NOTE]
> Bu makale, güvenlik işleçleri ve güvenlik yöneticileri için kılavuz olarak [Uç Nokta için Microsoft Defender.](microsoft-defender-endpoint.md)

## <a name="part-1-review-and-classify-alerts"></a>Bölüm 1: Uyarıları gözden geçirme ve sınıflandırma

Bir şeyin kötü [amaçlı veya](alerts.md) şüpheli olarak algılandığından tetiklenen bir uyarı görüyorsanız, bu varlıkla ilgili uyarının ılmasın. Ayrıca, hatalı pozitif sonuç olması gerekmeyen ancak raporlarda yer yer olmayan uyarıların ılması da engel olabilir. Uyarıları da sınıflandırmanizi öneririz.

Uyarılarınızı yönetme ve doğru/yanlış pozitifleri sınıflama, tehdit koruması çözümlerinizi eğitmenize yardımcı olur ve zaman içinde hatalı pozitif veya yanlış negatiflerin sayısını azaltır. Bu adımların atılması, güvenlik ekibinin daha yüksek öncelikli iş öğelerine odaklanması için güvenlik işlemleri panolarında gürültüyü azaltmaya da yardımcı olur.

### <a name="determine-whether-an-alert-is-accurate"></a>Uyarının doğru olup olmadığını belirleme

Uyarıyı sınıflandırmadan veya gizlemeden önce, uyarının doğru mu, yanlış pozitif mi yoksa doğru olup olmadığını belirleme.

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. Gezinti bölmesinde Uyarılar **sırası'ni seçin**.

3. Uyarı hakkında daha ayrıntılı bilgi için bir uyarı seçin. (Bkz[. Posta'da uyarıları Uç Nokta için Microsoft Defender](review-alerts.md).)

4. Uyarı durumuna bağlı olarak, aşağıdaki tabloda açıklanan adımları uygulayın:

   |Uyarı durumu|Ne yapmalı?|
   |---|---|
   |Uyarı doğru|Uyarıyı atayın ve daha [fazla araştıryın](investigate-alerts.md) .|
   |Uyarı hatalı bir pozitif|1. [Uyarıyı hatalı pozitif](#classify-an-alert) olarak sınıflandır.<br/><br/>2. [Uyarının bastırılması](#suppress-an-alert).<br/><br/>3. [Bu tablo için](#indicators-for-microsoft-defender-for-endpoint) bir Uç Nokta için Microsoft Defender.<br/><br/>4. [Çözümleme için bir dosyayı Microsoft'a gönderin](#part-4-submit-a-file-for-analysis).|
   |Uyarı doğru, ancak bu (önemsiz)|[Uyarıyı gerçek pozitif](#classify-an-alert) olarak sınıflandıracak ve sonra [da uyarının gizlemesi.](#suppress-an-alert)|

### <a name="classify-an-alert"></a>Uyarıyı sınıflandırma

Uyarılar, pozitif veya hatalı pozitif sonuç olarak Microsoft 365 Defender. Uyarıları sınıflendirmek, Uç Nokta için Microsoft Defender, zamanla daha çok doğru uyarı ve daha az yanlış uyarı görmelerini sağlar.

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. Uyarılar **sırası'ı** seçin ve sonra bir uyarı seçin.

3. Seçili uyarı için, Eylemleri Yönet **uyarıyı** \> **seçin**. Açılır bölme açılır.

4. Uyarıyı **yönet bölümünde** Doğru **uyarı'ya veya Yanlış uyarı'ya** **tıklayın**. (Hatalı **pozitif sonuç olarak** sınıflandırmak için Yanlış uyarıyı kullanın.)

> [!TIP]
> Uyarıların uyarılarını gizleme hakkında daha fazla bilgi için bkz[. Uç Nokta için Microsoft Defender yönetme](/microsoft-365/security/defender-endpoint/manage-alerts). Ayrıca, kuruluşta güvenlik bilgileri ve olay yönetimi (SIEM) sunucusu kullanıyorsa, orada da bir gizleme kuralı tanımlamaya bakın.

### <a name="suppress-an-alert"></a>Uyarıyı gizleme

Hatalı pozitif veya gerçek pozitif olan ancak rapor olmayan etkinlikler için uyarılarınız varsa, bu uyarıların doğru olmayan sonuçlarda Microsoft 365 Defender. Uyarıların gizlenmesi, güvenlik işlemleri pano seslerini azaltmaya yardımcı olur.

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. Gezinti bölmesinde Uyarılar **sırası'ni seçin**.

3. Ayrıntılar bölmesini açmak için, göstermesini istediğiniz **uyarıyı** seçin.

4. Ayrıntılar **bölmesinde** , üç noktayı (**...**) seçin ve ardından **Gösterme kuralı oluştur'a tıklayın**.

5. Gizleme kuralınız için tüm ayarları belirtin ve ardından Kaydet'i **seçin**.

> [!TIP]
> Gizleme kuralları için yardıma mı ihtiyacınız var? Bkz [. Uyarının ılması ve yeni bir gizleme kuralı oluşturma](/microsoft-365/security/defender-endpoint/manage-alerts#suppress-an-alert-and-create-a-new-suppression-rule).

## <a name="part-2-review-remediation-actions"></a>Bölüm 2: Düzeltme eylemlerini gözden geçirme

[Dosyayı karantinaya](manage-auto-investigation.md#remediation-actions) gönderme veya işlemi durdurma gibi düzeltme eylemleri, tehdit olarak algılanan varlıklara (dosyalar gibi) alınır. Çeşitli düzeltme eylemleri, otomatik araştırma ve düzeltme işlemleri aracılığıyla otomatik olarak Microsoft Defender Virüsten Koruma:

- Dosyayı karantinaya alın
- Kayıt defteri anahtarını kaldırma
- Süreci kill
- Hizmeti durdurma
- Sürücüyü devre dışı bırakma
- Zamanlanmış görevi kaldırma

Virüsten koruma taraması başlatma veya araştırma paketi toplama gibi diğer eylemler el ile veya Canlı Yanıt aracılığıyla [gerçekleşir](live-response.md). Canlı Yanıt aracılığıyla  alınan eylemler geri alınamaz.

Uyarılarınızı gözden geçirdikten sonra, bir sonraki adımınız düzeltme [eylemlerini gözden geçirmektir](manage-auto-investigation.md). Hatalı pozitif sonuçlar sonucunda herhangi bir eylem  edildiyse, birçok düzeltme eylemi türü geri alabilirsiniz. Özellikle şunları da s olabilir:

- [Karantinaya alınmış dosyayı İşlem Merkezi'nde geri yükleme](#restore-a-quarantined-file-from-the-action-center)
- [Bir defada birden çok eylemi geri alma](#undo-multiple-actions-at-one-time)
- [Dosyayı birden çok cihaz genelinde karantinadan kaldırın](#remove-a-file-from-quarantine-across-multiple-devices). ve
- [Dosyayı karantinadan geri yükleme](#restore-file-from-quarantine)

Hatalı pozitif sonuçlar sonucu elde edilen eylemleri gözden geçirmeyi ve geri almayı bitirseniz, gözden geçirme veya dışlamaları [tanımlamaya devam edin](#part-3-review-or-define-exclusions).

### <a name="review-completed-actions"></a>Tamamlanan eylemleri gözden geçirme

1. Gezinti bölmesinin sol Microsoft 365 Defender **Merkezi'ne tıklayın**.<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"></a>

2. Yapılan **eylemlerin** listesini görüntülemek için Geçmiş sekmesini seçin.

3. Yapılan düzeltme eylemi hakkında daha fazla ayrıntı görüntülemek için bir öğe seçin.

### <a name="restore-a-quarantined-file-from-the-action-center"></a>Karantinaya alınmış dosyayı İşlem Merkezi'nde geri yükleme

1. Görev portalının sol gezinti Microsoft 365 Defender, İşlem **merkezi'ne tıklayın**.

2. Geçmiş **sekmesinde** , geri almak istediğiniz eylemi seçin.

3. Uçarak çıkış bölmesinde Geri Al'ı **seçin**. Eylem bu yöntemle geri alınamazsa, Geri Al düğmesini **görmezsiniz** . (Daha fazla bilgi edinmek için bkz. [Tamamlanmış eylemleri geri alma](manage-auto-investigation.md#undo-completed-actions).)

### <a name="undo-multiple-actions-at-one-time"></a>Bir defada birden çok eylemi geri alma

1. Gezinti bölmesinin sol Microsoft 365 Defender **Merkezi'ne tıklayın**.<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"></a>

2. Geçmiş **sekmesinde** , geri almak istediğiniz eylemleri seçin.

3. Ekranın sağ tarafındaki bölmede Geri Al'ı **seçin**.

### <a name="remove-a-file-from-quarantine-across-multiple-devices"></a>Birden çok cihaz genelinde karantinadan dosya kaldırma

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/autoir-quarantine-file-1.png" alt-text="Dosyayı karantinaya alın" lightbox="images/autoir-quarantine-file-1.png":::

1. Gezinti bölmesinin sol Microsoft 365 Defender **Merkezi'ne tıklayın**.<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"></a>

2. Geçmiş **sekmesinde** , Eylem türü Dosyayı karantinaya alın olan **dosyayı seçin**.

3. Ekranın sağ tarafındaki bölmede, Bu dosyanın **daha fazla X** örneği için uygula'ya tıklayın ve sonra da Geri Al'ı **seçin**.

### <a name="restore-file-from-quarantine"></a>Dosyayı karantinadan geri yükleme

Bir incelemeden sonra temiz olduğunu belirlediysanız, dosyayı geri alın ve karantinadan kaldırabilirsiniz. Dosya karantinaya alınmış her cihazda aşağıdaki komutu çalıştırın.

1. Cihazda yükseltilmiş komut satırı istemini açın:

   1. **Başlat'a gidin** ve _cmd yazın_.
   2. Komut istemi'ne **sağ tıklayın ve** Yönetici olarak **çalıştır'ı seçin**.

2. Aşağıdaki komutu girin ve Enter tuşuna **basın**:

    ```console
    "%ProgramFiles%\Windows Defender\MpCmdRun.exe" -Restore -Name EUS:Win32/CustomEnterpriseBlock -All
    ```

    > [!IMPORTANT]
    > Bazı senaryolarda **ThreatName** olarak görünebilir `EUS:Win32/CustomEnterpriseBlock!cl`. Uç Nokta için Defender, son 30 gün içinde bu cihazda karantinaya alınmış olan tüm özel engellenen dosyaları geri yükleyebilir.
    >
    > Olası ağ tehditi olarak karantinaya alınmış bir dosya kurtarılamaz olabilir. Kullanıcı karantinadan sonra dosyayı geri yükleme girişiminde olursa, bu dosyaya erişilemez. Bunun nedeni sistemin artık dosyaya erişmek için ağ kimlik bilgilerine sahip olması olabilir. Normalde, bu durum sistem veya paylaşılan klasörde geçici olarak oturum açmanın sonucudur ve erişim belirteçlerinin süresi dolar.

3. Ekranın sağ tarafındaki bölmede, Bu dosyanın **daha fazla X** örneği için uygula'ya tıklayın ve sonra da Geri Al'ı **seçin**.

## <a name="part-3-review-or-define-exclusions"></a>Bölüm 3: Dışlamaları gözden geçirme veya tanımlama

Dışlama, düzeltme eylemlerine özel durum olarak belirttiğiniz dosya veya URL gibi bir varlıktır. Dışarıda bırakılan varlık yine de algılanır, ancak bu varlık üzerinde hiçbir düzeltme eylemi gerçekleştirlanmaz. Başka bir ifadeyle, algılanan dosya veya işlem durdurulamaz, karantinaya gönderilmez, kaldırılamaz veya başka bir Uç Nokta için Microsoft Defender.

Dışlamaları farklı Uç Nokta için Microsoft Defender için, aşağıdaki görevleri gerçekleştirin:

- [Dışlamaları özel Microsoft Defender Virüsten Koruma](#exclusions-for-microsoft-defender-antivirus)
- [Çalışma için "izin ver" göstergeleri Uç Nokta için Microsoft Defender](#indicators-for-microsoft-defender-for-endpoint)

> [!NOTE]
> Microsoft Defender Virüsten Koruma dışlamalar yalnızca virüsten koruma için geçerlidir; diğer Uç Nokta için Microsoft Defender geçerli değildir. Dosyaları genel olarak dışlamak için dışlamaları Microsoft Defender Virüsten Koruma [özel Uç Nokta için Microsoft Defender göstergeleri kullanın.](/microsoft-365/security/defender-endpoint/manage-indicators)

Bu bölümdeki yordamlarda dışlamaların ve göstergelerin nasıl tanımlanması açıklanmıştır.

### <a name="exclusions-for-microsoft-defender-antivirus"></a>Dışlamalar : Microsoft Defender Virüsten Koruma

Genelde, özel olarak dışlamaları tanımlamanız Microsoft Defender Virüsten Koruma. Dışlamaları ancak bir şekilde tanımladığınızdan ve yalnızca hatalı pozitif sonuç alan dosyaları, klasörleri, süreçleri ve süreç açılan dosyaları dahil etmeyi sağlarsınız. Ayrıca, tanımlı dışlamalarınızı düzenli olarak gözden geçirmeyi de sağlar. Virüsten koruma [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) dışlamalarınızı tanımlamak veya düzenlemek için grup ilkesi'i kullanmanızı öneririz; bununla birlikte, [grup ilkesi gibi başka](/azure/active-directory-domain-services/manage-group-policy) yöntemler [de kullanabilirsiniz](manage-mde-post-migration.md) (bkz. Uç Nokta için Microsoft Defender.

> [!TIP]
> Virüsten koruma dışlamaları için yardıma mı ihtiyacınız var? Bkz[. Taramalarda dışlamaları yapılandırma Microsoft Defender Virüsten Koruma doğrulama](configure-exclusions-microsoft-defender-antivirus.md).

#### <a name="use-microsoft-endpoint-manager-to-manage-antivirus-exclusions-for-existing-policies"></a>Virüsten Microsoft Endpoint Manager dışlamalarını yönetmek için dışlama kullanabilirsiniz (var olan ilkeler için)

1. Yönetim merkezine Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) ve oturum açma.

2. Uç **nokta güvenliği Virüsten** \> **Koruma'ya** ve sonra var olan bir ilkeye seçin. (Var olan bir ilkeniz yoksa veya yeni ilke oluşturmak için sonraki [yordama atlayabilirsiniz](#use-microsoft-endpoint-manager-to-create-a-new-antivirus-policy-with-exclusions)).

3. **Özellikler'i** seçin ve Yapılandırma **ayarları'nın yanında Düzenle'yi** **seçin**.

4. Özel **Microsoft Defender Virüsten Koruma'i genişletin** ve sonra dışlamalarınızı belirtin.

5. Gözden **Geçir + kaydet'i** ve sonra Kaydet'i **seçin**.

#### <a name="use-microsoft-endpoint-manager-to-create-a-new-antivirus-policy-with-exclusions"></a>Dışlamaların Microsoft Endpoint Manager yeni bir virüsten koruma ilkesi oluşturmak için dışlama kullanabilirsiniz

1. Yönetim merkezine Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) ve oturum açma.

2. Uç nokta **güvenliği Virüsten Koruma** \>  \> **+ İlke Oluştur'a seçin**.

3. Bir platform seçin (örneğin, **Windows 10 sonrası**, **macOS**, Windows 10 **ve Windows Server).**

4. Profil **için** dışlamaları **Microsoft Defender Virüsten Koruma sonra** Oluştur'a **tıklayın**.

5. Profil için bir ad ve açıklama belirtin, ardından Sonraki'yi **seçin**.

6. Yapılandırma ayarları **sekmesinde,** virüsten koruma dışlamalarınızı belirtin ve sonra da Sonraki'yi **seçin**.

7. Kapsam **etiketleri sekmesinde** , kuruluşta kapsam etiketleri kullanıyorsanız, oluşturmakta olduğu ilke için kapsam etiketleri belirtin. (Bkz [. Kapsam etiketleri](/mem/intune/fundamentals/scope-tags).)

8. Ödevler **sekmesinde** , ilkenizin uygulanması gereken kullanıcıları ve grupları belirtin ve ardından Sonraki'yi **seçin**. (Ödevlerle ilgili yardıma ihtiyacınız varsa bkz. [E-postada kullanıcı ve cihaz Microsoft Intune](/mem/intune/configuration/device-profile-assign).)

9. Gözden Geçir **+ oluştur sekmesinde** ayarları gözden geçirin ve ardından Oluştur'a **tıklayın**.

### <a name="indicators-for-microsoft-defender-for-endpoint"></a>Göstergeler: Uç Nokta için Microsoft Defender

[Göstergeler](/microsoft-365/security/defender-endpoint/manage-indicators) (özellikle güvenlik güvenliği göstergeleri veya PC'ler) güvenlik işlemleri ekibinizin varlıkları algılama, önleme ve dışlama işlemlerini tanımlamalarına olanak sağlar. Örneğin, bu dosyalarda taramalar ve düzeltme eylemlerinden atlanırsa belirli dosyaları Uç Nokta için Microsoft Defender. Belirli dosyalar, IP adresleri veya URL'ler için uyarılar oluşturmak için de göstergeler kullanılabilir.

Dışlamalar olarak varlıklar belirtmek Uç Nokta için Microsoft Defender, bu varlıklar için "izin ver" göstergeleri oluşturun. Bu tür "izin ver" Uç Nokta için Microsoft Defender düzeltme için yeni nesil [koruma, otomatik](microsoft-defender-antivirus-in-windows-10.md) [uç noktada algılama ve yanıtlama](overview-endpoint-detection-response.md) ve [otomatik & geçerlidir](/microsoft-365/security/defender-endpoint/automated-investigations).

"İzin Ver" göstergeleri şu için oluşturulabilir:

- [Dosyalar](#indicators-for-files)
- [IP adresleri, URL'ler ve etki alanları](#indicators-for-ip-addresses-urls-or-domains)
- [Uygulama sertifikaları](#indicators-for-application-certificates)

:::image type="content" source="images/false-positives-indicators.png" alt-text="Gösterge türleri" lightbox="images/false-positives-indicators.png":::

#### <a name="indicators-for-files"></a>Dosyalar için göstergeler

Bir dosya [için yürütülebilir dosya gibi bir "](/microsoft-365/security/defender-endpoint/indicator-file)izin ver" göstergesi oluşturmanız, kurumda kullanılan dosyaların engellenmiş durumda olmasına yardımcı olur. Dosyalar, dosya gibi taşınabilir yürütülebilir `.exe` (PE) dosyaları `.dll` içerebilir.

Dosyalar için göstergeler oluşturmadan önce, aşağıdaki gereksinimlerin karşı olduğundan emin olun:

- Microsoft Defender Virüsten Koruma bulut tabanlı koruma etkin olarak yapılandırılmıştır (bkz. [Bulut tabanlı korumayı yönetme](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus))
- Kötü amaçlı yazılımdan koruma istemci sürümü 4.18.1901.x veya sonraki sürümüdür.
- Cihazlar şu anda Windows 10, sürüm 1703 veya Windows 11; Windows Server 2016, Windows Server 2019 veya Windows Server 2022'de
- Engelle [veya izin ver özelliği açık](/microsoft-365/security/defender-endpoint/advanced-features)

#### <a name="indicators-for-ip-addresses-urls-or-domains"></a>IP adresleri, URL'ler veya etki alanları için göstergeler

Bir [IP adresi, URL](/microsoft-365/security/defender-endpoint/indicator-ip-domain) veya etki alanı için "izin ver" göstergesi güncelleştirmesi güncelleştirmesi, kurumda kullanılan sitelerin veya IP adreslerinin engellenmiş olarak engellenmiş olarak önlenmesine yardımcı olur.

IP adresleri, URL'ler veya etki alanları için göstergeler oluşturmadan önce, aşağıdaki gereksinimlerin karşı olduğundan emin olun:

- Uç nokta için Defender'da ağ koruması engelleme modunda etkindir (bkz [. Ağ korumasını etkinleştirme](/microsoft-365/security/defender-endpoint/enable-network-protection))
- Kötü amaçlı yazılımdan koruma istemci sürümü 4.18.1906.x veya sonrasıdır
- Cihazlar şu anda Windows 10, sürüm 1709 veya sonraki bir sürümde veya Windows 11

Çalışma alanı içinde özel ağ göstergeleri [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Daha fazla bilgi edinmek için bkz. [Gelişmiş özellikler](/microsoft-365/security/defender-endpoint/advanced-features).

#### <a name="indicators-for-application-certificates"></a>Uygulama sertifikaları için göstergeler

Uygulama sertifikası [için bir "izin ver"](/microsoft-365/security/defender-endpoint/indicator-certificates) göstergesi oluşturmanız, kurum içinde geliştirilen ve kurum içinde geliştirilen uygulamalar gibi uygulamaların engellenmiş durumdan yürütülmesini önlemeye yardımcı olur. `.CER` veya `.PEM` dosya uzantıları da desteklene.

Uygulama sertifikaları için göstergeler oluşturmadan önce, aşağıdaki gereksinimlerin karşı olduğundan emin olun:

- Microsoft Defender Virüsten Koruma bulut tabanlı koruma etkin olarak yapılandırılmıştır (bkz. [Bulut tabanlı korumayı yönetme](deploy-manage-report-microsoft-defender-antivirus.md)
- Kötü amaçlı yazılımdan koruma istemci sürümü 4.18.1901.x veya sonraki sürümüdür.
- Cihazlar şu anda Windows 10, sürüm 1703 veya Windows 11; Windows Server 2016, Windows Server 2019 veya Windows Server 2022'de
- Virüs ve tehdit koruma tanımları güncel

> [!TIP]
> Gösterge  oluşturdukta, bunları tek tek tanımlayabilir veya bir kerede birden çok öğe içeri aktarabilirsiniz. Tek bir kiracı için 15.000 gösterge sınırı olduğunu unutmayın. Ayrıca, önce dosya karma bilgileri gibi bazı ayrıntıları toplamanız da gerekir. Göstergeleri oluşturmadan önce önkoşulları [gözden geçirmeyi sağlar](manage-indicators.md).

## <a name="part-4-submit-a-file-for-analysis"></a>Bölüm 4: Çözümleme için dosya gönderme

Çözümleme için dosyalar ve dosyasız algılamalar gibi varlıkları Microsoft'a gönderebilirsiniz. Microsoft güvenlik araştırmacısı tüm gönderileri analiz eder ve sonuçları tehdit koruması Uç Nokta için Microsoft Defender yardımcı olur. Gönderme sitesinde oturum aken, gönderilerinizi izleyebilirsiniz.

### <a name="submit-a-file-for-analysis"></a>Çözümleme için dosya gönderme

Kötü amaçlı olarak yanlış algılanan veya kaçırılan bir dosyanız varsa, çözümleme için dosyayı göndermek için bu adımları izleyin.

1. Buradaki yönergeleri gözden geçirme: [Dosyaları çözümleme için gönderin](/windows/security/threat-protection/intelligence/submission-guide).

2. Site [Microsoft Güvenlik Zekası sitesini ziyaret](https://www.microsoft.com/wdsi/filesubmission) edin (https://www.microsoft.com/wdsi/filesubmission)ve dosyalarınızı gönderin).

### <a name="submit-a-fileless-detection-for-analysis"></a>Çözümleme için dosyasız algılama gönderme

Davranışa dayalı olarak bir şey kötü amaçlı yazılım olarak algılandısa ve dosyanız yoksa, çözümleme için dosyanızı `Mpsupport.cab` gönderebilirsiniz. *.cabWindows 10 veya Windows 11'da* Microsoft Malware Protection Command-Line Utility (MPCmdRun.exe) aracını kullanarak Windows 10 bu Windows 11.

1. 'a ` C:\ProgramData\Microsoft\Windows Defender\Platform\<version>`gidin ve yönetici `MpCmdRun.exe` olarak çalıştırın.

2. yazın `mpcmdrun.exe -GetFiles`ve Enter tuşuna **basın**.

   Çeşitli .cab günlükler içeren bir dosya oluşturulur. Dosyanın konumu, komut isteminin çıkışında belirtilir. Varsayılan olarak konum: `C:\ProgramData\Microsoft\Microsoft Defender\Support\MpSupportFiles.cab`.

3. Buradaki yönergeleri gözden geçirme: [Dosyaları çözümleme için gönderin](/windows/security/threat-protection/intelligence/submission-guide).

4. Microsoft Güvenlik Zekası [gönderme sitesini ziyaret](https://www.microsoft.com/wdsi/filesubmission) edin (https://www.microsoft.com/wdsi/filesubmission)ve .cab gönderin.

### <a name="what-happens-after-a-file-is-submitted"></a>Dosya gönderildikten sonra ne olur?

Gönderiniz, bir analist vakanızı işlemeye başlamadan önce bile size en son belirlemeyi vermek için sistemlerimiz tarafından hemen taranır. Bir dosya bir analist tarafından zaten gönderiliyor ve işleniyor olabilir. Böyle durumlarda, hızlı bir şekilde bir karar ve yapılır.

Henüz işlenmemiş olan gönderilerde, çözümleme için aşağıdaki gibi öncelikleri vardır:

- Çok sayıda bilgisayarın etkilenmesi olası yaygın dosyalara yüksek öncelik verilir.
- Kimliği doğrulanmış müşterilere, özellikle de geçerli Yazılım [Güvencesi Kimliklerine (SAID)](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx) sahip kurumsal müşterilere yüksek öncelik verilir.
- SAID sahipleri tarafından yüksek öncelikli olarak işaretlenen gönderilere anında dikkat verilir.

Gönderinize ilişkin güncelleştirmeleri kontrol etmek için, Gönderme Microsoft Güvenlik Zekası [oturum açma](https://www.microsoft.com/wdsi/filesubmission).

> [!TIP]
> Daha fazla bilgi edinmek için bkz [. Çözümleme için dosya gönderme](/windows/security/threat-protection/intelligence/submission-guide#how-does-microsoft-prioritize-submissions).

## <a name="part-5-review-and-adjust-your-threat-protection-settings"></a>Bölüm 5: Tehdit koruması ayarlarınızı gözden geçirme ve ayarlama

Uç Nokta için Microsoft Defender, çeşitli özelliklere ve özelliklere göre ayarların ince ayarını yapma olanağı da dahil olmak üzere çok çeşitli seçenekler sunar. Çok sayıda hatalı pozitif sonuç alıyorsanız, kuruluşa yönelik tehdit koruması ayarlarını gözden geçirmeyi kullanın. Bazı ayarlamalar yapmak için ihtiyacınız olabilir:

- [Bulut teslimi koruma](#cloud-delivered-protection)
- [İstenmeyen olabilecek uygulamalar için düzeltme](#remediation-for-potentially-unwanted-applications)
- [Otomatik araştırma ve düzeltme](#automated-investigation-and-remediation)

### <a name="cloud-delivered-protection"></a>Bulut teslimi koruma

Bulut teslimi koruma düzeyinizi kontrol edin ve Microsoft Defender Virüsten Koruma. Varsayılan olarak, bulut teslimi koruması Yapılandırılmadı olarak **ayarlanmıştır ve bu** çoğu kuruluş için normal bir koruma düzeyine karşılık gelen seçenektir. Bulut teslimi korumanız **Yüksek, Yüksek** **+** veya Sıfır olan bir değere **ayarlanmışsa, hatalı** pozitif sayısının yüksek olmasıyla karşınıza çıktı.

> [!TIP]
> Bulut teslimi korumanızı yapılandırma hakkında daha fazla bilgi edinmek için bkz [. Bulut teslimi koruma düzeyini belirtme](/windows/security/threat-protection/microsoft-defender-antivirus/specify-cloud-protection-level-microsoft-defender-antivirus).

Bulut [teslimi Microsoft Endpoint Manager](/mem/endpoint-manager-overview) ayarlarınızı düzenlemek veya ayarlamak için grup ilkesi'i kullanmanızı öneririz; bununla birlikte, [grup ilkesi (bkz](/azure/active-directory-domain-services/manage-group-policy). [Uç Nokta için Microsoft Defender.](manage-mde-post-migration.md)

#### <a name="use-microsoft-endpoint-manager-to-review-and-edit-cloud-delivered-protection-settings-for-existing-policies"></a>Bulut Microsoft Endpoint Manager koruma ayarlarını gözden geçirmek ve düzenlemek için E-posta Teslimi'ne (var olan ilkeler için)

1. Yönetim merkezine Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) ve oturum açma.

2. Uç **nokta güvenliği Virüsten** \> **Koruma'ya** ve sonra var olan bir ilkeye seçin. (Var olan bir ilkeniz yoksa veya yeni ilke oluşturmak için sonraki [yordama atlayabilirsiniz](#use-microsoft-endpoint-manager-to-set-cloud-delivered-protection-settings-for-a-new-policy)).

3. **Yönet'in** altında **Özellikler'i seçin**. Ardından, Yapılandırma **ayarları'nın yanında** Düzenle'yi **seçin**.

4. Bulut **koruması'nın** kapsamını genişletin ve Bulut teslimi koruma **düzeyi satırındaki mevcut ayarınızı gözden** geçirin. Bulut teslimi korumasını Yapılandırılmadı olarak ayarlamanızı **öneririz; bu**, güçlü bir koruma sağlarken hatalı pozitif sonuçlar alma riskini de azaltabilirsiniz.

5. Gözden **Geçir + kaydet'i** ve ardından **Kaydet'i seçin**.

#### <a name="use-microsoft-endpoint-manager-to-set-cloud-delivered-protection-settings-for-a-new-policy"></a>Bulut Microsoft Endpoint Manager koruma ayarlarını ayarlamak için E-posta teslimi ayarlarını kullanma (yeni ilke için)

1. Yönetim merkezine Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) ve oturum açma.

2. Uç nokta **güvenliği Virüsten Koruma** \>  \> **+ İlke oluştur'a seçin**.

3. Platform **için** bir seçenek belirleyin ve Profil için Virüsten Koruma veya Microsoft Defender Virüsten Koruma'ı **seçin (** belirli seçenek Platform için ne seçtiğinize **bağlıdır**.) Ardından **Oluştur'a seçin**.

4. Temel **Bilgiler sekmesinde** ilke için bir ad ve açıklama belirtin. Sonra, **Sonraki'yi seçin**.

5. Yapılandırma **ayarları sekmesinde** Bulut **koruması'nın kapsamını genişletin** ve aşağıdaki ayarları belirtin:

   - Bulut **teslimi korumasını aç'a** **Evet'i ayarlayın**.
   - Bulut **teslimi koruma düzeyini Yapılandırılmadı** **olarak ayarlayın**. (Bu düzey varsayılan olarak güçlü bir koruma düzeyi sağlar ve bu da hatalı pozitif sonuç alma riskini azalttı.)

6. Kapsam **etiketleri sekmesinde** , kuruluşta kapsam etiketleri kullanıyorsanız ilke için kapsam etiketleri belirtin. (Bkz [. Kapsam etiketleri](/mem/intune/fundamentals/scope-tags).)

7. Ödevler **sekmesinde** , ilkenizin uygulanması gereken kullanıcıları ve grupları belirtin ve ardından Sonraki'yi **seçin**. (Ödevlerle ilgili yardıma ihtiyacınız varsa bkz. [E-postada kullanıcı ve cihaz Microsoft Intune](/mem/intune/configuration/device-profile-assign).)

8. Gözden Geçir **+ oluştur sekmesinde** ayarları gözden geçirin ve ardından Oluştur'a **tıklayın**.

### <a name="remediation-for-potentially-unwanted-applications"></a>İstenmeyen olabilecek uygulamalar için düzeltme

İstenmeyen olabilecek uygulamalar (PUA), cihazların yavaş çalışmasına, beklenmeyen reklamlar görüntülemesine veya beklenmedik ya da istenmeyen başka yazılımlar yüklemesine neden olabilecek bir yazılım kategorisidir. PUA'ya örnek olarak, güvenlik ürünleriyle farklı davranan reklam yazılımı, iş amaçlı yazılım ve koruma yazılımı bulunmaktadır. PUA kötü amaçlı yazılım olarak kabul alınmasa da, bazı yazılım türleri davranışlarına ve itibarına bağlı olarak PUA'dır.

> [!TIP]
> PUA hakkında daha fazla bilgi edinmek için bkz [. İstenmeyen olabilecek uygulamaları algılama ve engelleme](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).

PuA koruma ayarlarınız, kurumda kullanılan uygulamalara bağlı olarak hatalı pozitif sonuçlar alıyor olabilir. Gerekirse, bir süre denetim modunda PUA korumasını çalıştırmayı göz önünde bulundurabilirsiniz veya puA korumasını, kurum daki cihazların bir alt kümesine uygulayabilirsiniz. PUA koruması, Microsoft Edge için ve Microsoft Defender Virüsten Koruma.

PUA koruma [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) düzenlemek veya ayarlamak için GRUP ILKESI'i öneririz; bununla birlikte, [grup ilkesi gibi başka](/azure/active-directory-domain-services/manage-group-policy) [yöntemler de kullanabilirsiniz](manage-mde-post-migration.md) (bkz. UÇ NOKTA IÇIN MICROSOFT DEFENDER.

#### <a name="use-microsoft-endpoint-manager-to-edit-pua-protection-for-existing-configuration-profiles"></a>PUA Microsoft Endpoint Manager (mevcut yapılandırma profilleri için) düzenlemeyi kullanma

1. Yönetim merkezine Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) ve oturum açma.

2. Cihaz **Yapılandırması** \> **profilleri'ne ve** sonra var olan bir ilkeyi seçin. (Var olan bir ilkeniz yoksa veya yeni ilke oluşturmak için sonraki [yordama atlayabilirsiniz](#use-microsoft-endpoint-manager-to-set-pua-protection-for-a-new-configuration-profile).)

3. **Yönet'in** altında **Özellikler'i** seçin ve sonra Yapılandırma **ayarları'nın yanındaki Düzenle'yi** **seçin**.

4. Yapılandırma ayarları **sekmesinde,** sayfayı aşağı kaydırın **ve Microsoft Defender Virüsten Koruma.**

5. **Denetlenen olası uygulamaları algıla'ya** **ayarlayın**. (Denetimi kapatabilirsiniz, ancak denetim modunu kullanarak algılamaları görebilirsiniz.)

6. Gözden **Geçir + kaydet'i** ve sonra Kaydet'i **seçin**.

#### <a name="use-microsoft-endpoint-manager-to-set-pua-protection-for-a-new-configuration-profile"></a>PUA Microsoft Endpoint Manager ayarlamak için yeni yapılandırma profili kullanma

1. Yönetim merkezine Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) ve oturum açma.

2. Cihazlar **Yapılandırma** \> **profilleri + Profil** \> **oluştur'a tıklayın**.

3. Platform için **Tercihler** ve **Windows 10 ve Profil** için **Cihaz** **kısıtlamaları'na tıklayın**.

4. Temel **Bilgiler sekmesinde** ilkeniz için bir ad ve açıklama belirtin. Sonra, **Sonraki'yi seçin**.

5. Yapılandırma ayarları **sekmesinde,** sayfayı aşağı kaydırın **ve Microsoft Defender Virüsten Koruma.**

6. **Denetlenecek olası uygulamaları algıla'ya** **ve** ardından Sonraki'yi **seçin**. (PUA korumasını kapatabilirsiniz, ancak denetim modunu kullanarak algılamaları görebilirsiniz.)

7. Ödevler **sekmesinde** , ilkenizin uygulanması gereken kullanıcıları ve grupları belirtin ve ardından Sonraki'yi **seçin**. (Ödevlerle ilgili yardıma ihtiyacınız varsa bkz. [E-postada kullanıcı ve cihaz Microsoft Intune](/mem/intune/configuration/device-profile-assign).)

8. Uygulanabilirlik **Kuralları sekmesinde** , ilkeye dahil etmek veya ilke dışında tutmak için işletim sistemi sürümlerini veya sürümlerini belirtin. Örneğin, ilkeyi belirli sürümlerin tüm cihazlarına uygulanacak şekilde Windows 10. Sonra, **Sonraki'yi seçin**.

9. Gözden Geçir **+ oluştur sekmesinde** , ayarlarınızı gözden geçirin ve ardından Oluştur'a **tıklayın**.

### <a name="automated-investigation-and-remediation"></a>Otomatik araştırma ve düzeltme

[Otomatik araştırma ve düzeltme](automated-investigations.md) (AIR) özellikleri, uyarıları inceleyen ve ihlalleri çözmek için acil bir işlem yapmak üzere tasarlanmıştır. Uyarılar tetiklendiğinde ve otomatik bir soruşturma çalıştırıldığı için araştırılan her kanıt parçası için bir karar oluşturulur. Kararlara Kötü *Amaçlı*, Şüpheli *veya* Tehdit *bulunamadı denmektedir*.

Kuruluş için otomasyon [kümesi düzeyine](/microsoft-365/security/defender-endpoint/automation-levels) ve diğer güvenlik ayarlarına bağlı olarak, kötü amaçlı veya Şüpheli olarak kabul edilen yapıtlarda *düzeltme eylemleri* *edilir*. Bazı durumlarda, düzeltme eylemleri otomatik olarak gerçekleşir; başka durumlarda düzeltme eylemleri el ile veya yalnızca güvenlik işlemleri ekibinin onayıyla yapılır.

- [Otomasyon düzeyleri hakkında daha fazla bilgi edinmek için](/microsoft-365/security/defender-endpoint/automation-levels); ve ardından
- [Uç Nokta için Defender'daki AIR özelliklerini yapılandır.](/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation)

> [!IMPORTANT]
> Otomatik araştırma *ve düzeltme için* Tam otomasyon'ı kullanmanizi öneririz. Hatalı pozitif sonuçlardan dolayı bu özellikleri kapatamazsiniz. Bunun yerine, [özel durumları tanımlamak için "](#indicators-for-microsoft-defender-for-endpoint)izin ver" göstergelerini kullanın ve uygun eylemleri otomatik olarak yapmak üzere otomatik soruşturmayı ve düzeltmeyi ayarlayın. Bu [kılavuzun takip](automation-levels.md#levels-of-automation) olması, güvenlik işlemleri ekibinin işlemesi gereken uyarı sayısını azaltmaya yardımcı olur.

## <a name="still-need-help"></a>Yine de yardım mı gerekiyor?

Bu makaledeki tüm adımların üzerinde çalıştınız ve hala yardıma ihtiyacınız varsa, teknik desteğe başvurun.

1. Oturum açma <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> gidin.

2. Sağ üst köşede soru işaretini (?) seçin ve **ardından** **Microsoft desteği'ne tıklayın**.

3. Destek **Yardımcısı penceresinde** sorunuz hakkında açıklama yazın ve iletinizi gönderin. Buradan bir hizmet isteği açabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

[Uç Nokta için Microsoft Defender](manage-mde-post-migration.md)

[Portala Microsoft 365 Defender genel bakış](/microsoft-365/security/defender-endpoint/use)
