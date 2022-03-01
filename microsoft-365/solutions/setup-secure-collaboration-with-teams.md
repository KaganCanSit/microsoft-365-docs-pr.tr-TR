---
title: İş ve Eğitim ile güvenli dosya ve belge Teams işbirliği Microsoft 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-securecollab
- m365solution-overview
ms.custom:
- M365solutions
- seo-marvel-jun2020
f1.keywords: NOCSH
recommendations: false
description: Verilerinizi duyarlılığına dayalı olarak korumak için E-Teams içinde güvenli dosya işbirliği ve paylaşım ayarlamaya yönelik en iyi uygulamaları öğrenin.
ms.openlocfilehash: 4bf18635b0c345e18c1ed5db8c7072ca6225e33c
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2021
ms.locfileid: "63005031"
---
# <a name="set-up-secure-file-sharing-and-collaboration-with-microsoft-teams"></a>Dosya paylaşımını güvenli bir şekilde ayarlama ve işbirliği Microsoft Teams

Aşırı paylaşımı önlerken, dosyaları ve belgeleri doğru kişilerle kolayca paylaşabiliyor olmak, kuruluşun başarıya ulaşması için çok önemli. Bu, gizli veya diğer hassas verileri yalnızca erişimi olması gerekenlerle güvenli bir şekilde paylaşabilirsiniz. Projeye bağlı olarak bu, hassas verileri kuruluş dışındaki kişiler ile paylaşmayı içerebilir.

Bu işbirliği çözümü kılavuzu, size yardımcı olacak iki bileşen içerir:

- Her Teams için doğru koruma düzeyiyle proje dağıtımı
- Her proje için uygun güvenlik ayarlarıyla dış paylaşımı yapılandırma

![Uygun Teams ile dış paylaşımı uygun güvenlik ayarlarıyla dağıtın ve dış paylaşımı yapılandırın.](..\media\solutions-architecture-center\secure-collaboration-overview.png)

Çok yönlü ve kullanımı kolay dosya işbirliği araçları kullanılamıyorsa, kullanıcılar çoğunlukla belgeleri e-postayla göndererek işbirliği yapacaktır. Bu, sıkıcı ve hataya uygun olmayan bir işbirliği yöntemidir ve uygunsuz bilgi paylaşımı riskini artırabilir. Kişiler dosya paylaşımını çok zor bulursa, geri dönerek, IT tarafından yönetilmiyor tüketici ürünleri kullanmaya geri döndürülebilirsiniz. Bu, daha da büyük bir risk oluşturduğuna neden olabilir.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxMmL?autoplay=false]

Microsoft 365 ile, Teams yardımcı olacak çeşitli yapılandırmalarla dağıtım sebilirsiniz:

- Fikri mülkiyet haklarınızı koruyun
- Belgeler ve diğer dosyalarla kolay işbirliğini etkinleştirme
- Güvenlik ve kullanım arasında, kullanıcı memnuniyetini artıran ve IT'ye gölge düşürme riskini azaltan bir bakiye oluşturun

Çoğu kuruluşta, bilgi uygunsuz şekilde paylaşılıyorsa duyarlılık dereceleri ve iş üzerindeki farklı etki dereceleri olan çeşitli bilgiler vardır. Belirli bir bilgi parçasının duyarlılığına bağlı olarak paylaşıma izin vermek için:

- Herkes (kimliği doğrulanmamış)
- Kuruluşun içindeki kişiler
- Kuruluş içindeki belirli kişiler
- Kuruluşun içindeki ve dışındaki belirli kişiler

Pazarlama broşürleri gibi bilgiler, kuruluş dışında geniş bir kitleyle paylaşmak için hazırlar. Yemek menüleri gibi bilgiler dış paylaşım için değil, dış paylaşım için uygun olsalar da ticari hiçbir etkisi olmaz. Bu tür bilgiler için çok az koruma gerekir veya hiç korunmaz.

Aynı pazarlama broşürleri geliştirme aşamasındayken yalnızca kuruluş içinde paylaşılıyor olabilir. Bu durumda, varsayılan Teams ayarları yeterli olabilir.

Geliştirme aşamasında olan yeni bir ürünle ilgili bilgiler, kuruluş içinde bile hassas kabul olabilir. Bu durumda büyük ölçüde koruma uygun olabilir. Örneğin, bu bilgilere erişimi belirli bir ekibin üyeleriyle sınırlandırebilirsiniz. Projeye bağlı olarak, satıcı veya iş ortağı kuruluş gibi, kuruluş dışındaki çalışanlarla işbirliğine ihtiyacınız olabilir.

