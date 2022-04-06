---
title: macOS'ta Uç Nokta için Microsoft Defender için el ile dağıtım
description: MacOS Uç Nokta için Microsoft Defender komut satırına el ile yükleme.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, yükleme, dağıtma, kaldırma, intune, jamf, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 7793a367b591490f3b70055bc5b437eec798cb28
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475993"
---
# <a name="manual-deployment-for-microsoft-defender-for-endpoint-on-macos"></a>macOS'ta Uç Nokta için Microsoft Defender için el ile dağıtım

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Bu konu başlığında, MacOS'ta Uç Nokta için Microsoft Defender el ile dağıtımı açıklanmıştır. Başarılı bir dağıtım için aşağıdaki adımların tamamlanmasını gerekir:

- [Yükleme ve ekleme paketlerini indirme](#download-installation-and-onboarding-packages)
- [Uygulama yükleme (macOS 10.15)](#application-installation-macos-1015)
- [Uygulama yükleme (macOS 11 ve daha yeni sürümler)](#application-installation-macos-11-and-newer-versions)
- [İstemci yapılandırması](#client-configuration)

## <a name="prerequisites-and-system-requirements"></a>Önkoşullar ve sistem gereksinimleri

Başlamadan önce, geçerli yazılım sürümünün [önkoşullarının Uç Nokta için Microsoft Defender için macOS'ta](microsoft-defender-endpoint-mac.md) ana sürüm sayfasına bakın.

## <a name="download-installation-and-onboarding-packages"></a>Yükleme ve ekleme paketlerini indirme

Yükleme ve ekleme paketlerini portaldan Microsoft 365 Defender indirin:

1. Uygulama <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender,</a> Cihaz yönetimi **Ayarlar > Uç Noktaları'> Ekleme'> gidin**.
2. Sayfanın 1. Bölümünde, işletim sistemini **macOS** ve Dağıtım yöntemi olarak Yerel **betik olarak ayarlayın**.
3. Sayfanın 2. Bölümünde Yükleme paketini **indir'i seçin**. Wdav.pkg olarak yerel bir dizine kaydedin.
4. Sayfanın Bölüm 2'de, Ekleme paketini **indir'i seçin**. Dosyayı aynı WindowsDefenderATPOnboardingPackage.zip bir dizine kaydedin.

   :::image type="content" source="images/portal-onboarding-macos.png" alt-text="Yükleme ve ekleme paketlerini indirme seçenekleri" lightbox="images/portal-onboarding-macos.png":::

5. Komut isteminden, iki dosyanın olduğunu doğrulayın.

## <a name="application-installation-macos-1015"></a>Uygulama yükleme (macOS 10.15)

Bu işlemi tamamlamak için cihazda yönetici ayrıcalıklarına sahip olmanız gerekir.

1. Finder'da indirilen wdav.pkg'ye gidin ve bunu açın.

   :::image type="content" source="images/mdatp-28-appinstall.png" alt-text="Uygulamanın yüklemesi" lightbox="images/mdatp-28-appinstall.png":::

2. **Devam'ı** seçin, Lisans koşullarını kabul edin ve istendiğinde parolayı girin.

   :::image type="content" source="images/mdatp-29-appinstalllogin.png" alt-text="Uygulama yüklemesi" lightbox="images/mdatp-29-appinstalllogin.png":::

   > [!IMPORTANT]
   > Microsoft'tan bir sürücünün yüklenmesine izin vermeniz istenir ("Sistem Uzantısı Engellendi" veya "Yükleme engellendi" veya her ikisi birden). Sürücünün yüklenmeye izin verilmiyor olması gerekir.

     :::image type="content" source="images/mdatp-30-systemextension.png" alt-text="Uygulamanın yüklemesi" lightbox="images/mdatp-30-systemextension.png":::

3. Güvenlik **Tercihlerini Aç'ı veya** **Sistem Tercihlerini Aç'ı > gizlilik & seçin**. İzin **Ver'i seçin**:

   :::image type="content" source="images/mdatp-31-securityprivacysettings.png" alt-text="Güvenlik ve gizlilik penceresi" lightbox="images/mdatp-31-securityprivacysettings.png":::

   Yükleme devam eder.

   > [!CAUTION]
   > İzin Ver'i **seçerek yükleme** 5 dakika sonra devam eder. Uç Nokta için Microsoft Defender yüklenir, ancak gerçek zamanlı koruma gibi bazı özellikler devre dışı bırakılır. Bunun [nasıl çözülecek olduğu hakkında bilgi](mac-support-kext.md) için bkz. Çekirdek uzantısı sorunlarını giderme.

> [!NOTE]
> macOS, ilk yüklemeden sonra cihazı yeniden başlatmayı Uç Nokta için Microsoft Defender. Cihaz yeniden başlatana kadar gerçek zamanlı koruma kullanılamaz.

## <a name="application-installation-macos-11-and-newer-versions"></a>Uygulama yükleme (macOS 11 ve daha yeni sürümler)

Bu işlemi tamamlamak için cihazda yönetici ayrıcalıklarına sahip olmanız gerekir.

1. Finder'da indirilen wdav.pkg'ye gidin ve bunu açın.

   :::image type="content" source="images/monterey-install-1.png" alt-text="Uygulamanın yükleme işlemi" lightbox="images/monterey-install-1.png":::

2. **Devam'ı** seçin, Lisans koşullarını kabul edin ve istendiğinde parolayı girin.

3. Yükleme işleminin sonunda, ürün tarafından kullanılan sistem uzantılarının onaylaması için yükseltisiniz. Güvenlik **Tercihlerini Aç'ı seçin**.

   :::image type="content" source="images/monterey-install-2.png" alt-text="Sistem uzantısı onayı" lightbox="images/monterey-install-2.png":::

4. Güvenlik ve **Gizlilik & İzin** Ver'i **seçin**.

   :::image type="content" source="images/monterey-install-3.png" alt-text="Sistem uzantısı güvenlik tercihleri1" lightbox="images/monterey-install-3.png":::

5. Mac'te & ile dağıtılmış tüm sistem uzantıları için 3. Uç Nokta için Microsoft Defender 4. adımı yinelayın.

6. Uç Nokta Algılama ve Yanıt özellikleri kapsamında, Mac'Uç Nokta için Microsoft Defender, yuva trafiğini inceler ve bu bilgileri Microsoft 365 Defender raporlar. Ağ trafiğini filtrelemek için Uç Nokta için Microsoft Defender izni istendiğinde İzin Ver'i **seçin**.

   :::image type="content" source="images/monterey-install-4.png" alt-text="Sistem uzantısı güvenlik tercihleri2" lightbox="images/monterey-install-4.png":::

7. Sistem **Tercihleri Güvenlik** **&'yi** \> açın ve Gizlilik sekmesine gidin.  **Microsoft Defender ve Microsoft Defenders** Uç Nokta Güvenlik Uzantısına Tam **Disk** Erişimi **izni ver.**

   :::image type="content" source="images/monterey-install-5.png" alt-text="Tam disk erişimi" lightbox="images/monterey-install-5.png":::

## <a name="client-configuration"></a>İstemci yapılandırması

1. wdav.pkg ve MicrosoftDefenderATPOnboardingMacOs.py macOS üzerinde wdav.pkg Uç Nokta için Microsoft Defender cihaza kopyalayın.

    İstemci cihazı diğer cihazla org_id. *org_id özniteliğinin* boş olduğunu unutmayın.

    ```bash
    mdatp health --field org_id
    ```

2. Yapılandırma dosyasını yüklemek için Python betiği çalıştırın:

    ```bash
    /usr/bin/python MicrosoftDefenderATPOnboardingMacOs.py
    ```

3. Cihazın şimdi organizasyonuyla ilişkili olduğunu doğrulayın ve geçerli bir kuruluş kimliği rapor edin:

    ```bash
    mdatp health --field org_id
    ```

    Yükleme sonrasında, sağ üst köşede macOS durum çubuğunda Microsoft Defender simgesini gösterilir.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-icon-bar.png" alt-text="Durum çubuğundaki Microsoft Defender simgesi" lightbox="images/mdatp-icon-bar.png":::

## <a name="how-to-allow-full-disk-access"></a>Tam Disk Erişimine İzin Verme

> [!CAUTION]
> macOS 10.15 (Catalina) yeni güvenlik ve gizlilik iyileştirmeleri içerir. Bu sürümden başarak, uygulamalar varsayılan olarak açık izin alınmadan diskte bazı konumlara (Belgeler, İndirmeler, Masaüstü, vb.) erişemez. Bu iznin olmaması Uç Nokta için Microsoft Defender, cihazınızı tam olarak koruyamaz.

1. İzin vermek için, Sistem **Tercihleri Güvenlik ve** \> **Gizlilik &** \> **Tam Disk Erişimi'ne** \> açın. Değişiklik yapmak için kilit simgesine tıklayın (iletişim kutusunun en altı). Seç'Uç Nokta için Microsoft Defender.

2. Cihazın düzgün bir şekilde işe alımlı olduğunu ve hizmete rapor olduğunu doğrulamak için AV algılama testini çalıştırın. Yeni eklenen cihazda aşağıdaki adımları uygulayın:

    1. Gerçek zamanlı korumanın etkinleştirildiğinden emin olun (aşağıdaki komutun çalıştırması 1 sonucuyla açıklandı):

        ```bash
        mdatp health --field real_time_protection_enabled
        ```

    1. Terminal penceresi açın. Aşağıdaki komutu kopyalayıp yürütün:

        ```bash
        curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    1. Dosya Mac'te Uç Nokta için Defender tarafından karantinaya alınmış olmalıdır. Algılanan tüm tehditleri listeleyen aşağıdaki komutu kullanın:

        ```bash
        mdatp threat list
        ```

3. Cihazın düzgün EDR ve hizmete rapor olduğunu doğrulamak için bir kullanıcı algılama testi çalıştırın. Yeni eklenen cihazda aşağıdaki adımları uygulayın:

   1. Mac veya Safari için Microsoft Edge gibi tarayıcınızda.

   1. MDATP MacOS'u DIY.zip ve ayıkla'yı https://aka.ms/mdatpmacosdiy indirin.

      İstendiğinde:

      > "Yüklemeler" üzerinde indirmelere izin vermek mdatpclientanalyzer.blob.core.windows.net?<br/>
      > Web Sitesi Tercihleri'ne göre dosya indiren web sitelerini değiştirebilirsiniz.

4. İzin **Ver'e tıklayın**.

5. **İndirilenler'i açın**.

6. **MDATP MacOS DIY görüyor olması gerekir**.

   > [!TIP]
   > Çift tıklarsanız aşağıdaki iletiyi alırsınız:
   >
   > > **"MDATP MacOS DIY" geliştirici doğrulayıcı olamaz, çünkü açılamıyor.**<br/>
   > > macOS, bu uygulamanın kötü amaçlı yazılımdan ücretsiz olduğunu doğrulayamaz.<br/>
   > > **\[Çöp Kutusu İptal'e\]** **\[Taşı\]**

7. **İptal'e tıklayın**.

8. **MDATP MacOS DIY'ye sağ tıklayın ve** ardından Aç'a **tıklayın**.

    Sistem aşağıdaki iletiyi görüntülemeli:

    > **macOS, MDATP MacOS DIY geliştiricisini doğrulayamaz. Açmak istediğinizden emin misiniz?**<br/>
    > Bu uygulamayı açarak, bilgisayarınızı ve kişisel bilgilerinizi Mac'inize zarar verecek veya gizliliğinizin tehlikeye atabilecek kötü amaçlı yazılımlara maruz açabilecek sistem güvenliğini geçersiz kılınır.

9. **Aç'a tıklayın**.

    Sistem aşağıdaki iletiyi görüntülemeli:

    > Uç Nokta için Microsoft Defender - macOS EDR DIY test dosyası<br/>
    > buna karşılık gelen uyarı MDATP portalında kullanılabilir.

10. **Aç'a tıklayın**.

    Birkaç dakika içinde "macOS Test Uyarısı" EDR uyarı yükseltilemektedir.

11. Portala Microsoft 365 Defender gidin (https://security.microsoft.com/).

12. Uyarı Sırasına gidin.

    :::image type="content" source="images/b8db76c2-c368-49ad-970f-dcb87534d9be.png" alt-text="Önem derecesini EDR, kategoriyi, algılama kaynağını ve daraltılmış eylem menüsünü gösteren bir macOS test uyarısı" lightbox="images/b8db76c2-c368-49ad-970f-dcb87534d9be.png":::

    Uyarı ayrıntılarına ve cihaz zaman çizelgesine bakın ve normal soruşturma adımlarını gerçekleştirin.

## <a name="logging-installation-issues"></a>Günlüğe kaydetme yükleme sorunları

Bir [hata oluştuğunda](mac-resources.md#logging-installation-issues) yükleyici tarafından oluşturulan otomatik günlüğü bulma hakkında daha fazla bilgi için bkz. Günlük yükleme sorunları.

## <a name="uninstallation"></a>Kaldırma

İstemci [cihazlarından](mac-resources.md#uninstalling) macOS'ta Uç Nokta için Microsoft Defender hakkında ayrıntılar için bkz. Kaldırma.
