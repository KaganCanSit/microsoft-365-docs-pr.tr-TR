---
title: Cihazları İş için Microsoft Defender'a ekleme
description: İş için Microsoft Defender'daki cihaz ekleme seçenekleri hakkında bilgi
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/09/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: a078b2a88fdde3af840cff64414fec0a712ae92e
ms.sourcegitcommit: 40f89c46032ea33de25417106f39cbeebef5a049
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2022
ms.locfileid: "63419312"
---
# <a name="onboard-devices-to-microsoft-defender-for-business"></a>Cihazları İş için Microsoft Defender'a ekleme

> [!IMPORTANT]
> İş için Microsoft Defender 1 Mart 2022 Microsoft 365 İş Ekstra müşterilere sunulmaktadır. Tek başına bir abonelik olarak İş için Defender önizlemededir ve istekte etmek için buraya kaydolan müşterilere ve IT İş Ortaklarına [aşamalı](https://aka.ms/mdb-preview) olarak tüm müşterilere aşamalı olarak tüm müşterilere aşamalı olarak ve tek başına bir abonelik sunar. Önizleme bir [dizi senaryo içerir ve](mdb-tutorials.md#try-these-preview-scenarios) düzenli olarak özellikler ekleycek.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

Defender for Business'daki cihaz ekleme deneyimi, Uç Nokta için Microsoft Defender'da bizim kullanmamız gerekenlere benzer süreçler üzerine inşa edilmiştir. Nasıl çalıştığını görmek için aşağıdaki videoyu izleyin:<br/><br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

İş için Microsoft Defender ile, kuruma uygun cihazları eklemeye yardımcı olmak için çeşitli seçenekleriniz vardır. Bu makale, seçenekleriniz üzerinde size yol sunar ve eklemenin nasıl çalıştığını genel bir bakış sunar.

> [!TIP]
> Uç nokta için Defender'da cihaz ekleme hakkında daha ayrıntılı bilgi görüntülemek için bkz. Cihazları ekleme ve Uç nokta özellikleri için [Microsoft Defender'ı yapılandırma](../defender-endpoint/onboard-configure.md).

## <a name="what-to-do"></a>Ne yapmalı?

