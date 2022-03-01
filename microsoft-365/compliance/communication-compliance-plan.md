---
title: İletişim uyumluluğunu planlama
description: Kuruluşta iletişim uyumluluğunu kullanmayı planlamayı öğrenin.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 77579a97016d37dd9bfc12f88db62200fbca0ccc
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2022
ms.locfileid: "63015294"
---
# <a name="plan-for-communication-compliance"></a>İletişim uyumluluğunu planlama

Kurum içinde iletişim [uyumluluğu çalışmaya](communication-compliance.md) başlamadan önce, bilgi teknolojisi ve uyumluluk yönetim ekipleri tarafından gözden geçir edilmesi gereken önemli planlama etkinlikleri ve dikkate alınacak noktalar vardır. Aşağıdaki alanlarda dağıtım yapmayı kapsamlı bir şekilde anlamanız ve planlamanız, uygulama ve iletişim uyumluluk özelliklerini kullanmanın sorunsuz şekilde olmasını ve çözüme yönelik en iyi uygulamalarla uyumlu olmasını sağlamaya yardımcı olur.

> [!IMPORTANT]
> İletişim uyumluluğu şu anda, Azure hizmet bağımlılıkları tarafından desteklenen coğrafi bölgelerde ve ülkelerde barındırılan kiracılarda kullanılabilir. İletişim uyumluluğunun organizasyonunız için destek olduğunu doğrulamak için bkz. [Ülkeye/bölgeye göre Azure bağımlılığı kullanılabilirliği](/troubleshoot/azure/general/dependency-availability-by-country).

## <a name="transitioning-from-supervision-in-office-365"></a>Office 365'ta Gözetimden Geçiş

Office 365'te gözetim ilkeleri kullanan kuruluşlar için, Microsoft 365'te iletişim uyumluluk ilkelerine geçiş yapmayı planlamanız ve şu önemli noktaları anlamanız gerekir:

- Office 365'daki gözetim çözümünün yerini, uyumluluk çözümü iletişim uyumluluk çözümü Microsoft 365. Yeni araştırma ve düzeltme geliştirmelerini kullanmak için mevcut gözetim ilkeleriyle aynı ayarlara sahip iletişim uyumluluğu için yeni ilkeler oluşturmanız önerilir.
- Gizlilik ilkesi eşleşmelerine Office 365 kaydedilen iletiler, iletişim uyumluluğu içinde taşınamaz veya Microsoft 365.
- Geçiş işlemi sırasında her iki çözümü de yan yana kullanılan kuruluşlarda, her çözümde kullanılan ilkeler benzersiz ilke adlara sahip olmalıdır. Gruplar ve özel anahtar sözcük sözlükleri bir geçiş döneminde çözümler arasında paylaşabilirsiniz.

