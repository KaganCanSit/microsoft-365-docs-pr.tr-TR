---
title: Microsoft Endpoint Manager kullanarak işe Microsoft Endpoint Manager
description: Microsoft Endpoint Manager kullanarak Uç Nokta için Microsoft Defender'a nasıl Microsoft Endpoint Manager
keywords: ekleme, yapılandırma, dağıtma, dağıtım, uç nokta yöneticisi, Uç nokta için Microsoft Defender, koleksiyon oluşturma, uç nokta algılama yanıtı, yeni nesil koruma, saldırı yüzeyini azaltma, microsoft uç nokta yöneticisi
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-scenario
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 0f1e9c88c003551ca74c76d6348465f52fdbd171
ms.sourcegitcommit: cde34d38bdfb6335b980f1c48c6b218da6a64bf8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2022
ms.locfileid: "63014094"
---
# <a name="onboarding-using-microsoft-endpoint-manager"></a>Microsoft Endpoint Manager kullanarak işe Microsoft Endpoint Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Bu makale, Dağıtım kılavuzunda yer almaktadır ve örnek bir ekleme yöntemi olarak hareket almaktadır.

Planlama [başlığında](deployment-strategy.md) , cihazları hizmete eklemeye için çeşitli yöntemler sağlanmıştır. Bu konu, bulut yerel mimarisini kapsar.

![Yerel bulut mimarisi görüntüsü.](images/cloud-native-architecture.png)
 *Ortam mimarisi diyagramı*

Uç Nokta için Defender çeşitli uç noktaların ve araçların onboarding'i destekler ama bu makale bunları desteklemez. Diğer desteklenen dağıtım araçları ve yöntemleri kullanılarak genel ekleme hakkında bilgi için bkz. [Eklemeye genel bakış](onboarding.md).

[Microsoft Endpoint Manager](/mem/endpoint-manager-overview), çeşitli hizmetleri bire bir veren bir çözüm platformudur. Bu, çeşitli [Microsoft Intune](/mem/intune/fundamentals/what-is-intune)

tabanlı cihaz yönetimi.

Bu konu başlığı, kullanıcıları şu konuda yönlendirmektedir:

- 1. Adım: ŞU cihazlarda yapılandırmaları atamak için Microsoft Endpoint Manager MEM) içinde bir grup oluşturarak cihazları hizmete ekleme
- 2. Adım: Defender'ı Uç Nokta özellikleri için yapılandırma Microsoft Endpoint Manager

Bu ekleme kılavuzu, bu kılavuzu kullanırken atılması gereken aşağıdaki temel Microsoft Endpoint Manager:

