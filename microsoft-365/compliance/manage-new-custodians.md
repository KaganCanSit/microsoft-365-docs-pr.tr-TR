---
title: eBulma (Premium) durumunda koruyucuları yönetme
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
description: Bir eBulma (Premium) olayındaki koruyucular listesinin ayrıntılarını görüntülemeyi, düzenlemeyi ve toplu düzenlemeyi öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: baffcb9d601d95d4be78cf47fcbc3037daff86c8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634038"
---
# <a name="manage-custodians-in-an-ediscovery-premium-case"></a>eBulma (Premium) durumunda koruyucuları yönetme

bir Microsoft Purview eKeşif (Premium) servis talebinin **Veri kaynakları** sekmesindeki **Koruyucular** sayfası, servis talebine eklenmiş olan tüm koruyucuların listesini içerir. Bir olaya koruyucu ekledikten sonra, her koruyucu hakkındaki ayrıntılar Azure Active Directory'den otomatik olarak toplanır ve eKeşif (Premium) içinde görüntülenebilir.

## <a name="view-custodian-details"></a>Koruyucu ayrıntılarını görüntüleme

Bir koruyucuyla ilgili ayrıntıları görüntülemek için, **Koruyucular** sekmesindeki listeden koruyucuya tıklayın. Bir açılır sayfa görüntülenir ve koruyucu hakkında aşağıdaki bilgileri içerir.

![Koruyucu ayrıntıları.](../media/CustodianDetails.PNG)

- İletişim bilgileri

  - **Başlık**. Koruyucunun iş unvanı.
  
  - **Kullanıcı asıl adı**. Koruyucunun kullanıcı asıl adı (UPN), örneğin AdeleV@contoso.onmicrosoft.com.
  
  - **Konum**. Bekçinin iş yerindeki ofis yeri.
  
  - **Yönetici**. Bekçinin yöneticisi. Atanan yönetici, bu koruyucu için herhangi bir yükseltme iletişimini alacak.
  
  - **Bölüm' de**. Bekçinin çalıştığı bölümün adı.

- Servis talebi bilgileri

  - **Durum.** Dava içindeki koruyucunun durumu. **Etkin** durumu, koruyucunun olayın bir parçası olduğunu gösterir. Bir servis talebinin koruyucusunun serbest bırakılması durumunda durum **Serbest Bırakıldı** olarak değiştirilir.
  
  - **Bekleyin**. Koruyucunun beklemeye alınmış olup olmadığını gösterir.

- Veri konumları ve saklama bilgileri

  ![Koruyucu veri konumları ve saklama bilgileri.](../media/CustodianHoldDetails.PNG)

  - **Gözetim yerleri**. Koruyucuyla ilişkilendirilmiş ve olayın bir parçası olan veri kaynaklarının (posta kutuları, siteler ve Teams) sayısını ve türünü gösterir.

    - Her veri konumu ayrı tutma durumunu gösterir. Bekletme durumu için olası değerler: **Beklemede**, **Beklemede değil** ve **Devam ediyor**.

    - Veri kaynağı için ayrı tutma durumunu görmüyorsanız lütfen servis talebi için **Ayrı Tut** sekmesinde listelenen koruyucu ayrı tutma durumunu denetleyin. Koruyucu ayrı tutma, ayrı tutmadaki belirli veri kaynaklarını tanımlar.

## <a name="edit-a-custodian"></a>Koruyucu düzenleme

Durumunuz ilerledikçe, belirli bir koruyucu ve olayla ilgili ek veri kaynakları olabileceğini keşfedebilirsiniz. Diğer senaryolarda, gözden geçirilmiş ve ilgili olmadığı düşünülen belirli veri kaynaklarını kaldırmak isteyebilirsiniz.

Bir koruyucuyla ilişkili veri kaynaklarını güncelleştirmek için:

1. **eBulma > eBulma (Premium)** bölümüne gidin ve servis talebini açın.
  
2. **Veri Kaynakları** sekmesine tıklayın.
  
