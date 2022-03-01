---
title: eBulma arama sonuçları için istatistikleri görüntüleme
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.search: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
description: Bir çalışma penceresinde, Çekirdek eKbulma durumuyla ilişkilendirilmiş İçerik aramaları ve aramaları için istatistikleri görüntülemek üzere arama istatistikleri özelliğini Microsoft 365 uyumluluk merkezi.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 04d24020cd22d40d6706295ccb53578bf3aef756
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033339"
---
# <a name="view-statistics-for-ediscovery-search-results"></a>eBulma arama sonuçları için istatistikleri görüntüleme

bir İçerik araması veya Çekirdek eBulma durumuyla ilişkilendirilmiş bir arama oluşturduk ve çalıştırdikten sonra, tahmini arama sonuçlarıyla ilgili istatistikleri görüntüebilirsiniz. Bu, arama sonuçlarının özetini (arama uç sayfası üzerinde görüntülenen tahmini arama sonuçlarının özetine benzer), içerik konumlarının sayısı, arama sorgusuyla eşleşen öğelerle birlikte sorgu istatistikleri ve en çok eşleşen öğelere sahip içerik konumlarının kimliği gibi sorgu istatistiklerini içerir.
  
Buna ek olarak, bir arama sorgusunda yer alan her anahtar sözcükle ilgili istatistikler bulmak üzere bir arama yapılandırmak için anahtar sözcükler listesini kullanabilirsiniz. Böylece, sorguda yer alan her anahtar sözcük tarafından döndürülen sonuç sayısını karşılaştırabilirsiniz.
  
Ayrıca, bir CSV dosyasına da arama istatistikleri indirebilirsiniz. Böylece, sonuçları karşılaştırmak ve raporları arama sonuçlarınız için Excel ve sıralama özelliklerini kullanabilirsiniz.
  
## <a name="get-statistics-for-searches"></a>Aramalar için istatistikleri al

İçerik arama veya Çekirdek eBulma durumuyla ilişkilendirilmiş bir aramanın istatistiklerini görüntülemek için:
  
1. Sayfa Microsoft 365 uyumluluk merkezi **Göster'e** tıklayın ve sonra da birini yapın:

   - İçerik **arama'yı** tıklatın ve sonra, uçarak çıkış sayfasını görüntülemek için bir arama seçin.

     VEYA

   - **eBulma Puanı'ne** >  **tıklayın, bir** vaka seçin ve sonra açılır sayfayı görüntülemek için  Aramalar sekmesinde bir arama seçin.

2. Seçili aramanın açılır sayfasında, Arama istatistikleri **sekmesine** tıklayın.
  
   ![Arama istatistikleri sekmesi.](../media/SearchStatistics1.png)

Arama **istatistikleri sekmesi** , aramayla ilgili farklı türde istatistikler içeren aşağıdaki bölümler için içerir.

### <a name="search-content"></a>İçerik arama

Bu bölümde, arama tarafından döndürülen tahmini öğelerin grafik bir özeti görüntülenir. Bu, arama ölçütlerine uyan öğelerin sayısını gösterir. Bu bilgiler, arama tarafından döndürülen tahmini öğe sayısı hakkında size bir fikir verir.

![Arama, arama tahminlerini sağlar.](../media/SearchContentReport.png)

- **Konumlara göre tahmini** öğeler: Arama tarafından döndürülen tahmini öğelerin toplam sayısı. Posta kutularında ve sitelerde bulunan belirli sayıda öğe de görüntülenir.

- **İsabet sayısı ile tahmini** konumlar: Arama tarafından döndürülen öğelerin bulunduğu toplam içerik konumu sayısı. Belirli sayıda posta kutusu ve site konumu da görüntülenir.

- **Konuma göre veri hacmi (MB)**: Arama tarafından döndürülen tahmini tüm öğelerin toplam boyutu. Ayrıca, posta kutusu öğelerinin ve site öğelerinin belirli boyutu da görüntülenir.

### <a name="condition-report"></a>Koşul raporu

Bu bölümde, arama sorgusuyla ilgili istatistikler ve arama sorgusunun farklı bölümleriyle eşan tahmini öğelerin sayısı görüntülenir. Arama sorgusunun her bileşenine uygun öğe sayısını çözümlemek için bu istatistikleri kullanabilirsiniz. Bu, arama ölçütlerini daraltmanıza ve gerekirse kapsamı daraltmanıza yardımcı olabilir. Ayrıca, bu raporun bir kopyasını CSV biçiminde de indirebilirsiniz.

![Koşul raporu.](../media/SearchContentReportNoKeywordList.png)

- **Konum türü**: Sorgu istatistiklerinin uygulan bulunduğu içerik konumu türü. Posta kutusunun **Exchange** kutusu konumunu, posta kutusunun değeri ise **SharePoint** bir site konumunu gösterir.

