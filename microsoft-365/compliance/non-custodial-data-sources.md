---
title: Özel durum durumuna özel olmayan veri Advanced eDiscovery ekleme
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Bir olayda özel olmayan veri kaynakları ekleyebilir Advanced eDiscovery veri kaynağını yerinde tutabilirsiniz. Özel durumlu olmayan veri kaynakları yeniden dizinlenir, böylece kısmen dizine alındı olarak işaretlenen tüm içerikler, tümüyle ve hızla aranabilir olacak şekilde yeniden işlenir.
ms.openlocfilehash: a4702ebdfbd41b2541c51380a1d44dd133d506c9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987306"
---
# <a name="add-non-custodial-data-sources-to-an-advanced-ediscovery-case"></a>Özel durum durumuna özel olmayan veri Advanced eDiscovery ekleme

Bazı Advanced eDiscovery, bu durum her zaman, bir Microsoft 365 veri kaynağını bir özel dosyayla ilişkilendirmek için size uygun değildir. Ancak yine de bu verileri bir vakayla ilişkilendirmek, böylelikle arama yapmak, gözden geçirme kümesine eklemek, çözümlemek ve gözden geçirmek için bu verileri ilişkilendirmek zorundayabilirsiniz. Özel özellik Advanced eDiscovery özel veri kaynakları olarak adlandırılan bu  özellik, özel veri kaynakları olarak adlandırılan bu özelliği bir özel durumla ilişkilendirmek zorunda kalmadan vakaya veri eklemenize olanak sağlar. Ayrıca, custo Advanced eDiscovery ilişkilendirilen veriler için kullanılabilen, özel veya özel olmayan verilere aynı özellik işlevini de uygular. Özel olmayan verilere uygulayabilecek en yararlı şeylerden ikisi, gelişmiş dizin oluşturma kullanılarak onu tutma ve [işlemeye yerleştirmektir](indexing-custodian-data.md).

## <a name="add-a-non-custodial-data-source"></a>Özel olmayan bir veri kaynağı ekleme

Bir olayda özel olmayan veri kaynaklarını eklemek ve yönetmek için bu Advanced eDiscovery izleyin.

1. Sayfa **Advanced eDiscovery** sayfasında, verileri eklemek istediğiniz vakaya tıklayın.

2. Veri kaynakları **sekmesine tıklayın** ve ardından Veri kaynağı **ekle Veri** >  **konumları ekle'ye tıklayın**.

3. Yeni **özel olmayan veri konumları** uç sayfasında, vakaya eklemek istediğiniz veri kaynaklarını seçin. Birden çok posta kutusu ve site eklemek için, posta kutusu veya **posta SharePoint** **Exchange** sonra da Düzenle'ye **tıklarsiniz**.

   ![Özel SharePoint ekleyin Exchange posta kutularını özel olmayan veri kaynakları olarak ekleyin.](../media/NonCustodialDataSources1.png)

   - **SharePoint**- Site eklemek **için Düzenle'ye** tıklayın. Listeden bir site seçin veya arama çubuğuna sitenin URL'sini yazarak siteyi arayabilirsiniz. Koruyucu olmayan veri kaynakları olarak eklemek istediğiniz siteleri seçin ve Ekle'ye **tıklayın**.

   - **Exchange**- Posta kutuları **eklemek için** Düzenle'ye tıklayın. Posta kutuları veya dağıtım gruplarının arama kutusuna bir ad veya diğer ad (en az üç karakter) yazın. Koruyucu olmayan veri kaynakları olarak eklemek istediğiniz posta kutularını seçin ve Ekle'ye **tıklayın**.

   > [!NOTE]
   > Ekip veya **SharePoint Exchange** site ve posta kutularını özel  olmayan veri kaynakları olarak eklemek için Yammer ve Posta Kutuları bölümlerini kullanabilirsiniz. Bir Ekip veya Ekip grubuyla ilişkilendirilmiş posta kutusunu ve siteyi ayrı Yammer gerekir.<br/><br/> Ayrıca, veri kaynağı olarak kök `https://contoso-my.sharepoint.com/personal/` `https://contoso-my.sharepoint.com/`site URL'sini (SharePoint) ekleme de desteklenmemektedir. Belirli siteleri eklemeniz gerekir.

4. Özel olmayan veri kaynaklarını ekledikten sonra, bu konumları yerinde tutma veya tutmama seçeneğiniz vardır. Veri kaynağını yerinde yerinde **tutmak** için, veri kaynağının yanındaki Yerinde Tut onay kutusunu seçin veya seçimini kaldırın.

5. Veri **kaynaklarını** vakaya eklemek için **, Özel** olmayan yeni veri konumları uç sayfasının altındaki Ekle'ye tıklayın.

   Kendi ekledikleri, özel olmayan her veri kaynağı, Veri kaynakları **sayfasında** listelenir. Özel olmayan veri kaynakları, Kaynak türü **sütunundaki Veri konumu** **değeri tarafından** tanımlanır.

   ![Veri kaynakları sekmesinde özel olmayan veri kaynakları.](../media/NonCustodialDataSources2.png)

Vakaya özel olmayan veri kaynaklarını eklemenizden sonra, olayın İşleri sekmesinde *Reindexing non custodial* data adlı bir iş oluşturulur ve görüntülenir. İş oluşturulduktan sonra, başlatılan gelişmiş dizin oluşturma işlemi ve veri kaynakları yeniden dizine oluşturulur.

## <a name="manage-the-hold-for-non-custodial-data-sources"></a>Özel olmayan veri kaynaklarının  tutulmalarını yönetme

Özel olmayan bir veri kaynağını yerinde tutma sonrasında, olayın özel veya özel olmayan veri kaynaklarını içeren bir tutma ilkesi otomatik olarak oluşturulur. Özel olmayan başka veri kaynaklarını yerinde tutarken, bunlar bu tutma ilkesine eklenir.

1. Büyük/Advanced eDiscovery açın ve Bekle **sekmesini** seçin.

2. **NCDSHold-'\<GUID\>** a tıklayın; burada GUID değeri büyük/harfe özeldir.

   Uçarak giriş sayfası, özel olmayan veri kaynakları hakkında bilgileri ve istatistikleri görüntüler.

   ![Özel olmayan veri kaynaklarının uçarak çıkış sayfası istatistikleri görüntüler.](../media/NonCustodialDataSourcesHoldFlyout.png)

3. Aşağıdaki **yönetim görevlerini** gerçekleştirmek üzere, tek ve özel olmayan veri kaynaklarını görüntülemek için Tutmayı düzenle'ye tıklayın:

   - Konumlar **sayfasında** , özel olmayan veri kaynağını tutmadan kaldırarak serbest leyebilirsiniz. Veri kaynağının serbest bırakılması, özel veri kaynağını bu durumdan kaldırmaz. Yalnızca veri kaynağına yerleştirilen tutmayı kaldırır.

   - Sorgu **sayfasında** , bu durumdaki özel olmayan tüm veri kaynaklarına uygulanan sorgu tabanlı bir tutma oluşturmak için tutmayı düzenleyebilirsiniz.
