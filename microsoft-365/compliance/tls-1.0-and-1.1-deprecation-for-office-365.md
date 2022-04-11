---
title: Microsoft 365 için TLS 1.0 ve 1.1'i devre dışı bırakma
description: Microsoft 365 için TLS 1.0 ve 1.1'in kullanımdan kaldırılması ve devre dışı bırakılması açıklanır.
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
ms.openlocfilehash: 519b2c025236be49f2f1c96e098c841f789c079b
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759677"
---
# <a name="disabling-tls-10-and-11-for-microsoft-365"></a>Microsoft 365 için TLS 1.0 ve 1.1'i devre dışı bırakma

> [!IMPORTANT]
> COVID-19 nedeniyle ticari müşteriler için TLS 1.0 ve 1.1'in devre dışı bırakılması geçici olarak durduruldu. Tedarik zincirleri ayarlandı ve bazı ülkeler yeniden açıldıktan sonra 15 Ekim 2020'de TLS 1.2 uygulama dağıtımını yeniden başlattık. Dağıtım sonraki haftalar ve aylar içinde devam edecektir.

31 Ekim 2018 itibarıyla Aktarım Katmanı Güvenliği (TLS) 1.0 ve 1.1 protokolleri Microsoft 365 hizmeti için kullanım dışı bırakılmıştır. Son kullanıcıların etkisi çok azdır. Bu değişiklik, aralık 2017'de yapılan ilk genel duyuruyla birlikte iki yıldan uzun süredir genel kullanıma açıklanmıştır. Bu makale yalnızca Office 365 hizmetiyle ilgili olarak Office 365 yerel istemciyi kapsamaya yöneliktir, ancak Office ve Office Online Server/Office Web Apps ile ilgili şirket içi TLS sorunlarına da uygulanabilir.