Kuruluş başarısı için kritik öneme sahip olan ya da sıkı güvenlik ve uyumluluk gereksinimlerine sahip bilgiler daha da fazla koruma düzeyi gerektirecektir.

![Düşükten (yayımlanan broşür) yüksek (hassas iş verileri) risk ölçeğine kadar).](../media/solutions-architecture-center/SecureCollaboration-SensitivityAndBusinessImpactofSharing-fromVisio.png)

Yukarıda belirtilen tüm senaryolarda, bilgileri depolamak, paylaşmak ve bunlar üzerinde Microsoft Teams ekipler kullanabilirsiniz.

Güvenli işbirliğini yapılandırmak için, bu özellik Microsoft 365 kullanırsiniz.

|Ürün veya bileşen|Özellik veya özellik|Lisanslama|
|---|---|---|
|Office 365 için Microsoft Defender|Kasa, Bağlantı Ve Bağlantı Ekleri için OneDrive'Teams; Kasa Belgeleri; Kasa için Bağlantılar'Teams|Microsoft 365 E1, E3 ve E5|
|SharePoint|Site ve dosya paylaşım ilkeleri, Site paylaşımı izinleri, Paylaşım bağlantıları, Erişim istekleri, Site konuk paylaşımı ayarları|Microsoft 365 E1, E3 ve E5|
|Microsoft Teams|Konuk erişimi, özel takımlar, özel kanallar|Microsoft 365 E1, E3 ve E5|
|Microsoft 365 Uyumluluğu|Duyarlılık etiketleri|Microsoft 365 E3 ve E5|

## <a name="collaboration-governance-framework-for-teams-and-microsoft-365"></a>Kurumsal ve kurumsal işbirliği Teams birlikte Microsoft 365

Microsoft 365 çözüme yönelik birçok seçenek sağlar. Organizasyonunız için en iyi işbirliği çözümünü oluşturmak için bu dağıtım içeriğini [işbirliği](collaboration-governance-overview.md) yönetimi içeriğiyle birlikte kullanmanızı öneririz.

### <a name="securing-teams-for-sensitive-and-highly-sensitive-data"></a>Hassas Teams çok hassas veriler için verilerin güvenliğini sağlama

Farklı duyarlılıkla bilgilere erişimi yönetmek için bu bilgilere erişim hakkında üç farklı koruma katmanı [Teams](configure-teams-three-tiers-protection.md). Gereksinimlerinize veya işlerinizi daha iyi karşılamak için bu katmanlardan herhangi birini özelleştirebilirsiniz.

![Üç koruma düzeyi grafiği Teams.](../media/solutions-architecture-center/Teams-tiers-of-protection-1.png)

Taban *çizgisi, hassas* ve *çok* hassas olan bu  katmanlar, aşağıdaki tabloda gösterildiği gibi, aşırı bilgi sızıntısını ve olası bilgi sızıntısını önlemeye yardımcı olan korumaları aşamalı olarak artıracaktır.

|-|Taban çizgisi katmanı|Hassas katman|Çok hassas katman|
|---|---|---|---|
|Genel veya özel ekip|Ya da|Özel|Özel|
|Kimliği doğrulanmamış paylaşım|Engellendi|Engellendi|Engellendi|
|Dosya paylaşımı|İzin verildi|İzin verildi|Yalnızca ekip sahipleri paylaşabilir.|
|Ekip üyeliği|Herkes herkese açık ekiplere katılabilir.<br>Özel ekiplere katılmak için ekip sahibi onayı gereklidir.|Katılmak için ekip sahibi onayı gereklidir.|Katılmak için ekip sahibi onayı gereklidir.|
|Belge şifrelemesi|||Duyarlılık etiketiyle kullanılabilir|
|Konuk paylaşımı|İzin verildi|İzin verilen veya engellenmiş olabilir|İzin verilen veya engellenmiş olabilir|
|Unmanaged devices|Kısıtlama yok|Yalnızca web erişimi|Engellendi|

Bu katmanların yapılandırılması şunları içerir:

