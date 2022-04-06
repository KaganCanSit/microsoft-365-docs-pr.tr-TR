---
title: E-posta teslim edilen kötü amaçlı e-postaları Microsoft 365, kötü amaçlı e-postaları bulma ve araştırma
keywords: TIMailData-Inline, Security Olayı, olay, Uç Nokta için Microsoft Defender PowerShell, e-posta kötü amaçlı yazılım, güvenliği ihlal edilmiş kullanıcılar, e-posta kimlik avı, e-posta kötü amaçlı yazılım, e-posta üst bilgilerini okuma, üst bilgileri okuma, e-posta üst bilgilerini açma, özel eylemler
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 12/16/2020
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 8f54cd33-4af7-4d1b-b800-68f8818e5b2a
ms.collection:
- M365-security-compliance
description: Kötü amaçlı e-postaları bulmak ve araştırmak için tehdit araştırma ve yanıt özelliklerini nasıl kullanabileceğinizi öğrenin.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 48deec7763981b10daf1d0c16cbef95d0e2dbaeb
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476543"
---
# <a name="investigate-malicious-email-that-was-delivered-in-microsoft-365"></a>Dosyada teslim edilen kötü amaçlı e-postaları Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Aşağıdakiler için geçerlidir:**

- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Office 365 için Microsoft Defender](defender-for-office-365.md), kuruluş riskine neden olan etkinlikleri araştırmanıza ve organizasyonlarınızı korumak için bir işlem uygulamanıza olanak sağlar. Örneğin, kuruluşun güvenlik ekibinin bir parçasısanız, teslim edilen şüpheli e-posta iletilerini bulabilir ve araştırabilirsiniz. Tehdit Gezgini'ni (veya [gerçek zamanlı algılamaları) kullanarak bunuabilirsiniz](threat-explorer.md).

> [!NOTE]
> Buradaki düzeltme makalesine [atlayın](remediate-malicious-email-delivered-office-365.md).

## <a name="before-you-begin"></a>Başlamadan önce

Aşağıdaki gereksinimlerin karşı olduğundan emin olun:

- Kuruluşun [kullanıcılara Office 365 için Microsoft Defender](defender-for-office-365.md) [lisansı var ve lisansları atanmış.](../../admin/manage/assign-licenses-to-users.md)

- [Denetim günlüğü](../../compliance/turn-audit-log-search-on-or-off.md) , sizin için açık.

- Kuruluşta istenmeyen posta önleme, kötü amaçlı yazılımdan koruma ve kimlik avı önleme gibi ilkeler tanımlanmıştır. Bkz[. Güvenlik tehditlerine karşı Office 365](protect-against-threats.md).

- Bir genel yöneticisiniz veya portalda Güvenlik Yöneticisi ya da Arama ve Temizleme rolü Microsoft 365 Defender. Daha fazla bilgi için bkz[. Microsoft 365 Defender portalına.](permissions-microsoft-365-security-center.md) Bazı eylemler için, Önizleme rolüne de atanmış olması gerekir.

### <a name="preview-role-permissions"></a>Rol izinlerini önizleme

İleti üst bilgilerini görüntüleme veya e-posta iletisi içeriğini indirme gibi bazı eylemleri gerçekleştirmek için, Uygun olan başka bir rol  grubuna Önizleme rolünün eklenmiş olması gerekir. Aşağıdaki tablo gerekli rolleri ve izinleri net bir şekilde açıklamayı sağlar.

|Etkinlik|Rol grubu|Önizleme rolü gerekli mi?|
|---|---|---|
|Tehditleri çözümlemek için Tehdit Gezgini'ni (ve Gerçek zamanlı algılamaları) kullanma|Genel Yönetici <p> Güvenlik Yöneticisi <p> Güvenlik Okuyucu|Hayır|
|Hem e-posta iletilerinin üst bilgilerini görüntülemek hem de karantinaya alınmış e-posta iletilerini önizlemek ve indirmek için Tehdit Gezgini'ni (ve Gerçek zamanlı algılamaları) kullanın|Genel Yönetici <p> Güvenlik Yöneticisi <p> Güvenlik Okuyucu|Hayır|
|Üstbilgileri görüntülemek, e-postayı önizlemek (yalnızca e-posta varlık sayfasında) ve posta kutularına teslim edilen e-posta iletilerini indirmek için Threat Explorer'ı kullanın|Genel Yönetici <p> Güvenlik Yöneticisi <p> Güvenlik Okuyucu <p> Önizleme|Evet|

