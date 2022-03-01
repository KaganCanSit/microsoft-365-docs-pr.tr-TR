---
title: Olay Görüntüleyicisi'ni kullanarak olayları ve hataları gözden geçirme
description: Uç Nokta için Microsoft Defender hizmeti tarafından bildirilen tüm etkinlikler için açıklamaları ve sorun giderme adımlarını (gerekirse) alın.
keywords: sorun giderme, olay görüntüleyicisi, günlük özeti, hata kodu, başarısız, Uç nokta hizmeti için Microsoft Defender, başlatılamadı, bozuk, başlatılamadı
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
ms.date: 05/21/2018
ms.technology: mde
ms.openlocfilehash: a09f034ac35aa3380ea834eafc149eaad9a7cb3d
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62996986"
---
# <a name="review-events-and-errors-using-event-viewer"></a>Olay Görüntüleyicisi'ni kullanarak olayları ve hataları gözden geçirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Olay Görüntüleyicisi
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Tek tek cihazlarda Olay Görüntüleyicisi'nde [olay kimliklerini](https://msdn.microsoft.com/library/aa745633(v=bts.10).aspx) gözden geçirebilirsiniz.

Örneğin, cihazlar Cihazlar listesinde **görünmüyorsa**, cihazlarda olay kimliklerini aramanız gerekir. Bundan sonra, başka sorun giderme adımlarını belirlemek için bu tabloyu kullanabilirsiniz.

**Olay Görüntüleyicisi'ni açın ve Uç nokta hizmet için Microsoft Defender olay günlüğünü bulun:**

1. Başlat **menüsünde** Başlat'Windows, Olay **Görüntüleyicisi yazın** ve Enter tuşuna **basın**.

2. Günlük listesinde, Günlük **Özeti'nin altında** **Microsoft-Windows-SENSE/Operational Windows görene kadar kaydırın**. Günlüğü açmak için öğeye çift tıklayın.

   Ayrıca, Uygulama ve Hizmet Günlükleri **Microsoft'u** \>  \> **genişleterek ve SENSE** \> **Windows'ye tıklar** ve İşlem'e **tıklar.**

   > [!NOTE]
   > SENSE, Uç Nokta için Microsoft Defender'a güç gücü yapan davranışsal algılayıcıya başvurmak için kullanılan iç addır.

