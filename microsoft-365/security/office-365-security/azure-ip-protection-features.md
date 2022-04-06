---
title: Azure Information Protection'daki koruma özellikleri var olan kiracılara sunuyor
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 7ad6f58e-65d7-4c82-8e65-0b773666634d
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Bu makalede, Azure Güvenlik Hizmetleri'nin koruma özelliklerine Information Protection
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 80256c3dc4ba8b460b1c5052081aa030a608a7d1
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471571"
---
# <a name="protection-features-in-azure-information-protection-rolling-out-to-existing-tenants"></a>Azure Information Protection'daki koruma özellikleri var olan kiracılara sunuyor

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Office 365 için Microsoft Defender plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Temmuz 2018'den itibaren, bilgilerin korunmasına yardımcı olmak için tüm Azure Information Protection kiracılarında Azure Information Protection koruma özellikleri varsayılan olarak açıktır. Azure Information Protection'Office 365 koruma özellikleri önceden Hak Yönetimi veya Azure RMS Office 365 olarak biliniyor vardı. Kuruluşta bir Office E3 hizmet planı veya daha yüksek bir hizmet planı varsa, bu özellikleri ne zaman Information Protection Azure Information Protection bilgileri korumaya başlayabilirsiniz.

## <a name="changes-beginning-july-1-2018"></a>1 Temmuz 2018'den itibaren yapılan değişiklikler

1 Temmuz 2018'den başlayarak, Microsoft, Azure Information Protection'da aşağıdaki abonelik planlarından birini kullanarak tüm kuruluşlar için koruma özelliğini etkinleştirecek:

- Office 365 İleti Şifrelemesi Office 365 E3 E5, Microsoft E3 ve E5, Office 365 A1, A3 ve A5 ile G3 ve G5'Office 365 sunulur. Azure Destek Hizmetleri tarafından desteklenen yeni koruma özelliklerini almak için ek lisanslara Information Protection.

- Ayrıca, yeni Office 365 İleti Şifrelemesi özelliklerini almak için aşağıdaki planlara Azure Information Protection Plan 1'i de ebilirsiniz: Exchange Online Plan 1, Exchange Online Plan 2, Office 365 F1, Microsoft 365 İş Temel, Microsoft 365 İş Standart E1'i Office 365 Kurumsal.

- İleti Şifreleme özelliğinden yararlanan Office 365, bu özellik kapsamında lisans sahibi olması gerekir.

