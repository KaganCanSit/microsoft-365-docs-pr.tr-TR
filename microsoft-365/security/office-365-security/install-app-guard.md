---
title: Yöneticiler için Office için Application Guard
keywords: application guard, koruma, yalıtım, yalıtılmış kapsayıcı, donanım yalıtımı
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
description: Donanım tabanlı yalıtımda en son bilgileri edinin. Açıklardan yararlanmalar veya kötü amaçlı bağlantılar gibi mevcut ve yeni ortaya çıkan saldırıların çalışanların üretkenliğini ve kurumsal güvenliğini kesintiye uğratmasını önleyin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9a7e820a4aedb4338111ef0fc76a35de480ea1f8
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530936"
---
# <a name="application-guard-for-office-for-admins"></a>Yöneticiler için Office için Application Guard

**Şunlar için geçerlidir:** Word, Excel ve Microsoft 365 için PowerPoint Uygulamaları, Windows 10 Enterprise Windows 11 Enterprise

Office için Microsoft Defender Application Guard (Office için Application Guard), güvenilmeyen dosyaların güvenilir kaynaklara erişmesini önlemeye yardımcı olur ve kuruluşunuzun yeni ve yeni saldırılara karşı güvende kalmasını sağlar. Bu makalede, Office için Application Guard önizlemesi için cihazları ayarlama işleminde yöneticilere yol gösterilir. Bir cihazda Office için Application Guard'ı etkinleştirmek için sistem gereksinimleri ve yükleme adımları hakkında bilgi sağlar.

## <a name="prerequisites"></a>Önkoşullar

### <a name="minimum-hardware-requirements"></a>En düşük donanım gereksinimleri

* **CPU**: 64 bit, 4 çekirdek (fiziksel veya sanal), sanallaştırma uzantıları (Intel VT-x VEYA AMD-V), Çekirdek i5 eşdeğeri veya üzeri önerilir
* **Fiziksel bellek**: 8 GB RAM
* **Sabit disk**: Sistem sürücüsünde 10 GB boş alan (SSD önerilir)

### <a name="minimum-software-requirements"></a>En düşük yazılım gereksinimleri

* **Windows**: Windows 10 Enterprise sürümü, İstemci Derlemesi sürüm 2004 (20H1) derlemesi 19041 veya üzeri. Windows 11 tüm sürümleri desteklenir.
* **Office**: 16.0.13530.10000 veya sonraki derlemelerle Microsoft 365 Uygulamaları. Geçerli Kanal ve Aylık Kurumsal Kanal yüklemeleri için bu, sürüm 2011'e eşittir. Semi-Annual Enterprise Channel ve Semi-Annual Enterprise Channel (Önizleme) için en düşük sürüm 2108 veya üzeridir. Hem 32 bit hem de 64 bit sürümler desteklenir.
* **Güncelleştirme paketi**: Windows 10 toplu aylık güvenlik güncelleştirmesi [KB4571756](https://support.microsoft.com/help/4571756/windows-10-update-KB4571756)

Ayrıntılı sistem gereksinimleri için bkz. [Microsoft Defender Application Guard için sistem gereksinimleri](/windows/security/threat-protection/microsoft-defender-application-guard/reqs-md-app-guard). Ayrıca, lütfen bilgisayar üreticinizin sanallaştırma teknolojisini etkinleştirme kılavuzlarına bakın.
Microsoft 365 Uygulamaları güncelleştirme kanalları hakkında daha fazla bilgi edinmek için bkz. [Microsoft 365 Uygulamaları için güncelleştirme kanallarına genel bakış](/deployoffice/overview-update-channels).

### <a name="licensing-requirements"></a>Lisans gereksinimleri

* Microsoft 365 E5 Güvenlik
* Fakülteler için Microsoft 365 A5
* Öğrenciler için Microsoft 365 A5

> [!NOTE]
> Paylaşılan bilgisayar etkinleştirme veya cihaz tabanlı lisanslama ile Kurumlar için Microsoft 365 Uygulamaları Office için Application Guard'a erişimi yoktur.
>
> Güvenli Belgeler lisans planları, Office için Application Guard'a erişim sağlar. Daha fazla bilgi için bkz. [Microsoft 365 E5/A5'te Güvenli Belgeler](/microsoft-365/security/office-365-security/safe-docs).

## <a name="deploy-application-guard-for-office"></a>Office için Application Guard'ı dağıtma