3. Hizmet tarafından kaydedilen olaylar günlükte görüntülenir. Hizmet tarafından kaydedilen olayların listesi için aşağıdaki tabloya bakın.

   <br>

   ****

   |Olay Kimliği|İleti|Açıklama|Eylem|
   |---|---|---|---|
   |1|Uç Nokta hizmeti için Microsoft Defender başlatıldı (Sürüm `variable`).|Sistem başlatma, kapatma ve ekleme sırasında gerçekleşir.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |2|Uç nokta hizmetinin kapatılması için Microsoft Defender.'ı seçin.|Cihaz kapatıldı veya çıkarıldı olduğunda gerçekleşir.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |3|Uç Nokta hizmeti için Microsoft Defender başlatılamadı. Hata kodu: `variable`.|Hizmet başlamadı.|Olası neden ve sorun giderme adımlarını belirlemek için diğer iletileri gözden geçirebilirsiniz.|
   |4|Uç Nokta hizmeti için Microsoft Defender sunucuyla bağlantı kurdı `variable`: .|Değişken = Uç nokta işleme sunucuları için Defender URL'si. <p> Bu URL, Güvenlik Duvarı veya ağ etkinliğinde görülen URL ile eşler.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |5|Uç Nokta hizmeti için Microsoft Defender, üzerinden sunucuya bağlanamadı `variable`.|Değişken = Uç nokta işleme sunucuları için Defender URL'si. <p> Hizmet, bu URL'de dış işleme sunucularıyla bağlantı kuramıyor.|URL bağlantısını kontrol edin. Bkz [. Proxy ve İnternet bağlantısını yapılandırma](configure-proxy-internet.md).|
   |6|Uç Nokta hizmeti için Microsoft Defender ekli değildir ve ekleme parametresi bulunamadı.|Cihaz doğru biçimde eklemedi ve portala bildirmiyor.|Hizmeti başlatmadan önce, eklemenin çalıştır olması gerekir. <p> Ekleme ayarlarının ve betiklerin düzgün dağıtıldığından emin olun. Yapılandırma paketlerini yeniden parça <p> Bkz[. Windows 10 cihaz ekleme](configure-endpoints.md).|
   |7|Uç Nokta Hizmeti için Microsoft Defender ekleme parametrelerini okuyamadı. Hata: `variable`.|Değişken = ayrıntılı hata açıklaması. Cihaz doğru biçimde eklemedi ve portala bildirmiyor.|Ekleme ayarlarının ve betiklerin düzgün dağıtıldığından emin olun. Yapılandırma paketlerini yeniden parça <p> Bkz[. Windows 10 cihaz ekleme](configure-endpoints.md).|
   |8|Uç Nokta hizmeti için Microsoft Defender yapılandırmasını temizleyemedi. Hata kodu: `variable`.|**Ekleme sırasında:** Hizmet, ekleme sırasında yapılandırmasını temizleyemedi. Ekleme işlemi devam eder. <p> **Çıkarma sırasında:** Hizmet, çıkar işlemi sırasında yapılandırmasını temizleyemedi. Offboard işlemi tamamlandı ancak hizmet devam ediyor.|**Ekleme:** Herhangi bir işlem gerekmez. <p> **Offboarding:** Sistemi yeniden başlatın. <p> Bkz[. Windows 10 cihaz ekleme](configure-endpoints.md).|
   |9|Uç Nokta hizmeti için Microsoft Defender başlangıç türünü değiştiremedi. Hata kodu: `variable`.|**Ekleme sırasında:** Cihaz doğru biçimde eklemedi ve portala bildirmiyor. <p>**Çıkarma sırasında:** Hizmet başlangıç türü değiştirılamadı. Çıkarma işlemi devam eder. |Ekleme ayarlarının ve betiklerin düzgün dağıtıldığından emin olun. Yapılandırma paketlerini yeniden parça <p> Bkz[. Windows 10 cihaz ekleme](configure-endpoints.md).|
   |10|Uç Nokta hizmeti için Microsoft Defender ekleme bilgilerini kalıcı olarak yükleyemedi. Hata kodu: `variable`.|Cihaz doğru biçimde eklemedi ve portala bildirmiyor.|Ekleme ayarlarının ve betiklerin düzgün dağıtıldığından emin olun. Yapılandırma paketlerini yeniden parça <p> Bkz[. Windows 10 cihaz ekleme](configure-endpoints.md).|
   |11|Uç nokta hizmeti için Defender'ın ekleme veya yeniden eklemesi tamamlandı.|Cihaz doğru şekilde alındı.|Normal işletim bildirimi; herhangi bir işlem gerekmez. <p> Cihazın portalda görünmesi birkaç saat sürebilir.|
   |12|Uç Nokta için Microsoft Defender varsayılan yapılandırmayı uygulayamadı.|Hizmet varsayılan yapılandırmayı uygulayamıyor.|Bu hata kısa bir süre sonra çözülecek.|
   |13|Uç nokta cihaz kimliği için Microsoft Defender hesaplanan: `variable`.|Normal işletim işlemi.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |15|Uç Nokta için Microsoft Defender, KOMUT kanalını URL ile başlatamıyor: `variable`.|Değişken = Uç nokta işleme sunucuları için Defender URL'si. <p> Hizmet, bu URL'de dış işleme sunucularıyla bağlantı kuramıyor.|URL bağlantısını kontrol edin. Bkz [. Proxy ve İnternet bağlantısını yapılandırma](configure-proxy-internet.md).|
   |17|Uç Nokta Hizmeti için Microsoft Defender, Bağlı Kullanıcı Deneyimleri ve Telemetri hizmeti konumunu değiştiremedi. Hata kodu: `variable`.|Telemetri hizmetinin Windows bir hata oluştu.|[Tanılama veri hizmetinin etkinleştirildiğinden emin olun">](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy) Tanılama veri hizmetinin etkinleştirildiğinden emin olun. <p> Ekleme ayarlarının ve betiklerin düzgün dağıtıldığından emin olun. Yapılandırma paketlerini yeniden parça <p> Bkz[. Windows 10 cihaz ekleme](configure-endpoints.md).|
   |18|OOBE (Windows Hoş Geldiniz) tamamlanmıştır.|Hizmet, herhangi bir güncelleştirme Windows tamamladikten sonra başlar.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |19|OOBE (Windows Hoş Geldiniz) henüz tamamlanmamıştır.|Hizmet, herhangi bir güncelleştirme Windows tamamladikten sonra başlar.|Normal işletim bildirimi; herhangi bir işlem gerekmez. <p> Sistem yeniden başlatıldıktan sonra da bu hata devam ederse, tüm Windows güncelleştirmelerinin tam yüklü olduğundan emin olun.|
   |20|OOBE (Hoş Geldiniz) Windows tamamlanacak şekilde bekleyok. Hata kodu: `variable`.|İç hata.|Sistem yeniden başlatıldıktan sonra da bu hata devam ederse, tüm Windows güncelleştirmelerinin tam yüklü olduğundan emin olun.|
   |25|Uç Nokta hizmeti için Microsoft Defender kayıt defterinde durum sıfırlanamadı. Hata kodu: `variable`.|Cihaz doğru şekilde eklemedi. Portala rapor eder, ancak hizmet SCCM'de veya kayıt defterinde kayıtlı olarak görünebiliyor olabilir.|Ekleme ayarlarının ve betiklerin düzgün dağıtıldığından emin olun. Yapılandırma paketlerini yeniden parça <p> Bkz[. Windows 10 cihaz ekleme](configure-endpoints.md).|
   |26|Uç Nokta hizmeti için Microsoft Defender kayıt defterinde ekleme durumunu ayarlayamadı. Hata kodu: `variable`.|Cihaz doğru şekilde eklemedi. <p> Portala rapor eder, ancak hizmet SCCM'de veya kayıt defterinde kayıtlı olarak görünebiliyor olabilir.|Ekleme ayarlarının ve betiklerin düzgün dağıtıldığından emin olun. Yapılandırma paketlerini yeniden parça <p> Bkz[. Windows 10 cihaz ekleme](configure-endpoints.md).|
   |27|Uç Nokta hizmeti için Microsoft Defender, Kullanıcı Modu'Microsoft Defender Virüsten Koruma. Ekleme işlemi başarısız oldu. Hata kodu: `variable`.|Normalde, Microsoft Defender Virüsten Koruma gerçek zamanlı kötü amaçlı yazılımdan koruma ürünü cihazda düzgün şekilde çalışıyorsa ve cihaz Uç Nokta için Defender'a rapor veriyorsa, özel bir pasif durumu girersiniz.|Ekleme ayarlarının ve betiklerin düzgün dağıtıldığından emin olun. Yapılandırma paketlerini yeniden parça <p> Bkz[. Windows 10 cihaz ekleme](configure-endpoints.md). <p> Gerçek zamanlı kötü amaçlı yazılımdan korumanın düzgün çalışıyor olduğundan emin olun.|
   |28|Uç Nokta Bağlantılı Kullanıcı Deneyimleri ve Telemetri hizmeti kaydı için Microsoft Defender başarısız oldu. Hata kodu: `variable`.|Telemetri hizmetinin Windows bir hata oluştu.|[Tanılama veri hizmetinin etkinleştirildiğinden emin olun](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy). <p> Ekleme ayarlarının ve betiklerin düzgün dağıtıldığından emin olun. Yapılandırma paketlerini yeniden parça <p> Bkz[. Windows 10 cihaz ekleme](configure-endpoints.md).|
   |29|Çıkarma parametreleri okunamadı. Hata türü: %1, Hata kodu: %2, Açıklama: %3|Bu olay, sistemin çıkarma parametrelerini okuması durumunda oluşur.|Cihazın İnternet erişimi olduğundan emin olun ve ardından tüm çıkar işlemini yeniden çalıştırın. Çıkartan kullanım paketinin süresinin dolmamış olduğundan emin olmak.|
   |30|Uç Nokta hizmeti için Microsoft Defender, Kullanıcı Modu'Microsoft Defender Virüsten Koruma. Hata kodu: `variable`.|Normalde, Microsoft Defender Virüsten Koruma gerçek zamanlı kötü amaçlı yazılımdan koruma ürünü cihazda düzgün şekilde çalışıyorsa ve cihaz Uç Nokta için Defender'a rapor veriyorsa, özel bir pasif durumu girersiniz.|Ekleme ayarlarının ve betiklerin düzgün dağıtıldığından emin olun. Yapılandırma paketlerini yeniden parça <p> Bkz[. Windows 10 cihaz ekleme](configure-endpoints.md). <p> Gerçek zamanlı kötü amaçlı yazılımdan korumanın düzgün çalışıyor olduğundan emin olun.|
   |31|Uç Nokta Bağlantılı Kullanıcı Deneyimleri ve Telemetri hizmeti için Microsoft Defender kaydı başarısız oldu. Hata kodu: `variable`.|Ekleme sırasında telemetri Windows bir hata oluştu. Çıkarma işlemi devam eder.|[Telemetri hizmetiyle ilgili Windows denetleyin](troubleshoot-onboarding.md#ensure-the-diagnostic-data-service-is-enabled).|
   |32|Uç Nokta hizmeti için Microsoft Defender, kendisiyle çıkar işlemi tamamlanamadıktan sonra bunu durduramadı. Hata kodu: %1|Çıkarma sırasında bir hata oluştu.|Cihazı yeniden başlatın.|
   |33|Uç Nokta hizmeti için Microsoft Defender SENSE GUID'in kalıcı olarak başarısız oldu. Hata kodu: `variable`.|Portala rapor eden her cihazı temsil eden benzersiz bir tanımlayıcı kullanılır. <p> Tanımlayıcı kalıcı olmazsa, portalda aynı cihaz iki kez görünebilir.|Hizmetin kayıt defterini güncelleştire olduğundan emin olmak için cihazda kayıt defteri izinlerini denetleyin.|
   |34|Uç Nokta hizmeti için Microsoft Defender kendini Bağlı Kullanıcı Deneyimleri ve Telemetri hizmetine bağımlılık olarak ekleyemedi ve bu da ekleme işleminin başarısız olmasına neden oldu. Hata kodu: `variable`.|Telemetri hizmetinin Windows bir hata oluştu.|[Tanılama veri hizmetinin etkinleştirildiğinden emin olun](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy). <p> Ekleme ayarlarının ve betiklerin düzgün dağıtıldığından emin olun. Yapılandırma paketlerini yeniden parça <p> Bkz[. Windows 10 cihaz ekleme](configure-endpoints.md).|
   |35|Uç Nokta hizmeti için Microsoft Defender, Bağlı Kullanıcı Deneyimleri ve Telemetri hizmetine bağımlılık olarak kendini kaldıramadı. Hata kodu: `variable`.|Çıkarma sırasında telemetri Windows bir hata oluştu. Çıkarma işlemi devam eder.|Tanılama veri hizmetiyle hataları Windows denetleyin.|
   |36|Uç Nokta Bağlantılı Kullanıcı Deneyimleri ve Telemetri hizmeti kaydı için Microsoft Defender başarılı oldu. Tamamlanma kodu: `variable`.|Bağlı Kullanıcı Deneyimleri ve Telemetri hizmetinin başarıyla tamamlandıktan sonra Uç Nokta için Defender'a kaydetme.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |37|Uç Nokta için Microsoft Defender Modülün kotası aşacak. Modül: %1, Kota: {%2} {%3}, Kota yüzdesi kullanımı: %4.|Cihaz, geçerli 24 saatlik pencerenin ayrılan kotasını neredeyse kullandı. Kısıtlamak için çok küçük bir iştir.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |38|Ağ bağlantısı, düşük olarak tanımlanır. Uç Nokta için Microsoft Defender her %1 dakikada bir sunucuyla bağlantı kuracak. Tarifeli bağlantı: %2, İnternet kullanılabilir: %3, ücretsiz ağ kullanılabilir: %4.|Cihaz tarifeli/ücretli bir ağ kullanıyor ve sunucuyla daha az bağlantı kuracak.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |39|Ağ bağlantısı normal olarak tanımlanır. Uç Nokta için Microsoft Defender her %1 dakikada bir sunucuyla bağlantı kuracak. Tarifeli bağlantı: %2, İnternet kullanılabilir: %3, ücretsiz ağ kullanılabilir: %4.|Cihaz tarifeli/ücretli bağlantı kullanmaz ve her zamanki gibi sunucuyla bağlantı kuracak.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |40|Pil durumu, düşük olarak tanımlanır. Uç Nokta için Microsoft Defender her %1 dakikada bir sunucuyla bağlantı kuracak. Pil durumu: %2.|Cihaz pil düzeyi düşüktür ve daha az sıklıkta sunucuyla bağlantı kuracak.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |41|Pil durumu normal olarak tanımlanır. Uç Nokta için Microsoft Defender her %1 dakikada bir sunucuyla bağlantı kuracak. Pil durumu: %2.|Cihaz pil düzeyi düşük değil ve her zamanki gibi sunucuyla bağlantı kuracak.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |42|Uç Nokta bileşeni için Microsoft Defender eylem gerçekleştiremedi. Bileşen: %1, Eylem: %2, Özel Durum Türü: %3, Özel durum iletisi: %4|İç hata. Hizmet başlatılamadı.|Bu hata devam ederse Destek ile iletişime geçin.|
   |43|Uç Nokta bileşeni için Microsoft Defender eylem gerçekleştiremedi. Bileşen: %1, Eylem: %2, Özel Durum Türü: %3, Özel Durum Hatası: %4, Özel durum iletisi: %5|İç hata. Hizmet başlatılamadı.|Bu hata devam ederse Destek ile iletişime geçin.|
   |44|Uç nokta hizmeti için Defender'ın offboarding tamamlandı.|Hizmet çıkarıldı.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |45|Kayıt işlemi başarısız oldu ve olay izleme oturumu başlatılamadı [%1]. Hata kodu: %2|ETW oturumu oluşturulurken hizmet başlatma sırasında bir hata oluştu. Bu, hizmet başlatma hatasına neden oldu.|Bu hata devam ederse Destek ile iletişime geçin.|
   |46|Kaynak olmaması nedeniyle olay izleme oturumu [%1] kaydediemedi ve başlatılamadı. Hata kodu: %2. Bunun nedeni büyük olasılıkla çok fazla etkin etkinlik izleme oturumu olmasıdır. Hizmet 1 dakika içinde yeniden denenecek.|EtW oturumu oluşturulurken kaynak olmaması nedeniyle hizmet başlatma sırasında bir hata oluştu. Hizmet başlatıldı ve çalışıyor, ancak ETW oturumu başlayana kadar algılayıcı etkinliklerini bildirmez.|Normal işletim bildirimi; herhangi bir işlem gerekmez. Hizmet, oturumu dakikalar içinde başlatmayı dener.|
   |47|Olay izleme oturumu başarıyla kaydedildi ve başlatıldı - önceki başarısız girişimler sonrasında kurtarıldı.|Bu olay, ETW oturumu başarıyla başlatıldıktan sonra önceki etkinliği izler.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |48|[%2] olay izleme oturumuna [%1] sağlayıcı eklenemedi. Hata kodu: %3. Bu, bu sağlayıcıdan gelen olayların bildirilemayacak olduğu anlamına gelir.|ETW oturumuna sağlayıcı eklenemedi. Sonuç olarak, sağlayıcı olayları bildir değildir.|Hata kodunu kontrol edin. Hata devam ederse Destek ile iletişime geçin.|
   |49|Geçersiz bulut yapılandırması komutu alındı ve yoksayıldı. Sürüm: %1, durum: %2, hata kodu: %3, ileti: %4|Bulut hizmeti tarafından yok sayılan geçersiz bir yapılandırma dosyası alındı.|Bu hata devam ederse Destek ile iletişime geçin.|
   |50|Yeni bulut yapılandırması başarıyla uygulandı. Sürüm: %1.|Bulut hizmetinin yeni yapılandırması başarıyla uygulandı.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |51|Yeni bulut yapılandırması uygulanamadı, sürüm: %1. Bilinen son iyi yapılandırma olan %2 sürümü başarıyla uygulandı.|Bulut hizmetlerinden hatalı bir yapılandırma dosyası alındı. Bilinen son iyi yapılandırma başarıyla uygulandı.|Bu hata devam ederse Destek ile iletişime geçin.|
   |52|Yeni bulut yapılandırması uygulanamadı, sürüm: %1. Ayrıca bilinen son iyi yapılandırma olan %2 sürümü uygulanamadı. Varsayılan yapılandırma başarıyla uygulandı.|Bulut hizmetlerinden hatalı bir yapılandırma dosyası alındı. Bilinen en son iyi yapılandırma uygulanamadı ve varsayılan yapılandırma uygulandı.|Hizmet, 5 dakika içinde yeni bir yapılandırma dosyası indirmeyi denecek. Olay #50'leri görmüyorsanız Destek'e başvurun.|
   |53|Kalıcı depolama sürümünden bulut yapılandırması yüklendi: %1.|Yapılandırma, hizmet başlangıçtaki kalıcı depolamadan yüklendi.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |55|Secure ETW otomatik günlüğü oluşturulamadı. Hata kodu: %1|Güvenli ETW logger oluşturulamadı.|Cihazı yeniden başlatın. Bu hata devam ederse Destek ile iletişime geçin.|
   |56|Secure ETW otomatik günlüğü kaldırılamadı. Hata kodu: %1|Çıkarma sırasında güvenli ETW oturumu kaldırılamadı.|Destek'e başvurun.|
   |57|Sorun giderme amacıyla makinenin anlık görüntüsünü yakalama.|Araştırma paketi olarak da bilinen araştırma paketi toplanıyor.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |59|Başlat komutu: %1|Yanıt komutunu yürütmeyi başlatma.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |60|%1 komutu çalıştırılamadı, hata: %2.|Yanıt komutu yürütülemedi.|Bu hata devam ederse Destek ile iletişime geçin.|
   |61|Veri toplama komutu parametreleri geçersiz: SasUri: %1, compressionLevel: %2.|Veri toplama komutu bağımsız değişkenleri (geçersiz bağımsız değişkenler) okunamadı veya ayrıştırılamadı.|Bu hata devam ederse Destek ile iletişime geçin.|
   |62|Bağlı Kullanıcı Deneyimleri ve Telemetri hizmeti başlatılamadı. Hata kodu: %1|Bağlı Kullanıcı Deneyimleri ve Telemetri (diagtrack) hizmeti başlatılamadı. Uç nokta telemetrisi için Microsoft Defender olmayanlar bu makineden gönderilmez.|Olay günlüğünde daha fazla sorun giderme ipucu bulun: Microsoft-Windows-UniversalTelemetryClient/Operational.|
   |63|Dış hizmetin başlangıç türünü güncelleştirme. Ad: %1, gerçek başlangıç türü: %2, beklenen başlangıç türü: %3, çıkış kodu: %4|Güncelleştirilmiş dış hizmetin başlangıç türü.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |64|Başlangıç durduruldu dış hizmet. Ad: %1, çıkış kodu: %2|Bir dış hizmet başlatma.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |65|Microsoft Güvenlik Olayları Bileşen Mini Filtre sürücüsü yüklenemedi. Hata kodu: %1|Dosya sistemi mini MsSecFlt.sys yüklenemedi.|Cihazı yeniden başlatın. Bu hata devam ederse Destek ile iletişime geçin.|
   |66|İlke güncelleştirmesi: Gecikme modu - %1|C&C bağlantı sıklığı ilkesi güncelleştirilmiştir.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |68|Hizmetin başlangıç türü beklenmedik bir durum. Hizmet adı: %1, gerçek başlangıç türü: %2, beklenen başlangıç türü: %3|Beklenmeyen dış hizmet başlangıç türü.|Dış hizmet başlangıç türünü düzeltin.|
   |69|Hizmet durduruldu. Hizmet adı: %1|Dış hizmet durduruldu.|Dış hizmeti başlatma.|
   |70|İlke güncelleştirmesi: Örnek koleksiyona izin ver - %1|Örnek koleksiyon ilkesi güncelleştirildi.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |71|Çalıştırıldı komutu başarılı oldu: %1|Komut başarıyla yürütülür.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |72|İlk tam makine profili raporunu göndermeyi deneildi. Sonuç kodu: %1|Yalnızca bilgilendirme.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |73|Platform için mantıklı başlangıç: %1|Yalnızca bilgilendirme.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |74|Kayıt defterindeki cihaz etiketi uzunluk sınırını aşıyor. Etiket adı: %2. Uzunluk sınırı: %1.|Cihaz etiketi uzunluk sınırını aşıyor.|Daha kısa bir cihaz etiketi kullanın.|
   |81|Endpoint ETW autologger için Microsoft Defender oluşturulamadı. Hata kodu: %1|ETW oturumu oluşturulamadı.|Cihazı yeniden başlatın. Bu hata devam ederse Destek ile iletişime geçin.|
   |82|Endpoint ETW autologger için Microsoft Defender kaldırılamadı. Hata kodu: %1|ETW oturumu silinemedi.|Destek'e başvurun.|
   |84|Çalışma Windows Defender Virüsten Koruma ayarlama. Pasif modunu zorlama: %1, sonuç kodu: %2.|Defender çalıştırma modunu ayarlama (etkin veya pasif).|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |85|Uç nokta yürütülebilir dosyası için Microsoft Defender tetiklanamadı. Hata kodu: %1|SenseIR yürütülebilir dosyası yürütülebilir olarak yürütülebilir olarak yürütülemedi.|Cihazı yeniden başlatın. Bu hata devam ederse Destek ile iletişime geçin.|
   |86|Yeniden başlat, olması gereken dış hizmeti durdurdu. Ad: %1, çıkış kodu: %2|Dış hizmeti yeniden başlatıyor.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |87|Dış hizmet başlat değil. Ad: %1|Dış hizmet başlatılamadı.|Destek'e başvurun.|
   |88|Dış hizmetin başlangıç türü yeniden güncelleştiriliyor. Ad: %1, gerçek başlangıç türü: %2, beklenen başlangıç türü: %3, çıkış kodu: %4|Dış hizmetin başlangıç türü güncelleştirildi.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |89|Dış hizmetin başlangıç türü güncelleştirile değil. Ad: %1, gerçek başlangıç türü: %2, beklenen başlangıç türü: %3|Dış hizmetin başlangıç türü güncelleştirile değil.|Destek'e başvurun.|
   |90|%1 coğrafi bölgedeki bulut hizmetine bağlanacak şekilde System Guard Çalışma Zamanı İzleyicisi yapılandırılamadı. Hata kodu: %2|System Guard Çalışma Zamanı İzleyicisi, bulut hizmetine attestation verileri göndermez.|Yazmama yolu üzerinde izinleri denetleyin: "HKLM\Software\Microsoft\Windows\CurrentVersion\Sgrm". Sorun olmazsa Destek ile iletişime geçin.|
   |91|System Guard Çalışma Zamanı İzleyicisi coğrafi bölge bilgileri kaldırılamadı. Hata kodu: %1|System Guard Çalışma Zamanı İzleyicisi, bulut hizmetine attestation verileri göndermez.|Yazmama yolu üzerinde izinleri denetleyin: "HKLM\Software\Microsoft\Windows\CurrentVersion\Sgrm". Sorun olmazsa Destek ile iletişime geçin.|
   |92|Veri kotası aşılırken algılayıcı siber veri kotasının gönderilmesi durduruluyor. Kota dönemi geçtikten sonra göndermeye devam eder. Durum Maskesi: %1|Azaltma sınırını aş.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |93|Algılayıcı siber verileri göndermeye devam ediyor. Durum Maskesi: %1|Siber veri gönderimi sürdür.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |94|Uç nokta yürütülebilir dosyası için Microsoft Defender başlatıldı|SenseCE yürütülebilir dosyası başlatıldı.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |95|Uç nokta yürütülebilir dosyası için Microsoft Defender sona erdi|SenseCE yürütülebilir dosyası sona erdi.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |96|Endpoint Init için Microsoft Defender'ın çağrısı. Sonuç kodu: %2|SenseCE yürütülebilir dosyası MCE başlatma olarak anlır.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |97|DLP senaryosu için Bulut'un bağlantı sorunları vardır|DLP sınıflandırma akışını etkileyen ağ bağlantısı sorunları vardır.|Ağ bağlantısını denetleyin.|
   |98|DLP senaryosu için Bulut bağlantısı geri yüklendi|Ağ bağlantısı geri yüklendi ve DLP sınıflandırma akışı devam ediyor olabilir.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |99|Algı, sunucuyla iletişim kurarken şu hatayla karşılaştı: (%1). Sonuç: (%2)|Bir iletişim hatası oluştu.|Diğer ayrıntılar için olay günlüğünde aşağıdaki olayları kontrol edin.|
   |100|Uç nokta yürütülebilir dosyası için Microsoft Defender başlatılamadı. Hata kodu: %1|SenseCE yürütülebilir dosyası başlatılamadı.|Cihazı yeniden başlatın. Bu hata devam ederse Destek ile iletişime geçin.|
   |102|Uç Nokta Ağ Algılama ve Yanıt yürütülebilir dosyası için Microsoft Defender başlatıldı|SenseNdr yürütülebilir dosyası başlatıldı.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |103|Uç Nokta Ağ Algılama ve Yanıt yürütülebilir dosyası için Microsoft Defender sona erdi|SenseNdr yürütülebilir dosyası sona erdi.|Normal işletim bildirimi; herhangi bir işlem gerekmez.|
   |

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-eventerrorcodes-belowfoldlink)

## <a name="see-also"></a>Ayrıca bkz.
- [Cihaz Windows 10 ekleme](configure-endpoints.md)
- [Cihaz ara sunucusunu ve İnternet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md)
- [Uç Nokta için Microsoft Defender Sorunlarını Giderme](troubleshoot-onboarding.md)
- [İstemci çözümleyicisi genel bakış](overview-client-analyzer.md)
- [İstemci çözümleyicisini indirme ve çalıştırma](download-client-analyzer.md)
- [Çözümleyici HTML raporunu anlama](analyzer-report.md)