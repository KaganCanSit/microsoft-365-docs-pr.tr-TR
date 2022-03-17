---
title: Hassas bilgi türleriyle tam olarak eşleşmesi için hassas bilgi kaynağı tablosuna karma sağlama ve yükleme
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Hassas veri eşleşmesi için hassas bilgi kaynağı tablosuna karma kullanın ve hassas bilgi türlerini yükleyin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8d3effe3d46375ffcaec268e4b3fc6d53fc5044e
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526506"
---
# <a name="hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types"></a>Hassas bilgi türleriyle tam olarak eşleşmesi için hassas bilgi kaynağı tablosuna karma sağlama ve yükleme

Bu makalede, hassas bilgi kaynağı tablolarınızı karma ve karşıya yükleme konularını bulabilirsiniz.

## <a name="hash-and-upload-the-sensitive-information-source-table"></a>Karma sağlama ve hassas bilgiler kaynak tabloyu karşıya yükleme

Bu aşamada:

1. özel güvenlik grubu ve kullanıcı hesabı ayarlama
2. EDM Upload aracını ayarlama
3. EDM Veri Upload aracını bir salt değeriyle, hassas bilgi kaynağı tablosuyla karma kullanmak ve karşıya yüklemek için kullanın.

Karma sağlama ve karşıya yükleme tek bir bilgisayar kullanılarak yapılabilir veya daha yüksek güvenlik için karma sağlama adımını karşıya yükleme adımdan ayırabilirsiniz.

Karma yapmak ve tek bir bilgisayardan karşıya yüklemek için, bunu kendi kiracınıza doğrudan bağlanan bir bilgisayardan Microsoft 365 gerekir. Bunun için, net metin duyarlı bilgi kaynak tablo dosyanız karma için o bilgisayardadır.

Net metin duyarlı bilgi kaynağı tablo dosyanızı doğrudan erişimli bilgisayarda göstermek istemiyorsanız, karma dosyayı güvenli bir konumdaki bilgisayarda karma olarak yer alan bir bilgisayarda karma olarak yer alan ve sonra da karma dosyayı ve salt dosyayı karşıya yüklemek üzere Microsoft 365 kiracınıza doğrudan bağlanacak bir bilgisayara kopyaabilirsiniz. Ayrılmış karma ve karşıya yükleme senaryosunda, her iki bilgisayarda da EDMUploadAgent değerine ihtiyacınız vardır.

