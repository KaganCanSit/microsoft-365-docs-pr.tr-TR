---
title: Kullanıcı ve kullanım Microsoft 365 etkin kullanıcı
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 093a6d0d-890b-489e-9f46-b15687d3fe4f
description: Kullanım analizi, etkinlik raporları ve benimseme Microsoft 365 hakkında bilgi edinin.
ms.openlocfilehash: 748bd08e08cc5e8243c3733c4b3f8448e15ab050
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "62973895"
---
# <a name="active-user-in-microsoft-365-usage-reports"></a>Kullanıcı ve kullanım Microsoft 365 etkin kullanıcı

## <a name="active-user-in-usage-reports"></a>Kullanım raporlarında etkin kullanıcı

Genel kullanım Microsoft 365 için Microsoft 365 [ürünlerinin](usage-analytics.md) etkin bir kullanıcısı ve yönetim merkezinde [Etkinlik Raporları aşağıdaki](../activity-reports/activity-reports.md) gibi tanımlanır. 
  
|**Ürün**|**Etkin kullanıcı tanımı**|**Notlar**|
|:-----|:-----|:-----|
|Exchange Online  <br/> |Aşağıdaki eylemlerden herhangi birini gerçekleştiren tüm kullanıcılar: Okundu olarak işaretle, ileti gönder, randevu oluştur, toplantı isteği gönder, toplantı isteklerini kabul et (belirsiz olarak) veya reddeder, toplantıları iptal eder.  <br/> |Takvim bilgileri temsil edilmemektedir; bu özellik yakında çıkacak bir güncelleştirmeyle eklenecektir.  <br/> |
|SharePoint Online  <br/> |Oluşturma, değiştirme, görüntüleme, silme, şirket içinde veya dışında paylaşma ya da herhangi bir sitedeki istemcilerle eşitleme yoluyla dosya etkileşimi gerçekleştirmiş veya herhangi bir sitede bir sayfayı görüntülemiş tüm kullanıcılar.  <br/> |SharePoint Online şablon uygulamasındaki SharePoint Online için etkin kullanıcı ölçümleri Microsoft 365 yalnızca bir SharePoint Ekip sitesine veya Grup sitesine yönelik olarak etkinlik yapan kullanıcıları yansıtır. Şablon uygulaması, tanımın yönetim merkezinde kullanım raporlarıyla aynı olacak şekilde eşitlenmesi için güncelleştirilecek.  <br/> |
|OneDrive İş  <br/> |Oluşturma, değiştirme, görüntüleme, silme, şirket içinde veya dışında paylaşma ya da istemcilerle eşitleme yoluyla dosya etkileşimi gerçekleştirmiş tüm kullanıcılar.  <br/> ||
|Yammer  <br/> |Yammer'da ileti okuyan, gönderen veya beğenen tüm kullanıcılar.  <br/> ||
|Skype Kurumsal  <br/> |Eşler arası bir oturuma (anlık mesajlaşma, sesli ve görüntülü aramalar, uygulama paylaşımı ve dosya aktarımları dahil) katılmış ya da bir konferans düzenlemiş veya konferansa katılmış tüm kullanıcılar.  <br/> ||
|Office  <br/> |Microsoft 365 Pro Plus, Visio Pro veya Project Pro aboneliğini en az bir cihazda etkinleştiren tüm kullanıcılar.  <br/> ||
|Microsoft 365 Grupları  <br/> |Posta kutusu etkinliği olan tüm grup üyeleri (gruba bir ileti gönderilmişse)  <br/> |Bu tanım, grup sitesi dosya etkinliği ve grup etkinliğiyle Yammer (grup sitesinde dosya etkinliği ve grupla ilişkili Yammer ileti ile geliştirilmiştir.) Bu veriler şu anda Microsoft 365 Usage Analytics şablon uygulamasında kullanılamaz  <br/> |
|Microsoft Teams  <br/> |Sohbet iletilerine, özel sohbet iletilerine, aramalara, toplantılara veya diğer etkinliklere katılan tüm kullanıcılar. Diğer etkinlikler, şunlardan bazıları dahil olmak ve bunlarla sınırlı değildir: iletileri beğenme, uygulamalar, dosyalar üzerinde çalışma, arama, ekipleri takip eden ve kanalı takip eden ve favorilere ekleyen diğer ekip etkinliklerinin sayısı olarak tanımlanır.  <br/> ||
   
## <a name="adoption-metrics"></a>Benimseme Ölçümleri

[Microsoft 365 analitiği,](usage-analytics.md) ürünlerin zaman içinde benimsenmesiyle ilgili etkin kullanıcılarla ilgili daha fazla benimseme ölçümü içerir. Bu ölçümler ay, yıl ve ürün için geçerlidir ve aşağıdaki gibi tanımlanır. 
  
|**Metrik**|**Açıklama**|
|:-----|:-----|
|EnabledUsers  <br/> |Ürünü ay içinde kullanmak için etkinleştirilmiş kullanıcı sayısı.  <br/> |
|ActiveUsers  <br/> |Ay içinde etkin olan kullanıcı sayısı.  <br/> |
|MoMReturningUsers  <br/> |Ay içinde etkin olan ve önceki ay da etkin olan kullanıcı sayısı.  <br/> |
|FirstTimeUsers  <br/> |Ay içinde hizmeti daha önce hiç kullanılmadan etkin olan kullanıcı sayısı.  <br/> |
|CumulativeActiveUsers  <br/> |Ay ile bir önceki ay içinde etkin olan kullanıcı sayısı.  <br/> |
|ActiveUsers(%)  <br/> |Ayda etkin olan en yakın onuncu değere yuvarlanan kullanıcıların yüzdesi, o ay etkinleştirilen kullanıcı sayısına göre.  <br/> |
|MoMReturningUsers(%)  <br/> |Bir önceki ay da etkin olan ayın en yakın onuncu değerine yuvarlanan kullanıcıların sayısı, etkin kullanıcı sayısına göre daha etkin olur.  <br/> |
   
MoMReturningUsers, FirstTimeUsers, &amp; CumulativeActiveUsers sıfırlandı ve 1 Ocak 2018'den başlayarak kullanıcı Microsoft Teams.
  
