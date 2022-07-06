---
title: PST dosyalarını almak için sürücü gönderimini kullanma
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 40829b57-793c-4d41-b171-e9270129173d
ms.custom: seo-marvel-apr2020
description: Yönetici, PST dosyalarını bir sabit sürücüye kopyalayıp Microsoft'a göndererek PST dosyalarını Microsoft 365 posta kutularına toplu olarak aktarmayı öğrenebilir.
ms.openlocfilehash: ac8b24c04823bf3635b7762d160cee71a356ebfd
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626083"
---
# <a name="use-drive-shipping-to-import-your-organizations-pst-files"></a>Kuruluşunuzun PST dosyalarını içeri aktarmak için sürücü gönderimini kullanma

**Bu makale yöneticilere yöneliktir. PST dosyalarını kendi posta kutunuza aktarmaya mı çalışıyorsunuz? Bkz. [Outlook .pst dosyasından e-postayı, kişileri ve takvimi içeri aktarma](https://go.microsoft.com/fwlink/p/?LinkID=785075)**
   
PST dosyalarını kullanıcı posta kutularına toplu olarak aktarmak için İçeri aktarma hizmeti ve sürücü gönderimi Office 365 kullanın. Sürücü gönderimi, PST dosyalarını bir sabit disk sürücüsüne kopyalamanız ve ardından sürücüyü fiziksel olarak Microsoft'a göndermeniz anlamına gelir. Microsoft sabit sürücünüzü aldığında, veri merkezi personeli verileri sabit sürücüden Microsoft bulutundaki bir depolama alanına kopyalar. Ardından, hangi verilerin içeri aktarılacağını denetleye filtreler ayarlayarak hedef posta kutularına aktarılan PST verilerini kırpma fırsatınız olur. İçeri aktarma işini başlattıktan sonra İçeri Aktarma hizmeti PST verilerini depolama alanından kullanıcı posta kutularına aktarır. PST dosyalarını kullanıcı posta kutularına aktarmak için sürücü gönderimini kullanmak, kuruluşunuzun e-postasını Office 365 geçirmenin bir yoludur.
  
PST dosyalarını Microsoft 365 posta kutularına aktarmak için sürücü gönderimini kullanmak için gereken adımlar şunlardır:
  
[1. Adım: PST İçeri Aktarma aracını indirme](#step-1-download-the-pst-import-tool)

[2. Adım: PST dosyalarını sabit sürücüye kopyalama](#step-2-copy-the-pst-files-to-the-hard-drive)

[3. Adım: PST İçeri Aktarma eşleme dosyasını oluşturma](#step-3-create-the-pst-import-mapping-file)

[4. Adım: Office 365'da PST İçeri Aktarma işi oluşturma](#step-4-create-a-pst-import-job-in-office-365)

[5. Adım: Sabit sürücüyü Microsoft'a gönderme](#step-5-ship-the-hard-drive-to-microsoft)

[6. Adım: Verileri filtreleme ve PST İçeri Aktarma işini başlatma](#step-6-filter-data-and-start-the-pst-import-job)
  
> [!IMPORTANT]
> İçeri aktarma aracını indirmek için 1. Adımı bir kez gerçekleştirmeniz gerekir. Bu adımları gerçekleştirdikten sonra, her sabit sürücüyü Microsoft'a göndermek istediğinizde 2. Adımdan 6. Adıma kadar ilerleyin. 
  
PST dosyalarını Office 365 aktarmak için sürücü gönderimi kullanma hakkında sık sorulan sorular için bkz. [PST dosyalarını içeri aktarmak için sürücü gönderimi kullanma hakkında SSS](./faqimporting-pst-files-to-office-365.yml#using-drive-shipping-to-import-pst-files). 
  
## <a name="before-you-import-pst-files"></a>PST dosyalarını içeri aktarmadan önce

- Microsoft Purview uyumluluk portalı içeri aktarma işleri oluşturmak ve PST dosyalarını kullanıcı posta kutularına aktarmak için Exchange Online'da Posta Kutusu İçeri Aktarma rolüne atanmış olmanız gerekir. Varsayılan olarak, bu rol Exchange Online'daki hiçbir rol grubuna atanmaz. Posta Kutusu İçeri Aktarma Dışarı Aktarma rolünü Kuruluş Yönetimi rol grubuna ekleyebilirsiniz. Ya da bir rol grubu oluşturabilir, Posta Kutusu İçeri Aktarma Dışarı Aktarma rolünü atayabilir ve ardından kendinizi üye olarak ekleyebilirsiniz. Daha fazla bilgi için Rol [gruplarını yönetme](/Exchange/permissions-exo/role-groups) bölümündeki "Rol grubuna rol ekleme" veya "Rol grubu oluşturma" bölümlerine bakın.

    Posta Kutusu İçeri Aktarma Dışarı Aktarma rolüne ek olarak, Exchange Online'de Posta Alıcıları rolüne de atanmış olmanız gerekir. Varsayılan olarak, bu rol Exchange Online'deki Kuruluş Yönetimi ve Alıcı Yönetimi rol gruplarına atanır.

    > [!TIP]
    > Exchange Online'da PST dosyalarını Office 365 içeri aktarmaya yönelik yeni bir rol grubu oluşturmayı göz önünde bulundurun. PST dosyalarını içeri aktarmak için gereken en düşük ayrıcalık düzeyi için, Posta Kutusu İçeri Aktarma Dışarı Aktarma ve Posta Alıcıları rollerini yeni rol grubuna atayın ve ardından üye ekleyin.
  
- Sabit sürücüye kopyalamak istediğiniz PST dosyalarını kuruluşunuzdaki bir dosya sunucusunda veya paylaşılan klasörde depolamanız gerekir. 2. Adımda, bu dosya sunucusunda veya paylaşılan klasörde depolanan PST dosyalarını sabit sürücüye kopyalayan Azure İçeri Aktarma Dışarı Aktarma aracını (WAImportExport.exe) çalıştırırsınız.

- Büyük PST dosyaları PST içeri aktarma işleminin performansını etkileyebilir. Bu nedenle, 2. Adımda sabit sürücüye kopyaladığınız her PST dosyasının 20 GB'tan büyük olmaması önerilir.

- yalnızca 2,5 inç katı hal sürücüleri (SSD' ler) veya 2,5 inç veya 3,5 inç SATA II/III dahili sabit sürücüler Office 365 İçeri Aktarma hizmetiyle kullanılmak üzere desteklenir. 10 TB'a kadar sabit sürücüleri kullanabilirsiniz. İçeri aktarma işleri için yalnızca sabit sürücüdeki ilk veri birimi işlenir. Veri birimi NTFS ile biçimlendirilmelidir. Bir sabit sürücüye veri kopyalarken, doğrudan 2,5 inç SSD veya 2,5 inç veya 3,5 inç SATA II/III bağlayıcı kullanarak veya harici bir 2,5 inç SSD veya 2,5 inç veya 3,5 inç SATA II/III USB bağdaştırıcısı kullanarak harici olarak takabilirsiniz.
    
    > [!IMPORTANT]
    > Yerleşik USB bağdaştırıcısıyla birlikte gelen harici sabit sürücüler, Office 365 İçeri Aktarma hizmeti tarafından desteklenmez. Ayrıca, harici bir sabit sürücünün kasası içindeki disk kullanılamaz. Lütfen harici sabit sürücüleri göndermeyin. 
  
- PST dosyalarını kopyaladığınız sabit sürücü BitLocker ile şifrelenmelidir. 2. Adımda çalıştırdığınız WAImportExport.exe aracı, BitLocker'ı ayarlamanıza yardımcı olur. Ayrıca, Microsoft veri merkezi personelinin PST dosyalarını Microsoft bulutunda Azure Depolama alanına yüklemek üzere sürücüye erişmek için kullandığı bir BitLocker şifreleme anahtarı oluşturur.
    
- Sürücü gönderimi bir Microsoft Kurumsal Anlaşma (EA) aracılığıyla sağlanır. Sürücü gönderimi, Microsoft Ürün ve Hizmet Sözleşmesi (MPSA) aracılığıyla kullanılamaz.
    
- PST dosyalarını Microsoft 365 posta kutularına sürücü gönderimi kullanarak aktarmanın maliyeti 1 GB veri başına 2 USD’dir. Örneğin, 1.000 GB (1 TB) PST dosyası içeren bir sabit sürücü gönderirseniz, maliyet 2.000 ABD dolarıdır. İthalat ücretini ödemek için bir iş ortağıyla çalışabilirsiniz. İş ortağı bulma hakkında bilgi için bkz. [Microsoft iş ortağınızı veya kurumsal bayinizi bulma](../admin/manage/find-your-partner-or-reseller.md).
    
- Sizin veya kuruluşunuzun FedEx veya DHL hesabı olmalıdır.
    
  - Birleşik Devletler, Brezilya ve Avrupa'daki kuruluşların FedEx hesapları olmalıdır.
    
  - Doğu Asya, Güneydoğu Asya, Japonya, Kore Cumhuriyeti ve Avustralya'daki kuruluşların DHL hesapları olmalıdır.
    
    Microsoft, sabit sürücüyü size geri döndürmek için bu hesabı kullanır (ve ücretlendirilir).
    
- Microsoft'a gönderdiğiniz sabit sürücü uluslararası sınırları aşabilir. Bu durumda, sabit sürücünün ve içerdiği verilerin ilgili yasalara uygun olarak içeri ve/veya dışarı aktarılmasını sağlamak sizin sorumluluğundadır. Sabit sürücüyü göndermeden önce, sürücünüzün ve verilerinizin tanımlanan Microsoft veri merkezine yasal olarak gönderilebildiğini doğrulamak için danışmanlarınıza danışın. Bu, Microsoft'a zamanında ulaşmasını sağlamaya yardımcı olur.
    
- Bu yordam, BitLocker şifreleme anahtarını kopyalamayı ve kaydetmeyi içerir. Parolaları veya güvenlikle ilgili diğer bilgileri korur gibi bu anahtarları korumak için önlem almayı unutmayın. Örneğin, bunları parola korumalı bir Microsoft Word belgesine veya şifrelenmiş bir USB sürücüsüne kaydedebilirsiniz. Bu anahtarların bir örneği için [Daha fazla bilgi](#more-information) bölümüne bakın. 
    
- PST dosyaları bir Microsoft 365 posta kutusuna aktarıldıktan sonra, posta kutusunun bekletme ayarı süresiz olarak açılır. Bu, saklama saklamayı kapatana veya saklamayı kapatmak için bir tarih ayarlayana kadar posta kutusuna atanan bekletme ilkesinin işlenmeyeceği anlamına gelir. Bunu neden yapıyoruz? Posta kutusuna içeri aktarılan iletiler eskiyse, posta kutusu için yapılandırılan bekletme ayarlarına göre bekletme süreleri dolduğundan kalıcı olarak silinebilir (temizlenebilir). Posta kutusunun bekletmeye yerleştirilmesi, posta kutusu sahibine bu yeni içeri aktarılan iletileri yönetmesi için zaman verir veya posta kutusunun bekletme ayarlarını değiştirmeniz için size zaman verir. Bekletme saklamayı yönetme hakkında öneriler için [Daha fazla bilgi](#more-information) bölümüne bakın. 
    
- Varsayılan olarak, Bir Microsoft 365 posta kutusu tarafından alınabilecek ileti boyutu üst sınırı 35 MB'tır. Bunun nedeni, bir posta kutusunun  *MaxReceiveSize*  özelliğinin varsayılan değerinin 35 MB olarak ayarlanmasıdır. Ancak, Microsoft 365'te ileti alma boyutu üst sınırı 150 MB'tır. Bu nedenle, 35 MB'tan büyük bir öğe içeren bir PST dosyasını içeri aktarırsanız İçeri Aktarma hizmeti Office 365 hedef posta kutusunda *MaxReceiveSize* özelliğinin değerini otomatik olarak 150 MB olarak değiştiririz. Bu, 150 MB'a kadar olan iletilerin kullanıcı posta kutularına aktarılmasını sağlar. 
    
    > [!TIP]
    > Bir posta kutusunun ileti alma boyutunu tanımlamak için şu komutu powershell Exchange Online de çalıştırabilirsiniz: `Get-Mailbox <user mailbox> | FL MaxReceiveSize`. 
  
- PST dosyalarını Office 365 etkin olmayan bir posta kutusuna aktarabilirsiniz. Bunu, PST İçeri Aktarma eşleme dosyasındaki parametresinde  `Mailbox` etkin olmayan posta kutusunun GUID'sini belirterek yaparsınız. Daha fazla bilgi için bkz [. 3. Adım: PST İçeri Aktarma eşleme dosyasını oluşturma](#step-3-create-the-pst-import-mapping-file) . 
    
- Exchange karma dağıtımında, birincil posta kutusu şirket içinde olan bir kullanıcının PST dosyalarını bulut tabanlı arşiv posta kutusuna aktarabilirsiniz. Bunu, PST İçeri Aktarma eşleme dosyasında aşağıdakileri yaparak yaparsınız:
    
  - parametresinde kullanıcının şirket içi posta kutusunun e-posta  `Mailbox` adresini belirtin. 
    
  - parametresinde `IsArchive` **TRUE** değerini belirtin. 
    
    Daha fazla bilgi için bkz [. 3. Adım: PST İçeri Aktarma eşleme dosyasını oluşturma](#step-3-create-the-pst-import-mapping-file) . 

## <a name="step-1-download-the-pst-import-tool"></a>1. Adım: PST İçeri Aktarma aracını indirme

İlk adım, aracı indirmek ve PST dosyalarını sabit sürücüye kopyalamak için 2. Adımda kullandığınız aracı indirmektir.
  
> [!IMPORTANT]
> Sürücü gönderim yöntemini kullanarak PST dosyalarını başarıyla içeri aktarmak için Azure İçeri/Dışarı Aktarma aracı sürüm 1'i (WAimportExportV1) kullanmanız gerekir. Azure İçeri/Dışarı Aktarma aracının 2. sürümü desteklenmez ve bunu kullanmak sabit sürücünün içeri aktarma işi için yanlış hazırlanmasına neden olur. Bu adımdaki yordamları izleyerek Microsoft Purview uyumluluk portalı Azure İçeri/Dışarı Aktarma aracını indirdiğinizden emin olun. 
  
1. <https://compliance.microsoft.com> Adresine gidin ve kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. Uyumluluk portalının sol gezinti bölmesinde **Veri yaşam döngüsü yönetimi** \> **İçeri Aktar'a** tıklayın.
    
    > [!NOTE]
    > Daha önce belirtildiği gibi, uyumluluk portalındaki **İçeri Aktar** sayfasına erişmek için size uygun izinlerin atanması gerekir.
  
3. **İçeri Aktar** sekmesinde Simge Ekle'ye tıklayın![.](../media/ITPro-EAC-AddIcon.gif) **Yeni içeri aktarma işi**.
    
4. İçeri aktarma işi sihirbazında, PST içeri aktarma işi için bir ad yazın ve **İleri'ye** tıklayın. Küçük harf, sayı, kısa çizgi ve alt çizgi kullanın. Büyük harfler kullanamaz veya ada boşluk ekleyemezsiniz.
    
5. **İçeri aktarma iş türünü seçin** sayfasında **Sabit sürücüleri fiziksel konumlarımızdan birine gönder'e** ve ardından **İleri'ye** tıklayın.
    
    ![Sürücü gönderimi içeri aktarma işi oluşturmak için Sabit sürücüleri fiziksel konumlarımızdan birine gönder'e tıklayın.](../media/1584fdc5-cd4c-4e47-932e-db6c8e07f5f8.png)
  
6. **Verileri içeri aktar** sayfasında aşağıdakileri yapın:     
    
    **Azure İçeri/Dışarı Aktarma aracını indirerek Azure İçeri/Dışarı** Aktarma (sürüm 1) aracını indirin.
    
    - WaImportExportV1.zip dosyasını yerel bilgisayarınızdaki bir klasöre kaydetmek için açılır pencerede **Farklı Kaydet'e** \> tıklayın.
    
    - WaImportExportV1.zip dosyasını ayıklayın.
    
7. Sihirbazı kapatmak için **İptal'e** tıklayın.
    
    4. Adımda **içeri aktarma** işini oluşturduğunuzda uyumluluk portalındaki İçeri Aktar sayfasına geri dönersiniz.

## <a name="step-2-copy-the-pst-files-to-the-hard-drive"></a>2. Adım: PST dosyalarını sabit sürücüye kopyalama

Sonraki adım, PST dosyalarını sabit sürücüye kopyalamak için WAImportExport.exe aracını kullanmaktır. Bu araç sabit sürücüyü BitLocker ile şifreler, PST'leri sabit sürücüye kopyalar ve kopyalama işlemiyle ilgili bilgileri depolayan bir günlük dosyası oluşturur. Bu adımı tamamlamak için PST dosyalarının kuruluşunuzdaki bir dosya paylaşımında veya dosya sunucusunda bulunması gerekir. Bu, aşağıdaki yordamda kaynak dizin olarak bilinir.

 Daha önce belirtildiği gibi, sabit sürücüye kopyaladığınız her PST dosyası 20 GB'tan büyük olmamalıdır. 20 GB'tan büyük PST dosyaları, 6. Adımda başladığınız PST içeri aktarma işleminin performansını etkileyebilir.
  
> [!IMPORTANT]
> Sabit sürücü için WAImportExport.exe aracını ilk kez çalıştırdıktan sonra, bundan sonra her seferinde farklı bir söz dizimi kullanmanız gerekir. Bu söz dizimi, PST dosyalarını sabit sürücüye kopyalamak için bu yordamın 4. adımında açıklanmıştır.
  
1. Yerel bilgisayarınızda bir Komut İstemi açın.
    
    > [!TIP]
    > Komut istemini yönetici olarak çalıştırırsanız (açtığınızda "Yönetici olarak çalıştır" seçeneğini belirleyerek) hata iletileri komut istemi penceresinde görüntülenir. Bu, WAImportExport.exe aracını çalıştırma sorunlarını gidermenize yardımcı olabilir.
  
2. 1. Adımda WAImportExport.exe aracını yüklediğiniz dizine gidin.
3. PST dosyalarını bir sabit sürücüye kopyalamak için WAImportExport.exe ilk kez kullandığınızda aşağıdaki komutu çalıştırın.

    ```powershell
    WAImportExport.exe PrepImport /j:<Name of journal file> /t:<Drive letter> /id:<Name of session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob /encrypt /logdir:<Log file location>
    ```

    Aşağıdaki tabloda parametreler ve gerekli değerleri açıklanmaktadır.
    
    |**Parametre**|**Açıklama**|**Örnek**|
    |:-----|:-----|:-----|
    | `/j:` <br/> |Günlük dosyasının adını belirtir. Bu dosya, WAImportExport.exe aracının bulunduğu klasöre kaydedilir. Microsoft'a gönderdiğiniz her sabit sürücüde bir günlük dosyası olmalıdır. PST dosyalarını bir sabit sürücüye kopyalamak için WAImportTool.exe her çalıştırdığınızda, bu sürücünün günlük dosyasına bilgiler eklenir.  <br/> Microsoft veri merkezi personeli, sabit sürücüyü 4. Adımda oluşturduğunuz içeri aktarma işiyle ilişkilendirmek ve PST dosyalarını Microsoft bulutunda Azure Depolama alanına yüklemek için günlük dosyasındaki bilgileri kullanır.  <br/> | `/j:PSTHDD1.jrn` <br/> |
    | `/t:` <br/> |Sabit sürücünün yerel bilgisayarınıza bağlıyken sürücü harfini belirtir.  <br/> | `/t:h` <br/> |
    | `/id:` <br/> |Kopyalama oturumunun adını belirtir. Bir oturum, dosyaları sabit sürücüye kopyalamak için WAImportExport.exe aracını her çalıştırdığınızda olarak tanımlanır. PST dosyaları, bu parametre tarafından belirtilen oturum adıyla adlı klasöre kopyalanır.  <br/> | `/id:driveship1` <br/> |
    | `/srcdir:` <br/> |Kuruluşunuzda oturum sırasında kopyalanacak PST dosyalarını içeren kaynak dizini belirtir. Bu parametrenin değerini çift tırnak işareti (" ") ile çevrelemeye özen gösterin.  <br/> | `/srcdir:"\\FILESERVER01\PSTs"` <br/> |
    | `/dstdir:` <br/> |PST'lerin yüklendiği Microsoft bulutundaki Azure Depolama alanındaki hedef dizini belirtir. değerini  `ingestiondata/`kullanmanız gerekir. Bu parametrenin değerini çift tırnak işareti (" ") ile çevrelemeye özen gösterin.  <br/> İsteğe bağlı olarak, bu parametrenin değerine ek bir dosya yolu da ekleyebilirsiniz. Örneğin, parametrede belirtilen  `/srcdir:` sabit sürücüdeki (URL biçimine dönüştürülür) kaynak dizinin dosya yolunu kullanabilirsiniz. Örneğin,  `\\FILESERVER01\PSTs` olarak  `FILESERVER01/PSTs`değiştirilir. Bu durumda, yine de dosya yoluna eklemeniz  `ingestiondata` gerekir. Bu örnekte parametresinin  `/dstdir:` değeri olacaktır  `"ingestiondata/FILESERVER01/PSTs"`.  <br/> Ek dosya yolunu eklemenin bir nedeni, aynı dosya adına sahip PST dosyalarınız olmasıdır.  <br/> > [!NOTE]> İsteğe bağlı yol adını eklerseniz, Bir PST dosyasının Azure Depolama alanına yüklendikten sonra ad alanı yol adını ve PST dosyasının adını içerir; örneğin,  `FILESERVER01/PSTs/annb.pst`. Yol adı eklemezseniz, ad alanı yalnızca PST dosya adıdır; örneğin  `annb.pst`, .           | `/dstdir:"ingestiondata/"` <br/> Veya  <br/>  `/dstdir:"ingestiondata/FILESERVER01/PSTs"` <br/> |
    | `/blobtype:` <br/> |PST dosyalarının içeri aktarılacağını Azure Depolama alanındaki blobların türünü belirtir. PST dosyalarını içeri aktarmak için **BlockBlob** değerini kullanın. Bu parametre gereklidir.   <br/> | `/blobtype:BlockBlob` <br/> |
    | `/encrypt` <br/> |Bu anahtar, sabit sürücü için BitLocker'i açar. bu parametre, WAImportExport.exe aracını ilk kez çalıştırdığınızda gereklidir.  <br/> BitLocker şifreleme anahtarı günlük dosyasına ve parametresini kullanırsanız  `/logfile:` oluşturulan günlük dosyasına kopyalanır. Daha önce açıklandığı gibi günlük dosyası, WAImportExport.exe aracının bulunduğu klasöre kaydedilir.  <br/> | `/encrypt` <br/> |
    | `/logdir:` <br/> |Bu isteğe bağlı parametre, günlük dosyalarının kaydedilecek bir klasörü belirtir. Belirtilmezse, günlük dosyaları WAImportExport.exe aracının bulunduğu klasöre kaydedilir. Bu parametrenin değerini çift tırnak işareti (" ") ile çevrelemeye özen gösterin.  <br/> | `/logdir:"c:\users\admin\desktop\PstImportLogs"` <br/> |
   
    Aşağıda, her parametre için gerçek değerleri kullanan WAImportExport.exe aracının söz dizimi örneği verilmiştir:
    
    ```powershell
    WAImportExport.exe PrepImport /j:PSTHDD1.jrn /t:f /id:driveship1 /srcdir:"\\FILESERVER01\PSTs" /dstdir:"ingestiondata/" blobtype:BlockBlob /encrypt /logdir:"c:\users\admin\desktop\PstImportLogs"
    ```

    Komutu çalıştırdıktan sonra, PST dosyalarını sabit sürücüye kopyalama işleminin ilerleme durumunu gösteren durum iletileri görüntülenir. Son durum iletisi, başarıyla kopyalanan dosyaların toplam sayısını gösterir.
    
4. PST dosyalarını aynı sabit sürücüye kopyalamak için WAImportExport.ext aracını her çalıştırdığınızda bu komutu çalıştırın.

    ```powershell
    WAImportExport.exe PrepImport /j:<Name of journal file> /id:<Name of new session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob 
    ```

    Aşağıda, PST dosyalarını aynı sabit sürücüye kopyalamak için sonraki oturumları çalıştırmaya yönelik söz dizimi örneği verilmiştir.

    ```powershell
    WAImportExport.exe PrepImport /j:PSTHDD1.jrn /id:driveship2 /srcdir:"\\FILESERVER01\PSTs\SecondBatch" /dstdir:"ingestiondata/" /blobtype:BlockBlob
    ```

## <a name="step-3-create-the-pst-import-mapping-file"></a>3. Adım: PST İçeri Aktarma eşleme dosyasını oluşturma

Microsoft veri merkezi personeli PST dosyalarını sabit sürücüden Azure Depolama alanına yükledikten sonra İçeri Aktarma hizmeti, PST dosyalarının hangi kullanıcı posta kutularına aktarılacağını belirten, virgülle ayrılmış bir değer (CSV) dosyası olan PST İçeri Aktarma eşleme dosyasındaki bilgileri kullanır. Bir PST İçeri Aktarma işi oluşturduğunuzda sonraki adımda bu CSV dosyasını gönderebilirsiniz.
  
1. [PST İçeri Aktarma eşleme dosyasının bir kopyasını indirin](https://go.microsoft.com/fwlink/p/?LinkId=544717).
    
2. CSV dosyasını yerel bilgisayarınıza açın veya kaydedin. Aşağıdaki örnekte tamamlanmış bir PST İçeri Aktarma eşleme dosyası (Not Defteri'nde açılır) gösterilmektedir. CSV dosyasını düzenlemek için Microsoft Excel'i kullanmak çok daha kolaydır.

    ```text
    Workload,FilePath,Name,Mailbox,IsArchive,TargetRootFolder,ContentCodePage,SPFileContainer,SPManifestContainer,SPSiteUrl
    Exchange,FILESERVER01/PSTs,annb.pst,annb@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,FILESERVER01/PSTs,annb_archive.pst,annb@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,FILESERVER01/PSTs,donh.pst,donh@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,FILESERVER01/PSTs,donh_archive.pst,donh@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,FILESERVER01/PSTs,pilarp.pst,pilarp@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,FILESERVER01/PSTs,pilarp_archive.pst,pilarp@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,,tonyk.pst,tonyk@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,,tonyk_archive.pst,tonyk@contoso.onmicrosoft.com,TRUE,,,,,
    Exchange,,zrinkam.pst,zrinkam@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,,zrinkam_archive.pst,zrinkam@contoso.onmicrosoft.com,TRUE,,,,,
    ```

    CSV dosyasının ilk satırı veya üst bilgi satırı, PST İçeri Aktarma hizmeti tarafından PST dosyalarını kullanıcı posta kutularına aktarmak için kullanılacak parametreleri listeler. Her parametre adı virgülle ayrılır. Üst bilgi satırının altındaki her satır, pst dosyasını belirli bir posta kutusuna aktarmaya yönelik parametre değerlerini temsil eder. Sabit sürücüye kopyalanan her PST dosyası için bir satıra ihtiyacınız vardır. Eşleme dosyasındaki yer tutucu verileri gerçek verilerinizle değiştirerek değiştirmeyi unutmayın.

    > [!NOTE]
    > SharePoint parametreleri de dahil olmak üzere üst bilgi satırında hiçbir şeyi değiştirmeyin; PST İçeri Aktarma işlemi sırasında yoksayılırlar. 
  
3. CSV dosyasını gerekli bilgilerle doldurmak için aşağıdaki tabloda yer alan bilgileri kullanın.
    
    |**Parametre**|**Açıklama**|**Örnek**|
    |:-----|:-----|:-----|
    | `Workload` <br/> |Verilerin içeri aktarılacağı hizmeti belirtir. PST dosyalarını kullanıcı posta kutularına aktarmak için kullanın  `Exchange`.  <br/> | `Exchange` <br/> |
    | `FilePath` <br/> | Sabit sürücü Microsoft'a gönderildiğinde PST dosyalarının kopyalanacağı Azure Depolama alanındaki klasör konumunu belirtir.  <br/>  CSV dosyasındaki bu sütuna ne eklediğiniz, önceki adımda parametresi için  `/dstdir:` ne belirttiğinize bağlıdır. Kaynak konumda alt klasörleriniz varsa, parametredeki `FilePath` değer alt klasörün göreli yolunu içermelidir; örneğin, /folder1/user1/.  <br/>  kullandıysanız  `/dstdir:"ingestiondata/"`, csv dosyasında bu parametreyi boş bırakın.  <br/>  parametresinin  `/dstdir:` değeri için isteğe bağlı bir yol adı eklediyseniz (örneğin,  `/dstdir:"ingestiondata/FILESERVER01/PSTs"`), CSV dosyasındaki bu parametre için bu yol adını ("ingestiondata" dahil değil) kullanın. Bu parametrenin değeri büyük/küçük harfe duyarlıdır.  <br/>  Her iki durumda  *da parametresinin*  değerine "ingestiondata" eklemeyin  `FilePath` . Bu parametreyi boş bırakın veya yalnızca isteğe bağlı yol adını belirtin.  <br/> > [!IMPORTANT]> Dosya yolu adı için durum, önceki adımda parametresinde  `/dstdir:` belirttiğiniz durumla aynı olmalıdır. Örneğin, önceki adımda alt klasör adı için kullandıysanız`"ingestiondata/FILESERVER01/PSTs"`, ancak ardından CSV dosyasındaki `FilePath` parametrede kullandıysanız`fileserver01/psts`, PST dosyasının içeri aktarma işlemi başarısız olur. Her iki durumda da aynı durumu kullandığınızdan emin olun.           |(boş bırakın)  <br/> Veya  <br/>  `FILESERVER01/PSTs` <br/> |
    | `Name` <br/> |Kullanıcı posta kutusuna aktarılacak PST dosyasının adını belirtir. Bu parametrenin değeri büyük/küçük harfe duyarlıdır.  <br/> > [!IMPORTANT]> CSV dosyasındaki PST dosya adının durumu, 2. Adımda Azure Depolama konumuna yüklenen PST dosyasıyla aynı olmalıdır. Örneğin, CSV dosyasındaki parametresinde `Name` kullanıyorsanız `annb.pst` ancak asıl PST dosyasının adı ise`AnnB.pst`, o PST dosyasının içeri aktarma işlemi başarısız olur. CSV dosyasındaki PST adının gerçek PST dosyasıyla aynı durumu kullandığından emin olun.           | `annb.pst` <br/> |
    | `Mailbox` <br/> |PST dosyasının içeri aktarılacağı posta kutusunun e-posta adresini belirtir. PST İçeri Aktarma Hizmeti, PST dosyalarının ortak klasörlere aktarılmasını desteklemediğinden ortak klasör belirtemezsiniz.  <br/> Pst dosyasını etkin olmayan bir posta kutusuna aktarmak için bu parametre için posta kutusu GUID'sini belirtmeniz gerekir. Bu GUID'yi almak için Exchange Online aşağıdaki PowerShell komutunu çalıştırın:`Get-Mailbox <identity of inactive mailbox> -InactiveMailboxOnly | FL Guid` <br/> > [!NOTE]> Bazen, aynı e-posta adresine sahip birden çok posta kutunuz olabilir; burada bir posta kutusu etkin bir posta kutusu, diğer posta kutusu geçici olarak silinmiş (veya etkin olmayan) durumdadır. Bu durumlarda, PST dosyasını içeri aktarılacak posta kutusunu benzersiz olarak tanımlamak için posta kutusu GUID'sini belirtmeniz gerekir. Etkin posta kutuları için bu GUID'yi almak için aşağıdaki PowerShell komutunu çalıştırın:  `Get-Mailbox <identity of active mailbox> | FL Guid`. Geçici olarak silinen (veya etkin olmayan) posta kutularının GUID'sini almak için şu komutu çalıştırın:  `Get-Mailbox <identity of soft-deleted or inactive mailbox> -SoftDeletedMailbox | FL Guid`.           | `annb@contoso.onmicrosoft.com` <br/> Veya  <br/>  `2d7a87fe-d6a2-40cc-8aff-1ebea80d4ae7` <br/> |
    | `IsArchive` <br/> | PST dosyasının kullanıcının arşiv posta kutusuna içeri aktarılıp aktarılmayacağını belirtir. İki seçenek vardır:  <br/> **FALSE** PST dosyasını kullanıcının birincil posta kutusuna aktarır.  <br/> **TRUE** PST dosyasını kullanıcının arşiv posta kutusuna aktarır. Bu, [kullanıcının arşiv posta kutusunun etkinleştirildiğini](enable-archive-mailboxes.md) varsayar. Bu parametreyi olarak  `TRUE` ayarlarsanız ve kullanıcının arşiv posta kutusu etkinleştirilmezse, söz konusu kullanıcının içeri aktarma işlemi başarısız olur. Bir kullanıcı için içeri aktarma işlemi başarısız olursa (arşivi etkinleştirilmediğinden ve bu özellik olarak ayarlandığından  `TRUE`), içeri aktarma işindeki diğer kullanıcılar etkilenmez.  <br/>  Bu parametreyi boş bırakırsanız, PST dosyası kullanıcının birincil posta kutusuna aktarılır.  <br/> **Not:** Pst dosyasını, birincil posta kutusu şirket içi olan bir kullanıcının bulut tabanlı arşiv posta kutusuna aktarmak için, bu parametre için belirtin  `TRUE` ve kullanıcının şirket içi posta kutusunun e-posta adresini parametre için  `Mailbox` belirtin.  <br/> | `FALSE` <br/> Veya  <br/>  `TRUE` <br/> |
    | `TargetRootFolder` <br/> | PST dosyasının içeri aktarıldığını posta kutusu klasörünü belirtir.  <br/>  Bu parametreyi boş bırakırsanız PST, posta kutusunun kök düzeyinde (Gelen Kutusu klasörü ve diğer varsayılan posta kutusu klasörleriyle aynı düzeyde) bulunan **İçeri Aktarıldı** adlı yeni bir klasöre aktarılır.  <br/>  belirtirseniz  `/`, PST dosyasındaki öğeler doğrudan kullanıcının Gelen Kutusu klasörüne aktarılır.  <br/>  belirtirseniz  `/<foldername>`, PST dosyasındaki öğeler adlı  *\<foldername\>* bir klasöre aktarılır. Örneğin, kullanırsanız  `/ImportedPst`, öğeler **ImportedPst** adlı bir klasöre aktarılır. Bu klasör, kullanıcının posta kutusunda Gelen Kutusu klasörüyle aynı düzeyde bulunur.  <br/> |(boş bırakın)  <br/> Veya  <br/>  `/` <br/> Veya  <br/>  `/ImportedPst` <br/> |
    | `ContentCodePage` <br/> |Bu isteğe bağlı parametre, PST dosyalarını ANSI dosya biçiminde içeri aktarmak için kullanılacak kod sayfası için sayısal bir değer belirtir. Bu diller genellikle karakter kodlaması için çift bayt karakter kümesi (DBCS) kullandığından, bu parametre Çince, Japonca ve Korece (CJK) kuruluşlarından PST dosyalarını içeri aktarmak için kullanılır. Bu parametre, posta kutusu klasör adları için DBCS kullanan diller için PST dosyalarını içeri aktarmak için kullanılmazsa, klasör adları genellikle içeri aktarıldıktan sonra bozuk olur.  <br/> Bu parametre için kullanılacak desteklenen değerlerin listesi için bkz. [Kod Sayfası Tanımlayıcıları](/windows/win32/intl/code-page-identifiers).  <br/> > [!NOTE]> Daha önce belirtildiği gibi, bu isteğe bağlı bir parametredir ve CSV dosyasına eklemeniz gerekmez. İsterseniz, bu değeri dahil edebilir ve değeri bir veya daha fazla satır için boş bırakabilirsiniz.           |(boş bırakın)  <br/> Veya  <br/>  `932` (ANSI/OEM Japonca için kod sayfası tanımlayıcısı)  <br/> |
    | `SPFileContainer` <br/> |PST İçeri Aktarma için bu parametreyi boş bırakın.  <br/> |Geçerli değil  <br/> |
    | `SPManifestContainer` <br/> |PST İçeri Aktarma için bu parametreyi boş bırakın.  <br/> |Geçerli değil  <br/> |
    | `SPSiteUrl` <br/> |PST İçeri Aktarma için bu parametreyi boş bırakın.  <br/> |Geçerli değil  <br/> |

## <a name="step-4-create-a-pst-import-job-in-office-365"></a>4. Adım: Office 365'da PST İçeri Aktarma işi oluşturma

Sonraki adım, Office 365'da İçeri Aktarma hizmetinde PST İçeri Aktarma işini oluşturmaktır. Daha önce açıklandığı gibi, 3. Adımda oluşturduğunuz PST İçeri Aktarma eşleme dosyasını gönderirsiniz. İşi oluşturduktan sonra İçeri Aktarma hizmeti, PST dosyaları sabit sürücüden Azure Depolama alanına kopyalanıp içeri aktarma işini oluşturup başlattıktan sonra PST dosyalarını belirtilen kullanıcı posta kutusuna aktarmak için eşleme dosyasındaki bilgileri kullanır.
  
1. <https://compliance.microsoft.com> Adresine gidin ve kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. Uyumluluk portalının sol gezinti bölmesinde **Veri yaşam döngüsü yönetimi** \> **İçeri Aktar'a** tıklayın.

3. **İçeri Aktar** sekmesinde Simge Ekle'ye tıklayın![.](../media/ITPro-EAC-AddIcon.gif) **Yeni içeri aktarma işi**.

    > [!NOTE]
    > Daha önce belirtildiği gibi, uyumluluk portalındaki **İçeri Aktar** sayfasına erişmek için size uygun izinlerin atanması gerekir.
  
4. PST içeri aktarma işi için bir ad yazın ve **İleri'ye** tıklayın. Küçük harf, sayı, kısa çizgi ve alt çizgi kullanın. Büyük harfler kullanamaz veya ada boşluk ekleyemezsiniz.

5. **İçeri aktarma iş türünü seçin** sayfasında **Sabit sürücüleri fiziksel konumlarımızdan birine gönder'e** ve ardından **İleri'ye** tıklayın.
  
6. 6. adımda, **sabit sürücülerimi hazırladım ve gerekli sürücü günlüğü dosyalarına erişimim var** ve **eşleme dosyasına erişimim var onay kutularına** tıklayın ve ardından **İleri'ye** tıklayın.

    ![6. adımda iki onay kutusuna tıklayın.](../media/fad43078-ea68-4acd-b2ed-75a800183262.png)
  
7. **Sürücü dosyasını seçin** sayfasında **Sürücü dosyasını seç'e** tıklayın ve ardından WAImportExport.exe aracının bulunduğu klasöre gidin. 2. Adımda oluşturulan günlük dosyası bu klasöre kopyalandı.

    ![WAImportExport.exe aracını çalıştırdığınızda oluşturulan günlük dosyasını göndermek için Sürücü dosyasını seç'e tıklayın.](../media/1ea35c04-bd88-4d7e-b7d9-dc390149d94f.png)
  
8. Günlük dosyasını seçin; örneğin, `PSTHDD1.jrn`.

    > [!TIP]
    > 2. Adımda WAImportExport.exe aracını çalıştırdığınızda, günlük dosyasının adı parametresi tarafından  `/j:` belirtildi.
  
9. Sürücü dosyasının adı **Sürücü dosyası** adı altında gösterildikten sonra, sürücü dosyanızda hata olup olmadığını denetlemek için **Doğrula'ya** tıklayın.

    ![Seçtiğiniz sürücü dosyasını doğrulamak için Doğrula'ya tıklayın.](../media/4b707f5a-152a-4e74-b9f5-449c88d1fec4.png)
  
    Bir PST İçeri Aktarma işi oluşturmak için sürücü dosyasının başarıyla doğrulanması gerekir. Dosya adı başarıyla doğrulandıktan sonra yeşil olarak değiştirilir. Doğrulama başarısız olursa **Günlüğü görüntüle** bağlantısına tıklayın. Dosyanın neden başarısız olduğu hakkında bilgi içeren bir hata iletisiyle birlikte bir doğrulama hata raporu açılır. 

    > [!NOTE]
    > Microsoft'a sevk ettiğiniz her sabit sürücü için bir günlük dosyası eklemeniz ve doğrulamanız gerekir. 
  
10. Microsoft'a gönderdiğiniz her sabit sürücü için günlük dosyası ekledikten ve doğruladıktan sonra **İleri'ye** tıklayın.
    
11. Simge Ekle'ye tıklayın ![.](../media/ITPro-EAC-AddIcon.gif) 3. Adımda oluşturduğunuz PST İçeri Aktarma eşleme dosyasını göndermek için **eşleme dosyasını seçin**. 

    ![İçeri aktarma işi için oluşturduğunuz CSV dosyasını göndermek için Eşleme dosyasını seç'e tıklayın.](../media/d30b1d73-80bb-491e-a642-a21673d06889.png)
  
12. CSV dosyasının adı **Eşleme dosyası adı** altında gösterildikten sonra, CSV dosyanızda hata olup olmadığını denetlemek için **Doğrula'ya** tıklayın. 

    ![CSV dosyasının hatalarını denetlemek için Doğrula'ya tıklayın.](../media/4680999d-5538-4059-b878-2736a5445037.png)
  
    PST İçeri Aktarma işi oluşturmak için CSV dosyasının başarıyla doğrulanması gerekir. Dosya adı başarıyla doğrulandıktan sonra yeşil olarak değiştirilir. Doğrulama başarısız olursa **Günlüğü görüntüle** bağlantısına tıklayın. Dosyadaki her satır için başarısız olan bir hata iletisiyle birlikte bir doğrulama hata raporu açılır. 

13. PST eşleme dosyası başarıyla doğrulandıktan sonra **İleri'ye** tıklayın.

14. **İletişim bilgilerini sağla** sayfasında, ilgili kutulara iletişim bilgilerinizi yazın. 

    Sabit sürücülerinizi gönderdiğiniz Microsoft konumunun adresi görüntülenir. Bu adres, Microsoft veri merkezi konumunuza göre otomatik olarak oluşturulur. Bu adresi bir dosyaya kopyalayın veya ekran görüntüsü alın.

15. Hüküm ve koşullar belgesini okuyun, onay kutusuna tıklayın ve ardından **kaydet'e** tıklayarak içeri aktarma işini gönderin. 

    İçeri aktarma işi başarıyla oluşturulduğunda, sürücü gönderim işleminin sonraki adımlarını açıklayan bir durum sayfası görüntülenir.

16. **İçeri Aktar** sekmesinde Yenile simgesine tıklayın![.](../media/O365-MDM-Policy-RefreshIcon.gif) İçeri aktarma işleri listesinde yeni sürücü gönderimi içeri aktarma işini görüntülemek için **yenileyin**. Durum, **İzleme numarası bekleniyor** olarak ayarlanır. İçeri aktarma işi hakkında daha ayrıntılı bilgiler içeren durum açılır sayfasını görüntülemek için içeri aktarma işine de tıklayabilirsiniz.

## <a name="step-5-ship-the-hard-drive-to-microsoft"></a>5. Adım: Sabit sürücüyü Microsoft'a gönderme

Sonraki adım, sabit sürücüyü Microsoft'a göndermek ve ardından sürücü gönderim işi için sevkiyat ve iade gönderimi bilgilerini takip numarası sağlamaktır. Sürücü Microsoft tarafından alındıktan sonra veri merkezi personelinin PST dosyalarınızı kuruluşunuz için Azure Depolama alanına yüklemesi 7 ila 10 iş günü arasında sürer.
  
> [!NOTE]
> İçeri aktarma işini oluşturduktan sonra 14 gün içinde takip numarasını ve iade sevkiyat bilgilerini sağlamazsanız, içeri aktarma işinin süresi dolar. Böyle bir durumda yeni bir sürücü gönderimi içeri aktarma işi oluşturmanız (bkz[. 4. Adım: Office 365'de PST İçeri Aktarma işi oluşturma](#step-4-create-a-pst-import-job-in-office-365)) ve sürücü dosyasını ve PST içeri aktarma eşleme dosyasını yeniden göndermeniz gerekir.
  
### <a name="ship-the-hard-drive"></a>Sabit sürücüyü gönderme

Sabit sürücüleri Microsoft'a gönderirken aşağıdakileri göz önünde bulundurun:
  
- SATA-USB bağdaştırıcısını göndermeyin; sadece sabit sürücüyü göndermeniz gerekir.

- Sabit sürücüyü düzgün bir şekilde paketleyin; örneğin, statik olmayan bir torba veya kabarcık sarmalama kullanın.

- Sabit sürücüyü Microsoft'a göndermek için istediğiniz teslimat taşıyıcısını kullanın.

- Sabit sürücüyü, 4. Adımda içeri aktarma işini oluştururken görüntülenen Microsoft konumunun adresine sevk edin. Sevk yeri adresine "Office 365 İçeri Aktarma Hizmeti" eklemeyi unutmayın.

- Sabit sürücüyü sevk ettikten sonra, teslimat taşıyıcısının adını ve takip numarasını yazdığınızdan emin olun. Sonraki adımda bunları sağlayacaksınız.
    
### <a name="enter-the-tracking-number-and-other-shipping-information"></a>takip numarasını ve diğer sevkiyat bilgilerini girin

Sabit sürücüyü Microsoft'a gönderdikten sonra hizmeti içeri aktarma sayfasında aşağıdaki yordamı tamamlayın.
  
1. <https://compliance.microsoft.com> Adresine gidin ve kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. Uyumluluk portalının sol gezinti bölmesinde **Veri yaşam döngüsü yönetimi** > **İçeri Aktar'a** tıklayın.

3. **İçeri Aktar** sekmesinde, takip numarasını girmek istediğiniz sürücü sevkiyatının işine tıklayın.

4. Durum açılır sayfasında **İzleme numarasını girin'e** tıklayın.

5. Aşağıdaki sevkiyat bilgilerini sağlayın:

   1. **Teslimat taşıyıcısı** Sabit sürücüyü Microsoft'a göndermek için kullandığınız teslimat taşıyıcısının adını yazın. 

   2. **İzleme numarası** Sabit sürücü sevkiyatı için izleme numarasını yazın. 

   3. **İade taşıyıcı hesap numarası** **İade** taşıyıcısı altında listelenen operatör için kuruluşunuzun hesap numarasını yazın. Microsoft, sabit sürücünüzü size geri göndermek için bu hesabı kullanır (ve ücretlendirilir). ABD ve Avrupa'daki kuruluşların FedEx hesabı olmalıdır. Asya'daki ve dünyanın geri kalanındaki kuruluşların DHL hesabı olmalıdır.

6. İçeri aktarma işi için bu bilgileri kaydetmek için **Kaydet'e** tıklayın. 

    **İçeri Aktar** sekmesinde Yenile simgesine tıklayın![.](../media/O365-MDM-Policy-RefreshIcon.gif) Sürücü gönderimi içeri aktarma işinizin bilgilerini güncelleştirmek için **yenileyin**. Durumun artık **Aktarımdaki Sürücüler** olarak ayarlandığına dikkat edin.

## <a name="step-6-filter-data-and-start-the-pst-import-job"></a>6. Adım: Verileri filtreleme ve PST İçeri Aktarma işini başlatma

Sabit sürücünüz Microsoft tarafından alındıktan sonra PST **dosyalarını içeri aktar** sayfasındaki içeri aktarma işinin durumu **Alınan Sürücüler** olarak değişir. Veri merkezi personeli, PST dosyalarınızı kuruluşunuzun Azure Depolama alanına yüklemek için günlük dosyasındaki bilgileri kullanır. Bu noktada, durum **devam eden İçeri aktar** olarak değişir. Daha önce belirtildiği gibi, PST dosyalarını karşıya yüklemek için sabit sürücünüzü aldıktan sonra 7 ila 10 iş günü sürer.
  
PST dosyaları Azure'a yüklendikten sonra durum **Analiz sürüyor** olarak değiştirilir. Bu, Microsoft 365'in öğelerin yaşını ve PST dosyalarına dahil edilen farklı ileti türlerini tanımlamak için PST dosyalarındaki verileri (güvenli ve güvenli bir şekilde) analiz ettiğini gösterir. Çözümleme tamamlandığında ve veriler içeri aktarmaya hazır olduğunda, içeri aktarma işinin durumu **Çözümleme tamamlandı** olarak değiştirilir. Bu noktada, PST dosyalarında yer alan tüm verileri içeri aktarma seçeneğiniz vardır veya hangi verilerin içeri aktarılacağını denetleyebilen filtreler ayarlayarak içeri aktarılan verileri kırpabilirsiniz.
  
1. <https://compliance.microsoft.com> Adresine gidin ve kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. Uyumluluk portalının sol gezinti bölmesinde **Veri yaşam döngüsü yönetimi** \> **İçeri aktar***'a tıklayın.

3. **İçeri Aktar** sekmesinde, 4. Adımda oluşturduğunuz içeri aktarma işini seçin ve **Office 365 için İçeri Aktar'a** tıklayın.
  
    PST dosyaları ve içeri aktarma işiyle ilgili diğer bilgiler içeren bir açılır sayfa görüntülenir.

4. **Office 365 için İçeri Aktar'a** tıklayın.

5. **Verilerinizi filtreleyin** sayfası görüntülenir. Verilerin yaşıyla ilgili bilgiler de dahil olmak üzere Office 365 tarafından PST dosyalarında gerçekleştirilen analizden kaynaklanan veri içgörülerini içerir. Bu noktada, içeri aktarılacak verileri filtreleme veya tüm verileri olduğu gibi içeri aktarma seçeneğiniz vardır. 

    ![PST dosyalarındaki verileri kırpabilir veya tümünü içeri aktarabilirsiniz.](../media/287fc030-99e9-417b-ace7-f64617ea5d4e.png)
  
6. Şunlardan birini yapın:

   1. İçeri aktardığınız verileri kırpmak için **Evet, içeri aktarmadan önce filtrelemek istiyorum'a** tıklayın.

      PST dosyalarındaki verileri filtreleme ve içeri aktarma işini başlatma hakkında ayrıntılı adım adım yönergeler için bkz. [PST dosyalarını Office 365 içeri aktarırken verileri filtreleme](filter-data-when-importing-pst-files.md).

      Veya

   1. PST dosyalarındaki tüm verileri içeri aktarmak için **Hayır, her şeyi içeri aktarmak istiyorum'a** tıklayın ve **İleri'ye** tıklayın.

7. Tüm verileri içeri aktarmayı seçtiyseniz, içeri aktarma işini başlatmak için **Verileri içeri aktar'a** tıklayın. 

    İçeri aktarma işinin durumu **PST dosyalarını içeri aktar** sayfasında görüntülenir. Yenile simgesine tıklayın ![.](../media/O365-MDM-Policy-RefreshIcon.gif) **Durum** sütununda görüntülenen durum bilgilerini güncelleştirmek için **yenileyin**. İçeri aktarılan her PST dosyasıyla ilgili durum bilgilerini görüntüleyen durum açılır listesini görüntülemek için içeri aktarma işine tıklayın. İçeri aktarma işlemi tamamlandığında ve PST dosyaları kullanıcı posta kutularına aktarıldığında, durum **Tamamlandı** olarak değiştirilir.

## <a name="view-a-list-of-the-pst-files-uploaded-to-microsoft-365"></a>Microsoft 365'e yüklenen PST dosyalarının listesini görüntüleme

Kuruluşunuzun Azure Depolama alanına (Microsoft veri merkezi personeli tarafından) yüklendiğimiz PST dosyalarının listesini görüntülemek için Microsoft Azure Depolama Gezgini (ücretsiz, açık kaynak bir araçtır) yükleyip kullanabilirsiniz. Bunu, Microsoft'a gönderdiğiniz sabit sürücülerden PST dosyalarının Azure Depolama alanına başarıyla yüklendiğini doğrulamak için yapabilirsiniz.
  
> [!IMPORTANT]
> PST dosyalarını karşıya yüklemek veya değiştirmek için Azure Depolama Gezgini kullanamazsınız. PST dosyalarını Microsoft 365'e aktarmak için desteklenen tek yöntem AzCopy kullanmaktır. Ayrıca, Azure blob'a yüklediğiniz PST dosyalarını silemezsiniz. BIR PST dosyasını silmeye çalışırsanız, gerekli izinlere sahip olmadığınız konusunda bir hata alırsınız. Tüm PST dosyaları Azure Depolama alanınızdan otomatik olarak silinir. Devam eden içeri aktarma işi yoksa, en son içeri aktarma işi oluşturulduktan 30 gün sonra ** alma verileri ** kapsayıcısında bulunan tüm PST dosyaları silinir.
  
Kuruluşunuzun Paylaşılan Erişim İmzası (SAS) URL'sini almak için aşağıdaki adımları gerçekleştirin. Bu URL, kuruluşunuz için Microsoft bulutundaki Azure Depolama konumu için ağ URL'si ile SAS anahtarının bir birleşimidir. Bu anahtar, kuruluşunuzun Azure Depolama konumuna erişmek için gerekli izinleri sağlar.

Azure Depolama Gezgini yüklemek ve Azure Depolama alanınıza bağlanmak için:

1. <https://compliance.microsoft.com> Adresine gidin ve kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. Uyumluluk portalının sol bölmesinde **Veri yaşam döngüsü yönetimi** > **İçeri Aktar'a** tıklayın.

3. **İçeri Aktar** sekmesinde Simge Ekle'ye tıklayın![.](../media/ITPro-EAC-AddIcon.gif) **Yeni içeri aktarma işi**.

4. İçeri aktarma işi sihirbazında, PST içeri aktarma işi için bir ad yazın ve **İleri'ye** tıklayın. Küçük harf, sayı, kısa çizgi ve alt çizgi kullanın. Büyük harfler kullanamaz veya ada boşluk ekleyemezsiniz.

5. **İçeri aktarma iş türünü seçin** sayfasında **Verilerinizi karşıya yükle'ye** ve ardından **İleri'ye** tıklayın.

6. 2. adımda **Ağ karşıya yükleme SAS URL'sini göster'e** tıklayın.

7. URL görüntülendikten sonra kopyalayın ve bir dosyaya kaydedin. URL'nin tamamını kopyaladığınızdan emin olun.

    > [!IMPORTANT]
    > SAS URL'sini korumak için önlem almayı unutmayın. Bu, kuruluşunuz için Azure depolama alanına erişmek için herkes tarafından kullanılabilir.
  
8. İçeri aktarma işi sihirbazını kapatmak için **İptal'e** tıklayın.

9. [Microsoft Azure Depolama Gezgini aracını](https://go.microsoft.com/fwlink/p/?LinkId=544842) indirin ve yükleyin.

10. Microsoft Azure Depolama Gezgini başlatın, sol bölmede **Depolama Hesapları'na** sağ tıklayın ve ardından **Azure Depolama'ya Bağlan'a** tıklayın.

    ![Depolama Hesapları'na sağ tıklayın ve ardından Azure Depolama'ya Bağlan'a tıklayın.](../media/75b80cc3-c336-4f96-ad32-54ac9b96a7af.png)
  
11. **Paylaşılan erişim imzası (SAS) URI'sini veya bağlantı dizesini kullan'a** ve **ardından İleri'ye** tıklayın.

12. **SAS URI'si kullan'a** tıklayın, 1. adımda aldığınız SAS URL'sini **URI'nin** altındaki kutuya yapıştırın ve ardından **İleri'ye** tıklayın.

13. **Bağlantı özeti** sayfasında bağlantı bilgilerini gözden geçirebilir ve **bağlan'a** tıklayabilirsiniz.

    **ingestiondata** kapsayıcısı açılır. Sabit sürücünüzden PST dosyalarını içerir. **ingestiondata** kapsayıcısı **Depolama Hesapları** \> **(SAS Bağlı Hizmetler)** \> **Blob Kapsayıcıları** altında bulunur.

    ![Azure Depolama Gezgini karşıya yüklediğiniz PST dosyalarının listesini görüntüler.](../media/12376fed-13a5-4a09-8fe6-e819e011b334.png)
  
14. Microsoft Azure Depolama Gezgini kullanmayı bitirdiğinizde, **alma verileri'ne** sağ tıklayın ve ardından Azure Depolama alanınızın bağlantısını kesmek için **Ayır'a** tıklayın. Aksi takdirde, bir sonraki ekleme denemesinde bir hata alırsınız. 

    ![Alma işlemine sağ tıklayın ve Azure Depolama alanınızın bağlantısını kesmek için Ayır'a tıklayın.](../media/1e8e5e95-4215-4ce4-a13d-ab5f826a0510.png)

## <a name="troubleshooting-tips"></a>Sorun giderme ipuçları

- **PST İçeri Aktarma CSV eşleme dosyasındaki hatalar nedeniyle içeri aktarma işi başarısız olursa ne olur?** Eşleme dosyasındaki hatalar nedeniyle içeri aktarma işi başarısız olursa, içeri aktarma işi oluşturmak için sabit sürücüyü Microsoft'a yeniden göndermeniz gerekmez. Bunun nedeni, sürücü gönderimi içeri aktarma işi için gönderdiğiniz sabit sürücüdeki PST dosyalarının kuruluşunuzun Azure Depolama alanına zaten yüklenmiş olmasıdır. Bu durumda, yalnızca PST İçeri Aktarma CSV eşleme dosyasındaki hataları düzeltmeniz ve ardından yeni bir "ağ karşıya yükleme" içeri aktarma işi oluşturmanız ve düzeltilmiş CSV eşleme dosyasını göndermeniz gerekir. Yeni bir ağ karşıya yükleme içeri aktarma işi oluşturmak ve başlatmak için bkz[. 5. Adım: Microsoft 365'te PST İçeri Aktarma işi oluşturma](use-network-upload-to-import-pst-files.md#step-5-create-a-pst-import-job) ve [6. Adım: Verileri filtreleme ve "PST](use-network-upload-to-import-pst-files.md#step-6-filter-data-and-start-the-pst-import-job) dosyalarını Office 365 aktarmak için ağ yükleme özelliğini kullanma" konusunda PST İçeri Aktarma işini başlatma. 
    
    > [!NOTE]
    > PST İçeri Aktarma CSV eşleme dosyasının sorunlarını gidermenize yardımcı olması için [, Azure Depolama Gezgini](#view-a-list-of-the-pst-files-uploaded-to-microsoft-365) aracını kullanarak Sabit sürücünüzden Azure depolama alanına yüklenen PST dosyalarının **alma verileri** kapsayıcısında klasör yapısını görüntüleyin. Eşleme dosyası hataları genellikle FilePath parametresindeki yanlış bir değerden kaynaklanıyor. Bu parametre, Bir PST dosyasının Azure depolama alanındaki konumunu belirtir. [3. Adım'daki](#step-3-create-the-pst-import-mapping-file) tablodaki FilePath parametresinin açıklamasına bakın. Daha önce açıklandığı gibi, [2. Adımda](#step-2-copy-the-pst-files-to-the-hard-drive) WAImportExport.exe aracını çalıştırdığınızda, Pst dosyalarının Azure depolama alanındaki konumu parametresi tarafından `/dstdir:` belirtildi. 
  
## <a name="more-information"></a>Daha fazla bilgi

- Sürücü gönderimi, kuruluşunuzda kullanılabilen uyumluluk özelliklerinden yararlanmak için büyük miktarlarda arşiv mesajlaşma verilerini Microsoft 365'e aktarmanın etkili bir yoludur. Arşiv verileri kullanıcı posta kutularına aktarıldıktan sonra şunları yapabilirsiniz:

  - Kullanıcılara veriler için daha fazla posta kutusu depolama alanı sağlamak için [arşiv posta kutularını](enable-archive-mailboxes.md) ve [arşivlemeyi otomatik olarak genişletmeyi](enable-autoexpanding-archiving.md) etkinleştirin. 

  - Verileri korumak için posta kutularını [Dava Tutma'ya](./create-a-litigation-hold.md) yerleştirin. 

  - Verilerde arama yapmak için Microsoft [eBulma araçlarını](search-for-content.md) kullanın. 

  - Verilerin ne kadar süreyle tutulacağını ve saklama süresi dolduktan sonra hangi eylemin yapılacağını denetlemek için [Microsoft 365 bekletme ilkeleri](retention.md) uygulayın. 

  - Denetim [günlüğünde](search-the-audit-log-in-security-and-compliance.md) bu veriyle ilgili olayları arayın. 

  - Verileri uyumluluk amacıyla arşivlerken [etkin olmayan posta kutularına](inactive-mailboxes-in-office-365.md) aktar. 

  - Kuruluşunuzu hassas bilgilerin [veri kaybına](dlp-learn-about-dlp.md) karşı koruyun. 

- Burada güvenli depolama hesabı anahtarı ve BitLocker şifreleme anahtarı örneği verilmiş. Bu örnek, PST dosyalarını sabit sürücüye kopyalamak için çalıştırdığınız WAImportExport.exe komutunun söz dizimini de içerir. Parolaları veya güvenlikle ilgili diğer bilgileri koruduğu gibi bunları korumak için önlem almayı unutmayın.

    ```text
    Secure storage account key: 

    yaNIIs9Uy5g25Yoak+LlSHfqVBGOeNwjqtBEBGqRMoidq6/e5k/VPkjOXdDIXJHxHvNoNoFH5NcVUJXHwu9ZxQ==

    BitLocker encryption key:

    397386-221353-718905-535249-156728-127017-683716-083391

  COMMAND SYNTAX

  First time:

  WAImportExport.exe PrepImport /j:<Name of journal file> /t:<Drive letter> /id:<Name of session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob /encrypt /logdir:<Log file location>

  Subsequent times:

  WAImportExport.exe PrepImport /j:<Name of journal file> /id:<Name of new session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob 

  EXAMPLES

  First time:

  WAImportExport.exe PrepImport /j:PSTHDD1.jrn /t:f /id:driveship1 /srcdir:"\\FILESERVER1\PSTs" /dstdir:"ingestiondata/"
  /blobtype:BlockBlob /encrypt /logdir:"c:\users\admin\desktop\PstImportLogs"

  Subsequent times:

  WAImportExport.exe PrepImport /j:PSTHDD1.jrn /id:driveship2 /srcdir:"\\FILESERVER1\PSTs\SecondBatch" /dstdir:"ingestiondata/" /blobtype:BlockBlob
    ```

- Daha önce açıklandığı gibi Office 365 İçeri Aktarma hizmeti, PST dosyaları bir posta kutusuna aktarıldıktan sonra bekletme saklama ayarını (süresiz olarak) açar. Bu,  *RentionHoldEnabled*  özelliğinin, posta kutusuna  `True` atanan bekletme ilkesinin işlenmemesi için olarak ayarlandığı anlamına gelir. Bu, bir silme veya arşiv ilkesinin eski iletileri silmesini veya arşivlemesini engelleyerek posta kutusu sahibine yeni içeri aktarılan iletileri yönetmesi için zaman verir. Bu bekletme saklamayı yönetmek için uygulayabileceğiniz bazı adımlar şunlardır: 

  - Belirli bir süre sonra komutunu çalıştırarak bekletme saklamayı  `Set-Mailbox -RetentionHoldEnabled $false` kapatabilirsiniz. Yönergeler için bkz [. Saklama bekletmeye posta kutusu yerleştirme](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

  - Bekletme saklamayı, gelecekte bir tarihte kapatılmış olacak şekilde yapılandırabilirsiniz. Komutunu çalıştırarak  `Set-Mailbox -EndDateForRetentionHold <date>` bunu yaparsınız. Örneğin, bugünün tarihinin 1 Haziran 2016 olduğunu ve bekletme bekletmenin 30 gün içinde kapatılmasını istediğinizi varsayarsak, şu komutu çalıştırırsınız:  `Set-Mailbox -EndDateForRetentionHold 7/1/2016`. Bu senaryoda  *RentionHoldEnabled*  özelliğini  *True* olarak bırakırsınız. Daha fazla bilgi için bkz. [Set-Mailbox](/powershell/module/exchange/set-mailbox).

  - posta kutusuna atanan bekletme ilkesinin ayarlarını değiştirebilirsiniz, böylece içeri aktarılan eski öğeler hemen silinmez veya kullanıcının arşiv posta kutusuna taşınmaz. Örneğin, posta kutusuna atanan bir silme veya arşiv ilkesi için saklama süresini uzatabilirsiniz. Bu senaryoda, bekletme ilkesinin ayarlarını değiştirdikten sonra posta kutusunda bekletmeyi kapatabilirsiniz. Daha fazla bilgi için bkz. [Kuruluşunuzdaki posta kutuları için arşiv ve silme ilkesi ayarlama](set-up-an-archive-and-deletion-policy-for-mailboxes.md).
