---
title: dosya dahil
description: dosya dahil
author: mjcaparas
ms.service: microsoft-365-enterprise
ms.author: macapara
ms.openlocfilehash: 126454f65f8f0e92161f1d51321390ffb60c1308
ms.sourcegitcommit: bcea69bacd1b48827bd60af2880909593a1609a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "62997195"
---
## <a name="prerequisites"></a>Önkoşullar

Uç Nokta Için Microsoft Defender Güvenlik Yönetimi Senaryosuna yönelik gereksinimler için aşağıdaki bölümleri gözden geçirme:

### <a name="environment"></a>Ortam

Cihaz Uç Nokta için Microsoft Defender'a ekli olduğunda:


- Cihaz, Intune'a mobil Endpoint Manager (MDM) kaydı olan mevcut bir iletişim durumu için ankete alınacaktır.
- Güvenlik iletişim Endpoint Manager olmayan cihazlar Güvenlik Yönetimi özelliğini etkinleştirir
- Henüz yoksa, Azure Active Directory bir Güven ile oluşturulur
- Azure Active Directory güven, ilkeleri alma (Intune) Endpoint Manager iletişim kurmak için kullanılır
- Dış cihazdan Endpoint Manager ilkesi, Uç Nokta için Microsoft Defender tarafından cihazda zorunlu kılındı

### <a name="active-directory-requirements"></a>Active Directory Gereksinimleri

Etki alanına katılmış bir cihaz Azure Active Directory güven oluşturduğunda, bu senaryo Karma Birleştirme *Azure Active Directory olarak adlandırılır*. Uç Nokta için Microsoft Defender Güvenlik Yönetimi, aşağıdaki gereksinimlerle bu senaryoyu tam olarak destekler:

- Azure Active Directory Bağlan (AAD Bağlan) uç nokta için Microsoft Defender'dan kullanılan kiracıyla eşitlenmiş olmalıdır
- Karma Azure Active Directory Birleştirme'nin ortamınız içinde yapılandırılması gerekir (Federasyon veya AAD Bağlan Eşitleme aracılığıyla)
- AAD Bağlan Eşitleme, eşitle *eşitleme kapsamındaki* cihaz nesnelerini de Azure Active Directory (birleştirme için gerektiğinde)
- AAD Bağlan kuralları, Server 2012 R2 için değiştirilmelidir (Server 2012 R2 desteği gerektiğinde)
- Tüm cihazların, Uç Nokta için Microsoft Defender Azure Active Directory barındıran kiracının Web sitesinde kaydolması gerekir. Kiracılar arası senaryolar desteklenmiyor. 

### <a name="connectivity-requirements"></a>Bağlantı Gereksinimleri

Cihazların aşağıdaki uç noktalara erişimi olmalıdır:

- `enterpriseregistration.windows.net` - Azure AD kaydı için.
- `login.microsoftonline.com` - Azure AD kaydı için.
- `*.dm.microsoft.com` - Joker karakter kullanımı kayıt, iade ve raporlama için kullanılan ve hizmet ölçekleri olarak değiş değişerek, bulut hizmeti uç noktalarını destekler.

### <a name="supported-platforms"></a>Desteklenen platformlar

Uç nokta güvenlik yönetimi için Microsoft Defender ilkeleri aşağıdaki cihaz platformlarında destekler:

