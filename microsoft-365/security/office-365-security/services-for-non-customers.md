---
title: Microsoft 365'e posta gönderen müşteri olmayanlara yönelik hizmetler
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 19fd3e0f-8dbf-4049-a810-2c8ee6cefd48
ms.collection:
- M365-security-compliance
description: Microsoft, e-posta kullanımında kullanıcı güvenini korumaya yardımcı olmak için kullanıcılarımızın korunmasına yardımcı olmak için çeşitli ilkeler ve teknolojiler getirmiştir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 80eff003ec75eba68d1b194fe83d216fa2d013c0
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64974201"
---
# <a name="services-for-non-customers-sending-mail-to-microsoft-365"></a>Microsoft 365'e posta gönderen müşteri olmayanlara yönelik hizmetler

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

E-posta kötüye kullanımı, gereksiz e-posta ve sahte e-postalar (kimlik avı) e-posta ekosisteminin tamamının yükünü yüklenmeye devam ediyor. Microsoft, e-posta kullanımında kullanıcı güvenini korumaya yardımcı olmak için kullanıcılarımızın korunmasına yardımcı olmak için çeşitli ilkeler ve teknolojiler getirmiştir. Ancak Microsoft, geçerli e-postaların olumsuz etkilenmemesi gerektiğini anlar. Bu nedenle, gönderenlerin gönderme itibarını proaktif olarak yöneterek Microsoft 365 kullanıcılara e-posta teslim etme becerilerini geliştirmelerine yardımcı olacak bir hizmet paketi oluşturduk.

Bu genel bakış, müşteri olmasanız bile kuruluşunuza sağladığımız avantajlar hakkında bilgi sağlar.

## <a name="sender-solutions"></a>Gönderen çözümleri

|Hizmet|Fayda -ları|
|---|---|
|Bu çevrimiçi yardım içeriği|Sağ -lar: <ul><li>EOP kullanıcılarına iletişim sağlamayla ilgili sorular için bir başlangıç noktası.</li><li>İlkelerimizi ve gereksinimlerimizi içeren basit bir çevrimiçi kılavuz içerir.</li><li>Microsoft tarafından kullanılan gereksiz e-posta filtreleri ve kimlik doğrulama teknolojilerine genel bakış.</li><ul>|
|[Microsoft desteği](#microsoft-support)|Teslim sorunları için kendi kendine yardım ve yükseltme desteği sağlar.|
|[İstenmeyen Posta Önleme IP Liste Kaldırma Portalı](#anti-spam-ip-delist-portal)|IP listeden çıkarma isteği göndermek için bir araç. Bu isteği göndermeden önce, söz konusu IP'den kaynaklanan diğer postaların kötü amaçlı veya kötü amaçlı olmadığından emin olmak gönderenin sorumluluğundadır.|
|[Exchange Online kaynaklı gereksiz e-posta için uygunsuz kullanım ve istenmeyen posta bildirimi](#abuse-and-spam-reporting-for-junk-email-originating-from-exchange-online)|İstenmeyen postaların ve diğer istenmeyen postaların Exchange Online gönderilmesini ve İnternet'in ve posta sisteminizin dağınık olmasına engel olur.|

## <a name="microsoft-support"></a>Microsoft desteği

Microsoft, Microsoft 365 alıcılara posta gönderirken sorun yaşayan kişiler için çeşitli destek seçenekleri sunar. Aşağıdakiler önerilir:

- Aldığınız teslim edilmedi raporundaki yönergeleri izleyin.

- Office 365 [gönderilen posta sorunlarını giderme](troubleshooting-mail-sent-to-office-365.md) bölümünde müşteri olmayanların karşılaştığı en yaygın sorunlara göz atın.

- IP'nizin engellenen gönderenler listesinden kaldırılması için bir istek göndermek için [Microsoft 365 liste kaldırma portalını](https://sender.office.com) kullanın.

- [Microsoft topluluk forumlarını](https://community.office365.com/f/) okuyun.

- Başka bir yöntem kullanarak e-posta göndermeye çalıştığınız müşteriye başvurun ve Microsoft Desteği iletişime geçip sizin adınıza bir destek bileti açmasını isteyin. Bazı durumlarda, yasal nedenlerle Microsoft Desteği engellenen IP alanının sahibi olan gönderenle doğrudan iletişim kurması gerekir. Ancak, müşteri olmayanlar genellikle destek biletlerini açamaz.

  Office 365 için Microsoft Teknik desteği hakkında daha fazla bilgi için bkz. [Destek](/office365/servicedescriptions/office-365-platform-service-description/support).

## <a name="anti-spam-ip-delist-portal"></a>İstenmeyen Posta Önleme IP Liste Kaldırma Portalı

Bu, engellenen Microsoft 365 gönderenler listesinden kendinizi kaldırmak için kullanabileceğiniz bir self servis portalıdır. E-posta adresi Microsoft 365 olan bir alıcıya e-posta göndermeye çalıştığınızda hata iletisi alıyorsanız ve e-posta adresi olması gerektiğini düşünmüyorsanız bu portalı kullanın. Daha fazla bilgi için bkz. [Liste kaldırma portalını kullanarak kendinizi engellenen gönderenler listesinden kaldırma](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md).

## <a name="abuse-and-spam-reporting-for-junk-email-originating-from-exchange-online"></a>Exchange Online kaynaklı gereksiz e-posta için uygunsuz kullanım ve istenmeyen posta bildirimi

Bazen Microsoft 365, üçüncü taraflar tarafından kullanım koşullarımızı ve ilkemizi ihlal ederek gereksiz e-posta göndermek için kullanılır. Office 365'dan gereksiz e-posta alırsanız, bu iletileri Microsoft'a bildirebilirsiniz. Yönergeler için bkz. [İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).
