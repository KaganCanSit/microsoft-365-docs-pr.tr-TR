---
title: İş için Microsoft Defender'da güvenlik ayarlarınızı görüntüleme ve düzenleme
description: İş için Microsoft Defender'da güvenlik ilkelerinizi yapılandırma
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: bccbc7cf33d8be285bac801512de974f0277cf06
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2022
ms.locfileid: "63512468"
---
# <a name="view-and-edit-your-security-policies-and-settings-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'da güvenlik ilkelerinizi ve ayarlarınızı görüntüleme ve düzenleme

> [!IMPORTANT]
> İş için Microsoft Defender 1 Mart 2022 [Microsoft 365 İş Ekstra'den](../../business-premium/index.md) itibaren tüm müşterilere sunulmaktadır. Tek başına bir abonelik olarak İş için Defender önizlemededir ve istekte etmek için buraya kaydolan müşterilere ve IT İş Ortaklarına [aşamalı](https://aka.ms/mdb-preview) olarak tüm müşterilere aşamalı olarak tüm müşterilere aşamalı olarak ve tek başına bir abonelik sunar. Önizleme bir [dizi senaryo içerir ve](mdb-tutorials.md#try-these-preview-scenarios) düzenli olarak özellikler ekleycek.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

## <a name="overview"></a>Genel bakış

Şirketinizin cihazlarını İş için Microsoft Defender'a ekledikten sonra, bir sonraki adımınız güvenlik ilkelerinizi ve ayarlarınızı görüntülemek ve gerekirse düzenlemektir. Güvenlik ilkeleri şunlardır:

- **[Virüsten koruma ve kötü](#view-or-edit-your-next-generation-protection-policies)** amaçlı yazılımdan korumayı belirleyen yeni nesil koruma ilkeleri

- **[Hangi ağ trafiğinin](#view-or-edit-your-firewall-policies-and-custom-rules)** şirket cihazlarına veya şirket cihazlarından akışına izin verilmiyor? Güvenlik duvarı koruması ve kuralları

- **[Yetişkin içeriği veya yasal](#set-up-web-content-filtering)** sorumluluk gibi kategorilere göre kişilerin belirli web sitelerini (URL) ziyaretlerini önleyen Web içeriği filtreleme.

Güvenlik ilkeleri, İş için Defender'da cihaz grupları aracılığıyla [cihazlara uygulanır](mdb-create-edit-device-groups.md#what-is-a-device-group). 

Güvenlik ilkelerinize ek olarak, Microsoft 365 Defender portalında [](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal)()[https://security.microsoft.com](https://security.microsoft.com) hangi saat dilimini kullanmak istediğiniz ve kullanılabilir hale gelen önizleme özelliklerinin edinip almayacakları gibi ayarları da görüntüleyemez ve düzenleyebilirsiniz.

Bu makaleyi, güvenlik ilkelerinizi ve ayarlarınızı yönetme kılavuzu olarak kullanın.

## <a name="what-to-do"></a>Ne yapmalı?

1. [Güvenlik ilkelerinizi ve cihazlarınızı yönetecek yeri seçin](#choose-where-to-manage-security-policies-and-devices).

2. [Yeni nesil koruma ilkelerinizi görüntüleme veya düzenleme](#view-or-edit-your-next-generation-protection-policies).

3. [Güvenlik duvarı ilkelerinizi ve özel kurallarınızı görüntüleme veya düzenleme](#view-or-edit-your-firewall-policies-and-custom-rules).

4. [Web içeriği filtrelemeyi ayarlama](#set-up-web-content-filtering).

5. [Web portalında diğer ayarları Microsoft 365 Defender düzenleyin](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal). 

6. [Sonraki adımlarınıza devam edin](#next-steps).

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="choose-where-to-manage-security-policies-and-devices"></a>Güvenlik ilkelerini ve cihazlarını yönetecek yeri seçme

Defender for Business, kurulum [ve yapılandırma sürecini kolaylaştıran](mdb-simplified-configuration.md) basitleştirilmiş bir yapılandırma işlemi içerir. Basitleştirilmiş yapılandırma işlemini seçiyorsanız, güvenlik ilkelerinizi web portalında () Microsoft 365 Defender yönetebilirsiniz[https://security.microsoft.com/](https://security.microsoft.com/). Ancak, bu seçenekle sınırlı değildirsiniz. Microsoft Endpoint Manager (Microsoft Intune) kullanıyorsanız, Endpoint Manager.

Aşağıdaki tablo, güvenlik ilkelerinizi ve cihazlarınızı yönetecek yeri seçmenize yardımcı olabilir. <br/><br/>

| Seçenek | Açıklama |
|:---|:---|
| **Önerilen Microsoft 365 Defender** *kullanma* | Mobil Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)), şirketin cihazlarını, güvenlik ilkelerini ve güvenlik ayarlarını yönetmek için tek alışverişte olacağınız yer olabilir. Güvenlik ilkelerinize ve ayarlarınıza erişebilir, [Tehdit &](mdb-view-tvm-dashboard.md) Güvenlik Açığı Yönetimi panoyu kullanabilir ve tüm olayları tek bir [yerde görüntüleyebilirsiniz](mdb-view-manage-incidents.md) ve yönetebilirsiniz. <br/><br/>Microsoft Endpoint Manager kullanıyorsanız, İş için Defender'a tümleşik cihazlarınız ve güvenlik ilkeleriniz Endpoint Manager. Daha fazla bilgi edinmek için aşağıdaki makalelere bakın:<br/><br/>- [İş için Defender varsayılan ayarları ve Microsoft Endpoint Manager](mdb-next-gen-configuration-settings.md#defender-for-business-default-settings-and-microsoft-endpoint-manager)<br/><br/>- [İş için Microsoft Defender'da Güvenlik Duvarı](mdb-firewall.md)   |
| **Microsoft Endpoint Manager'i kullanma** | Şirket güvenlik ilkelerini yönetmek için Endpoint Manager (Microsoft Intune içerir) kullanıyorsa, Endpoint Manager'ı kullanarak cihazları ve güvenlik ilkelerini yönetmeye devam edin. Daha fazla bilgi edinmek için bkz[. Cihaz güvenliğiyle cihaz güvenliğini uç nokta güvenlik ilkeleriyle yönetme Microsoft Intune](/mem/intune/protect/endpoint-security-policy). <br/><br/>İş için [Defender'da](mdb-simplified-configuration.md) basitleştirilmiş yapılandırma sürecine geçmeye karar verirseniz, daha sonra ilke çakışmalarını önlemek için Endpoint Manager tüm güvenlik ilkelerini [silmeniz](mdb-troubleshooting.yml) istenir. |

> [!IMPORTANT]
> Microsoft 365 Defender portalında güvenlik ilkelerini yönetiyorsanız, bu ilkeleri Endpoint Manager Virüsten Koruma veya Güvenlik  Duvarı ilkeleri olarak listelenmiş olarak görüntüebilirsiniz. Güvenlik duvarı ilkelerinizi güvenlik Endpoint Manager, listelenen iki ilke vardır: güvenlik duvarı korumanıza yönelik bir ilke ve özel kurallar için başka bir ilke.

## <a name="view-or-edit-your-next-generation-protection-policies"></a>Yeni nesil koruma ilkelerinizi görüntüleme veya düzenleme

Yeni nesil koruma ilkelerinizi yönetmek için Microsoft 365 Defender portalını mı yoksa Microsoft Endpoint Manager'i mi kullandığınıza bağlı olarak, aşağıdaki tabloda yer alan yordamlardan birini kullanın: <br/><br/>

| Portal | Yordam |
|:---|:---|
| Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Oturum Microsoft 365 Defender ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın. <br/><br/>2. Gezinti bölmesinde Cihaz **yapılandırması'ni seçin**. İlkeler, işletim sistemine ve ilke türüne göre düzenlenmiştir.<br/><br/>3. İşletim sistemi sekmesini seçin (örneğin, **Windows seçin**).<br/><br/>4. **İlke listenizi görüntülemek** için Yeni nesil koruması'nın kapsamını genişletin.<br/><br/>5. İlke hakkında daha fazla ayrıntı görüntülemek için bir ilke seçin. Değişiklik yapmak veya ilke ayarları hakkında daha fazla bilgi edinmek için aşağıdaki makalelere bakın: <br/>- [Cihaz ilkelerini görüntüleme veya düzenleme](mdb-view-edit-policies.md)<br/>- [Yeni nesil yapılandırma ayarlarını anlama](mdb-next-gen-configuration-settings.md)  |
| Microsoft Endpoint Manager merkezi ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Gidin ve [https://endpoint.microsoft.com](https://endpoint.microsoft.com) oturum açma. Artık Yönetim Merkezi'Microsoft Endpoint Manager siniz.<br/><br/>2. Uç nokta **güvenliği'ne seçin**.<br/><br/>3. Virüsten **Koruma'ya** seçerek bu kategorideki ilkelerinizi görüntüleyin. <br/><br/>Web'de güvenlik ayarlarınızı yönetmeye yardımcı Microsoft Endpoint Manager için, Güvenlik [açıkken uç nokta güvenliğini yönet Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="view-or-edit-your-firewall-policies-and-custom-rules"></a>Güvenlik duvarı ilkelerinizi ve özel kurallarınızı görüntüleme veya düzenleme

Güvenlik duvarı korumanızı yönetmek için Microsoft 365 Defender portalını mı yoksa Microsoft Endpoint Manager güvenlik duvarı korumasını mı kullandığınıza bağlı olarak, aşağıdaki tabloda yer alan yordamlardan birini kullanın: <br/><br/>

| Portal | Yordam |
|:---|:---|
| Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Oturum Microsoft 365 Defender ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın. <br/><br/>2. Gezinti bölmesinde Cihaz **yapılandırması'ni seçin**. İlkeler, işletim sistemine ve ilke türüne göre düzenlenmiştir.<br/><br/>3. İşletim sistemi sekmesini seçin (örneğin, **Windows seçin**).<br/><br/>4. İlke **listenizi** görüntülemek için Güvenlik Duvarı'nı genişletin.<br/><br/>5. İlke hakkında daha fazla ayrıntı görüntülemek için bir ilke seçin. Değişiklik yapmak veya ilke ayarları hakkında daha fazla bilgi edinmek için aşağıdaki makalelere bakın: <br/>- [Cihaz ilkelerini görüntüleme veya düzenleme](mdb-view-edit-policies.md)<br/>- [Güvenlik duvarı ayarları](mdb-firewall.md)<br/>- [Güvenlik duvarı ilkeleri için özel kurallarınızı yönetme](mdb-custom-rules-firewall.md)  |
| Microsoft Endpoint Manager merkezi ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Gidin ve [https://endpoint.microsoft.com](https://endpoint.microsoft.com) oturum açma. Artık Yönetim Merkezi'Microsoft Endpoint Manager siniz.<br/><br/>2. Uç nokta **güvenliği'ne seçin**.<br/><br/>3. bu **kategorideki ilkelerinizi** görüntülemek için Güvenlik Duvarı'nı seçin. Güvenlik duvarı koruması için tanımlanan özel kurallar ayrı ilkeler olarak listelenir.<br/><br/>Web'de güvenlik ayarlarınızı yönetmeye yardımcı Microsoft Endpoint Manager için, Güvenlik [açıkken uç nokta güvenliğini yönet Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="set-up-web-content-filtering"></a>Web içeriği filtrelemeyi ayarlama

Web içeriği filtreleme, güvenlik ekibinin içerik kategorilerine göre web sitelerine erişimi izlemesine ve düzenlemesine olanak sağlar. Örneğin:

- Yetişkinlere yönelik içerik: Cinsellik, çıplaklık, pornografi, cinsel içerikli içerik veya şiddet ile ilgili siteler

- Yüksek bant genişliği: Siteleri, resim paylaşım sitelerini veya eşler arası ana bilgisayarları indirme

- Yasal sorumluluk: Çocuğun kötüye kullanımı resimleri, yasa dışı faaliyetleri teşvik eden, işaret ya da okul hilesi teşvik eden veya zararlı etkinliklere teşvik eden siteler

- Boş zaman: Web tabanlı sohbet odaları, çevrimiçi oyun, web tabanlı e-posta veya sosyal ağ sağlayan siteler

- Kategorilere kapatılmamış: hiç içeriği olmayan veya yeni kaydedilen siteler

Bu kategorilere ait web sitelerinin hepsi kötü amaçlı değildir, ancak uyumluluk düzenlemeleri, bant genişliği kullanımı veya diğer endişelerden dolayı bunlar sorun yaratabilir. Buna ek olarak, güvenlik ekibinin tüm web sitesi kategorilerini engelleyip engellemey denetlemesi gerektiğini daha iyi anlamak için bir yalnızca denetim ilkesi oluşturabilirsiniz.

Web içeriği filtreleme, başlıca web tarayıcılarında Windows Defender SmartScreen (Microsoft Edge) ve Ağ Koruması (Chrome, Firefox, Doğru ve Opera) tarafından gerçekleştirilen bloklarla kullanılabilir. Daha fazla bilgi için bkz [. Web içeriği filtreleme önkoşulları](../defender-endpoint/web-content-filtering.md#prerequisites).

### <a name="to-set-up-web-content-filtering"></a>Web içeriği filtrelemeyi ayarlamak için

1. Web Microsoft 365 Defender () içinde,  >  Ayarlar [https://security.microsoft.com](https://security.microsoft.com) **Web içerik filtreleme+ İlke** **ekle'yi** >  seçin.

2. İlkeniz için bir ad ve açıklama belirtin.

3. Engellenecek kategorileri seçin. Her üst kategoriyi tamamen genişletmek ve belirli web içeriği kategorilerini seçmek için genişletme simgesini kullanın.

   Hiçbir web sitelerini engellemeden yalnızca denetim ilkesi ayarlamak için hiçbir kategori seçmeyin.

   Kategorilere **Göre Değil'i seçmeyin**.

4. İlkeyi uygulamak için cihaz gruplarını seçerek ilke kapsamını belirtin. Yalnızca seçili cihaz gruplarında yer alan cihazların seçili kategorilerde web sitelerine erişimi engellenebilir.

5. Özeti gözden geçirme ve ilkeyi kaydetme. İlke yenilemenin seçili cihazlarınıza geçerlik üzere 2 saat kadar sürebilir.

> [!TIP]
> Web içeriği filtreleme hakkında daha fazla bilgi edinmek için bkz [. Web içeriği filtreleme](../defender-endpoint/web-content-filtering.md).

## <a name="view-and-edit-other-settings-in-the-microsoft-365-defender-portal"></a>Web portalında diğer ayarları Microsoft 365 Defender düzenleme

Cihazlara uygulanan güvenlik ilkelerine ek olarak, İş için Defender'da görüntüleyemez ve düzenleyemezsiniz. Örneğin, kullanmak istediğiniz saat dilimini belirtirsiniz ve cihazları (veya çıkar) cihazları kullanabilirsiniz. 

> [!NOTE]
> Kiracınız için bu makalede listelenen ayarlardan daha fazla ayar bulabilirsiniz. Bu makalede, İş için Defender'da gözden geçirmeniz gereken en önemli ayarlar vurgulanır.

### <a name="settings-to-review-for-defender-for-business"></a>Ayarlar Defender for Business için gözden geçirmek zorunda değil

Aşağıdaki tabloda, İş için Defender'da görüntüleme (ve gerekirse düzenleme) ayarları açık almaktadır.

<br/><br/>

| Kategori | Ayar | Açıklama |
|:---|:---|:---|
| **Güvenlik merkezi** | **Saat dilimi** | Olaylarda görüntülenen tarih ve saatlerde, algılanan tehditlerde ve düzeltmelerde kullanılacak saat dilimini & seçin. UTC'i veya yerel saat diliminizi *kullanabilirsiniz (önerilir*).  |
| **Microsoft 365 Defender** | **Hesap** | Verilerinizin depolandığı yer, kiracı kimliğiniz ve kuruluş (kuruluş) kimliğiniz gibi ayrıntıları görüntüebilirsiniz. |
| **Microsoft 365 Defender**  | **Önizleme özellikleri**  | Yaklaşan özellikleri ve yeni özellikleri denemek için önizleme özelliklerini açma. Yeni özellikleri öniz alan ve geri bildirim sağlayan ilkler arasında yer görebilirsiniz. |
| **Uç noktalar**  | **E-posta bildirimleri** | E-posta bildirimi kurallarınızı ayarlayın veya düzenleyin. Güvenlik açıkları algılandığında veya bir uyarı oluşturulduğunda, e-posta bildirim kurallarında belirtilen alıcılar bir e-posta alır. [E-posta bildirimleri hakkında daha fazla bilgi alın](mdb-email-notifications.md). |
| **Uç noktalar**   | **Cihaz yönetimi** >  **Ekleme** | İndirilebilir bir betik kullanarak cihazları Defender for Business'a ekleme. Daha fazla bilgi edinmek için bkz [. Cihazları İş için Microsoft Defender'a ekleme](mdb-onboard-devices.md).   |  
| **Uç noktalar**  |  **Cihaz yönetimi** >  **Offboarding** | İş için Defender'dan çıkarma (kaldırma) cihazlar. Bir cihazla çıkarsanız artık verileri İş için Defender'a göndermez, ancak bu cihazdan çıkardan önce alınan veriler korunur. Daha fazla bilgi için bkz [. Cihaz çıkarma](mdb-onboard-devices.md#offboarding-a-device).  |

### <a name="access-your-settings-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında ayarlarınıza erişme

1. Microsoft 365 Defender portalına () gidin[https://security.microsoft.com/](https://security.microsoft.com/) ve oturum açın.

2. Önce **Ayarlar** sonra da bir kategori seçin (Güvenlik **merkezi**, Güvenlik Merkezi, **Microsoft 365 Defender** **Uç Noktalar gibi**).

3. Ayarlar listesinde, görüntülemek veya düzenlemek için bir öğe seçin.


## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki görevlerden bir veya birden fazlası ile devam edin:

- [İş için Microsoft Defender'ı kullanmaya başlama](mdb-get-started.md)

- [İş için Microsoft Defender'da cihazları yönetme](mdb-manage-devices.md)

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)

- [İş için Microsoft Defender'da ilkeleri görüntüleme veya düzenleme](mdb-view-edit-policies.md)
