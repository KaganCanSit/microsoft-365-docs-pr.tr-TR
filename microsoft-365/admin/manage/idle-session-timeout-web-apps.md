---
title: Microsoft 365 için boşta oturum zaman aşımı
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
description: Kullanıcının oturumlarının zaman aşımına uğramadan önce Microsoft 365'te ne kadar süreceğini ayarlayın.
ms.openlocfilehash: 611541ebc16c3ee8c187b8fc1a5b33661b221897
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487487"
---
# <a name="idle-session-timeout-for-microsoft-365"></a>Microsoft 365 için boşta oturum zaman aşımı

<!-- Add metadata: localization, AdminSurgePortfolio, admindeeplinkMAC. remove robots nofollow -->

Microsoft 365 web uygulamalarının oturumunun kapatılmadan önce kuruluşunuzda etkin olmayan kullanıcılarla ilgili bir ilke yapılandırmak için boşta oturum zaman aşımını kullanın. Bu, hassas şirket verilerini korumaya yardımcı olur ve şirket dışı veya paylaşılan cihazlarda çalışan son kullanıcılar için başka bir güvenlik katmanı ekler.

Bir kullanıcı ayarladığınız boşta kalma zaman aşımı oturumuna ulaştığında, oturumun kapatılacağını belirten bir bildirim alır. Oturumunun açık kalmasını seçmek zorundalar, aksi durumda tüm Microsoft 365 web uygulamalarında otomatik olarak oturumları kapatılacaktır.

> [!IMPORTANT]
> Boşta oturum zaman aşımı Microsoft 365 masaüstü ve mobil uygulamalarınızı etkilemez.

## <a name="turn-on-idle-session-timeout"></a>Boşta oturumu zaman aşımını açma

Microsoft 365 veya Office 365 genel yönetici değilseniz **Güvenlik & gizlilik** sekmesini görmezsiniz.

