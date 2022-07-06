---
title: Tam veri eşleşmeli hassas bilgi türleri için hassas bilgi kaynak tablosu karması oluşturma ve karşıya yükleme
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
description: Hassas bilgi türleriyle tam olarak eşleşen veriler için hassas bilgi kaynağı tablosunu karma olarak ekleyin ve karşıya yükleyin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: dd484f10cf8dad76132ed2a68a34f87b253e76b3
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641306"
---
# <a name="hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types"></a>Tam veri eşleşmeli hassas bilgi türleri için hassas bilgi kaynak tablosu karması oluşturma ve karşıya yükleme

Bu makalede hassas bilgi kaynağı tablonuzun karması ve karşıya yüklenmesi gösterilmektedir.

## <a name="hash-and-upload-the-sensitive-information-source-table"></a>Hassas bilgi kaynağı tablosunu karma ve karşıya yükleme

Bu aşamada:

1. özel güvenlik grubu ve kullanıcı hesabı ayarlama
2. EDM Karşıya Yükleme Aracısı aracını ayarlama
3. Bir tuz değeri, hassas bilgi kaynağı tablosuyla karma yapmak ve karşıya yüklemek için EDM Karşıya Yükleme Aracısı aracını kullanın.

Karma oluşturma ve karşıya yükleme işlemi bir bilgisayar kullanılarak yapılabilir veya daha fazla güvenlik için karma adımını karşıya yükleme adımından ayırabilirsiniz.

Bir bilgisayardan karma ve karşıya yüklemek istiyorsanız, bunu Doğrudan Microsoft 365 kiracınıza bağlanabilen bir bilgisayardan yapmanız gerekir. Bu, düz metin duyarlı bilgi kaynak tablo dosyanızın karma için bu bilgisayarda olmasını gerektirir.

Düz metin duyarlı bilgi kaynak tablo dosyanızı doğrudan erişim bilgisayarında kullanıma açmak istemiyorsanız, bunu güvenli bir konumdaki bir bilgisayarda karma yapabilir ve ardından karma dosyayı ve tuz dosyasını karşıya yükleme için doğrudan Microsoft 365 kiracınıza bağlanabilen bir bilgisayara kopyalayabilirsiniz. Ayrılmış karma ve karşıya yükleme senaryosunda her iki bilgisayarda da EDMUploadAgent gerekir.