### <a name="enable-application-guard-for-office"></a>Office için Application Guard'ı etkinleştirme

1. **Kb4571756 toplu aylık güvenlik güncelleştirmelerini Windows 10** indirip yükleyin.

2. Windows Özellikleri'nin altında **Microsoft Defender Application Guard'ı** ve **ardından Tamam'ı** seçin. Application Guard özelliğinin etkinleştirilmesi sistemin yeniden başlatılmasını ister. Şimdi veya 3. adımdan sonra yeniden başlatmayı seçebilirsiniz.

   :::image type="content" source="../../media/ag03-deploy.png" alt-text="AG'yi gösteren Windows Özellikleri iletişim kutusu" lightbox="../../media/ag03-deploy.png":::

   Bu özellik, yönetici olarak aşağıdaki PowerShell komutu çalıştırılarak da etkinleştirilebilir:

   ```powershell
   Enable-WindowsOptionalFeature -online -FeatureName Windows-Defender-ApplicationGuard
   ```

3. **Bilgisayar Yapılandırması\\Yönetim Şablonları\\Windows Bileşenleri\\ Microsoft Defender Application Guard'nde** bir grup ilkesi olan **Yönetilen Modda** Microsoft Defender Application Guard arayın. Seçenekler'in altındaki değeri **2** veya **3** olarak ayarlayıp Tamam veya **Uygula'yı** seçerek bu ilkeyi  açın.

   :::image type="content" source="../../media/ag04-deploy.png" alt-text="Ag'yi Yönetilen Modda açma seçeneği" lightbox="../../media/ag04-deploy.png":::

   Bunun yerine, karşılık gelen CSP ilkesini ayarlayabilirsiniz:

   > OMA-URI: **./Device/Vendor/MSFT/WindowsDefenderApplicationGuard/Settings/AllowWindowsDefenderApplicationGuard** <br> Veri türü: **Tamsayı** <br> Değer: **2**

4. Sistemi yeniden başlatın.

### <a name="set-diagnostics--feedback-to-send-full-data"></a>Tam veri göndermek için Tanılama & geri bildirimini ayarlama

> [!NOTE]
> Ancak bu gerekli değildir, ancak isteğe bağlı tanılama verilerini yapılandırmak bildirilen sorunları tanılamaya yardımcı olur.

Bu adım, sorunları tanımlamak ve düzeltmek için gereken verilerin Microsoft'a ulaşmasını sağlar. Windows cihazınızda tanılamayı etkinleştirmek için şu adımları izleyin:

1. Başlat menüsünden **Ayarlar'ı** açın.

   :::image type="content" source="../../media/ag05-diagnostic.png" alt-text="Başlat menüsü" lightbox="../../media/ag05-diagnostic.png":::

2. **Windows Ayarları'nda** **Gizlilik'i** seçin.

   :::image type="content" source="../../media/ag06-diagnostic.png" alt-text="Windows Ayarları menüsü" lightbox="../../media/ag06-diagnostic.png":::

3. Gizlilik bölümünde **Tanılama & geri bildirim'i** ve **ardından İsteğe bağlı tanılama verileri'ne** tıklayın.

   :::image type="content" source="../../media/ag07a-diagnostic.png" alt-text="Tanılama ve geri bildirim menüsü" lightbox="../../media/ag07a-diagnostic.png":::

Windows tanılama ayarlarını yapılandırma hakkında daha fazla bilgi için bkz. [Kuruluşunuzda Windows tanılama verilerini yapılandırma](/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enterprise-management).

### <a name="confirm-that-application-guard-for-office-is-enabled-and-working"></a>Office için Application Guard'ın etkinleştirildiğini ve çalıştığını onaylayın

Office için Application Guard'ın etkinleştirildiğini onaylamadan önce, ilkelerin dağıtıldığı bir cihazda Word, Excel veya PowerPoint'i başlatın. Office'in etkinleştirildiğinden emin olun. Önce Office ürününü etkinleştirmek için iş kimliğinizi kullanmanız gerekebilir.

Office için Application Guard'ın etkin olduğunu onaylamak için Word, Excel veya PowerPoint'i başlatın ve güvenilmeyen bir belge açın. Örneğin, İnternet'ten indirilen bir belgeyi veya kuruluşunuzun dışındaki bir kişiden gelen bir e-posta ekini açabilirsiniz.

