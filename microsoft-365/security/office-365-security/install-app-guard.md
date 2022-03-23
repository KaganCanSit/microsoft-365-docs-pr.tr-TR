---
title: Yöneticiler için Office Application Guard
keywords: uygulama koruması, koruma, yalıtım, yalıtılmış kapsayıcı, donanım yalıtımı
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
description: Donanım tabanlı yalıtımda en yeni özellikleri elde edin. Açıkları ve kötü amaçlı bağlantılar gibi geçerli ve ortaya çıkan saldırıların çalışan üretkenliğini ve kurumsal güvenliği kesintiye karşı engellemesini önle.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8a483c6430721e0540a7012dabfcbd4480fd7ad8
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63675382"
---
# <a name="application-guard-for-office-for-admins"></a>Yöneticiler için Office Application Guard

**Aşağıdakiler için geçerlidir:** Word, Excel, Microsoft 365 için PowerPoint, Windows 10 Enterprise, Windows 11 Enterprise

Microsoft Defender Application Guard (Office için Application Office Guard) güvenilmeyen dosyaların güvenilir kaynaklara erişmesini önlemeye, yeni ve ortaya çıkan saldırılardan kurum güvenliğinizi korumanıza yardımcı olur. Bu makale, yöneticilere, Mobil Cihazlar için Application Guard önizlemesi için cihazları ayarlama Office. Bir cihazda uygulama korumasının gereksinimlerini ve uygulamayı etkinleştirmeye ilişkin sistem Office hakkında bilgi sağlar.

## <a name="prerequisites"></a>Önkoşullar

### <a name="minimum-hardware-requirements"></a>Minimum donanım gereksinimleri

* **CPU**: 64 bit, 4 çekirdek (fiziksel veya sanal), sanallaştırma uzantıları (Intel VT-x VEYA AMD-V), Core i5 eşdeğeri veya daha yüksek önerilir
* **Fiziksel bellek**: 8 GB RAM
* **Sabit disk**: Sistem sürücüsü 10 GB boş alan (SSD önerilir)

### <a name="minimum-software-requirements"></a>Minimum yazılım gereksinimleri

