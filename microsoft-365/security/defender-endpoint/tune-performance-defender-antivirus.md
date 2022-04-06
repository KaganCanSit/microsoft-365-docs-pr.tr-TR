---
title: Sistem için performans çözümleyicisi Microsoft Defender Virüsten Koruma
description: Performans ayarlamanın performansını ayarlama yordamını Microsoft Defender Virüsten Koruma.
keywords: ayarlama, performans, uç nokta için Microsoft Defender, Defender virüsten koruma
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: b5d9346746dba3b7b4c75909cb8e36e47c3c9d99
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472517"
---
# <a name="performance-analyzer-for-microsoft-defender-antivirus"></a>Sistem için performans çözümleyicisi Microsoft Defender Virüsten Koruma

**Geçerli olduğu yer:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**Performans çözümleyicisi Microsoft Defender Virüsten Koruma nedir?**

Bazı durumlarda, belirli dosyaları ve klasörleri tararken Microsoft Defender Virüsten Koruma performansı ayarlamaları gerekir. Performans çözümleyicisi, tek tek uç noktalarda performans sorunlarına hangi dosyaların, dosya uzantılarının ve süreçlerin neden olabileceğini belirlemenize yardımcı olan bir PowerShell komut satırı aracıdır. Bu bilgiler, performans sorunlarını daha iyi değerlendirmek ve düzeltme eylemleri uygulamak için kullanılabilir.

Çözümle ilgili bazı seçenekler şunlardır:

- Tarama zamanlarını etkileyen en önemli dosyalar
- Tarama zamanlarını etkileyen en önemli işlemler
- Tarama zamanlarını etkileyen en önemli dosya uzantıları
- Kombinasyon – örneğin, uzantı başına en çok dosya sayısı, dosya başına en çok tarama, işlem başına en çok tarama

## <a name="running-performance-analyzer"></a>Performans çözümleyicisi çalışıyor

Performans çözümleyicisi çalıştırmaya yönelik üst düzey işlem aşağıdaki adımları içerir:

1. Uç nokta üzerinde yer alan en düşük performans olaylarının Microsoft Defender Virüsten Koruma kaydını toplamak için performans çözümleyicisi çalıştırın.

   > [!NOTE]
   > **Microsoft-Microsoft Defender Virüsten Koruma-Engine** türünde olan yazılım olaylarının performansı, performans çözümleyicisi aracılığıyla kaydedilir.

2. Tarama sonuçlarını farklı kayıt raporları kullanarak çözümlenin.

## <a name="using-performance-analyzer"></a>Performans çözümleyicisi kullanma

Sistem olaylarını kaydetmeye başlamak için PowerShell'i yönetim modunda açın ve aşağıdaki adımları gerçekleştirin:

