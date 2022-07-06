---
title: Veri kaybı önleme ve Microsoft Teams
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Microsoft Teams sohbetleri ve kanalları Veri Kaybı Önleme (DLP) ilkelerini destekler.
ms.openlocfilehash: 5d2ee7cefc23a85aec1a75fbe9fe121feacbb51f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638377"
---
# <a name="data-loss-prevention-and-microsoft-teams"></a>Veri kaybı önleme ve Microsoft Teams

Kuruluşunuzda Microsoft Purview Veri Kaybı Önleme (DLP) varsa, kişilerin bir Microsoft Teams kanalında veya sohbet oturumunda hassas bilgileri paylaşmasını engelleyen ilkeler tanımlayabilirsiniz. Bu korumanın nasıl çalıştığına dair bazı örnekler aşağıda verilmiştir:

- **Örnek 1: İletilerdeki hassas bilgileri koruma**. Birinin Teams sohbetinde veya kanalında hassas bilgileri konuklarla (dış kullanıcılar) paylaşmaya çalıştığını varsayalım. Bunu önlemek için tanımlanmış bir DLP ilkeniz varsa, dış kullanıcılara gönderilen hassas bilgilere sahip iletiler silinir. Bu, DLP ilkenizin nasıl yapılandırıldığına göre otomatik olarak ve saniyeler içinde gerçekleşir.

    > [!NOTE]
    > Microsoft Teams için DLP, aşağıdakilere sahip Microsoft Teams kullanıcıları ile paylaşıldığında hassas içeriği engeller:<br/>- ekiplerde ve kanallarda [konuk erişimi](/MicrosoftTeams/guest-access); Veya<br/>- [toplantılarda](/MicrosoftTeams/manage-external-access) ve sohbet oturumlarında dış erişim. <p>Dış sohbet oturumları için DLP yalnızca hem gönderen hem de alıcı Yalnızca Teams modundaysa ve [Microsoft Teams yerel federasyonu](/microsoftteams/manage-external-access) kullanıyorsa çalışır. Teams için DLP, Skype Kurumsal veya yerel olmayan federasyon sohbet oturumlarıyla [birlikte çalışmadaki](/microsoftteams/teams-and-skypeforbusiness-coexistence-and-interoperability#interoperability-of-teams-and-skype-for-business) iletileri engellemez.

- **Örnek 2: Belgelerde hassas bilgileri koruma**. Birinin microsoft teams kanalında veya sohbette konuklarla belge paylaşmaya çalıştığını ve belgenin hassas bilgiler içerdiğini varsayalım. Bunu önlemek için tanımlanmış bir DLP ilkeniz varsa, belge bu kullanıcılar için açılmaz. Korumanın uygulanabilmesi için DLP ilkenizin SharePoint ve OneDrive'ı içermesi gerekir. Bu, SharePoint için Microsoft Teams'de görüntülenen ve bu nedenle kullanıcıların Office 365 DLP lisansına sahip olmasını gerektiren (Office 365 E3 dahil) ancak kullanıcıların Office 365 Gelişmiş Uyumluluk lisansına sahip olmasını gerektirmeyen bir DLP örneğidir.)

- **Örnek 3: Teams Paylaşılan Kanallarında iletişimleri koruma**. Paylaşılan kanallar için konak Teams ekibi DLP ilkesi uygulanır. Örneğin Contoso'nun TeamA'sına ait paylaşılan bir kanal olduğunu varsayalım. TeamA'nın bir DLP ilkesi P1'i vardır. Kanalı paylaşmanın 3 yolu vardır:
    - **Üyeyle paylaşma**: Contoso'dan user1'i TeamA üyesi yapmadan paylaşılan kanala katılmaya davet edebilirsiniz. Kullanıcı1 dahil olmak üzere bu paylaşılan kanaldaki herkes P1 kapsamında olacaktır.
    - **Ekiple paylaşma (şirket içinde):** Kanalı Contoso'daki başka bir ekip TeamB ile paylaşırsınız. Başka bir ekibin farklı bir DLP ilkesi olabilir, ancak bu önemli değildir. P1, hem TeamA hem de TeamB kullanıcıları dahil olmak üzere bu paylaşılan kanaldaki herkes için geçerlidir.
    - **Ekiple paylaşma (kiracılar arası)**: Kanalı Fabrikam'daki teamF ekibiyle paylaşırsınız. Fabrikam'ın kendi DLP ilkesi olabilir, ancak bu önemli değildir. P1, hem TeamA (Contoso) hem de TeamF (Fabrikam) kullanıcıları dahil olmak üzere bu paylaşılan kanaldaki herkese uygulanır.
 
