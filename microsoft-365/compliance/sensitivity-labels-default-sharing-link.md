---
title: Aynı adres ve sitedeki siteler ve belgeler için varsayılan paylaşım bağlantı türünü yapılandırmak için duyarlılık SharePoint OneDrive
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
description: Aynı adres ve sitedeki siteler ve belgeler için varsayılan paylaşım bağlantı türünü yapılandırmak için duyarlılık SharePoint OneDrive.
ms.openlocfilehash: 122a8846893b97146dc74d3a9d30ccbfe050525b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704722"
---
# <a name="use-sensitivity-labels-to-configure-the-default-sharing-link-type-for-sites-and-documents-in-sharepoint-and-onedrive"></a>Aynı adres ve sitedeki siteler ve belgeler için varsayılan paylaşım bağlantı türünü yapılandırmak için duyarlılık SharePoint OneDrive

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

duyarlılık etiketleri için Microsoft 365 uyumluluk merkezi'te gördüğünüz ayarların ek bir yapılandırması [olarak, SharePoint](sensitivity-labels.md) sitesi veya OneDrive hesabı için ve tek tek belgeler için varsayılan paylaşım bağlantı türü ayarlarını yapılandırmak için bu etiketleri kullanabilirsiniz. Bu ayarlar otomatik olarak seçilir, ancak masaüstü uygulamalarının Paylaş düğmesini seçtiklerinde **kullanıcılar Office** görünmez. Örnek olarak:

![Örnek varsayılan paylaşım bağlantısı iletişim kutusu.](../media/default-sharing-link-example.png)

Varsayılan paylaşım bağlantı türü, kullanıcılar dosya ve klasör paylaştığında otomatik olarak seçilen kapsamı (kim) ve izinleri (görüntüleme veya düzenleme) ayarlar. Kullanıcılar paylaşım bağlantısını göndermeden önce her zaman bu varsayılan ayarları geçersiz kılsa da, sizin seçtiğiniz ayarlar güvenli bir temel sağlar. Normalde, kullanıcılar paylaşmadan önce ayarları değiştirmez.

Site düzeyinde (SharePoint sitesi veya OneDrive hesabı), duyarlılık etiketleri SharePoint yönetim merkezinde bir site için yapılandırılan varsayılan paylaşım bağlantı türünü ayarlamaya yönelik kullanışlı bir alternatif sağlar. Daha fazla bilgi için [bkz. Sitenin varsayılan bağlantı türünü](/sharepoint/change-default-sharing-link) değiştirme SharePoint.

Bu site düzeyinde yapılandırma, belgeleri aynı SharePoint olan tüm sitelere uygun şekilde çalışır. Ancak siteler daha kısıtlayıcı ayarlar gerektiren daha yüksek duyarlılık düzeyine sahip bazı belgeler içeriyorsa, varsayılan paylaşım bağlantı türü için farklı ayarlara sahip bir duyarlılık etiketi yapılandırarak bu etiketi belgelere uygulayabilirsiniz.

Sitenin varsayılan paylaşım bağlantı türü ayarlarına sahip olduğu ve bu sitenin farklı varsayılan bağlantı türü ayarlarına sahip olduğu bu senaryoda, kullanıcı belge için paylaşım seçeneğini tercih ettiyseniz daha kısıtlayıcı kapsam ayarları uygulanır. Örneğin:

- Sitenin varsayılan paylaşım bağlantı türü, kuruluş kapsamındaki herkes için kullanılır. Bu siteden bir belge, belirli kişiler için ayarlanmış varsayılan paylaşım bağlantı türüyle etiketlenmiş. Bir kullanıcı bu belgeyi paylaştığında, seçilen varsayılan paylaşım bağlantı türü belirli kişiler kapsamında olur.

