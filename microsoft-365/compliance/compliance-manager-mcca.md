---
title: Uyumluluk Yöneticisi için Microsoft Uyumluluk Yapılandırma Çözümleyicisi
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Microsoft Purview Uyumluluk Yöneticisi ile hızla çalışmaya başlamak için Microsoft Uyumluluk Yapılandırma Çözümleyicisi'ni kullanmayı öğrenin.
ms.openlocfilehash: a973412c2d40993b47343273675cee3922b57cdf
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012824"
---
# <a name="microsoft-compliance-configuration-analyzer-for-compliance-manager-preview"></a>Uyumluluk Yöneticisi için Microsoft Uyumluluk Yapılandırma Çözümleyicisi (önizleme)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**Bu makalede:** Microsoft Uyumluluk Yöneticisi'ni hızlı bir şekilde kullanmaya başlamak için Microsoft Uyumluluk Yapılandırma Çözümleyicisi aracını yüklemeyi ve çalıştırmayı öğrenin.

## <a name="microsoft-compliance-configuration-analyzer-mcca-preview-overview"></a>Microsoft Uyumluluk Yapılandırma Çözümleyicisi'ne (MCCA) (önizleme) genel bakış

Microsoft Uyumluluk Yapılandırma Çözümleyicisi (MCCA), [Microsoft Purview Uyumluluk Yöneticisi'ni](compliance-manager.md) kullanmaya başlamanıza yardımcı olabilecek bir önizleme aracıdır. MCCA, kuruluşunuzun geçerli yapılandırmalarını getiren ve bunları önerilen Microsoft 365 en iyi yöntemlerle doğrulayan PowerShell tabanlı bir yardımcı programdır. Bu en iyi yöntemler, veri koruma ve veri idaresi için temel düzenlemeleri ve standartları içeren bir dizi denetimi temel alır.

MCCA, Uyumluluk Yöneticisi'ndeki hangi iyileştirme eylemlerinin geçerli Microsoft 365 ortamınıza uygulandığını hızla görmenize yardımcı olabilir. MCCA tarafından tanımlanan her eylem, Uyumluluk Yöneticisi'ne doğrudan bağlantılar ve düzeltici eylem gerçekleştirmeye başlamak için geçerli çözümle birlikte size uygulama önerileri sunar.

MCCA'nın anlaşılması için ek bir kaynak, [GitHub'de BENIOKU yönergelerini](https://github.com/OfficeDev/MCCA#overview) ziyaret etmenizdir. Bu sayfa önkoşullar hakkında ayrıntılı bilgi sağlar ve tam yükleme yönergeleri sağlar. Bu sayfaya erişmek için bir GitHub hesabına ihtiyacınız yoktur.

**Kullanılabilirlik**: MCCA, Office 365 ve Microsoft 365 lisansları olan tüm kuruluşlar ve ABD Kamu Community (GCC) Orta, GCC Yüksek ve Savunma Bakanlığı (DoD) müşterileri tarafından kullanılabilir.

## <a name="install-mcca-and-run-a-report"></a>MCCA'yi yükleme ve rapor çalıştırma

Windows PowerShell kullanarak MCCA aracını yükleyebilirsiniz. Aracı indirip yükledikten sonra, raporları çalıştırmak için bu adımları yinelemeniz gerekmez. MCCA'yı her açtığınızda sizden oturum açma kimlik bilgilerinizi ister ve yeni, güncelleştirilmiş bir rapor oluşturur.

### <a name="step-1-install-the-exchange-online-powershell-v2-module"></a>1. Adım: Exchange Online PowerShell V2 modülünü yükleme

Başlamak için PowerShell galerisinde bulunan Exchange Online PowerShell modülüne (v2.0.3 veya üzeri) ihtiyacınız olacaktır. Yükleme yönergeleri için bkz. [EXO V2 modülünü yükleme ve koruma](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

### <a name="step-2-install-mcca"></a>2. Adım: MCCA'yi yükleme

MCCA'yı yüklemek için powershell'i yönetici modunda kullanarak başlayın. Aşağıdaki adımları izleyin:

1. **Windows Başlangıç** düğmesini seçin.
1. **PowerShell** yazın, **Windows PowerShell** sağ tıklayın ve Yönetici **olarak çalıştır'ı** seçin.
1. Komut istemine şunu yazın:

    ```powershell
    Install-Module -Name MCCAPreview
    ```

### <a name="step-3-run-a-report"></a>3. Adım: Rapor çalıştırma

MCCA'yı yükledikten sonra, MCCA'yı çalıştırabilir ve bir rapor oluşturabilirsiniz. Bir raporu çalıştırmak için:

1. PowerShell'i açma
2. Cmdlet'ini çalıştırın:

    ```powershell
    Get-MCCAReport
    ```

    GCC Yüksek müşterisiyseniz, raporu çalıştırmak için ek bir giriş parametresi sağlamanız gerekir:

    ```powershell
    Get-MCCAReport -ExchangeEnvironmentName O365USGovGCCHigh
    ```

3. MCCA çalıştırıldıktan sonra ilk sürüm denetimi yapar ve kimlik bilgilerini ister. Kullanıcı adını girin isteminde, Microsoft 365 hesabı e-posta adresinizle oturum açın ([rapor oluşturmaya uygun rolleri görüntüleyin](#role-based-reporting)). Ardından parola istemine parolanızı girin.

Ardından raporunuzun oluşturulması yaklaşık 2-5 dakika sürer. İşlem tamamlandığında bir tarayıcı penceresi açılır ve HTML raporunuzu görüntüler. Aracı her çalıştırdığınızda kimlik bilgilerinizi ister ve yeni bir rapor oluşturur. Bu rapor C: \ Users \ *username* \ AppData \ Local \ Microsoft \ MCCA dizininde yerel olarak depolanır.

Daha önce oluşturulan raporlara bu dizinden erişebilirsiniz.

## <a name="understanding-your-report"></a>Raporunuzu anlama

Raporunuz, oluşturulduğu tarih ve saate göre verileri yansıtır. En üstteki bölümde ne zaman oluşturulduğu, kuruluşunuzun adı ve kiracı kimliği hakkında ayrıntılı bilgi sağlanır.

### <a name="geolocation-based-reporting"></a>Coğrafi konum tabanlı raporlama

**Not** bölümünde raporunuzun kiracınızın coğrafi konumuna göre özelleştirildiğini gösterir. Araçta listelenen Öneriler ülkenize veya bölgenize özgü olacaktır.

Coğrafi konum seçiminiz, bu coğrafi konumla ilgili hassas bilgi türlerini (SCT) değerlendirmek ve ülkenize veya bölgenize uygun bir rapor oluşturmak için kullanılır. Kiracınızdaki verilere göre coğrafi konumları seçin.

Raporunuzun konum bilgilerini değiştirmek için bir coğrafi konum (-Geo) giriş parametresi sağlamanız gerekir. Kiracınız için geçerli olan bir veya birden çok coğrafi konumu seçebilirsiniz.

Raporu belirli bir konuma göre çalıştırmak için şu yönergeleri izleyin:

1. PowerShell'i açma
2. Belirli bir bölgeyi belirtmek için, aşağıdaki tablodan ülkeye veya bölgeye karşılık gelen sayıları kullanarak bir cmdlet çalıştıracaksınız. Birden çok sayıyı virgülle ayırarak girin. Örneğin, aşağıdaki cmdlet Asia-Pacific ve Japonya için özelleştirilmiş bir rapor çalıştırır:

    ```powershell
    Get-MCCAReport -Geo @(1,7)
    ```

  | Giriş |  Ülke veya Bölge |
  | :------------- | :------------: |
  | 1 | Asia-Pacific |
  | 2 | Avustralya |
  | 3 | Kanada |
  | 4 | Avrupa (Fransa hariç) / Orta Doğu / Afrika |
  | 5 | Fransa |
  | 6 | Hindistan |
  | 7 | Japonya |
  | 8 | Kore |
  | 9 | Kuzey Amerika (Kanada hariç) |
  | 10 | Güney Amerika |
  | 11 | South Africa |
  | 12 | İsviçre |
  | 13 | Birleşik Arap Emirlikleri |
  | 14 | Birleşik Krallık |

  > [!NOTE]
  > Rapor her zaman SWIFT kodu, kredi kartı numarası gibi MCCA tarafından desteklenen uluslararası hassas bilgi türlerini içerecektir.

### <a name="role-based-reporting"></a>Rol tabanlı raporlama

Raporunuz da rolünüz temelinde özelleştirilir.

Aşağıdaki tabloda, hangi rollerin raporun hangi bölümlerine erişimi olduğu gösterilmektedir. Kuruluşunuzdaki diğer roller (aşağıdaki tabloda listelenmeyen) aracı çalıştıramayabilir veya aracı çalıştırabilir ve son rapordaki bilgilere sınırlı erişime sahip olabilir.

![MCCA - roller.](../media/compliance-manager-mcca-roles.png "MCCA rolleri")

Özel durum:

1. Kullanıcılar , "Exchange Online için IRM kullanma" bölümünden farklı olarak IP için rapor oluşturamaz.
2. Kullanıcılar , "Exchange Online için IRM kullanma" bölümünden farklı olarak IP için rapor oluşturabilir.
3. Kullanıcılar , "O365'te İletişim Uyumluluğunu Etkinleştirme" bölümünden farklı olarak IP için rapor oluşturabilir.
4. Kullanıcılar , "Office 365'da Denetimi Etkinleştir" bölümünden farklı olarak IP için rapor oluşturamaz.
5. Kullanıcılar , "Office 365'da Denetimi Etkinleştirme" bölümünden farklı olarak IP için rapor oluşturabilir.

### <a name="solutions-summary-section"></a>Çözüm Özeti bölümü

Raporun **Çözüm Özeti** bölümünde, uyumluluk duruşunuzu geliştirmeye yardımcı olmak için kuruluşunuzun Uyumluluk Yöneticisi'nde gerçekleştirebileceği iyileştirme eylemlerine genel bir bakış sunulur.

![MCCA - çözüm özeti.](../media/compliance-manager-mcca-solutions.png "MCCA Çözümleri Özet ekranı")

MCCA, geçerli yapılandırmalarınızı Uyumluluk Yöneticisi'nde önerilen iyileştirme eylemlerine göre değerlendirir. MCCA aracı tarafından dikkat edilmesi gerektiği belirlenen tüm iyileştirme eylemleri bu bölümde listelenecektir.

Her Microsoft çözümünün yanında, Compliance Manager'daki iyileştirme eylemlerine karşılık gelen öğe sayısını gösteren renk kodlu kutular bulunur. Eylemler üç durum durumuna ayrılır:

- **Tamam**: Şu anda önerilen koşulları karşılayan ve dikkate gerek duymadan kullanılabilecek eylemler
- **İyileştirme**: dikkat gerektiren eylemler
- **Öneri**: dikkate gerek duymayan, ancak en iyi yöntemleri önerdiğimiz eylemler

İyileştirmeleri ve önerileri görüntülemek için bir kutu seçin.

#### <a name="items-with-the-improvement-status"></a>İyileştirme durumuna sahip öğeler

İyileştirme eyleminin sağındaki **İyileştirme** etiketinin yanındaki açılan listeyi seçin. Geçerli ayarlarınız ve önerilen iyileştirme eylemleri hakkında hızlı bir özet ve ayrıntılar görürsünüz. Özet, Uyumluluk Yöneticisi'ne doğrudan bağlantılar, Microsoft Purview uyumluluk portalındaki geçerli çözüm ve ilgili belgeleri içerir.

Uyumluluk Yöneticisi bağlantısına tıkladığınızda, bu çözüm içinde henüz uygulamadığınız tüm iyileştirme eylemlerinin filtrelenmiş bir görünümüne yönlendirilirsiniz. Buradan [, uyumluluk puanınızı](compliance-score-calculation.md) artırmak için ulaşabileceğiniz puan sayısını, bunların geçerli olduğu değerlendirmeleri ve geçerli düzenlemeleri ve sertifikaları görebilirsiniz.

DLP için, önerilenlere göre önceden oluşturulmuş bir PowerShell betiği sağlayan bir **Düzeltme Betiği** düğmesi vardır. Doğrudan PowerShell konsolunuza kopyalayıp yapıştırabilirsiniz. Test modunda bir DLP ilkesi oluşturur

#### <a name="items-with-recommendation-status"></a>Öneri durumundaki öğeler

İyileştirme eyleminin sağındaki **Öneri** etiketinin yanındaki açılan listeyi seçin. İyileştirme eylemiyle ilgili olarak kuruluşunuzun geçerli Microsoft 365 ortamının bir özetini ve önerilen en iyi yöntemleri görürsünüz.

## <a name="resources"></a>Kaynaklar

MCCA'yı yükleme, ayarlama ve kullanma hakkında daha ayrıntılı bilgi için [GitHub (GitHub hesabı gerekmez) hakkındaki BENİOKU yönergelerine](https://github.com/OfficeDev/MCCA#overview) bakın.

Windows PowerShell hakkında daha fazla bilgi [için Bkz. PowerShell belgelerini kullanma](/powershell/scripting/how-to-use-docs). Ayrıca bkz[. Başlangıç Windows PowerShell](/powershell/scripting/windows-powershell/starting-windows-powershell).
