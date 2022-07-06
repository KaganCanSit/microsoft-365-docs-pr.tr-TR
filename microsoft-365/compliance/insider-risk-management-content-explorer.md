---
title: Insider risk yönetimi İçerik gezgini
description: Microsoft Purview'da insider risk yönetimi İçerik gezgini hakkında bilgi edinin
keywords: Microsoft 365, Microsoft Purview, insider riski, risk yönetimi, uyumluluk
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
ms.openlocfilehash: c193325608feef3bc8114b50af9d5e5832eb9d66
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66642557"
---
# <a name="insider-risk-management-content-explorer"></a>Insider risk yönetimi İçerik gezgini

Insider risk yönetimi **İçerik gezgini** , *Insider Risk Yönetimi Araştırmacıları* rolüne atanan kullanıcıların uyarılardaki etkinlikle ilişkili içeriğin bağlamını ve ayrıntılarını incelemesine olanak tanır. İçerik gezginindeki servis talebi verileri her gün yeni etkinlik içerecek şekilde yenilenir. Bir servis talebi için onaylanan tüm uyarılar için, verilerin ve ileti dosyalarının kopyaları öğelerin zamanında anlık görüntü olarak arşivlenir ve depolama kaynaklarında özgün dosyalar ve iletiler korunur. Gerekirse, servis talebi veri dosyaları taşınabilir belge dosyası (PDF) olarak veya özgün dosya biçiminde dışarı aktarılabilir.

Yeni durumlarda, içerik gezgininde içeriğin doldurulma süresi genellikle yaklaşık bir saat sürer. Büyük miktarda içeriğe sahip durumlarda anlık görüntü oluşturmak daha uzun sürebilir. İçerik gezgininde içerik yüklenmeye devam ediyorsa tamamlanma yüzdesini gösteren bir ilerleme göstergesi görürsünüz.

Bazı durumlarda, bir servis talebiyle ilişkili veriler İçerik gezgininde gözden geçirilecek anlık görüntü olarak kullanılamayabilir. Bu durum, servis talebi verileri silindiğinde veya taşındığında veya olay verileri işlenirken geçici bir hata oluştuğunda ortaya çıkabilir. Bu durum oluşursa, her dosya için dosya adlarını, dosya yolunu ve hatanın nedenini görüntülemek için uyarı çubuğunda Dosyaları **görüntüle'yi** seçin. Gerekirse, bu bilgiler bir .csv (virgülle ayrılmış değerler) dosyasına aktarılabilir.

İçerik Bilgi Hakları Yönetimi izinlerini içeriyorsa, kopyalanan içerik için bu izinler korunur ve *Insider Risk Yönetimi Araştırmacıları* rolüne atanan kullanıcılar, dosyaları açıp görüntülemeleri gerekiyorsa bu izinlere ve haklara ihtiyaç duyar. Her dosya ve iletiye, yönetim amacıyla insider risk yönetimi örneğinde otomatik olarak benzersiz bir dosya kimliği atanır. Cihaz göstergesi etkinlikleriyle ilişkili belgeler İçerik gezginine dahil değildir.

> [!NOTE]
> İçerik gezgini; SharePoint, Exchange, Microsoft Teams ve OneDrive İş üzerindeki kullanıcı etkinliği gibi Microsoft 365 hizmet dosyalarıyla ilgili kullanıcı etkinliklerini içerir.

## <a name="column-options"></a>Sütun seçenekleri

Risk analistlerinin ve araştırmacıların yakalanan verileri ve iletileri gözden geçirmesini ve olayın bağlamını gözden geçirmesini kolaylaştırmak için İçerik gezginine çeşitli filtreleme ve sıralama araçları eklenmiştir. Temel sıralama için **Tarih** ve **Dosya sınıfı** sütunları, içerik kuyruğu bölmesindeki sütun başlıklarını kullanarak sıralamayı destekler. Diğer kuyruk sütunları, dosya ve iletilerde farklı özetler sağlamak için görünüme eklenebilir.

İçerik kuyruğuna sütun başlıkları eklemek veya kaldırmak için **Sütunları düzenle** denetimini kullanın ve aşağıdaki sütun seçeneklerinden birini belirleyin. Bu sütunlar İçerik gezgininde desteklenen ve bu makalenin devamında listelenen ortak, e-posta ve belge özelliği koşullarıyla eşlenmektedir.

