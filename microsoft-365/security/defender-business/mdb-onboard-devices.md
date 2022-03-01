---
title: Cihazları İş için Microsoft Defender'a ekleme (önizleme)
description: İş için Microsoft Defender'da (önizleme) cihaz ekleme seçenekleri hakkında bilgi
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/16/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 073478300e6b5a9d5a9fc10e634f6e3113897fb3
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2022
ms.locfileid: "63015342"
---
# <a name="onboard-devices-to-microsoft-defender-for-business-preview"></a>Cihazları İş için Microsoft Defender'a ekleme (önizleme)

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](mdb-tutorials.md#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

Defender for Business'daki cihaz ekleme deneyimi, Uç Nokta için Microsoft Defender'da kullanılan cihaz ekleme işlemleriyle aynıdır. Nasıl çalıştığını görmek için aşağıdaki videoyu izleyin:<br/><br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

İş için Microsoft Defender (önizleme) ile, kuruluş cihazlarınızı eklemeye yardımcı olmak için çeşitli seçenekleriniz vardır. Bu makale, seçenekleriniz üzerinde size yol sunar ve eklemenin nasıl çalıştığını genel bir bakış sunar.

> [!TIP]
> Uç nokta için Defender'da cihaz ekleme hakkında daha ayrıntılı bilgi görüntülemek için bkz. Cihazları ekleme ve Uç nokta özellikleri için [Microsoft Defender'ı yapılandırma](../defender-endpoint/onboard-configure.md).

## <a name="what-to-do"></a>Ne yapmalı?

