---
title: Multi-Geo Microsoft 365 planlama
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: Multi-Geo Microsoft 365, multi-geo'nın nasıl çalıştığını ve veri depolama için kullanılabilen coğrafi konumları öğrenin.
ms.openlocfilehash: 5c079d5cf5f093be2c942a53468494044913fbd7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984326"
---
# <a name="plan-for-microsoft-365-multi-geo"></a>Multi-Geo Microsoft 365 planlama

Bu kılavuz, Microsoft 365 kiracılarını hazırlayan çok uluslu şirketlerin (MCS) yöneticilerine, veri ikamet gereksinimlerini karşılamak üzere şirketin iletişim durumuna uygun olarak ek coğrafyalara genişletilecek şekilde tasarlanmıştır.

Çok coğrafi yapılandırmada, kiracınız Microsoft 365 bir merkezi konumdan ve bir veya daha fazla uydu konumdan oluşur. Bu, birden çok coğrafi konuma yayılan tek bir kiracıdır. Coğrafi konumlar da dahil olmak üzere kiracı bilgileri ana Azure Active Directory (Azure AD) içindedir.

Yapılandırmanın temel kavramlarını anlamanıza yardımcı olacak bazı önemli multi-geo terimleri:

-   **Kiracı** – Normalde bir veya daha fazla Microsoft 365 etki alanı (örneğin, ) olan kuruluş temsilihttps://contoso.sharepoint.com). 

-   **Coğrafi konumlar** – Verileri bir kiracıda barındırmak için kullanılabilen Microsoft 365.

-   **Uydu konumları** – Verileri bu kiracıda barındırmak üzere yapılandırmış olduğunuz ek coğrafi Microsoft 365 vardır. Çok coğrafi kiracılar birden çok coğrafi konuma (örneğin, Kuzey Amerika ve Avrupa) yayılanıdır.

-   **Tercih Edilen Veri Konumu (PDL)** – Tek bir kullanıcının veri kaynağı ve Exchange OneDrive konum. Bu, yönetici tarafından kiracı için yapılandırılmış olan coğrafi konumlardan herhangi biri olarak ayarlanabilirsiniz. PDL'de zaten bir OneDrive sitesi olan bir kullanıcının PDL'sini değiştirirsiniz, OneDrive verileri otomatik olarak yeni coğrafi konuma taşınmaz. Daha [fazla OneDrive için bkz. Bir kitaplık kitaplığını farklı bir coğrafi](move-onedrive-between-geo-locations.md) konuma taşıma. Posta kutuları Exchange, posta kutusu otomatik olarak yeni tercih edilen veri konuma taşınır.

Multi-Geo'ların etkinleştirilmesi için dört temel adım gerekir:

1.  Multi-Geo Özelliklerini bu hizmet _planına eklemek için hesap Microsoft 365_ üzerinde çalışabilirsiniz.

2.  İstediğiniz uydu konumlarını seçin ve bunları kiracınıza ekleyin.

3.  Kullanıcılarınızı tercih edilen veri konumunu istenen uydu konumu olarak ayarlayın. Kullanıcıya OneDrive posta Exchange posta kutusu sağlandı ise, PDL'lerine sağlandı.

