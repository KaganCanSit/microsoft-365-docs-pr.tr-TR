---
title: Engellenen gönderenler listesinden ve adres 5.7.511 Erişim reddedildi hatalarından kendinizi kaldırın
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
description: Bu makalede, listeden çıkarma portalını kullanarak kendinizi engellenen Microsoft 365 gönderenler listesinden kaldırmayı öğreneceksiniz. Bu, 5.7.511 Erişim reddedildi hatalarıyla ilgili en iyi yanıttır.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 83822faaf1c667524dd88fc1bba400c10fa30ac3
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647743"
---
# <a name="use-the-delist-portal-to-remove-yourself-from-the-blocked-senders-list-and-address-57511-access-denied-errors"></a>Engellenen gönderenler listesinden ve adres 5.7.511 Erişim reddedildi hatalarından kendinizi kaldırmak için listeden çıkarma portalını kullanın

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

E-posta adresi Microsoft 365 (örneğin ve adres 5.7.511 Erişimi reddedildi) olan bir alıcıya e-posta göndermeye çalıştığınızda bir hata iletisi mi alıyorsunuz? Hata iletisini almamanız gerektiğini düşünüyorsanız, listeden çıkarma portalını kullanarak kendinizi engellenen gönderenler listesinden kaldırabilirsiniz.

## <a name="what-is-the-blocked-senders-list"></a>Engellenen gönderenler listesi nedir?

Microsoft, müşterilerini istenmeyen posta, kimlik sahtekarlığı ve kimlik avı saldırılarına karşı korumak için engellenen gönderenler listesini kullanır. Posta sunucunuzun IP adresi, yani posta sunucunuzun İnternet'te kendisini tanımlamak için kullandığı adres, çeşitli nedenlerden biri nedeniyle Microsoft 365 için olası bir tehdit olarak etiketlendi. Microsoft 365 IP adresini listeye eklediğinde, IP adresi ve veri merkezlerimiz aracılığıyla müşterilerimiz arasında daha fazla iletişim olmasını engeller.

Aşağıdakine benzer bir hata içeren bir posta iletisine yanıt aldığınızda listeye eklendiğinizi anlarsınız:

> 550 5.7.606-649 Erişim reddedildi, IP göndermesi yasaklandı [_IP adresi_] (ör. 5.7.511 Erişim reddedildi: Bu listeden kaldırılmasını istemek için lütfen ziyaret edin <https://sender.office.com/> ve yönergeleri izleyin. Daha fazla bilgi için bkz[. Exchange Online'da teslim edilmedi raporlarını e-postayla gönderme](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

burada  _IP adresi_ , posta sunucusunun çalıştığı bilgisayarın IP adresidir.

## <a name="verify-senders-before-removing-them-from-the-blocked-senders-list"></a>Engellenen gönderenler listesinden kaldırmadan önce gönderenleri doğrulama

Gönderenlerin engellenen gönderenler listesine eklenmek için iyi nedenler vardır, ancak hatalar olabilir. Engellenen gönderenlerin ve listeden çıkarmanın dengeli bir açıklaması için bu videoya göz atın.
<p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMhvD]

## <a name="to-use-delist-portal-to-remove-yourself-from-the-blocked-senders-list-after-errors-like-57511-access-denied"></a>Listeden çıkarma portalını kullanarak engellenen gönderenler listesinden (5.7.511 Erişimi reddedildi gibi hatalardan sonra) kendinizi kaldırmak için

1. Web tarayıcısında adresine <https://sender.office.com>gidin.

2. Sayfadaki yönergeleri izleyin. Hata iletisinin gönderildiği e-posta adresini ve hata iletisinde belirtilen IP adresini kullandığınızdan emin olun. Her ziyarette yalnızca bir e-posta adresi ve bir IP adresi girebilirsiniz.

3. **Gönder'e** tıklayın.

    Portal, sağladığınız e-posta adresine bir e-posta gönderir. E-posta aşağıdakine benzer olacaktır:

    :::image type="content" source="../../media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png" alt-text="Listeden çıkarma portalı aracılığıyla istek gönderdiğinizde alınan e-posta" lightbox="../../media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png":::

4. Listeden çıkarma portalı tarafından size gönderilen e-postada onay bağlantısına tıklayın.

    Bu sizi listeden çıkarma portalına geri getirir.

5. Listeden çıkarma portalında **, LISTEDEN ÇıKAR IP'ye** tıklayın.

    IP adresi engellenen gönderenler listesinden kaldırıldıktan sonra, bu IP adresinden gelen e-posta iletileri Microsoft 365 kullanan alıcılara teslim edilir. Bu nedenle, bu IP adresinden gönderilen e-postaların kötü amaçlı veya kötü amaçlı olmayacağından emin olduğunuzdan emin olun; aksi takdirde, IP adresi yeniden engellenebilir.

    > [!NOTE]
    > Bu işlem 24 saate kadar sürebilir veya kısıtlamalar kaldırılmadan önce sonuçlar büyük ölçüde değişebilir.

Ip'nin engellenmesini önlemek için bkz. [EOP'de güvenilir gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md) ve [EOP'de giden istenmeyen posta koruması](outbound-spam-controls.md) .

### <a name="how-do-fix-error-code-57511"></a>Hata kodu 5.7.511 nasıl düzeltilir?

Gönderdiğiniz bir e-posta iletisini teslim ederken bir sorun olduğunda, Microsoft 365 veya Office 365 size bildirmek için bir e-posta gönderir. Aldığınız e-posta, DSN veya geri dönen ileti olarak da bilinen bir teslim durumu bildirimidir. En yaygın tür, teslim edilmedi raporu (NDR) olarak adlandırılır ve size iletinin teslim edilmemiş olduğunu söyler. Bazı durumlarda, Microsoft IP'nizden gelen trafiğe karşı ek araştırma yapmalıdır ve NDR kodu 5.7.511'i **alıyorsanız** listeden çıkarma portalını kullanamazsınız.

> 550 5.7.511 Erişim reddedildi, gönderen yasaklandı[xxx.xxx.xxx.xxx]. Bu listeden kaldırma isteğinde bulunmak için bu iletiyi delist@messaging.microsoft.com iletin. Daha fazla bilgi için adresine <https://go.microsoft.com/fwlink/?LinkId=526653>gidin.

Bu listeden kaldırma isteğinde bulunmak için e-postada tam NDR kodunu ve IP adresini sağlayın. Microsoft, sonraki adımlarla birlikte 48 saat içinde sizinle iletişime geçecektir.

## <a name="more-information"></a>Daha fazla bilgi

**Outlook.com için listeden çıkarma formu, tüketici hizmeti** [burada](https://support.microsoft.com/supportrequestform/8ad563e3-288e-2a61-8122-3ba03d6b8d75) bulunabilir. _Gönderme_ yönü için önce [SSS](https://sendersupport.olc.protection.outlook.com/pm/troubleshooting.aspx) bölümünü okuduğunuzdan emin olun.