1. Ekleme cihazları için [seçeneklerinize bakın](#device-onboarding-methods).

2. Aşağıdaki yöntemlerden birini kullanarak bir cihaz ekleme:
    - [Microsoft Endpoint Manager'a Windows cihazlar için otomatik Microsoft Endpoint Manager](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager)
    - [Windows, macOS ve Linux cihazları için yerel bir betik](#onboard-devices-using-a-local-script-in-defender-for-business)
    - [Microsoft Endpoint Manager, tabletler ve telefonlar için cihazlar](#onboard-devices-using-microsoft-endpoint-manager)
    - [Mobil cihazlar için Windows İlkesi](#onboard-windows-devices-using-group-policy)
    - [Burada listelenmiyor başka bir yöntem](#onboard-devices-using-a-method-not-listed-here)

3. [Yeni eklenen cihazlar için](#run-a-detection-test) bir algılama Windows çalıştırın.

4. [Sonraki adımlarınıza bakın](#next-steps). 

Bu makalede cihaz çıkarma [hakkında da bilgi bulabilirsiniz](#offboarding-a-device).

## <a name="device-onboarding-methods"></a>Cihaz ekleme yöntemleri

Aşağıdaki tabloda, İş için Defender'a cihazları eklemede en sık kullanılan yöntemler açık almaktadır. 

| Ekleme yöntemi  | Açıklama  |
|---------|---------|
| **Otomatik katılım**<br/>(*zaten Microsoft Endpoint Manager kullanan müşteriler tarafından kullanılabilir*) | Otomatik ekleme, defender for Business (önizleme) ile Microsoft Endpoint Manager arasındaki bağlantıyı ayarlar ve ardından Defender for Business (önizleme) Windows cihazlarıyla birlikte alır. Cihazlar cihaz zaten mobil cihaza Endpoint Manager.<br/><br/>Daha fazla bilgi edinmek için [bkz. Windows cihazlarında otomatik Microsoft Endpoint Manager](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager). |
| **Yerel betik**<br/>(*Önizleme sırasında önerilir; bir defada birkaç cihaza ekleme için yararlıdır*)  | Bilgisayarlarla, MacOS veya Linux cihazlarında indirerek ve bu cihazlarda çalıştırarak Defender for Business (önizleme) Windows edinebilirsiniz. Betik, otomatik bağlantı Azure Active Directory bir güven ayarlar ve cihazı kaydeder.<br/><br/>Bu yöntemi kullanmak için bkz. [İş için Defender'da yerel bir betik kullanarak cihazları ekleme](#onboard-devices-using-a-local-script-in-defender-for-business). |
| **Microsoft Intune** veya **Microsoft Endpoint Manager**<br/>(*zaten Microsoft Intune veya Endpoint Manager*) | [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) Mobil [Cihaz Yönetimi de](/mem/intune/enrollment/device-enrollment) mobil cihaz yönetiminin Endpoint Manager. İş için Defender'ı (Endpoint Manager) başlamadan önce zaten Endpoint Manager kullanıyorsanız cihazları eklemeye ve yönetmeye devam etmek için Endpoint Manager'i kullanmaya devam edin<br/><br/>Bu yöntemi kullanmak için bkz. [Cihaz ekleme ve Microsoft Endpoint Manager](#onboard-devices-using-microsoft-endpoint-manager). |
| **Grup İlkesi** | Kuruluş zaten Grup İlkesi kullanıyorsa, GPOS oluşturabilir ve bunları İş için Defender'da (önizleme) kuruluşun cihazlarına uygulayabilirsiniz.<br/><br/>Bu yöntem hakkında daha fazla bilgi edinmek için bkz[. Grup İlkesi Windows cihaz ekleme](#onboard-windows-devices-using-group-policy). | 

> [!IMPORTANT]
> Bir sorun olursa ve ekleme işleminiz başarısız olursa bkz. [İş için Microsoft Defender sorun giderme](mdb-troubleshooting.yml).

## <a name="automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager"></a>Microsoft Endpoint Manager'a Windows cihazlar için otomatik Microsoft Endpoint Manager

Otomatik ekleme seçeneği yalnızca Windows için geçerlidir. Bu seçenek, iş için Defender (önizleme) almadan önce Microsoft Intune'de Microsoft Endpoint Manager, Microsoft Intune veya Mobil Cihaz Yönetimi'yi (MDM) kullanıyorsa ve zaten Windows cihazlarınız varsa kullanılabilir Endpoint Manager. 

cihaz Windows zaten Endpoint Manager, siz İş için Defender'ı ayarlama ve yapılandırma sürecindeyken, İş için Defender bu cihazları algılar. Windows cihazlarının hepsi veya bazısı için otomatik ekleme özelliğini kullanmak Windows soruldu. 

Otomatik ekleme işlemi, İş için Defender ile Endpoint Manager arasındaki bir bağlantı ayarlar ve cihazları İş için Defender'a ayarlar. Bir defada tüm kayıtlı cihaza Windows veya eklemek için bir dizi Windows seçebilirsiniz.

Daha fazla bilgi edinmek için, İş için [Microsoft Defender'ı (önizleme) ayarlamak üzere sihirbazı kullanma makalesinde 3. adıma bakın](mdb-use-wizard.md).

## <a name="onboard-devices-using-a-local-script-in-defender-for-business"></a>Defender for Business'da yerel bir betik kullanarak cihazları ekleme

İş için Defender'a yerel bir betik Windows MacOS ve Linux cihazlarıyla birlikte kullanabilirsiniz. Ekleme betiğini bir cihazda çalıştırsanız, Azure Active Directory ile bir güven oluşturur, cihazı Microsoft Endpoint Manager'a kaydettirebilir ve cihazı İş için Defender'a ekler. Bu yöntem, Defender for Business'daki cihaz ekleme ve bir defada birkaç cihazı ekleme için yararlıdır.

1. Microsoft 365 Defender portalına () gidin[https://security.microsoft.com](https://security.microsoft.com) ve oturum açın.

2. Gezinti bölmesinde Kullanıcı Uçları'Ayarlar  > **seçin** ve ardından Cihaz **yönetimi'nin altında Ekleme'yi** **seçin**.

3. **Windows 10 11** gibi bir işletim sistemi seçin ve ardından Cihaz ekleme'nin altındaki **Dağıtım** yöntemi bölümünde Yerel **betik'i seçin**. 

4. Ekleme **paketini indir'i seçin**. Ekleme paketini çıkarılabilir bir sürücüye kaydetmenizi öneririz.

5. Aşağıdaki makalelerde yer alan yönergeleri izleyin:

   - Windows cihazlar: [Yerel Windows kullanarak cihazları ekleme](../defender-endpoint/configure-endpoints-script.md#onboard-devices)
   - macOS cihazları: [macOS'ta Uç Nokta için Microsoft Defender için el ile dağıtım](../defender-endpoint/mac-install-manually.md#client-configuration)
   - Linux cihazları: [Linux'ta Uç Nokta için Microsoft Defender'ı el ile dağıtma](../defender-endpoint/linux-install-manually.md#client-configuration)

> [!IMPORTANT]
> Bir sorun olursa ve ekleme işleminiz başarısız olursa bkz. [İş için Microsoft Defender (önizleme) sorun giderme](mdb-troubleshooting.yml).

## <a name="onboard-devices-using-microsoft-endpoint-manager"></a>Mobil cihaz kullanarak cihazları Microsoft Endpoint Manager

İş için Defender'ı (önizleme Microsoft Intune almadan önce zaten Microsoft Intune kullanıyorsanız cihazları eklemeye devam edin. Uygulama Endpoint Manager bilgisayar, tablet ve telefon abilirsiniz. 

Bkz[. Microsoft Intune'de cihaz kaydı](/mem/intune/enrollment/device-enrollment).

## <a name="onboard-windows-devices-using-group-policy"></a>Grup Windows kullanarak diğer cihazları ekleme

[Grup İlkesi,](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831791(v=ws.11)) Grup İlkesi ayarları ve Grup İlkesi Tercihleri aracılığıyla kullanıcılar ve bilgisayarlar için yönetilen yapılandırmalar belirtmenizi sağlayan bir altyapıdır. Grup İlkesi nesnesi (GPO), Grup İlkesi kapsayıcısı ve Grup İlkesi şablonu oluşturan mantıksal bir nesnedir. 

Kuruluş, cihazları yönetmek için Grup İlkesi kullanıyorsa, Cihazları Defender for Business'a eklemeye yardımcı olmak için Grup İlkesi'ne kullanabilirsiniz. Grup İlkesi'ne yeniyseniz, bunun yerine grup kullanımı veya yerel betik Endpoint Manager başka bir yöntem kullanmanız önerilir. 

Grup [İlkesi Windows cihaz ekleme'ye bakın](../defender-endpoint/configure-endpoints-gp.md).

## <a name="onboard-devices-using-a-method-not-listed-here"></a>Burada listelenmiyor bir yöntem kullanarak cihazları ekleme

Cihazları işe almak için bu makalede listelenmiyor başka bir yöntem kullanmak için bkz. [Ekleme ve yapılandırma aracı seçenekleri](../defender-endpoint/onboard-configure.md#onboarding-and-configuration-tool-options).

## <a name="run-a-detection-test"></a>Algılama testi çalıştırma

Windows Defender for Business (önizleme) sürümüne cihaz Windows, her şeyin düzgün düzgün olduğundan emin olmak için bir algılama testi çalıştırabilirsiniz.

1. Windows bir klasör oluşturun: `C:\test-MDATP-test`.

2. Yönetici olarak Komut İstemi'ne açın.

3. Komut İstemi penceresinde aşağıdaki PowerShell komutunu çalıştırın:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Komut çalıştır edildikten sonra, Komut İstemi penceresi otomatik olarak kapanır. Başarılı olursa, algılama testi tamamlandı olarak işaretlenir ve yaklaşık 10 dakika içinde yeni eklenen cihaz için Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com)) yeni bir uyarı görüntülenir.

## <a name="gradual-device-onboarding"></a>Aşamalı cihaz ekleme

Kuruluş cihazlarınızı aşamalar içinde eklemeye devam etmek için şu adımları izleyin:

1. Ekleme için bir cihaz kümesi belirleme.

2. Microsoft 365 Defender portalına () gidin[https://security.microsoft.com](https://security.microsoft.com) ve oturum açın.

3. Gezinti bölmesinde Kullanıcı Uçları'Ayarlar  > **seçin** ve ardından Cihaz **yönetimi'nin altında Ekleme'yi** **seçin**.

4. Bir işletim sistemi (örneğin, **Windows 10 11)** seçin ve sonra bir ekleme yöntemi (Yerel betik gibi **) seçin**. Seçtiğiniz yöntem için sağlanan yönergeleri izleyin.

5. Eklemek istediğiniz her cihaz kümesi için bu işlemi yinelayın. 

> [!TIP]
> Cihazları her eklemeye aynı ekleme paketini kullanmak zorunda değildir. Örneğin, bazı cihazları yerel betik kullanarak kullanabilir ve daha sonra daha fazla cihaza sahip olmak için başka bir yöntem seçebilirsiniz.

## <a name="offboarding-a-device"></a>Cihaz çıkarma

Bir cihazla çıkarılacak şekilde yer almak için şu adımları izleyin:

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. Gezinti bölmesinde, Gezinti **Bölmesi'Ayarlar** uç **noktalar'ı seçin**.

3. Cihaz **yönetimi'nin** altında **Çıkar'ı seçin**.

4. **Windows 10 ve 11** gibi bir işletim sistemi seçin ve ardından Cihaz çıkar'ın altındaki Dağıtım yöntemi bölümünde Yerel **betik'i seçin**. 

5. Onay ekranında bilgileri gözden geçirin ve devam etmek için **İndir'i** seçin.

6. İndirme **paketi'ne tıklayın**. Çıkarılabilir paketi çıkarılabilir bir sürücüye kaydetmenizi öneririz.

7. Betiği, çıkaracakları her cihaza çalıştırın. 

   Bu görevle ilgili yardıma mı ihtiyacınız var? Aşağıdaki kaynaklara bakın:   

   - Windows için: [Yerel Windows kullanarak çıkar çıkar](../defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script)
   - macOS cihazları: [macOS'ta kaldırma](../defender-endpoint/mac-resources.md#uninstalling)
   - Linux cihazları: [Linux'ta kaldırma](../defender-endpoint/linux-resources.md#uninstall)

> [!IMPORTANT]
> Bir cihaz çıkar çıkarıldı; cihazlar, verilerin Defender for Business (önizleme) sürümüne gönderilmesini durdurur. Bununla birlikte, karalama öncesinde alınan veriler altı (6) aya kadar korunur.

## <a name="next-steps"></a>Sonraki adımlar

Şu şekilde devam edin:

- [5. Adım: İş için Microsoft Defender'da (önizleme) güvenlik ayarlarınızı ve ilkelerinizi yapılandırma](mdb-configure-security-settings.md)

- [İş için Microsoft Defender'ı (önizleme) kullanmaya başlama](mdb-get-started.md) 