---
title: Cihazları İş için Microsoft Defender'a ekleme
description: İş için Microsoft Defender'daki cihaz ekleme seçenekleri hakkında bilgi
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/14/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: c5de66418b242beb975cce0d6ece299753360c99
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2022
ms.locfileid: "63504771"
---
# <a name="onboard-devices-to-microsoft-defender-for-business"></a>Cihazları İş için Microsoft Defender'a ekleme

> [!IMPORTANT]
> İş için Microsoft Defender 1 Mart 2022 [Microsoft 365 İş Ekstra'den](../../business-premium/index.md) itibaren tüm müşterilere sunulmaktadır. Tek başına bir abonelik olarak İş için Defender önizlemededir ve istekte etmek için buraya kaydolan müşterilere ve IT İş Ortaklarına [aşamalı](https://aka.ms/mdb-preview) olarak tüm müşterilere aşamalı olarak tüm müşterilere aşamalı olarak ve tek başına bir abonelik sunar. Önizleme bir [dizi senaryo içerir ve](mdb-tutorials.md#try-these-preview-scenarios) düzenli olarak özellikler ekleycek.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

İş için Microsoft Defender ile, kuruma uygun cihazları eklemeye yardımcı olmak için çeşitli seçenekleriniz vardır. Bu makale, seçenekleriniz üzerinde size yol sunar ve eklemenin nasıl çalıştığını genel bir bakış sunar.

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="get-the-device-onboarding-guide"></a>Cihaz ekleme kılavuzunu al

Aşağıdaki kılavuzu ve bilgileri kullanarak, organizasyonunıza en uygun seçeneği belirtin.

[:::image type="content" source="media/mdb-device-onboarding.png" alt-text="Cihaz ekleme diyagramının ekran görüntüsü":::](https://download.microsoft.com/download/4/d/2/4d2d8a86-2130-45b4-ba42-2997c854383a/MDB-DeviceOnboardingFlow-March2022.pdf) <br/>
[PDF](https://download.microsoft.com/download/4/d/2/4d2d8a86-2130-45b4-ba42-2997c854383a/MDB-DeviceOnboardingFlow-March2022.pdf) | [Visio](https://download.microsoft.com/download/4/d/2/4d2d8a86-2130-45b4-ba42-2997c854383a/MDB-DeviceOnboardingFlow-March2022.vsdx)

## <a name="what-to-do"></a>Ne yapmalı?

1. [Ekleme cihazları için seçeneklerinizi görebilir](#device-onboarding-methods) ve bir yöntem seçebilirsiniz. 

   - [Zaten başka bir cihaza Windows cihazlar için otomatik katılım Microsoft Endpoint Manager](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager)
   - [MacOS veya macOS cihazlarını Windows yerel betik kullanma](#local-script-in-defender-for-business)
   - [Microsoft Endpoint Manager, macOS veya mobil Windows cihazlarına cihaz ekleme](#microsoft-endpoint-manager)
   - [Microsoft Defender İş güvenlik yapılandırmasıyla cihaz ekleme hakkında bilgi](#microsoft-defender-for-business-security-configuration)

2. [Yeni eklenen cihazlarda](#run-a-detection-test) bir algılama Windows çalıştırın.

3. [Sonraki adımlarınıza bakın](#next-steps). 

Bu makalede cihaz çıkarma [hakkında da bilgi bulabilirsiniz](#offboarding-a-device).

## <a name="device-onboarding-methods"></a>Cihaz ekleme yöntemleri

İster zaten Microsoft Endpoint Manager kullanıyor olun, ister basitleştirilmiş bir ekleme deneyimi için olsun, İş için Defender size ekleme cihazları için birkaç farklı yöntem sunar. İş için Defender'a cihaz eklemek için en yaygın kullanılan yöntemler şunlardır:

- **Microsoft Endpoint Manager'a** Windows cihazlar için otomatik Microsoft Endpoint Manager. Otomatik ekleme, İş için Defender ile Microsoft Endpoint Manager arasında bir bağlantı ayarlar ve defender for Business Windows cihaz eklemeleri sağlar. Bu seçeneği kullanmak için, cihazlarınızı zaten Mobil Cihaz'a Endpoint Manager. Daha fazla bilgi edinmek için bkz [. Otomatik ekleme](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager).

- **İş için** Defender'a Windows macOS cihazlarını el ile eklemeye için yerel betik. Yerel betiği kullanarak bir defada en fazla 10 cihaz abilirsiniz. Daha fazla bilgi edinmek için bkz [. İş için Defender'da yerel betik](#local-script-in-defender-for-business).

- **Microsoft Intune**, **macOS Microsoft Endpoint Manager** mobil Windows için bağlantı ve bağlantı kullanın. Cihazları mobil cihaz kaydına Endpoint Manager cihazlarınızı Defender for Business'a  yanitabilirsiniz. [Microsoft 365 İş Ekstra](../../business-premium/index.md) zaten [mobil Microsoft Intune vardır](/mem/intune/fundamentals/what-is-intune) ve hem [Microsoft Intune hem de](/mem/intune/enrollment/device-enrollment) Mobil Cihaz Yönetimi de artık mobil cihaz yönetiminin bir Endpoint Manager. Bu yöntemi kullanmak için bkz. [Microsoft Endpoint Manager](#microsoft-endpoint-manager).

- **Cihazları doğrudan portala () eklemeye** yardımcı olmak için İş için Microsoft Defender Microsoft 365 Defender yapılandırması [https://security.microsoft.com](https://security.microsoft.com). Bu seçeneği kullanmak için, belirli ayarları yapılandırarak İş için Defender ile Kurumsal arasındaki iletişimi kolaylaştıracak Endpoint Manager. Ardından, her cihazdan Microsoft 365 Defender indirerek ve çalıştırarak mobil cihaz portalına ([https://security.microsoft.com](https://security.microsoft.com)) cihazları () dahil edin. Cihazlar ve cihazlar (Azure AD) Azure Active Directory Defender İş güvenlik ilkeleri arasında güven kurulur. Daha fazla bilgi edinmek için bkz. [İş için Microsoft Defender güvenlik yapılandırması](#microsoft-defender-for-business-security-configuration). 

> [!IMPORTANT]
> Bir sorun olursa ve ekleme işleminiz başarısız olursa bkz. [İş için Microsoft Defender sorun giderme](mdb-troubleshooting.yml).

## <a name="automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager"></a>Microsoft Endpoint Manager'a Windows cihazlar için otomatik Microsoft Endpoint Manager

Otomatik ekleme seçeneği yalnızca Windows için geçerlidir. Aşağıdaki koşullar karşı olursa otomatik ekleme kullanılabilir:

- İş için Defender'ı Microsoft Endpoint Manager, Microsoft Intune veya Mobil Cihaz Yönetimi'Microsoft Intune MDM) zaten kullanıyordur

- Zaten Windows Windows cihazlarınız var Endpoint Manager

cihaz Windows zaten Endpoint Manager, siz İş için Defender'ı ayarlama ve yapılandırma sürecindeyken, İş için Defender bu cihazları algılar. Windows cihazlarının hepsi veya bazısı için otomatik ekleme özelliğini kullanmak Windows soruldu. Tüm cihaz ve Windows bir kerede ekleyebilir veya başlangıç yapmak üzere belirli cihazlar seçin ve daha sonra daha fazla cihaz ekleyin.

> [!TIP]
> "Tüm cihazlar kayıtlı" seçeneğini seçmenizi öneririz. Böylece, Windows cihazlarınız daha sonra Endpoint Manager cihazlarında yer alan cihazlar, otomatik olarak İş için Defender'a eklenir. Buna ek olarak, Endpoint Manager'de güvenlik ilkelerini ve ayarlarını yönetiyorsanız, cihazlarınızı, ilkelerinizi ve ayarlarınızı yönetmek için Microsoft 365 Defender portalına geçmenizi öneririz. Daha fazla bilgi edinmek için bkz [. Güvenlik ilkelerini ve cihazlarını yönetecek yeri seçme](mdb-configure-security-settings.md#choose-where-to-manage-security-policies-and-devices).

Otomatik ekleme hakkında daha fazla bilgi edinmek için, İş için Microsoft Defender'ı ayarlamak üzere sihirbazı kullanma makalesinde 2 [. adıma bakın](mdb-use-wizard.md).

## <a name="local-script-in-defender-for-business"></a>İş için Defender'da yerel komut dosyası

Kullanıcıları ve Mac cihazlarına yerel bir Windows betik kullanabilirsiniz. Ekleme betiğini bir cihazda çalıştırsanız, Azure Active Directory ile bir güven oluşturur (bu güven henüz yoksa), cihazı Microsoft Endpoint Manager'e (henüz kayıtlı değilse) kaydederek cihazı İş için Defender'a tümleşik olarak sağlar. Bu yöntem, İş için Defender'da cihaz ekleme için kullanışlıdır. Bir defada en fazla 10 cihaz abilirsiniz.

1. Microsoft 365 Defender portalına () gidin[https://security.microsoft.com](https://security.microsoft.com) ve oturum açın.

2. Gezinti bölmesinde Kullanıcı Uçları'Ayarlar  > **seçin** ve ardından Cihaz **yönetimi'nin altında Ekleme'yi** **seçin**.

3. **Windows 10 ve 11** veya **macOS** gibi bir işletim sistemi seçin ve ardından Dağıtım yöntemi bölümünde Yerel  **betik'i seçin**. 

4. Ekleme **paketini indir'i seçin**. Ekleme paketini çıkarılabilir bir sürücüye kaydetmenizi öneririz. ( **MacOS'u seçtiysanız** Yükleme paketini **indir'i** de seçin ve çıkarılabilir cihazınıza kaydedin.)

5. Aşağıdaki tabloda yer alan yönergeleri izleyin:

   | İşletim Sistemi | Yordam |
   |---|---|
   | Windows | 1. Windows cihazda, yapılandırma paketinin içeriğini Masaüstü klasörü gibi bir konuma ayıklayın. adlı bir dosyanız olması gerekir `WindowsDefenderATPLocalOnboardingScript.cmd`. <br/><br/>2. Yönetici olarak Komut İstemi'ne başvurun.<br/><br/>3. Betik dosyasının konumunu yazın. Örneğin, dosyayı Masaüstü klasörüne kopyaladıysanız, şunları yazmanız gerekir: `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`ve sonra Enter tuşuna basın (veya Tamam'ı **seçin**).<br/><br/>4. Betik çalıştır edildikten sonra Algılama testi [çalıştırma'ya devam edin](#run-a-detection-test). |
   | macOS | 1. Mac bilgisayarda, yükleme paketini yerel bir dizine `wdav.pkg` kaydedin. <br/><br/>2. Ekleme paketini, yükleme `WindowsDefenderATPOnboardingPackage.zip` paketinde kullanılan dizine kaydedin. <br/><br/>3. Finder'ı kullanarak, `wdav.pkg` daha önce kaydedilmiş olan size gidin ve dosyayı açın.<br/><br/>4. **Devam'ı** seçin, Lisans koşullarını kabul edin ve ardından istendiğinde parolanızı girin.<br/><br/>5. Microsoft sürücüsünün yüklenmesine izin vermeniz istenir ("Sistem Uzantısı Engellendi" veya "Yükleme engellendi"), ya da her ikisini birden yüklemeniz istenir. Sürücünün yüklenmeye izin verilmiyor olması gerekir. Yüklemeye izin vermek için, **Güvenlik Tercihlerini Aç'ı** veya **Sistem** >  Tercihlerini **AçSecurity & ve sonra** İzin Ver'i **seçin**.<br/><br/>6. Ekleme paketini çalıştırmak için Bash'ta aşağıdaki Python komutunu kullanın: `/usr/bin/python MicrosoftDefenderATPOnboardingMacOs.py`. <br/><br/>7. Cihazın organizasyonuyla ilişkili olduğunu onaylamak için Bash'ta şu Python komutunu kullanın: `mdatp health --field org_id`.<br/><br/>8. macOS 10.15 (Catalina) veya sonraki bir bilgisayar kullanıyorsanız cihazınızı korumak için İş için Defender iznini alın. Sistem **TercihleriSecurity &** >  **PrivacyPrivacyFull** >  >  **Disk Access'e gidin**.  Değişiklik yapmak için kilit simgesini seçin (iletişim kutusunun alt kısmında) ve sonra İş için Microsoft Defender'ı (veya uç nokta için Defender'ı (görüyorsanız, uç nokta için Defender) seçin. <br/><br/>9. Cihazın yerleşik olduğunu doğrulamak için Bash'ta şu komutu kullanın: `mdatp health --field real_time_protection_enabled`.    |

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

Bir cihazı çıkararak kullanmak için aşağıdaki yordamlardan birini kullanın:

| İşletim sistemi | Yordam |
|---|---|
| Windows | 1. Giriş portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.<br/><br/>2. Gezinti bölmesinde, Gezinti Bölmesi'ni **Ayarlar** Uç **Noktalar'ı seçin**.<br/><br/>3. Cihaz **yönetimi'nin altında** **Çıkar'ı seçin**.<br/><br/>4. **Windows 10 ve 11** gibi bir işletim sistemi seçin ve ardından Cihaz çıkar'ın altındaki Dağıtım yöntemi bölümünde Yerel  **betik'i seçin**. <br/><br/>5. Onay ekranında bilgileri gözden geçirin ve devam etmek için **İndir'i** seçin.<br/><br/>6. İndirme **paketini indir'i seçin**. Çıkarılabilir paketi çıkarılabilir bir sürücüye kaydetmenizi öneririz.<br/><br/>7. Betiği, çıkararak almak istediğiniz her cihazda çalıştırın.| 
| macOS | 1. **FinderApplications'e** >  gidin. <br/><br/>2. İş için Microsoft Defender'a sağ tıklayın ve Çöp Kutusuna **Taşı'yı seçin**. <br/><br/>--- veya --- <br/><br/> Şu komutu kullanın: `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`.|

> [!IMPORTANT]
> Bir cihaz çıkar bırak bırak bırak, cihazların Verileri İş için Defender'a göndermesini durdurur. Bununla birlikte, karalama öncesinde alınan veriler altı (6) aya kadar korunur.

## <a name="next-steps"></a>Sonraki adımlar

Şu şekilde devam edin:

- [5. Adım: İş için Microsoft Defender'da güvenlik ayarlarınızı ve ilkelerinizi yapılandırma](mdb-configure-security-settings.md)

- [İş için Microsoft Defender'ı kullanmaya başlama](mdb-get-started.md) 
