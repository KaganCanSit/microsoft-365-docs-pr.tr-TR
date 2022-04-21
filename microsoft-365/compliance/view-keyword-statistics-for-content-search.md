---
title: eBulma arama sonuçlarının istatistiklerini görüntüleme
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
description: Microsoft Purview uyumluluk portalında eBulma (Standart) olayıyla ilişkili İçerik aramalarının ve aramalarının istatistiklerini görüntülemek için arama istatistikleri özelliğini kullanmayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5d35616823988562b3b075e7a513c8a98a4e3281
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "65000828"
---
# <a name="view-statistics-for-ediscovery-search-results"></a>eBulma arama sonuçlarının istatistiklerini görüntüleme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Bir İçerik araması veya Microsoft Purview eKeşif (Standart) olayıyla ilişkili bir arama oluşturup çalıştırdıktan sonra, tahmini arama sonuçlarıyla ilgili istatistikleri görüntüleyebilirsiniz. Bu, arama sonuçlarının özetini (arama açılır öğesi sayfasında görüntülenen tahmini arama sonuçlarının özetine benzer), arama sorgusuyla eşleşen öğelerin bulunduğu içerik konumlarının sayısı ve en çok eşleşen öğelere sahip içerik konumlarının kimliği gibi sorgu istatistiklerini içerir.
  
Ayrıca, arama sorgusundaki her anahtar sözcüğün istatistiklerini döndürmek üzere arama yapılandırmak için anahtar sözcükler listesini kullanabilirsiniz. Bu, sorgudaki her anahtar sözcük tarafından döndürülen sonuç sayısını karşılaştırmanıza olanak tanır.
  
Arama istatistiklerini bir CSV dosyasına da indirebilirsiniz. Bu, sonuçları karşılaştırmak ve raporları arama sonuçlarınız için hazırlamak için Excel'daki filtreleme ve sıralama özelliklerini kullanmanıza olanak tanır.
  
## <a name="get-statistics-for-searches"></a>Aramalar için istatistikleri alma

İçerik araması veya eBulma (Standart) servis talebiyle ilişkilendirilmiş bir aramanın istatistiklerini görüntülemek için:
  
1. Microsoft Purview uyumluluk portalında **Tümünü göster'e** tıklayın ve aşağıdakilerden birini yapın:

   - **İçerik araması'na** tıklayın ve açılır sayfayı görüntülemek için bir arama seçin.

     VEYA

   - Açılan sayfayı görüntülemek için **eBulma Çekirdeği'ne** >  tıklayın, bir servis talebi seçin ve **aramalar** sekmesinde bir arama seçin.

2. Seçili aramanın açılır sayfasında, **Arama istatistikleri** sekmesine tıklayın.
  
   ![İstatistikleri ara sekmesi.](../media/SearchStatistics1.png)

**Arama istatistikleri** sekmesi, aramayla ilgili farklı istatistik türleri içeren aşağıdaki bölümleri içerir.

### <a name="search-content"></a>İçerik arama

Bu bölümde, arama tarafından döndürülen tahmini öğelerin grafik özeti görüntülenir. Bu, arama ölçütlerine uyan öğe sayısını gösterir. Bu bilgiler, arama tarafından döndürülen tahmini öğe sayısı hakkında size bir fikir verir.

![Arama için tahminler.](../media/SearchContentReport.png)

- **Konumlara göre tahmini öğeler**: Arama tarafından döndürülen tahmini öğelerin toplam sayısı. Posta kutularında bulunan ve sitelerde bulunan belirli öğe sayısı da görüntülenir.

- **İsabetli tahmini konumlar**: Arama tarafından döndürülen öğeleri içeren içerik konumlarının toplam sayısı. Belirli sayıda posta kutusu ve site konumu da görüntülenir.

- **Konuma göre veri hacmi (MB cinsinden):** Arama tarafından döndürülen tüm tahmini öğelerin toplam boyutu. Posta kutusu öğelerinin ve site öğelerinin belirli boyutu da görüntülenir.

### <a name="condition-report"></a>Koşul raporu

Bu bölümde, arama sorgusuyla ilgili istatistikler ve arama sorgusunun farklı bölümleriyle eşleşen tahmini öğelerin sayısı görüntülenir. Arama sorgusunun her bileşeniyle eşleşen öğe sayısını analiz etmek için bu istatistikleri kullanabilirsiniz. Bu, arama ölçütlerini iyileştirmenize ve gerekirse kapsamı daraltmanıza yardımcı olabilir. Bu raporun bir kopyasını CSV biçiminde de indirebilirsiniz.

![Koşul raporu.](../media/SearchContentReportNoKeywordList.png)

- **Konum türü**: Sorgu istatistiklerinin uygulanabilecek içerik konumu türü. **Exchange** değeri posta kutusu konumunu, **SharePoint** değeri ise site konumunu gösterir.

