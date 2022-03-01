---
title: Güvenlik için tehdit korumasını Microsoft 365 İş Ekstra
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
description: Veri kaybını önlemek ve müşterinizin hassas bilgilerini güvende tutmaya yardımcı olmak için uyumluluk özelliklerini ayarlayın.
ms.openlocfilehash: 69960c4f158a30d9d47d749ed1e7eb2d2d74f430
ms.sourcegitcommit: b6ab10ba95e4b986065c51179ead3810cc1e2a85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "63018874"
---
# <a name="set-up-compliance-features"></a>Uyumluluk özelliklerini ayarlama

Müşterileriniz Microsoft 365 İş Ekstra verilerinizi ve cihazlarınızı korumaya ve sizin ve müşterilerinize hassas bilgilerini güvende tutmanıza yardımcı olacak özelliklerle birlikte gelir.

## <a name="watch-set-up-dlp-features"></a>İzle: DLP özelliklerini ayarlama

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3TGvL?autoplay=false]

Veri kaybı önleme ilkeleri, sosyal güvenlik numaraları veya tıbbi kayıtlar gibi işletmenizin hassas bilgilerini belirlemeye ve korumaya yardımcı olur.

1. Çalışmaya başlama için yönetim merkezine [gidin ve Kurulum'u](https://admin.microsoft.com) **seçin**.
1. Ekranı aşağı **kaydırarak Veri kaybını önlemeyi ayarla'ya** kaydırın ve ardından **Görüntüle'yi ve ardından** Yönet'i **seçin**.
1. Bir ilkeyi düzenlemek için ilkeyi seçin, İlkeyi **düzenle'yi** ve sonra değiştirecek ilkeyi seçin. Örneğin, **taranacakları değiştirmek** için Konumlar'ı seçin.
1. Yeni ilke oluşturmak için İlke **oluştur'a seçin**.
1. Özel bir ilke oluşturabilir veya bir şablonla başlayabilirsiniz. Örneğin, HIPAA ilkesi oluşturmak için, Tıbbi ve sağlık şablonunu  seçin ve ardından ABD Sağlık Sigortası Yasası **(HIPAA)'yı seçin**. **İleri**'yi seçin.
1. Ayarlarınızı gözden geçirerek Oluştur'a **tıklayın**. İlkeniz yürürlüğe girdikten sonra, açıklanan hassas bilgileri içeren e-posta engellenir ve bu bilgileri göndermeyi denen gönderen bir uyarı iletisi görür.

Kişisel [verilerin kaybından korunmaya yönelik bir](../../compliance/create-a-dlp-policy-from-a-template.md) ilke ayarlama hakkında bilgi için bkz. Şablondan DLP ilkesi oluşturma. 
  
DLP, birçok farklı yerel ayarı için kullanıma hazır birçok ilke şablonuyla birlikte gelir. Örneğin, Avustralya Finansal Verileri, Kanada Kişisel Bilgileri Yasası, ABD Finansal Verileri, ve diğer. Tam [liste için bkz. DLP](../../compliance/what-the-dlp-policy-templates-include.md) ilkesi şablonlarının şunları içerir. Bu şablonların hepsi, PII şablonu örneğine benzer şekilde etkinleştirilebilir.
 
## <a name="set-up-email-retention-with-exchange-online-archiving"></a>E-posta bekletmeyi otomatik olarak Exchange Online Arşivleme

 **Exchange Online Arşivleme** özellikleri, eKbulma için e-posta içeriğini koruyarak uyumluluk ve mevzuat standartlarını korumanıza yardımcı olur. Ayrıca, bir güvenlik ihlali durumunda riski azaltmanıza yardımcı olur ve güvenlik ihlali sonrasında veya silinmiş öğeleri kurtarmanız gereken durumlarda verileri kurtarmak için bir yol sağlar. Bir kullanıcının içeriğini korumak için mahkeme saklamayı veya korumak istediğiniz içeriği özelleştirmek için bekletme ilkelerini kullanabilirsiniz.
  
**Mahkeme tutma:** Kullanıcının posta kutusunun tamamını mahkemelere koyarak, silinmiş öğeler de dahil olmak üzere tüm posta kutusu içeriğini koruyabilirsiniz. 
    
Posta kutusunu mahkeme tutma için Yönetim merkezinde tutmak için:
    
1. Sol gezintide Kullanıcılar Etkin **kullanıcılar'a** \> **gidin**.
    
2. Posta kutusunu mahkemelere almak istediğiniz bir kullanıcı seçin. Kullanıcı bölmesinde Posta **ayarları'ni genişletin ve Diğer** ayarlar'ın **yanında Posta özelliklerini** **Exchange seçin**.
    
3. Kullanıcının posta kutusu sayfasında, sol gezintiden ** posta kutusu özellikleri ** seçin ve sonra Mahkeme tutma altındaki Etkinleştir **bağlantısını seçin**.
    
4. Mahkeme **tutma iletişim** kutusunda, Mahkeme tutma süresi alanında **mahkeme tutma süresini belirtebilirsiniz** . Sonsuz bir basılı tutmak istediğiniz alanı boş bırakın. Ayrıca, notlar ekleyebilir ve posta kutusu sahibini bir web sitesine yönlendirebilirsiniz ve bu konuda mahkeme tutma hakkında daha fazla açıklamanız gerekir. \>**Kaydet'i tıklatın**.
    
**Bekletme:** Örneğin, belirli bir süre boyunca korumak veya bekletme döneminin sonunda içeriği kalıcı olarak silmek için özelleştirilmiş bekletme ilkelerini etkinleştirebilirsiniz. Daha fazla bilgi edinmek için bkz [. Bekletme ilkelerine genel bakış](../../compliance/retention.md).

## <a name="watch-set-up-sensitivity-labels"></a>İzle: Duyarlılık etiketlerini ayarlama

Duyarlılık etiketleri Azure Information Protection (AIP) Plan 1'i içerir ve etiketleri uygulayarak belgelerinizi ve e-postalarınızı sınıflandırmanıza ve isteğe bağlı olarak korumanıza yardımcı olur. Etiketler, kurallar ve koşullar tanımlayan yöneticiler tarafından, kullanıcılar tarafından el ile veya kullanıcıların önerilerinin verildiği bir birleşim kullanılarak otomatik olarak uygulanabilir.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3VRGT?autoplay=false]

1. Yönetim [merkezinde Uyumluluk](https://admin.microsoft.com) yönetim **merkezini** seçin.
1. **Sınıflandırma'ya** ve ardından Duyarlılık **etiketleri'ne tıklayın**.
1. Etiket **oluştur'a** tıklayın ve uyarı görüntülendiğinde Evet'i **seçin**.
1. Ayarlarınızı gözden geçirerek Oluştur'a **tıklayın**. Etiketiniz oluşturuldu. İstediğiniz diğer etiketler için de bu işlemi yinelayın.
1. Varsayılan olarak, etiketler Office şu sırayla görünür: **Gizli**, **İç** ve **Genel**. Sırayı değiştirmek için, her etiket için üç noktayı (diğer eylemler) seçin ve ardından etiketi yukarı veya aşağı hareket ettirin. Normalde, izinler en düşük düzeyden en yüksek izin düzeyine kadar listelenir.
1. Ayarlarınızı gözden geçirerek Yayımla'yı **seçin**.

Etiketlerinizin çalışması için, her kullanıcının Azure Information Protection birleşik etiket istemcisini indirmesi gerekir. Web'de **AzinfoProtection_UL.exe**, ardından Microsoft İndirme Merkezi'nden indirin ve kullanıcılarının bilgisayarlarında çalıştırın.

Word gibi bir Office uygulaması tekrar açabilirsiniz; oluşturulan duyarlılık etiketlerini de göreceğiniz gibi. Bir etiketi değiştirmek veya uygulamak için Duyarlılık'ı seçin ve bir etiket seçin.

### <a name="install-the-azure-information-protection-client-manually"></a>Azure Information Protection istemcisini el ile yükleme

AIP istemcisini el ile yüklemek için:

1. Yükleme **AzinfoProtection_UL.exe** [Microsoft indirme merkezinden indirin](https://www.microsoft.com/download/details.aspx?id=53018).
 
2. Yüklemenin çalıştığını doğrulamak için bir Word belgesi görüntüleyebilirsiniz ve Giriş sekmesinde Duyarlılık **seçeneğinin** kullanılabilir olduğundan **emin** olun.
<br/>![Word belgesinde Koruma sekmesi açılan listesinde.](../../media/word-sensitivity.png)

Daha fazla bilgi için bkz [. İstemciyi yükleme](/azure/information-protection/infoprotect-tutorial-step3).