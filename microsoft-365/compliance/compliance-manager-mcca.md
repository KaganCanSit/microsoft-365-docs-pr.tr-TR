---
title: Uyumluluk Yöneticisi için Microsoft Uyumluluk Yapılandırması Çözümleyicisi
f1.keywords:
- NOCSH
ms.author: v-jgriffee
author: jmgriffee
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
description: Microsoft Uyumluluk Yöneticisi ile hızla kullanmaya devam etmek için Microsoft Uyumluluk Yapılandırma Çözümleyicisi'ni nasıl kullanabileceğinizi anlama.
ms.openlocfilehash: 2e0327a11067a4e474831d95b2c74c4c289086ce
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990007"
---
# <a name="microsoft-compliance-configuration-analyzer-for-compliance-manager-preview"></a>Uyumluluk Yöneticisi için Microsoft Uyumluluk Yapılandırması Çözümleyicisi (önizleme)

**Bu makalede:** Microsoft Uyumluluk Yönetimi'ne hızlı bir şekilde başlamak için Microsoft Uyumluluk Yapılandırma Çözümleyicisi aracını nasıl yükley yapılandırmayı ve çalıştırmayı öğrenin.

## <a name="microsoft-compliance-configuration-analyzer-mcca-preview-overview"></a>Microsoft Uyumluluk Yapılandırması Çözümleyicisi (MCCA) (önizleme) genel bakış

Microsoft Uyumluluk Yapılandırması Çözümleyicisi (MCCA), Microsoft Uyumluluk Yöneticisi'ni çalışmaya başlamanıza yardımcı olan bir [önizleme aracıdır](compliance-manager.md). MCCA, kuruluşun geçerli yapılandırmalarını getiren ve bunları önerilen en iyi yöntemlerle doğrulayan powershell Microsoft 365 yardımcı programdır. Bu en iyi uygulamalar, veri koruma ve veri idaresi için önemli düzenlemeleri ve standartları içeren bir denetim kümesine dayalıdır.

MCCA, Uyumluluk Yöneticisi'nde geçerli uyumluluk ortamınız için hangi geliştirme Microsoft 365 yardımcı olabilir. MCCA tarafından tanımlanan her eylem size Uyumluluk Yöneticisi'nin doğrudan bağlantıları ve düzeltme işlemi yapmaya başlamak için geçerli çözümün bağlantılarıyla uygulama hakkında öneriler sunar.

