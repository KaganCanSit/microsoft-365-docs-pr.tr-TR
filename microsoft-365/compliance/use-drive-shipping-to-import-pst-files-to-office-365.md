---
title: Sürücü gönderimini kullanarak kuruluş pst dosyalarını içeri aktarma
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
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 40829b57-793c-4d41-b171-e9270129173d
ms.custom: seo-marvel-apr2020
description: Yönetici, sabit sürücüye PST dosyalarını kopyalayıp Microsoft'a Microsoft 365 posta kutularına PST dosyalarını toplu olarak içeri aktarmayı öğrenebilirsiniz.
ms.openlocfilehash: 2b0e6e08d6c324914aaf2fdd9ce24b9b55ca2d95
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021449"
---
# <a name="use-drive-shipping-to-import-your-organizations-pst-files"></a>Sürücü gönderimini kullanarak kuruluş pst dosyalarını içeri aktarma

**Bu makale yöneticilere aittir. PST dosyalarını kendi posta kutunuza içeri aktarmaya mı çalışıyorsunuz? Bkz [. E-postayı, kişileri ve takvimi Outlook .pst dosyasından içeri aktarma](https://go.microsoft.com/fwlink/p/?LinkID=785075)**
   
PST dosyalarını Office 365 posta kutularına toplu olarak içeri aktarma için Hızlı İçeri Aktarma hizmetini ve sürücü gönderimi seçeneğini kullanın. Sürücü gönderimi, PST dosyalarını bir sabit disk sürücüsüne kopyalayıp fiziksel olarak Sürücüyü Microsoft'a göndermeniz anlamına gelir. Microsoft sabit sürücünizi aldığında, veri merkezi personeli sabit sürücüden verileri Microsoft bulutunda bir depolama alanına kopyalar. Ardından, hangi verilerin içeri aktar alın posta kutularını kontrol etmek için filtreler ayarp hedef posta kutularına aktarılmış PST verilerini kırpma fırsatınız olur. Siz içeri aktarma işini başladıktan sonra, İçeri Aktarma hizmeti PST verilerini depolama alanında kullanıcı posta kutularına içeri aktarıyor. PST dosyalarını kullanıcı posta kutularına içeri aktarmak için sürücü gönderimini kullanmak, kurum e-postanızı başka bir Office 365.
  
PST dosyalarını posta kutularına içeri aktararak sürücü gönderimi kullanımını şu Microsoft 365 gerekir:
  
[1. Adım: PST İçeri Aktarma aracını indirme](#step-1-download-the-pst-import-tool)

[2. Adım: PST dosyalarını sabit sürücüye kopyalama](#step-2-copy-the-pst-files-to-the-hard-drive)

[3. Adım: PST İçeri Aktarma eşleme dosyasını oluşturma](#step-3-create-the-pst-import-mapping-file)

[4. Adım: Office 365'te PST İçeri Aktarma işi oluşturma](#step-4-create-a-pst-import-job-in-office-365)

[5. Adım: Sabit sürücüyü Microsoft'a sevk edin](#step-5-ship-the-hard-drive-to-microsoft)

[6. Adım: Verileri filtreleme ve PST İçeri Aktarma işini başlatma](#step-6-filter-data-and-start-the-pst-import-job)
  
> [!IMPORTANT]
> İçeri aktarma aracını indirmek için 1. Adımı bir kez gerçekleştirmeniz gerekir. Bu adımları gerçekleştirdikten sonra, sabit sürücüyü Microsoft'a her gönderebilirsiniz ve 2 ile 6. Adım arasında adımları izleyin. 
  
PST dosyalarını içeri aktarmada sürücü gönderimi kullanma hakkında sık sorulan Office 365, PST dosyalarını içeri aktarmada sürücü gönderimi kullanımıyla ilgili [SSS'ler'e bakın](./faqimporting-pst-files-to-office-365.yml#using-drive-shipping-to-import-pst-files). 
  
## <a name="before-you-import-pst-files"></a>PST dosyalarını içeri aktarmadan önce

- Posta Kutusunda içeri aktarma işleri oluşturmak ve PST dosyalarını kullanıcı posta kutularına içeri Exchange Online için Microsoft 365 uyumluluk merkezi Kutusu İçeri/Dışarı Aktarma rolüne atanmışsınız. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü Kuruluş Yönetimi rol grubuna  eklersiniz. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve ardından kendinizi üye olarak  eklersiniz. Daha fazla bilgi için Rol gruplarını yönetme'de "Bir rol grubuna rol ekleme" veya "Rol grubu oluşturma" [bölümlerine bakın](/Exchange/permissions-exo/role-groups).

    Posta Kutusu İçeri/Dışarı Aktarma rolüne ek olarak, bu rolde posta kutusunda Posta Alıcıları rolüne de Exchange Online. Varsayılan olarak bu rol, aynı gruptaki Kuruluş Yönetimi ve Alıcı Yönetimi rol gruplarına Exchange Online.

    > [!TIP]
    > Pst dosyalarını diğer kullanıcılara Exchange Online özel olarak tasarlanmış yeni bir rol grubu oluşturmayı Office 365. PST dosyalarını içeri aktarmanız için gereken minimum düzeydeki ayrıcalıklar için Posta Kutusunu İçeri/Dışarı Aktar ve Posta Alıcıları rollerini yeni rol grubuna atayın ve ardından üyeleri ekleyin.
  
- Sabit sürücüye kopyalamak istediğiniz PST dosyalarını, dosya sunucusunda veya kurumda paylaşılan klasörde depolamanız gerekir. 2. Adımda, bu dosya sunucusunda veya paylaşılan klasörde depolanan PST dosyalarının sabit sürücüye kopyalandığı Azure İçeri Aktarma Aracı'nı (WAImportExport.exe) çalıştırın.

- Büyük PST dosyaları PST içeri aktarma işleminin performansını etkileyebilir. Bu nedenle, 2. Adımda sabit sürücüye kopyalayıp her PST dosyasının 20 GB'den büyük olmadığını öneririz.

- Office 365 İçeri Aktarma hizmeti için yalnızca 2,5 inç katı hal sürücülerin (CD'ler) ya da 2,5 inç veya 3,5 inç SATA II/III dahili sabit sürücülerin kullanımı desteklemektedir. 10 TB'a kadar sabit sürücü kullanabilirsiniz. İçeri aktarma işlerinde, yalnızca sabit sürücüde ilk veri birimi işlenir. Veri biriminin NTFS ile biçimlendirilmiş olması gerekir. Sabit sürücüye veri kopyalayıp, bunu 2,5 inç SSD veya 2,5 inç ya da 3,5 inç SATA II/III bağlayıcı kullanarak doğrudan iliştirebilirsiniz veya harici 2,5 inç SSD veya 2,5 inç ya da 3,5 inç SATA II/III USB bağdaştırıcısı kullanarak dışarıdan da iliştirebilirsiniz.
    
    > [!IMPORTANT]
    > Yerleşik USB bağdaştırıcısı olan harici sabit sürücüler, USB İçeri Aktarma hizmeti Office 365 desteklemez. Ayrıca, bir harici sabit sürücü kasa içindeki disk de kullanılamaz. Lütfen harici sabit sürücüleri sevk etme. 
  
- PST dosyalarını kopyalayıp sabit sürücü bitLocker ile şifrelenmeleri gerekir. 2WAImportExport.exe de çalıştıracak tüm araç bitLocker'ı ayarlamanıza yardımcı olur. Ayrıca, Microsoft veri merkezi personelinin PST dosyalarını Microsoft bulut'un Azure Depolama alanına yüklemek üzere sürücüye erişmek için kullanabileceği bir BitLocker şifreleme anahtarı oluşturulur.
    
- Sürücü gönderimi bir Microsoft Kurumsal Anlaşma (EA) aracılığıyla kullanılabilir. Sürücü gönderimi, bir Microsoft Ürün ve Hizmet Sözleşmesi (MPSA) ile kullanılamaz.
    
- PST dosyalarını Microsoft 365 posta kutularına sürücü gönderimi kullanarak aktarmanın maliyeti 1 GB veri başına 2 USD’dir. Örneğin, 1.000 GB (1 TB) PST dosyası içeren bir sabit sürücüyü sevk maliyeti 2.000 Amerikan Dolarıdır. İçeri aktarma ücretini ödemek için bir iş ortağıyla çalışabilirsiniz. İş ortağı bulma hakkında daha fazla bilgi için bkz [. Microsoft iş ortağınızı veya satıcınızı bulma](../admin/manage/find-your-partner-or-reseller.md).
    
- Sizin veya kuruluşta FedEx veya DHL hesabı olması gerekir.
    
  - Amerika Birleşik Devletleri, Brezilya ve Avrupa'daki kuruluşların FedEx hesapları olması gerekir.
    
  - Doğu Asya, Güneydoğu Asya, Japonya, Kore Cumhuriyeti ve Avustralya'daki kuruluşların DHL hesapları olması gerekir.
    
    Microsoft, sabit sürücüyü size geri iade etmek için bu hesabı kullanır (ve ücretler).
    
- Microsoft'a sevk etmek için sabit sürücü, uluslararası sınırların arasında olabilir. Bu durumda, sabit sürücü ve içerdiği verilerin ilgili yasalara uygun şekilde içe ve/veya dışarı aktarılmış olmasını sağlamak sizin sorumluluğundadır. Sabit sürücü göndermeden önce, sürücü ve verilerinizin yasal olarak tanımlanan Microsoft veri merkezine gönderilebilir olduğunu doğrulamak için danışmanlarınıza danışmanız gerekir. Bu, microsoft'a zamanında ulaşmasına yardımcı olur.
    
- Bu yordam bir BitLocker şifreleme anahtarını kopyalama ve kaydetmeyi içerir. Parolaları veya güvenlikle ilgili diğer bilgileri korur gibi bu anahtarları korumak için önlemler almaya devam edin. Örneğin, bunları bir parola korumalı belgeye veya Microsoft Word şifreli bir USB sürücüsüne kaydedebilirsiniz. Bu [anahtarlar örneği için](#more-information) Daha fazla bilgi bölümüne bakın. 
    
- PST dosyaları bir posta Microsoft 365 aktarıldıktan sonra, posta kutusunun bekletme ayarı süresiz olarak açık olur. Bu, siz bekletmeyi kapatana veya bekletmeyi kapatacak bir tarih ayarlamadan posta kutusuna atanan bekletme ilkesi işlenmez. Bunu neden yapacağız? Posta kutusuna aktarılan iletiler eskise, posta kutusu için yapılandırılan bekletme ayarlarına göre bekletme sürelerinin süresi sona ermiş olduğundan bunlar kalıcı olarak silinebilir (temiz kullanılabilir). Posta kutusunun bekletmeye yerleştirilmesi, posta kutusu sahibinin bu yeni aktarılan iletileri yönetmesi için zaman verir veya posta kutusunun bekletme ayarlarını değiştirmek için size zaman verir. Bekletmeyi [yönetme hakkında](#more-information) öneriler için Daha fazla bilgi bölümüne bakın. 
    
- Varsayılan olarak, bir posta kutusu tarafından alın en büyük ileti Microsoft 365 35 MB'dir. Bunun nedeni, posta kutusunun  *MaxReceiveSize*  özelliğinin varsayılan değeri 35 MB olarak ayarlanmıştır. Bununla birlikte, en büyük ileti alma boyutu sınırı Microsoft 365 150 MB'dir. Dolayısıyla, 35 MB'den büyük bir öğe içeren bir PST dosyasını içeri aktarıyorsanız Office 365 İçeri Aktarma hizmeti, hedef posta kutusunda *MaxReceiveSize* özelliğinin değerini otomatik olarak 150 MB olarak değiştiririz. Bu, 150 MB'a kadar olan iletilerin kullanıcı posta kutularına aktarılmaz. 
    
    > [!TIP]
    > Bir posta kutusunun ileti alma boyutunu belirlemek için bu komutu PowerShell Exchange Online çalıştırabilirsiniz: `Get-Mailbox <user mailbox> | FL MaxReceiveSize`. 
  
- PST dosyalarını, başka bir Office 365'te etkin olmayan bir posta kutusuna aktarabilirsiniz. Bunu yapmak için, PST İçeri Aktarma eşleme dosyasındaki parametrede etkin  `Mailbox` olmayan posta kutusunun GUID'sini belirtirsiniz. Daha [fazla bilgi için bkz. 3. Adım: PST İçeri Aktarma eşleme](#step-3-create-the-pst-import-mapping-file) dosyasını oluşturma. 
    
- Karma Exchange dağıtımda, birincil posta kutusu şirket içinde olan bir kullanıcı için PST dosyalarını bulut tabanlı bir arşiv posta kutusuna aktarabilirsiniz. Bunu yapmak için PST İçeri Aktarma eşleme dosyasında şunları yapın:
    
  - Parametrede kullanıcının şirket içi posta kutusunun e-posta adresini  `Mailbox` belirtin. 
    
  - Parametrede **DOĞRU** değerini  `IsArchive` belirtin. 
    
    Daha [fazla bilgi için bkz. 3. Adım: PST İçeri Aktarma eşleme](#step-3-create-the-pst-import-mapping-file) dosyasını oluşturma. 

## <a name="step-1-download-the-pst-import-tool"></a>1. Adım: PST İçeri Aktarma aracını indirme

İlk adım, aracı indirmek ve 2. Adımda PST dosyalarını sabit sürücüye kopyalamak için kullanmaktır.
  
> [!IMPORTANT]
> Sürücü gönderimi yöntemini kullanarak PST dosyalarını başarıyla içeri aktar almak için Azure İçeri/Dışarı Aktarma araç sürümü 1 (WAimportExportV1) kullanasınız. Azure İçeri/Dışarı Aktarma aracının 2. sürümü desteklenmiyor ve bu araç yanlış biçimde içeri aktarma işi için sabit sürücüye hazırlanıyor. Bu adımda, yordamları Microsoft 365 uyumluluk merkezi Azure İçeri/Dışarı Aktarma aracını ilk indirmeyi deneyin. 
  
1. <https://compliance.microsoft.com> Gidip, kurumda yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. Gezinti bölmesinin sol bölmesinde, Microsoft 365 uyumluluk merkezi yönetimi İçeri **Aktar'a** \> **tıklayın**.
    
    > [!NOTE]
    > Daha önce de belirtildiği gibi, çalışma sayfasındaki İçeri Aktar sayfasına erişmek **için uygun** izinlerin atan Microsoft 365 uyumluluk merkezi. 
  
3. İçeri Aktar **sekmesinde** Simge Ekle'ye ![tıklayın.](../media/ITPro-EAC-AddIcon.gif) **Yeni içeri aktarma işi**.
    
4. İş içeri aktarma sihirbazında, PST içeri aktarma işi için bir ad yazın ve Ardından Sonraki'ye **tıklayın**. Küçük harf, sayı, kısa çizgi ve alt çizgi kullanın. Büyük harf kullanamaz veya adlarında boşluk ekemezsiniz.
    
5. İçeri aktarma **iş türünü seçin sayfasında** Sabit sürücüleri fiziksel konumlarımıza gönder'e tıklayın ve **sonra da Sonraki'ye** **tıklayın**.
    
    ![Sürücü gönderimi içeri aktarma işi oluşturmak için Sabit sürücüleri fiziksel konumlarımıza gönder'e tıklayın.](../media/1584fdc5-cd4c-4e47-932e-db6c8e07f5f8.png)
  
6. Veri **içeri aktar** sayfasında şunları yapın:     
    
    **Azure İçeri/Dışarı Aktarma (sürüm** 1) aracını indirip İçeri/Dışarı Aktarma için Azure İçeri/Dışarı Aktarma aracını indirin.
    
    - Açılan pencerede, farklı kaydet'e  \> tıklayın ve WaImportExportV1.zip yerel bilgisayarınıza bir klasöre kaydedin. 
    
    - WaImportExportV1.zip ayıkla.
    
7. **İptal'e** tıklar ve sihirbazı kapatır. 
    
    4. Adımda **içeri aktarma** işini Microsoft 365 uyumluluk merkezi Içeri Aktar sayfasına dönersiniz. 

## <a name="step-2-copy-the-pst-files-to-the-hard-drive"></a>2. Adım: PST dosyalarını sabit sürücüye kopyalama

Sonraki adım, PST dosyalarını WAImportExport.exe sürücüye kopyalamak için Sabit Sürücü aracını kullanmaktır. Bu araç sabit sürücüyü BitLocker ile şifreler, PST'leri sabit sürücüye kopyalar ve kopyalama işlemiyle ilgili bilgileri depolar bir günlük dosyası oluşturur. Bu adımı tamamlamak için PST dosyalarının, kurumda bir dosya paylaşımında veya dosya sunucusunda yer alıyor olması gerekir. Bu, aşağıdaki yordamda kaynak dizin olarak bilinir. 

 Daha önce de belirtildiği gibi, sabit sürücüye kopyalayıp her PST dosyasının 20 GB'den büyük olması gerekir. 20 GB'tan büyük PST dosyaları, 6. Adım'da başlatan PST içeri aktarma işleminin performansını etkileyebilir.
  
> [!IMPORTANT]
> Sabit sürücü için WAImportExport.exe kez çalıştır kullandıktan sonra, bundan sonra her zaman farklı bir söz dizimi kullan gerekir. Bu söz dizimi, PST dosyalarını sabit sürücüye kopyalamak için bu yordamın 4. adımda açıklanmıştır. 
  
1. Yerel bilgisayarınızda Komut İstemi'ne açın.
    
    > [!TIP]
    > Komut istemini yönetici olarak çalıştırmanız (bunu ataştırken "Yönetici olarak çalıştır"ı seçerek) hata iletileri komut istemi penceresinde görüntülenir. Bu, Uygulama Aracı'nı çalıştırmayla ilgili WAImportExport.exe yardımcı olabilir. 
  
2. 1. Adımda Dosya Aracını WAImportExport.exe dizine gidin.
    
3. PST dosyalarını sabit sürücüye kopyalamak için dosya WAImportExport.exe aşağıdaki komutu çalıştırın.

    ```powershell
    WAImportExport.exe PrepImport /j:<Name of journal file> /t:<Drive letter> /id:<Name of session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob /encrypt /logdir:<Log file location>
    ```

    Aşağıdaki tabloda parametreler ve bunların gerekli değerleri açık almaktadır.
    
    |**Parametre**|**Açıklama**|**Örnek**|
    |:-----|:-----|:-----|
    | `/j:` <br/> |Günlük dosyasının adını belirtir. Bu dosya, Dosya Aracının bulunduğu WAImportExport.exe kaydedilir. Microsoft'a gönder her sabit sürücüde bir günlük dosyası bulunarak gönderebilirsiniz. PST dosyalarını bir WAImportTool.exe sürücüye kopyalamak için bu dosyayı her çalıştırsanız, bilgiler bu sürücüye ilişkin günlük dosyasına eklenir.  <br/> Microsoft veri merkezi personeli günlük dosyasındaki bilgileri kullanarak sabit sürücüyü 4. Adımda oluşturmakta istediğiniz içeri aktarma işiyle ilişkilendirmek ve PST dosyalarını Microsoft bulutunda Azure Depolama alanına yüklemek için kullanır.  <br/> | `/j:PSTHDD1.jrn` <br/> |
    | `/t:` <br/> |Sabit sürücü yerel bilgisayarınıza bağlıyken sürücü harfini belirtir.  <br/> | `/t:h` <br/> |
    | `/id:` <br/> |Kopya oturumunun adını belirtir. Dosyaları sabit sürücüye kopyalamak için dosya aracını her WAImportExport.exe bir oturum tanımlanır. PST dosyaları, bu parametre tarafından belirtilen oturum adı ile adlandırılmış bir klasöre kopyalanır.  <br/> | `/id:driveship1` <br/> |
    | `/srcdir:` <br/> |Oturum sırasında kopyalanan PST dosyalarını içeren, kuruluşta kaynak dizini belirtir. Bu parametrenin değerini çift tırnak işaretleri (" ") içine almanız gerekir.  <br/> | `/srcdir:"\\FILESERVER01\PSTs"` <br/> |
    | `/dstdir:` <br/> |MICROSOFT bulutun PSTS'lerin Depolama Azure Etki Alanı'nın hedef dizinini belirtir. değerini kullan gerekir  `ingestiondata/`. Bu parametrenin değerini çift tırnak işaretleri (" ") içine almanız gerekir.  <br/> İsteğe bağlı olarak, bu parametrenin değerine fazladan bir dosya yolu da  eklersiniz. Örneğin, sabit sürücüde kaynak dizininin dosya yolunu (URL biçimine dönüştürülür) kullanabilirsiniz ve bu parametrede belirtilir  `/srcdir:` . Örneğin,  `\\FILESERVER01\PSTs` olarak değiştirilir  `FILESERVER01/PSTs`. Bu durumda, dosya yolunu yine  `ingestiondata` de dahil etmek gerekir. Bu örnekte, parametrenin `/dstdir:` değeri .`"ingestiondata/FILESERVER01/PSTs"`  <br/> Ek dosya yolunu eklemenin bir nedeni, aynı dosya adı olan PSTS dosyalarınız olmasıdır.  <br/> > [!NOTE]> İsteğe bağlı yol adını dahil ediyorsanız, PST dosyasının Azure Depolama alanına yüklendikten sonra ad alanı PST dosyasının adını ve adını içerir; örneğin, `FILESERVER01/PSTs/annb.pst`. Yol adı yoksa, ad alanı yalnızca PST dosya adıdır;  `annb.pst`örneğin.           | `/dstdir:"ingestiondata/"` <br/> Veya  <br/>  `/dstdir:"ingestiondata/FILESERVER01/PSTs"` <br/> |
    | `/blobtype:` <br/> |PST dosyalarını içeri aktarın Azure Depolama alanında blobların türünü belirtir. PST dosyalarını içeri aktarma işlemi için **BlockBlob değerini kullanın**. Bu parametre gereklidir.   <br/> | `/blobtype:BlockBlob` <br/> |
    | `/encrypt` <br/> |Bu anahtar, sabit sürücü için BitLocker'ı etkinleştirir. Bu parametre, bu parametreyi ilk kez WAImportExport.exe gerekir.  <br/> BitLocker şifreleme anahtarı günlük dosyasına ve parametreyi kullanırsanız oluşturulan günlük dosyasına kopyalanır  `/logfile:` . Daha önce de belirtildiği gibi, günlük dosyası dosya dosyanın WAImportExport.exe kaydedilir.  <br/> | `/encrypt` <br/> |
    | `/logdir:` <br/> |Bu isteğe bağlı parametre, günlük dosyalarının kaydedl olduğu klasörü belirtir. Belirtilmezse, günlük dosyaları dosya aracının bulunduğu WAImportExport.exe kaydedilir. Bu parametrenin değerini çift tırnak işaretleri (" ") içine almanız gerekir.  <br/> | `/logdir:"c:\users\admin\desktop\PstImportLogs"` <br/> |
   
    Her parametre için gerçek değerleri kullanan WAImportExport.exe söz dizimi örneği:
    
    ```powershell
    WAImportExport.exe PrepImport /j:PSTHDD1.jrn /t:f /id:driveship1 /srcdir:"\\FILESERVER01\PSTs" /dstdir:"ingestiondata/" blobtype:BlockBlob /encrypt /logdir:"c:\users\admin\desktop\PstImportLogs"
    ```

    Komutu çalıştırdikten sonra, PST dosyalarını sabit sürücüye kopyalama ilerleme durumunun görüntülendiğinde durum iletileri görüntülenir. Son durum iletisi başarıyla kopyalanan dosyaların toplam sayısını gösterir.
    
4. PST dosyalarını aynı sabit sürücüye kopyalamak için WAImportExport.ext aracını her tekrar çalıştıracak şekilde bu komutu çalıştırın.

    ```powershell
    WAImportExport.exe PrepImport /j:<Name of journal file> /id:<Name of new session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob 
    ```

    PST dosyalarını aynı sabit sürücüye kopyalamak için sonraki oturumları çalıştırma söz dizimi örneği.

    ```powershell
    WAImportExport.exe PrepImport /j:PSTHDD1.jrn /id:driveship2 /srcdir:"\\FILESERVER01\PSTs\SecondBatch" /dstdir:"ingestiondata/" /blobtype:BlockBlob
    ```

## <a name="step-3-create-the-pst-import-mapping-file"></a>3. Adım: PST İçeri Aktarma eşleme dosyasını oluşturma

Microsoft veri merkezi personeli PST dosyalarını sabit sürücüden Azure Depolama alanına yükledikten sonra, İçeri Aktarma hizmeti PST dosyalarının hangi kullanıcı posta kutularına aktarılasını belirten virgülle ayrılmış değer (CSV) dosyası olan PST İçeri Aktarma eşleme dosyasındaki bilgileri kullanır. BIR PST İçeri Aktarma işi  oluşturmanın sonraki adımında bu CSV dosyasını gönderebilirsiniz.
  
1. [PST İçeri Aktarma eşleme dosyasının bir kopyasını indirin](https://go.microsoft.com/fwlink/p/?LinkId=544717).
    
2. CSV dosyasını yerel bilgisayarınıza açın veya kaydedin. Aşağıdaki örnekte tamamlanmış bir PST İçeri Aktarma eşleme dosyası (Not Defteri'de açılır) gösterir. CSV dosyasını düzenlemek için Microsoft Excel çok daha kolay.

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

    CSV dosyasının ilk satırı veya üst bilgi satırı, PST dosyalarını kullanıcı posta kutularına içeri aktarmada PST İçeri Aktarma hizmeti tarafından kullanılacak parametreleri listeler. Her parametre adı virgülle ayrılmıştır. Üst bilgi satırın altındaki her satır, PST dosyasını belirli bir posta kutusuna içeri aktarmaya yönelik parametre değerlerini temsil eder. Sabit sürücüye kopyalanan her PST dosyası için bir satıra ihtiyacınız vardır. Eşleme dosyasındaki yer tutucu verilerini gerçek verilerinizle değiştir mutlaka.

    > [!NOTE]
    > Üst bilgi satırındaki üst bilgi ve alt SharePoint, PST İçeri Aktarma işlemi sırasında yok sayılacaktır. 
  
3. CSV dosyasını gerekli bilgilerle doldurmak için aşağıdaki tabloda yer alan bilgileri kullanın.
    
    |**Parametre**|**Açıklama**|**Örnek**|
    |:-----|:-----|:-----|
    | `Workload` <br/> |Verilerin aktaracağız hizmeti belirtir. PST dosyalarını kullanıcı posta kutularına içeri aktarma için, ' kullanın  `Exchange`.  <br/> | `Exchange` <br/> |
    | `FilePath` <br/> | Sabit sürücü Microsoft'a Depolama PST dosyalarının kopyalanır, Azure Veri Alanı'nın klasör konumunu belirtir.  <br/>  CSV dosyasında bu sütuna ne ekley istediğiniz, önceki adımda parametre için  `/dstdir:` ne belirttiğinize bağlıdır. Kaynak konumda alt klasörünüz varsa, `FilePath` parametredeki değer alt klasörün göreli yolunu (örneğin, /klasör1/kullanıcı1/ ) içermesi gerekir.  <br/>  kullandıysanız  `/dstdir:"ingestiondata/"`, CSV dosyasında bu parametreyi boş bırakın.  <br/>  Parametrenin değeri için isteğe  `/dstdir:` bağlı bir yol adı kullandıysanız (örneğin,  `/dstdir:"ingestiondata/FILESERVER01/PSTs"`CSV dosyasında bu parametre için bu yol adını ("ingestiondata" dahil değildir) kullanın. Bu parametrenin değeri büyük/harfe duyarlıdır.  <br/>  Her iki  *şekilde de parametrenin*  değerine "ingestiondata" dahil  `FilePath` etme. Bu parametreyi boş bırakın veya yalnızca isteğe bağlı yol adını belirtin.  <br/> > [!IMPORTANT]> Dosya yolu adının durumu, önceki adımda parametrede  `/dstdir:` belirttiğiniz harfle aynı olmalıdır. Örneğin, önceki adımda  `"ingestiondata/FILESERVER01/PSTs"` alt klasör adı için kullandınız ancak  `fileserver01/psts`  `FilePath` daha sonra CSV dosyasındaki parametrede kullandınız, PST dosyası için içeri aktarma işlemi başarısız olur. Her iki durumda da aynı vakayı kullanmaya emin olun.           |(boş bırakın)  <br/> Veya  <br/>  `FILESERVER01/PSTs` <br/> |
    | `Name` <br/> |Kullanıcı posta kutusuna aktaracak PST dosyasının adını belirtir. Bu parametrenin değeri büyük/harfe duyarlıdır.  <br/> > [!IMPORTANT]> CSV dosyasındaki PST dosya adının durumu, 2. Adım'daki Azure Depolama konuma yüklenen PST dosyasıyla aynı olması gerekir. Örneğin, CSV dosyasındaki parametrede  `annb.pst`  `Name` kullanırsanız, ancak gerçek PST dosyasının adı aşağıdaki gibi olursa, bu PST  `AnnB.pst`dosyası için içeri aktarma işlemi başarısız olur. CSV dosyasındaki PST adının gerçek PST dosyasıyla aynı vakayı kullandığından emin olun.           | `annb.pst` <br/> |
    | `Mailbox` <br/> |PST dosyasının içeri aktarılmaz olduğu posta kutusunun e-posta adresini belirtir. PST İçeri Aktarma Hizmeti PST dosyalarını ortak klasörlere içeri aktarmayı desteklemez, çünkü ortak klasör belirtemezseniz.  <br/> PST dosyasını etkin olmayan bir posta kutusuna içeri aktarmak için, bu parametrenin posta kutusu GUID'ını belirtmeniz gerekir. Bu GUID'i almak için, Guid'te aşağıdaki PowerShell Exchange Online:`Get-Mailbox <identity of inactive mailbox> -InactiveMailboxOnly | FL Guid` <br/> > [!NOTE]> Bazen, aynı e-posta adresine sahip birden çok posta kutunuz olabilir; burada bir posta kutusu etkin bir posta kutusu ve diğer posta kutusu da yumuşak silinmiş (veya etkin olmayan) durumdadır. Bu gibi durumlarda, PST dosyasını içeri aktarın posta kutusunu benzersiz bir şekilde tanımlamak için posta kutusu GUID'ını belirtmeniz gerekir. Etkin posta kutuları için bu GUID'i almak için aşağıdaki PowerShell komutunu çalıştırın:  `Get-Mailbox <identity of active mailbox> | FL Guid`. Yumuşak silinmiş (veya etkin olmayan) posta kutularının GUID'sini almak için şu komutu çalıştırın:  `Get-Mailbox <identity of soft-deleted or inactive mailbox> -SoftDeletedMailbox | FL Guid`.           | `annb@contoso.onmicrosoft.com` <br/> Veya  <br/>  `2d7a87fe-d6a2-40cc-8aff-1ebea80d4ae7` <br/> |
    | `IsArchive` <br/> | PST dosyasının kullanıcının arşiv posta kutusuna aktarıp aktarılamayında bir değer belirtir. İki seçenek vardır:  <br/> **YANLIŞ** PST dosyası kullanıcının birincil posta kutusuna içeri aktarır.  <br/> **TRUE** PST dosyası kullanıcının arşiv posta kutusuna içeri aktarır. Burada, kullanıcının arşiv [posta kutusunun etkinleştirilmiştir](enable-archive-mailboxes.md). Bu parametreyi olarak ayarlasanız  `TRUE` ve kullanıcının arşiv posta kutusu etkinleştirilmediyse, bu kullanıcıya yapılan içeri aktarma işlemi başarısız olur. Bir kullanıcı için içeri aktarma işlemi başarısız olursa (  `TRUE`arşivi etkin değilse ve bu özellik olarak ayarlanmışsa), içeri aktarma işinden diğer kullanıcılar etkilenmez.  <br/>  Bu parametreyi boş bırakırsanız, PST dosyası kullanıcının birincil posta kutusuna aktarılır.  <br/> **Not:** Birincil posta kutusu şirket içinde olan bir kullanıcının PST dosyasını bulut tabanlı bir arşiv posta kutusuna içeri aktarmanız için,  `TRUE`  `Mailbox` bu parametreyi belirtmeniz ve parametrenin kullanıcının şirket içi posta kutusunun e-posta adresini belirtmeniz gerekir.  <br/> | `FALSE` <br/> Veya  <br/>  `TRUE` <br/> |
    | `TargetRootFolder` <br/> | PST dosyasının içeri aktar olduğu posta kutusu klasörünü belirtir.  <br/>  Bu parametreyi boş bırakırsanız, PST posta kutusunun kök düzeyinde (Gelen Kutusu klasörü ve  diğer varsayılan posta kutusu klasörleriyle aynı düzeyde) bulunan Alınan adlı yeni bir klasöre aktarılır.  <br/>  belirtirsiniz  `/`, PST dosyasındaki öğeler doğrudan kullanıcının Gelen Kutusu klasörüne içeri aktarılır.  <br/>  belirtirsiniz  `/<foldername>`, PST dosyasındaki öğeler adlı bir klasöre aktarılır  *\<foldername\>*. Örneğin, kullanırsanız,  `/ImportedPst`öğeler **importedPst adlı bir klasöre aktarılmış olabilir**. Bu klasör, kullanıcının posta kutusunda Gelen Kutusu klasörüyle aynı düzeyde bulunur.  <br/> |(boş bırakın)  <br/> Veya  <br/>  `/` <br/> Veya  <br/>  `/ImportedPst` <br/> |
    | `ContentCodePage` <br/> |Bu isteğe bağlı parametre, ANSI dosya biçiminde PST dosyalarını içeri aktarmada kullanılan kod sayfası için sayısal bir değer belirtir. Bu diller normalde karakter kodlaması için çift bayt karakter kümesi (DBCS) kullandığından, bu parametre Çince, Japonca ve Korece (CJK) kuruluşlarından PST dosyalarını içeri aktarmada kullanılır. Posta kutusu klasör adları olarak DBCS kullanan dillerin PST dosyalarını içeri aktarmada bu parametre kullanılmazsa, klasör adları içeri aktarıldıktan sonra çoğunlukla bozuk olur.  <br/> Bu parametrede kullanmak üzere desteklenen değerlerin listesi için bkz. [Kod Sayfası Tanımlayıcıları](/windows/win32/intl/code-page-identifiers).  <br/> > [!NOTE]> belirtildiği gibi, bu isteğe bağlı bir parametredir ve bunu CSV dosyasına eklemek zorunda değildir. Veya bu değeri dahil etmek ve bir veya birden çok satır için değeri boş bırakabilirsiniz.           |(boş bırakın)  <br/> Veya  <br/>  `932` (ANSI/OEM Japonca için kod sayfası tanımlayıcısıdır)  <br/> |
    | `SPFileContainer` <br/> |PST İçeri Aktarma için, bu parametreyi boş bırakın.  <br/> |Uygulanamaz  <br/> |
    | `SPManifestContainer` <br/> |PST İçeri Aktarma için, bu parametreyi boş bırakın.  <br/> |Geçerli değil  <br/> |
    | `SPSiteUrl` <br/> |PST İçeri Aktarma için, bu parametreyi boş bırakın.  <br/> |Uygulanamaz  <br/> |

## <a name="step-4-create-a-pst-import-job-in-office-365"></a>4. Adım: Office 365'te PST İçeri Aktarma işi oluşturma

Sonraki adım, bu hizmetin içeri aktarma hizmetsinde PST İçeri Aktarma işini Office 365. Daha önce de belirtildiği gibi, 3. Adımda oluşturduğunuz PST İçeri Aktarma eşleme dosyasını gönderin. Siz işi oluşturduktan sonra, İçeri Aktarma hizmeti eşleme dosyasındaki bilgileri kullanarak PST dosyaları sabit sürücüden Azure Depolama alanına kopyalanır ve içeri aktarma işini ayarlarsınız.
  
1. <https://compliance.microsoft.com> Gidip, kurumda yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. Gezinti bölmesinin sol bölmesinde, Microsoft 365 uyumluluk merkezi yönetimi İçeri **Aktar'a** \> **tıklayın**.

3. İçeri Aktar **sekmesinde** Simge Ekle'ye ![tıklayın.](../media/ITPro-EAC-AddIcon.gif) **Yeni içeri aktarma işi**.

    > [!NOTE]
    > Daha önce de belirtildiği gibi, çalışma sayfasındaki İçeri Aktar sayfasına erişmek **için uygun** izinlerin atan Microsoft 365 uyumluluk merkezi.
  
4. PST içeri aktarma işi için bir ad yazın ve ardından Sonraki'ye **tıklayın**. Küçük harf, sayı, kısa çizgi ve alt çizgi kullanın. Büyük harf kullanamaz veya adlarında boşluk ekemezsiniz.

5. İçeri aktarma **iş türünü seçin sayfasında** Sabit sürücüleri fiziksel konumlarımıza gönder'e tıklayın ve **sonra da Sonraki'ye** **tıklayın**.
  
6. 6. adımda, Sabit sürücülerimi hazırdim **ve** gerekli sürücü günlüğü dosyalarına erişimim var, eşleme dosyası onay kutularına  erişimim var onay kutularına tıklayın ve sonra da Sonraki'ye **tıklayın**.

    ![6. adımda iki onay kutusunu tıklatın.](../media/fad43078-ea68-4acd-b2ed-75a800183262.png)
  
7. Sürücü **dosyasını seçin sayfasında** , Sürücü dosyasını **seç'e** tıklayın ve araç dosyasının bulunduğu WAImportExport.exe gidin. 2. Adımda oluşturulan günlük dosyası bu klasöre kopyalandı.

    ![Sürücü dosyasını seç'e tıklarsanız, sürücü dosyasını ilk WAImportExport.exe.](../media/1ea35c04-bd88-4d7e-b7d9-dc390149d94f.png)
  
8. Günlük dosyasını seçin; örneğin, `PSTHDD1.jrn`.

    > [!TIP]
    > 2. adımda WAImportExport.exe aracına bakarak günlük dosyasının adı parametreyle belirtilmişti  `/j:` .
  
9. Sürücü dosyasının adı Drive dosyası adı altında göründüğünde, **sürücü** dosyanızı hatalı **olarak görmek** için Doğrula'ya tıklayın.

    ![Seçtiğiniz sürücü dosyasını doğrulamak için Doğrula'ya tıklayın.](../media/4b707f5a-152a-4e74-b9f5-449c88d1fec4.png)
  
    PST İçeri Aktarma işi oluşturmak için sürücü dosyasının başarıyla doğrulanması gerekir. Dosya adı, başarıyla doğrulandıktan sonra yeşil olarak değiştirilir. Doğrulama başarısız olursa, Günlüğü görüntüle **bağlantısını** tıklatın. Doğrulama hatası raporu açılır ve dosyanın neden başarısız olduğuyla ilgili bilgiyle bir hata iletisi yer alır. 

    > [!NOTE]
    > Microsoft'a sevk ettiyniz her sabit sürücü için bir günlük dosyası eklemeli ve doğrulamanız gerekir. 
  
10. Microsoft'a sevk ettiysiniz her sabit sürücü için bir günlük dosyası ekledikten ve doğruladikten sonra, Sonraki'ye **tıklayın**.
    
11. Simge Ekle'ye ![tıklayın.](../media/ITPro-EAC-AddIcon.gif) 3 **.** Adımda oluşturduğunuz PST İçeri Aktarma eşleme dosyasını göndermek için eşleme dosyasını seçin. 

    ![İçeri aktarma işi için oluşturduğunuz CSV dosyasını göndermek için Eşleme dosyası seç'e tıklayın.](../media/d30b1d73-80bb-491e-a642-a21673d06889.png)
  
12. CSV dosyasının adı Dosya adı eşleme **altında göründüğünde,** CSV dosyanızı hatalı **olarak görmek** için Doğrula'ya tıklayın. 

    ![CSV dosyasındaki hataları kontrol etmek için Doğrula'ya tıklayın.](../media/4680999d-5538-4059-b878-2736a5445037.png)
  
    PST İçeri Aktarma işi oluşturmak için CSV dosyasının başarıyla doğrulanması gerekir. Dosya adı, başarıyla doğrulandıktan sonra yeşil olarak değiştirilir. Doğrulama başarısız olursa, Günlüğü görüntüle **bağlantısını** tıklatın. Dosyadaki başarısız olan her satır için bir hata iletisiyle birlikte bir doğrulama hatası raporu açılır. 

13. PST eşleme dosyası başarıyla doğrulandıktan sonra, Sonraki'ne **tıklayın**.

14. Kişi **bilgilerini sağla** sayfasında, ilgili kutulara iletişim bilginizi yazın. 

    Sabit sürücülerinizi sevk etmek istediğiniz Microsoft konumunun adresi görüntülenir. Bu adres, Microsoft veri merkezi konumunuz temel alarak otomatik olarak oluşturulur. Bu adresi bir dosyaya kopyalayın veya ekran görüntüsü alın.

15. Hüküm ve koşullar belgesini okuyun, onay kutusuna tıklayın ve sonra içeri aktarma işini göndermek **için Kaydet'e** tıklayın. 

    İçeri aktarma işi başarıyla oluşturulduğunda, sürücü gönderim işleminin sonraki adımlarını açıklayan bir durum sayfası görüntülenir.

16. İçeri Aktar **sekmesinde** Yenile simgesine ![tıklayın.](../media/O365-MDM-Policy-RefreshIcon.gif) **Yeni** sürücü gönderimi içeri aktarma işi, içeri aktarma işleri listesinde görüntülenecek şekilde yenilenir. Durum, numarayı izleme için **bekliyor olarak ayarlanır**. ayrıca, içeri aktarma işi hakkında daha ayrıntılı bilgiler içeren durum sayfası görüntülemek için içeri aktarma işini de tıkleyebilirsiniz.

## <a name="step-5-ship-the-hard-drive-to-microsoft"></a>5. Adım: Sabit sürücüyü Microsoft'a sevk edin

Sonraki adım, sabit sürücüyü Microsoft'a sevk etmek ve ardından sürücü gönderimi işi için sevkiyat ve iade sevkiyat bilgilerini takip numarası sağlamak olacak. Sürücü Microsoft tarafından alındıktan sonra, veri merkezi personelinin PST dosyalarınızı kuruluş için Azure Depolama alanına yüklemesi, veri merkezi personelinin 7 ila 10 iş günü kadar sürer.
  
> [!NOTE]
> İzleme numarası sağlamaz ve sevkiyat bilgilerini içeri aktarma işini oluşturduklardan sonra 14 gün içinde geri getirersiniz, içeri aktarma işinin süresi dolar. Bu durumda, yeni bir sürücü gönderimi içeri aktarma işi oluşturmanız ([bkz. 4. Adım: Office 365'ta PST](#step-4-create-a-pst-import-job-in-office-365) İçeri Aktarma işi oluşturma) ve sürücü dosyasını ve PST içeri aktarma eşleme dosyasını yeniden göndermeniz gerekir.
  
### <a name="ship-the-hard-drive"></a>Sabit sürücüyü gönder

Sabit sürücüleri Microsoft'a iletirken aşağıdaki şeyleri unutmayın:
  
- SATA-USB bağdaştırıcısını sevk etme; yalnızca sabit sürücüyü gönderesiniz.

- Sabit sürücüyü düzgün paketle; Örneğin, statik olmayan bir paket veya kabarcık kaydırma kullanabilirsiniz.

- Sabit sürücüyü Microsoft'a sevk etmek için tercihi olan bir teslimat taşıyıcı kullanın.

- Sabit sürücüyü, 4. Adımda içeri aktarma işini oluşturulduğunda görüntülenen Microsoft konumu adresine sürükleyin. Sevk adresine "Office 365 Hizmeti" ekli olduğundan emin olun.

- Sabit sürücüyü sevk ettikten sonra, teslimat operatörünüzün adını ve takip numarasını not a not aktan emin olun. Bunları bir sonraki adımda sağlayacakz.
    
### <a name="enter-the-tracking-number-and-other-shipping-information"></a>Takip numarasını ve diğer sevkiyat bilgilerini girin

Sabit sürücüyü Microsoft'a sevk ettikten sonra, İçeri aktarma hizmeti sayfasındaki aşağıdaki yordamı izleyin.
  
1. <https://compliance.microsoft.com> Gidip, kurumda yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. Gezinti bölmesinin sol bölmesinde, Microsoft 365 uyumluluk merkezi yönetimi **ve İçeri Aktar'> tıklayın**.

3. İçeri **Aktar** sekmesinde, izleme numarasını girmek istediğiniz sürücü sevkiyatı işini tıklatın.

4. Durum sayfası izleme numarasını **girin'e tıklayın**.

5. Aşağıdaki sevkiyat bilgilerini sağlama:

   1. **Teslimat operatörü** Sabit sürücüyü Microsoft'a sevk etmek için kullanılan teslimat operatörünüzün adını yazın. 

   2. **Takip numarası** Sabit sürücü sevkiyatı için izleme numarasını yazın. 

   3. **Operatör hesap numarası iade** Return carrier altında listelenen operatör için kuruluş hesap **numarasını yazın**. Microsoft, sabit sürücülerinizi size geri götürmek için bu hesabı kullanır (ve ücretler kullanır). ABD ve Avrupa'daki kuruluşların FedEx hesabı olması gerekir. Asya'daki ve dünyanın geri kalanındaki kuruluşların DHL'de bir hesabı olması gerekir.

6. Bu **bilgileri içeri** aktarma işi için kaydetmek için Kaydet'e tıklayın. 

    İçeri Aktar **sekmesinde** Yenile simgesine ![tıklayın.](../media/O365-MDM-Policy-RefreshIcon.gif) **Sürücü** gönderimi içeri aktarma işinin bilgilerini güncelleştirmek için yenileyin. Durum'ın artık Sürücüler geçişte **olarak ayar olduğunu fark ettiysiniz**.

## <a name="step-6-filter-data-and-start-the-pst-import-job"></a>6. Adım: Verileri filtreleme ve PST İçeri Aktarma işini başlatma

Sabit sürücün Microsoft tarafından alındıktan sonra **PST** dosyalarını içeri aktar sayfasındaki içeri aktarma işinin durumu Sürücüler alındı **olarak değişir**. Veri merkezi personeli, PST dosyalarınızı azure karne alanına yüklemek için günlük dosyasındaki Depolama kullanır. Bu noktada durum, İçeri aktarma devam **ediyor olarak değişir**. Daha önce de belirtildiği gibi, sabit sürücüm aldıktan sonra PST dosyalarını karşıya yüklemek 7 ila 10 iş günü kadar sürer.
  
PST dosyaları Azure'a yüklendikten sonra Durumu Çözümleme devam **ediyor olarak değiştirilir**. Bu, Microsoft 365 yaşlarını ve PST dosyalarında yer alan farklı ileti türlerini tanımlamak için PST dosyalarında bulunan verileri (güvenli ve güvenli bir şekilde) çözümlemektedir. Çözümleme tamamlandığında ve veriler içeri aktarmaya hazır olduğunda, içeri aktarma işinin durumu Çözümleme tamamlandı olarak **değiştirilir**. Bu noktada, PST dosyalarında yer alan tüm verileri içeri aktarma seçeneğiniz vardır veya içeri aktarılan verileri, hangi verilerin içeri aktar alın dosyalarını kontrol etmek için filtreler ayarp kırpabilirsiniz.
  
1. <https://compliance.microsoft.com> Gidip, kurumda yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. Gezinti bölmesinin sol bölmesinde Bilgi idaresi ****Microsoft 365 uyumluluk merkezi** \> **** öğesini tıklatın.

3. İçeri Aktar **sekmesinde**, 4. Adımda oluşturduğunuz içeri aktarma işini seçin ve içeri **aktar'a tıklayın ve sonra da Office 365**.
  
    PST dosyaları ve içeri aktarma işiyle ilgili diğer bilgilerle birlikte dışarı uçan bir sayfa görüntülenir.

4. Verileri içeri **aktar'a Office 365**.

5. Verilerinizi **filtrele** sayfası görüntülenir. Verilerin yaşıyla ilgili bilgiler de dahil olmak üzere, PST dosyaları üzerinde OFFICE 365 tarafından gerçekleştirilen çözümlemeden elde edilen veri içgörülerini içerir. Bu noktada, içeri aktaracak veya tüm verileri olduğu gibi içeri aktaracak verilere filtre uygulama seçeneğiniz vardır. 

    ![PST dosyalarında verileri kırpabilirsiniz veya hepsini içeri aktarabilirsiniz.](../media/287fc030-99e9-417b-ace7-f64617ea5d4e.png)
  
6. Şunlardan birini yapın:

   1. İçeri aktarınan verileri kırpmak için Evet **, içeri aktarmadan önce filtrelemek istiyorum'a tıklayın**.

      PST dosyalarında verileri filtreleme ve içeri aktarma işini başlatma hakkında ayrıntılı adım adım yönergeler için bkz. PST dosyalarını içeri aktararak içeri aktarma ve içeri aktarma [Office 365](filter-data-when-importing-pst-files.md).

      Veya

   1. PST dosyalarında yer alan tüm verileri içeri aktarmak için Hayır, her şeyi içeri **aktarmayı istiyorum'a ve Sonra'ya** **tıklayın**.

7. Tüm verileri içeri aktarmayı seçtiysiniz, içeri **aktarma işini başlatmak için Verileri** içeri aktar'a tıklayın. 

    PST dosyalarını içeri aktarma sayfasında içeri aktarma **işinin durumu** görüntülenir. Yenile ![simgesine tıklayın.](../media/O365-MDM-Policy-RefreshIcon.gif) **Durum** sütununda görüntülenen durum bilgilerini güncelleştirmek **için yenileyin** . İçeri aktarılan her PST dosyasıyla ilgili durum bilgilerini görüntüleyen durum uç sayfası görüntülemek için içeri aktarma işini tıklatın. İçeri aktarma tamamlandığında ve PST dosyaları kullanıcı posta kutularına aktarılmışsa, durum Tamamlanmış olarak **değiştirilir**.

## <a name="view-a-list-of-the-pst-files-uploaded-to-microsoft-365"></a>Microsoft 365'a yüklenen PST dosyalarının listesini Microsoft 365

Microsoft Azure Depolama Gezgini'i (ücretsiz, açık kaynak bir araçtır) yükledikten sonra, (Microsoft veri merkezi personeli tarafından) azure Depolama alanına yüklenen PST dosyalarının listesini görüntülemek için yükleyebilir ve kullanabilirsiniz. Bunu, Microsoft'a gönderdiğiniz sabit sürücülerden gelen PST dosyalarının Azure Depolama alanına başarıyla yük Depolama.
  
> [!IMPORTANT]
> PST dosyalarını karşıya yüklemek Azure Depolama Gezgini değiştirmek için e-posta dosyasını değiştiremezsiniz. PST dosyalarını diğer dosyalarda içeri aktarmanın tek Microsoft 365 AzCopy kullanmaktır. Ayrıca Azure blob'larına yüklediğiniz PST dosyalarını silemezsiniz. Bir PST dosyasını silmeyi denersanız, gerekli izinlere sahip olmadığınız konusunda bir hata alırsınız. Tüm PST dosyaları Azure Depolama silinir. Devam eden bir içeri aktarma işi yoksa, ** ingestiondata ** kapsayıcısında yer alan tüm PST dosyaları, en son içeri aktarma işi oluşturulduktan 30 gün sonra silinir.
  
Organizasyon için Paylaşılan Erişim İmzası (SAS) URL'sini almak üzere aşağıdaki adımları uygulayın. Bu URL, azure ağ URL'si ile Depolama Microsoft bulutunda bir SAS anahtarı olan ağ URL'sinin bir bileşimidir. Bu anahtar, belirli bir konumdan, kuruluşun Azure veritabanına erişmek Depolama sağlar.

Azure Azure Depolama Gezgini alanınıza bağlanmak ve alanınıza bağlanmak Depolama:

1. <https://compliance.microsoft.com> Gidip, kurumda yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. Yönetim bölmesinin sol bölmesinde, Microsoft 365 uyumluluk merkezi yönetimi'ne **ve sonra İçeri Aktarma'> tıklayın**.

3. İçeri Aktar **sekmesinde** Simge Ekle'ye ![tıklayın.](../media/ITPro-EAC-AddIcon.gif) **Yeni içeri aktarma işi**.

4. İş içeri aktarma sihirbazında, PST içeri aktarma işi için bir ad yazın ve Ardından Sonraki'ye **tıklayın**. Küçük harf, sayı, kısa çizgi ve alt çizgi kullanın. Büyük harf kullanamaz veya adlarında boşluk ekemezsiniz.

5. İş türünü **içeri aktar'ı seçin** sayfasında, verilerinizi **Upload ve sonra** da Sonraki'yi **tıklatın**.

6. 2. adımda, Ağ karşıya yükleme **SAS URL'sini göster'e tıklayın**.

7. URL görüntülendikten sonra kopyalayın ve bir dosyaya kaydedin. URL'nin tamamını kopyalayıp kopyalamayı unutmayın.

    > [!IMPORTANT]
    > SAS URL'sini korumak için önlemler almaya emin olun. Bu, herkes tarafından kuruma uygun Azure depolama alanına erişmek için kullanılabilir.
  
8. İçeri **aktarma işi** sihirbazını kapatmak için İptal'e tıklayın.

9. Office 365'i [Microsoft Azure Depolama Gezgini yükleyin](https://go.microsoft.com/fwlink/p/?LinkId=544842).

10. Başlangıç Microsoft Azure Depolama Gezgini, sol bölmede **Hesaplar Depolama** sağ tıklayın ve **ardından Azure'a Bağlan Hesap Ekle'Depolama**.

    ![Hesaplar'a Depolama tıklayın ve ardından Azure'a Bağlan'a Depolama.](../media/75b80cc3-c336-4f96-ad32-54ac9b96a7af.png)
  
11. Paylaşılan **erişim imzası (SAS) URI'sini veya bağlantı dizesini kullan'ı tıklatın ve sonra da** Sonraki'yi **tıklatın**.

12. Sas **URI'si kullan'a** tıklayın, 1. adımda elde edilen SAS URL'sini **URI'nin** altındaki kutuya yapıştırın ve sonra da Sonraki'ye **tıklayın**.

13. Bağlantı **özeti sayfasında,** bağlantı bilgilerini gözden geçirebilirsiniz ve sonra Tamam'a **Bağlan**.

    **ingestiondata kapsayıcısı** açılır. Sabit sürücü bilgisayarınızdan PST dosyalarını içerir. **ingestiondata kapsayıcısı****, Depolama** \> **(SAS Ekli Hizmetler) Blob Kapsayıcıları'nın** \> **altında yer almaktadır**.

    ![Azure Depolama Gezgini, karşıya yüklediğiniz PST dosyalarının listesini görüntüler.](../media/12376fed-13a5-4a09-8fe6-e819e011b334.png)
  
14. Kaynak verilerini kullanmayı bitirdikten sonra, Microsoft Azure Depolama Gezgini **ingestiondata'ya** sağ tıklayın ve Azure Veri Alanı ile bağlantınızı  kesmek için Ayır'Depolama tıklayın. Aksi takdirde, eklemeye bir sonraki denemede hata alırsınız. 

    ![Azure Depolama alanınıza bağlantınızı kesmek için, ingestion'a sağ tıklayın ve Depolama tıklayın.](../media/1e8e5e95-4215-4ce4-a13d-ab5f826a0510.png)

## <a name="troubleshooting-tips"></a>Sorun giderme ipuçları

- **PST İçeri Aktarma CSV eşleme dosyasındaki hatalar nedeniyle içeri aktarma işi başarısız olursa ne olur?** Eşleme dosyasındaki hatalar nedeniyle içeri aktarma işi başarısız olursa, içeri aktarma işi oluşturmak için sabit sürücüyü Microsoft'a tekrar aktarmanız gerekir. Bunun nedeni, sürücü gönderimi içeri aktarma işi için gönderilen sabit sürücüden gelen PST dosyalarının, önceden kuruluşun Azure Depolama alanına yüklenmeleridir. Bu durumda, CSV içeri aktarma CSV eşleme dosyasındaki hataları yalnızca düzeltmeniz ve yeni bir "ağ karşıya yükleme" içeri aktarma işi oluşturmanız ve düzeltilmiş CSV eşleme dosyasını göndermeniz gerekir. Yeni ağ karşıya yükleme içeri aktarma işi oluşturmak ve başlatmak için bkz[. 5. Adım: Microsoft 365'te PST](use-network-upload-to-import-pst-files.md#step-5-create-a-pst-import-job) İçeri Aktarma işi oluşturma ve [6](use-network-upload-to-import-pst-files.md#step-6-filter-data-and-start-the-pst-import-job). Adım: Verileri filtreleme ve "PST dosyalarını başka bir klasöre içeri aktarma için ağ karşıya yükleme kullanma" konusunun PST İçeri Aktarma işini Office 365." 
    
    > [!NOTE]
    > PST İçeri Aktarma CSV eşleme dosyası sorunlarını gidermenize yardımcı olması için, [Azure Depolama Gezgini](#view-a-list-of-the-pst-files-uploaded-to-microsoft-365) aracını kullanarak Azure depolama alanına yüklenen sabit sürücüdeki PST dosyalarının **ingestiondata** kapsayıcısında klasör yapısını görüntülemeniz gerekir. Dosya eşleme hatalarına genellikle FilePath parametresinde yanlış değer neden olur. Bu parametre, Azure depolama alanında bir PST dosyasının konumunu belirtir. 3. Adımdaki tabloda FilePath [parametresinin açıklamasına bakın](#step-3-create-the-pst-import-mapping-file). Daha önce de belirtildiği gibi, Azure  `/dstdir:` depolama alanı içinde PST dosyalarının konumu, 2. Adım'da WAImportExport.exe parametre [tarafından belirtilmişti](#step-2-copy-the-pst-files-to-the-hard-drive). 
  
## <a name="more-information"></a>Daha fazla bilgi

- Sürücü gönderimi, büyük miktarlardaki arşivleme mesajlaşma verilerini, Microsoft 365 kullanılabilen uyumluluk özelliklerinden yararlanmak amacıyla içeri aktarmanın etkili bir yoludur. Arşivleme verileri kullanıcı posta kutularına aktarıldıktan sonra şunları kullanabilirsiniz:

  - [Kullanıcılara veriler için daha fazla](enable-archive-mailboxes.md) [posta kutusu depolama alanı sağlamak için](enable-autoexpanding-archiving.md) arşiv posta kutularını etkinleştirin ve arşivlemeyi otomatik olarak genişletin. 

  - Verileri korumak için [posta kutularını Mahkeme Tutma'ya](./create-a-litigation-hold.md) alın. 

  - Veride [arama yapmak için Microsoft eBulma](search-for-content.md) araçlarını kullanın. 

  - Verilerin [Microsoft 365 tutulacaklarını](retention.md) ve bekletme süresi dolduktan sonra hangi eylemin uygulanacaklarını kontrol etmek için bu bekletme ilkelerini uygulayabilirsiniz. 

  - Denetim [günlüğünde bu](search-the-audit-log-in-security-and-compliance.md) verilerle ilgili olayları arama. 

  - Verileri uyumluluk amacıyla [arşivlemek için etkin](inactive-mailboxes-in-office-365.md) olmayan posta kutularına aktarın. 

  - Hassas bilgilerin veri kaybına [karşı](dlp-learn-about-dlp.md) organizasyonlarınızı koruyun. 

- Güvenli depolama hesabı anahtarı ve BitLocker şifreleme anahtarı örneği. Bu örnekte, PST dosyalarını bir sabit WAImportExport.exe kopyalamak için çalıştırdınız Komut Dosyası komutunun söz dizimi de vardır. Aynı parolaları veya güvenlikle ilgili diğer bilgileri korur gibi bunları korumak için önlemler almaya devam edin.

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

- Daha önce de Office 365 olarak, PST dosyaları posta kutusuna aktarıldıktan sonra İçeri Aktarma hizmeti bekletme ayarını (süresiz bir süre için) etkinleştirir. Bu,  *RentionHoldEnabled*  `True` özelliğinin, posta kutusuna atanan bekletme ilkesi işlenmemeyecek şekilde ayar olduğu anlamına gelir. Bu, posta kutusu sahibine eski iletileri silme veya arşivleme ilkesi silmesini veya arşivlemesini engelerek, yeni aktarılan iletileri yönetmesi için zaman verir. Bu bekletmeyi yönetmek için atılması gereken bazı adımlar: 

  - Belirli bir süre sonra, komutu çalıştırarak bekletmeyi kapatabilirsiniz  `Set-Mailbox -RetentionHoldEnabled $false` . Yönergeler için bkz. [Posta kutusunu bekletmeye saklama](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

  - Bekletmeyi yapılandırarak, gelecekte bir tarihte kapatıldığından emin olun. Bunu, komutu çalıştırarak yapar  `Set-Mailbox -EndDateForRetentionHold <date>` . Örneğin, bugünün tarihin 1 Haziran 2016 olduğunu ve 30 gün içinde bekletmenin kapalı tutulmasını istediğiniz varsayarak şu komutu çalıştırabilirsiniz:  `Set-Mailbox -EndDateForRetentionHold 7/1/2016`. Bu senaryoda,  *RentionHoldEnabled*  özelliğini  *True olarak değiştirilebilir*. Daha fazla bilgi için bkz. [Set-Mailbox](/powershell/module/exchange/set-mailbox).

  - Posta kutusuna atanmış olan bekletme ilkesi ayarlarını değiştirebilirsiniz; böylelikle, aktarılan eski öğeler hemen silinmez veya kullanıcının arşiv posta kutusuna taşınmaz. Örneğin, posta kutusuna atanmış bir silme veya arşiv ilkesi için bekletme süresini uzatabilirsiniz. Bu senaryoda, bekletme ilkesi ayarlarını değiştirdikten sonra posta kutusunda bekletme bekletmeyi kapatabilirsiniz. Daha fazla bilgi için bkz [. Kuruluşlarınız için posta kutuları için arşivleme ve silme ilkesi ayarlama](set-up-an-archive-and-deletion-policy-for-mailboxes.md).
