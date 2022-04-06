---
title: Uç Nokta için Microsoft Defender değerlendirme laboratuvarı
description: Daha fazla Uç Nokta için Microsoft Defender öğrenin, saldırı benzetimleri çalıştırın ve tehditleri nasıl önlemektedir, algılar ve düzelter.
keywords: Uç Nokta için Microsoft Defender, değerlendirme, laboratuvar, benzetim, windows 10, windows server 2019, değerlendirme laboratuvarı
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
ms.openlocfilehash: 2b4c1cd9c37921fbb54633c0fc1bf2e42d308081
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472891"
---
# <a name="microsoft-defender-for-endpoint-evaluation-lab"></a>Uç Nokta için Microsoft Defender değerlendirme laboratuvarı

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Kapsamlı bir güvenlik ürünü değerlendirmesini yapmak,  end-end saldırı benzetimi yapamadan önce karmaşık bir ortam ve cihaz yapılandırması gerektiren karmaşık bir işlem olabilir. Karmaşıklık düzeyine eklemek, benzetim etkinliklerinin, uyarıların ve sonuçların değerlendirme sırasında yansıtıldıklarını izlemenin en zorluğudur.

Uç Nokta için Microsoft Defender değerlendirme laboratuvarı, cihaz ve ortam yapılandırmasının karmaşıklıklarını ortadan kaldıracak şekilde tasarlanmıştır; böylelikle platformun özelliklerini değerlendirmeye, benzetimler çalıştırmaya ve önleme, algılama ve düzeltme özelliklerini iş üzerinde görmeye odaklanabilirsiniz.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUM]

Basitleştirilmiş ayarlama deneyimiyle, kendi test senaryolarınızı ve önceden yapılan benzetimleri çalıştırmaya odaklanarak, Uç Nokta için Defender'ın nasıl performans gösterirken nasıl performans gösterir.

Platformun otomatik soruşturmalar, gelişmiş arama ve tehdit analizi gibi güçlü özelliklerine tam erişim sağlar, böylece Uç Nokta için Defender'ın sunduğu kapsamlı koruma yığınını test edin.

En son işletim sistemi sürümlerinin ve doğru güvenlik bileşenlerinin yanı sıra Office 2019 Standard'ı yüklemek üzere önceden yapılandırılmış olarak gelen Windows 10, Windows 11, Windows Server 2019, Windows Server 2016 ve Linux (Ubuntu) cihazlarını ebilirsiniz.

Ayrıca tehdit tehditlerini de yükleyebilirsiniz. Portaldan çıkmanıza gerek kalmadan Uç Nokta için Defender özelliklerini test etmeye yardımcı olmak için, Uç Nokta için Defender sektör lideri tehdit platformları ile ortak bir şekilde çalışır.

Tercih ettiğiniz sonuçları yükleyin, değerlendirme laboratuvarı içinde senaryoları çalıştırın ve platformun nasıl performans ortaya çıkarın. Size hiçbir ekstra ücret ödemeden kolayca kullanılabilir. Ayrıca, benzetimler kataloğuna erişip bu benzetimler kataloğundan çalıştırabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

Değerlendirme laboratuvarına erişmek için [lisans gereksinimlerini karşılamanız](minimum-requirements.md#licensing-requirements) veya test Uç Nokta için Microsoft Defender deneme erişiminiz vardır.

Şunları yapmak için **Güvenlik ayarlarını yönetme izinlerine sahip** olmak gerekir:

- Laboratuvar oluşturma
- Cihaz oluşturma
- Parolayı sıfırlayın
- Benzetimler oluşturma

Rol tabanlı erişim denetimi (RBAC) etkinleştirdiyse ve en az bir makine grubu oluşturduysanız, kullanıcıların Tüm makine gruplarına erişimi olmalıdır.

Daha fazla bilgi için bkz [. Rol oluşturma ve yönetme](user-roles.md).

Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink)

## <a name="get-started-with-the-lab"></a>Kullanmaya başlayın laboratuvarla birlikte gönder

Menüden laboratuvara erişebilirsiniz. Gezinti menüsünde Değerlendirme ve Değerlendirme laboratuvarı **için > seçin**.

