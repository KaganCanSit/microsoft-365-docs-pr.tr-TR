---
title: İçerik arama sonuçlarını dışarı aktarma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.CustomizeExport
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: ed48d448-3714-4c42-85f5-10f75f6a4278
description: Çalışma sayfalarındaki İçerik aramalarından arama sonuçlarını Microsoft 365 uyumluluk merkezi bilgisayara aktarın. E-posta sonuçları PST dosyaları olarak dışarı aktarıldı. Site SharePoint site OneDrive İş, yerel belge olarak Office dışarı aktarıldı.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 22f66333a5fa2c5b570b564276c626fa0b41f83d
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989963"
---
# <a name="export-content-search-results"></a>İçerik arama sonuçlarını dışarı aktarma

İçerik arama başarıyla çalıştırıldıktan sonra, arama sonuçlarını yerel bir bilgisayara aktarabilirsiniz. E-posta sonuçlarını dışarı aktarsanız, bunlar bilgisayarınıza PST dosyaları olarak indirilir. Site ve sitelerden içerik SharePoint OneDrive İş, yerel ve yerel Office belge kopyaları dışarı aktarıldı. Dışarı aktarıldı arama sonuçlarında başka belgeler ve raporlar da vardır.
  
İçerik arama sonuçlarını dışarı aktarma işlemi, sonuçların hazırlanmasını ve ardından bunları yerel bir bilgisayara indirmeyi içerir. Arama sonuçlarını dışarı aktarmaya yönelik bu adımlar, Core eKovery davaları ile ilişkilendirilmiş bir aramanın sonuçlarını dışarı aktarmada da geçerlidir.
  
## <a name="before-you-export-search-results"></a>Arama sonuçlarını dışarı aktarmadan önce

- Arama sonuçlarını dışarı aktaracak şekilde, bu arama sonuçlarında Dışarı aktarma yönetimi rolüne Microsoft 365 uyumluluk merkezi. Bu rol, yerleşik eBulma Yöneticisi rol grubuna atanır. Kuruluş Yönetimi rol grubuna varsayılan olarak atanmamaktadır. Daha fazla bilgi için bkz [. eBulma izinleri atama](assign-ediscovery-permissions.md).

- Arama sonuçlarını dışarı aktarmada kullanmakta olduğunuz bilgisayar aşağıdaki sistem gereksinimlerini karşılamalıdır:
  
  - En son Windows (32 bit veya 64 bit)
  
  - Microsoft .NET Framework 4.7 veya daha yüksek bir sürümü
  
