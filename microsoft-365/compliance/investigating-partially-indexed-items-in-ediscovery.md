---
title: eBulma'da kısmen dizine alınan öğeleri araştırma
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 06/14/2022
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
description: Kuruluşunuzdaki Exchange, SharePoint ve OneDrive İş kısmen dizine alınmış öğeleri (dizine alınmamış öğeler olarak da adlandırılır) yönetmeyi öğrenin.
ms.openlocfilehash: 528693febbb6d02f6ea143d94aaae154d3dfde7e
ms.sourcegitcommit: 1c8f54f9e7a7665bc10b5ef4a3d8c36e3e48f44c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/14/2022
ms.locfileid: "66078754"
---
# <a name="investigating-partially-indexed-items-in-ediscovery"></a>eBulma'da kısmen dizine alınan öğeleri araştırma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview uyumluluk portalı çalıştırdığınız bir eBulma araması, bir arama çalıştırdığınızda tahmini arama sonuçlarında otomatik olarak kısmen dizine alınan öğeler içerir. Kısmen dizine alınan öğeler, SharePoint ve OneDrive İş sitelerindeki posta kutusu öğeleri ve belgeleri Exchange ve herhangi bir nedenle arama için tamamen dizine eklenmedi. Çoğu e-posta iletisi ve site belgesi, [e-posta iletileri için Dizin oluşturma sınırları](limits-for-content-search.md#indexing-limits-for-email-messages) içinde olduğundan başarıyla dizinlenir. Ancak, bazı öğeler bu dizin oluşturma sınırlarını aşabilir ve kısmen dizine alınabilir. eBulma araması çalıştırdığınızda öğelerin arama için dizine alınamamalarının ve kısmen dizine alınan öğeler olarak döndürüllerinin diğer nedenleri şunlardır:
  
- E-posta iletilerinin ekli bir dosyası vardır ve bu dosya açılamaz; Bu, kısmen dizine alınan e-posta öğelerinin en yaygın nedenidir.

- E-posta iletisine çok fazla dosya iliştirildi.

- E-posta iletisine eklenmiş bir dosya çok büyük.

- Dosya türü dizin oluşturma için desteklenir, ancak belirli bir dosya için dizin oluşturma hatası oluştu.

Değişiklik gösterse de çoğu kuruluş müşterisi, topluca göre içeriğin %1'inden az, kısmen dizine alınan boyuta göre içeriğin %12'sinden daha az içeriğe sahiptir. Birim ile boyut arasındaki farkın nedeni, büyük dosyaların tamamen dizine alınamaz içerik içerme olasılığının daha yüksek olmasıdır.
  
## <a name="why-does-the-partially-indexed-item-count-change-for-a-search"></a>Kısmen dizine alınan öğe sayısı bir arama için neden değişiyor?

Bir eBulma araması çalıştırdıktan sonra, arama yapılan konumlardaki kısmen dizine alınan öğelerin toplam sayısı ve boyutu, aramanın ayrıntılı istatistiklerinde görüntülenen arama sonucu istatistiklerinde listelenir. Bunların arama istatistiklerinde  *dizinlenmemiş öğeler olarak adlandırıldıklarına*  dikkat edin. Aşağıda, arama sonuçlarında döndürülen kısmen dizine alınan öğelerin sayısını etkileyecek birkaç şey vardır:
  
- Bir öğe kısmen dizine eklenmişse ve arama sorgusuyla eşleşiyorsa, hem arama sonucu öğelerinin sayısına (hem de boyutuna) ve kısmen dizine alınan öğelere dahil edilir. Ancak, aynı aramanın sonuçları dışarı aktarıldığında, öğe yalnızca arama sonuçları kümesine eklenir; kısmen dizinlenmiş bir öğe olarak dahil değildir.

- SharePoint ve OneDrive sitelerinde bulunan kısmen dizinlenmiş öğeler, aramanın ayrıntılı istatistiklerinde görüntülenen kısmen dizinlenmiş öğelerin tahmininde yer *almaz*. Ancak, eBulma aramasının sonuçlarını dışarı aktardığınızda kısmen dizine alınan öğeler dışarı aktarılabilir. Örneğin, yalnızca sitelerde arama yaparsanız, kısmen dizine alınan tahmini öğe sayısı sıfır olur.
  
## <a name="calculating-the-ratio-of-partially-indexed-items-in-your-organization"></a>Kuruluşunuzda kısmen dizine alınan öğelerin oranını hesaplama

Kuruluşunuzun kısmen dizinlenmiş öğelere maruz kalmasını anlamak için, tüm posta kutularındaki tüm içerik için arama çalıştırabilirsiniz (boş bir anahtar sözcük sorgusu kullanarak). Aşağıdaki örnekte, 1.629.904 (146,46 GB) tam dizine alınan öğe ve kısmen dizinlenmiş 10.025 (10,27 GB) öğe vardır.
  
