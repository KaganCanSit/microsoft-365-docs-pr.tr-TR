---
title: Varsayılan paylaşım bağlantı türünü yapılandırmak için duyarlılık etiketlerini kullanma
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: SharePoint ve OneDrive'daki siteler ve belgeler için varsayılan paylaşım bağlantı türünü yapılandırmak için duyarlılık etiketlerini kullanın.
ms.openlocfilehash: ca4b74c2fb25c4f1f1ef96b8ae0241481358797d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628583"
---
# <a name="use-sensitivity-labels-to-configure-the-default-sharing-link-type-for-sites-and-documents-in-sharepoint-and-onedrive"></a>SharePoint ve OneDrive'da siteler ve belgeler için varsayılan paylaşım bağlantı türünü yapılandırmak için duyarlılık etiketlerini kullanma

>*[Güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[Duyarlılık etiketleri](sensitivity-labels.md) Microsoft Purview uyumluluk portalı gördüğünüz ayarlara ek bir yapılandırma olarak, sharepoint sitesi veya OneDrive hesabı ve tek tek belgeler için varsayılan paylaşım bağlantı türü ayarlarını yapılandırmak için bu etiketleri kullanabilirsiniz. Bu ayarlar otomatik olarak seçilir, ancak Office uygulamalarında **Paylaş** düğmesini seçtiklerinde kullanıcılara yüksek oranda görünmez. Örnek olarak:

![Örnek varsayılan paylaşım bağlantısı iletişim kutusu.](../media/default-sharing-link-example.png)

Varsayılan paylaşım bağlantı türü, kullanıcılar dosya ve klasörleri paylaştığında otomatik olarak seçilen kapsamı (kim) ve izinleri (görüntüleme veya düzenleme) ayarlar. Kullanıcılar paylaşım bağlantısını göndermeden önce her zaman bu varsayılan ayarları geçersiz kılabilir, ancak seçtiğiniz ayarlar güvenli bir temel sağlar. Genellikle, kullanıcılar paylaşımdan önce ayarları değiştirmez.

Site düzeyinde (SharePoint sitesi veya OneDrive hesabı), duyarlılık etiketleri SharePoint yönetim merkezinde bir site için yapılandırılabilir varsayılan paylaşım bağlantı türünü ayarlamak için kullanışlı bir alternatif sağlar. Daha fazla bilgi için SharePoint [belgelerinden sitenin varsayılan bağlantı türünü değiştirme](/sharepoint/change-default-sharing-link) bölümüne bakın.

Bu site düzeyi yapılandırma, belgeleri aynı duyarlılık düzeyine sahip olan SharePoint siteleri için iyi çalışır. Ancak, siteler daha kısıtlayıcı ayarlar gerektiren daha yüksek duyarlılık düzeyine sahip bazı belgeler içeriyorsa, varsayılan paylaşım bağlantı türü için farklı ayarlara sahip bir duyarlılık etiketi yapılandırabilir ve sonra bu etiketi belgelere uygulayabilirsiniz.

Sitenin varsayılan paylaşım bağlantı türü ayarlarına sahip olduğu ve bu sitedeki bir belgenin farklı varsayılan bağlantı türü ayarlarına sahip olduğu bu senaryoda, kullanıcı belge için paylaşım seçeneğini seçtiğinde daha kısıtlayıcı kapsam ayarları uygulanır. Örneğin:

- Site için varsayılan paylaşım bağlantı türünün kapsamı kuruluşunuzdaki herkes tarafından belirlenmiştir. Bu sitedeki bir belge, varsayılan paylaşım bağlantı türü belirli kişilere ayarlanmış olarak etiketlenmiştir. Kullanıcı bu belgeyi paylaştığında, seçilen varsayılan paylaşım bağlantı türünün kapsamı belirli kişilere göre belirlenir.

- Site için varsayılan paylaşım bağlantı türünün kapsamı, düzenleme izinlerine sahip belirli kişilere göre belirlenmiştir. Bu sitedeki bir belge, kuruluştaki herkese varsayılan paylaşım bağlantı türü ayarlanmış ve görüntüleme izinlerine sahip olarak etiketlenmiştir. Kullanıcı bu belgeyi paylaştığında, seçilen varsayılan paylaşım bağlantı türünün kapsamı düzenleme izinlerine sahip belirli kişilere göre belirlenir.

Belgeler için varsayılan bağlantı türünü yapılandırmak, site düzeyi ayarı olmadan da uygun olabilir. Örneğin, SharePoint siteleri genellikle aynı türde belgeleri barındıracak şekilde düzenlenmiş olsa da, OneDrive hesapları için böyle bir durum söz konusu değildir. Kullanıcılar genellikle kişisel ve iş belgelerinin bir karışımı da dahil olmak üzere çok çeşitli dosyaları OneDrive'a kaydeder. Kullanıcının OneDrive hesabı için tüm belgeler için varsayılan bağlantı türü ayarlamak büyük olasılıkla pratik değildir, ancak tek tek belgeler yine de bu ayarlardan yararlanabilir. Örneğin:

- **Çok Gizli** etiketli belgeler, paylaşımı kuruluştaki herhangi biri yerine belirli kişilerle kısıtlayan bir varsayılan paylaşım bağlantı türüne sahiptir.
- **Genel** etiketli belgeler, paylaşımı kuruluşunuzdaki kişilerle kısıtlayan bir varsayılan paylaşım bağlantı türüne sahiptir.
- **Kişisel** etiketli belgeler, bağlantıya sahip herkese paylaşıma izin veren varsayılan bir paylaşım bağlantı türüne sahiptir.

## <a name="prerequisites"></a>Önkoşullar

Siteler için varsayılan paylaşım bağlantı türünü uygulamak için kapsayıcılar için duyarlılık etiketlerinin etkinleştirilmesi gerekir. Bu özellik kiracınız için henüz etkinleştirilmediyse bkz. [Kapsayıcılar için duyarlılık etiketlerini etkinleştirme ve etiketleri eşitleme](sensitivity-labels-teams-groups-sites.md#how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels).

SharePoint ve OneDrive'daki belgeler için varsayılan paylaşım bağlantı türünü uygulamak için, bu hizmetler için duyarlılık etiketlerinin etkinleştirilmesi gerekir. Bu özellik kiracınız için henüz etkinleştirilmediyse bkz. [SharePoint ve OneDrive için duyarlılık etiketlerini etkinleştirme (kabul etme)](sensitivity-labels-sharepoint-onedrive-files.md#how-to-enable-sensitivity-labels-for-sharepoint-and-onedrive-opt-in).

PowerShell oturumunda, varsayılan paylaşım bağlantı türü [ayarlarını yapılandırmak için Office 365 Güvenlik & Uyumluluğu PowerShell'e bağlanmanız](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell) gerekir.

> [!NOTE]
> Gerekli olmasa da, önce [Microsoft Purview uyumluluk portalı duyarlılık etiketleri oluşturup yapılandırmak ve](create-sensitivity-labels.md) ardından bu etiketleri varsayılan paylaşım bağlantı türünü yapılandıran ayarlarla değiştirmek en kolay seçenektir.

## <a name="how-to-configure-settings-for-the-default-sharing-link-type"></a>Varsayılan paylaşım bağlantı türü için ayarları yapılandırma

Varsayılan paylaşım bağlantı türünün yapılandırma ayarları [, Güvenlik & Uyumluluğu](/powershell/exchange/scc-powershell) PowerShell'in [Set-Label](/powershell/module/exchange/set-label) ve [New-Label](/powershell/module/exchange/new-labelpolicy) cmdlet'leri ile PowerShell *AdvancedSettings* parametresini kullanır:

- **DefaultSharingScope**: Kullanılabilir değerler şunlardır:
    - **SpecificPeople**: Site için varsayılan paylaşım bağlantısını "Belirli kişiler" bağlantısına ayarlar
    - **Kuruluş**: Site için varsayılan paylaşım bağlantısını "kuruluş" bağlantısına veya şirket tarafından paylaşılabilir bağlantıya ayarlar
    - **Herkes**: Site için varsayılan paylaşım bağlantısını Anonim Erişim veya Herkes bağlantısına ayarlar

- **DefaultShareLinkPermission**: Kullanılabilir değerler şunlardır:
    - **Görünüm**: Site için varsayılan bağlantı iznini "görüntüleme" izinlerini ayarlar
    - **Düzenle**: Site için varsayılan bağlantı iznini "düzenleme" izinlerine ayarlar

Bu iki ayar ve değer, [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) cmdlet'indeki *DefaultSharingScope* ve *DefaultShareLinkPermission* parametrelerinin eşdeğeridir.

Duyarlılık etiketi **GUID'sinin 8faca7b8-8d20-48a3-8ea2-0f96310a848e** olduğu PowerShell örnekleri:

- Varsayılan paylaşım bağlantı türünü SpecificPeople olarak ayarlamak için:
    
    ````powershell
    Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultSharingScope="SpecificPeople"}
    ````

- Varsayılan paylaşım bağlantı türü izinlerini Düzenle olarak ayarlamak için:
    
    ````powershell
    Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultShareLinkPermission="Edit"}
    ````

PowerShell gelişmiş ayarlarını belirtme konusunda daha fazla yardım için bkz. [Gelişmiş ayarları belirtmek için PowerShell ipuçları](create-sensitivity-labels.md#powershell-tips-for-specifying-the-advanced-settings).

Bir sitenin varsayılan paylaşım bağlantı türünün ayarlarını yapılandırmak için, [duyarlılık etiketinin kapsamı](sensitivity-labels.md#label-scopes), duyarlılık etiketini Microsoft Purview uyumluluk portalı oluştururken **Gruplar & sitelerini** içermelidir. Oluşturulduktan sonra, bunu **Etiketler** sayfasındaki **Kapsam** sütununda **Site, UnifiedGroup** olarak ve PowerShell *ContentType* ayarı da aynı değeri görüntüler. Belgeler için kapsam, **Dosya, E-posta olarak görüntülenen Dosyalar & e-postalarını** içermelidir. Sonra:

- Kapsam **Gruplar & siteleri** içerdiğinde, etiketi bir siteye uygulayarak bu site için varsayılan paylaşım bağlantı türünü ayarlayabilirsiniz. Siteye duyarlılık etiketi uygulama hakkında bilgi için bkz. [Kapsayıcılara duyarlılık etiketleri uygulama](sensitivity-labels-teams-groups-sites.md#how-to-apply-sensitivity-labels-to-containers).

- Duyarlılık etiketinin kapsamı **Dosyalar & e-postalar** içerdiğinde, etiketi belgelere uygulayabilirsiniz ve bu da bu belge için varsayılan paylaşım bağlantı türünü ayarlar. Etiket [el ile](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) veya [otomatik olarak](apply-sensitivity-label-automatically.md) uygulanabilir.

> [!TIP]
> Etiketin, etiket [ilkesi ayarı](sensitivity-labels.md#what-label-policies-can-do) olarak yeni siteler veya yeni belgeler için uygulanacak varsayılan duyarlılık etiketi olduğunu da belirtebilirsiniz.