| **Sütun seçeneği** | **Açıklama** |
|:------------------|:----------------|
| **Yazar** | Bir belge kopyalandığında kalıcı olan Office belgelerindeki yazar alanı. Örneğin, bir kullanıcı bir belge oluşturursa ve belgeyi SharePoint'e yükleyen başka birine e-postayla bildirirse, belge özgün yazarı korur. |
| **Gizli** | Gizli ileti alanındaki kullanıcılar, e-posta iletileri için kullanılabilir. |
| **Cc** | Bilgi iletisi alanındaki kullanıcılar olan e-posta iletileri için kullanılabilir. |
| **Bileşik yol** | Öğenin kaynağını açıklayan okunabilir yol. |
| **Konuşma Kimliği** | İletideki konuşma kimliği. |
| **Konuşma dizini** | İletiden konuşma dizini. |
| **Oluşturma zamanı** | Dosyanın veya e-posta iletisinin oluşturulduğu saat. |
| **Tarih (UTC)** | E-posta için, iletinin bir alıcı tarafından alındığı veya gönderen tarafından gönderildiği tarih. Belgeler için, belgenin son değiştirildiği tarih. Tarih Eşgüdümlü Evrensel Saat (UTC) biçimindedir.|
| **Baskın tema** | Analiz için hesaplanmış baskın tema. |
| **E-posta kümesi kimliği** | Aynı e-posta kümesindeki tüm iletiler için grup kimliği. |
| **Aile Kimliği** | Aile Kimliği tüm öğeleri birlikte gruplandır; e-posta için bu sütun iletiyi ve tüm ekleri içerir; bu sütun, belgeler için belgeyi ve eklenmiş öğeleri içerir. |
| **Dosya sınıfı** | SharePoint ve OneDrive içeriği için: **Belge**; Exchange'den içerik için: **E-posta** veya **Ek**. |
| **Dosya Kimliği** | Servis talebi içinde benzersiz belge tanımlayıcısı. |
| **Dosya türü simgesi** | Dosyanın uzantısı; örneğin, docx, one, pptx veya xlsx. Bu alan, FileExtension site özelliğiyle aynı özelliktir. |
| **Kimlik** | Dosyanın GUID tanımlayıcısı. |
| **Sabit Kimlik** | Office 365 depolanan sabit kimlik. |
| **Kapsayıcı tür** | Analiz için hesaplanan kapsayıcı tür: **0** - dahil değil; **1** - dahil; **2** - dahil eksi; **3** - dahil kopya. |
| **Son değiştirme** | Belgenin son değiştirildiği tarih. |
| **Temsilci olarak işaretlendi** | Her yineleme kümesinden bir belge temsilci olarak işaretlenir. |
| **İleti türü** | Aranacak e-posta iletisinin türü. Olası değerler: kişiler, belgeler, e-posta, dış veriler, fakslar, anlık ileti, günlükler, toplantılar, Microsoft teams (Microsoft Teams'de sohbetlerden, toplantılardan ve aramalardan öğeleri döndürür), notlar, gönderiler, RSS akışları, görevler, sesli mesaj |
| **Katılımcı** | İletinin tüm katılımcılarının listesi; örneğin, Gönderen, Kime, Bilgi, Gizli. |
| **Özet Kimliği** | Özetin kimliği. |
| **Alınan** | E-posta iletisinin alıcı tarafından alındığı tarih. Bu alan, Alınan e-posta özelliğiyle aynı özelliktir. |
| **Alıcı** | E-posta iletisindeki tüm alıcı alanları. Bu alanlar Kime, Bilgi ve Gizli alanlarıdır. |
| **Temsilci Kimliği** | Her yineleme kümesinin sayısal tanımlayıcısı. |
| **Gönderen** | E-posta iletisinin göndereni. |
| **Gönderen/Yazar** | E-posta için, ileti gönderen kişi. Belgeler için, Office belgelerinden yazar alanında alıntı yapılan kişi. Virgülle ayırarak birden fazla ad yazabilirsiniz. İki veya daha fazla değer OR işleci tarafından mantıksal olarak bağlanır. |
| **Hassas bilgi türleri** | İçerikte tanımlanan hassas bilgi türleri. |
| **Duyarlılık etiketleri** | İçeriğe uygulanan duyarlılık etiketleri. |
| **Gönderilen** | Gönderen tarafından e-posta iletisinin gönderildiği tarih. Bu alan, Gönderilmiş e-posta özelliğiyle aynı özelliktir. |
| **Boyut** | Hem e-posta hem de belgeler için öğenin boyutu (bayt cinsinden). |
| **Konu** | E-posta iletisinin konu satırındaki metin. |
| **Konu/Başlık** | E-posta için, iletinin konu satırındaki metin. Belgeler için, belgenin başlığı. Daha önce açıklandığı gibi, Title özelliği Microsoft Office belgelerinde belirtilen meta verilerdir. Birden çok konunun/başlığın adını virgülle ayırarak yazabilirsiniz. İki veya daha fazla değer OR işleci tarafından mantıksal olarak bağlanır. |
| **Temalar listesi** | Analiz için hesaplanan temalar listesi. |
| **Başlık** | Belgenin başlığı. Title özelliği, Office belgelerinde belirtilen meta verilerdir. Belgenin dosya adından farklıdır. |
| **Hedef** | E-posta iletisinin Alıcı alanındaki alıcısı. |

## <a name="filtering"></a>Filtreleme

Bir aramanın kapsamını daraltmak ve daha iyileştirilmiş bir sonuç kümesi döndürmek için bir veya daha fazla filtre kullanabilirsiniz. Filtre ayarlamak için içerik kuyruğunun üst kısmındaki **Filtreler'i** seçin. Birçok filtre, filtre tarafından döndürülen sonuçları daraltmaya yardımcı olmak için ek filtreleme seçenekleri içerir. Örneğin *, Tarih* filtresi, Tarih filtresi için *Başlangıç tarihi* ve *Bitiş tarihi* yapılandırma denetimleri içerir. Aşağıdaki kategorilerden bir veya daha fazla filtre öğesi seçin:

### <a name="common-filters"></a>Ortak filtreler

| **Filtrele** | **Açıklama** |
|:---------------------|:----------------|
| **Tarih (UTC)** | E-posta için, iletinin bir alıcı tarafından alındığı veya gönderen tarafından gönderildiği tarih. Belgeler için, belgenin son değiştirildiği tarih. |
| **Gönderen/Yazar** | E-posta için, ileti gönderen kişi. Belgeler için, Office belgelerinden *Yazar* alanında alıntı yapılan kişi. Virgülle ayırarak birden fazla ad yazabilirsiniz. |
| **Kaynak** | Belgenin kuruluşunuzdaki konumu. Örneğin, belirli bir SharePoint sitesi konumu. |
| **Konu/Başlık** | E-posta için, iletinin konu satırındaki metin. Belgeler için, belgenin başlığı. Belgelerdeki Title özelliği, Microsoft Office belgelerinde belirtilen meta verilerdir. Birden çok konunun/başlığın adını virgülle ayırarak yazabilirsiniz. İki veya daha fazla değer OR işleci tarafından mantıksal olarak bağlanır. |

### <a name="email-filters"></a>E-posta filtreleri

| **Filtrele** | **Açıklama** |
|:---------------------|:----------------|
| **Gizli** | E-posta iletisinin Gizli alanı. |
| **Cc** | E-posta iletisinin Bilgi alanı. |
| **Eki var** | İletinin eki olup olmadığını gösterir. Değerler **true** veya **false** olarak listelenir. |
| **E-posta eki mi?** | Belge bir ekse, değer **Evet** olarak listelenir. |
| **Eklenmiş belgedir** | Belge e-posta iletisine eklenmişse, değer **Evet** olarak listelenir. |
| **Satır içi ektir** | Belge e-posta iletisinde satır içi bir ekse, değer **Evet** olarak listelenir. |
| **Katılımcı** | E-posta iletisindeki tüm kişiler alanları. Bu alanlar Kimden, Kime, Bilgi ve Gizli alanlarıdır. |
| **Alınan** | E-posta iletisinin alıcı tarafından alındığı tarih. |
| **Alıcı etki alanları** | İletinin alıcılarının tüm etki alanlarının listesi. |
| **Alıcı** | E-posta iletisi alıcıları. |
| **Gönderen** | İleti türleri için Gönderen (Kimden) alanı.  Biçim **DisplayName \<SmtpAddress>** şeklindedir. |
| **Gönderen etki alanı** | Gönderenin etki alanı. |
| **Hedef** | E-posta iletisinin To alanı. |
| **E-posta kümesinde benzersiz** | E-posta kümesinde ekin bir kopyası varsa False. |

## <a name="document-filters"></a>Belge filtreleri

| **Filtreler** | **Açıklama** |
|:---------------------|:----------------|
| **Uyumluluk etiketleri** | Office 365 uygulanan uyumluluk etiketleri. |
| **Oluşturma saati (UTC)** | Dosyanın veya e-posta iletisinin oluşturulduğu tarih ve saat. Tarih ve saat Eşgüdümlü Evrensel Saat (UTC) içindedir. |
| **Son değiştirme tarihi (UTC)** | Belgenin son değiştirildiği tarih. Tarih ve saat Eşgüdümlü Evrensel Saat (UTC) içindedir. |
| **Dosya uzantısı** | Dosyanın uzantı türü. |
| **Kullanıcı etkinliği olayları** | Bir servis talebindeki belirli kullanıcı etkinliğiyle ilgili öğeler için etkinlik.  Örneğin, bir servis talebinin **Kullanıcı Etkinliği** sayfasındaki bir etkinlik için 'İçeriği Keşfet' bağlantısını seçtiğinizde, bu filtre bu etkinlikle ilgili öğeleri görüntülemek için kullanılır. |
| **İş ürünü** | Belgenin iş ürününün türü. Örneğin, belgedeki ek açıklamalar veya etiketler. |