- eBulma Dışarı Aktarma Aracı Microsoft Edge <sup>1'i</sup> çalıştırabilirsiniz. Arama sonuçlarını dışarı aktarmada Internet Explorer 11 kullanmak artık <sup>desteklenmiyor2</sup>.
  
  > [!NOTE]
  > <sup>1</sup> Yeni E-postada yapılan son Microsoft Edge ClickOnce artık varsayılan olarak etkinleştirilmez. Edge'de ClickOnce etkinleştirme yönergeleri için bkz. [eBulma Dışarı Aktarma](configure-edge-to-export-search-results.md) Aracı'nı Microsoft Edge. Ayrıca Microsoft, üçüncü taraf uygulamaları için üçüncü taraf uzantıları veya eklentileri ClickOnce değildir. Üçüncü taraf uzantıları veya eklentileri olan desteklenmeyen bir tarayıcı kullanarak arama sonuçlarını dışarı aktarma desteklenmez.
  >
  > <sup>2</sup> Ağustos 2021'den itibaren Microsoft 365 uygulamaları ve hizmetleri artık Internet Explorer 11'i (IE11) desteklememektedir ve kullanıcılar daha iyi bir deneyime sahip olabilir veya bu uygulamalara ve hizmetlere bağlanamaz. Desteğin sorunsuz sona erer olması için, bu uygulama ve hizmetler önümüzdeki haftalarda ve aylarda aşamalı olarak yapılacaktır. Her uygulama ve hizmet bağımsız zamanlamalar üzerinde aşamalı olarak aşamalı olarak mektedir. Daha fazla bilgi için bu [blog gönderisi'ne bakın](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-365-apps-say-farewell-to-internet-explorer-11-and/ba-p/1591666).

- 2. Adımda arama sonuçlarını indirmek için kullanabileceğiniz eBulma Dışarı Aktarma Aracı, otomasyonu (betik kullanarak veya cmdlet'leri çalıştırarak) desteklemez. 1. Adımda hazırlık sürecini veya 2. Adım'daki indirme işlemini otomatikleştirmemanizi kesinlikle öneririz. Bu işlemlerden herhangi birini otomatik halelersiniz, sorun olursa Microsoft Desteği yardım sağlamaz.

- Arama sonuçlarını yerel bir bilgisayara indirmenizi öneririz. Şirketinizin güvenlik duvarı veya ara sunucu altyapısını arama sonuçlarını indirirken sorunlara neden olacak sorunları ortadan kaldırmak için, arama sonuçlarını ağ dışında sanal bir masaüstüne indirmeyi düşünebilirsiniz. Bu, çok fazla sayıda dosya dışarı aktarma sırasında Azure veri bağlantılarında oluşan zaman aşımını azaltabilir. Sanal masaüstleri hakkında daha fazla bilgi için Bkz[. Windows Sanal Masaüstü](https://azure.microsoft.com/services/virtual-desktop).

- Arama sonuçlarını indirirken performansı artırmak için, büyük bir sonuç kümesine dönüşen aramaları daha küçük aramalara bölmeyi göz önünde bulundurabilirsiniz. Örneğin, daha hızlı indirilebilen daha küçük bir sonuç kümesi elde etmek için arama sorgularında tarih aralıklarını kullanabilirsiniz.
  
- Arama sonuçlarını dışarı aktarsanız bile veriler, yerel bilgisayarınıza indir Depolama Microsoft tarafından sağlanan bir Azure bulut Depolama geçici olarak depolanır. Kuruluş kuruluşlarının Azure'daki **\*.blob.core.windows.net** uç noktasına bağlana olduğundan emin olun (joker karakter dışarı aktarmanız için benzersiz bir tanımlayıcıyı temsil eder). Arama sonuçları verileri, oluşturulduktan Depolama hafta sonra Azure Veri Kaynağı'nden silinir. 
  
- Kuruluş internet ile iletişim kurmak için bir proxy sunucusu kullanıyorsa, arama sonuçlarını dışarı aktarmada kullanılan bilgisayarda ara sunucu ayarlarını tanımlamanız gerekir (böylelikle dışarı aktarma aracının, proxy sunucunuz tarafından kimlik doğrulaması yapabilirsiniz). Bunu yapmak için *machine.configdosyanızı* dosya sürümünüzle eşleşen konumda Windows. 
  
  - **32 bit:** `%windir%\Microsoft.NET\Framework\[version]\Config\machine.config`
  
  - **64 bit:** `%windir%\Microsoft.NET\Framework64\[version]\Config\machine.config`
  
    Dosya dosyasına, etiketler  *machine.config*  bir yere aşağıdaki satırları  `<configuration>`  `</configuration>` ekleyin. Örneğin, kurum için  `ProxyServer` doğru  `Port` değerleri değiştiriyor veya doğru değerlerle değiştiriyor olun `proxy01.contoso.com:80`. 
  
    ```xml
    <system.net>
       <defaultProxy enabled="true" useDefaultCredentials="true">
         <proxy proxyaddress="https://ProxyServer :Port " 
                usesystemdefault="False" 
                bypassonlocal="True" 
                autoDetect="False" />
       </defaultProxy>
    </system.net>
    ```

- Bir aramanın sonuçları 7 günlükten eskiye kadar ise ve dışarı aktarma işi gönderdiğinizde, arama sonuçlarını güncelleştirmek için aramaya yeniden çalışmanızı istenen bir hata iletisi görüntülenir. Böyle bir durumda, dışarı aktarma işlemini iptal edin, aramanızı yeniden çalıştırın ve sonra dışarı aktarma işlemini yeniden başlatın.

## <a name="step-1-prepare-search-results-for-export"></a>1. Adım: Arama sonuçlarını dışarı aktarma için hazırlama

İlk adım, arama sonuçlarını dışarı aktarma için hazırlamaktır. Sonuçları hazırlarken, bunlar Microsoft tarafından sağlanan bir Azure veya Microsoft Depolama bir konuma karşıya yüklenenler. Posta kutuları ve sitelerden gelen içerikler, saatte en fazla 2 GB ücretle karşıya yüklenen içeriktir.
  
1. İçerik Microsoft 365 uyumluluk merkezi, sonuçları dışarı aktarmayı istediğiniz içerik aramanızı seçin.
  
2. Açılır **sayfanın en** altındaki Eylemler menüsünde Sonuçları dışarı aktar'a **tıklayın**.

   ![Eylemler menüsünde sonuçları dışarı aktar seçeneği.](../media/ActionMenuExportResults.png)

   Sonuçları **dışarı** aktar uç sayfası görüntülenir. İçerik dışarı aktarmada kullanılabilen dışarı aktarma seçenekleri, arama sonuçlarının posta kutularında mı yoksa sitelerde mi yoksa her ikisinde birden mi bulunduğuna bağlıdır.

3. Çıkış **seçenekleri'nin** altında aşağıdaki seçeneklerden birini belirleyin:
  
   ![Çıkış seçeneklerini dışarı aktarma.](../media/ExportOutputOptions.png)

    - **Tanınmayan biçime sahip olanlar** hariç olmak üzere tüm öğeler şifrelenir veya başka nedenlerle dizine alındı. Bu seçenek yalnızca dizine alındı olan öğeleri dışarı aktarıyor.
  
    - **Tanınmayan biçime sahip olanlar** da dahil olmak üzere tüm öğeler şifrelenir veya başka nedenlerle dizine alındı. Bu seçenek dizinli ve dizine eksiz öğeleri dışarı aktarıyor.
  
    - **Yalnızca tanınmayan biçime sahip öğeler şifrelenir veya başka nedenlerle dizine alındı.** Bu seçenek yalnızca tekinde olmayan öğeleri dışarı aktarıyor.

      Kısmen [dizine](#more-information) alınan öğelerin nasıl dışarı aktarıldı hakkında bir açıklama için Daha fazla bilgi bölümüne bakın. Kısmen dizine alınan öğeler hakkında daha fazla bilgi için bkz [. İçerik arama'da Kısmen dizine alınan öğeler](partially-indexed-items-in-content-search.md).

4. İçeriği **Exchange altında**, aşağıdaki seçeneklerden birini belirleyin:
  
   ![Exchange seçin.](../media/ExchangeExportOptions.png)

    - **Her posta kutusu için bir** PST dosyası: Arama sonuçları içeren her kullanıcı posta kutusu için bir PST dosyası dışarı aktarır. Kullanıcının arşiv posta kutusundan elde edilen tüm sonuçlar aynı PST dosyasına dahil edilir. Bu seçenek, kaynak posta kutusundan posta kutusu klasör yapısını yeniden oluşturur.
  
    - **Tüm iletileri içeren bir PST** dosyası: Aramaya dahil olan tüm kaynak posta kutularından arama sonuçlarını içeren tek bir PST dosyası (*Exchange.pst* olarak adlandırılmıştır) dışarı aktarma. Bu seçenek, her ileti için posta kutusu klasör yapısını yeniden oluşturur.
  
    - **Tek bir klasördeki tüm iletileri içeren bir PST** dosyası: Arama sonuçlarını, tüm iletilerin tek, en üst düzey bir klasörde bulunduğu tek bir PST dosyasına dışarı aktarır. Bu seçenek, gözden geçirenlerin her öğenin özgün posta kutusu klasör yapısında gezinmek zorunda kalmadan öğeleri kronolojik sırayla (öğeler gönderilmiş tarihe göre sıralanmış) gözden geçirmesine olanak sağlar.
  
    - **Tek tek iletiler**: .msg biçimini kullanarak arama sonuçlarını tek tek e-posta iletileri olarak dışarı aktarabilirsiniz. Bu seçeneği belirtirseniz, e-posta arama sonuçları dosya sistemideki bir klasöre dışarı aktarıldı. Tek tek iletilerin klasör yolu, sonuçları bir PST dosyasına aktardıysanız kullanılanla aynıdır.
  
5. Aşağıdaki ek seçenekleri yapılandırma:

   ![Diğer dışarı aktarma seçeneklerini yapılandırma.](../media/OtherExportOptions.png)

   1. Yinelenen iletileri **dışarıda tutmak için Bu içerik için Exchange** de-yinelemeyi etkinleştir onay kutusunu seçin.
  
      Bu seçeneği tercih ediyorsanız, aynı iletinin birden çok kopyası arama yapılan posta kutularında bulunsa bile iletinin yalnızca bir kopyası dışarı aktarılıyor. Dışarı aktarma sonuçları raporu (Results.csv adlı bir dosya), yinelenen iletinin her kopyası için bir satır içerir; böylece, yinelenen iletinin bir kopyasını içeren posta kutularını (veya ortak klasörleri) tanımlayabilirsiniz. Yinelemeyi de-yineleme ve yinelenen öğelerin nasıl tanım olduğu hakkında daha fazla bilgi için bkz. [eBulma arama sonuçlarında yinelemeyi geri bulma](de-duplication-in-ediscovery-search-results.md).
  
   2. Belgelerin **tüm sürümlerini dışarı SharePoint için Dosyaların** sürümlerini dahil edin onay SharePoint seçin. Bu seçenek yalnızca aramanın içerik kaynakları arama sonuçlarını veya site SharePoint OneDrive İş görünür.
  
   3. Sıkıştırılmış **(sıkıştırılmış) bir klasörde dosyaları dışarı aktar'ı seçin. Arama sonuçlarını sıkıştırılmış klasörlere dışarı SharePoint tek** tek iletileri ve belgeleri içeren onay kutusunu içerir. Bu seçenek yalnızca öğeleri ayrı Exchange ileti olarak dışarı aktarmayı seçtiyseniz ve arama sonuçlarında tek SharePoint veya OneDrive görüntülenir. Bu seçenek öncelikle öğeler dışarı aktarıldıken dosya yolu adlarında 260 Windows sınırını aşarak çalışmak için kullanılır. Daha fazla bilgi bölümünde "Dışarı aktaran öğelerin dosya [adları" bölümüne](#more-information) bakın.
   > [!IMPORTANT]
   > Sıkıştırılmış bir klasöre dosya dışarı aktarılabilir biçimde dışarı aktarma, dışarı aktarma sürelerini artıracaktır.
  
6. Dışarı **aktarma işlemini** başlatmak için Dışarı Aktar'a tıklayın. Arama sonuçları indirmeye hazırlanır ve bu da özgün içerik konumlarından toplanacakları ve sonra Microsoft bulut'ta bir Azure Depolama konumlarına yükleneceği anlamına gelir. Bu birkaç dakika sürebilir.

Dışarı aktaran arama sonuçlarını indirme yönergeleri için sonraki bölüme bakın.
  
## <a name="step-2-download-the-search-results"></a>2. Adım: Arama sonuçlarını indirme

Sonraki adım, arama sonuçlarını Azure Depolama Depolama yerel bilgisayarınıza indirmektir.

> [!NOTE]
> Dışarı aktarılan arama sonuçlarının, siz 1. Adımda dışarı aktarma işini oluşturduktan sonra 14 gün içinde indirilmiş olması gerekir.
  
1. İçerik **arama sayfasında**, Microsoft 365 uyumluluk merkezi **sekmesine** tıklayın
  
   Oluşturduğunuz dışarı aktarma **işinin gösterirken** dışarı aktarma işleri listesini güncelleştirmek için Yenile'ye tıklamanız gerekir. Dışarı aktarma işleri, arama adının sonuna eklenen **adla _Export** aramayla aynıdır.
  
2. 1. Adımda oluşturduğunuz dışarı aktarma işini seçin.

3. Dışarı aktar tuşu altındaki dışarı aktarma **sayfasında Panoya** **kopyala'ya tıklayın**. Arama sonuçlarını indirmek için 6. adımda bu anahtarı kullanırsiniz.
  
   > [!IMPORTANT]
   > Herkes eBulma Dışarı Aktarma aracını yük indirip başlatalır ve sonra arama sonuçlarını indirmek için bu anahtarı kullanabileceği için, aynı parolaları veya güvenlikle ilgili diğer bilgileri korur gibi, bu anahtarı korumak için önlemler almaya devam edin.

4. Uç uç sayfasının en üstünde Sonuçları **indir'e tıklayın**.

5. eBulma Dışarı Aktarma Aracı'nı yüklemeniz **istenirse Yükle'ye** **tıklayın**.

6. **eBulma Dışarı Aktarma Aracı'da** şunları yapın:

   ![eBulma Dışarı Aktarma Aracı.](../media/eDiscoveryExportTool.png)

   1. 3. adımda kopyalanmış olan dışarı aktarma anahtarını uygun kutuya yapıştırın.
  
   2. Arama **sonucu** dosyalarını indirmek istediğiniz konumu belirtmek için Gözat'a tıklayın.
  
      > [!IMPORTANT]
      >  İndirme sırasındaki yüksek ağ etkinliği nedeniyle, arama sonuçlarını yalnızca yerel bilgisayarınızki bir iç sürücüde yer alan bir konuma indirmeniz gerekir. En iyi indirme deneyimini yaşamak için aşağıdaki yönergeleri izleyin: <br/>
      >- Arama sonuçlarını bir UNC yoluna, eşlenmiş ağ sürücüsüne, harici USB sürücüsüne veya eşitlenmiş bir OneDrive İş indirmez.<br/>
      >- Arama sonuçlarını indiren klasör için virüsten koruma taramayı devre dışı bırak.<br/>
      >- Eşzamanlı indirme işleri için arama sonuçlarını farklı klasörlere indirin.

7. Arama **sonuçlarını** bilgisayarınıza indirmek için Başlat'a tıklayın.
  
    **eBulma Dışarı Aktarma Aracı**, indirilecek kalan öğelerin sayısının (ve boyutunun) tahmini de içinde olmak üzere, dışarı aktarma işlemiyle ilgili durum bilgilerini görüntüler. Dışarı aktarma işlemi tamamlandığında, dosyalar indirildikten sonra bu dosyalara erişebilirsiniz.

## <a name="more-information"></a>Daha fazla bilgi

Burada, arama sonuçlarını dışarı aktarma hakkında daha fazla bilgi ve bilgileri edinebilirsiniz.
  
[Dışarı aktarma sınırları](#export-limits)
  
[Raporları dışarı aktarma](#export-reports)
  
[Kısmen dizine alan öğeleri dışarı aktarma](#exporting-partially-indexed-items)

[Tek tek iletileri veya PST dosyalarını dışarı aktarma](#exporting-individual-messages-or-pst-files)

[RMS korumalı e-posta iletilerinin ve şifreli dosya eklerin şifresini çözme](#decrypting-rms-protected-email-messages-and-encrypted-file-attachments)

[Dışarı aktarıldı öğelerin dosya adı](#filenames-of-exported-items)  
  
[Diğer](#miscellaneous)
  
### <a name="export-limits"></a>Dışarı aktarma sınırları

İçerik arama sonuçlarını dışarı aktarma sınırları hakkında bilgi için, İçerik arama sınırlamaları bölümündeki "Dışarı aktarma sınırları" [bölümüne bakın](limits-for-content-search.md#export-limits).

### <a name="export-reports"></a>Raporları dışarı aktarma
  
- Arama sonuçlarını dışarı aktararak, arama sonuçlarına ek olarak aşağıdaki raporlar da yer almaktadır.
  
  - **Dışarı Aktarma Özeti** Dışarı Excel özetini içeren en iyi belge. Bunlar arasında arama yapılan içerik kaynaklarının sayısı, arama sonuçlarının tahmin edilen ve indirilen boyutları ve dışarı aktarıldı olarak tahmin edilen ve indirilen öğe sayısı gibi bilgiler yer gelir.
  
  - **Bildirim** Arama sonuçlarına dahil edilen her öğe hakkında bilgi içeren bir bildirim dosyası (XML biçiminde).
  
  - **Sonuçlar** Bir Excel arama sonucu olarak indirilen her öğe hakkında bilgi içeren en iyi belge. E-posta için, sonuç günlüğü her ileti hakkında aşağıdaki bilgileri içerir:
  
    - İletinin kaynak posta kutusunda bulunduğu konum (iletinin birincil posta kutusunda mı yoksa arşiv posta kutusunda mı bulunduğu da dahil).
  
    - İletinin gönderildiği veya alın aldığı tarih.

    - İletinin Konu satırı.

    - İletinin göndereni ve alıcıları.

    - Arama sonuçlarını dışarı aktarmada yinelemeyi geri alma seçeneğini etkinleştirdiyseniz iletinin yinelenen ileti olup olmadığı. Yinelenen iletilerin Öğeye Çoğalt **sütununda, iletiyi** yinelenen olarak tanımlayan bir değeri vardır. Öğeye Çoğalt **sütunundaki** değer, dışarı aktarılmış olan iletinin öğe kimliğini içerir. Daha fazla bilgi için bkz [. eBulma arama sonuçlarında yinelemeyi geri bulma](de-duplication-in-ediscovery-search-results.md).

      Site sitelerinden SharePoint ve OneDrive İş için, sonuç günlüğü her belgeyle ilgili bilgileri içerir; örneğin:

      - Belgenin URL'si.

      - Belgenin bulunduğu site koleksiyonunun URL'si.

      - Belgenin son değiştirilma tarihi.

      - Belgenin adı (sonuç günlüğünde Konu sütununda yer alır).

  - **Unindexed Items** Arama Excel kısmen dizine alınan öğeler hakkında bilgi içeren en iyi belge. Arama sonuçları raporunu  generateken kısmen dizine alındı öğeleri dahil etmediğiniz durumda, bu rapor yine de indirilir, ancak boş olur.

  - **Hatalar ve Uyarılar** Dışarı aktarma sırasında karşılaşılan dosyalar için hatalar ve uyarılar içerir. Tek tek hata veya uyarılara özgü bilgiler için Hata Ayrıntıları sütununa bakın.

  - **Atlanan Öğeler** Bu sitelerden ve sitelerden SharePoint OneDrive İş dışarı aktarabilirsiniz, dışarı aktarmada çoğunlukla atlanan öğeler raporu (atlanan öğe) yer SkippedItems.csv. Bu raporda adıilen öğeler genellikle klasör veya belge kümesi gibi indirilemedi öğelerdir. Bu tür öğeleri dışarı aktarmama tasarımına göredir. Atlanan diğer öğeler için, atlanan öğeler raporu'daki 'Hata Türü' ve 'Hata Ayrıntıları' alanı, öğenin atlanma nedenini ve diğer arama sonuçlarıyla birlikte indirilma nedenini gösterir.

  - **Trace.log Dışarı** aktarma işlemi hakkında ayrıntılı günlük bilgileri içerir ve dışarı aktarma sırasında sorunları ortaya çıkarmanıza yardımcı olabilir. Arama sonuçlarını dışarı aktarmayla ilgili bir sorun hakkında Microsoft Desteği ile bir bilet açarsanız, bu izleme günlüğünü sağlamanız isten olabilir.
  
    > [!NOTE]
    > Gerçek arama sonuçlarını dışarı aktarmaya gerek kalmadan bu belgeleri dışarı aktarabilirsiniz. Bkz [. İçerik arama raporunu dışarı aktarma](export-a-content-search-report.md).
  
### <a name="exporting-partially-indexed-items"></a>Kısmen dizine alan öğeleri dışarı aktarma
  
- Posta kutusu öğelerini arama sonuçlarında tüm posta kutusu öğelerini döndüren bir içerik aramasını dışarı aktarıyorsanız (arama sorgusuna dahil edilen anahtar sözcükler yoksa), kısmen dizine alan öğeler dizine alınmış öğelerin bulunduğu PST dosyasına kopyalanmaz. Bunun nedeni, kısmen dizine alınan öğeler de dahil olmak üzere tüm öğelerin otomatik olarak normal arama sonuçlarına dahil olmasıdır. Bu, kısmen dizine alınan öğelerin diğer, dizine alınan öğeleri içeren bir PST dosyasına (veya tek tek iletiler olarak) dahil edilecek olması anlamına gelir.

    Hem dizine hem de kısmen dizine alan öğeleri dışarı aktarıyorsanız veya tüm öğeleri döndüren içerik aramalarından yalnızca dizine alan öğeleri dışarı aktarıyorsanız, aynı sayıda öğe indirilir. bu durum, içerik arama tahmini arama sonuçları (Microsoft 365 uyumluluk merkezi'de arama istatistiklerinde görüntülenir) kısmen dizine alınan öğelerin sayısı için ayrı bir tahmin içermeye devam ediyor olsa bile, böyle olur. Örneğin, tüm öğeleri içeren bir arama tahminini (arama sorgusunda anahtar sözcük yok) 1.000 öğenin bulunduğu ve 200 kısmen dizine alınan öğenin de bulunduğu tahminini gösteriyor olabilir. Bu durumda, arama tüm öğeleri döndüren 1.000 öğe kısmen dizine alındı öğeleri içerir. Başka bir deyişle, arama tarafından döndürülen toplam 1.000 öğe vardır ve bunlar 1.200 öğe (beklediğiniz gibi) değildir. Bu aramanın sonuçlarını dışarı aktarıyor ve dizine alan veya kısmen dizine alan öğeleri dışarı aktarmayı (veya yalnızca kısmen dizine alan öğeleri dışarı aktarmayı) seçerseniz, 1.000 öğe indirilir. Bir kez daha belirtir, tüm öğeleri geri almak için boş bir arama sorgusu kullanırsanız, kısmen dizine alan öğeler normal (dizine alındı) sonuçlarına dahil edilir. Bu örnekte, yalnızca kısmen dizinemiş öğeleri dışarı aktarmayı seçerseniz, yalnızca dizine eksiz 200 öğe indirilir.

    Ayrıca, önceki örnekte (dizine alan ve kısmen dizine alan öğeleri dışarı aktarsanız veya yalnızca dizine sahip öğeleri dışarı aktardıysanız), dışarı aktarılan arama sonuçlarına dahil edilen Dışarı Aktarma Özeti raporunda, daha önce açıklandığı gibi tahmini 1.000 öğe ve indirilen öğelerden 1.000 öğe listeleniyor olabilir. 

- Sonuçları dışarı aktarmış olduğunuz arama, kurumdaki belirli içerik konumlarında veya tüm içerik konumlarında yapılan bir arama ise, yalnızca içerik konumlarından arama ölçütleriyle uyan öğelerin bulunduğu kısmi öğeler dışarı aktarıldı. Başka bir deyişle, bir posta kutusunda veya sitede hiç arama sonucu bulunamıyorsa, bu posta kutusu veya sitedeki kısmen dizine alınan öğelerden herhangi biri dışarı aktar olmaz. Bunun nedeni, kuruluşta birçok konumdan kısmen dizine alındı olarak dizine alan öğelerin dışarı aktarma işlemi, dışarı aktarma hataları olasılığını artırabilir ve arama sonuçlarını dışarı aktarma ve indirme için gereken zamanı artıracaktır.

    Kısmen dizine alınan öğeleri aramanın tüm içerik konumlarından dışarı aktarmak için, aramanızı tüm öğeleri sonuç olarak (arama sorgusundan anahtar sözcükleri kaldırarak) geri dönecek şekilde yapılandırın ve ardından arama sonuçlarını dışarı aktarıldığında yalnızca kısmen dizine alınan öğeleri dışarı aktarın.

    ![Yalnızcainde olmayan öğeleri dışarı aktarmak için üçüncü dışarı aktarma seçeneğini kullanın.](../media/5d7be338-a0e5-425f-8ba5-92769c24bf75.png)
  
- SharePoint veya OneDrive İş sitelerinden arama sonuçlarını dışarı aktarıyorsanız dizine eksiz öğeleri dışarı aktarma özelliği, seçtiğiniz dışarı aktarma seçeneğine ve arama yapılan bir sitenin arama ölçütleriyle eşleşen dizine alınan bir öğe içerdiğine de bağlıdır. Örneğin, belirli SharePoint veya OneDrive İş sitelerinde arama yaptıysanız ve hiç arama sonucu bulunamıyorsanız, hem dizinli hem de dizine eksiz öğeleri dışarı aktarmayı seçerseniz bu sitelerden dizinelanmamış hiçbir öğe dışarı aktarılamaz. Siteden dizine alınan bir öğe arama ölçütleriyle eş yoksa, hem dizine alınan hem de dizine eksiz öğeler dışarı aktarıldında bu sitedeki dizine eksiz tüm öğeler dışarı aktarıldı. Aşağıdaki çizimde, bir sitenin arama ölçütlerine uyan dizine alınan bir öğe içerdiğine bağlı olarak dışarı aktarma seçenekleri açık bulunmaktadır.

    ![Bir sitenin, arama ölçütleriyle eşleşen dizine alınan bir öğe içerdiğine bağlı olarak dışarı aktarma seçeneğini belirtin.](../media/94f78786-c6bb-42fb-96b3-7ea3998bcd39.png)

    a. Yalnızca arama ölçütlerine uyan dizine alındı öğeler dışarı aktarıldı. Kısmen dizine alındı öğe dışarı aktarıldı.

    b. Bir sitedeki dizine alınan hiçbir öğe arama ölçütleriyle eş zamana uygunsa, aynı siteden kısmen dizine alınan öğeler dışarı aktar aktarnmaz. Siteden dizine alınan öğeler arama sonuçlarında döndürülürse, bu siteden kısmen dizine alınan öğeler dışarı aktarıldı. Başka bir deyişle, yalnızca arama ölçütlerine uyan öğeler içeren sitelerden kısmen dizine alınan öğeler dışarı aktarıldı.

    c. Bir sitenin arama ölçütleriyle eşleşmesi ne olursa olsun, aramadaki tüm sitelerden kısmen dizine alınan öğelerin hepsi dışarı aktarıldı.

    Kısmen dizine alan öğeleri dışarı aktarmayı seçerseniz, Kısmen dizine alan posta kutusu öğeleri, Öğeleri dışarı aktarma altında seçtiğiniz seçenek ne olursa olsun ayrı **bir PST Exchange dışarı aktar.**

- Kısmen dizine alınan öğeler arama sonuçlarında döndürülürse (kısmen dizine alınan öğelerin diğer özellikleri arama ölçütleriyle eşli olduğundan), kısmen dizine alınan öğeler normal arama sonuçlarıyla dışarı aktarıldı. Dolayısıyla, hem dizine alınan öğeleri hem de kısmen dizine alınan öğeleri dışarı aktarmayı seçerseniz (tanınmayan  biçime sahip olanlar, şifrelenmiş veya başka nedenlerle dizine eklenmemiş öğeler de içinde olmak üzere) Tüm öğeler'i seçerek), normal sonuçlarla birlikte kısmen dizine alınan öğeler Results.csv raporunda listelenir. Bunlar, Tekin olmayan alan items.csv.
  
### <a name="exporting-individual-messages-or-pst-files"></a>Tek tek iletileri veya PST dosyalarını dışarı aktarma
  
- İletinin dosya yolu adı, bir iletinin en yüksek karakter Windows aşarsa, dosya yolu adı kesilir. Ancak özgün dosya yolu adı Bildirim ve ResultsLog'ta listelenir.
  
- Daha önce de belirtildiği gibi, e-posta arama sonuçları dosya sistemideki bir klasöre dışarı aktarıldı. Tek tek iletilerin klasör yolu, kullanıcının posta kutusunda klasör yolunu çoğaltılabilir. Örneğin, bir kullanıcının gelen kutusunda bulunan "ContosoCase101" adlı bir arama için klasör yolu bulunur  `~ContosoCase101\\<date of export\Exchange\user@contoso.com (Primary)\Top of Information Store\Inbox`.

- E-posta iletilerini tek bir klasördeki tüm iletileri içeren bir PST dosyasında dışarı aktarmayı seçerseniz, bir  Silinmiş Öğeler klasörü ve Arama  Klasörleri klasörü PST klasörünün en üst düzeyinde yer alır. Bu klasörler boştur.

- Daha önce de belirtildiği gibi, dışarı aktarıldıklarına RMS korumalı iletilerin şifresini çözmek için e-posta arama sonuçlarını tek tek iletiler olarak dışarı aktarmanız gerekir. E-posta arama sonuçlarını bir PST dosyası olarak dışarı aktarırsanız, şifrelenmiş iletiler şifrelenir.
  
### <a name="decrypting-rms-protected-email-messages-and-encrypted-file-attachments"></a>RMS korumalı e-posta iletilerinin ve şifreli dosya eklerin şifresini çözme

İçerik arama sonuçlarına dahil edilen hak korumalı (RMS korumalı) e-posta iletilerinin şifresini çözebilirsiniz. Buna ek olarak, [Microsoft](encryption.md) şifreleme teknolojisiyle şifrelenen ve arama sonuçlarına eklenmiş bir e-posta iletisine eklenen tüm dosyalar, dışarı aktarıldıklarında da şifreleri çözüler. eBulma Yöneticisi rol grubunun üyeleri için bu şifre çözme özelliği varsayılan olarak etkindir. Bunun nedeni, RMS Şifre Çözme yönetimi rolüne varsayılan olarak bu rol grubuna atanmıştır. Şifreli e-posta iletilerini ve ekleri dışarı aktarmada aşağıdakini göz unutmayın:
  
- Daha önce de belirtildiği gibi, RMS korumalı iletileri dışarı aktarsanız bile, arama sonuçlarını tek tek iletiler olarak dışarı aktarmanız gerekir. Arama sonuçlarını bir PST dosyasına dışarı aktarırsanız, RMS korumalı iletiler şifrelenmiş olarak kalır.

- Şifresini çözülmüş iletiler **ResultsLog raporunda** tanımlanır. Bu raporda Kod Çözme Durumu adlı **bir sütun vardır** ve bu sütundaki Kod  Çözme değeri, şifresini çözmüş iletileri tanımlar.

- Arama sonuçlarını dışarı aktararak dosya eklerin şifresini çözmenin yanı sıra, arama sonuçlarının önizlemesini görüntülerken şifresi çözülen dosyanın önizlemesini de görüntüde görebilirsiniz. Hak korunan e-posta iletisi, ancak dışarı aktar olduktan sonra iletiyi görüntüebilirsiniz.

- Şu anda, arama sonuçlarını dışarı aktarma işlemi şifre çözme özelliği SharePoint veya OneDrive İş içermemektedir. Öte yandan, Microsoft şifreleme teknolojileriyle şifrelenmiş, SharePoint Online ve OneDrive İş'de depolanan belgeler için yakında destek OneDrive İş.

- Birinin RMS ile koruma iletilerinin ve şifreli dosya eklerinin şifresini çözmesini önlemeye gerek varsa, özel bir rol grubu oluşturmanız (yerleşik eBulma Yöneticisi rol grubunu kopyalayıp) ve ardından RMS Şifre Çözme yönetimi rolünü özel rol grubundan kaldırmanız gerekir. Ardından, iletilerin şifresini çözmek istediğiniz kişiyi özel rol grubunun bir üyesi olarak ekleyin.
  
### <a name="filenames-of-exported-items"></a>Dışarı aktarıldı öğelerin dosya adı
  
- Yerel bilgisayarınıza dışarı aktarılan e-posta iletileri ve site belgeleri için tam yol adı için 260 karakterlik bir sınır vardır (işletim sistemi tarafından dayatılan). Dışarı aktarıldı öğeler için tam yol adı, öğenin özgün konumunu ve arama sonuçlarının indirilir yerel bilgisayarda bulunduğu klasör konumunu içerir. Örneğin, eBulma  `C:\Users\Admin\Desktop\SearchResults` Dışarı Aktarma aracında arama sonuçlarını indirmeyi belirtirsiniz, indirilen e-posta öğesinin tam yol adı olabilir  `C:\Users\Admin\Desktop\SearchResults\ContentSearch1\03.15.2017-1242PM\Exchange\sarad@contoso.com (Primary)\Top of Information Store\Inbox\Insider trading investigation.msg`.

- 260 karakterlik sınır aşılırsa, öğenin tam yol adı aşağıdakilere göre kesilir:

  - Tam yol adı 260 karakterden daha uzunsa, dosya adı sınırın altına inecek şekilde kısaltılacaktır; Kesilmiş dosya adı (dosya uzantısı hariç) sekiz karakterden az olmayacak.

  - Dosya adı kısaltılan tam yol adı yine de fazla uzunsa, öğe geçerli konumdan üst klasöre taşınır. Yol adı hala fazla uzunsa, işlem yinelenir: dosya adını kısaltın ve gerekirse üst klasöre yeniden gidin. Tam yol adı 260 karakter sınırının altına inene kadar bu işlem yinelenir.

  - Kesilmiş bir tam yol adı zaten varsa, dosya adının sonuna bir sürüm numarası eklenir; örneğin, `statusmessage(2).msg`.

    Bu sorunu azaltmak için, arama sonuçlarını kısa yol adına sahip bir konuma indirmeyi düşünebilirsiniz; örneğin, adlı bir klasöre  `C:\Results` arama sonuçlarının indirnerek dışarı aktarilen öğelerin yol adlarına, bu karakterleri adlı klasöre indirmekten daha az karakter ekler  `C:\Users\Admin\Desktop\Results`.

- Site belgelerini dışarı aktarsanız, belgenin özgün dosya adının da değiştirilebilir olması mümkündür. Bu durum özellikle yerinde SharePoint veya OneDrive İş yerinde silinmiş belgeler için gerçekleşir. Sitede saklamaya devam olan bir belge silindikten sonra, silinen belge otomatik olarak sitenin Saklama Kitaplığı'ne taşınır (site yerinde saklamaya geldiğinde oluşturulmuştur). Silinen belge Saklama kitaplığına taşındığında, rastgele oluşturulan ve benzersiz bir kimlik belgenin özgün dosya adının sonuna eklenir. Örneğin, bir  `FY2017Budget.xlsx` belgenin dosya adı varsa ve bu belge daha sonra silindikten sonra Saklama Kitaplığı'ne taşınırsa, Saklama Saklama kitaplığına taşınan belgenin dosya adı gibi bir adla değiştirilir  `FY2017Budget_DEAF727D-0478-4A7F-87DE-5487F033C81A2000-07-05T10-37-55.xlsx`. Saklama Kitaplığı'nda yer alan bir belge İçerik arama sorgusunu eşler ve bu aramanın sonuçlarını dışarı aktarırsanız, dışarı aktaran dosyada değiştirilmiş dosya adı vardır; bu örnekte, dışarı aktaran belgenin dosya adı .`FY2017Budget_DEAF727D-0478-4A7F-87DE-5487F033C81A2000-07-05T10-37-55.xlsx`

    Yerinde saklama olan bir belge değiştirildiğinde (ve site'de belge kitaplığının sürüm oluşturma özelliği etkinleştirildiğinde), Dosyanın bir kopyası Saklama kitaplığında otomatik olarak oluşturulur. Bu durumda, Rastgele oluşturulan ve benzersiz bir kimlik, Saklama Kitaplığı'nın kopyalanan belge dosya adının sonuna eklenir.

    Saklama kitaplığına taşınan veya kopyalanan belgelerin dosya adlarının çakışmasını önlemek, bu dosya adlarının çakışmasını önlemektir. Sitelerde ve Koruma Saklama kitaplığında yerinde saklama hakkında daha fazla bilgi için bkz. [SharePoint Server 2016'da](https://support.office.com/article/5e400d68-cd51-444a-8fe6-e4df1d20aa95) yerinde saklamaya genel bakış.

### <a name="miscellaneous"></a>Diğer
  
- eBulma Dışarı Aktarma Aracı'nı kullanarak arama sonuçlarını indirirken, şu hatayı alabilirsiniz: `System.Net.WebException: The remote server returned an error: (412) The condition specified using HTTP conditional header(s) is not met.` Bu geçici bir hatadır ve genellikle Azure Veri Merkezi Depolama gerçekleşir. Bu sorunu çözmek için arama [sonuçlarını indirmeyi yeniden deneyin](#step-2-download-the-search-results); bu da eBulma Dışarı Aktarma Aracı'nı yeniden başlatacak.

- Tüm arama sonuçları ve dışarı aktarma raporları, İçerik arama ile aynı adı içeren bir klasöre kaydedilir. Dışarı aktarıldı e-posta iletileri İletiler adlı bir **Exchange**. Belgeler, Belgeler adlı bir klasörde **SharePoint**.

- Belgeler yerel bilgisayarınıza dışarı aktarıldı SharePoint OneDrive İş belgeler için dosya sistemi meta verileri korunur. Bu, belgeler dışarı aktarıldıktan sonra oluşturulma ve son değiştirme tarihleri gibi belge özelliklerinin değiştirilmez olduğu anlamına gelir.

- Arama sonuçlarınız SharePoint'dan gelen ve arama sorgusuyla eşleşen bir liste öğesi içerirse, arama sorgusuyla ve liste ekleri ile eşleşen öğenin yanı sıra, listede yer alan tüm satırlar da dışarı aktarıldı. Bu davranışın nedeni, arama sonuçlarında döndürülen liste öğeleri için bir bağlam sağlamaktır. Ek liste öğeleri ve ekler, dışarı aktaran öğelerin sayısını arama sonuçlarının ilk tahmininden farklı olabilir.
