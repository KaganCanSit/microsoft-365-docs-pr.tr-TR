---
title: İletişim uyumluluğu ile kanal sinyallerini tespit etme
description: İletişim uyumluluğu ile kanal sinyallerini algılama hakkında daha fazla bilgi edinin.
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
ms.openlocfilehash: 0769dd3cfd64f611162803952a1e39b9241ac2ad
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638686"
---
# <a name="detect-channel-signals-with-communication-compliance"></a>İletişim uyumluluğu ile kanal sinyallerini tespit etme

İletişim uyumluluk ilkeleriyle, aşağıdaki iletişim platformlarından bir veya daha fazlasında iletileri grup veya tek başına kaynak olarak taramayı seçebilirsiniz. Bu platformlarda yakalanan özgün iletiler, kuruluşunuzun [saklama ve saklama ilkelerine](/microsoft-365/compliance/information-governance) uygun olarak özgün platform konumunda tutulur. İletişim uyumluluk ilkeleri tarafından analiz ve araştırma için kullanılan iletilerin kopyaları, kullanıcılar kuruluşunuzdan ayrılsa ve posta kutuları silinse bile, ilke olduğu sürece saklanır. bir iletişim ilkesi silindiğinde, ilkeyle ilişkili iletilerin kopyaları da silinir.

## <a name="microsoft-teams"></a>Microsoft Teams

Hem genel hem de özel Microsoft Teams kanallarında ve tek tek sohbetlerde sohbet iletişimleri taranabilir. Kullanıcılar, Microsoft Teams kapsamı seçiliyken bir iletişim uyumluluk ilkesine atandığında, kullanıcıların üyesi olduğu tüm Microsoft Teams'de kullanıcılara yönelik sohbet iletişimleri otomatik olarak izlenir. Microsoft Teams kapsamı, önceden tanımlanmış ilke şablonlarına otomatik olarak eklenir ve özel ilke şablonunda varsayılan olarak seçilir. İletişim uyumluluk ilkesi koşullarıyla eşleşen Teams sohbetlerinin işlenmesi 48 saat kadar sürebilir.

