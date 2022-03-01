---
title: Bir dava durumunda koruyucuları Advanced eDiscovery yönetme
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
description: Bir dava durumunda koruyucular listesini görüntülemeyi, düzenlemeyi ve toplu olarak Advanced eDiscovery öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 794677c8675f044bafb1c9a441e6c2bbee3e1c86
ms.sourcegitcommit: b19e54b3888a0b07d08dbd23172daec303c7c95b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2021
ms.locfileid: "63008083"
---
# <a name="manage-custodians-in-an-advanced-ediscovery-case"></a>Bir dava durumunda koruyucuları Advanced eDiscovery yönetme

Bir **çalışma sayfasındaki** Veri kaynakları sekmesindeki Koruyucular sayfası Advanced eDiscovery bu vakaya eklenmiş olan tüm koruyucuların listesini içerir. Bir vakaya koruyucular eklemenizden sonra, her custo Azure Active Directory hakkında ayrıntılar otomatik olarak toplanır ve Advanced eDiscovery.

## <a name="view-custodian-details"></a>Custo cust

Bir custo custo bir listesinden Custo custo custo bir **sekmeye** tıklayın. Bir flyout sayfası görüntülenir ve custo bir bilgi hakkında aşağıdaki bilgileri içerir.

![Custo cust](../media/CustodianDetails.PNG)

- İletişim bilgileri

  - **Başlık**. Custohal'in iş unvanı.
  
  - **Kullanıcı asıl adı**. Custoando için kullanıcı asıl adı(UPN) (UPN), örneğin, AdeleV@contoso.onmicrosoft.com.
  
  - **Konum'a iki farklı konum seçin**. Custo bir iş yerindeki ofis konumu.
  
  - **Yönetici**. Custohal'ın yöneticisi. Belirlenen yönetici, bu custo
  
  - **Department.** Custo custo bazında çalışan departmanın adı.

- Vaka bilgileri

  - **Durum'a .** Durum bilgili dosyanın durumu. Etkin durumu **,** özel dosyanın vakanın parçası olduğunu gösterir. Bir koruyucu bir vakadan çıkarıldı ise, durumu Serbest Bırakıldı **olarak değiştirilir**.
  
  - **Bekleyin**. Özel öğenin tutduruldu olup olduğunu gösterir.

- Veri konumları ve tutma bilgileri

  ![Custo veri konumları ve hold information.](../media/CustodianHoldDetails.PNG)

  - **Tek gözlere sahip konumlar**. Custo veri kaynağıyla ilişkilendirilmiş ve davanın bir parçası olan veri kaynaklarının (posta kutuları, siteler ve Teams) sayısını ve türünü gösterir.

    - Her veri konumu, tutma durumunu gösterir. Tutma durumu için olası değerler: **Tut** durumda, **Tutm durumda değil** ve **Sürüyor**.

    - Veri kaynağının tutma durumunu görmüyorsanız, lütfen bu durumla ilgili Olarak Tut sekmesinde listelenen koruyucu tutma **durumunu** kontrol edin. Özel tutma, belirli veri kaynaklarının yerinde tutma yerini tanımlar.

## <a name="edit-a-custodian"></a>Custo cust

Vakanız ilerledikçe, belirli bir koruyucuyla ve vakayla ilgili ek veri kaynakları olduğunu keşfedebilirsiniz. Diğer senaryolarda, gözden geçirilen ve ilgili olmadığını kabul etmiş olan bazı veri kaynaklarını kaldırmak istiyor olabilirsiniz.

Özel dosyayla ilişkilendirilmiş veri kaynaklarını güncelleştirmek için:

1. **eBulma E-> Advanced eDiscovery** gidin ve vakayı açın.
  
2. Veri Kaynakları **sekmesine** tıklayın.
  
3. Listeden bir koruyucu seçin ve sonra, uçarak çıkış **sayfasında** Düzenle'ye tıklayın.

    ![Veri Kaynaklarını Düzenleme.](../media/EditCustodianDataSource.PNG)
  