> [!NOTE]
> **Önizleme** bir rol grubu değil, bir rol grubu. Önizleme rolü, portalda var olan bir rol grubuna veya yeni bir rol grubuna Microsoft 365 Defender gerekir. Daha fazla bilgi için bkz[. Microsoft 365 Defender portalına.](permissions-microsoft-365-security-center.md)
>
> Genel Yönetici rolüne ' Microsoft 365 yönetim merkezi atanır<https://admin.microsoft.com>. Güvenlik Yöneticisi ve Güvenlik Okuyucusu rolleri portalda Microsoft 365 Defender atanır.

E-posta önizleme ve indirmenin hassas etkinlikler olduğunu anlıyoruz, bu nedenle bu etkinlikler için denetim etkinleştirilir. Yönetici bu etkinlikleri e-postada gerçekleştirsin mi, denetim günlükleri aynı  günlükler oluşturulur ve Microsoft 365 Defender portalında  \> <https://security.microsoft.com> Denetim Araması sekmesinde görülebilir ve Kullanıcılar kutusunda yönetici adına **göre** filtre uygulama. Filtrelenmiş sonuçlarda **AdminMailAccess etkinliği gösterir**. Önizlemesi görüntülendikten veya indirilen e-posta **hakkında daha fazla bilgi** bölümünde ayrıntıları görüntülemek için bir satır seçin.

## <a name="find-suspicious-email-that-was-delivered"></a>Teslim edilen şüpheli e-postayı bulma

Tehdit Gezgini, iletileri bulma ve silme, kötü amaçlı e-posta gönderenin IP adresini tanımlama veya daha fazla araştırma için olay başlatma gibi çeşitli amaçlara hizmet verebilecek güçlü bir rapordır. Aşağıdaki yordam, alıcının posta kutularından kötü amaçlı e-postaları bulmak ve silmek için Explorer kullanmaya odaklanır.

> [!NOTE]
> Gezgin'de varsayılan aramalar, şu anda bulut posta kutusundan sıfır saatlik otomatik temizleme (ZAP) ile kaldırılan teslim edilen öğeleri içermemiştir. Bu sınırlama tüm görünümler için geçerlidir (örneğin, E-posta Kötü Amaçlı **E-posta veya \>** **E-posta Kimlik Avı \>** görünümleri). ZAP tarafından kaldırılan öğeleri eklemek için ZAP tarafından kaldırıldı'yı **eklemek için** bir **Teslim eylemi kümesi eklemeniz gerekir**. Tüm seçenekleri dahil etmek üzere, ZAP tarafından kaldırılan öğeler de dahil olmak üzere tüm teslim eylemi sonuçlarının yer almaktadır.

1. aşağıdaki Microsoft 365 Defender portalında E-posta <https://security.microsoft.com>gönder **ve işbirliği &** \> **gidin**. Doğrudan Explorer sayfasına **gitmek için** kullanın <https://security.microsoft.com/threatexplorer>.

   Gezgin **sayfasında** , Ek **eylemler sütunu yöneticilerin** e-posta işleme sonuçlarını gösterir. Ek **eylemler sütununa** Teslim eylemi ve Teslim konumu **ile aynı** yerde **erişilebilir**. Yöneticiler için daha iyi arama deneyiminin daha iyi olması için yeni bir özellik olan Threat Explorer'ın e-posta zaman çizelgesinin sonunda özel eylemler güncelleştirilebilir.

