---
title: Yönetilen konuklarla B2B extranet oluşturma
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
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: İş ortağı bir kuruluştan yönetilen konuklarla B2B extranet sitesi veya ekip oluşturma hakkında bilgi edinebilirsiniz.
ms.openlocfilehash: ab8bba31538b9e79ed198f65349f14d8211f81f7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983741"
---
# <a name="create-a-b2b-extranet-with-managed-guests"></a>Yönetilen konuklarla B2B extranet oluşturma

Azure Active Directory [Yetkilendirme Yönetimi'yi](/azure/active-directory/governance/entitlement-management-overview) kullanarak, çalışma alanı veya lisans kullanan iş ortağı bir kuruluşla işbirliği yapmak için bir B2B extranet Azure Active Directory. Bu, kullanıcıların extranet sitesine veya ekibine kendi kendine kayıt yaptırarak onay iş akışı yoluyla erişim almalarını sağlar.

İş birliği için kaynakları paylaşma yöntemiyle, iş ortağı kuruluş, konuklarının bakım ve onaylamalarına yardımcı olarak, IT departmanınız üzerindeki yükü azaltıyor ve işbirliği anlaşmayı en iyi bilenlere kullanıcı erişimini yönetme izni verdi.

Bu makalede, self servis erişim kayıt modeli aracılığıyla iş ortağı bir kuruluşla paylaşabilirsiniz bir kaynak paketi (bu durumda bir site veya ekip) oluşturma adımlarında size yol gösterir. 

Başlamadan önce, iş ortağı kuruluşla paylaşmak istediğiniz siteyi veya ekibi oluşturun ve konuk paylaşımı için etkinleştirin. Daha [fazla bilgi için bkz. Sitede](collaborate-in-site.md) [konuklarla işbirliği yapma veya Ekipte konuklarla](collaborate-as-team.md) işbirliği yapma. Ayrıca konuklarla işbirliği içinde yönetim [](create-secure-guest-sharing-environment.md) ilkelerinizi korumanıza yardımcı olmak için kullanabileceğiniz güvenlik ve uyumluluk özellikleri hakkında bilgi için Güvenli bir konuk paylaşım ortamı oluşturma ortamı oluşturma'ya da gözden geçirmenizi öneririz.

## <a name="license-requirements"></a>Lisans gereksinimleri

Bu özelliği kullanmak için lisans Azure AD Premium P2 gerekir. 

Azure Germany ve Azure China 21Vianet gibi özel bulutlar şu anda kullanılamaz.

## <a name="video-demonstration"></a>Video tanıtımı

Bu videoda, bu makalede ele alan yordamlar göstermektedir.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4wKUj?autoplay=false]

## <a name="connect-the-partner-organization"></a>Bağlan kuruluşunda yer alan

İş ortağı kuruluşundan konukları davet etmek için, iş ortağının etki alanını bağlantılı kuruluş olarak İş Ortağı Merkezi'ne Azure Active Directory.

