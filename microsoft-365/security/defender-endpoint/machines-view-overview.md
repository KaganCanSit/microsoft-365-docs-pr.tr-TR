---
title: Cihaz envanteri
description: Araştırmayı geliştirmek için Sıralama, filtreleme ve listeyi dışarı aktarma gibi Cihazlar listesinden kullanabileceğiniz kullanılabilir özellikler hakkında bilgi edinin.
keywords: sort, filter, export, csv, device name, domain, last seen, internal IP, health state, active alerts, active malware detections, threat category, review alerts, network, connection, malware, type, password stealer, ransomware, exploit, threat, general malware, istenmeyen yazılım
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
ms.openlocfilehash: 78cb81b1a0da9f0d1965dab7c209067a4e8d02e6
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65874184"
---
# <a name="device-inventory"></a>Cihaz envanteri

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender Güvenlik Açığı Yönetimi](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-machinesview-abovefoldlink)

**Cihaz envanteri**, ağınızdaki uyarıların oluşturulduğu cihazların listesini gösterir. Kuyruk varsayılan olarak son 30 gün içinde görülen cihazları görüntüler.

Bir bakışta etki alanı, risk düzeyi, işletim sistemi platformu gibi bilgileri ve risk altındaki cihazların kolay tanımlanmasına yönelik diğer ayrıntıları göreceksiniz.

