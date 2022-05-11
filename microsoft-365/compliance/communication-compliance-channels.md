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
ms.openlocfilehash: 51cf52c4729a543130eac676b8732ccd2fe0a388
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65319088"
---
# <a name="detect-channel-signals-with-communication-compliance"></a>İletişim uyumluluğu ile kanal sinyallerini tespit etme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

İletişim uyumluluk ilkeleriyle, aşağıdaki iletişim platformlarından bir veya daha fazlasında iletileri grup veya tek başına kaynak olarak taramayı seçebilirsiniz. Bu platformlarda yakalanan özgün iletiler, kuruluşunuzun [saklama ve saklama ilkelerine](/microsoft-365/compliance/information-governance) uygun olarak özgün platform konumunda tutulur. İletişim uyumluluk ilkeleri tarafından analiz ve araştırma için kullanılan iletilerin kopyaları, kullanıcılar kuruluşunuzdan ayrılsa ve posta kutuları silinse bile, ilke olduğu sürece saklanır. bir iletişim ilkesi silindiğinde, ilkeyle ilişkili iletilerin kopyaları da silinir.

## <a name="microsoft-teams"></a>Microsoft Teams

Hem genel hem de özel Microsoft Teams kanallarındaki sohbet iletişimleri ve tek tek sohbetler taranabilir. Kullanıcılar, Microsoft Teams kapsamı seçili bir iletişim uyumluluk ilkesine atandığında, kullanıcıların üyesi olduğu tüm Microsoft Teams kullanıcılara yönelik sohbet iletişimleri otomatik olarak izlenir. Microsoft Teams kapsamı, önceden tanımlanmış ilke şablonlarına otomatik olarak eklenir ve özel ilke şablonunda varsayılan olarak seçilir. Teams iletişim uyumluluk ilkesi koşullarıyla eşleşen sohbetlerin işlenmesi 48 saate kadar sürebilir.