- Windows 10 Professional/Enterprise ([KB5006738 ile](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541))
- Windows Server 2012 Cihazlar için [Microsoft Defender ile Down-Level](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview) R2
- [Windows Server 2016 Cihazlar için Microsoft Defender ile Down-Level güncelleştirme](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Windows Server 2019 ([KB5006744 ile](https://support.microsoft.com/topic/october-19-2021-kb5006744-os-build-17763-2268-preview-e043a8a3-901b-4190-bb6b-f5a4137411c0))
- Windows Server 2022 ([KB5006745 ile](https://support.microsoft.com/topic/october-26-2021-kb5006745-os-build-20348-320-preview-8ff9319a-19e7-40c7-bbd1-cd70fcca066c))

### <a name="licensing-and-subscriptions"></a>Lisanslar ve abonelikler

Uç Nokta için Microsoft Defender güvenlik yönetimini kullanmak için gerekenler:

- Uç Nokta için Microsoft Defender lisansları (örneğin, Microsoft 365) veya yalnızca Uç Nokta için Microsoft Defender için tek başına lisans alan bir abonelik. Uç nokta lisansları için Microsoft Defender'a verilen bir abonelik, kiracınıza Etki Noktası yönetim merkezinin Uç nokta güvenlik düğümüne Microsoft Endpoint Manager sağlar.

  > [!NOTE]  
  > **Özel** durum: Yalnızca Bulut için Microsoft Defender lisansının (eski adı Azure Güvenlik Merkezi) bir parçası olarak Uç Nokta için Microsoft Defender'a erişiminiz varsa, Uç Nokta işlevselliği için Microsoft Defender Güvenlik Yönetimi kullanılamaz.

Uç nokta güvenlik düğümü, cihazlarınız için Uç Nokta için Microsoft Defender'ı yönetmek ve cihaz durumunu izlemek üzere ilkeleri yapılandır nereye dağıtın?

Seçenekler hakkında güncel bilgiler için bkz. Uç [Nokta için Microsoft Defender'a ilişkin en düşük gereksinimler](/microsoft-365/security/defender-endpoint/minimum-requirements?view=o365-worldwide&preserve-view=true).



## <a name="architecture"></a>Mimari

Aşağıdaki diyagram, Uç nokta güvenlik yapılandırma yönetim çözümü için Microsoft Defender'ın kavramsal bir gösterimidir.

:::image type="content" alt-text="Uç nokta güvenlik yapılandırma yönetim çözümü için Microsoft Defender'ın kavramsal gösterimi" source="../security/defender-endpoint/images/mde-architecture.png":::

1. Uç Nokta için Microsoft Defender'a ekli cihazlar.

2. Her cihazla Azure AD arasında bir güven kurulur. Bir cihazda varolan bir güven olduğunda, bu kullanılır. Cihazlar kayıtlı değilken, yeni bir güven oluşturulur.

3. Cihazlar, diğer cihazlarla iletişim kurmak için Azure AD Endpoint Manager. Bu kimlik Microsoft Endpoint Manager, iade edildiklerine cihazları hedef alan ilkeleri dağıtmaya olanak tanır.

4. Uç Nokta için Defender, ilkenin durumunu Uç Nokta durumuna geri Endpoint Manager.

## <a name="which-solution-should-i-use"></a>Hangi çözümü kullan gerekir?

Microsoft Endpoint Manager, cihazlar için Uç nokta için Defender yapılandırmasını yönetmek için çeşitli yöntemler ve ilke türleri içerir.

Cihaz korumanız uç nokta için Defender'ın yönetiminin ötesine geçene kadar ihtiyaç duyuyorsa, cihaz uyumluluğu, yönetilen uygulamalar, uygulama koruma ilkeleri ve üçüncü taraf uyumluluk ve mobil tehdit savunma iş ortaklarıyla tümleştirme gibi cihazların korunmasına yardımcı olmak üzere Microsoft Endpoint Manager tarafından sağlanan ek  özellikler hakkında bilgi edinmek için cihaz korumasına genel bakış bilgilerine bakın.[](/mem/intune/protect/device-protect) 

Aşağıdaki tablo, MDE ayarlarını yapılandıran ilkelerin farklı senaryolar tarafından yönetilen cihazlar tarafından destek destekler olduğunu anlamanıza yardımcı olabilir. Hem *MDE* güvenlik yapılandırması hem de *Microsoft Endpoint Manager* için desteklenen bir ilke dağıtın, bu ilkenin tek bir örneği yalnızca MDE'yi çalıştıran cihazlar ve Intune veya Configuration Manager tarafından yönetilen cihazlar tarafından işlenebilir.

| Microsoft Endpoint Manager  | workload | MDE Güvenlik yapılandırması  |  Microsoft Endpoint Manager |
|----------------|----------------|-------------------|------------|
| Uç nokta güvenliği    | Virüsten koruma                   | ![Destekleniyor](../media/green-check.png)  | ![Destekleniyor](../media/green-check.png)  |
|                      | Disk Şifrelemesi   |           | ![Destekleniyor](../media/green-check.png)  |
|                      | Güvenlik Duvarı (Profil ve Kurallar)                | ![Destekleniyor](../media/green-check.png) | ![Destekleniyor](../media/green-check.png)  |
|                      | Uç nokta algılama ve yanıt        | ![Destekleniyor](../media/green-check.png) | ![Destekleniyor](../media/green-check.png)  |
|                      | Saldırı yüzeyini azaltma    |           | ![Destekleniyor](../media/green-check.png)  |
|                      | Hesap Koruması       |       | ![Destekleniyor](../media/green-check.png)  |
|                      | Cihaz Uyumluluğu     |   | ![Destekleniyor](../media/green-check.png)  |
|                      | Koşullu Erişim    |   | ![Destekleniyor](../media/green-check.png)  |
|                      | Güvenlik taban çizgilerini      |   | ![Destekleniyor](../media/green-check.png)  |

**Uç nokta güvenlik** ilkeleri, güvenlik yöneticileri tarafından kullanılmak üzere tasarlanmış, ancak kuruluşta cihazları korumaya odaklanan ayrı ayarlar gruplarıdır.

- **Virüsten** koruma ilkeleri, Uç Nokta için Microsoft Defender'da bulunan güvenlik yapılandırmalarını yönetir. Uç  [nokta güvenliği](/mem/intune/protect/endpoint-security-antivirus-policy) için virüsten koruma ilkesine bakın.
- **Saldırı yüzeyini azaltma** ilkeleri, kuruluşlarının siber tehditlere ve saldırılara açık olduğu yerleri en aza indirmeye odaklanır. Daha fazla bilgi için tehdit koruması belgelerinde [saldırı](/windows/security/threat-protection/microsoft-defender-atp/overview-attack-surface-reduction) yüzeyini azaltmaya Windows ve uç nokta güvenliği için [saldırı yüzeyini](/mem/intune/protect/endpoint-security-asr-policy) azaltma ilkesine bakın.
- **Uç nokta algılama ve** yanıt (EDR) ilkeleri, gerçek zamanlı olarak yakın olan ve işlem gerçekleştirilebilir olan gelişmiş saldırı algılamaları sağlayan Uç Nokta için Defender özelliklerini yönetir. Güvenlik analistleri EDR için yapılandırmaları temel alarak uyarıları etkili bir şekilde önceliklerini belirlemeli, ihlallerin tam kapsamına yönelik görünürlük elde eder ve tehditleri düzeltmek için yanıt eylemleri gerçekleştirebilirsiniz. Uç [uç noktada algılama ve yanıtlama](/mem/intune/protect/endpoint-security-edr-policy) için daha fazla ilkeye bakın.
- **Güvenlik** duvarı ilkeleri odak cihazlarınız için Defender güvenlik duvarındadır. Uç [nokta güvenliği için](/mem/intune/protect/endpoint-security-firewall-policy) güvenlik duvarı ilkesine bakın.
- **Güvenlik Duvarı Kuralları** , belirli bağlantı noktaları, protokoller, uygulamalar ve ağlar dahil olmak üzere Güvenlik Duvarları için ayrıntılı kuralları yapılandırır. Uç [nokta güvenliği için](/mem/intune/protect/endpoint-security-firewall-policy) güvenlik duvarı ilkesine bakın.
- **Güvenlik taban çizgisi** Defender, Edge veya başka ürünler için Microsoft'un önerilen güvenlik posturlarını tanımlayan önceden yapılandırılmış güvenlik Windows. Varsayılan öneriler ilgili ürün ekiplerindendir ve önerilen güvenli yapılandırmayı cihazlara hızla dağıtmaya olanak tanır. Ayarlar her taban çizgisi içinde önceden yapılandırılmış durumdayken, bu ayarların özelleştirilmiş tekrarlarını oluşturabilir ve kuruluşla ilgili güvenlik beklentilerini oluşturabilirsiniz. Intune [için güvenlik](/mem/intune/protect/security-baselines) taban çizgilerine bakın.

## <a name="configure-your-tenant-to-support-microsoft-defender-for-endpoint-security-configuration-management"></a>Uç Nokta Güvenlik Yapılandırması Yönetimi için Microsoft Defender'ı destekleyecek şekilde kiracınızı yapılandırma

Microsoft Defender for Endpoint security configuration management for Endpoint security configuration management Microsoft Endpoint Manager center üzerinden, her konsol içinden bu iki uç nokta arasındaki iletişimi etkinleştirmeniz gerekir.

1. Portalda [oturum Microsoft 365 Defender ve](https://security.microsoft.com/) **Ayarlar** >  **EndpointsConfiguration** >  **ManagementEnforcement** >  **Scope seçeneğine** gidin ve güvenlik ayarları yönetimi için platformları etkinleştirin:

   :::image type="content" source="../media/enable-mde-settings-management-defender.png" alt-text="Defender konsolunda Uç nokta ayarları yönetimi için Microsoft Defender'ı etkinleştirin.":::

2. İlgili kullanıcıların, Güvenlik Portalı'Microsoft Endpoint Manager uç nokta güvenlik ayarlarını yönetme izinlerine sahip olduğundan emin olun veya Defender portalında bir rol yapılandırarak bu izinleri verin. **Ayarlar** >  **DeğilAdd** >  **öğesi'ne gidin**:

   :::image type="content" source="../media/add-role-in-mde.png" alt-text="Defender portalında yeni bir rol oluşturun.":::

   > [!TIP]
   > Var olan rolleri değiştirebilir ve gerekli izinleri ekleyebilir ve uç nokta için Microsoft Defender'da ek roller oluşturabilirsiniz

3. Rolü yapılandırarak kullanıcıları ekleyin ve şu bağlantıda Uç nokta güvenlik **ayarlarını yönet'i seçmeyi Microsoft Endpoint Manager**:

   :::image type="content" source="../media/add-role.png" alt-text="Ayarları yönetmesi için kullanıcılara izinler verin.":::

4. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) oturum açın.

5. Uç **nokta güvenliğiMicrosoft** >  **Defender For Endpoint** öğesini seçin ve Uç Nokta Güvenlik Yapılandırmaları (Önizleme) öğesini Açık olarak zorunlu tutularak Uç Nokta için **Microsoft Defender'a İzin Ver'i** **ayarlayın**.

   :::image type="content" source="../media/enable-mde-settings-management-mem.png" alt-text="Genel yönetim merkezinde Uç nokta ayarları yönetimi için Microsoft Defender Microsoft Endpoint Manager etkinleştirin.":::

   Bu seçeneği Açık olarak ayarsanız *, Microsoft Endpoint Manager* tarafından yönetilemedi uç nokta için Microsoft Defender'da platform kapsamındaki tüm cihazlar Uç Nokta için Microsoft Defender'a ekleme için uygun olur.

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>Cihazları Uç Nokta için Microsoft Defender'a ekleme

Uç Nokta için Microsoft Defender cihazları eklemeye yardımcı olmak için çeşitli seçenekleri destekler. Güncel bilgiler için bkz. [Uç nokta için Defender belgelerinde Windows cihazlara](/microsoft-365/security/defender-endpoint/security-config-management) yönelik ekleme araçları ve yöntemleri.


> [!IMPORTANT]
> Cihaz Uç Nokta için Microsoft Defender ile eklendikten sonra, Uç Nokta için Microsoft Defender Güvenlik Yönetimi'ne kaydolamadan önce **MDE-Management** ile etiketlenmiş olmalıdır. MDE'de cihaz etiketleme hakkında daha fazla bilgi için bkz [*. Cihaz etiketleri oluşturma ve yönetme*](/microsoft-365/security/defender-endpoint/machine-tags).


## <a name="co-existence-with-microsoft-endpoint-configuration-manager"></a>Diğerleriyle birlikte Microsoft Endpoint Configuration Manager
Configuration Manager kullanırken, güvenlik ilkesi yönetimi için en iyi yol Configuration [Manager kiracı eklemeyi kullanmaktır](/mem/configmgr/tenant-attach/endpoint-security-get-started). Bazı ortamlarda Microsoft Defender için Güvenlik Yönetimi'nin kullanımı tercih edilir olabilir. Microsoft Defender için Configuration Manager ile Güvenlik Yönetimi'ni kullanırken, uç nokta güvenlik ilkesi tek bir denetim uçağına yalıtılmış olmalıdır. İlkenin her iki kanalda da denetlenerek çakışmalar ve undesed sonuçlar için fırsat oluşturması gerekir.


## <a name="create-azure-ad-groups"></a>Azure AD Grupları oluşturma

Uç nokta için Defender'a ekli cihazlardan sonra, Uç Nokta için Microsoft Defender ilke dağıtımını desteklemek için cihaz grupları oluşturmanız gerekir.

Uç nokta için Microsoft Defender'a kaydolan ancak Intune veya Configuration Manager tarafından yönetil olmayan cihazları tanımlamak için:

1. Yönetim [merkezi'Microsoft Endpoint Manager oturum açma](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Tüm **cihazlar'a** >  gidin ve ardından Cihazların görünümünü **sıralamak için** Yönetilen sütununu seçin.

   Uç nokta için Microsoft Defender'a ekli olan ve kayıtlı olan ancak Intune tarafından yönetil olmayan cihazlar, Yönetilen sütununda Uç Nokta için **Microsoft Defender'ı** görüntüler. Bunlar, Uç Nokta için Microsoft Defender için güvenlik yönetimi ilkesi alan cihazlardır.

   Uç Nokta için Microsoft Defender güvenlik yönetimini kullanan cihazlar için iki etiket de bulabilirsiniz:

   - **MDEJoined** - Bu senaryonun bir parçası olarak dizine katılmış cihazlara eklenir.
   - **MDEManaged** - Güvenlik yönetimi senaryosu etkin olarak kullanan cihazlara eklenir. Uç Nokta için Defender güvenlik yapılandırmasını yönetmeyi durdurursa bu etiket cihazdan kaldırılır.

[Azure AD'de](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal) veya uygulama yönetim merkezinin [içinde bu cihazlar Microsoft Endpoint Manager oluşturabilirsiniz](/mem/intune/fundamentals/groups-add).

## <a name="deploy-policy"></a>İlkeyi dağıtma

Uç Nokta için Microsoft Defender tarafından yönetilen cihazlar içeren bir veya daha fazla Azure AD grubu oluşturduktan sonra, bu gruplara Uç Nokta için Microsoft Defender Güvenlik Yönetimi için aşağıdaki ilkeleri oluşturabilir ve dağıtabilirsiniz:

- Virüsten koruma
- Güvenlik Duvarı
- Güvenlik Duvarı Kuralları
- Uç Nokta Algılama ve Yanıt

> [!TIP]
> Bir cihaza aynı ayarı yöneten birden çok ilkeyi dağıtmaktan kaçının.
>
> Microsoft Endpoint Manager her ilke örneğinin cihaz tarafından ayrı olarak alınarak, her uç nokta güvenlik ilkesi türünün birden çok örneğini aynı cihaza dağıtmayı destekler. Bu nedenle, bir cihaz farklı ilkelerden aynı ayar için ayrı yapılandırmalar alabiliyor ve bu da çakışmaya neden olabilir. Bazı ayarlar (Virüsten Koruma Dışlamalar gibi) istemcide birleşecek ve başarılı bir şekilde uygulanacaktır.

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) oturum açın.

2. Uç nokta **güvenliği'ne** gidin, sonra Virüsten Koruma veya Güvenlik Duvarı olarak yapılandırmak istediğiniz ilke türünü seçin ve ardından İlke **Oluştur'a gidin**.

3. Aşağıdaki özellikleri veya seçtiğiniz ilke türünü girin:

   - Virüsten koruma ilkesi için şunları seçin:
     - Platform: **Windows 10, Windows 11 ve Windows Server (Önizleme)**
     - Profil: **Microsoft Defender Virüsten Koruma (Önizleme)**

   - Güvenlik duvarı ilkesi için şunları seçin:
     - Platform: **Windows 10, Windows 11 ve Windows Server (Önizleme)**
     - Profil: **Microsoft Defender Güvenlik Duvarı (Önizleme)**

   - Güvenlik Duvarı Kuralları ilkesi için şunları seçin:
     - Platform: **Windows 10, Windows 11 ve Windows Server (Önizleme)**
     - Profil: **Microsoft Defender Güvenlik Duvarı Kuralları (Önizleme)**

   - Uç Nokta Algılama ve Yanıt ilkesi için şunları seçin:
     - Platform: **Windows 10, Windows 11 ve Windows Server (Önizleme)**
     - Profil: Uç **nokta algılama ve yanıt (Önizleme)**

   >[!Note]
   > Bu profiller, Microsoft Intune ile Mobil Cihaz Yönetimi (MDM) aracılığıyla iletişim kurmanın yanı sıra Uç nokta istemcisi için Microsoft Defender kullanarak iletişim halinde olan cihazlar için de geçerlidir.
   >
   > Hedef kitlenizi ve gruplarınızı gereken şekilde gözden geçirmeyi sağlar.

4. **Oluştur**’u seçin.

5. **Temel Bilgiler** sayfasında, profil için bir ad ve açıklama girin, ardından **İleri**'yi seçin.

6. Yapılandırma **ayarları sayfasında** , bu profille yönetmek istediğiniz ayarları seçin. Bir ayar hakkında daha fazla bilgi edinmek için, ayarlarla ilgili bilgi iletişim  kutusunu genişletin ve daha fazla bilgi bağlantısına tıklayarak ayarın CSP bilgilerini satır içinde inceleyin.

   Ayarları yapılandırmayı tamamladığınızda **İleri**'yi seçin.

7. Atamalar **sayfasında** , bu profili alacak Azure AD gruplarını seçin. Profil atama hakkında daha fazla bilgi için bkz. [Kullanıcı ve cihaz profilleri atama](/mem/intune/configuration/device-profile-assign).

   Devam etmek **için Sonraki'yi** seçin.

   > [!TIP]
   >
   > - Atama filtreleri, Güvenlik Yapılandırma Yönetimi profilleri için desteklenmiyor.
   > - Uç *nokta yönetimi* için Microsoft Defender'a yalnızca Cihaz Nesneleri uygulanabilir. Kullanıcıları hedefleme desteklenmiyor.
   > - Yapılandırılan ilkeler hem Microsoft Intune uç Microsoft Intune için Microsoft Defender'a uygulanır

8. İlke oluşturma işlemini tamamlandıktan sonra Gözden Geçir **+ oluştur sayfasında Oluştur'a** **tıklayın**. Oluşturduğunuz profil için ilke türünü seçtiğinizde yeni profil listede görüntülenir.

9. İlkenin atanmalarını bekleyin ve ilkenin uygulandığını gösteren başarı göstergesini görüntülemeyi bekleyin.

10. [Get-MpPreference](/powershell/module/defender/get-mppreference#examples) komut yardımcı programını kullanarak ayarların istemciye yerel olarak uygulandığını doğru edebilirsiniz.
