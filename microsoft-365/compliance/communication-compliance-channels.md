---
title: İletişim uyumluluğuyla kanal sinyallerini algılama
description: İletişim uyumluluğu ile kanal sinyallerini algılama hakkında daha fazla bilgi edinin.
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
ms.openlocfilehash: 9cc2b77c9983fecc6e58be515fe316c6c5239fef
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317787"
---
# <a name="detect-channel-signals-with-communication-compliance"></a>İletişim uyumluluğuyla kanal sinyallerini algılama

İletişim uyumluluğu ilkeleriyle, aşağıdaki iletişim platformlarından bir veya birden çoksinde yer alan iletileri grup olarak veya tek başına kaynak olarak taramayı seçebilirsiniz. Bu platformlarda yakalanan özgün iletiler, kuruluşun bekletme ve saklama ilkelerine uygun olarak özgün platform [konumda korunur](/microsoft-365/compliance/information-governance). çözümleme ve soruşturma için iletişim uyumluluk ilkeleri tarafından kullanılan iletilerin kopyaları, kullanıcılar kuruluşdan ayrılsa ve posta kutuları silinmiş olsa bile, ilke olduğu sürece korunur. Bir iletişim ilkesi silindiğinde, ilkeyle ilişkilendirilmiş iletilerin kopyaları da silinir.

## <a name="microsoft-teams"></a>Microsoft Teams

Hem ortak hem de özel Microsoft Teams sohbet iletişimleri ve tek tek sohbetler taranabilirsiniz. Seçilen bir kapsam ile iletişim uyumluluğu ilkesine atanan Microsoft Teams, kullanıcıların sohbet iletişimleri kullanıcının üyesi olduğu tüm Microsoft Teams genelinde otomatik olarak izlenir. Microsoft Teams kapsam, önceden tanımlanmış ilke şablonlarına otomatik olarak eklenir ve özel ilke şablonunda varsayılan olarak seçilir. Teams iletişim uyumluluğu ilkesi koşulları eşleşen sohbetlerin işlemesi 48 saat kadar sürebilir.