- Konuk erişimi ve Teams kanallarında ayarları yapılandırma
- İç ve konuk paylaşımı, erişim istekleri SharePoint bağlantıları için ekibin ilişkili web sitesinde ayarları yapılandırma
- Hassas ve *çok* hassas  katmanlar için, ekipleri sınıflandırmak için duyarlılık etiketleri yapılandırma, konuk paylaşımını ve kolay olmayan cihazlardan erişimi denetleme
- Çok *hassas katman* için, duyarlılık etiketini uygulanarak uygulandığı belgeleri şifreleecek şekilde yapılandırma

Taban çizgisi katmanıyla çalışmaya devam edin ve sonra, hassas ve çok  hassas katmanları  kullanan ekipleri kurumda bilgileri korumaya yardımcı olmak için ekleyin. Çalışmaya başlamanız için şu kaynaklara bakın:

- [Taban çizgisi korumasıyla ekipleri yapılandırma](configure-teams-baseline-protection.md)
- [Hassas veriler için korumayla ekipleri yapılandırma](configure-teams-sensitive-protection.md)
- [Çok hassas veriler için ekipleri koruma ile yapılandırma](configure-teams-highly-sensitive-protection.md)

Son derece hassas bir projeniz varsa ve kurum içinde bile paylaşıma karşı ek koruma gerektiriyorsa, dosyaları şifrelemek için kendi duyarlılık etiketini kullanan bir ekibi, yalnızca ekip üyelerinin okuyabilması için yapılandırabilirsiniz. Ayrıntılar [için bkz. Ekibi güvenlik yalıtım ile](secure-teams-security-isolation.md) yapılandırma.

### <a name="sharing-with-people-outside-your-organization"></a>Kuruluş dışındaki kişilerle paylaşma

Tüm duyarlılık [bilgilerini kuruluş dışındaki kişiler ile paylaşmanız gerekiyor olabilir](collaborate-with-people-outside-your-organization.md). Bu, dünyanın her yanında yer alan büyük bir iş ortağı kuruluş veya bağımsız çalışanlarla büyük bir proje üzerinde işbirliği yapmak için tek bir kişi ile tek bir belge paylaşma arasında olabilir. Dış Microsoft 365, hassas bilgilerinizin korunmasına yardımcı olmak için bu dış paylaşım aralığını kolayca ve uygun korumalarla yapabilirsiniz.

Bu kaynaklar, organizasyon dışındaki kişilerle işbirliği için ortamınızı ayarlamaya başlamanıza yardımcı olur:

- [Tek tek klasör](collaborate-on-documents.md) dosyalarını paylaşmak için belgeler üzerinde işbirliği yapın.
- [Bir site içinde konuklarla](collaborate-in-site.md) işbirliği yapmak için bir sitede SharePoint yapın.
- [Bir ekipte konuklarla](collaborate-as-team.md) işbirliği yapmak için ekip olarak işbirliği yapın.

Paylaşılan bilgilerin duyarlılığına bağlı olarak, fazla paylaşımı önlemeye yardımcı olmak için korumalar  eklemeniz gerekir. Bu kaynaklar, organizasyonunız için gereken korumaları ayarlamanıza yardımcı olur:

- [Kimliği doğrulanmamış kullanıcılarla dosya ve klasör paylaşmak için en iyi yöntemler](best-practices-anonymous-sharing.md)
- [Kuruluş dışından kişilerle paylaşım sırasında dosyalarda yanlışlıkla açık kalma sürelerini sınırlama](share-limit-accidental-exposure.md)
- [Güvenli bir konuk paylaşım ortamı oluşturma](create-secure-guest-sharing-environment.md)

İş ortağı bir kuruluşla büyük bir projeniz varsa, Azure Yetkilendirme Yönetimi'ne kullanarak bu kuruluştan gelen konukları proje için ayar takım olarak yönetabilirsiniz. Ayrıntılı [bilgi için bkz. Yönetilen konuklarla B2B extranet](b2b-extranet.md) oluşturma.

## <a name="training-for-administrators"></a>Yöneticiler için eğitim

Microsoft Learn'den gelen bu eğitim modülleri, proje içinde ve diğer projelerde işbirliği, yönetim ve kimlik Teams SharePoint.

### <a name="teams"></a>Teams

