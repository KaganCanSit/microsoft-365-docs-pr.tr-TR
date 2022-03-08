---
title: Ekipte konuklarla işbirliği yapma
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
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkTEAMS
- admindeeplinkSPO
ms.localizationpriority: high
f1.keywords: NOCSH
recommendations: false
description: Konuk ekibin Microsoft 365, konuşma ve belgelerle işbirliği yapmak için gerekli yapılandırma adımları hakkında bilgi Teams.
ms.openlocfilehash: bb6ccf4f3e17192d86675d99072eca8b836973e2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324557"
---
# <a name="collaborate-with-guests-in-a-team"></a>Ekipte konuklarla işbirliği yapma

Konuklarla belgeler, görevler ve konuşmalar arasında işbirliği yapmak için bu belgeleri Microsoft Teams. Teams, kalıcı sohbet ve birleşik bir kullanıcı deneyiminde özelleştirilebilir ve genişletilebilir bir işbirliği araçları kümesiyle Office ve SharePoint'te kullanılabilen tüm işbirliği özelliklerini sağlar.

Bu makalede, konuklarla işbirliğine Microsoft 365 için gerekli tüm yapılandırma adımlarını takip edeceğiz. Konuk erişimini yapılandırdıktan sonra, Teams'de ek ekiplere konuk ekleme'de yer alan [adımları kullanarak konukları ekiplere Teams](https://support.microsoft.com/office/fccb4fa6-f864-4508-bdde-256e7384a14f).

## <a name="video-demonstration"></a>Video tanıtımı

Bu videoda, bu belgede açıklanan yapılandırma adımları gösterir.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44NTr?autoplay=false]

## <a name="azure-external-collaboration-settings"></a>Azure Dış işbirliği ayarları

Dış Microsoft 365, çalışma sayfasındaki [B2B dış işbirliği ayarları tarafından en yüksek Azure Active Directory](/azure/active-directory/external-identities/delegate-invitations). Azure AD'de konuk paylaşımı devre dışı bırakılmış veya kısıtlanmışsa, bu ayar Microsoft 365.

Konuklarla paylaşımın engellenmiş olduğundan emin olmak için B2B dış işbirliği ayarlarına göz yapın.

![Kurumsal İlişkiler Azure Active Directory sayfası Ayarlar ekran görüntüsü.](../media/azure-ad-organizational-relationships-settings.png)

Dış işbirliği ayarlarını ayarlamak için

1. Azure Active Directory'ta oturum açma[https://aad.portal.azure.com](https://aad.portal.azure.com).
2. Sol gezinti bölmesinde Ekle'ye **Azure Active Directory**.
3. Dış **kimlikler'e tıklayın**.
4. Çalışmaya başlama **ekranında,** sol gezinti bölmesinde Dış işbirliği **ayarları'ne tıklayın**.
5. Belirli yönetici **rollerine atanan** Üye kullanıcıların ve kullanıcıların, konuk kullanıcılar (üye izinleri olan konuklar dahil) davet etme veya Kuruluşta herkes konuk kullanıcılar (konuklar ve yönetici olmayanlar) seçili olarak davet olabilir.
6. Değişiklikler yaptıysanız Kaydet'e **tıklayın**.

İşbirliği kısıtlamaları bölümündeki **ayarlara dikkat** edin. Konukların işbirliği yapmak istediğiniz etki alanlarının engellenmiş olduğundan emin olun.

Birden çok kuruluştan konuklarla çalışıyorsanız, dizin verilerine erişim izinlerini kısıtlamak istemeyebilirsiniz. Bu, dizinde başka kimlerin konuk olduğunu görmelerini önler. Bunu yapmak için Konuk kullanıcı erişimi kısıtlamaları'nın **altında Konuk kullanıcıların** özelliklere erişimi ve dizin nesneleri ayarları üyeliği sınırlı seçeneğini veya Konuk kullanıcı erişimi kendi dizin nesnelerinin özellik ve üyelikleriyle **sınırlıdır**.

