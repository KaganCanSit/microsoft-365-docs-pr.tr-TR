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
description: Yeni ürün ve özellikler güncelleştirmeleri için sürüm seçeneğini ayarlama hakkında bilgi Microsoft 365 yönetim merkezi.
ms.openlocfilehash: 6e3cf1987d6b3c22ed1414bd8e352da7acf49e60
ms.sourcegitcommit: e246725b0935067aad886530d5178972c0f895d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2021
ms.locfileid: "63012861"
---
# <a name="set-up-the-standard-or-targeted-release-options"></a>Standart veya Hedefli sürüm seçeneklerini ayarlama

> [!IMPORTANT]
> Bu Microsoft 365 açıklanan en son güncelleştirmeler Microsoft 365, SharePoint Online ve Exchange Online. Bu sürüm seçenekleri, değişiklikleri en iyi şekilde Yayınla seçeneğiyle Microsoft 365, ancak her zaman ve her güncelleştirmede garanti edilemez. Bu hizmetler diğer Microsoft 365 Uygulamaları, Skype Kurumsal Microsoft Teams hizmetler için geçerli değildir. Bu konudaki sürüm seçenekleri hakkında bilgi Microsoft 365 Uygulamaları bkz. Yayın [için güncelleştirme kanallarına Microsoft 365 Uygulamaları](/deployoffice/overview-update-channels).

Yeni Microsoft 365, birkaç yılda bir yüksek maliyetli güncelleştirmeleri yapmak yerine, kullanılabilir oldukları anda yeni ürün güncelleştirmeleri ve özellikleri alırsınız. Kuruluşunuzun bu güncelleştirmeleri nasıl alacağını yönetebilirsiniz. Örneğin, kuruluşun güncelleştirmeleri önceden alması için erken sürüme kaydolabilirsiniz. Yalnızca belirli kişilerin güncelleştirmeleri almasını sağlayabilirsiniz. Bunun yerine varsayılan zamanlamada kalarak güncelleştirmeleri daha sonra alabilirsiniz. Bu makalede, farklı sürüm seçenekleri ve bunları organizasyonunız için nasıl kullanabileceğiniz açıklanmıştır.

## <a name="how-it-works---release-validation"></a>Nasıl çalışır? - Sürüm doğrulaması

Tüm yeni sürümler önce özellik ekibi tarafından, ardından tüm Microsoft tarafından, Microsoft 365 ve tüm Microsoft tarafından test edilir ve doğrulanır. Şirket içinde yapılan test ve doğrulamadan sonraki adım, **Hedefli sürümün** (önceki adıyla İlk sürüm) katılan müşterilere yayımlanmasıdır. Microsoft, her sürüm halkasında geri bildirim toplar ve başlıca kullanım ölçümlerini izleyerek sürüm kalitesini tam olarak doğrular. Bu aşamalı doğrulama dizisi, dünya çapında yayımlanan sürümün olabildiğince güçlü olduğundan emin olmak için uygulanır. Sürümler aşağıdaki şekilde resmedilmiştir. 
  
![Geçerlilik halkaları için Microsoft 365.](../../media/73611ed3-2d8c-4e7b-8074-9f03b239f9ed.png)
  