|Eğitim:|Destek ekibiyle işbirliğini Microsoft Teams|
|---|---|
|![Teams işbirliği eğitimi simgesi.](../media/manage-team-collaboration-with-microsoft-teams.svg)|Ekip işbirliğini yönetim Microsoft Teams, ekip işbirliği merkezi olan Microsoft Teams'ın özelliklerini ve özelliklerini size Microsoft 365. Masaüstünden tabletlere telefonlara kadar çok çeşitli cihazlarda, hem şirket içinde hem de şirket içinde ekip çalışması ve iletişimi kolaylaştırmak için Teams'i nasıl kullanabileceğinizi öğrenirken, Office 365 uygulamalarının tüm zengin işlevselliğinden yararlanmayı öğrenirsiniz. Uygulama ve cihazlar arasında işbirliği için Teams ve esnek bir ortam sağladığını anlamanız gerekir. Bu öğrenme yolu, İş Ortağı Sertifikalı: veya Yönetici Microsoft 365 için Teams yardımcı olabilir.<p>2 sa 17 dak . Learning Yol - 5 Modüller|

> [!div class="nextstepaction"]
> [Başlangıç >](/learn/modules/m365-teams-collab-prepare-deployment/introduction/)

### <a name="sharepoint"></a>SharePoint

|Eğitim:|İş'te SharePoint işbirliği Microsoft 365|
|---|---|
|![SharePoint simgesi.](../media/collaborate-with-sharepoint-in-microsoft-365.svg)|Paylaşılan içerikleri Microsoft SharePoint yönet özelliği, paylaşılan içeriklerin özellikleri ve SharePoint özellikleri ve bu içerikle nasıl çalıştığını Microsoft 365. Merkez siteleri de dahil olmak üzere, SharePoint koruma, raporlama ve izleme gibi farklı türler hakkında bilgi edinebilirsiniz. Ayrıca, işbirliğini iyileştirmek için SharePoint ve klasör paylaşımını kullanmayı, dosyaları dışarıdan paylaşmayı ve SharePoint yönetim merkezinde SharePoint sitelerini yönetmeyi de öğrenirsiniz. Bu öğrenme yolu, İş Ortağı Sertifikalı: Ekip Çalışması Yöneticisi Microsoft 365 sertifikasına hazırlanmanıza yardımcı olabilir.<p>1 sa 14 dak . Learning Yol - 4 Modül|

> [!div class="nextstepaction"]
> [Başlangıç >](/learn/modules/m365-teams-sharepoint-plan-sharepoint/introduction/)

### <a name="information-protection"></a>Bilgi koruması

|Eğitim:|Kurumsal bilgileri iş yerleriyle Microsoft 365|
|---|---|
|![Teams koruma eğitimi simgesini seçin.](../media/protect-enterprise-information-microsoft-365.svg)|Kuruluş bilgilerini korumak ve güvenliğini sağlamak her zaman olduğu kadar zor olabilir. Microsoft 365 ile kurumsal bilgileri koruma yolu, hassas verilerinizi yanlışlıkla yanlış şekilde ortaya çıkarma veya yanlış kullanımlara karşı koruma, verileri keşfetme ve sınıflandırma, duyarlılık etiketleriyle koruma ve hassas bilgilerini hem izleme hem de çözümleme konularını ele almaktadır. Bu öğrenme yolu, Destek Sertifikalı: Güvenlik Microsoft 365 İş ortağı ve güvenlik Microsoft 365: Enterprise Sertifikalarını hazırlamanıza yardımcı olabilir.<p>1 sa - Learning Yolu - 5 Modül|

> [!div class="nextstepaction"]
> [Başlangıç >](/learn/modules/m365-security-info-overview/introduction/)

### <a name="identity-and-access"></a>Kimlik ve erişim

|Eğitim:|Kimlik ve erişimi diğer Azure Active Directory|
|---|---|
|![Kimlik ve erişim eğitimi simgesi.](../media/protect-identity-and-access-with-microsoft-365.svg)|Identity ve Access öğrenme yolu en son kimlik ve erişim teknolojilerini, kimlik doğrulamayı güçlendirme araçlarını ve kuruluş içinde kimlik koruması konusunda yol gösterici bilgileri kapsar. Microsoft erişim ve kimlik teknolojileri, ister şirket içinde ister bulutta olsun, kuruluş kimliğinizin güvenliğini sağlamanızı ve kullanıcılarınızı herhangi bir konumdan güvenli bir şekilde çalışmalarını sağlamanızı sağlar. Bu öğrenme yolu, Eğitim Sertifikalı: Güvenlik Microsoft 365 İş ortağı ve eğitim Microsoft 365: Enterprise Uzman sertifikalarına hazırlanmanıza yardımcı olabilir.<p>2 sa 52 dak . Learning Yol - 6 Modüller|

