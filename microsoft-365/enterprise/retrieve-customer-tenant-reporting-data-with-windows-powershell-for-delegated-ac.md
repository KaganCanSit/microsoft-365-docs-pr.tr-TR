---
title: DAP iş ortakları için müşteri Windows PowerShell raporlama verilerini alma
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 'Özet: Raporları tek Windows PowerShell kiracılarından Microsoft Exchange Online için uzak depolamayı kullanın.'
ms.openlocfilehash: cc9046ab5c90dcb40cbf012772fd80b56f71ec79
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983833"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Temsilcili Erişim İzinleri (DAP) Windows PowerShell iş ortaklarıyla müşteri kiracı raporlama verilerini alma

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Tek tek müşteri Windows PowerShell rapor Microsoft Exchange Online için uzaktan bağlantı kullanın.

Dağıtım ve dağıtım Bulut Çözümü Sağlayıcısı (CSP) iş ortakları, Exchange Online PowerShell için uzaktan dağıtım ve dağıtım Windows PowerShell kullanarak müşteri kiracı raporlarını hazır Exchange Online. Bu, iş ortaklarının raporlama verilerini toplamalarını ve kaydetmelerini ve daha sonra bu veriler üzerinde başka işlemler gerçekleştirmelerini sağlar. Uzak bağlantıyı açtıktan sonra, müşteri kiralanması hakkında raporlama verileri almak, müşteri kiralanmasında herhangi bir cmdlet'i çalıştırmayla aynıdır.

Bu makalede, tek bir müşteri kira Windows PowerShell rapor Exchange Online için uzak depolama hizmetini kullanır ve raporu alırsiniz. Varsayılan olarak Windows PowerShell, birden çok müşteri verilerinden raporlama verilerini toplamayı desteklemez. Bu yordamla birlikte size verilen raporlar yalnızca  _bağlanan DelegatedOrg_ içindir.

## <a name="before-you-begin"></a>Başlamadan önce

- Uzaktan erişim izinlerini kullanarak Exchange Online kiracınıza bağlanmanız Windows PowerShell. Yönergeler için bkz. [Bağlan Erişim Exchange Online (DAP) iş ortakları için uzak Windows PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) sahip kiracıları yönetme.

## <a name="run-the-get-stalemailboxreport-sample"></a>Örnek Get-StaleMailboxReport çalıştırın

Exchange Online'ta uzak oturumu açtıktan sonra, bu komutu çalıştırarak 25/03/03-2015 ile 31/03/2015 tarih aralığı için **Get-StaleMailboxReport'ü** alın.

```powershell
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

Kullanabileceğiniz ileti izleme için Exchange Online, Lync Online ve SharePoint Online'ın yanı sıra diğer birçok raporlama cmdlet'i de kullanılabilir. Kullanılabilir raporlama cmdlet'leri ve Raporlama web Office 365 daha fazla bilgi için, aşağıdaki bölümde yer alan konulara bakın.

## <a name="see-also"></a>Ayrıca bkz.

[Office 365 Raporlama web hizmeti](/previous-versions/office/developer/o365-enterprise-developers/jj984325(v=office.15))

[Exchange Online'ta raporlama cmdlet'leri](/powershell/module/exchange/get-csclientdevicedetailreport)

[İş ortakları için yardım](https://go.microsoft.com/fwlink/p/?LinkID=533477)
