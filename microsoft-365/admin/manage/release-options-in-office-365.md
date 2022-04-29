---
title: Standart veya Hedefli sürüm seçeneklerini ayarlama
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 3b3adfa4-1777-4ff0-b606-fb8732101f47
description: Microsoft 365 yönetim merkezi yeni ürün ve özellik güncelleştirmeleri için sürüm seçeneğini ayarlamayı öğrenin.
ms.openlocfilehash: 176558448f31fadea0b0cf865bca5d1156e3eefe
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65129430"
---
# <a name="set-up-the-standard-or-targeted-release-options"></a>Standart veya Hedefli sürüm seçeneklerini ayarlama

> [!IMPORTANT]
> Bu makalede açıklanan Microsoft 365 güncelleştirmeleri Microsoft 365, SharePoint Online ve Exchange Online için geçerlidir. Bu sürüm seçenekleri hedeflenir, Microsoft 365 değişiklikleri yayınlamak için en iyi çaba yöntemleridir, ancak her zaman veya tüm güncelleştirmeler için garanti edilemez. Bunlar Microsoft 365 Uygulamaları, Skype Kurumsal, Microsoft Teams ve ilgili hizmetler için geçerli değildir. Microsoft 365 Uygulamaları sürüm seçenekleri hakkında bilgi için bkz. [Microsoft 365 Uygulamaları için güncelleştirme kanallarına genel bakış](/deployoffice/overview-update-channels).

Microsoft 365 sayesinde, birkaç yılda bir yüksek maliyetli güncelleştirmeler yapmak yerine yeni ürün güncelleştirmelerini ve özellikleri kullanıma sunuldukları anda alırsınız. Kuruluşunuzun bu güncelleştirmeleri nasıl alacağını yönetebilirsiniz. Örneğin, kuruluşun güncelleştirmeleri önceden alması için erken sürüme kaydolabilirsiniz. Yalnızca belirli kişilerin güncelleştirmeleri almasını sağlayabilirsiniz. Bunun yerine varsayılan zamanlamada kalarak güncelleştirmeleri daha sonra alabilirsiniz. Bu makalede farklı sürüm seçenekleri ve bunları kuruluşunuz için nasıl kullanabileceğiniz açıklanmaktadır.

## <a name="how-it-works---release-validation"></a>Nasıl çalışır? - Sürüm doğrulaması

Yeni sürümler önce özellik ekibi, ardından tüm Microsoft 365 özellik ekibi ve ardından tüm Microsoft tarafından test edilir ve doğrulanır. Şirket içinde yapılan test ve doğrulamadan sonraki adım, **Hedefli sürümün** (önceki adıyla İlk sürüm) katılan müşterilere yayımlanmasıdır. Microsoft, her sürüm halkasında geri bildirim toplar ve başlıca kullanım ölçümlerini izleyerek sürüm kalitesini tam olarak doğrular. Bu aşamalı doğrulama dizisi, dünya çapında yayımlanan sürümün olabildiğince güçlü olduğundan emin olmak için uygulanır. Sürümler aşağıdaki şekilde resmedilmiştir. 
  
![Microsoft 365 için sürüm doğrulama halkaları.](../../media/73611ed3-2d8c-4e7b-8074-9f03b239f9ed.png)
  
