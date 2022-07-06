---
title: PST dosyalarını içe aktarmak için ağ yüklemesini kullanma
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: "Yöneticiler için: Microsoft 365'te birden çok PST dosyasını kullanıcı posta kutularına toplu olarak aktarmak için ağ yüklemeyi kullanmayı öğrenin."
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0b24dc0ddc69c9af7516ee844af3899ff92fe4c4
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626039"
---
# <a name="use-network-upload-to-import-your-organizations-pst-files-to-microsoft-365"></a>Kuruluşunuzun PST dosyalarını Microsoft 365'e aktarmak için ağ yüklemeyi kullanma

> [!NOTE]
> Bu makale yöneticilere yöneliktir. PST dosyalarını kendi posta kutunuza aktarmaya mı çalışıyorsunuz? Bkz. [Outlook .pst dosyasından e-postayı, kişileri ve takvimi içeri aktarma](https://go.microsoft.com/fwlink/p/?LinkID=785075)
  
Birden çok PST dosyasını Microsoft 365 posta kutularına toplu olarak aktarmak için ağ yüklemesini kullanmak için gereken adım adım yönergeler aşağıdadır. PST dosyalarını Microsoft 365 posta kutularına toplu olarak aktarmak için ağ yükleme kullanma hakkında sık sorulan sorular için bkz. [PST dosyalarını içeri aktarmak için ağ yükleme kullanma hakkında SSS](./faqimporting-pst-files-to-office-365.yml#using-network-upload-to-import-pst-files).
  
[1. Adım: SAS URL'sini kopyalama ve AzCopy'yi indirme](#step-1-copy-the-sas-url-and-download-azcopy)

[2. Adım: PST dosyalarınızı Microsoft 365'e yükleme](#step-2-upload-your-pst-files-to-microsoft-365)

[(İsteğe bağlı) 3. Adım: Karşıya yüklenen PST dosyalarının listesini görüntüleme](#optional-step-3-view-a-list-of-the-pst-files-uploaded-to-microsoft-365)

[4. Adım: PST İçeri Aktarma eşleme dosyasını oluşturma](#step-4-create-the-pst-import-mapping-file)

[5. Adım: PST İçeri Aktarma işi oluşturma](#step-5-create-a-pst-import-job)

[6. Adım: Verileri filtreleme ve PST İçeri Aktarma işini başlatma](#step-6-filter-data-and-start-the-pst-import-job)

PST dosyalarını Microsoft 365 posta kutularına aktarmak için 1. Adımı yalnızca bir kez gerçekleştirmeniz gerekir. Bu adımları gerçekleştirdikten sonra, bir grup PST dosyasını karşıya yüklemek ve içeri aktarmak istediğinizde 2. Adımdan 6. Adıma kadar olan adımları izleyin.

## <a name="before-you-import-pst-files"></a>PST dosyalarını içeri aktarmadan önce
  
- Microsoft Purview uyumluluk portalı içeri aktarma işleri oluşturmak ve PST dosyalarını kullanıcı posta kutularına aktarmak için Exchange Online'da Posta Kutusu İçeri Aktarma rolüne atanmış olmanız gerekir. Varsayılan olarak, bu rol Exchange Online'daki hiçbir rol grubuna atanmaz. Posta Kutusu İçeri Aktarma Dışarı Aktarma rolünü Kuruluş Yönetimi rol grubuna ekleyebilirsiniz. Ya da bir rol grubu oluşturabilir, Posta Kutusu İçeri Aktarma Dışarı Aktarma rolünü atayabilir ve ardından kendinizi üye olarak ekleyebilirsiniz. Daha fazla bilgi için Rol [gruplarını yönetme](/Exchange/permissions-exo/role-groups) bölümündeki "Rol grubuna rol ekleme" veya "Rol grubu oluşturma" bölümlerine bakın.

    Posta Kutusu İçeri Aktarma Dışarı Aktarma rolüne ek olarak, Exchange Online'de Posta Alıcıları rolüne de atanmış olmanız gerekir. Varsayılan olarak, bu rol Exchange Online'deki Kuruluş Yönetimi ve Alıcı Yönetimi rol gruplarına atanır.

    > [!TIP]
    > Exchange Online'da PST dosyalarını içeri aktarmaya yönelik yeni bir rol grubu oluşturmayı göz önünde bulundurun. PST dosyalarını içeri aktarmak için gereken en düşük ayrıcalık düzeyi için, Posta Kutusu İçeri Aktarma Dışarı Aktarma ve Posta Alıcıları rollerini yeni rol grubuna atayın ve ardından üye ekleyin.
  
- PST dosyalarını Microsoft 365'e aktarmak için desteklenen tek yöntem, bu makalede açıklandığı gibi AzCopy aracını kullanmaktır. PST dosyalarını doğrudan Azure Depolama alanına yüklemek için Azure Depolama Gezgini kullanamazsınız.

- Büyük PST dosyaları PST içeri aktarma işleminin performansını etkileyebilir. Bu nedenle, 2. Adımda Azure Depolama konumuna yüklediğiniz her PST dosyasının 20 GB'tan büyük olmaması önerilir.

- Bu yordam, erişim anahtarı içeren bir URL'nin kopyasını kopyalayıp kaydetmeyi içerir. Bu bilgiler, PST dosyalarınızı karşıya yüklemek için 2. Adımda ve Microsoft 365'e yüklenen PST dosyalarının listesini görüntülemek istiyorsanız 3. Adımda kullanılacaktır. Parolaları veya güvenlikle ilgili diğer bilgileri koruyacağınız gibi bu URL'yi korumak için önlemler almayı unutmayın. Örneğin, parola korumalı bir Microsoft Word belgesine veya şifrelenmiş bir USB sürücüsüne kaydedebilirsiniz. Bu birleştirilmiş URL ve anahtar örneği için [Daha fazla bilgi](#more-information) bölümüne bakın.

- PST dosyalarını Microsoft 365'te etkin olmayan bir posta kutusuna aktarabilirsiniz. Bunu, PST İçeri Aktarma eşleme dosyasındaki parametresinde  `Mailbox` etkin olmayan posta kutusunun GUID'sini belirterek yaparsınız. Bilgi için bu makalenin **Yönergeler** sekmesindeki 4. Adıma bakın.

- Exchange karma dağıtımında, birincil posta kutusu şirket içinde olan bir kullanıcının PST dosyalarını bulut tabanlı arşiv posta kutusuna aktarabilirsiniz. Bunu, PST İçeri Aktarma eşleme dosyasında aşağıdakileri yaparak yaparsınız:

  - parametresinde kullanıcının şirket içi posta kutusunun e-posta  `Mailbox` adresini belirtin.

  - parametresinde `IsArchive` **TRUE** değerini belirtin.

    Daha fazla bilgi için bkz [. 4. Adım](#step-4-create-the-pst-import-mapping-file) .

- PST dosyaları içeri aktarıldıktan sonra, posta kutusunun bekletme ayarı süresiz olarak açılır. Bu, saklama saklamayı kapatana veya saklamayı kapatmak için bir tarih ayarlayana kadar posta kutusuna atanan bekletme ilkesinin işlenmeyeceği anlamına gelir. Bunu neden yapıyoruz? Posta kutusuna içeri aktarılan iletiler eskiyse, posta kutusu için yapılandırılan bekletme ayarlarına göre bekletme süreleri dolduğundan kalıcı olarak silinebilir (temizlenebilir). Posta kutusunun bekletmeye yerleştirilmesi, posta kutusu sahibine bu yeni içeri aktarılan iletileri yönetmesi için zaman verir veya posta kutusunun bekletme ayarlarını değiştirmeniz için size zaman verir. Bekletme saklamayı yönetme hakkında öneriler için bu makaledeki [Daha fazla bilgi](#more-information) bölümüne bakın.

- Varsayılan olarak, Bir Microsoft 365 posta kutusu tarafından alınabilecek ileti boyutu üst sınırı 35 MB'tır. Bunun nedeni, bir posta kutusunun  *MaxReceiveSize*  özelliğinin varsayılan değerinin 35 MB olarak ayarlanmasıdır. Ancak, Microsoft 365'te ileti alma boyutu üst sınırı 150 MB'tır. Bu nedenle, 35 MB'tan büyük bir öğe içeren bir PST dosyasını içeri aktarırsanız, Microsoft 365 İçeri Aktarma hizmeti hedef posta kutusunda  *MaxReceiveSize*  özelliğinin değerini otomatik olarak 150 MB olarak değiştiririz. Bu, 150 MB'a kadar olan iletilerin kullanıcı posta kutularına aktarılmasını sağlar.

    > [!TIP]
    > Bir posta kutusunun ileti alma boyutunu tanımlamak için şu komutu powershell Exchange Online de çalıştırabilirsiniz: `Get-Mailbox <user mailbox> | FL MaxReceiveSize`.

- PST İçeri Aktarma işlemine üst düzey genel bakış için bu [makalenin İçeri aktarma işleminin nasıl çalıştığı](#how-the-import-process-works) bölümüne bakın.

## <a name="step-1-copy-the-sas-url-and-download-azcopy"></a>1. Adım: SAS URL'sini kopyalama ve AzCopy'yi indirme

İlk adım, PST dosyalarını Microsoft 365'e yüklemek için 2. Adımda çalıştırdığınız AzCopy aracını indirmektir. Ayrıca kuruluşunuzun SAS URL'sini de kopyalarsınız. Bu URL, kuruluşunuz için Microsoft bulutunda Azure Depolama konumu için ağ URL'si ile Paylaşılan Erişim İmzası (SAS) anahtarının birleşimidir. Bu anahtar, PST dosyalarını bir Azure Depolama konumuna yüklemek için gerekli izinleri sağlar. SAS URL'sini korumak için önlem almayı unutmayın. Kuruluşunuza özgüdür ve 2. Adımda kullanılır.

> [!IMPORTANT]
> Bu makalede belgelenen ağ yükleme yöntemini ve komut söz dizimini kullanarak PST dosyalarını içeri aktarmak için, aşağıdaki yordamda 6b. adımda indirilebilen AzCopy sürümünü kullanmanız gerekir. Aynı AzCopy sürümünü [buradan](https://aka.ms/downloadazcopylatest) da indirebilirsiniz. AzCopy'nin farklı bir sürümünün kullanılması desteklenmez.
  
1. <https://compliance.microsoft.com> Adresine gidin ve kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. Uyumluluk portalının sol bölmesinde **Veri yaşam döngüsü yönetimi** \> **İçeri Aktar'a** tıklayın.

    > [!NOTE]
    > Uyumluluk portalında **İçeri Aktar** sayfasına erişmek için size uygun izinlerin atanması gerekir. Daha fazla bilgi için **Başlamadan önce** bölümüne bakın. 

3. **İçeri Aktar** sekmesinde Simge Ekle'ye tıklayın![.](../media/ITPro-EAC-AddIcon.gif) **Yeni içeri aktarma işi**.

    İçeri aktarma işi sihirbazı görüntülenir.

4. PST içeri aktarma işi için bir ad yazın ve **İleri'ye** tıklayın. Küçük harf, sayı, kısa çizgi ve alt çizgi kullanın. Büyük harfler kullanamaz veya ada boşluk ekleyemezsiniz.

5. **Verileri karşıya yüklemek veya göndermek istiyor musunuz?** sayfasında **Verilerinizi karşıya yükle'ye** ve ardından **İleri'ye** tıklayın.

    ![Ağ karşıya yükleme içeri aktarma işi oluşturmak için Verilerinizi karşıya yükleyin'e tıklayın.](../media/e59f9dc3-ccde-44ff-ac38-c4e39d76ae85.png)
  
6. **Verileri içeri aktar** sayfasında aşağıdaki iki işlemi yapın:

    ![SAS URL'sini kopyalayın ve Verileri içeri aktar sayfasında AzCopy aracını indirin.](../media/74411014-ec4b-4e25-9065-404c934cce17.png)
  
    1. 2. adımda **Ağ karşıya yükleme SAS URL'sini göster'e** tıklayın. SAS URL'si görüntülendikten sonra **Panoya kopyala'ya** tıklayın ve daha sonra erişebilmek için bunu yapıştırın ve bir dosyaya kaydedin.

    2. 3. adımda **Azure AzCopy'yi İndir'e** tıklayarak AzCopy aracını yerel bilgisayarınıza indirin. AzCopy'nin bu sürümü yalnızca yürütülebilir bir dosya olduğundan yüklenecek bir şey yoktur.

   > [!NOTE]
   > **Verileri içeri aktar** sayfasını açık bırakabilirsiniz (SAS URL'sini yeniden kopyalamanız gerekebilir) veya kapatmak için **İptal'e** tıklayabilirsiniz.

## <a name="step-2-upload-your-pst-files-to-microsoft-365"></a>2. Adım: PST dosyalarınızı Microsoft 365'e yükleme

Artık PST dosyalarını Microsoft 365'e yüklemek için AzCopy aracını kullanmaya hazırsınız. Bu araç PST dosyalarını Microsoft bulutunda Microsoft tarafından sağlanan bir Azure Depolama konumuna yükler ve depolar. Daha önce açıklandığı gibi PST dosyalarınızı karşıya yüklediğiniz Azure Depolama konumu, kuruluşunuzun bulunduğu bölgesel Microsoft veri merkezinde bulunur. Bu adımı tamamlamak için PST dosyalarının kuruluşunuzdaki bir dosya paylaşımında veya dosya sunucusunda ya da kuruluşunuz tarafından yönetilen bir Azure Depolama konumunda bulunması gerekir. PST depolama konumu, bu yordamdaki kaynak konum olarak bilinir. AzCopy aracını her çalıştırdığınızda farklı bir kaynak konumu belirtebilirsiniz.

> [!NOTE]
> Daha önce belirtildiği gibi, Azure Depolama konumuna yüklediğiniz her PST dosyası 20 GB'tan büyük olmamalıdır. 20 GB'tan büyük PST dosyaları, 6. Adımda başladığınız PST içeri aktarma işleminin performansını etkileyebilir. Ayrıca, her PST dosyasının benzersiz bir adı olmalıdır.

1. Yerel bilgisayarınızda bir Komut İstemi açın.

2. 1. Adımda azcopy.exe dosyasını indirdiğiniz dizine gidin.

3. PST dosyalarını Microsoft 365'e yüklemek için aşağıdaki komutu çalıştırın.

    ```powershell
    azcopy.exe copy "<Source location of PST files>" "<SAS URL>"
    ```

    > [!IMPORTANT]
    > Önceki komutta kaynak konum olarak bir dizin veya Azure Depolama konumu belirtebilirsiniz; tek bir PST dosyası belirtemezsiniz. Kaynak konumdaki tüm PST dosyaları karşıya yüklenir.

    Aşağıdaki tabloda azcopy.exe alanları ve bunların gerekli değerleri açıklanmaktadır. Önceki adımda aldığınız bilgiler bu alanların değerlerinde kullanılır.

    | Alan | Açıklama |
    |:-----|:-----|
    | Kaynak |İlk alan, kuruluşunuzda Microsoft 365'e yüklenecek PST dosyalarını içeren kaynak dizini belirtir. Alternatif olarak, karşıya yüklenecek PST dosyalarının kaynak konumu olarak bir Azure Depolama konumu belirtebilirsiniz. <br/> Bu alanın değerini çift tırnak işareti (" ") ile çevrelemeye özen gösterin.  <br/> <br/>**Örnekler**: <br/>`"\\FILESERVER01\PSTs"` <br/> Veya  <br/>`"https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx"`|  
    | Hedef |1. Adımda aldığınız SAS URL'sini belirtir.  <br/> Bu parametrenin değerini çift tırnak işareti (" ") ile çevrelemeye özen gösterin.<br/><br/>**Not:** Sas URL'sini bir betikte veya toplu iş dosyasında kullanıyorsanız, kaçılması gereken belirli karakterlere dikkat edin. Örneğin, olarak değiştirmeniz `%` `%%` ve olarak değiştirmeniz `&` gerekir `^&`.<br/><br/>**İpucu:** (İsteğe bağlı) PST dosyalarının yüklendiği Azure Depolama konumunda bir alt klasör belirtebilirsiniz. Bunu, SAS URL'sine bir alt klasör konumu ("ingestiondata" sonrasında) ekleyerek yaparsınız. İlk örnekte alt klasör belirtilmez. Bu, PST dosyalarının Azure Depolama konumunun köküne ( *ingestiondata* adlı) yüklendiği anlamına gelir. İkinci örnek, PST dosyalarını Azure Depolama konumunun kökündeki bir alt klasöre (  *PSTFiles* adlı) yükler.  <br/><br/>**Örnekler**: <br/> `"https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"` <br/> Veya  <br/>  `"https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata/PSTFiles?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"` <br/> |
    | `--recursive` |Bu isteğe bağlı bayrak özyinelemeli modu belirtir, böylece AzCopy aracı kaynak alan tarafından belirtilen kaynak dizinin alt klasörlerinde bulunan PST dosyalarını kopyalar. Bu bayrağın varsayılan değeri şeklindedir `true`. <br/>**Not:** Bu bayrağı eklerseniz, alt klasörlerdeki PST dosyaları karşıya yüklendikten sonra Azure Depolama konumunda farklı bir dosya yolu adına sahip olur. 4. Adımda oluşturduğunuz CSV dosyasında tam dosya yolu adını belirtmeniz gerekir.|
    | `--s2s-preserve-access-tier` | Bu isteğe bağlı bayrak yalnızca kaynak konum, erişim katmanlarını destekleyen genel amaçlı v2 Azure Depolama konumu olduğunda gereklidir. PST İçeri Aktarma senaryosunda, PST dosyalarını Azure Depolama hesabınızdan Microsoft tarafından sağlanan Azure Depolama konumuna kopyalarken erişim katmanını korumanız gerekmez. Bu durumda, bu bayrağı ekleyebilir ve değerini `false`kullanabilirsiniz. Erişim katmanlarını desteklemeyen klasik bir Azure Depolama hesabından PST dosyalarını kopyalarken bu bayrağı kullanmanız gerekmez.|
   |||

**azcopy.exe kopyalama** komutu hakkında daha fazla bilgi için bkz. [azcopy copy](/azure/storage/common/storage-ref-azcopy-copy).

Aşağıda, her parametre için gerçek değerleri kullanan AzCopy aracının söz diziminin örnekleri verilmiştir.

### <a name="example-1"></a>Örnek 1

Bu, dosya sunucusunda veya yerel bilgisayarda bulunan bir kaynak dizine örnektir.

```powershell
azcopy.exe copy "\\FILESERVER1\PSTs" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"
```

### <a name="example-2"></a>Örnek 2

Bu, alt dizinleri olan klasik bir Azure Depolama hesabında bulunan bir kaynak dizine örnektir.

```powershell
azcopy.exe copy "https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D" --recursive
```

### <a name="example-3"></a>Örnek 3

Bu, genel amaçlı v2 Azure Depolama hesabında bulunan bir kaynak dizine örnektir. PST dosyaları karşıya yüklendiğinde erişim katmanları korunmaz.

```powershell
azcopy.exe copy "https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D" --s2s-preserve-access-tier=false
```

Komutu çalıştırdıktan sonra, PST dosyalarını karşıya yükleme işleminin ilerleme durumunu gösteren durum iletileri görüntülenir. Son durum iletisi, başarıyla karşıya yüklenen dosyaların toplam sayısını gösterir.

> [!TIP]
> **azcopy.exe kopyalama** komutunu başarıyla çalıştırdıktan ve tüm parametrelerin doğru olduğunu doğruladıktan sonra, komut satırı söz diziminin bir kopyasını 1. Adımda elde ettiğiniz bilgileri kopyaladığınız aynı (güvenli) dosyaya kaydedin. Ardından, PST dosyalarını Microsoft 365'e yüklemek için AzCopy aracını her çalıştırmak istediğinizde bu komutu kopyalayıp komut istemine yapıştırabilirsiniz. Değiştirmeniz gerekebilecek tek değer kaynak alanıdır. Bu, PST dosyalarının bulunduğu kaynak dizine bağlıdır.

## <a name="optional-step-3-view-a-list-of-the-pst-files-uploaded-to-microsoft-365"></a>(İsteğe bağlı) 3. Adım: Microsoft 365'e yüklenen PST dosyalarının listesini görüntüleme

İsteğe bağlı bir adım olarak, Azure blob'a yüklediğiniz PST dosyalarının listesini görüntülemek için Microsoft Azure Depolama Gezgini (ücretsiz, açık kaynak bir araçtır) yükleyip kullanabilirsiniz. Bunu yapmak için iki iyi neden vardır:
  
- Kuruluşunuzdaki paylaşılan klasörden veya dosya sunucusundan PST dosyalarının Azure blob'a başarıyla yüklendiğini doğrulayın.

- Azure blob'a yüklenen her PST dosyası için dosya adını (ve varsa alt klasör yol adını) doğrulayın. Bu, bir sonraki adımda PST eşleme dosyasını oluştururken yararlıdır çünkü her PST dosyası için hem klasör yolu adını hem de dosya adını belirtmeniz gerekir. Bu adların doğrulanması PST eşleme dosyanızdaki olası hataları azaltmaya yardımcı olabilir.

tek başına Azure Depolama Gezgini uygulaması genel kullanıma sunulmuştur. Aşağıdaki yordamdaki bağlantıyı kullanarak en son sürümü indirebilirsiniz.
  
> [!IMPORTANT]
> PST dosyalarını karşıya yüklemek veya değiştirmek için Azure Depolama Gezgini kullanamazsınız. PST dosyalarını içeri aktarmak için desteklenen tek yöntem AzCopy kullanmaktır. Ayrıca, Azure blob'a yüklediğiniz PST dosyalarını silemezsiniz. BIR PST dosyasını silmeye çalışırsanız, gerekli izinlere sahip olmadığınız konusunda bir hata alırsınız. Tüm PST dosyalarının Azure depolama alanınızdan otomatik olarak silindiğini unutmayın. Devam eden içeri aktarma işi yoksa, en son içeri aktarma işi oluşturulduktan 30 gün sonra **ingestiondata** kapsayıcısında yer alan tüm PST dosyaları silinir.
  
Azure Depolama Gezgini yüklemek ve Azure Depolama alanınıza bağlanmak için:
  
1. [Microsoft Azure Depolama Gezgini aracını](https://go.microsoft.com/fwlink/p/?LinkId=544842) indirin ve yükleyin.

2. Microsoft Azure Depolama Gezgini başlatın.

3. **Azure Depolama'ya Bağlan** iletişim kutusundaki **Kaynak Seç** sayfasında **Blob kapsayıcısı'na** tıklayın.
  
4. **Kimlik Doğrulama Yöntemini Seç** sayfasında **Paylaşılan erişim imzası (SAS)** seçeneğini belirleyin ve **ardından İleri'ye** tıklayın.

5. **Bağlantı Bilgilerini Girin** sayfasında, 1. Adımda aldığınız SAS URL'sini **Blob kapsayıcıSı SAS URL'si** altındaki kutuya yapıştırın ve ardından **İleri'ye** tıklayın. SAS URL'sini yapıştırdıktan sonra **Görünen ad** altındaki kutu, **alma verileriyle** otomatik olarak doldurulur.

6. **Özet** sayfasında, bağlantı bilgilerini gözden geçirebilir ve **bağlan'a** tıklayabilirsiniz.

    **ingestiondata** kapsayıcısı açılır. 2. Adımda karşıya yüklediğiniz PST dosyalarını içerir. **ingestiondata** kapsayıcısı **Depolama Hesapları** \> **(Bağlı Kapsayıcılar)** \> **Blob Kapsayıcıları** altında bulunur. 
  
7. Microsoft Azure Depolama Gezgini kullanmayı bitirdiğinizde, **alma verileri'ne** sağ tıklayın ve ardından Azure Depolama alanınızın bağlantısını kesmek için **Ayır'a** tıklayın. Aksi takdirde, bir sonraki ekleme denemesinde bir hata alırsınız.
  
## <a name="step-4-create-the-pst-import-mapping-file"></a>4. Adım: PST İçeri Aktarma eşleme dosyasını oluşturma

PST dosyaları kuruluşunuz için Azure Depolama konumuna yüklendikten sonra, sonraki adım PST dosyalarının hangi kullanıcı posta kutularına aktarılacağını belirten bir virgülle ayrılmış değer (CSV) dosyası oluşturmaktır. Bir PST İçeri Aktarma işi oluşturduğunuzda sonraki adımda bu CSV dosyasını göndereceksiniz.
  
1. [PST İçeri Aktarma eşleme dosyasının bir kopyasını indirin](https://go.microsoft.com/fwlink/p/?LinkId=544717).

2. CSV dosyasını yerel bilgisayarınıza açın veya kaydedin. Aşağıdaki örnekte tamamlanmış bir PST İçeri Aktarma eşleme dosyası (Not Defteri'nde açılır) gösterilmektedir. CSV dosyasını düzenlemek için Microsoft Excel'i kullanmak çok daha kolaydır.

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

    CSV dosyasının ilk satırı veya üst bilgi satırı, PST İçeri Aktarma hizmeti tarafından PST dosyalarını kullanıcı posta kutularına aktarmak için kullanılacak parametreleri listeler. Her parametre adı virgülle ayrılır. Üst bilgi satırının altındaki her satır, pst dosyasını belirli bir posta kutusuna aktarmaya yönelik parametre değerlerini temsil eder. Kullanıcı posta kutusuna aktarmak istediğiniz her PST dosyası için bir satıra ihtiyacınız vardır. CSV eşleme dosyasında en fazla 500 satır olabilir. 500'den fazla PST dosyasını içeri aktarmak için, 5. Adımda birden çok eşleme dosyası oluşturmanız ve birden çok içeri aktarma işi oluşturmanız gerekir.

    > [!NOTE]
    > SharePoint parametreleri de dahil olmak üzere üst bilgi satırında hiçbir şeyi değiştirmeyin; PST İçeri Aktarma işlemi sırasında yoksayılırlar. Ayrıca, eşleme dosyasındaki yer tutucu verileri gerçek verilerinizle değiştirerek değiştirmeyi unutmayın.

3. CSV dosyasını gerekli bilgilerle doldurmak için aşağıdaki tabloda yer alan bilgileri kullanın.

    | Parametre | Açıklama | Örnek |
    |:-----|:-----|:-----|
    | `Workload` <br/> |Verilerin içeri aktarılacağı hizmeti belirtir. PST dosyalarını kullanıcı posta kutularına aktarmak için kullanın  `Exchange`.  <br/> | `Exchange` <br/> |
    | `FilePath` <br/> |2. Adımda PST dosyalarını karşıya yüklediğiniz Azure Depolama konumundaki klasör konumunu belirtir.  <br/> 2. Adım'daki parametrede SAS URL'sine  `/Dest:` isteğe bağlı bir alt klasör adı eklemediyseniz, BU parametreyi CSV dosyasında boş bırakın. Bir alt klasör adı eklediyseniz, bunu bu parametrede belirtin (ikinci örne bakın). Bu parametrenin değeri büyük/küçük harfe duyarlıdır.  <br/> Her iki durumda  *da parametresinin*  değerine "ingestiondata" eklemeyin  `FilePath` .  <br/><br/> **Önemli:** Dosya yolu adının durumu, 2. Adım'daki hedef alana SAS URL'sine isteğe bağlı bir alt klasör adı eklediyseniz kullandığınız durumla aynı olmalıdır. Örneğin, 2. Adımda alt klasör adı için kullandıysanız `PSTFiles` ve csv dosyasındaki parametresinde `FilePath` kullandıysanız`pstfiles`, PST dosyasının içeri aktarma işlemi başarısız olur. Her iki durumda da aynı durumu kullandığınızdan emin olun.  <br/> |(boş bırakın)  <br/> Veya  <br/>  `PSTFiles` <br/> |
    | `Name` <br/> |Kullanıcı posta kutusuna aktarılacak PST dosyasının adını belirtir. Bu parametrenin değeri büyük/küçük harfe duyarlıdır. İçeri aktarma işinin eşleme dosyasındaki her PST dosyasının dosya adı benzersiz olmalıdır. <br/> <br/>**Önemli:** CSV dosyasındaki PST dosya adının durumu, 2. Adımda Azure Depolama konumuna yüklenen PST dosyasıyla aynı olmalıdır. Örneğin, CSV dosyasındaki parametresinde `Name` kullanıyorsanız `annb.pst` ancak asıl PST dosyasının adı ise`AnnB.pst`, o PST dosyasının içeri aktarma işlemi başarısız olur. CSV dosyasındaki PST adının gerçek PST dosyasıyla aynı durumu kullandığından emin olun.  <br/> | `annb.pst` <br/> |
    | `Mailbox` <br/> |PST dosyasının içeri aktarılacağı posta kutusunun e-posta adresini belirtir. PST İçeri Aktarma Hizmeti, PST dosyalarının ortak klasörlere aktarılmasını desteklemediğinden ortak klasör belirtemezsiniz.  <br/> Pst dosyasını etkin olmayan bir posta kutusuna aktarmak için bu parametre için posta kutusu GUID'sini belirtmeniz gerekir. Bu GUID'yi almak için Exchange Online aşağıdaki PowerShell komutunu çalıştırın:`Get-Mailbox <identity of inactive mailbox> -InactiveMailboxOnly | FL Guid` <br/> <br/>**Not:** Bazen aynı e-posta adresine sahip birden çok posta kutunuz olabilir; burada bir posta kutusu etkin bir posta kutusu, diğer posta kutusu geçici olarak silinmiş (veya etkin olmayan) durumda olabilir. Bu durumlarda, PST dosyasını içeri aktarılacak posta kutusunu benzersiz olarak tanımlamak için posta kutusu GUID'sini belirtmeniz gerekir. Etkin posta kutuları için bu GUID'yi almak için aşağıdaki PowerShell komutunu çalıştırın:  `Get-Mailbox <identity of active mailbox> | FL Guid`. Geçici olarak silinen (veya etkin olmayan) posta kutularının GUID'sini almak için bu komutu  `Get-Mailbox <identity of soft-deleted or inactive mailbox> -SoftDeletedMailbox | FL Guid`çalıştırın.  <br/> | `annb@contoso.onmicrosoft.com` <br/> Veya  <br/>  `2d7a87fe-d6a2-40cc-8aff-1ebea80d4ae7` <br/> |
    | `IsArchive` <br/> | PST dosyasının kullanıcının arşiv posta kutusuna içeri aktarılıp aktarılmayacağını belirtir. İki seçenek vardır:  <br/><br/>**FALSE:** PST dosyasını kullanıcının birincil posta kutusuna aktarır.  <br/> **TRUE:** PST dosyasını kullanıcının arşiv posta kutusuna aktarır. Bu, [kullanıcının arşiv posta kutusunun etkinleştirildiğini](enable-archive-mailboxes.md) varsayar. <br/><br/>Bu parametreyi olarak  `TRUE` ayarlarsanız ve kullanıcının arşiv posta kutusu etkinleştirilmezse, söz konusu kullanıcının içeri aktarma işlemi başarısız olur. Bir kullanıcı için içeri aktarma işlemi başarısız olursa (arşivi etkinleştirilmediğinden ve bu özellik olarak ayarlandığından  `TRUE`), içeri aktarma işindeki diğer kullanıcılar etkilenmez.  <br/>  Bu parametreyi boş bırakırsanız, PST dosyası kullanıcının birincil posta kutusuna aktarılır.  <br/> <br/>**Not:** Pst dosyasını, birincil posta kutusu şirket içi olan bir kullanıcının bulut tabanlı arşiv posta kutusuna aktarmak için, bu parametre için belirtin  `TRUE` ve kullanıcının şirket içi posta kutusunun e-posta adresini parametre için  `Mailbox` belirtin.  <br/> | `FALSE` <br/> Veya  <br/>  `TRUE` <br/> |
    | `TargetRootFolder` <br/> | PST dosyasının içeri aktarıldığını posta kutusu klasörünü belirtir.  <br/> <br/> Bu parametreyi boş bırakırsanız, PST dosyası posta kutusunun kök düzeyinde (Gelen Kutusu klasörü ve diğer varsayılan posta kutusu klasörleriyle aynı düzeyde) **İçeri Aktarıldı** adlı yeni bir klasöre aktarılır.  <br/> <br/> belirtirseniz  `/`, PST dosyasındaki klasörler ve öğeler hedef posta kutusunda veya arşivde klasör yapısının en üstüne aktarılır. Hedef posta kutusunda bir klasör varsa (örneğin, Gelen Kutusu, Gönderilmiş Öğeler ve Silinmiş Öğeler gibi varsayılan klasörler), PST'deki bu klasördeki öğeler hedef posta kutusunda var olan klasörle birleştirilir. Örneğin, PST dosyası bir Gelen Kutusu klasörü içeriyorsa, bu klasördeki öğeler hedef posta kutusundaki Gelen Kutusu klasörüne aktarılır. Yeni klasörler, hedef posta kutusunun klasör yapısında yoksa oluşturulur.  <br/><br/>  belirtirseniz  `/<foldername>`, PST dosyasındaki öğeler ve klasörler adlı  *\<foldername\>*  bir klasöre aktarılır. Örneğin, kullanırsanız  `/ImportedPst`, öğeler **ImportedPst** adlı bir klasöre aktarılır. Bu klasör, kullanıcının posta kutusunda Gelen Kutusu klasörüyle aynı düzeyde bulunur.  <br/><br/> **Ipucu:** PST dosyalarını içeri aktarmak için en iyi klasör konumunu belirleyebilmek için bu parametreyle deneme yapmak için birkaç test toplu işlemi çalıştırmayı göz önünde bulundurun.  <br/> |(boş bırakın)  <br/> Veya  <br/>  `/` <br/> Veya  <br/>  `/ImportedPst` <br/> |
    | `ContentCodePage` <br/> |Bu isteğe bağlı parametre, PST dosyalarını ANSI dosya biçiminde içeri aktarmak için kullanılacak kod sayfası için sayısal bir değer belirtir. Bu diller genellikle karakter kodlaması için çift bayt karakter kümesi (DBCS) kullandığından, bu parametre Çince, Japonca ve Korece (CJK) kuruluşlarından PST dosyalarını içeri aktarmak için kullanılır. Bu parametre, posta kutusu klasör adları için DBCS kullanan diller için PST dosyalarını içeri aktarmak için kullanılmazsa, klasör adları genellikle içeri aktarıldıktan sonra bozuk olur.  <br/><br/> Bu parametre için kullanılacak desteklenen değerlerin listesi için bkz. [Kod Sayfası Tanımlayıcıları](/windows/win32/intl/code-page-identifiers).  <br/> <br/>**Not:** Daha önce belirtildiği gibi, bu isteğe bağlı bir parametredir ve CSV dosyasına eklemeniz gerekmez. İsterseniz, bu değeri dahil edebilir ve değeri bir veya daha fazla satır için boş bırakabilirsiniz.  <br/> |(boş bırakın)  <br/> Veya  <br/>  `932` (ANSI/OEM Japonca için kod sayfası tanımlayıcısı)  <br/> |
    | `SPFileContainer` <br/> |PST İçeri Aktarma için bu parametreyi boş bırakın.  <br/> |Geçerli değil  <br/> |
    | `SPManifestContainer` <br/> |PST İçeri Aktarma için bu parametreyi boş bırakın.  <br/> |Geçerli değil  <br/> |
    | `SPSiteUrl` <br/> |PST İçeri Aktarma için bu parametreyi boş bırakın.  <br/> |Geçerli değil  <br/> |

## <a name="step-5-create-a-pst-import-job"></a>5. Adım: PST İçeri Aktarma işi oluşturma

Sonraki adım, Microsoft 365'teki İçeri Aktarma hizmetinde PST İçeri Aktarma işini oluşturmaktır. Daha önce açıklandığı gibi, 4. Adımda oluşturduğunuz PST İçeri Aktarma eşleme dosyasını gönderirsiniz. İşi oluşturduktan sonra, Microsoft 365 PST dosyalarındaki verileri analiz eder ve ardından pst içeri aktarma eşleme dosyasında belirtilen posta kutularına aktarılan verileri filtreleme fırsatı verir (bkz. [6. Adım](#step-6-filter-data-and-start-the-pst-import-job)).
  
1. <https://compliance.microsoft.com> Adresine gidin ve kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. Uyumluluk portalının sol bölmesinde **veri yaşam döngüsü yönetimi > İçeri Aktar'a** tıklayın.

3. **İçeri Aktar** sekmesinde Simge Ekle'ye tıklayın![.](../media/ITPro-EAC-AddIcon.gif) **Yeni içeri aktarma işi**.

   > [!NOTE]
   > İçeri aktarma işi oluşturmak için uyumluluk portalındaki **İçeri Aktar** sayfasına erişmek için size uygun izinlerin atanması gerekir. Daha fazla bilgi için **PST dosyalarını içeri aktarmadan önce** bölümüne bakın. 

4. PST içeri aktarma işi için bir ad yazın ve **İleri'ye** tıklayın. Küçük harf, sayı, kısa çizgi ve alt çizgi kullanın. Büyük harfler kullanamaz veya ada boşluk ekleyemezsiniz.

5. **Verileri karşıya yüklemek veya göndermek istiyor musunuz?** sayfasında **Verilerinizi karşıya yükle'ye** ve ardından **İleri'ye** tıklayın.
  
6. **Verileri içeri aktar** sayfasındaki 4. adımda **Dosyalarımı karşıya yüklemeyi bitirdim** ve **eşleme dosyasına erişimim var onay kutularına** tıklayın ve ardından **İleri'ye** tıklayın.

    ![4. adımdaki iki onay kutusuna tıklayın.](../media/9f2427e8-3af2-4e27-95e6-a9f08430d3d8.png)
  
7. **Eşleme dosyasını seçin** sayfasında **Eşleme dosyasını seç'e** tıklayarak 4. Adımda oluşturduğunuz CSV eşleme dosyasını gönderin.

    ![İçeri aktarma işi için oluşturduğunuz CSV dosyasını göndermek için Eşleme dosyasını seç'e tıklayın.](../media/d30b1d73-80bb-491e-a642-a21673d06889.png)
  
8. CSV dosyasının adı **Eşleme dosyası adı** altında gösterildikten sonra, CSV dosyanızda hata olup olmadığını denetlemek için **Doğrula'ya** tıklayın.

    ![CSV dosyasının hatalarını denetlemek için Doğrula'ya tıklayın.](../media/4680999d-5538-4059-b878-2736a5445037.png)
  
    PST İçeri Aktarma işi oluşturmak için CSV dosyasının başarıyla doğrulanması gerekir. Dosya adı başarıyla doğrulandıktan sonra yeşil olarak değiştirilir. Doğrulama başarısız olursa **Günlüğü görüntüle** bağlantısına tıklayın. Dosyadaki her satır için başarısız olan bir hata iletisiyle birlikte bir doğrulama hata raporu açılır.

   > [!NOTE]
   > Daha önce açıklandığı gibi, eşleme dosyasının en fazla 500 satırı olabilir. Eşleme dosyası 500'den fazla satır içeriyorsa doğrulama başarısız olur. 500'den fazla PST dosyasını içeri aktarmak için birden çok eşleme dosyası ve birden çok içeri aktarma işi oluşturmanız gerekir.

9. Eşleme dosyası başarıyla doğrulandıktan sonra hüküm ve koşullar belgesini okuyun ve onay kutusuna tıklayın.

10. İşi göndermek için **Kaydet'e** tıklayın ve sonra iş başarıyla oluşturulduktan sonra **Kapat'a** tıklayın.

    Durum açılır sayfası görüntülenir ve **durum Çözümleme devam ediyor** ve yeni içeri aktarma işi **PST dosyalarını içeri aktar** sayfasındaki listede görüntülenir.

11. **Yenile Yenile** ![simgesine tıklayın.](../media/O365-MDM-Policy-RefreshIcon.gif) öğesini seçerek **Durum** sütununda görüntülenen durum bilgilerini güncelleştirin. Analiz tamamlandığında ve veriler içeri aktarılmaya hazır olduğunda, durum **Çözümleme tamamlandı** olarak değiştirilir.

    İçeri aktarma işini tıklayarak durum açılır listesini görüntüleyebilirsiniz. Bu sayfa, eşleme dosyasında listelenen her PST dosyasının durumu gibi içeri aktarma işi hakkında daha ayrıntılı bilgiler içerir.

## <a name="step-6-filter-data-and-start-the-pst-import-job"></a>6. Adım: Verileri filtreleme ve PST İçeri Aktarma işini başlatma

5. Adımda içeri aktarma işini oluşturduktan sonra, Microsoft 365 öğelerin yaşını ve PST dosyalarına dahil edilen farklı ileti türlerini belirleyerek PST dosyalarındaki verileri (güvenli ve güvenli bir şekilde) analiz eder. Analiz tamamlandığında ve veriler içeri aktarmaya hazır olduğunda, PST dosyalarında yer alan tüm verileri içeri aktarma seçeneğiniz olur veya hangi verilerin içeri aktarılacağını denetleye filtreler ayarlayarak içeri aktarılan verileri kırpabilirsiniz.
  
1. Uyumluluk portalındaki **İçeri Aktar** sekmesinde, 5. Adımda oluşturduğunuz içeri aktarma işlerini seçin ve ardından **Microsoft 365'e aktar'a** tıklayın.
  
   **Verilerinizi filtreleyin** sayfası görüntülenir. Verilerin yaşıyla ilgili bilgiler de dahil olmak üzere Microsoft 365 tarafından PST dosyalarında gerçekleştirilen analizden kaynaklanan veri içgörülerini içerir. Bu noktada, içeri aktarılacak verileri filtreleme veya tüm verileri olduğu gibi içeri aktarma seçeneğiniz vardır. 

    ![PST dosyalarındaki verileri kırpabilir veya tümünü içeri aktarabilirsiniz.](../media/287fc030-99e9-417b-ace7-f64617ea5d4e.png)
  
2. Şunlardan birini yapın:

   1. İçeri aktardığınız verileri kırpmak için **Evet, içeri aktarmadan önce filtrelemek istiyorum'a** tıklayın.

      PST dosyalarındaki verileri filtreleme ve içeri aktarma işini başlatma hakkında ayrıntılı adım adım yönergeler için bkz. [PST dosyalarını Microsoft 365'e aktarırken verileri filtreleme](filter-data-when-importing-pst-files.md).

      Veya

   2. PST dosyalarındaki tüm verileri içeri aktarmak için **Hayır, her şeyi içeri aktarmak istiyorum'a** tıklayın ve **İleri'ye** tıklayın.

3. Tüm verileri içeri aktarmayı seçtiyseniz, içeri aktarma işini başlatmak için **Verileri içeri aktar'a** tıklayın. 

   İçeri aktarma işinin durumu **PST dosyalarını içeri aktar** sayfasında görüntülenir. Yenile simgesine tıklayın ![.](../media/O365-MDM-Policy-RefreshIcon.gif) **Durum** sütununda görüntülenen durum bilgilerini güncelleştirmek için **yenileyin**. İçeri aktarılan her PST dosyasıyla ilgili durum bilgilerini görüntüleyen durum açılır listesini görüntülemek için içeri aktarma işine tıklayın.

## <a name="more-information"></a>Daha fazla bilgi

- PST dosyalarını neden Microsoft 365'e aktarabilirsiniz?

  - Kuruluşunuzun arşiv mesajlaşma verilerini Microsoft 365'e aktarmanın iyi bir yoludur.

  - Veriler bulutta depolandığından tüm cihazlardan kullanıcıya sağlanır.

  - İçeri aktardığınız PST dosyalarındaki verilere Microsoft Purview özelliklerini uygulamanıza izin vererek kuruluşunuzun uyumluluk gereksinimlerini karşılamaya yardımcı olur. Buna şunlar dahildir:

  - Kullanıcılara içeri aktardığınız verileri [depolamaları](enable-archive-mailboxes.md) için ek posta kutusu depolama alanı sağlamak için arşiv posta kutularını etkinleştirme ve [arşivlemeyi otomatik olarak genişletme](enable-autoexpanding-archiving.md) .

  - İçeri aktardığınız verileri korumak için posta kutularını [Dava Tutma'ya](./create-a-litigation-hold.md) yerleştirme.

  - İçeri aktardığınız verileri aramak için Microsoft [eBulma araçlarını](search-for-content.md) kullanma.

  - microsoft [365 saklama ilkelerini](retention.md) kullanarak içeri aktardığınız verilerin ne kadar süreyle tutulacağını ve saklama süresi dolduktan sonra hangi eylemlerin gerçekleştirileceğini denetleyin.

  - İçeri aktardığınız verileri etkileyen posta kutusuyla ilgili olaylar için [denetim günlüğünde](search-the-audit-log-in-security-and-compliance.md) arama yapma.

  - Verileri uyumluluk amacıyla arşivleme amacıyla [etkin olmayan posta kutularına](inactive-mailboxes-in-office-365.md) aktarma. 

  - Hassas verilerin kuruluşunuzun dışına sızmasını önlemek için [veri kaybı önleme ilkelerini](dlp-learn-about-dlp.md) kullanma.

- Daha önce açıklandığı gibi, PST dosyaları bir posta kutusuna aktarıldıktan sonra Microsoft 365 İçeri Aktarma hizmeti saklama ayarını (süresiz olarak) açar. Bu, posta kutusuna atanan bekletme ilkesinin işlenmemesi için  *RetentionHoldEnabled*  özelliğinin  **True** olarak ayarlandığı anlamına gelir. Bu, bir silme veya arşiv ilkesinin eski iletileri silmesini veya arşivlemesini engelleyerek posta kutusu sahibine yeni içeri aktarılan iletileri yönetmesi için zaman verir. Bu bekletme saklamayı yönetmek için uygulayabileceğiniz bazı adımlar şunlardır:

  - Belirli bir süre sonra **Set-Mailbox -RetentionHoldEnabled $false** komutunu çalıştırarak bekletmeyi kapatabilirsiniz. Yönergeler için bkz [. Saklama bekletmeye posta kutusu yerleştirme](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

  - Bekletme saklamayı, gelecekte bir tarihte kapatılmış olacak şekilde yapılandırabilirsiniz. Bunu yapmak için **Set-Mailbox -EndDateForRetentionHold *date*** komutunu çalıştırın. Örneğin, bugünün tarihinin 1 Haziran 2016 olduğunu ve bekletme saklamanın 30 gün içinde kapatılmasını istediğinizi varsayarsak şu komutu çalıştırırsınız:  **Set-Mailbox -EndDateForRetentionHold 7/1/2016**. Bu senaryoda  **RetentionHoldEnabled**  özelliğini  *True* olarak bırakırsınız. Daha fazla bilgi için bkz. [Set-Mailbox](/powershell/module/exchange/set-mailbox).

  - posta kutusuna atanan bekletme ilkesinin ayarlarını değiştirebilirsiniz, böylece içeri aktarılan eski öğeler hemen silinmez veya kullanıcının arşiv posta kutusuna taşınmaz. Örneğin, posta kutusuna atanan bir silme veya arşiv ilkesi için saklama süresini uzatabilirsiniz. Bu senaryoda, bekletme ilkesinin ayarlarını değiştirdikten sonra posta kutusunda bekletmeyi kapatabilirsiniz. Daha fazla bilgi için bkz. [Kuruluşunuzdaki posta kutuları için arşiv ve silme ilkesi ayarlama](set-up-an-archive-and-deletion-policy-for-mailboxes.md).

### <a name="how-the-import-process-works"></a>İçeri aktarma işlemi nasıl çalışır?
  
PST dosyalarını kullanıcı posta kutularına toplu olarak aktarmak için ağ yükleme seçeneğini ve Microsoft 365 İçeri Aktarma hizmetini kullanabilirsiniz. Ağ yükleme, PST dosyalarını Microsoft bulutunda geçici bir depolama alanı olarak karşıya yüklediğiniz anlamına gelir. Ardından Microsoft 365 İçeri Aktarma hizmeti, PST dosyalarını depolama alanından hedef kullanıcı posta kutularına kopyalar.
  
Aşağıda, PST dosyalarını Microsoft 365'teki posta kutularına aktarmaya yönelik ağ karşıya yükleme işleminin çizimi ve açıklaması yer alır.
  
![PST dosyalarını Microsoft 365'e aktarmak için ağ karşıya yükleme işleminin iş akışı.](../media/9e05a19e-1e7a-4f1f-82df-9118f51588c4.png)
  
1. **PST içeri aktarma aracını ve anahtarını özel Azure Depolama konumuna indirin:** İlk adım, AzCopy komut satırı aracını ve PST dosyalarını Microsoft bulutunda bir Azure Depolama konumuna yüklemek için kullanılan bir erişim anahtarını indirmektir. Bunları uyumluluk portalındaki **İçeri Aktar** sayfasından alırsınız. Anahtar (güvenli erişim imzası (SAS) anahtarı olarak adlandırılır, PST dosyalarını özel ve güvenli bir Azure Depolama konumuna yüklemek için gerekli izinleri sağlar. Bu erişim anahtarı kuruluşunuza özgüdür ve PST dosyalarınıza Microsoft buluta yüklendikten sonra yetkisiz erişimi önlemeye yardımcı olur. PST dosyalarını içeri aktarmak, kuruluşunuzun ayrı bir Azure aboneliğine sahip olmasını gerektirmez.

2. **PST dosyalarını Azure Depolama konumuna yükleyin:** Sonraki adım, PST dosyalarınızı kuruluşunuzun bulunduğu bölgesel Microsoft veri merkezinde bulunan bir Azure Depolama konumunda karşıya yüklemek ve depolamak için azcopy.exe aracını (1. adımda indirilir) kullanmaktır. Bunları karşıya yüklemek için içeri aktarmak istediğiniz PST dosyalarının kuruluşunuzdaki bir dosya paylaşımında veya dosya sunucusunda bulunması gerekir.

    PST dosyalarının Azure Depolama konumuna yüklendikten sonra listesini görüntülemek için gerçekleştirebileceğiniz isteğe bağlı bir adım vardır.

3. **PST içeri aktarma eşleme dosyası oluşturma:** PST dosyaları Azure Depolama konumuna yüklendikten sonra, sonraki adım PST dosyalarının hangi kullanıcı posta kutularına aktarılacağını belirten bir virgülle ayrılmış değer (CSV) dosyası oluşturmaktır. PST dosyasının kullanıcının birincil posta kutusuna veya arşiv posta kutusuna aktarılabildiğini unutmayın. Microsoft 365 İçeri Aktarma hizmeti, PST dosyalarını içeri aktarmak için CSV dosyasındaki bilgileri kullanır.

4. **PST içeri aktarma işi oluşturma:** Sonraki adım, uyumluluk portalındaki **PST dosyalarını içeri aktar** sayfasında bir PST içeri aktarma işi oluşturmak ve önceki adımda oluşturulan PST içeri aktarma eşleme dosyasını göndermektir. İçeri aktarma işini oluşturduktan sonra, Microsoft 365 PST dosyalarındaki verileri analiz eder ve ardından pst içeri aktarma eşleme dosyasında belirtilen posta kutularına gerçekte hangi verilerin içeri aktarılacağını denetleyebilen filtreler ayarlama fırsatı verir.

5. **Posta kutularına aktarılacak PST verilerini filtreleyin:** İçeri aktarma işi oluşturulup başlatıldıktan sonra, Microsoft 365 öğelerin yaşını ve PST dosyalarına dahil edilen farklı ileti türlerini belirleyerek PST dosyalarındaki verileri (güvenli ve güvenli bir şekilde) analiz eder. Analiz tamamlandığında ve veriler içeri aktarmaya hazır olduğunda, PST dosyalarında yer alan tüm verileri içeri aktarma seçeneğiniz olur veya hangi verilerin içeri aktarılacağını denetleye filtreler ayarlayarak içeri aktarılan verileri kırpabilirsiniz.

6. **PST içeri aktarma işini başlatın:** İçeri aktarma işi başlatıldıktan sonra Microsoft 365, PST içeri aktarma eşleme dosyasındaki bilgileri kullanarak PSTs dosyalarını Azure Depolama konumundan kullanıcı posta kutularına aktarır. İçeri aktarma işiyle ilgili durum bilgileri (içeri aktarılan her PST dosyası hakkındaki bilgiler dahil) uyumluluk portalındaki **PST dosyalarını içeri aktar** sayfasında görüntülenir. İçeri aktarma işi tamamlandığında, işin durumu **Tamamlandı** olarak ayarlanır.
