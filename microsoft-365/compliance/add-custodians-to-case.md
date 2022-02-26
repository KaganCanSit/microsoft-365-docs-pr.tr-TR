---
title: Bir vakaya koruyucular ekleme Advanced eDiscovery ekleme
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
ms.assetid: ''
description: İş akışlarınızı koordine etmek ve bir olayda ilgili veri kaynaklarını tanımlamak için Advanced eDiscovery koruyucu yönetim aracını nasıl kullanabileceğinizi öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b0a15610c84c9e1142cd1afa6ebf121f387ce807
ms.sourcegitcommit: 2e05865beeb2051fd9ece212a46179310b946a46
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2021
ms.locfileid: "62973864"
---
# <a name="add-custodians-to-an-advanced-ediscovery-case"></a>Bir vakaya koruyucular ekleme Advanced eDiscovery ekleme

Advanced eDiscovery'te yerleşik koruyucu yönetim aracını kullanarak, iş akışlarınızı koruyucuları yönetme ve vakayla ilişkili ilişkili, özel durumlu veri kaynaklarını belirleme arasında eşgüdüm elde edin. Bir custo custo bir Exchange ve OneDrive İş tutabilir. Araştırmanızı bulma işlemi sırasında, bir özel kullanıcıya erişen veya katkıda bulunan diğer veri kaynaklarını da (posta kutuları, siteler veya Teams) tanımlayabilirsiniz. Bu durumda, özel koruyucu yönetim aracını kullanarak bu veri kaynaklarını belirli bir custo ortak kullanabilirsiniz. Bir vakaya koruyucular ekdikten ve diğer veri kaynağını bu veri kaynağıyla ilişkilendirmenin ardından, verileri hızla koruyabilirsiniz ve özel veriler üzerinde aramaabilirsiniz.

Dört adımda, özel durumlar için özel Advanced eDiscovery ekleyebilir ve yönetebilirsiniz:

1. Koruyucuları tanımlama.

2. Özel veri konumlarını seçin.

3. Tutma ayarlarını yapılandırma.

4. Koruyucuları gözden geçirme ve işlemi tamamlama.

## <a name="make-sure-you-have-the-necessary-permissions"></a>Gerekli izinlere sahip olduğundan emin olun

Bir vakaya koruyucular eklemek için, eBulma Yöneticisi rol grubunun üyesi olmak gerekir. Bu size, bir vakaya koruyucuları eklemek ve özel veri kaynaklarını yerinde tutmak için gerekli izinleri sağlar. Daha fazla bilgi için bkz [. eBulma izinleri atama](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions).

## <a name="step-1-identify-custodians"></a>1. Adım: Koruyucuları belirleme

