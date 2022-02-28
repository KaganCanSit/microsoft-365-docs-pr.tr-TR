---
title: Kazara maruz kalmayı sınırla
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
ms.custom: ''
ms.localizationpriority: high
f1.keywords: NOCSH
recommendations: false
description: Kuruluş dışındaki kişiler ile dosya paylaştığınızda yanlışlıkla bilgilerin maruz kalmalarını sınırlamayı öğrenin.
ms.openlocfilehash: 4c60f77f7f7807395a503ce083795e76398d99b4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986708"
---
# <a name="limit-accidental-exposure-to-files-when-sharing-with-people-outside-your-organization"></a>Kuruluş dışından kişilerle paylaşım sırasında dosyalarda yanlışlıkla açık kalma sürelerini sınırlama

Dosyalarınızı ve klasörlerinizi kuruluş dışındakilerle paylaştığınızda, yanlışlıkla hassas bilgileri paylaşma riskini azaltmak için çeşitli seçenekler bulunur. Bu makaledeki seçenekleri, kuruma en uygun şekilde karşılayacak şekilde seçebilirsiniz.

## <a name="use-best-practices-for-anyone-links"></a>Herkes bağlantıları için en iyi yöntemleri kullanma

Kuruluşta kişilerin kimliği doğrulanmamış paylaşım yapmaları gerekiyorsa, ancak kimliği doğrulanmamış kişilerin içeriği değiştirmesi konusunda endişeleniyorsanız, Kurumda [](best-practices-anonymous-sharing.md) kimliği doğrulanmamış paylaşımla çalışma konusunda yol gösterici kılavuzlar için Kimliği doğrulanmamış paylaşım için en iyi yöntemler makalesini okuyun.

## <a name="turn-off-anyone-links"></a>Herkes bağlantılarını kapatma

Uygun içerik için *Herkes* bağlantılarını etkin bırakmanızı öneririz, çünkü bu paylaşım yapmanın en kolay yolu olup, KULLANıCıLARıN, BILGI bölümünizin denetimi dışında başka çözümler arama riskini azaltmaya yardımcı olabilir. *Herkes* bağlantıları başkalarına iletebilirsiniz, ancak dosya erişimi yalnızca bağlantıya sahip olanlar tarafından kullanılabilir.

Kuruluş dışından kişilerin SharePoint, Groups veya Teams'ta içeriğe erişirken her zaman kimlik doğrulaması yapmalarını Teams, Herkes *paylaşımını kapatabilirsiniz*. Bu, kullanıcıların içeriğin kimliği doğrulanmamış paylaşımını engellemek için.

Herkes bağlantılarını devre *dışı bıraksanız* bile kullanıcılar Belirli kişiler bağlantılarını kullanarak kolayca *konuklarla paylaşabilir* . Bu durumda, paylaşılan içeriğe erişmek için, kuruluş dışındaki tüm kişilerin kimlik doğrulaması yapmaları gerekir.

Gereksinimlerinize bağlı olarak, belirli siteler için veya tüm *organizasyonunız* için Herkes bağlantılarını devre dışı abilirsiniz.

Sizin için herkes *bağlantılarını* kapatmak için
1. Yönetim SharePoint sol gezinti bölmesinde, Paylaşım'a **tıklayın**.
2. Dış SharePoint ayarlarını Yeni ve var **olan konuklar olarak ayarlayın**.

   ![Site dış paylaşım ayarları SharePoint düzeyi ayarlarının ekran görüntüsü.](../media/sharepoint-organization-external-sharing-controls-new-users.png)

3. **Kaydet**'e tıklayın.

Site için *herkes* bağlantılarını kapatmak için
1. Genel SharePoint, sol gezinti bölmesinde Siteler'i genişletin **ve Etkin** **siteler'e tıklayın**.
2. Yapılandırmak istediğiniz siteyi seçin.
3. Şeritte Paylaşım'a **tıklayın**.
4. Paylaşımın Yeni ve mevcut konuklar **olarak ayar olduğundan emin olmak**.

   ![Sitenin dış paylaşım SharePoint düzeyi ayarlarının ekran görüntüsü.](../media/sharepoint-site-external-sharing-settings.png)

5. Değişiklikler yaptıysanız Kaydet'e **tıklayın**.

## <a name="domain-filtering"></a>Etki alanı filtreleme

Etki alanı izin listelerini kullanarak veya reddederek, kullanıcılarının kuruluş dışındaki kullanıcılarla paylaşımda kullanabileceği etki alanlarını belirtebilirsiniz.

İzin ver listesiyle, bir etki alanı listesi belirtebilirsiniz; burada, kuruluş dışındaki kullanıcılarla kuruluş dışındaki kullanıcılarla paylaşımda ekleyebilirsiniz. Diğer etki alanlarıyla paylaşım engellenir. Organizasyonunız yalnızca belirli etki alanları listesinden gelen kişiler ile işbirliği yapıyorsa, diğer etki alanlarıyla paylaşımı önlemek için bu özelliği kullanabilirsiniz.

