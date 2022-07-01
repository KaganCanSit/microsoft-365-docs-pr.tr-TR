---
title: Etki alanınızı Microsoft 365'e bağlayın
f1.keywords:
- NOCSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
- admindeeplinkMAC
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Etki alanınızı Microsoft 365'e bağlamayı öğrenin.
ms.openlocfilehash: 2b02687e8d62a40272ffa5dad8ccabec4fbde368
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603894"
---
# <a name="connect-your-domain-to-microsoft-365-for-business"></a>Etki alanınızı İş için Microsoft 365'e bağlama

YouTube'da [Microsoft 365 küçük işletme yardımına](https://go.microsoft.com/fwlink/?linkid=2197659) göz atın.

## <a name="watch-connect-your-domain-to-microsoft-365"></a>izleyin: Etki alanınızı Microsoft 365'e bağlama

[YouTube kanalımızda](https://go.microsoft.com/fwlink/?linkid=2198216) bu videoya ve diğer videolara göz atın.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LFpy?autoplay=false]

Microsoft 365'i ayarladıktan ve e-posta verilerinizi Google Workspace'ten taşıdıktan sonra, etki alanınızı Microsoft 365'e bağlayabilirsiniz. 

İlk olarak Mevcut DNS kayıtlarını Google'dan silmeniz gerekir ve ardından Microsoft 365'ten yeni DNS kayıtları ekleyebiliriz.

1. [admin.google.com'da](https://admin.google.com) Google Workspace yönetici konsolunuzda oturum açın.
1. Sol gezinti bölmesinde **Etki Alanları**, **Etki alanlarını yönet**, **Ayrıntıları görüntüle**, **Etki alanını yönet** ve **ARDıNDAN DNS'yi** seçin.
1. Ekranı aşağı kaydırarak **Sentetik kayıtlar'a** gidin, **Google Workspace'i** açın, **Sil'i** ve sonra yeniden **Sil'i** seçin.
1. Ekranı aşağı kaydırarak **Özel kaynak kayıtları'na** gelin ve daha önce Microsoft 365 için oluşturmuş olabileceğiniz kayıtlar da dahil olmak üzere görüntülenen mevcut DNS kayıtlarını silin.
1. [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) gidin.
1. Sol gezinti bölmesinde Tüm  > **Ayarlar** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Etki Alanlarını**</a> **Göster'i** seçin.
1. Ardından varsayılan etki alanınızı seçin.
1. **Kuruluma devam et'i** ve ardından etki alanınızı bağlamak için **Devam'ı** seçin.
1. Google'a kopyalanması gereken DNS kayıtlarını görüntülemek için aşağı kaydırın.
1. **MX Kayıtları'nı** açın ve **İşaret edilen adres veya değer'in** altında kaydı kopyalayın.
1. Google'a dönün ve **Özel kaynak kayıtları** bölümünde kayıt türü açılan listesini açın ve **MX'i** seçin.
1. **Veri** alanına kopyaladığınız kaydı yapıştırın.
1. Ardından **Ekle'yi** seçin.
1. CNAME ve TXT kayıtları için işlemi yineleyin ve Google DNS yönetim sayfasına değerleri ekleyin.
1. Microsoft 365 yönetim merkezi dönün ve **Devam'ı** seçin.

    Etki alanı kurulumunuz tamamlandı.