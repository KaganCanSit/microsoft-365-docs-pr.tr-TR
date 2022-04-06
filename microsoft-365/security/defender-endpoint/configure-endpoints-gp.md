---
title: Mobil Windows cihazları Uç Nokta için Microsoft Defender için grup ilkesi
description: Grup ilkesi' i kullanarak yapılandırma paketini Windows için uygun cihazlara dağıtın.
keywords: Grup ilkesi, cihaz yönetimi, cihazları yapılandırma, cihazları Uç Nokta için Microsoft Defender, cihaz ekleme Uç Nokta için Microsoft Defender, grup ilkesi kullanarak cihazları yapılandırma
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
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.date: 12/07/2021
ms.technology: mde
ms.openlocfilehash: e05927829ec680a303972090dc050514c31cdbc6
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468975"
---
# <a name="onboard-windows-devices-using-group-policy"></a>Windows kullanarak diğer cihazları grup ilkesi 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

**Aşağıdakiler için geçerlidir:**

- Grup İlkesi
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsgp-abovefoldlink)

> [!NOTE]
> Paketin grup ilkesi GP) güncelleştirmelerini kullanmak için, Windows Server 2008 R2 veya sonraki bir işletim sistemi kullanıyor olun.
>
> Windows Server 2019 ve Windows Server 2022 için, kaynak tercihin oluşturduğu XML dosyasının NT AUTHORITY\SYSTEM ile NT AUTHORITY\Well-Known-System-Account yerine NT AUTHORITY\SYSTEM grup ilkesi değiştirmeniz gerekir.

> [!NOTE]
> Windows Server 2012 R2 ve 2016 için yeni, birleşik Uç Nokta için Microsoft Defender çözümünü kullanıyorsanız, doğru veri ilkesi seçeneklerine erişmek için lütfen merkezi mağazanıza en son ADMX dosyalarını Uç Nokta için Microsoft Defender emin olun. Lütfen [Windows Yönetim](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) Şablonları için Merkezi Mağaza grup ilkesi oluşturma ve yönetme hakkında bilgi edinebilirsiniz ve Windows 10 için en son **dosyaları indirebilirsiniz**.