MCCA'yı anlamanız için ek bir kaynak, [2013'e okuma yönergelerini GitHub](https://github.com/OfficeDev/MCCA#overview). Bu sayfada önkoşullar hakkında ayrıntılı bilgiler ve yükleme yönergelerinin tamamını bulabilirsiniz. Bu sayfaya erişmek için GitHub hesabınız yok.

**Kullanılabilirlik** durumu: MCCA, Office 365 ve Microsoft 365 lisansına ve US Government Community (GCC) Moderate, GCC High ve Department of Defense (DoD) müşterileri olan tüm kuruluşlar tarafından kullanılabilir.

## <a name="install-mcca-and-run-a-report"></a>MCCA yükleme ve rapor çalıştırma

MCCA aracını yüklemek için, Windows PowerShell. Aracı indirip yüklekten sonra, raporları çalıştırmak için bu adımları yinelemeniz gerekli değildir. MCCA'yı her açtığınızda oturum açma bilgilerinizi sorar ve yeni, güncelleştirilmiş bir rapor üretir.

### <a name="step-1-install-windows-powershell"></a>1. Adım: Yükleme Windows PowerShell

Başlamak için, PowerShell galerisinde Exchange Online bir PowerShell modülü (v2.0.3 veya daha yüksek) gerekir. [Yükleme yönergelerini al'a bakın](https://www.powershellgallery.com/packages/ExchangeOnlineManagement/2.0.3).

### <a name="step-2-install-mcca"></a>2. Adım: MCCA'yı yükleme

MCCA yüklemek için, PowerShell'i yönetici modunda kullanarak başlatın. Aşağıdaki adımları izleyin:

1. Başlat **Windows seçin.**
1. **PowerShell yazın**, Seçenekler'e sağ **Windows PowerShell** yönetici olarak **çalıştır'ı seçin**.
1. Komut istemine şunu yazın:

    ```powershell
    Install-Module -Name MCCAPreview
    ```

### <a name="step-3-run-a-report"></a>3. Adım: Rapor çalıştırma

MCCA'yı yükledikten sonra, MCCA'yı çalıştırarak bir rapor oluşturabilirsiniz. Raporu çalıştırmak için:

1. PowerShell'i açma
2. Cmdlet'i çalıştırın:

    ```powershell
    Get-MCCAReport
    ```

    GCC High müşterisiysiniz, raporu çalıştırmak için ek bir giriş parametresi sağlamanız gerekir:

    ```powershell
    Get-MCCAReport -ExchangeEnvironmentName O365USGovGCCHigh
    ```

3. MCCA çalıştırlandıktan sonra, bir ilk sürüm denetimi yapar ve kimlik bilgilerini sorar. Kullanıcı adı istemini girin adım adım hesap e-Microsoft 365 oturum açın (rapor [oluşturmak için uygun rolleri görüntüleme](#role-based-reporting)). Ardından, parola istemine parolanızı girin.

Daha sonra raporunuz oluşturmak yaklaşık 2-5 dakika sürer. Bittiğinde, bir tarayıcı penceresi açılır ve HTML raporlarınızı görüntüler. Aracı her çalıştırsanız, kimlik bilgilerinizi sorar ve yeni bir rapor oluşturulur. Bu rapor, aşağıdaki dizinde yerel olarak depolanır:

C:\Users\<username>\AppData\Local\Microsoft\MCCA. 

Daha önce oluşturulan raporlara bu dizinden erişebilirsiniz.

## <a name="understanding-your-report"></a>Raporlarınızı anlama

Raporunuz, oluşturulma tarihi ve saatine göre verileri yansıtıyor. En üst bölümde ne zaman oluşturulladığı, kuruluş adınız ve kiracı kimliğiniz ile ilgili ayrıntılar yer almaktadır.

#### <a name="geolocation-based-reporting"></a>Coğrafi konum tabanlı raporlama

Not **bölümünde** , rapor alarak kiracının coğrafi konumu temel alarak özelleştirildiniz. Öneriler listelenen liste ülkenize veya bölgenize özeldir.

Coğrafi konum seçiminiz, o coğrafi konumla ilgili hassas bilgi türlerini (SITS) değerlendirmek ve ülkenize veya bölgenize uygun bir rapor oluşturmak için kullanılır. Kiracınıza sahip olduğunuz verilere dayalı olarak coğrafi konumlar'ı seçin.

Rapor un konum bilgilerini değiştirmek için coğrafi konum (-Geo) giriş parametresi sağlaymanız gerekir. Kiracınız için geçerli olan bir veya birden çok coğrafi konum seçebilirsiniz.

Raporu belirli bir konuma göre çalıştırmak için şu yönergeleri izleyin:

1. PowerShell'i açma
2. Belirli bir bölgeyi belirtmek için, aşağıdaki tabloda ülke veya bölgeye karşılık gelen numaraları kullanarak bir cmdlet çalıştırabilirsiniz. Birden çok numara girmek için bunları virgülle birbirinden ayırarak girin. Örneğin, aşağıdaki cmdlet, Asia-Pacific ve Japonya için özelleştirilmiş bir rapor çalıştıracak:

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
> Rapor her zaman SWIFT kodu, kredi kartı numarası gibi MCCA tarafından desteklenen uluslararası hassas bilgi türlerini içerir.

#### <a name="role-based-reporting"></a>Rol tabanlı raporlama

Raporunuz da rolünüz temel alarak özelleştirilebilir.

Aşağıdaki tabloda, hangi rollerin raporun hangi bölümlerine erişimi olduğu gösterilmiştir. Organizasyondaki diğer roller (aşağıdaki tabloda listelenmiyor) aracı çalıştıramayabilecek veya aracı çalıştırarak son rapordaki bilgilere sınırlı erişime sahip olabilir.

![MCCA - roller.](../media/compliance-manager-mcca-roles.png "MCCA rolleri")

Özel Durumlar:
1. Kullanıcılar "IP için IRM kullan" bölümünden farklı olarak IP Exchange Online oluşturamaz.
2. Kullanıcılar, "IP için IRM kullan" bölümünden farklı olarak IP Exchange Online elde edeb.'
3. Kullanıcılar, "O365'te İletişim Uyumluluğunu Etkinleştir" bölümünden farklı olarak IP için rapor oluşturabilecektir.
4. Kullanıcılar "Sitelerde Denetimi Etkinleştir" bölümünden IP için rapor Office 365 oluşturamaz.
5. Kullanıcılar, "YeniDek'te Denetimi Etkinleştir" bölümü dışında IP için Office 365 oluşturabilecektir.

#### <a name="solutions-summary-section"></a>Çözüm Özeti bölümü

Raporun **Çözüm Özeti** bölümünde, uyumluluk sonrası sonrası için Uyumluluk Yöneticisi'nde kuruma yönelik olarak gerçekleştirilen geliştirme eylemlerine genel bir bakış yer almaktadır.

![MCCA - Çözüm özeti.](../media/compliance-manager-mcca-solutions.png "MCCA Çözüm Özeti ekranı")

MCCA, geçerli yapılandırmalarınızı Uyumluluk Yöneticisi'nde önerilen geliştirme eylemlerine göre değerlendirir. MCCA aracı tarafından dikkat gerekiyor olarak tanımlanan tüm geliştirme eylemi bu bölümde listelenmiştir.

Her Microsoft çözümünün yanında, Uyumluluk Yöneticisi'nde yapılan geliştirme eylemlerine karşılık gelen öğe sayısını belirten renk kodlu kutular vardır. Eylemler üç durum durumuna göre birleşiktir:

- **Tamam**: Önerilen koşulları karşılayacak ve şu anda dikkat gerektir gereken eylemler
- **Geliştirme**: Dikkat gereken eylemler
- **Öneri**: dikkat gerektir yapmayan, ancak en iyi yöntemleri öneren eylemler
 
Geliştirmeleri ve önerileri görüntülemek için bir kutu seçin.

**Geliştirme durumu olan öğeler**

Geliştirme eyleminin sağ tarafından **Geliştirme** etiketi'nin yanındaki açılan etiketi seçin. Geçerli ayarlarınız ve önerilen geliştirme eylemleri hakkında hızlı bir özet ve ayrıntılara bakabilirsiniz. Bu özet, Uyumluluk Yöneticisi'ne, Uyumluluk Yöneticisi'ne ve ilgili belgelere Microsoft 365 uyumluluk merkezi bağlantıları içerir.

Uyumluluk Yöneticisi bağlantısına tıklamak, sizi o çözümde henüz uygulamamış olmadığınız tüm geliştirme eylemlerinin filtrelenmiş görünümüne alır. Buradan, uyumluluk puanınızı artırmak için kaç puanlık bir puanlık elde edin bütüncül [olduğunu ve](compliance-score-calculation.md) uygulanabilecek düzenlemeleri ve sertifikaları görebilirler.

DLP'de, size önerilenlere  dayalı önceden oluşturulmuş bir PowerShell betiği veren bir Düzeltme Betiği düğmesi vardır. Kopyalayıp doğrudan PowerShell konsolunuzun içine yapıştırabilirsiniz. Test modunda bir DLP ilkesi oluşturacak

**Öneri durumu olan öğeler**

Geliştirme eyleminin sağ yanındaki **Öneri** etiketinin yanındaki açılanı seçin. Geliştirme eylemiyle ilgili olarak, Microsoft 365 durum ortamının özetini ve önerilen en iyi yöntemleri buradasınız.

## <a name="resources"></a>Kaynaklar

MCCA'yı yükleme, ayarlama ve kullanma hakkında daha ayrıntılı bilgi için, GitHub ile ilgili [BENI GITHUB](https://github.com/OfficeDev/MCCA#overview) bakın.

PowerShell belgeleri Windows PowerShell hakkında daha fazla [bilgi için, başlangıç olarak PowerShell'i kullanın](/powershell/scripting/how-to-use-docs). Ayrıca bkz[. Windows PowerShell](/powershell/scripting/windows-powershell/starting-windows-powershell).
