---
title: Insider risk yönetimi İçerik gezgini
description: Insider risk yönetimi Hakkında bilgi edinmek için Microsoft 365
keywords: Microsoft 365, insider risk yönetimi, risk yönetimi, uyumluluk
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: d60726b7fbf68ecbeb8af2d40c4c18e2bb9aaa7c
ms.sourcegitcommit: be074f57e33c811bb3857043152825209bc8af07
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "62988805"
---
# <a name="insider-risk-management-content-explorer"></a>Insider risk yönetimi İçerik gezgini

Insider risk yönetimi **İçerik gezgini** , uyarılarda etkinlikle ilişkilendirilmiş içeriğin bağlamını ve ayrıntılarını incelemek için *Insider Risk Yönetimi* Güvenlik Rolü'ne atanan kullanıcıların olanak sağlar. İçerik gezgininde olay verileri yeni etkinlikler eklemek için her gün yenilenir. Bir vakada onaylanan tüm uyarılar için, veri ve ileti dosyalarının kopyaları öğelerin zamanında anlık görüntü olarak arşivlenir ve bu sırada depolama kaynaklarında özgün dosyalar ve iletiler tutularak arşivlenir. Gerekirse, büyük/küçük harf veri dosyaları taşınabilir belge dosyası (PDF) olarak veya özgün dosya biçiminde dışarı aktarabilirsiniz.

Yeni durumlarda, genellikle içeriğin İçerik gezgini'nde doldurmak yaklaşık bir saat sürer. Çok fazla içerik olan durumlarda anlık görüntü oluşturmak daha uzun sürebilir. İçerik gezgininde hala içerik yükleniyorsa, tamamlanma yüzdesini gösteren bir ilerleme göstergesi görüntülenir.

Bazı durumlarda, bir vakayla ilişkilendirilmiş veriler İçerik Gezgini'nde gözden geçirme için anlık görüntü olarak kullanılamıyor olabilir. Bu durum, büyük/küçük harf verileri silindiğinde veya taşındığında ya da büyük/küçük harf verileri iş sürecinde geçici bir hata oluştuğunda oluşabilir. Bu durum oluşursa, dosya **adlarını** , dosya yolunu ve her dosyanın başarısızlığın nedenini görüntülemek için uyarı çubuğunda Dosyaları görüntüle'yi seçin. Gerekirse, bu bilgiler bir .csv (virgülle ayrılmış değerler) dosyasına aktarabilirsiniz.

İçerik Bilgi Hakları Yönetimi izinlerini de içerirse, kopyalanan içerik için bu izinler korunur ve *Insider Risk Management Atı'lara* Rol atanan kullanıcılar, dosyaları açmaları ve görüntülemeleri gerekirse bu izinlere ve haklara ihtiyaç yaşar. Yönetim amacıyla insider risk yönetimi durumunda her dosyaya ve iletiye otomatik olarak benzersiz bir dosya kimliği atanır. Cihaz göstergesi etkinlikleriyle ilişkili belgeler İçerik gezgininde yerlanmaz.

> [!NOTE]
> İçerik gezgini, Microsoft 365, Exchange, Microsoft Teams ve diğer sitelerde kullanıcı etkinliği gibi, SharePoint hizmet dosyalarıyla ilgili kullanıcı OneDrive İş.

## <a name="column-options"></a>Sütun seçenekleri

Risk analistleri ve güvenlik analistleri için yakalanan verileri ve iletileri gözden geçirmeyi ve durumu incelemeyi kolaylaştırmak için İçerik gezgininde çeşitli filtreleme ve sıralama araçları yer almaktadır. Temel sıralama için, **Tarih ve** **Dosya sınıf sütunları** içerik sırası bölmesindeki sütun başlıklarını kullanarak sıralamayı destekler. Dosyalar ve iletiler üzerinde farklı özetler sağlamak için, görünüme eklemek için diğer kuyruk sütunları kullanılabilir.

İçerik kuyruğuna sütun başlıkları eklemek veya kaldırmak için Sütunları düzenle **denetimine tıklayın** ve aşağıdaki sütun seçeneklerinden birini belirleyin. Bu sütunlar, İçerik gezgininde desteklenen ve bu makalenin sonraki sayfalarında listelenen ortak, e-posta ve belge özelliği koşullarıyla eşlenmiştir.

