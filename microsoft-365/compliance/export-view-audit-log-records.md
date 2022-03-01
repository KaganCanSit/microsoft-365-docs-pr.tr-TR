---
title: Denetim günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Bu makalede, denetim günlüğü kayıtlarını dışarı aktarmayı, yapılandırmayı ve görüntülemeyi Microsoft 365 öğrenirsiniz.
ms.openlocfilehash: efb71ea0ff0b7098c3524707cff101d7ba25877f
ms.sourcegitcommit: 678e827a1c3bc9f4edfc48003f9b29f7bbf20ab5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2021
ms.locfileid: "63021578"
---
# <a name="export-configure-and-view-audit-log-records"></a>Denetim günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme

Denetim günlüğünde arama yaptıktan ve arama sonuçlarını bir CSV dosyasına indirdikten sonra, dosyada Her olay hakkında ek bilgiler içeren **Denetim** Verileri adlı bir sütun bulunur. Bu sütundaki veriler, özellik *:* değer çiftleri virgülle ayrılmış olarak yapılandırılan birden çok özelliği içeren JSON nesnesi olarak biçimlendirildi. Excel'daki Power Query Düzenleyicisi'nde JSON dönüştürme özelliğini kullanarak Denetim Verileri sütunundaki JSON nesnesinde yer alan her özelliği birden çok sütuna  bölebilir ve bu şekilde her özelliğin kendi sütunu olur. Bu, bu özelliklerden birini veya birden fazlasını sıralamanıza ve filtrelemenıza olanak sağlar ve bu, istediğiniz belirli denetim verilerini hızla bulamanıza yardımcı olabilir.

## <a name="step-1-export-audit-log-search-results"></a>1. Adım: Denetim günlüğü arama sonuçlarını dışarı aktarma

İlk adım denetim günlüğünde arama yapmak ve sonra sonuçları virgülle ayrılmış değer (CSV) dosyasıyla yerel bilgisayarınıza dışarı aktarmanızdır.
  