Güvenilmeyen bir dosyayı ilk kez açtığınızda, aşağıdaki örneğe benzer bir Office giriş ekranı görebilirsiniz. Office için Application Guard etkinleştirilirken ve dosya açılırken bir süre görüntülenebilir. Güvenilmeyen dosyaların sonraki açılışları daha hızlı olmalıdır.

:::image type="content" source="../../media/ag08-confirm.png" alt-text="Office uygulaması giriş sayfası" lightbox="../../media/ag08-confirm.png":::

Dosya açıldıktan sonra, dosyanın Office için Application Guard'da açıldığını gösteren birkaç görsel gösterge göstermelidir:

* Şeritteki açıklama balonu

  :::image type="content" source="../../media/ag09-confirm.png" alt-text="Küçük App Guard notunu gösteren Belge dosyası" lightbox="../../media/ag09-confirm.png":::

* Görev çubuğunda kalkan bulunan uygulama simgesi

  ![Görev çubuğundaki simge.](../../media/ag12-limitations.png)

## <a name="configure-application-guard-for-office"></a>Office için Application Guard'ı yapılandırma

Office, Office için Application Guard'ın özelliklerini yapılandırmanıza olanak tanımak için aşağıdaki ilkeleri destekler. Bu ilkeler Grup ilkeleri veya [Office bulut ilkesi hizmeti](/DeployOffice/overview-office-cloud-policy-service) aracılığıyla yapılandırılabilir.

> [!NOTE]
> Bu ilkelerin yapılandırılması, Office için Application Guard'da açılan dosyalar için bazı işlevleri devre dışı bırakabilir.

|Ilkesi|Açıklama|
|---|---|
|Office için Application Guard kullanma|Bu ilkeyi etkinleştirmek Word, Excel ve PowerPoint'i Office için Application Guard yerine Korumalı Görünüm yalıtım kapsayıcısını kullanmaya zorlar. Bu ilke, Office için Application Guard'ı Microsoft Edge için etkin bırakırken sorunlar olduğunda geçici olarak devre dışı bırakmak için kullanılabilir.|
|Office kapsayıcısı oluşturma öncesi için Application Guard'ı yapılandırma|Bu ilke, güvenilmeyen dosyaları yalıtmaya yönelik Office için Application Guard kapsayıcısının geliştirilmiş çalışma zamanı performansı için önceden oluşturulup oluşturulmadığını belirler. Bu ayarı etkinleştirirseniz, kapsayıcıyı önceden oluşturmaya devam etmek için gün sayısını belirtebilir veya Office'in yerleşik buluşsal buluşsal öğesinin kapsayıcıyı önceden oluşturmasına izin vekleyebilirsiniz.
|Office için Application Guard'da açılan Office belgeleri için kopyalama/yapıştırmaya izin verme|Bu ilkenin etkinleştirilmesi, kullanıcının Office için Application Guard'da açılan bir belgedeki içeriği, dışında açılmış bir belgeye kopyalamasını ve yapıştırmasını engeller.|
|Office için Application Guard'da donanım hızlandırmayı devre dışı bırakma|Bu ilke, Office için Application Guard'ın grafikleri işlemek için donanım hızlandırma kullanıp kullanmadığını denetler. Bu ayarı etkinleştirirseniz, Office için Application Guard yazılım tabanlı (CPU) işleme kullanır ve herhangi bir üçüncü taraf grafik sürücüsü yüklemez veya bağlı grafik donanımıyla etkileşim kurmaz.
|Office için Application Guard'da desteklenmeyen dosya türleri korumasını devre dışı bırakma|Bu ilke, Office için Application Guard'ın desteklenmeyen dosya türlerinin açılmasını engelleyip engellemeyeceğini veya Korumalı Görünüm'e yeniden yönlendirmeyi etkinleştirip etkinleştirmeyeceğini denetler.
|Office için Application Guard'da açılan belgeler için kamera ve mikrofon erişimini kapatma|Bu ilke etkinleştirildiğinde, Office için Application Guard'ın içindeki kamera ve mikrofona Office erişimi kaldırılır.|
|Office için Application Guard'da açılan belgelerden yazdırmayı kısıtlama|Bu ilkenin etkinleştirilmesi, kullanıcının Office için Application Guard'da açılan bir dosyadan yazdırabileceği yazıcıları sınırlandırır. Örneğin, bu ilkeyi kullanarak kullanıcıları yalnızca PDF'ye yazdıracak şekilde kısıtlayabilirsiniz.|
|Kullanıcıların dosyalarda Office için Application Guard korumasını kaldırmasını engelleme|Bu ilkenin etkinleştirilmesi, Office koruması için Application Guard'ı devre dışı bırakma veya Office için Application Guard dışında bir dosya açma seçeneğini (Office uygulama deneyimi içinde) kaldırır. <p> **Not:** Kullanıcılar, dosyadan web işareti özelliğini el ile kaldırarak veya belgeyi Güvenilen konuma taşıyarak bu ilkeyi yine atlayabilir.|

