---
title: İleti şifreleme sürümü karşılaştırması
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Bu makale, ileti şifrelemesinin farklı sürümleri arasındaki farkları açıklamaya yardımcı olur.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 64a67ac9423463e4fcf1b5a3ff6c2262801933b0
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629343"
---
# <a name="compare-versions-of-message-encryption"></a>İleti şifreleme sürümlerini karşılaştırma

> [!IMPORTANT]
> Microsoft, 28 Şubat 2021'de Exchange Online'da AD RMS desteğini kullanımdan kaldırmıştı. Exchange posta kutularınızın çevrimiçi olduğu bir karma ortam dağıttıysanız ve şirket içi Active Directory RMS ile IRM kullanıyorsanız Azure'a geçiş yapmanız gerekir. GCC Orta ortamına dağıtılan kuruluşlar da etkilenir. Bilgi için bu makaledeki "Exchange Online'da AD RMS'nin kullanımdan kaldırılmasına genel bakış" bölümüne bakın.

Bu makalenin geri kalanında eski Office 365 İleti Şifrelemesi (OME) ile Microsoft Purview İleti Şifrelemesi ve Microsoft Purview Gelişmiş İleti Şifrelemesi karşılaştırılır. Microsoft Purview İleti Şifrelemesi, hem OME hem de Bilgi Hakları Yönetimi'nin (IRM) birleştirilmesi ve daha yeni bir sürümüdür. GCC High'a dağıtmanın benzersiz özellikleri de özetlenmiştir. bu ikisi kuruluşunuzda bir arada bulunabilir. Yeni özelliklerin nasıl çalıştığı hakkında bilgi için bkz. [İleti Şifrelemesi (OME) Office 365](ome.md).

Bu makale, ileti şifreleme hakkında daha büyük bir makale serisinin parçasıdır. Bu makale yöneticilere ve BTPro'lara yöneliktir. Yalnızca şifreli ileti gönderme veya alma hakkında bilgi arıyorsanız [İleti şifrelemesi](ome.md) makalelerinin listesine bakın ve gereksinimlerinize en uygun makaleyi bulun.

## <a name="overview-of-ad-rms-deprecation-in-exchange-online"></a>Exchange Online'da AD RMS'nin kullanımdan kaldırılmasına genel bakış

Exchange Online, e-posta iletilerinin ve eklerinin çevrimiçi ve çevrimdışı olarak korunmasını sağlayan Bilgi Hakları Yönetimi (IRM) işlevselliğini içerir. varsayılan olarak, Exchange Online Azure Information Protection kullanır. Ancak, kuruluşunuz Exchange Online IRM'yi şirket içi Active Directory Rights Management Service'i (AD RMS) kullanacak şekilde yapılandırmış olabilir. Exchange Online'da AD RMS desteği sona eriyor. Bunun yerine Azure Information Protection AD RMS'nin yerini tamamen alır.

