---
title: Uç Nokta için Microsoft Defender değerlendirme laboratuvarı
description: Uç Nokta için Microsoft Defender özellikleri hakkında bilgi edinin, saldırı benzetimi çalıştırın ve tehditleri nasıl önlediğine, algılayıp düzelttiğine bakın.
keywords: Uç Nokta için Microsoft Defender değerlendirme, değerlendirme, laboratuvar, simülasyon, windows 10, windows server 2019, değerlendirme laboratuvarı
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.prod: m365-security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-evalutatemtp
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 3d13c3b126f4aae75ff775ac3170049dfc9c0a2e
ms.sourcegitcommit: 872ab0b6a225c20274916e07ed4cc4944be9509a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2022
ms.locfileid: "65679450"
---
# <a name="microsoft-defender-for-endpoint-evaluation-lab"></a>Uç Nokta için Microsoft Defender değerlendirme laboratuvarı

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Kapsamlı bir güvenlik ürünü değerlendirmesi yapmak, uçtan uca saldırı simülasyonu yapılabilmesi için önce hantal ortam ve cihaz yapılandırması gerektiren karmaşık bir süreç olabilir. Karmaşıklık düzeyine eklemek, değerlendirme sırasında simülasyon etkinliklerinin, uyarıların ve sonuçların yansıtıldığı yeri izleme zorluğudur.

Uç Nokta için Microsoft Defender değerlendirme laboratuvarı, platformun özelliklerini değerlendirmeye, simülasyon çalıştırmaya ve önleme, algılama ve düzeltme özelliklerini çalışırken görmeye odaklanabilmeniz için cihaz ve ortam yapılandırmasının karmaşıklıklarını ortadan kaldıracak şekilde tasarlanmıştır.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUM]

Basitleştirilmiş kurulum deneyimiyle, Uç Nokta için Defender'ın nasıl performans sergilediğini görmek için kendi test senaryolarınızı ve önceden hazırlanmış simülasyonları çalıştırmaya odaklanabilirsiniz.

Platformun otomatik araştırma, gelişmiş tehdit analizi ve tehdit analizi gibi güçlü özelliklerine tam erişiminiz olacak ve bu sayede Uç Nokta için Defender'ın sunduğu kapsamlı koruma yığınını test edebilirsiniz.

En son işletim sistemi sürümlerinin ve doğru güvenlik bileşenlerinin yanı sıra Office 2019 Standard'ın yüklü olması için önceden yapılandırılmış olarak gelen Windows 10, Windows 11, Windows Server 2019, Windows Server 2016 ve Linux (Ubuntu) cihazları ekleyebilirsiniz.

Tehdit simülatörlerini de yükleyebilirsiniz. Uç Nokta için Defender, portaldan çıkmak zorunda kalmadan Uç Nokta için Defender özelliklerini test etmeye yardımcı olmak için sektör lideri tehdit simülasyonu platformlarıyla iş ortaklığı yaptı.

Tercih ettiğiniz simülatörü yükleyin, değerlendirme laboratuvarında senaryolar çalıştırın ve platformun nasıl performans sergilediğini anında görün. Bunların hepsi sizin için ek ücret ödemeden kolayca kullanılabilir. Ayrıca, simülasyon kataloğundan erişebileceğiniz ve çalıştırabileceğiniz çok çeşitli simülasyonlara da kolayca erişebilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

Değerlendirme laboratuvarına erişmek için [lisanslama gereksinimlerini](minimum-requirements.md#licensing-requirements) karşılamanız veya Uç Nokta için Microsoft Defender deneme erişimine sahip olmanız gerekir.

**Güvenlik ayarlarını yönet** izinlerine sahip olmanız gerekir:

- Laboratuvarı oluşturma
- Cihaz oluşturma
- Parolayı sıfırlayın
- Benzetimi oluşturma

Rol tabanlı erişim denetimini (RBAC) etkinleştirdiyseniz ve en az bir makine grubu oluşturduysanız, kullanıcıların Tüm makine gruplarına erişimi olmalıdır.

Daha fazla bilgi için bkz. [Rolleri oluşturma ve yönetme](user-roles.md).

Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink)

## <a name="get-started-with-the-lab"></a>Laboratuvarla Kullanmaya başlayın

Laboratuvara menüden erişebilirsiniz. Gezinti menüsünde **Değerlendirme ve öğreticiler > Değerlendirme laboratuvarı'nı** seçin.