2. Görünüm menüsünde **açılan listeden** Tüm **e-postayı** \> **E-postayla** Gönder'i seçin.

    :::image type="content" source="../../media/tp-InvestigateMalEmail-viewmenu.png" alt-text="Kötü Amaçlı Yazılım açılan listesi" lightbox="../../media/tp-InvestigateMalEmail-viewmenu.png":::

    Kötü *Amaçlı Yazılım* görünümü şu anda varsayılan görünüm durumdadır ve kötü amaçlı yazılım tehdidinin algı bulunduğu e-postaları yakalar. Kimlik *Avı* görünümü, Kimlik Avı için de aynı şekilde çalışır.

    Bununla birlikte, *Tüm e-posta* görünümünde, kuruluş tarafından alınan her posta tehdit algılanır veya algılanmaz. Tahmin edin, bu çok fazla veridir ve bu nedenle bu görünümde filtrenin uygulanmasını isteyen bir yer tutucu görüntülenir. (Bu görünüm yalnızca Office 365 için Defender P2 müşterileri tarafından kullanılabilir.)

    *Gönderiler* görünümü yönetici veya kullanıcı tarafından Microsoft'a bildirilen tüm postaları gösterir.

4. **Tehdit Gezgini'nde arama** ve filtreleme: Filtreler, araştırmalarında yöneticilere yardımcı olmak için arama çubuğunda sayfanın en üstünde görüntülenir. Aynı anda birden çok filtrenin uygulanamaya ve arama daraltmak için bir filtreye eklenen birden çok virgülle ayrılmış değere dikkat edin. Unutmayın:

    - Filtreler, çoğu filtre koşullarında tam olarak eşler.
    - Konu filtresi CONTAINS sorgusu kullanır.
    - URL filtreleri protokollerle birlikte veya protokoller olmadan çalışır (örneğin. https).
    - URL etki alanı, URL yolu, URL etki alanı ve yol filtreleri için filtre uygulama protokolü gerekli değildir.
    - İlgili sonuçları elde etmek için filtre değerlerini her değiştirken Yenile simgesine tıklamalısınız.

5. **Gelişmiş filtreler**: Bu filtrelerle, karmaşık sorgular oluşturabilir ve veri kümenize filtre ekleyebilirsiniz. Gelişmiş *Filtreler'e tıklamak* , seçeneklerin olduğu bir açılır pencere açar.

   Gelişmiş filtreleme, arama özelliklerine büyük bir ektir. Alıcı **, Gönderen** ve Gönderen etki alanı **filtrelerinin** boole  NOT değeri, yöneticilerin değerleri dışlayarak araştırmalarına olanak sağlar. Bu seçenek, Eşittir **yok seçimidir** . Bu seçenek yöneticilerin istenmeyen posta kutularını soruşturmaların dışında çekmesini sağlar (örneğin, uyarı posta kutuları ve varsayılan yanıt posta kutuları) ve yöneticilerin Belirli bir konuyu (örneğin, Dikkat) araysa da, Alıcının Eşittir yok: yok olarak ayarlandırıldığı *durumlarda defaultMail@contoso.com*. Bu tam bir değer aramasıdır.

   :::image type="content" source="../../media/tp-InvestigateMalEmail-AdvancedFilter.png" alt-text="Alıcılar bölmesi" lightbox="../../media/tp-InvestigateMalEmail-AdvancedFilter.png":::

   Başlangıç tarihi ve bitiş tarihine bir zaman filtresi eklemek, güvenlik ekibinin hızla detaya inmelerine yardımcı olur. İzin verilen en kısa süre 30 dakikadır. Şüpheli eylemi zaman çerçevesine göre (örneğin, 3 saat önce oldu) daraltabiliyorsanız, bu işlem bağlamı sınırlandırır ve sorunun yerini an etmeye yardımcı olur.

   :::image type="content" source="../../media/tp-InvestigateMalEmail-FilterbyHours.png" alt-text="Saate göre filtreleme seçeneği" lightbox="../../media/tp-InvestigateMalEmail-FilterbyHours.png":::

