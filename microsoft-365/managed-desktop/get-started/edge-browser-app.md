---
title: Microsoft Edge
description: Tarayıcının Microsoft Edge ve güncelleştirilmiş olduğunu açıklar
keywords: tarayıcı, Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: aab02ec260f0131ab32d28834152f50b84abce21
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2022
ms.locfileid: "63016658"
---
# <a name="microsoft-edge"></a>Microsoft Edge

[Microsoft Edge](https://www.microsoft.com/edge), birinci sınıf performans ve değer sağlar:

- Daha fazla gizlilik ve dış tehditlere karşı koruma.
- Uygulamalar, dosyalar, siteler ve Office sitelere daha fazla üretkenlik için hızlı Microsoft Arama.
- Cihazlar arasında platformlar arası destek ve profillerle eşitlenen sorunsuz deneyim.

> [!IMPORTANT]
> Internet Explorer 11 masaüstü uygulaması 15 Haziran 2022'de kaldırılmış olacak ve destekten çıkar (kapsamda neler olduğunu görmek için bkz. [SSS](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/internet-explorer-11-desktop-app-retirement-faq/ba-p/2366549). Bugün kullanabileceğiniz aynı IE11 uygulamaları ve siteleri, Internet Explorer Microsoft Edge içinde açabilirsiniz. [Daha fazla bilgi edinmek için buraya tıklayın](https://blogs.windows.com/windowsexperience/2021/05/19/the-future-of-internet-explorer-on-windows-10-is-in-microsoft-edge/).

## <a name="updates-to-microsoft-edge"></a>Güncelleştirmeler Microsoft Edge

Microsoft Yönetilen Masaüstü, her [sekiz haftada bir otomatik olarak](/deployedge/microsoft-edge-channels#extended-stable-channel) güncelleştirilen Microsoft Edge Genişletilmiş Kararlı kanalını dağıtıyor. Genişletilmiş Kararlı kanalda yapılan güncelleştirmeler, [müşterilere en](/deployedge/microsoft-edge-update-progressive-rollout) iyi deneyimi sağlamak Microsoft Edge ürün grubu tarafından aşamalı olarak sunulmaktadır.

[Beta Kanalı,](/deployedge/microsoft-edge-channels#beta-channel) kuruluş içinde temsili doğrulama için Test grubunda bulunan cihazlara dağıtılır. Bu kanal tam olarak destekleniyor ve yaklaşık dört haftada bir yeni özelliklerle otomatik olarak güncelleştirilir.

> [!IMPORTANT]
> Güncelleştirmelerin doğru Microsoft Edge için, güncelleştirme ilkelerini Microsoft Edge [değiştirmeyin](/deployedge/microsoft-edge-update-policies).

## <a name="settings-managed-by-microsoft-managed-desktop"></a>Ayarlar Yönetilen Masaüstü tarafından yönetilen çalışma

Microsoft Yönetilen Masaüstü, tarayıcının güvenliğini sağlamak için Microsoft Edge ilkeler kümesi oluşturdu. Varsayılan tarayıcı ayarları şunlardır:

### <a name="microsoft-edge-extensions"></a>Microsoft Edge uzantıları

Microsoft Yönetilen Masaüstü cihazlarında Microsoft Edge için güvenlik temeli, tüm Chrome uzantılarını ve kullanıcıların güvenliğini sağlamak için iki ilke ayarlar. Ortamınıza uzantıları etkinleştirmek ve dağıtmak için bkz. [Ayarlar yönetme.](#settings-you-manage)

| Ayar | Varsayılan değer | Açıklama |
| ------ | ------ | ------ |
| Uzantı yükleme engelleme listesi | Tümü | Microsoft Yönetilen Masaüstü, Chrome uzantılarının yönetilen uç noktalara yüklenmesini önlemek için bu ilkeyi ayarlar. Veri kaybına karşı koruma, gizlilik Chromium cihazların güvenliğini tehlikeye at riskler de içinde olmak üzere bu uzantı modeliyle ilişkili bilinen riskler vardır. |
| Kullanıcı düzeyi yerel mesajlaşma ana bilgisayarlarına izin verme (yönetici izinleri olmadan yüklenir) | Devre dışı | Bu ilke devre dışı bırak Microsoft Edge, yalnızca sistem düzeyinde yüklü yerel mesajlaşma ana bilgisayarlarını kullanır. Yerel mesajlaşma ana bilgisayarları, tarayıcının kullanıcının uç noktasının diğer bölümleriyle etkileşim kurmasına ve çeşitli güvenlik kaygıları oluşturmasına olanak sağlayan Chrome uzantılarının bir parçasıdır. |

### <a name="secure-sockets-layer-tlsssl"></a>Güvenli Yuva Katmanı (TLS/SSL)

| Ayar | Varsayılan değer | Açıklama
| ------ | ------ | ------ |
| Minimum TLS sürümü | Minimum TLS 1.2 desteklenen | Daha az güvenli TLS 1.1'i kullanmak için istekte bulunabilirsiniz. |
| Kullanıcıların SSL uyarı sayfasından devamlerine izin ver | Devre dışı | Kullanıcıların TSL hataları olan siteleri ziyaret etmelerine olanak sağlarken bu ayarı etkinleştirmenizi önerilmez. |

### <a name="microsoft-defender-smartscreen"></a>Microsoft Defender SmartScreen

| Ayar | Varsayılan değer | Açıklama
| ------ | ------ | ------ |
| SmartScreen Windows Defender yapılandırma | Etkin | Kullanıcıların korunmasına yardımcı olmak için varsayılan olarak etkindir. |
| Windows Defender SmartScreen istemleri | Etkin | Kullanıcıların uyarıları yoksaymalarına ve kötü amaçlı olabilecek sitelere devam etmelerine olanak sağlayan bu ayarı devre dışı bırakmamanız önerilir. |
| İndirmeler hakkında SmartScreen Windows Defender uyarılarını atlayarak engelleme | Etkin | Kullanıcıların uyarıları yoksaymalarına ve doğrulanmamış indirmeleri tamamlamalarına olanak verecek şekilde bu ayarı devre dışı bırakmamanız önerilir. |

### <a name="adobe-flash"></a>Adobe Flash

| Ayar | Varsayılan değer | Açıklama
| ------ | ------ | ------ |
| Varsayılan Adobe Flash ayarı | Devre dışı | İlişkili güvenlik riskleri nedeniyle Flash kullanılması önerilmez. <br><br> Flash'a bağlı olan süreçleriniz devam ediyorsa, flash özelliğine ihtiyaç olan siteler için Flash'ı etkinleştirmek için **[PluginsAllowedForUrls](/deployedge/microsoft-edge-policies#pluginsallowedforurls)** ilkesi ayarlayın. Flash'ın kullanımına izin verilen bir site listesini koruyamıyorsanız, değeri Oynatmak için Tıklayın olarak değiştirmek üzere bir değişiklik isteği dosyası çalıştırın; bu sayede kullanıcılar Flash'ı ne zaman çalıştıracaklarını seçebilirler. |

### <a name="password-manager"></a>Parola yöneticisi

| Ayar | Varsayılan değer | Açıklama
| ------ | ------ | ------ |
| Parola yöneticisine parola kaydetmeyi etkinleştirme | Devre dışı | Parola yöneticisi varsayılan olarak devre dışıdır. Bu özelliğin etkinleştirilmesi sizin için bir destek isteğinde bulunarak hizmet mühendislerimiz bu ayarı ortamınıza etkinleştirebilirsiniz. |

### <a name="internet-explorer-mode-in-microsoft-edge"></a>Microsoft Edge'te Internet Explorer Modu

IE modu Microsoft Edge bir tarayıcıda, kuruma gereken tüm sitelerin kullanımını kolaylaştırır. Site işleme altyapısıyla Chromium tümleştirilmiş sistem altyapısını Chromium kullanır. Microsoft Edge, IE işlevselliğine bağımlı olmayan veya bağımlılıkları olmayan siteler için Internet Explorer 11'den (IE11) gelen Trident MSHTML altyapısını kullanır. [Daha fazla bilgi edinin](/DeployEdge/edge-ie-mode)

Microsoft Yönetilen Masaüstü cihazlarınız için varsayılan olarak Internet Explorer modunu sağlar.

| Ayar | Varsayılan değer | Açıklama
| ------ | ------ | ------ |
| Internet Explorer modu tümleştirmesi | Internet Explorer modu | Varsayılan olarak, cihazlar Internet Explorer modunu kullanmaya ayarlanmıştır, ancak siteleri bunun yerine tek başına bir Internet Explorer 11 penceresinde açılacak şekilde de değiştirebilirsiniz. Bu davranışı değiştirmek için bir destek isteği dosyalanın. |
| Site Modu Enterprise listesine site ekleme | Açıklamaya bakın | Sitelerin Internet Explorer modunda açılması için, bunları Site listesinde [Enterprise gerekir](/DeployEdge/edge-ie-mode-sitelist). Site listesinin bakımını ve Enterprise sorumluluğundadır. Ayrıntılar için bkz[. En Son Site Listesini Enterprise kullanarak yapılandırma](/DeployEdge/edge-ie-mode-policies#configure-using-the-configure-the-enterprise-mode-site-list-policy). |

### <a name="other-settings"></a>Diğer ayarlar

| Ayar | Varsayılan değer | Açıklama
| ------ | ------ | ------ |
| Her site için site yalıtıldı ayarını etkinleştirme | Etkin | Bu ilke etkinleştirildiğinde, kullanıcılar her sitenin kendi iş yerinde çalıştırıldı varsayılan davranışını devre dışı bırakmaz. |
| Desteklenen kimlik doğrulama düzenleri | NTLM, Negotiate | Microsoft Yönetilen Masaüstü Temel veya Özet Kimlik Doğrulaması düzenlerini desteklemez. |
| İlk çalıştırmada başka bir tarayıcının verilerini ve ayarlarını otomatik olarak içeri aktarma | Desteklenen tüm veri türlerini ve ayarları varsayılan tarayıcıdan otomatik olarak içeri aktar. | Bu ilke uygulandığında, İlk Çalıştırma Deneyimi kullanıcı etkileşimini en aza indirecek olan içeri aktarma bölümünü atlar. Bu ayardan bağımsız olarak Microsoft Edge eski sürümlerinin tarayıcı verileri ilk çalıştırmada her zaman sessiz geçirilir. |

## <a name="settings-you-manage"></a>Ayarlar yönetme

Daha önce açık Microsoft Edge Yönetim Şablonları profilini kullanarak açıklandırılan tüm Yönetim Microsoft Intune. Ayrıntılar için bkz. [Microsoft Edge ilke ayarlarını yapılandırma Microsoft Intune](/deployedge/configure-edge-with-intune). Şu anda Intune'daki Microsoft Edge Yönetim Şablonları'nın içinde yer kullanmayan bir ilkeyi değerlendirmek için, Intune'daki diğer Windows 10 için özel ayarları kullanabilirsiniz.

| Ayar | Açıklama
| ------ | ------ |
| Belirli Chrome uzantılarını etkinleştirme | Yönetim Şablonu, belirli Chrome uzantılarının daha kolay dağıtılacağı bir Microsoft Intune. Bu uzantıyı Bilgisayar Yapılandırması **veya > Microsoft Edge > Uzantılar ve > İzin Ver seçeneklerinde bulabilirsiniz**. |
| Uzantıları sessiz yükleme | Ayrıca, Yönetim Şablonu'Microsoft Edge kullanıcıya uyarı vermeden uzantıları yüklemek üzere ayarlamayı da kullanabilirsiniz. Bu uzantıyı Bilgisayar **Yapılandırması veya > Microsoft Edge > Uzantılar > hangi uzantıların sessiz yük olduğunu Denetleme altında bulabilirsiniz**. |
| Microsoft Edge ilkelerini güncelleştirme | Güncelleştirmelerin doğru Microsoft Edge için, güncelleştirme ilkelerini Microsoft Edge [değiştirmeyin](/deployedge/microsoft-edge-update-policies). |
| Diğer ortak kurumsal ilkeler | Microsoft Edge çok sayıda başka ilke sunar. Aşağıda daha yaygın olanlardan bazıları ve birkaçı ve ardından: <ul> <li> [Site Listesi'Enterprise IE Modunda Siteleri yapılandırma](/deployedge/edge-ie-mode-sitelist)</li><li> [Başlangıç, giriş sayfası ve yeni sekme sayfası ayarlarını yapılandırma](/deployedge/microsoft-edge-policies#startup-home-page-and-new-tab-page)</li> <li> [Sörf oyunu ayarını yapılandırma](/deployedge/microsoft-edge-policies#allowsurfgame)</li> <li> [Proxy sunucu ayarlarını yapılandırma](/deployedge/microsoft-edge-policies#proxy-server)</li></ul>
