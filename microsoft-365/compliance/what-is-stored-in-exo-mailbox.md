---
title: Exchange Online posta kutularında depolanan içerik
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: ''
description: Microsoft 365'te bulut tabanlı uygulamalar tarafından üretilen içerik bir kullanıcının Exchange Online posta kutusuyla depolanır veya ilişkilendirilir. Bu içerik Microsoft eBulma araçları kullanılarak aranabilir.
ms.openlocfilehash: a5006721166a2f56d8abae9b79442f4ad93276a4
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641064"
---
# <a name="content-stored-in-exchange-online-mailboxes-for-ediscovery"></a>eBulma için Exchange Online posta kutularında depolanan içerik

Exchange Online'deki posta kutusu öncelikli olarak iletiler, takvim öğeleri, görevler ve notlar gibi e-postayla ilgili öğeleri depolamak için kullanılır. Ancak daha fazla bulut tabanlı uygulama verilerini kullanıcının posta kutusunda depoladıkça bu durum değişir. Verileri posta kutusunda depolamanın avantajlarından biri, bu bulut tabanlı uygulamalardan verileri bulmak, görüntülemek ve dışarı aktarmak için içerik arama, Microsoft Purview eKeşif (Standart) ve Microsoft Purview eKeşif (Premium) arama araçlarını kullanabilmenizdir. Bu uygulamalardan bazılarına ait veriler, posta kutusunda kişiler arası olmayan bir ileti (IPM olmayan) alt ağaçta bulunan gizli klasörlerde depolanır. Diğer bulut tabanlı uygulamalardan gelen veriler posta _kutusunda depolanmayabilir_ , ancak posta _kutusuyla ilişkilendirilir_ ve aramalarda döndürülür (bu veriler arama sorgusuyla eşleşiyorsa). Bulut tabanlı verilerin bir kullanıcı posta kutusunda depolanıp depolanmadığına veya kullanıcı posta kutusuyla ilişkilendirilip ilişkilendirilmediğine bakılmaksızın, kullanıcı posta kutusunu açtığında veriler genellikle e-posta istemcisinde görünmez.

Aşağıdaki tabloda verileri depolayan veya bulut tabanlı bir posta kutusuyla ilişkilendiren uygulamalar listelenir. Tabloda, her uygulamanın ürettiği içerik türü de açıklanır.

<br>

****

|Microsoft 365 uygulaması|Açıklama|
|---|---|
|Forms<sup>*</sup>|Formlar ve bir forma verilen yanıtlar, e-posta iletilerine eklenmiş dosyalarda depolanır ve formu oluşturan kullanıcının posta kutusundaki gizli bir klasörde depolanır. Nisan 2020'de oluşturulan formlar PDF dosyası olarak depolanır. 2020'nin ardından oluşturulan formlar JSON dosyası olarak depolanır. Bir forma verilen yanıtlar CSV dosyasında depolanır. Bir PST dosyasındaki Formlardan içeriği dışarı aktardığınızda, bu veriler **applicationdataroot** klasöründe aşağıdaki genel olarak benzersiz olarak tanımlanan (GUID) adlı bir alt klasörde bulunur: **c9a559d2-7aab-4f13-a6ed-e7e9c52aec87**.|
|Microsoft 365 Grupları|E-posta iletileri, takvim öğeleri, kişiler (Kişiler), notlar ve görevler bir Microsoft 365 grubuyla ilişkili posta kutusunda depolanır.|
|Outlook/Exchange Online|E-posta iletileri, takvim öğeleri, kişiler (Kişiler), notlar ve görevler kullanıcının posta kutusunda depolanır.|
|Insanlar|Kişiler uygulamasındaki kişiler (Outlook'ta erişilebilen kişilerle aynı kişilerdir) kullanıcının posta kutusunda depolanır.|
|Sınıf Zamanlaması|Sınıf Zamanlaması'nda oluşturulan planlar, yeni bir plan oluşturulduğunda sağlanan ilgili Microsoft 365 Grubunun posta kutusunda depolanır. Grup posta kutusunun diğer adı planın adıdır.|
|Skype Kurumsal|Skype Kurumsal konuşmaları kullanıcının posta kutusunda Konuşma Geçmişi klasöründe depolanır. Skype toplantısı katılımcısının posta kutusu Dava Bekletme'ye yerleştirilirse veya bekletme ilkesine atanırsa, toplantıya eklenen dosyalar katılımcıların posta kutusunda tutulur.|
|Sway<sup>*</sup>|Sway tuvalleri, e-posta iletisine eklenmiş bir HTML dosyası olarak depolanır ve sway'i oluşturan kullanıcının posta kutusunda gizli bir klasörde depolanır. PST dosyasındaki Sway içeriği dışarı aktardığınızda, bu veriler **ApplicationDataRoot** klasöründe şu GUID ile adlandırılan bir alt klasörde bulunur: **905fcf26-4eb7-48a0-9ff0-8dcc7194b5ba**.|
|Görevler|Görevler uygulamasındaki görevler (Outlook'ta erişilebilen görevlerle aynı görevlerdir) kullanıcının posta kutusunda depolanır.|
|Teams|Teams kanalının parçası olan konuşmalar Teams posta kutusuyla ilişkilendirilir. Teams'deki Sohbet listesinin bir parçası olan konuşmalar ( *1 x N sohbet olarak* da adlandırılır) sohbete katılan kullanıcıların posta kutusuyla ilişkilendirilir. Ayrıca, Teams kanalındaki toplantılar ve aramalar için özet bilgiler, toplantıya veya aramaya arayarak bağlanan kullanıcıların posta kutularıyla ilişkilendirilir. Bu nedenle, Teams içeriğini ararken Teams posta kutusunda kanal konuşmalarındaki içeriği arar ve kullanıcı posta kutularında 1 x N sohbette içerik ararsınız.|
|To-Do|To-Do uygulamasındaki görevler (yapılacaklar listelerine kaydedilen *yapılacaklar* olarak adlandırılır) kullanıcının posta kutusunda depolanır.|
|Yammer|Yammer topluluğundaki konuşmalar ve açıklamalar, Microsoft 365 Grubu posta kutusunun yanı sıra yazarın ve adlandırılmış alıcıların (@ bahsedilen veya Bilgi'ed kullanıcılar) kullanıcı posta kutusuyla ilişkilendirilir. Yammer topluluğu dışında gönderilen özel iletiler, özel iletiye katılan kullanıcıların posta kutusunda depolanır.|
|

> [!NOTE]
> <sup>*</sup> Şu anda, bir saklama bir posta kutusuna yerleştirilirse (eBulma (Standart) veya eBulma (Premium) durumlarında ayrı tutmalar kullanılarak), bu uygulamadaki içerik ayrı tutma tarafından korunmaz.
