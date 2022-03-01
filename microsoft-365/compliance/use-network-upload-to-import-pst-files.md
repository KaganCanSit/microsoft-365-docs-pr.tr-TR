---
title: Ağ karşıya yükleme kullanarak kuruluş PST dosyalarını içeri aktarma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 103f940c-0468-4e1a-b527-cc8ad13a5ea6
description: 'Yöneticiler için: Birden çok PST dosyasını aynı anda birçok PST dosyasını toplu olarak kendi posta kutularına toplu olarak içeri yüklemek için ağ karşıya yükleme Microsoft 365.'
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b189be60efb48af33d26ea459bbee77878d4a93c
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021511"
---
# <a name="use-network-upload-to-import-your-organizations-pst-files-to-microsoft-365"></a>Ağ karşıya yükleme kullanarak, kuruluş PST dosyalarını başka bir Microsoft 365

> [!NOTE]
> Bu makale yöneticilere aittir. PST dosyalarını kendi posta kutunuza içeri aktarmaya mı çalışıyorsunuz? Bkz[. E-postayı, kişileri ve takvimi Outlook .pst dosyasından içeri aktarma](https://go.microsoft.com/fwlink/p/?LinkID=785075)
  
Posta kutularına birden çok PST dosyasını toplu olarak içeri aktararak ağ karşıya yükleme için gereken adım Microsoft 365 ve açık ve açık. PST dosyalarını posta kutularına toplu olarak içeri aktararak ağ karşıya yükleme hakkında sık Microsoft 365 için bkz. PST dosyalarını içeri aktarmada ağ karşıya yükleme kullanma hakkında [SSS](./faqimporting-pst-files-to-office-365.yml#using-network-upload-to-import-pst-files).
  
[1. Adım: SAS URL'sini kopyalama ve AzCopy'yi indirme](#step-1-copy-the-sas-url-and-download-azcopy)

[2. Adım: UPLOAD dosyalarınızı başka bir Microsoft 365](#step-2-upload-your-pst-files-to-microsoft-365)

[(İsteğe bağlı) 3. Adım: Karşıya yüklenen PST dosyalarının listesini görüntüleme](#optional-step-3-view-a-list-of-the-pst-files-uploaded-to-microsoft-365)

[4. Adım: PST İçeri Aktarma eşleme dosyasını oluşturma](#step-4-create-the-pst-import-mapping-file)

[5. Adım: PST İçeri Aktarma işi oluşturma](#step-5-create-a-pst-import-job)

[6. Adım: Verileri filtreleme ve PST İçeri Aktarma işini başlatma](#step-6-filter-data-and-start-the-pst-import-job)

PST dosyalarını posta kutularına içeri aktarmanız için 1. Microsoft 365 gerekir. Bu adımları gerçekleştirdikten sonra, toplu PST dosyalarını karşıya yüklemek ve içeri aktarın.

## <a name="before-you-import-pst-files"></a>PST dosyalarını içeri aktarmadan önce
  
- Posta Kutusunda içeri aktarma işleri oluşturmak ve PST dosyalarını kullanıcı posta kutularına içeri Exchange Online için Microsoft 365 uyumluluk merkezi Kutusu İçeri/Dışarı Aktarma rolüne atanmışsınız. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü Kuruluş Yönetimi rol grubuna  eklersiniz. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve ardından kendinizi üye olarak  eklersiniz. Daha fazla bilgi için Rol gruplarını yönetme'de "Bir rol grubuna rol ekleme" veya "Rol grubu oluşturma" [bölümlerine bakın](/Exchange/permissions-exo/role-groups).

    Posta Kutusu İçeri/Dışarı Aktarma rolüne ek olarak, bu rolde posta kutusunda Posta Alıcıları rolüne de Exchange Online. Varsayılan olarak bu rol, aynı gruptaki Kuruluş Yönetimi ve Alıcı Yönetimi rol gruplarına Exchange Online.

    > [!TIP]
    > Bu dosyalarda, PST dosyalarını içeri Exchange Online yönelik yeni bir rol grubu oluşturmayı göz önünde bulundurabilirsiniz. PST dosyalarını içeri aktarmanız için gereken minimum düzeydeki ayrıcalıklar için Posta Kutusunu İçeri/Dışarı Aktar ve Posta Alıcıları rollerini yeni rol grubuna atayın ve ardından üyeleri ekleyin.
  
- PST dosyalarını bu makalede açıklandığı gibi Microsoft 365'e aktarmanın desteklenen tek yöntemi AzCopy aracını kullanmaktır. PST dosyalarını doğrudan Azure Azure Depolama Gezgini alanına yüklemek için E-posta Depolama.

- Büyük PST dosyaları PST içeri aktarma işleminin performansını etkileyebilir. Bu nedenle, 2. Adımda Azure Depolama Depolama yüklediğiniz her PST dosyasının 20 GB'den büyük olmadığını öneririz.

- Bu yordam, erişim anahtarı içeren bir URL'nin kopyasını kopyalama ve kaydetmeyi içerir. Bu bilgiler 2. Adımda PST dosyalarınızı karşıya yüklemek için ve 3. Adımda da Microsoft 365'e yüklenen PST dosyalarının listesini görüntülemek için kullanılacaktır. Parolaları veya güvenlikle ilgili diğer bilgileri korur gibi bu URL'yi korumak için önlemler almaya devam edin. Örneğin, belgeyi parola korumalı bir belgeye Microsoft Word şifreli bir USB sürücüsüne kaydedebilirsiniz. Bu [birleştirilmiş URL ve](#more-information) anahtar örneği için Daha fazla bilgi bölümüne bakın.

- PST dosyalarını etkin olmayan bir posta kutusuna kendi posta kutunuzda Microsoft 365. Bunu yapmak için, PST İçeri Aktarma eşleme dosyasındaki parametrede etkin  `Mailbox` olmayan posta kutusunun GUID'sini belirtirsiniz. Bilgi için, bu makalenin **Yönergeler sekmesindeki** 4. Adım'a bakın.

- Karma Exchange dağıtımda, birincil posta kutusu şirket içinde olan bir kullanıcı için PST dosyalarını bulut tabanlı bir arşiv posta kutusuna aktarabilirsiniz. Bunu yapmak için PST İçeri Aktarma eşleme dosyasında şunları yapın:

  - Parametrede kullanıcının şirket içi posta kutusunun e-posta adresini  `Mailbox` belirtin.

  - Parametrede **DOĞRU** değerini  `IsArchive` belirtin.

    Daha [fazla bilgi için 4](#step-4-create-the-pst-import-mapping-file) . Adım'a bakın.

- PST dosyaları içeri aktarıldıktan sonra, posta kutusunun bekletme ayarı süresiz olarak açık olur. Bu, siz bekletmeyi kapatana veya bekletmeyi kapatacak bir tarih ayarlamadan posta kutusuna atanan bekletme ilkesi işlenmez. Bunu neden yapacağız? Posta kutusuna aktarılan iletiler eskise, posta kutusu için yapılandırılan bekletme ayarlarına göre bekletme sürelerinin süresi sona ermiş olduğundan bunlar kalıcı olarak silinebilir (temiz kullanılabilir). Posta kutusunun bekletmeye yerleştirilmesi, posta kutusu sahibinin bu yeni aktarılan iletileri yönetmesi için zaman verir veya posta kutusunun bekletme ayarlarını değiştirmek için size zaman verir. Bekletmeyi [yönetme hakkında](#more-information) öneriler için bu makalenin Daha fazla bilgi bölümüne bakın.

- Varsayılan olarak, bir posta kutusu tarafından alın en büyük ileti Microsoft 365 35 MB'dir. Bunun nedeni, posta kutusunun  *MaxReceiveSize*  özelliğinin varsayılan değeri 35 MB olarak ayarlanmıştır. Bununla birlikte, en büyük ileti alma boyutu sınırı Microsoft 365 150 MB'dir. Dolayısıyla, 35 MB'den büyük bir öğe içeren bir PST dosyasını içeri aktarıyorsanız Microsoft 365 İçeri Aktarma hizmeti, hedef posta kutusunda *MaxReceiveSize* özelliğinin değerini otomatik olarak 150 MB olarak değiştiririz. Bu, 150 MB'a kadar olan iletilerin kullanıcı posta kutularına aktarılmaz.

    > [!TIP]
    > Bir posta kutusunun ileti alma boyutunu belirlemek için bu komutu PowerShell Exchange Online çalıştırabilirsiniz: `Get-Mailbox <user mailbox> | FL MaxReceiveSize`.

- PST İçeri Aktarma işlemiyle ilgili üst düzey bir genel bakış için, bu [makalenin İçeri aktarma işlemi](#how-the-import-process-works) nasıl çalışır? bölümüne bakın.

## <a name="step-1-copy-the-sas-url-and-download-azcopy"></a>1. Adım: SAS URL'sini kopyalama ve AzCopy'yi indirme

İlk adım, 2. Adımda çalıştırarak PST dosyalarını Dosya'ya yüklemek için azCopy aracını Microsoft 365. Ayrıca, kurum için SAS URL'sini de kopyalarsiniz. Bu URL, azure ağ URL'si ile Depolama Microsoft bulutunda yer alan ağ URL'si ve bir Paylaşılan Erişim İmzası (SAS) anahtarıdır. Bu anahtar, PST dosyalarını azure depolama veya depolama Depolama sağlar. SAS URL'sini korumak için önlemler almaya emin olun. Bu, sizin için benzersizdir ve 2. Adımda kullanılacaktır.

> [!IMPORTANT]
> PST dosyalarını, bu makalede belgelenmiş ağ karşıya yükleme yöntemi ve komut söz dizimi kullanarak içeri aktarma için, aşağıdaki yordamın 6b. adımında indirilebilen AzCopy sürümünü kullanmalıdır. AzCopy'nin aynı sürümünü buradan da [indirebilirsiniz](https://aka.ms/downloadazcopylatest). AzCopy'nin farklı bir sürümünü kullanma desteklemektedir.
  
1. <https://compliance.microsoft.com> Gidip, kurumda yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. İlke bölmesinin sol bölmesinde, Microsoft 365 uyumluluk merkezi yönetimi İçeri **Aktar'a** \> **tıklayın**.

    > [!NOTE]
    > Ana sayfada İçeri Aktar sayfasına erişmek için uygun **izinlerin** atan Microsoft 365 uyumluluk merkezi. Daha fazla **bilgi için Başlamadan** önce bölümüne bakın. 

3. İçeri Aktar **sekmesinde** Simge Ekle'ye ![tıklayın.](../media/ITPro-EAC-AddIcon.gif) **Yeni içeri aktarma işi**.

    İçeri aktarma işi sihirbazı görüntülenir.

4. PST içeri aktarma işi için bir ad yazın ve ardından Sonraki'ye **tıklayın**. Küçük harf, sayı, kısa çizgi ve alt çizgi kullanın. Büyük harf kullanamaz veya adlarında boşluk ekemezsiniz.

5. Verileri karşıya **yüklemek veya sevk etmek istiyor musunuz? sayfasında Verilerinizi** karşıya Upload **sonra da** Sonraki'yi **tıklatın**.

    ![Ağ Upload içeri aktarma işi oluşturmak için verilerinizi toplama'ya tıklayın.](../media/e59f9dc3-ccde-44ff-ac38-c4e39d76ae85.png)
  
6. Veri **içeri aktar** sayfasında, aşağıdaki iki işlemi yapın:

    ![SAS URL'sini kopyalayın ve Verileri içeri aktar sayfasındaki AzCopy aracını indirin.](../media/74411014-ec4b-4e25-9065-404c934cce17.png)
  
    1. 2. adımda, Ağ karşıya yükleme **SAS URL'sini göster'e tıklayın**. SAS URL'si görüntülendikten sonra, **Panoya** kopyala'ya tıklayın ve daha sonra erişmek için yapıştırarak bir dosyaya kaydedin.

    2. 3. adımda, **AzCopy aracını yerel** bilgisayarınıza indirmek için Azure AzCopy'yi İndir'e tıklayın. AzCopy'nin bu sürümü yalnızca yürütülebilir bir dosyadır, dolayısıyla hiçbir şey yüklenmez.

   > [!NOTE]
   > Veri içeri aktar sayfasını **açık** bırakın (SAS URL'sini yeniden kopyalamanız gerekiyor olabilir) veya İptal'e **tıklayıp** URL'yi kapatabilirsiniz.

## <a name="step-2-upload-your-pst-files-to-microsoft-365"></a>2. Adım: UPLOAD dosyalarınızı başka bir Microsoft 365

Artık PST dosyalarını karşıya yüklemek için AzCopy aracını kullanmaya Microsoft 365. Bu araç PST dosyalarını Microsoft tarafından sağlanan bir Azure bulut Depolama konuma yükler ve depolar. Daha önce de Depolama olarak, PST dosyalarınızı karşıya yüklediğiniz Azure Depolama konumu, aynı bölgesel Microsoft veri merkezinde yer alır. Bu adımı tamamlamak için PST dosyalarının, kurumuz tarafından yönetilen bir dosya paylaşımında veya dosya sunucusunda ya da Azure Depolama bir konumda yer alıyor olması gerekir. PST depolama konumu, bu yordamda kaynak konum olarak bilinir. AzCopy aracını her çalıştırabilirsiniz, farklı bir kaynak konumu belirtebilirsiniz.

> [!NOTE]
> Daha önce de belirtildiği gibi, Azure Posta'ya yüklediğiniz her PST Depolama 20 GB'tan büyük olmalıdır. 20 GB'tan büyük PST dosyaları, 6. Adım'da başlatan PST içeri aktarma işleminin performansını etkileyebilir. Ayrıca, her PST dosyasının benzersiz bir adı olmalıdır.

1. Yerel bilgisayarınızda Komut İstemi'ne açın.

2. 1. Adım'da, azcopy.exe indirdiğiniz dizine gidin.

3. PST dosyalarını karşıya yüklemek için aşağıdaki komutu Microsoft 365.

    ```powershell
    azcopy.exe copy "<Source location of PST files>" "<SAS URL>"
    ```

    > [!IMPORTANT]
    > Bir dizini veya Azure Azure Depolama önceki komutun kaynak konumu olarak belirtebilirsiniz; tek bir PST dosyası belirleyemezseniz. Kaynak konumdaki tüm PST dosyaları karşıya yükler.

    Aşağıdaki tabloda, tablodaki azcopy.exe değerleri ve bunların gerekli değerleri açıkmektedir. Önceki adımda edinilen bilgiler, bu alanların değerlarında kullanılır.

    | Alan | Açıklama |
    |:-----|:-----|
    | Kaynak |İlk alan, bilgisayarınıza yüklenen PST dosyalarını içeren kaynak dizini belirtir ve bu dizin Microsoft 365. Alternatif olarak, karşıya yüklenilen PST Depolama kaynak konumu olarak bir Azure Depolama Alanı konumu belirtebilirsiniz. <br/> Bu alanın değerini çift tırnak işaretleri (" ") içine almanız gerekir.  <br/> <br/>**Örnekler**: <br/>`"\\FILESERVER01\PSTs"` <br/> Veya  <br/>`"https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx"`|  
    | Hedef |1. Adımda edinilen SAS URL'sini belirtir.  <br/> Bu parametrenin değerini çift tırnak işaretleri (" ") içine almanız gerekir.<br/><br/>**Not:** Sas URL'sini bir betikte veya toplu işlem dosyasında kullanıyorsanız, karakterin dışarı kaç olması gereken bazı karakterlere dikkat edin. Örneğin, olarak değiştirmeli `%` ve `%%` olarak değiştirlisiniz `&` `^&`.<br/><br/>**İpucu:** (İsteğe bağlı) PST dosyalarını karşıya yüklemek için Azure Depolama bir alt klasör belirtebilirsiniz. Bu, SAS URL'sinde bir alt klasör konumu (ingestiondata'dan sonra") ekleyerek bunu yapar. İlk örnekte bir alt klasör belirtmezseniz. Bu, PST'lerin Azure Veri Sayfası konumunun köküne (*ingestiondata* olarak adlandırılmış) Depolama gelir. İkinci örnekte, PST dosyaları Azure Dosya Konumu'nın kökünde bir alt klasöre (*PSTFiles* Depolama yükler.  <br/><br/>**Örnekler**: <br/> `"https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"` <br/> Veya  <br/>  `"https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata/PSTFiles?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"` <br/> |
    | `--recursive` |Bu isteğe bağlı bayrak, azCopy aracının kaynak alan tarafından belirtilen kaynak dizinde alt klasörlerde yer alan PSTS dosyalarını kopyalar. Bu bayrağın varsayılan değeri: `true`. <br/>**Not:** Bu bayrağı belirtirsiniz, alt klasörlere PST dosyaları karşıya yüklendikten sonra Azure Depolama konumlarına farklı bir dosya yol adı olur. 4. Adımda oluşturmak istediğiniz CSV dosyasında tam dosya yol adını belirtmeniz gerekir.|
    | `--s2s-preserve-access-tier` | Bu isteğe bağlı bayrak yalnızca kaynak konum, erişim katmanlarını destekleyen genel amaçlı bir v2 Azure Depolama konumu olduğunda gereklidir. PST İçeri Aktarma senaryosunda, Azure Depolama hesabınızdan Microsoft tarafından sağlanan Azure veritabanına PST dosyaları kopyalayıp bu konuma Depolama gerek yoktur. Bu durumda, bu bayrağı ek olarak kullanabilir ve 'ın değerini kullanabilirsiniz `false`. Erişim katmanlarını desteklemeen klasik bir Azure Depolama hesabından PST dosyalarını kopyalarken bu bayrağı kullanmak zorunda değilsiniz.|
   |||

Kopyalama komutu hakkında daha **fazlaazcopy.exe için** bkz. [azcopy kopyalama](/azure/storage/common/storage-ref-azcopy-copy).

Aşağıda, her parametrenin gerçek değerlerini kullanarak AzCopy aracının söz dizimi örnekleri verilmiştir.

### <a name="example-1"></a>Örnek 1

Bu, dosya sunucusunda veya yerel bilgisayarda bulunan bir kaynak dizin için bir örnektir.

```powershell
azcopy.exe copy "\\FILESERVER1\PSTs" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"
```

### <a name="example-2"></a>Örnek 2

Bu, klasik Azure Depolama hesabında bulunan bir kaynak dizini için bir örnektir.

```powershell
azcopy.exe copy "https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D" --recursive
```

### <a name="example-3"></a>Örnek 3

Bu, genel amaçlı v2 Azure Depolama hesabında bulunan bir kaynak Depolama örneğidir. PST dosyaları karşıya yük olduğunda Access katmanları korunmaz.

```powershell
azcopy.exe copy "https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D" --s2s-preserve-access-tier=false
```

Komutu çalıştırdikten sonra, PST dosyalarını karşıya yüklemenin ilerleme durumunun görüntülendiğinde durum iletileri görüntülenir. Son durum iletisi, başarıyla karşıya yüklenen toplam dosya sayısını gösterir.

> [!TIP]
> **azcopy.exe** kopyala komutunu başarıyla çalıştırdikten ve tüm parametrelerin doğru olduğunu doğrulayan sonra, 1. Adımda edinilen bilgileri kopyalayıp aynı (güvenli) dosyanın komut satırı sözdiziminin bir kopyasını kaydedin. Ardından, PST dosyalarını Dosya'ya yüklemek için AzCopy aracını her çalıştırmak istediğiniz her komut için Komut İstemi'nde bu komutu kopyalayıp Microsoft 365. Değiştirmek zorunda olabileceğiniz tek değer kaynak alandır. Bu, PST dosyalarının bulunduğu kaynak dizine bağlıdır.

## <a name="optional-step-3-view-a-list-of-the-pst-files-uploaded-to-microsoft-365"></a>(İsteğe bağlı) 3. Adım: Posta'ya yüklenen PST dosyalarının Microsoft 365

İsteğe bağlı bir adım olarak, Azure blob'a yüklediğiniz PST dosyalarının listesini görüntülemek için Microsoft Azure Depolama Gezgini aracını (ücretsiz, açık kaynak araçtır) yükleyebilir ve kullanabilirsiniz. Bunu yapmak için iki iyi neden vardır:
  
- Kuruluşta paylaşılan klasör veya dosya sunucusundaki PST dosyalarının Azure blob'a başarıyla yük doğrulamak.

- Azure blob'a yüklenen her PST dosyası için dosya adını (ve varsa alt klasör yol adını) doğrulayın. Bu, sonraki adımda PST eşleme dosyasını oluştururken yararlı olur, çünkü her PST dosyası için hem klasör yol adını hem de dosya adını belirtmeniz gerekir. Bu adların doğrunlaması PST eşleme dosyanız için olası hataları azaltmaya yardımcı olabilir.

Tek Azure Depolama Gezgini olan uygulama genel olarak kullanılabilir. Aşağıdaki yordamda yer alan bağlantıyı kullanarak en son sürümü indirebilirsiniz.
  
> [!IMPORTANT]
> PST dosyalarını karşıya yüklemek Azure Depolama Gezgini değiştirmek için e-posta dosyasını değiştiremezsiniz. PST dosyalarını içeri aktarmanın tek desteklenen yöntemi AzCopy kullanmaktır. Ayrıca Azure blob'larına yüklediğiniz PST dosyalarını silemezsiniz. Bir PST dosyasını silmeyi denersanız, gerekli izinlere sahip olmadığınız konusunda bir hata alırsınız. Tüm PST dosyalarının Azure depolama alanınıza otomatik olarak silineceklerini unutmayın. Devam eden bir içeri aktarma işi yoksa, **ingestiondata** kapsayıcısında yer alan tüm PST dosyaları, en son içeri aktarma işi oluşturulduktan 30 gün sonra silinir.
  
Azure Azure Depolama Gezgini alanınıza bağlanmak ve alanınıza bağlanmak Depolama:
  
1. Office 365'i [Microsoft Azure Depolama Gezgini yükleyin](https://go.microsoft.com/fwlink/p/?LinkId=544842).

2. Başlat'Microsoft Azure Depolama Gezgini.

3. Azure **Bağlan** iletişim **kutusundaki Kaynak Seç Depolama** **Blob kapsayıcısı'a tıklayın**.
  
4. Kimlik Doğrulama **Yöntemi Seç sayfasında** Paylaşılan erişim imzası **(SAS)** seçeneğini belirtin ve ardından Sonraki'ye **tıklayın**.

5. Bağlantı Bilgilerini **Girin sayfasında** , 1. Adımda edinilen SAS URL'sini **Blob kapsayıcı SAS URL'si** altındaki kutuya yapıştırın ve ardından Sonraki'ye **tıklayın**. SAS URL'sini yapıştırdikten sonra, **Görünen ad'ın** altındaki kutu **ingestiondata ile otomatik olarak gösterilir**.

6. Özet **sayfasında,** bağlantı bilgilerini gözden geçirebilirsiniz ve sonra Tamam'a **Bağlan**.

    **ingestiondata kapsayıcısı** açılır. 2. Adımda karşıya yüklediğiniz PST dosyalarını içerir. **ingestiondata kapsayıcısı**, Hesaplar (**Depolama Kapsayıcılar** \> **) Blob Kapsayıcıları'nın** \> **altında yer almaktadır**. 
  
7. Kaynak verilerini kullanmayı bitirdikten sonra, Microsoft Azure Depolama Gezgini **ingestiondata'ya** sağ tıklayın ve Azure Veri Alanı ile bağlantınızı  kesmek için Ayır'Depolama tıklayın. Aksi takdirde, eklemeye bir sonraki denemede hata alırsınız.
  
## <a name="step-4-create-the-pst-import-mapping-file"></a>4. Adım: PST İçeri Aktarma eşleme dosyasını oluşturma

PST dosyaları, kuruluşun Azure Depolama konuma yüklendikten sonra, bir sonraki adım PST dosyalarının hangi kullanıcı posta kutularına aktar alın olacağını belirten bir virgülle ayrılmış değer (CSV) dosyası oluşturmaktır. BIR PST İçeri Aktarma işi  oluşturmanın sonraki adımında bu CSV dosyasını gönderebilirsiniz.
  
1. [PST İçeri Aktarma eşleme dosyasının bir kopyasını indirin](https://go.microsoft.com/fwlink/p/?LinkId=544717).

2. CSV dosyasını yerel bilgisayarınıza açın veya kaydedin. Aşağıdaki örnekte tamamlanmış bir PST İçeri Aktarma eşleme dosyası (Not Defteri'de açılır) gösterir. CSV dosyasını düzenlemek için Microsoft Excel çok daha kolay.

    ```console
    Workload,FilePath,Name,Mailbox,IsArchive,TargetRootFolder,ContentCodePage,SPFileContainer,SPManifestContainer,SPSiteUrl
    Exchange,,annb.pst,annb@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,,annb_archive.pst,annb@contoso.onmicrosoft.com,TRUE,,,,,
    Exchange,,donh.pst,donh@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,,donh_archive.pst,donh@contoso.onmicrosoft.com,TRUE,,,,,
    Exchange,PSTFiles,pilarp.pst,pilarp@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,PSTFiles,pilarp_archive.pst,pilarp@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,PSTFiles,tonyk.pst,tonyk@contoso.onmicrosoft.com,FALSE,,,,,
    Exchange,PSTFiles,tonyk_archive.pst,tonyk@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,PSTFiles,zrinkam.pst,zrinkam@contoso.onmicrosoft.com,FALSE,,,,,
    Exchange,PSTFiles,zrinkam_archive.pst,zrinkam@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    ```

    CSV dosyasının ilk satırı veya üst bilgi satırı, PST dosyalarını kullanıcı posta kutularına içeri aktarmada PST İçeri Aktarma hizmeti tarafından kullanılacak parametreleri listeler. Her parametre adı virgülle ayrılmıştır. Üst bilgi satırın altındaki her satır, PST dosyasını belirli bir posta kutusuna içeri aktarmaya yönelik parametre değerlerini temsil eder. Kullanıcı posta kutusuna içeri aktarma işlemi yapmak istediğiniz her PST dosyası için bir satıra ihtiyacınız vardır. CSV eşleme dosyasında en çok 500 satır olabilir. 500'den fazla PST dosyasını içeri aktarmak için, 5. Adımda birden çok eşleme dosyası oluşturmanız ve birden çok içeri aktarma işi oluşturmanız gerekir.

    > [!NOTE]
    > Üst bilgi satırındaki üst bilgi ve alt SharePoint, PST İçeri Aktarma işlemi sırasında yok sayılacaktır. Ayrıca, eşleme dosyasındaki yer tutucu verilerini gerçek verilerinizle değiştir mutlaka.

3. CSV dosyasını gerekli bilgilerle doldurmak için aşağıdaki tabloda yer alan bilgileri kullanın.

    | Parametre | Açıklama | Örnek |
    |:-----|:-----|:-----|
    | `Workload` <br/> |Verilerin aktaracağız hizmeti belirtir. PST dosyalarını kullanıcı posta kutularına içeri aktarma için, ' kullanın  `Exchange`.  <br/> | `Exchange` <br/> |
    | `FilePath` <br/> |Azure Veri Hizmetleri'Depolama PST dosyalarını yüklediğiniz klasörü konumunu 2. Adım'da belirtir.  <br/> 2. Adımda parametrenin SAS URL'sinde  `/Dest:` isteğe bağlı bir alt klasör adı yoksa, CSV dosyasında bu parametreyi boş bırakın. Bir alt klasör adı dahil ettiysanız bu parametreyi belirtin (ikinci örnekteki adıma bakın). Bu parametrenin değeri büyük/harfe duyarlıdır.  <br/> Her iki  *şekilde de parametrenin*  değerine "ingestiondata" dahil  `FilePath` etme.  <br/><br/> **Önemli:** 2. Adım'da hedef alana SAS URL'sine isteğe bağlı bir alt klasör adı kullandıysanız, dosya yolu adının büyük/yeni adı ile aynı olmalıdır. Örneğin, 2 `pstfiles` `FilePath`. `PSTFiles` Adım'da alt klasör adı için kullandınız ve ardından CSV dosyasındaki parametrede kullandıysanız, PST dosyası için içeri aktarma işlemi başarısız olur. Her iki durumda da aynı vakayı kullanmaya emin olun.  <br/> |(boş bırakın)  <br/> Veya  <br/>  `PSTFiles` <br/> |
    | `Name` <br/> |Kullanıcı posta kutusuna aktaracak PST dosyasının adını belirtir. Bu parametrenin değeri büyük/harfe duyarlıdır. İçeri aktarma işinin eşleme dosyasındaki her PST dosyasının adı benzersiz olmalıdır. <br/> <br/>**Önemli:** CSV dosyasındaki PST dosya adının durumu, 2. Adım'daki Azure Depolama konuma yüklenen PST dosyasıyla aynı olması gerekir. Örneğin, CSV dosyasındaki parametrede  `annb.pst`  `Name` kullanırsanız, ancak gerçek PST dosyasının adı aşağıdaki gibi olursa, bu PST `AnnB.pst`dosyası için içeri aktarma işlemi başarısız olur. CSV dosyasındaki PST adının gerçek PST dosyasıyla aynı vakayı kullandığından emin olun.  <br/> | `annb.pst` <br/> |
    | `Mailbox` <br/> |PST dosyasının içeri aktarılmaz olduğu posta kutusunun e-posta adresini belirtir. PST İçeri Aktarma Hizmeti PST dosyalarını ortak klasörlere içeri aktarmayı desteklemez, çünkü ortak klasör belirtemezseniz.  <br/> PST dosyasını etkin olmayan bir posta kutusuna içeri aktarmak için, bu parametrenin posta kutusu GUID'ını belirtmeniz gerekir. Bu GUID'i almak için, Guid'te aşağıdaki PowerShell Exchange Online:`Get-Mailbox <identity of inactive mailbox> -InactiveMailboxOnly | FL Guid` <br/> <br/>**Not:** Bazen, aynı e-posta adresine sahip birden çok posta kutunuz olabilir; burada bir posta kutusu etkin bir posta kutusu ve diğer posta kutusu da yumuşak silinmiş (veya etkin olmayan) durumdadır. Bu gibi durumlarda, PST dosyasını içeri aktarın posta kutusunu benzersiz bir şekilde tanımlamak için posta kutusu GUID'ını belirtmeniz gerekir. Etkin posta kutuları için bu GUID'i almak için aşağıdaki PowerShell komutunu çalıştırın:  `Get-Mailbox <identity of active mailbox> | FL Guid`. Yumuşak silinmiş (veya etkin olmayan) posta kutularının GUID'sini almak için, bu komutu çalıştırın  `Get-Mailbox <identity of soft-deleted or inactive mailbox> -SoftDeletedMailbox | FL Guid`.  <br/> | `annb@contoso.onmicrosoft.com` <br/> Veya  <br/>  `2d7a87fe-d6a2-40cc-8aff-1ebea80d4ae7` <br/> |
    | `IsArchive` <br/> | PST dosyasının kullanıcının arşiv posta kutusuna aktarıp aktarılamayında bir değer belirtir. İki seçenek vardır:  <br/><br/>**YANLIŞ:** PST dosyası kullanıcının birincil posta kutusuna içeri aktarır.  <br/> **DOĞRU:** PST dosyası kullanıcının arşiv posta kutusuna içeri aktarır. Burada, kullanıcının arşiv [posta kutusunun etkinleştirilmiştir](enable-archive-mailboxes.md). <br/><br/>Bu parametreyi olarak ayarlasanız  `TRUE` ve kullanıcının arşiv posta kutusu etkinleştirilmediyse, bu kullanıcıya yapılan içeri aktarma işlemi başarısız olur. Bir kullanıcı için içeri aktarma işlemi başarısız olursa (  `TRUE`arşivi etkin değilse ve bu özellik olarak ayarlanmışsa), içeri aktarma işinden diğer kullanıcılar etkilenmez.  <br/>  Bu parametreyi boş bırakırsanız, PST dosyası kullanıcının birincil posta kutusuna aktarılır.  <br/> <br/>**Not:** Birincil posta kutusu şirket içinde olan bir kullanıcının PST dosyasını bulut tabanlı bir arşiv posta kutusuna içeri aktarmanız için,  `TRUE`  `Mailbox` bu parametreyi belirtmeniz ve parametrenin kullanıcının şirket içi posta kutusunun e-posta adresini belirtmeniz gerekir.  <br/> | `FALSE` <br/> Veya  <br/>  `TRUE` <br/> |
    | `TargetRootFolder` <br/> | PST dosyasının içeri aktar olduğu posta kutusu klasörünü belirtir.  <br/> <br/> Bu parametreyi boş bırakırsanız, PST dosyası posta kutusunun kök düzeyinde (Gelen Kutusu klasörü ve  diğer varsayılan posta kutusu klasörleriyle aynı düzeyde) Alınan adlı yeni bir klasöre aktarılır.  <br/> <br/> belirtirsiniz  `/`, PST dosyasındaki klasörler ve öğeler hedef posta kutusunda veya arşivde klasör yapısının en üstüne aktarılır. Hedef posta kutusunda bir klasör varsa (örneğin, Gelen Kutusu, Gönderilmiş Öğeler ve Silinmiş Öğeler gibi varsayılan klasörler), PST'de bu klasördeki öğeler hedef posta kutusunda var olan klasörle birleştirilir. Örneğin, PST dosyasında bir Gelen Kutusu klasörü varsa, o klasördeki öğeler hedef posta kutusunun Gelen Kutusu klasörüne aktarılır. Hedef posta kutusunun klasör yapısında yoksa yeni klasörler oluşturulur.  <br/><br/>  belirtirsiniz  `/<foldername>`, PST dosyasındaki öğeler ve klasörler adlı bir klasöre aktarılır  *\<foldername\>*  . Örneğin, kullanırsanız,  `/ImportedPst`öğeler **importedPst adlı bir klasöre aktarılmış olabilir**. Bu klasör, kullanıcının posta kutusunda Gelen Kutusu klasörüyle aynı düzeyde bulunur.  <br/><br/> **İpucu:** PSTS dosyalarını içeri aktarın en iyi klasör konumunu belirlemek için, bu parametreyi denemek üzere birkaç test toplu işlemi çalıştırmayı göz önünde bulundurabilirsiniz.  <br/> |(boş bırakın)  <br/> Veya  <br/>  `/` <br/> Veya  <br/>  `/ImportedPst` <br/> |
    | `ContentCodePage` <br/> |Bu isteğe bağlı parametre, ANSI dosya biçiminde PST dosyalarını içeri aktarmada kullanılan kod sayfası için sayısal bir değer belirtir. Bu diller normalde karakter kodlaması için çift bayt karakter kümesi (DBCS) kullandığından, bu parametre Çince, Japonca ve Korece (CJK) kuruluşlarından PST dosyalarını içeri aktarmada kullanılır. Posta kutusu klasör adları olarak DBCS kullanan dillerin PST dosyalarını içeri aktarmada bu parametre kullanılmazsa, klasör adları içeri aktarıldıktan sonra çoğunlukla bozuk olur.  <br/><br/> Bu parametrede kullanmak üzere desteklenen değerlerin listesi için bkz. [Kod Sayfası Tanımlayıcıları](/windows/win32/intl/code-page-identifiers).  <br/> <br/>**Not:** Daha önce de belirtildiği gibi, bu isteğe bağlı bir parametredir ve bunu CSV dosyasına eklemek zorunda değildir. Veya bu değeri dahil etmek ve bir veya birden çok satır için değeri boş bırakabilirsiniz.  <br/> |(boş bırakın)  <br/> Veya  <br/>  `932` (ANSI/OEM Japonca için kod sayfası tanımlayıcısıdır)  <br/> |
    | `SPFileContainer` <br/> |PST İçeri Aktarma için, bu parametreyi boş bırakın.  <br/> |Uygulanamaz  <br/> |
    | `SPManifestContainer` <br/> |PST İçeri Aktarma için, bu parametreyi boş bırakın.  <br/> |Uygulanamaz  <br/> |
    | `SPSiteUrl` <br/> |PST İçeri Aktarma için, bu parametreyi boş bırakın.  <br/> |Geçerli değil  <br/> |

## <a name="step-5-create-a-pst-import-job"></a>5. Adım: PST İçeri Aktarma işi oluşturma

Sonraki adım, bu hizmetin içeri aktarma hizmetsinde PST İçeri Aktarma işini Microsoft 365. Daha önce de belirtildiği gibi, 4. Adımda oluşturduğunuz PST İçeri Aktarma eşleme dosyasını gönderin. Siz işi oluşturdukktan sonra, Microsoft 365 PST dosyalarında yer alan verileri analiz eder ve size PST içeri aktarma eşleme dosyasında belirtilen posta kutularına gerçekten içeri aktarılan verileri filtreleme fırsatı verir (bkz. [6](#step-6-filter-data-and-start-the-pst-import-job). Adım).
  
1. <https://compliance.microsoft.com> Gidip, kurumda yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. Yönetim bölmesinin sol bölmesinde, Microsoft 365 uyumluluk merkezi yönetimi'ne **ve sonra İçeri Aktarma'> tıklayın**.

3. İçeri Aktar **sekmesinde** Simge Ekle'ye ![tıklayın.](../media/ITPro-EAC-AddIcon.gif) **Yeni içeri aktarma işi**.

   > [!NOTE]
   > Bir içeri aktarma işi oluşturmak için çalışma sayfasındaki İçeri **Aktar** sayfasına erişmek Microsoft 365 uyumluluk merkezi izinlere atanmış olması gerekir. Daha fazla **bilgi için Başlamadan** önce bölümüne bakın. 

4. PST içeri aktarma işi için bir ad yazın ve ardından Sonraki'ye **tıklayın**. Küçük harf, sayı, kısa çizgi ve alt çizgi kullanın. Büyük harf kullanamaz veya adlarında boşluk ekemezsiniz.

5. Verileri karşıya **yüklemek veya sevk etmek istiyor musunuz? sayfasında Verilerinizi** karşıya Upload **sonra da** Sonraki'yi **tıklatın**.
  
6. Verileri içeri aktarma sayfasının 4.  adımında, Dosyalarımı karşıya yüklemem bitti ve eşleme dosyası onay kutularına  erişimim var onay kutularına tıklayın ve sonra da Sonraki'ye **tıklayın**.

    ![4. adımda iki onay kutusunu tıklatın.](../media/9f2427e8-3af2-4e27-95e6-a9f08430d3d8.png)
  
7. Eşleme **dosyasını seçin sayfasında** , 4. Adımda **oluşturduğunuz** CSV eşleme dosyasını göndermek için Eşleme dosyasını seç'e tıklayın.

    ![İçeri aktarma işi için oluşturduğunuz CSV dosyasını göndermek için Eşleme dosyası seç'e tıklayın.](../media/d30b1d73-80bb-491e-a642-a21673d06889.png)
  
8. CSV dosyasının adı Dosya adı eşleme **altında göründüğünde,** CSV dosyanızı hatalı **olarak görmek** için Doğrula'ya tıklayın.

    ![CSV dosyasındaki hataları kontrol etmek için Doğrula'ya tıklayın.](../media/4680999d-5538-4059-b878-2736a5445037.png)
  
    PST İçeri Aktarma işi oluşturmak için CSV dosyasının başarıyla doğrulanması gerekir. Dosya adı, başarıyla doğrulandıktan sonra yeşil olarak değiştirilir. Doğrulama başarısız olursa, Günlüğü görüntüle **bağlantısını** tıklatın. Dosyadaki başarısız olan her satır için bir hata iletisiyle birlikte bir doğrulama hatası raporu açılır.

   > [!NOTE]
   > Daha önce de belirtildiği gibi, eşleme dosyasının en çok 500 satırı olabilir. Eşleme dosyasında 500'den fazla satır varsa, doğrulama başarısız olur. 500'den fazla PST dosyasını içeri aktarmak için, birden çok eşleme dosyası ve birden çok içeri aktarma işi oluşturmanız gerekir.

9. Eşleme dosyası başarıyla doğrulandıktan sonra, hüküm ve koşullar belgesini okuyun ve sonra onay kutusuna tıklayın.

10. Işi **göndermek** için Kaydet'e tıklayın ve sonra iş **başarıyla** oluşturulduktan sonra Kapat'a tıklayın.

    Durum dışarı aktarma sayfası görüntülenir; Çözümleme devam ediyor **durumundadır** ve PST dosyalarını içeri aktar sayfasındaki listede yeni **içeri aktarma işi** görüntülenir.

11. Yenile **simgesini** ![tıklatın.](../media/O365-MDM-Policy-RefreshIcon.gif) seçin. Çözümleme tamamlandığında ve veriler aktar gitmeye hazır olduğunda, durum Çözümleme tamamlandı olarak **değiştirilir**.

    Eşleme dosyasında listelenen her PST dosyasının durumu gibi içeri aktarma işi hakkında daha ayrıntılı bilgiler içeren durum uç noktası sayfasını görüntülemek için içeri aktarma işini tıklatabilirsiniz.

## <a name="step-6-filter-data-and-start-the-pst-import-job"></a>6. Adım: Verileri filtreleme ve PST İçeri Aktarma işini başlatma

5. Adımda içeri aktarma işini oluşturduk tan sonra, Microsoft 365 PST dosyalarında yer alan öğelerin yaşını ve farklı ileti türlerini tanımarak PST dosyalarıdaki verileri (güvenli ve güvenli bir şekilde) analiz eder. Çözümleme tamamlandığında ve veriler içeri aktarmaya hazır olduğunda, PST dosyalarında yer alan tüm verileri içeri aktarma seçeneğiniz vardır veya içeri aktarılan verileri, hangi verilerin içeri aktar ayarlanacaklarını denetimi altına alan filtreler ayararak kırpabilirsiniz.
  
1. Dosyanın **İçeri** Aktar sekmesinde Microsoft 365 uyumluluk merkezi 5. Adımda oluşturduğunuz içeri aktarma işlerini seçin ve sonra da İçeri **Aktar'a** Microsoft 365.
  
   Verilerinizi **filtrele** sayfası görüntülenir. Verilerin yaşıyla ilgili bilgiler de dahil olmak üzere, PST dosyaları üzerinde MICROSOFT 365 tarafından gerçekleştirilen çözümlemeden elde edilen veri içgörülerini içerir. Bu noktada, içeri aktaracak veya tüm verileri olduğu gibi içeri aktaracak verilere filtre uygulama seçeneğiniz vardır. 

    ![PST dosyalarında verileri kırpabilirsiniz veya hepsini içeri aktarabilirsiniz.](../media/287fc030-99e9-417b-ace7-f64617ea5d4e.png)
  
2. Şunlardan birini yapın:

   1. İçeri aktarınan verileri kırpmak için Evet **, içeri aktarmadan önce filtrelemek istiyorum'a tıklayın**.

      PST dosyalarında verileri filtreleme ve içeri aktarma işini başlatma hakkında ayrıntılı adım adım yönergeler için bkz. PST dosyalarını içeri aktararak içeri aktarma ve içeri aktarma [Microsoft 365](filter-data-when-importing-pst-files.md).

      Veya

   2. PST dosyalarında yer alan tüm verileri içeri aktarmak için Hayır, her şeyi içeri **aktarmayı istiyorum'a ve Sonra'ya** **tıklayın**.

3. Tüm verileri içeri aktarmayı seçtiysiniz, içeri **aktarma işini başlatmak için Verileri** içeri aktar'a tıklayın. 

   PST dosyalarını içeri aktar sayfasında içeri aktarma **işinin durumu görüntülenir** . Yenile ![simgesine tıklayın.](../media/O365-MDM-Policy-RefreshIcon.gif) **Durum** sütununda görüntülenen durum bilgilerini güncelleştirmek **için yenileyin** . İçeri aktarılan her PST dosyasıyla ilgili durum bilgilerini görüntüleyen durum uç sayfası görüntülemek için içeri aktarma işini tıklatın.

## <a name="more-information"></a>Daha fazla bilgi

- PST dosyaları neden başka bir Microsoft 365?

  - Bu, arşivlemek için kuruluş mesajlaşma verilerini arşivlemek için iyi bir Microsoft 365.

  - Veriler, bulutta depolandığı için tüm cihazlardan kullanıcıya mevcuttur.

  - Bu, içeri aktarılmış PST dosyalarından gelen verilere uyumluluk Microsoft 365 izin vererek, kuruluş uyumluluk 2013'e yardımcı olur. Bu şunları içerir:

  - Arşiv posta [kutularını etkinleştirme ve kullanıcılara](enable-archive-mailboxes.md) [aktarılmış verileri depolamak](enable-autoexpanding-archiving.md) için ek posta kutusu depolama alanı sağlamak için otomatik genişleyen arşivleme.

  - Aktarmış olduğunuz [verileri tutmak için posta](./create-a-litigation-hold.md) kutularını Mahkeme Tutma'ya yerleştirebilirsiniz.

  - İçe [aktarılmış olan veride arama](search-for-content.md) yapmak için Microsoft eBulma araçlarını kullanma.

  - [İlke Microsoft 365 aktarmış](retention.md) olunan verilerin ne kadar süreyle tutulacaklarını ve bekletme süresinin sona erdikten sonra ne kadar süreyle tutulacaklarını denetlemeye yönelik bekletme ilkeleri kullanma.

  - Denetim [günlüğünde,](search-the-audit-log-in-security-and-compliance.md) aktarılmış verileri etkileyen, posta kutusuyla ilgili olaylar için arama yapılıyor.

  - Uyumluluk amacıyla verileri [arşivlemek için etkin olmayan](inactive-mailboxes-in-office-365.md) posta kutularına veri aktarma. 

  - Hassas [verilerin kuruluş dışına sızdır](dlp-learn-about-dlp.md) olmasını önlemek için veri kaybı önleme ilkelerini kullanma.

- Daha önce de Microsoft 365 olarak, PST dosyaları posta kutusuna aktarıldıktan sonra İçeri Aktarma hizmeti belirsiz bir süre boyunca bekletme ayarını etkinleştirir. Bu, posta kutusuna atanan bekletme ilkesi işlenmemeyecek şekilde  *RetentionHoldEnabled*  özelliğinin  **True** olarak ayar olduğu anlamına gelir. Bu, posta kutusu sahibine eski iletileri silme veya arşivleme ilkesi silmesini veya arşivlemesini engelerek, yeni aktarılan iletileri yönetmesi için zaman verir. Bu bekletmeyi yönetmek için atılması gereken bazı adımlar:

  - Belirli bir süre sonra, **Set-Mailbox -RetentionHoldEnabled veya $false komutunu çalıştırarak bekletmeyi $false** kapatabilirsiniz. Yönergeler için bkz. [Posta kutusunu bekletmeye saklama](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

  - Bekletmeyi yapılandırarak, gelecekte bir tarihte kapatıldığından emin olun. Bunu yapmak için **Set-Mailbox -EndDateForRetentionHold *tarih komutunu çalıştırabilirsiniz*** . Örneğin, bugünün tarihin 1 Haziran 2016 olduğunu ve 30 gün içinde bekletmenin kapalı tutulmasını istediğiniz varsayarak şu komutu çalıştırabilirsiniz:  **Set-Mailbox -EndDateForRetentionHold 7/1/2016**. Bu senaryoda,  **RetentionHoldEnabled özelliğini True**  olarak  *kümeli olarak bırakabilirsiniz*. Daha fazla bilgi için bkz. [Set-Mailbox](/powershell/module/exchange/set-mailbox).

  - Posta kutusuna atanmış olan bekletme ilkesi ayarlarını değiştirebilirsiniz; böylelikle, aktarılan eski öğeler hemen silinmez veya kullanıcının arşiv posta kutusuna taşınmaz. Örneğin, posta kutusuna atanmış bir silme veya arşiv ilkesi için bekletme süresini uzatabilirsiniz. Bu senaryoda, bekletme ilkesi ayarlarını değiştirdikten sonra posta kutusunda bekletme bekletmeyi kapatabilirsiniz. Daha fazla bilgi için bkz [. Kuruluşlarınız için posta kutuları için arşivleme ve silme ilkesi ayarlama](set-up-an-archive-and-deletion-policy-for-mailboxes.md).

### <a name="how-the-import-process-works"></a>İçeri aktarma işlemi nasıl çalışır?
  
PST dosyalarını kullanıcı posta kutularına toplu olarak içeri Microsoft 365 için ağ karşıya yükleme seçeneğini ve İçeri Aktarma hizmetini kullanabilirsiniz. Ağ karşıya yükleme, PST dosyalarını Microsoft bulutunda geçici bir depolama alanı olarak karşıya yüklediğiniz anlamına gelir. Ardından, Microsoft 365 Aktarma hizmeti depolama alanında yer alan PST dosyalarını hedef kullanıcı posta kutularına kopyalar.
  
PST dosyalarını diğer posta kutularına içeri aktarmaya ilişkin ağ karşıya yükleme işleminin bir çizimi ve Microsoft 365.
  
![PST dosyalarını karşıya yükleme için ağ karşıya yükleme işleminin iş Microsoft 365.](../media/9e05a19e-1e7a-4f1f-82df-9118f51588c4.png)
  
1. PST içeri aktarma aracını ve anahtarını özel **Azure Depolama** konumu için indirin: İlk adım, AzCopy komut satırı aracını ve PST dosyalarını Microsoft bulutunda bir Azure Depolama konuma yüklemek için kullanılan erişim anahtarını indirmektir. Bunları, çalışma **sayfasındaki İçeri** Aktar Microsoft 365 uyumluluk merkezi. Anahtar (güvenli erişim imzası (SAS) anahtarı olarak adlandırılan anahtar, PST dosyalarını özel ve güvenli bir Azure Ağ Konumu'Depolama sağlar. Bu erişim anahtarı, sizin için benzersizdir ve Microsoft buluta yüklendikten sonra PST dosyalarınıza yetkisiz erişimin önlenmesine yardımcı olur. PST dosyalarını içeri aktarma işlemi, kurum için ayrı bir Azure aboneliğinin olması gerektirmez. 

2. **Upload PST dosyalarını Azure Depolama'a taşıyın:** Sonraki adım, azcopy.exe aracını (1. adımda indirilen) kullanmak, PST dosyalarınızı, kurumla aynı bölgesel Microsoft veri merkezinde bulunan Azure Depolama konumlarına yüklemek ve depolamaktır. Bunları karşıya yüklemek için, içeri aktarma işlemi yapmak istediğiniz PST dosyalarının, kurumda bir dosya paylaşımında veya dosya sunucusunda yer almaları gerekir.

    PST dosyaları Azure Depolama konuma yüklendikten sonra, bu dosyaların listesini görüntülemek için isteğe bağlı bir Depolama vardır.

3. **PST içeri aktarma eşleme dosyası oluşturma:** PST dosyaları Azure Depolama konuma yüklendikten sonra, bir sonraki adım, PST dosyalarının hangi kullanıcı posta kutularına aktar alın olacağını belirten bir virgülle ayrılmış değer (CSV) dosyası oluşturmaktır. PST dosyasının kullanıcının birincil posta kutusuna veya kullanıcının arşiv posta kutusuna aktarılana dikkat edin. Veri Microsoft 365 Hizmeti, PST dosyalarını içeri aktarmada CSV dosyasındaki bilgileri kullanır.

4. **PST içeri aktarma işi oluşturma:** Sonraki adım, dosyanın PST dosyalarını içeri aktarma sayfasında **bir PST** içeri aktarma işi Microsoft 365 uyumluluk merkezi ve önceki adımda oluşturulan PST içeri aktarma eşleme dosyasını göndermektir. siz içeri aktarma işini oluşturdukktan sonra, Microsoft 365 PST dosyalarında yer alan verileri analiz eder ve size PST içeri aktarma eşleme dosyasında belirtilen posta kutularına gerçek olarak hangi verilerin içeri aktarılasını denetleme fırsatı verir. 

5. **Posta kutularına aktaracak PST verilerini filtrele:** İçeri aktarma işi oluşturulduktan ve başlatıldıktan sonra, Microsoft 365 PST dosyalarında bulunan öğelerin yaşını ve farklı ileti türlerini tanımarak (güvenli ve güvenli bir şekilde) PST dosyalarıdaki verileri analiz eder. Çözümleme tamamlandığında ve veriler içeri aktarmaya hazır olduğunda, PST dosyalarında yer alan tüm verileri içeri aktarma seçeneğiniz vardır veya içeri aktarılan verileri, hangi verilerin içeri aktar ayarlanacaklarını denetimi altına alan filtreler ayararak kırpabilirsiniz.

6. **PST içeri aktarma işini başlatma:** İçeri aktarma işi başlatıldıktan sonra, Microsoft 365 PST içeri aktarma eşleme dosyasındaki bilgileri kullanarak PSTS dosyalarını Azure Depolama posta kutularına aktarın. İşle ilgili durum bilgileri (içeri aktarılan her PST dosyasıyla ilgili bilgiler de dahil olmak üzere) pst  dosyalarını içeri aktar sayfasında Microsoft 365 uyumluluk merkezi. İçeri aktarma işi bittiğinde, işin durumu Tamamlandı olarak **ayarlanır**.
