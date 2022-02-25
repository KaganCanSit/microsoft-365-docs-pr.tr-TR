---
title: Deneme Microsoft 365 Defender veya pilot ortamı için sütun sütunlarını yapılandırma
description: Deneme Microsoft 365 Defender veya pilot ortamınız için Office 365 için Microsoft Defender, Identity için Microsoft Defender, Microsoft Cloud App Security ve Uç Nokta için Microsoft Defender gibi sütun sütunlarını yapılandırabilirsiniz.
keywords: deneme Microsoft 365 Defender yapılandırma, Microsoft 365 Defender yapılandırma, pilot Microsoft 365 Defender yapılandırma, sütun Microsoft 365 Defender yapılandırma, Microsoft 365 Defender sütunlar
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: e50210f02d14be33c357517515d456318aac4bb6
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2021
ms.locfileid: "62959681"
---
# <a name="configure-microsoft-365-defender-pillars-for-your-trial-lab-or-pilot-environment"></a>Deneme Microsoft 365 Defender veya pilot ortamınız için sütun sütunlarını yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender


Deneme Microsoft 365 Defender pilot ortamı oluşturmak ve bu ortamı dağıtmak üç aşamalı bir işlemdir:

|[![Aşama 1: Hazırlama](../../media/phase-diagrams/prepare.png)](prepare-m365d-eval.md)<br/>[Aşama 1: Hazırlama](prepare-m365d-eval.md) |[![Aşama 2: Ayarlama](../../media/phase-diagrams/setup.png)](setup-m365deval.md)<br/>[Aşama 2: Ayarlama](setup-m365deval.md) |![Aşama 3: Ekleme](../../media/phase-diagrams/onboard.png)<br/>Aşama 3: Ekleme | [![Pilot'a geri dön](../../media/phase-diagrams/backtopilot.png)](m365d-pilot.md)<br/>[Pilot playbook'a geri dön](m365d-pilot.md) |
|--|--|--|--|
|| |*Buradasınız!* | |

Şu anda yapılandırma aşamasındayız.

Hazırlık, başarılı bir dağıtım için çok önemli. Bu makalede, Uç Nokta için Microsoft Defender'ı dağıtırken göz önünde bulundurabilirsiniz.

## <a name="microsoft-365-defender-pillars"></a>Microsoft 365 Defender sütunlar
Microsoft 365 Defender dört sütundan oluşur. Bir sütun zaten ağ kuruluş güvenliği için değer sağlaysa da, dört sütunlu sütunun etkinleştirilmesi Microsoft 365 Defender en fazla değeri verir.

![Image of_Microsoft 365 Defender çözümü, kullanıcılar için Microsoft Defender for Identity, for endpoints Microsoft Defender for Endpoint, for Cloud apps, Microsoft Cloud App Security, for data, Microsoft Defender for Office 365](../../media/mtp/m365pillars.png)

Bu bölüm, şunları yapılandırmak için sizi yönlendirecek:

- Office 365 için Microsoft Defender
- Kimlik için Microsoft Defender
- Microsoft Cloud App Security
- Uç Nokta için Microsoft Defender

## <a name="configure-microsoft-defender-for-office-365"></a>Windows için Microsoft Defender'ı Office 365

> [!NOTE]
> Defender for-Step'i zaten etkinleştirdiysem bu adımı Office 365.

Bu ayarlardan bazılarının belirlenmesine yardımcı Office 365 Gelişmiş Tehdit Koruması Önerilen Yapılandırma Çözümleyicisi *(ORCA)* adlı bir PowerShell Modülü vardır. Kiracınız içinde yönetici olarak çalıştırsanız, get-ORCAReport istenmeyen posta önleme, kimlik avı önleme ve diğer ileti olay ayarlarıyla ilgili bir değerlendirme oluşturmak için yardımcı olur. Bu modülü 'dan indirebilirsiniz https://www.powershellgallery.com/packages/ORCA/.

1. Güvenlik [ve uyumluluk Office 365'&](https://protection.office.com/homepage) >  **Threat managementPolicy'ye** >  **gidin**.

   ![Görüntü of_Office 365 Güvenlik & Uyumluluk Merkezi Tehdit yönetimi ilkesi sayfası](../../media/mtp-eval-32.png)

2. Kimlik **avı önleme'ye tıklayın**, **İlke adını** ve açıklamasını oluştur ve doldur'u seçin. **İleri**'ye tıklayın.

   ![Image of_Office 365 Security & Center anti-phishing policy page where you can name your policy](../../media/mtp-eval-33.png)

   > [!NOTE]
   > Daha fazla bilgi için Microsoft Defender'da Gelişmiş kimlik avıyla mücadele Office 365. Gelişmiş **Kimlik Avı Eşiği'ne** **2 - Saldırgan olarak değiştirme**.

3. Koşul **ekle açılan menüsüne** tıklayın ve alıcı etki alanı olarak etki alanlarınızı seçin. **İleri**'ye tıklayın.

   ![Image of_Office 365 Security & Center anti-phishing policy page where you can add a condition for its application](../../media/mtp-eval-34.png)

4. Ayarlarınızı gözden geçirebilirsiniz. Onaylamak **için Bu ilkeyi oluştur'a** tıklayın.

   ![Image of_Office 365 Security & Center anti-phishing policy page where you can review your settings and click the create this policy button](../../media/mtp-eval-35.png)

5. **Ekleri Kasa'i** seçin ve **AtP'yi SharePoint, OneDrive ve** Devre Microsoft Teams seçin.

   ![Image of_Office 365 Security & Center page where you can turn atp for SharePoint, OneDrive, and Microsoft Teams](../../media/mtp-eval-36.png)

6. Yeni bir güvenli ek ilkesi oluşturmak ve bunu etki alanlarınıza alıcı etki alanı olarak uygulamak için + simgesine tıklayın. **Kaydet**'e tıklayın.

   ![Yeni of_Office bir güvenli ek ilkesi & oluşturabilirsiniz. 365 Güvenlik ve Uyumluluk Merkezi sayfası görüntüsü](../../media/mtp-eval-37.png)

7. Ardından, Bağlantılar **Kasa seçin** ve ardından varsayılan ilkeyi düzenlemek için kalem simgesine tıklayın.

8. Kullanıcılar güvenli **bağlantılara tıklarken izleme** seçeneğinin seçili olmadığını ve diğer seçeneklerin seçili olduğundan emin olun. Ayrıntılar [Kasa Bağlantı ayarlarını değiştirme](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365) bağlantısına bakın. **Kaydet**'e tıklayın.

   ![Image of_Office 365 Security & Center page which shows that the option Do not track when users click safe is not selected](../../media/mtp-eval-38.png)

9. Ardından Kötü amaçlı **yazılımdan koruma ilkesi'ne** tıklayın, varsayılanı seçin ve kalem simgesini seçin.

10. Evet **Ayarlar i** tıklatın ve **Evet'i seçin ve Kötü Amaçlı Yazılım Algılama Yanıtı'yı** etkinleştirmek için **varsayılan bildirim metnini kullanın**. Ortak Ek **Türleri Filtresi'ne** tıklayın. **Kaydet**'e tıklayın.

    ![Image of_Office 365 Security & Compliance Center page which shows the malware detection response is turned with default notification and the common attachment types filter is turned on](../../media/mtp-eval-39.png)

11. Güvenlik [ve Office 365 Merkezi&](https://protection.office.com/homepage) **SearchAudit** >  >  **günlük aramalarına gidin** ve Denetimi açma.

    ![Denetim günlüğü of_Office açabilirsiniz & 365 Güvenlik ve Uyumluluk Merkezi sayfası görüntüsü](../../media/mtp-eval-40.png)

12. Sistem için Microsoft Defender'ı Office 365 için Microsoft Defender ile Uç Nokta için Microsoft Defender'ı tümleştirin. Office 365 [Güvenlik](https://protection.office.com/homepage) >  & Uyumluluk **MerkeziThreat** **managementExplorer'a** >  gidin ve ekranın sağ üst köşesindeki Uç Nokta Ayarlar için **Microsoft Defender'ı** seçin. Uç nokta bağlantısı için Defender iletişim kutusunda, Uç Nokta için **Bağlan Için Defender'ı açın**.

    ![Image of_Office 365 Security & Center page where you can turn Microsoft Defender for Endpoint connection on](../../media/mtp-eval-41.png)

## <a name="configure-microsoft-defender-for-identity"></a>Kimlik için Microsoft Defender'ı yapılandırma

> [!NOTE]
> Kimlik için Microsoft Defender'ı zaten etkinleştirdiysem bu adımı atla

1. Güvenlik [Merkezi'Microsoft 365 gidin ve](https://security.microsoft.com/info) > **KaynaklarMicrosoft** >  **Defender Kimlik'i seçin**.

   ![Kimlik of_Microsoft Microsoft Defender'ı açma seçeneğinin bulunduğu 365 Güvenlik Merkezi sayfası görüntü](../../media/mtp-eval-42.png)

2. Kimlik **için** Microsoft Defender sihirbazını başlatmak için Oluştur'a tıklayın.

   ![Image of_Microsoft Defender for Identity wizard page where you should click Create button](../../media/mtp-eval-43.png)

3. **Active Directory ormanınıza bağlanmak için Kullanıcı adı ve parola sağla'ya tıklayın**.

   ![Image of_Microsoft Defender for Identity welcome page](../../media/mtp-eval-44.png)

4. Active Directory şirket içi kimlik bilgilerinizi girin. Bu, Active Directory'ye okuma erişimi olan herhangi bir kullanıcı hesabı olabilir.

   ![Kimlik of_Microsoft koymak istediğiniz Kimlik Dizini hizmetleri için Defender'ın görüntüsü](../../media/mtp-eval-45.png)

5. Ardından Algılayıcı Kurulumunu **İndir ve dosyayı etki** alanı denetleyicinize aktar'ı seçin.

   ![Image of_Microsoft Defender for Identity page where you can select Download Algılayıcı Kurulumu](../../media/mtp-eval-46.png)

6. Kimlik Algılayıcısı Kurulumu için Microsoft Defender'ı çalıştırın ve sihirbazı takip edin.

   ![Image of_Microsoft Defender for Identity page where you should click next to follow the Microsoft Defender for Identity sensor wizard](../../media/mtp-eval-47.png)

7. Algılayıcı **dağıtım** türüne göre Sonraki'ye tıklayın.

   ![Image of_Microsoft Defender for Identity page where you should click next to go to next page](../../media/mtp-eval-48.png)

8. Erişim anahtarını kopyalayın çünkü Sihirbazın yanına girmeniz gerekir.

   ![Görüntü of_the algılayıcılar sayfası için bir sonraki Microsoft Defender Kimlik algılayıcısı kurulum sihirbazı sayfasında girmeniz gereken erişim anahtarını kopyalamanız gereken algılayıcılar sayfası görüntüsü](../../media/mtp-eval-49.png)

9. Erişim anahtarını Sihirbaz'a kopyalayın ve Yükle'ye **tıklayın**.

   ![Image of_Microsoft Defender for Identity sensor wizard page where you should provide the access key and then click the install button](../../media/mtp-eval-50.png)

10. Tebrikler, etki alanı denetleyicisinde Identity için Microsoft Defender'ı başarıyla yapılandırdınız.

    ![Image of_Microsoft Defender for Identity sensor wizard installation completion where you should click the finish button](../../media/mtp-eval-51.png)

11. Kimlik için [Microsoft Defender Ayarları bölümünün](https://go.microsoft.com/fwlink/?linkid=2040449) altında **Uç Nokta için **Microsoft Defender ** seçeneğini seçin ve ardından iki durumlu düğmeyi açabilirsiniz. **Kaydet**'e tıklayın.

    ![Image of_the the Microsoft Defender for Identity settings page where you should turn the Microsoft Defender for Endpoint toggle on](../../media/mtp-eval-52.png)

## <a name="configure-microsoft-cloud-app-security"></a>Microsoft Cloud App Security

> [!NOTE]
> Bu özelliği zaten etkinleştirdiysek bu adımı Microsoft Cloud App Security.

1. Güvenlik Merkezi [Microsoft 365 More Resources](https://security.microsoft.com/info) >  **Microsoft Cloud App Security** > **.**

   ![Görüntü of_Microsoft Microsoft Bulut Uygulaması kartını gördüğünüz ve aç düğmesine tıklamanız gereken 365 Güvenlik Merkezi sayfası](../../media/mtp-eval-53.png)

2. Kimlik için Microsoft Defender'ı tümleştirin bilgi isteminde Kimlik veri **tümleştirmesi için Microsoft Defender'ı Etkinleştir'i seçin**.

   ![Image of_the information prompt to integrate Microsoft Defender for Identity where you should select the Microsoft Defender for Identity data integration link](../../media/mtp-eval-54.png)

   > [!NOTE]
   > Bu istemi görmüyorsanız, bu Kimlik için Microsoft Defender veri tümleştirmenizin zaten etkinleştirilmiş olduğu anlamına gelir. Ancak emin değilseniz, onaylamak için IT Yöneticinize başvurun.

3. Kimlik Tümleştirme **Ayarlar** için **Microsoft Defender'ı açıp** Kaydet'e **tıklayın**.

   ![Image of_the settings page where you should turn on the Microsoft Defender for Identity integration toggle then click save](../../media/mtp-eval-55.png)

   > [!NOTE]
   > Yeni Identity örnekleri için Microsoft Defender'da bu tümleştirme iki durumlu düğme otomatik olarak açılır. Bir sonraki adıma devammeden önce Kimlik için Microsoft Defender tümleştirmenizin etkinleştirildiğinden emin olun.

4. Bulut bulma ayarları altında Uç nokta **tümleştirmesi için Microsoft Defender'ı seçin** ve tümleştirmeyi etkinleştirin. **Kaydet**'e tıklayın.

   ![Image of_the Defender for Endpoint page where the block unsanctioned apps onay kutusunun under Microsoft Defender for Endpoint integration is selected. Kaydet'e tıklayın.](../../media/mtp-eval-56.png)

5. Bulut bulma ayarları'nın altında Kullanıcı **zenginleştirme'yi** seçin ve sonra verilerle tümleştirmeyi Azure Active Directory.

   ![Zenginleştirme bulunan kullanıcı tanımlayıcılarının kullanıcı adları onay kutusunun seçili Azure Active Directory zenginleştirme bölümünün resmi](../../media/mtp-eval-57.png)

## <a name="configure-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'ı yapılandırma

> [!NOTE]
> Uç Nokta için Microsoft Defender'ı zaten etkinleştirdiysem bu adımı atlayabilirsiniz.

1. Güvenlik Merkezi [Microsoft 365 More Resources](https://security.microsoft.com/info) >  **Microsoft Defender Güvenlik Merkezi** > **.** **Aç'a tıklayın**.

   ![Güvenlik of_Microsoft sayfasındaki Defender Güvenlik Merkezi Microsoft 365 görüntüsü](../../media/mtp-eval-58.png)

2. Uç Nokta için Microsoft Defender sihirbazını izleyin. **İleri**'ye tıklayın.

   ![Resim of_the Microsoft Defender Güvenlik Merkezi hoş geldiniz sihirbazı sayfası](../../media/mtp-eval-59.png)

3. Tercih ettiğiniz veri depolama konumu, veri bekletme ilkesi, kuruluş boyutu ve önizleme özellikleri için kabul edin.

   ![Veri of_the, bekletme ilkenizi ve kuruluş boyutunu seçmek için resim sayfası. Seçmeyi bitirerek sonraki seçeneğine tıklayın.](../../media/mtp-eval-60.png)

   > [!NOTE]
   > Daha sonra veri depolama konumu gibi bazı ayarları değiştiremezsiniz.

   **İleri**'ye tıklayın.

4. **Devam'a** tıklayın; Uç nokta kiracısı için Microsoft Defender'nızı sağlar.

   ![Bulut of_the için devam düğmesine tıklamanızı istemiyle bir sayfa görüntüsü](../../media/mtp-eval-61.png)

5. Grup İlkeleri aracılığıyla veya Microsoft Endpoint Manager için Microsoft Defender'da yerel bir betik çalıştırarak uç noktalarınızı ekleme. Basitlik açısından, bu kılavuz yerel betiği kullanır.

6. Paketi **indir'e** tıklayın ve ekleme betiği uç noktalarınıza kopyalayın.

   ![Ekleme of_page yükleme betiğini uç noktanıza veya uç noktalarınıza kopyalamak için Paket indir düğmesine tıklamanızı istemiyle ilgili görüntü](../../media/mtp-eval-62.png)

7. Uç noktanız üzerinde, ekleme betiği yönetici olarak çalıştırın ve Y'yi seçin.

   ![Ekleme of_the ve devam etmek için Y'yi seçtiğiniz komut satırı görüntüsü](../../media/mtp-eval-63.png)

8. Tebrikler, ilk uç noktanızı sizin için kullandınız.

   ![Resim of_the, ilk uç noktanızı var olduğunu onayını alan komut satırı görüntüsü. Devam etmek için herhangi bir tuşa basın](../../media/mtp-eval-64.png)

9. Algılama sınamalarını Uç nokta için Microsoft Defender sihirbazından kopyalayıp yapıştırın.

   ![Görüntü of_the komut istemine yapıştırmanız gereken algılama sınama betiği kopyalamak için Kopyala'ya tıklamanız gereken bir algılama testi adımı çalıştırması](../../media/mtp-eval-65.png)

10. PowerShell betiği yükseltilmiş bir komut istemine kopyalayın ve çalıştırın.

    ![PowerShell of_command yükseltilmiş bir komut istemine kopyalamanız ve çalıştırmanız gereken komut istemine resim görüntüsü](../../media/mtp-eval-66.png)

11. **Sihirbazdan Uç Nokta için Microsoft Defender'ı Kullanmaya** Başla'ya tıklayın.

    ![Uç of_the için Microsoft Defender'ı kullanmaya başla'ya tıklamanız gereken sihirbazdan gelen resim ve onay istemi](../../media/mtp-eval-67.png)

12. Ziyaret [Microsoft Defender Güvenlik Merkezi.](https://securitycenter.windows.com/) Gelişmiş **özellikler'Ayarlar** ve sonra da Gelişmiş **özellikler'i seçin**.

    ![Image of_Microsoft Defender Security Center Ayarlar menu where you should select Advanced features](../../media/mtp-eval-68.png)

13. Identity için **Microsoft Defender ile tümleştirmeyi açma**.

    ![Image of_Microsoft Defender Security Center Advanced features, Microsoft Defender for Identity option toggle that need to turn on](../../media/mtp-eval-69.png)

14. Tehdit İstihbaratı ile **Office 365 açma**.

    ![Image of_Microsoft Defender Security Center Advanced features, Office 365 Threat Intelligence option toggle that need to turn on](../../media/mtp-eval-70.png)

15. Microsoft Cloud App Security ile **tümleştirmeyi Microsoft Cloud App Security**.

    ![Image of_Microsoft Defender Security Center Advanced features, Microsoft Cloud App Security toggle that need to turn on](../../media/mtp-eval-71.png)

16. Yeni tümleştirmeleri onaylamak **için ekranı aşağı kaydırın** ve Kaydetme tercihleri'ne tıklayın.

    ![Resim of_Save tıklamanız gereken tercihler düğmesi](../../media/mtp-eval-72.png)

## <a name="start-the-microsoft-365-defender-service"></a>Microsoft 365 Defender hizmetini başlatma

> [!NOTE]
> 1 Haziran 2020'den başlayarak, Microsoft tüm uygun Microsoft 365 Defender kiracılara uygulama özelliklerini otomatik olarak sağlar. Ayrıntılar için [lisans Community ile ilgili bu Microsoft Tech teknik makalesine](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/microsoft-threat-protection-will-automatically-turn-on-for/ba-p/1345426) bakın.

Güvenlik [Merkezi'Microsoft 365 gidin](https://security.microsoft.com/homepage). **Arama'ya Ayarlar** ve sonra **Seç'i Microsoft 365 Defender**.

![güvenlik of_Microsoft merkezi giriş sayfasından 365 Defender Microsoft 365 görüntü Ayarlar görüntüsü](../../media/mtp-eval-72b.png)

Daha kapsamlı bir kılavuz için bkz[. Kılavuzu Microsoft 365 Defender](m365d-enable.md).

Tebrikler! Deneme laboratuvarınızı veya pilot Microsoft 365 Defender ortamınızı yeni oluşturdunız! Artık yeni kullanıcı arabirimini Microsoft 365 Defender bilebilirsiniz! Aşağıdaki etkileşimli kılavuzda neler öğrenebilirsiniz Microsoft 365 Defender öğrenin ve her bir panoyu günlük güvenlik işlemi görevleriniz için nasıl kullanabileceğinizi öğrenin.

[Etkileşimli kılavuza göz atabilirsiniz](https://aka.ms/MTP-Interactive-Guide)

Ardından bir saldırının benzetimini yapmak ve çapraz ürünün özelliklerini nasıl algılayanın, uyarı oluşturarak ve uç noktada dosyasız bir saldırıya otomatik olarak yanıt verebilirsiniz.

## <a name="next-step"></a>Sonraki adım

- [Test uyarısı oluşturma](generate-test-alert.md) - Test laboratuvarında bir saldırı benzetimi Microsoft 365 Defender çalıştırın.