1. Denetim günlüğü [arama çalıştırın ve](search-the-audit-log-in-security-and-compliance.md#search-the-audit-log) gerekli sonuçları elde inceye kadar gerekiyorsa arama ölçütlerini düzeltin.

2. Arama sonuçları sayfasında Dışarı Aktar Tüm **sonuçları** **yükle'ye** >  tıklayın.

   ![Tüm sonuçları indir'e tıklayın.](../media/ExportAuditSearchResults.png)

   Bu seçenek, 1. adımda doğru ilerleyen denetim günlüğü aramalarından tüm denetim kayıtlarını dışarı aktarır ve denetim günlüğünden ham verileri CSV dosyasına ekler. İndirme dosyasının büyük bir arama için hazırlanması biraz zaman alır. Büyük dosyalar tüm etkinlikler için aramalarda veya geniş bir tarih aralığı kullanılırken ortaya çıkan sonuçlardır.

3. Dışarı aktarma işlemi tamamlandıktan sonra, pencerenin en üstünde CSV dosyasını açmanızı ve yerel bilgisayarınıza kaydetmenizi istediğiniz bir ileti görüntülenir. Csv dosyasına, İndirmeler klasöründen de erişebilirsiniz.

   > [!NOTE]
   > Tek bir denetim günlüğü aramalarından CSV dosyasına en çok 50.000 girdi indirebilirsiniz. CSV dosyasına 50.000 girdi indirilirse, büyük olasılıkla arama ölçütlerine uyan 50.000'den çok olay olduğunu varsayabilirsiniz. Bu sınırdan fazlasını dışarı aktarmayı denemek için, denetim günlüğü kayıtlarının sayısını azaltmak için daha dar bir tarih aralığı kullanmayı deneyin. 50.000'den fazla girdiyi dışarı aktaracak şekilde, daha küçük tarih aralıklarında birden çok arama çalıştırmaya gerek kullanabilirsiniz.

## <a name="step-2-format-the-exported-audit-log-using-the-power-query-editor"></a>2. Adım: Power Query Düzenleyicisi'ni kullanarak dışarı aktaran denetim günlüğünü biçimlendirme

Sonraki adım, denetim **Verileri** sütunundaki JSON nesnesinde yer alan her özelliği kendi sütununa bölmek için Excel'de Power Query Düzenleyicisi'nde JSON dönüştürme özelliğini kullanmaktır. Ardından, kayıtları belirli özelliklerin değerlerine göre görüntülemek için sütunları filtrelersiniz. Bu, istediğiniz belirli denetim verilerini hızla bulamanıza yardımcı olabilir.

1. Office 365, Excel 2019 veya Excel'da boş bir çalışma kitabı Excel 2016.

2. Veri **sekmesinin** Veri Al ve **Dönüştür & grubunda** Metinden **/CSV'den seçeneğini tıklatın**.

    ![Veri sekmesinde Metinden/CSV'den seçeneğini tıklatın.](../media/JSONTransformOpenCSVFile.png)

3. 1. Adımda indirdiğiniz CSV dosyasını açın.

4. Görüntülenen pencerede Verileri **Dönüştür'e tıklayın**.

   ![Verileri Dönüştür'e tıklayın.](../media/JSONOpenPowerQuery.png)

   CSV dosyası Sorgu **Düzenleyicisi'nde açılır**. Dört sütun vardır: **Oluşturma Tarihi**, **Kullanıcı Kimlikleri**, **İşlemler** ve **Denetim Verileri**. **Denetim Verileri sütunu**, birden çok özellik içeren bir JSON nesnesidir. Sonraki adım, JSON nesnesinde her özellik için bir sütun oluşturmaktır.

5. Denetim Verileri sütununda başlığı sağ tıklatın, **Dönüştür'i** **ve** **JSON'u tıklatın**. 

   ![Denetim Verileri sütununa sağ tıklayın, Dönüştür'e tıklayın ve JSON'u seçin.](../media/JSONTransform.png)

6. Denetim Verileri sütunlarının sağ üst **köşesinde** , genişletme simgesine tıklayın.

   ![Denetim Verileri sütununda genişlet simgesine tıklayın.](../media/JSONTransformExpandIcon.png)

   Denetim Verileri sütunundaki JSON nesnelerindeki özelliklerin kısmi **bir** listesi görüntülenir.

7. Denetim **Verileri sütununda** JSON nesnelerinin tüm özelliklerini görüntülemek için Daha fazla **yükle'ye** tıklayın.

   ![JSON nesnesinde tüm özellikleri görüntülemek için Daha fazla yükle'ye tıklayın.](../media/JSONTransformLoadJSONProperties.png)

   Dahil etmek istemediğiniz tüm özelliğin yanındaki onay kutusunun seçimini kaldırabilirsiniz. Araştırmanız için yararlı olmayan sütunları eleyerek denetim günlüğünde görüntülenen veri miktarını azaltmanın iyi bir yoludur. 

   > [!NOTE]
   > Önceki ekran görüntüsünde görüntülenen JSON özelliklerinde (Daha fazla yükle'ye tıklarsanız **), CSV** dosyasındaki ilk 1.000 satırda yer alan Denetim Verileri sütununda bulunan özellikler temel alınarak kullanılır. İlk 1.000 satırdan sonra kayıtlarda farklı JSON özellikleri varsa, **Denetim** Verileri sütunu birden çok sütuna bölünüyorsa bu özellikler (ve ilgili bir sütun) dahil edilir. Bunu önlemeye yardımcı olmak için, denetim günlüğü aramasını yeniden çalıştırmayı ve daha az kayıt döndürülması için arama ölçütlerini daraltmayı göz önünde bulundurabilirsiniz. Bir diğer geçici çözüm de, Denetim Verileri  sütununda JSON nesnesini dönüştürmeden önce, (yukarıdaki 5. adımı gerçekleştirmeden önce) İşlemler sütunundaki öğeleri **filtrelemektir**.

   > [!TIP]
   > AuditData.affectedItems gibi bir liste içindeki özniteliği görüntülemek için, özniteliği almak istediğiniz sütunun sağ üst köşesindeki Genişlet simgesine tıklayın ve Yeni Satıra  **Genişlet'i seçin**.  Burada bir kayıt olur ve sütunun sağ üst köşesindeki Genişlet  simgesine tıklar, öznitelikleri genişletilebilir ve ayıklamak istediğiniz kaydı seçin.

8. Seçilen her JSON özelliği için eklenen sütunların başlığını biçimlendirmek üzere aşağıdaki şeylerden birini yapın.

    - JSON **özelliğinin adını sütun adları olarak kullanmak** için Özgün sütun adını ön ek olarak kullan onay kutusunun seçimini kaldırın; örneğin, **RecordType** veya **SourceFileName**.

    - Denetim Verileri **ön eklerini sütun adlara** eklemek için Özgün sütun adını ön ek olarak kullan onay kutusunu seçili bırakın; örneğin, **AuditData.RecordType** veya **AuditData.SourceFileName**.

9. **Tamam**'a tıklayın.

    Denetim **Verileri sütunu** birden çok sütuna ayrılır. Her yeni sütun Denetim Verileri JSON nesnesinde bir özellik ifade eder. Sütundaki her satır özelliğin değerini içerir. Özellik bir değer içeriyorsa, *null değer* görüntülenir. Boş Excel boş değer içeren hücreler boştur.
  
10. Power Query **Düzenleyicisi'ni** **kapatmak ve dönüştürülmüş CSV &** bir çalışma kitabında açmak için, Giriş sekmesinde Kapat ve Yükle'Excel tıklayın.

## <a name="use-powershell-to-search-and-export-audit-log-records"></a>Denetim günlüğü kayıtlarında arama yapmak ve dışarı aktarma için PowerShell kullanma

Microsoft 365 uyumluluk merkezi'de denetim günlüğü arama aracını kullanmak yerine, Exchange Online PowerShell'de [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) cmdlet'ini kullanarak denetim günlüğü aramanın sonuçlarını CSV dosyasına aktarabilirsiniz. Ardından, Power Query düzenleyicisini kullanarak denetim günlüğünü biçimlendirmek için 2. Adımda açıklanan yordamın aynısını izleyin. PowerShell cmdlet'ini kullanmanın bir avantajı, RecordType parametresini kullanarak belirli bir hizmetten olayları *arayabilirsiniz* . Aşağıda, PowerShell kullanarak denetim kayıtlarını CSV dosyasına aktarmaya ve böylelikle Power Query düzenleyicisini kullanarak Denetim **Verileri** sütunundaki JSON nesnesini 2. Adımda açıklandığı gibi dönüştürebilirsiniz.

Bu örnekte, en son paylaşım işlemleriyle ilgili tüm kayıtları geri SharePoint çalıştırın.

```powershell
$auditlog = Search-UnifiedAuditLog -StartDate 06/01/2019 -EndDate 06/30/2019 -RecordType SharePointSharingOperation
```

```powershell
$auditlog | Select-Object -Property CreationDate,UserIds,RecordType,AuditData | Export-Csv -Path c:\AuditLogs\PowerShellAuditlog.csv -NoTypeInformation
```

Arama sonuçları dört sütun içeren *PowerShellAuditlog* adlı bir CSV dosyasına dışarı aktarıldı: CreationDate, UserIds, RecordType, AuditData).

RecordType parametresinin değeri olarak kayıt türünün ad veya enum değerini de *kullanabilirsiniz* . Kayıt türü adlarının ve karşılık gelen enum değerlerinin listesi için, Office 365 Management Activity API şemasındaki *AuditLogRecordType* [tablosuna bakın](/office/office-365-management-api/office-365-management-activity-api-schema#enum-auditlogrecordtype---type-edmint32).

*RecordType* parametresi için yalnızca tek bir değer include. Diğer kayıt türlerinin denetim kayıtlarını aramak için, farklı bir kayıt türü belirtmek ve bu sonuçları özgün CSV dosyasına eklemek için önceki iki komutu yeniden çalıştırmanız gerekir. Örneğin, aynı tarih aralığından SharePoint dosya etkinlikleri eklemek için aşağıdaki iki komutu PowerShellAuditlog.csv çalıştırabilirsiniz.

```powershell
$auditlog = Search-UnifiedAuditLog -StartDate 06/01/2019 -EndDate 06/30/2019 -RecordType SharePointFileOperation
```

```powershell
$auditlog | Select-Object -Property CreationDate,UserIds,RecordType,AuditData | Export-Csv -Append -Path c:\AuditLogs\PowerShellAuditlog.csv -NoTypeInformation
```

## <a name="tips-for-exporting-and-viewing-the-audit-log"></a>İpuçları ve denetim günlüğünü görüntülemeye uygun bir veri alanı

Aşağıda, JSON dönüştürme özelliğini kullanarak Denetim Verileri sütununu birden çok sütuna bölmek için denetim günlüğünü dışarı aktarma ve görüntülemeyle ilgili bazı  ipuçları ve örnekler verilmiştir.

- Belirli bir **hizmet veya** işlevsel alandan yalnızca kayıtları görüntülemek için RecordType sütununa filtre uygulama. Örneğin, paylaşımla ilgili SharePoint göstermek için **14**(paylaşım etkinlikleri tarafından tetiklenen kayıtların enum değeri) SharePoint seçersiniz. **RecordType** sütununda görüntülenen enum değerlerine karşılık gelen hizmetlerin listesi için bkz [. Denetim günlüğünde ayrıntılı özellikler](detailed-properties-in-the-office-365-audit-log.md).

- Belirli **etkinliklere** yönelik kayıtları görüntülemek için İşlemler sütununa filtre uygulama. Denetim günlüğü arama aracında aramalanabilir bir faaliyete karşılık gelen işlemlerin listesi Microsoft 365 uyumluluk merkezi, Denetim günlüğünde arama'nın "Denetlenen etkinlikler" [bölümüne bakın](search-the-audit-log-in-security-and-compliance.md#audited-activities).
