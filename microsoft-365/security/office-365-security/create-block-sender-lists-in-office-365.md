---
title: Engellenen gönderen listeleri oluşturma
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150s
description: Yöneticiler, EOP'de (EOP) gelen iletileri engellemek için kullanılabilen ve tercih Exchange Online Protection bilgi edinebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 71f6312f160a445c184a52f96493360af8b9a360
ms.sourcegitcommit: 9f0e84835121ce6228fdc69182c24be7ad1cb20e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015464"
---
# <a name="create-blocked-sender-lists-in-eop"></a>EOP'de engellenen gönderen listeleri oluşturma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

EOP Microsoft 365 posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutusu Exchange Online kuruluşlarda, EOP istenmeyen gönderenlerden gelen e-postaları engellemek için çeşitli yollar sunar. Bu seçenekler Outlook Engellenen Gönderenler, istenmeyen posta önleme ilkelerinde engellenen gönderenler listeleri veya engellenen etki alanı listelerini, Exchange akış kurallarını (aktarım kuralları olarak da bilinir) ve IP Engelleme Listesini (bağlantı filtreleme) içerir. Toplu olarak, bu seçenekleri engellenen gönderen listeleri _olarak düşünebilirsiniz_.

Gönderenleri engellemenin en iyi yöntemi etki kapsamına göre değişir. Tek bir kullanıcı için, doğru çözüm Engellenen Outlook olabilir. Birçok kullanıcı için, diğer seçeneklerden biri daha uygun olacaktır. Aşağıdaki seçenekler hem etki kapsamına hem de ekmek seçeneğine göre sıralandı. Liste dar görüşten genişe doğru ilerler, _ancak tam öneriler_ için özel bilgileri okuyun.

1. Outlook Gönderenler listesi (her posta kutusunda depolanan Engellenen Gönderenler listesi)

2. Engellenen gönderenler listeleri veya engellenen etki alanı listeleri (istenmeyen posta önleme ilkeleri)

3. Posta akış kuralları

4. IP Engelleme Listesi (bağlantı filtreleme)

> [!NOTE]
> Kuruluş genelinde hatalı negatif sonuçları (istenmeyen posta yanıtsız) ele alırken, bu iletileri çözümleme için Microsoft'a da göndermeniz gerekir. Engelleme listelerini kullanarak hatalı negatifleri yönetmek, yönetim yükünü önemli ölçüde artırır. Cevapsız istenmeyen postaları engellemek için engelleme listelerini kullanırsanız İletileri ve dosyaları Microsoft'a bildirme [konusunu](report-junk-email-messages-to-microsoft.md) hazır tutmanız gerekir.

Buna karşılık, güvenilir gönderen listelerini kullanarak belirli kaynaklardan gelen e-postalara her zaman izin vermek için çeşitli _seçenekleriniz vardır_. Daha fazla bilgi için bkz [. Güvenilir gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md).

## <a name="email-message-basics"></a>E-posta iletisiyle ilgili temel bilgiler

Standart SMTP e-posta iletisi, ileti _zarfı ve ileti_ içeriğilerinden oluşur. İleti zarfı, iletiyi SMTP sunucuları arasında ileterek teslim etmek için gereken bilgileri içerir. İleti içeriği, ileti üst bilgisi alanlarını (toplu olarak _ileti üst bilgisi_ denir) ve ileti gövdeyi içerir. İleti zarfı RFC 5321'de ve ileti üst bilgisi de RFC 5322'de açıklanmıştır. alıcılar hiçbir zaman gerçek ileti zarfını görmez, çünkü ileti iletim süreci tarafından oluşturulur ve aslında iletinin bir parçası değildir.

- Adres `5321.MailFrom` (MAIL **FROM** adresi, P1 göndereni veya zarf gönderen olarak da bilinir), iletinin SMTP iletiminde kullanılan e-posta adresidir. Bu **e-posta** adresi normalde ileti üst bilgisinde Dönüş Yolu üst bilgi alanına kaydedilir (ancak gönderen farklı bir **Dönüş Yolu e-posta** adresi ataması mümkündür). İleti teslim edilene kadar teslim edileme raporunun (NDR veya geri dönen ileti olarak da bilinir) alıcısı olur.

- Gönderen `5322.From` adresi veya P2 göndereni olarak da bilinir), Gönderen üst bilgisi alanında yer alan e-posta adresidir ve e-posta istemcisinde görüntülenen gönderenin e-posta adresidir. 