4. Custo belge için birincil posta kutusu OneDrive ve posta kutusu hesabı eklemek veya kaldırmak için:

    - Custo ortak daha önce ilişkili olan birincil veri konumlarını görüntülemek için custo custo ortaklarını genişletin.

    - **Custo** bir posta **kutusu veya** **posta OneDrive** eklemek için Posta Kutusu veya Posta Kutusu'nun yanındaki OneDrive tıklayın.

    - Custo belirli  bir **hesabın** **posta OneDrive** ve posta kutusunun bu custo OneDrive ortak için bir veri konumu olarak ilişkilendirilen öğesini kaldırmak için Posta Kutusu veya Posta Kutusu'nun yanındaki Temizle'yi seçin.

5. Belirli bir özel ekliye diğer posta kutularını, siteleri, Teams veya Yammer gruplarını eklemek veya kaldırmak için, veri konumu eklemek için hizmetin yanındaki Düzenle'ye tıklayın.

   - **Exchange**: Diğer posta kutularını custo ortak yapmak için kullanın. Arama kutusuna, kullanıcı posta kutularının veya dağıtım gruplarının adını veya diğer adını (en az üç karakter) yazın. Özel kişi'ye atamak istediğiniz posta kutularını seçin ve Ekle'ye **tıklayın**.

   - **SharePoint**: Özel siteleri SharePoint Custo ortaklarını ilişkilendirmek için kullanın. Listeden bir site seçin veya arama kutusuna bir URL yazarak siteyi arayın. Custo custo bir siteyi seçin ve Ekle'ye **tıklayın**.

   - **Teams**: Custo belirli bir Microsoft Teams atamak için kullanın. Özel belgeye atamak istediğiniz ekipleri seçin ve Ekle'ye **tıklayın**. Siz bir ekip ekledikten sonra, sistem otomatik olarak bu ekiple ilişkilendirilmiş SharePoint siteyi ve grup posta kutusunu otomatik olarak tanımlar ve bu posta kutusunu custo custo bir ekip olarak atar.

   - **Yammer**: Custo belirli Yammer şu anda üyesi olduğu kullanıcı gruplarını atamak için kullanın. Custo custo ve add seçeneğine **tıklayın**. Bir ekip eklemenizden sonra, sistem bu grupla ilişkilendirilmiş SharePoint posta kutusunu otomatik olarak tanımlar ve bu siteyi ve grup posta kutusunu tanımlar ve custo custo ayrıcalarına atar.

   > [!NOTE]
   > **Exchange** ve **SharePoint** konum seçicilerini kullanarak, kuruluşta yer alan herhangi bir posta kutusu veya siteyi (koruyucu, üye olmadığınız ekipler veya Yammer grupları gibi) bir özelkök ile bir custohal ile ilişkilendirmek için kullanabilirsiniz. Bunu yapmak için, hem posta kutusunu hem de her ekiple veya grupla ilişkilendirilmiş siteyi Yammer gerekir.

6. Özel dosya için veri konumlarını düzenledikten sonra, Tutma **ayarları** sayfasına gitmek için **Sonraki'ne** tıklayın.  

7. Tutma **ayarları sayfasında** , custo cust için tutma ayarlarını güncelleştirin.

## <a name="reindex-custodian-data"></a>Reindex custo cust

Yasal soruşturmalara ilişkin eBulma iş akışlarının çoğunda, yasal bir vakaya özel koruyucu eklendikten sonra custo bir custo bir veri alt kümesinde arama yapılan bir durumdur. Çok büyük dosya boyutları veya olası veri bozulmaları nedeniyle, koruyucuyla ilişkilendirilmiş veri kaynaklarında yer alan bazı öğeler kısmen dizine edilebilir. Gelişmiş [dizin oluşturma özelliği](indexing-custodian-data.md) kullanılarak, Advanced eDiscovery kısmen dizine alan öğeler, isteğe bağlı olarak yeniden dizine kullanılarak otomatik olarak düzeltilir.

