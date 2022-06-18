---
title: macOS üzerinde Uç Nokta için Microsoft Defender için el ile dağıtım
description: komut satırından Uç Nokta için Microsoft Defender macOS el ile yükleyin.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, installation, deploy, uninstallation, intune, jamf, macos, catalina, mojave, high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 68f91e4b8f789087aacea14b6b2a8a8b67262fd0
ms.sourcegitcommit: b0b1be67de8f40b199bb9b51eb3568e59377e93a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2022
ms.locfileid: "66159629"
---
# <a name="manual-deployment-for-microsoft-defender-for-endpoint-on-macos"></a>macOS üzerinde Uç Nokta için Microsoft Defender için el ile dağıtım

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink).

Bu konuda, Uç Nokta için Microsoft Defender macOS el ile nasıl dağıtılacağı açıklanmaktadır. Başarılı bir dağıtım için aşağıdaki adımların tümünün tamamlanması gerekir:

- [Yükleme ve ekleme paketlerini indirme](#download-installation-and-onboarding-packages)
- [Uygulama yüklemesi (macOS 10.15)](#application-installation-macos-1015)
- [Uygulama yüklemesi (macOS 11 ve daha yeni sürümler)](#application-installation-macos-11-and-newer-versions)
- [İstemci yapılandırması](#client-configuration)

## <a name="prerequisites-and-system-requirements"></a>Önkoşullar ve sistem gereksinimleri

Başlamadan önce, geçerli yazılım sürümü için önkoşulların ve sistem gereksinimlerinin açıklaması için [macOS sayfasındaki ana Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md) bakın.

## <a name="download-installation-and-onboarding-packages"></a>Yükleme ve ekleme paketlerini indirme

Yükleme ve ekleme paketlerini Microsoft 365 Defender portalından indirin:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalında</a> **Ayarlar > Uç Noktaları > Cihaz yönetimi > Ekleme'ye** gidin.
2. Sayfanın Bölüm 1'inde işletim sistemini **macOS** ve Dağıtım yöntemini **Yerel betik** olarak ayarlayın.
3. Sayfanın 2. Bölümünde **Yükleme paketini indir'i** seçin. Yerel bir dizine wdav.pkg olarak kaydedin.
4. Sayfanın 2. Bölümünde **Ekleme paketini indir'i** seçin. Aynı dizine WindowsDefenderATPOnboardingPackage.zip olarak kaydedin.

   :::image type="content" source="images/portal-onboarding-macos.png" alt-text="Yükleme ve ekleme paketlerini indirme seçenekleri" lightbox="images/portal-onboarding-macos.png":::

5. Komut isteminden iki dosyaya sahip olduğunuzu doğrulayın.

## <a name="application-installation-macos-1015"></a>Uygulama yüklemesi (macOS 10.15)

Bu işlemi tamamlamak için cihazda yönetici ayrıcalıklarına sahip olmanız gerekir.

1. Finder'da indirilen wdav.pkg'ye gidin ve açın.

   :::image type="content" source="images/mdatp-28-appinstall.png" alt-text="Uygulamanın yüklenmesi" lightbox="images/mdatp-28-appinstall.png":::

2. **Devam'ı** seçin, Lisans koşullarını kabul edin ve istendiğinde parolayı girin.

   :::image type="content" source="images/mdatp-29-appinstalllogin.png" alt-text="Uygulama yüklemesi" lightbox="images/mdatp-29-appinstalllogin.png":::

   > [!IMPORTANT]
   > Microsoft'tan bir sürücünün yüklenmesine izin vermeniz istenir ("Sistem Uzantısı Engellendi" veya "Yükleme beklemede" veya her ikisi de. Sürücünün yüklenmesine izin verilmelidir.

     :::image type="content" source="images/mdatp-30-systemextension.png" alt-text="Uygulamanın yüklemesi" lightbox="images/mdatp-30-systemextension.png":::

3. **Güvenlik & Gizlilik > Güvenlik Tercihlerini Aç'ı veya Sistem Tercihlerini Aç'ı** seçin. **İzin Ver'i** seçin:

   :::image type="content" source="images/mdatp-31-securityprivacysettings.png" alt-text="Güvenlik ve gizlilik penceresi" lightbox="images/mdatp-31-securityprivacysettings.png":::

   Yükleme devam eder.

   > [!CAUTION]
   > **İzin Ver'i** seçmezseniz yükleme 5 dakika sonra devam eder. Uç Nokta için Microsoft Defender yüklenir, ancak gerçek zamanlı koruma gibi bazı özellikler devre dışı bırakılır. Bunun nasıl çözüleceğini öğrenmek için bkz. [Çekirdek uzantısı sorunlarını giderme](mac-support-kext.md) .

> [!NOTE]
> macOS, Uç Nokta için Microsoft Defender ilk yüklemesinde cihazı yeniden başlatmayı isteyebilir. Cihaz yeniden başlatılana kadar gerçek zamanlı koruma kullanılamaz.

## <a name="application-installation-macos-11-and-newer-versions"></a>Uygulama yüklemesi (macOS 11 ve daha yeni sürümler)

Bu işlemi tamamlamak için cihazda yönetici ayrıcalıklarına sahip olmanız gerekir.

1. Finder'da indirilen wdav.pkg'ye gidin ve açın.

   :::image type="content" source="images/monterey-install-1.png" alt-text="Uygulama için yükleme işlemi" lightbox="images/monterey-install-1.png":::

2. **Devam'ı** seçin, Lisans koşullarını kabul edin ve istendiğinde parolayı girin.

3. Yükleme işleminin sonunda, ürün tarafından kullanılan sistem uzantılarını onaylayacak şekilde yükseltileceksiniz. **Güvenlik Tercihlerini Aç'ı** seçin.

   :::image type="content" source="images/monterey-install-2.png" alt-text="Sistem uzantısı onayı" lightbox="images/monterey-install-2.png":::

4. **Güvenlik & Gizlilik** penceresinde **İzin Ver'i** seçin.

   :::image type="content" source="images/monterey-install-3.png" alt-text="Sistem uzantısı güvenlik tercihleri1" lightbox="images/monterey-install-3.png":::

5. Mac'te Uç Nokta için Microsoft Defender ile dağıtılan tüm sistem uzantıları için 3. & 4. adımları yineleyin.

6. Mac'te Uç Nokta için Microsoft Defender Uç Nokta Algılama ve Yanıt özelliklerinin bir parçası olarak yuva trafiğini inceler ve bu bilgileri Microsoft 365 Defender portalına bildirir. Ağ trafiğini filtrelemek için Uç Nokta için Microsoft Defender izin vermeniz istendiğinde **İzin Ver'i** seçin.

   :::image type="content" source="images/monterey-install-4.png" alt-text="Sistem uzantısı güvenlik tercihleri2" lightbox="images/monterey-install-4.png":::

7. **Sistem Tercihleri** \> **Güvenliği & Gizlilik'i** açın ve **Gizlilik** sekmesine gidin. **Microsoft Defender ve Microsoft Defenders** **Endpoint Security Uzantısı'na** **Tam Disk Erişimi** izni verin.

   :::image type="content" source="images/monterey-install-5.png" alt-text="Tam disk erişimi" lightbox="images/monterey-install-5.png":::

## <a name="client-configuration"></a>İstemci yapılandırması

1. macOS Uç Nokta için Microsoft Defender dağıttığınız cihaza wdav.pkg ve MicrosoftDefenderATPOnboardingMacOs.sh kopyalayın.

    İstemci cihazı org_id ile ilişkili değildir. *org_id* özniteliğinin boş olduğunu unutmayın.

    ```bash
    mdatp health --field org_id
    ```

2. Yapılandırma dosyasını yüklemek için Bash betiğini çalıştırın:

    ```bash
    Sudo bash -x MicrosoftDefenderATPOnboardingMacOs.sh
    ```

3. Cihazın artık kuruluşunuzla ilişkilendirildiğini ve geçerli bir kuruluş kimliği bildirdiğini doğrulayın:

    ```bash
    mdatp health --field org_id
    ```

    Yüklemeden sonra, sağ üst köşedeki macOS durum çubuğunda Microsoft Defender simgesini görürsünüz.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-icon-bar.png" alt-text="Durum çubuğundaki Microsoft Defender simgesi" lightbox="images/mdatp-icon-bar.png":::

## <a name="how-to-allow-full-disk-access"></a>Tam Disk Erişimine İzin Verme

> [!CAUTION]
> macOS 10.15 (Catalina) yeni güvenlik ve gizlilik geliştirmeleri içerir. Bu sürümden başlayarak, uygulamalar varsayılan olarak açık onay olmadan disk üzerindeki belirli konumlara (Belgeler, İndirmeler, Masaüstü vb.) erişemez. Bu onay olmadığında, Uç Nokta için Microsoft Defender cihazınızı tam olarak koruyamaz.

1. Onay vermek için **Sistem Tercihleri** \> **Güvenliği & Gizlilik** \> **Gizliliği** \> **Tam Disk Erişimi'ni** açın. Değişiklik yapmak için kilit simgesine tıklayın (iletişim kutusunun en altında). Uç Nokta için Microsoft Defender'ı seçin.

2. Cihazın düzgün şekilde eklendiğini ve hizmete bildirildiğini doğrulamak için bir AV algılama testi çalıştırın. Yeni eklenen cihazda aşağıdaki adımları gerçekleştirin:

    1. Gerçek zamanlı korumanın etkinleştirildiğinden emin olun (aşağıdaki komutu çalıştırmanın 1 sonucuyla belirtilir):

        ```bash
        mdatp health --field real_time_protection_enabled
        ```

    1. Terminal penceresi açın. Aşağıdaki komutu kopyalayın ve yürütin:

        ```bash
        curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    1. Dosya Mac'te Uç Nokta için Defender tarafından karantinaya alınmış olmalıdır. Algılanan tüm tehditleri listelemek için aşağıdaki komutu kullanın:

        ```bash
        mdatp threat list
        ```

3. Cihazın düzgün şekilde eklendiğini ve hizmete bildirildiğini doğrulamak için bir EDR algılama testi çalıştırın. Yeni eklenen cihazda aşağıdaki adımları gerçekleştirin:

   1. Mac veya Safari için Microsoft Edge gibi tarayıcınızda.

   1. MDATP MacOS DIY.zip indirip https://aka.ms/mdatpmacosdiy ayıklayın.

      Sizden istenebilir:

      > "mdatpclientanalyzer.blob.core.windows.net" üzerindeki indirmelere izin vermek istiyor musunuz?<br/>
      > Web Siteleri Tercihleri'nde hangi web sitelerinin dosya indirebileceğini değiştirebilirsiniz.

4. **İzin Ver'e** tıklayın.

5. **İndirmeler'i** açın.

6. **MDATP MacOS DIY'i** görmeniz gerekir.

   > [!TIP]
   > Çift tıklarsanız aşağıdaki iletiyi alırsınız:
   >
   > > **Geliştirici doğrulanamadığından "MDATP MacOS DIY" açılamıyor.**<br/>
   > > macOS bu uygulamanın kötü amaçlı yazılım içermediğini doğrulayamıyor.<br/>
   > > **\[Çöp Sepeti\]** **\[İptaline\]** Taşı

7. **İptal'e** tıklayın.

8. **MDATP MacOS DIY'ye** sağ tıklayın ve ardından **Aç'a** tıklayın.

    Sistem aşağıdaki iletiyi göstermelidir:

    > **macOS MDATP MacOS DIY geliştiricisini doğrulayamıyor. Açmak istediğinizden emin misiniz?**<br/>
    > Bu uygulamayı açarak, bilgisayarınızı ve kişisel bilgilerinizi Mac'inize zarar verebilecek veya gizliliğinizi tehlikeye atabilecek kötü amaçlı yazılımlara maruz bırakabilecek sistem güvenliğini geçersiz kılacaksınız.

9. **Aç'a** tıklayın.

    Sistem aşağıdaki iletiyi göstermelidir:

    > Uç Nokta için Microsoft Defender - macOS EDR DIY test dosyası<br/>
    > İlgili uyarı MDATP portalında kullanılabilir.

10. **Aç'a** tıklayın.

    Birkaç dakika içinde "macOS EDR Test Uyarısı" adlı bir uyarı tetiklenmelidir.

11. Microsoft 365 Defender portalına (https://security.microsoft.com/) gidin.

12. Uyarı Kuyruğu'na gidin.

    :::image type="content" source="images/b8db76c2-c368-49ad-970f-dcb87534d9be.png" alt-text="Önem derecesini, kategoriyi, algılama kaynağını ve daraltılmış eylemler menüsünü gösteren bir macOS EDR test uyarısı" lightbox="images/b8db76c2-c368-49ad-970f-dcb87534d9be.png":::

    Uyarı ayrıntılarına ve cihaz zaman çizelgesine bakın ve normal araştırma adımlarını gerçekleştirin.

## <a name="logging-installation-issues"></a>Yükleme sorunlarını günlüğe kaydetme

Bir hata oluştuğunda yükleyici tarafından oluşturulan otomatik olarak oluşturulan günlüğü bulma hakkında daha fazla bilgi için bkz [. Yükleme sorunlarını günlüğe](mac-resources.md#logging-installation-issues) kaydetme.

## <a name="uninstallation"></a>Kaldırma

İstemci cihazlarından macOS Uç Nokta için Microsoft Defender kaldırma hakkında ayrıntılı bilgi için bkz. [Kaldırma](mac-resources.md#uninstalling).