Önemli güncelleştirmeler için, müşteriler başlangıçta [Microsoft 365 Yol Haritası](https://products.office.com/business/office-365-roadmap) tarafından bildirilir. Bir güncelleştirme kullanıma sunulmaya yaklaştıkça[, Microsoft 365 İleti merkeziniz](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/MessageCenter) üzerinden iletilir.

> [!NOTE]
> [yönetim](/office365/admin/admin-overview/admin-center-overview) merkezi üzerinden İleti merkezinize erişmek için bir Microsoft 365 veya Azure AD hesabınız olmalıdır. Microsoft 365 ev planı kullanıcılarının yönetim merkezi yoktur.

## <a name="standard-release"></a>Standart sürüm

Bu, sizin ve kullanıcılarınızın en son güncelleştirmeleri tüm müşterilere geniş bir şekilde yayımlandıklarında aldığı varsayılan seçenektir.
  
İyi bir uygulama, yeni özellikleri değerlendirmek ve ekipleri iş kullanıcılarını ve yöneticilerini desteklemek üzere hazırlamak için **Standart sürümdeki** kullanıcıların çoğunluğunu ve BT Uzmanlarını ve ileri düzey kullanıcıları **Hedefli sürümde** bırakmaktır. 
  
> [!NOTE]
> Hedeflenen sürümden standart sürüme geçtiğinizde kullanıcılarınız, henüz standart sürümde olmayan özelliklere erişimi kaybedebilir. 
  
## <a name="targeted-release"></a>Hedefli sürüm

Bu seçenekte, siz ve kullanıcılarınız en son güncelleştirmeleri önceden görebilir ve erken geri bildirim sağlayarak ürünün şekillenmesine yardımcı olabilirsiniz. Ayrı ayrı kişilerin veya tüm kuruluşun güncelleştirmeleri erkenden alıp almayacağını seçebilirsiniz.
  
> [!IMPORTANT]
> - Kullanıcıların olumsuz yönde etkilenmemesi için büyük ve karmaşık güncelleştirmelerin yayımlanması daha uzun sürebilir. Sürümler için kesin bir zaman çizelgesi yoktur.
> - Hedefli sürüm şu anda Office 365 GCC planına veya Office 365 GCC High ve DoD planına sahip müşteriler tarafından kullanılamaz.
  
### <a name="targeted-release-for-entire-organization"></a>Tüm kuruluş için hedeflenen sürüm

Bu [seçeneğin yönetim merkezinde yayın seçeneğini ayarlarsanız](#set-up-the-release-option-in-the-admin-center) , tüm kullanıcılarınız Hedeflenen sürüm deneyimine sahip olur. 300'den fazla kullanıcısı olan kuruluşlara bu seçenek için test aboneliği kullanmaları önerilir. Test aboneliği hakkında bilgi için lütfen Microsoft'taki ilgili kişiye ulaşın. 
  
### <a name="targeted-release-for-selected-users"></a>Seçili kullanıcılar için Hedefli sürüm

Bu [seçeneğin yönetim merkezinde sürüm seçeneğini ayarlarsanız](#set-up-the-release-option-in-the-admin-center) , özelliklere ve işlevlere erken erişim elde etmek için belirli kullanıcıları (genellikle güçlü kullanıcılar) tanımlayabilirsiniz.

> [!IMPORTANT]
> Bazı özellikler yalnızca kuruluş bazında kullanıma sunulur. Bu, kuruluşun tamamının özelliğe aynı anda erişim alacağı anlamına gelir. Bu gibi özellikler için, hedeflenen yayın programındaki seçili kullanıcıların özelliği erken alması mümkün değildir. Bu, hedeflenen sürümde seçili kullanıcıları yapılandırdıysanız kuruluşunuzun bu özellikleri erken alamayacağı anlamına gelir. Hedeflenen sürümdeki tüm özellikleri gördüğünüzden emin olmak için tüm kuruluş için hedefli sürümü yapılandırmanız veya bir test kuruluşu ayarlamanız gerekir.
  
## <a name="benefits-of-targeted-release"></a>Hedefli sürüm avantajları

Hedeflenen sürüm, yöneticilerin, değişiklik yöneticilerinin veya güncelleştirmelerin Microsoft 365 sorumlu olan herkesin aşağıdakilere izin vererek yaklaşan değişikliklere hazırlanmalarına olanak tanır:
  
- Yeni güncelleştirmeleri, kuruluşunuzdaki tüm kullanıcılara sunulmadan önce test edip doğrulama.
    
- Güncelleştirmeler dünya çapında yayımlanmadan önce kullanıcı bildirimi ve belgelerini hazırlama.
    
- Şirket içi yardım masasını gelecek değişiklikler için hazırlama.
    
- Uyumluluk ve güvenlik incelemeleri yapma.
    
- Güncelleştirmelerin son kullanıcılara yayımlanmasını denetlemek için mümkün olan durumlarda özellik denetimlerini kullanma.
    
## <a name="set-up-the-release-option-in-the-admin-center"></a>Yönetim merkezinde sürüm seçeneğini ayarlama

Bu adımları izleyerek kuruluşunuzun Microsoft 365 güncelleştirmeleri alma şeklini değiştirebilirsiniz. Kabul etmek için Microsoft 365'da genel yönetici olmanız gerekir.
  
> [!IMPORTANT]
> Aşağıdaki değişikliklerin Microsoft 365 etkili olması 24 saat kadar sürebilir. Etkinleştirdikten sonra hedefli sürümden ayrılırsanız kullanıcılarınız, henüz zamanlanan sürümlerde bulunmayan özelliklere erişimi kaybedebilir. 
  
1. Yönetim merkezinde **Ayarlar** >  **Org Ayarı'na** gidin ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2067339" target="_blank">**Kuruluş profili** sekmesinin</a> altında **Yayın tercihleri'ni** seçin.

5. Hedeflenen sürümü devre dışı bırakmak için **Standart sürüm'e** ve ardından **Değişiklikleri kaydet'e** tıklayın. 
    
6. Kuruluşunuzdaki tüm kullanıcılar için hedefli sürümü etkinleştirmek için **Herkes için hedeflenen sürüm'e** tıklayın ve ardından **Değişiklikleri kaydet'e** tıklayın. 
    
7. Kuruluşunuzdaki bazı kişiler için hedefli sürümü etkinleştirmek için **Seçili kullanıcılar için hedefli sürüm'e** ve ardından **Değişiklikleri kaydet'e** tıklayın. 
    
8. Kullanıcıları tek tek eklemek için **Kullanıcıları seçin'i** seçin veya kullanıcıları toplu olarak eklemek için **Upload**.
    
9. Kullanıcı eklemeyi bitirdiğinizde **Değişiklikleri kaydet'i** seçin.
  
## <a name="next-steps"></a>Sonraki adımlar

Yaklaşan Microsoft 365 güncelleştirmeleri ve yayınları hakkında bildirim almak için [Microsoft 365 İleti merkezinizdeki](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/MessageCenter) [iletilerin nasıl yönetileceğini](/office365/admin/manage/message-center) keşfedin.

## <a name="related-content"></a>İlgili içerik

[Office Insider Programı'na katılma](https://insider.office.com/join/windows) (makale)