- [Hedef cihazları veya kullanıcıları tanımlama](#identify-target-devices-or-users)
  - Grup oluşturma Azure Active Directory (Kullanıcı veya Cihaz)
- [Yapılandırma Profili Oluşturma](#step-2-create-configuration-policies-to-configure-microsoft-defender-for-endpoint-capabilities)
  - Bu Microsoft Endpoint Manager, her özellik için ayrı bir ilke oluşturma konusunda size yol edeceğiz.

## <a name="resources"></a>Kaynaklar

Burada, sürecin kalan kalanı için size gereken bağlantılar ve ardından:

- [MEM portalı](https://aka.ms/memac)
- [Microsoft 365 Defender](https://security.microsoft.com)
- [Intune Güvenlik taban çizgisi](/mem/intune/protect/security-baseline-settings-defender-atp#microsoft-defender)

Çalışma hakkında daha fazla Microsoft Endpoint Manager için şu kaynaklara bakın:

- [Microsoft Endpoint Manager sayfası](/mem/)
- [Intune ve ConfigMgr'in yakınsamasıyla ilgili blog gönderisi](https://www.microsoft.com/microsoft-365/blog/2019/11/04/use-the-power-of-cloud-intelligence-to-simplify-and-accelerate-it-and-the-move-to-a-modern-workplace/)
- [MEM'ye giriş videosu](https://www.microsoft.com/microsoft-365/blog/2019/11/04/use-the-power-of-cloud-intelligence-to-simplify-and-accelerate-it-and-the-move-to-a-modern-workplace)

## <a name="step-1-onboard-devices-by-creating-a-group-in-mem-to-assign-configurations-on"></a>1. Adım: CIHAZLARı, ŞU cihazlarda yapılandırmaları atamak için MEM'de bir grup oluşturarak ekleme

### <a name="identify-target-devices-or-users"></a>Hedef cihazları veya kullanıcıları belirleme

Bu bölümde, yapılandırmalarınızı atamak için bir test grubu oluşturuz.

> [!NOTE]
> Intune, Azure Active Directory yönetmek için Azure AD) gruplarında çalışır. Intune yöneticisi olarak, grupları kuruluş ihtiyaçlarını karşılamak için kurebilirsiniz.
>
> Daha fazla bilgi için bkz [. Kullanıcıları ve cihazları düzenlemek için grup ekleme](/mem/intune/fundamentals/groups-add).

### <a name="create-a-group"></a>Grup oluşturma

1. MEM portalını açın.

2. Yeni **Grup > Gruplar'a açın**.

    > [!div class="mx-imgBorder"]
    > ![Portal1 Microsoft Endpoint Manager resmi.](images/66f724598d9c3319cba27f79dd4617a4.png)

3. Ayrıntıları girin ve yeni grup oluşturun.

    > [!div class="mx-imgBorder"]
    > ![Portal2 Microsoft Endpoint Manager resmi.](images/b1e0206d675ad07db218b63cd9b9abc3.png)

4. Test kullanıcınızı veya cihazınızı ekleyin.

5. Tüm gruplar **> altında** yeni grubunızı açın.

6. **Üyeler'i > Ekle'yi seçin**.

7. Test kullanıcınızı veya cihazınızı bulun ve seçin.

    > [!div class="mx-imgBorder"]
    > ![Portal3 Microsoft Endpoint Manager resmi.](images/149cbfdf221cdbde8159d0ab72644cd0.png)

8. Test grubunuz artık test etmek için bir üyeye sahip.

## <a name="step-2-create-configuration-policies-to-configure-microsoft-defender-for-endpoint-capabilities"></a>2. Adım: Uç nokta özellikleri için Microsoft Defender'ı yapılandırmak üzere yapılandırma ilkeleri oluşturma

Aşağıdaki bölümde bir dizi yapılandırma ilkeleri oluşturabilirsiniz.

İlk olarak, Uç Nokta için Defender'a hangi kullanıcı veya cihaz gruplarının yer olacağını seçmek için bir yapılandırma ilkesi vardır:

- [Uç nokta algılama ve yanıt](#endpoint-detection-and-response)

Ardından, farklı türde uç nokta güvenlik ilkeleri oluşturarak devam edersiniz:

- [Yeni nesil koruma](#next-generation-protection)
- [Saldırı yüzeyini azaltma](#attack-surface-reduction---attack-surface-reduction-rules)

### <a name="endpoint-detection-and-response"></a>Uç nokta algılama ve yanıt

1. MEM portalını açın.

2. Uç nokta **algılama ve > uç nokta güvenlik durumu'ne gidin**. Profil **Oluştur'a tıklayın**.

    > [!div class="mx-imgBorder"]
    > ![Portal4 Microsoft Endpoint Manager resmi.](images/58dcd48811147feb4ddc17212b7fe840.png)

3. Platform **altında, Oluştur Windows 10 da Profil - Uç nokta algılama ve yanıt > seçin**.

4. Bir ad ve açıklama girin, ardından Sonraki'yi  **seçin**.

    > [!div class="mx-imgBorder"]
    > ![Portal5'Microsoft Endpoint Manager resmi.](images/a5b2d23bdd50b160fef4afd25dda28d4.png)

5. Gerekli ayarları ve ardından Sonraki'yi  **seçin**.

    > [!div class="mx-imgBorder"]
    > ![Portal6'Microsoft Endpoint Manager resmi.](images/cea7e288b5d42a9baf1aef0754ade910.png)

    > [!NOTE]
    > Bu örnekte, uç nokta için Defender intune ile zaten tümleştirilmiş olarak bu otomatik doldurulmuştu. Tümleştirme hakkında daha fazla bilgi için bkz. [Intune'da Uç Nokta için Microsoft Defender'ı Etkinleştirme](/mem/intune/protect/advanced-threat-protection-configure#to-enable-microsoft-defender-atp).
    >
    > Aşağıdaki resim, Uç Nokta için Microsoft Defender Intune ile tümleşik DEĞIL olduğunda göreceğiz resmin bir örneğidir:
    >
    > ![Portal7'Microsoft Endpoint Manager resmi.](images/2466460812371ffae2d19a10c347d6f4.png)

6. Gerekirse kapsam etiketleri ekleyin ve ardından Sonraki'yi  **seçin**.

    > [!div class="mx-imgBorder"]
    > ![Portal8 Microsoft Endpoint Manager resmi.](images/ef844f52ec2c0d737ce793f68b5e8408.png)

7. Eklemek istediğiniz grupları seçin seçeneğine **tıklayarak test grubu ekleyin** ve ardından Sonraki'yi  **seçin**.

    > [!div class="mx-imgBorder"]
    > ![Portal9'Microsoft Endpoint Manager resmi.](images/fc3525e20752da026ec9f46ab4fec64f.png)

8. Gözden geçir ve kabul et, ardından Oluştur'a  **seçin**.

    > [!div class="mx-imgBorder"]
    > ![Portal10 Microsoft Endpoint Manager resmi.](images/289172dbd7bd34d55d24810d9d4d8158.png)

9. Tamamlanmış ilkenizi görüntüabilirsiniz.

    > [!div class="mx-imgBorder"]
    > ![Portal11 Microsoft Endpoint Manager görüntüsü.](images/5a568b6878be8243ea2b9d82d41ed297.png)

### <a name="next-generation-protection"></a>Yeni nesil koruma

1. MEM portalını açın.

2. Virüsten Koruma **ve İlke > Uç >'e gidin**.

    > [!div class="mx-imgBorder"]
    > ![Portal12 Microsoft Endpoint Manager görüntüsü.](images/6b728d6e0d71108d768e368b416ff8ba.png)

3. Platform **- Windows 10 ve Sonraki - Windows - Oluştur'Microsoft Defender Virüsten Koruma > seçin**.

4. Ad ve açıklama girin, ardından Sonraki'yi  **seçin**.

    > [!div class="mx-imgBorder"]
    > ![Portal13 Microsoft Endpoint Manager görüntüsü.](images/a7d738dd4509d65407b7d12beaa3e917.png)

5. Yapılandırma ayarları **sayfasında**: Sistem yapılandırması için Microsoft Defender Virüsten Koruma yapılandırmaları ayarlayın (Bulut Koruması, Dışlamalar, Real-Time ve Düzeltme).

    > [!div class="mx-imgBorder"]
    > ![Portal14 Microsoft Endpoint Manager resmi.](images/3840b1576d6f79a1d72eb14760ef5e8c.png)

6. Gerekirse kapsam etiketleri ekleyin ve ardından Sonraki'yi  **seçin**.

    > [!div class="mx-imgBorder"]
    > ![Portal15 Microsoft Endpoint Manager resmi.](images/2055e4f9b9141525c0eb681e7ba19381.png)

7. Dahil etmek istediğiniz grupları seçin, test grubunuza attay ın ardından Sonraki'yi  **seçin**.

    > [!div class="mx-imgBorder"]
    > ![Portal16 Microsoft Endpoint Manager resmi.](images/48318a51adee06bff3908e8ad4944dc9.png)

8. Gözden geçir ve oluştur'a ve ardından Oluştur'a  **seçin**.

    > [!div class="mx-imgBorder"]
    > ![Portal17 Microsoft Endpoint Manager resmi.](images/dfdadab79112d61bd3693d957084b0ec.png)

9. Oluşturduğunuz yapılandırma ilkesi buradadır.

    > [!div class="mx-imgBorder"]
    > ![Portal18 Microsoft Endpoint Manager resmi.](images/38180219e632d6e4ec7bd25a46398da8.png)

### <a name="attack-surface-reduction---attack-surface-reduction-rules"></a>Saldırı Yüzeyini Azaltma - Saldırı yüzeyini azaltma kuralları

1. MEM portalını açın.

2. Saldırı yüzeyini **azaltma hakkında > uç nokta güvenliğine gidin**.

3. İlke  **Oluştur'a seçin**.

4. Platform **- Uygulama Windows 10 - Profil - Saldırı yüzeyini azaltma kuralları'na ve Oluştur'> seçin**.

    > [!div class="mx-imgBorder"]
    > ![Portal19 Microsoft Endpoint Manager görüntüsü.](images/522d9bb4288dc9c1a957392b51384fdd.png)

5. Bir ad ve açıklama girin, ardından Sonraki'yi  **seçin**.

    > [!div class="mx-imgBorder"]
    > ![Portal20 Microsoft Endpoint Manager resmi.](images/a5a71fd73ec389f3cdce6d1a6bd1ff31.png)

6. Yapılandırma ayarları **sayfasında:** Saldırı yüzeyini azaltma kuralları için gereken yapılandırmaları ayarlayın ve ardından Sonraki'yi  **seçin**.

    > [!NOTE]
    > Saldırı yüzeyini azaltma kurallarının hepsini Denetim'e göre yapılandıracak şekilde yapılandır istiyoruz.
    >
    > Daha fazla bilgi için Saldırı [yüzeyini azaltma kuralları'ne bakın](attack-surface-reduction.md).

    > [!div class="mx-imgBorder"]
    > ![Portal21 Microsoft Endpoint Manager resmi.](images/dd0c00efe615a64a4a368f54257777d0.png)

7. Kapsam Etiketlerini gereken şekilde ekleyin ve ardından Sonraki'yi  **seçin**.

    > [!div class="mx-imgBorder"]
    > ![Portal22 Microsoft Endpoint Manager görüntüsü.](images/6daa8d347c98fe94a0d9c22797ff6f28.png)

8. Dahil etmek ve test grubuna atamak için grupları seçin, sonra da Sonraki'yi  **seçin**.

    > [!div class="mx-imgBorder"]
    > ![Portal23 Microsoft Endpoint Manager resmi.](images/45cefc8e4e474321b4d47b4626346597.png)

9. Ayrıntıları gözden geçirerek Oluştur'a  **tıklayın**.

    > [!div class="mx-imgBorder"]
    > ![Portal24 Microsoft Endpoint Manager resmi.](images/2c2e87c5fedc87eba17be0cdeffdb17f.png)

10. İlkeyi görüntüleme.

    > [!div class="mx-imgBorder"]
    > ![Portal25 Microsoft Endpoint Manager resmi.](images/7a631d17cc42500dacad4e995823ffef.png)

### <a name="attack-surface-reduction---web-protection"></a>Saldırı Yüzeyini Azaltma - Web Koruması

1. MEM portalını açın.

2. Saldırı yüzeyini **azaltma hakkında > uç nokta güvenliğine gidin**.

3. İlke  **Oluştur'a seçin**.

4. **Oluştur'Windows 10 - Web koruma ve daha > seçin**.

    > [!div class="mx-imgBorder"]
    > ![Portal26 Microsoft Endpoint Manager resmi.](images/cd7b5a1cbc16cc05f878cdc99ba4c27f.png)

5. Bir ad ve açıklama girin, ardından Sonraki'yi  **seçin**.

    > [!div class="mx-imgBorder"]
    > ![Portal27 Microsoft Endpoint Manager resmi.](images/5be573a60cd4fa56a86a6668b62dd808.png)

6. Yapılandırma ayarları **sayfasında:** Web Koruması için gereken yapılandırmaları ayarlayın ve ardından Sonraki'yi  **seçin**.

    > [!NOTE]
    > Web Korumasını Engelle olarak yapılandırıyoruz.
    >
    > Daha fazla bilgi için bkz. [Web Koruması](web-protection-overview.md).

    > [!div class="mx-imgBorder"]
    > ![Portal28 Microsoft Endpoint Manager resmi.](images/6104aa33a56fab750cf30ecabef9f5b6.png)

7. Sonraki **adımla, Gerektiğinde Kapsam > ekleyin**.

    > [!div class="mx-imgBorder"]
    > ![Portal29 Microsoft Endpoint Manager resmi.](images/6daa8d347c98fe94a0d9c22797ff6f28.png)

8. Grup **test etmek için ata'> seçin**.

    > [!div class="mx-imgBorder"]
    > ![Portal30 Microsoft Endpoint Manager resmi.](images/45cefc8e4e474321b4d47b4626346597.png)

9. Gözden Geçir **ve Oluştur'> seçin**.

    > [!div class="mx-imgBorder"]
    > ![Portal31 Microsoft Endpoint Manager resmi.](images/8ee0405f1a96c23d2eb6f737f11c1ae5.png)

10. İlkeyi görüntüleme.

    > [!div class="mx-imgBorder"]
    > ![Portal32 Microsoft Endpoint Manager görüntüsü.](images/e74f6f6c150d017a286e6ed3dffb7757.png)

## <a name="validate-configuration-settings"></a>Yapılandırma ayarlarını doğrulama

### <a name="confirm-policies-have-been-applied"></a>İlkelerin uygulandığını onaylama

Yapılandırma ilkesi atandıktan sonra, ilkenin geçerliksi biraz zaman alır.

Zamanlama hakkında bilgi için bkz [. Intune yapılandırma bilgileri](/mem/intune/configuration/device-profile-troubleshoot#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

Test cihazınıza yapılandırma ilkesi uygulandığını onaylamak için, her yapılandırma ilkesi için aşağıdaki işlemi izleyin.

1. MEM portalını açın ve yukarıdaki adımlarda gösterildiği gibi ilgili ilkeye gidin. Aşağıdaki örnek, yeni nesil koruma ayarlarını gösterir.

    > [!div class="mx-imgBorder"]
    > [![Portal33 Microsoft Endpoint Manager resmi.](images/43ab6aa74471ee2977e154a4a5ef2d39.png)](images/43ab6aa74471ee2977e154a4a5ef2d39.png#lightbox)

2. İlke **durumunu görüntülemek** için Yapılandırma İlkesi'ne tıklayın.

    > [!div class="mx-imgBorder"]
    > [![Portal34 Microsoft Endpoint Manager resmi.](images/55ecaca0e4a022f0e29d45aeed724e6c.png)](images/55ecaca0e4a022f0e29d45aeed724e6c.png#lightbox)

3. Durumu  **görmek için** Cihaz Durumu'mu seçin.

    > [!div class="mx-imgBorder"]
    > [![Portal35 Microsoft Endpoint Manager resmi.](images/18a50df62cc38749000dbfb48e9a4c9b.png)](images/18a50df62cc38749000dbfb48e9a4c9b.png#lightbox)

4. Durumu  **görmek için** Kullanıcı Durumu'mu seçin.

    > [!div class="mx-imgBorder"]
    > [![Portal36 Microsoft Endpoint Manager resmi.](images/4e965749ff71178af8873bc91f9fe525.png)](images/4e965749ff71178af8873bc91f9fe525.png#lightbox)

5. Durumu  **görmek için Ayar başına durum'ı** seçin.

    > [!TIP]
    > Bu görünüm, başka bir ilkeyle çakışan ayarları belirlemek için çok yararlıdır.

    > [!div class="mx-imgBorder"]
    > [![Portal37 Microsoft Endpoint Manager resmi.](images/42acc69d0128ed09804010bdbdf0a43c.png)](images/42acc69d0128ed09804010bdbdf0a43c.png#lightbox)

### <a name="confirm-endpoint-detection-and-response"></a>Onay uç noktada algılama ve yanıtlama

1. Yapılandırmayı uygulamadan önce, Endpoint Protection Için Defender başlat bağlı değil.

    > [!div class="mx-imgBorder"]
    > [![Hizmetler paneli1'in görüntüsü.](images/b418a232a12b3d0a65fc98248dbb0e31.png)](images/b418a232a12b3d0a65fc98248dbb0e31.png#lightbox)

2. Yapılandırma uygulandıktan sonra, Endpoint Protection için Defender başlatmalıdır.

    > [!div class="mx-imgBorder"]
    > [![Hizmetler paneli2'nin görüntüsü.](images/a621b699899f1b41db211170074ea59e.png)](images/a621b699899f1b41db211170074ea59e.png#lightbox)

3. Hizmetler cihazda çalışıyor olduktan sonra, bu cihazda Microsoft Defender Güvenlik Merkezi.

    > [!div class="mx-imgBorder"]
    > [![Resim Microsoft Defender Güvenlik Merkezi.](images/df0c64001b9219cfbd10f8f81a273190.png)](images/df0c64001b9219cfbd10f8f81a273190.png#lightbox)

### <a name="confirm-next-generation-protection"></a>Yeni nesil korumayı onayla

1. İlkeyi test cihazına uygulamadan önce, aşağıda gösterildiği gibi ayarları el ile yönetebilirsiniz.

    > [!div class="mx-imgBorder"]
    > ![Sayfa1 ayarlama resmi.](images/88efb4c3710493a53f2840c3eac3e3d3.png)

2. İlke uygulandıktan sonra, ayarları el ile yönetemelisiniz.

    > [!NOTE]
    > Aşağıdaki resimde **Buluta teslim edilen korumayı aç** **ve Gerçek zamanlı korumayı aç** yönetiliyor olarak gösterilmektedir.

    > [!div class="mx-imgBorder"]
    > ![Sayfa2'nin ayar görüntüsü.](images/9341428b2d3164ca63d7d4eaa5cff642.png)

### <a name="confirm-attack-surface-reduction---attack-surface-reduction-rules"></a>Saldırı Yüzeyini Azaltma - Saldırı yüzeyini azaltma kurallarını onaylayın

1. İlkeyi test cihazına uygulamadan önce, kalemle bir PowerShell Penceresi yazın `Get-MpPreference`.

2. Bu, içeriğiz yer vermeyen aşağıdaki satırlarla yanıt verir:

    > AttackSurfaceReductionOnlyExclusions:
    >
    > AttackSurfaceReductionRules_Actions:
    >
    > AttackSurfaceReductionRules_Ids:

    ![Komut satırı1'in görüntüsü.](images/cb0260d4b2636814e37eee427211fe71.png)

3. İlkeyi bir test cihazına uygulamadan sonra bir PowerShell Windows yazın`Get-MpPreference`.

4. Bu, aşağıda gösterildiği gibi içeriği olan aşağıdaki satırlarla yanıt vermektedir:

    ![Komut satırı 2'nin resmi.](images/619fb877791b1fc8bc7dfae1a579043d.png)

### <a name="confirm-attack-surface-reduction---web-protection"></a>Saldırı Yüzeyini Azaltma - Web Koruması

1. Test cihazında bir PowerShell Windows yazın`(Get-MpPreference).EnableNetworkProtection`.

2. Bu, aşağıda gösterildiği gibi 0 ile yanıt verir.

    ![Komut satırı 3'in resmi.](images/196a8e194ac99d84221f405d0f684f8c.png)

3. İlkeyi uygulamadan sonra bir PowerShell Windows açın ve yazın`(Get-MpPreference).EnableNetworkProtection`.

4. Bu, aşağıda gösterildiği gibi 1 ile yanıt verir.

    ![Komut satırı4'in resmi.](images/c06fa3bbc2f70d59dfe1e106cd9a4683.png)