Özel sohbet ve özel kanallar için iletişim uyumluluk ilkeleri [Paylaşılan Kanallar'ı](/MicrosoftTeams/shared-channels) ve Modern ek taramasını destekler. Teams'de Paylaşılan Kanallar desteği otomatik olarak işlenir ve ek iletişim uyumluluk yapılandırması değişiklikleri gerektirmez. Aşağıdaki tabloda Teams kanallarını gruplar ve kullanıcılarla paylaşırken iletişim uyumluluğu davranışı özetlenmiştir:

|**Senaryo**|**İletişim uyumluluğu davranışı**|
|:-----------|:------------------------------------|
| **Kanalı bir iç ekiple paylaşma** | İletişim uyumluluk ilkeleri, kapsam içi kullanıcılar ve paylaşılan kanaldaki tüm iletiler için geçerlidir |
| **Dış ekiple kanal paylaşma** | İletişim uyumluluk ilkeleri, iç kuruluş için paylaşılan kanaldaki dahili kapsam içi kullanıcılar ve iletiler için geçerlidir |

Modern ekler, Teams iletilerine dahil edilen [OneDrive](/onedrive/plan-onedrive-enterprise#modern-attachments) veya [SharePoint](/sharepoint/dev/solution-guidance/modern-experience-customizations) sitelerinden alınan dosyalardır. Otomatik işleme ve etkin iletişim uyumluluk ilkesi koşulları ve sınıflandırıcılarla olası eşleşmeler için bu eklerden metin otomatik olarak ayıklanır. Modern ek algılama ve işleme için gerekli ek yapılandırma yoktur. Metin yalnızca ilke koşullarıyla eşleşen ekler için ayıklanır. İlke eşleşmesi olan iletilere yönelik ekler için, ekin bir ilke eşleşmesi de olsa metin ayıklanmamıştır.

Modern ek taraması aşağıdaki dosya türleri için desteklenir:

- Microsoft Word (.docx)
- Microsoft Excel (.xlsx)
- Microsoft PowerPoint (.pptx)
- Metin (.txt)
- Taşınabilir Belge Biçimi (.pdf)

Modern ekler için ayıklanan metin, bir ilkenin **Bekleyen** uyarılar panosundaki ilişkili iletiye eklenir. Ek için ayıklanan metin, ek dosya adı (ve biçim uzantısı) ve .txt uzantısı olarak adlandırılır. Örneğin, *ContosoBusinessPlan.docx* adlı ek için ayıklanan metin, bir ilkenin **Bekleyen** uyarılar panosunda *ContosoBusinessPlan.docx.txt* olarak görünür.

*Kaynak* ve *Düz metin* görünümlerindeki ayrıntıları görüntülemek için ayıklanan ek metnini seçin. Gözden geçirdikten sonra, komut çubuğu denetimlerini kullanarak ek metnini çözümleyebilir veya üzerinde işlem yapabilirsiniz. Ayrıca, iletişim uyumluluğu gözden geçirme işleminin dışında gözden geçirmek üzere eki indirme seçeneğiniz de vardır.

Teams'de bireysel kullanıcı sohbetlerini ve kanal iletişimlerini denetlemek için aşağıdaki grup yönetimi yapılandırmalarını kullanın:

- **Teams sohbet iletişimleri için:** İletişim uyumluluk ilkesine tek tek kullanıcılar atayın veya bir [dağıtım grubu](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) atayın. Bu ayar, bire bir veya bire çok kullanıcı/sohbet ilişkileri içindir.
- **Teams Channel iletişimleri için:** Belirli bir kullanıcıyı içeren taramak istediğiniz her Microsoft Teams kanalını veya Microsoft 365 grubunu iletişim uyumluluk ilkesine atayın. Aynı kullanıcıyı diğer Microsoft Teams kanallarına veya Microsoft 365 gruplarına eklerseniz, bu yeni kanalları ve grupları iletişim uyumluluk ilkesine eklediğinizden emin olun. Kanalın herhangi bir üyesi bir ilke içinde denetimli bir kullanıcıysa ve *Gelen* yönü bir ilkede yapılandırılmışsa, kanal içinde gönderilen tüm iletiler gözden geçirilebilir ve olası ilke eşleşmeleri (kanaldaki kullanıcılar için bile açıkça denetlenmeyenler için). Örneğin, A Kullanıcısı bir kanalın sahibi veya üyesidir. B ve C Kullanıcısı aynı kanalın üyeleridir ve yalnızca A Kullanıcısını denetleyen uygunsuz içerik ilkesiyle eşleşen dili kullanır. Kullanıcı B ve C Kullanıcısı, uygunsuz içerik ilkesinde doğrudan denetlenmese bile kanal içindeki konuşmalar için ilke eşleşmeleri oluşturur. A Kullanıcısını içeren kanalın dışında yer alan B kullanıcısı ile C Kullanıcısı arasındaki teams konuşmaları, A Kullanıcısını içeren uygunsuz içerik ilkesine tabi olmaz. Kanalın diğer üyeleri açıkça denetlendiğinde kanal üyelerini denetimden çıkarmak için, ilgili iletişim uyumluluk ilkesinde *Gelen* iletişim yönü ayarını kapatın.
- **Karma e-posta ortamlarıyla Teams sohbet iletişimleri** için: İletişim uyumluluğu, şirket içi Exchange dağıtımına veya Microsoft Teams'i etkinleştirmiş bir dış e-posta sağlayıcısına sahip kuruluşlar için kullanıcılara yönelik sohbet iletilerini algılayabilir. İzlemesi için şirket içi veya dış posta kutuları olan kullanıcılar için bir dağıtım grubu oluşturmanız gerekir. İletişim uyumluluk ilkesi oluştururken, bu dağıtım grubunu ilke sihirbazında **Denetimli kullanıcılar ve gruplar** seçimi olarak atayacaksınız. Bulut tabanlı depolamayı etkinleştirme gereksinimleri ve sınırlamaları ve şirket içi kullanıcılar için Teams desteği hakkında daha fazla bilgi için bkz. [Şirket içi kullanıcılar için Teams sohbet verilerini arama](search-cloud-based-mailboxes-for-on-premises-users.md).

## <a name="exchange-email"></a>Exchange e-postası

Microsoft 365 veya Office 365 aboneliğinizin bir parçası olarak Exchange Online'da barındırılan posta kutularının tümü ileti taraması için uygundur. İletişim uyumluluk ilkesi koşullarıyla eşleşen Exchange e-posta iletilerinin ve eklerinin işlenmesi yaklaşık 24 saat sürebilir. İletişim uyumluluğu için desteklenen ek türleri [, Exchange posta akışı kuralı içerik denetimleri için desteklenen dosya türleriyle aynıdır](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection).

## <a name="yammer"></a>Yammer

Yammer topluluklarındaki özel iletiler, genel konuşmalar ve ilişkili ekler taranabilir. Kullanıcı, yammer'ı tanımlı bir kanal olarak içeren iletişim uyumluluk ilkesine eklendiğinde, kullanıcının üyesi olduğu tüm Yammer toplulukları arasındaki iletişimler tarama işlemine dahil edilir. İletişim uyumluluk ilkesi koşullarıyla eşleşen Yammer sohbetlerinin ve eklerinin işlenmesi 24 saat kadar sürebilir. 

Yammer iletişimlerini ve eklerini izlemek için iletişim uyumluluk ilkeleri için Yammer [Yerel Modda](/yammer/configure-your-yammer-network/overview-native-mode) olmalıdır. Yerel Modda, tüm Yammer kullanıcıları Azure Active Directory'de (AAD), tüm gruplar Office 365 Gruplar'dır ve tüm dosyalar SharePoint Online'da depolanır.

## <a name="third-party-sources"></a>Üçüncü taraf kaynaklar

Microsoft 365 kuruluşunuzdaki posta kutularına aktarılan verilerin iletişimlerini [Instant Bloomberg](archive-instant-bloomberg-data.md), [Slack](archive-slack-data.md), [Zoom](archive-zoommeetings-data.md), SMS ve diğerleri gibi üçüncü taraf kaynaklardan tarayabilirsiniz. İletişim uyumluluğunda desteklenen bağlayıcıların tam listesi için bkz. [Üçüncü taraf verilerini arşivle](archiving-third-party-data.md).

Bağlayıcıyı bir iletişim uyumluluk ilkesine atayabilmeniz için önce Microsoft 365 kuruluşunuz için bir üçüncü taraf bağlayıcı yapılandırmanız gerekir. İletişim uyumluluk ilkesi sihirbazının **Üçüncü Taraf Kaynaklar** bölümü yalnızca şu anda yapılandırılmış olan üçüncü taraf bağlayıcılarını görüntüler.
