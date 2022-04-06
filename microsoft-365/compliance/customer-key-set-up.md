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
description: Microsoft 365 için Müşteri Anahtarını ayarlamayı öğrenin.
ms.openlocfilehash: 6a0b186b5c2648d79f1f772e8dd19f1820d5cb9d
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663683"
---
# <a name="set-up-customer-key"></a>Müşteri Anahtarını Ayarlama

Müşteri Anahtarı ile kuruluşunuzun şifreleme anahtarlarını denetler ve ardından Microsoft 365 Microsoft'un veri merkezlerinde bekleyen verilerinizi şifrelemek için bunları kullanacak şekilde yapılandırabilirsiniz. Başka bir deyişle Müşteri Anahtarı, müşterilerin anahtarlarıyla kendilerine ait bir şifreleme katmanı eklemesine olanak tanır.

Office 365 için Müşteri Anahtarı'nın kullanılabilmesi için Önce Azure'i ayarlayın. Bu makalede, gerekli Azure kaynaklarını oluşturmak ve yapılandırmak için izlemeniz gereken adımlar açıklanır ve ardından Office 365'da Müşteri Anahtarı'nı ayarlama adımları sağlanır. Azure'ı ayarladıktan sonra, kuruluşunuzdaki çeşitli Microsoft 365 iş yüklerinde verileri şifrelemek için hangi ilkeyi ve dolayısıyla hangi anahtarların atandığını belirlersiniz. Müşteri Anahtarı hakkında daha fazla bilgi edinmek veya genel bir genel bakış için bkz. [Office 365'de Müşteri Anahtarı ile hizmet şifrelemesi](customer-key-overview.md).
  
> [!IMPORTANT]
> Bu makaledeki en iyi yöntemleri izlemenizi kesinlikle öneririz. Bunlar **TIP** ve **ÖNEMLİ** olarak adlandırılır. Müşteri Anahtarı, kapsamı kuruluşunuzun tamamı kadar büyük olabilecek kök şifreleme anahtarları üzerinde denetim sağlar. Bu, bu anahtarlarla yapılan hataların geniş bir etkiye sahip olabileceği ve hizmet kesintilerine veya verilerinizin geri alınamaz bir şekilde kaybolmasına neden olabileceği anlamına gelir.
  
## <a name="before-you-set-up-customer-key"></a>Müşteri Anahtarını ayarlamadan önce

Başlamadan önce, kuruluşunuz için uygun Azure aboneliklerine ve M365/O365 lisanslarına sahip olduğunuzdan emin olun. Ücretli Azure Aboneliklerini kullanmanız gerekir. Ücretsiz, Deneme, Sponsorluklar, MSDN Abonelikleri ve Eski Destek kapsamındaki abonelikler uygun değildir.

> [!IMPORTANT]
> M365 Müşteri Anahtarı sunan geçerli M365/O365 lisansları şunlardır:
>
> - Office 365 E5
> - Microsoft 365 E5
> - Microsoft 365 E5 Uyumluluk
> - Microsoft 365 E5 Information Protection & İdare SKU'ları
> - FLW için Microsoft 365 Güvenlik ve Uyumluluk

Mevcut Office 365 Gelişmiş Uyumluluk lisansları desteklenmeye devam edecektir.