> [!NOTE]
> Cihaz envanteri farklı Microsoft 365 Defender hizmetlerde kullanılabilir. Kullanabileceğiniz bilgiler lisansınıza bağlı olarak farklılık gösterir. [Uç Nokta için Microsoft Defender Plan 2'yi](https://go.microsoft.com/fwlink/p/?linkid=2154037) kullanırken en eksiksiz özellikler kümesini elde edersiniz.

Cihaz listesi görünümünü özelleştirmek için aralarından seçim yapabileceğiniz çeşitli seçenekler vardır. Üst gezintide aşağıdakileri yapabilirsiniz:

- Sütun ekleme veya kaldırma
- Listenin tamamını CSV biçiminde dışarı aktarma
- Sayfa başına gösterilecek öğe sayısını seçin
- Filtre uygulama

Ekleme işlemi sırasında **Cihazlar listesi** , algılayıcı verilerini raporlamaya başlarken cihazlarla aşamalı olarak doldurulur. Eklenen uç noktalarınızı çevrimiçi olarak izlemek için bu görünümü kullanın veya çevrimdışı analiz için tam uç nokta listesini CSV dosyası olarak indirin.

> [!NOTE]
> Cihaz listesini dışarı aktarırsanız, kuruluşunuzdaki tüm cihazları içerir. Kuruluşunuzun ne kadar büyük olduğuna bağlı olarak indirilmesi önemli ölçüde zaman alabilir. Listeyi CSV biçiminde dışarı aktarmak, verileri filtrelenmemiş bir şekilde görüntüler. CSV dosyası, görünüme uygulanan filtrelemelerden bağımsız olarak kuruluştaki tüm cihazları içerir.

:::image type="content" source="images/device-inventory.png" alt-text="Cihaz listesi" lightbox="images/device-inventory.png":::

## <a name="sort-and-filter-the-device-list"></a>Cihaz listesini sıralama ve filtreleme

Uyarı listesini sınırlamak ve daha odaklanmış bir görünüm elde etmek için aşağıdaki filtreleri uygulayabilirsiniz.

### <a name="device-name"></a>Cihaz adı

Uç Nokta için Microsoft Defender ekleme işlemi sırasında, MDE'ye eklenen cihazlar, algılayıcı verilerini raporlamaya başladığında aşamalı olarak cihaz envanterine doldurulur. Bundan sonra, cihaz envanteri, cihaz bulma işlemi aracılığıyla ağınızda bulunan cihazlar tarafından doldurulur. Cihaz envanterinde cihazları listeleyen üç sekme vardır:

- **Bilgisayarlar ve Mobil**: Enterprise uç noktaları (iş istasyonları, sunucular ve mobil cihazlar)
- **Ağ cihazları**: Yönlendiriciler ve anahtarlar gibi cihazlar
- **IoT cihazları**: Yazıcılar ve kameralar gibi cihazlar

## <a name="navigate-to-the-device-inventory-page"></a>Cihaz envanteri sayfasına gidin

[Microsoft 365 Defender portalındaki](/microsoft-365/security/defender-business/mdb-get-started) **Uç Noktalar** gezinti **menüsünden Cihaz envanteri'ni** seçerek cihaz envanteri sayfasına erişin.

## <a name="device-inventory-overview"></a>Cihaz envanteri genel bakış

Cihaz envanteri **Bilgisayarlar ve Mobil** sekmesinde açılır. Bir bakışta cihaz adı, etki alanı, risk düzeyi, maruz kalma düzeyi, işletim sistemi platformu, ekleme durumu, algılayıcı sistem durumu ve en çok risk altındaki cihazların kolay tanımlanması için diğer ayrıntılar gibi bilgileri göreceksiniz.

Bulunan cihazlara ve zaten Uç Nokta için Microsoft Defender eklenen cihazlara göre sıralamak ve filtrelemek için **Ekleme Durumu** sütununu kullanın.

![Cihaz listesinin yer aldığı cihaz listesinin görüntüsü.](images/device-inventory.png)

**Ağ cihazları** ve **IoT cihazları** sekmelerinden satıcı, model ve cihaz türü gibi bilgileri de görürsünüz:

![Ağ cihazları listesinin görüntüsü.](images/device-inventory-networkdevices.png)

Her cihaz envanteri sekmesinin en üstünde, toplam cihaz sayısını, henüz eklenmemiş cihaz sayısını ve kuruluşunuz için daha yüksek risk olarak tanımlanan cihaz sayısını görebilirsiniz. Güvenlik duruşu geliştirmeleri için cihazların önceliklerini belirlemenize yardımcı olması için bu bilgileri kullanabilirsiniz.

Ağ cihazları ve IoT cihazları sekmeleri için **yeni bulunan** cihaz sayısı, geçerli görünümde listelenen son 7 gün içinde bulunan yeni cihazların sayısını gösterir.

![Bulunan yeni cihaz sayısının resmi.](images/new-discovered-devices.png)

## <a name="explore-the-device-inventory"></a>Cihaz envanterini keşfetme

Cihaz envanter görünümünü özelleştirmek için aralarından seçim yapabileceğiniz çeşitli seçenekler vardır. Her sekmenin üst gezintisinde aşağıdakileri yapabilirsiniz:

- Bir cihazı ada göre arama
- Bir cihazı en son kullanılan IP adresine veya IP adresi ön eklerine göre arama
- Sütun ekleme veya kaldırma
- Çevrimdışı analiz için listenin tamamını CSV biçiminde dışarı aktarma
- Görüntülenecek tarih aralığını seçin
- Filtre uygulama

> [!NOTE]
> Cihaz listesini dışarı aktarırsanız, kuruluşunuzdaki tüm cihazları içerir. Kuruluşunuzun ne kadar büyük olduğuna bağlı olarak indirilmesi önemli ölçüde zaman alabilir. Listeyi CSV biçiminde dışarı aktarmak, verileri filtrelenmemiş bir şekilde görüntüler. CSV dosyası, görünüme uygulanan filtrelemelerden bağımsız olarak kuruluştaki tüm cihazları içerir.

Daha odaklanmış bir görünüm elde etmek ve kuruluşunuzdaki cihazları değerlendirmenize ve yönetmenize yardımcı olmak için her cihaz envanteri sekmesinde bulunan sıralama ve filtreleme işlevini kullanabilirsiniz.

Her sekmenin en üstündeki sayılar geçerli görünüme göre güncelleştirilir.

## <a name="use-filters-to-customize-the-device-inventory-views"></a>Cihaz envanter görünümlerini özelleştirmek için filtreleri kullanma

Filtrele | Açıklama
:---|:---
**Risk düzeyi** </br> | Risk düzeyi, cihazdaki etkin uyarıların türleri ve önem derecesi de dahil olmak üzere faktörlerin bir bileşimine göre cihazın genel risk değerlendirmesini yansıtır. Etkin uyarıları çözümleme, düzeltme etkinliklerini onaylama ve sonraki uyarıların gizlenmesi risk düzeyini düşürebilir.
**Maruz kalma düzeyi** </br> | Maruz kalma düzeyi, bekleyen güvenlik önerilerinin kümülatif etkisine bağlı olarak cihazın geçerli maruziyetini yansıtır. Olası düzeyler düşük, orta ve yüksektir. Düşük maruz kalma, cihazlarınızın yararlanmaya karşı daha az savunmasız olduğu anlamına gelir. </br> </br> Maruz kalma düzeyinde "Kullanılabilir veri yok" ifadesi varsa, bunun olmasının birkaç nedeni vardır:</br>- Cihaz 30 günden uzun süre raporlamayı durdurdu. Bu durumda etkin değil olarak kabul edilir ve açığa çıkarma hesap edilmez.</br>- Cihaz işletim sistemi desteklenmiyor - [Uç Nokta için Microsoft Defender için en düşük gereksinimlere](/microsoft-365/security/defender-endpoint/minimum-requirements) bakın.</br>- Eski aracılı cihaz (olası değildir).
**Etiketler** </br> | Tek tek cihazlara eklediğiniz gruplandırma ve etiketlemeye göre listeyi filtreleyin. Bkz. [Cihaz etiketlerini oluşturma ve yönetme](machine-tags.md).
**Cihaz değeri**</br> | Cihazın yüksek değer olarak mı yoksa düşük değer olarak mı işaretlendiğine göre listeyi filtreleyin.
**Dışlama durumu** </br> | Cihazın dışlanıp dışlanmadığına göre listeyi filtreleyin. Daha fazla bilgi için bkz. [Cihazları dışlama](exclude-devices.md).
**İşletim Sistemi Platformu** </br>| Araştırmak istediğiniz işletim sistemi platformlarına göre filtreleme </br></br>(_Yalnızca bilgisayarlar ve mobil ve IoT cihazları_)
**İlk kez görüldü** </br> | Cihazınızın ağda ilk görüldüğü veya Uç Nokta için Microsoft Defender algılayıcısı tarafından ilk bildirildiği zaman temelinde görünümünüzü filtreleyin.</br></br>(_Yalnızca bilgisayarlar ve mobil ve IoT cihazları_)
**Windows sürümü** </br> | Araştırmak istediğiniz Windows sürümlerine göre filtreleyin.</br></br> (_Yalnızca bilgisayarlar ve mobil_ cihazlar)
**Algılayıcı sistem durumu** </br> | Uç Nokta için Microsoft Defender eklenen cihazlar için aşağıdaki algılayıcı sistem durumu durumlarına göre filtreleyin:</br> - **Etkin**: Algılayıcı verilerini hizmete etkin olarak bildiren cihazlar.</br> - **Etkin değil**: Sinyal göndermeyi 7 günden fazla durduran cihazlar. </br> - **Yanlış yapılandırılmış**: Hizmetle iletişim bozukluğu olan veya algılayıcı verilerini gönderemeyen cihazlar. </br> Yanlış yapılandırılmış cihazlar şu şekilde sınıflandırılabilir: </br>  - Algılayıcı verisi yok </br>  - Bozuk iletişimler </br>  Yanlış yapılandırılmış cihazlardaki sorunları giderme hakkında daha fazla bilgi için bkz. [İyi durumda olmayan algılayıcıları düzeltme](/microsoft-365/security/defender-endpoint/fix-unhealthy-sensors).</br></br> (_Yalnızca bilgisayarlar ve mobil_ cihazlar)
**Ekleme durumu** </br> | Ekleme durumu, cihazın şu anda Uç Nokta için Microsoft Defender eklenip eklenmediğini gösterir. Aşağıdaki durumlara göre filtreleyebilirsiniz: </br> - **Eklenen**: Uç nokta Uç Nokta için Microsoft Defender eklenir.  </br> - **Eklenebilir**: Uç nokta ağdaki desteklenen bir cihaz olarak bulundu, ancak şu anda eklenmemiş. Microsoft bu cihazları eklemenizi kesinlikle önerir. </br> - **Desteklenmeyen**: Uç nokta ağda bulundu, ancak Uç Nokta için Microsoft Defender tarafından desteklenmiyor. </br> - **Yetersiz bilgi**: Sistem cihazın desteklenebilirliğini belirleyemedi.</br></br> (_Yalnızca bilgisayarlar ve mobil_ cihazlar)
**Virüsten koruma durumu** </br> | Virüsten koruma durumunun devre dışı, güncelleştirilmemiş veya bilinmiyor olmasına göre görünümü filtreleyin.</br></br> (_Yalnızca bilgisayarlar ve mobil_ cihazlar)
**Grup** </br> | Listeyi araştırmak istediğiniz gruba göre filtreleyin. </br></br> (_Yalnızca bilgisayarlar ve mobil_ cihazlar)
**Tarafından yönetilir** </br> | Tarafından yönetilir, cihazın nasıl yönetildiğini gösterir. Filtre ölçütü:</br>- Uç Nokta için Microsoft Defender </br> - Mobil cihaz yönetimi (MDM) </br>- Bilinmiyor: Bunun nedeni eski bir Windows sürümünün çalıştırılması, SCCM'nin yerinde olması veya başka bir üçüncü taraf MDM'sinin olması olabilir.</br></br> (_Yalnızca bilgisayarlar ve mobil_ cihazlar)
**Cihaz Türü** </br> | Araştırmak istediğiniz cihaz türüne göre filtreleyin.</br></br> (_Yalnızca IoT cihazları_)

## <a name="use-columns-to-customize-the-device-inventory-views"></a>Cihaz envanter görünümlerini özelleştirmek için sütunları kullanma

Kullanılabilir bir sütun üst bilgisine tıklayarak görünüme sütun ekleyebilir veya görünümden sütunları kaldırabilir ve girişleri sıralayabilirsiniz.

Kullanılabilir sütunları görmek için **Bilgisayar ve Cep Telefonları** sekmesinde **Sütunları özelleştir'i** seçin. Varsayılan değerler aşağıdaki görüntüde denetlenmektedir:

![Bilgisayarların ve cep telefonlarının görüntüsü](images/computerandmobilescolumns.png)

Kullanılabilir sütunları görmek için **Ağ cihazları** sekmesinde **Sütunları özelleştir'i** seçin. Varsayılan değerler aşağıdaki görüntüde denetlenmektedir:

![Ağ cihazı sütunlarının görüntüsü](images/networkdevicescolumns.png)

Kullanılabilir sütunları görmek için **IoT cihazları** sekmesinde **Sütunları özelleştir'i** seçin. Varsayılan değerler aşağıdaki görüntüde denetlenmektedir:

![IoT cihaz sütunlarının görüntüsü](images/iotdevicescolumns.png)

## <a name="related-articles"></a>İlgili makaleler

[Uç Nokta için Microsoft Defender Cihazlar listesindeki cihazları araştırma](investigate-machines.md)
