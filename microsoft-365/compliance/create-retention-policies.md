---
title: İçeriği otomatik olarak korumak veya silmek için bekletme ilkeleri oluşturma ve yapılandırma
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
description: Kullanıcıların e-posta, belgeler ve konuşmalarda kendi oluşturanın içeriğinin kontrolünü etkin bir şekilde tutmak için bekletme ilkesi kullanın. Istemediklerden kurtulun ve istemediklerden kurtulun.
ms.openlocfilehash: ddd0553405aa92a1eb7a7978398392b780a0a2ea
ms.sourcegitcommit: 677dcc74aa898b2a17eb8430a32e675fea4e3fe5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63557817"
---
# <a name="create-and-configure-retention-policies"></a>Bekletme ilkeleri oluşturma ve yapılandırma

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

İçeriği tutma, içeriği silme veya alıkoyma ve sonra da silme arasında önceden karar vererek, kuruluşun verilerini yönetmek için bekletme ilkesi kullanın.

Bekletme ilkesi, kapsayıcı düzeyinde aynı bekletme ayarlarını bu kapsayıcının içeriği tarafından otomatik olarak devralınacak şekilde ataarak bu görevi çok verimli bir şekilde yapmanizi sağlar. Örneğin, SharePoint sitedeki tüm öğeler, kullanıcıların posta kutularında yer alan tüm e Exchange iletileri, ekipler için kullanılan tüm kanal iletileri Microsoft Teams. Kapsayıcı düzeyinde bir bekletme ilkesi mi yoksa öğe düzeyinde bir bekletme etiketi mi kullanmaya karar verdiyseniz, bkz. Bekletme ilkeleri ve [bekletme etiketleri](retention.md#retention-policies-and-retention-labels).

Bekletme ilkeleri ve bekletmenin çalışma yöntemleri hakkında daha fazla bilgi Microsoft 365 bkz[. Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinebilirsiniz](retention.md).

> [!NOTE]
> Bu sayfada yer alan bilgiler uyumluluk yöneticilerine göredir. Yönetici değilseniz ve kullanabileceğiniz uygulamalar için bekletme ilkelerinin nasıl yapılandırıldığından emin olmak için yardım masanıza, IT departmanınıza veya yöneticinize başvurun. Bir sohbette ve kanal iletisinde bekletme ilkeleriyle ilgili iletileri Teams, bekletme ilkeleriyle ilgili iletileri [Teams yararlı bulabilirsiniz](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

## <a name="before-you-begin"></a>Başlamadan önce

Genel yöneticinin, bekletme ilkeleri oluşturma ve düzenlemeye yönelik tam izinleri vardır. Genel yönetici olarak oturum açmadısanız, bilgi yönetimi [için izin bilgilerine bakın](get-started-with-information-governance.md#permissions-for-retention-policies-and-retention-labels).

Bekletme ilkenizi uyarlanabilir mi yoksa statik mi olacağını **oluşturmadan** önce karar **verin**. Daha fazla bilgi için bkz. [Bekletme için uyarlanabilir veya statik ilke kapsamları](retention.md#adaptive-or-static-policy-scopes-for-retention). Uyarlanabilir bir ilke kullanmaya karar verdiyseniz, bekletme ilkenizi oluşturmadan önce bir veya birden çok uyarlanabilir kapsam oluşturmanız ve sonra bekletme ilkesi oluşturma işlemi sırasında bu kapsamları seçmeniz gerekir. Yönergeler için bkz. [Uyarlanabilir kapsamlar için yapılandırma bilgileri](retention-settings.md#configuration-information-for-adaptive-scopes).

## <a name="create-and-configure-a-retention-policy"></a>Bekletme ilkesi oluşturma ve yapılandırma

Bekletme ilkesi, bekletme ilkesinde "konumlar" olarak tanımlanan birden çok hizmeti destekleyese de, desteklenen konumların hepsini içeren tek bir bekletme ilkesi oluşturamaz:

- Exchange-posta gönderme
- SharePoint sitesi
- OneDrive hesapları
- Microsoft 365 grupları
- Skype Kurumsal
- Exchange klasörleri taşıma
- Teams iletilerini gönderme
- Teams sohbetleri geri
- Teams kanal iletilerini gönderme
- Yammer iletilerini gönderme
- Yammer iletilerini gönderme

Bekletme ilkesi Teams konumlarını Yammer konumlarını seçerseniz, diğer konumlar otomatik olarak dışılır. Bu, yönergelerin takip etmek istediğiniz yönergelerin, bağlı konumlarını mı yoksa konumlarını mı Teams Yammer bağlıdır:

- [Posta konumları için bekletme Teams yönergeleri](#retention-policy-for-teams-locations)
- [Posta konumları için bekletme Yammer yönergeleri](#retention-policy-for-yammer-locations)
- [Konumlar ve Konumlar dışında konumlar için Teams ilkesi Yammer](#retention-policy-for-locations-other-than-teams-and-yammer)

> [!NOTE]
> Statik ilkeler yerine uyarlanabilir ilkeler kullanırken, tek bir bekletme ilkesi yapılandırarak hem Teams hem de Yammer yapılandırabilirsiniz. Farklı konumlarda ve farklı konumlarda Teams Yammer ilkeler böyle değildir.

Birden fazla bekletme ilkeniz varsa ve bekletme etiketlerini de kullanıyorken, aynı içeriğe birden çok bekletme ayarı uygulanırken eldeki sonucu anlamak için bkz. Bekletme ilkeleri veya öncelik neler olur[?](retention.md#the-principles-of-retention-or-what-takes-precedence)

### <a name="retention-policy-for-teams-locations"></a>Konumlar için bekletme Teams ilkesi

1. İlke [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com/) Yönetim **İlkeleri'ne** >  **seçin**.

2. Bekletme **ilkesi yapılandırmasını başlatmak** için Yeni bekletme **ilkesi'ne seçin** ve yeni bekletme ilkenizi bir adyla yazın.

3. Oluşturulecek **bekletme ilkesi türünü seçin sayfasında**, Başlamadan önce yönergelerinden seçime bağlı olarak Uyarlanabilir veya [Statik'i](#before-you-begin) seçin. Uyarlanabilir kapsamları daha önce oluşturmadıysanız Uyarlanabilir'i  seçebilirsiniz, ancak seçecek herhangi bir uyarlanabilir kapsam olmayacaksa, bu seçenekle yapılandırmayı bitiresiniz.

4. Seçtiğiniz kapsama bağlı olarak:
    
    -  Uyarlanabilir'i seçtiyseniz: Uyarlanabilir ilke kapsamlarını ve konumlarını seçin sayfasında  Kapsam ekle'yi seçin ve oluşturulmuş bir veya birden çok uyarlanabilir kapsam seçin. Ardından bir veya daha fazla konum seçin. Seçebilirsiniz konumlar, eklenen kapsam [türlerine bağlıdır](retention-settings.md#configuration-information-for-adaptive-scopes) . Örneğin, yalnızca bir Kullanıcı kapsamı türü eklediysanız **, kanal** mesajlarını seçerek **sohbetleri Teams** ancak **Teams edebilirsiniz**. 
    
    - **Statik'i seçtiyseniz**, **İlkeyi** uygulamak için konumları seçin sayfasında, İş için bir veya daha fazla Teams:
        - **Teams mesajı görüntüler**: Standart kanal sohbetlerinden ve standart kanal toplantılarından gelen iletiler; ancak kendi ilke konumlarına [](/microsoftteams/private-channels) sahip özel kanallardan değil.
        - **Teams sohbetleri**: Özel bire bir sohbetlerden, grup sohbetlerinden ve toplantı sohbetlerinden gelen mesajlar.
        - **Teams mesajları: Özel** kanal sohbetlerinden ve özel kanal toplantılarından gelen iletiler.
        
       Varsayılan olarak tüm [ekipler ve tüm kullanıcılar seçilidir](retention-settings.md#a-policy-that-applies-to-entire-locations), ancak Seç ve Dışla seçeneklerini seçerek [**bunu** **daraltabilirsiniz**](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions).

5. İçeriği **korumak mı, silmek mi yoksa her** ikisini birden mi silmek istediğinize karar vermek için, içeriği tutmak ve silmek için yapılandırma seçeneklerini belirtin.

   İçeriği silmeden, belirli bir süre sonunda veya yalnızca belirtilen süre sonunda içeriği silerek, yalnızca içeriği silerek bir bekletme ilkesi oluşturabilirsiniz. Daha fazla bilgi için bkz[. Ayarlar tutma ve silme hakkında daha fazla bilgi.](retention-settings.md#settings-for-retaining-and-deleting-content)

6. Yapılandırmayı tamamlama ve ayarlarınızı kaydetme.

İlke ve son kullanıcı deneyimini anlamak üzere bekletme Teams konusunda yol gösterme için bkz. İlke belgelerine [](/microsoftteams/retention-policies) bakarak Microsoft Teams için bekletme Teams yönetme.

Örnek adımlarla, bekletme ve zamanlama bilgileri için desteklenen ileti öğeleri de dahil olmak üzere, Teams'de bekletmenin nasıl çalıştığını içeren teknik ayrıntılar için bkz. [Microsoft Teams.](retention-policies-teams.md)

#### <a name="known-configuration-issues"></a>Bilinen yapılandırma sorunları

- Öğelerin son değiştirilma tarihlerini bekletme dönemini başlatma seçeneğini de kullanabilirsiniz, ancak Ne zaman **oluşturuldu? değeri** her zaman kullanılır. Düzenlenen iletilerde, önceden düzenlenmiş bu iletinin ne zaman oluşturuldığını belirlemek için özgün iletinin bir kopyası özgün zaman damgasıyla kaydedilir ve düzenlenmiş iletide daha yeni bir zaman damgası yer alır.

- Sohbet konumu **için** Düzenle'Teams, konukları ve posta kutusu olmayan kullanıcıları görebilirler. Bekletme ilkeleri bu kullanıcılar için tasarlanmamalıdır, bu nedenle onları seçmemelisiniz.


#### <a name="additional-retention-policy-needed-to-support-teams"></a>Destek ve destek için gereken ek bekletme Teams

Teams yalnızca sohbetler ve kanal iletileri değil. Microsoft 365 grubundan (eski adı Office 365 grubu) oluşturulan ekipleriz varsa, Microsoft 365 Grupları konumunu kullanarak bu Microsoft 365 grubunu içeren bir bekletme ilkesi **de yapılandırabilirsiniz**. Bu bekletme ilkesi grubun posta kutusu, site ve dosyalarında bulunan içeriklere uygulanır.

Bir Microsoft 365 grubuna bağlı olmayan ekip siteleriniz varsa, Microsoft 365'de dosyaları alıkoyma ve silme için **SharePoint** sitelerini veya **OneDrive** hesap konumlarını içeren bir bekletme ilkesine Teams:

- Sohbette paylaşılan dosyalar, OneDrive paylaşan kullanıcının hesaplarında depolanır.

- Kanallara yüklenen dosyalar, ekibin SharePoint bir ekip sitesinde depolanır.

> [!TIP]
> Bekletme ilkesi, bir Microsoft 365 grubuna bağlı değilken yalnızca belirli bir ekibin dosyalarına, ekip için SharePoint sitesini ve Ekip'OneDrive kullanıcıların hesaplarını seçerek uygulayabilirsiniz.

Microsoft 365 gruplarına, SharePoint sitelerine veya OneDrive hesaplarına uygulanan bir bekletme ilkesi, bu iletilerin silinmeden önce bir Teams sohbeti veya kanal mesajında başvurulan bir dosyayı silebilir. Bu senaryoda, dosya en son Teams görüntülenir, ancak kullanıcılar dosyayı seçerken "Dosya bulunamadı" hatası alır. Bu davranış bekletme ilkelerine özgü değildir ve kullanıcı dosyayı başka bir dosyadan el ile silebilir SharePoint OneDrive.

### <a name="retention-policy-for-yammer-locations"></a>Konumlar için bekletme Yammer ilkesi

> [!NOTE]
> Bekletme ilkeleri Yammer önizlemededir ve bekletme ilkesi nedeniyle şu anda iletiler silindiğinde kullanıcılara bildiremez.
>
> Bu özelliği kullanmak için, Yammer ağın Karma Mod değil, [Yerel](/yammer/configure-your-yammer-network/overview-native-mode) Mod olması gerekir.

1. İlke [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com/) Yönetim **İlkeleri'ne** >  **seçin**.

2. Yeni **bir bekletme ilkesi oluşturmak için** Yeni bekletme ilkesi'ne seçin.

3. Oluşturulecek **bekletme ilkesi türünü seçin sayfasında**, Başlamadan önce yönergelerinden seçime bağlı olarak Uyarlanabilir veya [Statik'i](#before-you-begin) seçin. Uyarlanabilir kapsamları daha önce oluşturmadıysanız Uyarlanabilir'i  seçebilirsiniz, ancak seçecek herhangi bir uyarlanabilir kapsam olmayacaksa, bu seçenekle yapılandırmayı bitiresiniz.

4. Seçtiğiniz kapsama bağlı olarak:
    
    -  Uyarlanabilir'i seçtiyseniz: Uyarlanabilir ilke kapsamlarını ve konumlarını seçin sayfasında  Kapsam ekle'yi seçin ve oluşturulmuş bir veya birden çok uyarlanabilir kapsam seçin. Ardından bir veya daha fazla konum seçin. Seçebilirsiniz konumlar, eklenen kapsam [türlerine bağlıdır](retention-settings.md#configuration-information-for-adaptive-scopes) . Örneğin, yalnızca bir Kullanıcı kapsamı türü eklediysanız **, kullanıcı** iletilerini Yammer **ancak** topluluk iletilerini **Yammer seçebilirsiniz**. 
    
    - Statik: **İlkeyi** uygulamak için  konumları seçin sayfasında, **Yammer: Yammer** için konumların birini veya her ikisini de açıp kullanıcı iletilerini Yammer **seçin**.
        
        > [!IMPORTANT]
        > Yalnızca bu kullanıcı iletileri için bir bekletme ilkesi Yammer, ancak bu konumun bekletme ilkesi tüm topluluk üyeleri için Yammer uygulamasından topluluk iletilerini silebilir.
        > 
        > Bu seçeneği belirtirseniz ve bekletme ilkesi kullanıcı iletilerini silmek üzere yapılandırılırsa, bunun bir etkiyi anlamış olduğundan emin olun. Daha fazla bilgi için bkz[. Bekletme nasıl Yammer](retention-policies-yammer.md#how-retention-works-with-yammer).
        
        Varsayılan olarak, tüm topluluklar ve kullanıcılar seçilir, ancak dahil edilecek veya hariç tutulacak toplulukları ve kullanıcıları belirterek bu değeri daraltabilirsiniz.
        
        Kullanıcı Yammer iletileri için: 
        - Varsayılan ayarı Tüm kullanıcılar olarak **bırakırsanız**, Azure B2B konuk kullanıcıları dahil değildir. 
        - Tüm kullanıcılar için  **Düzenle'yi seçerseniz**, bu kullanıcıların hesaplarını biliyorsanız dış kullanıcılara bir bekletme ilkesi uygulayabilirsiniz.

5. İçeriği **korumak mı, silmek mi yoksa her** ikisini birden mi silmek istediğinize karar vermek için, içeriği tutmak ve silmek için yapılandırma seçeneklerini belirtin. 
    
    İçeriği silmeden, belirli bir süre sonunda veya yalnızca belirtilen süre sonunda içeriği silerek, yalnızca içeriği silerek bir bekletme ilkesi oluşturabilirsiniz. Daha fazla bilgi için bkz[. Ayarlar tutma ve silme hakkında daha fazla bilgi.](retention-settings.md#settings-for-retaining-and-deleting-content)

6. Yapılandırmayı tamamlama ve ayarlarınızı kaydetme.

Bu konuda bekletme ilkelerinin nasıl çalışır? Yammer için [bekletme hakkında bilgi Yammer](retention-policies-yammer.md).

#### <a name="additional-retention-policies-needed-to-support-yammer"></a>Destek olmak için gereken ek bekletme Yammer

Yammer yalnızca topluluk iletileri ve özel iletiler değil. Yammer ağ bağlantınıza gelen e-posta iletilerini korumak ve silmek için, Microsoft 365 Grupları konumunu kullanarak Yammer için kullanılan tüm Microsoft 365 gruplarını içeren **ek bir bekletme Microsoft 365 yapılandırabilirsiniz**. 

Yammer'de depolanan dosyaları alıkoyma ve silme için, **Microsoft 365 Grupları** konumunu veya hesap konumlarını içeren **OneDrive** ilkeniz gerekir:

- Özel iletilerde paylaşılan dosyalar, dosyayı OneDrive kullanıcıya gönderilen posta hesabında depolanır. 

- Topluluklara yüklenen dosyalar, toplulukta yer alan topluluk için grup SharePoint grup Yammer depolanır.

SharePoint sitelerine veya OneDrive hesaplarına uygulanan bir bekletme ilkesi, bu iletilerin silinmeden önce bir Yammer iletisinde başvurulan bir dosyayı silebilir. Bu senaryoda, dosya Yammer iletisinde görüntülenir, ancak kullanıcılar dosyayı seçerken "Dosya bulunamadı" hatası alır. Bu davranış bekletme ilkelerine özgü değildir ve kullanıcı dosyayı başka bir dosyadan el ile silebilir SharePoint OneDrive.

### <a name="retention-policy-for-locations-other-than-teams-and-yammer"></a>Konumlar ve Konumlar dışında Teams bekletme Yammer

Bu hizmetlerden herhangi biri için geçerli olan bekletme ilkeleri için aşağıdaki yönergeleri kullanın:

- Exchange: E-posta ve ortak klasörler
- SharePoint: Siteler
- OneDrive: Hesaplar
- Microsoft 365 grupları
- Skype Kurumsal

1. İlke [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com/) Yönetim **İlkeleri'ne** >  **seçin**.

2. Bekletme **ilkesi yapılandırmasını başlatmak** için Yeni bekletme **ilkesi'ne seçin** ve yeni bekletme ilkenizi bir adyla yazın.

3. Oluşturulecek **bekletme ilkesi türünü seçin sayfasında**, Başlamadan önce yönergelerinden seçime bağlı olarak Uyarlanabilir veya [Statik'i](#before-you-begin) seçin. Uyarlanabilir kapsamları daha önce oluşturmadıysanız Uyarlanabilir'i  seçebilirsiniz, ancak seçecek herhangi bir uyarlanabilir kapsam olmayacaksa, bu seçenekle yapılandırmayı bitiresiniz. Uyarlanabilir ilkeler ortak klasörlerin veya klasörlerin Exchange için Skype Kurumsal.

4. Seçtiğiniz kapsama bağlı olarak:
    
    -  Uyarlanabilir'i seçtiyseniz: Uyarlanabilir ilke kapsamlarını ve konumlarını seçin sayfasında  Kapsam ekle'yi seçin ve oluşturulmuş bir veya birden çok uyarlanabilir kapsam seçin. Ardından bir veya daha fazla konum seçin. Seçebilirsiniz konumlar, eklenen kapsam [türlerine bağlıdır](retention-settings.md#configuration-information-for-adaptive-scopes) . Örneğin, yalnızca bir Kullanıcı kapsamı türü eklediysanız **,** e-postayla ilgili e-Exchange **seçebilirsiniz** ancak **SharePoint seçebilirsiniz**. 
    
    - Statik:**Konum** seçin sayfasında, Konum  ve Bağlantı Konumları konumları dışında herhangi bir konumu açıp Teams Yammer. Her konum için, ilkeyi varsayılan olarak bırakarak ilkeyi [](retention-settings.md#a-policy-that-applies-to-entire-locations)konumun tamamına uygulayabilir ya da içerir [ve dışarıda bırakılacakları belirtebilirsiniz](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions).
    
    Konumlara özgü bilgiler:
    - [Exchange postayı ve Exchange klasörleri taşıma](retention-settings.md#configuration-information-for-exchange-email-and-exchange-public-folders)
    - [SharePoint sitelerini ve OneDrive hesaplarınız](retention-settings.md#configuration-information-for-sharepoint-sites-and-onedrive-accounts)
    - [Microsoft 365 Grupları](retention-settings.md#configuration-information-for-microsoft-365-groups)
    - [Skype Kurumsal](retention-settings.md#configuration-information-for-skype-for-business)

5. İçeriği **korumak mı, silmek mi yoksa her** ikisini birden mi silmek istediğinize karar vermek için, içeriği tutmak ve silmek için yapılandırma seçeneklerini belirtin.
    
    İçeriği silmeden, belirli bir süre sonunda veya yalnızca belirtilen süre sonunda içeriği silerek, yalnızca içeriği silerek bir bekletme ilkesi oluşturabilirsiniz. Daha fazla bilgi için Ayarlar [içeriği tutma ve silme hakkında daha fazla](retention-settings.md#settings-for-retaining-and-deleting-content) bilgi için bkz.

6. Yapılandırmayı tamamlama ve ayarlarınızı kaydetme.

## <a name="how-long-it-takes-for-retention-policies-to-take-effect"></a>Bekletme ilkelerinin yürürlüğe girecekleri süre

Bekletme ilkesi  oluşturmanız ve göndermeniz, bekletme ilkesinin uygulanması yedi gün kadar zaman alabiliyor:
  
![Bekletme ilkesi ne zaman yürürlüğe girecek? diyagramı.](../media/retention-policy-timings.png)

İlk olarak, bekletme ilkesi seçtiğiniz konumlara dağıtılmalı ve sonra da içeriğe uygulanmalıdır. İstediğiniz zaman uyumluluk merkezinde Bekletme ilkeleri sayfasından ilkeyi seçerek **bekletme ilkesi** dağıtım durumunu kontrol edebilirsiniz. Uç uç bölmesinde, durumla ilgili (Hata **)** durumunu görüyorsanız ve konumlara ilişkin ayrıntılarda ilkenin dağıtılması beklenenden uzun süre alıyor veya ilkeyi yeniden dağıtmayı denemek için [, Set-AppRetentionCompliancePolicy](/powershell/module/exchange/set-appretentioncompliancepolicy) veya [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) PowerShell komutunu çalıştırarak ilke dağıtımını yeniden deneyin:

1. [Bağlan ve Uyumluluk & PowerShell'e.](/powershell/exchange/connect-to-scc-powershell)

2. Aşağıdaki komutlardan birini çalıştırın:
    
    - Özel kanal iletilerinin Teams **ilke konumları için**, **Yammer iletilerini ve topluluk** **Yammer mesajlarını iletin**:
    
        ```PowerShell
        Set-AppRetentionCompliancePolicy -Identity <policy name> -RetryDistribution
        ```
    
    - E-posta gönderme, site Exchange **, kanal** **SharePoint gibi** diğer tüm **ilke Teams için**:
    
        ```PowerShell
        Set-RetentionCompliancePolicy -Identity <policy name> -RetryDistribution
        ```

## <a name="updating-retention-policies"></a>Bekletme ilkelerini güncelleştirme

Bekletme ilkesinden alınan ayarlar içeriğe zaten uygulandığında, ilkenin yapılandırmasında yapılan bir değişiklik yeni tanımlanan içeriğe ek olarak bu içeriğe otomatik olarak uygulanır.

İlke oluşturulduktan ve kaydedildikten sonra bazı ayarlar değiştirilemez. Bunlar bekletme ilkesi adını, kapsam türünü (uyarlanabilir veya statik) ve bekletme süresi dışında bekletme ayarlarını içerir.

## <a name="next-steps"></a>Sonraki adımlar

Exchange, SharePoint, OneDrive veya Microsoft 365 Grupları için bazı öğeler için yapılandırılan bekletme ilkesi ayarlarından farklı bekletme ayarları gerekirse, bu özel durumlar için bekletme etiketleri [oluşturun](create-retention-labels-information-governance.md).

Öte yandan, iş, yasal veya mevzuata yönelik kayıt tutma gereksinimleri için yüksek değerli öğelerin yaşam döngüsü yönetimini arıyorsanız, bekletme etiketleri oluşturmak ve yönetmek için dosya [planını kullanın](file-plan-manager.md).
