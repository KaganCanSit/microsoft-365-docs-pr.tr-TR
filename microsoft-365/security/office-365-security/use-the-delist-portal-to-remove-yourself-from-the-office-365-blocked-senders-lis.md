---
title: Engellenen gönderenler listesinden kendinizi kaldırın ve 5.7.511 Erişim engellendi hatalarına neden olun
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 04/18/2016
audience: ITPro
ms.topic: troubleshooting
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 0bcecdd4-3343-4cc0-9e58-e19d4de515e8
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Bu makalede, sizi engellenen gönderenler listesinden kaldırmak için deliste Microsoft 365 kullanmayı öğrenirsiniz. Bu, 5.7.511 Erişim reddedildi hatalarına verilen en iyi yanıttır.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 58ddb2913ce7ecd047b1d5acb360c8f4c9ff5074
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775796"
---
# <a name="use-the-delist-portal-to-remove-yourself-from-the-blocked-senders-list-and-address-57511-access-denied-errors"></a>Kendinizi engellenen gönderenler listesinden kaldırmak ve 5.7.511 Access'in reddedilen hatalarına karşı adres olarak liste kaldırma portalını kullanma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

E-posta adresi Microsoft 365 olan bir alıcıya e-posta göndermeye çalışsanız da hata iletisi alıyor musunuz (örneğin ve 5.7.511 Erişim reddedildi)? Hata iletisini almamanız gerektiğini düşünüyorsanız, liste portalını kullanarak kendinizi engellenen gönderenler listesinden kaldırabilirsiniz.

## <a name="what-is-the-blocked-senders-list"></a>Engellenen gönderenler listesi nedir?

Microsoft, müşterilerini istenmeyen posta, kimlik avı ve kimlik avı saldırılarından korumak için engellenen gönderenler listesini kullanır. Posta sunucusunun IP adresi, başka bir ifadeyle, posta sunucunuzda İnternet'te kendisini tanımlamak için kullandığı adres, çeşitli nedenlerden biri Microsoft 365 tehdit olarak etiketlendi. BU Microsoft 365 IP adresini listeye ekleyeni zaman, veri merkezlerimiz üzerinden IP adresiyle müşterilerimizden herhangi biri arasındaki tüm iletişimi de önler.

Aşağıdakine benzer bir hata içeren bir e-posta iletisine yanıt geldiğinde, listeye eklenmiştir bilginiz olur:

> 550 5.7.606-649 Erişim reddedildi, IP göndermeyi yasakladı [_IP adresi_] (ör. 5.7.511 Erişim reddedildi): Bu listeden kaldırma isteğide etmek için lütfen yönergeleri ziyaret <https://sender.office.com/> edin ve takip edin. Daha fazla bilgi için bkz[. E-posta teslimi olmayan raporlar Exchange Online](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

burada  _IP adresi_ , posta sunucusunun çalıştır yer alan bilgisayarın IP adresidir.

## <a name="verify-senders-before-removing-them-from-the-blocked-senders-list"></a>Engellenen gönderenler listesinden kaldırmadan önce gönderenleri doğrulama

Gönderenlerin engellenen gönderenler listesine yer eklemesi için iyi nedenler vardır, ancak hatalar olabilir. Engellenen gönderenler velistelerin dengeli bir açıklaması için bu videoya bakın.
<p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMhvD]

## <a name="to-use-delist-portal-to-remove-yourself-from-the-blocked-senders-list-after-errors-like-57511-access-denied"></a>Liste portalını kullanarak kendinizi engellenen gönderenler listesinden kaldırmak için (5.7.511 Erişimi reddedildi gibi hatalardan sonra)

1. Web tarayıcısında, ' gidin <https://sender.office.com>.

2. Sayfa yönergelerini izleyin. Hata iletisinin gönderildiği e-posta adresini ve hata iletisinde belirtilen IP adresini kullanmaya emin olun. Her ziyaret için yalnızca bir e-posta adresi ve bir IP adresi girebilirsiniz.

3. **Gönder'e tıklayın**.

    Portal, sağlarken kaynak e-posta adresine bir e-posta gönderir. E-posta aşağıdakine benzer şekilde olur:

    ![Liste portalı aracılığıyla bir istek gönderdiğinizde alınan e-postanın ekran görüntüsü.](../../media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png)

4. Liste portalı tarafından size gönderilen e-postada onay bağlantısına tıklayın.

    Bu siziliste portalına geri getirir.

5. Liste portalında **IP'yi Listele'ye tıklayın**.

    IP adresi engellenen gönderenler listesinden kaldırıldıktan sonra, bu IP adresine gelen e-posta iletileri Gönderen listesinden kullanan alıcılara Microsoft 365. Bu nedenle, bu IP adresi üzerinden gönderilen e-postanın kötü amaçlı veya kötü amaçlı olmayacak olduğundan emin olun; aksi takdirde IP adresi yeniden engellenmiş olabilir.

    > [!NOTE]
    > Kısıtlamaların kaldırılması için 24 saat kadar sürebilir veya sonuçlar çok fazla değişiklik gösterebilir.

[IP'nin engellenmiş olarak korunmasını önlemek için bkz. EOP'de](create-safe-sender-lists-in-office-365.md) güvenilir gönderen listeleri ve [EOP'de](outbound-spam-controls.md) Giden istenmeyen posta koruması oluşturma.

### <a name="how-do-fix-error-code-57511"></a>Hata kodu 5.7.511'i düzeltme

Kendi gönderdiniz e-posta iletisi teslimi konusunda sorun olduğunda, Microsoft 365 veya Office 365 size bir e-posta gönderir. Size gelen e-posta, DSN veya geri dönen ileti olarak da bilinen bir teslim durumu bildirimidir. En yaygın türe teslim edil raporu (NDR) denir ve bu rapor size bir iletinin teslim edile olmadığını söyler. Bazı durumlarda, Microsoft'un IP'niz üzerinden gelen trafik üzerinde ek soruşturmalar yürütmesi gerekir ve NDR kodu 5.7.511'i alıyorsanız,list portalını kullanasınız.

> 550 5.7.511 Erişim reddedildi, yasaklanmış gönderen[xxx.xxx.xxx.xxx]. Bu listeden kaldırma isteğide etmek için, bu iletiyi destek delist@messaging.microsoft.com. Daha fazla bilgi için , gidin <https://go.microsoft.com/fwlink/?LinkId=526653>.

Bu listeden kaldırma isteğinde ekleyebilirsiniz e-postada, tam NDR kodunu ve IP adresini girin. Microsoft, sonraki adımlarla birlikte 48 saat içinde size başvuracak.

## <a name="more-information"></a>Daha fazla bilgi

**Outlook.com için delisting** formu, tüketici hizmeti burada [bulunabilir](https://support.microsoft.com/supportrequestform/8ad563e3-288e-2a61-8122-3ba03d6b8d75). Gönderi yönü için önce [SSS](https://sendersupport.olc.protection.outlook.com/pm/troubleshooting.aspx) bölümünü _okuduğundan emin_ olun.
