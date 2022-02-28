---
title: İleti Şifrelemesi (OME) sürüm karşılaştırması
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
description: Bu makale, farklı sürümleri arasındaki farkları açıklamaya yardımcı Office 365 İleti Şifrelemesi.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 508a129cd472c8843e2af4a012560b17a44c49aa
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987404"
---
# <a name="compare-versions-of-ome"></a>OME sürümlerini karşılaştırma

> [!IMPORTANT]
> 28 Şubat 2021'de, Microsoft, Exchange Online'te AD RMS desteğini Exchange Online. Exchange posta kutularınizin çevrimiçi olduğu karma bir ortam dağıttıysanız ve Şirket içi Active Directory RMS ile IRM kullanıyorsanız, Azure'a geçişniz gerekir. Daha önce Orta düzeydeki bir GCC de bundan etkilenir. Bilgi için, bu makaledeki "AD RMS'nin Exchange Online" makalesine bakın.

Bu makalenin kalan bölümü, eski Office 365 İleti Şifrelemesi (OME) ile yeni OME özellikleri ve özellikleri Office 365 Gelişmiş İleti Şifrelemesi. Yeni özellikler bir birleşme ve hem OME'nin hem de Bilgi Hakları Yönetimi'nin (IRM) daha yeni bir sürümüdür. GCC Yüksek'e dağıtmanın benzersiz özellikleri de ana hatlarıyla açık sahiptir. Bu ikisi kuruluş içinde birlikte yer alan bir kişi olabilir. Yeni becerilerin nasıl çalışması hakkında bilgi için bkz. [Office 365 İleti Şifrelemesi(OME)](ome.md).

Bu makale, bu konuda daha geniş bir makale dizisinin Office 365 İleti Şifrelemesi. Bu makale yöneticilere ve ITPro'lere yöneliktir. Şifreli bir iletiyi gönderme veya alma hakkında yalnızca bilgi arıyorsanız, [Office 365 İleti Şifrelemesi (OME)](ome.md) makalelerinin listesine bakın ve ihtiyaçlarına en uygun makaleyi bulun.

## <a name="overview-of-ad-rms-deprecation-in-exchange-online"></a>Exchange Online'da AD RMS'nin kullanımdan Exchange Online

Exchange Online, e-posta iletilerinin ve eklerin çevrimiçi ve çevrimdışı korunmasını sağlayan Bilgi Hakları Yönetimi (IRM) işlevini içerir. Varsayılan olarak, Exchange Online Azure Information Protection'i kullanır. Öte yandan, kuruluş IRM'yi şirket Exchange Online Active Directory Rights Management Service (AD RMS) kullanmak üzere yapılandırmış olabilir. E-Exchange Online AD RMS desteği artık desteklenmiyor. Bunun yerine, Azure Information Protection AD RMS'nin tamamen yerini alır.