![Kısmen dizine alınan öğeleri gösteren arama istatistikleri örneği.](../media/PartiallyIndexedItemsTest.png)
  
Aşağıdaki hesaplamaları kullanarak kısmen dizine alınan öğelerin yüzdesini belirleyebilirsiniz.
  
 **Kuruluşunuzda kısmen dizine alınan öğelerin oranını hesaplamak için:**

`(Total number of partially indexed items/Total number of items) x 100`

`(10025/1629904) x 100 = 0.62%`

Önceki örnekteki arama sonuçları kullanıldığında, tüm posta kutuları öğelerinin %0,62'sinde kısmen dizin oluşturulur.
  
 **Kuruluşunuzda kısmen dizine alınan öğelerin boyutunun yüzdesini hesaplamak için:**

`(Size of all partially indexed items/Size of all items) x 100`

`(10.27 GB/146.46 GB) x 100 = 7.0%`

Bu nedenle, önceki örnekte posta kutusu öğelerinin toplam boyutunun %7'sini kısmen dizine alınan öğeler oluşturur. Daha önce belirtildiği gibi çoğu kuruluş müşterisi, topluca göre içeriğin %1'inden az ve kısmen dizinlenmiş boyuta göre içeriğin %12'sinden daha az içeriğe sahiptir.

## <a name="working-with-partially-indexed-items"></a>Kısmen dizinlenmiş öğelerle çalışma

İlgili bilgileri içermediklerini doğrulamak için kısmen dizine alınan öğeleri incelemeniz gerektiğinde, kısmen dizine alınan öğeler hakkında bilgi içeren [bir içerik arama raporunu dışarı aktarabilirsiniz](export-a-content-search-report.md) . İçerik arama raporunu dışarı aktarırken, kısmen dizine alınan öğeler içeren dışarı aktarma seçeneklerinden birini seçtiğinizden emin olun.
  
![Kısmen dizine alınan öğeleri dışarı aktarmak için ikinci veya üçüncü seçeneği belirtin.](../media/PartiallyIndexedItemsExportOptions.png)
  
Bu seçeneklerden birini kullanarak eBulma arama sonuçlarını veya arama raporunu dışarı aktardığınızda, dışarı aktarma işlemi Unindexed Items.csv adlı bir rapor içerir. Bu rapor, ResultsLog.csv dosyasıyla aynı bilgilerin çoğunu içerir; Ancak, Unindexed Items.csv dosyası kısmen dizine alınmış öğelerle ilgili iki alan da içerir: **Hata Etiketleri** ve **Hata Özellikleri**. Bu alanlar, kısmen dizine alınan her öğe için dizin oluşturma hatası hakkında bilgi içerir. Bu iki alandaki bilgileri kullanmak, belirli bir dizin oluşturma hatasının araştırmanızı etkileyip etkilemediğini belirlemenize yardımcı olabilir. 

> [!NOTE]
> Unindexed Items.csv dosyası, **Hata Türü** ve **Hata İletisi** adlı alanları da içerir. Bunlar, **Hata Etiketleri** ve **Hata Özellikleri** alanlarındaki bilgilere benzer ancak daha az ayrıntılı bilgi içeren bilgiler içeren eski alanlardır. Bu eski alanları güvenle yoksayabilirsiniz.
  
## <a name="errors-related-to-partially-indexed-items"></a>Kısmen dizine alınan öğelerle ilgili hatalar

Hata etiketleri, hata ve dosya türü olan iki bilgi parçasından oluşur. Örneğin, bu hata/dosya türü çiftinde:

```text
 parseroutputsize_xls
```

 `parseroutputsize` hatadır ve `xls` hatanın oluştuğu dosyanın dosya türüdür. Dosya türünün tanınmadığı veya dosya türünün hataya uygulanmadığı durumlarda, dosya türünün yerine değeri `noformat` görürsünüz.
  
Aşağıda dizin oluşturma hatalarının listesi ve hatanın olası nedeninin açıklaması yer alır.
  