1. Kaydı başlatmak için aşağıdaki komutu çalıştırın:

   `New-MpPerformanceRecording -RecordTo <recording.etl>`
 
    burada `-RecordTo` parametre izleme dosyasının kaydedl olduğu tam yol konumunu belirtir. Daha fazla cmdlet bilgisi için bkz[. Microsoft Defender Virüsten Koruma cmdlet'leri.](/powershell/module/defender)

2. Performansı etkilediği düşünilen süreçler veya hizmetler varsa, ilgili görevleri yerine taşıyarak durumu yeniden üretin.

3. Kaydı **durdurmak ve** kaydetmek için ENTER tuşuna, kaydı **iptal etmek için Ctrl+C** tuşlarına basın.

4. Performans çözümleyicisi'nin parametresini kullanarak sonuçları çözümlenin `Get-MpPerformanceReport`. Örneğin, komutunu yürütürken `Get-MpPerformanceReport -Path <recording.etl> -TopFiles 3 -TopScansPerFile 10`, kullanıcıya performansı etkileyen ilk 3 dosya için ilk on taramanın listesi sağlanır. 

Komut satırı parametreleri ve seçenekleri hakkında daha fazla bilgi için [bkz. New-MpPerformanceRecording ve](#new-mpperformancerecording) [Get-MpPerformanceReport](#get-mpperformancereport).

> [!NOTE]
> Kaydı çalıştırma sırasında "Windows Performans Kaydedicisi zaten kaydediliyor olduğundan performans kaydı başlatılam" hatasını alırsanız, var olan izlemeyi yeni komutla durdurmak için aşağıdaki komutu çalıştırın: **wpr -cancel -instancename MSFT_MpPerformanceRecording**

### <a name="performance-tuning-data-and-information"></a>Verileri ve bilgileri performans ayarlama

Kullanıcı, sorguya bağlı olarak, tarama sayısı, süre (toplam/min/ortalama/mak/ortan), yol, süreç ve tarama nedeni ile ilgili verileri 2. Aşağıdaki resimde, etkiyi taramaya karşı basit bir sorgu olan ilk 10 dosyanın örnek çıktısı gösterilmiştir. 

:::image type="content" source="images/example-output.png" alt-text="Temel TopFiles sorgusu için örnek çıktı" lightbox="images/example-output.png":::

### <a name="additional-functionality-exporting-and-converting-to-csv-and-json"></a>Ek işlevler: CSV ve JSON'a aktarma ve dönüştürme

Performans çözümleyicisi sonuçları da CSV veya JSON dosyasına dışarı aktarıldı ve  dönüştürülebilir.
Örnek kodlar aracılığıyla "dışarı aktarma" ve "dönüştürme" işlemlerini açıklayan örnekler için aşağıdakilere bakın.

#### <a name="for-csv"></a>CSV için

- **Dışarı aktarma:**`(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:1000). TopScans | Export-CSV -Path:.\Repro-Install-Scans.csv -Encoding:UTF8 -NoTypeInformation`

- **Dönüştürmek için**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:100). TopScans | ConvertTo-Csv -NoTypeInformation`

#### <a name="for-json"></a>JSON için

- **Dönüştürmek için**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:1000). TopScans | ConvertTo-Json -Depth:1`

### <a name="requirements"></a>Gereksinimler
Microsoft Defender Virüsten Koruma çözümleyicisi aşağıdaki önkoşullara sahip:

- Desteklenen Windows sürümleri: Windows 10, Windows 11 ve Windows Server 2016 sürümleri
- Platform Sürümü: 4.18.2108.7+
- PowerShell Sürümü: PowerShell Sürüm 5.1, PowerShell ISE, Uzak PowerShell (4.18.2201.10+), PowerShell 7.x (4.18.2201.10+)

## <a name="powershell-reference"></a>PowerShell başvurusu
Bu cmdlet'lerin performansını ayarlamak için kullanılan iki yeni PowerShell Microsoft Defender Virüsten Koruma: 

- [New-MpPerformanceRecording](#new-mpperformancerecording)
- [Get-MpPerformanceReport](#get-mpperformancereport)


### <a name="new-mpperformancerecording"></a>New-MpPerformanceRecording

Aşağıdaki bölümde, yeni PowerShell cmdlet New-MpPerformanceRecording cmdlet'inin başvurusu açık almaktadır. Bu cmdlet, taramalarda performans Microsoft Defender Virüsten Koruma toplar.

#### <a name="syntax-new-mpperformancerecording"></a>Sözdizimi: New-MpPerformanceRecording

```powershell
New-MpPerformanceRecording -RecordTo <String >
```

#### <a name="description-new-mpperformancerecording"></a>Açıklama: New-MpPerformanceRecording
Cmdlet`New-MpPerformanceRecording`, taramaların performans Microsoft Defender Virüsten Koruma toplar. Bu performans kayıtları Microsoft-Antimalware-Engine ve NT kernel process olaylarını içerir ve [Get-MpPerformanceReport](#get-mpperformancereport) cmdlet'i kullanılarak toplama sonrasında çözümlenebilir.

Bu `New-MpPerformanceRecording` cmdlet, dosya performansında düşüşe neden olan sorunlu dosyalar hakkında bilgi Microsoft Defender Virüsten Koruma. Bu araç "OLDUĞU GIBI" sağlanır ve dışlamalar hakkında öneriler sağlamak üzere değildir. Dışlamalar, uç noktalarınız üzerinde koruma düzeyini düşürebilirsiniz. Varsa, dışlamalar dikkatli bir şekilde tanımlanmalıdır.

Performans çözümleyicisi hakkında daha fazla bilgi için bkz[. Performans Analizi](/windows-hardware/test/wpt/windows-performance-analyzer) bakın.

> [!IMPORTANT]
> Bu cmdlet, yükseltilmiş yönetici ayrıcalıkları gerektirir.

**Desteklenen işletim sistemi sürümleri**

Windows 10 ve sonraki bir sürümü deneyin.

> [!NOTE]
> Bu özellik, platform sürümü 4.18.2108.X ve sonraki sürümlerde kullanılabilir.

#### <a name="examples-new-mpperformancerecording"></a>Örnekler: New-MpPerformanceRecording

##### <a name="example-1-collect-a-performance-recording-and-save-it"></a>Örnek 1: Performans kaydını toplama ve kaydetme

```powershell
New-MpPerformanceRecording -RecordTo:.\Defender-scans.etl
```

Yukarıdaki komut bir performans kaydı toplar ve bunu belirtilen yola kaydeder: **.\Defender-scans.etl**.

##### <a name="example-2-collect-a-performance-recording-for-remote-powershell-session"></a>Örnek 2: Uzak PowerShell oturumu için performans kaydı toplama

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
New-MpPerformanceRecording -RecordTo C:\LocalPathOnServer02\trace.etl -Session $s
```

Yukarıdaki komut, Server02'de (Parametre Oturumu bağımsız değişkeni $s belirtildiği gibi) bir performans kaydı toplar ve bunu belirtilen yola kaydeder: **C:\LocalPathOnServer02\trace.etl** on Server02.

#### <a name="parameters-new-mpperformancerecording"></a>Parametreler: New-MpPerformanceRecording

##### <a name="-recordto"></a>-RecordTo
Microsoft Defender Kötü amaçlı yazılımlardan koruma performans kaydının kayded silinebilir olduğu konumu belirtir.

```yaml
Type: String
Position: Named
Default value: None
Accept pipeline input: False 
Accept wildcard characters: False
```

##### <a name="-session"></a>-Session 
Performans kaydı oluşturmak ve kaydetmek için gereken PSSession Microsoft Defender Virüsten Koruma belirtir. Bu parametreyi kullanırken RecordTo parametresi uzak makinede yerel yola başvurur. Defender platform sürümü 4.18.2201.10 ile birlikte kullanılabilir.

```yaml
Type: PSSession[]
Position: 0
Default value: None
Accept pipeline input: False 
Accept wildcard characters: False
```

### <a name="get-mpperformancereport"></a>Get-MpPerformanceReport

Aşağıdaki bölümde PowerShell cmdlet'inin Get-MpPerformanceReport anlatıldı. Performans kaydı (MDAV) Microsoft Defender Virüsten Koruma analiz eder ve raporlar.

#### <a name="syntax-get-mpperformancereport"></a>Sözdizimi: Get-MpPerformanceReport

```powershell
Get-MpPerformanceReport    [-Path] <String>
[-TopScans <Int32>]
[-TopFiles  <Int32>
    [-TopScansPerFile <Int32>]
    [-TopProcessesPerFile  <Int32>  
        [-TopScansPerProcessPerFile <Int32>]
    ]
] 
[-TopExtensions  <Int32>
    [-TopScansPerExtension <Int32>]
    [-TopProcessesPerExtension <Int32>
        [-TopScansPerProcessPerExtension <Int32>]
        ]
    [-TopFilesPerExtension  <Int32>
        [-TopScansPerFilePerExtension <Int32>]
        ]
    ] 
]
[-TopProcesses  <Int32>
    [-TopScansPerProcess <Int32>]
    [-TopExtensionsPerProcess <Int32>
        [-TopScansPerExtensionPerProcess <Int32>]
    ]
]
[-TopFilesPerProcess  <Int32>
    [-TopScansPerFilePerProcess <Int32>]
]
[-MinDuration <String>]
```

#### <a name="description-get-mpperformancereport"></a>Açıklama: Get-MpPerformanceReport
`Get-MpPerformanceReport` Cmdlet, daha önce toplanan bir Microsoft Defender Virüsten Koruma performans kaydını ([New-MpPerformanceRecording](#new-mpperformancerecording)) analiz eder ve taramalarda en çok etkiyi ortaya alan dosya yollarını, dosya uzantılarını ve süreçleri Microsoft Defender Virüsten Koruma raporlar.

Performans çözümleyicisi, sistem performansının düşmesine neden olan sorunlu dosyalar hakkında bilgi Microsoft Defender Virüsten Koruma. Bu araç "OLDUĞU GIBI" sağlanır ve dışlamalar hakkında öneriler sağlamak üzere değildir. Dışlamalar, uç noktalarınız üzerinde koruma düzeyini düşürebilirsiniz. Varsa, dışlamalar dikkatli bir şekilde tanımlanmalıdır.

Performans çözümleyicisi hakkında daha fazla bilgi için bkz[. Performans Analizi](/windows-hardware/test/wpt/windows-performance-analyzer) bakın.

**Desteklenen işletim sistemi sürümleri**

Windows 10 ve sonraki bir sürümü deneyin.

> [!NOTE]
> Bu özellik, platform sürümü 4.18.2108.X ve sonraki sürümlerde kullanılabilir.

#### <a name="examples-get-mpperformancereport"></a>Örnekler: Get-MpPerformanceReport

##### <a name="example-1-single-query"></a>Örnek 1: Tek sorgu 

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopScans:20
```

##### <a name="example-2-multiple-queries"></a>Örnek 2: Birden çok sorgu 

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopFiles:10 -TopExtensions:10 -TopProcesses:10 -TopScans:10
```

##### <a name="example-3-nested-queries"></a>Örnek 3: İç içe sorgular 

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopProcesses:10 -TopExtensionsPerProcess:3 -TopScansPerExtensionPerProcess:3
```

##### <a name="example-4-using--minduration-parameter"></a>Örnek 4: Using -MinDuration parametresi

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopScans:100 -MinDuration:100ms
```

#### <a name="parameters-get-mpperformancereport"></a>Parametreler: Get-MpPerformanceReport

##### <a name="-minduration"></a>-MinDuration
Rapora dahil edilen dosyaların, uzantıların ve işlemlerin tarama veya toplam tarama süresinin en kısa süresini belirtir;  **0,1234567sec**, **0,1234ms**, **0,1us** veya geçerli bir TimeSpan gibi değerleri kabul eder.

```yaml
Type: String
Position: Named
Default value: None
Accept pipeline input: False 
Accept wildcard characters: False
```

##### <a name="-path"></a>-Yol
Bir veya birden çok konumun yollarını belirtir.

```yaml
Type: String
Position: 0
Default value: None
Accept pipeline input: True
Accept wildcard characters: False
```

### <a name="-topextensions"></a>-TopExtensions 
Çıkışta "Süre" ayarına göre sıralanmış kaç en üst uzantı olduğunu belirtir.

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topextensionsperprocess"></a>-TopExtensionsPerProcess 
Her üst işlem için kaç tane en üst uzantının çıkışını "Süre" olarak sıralanmış olarak belirtir.

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topfiles"></a>-TopFiles
En üst düzey dosyalar raporunu istekler ve çıkışta "Süre" ayarına göre sıralanmış kaç tane en çok dosya çıkışı olduğunu belirtir.


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topfilesperextension"></a>-TopFilesPerExtension 
Her üst uzantı için, "Süre" ayarına göre sıralanmış, kaç tane en çok dosya çıkışı toplanmış olduğunu belirtir.


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topfilesperprocess"></a>-TopFilesPerProcess
Her bir üst işlem için, "Süre" ayarına göre sıralanmış, kaç tane en çok dosya çıkışı topla ilgili olduğunu belirtir.

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topprocesses"></a>-TopProcesses
En üst işlem raporunu istekler ve en çok çıkış yapılan işlemlerden kaçını "Süre" ayarına göre sıralanmış olarak belirtir.

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topprocessesperextension"></a>-TopProcessesPerExtension 
Her üst uzantı için, "Süre" ayarına göre sıralanmış kaç tane en üst uzantı için çıkış işlemi olduğunu belirtir.


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topprocessesperfile"></a>-TopProcessesPerFile
Her bir üst dosya için, "Süre" ayarına göre sıralanmış kaç tane en çok işlem açacağız?


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscans"></a>-TopScans
En çok tarama raporu talep eder ve "Süre" ayarına göre sıralanmış çıktı için kaç tarama yapmak zorunda olduğunu belirtir.


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperextension"></a>-TopScansPerExtension
"Süre" ayarına göre sıralanmış, her bir üst uzantı için kaç en çok tarama yapmak zorunda olduğunu belirtir.


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperextensionperprocess"></a>-TopScansPerExtensionPerProcess 
Her üst işlem için her üst uzantı için kaç en üst tarama yapmak için "Süre" ayarına göre sıralanmış olduğunu belirtir.


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperfile"></a>-TopScansPerFile
Her bir üst dosya için kaç en çok tarama yapmak için "Süre" ayarına göre sıralanmış olduğunu belirtir.


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscansperfileperextension"></a>-TopScansPerFilePerExtension 
Her üst uzantı için en üstte yer alan dosyalarda, "Süre" ayarına göre sıralanmış, kaç en çok tarama yapmak istediğiniz belirtir.


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperfileperprocess"></a>-TopScansPerFilePerProcess 
Her bir üst işlem için en üst düzey dosyanın kaç kez çıktısı için "Süre" olarak sıralanmış olduğunu belirtir.


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperprocess"></a>-TopScansPerProcess 
En İyi İşlemler raporunda, "Süre" ayarına göre sıralanmış olarak, her bir üst işlem için kaç en çok tarama yapmak için çıktısı olduğunu belirtir.


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscansperprocessperextension"></a>-TopScansPerProcessPerExtension
Her üst uzantı için, "Süre" ayarına göre sıralanmış, her üst uzantı için kaç en üst taramada çıktı atılları olduğunu belirtir.


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscansperprocessperfile"></a>-TopScansPerProcessPerFile
Her bir üst dosya için en üst düzey işlem için kaç en çok çıktı taraması olduğunu "Süre" ayarına göre sıralanmış olarak belirtir.


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```
