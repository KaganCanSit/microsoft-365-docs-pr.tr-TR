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
description: İçerik aramalarının gerçek sonuçlarını ilk çalışma yerine dışarı Microsoft 365 uyumluluk merkezi, arama sonuçları raporunu dışarı aktarabilirsiniz. Rapor, arama sonuçlarının özetini ve dışarı aktarıla her öğe hakkında ayrıntılı bilgiler içeren bir belge içerir.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d06cc712e8c81304bbd11a9c93f35e48d279a36e
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989974"
---
# <a name="export-a-content-search-report"></a>İçerik arama raporunu dışarı aktarma

Microsoft 365 uyumluluk merkezi'daki İçerik aramasında (veya Çekirdek eBulma durumuyla ilişkilendirilmiş bir aramadan) tüm arama sonuçları kümesi dışarı aktar yerine, asıl arama sonuçlarını dışarı aktararak oluşturulan aynı raporları dışarı aktarabilirsiniz.
  
Raporu dışarı aktarsanız da, rapor dosyaları yerel bilgisayarınızda İçerik Arama ile aynı adı içeren bir klasöre indirilir, ancak bu klasör *_ReportsOnly.* Örneğin, İçerik Arama adı  *ContosoCase0815 ise, rapor ContosoCase0815* adlı bir *klasöre ContosoCase0815_ReportsOnly*. Rapora dahil edilen belgelerin listesi için bkz [. Rapora nelerin dahil olduğu](#whats-included-in-the-report).

## <a name="before-you-export-a-search-report"></a>Arama raporunu dışarı aktarmadan önce

- Bir arama raporunu dışarı aktarabilirsiniz ve bu raporda Uyumluluk Arama yönetimi rolüne Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak yerleşik eBulma Yöneticisi ve Kuruluş Yönetimi rol gruplarına atanır. Daha fazla bilgi için bkz [. eBulma izinleri atama](assign-ediscovery-permissions.md).

- Raporu dışarı aktarsanız bile veriler, yerel bilgisayarınıza Depolama önce Microsoft bulutunda geçici olarak Bir Azure bulut Depolama depolanır. Kuruluş kuruluşlarının Azure'daki **\*.blob.core.windows.net** uç noktasına bağlana olduğundan emin olun (joker karakter dışarı aktarmanız için benzersiz bir tanımlayıcıyı temsil eder). Arama sonuçları verileri, oluşturulduktan Depolama hafta sonra Azure Veri Kaynağı'nden silinir.

- Arama raporunu dışarı aktarmada kullanmakta olduğunuz bilgisayar aşağıdaki sistem gereksinimlerini karşılamalıdır:
  
  - En son Windows (32 bit veya 64 bit)
  
  - Microsoft .NET Framework 4.7 veya daha yüksek bir sürümü
  
- eBulma Dışarı Aktarma Aracı Microsoft Edge <sup>1'i</sup> çalıştırabilirsiniz. Arama sonuçlarını dışarı aktarmada Internet Explorer 11 kullanmak artık <sup>desteklenmiyor2</sup>.
  
  > [!NOTE]
  > <sup>1</sup> Yeni E-postada yapılan son Microsoft Edge ClickOnce artık varsayılan olarak etkinleştirilmez. Edge'de ClickOnce etkinleştirme yönergeleri için bkz. [eBulma Dışarı Aktarma](configure-edge-to-export-search-results.md) Aracı'nı Microsoft Edge. Ayrıca Microsoft, üçüncü taraf uygulamaları için üçüncü taraf uzantıları veya eklentileri ClickOnce değildir. Üçüncü taraf uzantıları veya eklentileri olan desteklenmeyen bir tarayıcı kullanarak arama sonuçlarını dışarı aktarma desteklenmez.
  > 
  > <sup>2</sup> Ağustos 2021'den itibaren Microsoft 365 uygulamaları ve hizmetleri artık Internet Explorer 11'i (IE11) desteklememektedir ve kullanıcılar daha iyi bir deneyime sahip olabilir veya bu uygulamalara ve hizmetlere bağlanamaz. Desteğin sorunsuz sona erer olması için, bu uygulama ve hizmetler önümüzdeki haftalarda ve aylarda aşamalı olarak yapılacaktır. Her uygulama ve hizmet bağımsız zamanlamalar üzerinde aşamalı olarak aşamalı olarak mektedir. Daha fazla bilgi için bu [blog gönderisi'ne bakın](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-365-apps-say-farewell-to-internet-explorer-11-and/ba-p/1591666).

- Arama tarafından döndürülen sonuçların tahmini toplam boyutu 2 TB'ın üzerinde olursa, raporları dışarı aktarma işlemi başarısız olur. Raporları başarıyla dışarı aktarmayı denemek için, kapsamı daraltmayı ve aramanın tahmini boyutunun 2 TB'ın altında olması için yeniden çalıştırmayı deneyin.

- Bir aramanın sonuçları 7 günlükten eskiye kadar ise ve dışarı aktarma raporu işi gönderdiğinizde, arama sonuçlarını güncelleştirmek için aramaya yeniden çalışmanızı istenen bir hata iletisi görüntülenir. Böyle bir durumda, dışarı aktarma işlemini iptal edin, aramanızı yeniden çalıştırın ve sonra dışarı aktarma işlemini yeniden başlatın.

- Arama raporlarını dışarı aktarma, aynı anda çalışan en fazla dışarı aktarma sayısına ve tek bir kullanıcının çalıştırılacağı en fazla dışarı aktarma sayısına göre sayılır. Dışarı aktarma sınırları hakkında daha fazla bilgi için bkz. [İçeriği Dışarı Aktarma arama sonuçları](export-search-results.md#export-limits).
  
## <a name="step-1-generate-the-report-for-export"></a>1. Adım: Dışarı aktarma için raporu oluşturma

İlk adım, raporu bilgisayarınıza dışarı aktarma işlemi için hazırlamaktır. Raporu dışarı aktarabilirsiniz, rapor belgeleri Microsoft bulutunda bir Azure Depolama alanına karşıya yükler.
  
1. İçerik Microsoft 365 uyumluluk merkezi, raporu dışarı aktarmayı istediğiniz İçerik arama'ya seçin.
  
2. Arama **açılır sayfasının** en altındaki Eylemler menüsünde Raporu dışarı aktar'a **tıklayın**.

   ![Eylemler menüsünde Raporu dışarı aktar seçeneği.](../media/ActionMenuExportReport.png)

   Rapor **dışarı aktarma** sayfası görüntülenir. Aramayla ilgili bilgileri dışarı aktar için kullanılabilen dışarı aktarma raporu seçenekleri, arama sonuçlarının posta kutularında mı yoksa sitelerde mi yoksa her ikisinde birden mi bulunduğuna bağlıdır.
  
3. Çıkış **seçenekleri'nin** altında aşağıdaki seçeneklerden birini belirleyin:
  
   ![Çıkış seçeneklerini dışarı aktarma.](../media/ExportOutputOptions.png)

    - **Tanınmayan biçime sahip olanlar** hariç olmak üzere tüm öğeler şifrelenir veya başka nedenlerle dizine alındı. Bu seçenek yalnızca dizine alınan öğelerle ilgili bilgileri dışarı aktarıyor.
  
    - **Tanınmayan biçime sahip olanlar** da dahil olmak üzere tüm öğeler şifrelenir veya başka nedenlerle dizine alındı. Bu seçenek dizine alınan ve dizine eksiz öğelerle ilgili bilgileri dışarı aktarıyor.
  
    - **Yalnızca tanınmayan biçime sahip öğeler şifrelenir veya başka nedenlerle dizine alındı.** Bu seçenek yalnızca, ilk kez ekli olmayan öğelerle ilgili bilgileri dışarı aktarıyor.

4. İçerikte **yinelemeyi etkinleştir seçeneğini Exchange yapılandırabilirsiniz**.
  
   - Bu seçeneği kullanırsanız, yinelenen iletilerin sayısı (yinelemeyi de-yinelemeden önce ve yinelemeden sonra) dışarı aktarma özeti raporuna dahil edilir. Ayrıca bu dosyada iletinin yalnızca bir kopyası manifest.xml. Ancak dışarı aktarma sonuçları raporu, yinelenen iletinin her kopyası için bir satır içerir; böylelikle, yinelenen iletinin bir kopyasını içeren posta kutularını tanımlayabilirsiniz. Dışarı aktarıldı raporlar hakkında daha fazla bilgi için bkz [. Rapora dahil edilenler](#whats-included-in-the-report).

   - Bu seçeneği seç dönmezseniz, dışarı aktarma raporları, yinelemeler dahil olmak üzere arama tarafından döndürülen tüm iletiler hakkında bilgi içerir.

     Yinelemeyi de-yineleme ve yinelenen öğelerin nasıl tanım olduğu hakkında daha fazla bilgi için bkz. [eBulma arama sonuçlarında yinelemeyi geri bulma](de-duplication-in-ediscovery-search-results.md).

5. Rapor **oluştur'a tıklayın**.

   Arama raporları indirmeye hazırlanır ve bu da rapor belgelerinin Microsoft bulutunda bir Azure Depolama bir konuma yük anlamına gelir. Bu birkaç dakika sürebilir.

Dışarı aktarıldı arama raporlarını indirme yönergeleri için sonraki bölüme bakın.
  
## <a name="step-2-download-the-report"></a>2. Adım: Raporu indirme

Sonraki adım, raporu Azure Veri Alanı'Depolama yerel bilgisayarınıza indirmektir.

> [!NOTE]
> Dışarı aktarıldı arama raporunun, raporu 1. Adımda oluşturması sonrasında 14 gün içinde indirilmiş olması gerekir.

1. İçerik **arama sayfasında**, Microsoft 365 uyumluluk merkezi **sekmesine** tıklayın
  
   Oluşturduğunuz dışarı aktarma **işinin gösterirken** dışarı aktarma işleri listesini güncelleştirmek için Yenile'ye tıklamanız gerekir. Rapor dışarı aktarma işleri, arama adının sonuna eklenen **adla _ReportsOnly** aramayla aynı olur.
  
2. 1. Adımda oluşturduğunuz dışarı aktarma işini seçin.

3. Dışarı aktar **tuşu altındaki Rapor** dışarı aktarma sayfasında **Panoya** **kopyala'ya tıklayın**. Arama sonuçlarını indirmek için 6. adımda bu anahtarı kullanırsiniz.
  
   > [!IMPORTANT]
   > Herkes eBulma Dışarı Aktarma aracını yük indirip başlatalır ve sonra arama raporunu indirmek için bu anahtarı kullana olduğundan, aynı parolaları veya güvenlikle ilgili diğer bilgileri korur gibi bu anahtarı korumak için önlemler almaya devam edin.

4. Uç uç sayfasının en üstünde Sonuçları **indir'e tıklayın**.

5. eBulma Dışarı Aktarma Aracı'nı yüklemeniz **istenirse Yükle'ye** **tıklayın**.

6. **eBulma Dışarı Aktarma Aracı'da** şunları yapın:

   ![eBulma Dışarı Aktarma Aracı.](../media/eDiscoveryExportTool.png)

   1. 3. adımda kopyalanmış olan dışarı aktarma anahtarını uygun kutuya yapıştırın.
  
   2. Arama **raporu** dosyalarını indirmek istediğiniz konumu belirtmek için Gözat'a tıklayın.

7. Arama **sonuçlarını** bilgisayarınıza indirmek için Başlat'a tıklayın.
  
    **eBulma Dışarı Aktarma Aracı**, indirilecek kalan öğelerin sayısının (ve boyutunun) tahmini de içinde olmak üzere, dışarı aktarma işlemiyle ilgili durum bilgilerini görüntüler. Dışarı aktarma işlemi tamamlandığında, dosyalar indirildikten sonra bu dosyalara erişebilirsiniz.
  
## <a name="whats-included-in-the-report"></a>Rapora neler dahildir?

İçerik arama sonuçlarıyla ilgili bir rapor oluşturmak ve dışarı aktararak, aşağıdaki belgeler indirilir:
  
- **Dışarı aktarma özeti:** Dışarı Excel özetini içeren en iyi belge. Bunlar arasında arama yapılan içerik kaynağı sayısı, her içerik konumunun arama sonucu sayısı, tahmini öğe sayısı, dışarı aktaracak olacak gerçek öğe sayısı ve dışarı aktaracak tahmini ve gerçek öğe boyutu gibi bilgiler yer sağlar.

   Raporu dışarı aktarıyorsanız, bağımsız olmayan öğelerin sayısı toplam tahmini arama sonuçları sayısına ve dışarı aktarma özet raporunda listelenen indirilen arama sonuçlarının toplam sayısına (arama sonuçlarını dışarı aktarmanız gerekirse) dahil edilir. Başka bir deyişle, indirilecek toplam öğe sayısı tahmini sonuçların toplam sayısına ve toplaminde eşit olmayan öğe sayısına eşittir.
  
- **Bildirim:** Arama sonuçlarına dahil edilen her öğe hakkında bilgi içeren bir bildirim dosyası (XML biçiminde). Yinelemeyi de etkinleştirdiyseyseniz, yinelenen iletiler bildirim dosyasına dahil değildir.

- **Sonuçlar:** Arama Excel alınan her bir dizine alınan öğe hakkında bilgi içeren bir satır içeren en iyi belge. E-posta için, sonuç günlüğü her ileti hakkında aşağıdaki bilgileri içerir: 

  - İletinin kaynak posta kutusunda bulunduğu konum (iletinin birincil posta kutusunda mı yoksa arşiv posta kutusunda mı bulunduğu da dahil).

  - İletinin gönderildiği veya alın aldığı tarih.

  - İletinin Konu satırı.

  - İletinin göndereni ve alıcıları.

  SharePoint ve OneDrive İş sitelerinden gelen belgeler için, sonuç günlüğü her belgeyle ilgili bilgileri içerir; örneğin:

  - Belgenin URL'si.

  - Belgenin bulunduğu site koleksiyonunun URL'si.

  - Belgenin son değiştirilma tarihi.

  - Belgenin adı (sonuç günlüğünde Konu sütununda yer alır).

  > [!NOTE]
  > Sonuçlar raporu'daki **satır sayısı** , toplam arama sonucu sayısı eksi İşaretsiz Öğeler raporunda listelenen öğelerin toplam **sayısına eşit** olması gerekir.
  
- **Trace.log:** Dışarı aktarma işlemi hakkında ayrıntılı günlük bilgileri içeren ve dışarı aktarma sırasında sorunları ortaya çıkarmanıza yardımcı olan izleme günlüğü. Arama raporlarını dışarı aktarmayla ilgili bir sorun hakkında Microsoft Desteği ile bir bilet açarsanız, bu izleme günlüğünü sağlamanız isten olabilir.

- **Tekinde olmayan öğeler:** Arama Excel ekli olduğu, satırlanmamış öğelerle ilgili bilgileri içeren en son belge. Arama sonuçları raporunu 2013'te indirebilirsiniz; bu rapor yine de indirilir, ancak boş kalır.
