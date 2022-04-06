---
title: Cihaz envanteri
description: İncelemeleri geliştirmek için Cihazlar listesinden kullanabileceğiniz sıralama, filtreleme ve listenin dışarı aktarma gibi kullanılabilir özellikleri hakkında bilgi edinebilirsiniz.
keywords: sıralama, filtreleme, dışarı aktarma, csv, cihaz adı, etki alanı, son görülen, iç IP, durum, etkin uyarılar, etkin kötü amaçlı yazılım algılamaları, tehdit kategorisi, uyarıları gözden geçirme, ağ, bağlantı, kötü amaçlı yazılım, tür, parola çalmak, fidye yazılımı, istismar, tehdit, genel kötü amaçlı yazılım, istenmeyen yazılım
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a9753cdc818aefdf33411bd237327310dfc512ab
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474761"
---
# <a name="device-inventory"></a>Cihaz envanteri

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-machinesview-abovefoldlink)

Cihazlar **listesinde** , ağda uyarıların oluşturulmuş olduğu cihazların listesi görüntülenir. Varsayılan olarak, kuyruk son 30 gün içinde görülen cihazları görüntüler.

En çok risk altında olan cihazların kolayca tanımlanması için etki alanı, risk düzeyi, işletim sistemi platformu gibi bilgileri ve diğer ayrıntıları bir bakışta görebilirsiniz.

Cihaz listesi görünümünü özelleştirmek için seçebileceğiniz çeşitli seçenekler vardır. Üst gezintiden şunlarıabilirsiniz:

- Sütun ekleme veya kaldırma
- Listenin tamamını CSV biçiminde dışarı aktarma
- Sayfa başına göstermek istediğiniz öğe sayısını seçin
- Filtre uygulama

Ekleme işlemi sırasında Cihazlar listesi, **algılayıcı** verilerini bildirmeye başlayan cihazlarla aşamalı olarak doldurulur. Çevrimiçi duruma geldiklerinde eklenilen uç noktalarınızı izlemek için bu görünümü kullanın veya çevrimdışı çözümleme için tam uç nokta listesini CSV dosyası olarak indirin.

> [!NOTE]
> Cihaz listesini dışarı aktardıysanız, bu liste, organizasyonlar'daki tüm cihazlarınızı içerir. İndirmek, kuruma ne kadar büyük olduğunu bağlı olarak önemli ölçüde zaman alsa da bu kadar uzun olabilir. Listeyi CSV biçiminde dışarı aktaran veriler filtrelenmemiş bir şekilde görüntülenir. CSV dosyası, görünümde kendisine uygulanan filtrelerden bağımsız olarak, kuruluşta tüm cihazları içerir.

:::image type="content" source="images/device-inventory.png" alt-text="Cihazların listesi" lightbox="images/device-inventory.png":::

## <a name="sort-and-filter-the-device-list"></a>Cihaz listesini sıralama ve filtreleme

Uyarı listesini sınırlandırarak daha odaklanmış bir görünüm elde etmek için aşağıdaki filtreleri uygulayabilirsiniz.

### <a name="device-name"></a>Cihaz adı

Kullanıcı Uç Nokta için Microsoft Defender sırasında MDE'ye yerleşik cihazlar, algılayıcı verilerini bildirmeye başlandıklarına göre cihaz envanterine aşamalı olarak doldurulur. Bu işlemden sonra, cihaz stoku, cihaz bulma işlemi aracılığıyla ağda bulunan cihazlar tarafından doldurulur. Cihaz envanteri, cihazları şu şekilde listeleen üç sekmeye sahip:

- **Bilgisayarlar ve Mobil**: Enterprise uç noktaları (iş istasyonları, sunucular ve mobil cihazlar) kullanılabilir
- **Ağ cihazları**: Yönlendiriciler ve anahtarlar gibi cihazlar
- **IoT cihazları**: Yazıcı ve kamera gibi cihazlar

## <a name="navigate-to-the-device-inventory-page"></a>Cihaz stoku sayfasına gidin

Mobil portalda Uç noktalar gezinti **menüsünden Cihaz** **envanteri'ni** seçerek cihaz [Microsoft 365 Defender erişin](/defender/microsoft-365-security-center-mde).

## <a name="device-inventory-overview"></a>Cihaz stoku için genel bakış

Cihaz envanteri Bilgisayarlar ve **Mobil sekmesinde** açılır. En çok risk olan cihazların kolayca tanımlanması için cihaz adı, etki alanı, risk düzeyi, pozlama düzeyi, işletim sistemi platformu, kullanım durumu, algılayıcı durumu ve diğer ayrıntılar gibi bilgileri bir bakışta görebilirsiniz.

Bulunan **cihazlara göre sıralamak** ve filtrelemek için Ekleme Durumu sütununu kullanın; bu cihazlarda zaten var olan cihazlar Uç Nokta için Microsoft Defender.

![Cihaz listesiyle birlikte cihazlar listesinin görüntüsü.](images/device-inventory.png)

