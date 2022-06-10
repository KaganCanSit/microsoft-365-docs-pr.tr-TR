---
title: İleti Şifrelemesi'nin önceki sürümü için Azure Rights Management ayarlama
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
description: Office 365 İleti Şifrelemesi'nin önceki sürümü Microsoft Azure Rights Management (daha önce Windows Azure Active Directory Rights Management olarak bilinirdi) bağlıdır.
ms.openlocfilehash: 66447d601d86f1863cf060a3ad097686bb58be98
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016250"
---
# <a name="set-up-azure-rights-management-for-the-previous-version-of-message-encryption"></a>İleti Şifrelemesi'nin önceki sürümü için Azure Rights Management ayarlama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Bu konu başlığı altında, Office 365 İleti Şifrelemesi'nin (OME) önceki sürümüyle kullanılmak üzere Azure Information Protection'nin bir parçası olan Azure Rights Management'ı (RMS) etkinleştirmek ve ayarlamak için izlemeniz gereken adımlar açıklanmaktadır.

## <a name="this-article-only-applies-to-the-previous-version-of-ome"></a>Bu makale yalnızca OME'nin önceki sürümü için geçerlidir

Kuruluşunuzu henüz Microsoft Purview İleti Şifrelemesi'ne taşımadıysanız ancak OME'yi zaten dağıttıysanız, bu makaledeki bilgiler kuruluşunuz için geçerlidir. Microsoft, kuruluşunuz için makul olduğu anda Microsoft Purview İleti Şifrelemesi'ne geçmek için bir plan yapmanızı önerir. Yönergeler için bkz. [Microsoft Purview İleti Şifrelemesini Ayarlama](set-up-new-message-encryption-capabilities.md). Yeni özelliklerin ilk olarak nasıl çalıştığı hakkında daha fazla bilgi edinmek istiyorsanız bkz. [İleti Şifrelemesi](ome.md). Bu makalenin geri kalanı, Microsoft Purview İleti Şifrelemesi'nin yayımlanmasından önceki OME davranışını ifade eder.

## <a name="prerequisites-for-using-the-previous-version-of-office-365-message-encryption"></a>Office 365 İleti Şifrelemesi'nin önceki sürümünü kullanma önkoşulları
<a name="warmprereqs"> </a>

IRM de dahil olmak üzere Office 365 İleti Şifrelemesi (OME), Azure Rights Management'ne (Azure RMS) bağlıdır. Azure RMS, Azure Information Protection tarafından kullanılan koruma teknolojisidir. OME'yi kullanmak için kuruluşunuzun azure Rights Management aboneliği içeren bir Exchange Online veya Exchange Online Protection aboneliği içermesi gerekir.

- Aboneliğinizin ne içerdiğinden emin değilseniz [İleti İlkesi, Kurtarma ve Uyumluluk](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance) için Exchange Online hizmet açıklamalarına bakın.

- Azure Rights Management'niz varsa ancak Exchange Online veya Exchange Online Protection için ayarlanmadıysa, bu makalede Azure Rights Management'nin nasıl etkinleştirilmediği açıklanır ve ardından OME'yi Azure ile çalışacak şekilde ayarlamanın en iyi yolu açıklanır Rights Management.

- OME'yi Exchange Online veya Exchange Online Protection için Azure Rights Management ile çalışacak şekilde ayarladıysanız, OME'yi ve yeni özelliklerini kullanmaya hemen başlayabilirsiniz. Bu makalede, OME'yi doğru ayarlayıp ayarlamadığınız nasıl belirleneceği, kurulumunuzu değiştirmeniz gerekirse ne yapmanız gerektiği ve kurulumunuzu değiştirmemeyi seçerseniz ne olacağı açıklanmaktadır. Örneğin, yeni özellikleri kullanmak için Azure RMS'yi OME ile kullanmanız gerekir. Yeni özellikleri bir şirket içi Active Directory RMS ile kullanamazsınız.

## <a name="activate-azure-rights-management-for--the-previous-version-of-ome-in-office-365"></a>Office 365'da OME'nin önceki sürümü için Azure Rights Management etkinleştirme

Kuruluşunuzdaki kullanıcıların gönderdikleri iletilere bilgi koruması uygulayabilmesi ve Azure Rights Management hizmeti tarafından korunan iletileri ve dosyaları açabilmesi için Azure Rights Management etkinleştirmeniz gerekir. Yönergeler için bkz[. Azure Rights Management etkinleştirme](/azure/information-protection/activate-service). Etkinleştirmeyi tamamladıktan sonra buraya dönün ve bu makaledeki görevlere devam edin.

## <a name="set-up-the-previous-version-of-ome-to-use-azure-rms-by-importing-trusted-publishing-domains-tpds"></a>Güvenilen yayımlama etki alanlarını (TPD) içeri aktararak OME'nin önceki sürümünü Azure RMS kullanacak şekilde ayarlama

TPD, kuruluşunuzun hak yönetimi ayarları hakkında bilgi içeren bir XML dosyasıdır. Örneğin, TPD sertifikaları ve lisansları imzalamak ve şifrelemek için kullanılan sunucu lisans sertifikası (SLC), lisanslama ve yayımlama için kullanılan URL'ler vb. hakkında bilgi içerir. PowerShell kullanarak TPD'yi kuruluşunuza aktarabilirsiniz.

