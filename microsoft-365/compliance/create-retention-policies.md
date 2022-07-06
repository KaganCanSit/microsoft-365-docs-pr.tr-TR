---
title: Bekletme ilkelerini kullanarak içeriği otomatik olarak saklama veya silme
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Kullanıcıların e-posta, belgeler ve konuşmalarla oluşturduğu içeriğin denetimini verimli bir şekilde korumak için bekletme ilkesi kullanın. İstediğinizi koruyun ve istemediğinizden kurtulun.
ms.openlocfilehash: 0f0fa2da9c41700216b0142827897980870f006d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627679"
---
# <a name="create-and-configure-retention-policies"></a>Bekletme ilkeleri oluşturma ve yapılandırma

>*[Güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

İçeriği saklamaya, içeriği silmeye veya saklamaya ve sonra silmeye proaktif olarak karar vererek kuruluşunuzun verilerini yönetmek için bir bekletme ilkesi kullanın.

Bekletme ilkesi, kapsayıcı düzeyinde aynı bekletme ayarlarını bu kapsayıcıdaki içerik tarafından otomatik olarak devralınacak şekilde atayarak bunu çok verimli bir şekilde yapmanıza olanak tanır. Örneğin, SharePoint sitelerindeki tüm öğeler, kullanıcıların Exchange posta kutularındaki tüm e-posta iletileri, Microsoft Teams ile kullanılan ekipler için tüm kanal iletileri. Kapsayıcı düzeyinde bekletme ilkesi mi yoksa öğe düzeyinde bekletme etiketi mi kullanacağınızdan emin değilseniz bkz [. Bekletme ilkeleri ve bekletme etiketleri](retention.md#retention-policies-and-retention-labels).

Bekletme ilkeleri ve Microsoft 365'te bekletmenin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin](retention.md).

> [!NOTE]
> Bu sayfadaki bilgiler uyumluluk yöneticilerine yöneliktir. Yönetici değilseniz ve kullandığınız uygulamalar için bekletme ilkelerinin nasıl yapılandırıldığını anlamak istiyorsanız yardım masanıza, BT departmanınıza veya yöneticinize başvurun. Teams sohbetlerinde ve kanal iletilerinde bekletme ilkeleriyle ilgili iletiler görüyorsanız, [Bekletme ilkeleriyle ilgili Teams iletilerini](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b) gözden geçirmeniz yararlı olabilir.

## <a name="before-you-begin"></a>Başlamadan önce

Kuruluşunuzun genel yöneticisi, bekletme ilkeleri oluşturmak ve düzenlemek için tam izinlere sahiptir. Genel yönetici olarak oturum açmadıysanız [veri yaşam döngüsü yönetimi için izin bilgilerine](get-started-with-data-lifecycle-management.md#permissions-for-retention-policies-and-retention-labels) bakın.

Bekletme ilkenizi oluşturmadan önce **uyarlamalı** mı yoksa **statik** mi olacağını belirleyin. Daha fazla bilgi için bkz. [Bekletme için uyarlamalı veya statik ilke kapsamları](retention.md#adaptive-or-static-policy-scopes-for-retention). Uyarlamalı bir ilke kullanmaya karar verirseniz, bekletme ilkenizi oluşturmadan önce bir veya daha fazla uyarlamalı kapsam oluşturmanız ve bekletme ilkesi oluşturma işlemi sırasında bunları seçmeniz gerekir. Yönergeler için bkz [. Uyarlamalı kapsamlar için yapılandırma bilgileri](retention-settings.md#configuration-information-for-adaptive-scopes).

## <a name="create-and-configure-a-retention-policy"></a>Bekletme ilkesi oluşturma ve yapılandırma

Bekletme ilkesi, bekletme ilkesinde "konumlar" olarak tanımlanan birden çok hizmeti destekleyebilse de, desteklenen tüm konumları içeren tek bir bekletme ilkesi oluşturamazsınız:

- Exchange e-postası
- SharePoint sitesi
- OneDrive hesapları
- Microsoft 365 grupları
- Skype Kurumsal
- Exchange ortak klasörleri
- Teams kanal iletileri
- Teams sohbetleri
- Teams özel kanal iletileri
- Yammer topluluk iletileri
- Yammer kullanıcı iletileri

Bekletme ilkesi oluştururken Teams veya Yammer konumlarını seçerseniz, diğer konumlar otomatik olarak dışlanır. Bu, izleyebileceğiniz yönergelerin Teams veya Yammer konumlarını dahil etmeniz gerekip gerekmediğine bağlı olduğu anlamına gelir:

- [Teams konumları için bekletme ilkesi yönergeleri](#retention-policy-for-teams-locations)
- [Yammer konumları için bekletme ilkesi yönergeleri](#retention-policy-for-yammer-locations)
- [Teams ve Yammer dışındaki konumlar için bekletme ilkesi yönergeleri](#retention-policy-for-locations-other-than-teams-and-yammer)

> [!NOTE]
> Statik ilkeler yerine uyarlamalı ilkeler kullandığınızda, hem Teams hem de Yammer konumlarını içerecek şekilde tek bir bekletme ilkesi yapılandırabilirsiniz. Teams ve Yammer konumlarının kendi bekletme ilkelerini gerektirdiği statik ilkeler için bu durum geçerli değildir.

Birden fazla bekletme ilkeniz varsa ve bekletme etiketlerini de kullandığınızda, aynı içeriğe birden çok bekletme ayarı uygulandığında sonucu anlamak için bkz. [Bekletme ilkeleri veya öncelik nelerdir?](retention.md#the-principles-of-retention-or-what-takes-precedence)

### <a name="retention-policy-for-teams-locations"></a>Teams konumları için bekletme ilkesi

> [!NOTE]
> Bekletme ilkeleri artık şu anda önizleme aşamasında olan [paylaşılan kanalları](/MicrosoftTeams/shared-channels) destekliyor. **Teams kanalı ileti** konumu için bekletme ayarlarını yapılandırdığınızda, bir ekibin paylaşılan kanalları varsa, bu kişiler bekletme ayarlarını üst ekibinden devralır.

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/) **Veri yaşam döngüsü yönetimi** > **Bekletme İlkeleri'ni** seçin.

2. Bekletme ilkesi oluştur yapılandırmasını başlatmak için **Yeni bekletme ilkesi'ni** seçin ve yeni bekletme ilkenizi adlandırın.

3. **Oluşturulacak bekletme ilkesinin türünü seçin** sayfasında, [Başlamadan önce](#before-you-begin) yönergelerinden yaptığınız seçime bağlı olarak **Uyarlamalı** veya **Statik'i** seçin. Uyarlamalı kapsamlar oluşturmadıysanız **Uyarlamalı'yı** seçebilirsiniz, ancak seçilecek uyarlamalı kapsamlar olmayacağından yapılandırmayı bu seçenekle tamamlayamazsınız.

4. Seçtiğiniz kapsama bağlı olarak:
    
    - **Uyarlamalı**: **Uyarlamalı ilke kapsamlarını ve konumlarını seçin** sayfasında **Kapsam ekle'yi** seçin ve oluşturulmuş bir veya daha fazla uyarlamalı kapsam seçin. Ardından bir veya daha fazla konum seçin. Seçebileceğiniz konumlar eklenen [kapsam türlerine](retention-settings.md#configuration-information-for-adaptive-scopes) bağlıdır. Örneğin, yalnızca bir **Kullanıcı** kapsam türü eklediyseniz **Teams sohbetlerini** seçebilirsiniz ancak **Teams kanal iletilerini** seçemezsiniz. 
    
    - **Statik'i** seçtiyseniz: **İlkenin uygulanacağı konumları seçin** sayfasında Teams için bir veya daha fazla konum seçin:
        - **Teams kanal iletisi**: Standart ve paylaşılan kanal sohbetlerinden, standart ve paylaşılan kanal toplantılarından gelen iletiler, ancak kendi ilke konumlarına sahip [özel kanallardan](/microsoftteams/private-channels) değil.
        - **Teams sohbetleri**: Özel 1:1 sohbetlerinden, grup sohbetlerinden ve toplantı sohbetlerinden gelen iletiler.
        - **Teams özel kanal iletileri**: Özel kanal sohbetlerinden ve özel kanal toplantılarından gelen iletiler.
        
       Varsayılan olarak [, tüm ekipler ve tüm kullanıcılar seçilir](retention-settings.md#a-policy-that-applies-to-entire-locations), ancak [**Seç** ve **Dışla** seçeneklerini](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions) belirleyerek bunu iyileştirebilirsiniz.

5. **İçeriği korumak mı, silmek mi yoksa her iki sayfayı da silmek mi istediğinize karar ver** için, içeriği korumak ve silmek için yapılandırma seçeneklerini belirtin.

   İçeriği yalnızca silmeden saklayan, belirli bir süre sonra saklayan ve silecek veya yalnızca belirli bir süreden sonra içeriği silecek bir bekletme ilkesi oluşturabilirsiniz. Daha fazla bilgi için bkz. [İçeriği saklama ve silme ayarları](retention-settings.md#settings-for-retaining-and-deleting-content).

6. Yapılandırmayı tamamlayın ve ayarlarınızı kaydedin.

Teams için bekletme ilkelerini kullanma ve son kullanıcı deneyimini anlama konusunda rehberlik için Teams belgelerinden [Microsoft Teams için bekletme ilkelerini yönetme](/microsoftteams/retention-policies) bölümüne bakın.

Örnek kılavuzlarla bekletme ve zamanlama bilgileri için hangi ileti öğelerinin desteklendiği de dahil olmak üzere, teams için bekletmenin nasıl çalıştığı hakkında teknik ayrıntılar için bkz. [Microsoft Teams için bekletme hakkında bilgi edinin](retention-policies-teams.md).

#### <a name="known-configuration-issues"></a>Bilinen yapılandırma sorunları

- Öğelerin en son değiştirildiği saklama süresini başlatma seçeneğini belirleyebilirsiniz ancak **öğeler oluşturulduğunda** değeri her zaman kullanılır. Düzenlenen iletiler için, bu önceden düzenlenmiş iletinin ne zaman oluşturulduğunu belirlemek için özgün iletinin bir kopyası özgün zaman damgasıyla birlikte kaydedilir ve düzenlenen iletinin daha yeni bir zaman damgası vardır.

- Teams sohbetleri konumu için **Düzenle'yi** seçtiğinizde konukları ve posta kutusu olmayan kullanıcıları görebilirsiniz. Bekletme ilkeleri bu kullanıcılar için tasarlanmamıştır, bu nedenle bunları seçmeyin.


#### <a name="additional-retention-policy-needed-to-support-teams"></a>Teams'i desteklemek için ek saklama ilkesi gerekiyor

Teams yalnızca sohbetlerden ve kanal iletilerinden daha fazlasıdır. Bir Microsoft 365 grubundan (eski adıyla Office 365 grubu) oluşturulmuş ekipleriniz varsa, **Microsoft 365 Grupları** konumunu kullanarak bu Microsoft 365 grubunu içeren bir bekletme ilkesi de yapılandırmanız gerekir. Bu bekletme ilkesi, grubun posta kutusu, sitesi ve dosyalarındaki içerik için geçerlidir.

Microsoft 365 grubuna bağlı olmayan ekip siteleriniz varsa, Teams'de dosyaları saklamak ve silmek için **SharePoint sitelerini** veya **OneDrive hesap** konumlarını içeren bir bekletme ilkesine ihtiyacınız vardır:

- Sohbette paylaşılan dosyalar, dosyayı paylaşan kullanıcının OneDrive hesabında depolanır.

- Kanallara yüklenen dosyalar ekip için SharePoint sitesinde depolanır.

> [!TIP]
> Ekip için SharePoint sitesini ve Ekipteki kullanıcıların OneDrive hesaplarını seçerek bir Microsoft 365 grubuna bağlı olmadığında yalnızca belirli bir ekibin dosyalarına bekletme ilkesi uygulayabilirsiniz.

Microsoft 365 gruplarına, SharePoint sitelerine veya OneDrive hesaplarına uygulanan bir bekletme ilkesi, söz konusu iletiler silinmeden önce Teams sohbetinde veya kanal iletisinde başvuruda bulunan bir dosyayı silebilir. Bu senaryoda, dosya Hala Teams iletisinde görüntülenir, ancak kullanıcılar dosyayı seçtiğinde bir "Dosya bulunamadı" hatası alır. Bu davranış bekletme ilkelerine özgü değildir ve bir kullanıcı sharepoint veya OneDrive'dan el ile bir dosya silerse de oluşabilir.

### <a name="retention-policy-for-yammer-locations"></a>Yammer konumları için bekletme ilkesi

> [!NOTE]
> Yammer için bekletme ilkeleri şu anda bir bekletme ilkesi sonucunda iletiler silindiğinde kullanıcıları bilgilendirmez.
>
> Bu özelliği kullanmak için Yammer ağınızın Karma Mod değil [Yerel Mod](/yammer/configure-your-yammer-network/overview-native-mode) olması gerekir.

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/) **Veri yaşam döngüsü yönetimi** > **Bekletme İlkeleri'ni** seçin.

2. **Yeni bir bekletme ilkesi** oluşturmak için Yeni bekletme ilkesi'ni seçin.

3. **Oluşturulacak bekletme ilkesinin türünü seçin** sayfasında, [Başlamadan önce](#before-you-begin) yönergelerinden yaptığınız seçime bağlı olarak **Uyarlamalı** veya **Statik'i** seçin. Uyarlamalı kapsamlar oluşturmadıysanız **Uyarlamalı'yı** seçebilirsiniz, ancak seçilecek uyarlamalı kapsamlar olmayacağından yapılandırmayı bu seçenekle tamamlayamazsınız.

4. Seçtiğiniz kapsama bağlı olarak:
    
    - **Uyarlamalı**: **Uyarlamalı ilke kapsamlarını ve konumlarını seçin** sayfasında **Kapsam ekle'yi** seçin ve oluşturulmuş bir veya daha fazla uyarlamalı kapsam seçin. Ardından bir veya daha fazla konum seçin. Seçebileceğiniz konumlar eklenen [kapsam türlerine](retention-settings.md#configuration-information-for-adaptive-scopes) bağlıdır. Örneğin, yalnızca bir **Kullanıcı** kapsam türü eklediyseniz **Yammer kullanıcı iletilerini** seçebilirsiniz ancak **Yammer topluluk iletilerini** seçemezsiniz. 
    
    - **Statik'i** seçtiyseniz: **İlkenin uygulanacağı konumları seçin** sayfasında Yammer için konumlardan birini veya her ikisini de açın: **Yammer topluluk iletisi** ve **Yammer kullanıcı iletileri**.
        
        Varsayılan olarak tüm topluluklar ve kullanıcılar seçilir, ancak dahil edilecek veya dışlanacak toplulukları ve kullanıcıları belirterek bunu iyileştirebilirsiniz.
        
        Yammer kullanıcı iletileri için: 
        - **Varsayılan ayarı Tüm kullanıcılar** olarak bırakırsanız Azure B2B konuk kullanıcıları dahil değildir. 
        - **Tüm kullanıcılar** için **Düzenle'yi** seçerseniz, hesabını biliyorsanız dış kullanıcılara bir bekletme ilkesi uygulayabilirsiniz.

5. **İçeriği korumak mı, silmek mi yoksa her iki sayfayı da silmek mi istediğinize karar ver** için, içeriği korumak ve silmek için yapılandırma seçeneklerini belirtin. 
    
    İçeriği yalnızca silmeden saklayan, belirli bir süre sonra saklayan ve silecek veya yalnızca belirli bir süreden sonra içeriği silecek bir bekletme ilkesi oluşturabilirsiniz. Daha fazla bilgi için bkz. [İçeriği saklama ve silme ayarları](retention-settings.md#settings-for-retaining-and-deleting-content).

6. Yapılandırmayı tamamlayın ve ayarlarınızı kaydedin.

Yammer'da bekletme ilkelerinin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [Yammer için bekletme hakkında bilgi edinin](retention-policies-yammer.md).

#### <a name="additional-retention-policies-needed-to-support-yammer"></a>Yammer'ı desteklemek için gereken ek saklama ilkeleri

Yammer yalnızca topluluk iletilerinden ve özel iletilerden daha fazlasıdır. Yammer ağınızda e-posta iletilerini korumak ve silmek için, **Microsoft 365 Grupları** konumunu kullanarak Yammer için kullanılan tüm Microsoft 365 gruplarını içeren ek bir bekletme ilkesi yapılandırın.

Bu konum, Yammer topluluklarına yüklenen dosyaları da içerir. Bu dosyalar Yammer topluluğu için gruba bağlı SharePoint sitesinde depolanır.

SharePoint sitelerine uygulanan bir bekletme ilkesi, bu iletiler silinmeden önce Yammer iletisinde başvuruda bulunan bir dosyayı silebilir. Bu senaryoda, dosya Yammer iletisinde görüntülenmeye devam eder, ancak kullanıcılar dosyayı seçtiğinde "Dosya bulunamadı" hatası alır. Bu davranış bekletme ilkelerine özgü değildir ve kullanıcı SharePoint'ten bir dosyayı el ile silerse de oluşabilir.

### <a name="retention-policy-for-locations-other-than-teams-and-yammer"></a>Teams ve Yammer dışındaki konumlar için bekletme ilkesi

Bu hizmetlerden herhangi biri için geçerli olan bekletme ilkeleri için aşağıdaki yönergeleri kullanın:

- Exchange: E-posta ve ortak klasörler
- SharePoint: Siteler
- OneDrive: Hesaplar
- Microsoft 365 grupları
- Skype Kurumsal

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/) **Veri yaşam döngüsü yönetimi** > **Bekletme İlkeleri'ni** seçin.

2. Bekletme ilkesi oluştur yapılandırmasını başlatmak için **Yeni bekletme ilkesi'ni** seçin ve yeni bekletme ilkenizi adlandırın.

3. **Oluşturulacak bekletme ilkesinin türünü seçin** sayfasında, [Başlamadan önce](#before-you-begin) yönergelerinden yaptığınız seçime bağlı olarak **Uyarlamalı** veya **Statik'i** seçin. Uyarlamalı kapsamlar oluşturmadıysanız **Uyarlamalı'yı** seçebilirsiniz, ancak seçilecek uyarlamalı kapsamlar olmayacağından yapılandırmayı bu seçenekle tamamlayamazsınız. Uyarlamalı ilkeler, Exchange ortak klasörlerinin veya Skype Kurumsal konumlarını desteklemez.

4. Seçtiğiniz kapsama bağlı olarak:
    
    - **Uyarlamalı**: **Uyarlamalı ilke kapsamlarını ve konumlarını seçin** sayfasında **Kapsam ekle'yi** seçin ve oluşturulmuş bir veya daha fazla uyarlamalı kapsam seçin. Ardından bir veya daha fazla konum seçin. Seçebileceğiniz konumlar eklenen [kapsam türlerine](retention-settings.md#configuration-information-for-adaptive-scopes) bağlıdır. Örneğin, yalnızca bir **Kullanıcı** kapsam türü eklediyseniz **, Exchange e-postasını** seçebilirsiniz ancak **SharePoint sitelerini** seçemezsiniz. 
    
    - **Statik'i** seçtiyseniz: **Konumları seçin** sayfasında, Teams ve Yammer konumları dışında konumlardan herhangi birini açın veya kapatın. Her konum için, [ilkeyi konumun tamamına uygulamak için](retention-settings.md#a-policy-that-applies-to-entire-locations) varsayılan olarak bırakabilir veya [dahil etme ve dışlamaları belirtebilirsiniz](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions).
    
    Konumlara özgü bilgiler:
    - [Exchange e-postası ve Exchange ortak klasörleri](retention-settings.md#configuration-information-for-exchange-email-and-exchange-public-folders)
    - [SharePoint siteleri ve OneDrive hesapları](retention-settings.md#configuration-information-for-sharepoint-sites-and-onedrive-accounts)
    - [Microsoft 365 Grupları](retention-settings.md#configuration-information-for-microsoft-365-groups)
    - [Skype Kurumsal](retention-settings.md#configuration-information-for-skype-for-business)

5. **İçeriği korumak mı, silmek mi yoksa her iki sayfayı da silmek mi istediğinize karar ver** için, içeriği korumak ve silmek için yapılandırma seçeneklerini belirtin.
    
    İçeriği yalnızca silmeden saklayan, belirli bir süre sonra saklayan ve silecek veya yalnızca belirli bir süreden sonra içeriği silecek bir bekletme ilkesi oluşturabilirsiniz. Daha fazla bilgi için bkz. Bu sayfadaki [içeriği saklama ve silme ayarları](retention-settings.md#settings-for-retaining-and-deleting-content) .

6. Yapılandırmayı tamamlayın ve ayarlarınızı kaydedin.

## <a name="how-long-it-takes-for-retention-policies-to-take-effect"></a>Bekletme ilkelerinin geçerli olması ne kadar sürer?

Bir bekletme ilkesi oluşturup gönderdiğinizde, bekletme ilkesinin uygulanması yedi güne kadar sürebilir:
  
![Bekletme ilkesinin ne zaman etkin olduğunu açıklayan diyagram.](../media/retention-policy-timings.png)

İlk olarak, bekletme ilkesinin seçtiğiniz konumlara dağıtılması ve ardından içeriğe uygulanması gerekir. Bekletme ilkesinin dağıtım durumunu her zaman Microsoft Purview uyumluluk portalı **Bekletme ilkeleri** sayfasından seçerek de kontrol edebilirsiniz. Açılır bölmeden, duruma **(Hata)** eklendiğini görürseniz ve konumların ayrıntılarında ilkeyi dağıtmanın veya ilkeyi yeniden dağıtmayı denemenin beklenenden uzun sürdüğünü belirten bir ileti görürseniz, ilke dağıtımını yeniden denemek için [Set-AppRetentionCompliancePolicy](/powershell/module/exchange/set-appretentioncompliancepolicy) veya [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) PowerShell komutunu çalıştırmayı deneyin:

1. [Güvenlik & Uyumluluğu PowerShell'e bağlanın](/powershell/exchange/connect-to-scc-powershell).

2. Aşağıdaki komutlardan birini çalıştırın:
    
    - İlke konumları **için Teams özel kanal iletileri**, **Yammer kullanıcı iletileri** ve **Yammer topluluk iletileri**:
    
        ```PowerShell
        Set-AppRetentionCompliancePolicy -Identity <policy name> -RetryDistribution
        ```
    
    - **Exchange e-postası**, **SharePoint siteleri** ve **Teams kanal iletileri** gibi diğer tüm ilke konumları için:
    
        ```PowerShell
        Set-RetentionCompliancePolicy -Identity <policy name> -RetryDistribution
        ```

## <a name="updating-retention-policies"></a>Bekletme ilkelerini güncelleştirme

Bekletme ilkesindeki ayarlar içeriğe zaten uygulandığında, ilke yapılandırmasında yapılan bir değişiklik, yeni tanımlanan içeriğe ek olarak bu içeriğe otomatik olarak uygulanır.

bekletme ilkesinin adı, kapsam türü (uyarlamalı veya statik) ve bekletme süresi dışında bekletme ayarlarını içeren ilke oluşturulduktan ve kaydedildikten sonra bazı ayarlar değiştirilemez.

## <a name="next-steps"></a>Sonraki adımlar

Exchange, SharePoint, OneDrive veya Microsoft 365 Grupları için bazı öğeler yapılandırdığınız bekletme ilkesi ayarlarından farklı bekletme ayarlarına ihtiyaç duyuyorsa[, bu özel durumlar için bekletme etiketleri oluşturun](create-retention-labels-data-lifecycle-management.md).

Bununla birlikte, iş, yasal veya mevzuat kaydı tutma gereksinimleri için yüksek değerli öğeleri yönetmek istiyorsanız [, bekletme etiketleri oluşturmak ve yönetmek için dosya planını kullanın](file-plan-manager.md).
