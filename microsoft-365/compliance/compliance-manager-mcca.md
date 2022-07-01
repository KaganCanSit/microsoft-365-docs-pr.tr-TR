---
title: Microsoft Purview için Yapılandırma Çözümleyicisi
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
description: Microsoft Purview Uyumluluk Yöneticisi ile hızlı bir şekilde çalışmaya başlamak için Microsoft Purview için Yapılandırma Çözümleyicisi'ni nasıl kullanacağınızı öğrenin.
ms.openlocfilehash: d2e5fbc0d928fb5931139a274cf9cce5bdc4d983
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66573957"
---
# <a name="configuration-analyzer-for-microsoft-purview-camp"></a>Microsoft Purview için Yapılandırma Çözümleyicisi (CAMP)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**Bu makalede:** Microsoft Purview Uyumluluk Yöneticisi'ni hızlı bir şekilde kullanmaya başlamak için Microsoft Purview (CAMP) için Configuration Analyzer aracını yüklemeyi ve çalıştırmayı öğrenin.

## <a name="compliance-configuration-analyzer-camp-overview"></a>Uyumluluk Yapılandırma Çözümleyicisi'ne (CAMP) genel bakış

Microsoft Purview için Yapılandırma Çözümleyicisi (CAMP), [Microsoft Purview Uyumluluk Yöneticisi'ni](compliance-manager.md) kullanmaya başlamanıza yardımcı olabilecek bir araçtır. CAMP, kuruluşunuzun geçerli yapılandırmalarını getiren ve bunları Microsoft 365 tarafından önerilen en iyi yöntemlerle doğrulayan PowerShell tabanlı bir yardımcı programdır. Bu en iyi yöntemler, veri koruma ve veri idaresi için temel düzenlemeleri ve standartları içeren bir dizi denetimi temel alır.

CAMP, Uyumluluk Yöneticisi'ndeki hangi iyileştirme eylemlerinin geçerli Microsoft 365 ortamınız için geçerli olduğunu hızla görmenize yardımcı olabilir. CAMP tarafından tanımlanan her eylem, Uyumluluk Yöneticisi'ne doğrudan bağlantılar ve düzeltici işlem yapmaya başlamak için geçerli çözümle birlikte uygulama önerileri sunar.

Önkoşullar ve tam yükleme yönergeleri de dahil olmak üzere CAMP hakkında daha fazla ayrıntı için [GitHub'da BENIOKU yönergelerini](https://github.com/OfficeDev/CAMP#overview) ziyaret edin. Bu sayfaya erişmek için GitHub hesabına ihtiyacınız yoktur.

#### <a name="availability"></a>Kullanılabilirlik
CAMP, Office 365 ve Microsoft 365 lisanslarına sahip tüm kuruluşlar ve US Government Community (GCC) Moderate, GCC High ve Department of Defense (DoD) müşterileri tarafından kullanılabilir.

#### <a name="roles"></a>Rolleri

CAMP'e erişmek ve bunları kullanmak ve raporlardaki bilgilere erişmek için belirli kullanıcı rolleri gereklidir. [GitHub'da CAMP önkoşul bilgilerini](https://github.com/OfficeDev/CAMP#pre-requisites) ziyaret edin.

## <a name="install-camp-and-run-a-report"></a>CAMP'i yükleme ve rapor çalıştırma

WINDOWS POWERSHELL kullanarak CAMP aracını yükleyebilirsiniz. Aracı indirip yükledikten sonra, raporları çalıştırmak için bu adımları yinelemeniz gerekmez. CAMP'i her açtığınızda oturum açmanızı ister ve yeni, güncelleştirilmiş bir rapor oluşturur.

### <a name="step-1-install-the-exchange-online-powershell-v2-module"></a>1. Adım: Exchange Online PowerShell V2 modülünü yükleme

Başlamak için PowerShell galerisinde bulunan Exchange Online PowerShell modülüne (v2.0.3 veya üzeri) ihtiyacınız olacaktır. Yükleme yönergeleri için bkz. [EXO V2 modülünü yükleme ve koruma](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

### <a name="step-2-install-camp"></a>2. Adım: CAMP'i yükleme

CAMP'i yüklemek için powershell'i yönetici modunda kullanarak başlayın. Aşağıdaki adımları izleyin:

1. Windows **Başlangıç** düğmesini seçin.
1. **PowerShell** yazın, **Windows PowerShell** sağ tıklayın ve Yönetici **olarak çalıştır'ı** seçin.
1. Komut istemine şunu yazın:

    ```powershell
    Install-Module -Name CAMP
    ```

### <a name="step-3-run-a-report"></a>3. Adım: Rapor çalıştırma

CAMP'i yükledikten sonra CAMP'i çalıştırabilir ve bir rapor oluşturabilirsiniz. Bir raporu çalıştırmak için:

1. PowerShell'i açma
2. Cmdlet'ini çalıştırın:

    ```powershell
    Get-CAMPReport
    ```

    GCC High müşterisiyseniz raporu çalıştırmak için ek bir giriş parametresi sağlamanız gerekir:

    ```powershell
    Get-CAMPReport -ExchangeEnvironmentName O365USGovGCCHigh
    ```

3. CAMP çalıştırıldıktan sonra ilk sürüm denetimi yapar ve kimlik bilgilerini ister. Kullanıcı adını girin isteminde Microsoft 365 hesabı e-posta adresinizle oturum açın ([rapor oluşturmaya uygun rolleri görüntüleyin](https://github.com/OfficeDev/CAMP#pre-requisites)). Ardından parola istemine parolanızı girin.

Ardından raporunuzun oluşturulması yaklaşık 2-5 dakika sürer. İşlem tamamlandığında bir tarayıcı penceresi açılır ve HTML raporunuzu görüntüler. Aracı her çalıştırdığınızda kimlik bilgilerinizi ister ve yeni bir rapor oluşturur. Bu rapor C: \ Users \ *username* \ AppData \ Local \ Microsoft \ CAMP dizininde yerel olarak depolanır.

Daha önce oluşturulan raporlara bu dizinden erişebilirsiniz.

## <a name="understanding-your-report"></a>Raporunuzu anlama

Raporunuz, oluşturulduğu tarih ve saate göre verileri yansıtır. En üstteki bölümde ne zaman oluşturulduğu, kuruluşunuzun adı ve kiracı kimliği hakkında ayrıntılı bilgi sağlanır.

### <a name="geolocation-based-reporting"></a>Coğrafi konum tabanlı raporlama

**Not** bölümünde raporunuzun kiracınızın coğrafi konumuna göre özelleştirildiğini gösterir. Araçta listelenen öneriler ülkenize veya bölgenize özgü olacaktır.

Coğrafi konum seçiminiz, bu coğrafi konumla ilgili hassas bilgi türlerini (SCT) değerlendirmek ve ülkenize veya bölgenize uygun bir rapor oluşturmak için kullanılır. Kiracınızdaki verilere göre coğrafi konumları seçin.

Raporunuzun konum bilgilerini değiştirmek için bir coğrafi konum (-Geo) giriş parametresi sağlamanız gerekir. Kiracınız için geçerli olan bir veya birden çok coğrafi konumu seçebilirsiniz.

Raporu belirli bir konuma göre çalıştırmak için şu yönergeleri izleyin:

1. PowerShell'i açma
2. Belirli bir bölgeyi belirtmek için, aşağıdaki tablodan ülkeye veya bölgeye karşılık gelen sayıları kullanarak bir cmdlet çalıştıracaksınız. Birden çok sayıyı virgülle ayırarak girin. Örneğin, aşağıdaki cmdlet Asia-Pacific ve Japonya için özelleştirilmiş bir rapor çalıştırır:

    ```powershell
    Get-CAMPReport -Geo @(1,7)
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
  > Rapor her zaman SWIFT kodu, kredi kartı numarası gibi CAMP tarafından desteklenen uluslararası hassas bilgi türlerini içerecektir.

### <a name="role-based-reporting"></a>Rol tabanlı raporlama

Raporunuz da rolünüz temelinde özelleştirilir. [GitHub'da CAMP önkoşul bilgileri](https://github.com/OfficeDev/CAMP#pre-requisites), hangi rollerin raporun hangi bölümlerine erişimi olduğunu özetler. Kuruluşunuzdaki diğer roller aracı çalıştıramayabilir veya aracı çalıştırabilir ve son rapordaki bilgilere sınırlı erişime sahip olabilir.

### <a name="solutions-summary-section"></a>Çözüm Özeti bölümü

Raporun **Çözüm Özeti** bölümünde, uyumluluk duruşunuzu geliştirmeye yardımcı olmak için kuruluşunuzun Uyumluluk Yöneticisi'nde gerçekleştirebileceği iyileştirme eylemlerine genel bir bakış sunulur.

![MCCA - çözüm özeti.](../media/compliance-manager-mcca-solutions.png "CAMP Çözümleri Özet ekranı")

CAMP, geçerli yapılandırmalarınızı Uyumluluk Yöneticisi'nde önerilen iyileştirme eylemlerine göre değerlendirir. CAMP aracı tarafından dikkat edilmesi gerektiği belirlenen tüm iyileştirme eylemleri bu bölümde listelenecektir.

Her Microsoft çözümünün yanında, Compliance Manager'daki iyileştirme eylemlerine karşılık gelen öğe sayısını gösteren renk kodlu kutular bulunur. Eylemler üç durum durumuna ayrılır:

- **Tamam**: Şu anda önerilen koşulları karşılayan ve dikkate gerek duymadan kullanılabilecek eylemler
- **İyileştirme**: dikkat gerektiren eylemler
- **Öneri**: dikkate gerek duymayan, ancak en iyi yöntemleri önerdiğimiz eylemler

İyileştirmeleri ve önerileri görüntülemek için bir kutu seçin.

#### <a name="items-with-the-improvement-status"></a>İyileştirme durumuna sahip öğeler

İyileştirme eyleminin sağındaki **İyileştirme** etiketinin yanındaki açılan listeyi seçin. Geçerli ayarlarınız ve önerilen iyileştirme eylemleri hakkında hızlı bir özet ve ayrıntılar görürsünüz. Özet, Uyumluluk Yöneticisi'ne doğrudan bağlantılar, Microsoft Purview uyumluluk portalı ilgili çözüm ve ilgili belgeleri içerir.

Uyumluluk Yöneticisi bağlantısını seçtiğinizde, bu çözümdeki henüz uygulamadığınız tüm iyileştirme eylemlerinin filtrelenmiş bir görünümüne yönlendirilirsiniz. Buradan [, uyumluluk puanınızı](compliance-score-calculation.md) artırmak için ulaşabileceğiniz puan sayısını, bunların geçerli olduğu değerlendirmeleri ve geçerli düzenlemeleri ve sertifikaları görebilirsiniz.

DLP için, önerilenlere göre önceden oluşturulmuş bir PowerShell betiği sağlayan bir **Düzeltme Betiği** düğmesi vardır. Doğrudan PowerShell konsolunuza kopyalayıp yapıştırabilirsiniz. Test modunda bir DLP ilkesi oluşturur

#### <a name="items-with-recommendation-status"></a>Öneri durumundaki öğeler

İyileştirme eyleminin sağındaki **Öneri** etiketinin yanındaki açılan listeyi seçin. İyileştirme eylemiyle ilgili olarak kuruluşunuzun geçerli Microsoft 365 ortamının bir özetini ve önerilen en iyi yöntemleri görürsünüz.

## <a name="resources"></a>Kaynaklar

CAMP'ı yükleme, ayarlama ve kullanma hakkında daha ayrıntılı bilgi için [GitHub'da README yönergelerine bakın (GitHub](https://github.com/OfficeDev/CAMP#overview) hesabı gerekmez).

Windows PowerShell hakkında daha fazla bilgi [için Bkz. PowerShell belgelerini kullanma](/powershell/scripting/how-to-use-docs). Ayrıca bkz[. Başlangıç Windows PowerShell](/powershell/scripting/windows-powershell/starting-windows-powershell).
