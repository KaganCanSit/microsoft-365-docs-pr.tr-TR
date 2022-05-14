---
title: eBulma (Premium) olayına koruyucu ekleme
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
ms.assetid: ''
description: İş akışlarınızı koordine etmek ve bir durumda ilgili veri kaynaklarını tanımlamak için Microsoft Purview eKeşif (Premium) içindeki yerleşik koruyucu yönetim aracını nasıl kullanacağınızı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 59caac668972968ae3eada2d52d4a5fff8abeae0
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416122"
---
# <a name="add-custodians-to-an-ediscovery-premium-case"></a>eBulma (Premium) olayına koruyucu ekleme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview eBulma'da (Premium) yerleşik koruyucu yönetim aracını kullanarak, iş akışlarınızı koruyucuları yönetme ve bir olayla ilişkili ilgili, gözetimli veri kaynaklarını belirleme konusunda koordine edin. Bir koruyucu eklediğinizde, sistem Exchange posta kutusunu ve OneDrive İş hesabını otomatik olarak tanımlayabilir ve ayrı tutabilir. Araştırmanızın bulma işlemi sırasında, bir koruyucunun eriştiği veya katkıda bulunduğu diğer veri kaynaklarını (posta kutuları, siteler veya Teams gibi) de tanımlayabilirsiniz. Bu durumda, söz konusu veri kaynaklarını ilişkilendirmek için koruyucu yönetim aracını kullanabilirsiniz. Bir olaya koruyucular ekledikten ve diğer veri kaynaklarını bunlarla ilişkilendirdikten sonra, verileri hızla koruyabilir ve gözaltı verilerini arayabilirsiniz.

eBulma (Premium) olaylarında dört adımda koruyucu ekleyebilir ve yönetebilirsiniz:

1. Koruyucuları belirleyin.

2. Koruyucu veri konumlarını seçin.

3. Ayrı tutma ayarlarını yapılandırın.

4. Koruyucuları gözden geçirin ve işlemi tamamlayın.

## <a name="make-sure-you-have-the-necessary-permissions"></a>Gerekli izinlere sahip olduğunuzdan emin olun

Bir servis talebine koruyucu eklemek için eBulma Yöneticisi rol grubunun üyesi olmanız gerekir. Bu, bir olaya koruyucu eklemek ve koruyucu veri kaynaklarını ayrı tutmanız için gerekli izinleri sağlar. Daha fazla bilgi için bkz. [eBulma izinleri atama](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions).

## <a name="step-1-identify-custodians"></a>1. Adım: Koruyucuları belirleme

