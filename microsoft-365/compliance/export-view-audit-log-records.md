---
title: Denetim günlüğü kayıtlarını dışa aktarma, yapılandırma ve görüntüleme
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 0d4d0f35-390b-4518-800e-0c7ec95e946c
ms.custom: seo-marvel-apr2020
description: Bu makalede, Microsoft 365 denetim günlüğü kayıtlarını dışarı aktarmayı, yapılandırmayı ve görüntülemeyi öğreneceksiniz.
ms.openlocfilehash: 73771e41c785bbf74c843821400b65a7049b902a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098096"
---
# <a name="export-configure-and-view-audit-log-records"></a>Denetim günlüğü kayıtlarını dışa aktarma, yapılandırma ve görüntüleme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Denetim günlüğünde arama yaptıktan ve arama sonuçlarını bir CSV dosyasına indirdikten sonra, dosya her olay hakkında ek bilgiler içeren **AuditData** adlı bir sütun içerir. Bu sütundaki veriler, virgülle ayrılmış *property:value* çiftleri olarak yapılandırılan birden çok özellik içeren bir JSON nesnesi olarak biçimlendirilir. Excel'daki Power Query Düzenleyicisi JSON dönüştürme özelliğini kullanarak **AuditData** sütunundaki JSON nesnesindeki her özelliği birden çok sütuna bölerek her özelliğin kendi sütununa sahip olmasını sağlayabilirsiniz. Bu, aradığınız denetim verilerini hızla bulmanıza yardımcı olabilecek bu özelliklerden birini veya daha fazlasını sıralamanıza ve filtrelemenize olanak tanır.

## <a name="step-1-export-audit-log-search-results"></a>1. Adım: Denetim günlüğü arama sonuçlarını dışarı aktarma

İlk adım, denetim günlüğünde arama yapmak ve ardından sonuçları virgülle ayrılmış değer (CSV) dosyasında yerel bilgisayarınıza aktarmaktır.
  
