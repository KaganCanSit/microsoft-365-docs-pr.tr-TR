---
title: İş için Microsoft Defender'da güvenlik ayarlarınızı yapılandırma
description: İş için Microsoft Defender'da güvenlik ilkelerinizi yapılandırma
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/14/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 3d1c024858e81031c5ae985857211723db7b10ac
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2022
ms.locfileid: "63015332"
---
# <a name="configure-your-security-policies-in-microsoft-defender-for-business-preview"></a>İş için Microsoft Defender'da (önizleme) güvenlik ilkelerinizi yapılandırma

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](mdb-tutorials.md#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

Kuruluş cihazlarını İş için Microsoft Defender'a (önizleme) katıldıktan sonra, bir sonraki adımınız güvenlik ilkelerinizi görüntülemek ve gerekirse düzenlemektir. İş için Defender (önizleme) içinde, güvenlik ayarları ilkeler aracılığıyla cihazlara uygulanır. Bu ilkeler cihaz [gruplarına uygulanır](mdb-create-edit-device-groups.md#what-is-a-device-group). 

Defender for Business (önizleme) içinde yapılandırabilirsiniz diğer ayarlar da vardır. Bu ayarlar arasında saat dilimi, önizleme özelliklerini alma ve daha fazlası yer alır.

## <a name="what-to-do"></a>Ne yapmalı?

1. [İş için Defender'daki varsayılan güvenlik ilkelerine hızlı bir genel bakış elde](#default-policies-in-defender-for-business)

2. [Güvenlik ilkelerinizi ve cihazlarınızı yönetecek yeri seçin](#choose-where-to-manage-security-policies-and-devices).

3. [Güvenlik ilkelerinizi görüntüleme](#view-your-security-policies).

4. [Web portalında diğer ayarları Microsoft 365 Defender düzenleme](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal) 

5. [Sonraki adımlarınıza devam edin](#next-steps).

## <a name="default-policies-in-defender-for-business"></a>İş için Defender'da varsayılan ilkeler

İş için Defender (önizleme), önerilen ayarları kullanan varsayılan ilkeler içerir. Bu ilkeler şunlardır:

- [Yeni nesil koruma ayarlarının nasıl](mdb-next-gen-configuration-settings.md) yapılandır Microsoft Defender Virüsten Koruma diğer tehdit koruması özelliklerinin yapılandırıldığından emin olun ve 
- [Hangi ağ](mdb-firewall.md) trafiğinin istemci cihazlarında ve bu ağ ağlarından akışa izin verdiğini belirleyen Windows ayarları.

İlk kurulum işleminiz sırasında varsayılan Windows cihazlarınıza uygulayabilirsiniz. Ayrıca yeni ilkeler tanımlayabilir ve var olan ilkeleri iş ihtiyaçlarına uygun olarak düzenleyebilirsiniz. 

## <a name="choose-where-to-manage-security-policies-and-devices"></a>Güvenlik ilkelerini ve cihazlarını yönetecek yeri seçme

İş için Defender (önizleme), kurulumu [ve yapılandırma işlemini kolaylaştıran](mdb-simplified-configuration.md) basitleştirilmiş bir yapılandırma işlemi içerir. Basitleştirilmiş yapılandırma işlemini seçiyorsanız, güvenlik ilkelerinizi web portalında () Microsoft 365 Defender yönetebilirsiniz[https://security.microsoft.com/](https://security.microsoft.com/). Ancak, bu seçenekle sınırlı değildirsiniz. Güvenlik ilkelerinizi ve cihazlarınızı yönetmek için Microsoft Endpoint Manager (Microsoft Intune içerir) veya Microsoft'a yönelik olmayan bir üretkenlik çözümü kullanıyorsanız, geçerli çözümlerinizi kullanmaya devamabilirsiniz.

Aşağıdaki tablo, güvenlik ilkelerinizi ve cihazlarınızı yönetecek yeri seçmenize yardımcı olabilir. <br/><br/>

| Seçenek | Açıklama |
|:---|:---|
| **Microsoft 365 Defender portalında varsayılan güvenlik ilkelerini kullanma** (*önerilen*) | İş için Defender (önizleme), kurumsal olarak meşgul olan küçük veya orta ölçekli işletmeler için tasarlanmıştır. Defender for Business'daki varsayılan güvenlik ilkeleri, kuruluş cihazlarınızı ilk günden korumak için tasarlanmıştır.<br/><br/>Güvenlik ilkelerinizi görüntülemek Microsoft 365 Defender yönetmek için Güvenlik Portalı'Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/) ) kullanabilirsiniz.<br/><br/>Daha fazla bilgi edinmek için bkz [. Cihaz ilkelerini görüntüleme veya düzenleme](mdb-view-edit-policies.md). |
| **Microsoft Endpoint Manager'i kullanma** | Kuruluş, güvenlik Microsoft Endpoint Manager Microsoft Endpoint Manager kullanıyorsa, güvenlik ilkelerini kullanmaya devam Endpoint Manager bazı cihazlara veya tüm cihazlara güvenlik ilkeleri uygulayabilirsiniz. Daha fazla bilgi edinmek için bkz[. Cihaz güvenliğiyle cihaz güvenliğini uç nokta güvenlik ilkeleriyle yönetme Microsoft Intune](/mem/intune/protect/endpoint-security-policy). <br/><br/>İş için [Defender'da basitleştirilmiş yapılandırma sürecine geçmeyi düşünün](mdb-simplified-configuration.md). Geçiş olursa, İş için Defender'da basitleştirilmiş yapılandırma sürecine devam etmeden Microsoft Endpoint Manager içinde var olan tüm güvenlik ilkelerini silmeniz istenir. İlkelerinizi tek bir Microsoft Endpoint Manager, daha sonra ilke çakışmalarını önlemeye yardımcı olur. |

> [!TIP]
> İş için Microsoft Defender önizleme programına kaydolmak için şu sayfayı ziyaret edin [https://aka.ms/MDB-Preview](https://aka.ms/MDB-Preview): Daha fazla bilgi edinmek için bkz [. İş için Microsoft Defender'ı (önizleme) öğrenme](get-defender-business.md).

## <a name="view-your-security-policies"></a>Güvenlik ilkelerinizi görüntüleme

Güvenlik ilkeleri listenizi görüntülemek için, aşağıdaki tabloda yer alan yordamlardan birini kullanın:
<br/><br/>

| Portal | Yordam |
|:---|:---|
| Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Oturum Microsoft 365 Defender ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın. <br/><br/>2. Gezinti bölmesinde Cihaz **yapılandırması'ni seçin**. İlkeler, işletim sistemine ve ilke türüne göre düzenlenmiştir.<br/><br/>3. İşletim sistemi sekmesini seçin (örneğin, **Windows seçin**).<br/><br/>4. İlke listenizi görüntülemek için **bir** kategoriyi (Yeni nesil koruması veya Güvenlik Duvarı **gibi) genişletin**.<br/><br/>5. İlke hakkında daha fazla ayrıntı görüntülemek için bir ilke seçin. Değişiklik yapmak veya ilke ayarları hakkında daha fazla bilgi edinmek için aşağıdaki makalelere bakın: <br/>- [Cihaz ilkelerini görüntüleme veya düzenleme](mdb-view-edit-policies.md)<br/>- [Yeni nesil yapılandırma ayarlarını anlama](mdb-next-gen-configuration-settings.md)<br/>- [Güvenlik duvarı ayarları](mdb-firewall.md)  |
| Microsoft Endpoint Manager merkezi ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Gidin ve [https://endpoint.microsoft.com](https://endpoint.microsoft.com) oturum açma. Artık Yönetim Merkezi'Microsoft Endpoint Manager siniz.<br/><br/>2. Uç nokta **güvenliği'ne seçin**.<br/><br/>3. Bu kategorideki ilkeleri görüntülemek için Virüsten **Koruma****, Güvenlik** **Duvarı, Uç** nokta algılama ve yanıt veya **Saldırı** yüzeyini azaltma gibi bir kategori seçin. <br/><br/>Web'de güvenlik ayarlarınızı yönetmeye yardımcı Microsoft Endpoint Manager için, Güvenlik [açıkken uç nokta güvenliğini yönet Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="view-and-edit-other-settings-in-the-microsoft-365-defender-portal"></a>Web portalında diğer ayarları Microsoft 365 Defender düzenleme

Cihazlara uygulanan güvenlik ilkelerine ek olarak, İş için Defender'da (önizleme) görüntüleyemez ve düzenleyemezsiniz başka ayarlar da vardır. Örneğin, kullanmak istediğiniz saat dilimini belirtirsiniz ve cihazları (veya çıkar) cihazları kullanabilirsiniz. 

> [!NOTE]
> Kiracınız için bu makalede listelenen ayarlardan daha fazla ayar bulabilirsiniz. İş için Defender'da (önizleme) gözden geçirmeniz gereken ayarları vurgularız.

### <a name="settings-to-review-for-defender-for-business"></a>Ayarlar Defender for Business için gözden geçirmek zorunda değil

Aşağıdaki tabloda, İş için Defender'da (önizleme) görüntüleme (ve gerekirse düzenleme) ayarları açık almaktadır.

<br/><br/>

| Kategori | Ayar | Açıklama |
|:---|:---|:---|
| **Güvenlik merkezi** | **Saat dilimi** | Olaylarda görüntülenen tarih ve saatlerde, algılanan tehditlerde ve düzeltmelerde kullanılacak saat dilimini & seçin. UTC'i veya yerel saat diliminizi *kullanabilirsiniz (önerilir*).  |
| **Microsoft 365 Defender** | **Hesap** | Verilerinizin depolandığı yer, kiracı kimliğiniz ve kuruluş (kuruluş) kimliğiniz gibi ayrıntıları görüntüebilirsiniz. |
| **Microsoft 365 Defender**  | **Önizleme özellikleri**  | Yaklaşan özellikleri ve yeni özellikleri denemek için önizleme özelliklerini açma. Yeni özellikleri öniz alan ve geri bildirim sağlayan ilkler arasında yer görebilirsiniz. |
| **Uç noktalar**  | **E-posta bildirimleri** | E-posta bildirimi kurallarınızı ayarlayın veya düzenleyin. Güvenlik açıkları algılandığında veya bir uyarı oluşturulduğunda, e-posta bildirim kurallarında belirtilen alıcılar bir e-posta alır. [E-posta bildirimleri hakkında daha fazla bilgi alın](mdb-email-notifications.md). |
| **Uç noktalar**   | **Cihaz yönetimi** >  **Ekleme** | İndirilebilir bir betik kullanarak cihazları Defender for Business'a ekleme. Daha fazla bilgi edinmek için bkz [. Cihazları İş için Microsoft Defender'a (önizleme) ekleme](mdb-onboard-devices.md).   |  
| **Uç noktalar**  |  **Cihaz yönetimi** >  **Offboarding** | Defender For Business (önizleme) özelliğinden çıkarma (kaldırma) cihazlar. Bir cihazla çıkarsanız artık verileri İş için Defender'a (önizleme) göndermez, ancak çıkardan önce alınan veriler korunur. Daha fazla bilgi için bkz [. Cihaz çıkarma](mdb-onboard-devices.md#offboarding-a-device).  |

### <a name="access-your-settings-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında ayarlarınıza erişme

1. Microsoft 365 Defender portalına () gidin[https://security.microsoft.com/](https://security.microsoft.com/) ve oturum açın.

2. Önce **Ayarlar** sonra da bir kategori seçin (Güvenlik **merkezi**, Güvenlik Merkezi, **Microsoft 365 Defender** **Uç Noktalar gibi**).

3. Ayarlar listesinde, görüntülemek veya düzenlemek için bir öğe seçin.


## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki görevlerden bir veya birden fazlası ile devam edin:

- [İş için Microsoft Defender'ı (önizleme) kullanmaya başlama](mdb-get-started.md)

- [İş için Microsoft Defender'da cihazları yönetme (önizleme)](mdb-manage-devices.md)

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme (önizleme)](mdb-view-manage-incidents.md)

- [İş için Microsoft Defender'da ilkeleri görüntüleme veya düzenleme (önizleme)](mdb-view-edit-policies.md)