Reddedenler listesiyle, etki alanlarının listesini belirtebilirsiniz; bu liste, kurum dışındaki kullanıcılarla organizasyon dışındaki kullanıcılarla paylaşamaz. Listelenen etki alanlarıyla paylaşım engellenir. Bu özellik, örneğin kimlerin kuruluşta yer alan içeriğe erişmesini engellemek istediğiniz rakipler varsa kullanışlı olabilir.

İzin ver ve reddet listeleri yalnızca konuklarla paylaşımı etkiler. Kullanıcılar, devre dışı olmadığınız Herkes bağlantılarını kullanarak yasak etki *alanlarını* kullanan kullanıcılarla paylaşımda ılabilir. Etki alanı izin verme ve reddetme listelerinde en iyi sonuçları elde etmek için yukarıda *açıklandığı gibi Herkes* bağlantılarını devre dışı bırakmayı göz önünde bulundurabilirsiniz.

Etki alanı izin verme veya reddedilenler listesi ayarlamak için
1. Yönetim SharePoint sol gezinti bölmesinde, Paylaşım'a **tıklayın**.
2. Dış **paylaşım için gelişmiş ayarlar'ın** altında Dış paylaşımı **etki alanına göre sınırla onay** kutusunu seçin.
3. Etki alanı **ekle'ye tıklayın**.
4. Etki alanlarını engellemek isteyip istemediklerini seçin, etki alanlarını yazın ve Tamam'a **tıklayın**.

   ![Dış paylaşımı SharePoint etki alanına göre sınırla ayarının ekran görüntüsü.](../media/sharepoint-sharing-block-domain.png)

5. **Kaydet**'e tıklayın.

Etki alanına göre paylaşımı SharePoint ve OneDrive'den daha yüksek bir düzeyde sınırlamak için Azure Active Directory'de belirli kuruluşlardan [B2B](/azure/active-directory/b2b/allow-deny-list) kullanıcılarına davetlere izin ve Azure Active Directory. (Bu ayarların etki [SharePoint OneDrive için Azure AD B2B Preview ile Azure AD B2B Preview](/sharepoint/sharepoint-azureb2b-integration-preview) SharePoint ve OneDrive.)

## <a name="limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups"></a>Dosyaların, klasörlerin ve sitelerin paylaşımını belirli güvenlik gruplarıyla sınırlama

Dosyaların, klasörlerin ve sitelerin paylaşımını belirli bir güvenlik grubunun üyeleriyle, kuruluş dışındaki çalışanlarla sınırlandırabilirsiniz. Bu özellik, dış paylaşımı etkinleştirmek, ancak onay iş akışı veya istek süreciyle etkinleştirmek istediğiniz durumlarda kullanışlıdır. Alternatif olarak, kullanıcılarınızı güvenlik grubuna eklenmeden ve dış paylaşıma izin verilmeden önce bir eğitim kursını tamamlamalarını gerektirmeniz gerekir.

Dış paylaşımı bir güvenlik grubunun üyeleriyle sınırlamak için
1. Genel SharePoint [, sol gezinti](https://admin.microsoft.com/sharepoint) bölmesinde, İlkeler'in **altında Paylaşım'a** **tıklayın**.
2. Dış **paylaşım'ın** altında Diğer **dış paylaşım ayarları'nın genişletin**.

3. Yalnızca **belirli güvenlik gruplarında yer alan kullanıcıların dışarıdan paylaşıma izin ver'i seçin ve** sonra da Güvenlik gruplarını **yönet'i seçin**.

    ![Güvenlik gruplarını yönet panelinin ekran görüntüsü.](/sharepoint/sharepointonline/media/manage-security-groups.png)

4. Güvenlik **grubu ekle kutusunda** , güvenlik grubu için bir ad girin. Güvenlik grubu kutusu görüntülenir.

5. Güvenlik grubu adının yanındaki Paylaş şu **seçeneklerden** birini seçin:

    - **Yalnızca kimliği doğrulanmış konuklar** (varsayılan)
    - **Herkes**

6. **Kaydet**'i seçin.

Bunun dosyaları, klasörleri ve siteleri etkilediğini, ancak grupların veya sitelerin Microsoft 365 etkileyeceğini Teams. Üyeler konukları özel bir Microsoft 365 özel bir gruba veya Microsoft Teams bir ekipe davet etmek için davet, onay için gruba veya ekip sahibine gönderilir.

## <a name="see-also"></a>Ayrıca Bkz

[Güvenli bir konuk paylaşım ortamı oluşturma](create-secure-guest-sharing-environment.md)

[Anonim kullanıcılarla dosya ve klasör paylaşmak için en iyi yöntemler](best-practices-anonymous-sharing.md)
