---
title: Mevcut kiracılara Azure Information Protection'ın koruma özellikleri
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
description: Bu makalede, Azure Information Protection'daki koruma özelliklerinde yapılan değişiklikler açıklanmıştır.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a11821e6c2165c79e286612b89d42f7e19b1593d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988609"
---
# <a name="protection-features-in-azure-information-protection-rolling-out-to-existing-tenants"></a>Mevcut kiracılara Azure Information Protection'ın koruma özellikleri

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Office 365 için Microsoft Defender plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Temmuz 2018'den itibaren, tüm Azure Information Protection uygun kiracıları, Azure Information Protection'daki koruma özelliklerini varsayılan olarak açık olacak. Azure Information Protection'daki koruma özellikleri önceden Hak Yönetimi veya Azure RMS Office 365 olarak biliniyor vardı. Kuruluşta bir E3 Office veya daha yüksek bir hizmet planı varsa, bu özellikleri sunarken Azure Information Protection aracılığıyla bilgileri korumaya başlayabilirsiniz.

## <a name="changes-beginning-july-1-2018"></a>1 Temmuz 2018'den itibaren yapılan değişiklikler

1 Temmuz 2018'den itibaren Microsoft, Azure Information Protection'da aşağıdaki abonelik planlarından birini kullanarak tüm kuruluşlar için koruma özelliğini etkinleştirecek:

- Office 365 İleti Şifrelemesi, Office 365 E3 ve E5, Microsoft E3 ve E5, Office 365 A1, A3 ve A5 ile G3 ve G5'Office 365 sunulur. Azure Information Protection tarafından desteklenen yeni koruma özelliklerini almak için ek lisanslara ihtiyacınız yok.

- Ayrıca, yeni özellik özelliklerini almak için aşağıdaki planlara Azure Information Protection Plan 1'i de Office 365 İleti Şifrelemesi: Exchange Online Plan 1, Exchange Online Plan 2, Office 365 F1, Microsoft 365 İş Temel, Microsoft 365 İş Standart E1'i Office 365 Kurumsal.

- Bu özellikten yararlanan Office 365 İleti Şifrelemesi bu özellik kapsamında lisans sahibi olması gerekir.

- Tam liste için bkz. [Exchange Online hizmet açıklamalarını](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description) Office 365 İleti Şifrelemesi.

Kiracı yöneticileri, koruma durumunu yönetici portalında Office 365 kontrol edebilirsiniz.

![Dosyada hak yönetiminin etkinleştirildikten Office 365 ekran görüntüsü.](../../media/303453c8-e4a5-4875-b49f-e80c3eb7b91e.png)

## <a name="why-are-we-making-this-change"></a>Bu değişikliği neden yapıyoruz?

Office 365 İleti Şifrelemesi, Azure Information Protection'daki koruma yeteneklerine sahip olur. Office 365 İleti Şifrelemesi'a yapılan son geliştirmelerin ve Microsoft 365'te bilgi korumasına daha fazla yatırımlarımızın merkezinde, geçmişte şifreleme teknolojilerinin ayarlamakta zor olduğu için kuruluşların koruma yeteneklerimizi açmasını ve kullanmasını kolaylaştırıyoruz. Azure Information Protection'daki koruma özelliklerini varsayılan olarak açmayla, hassas verilerinizi korumaya hızlı bir şekilde başabilirsiniz.

## <a name="does-this-impact-me"></a>Bu beni etkiliyor mu?

Organizasyonunız uygun bir lisans Office 365 satın aldı ise, kiracınız bu değişiklikden etki edilir.

> [!IMPORTANT]
> Şirket içi ortamınıza Active Directory Rights Management Services (AD RMS) kullanıyorsanız, bu değişikliği sonraki 30 gün içinde yayımlamadan önce bu değişikliği hemen geri çevirmelisiniz veya Azure Information Protection'a geçirmelisiniz. Geri çıkma hakkında bilgi için bkz. "AD RMS'yi kullanmak istiyorum, nasıl iptal musunuz?" bu makalenin devamsında bulabilirsiniz. Geçirmeyi tercih ediyorsanız, bkz[. AD RMS'den Azure Information Protection'a geçiş.](/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)

## <a name="can-i-use-azure-information-protection-with-active-directory-rights-management-services-ad-rms"></a>Azure Information Protection'i Active Directory Rights Management Services (AD RMS) ile kullanabilir miyim?

Hayır. Bu desteklenen bir dağıtım senaryosu değildir. Ek geri bırakma adımlarını almadan, bazı bilgisayarlar otomatik olarak Azure Rights Management hizmetini kullanmaya başlayabilir ve ayrıca AD RMS kümenize bağlanabilirsiniz. Bu senaryo desteklenmiyor ve güvenilir olmayan sonuçlara sahip olduğu için, bu yeni özellikleri sunduğumuzda sonraki 30 gün içinde bu değişikliği geri bırakmanız önemlidir. Geri çıkma hakkında bilgi için bkz. "AD RMS'yi kullanmak istiyorum, nasıl iptal musunuz?" bu makalenin devamsında bulabilirsiniz. Geçirmeyi tercih ediyorsanız bkz. [AD RMS'den Azure Information Protection'a geçiş.](/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)

## <a name="how-do-i-know-if-im-using-ad-rms"></a>AD RMS'yi kullanıyor olup olduğumu nasıl bilim?

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

Bu etkinleştirildikten sonra, devre dışı bırakmamanız şartıyla [Microsoft Ignite 2017'de](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801) duyurulan yeni Office 365 İleti Şifrelemesi sürümünü kullanmaya başlayabilir ve Azure Information Protection'ın şifreleme ve koruma yetenekleriden faydalanabilirsiniz.

![Dosyada OME korumalı bir iletiyi gösteren Web üzerinde Outlook.](../../media/599ca9e7-c05a-429e-ae8d-359f1291a3d8.png)

Yeni iyileştirmeler hakkında daha fazla bilgi için bkz. [Office 365 İleti Şifrelemesi](../../compliance/ome.md).