> [!div class="nextstepaction"]
> [Başlangıç >](/learn/modules/m365-identity-overview/introduction/)

## <a name="training-for-end-users"></a>Son kullanıcılar için eğitim

Bu eğitim modülleri kullanıcılarının iş birliği için Teams grupları ve grupları kullanmalarına SharePoint yardımcı Microsoft 365.

|Teams|SharePoint|
|---|---|
|![Ekip eğitimi simgenizi ayarlayın ve özelleştirin.](../media/set-up-customize-team-training.png)<br>**[Ekibinizi ayarlama ve özelleştirme](https://support.microsoft.com/office/702a2977-e662-4038-bef5-bdf8ee47b17b)**|![SharePoint paylaşma ve eşitleme eğitimi simgesi](../media/sharepoint-share-sync-training.png)<br>**[Paylaşma ve eşitleme](https://support.microsoft.com/office/98cb2ff2-c27e-42ea-b055-c2d895f8a5de)**|
|![Teams ve bulma eğitimi simgesini seçin.](../media/smc-teams-upload-find-files-training.png)<br>**[Upload bulma ve bulma](https://support.microsoft.com/office/57b669db-678e-424e-b0a0-15d19215cb12)**||
|![Ekiplerde ve kanallarda işbirliği yap simgesi.](../media/teams-collaborate-channels-training.png)<br>**[Ekiplerde ve kanallarda işbirliği yapma](https://support.microsoft.com/office/c3d63c10-77d5-4204-a566-53ddcf723b46)**||

## <a name="illustrations"></a>Çizimler

Bu çizimler, grupların ve ekiplerin kuruluş içinde diğer hizmetlerle nasıl etkileşim kurduğuna ve Microsoft 365 içinde bu hizmetleri yönetmenize yardımcı olmak için hangi yönetim ve uyumluluk özelliklerinin kullanılabilir olduğunu anlamanıza yardımcı olur.

### <a name="groups-in-microsoft-365-for-it-architects"></a>IT Architects için Microsoft 365 Grupları

Bu mimarların proje içinde gruplar hakkında neleri Microsoft 365

|**Öğe**|**Açıklama**|
|---|---|
|[![Gruplar bilgi grafiği için başparmak resmi.](../downloads/msft-m365-groups-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-groups.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-groups.vsdx) <br> Güncelleştirme Haziran 2019|Bu çizimler farklı grup türlerini, bunların nasıl oluşturulacaklarını ve yönetil grafiklerini ve birkaç yönetim önerilerini ayrıntılarıyla açıklar.|

### <a name="microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects"></a>Microsoft Teams mimarlar için Microsoft 365'te veri ve ilgili üretkenlik hizmetleri

Verilerde üretkenlik hizmetlerinin mantıksal mimarisi, Microsoft 365 yol Microsoft Teams.

|**Öğe**|**Açıklama**|
|---|---|
|[![Mantıksal mimari posteri Teams küçük resim.](../downloads/msft-teams-logical-architecture-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) <br/> [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/msft-m365-teams-logical-architecture.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-teams-logical-architecture.vsdx)  <br>Güncelleştirme: Nisan 2019|Microsoft, veri yönetimi, güvenlik ve uyumluluk özellikleriyle ilgili işbirliği deneyimleri sunmak için birlikte çalışan bir üretkenlik hizmetleri paketi sunar. <p>Bu çizim serisi, kurumsal mimarlar için üretkenlik hizmetlerinin mantıksal mimarisine, önde gelen ve kurumsal şirketlere Microsoft Teams.|

## <a name="deploy-the-secure-collaboration-solution"></a>Güvenli işbirliği çözümünü dağıtma

Bu çözümü dağıtmaya hazır olduğunda, şu adımlarla devam edin:

1. Güvenlik katmanı [için üç farklı koruma katmanı Teams](configure-teams-three-tiers-protection.md).
2. Duyarlılıkla [ilgili bilgileri kuruluş dışındakilerle paylaşmak için ayarları yapılandırabilirsiniz](collaborate-with-people-outside-your-organization.md).

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 belgeleri](../security/index.yml)

[Microsoft 365 uyumluluğu belgeleri](../compliance/index.yml)

[Microsoft Teams'e hoş geldiniz](/MicrosoftTeams/Teams-overview)