1. Ekleme cihazları için [seçeneklerinizi](#device-onboarding-methods) görebilir ve aşağıdaki yöntemlerden birini seçebilirsiniz: 

   - [Microsoft Endpoint Manager'a Windows cihazlar için otomatik Microsoft Endpoint Manager](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager)
   - [Windows Mac cihazları için yerel betik](#local-script-in-defender-for-business)
   - [Microsoft Endpoint Manager (Microsoft Intune)](#microsoft-endpoint-manager)
   - [İş için Microsoft Defender güvenlik yapılandırması](#microsoft-defender-for-business-security-configuration)

2. [Yeni eklenen cihazlar için](#run-a-detection-test) bir algılama Windows çalıştırın.

3. [Sonraki adımlarınıza bakın](#next-steps). 

Bu makale ayrıca, Cihazlarınız için [algılama testi Windows ve Bir cihazla](#run-a-detection-test) [çıkarma hakkında da bilgi içerir](#offboarding-a-device).

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="device-onboarding-methods"></a>Cihaz ekleme yöntemleri

Aşağıdaki tabloda, İş için Defender'a cihazları eklemede en sık kullanılan yöntemler açık almaktadır. 

| Ekleme yöntemi  | Açıklama  | işletim sistemi |
|---------|---------|---------|
| **Otomatik katılım**<br/>(*zaten Microsoft Endpoint Manager kullanan müşteriler tarafından kullanılabilir*) | *Microsoft 365 İş Ekstra müşteriler zaten Microsoft Intune sahip olabilir ve bu seçeneği kullanabilir*. Otomatik ekleme, İş için Defender ile Microsoft Endpoint Manager arasında bir bağlantı ayarlar ve defender for Business Windows cihaz eklemeleri sağlar. Bu seçeneği kullanmak için, cihazlarınızı zaten Mobil Cihaz'a Endpoint Manager.<br/><br/>Daha fazla bilgi edinmek için bkz [. Otomatik ekleme](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager). | Windows |
| **Yerel betik** <br/> | Bu seçenek, İş için Defender'a cihazları el ile eklemeye olanak tanır. Yerel betiği kullanarak bir defada en fazla 10 cihaz abilirsiniz.<br/><br/>Daha fazla bilgi edinmek için bkz [. İş için Defender'da yerel betik](#local-script-in-defender-for-business). | Windows <br/>macOS |
| **Microsoft Intune** veya **Microsoft Endpoint Manager**<br/>(*Microsoft Intune veya Endpoint Manager*) | [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) Mobil [Cihaz Yönetimi de](/mem/intune/enrollment/device-enrollment) mobil cihaz yönetiminin Endpoint Manager. Microsoft 365 İş Ekstra müşteriler zaten Microsoft Intune ve bu seçeneği kullanabilir.<br/><br/>İş için Defender'ı Endpoint Manager önceden Endpoint Manager kullanıyorsanız cihazları eklemeye ve yönetmeye devam etmek için Endpoint Manager'i kullanmaya devam edin<br/><br/>Bu yöntemi kullanmak için bkz. [Microsoft Endpoint Manager](#microsoft-endpoint-manager). | Windows <br/>macOS<br/>iOS<br/>Android OS | 
| **İş için Microsoft Defender güvenlik yapılandırması** <br/>(*Microsoft 365 Defender kullanır*) | Bu seçeneği kullanmak için, belirli ayarları yapılandırarak İş için Defender ile Kurumsal arasındaki iletişimi kolaylaştıracak Endpoint Manager. Ardından, her cihaza indirerek Microsoft 365 Defender bir paket kullanarak cihazları Web portalına ([https://security.microsoft.com](https://security.microsoft.com)) da () dahil edin. Cihazlar ve cihazlar (Azure AD) Azure Active Directory Defender İş güvenlik ilkeleri arasında güven kurulur.<br/><br/>Daha fazla bilgi edinmek için bkz. [İş için Microsoft Defender güvenlik yapılandırması](#microsoft-defender-for-business-security-configuration). | Windows <br/>macOS |

> [!IMPORTANT]
> Bir sorun olursa ve ekleme işleminiz başarısız olursa bkz. [İş için Microsoft Defender sorun giderme](mdb-troubleshooting.yml).

## <a name="automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager"></a>Microsoft Endpoint Manager'a Windows cihazlar için otomatik Microsoft Endpoint Manager

Otomatik ekleme seçeneği yalnızca Windows için geçerlidir. Otomatik ekleme, siz İş için Defender'ı edinmeden önce Microsoft Intune'te Microsoft Endpoint Manager, Microsoft Intune veya Mobil Cihaz Yönetimi'Windows kullanıyorsa ve zaten Windows cihazlarınız varsa kullanılabilir Endpoint Manager. 

cihaz Windows zaten Endpoint Manager, siz İş için Defender'ı ayarlama ve yapılandırma sürecindeyken, İş için Defender bu cihazları algılar. Windows cihazlarının hepsi veya bazısı için otomatik ekleme özelliğini kullanmak Windows soruldu. Tüm cihaz ve Windows bir kerede ekleyebilir veya başlangıç yapmak üzere belirli cihazlar seçin ve daha sonra daha fazla cihaz ekleyin.

Otomatik ekleme hakkında daha fazla bilgi edinmek için, İş için Microsoft Defender'ı ayarlamak üzere sihirbazı kullanma makalesinde 2 [. adıma bakın](mdb-use-wizard.md).

## <a name="local-script-in-defender-for-business"></a>İş için Defender'da yerel komut dosyası

Kullanıcıları ve Mac cihazlarına yerel bir Windows betik kullanabilirsiniz. Ekleme betiğini bir cihazda çalıştırsanız, Azure Active Directory ile bir güven oluşturur (bu güven henüz yoksa), cihazı Microsoft Endpoint Manager'e (henüz kayıtlı değilse) kaydederek cihazı İş için Defender'a tümleşik olarak sağlar. Bu yöntem, İş için Defender'da cihaz ekleme için kullanışlıdır. Bir defada en fazla 10 cihaz abilirsiniz.

1. Microsoft 365 Defender portalına () gidin[https://security.microsoft.com](https://security.microsoft.com) ve oturum açın.

2. Gezinti bölmesinde Kullanıcı Uçları'Ayarlar  > **seçin** ve ardından Cihaz **yönetimi'nin altında Ekleme'yi** **seçin**.

3. **Windows 10 11** gibi bir işletim sistemi seçin ve ardından Cihaz ekleme'nin altındaki **Dağıtım** yöntemi bölümünde Yerel **betik'i seçin**. 

4. Ekleme **paketini indir'i seçin**. Ekleme paketini çıkarılabilir bir sürücüye kaydetmenizi öneririz.

5. Aşağıdaki makalelerde yer alan yönergeleri izleyin:

   - Windows cihazlar: [Yerel Windows kullanarak cihazları ekleme](../defender-endpoint/configure-endpoints-script.md#onboard-devices)
   - macOS cihazları: [macOS'ta Uç Nokta için Microsoft Defender için el ile dağıtım](../defender-endpoint/mac-install-manually.md#client-configuration)

## <a name="microsoft-endpoint-manager"></a>Microsoft Endpoint Manager

zaten Endpoint Manager kullanıyorsanız (Microsoft Intune ve Mobil Cihaz Yönetimi dahil), Endpoint Manager'ı kullanarak kuruluş cihazlarını eklemeye devam edebilirsiniz. Uygulama Endpoint Manager iOS ve Android cihazları dahil olmak üzere bilgisayarları, tabletleri ve telefonları dahil edin.

Bkz[. Microsoft Intune'de cihaz kaydı](/mem/intune/enrollment/device-enrollment).

## <a name="microsoft-defender-for-business-security-configuration"></a>İş için Microsoft Defender güvenlik yapılandırması

> [!NOTE]
> Cihazlarınızı ve güvenlik ilkelerinizi yönetmek Endpoint Manager için zaten Microsoft Endpoint Manager kullanıyorsanız, bu yöntemi [atlayıp Microsoft Endpoint Manager](#microsoft-endpoint-manager) bakın.

İş için Microsoft Defender güvenlik yapılandırması, Uç Nokta için Microsoft Defender Güvenlik Yönetimi (önizleme) olarak bilinen [bir özellik üzerine ek edilmiştir](/mem/intune/protect/mde-security-integration). Bu özellik, cihazları önceden Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) tam olarak kaydolmak zorunda kalmadan, Microsoft Endpoint Manager Defender for Business'a cihaz eklemeye olanak tanır. 

Bu yöntem, mobil cihaz eklemeye ve virüsten koruma ile güvenlik duvarı ilkelerinizi portala () Microsoft 365 Defender sağlar[https://security.microsoft.com](https://security.microsoft.com). Bunların hepsi şöyle çalışır:

1. Microsoft 365 Defender portaldan bir ekleme paketi indirir ve bu cihazları Defender for Business'a yüklemek için cihazlarınız üzerinde paketi çalıştırın.

2. Paketin çalıştırnıyor olması, her cihaz (güven yoksa) ve diğer (Azure AD) Azure Active Directory bir güven sağlar. 

3. Cihazlar, Azure AD Endpoint Manager kullanarak diğer cihazlarla iletişim kurar ve İş için Defender'daki güvenlik ilkeleri cihazlara itilir.

4. Cihazlarınızı ve ilkelerinizi hem Mobil portalda hem de Microsoft 365 Defender yönetim merkezinde () Endpoint Manager görüntüebilirsiniz[https://endpoint.microsoft.com](https://endpoint.microsoft.com).

Bu seçeneği kullanmak için, bazı ayarların önceden yapılandırılması gerekir. Önkoşullar ve desteklenen işletim sistemleri de dahil olmak üzere daha fazla bilgi edinmek için bkz. Önkoşulları olan cihazlarda uç nokta için [Microsoft Defender'ı Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).

## <a name="run-a-detection-test"></a>Algılama testi çalıştırma

Windows Için Defender'Windows cihazları işe başladıktan sonra, her şeyin düzgün olduğundan emin olmak için Windows bir algılama testi çalıştırabilirsiniz.

1. Windows bir klasör oluşturun: `C:\test-MDATP-test`.

2. Yönetici olarak Komut İstemi'ne açın.

3. Komut İstemi penceresinde aşağıdaki PowerShell komutunu çalıştırın:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Komut çalıştır edildikten sonra, Komut İstemi penceresi otomatik olarak kapanır. Başarılı olursa, algılama testi tamamlandı olarak işaretlenir ve yaklaşık 10 dakika içinde yeni eklenen cihaz için Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com)) yeni bir uyarı görüntülenir.

## <a name="gradual-device-onboarding"></a>Aşamalı cihaz ekleme

Kuruluş cihazlarınızı aşamalar içinde  onboard. *Bu aşamalı cihaz ekleme çağrısını aşamalı olarak çağrıltır.* 

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

7. Betiği, çıkaracakları her cihaza çalıştırın. Bu görevle ilgili yardıma mı ihtiyacınız var? Aşağıdaki kaynaklara bakın:   

   - Windows için: [Yerel Windows kullanarak çıkar çıkar](../defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script)
   - macOS cihazları: [macOS'ta kaldırma](../defender-endpoint/mac-resources.md#uninstalling)

> [!IMPORTANT]
> Bir cihaz çıkar bırak bırak bırak, cihazların Verileri İş için Defender'a göndermesini durdurur. Bununla birlikte, karalama öncesinde alınan veriler altı (6) aya kadar korunur.

## <a name="next-steps"></a>Sonraki adımlar

Şu şekilde devam edin:

- [5. Adım: İş için Microsoft Defender'da güvenlik ayarlarınızı ve ilkelerinizi yapılandırma](mdb-configure-security-settings.md)

- [İş için Microsoft Defender'ı kullanmaya başlama](mdb-get-started.md) 
