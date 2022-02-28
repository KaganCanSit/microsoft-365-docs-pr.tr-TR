---
title: Microsoft 365 Merkezinde Rapor Raporları - SharePoint kullanımını sağlar
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Kullanıcıların SharePoint kaç dosya depola olduğunu, kaç kullanıcının etkin olarak SharePoint ve kullanılan toplam depolama alanını bilmek için en iyi site kullanım raporunu elde edin.
ms.openlocfilehash: 2c29234df1076fa31ea836b7ead51234e121004e
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989896"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-site-usage"></a>Microsoft 365 Merkezinde Rapor Raporları - SharePoint kullanımını sağlar

Bir Microsoft 365 yöneticisi olarak, Raporlar panosu, kurum çeşitli ürünlerin etkinliğine bir genel bakış gösterir. Bu pano size, her ürüne özgü etkinlikler hakkında daha ayrıntılı bilgi edinmek için detaya gitme olanağı tanır. Örneğin, kullanıcıların SharePoint sitelerinde depolayanın toplam dosya sayısı, etkin olarak kullanılan dosya sayısı ve tüm bu sitelerde kullanılan depolama bilgileri açısından SharePoint'tan elde etmiş olunan değerin üst düzey bir görünümünü elde edin. Daha sonra, tüm siteler için eğilimleri ve site düzeyinde ayrıntıları anlamak için SharePoint site kullanım raporunda detaya gidebilirsiniz. 

## <a name="how-to-get-to-the-sharepoint-site-usage-report"></a>SharePoint sitesi kullanım raporunu alma

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin. 
2. Pano giriş sayfasında, pano kartında **Daha fazla** görüntüle SharePoint tıklayın.

## <a name="show-user-details-in-the-reports"></a>Raporlarda kullanıcı ayrıntılarını gösterme

Raporlar, kurum kurum kullanım verileri hakkında bilgi sağlar. Varsayılan olarak, raporlar kullanıcılar, gruplar ve siteler için tanımlayıcı adlar içeren bilgiler görüntüler. 1 Eylül 2021'den başlayarak, şirketlerin yerel gizlilik yasalarını desteklemelerine yardımcı olmak için devam eden taahhüdlerimizin bir parçası olarak tüm raporlar için kullanıcı bilgilerini varsayılan olarak gizleriz.
  
Kullanıcı listeniz şöyle görünür:
  
![Raporlar - anonimleştirilmiş kullanıcı listesi.](../../media/2ed99bce-4978-4ee3-9ea2-4a8db26eef02.png)
  
Genel yöneticiler bu değişikliği kiracıları için geri döndürebilir ve kuruluşlarının gizlilik uygulamaları buna izin verdiyse tanımlanabilecek kullanıcı bilgilerini gösterebilir. Aşağıdaki adımları kullanarak Microsoft 365 yönetim merkezi sağ edilebilir:
  
1. Yönetim merkezinde Kuruluş Yönetim Merkezi **Ayarlar** \> **Hizmetler Ayarlar** \> **gidin.**

2. **Raporlar**'ı seçin. 
  
3. Tüm raporlarda **ifadenin işaretini kaldırın, kullanıcılar,** gruplar ve siteler için tanımlanmamış adları görüntüler ve sonra değişikliklerinizi kaydedin. 
  
## <a name="interpret-the-sharepoint-site-usage-report"></a>Site SharePoint raporunu yorumlama

Site kullanımı sekmesini seçerek SharePoint raporunda **site kullanımını görüntüleyebilirsiniz**.

:::image type="content" alt-text="Microsoft 365- Microsoft SharePoint kullanımı raporu." source="../../media/d1cb6200-e81c-460b-9d05-53f4bd7cf5ee.png" lightbox="../../media/d1cb6200-e81c-460b-9d05-53f4bd7cf5ee.png":::

Raporda **sütun eklemek** veya kaldırmak için Sütunları seç'i seçin.

:::image type="content" alt-text="SharePoint kullanımı raporu - Sütunları seçin." source="../../media/71ac3195-c494-40c1-9346-a858125ef6df.png":::

Ayrıca, Dışarı Aktar bağlantısını seçerek Excel .csv verilerini bir Excel .csv dosyasına **aktarabilirsiniz**. Bu işlem tüm kullanıcıların verilerini dışarı aktarır ve daha fazla çözümleme yapmak için basit sıralama ve filtreleme işlemlerini kullanmanıza olanak tanır. 2000'den az kullanıcınız varsa, raporun kendi içindeki tabloda sıralama ve filtreleme yapabilirsiniz. 2000'den çok kullanıcınız varsa, filtrelemek ve sıralamak için verileri dışarı aktarmanız gerekir. 

En **SharePoint kullanımı** raporu, son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilirsiniz. Ancak rapordaki belirli bir günü seçersiniz, tablo geçerli tarihten (raporun oluşturulma tarihine değil) itibaren 28 güne kadar olan verileri gösterir.
  
|Metrik|Açıklama|
|:-----|:-----|
|Site URL'si  |Sitenin tam URL'si. |
|Silindi  |Sitenin silinme durumu. Sitelerin silinmiş olarak işaretlenmesi en az 7 gün sürer.  |
|Site sahibi  |Sitenin birincil sahibinin kullanıcı adı.   |
|Site sahibi asıl adı  |Site sahibinin e-posta adresi. |
|Son etkinlik tarihi (UTC)  | Sitede en son dosya etkinliğinin algılandığında veya bir sayfanın görüntü bitiş tarihi.  |
|Site duyarlılık etiket kimliği  | Sitenin duyarlılık etiketi.  |
|Dış paylaşım  | Sitenin dış paylaşılabilir ayarları.  |
|Unmanaged device policy  | Unmanaged devices için site erişim ilkesi.  |
|Coğrafi konum  | Sitenin coğrafi konumu.  |
|Dosyalar  |Site'nin dosya sayısı. |
|Etkin dosyalar  | Site'nin etkin dosyalarının sayısı.<br/> NOT: Rapor için belirtilen dönem içinde dosya kaldırıldısa, raporda gösterilen etkin dosyaların sayısı sitenin geçerli dosya sayısından büyük olabilir.  |
|Depolama kullanılan alan (MB)  |Şu anda sitede kullanılan depolama miktarı.  |
|Depolama (MB)  |Site için ayrılan depolama alanı üst miktarı.  |
|Sayfa görünümleri  |Sayfaların sitede kaç kez görüntülendiklerinin sayısı.  |
|Ziyaret edilen sayfalar  |Sitede ziyaret edilen benzersiz sayfaların sayısı.  |
|Anonim bağlantı sayısı  |Belge veya klasörlerin sitede "Bağlantısı olan herkes" kullanılarak paylaşılma sayısı.  |
|Şirket bağlantı sayısı  |Belge veya klasörlerin sitede "Kuruluşta bağlantısı olan kişiler" kullanılarak paylaşılma sayısı.  |
|Konuk sayısı için güvenli bağlantı  |Belge veya klasörlerin sitede "belirli kişiler" kullanılarak paylaşılma sayısı.  |
|Üye sayısı için güvenli bağlantı  |Belge veya klasörlerin sitede "belirli kişiler" kullanılarak paylaşılma sayısı.  |
|Kök Web Şablonu  |Siteyi oluşturmak için kullanılan şablon.  <br/> NOT: Verileri farklı site türlerine göre filtrelemek için, verileri dışarı aktarın ve Kök Web Şablonu sütununu kullanın. |