Ağ **cihazları ve** **IoT cihazları** sekmelerinde satıcı, model ve cihaz türü gibi bilgileri de görüntülersiniz:

![Ağ cihazları listesinin resmi.](images/device-inventory-networkdevices.png)

Her cihaz envanteri sekmesinin en üstünde, toplam cihaz sayısını, henüz eklememiş cihazların sayısını ve kuruluş için daha yüksek bir risk olarak tanımlanan cihaz sayısını görebilirsiniz. Güvenlik sonrası iyileştirmeleri için cihazların önceliklerini belirlemede size yardımcı olması için bu bilgileri kullanabilirsiniz.

Ağ **cihazları ve** IoT cihazları için Yeni bulunan cihaz sayısı sekmeleri, son 7 gün içinde bulunan ve geçerli görünümde listelenen yeni cihazların sayısını gösterir.

![Yeni bulunan cihaz sayısını gösterir.](images/new-discovered-devices.png)

## <a name="explore-the-device-inventory"></a>Cihaz envanterini keşfedin

Cihaz stoku görünümünü özelleştirmek için seçebileceğiniz çeşitli seçenekler vardır. Her sekme için üst gezintide şunları yapın:

- Cihazı adına göre arama
- En son kullanılan IP adresi veya IP adresi öneki ile bir cihazı arama
- Sütun ekleme veya kaldırma
- Çevrimdışı çözümleme için listenin tamamını CSV biçiminde dışarı aktarma
- Görüntülenmek istediğiniz tarih aralığını seçin
- Filtre uygulama

> [!NOTE]
> Cihaz listesini dışarı aktardıysanız, bu liste, organizasyonlar'daki tüm cihazlarınızı içerir. İndirmek, kuruma ne kadar büyük olduğunu bağlı olarak önemli ölçüde zaman alsa da bu kadar uzun olabilir. Listeyi CSV biçiminde dışarı aktaran veriler filtrelenmemiş bir şekilde görüntülenir. CSV dosyası, görünümde kendisine uygulanan filtrelerden bağımsız olarak, kuruluşta tüm cihazları içerir.

Daha odaklanmış bir görünüm elde etmek ve kurumda cihazları değerlendirmenize ve yönetmenize yardımcı olmak için, her bir cihaz envanteri sekmesinde bulunan sıralama ve filtreleme işlevlerini kullanabilirsiniz.

Her sekmenin üst kısmında yer alan sayımlar geçerli görünüme göre güncelleştirilir.

## <a name="use-filters-to-customize-the-device-inventory-views"></a>Cihaz envanteri görünümlerini özelleştirmek için filtreleri kullanma

