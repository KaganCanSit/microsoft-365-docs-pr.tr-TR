---
title: Oturum için idle session timeout Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Adm_TOC
description: Kullanıcının oturumunun zamanları ne kadar Microsoft 365 içinde ne kadar süreyle devam eeceklerini ayarlayın.
ms.openlocfilehash: 215b900315b2d98b01a8cf87b14a6fa65289e121
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2022
ms.locfileid: "63705372"
---
# <a name="idle-session-timeout-for-microsoft-365-public-preview"></a>Microsoft 365 için boşta Microsoft 365 zaman aşımı (Genel önizleme)

<!-- Add metadata: localization, AdminSurgePortfolio, admindeeplinkMAC. remove robots nofollow -->

Kullanıcıların web uygulamalarıyla oturumları dışında kalmadan önce kuruluşta ne kadar süreyle etkin olmayan kullanıcılar olduğunu ilke olarak yapılandırmak için boşta Microsoft 365 kullanın. Bu, hassas şirket verilerini korumaya yardımcı olur ve şirket dışı veya paylaşılan cihazlarda çalışan son kullanıcılar için bir güvenlik katmanı daha ekler.

Bir kullanıcı ayarmış olduğunuz boşta kalma zaman aşımı oturumuna ulaştığında, oturumunun açık olduğunu haber alır. Oturumlarının açık kalmasını seçmeleri gerekir veya tüm web uygulamalarınız için oturumları otomatik Microsoft 365 olur.

> [!IMPORTANT]
> Boşta oturum zaman aşımı, masaüstü ve Microsoft 365 uygulamalarınızı etkilemez.

## <a name="turn-on-idle-session-timeout"></a>Idle oturum zaman aşımını açma

Yönetici veya genel Microsoft 365 Office 365 değilseniz, Güvenlik ayarları veya **gizlilik & göresiniz**.