SharePoint ve OneDrive için .NET'i TLS 1.2'yi destekleyecek şekilde güncelleştirmeniz ve yapılandırmanız gerekir. Bilgi için bkz. [İstemcilerde TLS 1.2'yi etkinleştirme](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

## <a name="office-365-and-tls-overview"></a>Office 365 ve TLS'ye genel bakış

Office istemcisi, TLS protokolleri üzerinden trafik gönderip almak için Windows web hizmetine (WINHTTP) dayanır. Yerel bilgisayarın web hizmeti TLS 1.2 kullanabiliyorsa, Office istemcisi TLS 1.2 kullanabilir. TLS ve SSL protokolleri işletim sisteminin bir parçası olduğundan ve Office istemcisine özgü olmadığından tüm Office istemcileri TLS protokollerini kullanabilir.

### <a name="on-windows-8-and-later-versions"></a>Windows 8 ve sonraki sürümlerde

Varsayılan olarak TLS 1.2 ve 1.1 protokolleri, TLS 1.2 trafiğini reddedecek şekilde yapılandırılmış ağ cihazları yoksa kullanılabilir.

### <a name="on-windows-7"></a>Windows 7 tarihinde

[KB 3140245](https://support.microsoft.com/help/3140245) güncelleştirmesi olmadan TLS 1.1 ve 1.2 protokolleri kullanılamaz. Güncelleştirme bu sorunu giderir ve aşağıdaki kayıt defteri alt anahtarını ekler:

```console
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp
```

> [!NOTE]
> Windows 31 Ekim 2018 itibarıyla bu güncelleştirmeye sahip olmayan 7 kullanıcı etkilenir. [KB 3140245](https://support.microsoft.com/help/3140245) , TLS protokollerini etkinleştirmek için WINHTTP ayarlarını değiştirme hakkında ayrıntılar içerir.

#### <a name="more-information"></a>Daha fazla bilgi

KB makalesinde açıklanan **DefaultSecureProtocols** kayıt defteri anahtarının değeri, hangi ağ protokollerinin kullanılabileceğini belirler:

|DefaultSecureProtocols Değeri|Protokol etkinleştirildi|
|---|---|
|0x00000008|SSL 2.0'ın varsayılan olarak etkinleştirilmesi|
|0x00000020|SSL 3.0'ın varsayılan olarak etkinleştirilmesi|
|0x00000080|TLS 1.0'ın varsayılan olarak etkinleştirilmesi|
|0x00000200|TLS 1.1'i varsayılan olarak etkinleştirme|
|0x00000800|TLS 1.2'yi varsayılan olarak etkinleştirme|

## <a name="office-clients-and-tls-registry-keys"></a>İstemcileri ve TLS kayıt defteri anahtarlarını Office

[Office 365'da TLS 1.2'nin zorunlu kullanımına hazırlanma 4057306 KB'ye](https://support.microsoft.com/help/4057306) başvurabilirsiniz. Bu, BT yöneticileri için genel bir makaledir ve TLS 1.2 değişikliğiyle ilgili resmi belgelerdir.

Aşağıdaki tabloda, 31 Ekim 2018'in ardından Office 365 istemcilerinde uygun kayıt defteri anahtarı değerleri gösterilmektedir.

|31 Ekim 2018'de Office 365 hizmeti için etkin protokoller|Onaltılık değer|
|---|---|
|TLS 1.0 + 1.1 + 1.2|0x00000A80|
|TLS 1.1 + 1.2|0x00000A00|
|TLS 1.0 + 1.2|0x00000880|
|TLS 1.2|0x00000800|

> [!IMPORTANT]
> **DefaultSecureProtocols** anahtarı kullanılarak da ayarlanabilen SSL 2.0 ve 3.0 protokollerini kullanmayın. SSL 2.0 ve 3.0 eski ve güvenli olmayan protokoller olarak kabul edilir. En iyi yöntem SSL 2.0 ve SSL 3.0 kullanımını sonlandırmaktır, ancak bunu yapma kararı nihai olarak ürün gereksinimlerinizi en iyi karşılayan şeye bağlıdır. SSL 3.0 güvenlik açıkları hakkında daha fazla bilgi için [bkz. KB 3009008](https://support.microsoft.com/help/3009008).

Programcı modunda varsayılan Windows Hesaplayıcısı'nı kullanarak aynı başvuru kayıt defteri anahtarı değerlerini ayarlayabilirsiniz. Daha fazla bilgi için bkz. [kb 3140245 güncelleştirme tls 1.1 ve TLS 1.2 etkinleştirmek için varsayılan güvenli protokoller winhttp Windows](https://support.microsoft.com/help/3140245).

Windows 7 güncelleştirmesinin ([KB 3140245](https://support.microsoft.com/help/3140245)) yüklü olup olmamasına bakılmaksızın, DefaultSecureProtocols kayıt defteri alt anahtarı mevcut değildir ve el ile veya grup ilkesi nesnesi (GPO) aracılığıyla eklenmelidir. Başka bir ifadeyle, hangi güvenli protokollerin etkinleştirildiğini veya kısıtlandığını özelleştirmeniz gerekmediği sürece bu anahtar gerekli değildir. Yalnızca Windows 7 SP1 ([KB 3140245](https://support.microsoft.com/help/3140245)) güncelleştirmesine ihtiyacınız vardır.

## <a name="update-and-configure-the-net-framework-to-support-tls-12"></a>.NET Framework TLS 1.2'yi destekleyecek şekilde güncelleştirme ve yapılandırma

TLS 1.2 kullanmak için TLS 1.0 veya TLS 1.1 üzerinden Microsoft 365 API'lerini çağıran uygulamaları güncelleştirmeniz gerekir. .NET 4.5 varsayılan olarak TLS 1.1'dir. .NET yapılandırmanızı güncelleştirmek için bkz [. İstemcilerde Aktarım Katmanı Güvenliği (TLS) 1.2'yi etkinleştirme](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

## <a name="more-information"></a>Daha fazla bilgi

Daha fazla bilgi için bkz. [Office 365'de TLS 1.2'nin zorunlu kullanımına hazırlanma](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

## <a name="references"></a>Başvurular

Aşağıdaki kaynaklar, istemcilerinizin TLS 1.2 veya sonraki bir sürümü kullandığından emin olmak ve TLS 1.0 ve 1.1'i devre dışı bırakmak için rehberlik sağlar:

- Office 365'e bağlanan Windows 7 istemcileri için TLS 1.2'nin Windows'da WinHTTP'deki varsayılan güvenli protokol olduğundan emin olun. Daha fazla bilgi için bkz[. KB 3140245 - Windows'da WinHTTP'da varsayılan güvenli protokoller olarak TLS 1.1 ve TLS 1.2'yi etkinleştirmek için güncelleştirme](https://support.microsoft.com/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in).
- TLS 1.0 ve 1.1 bağımlılıklarını kaldırarak zayıf TLS kullanımını gidermek için bkz. [Microsoft'ta TLS 1.2 desteği](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/20/tls-1-2-support-at-microsoft/).
- [Yeni IIS işlevi,](https://cloudblogs.microsoft.com/microsoftsecure/2017/09/07/new-iis-functionality-to-help-identify-weak-tls-usage/) [Windows Server 2012 R2](https://support.microsoft.com/help/4025335/windows-8-1-windows-server-2012-r2-update-kb4025335) ve [Windows Server 2016](https://support.microsoft.com/help/4025334/windows-10-update-kb4025334)'da zayıf güvenlik protokolleri kullanarak hizmete bağlanan istemcileri bulmayı kolaylaştırır.
- [TLS 1.0 sorununu çözme](https://www.microsoft.com/download/details.aspx?id=55266) hakkında daha fazla bilgi edinin.
- Güvenlik yaklaşımımız hakkında genel bilgi için [Office 365 Güven Merkezi](https://www.microsoft.com/trustcenter/cloudservices/office365)'ne gidin.
- [TLS 1.0/1.1'i Kullanımdan Kaldırmaya Hazırlık - Office 365 Skype Kurumsal](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/ba-p/222247)
- [Exchange Server TLS kılavuzu, bölüm 1: TLS 1.2'ye Hazırlanıyor](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-1-getting-ready-for-tls-1-2/ba-p/607649)
- [Exchange Server TLS kılavuzu, Bölüm 2: TLS 1.2'yi Etkinleştirme ve Kullanmayan İstemcileri Belirleme](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-2-enabling-tls-1-2-and/ba-p/607761)
- [Exchange Server TLS kılavuzu, Bölüm 3: TLS 1.0/1.1'i kapatma](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-3-turning-off-tls-1-0-1-1/ba-p/607898)
- [Office Online Server'da TLS 1.1 ve TLS 1.2 desteğini etkinleştirme](/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server)