6. **Tehdit Gezgini'nde alanlar**: Tehdit Gezgini Teslim *eylemi, Teslim* *konumu, Özel* eylem, Yön, Geçersiz Kılmalar ve URL tehdidi gibi güvenlikle ilgili çok daha fazla *posta bilgisi sağlar*. Ayrıca, kuruluş güvenlik ekibinin daha yüksek bir kesinlik ile araştırmalarına olanak sağlar.

    *Teslim eylemi* , var olan ilkeler veya algılamalar nedeniyle e-posta üzerinde ilen eylemdir. Bir e-postanın gerçekleştir aşağıdaki olası eylemleri gerçekleştirebilirsiniz:

    - **Teslim** Edildi – e-posta kullanıcının gelen kutusu veya klasörüne teslim edildi ve kullanıcı doğrudan buna erişebilirsiniz.
    - **Gereksiz (** Gereksiz postaya teslim edildi)– e-posta kullanıcının gereksiz klasörüne veya silinmiş klasörüne gönderilmiştir ve kullanıcının Gereksiz veya Silinmiş klasöründeki e-posta iletilerine erişimi olur.
    - **Engellendi –** karantinaya alınan, başarısız olan veya bırakılan tüm e-posta iletileri.
    - **Değiştirildi –** kötü amaçlı eklerin kötü amaçlı eklerin değiştir olduğu tüm e-.txt ekin kötü amaçlı olduğunu ima alan dosyalar

    **Teslim konumu**: Yöneticilerin kötü amaçlı e-postanın nerede sona ermiştir ve bu iletide hangi eylemlerin gerçekleştirildiklerini anlamalerine yardımcı olmak için Teslim konumu filtresi kullanılabilir. Sonuçta elde edilen veriler elektronik tablo olarak dışarı aktarabilirsiniz. Olası teslim konumları:

    - **Gelen kutusu veya** klasör – E-posta, e-posta kurallarınıza göre Gelen Kutusu'ta veya belirli bir klasördedir.
    - **Şirket içi veya dış** – Posta kutusu Bulutta yoktur ama şirket içindedir.
    - **Gereksiz klasörü** – E-posta kullanıcının Gereksiz posta klasöründedir.
    - **Silinmiş öğeler klasörü** – E-posta kullanıcının Silinmiş öğeler klasöründedir.
    - **Karantina** – Kullanıcının posta kutusunda değil, karantinada olan e-posta.
    - **Başarısız** – E-posta posta posta kutusuna ulaşamadı.
    - **Bırakılan** – E-posta, posta akışında bir yerde kayboldu.

    **Yön:** Bu seçenek, güvenlik işlemleri ekibimizin bir postanın geldiği veya gidiyor olan 'yönü' ile filtrelemesini sağlar. Yön değerleri *Gelen, Giden* ve *Intra-kuruluş* değerleridir (sırasıyla, kuruluş dışından kuruluşa gelen, kuruluş dışından gönderilen veya şirket içinde kendi kuruluşa gönderilen postaya karşılık gelir).  Bu bilgiler, güvenlik işlemleri ekiplerinin kimlik sahteliği ve kimliğe bürünme farkını farklarına yardımcı olabilir, çünkü Yön değeri arasındaki bir yanlışlık (örneğin. *Gelen)* ve gönderenin (iç *etki alanı gibi* görünen) etki alanı ortaya çıkar! Yön değeri ayrıdır ve İleti İzleme'den farklı olabilir. Sonuçlar elektronik tablo olarak dışarı aktarabilirsiniz.

    **Geçersiz kılmalar**: Bu filtre, postanın ayrıntılar sekmesinde görünen bilgileri alır ve bunu, postalara izin verme ve engellemeye izin veren kuruluş veya kullanıcı ilkelerinin geçersiz k olduğu yeri göstermek *için kullanır*. Bu filtreyle ilgili en önemli şey, kuruluş güvenlik ekibinin yapılandırma nedeniyle teslim edilen şüpheli e-postaların ne kadar olduğunu görmelerine yardımcı olmasıdır. Bu, onlara gerektiğinde izin ve blokları değiştirme fırsatı verir. Bu filtrenin sonuç kümesi elektronik tabloya aktarabilirsiniz.

    |Tehdit Gezgini Geçersiz Kılmaları|Bunların anlamı|
    |---|---|
    |Kuruluş İlkesi tarafından izin verildi|Posta, kuruluş ilkesi tarafından yönlendirildi ve posta kutusuna izin verildi.|
    |Kuruluş ilkesi tarafından engellendi|Postanın, kuruluş ilkesi tarafından yönlendirilen posta kutusuna teslimi engellendi.|
    |Kuruluş İlkesi tarafından engellenen dosya uzantısı|Dosyanın, kuruluş ilkesi tarafından yönlendirilen posta kutusuna teslimi engellendi.|
    |Kullanıcı İlkesi tarafından İzin Verildi|Posta, kullanıcı ilkesi tarafından yönlendirildi ve posta kutusuna izin verildi.|
    |Kullanıcı İlkesi tarafından engellendi|Posta'nın, kullanıcı ilkesi tarafından yönlendirilen posta kutusuna teslimi engellenmiş.|

    **URL tehditi**: URL tehdit alanı, bir URL tarafından sunulan  tehdidi göstermek için e-postanın ayrıntılar sekmesine ekli olarak bulunmaktadır. Bir  URL tarafından sunulan tehditlerde *Kötü Amaçlı* *Yazılım, Kimlik* Avı veya *İstenmeyen* Posta ve tehdit olmayan bir URL'de tehdit yoktur bölümü vardır.

