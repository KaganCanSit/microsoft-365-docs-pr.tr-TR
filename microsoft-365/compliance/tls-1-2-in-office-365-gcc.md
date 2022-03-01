---
title: Yüksek ve DoD'da TLS 1.0 ve 1.1 Microsoft 365 GCC devre dışı bırakma
description: Microsoft'un, Microsoft'un aynı ortamdaki GCC Yüksek ve DoD ortamlarında TLS 1.1 ve 1.0 desteğini nasıl devre dışı Microsoft 365.
author: kccross
manager: laurawi
ms.localizationpriority: medium
search.appverid:
- MET150
audience: ITPro
ms.collection: M365-security-compliance
ms.service: information-protection
ms.topic: article
ms.reviewer: krowley
ms.author: krowley
appliesto:
- Office 365 Business
ms.openlocfilehash: 29ee02c7c54fc7de6ee178f8219f7148a8cb4bfd
ms.sourcegitcommit: 19e16b16f144159b55bb4c544403e3642b69e335
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2022
ms.locfileid: "63015266"
---
# <a name="disabling-tls-10-and-11-in-microsoft-365-gcc-high-and-dod"></a>Yüksek ve DoD'da TLS 1.0 ve 1.1 Microsoft 365 GCC devre dışı bırakma

## <a name="summary"></a>Özet

Federal Risk ve Yetkilendirme Yönetim Programı'nın (FedRAMP) en son uyumluluk standartlarına uymanız için, Microsoft 365 GCC Yüksek ve DoD ortamları için Microsoft 365'de Aktarım Katmanı Güvenliği (TLS) sürüm 1.1 ve 1.0'ı devre dışı bırakmaktadırk. Bu değişiklik daha önce Microsoft Desteği tarafından, Microsoft'ta [TLS 1.2'nin](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365) zorunlu olarak kullanımına hazırlanma makalesinde Office 365.

Verilerinizin güvenliği önemlidir ve hizmeti kullanımınızı etkileyebilecek değişikliklerle ilgili saydamlığı taahhütte bulunduk.

[Microsoft TLS 1.0 uygulamasının](https://support.microsoft.com/help/3117336) bilinen bir güvenlik açıkları olmasına rağmen, FedRAMP uyumluluk standartlarını taahhüt ediyoruz. Bu nedenle, 15 Ocak 2020'de GCC Yüksek ve DoD ortamlarında Microsoft 365'de TLS 1.1 ve 1.0'i devre dışı bırakılmıştır. TLS 1.1 ve 1.0 bağımlılıklarını kaldırma hakkında bilgi için aşağıdaki teknik belgeye bakın:

[TLS 1.0 sorununu çözme](https://www.microsoft.com/download/details.aspx?id=55266)

## <a name="more-information"></a>Daha fazla bilgi

15 Ocak 2020'den itibaren Microsoft 365 GCC Yüksek ve DoD ortamlarındaki TLS 1.1 ve 1.0 devre dışı bırakılacaktır.

15 Ocak 2020'den itibaren, istemci sunucuları ve tarayıcı sunucularının tüm bileşimleri TLS sürüm 1.2'yi (veya daha sonraki bir sürümü) kullanarak, bağlantı sorunlarının olmadan tüm bağlantılar Microsoft 365. Bu işlem, istemci sunucularının ve tarayıcı sunucularının bazı bileşimlerinin güncelleştirmelerini gerekli olabilir.

Daha SharePoint ve OneDrive için, TLS 1.2'yi destekleyecek şekilde .NET'i güncelleştirmeniz ve yapılandırmaniz gerekir. Bilgi için bkz [. İstemcilerde TLS 1.2'yi etkinleştirme](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

Yüksek ve DoD alanlarına kesintisiz erişimi korumak için istemci bilgisayarlarınızı Office 365 GCC gerekir.

TLS 1.2'yi kullanmak için, MICROSOFT 365 API'leri TLS 1.0 veya TLS 1.1 üzerinden çağıran uygulamaları güncelleştirmeniz gerekir. .NET 4.5 varsayılan olarak TLS 1.1'i kullanır. .NET yapılandırmanızı güncelleştirmek için bkz. [İstemcilerde Aktarım Katmanı Güvenliği (TLS) 1.2'yi etkinleştirme](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client). Daha fazla bilgi için bkz. Yeni Aralık'ta [TLS 1.2'nin zorunlu kullanımına hazırlanma Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

Aşağıdaki istemci uygulamalarının TLS 1.2'yi kullanamayanı biliyoruz:

- Android 4.3 ve önceki sürümleri
- Firefox 5.0 ve önceki sürümleri
- 7 ve önceki sürümlerde Internet Explorer Windows 8–10
- Internet Explorer 10 8.0 Windows Phone da yenile
- Safari 6.0.4/OS X 10.8.4 ve önceki sürümler

Microsoft Online hizmetleri bağlantılarının geçerli çözümlemesi, çoğu hizmet ve uç noktanın TLS 1.1 ve 1.0 kullanımının az olduğunu gösteriyor olsa da, TLS 1.1 ve 1.0'ın sona ermeden önce etkilenen istemcileri veya sunucuları gerektiğinde güncelleştirebilirsiniz. Karma senaryolar veya Active Directory Federasyon Hizmetleri (AD FS) için herhangi bir şirket içi altyapı kullanıyorsanız, altyapının TLS 1.2 (veya daha sonraki bir sürüm) kullanan gelen ve giden bağlantıları destekleyeye olduğundan emin olun.

TLS 1.2 kullanmayacak listelenen istemcileri kullanıyorsanız, yaşanabilecek kesintilere ek olarak, TLS 1.1 ve 1.0'ın kaldırılması, aşağıdaki Microsoft ürününü kullanamanizi engel olur:

- Lync telefonu

## <a name="references"></a>Başvurular

İstemcilerin TLS 1.2'yi kullanırkenn emin olmak için yol gösterme ve başvurular için, bkz. Office 365'de [TLS 1.2'nin zorunlu kullanımına hazırlanma](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).