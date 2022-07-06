---
title: Bir eBulma (Premium) olayına gözetimsiz veri kaynakları ekleme
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Bir eBulma (Premium) olayına gözetimsiz veri kaynakları ekleyebilir ve veri kaynağına ayrı tutabilirsiniz. Gözaltı olmayan veri kaynakları yeniden dizinlenir, bu nedenle kısmen dizinlenmiş olarak işaretlenmiş tüm içerikler tamamen ve hızlı bir şekilde aranabilir hale getirmek için yeniden işlenir.
ms.openlocfilehash: bb5ff8a4a58e62d3f4bf36f7c7e1e9001d829036
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625137"
---
# <a name="add-non-custodial-data-sources-to-an-ediscovery-premium-case"></a>Bir eBulma (Premium) olayına gözetimsiz veri kaynakları ekleme

Microsoft Purview eKeşif (Premium) durumlarda, bir Microsoft 365 veri kaynağını bu durumda bir koruyucuyla ilişkilendirme gereksinimlerinizi her zaman karşılamaz. Ancak yine de arama yapmak, bir gözden geçirme kümesine eklemek ve analiz edip gözden geçirmek için bu verileri bir servis talebiyle ilişkilendirmeniz gerekebilir. eBulma (Premium) özelliği *, gözetim dışı veri kaynakları* olarak adlandırılır ve bunu bir koruyucuyla ilişkilendirmek zorunda kalmadan bir servis talebine veri eklemenize olanak tanır. Ayrıca, aynı eBulma (Premium) işlevselliğini, koruyucuyla ilişkili veriler için kullanılabilen gözetimsiz verilere de uygular. Gözaltı olmayan verilere uygulayabileceğiniz en yararlı şeylerden ikisi, bunları bekletmek ve [Gelişmiş dizin oluşturma](indexing-custodian-data.md) kullanarak işlemektir.

## <a name="add-a-non-custodial-data-source"></a>Gözetim altında olmayan bir veri kaynağı ekleme

Bir eBulma (Premium) olayına gözetimsiz veri kaynakları eklemek ve yönetmek için bu adımları izleyin.

1. **eBulma (Premium)** giriş sayfasında, verileri eklemek istediğiniz servis talebine tıklayın.

2. **Veri kaynakları** sekmesine ve ardından **Veri kaynağı** >  ekle **Veri konumları ekle'ye** tıklayın.

3. **Yeni gözetim dışı veri konumları** açılır sayfasında, servis talebine eklemek istediğiniz veri kaynaklarını seçin. **SharePoint** veya **Exchange** bölümlerini genişletip **Düzenle'ye** tıklayarak birden çok posta kutusu ve site ekleyebilirsiniz.

   ![SharePoint sitelerini ve Exchange posta kutularını gözaltı olmayan veri kaynakları olarak ekleyin.](../media/NonCustodialDataSources1.png)

   - **SharePoint** - Site eklemek için **Düzenle'ye** tıklayın. Listeden bir site seçin veya arama çubuğuna sitenin URL'sini yazarak siteyi arayabilirsiniz. Koruyucu olmayan veri kaynakları olarak eklemek istediğiniz siteleri seçin ve **Ekle'ye** tıklayın.

   - **Exchange** - Posta kutuları eklemek için **Düzenle'ye** tıklayın. Posta kutuları veya dağıtım grupları için arama kutusuna bir ad veya diğer ad (en az üç karakter) yazın. Koruyucu olmayan veri kaynakları olarak eklemek istediğiniz posta kutularını seçin ve **Ekle'ye** tıklayın.

   > [!NOTE]
   > **SharePoint** ve **Exchange** bölümlerini, bir Ekip veya Yammer grubuyla ilişkili siteleri ve posta kutularını gözetim dışı veri kaynakları olarak eklemek için kullanabilirsiniz. Ekip veya Yammer grubuyla ilişkili posta kutusunu ve siteyi ayrı olarak eklemeniz gerekir.<br/><br/> Ayrıca, SharePoint veri kaynağı olarak bir kök site URL'si (veya `https://contoso-my.sharepoint.com/`gibi`https://contoso-my.sharepoint.com/personal/`) eklenmesi desteklenmez. Belirli siteleri eklemeniz gerekir.

4. Gözetimsiz veri kaynaklarını ekledikten sonra, bu konumları beklemeye alma veya saklama seçeneğiniz vardır. Veri kaynağını beklemeye almak için veri kaynağının yanındaki **Ayrı Tut** onay kutusunu seçin veya seçimini kaldırın.

5. Veri kaynaklarını servis talebine eklemek için **Yeni gözetim dışı veri konumları** açılır sayfasının altındaki **Ekle'ye** tıklayın.

   Eklediğiniz her gözetim dışı veri kaynağı **, Veri kaynakları** sayfasında listelenir. Gözaltı olmayan veri kaynakları **, Kaynak türü** sütunundaki **Veri konumu** değeriyle tanımlanır.

   ![Veri kaynakları sekmesindeki gözetimsiz veri kaynakları.](../media/NonCustodialDataSources2.png)

Servis talebine gözetimsiz veri kaynakları ekledikten sonra, *gözetimsiz verileri yeniden dizine alma* adlı bir iş oluşturulur ve servis talebinin **İşler** sekmesinde görüntülenir. İş oluşturulduktan sonra, gelişmiş dizin oluşturma işlemi başlatılır ve veri kaynakları yeniden dizine alınır.

## <a name="manage-the-hold-for-non-custodial-data-sources"></a>Gözetim altında olmayan veri kaynakları için ayrı tutma işlemini yönetme

Gözetim dışı bir veri kaynağına ayrı tutma işlemi yaptıktan sonra, servis talebi için gözetim dışı veri kaynaklarını içeren bir saklama ilkesi otomatik olarak oluşturulur. Diğer gözetim dışı veri kaynaklarını ayrı tutmaya aldığınızda, bunlar bu saklama ilkesine eklenir.

1. eBulma (Premium) servis talebini açın ve **Ayrı Tut** sekmesini seçin.

2. GUID değerinin büyük/küçük harfe özel olduğu **NCDSHold-\<GUID\>** öğesine tıklayın.

   Açılır sayfa, gözetim altında tutulamayan veri kaynaklarıyla ilgili bilgileri ve istatistikleri görüntüler.

   ![Gözaltı olmayan veri kaynaklarının açılır sayfasında istatistikler görüntülenir.](../media/NonCustodialDataSourcesHoldFlyout.png)

3. Saklama dışı veri kaynaklarını görüntülemek ve aşağıdaki yönetim görevlerini gerçekleştirmek için Ayrı tutmayı **düzenle'ye** tıklayın:

   - **Konumlar** sayfasında, saklama dışı bir veri kaynağını ayrı tutmadan kaldırarak serbest bırakabilirsiniz. Bir veri kaynağının serbest bırakılması, gözetim altında olmayan veri kaynağını olaydan kaldırmaz. Yalnızca veri kaynağına yerleştirilen ayrı tutmayı kaldırır.

   - **Sorgu** sayfasında, saklamayı düzenleyerek bu durumdaki tüm gözetimsiz veri kaynaklarına uygulanan sorgu tabanlı bir ayrı tutma oluşturabilirsiniz.