* **Windows**: Windows 10 Enterprise sürümü, İstemci Derlemesi sürüm 2004 (20H1) derleme 19041 veya sonrası. Windows 11'in tüm sürümleri de desteklenen bir uygulamadır. 
* **Office**: Office Kanal ve Aylık Enterprise Kanalı, Derleme sürümü 2011 16.0.13530.10000 veya üzerinde. Office Semi-Annual Enterprise, Derleme 2108 veya sonraki sürümler. E-postanın 32 bit ve 64 bit Office sürümleri de destekle.
* **Güncelleştirme paketi**: Windows 10 [kb4571756 toplu aylık güvenlik güncelleştirmesini güncelleştirme](https://support.microsoft.com/help/4571756/windows-10-update-KB4571756)

Ayrıntılı sistem gereksinimleri için bkz. Sistem [gereksinimleri Microsoft Defender Application Guard](/windows/security/threat-protection/microsoft-defender-application-guard/reqs-md-app-guard). Ayrıca, lütfen bilgisayar üreticinizin sanallaştırma teknolojisini etkinleştirme kılavuzlarını kullanın.
Güncelleştirme kanallarını güncelleme hakkında Office fazla bilgi edinmek için bkz. [Kanallara ve kanallara genel Microsoft 365](/deployoffice/overview-update-channels).

### <a name="licensing-requirements"></a>Lisans gereksinimleri

* Microsoft 365 E5 veya Microsoft 365 E5 Güvenlik

> [!NOTE]
> Kurumlar için Microsoft 365 Uygulamaları tabanlı lisansa sahip olan kullanıcı, posta için Application Guard'a Office.

## <a name="deploy-application-guard-for-office"></a>Uygulama Koruması'nın Office

### <a name="enable-application-guard-for-office"></a>Uygulama Koruması'Office

1. **KB4571756 toplu Windows 10 güncelleştirmelerini kb4571756 indirip yükleyin**.

2. Özellikler **altında Microsoft Defender Application Guard'Windows** Tamam'ı **seçin**. Application Guard özelliğinin etkinleştirilmesi, sistemin yeniden başlatılmasını gerektirir. Şimdi veya 3. adımdan sonra yeniden başlatmayı seçebilirsiniz.

   ![Windows GÖSTEREN ÖZELLİkLER iletişim kutusu.](../../media/ag03-deploy.png)

   Özellik, aşağıdaki PowerShell komutunu yönetici olarak çalıştırarak da etkinleştirilebilir:

   ```powershell
   Enable-WindowsOptionalFeature -online -FeatureName Windows-Defender-ApplicationGuard
   ```

3. Bilgisayar **Microsoft Defender Application Guard Şablonunda** grup **\\\\ilkesi olan Yönetilen Mod'da veya Bileşenler Windows\\** içinde grup Microsoft Defender Application Guard. Seçenekler'in altındaki değeri **2** veya **3** olarak ayarp ardından Tamam veya Uygula'ya **seçerek bu** ilkeyi **açabilirsiniz**.

   ![Yönetilen Mod'da AG'ye açma.](../../media/ag04-deploy.png)

   Bunun yerine, karşılık gelen CSP İlkesini de ayarlayın:

   > OMA-URI: **./Device/Vendor/MSFT/WindowsDefenderApplicationGuard/Ayarlar/AllowWindowsDefenderApplicationGuard** <br> Veri türü: **Tamsayı** <br> Değer: **2**

4. Sistemi yeniden başlatın.

### <a name="set-diagnostics--feedback-to-send-full-data"></a>Tanılama ve geri & verileri gönderecek şekilde ayarlama

> [!NOTE]
> Bu gerekli değildir, ancak isteğe bağlı tanılama verileri yapılandırmak bildirilen sorunları tanılamaya yardımcı olur.

Bu adım, sorunları tanımlamak ve düzeltmek için gereken verilerin Microsoft'a ulaşmasını sağlar. Tanılamayı Windows etkinleştirmek için şu Windows izleyin:

1. Dosya **Ayarlar'i** Başlat menüsü.

   ![Başlat menüsü.](../../media/ag05-diagnostic.png)

2. Gizlilik **Windows Ayarlar'i** **seçin**.

   ![Windows Ayarlar seçin.](../../media/ag06-diagnostic.png)

3. Gizlilik altında Tanılama ve geri **bildirim & İsteğe** bağlı tanılama **verileri'ne seçin**.

   ![Tanılama ve geri bildirim menüsü.](../../media/ag07a-diagnostic.png)

Tanılama ayarlarını yapılandırma hakkında Windows için bkz. [Windows verilerini yapılandırma](/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enterprise-management).

### <a name="confirm-that-application-guard-for-office-is-enabled-and-working"></a>Kullanıcı için Application Guard'Office etkinleştirildiğinden ve çalıştığını onaylama

Office için Application Guard'ın etkin olduğunu onaylamadan önce, ilkelerin dağıtıldı olduğu cihazda Word, Excel veya PowerPoint'i açın. Bu Office emin olun. İlk olarak iş kimliğinizi kullanarak en son ürünü Office gerekir.

Application Guard'ın etkinleştirildiğinden Office için Word, Excel veya PowerPoint'i açın ve ardından güvenilmeyen bir belgeyi açın. Örneğin, İnternet'den indirilen bir belgeyi veya kuruluş dışındaki bir kişi tarafından e-posta ekini açabilirsiniz.

Güvenilmeyen bir dosyayı ilk kez asanız, aşağıdaki örnekte Office bir giriş ekranı görebilirsiniz. Bir süre için Application Guard for Office etkinken ve dosya açıkken görüntülenebilir. Güvenilmeyen dosyaların sonraki açılışları daha hızlı olur.

![Office uygulaması giriş ekranı.](../../media/ag08-confirm.png)

Açıldığında, dosyanın, uygulama koruması altında açılması için birkaç görsel gösterge Office:

* Şeritte bir callout

  ![Küçük App Guard notunu gösteren belge dosyası.](../../media/ag09-confirm.png)

* Görev çubuğunda kalkanlı uygulama simgesi

  ![Görev çubuğundaki simge.](../../media/ag12-limitations.png)

## <a name="configure-application-guard-for-office"></a>Uygulama Koruması'nın ayarlarını Office

Office, güvenlik özellikleri için Application Guard'ın özelliklerini yapılandırmayı etkinleştirmek üzere aşağıdaki Office. Bu ilkeler Grup ilkeleri aracılığıyla veya Office [ilkesi hizmeti aracılığıyla yalnabilirsiniz](/DeployOffice/overview-office-cloud-policy-service).


> [!NOTE]
> Bu ilkelerin yapılandırılması, Office için Application Guard'da açılan dosyalar için bazı işlevleri devre Office.

|İlke|Açıklama|
|---|---|
|Application Guard';;da uygulama koruması Office|Bu ilkenin etkinleştirilmesi, Word, Excel ve PowerPoint'i, Office için Application Guard yerine Korumalı Görünüm yalıtım kapsayıcısı kullanmaya Office. Bu ilke, güvenlik nedeniyle güvenliği etkinleştirmede sorun olduğunda Office Için Application Guard'ı geçici olarak Microsoft Edge.|
|Önceden oluşturulacak kapsayıcı Office Application Guard'ını yapılandırma|Bu ilke, güvenilmeyen dosyalar için Office Application Guard'ın, geliştirilmiş çalıştırma süresi performansı için önceden oluşturulsa bunu belirler. Bu ayarı etkinleştirirseniz, önceden bir kapsayıcı oluşturmaya devam etmek için gün sayısını belirtebilirsiniz veya Office önceden kapsayıcıyı oluşturmasına izin veebilirsiniz.
|Belgeler için Application Guard'da Office/yapıştırmaya izin Office|Bu ilkenin etkinleştirilmesi, kullanıcının, application Guard'da açılan bir belgeden içeriği kopyalayıp, Office dışında açılan bir belgeye kopyalamasını ve kopyalamasını engelleyecek.|
|Application Guard'da donanım hızlandırmayı devre dışı Office|Bu ilke, bilgisayarınızın Application Guard'ın Office işlemek için donanım hızlandırması kullandığını kontrol eder. Bu ayarı etkinleştirirseniz, Office için Application Guard yazılım tabanlı (CPU) işleme kullanır ve hiçbir üçüncü taraf grafik sürücüsü yüklemez veya bağlantılı grafik donanımıyla etkileşimde bulunmazsanız.
|For Application Guard'da desteklenmeyen dosya türleri korumasını devre dışı Office|Bu ilke, For Office Application Guard'ın desteklenmeyen dosya türlerinin açılmasını mı engelley yoksa yeniden yönlendirmeyi Korumalı Görünüm'e etkinleştirmesini mi engelleyecektir?
|Daha fazla bilgi için Application Guard'da açılan belgeler için kamera ve mikrofon Office|Bu ilkenin etkinleştirilmesi, Office için Application Guard'ın içinde kameraya ve mikrofona erişimi Office.|
|Belgeler için Application Guard'da açılan belgelerden yazdırmayı Office|Bu ilkenin etkinleştirilmesi, kullanıcının bu yazıcılar için Application Guard'da açılan bir dosyadan yazdır olduğu yazıcıları Office. Örneğin, kullanıcıları yalnızca PDF'ye yazdırılacak şekilde kısıtlamak için bu ilkeyi kullanabilirsiniz.|
|Kullanıcıların dosyalarda Uygulama Koruması'Office kaldırmasını engelleme|Bu ilkenin etkinleştirilmesi, Application Guard'ı Office koruması için devre dışı bırakma veya Office için Application Guard dışında bir dosya açma seçeneğini (Office. <p> **Not:** Kullanıcılar, web'de işaret özelliğini dosyadan el ile kaldırarak veya bir belgeyi Güvenilir konuma kaldırarak bu ilkeyi atlarlar.|

> [!NOTE]
> Aşağıdaki ilkeler, kullanıcının oturumlarını açmasını ve yürürlüğe almak için Windows açmasını gerektirir:
>
> * For Application Guard'da açılan belgeler için kopyalama/yapıştırmayı devre dışı Office
> * Belgeler için Application Guard'da açılan belgeler için yazdırmayı Office
> * Uygulama Koruması'na açılan belgelere kamera ve mikrofon erişimini Office

## <a name="submit-feedback"></a>Geri bildirim gönderme

### <a name="submit-feedback-via-feedback-hub"></a>Geri Bildirim Merkezi aracılığıyla geri bildirim gönderme

Destek için Application Guard'ı Office sorunla karşılaşırsanız, Geri Bildirim Merkezi aracılığıyla geri bildiriminizi göndermeniz teşvik edildi:

1. Geri Bildirim **Merkezi uygulamasını açın** ve oturum açın.

2. Application Guard'ı başlatma sırasında bir hata iletişim kutusu alırsanız, yeni bir geri bildirim gönderme başlatmak için hata iletişim kutusunda **Microsoft'a** Bildir'i seçin. Aksi takdirde, Application <https://aka.ms/mdagoffice-fb> Guard için doğru kategoriyi seçmek için gidin ve sağ üst **+&nbsp;yakınına yeni geri** bildirim ekle'yi seçin.

3. Sizin için henüz **doldurulmadı** ise, Geri bildiriminizi özetleme kutusuna bir özet girin.

4. Deneyimle ilgili ayrıntılı bir açıklama girin ve Daha fazla ayrıntı için açıkla kutusuna hangi adımları uygulayın **, ardından** Sonraki'yi **seçin**.

5. Sorun'a yanındaki kabarcığı **seçin**. Seçilen kategorinin Güvenlik ve Gizlilik Ayarları **(Güvenlik ve \> Microsoft Defender Application Guard) olduğundan emin Office** sonra da Sonraki'yi **seçin**.

6. Yeni geri **bildirim'i** ve ardından **Sonraki'yi seçin**.

7. Sorunla ilgili izlemeleri toplayın:

   1. Sorunımı **yeniden oluştur kutucuğunu** genişletin.

   2. Application Guard çalışırken bu sorunla karşılaşıyorsanız, Application Guard örneğini açın. Bir örneği açmak, Application Guard kapsayıcısı içinde ek izlemeler toplanabilir.

   3. Kaydı **başlat'ı** seçin ve kutucuğun döneni durdurması ve Kaydı durdur *seçeneğini söylemelerini bekleyin*.

   4. Application Guard ile sorunu tümüyle yeniden üretin. Yeniden üretme, bir Application Guard örneğini başlatmayı denemeyi, başarısız olana kadar beklemeyi veya çalışan Application Guard örneğinde bir sorunu yeniden üretmeyi içerebilir.

   5. Kaydı durdur **kutucuğunu** seçin.

   6. Kapsayıcı tanılamanın da toplansını için, gönderiden birkaç dakika sonra bile tüm çalışan Application Guard örneklerini açık tutabilirsiniz.

8. Sorunla ilgili ekran görüntüleri veya dosyalar iliştirin.

9. **Gönder'i seçin**.

### <a name="submit-feedback-via-office-customer-voice"></a>Müşteri Sesi'Office geri bildirim gönderme

Uygulama Koruması'Office belgeler açıldığında sorun Office e-postanın Office geri bildirim gönderebilirsiniz. Geri bildirim Office [Insider El Kitabı'na](https://insider.office.com/handbook) bakın.

## <a name="integration-with-microsoft-defender-for-endpoint-and-microsoft-defender-for-office-365"></a>Uç Nokta için Microsoft Defender ve Güvenlik için Microsoft Defender ile Office 365

Application Guard for Office is integrated with Microsoft Defender for Endpoint to provide monitoring and alerting on malicious activity that happens in the is yalıtılmış ortamda.

[Kasa E365 E5'te Belgeler, microsoft e-posta](/microsoft-365/security/office-365-security/safe-docs) için Application Guard'da açılan belgeleri taramak için Uç Nokta için Microsoft Defender'ı kullanan bir Office. Ek bir koruma katmanı için, tarama sonuçları belirlenene kadar kullanıcılar Office Application Guard'dan ayrılamaz.

Uç Nokta için Microsoft Defender, kurumsal ağların gelişmiş tehditleri engellemesini, algılamasını, araştırmasını ve yanıtlamasını önlemeye yardımcı olmak için tasarlanmış bir güvenlik platformudur. Bu platform hakkında daha fazla ayrıntı için bkz. [Uç Nokta için Microsoft Defender](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp). Bu platforma cihaz ekleme hakkında daha fazla bilgi edinmek için bkz. [Uç nokta hizmeti için Microsoft Defender'a cihaz ekleme](/windows/security/threat-protection/microsoft-defender-atp/onboard-configure).

Ayrıca, uç nokta için Defender ile Office 365 için Microsoft Defender'ı da yapılandırebilirsiniz. Daha fazla bilgi için bkz. [Office 365 için Microsoft Defender ile Uç Nokta için Defender'ı Tümleştir.](integrate-office-365-ti-with-mde.md)

## <a name="limitations-and-considerations"></a>Sınırlamalar ve dikkate alınacak noktalar

* Office için Application Guard, güvenilir olmayan belgeleri yalıtır ve böylece bilgisayarda güvenilir şirket kaynaklarına, intranete, kullanıcının kimliğine ve rastgele dosyalara erişiyemeyen bir korumalı moddur. Sonuç olarak, kullanıcı diskte yerel bir dosyadan resim ekleme gibi bu tür erişime bağımlı bir özel özellikle erişmeyi çalışırsa, erişim başarısız olur ve aşağıdaki örneğine benzer bir istem oluşturur. Güvenilmeyen bir belgenin güvenilen kaynaklara erişmesi için, kullanıcıların belgeden Application Guard korumasını kaldırması gerekir. 

  ![Güvenli tutmanıza yardımcı olmak için bu özelliği kullanılamaz söyleyen iletişim kutusu.](../../media/ag10-limitations.png)

  > [!NOTE]
  > Kullanıcılara yalnızca dosyaya ve kaynağına ya da kaynağına güvenseler korumayı kaldırmalarını önerin.

* Güvenilmeyen bir belge güvenilir bir konumda depolanıyorsa, bu konumdaki güven belgeye devralınan bir belgedir. Normalde, kuruluşun bulut depolama alanı güvenilir bir konum olarak tanımlanır.
  
* Makrolar ve makrolar gibi belgelerde etkin ActiveX, bu denetimler için Application Guard'da Office. Kullanıcıların etkin içeriği etkinleştirmek için Application Guard korumasını kaldırmaları gerekir.

* Farklı bir kuruluşun OneDrive, OneDrive İş veya SharePoint Online'dan paylaşılan ağ paylaşımlarından veya dosyalardan güvenilmeyen dosyalar Application Guard'da salt okunur olarak açılır. Kullanıcılar kapsayıcıda çalışmaya devam etmek için bu dosyaların yerel kopyasını kaydedebilir veya özgün dosyayla doğrudan çalışmak için korumayı kaldırabilir.

* Bilgi Hakları Yönetimi (IRM) tarafından korunan dosyalar varsayılan olarak engellenir. Kullanıcılar bu tür dosyaları Korumalı Görünüm'de açmak isterse, yöneticinin kuruluşta desteklenmeyen dosya türleri için ilke ayarlarını yapılandırması gerekir.

* Application Guard Office da Office uygulamalarına yapılan hiçbir özelleştirme, kullanıcı oturumlarını çıkıp yeniden oturum aktan sonra veya cihaz yeniden başlatıldıktan sonra kalıcı olmaz.

* Yalnızca UIA çerçevesini kullanan Erişilebilirlik araçları, güvenlik özellikleri için Application Guard'da açılan dosyalar için erişilebilir bir Office.

* Yüklemeden sonra Application Guard'ın ilk başlatması için ağ bağlantısı gereklidir. Application Guard'ın lisansı doğrulaması için bağlantı gereklidir.

* Belgenin bilgi bölümünde, *Last Modified By* özelliği **WDAGUtilityAccount'ı kullanıcı** olarak değiştirilebilir. WDAGUtilityAccount, Application Guard'da yapılandırılan anonim kullanıcıdır. Masaüstü kullanıcı kimliği Application Guard kapsayıcısı içinde paylaşılmaz.

## <a name="performance-optimizations-for-application-guard-for-office"></a>Uygulama Koruması için performans iyileştirmeleri Office

Bu bölümde, uygulama korumaları için Application Guard'da kullanılan performans iyileştirmeleri hakkında genel Office. Bu bilgiler yöneticilerin, Application Guard etkinleştirildiğinde performansı veya genel sistemle ilgili Office raporları tanılamaya yardımcı olabilir.

Application Guard güvenilmeyen belgeleri sistemden ayırmak için sanallaştırılmış bir kapsayıcı kullanır. Kapsayıcı oluşturma ve Application Guard kapsayıcıyı Office belgelerini açmak için ayarlama işlemi, kullanıcılar güvenilmeyen bir belgeyi açtıkları için kullanıcı deneyimini olumsuz etkileyen bir performans yüküne sahiptir.

Kullanıcılara beklenen dosya açma deneyimini sağlamak için, Application Guard sistemde aşağıdaki üç çıtayı karşı açtığında bir kapsayıcı önceden oluşturmak için mantık kullanır: Kullanıcı son 28 gün içinde bir dosyayı Korumalı Görünüm veya Application Guard'da açtı.

Bu üç durumlu durumla karşılaş Office, Windows'te oturum akten sonra kullanıcı için önceden bir Application Guard kapsayıcısı Windows. Bu önceden oluşturma işlemi devam ederken, sistem yavaş performansla neden olabilir, ancak işlem tamamlandıktan sonra bu etki çözülecek.

> [!NOTE]
> Kapsayıcıyı önceden oluşturmak için var olan ipuçları, kullanıcı tarafından Office olarak oluşturulur. Kullanıcı Application Guard'Office yeni bir sisteme Office, kullanıcı sistemde güvenilmeyen bir belgeyi ilk kez açana kadar Office kapsayıcıyı önceden oluşturmaz. Kullanıcı, bu ilk dosyanın Application Guard'da açılmasının daha uzun zaman alı olduğunu gözlemler.

## <a name="known-issues"></a>Bilinen sorunlar

* Web bağlantıları ( veya`http` `https`) seçerek tarayıcı açılmaz.
* Kopyalama-yapıştırma koruması ilkesi için varsayılan ayar pano erişimini yalnızca metne etkinleştirmektir.
* Desteklenmeyen dosya türleri koruma ilkesi için varsayılan ayar, şifrelenmiş veya Bilgi Hakları Yönetimi (IRM) ayarlanmış güvenilmeyen dosya türlerinin açılmasını engellemektir. Bu, şifreleme (gizli Microsoft Bilgi Koruması çok gizli) kullanarak hassas duyarlılık etiketleri içeren dosyaları içerir.
* CSV ve HTML dosyaları şu anda desteklenmiyor.
* Application Guard for Office şu anda NTFS sıkıştırılmış hacimleri ile çalışmıyor. "Ses düzeyi" hatasını ERROR_VIRTUAL_DISK_LIMITATION ses düzeyinin sıkıştırılmamış olarak sıkıştırılmamış olarak  denemesi gerekir.
* .NET güncelleştirmeleri, dosyaların Application Guard'da açılmalarına neden olabilir. Geçici bir çözüm olarak, kullanıcılar bu hatayla karşı karşıya olduğunda cihazlarını yeniden başlatabilirsiniz. Korumalı Alan'da veya Korumalı [Alanı'nda açılmaya çalışılıyorken hata iletisi Windows Defender Application Guard hakkında Windows bilgi alın](https://support.microsoft.com/help/4575917/receiving-an-error-message-when-attempting-to-open-windows-defender-ap).
* Ek bilgi [için lütfen Sık sorulan Microsoft Defender Application Guard - Yardım'a bakın.](/windows/security/threat-protection/microsoft-defender-application-guard/faq-md-app-guard) 