- Sitenin varsayılan paylaşım bağlantı türü, düzenleme izinlerine sahip belirli kişiler kapsamındadır. Bu siteden bir belge, görüntüleme izinlerine sahip olarak kuruluşta herkes için ayarlanmış varsayılan paylaşım bağlantı türüyle etiketlenmiş. Bir kullanıcı bu belgeyi paylaştığında, seçilen varsayılan paylaşım bağlantı türü düzenleme izinlerine sahip belirli kişiler kapsamında olur.

Belgeler için varsayılan bağlantı türünün yapılandırılması, site düzeyi ayarı olmadan da uygun olabilir. Örneğin, SharePoint siteleri aynı türde belgeleri barındırmak için düzenlense de, bu aynı hesaplarda OneDrive durum değildir. Kullanıcılar genellikle kişisel ve iş belgelerinin bir karışımı OneDrive dosyaları kaydetmek için çok çeşitli dosyaları kaydedebilir. Kullanıcının kullanıcı hesabı için tüm belgeler için varsayılan bir bağlantı türü OneDrive pratik olmaz, ancak tek tek belgeler bu ayarlardan yararlanabilir. Örneğin:

- Çok Gizli **olarak etiketlenmiş belgelerde** , paylaşımı kuruluşta herhangi biri yerine belirli kişiler ile kısıtlayan bir varsayılan paylaşım bağlantı türü vardır.
- Genel etiketli **belgelerin** , paylaşımı kuruluşta yer alan kişilerle kısıtlayan bir varsayılan paylaşım bağlantı türü vardır.
- Kişisel etiketli **belgeler** , bağlantıya sahip olan herkesle paylaşıma olanak sağlayan varsayılan bir paylaşım bağlantı türüne sahip olur.

## <a name="prerequisites"></a>Önkoşullar