> [!IMPORTANT]
> Şema dosyanızı oluşturmak için Tam Veri Eşleştirme şemasını ve hassas bilgi türü sihirbazını kullandıysanız, henüz yapmadıysanız bu yordam için şemayı indirmeniz ***gerekir*** . Bkz. [EDM şema dosyasını XML biçiminde dışarı aktarma](sit-get-started-exact-data-match-create-schema.md#export-of-the-edm-schema-file-in-xml-format).

> [!NOTE]
> Kuruluşunuz [Microsoft 365 için Müşteri Anahtarı'nı kiracı düzeyinde](customer-key-overview.md) ayarladıysa, tam veri eşleşmesi şifreleme işlevini otomatik olarak kullanır. Bu yalnızca Ticari buluttaki E5 lisanslı kiracılar tarafından kullanılabilir.

### <a name="best-practices"></a>En iyi uygulamalar

İşlemdeki sorunları daha kolay yalıtabilmeniz için hassas verileri karmalama ve karşıya yükleme işlemlerini birbirinden ayırın.

Üretime geçtikten sonra, çoğu durumda iki adımı ayrı tutun. Karma işlemini yalıtılmış bir bilgisayarda gerçekleştirmek ve ardından dosyayı İnternet'e yönelik bir bilgisayara yüklemek üzere aktarmak, internet bağlantısı nedeniyle güvenliği aşılmış olabilecek bir bilgisayarda gerçek verilerin hiçbir zaman düz metin biçiminde kullanılamamasını sağlar.

### <a name="ensure-your-sensitive-data-table-doesnt-have-formatting-issues"></a>Hassas veri tablonuzda biçimlendirme sorunları olmadığından emin olun

Hassas verilerinizi karma olarak oluşturup karşıya yüklemeden önce, içeriği ayrıştırmada sorunlara neden olabilecek özel karakterlerin varlığını doğrulamak için bir arama yapın.
Aşağıdaki söz dizimine sahip EDM karşıya yükleme aracısını kullanarak tablonun EDM ile kullanıma uygun bir biçimde olduğunu doğrulayabilirsiniz:

```powershell
EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file]
```

Araç sütun sayısında uyuşmazlık gösteriyorsa, tablodaki değerlerin içinde sütun sınırlayıcılarıyla karıştırılan virgül veya tırnak karakterlerinin bulunmasından kaynaklanıyor olabilir. Bir değerin tamamını çevrelemedikçe, tek ve çift tırnaklar aracın tek bir sütunun nerede başladığını veya bittiğini yanlış belirlemesine neden olabilir.

**Tam değerleri çevreleyen tek veya çift tırnak karakterleri bulursanız**, bunları olduğu gibi bırakabilirsiniz.

**Bir değerin içinde tek tırnak karakterleri veya virgüller bulursanız**: örneğin kişinin adı Tom O'Neil veya kesme işareti karakteriyle başlayan city 's-Gravenhage, bu tür sütunları çift tırnakla çevreleyecek şekilde hassas bilgi tablosu oluşturmak için kullanılan veri dışarı aktarma işlemini değiştirmeniz gerekir.

**Değerlerin içinde çift tırnak karakterleri bulunursa**, tablo için bu tür sorunlara daha az duyarlı olan Sekmeyle sınırlandırılmış biçimin kullanılması tercih edilebilir.

### <a name="prerequisites"></a>Önkoşullar

- Microsoft 365 için **EDM\_DataUploaders** güvenlik grubuna eklenecek bir iş veya okul hesabı
- .NET sürüm 4.6.2 ile bir Windows 10 veya Windows Server 2016 makinesi <!--4.7.2 un comment this around 9/29-->EDMUploadAgent'ı çalıştırmak için
- için karşıya yükleme makinenizdeki bir dizin:
  - [EDM Karşıya Yükleme Aracısı](#links-to-edm-upload-agent-by-subscription-type)
  - hassas öğe dosyanızı .csv, .tsv veya kanal (|) biçiminde **PatientRecords.csv** örneklerimizde bulabilirsiniz
  - bu yordamda oluşturulan çıkış karması ve tuz dosyaları
  - **edm.xml** dosyasındaki veri deposu adı, örneğin`PatientRecords`

#### <a name="set-up-the-security-group-and-user-account"></a>Güvenlik grubunu ve kullanıcı hesabını ayarlama

1. Genel yönetici olarak [aboneliğiniz için uygun bağlantıyı](sit-get-started-exact-data-match-based-sits-overview.md#portal-links-for-your-subscription) kullanarak yönetim merkezine gidin ve **EDM\_DataUploaders** adlı [bir güvenlik grubu oluşturun](/office365/admin/email/create-edit-or-delete-a-security-group).

2. **EDM\_DataUploaders** güvenlik grubuna bir veya daha fazla kullanıcı ekleyin. (Bu kullanıcılar hassas bilgi veritabanını yönetir.)

### <a name="hash-and-upload-from-one-computer"></a>Bir bilgisayardan karma ve karşıya yükleme

Bu bilgisayarın Microsoft 365 kiracınıza doğrudan erişimi olmalıdır.

> [!NOTE]
> Bu yordama başlamadan önce **EDM\_DataUploaders** güvenlik grubunun üyesi olduğunuzdan emin olun.

> [!TIP]
>İsteğe bağlı olarak, şu komutu çalıştırarak karşıya yüklemeden önce hataları denetlemek için hassas bilgi kaynağı tablo dosyanızda bir doğrulama çalıştırabilirsiniz:
>
> `EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file]`
>
> Desteklenen tüm EdmUploadAgent.exe parametreleri hakkında daha fazla bilgi için komutunu çalıştırın
>
> `EdmUploadAgent.exe /?`

#### <a name="links-to-edm-upload-agent-by-subscription-type"></a>Abonelik türüne göre EDM karşıya yükleme aracısına bağlantılar

- [Ticari + GCC](https://go.microsoft.com/fwlink/?linkid=2088639) - çoğu ticari müşteri bunu kullanmalıdır
- [GCC-High](https://go.microsoft.com/fwlink/?linkid=2137521) - Bu özellikle yüksek güvenlikli kamu bulut abonelerine yöneliktir
- [DoD](https://go.microsoft.com/fwlink/?linkid=2137807) - Bu özellikle Birleşik Devletler Savunma Bakanlığı bulut müşterilerine yöneliktir

1. EDMUploadAgent için bir çalışma dizini oluşturun. Örneğin, **C:\EDM\Data**. **PatientRecords.csv** dosyasını buraya yerleştirin.

2. Aboneliğiniz için uygun [EDM Karşıya Yükleme Aracısını](#links-to-edm-upload-agent-by-subscription-type) indirin ve 1. adımda oluşturduğunuz dizine yükleyin.

   > [!NOTE]
   > Yukarıdaki bağlantılarda yer alan EDMUploadAgent, karma verilere otomatik olarak bir tuz değeri ekleyecek şekilde güncelleştirilmiştir. Alternatif olarak, kendi tuz değerinizi sağlayabilirsiniz. Bu sürümü kullandıktan sonra, EDMUploadAgent'ın önceki sürümünü kullanamazsınız.
   >
   > EDMUploadAgent ile verileri belirli bir veri deposuna günde yalnızca iki kez yükleyebilirsiniz.

3. EDM Karşıya Yükleme Aracısı'nı yetkilendileyin, Yönetici olarak Komut İstemi penceresini açın, **C:\EDM\Data** dizinine geçin ve aşağıdaki komutu çalıştırın:

   `EdmUploadAgent.exe /Authorize`

   > [!IMPORTANT]
   > **EdmUploadAgent'ı** yüklü olduğu klasörden çalıştırmanız ve veri dosyalarınızın tam yolunu belirtmeniz gerekir.

4. EDM_DataUploaders güvenlik grubuna eklenen Microsoft 365 için iş veya okul hesabınızla oturum açın. Bağlantı oluşturmak için kiracı bilgileriniz kullanıcı hesabından ayıklanır.

   İsteğE BAĞLI: Şemanızı oluşturmak için Tam Veri Eşleştirme şemasını ve hassas bilgi türü sihirbazını kullandıysanız, henüz yapmadıysanız bu yordamlarda kullanmak üzere indirmeniz ***gerekir*** . Komut İstemi penceresinde bu komutu çalıştırın:

   ```dos
   EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>
   ```

5. Hassas verileri karma olarak kullanmak ve karşıya yüklemek için Komut İstemi penceresinde aşağıdaki komutu çalıştırın:

   ```dos
   EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /ColumnSeparator ["{Tab}"|"|"] /AllowedBadLinesPercentage [value]
   ```

   > [!NOTE]
   > Hassas veri dosyasının varsayılan biçimi virgülle ayrılmış değerlerdir. /ColumnSeparator parametresiyle "{Tab}" seçeneğini belirterek sekmeyle ayrılmış bir dosya belirtebilir veya "|" seçeneğini belirterek kanalla ayrılmış bir dosya belirtebilirsiniz.
   >
   > Örnek: `EdmUploadAgent.exe /UploadData /DataStoreName PatientRecords /DataFile C:\Edm\Hash\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml /AllowedBadLinesPercentage 5`

   Hassas bilgi tablonuzda bazı yanlış biçimlendirilmiş değerler varsa, ancak yine de geçersiz satırları yoksayarak kalan verileri içeri aktarmak istiyorsanız, komutta */AllowedBadLinesPercentage* parametresini kullanabilirsiniz. Yukarıdaki örnekte yüzde beşlik bir eşik belirtmektedir. Bu, satırların yüzde beşine kadar geçersiz olsa bile aracın hassas bilgi tablosunu karma hale getireceği ve karşıya yükleyeceği anlamına gelir.

   Bu komut, daha fazla güvenlik için karmaya otomatik olarak rastgele oluşturulmuş bir tuz değeri ekler. İsteğe bağlı olarak, kendi tuz değerinizi kullanmak istiyorsanız komutuna **/Salt \<saltvalue\>** değerini ekleyin. Bu değer 64 karakter uzunluğunda olmalı ve yalnızca a-z karakterlerini ve 0-9 karakterlerini içerebilir.

6. Şu komutu çalıştırarak karşıya yükleme durumunu denetleyin:

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName \<DataStoreName\>
   ```

   Örnek: `EdmUploadAgent.exe /GetSession /DataStoreName PatientRecords`

   **ProcessingInProgress** içinde durumunu arayın. Durum **Tamamlandı** olarak değişene kadar birkaç dakikada bir yeniden denetleyin. Durum tamamlandıktan sonra EDM verileriniz kullanıma hazırdır. Hassas bilgi kaynağı tablo dosyanızın boyutuna bağlı olarak, bu işlem birkaç dakika ile birkaç saat sürebilir.

> [!TIP]
> Karşıya yüklenen hassas veriler kullanıma hazır olduğunda bildirim almak istiyorsanız [, Tam veri eşleştirme etkinlikleri için bildirimler oluşturma](sit-edm-notifications-activities.md#create-notifications-for-exact-data-match-activities) başlığı altında yer alan yordamları izleyin.

### <a name="separate-hash-and-upload"></a>Karmayı ayırma ve karşıya yükleme

Karmayı güvenli bir ortamdaki bir bilgisayarda gerçekleştirin. Her iki bilgisayarda **da EDMUploadAgent** yüklü olmalıdır.

İsteğE BAĞLI: Şemanızı oluşturmak için Tam Veri Eşleştirme şemasını ve hassas bilgi türü sihirbazını kullandıysanız ve henüz indirmediyseniz, dosyayı XML biçiminde indirmek için komut istemi penceresinde aşağıdaki komutu çalıştırın:

```dos
EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>
````

1. Güvenli ortamdaki bilgisayarda, Komut İstemi pencerelerinde aşağıdaki komutu çalıştırın:

   ```dos
   EdmUploadAgent.exe /CreateHash /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /AllowedBadLinesPercentage [value]
   ```

   Örneğin:

   ```dos
   EdmUploadAgent.exe /CreateHash /DataFile C:\Edm\Data\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml /AllowedBadLinesPercentage 5
   ```

   > [!NOTE]
   > Hassas veri dosyasının varsayılan biçimi virgülle ayrılmış değerlerdir. /ColumnSeparator parametresiyle "{Tab}" seçeneğini belirterek sekmeyle ayrılmış bir dosya belirtebilir veya "|" seçeneğini belirterek kanalla ayrılmış bir dosya belirtebilirsiniz.

   **Bu, /Salt \<saltvalue\>** seçeneğini belirtmediyseniz karma dosya ve şu uzantılara sahip bir tuz dosyası oluşturur:

   - . EdmHash
   - . EdmSalt

2. Bu dosyaları güvenli bir şekilde hassas bilgi kaynağı tablo dosyanızı (PatientRecords) kiracınıza yüklemek için kullanacağınız bilgisayara kopyalayın.

3. EDM Karşıya Yükleme Aracısı'nı yetkilendileyin, Yönetici olarak Komut İstemi penceresini açın, **C:\EDM\Data** dizinine geçin ve aşağıdaki komutu çalıştırın:

   ```dos
   EdmUploadAgent.exe /Authorize
   ```

   > [!IMPORTANT]
   > **EdmUploadAgent'ı** yüklü olduğu klasörden çalıştırmanız ve veri dosyalarınızın tam yolunu belirtmeniz gerekir.

4. EDM_DataUploaders güvenlik grubuna eklenen Microsoft 365 için iş veya okul hesabınızla oturum açın. Bağlantı oluşturmak için kiracı bilgileriniz kullanıcı hesabından ayıklanır.

5. Karma verileri karşıya yüklemek için Windows Komut İstemi'nde aşağıdaki komutu çalıştırın:

   ```dos
   EdmUploadAgent.exe /UploadHash /DataStoreName \<DataStoreName\> /HashFile \<HashedSourceFilePath\ /ColumnSeparator ["{Tab}"|"|"]
   ```

   Örneğin:

   ```dos
   EdmUploadAgent.exe /UploadHash /DataStoreName PatientRecords /HashFile C:\\Edm\\Hash\\**PatientRecords.EdmHash**
   ```

6. Hassas verilerinizin karşıya yüklendiğini doğrulamak için Komut İstemi penceresinde aşağıdaki komutu çalıştırın:

   ```dos
   EdmUploadAgent.exe /GetDataStore
   ```

   Veri depolarının listesini ve bunların en son ne zaman güncelleştirildiğini görürsünüz.

7. Belirli bir depoya yüklenen tüm verileri görmek istiyorsanız, windows komut isteminde aşağıdaki komutu çalıştırarak tüm veri depolarının listesini ve ne zaman güncelleştirildiklerini görün:

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName <DataStoreName>
   ```

> [!NOTE]
> Karma ve karşıya yükleme işlemini ilk kez oluşturduktan sonra otomatikleştirmek için bkz. [Hassas bilgi kaynağı tablo dosyasıyla tam olarak eşleşen verilerinizi yenileme](sit-use-exact-data-refresh-data.md).

## <a name="next-step"></a>Sonraki Adım

- [Tam veri eşleşmesi hassas bilgi türü/kural paketi oluşturma](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package)
