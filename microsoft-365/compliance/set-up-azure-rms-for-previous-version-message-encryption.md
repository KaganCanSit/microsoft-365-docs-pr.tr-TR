---
title: İleti Şifreleme'nin önceki sürümü için Azure Hak Yönetimi'i ayarlama
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 10/30/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 2cba47b3-f09e-4911-9207-ac056fcb9db7
description: Bu sürümlerden önceki Office 365 İleti Şifrelemesi, Microsoft Azure Yönetimi'ne (daha önce Hak Yönetimi Windows Azure Active Directory bağlıdır).
ms.openlocfilehash: c94497069d929dd3819e3ced915c8e778e983c10
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983719"
---
# <a name="set-up-azure-rights-management-for-the-previous-version-of-message-encryption"></a>İleti Şifreleme'nin önceki sürümü için Azure Hak Yönetimi'i ayarlama

Bu konu başlığı altında, Azure Information Protection'ın bir parçası olan Azure Rights Management'ı (RMS) etkinleştirmeniz ve ardından OME'nin önceki sürümüyle kullanmak üzere ayarlamak için Office 365 İleti Şifrelemesi açıklanmıştır.

## <a name="this-article-only-applies-to-the-previous-version-of-ome"></a>Bu makale yalnızca OME'nin önceki sürümü için geçerlidir

Henüz organizasyonlarınızı yeni OME özelliklerine taşıdıysanız, ancak OME'nin zaten dağıtmış olduğu bilgiler, bu makaledeki bilgiler organizasyonunız için geçerlidir. Microsoft, yeni OME özelliklerine, kurum için uygun olduğu anda bir plan yapmanızı önerir. Yönergeler için bkz[. Yeni özellik Office 365 İleti Şifrelemesi ayarlama](set-up-new-message-encryption-capabilities.md). Yeni becerilerin nasıl ilk kez çalışması hakkında daha fazla bilgi almak için [bkz. Office 365 İleti Şifrelemesi](ome.md). Bu makalenin kalan bölümü, yeni OME özelliklerini piyasaya çıkarmadan önce OME davranışını ifade eder.

## <a name="prerequisites-for-using-the-previous-version-of-office-365-message-encryption"></a>Office 365 İleti Şifrelemesi'un önceki sürümünü kullanmak için önkoşullar
<a name="warmprereqs"> </a>

Office 365 İleti Şifrelemesi (OME) IRM de içinde olmak üzere, Azure Hak Yönetimi 'ne (Azure RMS) bağlıdır. Azure RMS, Azure Information Protection tarafından kullanılan koruma teknolojisidir. OME'i kullanmak için, Exchange Online Exchange Online Protection azure hak yönetimi aboneliği de içeren bir iş aboneliği içermesi gerekir.
  
- Aboneliğinizin neleri dahil olduğundan emin değilseniz İleti İlkesi, Exchange Online ve Uyumluluk ile ilgili hizmet [açıklamalarına bakın](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance).

- Azure Hak Yönetimi'ne sahipsiniz ancak azure Exchange Online veya Exchange Online Protection için ayarlanmazsa, bu makalede Azure Hak Yönetimi'nin nasıl etkinleştirildi ve ardından OME'i Azure Hak Yönetimi ile çalışacak şekilde ayarlamanın en iyi yolu açıklanmıştır.

- OME'i Exchange Online veya Exchange Online Protection için Azure Hak Yönetimi ile birlikte çalışacak şekilde önceden ayarladıysanız, nasıl ayar kullandığınıza bağlı olarak OME'ye ve onun yeni özelliklerini kullanmaya hemen başlayabilirsiniz. Bu makalede, OME'yi doğru ayarip ayarlamamanızı, kurulumlarınızı değiştirmeniz gerekirse ne olacağını ve kurulumlarınızı değiştirmemenizi seçerseniz ne olacağını nasıl belirleyecekleri açıklanmıştır. Örneğin, yeni özellikleri kullanmak için Azure RMS'yi OME ile birlikte kullanabilirsiniz. Yeni özellikleri şirket içi Active Directory RMS ile birlikte kullanaabilirsiniz.

## <a name="activate-azure-rights-management-for--the-previous-version-of-ome-in-office-365"></a>yeni sürümde OME'nin önceki sürümü için Azure Hak Yönetimi'Office 365

Azure Hak Yönetimi'ne etkinleştirerek, organizasyonu kullananların göndermekte olduğu iletilere bilgi koruması uygulayabileceklerini ve Azure Hak Yönetimi hizmeti tarafından korunan iletileri ve dosyaları açabileceklerini etkinleştirmeniz gerekir. Yönergeler için bkz. [Azure Hak Yönetimini Etkinleştirme](/azure/information-protection/activate-service). Etkinleştirmeyi tamamlandıktan sonra buraya geri dönüp bu makaledeki görevlerle devam gerçekleştirin.
  
## <a name="set-up-the-previous-version-of-ome-to-use-azure-rms-by-importing-trusted-publishing-domains-tpds"></a>Güvenilir yayımlama etki alanlarını (TPD) içeri aktararak Azure RMS'yi kullanmak için OME'nin önceki sürümünü ayarlama

TPD, kuruma ilişkin hak yönetimi ayarları hakkında bilgi içeren bir XML dosyasıdır. Örneğin, TPD, sertifikaları ve lisansları imzalamak ve şifrelemek için kullanılan sunucu lisans sertifikası (SLC), lisans ve yayımlama için kullanılan URL'ler gibi bilgiler içerir. TPD'yi, diğer kullanıcı izinlerini kullanarak Windows PowerShell.
  
