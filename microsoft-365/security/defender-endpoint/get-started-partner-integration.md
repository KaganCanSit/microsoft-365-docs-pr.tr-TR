---
title: Uç nokta iş ortağı için Microsoft Defender'a olun
ms.reviewer: ''
description: Çözümlerinizi Uç Nokta için Microsoft Defender ile tümleştirin ve iş ortağı olun adımlarını ve gereksinimlerini öğrenin
keywords: iş ortağı, tümleştirme, çözüm doğrulama, sertifika, gereksinimler, üye, misa, uygulama portalı
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.openlocfilehash: b063d8435817d7dd64c3febf6e3399f3876ef894
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319833"
---
# <a name="become-a-microsoft-defender-for-endpoint-partner"></a>Uç nokta iş ortağı için Microsoft Defender'a olun

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


Uç nokta çözüm ortağı için Defender olmak için, aşağıdaki adımları izlemeli ve tamamlamanız gerekir.

## <a name="step-1-subscribe-to-a-microsoft-defender-for-endpoint-license"></a>1. Adım: Uç nokta lisansı için Microsoft Defender'a abone olma

Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink). Abone olarak, uç nokta için Microsoft Defender ile tümleştirilmiş çözümler geliştirmek üzere en çok üç cihazla Uç Nokta için Microsoft Defender kiracısı kullanabilirsiniz.

## <a name="step-2-fulfill-the-solution-validation-and-certification-requirements"></a>2. Adım: Çözüm doğrulama ve sertifika gereksinimlerini karşılamak

Teknoloji iş ortaklarının tümleştirme çalışmalarını onaylarının en iyi yolu, ortak bir müşterinin önerilen tümleştirme tasarımını onaylamasını sağlamaktır  (\(müşteri, Microsoft 365 Defender'daki İş Ortağı Uygulaması sayfasında İş Ortağı ve API > [](https://security.microsoft.com/interoperability/partnersapps)\) İş Ortağı uygulamaları önerin seçeneğini kullanabilir ve uç nokta için Microsoft Defender ekibi tarafından test edilebilir ve indirilebilir.

Uç Nokta için Microsoft Defender ekibi tümleştirmeyi gözden geçirip onaylarsa sizi Microsoft Akıllı Güvenlik Birliği'nde iş ortağı olarak dahil edileceksiniz.

## <a name="step-3-get-listed-in-the-microsoft-defender-for-endpoint-partner-application-portal"></a>3. Adım: Uç nokta iş ortağı uygulama portalı için Microsoft Defender'da listelenmiştir

Uç Nokta için Microsoft Defender, Uç nokta için Microsoft Defender yönetim portalına eklenmiş olan ürün [](partner-applications.md) ortağı sayfası kullanılarak üçüncü taraf uygulamaları bulma ve tümleştirmeyi destekler.

Şirketinizin ürün için iş ortağı sayfasında iş ortağı olarak listelenmiş olarak yer almak için, aşağıdaki bilgileri sağlaym gerekir:

1. Kare logo (SVG).
2. Sunulacak ürünün adı.
3. 15 sözcüklik bir ürün açıklaması girin.
4. Müşteriler için yeterli bilgi içerecek tümleştirmeyi veya blog gönderilerini tamamlamak için müşterinin giriş sayfasına bağlantı. Pazarlama ve mühendislik ekipleri Uç Nokta ürün adı için Microsoft Defender dahil olmak üzere tüm basın yayınlarını gözden geçirebilirsiniz. Gözden geçirme işleminin yapılması için en az 10 gün bekleyin.
5. Çok kiracılı bir Azure AD yaklaşımı kullanıyorsanız, uygulamanın kullanımını izlemek için Azure AD uygulama adı gerekir.
6. Microsoft DefenderUser-Agent Uç nokta genel API'leri kümesi için Microsoft Defender'a yapılan her API aramalarına api alanını Graph API'leri dahil edin. Bu, istatistiksel amaçlarla, sorun giderme ve iş ortağı tanıma için kullanılır. Ayrıca bu adım, Microsoft Akıllı Güvenlik İlişkisi'ne (MISA) üyelik için bir zorunluluktur.

   Şu adımları izleyin:

   - Her User-Agent HTTP isteği üst bilgisinde Varsayılan Alan alanını aşağıdaki biçime ayarlayın.

     ```http
     MdePartner-{CompanyName}-{ProductName}/{Version}
     ```

     Örneğin, Kullanıcı-Aracısı:

     ```http
     MdePartner-Contoso-ContosoCognito/1.0.0
     ```

   - Daha fazla bilgi için [bkz. RFC 2616 section-14.43](https://tools.ietf.org/html/rfc2616#section-14.43).

Uç Nokta için Microsoft Defender ile ortaklıklar, ortak müşterilerimizin savunmayı daha da kolaylaştırmasına, tümleştirerek ve savunmayı kolaylaştırmasına yardımcı olur. Modern tehditleri birlikte engelp yanıtarak, Uç Nokta için Microsoft Defender iş ortağı olmayı ve müşterileri ve onların varlıklarını etkili bir şekilde koruma ortak hedefine ulaşmaktan mutluluk istiyoruz.

## <a name="misa-nomination"></a>MİSA synliği 
Yönetilen güvenlik hizmeti sağlayıcıları (MSSP) ve bağımsız yazılım satıcıları (ISV) Microsoft Akıllı Güvenlik Birliği'ne (MISA) aday göster olabilir. Daha fazla bilgi için [bkz. MISA bilgileri sayfası](https://www.microsoft.com/security/business/intelligent-security-association).


## <a name="related-topics"></a>İlgili konular

- [Teknik iş ortağı fırsatları](partner-integration.md)