Genellikle, adresler `5321.MailFrom` `5322.From` ve adresler aynıdır (kişiler arasında iletişim). Bununla birlikte, başka biri adına e-posta gönderi olduğunda, adresler farklı olabilir.

EOP'de istenmeyen posta önleme ilkelerinde engellenen gönderenler listeleri ve engellenen etki alanı listeleri hem adresleri hem de adresleri `5321.MailFrom` `5322.From` inceler. Outlook Gönderenler yalnızca adresi `5322.From` kullanır.

## <a name="use-outlook-blocked-senders"></a>Engellenen Outlook'i kullanma

Yalnızca az sayıda kullanıcı istenmeyen e-posta aldıklarında, kullanıcılar veya yöneticiler posta kutusunda gönderenin e-posta adreslerini Engellenen Gönderenler listesine ekleyebilir. Yönergeler için bkz. [Posta kutularına gereksiz e-Exchange Online yapılandırma](configure-junk-email-settings-on-exo-mailboxes.md).

Bir kullanıcının Engellenen Gönderenler listesi nedeniyle iletiler başarıyla engel olduğunda, **X-Forefront-Antispam-Report** üst bilgi alanı değeri içerir `SFV:BLK`.

> [!NOTE]
> İstenmeyen iletiler saygın ve tanınan bir kaynaktan gelen bültenlerse, kullanıcının iletileri almalarını durdurmanın bir diğer seçeneği de e-postadan abonelikten çıkmaktır.

## <a name="use-blocked-sender-lists-or-blocked-domain-lists"></a>Engellenen gönderenler listelerini veya engellenen etki alanı listelerini kullanma

Birden çok kullanıcı etki durumdayken kapsam daha geniştir, bu nedenle bir sonraki en iyi seçenek istenmeyen posta önleme ilkelerinde engellenen gönderen listeleri veya engellenen etki alanı listeleridir. Listelerde yer alan gönderenlerden gelen iletiler İstenmeyen **Posta olarak işaretlenir** (Yüksek güveni olmayan istenmeyen posta **değil) ve** İstenmeyen  posta filtresi kararı için yapılandırmış olduğunuz eylem iletiye alınır. Daha fazla bilgi için bkz [. İstenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

Bu listeler için en yüksek sınır yaklaşık 1000 girdidir.

## <a name="use-mail-flow-rules"></a>Posta akış kurallarını kullanma

Belirli kullanıcılara veya kuruluşun tamamına gönderilen iletileri engellemeniz gerekirse, posta akışı kurallarını kullanabilirsiniz. Posta akış kuralları, istenmeyen iletilerde anahtar sözcükleri veya diğer özellikleri de arama yapabilecekleri için, engellenen gönderen listelerine veya engellenen gönderen etki alanı listelerine göre daha esnektir.

İletileri tanımlamak için hangi koşulları veya özel durumları kullanırsanız kullanın, eylemi iletinin istenmeyen posta güven düzeyi (SCL) 9 olarak (SCL) ayarlanacak şekilde yapılandırmış ve bu da iletiyi Yüksek güven düzeyinde istenmeyen posta olarak **işaretler.** Daha fazla bilgi için bkz [. İletilerde SCL'i ayarlamak için posta akışı kurallarını kullanma](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

> [!IMPORTANT]
> Aşırı agresif kurallar oluşturmak kolaydır, dolayısıyla yalnızca engellemek  istediğiniz iletileri, çok özel ölçütler kullanarak tanımlamanız önemlidir. Ayrıca, her şeyin beklendiği gibi olduğundan emin olmak için kuralda denetimi etkinleştirmeyi ve kuralın sonuçlarını sınayın.

## <a name="use-the-ip-block-list"></a>IP Engelleme Listesini kullanma

Göndereni engellemek için diğer seçeneklerden birini kullanmak mümkün değilken _, yalnızca_ bağlantı filtresi ilkesinde IP Engelleme Listesi'ne sahipseniz kullanın. Daha fazla bilgi için bkz [. Bağlantı filtresi ilkesi yapılandırma](configure-the-connection-filter-policy.md). Engellenen IP'lerin sayısını en az düzeyde tutmanız önemlidir, bu nedenle IP adresi aralıklarının tamamının _engellenmesi_ önerilmez.

Özellikle _tüketici_ hizmetleriyle (örneğin, outlook.com) veya paylaşılan altyapılara ait IP adresi aralıklarını eklemekten kaçınmalı ve ayrıca düzenli bakım kapsamında engellenen IP adresleri listesini gözden geçirmeyi sağ özellikle belirtebilirsiniz.