> [!IMPORTANT]
> Şema dosyanızı oluşturmak için Tam Veri Eşleşme şeması ve hassas bilgi türü sihirbazını kullandıysanız, henüz  bunu yapmadıysanız, bu yordamın şemasını indirmeniz gerekir. Bkz [. EDM şema dosyasını XML biçiminde dışarı aktarma](sit-get-started-exact-data-match-create-schema.md#export-of-the-edm-schema-file-in-xml-format).

> [!NOTE]
> If your organization has set up [Customer Key for Microsoft 365 at the tenant](customer-key-overview.md) level, Exact data match will make use of its encryption functionality automatically. Bu yalnızca Ticari buluttaki E5 lisanslı kiracılar için kullanılabilir.

### <a name="best-practices"></a>En iyi uygulamalar

Hassas verileri karmalama ve karşıya yükleme işlemlerini birbirinden ayırarak süreçteki sorunları daha kolay yalıtabilirsiniz.
 
Üretime başladıktan sonra, çoğu durumda bu iki adımı birbirinden ayrı tutabilirsiniz. Yalıtılmış bir bilgisayarda karma işlemi gerçekleştirdikten sonra dosyayı İnternet'e yönelik bir bilgisayara yüklemek için aktararak, İnternet bağlantısı nedeniyle güvenliği ihlal edilmiş olan bir bilgisayarda gerçek verilerin asla net metin formunda kullanılamaz.

### <a name="ensure-your-sensitive-data-table-doesnt-have-formatting-issues"></a>Hassas veri tablonuzda biçimlendirme sorunları olduğundan emin olma. 

Hassas verilerinizi karmalamadan ve karşıya yüklemeden önce, içeriği ayrıştırmada sorunlara neden olan özel karakterlerin varlığını doğrulamak için bir arama kullanın. Aşağıdaki söz dizim ile EDM karşıya yükleme aracılarını kullanarak tablonun EDM ile kullanmaya uygun bir biçimde olduğunu doğruabilirsiniz:

```powershell
EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file] 
```

Araç, sütun sayısıyla ilgili bir yanlışlık olduğunu gösteriyorsa, tablodaki değerlerde virgül veya tırnak karakterleri olması sütun sınırlayıcılarla karıştırılmış olabilir. Bir değerin tamamını çevrelemiyorsanız, tek ve çift tırnaklar tek tek bir sütunun nereden başladığı veya bittiği aracının yanlış tanımlanabilmektedir. 

**Tam değerleri çevreleyen tek veya çift tırnak karakterleri bulursanız**, bunları olduğu gibi bırakın.

Bir değerin **içinde** tek tırnak karakterleri veya virgüller bulursanız: örneğin, kişinin adı Tom O'Neil veya şehir 's-Gravenhage' (kesme işareti karakteriyle başlayan) gibi, hassas bilgi tablosu oluşturmak için kullanılan veri aktarma işlemini değiştirerek bu tür sütunları çift tırnak içine alırsınız.

**Değerlerin içinde çift** tırnak karakterleri bulunursa, tablonun bu tür sorunlar için daha az duyarlı olmayan Sekmeyle ayrılmış biçimini kullanmak daha iyi bir tercih olabilir.

### <a name="prerequisites"></a>Önkoşullar

- **EDMDataUploaders\_** güvenlik Microsoft 365 için iş veya okul hesabı
- .NET Windows 10 4.6.2 Windows Server 2016 yüklü bir makine <!--4.7.2 un comment this around 9/29-->EDMUploadAgent'i çalıştırma için
- aşağıdakiler için karşıya yükleme makinenizin dizininde bir dizin kullanın:
  - [EDM Upload Aracısı](#links-to-edm-upload-agent-by-subscription-type)
  - hassas öğe dosyanız .csv, .tsv veya pipe (|) **biçimindedir vePatientRecords.csv** örneklerde
  - Bu yordamda oluşturulan çıkış karması ve salt dosyaları
  - edm.xmlveri **deposu** adı, örneğin `PatientRecords`

#### <a name="set-up-the-security-group-and-user-account"></a>Güvenlik grubunu ve kullanıcı hesabını ayarlama

1. Genel yönetici olarak, aboneliğiniz için uygun bağlantıyı kullanarak yönetim merkezine gidin [](sit-get-started-exact-data-match-based-sits-overview.md#portal-links-for-your-subscription) ve **EDMDataUploaders\_ adlı bir güvenlik grubu oluşturun**.[](/office365/admin/email/create-edit-or-delete-a-security-group)

2. **EDMDataUploaders\_ güvenlik grubuna bir veya daha fazla kullanıcı** ekleyin. (Bu kullanıcılar hassas bilgilerin veritabanını yönetir.)

### <a name="hash-and-upload-from-one-computer"></a>Karma sağlama ve tek bir bilgisayardan karşıya yükleme

Bu bilgisayarın kiracınıza doğrudan erişimi Microsoft 365 gerekir.

> [!NOTE]
> Bu yordama başlamadan önce, **EDMDataUploaders\_ güvenlik grubunun üyesi olduğundan** emin olun.

> [!TIP] 
>İsteğe bağlı olarak, karşıya yüklemeden önce hata denetimi yapmak için hassas bilgi kaynağı tablo dosyanız üzerinde doğrulama çalıştırabilirsiniz:
>
> `EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file]`
>
> Desteklenen tüm parametreler EdmUploadAgent.exe daha fazla bilgi için
>
> `EdmUploadAgent.exe /?`

#### <a name="links-to-edm-upload-agent-by-subscription-type"></a>EDM'nin abonelik türüne göre karşıya yükleme aracısı bağlantıları

- [Ticari + GCC](https://go.microsoft.com/fwlink/?linkid=2088639) - çoğu ticari müşteri bunu kullan
- [GCC-Yüksek](https://go.microsoft.com/fwlink/?linkid=2137521) - Bu, özel olarak yüksek güvenlikli devlet bulut aboneleri için
- [DoD](https://go.microsoft.com/fwlink/?linkid=2137807) - Bu özel olarak AMERIKA Birleşik Devletleri Savunma bulut müşterileri için

1. EDMUploadAgent için bir çalışma dizini oluşturun. Örneğin, **C:\EDM\Data**. Dosyayı **PatientRecords.csv** yere.

2. 1. adımda oluşturduğunuz [dizine Upload için uygun EDM](#links-to-edm-upload-agent-by-subscription-type) Güvenlik Aracısı aracınızı indirin ve yükleyin.

   > [!NOTE]
   > Yukarıdaki bağlantıların EDMUploadAgent değeri, karma verilere otomatik olarak bir salt değeri eklemek üzere güncelleştirildi. Alternatif olarak, kendi salt değerinizi de s olabilir. Bu sürümü kullandıktan sonra, EDMUploadAgent'ın önceki sürümünü kullanamayacaktır.
   >
   > EDMUploadAgent ile verileri, veri deposuna günde yalnızca iki kez yükleyebilirsiniz.

3. EDM Hizmet Upload yetkilendirin, yönetici olarak Komut İstemi penceresini açın, **C:\EDM\Data** dizinine geçin ve sonra aşağıdaki komutu çalıştırın:

   `EdmUploadAgent.exe /Authorize`

> [!IMPORTANT]
> **EdmUploadAgent'i** yüklü olduğu klasörden çalıştırmanız ve veri dosyalarınızın tam yolunu belirtebilirsiniz. 

4. İş veya okul hesabınızla, Microsoft 365 grubuna eklenmiş olan iş veya okul EDM_DataUploaders açın. Bağlantıyı yapmak için kullanıcı hesabından kiracı bilgileri ayıklanır.

   İsteğE BAĞLı: Şemanızı oluşturmak için Tam Veri Eşleşme şeması ve hassas bilgi türü sihirbazını kullandıysanız, henüz indirmedıysanız, bunu bu yordamlarda kullanmak için indirmeniz gerekir. Komut İstemi penceresinde bu komutu çalıştırın:

   ```dos
   EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>
   ```

5. Hassas verileri karma yapmak ve karşıya yüklemek için Komut İstemi penceresinde aşağıdaki komutu çalıştırın:

   ```dos
   EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /ColumnSeparator ["{Tab}"|"|"] /AllowedBadLinesPercentage [value]
   ```
   > [!NOTE]
> Hassas veri dosyasının varsayılan biçimi virgülle ayrılmış değerlerdir. "{Tab}" seçeneğini /ColumnSeparator parametresiyle belirterek sekmeyle ayrılmış bir dosya belirtebilirsiniz veya "Sekme" seçeneğini belirterek, boruyla ayrılmış bir | belirtebilirsiniz.

   Örnek: **EdmUploadAgent.exe /UploadData /DataStoreName PatientRecords /DataFile C:\Edm\Hash\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml /AllowedBadLinesPercentage 5**

Hassas bilgi tablolarında hatalı biçimlendirilmiş bazı değerler varsa, ancak yine de geçersiz satırları yoksayarken kalan verileri içeri aktarmayı istiyorsanız, komutta */AllowedBadLinesPercentage* parametresini kullanabilirsiniz. Yukarıdaki örnekte yüzde beş eşik belirtir. Bu, satırın en çok beş yüzdesi geçersiz olsa bile aracın karma değerine sahip olduğu ve hassas bilgi tablosu karşıya yükley istediğiniz anlamına gelir. 

Bu komut daha yüksek güvenlik için karmaya rastgele oluşturulmuş bir salt değeri otomatik olarak ekler. İsteğe bağlı olarak, kendi salt değerinizi kullanmak istediğiniz **/Salt komutunu <saltvalue>** komuta ekleyin. Bu değer 64 karakter uzunluğunda olmalı ve yalnızca a-z karakterlerini ve 0-9 karakterlerini içerebilir.

6. Şu komutu çalıştırarak karşıya yükleme durumunu kontrol edin:

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName \<DataStoreName\>
   ```

   Örnek: **EdmUploadAgent.exe /GetSession /DataStoreName PatientRecords**

   **ProcessingInProgress içinde olmak için durumlara bakın**. Durum, Tamamlandı olarak tamamlanana kadar birkaç dakikada bir yeniden **kontrol edin**. Durum tamamlandıktan sonra EDM verileriniz kullanıma hazır olur. Hassas bilgi kaynağı tablo dosyanın boyutuna bağlı olarak, bu birkaç dakikadan birkaç saate kadar sürebilir. 

> [!TIP]
> Karşıya yüklenen hassas veriler kullanıma hazır olduğunda size bildirilmesi için Tam veri eşleşme etkinlikleri için bildirimler [oluşturma'daki yordamları izleyin](sit-edm-notifications-activities.md#create-notifications-for-exact-data-match-activities).

### <a name="separate-hash-and-upload"></a>Karma'yı ayırma ve karşıya yükleme

Karma değeri, güvenli bir ortamda bilgisayarda gerçekleştirin. **EDMUploadAgent her iki bilgisayarda** da yüklü olmalı.

İsteğE BAĞLı: Şemanızı oluşturmak için Tam Veri Eşleşme şeması ve hassas bilgi türü sihirbazını kullandıysanız ve henüz indirmedıysanız, komut istemi penceresinde dosyayı XML biçiminde indirmek için aşağıdaki komutu çalıştırın:

```dos
EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>
````

1. Güvenli ortamdaki bilgisayarda, Komut İstemi penceresinde aşağıdaki komutu çalıştırın:

   ```dos
   EdmUploadAgent.exe /CreateHash /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /AllowedBadLinesPercentage [value]
   ```

   Örneğin:

   ```dos
   EdmUploadAgent.exe /CreateHash /DataFile C:\Edm\Data\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml /AllowedBadLinesPercentage 5
   ```

> [!NOTE]
> Hassas veri dosyasının varsayılan biçimi virgülle ayrılmış değerlerdir. "{Tab}" seçeneğini /ColumnSeparator parametresiyle belirterek sekmeyle ayrılmış bir dosya belirtebilirsiniz veya "Sekme" seçeneğini belirterek, boruyla ayrılmış bir | belirtebilirsiniz.


   Bu, /Salt seçeneğini belirtmedıyseniz, karma bir dosyanın ve bu uzantılara sahip bir salt dosyanın **çıkışını <saltvalue>** alır:

   - . EdmHash
   - . EdmSalt


2. Bu dosyaları, hassas bilgi kaynağı tablo dosyanızı (PatientRecords) kiracınıza yüklemek için kullanabileceğiniz bilgisayara güvenli bir şekilde kopyalayın.

3. EDM Hizmet Upload yetkilendirin, yönetici olarak Komut İstemi penceresini açın, **C:\EDM\Data** dizinine geçin ve sonra aşağıdaki komutu çalıştırın:

   `EdmUploadAgent.exe /Authorize`

> [!IMPORTANT]
> **EdmUploadAgent'i** yüklü olduğu klasörden çalıştırmanız ve veri dosyalarınızın tam yolunu belirtebilirsiniz. 

4. İş veya okul hesabınızla, Microsoft 365 grubuna eklenmiş olan iş veya okul EDM_DataUploaders açın. Bağlantıyı yapmak için kullanıcı hesabından kiracı bilgileri ayıklanır.

5. Karma verileri karşıya yüklemek için, Karma Komut İstemi'Windows çalıştırın:

   ```dos
   EdmUploadAgent.exe /UploadHash /DataStoreName \<DataStoreName\> /HashFile \<HashedSourceFilePath\ /ColumnSeparator ["{Tab}"|"|"]
   ```

   Örneğin:

   ```dos
   EdmUploadAgent.exe /UploadHash /DataStoreName PatientRecords /HashFile C:\\Edm\\Hash\\**PatientRecords.EdmHash**
   ```

6. Hassas verilerinizin karşıya yük yük doğrulamak için Komut İstemi penceresinde aşağıdaki komutu çalıştırın:

   ```dos
   EdmUploadAgent.exe /GetDataStore
   ```
   Veri depolarının listesini ve en son ne zaman güncelleştirilenleri burada bulabilirsiniz.

7. Belirli bir depoya yüklenen tüm verileri görmek için, Windows komut isteminde aşağıdaki komutu çalıştırarak tüm veri depolarının listesini ve ne zaman güncelleştirilenleri bakın:

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName <DataStoreName>
   ```
     
## <a name="next-step"></a>Sonraki Adım

- [Hassas bilgi türü/kural paketiyle tam olarak eşleşmesi için veri oluşturma](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package)