Bağlı kuruluş eklemek için
1. Aşağıdaki [Azure Active Directory](https://aad.portal.azure.com) **Yönetimi'ne tıklayın**.
2. Bağlı **kuruluşlar'a tıklayın**.
4. Bağlı kuruluş **ekle'ye tıklayın**.
5. Kuruluş için bir ad ve açıklama yazın, ardından Sonraki **: Dizin + etki alanı'ne tıklayın**.
6. Dizin + **etki alanı ekle'ye tıklayın**.
7. Bağlanmak istediğiniz kuruluşun etki alanını yazın ve Ekle'ye **tıklayın**.
8. **Sponsorlar Bağlan** a ve ardından Sonraki **: Sponsorlar'a tıklayın**.
9. Konuklar için erişimi onaylamak istediğiniz kişilerden, organizasyondan veya bağlantıda olduğunuz kuruluştan kişi ekleyin.
10. Sonraki **: Gözden Geçir + Oluştur'a tıklayın**.
11. Seçtiğiniz ayarları gözden geçirin ve Oluştur'a **tıklayın**.

    ![Azure Active Directory'da bağlı kuruluşlar sayfasının ekran Azure Active Directory.](../media/identity-governance-connected-organizations.png)

## <a name="choose-the-resources-to-share"></a>Paylaşacağız kaynakları seçme

İş ortağı bir kuruluşla paylaşmak istediğiniz kaynakları seçmenin ilk adımı, bunları içeren bir katalog oluşturmaktır.

Katalog oluşturmak için
1. Aşağıdaki [Azure Active Directory](https://aad.portal.azure.com) **Yönetimi'ne tıklayın**.
2. **Kataloglar'a tıklayın**.
3. Yeni **katalog'a tıklayın**.
4. Katalog için bir ad ve açıklama yazın ve Dış kullanıcılar için **Etkinleştirilen** ve **Etkin'in her ikisinin de Evet** olarak **ayarlayın.**
5. **Oluştur'a tıklayın**.

   ![Kimlik Yönetimi'ne giriş sayfasındaki Azure Active Directory ekran görüntüsü.](../media/identity-governance-catalogs.png)

Katalog oluşturulduktan sonra, iş ortağı SharePoint paylaşmak istediğiniz siteyi veya ekibi ekleyin.

Kataloga kaynak eklemek için
1. Azure AD Kimlik **Yönetimi'ne tıklayın**, Kataloglar'a tıklayın ve sonra da kaynakları eklemek istediğiniz kataloga tıklayın.
2. **Kaynaklar'a** ve ardından Kaynak **ekle'ye tıklayın**.
3. Extranet'SharePoint istediğiniz ekipleri veya siteyi seçin ve Ekle'ye **tıklayın**.

   ![Kimlik Yönetimi'ne giriş sayfasında katalog Azure Active Directory ekran görüntüsü.](../media/identity-governance-catalog-resource.png)

Paylaşmak istediğiniz kaynakları tanımdan sonra, bir sonraki adım iş ortağı kullanıcılarına verilen erişim türünü tanımlayan bir erişim paketi oluşturmak ve erişim isteyen yeni iş ortağı kullanıcıları için onay işlemini yapmaktır.

Erişim paketi oluşturmak için
1. Azure AD Kimlik **Yönetimi'ne tıklayın**, Kataloglar'a tıklayın ve sonra da erişim paketi oluşturmak istediğiniz kataloga tıklayın.
2. **Access paketleri'ne** ve ardından Yeni erişim **paketi'ne tıklayın**.
3. Erişim paketi için bir ad ve açıklama yazın ve ardından Sonraki **: Kaynak rolleri'ne tıklayın**.
4. Extranet'iniz için kullanmak istediğiniz kaynakları katalogdan seçin.
5. Her kaynak için **Rol sütununda** , extranet'i kullanan konuklara vermek istediğiniz kullanıcı rolünü seçin.
6. Sonraki **: İstekler'e tıklayın**.
7. Erişim **isteyen kullanıcılar'ın altında Dizinde** **yer alan kullanıcılar için'i seçin**.
8. Belirli bağlı kuruluşlar **seçeneğinin seçildiğinden** emin olun ve Dizin **ekle'ye tıklayın**.
9. Daha önce eklemek istediğiniz bağlı kuruluşu seçin ve ardından Seç'e **tıklayın.**
10. Onay **altında,** Onay **gerektir için** **Evet'i seçin**.
11. İlk **onaylayan altında**, daha önce ekleytüytüniz sponsorlardan birini seçin veya belirli bir kullanıcı seçin.
12. Geri **dönüş ekle'ye** tıklayın ve bir geri dönüş onaylayanı seçin.
13. **Etkinleştir'in** altında Evet'i **seçin**.
14. Sonraki: **Yaşam Döngüsü'ne tıklayın**.
15. Kullanmak istediğiniz süre sonu ve erişim gözden geçirme ayarlarını seçin ve ardından Sonraki: Gözden Geçir **+ Oluştur'a tıklayın**.
16. Ayarlarınızı gözden geçirin ve Oluştur'a **tıklayın**.

    ![Kimlik Yönetimi'nin erişim paketleri Azure Active Directory ekran görüntüsü.](../media/identity-governance-access-packages.png)

Büyük bir kuruluşla iş ortağınız varsa, erişim paketini gizlemek istiyor olabilir. Paket gizlenmişse, iş ortağı kuruluşta olan kullanıcılar Erişimim portalında paketi *göremez* . Bunun yerine, pakete kaydolmaları için doğrudan bir bağlantı göndermeleri gerekir. Erişim paketinin gizlensi, uygun olmayan erişim isteklerinin sayısını azaltıp kullanılabilir erişim paketlerini iş ortağı kuruluşun portalında düzenli tutmaya yardımcı olabilir.

Erişim paketini gizli olarak ayarlamak için
1. Azure AD Kimlik Yönetimi'nden, **Access paketleri'ne** ve sonra da erişim paketinize tıklayın.
2. Genel Bakış **sayfasında** Düzenle'ye **tıklayın**.
3. **Özellikler'in** altında Gizli **için** **Evet'i seçin** ve kaydet'e **tıklayın**.

   ![Erişim paketi özelliklerini düzenleme ekran görüntüsü.](../media/identity-governance-access-package-hidden.png)

## <a name="invite-partner-users"></a>İş ortağı kullanıcılarını davet etme

Erişim paketini gizli olarak ayarsanız, iş ortağı kuruluşa doğrudan bir bağlantı göndermeniz gerekir; böylece onlar da sitenize veya takımınıza erişim isteğinde olabilir.

Erişim portalı bağlantısını bulmak için
1. Azure AD Kimlik Yönetimi'nden, **Access paketleri'ne** ve sonra da erişim paketinize tıklayın.
2. Genel Bakış **sayfasında** , **Erişimim portalı bağlantısı için** Panoya **kopyala bağlantısına tıklayın**.

   ![Erişim portalı bağlantısıyla birlikte erişim paketi özelliklerinin ekran görüntüsü.](../media/identity-governance-access-portal-link.png)

Bağlantıyı kopya sonra, iş ortağı kuruluşta ilgili kişi ile paylaşabilirsiniz ve onlar da bağlantıyı kendi işbirliği ekibinde yer alan kullanıcılara gönderebilir.

## <a name="see-also"></a>Ayrıca Bkz

[Güvenli bir konuk paylaşım ortamı oluşturma](create-secure-guest-sharing-environment.md)