Bir vakaya bir özel bilgi ek olduğunda, custo bir veri kaynağında yer alan veriler otomatik olarak yeniden dizine alır (gelişmiş dizin oluşturma işlemi tarafından). Bu, verileri indirmek, düzeltmek ve ardından çevrimdışı aramak zorunda kalmadan olduğu gibi, verilerin yerinde bırakılacağı anlamına gelir. Bununla birlikte, bir yasal davanın yaşam döngüsü sırasında yeni veri kaynakları bir koruyucuyla ilişkilendirilebilirsiniz. Bu durumda, kısmen dizine alınan öğeleri düzeltmek ve custo bir veri dizini güncelleştirmek için gelişmiş dizin oluşturma işlemini yeniden çalıştırarak custo dizine edebilirsiniz.

Yeniden dizine kısmen dizine alan öğelerin işaretlendiğinde yeniden dizin oluşturma işlemini tetiklemek için:

1. **eBulma E-> Advanced eDiscovery** gidin ve vakayı açın.

2. Kaynaklar **sekmesine** tıklayın.

3. **Custodians sayfasında**, verileri yenidenxed olması gereken bir özel koruyucu seçin.

4. Uçarak çıkış sayfasında Dizini **güncelleştir'e tıklayın**.

   Dizin işinin oluşturulmuş olduğunu söyleyen bir iletişim kutusu görüntülenir.

Custo custo bir uzun süre çalışan bir işlemdir; oluşturulan ilgili iş **Re-indexing custo veri olarak adlandırılmıştır**. İşlerin ilerleme durumunu, **İş** sekmesinde veya Koruyucular sekmesinde Dizin  oluşturma iş durumu sütunundaki **durumu izleerek izleyebilirsiniz**.

Daha fazla bilgi için bkz.:

- [İşleme hatalarla çalışma](processing-data-for-case.md)

- [İşleri yönetme](managing-jobs-ediscovery20.md)

## <a name="release-a-custodian-from-a-case"></a>Bir davadan koruyucu bırakma

Bir davanın kapatılan durumlarda koruyucu çıkarılmıştır, koruyucuların bir davanın içeriğini koruma yükümlülüğü yoktur veya koruyucu artık davayla ilgili olmadığı kabul edildinde. 

Bir tutma bildirimi yayımlandıktan sonra bir custo bir sürüm bildirimi gönderilir. Ayrıca, koruyucularla ilişkilendirilmiş veri kaynaklarına yerleştirilen tüm korumalar kaldırılır. Custo custo custo her hangi bir yasal tutma bildirimi düzenlemeyen sessiz bir tutma durumuna yerleştirilirse, bir sürüm bildirimi gönderilmez ama bu özel kişi ile ilişkilendirilmiş veri kaynaklarına yerleştirilen tüm tutmalar kaldırılır.

Bir custo cust

1. **eBulma E-> Advanced eDiscovery** gidin ve vakayı açın.

2. Kaynaklar **sekmesine** tıklayın.

3. **Custodians sayfasında**, ve ardından durumdan serbest bıraklık olan custo bir seçin.

4. Uçarak çıkış sayfasında Release **custo cust**

   Özel durumla ilişkilendirilmiş bir veri kaynağına tutma yerleştirilirse tutma durumunda tutmanın kaldırılacak ve farklı bir koruma durumuyla ilişkilendirilmiş diğer tüm verilerin Advanced eDiscovery geçerli olacağını açıklayan bir uyarı sayfası görüntülenir. Bu, diğer tür saklama ve bekletme özelliklerini (örneğin, bir saklama Microsoft 365 içerir).

5. **Custo** ayrıca seçeneğini serbest bırakmak istediğiniz onaylamak için Evet'e tıklayın. 

    Koruyucular sekmesinde bu kullanıcının durumu Serbest  bırakıldı olarak ayarlanır ve açılır sayfada Tutma  durumu **False olarak değiştirilir**.

> [!NOTE]
> Bir koruyucu aynı anda çeşitli yasal davalara dahil olabilir. Bir özel durumdan özel bir koruyucu çıkarıldında, diğer davalarda tıla ve bildirimlerden etkilenmez.