## <a name="dlp-licensing-for-microsoft-teams"></a>Microsoft Teams için DLP Lisansı

[Veri kaybı önleme](dlp-learn-about-dlp.md) özellikleri şunlar için **özel kanal iletileri de dahil olmak üzere** Microsoft Teams sohbet ve kanal iletilerini içerir:

- Office 365 E5/A5/G5
- Microsoft 365 E5/A5/G5
- Microsoft 365 E5/A5/G5 Information Protection ve İdare
- Microsoft 365 E5/A5/G5/F5 Uyumluluğu ve F5 Güvenlik & Uyumluluğu

Office 365 ve Microsoft 365 E3 SharePoint Online, OneDrive ve Exchange Online için DLP koruması içerir. Teams dosyaları paylaşmak için SharePoint Online ve OneDrive kullandığından Teams aracılığıyla paylaşılan dosyaları da içerir.

Teams Sohbeti'nde DLP koruması desteği E5 gerektirir.

Lisans gereksinimleri hakkında daha fazla bilgi edinmek için bkz. [Microsoft 365 Tenant-Level Hizmetleri Lisanslama Kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

> [!IMPORTANT]
> DLP yalnızca sohbetteki veya kanal yazışmalarındaki gerçek iletilere uygulanır. Kısa bir ileti önizlemesi içeren ve kullanıcının bildirim ayarlarına göre görünen etkinlik bildirimleri Teams DLP'ye dahil **değildir** . İletinin önizlemede görünen bölümünde bulunan tüm hassas bilgiler, DLP ilkesi uygulandıktan ve iletinin kendisine hassas bilgiler kaldırıldıktan sonra bile bildirimde görünür durumda kalır.

## <a name="scope-of-dlp-protection"></a>DLP korumasının kapsamı

DLP koruması Teams varlıklarına farklı uygulanır.

|İlkenin kapsamı |Bu Teams Varlıkları |DLP koruması kullanılabilir olacak|
|---------|---------|---------|
|Bireysel kullanıcı hesapları     |1:1/n sohbetler         |Evet         |
|     |Standart ve paylaşılan kanal iletileri         |Hayır         |
|     |Özel kanal iletileri         |Evet         |
|Güvenlik grupları/dağıtım listeleri  | 1:1/n sohbetler         |Evet         |
|     |Standart ve paylaşılan kanal iletileri  |Hayır         |
|     |Özel kanal iletileri         |Evet        |
|Microsoft 365 grubu    |1:1/n sohbetler          |Hayır         |
|     |Standart ve paylaşılan kanal iletileri          |Evet        |
|     |Özel kanal iletileri|Hayır| 


## <a name="policy-tips-help-educate-users"></a>İlke ipuçları, kullanıcıları eğitmene yardımcı olur

[DLP'nin Exchange, Outlook, Web üzerinde Outlook,](data-loss-prevention-policies.md#policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web) [SharePoint Online, OneDrive İş siteleri](data-loss-prevention-policies.md#policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites) ve [Office masaüstü istemcilerinde](data-loss-prevention-policies.md#policy-evaluation-in-the-office-desktop-programs) nasıl çalıştığına benzer şekilde, bir eylem DLP ilkesiyle tetiklendiğinde ilke ipuçları görüntülenir. İlke ipucu örneği aşağıda verilmişti:

![Teams'de engellenen ileti bildirimi.](../media/dlp-teams-blockedmessage-notification.png)

Burada, gönderen bir Microsoft Teams kanalında sosyal güvenlik numarası paylaşmaya çalıştı. **Ne yapabilirim?** bağlantısı, gönderenin sorunu çözmesi için seçenekler sağlayan bir iletişim kutusu açar. Gönderenin ilkeyi geçersiz kılmayı tercih ettiğini veya bir yöneticiyi gözden geçirip çözmesi için bilgilendirebileceğine dikkat edin.

![Engellenen iletiyi çözümleme seçenekleri.](../media/dlp-teams-blockedmessage-possibleactions.png)

Kuruluşunuzda, kullanıcıların bir DLP ilkesini geçersiz kılmasına izin vermeyi seçebilirsiniz. DLP ilkelerinizi yapılandırırken varsayılan ilke ipuçlarını kullanabilir veya kuruluşunuz için [ilke ipuçlarını özelleştirebilirsiniz](#to-customize-policy-tips) .

Bir gönderenin Teams kanalında sosyal güvenlik numarası paylaştığı örneğimize dönüp alıcının gördüğü şey şu şekildedir:

> [!div class="mx-imgBorder"]
> ![İleti engellendi.](../media/dlp-teams-blockedmessage-notification-to-user.png)

### <a name="to-customize-policy-tips"></a>İlke ipuçlarını özelleştirmek için

Bu görevi gerçekleştirmek için DLP ilkelerini düzenleme izinlerine sahip bir rol atanmış olmalıdır. Daha fazla bilgi için bkz. [İzinler](data-loss-prevention-policies.md#permissions).

1. Purview Uyumluluk Merkezi'ne ([https://compliance.microsoft.com](https://compliance.microsoft.com)) gidin ve oturum açın.

2. **Veri kaybı önleme** > **İlkesi'ni** seçin.

3. Bir ilke seçin ve **İlke ayarları'nın** yanında **Düzenle'yi** seçin.

4. Yeni bir kural oluşturun veya ilke için mevcut bir kuralı düzenleyin.

5. **Kullanıcı bildirimleri** sekmesinde **E-posta metnini özelleştir** ve/veya **İlke ipucu metin seçeneklerini özelleştir'i** seçin.

6. E-posta bildirimleri ve/veya ilke ipuçları için kullanmak istediğiniz metni belirtin ve **kaydet'i** seçin.

7. **İlke ayarları** sekmesinde **Kaydet'i** seçin.

Yaptığınız değişikliklerin veri merkeziniz üzerinden çalışması ve kullanıcı hesaplarıyla eşitlenmesi için yaklaşık bir saat bekleyin.
 <!-- why are these syncing to user accounts? -->

## <a name="add-microsoft-teams-as-a-location-to-existing-dlp-policies"></a>Microsoft Teams'i mevcut DLP ilkelerine konum olarak ekleme

Bu görevi gerçekleştirmek için DLP ilkelerini düzenleme izinlerine sahip bir rol atanmış olmalıdır. Daha fazla bilgi için bkz. [İzinler](data-loss-prevention-policies.md#permissions).

1. Uyumluluk Merkezi'ne ([https://compliance.microsoft.com](https://compliance.microsoft.com)) gidin ve oturum açın.

2. **Veri kaybı önleme** > **İlkesi'ni** seçin.

3. bir ilke seçin ve **Konumlar'ın** altındaki değerlere bakın. **Teams sohbeti ve kanal iletilerini** görürseniz hazırsınız demektir. Bunu yapmazsanız **Düzenle'ye** tıklayın.

4. **Durum** sütununda **Teams sohbeti ve kanal iletileri** için ilkeyi açın.

5. **Konumları seç** sekmesinde, tüm hesapların varsayılan ayarını koruyun veya **Belirli konumları seçmeme izin ver'i** seçin. Şunları belirtebilirsiniz:

    1. Dahil etmek veya hariç tutmak için en fazla 1000 bireysel hesap
    1. Dahil etmek veya dışlamak için dağıtım listeleri ve güvenlik grupları. 
    <!-- 1. the shared mailbox of a shared channel. **This is a public preview feature.**--> 
    
6. Ardından **İleri'yi** seçin.

7. **Kaydet**'e tıklayın.

Yaptığınız değişikliklerin veri merkeziniz üzerinden çalışması ve kullanıcı hesaplarıyla eşitlenmesi için yaklaşık bir saat bekleyin.
<!-- again, why user accounts? -->

## <a name="define-a-new-dlp-policy-for-microsoft-teams"></a>Microsoft Teams için yeni bir DLP ilkesi tanımlama

Bu görevi gerçekleştirmek için DLP ilkelerini düzenleme izinlerine sahip bir rol atanmış olmalıdır. Daha fazla bilgi için bkz. [İzinler](data-loss-prevention-policies.md#permissions).

1. Uyumluluk Merkezi'ne ([https://compliance.microsoft.com](https://compliance.microsoft.com)) gidin ve oturum açın.

2. **Veri kaybı önleme** > **İlkesi+ İlke** >  **oluştur'u** seçin.

3. Bir [şablon](data-loss-prevention-policies.md#dlp-policy-templates) seçin ve ardından **İleri'yi** seçin.

    Örneğimizde, ABD Kişisel Bilgi Verileri şablonunu seçtik.

4. **İlkenizi adlandırın** sekmesinde ilke için bir ad ve açıklama belirtin ve ardından **İleri'yi** seçin.

5. **Konumları seç** sekmesinde, tüm hesapların varsayılan ayarını koruyun veya **Belirli konumları seçmeme izin ver'i** seçin. Şunları belirtebilirsiniz:

    1. Dahil etmek veya hariç tutmak için en fazla 1000 bireysel hesap
    1. Dahil etmek veya dışlamak için dağıtım listeleri ve güvenlik grupları. **Bu bir genel önizleme özelliğidir.**
    <!-- 1. the shared mailbox of a shared channel. **This is a public preview feature.**-->  

 
    > [!NOTE]
    > Hassas bilgiler içeren belgelerin Teams'de uygunsuz bir şekilde paylaşılmadığından emin olmak istiyorsanız, **Teams sohbeti ve kanal iletileriyle** birlikte **SharePoint sitelerinin** ve **OneDrive hesaplarının** açık olduğundan emin olun.

6. **İlke ayarları** sekmesinde, **Korumak istediğiniz içerik türünü özelleştir'in** altında varsayılan basit ayarları koruyun veya **Gelişmiş ayarları kullan'ı** ve ardından **İleri'yi** seçin. Gelişmiş ayarları seçerseniz, ilkeniz için kurallar oluşturabilir veya düzenleyebilirsiniz. Bu konuda yardım almak için bkz [. Basit ayarlar ve gelişmiş ayarlar](data-loss-prevention-policies.md#simple-settings-vs-advanced-settings).

7.  **İlke ayarları** sekmesindeki **Hassas bilgileri algılarsak ne yapmak istiyorsunuz?** altında ayarları gözden geçirin. Varsayılan [ilke ipuçlarını ve e-posta bildirimlerini](use-notifications-and-policy-tips.md) burada tutabilir veya özelleştirebilirsiniz.



    Ayarları gözden geçirmeyi veya düzenlemeyi bitirdiğinizde **İleri'yi** seçin.

8. **İlke ayarları** sekmesinde, **İlkeyi açmak mı yoksa önce işleri test etmek mi istiyorsunuz?** altında, ilkeyi açmayı, [önce test](dlp-overview-plan-for-dlp.md#policy-deployment) etmeyi veya şimdilik kapalı tutmayı seçin ve **ardından İleri'yi** seçin.

9. **Ayarlarınızı gözden geçirin** sekmesinde, yeni ilkenizin ayarlarını gözden geçirin. Değişiklik yapmak için **Düzenle'yi** seçin. İşiniz bittiğinde **Oluştur'u** seçin.

Yeni ilkenizin veri merkezinizde çalışması ve kullanıcı hesaplarıyla eşitlenmesi için yaklaşık bir saat bekleyin.

## <a name="prevent-external-access-to-sensitive-documents"></a>Hassas belgelere dış erişimi engelleme

Hassas bilgiler içeren SharePoint belgelerine dış konuklar tarafından varsayılan olarak SharePoint veya Teams'den erişilemediğinden emin olmak için aşağıdakileri seçin:

- DLP, [yeni dosyaları varsayılan olarak hassas olarak işaretleyerek](/sharepoint/sensitive-by-default) belgeleri tarayana ve paylaşılabilir olarak işaretleyene kadar korunduğundan emin olabilirsiniz.

- Önerilen DLP ilke yapısı

    - **Koşul -ları**
        - İçerik şu hassas bilgi türlerinden herhangi birini içerir: [Geçerli olan tümünü seçin]
        
        - İçerik Microsoft 365'ten kuruluşum dışındaki kişilerle paylaşılıyor
        
          > [!div class="mx-imgBorder"]
          > ![Hassas içeriğin dış paylaşımını algılamak için DLP koşulları.](../media/dlp-teams-external-sharing/external-condition.png)

    - **Eylem**
        - Dış kullanıcılar için içeriğe erişimi kısıtlama
        
        - Kullanıcılara e-posta ve ilke ipuçlarıyla bildirme
        
        - Olay raporlarını Yöneticiye gönderme
        
        > [!div class="mx-imgBorder"]
        > ![Hassas içeriğin dış paylaşımını engellemek için DLP eylemi.](../media/dlp-teams-external-sharing/external-action.png)

SharePoint'te hassas bilgiler içeren bir belgeyi dış konukla paylaşmaya çalışırken DLP ilkesi çalışır durumda:

> [!div class="mx-imgBorder"]
> ![Dış paylaşım engellendi.](../media/dlp-teams-external-sharing/external-sharing-blocked.png)

<!--DLP policy in action when guest attempts to open a document in Teams with block external:
can't use the below image it contains a non-approved name.
> [!div class="mx-imgBorder"]
> ![External access blocked.](../media/dlp-teams-external-sharing/external-access-blocked.png)-->

## <a name="related-articles"></a>İlgili makaleler

- [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md)
- [DLP ilkeleri için e-posta bildirimleri gönderme ve ilke ipuçlarını gösterme](use-notifications-and-policy-tips.md)