| Hata etiketi | Açıklama |
|:-----|:-----|
| `attachmentcount` <br/> |Bir e-posta iletisinde çok fazla ek vardı ve bu eklerden bazıları işlenmedi.  <br/> |
| `attachmentdepth` <br/> |İçerik seçici ve belge ayrıştırıcısı, diğer eklerin içine yerleştirilmiş çok fazla sayıda ek düzeyi buldu. Bu eklerden bazıları işlenmedi.  <br/> |
| `attachmentrms` <br/> |RMS korumalı olduğundan bir ekin kodu çözülemedi.  <br/> |
| `attachmentsize` <br/> |E-posta iletisine eklenmiş bir dosya çok büyük ve işlenemedi.  <br/> |
| `indexingtruncated` <br/> |İşlenen e-posta iletisi dizine yazılırken, dizine alınabilir özelliklerden biri çok büyük ve kesildi. Kesilen özellikler Hata Özellikleri alanında listelenir.  <br/> |
| `invalidunicode` <br/> |Geçerli Unicode olarak işlenemeyen bir e-posta iletisi metni içeriyordu. Bu öğe için dizin oluşturma tamamlanmamış olabilir.  <br/> |
| `parserencrypted` <br/> |Ek veya e-posta iletisinin içeriği şifrelenir ve Microsoft 365 içeriğin kodunu çözemedi.  <br/> |
| `parsererror` <br/> |Ayrıştırma sırasında bilinmeyen bir hata oluştu. Bu durum genellikle bir yazılım hatasından veya hizmet kilitlenmesinden kaynaklar.  <br/> |
| `parserinputsize` <br/> |Ek ayrıştırıcının işleyemeyecek kadar büyük olduğunu ve bu ekin ayrıştırılması gerçekleşmedi veya tamamlanmadı.  <br/> |
| `parsermalformed` <br/> |Ek yanlış biçimlendirilmiş ve ayrıştırıcı tarafından işlenemedi. Bu sonuç eski dosya biçimlerinden, uyumsuz yazılımlar tarafından oluşturulan dosyalardan veya iddia edilenden başka bir şeymiş gibi davranan virüslerden kaynaklanabilir.  <br/> |
| `parseroutputsize` <br/> |Ek ayrıştırma çıktısı çok büyük ve kesilmesi gerekiyordu.  <br/> |
| `parserunknowntype` <br/> |Ekin Microsoft 365 algılayamadık bir dosya türü vardı.  <br/> |
| `parserunsupportedtype` <br/> |Ekin Office 365 algılayabildiği bir dosya türü vardı, ancak bu dosya türünün ayrıştırılması desteklenmiyor.  <br/> |
| `propertytoobig` <br/> |Exchange Store'daki bir e-posta özelliğinin değeri alınamayacak kadar büyük ve ileti işlenemedi. Bu genellikle yalnızca bir e-posta iletisinin gövde özelliğine olur.  <br/> |
| `retrieverrms` <br/> |İçerik alıcı, RMS korumalı bir iletinin kodunu çözemedi.  <br/> |
| `wordbreakertruncated` <br/> |Dizin oluşturma sırasında belgede çok fazla sözcük tanımlandı. Sınıra ulaşıldığında özelliğin işlenmesi durduruldu ve özellik kesildi.  <br/> |

Hata alanları, Hata Etiketleri alanında listelenen işleme hatasından hangi alanların etkilendiğini açıklar. veya `participants`gibi `subject` bir özelliği arıyorsanız, iletinin gövdesindeki hatalar aramanızın sonuçlarını etkilemez. Bu, tam olarak hangi kısmen dizine alınan öğeleri daha fazla araştırmanız gerekebileceğini belirlerken yararlı olabilir.

<!--
## Using a PowerShell script to determine your organization's exposure to partially indexed email items

The following steps show you how to run a PowerShell script that searches for all items in all Exchange mailboxes, and then generates a report about your organization's ratio of partially indexed email items (by count and by size) and displays the number of items (and their file type) for each indexing error that occurs. Use the error tag descriptions in the previous section to identify the indexing error.
  
1. Save the following text to a Windows PowerShell script file by using a filename suffix of .ps1; for example, `PartiallyIndexedItems.ps1`.

   ```powershell
     write-host "**************************************************"
     write-host "     Security & Compliance PowerShell      " -foregroundColor yellow -backgroundcolor darkgreen
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

2. [Connect to Security & Compliance PowerShell](/powershell/exchange/exchange-online-powershell).

3. In Security & Compliance PowerShell, go to the folder where you saved the script in step 1, and then run the script; for example:

   ```powershell
   .\PartiallyIndexedItems.ps1
   ```

Here's an example fo the output returned by the script.
  
![Example of output from script that generates a report on your organization's exposure to partially indexed email items.](../media/aeab5943-c15d-431a-bdb2-82f135abc2f3.png)

> [!NOTE]
> Note the following:
>  
> - The total number and size of email items, and your organization's ratio of partially indexed email items (by count and by size).
> 
> - A list error tags and the corresponding file types for which the error occurred.
-->

## <a name="see-also"></a>Ayrıca bkz.

[eBulma'da kısmen dizine alınan öğeler](partially-indexed-items-in-content-search.md)