Bu makaledeki kavramları ve yordamları anlamak için [Azure Key Vault](/azure/key-vault/) belgelerini gözden geçirin. Ayrıca Azure [AD kiracısı](/previous-versions/azure/azure-services/jj573650(v=azure.100)#what-is-an-azure-ad-tenant) gibi Azure'da kullanılan terimleri de tanıyın.
  
Belgelerin ötesinde daha fazla desteğe ihtiyacınız varsa yardım için Microsoft Danışmanlık Hizmetleri (MCS), Premier Alan Mühendisliği (PFE) veya bir Microsoft iş ortağı ile iletişime geçin. Belgeler de dahil olmak üzere Müşteri Anahtarı hakkında geri bildirim sağlamak için fikirlerinizi, önerilerinizi ve perspektiflerinizi customerkeyfeedback@microsoft.com gönderin.
  
## <a name="overview-of-steps-to-set-up-customer-key"></a>Müşteri Anahtarını ayarlama adımlarına genel bakış

Müşteri Anahtarını ayarlamak için bu görevleri listelenen sırayla tamamlayın. Bu makalenin geri kalanında her görev için ayrıntılı yönergeler sağlanır veya işlemdeki her adımla ilgili daha fazla bilgi için bağlantı sağlanır.
  
**Azure'da ve Microsoft FastTrack:**
  
Bu görevlerin çoğunu Azure PowerShell uzaktan bağlanarak tamamlayacaksınız. En iyi sonuçları elde için Azure PowerShell 4.4.0 veya sonraki bir sürümünü kullanın.
  
- [İki yeni Azure aboneliği oluşturma](#create-two-new-azure-subscriptions)

- [Office 365 için Müşteri Anahtarını etkinleştirme isteği gönderme](#submit-a-request-to-activate-customer-key-for-office-365)

- [Zorunlu saklama süresi kullanmak için Azure aboneliklerini kaydetme](#register-azure-subscriptions-to-use-a-mandatory-retention-period)

  Bu kayıt işleminin tamamlanması beş iş günü sürer.
- [İşleme devam etmek için ilgili Microsoft diğer adına başvurun](#contact-the-corresponding-microsoft-alias-to-proceed-with-the-process)

- [Her abonelikte premium Azure Key Vault oluşturma](#create-a-premium-azure-key-vault-in-each-subscription)

- [Her anahtar kasasına izin atama](#assign-permissions-to-each-key-vault)

- [Anahtar kasalarınızda geçici silme özelliğinin etkinleştirildiğinden emin olun](#make-sure-soft-delete-is-enabled-on-your-key-vaults)

- [Anahtar oluşturarak veya içeri aktararak her anahtar kasasına anahtar ekleme](#add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key)

- [Anahtarlarınızın sona erme tarihini doğrulama](#verify-expiration-date-of-your-keys)

- [Anahtarlarınızın kurtarma düzeyini denetleme](#check-the-recovery-level-of-your-keys)

- [Azure Key Vault yedekleme](#back-up-azure-key-vault)

- [Her Azure Key Vault anahtarı için URI'yi alma](#obtain-the-uri-for-each-azure-key-vault-key)
  
## <a name="complete-tasks-in-azure-key-vault-and-microsoft-fasttrack-for-customer-key"></a>Müşteri Anahtarı için Azure Key Vault ve Microsoft FastTrack görevlerini tamamlama

Bu görevleri Azure Key Vault'da tamamlayın. Müşteri Anahtarı ile kullandığınız tüm DEP'ler için bu adımları tamamlamanız gerekir.
  
### <a name="create-two-new-azure-subscriptions"></a>İki yeni Azure aboneliği oluşturma

Müşteri Anahtarı için iki Azure aboneliği gerekir. En iyi uygulama olarak Microsoft, Müşteri Anahtarı ile kullanmak üzere yeni Azure abonelikleri oluşturmanızı önerir. Azure Key Vault anahtarları yalnızca aynı Azure Active Directory (Microsoft Azure Active Directory) kiracıdaki uygulamalar için yetkilendirilebilir. Yeni abonelikleri, DEP'lerin atanacağı kuruluşunuzda kullanılan Azure AD kiracısını kullanarak oluşturmanız gerekir. Örneğin, kuruluşunuzda genel yönetici ayrıcalıklarına sahip iş veya okul hesabınızı kullanma. Ayrıntılı adımlar için bkz. [Azure'a kuruluş olarak kaydolma](/azure/active-directory/fundamentals/sign-up-organization).
  
> [!IMPORTANT]
> Müşteri Anahtarı, her veri şifreleme ilkesi (DEP) için iki anahtar gerektirir. Bunu başarmak için iki Azure aboneliği oluşturmanız gerekir. En iyi uygulama olarak Microsoft, kuruluşunuzun ayrı üyelerinin her abonelikte bir anahtar yapılandırmanızı önerir. Bu Azure aboneliklerini yalnızca Office 365 şifreleme anahtarlarını yönetmek için kullanmanız gerekir. Bu, operatörlerinizden birinin sorumlu oldukları anahtarları yanlışlıkla, kasıtlı olarak veya kötü amaçlı olarak silmesi veya başka bir şekilde yanlış yönetmesi durumunda kuruluşunuzu korur.

Kuruluşunuz için oluşturabileceğiniz Azure aboneliklerinin sayısı için pratik bir sınır yoktur. Bu en iyi yöntemlerin kullanılması, Müşteri Anahtarı tarafından kullanılan kaynakların yönetilmesine yardımcı olurken insan hatasının etkisini en aza indirir.
  
### <a name="submit-a-request-to-activate-customer-key-for-office-365"></a>Office 365 için Müşteri Anahtarını etkinleştirme isteği gönderme

İki yeni Azure aboneliğini oluşturduktan sonra Microsoft FastTrack [portalında](https://fasttrack.microsoft.com/) uygun Müşteri Anahtarı teklif isteğini göndermeniz gerekir. Teklif formunda kuruluşunuzdaki yetkili atamalar hakkında yaptığınız seçimler, Müşteri Anahtarı kaydının tamamlanması için kritik ve gereklidir. Kuruluşunuzda seçilen rollerdeki görevliler, Müşteri Anahtarı veri şifreleme ilkesiyle kullanılan tüm anahtarları iptal etme ve yok etme isteklerinin orijinalliğini güvence altına alır. Kuruluşunuz için kullanmayı planladığınız her Müşteri Anahtarı DEP türü için bu adımı bir kez gerçekleştirmeniz gerekir.

**FastTrack ekibi Müşteri Anahtarı ile ilgili yardım sağlamaz. Office 365, formu göndermenizi sağlamak ve Müşteri Anahtarı ile ilgili teklifleri izlememize yardımcı olmak için FastTrack portalını kullanır. FastTrack isteğini gönderdikten sonra, ekleme işlemini başlatmak için ilgili Müşteri Anahtarı ekleme ekibine ulaşın.**
  
Müşteri Anahtarını etkinleştirme teklifi göndermek için şu adımları tamamlayın:
  
1. Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak [Microsoft FastTrack portalında](https://fasttrack.microsoft.com/) oturum açın.

2. Oturum açtıktan sonra uygun etki alanını seçin.

3. Seçili etki alanı için üst gezinti çubuğundan **Hizmet iste'yi** seçin ve kullanılabilir tekliflerin listesini gözden geçirin.

4. Sizin için geçerli olan teklifin bilgi kartını seçin:

   - **Birden çok Microsoft 365 iş yükü:** **Microsoft 365 teklifi için şifreleme anahtarı yardımı isteme'yi** seçin.

   - **Exchange Online ve Skype Kurumsal:** **Exchange teklifi için Şifreleme anahtarı yardımı isteme'yi** seçin.

   - **Çevrimiçi, OneDrive ve Teams dosyaları SharePoint:** **SharePoint ve OneDrive İş teklifi için şifreleme anahtarı yardımı isteme'yi** seçin.

5. Teklif ayrıntılarını gözden geçirdikten sonra **2. adıma devam et'i** seçin.

6. Teklif formundaki tüm geçerli ayrıntıları ve istenen bilgileri doldurun. Şifreleme anahtarlarının ve verilerin kalıcı ve geri alınamaz şekilde yok edilmesini onaylama yetkisi vermek istediğiniz kuruluşunuzdaki memurların seçimlerine özellikle dikkat edin. Formu tamamladıktan sonra **Gönder'i** seçin.

### <a name="register-azure-subscriptions-to-use-a-mandatory-retention-period"></a>Zorunlu saklama süresi kullanmak için Azure aboneliklerini kaydetme

Kök şifreleme anahtarlarının geçici veya kalıcı olarak kaybedilmesi hizmet işlemini kesintiye uğratabilir ve hatta yıkıcı olabilir ve veri kaybına neden olabilir. Bu nedenle Müşteri Anahtarı ile kullanılan kaynaklar güçlü koruma gerektirir. Müşteri Anahtarı ile kullanılan tüm Azure kaynakları, varsayılan yapılandırmanın ötesinde koruma mekanizmaları sunar. Azure aboneliklerini *zorunlu saklama süresi* için etiketleyebilir veya kaydedebilirsiniz. Zorunlu saklama süresi, Azure aboneliğinizin hemen ve geri alınamaz iptalini engeller. Azure aboneliklerini zorunlu saklama süresine kaydetmek için gereken adımlar, Microsoft 365 ekibiyle işbirliği gerektirir. Bu işlemin tamamlanması beş iş günü sürer. Daha önce zorunlu saklama süresi bazen "İptal Etmeyin" olarak da adlandırılırdı.
  
> [!IMPORTANT]
> Microsoft 365 ekibine başvurmadan önce, Müşteri Anahtarı ile kullandığınız **her** Azure aboneliği için aşağıdaki adımları gerçekleştirmeniz gerekir. Başlamadan önce [Azure PowerShell Az](/powershell/azure/new-azureps-module-az) modülünün yüklü olduğundan emin olun.

1. Azure PowerShell ile oturum açın. Yönergeler için bkz. [Azure PowerShell ile oturum açma](/powershell/azure/authenticate-azureps).

2. Aboneliklerinizi zorunlu saklama süresi kullanacak şekilde kaydetmek için Register-AzProviderFeature cmdlet'ini çalıştırın. Her abonelik için bu eylemi tamamlayın.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzProviderFeature -FeatureName mandatoryRetentionPeriodEnabled -ProviderNamespace Microsoft.Resources
   ```

### <a name="contact-the-corresponding-microsoft-alias-to-proceed-with-the-process"></a>İşleme devam etmek için ilgili Microsoft diğer adına başvurun

>[!NOTE]
> İlgili Microsoft diğer adıyla iletişim kurmadan önce M365 Müşteri Anahtarı için FastTrack isteklerinizi tamamladığınızdan emin olun.

- Tek tek Exchange Online posta kutularına DEP atamak üzere Müşteri Anahtarı'nın etkinleştirilmesi için [exock@microsoft.com](mailto:exock@microsoft.com) başvurun.

- Tüm kiracı kullanıcıları için çevrimiçi SharePoint ve OneDrive İş içeriği (Teams dosyaları dahil) şifrelemek üzere DEP'ler atamak üzere Müşteri Anahtarı'nın etkinleştirilmesi için [spock@microsoft.com](mailto:spock@microsoft.com) başvurun.

- Tüm kiracı kullanıcıları için birden çok Microsoft 365 iş yükünde (Exchange Online, Teams, MIP EDM) içeriği şifrelemek üzere DEP'ler atamak üzere Müşteri Anahtarı'nın etkinleştirilmesi için [m365-ck@service.microsoft.com](mailto:m365-ck@service.microsoft.com) başvurun.

- E-postanıza aşağıdaki bilgileri ekleyin:

     **Konu**: Müşteri Anahtarı \<*Your tenant's fully qualified domain name*\>

     **Gövde**: Eklemek istediğiniz Müşteri Anahtarı hizmetlerinin **her** biri için FastTrack İstek Kimliklerini ve abonelik kimliklerini ekleyin. Bu abonelik kimlikleri, her abonelik için zorunlu saklama süresini ve Get-AzProviderFeature çıkışını tamamlamak istediğiniz kimliklerdir.

Bu işlemin tamamlanması için Hizmet Düzeyi Sözleşmesi (SLA), Microsoft'a aboneliklerinizi zorunlu saklama süresi kullanmak üzere kaydettiğinizi bildirdikten (ve doğruladıktan) sonra beş iş günüdür.

### <a name="verify-the-status-of-each-your-azure-subscriptions"></a>Azure Aboneliklerinizin her birinin durumunu doğrulama

Microsoft'tan kaydın tamamlandığını belirten bir bildirim aldıktan sonra, Get-AzProviderFeature komutunu aşağıdaki gibi çalıştırarak kaydınızın durumunu doğrulayın. Doğrulanırsa, Get-AzProviderFeature komutu **Kayıt Durumu** özelliği için **Kayıtlı** değerini döndürür. **Her** abonelik için bu adımı tamamlayın.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Get-AzProviderFeature -ProviderNamespace Microsoft.Resources -FeatureName mandatoryRetentionPeriodEnabled
   ```

İşlemi tamamlamak için Register-AzResourceProvider komutunu çalıştırın. **Her** abonelik için bu adımı tamamlayın.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   ```

   ```powershell
   Register-AzResourceProvider -ProviderNamespace Microsoft.KeyVault
   ```

> [!TIP]
> Devam etmeden önce, aşağıdaki görüntüde olduğu gibi 'RegistrationState' değerinin 'Registered' olarak ayarlandığından emin olun.
>
> ![Zorunlu Saklama Süresi](../media/MandatoryRetentionPeriod.png)

### <a name="create-a-premium-azure-key-vault-in-each-subscription"></a>Her abonelikte premium Azure Key Vault oluşturma

Anahtar kasası oluşturma adımları [Azure Key Vault Kullanmaya Başlama](/azure/key-vault/general/overview) bölümünde belgelenmiştir. Bu, Azure PowerShell yükleme ve başlatma, Azure aboneliğinize bağlanma, kaynak grubu oluşturma ve bu kaynak grubunda anahtar kasası oluşturma konusunda size yol gösterir.
  
Bir anahtar kasası oluşturduğunuzda bir SKU seçmeniz gerekir: Standart veya Premium. Standart SKU, Azure Key Vault anahtarlarının yazılımla korunmasına olanak tanır; Donanım Güvenlik Modülü (HSM) anahtar koruması yoktur ve Premium SKU, Key Vault anahtarların korunması için HSM'lerin kullanılmasına olanak tanır. Müşteri Anahtarı, SKU kullanan anahtar kasalarını kabul eder, ancak Microsoft yalnızca Premium SKU'yu kullanmanızı kesinlikle önerir. Her iki tür anahtara sahip işlemlerin maliyeti aynıdır, bu nedenle maliyetteki tek fark HSM korumalı anahtarlar için aylık maliyettir. Ayrıntılar için bkz. [Key Vault fiyatlandırması](https://azure.microsoft.com/pricing/details/key-vault/).
  
> [!IMPORTANT]
> Üretim verileri için Premium SKU anahtar kasalarını ve HSM korumalı anahtarları kullanın ve test ve doğrulama amacıyla yalnızca Standart SKU anahtar kasalarını ve anahtarlarını kullanın.
  
Müşteri Anahtarını kullanacağınız her Microsoft 365 hizmeti için, oluşturduğunuz iki Azure aboneliğinin her birinde bir anahtar kasası oluşturun. Örneğin, Müşteri Anahtarının Exchange Online, SharePoint Online ve çok iş yükü senaryolarında DEP'leri kullanmasını sağlamak için üç çift anahtar kasası oluşturacaksınız.
  
Kasaları ilişkilendirebileceğiniz DEP'nin amaçlanan kullanımını yansıtan anahtar kasaları için bir adlandırma kuralı kullanın. Adlandırma kuralı önerileri için aşağıdaki En İyi Yöntemler bölümüne bakın.
  
Her veri şifreleme ilkesi için ayrı, eşleştirilmiş bir kasa kümesi oluşturun. Exchange Online için, ilkeyi posta kutusuna atadığınızda veri şifreleme ilkesinin kapsamı sizin tarafınızdan seçilir. Bir posta kutusuna yalnızca bir ilke atanabilir ve en fazla 50 ilke oluşturabilirsiniz. SharePoint Online ilkesinin kapsamı, bir kuruluştaki coğrafi konumdaki veya *coğrafi* konumdaki tüm verileri içerir. Birden çok iş yükü ilkesinin kapsamı, tüm kullanıcılar için desteklenen iş yükleri genelindeki tüm verileri içerir.

Anahtar kasalarının oluşturulması azure kaynak gruplarının oluşturulmasını da gerektirir çünkü anahtar kasaları depolama kapasitesine (küçük olsa da) ve Key Vault günlüğe kaydetmeye ihtiyaç duyar ve etkinleştirilirse depolanan veriler de oluşturur. En iyi yöntem olarak Microsoft, tüm ilgili Müşteri Anahtarı kaynaklarını yönetecek yönetici kümesiyle uyumlu yönetimle her kaynak grubunu yönetmek için ayrı yöneticiler kullanılmasını önerir.
  
### <a name="assign-permissions-to-each-key-vault"></a>Her anahtar kasasına izin atama

Uygulamanıza bağlı olarak her anahtar kasası için üç ayrı izin kümesi tanımlamanız gerekir. Örneğin, aşağıdakilerin her biri için bir izin kümesi tanımlamanız gerekir:
  
- Kuruluşunuz **için anahtar kasanızın** günlük yönetimini üstleyen anahtar kasası yöneticileri. Bu görevler yedekleme, oluşturma, alma, içeri aktarma, listeleme ve geri yüklemeyi içerir.

  > [!IMPORTANT]
  > Anahtar kasası yöneticilerine atanan izin kümesi anahtarları silme iznini içermez. Bu kasıtlı ve önemli bir uygulamadır. Şifreleme anahtarlarını silme işlemi genellikle yapılmaz çünkü bunu yapmak verileri kalıcı olarak yok eder. En iyi yöntem olarak, bu izni varsayılan olarak anahtar kasası yöneticilerine vermeyin. Bunun yerine, bunu anahtar kasasına katkıda bulunanlar için ayırın ve sonuçları net bir şekilde anladıktan sonra bunu kısa süreli olarak bir yöneticiye atayın.
  
  Bu izinleri kuruluşunuzdaki bir kullanıcıya atamak için Azure PowerShell ile Azure aboneliğinizde oturum açın. Yönergeler için bkz. [Azure PowerShell ile oturum açma](/powershell/azure/authenticate-azureps).

  - Gerekli izinleri atamak için Set-AzKeyVaultAccessPolicy cmdlet'ini çalıştırın.

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user> -PermissionsToKeys create,import,list,get,backup,restore
   ```

   Örneğin:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -UserPrincipalName alice@contoso.com -PermissionsToKeys create,import,list,get,backup,restore
   ```

- Azure Key Vault üzerindeki izinleri değiştirebilen **anahtar kasası katkıda bulunanları**. Çalışanlar ayrıldığında veya ekibinize katıldığında bu izinleri değiştirmeniz gerekir. Anahtar kasası yöneticilerinin bir anahtarı silmek veya geri yüklemek için yasal olarak izne ihtiyacı olduğu nadir durumlarda izinleri de değiştirmeniz gerekir. Bu anahtar kasası katkıda bulunanları kümesine anahtar kasanızda **Katkıda Bulunan** rolü verilmesi gerekir. Azure Resource Manager kullanarak bu rolü atayabilirsiniz. Ayrıntılı adımlar için bkz. [Azure abonelik kaynaklarınıza erişimi yönetmek için Role-Based Access Control kullanma](/azure/active-directory/role-based-access-control-configure). Abonelik oluşturan yöneticinin bu erişimi örtük olarak ve katkıda bulunan rolüne diğer yöneticileri atama özelliği vardır.

- Müşteri Anahtarı için kullandığınız her anahtar kasası için **uygulamaları Microsoft 365 izinleri**, wrapKey vermeniz, anahtar kaldırmanız ve ilgili Microsoft 365 Hizmet Sorumlusu için izinler almanız gerekir.

  Microsoft 365 Hizmet Sorumlusuna izin vermek için aşağıdaki söz dizimini kullanarak **Set-AzKeyVaultAccessPolicy** cmdlet'ini çalıştırın:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Office 365 appID>
   ```

   Nerede:
   - *kasa adı* , oluşturduğunuz anahtar kasasının adıdır.
   - Exchange Online ve Skype Kurumsal için *Office 365 appID* değerini şununla değiştirin:`00000002-0000-0ff1-ce00-000000000000`
   - SharePoint Online, OneDrive İş ve Teams dosyaları için *Office 365 appID* değerini şununla değiştirin:`00000003-0000-0ff1-ce00-000000000000`
   - Tüm kiracı kullanıcıları için geçerli olan çok iş yükü ilkesi (Exchange, Teams, Microsoft Bilgi Koruması) için *Office 365 appID* değerini şununla değiştirin:`c066d759-24ae-40e7-a56f-027002b5d3e4`

  Örnek: Exchange Online ve Skype Kurumsal için izinleri ayarlama:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
   ```

  Örnek: SharePoint Online, OneDrive İş ve Teams dosyaları için izinleri ayarlama:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-SP-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
   ```

  *Get-AzKeyVault* cmdlet'ini çalıştırarak **her** anahtar kasasına *Get, wrapKey ve unwrapKey'in* verildiğini onaylayın.

   ```powershell
   Get-AzKeyVault -VaultName <vault name> | fl
   ```  

> [!Tip]
> Devam etmeden önce, anahtar kasası için izinlerin düzgün yapılandırıldığından emin olun; *Anahtarlara İzinler* **wrapKey, unwrapKey, get** döndürür.
> Eklediğiniz doğru hizmete yönelik izinleri düzeltdiğinizden emin olun. Her hizmetin *Görünen Adı* aşağıda listelenmiştir:  
  >
  > - Exchange Online ve Skype Kurumsal: *Office 365 Exchange Online*
  > - SharePoint Online, OneDrive ve Teams dosyaları: *Office 365 SharePoint Online*
  > - Birden çok Microsoft 365 iş yükü: *M365DataAtRestEncryption*
  >  
  > Örneğin, aşağıdaki kod parçacığı, izinlerin M365DataAtRestEncryption için yapılandırıldığından emin olmak için bir örnektir. *mmcexchangevault* adlı bir kasaya sahip aşağıdaki cmdlet aşağıdaki alanları görüntüler.
  >
  > ```powershell
  >   Get-AzKeyVault -VaultName mmcexchangevault | fl
  >   ```  
  >
  >
  > ![Exchange Online Müşteri Anahtarı için şifreleme şifreleri.](../media/KeyVaultPermissions.png)

### <a name="make-sure-soft-delete-is-enabled-on-your-key-vaults"></a>Anahtar kasalarınızda geçici silme özelliğinin etkinleştirildiğinden emin olun

Anahtarlarınızı hızlı bir şekilde kurtarabildiğinizde, yanlışlıkla veya kötü amaçlı olarak silinen anahtarlar nedeniyle genişletilmiş hizmet kesintisi yaşama olasılığınız daha düşüktür. Anahtarlarınızı Müşteri Anahtarı ile kullanabilmek için önce Geçici Silme olarak adlandırılan bu yapılandırmayı etkinleştirin. Geçici Silme'yi etkinleştirmek, anahtarları veya kasaları silme işleminden sonraki 90 gün içinde yedeklemeden geri yüklemenize gerek kalmadan kurtarmanıza olanak tanır.
  
Anahtar kasalarınızda Geçici Silme'yi etkinleştirmek için şu adımları tamamlayın:
  
1. Windows PowerShell ile Azure aboneliğinizde oturum açın. Yönergeler için bkz. [Azure PowerShell ile oturum açma](/powershell/azure/authenticate-azureps).

2. [Get-AzKeyVault](/powershell/module/az.keyvault/get-azkeyvault) cmdlet'ini çalıştırın. Bu örnekte *kasa adı* , geçici silmeyi etkinleştirdiğiniz anahtar kasasının adıdır:

   ```powershell
   $v = Get-AzKeyVault -VaultName <vault name>
   $r = Get-AzResource -ResourceId $v.ResourceId
   $r.Properties | Add-Member -MemberType NoteProperty -Name enableSoftDelete -Value 'True'
   Set-AzResource -ResourceId $r.ResourceId -Properties $r.Properties
   ```

3. **Get-AzKeyVault** cmdlet'ini çalıştırarak anahtar kasası için geçici silmenin yapılandırıldığını onaylayın. Geçici silme anahtar kasası için düzgün yapılandırıldıysa Geçici *Silme Etkin* özelliği **True** değerini döndürür:

   ```powershell
   Get-AzKeyVault -VaultName <vault name> | fl
   ```

> [!TIP]
> Devam etmeden önce 'Geçici Silme Etkinleştirildi mi?' aşağıdaki görüntüde olduğu gibi 'True' olarak ayarlanır.
>
> <img src="../media/SoftDeleteEnabled.png" alt="SoftDelete" width="400"/>

### <a name="add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key"></a>Anahtar oluşturarak veya içeri aktararak her anahtar kasasına anahtar ekleme

Azure Key Vault anahtar eklemenin iki yolu vardır; doğrudan Key Vault'da anahtar oluşturabilir veya bir anahtarı içeri aktarabilirsiniz. Doğrudan Key Vault'de anahtar oluşturmak daha az karmaşıktır, ancak bir anahtarı içeri aktarmak anahtarın nasıl oluşturulduğu üzerinde tam denetim sağlar. RSA anahtarlarını kullanın. Azure Key Vault, eliptik eğri anahtarlarla sarmalama ve sarmalama kaldırmayı desteklemez.

Her kasaya anahtar ekleme yönergeleri için bkz. [Add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey).

 Şirket içinde anahtar oluşturma ve anahtar kasanıza aktarmaya yönelik ayrıntılı adımlar için bkz. [Azure Key Vault için HSM korumalı anahtarlar oluşturma ve aktarma](/azure/key-vault/keys/hsm-protected-keys). Her anahtar kasasında anahtar oluşturmak için Azure yönergelerini kullanın.

### <a name="verify-expiration-date-of-your-keys"></a>Anahtarlarınızın sona erme tarihini doğrulama

Anahtarlarınız için son kullanma tarihinin ayarlı olmadığını doğrulamak için [Get-AzKeyVaultKey](/powershell/module/az.keyvault/get-azkeyvault) cmdlet'ini aşağıdaki gibi çalıştırın:
  
```powershell
Get-AzKeyVaultKey -VaultName <vault name>
```

Müşteri Anahtarı süresi dolmuş bir anahtarı kullanamaz. Süresi dolmuş bir anahtarla denenen işlemler başarısız olur ve hizmet kesintisine neden olabilir. Müşteri Anahtarı ile kullanılan anahtarların son kullanma tarihi olmadığını kesinlikle öneririz. Ayarlandıktan sonra sona erme tarihi kaldırılamaz, ancak farklı bir tarihe değiştirilebilir. Son kullanma tarihi ayarlanmış bir anahtar kullanılması gerekiyorsa, süre sonu değerini 31.12.9999 olarak değiştirin. Son kullanma tarihi 31/12/9999 dışında bir tarihe ayarlanmış anahtarlar Microsoft 365 doğrulamayı geçirmez.
  
31.12.9999 dışında bir değere ayarlanmış bir sona erme tarihini değiştirmek için [Update-AzKeyVaultKey](/powershell/module/az.keyvault/update-azkeyvaultkey) cmdlet'ini aşağıdaki gibi çalıştırın:
  
```powershell
Update-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Expires (Get-Date -Date "12/31/9999")
```

> [!CAUTION]
> Müşteri Anahtarı ile kullandığınız şifreleme anahtarlarında son kullanma tarihleri ayarlamayın.  

### <a name="check-the-recovery-level-of-your-keys"></a>Anahtarlarınızın kurtarma düzeyini denetleme

Microsoft 365, Azure Key Vault aboneliğinin İptal Etmeyin olarak ayarlanmasını ve Müşteri Anahtarı tarafından kullanılan anahtarların geçici silme özelliğinin etkinleştirilmesini gerektirir. Anahtarlarınızın kurtarma düzeyine bakarak abonelik ayarlarınızı onaylayabilirsiniz.
  
Bir anahtarın kurtarma düzeyini denetlemek için Azure PowerShell Get-AzKeyVaultKey cmdlet'ini aşağıdaki gibi çalıştırın:
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name> -Name <key name>).Attributes
```

> [!Tip]
> Devam etmeden önce *Kurtarma Düzeyi* özelliği **Recoverable+ProtectedSubscription** değeri dışında bir değer döndürürse abonelikte *MandatoryRetentionPeriodEnabled* özelliğini kaydettiğinizden ve anahtar kasalarınızın her birinde geçici silme özelliğini etkinleştirdiğinizden emin olun.
>
>    <img src="../media/RecoveryLevel.png" alt="drawing" width="500"/>

### <a name="back-up-azure-key-vault"></a>Azure Key Vault yedekleme

Oluşturma işleminden veya anahtarda yapılan herhangi bir değişikliğin hemen ardından yedekleme gerçekleştirin ve yedeklemenin kopyalarını hem çevrimiçi hem de çevrimdışı olarak depolayın.
Azure Key Vault anahtarının yedeğini oluşturmak için [Backup-AzKeyVaultKey](/powershell/module/az.keyvault/backup-azkeyvaultkey) cmdlet'ini çalıştırın.

### <a name="obtain-the-uri-for-each-azure-key-vault-key"></a>Her Azure Key Vault anahtarı için URI'yi alma

Anahtar kasalarınızı ayarladıktan ve anahtarlarınızı ekledikten sonra, her anahtar kasasındaki anahtarın URI'sini almak için aşağıdaki komutu çalıştırın. Bu URI'leri daha sonra her DEP'i oluşturur ve atarken kullanırsınız, bu nedenle bu bilgileri güvenli bir yere kaydedin. Her anahtar kasası için bu komutu bir kez çalıştırın.
  
Azure PowerShell içinde:
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name>).Id
```

## <a name="next-steps"></a>Sonraki adımlar

Bu makaledeki adımları tamamladıktan sonra, DEP'leri oluşturmaya ve atamaya hazırsınız demektir. Yönergeler için bkz. [Müşteri Anahtarını Yönetme](customer-key-manage.md).

## <a name="related-articles"></a>İlgili makaleler

- [Müşteri Anahtarı ile hizmet şifrelemesi](customer-key-overview.md)

- [Müşteri Anahtarını Yönet](customer-key-manage.md)

- [Bir Müşteri Anahtarını veya uygunluk anahtarını toplama veya döndürme](customer-key-availability-key-roll.md)

- [Kullanılabilirlik anahtarı hakkında bilgi edinin](customer-key-availability-key-understand.md)

- [Hizmet Şifrelemesi](office-365-service-encryption.md)