> [!NOTE]
> Aşağıdaki ilkeler, kullanıcının etkin olması için oturumu kapatmasını ve Windows'ta yeniden oturum açmasını gerektirir:
>
> * Office için Application Guard'da açılan belgeler için kopyalama/yapıştırmayı devre dışı bırakma
> * Office için Application Guard'da açılan belgeler için yazdırmayı kısıtlama
> * Office için Application Guard'da açılan belgelere kamera ve mikrofon erişimini kapatma

## <a name="submit-feedback"></a>Geri bildirim gönderme

### <a name="submit-feedback-via-feedback-hub"></a>Geri Bildirim Merkezi aracılığıyla geri bildirim gönderme

Office için Application Guard'ı başlatırken herhangi bir sorunla karşılaşırsanız geri bildiriminizi Geri Bildirim Merkezi aracılığıyla göndermeniz teşvik edilir:

1. **Geri Bildirim Merkezi uygulamasını** açın ve oturum açın.

2. Application Guard'ı başlatırken bir hata iletişim kutusu alırsanız, yeni bir geri bildirim gönderimi başlatmak için hata iletişim kutusunda **Microsoft'a Bildir'i** seçin. Aksi takdirde, Application Guard için doğru kategoriyi seçmek için adresine gidin <https://aka.ms/mdagoffice-fb> ve sağ üst kısımdaki **Yeni geri bildirim ekle'yi seçin+&nbsp;**.

3. Sizin için henüz doldurulmadıysa **Geri bildiriminizi özetleyin** kutusuna bir özet girin.

4. Karşılaştığınız sorunun ayrıntılı açıklamasını ve **daha ayrıntılı olarak açıkla** kutusuna hangi adımları uyguladığınızı girin ve **İleri'yi** seçin.

5. **Sorun'un** yanındaki baloncuğu seçin. Seçilen kategorinin **Güvenlik ve Gizlilik \> Microsoft Defender Application Guard – Office** olduğundan emin olun ve **İleri'yi** seçin.

6. **Yeni geri bildirim'i** ve ardından **İleri'yi** seçin.

7. Sorunla ilgili izlemeleri toplayın:

   1. **Sorunumu yeniden oluştur** kutucuğunu genişletin.

   2. Karşılaştığınız sorun Application Guard çalışırken oluşuyorsa bir Application Guard örneği açın. Bir örneği açmak, Application Guard kapsayıcısından ek izlemelerin toplanmasına olanak tanır.

   3. **Kaydı başlat'ı** seçin ve kutucuğun dönmesini bekleyin ve *Kaydı durdur* deyin.

   4. Application Guard ile sorunu tam olarak yeniden oluşturun. Çoğaltma bir Application Guard örneğini başlatmayı denemeyi ve başarısız olana kadar beklemeyi veya çalışan bir Application Guard örneğinde bir sorunu yeniden oluşturmayı içerebilir.

   5. **Kaydı durdur** kutucuğunu seçin.

   6. Kapsayıcı tanılamalarının da toplanabilmesi için, gönderimden sonra birkaç dakika boyunca bile çalışan Application Guard örneklerini açık tutun.

8. Sorunla ilgili tüm ilgili ekran görüntülerini veya dosyaları ekleyin.

9. **Gönder'i** seçin.

### <a name="submit-feedback-via-office-customer-voice"></a>Office Customer Voice aracılığıyla geri bildirim gönderme