- **Bölüm**: Arama sorgusunun istatistik bölümü uygulanabilir. **Birincil** , tüm arama sorgusunu gösterir. **Anahtar** sözcük, satırdaki istatistiklerin belirli bir anahtar sözcük için olduğunu gösterir. Arama sorgusu için bir anahtar sözcük listesi kullanırsanız, sorgunun her bileşenine ilişkin istatistikler bu tabloya eklenir. Daha fazla bilgi için bkz [. Aramalar için anahtar sözcük istatistiklerini al](#get-keyword-statistics-for-searches).

- **Koşul**: İlgili satırda görüntülenen istatistikleri döndürülen arama sorgusunun gerçek bileşeni (anahtar sözcük veya koşul).

- **Hits içeren konumlar**: Koşul sütununda listelenen birincil veya anahtar sözcük sorgusuyla eşananlı öğeler içeren içerik konumlarının (Konum türü sütunu tarafından belirtilen **)** sayısı.

- **Öğeler**: Koşul sütununda listelenen sorguyla aynı olan öğelerin sayısı (belirtilen içerik **konumdan)** Daha önce de belirtildiği gibi, bir öğede arama yapılan birden çok anahtar sözcük örneği varsa, bu sütunda yalnızca bir kez sayılır.

- **Boyut (MB)**: Bulunan (belirtilen içerik konumda) bulunan ve Koşul sütunundaki arama sorgusuyla eşanan tüm öğelerin **toplam** boyutu.

### <a name="top-locations"></a>En üst konumlar

Bu bölümde, arama tarafından döndürülen en fazla öğeyle birlikte belirli içerik konumlarına ilişkin istatistikler görüntülenir. En yüksek 1.000 konum görüntülenir. Ayrıca, bu raporun bir kopyasını CSV biçiminde de indirebilirsiniz.

- Konum adının adı (posta kutularının e-posta adresi ve sitelerin URL'si).

- Konum türü (posta kutusu veya site).

- Arama tarafından döndürülen içerik konumdaki tahmini öğe sayısı.

- Her içerik konumuyla ilgili tahmini öğelerin toplam boyutu.

## <a name="get-keyword-statistics-for-searches"></a>Aramalar için anahtar sözcük istatistiklerini al

Daha önce de **açıklanan Koşul raporu** bölümü, arama sorgusunu ve sorguyla eşleşmeye sahip öğelerin sayısını (ve boyutunu) gösterir. Arama sorgusu ekleyebilirsiniz veya düzenlerken anahtar sözcük listesi kullanırsanız, her anahtar sözcük veya anahtar sözcük tümceciğiyle kaç öğenin eşleştirilmiş olduğunu gösterecek gelişmiş istatistikler eldeebilirsiniz. Bu, sorgunun en etkili (ve en az) hangi bölümlerinin etkili olduğunu hızla tanımlamanıza yardımcı olabilir. Örneğin, anahtar sözcük çok fazla sayıda öğe döndürürse, arama sonuçlarını daraltmak için anahtar sözcük sorgusunu daraltmayı seçebilirsiniz.

Bir anahtar sözcük listesi oluşturmak ve arama anahtar sözcük istatistiklerini görüntülemek için:
  
1. İçerik Microsoft 365 uyumluluk merkezi bir İçerik araması veya Çekirdek eKbulma durumuyla ilişkilendirilmiş bir arama oluşturun.

2. Arama **sihirbazının** Koşullar sayfasında. Anahtar sözcük **listesini göster onay** kutusunu seçin.

   ![Anahtar sözcük listesini göster onay kutusu.](../media/SearchKeywordsList1.png)

3. Anahtar sözcükler tablosuna bir satıra bir anahtar sözcük veya anahtar sözcük aşaması yazın. Örneğin, ilk **satıra bütçe** yazın **, ikinci** satıra güvenlik ve üçüncü satıra **da FY2021** yazın.

   ![Listeye en çok 20 anahtar sözcük veya anahtar sözcük tümceciği yazın.](../media/SearchKeywordsList2.png)

   > [!NOTE]
   > Büyük anahtar sözcük listelerinin neden olduğu sorunları azaltmaya yardımcı olmak için, arama sorgusunun anahtar sözcük listesinde en çok 20 satırla sınırlıdırsiniz.

4. Aramak ve istatistikleri almak istediğiniz anahtar sözcükleri listeye ekledikten sonra, aramanızı çalıştırın.

5. Arama tamamlandığında, uçarak çıkış sayfasını görüntülemek için seçin.

6. Arama **istatistikleri sekmesinde** Koşul raporuna **tıklayın ve** aramanın anahtar sözcük istatistiklerini görüntüleyin.

    ![Her anahtar sözcüğün istatistikleri görüntülenir.](../media/SearchKeywordsList3.png)
  
    Önceki ekran görüntüsünde gösterildiği gibi, her anahtar sözcüğün istatistikleri görüntülenir; bu, şunları kapsar:

    - Aramaya dahil edilen her içerik konumu türü için anahtar sözcük istatistikleri.

    - Diziye eksiz posta kutusu öğelerinin sayısı.

    - Asıl arama sorgusu ve her anahtar sözcüğün sonuçları (Parça sütununda **Anahtar** Sözcük olarak  tanımlanır), arama sorgusundan gelen koşulları içerir.

    - Tam arama sorgusu (Parça sütununda **Birincil** olarak **tanımlanır** ) ve her konum türü için tam sorgu istatistikleri. Bunların, Özet sekmesinde görüntülenen istatistiklerin aynı **olduğunu** unutmayın.