Önemli güncelleştirmeler için müşterilere yol haritasında Microsoft 365[.](https://products.office.com/business/office-365-roadmap) Bir güncelleştirmenin ne kadar yakınsa, bu güncelleştirme sizin ileti merkeziniz [Microsoft 365 iletmektedir](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/MessageCenter).

> [!NOTE]
> İleti merkezinize Microsoft 365 yönetim merkezi aracılığıyla erişebilirsiniz.[](/office365/admin/admin-overview/about-the-admin-center) Microsoft 365 ev planı kullanıcılarının yönetim merkezi olmaz.


## <a name="standard-release"></a>Standart sürüm

Bu, sizin ve kullanıcılarınızın tüm müşterilere geniş bir şekilde yayın geldiğinde en son güncelleştirmeleri almaları için varsayılan seçenektir.
  
Kullanıcıların çoğunun Standart sürümde bırakılacağı ve yeni özellikleri  değerlendirmek ve ekipleri iş kullanıcılarını ve yöneticilere destek  olacak şekilde hazırlamak için Hedeflenen sürümde yer alan IT Pro'ları ve güçlü kullanıcıları bırakmak iyi bir uygulamadır. 
  
> [!NOTE]
> Hedeflenen sürümden standart sürüme geçtiğinizde kullanıcılarınız, henüz standart sürümde olmayan özelliklere erişimi kaybedebilir. 
  
## <a name="targeted-release"></a>Hedefli sürüm

Bu seçenekte, siz ve kullanıcılarınız en son güncelleştirmeleri önceden görebilir ve erken geri bildirim sağlayarak ürünün şekillenmesine yardımcı olabilirsiniz. Ayrı ayrı kişilerin veya tüm kuruluşun güncelleştirmeleri erkenden alıp almayacağını seçebilirsiniz.
  
> [!IMPORTANT]
> - Kullanıcıların olumsuz yönde etkilenmemesi için büyük ve karmaşık güncelleştirmelerin yayımlanması daha uzun sürebilir. Sürümler için kesin bir zaman çizelgesi yoktur.
> - Hedefli sürüm, şu anda Office 365 GCC High ve DoD planına Office 365 GCC müşteriler için mevcut değildir.
  
### <a name="targeted-release-for-entire-organization"></a>Tüm kuruluş için hedeflenen sürüm

Yönetim [merkezinde sürüm seçeneğini bu seçenek için](#set-up-the-release-option-in-the-admin-center) ayarsanız tüm kullanıcılarınız Hedefli sürüm deneyimini elde edin. 300'den fazla kullanıcısı olan kuruluşlara bu seçenek için test aboneliği kullanmaları önerilir. Test aboneliği hakkında bilgi için lütfen Microsoft'taki ilgili kişiye ulaşın. 
  
### <a name="targeted-release-for-selected-users"></a>Seçili kullanıcılar için Hedefli sürüm

Yönetim merkezinde [sürüm seçeneğini](#set-up-the-release-option-in-the-admin-center) bu seçenek için ayarladığınız durumda, özelliklere ve işlevlere erken erişim sağlamak için belirli kullanıcıları (çoğunlukla güçlü kullanıcılar) tanımlayabilirsiniz. 
  
## <a name="benefits-of-targeted-release"></a>Hedefli sürüm avantajları

Hedefli sürüm yöneticilerin, değişiklik yöneticilerinin veya güncelleştirmelerden sorumlu Microsoft 365 onlara izin vererek yaklaşan değişikliklere hazırlanmalarına olanak sağlar:
  
- Yeni güncelleştirmeleri, kuruluşunuzdaki tüm kullanıcılara sunulmadan önce test edip doğrulama.
    
- Güncelleştirmeler dünya çapında yayımlanmadan önce kullanıcı bildirimi ve belgelerini hazırlama.
    
- Şirket içi yardım masasını gelecek değişiklikler için hazırlama.
    
- Uyumluluk ve güvenlik incelemeleri yapma.
    
- Güncelleştirmelerin son kullanıcılara yayımlanmasını denetlemek için mümkün olan durumlarda özellik denetimlerini kullanma.
    
## <a name="set-up-the-release-option-in-the-admin-center"></a>Yönetim merkezinde sürüm seçeneğini ayarlama

Aşağıdaki adımları takip edinerek, Microsoft 365 güncelleştirmeleri nasıl aldığını değiştirebilirsiniz. Kabul etmek için bu iletişim Microsoft 365 genel yönetici olmak gerekir.
  
> [!IMPORTANT]
> Aşağıdaki değişikliklerin etkili bir şekilde son 24 saate kadar Microsoft 365. Etkinleştirdikten sonra hedefli sürümden ayrılırsanız kullanıcılarınız, henüz zamanlanan sürümlerde bulunmayan özelliklere erişimi kaybedebilir. 
  
1. Yönetim merkezinde Grup Ayarı Ayarlar  > **na** gidin ve Kuruluş profili <a href="https://go.microsoft.com/fwlink/p/?linkid=2067339" target="_blank">**sekmesinin Altında**</a> Sürüm tercihleri'ni **seçin**.

5. Hedefli sürümü devre dışı bırakmak için Standart **sürüm'e ve** sonra Değişiklikleri **kaydet'e tıklayın**. 
    
6. Hedefli sürümü kuruluşta tüm kullanıcılar için etkinleştirmek için Herkes için hedeflenen **sürüm'e** ve ardından Değişiklikleri **kaydet'e tıklayın**. 
    
7. Kuruluşta bazı kişiler için hedefli sürümü etkinleştirmek için Seçili kullanıcılar için hedeflenen **sürüm'e ve sonra Değişiklikleri** **kaydet'e tıklayın**. 
    
8. Kullanıcıları **tek tek** eklemek için Kullanıcıları seç'i veya kullanıcıları **Upload toplu olarak** eklemek için Kullanıcıları seç'i seçin.
    
9. Kullanıcı eklemeyi bitirerek Değişiklikleri **kaydet'i seçin**.
  
## <a name="next-steps"></a>Sonraki adımlar

Yaklaşan güncelleştirmeler [ve](/office365/admin/manage/message-center) sürümler [hakkında bildirim Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/MessageCenter) için İleti merkezinize iletilerin Microsoft 365 keşfedin.

## <a name="related-content"></a>İlgili içerik

[Office Insider Programına katılma](https://insider.office.com/join/windows) (makale)