7. **E-posta zaman** çizelgesi görünümü: Güvenlik işlemleri ekibimizin daha fazla araştırma yapmak için e-posta ayrıntılarını derinden incelemesi gerekiyor olabilir. E-posta zaman çizelgesi yöneticilerin, bir e-posta üzerinde teslimden teslim sonrası teslime kadar  gerçekleştirilen eylemleri görüntülemelerini sağlar. E-posta zaman çizelgesini görüntülemek için, e-posta iletisi konusunu tıklatın ve sonra E-posta zaman çizelgesi'ni tıklatın. (Bu başlık, panelde Özet veya Ayrıntılar gibi diğer başlıklar arasında gösterilir.) Bu sonuçlar elektronik tablo olarak dışarı aktarabilirsiniz.

    E-posta zaman çizelgesi, e-posta için tüm teslim ve teslim sonrası olaylarını gösteren bir tablo açar. E-postada başka eylem yoksa, özgün teslim için Bir sonuç olduğunu (Örneğin Engellendi) ve Kimlik Avı gibi bir karara sahip bir olay *görüyorsanız*. Yöneticiler, sekme ve e-postanın tüm ayrıntıları (Konu, Gönderen, Alıcı, Ağ ve İleti Kimliği gibi) dahil olmak üzere, e-posta zaman çizelgesinin tamamını dışarı aktarabilirsiniz. E-posta geldiğinden bu yana olan olayları anlamaya denemek için farklı konumları kontrol etmek için daha az zaman harcadığınız için e-posta zaman çizelgesi rastgele başlatmayı keser. E-postada birden fazla olay olduğunda veya e-postaya yakın bir zamanda olduğunda, bu olaylar zaman çizelgesi görünümünde görünür.

