---
title: Adım 2. Şirket içi uygulama ve hizmetlere uzaktan erişim sağlama
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-scenario
ms.custom: ''
description: Uzak çalışanlarının şirket içi kaynaklara erişene kadar, bu kaynaklara erişimi en iyi duruma getirerek bulut Microsoft 365 emin olur.
ms.openlocfilehash: 6baaa8c4e3935676278ff411d0282b82143056fc
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328659"
---
# <a name="step-2-provide-remote-access-to-on-premises-apps-and-services"></a>Adım 2. Şirket içi uygulama ve hizmetlere uzaktan erişim sağlama

Kuruluş bir uzaktan erişim VPN çözümü kullanıyorsa (normalde ağ bağlantınız kenarında VPN sunucuları ve kullanıcılarınızın cihazlarında yüklü VPN istemcileri varsa, kullanıcılarınız şirket içi uygulamalara ve sunuculara erişmek için uzaktan erişim VPN bağlantılarını kullanabilirler. Ancak, trafiği bulut tabanlı Microsoft 365 için en iyi duruma getirmen gerekir.

Kullanıcılarınız VPN çözümü kullanmazsa, tüm uygulamalarınızı web tabanlı olup olmadığını bağlı olarak erişim sağlamak için Azure Active Directory (Azure AD) Uygulama Ara Sunucusu ve Azure Noktadan Siteye (P2S) VPN kullanabilirsiniz.

Uzaktan erişim için birincil yapılandırmalar şöyledir:

- Zaten bir uzaktan erişim VPN çözümü kullanıyorsanız.
- Uzaktan erişim VPN çözümü kullana istemiyor ve uzaktan çalışanlarının kendi kişisel bilgisayarlarını kullanmalarını istiyor olun.
- Uzaktan erişim VPN çözümü kullanmaz, karma kimliğiniz vardır ve yalnızca şirket içi web tabanlı uygulamalara uzaktan erişime ihtiyacınız vardır.
- Uzaktan erişim VPN çözümü kullanamayabilirsiniz ve bazıları web tabanlı olmayan şirket içi uygulamalara erişmeniz gerekir.

Bu makalede ele alan uzaktan erişim yapılandırma seçenekleri için bu akış çizelgesine bakın.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-flowchart.png" alt-text="Uzaktan erişim yapılandırması akış çizelgesi." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-flowchart.png":::

Uzaktan erişim bağlantılarla, kullanıcılarınızı [bir şirket](https://support.microsoft.com/help/4028379/windows-10-how-to-use-remote-desktop) içi bilgisayara bağlamak için Uzak Masaüstü'nüz de kullanabilirsiniz. Örneğin, uzaktan çalışan kendi iş yerlerinde çalışanlardan biri kendi bilgisayarına Windows iOS veya Android cihazından Uzak Masaüstü'ne bağlanabilir. Uzaktan bağlandıktan sonra, sanki bu bağlantının önünde duruyor gibi kullanabilirler.

## <a name="optimize-performance-for-remote-access-vpn-clients-to-microsoft-365-cloud-services"></a>Uzaktan erişim VPN istemcileri ile bulut hizmetlerini Microsoft 365 performansı iyileştirme

Uzaktan çalışanlarınız kuruluş ağınıza uzaktan erişim elde etmek için geleneksel bir VPN istemcisi kullanıyorsa VPN istemcisinin bölünmüş şifreleme desteğine sahip olduğunu doğrulayın.

Bölünmüş bölme olmadan, uzaktan iş trafiğinizin hepsi VPN bağlantısı üzerinden gönderilir, bu trafik kuruluşun uç cihazlarına ilet olmalı, işlenmeli ve İnternet'e gönderilir.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-before-tunneling.png" alt-text="VPN istemcilerinden gelen ağ trafiğine hiçbir şey olunmaz." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-before-tunneling.png":::

Microsoft 365, trafiğin, VPN istemcisinin fiziksel konumunun çok uzakta olan Microsoft ağ giriş noktasına yönlendirilen dolaylı bir yol olması gerekir. Bu dolaylı yol ağ trafiğine gecikme ekler ve genel performansı düşürer.

Bölünmüş bölmeyle, VPN istemcinizi kuruluş ağına VPN bağlantısı üzerinden gönderilen trafiğin belirli türlerini dışarıda bırakacak şekilde yapılandırabilirsiniz.

Bulut kaynaklarına erişimi Microsoft 365 için bölünmüş VPN istemcilerinizi yapılandırarak trafiği VPN bağlantısı üzerinden en iyi duruma Microsoft 365 uç noktalarını iyileştirmek için  kullanın. Daha fazla bilgi için bkz. [Office 365 kategorilerini yapılandırma](../enterprise/microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories). Kategori [uç noktalarını](../enterprise/urls-and-ip-address-ranges.md) en iyi duruma getirme listesine bakın.

Sonuçta ortaya çıkan trafik akışı yer alsa da, bulut uygulamalarına Microsoft 365 trafiğin çoğu VPN bağlantısını atlar.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-after-tunneling.png" alt-text="VPN istemcilerinden gelen ağ trafiği ve tarak." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-after-tunneling.png":::

Bu VPN istemcisinin doğrudan İnternet üzerinden ve Microsoft ağına en Microsoft 365 giriş noktasına önemli bir bulut hizmeti trafiği göndermesine ve ağına sahip olmasına olanak sağlar.

Daha fazla bilgi ve rehberlik için bkz. [VPN bölünmüş Office 365 kullanan uzak kullanıcılar için en iyi duruma getirme](../enterprise/microsoft-365-vpn-split-tunnel.md).

## <a name="deploy-remote-access-when-all-your-apps-are-web-apps-and-you-have-hybrid-identity"></a>Tüm uygulamalarınız web uygulamaları olduğunda ve karma kimliğiniz olduğunda uzaktan erişimi dağıtma

Uzaktan çalışanlarınız geleneksel VPN istemcisini kullanıyorsa ve şirket içi kullanıcı hesaplarınız ve gruplarınız Azure AD ile eşitlenmişse, şirket içi sunucularda barındırılan web tabanlı uygulamalara güvenli uzaktan erişim sağlamak için Azure AD Uygulama Ara Sunucusu'u kullanabilirsiniz. Web tabanlı uygulamalar SharePoint Server sitelerini, Outlook Web Access sunucularını veya diğer tüm web tabanlı iş uygulamalarını içerir.

Azure AD Uygulama Ara Sunucusu'nın bileşenleri aşağıdaki gibidir.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-application-proxy.png" alt-text="Azure AD Uygulama Ara Sunucusunun bileşenleri." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-application-proxy.png":::

Daha fazla bilgi için bkz. [Azure AD Uygulama Ara Sunucusu'ya genel bakış](/azure/active-directory/manage-apps/application-proxy).

> [!NOTE]
> Azure AD Uygulama Ara Sunucusu, bir Microsoft 365 dahil değildir. Kullanım için ayrı bir Azure aboneliğiyle ödemeniz gerekir.

## <a name="deploy-remote-access-when-not-all-your-apps-are-web-apps"></a>Tüm uygulamalarınız web uygulaması değilken uzaktan erişimi dağıtma

Uzaktan çalışanlarınız geleneksel VPN istemcisini kullanıyorsa ve web tabanlı olmayan uygulamalarınız varsa, Azure Noktadan Siteye (P2S) VPN kullanabilirsiniz.

P2S VPN bağlantısı, bir uzak çalışanın cihazından Azure sanal ağı aracılığıyla kuruluş ağınıza güvenli bir bağlantı oluşturur.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-p2s-vpn.png" alt-text="Azure P2S VPN bileşenleri." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-p2s-vpn.png":::

Daha fazla bilgi için [P2S VPN'ye genel bakış bilgilerine bakın](/azure/vpn-gateway/point-to-site-about).

> [!NOTE]
> Azure P2S VPN, bir Microsoft 365 dahil değildir. Kullanım için ayrı bir Azure aboneliğiyle ödemeniz gerekir.

## <a name="deploy-windows-365-to-provide-remote-access-for-remote-workers-using-personal-devices"></a>Kişisel Windows kullanan uzaktan çalışanlar için uzaktan erişim sağlamak için Office 365'i dağıtma

Yalnızca kişisel ve yönetimsiz cihazlarını kullanan uzaktan çalışanları desteklemek için, Windows 365'i kullanarak kullanıcılarınıza evden sanal masaüstleri oluşturun ve tahsis edin. Şirket içi ağ bağlantısıyla (OPNC) Windows 365 Bulut PC'ler, aynı kuruluş ağınıza bağlı bilgisayarlarda olduğu gibi davranır.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-windows-365.png" alt-text="Windows 365 bileşenleri." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-windows-365.png":::

Daha fazla bilgi için bkz. [Windows 365](/windows-365/overview).

> [!NOTE]
> Windows 365, yeni bir abonelik Microsoft 365 değildir. Kullanım için ayrı bir abonelikle ödemeniz gerekir.

## <a name="protect-your-remote-desktop-services-connections-with-the-remote-desktop-services-gateway"></a>Uzak Masaüstü Hizmetleri Ağ Geçidi ile Uzak Masaüstü Hizmetleri bağlantılarınızı koruma

Çalışanların şirket içi ağınızdaki Windows tabanlı bilgisayarlara bağlanmalarına izin vermek için Uzak Masaüstü Hizmetleri'ni (RDS) kullanıyorsanız, kenar ağınızdaki Microsoft Uzak Masaüstü Hizmetleri ağ geçidini kullanabilirsiniz. Ağ geçidi, trafiği şifrelemek için Aktarım Katmanı Güvenliği 'ni (TLS) kullanır ve RDS'yi barındıran şirket içi bilgisayarın doğrudan İnternet'e maruz kalmasını sağlar.

:::image type="content" source="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-remote-desktop.png" alt-text="Uzak Masaüstü Hizmetleri Ağ Geçidi ile Uzak Masaüstü Hizmetleri bağlantıları." lightbox="../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-remote-desktop.png":::

Daha [fazla bilgi için](https://www.microsoft.com/security/blog/2020/04/16/security-guidance-remote-desktop-adoption/) bu makaleye bakın.

## <a name="admin-technical-resources-for-remote-access"></a>Uzaktan erişim için yönetici teknik kaynakları

- [Uzak personel ve Office 365 için trafiği hızlı bir & altyapı üzerindeki yükü azaltma](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571)
- [VPN bölünmüş Office 365 kullanarak uzak kullanıcılar için ayrım bağlantısını en iyi duruma getirme](../enterprise/microsoft-365-vpn-split-tunnel.md)

## <a name="results-of-step-2"></a>Adım 2'nin sonuçları

Uzak çalışanlarınız için uzaktan erişim çözümünün dağıtımı sonrasında:

| Uzaktan erişim yapılandırması | Sonuçlar |
|:-------|:-----|
| Bir uzaktan erişim VPN çözümü karşınıza geldi | Uzaktan erişim VPN istemcinizi bölünmüş tünel için ve Microsoft 365 uç noktalarının En İyi Duruma Microsoft 365 yapılandırdınız. |
| Uzaktan erişim VPN çözümü yoktur ve yalnızca şirket içi web tabanlı uygulamalara uzaktan erişime ihtiyacınız vardır | Azure Uygulama Ara Sunucu'larını yapılandırdınız. |
| Uzaktan erişim VPN çözümü yoktur ve bazıları web tabanlı olmayan şirket içi uygulamalara erişmeniz gerekir | Azure P2S VPN'yi yapılandırdınız. |
| Uzaktan çalışanlar evde kendi kişisel cihazlarını kullanıyor | Windows 365'i yapılandırmış Windows. |
| Uzak çalışanlar şirket içi sistemlere RDS bağlantıları kullanıyor | Uç ağ geçidinde bir Uzak Masaüstü Hizmetleri ağ geçidi dağıttınız. |
|||

## <a name="next-step"></a>Sonraki adım

[![3. Adım: Güvenlik Microsoft 365 uyumluluk hizmetlerini dağıtın.](../media/empower-people-to-work-remotely/remote-workers-step-grid-3.png)](empower-people-to-work-remotely-security-compliance.md)

Uygulamalarınızı[, verilerinizi ve](empower-people-to-work-remotely-security-compliance.md) cihazlarınızı korumak Microsoft 365 uyumluluk hizmetlerini dağıtmak için 3. Adım ile devam edin.
