---
title: Posta kutularında Exchange Online içerik
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Buluttaki bulut tabanlı uygulamalar tarafından üretilen Microsoft 365, bir kullanıcının kendi posta kutusuyla depolanır Exchange Online ilişkilendirilz. Bu içerikte, Microsoft eBulma araçları kullanılarak arama kullanılabilir.
ms.openlocfilehash: f7db327d21928df925bfd6451226ab96782d715b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986484"
---
# <a name="content-stored-in-exchange-online-mailboxes-for-ediscovery"></a>eBulma için Exchange Online kutularında depolanan içerik

E-posta Exchange Online posta kutusu öncelikle iletiler, takvim öğeleri, görevler ve notlar gibi e-postayla ilgili öğeleri depolamak için kullanılır. Ancak daha fazla bulut tabanlı uygulama da verilerini kullanıcının posta kutusunda depolayana kadar değişir. Verileri bir posta kutusunda depolamanın bir avantajı, bu bulut tabanlı uygulamalardan verileri bulmak, görüntülemek ve dışarı aktarmak için içerik arama, Core eKbulma ve Advanced eDiscovery'daki arama araçlarını kullan biliyor olmaktır. Bu uygulamalardan bazılarına gelen veriler, posta kutusunun kişiler arası olmayan (IPM olmayan) alt ağaçlarında bulunan gizli klasörlerde depolanır. Diğer bulut tabanlı uygulamalardan veriler posta kutusunda depolanmaz,  ancak posta kutusuyla ilişkilendirilmiştir ve aramalarda döndürülür (bu veriler arama sorgusuyla eşlerise). Bulut tabanlı verilerin bir kullanıcı posta kutusunda depolanmış veya kullanıcı posta kutusuyla ilişkilendirilmiş olup olmadığı bakılmaksızın, kullanıcı posta kutusunu açtığında veriler normalde e-posta istemcisinde görünmez.

Aşağıdaki tabloda, verileri bulut tabanlı bir posta kutusuyla depoleyen veya ilişkilendiren uygulamalar listeledir. Tabloda ayrıca, her uygulamanın ürettiği içerik türü de açık almaktadır.

<br>

****

|Microsoft 365 uygulaması|Açıklama|
|---|---|
|Formlar<sup>*</sup>|Formlar ve forma verilen yanıtlar, e-posta iletilerine ekli olan ve formu oluşturan kullanıcının posta kutusunda gizli bir klasörde depolanan dosyalarda depolanır. Nisan 2020'den önce oluşturulan formlar PDF dosyası olarak depolanır. 2020'den sonra oluşturulan formlar JSON dosyası olarak depolanır. Forma verilen yanıtlar bir CSV dosyasında depolanır. Bir PST dosyasındaki Forms'dan içerik aktarıyorsanız, bu veriler **ApplicationDataRoot** klasöründe, aşağıdaki genel benzersiz tanımlanan (GUID) adlı bir alt klasörde yer almaktadır: **c9a559d2-7aab-4f13-a6ed-e7e9c52aec87**.|
|Microsoft 365 Grupları|E-posta iletileri, takvim öğeleri, kişiler (Kişiler), notlar ve görevler bir Grupla ilişkilendirilmiş posta Microsoft 365 depolanır.|
|Outlook/Exchange Online|E-posta iletileri, takvim öğeleri, kişiler (Kişiler), notlar ve görevler kullanıcının posta kutusunda depolanır.|
|Kişiler|Kişiler uygulamasındaki kişiler (bu kişiler Outlook'da erişilebilenler ile aynı kişiler) kullanıcının posta kutusunda depolanır.|
|Ders Programı|Sınıf Zamanlama'da oluşturulan planlar, yeni bir plan oluşturulduğunda Microsoft 365 Ilgili Grup Grubunun posta kutusunda depolanır. Grup posta kutusunun diğer adı, planın adıdır.|
|Skype Kurumsal|Yeni Skype Kurumsal konuşmalar, kullanıcının posta kutusunun Konuşma Geçmişi klasöründe depolanır. Bir toplantı katılımcısı olan bir Skype posta kutusu Mahkeme Tutma'ya yerleştirilirse veya bir bekletme ilkesine atanmışsa, toplantıya ekli dosyalar katılımcılar posta kutusunda korunur.|
|Sway<sup>*</sup>|Sway, e-posta iletisine eklenmiş bir HTML dosyası olarak depolanır ve sway'i oluşturan kullanıcının posta kutusunda gizli bir klasörde depolanır. Sway'den bir PST dosyasına içerik aktarıyorsanız, bu veriler **ApplicationDataRoot** klasöründe, şu GUID ile adlandırılmış bir alt klasörde yer alır: **905fcf26-4eb7-48a0-9ff0-8dcc7194b5ba**.|
|Görevler|Görevler uygulamasındaki görevler (bu görevler posta kutusunda erişilebilen görevlerle Outlook) kullanıcının posta kutusunda depolanır.|
|Teams|Bir posta kutusunun parçası olan Teams konuşmalar, posta kutunuzla Teams ilişkilendirilz. Teams'ta Sohbet listesinin parçası olan konuşmalar (*1 x N* sohbetler olarak da adlandırılan) sohbete katılan kullanıcıların posta kutusuyla ilişkilendirilz. Ayrıca, bir kanalda yapılan toplantılar ve Teams özet bilgileri, toplantıyı veya aramayı arayarak bağlanılan kullanıcıların posta kutularıyla ilişkilendirilz. Bu nedenle, Teams kutusunda kanal konuşmalarında içerik için Teams kutusunda ve kullanıcı posta kutularında 1 x N sohbetlerde içerik için aramanız gerekir.|
|To-Do|To-Do uygulamasındaki görevler (yapılacaklar listesinde kayıtlı olan yapılacaklar görevleri) kullanıcının posta kutusunda depolanır.|
|Yammer|bir Yammer topluluğu içindeki konuşmalar ve yorumlar, hem Microsoft 365 Grubu posta kutusuyla hem de yazarın ve adlandırılmış alıcıların (@ bahsedilen veya Bilgi'ye sahip kullanıcılar) kullanıcı posta kutusuyla ilişkilendirilmiştir. Bir Yammer dışındaki özel iletiler, özel iletiye katılan kullanıcıların posta kutusunda depolanır.|
|

> [!NOTE]
> <sup>*</sup>Şu anda, bir posta kutusuna yerinde tutma yerleştirilirse (Core eDiscovery veya Advanced eDiscovery durumlarda 10 ayrı tutma kullanılarak), bu uygulamanın içeriği yerinde tutma tarafından korunmaz.