1. [Bir denetim günlüğü araması](search-the-audit-log-in-security-and-compliance.md#search-the-audit-log) çalıştırın ve istediğiniz sonuçları elde edene kadar gerekirse arama ölçütlerini düzeltin.

2. Arama sonuçları sayfasında **Dışarı Aktar** >  **Tüm sonuçları indir'e** tıklayın.

   ![Tüm sonuçları indir'e tıklayın.](../media/ExportAuditSearchResults.png)

   Bu seçenek, 1. adımda çalıştırdığınız denetim günlüğü aramasından tüm denetim kayıtlarını dışarı aktarır ve denetim günlüğündeki ham verileri csv dosyasına ekler. İndirme dosyasını büyük bir arama için hazırlamak biraz zaman alır. Tüm etkinlikler aranırken veya geniş bir tarih aralığı kullanılırken büyük dosyalar ortaya çıkacaktır.

3. Dışarı aktarma işlemi tamamlandıktan sonra pencerenin üst kısmında CSV dosyasını açmanızı ve yerel bilgisayarınıza kaydetmenizi isteyen bir ileti görüntülenir. CSV dosyasına İndirmeler klasöründen de erişebilirsiniz.

   > [!NOTE]
   > Tek bir denetim günlüğü aramasından CSV dosyasına en fazla 50.000 girdi indirebilirsiniz. CSV dosyasına 50.000 girdi indirilirse, büyük olasılıkla arama ölçütlerine uyan 50.000'den fazla olay olduğunu varsayabilirsiniz. Bu sınırdan daha fazlasını dışarı aktarmak için, denetim günlüğü kayıtlarının sayısını azaltmak için daha dar bir tarih aralığı kullanmayı deneyin. 50.000'den fazla girişi dışarı aktarmak için daha küçük tarih aralıklarıyla birden çok arama çalıştırmanız gerekebilir.

## <a name="step-2-format-the-exported-audit-log-using-the-power-query-editor"></a>2. Adım: Power Query Düzenleyicisi kullanarak dışarı aktarılan denetim günlüğünü biçimlendirme

Sonraki adım, **AuditData** sütunundaki JSON nesnesindeki her özelliği kendi sütununa bölmek için Excel'deki Power Query Düzenleyicisi JSON dönüştürme özelliğini kullanmaktır. Ardından belirli özelliklerin değerlerine göre kayıtları görüntülemek için sütunları filtreleyebilirsiniz. Bu, aradığınız denetim verilerini hızla bulmanıza yardımcı olabilir.

1. Office 365, Excel 2019 veya Excel 2016 için Excel'de boş bir çalışma kitabı açın.

2. **Veri** sekmesinin **Veri Al & Dönüştürme** şerit grubunda **Metinden/CSV'den'e** tıklayın.

    ![Veri sekmesinde Metinden/CSV'den'e tıklayın.](../media/JSONTransformOpenCSVFile.png)

3. 1. Adımda indirdiğiniz CSV dosyasını açın.

4. Görüntülenen pencerede **Verileri Dönüştür'e** tıklayın.

   ![Verileri Dönüştür'e tıklayın.](../media/JSONOpenPowerQuery.png)

   CSV dosyası **Sorgu Düzenleyicisi** açılır. Dört sütun vardır: **CreationDate**, **UserIds**, **Operations** ve **AuditData**. **AuditData** sütunu, birden çok özellik içeren bir JSON nesnesidir. Sonraki adım, JSON nesnesindeki her özellik için bir sütun oluşturmaktır.

5. **AuditData** sütununda başlığa sağ tıklayın, **Dönüştür'e** ve ardından **JSON'a** tıklayın. 

   ![AuditData sütununa sağ tıklayın, Dönüştür'e tıklayın ve ardından JSON'ı seçin.](../media/JSONTransform.png)

6. **AuditData** sütununun sağ üst köşesinde genişlet simgesine tıklayın.

   ![AuditData sütununda genişlet simgesine tıklayın.](../media/JSONTransformExpandIcon.png)

   **AuditData** sütunundaki JSON nesnelerindeki özelliklerin kısmi listesi görüntülenir.

7. **AuditData** sütunundaki JSON nesnelerindeki tüm özellikleri görüntülemek için **Daha fazla yükle'ye** tıklayın.

   ![JSON nesnesindeki tüm özellikleri görüntülemek için Daha fazla yükle'ye tıklayın.](../media/JSONTransformLoadJSONProperties.png)

   Eklemek istemediğiniz herhangi bir özelliğin yanındaki onay kutusunun seçimini kaldırabilirsiniz. Araştırmanız için yararlı olmayan sütunları ortadan kaldırmak, denetim günlüğünde görüntülenen veri miktarını azaltmanın iyi bir yoludur. 

   > [!NOTE]
   > Önceki ekran görüntüsünde görüntülenen JSON özellikleri ( **Daha fazla yükle'ye** tıkladıktan sonra), CSV dosyasındaki ilk 1.000 satırdaki **AuditData** sütununda bulunan özellikleri temel alır. Kayıtlarda ilk 1.000 satırdan sonra farklı JSON özellikleri varsa, **AuditData** sütunu birden çok sütuna bölündüğünde bu özellikler (ve buna karşılık gelen sütun) dahil edilmeyecektir. Bunu önlemeye yardımcı olmak için denetim günlüğü aramasını yeniden çalıştırmayı ve daha az kayıt döndürülecek şekilde arama ölçütlerini daraltmayı göz önünde bulundurun. Bir diğer geçici çözüm de **, AuditData** sütunundaki JSON nesnesini dönüştürmeden önce satır sayısını azaltmak için **İşlemler** sütunundaki öğeleri filtrelemektir (yukarıdaki 5. adımı gerçekleştirmeden önce).

   > [!TIP]
   > AuditData.AffectedItems gibi bir listedeki özniteliği görüntülemek için, özniteliğini çekmek istediğiniz sütunun sağ üst köşesindeki **Genişlet** simgesine tıklayın ve ardından **Yeni Satıra Genişlet'i** seçin.  Buradan bir kayıt olur ve sütunun sağ üst köşesindeki **Genişlet** simgesine tıklayabilir, öznitelikleri görüntüleyebilir ve görüntülemek veya ayıklamak istediğiniz kaydı seçebilirsiniz.

8. Seçilen her JSON özelliği için eklenen sütunların başlığını biçimlendirmek için aşağıdakilerden birini yapın.

    - JSON özelliğinin **adını sütun adları olarak kullanmak için Ön ek olarak özgün sütun adını kullan** onay kutusunun seçimini kaldırın; örneğin, **RecordType** veya **SourceFileName**.

    - Sütun adlarına AuditData **ön ekini eklemek için Özgün sütun adını önek olarak kullan** onay kutusunu seçili bırakın; örneğin, **AuditData.RecordType** veya **AuditData.SourceFileName**.

9. **Tamam**'a tıklayın.

    **AuditData** sütunu birden çok sütuna bölünür. Her yeni sütun AuditData JSON nesnesindeki bir özelliğe karşılık gelir. Sütundaki her satır özelliğin değerini içerir. Özellik bir değer içermiyorsa *null* değer görüntülenir. Excel,null değerleri olan hücreler boştur.
  
10. **Giriş** sekmesinde, Power Query Düzenleyicisi kapatmak ve dönüştürülmüş CSV dosyasını Excel çalışma kitabında açmak için **Yükle & Kapat'a** tıklayın.

## <a name="use-powershell-to-search-and-export-audit-log-records"></a>Denetim günlüğü kayıtlarını aramak ve dışarı aktarmak için PowerShell kullanma

Microsoft Purview uyumluluk portalında denetim günlüğü arama aracını kullanmak yerine, Exchange Online PowerShell'de [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) cmdlet'ini kullanarak denetim günlüğü aramasının sonuçlarını CSV dosyasına aktarabilirsiniz. Ardından, Power Query düzenleyicisini kullanarak denetim günlüğünü biçimlendirmek için 2. Adım'da açıklanan yordamın aynısını izleyebilirsiniz. PowerShell cmdlet'ini kullanmanın avantajlarından biri, *RecordType* parametresini kullanarak belirli bir hizmetten gelen olayları aramanızdır. Aşağıda, Denetim Kayıtları'nı CSV dosyasına aktarmak için PowerShell'i kullanarak 2. Adımda açıklandığı gibi **AuditData** sütunundaki JSON nesnesini dönüştürmek için Power Query düzenleyicisini kullanabileceğiniz birkaç örnek verilmiştir.

Bu örnekte, SharePoint paylaşım işlemleriyle ilgili tüm kayıtları döndürmek için aşağıdaki komutları çalıştırın.

```powershell
$auditlog = Search-UnifiedAuditLog -StartDate 06/01/2019 -EndDate 06/30/2019 -RecordType SharePointSharingOperation
```

```powershell
$auditlog | Select-Object -Property CreationDate,UserIds,RecordType,AuditData | Export-Csv -Path c:\AuditLogs\PowerShellAuditlog.csv -NoTypeInformation
```

Arama sonuçları dört sütun içeren *PowerShellAuditlog* adlı bir CSV dosyasına aktarılır: CreationDate, UserIds, RecordType, AuditData).

Kayıt türünün adını veya numaralandırma değerini *RecordType* parametresinin değeri olarak da kullanabilirsiniz. Kayıt türü adlarının ve karşılık gelen sabit listesi değerlerinin listesi için, [Office 365 Yönetim Etkinliği API'sinin şemasındaki](/office/office-365-management-api/office-365-management-activity-api-schema#enum-auditlogrecordtype---type-edmint32) *AuditLogRecordType* tablosuna bakın.

*RecordType* parametresi için yalnızca tek bir değer ekleyebilirsiniz. Diğer kayıt türlerinin denetim kayıtlarını aramak için, önceki iki komutu yeniden çalıştırarak farklı bir kayıt türü belirtmeniz ve bu sonuçları özgün CSV dosyasına eklemeniz gerekir. Örneğin, aynı tarih aralığındaki SharePoint dosya etkinliklerini PowerShellAuditlog.csv dosyasına eklemek için aşağıdaki iki komutu çalıştırırsınız.

```powershell
$auditlog = Search-UnifiedAuditLog -StartDate 06/01/2019 -EndDate 06/30/2019 -RecordType SharePointFileOperation
```

```powershell
$auditlog | Select-Object -Property CreationDate,UserIds,RecordType,AuditData | Export-Csv -Append -Path c:\AuditLogs\PowerShellAuditlog.csv -NoTypeInformation
```

## <a name="tips-for-exporting-and-viewing-the-audit-log"></a>Denetim günlüğünü dışarı aktarmak ve görüntülemek için İpuçları

**Aşağıda, AuditData** sütununu birden çok sütuna bölmek için JSON dönüştürme özelliğini kullanmadan önce ve sonra denetim günlüğünü dışarı aktarma ve görüntülemeye ilişkin bazı ipuçları ve örnekler verilmiştir.

- Yalnızca belirli bir hizmet veya işlevsel alandaki kayıtları görüntülemek için **RecordType** sütununu filtreleyin. Örneğin, SharePoint paylaşımıyla ilgili olayları göstermek için **14** 'i (SharePoint paylaşım etkinlikleri tarafından tetiklenen kayıtların numaralandırma değeri) seçersiniz. **RecordType** sütununda görüntülenen numaralandırma değerlerine karşılık gelen hizmetlerin listesi için [denetim günlüğündeki Ayrıntılı özellikler bölümüne](detailed-properties-in-the-office-365-audit-log.md) bakın.

- Belirli etkinliklerin kayıtlarını görüntülemek için **İşlemler** sütununu filtreleyin. Uyumluluk portalındaki denetim günlüğü arama aracında aranabilir bir etkinliğe karşılık gelen çoğu işlemin listesi için Denetim [günlüğünde arama](search-the-audit-log-in-security-and-compliance.md#audited-activities) yapma bölümündeki "Denetlenen etkinlikler" bölümüne bakın.
