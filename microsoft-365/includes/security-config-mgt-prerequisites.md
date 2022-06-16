---
title: dosyayı dahil et
description: dosyayı dahil et
author: mjcaparas
ms.service: microsoft-365-enterprise
ms.author: macapara
ms.openlocfilehash: 31008df3e43c99f3a97dad3dce037b96e3b0c4b5
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66116304"
---
## <a name="prerequisites"></a>Önkoşullar

Uç Nokta için Microsoft Defender Senaryosu için Güvenlik Yönetimi gereksinimleri için aşağıdaki bölümleri gözden geçirin:

### <a name="environment"></a>Ortam

Bir cihaz Uç Nokta için Microsoft Defender eklendiğinde:


- Cihaz, Intune için mobil cihaz yönetimi (MDM) kaydı olan mevcut bir Endpoint Manager iletişim durumu için ankete alınır
- Endpoint Manager varlığı olmayan cihazlar Güvenlik Yönetimi özelliğini etkinleştirir
- Henüz yoksa Azure Active Directory ile bir güven oluşturulur
- Endpoint Manager (Intune) ile iletişim kurmak ve ilkeleri almak için Azure Active Directory güven kullanılır
- Endpoint Manager'den ilke alma, Uç Nokta için Microsoft Defender tarafından cihazda zorlanır

### <a name="active-directory-requirements"></a>Active Directory Gereksinimleri

Etki alanına katılmış bir cihaz Azure Active Directory ile güven oluşturduğunda, bu senaryo *Karma Azure Active Directory Katılma* senaryosu olarak adlandırılır. Uç Nokta için Microsoft Defender için Güvenlik Yönetimi bu senaryoyu aşağıdaki gereksinimlerle tam olarak destekler:

