---
title: İşletmeler için Office istemci dağıtımına Microsoft 365 hazırlama
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
ms.date: 02/25/2022
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: M365-subscription-management
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ROBOTS: NO INDEX, NO FOLLOW
ms.assetid: ed34fff3-2881-4ed4-9906-1ba6bb8dd804
description: Bilgisayarınıza 32 bit Office uygulamalarını otomatik olarak Windows 10 ve güncel tutma hakkında bilgi edinin.
ms.openlocfilehash: aa14aa9407f7115e31f01a8e20ea1324a23452ec
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63321173"
---
# <a name="prepare-for-office-client-deployment-by-microsoft-365-for-business"></a>İşletmeler için Office istemci dağıtımına Microsoft 365 hazırlama

Bu makale diğer Microsoft 365 İş Ekstra.

> [!NOTE]
> İş için Microsoft Defender 1 Mart 2022 Microsoft 365 İş Ekstra müşterilere sunulmaktadır. Bu teklif, cihazlar için ek güvenlik özellikleri sağlar. [İş için Defender hakkında daha fazla bilgi öğrenin](../../security/defender-business/mdb-overview.md).

## <a name="prepare-to-automatically-install-office-apps-to-client-computers"></a>İstemci bilgisayarlara Office uygulamalarını otomatik olarak yükleme hazırlığı

Microsoft 365 İş Ekstra'i kullanarak bilgisayarınıza 32 bit Office uygulamalarını Windows 10 güncelleştirmelerle bunları güncel tutabilirsiniz.
  
Otomatik yükleme en iyi şekilde, son kullanıcının bilgisayarı bilgisayarda ise en Windows 10 Business ve:
  
- Mevcut Office masaüstü uygulamaları (Word, Excel, PowerPoint, Outlook, OneNote, Publisher, Access ve OneDrive) bulunmamalıdır.
    
    veya
    
- Office'in Tıkla-Çalıştır sürümü yüklü olmalıdır.
    
Office'in Tıkla-Çalıştır sürümüne sahip olup olmadığınızı belirlemek için, herhangi bir Office uygulamasında **Dosya** \> **Hesap**'a (Outlook'ta **Office Hesabı**) gidin. Aşağıdaki şekilde **Office Güncelleştirmeler** görüyorsanız, yükleme Tıkla-Çalıştır kullanılarak gerçekleştirildi. 
  
![Hesap'Office güncelleştirmeleri Office uygulaması ekran görüntüsü.](../../media/e3439380-fa43-4ed6-ae5d-64851c297df5.png)
  
 **Who özelliğin avantajlarından yararlanma**
  
Bilgisayarı aşağıdaki özelliklere sahip olan son kullanıcılar:
  
- **İş** Windows 10 Business lisansına sahip, Microsoft 365 lisansına sahip Windows 10 Creators Update lisansına sahip ve Azure Active Directory. 
    
- 64 **bit** uygulama (örneğin: Word Office, Excel, tamam PowerPoint. 64 bit Office uygulamaları gerekirse, bu özellik uygun değildir çünkü kurumsal yönetim konsolundan Office'ın 64 bit 2016 Tıkla-Çalıştır sürümünü tetikleme desteği Microsoft 365 değildir. 
    
- Herhangi bir 2016 Windows Installer (MSI) tek başına uygulaması (örneğin, Visio veya Project) **yoktur**. Microsoft 365 2016 Office Tıkla-Çalıştır sürümüne yükseltmeler için Office bu, Office 2016 MSI tek başına uygulamalarıyla işe yaramadı. 
    
Aşağıdaki tabloda, son kullanıcıların/yöneticilerin, başlangıç durumlarına bağlı olarak işletmeler için Microsoft 365 yönetim konsolundan Office'un Tıkla-Çalıştır sürümünün başarılı bir şekilde dağıtımını yapmak için hangi eylemi uygulaması gerekten olduğu görüntülenir.<br/>


|Başlangıçtaki Office yükleme durumu|İşletmeler için yüklemeden Microsoft 365 önce Office işlem|Son durum|
|:-----|:-----|:-----|
|Hiçbir Office paketi yüklü değil  <br/> |Yok  <br/> |Office-Çalıştır kullanılarak 2016 32 bit yüklenir  <br/> |
|Office'in Tıkla-Çalıştır 32 bit sürümü (2016 veya önceki) var ve tek başına uygulama yok  <br/> |Yok  <br/> |Gerektiği gibi Office 2016'nın en son 32 bit Tıkla-Çalıştır sürümüne yükseltilir **\*** <br/> |
|Office'in Tıkla-Çalıştır 32 bit sürümü ve Tıkla-Çalıştır 32 bit veya 64 bit tek başına Office uygulamaları (örneğin, Visio, Project)  <br/> |Yok  <br/> |Tek başına uygulamalar etkilenmez. Paket, Office 2016'nın Tıkla-Çalıştır 32 bit sürümüne yükseltilir  <br/> |
|Office'in Tıkla-Çalıştır 32 bit sürümü ve 32 bit veya 64 bit (2016 dışında) MSI tek başına Office uygulamaları var  <br/> |Yok  <br/> |Tek başına uygulamalar etkilenmez. Paket, Office 2016'nın Tıkla-Çalıştır 32 bit sürümüne yükseltilir  <br/> |
|Office'in Tıkla-Çalıştır 64 bit sürümü var  <br/> |64 bit veya Office, 32 bit veya 32 bit uygulamalarla değiştirilmesi sorun Office kaldırma  <br/> |Office 64 bit uygulamaları kaldırılmışsa, Office 2016'nın Tıkla-Çalıştır 32 bit sürümü yüklenir  <br/> |
|Tek başına uygulamalarla veya bu uygulamalar olmadan Office 2016'nın MSI yüklemesi var  <br/> |MSI Office 2016'yı kaldırın.  <br/> |Office 2016'nın Tıkla-Çalıştır 32 bit sürümü yüklenir. Tek başına uygulamalarda hiçbir değişiklik olmaz  <br/> |
|Office 2013'ün (veya önceki sürümlerin) ve/veya tek başına Office uygulamalarının MSI yüklemesi var  <br/> |Yok  <br/> |Office 2016'nın Tıkla-Çalıştır 32 bit sürümü, önceden var olan MSI Office yüklemesiyle (ve tek başına uygulamalarla) birlikte kullanılır  <br/> |
||||
   
 **(\*) Not:** Bilinen bir hata nedeniyle Office 2016'nın Tıkla-Çalıştır 32 bit sürümüne yükseltilmez. Düzeltme için çalışma devam etmektedir. 
  