> [!NOTE]
>
> - Seçtiğiniz ortam yapısının türüne bağlı olarak, cihazlar etkinleştirme gününden itibaren belirtilen sayıda saat boyunca kullanılabilir.
> - Her ortam sınırlı sayıda test cihazıyla sağlanır. Sağlanan cihazları kullanıp sildiğinizde daha fazla cihaz isteyebilirsiniz.
> - Laboratuvar kaynakları için ayda bir istekte bulunabilirsiniz.

Zaten bir laboratuvarınız var mı? Yeni tehdit simülatörlerini etkinleştirdiğinizden ve etkin cihazlara sahip olduğundan emin olun.

## <a name="setup-the-evaluation-lab"></a>Değerlendirme laboratuvarını ayarlama

1. Gezinti bölmesinde **Değerlendirme & öğreticiler** \> **Değerlendirme laboratuvarı'nı** ve ardından **Kurulum laboratuvarı'nı** seçin.

   :::image type="content" source="../../media/evaluationtutormenu.png" alt-text="Değerlendirme laboratuvarı karşılama sayfası" lightbox="../../media/evaluationtutormenu.png":::

2. Değerlendirme gereksinimlerinize bağlı olarak, daha uzun bir süre için daha az veya daha kısa bir süre için daha fazla cihaz içeren bir ortam ayarlamayı seçebilirsiniz. Tercih ettiğiniz laboratuvar yapılandırmasını ve ardından **İleri'yi** seçin.

    :::image type="content" source="images/lab-creation-page.png" alt-text="Laboratuvar yapılandırma seçenekleri" lightbox="images/lab-creation-page.png":::

3. (İsteğe bağlı) Tehdit simülatörlerini laboratuvara yüklemeyi seçebilirsiniz.

    :::image type="content" source="images/install-agent.png" alt-text="Simülatör aracısını yükleme sayfası" lightbox="images/install-agent.png":::

   > [!IMPORTANT]
   > Öncelikle hüküm ve bilgi paylaşım bildirimlerini kabul etmeniz ve onay vermeniz gerekir.

4. Kullanmak istediğiniz tehdit simülasyonu aracısını seçin ve ayrıntılarınızı girin. Tehdit simülatörlerini daha sonra yüklemeyi de seçebilirsiniz. Laboratuvar kurulumu sırasında tehdit simülasyon aracılarını yüklemeyi seçerseniz, eklediğiniz cihazlara kolayca yükleme avantajından yararlanabilirsiniz.

   :::image type="content" source="images/lab-setup-summary.png" alt-text="Özet sayfası" lightbox="images/lab-setup-summary.png":::

5. Özeti gözden geçirin ve **Kurulum laboratuvarı'nı** seçin.

Laboratuvar kurulum işlemi tamamlandıktan sonra cihaz ekleyebilir ve benzetimi çalıştırabilirsiniz.

## <a name="add-devices"></a>Cihaz ekleme

Ortamınıza bir cihaz eklediğinizde, Uç Nokta için Defender bağlantı ayrıntılarıyla iyi yapılandırılmış bir cihaz ayarlar. Windows 10, Windows 11, Windows Server 2019, Windows Server 2016 ve Linux (Ubuntu) ekleyebilirsiniz.

Cihaz, java, Python ve SysIntenals gibi diğer uygulamaların yanı sıra işletim sisteminin ve Office 2019 Standard'ın en güncel sürümüyle yapılandırılır.

Laboratuvar kurulumu sırasında bir tehdit simülatörü eklemeyi seçerseniz, eklediğiniz cihazlarda tüm cihazlarda tehdit simülatörü aracısı yüklü olur.

Cihaz, önerilen Windows güvenlik bileşenleri açık ve denetim modunda olacak şekilde kiracınıza otomatik olarak eklenir ve sizin tarafınızda hiçbir çaba olmaz.

Aşağıdaki güvenlik bileşenleri test cihazlarında önceden yapılandırılmıştır:

- [Saldırı yüzeyini azaltma](attack-surface-reduction.md)
- [İlk görüşte engelle](configure-block-at-first-sight-microsoft-defender-antivirus.md)
- [Denetimli klasör erişimi](controlled-folders.md)
- [Exploit Protection](enable-exploit-protection.md)
- [Ağ koruması](network-protection.md)
- [İstenmeyebilecek uygulama algılama](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)
- [Bulut tabanlı koruma](cloud-protection-microsoft-defender-antivirus.md)
- [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

> [!NOTE]
> Microsoft Defender Virüsten Koruma açık (denetim modunda değil). Microsoft Defender Virüsten Koruma simülasyonunuzu çalıştırmanızı engelliyorsa, Windows Güvenliği aracılığıyla cihazda gerçek zamanlı korumayı kapatabilirsiniz. Daha fazla bilgi için bkz. [Her zaman açık korumayı yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md).

Otomatik araştırma ayarları kiracı ayarlarına bağımlı olacaktır. Varsayılan olarak yarı otomatik olacak şekilde yapılandırılır. Daha fazla bilgi için bkz. [Otomatik araştırmalara genel bakış](automated-investigations.md).

> [!NOTE]
> Test cihazlarına bağlantı RDP kullanılarak yapılır. Güvenlik duvarı ayarlarınızın RDP bağlantılarına izin verin.

1. Panodan **Cihaz ekle'yi** seçin.

2. Eklenecek cihaz türünü seçin. Windows 10, Windows 11, Windows Server 2019, Windows Server 2016 ve Linux (Ubuntu) eklemeyi seçebilirsiniz.

   :::image type="content" source="../../media/add-machine-optionsnew.png" alt-text="Cihaz seçenekleriyle laboratuvar kurulumu" lightbox="../../media/add-machine-optionsnew.png":::

   > [!NOTE]
   > Cihaz oluşturma işleminde bir sorun olursa size bildirilir ve yeni bir istek göndermeniz gerekir. Cihaz oluşturma işlemi başarısız olursa, izin verilen genel kotaya göre sayılmaz.

3. Bağlantı ayrıntıları görüntülenir. Cihazın parolasını kaydetmek için **Kopyala'yı** seçin.

   > [!NOTE]
   > Parola yalnızca bir kez görüntülenir. Daha sonra kullanmak üzere kaydettiğinizden emin olun.

    :::image type="content" source="../../media/add-machine-eval-lab-new.png" alt-text="Bağlantı ayrıntılarıyla eklenen cihaz" lightbox="../../media/add-machine-eval-lab-new.png":::

4. Cihaz kurulumu başlar. Bu işlem yaklaşık 30 dakika sürebilir.

5. **Cihazlar** sekmesini seçerek test cihazlarının durumunu, risk ve maruz kalma düzeylerini ve simülatör yüklemelerinin durumunu görün.

   :::image type="content" source="images/machines-tab.png" alt-text="Cihazlar sekmesi" lightbox="images/machines-tab.png":::
    

   > [!TIP]
   > **Simülatör durumu** sütununda, aracının yükleme durumunu öğrenmek için bilgi simgesinin üzerine gelebilirsiniz.


## <a name="add-a-domain-controller-preview"></a>Etki alanı denetleyicisi ekleme (Önizleme)

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen önceden yayımlanmış ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Birden çok cihazda yanal hareket ve çok aşamalı saldırılar gibi karmaşık senaryoları çalıştırmak için bir etki alanı denetleyicisi ekleyin.


>[!NOTE]
>Etki alanı desteği yalnızca Microsoft 365 Defender portalında (security.microsoft.com) kullanılabilir.

1. Panodan **Cihaz ekle'yi** seçin.

2. **Windows Server 2019'ı** ve ardından **Etki alanı denetleyicisi olarak ayarla'yı** seçin. 

3. Etki alanı denetleyiciniz sağlandığında, **Cihaz ekle'ye** tıklayarak etki alanına katılmış cihazlar oluşturabilirsiniz. Ardından Windows 10 / Windows 11'ı ve **ardından Etki alanına katıl'ı** seçin. 

>[!NOTE]
>Aynı anda yalnızca bir etki alanı denetleyicisi canlı olabilir. Etki alanı denetleyicisi cihazına bağlı canlı bir cihaz olduğu sürece canlı kalır.



## <a name="request-for-more-devices"></a>Daha fazla cihaz isteme

Tüm mevcut cihazlar kullanıldığında ve silindiğinde, daha fazla cihaz isteyebilirsiniz. Laboratuvar kaynakları için ayda bir istekte bulunabilirsiniz.

1. Değerlendirme laboratuvarı panosundan **Daha fazla cihaz iste'yi** seçin.

   :::image type="content" source="images/request-more-devices.png" alt-text="Daha fazla cihaz isteği seçeneği" lightbox="images/request-more-devices.png":::

2. Yapılandırmanızı seçin.
3. İsteği gönderin.

İstek başarıyla gönderildiğinde yeşil bir onay başlığı ve son gönderim tarihini görürsünüz.

İsteğinizin durumunu, birkaç saat içinde onaylanacak olan **Kullanıcı Eylemleri** sekmesinde bulabilirsiniz.

Onaylandığında, istenen cihazlar laboratuvar kurulumunuza eklenir ve daha fazla cihaz oluşturabilirsiniz.

> [!TIP]
> Laboratuvarınızdan daha fazla yararlanmak için simülasyon kitaplığımızı gözden geçirin.

## <a name="simulate-attack-scenarios"></a>Saldırı senaryolarının benzetimini yapmak

Kendi saldırı simülasyonlarınızı çalıştırmak için test cihazlarını kullanarak bunlara bağlanın.

Saldırı senaryolarının benzetimini şu şekilde yapabilirsiniz:

- ["Kendiniz Yapın" saldırı senaryoları](https://security.microsoft.com/tutorials/all)
- Tehdit simülatörleri

Ayrıca, yeni ortaya çıkan tehditlerle ilgili raporları görüntülemek üzere verileri ve [Tehdit analizini](threat-analytics.md) sorgulamak için [Gelişmiş avcılık](advanced-hunting-overview.md) özelliğini de kullanabilirsiniz.

### <a name="do-it-yourself-attack-scenarios"></a>Kendi kendine saldırı senaryoları

Önceden hazırlanmış bir simülasyon arıyorsanız ["Kendiniz Yapın" saldırı senaryolarımızı](https://security.microsoft.com/tutorials/all) kullanabilirsiniz. Bu betikler güvenlidir, belgelenir ve kullanımı kolaydır. Bu senaryolar Uç Nokta için Defender özelliklerini yansıtır ve araştırma deneyiminde size yol gösterir.

> [!NOTE]
> Test cihazlarına bağlantı RDP kullanılarak yapılır. Güvenlik duvarı ayarlarınızın RDP bağlantılarına izin verin.

1. cihazınıza Bağlan ve **Bağlan'ı** seçerek bir saldırı simülasyonu çalıştırın.

    :::image type="content" source="images/test-machine-table.png" alt-text="Test cihazları için Bağlan düğmesi" lightbox="images/test-machine-table.png":::


   :::image type="content" source="images/remote-connection.png" alt-text="Uzak masaüstü bağlantısı ekranı" lightbox="images/remote-connection.png":::

    **Linux cihazları** için: Yerel bir SSH istemcisi ve sağlanan komutu kullanmanız gerekir. 


    > [!NOTE]
    > İlk kurulum sırasında parolanın bir kopyası kaydedilmediyse, menüden **Parolayı sıfırla'yı seçerek parolayı** sıfırlayabilirsiniz:
    >
    > :::image type="content" source="images/reset-password-test-machine.png" alt-text="Parolayı sıfırla seçeneği" lightbox="images/reset-password-test-machine.png":::
    >
    > Cihaz durumunu "Parola sıfırlama yürütülüyor" olarak değiştirir, ardından size birkaç dakika içinde yeni parolanız sunulur.

3. Cihaz oluşturma adımı sırasında görüntülenen parolayı girin.

   :::image type="content" source="images/enter-password.png" alt-text="Kimlik bilgilerini girdiğiniz ekran" lightbox="images/enter-password.png":::

4. Cihazda Kendin yap saldırı simülasyonlarını çalıştırın.

### <a name="threat-simulator-scenarios"></a>Tehdit simülatörü senaryoları

Laboratuvar kurulumu sırasında desteklenen tehdit simülatörlerinden herhangi birini yüklemeyi seçtiyseniz, yerleşik simülasyonları değerlendirme laboratuvarı cihazlarında çalıştırabilirsiniz.

Üçüncü taraf platformlarını kullanarak tehdit simülasyonları çalıştırmak, laboratuvar ortamının sınırları içinde Uç Nokta için Microsoft Defender özellikleri değerlendirmek için iyi bir yoldur.

> [!NOTE]
>
> Simülasyonları çalıştırabilmeniz için önce aşağıdaki gereksinimlerin karşılandığından emin olun:
>
> - Cihazların değerlendirme laboratuvarına eklenmesi gerekir
> - Tehdit simülatörleri değerlendirme laboratuvarına yüklenmelidir

1. Portaldan **Simülasyon oluştur'u** seçin.

2. Bir tehdit simülatörü seçin.

   :::image type="content" source="images/select-simulator.png" alt-text="Tehdit simülatörü seçimi" lightbox="images/select-simulator.png":::

3. Bir simülasyon seçin veya kullanılabilir simülasyonlara göz atmak için simülasyon galerisine bakın.

    Simülasyon galerisine buradan ulaşabilirsiniz:
    - **Simülasyonlara genel bakış** kutucuğundaki ana değerlendirme panosu veya
    - Gezinti bölmesinden **Değerlendirme ve öğretici simülasyonu** \> **& öğreticiler'e** giderek **Simülasyonlar kataloğu'nu** seçin.

4. Simülasyonu çalıştırmak istediğiniz cihazları seçin.

5. **Simülasyon oluştur'u** seçin.

6. **Simülasyonlar** sekmesini seçerek simülasyonun ilerleme durumunu görüntüleyin. Simülasyon durumunu, etkin uyarıları ve diğer ayrıntıları görüntüleyin.

   :::image type="content" source="images/simulations-tab.png" alt-text="Simülasyonlar sekmesi" lightbox="images/simulations-tab.png":::

Simülasyonlarınızı çalıştırdıktan sonra laboratuvar ilerleme çubuğunu incelemenizi ve **otomatik araştırmayı ve düzeltmeyi tetikleyen Uç Nokta için Microsoft Defender** keşfetmenizi öneririz. Özellik tarafından toplanan ve analiz edilen kanıtlara göz atın.

Zengin sorgu dilini ve ham telemetriyi kullanarak gelişmiş avcılık yoluyla saldırı kanıtı arayın ve Tehdit analizinde belgelenen dünya çapındaki bazı tehditlere göz atın.

## <a name="simulation-gallery"></a>Simülasyon galerisi

Uç Nokta için Microsoft Defender, platformun özelliklerini doğrudan portaldan test etmek için size kolay erişim sağlamak için çeşitli tehdit simülasyonu platformlarıyla işbirliği yaptı.

Menüden **Simülasyonlar ve öğreticiler Simülasyonlar** kataloğu'na giderek tüm kullanılabilir **simülasyonları** \> görüntüleyin.

Desteklenen üçüncü taraf tehdit simülasyonu aracılarının listesi listelenir ve katalogda ayrıntılı açıklamalarla birlikte belirli simülasyon türleri sağlanır.

Kullanılabilir simülasyonları doğrudan katalogdan kolayca çalıştırabilirsiniz.

:::image type="content" source="images/simulations-catalog.png" alt-text="Simülasyon kataloğu" lightbox="images/simulations-catalog.png":::

Her simülasyonda saldırı senaryosunun ayrıntılı bir açıklaması ve kullanılan MITRE saldırı teknikleri ve çalıştırdığınız örnek Gelişmiş tehdit avcılığı sorguları gibi başvurular bulunur.

**Örnekler:**

:::image type="content" source="images/simulation-details-aiq.png" alt-text="Kalıcılık yöntemleri için simülasyon açıklaması ayrıntıları bölmesi örneği" lightbox="images/simulation-details-aiq.png":::

:::image type="content" source="images/simulation-details-sb.png" alt-text="APT29 için simülasyon açıklaması ayrıntıları" lightbox="images/simulation-details-sb.png":::

## <a name="evaluation-report"></a>Değerlendirme raporu

Laboratuvar raporları, cihazlarda gerçekleştirilen simülasyonların sonuçlarını özetler.

:::image type="content" source="images/eval-report.png" alt-text="Değerlendirme raporu" lightbox="images/eval-report.png":::

Bir bakışta şunları hızlıca görebilirsiniz:

- Tetiklenen olaylar
- Oluşturulan uyarılar
- Maruz kalma düzeyine ilişkin değerlendirmeler
- Gözlenen tehdit kategorileri
- Algılama kaynakları
- Otomatik araştırma

## <a name="provide-feedback"></a>Geri bildirim gönderin

Geri bildiriminiz, ortamınızı gelişmiş saldırılara karşı koruma konusunda daha iyi olmamıza yardımcı olur. Ürün özelliklerinden ve değerlendirme sonuçlarından deneyiminizi ve gösterimlerinizi paylaşın.

**Geri bildirim sağla'yı** seçerek düşüncelerinizi bize bildirin.

:::image type="content" source="images/send-us-feedback-eval-lab.png" alt-text="Geri bildirim sayfası" lightbox="images/send-us-feedback-eval-lab.png":::
