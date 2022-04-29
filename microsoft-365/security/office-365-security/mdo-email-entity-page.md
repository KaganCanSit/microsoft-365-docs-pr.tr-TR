---
title: Office 365 için Microsoft Defender e-posta varlığı sayfası
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 04/01/2022
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.technology: mdo
ms.localizationpriority: medium
search.appverid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Office 365 için Microsoft Defender E5, P1 ve P2 müşterileri artık e-posta varlık sayfasıyla her e-postanın 360 derecelik görünümünü alabilir.
ms.openlocfilehash: c2dfd4016f756073407e7d1c22034031c60a901f
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131096"
---
# <a name="the-email-entity-page"></a>E-posta varlığı sayfası

**Bu makalede:**
- [E-posta varlığı sayfasına ulaşma](#reach-the-email-entity-page)
- [E-posta varlık sayfasını okuma](#read-the-email-entity-page)
- [E-posta varlığı sayfa sekmelerini kullanma](#use-email-entity-page-tabs)
- [E-posta varlığı sayfasında yeni](#new-to-the-email-entity-page)

Office 365 için Microsoft Defender E5 ve Office P1 ve P2 için Defender yöneticileri, **E-posta varlığı sayfasını** kullanarak e-postanın 360 derecelik bir görünümüne sahiptir. Bu e-postaya gitme sayfası [, Tehdit Gezgini 'e-posta ayrıntıları' açılır](threat-explorer-views.md) penceresinde sunulan bilgileri geliştirmek için oluşturulmuştur.

## <a name="reach-the-email-entity-page"></a>E-posta varlığı sayfasına ulaşma

E-posta varlığı sayfası, Microsoft 365 Defender portalında **E-posta & işbirliği** \> **Gezgini'nde**<https://security.microsoft.com> bulunabilir. Veya doğrudan **Gezgin** sayfasına gitmek için kullanın <https://security.microsoft.com/threatexplorer>.

**Gezgin'de**, araştırdığınız e-postanın konusunu seçin. Bu posta için açılan e-postanın üst kısmında altın renkli bir çubuk görüntülenir. Yeni sayfaya gönderilen bu davette "Zenginleştirilmiş verilerle yeni e-posta varlığı sayfamızı deneyin..." ifadesi yer alır. Yeni sayfayı görüntülemek için öğesini seçin.

:::image type="content" source="../../media/email-entities-1-navigation-to-ee.png" alt-text="Yeni deneyime gitmek için *Zenginleştirilmiş verilerle yeni e-posta varlık sayfamızı deneyin* sözcüklerini içeren altın renkli başlık" lightbox="../../media/email-entities-1-navigation-to-ee.png":::

:::image type="content" source="../../media/email-entities-2-eep.png" alt-text="Göreceğiniz başlıklara odaklanan e-posta varlığı sayfasının grafiği" lightbox="../../media/email-entities-2-eep.png":::

> [!NOTE]
> Bu sayfayı görüntülemek ve kullanmak için gereken izinler **, Gezgin'i** görüntülemek için gereken izinlerle aynıdır. Yöneticinin Genel yönetici veya genel okuyucu ya da Güvenlik yöneticisi ya da Güvenlik Okuyucusu üyesi olması gerekir. Daha fazla bilgi için bkz. [Microsoft 365 Defender portalında İzinler](permissions-microsoft-365-security-center.md).

## <a name="read-the-email-entity-page"></a>E-posta varlık sayfasını okuma

Yapı, bir bakışta okunması ve gezinmesi kolay olacak şekilde tasarlanmıştır. Sayfanın üst kısmındaki çeşitli sekmeler, daha ayrıntılı araştırma yapmanızı sağlar. Düzen şu şekilde çalışır:

1. En gerekli alanlar, açılır çubuğun sol tarafındadır. Bu ayrıntılar "yapışkandır", yani açılır ögenin geri kalanında hangi sekmeye giderseniz gidin sola sabitlenirler.

    :::image type="content" source="../../media/email-entities-3-left-panel.png" alt-text="Sol tarafı vurgulanmış e-posta varlığı sayfasının Grafiği" lightbox="../../media/email-entities-3-left-panel.png":::

2. Sağ üst köşede bir e-postada gerçekleştirilebilecek eylemler bulunur. **Gezgin** aracılığıyla gerçekleştirilebilecek tüm eylemler e-posta varlık sayfası aracılığıyla da kullanılabilir.

    :::image type="content" source="../../media/email-entities-5-preview.png" alt-text="Sağ tarafı vurgulanmış e-posta varlığı sayfasının Grafiği" lightbox="../../media/email-entities-5-preview.png":::

3. Sayfanın geri kalanında sıralama yaparak daha ayrıntılı analiz yapılabilir. E-posta algılama ayrıntılarını, e-posta kimlik doğrulama durumunu ve üst bilgiyi denetleyin. Bu alana büyük/küçük harf temelinde bakılmalıdır, ancak bu sekmelerdeki bilgiler herhangi bir e-posta için kullanılabilir.

    :::image type="content" source="../../media/email-entities-4-middle-panel.png" alt-text="E-posta üst bilgisini ve kimlik doğrulama durumunu içeren sayfanın ana paneli" lightbox="../../media/email-entities-4-middle-panel.png":::

### <a name="use-email-entity-page-tabs"></a>E-posta varlığı sayfa sekmelerini kullanma

Varlık sayfasının üst kısmındaki sekmeler, e-postayı verimli bir şekilde araştırmanıza olanak sağlar.

1. **Zaman Çizelgesi**: E-postanın zaman çizelgesi görünümü ( **Gezgin** zaman çizelgesi başına), bir e-postada gerçekleşen teslim sonrası olaylara özgün teslimi gösterir. Teslim sonrası eylemleri olmayan e-postalar için görünüm, zaman çizelgesi görünümünde özgün teslim satırını gösterir. Şunun gibi olaylar: Sıfır saatlik otomatik temizleme (ZAP), Düzeltme, URL tıklamaları, vb. gibi kaynaklardan: sistem, yönetici ve kullanıcı, burada, oluştukları sırada gösterilir.
2. **Analiz**: Analiz, yöneticilerin bir e-postayı derinlemesine analiz etmelerine yardımcı olan alanları gösterir. Yöneticilerin algılama, gönderen/alıcı ve e-posta kimlik doğrulaması ayrıntıları hakkında daha fazla bilgi sahibi olması gereken durumlarda Çözümleme sekmesini kullanmaları gerekir. Ekler ve URL'ler için bağlantılar da bu sayfada, 'İlgili Varlıklar' altında bulunur. Hem ekler hem de tanımlanan tehditler burada numaralandırılır ve tıklama sizi doğrudan Ekler ve URL sayfalarına götürür. Bu sekmede, *e-posta üst bilgisini gösteren bir Üst bilgiyi görüntüle* seçeneği de vardır. Yöneticiler, netlik için e-posta üst bilgilerinden gelen tüm ayrıntıları ana paneldeki bilgilerle yan yana karşılaştırabilir.
3. **Ekler**: Bu, e-postada bulunan ekleri inceler ve eklerde bulunan diğer ayrıntıları içerir. Gösterilen ek sayısı şu anda 10 ile sınırlıdır. Kötü amaçlı olduğu belirlenen eklerin patlama ayrıntılarının da burada gösterildiğine dikkat edin.
4. **URL'ler**: Bu sekme, e-postada bulunan URL'leri ve URL'lerle ilgili diğer ayrıntıları listeler. URL sayısı şu anda 10 ile sınırlıdır, ancak önce *kötü amaçlı URL'lerin* gösterilmesi için bu 10'un önceliği belirlenmiştir. Öncelik belirleme size zaman ve tahmin çalışması kazandırır. Kötü amaçlı olduğu ve patlatıldığı belirlenen URL'ler de burada gösterilir.
5. **Benzer e-postalar**: Bu sekmede, bu e-postaya özgü *ağ ileti kimliği + alıcı* bileşimine benzer tüm e-postalar listelenir. Benzerlik yalnızca *iletinin gövdesini* temel alır. Postaları 'benzer' olarak kategorilere ayırmak için yapılan *belirlemeler ekleri* dikkate almaz.

## <a name="new-to-the-email-entity-page"></a>E-posta varlığı sayfasında yeni

Bu e-posta varlık sayfasıyla birlikte gelen yeni özellikler vardır. Liste burada.

### <a name="email-preview-for-cloud-mailboxes"></a>Bulut posta kutuları için e-posta önizlemesi

E-postalar bulutta hala ***mevcutsa*** yöneticiler Bulut posta kutularında e-postaların önizlemesini görebilir. Geçici silme (yönetici veya kullanıcı tarafından) veya ZAP (karantinaya almak için) durumunda e-postalar artık Bulut konumunda bulunmaz. Bu durumda, yöneticiler bu belirli postaların önizlemesini göremez. Bırakılan veya teslimin başarısız olduğu e-postalar hiçbir zaman posta kutusuna giremedi. Sonuç olarak, yöneticiler de bu e-postaların önizlemesini göremez.

> [!WARNING]
> E-postaların önizlemesi için **Önizleme** adlı özel bir rol gerekir. Bu rolü Microsoft 365 Defender portalındaki [E-posta & işbirliği rollerinde açıklandığı gibi Microsoft 365 Defender portalına](permissions-microsoft-365-security-center.md#email--collaboration-roles-in-the-microsoft-365-defender-portal) ekleyebilirsiniz. Burada yeni bir **E-posta & işbirliği** rol grubu oluşturmanız ve **Önizleme** rolünü bu yeni rol grubuna eklemeniz veya **Önizleme rolünü** kuruluşunuzdaki yöneticilerin **Explorer'da** çalışmasına izin veren bir rol grubuna eklemeniz gerekebilir.

### <a name="detonation-details"></a>Patlama ayrıntıları

Bu ayrıntılar e-posta eklerine ve URL'lere özeldir. Kullanıcılar, Gezgin'e gidip *algılama teknolojisi* filtre kümesini dosya açma veya URL patlamalarına uygulayarak bu ayrıntıları görebilir. Dosya açma için filtrelenen e-postalar, patlama ayrıntılarını içeren kötü amaçlı bir dosya içerir ve URL'ler için filtrelenenler kötü amaçlı bir URL ve patlama ayrıntılarını içerir.

Kullanıcılar, e-postalarında bulunan ve belirli bir kiracı için patlatılan bilinen kötü amaçlı eklerin veya URL'lerin zenginleştirilmiş patlama ayrıntılarını görür. Müşterilerin ekin veya URL'nin neden kötü amaçlı olarak kabul edildiği ve patlatıldığını anlamasına yardımcı olmak için Patlama zinciri, Patlama özeti, Ekran Görüntüsü ve Gözlemlenen davranış ayrıntılarını içerir.

1. *Patlama zinciri*. Tek bir dosya veya URL'nin patlatılması birden çok patlamayı tetikleyebilir. Patlama zinciri, karara neden olan özgün kötü amaçlı dosya veya URL ve patlamadan etkilenen diğer tüm dosyalar veya URL'ler de dahil olmak üzere patlamaların yolunu izler. Bu URL'ler veya ekli dosyalar doğrudan e-postada bulunmayabilir, ancak bu çözümleme dahil olmak, dosyanın veya URL'nin neden kötü amaçlı olduğunu belirlemek için önemlidir.  

    > [!NOTE]
    > Bu, bağlantılı varlıkların hiçbirinin sorunlu bulunmamış veya patlatılmış olması durumunda yalnızca en üst düzey öğeyi gösterebilir.

1. *Patlama Özeti* , *analiz zamanı*, patlamanın gerçekleştiği zaman, işletim sistemi ve uygulama, patlamanın oluştuğu işletim sistemi ve uygulama, dosya boyutu ve karar nedeni gibi patlama için temel bir özet sağlar.
1. *Ekran görüntüleri* , patlama sırasında yakalanan ekran görüntülerini gösterir. Patlama sırasında birden çok ekran görüntüsü olabilir. için ekran görüntüsü yakalanmaz
    - .zip veya .rar gibi kapsayıcı türü dosyaları.
    - Url doğrudan dosya indiren bir bağlantıda açılırsa. Ancak indirilen dosyayı patlama zincirinde görürsünüz.
1. *Davranış Ayrıntıları* , patlama sırasında gerçekleşen tam olaylar gibi davranış ayrıntılarını ve patlama sırasında bulunan URL'ler, IP'ler, etki alanları ve dosyalar içeren gözlemlenebilir öğeler (ve sorunlu veya zararsız olabilir) gösteren bir dışarı aktarma işlemidir. Aşağıdakiler için hiçbir davranış ayrıntısı bulunmadığını unutmayın:
    - Diğer dosyaları tutan .zip veya .rar gibi kapsayıcı dosyaları.

:::image type="content" source="../../media/email-entities-6-detonation-page.png" alt-text="*Derin Analiz* başlığı altında zinciri, özeti, patlama ayrıntılarını ve ekran görüntüsünü gösteren patlama özeti" lightbox="../../media/email-entities-6-detonation-page.png":::

### <a name="other-innovations"></a>Diğer yenilikler

*Etiketler*: Bunlar kullanıcılara uygulanan etiketlerdir. Kullanıcı alıcıysa, yöneticiler bir *alıcı* etiketi görür. Benzer şekilde, kullanıcı bir gönderense, *gönderen* etiketidir. Bu, e-posta varlıkları sayfasının sol tarafında görünür ( *yapışkan* olarak tanımlanan ve bu nedenle sayfaya tutturulmuş kısımda).

*En son teslim konumu*: En son teslim konumu, ZAP gibi sistem eylemlerini veya Silinmiş Öğelere Taşı, son gibi yönetici eylemlerini tamamladıktan sonra e-postanın geldiği konumdur. En son teslim konumu, yöneticileri iletinin *geçerli* konumu hakkında bilgilendirmek için tasarlanmamıştır. Örneğin, bir kullanıcı iletiyi silerse veya arşive taşırsa, teslim konumu güncelleştirilmez. Ancak, bir sistem eylemi gerçekleştirilip konumu güncelleştirmişse (örneğin, karantinaya alınan bir e-postanın karantinaya alınmasına neden olan ZAP gibi) bu işlem karantinaya almak için en son teslim konumunu güncelleştirir.

*E-posta ayrıntıları*: *Analiz* sekmesinde bulunan e-postayı daha ayrıntılı anlamak için gereken ayrıntılar.

- *Exchange aktarım kuralları (posta akışı kuralları veya ETR'ler olarak da bilinir):* Bu kurallar aktarım katmanındaki bir iletiye uygulanır ve kimlik avı ve istenmeyen posta kararlarından önceliklidir. Posta akışı kuralları, konumundaki Exchange yönetim merkezinde <https://admin.exchange.microsoft.com/#/transportrules>oluşturulur ve değiştirilir, ancak iletiye herhangi bir posta akışı kuralı uygulanırsa, kural adı ve GUID burada gösterilir. İzleme amacıyla değerli bilgiler.

- *Birincil Geçersiz Kılma: Kaynak:* Birincil geçersiz kılma ve kaynak, e-postanın teslimini etkileyen ve sistem tarafından verilen teslim konumunu geçersiz kılan kiracı veya kullanıcı ayarına (tehdit ve algılama teknolojisine göre) başvurur. Örneğin, kiracı tarafından yapılandırılmış aktarım kuralı nedeniyle engellenen bir e-posta veya Kasa Gönderenler için son kullanıcı ayarı nedeniyle izin verilen bir e-posta olabilir. 

- *Tüm Geçersiz Kılmalar*: Tüm Geçersiz Kılmalar, e-postaya uygulanmış olan ve e-postanın teslimini etkileyebilecek veya etkilememiş olabilecek geçersiz kılmaların (kiracı veya kullanıcı ayarları) listesine başvurur. Örneğin, kiracı tarafından yapılandırılmış taşıma kuralının yanı sıra kiracı tarafından yapılandırılmış bir ilke ayarı (örneğin, Kiracı İzin Verme Engelleme listesinden) bir e-postaya uygulanırsa, her ikisi de bu alanda listelenir. E-postanın teslimini etkileyen ayarı belirlemek için birincil geçersiz kılma alanını de kontrol edebilirsiniz. 

- *Toplu Şikayet Düzeyi (BCL)*: İletinin toplu şikayet düzeyi (BCL). Daha yüksek bir BCL, toplu posta iletisinin şikayet oluşturma olasılığının daha yüksek olduğunu belirtir (e-postanın istenmeyen posta olma olasılığı varsa doğal sonuç).

- *İstenmeyen Posta Güvenilirlik Düzeyi (SCL):* İletinin istenmeyen posta güvenilirlik düzeyi (SCL). Daha yüksek bir değer, iletinin istenmeyen posta olma olasılığının daha yüksek olduğunu gösterir.

- *İstemci türü*: E-postanın REST gibi gönderildiği İstemci türünü gösterir.

- *İletme*: Autoforwaridng içeren senaryolar için, iletme kullanıcısının yanı sıra ETR veya SMTP iletme gibi iletme türünü gösterir. 

- *Dağıtım listesi*: Alıcı e-postayı listenin bir üyesi olarak aldıysa dağıtım listesini gösterir. İç içe dağıtım listeleri varsa en üst düzey dağıtım listesini gösterir.  

- *Kime, Bilgi*: E-postanın Kime, Bilgi alanlarında listelenen adresleri gösterir. Bu alanlardaki bilgiler 5000 karakterle sınırlıdır. 

- *Etki Alanı Adı*: Gönderen etki alanı adıdır.

- *Etki Alanı Sahibi*: Gönderen etki alanının sahibini belirtir.

- *Etki Alanı Konumu*: Gönderen etki alanının konumunu belirtir.

- *Etki Alanı Oluşturma Tarihi*: Gönderen etki alanının oluşturulma tarihini belirtir. Yeni oluşturulan bir etki alanı, diğer sinyaller bazı şüpheli davranışları gösteriyorsa dikkatli olabileceğiniz bir şeydir.

*E-posta Kimlik Doğrulaması*: Microsoft 365 tarafından kullanılan e-posta kimlik doğrulama yöntemleri SPF, DKIM ve DMARC'yi içerir.

- Sender Policy Framework (**SPF**): İleti için SPF denetiminin sonuçlarını açıklar. Olası değerler:
  - Geçiş (IP adresi): Geçirilen ileti için SPF denetimi ve gönderenin IP adresini içerir. İstemci, gönderenin etki alanı adına e-posta gönderme veya aktarma yetkisine sahip.
  - Başarısız (IP adresi): İleti için SPF denetimi başarısız oldu ve gönderenin IP adresini içerir. Bu bazen zor başarısız olarak adlandırılır.
  - Geçici yazılım (neden): SPF kaydı konağı göndermesine izin verilmediğini ancak geçişte olduğunu belirledi.
  - Nötr: SPF kaydı açıkça IP adresinin gönderme yetkisi olup olmadığını onaylamadığını belirtir.
  - Yok: Etki alanının SPF kaydı yok veya SPF kaydı bir sonuç olarak değerlendirilmez.
  - Temperror: Geçici bir hata oluştu. Örneğin, bir DNS hatası. Aynı denetim daha sonra başarılı olabilir.
  - Permerror: Kalıcı bir hata oluştu. Örneğin, etki alanının hatalı biçimlendirilmiş bir SPF kaydı vardır.

- DomainKeys Tanımlanan Posta (**DKIM**):
  - Geçiş: Geçirilen ileti için DKIM denetimini gösterir.
  - Başarısız (neden): İleti için DKIM denetiminin başarısız olduğunu ve nedenini gösterir. Örneğin, ileti imzalanmamışsa veya imza doğrulanmamışsa.
  - Yok: İletinin imzalanmadığını gösterir. Bu, etki alanının DKIM kaydı olduğunu veya DKIM kaydının bir sonuç olarak değerlendirilmediğini, yalnızca bu iletinin imzalanmadığını gösterebilir veya göstermeyebilir.

- Etki Alanı Tabanlı İleti Kimlik Doğrulaması, Raporlama ve Uyumluluk (**DMARC**):
  - Geçiş: Geçirilen ileti için DMARC denetimini gösterir.
  - Başarısız: İleti için DMARC denetiminin başarısız olduğunu gösterir.
  - Bestguesspass: Etki alanı için DMARC TXT kaydı olmadığını gösterir, ancak varsa, ileti için DMARC denetimi geçirilirdi.
  - Yok: DNS'de gönderen etki alanı için DMARC TXT kaydı olmadığını gösterir.

*Bileşik Kimlik Doğrulaması*: bu, Microsoft 365 tarafından iletinin doğru olup olmadığını belirlemek üzere SPF, DKIM ve DMARC gibi e-posta kimlik doğrulamasını birleştirmek için kullanılan bir değerdir. Değerlendirmenin temeli olarak postanın *Kimden:* etki alanını kullanır.

### <a name="email-summary-panel"></a>E-posta özet paneli

E-posta özeti paneli, tam e-posta varlık sayfasının özetlenmiş bir görünümüdür. E-posta (örneğin algılamalar) hakkında standartlaştırılmış ayrıntıların yanı sıra bağlama özgü bilgiler (örneğin, Karantina veya Gönderimler meta verileri için) içerir. E-posta özeti paneli geleneksel Gerçek Zamanlı Algılamalar, Tehdit Gezgini, Gönderimler ve Raporlama açılır bileşenlerinin yerini alır.

> [!div class="mx-imgBorder"]
> ![E-posta varlığı bağlantısını açın.](../../media/open-email-entity-mdo.png)

> [!NOTE]
> Tüm bileşenleri görüntülemek için **E-posta varlığını aç** bağlantısına tıklayarak tam e-posta varlığı sayfasını açın.  

E-posta özet paneli aşağıdaki bölümlere ayrılmıştır:  

- *Teslim ayrıntıları: Tehditler* ve buna karşılık gelen güvenilirlik düzeyi, algılama teknolojileri ve özgün ve en son teslim konumu hakkında bilgi içerir.

- *E-posta ayrıntıları*: Gönderen adı, gönderen adresi, alınan süre, kimlik doğrulama ayrıntıları ve diğer birçok diğer ayrıntı gibi e-posta özellikleri hakkında bilgi içerir.

- *URL'ler*: Varsayılan olarak, 3 URL ve karşılık gelen tehditlerini görürsünüz. **Tüm URL'leri** genişletip görmek ve dışarı aktarmak için istediğiniz zaman Tüm URL'leri görüntüle'ye tıklayabilirsiniz.  

- *Ekler*: Varsayılan olarak 3 ek görürsünüz. Tüm ekleri genişletmek ve görmek için her zaman **Tüm ekleri görüntüle'ye** tıklayabilirsiniz. 

Yukarıdaki bölümlere ek olarak, özet paneliyle tümleştirilen birkaç deneyime özgü bölümler de görürsünüz: 

- Gönderi: 

    - *Gönderim ayrıntıları*: Belirli gönderimler hakkında aşağıdakiler gibi bilgiler içerir:
        - Gönderilme tarihi
        - Konu
        - Gönderim türü
        - Gönderme nedeni
        - Gönderim Kimliği
        - Gönderen

    - *Sonuç ayrıntıları*: Gönderilen iletiler gözden geçirilir. Gönderiminizin sonucunu ve önerilen sonraki adımları görebilirsiniz.

- Karantina:  

    - *Karantina ayrıntıları: Karantinaya* özgü ayrıntıları içerir. Daha fazla bilgi için bkz. [Karantinaya alınan iletileri yönetme](manage-quarantined-messages-and-files.md#view-quarantined-message-details).

        - Süre sonu: İletinin otomatik olarak silineceği ve karantinadan kalıcı olarak silineceği tarih/saat.
        - Yayın tarihi: İletinin yayımlandığı tüm e-posta adresleri (varsa).
        - Henüz yayımlanmadı: İletinin henüz yayımlanmadığı tüm e-posta adresleri (varsa).

    - *Karantina eylemleri*: Farklı karantina eylemleri hakkında daha fazla bilgi için bkz. [Karantinaya alınan iletileri yönetme](manage-quarantined-messages-and-files.md#take-action-on-quarantined-email).