Sitelere varsayılan paylaşım bağlantı türünü uygulamak için duyarlılık etiketlerinin kapsayıcılar için etkinleştirilmiş olması gerekir. Bu özellik kiracınız için henüz etkinleştirilmediyse bkz. Kapsayıcılar için [duyarlılık etiketlerini etkinleştirme ve etiketleri eşitleme](sensitivity-labels-teams-groups-sites.md#how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels).

Belge ve site belgelerine varsayılan paylaşım bağlantı türünü SharePoint OneDrive, bu hizmetler için duyarlılık etiketlerinin etkinleştirilmesi gerekir. Bu özellik kiracınız için henüz etkinleştirilmemişse bkz. Kiracınız için duyarlılık etiketlerini [SharePoint (OneDrive)](sensitivity-labels-sharepoint-onedrive-files.md#how-to-enable-sensitivity-labels-for-sharepoint-and-onedrive-opt-in).

PowerShell oturumunda, varsayılan paylaşım [bağlantı türüne Office 365 için & Güvenlik ve Uyumluluk Merkezi PowerShell'e](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell) bağlanmanız gerekir.

> [!NOTE]
> Gerekli değildir, ancak önce etiket etiketlerini oluşturmak ve [](create-sensitivity-labels.md)yapılandırmak ve ardından varsayılan paylaşım bağlantı türünü yapılandıran ayarlarla bu Microsoft 365 uyumluluk merkezi'te değişiklik yapmak en kolay yöntemdir.

## <a name="how-to-configure-settings-for-the-default-sharing-link-type"></a>Varsayılan paylaşım bağlantı türü ayarlarını yapılandırma

Varsayılan paylaşım bağlantı türünün yapılandırma ayarları, Güvenlik ve Uyumluluk Merkezi [PowerShell'in](/powershell/exchange/scc-powershell) [Set-Label](/powershell/module/exchange/set-label) ve [New-Label](/powershell/module/exchange/new-labelpolicy) cmdlet'leriyle PowerShell *AdvancedSettings* & kullanır:

- **DefaultSharingScope**: Kullanılabilir değerler:
    - **SpecificPeople**: Sitenin varsayılan paylaşım bağlantısını "Belirli kişiler" bağlantısına ayarlar
    - **Kuruluş**: Sitenin varsayılan paylaşım bağlantısını "kuruluş" bağlantısına veya şirket paylaşılabilir bağlantısına ayarlar
    - **Herkes**: Sitenin varsayılan paylaşım bağlantısını Anonim Erişim veya Herkes bağlantısına ayarlar

- **DefaultShareLinkPermission**: Kullanılabilir değerler:
    - **Görüntüleme**: Sitenin varsayılan bağlantı iznini "görüntüleme" izinlerine ayarlar
    - **Düzenle**: Sitenin varsayılan bağlantı iznini "düzenleme" izinlerine ayarlar

Bu iki ayar ve değer, [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) cmdlet'inden *DefaultSharingScope* ve *DefaultShareLinkPermission* parametrelerinin eşdeğeridir.

Duyarlılık etiketi GUID'nin **8faca7b8-8d20-48a3-8ea2-0f96310a848e** olduğu PowerShell örnekleri:

- Varsayılan paylaşım bağlantı türünü SpecificPeople olarak ayarlamak için:
    
    ````powershell
    Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultSharingScope="SpecificPeople"}
    ````

- Varsayılan paylaşım bağlantısı türü izinlerini Düzenle olarak ayarlamak için:
    
    ````powershell
    Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultShareLinkPermission="Edit"}
    ````

Sitenin varsayılan paylaşım bağlantı türü ayarlarını yapılandırmak için, duyarlılık etiketinin kapsamının [](sensitivity-labels.md#label-scopes) Grup gruplarında **veya** & sitesinde duyarlılık etiketini oluşturmanız Microsoft 365 uyumluluk merkezi. Oluşturulduktan sonra, etiketler sayfasındaki Kapsam sütununda **Site, UnifiedGroup** olarak görüntülenir ve PowerShell *ContentType* ayarı  da aynı değeri görüntüler. Belgeler için kapsam, Dosya, **E-& e-posta** olarak görüntüleyen dosyalar veya **e-postalar içerebilir**. Ardından:

- Kapsam Grupları veya **& olduğunda**, etiketi bir siteye uygulayabilirsiniz; bu etiket o site için varsayılan paylaşım bağlantı türünü ayarlar. Siteye duyarlılık etiketi uygulama hakkında bilgi için bkz. Duyarlılık [etiketlerini kapsayıcılara uygulama](sensitivity-labels-teams-groups-sites.md#how-to-apply-sensitivity-labels-to-containers).

- Duyarlılık etiketinin kapsamı Dosyalar veya e- **&** olduğunda, bu etiketi belgelere uygulayabilirsiniz; böylece bu belge için varsayılan paylaşım bağlantı türü ayarlar. Etiket el ile veya [otomatik olarak](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) [uygulanabilir](apply-sensitivity-label-automatically.md).

> [!TIP]
> Ayrıca, etiket ilkesi ayarı olarak bu etiketin yeni siteler veya yeni belgelere uygulanacak varsayılan duyarlılık etiketi olduğunu [da belirtebilirsiniz](sensitivity-labels.md#what-label-policies-can-do).

### <a name="powershell-tips-for-specifying-the-advanced-settings"></a>Gelişmiş ayarları belirtmek için PowerShell ipuçları

Duyarlılık etiketini adına göre belirtesiniz, ancak etiket adını veya görünen adı belirtme konusunda olası karışıklıkları önlemek için etiket GUID'sini kullanmayı öneririz. GUID'i bulmak ve etiketin kapsamını onaylamak için:

````powershell
Get-Label | Format-Table -Property DisplayName, Name, Guid, ContentType
````

Bu gelişmiş ayarlardan birini duyarlılık etiketinden kaldırmak için aynı AdvancedSettings parametre söz dizimini kullanın, ancak bir null dize değeri belirtin. Örneğin:

````powershell
Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultSharingScope=""}
````

