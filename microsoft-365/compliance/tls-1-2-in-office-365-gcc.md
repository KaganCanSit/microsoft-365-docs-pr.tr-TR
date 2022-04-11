---
title: Microsoft 365 GCC High ve DoD'da TLS 1.0 ve 1.1'i devre dışı bırakma
description: Microsoft'un Microsoft 365'daki GCC High ve DoD ortamlarında TLS 1.1 ve 1.0 desteğini nasıl devre dışı bırakıldığını açıklar.
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
ms.openlocfilehash: bad0dc997f2c564670858d2ac35b2cd3177e0578
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760400"
---
# <a name="disabling-tls-10-and-11-in-microsoft-365-gcc-high-and-dod"></a>Microsoft 365 GCC High ve DoD'da TLS 1.0 ve 1.1'i devre dışı bırakma

## <a name="summary"></a>Özet

Federal Risk ve Yetkilendirme Yönetimi Programı 'nın (FedRAMP) en son uyumluluk standartlarına uymak için, GCC Yüksek ve DoD ortamları için Microsoft 365 Aktarım Katmanı Güvenliği (TLS) 1.1 ve 1.0 sürümlerini devre dışı bırakıyoruz. Bu değişiklik daha önce [Office 365'de TLS 1.2'nin zorunlu kullanımına hazırlanma bölümünde Microsoft Desteği](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365) aracılığıyla duyurulmuştu.

Verilerinizin güvenliği önemlidir ve hizmet kullanımınızı etkileyebilecek değişiklikler konusunda şeffaflığı taahhüt ediyoruz.

[Microsoft TLS 1.0 uygulamasının](https://support.microsoft.com/help/3117336) bilinen güvenlik açıkları olmasa da FedRAMP uyumluluk standartlarına bağlı kalırız. Bu nedenle 15 Ocak 2020'de GCC High ve DoD ortamlarında Microsoft 365 TLS 1.1 ve 1.0'ı devre dışı bırakmış olduk. TLS 1.1 ve 1.0 bağımlılıklarını kaldırma hakkında bilgi için aşağıdaki teknik incelemeye bakın:

[TLS 1.0 sorununu çözme](https://www.microsoft.com/download/details.aspx?id=55266)

## <a name="more-information"></a>Daha fazla bilgi

15 Ocak 2020'den itibaren GCC High ve DoD ortamlarındaki Microsoft 365 TLS 1.1 ve 1.0'ı devre dışı bırakacaktır.

15 Ocak 2020'ye kadar istemci sunucuları ve tarayıcı sunucularının tüm birleşimleri, tüm bağlantıların Microsoft 365 sorunları olmadan yapılabileceğinden emin olmak için TLS sürüm 1.2 'yi (veya sonraki bir sürümü) kullanmalıdır. Bu, istemci sunucuları ve tarayıcı sunucularının belirli birleşimlerinde güncelleştirmeler yapılmasını gerektirebilir.

SharePoint ve OneDrive için .NET'i TLS 1.2'yi destekleyecek şekilde güncelleştirmeniz ve yapılandırmanız gerekir. Bilgi için bkz. [İstemcilerde TLS 1.2'yi etkinleştirme](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

Office 365 GCC Yüksek ve DoD'ye kesintisiz erişiminizi sürdürdüğünüzden emin olmak için istemci bilgisayarlarınızı güncelleştirmeniz gerekir.

TLS 1.2 kullanmak için TLS 1.0 veya TLS 1.1 üzerinden Microsoft 365 API'lerini çağıran uygulamaları güncelleştirmeniz gerekir. .NET 4.5 varsayılan olarak TLS 1.1'dir. .NET yapılandırmanızı güncelleştirmek için bkz [. İstemcilerde Aktarım Katmanı Güvenliği (TLS) 1.2'yi etkinleştirme](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client). Daha fazla bilgi için bkz. [Office 365'de TLS 1.2'nin zorunlu kullanımına hazırlanma](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

Aşağıdaki istemci uygulamalarının TLS 1.2'yi kullanamayacağını biliyoruz:

- Android 4.3 ve önceki sürümleri
- Firefox 5.0 ve önceki sürümleri
- Windows 7 ve önceki sürümlerinde Internet Explorer 8-10
- Windows Phone 8.0'da Internet Explorer 10
- Safari 6.0.4/OS X 10.8.4 ve önceki sürümleri

Microsoft Online hizmetlerine yönelik bağlantıların geçerli analizi çoğu hizmet ve uç noktanın çok az TLS 1.1 ve 1.0 kullanımı gördüğünü gösterse de, TLS 1.1 ve 1.0 desteği sona ermeden önce etkilenen istemcileri veya sunucuları gerektiği gibi güncelleştirebilmeniz için bu değişikliğe ilişkin bir bildirim sağlıyoruz. Karma senaryolar veya Active Directory Federasyon Hizmetleri (AD FS) (AD FS) için herhangi bir şirket içi altyapı kullanıyorsanız, altyapının TLS 1.2 (veya sonraki bir sürüm) kullanan hem gelen hem de giden bağlantıları destekleyebildiğinden emin olun.

TLS 1.2 kullanamayan listelenen istemcileri kullanırsanız karşılaşabileceğiniz kesintilere ek olarak, TLS 1.1 ve 1.0'ın kaldırılması aşağıdaki Microsoft ürününü kullanabilmenizi engeller:

- Lync telefonu

## <a name="references"></a>Başvurular

İstemcilerinizin TLS 1.2 kullandığından emin olmak için yönergeler ve başvurular için bkz. [Office 365'de TLS 1.2'nin zorunlu kullanımına hazırlanma](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).