Sorun, Office belgeleri Application Guard'da açıldığında ortaya çıkarsa, Office'in içinden de geri bildirim gönderebilirsiniz. Geri bildirim göndermek için [Office Insider El Kitabı'na](https://insider.office.com/handbook) bakın.

## <a name="integration-with-microsoft-defender-for-endpoint-and-microsoft-defender-for-office-365"></a>Uç Nokta için Microsoft Defender ve Office 365 için Microsoft Defender ile tümleştirme

Office için Application Guard, yalıtılmış ortamda gerçekleşen kötü amaçlı etkinliklerde izleme ve uyarı sağlamak için Uç Nokta için Microsoft Defender ile tümleşiktir.

[Microsoft E365 E5'teki Güvenli Belgeler](/microsoft-365/security/office-365-security/safe-docs), Office için Application Guard'da açılan belgeleri taramak için Uç Nokta için Microsoft Defender kullanan bir özelliktir. Ek bir koruma katmanı için, tarama sonuçları belirlenene kadar kullanıcılar Office için Application Guard'dan ayrılamaz.

Uç Nokta için Microsoft Defender, kurumsal ağların gelişmiş tehditleri önlemesine, algılamasına, araştırmasına ve yanıtlamasına yardımcı olmak için tasarlanmış bir güvenlik platformudur. Bu platform hakkında daha fazla ayrıntı için bkz. [Uç Nokta için Microsoft Defender](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp). Cihazları bu platforma ekleme hakkında daha fazla bilgi için bkz. [Cihazları Uç Nokta için Microsoft Defender hizmetine ekleme](/windows/security/threat-protection/microsoft-defender-atp/onboard-configure).

Ayrıca Office 365 için Microsoft Defender Uç Nokta için Defender ile çalışacak şekilde yapılandırabilirsiniz. Daha fazla bilgi için bkz. [Office 365 için Defender Uç Nokta için Microsoft Defender ile tümleştirme](integrate-office-365-ti-with-mde.md).

## <a name="limitations-and-considerations"></a>Sınırlamalar ve dikkat edilmesi gerekenler

* Office için Application Guard, güvenilmeyen belgeleri, güvenilen şirket kaynaklarına, intranete, kullanıcının kimliğine ve bilgisayardaki rastgele dosyalara erişemeyecek şekilde yalıtan korumalı bir moddur. Sonuç olarak, bir kullanıcı disk üzerindeki yerel bir dosyadan resim ekleme gibi bu tür erişime bağımlılığı olan bir özelliğe erişmeye çalışırsa, erişim başarısız olur ve aşağıdaki örneğe benzer bir istem üretir. Güvenilmeyen bir belgenin güvenilen kaynaklara erişmesini sağlamak için, kullanıcıların belgeden Application Guard korumasını kaldırması gerekir.

  :::image type="content" source="../../media/ag09-confirm.png" alt-text="Güvenlik iletisini ve özellik durumunu belirten iletişim kutusu" lightbox="../../media/ag09-confirm.png":::

  > [!NOTE]
  > Kullanıcılara yalnızca dosyaya ve kaynağına veya nereden geldiğine güveniyorlarsa korumayı kaldırmalarını önerin.

* Güvenilmeyen bir belge güvenilir bir konumda depolandığında, konumdaki güven belge tarafından devralınır. Genellikle bir kuruluşun bulut depolama alanı güvenilir bir konum olarak tanımlanır.

* Makrolar ve ActiveX denetimleri gibi belgelerdeki etkin içerik, Office için Application Guard'da devre dışı bırakılır. Kullanıcıların etkin içeriği etkinleştirmek için Application Guard korumasını kaldırması gerekir.

* Ağ paylaşımlarındaki güvenilmeyen dosyalar veya farklı bir kuruluştan OneDrive, OneDrive İş veya SharePoint Online'dan paylaşılan dosyalar Application Guard'da salt okunur olarak açılır. Kullanıcılar kapsayıcıda çalışmaya devam etmek için bu tür dosyaların yerel bir kopyasını kaydedebilir veya doğrudan özgün dosyayla çalışmak için korumayı kaldırabilir.

* Bilgi Hakları Yönetimi (IRM) tarafından korunan dosyalar varsayılan olarak engellenir. Kullanıcılar bu tür dosyaları Korumalı Görünüm'de açmak isterse, yöneticinin kuruluş için desteklenmeyen dosya türleri için ilke ayarlarını yapılandırması gerekir.

* Kullanıcı oturumu kapatıp yeniden oturum açtığında veya cihaz yeniden başlatıldıktan sonra Office için Application Guard'da Office uygulamalarında yapılan özelleştirmeler kalıcı olmaz.

* Yalnızca UIA çerçevesini kullanan Erişilebilirlik araçları, Office için Application Guard'da açılan dosyalar için erişilebilir bir deneyim sağlayabilir.

* Yüklemeden sonra Application Guard'ın ilk başlatılması için ağ bağlantısı gereklidir. Application Guard'ın lisansı doğrulaması için bağlantı gereklidir.

* Belgenin bilgi bölümünde *, Son Değiştiren* özelliği kullanıcı olarak **WDAGUtilityAccount** görüntüleyebilir. WDAGUtilityAccount, Application Guard'da yapılandırılan anonim kullanıcıdır. Masaüstü kullanıcısının kimliği Application Guard kapsayıcısı içinde paylaşılmıyor.

## <a name="performance-optimizations-for-application-guard-for-office"></a>Office için Application Guard için performans iyileştirmeleri

Bu bölümde, Office için Application Guard'da kullanılan performans iyileştirmelerine genel bir bakış sağlanır. Bu bilgiler, Yöneticilerin Application Guard etkinleştirildiğinde Office'in performansı veya genel sistemle ilgili kullanıcılardan gelen raporları tanılamasına yardımcı olabilir.

Application Guard, güvenilmeyen belgeleri sistemden yalıtmak için sanallaştırılmış bir kapsayıcı kullanır. Kapsayıcı oluşturma ve Office belgelerini açmak için Application Guard kapsayıcısını ayarlama işlemi, kullanıcılar güvenilmeyen bir belgeyi açtığında kullanıcı deneyimini olumsuz etkileyebilecek bir performans yüküne sahiptir.

Application Guard, kullanıcılara beklenen dosya açma deneyimini sağlamak için bir sistemde aşağıdaki buluşsal yöntem karşılandığında kapsayıcıyı önceden oluşturmak için mantığı kullanır: Kullanıcı son 28 gün içinde korumalı görünümde veya Application Guard'da bir dosya açmıştır.

Bu buluşsal durum karşılandığında Office, Windows'ta oturum açtıktan sonra kullanıcı için bir Application Guard kapsayıcısı oluşturur. Bu ön oluşturma işlemi devam ederken sistem yavaş performansla karşılaşabilir, ancak işlem tamamlanır tamamlanmaz etki çözülür.

> [!NOTE]
> Kapsayıcıyı önceden oluşturmak için buluşsal yöntem için gereken ipuçları, office uygulamaları tarafından kullanıcı tarafından kullanılırken oluşturulur. Kullanıcı Office'i Application Guard'ın etkinleştirildiği yeni bir sisteme yüklerse, kullanıcı sistemde güvenilmeyen bir belgeyi ilk kez açana kadar Office kapsayıcıyı önceden oluşturmaz. Kullanıcı, bu ilk dosyanın Application Guard'da açılmasının daha uzun sürdüğünü gözlemler.

## <a name="known-issues"></a>Bilinen sorunlar

* Web bağlantılarının (`http` veya `https`) seçilmesi tarayıcıyı açmaz.
* Kopyalama-yapıştırma koruma ilkesi için varsayılan ayar yalnızca metne pano erişimini etkinleştirmektir.
* Desteklenmeyen dosya türleri koruma ilkesi için varsayılan ayar, şifrelenmiş veya Bilgi Hakları Yönetimi (IRM) ayarlanmış güvenilmeyen desteklenmeyen dosya türlerinin açılmasını engellemektir. Bu, Microsoft Purview Bilgi Koruması duyarlılık etiketleri kullanılarak şifrelenen dosyaları içerir.
* CSV ve HTML dosyaları şu anda desteklenmiyor.
* Office için Application Guard şu anda NTFS sıkıştırılmış birimleriyle çalışmıyor. "ERROR_VIRTUAL_DISK_LIMITATION" hatası görüyorsanız lütfen birimin sıkıştırmasını kaldırmayı deneyin.
* .NET'e Güncelleştirmeler, dosyaların Application Guard'da açılmamasına neden olabilir. Geçici bir çözüm olarak, kullanıcılar bu hatayla karşılaşınca cihazlarını yeniden başlatabilir. Sorun hakkında daha fazla bilgi için bkz[. Windows Defender Application Guard veya Windows Korumalı Alanı açmaya çalışırken hata iletisi alma](https://support.microsoft.com/help/4575917/receiving-an-error-message-when-attempting-to-open-windows-defender-ap).
* [Daha fazla bilgi için lütfen sık sorulan sorular - Microsoft Defender Application Guard](/windows/security/threat-protection/microsoft-defender-application-guard/faq-md-app-guard) bölümüne bakın.
