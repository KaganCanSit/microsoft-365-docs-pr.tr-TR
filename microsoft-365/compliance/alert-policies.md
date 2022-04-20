---
title: uyarı ilkelerini Microsoft 365
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
description: Olası tehditleri, veri kaybını ve izin sorunlarını izlemek için Microsoft Purview uyumluluk portalında veya Microsoft 365 Defender portalında uyarı ilkeleri oluşturun.
ms.openlocfilehash: ad7099ddcbc99fd6cf852b1bb7f564c0caf444a7
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944271"
---
# <a name="alert-policies-in-microsoft-365"></a>Microsoft 365 uyarı ilkeleri

Uyarı ilkelerini ve uyarı panosunu Microsoft Purview uyumluluk portalında veya Microsoft 365 Defender portalında kullanarak uyarı ilkeleri oluşturabilir ve kullanıcılar uyarı ilkesinin koşullarıyla eşleşen etkinlikler gerçekleştirdiğinde oluşturulan uyarıları görüntüleyebilirsiniz. Exchange Online yönetici ayrıcalıkları atama, kötü amaçlı yazılım saldırıları, kimlik avı kampanyaları ve olağan dışı dosya silme ve dış paylaşım düzeyleri gibi etkinlikleri izlemenize yardımcı olan çeşitli varsayılan uyarı ilkeleri vardır.

