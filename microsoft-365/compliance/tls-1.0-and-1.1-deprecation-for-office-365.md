---
title: Kullanıcı için TLS 1.0 ve 1.1'i devre dışı Microsoft 365
description: TTM'nin TLS 1.0 ve 1.1'i kullanımdan Microsoft 365.
author: workshay
manager: laurawi
ms.localizationpriority: medium
search.appverid:
- MET150
audience: ITPro
ms.service: O365-seccomp
ms.topic: article
ms.author: fasqiu
ms.reviewer: krowley
appliesto:
- Microsoft 365 Apps for enterprise
- Office 365 Business
- Office 365 Personal
- Office Online Server
- Office Web Apps
ms.openlocfilehash: 3084232f267a1180425d2daa3fcd2ba2fbcbd063
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973729"
---
# <a name="disabling-tls-10-and-11-for-microsoft-365"></a>Kullanıcı için TLS 1.0 ve 1.1'i devre dışı Microsoft 365

> [!IMPORTANT]
> COVID-19 nedeniyle ticari müşteriler için TLS 1.0 ve 1.1'in devre dışı bırakıldığını geçici olarak durdurduk. Tedarik zincirleri ayarlandı ve bazı ülkeler yeniden açıldıktan sonra TLS 1.2 zorlamasını 15 Ekim 2020'de yeniden başlattık. Aşağıdaki haftalarda ve aylarda, bu kodda yer a kalacaktır.

31 Ekim 2018'den bu yana, Aktarım Katmanı Güvenliği (TLS) 1.0 ve 1.1 protokolleri Microsoft 365 kullanım dışıdır. Son kullanıcılar için etkisi çok düşüktür. Bu değişiklik, Aralık 2017'de yapılan ilk genel duyuruyla birlikte iki yıldır genele açık hale getirildi. Bu makale yalnızca Office 365 hizmetiyle ilgili olarak Office 365 yerel istemcisini kapsıyor olması amaçlanmıştır, ancak Office ve Office Online Server/Office web uygulamalarıyla ilgili şirket içi TLS sorunlarına da uygulanabilir.

