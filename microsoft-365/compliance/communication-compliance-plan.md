---
title: İletişim uyumluluğu planı
description: Kuruluşunuzda iletişim uyumluluğunu kullanmayı planlama hakkında bilgi edinin.
keywords: Microsoft 365, Microsoft Purview, uyumluluk, iletişim uyumluluğu
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
ms.openlocfilehash: c0644f72e702a774ab95a7db8e6ae581edfd3377
ms.sourcegitcommit: c216ffa5da8f431e4380bb133a234ae7d94144c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2022
ms.locfileid: "65892548"
---
# <a name="plan-for-communication-compliance"></a>İletişim uyumluluğu planı

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Kuruluşunuzda [iletişim uyumluluğunu](communication-compliance.md) kullanmaya başlamadan önce, bilgi teknolojisi ve uyumluluk yönetimi ekipleriniz tarafından gözden geçirilmesi gereken önemli planlama etkinlikleri ve dikkat edilmesi gereken noktalar vardır. Aşağıdaki alanlarda dağıtımı ayrıntılı bir şekilde anlamak ve planlamak, iletişim uyumluluk özelliklerini uygulama ve kullanımınızın sorunsuz bir şekilde ilerlemesini ve çözüm için en iyi yöntemlerle uyumlu olmasını sağlamaya yardımcı olur.