8. **Önizleme / indirme**: Threat Explorer güvenlik işlemleri ekibinize şüpheli e-postaları araştırmaları için gereken ayrıntıları verir. Güvenlik işlemleri ekipleriniz şunları da olabilir:

    - [Teslim eylem ve konumunu kontrol edin](#check-the-delivery-action-and-location).

    - [E-postanızı zaman çizelgenizi görüntüleme](#view-the-timeline-of-your-email).

### <a name="check-the-delivery-action-and-location"></a>Teslim eylem ve konumunu denetleme

Tehdit [Gezgini'nde (ve gerçek zamanlı algılamalar)](threat-explorer.md) artık eski Teslim Durumu  sütunu yerine Teslim  Eylemi ve Teslim Konumu **sütunlarına sahipsiniz**. Böylece, e-posta iletilerinizin nereye gittiğinin resmi daha eksiksiz olur. Bu değişikliğin bir parçası olarak, güvenlik işlemleri ekipleri için soruşturmaları daha kolay hale getirirsiniz, ancak net sonuç bir bakışta sorun e-posta iletilerinin yerini bilmektir.

Teslim Durumu şimdi iki sütuna ayrıldı:

- **Teslim eylemi** - Bu e-postanın durumu nedir?
- **Teslim konumu** - Bu e-posta bu şekilde nereye yönlendirildi?

Teslim eylemi, var olan ilkeler veya algılamalar nedeniyle e-posta üzerinde ilen eylemdir. Bir e-postanın gerçekleştir aşağıdaki olası eylemleri gerçekleştirebilirsiniz:

- **Teslim** Edildi – e-posta kullanıcının gelen kutusu veya klasörüne teslim edildi ve kullanıcı doğrudan buna erişebilirsiniz.
- **Gereksiz –** e-posta kullanıcının gereksiz klasörüne veya silinmiş klasörüne gönderilmiştir ve kullanıcının Gereksiz veya Silinmiş klasöründeki e-posta iletilerine erişimi olur.
- **Engellendi –** karantinaya alınan, başarısız olan veya bırakılan tüm e-posta iletileri.
- **Değiştirildi –** kötü amaçlı eklerin kötü amaçlı eklerin değiştir olduğu tüm e-.txt ekin kötü amaçlı olduğunu ifade ediyor olan dosyalarla değiştirilir.

Teslim konumu, teslim sonrası çalıştırmayı gösteren ilke ve algılamaların sonuçlarını gösterir. Bir Teslim Eylemine bağlıdır. Sorun posta bulunurken  alınan eylemle ilgili bilgi vermek için bu alan eklenmiştir. Teslim konumunun olası değerleri şöyledir:

- **Gelen kutusu veya** klasör – E-posta gelen kutusunda veya klasördedir (e-posta kurallarınıza göre).
- **Şirket içi veya dış** – Posta kutusu bulutta yoktur ama şirket içindedir.
- **Gereksiz klasörü** – E-posta kullanıcının Gereksiz E-posta klasöründedir.
- **Silinmiş öğeler klasörü** – E-posta kullanıcının Silinmiş öğeler klasöründedir.
- **Karantina** – Kullanıcının posta kutusunda değil, karantinada olan e-posta.
- **Başarısız** – E-posta posta posta kutusuna ulaşamadı.
- **Bırakılan** – E-posta, posta akışında bir yere kaybolur.

### <a name="view-the-timeline-of-your-email"></a>E-postanızı zaman çizelgenizi görüntüleme

**E-posta** Zaman Çizelgesi, Tehdit Gezgini'nde güvenlik işlemleri takımınız için daha kolay arama yapan bir alandır. E-postada birden çok olay aynı anda veya o anda olduğunda, bu olaylar zaman çizelgesi görünümünde görünür. E-postaya teslim sonrası yapılan bazı olaylar Özel eylemler **sütununda yakalanır** . E-posta iletisinin zaman çizelgesinden gelen bilgileri teslim sonrası için yapılan özel işlemlerle birleştirme, yöneticilere ilkeler ve tehdit işleme (örneğin, postanın nereye yönlendirildi ve bazı durumlarda son değerlendirmenin ne olduğu gibi) hakkında fikir verir.

> [!IMPORTANT]
> Burada bir düzeltme başlığına [atlayın](remediate-malicious-email-delivered-office-365.md).

## <a name="related-topics"></a>İlgili konular

[Office 365'te teslim edilen kötü amaçlı e-postaları düzeltme](remediate-malicious-email-delivered-office-365.md)

[Office 365 için Microsoft Defender](office-365-ti.md)

[Güvenlik tehditlerine karşı Office 365](protect-against-threats.md)

[Raporlar için raporları Office 365 için Defender](view-reports-for-mdo.md)