> [!IMPORTANT]
> Daha önce, TPD'leri Active Directory Rights Management hizmetinden (AD RMS) kuruluşunuza aktarmayı seçebilirsiniz. Ancak bunu yaptığınızda Microsoft Purview İleti Şifrelemesi'nin kullanılması önerilmez. Kuruluşunuz şu anda bu şekilde yapılandırılmışsa Microsoft, şirket içi Active Directory RMS'nizden bulut tabanlı Azure Information Protection geçiş planı oluşturmanızı önerir. Daha fazla bilgi için bkz. [AD RMS'den Azure'a geçiş Information Protection](/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms). Azure Information Protection geçişini tamamlayana kadar Microsoft Purview İleti Şifrelemesi'ni kullanamazsınız.

**TPD'leri Azure RMS'den içeri aktarmak için**:

1. [PowerShell'i Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kuruluşunuzun coğrafi konumuna karşılık gelen anahtar paylaşım URL'sini seçin:

   |Konum|Anahtar paylaşım konumu URL'si|
   |---|---|
   |Kuzey Amerika|<https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc>|
   |Avrupa Birliği|<https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc>|
   |Asya|<https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc>|
   |Güney Amerika|<https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc>|
   |Kamu için Office 365 (Government Community Cloud)  <br/> Bu RMS anahtar paylaşımı konumu, Kamu SKU'ları için Office 365 satın alan müşteriler için ayrılmıştır.|<https://sp-rms.govus.aadrm.com/TenantManagement/ServicePartner.svc>|

3. [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) cmdlet'ini aşağıdaki gibi çalıştırarak anahtar paylaşımı konumunu yapılandırın:

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "<RMSKeySharingURL >"
   ```

   Örneğin, kuruluşunuz Kuzey Amerika konumundaysa anahtar paylaşım konumunu yapılandırmak için:

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
   ```

4. TPD'yi Azure Rights Management'dan içeri aktarmak için -RMSOnline anahtarıyla [Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain) cmdlet'ini çalıştırın:

   ```powershell
   Import-RMSTrustedPublishingDomain -RMSOnline -Name "<TPDName> "
   ```

   Burada  *TPDName, TPD*  için kullanmak istediğiniz addır. Örneğin, "Contoso Kuzey Amerika TPD".

5. Kuruluşunuzu Azure Rights Management hizmetini kullanacak şekilde başarıyla yapılandırdığınızdan emin olmak için-RMSOnline anahtarıyla [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration) cmdlet'ini aşağıdaki gibi çalıştırın:

   ```powershell
   Test-IRMConfiguration -RMSOnline
   ```

   Diğer şeylerin yanında, bu cmdlet Azure Rights Management hizmetiyle bağlantıyı denetler, TPD'yi indirir ve geçerliliğini denetler.

6. Azure Rights Management şablonlarının Web üzerinde Outlook ve Outlook kullanılabilir olmasını devre dışı bırakmak için [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) cmdlet'ini aşağıdaki gibi çalıştırın:

   ```powershell
   Set-IRMConfiguration -ClientAccessServerEnabled $false
   ```

7. Bulut tabanlı e-posta kuruluşunuzda Azure Rights Management etkinleştirmek ve Office 365 İleti Şifrelemesi için Azure Rights Management kullanmak üzere yapılandırmak için [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) cmdlet'ini aşağıdaki gibi çalıştırın:

   ```powershell
   Set-IRMConfiguration -InternalLicensingEnabled $true
   ```

8. TPD'yi başarıyla içeri aktarıp Azure Rights Management etkinleştirdiğinizden emin olmak için Test-IRMConfiguration cmdlet'ini kullanarak Azure Rights Management işlevselliğini test edin. Ayrıntılar için bkz. [Test-IRMConfiguration'daki](/powershell/module/exchange/test-irmconfiguration) "Örnek 1".

## <a name="i-have-the-previous-version-of-ome-set-up-with-active-directory-rights-management-not-azure-information-protection-what-do-i-do"></a>Azure Information Protection değil Active Directory Rights Management OME'nin önceki sürümünü ayarladım, ne yapmalıyım?
<a name="importTPDs"> </a>

Active Directory Rights Management ile mevcut Office 365 İleti Şifrelemesi posta akışı kurallarınızı kullanmaya devam edebilirsiniz, ancak Microsoft Purview İleti Şifrelemesi'ni yapılandıramaz veya kullanamazsınız. Bunun yerine Azure Information Protection'a geçmeniz gerekir. Geçiş ve bunun kuruluşunuz için ne anlama geldiğini öğrenmek için bkz. [AD RMS'den Azure'a geçiş Information Protection](/information-protection/deploy-use/prepare-environment-adrms).

## <a name="next-steps"></a>Sonraki adımlar
<a name="importTPDs"> </a>

Azure Rights Management kurulumunu tamamladıktan sonra, Microsoft Purview İleti Şifrelemesi'nin etkinleştirilmesini istiyorsanız bkz. [Microsoft Purview İleti Şifrelemesini Ayarlama](./set-up-new-message-encryption-capabilities.md).

Kuruluşunuzu Microsoft Purview İleti Şifrelemesi'ni kullanacak şekilde ayarladıktan sonra, [Posta akışı kurallarını tanımlamaya](define-mail-flow-rules-to-encrypt-email.md) hazır olursunuz.

## <a name="related-topics"></a>İlgili konular
<a name="importTPDs"> </a>

[Office 365'de şifreleme](encryption.md)

[Office 365'de şifreleme hakkında teknik başvuru ayrıntıları](technical-reference-details-about-encryption.md)

[Azure Rights Management nedir?](/information-protection/understand-explore/what-is-azure-rms)
