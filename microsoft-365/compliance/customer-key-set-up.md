---
title: Müşteri Anahtarını Ayarlama
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Müşteri Anahtarı ayarlamayı öğrenin ve Microsoft 365.
ms.openlocfilehash: f3d7da27e0c9a5e27f0c3e7bcc3adb48dad5d42c
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634525"
---
# <a name="set-up-customer-key"></a>Müşteri Anahtarını Ayarlama

Müşteri Anahtarı ile, kuruluşun şifreleme anahtarlarını kontrol eder ve sonra Microsoft 365 Microsoft'un veri merkezlerindeki verilerinizi şifrelemek için bunları kullanmak üzere yapılandırabilirsiniz. Başka bir deyişle, Müşteri Anahtarı müşterilerin anahtarlarıyla birlikte onlara ait bir şifreleme katmanı eklemelerine olanak sağlar.

Müşteri Anahtarını müşteri hizmetleri için kullanamadan önce Azure'Office 365. Bu makalede, gerekli Azure kaynaklarını oluşturmak ve yapılandırmak için izlemeniz gereken adımlar açıklanmıştır, ardından Bu makalede Müşteri Anahtarını ayarlama adımları Office 365. Azure'i ayardikten sonra, çeşitli iş yükleri genelinde verileri şifrelemek üzere hangi ilkeyi ve dolayısıyla Microsoft 365 tuşları atayabilirsiniz. Müşteri Anahtarı hakkında daha fazla bilgi veya genel bir genel bakış için bkz. Müşteri Anahtarı ile [Hizmet şifrelemesi Office 365](customer-key-overview.md).
  
> [!IMPORTANT]
> Bu makaledeki en iyi yöntemleri izlemenizi kesinlikle öneririz. Bunlar TIP ve ÖNEMLİ **olarak** **ifade edildi**. Müşteri Anahtarı, kapsamı tüm organizasyon kadar büyük olan kök şifreleme anahtarları üzerinde denetim sağlar. Bu, bu tuşlarla yapılan hataların çok büyük bir etkisi olduğu ve hizmette kesintilere veya geri dönülemez veri kaybına neden olduğu anlamına gelir.
  
## <a name="before-you-set-up-customer-key"></a>Müşteri Anahtarını ayarlamadan önce

Başlamadan önce, kurum için uygun Azure aboneliklerine ve lisanslara sahip olduğundan emin olur. Ücretli Azure Aboneliklerini bir Bulut Hizmeti Kurumsal Anlaşma kullanarak kullanın. Kredi Kartı tabanlı ödemeler kabul edilmemektedir. Faturalama için hesap  ihtiyaçlarını onaylar ve ayarlayın. Ücretsiz, Deneme, Sponsorluk, MSDN Abonelikleri aracılığıyla sahip olduğunuz abonelikler ve Eski Destek kapsamındaki abonelikler uygun değildir.

Office 365 E5, Microsoft 365 E5, Microsoft 365 E5 Uyumluluk ve yönetim Microsoft 365 E5 Information Protection & SK'lar Müşteri Anahtarı teklif ediyor. Office 365 Gelişmiş Uyumluluk SKU artık yeni lisansların temini için kullanılamaz. Mevcut Office 365 Gelişmiş Uyumluluk lisansları destek olmaya devam edecektir.

Bu makaledeki kavramları ve yordamları anlamak için[, Azure Hizmet Key Vault](/azure/key-vault/) gözden geçirin. Ayrıca, örneğin Azure AD kiracısı gibi Azure'da kullanılan terimleri [de öğrenin](/previous-versions/azure/azure-services/jj573650(v=azure.100)#what-is-an-azure-ad-tenant).
  
Belgeler dışında daha fazla de yardıma ihtiyacınız varsa, yardım için Microsoft Consulting Services (MCS), Premier Field Engineering (PFE) veya bir Microsoft iş ortağına başvurun. Müşteri Anahtarı hakkında belgeler dahil olmak üzere geri bildirim sağlamak, fikirlerinizi, önerilerinizi ve perspektiflerinizi size customerkeyfeedback@microsoft.com.
  
## <a name="overview-of-steps-to-set-up-customer-key"></a>Müşteri Anahtarını ayarlama adımlarına genel bakış

Müşteri Anahtarını ayarlamak için, bu görevleri listelenen sırayla gerçekleştirin. Bu makalenin kalan bölümü her görev için ayrıntılı yönergeler sağlar veya sürecin her adımı için daha fazla bilgiye bağlantı sağlar.
  
**Azure ve Microsoft FastTrack:**
  
Diğer görevlere uzaktan bağlanarak bu görevlerin çoğunu Azure PowerShell. En iyi sonuçları elde etmek için 4.4.0 veya sonraki bir sürümünü Azure PowerShell.
  