> [!NOTE]
>
> - Seçtiğiniz ortamın yapısına bağlı olarak, cihazlar etkinleştirme gününden itibaren belirtilen saat sayısı boyunca kullanılabilir.
> - Her ortam sınırlı bir test cihazı kümesiyle hazır olur. Sağlanan cihazları kullandınız ve sildikten sonra daha fazla cihaz için istekte bulundurabilirsiniz.
> - Ayda bir laboratuvar kaynakları talep edilebilir.

Zaten bir laboratuvarınız var mı? Yeni tehdit tehditlerini etkinleştiren ve etkin cihazlara sahip olduğundan emin olun.

## <a name="setup-the-evaluation-lab"></a>Değerlendirme laboratuvarının kurulumu

1. Gezinti bölmesinde Değerlendirme ve Değerlendirme & **laboratuvar'ı** \> **ve** ardından Kurulum **laboratuvarı'nı seçin**.

   :::image type="content" source="../../media/evaluationtutormenu.png" alt-text="Değerlendirme laboratuvarı karşılama sayfası" lightbox="../../media/evaluationtutormenu.png":::

2. Değerlendirme gereksinimlerinize bağlı olarak, daha uzun bir süre için daha az cihaza veya daha fazla cihaza sahip bir ortamı daha kısa bir süre için ayarlamayı seçebilirsiniz. Tercih ettiğiniz laboratuvar yapılandırmasını ve ardından Sonraki'yi **seçin**.

    :::image type="content" source="images/lab-creation-page.png" alt-text="Laboratuvar yapılandırma seçenekleri" lightbox="images/lab-creation-page.png":::

3. (İsteğe bağlı) Laboratuvara tehdit tehditlerini yüklemeyi seçebilirsiniz.

    :::image type="content" source="images/install-agent.png" alt-text="Yükleme aracısı sayfası" lightbox="images/install-agent.png":::

   > [!IMPORTANT]
   > İlk olarak hüküm ve bilgi paylaşım açıklamalarını kabul etmek ve buna izin sağlamak gerekir.

4. Kullanmak istediğiniz tehdit benzetimi temsilcisini seçin ve ayrıntılarınızı girin. Ayrıca, tehdit tehditlerini daha sonra yüklemek de seçebilirsiniz. Laboratuvar kurulumu sırasında tehdit benzetimi aracılarını yüklemeyi seçerseniz, bunları seçtiğiniz cihazlara rahatça yüklemenin avantajından yararlanabilirsiniz.

   :::image type="content" source="images/lab-setup-summary.png" alt-text="Özet sayfası" lightbox="images/lab-setup-summary.png":::

5. Özeti gözden geçirerek Kurulum **laboratuvarı'nı seçin**.

Laboratuvar kurulumu işlemi tamamlandıktan sonra cihazlar ekleyebilir ve benzetimler çalıştırabilirsiniz.

## <a name="add-devices"></a>Cihaz ekle

Ortamınıza bir cihaz eklerken, Uç Nokta için Defender bağlantı ayrıntılarına sahip iyi yapılandırılmış bir cihaz ayarlar. Windows 10, Windows 11, Windows Server 2019, Windows Server 2016 ve Linux (Ubuntu) abilirsiniz.

Cihaz, işletim sistemi ve Office 2019 Standard'ın yanı sıra Java, Python ve SysIntenals gibi diğer uygulamaların en güncel sürümüyle yapılandırılır.

Laboratuvar kurulumu sırasında tehdit tehditlerini eklemeyi seçtiysiniz, tüm cihazlara tehdit aracısı, eklemiş olduğunuz cihazlara yüklenir.

Cihaz, sizin tarafınıza hiçbir çaba gerek Windows önerilen güvenlik bileşenlerinin açık ve denetim modunda olduğu kiracınıza otomatik olarak eklenir.

Aşağıdaki güvenlik bileşenleri test cihazlarında önceden yapılandırılmıştır:

- [Saldırı yüzeyini azaltma](attack-surface-reduction.md)
- [İlk görüşte engelle](configure-block-at-first-sight-microsoft-defender-antivirus.md)
- [Denetimli klasör erişimi](controlled-folders.md)
- [Exploit protection](enable-exploit-protection.md)
- [Ağ koruması](network-protection.md)
- [İstenmeyen olabilecek uygulama algılama](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)
- [Bulut teslimi koruma](cloud-protection-microsoft-defender-antivirus.md)
- [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

> [!NOTE]
> Microsoft Defender Virüsten Koruma açık olur (denetim modunda değil). Bu Microsoft Defender Virüsten Koruma benzetiminizi çalıştırmanızı engellerse, benzetim yoluyla cihazda gerçek zamanlı korumayı Windows Güvenliği. Daha fazla bilgi için bkz [. Her zaman açık korumayı yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md).

Otomatik araştırma ayarları kiracı ayarlarına bağımlıdır. Varsayılan olarak yarı otomatik olarak yapılandırıldı. Daha fazla bilgi için bkz [. Otomatik soruşturmalara genel bakış](automated-investigations.md).

> [!NOTE]
> Test cihazlarıyla bağlantı RDP kullanılarak yapılır. Güvenlik duvarı ayarlarınızın RDP bağlantılarına izin olduğundan emin olun.

1. Panodan Cihaz **ekle'yi seçin**.

2. Eklemek istediğiniz cihaz türünü seçin. Windows 10, Windows 11 Server 2019, Windows, Windows Server 2016 ve Linux (Ubuntu) ile 3.5.

   :::image type="content" source="../../media/add-machine-optionsnew.png" alt-text="Cihaz seçenekleriyle laboratuvar kurulumu" lightbox="../../media/add-machine-optionsnew.png":::

   > [!NOTE]
   > Cihaz oluşturma işlemiyle ilgili bir sorun olursa bu size bildirilecek ve yeni bir istek göndermeniz gerekir. Cihaz oluşturma başarısız olursa, izin verilen genel kotada sayılmaz.

3. Bağlantı ayrıntıları görüntülenir. Cihazın **parolasını** kaydetmek için Kopyala'ya tıklayın.

   > [!NOTE]
   > Parola yalnızca bir kez görüntülenir. Daha sonra kullanmak üzere kaydetmeyi deneyin.

    :::image type="content" source="../../media/add-machine-eval-lab-new.png" alt-text="Bağlantı ayrıntılarıyla eklenen cihaz" lightbox="../../media/add-machine-eval-lab-new.png":::

4. Cihaz ayarlama başlar. Bu yaklaşık 30 dakika kadar sürebilir.

5. Cihazlar sekmesini seçerek test cihazlarının durumunu, risk ve pozlama düzeylerini ve kurulumların **durumunu** görebilirsiniz.

   :::image type="content" source="images/machines-tab.png" alt-text="Cihazlar sekmesi" lightbox="images/machines-tab.png":::
    

   > [!TIP]
   > SütunDaki **Bilgi durumu** sütununda bilgi simgesinin üzerine gelerek bir aracının yükleme durumunu öğrenebilirsiniz.


## <a name="request-for-more-devices"></a>Daha fazla cihaz için istekte olun

Mevcut tüm cihazlar kullanılıyor ve silindiğinde daha fazla cihaz için istekte bulundurabilirsiniz. Ayda bir laboratuvar kaynakları talep edilebilir.

1. Değerlendirme laboratuvarı panosundan Daha fazla cihaz **için istekte bulun'ı seçin**.

   :::image type="content" source="images/request-more-devices.png" alt-text="Daha fazla cihaz isteği seçeneği" lightbox="images/request-more-devices.png":::

2. Yapılandırmanızı seçin.
3. İsteği gönderin.

İstek başarıyla gönderildikten sonra yeşil bir onay başlığı ve son gönderimin tarihini alacaksınız.

İsteğinizin durumunu, birkaç **saat içinde** onaylanabilecek Kullanıcı Eylemleri sekmesinde bulabilirsiniz.

Onaylandıktan sonra, istenen cihazlar laboratuvara eklenecek ve daha fazla cihaz oluşturabilirsiniz.

> [!TIP]
> Laboratuvardan daha iyi şekilde emin olmak için benzetimler kitaplığımıza göz atabilirsiniz.

## <a name="simulate-attack-scenarios"></a>Saldırı senaryolarını benzetin

Bağlantı üzerinden kendi saldırı benzetimlerinizi çalıştırmak için test cihazlarını kullanın.

Saldırı senaryolarını benzetmek için şunları kullanılabilir:

- ["Do It Yourself" saldırı senaryoları](https://security.microsoft.com/tutorials/all)
- Tehdit tehdit

Yeni ortaya çıkan tehditlerle [ilgili raporları görüntülemek](advanced-hunting-overview.md) için [Gelişmiş arama'ya](threat-analytics.md) , verileri sorgulamak ve Tehdit Analizi'ne de sahip olmak için kullanabilirsiniz.

### <a name="do-it-yourself-attack-scenarios"></a>Do-it-yourself saldırı senaryoları

Önceden yapılmış bir benzetim arıyorsanız " [Do It Yourself" saldırı senaryolarımızı kullanabilirsiniz](https://security.microsoft.com/tutorials/all). Bu betikler güvenli, belgelenmiş ve kullanımı kolaydır. Bu senaryolar, Uç Nokta için Defender özelliklerini yansıtacak ve araştırma deneyimi boyunca size yol sunar.

> [!NOTE]
> Test cihazlarıyla bağlantı RDP kullanılarak yapılır. Güvenlik duvarı ayarlarınızın RDP bağlantılarına izin olduğundan emin olun.

1. Bağlan seçin ve saldırı benzetimini çalıştırarak cihazınıza **Bağlan**.

    :::image type="content" source="images/test-machine-table.png" alt-text="Test Bağlan için Mobil Cihaz düğmesi" lightbox="images/test-machine-table.png":::


   :::image type="content" source="images/remote-connection.png" alt-text="Uzak masaüstü bağlantısı ekranı" lightbox="images/remote-connection.png":::

    **Linux cihazları** için: Yerel bir SSH istemcisi ve sağlanan komutu kullan gerekir. 


    > [!NOTE]
    > İlk kurulum sırasında kayıtlı parolanın kopyası yoksa, menüden Parolayı sıfırla'yı seçerek **parolayı** sıfırlayabilirsiniz:
    >
    > :::image type="content" source="images/reset-password-test-machine.png" alt-text="Parolayı sıfırla seçeneği" lightbox="images/reset-password-test-machine.png":::
    >
    > Cihaz, durumunu "Parola sıfırlamayı yürütünecek" olarak değiştirir ve birkaç dakika içinde yeni parolanız da size sunulacaktır.

3. Cihaz oluşturma adımı sırasında görüntülenen parolayı girin.

   :::image type="content" source="images/enter-password.png" alt-text="Kimlik bilgilerini girmek için ekranınız" lightbox="images/enter-password.png":::

4. Cihazda Do-it-yourself saldırı benzetimlerini çalıştırın.

### <a name="threat-simulator-scenarios"></a>Tehdit senaryoları

Laboratuvar kurulumu sırasında desteklenen tehdit tehditlerinin herhangi birini yüklemenize izin verirse, yerleşik benzetimleri değerlendirme laboratuvar cihazları üzerinde çalıştırabilirsiniz.

Üçüncü taraf platformları kullanarak tehdit benzetimleri yapmak, laboratuvar ortamıyla sınırlı Uç Nokta için Microsoft Defender özellikleri değerlendirmenin iyi bir yoludur.

> [!NOTE]
>
> Benzetimler çalıştırmadan önce aşağıdaki gereksinimlerin karşı olduğundan emin olun:
>
> - Cihazlar değerlendirme laboratuvarına eklenmiştir
> - Tehdit laboratuvara yüklenmeleri gerekiyor

1. Portaldan Benzetim **oluştur'a seçin**.

2. Bir tehdit tehditi seçin.

   :::image type="content" source="images/select-simulator.png" alt-text="Tehdit seçimi" lightbox="images/select-simulator.png":::

3. Kullanılabilir benzetimlere göz atmak için bir benzetim seçin veya benzetim galerisine bakın.

    Benzetim galerisine şu ifadelerden edinebilirsiniz:
    - Benzetimler genel bakış **kutucuğunun veya**
    - Gezinti bölmesinden Değerlendirme ve öğreticiler **Benzetim** \> uygulama ve öğreticilerde **gezinerek** & benzetimler **kataloğu'na tıklayın**.

4. Benzetimi üzerinde çalıştırmak istediğiniz cihazları seçin.

5. Benzetim **oluştur'ı seçin**.

6. Benzetimler sekmesini seçerek bir benzetimin **ilerlemesini** görüntüleyin. Benzetim durumunu, etkin uyarıları ve diğer ayrıntıları görüntüleme.

   :::image type="content" source="images/simulations-tab.png" alt-text="Benzetimler sekmesi" lightbox="images/simulations-tab.png":::

Benzetimlerinizi çalıştırdikten sonra, laboratuvar ilerleme çubuğunda ilerlemenizi ve otomatik bir Uç Nokta için Microsoft Defender düzeltmeyi tetikleyen laboratuvar ilerleme **çubuğunu incelemenizi teşvikiyoruz**. Bu özellikle toplanan ve analiz edilen kanıtlara göz atabilirsiniz.

Zengin sorgu dili ve ham telemetri kullanarak gelişmiş arama yoluyla saldırı kanıtı için avına devam edin ve Tehdit çözümlemelerinde belgelenmiş dünya çapında tehditlere göz atabilirsiniz.

## <a name="simulation-gallery"></a>Benzetim galerisi

Uç Nokta için Microsoft Defender portalda platformun özelliklerini test etmek için size kullanışlı erişim vermek üzere çeşitli tehdit benzetim platformları ile ortak çalışmalar yaptı.

Menüden Benzetimler ve öğreticiler  **Benzetimler kataloğu'ne** \> gidip kullanılabilir **tüm benzetimleri**  izleyin.

Desteklenen üçüncü taraf tehdit benzetimi aracılarının listesi listelenir ve katalogda ayrıntılı açıklamaların yanı sıra belirli benzetim türleri sağlanır.

Herhangi bir benzetimi katalogdan kolayca çalıştırabilirsiniz.

:::image type="content" source="images/simulations-catalog.png" alt-text="Benzetimler kataloğu" lightbox="images/simulations-catalog.png":::

Her benzetim, saldırı senaryosuyla ilgili ayrıntılı bir açıklamaya ve kullanılan MITRE saldırı teknikleri ve çalıştırdınız Gelişmiş av sorgularına örnek başvurular gibi başvurularla birlikte gelir.

**Örnekler:**

:::image type="content" source="images/simulation-details-aiq.png" alt-text="Kalıcılık yöntemleri için benzetim açıklaması ayrıntılar bölmesi örneği" lightbox="images/simulation-details-aiq.png":::

:::image type="content" source="images/simulation-details-sb.png" alt-text="APT29 için benzetim açıklaması ayrıntıları" lightbox="images/simulation-details-sb.png":::

## <a name="evaluation-report"></a>Değerlendirme raporu

Laboratuvar raporları, cihazlar üzerinde yapılan benzetimlerin sonuçlarını özetler.

:::image type="content" source="images/eval-report.png" alt-text="Değerlendirme raporu" lightbox="images/eval-report.png":::

Bir bakışta şunları hızla görebilirsiniz:

- Tetiklenen olaylar
- Oluşturulan uyarılar
- Pozlama düzeyinde değerlendirmeler
- Tehdit kategorileri gözlendi
- Algılama kaynakları
- Otomatik soruşturmalar

## <a name="provide-feedback"></a>Geri bildirim gönderin

Geri bildiriminiz, ortamınızı gelişmiş saldırılardan koruma konusunda daha iyi bir yer alsak da bize yardımcı olur. Ürün özellikleri ve değerlendirme sonuçlarından deneyimlerinizi ve yeteneğinizi paylaşın.

Geri bildirim sağla'ya seçerek görüşlerinizi **bize bildirin**.

:::image type="content" source="images/send-us-feedback-eval-lab.png" alt-text="Geri bildirim sayfası" lightbox="images/send-us-feedback-eval-lab.png":::