Daha fazla bilgi edinmek ve kuruluşunuzdaki uyumluluk ve riskli etkinlikleri ele almak için planlama sürecine genel bakış için bkz. [Insider risk yönetimi programı başlatma](https://download.microsoft.com/download/b/2/0/b208282a-2482-4986-ba07-15a9b9286df0/pwc-starting-an-insider-risk-management-program-with-pwc-and-microsoft.pdf).

Ayrıca, kuruluşunuzdaki kullanıcıların veri risklerini en aza indirmeye yardımcı olmak için insider risk yönetimi ve iletişim uyumluluğunun birlikte nasıl çalıştığına ilişkin [Microsoft Mechanics videosunu](https://www.youtube.com/watch?v=Ynkfu8OF0wQ) da gözden geçirin.

> [!IMPORTANT]
> İletişim uyumluluğu şu anda coğrafi bölgelerde ve Azure hizmet bağımlılıkları tarafından desteklenen ülkelerde barındırılan kiracılarda kullanılabilir. Kuruluşunuzda iletişim uyumluluğunu desteklediğini doğrulamak için bkz. [Ülkeye/bölgeye göre Azure bağımlılığı kullanılabilirliği](/troubleshoot/azure/general/dependency-availability-by-country).

## <a name="transitioning-from-supervision-in-office-365"></a>Office 365'te Denetimden Geçiş

Office 365'te denetim ilkeleri kullanan kuruluşlar için, Microsoft Purview'da iletişim uyumluluk ilkelerine geçişi hemen planlamanız ve şu önemli noktaları anlamanız gerekir:

- Office 365'teki denetim çözümünün yerini Microsoft Purview'daki iletişim uyumluluk çözümü almıştır. Yeni araştırma ve düzeltme iyileştirmelerini kullanmak için iletişim uyumluluğunda mevcut denetim ilkeleriyle aynı ayarlara sahip yeni ilkeler oluşturmanızı öneririz.
- Office 365 ilke eşleşmelerinde denetimde kaydedilen iletiler iletişim uyumluluğuna taşınamaz veya paylaşılamaz.
- Geçiş işlemi sırasında her iki çözümü de yan yana kullanan kuruluşlar için, her çözümde kullanılan ilkelerin benzersiz ilke adları olmalıdır. Gruplar ve özel anahtar sözcük sözlükleri, geçiş döneminde çözümler arasında paylaşılabilir.

Office 365'te denetim için kullanımdan kaldırma bilgileri için ayrıntılar için [Microsoft 365 Yol Haritası'na](https://www.microsoft.com/microsoft-365/roadmap) bakın.

## <a name="work-with-stakeholders-in-your-organization"></a>Kuruluşunuzdaki paydaşlarla çalışma

İletişim uyumluluğu uyarılarında eylem gerçekleştirmeye yönelik işbirliği yapmak için kuruluşunuzdaki uygun paydaşları belirleyin. İlk planlama ve uçtan uca [iletişim uyumluluğu iş akışı](communication-compliance.md#workflow) dahil olmak üzere dikkate alınması önerilen bazı paydaşlar, kuruluşunuzun aşağıdaki alanlarından kişilerdir:

- Bilgi teknolojisi
- Uyumluluk
- Gizlilik
- Güvenlik
- İnsan kaynakları
- Yasal

## <a name="plan-for-the-investigation-and-remediation-workflow"></a>Araştırma ve düzeltme iş akışını planlama

### <a name="permissions"></a>İzinler

[Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com/) düzenli aralıklarla uyarıları ve servis taleplerini izlemek ve gözden geçirmek için ayrılmış paydaşları seçin. Kullanıcıları ve paydaşları kuruluşunuzdaki farklı iletişim uyumluluğu rol gruplarına nasıl atayabileceğinizi anladığınızdan emin olun.

> [!IMPORTANT]
> Rol gruplarınızı yapılandırdıktan sonra, rol grubu izinlerinin kuruluşunuz genelinde atanan kullanıcılara uygulanması 30 dakika kadar sürebilir.

İletişim uyumluluk özelliklerini yönetmek için ilk izinleri yapılandırmak için kullanılan altı rol grubu vardır. **İletişim uyumluluğunu** Microsoft Purview uyumluluk portalında menü seçeneği olarak kullanılabilir hale getirmek ve bu yapılandırma adımlarına devam etmek için aşağıdaki rol veya rol gruplarından birine atanmalısınız:

- Azure Active Directory [*Genel Yönetici*](/azure/active-directory/roles/permissions-reference#global-administrator) rolü
- Azure Active Directory [*Uyumluluk Yöneticisi*](/azure/active-directory/roles/permissions-reference#compliance-administrator) rolü
- Microsoft Purview uyumluluk portalı [*Kuruluş Yönetimi*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) rol grubu
- Microsoft Purview uyumluluk portalı [*Uyumluluk Yöneticisi*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) rol grubu
- *İletişim Uyumluluğu* rol grubu
- *İletişim Uyumluluğu Yöneticisi* rol grubu

Aşağıdaki rollerin üyeleri *, İletişim Uyumluluğu Yöneticisi* rol grubuna dahil edilen çözüm izinlerine sahiptir:

- Azure Active Directory *Genel Yöneticisi*
- Azure Active Directory *Uyumluluk Yöneticisi*
- Microsoft Purview uyumluluk portalı *Kuruluş Yönetimi*
- Microsoft Purview uyumluluk portalı *Uyumluluk Yöneticisi*

> [!IMPORTANT]
> İletişim *uyumluluk* yapılandırmanızın kuruluşunuzdan ayrılması durumunda iletişim uyumluluk yapılandırmanızın 'sıfır yönetici' senaryosunda yer almaması için İletişim *Uyumluluğu veya İletişim Uyumluluğu Yöneticisi* rol gruplarında her zaman en az bir kullanıcınız olduğundan emin olun (belirlediğiniz seçeneğe bağlı olarak).

İletişim uyumluluk ilkelerini ve uyarılarını nasıl yönetmek istediğinize bağlı olarak, farklı iletişim uyumluluk özellikleri kümelerini yönetmek için kullanıcıları belirli rol gruplarına atamanız gerekir. Farklı uyumluluk özellikleri alanlarını yönetmek için farklı uyumluluk sorumluluklarına sahip kullanıcıları belirli rol gruplarına atama seçeneğiniz vardır. Ya da belirlenen yöneticiler, analistler, araştırmacılar ve görüntüleyiciler için tüm kullanıcı hesaplarını *İletişim Uyumluluğu* rol grubuna atamaya karar vekleyebilirsiniz. Uyumluluk yönetimi gereksinimlerinize en uygun tek bir rol grubu veya birden çok rol grubu kullanın.

İletişim uyumluluğunu yapılandırırken ve yönetirken şu çözüm rol grubu seçeneklerinden birini belirleyin:

|**Rol**|**Rol izinleri**|
|:-----|:-----|
| **İletişim Uyumluluğu** | Kuruluşunuz için iletişim uyumluluğunu tek bir grupta yönetmek için bu rol grubunu kullanın. Belirlenen yöneticiler, analistler, araştırmacılar ve görüntüleyiciler için tüm kullanıcı hesaplarını ekleyerek, iletişim uyumluluk izinlerini tek bir grupta yapılandırabilirsiniz. Bu rol grubu tüm iletişim uyumluluk izni rollerini içerir. Bu yapılandırma, iletişim uyumluluğunu hızlı bir şekilde kullanmaya başlamanın en kolay yoludur ve ayrı kullanıcı grupları için ayrı izinlere ihtiyaç duymayan kuruluşlar için uygundur. İletişim uyumluluk yöneticisi olarak ilke oluşturan kullanıcıların posta kutuları Exchange Online'da barındırılmalıdır. |
| **İletişim Uyumluluğu Yöneticisi** | İletişim uyumluluğunu başlangıçta yapılandırmak ve daha sonra iletişim uyumluluk yöneticilerini tanımlı bir gruba ayırmak için bu rol grubunu kullanın. Bu rol grubuna atanan kullanıcılar iletişim uyumluluk ilkelerini, genel ayarları ve rol grubu atamalarını oluşturabilir, okuyabilir, güncelleştirebilir ve silebilir. Bu rol grubuna atanan kullanıcılar ileti uyarılarını görüntüleyemez. İletişim uyumluluk yöneticisi olarak ilke oluşturan kullanıcıların posta kutuları Exchange Online'da barındırılmalıdır. |
| **İletişim Uyumluluğu Analisti** | İletişim uyumluluğu analistleri olarak görev yapacak kullanıcılara izin atamak için bu grubu kullanın. Bu rol grubuna atanan kullanıcılar, Gözden Geçiren olarak atandıkları ilkeleri görüntüleyebilir, ileti meta verilerini görüntüleyebilir (ileti içeriği değil), ek gözden geçirenlere iletebilir veya kullanıcılara bildirim gönderebilir. Analistler bekleyen uyarıları çözümleyemez. |
| **İletişim Uyumluluğu Araştırmacısı** | İletişim uyumluluk araştırmacısı olarak görev yapacak kullanıcılara izin atamak için bu grubu kullanın. Bu rol grubuna atanan kullanıcılar ileti meta verilerini ve içeriğini görüntüleyebilir, ek gözden geçirenlere iletebilir, eBulma (Premium) olayına iletebilir, kullanıcılara bildirim gönderebilir ve uyarıyı çözebilir. |
| **İletişim Uyumluluğu Görüntüleyicisi** | İletişim raporlarını yönetecek kullanıcılara izin atamak için bu grubu kullanın. Bu rol grubuna atanan kullanıcılar, iletişim uyumluluğu giriş sayfasındaki tüm raporlama pencere öğelerine erişebilir ve tüm iletişim uyumluluk raporlarını görüntüleyebilir. |

### <a name="supervised-users"></a>Denetimli kullanıcılar

İletişim uyumluluğunu kullanmaya başlamadan önce kimlerin iletişimlerinin gözden geçirilmesi gerektiğini belirlemeniz gerekir. İlkede, kullanıcı e-posta adresleri denetlenecek kişileri veya kişi gruplarını tanımlar. Bu gruplara örnek olarak Microsoft 365 Grupları, Exchange tabanlı dağıtım listeleri, Yammer toplulukları ve Microsoft Teams kanalları verilebilir. Ayrıca belirli kullanıcıları veya grupları belirli bir dışlama grubu veya grup listesiyle taramanın dışında tutabilirsiniz. İletişim uyumluluk ilkelerinde desteklenen grup türleri hakkında daha fazla bilgi için bkz. [İletişim uyumluluğunu kullanmaya başlama](communication-compliance-configure.md#step-3-optional-set-up-groups-for-communication-compliance).

> [!IMPORTANT]
> İletişim uyumluluk ilkeleri kapsamındaki kullanıcıların Microsoft 365 E5 Uyumluluk lisansına, Gelişmiş Uyumluluk eklentisine sahip bir Office 365 Kurumsal E3 lisansına sahip olması veya office 365 Kurumsal E5 aboneliğine dahil edilmesi gerekir. Mevcut bir Kurumsal E5 planınız yoksa ve iletişim uyumluluğunu denemek istiyorsanız [, Office 365 Kurumsal E5 deneme sürümüne kaydolabilirsiniz](https://go.microsoft.com/fwlink/p/?LinkID=698279).

### <a name="reviewers"></a>Yorumcu -lar

İletişim uyumluluk ilkesi oluşturduğunuzda, denetimli kullanıcıların iletilerini kimin gözden geçireceğini belirlemeniz gerekir. İlkede, kullanıcı e-posta adresleri denetimli iletişimleri gözden geçirmek için kişileri veya kişi gruplarını tanımlar. Tüm gözden geçirenlerin Exchange Online'da barındırılan posta kutuları olmalıdır, *İletişim Uyumluluk Analisti* veya *İletişim Uyumluluğu Araştırmacısı* rol gruplarına atanmalıdır ve araştırılması gereken ilkede atanmalıdır. Gözden geçirenler bir ilkeye eklendiğinde, ilkeye atamayı bildiren ve gözden geçirme işlemiyle ilgili bilgilerin bağlantılarını sağlayan bir e-posta iletisini otomatik olarak alır.

### <a name="groups-for-supervised-users-and-reviewers"></a>Denetimli kullanıcılar ve gözden geçirenler için gruplar

Kurulumunuzu basitleştirmek için, iletişimlerinin gözden geçirilmesi gereken kişiler için gruplar ve bu iletişimleri gözden geçiren kişiler için gruplar oluşturun. Grupları kullanıyorsanız, birkaç gruba ihtiyacınız olabilir. Örneğin, iki ayrı kişi grubu arasındaki iletişimleri taramak veya denetimli olmayan bir grup belirtmek istiyorsanız. İlkede bir Dağıtım grubu atadığınızda, ilke Dağıtım grubundaki her kullanıcıdan gelen tüm e-postaları izler. İlkeye bir Microsoft 365 grubu atadığınızda, ilke her grup üyesi tarafından alınan tek tek e-postaları değil, o gruba gönderilen tüm e-postaları izler.

İletişim uyumluluk ilkelerine grup ve dağıtım listeleri eklemek, genel koşulların ve kuralların bir parçasıdır, bu nedenle bir ilkenin desteklediği en fazla grup ve dağıtım listesi sayısı, ilkeye eklenen koşulların sayısına bağlı olarak değişir. her ilke, ilkede bulunan ek koşulların sayısına bağlı olarak yaklaşık 20 grubu veya dağıtım listesini desteklemelidir.

Kuruluşunuzdaki grupları iletişim uyumluluk ilkeleri için yapılandırmanıza yardımcı olması için aşağıdaki grafiği kullanın:

| **İlke Üyesi** | **Desteklenen Gruplar** | **Desteklenmeyen Gruplar** |
|:-----|:-----|:-----|
|Denetimli kullanıcılar <br> Dışlanan kullanıcılar | Dağıtım grupları <br> Microsoft 365 Grupları | Dinamik dağıtım grupları <br> İç içe dağıtım grupları <br> Posta özellikli güvenlik grupları <br> Dinamik üyeliği olan Microsoft 365 grupları |
| Yorumcu -lar | Yok | Dağıtım grupları <br> Dinamik dağıtım grupları <br> İç içe dağıtım grupları <br> Posta özellikli güvenlik grupları |

### <a name="privacy"></a>Gizlilik

İlke eşleşmeleri olan kullanıcıların gizliliğini korumak önemlidir ve iletişim uyumluluğu uyarıları için veri araştırma ve analiz incelemelerinde nesnelliği artırmaya yardımcı olabilir. Bu ayar yalnızca iletişim uyumluluk çözümünü görüntüleyen kullanıcı adları için geçerlidir. Adların diğer uyumluluk çözümlerinde veya yönetim merkezinde nasıl görüntüleneceğini etkilemez.

İletişim uyumluluğu eşleşmesi olan kullanıcılar için İletişim **uyumluluk** ayarları'nda aşağıdaki ayarlardan birini seçebilirsiniz:

- **Kullanıcı adlarının anonimleştirilmiş sürümlerini göster**: *İletişim Uyumluluğu Analisti* rol grubundaki kullanıcıların ilke uyarılarıyla ilişkili kimleri görmesini önlemek için kullanıcı adları anonimleştirilir. *İletişim Uyumluluk Araştırmacısı* rol grubundaki kullanıcılar anonimleştirilmiş sürümleri değil, her zaman kullanıcı adlarını görür. Örneğin, iletişim uyumluluk deneyiminin tüm alanlarında 'AnonIS8-988' gibi rastgele bir takma adla 'Grace Taylor' kullanıcısı görünür. Bu ayarın seçilmesi, geçerli ve geçmiş ilke eşleşmeleri olan tüm kullanıcıları anonim hale getirir ve tüm ilkeler için geçerlidir. İletişim uyumluluğu uyarı ayrıntılarındaki kullanıcı profili bilgileri, bu seçenek seçildiğinde kullanılamaz. Ancak, mevcut ilkelere yeni kullanıcılar eklenirken veya yeni ilkelere kullanıcı atanırken kullanıcı adları görüntülenir. Bu ayarı kapatmayı seçerseniz, geçerli veya geçmiş ilke eşleşmeleri olan tüm kullanıcılar için kullanıcı adları görüntülenir.
- **Kullanıcı adlarının anonimleştirilmiş sürümlerini gösterme**: İletişim uyumluluk uyarıları için geçerli ve geçmiş tüm ilke eşleşmeleri için kullanıcı adları görüntülenir. Kullanıcı profili bilgileri (ad, başlık, diğer ad ve kuruluş veya departman) tüm iletişim uyumluluk uyarıları için kullanıcı için görüntülenir.

## <a name="plan-for-policies"></a>İlkeleri planlama

Uygunsuz içerik, hassas bilgiler ve mevzuat uyumluluğu için [önceden tanımlanmış şablonlarla](communication-compliance-policies.md#policy-templates) iletişim uyumluluk ilkeleri oluşturmak hızlı ve kolaydır. Özel iletişim uyumluluk ilkeleri, kuruluşunuza ve gereksinimlerinize özgü sorunları algılama ve araştırma esnekliği sağlar.

İletişim uyumluluk ilkelerini planlarken aşağıdaki alanları göz önünde bulundurun:

- kuruluşunuzdaki tüm kullanıcıları iletişim uyumluluk ilkelerinizin kapsamına eklemeyi göz önünde bulundurun. Belirli kullanıcıları tek tek ilkeler için kapsam dahilinde belirlemek bazı durumlarda yararlıdır, ancak çoğu kuruluş tüm kullanıcıları taciz veya ayrımcılık algılama için iyileştirilmiş iletişim uyumluluk ilkelerine dahil etmelidir.
- İlkelerin kuruluşunuza yönelik iletişimlerdeki tüm sorunları yakalamasını sağlamak için iletişim yüzdesini %100'de gözden geçirecek şekilde yapılandırın.
- Microsoft 365 kuruluşunuzdaki posta kutularına aktarılan veriler için [üçüncü taraf kaynaklardan gelen iletişimleri](communication-compliance-channels.md#third-party-sources) tarayabilirsiniz. Bu platformlardaki iletişimlerin gözden geçirilmesini eklemek için, ilke koşullarını karşılayan iletiler iletişim ilkesi tarafından izlenmeden önce bu hizmetlere bir bağlayıcı yapılandırmanız gerekir.
- İlkeler, özel iletişim uyumluluk ilkelerinde İngilizce dışındaki izleme dillerini destekleyebilir. Microsoft 365'te [eğitilebilir sınıflandırıcıları](classifier-get-started-with.md) kullanarak dilediğiniz dilde rahatsız edici sözcüklerden oluşan [özel bir anahtar sözcük sözlüğü](communication-compliance-policies.md#custom-keyword-dictionaries) oluşturun veya kendi makine öğrenmesi modelinizi oluşturun.
- Tüm kuruluşların farklı iletişim standartları ve ilke gereksinimleri vardır. İletişim uyumluluk [ilkesi koşullarını](communication-compliance-policies.md#conditional-settings) kullanarak belirli anahtar sözcükleri izleyin veya [özel hassas bilgi türleriyle belirli bilgi türlerini](create-a-custom-sensitive-information-type.md) izleyin.

## <a name="creating-a-communication-compliance-policy-walkthrough"></a>İletişim uyumluluk ilkesi oluşturma kılavuzu

Yeni bir iletişim uyumluluk ilkesi ayarlama ve uyarıyı düzeltme konusunda ayrıntılı bir izlenecek yol görmek ister misiniz? İletişim uyumluluk ilkelerinin uygunsuz iletileri algılamanıza, olası ihlalleri araştırmanıza ve uyumluluk sorunlarını düzeltmenize nasıl yardımcı olabileceğini gösteren bir tanıtım görmek için aşağıdaki 15 dakikalık videoya göz atın.
<br>
<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RWNchy]
<br>

## <a name="ready-to-get-started"></a>Başlamaya hazır mısınız?

Microsoft 365 kuruluşunuz için iletişim uyumluluğunu yapılandırmak için bkz. [İletişim uyumluluğunu yapılandırma](communication-compliance-configure.md) veya [Contoso için örnek olay incelemesine](communication-compliance-case-study.md) ve Microsoft Teams, Exchange Online ve Yammer iletişimlerinde uygunsuz içeriği izlemek için iletişim uyumluluk ilkesini nasıl hızlı bir şekilde yapılandırdıklarını gözden geçirin.