Filtre | Açıklama
:---|:---
**Risk düzeyi** </br> | Risk düzeyi, cihaz üzerinde etkin uyarıların türleri ve önem düzeyi de içinde olmak üzere bir etmenler birleşimine bağlı olarak cihazın genel risk değerlendirmesini yansıtmaktadır. Etkin uyarıları çözümleme, düzeltme etkinliklerini onaylama ve sonraki uyarıları gizleme, risk düzeyini düşürebilir.
**Pozlama düzeyi** </br> | Etkilenme düzeyi, bekleyen güvenlik önerilerinin kümülatif etkisine bağlı olarak cihazın geçerli etkilenme düzeyini yansıtmaktadır. Olası düzeyler düşük, orta ve yüksektir. Düşük pozlama, cihazlarınızı açıklardan yararlanmaya karşı daha az korumasız olduğu anlamına gelir. </br> </br> Pozlama düzeyi "Veri yok" ifadesini belirtiyorsa, bunun birkaç nedeni olabilir:</br>- Cihaz 30 gün boyunca raporlamayı durdurdu. Bu durumda devre dışı olduğu kabul edilir ve maruz kalma durumu hesaplanmayacaktır.</br>- Cihaz işletim sistemi desteklenmiyor - Mobil cihaz [gereksinimleri için en düşük Uç Nokta için Microsoft Defender](https://microsoft-my.sharepoint.com/personal/siosulli_microsoft_com/Documents/Security%20Posture/TVM/minimum-requirements.md).</br>- Eski aracısı olan cihaz (pek olası değil).
**Etiketler** </br> | Listeyi, tek tek cihazlara ekleytilen gruplama ve etiketlemeye göre filtrele. Bkz [. Cihaz etiketlerini oluşturma ve yönetme](machine-tags.md).
**Cihaz değeri**</br> | Cihazın yüksek değer veya düşük değer olarak işaretlenmiş olup olmadığını temel alarak listeye filtre uygulama.
**Dışlama durumu** </br> | Cihazın dışlanmış veya dışlanmış olup olmadığını temel alarak listeye filtre uygulama. Daha fazla bilgi için bkz. [Cihazları dışla](exclude-devices.md).
**Işletim Sistemi Platformu** </br>| Araştırırken ilgilendiğiniz işletim sistemi platformlarını filtrele </br></br>(_Yalnızca bilgisayarlar ve mobil ve IoT cihazları_)
**İlk görülen** </br> | Görünümlerinizi, cihazın ağda ilk ne zaman görüntülandığına veya algılayıcı tarafından ilk ne zaman bildir Uç Nokta için Microsoft Defender filtrele.</br></br>(_Yalnızca bilgisayarlar ve mobil ve IoT cihazları_)
**Windows sürümü** </br> | Araştırırken ilgilendiğiniz Windows sürümlerine göre filtrelenin.</br></br> (_Yalnızca bilgisayarlar ve mobil_)
**Algılayıcıların durumu** </br> | Aşağıdaki algılayıcı durumuna göre filtre yapın. Cihaz, cihaza şu Uç Nokta için Microsoft Defender:</br> - **Etkin**: Algılayıcı verilerini etkin bir şekilde hizmete bildiren cihazlar.</br> - **Etkin değil**: 7 gün boyunca sinyalleri göndermeyi durduran cihazlar. </br> - **Yanlış Yapılandırılmış: Hizmetle** iletişim engeli olan veya algılayıcı verilerini gönderemeyen cihazlar. </br> Yanlış yapılandırılmış cihazlar, aşağıdakiler için daha fazla sınıflandırılabilir: </br>  - Algılayıcı verisi yok </br>  - Engelli iletişimler </br>  Hatalı yapılandırılmış cihazlardaki sorunları çözme hakkında daha fazla bilgi için bkz. [Uygun olmayan algılayıcıları düzeltme](https://microsoft-my.sharepoint.com/personal/siosulli_microsoft_com/Documents/Security%20Posture/TVM/fix-unhealthy-sensors.md).</br></br> (_Yalnızca bilgisayarlar ve mobil_)
**Ekleme durumu** </br> | Ekleme durumu, cihazın şu anda kullanıcıya hazır olup olmadığını Uç Nokta için Microsoft Defender gösterir. Aşağıdaki eyaletlere göre filtre yapabilirsiniz: </br> - **Eklemeli**: Uç nokta, Alan Uç Nokta için Microsoft Defender.  </br> - **Kullanılabilir**: Uç nokta ağda desteklenen bir cihaz olarak bulundu ancak şu anda eklemedi. Microsoft bu cihazları işe eklemeyi kesinlikle önermektedir. </br> - **Desteklenmiyor**: Uç nokta ağda bulundu ancak diğer kullanıcılar tarafından Uç Nokta için Microsoft Defender. </br> - **Yetersiz bilgi**: Sistem, cihazın desteklanabilirliğini belirleyemedi.</br></br> (_Yalnızca bilgisayarlar ve mobil_)
**Virüsten koruma durumu** </br> | Virüsten koruma durumunun devre dışı olup olmadığını, güncelleştirilme veya bilinmiyor olup olmadığını temel alarak görünüme filtre uygulama.</br></br> (_Yalnızca bilgisayarlar ve mobil_)
**Grup** </br> | Araştırırken ilgilendiğiniz gruba göre listeye filtre uygulama. </br></br> (_Yalnızca bilgisayarlar ve mobil_)
**Yönetilen** </br> | Yönetilen, cihazın nasıl yönetilmiyor olduğunu gösterir. Filtreyi şu ölçütlere göre filtreleysiniz:</br>- Uç Nokta için Microsoft Defender </br> - Mobil cihaz yönetimi (MDM) </br>- Bilinmiyor: Bunun nedeni, eski sürümün veya SCCM Windows başka bir üçüncü taraf MDM'nin çalışıyor olması olabilir.</br></br> (_Yalnızca bilgisayarlar ve mobil_)
**Cihaz Türü** </br> | Araştırırken ilgilendiğiniz cihaz türüne göre filtre kullanın.</br></br> (_Yalnızca IoT cihazları_)

## <a name="use-columns-to-customize-the-device-inventory-views"></a>Cihaz stoku görünümlerini özelleştirmek için sütunları kullanma

Kullanılabilir bir sütun başlığına tıklayarak görünümdeki sütunları ekleyebilir veya kaldırabilir ve girdileri sıralayabilirsiniz.

Bilgisayar ve **Mobil Cihazlar sekmesinde** Sütunları **özelleştir'i seçerek** kullanılabilir sütunları görüntüleyin. Aşağıdaki resimde varsayılan değerler denetlenir:

![Bilgisayar ve cep telefonlarının görüntüsü](images/computerandmobilescolumns.png)

Kullanılabilir **sütunları görmek için** Ağ cihazları **sekmesinde Sütunları** özelleştir'i seçin. Aşağıdaki resimde varsayılan değerler denetlenir:

![Ağ cihazı sütunlarının görüntüsü](images/networkdevicescolumns.png)

Kullanılabilir sütunları **görmek için IoT** cihazları **sekmesinde Sütunları** özelleştir'i seçin. Aşağıdaki resimde varsayılan değerler denetlenir:

![IoT cihaz sütunlarının resmi](images/iotdevicescolumns.png)

## <a name="related-articles"></a>İlgili makaleler

[Uç Nokta için Microsoft Defender Cihazlar listesinde cihazları araştırma](investigate-machines.md)