Daha SharePoint ve OneDrive için, TLS 1.2'yi destekleyecek şekilde .NET'i güncelleştirmeniz ve yapılandırmaniz gerekir. Bilgi için bkz [. İstemcilerde TLS 1.2'yi etkinleştirme](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

## <a name="office-365-and-tls-overview"></a>Office 365 TLS'ye genel bakış

En Office istemcisi, TLS protokolleri üzerinden trafik göndermek Windows web hizmetine (WINHTTP) dayandır. Yerel Office web hizmeti TLS 1.2'yi kullanıyorsa, İSTEMCI İstemcisi TLS 1.2'yi kullanabilir. Tüm Office, TLS ve SSL protokolleri işletim sisteminin bir parçası olduğu ve istemciye özel değil, TLS protokollerini Office kullanır.

### <a name="on-windows-8-and-later-versions"></a>Windows 8 sonraki sürümlerde

Varsayılan olarak, HIÇBIR ağ cihazı TLS 1.2 trafiğini reddedecek şekilde yapılandırılmamışsa TLS 1.2 ve 1.1 protokolleri kullanılabilir.

### <a name="on-windows-7"></a>Windows 7'de

[TLS](https://support.microsoft.com/help/3140245) 1.1 ve 1.2 protokolleri KB veya 3140245 kullanılamaz. Güncelleştirme bu sorunu gidermekte ve aşağıdaki kayıt defteri alt anahtarını ekler:

```console
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp
```

> [!NOTE]
> Windows 7 kullanıcı bu güncelleştirmeye sahip değilken 31 Ekim 2018'den etkilenir. [KB 3140245](https://support.microsoft.com/help/3140245) , TLS protokollerini etkinleştirmek için WINHTTP ayarlarını değiştirme hakkında ayrıntılar içerir.

#### <a name="more-information"></a>Daha fazla bilgi

KB makalesinde açık **olan DefaultSecureProtocols** kayıt defteri anahtarının değeri, hangi ağ protokollerinin kullanıl olacağını belirler:

|DefaultSecureProtocols Değeri|Etkin protokol|
|-|-|
|0x00000008|SSL 2.0'i varsayılan olarak etkinleştirme|
|0x00000020|SSL 3.0'i varsayılan olarak etkinleştirme|
|0x00000080|TLS 1.0'i varsayılan olarak etkinleştirme|
|0x00000200|TLS 1.1'i varsayılan olarak etkinleştirme|
|0x00000800|TLS 1.2'yi varsayılan olarak etkinleştirme|

## <a name="office-clients-and-tls-registry-keys"></a>Office ve TLS kayıt defteri anahtarlarını yükleme

KB Veri [Bankası'4057306 TlS 1.2'nin](https://support.microsoft.com/help/4057306) zorunlu kullanımına hazırlanma makalesinde Office 365. Bu, IT yöneticileri için genel bir makaledir ve TLS 1.2 değişikliğiyle ilgili resmi belgelerdir.

Aşağıdaki tabloda, 31 Ekim 2018 Office 365 sonra istemcilerde uygun kayıt defteri anahtarı değerleri yer alır.

|31 Ekim 2018 Office 365 sonrası hizmet için etkin protokoller|Onaltılı değer|
|-|-|
|TLS 1.0 + 1.1 + 1.2|0x00000A80|
|TLS 1.1 + 1.2|0x00000A00|
|TLS 1.0 + 1.2|0x00000880|
|TLS 1.2|0x00000800|

> [!IMPORTANT]
> **DefaultSecureProtocols** anahtarı kullanılarak da ayarlanan SSL 2.0 ve 3.0 protokollerini kullanmayın. SSL 2.0 ve 3.0, zaman dışından ve güvenli olmayan protokol olarak kabul edilir. En iyi uygulama, SSL 2.0 ve SSL 3.0 kullanımını sona erer; ancak bunu yapma kararı nihai olarak ürün ihtiyaçlarını en iyi neleri karşı aldığına bağlıdır. SSL 3.0 güvenlik açıkları hakkında daha fazla bilgi için [KB güvenlik açıkları 3009008](https://support.microsoft.com/help/3009008).

Aynı başvuru kayıt defteri anahtarı Windows ayarlamak için Programcı modunda varsayılan Hesap Makinesi'ni kullanabilirsiniz. Daha fazla bilgi için bkz. [3140245'de WinHTTP'da varsayılan güvenlik protokolleri olarak TLS 1.1 ve TLS 1.2'yi etkinleştirmek için KB Windows](https://support.microsoft.com/help/3140245).

Windows 7 güncelleştirmesi ([KB 3140245](https://support.microsoft.com/help/3140245)) yüklü olup değilse, DefaultSecureProtocols kayıt defteri alt anahtarı mevcut değildir ve el ile veya bir grup ilkesi nesnesi (GPO) aracılığıyla ekleniyor olmalıdır. Başka bir ifadeyle, etkinleştirilen veya kısıtlanan güvenlik protokollerini özelleştirmeniz gerekmiyorsa, bu anahtar gerekli değildir. Yalnızca 7 SP1 (KB Windows) güncelleştirmesi [3140245](https://support.microsoft.com/help/3140245) gerekir.

## <a name="update-and-configure-the-net-framework-to-support-tls-12"></a>TLS 1.2 .NET Framework güncelleştirme ve yapılandırma

TLS 1.2'yi kullanmak için, MICROSOFT 365 API'leri TLS 1.0 veya TLS 1.1 üzerinden çağıran uygulamaları güncelleştirmeniz gerekir. .NET 4.5 varsayılan olarak TLS 1.1'i kullanır. .NET yapılandırmanızı güncelleştirmek için bkz. [İstemcilerde Aktarım Katmanı Güvenliği (TLS) 1.2'yi etkinleştirme](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

## <a name="more-information"></a>Daha fazla bilgi

Daha fazla bilgi için bkz. Çalışma Sayfalarında [TLS 1.2'nin zorunlu kullanımına hazırlanma Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

## <a name="references"></a>Başvurular

Aşağıdaki kaynaklar istemcilerinizi TLS 1.2 veya daha sonraki bir sürümünü kullanırkenn ve TLS 1.0 ve 1.1'i devre dışı bırakmak için yol gösterici bilgiler sağlar:

- Office 365'e bağlanan Windows 7 istemcileri için TLS 1.2'nin Windows'da WinHTTP'deki varsayılan güvenli protokol olduğundan emin olun. Daha fazla bilgi için [bkz. KB 3140245 - Win'te varsayılan güvenlik protokolleri olarak TLS 1.1 ve TLS 1.2'yi etkinleştirmek için Windows](https://support.microsoft.com/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in).
- TLS 1.0 ve 1.1 bağımlılıklarını kaldırarak zayıf TLS kullanımına karşı, [bkz. Microsoft'ta TLS 1.2 desteği](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/20/tls-1-2-support-at-microsoft/).
- [Yeni IIS işlevi,](https://cloudblogs.microsoft.com/microsoftsecure/2017/09/07/new-iis-functionality-to-help-identify-weak-tls-usage/) [Windows Server 2012 R2](https://support.microsoft.com/help/4025335/windows-8-1-windows-server-2012-r2-update-kb4025335) ve [Windows Server 2016](https://support.microsoft.com/help/4025334/windows-10-update-kb4025334)'da zayıf güvenlik protokolleri kullanarak hizmete bağlanan istemcileri bulmayı kolaylaştırır.
- [TLS 1.0 sorununu çözme hakkında daha fazla bilgi edinebilirsiniz](https://www.microsoft.com/download/details.aspx?id=55266).
- Güvenlik yaklaşımımız hakkında genel bilgi için [Office 365 Güven Merkezi](https://www.microsoft.com/trustcenter/cloudservices/office365)'ne gidin.
- [TLS 1.0/1.1'i Kullanımdan Kaldırmaya Hazırlık - Office 365 Skype Kurumsal](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/ba-p/222247)
- [Exchange Server TLS kılavuzu, bölüm 1: TLS 1.2'ye Hazırlanıyor](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-1-getting-ready-for-tls-1-2/ba-p/607649)
- [Exchange Server TLS kılavuzu, Bölüm 2: TLS 1.2'yi Etkinleştirme ve Kullanmayan İstemcileri Belirleme](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-2-enabling-tls-1-2-and/ba-p/607761)
- [Exchange Server TLS kılavuzu, Bölüm 3: TLS 1.0/1.1'i kapatma](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-3-turning-off-tls-1-0-1-1/ba-p/607898)
- [Office Online Server'da TLS 1.1 ve TLS 1.2 desteğini etkinleştirme](/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server)