Uç Nokta için [Defender'Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) çeşitli yolları görmek için PDF veya Dosya Ayarları'ne göz atabilirsiniz.[](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)

1. Hizmet ekleme sihirbazından indirdiğiniz GP yapılandırma paketi dosyasını (`WindowsDefenderATPOnboardingPackage.zip`) açın. Paketi şu portaldan da <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>:

    1. Gezinti bölmesinde, Gezinti **Bölmesi'Ayarlar** >  **EndpointsDevice** >  **managementOnboarding**  >  öğesini seçin.

    1. İşletim sistemini seçin.

    1. Dağıtım yöntemi **alanında** Grup **ilkesi'ne seçin**.

    1. Paketi **indir'e** tıklayın ve .zip kaydedin.

2. .zip dosyasının içeriğini cihaz tarafından erişilebilen, salt okunur bir konuma ayıklar. *optionalParamsPolicy* adlı bir klasörünüz ve *WindowsDefenderATPOnboardingScript.cmd dosyası olmalıdır*.

3. Yeni bir GPO oluşturmak için, [Grup ilkesi](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) Yönetim Konsolu'nu (GPMC) açın, yapılandırmak istediğiniz grup ilkesi Nesneleri  Ekle'ye sağ tıklayın ve Yeni'ye **tıklayın**. Görüntülenen iletişim kutusuna yeni GPO'nun adını girin ve Tamam'a **tıklayın**.

4. GPMC [grup ilkesi'nu açın](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11), yapılandırmak istediğiniz grup ilkesi Nesnesine (GPO) sağ tıklayın ve Düzenle'ye **tıklayın**.

5. Denetim **Masası grup ilkesi, Bilgisayar** yapılandırması'nı, **Tercihler'i** ve denetim masası **ayarları'nı seçin**.

6. Zamanlanmış **görevler'e sağ tıklayın**, **Yeni'nin** üzerine gelin ve Anlık Görev **(En az 7 Windows) tıklayın**.

7. Açılan **Görev** penceresinde Genel **sekmesine** gidin. Güvenlik **seçenekleri'nin** altında **Kullanıcı veya Grubu Değiştir'e** tıklayın, SİSS SISTEMI yazın ve Adları **Denetleme'ye ve Tamam'a** **tıklayın**. NT AUTHORITY\SYSTEM, görevin çalıştıracak olduğu kullanıcı hesabı olarak görünür.

8. Kullanıcının **oturum açmış olup olmadığını çalıştır'ı seçin ve** En yüksek **ayrıcalıklarla çalıştır onay** kutusunu işaretleyin.

9. Ad alanına, zamanlanmış görev için uygun bir ad yazın (örneğin, Uç Nokta Dağıtımı için Defender).

10. Eylemler sekmesine **gidin** ve Yeni **... öğesini seçin.** Eylem alanında **Program başlat'ın** seçili olduğundan **emin** olun. Paylaşılan *WindowsDefenderATPOnboardingScript.cmd* dosyasının dosya sunucusunun tam etki alanı adını (FQDN) kullanarak UNC yolunu girin.

11. **Tamam'ı** seçin ve tüm açık GPMC pencerelerini kapatın.

12. GPO'nun Kuruluş Birimine (OU) bağlantısını eklemek için sağ tıklayın ve Varolan **bir GPO'ya bağlantı ekle'yi seçin**. Görüntülenen iletişim kutusunda, grup ilkesi Nesne Seçin'i seçin. **Tamam**'a tıklayın.

> [!TIP]
> Cihazı işe seçtikten sonra, cihazın hizmete düzgün bir şekilde yer olduğunu doğrulamak için bir algılama testi çalıştırmayı seçebilirsiniz. Daha fazla bilgi için bkz [. Uç nokta cihazı için yeni eklenen bir Defender'da algılama testi çalıştırma](run-detection-test.md).

## <a name="additional-defender-for-endpoint-configuration-settings"></a>Uç nokta yapılandırma ayarları için Ek Defender

Her cihazda, derin çözümleme için bir dosya göndermek için bir istek göndererek, Microsoft 365 Defender örneklerin cihazdan toplanabilir olup olmadığını ifade edebilirsiniz.

Bu (GP) grup ilkesi, derin çözümleme özelliğinde kullanılan örnek paylaşım ayarları gibi ayarları yapılandırmak için kullanabilirsiniz.

### <a name="configure-sample-collection-settings"></a>Örnek koleksiyon ayarlarını yapılandırma

1. GP yönetim aygıtınızda, yapılandırma paketinden aşağıdaki dosyaları kopyalayın:

    - _AtpConfiguration.admx'i_ _C:\\Windows\\ PolicyDefinitions içine kopyalama_

    - _AtpConfiguration.adml_ dosyasını _C:\\Windows\\ PolicyDefinitionsen-US\\ içine kopyalama_

    Yönetim Şablonlarını Oluşturmak için [Merkezi grup ilkesi kullanıyorsanız](https://support.microsoft.com/help/3087759/how-to-create-and-manage-the-central-store-for-group-policy-administra), yapılandırma paketinden aşağıdaki dosyaları kopyalayın:

    - _AtpConfiguration.admx_ _\\\\\\\<forest.root\>dosyasını SysVolPoliciesPolicyDefinitions\\\<forest.root\>\\\\ içine kopyalama_

    - _AtpConfiguration.adml_ _\\\\\\\<forest.root\>dosyasını SysVolPoliciesPolicyDefinitionsen-US\\\\\<forest.root\>\\\\ içine kopyalama_

2. Yönetim [grup ilkesi açın, yapılandırmak](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) istediğiniz GPO'ya sağ tıklayın ve Düzenle'ye **tıklayın**.

3. Sistem Grup ilkesi **Düzenleyicisi'nde** Bilgisayar **yapılandırması'ne gidin**.

4. **İlkeler'e** ve **ardından Yönetim şablonları'ne tıklayın**.

5. Bileşenleri **Windows ve** **ATP'Windows Defender tıklayın**.

6. Cihazlarından örnek paylaşımı etkinleştirmeyi veya devre dışı bırakmayı seçin.

> [!NOTE]
> Değer ayarlay önce varsayılan değer örnek koleksiyonu etkinleştirmektir.

## <a name="other-recommended-configuration-settings"></a>Önerilen diğer yapılandırma ayarları

### <a name="update-endpoint-protection-configuration"></a>Uç nokta koruma yapılandırmasını güncelleştirme

Ekleme betiği yapılandır olduktan sonra, uç nokta koruma yapılandırmaları eklemek için aynı grup ilkesi düzenlemeye devam edin. Tüm gerekli güvenlik özelliklerine sahip olmak için Windows 10 veya Server 2019, Windows 11 veya Windows Server 2022 çalıştıran bir sistemden grup ilkesi düzenlemeleri Microsoft Defender Virüsten Koruma gerçekleştirin. Defender ATP yapılandırma ayarlarını kaydetmek için grup ilkesi nesnesini kapatıp yeniden açabilirsiniz.

Tüm ilkeler altında yer almaktadır `Computer Configuration\Policies\Administrative Templates`.

**İlke konumu:** \Windows Components\Windows Defender ATP

İlke|Ayar
---|---
Örnek koleksiyonunu etkinleştir\Devre Dışı Bırak|Etkin - "Makinelerde örnek koleksiyonu etkinleştir" işaretli

<br>

**İlke konumu:** \Windows Components\Microsoft Defender Virüsten Koruma

İlke|Ayar
---|---
İstenmeyen olabilecek uygulamaları algılamayı yapılandırma|Etkin, Engelle

<br>

**İlke konumu:** \Windows Bileşenler\Microsoft Defender Virüsten Koruma\HARITALAR

İlke|Ayar
---|---
Microsoft MAPS'a katılma|Etkin, Gelişmiş HARITALAR
Daha fazla çözümleme gerektiğinde dosya örnekleri gönderme | Etkin, Güvenli örnekler gönderme

<br>

**İlke konumu:** \Windows Components\Microsoft Defender Virüsten Koruma\Real-time Protection

İlke|Ayar
---|---
Gerçek zamanlı korumayı kapatma|Devre dışı
Davranış izlemeyi açma|Etkin
İndirilen tüm dosyaları ve ekleri tarama|Etkin
Bilgisayarınızda dosya ve program etkinliğini izleme|Etkin

<br>

**İlke konumu:** \Windows Components\Microsoft Defender Virüsten Koruma\Scan

Bu ayarlar, uç noktanın düzenli olarak tarar. Haftalık hızlı tarama ve performansa izin verilen bir performans gerçekleştirmenizi öneririz.

İlke|Ayar
---|---
Zamanlanmış bir tarama çalıştırmadan önce en son virüs ve casus yazılım güvenlik zekasını denetleme |Etkin

<br>

**İlke konumu:** \Windows Components\Microsoft Defender Virüsten Koruma\Microsoft Defender Exploit Guard\Attack Surface Azaltma

Saldırı yüzeyini azaltma kuralları GUID'lerinin geçerli listesini Saldırı yüzeyini azaltma kuralları dağıtımı [Adım 3: ASR kurallarını uygulama'dan edin.](attack-surface-reduction-rules-deployment-implement.md) Kural başına ek ayrıntılar için saldırı yüzeyini azaltma [kuralları başvurusu'ne bakın](attack-surface-reduction-rules-reference.md).

1. Saldırı Yüzeyini **Azaltmayı Yapılandır ilkeyi** açın.

1. **Etkin'i seçin**.

1. Göster **düğmesini** seçin.

1. Değer Adı alanına HER GUID **değerini** 2 değeriyle ekleyin.

   Bu, her biri yalnızca denetim için ayarlanır.

   :::image type="content" source="images/asr-guid.png" alt-text="Saldırı yüzeyini azaltma yapılandırması" lightbox="images/asr-guid.png":::

İlke|Konum|Ayar
---|---|---
Denetimli klasör erişimini yapılandırma| \Windows Components\Microsoft Defender Virüsten Koruma\Microsoft Defender Exploit Guard\Controlled Folder Access| Etkin, Denetim Modu

## <a name="run-a-detection-test-to-verify-onboarding"></a>Eklemeyi doğrulamak için bir algılama testi çalıştırma

Cihazı işe seçtikten sonra, bir cihazın hizmete düzgün bir şekilde yer olduğunu doğrulamak için bir algılama testi çalıştırmayı seçebilirsiniz. Daha fazla bilgi için bkz[. Yeni eklenen bir cihazda algılama Uç Nokta için Microsoft Defender çalıştırma](run-detection-test.md).

## <a name="offboard-devices-using-group-policy"></a>Grup ilkesi kullanan offboard grup ilkesi

Güvenlik nedeniyle, Offboard cihazları için kullanılan paketin süresi, indirildikten 30 gün sonra sona erer. Bir cihaza gönderilen süresi dolmuş offboard paketleri reddedilir. Bir çıkartan kullanım paketi indirirken paketlerin son kullanma tarihi size bildirilecek ve paket adına bu paket de dahil edilecektir.

> [!NOTE]
> Ekleme ve çıkarma ilkeleri aynı cihazda aynı anda dağıtıldığından, öngörülemeyen zararlara neden olur.

1. Aşağıdaki portaldan çıkar çıkar paketini <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender:</a>

    1. Gezinti bölmesinde, Ayarlar  > **EndpointsDevice** >  **managementOffboarding** >  öğesini seçin.

    1. İşletim sistemini seçin.
    
    1. Dağıtım yöntemi **alanında** Grup **ilkesi'ne seçin**.

    1. Paketi **indir'e** tıklayın ve .zip kaydedin.

2. .zip dosyasının içeriğini cihaz tarafından erişilebilen, salt okunur bir konuma ayıklar. *WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd adlı bir dosyanız olmalıdır*.

3. GPMC [grup ilkesi'nu açın](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11), yapılandırmak istediğiniz grup ilkesi Nesnesine (GPO) sağ tıklayın ve Düzenle'ye **tıklayın**.

4. Denetim **Masası grup ilkesi, Bilgisayar** yapılandırması'nı **, Tercihler'i** **ve denetim masası** **ayarları'nı seçin**.

5. Zamanlanmış **görevler'e sağ tıklayın**, **Yeni'nin üzerine gelin** ve Anlık **görev'e tıklayın**.

6. Açılan **Görev** penceresinde Genel **sekmesine** gidin. Güvenlik seçenekleri'nin altında yerel SYSTEM kullanıcı hesabını (BUILTIN\SYSTEM) **seçin**.

7. Kullanıcının **oturum açmış olup olmadığını çalıştır'ı seçin ve** En yüksek **ayrıcalıklarla çalıştır onay** kutusunu işaretleyin.

8. Ad alanına, zamanlanmış görev için uygun bir ad yazın (örneğin, Uç Nokta Dağıtımı için Defender).

9. Eylemler sekmesine **gidin** ve Yeni... **öğesini seçin**. Eylem alanında **Program başlat'ın** seçili olduğundan **emin** olun. Paylaşılan *WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd* dosyasının dosya sunucusunun tam etki alanı adını (FQDN) kullanarak UNC yolunu girin.

10. **Tamam'ı** seçin ve tüm açık GPMC pencerelerini kapatın.

> [!IMPORTANT]
> Offboard, cihazın algılayıcı verilerini portala göndermeyi durdurmaya neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere cihazdan alınan veriler 6 ay süreyle korunur.

## <a name="monitor-device-configuration"></a>Cihaz yapılandırmasını izleme

Diğer grup ilkesi, ilkelerin cihazlara dağıtımını izleme seçeneği yok. İzleme doğrudan portalda veya farklı dağıtım araçları kullanılarak yapılabilir.

## <a name="monitor-devices-using-the-portal"></a>Portalı kullanarak cihazları izleme

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender gidin</a>.
2. Cihazlar **envanteri'ne tıklayın**.
3. Cihazların görüntüde olduğunu doğrulayın.

> [!NOTE]
> Cihazların Cihazlar listesinde göstermeye başlaması birkaç gün **kadar zaman alıyor**. İlkelerin cihaza dağıtılması için gereken süre, kullanıcı oturum amadan önce geçen süre ve uç noktanın raporlamaya başlaması için geçen süre de buna dahildir.

## <a name="setup-defender-av-policies"></a>Setup Defender AV ilkeleri

Bu ayarları grup ilkesi ilkelerle birlikte yeni bir grup oluşturun veya grup oluşturun. Bu, müşteri ortamına ve farklı kuruluş birimlerini (OU) hedefleerek hizmeti nasıl sunmak istediğinize bağlıdır.

1. GP'yi seçtikten veya yeni bir GP oluşturdukta, GP'yi düzenleyin.

2. **Computer** **ConfigurationPoliciesAdministrative** >  >  **Templates** >  **Windows Components** >  **Microsoft Defender Virüsten Koruma Gerçek** >  **zamanlı Koruma'ya göz atabilirsiniz**.

    :::image type="content" source="images/realtime-protect.png" alt-text="Gerçek zamanlı koruma" lightbox="images/realtime-protect.png":::

1. Karantina klasöründe, öğeleri Karantina klasöründen kaldırmayı yapılandırabilirsiniz.

    :::image type="content" source="images/removal-items-quarantine1.png" alt-text="Öğeleri karantinaya almak için klasörü kaldırma" lightbox="images/removal-items-quarantine1.png":::

    :::image type="content" source="images/config-removal-items-quarantine2.png" alt-text="config-removal karantina" lightbox="images/config-removal-items-quarantine2.png":::

4. Tarama klasöründe, tarama ayarlarını yapılandırabilirsiniz.

    :::image type="content" source="images/gpo-scans.png" alt-text="gpo taramaları" lightbox="images/gpo-scans.png":::

### <a name="monitor-all-files-in-real-time-protection"></a>Gerçek zamanlı korumada tüm dosyaları izleme

Gerçek Zamanlı **Koruma için** \> **Bilgisayar** \> **Yapılandırma** \> **İlkeleri Windows Microsoft Defender Virüsten Koruma** \>  \> **Şablonları'ne gidin**.

:::image type="content" source="images/config-monitor-incoming-outgoing-file-act.png" alt-text="Gelen giden dosya etkinliği için izlemeyi yapılandırma" lightbox="images/config-monitor-incoming-outgoing-file-act.png":::

### <a name="configure-windows-defender-smartscreen-settings"></a>SmartScreen Windows Defender yapılandırma

1. SmartScreen **Gezgini'nde** \> **,** \> **Bilgisayar** \> **Yapılandırma Windows Yönetim** \> **Windows Defender'ne** \> **gidin**.

   :::image type="content" source="images/config-windows-def-smartscr-explorer.png" alt-text="Windows Defender akıllı ekran gezginini yapılandırma" lightbox="images/config-windows-def-smartscr-explorer.png":::
 
2. Bilgisayar **YapılandırmasıPoliciesAdministrative** >  >  Şablonlar **Windows** >  Bileşenler **Windows Defender** >  **SmartScreen Microsoft Edge** > .

    :::image type="content" source="images/config-windows-def-smartscr-explorer.png" alt-text="Windows Defender akıllı ekran Edge'i yapılandırma" lightbox="images/config-windows-def-smartscr-explorer.png":::

### <a name="configure-potentially-unwanted-applications"></a>İstenmeyen olabilecek uygulamaları yapılandırma

Bilgisayar Yapılandırma **İlkeleri** \> **Yönetim** \> **Şablonları ve Bileşenleri** **Windows'Microsoft Defender Virüsten Koruma** \> \>.

:::image type="content" source="images/config-potential-unwanted-apps.png" alt-text="Config potansiyel istenmeyen uygulama" lightbox="images/config-potential-unwanted-apps.png":::

:::image type="content" source="images/config-potential-unwanted-apps2.png" alt-text="yapılandırma potansiyel" lightbox="images/config-potential-unwanted-apps2.png":::

### <a name="configure-cloud-deliver-protection-and-send-samples-automatically"></a>Bulut Teslim Koruması'nı yapılandırma ve örnekleri otomatik olarak gönderme

**HARITALAR'da Bilgisayar Yapılandırma** \> **İlkeleri**  \> Yönetim \> **Windows'Microsoft Defender Virüsten Koruma** \>  \> **gidin**.

:::image type="content" source="images/gpo-maps1.png" alt-text="haritalar" lightbox="images/gpo-maps1.png":::

:::image type="content" source="images/gpo-maps-block-atfirst-sight.png" alt-text="İlk görüşte engelle" lightbox="images/gpo-maps-block-atfirst-sight.png":::

:::image type="content" source="images/gpo-maps-join-ms-maps.png" alt-text="Microsoft haritalara katılın" lightbox="images/gpo-maps-join-ms-maps.png":::

:::image type="content" source="images/send-file-sample-further-analysis-require.png" alt-text="Daha fazla çözümleme gerektiğinde dosya örneği gönder" lightbox="images/send-file-sample-further-analysis-require.png":::

> [!NOTE]
> Tüm **örnekleri gönder seçeneği** ikili dosyalar/betikler/belgeler için en iyi çözümlemeyi sağlar ve bu da güvenlik mezbenizi artırır.
Güvenli **örnekler gönder seçeneği** çözüm edülen ikili dosya/betik/belge türünü sınırlar ve güvenlik postürlerini azalttır. 

Daha fazla bilgi için bkz[.](enable-cloud-protection-microsoft-defender-antivirus.md) Microsoft Defender Virüsten Koruma'de bulut korumasını açma ve E-posta'da bulut [koruması ve Microsoft Defender Virüsten Koruma.](cloud-protection-microsoft-antivirus-sample-submission.md)

### <a name="check-for-signature-update"></a>İmza güncelleştirmesini denetleme

Güvenlik **Zekası Güncelleştirmeleri** \> **için** \> **Bileşenleri ve** \> **Windows İlkeleri** \> **yönetim Microsoft Defender Virüsten Koruma** \> **göz atabilirsiniz**.

:::image type="content" source="images/signature-update-1.png" alt-text="İmza güncelleştirmesi" lightbox="images/signature-update-1.png":::

:::image type="content" source="images/signature-update-2.png" alt-text="İmza tanımı güncelleştirmesi" lightbox="images/signature-update-2.png":::

### <a name="configure-cloud-deliver-timeout-and-protection-level"></a>Bulut zaman aşımı ve koruma düzeyini yapılandırma

Bilgisayar Yapılandırma **İlkeleri** \> **Yönetim** \> **Şablonları ve** \> **Bileşenleri Windows MpEngine** \> **Microsoft Defender Virüsten Koruma** \> **göz atabilirsiniz**.
Bulut koruma düzeyi ilkesi varsayılan kimlik engelleme Microsoft Defender Virüsten Koruma **ilkeyi** devre dışı bırakır. Koruma düzeyini varsayılan pencerelere ayarlamak için gereken de budur.

:::image type="content" source="images/config-extended-cloud-check.png" alt-text="config genişletilmiş bulut denetimi" lightbox="images/config-extended-cloud-check.png":::

:::image type="content" source="images/cloud-protection-level.png" alt-text="yapılandırma bulut koruma düzeyi" lightbox="images/cloud-protection-level.png":::

## <a name="related-topics"></a>İlgili konular
- [Microsoft Endpoint Configuration Manager kullanarak Windows cihazları Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [Mobil Windows araçlarını kullanarak diğer Cihaz Yönetimi cihaza ekleme](configure-endpoints-mdm.md)
- [Yerel Windows kullanarak cihazları ekleme](configure-endpoints-script.md)
- [Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarının katılımı](configure-endpoints-vdi.md)
- [Yeni eklenen cihazlarda algılama testi Uç Nokta için Microsoft Defender çalıştırma](run-detection-test.md)
- [Uç Nokta için Microsoft Defender ekleme sorunlarını giderme](troubleshoot-onboarding.md)