1. Kuruluş Microsoft 365 yönetim merkezi Güvenlik  **->** Ayarlar [Gizlilik sekmesine &](https://go.microsoft.com/fwlink/p/?linkid=2072756) Idle **session timeout öğesini seçin**.  

2. Idle **Session Timeout'ta** açmak için iki durumlu düğmeyi seçin. Varsayılan bir ayar seçebilir veya kendi özel saatlerinizi seçebilirsiniz. Kurumda boşta oturumun açık durumdaki süresi birkaç dakika sürer.

> [!NOTE]
> [Outlook web](https://support.microsoft.com/topic/description-of-the-activity-based-authentication-timeout-for-owa-in-office-365-0c101e1b-020e-69c1-a0b0-26532d60c0a4) uygulaması ve [SharePoint Online](/sharepoint/sign-out-inactive-users) için boşta oturum zaman aşımı ilkeleri ayarladıysanız, Microsoft 365 yönetim merkezi'te boşta kalma oturumu zaman aşımını açma, Outlook web uygulamasını ve SharePoint ayarlarını geçersiz kılar.

Idle session timeout is one of the many security measures in Microsoft 365. Çalışma 2013'te diğer güvenlik Microsoft 365 [hakkında bilgi edinmek için](../../security/top-security-tasks-for-remote-work.md) bkz. Microsoft 365.  

## <a name="what-users-will-see"></a>Kullanıcıların göreceği

Bir kullanıcı seçtiğiniz süre boyunca Microsoft 365 web uygulamaları üzerinde etkin değilken aşağıdaki istemi görebilir. Oturum açık **kal'ı seçmeleri** , yoksa oturumları da imzalanmış olur.

:::image type="content" source="../../media/idle-session-timeout.png" alt-text="Ekran görüntüsü: Oturum sürenizin dolmak üzere olduğunu size bilgi istemiyle haber verme. Oturumları ve web uygulamalarıyla ilgili oturumları imzalamak için Oturum Microsoft 365 seçin":::

## <a name="details-about-idle-session-timeout"></a>Boşta oturumu zaman aşımı ile ilgili ayrıntılar

- Aşağıdaki Microsoft 365 web uygulamaları destekledir. Yakında daha fazla web uygulaması eklenecektir.

    - Outlook Web App

    - OneDrive İş

    - SharePoint Online (SPO)

    - Office.com ve diğer başlangıç sayfaları

    - Office web üzerinde Excel (Word, PowerPoint, PowerPoint)

    - Microsoft 365 Yönetici Merkezi

- Etkinlik, web uygulamasının bağlamında olan herhangi bir istemci tarafı kullanıcı etkileşimi anlamına gelir. Örneğin, fare tıklamaları ve klavye basları.  

- Idle session timeout works on a browser session basis. Bir kullanıcının Google Chrome Microsoft Edge tarayıcılarda yaptıkları etkinlikten farklı şekilde işlem yapılır. Kullanıcıların oturumları, tarayıcı oturumunda hesaplarına karşılık gelen tüm sekmelerde oturumları açılır.

- Boşta kalma oturumu zaman aşımını açtıktan sonra bu tüm kuruluş için geçerlidir ve belirli kullanıcılar, kuruluş birimleri veya gruplar kapsamında değildir. Farklı [kullanıcılar ve gruplara yönelik ilkeler için Azure AD](/azure/active-directory/conditional-access/) Koşullu Erişim'i kullanın.

- Kullanıcılar, yapılandırılmış süre boyunca Microsoft 365 web uygulaması sekmelerinde etkin değildir. Kullanıcı bir sekmede (örneğin OWA) etkinken başka bir sekmede (örneğin SPO) etkinse, etkin olduğu kabul edilir ve oturumları da açıklanmaz.  

- Bu durumlarda kullanıcılar oturumlarını atamaz.
    - Cihaz tarafından bir araya gelen hesaptan web uygulamasına çoklu oturum açma (SSO) alındı ise veya oturum açma  zamanında oturum aç'a seçiliyse. Bu seçeneğin kurum için gizlen hakkında daha fazla bilgi için bkz. [Kuruluş oturum açma sayfasına markalama ekleme](/azure/active-directory/fundamentals/customize-branding).
    - Yönetilen bir cihazdaysa (bir etki alanına uyumlu veya bir etki alanına katılmış) ve Microsoft Edge ya da Google Chrome (Windows Hesapları uzantısıyla) gibi desteklenen [bir tarayıcı kullanıyorsa](https://chrome.google.com/webstore/detail/windows-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji). Bu özelliğin yönetilen bir cihazda tetikleyicisi olmaz, uygun bir Azure AD Premium P1 veya P2 aboneliği ve belirli bir Koşullu Erişim ilkesi gereklidir. Diğer ayrıntılar için aşağıya bakın.

> [!IMPORTANT]
> 21Vianet tarafından çalıştırılan Microsoft 365 veya Almanya'da boşta kalma oturum zaman aşımı Microsoft 365 kullanılamaz.

## <a name="idle-session-timeout-on-unmanaged-devices"></a>Unmanaged cihazlarda idle session timeout  

Yönetnemeyen cihazlarda boşta oturumu zaman aşımına neden olmak için Azure AD yönetim merkezine bir Koşullu Erişim ilkesi eklemeniz gerekir.

1. Koşullu **Erişim |** Azure AD yönetim merkezinin İlkeler sayfasında Yeni **ilke'yi** seçin ve ilke için bir ad girin.

2. Kullanıcılar **veya iş yükü kimlikleri'ne ve** sonra Tüm **kullanıcılar'a seçin**.

3. Bulut **uygulamaları veya eylemler'i**, **Uygulamaları seçin'i** seçin **ve Office 365.** **Tamam'Office 365** ardından **Seç'i seçin**.  

4. Koşullar **,** İstemci **uygulamaları, Evet**, **Tarayıcı olarak** **Yapılandır'ı ve** ardından Bitti'yi **seçin**.

5. **Oturum'ı** **seçin, Uygulamanın zorunlu kısıtlamalarını kullan'ı** ve sonra da **Seç'i seçin**.

6. İlkeyi oluşturun ve Oluştur'a **seçin**.

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="are-there-any-browsers-or-browser-scenarios-in-which-idle-session-timeout-feature-doesnt-work"></a>Boşta boşta oturum zaman aşımı özelliğinin çalışmay olduğu tarayıcılar veya tarayıcı senaryoları var mı?  

Tarayıcıda üçüncü taraf tanımlama bilgileri devre dışı bırakılmıştır ve boşta kalma oturumu zaman aşımı desteklenmiyor. Kullanıcılar hiçbir oturum açma istemi görmez. Diğer tarayıcılar için izleme engelleme ayarını [Dengeli (Varsayılan)](/microsoft-edge/web-platform/tracking-prevention) Microsoft Edge ve diğer tarayıcılarda üçüncü taraf tanımlama bilgileri etkin durumda tutmanızı öneririz. Microsoft 365 17 Ağustos 2021'den bu yana uygulamalar ve hizmetler Internet Explorer 11'i desteklemeyi durdurdu.

### <a name="how-should-i-prepare-if-my-organization-is-already-using-existing-outlook-web-app-and-sharepoint-online-idle-timeout-policies"></a>Kuruluşum zaten var olan Outlook web uygulamasını kullanıyorsa ve SharePoint Online boşta kalma zaman aşımı ilkelerini kullanıyorsa nasıl hazırlanmam gerekir?  

Zaten var olan Outlook web uygulamasını kullanıyorsanız ve SharePoint Online boşta kalma zaman aşımı ilkelerini kullanıyorsanız, yine de boşta oturum zaman aşımı özelliğini açabilirsiniz. Boşta kalma zaman aşımı ilkesini açtıktan sonra, bu ilke var olan Outlook ve SharePoint Online ilkelerine göre öncelikli olur. Yakın gelecekte var olan Outlook Web App ve SharePoint Online ilkelerini kullanımdandan gitmeyi planlıyoruz. Organizasyonlarınızı daha iyi hazırlamak için boşta bekleme süresini açmanızı öneririz.

### <a name="what-happens-if-i-am-inactive-on-an-included-microsoft-365-web-app-but-active-on-a-microsoft-web-app-or-saas-web-app-that-doesnt-have-idle-session-timeout-turned-on"></a>Dahil edilen bir Microsoft 365 web uygulamasında etkin değilken boşta oturum zaman aşımı açık olmayan bir Microsoft web uygulamasında veya SaaS web uygulamasında etkin olduğumda ne olur?  

Aşağıdaki Microsoft 365 web uygulamaları destekledir.

- Outlook Web App

- OneDrive İş

- SharePoint Online (SPO)

- Office.com ve diğer başlangıç sayfaları

- Office web üzerinde Excel (Word, PowerPoint, PowerPoint)

- Microsoft 365 Yönetici Merkezi

Aynı hesabı olan başka bir web uygulaması üzerinde çalışıyorsanız, bu web uygulamasındaki etkinlik boşta kalma oturumu zaman aşımına uygulanmaz.

### <a name="i-want-to-make-changes-to-the-idle-session-timeout-policy-or-delete-it-how-can-i-do-that"></a>Boşta boşta oturumu zaman aşımı ilkesinde değişiklik yapmak veya ilkeyi silmek istiyorum. Bunu nasıl yapabilirim?

İlkeyi güncelleştirin:

1. Aşağıdaki Microsoft 365 yönetim merkezi **Ayarları'ı seçin**, Güvenlik ve Gizlilik **& Idle** **session timeout öğesini seçin**.

2. Açılan menüde farklı bir zaman aşımı değeri seçin ve ardından Kaydet'i **seçin**.  

İlkeyi silin:

1. Aşağıdaki Microsoft 365 yönetim merkezi **Ayarları'ı seçin**, Güvenlik ve Gizlilik **& Idle** **session timeout öğesini seçin**.

2. Diğer **web uygulamalarıyla kullanan kullanıcıların** oturum kapatma sürelerini ayarlamak için Aç'ın Office kaydet'i **seçin**.