Bu kullanımdan geçirmenin kuruluşu etkileyip etkilemeyeceklerini değerlendirmek için, bkz. [Exchange Online'te AD RMS'yi Azure RMS'ye geçirme](/exchange/troubleshoot/administration/migrate-ad-rms-to-azure). Bu makalede geçiş seçenekleriyle ilgili öneriler sunulmaktadır.

## <a name="side-by-side-comparison-of-ome-features-and-capabilities"></a>OME özelliklerinin ve özelliklerinin yan yana karşılaştırması

|           **Durum**           | **Eski OME**    | **AD RMS'de IRM**        | **Yeni OME özellikleri** |
|-----------------------------------|-------------------|-------------------|--------------------------|
|*Şifreli posta gönderme*        |Posta Exchange kuralları aracılığıyla|Son kullanıcı Web'Outlook masaüstünden Outlook veya posta akış kuralları aracılığıyla Exchange başlatılmıştır|Web üzerinde Outlook masaüstü, Mac için Outlook veya Outlook'den başlatılan son kullanıcı; Exchange posta akış kuralları (aktarım kuralları olarak da bilinir) ve Veri Kaybı Önleme (DLP) aracılığıyla|
|*Hak yönetimi şablonu*       |   Yok      |Do Not Forward option and custom templates|Do Not Forward option, encrypt-only option, and custom templates|
|*Alıcı türü*                   |İç ve dış alıcılar|Yalnızca iç alıcılar         |İç ve dış alıcılar|
|*İç alıcı deneyimi*|Alıcılar bir HTML iletisi alırlar ve bu ileti bir web tarayıcısında veya mobil uygulamada indir açıp açılır|Outlook istemcilerinde yerel satır içi deneyimi|Yerel istemci kullanan aynı kuruluşta yer alan alıcılar için yerel satır içi Outlook.  Alıcılar OME portalında diğer istemcileri kullanarak iletiyi okuyabilir (Outlook veya uygulama gerekmez).|
|*Dış alıcı deneyimi*|Alıcılar bir HTML iletisi alırlar ve bu ileti bir web tarayıcısında veya mobil uygulamada indir açıp açılır|Yok|Alıcılar için yerel satır içi Microsoft 365 deneyimi. Diğer tüm alıcılar OME portalında ileti okuyabilir (indirme veya uygulama gerekmez).|
|*Ek izinleri*           |Eklerde kısıtlama yok|Ekler korumalıdır|Ekler, "Iletme" seçeneği ve özel şablonlar için korunur. Yöneticiler, yalnızca şifrele seçeneği için eklerin korumalı olup olmadığını seçebilir.|
|*Kendi anahtarınızı (BYOK) getirin desteği*|Yok                |Yok               |BYOK destekli          |
||

## <a name="advantages-of-the-new-ome-capabilities-over-legacy-ome"></a>Eski OME'nin sağladığı yeni OME özelliklerinin avantajları

Yeni özellikler aşağıdaki avantajları sağlar:

- Yalnızca şifrele seçeneğini (güvenli işbirliğine olanak sağlar), İtelama seçeneği ve özel kısıtlamalar kullanabilirsiniz.
- Gönderenler, masaüstü, masaüstü ve masaüstü istemcilerinden yeni özelliklerle Outlook posta Mac için Outlook Web üzerinde Outlook gönderebilir.
- Microsoft 365, desteklenen istemcilerde satır içi deneyimi Outlook. Alternatif olarak, yöneticiler alıcılara markalı Microsoft 365 göstermeyi seçebilir.
- Gmail, Yahoo Microsoft 365 Microsoft hesapları gibi hesaplar, bu alıcılar için daha iyi bir kullanıcı deneyimi sağlayan OME portalıyla federasyon olarak yer almaktadır. Diğer tüm kimlikler, şifreli iletilere erişmek için tek kullanımlık parola kullanır.
- Yöneticiler markalamayı özelleştirilebilir ve birden çok markalama şablonu oluşturabilir.
- Yöneticiler yeni özelliklerle şifrelenmiş e-postaları iptal e-postaları iptal e-posta olarak geri gönderebilirsiniz.
- Bu yeni özellikler, Güvenlik Uyumluluk Merkezi aracılığıyla ayrıntılı kullanım raporları &amp; sağlar.

## <a name="office-365-advanced-message-encryption-capabilities"></a>Office 365 Gelişmiş İleti Şifrelemesi özellikleri

Office 365 Gelişmiş İleti Şifrelemesi, yeni OME özellikleri hakkında ek özellikler sunar. Gelişmiş İleti Şifrelemesi Office 365 İleti Şifrelemesi için, organizasyonda ayarlanmış yeni güvenlik özelliklerine sahip olmak gerekir. Ayrıca, bu özellikleri kullanmak için alıcıların OME Portalı aracılığıyla güvenli postayı görüntülemesi ve yanıtlaması gerekir. Gelişmiş özellikler şunlardır:

- İleti iptali

- İletinin süre sonu

- Birden çok markalama şablonu

Office 365 Gelişmiş İleti Şifrelemesi, GCC High'da destek değildir.

Gelişmiş İleti Şifrelemesi'nin kullanımı hakkında bilgi için bkz[. Office 365 Gelişmiş İleti Şifrelemesi](ome-advanced-message-encryption.md).

## <a name="unique-characteristics-of-office-365-message-encryption-in-a-gcc-high-deployment"></a>GCC Yüksek Office 365 İleti Şifrelemesi bir GCC özellikleri

Office 365 İleti Şifrelemesi Yüksek Office 365 İleti Şifrelemesi kullanmayı planlıyorsanız, GCC deneyimiyle ilgili bazı benzersiz özellikler vardır.

### <a name="encrypted-email-between-gcc-high-and-gcc-high-recipients"></a>Yüksek ve Yüksek alıcılar arasında GCC-posta GCC-posta

E-postalar PC ve Mac Outlook Mac için Web üzerinde Outlook'de e-postaları el ile şifreleyebilirsiniz ya da kuruluşlar e-postaları şifrelemek için bir ilke Exchange akış kurallarını kullanarak e-postaları şifreler.

GCC High içindeki alıcılar, PC ve Mac için Outlook'de aynı satır içi okuma deneyimini ve diğer Web üzerinde Outlook aynı şekilde devam edin.

### <a name="encrypted-email-between-gcc-high-and-non-gcc-high-recipients"></a>Yüksek ve Yüksek GCC Olmayan alıcılar arasında GCC e-posta

GCC High içindeki gönderenler, şifrelenmiş e-postayı GCC sınırının dışında gönderebilir.

GCC High dışındaki tüm alıcılar, örneğin ticari Microsoft 365 kullanıcıları, Outlook.com kullanıcıları ve Gmail ve Yahoo gibi diğer e-posta sağlayıcılarının diğer kullanıcıları bir kaydırma postası alır. Bu kaydırma postası alıcıyı, iletiyi okuyabilmek ve yanıtlamak için alıcının bulunduğu OME Portalı'ne yeniden gönderir. Bu durum, OME şifreli postayı Yüksek olarak gönderen GCC dışından gönderenler için de GCC olur.

## <a name="coexistence-of-legacy-ome-and-the-new-capabilities-in-the-same-tenant"></a>Aynı kiracıda eski OME'nin birlikte olması ve yeni özellikleri

Aynı kiracıda hem eski OME'yi hem de yeni özellikleri kullanabilirsiniz. Yönetici olarak bunu, posta akışı kurallarınızı 2013'e göre oME'nin hangi sürümünü kullanmak istediğinize karar verdiyseniz.

- OME'nin eski sürümünü belirtmek için, Exchange akışı kuralı eylem planı **OME'nin önceki sürümünü uygulama.**

- Yeni özellikleri belirtmek için Posta akışı kuralı Exchange Uygula eylemlerini ve **Office 365 İleti Şifrelemesi korumasını kullanın**.

Kullanıcılar masaüstü, masaüstü ve masaüstü bilgisayarlarından yeni özelliklerle şifrelenmiş Outlook posta Mac için Outlook posta Web üzerinde Outlook.

## <a name="migrate-from-legacy-ome-to-the-new-capabilities"></a>Eski OME'den yeni özelliklere geçiş

OME'nin her iki sürümü de bir arada kullanabiliyor olsa da, kural eylemini kullanan eski posta akışı kurallarınızı düzenlemenizi kesinlikle öneririz. Yeni özellikleri kullanmak için **OME'nin** önceki sürümünü kullanın. Posta akışı kural eylemsini kullanmak için Bu kuralları güncelleştirin **Office 365 İleti Şifrelemesi koruma uygula**. Yönergeler için bkz. [E-posta iletilerini şifrelemek için posta akış kurallarını Office 365](define-mail-flow-rules-to-encrypt-email.md).

## <a name="get-started-with-ome"></a>OME ile çalışmaya başlama

Normalde, yeni OME özellikleri, organizasyonunız için otomatik olarak etkinleştirilir. Kuruluş içindeki yeni OME özellikleri hakkında daha fazla bilgi için bkz. Yeni [işletim sistemi Office 365 İleti Şifrelemesi ayarlama](set-up-new-message-encryption-capabilities.md).

Azure Information Protection'ı etkinleştirdiyseniz, oME'nin eski sürümü, organizasyonunız için otomatik olarak etkinleştirilir. Geçmişte, Azure Information Protection etkinleştirilmemiş olsa bile eski OME çalışıyordu. Bu artık durum böyle değildir.

Eski OME'yi kullanmaya başlamak için Azure Information Protection'ı etkinleştirdiyseniz, kural eylemlerini kullanan posta akışı kurallarını **yapılandırarak OME'nin önceki sürümünü uygulama.** Yönergeler için bkz. [E-posta iletilerini şifrelemek için posta akışı kurallarını tanımlama](define-mail-flow-rules-to-encrypt-email.md).
