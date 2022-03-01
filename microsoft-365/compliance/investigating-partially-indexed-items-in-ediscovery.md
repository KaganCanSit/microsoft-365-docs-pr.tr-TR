---
title: eBulma'da kısmen dizine alan öğeleri inceleme
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
ms.assetid: 4e8ff113-6361-41e2-915a-6338a7e2a1ed
ms.custom:
- seo-marvel-apr2020
description: Kısmen dizine alındı öğeleri (dizine eksiz öğeler olarak da adlandırılan) Exchange, SharePoint ve OneDrive İş öğeleri yönetmeyi öğrenin.
ms.openlocfilehash: 308b99b8bcb8d11c53759700d43651e521987948
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033345"
---
# <a name="investigating-partially-indexed-items-in-ediscovery"></a>eBulma'da kısmen dizine alan öğeleri inceleme

Arama sonuçlarından çalıştırmış Microsoft 365 uyumluluk merkezi, bir arama Microsoft 365 uyumluluk merkezi tahmin edilen arama sonuçlarına kısmen dizine alan öğeleri otomatik olarak dahil eder. Kısmen dizine alınan Exchange, SharePoint ve OneDrive İş sitelerinden posta kutusu öğeleriyle belgelerine, bazı nedenlerden dolayı arama için tamamen dizine alınmmış değil. E-posta iletilerinin ve site belgelerinin çoğu, e-posta iletilerinin Dizin oluşturma sınırları [içinde olduğundan başarılı bir şekilde dizine alınmıştır](limits-for-content-search.md#indexing-limits-for-email-messages). Bununla birlikte, bazı öğeler bu dizin oluşturma sınırlarını aşar ve kısmen dizine alındı. eBulma aramalarını çalıştırarak, arama için öğelerin dizine alamamalarının ve kısmen dizine alınan öğeler olarak döndürüllemelerinin diğer nedenleri:
  
- E-posta iletilerinin resim dosyaları gibi açılamıyor bir ekli dosyası vardır; kısmen dizine alınmış e-posta öğelerinin en yaygın nedeni bu olur.

- E-posta iletisine eklenmiş çok fazla dosya var.

- E-posta iletisine eklenen dosya çok büyük.

- Dosya türü dizin oluşturma için destekle birlikte, belirli bir dosya için dizin oluşturma hatası oluştu.

Her ne kadar değişken olsa da çoğu kuruluşta, müşterilerin çoğunda hacmin %1'inden az, kısmen dizine alan içerik boyutuna göre içeriğin %12'den küçükleri vardır. Ses düzeyi ile boyut arasındaki farkın nedeni, daha büyük dosyaların tam olarak dizine alamayacak içerik içeriklerinin olasılığının daha yüksek olmasıdır.
  
## <a name="why-does-the-partially-indexed-item-count-change-for-a-search"></a>Kısmen dizine alındı öğe sayısı aramada neden değişir?

eBulma aramalarını çalıştırdikten sonra, arama yapılan konumlarda kısmen dizine alan öğelerin toplam sayısı ve boyutu, aramanın ayrıntılı istatistiklerinde görüntülenen arama sonucu istatistiklerinde listelenir. Bunlara, arama  *istatistiklerindeinde eksiz*  öğeler adı ve unindexed( Arama sonuçlarında döndürülen kısmen dizine alındı öğelerinin sayısını etkileyecek birkaç şey şu şekildedir:
  
- Bir öğe kısmen dizine alındı ise ve arama sorgusuyla eş büyüklükte olursa, arama sonucu öğelerinin sayısına (ve boyutuna) ve kısmen dizine alan öğelere dahil edilir. Bununla birlikte, aynı aramanın sonuçları dışarı aktarıldı mı, öğe yalnızca arama sonuçları kümesine dahil edilir; kısmen dizine alan bir öğe olarak dahil değildir.

- SharePoint ve OneDrive sitelerinde kısmen dizine alınan öğeler, aramanın ayrıntılı istatistiklerinde görüntülenen  kısmen dizine alınan öğelerin tahminlerine dahil değildir. Bununla birlikte, eBulma aramanın sonuçlarını dışarı aktarıyorken kısmen dizine alan öğeler dışarı aktarabilirsiniz. Örneğin, yalnızca sitelerde arama yaptıysanız, kısmen dizine alınan tahmini öğe sayısı sıfır olur.
  
## <a name="calculating-the-ratio-of-partially-indexed-items-in-your-organization"></a>Kuruluşta kısmen dizine alan öğelerin oranını hesaplama

Kuruluşlarının kısmen dizine alan öğelere maruz kalma özelliğini anlamak için, tüm posta kutularında (boş bir anahtar sözcük sorgusu kullanarak) tüm içerik için arama çalıştırabilirsiniz. Aşağıdaki örnekte, 1.629.904 (146,46 GB) tam dizine sahip öğeler ve 10.025 (10,27 GB) kısmen dizine alan öğeler vardır.
  
![Kısmen dizine alındı öğeleri gösteren arama istatistiklerinin örneği.](../media/PartiallyIndexedItemsTest.png)
  
Aşağıdaki hesaplamaları kullanarak kısmen dizine alan öğelerin yüzdesini hesapabilirsiniz.
  
 **Kısmen dizine alan öğelerin oranını hesaplamak için:**

`(Total number of partially indexed items/Total number of items) x 100`

`(10025/1629904) x 100 = 0.62%`

Önceki örnekte yer alan arama sonuçları kullanılarak, posta kutusu öğelerinin %0,62'si kısmen dizine alınarak.
  
 **Kuruluşta kısmen dizine alan öğelerin boyutunun yüzdesini hesaplamak için:**

`(Size of all partially indexed items/Size of all items) x 100`

`(10.27 GB/146.46 GB) x 100 = 7.0%`

Önceki örnekte, posta kutusu öğelerinin toplam boyutunun %7'si kısmen dizine alınmış öğelerden alınıyor. Daha önce de belirtildiği gibi çoğu kuruluşta, çoğu kuruluşun içeriği hacmine göre %1'den az ve kısmen dizine alan içerik boyutuna göre %12'den az içeriği vardır.

## <a name="working-with-partially-indexed-items"></a>Kısmen dizine alındı öğeleriyle çalışma

İlgili bilgiler içer olmadığını doğrulamak için kısmen dizine alınan öğeleri incelemeniz gereken durumlarda, kısmen dizine alınan öğeler hakkında bilgi [](export-a-content-search-report.md) içeren bir içerik arama raporunu dışarı aktarabilirsiniz. İçerik arama raporunu dışarı aktarıyorken, kısmen dizine alan öğeleri içeren dışarı aktarma seçenekleriden birini seçmeye emin olun.
  
![Kısmen dizine alan öğeleri dışarı aktarmaya yönelik ikinci veya üçüncü seçeneği belirtin.](../media/PartiallyIndexedItemsExportOptions.png)
  
Bu seçeneklerden birini kullanarak eBulma arama sonuçlarını veya arama raporunu dışarı aktarsanız, dışarı aktarmada Tekil Olarak Adlı Rapor Items.csv. Bu rapor, dosyayla aynı bilgilerin çoğunu ResultsLog.csv içerir; Bununla birlikte, Dizine Alındı Items.csv kısmen dizine alan öğelerle ilgili iki alan da vardır: Hata **Etiketleri** ve **Hata Özellikleri**. Bu alanlar, kısmen dizine alınan her öğe için dizin oluşturma hatası hakkında bilgi içerir. Bu iki alanda yer alan bilgileri kullanmak, belirli bir dizin hatasının araştırmanızı etki edip ete olmadığını belirlemenize yardımcı olabilir. 

> [!NOTE]
> Bu Dosya ya da Items.csv, Hata Türü ve **Hata İletisi adlı** **alanları da içerir**. Bunlar, Hata Etiketleri ve Hata Özellikleri alanlarındaki bilgilere benzeyen, ancak daha az  ayrıntılı bilgi içeren  eski alanlardır. Bu eski alanları güvenle yoksayabilirsiniz.
  
## <a name="errors-related-to-partially-indexed-items"></a>Kısmen dizine alan öğelerle ilgili hatalar

Hata etiketleri iki bilgiden, hatadan ve dosya türünden oluştu. Örneğin, bu hata/dosya türü çifti:

```text
 parseroutputsize_xls
```

 `parseroutputsize` hatadır ve `xls` hatanın üzerinde yer alan dosyanın dosya türü olur. Dosya türünün tanınması veya hataya dosya türünün geçerli olmadığı durumlarda, dosya türünün `noformat` yerine değerin yerini alırsınız.
  
Aşağıda dizin hataları listesi ve hatanın olası nedeninin açıklaması ve açıklamaları ve yer alır.
  
| Hata etiketi | Açıklama |
|:-----|:-----|
| `attachmentcount` <br/> |E-posta iletisinde çok fazla ek var ve bu eklerden bazıları işlenmedi.  <br/> |
| `attachmentdepth` <br/> |İçerik alicisi ve belge ayrıştırıcısı, diğer eklerin içinde iç içe çok fazla ek düzeyi buldu. Bu eklerden bazıları işlenmedi.  <br/> |
| `attachmentrms` <br/> |RMS korumalı olduğundan bir ek kod çözme işlemi başarısız oldu.  <br/> |
| `attachmentsize` <br/> |E-posta iletisine eklenen dosya fazla büyük ve işlenemez.  <br/> |
| `indexingtruncated` <br/> |İşlenen e-posta iletisi dizine yazarken, dizine alınabilir özelliklerden biri fazla büyük ve kesilmişti. Kesilmiş özellikler Hata Özellikleri alanında listelenir.  <br/> |
| `invalidunicode` <br/> |E-posta iletisi, geçerli Unicode olarak işlenemedi metni içeriyor. Bu öğe için dizin oluşturma tamamlanmamış olabilir.  <br/> |
| `parserencrypted` <br/> |Ek veya e-posta iletisi içeriği şifrelenir Microsoft 365 içeriği çözemedi.  <br/> |
| `parsererror` <br/> |Ayrıştırma sırasında bilinmeyen bir hata oluştu. Bu durum genellikle bir yazılım hatası veya hizmet kilitlenmesi ile sonuç verir.  <br/> |
| `parserinputsize` <br/> |Ek, ayrıştırıcının işlemek için fazla büyük olduğu için bu ekin ayrıştırılamadı veya tamamlanmadı.  <br/> |
| `parsermalformed` <br/> |Ek, yanlış biçimlendirilmiş ve ayrıştırıcı tarafından işnemedi. Bu sonuç, eski dosya biçimlerden, uyumsuz yazılım tarafından oluşturulan dosyalardan veya iddia edilenden farklı bir şey olarak taklit edilen virüslerden dolayı olabilir.  <br/> |
| `parseroutputsize` <br/> |Bir ekin ayrıştırmanın çıktısı fazla büyükti ve kesilmesi gerekti.  <br/> |
| `parserunknowntype` <br/> |Bir ekin, algılaya Microsoft 365 bir dosya türü vardı.  <br/> |
| `parserunsupportedtype` <br/> |Bir ekin algılay Office 365 bir dosya türü vardı, ancak bu dosya türünün ayrıştırıcısı desteklenmiyor.  <br/> |
| `propertytoobig` <br/> |Exchange Mağazası'Exchange e-posta özelliğinin değeri alınamıyor ve ileti işlenemez. Bu normalde yalnızca e-posta iletinin gövde özelliğinde olur.  <br/> |
| `retrieverrms` <br/> |İçerik alıcı RMS korumalı iletinin kodunu çözemedi.  <br/> |
| `wordbreakertruncated` <br/> |Dizin oluşturma sırasında belgede çok fazla sözcük tanımlandı. Sınıra ulaşılırken özellik iş süreci durdurulur ve özellik kesilir.  <br/> |

Hata alanları, Hata Etiketleri alanında listelenen işleme hatasında hangi alanların etkilendiğini açıklar. veya gibi bir özelliği arıyorsanız  `subject`  `participants`, iletinin gövdesinde oluşan hatalar aramanın sonuçlarını etkilemez. Bu, tam olarak hangi kısmen dizine alan öğeleri daha fazla araştırmak zorunda olabileceğini belirlerken yararlı olabilir.
  
## <a name="using-a-powershell-script-to-determine-your-organizations-exposure-to-partially-indexed-email-items"></a>PowerShell betiği kullanarak, kuruluşta kısmen dizine alan e-posta öğelerine maruz kalma sürenizi belirleme

Aşağıdaki adımlar, tüm Exchange posta kutularında tüm öğeleri arar ve sonra da kuruluşun kısmen dizine alan e-posta öğelerinin oranı hakkında bir rapor (sayma ve boyuta göre) oluşturan ve oluşan her dizin oluşturma hatası için öğe sayısını (ve dosya türünü) görüntüleyen bir PowerShell betiği çalıştırmayı gösterir. Dizin oluşturma hatasını tanımlamak için önceki bölümdeki hata etiketi açıklamalarını kullanın.
  
1. Aşağıdaki metni, Windows PowerShell dosya adı son eklerini kullanarak bir .ps1 betik dosyasına kaydedin; örneğin, `PartiallyIndexedItems.ps1`.

   ```powershell
     write-host "**************************************************"
     write-host "     Security & Compliance Center PowerShell      " -foregroundColor yellow -backgroundcolor darkgreen
     write-host "   eDiscovery Partially Indexed Item Statistics   " -foregroundColor yellow -backgroundcolor darkgreen
     write-host "**************************************************"
     " " 
     # Create a search with Error Tags Refinders enabled
     Remove-ComplianceSearch "RefinerTest" -Confirm:$false -ErrorAction 'SilentlyContinue'
     New-ComplianceSearch -Name "RefinerTest" -ContentMatchQuery "size>0" -RefinerNames ErrorTags -ExchangeLocation ALL
     Start-ComplianceSearch "RefinerTest"
     # Loop while search is in progress
     do{
         Write-host "Waiting for search to complete..."
         Start-Sleep -s 5
         $complianceSearch = Get-ComplianceSearch "RefinerTest"
     }while ($complianceSearch.Status -ne 'Completed')
     $refiners = $complianceSearch.Refiners | ConvertFrom-Json
     $errorTagProperties = $refiners.Entries | Get-Member -MemberType NoteProperty
     $partiallyIndexedRatio = $complianceSearch.UnindexedItems / $complianceSearch.Items
     $partiallyIndexedSizeRatio = $complianceSearch.UnindexedSize / $complianceSearch.Size
     " "
     "===== Partially indexed items ====="
     "         Total          Ratio"
     "Count    {0:N0}{1:P2}" -f $complianceSearch.Items.ToString("N0").PadRight(15, " "), $partiallyIndexedRatio
     "Size(GB) {0:N2}{1:P2}" -f ($complianceSearch.Size / 1GB).ToString("N2").PadRight(15, " "), $partiallyIndexedSizeRatio
     " "
     Write-Host ===== Reasons for partially indexed items =====
     foreach($errorTagProperty in $errorTagProperties)
     {
         $name = $refiners.Entries.($errorTagProperty.Name).Name
         $count = $refiners.Entries.($errorTagProperty.Name).TotalCount
         $frag = $name.Split("{_}")
         $errorTag = $frag[0]
         $fileType = $frag[1]
         if ($errorTag -ne $lastErrorTag)
         {
             $errorTag
         }
         "    " + $fileType + " => " + $count
         $lastErrorTag = $errorTag
     }
   ```

2. [Bağlan ve Uyumluluk & PowerShell'e.](/powershell/exchange/exchange-online-powershell)

3. Güvenlik & Uyumluluk Merkezi PowerShell'de, 1. adımda betiği kaydeden klasöre gidin ve betiği çalıştırın; örneğin:

   ```powershell
   .\PartiallyIndexedItems.ps1
   ```

Betik tarafından döndürülen çıktının bir örneği şu şekildedir.
  
![Komut dosyasından çıktı alınarak, kuruluşun kısmen dizine alan e-posta öğelerine maruz kalmakla ilgili bir rapor oluşturan örneği.](../media/aeab5943-c15d-431a-bdb2-82f135abc2f3.png)

> [!NOTE]
> Unutmayın:
>  
> - E-posta öğelerinin toplam sayısı ve boyutu ve kuruluşun kısmen dizine alan e-posta öğelerinin oranı (sayma ve boyuta göre).
> 
> - Hatanın meydana geldiği liste hata etiketleri ve ilgili dosya türleri.
  
## <a name="see-also"></a>Ayrıca bkz.

[eBulma'da kısmen dizine alan öğeler](partially-indexed-items-in-content-search.md)