Özel sohbet ve özel kanallar için iletişim uyumluluk ilkeleri [Paylaşılan Kanallar'ı](/MicrosoftTeams/shared-channels) ve Modern ek taramasını destekler. Teams'daki Paylaşılan Kanallar desteği otomatik olarak işlenir ve ek iletişim uyumluluk yapılandırması değişiklikleri gerektirmez. Aşağıdaki tabloda, gruplar ve kullanıcılarla Teams kanalları paylaşırken iletişim uyumluluğu davranışı özetlemektedir:

|**Senaryo**|**İletişim uyumluluğu davranışı**|
|:-----------|:------------------------------------|
| **Kanalı bir iç ekiple paylaşma** | İletişim uyumluluk ilkeleri, kapsam içi kullanıcılar ve paylaşılan kanaldaki tüm iletiler için geçerlidir |
| **Dış ekiple kanal paylaşma** | İletişim uyumluluk ilkeleri, iç kuruluş için paylaşılan kanaldaki dahili kapsam içi kullanıcılar ve iletiler için geçerlidir |

Modern ekler, Teams iletilerde yer alan [OneDrive](/onedrive/plan-onedrive-enterprise#modern-attachments) veya [SharePoint](/sharepoint/dev/solution-guidance/modern-experience-customizations) sitelerden alınan dosyalardır. Otomatik işleme ve etkin iletişim uyumluluk ilkesi koşulları ve sınıflandırıcılarla olası eşleşmeler için bu eklerden metin otomatik olarak ayıklanır. Modern ek algılama ve işleme için gerekli ek yapılandırma yoktur. Metin yalnızca ilke koşullarıyla eşleşen ekler için ayıklanır. İlke eşleşmesi olan iletilere yönelik ekler için, ekin bir ilke eşleşmesi de olsa metin ayıklanmamıştır.

Modern ek taraması aşağıdaki dosya türleri için desteklenir:

- Microsoft Word (.docx)
- Microsoft Excel (.xlsx)
- Microsoft PowerPoint (.pptx)
- Metin (.txt)
- Taşınabilir Belge Biçimi (.pdf)

Modern ekler için ayıklanan metin, bir ilkenin **Bekleyen** uyarılar panosundaki ilişkili iletiye eklenir. Ek için ayıklanan metin, ek dosya adı (ve biçim uzantısı) ve .txt uzantısı olarak adlandırılır. Örneğin, *ContosoBusinessPlan.docx* adlı ek için ayıklanan metin, bir ilkenin **Bekleyen** uyarılar panosunda *ContosoBusinessPlan.docx.txt* olarak görünür.

*Kaynak* ve *Düz metin* görünümlerindeki ayrıntıları görüntülemek için ayıklanan ek metnini seçin. Gözden geçirdikten sonra, komut çubuğu denetimlerini kullanarak ek metnini çözümleyebilir veya üzerinde işlem yapabilirsiniz. Ayrıca, iletişim uyumluluğu gözden geçirme işleminin dışında gözden geçirmek üzere eki indirme seçeneğiniz de vardır.

Teams'da tek tek kullanıcı sohbetlerini ve kanal iletişimlerini denetlemek için aşağıdaki grup yönetimi yapılandırmalarını kullanın:

- **Teams sohbet iletişimleri için:** İletişim uyumluluk ilkesine tek tek kullanıcılar atayın veya bir [dağıtım grubu](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) atayın. Bu ayar, bire bir veya bire çok kullanıcı/sohbet ilişkileri içindir.
- **Teams Kanal iletişimleri için:** Belirli bir kullanıcıyı içeren taramak istediğiniz her Microsoft Teams kanalı veya Microsoft 365 grubunu iletişim uyumluluk ilkesine atayın. Aynı kullanıcıyı diğer Microsoft Teams kanallarına veya Microsoft 365 gruplarına eklerseniz, bu yeni kanalları ve grupları iletişim uyumluluk ilkesine eklediğinizden emin olun. Kanalın herhangi bir üyesi bir ilke içinde denetimli bir kullanıcıysa ve *Gelen* yönü bir ilkede yapılandırılmışsa, kanal içinde gönderilen tüm iletiler gözden geçirilebilir ve olası ilke eşleşmeleri (kanaldaki kullanıcılar için bile açıkça denetlenmeyenler için). Örneğin, A Kullanıcısı bir kanalın sahibi veya üyesidir. B ve C Kullanıcısı aynı kanalın üyeleridir ve yalnızca A Kullanıcısını denetleyen uygunsuz içerik ilkesiyle eşleşen dili kullanır. Kullanıcı B ve C Kullanıcısı, uygunsuz içerik ilkesinde doğrudan denetlenmese bile kanal içindeki konuşmalar için ilke eşleşmeleri oluşturur. A Kullanıcısı'nı içeren kanalın dışında yer alan B kullanıcısı ile C Kullanıcısı arasındaki konuşmaları Teams, A Kullanıcısını içeren uygunsuz içerik ilkesine tabi olmaz. Kanalın diğer üyeleri açıkça denetlendiğinde kanal üyelerini denetimden çıkarmak için, ilgili iletişim uyumluluk ilkesinde *Gelen* iletişim yönü ayarını kapatın.
- **Karma e-posta ortamlarıyla Teams sohbet iletişimi** için: İletişim uyumluluğu, şirket içi dağıtımı Exchange veya Microsoft Teams etkinleştirmiş bir dış e-posta sağlayıcısı olan kuruluşlar için kullanıcılara yönelik sohbet iletilerini izleyebilir. İzlemesi için şirket içi veya dış posta kutuları olan kullanıcılar için bir dağıtım grubu oluşturmanız gerekir. İletişim uyumluluk ilkesi oluştururken, bu dağıtım grubunu ilke sihirbazında **Denetimli kullanıcılar ve gruplar** seçimi olarak atayacaksınız. Bulut tabanlı depolamayı etkinleştirme gereksinimleri ve sınırlamaları ve şirket içi kullanıcılar için Teams desteği hakkında daha fazla bilgi için bkz. [Şirket içi kullanıcılar için Teams sohbet verilerini arama](search-cloud-based-mailboxes-for-on-premises-users.md).

## <a name="exchange-email"></a>e-postayı Exchange

Microsoft 365 veya Office 365 aboneliğinizin bir parçası olarak Exchange Online'da barındırılan posta kutularının tümü ileti taraması için uygundur. Exchange e-posta iletilerinin ve iletişim uyumluluk ilkesi koşullarıyla eşleşen eklerin işlenmesi yaklaşık 24 saat sürebilir. İletişim uyumluluğu için desteklenen ek türleri, [Exchange posta akışı kuralı içerik denetimleri için desteklenen dosya türleriyle aynıdır](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection).

## <a name="yammer"></a>Yammer

özel iletiler, genel konuşmalar ve Yammer topluluklardaki ilişkili ekler taranabilir. Kullanıcı, tanımlanmış bir kanal olarak Yammer içeren iletişim uyumluluk ilkesine eklendiğinde, kullanıcının üyesi olduğu tüm Yammer toplulukları arasındaki iletişimler tarama işlemine dahil edilir. Yammer iletişim uyumluluk ilkesi koşullarıyla eşleşen sohbetlerin ve eklerin işlenmesi 24 saat kadar sürebilir. 

Yammer Yammer iletişimleri ve ekleri izlemek için iletişim uyumluluk ilkelerinin [Yerel Modda](/yammer/configure-your-yammer-network/overview-native-mode) olması gerekir. Yerel Modda, tüm Yammer kullanıcılar Azure Active Directory (AAD), tüm gruplar Office 365 Gruplar ve tüm dosyalar SharePoint Online'da depolanır.

## <a name="skype-for-business-online"></a>Skype Kurumsal Çevrimiçi

Skype Kurumsal Online'daki sohbet iletişimleri ve ilişkili ekler denetlenebilir. Skype Kurumsal İletişim uyumluluk ilkesi koşullarıyla eşleşen çevrimiçi sohbetlerin işlenmesi 24 saat kadar sürebilir. Denetimli sohbet konuşmaları[, Skype Kurumsal Online'da kaydedilen önceki konuşmalardan](https://support.office.com/article/Find-a-previous-Skype-for-Business-conversation-18892eba-5f18-4281-8c87-fd48bd72e6a2) alınır.  

Skype Kurumsal Online'da kullanıcı sohbeti iletişimlerini denetlemek için aşağıdaki grup yönetimi yapılandırmasını kullanın:

- **Skype Kurumsal Çevrimiçi sohbet iletişimleri için**: İletişim uyumluluk ilkesine tek tek kullanıcılar atayın veya bir [dağıtım grubu](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) atayın. Bu ayar, bire bir veya bire çok kullanıcı/sohbet ilişkileri içindir.

## <a name="third-party-sources"></a>Üçüncü taraf kaynaklar

[Anlık Bloomberg](archive-instant-bloomberg-data.md), [Slack](archive-slack-data.md), [Zoom](archive-zoommeetings-data.md), SMS gibi üçüncü taraf kaynaklardan Microsoft 365 kuruluşunuzdaki posta kutularına aktarılan verileri tarayabilirsiniz. İletişim uyumluluğunda desteklenen bağlayıcıların tam listesi için bkz. [Üçüncü taraf verilerini arşivle](archiving-third-party-data.md).

Bağlayıcıyı bir iletişim uyumluluk ilkesine atayabilmeniz için önce Microsoft 365 kuruluşunuz için bir üçüncü taraf bağlayıcı yapılandırmanız gerekir. İletişim uyumluluk ilkesi sihirbazının **Üçüncü Taraf Kaynaklar** bölümü yalnızca şu anda yapılandırılmış olan üçüncü taraf bağlayıcılarını görüntüler.