Denetim ve gözetim için emeklilik Office 365 ayrıntılı bilgi [için Microsoft 365 Yol Haritası'Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) bakın.

## <a name="work-with-stakeholders-in-your-organization"></a>Kuruluşta proje katılımcıları ile çalışma

İletişim uyumluluğu uyarıları üzerinde işlem yapmak için, organizasyonuz içinde uygun paydaşları belirleyerek işbirliği yapın. Başlangıç planlaması ve sona uç iletişim uyumluluk iş akışı dahil olmak üzere dikkate adede olması önerilen [](communication-compliance.md#workflow) bazı paydaşlar, kurumnizin aşağıdaki alanlarında yer alan kişilerdir:

- Bilgi teknolojisi
- Uyumluluk
- Gizlilik
- Güvenlik
- İnsan kaynakları
- Yasal

## <a name="plan-for-the-investigation-and-remediation-workflow"></a>Araştırma ve düzeltme iş akışını planlama

### <a name="permissions"></a>İzinler

Uyarıları ve vakaları takip etmek ve gözden geçirmek için özel paydaşları seçerek proje [Microsoft 365 uyumluluk merkezi.](https://compliance.microsoft.com/) Kullanıcıları ve proje katılımcılarını, kurum içinde farklı iletişim uyumluluğu rol gruplarına nasıl atayacaklarınızı anlıyoruz.

> [!IMPORTANT]
> Rol gruplarınızı yapılandırdikten sonra, rol grubu izinlerin kuruluş genelinde atanan kullanıcılara uygulamak 30 dakika kadar sürebilir.

İletişim uyumluluğu özelliklerini yönetmek için başlangıç izinlerini yapılandırmak için kullanılan altı rol grubu vardır. İletişim **uyumluluğunun** E-Microsoft 365 uyumluluk merkezi menü seçeneği olarak kullanılabilir olması ve bu yapılandırma adımlarına devam etmek için, aşağıdaki rollerden veya rol gruplarından biri size atanmış olması gerekir:

- Azure Active Directory [*Yönetici rolü*](/azure/active-directory/roles/permissions-reference#global-administrator)
- Azure Active Directory [*Uyumluluk Yöneticisi*](/azure/active-directory/roles/permissions-reference#compliance-administrator) rolü
- Microsoft 365 uyumluluk merkezi [*Yönetimi*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) rol grubu
- Microsoft 365 uyumluluk merkezi [*Yöneticisi rol*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) grubu
- *İletişim Uyumluluğu* rol grubu
- *İletişim Uyumluluğu Yöneticisi* rol grubu

Aşağıdaki rollerin üyeleri, İletişim Uyumluluğu Yöneticisi rol grubuyla *aynı çözüm izinlerine* sahip olur:

- Azure Active Directory *Yönetici*
- Azure Active Directory *Uyumluluk Yöneticisi*
- Microsoft 365 uyumluluk merkezi *Yönetimi*
- Microsoft 365 uyumluluk merkezi *Uyumluluk Yöneticisi*

> [!IMPORTANT]
> İletişim Uyumluluğu veya İletişim Uyumluluğu Yöneticisi rol gruplarında her zaman  en az bir  kullanıcınız olduğundan emin olun (seçtiğiniz seçen bağlı olarak), iletişim uyumluluk yapılandırmanız belirli kullanıcılar kuruluşlarından ayrılırsa 'sıfır yönetici' senaryosuna uymaz.

İletişim uyumluluk ilkelerini ve uyarılarını nasıl yönetmek istediğinize bağlı olarak, farklı iletişim uyumluluk özellikleri kümelerini yönetmek için kullanıcıları belirli rol gruplarına atamanız gerekir. Farklı iletişim uyumluluk özellikleri alanlarını yönetmek için, farklı uyumluluk sorumluluklarına sahip kullanıcıları belirli rol gruplarına atama seçeneğiniz vardır. Ya da belirli yöneticiler, analistler, analistler ve izleyiciler için tüm kullanıcı hesaplarını İletişim Uyumluluğu *rol grubuna atamaya karar* veabilirsiniz. Uyumluluk yönetimi gereksinimlerinize en uygun şekilde tek bir rol grubu veya birden çok rol grubu kullanın.

İletişim uyumluluğunu yapılandıran ve yöneten şu çözüm rol grubu seçeneklerinden birini belirleyin:

|**Rol**|**Rol izinleri**|
|:-----|:-----|
| **İletişim Uyumluluğu** | Tek bir grupta, organizasyona iletişimi uyumluluğu yönetmek için bu rol grubunu kullanın. Belirlenen yöneticiler, analistler, analistler ve görüntüleyiciler için tüm kullanıcı hesaplarını ekleyerek, iletişim uyumluluk izinlerini tek bir grupta yapılandırabilirsiniz. Bu rol grubu tüm iletişim uyumluluğu izin rollerini içerir. bu yapılandırma, iletişim uyumluluğuyla hızlı bir şekilde çalışmaya başlamanın en kolay yoludur ve ayrı kullanıcı grupları için tanımlanmış ayrı izinlere ihtiyacı olan kuruluşlara iyi uyum sağlar. İletişim uyumluluk yöneticisi olarak ilkeler oluşturmaları için, posta kutularının Posta Kutusu'Exchange Online. |
| **İletişim Uyumluluğu Yöneticisi** | Bu rol grubunu ilk başta iletişim uyumluluğunu yapılandırmak ve daha sonra iletişim uyumluluk yöneticilerini tanımlı bir grup haline çekmek için kullanın. Bu rol grubuna atanan kullanıcılar, iletişim uyumluluk ilkelerini, genel ayarları ve rol grubu atamalarını oluşturabilir, okuyabilir, güncelleştirabilir ve silebilir. Bu rol grubuna atanan kullanıcılar ileti uyarılarını görüntüamaz. İletişim uyumluluk yöneticisi olarak ilkeler oluşturmaları için, posta kutularının Posta Kutusu'Exchange Online. |
| **İletişim Uyumluluğu Analisti** | İletişim uyumluluğu analistleri olarak görevecek kullanıcılara izin atamak için bu grubu kullanın. Bu rol grubuna atanmış olan kullanıcılar, Gözden Geçiren olarak atandığı ilkeleri iletiyi iletiyi gözden geçiricilerine gönderebilir (ileti içeriğine değil), ek gözden geçirenlere gönderebilir veya kullanıcılara bildirim gönderebilir. Analistler bekleyen uyarıları çözümleyemezse. |
| **İletişim Uyumluluğu Uyumluluk Uyumlulukları** | İletişim uyumluluğu uyumluluk uyumluluk uyumlulukları gibi davranacak kullanıcılara izinler atamak için bu grubu kullanın. Bu rol grubuna atanan kullanıcılar ileti meta verilerini ve içeriğini  neleri iletiyi gözden geçirenlere iletir, Advanced eDiscovery durumuna iyileştirmeyi, kullanıcılara bildirim gönderebilir ve uyarıyı çözebilir. |
| **İletişim Uyumluluğu Görüntüleyicisi** | İletişim raporlarını yönetecek kullanıcılara izin atamak için bu grubu kullanın. Bu rol grubuna atanan kullanıcılar, iletişim uyumluluğu giriş sayfasında tüm raporlama pencere öğelerine erişim sağlar ve tüm iletişim uyumluluk raporlarını  görebilirsiniz. |

### <a name="supervised-users"></a>Denetimli kullanıcılar

İletişim uyumluluğunu kullanmaya başlamadan önce, kimlerin iletişimlerinin gözden geçirn gerektiğini belirlemelisiniz. İlkede, kullanıcı e-posta adresleri denetleme için bireyleri veya grupları belirlemeyi sağlar. Bu gruplara bazı örnekler Microsoft 365 Grupları, Exchange tabanlı dağıtım listeleri, Yammer toplulukları ve diğer Microsoft Teams verilmiştir. Ayrıca, belirli kullanıcıları veya grupları belirli bir dışlama grubuyla veya bir grup listesiyle taramanın dışında tutabilirsiniz. İletişim uyumluluğu ilkelerinde desteklenen grup türleri hakkında daha fazla bilgi için bkz [. İletişim uyumluluğunu çalışmaya başlama](communication-compliance-configure.md#step-3-optional-set-up-groups-for-communication-compliance).

> [!IMPORTANT]
> İletişim uyumluluk ilkeleri kapsamındaki kullanıcıların bir Microsoft 365 E5 Uyumluluk lisansına, Gelişmiş Uyumluluk eklentisine sahip bir Office 365 Kurumsal E3 lisansına ya da bir Office 365 Kurumsal E5 aboneliğine dahil olması gerekir. Mevcut bir Enterprise E5 planınız yoksa ve iletişim uyumluluğunu denemek için [E5 deneme sürümüne Office 365 Kurumsal](https://go.microsoft.com/fwlink/p/?LinkID=698279).

### <a name="reviewers"></a>Gözden Geçirenler

Bir iletişim uyumluluk ilkesi  oluşturmak için, denetleme yapan kullanıcıların iletilerini gözden kimin gözden geçirildiklerine karar ve sonra da belirlemelisiniz. İlkede, kullanıcı e-posta adresleri denetlemeli iletişimleri gözden geçirecek bireyleri veya kişi gruplarını belirlemeyi sağlar. Gözden geçirenlerin tüm posta kutuları Exchange Online'de barındırılan posta kutularına sahip olmalı, İletişim Uyumluluğu Analisti'ne veya İletişim  Uyumluluğu Yasal Rolü rol gruplarına atanmalı ve incelemeleri gereken ilkeye atanmış olması gerekir. Gözden geçirenler bir ilkeye ekli olduğunda, otomatik olarak ilkeye atamayı haber veren ve gözden geçirme işlemiyle ilgili bilgilerin bağlantılarını veren bir e-posta iletisi alırlar.

### <a name="groups-for-supervised-users-and-reviewers"></a>Denetimli kullanıcılar ve gözden geçirenler için gruplar

Kurulumlarınızı basitleştirmek için, iletişimlerinin gözden geçirleştirilmesi gereken kişiler için gruplar ve bu iletişimleri gözden geçiren kişiler için gruplar oluşturun. Grupları kullanıyorsanız, birkaç gruba ihtiyacınız olabilir. Örneğin, iki farklı kişi grubu arasındaki iletişimi taramak veya denetlemeden denetlenen bir grup belirtmek istiyorsanız. İlkede bir Dağıtım grubu atadığınız zaman, ilke Dağıtım grubunda her kullanıcının tüm e-postalarını izler. İlkede bir Microsoft 365 atadığınız zaman, ilke her grup üyesinin aldığı e-postaları değil, o gruba gönderilen tüm e-postaları izler.

İletişim uyumluluk ilkelerine grup ve dağıtım listeleri eklemek genel koşullar ve kurallar kümesi içinde yer a desteklediği için, ilkenin desteklediği grup ve dağıtım listesi sayısı, ilkeye eklenen koşulların sayısına bağlı olarak değişir. Her ilke, ilkede var olan ek koşulların sayısına bağlı olarak yaklaşık 20 grubu veya dağıtım listelerini desteklemeli.

Aşağıdaki grafiği kullanarak, iletişim uyumluluk ilkeleri için organizasyonu grupları yapılandırmanıza yardımcı olun:

| **İlke Üyesi** | **Desteklenen Gruplar** | **Desteklenmeyen Gruplar** |
|:-----|:-----|:-----|
|Denetimli kullanıcılar <br> Dışlanan kullanıcılar | Dağıtım grupları <br> Microsoft 365 Grupları | Dinamik dağıtım grupları <br> İç içe dağıtım grupları <br> Posta özellikli güvenlik grupları <br> Microsoft 365 üyeliği olan gruplarla çalışma |
| Gözden Geçirenler | Yok | Dağıtım grupları <br> Dinamik dağıtım grupları <br> İç içe dağıtım grupları <br> Posta özellikli güvenlik grupları |

### <a name="privacy"></a>Gizlilik

İlke eşleşmesi olan kullanıcıların gizliliğini korumak önemlidir ve iletişim uyumluluğu uyarıları için veri araştırmasında ve çözümleme incelemesinde nesnenin daha yaygın korunmasına yardımcı olabilir. Bu ayar yalnızca iletişim uyumluluk çözümünün görüntü olduğu kullanıcı adları için geçerlidir. Bu, adların diğer uyumluluk çözümsinde veya yönetim merkezinde görüntülenmelerini etkilemez.

İletişim uyumluluğu eşleşmesi olan kullanıcılar için, İletişim uyumluluğu ayarları'nın aşağıdaki **ayarlardan birini seçebilirsiniz**:

- **Kullanıcı adlarının anonimleştirilmiş** sürümlerini gösterme: İletişim Uyumluluğu Analisti rol grubu kullanıcılarının ilke  uyarılarını kimlerle ilişkili olduğunu görmelerini önlemek için, kullanıcı adları anonimleştirilmiştir. İletişim Uyumluluğu Rol *grubunda yer* alan kullanıcılar her zaman anonimleştirilmiş sürümleri değil kullanıcı adlarını görebilirler. Örneğin, 'Grace Taylor' kullanıcısı iletişim uyumluluk deneyiminin tüm alanlarında rastgele takma adla ('AnonIS8-988' gibi) görünür. Bu ayarın seçimi, geçerli ve geçmiş ilke eşleşmeleri olan tüm kullanıcıları anonim olarak uygular ve tüm ilkelere uygulanır. İletişim uyumluluğu uyarı ayrıntılarında yer alan kullanıcı profili bilgileri, bu seçenek seçildikten sonra kullanılamaz. Bununla birlikte, var olan ilkelere yeni kullanıcılar eklerken veya yeni ilkelere kullanıcı atarken kullanıcı adları görüntülenir. Bu ayarı kapatmayı seçerseniz, geçerli veya eski ilke eşleşmesi olan tüm kullanıcılar için kullanıcı adları görüntülenir.
- **Kullanıcı adlarının anonimleştirilmiş sürümlerini** gösterme: İletişim uyumluluğu uyarıları için mevcut ve geçmiş ilke eşleşmelerinin tüm kullanıcı adları görüntülenir. Tüm iletişim uyumluluk uyarıları için kullanıcı profil bilgileri (ad, unvan, diğer ad ve kuruluş veya bölüm) kullanıcı için görüntülenir.

## <a name="plan-for-policies"></a>İlkeleri planlama

uygunsuz içerik, hassas bilgiler ve mevzuat uyumluluğu için önceden tanımlanmış [şablonlarla](communication-compliance-policies.md#policy-templates) iletişim uyumluluk ilkeleri oluşturmak hızlı ve kolaydır. Özel iletişim uyumluluğu ilkeleri, organizasyonunıza ve gereksinimlerinize özgü sorunları algılama ve soruşturma esnekliği sağlar.

İletişim uyumluluğu ilkelerini planlarken aşağıdaki alanları dikkate alın:

- İletişim uyumluluk ilkeleriniz için, kuruluş kapsamındaki tüm kullanıcıları eklemeyi göz önünde bulundurabilirsiniz. Belirli kullanıcıları tek tek ilkeler için kapsam içinde belirlemek bazı durumlarda yararlı olur, ancak çoğu kuruluş tüm kullanıcıları taciz veya algılama için iyileştirilmiş iletişim uyumluluk ilkelerine dahilmalıdır.
- İlkelerin, sizin için iletişimle ilgili tüm sorunları yakalayacak şekilde gözden geçirlecek iletişim yüzdesini %100 oranında yapılandırabilirsiniz.
- Üçüncü taraf kaynaklarından [gelen iletişimleri, kendi](communication-compliance-channels.md#third-party-sources) iş yeri veya kuruluş içinde posta kutularına aktarılan Microsoft 365 tarayabilirsiniz. Bu platformlarda iletişimlerin gözden geçirmesini eklemek için, ileti toplantı ilkesi koşulları iletişim ilkesi tarafından izlenmeden önce bu hizmetlere bir bağlayıcı yapılandırmanız gerekir.
- İlkeler, özel iletişim uyumluluk ilkelerinde İngilizce dışında izleme dillerini desteklemektedir. Istediğiniz dilde [rahatsız edici sözcükler içeren](communication-compliance-policies.md#custom-keyword-dictionaries) bir özel anahtar sözcük sözlüğü oluşturabilir veya aynı Microsoft 365'de eğitilebilir sınıflayıcıları kullanarak [](classifier-get-started-with.md) kendi makine öğrenme modelinizi oluşturabilirsiniz.
- Tüm kuruluşların farklı iletişim standartları ve ilke ihtiyaçları vardır. İletişim uyumluluğu ilkesi koşullarını kullanarak belirli anahtar [sözcükleri takip edin veya](communication-compliance-policies.md#conditional-settings) özel hassas bilgi türleriyle belirli [bilgi türlerini takip edin](create-a-custom-sensitive-information-type.md).

## <a name="creating-a-communication-compliance-policy-walkthrough"></a>İletişim uyumluluğu ilkesi adım adım oluşturma

Yeni bir iletişim uyumluluk ilkesi ayarlama ve uyarı düzeltme hakkında ayrıntılı bir yol mu görmeksiniz? İletişim uyumluluk ilkelerinin uygunsuz iletileri algılamanıza, olası ihlalleri araştırmanıza ve uyumluluk sorunlarını düzeltmeye nasıl yardımcı olduğunu göstermeyi görmek için aşağıdaki 15 dakikalık videoyu izleyin.
<br>
<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RWNchy]
<br>

## <a name="ready-to-get-started"></a>Başlamaya hazır mısınız?

Microsoft 365'nizin iletişim uyumluluğunu yapılandırmak için, [Microsoft 365](communication-compliance-configure.md) için iletişim uyumluluğunu yapılandırma'ya bakın veya [Contoso](communication-compliance-case-study.md) için örnek olay incelemesini ve Microsoft Teams'te uygunsuz içeriği izlemek üzere bir iletişim uyumluluk ilkesi nasıl yapılandırıldılarına bakın. Exchange Online ve iletişim Yammer.