## <a name="teams-guest-access-settings"></a>Teams erişimi ayarlarını değiştirme

Teams erişim için bir ana açma/kapatma anahtarına ve konukların bir ekipte neler yaplarını denetlemeye uygun çeşitli ayarlar vardır. İş yerizde **konuk erişimine izin ver Teams** **ana anahtarı**, konuk erişiminin açık olması Teams.

Konuk erişiminin her gün etkinleştirildiğinden emin Teams ve konuk ayarlarında iş ihtiyaçlarına göre ayarlamalar yapın. Bu ayarların tüm ekipleri etkileyeceğini unutmayın.

![Konuk erişimi Teams iki durumlu düğmenin ekran görüntüsü.](../media/teams-guest-access-toggle-on.png)

Konuk erişimi Teams ayarlarını yapmak için

1. hesabıyla oturum Microsoft 365 yönetim merkezi.[https://admin.microsoft.com](https://admin.microsoft.com)
2. Sol gezinti bölmesinde, Hepsini **göster'e tıklayın**.
3. Yönetim **merkezleri altında,** Yönetim **Merkezi'nin Teams**.
4. Teams yönetim merkezinde, sol gezinti bölmesinde <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**UsersGuest access öğesini**</a> >  seçin.
5. **E-postada konuk erişimine izin ver Teams'in** On olarak ayar olduğundan emin **olun**.
6. Ek konuk ayarlarında istediğiniz değişiklikleri yapın ve ardından Kaydet'e **tıklayın**.

Konuk Teams açıkken, isteğe bağlı olarak duyarlılık etiketlerini kullanarak tek tek ekiplere ve konukla ilişkilendirilmiş SharePoint erişimini kontrol edin. Daha fazla bilgi için bkz. Site site sitelerine, [gruplara ve sitelere Microsoft Teams Microsoft 365 için duyarlılık SharePoint kullanma](../compliance/sensitivity-labels-teams-groups-sites.md).

> [!NOTE]
> Bu ayarın etkin olması için konuk ayarlarının Teams olması yirmi dört saat kadar sürebilir.

## <a name="microsoft-365-groups-guest-settings"></a>Microsoft 365 Grupları konuk ayarlarını değiştirme

Teams üyeliği Microsoft 365 grupları kullanır. Konuk Microsoft 365 için grup gruplarında konuk ayarlarının açık olması gerekir. Bu Teams gerekir.

![Grup Grup Microsoft 365 ayarlarının ekran Microsoft 365 yönetim merkezi.](../media/office-365-groups-guest-settings.png)

Grup konuk Microsoft 365 ayarlarını ayarlamak için

1. Gezinti Microsoft 365 yönetim merkezi gezinti bölmesinde Gezinti **Bölmesi'ni Ayarlar**.
2. Kuruluş **ayarları'ne tıklayın**.
3. Listede Grup **Ekle'Microsoft 365 tıklayın**.
4. Grup sahiplerinin kuruluş **dışından kişi eklemesine izin ver Microsoft 365 Grupları** konuk olarak ekle ve Konuk grup üyelerinin grup içeriğine erişmesine izin **ver onay** kutularının her ikisi de işaretlidir.
5. Değişiklik yaptıysanız, Değişiklikleri **kaydet'e tıklayın**.


## <a name="sharepoint-organization-level-sharing-settings"></a>SharePoint düzeyinde paylaşım ayarlarını değiştirme

Teams, klasörler ve listeler gibi tüm içerikler dosya veya kitaplıkta SharePoint. Konukların Teams'ta bu öğelere erişimi olması için, SharePoint düzeyinde paylaşım ayarlarının konuklarla paylaşım için izin vermesi gerekir.

Kuruluş düzeyindeki ayarlar, ekiplerle ilişkilendirilmiş siteler dahil olmak üzere tek tek siteler için hangi ayarların kullanılabilir olduğunu belirler. Site ayarları, kuruluş düzeyindeki ayarlardan daha izinli olamaz.

Kimliği doğrulanmamış kullanıcılarla dosya ve klasör paylaşımına izin vermek için Herkes'i **seçin**. Tüm konukların kimlik doğrulaması yapmak zorunda olduğundan emin olmak için Yeni ve mevcut **konuklar'ı seçin**. Kuruluş herhangi bir site tarafından gerekli olacak en izinli ayarı seçin.

![Kuruluş düzeyi SharePoint ayarlarının ekran görüntüsü.](../media/sharepoint-organization-external-sharing-controls.png)


Kuruluş SharePoint paylaşım ayarlarını ayarlamak için

1. Gezinti <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a>, sol gezinti bölmesindeki Yönetim **merkezleri'nin altında** **Seçenekler'i SharePoint**.
2. SharePoint yönetim merkezinde, sol gezinti bölmesinde İlkeler'i **genişletin ve sonra** Paylaşım'ı <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**seçin**</a>.
3. Dış paylaşım için dış SharePoint Herkes veya Yeni **ve var olan** **konuklar olarak ayarlayın**.
4. Değişiklik yaptıysanız Kaydet'i **seçin**.


## <a name="sharepoint-organization-level-default-link-settings"></a>SharePoint düzeyinde varsayılan bağlantı ayarlarını değiştirme

Varsayılan dosya ve klasör bağlantısı ayarları, bir dosya veya klasör paylaştıklarda kullanıcılara varsayılan olarak gösterilecek bağlantı seçeneğini belirler. Kullanıcılar,  istediklerinizi paylaşmadan önce bağlantı türünü diğer seçeneklerden biri ile değiştirebilir.

Bu ayarın tüm ekipleri ve tüm ekiplerini SharePoint etkileyeceğini unutmayın.

Kullanıcılar dosya ve klasör paylaştığında varsayılan olarak seçilen aşağıdaki bağlantı türlerinden herhangi birini seçin:

- **Bağlantısı olan herkes** - Çok fazla sayıda kimliği doğrulanmamış dosya ve klasör paylaşımı görmeyi bekliyorsanız bu seçeneği belirtin. Herkes bağlantılarına izin *vermek istiyor* ancak kimliği doğrulanmamış paylaşım konusunda endişeleniyorsanız, varsayılan olarak diğer seçeneklerden birini kullanın. Bu bağlantı türü yalnızca Herkes paylaşımını **etkinleştirdiysen** kullanılabilir.
- **Yalnızca kuruluş içindeki kişiler** - Çoğu dosya ve klasör paylaşımının kuruluş içindeki kişilerle olmasını bekliyorsanız bu seçeneği belirleyin.
- **Belirli kişiler** - Konuklarla çok fazla dosya ve klasör paylaşımı olmasını bekliyorsanız, bu seçeneği göz önünde bulundurabilirsiniz. Bu bağlantı türü konuklar için çalışır ve konukların kimlik doğrulamasını gerektirir.
 
![Kuruluş düzeyi SharePoint klasörleri paylaşma ayarlarının ekran görüntüsü.](../media/sharepoint-organization-files-folders-sharing-settings.png)


Kuruluş düzeyinde SharePoint bağlantı ayarlarını ayarlamak için

1. Yönetim <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**merkezinde Paylaşım**</a> SharePoint gidin.
2. Dosya **ve klasör bağlantıları'nın** altında, kullanmak istediğiniz varsayılan paylaşım bağlantısını seçin.
3. Değişiklik yaptıysanız Kaydet'i **seçin**.

## <a name="create-a-team"></a>Ekip oluşturma

Sonraki adım, konuklarla işbirliği yapmak için kullanmayı planlayın ekibi oluşturmak olur.

Ekip oluşturmak için
1. Giriş Teams, Oluştur **Teams** sol **bölmenin alt kısmında Bulunan** ekle veya ek ekip oluştur'a tıklayın.
2. Ekip **oluştur'a tıklayın**.
3. **Sıfırdan ekip oluşturma'ya tıklayın**.
4. Özel  veya **Genel'i seçin**.
5. Ekip için bir ad ve açıklama yazın, ardından Oluştur'a **tıklayın**.
6. **Atla'ya tıklayın**.

Kullanıcıları daha sonra davetacağız. Daha sonra, ekiple ilişkili sitenin site SharePoint paylaşım ayarlarını denetlemeniz önemlidir.

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint düzeyinde paylaşım ayarlarını değiştirme

Bu ekip için istediğiniz erişim türüne izin vermek için site düzeyinde paylaşım ayarlarını kontrol edin. Örneğin, kuruluş düzeyi ayarlarını Herkes olarak ayarlarsanız **ancak tüm** konukların bu ekip için kimlik doğrulaması yapmalarını istiyorsanız, site düzeyinde paylaşım ayarlarının Yeni ve mevcut konuklar olarak ayarlanmış olduğundan **emin olun**.

![Site dış SharePoint ayarlarının ekran görüntüsü.](../media/sharepoint-site-external-sharing-settings.png)

Site düzeyinde paylaşım ayarlarını ayarlamak için
1. Gezinti SharePoint gezinti bölmesinde Siteler'i genişletin ve **Etkin** <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**siteler'i seçin**</a>.
2. Yeni oluşturduğunuz ekip için siteyi seçin.
3. Şu seçeneği seçin: ... ve **Paylaşım'ı seçin**.
4. Paylaşımın Herkes veya Yeni ve mevcut **konuklar** **olarak ayarlanmış olduğundan emin olmak**.
5. Değişiklik yaptıysanız Kaydet'i **seçin**.

## <a name="invite-users"></a>Kullanıcıları davet et

Konuk paylaşım ayarları artık yapılandırılmıştır, böylece iç kullanıcıları ve konukları takımınıza eklemeye başlayabilirsiniz. 

İç kullanıcıları bir takıma davet etmek için
1. Ekipte Diğer seçenekler () **ve ardından****\*\*\*** Üye **ekle'ye tıklayın**.
2. Davet etmek istediğiniz kişinin adını yazın.
3. **Ekle'yi** ve ardından Kapat'ı **tıklatın**.

Konukları bir takıma davet etmek için
1. Ekipte Diğer seçenekler () **ve ardından****\*\*\*** Üye **ekle'ye tıklayın**.
2. Davet etmek istediğiniz konuğun e-posta adresini yazın.
3. Konuk **bilgilerini düzenle'ye tıklayın**.
4. Konuğun tam adını yazın ve onay işaretine tıklayın.
5. **Ekle'yi** ve ardından Kapat'ı **tıklatın**.

> [!NOTE]
> İş veya okul hesabı olan konuklar yalnızca Kullanıcı Asıl Adı (UPN) (örneğin, Okul Adı) kullanılarak davet adele@contoso.com. EAS KIMLIĞI veya diğer e-posta biçimlerini kullanarak konuk davet etme desteklenemektedir.

## <a name="see-also"></a>Ayrıca bkz.

[Kimliği doğrulanmamış kullanıcılarla dosya ve klasör paylaşmak için en iyi yöntemler](best-practices-anonymous-sharing.md)

[Konuklarla paylaşım sırasında dosyalarda yanlışlıkla açık kalma sürelerini sınırlama](share-limit-accidental-exposure.md)

[Güvenli bir konuk paylaşım ortamı oluşturma](create-secure-guest-sharing-environment.md)

[Yönetilen konuklarla B2B extranet oluşturma](b2b-extranet.md)

[Azure Active Directory B2B ile SharePoint ve OneDrive tümleştirmesi](/sharepoint/sharepoint-azureb2b-integration-preview)

[Bir dosyadan veya dosyadan paylaşım SharePoint seçenekleri gri OneDrive](/sharepoint/troubleshoot/administration/sharing-options-grayed-out-when-sharing-from-sharepoint-online-or-onedrive)