- Tam liste için, İleti [Şifrelemesi'Exchange Online hizmet](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description) açıklamalarını Office 365 bakın.

Kiracı yöneticileri, koruma durumunu yönetici portalında Office 365 kontrol edebilirsiniz.

:::image type="content" source="../../media/303453c8-e4a5-4875-b49f-e80c3eb7b91e.png" alt-text="Etkinleştirilmiş Office 365 hakları yönetimi" lightbox="../../media/303453c8-e4a5-4875-b49f-e80c3eb7b91e.png":::

## <a name="why-are-we-making-this-change"></a>Bu değişikliği neden yapıyoruz?

Office 365 İleti Şifrelemesi, Azure Şifrelemesi'nin koruma Information Protection. Office 365 İleti Şifrelemesi'ne yapılan son geliştirmelerin ve Microsoft 365'te bilgi korumasına daha fazla yatırımlarımızın merkezinde, geçmişte şifreleme teknolojilerinin ayarlamakta zor olduğu için kuruluşların koruma yeteneklerimizi açmasını ve kullanmasını kolaylaştırıyoruz. Azure Information Protection'ta koruma özelliklerini varsayılan olarak ayarerek, hassas verilerinizi korumaya hızlı bir şekilde başlatabilirsiniz.

## <a name="does-this-impact-me"></a>Bu beni etkiliyor mu?

Organizasyonunız uygun bir lisans Office 365 satın aldı ise, kiracınız bu değişiklikden etki edilir.

> [!IMPORTANT]
> Şirket içi ortamınıza Active Directory Rights Management Services (AD RMS) kullanıyorsanız, biz bu değişikliği sonraki 30 gün içinde yayımlamadan önce bu değişikliği hemen geri çevirmelisiniz veya Azure Information Protection'e geçirmelisiniz. Geri çıkma hakkında bilgi için bkz. "AD RMS'yi kullanmak istiyorum, nasıl iptal musunuz?" bu makalenin devamsında bulabilirsiniz. Geçirmeyi tercih ediyorsanız, bkz. [AD RMS'den Azure'a Information Protection.](/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)

## <a name="can-i-use-azure-information-protection-with-active-directory-rights-management-services-ad-rms"></a>Azure Information Protection'i Active Directory Rights Management Services (AD RMS) ile kullanabilir miyim?

Hayır. Bu desteklenen bir dağıtım senaryosu değildir. Ek geri bırakma adımlarını almadan, bazı bilgisayarlar otomatik olarak Azure Rights Management hizmetini kullanmaya başlayabilir ve ayrıca AD RMS kümenize bağlanabilirsiniz. Bu senaryo desteklenmiyor ve güvenilir olmayan sonuçlara sahip olduğu için, bu yeni özellikleri sunduğumuzda sonraki 30 gün içinde bu değişikliği geri bırakmanız önemlidir. Geri çıkma hakkında bilgi için bkz. "AD RMS'yi kullanmak istiyorum, nasıl iptal musunuz?" bu makalenin devamsında bulabilirsiniz. Geçirmeyi tercih ediyorsanız, bkz. [AD RMS'den Azure'a geçiş Information Protection.](/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)

## <a name="how-do-i-know-if-im-using-ad-rms"></a>Nasıl yaparım? RMS'yi kullanmakta olup olduğumu biliyor musunuz?

AD RMS'yi dağıtınca kontrol etmek için bu yönergeleri ( [AD RMS)](/azure/information-protection/deploy-use/prepare-environment-adrms) Active Directory Rights Management Services Azure Rights Management ortamını hazırlama konusunda verilen şu yönergeleri kullanın:

1. İsteğe bağlı olsa da, çoğu AD RMS dağıtımları etki alanı bilgisayarlarında AD RMS kümesini bulmaları için hizmet bağlantı noktasını (SCP) Active Directory'de yayımlar.

   Active Directory'de yayımlanmış bir SCP'niz olup olmadığını görmek için ADSI Düzenleme'yi kullanın: CN=Configuration [sunucu adı], CN=Services, CN=RightsManagementServices, CN=SCP

2. SCP kullanmazsanız, Windows RMS kümesine bağlı olan bilgisayarların istemci tarafı hizmet bulma veya lisans yeniden yönlendirmesi için Windows defteri kullanılarak yapılandırılması gerekir: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC\ServiceLocation`.

Bu kayıt defteri yapılandırmaları hakkında daha fazla bilgi için bkz. Windows defteri kullanarak istemci [tarafı](/azure/information-protection/rms-client/client-deployment-notes#enabling-client-side-service-discovery-by-using-the-windows-registry) hizmet bulma özelliğini etkinleştirme ve Lisans sunucusu trafiğini [yeniden yönlendirme](/azure/information-protection/rms-client/client-deployment-notes#redirecting-licensing-server-traffic).

## <a name="i-use-ad-rms-how-do-i-opt-out"></a>AD RMS'yi kullanıyor, nasıl gerilim?

Yaklaşan değişiklikten vazgeçmek için şu adımları tamamlayın:

1. Kuruluşta genel yönetici izinleri olan bir iş veya okul hesabı kullanarak yeni bir oturum Windows PowerShell bu hesaba bağlanarak Exchange Online. Yönergeler için bkz. [Bağlan PowerShell'Exchange Online yükleme](/powershell/exchange/connect-to-exchange-online-powershell).

2. Aşağıdaki söz Set-IRMConfiguration kullanarak Set-IRMConfiguration cmdlet'ini çalıştırın:

  ```powershell
  Set-IRMConfiguration -AutomaticServiceUpdateEnabled $false
  ```

## <a name="what-can-i-expect-after-this-change-has-been-made"></a>Bu değişiklik yapıldıktan sonra neler beklim?

Bu etkinleştirildikten sonra, devre dışı bırakmamanız şartıyla[, Microsoft Ignite 2017'de duyurulan ve Azure Ignite 2017'de](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801) duyurulan yeni Office 365 İleti Şifrelemesi'nin yeni sürümünü kullanmaya başlayabilir ve Azure Information Protection.

:::image type="content" source="../../media/599ca9e7-c05a-429e-ae8d-359f1291a3d8.png" alt-text="E-postada OME korumalı Web üzerinde Outlook" lightbox="../../media/599ca9e7-c05a-429e-ae8d-359f1291a3d8.png":::

Yeni iyileştirmeler hakkında daha fazla bilgi için bkz. [İleti Office 365'ne bakın](../../compliance/ome.md).