> [!TIP]
> Kullanılabilir [uyarı ilkelerinin](#default-alert-policies) listesi ve açıklaması için bu makaledeki Varsayılan uyarı ilkeleri bölümüne gidin.

Uyarı ilkeleri, bir ilke tarafından tetiklenen uyarıları kategorilere ayırmanıza, ilkeyi kuruluşunuzdaki tüm kullanıcılara uygulamanıza, bir uyarının tetiklenmesi için bir eşik düzeyi ayarlamanıza ve uyarılar tetiklendiğinde e-posta bildirimleri alıp almamaya karar vermenize olanak sağlar. Ayrıca uyarıları görüntüleyip filtreleyebileceğiniz, uyarıları yönetmenize yardımcı olacak bir uyarı durumu ayarlayabileceğiniz ve temel olayı ele aldıktan veya çözümledikten sonra uyarıları kapatabileceğiniz bir **Uyarılar** sayfası da vardır.

> [!NOTE]
> Uyarı ilkeleri ABD Kamu E1/F1/G1, E3/F3/G3 veya E5/G5 aboneliğine sahip Microsoft 365 Kurumsal, Office 365 Kurumsal veya Office 365 kuruluşlar için kullanılabilir. Gelişmiş işlevler yalnızca E5/G5 aboneliği olan kuruluşlarda ya da E1/F1/G1 veya E3/F3/G3 aboneliğine sahip kuruluşlarda ve Office 365 için Microsoft Defender P2 veya Microsoft 365 E5 Uyumluluk ya da E5 eBulma ve Denetim eklentisi aboneliğine sahip kuruluşlar için kullanılabilir. E5/G5 veya eklenti aboneliği gerektiren işlevler bu konuda vurgulanır. Uyarı ilkelerinin Office 365 GCC, yüksek GCC ve DoD ABD kamu ortamlarında kullanılabildiğini de unutmayın.

## <a name="how-alert-policies-work"></a>Uyarı ilkeleri nasıl çalışır?

Aşağıda, uyarı ilkelerinin nasıl çalıştığına ve kullanıcı veya yönetici etkinliği uyarı ilkesinin koşullarıyla eşleştiğinde tetikleyen uyarılara hızlı bir genel bakış verilmiştir.

![Uyarı ilkelerinin çalışma şekline genel bakış.](../media/M365ComplianceDefender-AlertPolicies-Overview.png)

1. Kuruluşunuzdaki bir yönetici, uyumluluk portalındaki veya Microsoft 365 Defender portalındaki Uyarı ilkeleri sayfasını kullanarak bir **uyarı ilkesi** oluşturur, yapılandırıp açar. Güvenlik & Uyumluluk Merkezi PowerShell'deki [New-ProtectionAlert](/powershell/module/exchange/new-protectionalert) cmdlet'ini kullanarak da uyarı ilkeleri oluşturabilirsiniz.

   Uyarı ilkeleri oluşturmak için uyumluluk portalında veya Defender portalında Uyarıları Yönet rolüne veya Kuruluş Yapılandırması rolüne atanmış olmanız gerekir.

   > [!NOTE]
   > Uyarıların ilke tarafından tetiklenebilmesi için bir uyarı ilkesi oluşturulduktan veya güncelleştirildikten sonra 24 saat kadar sürer. Bunun nedeni, ilkenin uyarı algılama altyapısıyla eşitlenmesi gerekir.

2. Kullanıcı, uyarı ilkesinin koşullarıyla eşleşen bir etkinlik gerçekleştirir. Kötü amaçlı yazılım saldırıları söz konusu olduğunda, kuruluşunuzdaki kullanıcılara gönderilen virüslü e-posta iletileri bir uyarı tetikler.

3. Microsoft 365, uyumluluk portalındaki veya Defender portalındaki **Uyarılar** sayfasında görüntülenen bir uyarı oluşturur. Ayrıca, uyarı ilkesi için e-posta bildirimleri etkinleştirildiyse, Microsoft alıcı listesine bir bildirim gönderir. Bir yöneticinin veya diğer kullanıcıların Uyarılar sayfasında görebileceği uyarılar, kullanıcıya atanan roller tarafından belirlenir. Daha fazla bilgi için bkz. [Uyarıları görüntülemek için gereken RBAC izinleri](#rbac-permissions-required-to-view-alerts).

4. Yönetici, uyumluluk merkezinde uyarıları yönetir. Uyarıları yönetmek, herhangi bir araştırmayı izlemeye ve yönetmeye yardımcı olmak için bir uyarı durumu atamaktan oluşur.

## <a name="alert-policy-settings"></a>Uyarı ilkesi ayarları

Uyarı ilkesi, uyarı oluşturan kullanıcı veya yönetici etkinliğini tanımlayan bir dizi kural ve koşuldan, etkinliği gerçekleştirdiklerinde uyarıyı tetikleyen kullanıcıların listesinden ve bir uyarı tetiklenmeden önce etkinliğin kaç kez gerçekleştirildiğini tanımlayan bir eşikten oluşur. Ayrıca ilkeyi kategorilere ayırıp bir önem düzeyi atarsınız. Bu iki ayar, uyumluluk merkezinde ilkeleri yönetirken ve uyarıları görüntülerken bu ayarları filtreleyebileceğinizden, uyarı ilkelerini (ve ilke koşulları eşleştiğinde tetiklenen uyarıları) yönetmenize yardımcı olur. Örneğin, aynı kategorideki koşullarla eşleşen uyarıları görüntüleyebilir veya aynı önem düzeyine sahip uyarıları görüntüleyebilirsiniz.

Uyarı ilkelerini görüntülemek ve oluşturmak için:

### <a name="microsoft-purview-compliance-portal"></a>Microsoft Purview uyumluluk portalı

<a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Uyumluluk portalına</a> gidin ve **İlkelerAlertAlert** >  >  **ilkeleri'ni** seçin.

![Uyumluluk merkezinde İlkeler'i seçin ve Uyarı'nın altında Uyarı ilkeleri'ni seçerek uyarı ilkelerini görüntüleyin ve oluşturun.](../media/LaunchAlertPoliciesMCC.png)

### <a name="microsoft-365-defender-portal"></a>Microsoft 365 Defender portalı

<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalına</a> gidin ve **E-posta & işbirliği** bölümünde **İlkeler & kurallarAlert** >  **ilkesi'ni** seçin. Alternatif olarak doğrudan adresine <https://security.microsoft.com/alertpolicies>gidebilirsiniz.

![Defender portalında, E-posta & işbirliği altında İlkeler & kuralları'nı seçin ve ardından uyarı ilkelerini görüntülemek ve oluşturmak için Uyarı ilkesi'ni seçin.](../media/LaunchAlertPoliciesDefenderPortal.png)

> [!NOTE]
> Uyumluluk merkezinde veya Defender portalında uyarı ilkelerini görüntülemek için View-Only Uyarıları Yönet rolüne atanmış olmanız gerekir. Uyarı ilkeleri oluşturmak ve düzenlemek için Uyarıları Yönet rolüne atanmış olmanız gerekir. Daha fazla bilgi için bkz. [Güvenlik ve uyumluluk merkezindeki izinler](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

Uyarı ilkesi aşağıdaki ayarlardan ve koşullardan oluşur.

- **Uyarının izlediği etkinlik**. Bir etkinliği izlemek için bir ilke oluşturursunuz veya bazı durumlarda bir dosyayı paylaşarak, erişim izinleri atayarak veya anonim bağlantı oluşturarak bir dosyayı dış kullanıcıyla paylaşma gibi birkaç ilgili etkinlik oluşturursunuz. Kullanıcı ilke tarafından tanımlanan etkinliği gerçekleştirdiğinde, uyarı eşiği ayarlarına göre bir uyarı tetikler.

    > [!NOTE]
    > İzleyebileceğiniz etkinlikler, kuruluşunuzun Office 365 Kurumsal veya OFFICE 365 ABD Kamu planına bağlıdır. Genel olarak kötü amaçlı yazılım kampanyaları ve kimlik avı saldırıları ile ilgili etkinlikler için E5/G5 aboneliği veya [Office 365 için Defender Plan 2](../security/office-365-security/defender-for-office-365.md) eklenti aboneliğine sahip bir E1/F1/G1 veya E3/F3/G3 aboneliği gerekir.

- **Etkinlik koşulları**. Çoğu etkinlik için, uyarı tetikleme amacıyla karşılanması gereken ek koşullar tanımlayabilirsiniz. Yaygın koşullar IP adreslerini (kullanıcı etkinliği belirli bir IP adresine sahip bir bilgisayarda veya IP adresi aralığı içinde gerçekleştirdiğinde bir uyarının tetiklenebilmesi için), belirli bir kullanıcı veya kullanıcı bu etkinliği gerçekleştirirse uyarının tetiklenip tetiklenmediğini ve etkinliğin belirli bir dosya adında veya URL'de gerçekleştirilip gerçekleştirilmediğini içerir. Etkinlik kuruluşunuzdaki herhangi bir kullanıcı tarafından gerçekleştirildiğinde uyarı tetikleyen bir koşul da yapılandırabilirsiniz. Kullanılabilir koşullar seçili etkinliğe bağlıdır.

Kullanıcı etiketlerini uyarı ilkesinin koşulu olarak da tanımlayabilirsiniz. Bu, etkilenen kullanıcının bağlamını dahil etmek için ilke tarafından tetiklenen uyarılarla sonuçlanır. Sistem kullanıcı etiketlerini veya özel kullanıcı etiketlerini kullanabilirsiniz. Daha fazla bilgi için bkz. [Office 365 için Microsoft Defender'de kullanıcı etiketleri](/microsoft-365/security/office-365-security/user-tags).

- **Uyarı tetiklendiğinde**. Bir uyarı tetiklenmeden önce etkinliğin ne sıklıkta gerçekleşebileceğini tanımlayan bir ayar yapılandırabilirsiniz. Bu, bir etkinliğin ilke koşullarıyla her eşleştiğinde, belirli bir eşiğin aşıldığında veya uyarının izlediği etkinliğin oluşması kuruluşunuz için olağan dışı hale geldiğinde uyarı oluşturmak için bir ilke ayarlamanıza olanak tanır.

    ![Etkinliğin ne zaman gerçekleştiğine, bir eşik veya kuruluşunuz için olağan dışı etkinliğe bağlı olarak uyarıların nasıl tetiklenmesini yapılandırabilirsiniz.](../media/howalertsaretriggered.png)

    Olağan dışı etkinliğe göre ayarı seçerseniz, Microsoft seçilen etkinlik için normal sıklığı tanımlayan bir temel değer oluşturur. Bu temelin oluşturulması yedi güne kadar sürer ve bu süre boyunca uyarılar oluşturulmaz. Temel oluşturulduktan sonra, uyarı ilkesi tarafından izlenen etkinliğin sıklığı temel değeri büyük ölçüde aştığında bir uyarı tetiklenir. Denetimle ilgili etkinlikler (dosya ve klasör etkinlikleri gibi) için, tek bir kullanıcıyı veya kuruluşunuzdaki tüm kullanıcıları temel alan bir temel oluşturabilirsiniz; kötü amaçlı yazılımla ilgili etkinlikler için tek bir kötü amaçlı yazılım ailesini, tek bir alıcıyı veya kuruluşunuzdaki tüm iletileri temel alan bir temel oluşturabilirsiniz.

    > [!NOTE]
    > Uyarı ilkelerini bir eşiğe veya olağan dışı etkinliklere göre yapılandırabilmek için E5/G5 aboneliği ya da Office 365 için Microsoft Defender P2, Microsoft 365 E5 Uyumluluk veya Microsoft 365 eBulma ve Denetim eklentisine sahip bir E1/F1/G1 veya E3/F3/G3 aboneliği gerekir Abonelik. E1/F1/G1 ve E3/F3/G3 aboneliğine sahip kuruluşlar, yalnızca bir etkinlik gerçekleştiğinde bir uyarının tetiklendiği uyarı ilkeleri oluşturabilir.

- **Uyarı kategorisi**. İlke tarafından oluşturulan uyarıları izleme ve yönetme konusunda yardımcı olmak için bir ilkeye aşağıdaki kategorilerden birini atayabilirsiniz.

  - Veri kaybı önleme

  - Bilgi Yönetişimi

  - Posta akışı

  - İzinler

  - Tehdit yönetimi

  - Diğer

  Uyarı ilkesinin koşullarıyla eşleşen bir etkinlik gerçekleştiğinde, oluşturulan uyarı bu ayarda tanımlanan kategoriyle etiketlenmiş olur. Bu, uyumluluk merkezindeki **Uyarılar** sayfasında aynı kategori ayarına sahip uyarıları izlemenize ve yönetmenize olanak tanır çünkü uyarıları kategoriye göre sıralayabilir ve filtreleyebilirsiniz.

- **Uyarı önem derecesi**. Uyarı kategorisine benzer şekilde, uyarı ilkelerine bir önem derecesi özniteliği (**Düşük**, **Orta**, **Yüksek** veya **Bilgilendirici**) atarsınız. Uyarı kategorisi gibi, uyarı ilkesinin koşullarıyla eşleşen bir etkinlik gerçekleştiğinde, oluşturulan uyarı uyarı ilkesi için ayarlanan önem düzeyiyle etiketlenmiş olur. Bu da **Uyarılar sayfasında aynı** önem derecesine sahip uyarıları izlemenize ve yönetmenize olanak tanır. Örneğin, uyarı listesini filtreleyerek yalnızca **Yüksek** önem derecesine sahip uyarıların görüntülenmesini sağlayabilirsiniz.

    > [!TIP]
    > Uyarı ilkesi ayarlarken, kullanıcılara teslim sonrasında kötü amaçlı yazılım algılama, hassas veya sınıflandırılmış verileri görüntüleme, dış kullanıcılarla veri paylaşma veya veri kaybına veya güvenlik tehditlerine yol açabilecek diğer etkinlikler gibi ciddi olumsuz sonuçlara neden olabilecek etkinliklere daha yüksek önem derecesi atamayı göz önünde bulundurun. Bu, uyarıların ve temel nedenlerin araştırılması ve çözümlenmesi için gerçekleştirdiğiniz eylemlerin önceliklerini belirlemenize yardımcı olabilir.

- **Otomatik araştırma.** Bazı uyarılar, düzeltme veya azaltma gerektiren olası tehditleri ve riskleri belirlemek için otomatik araştırmalara neden olur.  Çoğu durumda bu uyarılar kötü amaçlı e-postaların veya etkinliklerin algılanmasıyla tetiklenir, ancak bazı durumlarda uyarılar güvenlik portalındaki yönetici eylemleri tarafından tetiklenir.  Otomatik araştırmalarla ilgili daha fazla bilgi için bkz. [Office 365 için Microsoft Defender'de otomatik araştırma ve yanıt (AIR).](../security/office-365-security/office-365-air.md)

- **E-posta bildirimleri**. İlkeyi, uyarı tetiklendiğinde e-posta bildirimlerinin bir kullanıcı listesine gönderilmesini (veya gönderilmemesi) için ayarlayabilirsiniz. Ayrıca, en fazla bildirim sayısına ulaşıldığında o gün boyunca uyarı için başka bildirim gönderilmemesi için günlük bildirim sınırı da ayarlayabilirsiniz. E-posta bildirimlerine ek olarak, siz veya diğer yöneticiler **Uyarılar sayfasında bir** ilke tarafından tetiklenen uyarıları görüntüleyebilirsiniz. Belirli bir kategorinin veya daha yüksek önem derecesine sahip uyarı ilkeleri için e-posta bildirimlerini etkinleştirmeyi göz önünde bulundurun.

## <a name="default-alert-policies"></a>Varsayılan uyarı ilkeleri

Microsoft, Exchange yönetici izinlerinin kötüye kullanımı, kötü amaçlı yazılım etkinliği, olası dış ve iç tehditler ile bilgi idaresi risklerinin belirlenmesine yardımcı olan yerleşik uyarı ilkeleri sağlar. **Uyarı ilkeleri** sayfasında, bu yerleşik ilkelerin adları kalın yazı tipindedir ve ilke türü **Sistem** olarak tanımlanır. Bu ilkeler varsayılan olarak açıktır. Bu ilkeleri kapatabilir (veya yeniden açabilir), e-posta bildirimleri gönderecek alıcıların listesini ayarlayabilir ve günlük bildirim sınırı ayarlayabilirsiniz. Bu ilkelerin diğer ayarları düzenlenemez.

Aşağıdaki tabloda, kullanılabilir varsayılan uyarı ilkeleri ve her ilkenin atandığı kategori listelenip açıklanmaktadır. Kategori, kullanıcının Uyarılar sayfasında hangi uyarıları görüntüleyebileceğini belirlemek için kullanılır. Daha fazla bilgi için bkz. [Uyarıları görüntülemek için gereken RBAC izinleri](#rbac-permissions-required-to-view-alerts).

Tabloda ayrıca her biri için gereken Office 365 Kurumsal ve Office 365 ABD Kamu planı da gösterilir. Kuruluşunuzun E1/F1/G1 veya E3/F3/G3 aboneliğine ek olarak uygun eklenti aboneliği varsa bazı varsayılan uyarı ilkeleri kullanılabilir.
 
| Varsayılan uyarı ilkesi | Açıklama | Kategori | Otomatik araştırma | aboneliği Enterprise |
|:-----|:-----|:-----|:-----|:-----|
|**Kötü amaçlı olabilecek bir URL tıklaması algılandı**|Kuruluşunuzdaki [Kasa Bağlantıları](../security/office-365-security/safe-links.md) tarafından korunan bir kullanıcı kötü amaçlı bir bağlantıya tıkladığında bir uyarı oluşturur. URL karar değişiklikleri Office 365 için Microsoft Defender tarafından tanımlandığında veya kullanıcılar Kasa Bağlantıları sayfalarını geçersiz kıldığında (kuruluşunuzun Microsoft 365 iş Kasa Bağlantıları ilkesine bağlı olarak) bu olay tetiklenir. Bu uyarı ilkesinin **Yüksek** önem derecesi ayarı vardır. Office 365 için Defender P2, E5, G5 müşterileri için bu uyarı otomatik [araştırmayı ve yanıtı otomatik olarak Office 365](../security/office-365-security/office-365-air.md) tetikler. Bu uyarıyı tetikleyen olaylar hakkında daha fazla bilgi için bkz. [Kasa Bağlantıları ilkelerini ayarlama](../security/office-365-security/set-up-safe-links-policies.md).|Tehdit yönetimi|Evet|E5/G5 veya Office 365 için Defender P2 eklenti aboneliği|
|**Yönetici Gönderimi sonucu tamamlandı**|[Yönetici Gönderimi](../security/office-365-security/admin-submission.md) gönderilen varlığın yeniden taramasını tamamladığında bir uyarı oluşturur. Bir Yönetici Gönderiminden her yeniden tarama sonucu işlendiğinde bir uyarı tetiklenir. Bu uyarılar [, önceki gönderimlerin sonuçlarını gözden geçirmenizi](https://compliance.microsoft.com/reportsubmission), en son ilke denetimini almak ve kararları yeniden taramak için kullanıcı tarafından bildirilen iletileri göndermenizi ve kuruluşunuzdaki filtreleme ilkelerinin hedeflenen etkiyi sağlayıp sağlamadığını belirlemenize yardımcı olmayı anımsatmak için tasarlanmıştır. Bu ilkenin **Bilgi önem** derecesi ayarı vardır.|Tehdit yönetimi|Hayır|E1/F1, E3/F3 veya E5|
|**Yönetici tarafından tetiklenen el ile e-posta araştırması**|Bir yönetici Tehdit Gezgini'nden bir e-postanın el ile araştırmasını tetiklediğinde bir uyarı oluşturur. Daha fazla bilgi için bkz [. Örnek: Güvenlik yöneticisi Tehdit Gezgini'nden bir araştırma tetikler](../security/office-365-security/automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer). Bu uyarı, kuruluşunuza araştırmanın başlatıldığını bildirir. Uyarı, bu uyarıyı kimin tetiklediği hakkında bilgi sağlar ve araştırmanın bağlantısını içerir. Bu ilkenin **Bilgilendirici** önem derecesi ayarı vardır.|Tehdit yönetimi|Evet|E5/G5 veya Office 365 için Microsoft Defender P2 eklenti aboneliği|
|**Yönetici tarafından tetiklenen kullanıcı güvenliği aşım araştırması**|Yönetici, Tehdit Gezgini'nden bir e-posta göndereni veya alıcısını el ile ele geçirerek kullanıcı güvenliğini aşma araştırmasını tetiklediğinde bir uyarı oluşturur. Daha fazla bilgi için bkz [. Örnek: Güvenlik yöneticisi Tehdit Gezgini'nden bir araştırmayı tetikler](../security/office-365-security/automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer). Bu, e-postada bir araştırmanın ilgili el ile tetiklenmesi işlemini gösterir. Bu uyarı, kuruluşunuza kullanıcı güvenliğini aşma araştırmasının başlatıldığını bildirir. Uyarı, bu uyarıyı kimin tetiklediği hakkında bilgi sağlar ve araştırmanın bağlantısını içerir. Bu ilkenin **Orta** önem derecesi ayarı vardır.|Tehdit yönetimi|Evet|E5/G5 veya Office 365 için Microsoft Defender P2 eklenti aboneliği|
|**İletme/yeniden yönlendirme kuralı oluşturma**|Kuruluşunuzdaki bir kişi, posta kutusu için iletileri başka bir e-posta hesabına yönlendiren veya yeniden yönlendiren bir gelen kutusu kuralı oluşturduğunda bir uyarı oluşturur. Bu ilke yalnızca Web üzerinde Outlook (eski adıyla Outlook Web App) veya PowerShell Exchange Online kullanılarak oluşturulan gelen kutusu kurallarını izler. Bu ilkenin **Bilgi önem** derecesi ayarı vardır. Web üzerinde Outlook'da e-postayı iletmek ve yeniden yönlendirmek için gelen kutusu kurallarını kullanma hakkında daha fazla bilgi için bkz. [İletileri otomatik olarak başka bir hesaba iletmek için Web üzerinde Outlook kuralları kullanma](https://support.office.com/article/1433e3a0-7fb0-4999-b536-50e05cb67fed).|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**eBulma araması başlatıldı veya dışarı aktarıldı**|Birisi Güvenlik ve uyumluluk merkezindeki İçerik arama aracını kullandığında bir uyarı oluşturur. Aşağıdaki içerik arama etkinlikleri gerçekleştirildiğinde bir uyarı tetiklenir: <br><br> <li> İçerik araması başlatıldı <li> İçerik aramasının sonuçları dışarı aktarılır <li> İçerik arama raporu dışarı aktarıldı <br><br> Uyarılar, önceki içerik arama etkinlikleri bir eBulma olayıyla ilişkili olarak gerçekleştirildiğinde de tetiklenir. Bu ilkenin **Bilgi önem** derecesi ayarı vardır. İçerik arama etkinlikleri hakkında daha fazla bilgi için bkz. [Denetim günlüğünde eBulma etkinliklerini](search-for-ediscovery-activities-in-the-audit-log.md#ediscovery-activities) arama.|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Exchange yönetici ayrıcalığının yükseltilmesi**|Exchange Online kuruluşunuzda birine yönetici izinleri atandığında bir uyarı oluşturur. Örneğin, bir kullanıcı Exchange Online'daki Kuruluş Yönetimi rol grubuna eklendiğinde. Bu ilke **düşük önem** derecesine sahiptir.|İzinler|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Kötü amaçlı dosya içeren e-posta iletileri teslimden sonra kaldırıldı**|Kötü amaçlı bir dosya içeren iletiler kuruluşunuzdaki posta kutularına teslim edildiğinde bir uyarı oluşturur. Bu olay oluşursa, Microsoft [sıfır saatlik otomatik temizlemeyi](../security/office-365-security/zero-hour-auto-purge.md) kullanarak virüslü iletileri Exchange Online posta kutularından kaldırır. Bu ilke bir **Bilgilendirici** önem derecesi ayarına sahiptir ve [Office 365 otomatik araştırma ve yanıtı](../security/office-365-security/office-365-air.md) otomatik olarak tetikler. Bu yeni ilke hakkında daha fazla bilgi için bkz. [Office 365 için Microsoft Defender'de yeni uyarı ilkeleri](new-defender-alert-policies.md).|Tehdit yönetimi|Evet|E5/G5 veya Office 365 için Microsoft Defender P2 eklenti aboneliği|
|**Kötü amaçlı URL içeren e-posta iletileri teslimden sonra kaldırıldı**|Kötü amaçlı URL içeren iletiler kuruluşunuzdaki posta kutularına teslim edildiğinde bir uyarı oluşturur. Bu olay oluşursa, Microsoft [sıfır saatlik otomatik temizlemeyi](../security/office-365-security/zero-hour-auto-purge.md) kullanarak virüslü iletileri Exchange Online posta kutularından kaldırır. Bu ilke bir **Bilgilendirici** önem derecesi ayarına sahiptir ve [Office 365 otomatik araştırma ve yanıtı](../security/office-365-security/office-365-air.md) otomatik olarak tetikler. Bu yeni ilke hakkında daha fazla bilgi için bkz. [Office 365 için Microsoft Defender'de yeni uyarı ilkeleri](new-defender-alert-policies.md).|Tehdit yönetimi|Evet|E5/G5 veya Office 365 için Defender P2 eklenti aboneliği|
|**Kampanyadan gelen e-posta iletileri teslimden sonra kaldırıldı**|[Kampanya](../security/office-365-security/campaigns.md) ile ilişkili iletiler kuruluşunuzdaki posta kutularına teslim edildiğinde bir uyarı oluşturur. Bu olay oluşursa, Microsoft [sıfır saatlik otomatik temizlemeyi](../security/office-365-security/zero-hour-auto-purge.md) kullanarak virüslü iletileri Exchange Online posta kutularından kaldırır. Bu ilke bir **Bilgilendirici** önem derecesi ayarına sahiptir ve [Office 365 otomatik araştırma ve yanıtı](../security/office-365-security/office-365-air.md) otomatik olarak tetikler. Bu yeni ilke hakkında daha fazla bilgi için bkz. [Office 365 için Microsoft Defender'de yeni uyarı ilkeleri](new-defender-alert-policies.md).|Tehdit yönetimi|Evet|E5/G5 veya Office 365 için Defender P2 eklenti aboneliği|
|**Teslimden sonra e-posta iletileri kaldırıldı**|Kötü amaçlı bir varlık (URL veya Dosya) içermeyen veya Kampanya ile ilişkilendirilmiş kötü amaçlı iletiler kuruluşunuzdaki posta kutularına teslim edildiğinde bir uyarı oluşturur. Bu olay oluşursa, Microsoft [sıfır saatlik otomatik temizlemeyi](../security/office-365-security/zero-hour-auto-purge.md) kullanarak virüslü iletileri Exchange Online posta kutularından kaldırır. Bu ilke bir **Bilgilendirici** önem derecesi ayarına sahiptir ve [Office 365 otomatik araştırma ve yanıtı](../security/office-365-security/office-365-air.md) otomatik olarak tetikler. Bu yeni ilke hakkında daha fazla bilgi için bkz. [Office 365 için Microsoft Defender'de yeni uyarı ilkeleri](new-defender-alert-policies.md).|Tehdit yönetimi|Evet|E5/G5 veya Office 365 için Defender P2 eklenti aboneliği|
|**Kullanıcı tarafından kötü amaçlı yazılım veya kimlik avı olarak bildirilen e-posta**|Kuruluşunuzdaki kullanıcılar, Rapor İletisi eklentisini kullanarak iletileri kimlik avı e-postası olarak bildirdiğinde bir uyarı oluşturur. Bu ilke **düşük önem** derecesine sahip bir ayara sahiptir. Bu eklenti hakkında daha fazla bilgi için bkz. [Rapor İletisi eklentisini kullanma](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2). Office 365 için Defender P2, E5, G5 müşterileri için bu uyarı otomatik [araştırmayı ve yanıtı otomatik olarak Office 365](../security/office-365-security/office-365-air.md) tetikler.|Tehdit yönetimi|Evet|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**E-posta gönderme sınırı aşıldı**|Kuruluşunuzdaki biri giden istenmeyen posta ilkesi tarafından izin verilenden daha fazla posta gönderdiğinde bir uyarı oluşturur. Bu genellikle kullanıcının çok fazla e-posta gönderdiğinin veya hesabın gizliliğinin tehlikeye girmiş olabileceğinin göstergesidir. Bu ilkenin **Orta** önem derecesi ayarı vardır. Bu uyarı ilkesi tarafından oluşturulan bir uyarı alırsanız [, kullanıcı hesabının gizliliğinin ihlal edilip edilmediğini denetlemek iyi bir fikirdir](../security/office-365-security/responding-to-a-compromised-email-account.md).|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Olası kimlik avı girişimi nedeniyle form engellendi**|Kuruluşunuzdaki birinin formları paylaşması ve yinelenen kimlik avı girişimi davranışı algılanması nedeniyle Microsoft Forms kullanarak yanıt toplaması kısıtlandığında bir uyarı oluşturur. Bu ilkenin **Yüksek önem derecesi** ayarı vardır.|Tehdit yönetimi|Hayır|E1, E3/F3 veya E5|
|**Kimlik avı olarak işaretlenen ve onaylanan form**|Kuruluşunuzun içinden Microsoft Forms oluşturulan bir form, Kötüye Kullanım Raporu aracılığıyla olası kimlik avı olarak tanımlandığında ve Microsoft tarafından kimlik avı olarak onaylandığında bir uyarı oluşturur. Bu ilkenin **Yüksek** önem derecesi ayarı vardır.|Tehdit yönetimi|Hayır|E1, E3/F3 veya E5|
|**İletiler geciktirildi**|Microsoft, bağlayıcı kullanarak şirket içi kuruluşunuza veya iş ortağı sunucunuza e-posta iletileri gönderemiyorsa bir uyarı oluşturur. Bu durumda, ileti Office 365 kuyruğa alınır. Bu uyarı, bir saatten uzun süredir kuyruğa alınmış 2.000 veya daha fazla ileti olduğunda tetiklenir. Bu ilkenin **Yüksek** önem derecesi ayarı vardır.|Posta akışı|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Teslimden sonra kötü amaçlı yazılım kampanyası algılandı**|Kötü amaçlı yazılım içeren çok sayıda ileti kuruluşunuzdaki posta kutularına teslim edildiğinde bir uyarı oluşturur. Bu olay oluşursa, Microsoft virüslü iletileri Exchange Online posta kutularından kaldırır. Bu ilkenin **Yüksek** önem derecesi ayarı vardır.|Tehdit yönetimi|Hayır|E5/G5 veya Office 365 için Microsoft Defender P2 eklenti aboneliği|
|**Kötü amaçlı yazılım kampanyası algılandı ve engellendi**|Birisi kuruluşunuzdaki kullanıcılara belirli bir tür kötü amaçlı yazılım içeren olağan dışı derecede çok sayıda e-posta iletisi göndermeye çalıştığında bir uyarı oluşturur. Bu olay oluşursa, virüslü iletiler Microsoft tarafından engellenir ve posta kutularına teslim edilmez. Bu ilke **düşük önem** derecesine sahiptir.|Tehdit yönetimi|Hayır|E5/G5 veya Office 365 için Defender P2 eklenti aboneliği|
|**SharePoint ve OneDrive'de kötü amaçlı yazılım kampanyası algılandı**|Kuruluşunuzdaki SharePoint sitelerinde veya OneDrive hesaplarında bulunan dosyalarda olağan dışı derecede yüksek miktarda kötü amaçlı yazılım veya virüs algılandığında bir uyarı oluşturur. Bu ilkenin **Yüksek** önem derecesi ayarı vardır.|Tehdit yönetimi|Hayır|E5/G5 veya Office 365 için Defender P2 eklenti aboneliği|
|**ZAP devre dışı bırakıldığından kötü amaçlı yazılım engellenmedi**| Kimlik Avı iletileri için Otomatik Temizleme devre dışı bırakıldığından, Microsoft bir kötü amaçlı yazılım iletisini Zero-Hour n posta kutusuna teslimini algıladığında bir uyarı oluşturur. Bu ilkenin **Bilgilendirici** önem derecesi ayarı vardır. |Tehdit yönetimi|Hayır|E5/G5 veya Office 365 için Defender P2 eklenti aboneliği|
|**Kullanıcının Gereksiz Posta klasörü devre dışı bırakıldığından kimlik avı teslim edildi**|Microsoft bir kullanıcının Gereksiz Posta klasörünün devre dışı bırakıldığında bir uyarı oluşturur ve bu sayede posta kutusuna yüksek güvenilirlikli kimlik avı iletisinin teslim edilmesine olanak tanır. Bu ilkenin **Bilgilendirici** önem derecesi ayarı vardır.|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**ETR geçersiz kılma nedeniyle kimlik avı teslim edildi**|Microsoft, yüksek güvenilirlikli kimlik avı iletisinin bir posta kutusuna teslim edilmesine izin veren bir Exchange Aktarım Kuralı (ETR) algıladığında bir uyarı oluşturur. Bu ilkenin **Bilgilendirici** önem derecesi ayarı vardır. Exchange Aktarım Kuralları (Posta akışı kuralları) hakkında daha fazla bilgi için bkz. [Exchange Online'de Posta akışı kuralları (aktarım kuralları).](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**IP izin verme ilkesi nedeniyle kimlik avı teslim edildi**|Microsoft, yüksek güvenilirlikli kimlik avı iletisinin bir posta kutusuna teslim edilmesine izin veren bir IP izin ilkesi algıladığında bir uyarı oluşturur. Bu ilkenin **Bilgilendirici** önem derecesi ayarı vardır. IP izin verme ilkesi (bağlantı filtreleme) hakkında daha fazla bilgi için bkz[. Varsayılan bağlantı filtresi ilkesini yapılandırma - Office 365](../security/office-365-security/configure-the-connection-filter-policy.md).|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**ZAP devre dışı bırakıldığından kimlik avı engellenmedi**| Zero-Hour Kimlik Avı iletileri için Otomatik Temizleme devre dışı bırakıldığından, Microsoft yüksek güvenilirlikli bir kimlik avı iletisinin posta kutusuna teslimini algıladığında bir uyarı oluşturur. Bu ilkenin **Bilgilendirici** önem derecesi ayarı vardır.|Tehdit yönetimi|Hayır|E5/G5 veya Office 365 için Defender P2 eklenti aboneliği|
|**Kiracı veya kullanıcı geçersiz kılma nedeniyle kimlik avı teslim** <sup>edildi1</sup>|Microsoft, kimlik avı iletisinin posta kutusuna teslim edilmesine izin verilen bir yönetici veya kullanıcı geçersiz kılma algıladığında bir uyarı oluşturur. Geçersiz kılmalara örnek olarak, belirli bir gönderenden veya etki alanından gelen iletilere izin veren bir gelen kutusu veya posta akışı kuralı ya da belirli gönderenlerden veya etki alanlarından gelen iletilere izin veren istenmeyen posta önleme ilkesi verilebilir. Bu ilkenin **Yüksek** önem derecesi ayarı vardır.|Tehdit yönetimi|Hayır|E5/G5 veya Office 365 için Defender P2 eklenti aboneliği|
|**Şüpheli e-posta iletme etkinliği**|Kuruluşunuzdaki biri şüpheli bir dış hesaba otomatik olarak e-posta gönderdiğinde bir uyarı oluşturur. Bu, hesabın gizliliğinin aşıldığını ancak kullanıcıyı kısıtlayabilecek kadar ciddi olmadığını gösteren davranışlar için erken bir uyarıdır. Bu ilkenin **Yüksek** önem derecesi ayarı vardır. Nadir olsa da, bu ilke tarafından oluşturulan bir uyarı bir anomali olabilir. [Kullanıcı hesabının gizliliğinin ihlal edilip edilmediğini denetlemek iyi bir fikirdir](../security/office-365-security/responding-to-a-compromised-email-account.md).|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Şüpheli e-posta gönderme desenleri algılandı**|Kuruluşunuzdaki bir kişi şüpheli e-posta gönderdiğinde ve e-posta göndermesi kısıtlanma riskiyle karşılandığında bir uyarı oluşturur. Bu, hesabın gizliliğinin tehlikeye girdiğini ancak kullanıcıyı kısıtlayabilecek kadar ciddi olmadığını gösteren davranışlar için erken bir uyarıdır. Bu ilkenin **Orta** önem derecesi ayarı vardır. Nadir olsa da, bu ilke tarafından oluşturulan bir uyarı bir anomali olabilir. Ancak [, kullanıcı hesabının gizliliğinin ihlal edilip edilmediğini denetlemek iyi bir fikirdir](../security/office-365-security/responding-to-a-compromised-email-account.md).|Tehdit yönetimi|Evet|E1/F1/G1, E3/F3/G3 veya E5/G5  |
|**Kiracı İzin Ver/Engelle Listesi girdisi süresi dolmak üzere**|Kiracı İzin Ver/Engelle Listesi girdisi kaldırılacakken bir uyarı oluşturur. Bu olay, son kullanma tarihinden üç gün önce tetiklenerek girişin oluşturulduğu veya en son güncelleştirildiği tarih temel alınmıştır. Bu uyarı ilkesi bir **Bilgilendirici** önem derecesi ayarına sahiptir. Bunun nedeni, izin verme veya engellemenin ortadan kalkabileceği için filtrelerde yapılacak değişiklikler hakkında yöneticileri bilgilendirmektir. Bloklar için, bloğu yerinde tutmak için sona erme tarihini uzatabilirsiniz. İzin vermek için, analistlerimizin bir daha bakabilmesi için öğeyi yeniden göndermeniz gerekir. Ancak, izin verilen değer hatalı pozitif olarak zaten derecelendirildiyse, girişin süresi yalnızca sistem filtreleri girişe doğal olarak izin verecek şekilde güncelleştirildiğinde sona erer. Bu uyarıyı tetikleyen olaylar hakkında daha fazla bilgi için bkz. [Kiracı İzin Ver/Engelle listesini yönetme](../security/office-365-security/tenant-allow-block-list.md).|Tehdit yönetimi|Hayır|E5/G5 veya Office 365 için Defender P2 eklenti aboneliği|
|**Kiracının e-posta göndermesi kısıtlandı**|Kuruluşunuzdan gelen e-posta trafiğinin çoğu şüpheli olarak algılandığında ve Microsoft kuruluşunuzun e-posta göndermesini kısıtladığında bir uyarı oluşturur. Güvenliği aşılmış olabilecek kullanıcı ve yönetici hesaplarını, yeni bağlayıcıları veya açık geçişleri araştırın ve kuruluşunuzun engelini kaldırmak için Microsoft Desteği başvurun. Bu ilkenin **Yüksek** önem derecesi ayarı vardır. Kuruluşların neden engellendiği hakkında daha fazla bilgi için bkz. [Exchange Online'de hata kodu 5.7.7xx için e-posta teslim sorunlarını düzeltme](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-7-700-through-5-7-750).|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Kiracının sağlanmamış e-posta göndermesi kısıtlandı**|Kayıtlı olmayan etki alanlarından (sağlanmamış etki *alanları olarak da* bilinir) çok fazla e-posta gönderildiğinde bir uyarı oluşturur. Office 365, kayıtlı olmayan etki alanlarından makul miktarda e-posta gönderilmesine izin verir, ancak kullandığınız her etki alanını e-postayı kabul edilen bir etki alanı olarak gönderecek şekilde yapılandırmanız gerekir. Bu uyarı, kuruluştaki tüm kullanıcıların artık e-posta gönderemeyeceklerini gösterir. Bu ilkenin **Yüksek** önem derecesi ayarı vardır. Kuruluşların neden engellendiği hakkında daha fazla bilgi için bkz. [Exchange Online'de hata kodu 5.7.7xx için e-posta teslim sorunlarını düzeltme](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-7-700-through-5-7-750).|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Olağan dışı dış kullanıcı dosyası etkinliği**|Kuruluşunuz dışındaki kullanıcılar tarafından SharePoint veya OneDrive dosyalar üzerinde olağan dışı derecede çok sayıda etkinlik gerçekleştirildiğinde bir uyarı oluşturur. Bu, dosyalara erişme, dosyaları indirme ve dosyaları silme gibi etkinlikleri içerir. Bu ilkenin **Yüksek** önem derecesi ayarı vardır.|Bilgi Yönetişimi|Hayır|E5/G5, Office 365 için Microsoft Defender P2 veya Microsoft 365 E5 eklenti aboneliği|
|**Olağan dışı dış dosya paylaşımı hacmi**|SharePoint veya OneDrive'daki çok fazla sayıda dosya kuruluşunuzun dışındaki kullanıcılarla paylaşıldığında bir uyarı oluşturur. Bu ilkenin **Orta** önem derecesi ayarı vardır.|Bilgi Yönetişimi|Hayır|E5/G5, Office 365 için Defender P2 veya Microsoft 365 E5 eklenti aboneliği|
|**Olağan dışı dosya silme hacmi**|SharePoint veya OneDrive kısa bir süre içinde olağan dışı derecede çok sayıda dosya silindiğinde bir uyarı oluşturur. Bu ilkenin **Orta** önem derecesi ayarı vardır.|Bilgi Yönetişimi|Hayır|E5/G5, Office 365 için Defender P2 veya Microsoft 365 E5 eklenti aboneliği|
|**Kimlik avı olarak bildirilen e-postada olağan dışı artış**|İletileri kimlik avı postası olarak raporlamak için Outlook Rapor İletisi eklentisini kullanan kuruluşunuzdaki kişi sayısında önemli bir artış olduğunda bir uyarı oluşturur. Bu ilkenin **Orta** önem derecesi ayarı vardır. Bu eklenti hakkında daha fazla bilgi için bkz. [Rapor İletisi eklentisini kullanma](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2).|Tehdit yönetimi|Hayır|E5/G5 veya Office 365 için Defender P2 eklenti aboneliği|
|**Gelen kutusuna/klasörüne teslim edilen kullanıcı kimliğe bürünme kimlik** <sup>avı1,2</sup><sup></sup>|Microsoft, bir yönetici veya kullanıcı geçersiz kılmasının bir kullanıcının kimliğe bürünme kimlik avı iletisinin bir posta kutusunun gelen kutusuna (veya kullanıcı tarafından erişilebilen başka bir klasöre) teslim edilmesine izin ettiğini algıladığında bir uyarı oluşturur. Geçersiz kılmalara örnek olarak, belirli bir gönderenden veya etki alanından gelen iletilere izin veren bir gelen kutusu veya posta akışı kuralı ya da belirli gönderenlerden veya etki alanlarından gelen iletilere izin veren istenmeyen posta önleme ilkesi verilebilir. Bu ilkenin **Orta** önem derecesi ayarı vardır.|Tehdit yönetimi|Hayır|E5/G5 veya Office 365 için Defender P2 eklenti aboneliği|
|**Kullanıcı karantinaya alınmış bir iletiyi serbest bırakmak istedi**|Kullanıcı karantinaya alınmış bir iletinin yayınlanmasını istediğinde bir uyarı oluşturur. Karantinaya alınan iletilerin yayımlanmasını istemek için, karantina ilkesinde (örneğin, **Sınırlı erişim** önceden ayarlanmış izinler grubundan) **alıcıların karantinadan çıkarılacak bir ileti istemesine izin ver** (_PermissionToRequestRelease_) izni gerekir. Daha fazla bilgi için bkz. [Alıcıların karantina izninden serbest bırakılacak bir ileti istemesine izin verme](../security/office-365-security/quarantine-policies.md#allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission). Bu ilkenin **Bilgilendirici** önem derecesi ayarı vardır.|Tehdit yönetimi|Hayır|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Kullanıcının e-posta göndermesi kısıtlandı**|Kuruluşunuzdaki birinin giden posta göndermesi kısıtlandığında bir uyarı oluşturur. Bu durum genellikle bir hesabın güvenliği aşıldığında ve kullanıcı uyumluluk portalındaki **Kısıtlı Kullanıcılar** sayfasında listelendiğinde sonuçlanır. (Bu sayfaya erişmek için **Tehdit yönetimi > Kısıtlanmış Kullanıcılar > Gözden Geçir'e** gidin). Bu ilkenin **Yüksek** önem derecesi ayarı vardır. Kısıtlanmış kullanıcılar hakkında daha fazla bilgi için bkz. [İstenmeyen e-posta gönderdikten sonra engellenenler listesinden kullanıcı, etki alanı veya IP adresini kaldırma](/office365/securitycompliance/removing-user-from-restricted-users-portal-after-spam).|Tehdit yönetimi|Evet|E1/F1/G1, E3/F3/G3 veya E5/G5|
|**Kullanıcının formları paylaşması ve yanıt toplaması kısıtlandı**|Kuruluşunuzdaki birinin formları paylaşması ve yinelenen kimlik avı girişimi davranışı algılanması nedeniyle Microsoft Forms kullanarak yanıt toplaması kısıtlandığında bir uyarı oluşturur. Bu ilkenin **Yüksek** önem derecesi ayarı vardır.|Tehdit yönetimi|Hayır|E1, E3/F3 veya E5|

> [!NOTE]
> <sup>1</sup> Bu varsayılan uyarı ilkesini müşteri geri bildirimlerine göre geçici olarak kaldırdık. Geliştirmek için çalışıyoruz ve yakın gelecekte yeni bir sürümle değiştireceğiz. O zamana kadar, aşağıdaki ayarları kullanarak bu işlevselliği değiştirmek için özel bir uyarı ilkesi oluşturabilirsiniz: <ul><li>Etkinlik, teslim sırasında kimlik avı e-postası algılandı</li> <li>Posta ZAP değil</li> <li>Posta yönü Gelen</li> <li>Posta teslim durumu Teslim Edildi</li> <li>Algılama teknolojisi Kötü Amaçlı URL saklama, URL'yi patlatma, Gelişmiş kimlik avı filtresi, Genel kimlik avı filtresi, Etki alanı kimliğe bürünme, Kullanıcı kimliğe bürünme ve Marka kimliğe bürünmedir</li></ul> Office 365'da kimlik avı önleme hakkında daha fazla bilgi için bkz. [Kimlik avı önleme ve kimlik avı önleme ilkelerini ayarlama](../security/office-365-security/set-up-anti-phishing-policies.md).<br/><br/><sup>2</sup> Bu uyarı ilkesini yeniden oluşturmak için önceki dipnottaki yönergeleri izleyin, ancak tek Algılama teknolojisi olarak Kullanıcı kimliğe bürünme'yi seçin.

Bazı yerleşik ilkeler tarafından izlenen olağan dışı etkinlik, daha önce açıklanan uyarı eşiği ayarıyla aynı işlemi temel alır. Microsoft, "normal" etkinlik için normal sıklığı tanımlayan bir temel değer oluşturur. Yerleşik uyarı ilkesi tarafından izlenen etkinliklerin sıklığı temel değeri büyük ölçüde aştığında uyarılar tetiklenir.

<a name="viewing-alerts"></a>

## <a name="view-alerts"></a>Uyarıları görüntüleme

Kuruluşunuzdaki kullanıcılar tarafından gerçekleştirilen bir etkinlik bir uyarı ilkesinin ayarlarıyla eşleştiğinde, uyumluluk merkezindeki veya Defender portalındaki **Uyarılar** sayfasında bir uyarı oluşturulur ve görüntülenir. Uyarı ilkesinin ayarlarına bağlı olarak, bir uyarı tetiklendiğinde belirtilen kullanıcıların listesine bir e-posta bildirimi de gönderilir. Her uyarı için **, Uyarılar** sayfasındaki panoda ilgili uyarı ilkesinin adı, uyarının önem derecesi ve kategorisi (uyarı ilkesinde tanımlanır) ve uyarının oluşturulmasıyla sonuçlanan etkinlik sayısı görüntülenir. Bu değer, uyarı ilkesinin eşik ayarını temel alır. Pano ayrıca her uyarının durumunu da gösterir. Uyarıları yönetmek için durum özelliğini kullanma hakkında daha fazla bilgi için bkz. [Uyarıları yönetme](#manage-alerts).

Uyarıları görüntülemek için:

### <a name="microsoft-purview-compliance-portal"></a>Microsoft Purview uyumluluk portalı

 <https://compliance.microsoft.com> Öğesine gidin ve **Uyarılar'ı** seçin. Alternatif olarak doğrudan adresine <https://compliance.microsoft.com/compliancealerts>gidebilirsiniz.

![Uyumluluk portalında Uyarılar'ı seçin.](../media/ViewAlertsMCC.png)

### <a name="microsoft-365-defender-portal"></a>Microsoft 365 Defender portalı

<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalına</a> gidin ve **ardından Olaylar &** **uyarılarAlerts'i** >  seçin. Alternatif olarak doğrudan adresine <https://security.microsoft.com/alerts>gidebilirsiniz.

![Microsoft 365 Defender portalında Olaylar & uyarılar'ı ve ardından Uyarılar'ı seçin.](../media/ViewAlertsDefenderPortal.png)

**Uyarılar** sayfasında tüm uyarıların bir alt kümesini görüntülemek için aşağıdaki filtreleri kullanabilirsiniz.

- **Durum.** Belirli bir duruma atanan uyarıları göstermek için bu filtreyi kullanın. Varsayılan durum **Etkin'dir**. Siz veya diğer yöneticiler durum değerini değiştirebilirsiniz.

- **Ilkesi.** Bir veya daha fazla uyarı ilkesi ayarıyla eşleşen uyarıları göstermek için bu filtreyi kullanın. Ya da tüm uyarı ilkeleri için tüm uyarıları görüntüleyebilirsiniz.

- **Zaman aralığı.** Belirli bir tarih ve saat aralığında oluşturulan uyarıları göstermek için bu filtreyi kullanın.

- **Önem.** Belirli bir önem derecesine atanan uyarıları göstermek için bu filtreyi kullanın.

- **Kategori.** Bir veya daha fazla uyarı kategorisindeki uyarıları göstermek için bu filtreyi kullanın.

- **Etiketler.** Bir veya daha fazla kullanıcı etiketinden gelen uyarıları göstermek için bu filtreyi kullanın. Etiketler, uyarılarda görünen etiketli posta kutularına veya kullanıcılara göre yansıtılır. Daha fazla bilgi için bkz. [Office 356 ATP'deki kullanıcı etiketleri](../security/office-365-security/user-tags.md).

- **Kaynak.** Uyumluluk merkezinde uyarı ilkeleri tarafından tetiklenen uyarıları veya Office 365 Bulut Uygulamaları Güvenliği ilkeleri tarafından tetiklenen uyarıları veya her ikisini birden göstermek için bu filtreyi kullanın. Office 365 Bulut Uygulamaları Güvenliği uyarıları hakkında daha fazla bilgi için bkz[. Bulut için Defender Uygulamaları uyarılarını görüntüleme](#viewing-cloud-app-security-alerts).

> [!IMPORTANT]
> Kullanıcı etiketlerine göre filtreleme ve sıralama şu anda genel önizleme aşamasındadır.
> Ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilir. Microsoft, bu konuda sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

## <a name="alert-aggregation"></a>Uyarı toplama

Bir uyarı ilkesinin koşullarıyla eşleşen birden çok olay kısa bir süre içinde gerçekleştiğinde, *bunlar uyarı toplama* adlı bir işlem tarafından var olan bir uyarıya eklenir. Bir olay bir uyarıyı tetiklediğinde, uyarı oluşturulur ve **Uyarılar** sayfasında görüntülenir ve bir bildirim gönderilir. Aynı olay toplama aralığı içinde gerçekleşirse, Microsoft 365 yeni bir uyarı tetikleme yerine mevcut uyarıya yeni olayla ilgili ayrıntıları ekler. Uyarı toplamanın amacı, uyarı "yorgunluğunu" azaltmaya yardımcı olmak ve aynı olay için daha az uyarıya odaklanmanızı ve eylem gerçekleştirmenizi sağlamaktır.

Toplama aralığının uzunluğu Office 365 veya Microsoft 365 aboneliğinize bağlıdır.

|Abonelik|Toplama aralığı|
|:---------|:---------:|
|Office 365 veya Microsoft 365 E5/G5|1 dakika|
|Office 365 için Defender Plan 2 |1 dakika|
|E5 Uyumluluk eklentisi veya E5 Bulma ve Denetim eklentisi|1 dakika|
|E1/F1/G1 veya E3/F3/G3 Office 365 veya Microsoft 365|15 dakika|
|Plan 1 veya Exchange Online Protection Office 365 için Defender|15 dakika|

Toplama aralığında aynı uyarı ilkesiyle eşleşen olaylar gerçekleştiğinde, sonraki olayla ilgili ayrıntılar özgün uyarıya eklenir. Tüm olaylar için, toplanan olaylar hakkındaki bilgiler ayrıntılar alanında görüntülenir ve toplama aralığıyla bir olayın kaç kez gerçekleştiği etkinlik/isabet sayısı alanında görüntülenir. Etkinlik listesini görüntüleyerek tüm toplanan olay örnekleri hakkında daha fazla bilgi görüntüleyebilirsiniz.

Aşağıdaki ekran görüntüsünde dört toplu olay içeren bir uyarı gösterilmektedir. Etkinlik listesi uyarıyla ilgili dört e-posta iletisi hakkında bilgi içerir.

![Uyarı toplama örneği.](../media/AggregatedAlertExample.png)

Uyarı toplama hakkında aşağıdaki şeyleri göz önünde bulundurun:

- **Kötü amaçlı olabilecek BIR URL tıklaması** tarafından tetiklenen uyarılar algılandı [varsayılan uyarı ilkesi](#default-alert-policies) toplanmaz. Bunun nedeni, bu ilke tarafından tetiklenen uyarıların her kullanıcı ve e-posta iletisi için benzersiz olmasıdır.

- Şu anda **İsabet sayısı** uyarı özelliği, tüm uyarı ilkeleri için toplanan olayların sayısını göstermez. Bu uyarı ilkeleri tarafından tetiklenen uyarılar için, **ileti listesini görüntüle'ye** veya uyarıdaki **Etkinliği görüntüle'ye** tıklayarak toplanan olayları görüntüleyebilirsiniz. **İsabet sayısı** uyarı özelliğinde listelenen toplu olayların sayısını tüm uyarı ilkeleri için kullanılabilir hale getirmek için çalışıyoruz.

## <a name="rbac-permissions-required-to-view-alerts"></a>Uyarıları görüntülemek için gereken RBAC izinleri

Kuruluşunuzdaki kullanıcılara atanan Rol Tabanlı Access Control (RBAC) izinleri, kullanıcının **Uyarılar** sayfasında hangi uyarıları görebileceğini belirler. Bu nasıl başarıldı? Kullanıcılara atanan yönetim rolleri (uyumluluk portalındaki veya Microsoft 365 Defender portalındaki rol gruplarındaki üyeliklerine bağlı olarak), kullanıcının Uyarılar sayfasında hangi uyarı **kategorilerini** görebileceğini belirler. İşte birkaç örnek:

- Kayıt Yönetimi rol grubunun üyeleri yalnızca **Bilgi idaresi** kategorisine atanan uyarı ilkeleri tarafından oluşturulan uyarıları görüntüleyebilir.

- Uyumluluk Yöneticisi rol grubunun üyeleri **, Tehdit yönetimi** kategorisine atanan uyarı ilkeleri tarafından oluşturulan uyarıları görüntüleyemez.

- Atanan rollerin hiçbiri herhangi bir uyarı kategorisindeki uyarıları görüntüleme izni vermediğinden, eBulma Yöneticisi rol grubunun üyeleri hiçbir uyarıyı görüntüleyemiyor.

Bu tasarım (RBAC izinlerine göre) kuruluşunuzdaki belirli iş rollerindeki kullanıcılar tarafından hangi uyarıların görüntüleneceğini (ve yönetilebileceğini) belirlemenize olanak tanır.

Aşağıdaki tabloda, altı farklı uyarı kategorisindeki uyarıları görüntülemek için gereken roller listelenmiştir. Tablolardaki ilk sütun, uyumluluk portalındaki veya Microsoft 365 Defender portalındaki tüm rolleri listeler.  Onay işareti, bu role atanan bir kullanıcının uyarıları üst satırda listelenen ilgili uyarı kategorisinden görüntüleyebileceğini gösterir.

Varsayılan uyarı ilkesinin atandığı kategoriyi görmek için [Varsayılan uyarı ilkeleri'ndeki](#default-alert-policies) tabloya bakın.

|Rol|Bilgi Yönetişimi|Veri kaybı önleme|Posta akışı|İzinler|Tehdit yönetimi|Diğer|
|:---------|:---------:|:---------:|:---------:|:---------:|:---------:|:---------:|
|Denetim Günlükleri|||||||
|Olay Yönetimi|||||||
|Uyumluluk Yöneticisi|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)||![Onay işareti.](../media/checkmark.png)||![Onay işareti.](../media/checkmark.png)|
|Uyumluluk Araması|||||||
|Cihaz Yönetimi|||||||
|Disposition Management|||||||
|DLP Uyumluluk Yönetimi||![Onay işareti.](../media/checkmark.png)|||||
|Dışarı aktarma|||||||
|Tutun|||||||
|Information Protection Analisti||![Onay işareti.](../media/checkmark.png)|||||
|Information Protection Araştırmacısı||![Onay işareti.](../media/checkmark.png)|||||
|Uyarıları Yönet||||||![Onay işareti.](../media/checkmark.png)|
|Kuruluş Yapılandırması||||||![Onay işareti.](../media/checkmark.png)|
|Önizleme|||||||
|Kayıt Yönetimi|![Onay işareti.](../media/checkmark.png)||||||
|Bekletme Yönetimi|![Onay işareti.](../media/checkmark.png)||||||
|Gözden geçirin|||||||
|RMS Şifre Çözme|||||||
|Rol Yönetimi||||![Onay işareti.](../media/checkmark.png)|||
|Arama ve Temizleme|||||||
|Güvenlik Yöneticisi||![Onay işareti.](../media/checkmark.png)||![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|
|Güvenlik Okuyucusu||![Onay işareti.](../media/checkmark.png)||![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)|![Onay işareti.](../media/checkmark.png)
|Hizmet Güvencesi Görünümü|||||||
|Gözetmen Gözden Geçirme Yöneticisi|||||||
|Denetim Günlüklerini View-Only|||||||
|View-Only Cihaz Yönetimi|||||||
|View-Only DLP Uyumluluk Yönetimi||![Onay işareti.](../media/checkmark.png)|||||
|Uyarıları View-Only Yönetme||||||![Onay işareti](../media/checkmark.png)|
|alıcıları View-Only|||![Onay işareti](../media/checkmark.png)||||
|View-Only Kayıt Yönetimi|![Onay işareti](../media/checkmark.png)||||||
|View-Only Bekletme Yönetimi|![Onay işareti](../media/checkmark.png)||||||

> [!TIP]
> Varsayılan rol gruplarının her birine atanan rolleri görüntülemek için Güvenlik & Uyumluluk Merkezi PowerShell'de aşağıdaki komutları çalıştırın:
>
> ```powershell
> $RoleGroups = Get-RoleGroup
> ```
>
> ```powershell
> $RoleGroups | foreach {Write-Output -InputObject `r`n,$_.Name,"-----------------------"; Get-RoleGroup $_.Identity | Select-Object -ExpandProperty Roles}
> ```
>
> Uyumluluk portalında veya Microsoft 365 Defender portalında bir rol grubuna atanan rolleri de görüntüleyebilirsiniz. **İzinler** sayfasına gidin ve bir rol grubu seçin. Atanan roller açılır sayfada listelenir.

<a name="manage-alerts"></a>

## <a name="manage-alerts"></a>Uyarıları yönetin

Uyarılar oluşturulduktan ve uyumluluk merkezindeki **Uyarılar** sayfasında görüntülendikten sonra bunları önceliklendikten, araştırabilir ve çözümleyebilirsiniz. Kullanıcılara [uyarılara erişim sağlayan RBAC izinleri](#rbac-permissions-required-to-view-alerts) , onlara uyarıları yönetme olanağı da verir.

Uyarıları yönetmek için gerçekleştirebileceğiniz bazı görevler aşağıdadır.

- **Uyarılara bir durum atayın.** Uyarılara şu durumlardan birini atayabilirsiniz: **Etkin** (varsayılan değer), **Araştırma**, **Çözümlendi** veya **Kapatıldı**. Ardından, aynı durum ayarına sahip uyarıları görüntülemek için bu ayarı filtreleyebilirsiniz. Bu durum ayarı, uyarıları yönetme işlemini izlemeye yardımcı olabilir.

- **Uyarı ayrıntılarını görüntüleyin.** Uyarıyla ilgili ayrıntıları içeren bir açılır sayfa görüntülemek için bir uyarı seçebilirsiniz. Ayrıntılı bilgiler ilgili uyarı ilkesine bağlıdır, ancak genellikle aşağıdakileri içerir:

  - Cmdlet veya denetim günlüğü işlemi gibi uyarıyı tetikleyen gerçek işlemin adı.

  - Uyarıyı tetikleyen etkinliğin açıklaması.

  - Uyarıyı tetikleyen kullanıcı (veya kullanıcı listesi). Bu yalnızca tek bir kullanıcıyı veya tek bir etkinliği izlemek için ayarlanan uyarı ilkelerine dahildir.

  - Uyarı tarafından izlenen etkinliğin kaç kez gerçekleştirildiği. Daha fazla uyarı tetiklenmiş olabileceğinden, bu sayı Uyarılar sayfasında listelenen ilgili uyarı sayısıyla eşleşmeyebilir.

  - Uyarıyı tetikleyen gerçekleştirilen her etkinlik için bir öğe içeren bir etkinlik listesinin bağlantısı. Bu listedeki her girdi, etkinliğin ne zaman gerçekleştiğini, gerçek işlemin adını ("FileDeleted" gibi), etkinliği gerçekleştiren kullanıcıyı, etkinliğin gerçekleştirildiği nesneyi (dosya, eBulma olayı veya posta kutusu gibi) ve kullanıcının bilgisayarının IP adresini tanımlar. Kötü amaçlı yazılımla ilgili uyarılar için bu, bir ileti listesine bağlanır.

  - İlgili uyarı ilkesinin adı (ve bağlantısı).

- **E-posta bildirimlerini gizleme.** Bir uyarı için açılır sayfadan e-posta bildirimlerini kapatabilirsiniz (veya gizleyebilirsiniz). E-posta bildirimlerini gizlediğinizde, uyarı ilkesinin koşullarıyla eşleşen etkinlikler veya olaylar gerçekleştiğinde Microsoft bildirim göndermez. Ancak kullanıcılar tarafından gerçekleştirilen etkinlikler uyarı ilkesinin koşullarıyla eşleştiğinde uyarılar tetiklenir. Uyarı ilkesini düzenleyerek e-posta bildirimlerini de kapatabilirsiniz.

- **Uyarıları çözün.** Uyarının açılır sayfasında bir uyarıyı çözümlendi olarak işaretleyebilirsiniz (uyarının durumunu **Çözüldü** olarak ayarlar). Filtreyi değiştirmediğiniz sürece, çözümlenen uyarılar **Uyarılar** sayfasında görüntülenmez.

<a name="viewing-cloud-app-security-alerts"></a>

## <a name="view-defender-for-cloud-apps-alerts"></a>Bulut için Defender Uygulamaları uyarılarını görüntüleme

Office 365 Bulut Uygulamaları Güvenliği ilkeleri tarafından tetiklenen uyarılar artık uyumluluk merkezindeki **Uyarılar** sayfasında görüntülenir. Bu, etkinlik ilkeleri tarafından tetiklenen uyarıları ve Office 365 Bulut Uygulamaları Güvenliği anomali algılama ilkeleri tarafından tetiklenen uyarıları içerir. Bu, uyumluluk merkezinde tüm uyarıları görüntüleyebileceğiniz anlamına gelir. Office 365 Bulut Uygulamaları Güvenliği yalnızca Office 365 Kurumsal E5 veya Office 365 US Government G5 aboneliği olan kuruluşlar için kullanılabilir. Daha fazla bilgi için bkz. [Bulut için Defender Uygulamalarına Genel Bakış](/cloud-app-security/what-is-cloud-app-security).

Enterprise Mobility + Security E5 aboneliği veya tek başına hizmet olarak Microsoft Defender for Cloud Apps sahip kuruluşlar da Microsoft 365 ile ilgili Bulut için Defender Uygulamaları uyarılarını görüntüleyebilir  uyumluluk portalında veya Microsoft 365 Defender portalında uygulamalar ve hizmetler.

Uyumluluk merkezinde veya Defender portalında yalnızca Bulut için Defender Uygulamalar uyarılarını görüntülemek için **Kaynak** filtresini kullanın ve **Uygulamalar'ı Bulut için Defender** seçin.

![Yalnızca Bulut için Defender Uygulamaları uyarılarını görüntülemek için Kaynak filtresini kullanın.](../media/FilterCASAlerts.png)

Uyumluluk merkezindeki bir uyarı ilkesi tarafından tetiklenen uyarıya benzer şekilde, Bulut için Defender Uygulamalar uyarısını seçerek uyarıyla ilgili ayrıntıları içeren bir açılır sayfa görüntüleyebilirsiniz. Uyarı, ayrıntıları görüntülemek ve Bulut için Defender Uygulamalar portalında uyarıyı yönetmek için bir bağlantı ve uyarıyı tetikleyen ilgili Bulut için Defender Uygulamaları ilkesinin bağlantısını içerir. Bkz[. Bulut için Defender Uygulamalarında uyarıları izleme](/cloud-app-security/monitor-alerts).

![Uyarı ayrıntıları, Bulut için Defender Uygulamaları portalının bağlantılarını içerir.](../media/CASAlertDetail.png)

> [!IMPORTANT]
> Uyumluluk merkezinde bir Bulut için Defender Uygulamaları uyarısının durumunu değiştirmek, Bulut için Defender Uygulamaları portalında aynı uyarının çözüm durumunu güncelleştirmez. Örneğin, uyumluluk merkezinde uyarının durumunu **Çözüldü** olarak işaretlerseniz, Bulut için Defender Uygulamalar portalındaki uyarının durumu değişmez. Bulut için Defender Uygulamaları uyarısını çözmek veya kapatmak için, Bulut için Defender Uygulamalar portalında uyarıyı yönetin.