- Azure Active Directory Bağlan (AAD Bağlan) Uç Nokta için Microsoft Defender'dan kullanılan kiracıyla eşitlenmelidir
- Karma Azure Active Directory Katılma ortamınızda yapılandırılmalıdır (Federasyon veya AAD Bağlan Eşitleme aracılığıyla)
- AAD Bağlan Eşitlemesi, Azure Active Directory ile *eşitleme için cihaz* nesnelerini kapsama eklemelidir (birleştirme için gerektiğinde)
- Eşitleme için AAD Bağlan kuralları [Server 2012 R2 için değiştirilmelidir (Server](/microsoft-365/security/defender-endpoint/troubleshoot-security-config-mgt?view=o365-worldwide#instructions-for-applying-computer-join-rule-in-aad-connect) 2012 R2 desteği gerektiğinde)
- Tüm cihazların Uç Nokta için Microsoft Defender barındıran kiracının Azure Active Directory kaydolması gerekir. Kiracılar arası senaryolar desteklenmez. 

### <a name="connectivity-requirements"></a>Bağlantı Gereksinimleri

Cihazların aşağıdaki uç noktalara erişimi olmalıdır:

- `enterpriseregistration.windows.net`- Azure AD kayıt için.
- `login.microsoftonline.com`- Azure AD kayıt için.
- `*.dm.microsoft.com` - Joker karakter kullanımı, kayıt, iade ve raporlama için kullanılan ve hizmet ölçeklendirildikçe değişebilen bulut hizmeti uç noktalarını destekler.

> [!Note]
> Kuruluşunuz Güvenli Yuva Katmanı (SSL) incelemesi kullanıyorsa uç noktalar incelemenin dışında tutulmalıdır.

### <a name="supported-platforms"></a>Desteklenen platformlar

Uç Nokta için Microsoft Defender güvenlik yönetimi ilkeleri aşağıdaki cihaz platformları için desteklenir:

- Windows 10 Professional/Enterprise ([KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) ile)
- Windows 11 Professional/Enterprise
- Down-Level [Cihazlar için Microsoft Defender ile R2 Windows Server 2012](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Down-Level [Cihazlar için Microsoft Defender ile Windows Server 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Windows Server 2019 ([KB5006744](https://support.microsoft.com/topic/october-19-2021-kb5006744-os-build-17763-2268-preview-e043a8a3-901b-4190-bb6b-f5a4137411c0) ile)
- Windows Server 2022 ([KB5006745](https://support.microsoft.com/topic/october-26-2021-kb5006745-os-build-20348-320-preview-8ff9319a-19e7-40c7-bbd1-cd70fcca066c) ile)

### <a name="licensing-and-subscriptions"></a>Lisanslama ve abonelikler

Uç Nokta için Microsoft Defender için güvenlik yönetimini kullanmak için şunlar gerekir:

- Microsoft 365 gibi Uç Nokta için Microsoft Defender lisansları veya yalnızca Uç Nokta için Microsoft Defender için tek başına lisans veren abonelik. Uç Nokta için Microsoft Defender lisansları veren bir abonelik, kiracınıza Microsoft Endpoint Manager yönetim merkezinin Uç nokta güvenlik düğümüne de erişim verir.

  > [!NOTE]  
  > **Özel durum**: Yalnızca Bulut için Microsoft Defender lisansının (eski adıyla Azure Güvenlik Merkezi) bir parçası olarak Uç Nokta için Microsoft Defender erişiminiz varsa, Uç Nokta için Microsoft Defender işlevselliği kullanılamaz.

Uç nokta güvenlik düğümü, cihazlarınız için Uç Nokta için Microsoft Defender yönetmek ve cihaz durumunu izlemek için ilkeleri yapılandırıp dağıtabileceğiniz yerdir.

Seçenekler hakkında güncel bilgi için bkz. [Uç Nokta için Microsoft Defender için en düşük gereksinimler](/microsoft-365/security/defender-endpoint/minimum-requirements?view=o365-worldwide&preserve-view=true).



## <a name="architecture"></a>Mimari

Aşağıdaki diyagram, Uç Nokta için Microsoft Defender güvenlik yapılandırma yönetimi çözümünün kavramsal bir gösterimidir.

:::image type="content" alt-text="Uç Nokta için Microsoft Defender güvenlik yapılandırma yönetimi çözümünün kavramsal gösterimi" source="../security/defender-endpoint/images/mde-architecture.png":::

1. cihazlar Uç Nokta için Microsoft Defender...

2. Her cihaz ve Azure AD arasında bir güven kurulur. Bir cihazın mevcut bir güveni olduğunda, bu kullanılır. Cihazlar kaydedilmediğinde yeni bir güven oluşturulur.

3. Cihazlar, Endpoint Manager ile iletişim kurmak için Azure AD Kimliklerini kullanır. Bu kimlik, Microsoft Endpoint Manager kullanıma aldıklarında hedeflenen ilkeleri cihazlara dağıtmasını sağlar.

4. Uç Nokta için Defender, ilkenin durumunu Endpoint Manager'a geri bildirir.

## <a name="which-solution-should-i-use"></a>Hangi çözümü kullanmalıyım?

Microsoft Endpoint Manager, cihazlarda Uç Nokta için Defender yapılandırmasını yönetmek için çeşitli yöntemler ve ilke türleri içerir.

Cihaz koruma gereksinimleriniz Uç Nokta için Defender'ı yönetmenin ötesine geçtiğinde cihaz uyumluluğu, *yönetilen uygulamalar*, *uygulama koruma ilkeleri* ve üçüncü taraf uyumluluk ve *mobil tehdit savunması* iş ortakları ile tümleştirme gibi cihazların korunmasına yardımcı olmak üzere Microsoft Endpoint Manager tarafından sağlanan ek özellikler hakkında bilgi edinmek için bkz. *Cihaz* korumasına [genel bakış](/mem/intune/protect/device-protect).

Aşağıdaki tablo, MDE ayarlarını yapılandırabilen ilkelerin farklı senaryolar tarafından yönetilen cihazlar tarafından desteklendiğini anlamanıza yardımcı olabilir. *Hem MDE güvenlik yapılandırması* hem de *Microsoft Endpoint Manager* için desteklenen bir ilke dağıttığınızda, bu ilkenin tek bir örneği yalnızca Uç Nokta için Microsoft Defender çalıştıran cihazlar ve Intune veya Intune tarafından yönetilen cihazlar tarafından işlenebilir Configuration Manager.

| Microsoft Endpoint Manager  | Iş yük -ünü |Ilkesi| MDE Güvenlik yapılandırması  |  Microsoft Endpoint Manager |
|----------------|----------------|-------------------|------------|
| Uç nokta güvenliği    | Antivirus   |     Antivirus           | ![Destekleniyor](../media/green-check.png)  | ![Destekleniyor](../media/green-check.png)  |
|                      | Antivirus   |   Virüsten Koruma Dışlamaları   | ![Destekleniyor](../media/green-check.png)  | ![Destekleniyor](../media/green-check.png)  |
|                      | Antivirus   | Windows Güvenliği Deneyimi |                        | ![Destekleniyor](../media/green-check.png)  |
|                      | Disk Şifrelemesi   |     Tümü |      | ![Destekleniyor](../media/green-check.png)  |
|                      | Güvenlik duvarı   | Güvenlik duvarı              | ![Destekleniyor](../media/green-check.png) | ![Destekleniyor](../media/green-check.png)  |
|                      | Güvenlik duvarı | Güvenlik Duvarı Kuralları                | ![Destekleniyor](../media/green-check.png) | ![Destekleniyor](../media/green-check.png)  |
|                      | Uç nokta algılama ve yanıt   | Uç nokta algılama ve yanıt | ![Destekleniyor](../media/green-check.png) | ![Destekleniyor](../media/green-check.png)  |
|                      | Saldırı yüzeyini azaltma    |   Tümü |          | ![Destekleniyor](../media/green-check.png)  |
|                      | Hesap Koruması       |    Tümü |     | ![Destekleniyor](../media/green-check.png)  |
|                      | Cihaz Uyumluluğu     |   Tümü |  | ![Destekleniyor](../media/green-check.png)  |
|                      | Koşullu Erişim    |   Tümü |  | ![Destekleniyor](../media/green-check.png)  |
|                      | Güvenlik temel hatları      |  Tümü |   | ![Destekleniyor](../media/green-check.png)  |

**Uç nokta güvenlik ilkeleri** , kuruluşunuzdaki cihazları korumaya odaklanan güvenlik yöneticileri tarafından kullanılmak üzere tasarlanmış ayrık ayar gruplarıdır.

- **Virüsten koruma** ilkeleri, Uç Nokta için Microsoft Defender bulunan güvenlik yapılandırmalarını yönetir. Bkz. Uç nokta güvenliği için  [virüsten koruma](/mem/intune/protect/endpoint-security-antivirus-policy) ilkesi.
- **Saldırı yüzeyi azaltma** ilkeleri, kuruluşunuzun siber tehditlere ve saldırılara karşı savunmasız olduğu yerleri en aza indirmeye odaklanır. Daha fazla bilgi için bkz. Windows Tehdit koruması belgelerindeki [saldırı yüzeyi azaltmaya genel bakış](/windows/security/threat-protection/microsoft-defender-atp/overview-attack-surface-reduction) ve uç nokta güvenliği için [saldırı yüzeyi azaltma](/mem/intune/protect/endpoint-security-asr-policy) ilkesi.
- **Uç nokta algılama ve yanıt** (EDR) ilkeleri, neredeyse gerçek zamanlı ve eyleme dönüştürülebilir gelişmiş saldırı algılamaları sağlayan Uç Nokta için Defender özelliklerini yönetir. Güvenlik analistleri EDR yapılandırmalarına bağlı olarak uyarıların önceliklerini etkili bir şekilde belirleyebilir, ihlal kapsamının tamamını görebilir ve tehditleri düzeltmek için yanıt eylemleri gerçekleştirebilir. Bkz. uç nokta güvenliği için [uç noktada algılama ve yanıtlama](/mem/intune/protect/endpoint-security-edr-policy) ilkesi.
- **Güvenlik duvarı** ilkeleri, cihazlarınızdaki Defender güvenlik duvarına odaklanır. Uç nokta güvenliği için güvenlik [duvarı](/mem/intune/protect/endpoint-security-firewall-policy) ilkesine bakın.
- **Güvenlik Duvarı Kuralları** belirli bağlantı noktaları, protokoller, uygulamalar ve ağlar dahil olmak üzere Güvenlik Duvarları için ayrıntılı kurallar yapılandırılır. Uç nokta güvenliği için güvenlik [duvarı](/mem/intune/protect/endpoint-security-firewall-policy) ilkesine bakın.
- **Güvenlik temelleri**, Defender, Edge veya Windows gibi farklı ürünler için Microsoft tarafından önerilen güvenlik duruşunu tanımlayan önceden yapılandırılmış güvenlik ayarlarını içerir. Varsayılan öneriler ilgili ürün ekiplerindendir ve önerilen güvenli yapılandırmayı cihazlara hızla dağıtmanızı sağlar. Ayarlar her temelde önceden yapılandırılmış olsa da, kuruluşunuzun güvenlik beklentilerini oluşturmak için bunların özelleştirilmiş örneklerini oluşturabilirsiniz. Bkz. Intune için [güvenlik temelleri](/mem/intune/protect/security-baselines).

## <a name="configure-your-tenant-to-support-microsoft-defender-for-endpoint-security-configuration-management"></a>Kiracınızı Uç Nokta için Microsoft Defender Güvenlik Yapılandırma Yönetimi'ne destek olacak şekilde yapılandırma

Microsoft Endpoint Manager yönetim merkezi aracılığıyla Uç Nokta için Microsoft Defender güvenlik yapılandırması yönetimini desteklemek için, her konsolun içinden aralarındaki iletişimi etkinleştirmeniz gerekir.

1. [Microsoft 365 Defender portalında](https://security.microsoft.com/) oturum açın ve **Ayarlar** >  **Endpoints****Yapılandırma Yönetimi** > **Zorlama Kapsamı'na** gidin ve güvenlik ayarları yönetimi için platformları  >  etkinleştirin:

   :::image type="content" source="../media/security-settings-mgt.png" alt-text="Defender konsolunda Uç Nokta için Microsoft Defender ayarları yönetimini etkinleştirin.":::
    
1. Pilot Modu ve Configuration Manager yetkili ayarlarını kuruluşunuzun gereksinimlerine uyacak şekilde yapılandırın:

   :::image type="content" source="../media/pilot-CMAuthority-mde-settings-management-defender.png" alt-text="Microsoft 365 Defender portalında Uç nokta ayarları yönetimi için Pilot modu yapılandırın.":::
   
  > [!TIP]
  > Az sayıda cihazda dağıtımınızı test etmek ve doğrulamak için pilot modu ve uygun cihaz etiketlerini kullanın. Pilot modu kullanılmadan, yapılandırılan kapsama giren tüm cihazlar otomatik olarak kaydedilir.

1. İlgili kullanıcıların Microsoft Endpoint Manager uç nokta güvenlik ayarlarını yönetme izinlerine sahip olduğundan emin olun veya Defender portalında bir rol yapılandırarak bu izinleri verin. **Ayarlar** >  **Roles** > **Öğe ekle'ye** gidin:

   :::image type="content" source="../media/add-role-in-mde.png" alt-text="Defender portalında yeni bir rol oluşturun.":::

   > [!TIP]
   > Mevcut rolleri değiştirebilir ve Uç Nokta için Microsoft Defender'de ek roller oluşturmak yerine gerekli izinleri ekleyebilirsiniz

1. Rolü yapılandırırken kullanıcıları ekleyin ve **Microsoft Endpoint Manager'da Uç nokta güvenlik ayarlarını yönet'i seçtiğinizden** emin olun:

   :::image type="content" source="../media/add-role.png" alt-text="Kullanıcılara ayarları yönetme izinleri verin.":::

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) oturum açın.

1. **Uç nokta güvenliği** >  **Uç Nokta için Microsoft Defender'yi** seçin ve **Uç Nokta Güvenlik Yapılandırmalarını zorlamak için Uç Nokta için Microsoft Defender İzin Ver 'i Açık** olarak **ayarlayın.**

   :::image type="content" source="../media/enable-mde-settings-management-mem.png" alt-text="Microsoft Endpoint Manager yönetim merkezinde Uç Nokta için Microsoft Defender ayarları yönetimini etkinleştirin.":::

   Bu seçeneği *Açık* olarak ayarladığınızda, Microsoft Endpoint Manager tarafından yönetilmeyen Uç Nokta için Microsoft Defender platform kapsamındaki tüm cihazlar Uç Nokta için Microsoft Defender eklemeye hak kazanacaktır.

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>Cihazları Uç Nokta için Microsoft Defender ekleme

Uç Nokta için Microsoft Defender, cihazları eklemek için çeşitli seçenekleri destekler. Geçerli yönergeler için Uç Nokta için Defender belgelerindeki [Windows cihazlar için ekleme araçları ve yöntemleri](/microsoft-365/security/defender-endpoint/security-config-management) bölümüne bakın.



## <a name="co-existence-with-microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager ile birlikte yaşama
Bazı ortamlarda, [Configuration Manager kiracı iliştirilmiş](/mem/configmgr/tenant-attach/endpoint-security-get-started) Uç Nokta için Microsoft Defender için Güvenlik Yönetimi'nin kullanılması istenebilir. Her ikisini de kullanırsanız, birden fazla kanal kullanmak çakışmalar ve istenmeyen sonuçlar için fırsat oluşturduğundan, ilkeyi tek bir kanal üzerinden denetlemeniz gerekir.

Bunu desteklemek için *, Configuration Manager seçeneğini Kapalı olarak değiştirerek Güvenlik ayarlarını yapılandırın*.  [Microsoft 365 Defender portalında](https://security.microsoft.com/) oturum açın ve **Ayarlar** >  **Endpoints** > **Yapılandırma Yönetimi** > **Zorlama Kapsamı'na** gidin:

:::image type="content" source="../media/manage-security-settings-cfg-mgr.png" alt-text="Configuration Manager ayarını kullanarak güvenlik ayarlarını yönetin.":::

>[!NOTE]
>Configuration Manager ile Uç Nokta için Microsoft Defender için Güvenlik Yönetimi kullanılırken, uç nokta güvenlik ilkesi tek bir denetim düzlemine yalıtılmalıdır. İlkeyi her iki kanal üzerinden denetlemek çakışmalara ve istenmeyen sonuçlara neden olabilir.


## <a name="create-azure-ad-groups"></a>Azure AD Grupları Oluşturma

Cihazlar Uç Nokta için Defender'a eklendikten sonra, Uç Nokta için Microsoft Defender için ilke dağıtımını desteklemek üzere cihaz grupları oluşturmanız gerekir.

Uç Nokta için Microsoft Defender kaydedilmiş ancak Intune veya Configuration Manager tarafından yönetilmeyen cihazları tanımlamak için:

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) oturum açın.

2. **Cihazlar** > **Tüm cihazlar'a** gidin ve ardından cihazların görünümünü sıralamak için **Yönetilen** sütununu seçin.

   Uç Nokta için Microsoft Defender eklenen ve kayıtlı olan ancak Intune tarafından yönetilmeyen cihazlar *, Yönetilen* sütununda **Uç Nokta için Microsoft Defender** görüntüler. Bunlar, Uç Nokta için Microsoft Defender için güvenlik yönetimi ilkesi alabilen cihazlardır.

   Ayrıca Uç Nokta için Microsoft Defender için güvenlik yönetimi kullanan cihazlar için iki etiket bulacaksınız:

   - **MDEJoined** - Bu senaryonun bir parçası olarak dizine katılmış cihazlara eklendi.
   - **MDEManaged** - Güvenlik yönetimi senaryolarını etkin olarak kullanan cihazlara eklenir. Uç Nokta için Defender güvenlik yapılandırmasını yönetmeyi durdurursa bu etiket cihazdan kaldırılır.

Bu cihazlar için [grupları Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal) veya [Microsoft Endpoint Manager yönetim merkezinden](/mem/intune/fundamentals/groups-add) oluşturabilirsiniz.

## <a name="deploy-policy"></a>İlke dağıtma

Uç Nokta için Microsoft Defender tarafından yönetilen cihazları içeren bir veya daha fazla Azure AD grubu oluşturduktan sonra, Uç Nokta için Microsoft Defender için Güvenlik Yönetimi için aşağıdaki ilkeleri oluşturabilir ve bu gruplara dağıtabilirsiniz:

- Antivirus
- Güvenlik duvarı
- Güvenlik Duvarı Kuralları
- Uç Nokta Algılama ve Yanıt

> [!TIP]
> Aynı ayarı yöneten birden çok ilkeyi bir cihaza dağıtmaktan kaçının.
>
> Microsoft Endpoint Manager her bir uç nokta güvenlik ilkesi türünün birden çok örneğinin aynı cihaza dağıtılmasını ve her ilke örneğinin cihaz tarafından ayrı olarak alınmasını destekler. Bu nedenle, bir cihaz aynı ayar için farklı ilkelerden ayrı yapılandırmalar alabilir ve bu da çakışmaya neden olur. Bazı ayarlar (Virüsten Koruma Dışlamaları gibi) istemcide birleştirilir ve başarıyla uygulanır.

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) oturum açın.

2. **Uç nokta güvenliği'ne** gidin ve yapılandırmak istediğiniz ilke türünü (Virüsten Koruma veya Güvenlik Duvarı) ve ardından **İlke Oluştur'u** seçin.

3. Aşağıdaki özellikleri veya seçtiğiniz ilke türünü girin:

   - Virüsten koruma ilkesi için şunları seçin:
     - Platform: **Windows 10, Windows 11 ve Windows Sunucusu (Önizleme)**
     - Profil: **Microsoft Defender Virüsten Koruma (Önizleme)**

   - Güvenlik duvarı ilkesi için şunları seçin:
     - Platform: **Windows 10, Windows 11 ve Windows Sunucusu (Önizleme)**
     - Profil: **Microsoft Defender Güvenlik Duvarı (Önizleme)**

   - Güvenlik Duvarı Kuralları ilkesi için şunları seçin:
     - Platform: **Windows 10, Windows 11 ve Windows Sunucusu (Önizleme)**
     - Profil: **Microsoft Defender Güvenlik Duvarı Kuralları (Önizleme)**

   - Uç Nokta Algılama ve Yanıt ilkesi için şunları seçin:
     - Platform: **Windows 10, Windows 11 ve Windows Sunucusu (Önizleme)**
     - Profil: **Uç nokta algılama ve yanıt (Önizleme)**

   >[!Note]
   > Bu profiller, Microsoft Intune ile Mobil Cihaz Yönetimi (MDM) üzerinden iletişim kurabilen cihazlara ve Uç Nokta için Microsoft Defender istemcisini kullanarak iletişimde bulunan cihazlara uygulanır.
   >
   > Hedeflemenizi ve gruplarınızı gerektiği gibi gözden geçirdiğinizden emin olun.

4. **Oluştur**’u seçin.

5. **Temel Bilgiler** sayfasında, profil için bir ad ve açıklama girin, ardından **İleri**'yi seçin.

6. **Yapılandırma ayarları** sayfasında, bu profille yönetmek istediğiniz ayarları seçin. Bir ayar hakkında daha fazla bilgi edinmek için bilgi iletişim kutusunu genişletin ve daha *fazla bilgi edinin* bağlantısını seçerek ilgili ayarın CSP bilgilerini satır içi belgelerde görüntüleyin.

   Ayarları yapılandırmayı tamamladığınızda **İleri**'yi seçin.

7. **Atamalar** sayfasında, bu profili alacak Azure AD gruplarını seçin. Profil atama hakkında daha fazla bilgi için bkz. [Kullanıcı ve cihaz profilleri atama](/mem/intune/configuration/device-profile-assign).

   Devam etmek için **İleri'yi** seçin.

   > [!TIP]
   >
   > - Atama filtreleri Güvenlik Yapılandırma Yönetimi profilleri için desteklenmez.
   > - Uç Nokta için Microsoft Defender yönetimi için yalnızca *Cihaz Nesneleri* geçerlidir. Kullanıcıları hedefleme desteklenmez.
   > - Yapılandırılan ilkeler hem Microsoft Intune hem de Uç Nokta için Microsoft Defender istemcileri için geçerlidir

8. İlke oluşturma işlemini tamamlayın ve **gözden geçir + oluştur** sayfasında **Oluştur'u** seçin. Oluşturduğunuz profil için ilke türünü seçtiğinizde yeni profil listede görüntülenir.

9. İlkenin atanacağını bekleyin ve ilkenin uygulandığına ilişkin başarı göstergesini görüntüleyin.

10. [Get-MpPreference](/powershell/module/defender/get-mppreference#examples) komut yardımcı programını kullanarak ayarların istemciye yerel olarak uygulandığını doğrulayabilirsiniz.