Bu kullanımdan kaldırmanın kuruluşunuzu etkileyip etkilemediğini değerlendirmek için bkz. [Exchange Online'de AD RMS'yi Azure RMS'ye geçirme](/exchange/troubleshoot/administration/migrate-ad-rms-to-azure). Bu makalede geçiş seçenekleriyle ilgili öneriler sağlanır.

## <a name="side-by-side-comparison-of-message-encryption-features-and-capabilities"></a>İleti şifreleme özelliklerinin ve özelliklerinin yan yana karşılaştırması

|           **Durum**           | **Eski OME**    | **AD RMS'de IRM**        | **Microsoft Purview İleti Şifrelemesi** |
|-----------------------------------|-------------------|-------------------|--------------------------|
|*Şifrelenmiş posta gönderme*        |Exchange posta akışı kuralları aracılığıyla|Outlook masaüstünden veya Web üzerinde Outlook'tan başlatılan son kullanıcı; veya Exchange posta akışı kuralları aracılığıyla|Outlook masaüstü, Mac için Outlook veya Web üzerinde Outlook'tan başlatılan son kullanıcı; Exchange posta akışı kuralları (aktarım kuralları olarak da bilinir) ve veri kaybı önleme (DLP) aracılığıyla|
|*Hak yönetimi şablonu*       |   Yok      |İletme seçeneği ve özel şablonlar|İletme seçeneği, yalnızca şifrele seçeneği ve özel şablonlar|
|*Alıcı türü*                   |İç ve dış alıcılar|Yalnızca iç alıcılar         |İç ve dış alıcılar|
|*İç alıcı deneyimi*|Alıcılar web tarayıcısında veya mobil uygulamada indirdikleri ve açtıkları bir HTML iletisi alır|Outlook istemcilerinde yerel satır içi deneyim|Outlook istemcilerini kullanan aynı kuruluştaki alıcılar için yerel satır içi deneyim.  Alıcılar, Outlook dışındaki istemcileri kullanarak OME portalından ileti okuyabilir (indirme veya uygulama gerekmez).|
|*Dış alıcı deneyimi*|Alıcılar web tarayıcısında veya mobil uygulamada indirdikleri ve açtıkları bir HTML iletisi alır|Yok|Microsoft 365 alıcıları için yerel satır içi deneyim. Diğer tüm alıcılar OME portalından iletiyi okuyabilir (indirme veya uygulama gerekmez).|
|*Ek izinleri*           |Eklerde kısıtlama yok|Ekler korunur|Ekler İletme seçeneği ve özel şablonlar için korunur. Yöneticiler yalnızca şifrele seçeneğinin eklerinin korunup korunmayacağını seçebilir.|
|*Kendi anahtarını getir (BYOK) desteği*|Yok                |Yok               |BYOK desteklenir          |
||

## <a name="advantages-of-microsoft-purview-message-encryption-over-legacy-ome"></a>eski OME'ye kıyasla Microsoft Purview İleti Şifrelemesi avantajları

Yeni özellikler aşağıdaki avantajları sağlar:

- Yalnızca şifrele seçeneğini (güvenli işbirliğine olanak tanıyan), İletme seçeneğini ve özel kısıtlamaları kullanabilme.
- Gönderenler, outlook masaüstü, Mac için Outlook ve Web üzerinde Outlook istemcilerinden el ile yeni özelliklerle şifrelenmiş posta gönderebilir.
- Microsoft 365 alıcıları, desteklenen Outlook istemcilerinde satır içi bir deneyim kullanabilir. Alternatif olarak, yöneticiler Microsoft 365 alıcılarına markalı bir deneyim göstermeyi seçebilir.
- Gmail, Yahoo ve Microsoft hesapları gibi Microsoft 365 dışındaki hesaplar, bu alıcılar için daha iyi bir kullanıcı deneyimi sağlayan OME portalıyla birleştirilir. Diğer tüm kimlikler şifrelenmiş iletilere erişmek için tek seferlik bir geçiş kodu kullanır.
- Yöneticiler markayı özelleştirebilir ve birden çok marka şablonu oluşturabilir.
- Yöneticiler yeni özelliklerle şifrelenmiş e-postaları iptal edebilir.
- Yeni özellikler, Güvenlik &amp; Uyumluluk Merkezi aracılığıyla ayrıntılı kullanım raporları sağlar.

## <a name="microsoft-purview-advanced-message-encryption-capabilities"></a>Microsoft Purview Gelişmiş İleti Şifreleme özellikleri

Microsoft Purview Gelişmiş İleti Şifrelemesi, Microsoft Purview İleti Şifrelemesi ek özellikler sunar. Gelişmiş İleti Şifrelemesi'ni kullanmak için kuruluşunuzda Microsoft Purview İleti Şifrelemesi ayarlamış olmanız gerekir. Ayrıca, bu özellikleri kullanabilmek için alıcıların güvenli postaları Microsoft Purview İleti Şifrelemesi Portalı üzerinden görüntülemesi ve yanıtlaması gerekir. Gelişmiş özellikler şunlardır:

- İleti iptali

- İleti süre sonu

- Birden çok marka şablonu

Gelişmiş İleti Şifrelemesi GCC High'da desteklenmez.

Gelişmiş İleti Şifrelemesi kullanma hakkında bilgi için bkz. [Microsoft Purview Gelişmiş İleti Şifrelemesi](ome-advanced-message-encryption.md).

## <a name="unique-characteristics-of-microsoft-purview-message-encryption-in-a-gcc-high-deployment"></a>GCC Yüksek dağıtımında Microsoft Purview İleti Şifrelemesi benzersiz özellikleri

Microsoft Purview İleti Şifrelemesi bir GCC High ortamında kullanmayı planlıyorsanız, alıcı deneyimiyle ilgili bazı benzersiz özellikler vardır.

### <a name="encrypted-email-between-gcc-high-and-gcc-high-recipients"></a>GCC High ve GCC High alıcıları arasında şifrelenmiş e-posta

Gönderenler PC ve Mac için Outlook'ta e-postaları el ile şifreleyebilir ve Web üzerinde Outlook veya kuruluşlar Exchange posta akışı kurallarını kullanarak e-postaları şifrelemek için bir ilke ayarlayabilir.

GCC High içindeki alıcılar, PC ve Mac için Outlook'ta diğer tüm kullanıcılarla aynı satır içi okuma deneyimini ve Web üzerinde Outlook alır.

### <a name="encrypted-email-between-gcc-high-and-non-gcc-high-recipients"></a>GCC High ve GCC Dışı Yüksek alıcılar arasında şifrelenmiş e-posta

GCC High içindeki gönderenler, şifrelenmiş e-postaları GCC Yüksek sınırının dışına gönderebilir ve bunun tersi de geçerlidir.

Ticari Microsoft 365 kullanıcıları, Outlook.com kullanıcıları ve Gmail ve Yahoo gibi diğer e-posta sağlayıcılarının diğer kullanıcıları dahil olmak üzere GCC High dışındaki tüm alıcılar bir sarmalayıcı posta alır. Bu sarmalayıcı posta, alıcıyı Microsoft Purview İleti Şifrelemesi Portalı'na yönlendirir; burada alıcı iletiyi okuyabilir ve yanıtlayabilir. Bu, GCC High dışında GCC High'a OME şifreli posta gönderenler için de geçerlidir.

## <a name="coexistence-of-legacy-ome-and-microsoft-purview-message-encryption-in-the-same-tenant"></a>Aynı kiracıda eski OME ve Microsoft Purview İleti Şifrelemesi birlikte bulunma

Aynı kiracıda hem eski OME hem de Microsoft Purview İleti Şifrelemesi kullanabilirsiniz. Yönetici olarak, posta akışı kurallarınızı oluştururken hangi ileti şifreleme sürümünü kullanmak istediğinizi seçerek bunu yaparsınız.

- OME'nin eski sürümünü belirtmek için, OME'nin **önceki sürümünü uygula** Exchange posta akışı kuralı eylemini kullanın.

- Microsoft Purview İleti Şifrelemesi belirtmek için, İleti **Şifrelemesi ve hak koruması Office 365 Uygula** Exchange posta akışı kuralı eylemini kullanın.

Kullanıcılar Outlook Masaüstü, Mac için Outlook ve Web üzerinde Outlook Microsoft Purview İleti Şifrelemesi ile şifrelenmiş postaları el ile gönderebilir.

## <a name="migrate-from-legacy-ome-to-microsoft-purview-message-encryption"></a>Eski OME'den Microsoft Purview İleti Şifrelemesi geçiş

Her iki sürüm de bir arada bulunabilse de, Microsoft Purview İleti Şifrelemesi kullanmak için **OME'nin önceki sürümünü uygula** kural eylemini kullanan eski posta akışı kurallarınızı düzenlemenizi kesinlikle öneririz. Posta akışı kuralı eylemini **Office 365 İleti Şifrelemesi ve hak koruması uygula** eylemini kullanacak şekilde bu kuralları güncelleştirin. Yönergeler için bkz. [E-posta iletilerini şifrelemek için posta akışı kuralları tanımlama](define-mail-flow-rules-to-encrypt-email.md).

## <a name="get-started-with-ome"></a>OME kullanmaya başlama

Genellikle Microsoft Purview İleti Şifrelemesi kuruluşunuz için otomatik olarak etkinleştirilir. Kuruluşunuzdaki Microsoft Purview İleti Şifrelemesi hakkında daha fazla bilgi için bkz. [Microsoft Purview İleti Şifrelemesi ayarlama](set-up-new-message-encryption-capabilities.md).

Azure Information Protection etkinleştirdiyseniz kuruluşunuz için OME'nin eski sürümü otomatik olarak etkinleştirilir. Geçmişte Azure Information Protection etkinleştirilmemiş olsa bile eski OME çalışıyordu. Bu durum artık geçerli değil.

Eski OME'yi kullanmaya başlamak için Azure Information Protection etkinleştirdiyseniz, **OME'nin önceki sürümünü uygula** kural eylemini kullanan posta akışı kurallarını yapılandırın. Yönergeler için bkz. [E-posta iletilerini şifrelemek için posta akışı kuralları tanımlama](define-mail-flow-rules-to-encrypt-email.md).