1. Microsoft 365 yönetim merkezi **Kuruluş Ayarları** **->**[Güvenlik & gizlilik](https://go.microsoft.com/fwlink/p/?linkid=2072756) sekmesini ve **Boşta oturum zaman aşımı'nı** seçin.  

2. **Boşta Oturum Zaman Aşımı'nda** açmak için iki durumlu düğmeyi seçin. Varsayılan bir ayar seçebilir veya kendi özel zamanınızı seçebilirsiniz. Kuruluşunuzda boşta oturum açma işlemi birkaç dakika sürer.

> [!NOTE]
> [Outlook web uygulaması](https://support.microsoft.com/topic/description-of-the-activity-based-authentication-timeout-for-owa-in-office-365-0c101e1b-020e-69c1-a0b0-26532d60c0a4) ve [SharePoint Online](/sharepoint/sign-out-inactive-users) için boşta oturum zaman aşımı ilkeleri ayarladıysanız, Microsoft 365 yönetim merkezi boşta oturum zaman aşımını açtığınızda Outlook web uygulaması ve SharePoint ayarları geçersiz kılınır.

Boşta oturum zaman aşımı, Microsoft 365'teki birçok güvenlik önlemi arasında yer alır. Microsoft 365'teki diğer güvenlik görevleri hakkında bilgi edinmek için bkz. [Microsoft 365'teki en önemli güvenlik görevleri](../../security/top-security-tasks-for-remote-work.md).  

## <a name="what-users-will-see"></a>Kullanıcıların görecekleri

Bir kullanıcı seçtiğiniz süre boyunca Microsoft 365 web uygulamalarında etkin olmadığında aşağıdaki istemi görür. **Oturum açık kalsın'ı** seçmeleri gerekir, aksi durumda oturumları kapatılacaktır.

:::image type="content" source="../../media/idle-session-timeout.png" alt-text="Ekran görüntüsü: Oturumunuzun süresinin dolmak üzere olduğunu bildiren istem. Microsoft 365 web uygulamalarının oturumunun kapatılamaması için Oturum açık kalsın'ı seçin":::

## <a name="details-about-idle-session-timeout"></a>Boşta oturum zaman aşımı hakkındaki ayrıntılar

- Aşağıdaki Microsoft 365 web uygulamaları desteklenir. Yakında daha fazla web uygulaması eklenecektir.

    - Outlook Web App

    - OneDrive İş

    - SharePoint Online (SPO)

    - Office.com ve diğer başlangıç sayfaları

    - Web üzerinde Office (Word, Excel, PowerPoint)

    - Microsoft 365 Yönetici Merkezi

- Etkinlik, web uygulaması bağlamında gerçekleşen istemci tarafı kullanıcı etkileşimlerini ifade eder. Örneğin, fare tıklamaları ve klavye basmaları.  

- Boşta oturum zaman aşımı tarayıcı başına oturum temelinde çalışır. Kullanıcının Microsoft Edge'deki etkinliği, Google Chrome gibi diğer tarayıcılardaki etkinliklerinden farklı olarak değerlendirilir. Kullanıcılar, bu tarayıcı oturumunda hesaplarına karşılık gelen tüm sekmelerde oturumu kapatılır.

- Boşta oturum zaman aşımını açtıktan sonra, bu durum tüm kuruluşunuz için geçerlidir ve kapsamı belirli kullanıcılar, kuruluş birimleri veya gruplara eklenemez. SharePoint'e ve Exchange Online erişmek için farklı kullanıcılar ve gruplar için Azure AD [Koşullu Erişim](/azure/active-directory/conditional-access/) ilkelerini kullanın.

- Kullanıcıların yapılandırılan süre boyunca tüm Microsoft 365 web uygulaması sekmelerinde etkin olmamalıdır. Kullanıcı başka bir sekmede etkin değilken (OWA gibi) bir sekmede etkinse (SPO gibi), etkin olarak kabul edilir ve oturumu kapatılmaz.  

- Bu durumlarda kullanıcıların oturumları kapatılamaz.
    - Cihaza katılmış hesaptan web uygulamasında çoklu oturum açma (SSO) alıyorsa veya oturum açma sırasında **Oturum açık kalsın'ı** seçtiyse. Kuruluşunuzda bu seçeneği gizleme hakkında daha fazla bilgi için bkz. [Kuruluşunuzun oturum açma sayfasına marka ekleme](/azure/active-directory/fundamentals/customize-branding).
    - Yönetilen bir cihazdaysa (uyumlu veya bir etki alanına katılmış bir cihaz) ve Microsoft Edge veya Google Chrome gibi desteklenen bir tarayıcı kullanıyorsa ( [Windows Hesapları uzantısıyla](https://chrome.google.com/webstore/detail/windows-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji)). Bu özelliğin yönetilen bir cihazda tetiklenmemesi için uygun bir Azure AD Premium P1 veya P2 aboneliği ve belirli bir Koşullu Erişim ilkesi gerekir. Diğer ayrıntılar için aşağıya bakın.

> [!IMPORTANT]
> Boşta oturum zaman aşımı, 21Vianet veya Microsoft 365 Germany tarafından sağlanan Microsoft 365 için kullanılamaz.

## <a name="idle-session-timeout-on-unmanaged-devices"></a>Yönetilmeyen cihazlarda boşta oturum zaman aşımı  

Yönetilmeyen cihazlarda tetiklenen boşta oturum zaman aşımı için, Azure AD yönetim merkezine bir Koşullu Erişim ilkesi eklemeniz gerekir.

1. **Koşullu Erişim | Azure AD yönetim merkezinin İlkeler** sayfası, **Yeni ilke'yi** seçin ve ilke için bir ad girin.

2. **Kullanıcılar veya iş yükü kimlikleri'ne** ve ardından **Tüm kullanıcılar'a** tıklayın.

3. **Bulut uygulamaları veya eylemleri'ne** tıklayın, **Uygulamaları seçin** ve **Office 365** arayın. **Office 365** ve ardından **Seç'i seçin**.  

4. **Koşullar**, **İstemci uygulamaları**, **Evet olarak yapılandır**, **Tarayıcı'yı** ve ardından **Bitti'yi** seçin.

5. **Oturum'a**, **Uygulama tarafından zorlanan kısıtlamaları kullan'a** ve ardından **Seç'e tıklayın**.

6. İlkeyi açın ve **Oluştur'u** seçin.

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="are-there-any-browsers-or-browser-scenarios-in-which-idle-session-timeout-feature-doesnt-work"></a>Boşta oturum zaman aşımı özelliğinin çalışmadığı tarayıcılar veya tarayıcı senaryoları var mı?  

Tarayıcıda üçüncü taraf tanımlama bilgileri devre dışı bırakıldığında boşta oturum zaman aşımı desteklenmez. Kullanıcılar hiçbir oturum kapatma istemi görmez. İzleme önleme ayarını Microsoft Edge için [Dengeli (Varsayılan)](/microsoft-edge/web-platform/tracking-prevention) ve diğer tarayıcılarınızda etkinleştirilmiş üçüncü taraf tanımlama bilgileri olarak tutmanızı öneririz. Microsoft 365 uygulamaları ve hizmetleri, 17 Ağustos 2021'den bu yana Internet Explorer 11'i desteklemeyi durdurdu.

### <a name="how-should-i-prepare-if-my-organization-is-already-using-existing-outlook-web-app-and-sharepoint-online-idle-timeout-policies"></a>Kuruluşum zaten mevcut Outlook web uygulamasını ve SharePoint Online boşta kalma zaman aşımı ilkelerini kullanıyorsa nasıl hazırlanmalıyım?  

Zaten mevcut Outlook web uygulamasını ve SharePoint Online boşta kalma zaman aşımı ilkelerini kullanıyorsanız boşta oturum zaman aşımı özelliğini açabilirsiniz. Boşta kalma zaman aşımı ilkesini açtığınızda, bu ilke mevcut Outlook web uygulaması ve SharePoint Online ilkelerine göre önceliklidir. Yakın gelecekte mevcut Outlook web uygulamasını ve SharePoint Online ilkelerini kullanımdan kaldırmayı planlıyoruz. Kuruluşunuzu daha iyi hazırlamak için boşta oturum zaman aşımını açmanızı öneririz.

### <a name="what-happens-if-i-am-inactive-on-an-included-microsoft-365-web-app-but-active-on-a-microsoft-web-app-or-saas-web-app-that-doesnt-have-idle-session-timeout-turned-on"></a>Dahil edilen bir Microsoft 365 web uygulamasında etkin değilsem ancak boşta oturum zaman aşımı açık olmayan bir Microsoft web uygulamasında veya SaaS web uygulamasında etkinsem ne olur?  

Aşağıdaki Microsoft 365 web uygulamaları desteklenir.

- Outlook Web App

- OneDrive İş

- SharePoint Online (SPO)

- Office.com ve diğer başlangıç sayfaları

- Web üzerinde Office (Word, Excel, PowerPoint)

- Microsoft 365 Yönetici Merkezi

Aynı hesaba sahip farklı bir web uygulaması üzerinde çalışıyorsanız, bu web uygulamasındaki etkinlik boşta oturum zaman aşımına uygulanmaz.

### <a name="i-want-to-make-changes-to-the-idle-session-timeout-policy-or-delete-it-how-can-i-do-that"></a>Boşta oturum zaman aşımı ilkesinde değişiklik yapmak veya silmek istiyorum. Bunu nasıl yapabilirim?

İlkeyi güncelleştirin:

1. Microsoft 365 yönetim merkezi **Kuruluş ayarları'nı** seçin, **Güvenlik & Gizlilik** sekmesine gidin ve **Boşta oturum zaman aşımı'nı** seçin.

2. Açılan menüden farklı bir zaman aşımı değeri seçin ve ardından **Kaydet'i seçin**.  

İlkeyi silin:

1. Microsoft 365 yönetim merkezi **Kuruluş ayarları'nı** seçin, **Güvenlik & Gizlilik** sekmesine gidin ve **Boşta oturum zaman aşımı'nı** seçin.

2. **Kullanıcıların Office web uygulamalarının oturumunu kapatması için etkinlik dışı kalma süresini ayarlamak için Aç'ın** işaretini kaldırın ve **Kaydet'i** seçin.
