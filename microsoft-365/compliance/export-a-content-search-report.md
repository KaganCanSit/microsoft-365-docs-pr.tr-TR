---
title: İçerik arama raporunu dışarı aktarma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.CustomizeExportReport
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.assetid: 5c8c1db6-d8ac-4dbb-8a7a-f65d452169b9
description: Microsoft Purview uyumluluk portalında bir İçerik aramasının gerçek sonuçlarını dışarı aktarmak yerine, arama sonuçları raporunu dışarı aktarabilirsiniz. Rapor, arama sonuçlarının özetini ve dışarı aktarılacak her öğe hakkında ayrıntılı bilgi içeren bir belge içerir.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6ac46944ab454271358168c95a7df94d606e0ec5
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944843"
---
# <a name="export-a-content-search-report"></a>İçerik arama raporunu dışarı aktarma

Arama sonuçlarının tamamını Microsoft Purview uyumluluk portalındaki bir İçerik aramasından (veya Microsoft Purview eKeşif (Standart) durumuyla ilişkili bir aramadan) dışarı aktarmak yerine, gerçek arama sonuçlarını dışarı aktardığınızda oluşturulan raporları dışarı aktarabilirsiniz.
  
Bir raporu dışarı aktardığınızda, rapor dosyaları yerel bilgisayarınızdaki İçerik Arama ile aynı ada sahip ancak *_ReportsOnly* eklenmiş bir klasöre indirilir. Örneğin, İçerik Araması  *ContosoCase0815* olarak adlandırılırsa rapor *ContosoCase0815_ReportsOnly* adlı bir klasöre indirilir. Rapora dahil edilen belgelerin listesi için bkz. [Rapora eklenenler](#whats-included-in-the-report).

## <a name="before-you-export-a-search-report"></a>Arama raporunu dışarı aktarmadan önce

- Bir arama raporunu dışarı aktarmak için uyumluluk portalında Uyumluluk Araması yönetim rolüne atanmış olmanız gerekir. Bu rol varsayılan olarak yerleşik eBulma Yöneticisi ve Kuruluş Yönetimi rol gruplarına atanır. Daha fazla bilgi için bkz. [eBulma izinleri atama](assign-ediscovery-permissions.md).

- Bir raporu dışarı aktardığınızda, veriler yerel bilgisayarınıza indirilmeden önce geçici olarak Microsoft bulutundaki bir Azure Depolama konumunda depolanır. Kuruluşunuzun Azure'da .blob.core.windows.net (joker karakter dışarı **\*** aktarmanız için benzersiz bir tanımlayıcıyı temsil eder) uç noktasına bağlanaabildiğinden emin olun. Arama sonuçları verileri oluşturulduktan iki hafta sonra Azure Depolama konumundan silinir.

- Arama raporunu dışarı aktarmak için kullandığınız bilgisayarın aşağıdaki sistem gereksinimlerini karşılaması gerekir:
  
  - en son Windows sürümü (32 bit veya 64 bit)
  
  - Microsoft .NET Framework 4.7 veya üzeri
  
- eBulma Dışarı Aktarma Aracı'nı çalıştırmak için Microsoft Edge <sup>1</sup> kullanmanız gerekir. Arama sonuçlarını dışarı aktarmak için Internet Explorer 11'in kullanılması artık <sup>desteklenmiyor2</sup>.
  
  > [!NOTE]
  > <sup>1</sup> Microsoft Edge yapılan son değişikliklerin bir sonucu olarak, ClickOnce desteği artık varsayılan olarak etkin değildir. Edge'de ClickOnce desteğini etkinleştirme yönergeleri için bkz. [Microsoft Edge'de eBulma Dışarı Aktarma Aracı'nı kullanma](configure-edge-to-export-search-results.md). Ayrıca Microsoft, ClickOnce uygulamaları için üçüncü taraf uzantılar veya eklentiler üretmez. Üçüncü taraf uzantıları veya eklentileri olan desteklenmeyen bir tarayıcı kullanarak arama sonuçlarını dışarı aktarma desteklenmez.
  > 
  > <sup>2</sup> Ağustos 2021'den itibaren Microsoft 365 uygulamalar ve hizmetler artık Internet Explorer 11'i (IE11) desteklemeyecektir ve kullanıcılar düşük bir deneyime sahip olabilir veya bu uygulama ve hizmetlere bağlanamayabilir. Bu uygulamalar ve hizmetler, desteğin sorunsuz bir şekilde sona ermesini sağlamak için önümüzdeki haftalar ve aylar içinde aşamalı olarak kullanıma sunulacaktır. Her uygulama ve hizmet, bağımsız zamanlamalarla aşamalı olarak kullanıma alınıyor. Daha fazla bilgi için bu [blog gönderisini inceleyin](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-365-apps-say-farewell-to-internet-explorer-11-and/ba-p/1591666).

- Arama tarafından döndürülen sonuçların tahmini toplam boyutu 2 TB'ı aşarsa, raporları dışarı aktarma işlemi başarısız olur. Raporları başarılı bir şekilde dışarı aktarmak için kapsamı daraltmayı ve sonuçların tahmini boyutunun 2 TB'tan küçük olması için aramayı yeniden çalıştırmayı deneyin.

- Bir aramanın sonuçları 7 günden eskiyse ve dışarı aktarma raporu işi gönderirseniz, arama sonuçlarını güncelleştirmek için aramayı yeniden çalıştırmanızı isteyen bir hata iletisi görüntülenir. Böyle bir durumda dışarı aktarmayı iptal edin, aramayı yeniden çalıştırın ve dışarı aktarmayı yeniden başlatın.

- Arama raporlarını dışarı aktarmak, aynı anda çalışan en fazla dışarı aktarma sayısına ve tek bir kullanıcının çalıştırabileceği maksimum dışarı aktarma sayısına göre sayılır. Dışarı aktarma sınırları hakkında daha fazla bilgi için bkz. [İçeriği Dışarı Aktarma arama sonuçları](export-search-results.md#export-limits).
  
## <a name="step-1-generate-the-report-for-export"></a>1. Adım: Dışarı aktarma için rapor oluşturma

İlk adım, raporu bilgisayarınıza aktarmaya indirmek üzere hazırlamaktır. Raporu dışarı aktardığınızda, rapor belgeleri Microsoft bulutunda bir Azure Depolama alanına yüklenir.
  
1. Uyumluluk portalında, raporu dışarı aktarmak istediğiniz İçerik aramasını seçin.
  
2. Arama açılır penceresinin en altındaki **Eylemler** menüsünde **Raporu dışarı aktar'a** tıklayın.

   ![Eylemler menüsünde raporu dışarı aktar seçeneği.](../media/ActionMenuExportReport.png)

   **Raporu dışarı aktar** açılır sayfası görüntülenir. Arama hakkındaki bilgileri dışarı aktarmak için kullanılabilen dışarı aktarma raporu seçenekleri, arama sonuçlarının posta kutularında mı yoksa sitelerde mi yoksa her ikisinin birleşiminde mi bulunduğuna bağlıdır.
  
3. **Çıkış seçenekleri'nin** altında aşağıdaki seçeneklerden birini belirleyin:
  
   ![Çıkış seçeneklerini dışarı aktarın.](../media/ExportOutputOptions.png)

    - **Tanınmayan biçime sahip olanlar hariç olmak üzere tüm öğeler şifrelenir veya başka nedenlerle dizine eklenmemiştir**. Bu seçenek yalnızca dizine alınan öğeler hakkındaki bilgileri dışarı aktarır.
  
    - **Tanınmayan biçime sahip öğeler de dahil olmak üzere tüm öğeler şifrelenir veya başka nedenlerle dizine eklenmemiştir**. Bu seçenek, dizine alınmış ve dizine alınmamış öğeler hakkındaki bilgileri dışarı aktarır.
  
    - **Yalnızca tanınmayan biçime sahip olan, şifrelenen veya başka nedenlerle dizine eklenemeyen öğeler**. Bu seçenek yalnızca dizine alınmamış öğeler hakkındaki bilgileri dışarı aktarır.

4. **Exchange içerik için yinelenenleri kaldırmayı etkinleştir** seçeneğini yapılandırın.
  
   - Bu seçeneği seçerseniz, yinelenen iletilerin sayısı (yinelenenleri kaldırmadan önce ve yinelenenleri kaldırmadan sonra) dışarı aktarma özeti raporuna eklenir. Ayrıca, bir iletinin yalnızca bir kopyası manifest.xml dosyasına eklenir. Ancak dışarı aktarma sonuçları raporu, yinelenen iletinin bir kopyasını içeren posta kutularını tanımlayabilmeniz için yinelenen iletinin her kopyası için bir satır içerir. Dışarı aktarılan raporlar hakkında daha fazla bilgi için bkz. [Rapora eklenenler](#whats-included-in-the-report).

   - Bu seçeneği belirlemezseniz, dışarı aktarma raporları, yinelenenler de dahil olmak üzere arama tarafından döndürülen tüm iletiler hakkında bilgi içerir.

     Yinelenenleri kaldırma ve yinelenen öğeleri tanımlama hakkında daha fazla bilgi için bkz. [eBulma arama sonuçlarında](de-duplication-in-ediscovery-search-results.md) yinelenenleri kaldırma.

5. **Rapor oluştur'a** tıklayın.

   Arama raporları indirilmeye hazırlanır. Bu da rapor belgelerinin Microsoft bulutundaki bir Azure Depolama konumuna yüklendiği anlamına gelir. Bu işlem birkaç dakika sürebilir.

Dışarı aktarılan arama raporlarını indirme yönergeleri için sonraki bölüme bakın.
  
## <a name="step-2-download-the-report"></a>2. Adım: Raporu indirme

Sonraki adım, raporu Azure Depolama alanından yerel bilgisayarınıza indirmektir.

> [!NOTE]
> Dışarı aktarılan arama raporu, raporu 1. Adımda oluşturduktan sonraki 14 gün içinde indirilmelidir.

1. Uyumluluk portalındaki **İçerik arama** sayfasında **Dışarı Aktarmalar** sekmesini seçin
  
   Dışarı aktarma işlerinin listesini oluşturduğunuz dışarı aktarma işini gösterecek şekilde güncelleştirmek için **Yenile'ye** tıklamanız gerekebilir. Dışarı aktarma rapor işleri, arama adının sonuna **_ReportsOnly** ilgili aramayla aynı ada sahiptir.
  
2. 1. Adımda oluşturduğunuz dışarı aktarma işini seçin.

3. **Dışarı aktarma anahtarı altındaki Raporu dışarı** **aktar** açılır sayfasında **Panoya kopyala'ya** tıklayın. Arama sonuçlarını indirmek için 6. adımda bu anahtarı kullanırsınız.
  
   > [!IMPORTANT]
   > Herkes eBulma Dışarı Aktarma aracını yükleyip başlatabileceğinden ve arama raporunu indirmek için bu anahtarı kullanabileceğinden, parolaları veya güvenlikle ilgili diğer bilgileri koruyacağınız gibi bu anahtarı korumak için önlem almayı unutmayın.

4. Açılır sayfanın üst kısmında **Sonuçları indir'e** tıklayın.

5. **eBulma Dışarı Aktarma Aracı'nı** yüklemeniz istenirse **Yükle'ye** tıklayın.

6. **eBulma Dışarı Aktarma Aracı'nda** aşağıdakileri yapın:

   ![eBulma Dışarı Aktarma Aracı.](../media/eDiscoveryExportTool.png)

   1. 3. adımda kopyaladığınız dışarı aktarma anahtarını uygun kutuya yapıştırın.
  
   2. Arama raporu dosyalarını indirmek istediğiniz konumu belirtmek için **Gözat'a** tıklayın.

7. Arama sonuçlarını bilgisayarınıza indirmek için **Başlat'a** tıklayın.
  
    **eBulma Dışarı Aktarma Aracı**, indirilecek kalan öğelerin sayısının (ve boyutunun) tahmini de dahil olmak üzere dışarı aktarma işlemiyle ilgili durum bilgilerini görüntüler. Dışarı aktarma işlemi tamamlandığında dosyalara indirildikleri konumdan erişebilirsiniz.
  
## <a name="whats-included-in-the-report"></a>Rapora eklenenler

İçerik aramasının sonuçlarıyla ilgili bir rapor oluşturup dışarı aktardığınızda, aşağıdaki belgeler indirilir:
  
- **Dışarı aktarma özeti:** Dışarı aktarmanın özetini içeren bir Excel belgesi. Bu, aranan içerik kaynaklarının sayısı, her içerik konumundan alınan arama sonuçlarının sayısı, tahmini öğe sayısı, dışarı aktarılacak öğelerin gerçek sayısı ve dışarı aktarılacak öğelerin tahmini ve gerçek boyutu gibi bilgileri içerir.

   Raporu dışarı aktarırken dizine alınmamış öğeler eklerseniz, dizine alınmamış öğelerin sayısı tahmini arama sonuçlarının toplam sayısına ve dışarı aktarma özeti raporunda listelenen indirilen arama sonuçlarının toplam sayısına (arama sonuçlarını dışarı aktarmanız gerekiyorsa) dahil edilir. Başka bir deyişle, indirilecek öğelerin toplam sayısı, tahmini sonuçların toplam sayısına ve dizine alınmamış öğelerin toplam sayısına eşittir.
  
- **Bildirim:** Arama sonuçlarına dahil edilen her öğe hakkında bilgi içeren bir bildirim dosyası (XML biçiminde). Yinelenenleri kaldırma seçeneğini etkinleştirdiyseniz, yinelenen iletiler bildirim dosyasına eklenmez.

- **Sonuç -ları:** Arama sonuçlarıyla birlikte dışarı aktarılacak dizine alınan her öğe hakkında bilgi içeren bir satır içeren bir Excel belgesi. E-posta için, sonuç günlüğü her ileti hakkında aşağıdakiler dahil olmak üzere bilgiler içerir: 

  - İletinin kaynak posta kutusunda konumu (iletinin birincil posta kutusunda mı yoksa arşiv posta kutusunda mı olduğu dahil).

  - İletinin gönderildiği veya alındığı tarih.

  - İletideki Konu satırı.

  - İletinin göndereni ve alıcıları.

  SharePoint ve OneDrive İş sitelerindeki belgeler için, sonuç günlüğü her belge hakkında aşağıdakiler dahil olmak üzere bilgiler içerir:

  - Belgenin URL'si.

  - Belgenin bulunduğu site koleksiyonunun URL'si.

  - Belgenin son değiştirildiği tarih.

  - Belgenin adı (sonuç günlüğündeki Konu sütununda bulunur).

  > [!NOTE]
  > **Sonuçlar** raporundaki satır sayısı, arama sonuçlarının toplam sayısı eksi **Unindexed Items** raporunda listelenen toplam öğe sayısına eşit olmalıdır.
  
- **Trace.log:** Dışarı aktarma işlemiyle ilgili ayrıntılı günlük bilgilerini içeren ve dışarı aktarma sırasındaki sorunların ortaya çıkarılmasına yardımcı olabilecek bir izleme günlüğü. Arama raporlarını dışarı aktarmayla ilgili bir sorun hakkında Microsoft Desteği içeren bir bilet açarsanız, bu izleme günlüğünü sağlamanız istenebilir.

- **Dizine alınmamış öğeler:** Arama sonuçlarına dahil edilen dizinlenmemiş öğeler hakkında bilgi içeren bir Excel belgesi. Arama sonuçları raporunu oluştururken dizine alınmamış öğeler eklemezseniz, bu rapor yine indirilir, ancak boş kalır.