| **Sütun seçeneği** | **Açıklama** |
|:------------------|:----------------|
| **Yazar** | Belgelerden yazar Office alanı; belge kopyalanırsa kalıcı olur. Örneğin, bir kullanıcı belgeyi oluşturur ve bu belgeyi başka birine e-postayla gönderdikten sonra SharePoint, belge özgün yazarı korur. |
| **Gizli** | E-posta iletileri için, Gizli ileti alanında bulunan kullanıcılar tarafından kullanılabilir. |
| **Bilgi** | E-posta iletileri için, Bilgi ileti alanında bulunan kullanıcılar tarafından kullanılabilir. |
| **Bileşik yol** | Öğenin kaynağını açıklayan, insanlar tarafından okunabilir yol. |
| **Konuşma Kimliği** | İletiden Konuşma Kimliği. |
| **Konuşma dizini** | İletiden konuşma dizini. |
| **Oluşturulma zamanı** | Dosya veya e-posta iletisi oluşturma zamanı. |
| **Tarih (UTC)** | E-posta için, iletinin bir alıcı tarafından veya gönderen tarafından gönderildiği tarihtir. Belgeler için, belgenin son değiştirilma tarihidir. Tarih Eşgüdümli Evrensel Saat 'e (UTC) sahiptir.|
| **Baskın tema** | Analizler için hesaplanan olarak baskın tema. |
| **E-posta kümesi kimliği** | Aynı e-posta kümesinde yer alan tüm iletiler için grup kimliği. |
| **Aile Kimliği** | Aile Kimliği, tüm öğeleri bir araya gruplar; e-posta için bu sütun iletiyi ve tüm ekleri içerir; Belgeler için, bu sütun belgeyi ve ekli öğeleri içerir. |
| **Dosya sınıfı** | E-posta SharePoint OneDrive için: **Belge**; Exchange içeriği için: **E-posta** veya **Ek**. |
| **Dosya Kimliği** | Olay içindeki benzersiz belge tanımlayıcısı. |
| **Dosya türü simgesi** | Dosyanın uzantısı; örneğin, docx, one, pptx veya xlsx. Bu alan, FileExtension site özelliğiyle aynı özelliktir. |
| **Kimlik** | Dosyanın GUID tanımlayıcısı. |
| **Değişmez Kimlik** | Dosyada depolandığı gibi değişmez Office 365. |
| **Kapsayıcı tür** | Çözümleme için hesaplanan kapsayıcı tür: **0** - dahil değildir; **1** - dahil; **2** - dahil eksi; **3** - dahil kopya. |
| **Son değiştirme** | Belgenin son değiştir bitiş tarihi. |
| **Temsili olarak işaretlenmiş** | Her bir yineleme kümesinden bir belge temsilci olarak işaretlenir. |
| **İletinin tür** | Aranan e-posta iletisi türü. Olası değerler: kişiler, belgeler, e-posta, dış veriler, fakslar, im, günlükler, toplantılar, microsoft ekipleri (Microsoft Teams'ta sohbetlerden, toplantılardan ve aramalardan öğe döndürür), notlar, gönderiler, RSS akışları, görevler, sesli mesaj |
| **Katılımcılar** | İletinin tüm katılımcılarının listesi; örneğin, Gönderen, Son, Bilgi, Gizli. |
| **Özet Kimlik** | Özet kimliği. |
| **Alındı** | E-posta iletisi alıcı tarafından alınmıştır. Bu alan, Alınan e-posta özelliğiyle aynı özelliktir. |
| **Alıcılar** | E-posta iletisinde tüm alıcı alanları. Bu alanlar To, Bilgi ve Gizli'dir. |
| **Temsili Kimlik** | Her bir tam yineleme kümesi için sayısal tanımlayıcı. |
| **Gönderen** | E-posta iletisi gönderen. |
| **Gönderen/Yazar** | E-posta için, iletiyi gönderen kişidir. Belgeler için, yazar alanında adı geçen kişi Office içerir. Virgülle ayırarak birden çok ad yazın. İki veya daha fazla değer OR işleci tarafından mantıksal olarak bağlantılıdır. |
| **Hassas bilgi türleri** | İçerikte tanımlanan hassas bilgi türleri. |
| **Duyarlılık etiketleri** | İçeriklere uygulanan duyarlılık etiketleri. |
| **Gönderildi** | Gönderen tarafından e-posta iletisi gönderildiği tarih. Bu alan, Gönderilmiş e-posta özelliğiyle aynı özelliktir. |
| **Boyut** | Hem e-posta hem de belgeler için, öğenin boyutu (bayt cinsinden). |
| **Konu** | E-posta iletisi konu satırı metindir. |
| **Konu/Başlık** | E-posta için, iletinin konu satırı metindir. Belgeler için, belgenin başlığı. Daha önce de belirtildiği gibi Başlık özelliği, bu belgelerde belirtilen Microsoft Office veridir. Birbirinden virgülle ayırarak birden çok konu/başlığın adını yazın. İki veya daha fazla değer OR işleci tarafından mantıksal olarak bağlantılıdır. |
| **Temalar listesi** | Analizler için hesaplanan temalar listesi. |
| **Başlık** | Belgenin başlığı. Başlık özelliği, bu belgelerde belirtilen meta Office kullanılır. Belgenin dosya adıyla aynı değil. |
| **Hedef** | E-posta iletisi alıcısı, Son alanında. |

## <a name="filtering"></a>Filtreleme

Bir aramanın kapsamını daraltmak ve daha daraltılmış bir sonuç kümesi geri dönmek için bir veya daha fazla filtre kullanabilirsiniz. Filtre ayarlamak için, içerik **kuyruğun** üst kısmında Filtreler'i seçin. Birçok filtre, filtre tarafından döndürülen sonuçları daraltmaya yardımcı olmak için ek filtreleme seçenekleri içerir. Örneğin, Tarih filtresi *,* Tarih filtresi için Başlangıç tarihi *ve Bitiş* *tarihi yapılandırma* **denetimlerini** içerir. Aşağıdaki kategorilerden bir veya daha fazla filtre öğesini seçin:

### <a name="common-filters"></a>Ortak filtreler

| **Filtre** | **Açıklama** |
|:---------------------|:----------------|
| **Tarih (UTC)** | E-posta için, iletinin bir alıcı tarafından veya gönderen tarafından gönderildiği tarihtir. Belgeler için, belgenin son değiştirilma tarihidir. |
| **Gönderen/Yazar** | E-posta için, iletiyi gönderen kişidir. Belgeler için, belgelerde Yazar alanında *adı* Office. Virgülle ayırarak birden çok ad yazın. |
| **Kaynak** | Belgenizin kuruluş konumunu gösterir. Örneğin, belirli bir SharePoint konumu. |
| **Konu/Başlık** | E-posta için, iletinin konu satırı metindir. Belgeler için, belgenin başlığı. Belgeler'in Başlık özelliği, bu belgelerde belirtilen Microsoft Office verilerdir. Birbirinden virgülle ayırarak birden çok konu/başlığın adını yazın. İki veya daha fazla değer OR işleci tarafından mantıksal olarak bağlantılıdır. |

### <a name="email-filters"></a>E-posta filtreleri

| **Filtre** | **Açıklama** |
|:---------------------|:----------------|
| **Gizli** | E-posta iletisine ait Gizli alanı. |
| **Bilgi** | E-posta iletisi bilgi alanı. |
| **Eki var** | İletinin eki olup olmadığını gösterir. Değerler doğru veya **yanlış olarak** **listelenir**. |
| **E-posta ekidir** | Belge bir ekse, değer Evet olarak **listelenir**. |
| **Belge eklenmiş** | Belge e-posta iletisine eklenmişse, değer Evet olarak **listelenir**. |
| **Satır içi ek** | Belge e-posta iletisine gelen satır içi bir ekse, değer Evet olarak **listelenir**. |
| **Katılımcılar** | E-posta iletisinde tüm kişiler alanları. Bu alanlar Ilk, Son, Bilgi ve Gizli alanlarıdır. |
| **Alındı** | E-posta iletisi alıcı tarafından alınmıştır. |
| **Alıcı etki alanları** | İletinin tüm alıcıları etki alanlarının listesi. |
| **Alıcılar** | E-posta iletisi alıcıları. |
| **Gönderen** | İleti türleri için Gönderen (Gönderen) alanı.  Biçim, **DisplayName 'tir \<SmtpAddress>**. |
| **Gönderen etki alanı** | Gönderenin etki alanı. |
| **Hedef** | E-posta iletisine gelen To alanı. |
| **E-posta kümesinde benzersiz** | E-posta kümesinde ekin yinelenen bir kopyası varsa False. |

## <a name="document-filters"></a>Belge filtreleri

| **Filtreler** | **Açıklama** |
|:---------------------|:----------------|
| **Uyumluluk etiketleri** | Uyumluluk etiketleri alanlarına Office 365. |
| **Oluşturma saati (UTC)** | Dosya veya e-posta iletisi oluşturulan tarih ve saat. Tarih ve saat, Eşgüdümli Evrensel Saat'e (UTC) sahiptir. |
| **Son değiştirme tarihi (UTC)** | Belgenin son değiştir bitiş tarihi. Tarih ve saat, Eşgüdümli Evrensel Saat'e (UTC) sahiptir. |
| **Dosya uzantısı** | Dosyanın uzantı türü. |
| **Kullanıcı etkinliği olayları** | Olaydaki belirli kullanıcı etkinliğiyle ilgili öğeler için etkinlik.  Örneğin, bir vakanın Kullanıcı Etkinliği sayfasında bir etkinlik için 'İçeriği Keşfet' bağlantısını seçerek  bu etkinlikle ilgili öğeleri görüntülemek için bu filtre kullanılır. |
| **İş ürünü** | Belge için iş ürününün türü. Örneğin, belgedeki ek açıklamalar veya etiketler. |