3. Listeden bir koruyucu seçin ve açılır sayfada **Düzenle'ye** tıklayın.

    ![Veri Kaynaklarını Düzenle'yi seçin.](../media/EditCustodianDataSource.PNG)
  
4. Koruyucunun birincil posta kutusunu ve OneDrive hesabını eklemek veya kaldırmak için:

    - Daha önce koruyucuyla ilişkilendirilmiş birincil veri konumlarını görüntülemek için koruyucuyu genişletin.

    - **Posta Kutusu** veya **OneDrive'ın** yanındaki **Düzenle'ye** tıklayarak koruyucunun posta kutusunu veya OneDrive konumunu ekleyin.

    - **Posta Kutusu'nun** veya **OneDrive'ın** yanındaki **Temizle'yi** seçerek, koruyucunun posta kutusunu veya OneDrive hesabını bu koruyucu için veri konumu olarak ilişkilendirilmeye kaldırın.

5. Belirli bir koruyucuya başka posta kutuları, siteler, Teams veya Yammer grupları eklemek veya kaldırmak için hizmetin yanındaki **Düzenle'ye** tıklayarak veri konumu ekleyin.

   - **Exchange**: Diğer posta kutularını koruyucuyla ilişkilendirmek için kullanın. Arama kutusuna kullanıcı posta kutularının veya dağıtım gruplarının adını veya diğer adını (en az üç karakter) yazın. Koruyucuya atanacak posta kutularını seçin ve **ekle'ye** tıklayın.

   - **SharePoint**: SharePoint sitelerini koruyucuyla ilişkilendirmek için kullanın. Listeden bir site seçin veya arama kutusuna bir URL yazarak siteyi arayın. Koruyucuya atanacak siteleri seçin ve **ekle'ye** tıklayın.

   - **Teams**: Koruyucunun şu anda üyesi olduğu Microsoft Teams'i atamak için kullanın. Koruyucuya atanacak ekipleri seçin ve **ekle'ye** tıklayın. Bir ekip ekledikten sonra, sistem otomatik olarak bu ekiple ilişkili SharePoint sitesini ve grup posta kutusunu tanımlar ve bulur ve bunları koruyucuya atar.

   - **Yammer**: Koruyucunun şu anda üyesi olduğu Yammer gruplarını atamak için kullanın. Koruyucuya atanacak grupları seçin ve **ekle'ye** tıklayın. Bir ekip ekledikten sonra sistem, bu grupla ilişkilendirilmiş SharePoint sitesini ve grup posta kutusunu otomatik olarak tanımlar ve bulur ve bunları koruyucuya atar.

   > [!NOTE]
   > **Exchange** ve **SharePoint** konum seçicilerini kullanarak, kuruluşunuzdaki bir posta kutusunu veya siteyi, bir koruyucunun üyesi olmadığı ekipler veya Yammer grupları dahil olmak üzere bir koruyucuyla ilişkilendirebilirsiniz. Bunu yapmak için her ekip veya Yammer grubuyla ilişkili hem posta kutusunu hem de siteyi eklemeniz gerekir.

6. Koruyucunun veri konumlarını düzenledikten sonra **, Ayrı Tutma ayarları** sayfasına gitmek için **İleri'ye** tıklayın.  

7. **Saklama ayarları** sayfasında, koruyucunun saklama ayarlarını güncelleştirin.

## <a name="reindex-custodian-data"></a>Koruyucu verilerini yeniden dizine alma

Yasal araştırmalara yönelik çoğu eBulma iş akışında, yasal bir davaya koruyucu eklendikten sonra bir koruyucunun verilerinin bir alt kümesi aranır. Çok büyük dosya boyutları veya olası veri bozulması nedeniyle, bir koruyucuyla ilişkili veri kaynaklarındaki bazı öğeler kısmen dizine alınabilir. eBulma'da (Premium) [gelişmiş dizin oluşturma](indexing-custodian-data.md) özelliği kullanıldığında, çoğu kısmen dizine alınan öğeler isteğe bağlı olarak bu öğeler yeniden dizine alınarak otomatik olarak düzeltilebilir.

Bir servis talebine bir koruyucu eklendiğinde, koruyucuyla ilişkili veri kaynaklarında bulunan veriler otomatik olarak yeniden dizine alınır (gelişmiş dizin oluşturma işlemi tarafından). Bu, verileri indirip düzeltmek ve ardından çevrimdışı aramak yerine yerinde bırakabileceğiniz anlamına gelir. Ancak, yasal bir olayın yaşam döngüsü sırasında yeni veri kaynakları bir koruyucuyla ilişkilendirilebilir. Bu durumda, kısmen dizinlenmiş öğeleri düzeltmek ve koruyucunun verilerinin dizinini güncelleştirmek için gelişmiş dizin oluşturma işlemini yeniden çalıştırarak koruyucunun verilerini yeniden dizine alabilirsiniz.

Kısmen dizine alınmış öğeleri ele almak üzere yeniden dizinleme işlemini tetikleme:

1. **eBulma > eBulma (Premium)** bölümüne gidin ve servis talebini açın.

2. **Kaynaklar** sekmesine tıklayın.

3. **Koruyucular** sayfasında, verilerinin yeniden dizine alınması gereken bir koruyucu seçin.

4. Açılır sayfada **Dizini güncelleştir'e** tıklayın.

   Dizin işinin oluşturulduğunu belirten bir iletişim kutusu görüntülenir.

Koruyucu verilerinin yeniden dizine alınması uzun süren bir işlemdir; oluşturulan ilgili iş, **koruyucu verilerini yeniden dizine alma** olarak adlandırılır. **İlerleme durumunu İşler** sekmesinde veya **Koruyucular** sekmesinde **, Dizin oluşturma işi durumu** sütunundaki durumu izleyerek izleyebilirsiniz.

Daha fazla bilgi için bkz.:

- [İşleme hatalarıyla çalışma](processing-data-for-case.md)

- [İşleri yönetme](managing-jobs-ediscovery20.md)

## <a name="release-a-custodian-from-a-case"></a>Bir davadan koruyucu serbest bırakma

Bir davanın kapatıldığı durumlarda bir koruyucu serbest bırakılır, koruyucu artık bir davanın içeriğini koruma yükümlülüğü altında değildir veya koruyucunun artık davayla ilgili olmadığı kabul edilir. 

Bir saklama bildirimi yayımlandıktan sonra bir koruyucuyu serbest bırakırsanız, koruyucuya bir yayın bildirimi gönderilir. Ayrıca, koruyucuyla ilişkilendirilmiş veri kaynaklarına yerleştirilen tüm tutmalar kaldırılır. Koruyucu, hiçbir yasal saklama bildirimi verilmediği *sessiz bir beklemeye* alınırsa, bir serbest bırakma bildirimi gönderilmez, ancak söz konusu koruyucuyla ilişkili veri kaynaklarına yerleştirilen tüm saklamalar kaldırılır.

Bir bekçiyi serbest bırakmak için:

1. **eBulma > eBulma (Premium)** bölümüne gidin ve servis talebini açın.

2. **Kaynaklar** sekmesine tıklayın.

3. **Koruyucular** sayfasında, ardından davadan tahliye edilen koruyucuyu seçin.

4. Açılır sayfada **Koruyucuyu serbest bırak'a** tıklayın.

   Koruyucuyla ilişkilendirilmiş bir veri kaynağına bir ayrı tutma yerleştirildiğinde ayrı tutmanın kaldırılacağını ve farklı bir eBulma (Premium) olayıyla ilişkili diğer tüm ayrı tutmaların yine geçerli olacağını açıklayan bir uyarı sayfası görüntülenir. Bu, diğer koruma ve saklama özelliklerini içerir (microsoft 365 saklama ilkesi gibi).

5. Koruyucuyu serbest bırakmak istediğinizi onaylamak için **Evet'e** tıklayın. 

    **Bu kullanıcının Koruyucular** sekmesindeki durumu **Serbest Bırakıldı** olarak ayarlanır ve açılır sayfadaki **Ayrı Tutma durumu** **False** olarak değiştirilir.

> [!NOTE]
> Bir koruyucu aynı anda birçok yasal davaya dahil olabilir. Bir koruyucu belirli bir davadan serbest bırakıldığında, diğer durumlardaki tutmalar ve bildirimler etkilenmez.