- **Bölüm**: arama sorgusunun istatistikler için geçerli olan bölümü. **Birincil** , arama sorgusunun tamamını gösterir. **Anahtar sözcük** , satırdaki istatistiklerin belirli bir anahtar sözcük için olduğunu gösterir. Arama sorgusu için bir anahtar sözcük listesi kullanırsanız, sorgunun her bileşenine ilişkin istatistikler bu tabloya eklenir. Daha fazla bilgi için bkz. [Aramalar için anahtar sözcük istatistiklerini alma](#get-keyword-statistics-for-searches).

- **Koşul**: İlgili satırda görüntülenen istatistikleri döndüren arama sorgusunun gerçek bileşeni (anahtar sözcük veya koşul).

- **İsabetli konumlar**: **Koşul** sütununda listelenen birincil veya anahtar sözcük sorgusuyla eşleşen öğeleri içeren içerik konumlarının sayısı (**Konum türü** sütunu tarafından belirtilir).

- **Öğeler**: **Koşul** sütununda listelenen sorguyla eşleşen öğe sayısı (belirtilen içerik konumundan). Daha önce açıklandığı gibi, bir öğe aranmakta olan bir anahtar sözcüğün birden çok örneğini içeriyorsa, bu sütunda yalnızca bir kez sayılır.

- **Boyut (MB)**: **Koşul** sütunundaki arama sorgusuyla eşleşen bulunan tüm öğelerin (belirtilen içerik konumunda) toplam boyutu.

### <a name="top-locations"></a>En iyi konumlar

Bu bölümde, arama tarafından döndürülen en çok öğeye sahip belirli içerik konumlarıyla ilgili istatistikler görüntülenir. İlk 1.000 konum görüntülenir. Bu raporun bir kopyasını CSV biçiminde de indirebilirsiniz.

- Konum adının adı (posta kutularının e-posta adresi ve sitelerin URL'si).

- Konum türü (posta kutusu veya site).

- Arama tarafından döndürülen içerik konumundaki tahmini öğe sayısı.

- Her içerik konumundaki tahmini öğelerin toplam boyutu.

## <a name="get-keyword-statistics-for-searches"></a>Aramalar için anahtar sözcük istatistikleri alma

Daha önce açıklandığı gibi **Koşul raporu** bölümünde arama sorgusu ve sorguyla eşleşen öğelerin sayısı (ve boyutu) gösterilir. Arama sorgusu oluştururken veya düzenlerken anahtar sözcük listesi kullanırsanız, her anahtar sözcük veya anahtar sözcük tümceciğiyle eşleşen öğe sayısını gösteren gelişmiş istatistikler elde edebilirsiniz. Bu, sorgunun hangi bölümlerinin en (ve en az) etkili olduğunu hızla belirlemenize yardımcı olabilir. Örneğin, bir anahtar sözcük çok sayıda öğe döndürüyorsa, arama sonuçlarını daraltmak için anahtar sözcük sorgusunu daraltmayı seçebilirsiniz.

Bir anahtar sözcük listesi oluşturmak ve arama için anahtar sözcük istatistiklerini görüntülemek için:
  
1. Uyumluluk portalında yeni bir İçerik araması veya eBulma (Standart) servis talebiyle ilişkilendirilmiş bir arama oluşturun.

2. Arama sihirbazının **Koşullar** sayfasında. **Anahtar sözcük listesini göster** onay kutusunu seçin.

   ![Anahtar sözcükler listesini göster onay kutusu.](../media/SearchKeywordsList1.png)

3. Anahtar sözcükler tablosundaki bir satıra anahtar sözcük veya anahtar sözcük aşaması yazın. Örneğin, ilk satıra **bütçe** yazın, ikinci satıra **güvenlik** yazın ve üçüncü satıra **FY2021** yazın.

   ![Listeye en fazla 20 anahtar sözcük veya anahtar sözcük tümceciği yazın.](../media/SearchKeywordsList2.png)

   > [!NOTE]
   > Büyük anahtar sözcük listelerinin neden olduğu sorunları azaltmaya yardımcı olmak için, arama sorgusunun anahtar sözcük listesinde en fazla 20 satırla sınırlandırılırsınız.

4. Arama yapmak ve istatistiklerini almak istediğiniz anahtar sözcükleri listeye ekledikten sonra aramayı çalıştırın.

5. Arama tamamlandığında açılır sayfayı görüntülemek için seçin.

6. **Arama istatistikleri** sekmesinde **Koşul raporuna** tıklayarak aramanın anahtar sözcük istatistiklerini görüntüleyin.

    ![Her anahtar sözcüğün istatistikleri görüntülenir.](../media/SearchKeywordsList3.png)
  
    Önceki ekran görüntüsünde gösterildiği gibi, her anahtar sözcüğün istatistikleri görüntülenir; buna şunlar dahildir:

    - Aramaya dahil edilen her içerik konumu türü için anahtar sözcük istatistikleri.

    - Dizine alınmamış posta kutusu öğelerinin sayısı.

    - Her anahtar sözcüğün gerçek arama sorgusu ve sonuçları (**Bölüm** sütununda **Anahtar Sözcük** olarak tanımlanır) ve arama sorgusundan herhangi bir koşul içerir.

    - Tam arama sorgusu (**Bölüm** sütununda **Birincil** olarak tanımlanır) ve her konum türü için tam sorgunun istatistikleri. Bunların **Özet** sekmesinde görüntülenen istatistiklerle aynı olduğunu unutmayın.