- [İki yeni Azure aboneliği oluşturma](#create-two-new-azure-subscriptions)

- [Müşteri Anahtarı Müşteri Anahtarını etkinleştirmek için bir istek Office 365](#submit-a-request-to-activate-customer-key-for-office-365)
 
- [Zorunlu bir bekletme süresi kullanmak için Azure aboneliklerini kaydetme](#register-azure-subscriptions-to-use-a-mandatory-retention-period)

  Bu kayıt işleminin tamamlanması beş iş günü sürecektir.

- [Her abonelikte premium Key Vault Azure Hesabı oluşturma](#create-a-premium-azure-key-vault-in-each-subscription)

- [Her bir anahtar kasaya izin atama](#assign-permissions-to-each-key-vault)

- [Anahtar kasalar üzerinde yumuşak silmenin etkinleştirildiğinden emin olun](#make-sure-soft-delete-is-enabled-on-your-key-vaults)

- [Anahtar oluşturarak veya içeri aktararak her bir anahtar kasaya anahtar ekleyin](#add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key)

- [Anahtarlarınızı kurtarma düzeyini denetleme](#check-the-recovery-level-of-your-keys)

- [Azure Key Vault'i Key Vault](#back-up-azure-key-vault)

- [Azure Key Vault yapılandırma ayarlarını doğrulama](#validate-azure-key-vault-configuration-settings)

- [Her Azure Key Vault anahtarının URI'lerini alma](#obtain-the-uri-for-each-azure-key-vault-key)
  
## <a name="complete-tasks-in-azure-key-vault-and-microsoft-fasttrack-for-customer-key"></a>Müşteri Anahtarı için Azure Key Vault ve Microsoft FastTrack'te görevleri tamamlama

Bu görevleri Azure Key Vault. Müşteri Anahtarı ile birlikte kullanarak tüm DEP'ler için bu adımları tamamlamanız gerekir.
  
### <a name="create-two-new-azure-subscriptions"></a>İki yeni Azure aboneliği oluşturma

Müşteri Anahtarı için iki Azure aboneliği gerekir. En iyi uygulama olarak Microsoft, Müşteri Anahtarı ile kullanmak üzere yeni Azure abonelikleri oluşturmanızı önermektedir. Azure Key Vault anahtarları yalnızca aynı Azure Active Directory (Microsoft Azure Active Directory) kiracısı uygulamaları için yetkilendirilene kadar, yeni abonelikleri oluşturmak için DEP'lerin atandığı kuruluşla kullanılan Azure AD kiracısı ile aynı şekilde oluşturmanız gerekir. Örneğin, genel yönetici ayrıcalıklarına sahip iş veya okul hesabınız kullanarak. Ayrıntılı adımlar için bkz [. Kuruluş olarak Azure'a kaydolma](/azure/active-directory/fundamentals/sign-up-organization).
  
> [!IMPORTANT]
> Müşteri Anahtarı, her veri şifreleme ilkesi (DEP) için iki anahtar gerektirir. Bunu yapmak için iki Azure aboneliği oluşturmanız gerekir. En iyi uygulama olarak Microsoft, her abonelikte kuruluştan ayrı üyelerinizin tek bir anahtar yapılandırmanızı önermektedir. Bu Azure aboneliklerini yalnızca bu aboneliklerin şifreleme anahtarlarını yönetmek için Office 365. İşleçlerden birinin yanlışlıkla, bilerek veya kötü amaçlı olarak silmesi veya sorumlu olduğu anahtarları başka bir şekilde kötü amaçlı olarak kötü amaçlı olarak silmesi durumunda, bu durum organizasyonlarınızı korur.

Organizasyonunız için oluşturabilirsiniz Azure aboneliklerinin sayısında pratik bir sınır yoktur. Bu en iyi yöntemlerin takipilmesi, insan hatasının etkisini en aza indirgerken, Customer Key tarafından kullanılan kaynakların yönetimine de yardımcı olur.
  
### <a name="submit-a-request-to-activate-customer-key-for-office-365"></a>Müşteri Anahtarı Müşteri Anahtarını etkinleştirmek için bir istek Office 365

İki yeni Azure aboneliğini oluşturduktan sonra, portalda uygun Müşteri Anahtarı teklifi isteğini [Microsoft FastTrack](https://fasttrack.microsoft.com/). Teklif formunda kurum içindeki yetkili atamalar hakkında seçiminiz kritik öneme sahiptir ve Müşteri Anahtarı kaydının tamamlanması için gereklidir. Organizasyon kapsamında seçilen rollerdeki sorumlular, Müşteri Anahtarı veri şifreleme ilkesiyle kullanılan tüm anahtarları iptal etmek ve yok etmek için tüm isteklerin orijinalliğini sağlar. Bu adımı, organizasyonunız için kullanmayı istediğiniz her Müşteri Anahtarı DEP türü için bir kez gerekir.

**Müşteri FastTrack, Müşteri Anahtarı ile ilgili yardım sağlamaz. Office 365, müşteri FastTrack anahtarıyla ilgili teklifleri izlememizi sağlamak için FastTrack portalını kullanıyor. Müşteri ekleme isteğini FastTrack, ilgili Müşteri Anahtarı ekleme ekibine ulaşarak ekleme işlemini başlatabilirsiniz.**
  
Müşteri Anahtarını etkinleştirmek üzere bir teklif göndermek için şu adımları tamamlayın:
  
1. Kuruluşta genel yönetici izinleri olan bir iş veya okul hesabı kullanarak, genel yönetici Microsoft FastTrack [açın](https://fasttrack.microsoft.com/).

2. Oturum açtıktan sonra uygun etki alanını seçin.

3. Seçili etki alanı için üst gezinti **çubuğundan** Hizmetleri taleple'yi seçin ve kullanılabilir teklifler listesini gözden geçirin.

4. Teklifin sizin için geçerli olan bilgi kartını seçin:

   - **Birden Microsoft 365 iş yükü:** Yeni teklif **sunmak için Şifreleme anahtarı Microsoft 365** seçin.

   - **Exchange Online ve Skype Kurumsal:** Teklif için **şifreleme anahtarı isteği Exchange** seçin.

   - **SharePoint Online, OneDrive ve Teams dosyaları için:** SharePoint ve OneDrive İş teklifi için **Şifreleme anahtarı OneDrive İş** seçin.

5. Teklif ayrıntılarını gözden geçirmenin ardından **2. adıma geçin'i seçin**.

6. Teklif formunda tüm geçerli ayrıntıları ve istenen bilgileri doldurun. Kalıcı ve geri alınamaz şifreleme anahtarları ve verileri onaylamak üzere yetki vermek istediğiniz kuruluş yetkililerini seçimlerinizi özellikle önemsersiniz. Formu tamamlandıktan sonra Gönder'i **seçin**.

### <a name="register-azure-subscriptions-to-use-a-mandatory-retention-period"></a>Zorunlu bir bekletme süresi kullanmak için Azure aboneliklerini kaydetme

Kök şifreleme anahtarlarının geçici veya kalıcı olarak kaybı, hizmet işleminde kesintiye neden veya hatta bir etki olabilir ve veri kaybına neden olabilir. Bu nedenle, Müşteri Anahtarı ile kullanılan kaynaklar güçlü bir koruma gerektirir. Customer Key ile birlikte kullanılan tüm Azure kaynakları, varsayılan yapılandırmanın ötesinde koruma mekanizmaları sunar. Zorunlu bir bekletme süresi için Azure aboneliklerini *etiketlebilirsiniz veya kaydettirebilirsiniz*. Zorunlu bekletme süresi, Azure aboneliğinizin hemen ve geri alınamaz iptalini önler. Zorunlu bir bekletme süresi için Azure aboneliklerini kaydetmek için gerekli adımlar için ekip ekiple Microsoft 365 gerekir. Bu işlem beş iş günü içinde tamamlanacak. Önceden, zorunlu bekletme süresi bazen "İptal Etme" olarak da adlandırılırdı.
  
Müşteri Anahtarı ile Microsoft 365 Azure aboneliği için aşağıdaki adımları uygulayın. Başlamadan önce en az [Azure PowerShell](/powershell/azure/new-azureps-module-az) modülün yüklü olduğundan emin olmak.
  
1. Diğerleriyle oturum Azure PowerShell. Yönergeler için bkz[. Posta ile Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Aboneliklerinizi Register-AzProviderFeature için zorunlu bir bekletme süresi kullanmak üzere aşağıdaki cmdlet'i çalıştırın. Her abonelik için bu eylemi tamamlama.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzProviderFeature -FeatureName mandatoryRetentionPeriodEnabled -ProviderNamespace Microsoft.Resources
   ```

3. işlemi tamamlamak için Microsoft'a ulaşın.

   - Posta kutularına tek tek DEP atamak için Müşteri Anahtarını etkinleştirmek Exchange Online posta [kutunuza exock@microsoft.com](mailto:exock@microsoft.com).

   - Tüm kiracı kullanıcıları için SharePoint Online ve OneDrive İş içeriğini (Teams dosyaları dahil) şifrelemek üzere DEP'leri atamak üzere Müşteri Anahtarını etkinleştirmek için [spock@microsoft.com.](mailto:spock@microsoft.com)

   - Birden çok Microsoft 365 iş yükü (Exchange Online, Teams, Microsoft Bilgi Koruması) genelinde içeriği şifrelemek üzere DEP'leri atamak üzere Müşteri Anahtarını etkinleştirmek için, [m365-ck@service.microsoft.com.](mailto:m365-ck@service.microsoft.com)

   - E-postanıza aşağıdaki bilgileri girin:

     **Konu**: Müşteri Anahtarı \<*Your tenant's fully qualified domain name*\>

     **Gövde**: Zorunlu bekletme dönemini tamamlamak istediğiniz abonelik kimliklerini ve her abonelik için Get-AzProviderFeature çıktısını dahil edin.

     Bu işlemi tamamlamanız için Hizmet Düzeyi Sözleşmesi (SLA), Microsoft'a zorunlu bir bekletme süresi kullanmak üzere aboneliklerinizi kaydettirtnizin bildirilmesi (ve doğrulanmasının) ardından beş iş günü olur.

4. Microsoft'tan kayıt işleminin tamamlandıktan sonra, kayıt işleminin durumunu aşağıdaki gibi Get-AzProviderFeature doğrulayın. Doğrulanmışsa, Get-AzProviderFeature Komutu Kayıt Durumu özelliği için **Registered** **değerini** döndürür. Her abonelik için bu adımı tamamlama.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Get-AzProviderFeature -ProviderNamespace Microsoft.Resources -FeatureName mandatoryRetentionPeriodEnabled
   ```

5. Işlemi tamamlamak için, Tamamla Register-AzResourceProvider çalıştırın. Her abonelik için bu adımı tamamlama.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzResourceProvider -ProviderNamespace Microsoft.KeyVault
   ```

### <a name="create-a-premium-azure-key-vault-in-each-subscription"></a>Her abonelikte premium Key Vault Azure Hesabı oluşturma

Anahtar kasa oluşturma adımları[, Azure Key Vault'i](/azure/key-vault/general/overview) yükleyerek başlatma Azure PowerShell, Azure aboneliğinize bağlanma, kaynak grubu oluşturma ve bu kaynak grubunda anahtar kasa oluşturma konusunda size yol gösteren Azure Key Vault'i Başlatma altında belge içerir.
  
Anahtar kasa 2 yken bir SKU seçmeniz gerekir: Standart veya Standart Premium. Standart SKU, Azure Key Vault anahtarlarının yazılımla korunmasına olanak sağlar ; Donanım Güvenlik Modülü (HSM) anahtar koruması yoktur ve Premium SKU, HSM'lerin yazılımlara karşı korunmasına Key Vault sağlar. Müşteri Anahtarı, SKU kullanan anahtar kasalarını kabul eder, ancak Microsoft SKU için yalnızca SKU kullanan Premium öneririz. Her iki tür de anahtarlı işlemlerin maliyeti aynıdır, bu nedenle maliyetteki tek fark, HSM korumalı her anahtarın aylık maliyetidir. Ayrıntılar [Key Vault fiyatlandırmaya](https://azure.microsoft.com/pricing/details/key-vault/) bakın.
  
> [!IMPORTANT]
> Üretim verileri Premium SKU anahtar kasaları ve HSM korumalı anahtarlar kullanın ve test ve doğrulama amacıyla yalnızca Standart SKU anahtar kasaları ve anahtarlarını kullanın.
  
Müşteri Microsoft 365 kullanabileceğiniz her hizmet için, oluşturduğunuz iki Azure aboneliğinin her biri için bir anahtar kasası oluşturun. Örneğin, Müşteri Anahtarının DEP'leri Exchange Online, SharePoint Online ve çok iş yükü senaryolarında kullanmasını sağlamak için, üç çift anahtar kasası oluşturabilirsiniz.
  
Kasaları ilişkilendirmek istediğiniz DEP kullanımını yansıtan anahtar kasalar için bir adlandırma kuralı kullanın. Adlandırma kuralı önerileri için aşağıdaki En İyi Yöntemler bölümüne bakın.
  
Her veri şifreleme ilkesi için ayrı, eşleştirilmiş bir kasa kümesi oluşturun. Daha Exchange Online için, ilkeyi posta kutusuna atadığınız zaman bir veri şifreleme ilkesi kapsamı sizin tarafından seçilir. Posta kutusuna tek bir ilke atanmış olabilir ve en çok 50 ilke oluşturabilirsiniz. SharePoint Online politikasının kapsamı, kuruluş içinde coğrafi bir konumdaki veya coğrafi konumdaki tüm verileri _içerir_. Çok iş yüküne sahip bir ilkenin kapsamı, tüm kullanıcıların desteklenen iş yükleri genelindeki tüm verileri içerir.

Anahtar kasaların oluşturulması, Azure kaynak gruplarının oluşturulmasını da gerektirir, çünkü anahtar kasalarında depolama kapasitesi gerekir (küçük olsa da) ve etkinse Key Vault günlüğe kaydetme de depolanmış veriler üretir. En iyi uygulama olarak Microsoft, her kaynak grubunu yönetmek için ayrı yöneticiler kullanır ve tüm ilgili Müşteri Anahtarı kaynaklarını yönetecek yöneticiler kümesiyle uyumlu bir yönetim sağlar.
  
> [!IMPORTANT]
> Kullanılabilirliği en üst düzeye çıkarmak için önemli kasalarınızı Microsoft 365 hizmetinizin yakınında yer alan bölgelere kapatın. Örneğin, Exchange Online kuruluşlarınız Kuzey Amerika'te ise anahtar kasalarınızı Kuzey Amerika. Exchange Online Avrupa'da ise, önemli kasalarınızı Avrupa'ya kilitlersiniz.
>
> Anahtar kasaları için yaygın bir ön ek kullanın, ayrıca anahtar kasa ve anahtarların (örneğin, kasaların Kuzey Amerika'te bulunamayacak Contoso SharePoint hizmeti için) kullanımı ve kapsamının kısaltmalarını içerir; olası bir ad çifti Contoso-CK-SP-NA-VaultA1 ve Contoso-CK-SP-NA-VaultA2'dır. Kasa adları Azure'daki genel benzersiz dizelerdir, bu nedenle istenen adların diğer Azure müşterileri tarafından zaten talep edildi olması durumunda istediğiniz ad çeşitlemelerini denemeniz gerekmektedir. Temmuz 2017'den sonra kasa adları değiştirilemez, bu nedenle en iyi uygulama, kurulum için yazılı bir plana sahip olmak ve planın doğru şekilde yürütüldiğini doğrulamak için ikinci bir kişi kullanmaktır.
>
> Mümkünse, eşleştirilmiş olmayan bölgelerde kasalarınızı oluşturun. Eşleştirilmiş Azure bölgeleri, hizmet hatası etki alanlarında yüksek kullanılabilirlik sağlar. Bu nedenle, bölgesel çiftler birbirlerinin yedekleme bölgesi olarak düşün olabilir. Bu, bir bölgeye yerleştirilen Azure kaynağının eşleştirilmiş bölge aracılığıyla otomatik olarak hata dayanıklılığına neden olduğu anlamına gelir. Bu nedenle, veri şifreleme ilkesinde kullanılan ve bölgelerin eşleştirilmiş olduğu iki kasa için bölge seçmek, kullanımdaki yalnızca toplam iki kullanılabilirlik bölgesi olduğu anlamına gelir. Çoğu coğrafyanın yalnızca iki bölgesi vardır, bu nedenle henüz eşleştirilmiş olmayan bölgeleri seçmek mümkün değildir. Mümkünse, veri şifreleme ilkesiyle kullanılan iki kasa için eşleştirilmiş olmayan iki bölge seçin. Bu, kullanılabilirlik toplam dört bölgeden elde edilir. Daha fazla bilgi için bkz [. İş sürekliliği ve olağanüstü durum kurtarma (BCDR):](/azure/best-practices-availability-paired-regions) Geçerli bölgesel çiftlerin listesi için Azure Eşli Bölgeleri.
  
### <a name="assign-permissions-to-each-key-vault"></a>Her bir anahtar kasaya izin atama

Uygulamanıza bağlı olarak, her anahtar kasası için üç ayrı izin kümesi tanımlamanız gerekir. Örneğin, aşağıdakilerin her biri için bir izin kümesi tanımlamanız gerekir:
  
- **Önemli kasanız** için günlük olarak yönetimi çalışan önemli kasa yöneticileri. Bu görevler yedekleme, oluşturma, alma, içeri aktarma, liste ve geri yükleme görevleridir.

  > [!IMPORTANT]
  > Anahtar kasası yöneticilerine atanan izin kümesi anahtar silme iznini içermez. Bu, bilerek yapılan ve önemli bir uygulamadır. Şifreleme anahtarlarını silme işlemi normalde yapılmaz, çünkü bunu yapmak verileri kalıcı olarak yok eder. En iyi uygulama olarak, bu izni anahtar kasa yöneticilerine varsayılan olarak verlanmaz. Bunun yerine, bunu önemli kasa katkıda bulunanları için rezerve etmek ve sonuçların net bir şekilde anlaşılması anlaşılması için bunu kısa vadeli olarak bir yöneticiye attayabilirsiniz.
  
  Bu izinleri kuruluşta yer alan bir kullanıcıya atamak için, Azure PowerShell. Yönergeler için bkz[. Posta ile Azure PowerShell](/powershell/azure/authenticate-azureps).

- Gerekli Set-AzKeyVaultAccessPolicy atamak için Set-AzKeyVaultAccessPolicy cmdlet'ini çalıştırın.

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user> -PermissionsToKeys create,import,list,get,backup,restore
   ```

   Örneğin:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -UserPrincipalName alice@contoso.com -PermissionsToKeys create,import,list,get,backup,restore
   ```

- **Azure'da izinleri değiştiren** anahtar kasa Key Vault. Çalışanlar ayrılarak veya takımınıza katıldıkları için bu izinleri değiştirebilirsiniz. Anahtar kasası yöneticilerinin bir anahtarı silmek veya geri yüklemek için yasal olarak izinlere ihtiyacı olduğu ender durumlarda, izinleri de değiştirebilirsiniz. Bu anahtar kasası katılımcıları kümesine, anahtar kasasında **Katkıda** Bulunan rolü verilmesi gerekir. Azure Resource Manager kullanarak bu rolü Resource Manager. Ayrıntılı adımlar için bkz. [Azure Role-Based Access Control kaynaklarınıza erişimi yönetmek için Aboneliği kullanma](/azure/active-directory/role-based-access-control-configure). Abonelik oluşturan yöneticinin bu erişimi örtülü olarak ve diğer yöneticileri Katkıda Bulunan rolüne atama özelliği vardır.

- **Müşteri Anahtarı Microsoft 365** tüm anahtar kasaları için uygulama izinleri vermek üzere wrapKey'i vermeli, kaydırmaKarakKey'i açabilirsiniz ve ilgili Hizmet Sorumlusuna Microsoft 365 gerekir. 

  Hizmet Sorumlusuna erişim izni Microsoft 365, **Set-AzKeyVaultAccessPolicy** cmdlet'ini aşağıdaki söz dizimini kullanarak çalıştırın:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Office 365 appID>
   ```

   Burada:

   - *kasa adı* , oluşturduğunuz anahtar kasanın adıdır.
   - Uygulama Exchange Online Skype Kurumsal *için appID'Office 365 yerine*`00000002-0000-0ff1-ce00-000000000000`
   - Çevrimiçi SharePoint, OneDrive İş ve Teams için *appID'leri Office 365 yerine*`00000003-0000-0ff1-ce00-000000000000`
   - Tüm kiracı kullanıcıları için geçerli olan çok iş yükü ilkesi (Exchange, Teams, Microsoft Bilgi Koruması) için, *Office 365 appID'sini*`c066d759-24ae-40e7-a56f-027002b5d3e4`

  Örnek: E-Exchange Online izinlerini Skype Kurumsal:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
   ```

  Örnek: SharePoint Online, OneDrive İş dosyaları ve Teams ayarlama:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-SP-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
   ```

### <a name="make-sure-soft-delete-is-enabled-on-your-key-vaults"></a>Anahtar kasalar üzerinde yumuşak silmenin etkinleştirildiğinden emin olun

Anahtarlarınızı hızlı bir şekilde kurtar kurtarabilirsiniz; yanlışlıkla veya kötü amaçlı silinen tuşlar nedeniyle hizmet kesintisi yaşama olasılığınız daha düşük olur. Anahtarlarınızı Müşteri Anahtarı ile kullanamadan önce, Yazılımdan Silme olarak adlandırılan bu yapılandırmayı etkinleştirin. Yumuşak Sil'i etkinleştirmek, silme işleminin ardından 90 gün içinde anahtarları veya kasaları yedekten geri yüklemek zorunda kalmadan kurtarmana olanak sağlar.
  
Anahtar kasalar üzerinde Yumuşak Sil'i etkinleştirmek için şu adımları tamamlayın:
  
1. Windows PowerShell ile Azure aboneliğinde oturum Windows PowerShell. Yönergeler için bkz[. Posta ile Azure PowerShell](/powershell/azure/authenticate-azureps).

2. [Get-AzKeyVault](/powershell/module/az.keyvault/get-azkeyvault) cmdlet'ini çalıştırın. Bu örnekte kasa *adı* , yumuşak silmeyi etkinleştiren anahtar kasanın adıdır:

   ```powershell
   $v = Get-AzKeyVault -VaultName <vault name>
   $r = Get-AzResource -ResourceId $v.ResourceId
   $r.Properties | Add-Member -MemberType NoteProperty -Name enableSoftDelete -Value 'True'
   Set-AzResource -ResourceId $r.ResourceId -Properties $r.Properties
   ```

3. **Get-AzKeyVault** cmdlet'i çalıştırarak yumuşak silmenin anahtar kasa için yapılandırıldığından emin olun. Anahtar kasa için yumuşak silme düzgün yapılandırıldıysa, Yumuşak _Silme Etkin_ özelliği Doğru değerini **döndürür**:

   ```powershell
   Get-AzKeyVault -VaultName <vault name> | fl
   ```

### <a name="add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key"></a>Anahtar oluşturarak veya içeri aktararak her bir anahtar kasaya anahtar ekleyin

Azure Key Vault'e anahtar eklemenin iki yolu vardır: Key Vault'de doğrudan anahtar oluşturabilir veya anahtarı içeri aktarabilirsiniz. Doğrudan bu anahtar Key Vault daha az karmaşıktır, ancak anahtarı içeri aktarma işlemi anahtarın nasıl oluşturulacakları üzerinde toplam denetim sağlar. RSA tuşlarını kullanın. Azure Key Vault, üç nokta eğri tuşlarıyla kaydırmayı ve kırpmayı desteklemez.
  
Anahtarı doğrudan anahtar kasasında oluşturmak için [Add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey) cmdlet'ini aşağıdaki gibi çalıştırın:
  
```powershell
Add-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Destination <HSM|Software> -KeyOps wrapKey,unwrapKey
```

Burada:

- *kasa* adı, anahtarı oluşturmak istediğiniz anahtar kasanın adıdır.

- *anahtar* adı, yeni anahtara vermek istediğiniz addır.

  > [!TIP]
  > Anahtar kasaları için yukarıda açıklandığı gibi benzer bir adlandırma kuralı kullanan ad tuşları. Bu şekilde, yalnızca anahtar adını içeren araçlarda dize kendi kendine tarif ediyor.
  
Anahtarı bir HSM ile korumak için, **HSM'yi** _Destination_ parametresinin değeri olarak belirttiğinizden emin olun; aksi takdirde Yazılım'ı **belirtin**.

Örneğin:
  
```powershell
Add-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -Destination HSM -KeyOps wrapKey,unwrapKey
```

Anahtarı doğrudan anahtar kasanıza içeri aktarabilirsiniz, nCipher nShield Donanım Güvenlik Modülü'ne sahip olmak gerekir.
  
Bazı kuruluşlar anahtarlarının kanıtını kurmak için bu yaklaşımı tercih eder ve ardından bu yöntem aşağıdaki testleri de sağlar:
  
- İçeri aktarma için kullanılan araç kümesi, nCipher'dan, sizin oluşturulan anahtarı şifrelemek için kullanılan Key Exchange Key (DEG) anahtarının dışarı aktarılamaz olduğunu ve nCipher tarafından üretilen orijinal bir HSM içinde üretilen bir HSM olduğunu doğrular.

- Araçlaret, Azure Güvenlik Dünya'nın nCipher tarafından üretilen orijinal bir HSM üzerinde de Key Vault bir HSM üzerinde oluşturulmuş olduğunu doğrular. Bu kanıtlama, Microsoft'un orijinal nCipher donanımı da kullanıyor olduğunu kanıtlar.

Yukarıdaki testlerin gerekli olup olmadığını belirlemek için güvenlik grubunuzla birlikte kontrol edin. Şirket içinde anahtar oluşturmanın ve anahtarı anahtar kasanıza aktarmanın ayrıntılı adımları için bkz. Azure Key Vault için [HSM](/azure/key-vault/keys/hsm-protected-keys) korumalı anahtarlar oluşturma ve aktarma. Her bir anahtar kasasında bir anahtar oluşturmak için Azure yönergelerini kullanın.
  
### <a name="check-the-recovery-level-of-your-keys"></a>Anahtarlarınızı kurtarma düzeyini denetleme

Microsoft 365 için Azure Key Vault aboneliğinin İptal Etme olarak ayarlanmış olması ve Müşteri Anahtarı tarafından kullanılan anahtarların yazılımdan silmenin etkinleştirilmesi gerekir. Anahtarlar üzerinde kurtarma düzeyine bakarak abonelik ayarlarınızı onaylayın.
  
Anahtarın kurtarma düzeyini kontrol etmek için, Azure PowerShell cmdlet'ini Get-AzKeyVaultKey çalıştırın:
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name> -Name <key name>).Attributes
```

Kurtarma Düzeyi  özelliği **Recoverable+ProtectedSubscription** değeri dışında bir şey döndürürse, aboneliği İptal Etme listesine eklemiş ve anahtar kasalarının her biri için yumuşak silme özelliğini etkinleştirmiş durumda olduğundan emin olun.
  
### <a name="back-up-azure-key-vault"></a>Azure Key Vault'i Key Vault

Oluşturma işleminin hemen ardından veya anahtarda yapılan herhangi bir değişikliğin ardından, yedeklemeyi hem çevrimiçi hem de çevrimdışı olarak gerçekleştirin ve yedek kopyalarını depolayabilirsiniz. Çevrimdışı kopyaları hiçbir ağa bağlanmayın. Bunun yerine, bunları fiziksel bir güvenli veya ticari depolama tesisinde olduğu gibi çevrimdışı bir yerde depolayabilirsiniz. Bir olağanüstü durum ortaya çıkarsa, yedeğin en az bir kopyasının erişilebilir bir konumda depolanmış olması gerekir. Yedek bloblar, bir anahtarın kalıcı olarak yok Key Vault veya başka bir şekilde işlenebilir durumda olması gereken tek geri yükleme araçtır. Azure Key Vault'Key Vault dışında olan ve Azure Key Vault'e aktarılan anahtarlar yedek olarak nitelendirılmaz, çünkü Müşteri Anahtarının anahtarı kullanması için gereken meta veriler dış anahtarda yoktur. Müşteri Anahtarı ile geri yükleme işlemleri Key Vault azure hizmetlerinden yalnızca bir yedek alınır. Bu nedenle, anahtarı karşıya yükledikten veya Key Vault Azure Key Vault yedeğini oluşturmanız gerekir.
  
Azure veritabanı anahtarının yedeğini Key Vault için[, Backup-AzKeyVaultKey](/powershell/module/az.keyvault/backup-azkeyvaultkey) cmdlet'ini aşağıdaki gibi çalıştırın:

```powershell
Backup-AzKeyVaultKey -VaultName <vault name> -Name <key name>
-OutputFile <filename.backup>
```

Çıkış dosyanıza son eki kullandığıdan emin olun `.backup`.
  
Bu cmdlet'in sonucundaki çıkış dosyası şifrelenir ve Azure veritabanı dışında Key Vault. Yedekleme, yalnızca yedeğin alınarak azure aboneliğine geri yüklenebilir.
  
> [!TIP]
> Çıkış dosyası için kasa adınızla anahtar adınız birleşimini seçin. Bu, dosya adını kendi kendine açıklamaya neden olur. Ayrıca, yedek dosya adlarının harmanlanmayacak şekilde olmasını da sağlar.
  
Örneğin:
  
```powershell
Backup-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -OutputFile Contoso-CK-EX-NA-VaultA1-Key001-Backup-20170802.backup
```

### <a name="validate-azure-key-vault-configuration-settings"></a>Azure Key Vault yapılandırma ayarlarını doğrulama

DEP'de tuşları kullanmadan önce doğrulama isteğe bağlıdır, ancak kesinlikle önerilir. Anahtarlarınızı ve kasalarınızı bu makalede açıklanandan farklı olarak ayarlama adımlarını kullanırsanız, Müşteri Anahtarını yapılandırmadan önce Azure Key Vault kaynaklarınızı durumunu doğrulayın.
  
Anahtarlarınızı 'nın ve işlemlerinin `get`etkinleştirildiğinden `wrapKey``unwrapKey` emin olmak için:
  
[Get-AzKeyVault](/powershell/module/az.keyvault/get-azkeyvault) cmdlet'ini aşağıdaki gibi çalıştırın:
  
```powershell
Get-AzKeyVault -VaultName <vault name>
```

Çıkışta Access İlkesi'ne ve uygun şekilde Exchange Online kimliğini (GUID) veya SharePoint Çevrimiçi kimliğini (GUID) seçin. Yukarıdaki izinlerin üçü de Tuşlara İzinler altında göster gerekir.
  
Erişim ilkesi yapılandırması yanlış olursa, aşağıdaki gibi Set-AzKeyVaultAccessPolicy cmdlet'i çalıştırın:
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Office 365 appID>
```

Örneğin, Exchange Online ve Skype Kurumsal:
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 
-PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
```

Örneğin, SharePoint Online ve OneDrive İş:
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-SP-NA-VaultA1
-PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
```

Anahtarlarınız için bir sona erme tarihi ayarlan olmadığını doğrulamak için [Get-AzKeyVaultKey](/powershell/module/az.keyvault/get-azkeyvault) cmdlet'ini aşağıdaki gibi çalıştırın:
  
```powershell
Get-AzKeyVaultKey -VaultName <vault name>
```

Müşteri Anahtarı süresi dolan bir anahtarı kullanamaz. Süresi dolmuş bir anahtarla denenen işlemler başarısız olur ve bir hizmet kesintisi olabilir. Müşteri Anahtarı ile kullanılan anahtarların son kullanma tarihi olmadığını kesinlikle öneririz. Bir kez ayarlanmış bir son kullanma tarihi kaldırılamaz, ancak farklı bir tarihe değiştirilebilir. Sona erme tarihi ayarlanmış bir anahtar kullanılmalıdırsa, sona erme değerini 31/12/9999 olarak ayarlayın. Son kullanma tarihi 31/12/9999'dan farklı bir tarihe ayarlanmış anahtarlar geçerlilik Microsoft 365 geç olmayacaktır.
  
31/12/9999 dışında bir değere ayarlanmış bir sona erme tarihini değiştirmek için [Update-AzKeyVaultKey](/powershell/module/az.keyvault/update-azkeyvaultkey) cmdlet'ini aşağıdaki gibi çalıştırın:
  
```powershell
Update-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Expires (Get-Date -Date "12/31/9999")
```

> [!CAUTION]
> Müşteri Anahtarı ile birlikte kullanılan şifreleme anahtarlarını son kullanma tarihlerini ayarlayın.
  
### <a name="obtain-the-uri-for-each-azure-key-vault-key"></a>Her Azure Key Vault anahtarının URI'lerini alma

Anahtar kasalarınızı ayarp anahtarlarınızı eklediktan sonra, her bir anahtar kasasında anahtar için URI'yi almak için aşağıdaki komutu çalıştırın. Daha sonra her DEP'yi oluşturmak ve atamak için bu  URL'leri kullan çünkü bu bilgileri güvenli bir yere kaydedin. Bu komutu her anahtar kasa için bir kez çalıştırın.
  
Azure PowerShell:
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name>).Id
```

## <a name="next-steps"></a>Sonraki adımlar

Bu makaledeki adımları tamamlandıktan sonra, DEP'leri oluşturmak ve atamak için hazır oluruz. Yönergeler için bkz. [Müşteri Anahtarını Yönetme](customer-key-manage.md).

## <a name="related-articles"></a>İlgili makaleler

- [Müşteri Anahtarı ile Hizmet şifrelemesi](customer-key-overview.md)

- [Müşteri Anahtarını Yönet](customer-key-manage.md)

- [Bir Müşteri Anahtarını veya uygunluk anahtarını toplama veya döndürme](customer-key-availability-key-roll.md)

- [Kullanılabilirlik anahtarı hakkında bilgi](customer-key-availability-key-understand.md)

- [Hizmet Şifrelemesi](office-365-service-encryption.md)