Özel sohbetler ve özel kanallar için, iletişim uyumluluk ilkeleri Modern ek taramayı destekler. Modern ekler, e-postalara [OneDrive](/onedrive/plan-onedrive-enterprise#modern-attachments) [SharePoint](/sharepoint/dev/solution-guidance/modern-experience-customizations) sitelerinden kaynaklandırarak gelen Teams olur. Etkin iletişim uyumluluğu ilkesi koşulları ve sınıflayıcılarla otomatik işleme ve olası eşleşmeler için bu eklerden metin otomatik olarak ayıklanır. Modern ek algılama ve işleme için gereken herhangi bir ek yapılandırma yoktur. Metin yalnızca eklerin eşleşen ilke koşulları için ayıklanır. İlke eşleşmesi olan iletilerin ekleri için metin ayıklanmayacak (ekin ilke eşleşmesi olsa bile).

Modern ek tarama, aşağıdaki dosya türlerinde destekler:

- Microsoft Word (.docx)
- Microsoft Excel (.xlsx)
- Microsoft PowerPoint (.pptx)
- Metin (.txt)
- Taşınabilir Belge Biçimi (.pdf)

Modern ekler için ayıklanan metin, ilkeye yönelik Bekleyen uyarılar panosunda **ilişkilendirilmiş** iletiye dahil edilir. Bir ekin ayıklanan metni, ekin dosya adı (ve biçim uzantısı) ve dosya .txt olarak adlandırılmıştır. Örneğin,ContosoBusinessPlan.docxadlı ekin ayıklanan *metni,ContosoBusinessPlan.docx.txt* **için Bekleyen** uyarılar panosunda ek olarak ** görünebilir.

Kaynak ve Düz metin görünümlerde ayrıntıları görüntülemek için *ayıklanan ek* *metnini* seçin. Gözden geçirmenin ardından, komut çubuğu denetimlerini kullanarak ek metnini çözebilir veya bu metin üzerinde eyleme geçebilirsiniz. Eki, iletişim uyumluluğu gözden geçirme işleminin dışında gözden geçirmek için indirme seçeneğiniz de vardır.

Aşağıdaki grup yönetimi yapılandırmalarını kullanarak tek tek kullanıcı sohbetlerini ve kanal iletişimlerini denetleme Teams:

- **Sohbet Teams: Tek** tek kullanıcılar atama veya iletişim [uyumluluk ilkesine](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) bir dağıtım grubu atama. Bu ayar bire bir veya bire çok kullanıcı/sohbet ilişkileri içindir.
- **Kanal Teams iletişimleri için:** Belirli bir Microsoft Teams içeren taramak istediğiniz her Microsoft 365 kanalını veya grup grubunu iletişim uyumluluk ilkesine attaynın. Aynı kullanıcıyı diğer kanal ve Microsoft Teams başka Microsoft 365, bu yeni kanal ve grupları iletişim uyumluluk ilkesine eklemeye emin olun. Kanalın herhangi bir üyesi bir ilkede denetimli bir kullanıcı ise ve Gelen yönü  bir ilkede yapılandırıldısa, kanal içinde gönderilen tüm iletiler gözden geçir ve olası ilke eşleşmeleri (kanalda açıkça denetlenen olmayan kullanıcılar için bile) gözden geçir ve olası ilke eşleşmeleri olur. Örneğin, Kullanıcı A, kanalın sahibi veya üyesidir. Kullanıcı B ve Kullanıcı C, aynı kanalın üyeleridir ve yalnızca Kullanıcı A'nın denetimine sahip uygunsuz içerik ilkesiyle eşleşen kullanım dilidir. Kullanıcı B ve Kullanıcı C, kanal içinde konuşmalar için ilke eşleşmeleri sağlar. Ancak bunlar doğrudan uygunsuz içerik ilkesinde denetlenen içerik ilkesinde denetlenmesin. Teams A Kullanıcısı'nın da dahil olduğu kanalın dışında yer alan B Kullanıcısı ile C Kullanıcısı arasındaki konuşmalar, A Kullanıcı'sı'nın dahil olduğu uygunsuz içerik ilkesine tabi olmaz. Kanalın diğer üyeleri açıkça denetim altında tutulsa da, kanal üyeleri gözetim dışında tutmak için, geçerli iletişim uyumluluğu  ilkesinde Gelen iletişim yönü ayarını kapatın.
- **Karma Teams** ortamlarla sohbet iletişimleri için: İletişim uyumluluğu, şirket için Exchange dağıtımı olan veya etkinleştirilmiş dış e-posta sağlayıcısı olan kuruluşların kullanıcılarının sohbet iletilerini Microsoft Teams. Şirket içi veya dış posta kutuları olan kullanıcıların izlemesi için bir dağıtım grubu oluşturmanız gerekir. bir iletişim uyumluluk ilkesi oluştururken, bu dağıtım grubunu ilke sihirbazında Denetimli kullanıcılar ve **gruplar seçimi olarak** atarsınız. Bulut tabanlı depolamayı etkinleştirme gereksinimleri ve sınırlamaları hakkında daha fazla bilgi Teams için bkz. Şirket içi kullanıcılar için [Teams sohbet verilerini arama](search-cloud-based-mailboxes-for-on-premises-users.md).

## <a name="exchange-email"></a>Exchange-posta gönderme

E-posta Exchange Online veya Microsoft 365 aboneliğiniz kapsamında Office 365 posta kutularının hepsi ileti tarama için uygundur. Exchange-posta iletilerinin ve eklerin uyumlu iletişim uyumluluk ilkesi koşullarının işlemesi 24 saat kadar sürebilir. İletişim uyumluluğu için desteklenen ek türleri, posta akışı kuralı içerik denetimlerinde [desteklenen Exchange türleriyle aynıdır](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection).

## <a name="yammer"></a>Yammer

Özel iletiler, ortak konuşmalar ve diğer topluluklarda Yammer ekler taranabilirsiniz. Kullanıcı, tanımlı kanal olarak Yammer içeren iletişim uyumluluk ilkesine ekli olduğunda, kullanıcının üyesi olduğu tüm Yammer toplulukları arasındaki iletişimler tarama sürecine dahil edilir. Yammer uyumluluk ilkesi koşullarıyla eşleşen sohbetlerin ve eklerin işlemesi 24 saat kadar sürebilir. 

Yammer ve [ekleri izlemek için](/yammer/configure-your-yammer-network/overview-native-mode), iletişim uyumluluk ilkelerinin Yerel Yammer modunda olması gerekir. Yerel Mod'da, Yammer tüm kullanıcılar Azure Active Directory (AAD), tüm gruplar Office 365 Grupları'dır ve tüm dosyalar SharePoint Online'da depolanır.

## <a name="skype-for-business-online"></a>Skype Kurumsal Çevrimiçi

Skype Kurumsal Online'da sohbet iletişimleri ve ilişkili ekler denetlenerek denetlenebilirsiniz. Skype Kurumsal Çevrimiçi sohbetlerle eşleşen iletişim uyumluluğu ilkesi koşullarının işlemesi 24 saat kadar sürebilir. Denetlenen sohbet konuşmaları, [Skype Kurumsal Online'da kaydedilmiş olan konuşmalardan kaynaklandı](https://support.office.com/article/Find-a-previous-Skype-for-Business-conversation-18892eba-5f18-4281-8c87-fd48bd72e6a2).  

Skype Kurumsal Online'da kullanıcı sohbeti iletişimlerini denetleme için aşağıdaki grup yönetimi Skype Kurumsal kullanın:

- **Çevrimiçi Skype Kurumsal iletişimleri hakkında** bilgi için: Tek tek kullanıcılar atama [veya iletişim uyumluluk](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) ilkesine dağıtım grubu atama. Bu ayar bire bir veya bire çok kullanıcı/sohbet ilişkileri içindir.

## <a name="third-party-sources"></a>Üçüncü taraf kaynakları

Anlık [Bloomberg](archive-instant-bloomberg-data.md), [Slack](archive-slack-data.md), [Zoom](archive-zoommeetings-data.md), SMS Microsoft 365 gibi üçüncü taraf kaynaklardan gelen ve Microsoft 365 posta kutularına aktarılan veriler için iletişimi tarayabilirsiniz. İletişim uyumluluğu için desteklenen bağlayıcıların tam listesi için bkz [. Üçüncü taraf verilerini arşivleme](archiving-third-party-data.md).

Bağlayıcıyı iletişim uyumluluk ilkesine atay Microsoft 365 için, önce bu kuruluş için üçüncü taraf bağlayıcısı yapılandırmanız gerekir. İletişim **uyumluluk ilkesi sihirbazının** Üçüncü Taraf Kaynakları bölümü yalnızca o anda yapılandırılmış olan üçüncü taraf bağlayıcılarını görüntüler.