4.  Kullanıcılarınızı merkezi konumdan OneDrive olan veri konumlarına ve gerektiğinde tercih edilen veri konumlarına geçirme. (Exchange PDL'lerini ayarsız olarak posta kutuları otomatik olarak geçirilir.)

Bu [adımların Microsoft 365 için bkz. Multi-Geo'da](multi-geo-tenant-configuration.md) Yapılandırma.

> [!IMPORTANT]
> Multi-Geo Microsoft 365 performans iyileştirme için tasarlanmasa da, verilerin ikamet gereksinimlerini karşılamak için tasarlanmamaktadır. E-posta için performans iyileştirme Microsoft 365 için bkz. E-posta için ağ [Microsoft 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) performans ayarı veya destek grubunuzla iletişime geçin.

Aşağıdaki konumlardan herhangi birini uydu konumları olarak yapılandırabilirsiniz ve bu konumlarda OneDrive SharePoint ve posta Exchange kullanabilirsiniz. Multi-geo'ya uygun olarak, kiracınıza eklemek istediğiniz konumların listesini Microsoft 365 kullanın. Bir veya iki uydu konumuyla başlamayı ve ardından gerekirse aşamalı olarak daha fazla coğrafi konuma genişletmenizi öneririz.

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

Multi-geo'yu yapılandırırken, kaynak yapısına ilerlerken şirket içi altyapınızı birleştirme Microsoft 365. Örneğin, Singapur ve Malezya'da şirket içi grup varsa, bunları APC uydu konumu olarak birleştirebilirsiniz ve bu şekilde veri yerleşim gereksinimleri sağlanır.

## <a name="best-practices"></a>En iyi uygulamalar

Bazı ilk testler yapmak için Microsoft 365 bir test kullanıcısı oluşturmanızı öneririz. Üretim kullanıcılarını Microsoft 365 Multi-Geo'ya eklemeye devam başlamadan önce bu kullanıcıyla bazı test ve doğrulama adımlarını tamamlaacağız.

Test kullanıcısına test etme tamamlandıktan sonra, yeni coğrafi konumda test etmek üzere ilk kullanan ve en iyi OneDrive olmak üzere bir pilot grubu (belki de IT departmanından) OneDrive Exchange seçin. Bu ilk grup için, henüz 2. grubu olan OneDrive. Bu ilk grupta beşten fazla kişi önerilmez ve toplu bir geçiş yaklaşımının ardından aşamalı olarak genişletilmez.

Her kullanıcının tercih edilen *bir veri* konumu (PDL) ayarlanmış olması gerekir ve böylelikle Microsoft 365 hangi coğrafi konumda konum sağlanarak OneDrive. Kullanıcının tercih ettiği veri konumu, seçtiğiniz uydu konumlarından veya merkezi konumunuzla eşleşmeli. PDL alanı zorunlu değildir ama tüm kullanıcılar için bir PDL ayarlamayı öneririz. PDL olmayan bir kullanıcının iş yükleri merkezi konumda sağlandı.

Kullanıcılarınızı içeren bir liste oluşturun ve bunların kullanıcı asıl adını (UPN) ve uygun tercih edilen veri konumu için konum kodunu ekleyin. Başlangıç olarak test kullanıcınızı ve ilk pilot grubunızı da dahil etmek. Yapılandırma yordamları için bu listeye ihtiyacınız vardır.

Kullanıcılarınız şirket içi Active Directory sisteminden active directory Azure Active Directory için eşitlenmişse, tercih edilen veri konumunu bir Active Directory özniteliği olarak ayarlamalı ve Azure Active Directory Bağlan. Azure AD PowerShell kullanarak eşitlenmiş kullanıcılar için tercih edilen veri konumunu doğrudan yapılandıramazsanız. Active Directory'de PDL'yi ayarlama ve Eşitleme adımları, eşitlemeyi eşitleme Azure Active Directory Bağlan: Kullanıcı kaynakları için tercih edilen [veri Microsoft 365 yapılandırma](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

Çok coğrafi kiracının yönetimi, çok coğrafi olmayan bir kiracıdan farklı olabilir; bunun için, SharePoint ve OneDrive çok coğrafi olarak farkındadır. Yapılandırmanıza devam etmek [için, çok coğrafi bir](administering-a-multi-geo-environment.md) ortamı yönetmeyi gözden geçirmenizi öneririz.

Çok [coğrafi bir ortamda son kullanıcı deneyimiyle](multi-geo-user-experience.md) ilgili ayrıntılar için, Çok coğrafi bir ortamda kullanıcı deneyimi makalesinde okuyabilirsiniz.

Multi-Geo'da Microsoft 365 için bkz. [Multi-Geo Microsoft 365 yapılandırma](multi-geo-tenant-configuration.md).

Yapılandırmayı tamamlandıktan sonra, [kullanıcılarınızı tercih edilen veri konumlarından OneDrive](move-onedrive-between-geo-locations.md) için gerektiğinde kullanıcılarınızı ve kitaplıklarınızı geçirmeyi unutmayın.

## <a name="related-topics"></a>İlgili konular

[Microsoft 365 Multi-Geo eK bulma yapılandırması](./multi-geo-ediscovery-configuration.md)