1. [https://compliance.microsoft.com](https://compliance.microsoft.com) adresine gidin ve uygun eBulma izinlerine atanmış bir kullanıcı hesabıyla oturum açın.

2. Microsoft Purview uyumluluk portalı sol gezinti bölmesinde **eKeşifBulmaBulma** >  **(Premium)** öğesini seçin ve [**Servis Talepleri**](https://go.microsoft.com/fwlink/p/?linkid=2173764) sekmesini seçin.

3. Koruyucu eklemek istediğiniz servis talebini seçin.

4. **Veri kaynakları** sekmesini ve ardından **Veri kaynağı** >  **ekleYeni koruyucu** ekle'yi seçin.

5. Bir kişinin adının veya diğer adının ilk bölümünü yazarak kuruluşunuzdaki bir veya daha fazla kullanıcıyı servis talebine koruyucu olarak ekleyin. Doğru kişiyi buldukta adını seçerek listeye ekleyin.

## <a name="step-2-choose-custodian-data-locations"></a>2. Adım: Koruyucu veri konumlarını seçme

Siz koruyucuları seçtikten sonra sistem otomatik olarak bu kullanıcıları ve veri kaynaklarını tanımlamaya ve doğrulamaya çalışır. Listeye koruyucular eklendikten sonra, araç otomatik olarak her koruyucu için birincil posta kutusunu ve OneDrive hesabını içerir. Olaya koruyucu eklerken bu veri kaynaklarını dahil etmemeyi seçebilirsiniz.

Bir koruyucunun posta kutusuna ve OneDrive hesabına ek olarak, diğer veri konumlarını da SharePoint sitesi veya koruyucunun üyesi olduğu bir Microsoft Ekibi gibi bir koruyucuyla ilişkilendirebilirsiniz. Bu, davanın koruyucularıyla ilişkili diğer veri kaynaklarındaki içeriği korumanıza, toplamanıza, analiz etmenizi ve gözden geçirmenizi sağlar.

Bir koruyucunun birincil posta kutusunun ve OneDrive hesabının seçimini kaldırmak için:

1. Her bir koruyucuyla otomatik olarak ilişkilendirilen birincil veri konumlarını görüntülemek için koruyucuyu genişletin.

2. **Posta Kutusu'nun** yanındaki **Temizle'yi** veya **OneDrive'ı** seçerek bir koruyucuya ait posta kutusunun veya OneDrive hesabının bu koruyucu için veri konumu olarak ilişkilendirildiğini kaldırın.

   ![Konumları bir koruyucuyla ilişkilendirilecek şekilde yapılandırın.](../media/ConfigureCustodianLocations.png)

Diğer posta kutularını, siteleri, Teams veya Yammer gruplarını belirli bir koruyucuyla ilişkilendirmek için:

1. Veri konumlarını koruyucuyla ilişkilendirmek için aşağıdaki hizmetleri görüntülemek için bir koruyucuyu genişletin. Veri konumu eklemek için hizmetin yanındaki **Düzenle'ye** tıklayın.

   - **Exchange**: Diğer posta kutularını koruyucuyla ilişkilendirmek için kullanın. Arama kutusuna kullanıcı posta kutularının veya dağıtım gruplarının adını veya diğer adını (en az üç karakter) yazın. Koruyucuya atanacak posta kutularını seçin ve **ekle'ye** tıklayın.

   - **SharePoint**: SharePoint siteleri koruyucuyla ilişkilendirmek için kullanın. Listeden bir site seçin veya arama kutusuna bir URL yazarak siteyi arayın. Koruyucuya atanacak siteleri seçin ve **ekle'ye** tıklayın.

   - **Teams**: Koruyucunun şu anda üyesi olduğu Microsoft Teams atamak için kullanın. Koruyucuya atanacak ekipleri seçin ve **ekle'ye** tıklayın. Bir ekip ekledikten sonra sistem, bu ekiple ilişkili SharePoint sitesini ve grup posta kutusunu otomatik olarak tanımlar ve bulur ve bunları koruyucuya atar.

   - **Yammer**: Koruyucunun şu anda üyesi olduğu Yammer gruplarını atamak için kullanın. Koruyucuya atanacak grupları seçin ve **ekle'ye** tıklayın. Bir ekip ekledikten sonra sistem, bu grupla ilişkilendirilmiş SharePoint siteyi ve grup posta kutusunu otomatik olarak tanımlar ve bulur ve bunları koruyucuya atar.

   > [!NOTE]
   > Kuruluşunuzdaki herhangi bir posta kutusunu veya siteyi bir koruyucuyla ilişkilendirmek için **Exchange** ve **SharePoint** konum seçicilerini kullanabilirsiniz. , Bu, bir koruyucunun üyesi olmadığı bir Microsoft Ekibi veya Yammer grubu için posta kutusuyla siteyi ilişkilendirmeyi içerir. Bunu yapmak için, her ekip veya Yammer grubuyla ilişkili hem posta kutusunu hem de siteyi eklemeniz gerekir.

2. Tablodaki her koruyucuyu genişleterek her bir koruyucuya atanan posta kutularının, sitelerin, Teams ve Yammer gruplarının toplam sayısını görüntüleyebilirsiniz. Her koruyucu için atanan veri konumlarını son haline getirdiğinizde, bu ilişkilendirmeler eBulma (Premium) iş akışındaki toplama, işleme ve gözden geçirme aşamalarında korunur ve kullanılır.

3. Koruyucuları ekledikten ve veri konumlarını yapılandırdıktan sonra, **Ayrı Tutma ayarları** sayfasına gitmek için **İleri'ye** tıklayın.  

## <a name="step-3-configure-hold-settings"></a>3. Adım: Ayrı tutma ayarlarını yapılandırma

 Koruyucuları ve veri konumlarını son haline getirdikten sonra, koruyucuların bazılarını veya tümünü beklemeye alabilirsiniz. Bir koruyucuyu beklemeye aldığınızda, saklamayı kaldırana veya koruyucuyu ayrı tutmadan serbest bırakana kadar, koruyucuyla ilişkili tüm içerik konumlarındaki tüm içerik korunur. Bazı durumlarda, bir servis talebine saklamadan koruyucu eklemek isteyebilirsiniz.

Koruyucuları ve veri kaynaklarını beklemeye almak için:

1. **Ayrı tutma ayarları** sayfasında Ayrı tutma sütununun altındaki onay kutusunu seçerek tek tek koruyuculara **ayrı saklama** uygulayabilirsiniz.

   Alternatif olarak, sütunun üst kısmındaki **Ayrı Tut** onay kutusunu seçerek tüm koruyucuları beklemeye alabilirsiniz.

2. Koruyucunun seçimleri tuttuğunu doğrulayın ve **İleri'ye** tıklayın.

   > [!NOTE]
   > Bir koruyucuya saklamazsanız, koruyucu ve ilişkili veri kaynakları servis talebine eklenir, ancak söz konusu veri kaynaklarındaki içerik, servis talebiyle ilişkili ayrı tutma tarafından korunmaz.

## <a name="step-4-review-the-custodians-and-complete-the-process"></a>4. Adım: Koruyucuları gözden geçirin ve işlemi tamamlayın

Olaya koruyucuları eklemeden önce, koruyucuların listesini, kendilerine atanan veri konumlarını ve saklama ayarlarını gözden geçirebilirsiniz.

1. Tablodaki her koruyucuyla ilişkili tüm veri kaynakları sayısını ve saklama ayarını doğrulayın ve gözden geçirin. Gerekirse, değişiklik yapmak için **Koruyucuyu tanımla** veya **Ayarları tut** sayfalarına geri dönün.

2. Olaya koruyucuları ve veri konumlarını eklemek ve tüm saklama saklama ayarlarını uygulamak için **Gönder'e** tıklayın.

   Yeni koruyucular servis talebine eklenir ve **Veri kaynakları** sekmesinde görüntülenir.

   [![Veri kaynakları sekmesinde listelenen koruyucular.](../media/DataSourcesTab.png) ](../media/DataSourcesTab.png#lightbox)