> [!IMPORTANT]
> Daha önce, TPD'leri Active Directory Rights Management service'den (AD RMS) kuruluşa aktarmayı seçebilirsiniz. Bununla birlikte, bunu yapmak yeni OME özelliklerini kullanmamanizi engel olur ve önerilmez. Organizasyonunız şu anda bu şekilde yapılandırılmışsa, Microsoft şirket içi Active Directory RMS'niz'den bulut tabanlı Azure Information Protection'a geçiş için bir plan oluşturmanızı önerir. Daha fazla bilgi için bkz [. AD RMS'den Azure Information Protection'a uygulama](/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms). Azure Information Protection'a geçişi tamamlayana kadar yeni OME özelliklerini kullanamayacaksiniz.
  
 **TPD'leri Azure RMS'den içeri aktarma**
  
1. [Bağlan PowerShell Exchange Online'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kuruluşun coğrafi konumuyla ilgili anahtar paylaşan URL'yi seçin:

|**Konum**|**Anahtar paylaşım konumu URL'si**|
|:-----|:-----|
|Kuzey Amerika  <br/> |https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|Avrupa Birliği  <br/> |https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|Asya  <br/> |https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|Güney Amerika  <br/> |https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|Office 365 (Government Community Cloud)  <br/> Bu RMS anahtar paylaşım konumu, Kamu SKU'ları için Office 365 müşterilere ayrılmıştır.  <br/> |https://sp-rms.govus.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
  
3. [Set-IRMConfiguration cmdlet'ini aşağıdaki gibi çalıştırarak](/powershell/module/exchange/set-irmconfiguration) anahtar paylaşım konumunu yapılandırma: 

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "<RMSKeySharingURL >"
   ```
  
   Örneğin, organizasyonunız Kuzey Amerika'da yer alıyorsa anahtar paylaşım konumunu yapılandırmak için:

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
   ```

4. TPD'yi Azure Rights Management'tan içeri aktaracak şekilde , [Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain) cmdlet'ini -RMSOnline anahtarıyla çalıştırın: 

   ```powershell
   Import-RMSTrustedPublishingDomain -RMSOnline -Name "<TPDName> "
   ```

   Burada  *TPDAdı*  , TPD için kullanmak istediğiniz addır. Örneğin, "Contoso Kuzey Amerika TPD". 

5. Kuruluşu Azure Rights Management hizmetini kullanmak üzere başarıyla yapılandırmış olduğunu doğrulamak için, [Test-IRMConfiguration cmdlet'ini](/powershell/module/exchange/test-irmconfiguration) -RMSOnline anahtarıyla aşağıdaki gibi çalıştırın:

   ```powershell
   Test-IRMConfiguration -RMSOnline
   ```

   Başka şeylerin yanında, bu cmdlet, Azure Rights Management hizmetiyle bağlantı sorunlarını denetler, TPD'yi indirir ve geçerliliğini denetler.

6. Azure Hak Yönetimi şablonlarının aşağıdaki gibi [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) cmdlet'ini çalıştırarak Azure Hak Yönetimi şablonlarının şu Web üzerinde Outlook Outlook: 

   ```powershell
   Set-IRMConfiguration -ClientAccessServerEnabled $false
   ```

7. Bulut tabanlı e-posta kuruluşlarınız için Azure Hak Yönetimi'ne olanak sağlamak ve azure'u aşağıdaki gibi Azure Hak Yönetimi'nde kullanmak üzere yapılandırmak için [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) cmdlet'ini Office 365 İleti Şifrelemesi:

   ```powershell
   Set-IRMConfiguration -InternalLicensingEnabled $true
   ```

8. TPD'yi başarıyla içe aktarılmış ve Azure Hak Yönetimi'yi etkinleştirmiş olmak için, Test-IRMConfiguration cmdlet'ini kullanarak Azure Hak Yönetimi işlevselliğini test edin. Ayrıntılar için, [Test-IRMConfiguration'daki](/powershell/module/exchange/test-irmconfiguration) "Örnek 1"e bakın.

## <a name="i-have-the-previous-version-of-ome-set-up-with-active-directory-rights-management-not-azure-information-protection-what-do-i-do"></a>Azure Information Protection'ı değil Active Directory Rights Management ile ayarlanmış önceki OME sürümüm var, ne yapabilirim?
<a name="importTPDs"> </a>

Var olan e-posta Office 365 İleti Şifrelemesi Active Directory Rights Management ile kullanmaya devam edersiniz, ancak yeni OME özelliklerini yapılandıramıyor veya kullanamazsanız. Bunun yerine, Azure Information Protection'a geçiş yapmak gerekir. Geçiş hakkında ve bunun organizasyonunız için ne anlama geldiğini görmek için bkz. [AD RMS'den Azure Information Protection'a geçiş](/information-protection/deploy-use/prepare-environment-adrms).
  
## <a name="next-steps"></a>Sonraki adımlar
<a name="importTPDs"> </a>

Azure Hak Yönetimi kurulumunu tamamlandıktan sonra, yeni OME özelliklerini etkinleştirmek için bkz. [Azure Information Protection'ın Office 365 İleti Şifrelemesi özelliklerini ayarlama.](./set-up-new-message-encryption-capabilities.md)
  
Yeni OME özelliklerini kullanmak üzere organizasyon organizasyonlarınızı ayardikten sonra, e-posta iletilerini yeni OME özellikleriyle korumak için posta akış kurallarını [tanımlamaya hazır olursanız](define-mail-flow-rules-to-encrypt-email.md).
  
## <a name="related-topics"></a>İlgili konular
<a name="importTPDs"> </a>

[Şifreleme Office 365](encryption.md)
  
[E-Office 365'de şifreleme hakkında teknik başvuru ayrıntıları](technical-reference-details-about-encryption.md)
  
[Azure Hak Yönetimi nedir?](/information-protection/understand-explore/what-is-azure-rms)