---
title: Microsoft 365 ilkelerini ve
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
- admindeeplinkDEFENDER
description: Olası tehditleri, veri Microsoft 365 uyumluluk merkezi izin sorunlarını izlemek için Microsoft 365 Defender portalda veya Web portalında uyarı ilkeleri oluşturun.
ms.openlocfilehash: 9137c74cd2c32539a339a9cabc2d9f66f6923636
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/10/2022
ms.locfileid: "62974161"
---
# <a name="alert-policies-in-microsoft-365"></a>E-postada uyarı Microsoft 365

Microsoft 365 uyumluluk merkezi veya Microsoft 365 Defender portalında uyarı ilkelerini ve uyarı panosuyu kullanarak uyarı ilkeleri oluşturabilir ve ardından kullanıcılar bir uyarı ilkesi koşullarına uygun etkinlikler gerçekleştirecekken oluşturulan uyarıları görüntüleyebilirsiniz. Exchange Online'ta yönetici ayrıcalıkları atama, kötü amaçlı yazılım saldırıları, kimlik avı kampanyaları ve sıra dışı dosya silme ve dış paylaşım düzeyleri gibi etkinlikleri izlemenizi sağlar.

> [!TIP]
> Kullanılabilir uyarı [ilkelerinin listesi ve](#default-alert-policies) açıklaması için, bu makalenin Varsayılan uyarı ilkeleri bölümüne gidin.

Uyarı ilkeleri, bir ilke tarafından tetiklenen uyarıları kategorilere ayırmanıza, ilkeyi kuruluş tüm kullanıcılarınıza uygulamanıza, uyarının tetiklendiğinde bir eşik düzeyi ayarlamanıza ve uyarılar tetiklendiğinde e-posta bildirimlerinin alınıp alınmayacaklarına karar vermenizi sağlar. Ayrıca, bir De Uyarılar  sayfası vardır ve burada uyarıları görüntüleyebilirsiniz ve filtreleyebilirsiniz, uyarıları yönetmenize yardımcı olacak bir uyarı durumu ayarlayın ve temel olayı çözdükten veya çözdükten sonra uyarıları reddedin.

> [!NOTE]
> UYARı ilkeleri ABD Devlet E1/F1/G1, E3/F3/G3 veya E5/G5 aboneliği olan Microsoft 365 Kurumsal, Office 365 Kurumsal veya Office 365 olan kuruluşlar tarafından kullanılabilir. Gelişmiş işlevsellik yalnızca E5/G5 aboneliği olan kuruluşlarda ya da E1/F1/G1 veya E3/F3/G3 aboneliğine ve Office 365 P2 için Microsoft Defender ya da Microsoft 365 E5 Uyumluluk veya E5 eBulma ve Denetim eklenti aboneliğine sahip kuruluşlarda kullanılabilir. E5/G5 veya eklenti aboneliği gerektiren işlevler bu konuda vurgulanmıştır. Ayrıca, uyarı ilkelerinin en son Office 365 GCC, GCC dod ABD kamu ortamlarında da kullanılabilir olduğunu unutmayın.

## <a name="how-alert-policies-work"></a>Uyarı ilkeleri nasıl çalışır?

Burada, uyarı ilkelerinin nasıl çalışır ve kullanıcı veya yönetici etkinliği bir uyarı ilkesi koşullarıyla eşlendiğinde tetiklenen uyarı ilkelerinin nasıl tetiklenen genel bakış bilgilerine hızlı bir genel bakış sağlar.

![Uyarı ilkelerinin nasıl çalışmasına genel bakış.](../media/M365ComplianceDefender-AlertPolicies-Overview.png)

1. Kuruluş yöneticiniz, Microsoft 365 uyumluluk merkezi portalında Uyarı ilkeleri sayfasını kullanarak bir uyarı ilkesi oluşturur, yapılandırr ve Microsoft 365 Defender. Ayrıca, Güvenlik ve Uyumluluk Merkezi PowerShell'de [New-ProtectionAlert](/powershell/module/exchange/new-protectionalert) cmdlet'ini kullanarak & oluşturabilirsiniz.

   Uyarı ilkeleri oluşturmak için, ilgili kuruluşta veya Defender portalında Uyarıları Yönetme rolüne Microsoft 365 uyumluluk merkezi Kuruluş Yapılandırması rolüne atanmışsınız.

   > [!NOTE]
   > Uyarı ilkesi oluşturulması veya güncelleştirildikten sonra uyarıların ilke tarafından tetiklenmesi 24 saate kadar sürebilir. Bunun nedeni, ilkenin uyarı algılama altyapısıyla eşitlanması gerekir.

2. Kullanıcı, uyarı ilkesi koşullarına uygun bir etkinlik gerçekleştirir. Kötü amaçlı yazılım saldırılarında, organizasyonu kullanan kullanıcılara gönderilen virüs bulaşmış e-posta iletileri bir uyarıyı tetikler.

3. Microsoft 365, portalda veya Defender portalında **Uyarılar Microsoft 365 uyumluluk merkezi** bir uyarı üretir. Ayrıca, uyarı ilkesi için e-posta bildirimleri etkinleştirildiyse, Microsoft alıcı listesine bir bildirim gönderir. Yöneticinin veya diğer kullanıcıların Uyarılar sayfasında kullanıcıya atanan roller tarafından belirlen uyarılarını görebilirsiniz. Daha fazla bilgi için bkz. [Uyarıları görüntülemek için gereken RBAC izinleri](#rbac-permissions-required-to-view-alerts).

4. Bir yönetici, uyumluluk merkezinde uyarıları yönetir. Uyarıların yönetilmesi, herhangi bir soruşturmayı izley ve yönetmeye yardımcı olmak için uyarı durumu atamadan oluşur.

## <a name="alert-policy-settings"></a>Uyarı ilkesi ayarları

Uyarı ilkesi, bir uyarı oluşturan kullanıcı veya yönetici etkinliğini tanımlayan kurallar ve koşullar kümesiden, etkinliği gerçekleştirecekse uyarıyı tetikleyen kullanıcıların listesinden ve uyarının tetiklerden önce kaç kez etkinlik gerçekleşmesinin gerekli olduğunu tanımlayan bir eşiklerden oluşur. Ayrıca, ilkeyi kategorilere ayırarak önem düzeyi atersiniz. Bu iki ayar uyarı ilkelerini (ve ilke koşulları eşlendiğinde tetiklenen uyarıları) yönetmenize yardımcı olur, çünkü ilkeleri yönetirken ve uyumluluk merkezinde uyarıları görüntülerken bu ayarlara filtre uygulamanıza yardımcı olur. Örneğin, aynı kategorideki koşullarla eşleşmeye yönelik uyarıları veya aynı önem düzeyine sahip uyarıları görüntüabilirsiniz.

Uyarı ilkelerini görüntülemek ve oluşturmak için:

### <a name="microsoft-365-compliance-center"></a>Microsoft 365 uyumluluk merkezi

İlkeler'e <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a> **ardından** İlkelerAlert  > **İlkeleri'ne** >  gidin.

![Uyumluluk merkezinde İlkeler'i seçin ve uyarı ilkelerini görüntülemek ve oluşturmak için Uyarı ilkeleri'nin altında Uyarı ilkeleri'ne tıklayın.](../media/LaunchAlertPoliciesMCC.png)

### <a name="microsoft-365-defender-portal"></a>Microsoft 365 Defender portalı

Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalına gidin ve E-posta</a> ve **& altında** **İlkeler ve kurallarAlt &'ı** >  **seçin**. Alternatif olarak doğrudan 'a gidebilirsiniz <https://security.microsoft.com/alertpolicies>.

![Defender portalında, E-posta & altında İlkeler ve &'i seçin ve sonra uyarı ilkelerini görüntülemek ve oluşturmak için Uyarı ilkesi'ne tıklayın.](../media/LaunchAlertPoliciesDefenderPortal.png)

> [!NOTE]
> Uyumluluk merkezinde veya Defender portalında View-Only ilkelerini görüntülemek için, size Uyarı yönetme rolü atanmalıdır. Uyarı ilkeleri oluşturmak ve düzenlemek için Uyarıları Yönet rolüne atanmış olması gerekir. Daha fazla bilgi için bkz [. Güvenlik ve uyumluluk merkezinde izinler](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

Uyarı ilkesi aşağıdaki ayarlardan ve koşullardan oluşur.

- **Uyarının izleme etkinliği**. Bir etkinliği izlemek veya bazı durumlarda dosyayı bir dış kullanıcıyla paylaşmak, erişim izinleri atamak veya anonim bağlantı oluşturmak gibi birkaç ilgili etkinliği izlemek için bir ilke oluşturabilirsiniz. Kullanıcı ilke tarafından tanımlanan etkinliği gerçekleştir olduğunda, uyarı eşiği ayarlarına bağlı olarak bir uyarı tetiklenir.

    > [!NOTE]
    > Takip etmek için kullandığınız etkinlikler, kuruluş kuruluşlarının ABD Kamu Office 365 Kurumsal veya Office 365 bağlıdır. Genel olarak, kötü amaçlı yazılım kampanyaları ve kimlik avı saldırılarına ilişkin etkinlikler için E5/G5 aboneliği ya da Office 365 Plan 2 eklenti aboneliği için Defender ile E1/F1/G1 ya da [E3](../security/office-365-security/defender-for-office-365.md)/F3/G3 aboneliği gerekir.

- **Etkinlik koşulları**. Etkinliklerin çoğu için, uyarıyı tetiklemesi için karşı olması gereken ek koşullar tanımlayabilirsiniz. Yaygın koşullar IP adreslerini (böylelikle kullanıcı belirli bir IP adresine veya IP adresi aralığına sahip bir bilgisayarda etkinliği gerçekleştirdiği zaman uyarının tetiklenir), belirli bir kullanıcı veya kullanıcıların bu etkinliği gerçekleştirip gerçekleştirmesi ve etkinliğin belirli bir dosya adı veya URL'de gerçekleştirilip gerçekleştiril ip adresi olmadığını içerir. Ayrıca, kuruluşta herhangi bir kullanıcı tarafından etkinlik gerçekleştirıldığında uyarıyı tetikleyen bir koşul da yapılandırmış olursiniz. Kullanılabilir koşullar, seçili etkinliklere bağlıdır.

Ayrıca, kullanıcı etiketlerini uyarı ilkesi koşulu olarak da tanımlayabilirsiniz. Bu da, etkilenen kullanıcının bağlamını içermesi için ilke tarafından tetiklenen uyarılara neden olur. Sistem kullanıcı etiketlerini veya özel kullanıcı etiketlerini kullanabilirsiniz. Daha fazla bilgi için bkz[. Windows için Microsoft Defender'da Office 365](/microsoft-365/security/office-365-security/user-tags).

- **Uyarı tetiklendiğinde**. Bir uyarının tetik gelmeden önce ne sıklıkta etkinlik gerçekleşmesine neden olduğunu tanımlayan bir ayar yapılandırabilirsiniz. Bu, bir etkinlik ilke koşullarıyla her eşleşirse, belirli bir eşik aşılırken veya uyarının izlemede olduğu etkinlik, sizin için olağan dışı hale geldiğinde uyarı oluşturmak için bir ilke ayarlamanızı sağlar.

    ![Etkinliklerin ne zaman oluştuğuna, bir eşike veya kuruluş için olağan dışı bir etkinlike bağlı olarak uyarıların nasıl tetiklenir olduğunu yapılandırın.](../media/howalertsaretriggered.png)

    Bu ayarı alışılmış dışında bir etkinlik temel alarak seçtiyseniz, Microsoft seçilen etkinlik için normal sıklığı tanımlayan bir temel değeri ayarlar. Bu temelin kurulması yedi gün kadar sürer ve bu süre içinde uyarılar oluşturulmayacaktır. Temel alındıktan sonra, uyarı ilkesi tarafından izlenen etkinliğin sıklığı temel değeri önemli ölçüde aştıktan sonra bir uyarı tetiklenir. Denetimle ilgili etkinlikler için (dosya ve klasör etkinlikleri gibi), tek bir kullanıcıya dayalı olarak veya kuruluş tüm kullanıcıları temel alarak bir taban çizgisi kurabilirsiniz; kötü amaçlı yazılımla ilgili etkinlikler için, tek bir kötü amaçlı yazılım ailesi, tek bir alıcı veya kuruluşta tüm iletilere dayalı bir taban çizgisi kurabilirsiniz.

    > [!NOTE]
    > Uyarı ilkelerini bir eşiğe göre veya olağan dışı etkinliklere dayalı olarak yapılandırabilme özelliği için E5/G5 aboneliği ya da Office 365 P2, Microsoft 365 E5 Uyumluluk veya Microsoft 365 için Microsoft Defender ile E1/F1/G1 ya da E3/F3/G3 aboneliği gerekir. E1/F1/G1 ve E3/F3/G3 aboneliği olan kuruluşlar yalnızca her etkinlik oluştuğunda uyarının tetiklendiğinde uyarı ilkeleri oluşturabilir.

- **Uyarı kategorisi**. İlke tarafından oluşturulan uyarıların takibine ve yönetimine yardımcı olmak için, ilkeye aşağıdaki kategorilerden birini atabilirsiniz.

  - Veri kaybını önleme

  - Bilgi yönetimi

  - Posta akışı

  - İzinler

  - Tehdit yönetimi

  - Diğer

  Uyarı ilkesi koşullarına uygun bir etkinlik oluştuğunda, oluşturulan uyarı bu ayarda tanımlanan kategoriyle etiketlenir. Bu, uyarıları kategoriye göre sıralayma ve filtrelemeniz nedeniyle uyumluluk merkezinin Uyarılar  sayfasında aynı kategori ayarına sahip uyarıları izlemenizi ve yönetmenizi sağlar.

- **Önem derecesine dikkat.** Uyarı kategorisine benzer şekilde, uyarı ilkelerine önem düzeyi özniteliği (**Düşük**, **Orta**, **Yüksek** **veya Bilgili**) atarsiniz. Uyarı kategorisi gibi, uyarı ilkesi koşullarına uygun bir etkinlik oluştuğunda, oluşturulan uyarı, uyarı ilkesi için ayarlanmış olan önem düzeyiyle etiketlenir. Bu, Uyarılar sayfasında aynı önem düzeyi ayarına sahip uyarıları izlemenizi ve **yönetmenizi** sağlar. Örneğin, yalnızca Yüksek önem düzeyine sahip uyarıların görüntülenebilir olması **için uyarı listesini** filtreleebilirsiniz.

    > [!TIP]
    > Bir uyarı ilkesi ayarlarken, kullanıcılara teslim edildikten sonra kötü amaçlı yazılım algılaması, hassas veya sınıflandırılmış verileri görüntüleme, verileri dış kullanıcılarla paylaşma ya da veri kaybına veya güvenlik tehditlerine neden olacak diğer etkinlikler gibi ciddi negatif sonuçlar doğuracak etkinliklere yüksek önem düzeyi atamayı düşünebilirsiniz. Bu, temel alınan nedenleri araştırmak ve çözmek için gerçekleştirilen uyarıları ve eylemleri önceliklendirmenize yardımcı olabilir.

- **Otomatik soruşturmalar**. Bazı uyarılar, düzeltme veya risk azaltma gereken olası tehditleri ve riskleri tanımlamak için otomatik soruşturmalar tetikler.  Çoğu durumda bu uyarılar kötü amaçlı e-posta veya etkinliklerin algılanmasıyla tetiklenir, ancak bazı durumlarda bu uyarılar güvenlik portalında yönetici eylemleri tarafından tetiklenir.  Otomatik soruşturmalar hakkında daha fazla bilgi için bkz. Daha fazla bilgi için bkz. [Microsoft Defender'da otomatik soruşturma ve Office 365](../security/office-365-security/office-365-air.md).

- **E-posta bildirimleri**. Uyarı tetiklendiğinde kullanıcı listesine e-posta bildirimlerinin gönderilmesi (veya gönderilmeyilmesi) için ilkeyi kurabilirsiniz. Ayrıca, en fazla bildirim sayısına ulaşıldıktan sonra uyarı için o gün içinde daha fazla bildirim gönderilmeysin diye günlük bildirim sınırı da sabilirsiniz. Siz veya diğer yöneticiler, e-posta bildirimlerine ek olarak, Uyarılar sayfasında bir ilke tarafından tetiklenen **uyarıları da görebilirsiniz** . Belirli bir kategorinin uyarı ilkeleri veya önem düzeyi daha yüksek olan ilkeler için e-posta bildirimlerini etkinleştirmeyi göz önünde bulundurabilirsiniz.

## <a name="default-alert-policies"></a>Varsayılan uyarı ilkeleri

Microsoft; yönetici izinlerini kötüye kullanımı, kötü amaçlı yazılım etkinliğini, olası dış Exchange iç tehditlerini ve bilgi yönetimi risklerini belirlemeye yardımcı olan yerleşik uyarı ilkeleri sağlar. Uyarı **ilkeleri sayfasında** , bu yerleşik ilkelerin adları kalın yazıyla gösterilir ve ilke türü Sistem olarak **tanımlanır**. Bu ilkeler varsayılan olarak açıktır. Bu ilkeleri kapatabilirsiniz (veya yeniden açabilirsiniz), e-posta bildirimleri göndermek için alıcıların listesini ayarlayın ve günlük bildirim sınırı ayarlayın. Bu ilkelerin diğer ayarları düzenlenemez.

Aşağıdaki tabloda, kullanılabilir varsayılan uyarı ilkeleri ve her ilkenin atandığı kategori listelanmıştır ve açıklanmıştır. Kategori, kullanıcının Uyarılar sayfasında hangi uyarıları görüntüleyebilirsiniz olduğunu belirlemek için kullanılır. Daha fazla bilgi için bkz. [Uyarıları görüntülemek için gereken RBAC izinleri](#rbac-permissions-required-to-view-alerts).

Tabloda, her biri için Office 365 Kurumsal ve Office 365 planına nelerin gerekli olduğu da işaret ediyor. E1/F1/G1 veya E3/F3/G3 aboneliğine ek olarak, organizasyon uygun eklenti aboneliğine sahipse bazı varsayılan uyarı ilkeleri kullanılabilir.
 
| Varsayılan uyarı ilkesi | Açıklama | Kategori | Otomatik araştırma | Enterprise aboneliği |
|:-----|:-----|:-----|:-----|:-----|
|**Kötü amaçlı olabilecek bir URL tıklaması algılandı**|Bir kullanıcı, Kasa bağlantıları tarafından [kötü amaçlı bir](../security/office-365-security/safe-links.md) bağlantıya tıkladığında uyarı üretir. OFFICE 365 için Microsoft Defender tarafından URL karar değişiklikleri tanımlendiğinde veya kullanıcılar Kasa Bağlantıları sayfalarını geçersiz kıldında (kuruluş Microsoft 365 Bağlantıları ilkesine bağlı olarak) bu Kasa tetiklenir. Bu uyarı ilkesi yüksek önem **derecesine** sahip bir ayara sahip. Office 365 P2, E5 ve G5 müşterileri için Defender için bu uyarı otomatik olarak bu uyarı tüm müşteriler için otomatik olarak otomatik [Office 365](../security/office-365-security/office-365-air.md). Bu uyarıyı tetikleyen olaylar hakkında daha fazla bilgi için bkz. Bağlantı [Kasa ayarlama](../security/office-365-security/set-up-safe-links-policies.md).|Tehdit yönetimi|Evet|Office 365 P2 eklenti aboneliği için E5/G5 veya Defender|
|**Yönetici Gönderimi sonucu tamamlandı**|Bir Yönetici Gönderimi [gönderilen varlığın](../security/office-365-security/admin-submission.md) yeniden başvuru işlemini tamamlayana kadar bir uyarı üretir. Yönetici Gönderimi tarafından işlenen yeniden gönderme sonuçları her işlendiğinde uyarı tetiklenir. Bu uyarıların [amacı, önceki](https://compliance.microsoft.com/reportsubmission) gönderimlerin sonuçlarını gözden geçirmenizi, en son ilke denetimi almak ve kararları yeniden elde etmek için kullanıcıya bildirilen iletileri göndermenizi ve kuruluşta filtreleme ilkelerinin hedeflenen etkiyi elde etmek üzere olup olmadığını belirlemenize yardımcı olmaktır. Bu ilkenin Bilgilendirme **önem düzeyi** ayarı var.|Tehdit yönetimi|Hayır|E1/F1, E3/F3 veya E5|
|**Yönetici e-postanın el ile soruşturmasını tetikledi**|Yönetici, Threat Explorer'dan gelen bir e-postanın el ile soruşturmasını tetiklesin diye bir uyarı üretir. Daha fazla bilgi için bkz [. Örnek: Güvenlik yöneticisi Threat Explorer'dan gelen bir soruşturmayı tetikler](../security/office-365-security/automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer). Bu uyarı, araştırmanın başlatıldığı hakkında kuruluşa bilgi sağlar. Bu uyarı kimin tetikle ilgili bilgi sağladığını ve araştırmanın bağlantısını içerir. Bu ilkenin Bilgilendirme **önem düzeyi** ayarı vardır.|Tehdit yönetimi|Evet|Office 365 P2 eklenti aboneliği için E5/G5 veya Microsoft Defender|
|**Yönetici, kullanıcının güvenliği tehlikeye atarak araştırmayı tetikledi**|Yönetici, Tehdit Gezgini'nde e-postayı gönderen veya alıcının el ile güvenlik araştırmasını tetiklesin diye bir uyarı üretir. Daha fazla bilgi için bkz. Örnek: Güvenlik yöneticisi [Threat Explorer'dan](../security/office-365-security/automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) gelen ve bir e-posta üzerinde bir soruşturmayı el ile tetikleyen ilgili soruşturmayı tetikler. Bu uyarı, kuruluşa kullanıcı güvenliğiyle ilgili inceleme başlatıldığı konusunda bilgi sağlar. Bu uyarı kimin tetikle ilgili bilgi sağladığını ve araştırmanın bağlantısını içerir. Bu ilkenin Orta önem **düzeyi ayarı** var.|Tehdit yönetimi|Evet|Office 365 P2 eklenti aboneliği için E5/G5 veya Microsoft Defender|
|**Yönlendirme/yeniden yönlendirme kuralı oluşturma**|Organizasyonuzdan biri, iletileri başka bir e-posta hesabına iletir veya yeniden yönlendiren posta kutuları için bir gelen kutusu kuralı oluşturduğunda bir uyarı oluşturur. Bu ilke yalnızca Web üzerinde Outlook (eski adı Outlook Web App) veya PowerShell kullanılarak Exchange Online gelen kutusu kurallarını izler. Bu ilkenin Bilgilendirme **önem düzeyi** ayarı var. E-postayı başka bir hesapta yönlendirmek ve yönlendirmek üzere gelen kutusu kurallarını kullanma hakkında daha fazla bilgi için bkz. Web üzerinde Outlook e-postaları otomatik olarak başka bir hesaba Web üzerinde Outlook için [kuralları kullanma](https://support.office.com/article/1433e3a0-7fb0-4999-b536-50e05cb67fed).|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**eBulma araması başlatıldı veya dışarı aktarıldı**|Birisi Güvenlik ve uyumluluk merkezinde İçerik arama aracını kullandığında bir uyarı üretir. Aşağıdaki içerik arama etkinlikleri gerçekleştirlendiğinde uyarı tetiklenir: <br><br> <li> İçerik arama başlatıldı <li> İçerik arama sonuçları dışarı aktarıldı <li> İçerik arama raporu dışarı aktarıldı <br><br> Önceki içerik arama etkinlikleri bir eBulma durumuyla ilgili olarak gerçekleştirlendiğinde de uyarılar tetiklenir. Bu ilkenin Bilgilendirme **önem düzeyi** ayarı var. İçerik arama etkinlikleri hakkında daha fazla bilgi için bkz [. Denetim günlüğünde eBulma etkinliklerini arama](search-for-ediscovery-activities-in-the-audit-log.md#ediscovery-activities).|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Yönetici ayrıcalıklarını Exchange yükseltme**|Bir kişi, iş yer ibaresinde yönetici izinleri atandığı Exchange Online üretir. Örneğin, iş yerizsinde Kuruluş Yönetimi rol grubuna bir kullanıcı Exchange Online. Bu ilkenin düşük **önem düzeyi** ayarı var.|İzinler|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Teslimden sonra kötü amaçlı dosya içeren e-posta iletileri kaldırıldı**|Kötü amaçlı dosya içeren tüm iletiler kuruluş posta kutularına teslim edilirken bir uyarı üretir. Bu olay oluşursa, Microsoft Sıfır saatlik otomatik temizleme Exchange Online etkilenen iletileri ve posta [kutularından kaldırır](../security/office-365-security/zero-hour-auto-purge.md). Bu ilkenin Bir **Bilgi önem** düzeyi ayarı vardır ve bu ayar otomatik olarak, bilgi işlemsinde otomatik [soruşturmayı ve Office 365](../security/office-365-security/office-365-air.md). Bu yeni ilke hakkında daha fazla bilgi için bkz[. İlkeler için Microsoft Defender'da Office 365](new-defender-alert-policies.md).|Tehdit yönetimi|Evet|Office 365 P2 eklenti aboneliği için E5/G5 veya Microsoft Defender|
|**Teslimden sonra kötü amaçlı URL içeren e-posta iletileri kaldırıldı**|Kötü amaçlı URL içeren tüm iletiler, kuruluşta posta kutularına teslim edilirken bir uyarı üretir. Bu olay oluşursa, Microsoft Sıfır saatlik otomatik temizleme Exchange Online etkilenen iletileri ve posta [kutularından kaldırır](../security/office-365-security/zero-hour-auto-purge.md). Bu ilkenin Bir **Bilgi önem** düzeyi ayarı vardır ve bu ayar otomatik olarak, bilgi işlemsinde otomatik [soruşturmayı ve Office 365](../security/office-365-security/office-365-air.md). Bu yeni ilke hakkında daha fazla bilgi için bkz[. İlkeler için Microsoft Defender'da Office 365](new-defender-alert-policies.md).|Tehdit yönetimi|Evet|Office 365 P2 eklenti aboneliği için E5/G5 veya Defender|
|**Teslimden sonra kampanyadan e-posta iletileri kaldırıldı**|Bir Kampanya ile ilişkili tüm iletiler organizasyonuz [daki posta](../security/office-365-security/campaigns.md) kutularına teslim edilirken bir uyarı üretir. Bu olay oluşursa, Microsoft Sıfır saatlik otomatik temizleme Exchange Online etkilenen iletileri ve posta [kutularından kaldırır](../security/office-365-security/zero-hour-auto-purge.md). Bu ilkenin Bir **Bilgi önem** düzeyi ayarı vardır ve bu ayar otomatik olarak, bilgi işlemsinde otomatik [soruşturmayı ve Office 365](../security/office-365-security/office-365-air.md). Bu yeni ilke hakkında daha fazla bilgi için bkz[. İlkeler için Microsoft Defender'da Office 365](new-defender-alert-policies.md).|Tehdit yönetimi|Evet|Office 365 P2 eklenti aboneliği için E5/G5 veya Defender|
|**E-posta iletileri teslimden sonra kaldırıldı**|Kötü amaçlı varlık (URL veya Dosya) içermeen veya Kampanya ile ilişkilendirilmiş olan tüm kötü amaçlı iletiler, kuruluş posta kutularına teslim edilirken uyarı üretir. Bu olay oluşursa, Microsoft Sıfır saatlik otomatik temizleme Exchange Online etkilenen iletileri ve posta [kutularından kaldırır](../security/office-365-security/zero-hour-auto-purge.md). Bu ilkenin Bir **Bilgi önem** düzeyi ayarı vardır ve bu ayar otomatik olarak, bilgi işlemsinde otomatik [soruşturmayı ve Office 365](../security/office-365-security/office-365-air.md). Bu yeni ilke hakkında daha fazla bilgi için bkz[. İlkeler için Microsoft Defender'da Office 365](new-defender-alert-policies.md).|Tehdit yönetimi|Evet|Office 365 P2 eklenti aboneliği için E5/G5 veya Defender|
|**Kullanıcı tarafından kötü amaçlı yazılım veya kimlik avı olarak bildirilen e-posta**|Rapor İletisi eklentisinde, kuruluş kullanıcıları kimlik avı e-postası olarak ileti bildirsin diye bir uyarı üretir. Bu ilkenin Düşük **önem düzeyi** ayarı var. Bu eklenti hakkında daha fazla bilgi için bkz [. Rapor İletisi eklentiyi kullanma](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2). Office 365 P2, E5, G5 müşterileri için Defender için bu uyarı otomatik olarak bu uyarı tüm müşteriler için otomatik olarak otomatik [Office 365](../security/office-365-security/office-365-air.md).|Tehdit yönetimi|Evet|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**E-posta gönderme sınırı aşıldı**|Giden istenmeyen posta ilkesi, kurumdan biri izin verilenden daha fazla posta gönderdiğinde bir uyarı üretir. Bu genellikle kullanıcının çok fazla e-posta gönderdiğinin veya hesabın tehlikeye atılmış olduğunun göstergesidir. Bu ilkenin Orta önem **düzeyi ayarı** var. Bu uyarı ilkesi tarafından oluşturulan bir uyarıyla, kullanıcı hesabının tehlikeye atılmış olup olmadığını [denetlemeye devam etmek iyi bir fikirdir](../security/office-365-security/responding-to-a-compromised-email-account.md).|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Olası kimlik avı girişimi nedeniyle engellenen form**|Yinelenen kimlik avı girişimi algılandığından, kuruluşta biri form paylaşmaya ve Microsoft Forms kullanarak yanıt toplamaya kısıtlandığında bir uyarı oluşturur. Bu ilkenin önem **düzeyi yüksek bir ayar** var.|Tehdit yönetimi|Hayır|E1, E3/F3 veya E5|
|**Kimlik avı olarak bayrakla işaretlenen ve onaylenen form**|Microsoft Forms'da kurum içinden oluşturulan bir form, Kötüye Kullanımı Bildir aracılığıyla olası kimlik avı olarak tanımlandıktan ve Microsoft tarafından kimlik avı olarak onaylandıktan sonra bir uyarı oluşturur. Bu ilkenin önem **düzeyi yüksek bir** ayar var.|Tehdit yönetimi|Hayır|E1, E3/F3 veya E5|
|**İletiler gecikmiş**|Microsoft, bağlayıcı kullanarak şirket içi bir kuruluşa veya iş ortağı sunucusuna e-posta iletileri teslim e-postası alama geldiğinde bir uyarı verir. Böyle bir durumda, ileti başka bir Office 365. Bir saatten uzun süre sıraya alınan 2.000 ileti veya daha fazla olduğunda bu uyarı tetiklenir. Bu ilkenin önem **düzeyi yüksek bir** ayar var.|Posta akışı|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Teslimden sonra algılanan kötü amaçlı yazılım kampanyası**|Kötü amaçlı yazılım içeren sıra dışı sayıda ileti, kuruluş posta kutularına teslim edilirse bir uyarı oluşturur. Bu olay oluşursa, Microsoft bulaşarak etkilenen iletileri Exchange Online kaldırır. Bu ilkenin önem **düzeyi yüksek bir** ayar var.|Tehdit yönetimi|Hayır|Office 365 P2 eklenti aboneliği için E5/G5 veya Microsoft Defender|
|**Kötü amaçlı yazılım kampanyası algılandı ve engellendi**|Birisi, belirli türde bir kötü amaçlı yazılım içeren olağan dışı sayıda e-posta iletilerini, organizasyon daki kullanıcılara göndermeyi denerek bir uyarı oluşturur. Bu olay oluşursa, virüsü bulaşmış iletiler Microsoft tarafından engellenir ve posta kutularına teslim edilir. Bu ilkenin düşük **önem düzeyi** ayarı var.|Tehdit yönetimi|Hayır|Office 365 P2 eklenti aboneliği için E5/G5 veya Defender|
|**SharePoint ve OneDrive'de kötü amaçlı yazılım OneDrive**|SharePoint sitelerinde veya OneDrive hesaplarında yer alan dosyalarda olağan dışı yüksek bir kötü amaçlı yazılım veya virüs miktarı algılandığında uyarı oluşturur. Bu ilkenin önem **düzeyi yüksek bir** ayar var.|Tehdit yönetimi|Hayır|Office 365 P2 eklenti aboneliği için E5/G5 veya Defender|
|**ZAP devre dışı bırakılı olduğundan kötü amaçlı yazılım eşlenmemiş**| Kimlik Avı iletileri için Otomatik Temizleme özelliği devre dışı bırakılamaz olduğundan, Microsoft bir kötü amaçlı yazılım iletisi posta kutusuna teslim Zero-Hour bir uyarı oluşturur. Bu ilkenin Bilgilendirme **önem düzeyi** ayarı vardır. |Tehdit yönetimi|Hayır|Office 365 P2 eklenti aboneliği için E5/G5 veya Defender|
|**Kullanıcının Gereksiz Posta klasörü devre dışı bırakılmıştır, çünkü kimlik avı teslim edildi**|Microsoft bir kullanıcının Gereksiz Posta klasörünün devre dışı bırak bırak olmadığını algılasa bir uyarı oluşturur ve bu uyarı bir posta kutusuna yüksek güvenli kimlik avı iletisinin teslimi sağlar. Bu ilkenin Bilgilendirme **önem düzeyi** ayarı vardır.|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**EtR geçersiz kılma nedeniyle teslim edilen kimlik avı**|Microsoft, posta kutusuna yüksek güveni olan bir kimlik avı iletisi teslimine izin verilen bir Aktarım Kuralı (ETR) Exchange bir uyarı üretir. Bu ilkenin Bilgilendirme **önem düzeyi** ayarı vardır. Aktarım Kuralları(Posta Exchange kuralları) hakkında daha fazla bilgi için, bu konuda bilgi için bkz. Posta akış [kuralları (Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Kimlik avı, IP izin verme ilkesi nedeniyle teslim edildi**|Microsoft, yüksek güveni olan kimlik avı iletisi posta kutusuna teslimine izin verilen bir IP izin ilkesi algılayana kadar bir uyarı üretir. Bu ilkenin Bilgilendirme **önem düzeyi** ayarı vardır. IP izin verme ilkesi (bağlantı filtreleme) hakkında daha fazla bilgi için bkz. Varsayılan [bağlantı filtresi ilkesi yapılandırma - Office 365](../security/office-365-security/configure-the-connection-filter-policy.md).|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**ZAP devre dışı bırakıldı diye kimlik avı eşlenmemiş**| Kimlik avı iletileri için Otomatik Temizleme özelliği devre dışı bırakılmıştır, çünkü Zero-Hour Microsoft bir posta kutusuna yüksek güvene sahip bir kimlik avı iletisi teslimi algılarsa bir uyarı verir. Bu ilkenin Bilgilendirme **önem düzeyi** ayarı vardır.|Tehdit yönetimi|Hayır|Office 365 P2 eklenti aboneliği için E5/G5 veya Defender|
|**Kiracı veya kullanıcı geçersiz kılma nedeniyle teslim edilen kimlik avı1**<sup></sup>|Microsoft bir yönetici veya kullanıcının kimlik avı iletisine teslimine izin verilen yöneticiyi veya kullanıcının geçersiz k olduğunu algılayana kadar bir uyarı üretir. Geçersiz kılma örnekleri, belirli bir gönderenden veya etki alanındaki iletilere izin veren gelen kutusu veya posta akışı kuralı ya da belirli gönderenlerden veya etki alanlarından gelen iletilere izin veren istenmeyen posta önleme ilkesi içerir. Bu ilkenin önem **düzeyi yüksek bir** ayar var.|Tehdit yönetimi|Hayır|Office 365 P2 eklenti aboneliği için E5/G5 veya Defender|
|**Şüpheli e-posta iletme etkinliği**|Organizasyonlu bir kişi e-postayı şüpheli bir dış hesaba otomatik olarak iletirken bir uyarı üretir. Bu, hesabın güvenliği ihlal edilmiş olduğu, ancak kullanıcının kısıtlanmaları için yeterince ciddi olmadığını belirten erken bir uyarıdır. Bu ilkenin önem **düzeyi yüksek bir** ayar var. Nadiren de olsa, bu ilke tarafından oluşturulan bir uyarı anormal olabilir. Kullanıcı hesabının güvenliği ihlal edilmiş [olup olmadığını denetlemek iyi bir fikirdir](../security/office-365-security/responding-to-a-compromised-email-account.md).|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Algılanan şüpheli e-posta gönderme desenleri**|Organizasyonlu bir kişi şüpheli e-posta gönderdiğinde ve e-posta göndermesi kısıtlanmışsa bir uyarı üretir. Bu, hesabın ihlal edilmiş olduğunu, ancak kullanıcının kısıtlanmaları için yeterince ciddi olmadığını belirten erken bir uyarıdır. Bu ilkenin Orta önem **düzeyi ayarı** var. Nadiren de olsa, bu ilke tarafından oluşturulan bir uyarı anormal olabilir. Bununla birlikte, kullanıcı hesabının güvenliği ihlal [edilmiş olup olmadığını denetlemeyi de göz atabilirsiniz](../security/office-365-security/responding-to-a-compromised-email-account.md).|Tehdit yönetimi|Evet|E1/F1/G1, E3/F3/G3 veya E5/G5  |
|**Kiracı İzin Ver/Listeyi Engelle girdinin süresi dolmak üzere**|Kiracı İzin Ver/Engelleme Listesi girdisi kaldırılacak olduğunda bir uyarı üretir. Bu olay, girişin ne zaman oluşturulduğunda veya son güncelleştirmede temel alınan sona erme tarihinden üç gün önce tetiklenir. Bu uyarı ilkesi bir Bilgilendirme **önem düzeyi** ayarına sahip. Bunun yolu, izin verme veya engellemenin neden olması nedeniyle filtrelerde yapılacak değişikliklerle ilgili yöneticileri bilgilendirmektir. Bloklar için, bloğun yerinde tutulacak şekilde sona erme tarihini uzatın. Olanaklar için, analistlerimizin başka bir görünüme göz atlarını için öğeyi yeniden geri edelirsiniz. Bununla birlikte, izin verme önceden hatalı pozitif sonuç olarak notlandısa, girdinin süresi yalnızca sistem filtreleri girdiye doğal bir şekilde izin verecek şekilde güncelleştirildiğinde geçerli olur. Bu uyarıyı tetikleyen olaylar hakkında daha fazla bilgi için bkz [. Kiracı İzin Ver/Engelle listesini yönetme](../security/office-365-security/tenant-allow-block-list.md).|Tehdit yönetimi|Hayır|Office 365 P2 eklenti aboneliği için E5/G5 veya Defender|
|**Kiracı e-posta göndererek kısıtlandı**|Kuruluştan gelen e-posta trafiğinin çoğu şüpheli olarak algılandığında ve Microsoft bu trafiğin e-posta göndermesi için kısıtlandığında bir uyarı üretir. Güvenliği ihlal edilmiş olabilecek kullanıcı ve yönetici hesaplarını, yeni bağlayıcıları veya açık geçişleri araştırnın ve sonra Microsoft Desteği'ne başvurarak kuruluş engelini kaldırabilirsiniz. Bu ilkenin önem **düzeyi yüksek bir** ayar var. Kuruluşların neden engellenmiş olduğu hakkında daha fazla bilgi için bkz. Hata kodu [5.7.7xx](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-7-700-through-5-7-750) için e-posta teslim Exchange Online.|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Kiracı, unprovisioned e-posta göndererek kısıtlandı**|Kaydı olmayan etki alanlarından (unprovisioned etki alanları olarak da bilinir) çok fazla e-posta gönder *istendiği zaman bir uyarı* üretir. Office 365, kaydı olmayan etki alanlarından makul miktarda e-postaya izin verir, ancak e-postayı kabul edilen etki alanı olarak göndermek için kullanıyorsanız her etki alanını yapılandırmanız gerekir. Bu uyarı, kuruluşta olan tüm kullanıcıların artık e-posta göndereylene olmadığını gösterir. Bu ilkenin önem **düzeyi yüksek bir** ayar var. Kuruluşların neden engellenmiş olduğu hakkında daha fazla bilgi için bkz. Hata kodu [5.7.7xx](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-7-700-through-5-7-750) için e-posta teslim Exchange Online.|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Alışılmış dışı dış kullanıcı dosyası etkinliği**|Kuruluş dışından kullanıcılar tarafından dosyalarda olağan dışı sayıda etkinlik SharePoint veya OneDrive için uyarı üretir. Bu, dosyalara erişme, dosyaları indirme ve dosyaları silme gibi etkinlikleri içerir. Bu ilkenin önem **düzeyi yüksek bir** ayar var.|Bilgi yönetimi|Hayır|E5/G5, Office 365 P2 için Microsoft Defender veya Microsoft 365 E5 aboneliği|
|**Olağan dışı dış dosya paylaşımı hacmi**|Kuruluş veya posta dosyalarında olağan dışı sayıda dosya SharePoint OneDrive dışından kullanıcılarla paylaşılırken uyarı üretir. Bu ilkenin Orta önem **düzeyi ayarı** var.|Bilgi yönetimi|Hayır|E5/G5, Office 365 P2 için Defender veya Microsoft 365 E5 aboneliği için|
|**Olağan dışı dosya silme hacmi**|Zaman içinde veya kısa bir zaman diliminde olağan dışı sayıda dosya SharePoint OneDrive bir uyarı üretir. Bu ilkenin Orta önem **düzeyi ayarı** var.|Bilgi yönetimi|Hayır|E5/G5, Office 365 P2 için Defender veya Microsoft 365 E5 aboneliği için|
|**Kimlik avı olarak bildirilen e-postada olağan dışı artış**|İletileri kimlik avı postası olarak rapor etmek için Outlook'daki Rapor İletisi eklentiini kullanarak kuruluşta kişi sayısında önemli bir artış olduğunda uyarı üretir. Bu ilkenin Orta önem **düzeyi ayarı** var. Bu eklenti hakkında daha fazla bilgi için bkz [. Rapor İletisi eklentiyi kullanma](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2).|Tehdit yönetimi|Hayır|Office 365 P2 eklenti aboneliği için E5/G5 veya Defender|
|**Gelen kutusu/klasör1,2'ye teslim edilen kullanıcı** <sup>kimliğine bürünme kimlik</sup> <sup>avı</sup>|Microsoft bir yöneticinin veya kullanıcının geçersiz kılarak bir kullanıcının kimliğe bürünme kimlik avı iletisi teslimine posta kutusunun gelen kutusuna (veya başka bir kullanıcı erişilebilir klasöre) teslimine izin olduğunu algılar ve bir uyarı oluşturur. Geçersiz kılma örnekleri, belirli bir gönderenden veya etki alanındaki iletilere izin veren gelen kutusu veya posta akışı kuralı ya da belirli gönderenlerden veya etki alanlarından gelen iletilere izin veren istenmeyen posta önleme ilkesi içerir. Bu ilkenin Orta önem **düzeyi ayarı** var.|Tehdit yönetimi|Hayır|Office 365 P2 eklenti aboneliği için E5/G5 veya Defender|
|**Kullanıcı karantinaya alınmış iletiyi serbest bırakmak için istekte bulundu**|Kullanıcı karantinaya alınmış bir ileti için sürüm isteğinda bulundurarak bir uyarı üretir. Karantinaya alınmış iletilerin serbest bırak alınmasını talep etmek için, alıcıların karantinadan çıkarılmazken istekte olmasına izin **verme (**_PermissionToRequestRelease_) izni karantina ilkesinde gerekir (örneğin, Sınırlı erişim için önceden  ayarlanmış izinler grubundan). Daha fazla bilgi için bkz [. Alıcıların iletiyi karantina izninden serbest bırakmasına izin verme](../security/office-365-security/quarantine-policies.md#allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission). Bu ilkenin Bilgilendirme **önem düzeyi** ayarı vardır.|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Kullanıcının e-posta göndermesi kısıtlandı**|Kuruluşta birinin giden posta göndermesi kısıtlanmışsa, bir uyarı üretir. Bu durum normalde bir hesabın güvenliği ihlal edilmiş ve kullanıcı profilinde **Kısıtlanmış Kullanıcılar** sayfasında Microsoft 365 uyumluluk merkezi. (Bu sayfaya erişmek için Tehdit yönetimi ve **Kısıtlanmış > Gözden >'e gidin**). Bu ilkenin önem **düzeyi yüksek bir** ayar var. Kısıtlanmış kullanıcılar hakkında daha fazla bilgi için bkz. İstenmeyen posta gönderen bir kullanıcı, etki alanı veya [IP adresini engellenenler listesinden kaldırma](/office365/securitycompliance/removing-user-from-restricted-users-portal-after-spam).|Tehdit yönetimi|Evet|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Kullanıcı formları paylaşma ve yanıtları toplama kısıtlaması**|Yinelenen kimlik avı girişimi algılandığından, kuruluşta biri form paylaşmaya ve Microsoft Forms kullanarak yanıt toplamaya kısıtlandığında bir uyarı oluşturur. Bu ilkenin önem **düzeyi yüksek bir** ayar var.|Tehdit yönetimi|Hayır|E1, E3/F3 veya E5|

> [!NOTE]
> <sup>1</sup> Müşteri geri bildirimlerine bağlı olarak bu varsayılan uyarı ilkesi geçici olarak kaldırıldı. Geliştirmek için çalışıyoruz ve yakın gelecekte bu sürümü yeni bir sürümle değiştireceğiz. O zamana kadar, aşağıdaki ayarları kullanarak bu işlevselliği değiştirmek için özel bir uyarı ilkesi oluşturabilirsiniz: <ul><li>Etkinlik, kimlik avı e-postası teslim sırasında algılandı</li> <li>Posta ZAP'd değil</li> <li>Posta yönü Gelen yönü</li> <li>Posta teslim durumu Teslim Edildi</li> <li>Algılama teknolojisi Kötü amaçlı URL bekletme, URL'yi temizleme, Gelişmiş kimlik avı filtresi, Genel kimlik avı filtresi, Etki alanı kimliğine bürünme, Kullanıcı kimliğine bürünme ve Marka kimliğe bürünme teknolojileridir</li></ul> E-postada kimlik avı önleme hakkında daha fazla Office 365 için bkz. Kimlik avı önleme ve [kimlik avı önleme ilkelerini ayarlama](../security/office-365-security/set-up-anti-phishing-policies.md).<br/><br/><sup>2</sup> Bu uyarı ilkesi yeniden oluşturmak için önceki dipnotta yer alan yönergeleri izleyin, ancak yalnızca Algılama teknolojisi olarak Kullanıcı kimliğine bürünme'yi seçin.

Yerleşik ilkelerin bazılarında izlenen sıra dışı etkinlik, daha önce açıklanan uyarı eşiği ayarıyla aynı işleme dayalıdır. Microsoft, "normal" etkinlik için normal sıklığı tanımlayan bir temel değeri sağlar. Yerleşik uyarı ilkesi tarafından izlenen etkinliklerin sıklığı temel değerin çok fazla üzerine geldiğinde uyarılar tetiklenir.

<a name="viewing-alerts"></a>

## <a name="view-alerts"></a>Uyarıları görüntüleme

Kuruluşta kullanıcılar tarafından gerçekleştirilen bir etkinlik bir uyarı ilkesi ayarlarıyla eşlendiğinde, uyumluluk merkezinde veya Defender portalında Uyarılar sayfasında bir uyarı oluşturulur ve  görüntülenir. Uyarı ilkesi ayarlarına bağlı olarak, bir uyarı tetiklendiğinde belirtilen kullanıcılar listesine de e-posta bildirimi gönderilir. Her uyarı için, Uyarılar sayfasındaki pano  ilgili uyarı ilkesi adını, uyarının önem derecesini ve kategorisini (uyarı ilkesinde tanımlanmıştır) ve uyarının oluşturularak ortaya çıkan etkinlik sayısını görüntüler. Bu değer, uyarı ilkesi eşik ayarına göredir. Pano her uyarının durumunu da gösterir. Uyarıları yönetmek için durum özelliğini kullanma hakkında daha fazla bilgi için bkz [. Uyarıları yönetme](#manage-alerts).

Uyarıları görüntülemek için:

### <a name="microsoft-365-compliance-center"></a>Microsoft 365 uyumluluk merkezi

 Uyarılar'a <https://compliance.microsoft.com> gidin **ve bu seçeneği seçin**. Alternatif olarak doğrudan 'a gidebilirsiniz <https://compliance.microsoft.com/compliancealerts>.

![Daha fazla Microsoft 365 uyumluluk merkezi'ı seçin.](../media/ViewAlertsMCC.png)

### <a name="microsoft-365-defender-portal"></a>Microsoft 365 Defender portalı

Güvenlik <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalına Microsoft 365 Defender ve</a> sonra **Uyarılarda Olay** **&'ı** >  seçin. Alternatif olarak doğrudan 'a gidebilirsiniz <https://security.microsoft.com/alerts>.

![Microsoft 365 Defender portalında Olaylar ve uyarılar& ardından Uyarılar'ı seçin.](../media/ViewAlertsDefenderPortal.png)

Aşağıdaki filtreleri kullanarak, Uyarılar sayfasındaki tüm uyarıların bir alt kümesini **görüntüleyebilirsiniz** .

- **Durum'a .** Belirli bir durum atanmış uyarıları göstermek için bu filtreyi kullanın. Varsayılan durum **Etkin'tir**. Siz veya diğer yöneticiler durum değerini değiştirebilirsiniz.

- **İlke.** Bir veya birden çok uyarı ilkelerinin ayarına uygun uyarıları göstermek için bu filtreyi kullanın. Ya da tüm uyarı ilkeleri için tüm uyarıları görüntüye hazır olun.

- **Zaman aralığı.** Belirli bir tarih ve saat aralığında oluşturulan uyarıları göstermek için bu filtreyi kullanın.

- **Önem Derecesi.** Belirli bir önem düzeyi atanmış uyarıları göstermek için bu filtreyi kullanın.

- **Kategori.** Bir veya birden çok uyarı kategorisindeki uyarıları göstermek için bu filtreyi kullanın.

- **Etiketler.** Bir veya birden çok kullanıcı etiketinden gelen uyarıları göstermek için bu filtreyi kullanın. Etiketler, uyarılarda görünen etiketli posta kutularına veya kullanıcılara göre yansıtılmaktadır. Daha [fazla bilgi için bkz. Office 356 ATP'de](../security/office-365-security/user-tags.md) kullanıcı etiketleri.

- **Kaynak.** Uyumluluk merkezinde uyarı ilkeleri tarafından tetiklenen uyarıları veya güvenlik ilkeleri ya da her ikisini birden Office 365 Bulut Uygulamaları Güvenliği için bu filtreyi kullanın. Bu uyarıları görüntüleme hakkında Office 365 Bulut Uygulamaları Güvenliği için bkz. [Bulut Uygulamaları için Defender Uyarılarını Görüntüleme](#viewing-cloud-app-security-alerts).

> [!IMPORTANT]
> Kullanıcı etiketlerine göre filtreleme ve sıralama şu anda genel önizlemede.
> Ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir. Microsoft, bu konuda sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

## <a name="alert-aggregation"></a>Uyarı toplaması

Kısa bir süreyle uyarı ilkesi koşullarına uygun birden çok olay gerçekleşirken, bunlar uyarı toplama adı verilen bir işlem tarafından var olan *uyarıya eklenir*. Bir olay bir uyarıyı tetikle olduğunda, uyarı oluşturulur, Uyarılar **sayfasında görüntülenir** ve bir bildirim gönderilir. Aynı olay toplama aralığı içinde gerçekleşirse, Microsoft 365 yeni uyarıyı tetiklemek yerine var olan uyarıya yeni olayla ilgili ayrıntıları ekler. Uyarı toplamanın amacı, uyarıyı "yorgunluğu" azaltmaya yardımcı olmak ve aynı olay için daha az uyarıya odaklanmak ve önlem almaktır.

Toplama aralığının uzunluğu Office 365 veya Microsoft 365 bağlıdır.

|Abonelik|Toplama aralığı|
|:---------|:---------:|
|Office 365 veya Microsoft 365 E5/G5|1 dakika|
|Office 365 için Defender Plan 2 |1 dakika|
|E5 Uyumluluk eklentisi veya E5 Bulma ve Denetim eklentisi|1 dakika|
|Office 365 veya Microsoft 365 E1/F1/G1 veya E3/F3/G3|15 dakika|
|Plan 1 Office 365 için Defender Exchange Online Protection|15 dakika|

Aynı uyarı ilkesine sahip olaylar toplama aralığı içinde gerçekleşirken, izleyen olayla ilgili ayrıntılar özgün uyarıya eklenir. Tüm olaylar için, toplanan olaylar hakkında bilgiler ayrıntılar alanında ve toplama aralığıyla bir olayın kaç kez etkinlik/isabet sayısı alanında görüntüleniyor. Etkinlik listesini görüntüerek, tüm toplanan olay örnekleri hakkında daha fazla bilgi görüntüebilirsiniz.

Aşağıdaki ekran görüntüsünde birleştirilmiş dört olayla birlikte bir uyarı görebilirsiniz. Etkinlik listesi, uyarıyla ilgili dört e-posta iletileri hakkında bilgi içerir.

![Uyarı toplama örneği.](../media/AggregatedAlertExample.png)

Uyarı toplaması hakkında aşağıdaki bilgileri unutmayın:

- Kötü amaçlı olabilecek **URL tıklaması tarafından tetiklenen uyarılar varsayılan** [uyarı ilkesi algılanmadı](#default-alert-policies) . Bunun nedeni, bu ilke tarafından tetiklenen uyarıların her kullanıcı ve e-posta iletisi için benzersiz olmasıdır.

- Şu anda, **Sayı sayısı** uyarı özelliği tüm uyarı ilkeleri için toplanan olayların sayısını gösteriyor. Bu uyarı ilkeleri tarafından tetiklenen uyarılar için, toplanan olayları görüntülemek için uyarıda İleti listesini görüntüle'ye **veya Etkinliği** **görüntüle'ye** tıklayın. Sayı uyarı özelliğinde listelenen toplanan etkinliklerin sayısını tüm uyarı ilkeleri için kullanılabilir hale  toplamak için çalışıyoruz.

## <a name="rbac-permissions-required-to-view-alerts"></a>Uyarıları görüntülemek için RBAC izinleri gerekir

Bir kullanıcının Uyarılar sayfasında hangi uyarıları göreceğini, kuruluşta kullanıcılara atanmış olan Rol Tabanlı Erişim Denetimi (RBAC) **izinleri** belirler. Bunu nasıl başarırsınız? Kullanıcılara atanan yönetim rolleri (Microsoft 365 uyumluluk merkezi veya Microsoft 365 Defender portalında rol gruplarında yaptıkları üyeliklere göre), kullanıcının Uyarılar sayfasında hangi uyarı kategorilerini **göreceğini** belirler. İşte birkaç örnek:

- Kayıt Yönetimi rol grubunun üyeleri yalnızca Bilgi yönetimi kategorisine atanan uyarı ilkeleri tarafından oluşturulan **uyarıları** bakabilir.

- Uyumluluk Yöneticisi rol grubunun üyeleri, Tehdit yönetimi kategorisine atanan uyarı ilkeleri tarafından oluşturulan **uyarıları görüntüleyemmektedir** .

- eBulma Yöneticisi rol grubunun üyeleri, atanan rollerden hiçbiri herhangi bir uyarı kategorisindeki uyarıları görüntüleme izni sağlamadığı için herhangi bir uyarıyı görüntüleyemmektedir.

Bu tasarım (RBAC izinlerine dayalı olarak), kullanıcılar tarafından organizasyonda belirli iş rollerinde hangi uyarıların görüntülenbibini (ve yönetil uyarılarını) belirlemenize olanak sağlar.

Aşağıdaki tabloda, altı farklı uyarı kategorisindeki uyarıları görüntülemek için gereken roller listelemektedir. Tablodaki ilk sütunda, tablodaki veya Microsoft 365 uyumluluk merkezi tüm Microsoft 365 Defender.  Onay işareti, bu rolün atandığı kullanıcının en üst satırda listelenen ilgili uyarı kategorisindeki uyarıları görüntüley olduğunu gösterir.

Varsayılan uyarı ilkesine hangi kategorinin atandığı görmek için Varsayılan uyarı [ilkeleri'nin tabloyu görüntüleyin](#default-alert-policies).

|Rol|Bilgi yönetimi|Veri kaybını önleme|Posta akışı|İzinler|Tehdit yönetimi|Diğer|
|:---------|:---------:|:---------:|:---------:|:---------:|:---------:|:---------:|
|Denetim Günlükleri|||||||
|Vaka Yönetimi|||||||
|Uyumluluk Yöneticisi|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)||![Onay işareti.](../media/checkmark.png)||![Onay işareti.](../media/checkmark.png)|
|Uyumluluk Araması|||||||
|Cihaz Yönetimi|||||||
|Disposition Management|||||||
|DLP Uyumluluk Yönetimi||![Onay işareti.](../media/checkmark.png)|||||
|Dışarı aktarma|||||||
|Bekle|||||||
|Bilgi Koruma Analisti||![Onay işareti.](../media/checkmark.png)|||||
|Bilgi Koruma Koruma Koruma Koruması||![Onay işareti.](../media/checkmark.png)|||||
|Uyarıları Yönetme||||||![Onay işareti.](../media/checkmark.png)|
|Kuruluş Yapılandırması||||||![Onay işareti.](../media/checkmark.png)|
|Önizleme|||||||
|Kayıt Yönetimi|![Onay işareti.](../media/checkmark.png)||||||
|Bekletme Yönetimi|![Onay işareti.](../media/checkmark.png)||||||
|Gözden Geçir|||||||
|RMS Şifre Çözme|||||||
|Rol Yönetimi||||![Onay işareti.](../media/checkmark.png)|||
|Arama ve Temizleme|||||||
|Güvenlik Yöneticisi||![Onay işareti.](../media/checkmark.png)||![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|
|Güvenlik Okuyucu||![Onay işareti.](../media/checkmark.png)||![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)
|Hizmet Güvencesi Görünümü|||||||
|Gözetmen İnceleme Yöneticisi|||||||
|View-Only Günlüklerini Denetleme|||||||
|View-Only Yönetimi'ne bakın|||||||
|View-Only DLP Uyumluluk Yönetimi||![Onay işareti.](../media/checkmark.png)|||||
|View-Only Yönetme||||||![Onay işareti](../media/checkmark.png)|
|View-Only Alıcılar'a|||![Onay işareti](../media/checkmark.png)||||
|View-Only Kaydı Yönetimi|![Onay işareti](../media/checkmark.png)||||||
|View-Only Bekletme Yönetimi|![Onay işareti](../media/checkmark.png)||||||

> [!TIP]
> Varsayılan rol gruplarının her bir role atanmış olan rolleri görüntülemek için Güvenlik ve Uyumluluk Merkezi PowerShell'de & çalıştırın:
>
> ```powershell
> $RoleGroups = Get-RoleGroup
> ```
>
> ```powershell
> $RoleGroups | foreach {Write-Output -InputObject `r`n,$_.Name,"-----------------------"; Get-RoleGroup $_.Identity | Select-Object -ExpandProperty Roles}
> ```
>
> Ayrıca, üst portalda veya portalda, bir rol Microsoft 365 uyumluluk merkezi atanmış Microsoft 365 Defender görüntüebilirsiniz. İzinler **sayfasına** gidin ve bir rol grubu seçin. Atanan roller, uç uç sayfada listelenir.

<a name="manage-alerts"></a>

## <a name="manage-alerts"></a>Uyarıları yönetme

Uyarılar oluşturularak uyumluluk merkezinin Uyarılar sayfasında görüntülendikten sonra, uyarıların öncesini çözümleyebilirsiniz, bunları inceleyebilirsiniz. Kullanıcılara [uyarılara erişim](#rbac-permissions-required-to-view-alerts) izniyle aynı RBAC izinleri, kullanıcılara uyarıları yönetme olanağı da sağlar.

Uyarıları yönetmek için gerçekleştirebilirsiniz.

- **Uyarılar için durum atama.** Uyarılar için aşağıdaki durumlardan birini attaysanız **: Etkin** (varsayılan **değer),** Araştırılıyor, **Çözümlendi** veya **Yok.** Ardından, aynı durum ayarına sahip uyarıları görüntülemek için bu ayara göre filtre abilirsiniz. Bu durum ayarı uyarıları yönetme sürecini takip etmeye yardımcı olabilir.

- **Uyarı ayrıntılarını görüntüleme.** Uyarıyla ilgili ayrıntıların yer almalı bir çıkış sayfası görüntülemek için bir uyarı seçin. Ayrıntılı bilgiler ilgili uyarı ilkesine bağlı olarak değişir, ancak genellikle şunları içerir:

  - Uyarıyı tetikleyen cmdlet veya denetim günlüğü işlemi gibi gerçek işlem adı.

  - Uyarıyı tetikleyen etkinliğin açıklaması.

  - Uyarıyı tetikleyen kullanıcı (veya kullanıcı listesi). Bu yalnızca, tek bir kullanıcı veya tek bir etkinliği izlemek için ayarlanmış uyarı ilkelerine dahildir.

  - Uyarı tarafından etkinlik izleme sayısı. Bu sayı, Uyarılar sayfasında listelenen ilgili uyarıların gerçek sayısıyla eşleşmeyebilirsiniz, çünkü daha fazla uyarı tetiklenmiş olabilir.

  - Uyarıyı tetikleyen, gerçekleştirilen her etkinlik için bir öğe içeren etkinlik listesinin bağlantısı. Bu listede yer alan her girdi, etkinlik gerçekleştirilen etkinliğin adını (örneğin "FileDeleted"), etkinliği gerçekleştiren kullanıcıyı, etkinliğin gerçekleştirdiğini nesne (dosya, eBulma durumu veya posta kutusu gibi) ve kullanıcının bilgisayarının IP adresini tanımlar. Kötü amaçlı yazılımla ilgili uyarılar için, bu bağlantılar bir ileti listesinedir.

  - İlgili uyarı ilkesi adı (ve bağlantısı).

- **E-posta bildirimlerini gizleme.** Uyarı için, uç sayfadan e-posta bildirimlerini kapatabilir (veya gizlemeyi) sebilirsiniz. E-posta bildirimlerini gizlemeyseniz, uyarı ilkesi koşullarına uygun etkinlikler veya olaylar gerçekleşirken Microsoft bildirim göndermez. Ancak, kullanıcılar tarafından gerçekleştirilen etkinlikler uyarı ilkesi koşullarına uygun olduğunda uyarılar tetiklenir. Ayrıca, uyarı ilkesi düzenleyerek e-posta bildirimlerini kapatabilirsiniz.

- **Uyarıları giderin.** Bir uyarının uç sayfada çözümlenmiş olarak işaretleyebilirsiniz (bu, uyarının durumunu Çözümlendi olarak **ayarlar**). Filtreyi değiştirmedikçe çözülen uyarılar Uyarılar **sayfasında görüntülenmez** .

<a name="viewing-cloud-app-security-alerts"></a>

## <a name="view-defender-for-cloud-apps-alerts"></a>Bulut Uygulamaları için Defender'ı Görüntüle uyarıları

İlkeler ve Office 365 Bulut Uygulamaları Güvenliği tarafından tetiklenen uyarılar artık uyumluluk **merkezinin** Uyarılar sayfasında görüntülenir. Bu, etkinlik ilkeleri tarafından tetiklenen uyarıları ve Office 365 Bulut Uygulamaları Güvenliği'de anormal algılama ilkeleri tarafından tetiklenen uyarıları içerir. Bu, tüm uyarıları uyumluluk merkezinde görüntüleyy görüntüleyy görüntüleyy görüntüleyy i Office 365 Bulut Uygulamaları Güvenliği yalnızca ABD Government G5 aboneliği Office 365 Kurumsal veya Office 365 kuruluşlar tarafından kullanılabilir. Daha fazla bilgi için bkz [. Bulut Uygulamaları için Defender'a Genel Bakış](/cloud-app-security/what-is-cloud-app-security).

Enterprise Mobility + Security E5 aboneliğinin bir parçası olarak ya da tek başına bir hizmet olarak Bulut Uygulamaları için Microsoft Defender'a sahip olan kuruluşlar, aynı zamanda Microsoft 365'ta yer alan Microsoft 365 uygulamaları ve hizmetleriyle ilgili Bulut Uygulamaları için Defender uyarılarını da Microsoft 365 uyumluluk merkezi Microsoft 365 Defender portalında oturum açın.

Uyumluluk merkezinde veya Defender portalında yalnızca Bulut Uygulamaları için Defender uyarılarını görüntülemek için Kaynak filtresini **kullanın ve Bulut** Uygulamaları için **Defender'ı seçin**.

![Yalnızca Bulut Uygulamaları için Defender uyarılarını görüntülemek için Kaynak filtresini kullanın.](../media/FilterCASAlerts.png)

Uyumluluk merkezinde uyarı ilkesi tarafından tetiklenen uyarıya benzer şekilde, bir Bulut Uygulamaları için Defender uyarısı seçerek uyarıyla ilgili ayrıntıların yer alan bir çıkış sayfası görüntüleyebilirsiniz. Uyarı, Bulut Uygulamaları için Defender portalında ayrıntıları görüntülemek ve uyarıyı yönetmek için bir bağlantı ve uyarıyı tetikleyen ilgili Bulut Uygulamaları için Defender ilkesine bağlantı içerir. Bulut [Uygulamaları için Defender'da Uyarıları izleme'ye bakın](/cloud-app-security/monitor-alerts).

![Uyarı ayrıntıları, Bulut Uygulamaları için Defender portalının bağlantılarını içerir.](../media/CASAlertDetail.png)

> [!IMPORTANT]
> Uyumluluk merkezinde Bulut Uygulamaları için Defender uyarısının durumunu değiştirmek, Bulut Uygulamaları için Defender portalında aynı uyarının çözüm durumunu güncelleştirmez. Örneğin, uyarının durumunu uyumluluk merkezinde Çözümlendi olarak işaretlenirse, Bulut Uygulamaları için Defender portalında uyarının durumu değişmez. Bulut Uygulamaları için Defender uyarısını çözmek veya yoksay etmek için, Bulut Uygulamaları için Defender portalında uyarıyı yönetin.