1. [https://compliance.microsoft.com](https://compliance.microsoft.com) Uygun eBulma izinleri atanmış bir kullanıcı hesabına gidip oturum açın.

2. Gezinti bölmesinin sol bölmesinde eK **Microsoft 365 uyumluluk merkezi'ı** >  **Advanced eDiscovery** Durumlar [**sekmesini**](https://go.microsoft.com/fwlink/p/?linkid=2173764) seçin.

3. Koruyucu eklemek istediğiniz vakayı seçin.

4. Veri kaynakları **sekmesini seçin** ve ardından Veri kaynağı **ekleYeni** >  **koruyucular ekle'yi seçin**.

5. Bir kişinin adının veya diğer adının ilk kısmını yazarak, kurumda bir veya birden çok kişiyi koruyucu olarak ekleyin. Doğru kişiyi buktan sonra listeye eklemek için adını seçin.

## <a name="step-2-choose-custodian-data-locations"></a>2. Adım: Özel veri konumlarını seçme

Siz koruyucuları seçdikten sonra, sistem otomatik olarak bu kullanıcıları ve onların veri kaynaklarını tanımlamaya ve doğrulamaya çalışır. Listeye koruyucular ekledikten sonra, araç otomatik olarak birincil posta kutusunu ve her custo custo custo verisi OneDrive posta kutusunu içerir. Vakaya koruyucular eklerken bu veri kaynaklarını eklemeyebilirsiniz.

Bir custo custo her iki posta kutusunun ve OneDrive hesabının yanı sıra, SharePoint sitesi veya Microsoft Team the custo ya da custo ya da bir Microsoft Team gibi bir custo custo bir üyesiyle de ilişkilendirmeniz gerekir. Bu, davanın koruyucuları ile ilişkilendirilmiş diğer veri kaynaklarında içeriği korumanız, toplamanız, çözümlemeniz ve gözden geçirmenizi sağlar.

Bir custo custo custo bir OneDrive posta kutusunun seçimini kaldırmak için:

1. Her custo ortak ile otomatik olarak ilişkilendirilmiş birincil veri konumlarını görüntülemek için custo custo ortaklarını genişletin.

2. Bir **custo** OneDrive  posta kutusunu veya **OneDrive** hangi hesabın bu custo ortak için veri konumu olarak ilişkilendirilen öğesini kaldırmak için Posta Kutusu veya Posta Kutusu'nun yanındaki Temizle'yi seçin.

   ![Bir custo cust ile ilişkilendirmek için konumları yapılandırma.](../media/ConfigureCustodianLocations.png)

Diğer posta kutularını, siteleri, siteleri, Teams veya Yammer özel bir koruyucuyla ilişkilendirmek için:

1. Veri konumlarını custo custo custo ortaklarını ilişkilendirmek için aşağıdaki hizmetleri görüntülemek için bir custo custo ortak kullanın. Veri **konumu** eklemek için hizmetin yanındaki Düzenle'ye tıklayın.

   - **Exchange**: Diğer posta kutularını özel dosyayla ilişkilendirmek için kullanın. Arama kutusuna, kullanıcı posta kutularının veya dağıtım gruplarının adını veya diğer adını (en az üç karakter) yazın. Özel kişi'ye atamak istediğiniz posta kutularını seçin ve Ekle'ye **tıklayın**.

   - **SharePoint**: Özel siteleri SharePoint custo custo ortaklarını kullanmak için kullanın. Listeden bir site seçin veya arama kutusuna bir URL yazarak siteyi arayın. Custo custo bir siteyi seçin ve Ekle'ye **tıklayın**.

   - **Teams**: Custo belirli bir Microsoft Teams atamak için kullanın. Özel belgeye atamak istediğiniz ekipleri seçin ve Ekle'ye **tıklayın**. Bir ekip eklemenizden sonra sistem, o ekiple ilişkilendirilmiş SharePoint posta kutusunu otomatik olarak tanımlar ve bu siteyi ve grup posta kutusunu tanımlar ve custo custo custo ayrıcalarına atar.

   - **Yammer**: Custo belirli Yammer şu anda üyesi olan kullanıcı gruplarını atamak için kullanın. Custo custo ve add seçeneğine **tıklayın**. Bir ekip eklemenizden sonra, sistem bu grupla ilişkilendirilmiş SharePoint posta kutusunu otomatik olarak tanımlar ve bu siteyi ve grup posta kutusunu tanımlar ve custo belgeye atar.

   > [!NOTE]
   > Exchange ve **SharePoint** posta kutusu veya siteyi  bir custo custo ortak olarak ilişkilendirmek için posta kutusu ve konum seçicilerini kullanabilirsiniz. , Bu, bir Microsoft Team veya Yammer olan ve custo custo custo bir üyesi olmadığını belirten posta kutusu ve siteyi birleçer. Bunu yapmak için, hem posta kutusunu hem de her ekiple ilişkili siteyi veya bir grup Yammer gerekir.

2. Tablodaki her koruyucuyu genişleterek, her özel Teams ve Yammer posta kutusu, site, posta kutusu ve Yammer gruplarının toplam sayısını görüntüebilirsiniz. Her custo Advanced eDiscovery custo bir iş akışında aşamalar top, işleme ve gözden geçirme sırasında korunur ve kullanılır.

3. Koruyucular ekledikten ve veri konumlarını yapılandırdikten sonra, **Tutma ayarları sayfasına** gitmek için **Sonraki'ne** tıklayın.  

## <a name="step-3-configure-hold-settings"></a>3. Adım: Tutma ayarlarını yapılandırma

 Koruyucuları ve bunların veri konumlarını sonuçlaştırdikten sonra, koruyucuların bir veya hepsini tutabilirsiniz. Bir custo custo ortaklarını yerinde tutabilirsiniz; bu şekilde tutma kaldırana veya koruyucuları tutmadan çıkarıncaya kadar, tüm içerik konumlarında bu içerik korunur. Bazı durumlarda, bir vakaya özel koruyucular eklemek ve onları tutmadan eklemek iyi olabilir.

Koruyucuları ve veri kaynaklarını yerinde tutmak için:

1. Tutma **ayarları sayfasında** , Ayrı tutma sütununu içeren onay kutusunu seçerek tek tek koruyuculara tutma **uygulayabilirsiniz** .

   Alternatif olarak, sütunun üst kısmında yer alan Tut onay kutusunu seçerek tüm koruyucuları yerinde tutebilirsiniz.

2. Koruyucuları tutma seçimlerini doğrulayın ve ardından Sonraki'ye **tıklayın**.

   > [!NOTE]
   > Bir custo custo ve bunların ilişkili veri kaynakları vakaya eklenir, ancak bu veri kaynaklarında yer alan içerik, durumla ilişkilendirilmiş olan tutma tarafından korunmaz.

## <a name="step-4-review-the-custodians-and-complete-the-process"></a>4. Adım: Koruyucuları gözden geçirme ve işlemi tamamlama

Bu vakaya koruyucuları gerçekten eklemeden önce, koruyucu listesini, onlara atanmış veri konumlarını ve tutma ayarlarını gözden geçirebilirsiniz.

1. Tablodaki her koruyucuyla ilişkili tüm veri kaynakları sayısını ve tutma ayarını doğrulayın ve gözden geçirin. Gerekirse, herhangi bir değişiklik yapmak **için Custo cust veya** **Hold settings** sayfalarına geri gidin.

2. **Vakaya** koruyucuları ve onların veri konumlarını eklemek ve tüm özel tutma ayarlarını uygulamak için Gönder'e tıklayın.

   Yeni koruyucular vakaya eklenir ve Veri kaynakları **sekmesinde** görüntülenir.

   [![Veri kaynakları sekmesinde listelenen koruyucular.](../media/DataSourcesTab.png) ](../media/DataSourcesTab.png#lightbox)
