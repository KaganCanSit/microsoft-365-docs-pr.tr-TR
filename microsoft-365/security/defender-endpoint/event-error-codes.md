---
title: Olay Görüntüleyicisi kullanarak olayları ve hataları gözden geçirme
description: Uç Nokta için Microsoft Defender hizmeti tarafından bildirilen tüm olaylar için açıklamaları ve diğer sorun giderme adımlarını (gerekirse) alın.
keywords: sorun giderme, olay görüntüleyicisi, günlük özeti, hata kodu, başarısız, Uç Nokta için Microsoft Defender hizmeti, başlatılamıyor, bozuk, başlatılamıyor
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
ms.openlocfilehash: a598361851593fc84a06e9c4a1ef94e3ed6e1fba
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554301"
---
# <a name="review-events-and-errors-using-event-viewer"></a>Olay Görüntüleyicisi kullanarak olayları ve hataları gözden geçirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- Olay Görüntüleyicisi
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Olay kimliklerini tek tek [cihazlardaki Olay Görüntüleyicisi](https://msdn.microsoft.com/library/aa745633(v=bts.10).aspx) inceleyebilirsiniz.

Örneğin cihazlar **Cihazlar listesinde** görünmüyorsa cihazlarda olay kimliklerini aramanız gerekebilir. Daha sonra bu tabloyu kullanarak diğer sorun giderme adımlarını belirleyebilirsiniz.

**Olay Görüntüleyicisi açın ve Uç Nokta için Microsoft Defender hizmeti olay günlüğünü bulun:**

1. Windows menüsünde **Başlat'a** tıklayın, **Olay Görüntüleyicisi** yazın ve **Enter tuşuna** basın.

2. Günlük listesinde, **Günlük Özeti'nin** altında **Microsoft-Windows-SENSE/Operasyonel** ifadesini görene kadar kaydırın. Günlüğü açmak için öğeye çift tıklayın.

   Ayrıca Microsoft **Windows** \> **SENSE** **Uygulama ve Hizmet Günlükleri'ni** \>  \> genişletip İşletimsel'e tıklayarak da **günlüğe erişebilirsiniz**.

   > [!NOTE]
   > SENSE, Uç Nokta için Microsoft Defender destekleyen davranış algılayıcısına başvurmak için kullanılan iç addır.

3. Hizmet tarafından kaydedilen olaylar günlükte görünür. Hizmet tarafından kaydedilen olayların listesi için aşağıdaki tabloya bakın.

   <br>

   ****

   |Olay Kimliği|İleti|Açıklama|Eylem|
   |---|---|---|---|
   |1|Uç Nokta için Microsoft Defender hizmeti başlatıldı (Sürüm `variable`).|Sistem başlatma, kapatma ve ekleme sırasında gerçekleşir.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |2|Uç Nokta için Microsoft Defender hizmet kapatma.|Cihaz kapatıldığında veya kapatıldığında gerçekleşir.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |3|Uç Nokta için Microsoft Defender hizmeti başlatılamadı. Hata kodu: `variable`.|Hizmet başlatılmadı.|Olası neden ve sorun giderme adımlarını belirlemek için diğer iletileri gözden geçirin.|
   |4|Uç Nokta için Microsoft Defender hizmeti konumundaki `variable`sunucuyla iletişim kurdu.|Değişken = Uç Nokta işleme sunucuları için Defender URL'si. <p> Bu URL, Güvenlik Duvarı veya ağ etkinliğinde görülen url ile eşleşecektir.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |5|Uç Nokta için Microsoft Defender hizmeti konumundaki `variable`sunucuya bağlanamadı.|Değişken = Uç Nokta işleme sunucuları için Defender URL'si. <p> Hizmet, bu URL'deki dış işleme sunucularına başvuramadı.|URL bağlantısını denetleyin. Bkz [. Ara sunucu ve İnternet bağlantısını yapılandırma](configure-proxy-internet.md).|
   |6|Uç Nokta için Microsoft Defender hizmeti eklenmedi ve ekleme parametresi bulunamadı.|Cihaz doğru şekilde eklemedi ve portala rapor vermiyor.|Hizmeti başlatmadan önce ekleme çalıştırılmalıdır. <p> Ekleme ayarlarının ve betiklerinin düzgün dağıtılıp dağıtılmadığını denetleyin. Yapılandırma paketlerini yeniden dağıtmayı deneyin. <p> Bkz[. Windows 10 cihazları ekleme](configure-endpoints.md).|
   |7|Uç Nokta için Microsoft Defender hizmeti ekleme parametrelerini okuyamadı. Hata: `variable`.|Değişken = ayrıntılı hata açıklaması. Cihaz doğru şekilde eklemedi ve portala rapor vermiyor.|Ekleme ayarlarının ve betiklerinin düzgün dağıtılıp dağıtılmadığını denetleyin. Yapılandırma paketlerini yeniden dağıtmayı deneyin. <p> Bkz[. Windows 10 cihazları ekleme](configure-endpoints.md).|
   |8|Uç Nokta için Microsoft Defender hizmeti yapılandırmasını temizleyemedi. Hata kodu: `variable`.|**Ekleme sırasında:** Hizmet, ekleme sırasında yapılandırmasını temizleyemedi. Ekleme işlemi devam eder. <p> **Çıkarma sırasında:** Hizmet, çıkarma sırasında yapılandırmasını temizleyemedi. Çıkarma işlemi tamamlandı, ancak hizmet çalışmaya devam ediyor.|**Ekleme:** Eylem gerekmez. <p> **Çıkarma:** Sistemi yeniden başlatın. <p> Bkz[. Windows 10 cihazları ekleme](configure-endpoints.md).|
   |9|Uç Nokta için Microsoft Defender hizmeti başlangıç türünü değiştiremedi. Hata kodu: `variable`.|**Ekleme sırasında:** Cihaz doğru şekilde eklemedi ve portala rapor vermiyor. <p>**Çıkarma sırasında:** Hizmet başlangıç türü değiştirılamadı. Çıkarma işlemi devam eder. |Ekleme ayarlarının ve betiklerinin düzgün dağıtılıp dağıtılmadığını denetleyin. Yapılandırma paketlerini yeniden dağıtmayı deneyin. <p> Bkz[. Windows 10 cihazları ekleme](configure-endpoints.md).|
   |10|Uç Nokta için Microsoft Defender hizmeti ekleme bilgilerini kalıcı hale alamadı. Hata kodu: `variable`.|Cihaz doğru şekilde eklemedi ve portala rapor vermiyor.|Ekleme ayarlarının ve betiklerinin düzgün dağıtılıp dağıtılmadığını denetleyin. Yapılandırma paketlerini yeniden dağıtmayı deneyin. <p> Bkz[. Windows 10 cihazları ekleme](configure-endpoints.md).|
   |11|Uç Nokta için Defender hizmetinin ekleme veya yeniden ekleme işlemi tamamlandı.|Cihaz doğru şekilde eklenmiştir.|Normal çalışma bildirimi; eyleme gerek yoktur. <p> Cihazın portalda görünmesi birkaç saat sürebilir.|
   |12|Uç Nokta için Microsoft Defender varsayılan yapılandırma uygulanamadı.|Hizmet varsayılan yapılandırmayı uygulayamadı.|Bu hata kısa bir süre sonra çözülmelidir.|
   |13|Uç Nokta için Microsoft Defender cihaz kimliği hesaplandı: `variable`.|Normal çalışma süreci.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |15|Uç Nokta için Microsoft Defender, komut kanalını URL ile başlatamaz: `variable`.|Değişken = Uç Nokta işleme sunucuları için Defender URL'si. <p> Hizmet, bu URL'deki dış işleme sunucularına başvuramadı.|URL bağlantısını denetleyin. Bkz [. Ara sunucu ve İnternet bağlantısını yapılandırma](configure-proxy-internet.md).|
   |17|Uç Nokta için Microsoft Defender hizmeti Bağlı Kullanıcı Deneyimleri ve Telemetri hizmeti konumunu değiştiremedi. Hata kodu: `variable`.|Windows telemetri hizmetinde bir hata oluştu.|[Tanılama veri hizmetinin etkinleştirildiğinden emin olun](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)">Tanılama veri hizmetinin etkinleştirildiğinden emin olun. <p> Ekleme ayarlarının ve betiklerinin düzgün dağıtılıp dağıtılmadığını denetleyin. Yapılandırma paketlerini yeniden dağıtmayı deneyin. <p> Bkz[. Windows 10 cihazları ekleme](configure-endpoints.md).|
   |18|OOBE (Windows'a Hoş Geldiniz) tamamlandı.|Hizmet yalnızca tüm Windows güncelleştirmelerinin yüklenmesi tamamlandıktan sonra başlatılır.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |19|OOBE (Windows'a Hoş Geldiniz) henüz tamamlanmadı.|Hizmet yalnızca tüm Windows güncelleştirmelerinin yüklenmesi tamamlandıktan sonra başlatılır.|Normal çalışma bildirimi; eyleme gerek yoktur. <p> Sistem yeniden başlatıldıktan sonra bu hata devam ederse tüm Windows güncelleştirmelerinin tam yüklü olduğundan emin olun.|
   |20|OOBE'nin (Windows'a Hoş Geldiniz) tamamlanması beklenemiyor. Hata kodu: `variable`.|İç hata.|Sistem yeniden başlatıldıktan sonra bu hata devam ederse tüm Windows güncelleştirmelerinin tam yüklü olduğundan emin olun.|
   |25|Uç Nokta için Microsoft Defender hizmeti kayıt defterinde sistem durumunu sıfırlayamadı. Hata kodu: `variable`.|Cihaz doğru şekilde eklemedi. Portala raporlanır, ancak hizmet SCCM'de veya kayıt defterinde kayıtlı olarak görünmeyebilir.|Ekleme ayarlarının ve betiklerinin düzgün dağıtılıp dağıtılmadığını denetleyin. Yapılandırma paketlerini yeniden dağıtmayı deneyin. <p> Bkz[. Windows 10 cihazları ekleme](configure-endpoints.md).|
   |26|Uç Nokta için Microsoft Defender hizmeti kayıt defterinde ekleme durumunu ayarlayamadı. Hata kodu: `variable`.|Cihaz doğru şekilde eklemedi. <p> Portala raporlanır, ancak hizmet SCCM'de veya kayıt defterinde kayıtlı olarak görünmeyebilir.|Ekleme ayarlarının ve betiklerinin düzgün dağıtılıp dağıtılmadığını denetleyin. Yapılandırma paketlerini yeniden dağıtmayı deneyin. <p> Bkz[. Windows 10 cihazları ekleme](configure-endpoints.md).|
   |27|Uç Nokta için Microsoft Defender hizmeti Microsoft Defender Virüsten Koruma'da SENSE algılama modunu etkinleştiremedi. Ekleme işlemi başarısız oldu. Hata kodu: `variable`.|Normalde, cihazda başka bir gerçek zamanlı kötü amaçlı yazılımdan koruma ürünü düzgün çalışıyorsa ve cihaz Uç Nokta için Defender'a bildiriyorsa, Microsoft Defender Virüsten Koruma özel bir pasif duruma girer.|Ekleme ayarlarının ve betiklerinin düzgün dağıtılıp dağıtılmadığını denetleyin. Yapılandırma paketlerini yeniden dağıtmayı deneyin. <p> Bkz[. Windows 10 cihazları ekleme](configure-endpoints.md). <p> Gerçek zamanlı kötü amaçlı yazılımdan korumanın düzgün çalıştığından emin olun.|
   |28|Uç Nokta için Microsoft Defender Bağlı Kullanıcı Deneyimleri ve Telemetri hizmeti kaydı başarısız oldu. Hata kodu: `variable`.|Windows telemetri hizmetinde bir hata oluştu.|[Tanılama veri hizmetinin etkinleştirildiğinden emin olun](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy). <p> Ekleme ayarlarının ve betiklerinin düzgün dağıtılıp dağıtılmadığını denetleyin. Yapılandırma paketlerini yeniden dağıtmayı deneyin. <p> Bkz[. Windows 10 cihazları ekleme](configure-endpoints.md).|
   |29|Çıkarma parametreleri okunamadı. Hata türü: %1, Hata kodu: %2, Açıklama: %3|Bu olay, sistem çıkarma parametrelerini okuyamayınca oluşur.|Cihazın İnternet erişimi olduğundan emin olun, ardından tüm çıkarma işlemini yeniden çalıştırın. Çıkarma paketinin süresinin dolmadığından emin olun.|
   |30|Uç Nokta için Microsoft Defender hizmeti Microsoft Defender Virüsten Koruma'da SENSE algılama modunu devre dışı bırakamadı. Hata kodu: `variable`.|Normalde, cihazda başka bir gerçek zamanlı kötü amaçlı yazılımdan koruma ürünü düzgün çalışıyorsa ve cihaz Uç Nokta için Defender'a bildiriyorsa, Microsoft Defender Virüsten Koruma özel bir pasif duruma girer.|Ekleme ayarlarının ve betiklerinin düzgün dağıtılıp dağıtılmadığını denetleyin. Yapılandırma paketlerini yeniden dağıtmayı deneyin. <p> Bkz[. Windows 10 cihazları ekleme](configure-endpoints.md). <p> Gerçek zamanlı kötü amaçlı yazılımdan korumanın düzgün çalıştığından emin olun.|
   |31|Uç Nokta için Microsoft Defender Bağlı Kullanıcı Deneyimleri ve Telemetri hizmetinin kaydı silinemedi. Hata kodu: `variable`.|Ekleme sırasında Windows telemetri hizmetinde bir hata oluştu. Çıkarma işlemi devam eder.|[Windows telemetri hizmetiyle ilgili hataları denetleyin](troubleshoot-onboarding.md#ensure-the-diagnostic-data-service-is-enabled).|
   |32|Uç Nokta için Microsoft Defender hizmeti, çıkarma işleminden sonra kendisini durdurma isteğinde bulunamadı. Hata kodu: %1|Çıkarma sırasında bir hata oluştu.|Cihazı yeniden başlatın.|
   |33|Uç Nokta için Microsoft Defender hizmeti SENSE GUID'sini kalıcı hale alamadı. Hata kodu: `variable`.|Portala rapor veren her cihazı temsil etmek için benzersiz bir tanımlayıcı kullanılır. <p> Tanımlayıcı kalıcı olmazsa aynı cihaz portalda iki kez görünebilir.|Hizmetin kayıt defterini güncelleştirediğinden emin olmak için cihazdaki kayıt defteri izinlerini denetleyin.|
   |34|Uç Nokta için Microsoft Defender hizmeti, Bağlı Kullanıcı Deneyimleri ve Telemetri hizmetine bağımlılık olarak kendini ekleyemedi ve ekleme işleminin başarısız olmasına neden oldu. Hata kodu: `variable`.|Windows telemetri hizmetinde bir hata oluştu.|[Tanılama veri hizmetinin etkinleştirildiğinden emin olun](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy). <p> Ekleme ayarlarının ve betiklerinin düzgün dağıtılıp dağıtılmadığını denetleyin. Yapılandırma paketlerini yeniden dağıtmayı deneyin. <p> Bkz[. Windows 10 cihazları ekleme](configure-endpoints.md).|
   |35|Uç Nokta için Microsoft Defender hizmeti, Bağlı Kullanıcı Deneyimleri ve Telemetri hizmetine bağımlılık olarak kendisini kaldıramadı. Hata kodu: `variable`.|Çıkarma sırasında Windows telemetri hizmetinde bir hata oluştu. Çıkarma işlemi devam eder.|Windows tanılama veri hizmetiyle ilgili hataları denetleyin.|
   |36|Uç Nokta için Microsoft Defender Bağlı Kullanıcı Deneyimleri ve Telemetri hizmeti kaydı başarılı oldu. Tamamlanma kodu: `variable`.|Uç Nokta için Defender'ı Bağlı Kullanıcı Deneyimleri ve Telemetri hizmetiyle kaydetme işlemi başarıyla tamamlandı.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |37|Uç Nokta için Microsoft Defender Bir modül kotasını aşmak üzeredir. Modül: %1, Kota: {%2} {%3}, Kota kullanım yüzdesi: %4.|Cihaz, geçerli 24 saatlik zaman aralığı için ayrılan kotasını neredeyse kullanmıştır. Kısıtlamak üzere.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |38|Ağ bağlantısı düşük olarak tanımlanır. Uç Nokta için Microsoft Defender her %1 dakikada bir sunucuyla iletişim kuracak. Tarifeli bağlantı: %2, İnternet kullanılabilir: %3, kullanılabilir ücretsiz ağ: %4.|Cihaz tarifeli/ücretli bir ağ kullanıyor ve daha az sıklıkta sunucuyla iletişim kuracak.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |39|Ağ bağlantısı normal olarak tanımlanır. Uç Nokta için Microsoft Defender her %1 dakikada bir sunucuyla iletişim kuracak. Tarifeli bağlantı: %2, İnternet kullanılabilir: %3, kullanılabilir ücretsiz ağ: %4.|Cihaz tarifeli/ücretli bağlantı kullanmıyor ve her zamanki gibi sunucuyla iletişim kuracak.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |40|Pil durumu düşük olarak tanımlanır. Uç Nokta için Microsoft Defender her %1 dakikada bir sunucuyla iletişim kuracak. Pil durumu: %2.|Cihaz düşük pil düzeyine sahiptir ve sunucuyla daha az sıklıkta iletişim kurar.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |41|Pil durumu normal olarak tanımlanır. Uç Nokta için Microsoft Defender her %1 dakikada bir sunucuyla iletişim kuracak. Pil durumu: %2.|Cihaz düşük pil düzeyine sahip değildir ve her zamanki gibi sunucuyla iletişim kurar.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |42|Uç Nokta için Microsoft Defender bileşeni eylem gerçekleştiremedi. Bileşen: %1, Eylem: %2, Özel Durum Türü: %3, Özel durum iletisi: %4|İç hata. Hizmet başlatılamadı.|Bu hata devam ederse Destek'e başvurun.|
   |43|Uç Nokta için Microsoft Defender bileşeni eylem gerçekleştiremedi. Bileşen: %1, Eylem: %2, Özel Durum Türü: %3, Özel Durum Hatası: %4, Özel durum iletisi: %5|İç hata. Hizmet başlatılamadı.|Bu hata devam ederse Destek'e başvurun.|
   |44|Uç Nokta için Defender hizmetinin kullanıma hazırlanması tamamlandı.|Hizmet devre dışı bırakıldı.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |45|[%1] olay izleme oturumu kaydedilemedi ve başlatılamadı. Hata kodu: %2|ETW oturumu oluşturulurken hizmet başlatma sırasında bir hata oluştu. Bu, hizmet başlatma hatasına neden oldu.|Bu hata devam ederse Destek'e başvurun.|
   |46|Kaynak yetersizliği nedeniyle [%1] olay izleme oturumu kaydedilemedi ve başlatılamadı. Hata kodu: %2. Bunun nedeni büyük olasılıkla çok fazla etkin olay izleme oturumu olmasıdır. Hizmet 1 dakika içinde yeniden denenecek.|Kaynak eksikliği nedeniyle ETW oturumu oluşturulurken hizmet başlatma sırasında bir hata oluştu. Hizmet başlatıldı ve çalışıyor, ancak ETW oturumu başlatılana kadar hiçbir algılayıcı olayı bildirmez.|Normal çalışma bildirimi; eyleme gerek yoktur. Hizmet, oturumu dakikada bir başlatmayı dener.|
   |47|Olay izleme oturumu başarıyla kaydedildi ve başlatıldı - önceki başarısız denemelerden sonra kurtarıldı.|Bu olay, ETW oturumunu başarıyla başlattıktan sonra önceki olayı izler.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |48|[%2] olay izleme oturumuna [%1] sağlayıcı eklenemedi. Hata kodu: %3. Bu, bu sağlayıcıdan gelen olayların bildirilmeyeceğini gösterir.|ETW oturumuna sağlayıcı eklenemedi. Sonuç olarak sağlayıcı olayları bildirilir.|Hata kodunu denetleyin. Hata devam ederse Desteğe başvurun.|
   |49|Geçersiz bulut yapılandırma komutu alındı ve yoksayıldı. Sürüm: %1, durum: %2, hata kodu: %3, ileti: %4|Bulut hizmetinden yoksayılan geçersiz bir yapılandırma dosyası alındı.|Bu hata devam ederse Destek'e başvurun.|
   |50|Yeni bulut yapılandırması başarıyla uygulandı. Sürüm: %1.|Bulut hizmetinden yeni bir yapılandırma başarıyla uygulandı.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |51|Yeni bulut yapılandırması uygulanamadı, sürüm: %1. Bilinen son iyi yapılandırma olan %2 sürümü başarıyla uygulandı.|Bulut hizmetinden hatalı bir yapılandırma dosyası alındı. Bilinen son iyi yapılandırma başarıyla uygulandı.|Bu hata devam ederse Destek'e başvurun.|
   |52|Yeni bulut yapılandırması uygulanamadı, sürüm: %1. Ayrıca bilinen son iyi yapılandırma olan %2 sürümü uygulanamadı. Varsayılan yapılandırma başarıyla uygulandı.|Bulut hizmetinden hatalı bir yapılandırma dosyası alındı. Bilinen son iyi yapılandırma uygulanamadı ve varsayılan yapılandırma uygulandı.|Hizmet 5 dakika içinde yeni bir yapılandırma dosyası indirmeyi dener. Olay #50'i görmüyorsanız Destek'e başvurun.|
   |53|Kalıcı depolamadan yüklenen bulut yapılandırması, sürüm: %1.|Yapılandırma, hizmet başlangıcında kalıcı depolama alanından yüklendi.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |54| Genel (desen başına) durum değişti. Durum: %1, desen: %2 | Durum = 0: Siber veri raporlama kuralı tanımlı eşleme kotasına ulaştıysa ve sınırlama kotası dolana kadar daha fazla veri göndermez. Durum = 1: Eşleme kotasının süresi dolduysa ve kural veri göndermeye devam eder. | Normal çalışma bildirimi; eyleme gerek yoktur. |
   |55|Güvenli ETW otomatik günlükçü oluşturulamadı. Hata kodu: %1|Güvenli ETW günlükçü oluşturulamadı.|Cihazı yeniden başlatın. Bu hata devam ederse Destek'e başvurun.|
   |56|Güvenli ETW otomatik günlükçü kaldırılamadı. Hata kodu: %1|Çıkarmada güvenli ETW oturumu kaldırılamadı.|Desteğe başvurun.|
   |57|Sorun giderme amacıyla makinenin anlık görüntüsünü yakalama.|Adli tıp paketi olarak da bilinen bir araştırma paketi toplanıyor.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |59|Komut başlatılıyor: %1|Yanıt komutu yürütme başlatılıyor.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |60|%1 komutu çalıştırılamadı, hata: %2.|Yanıt komutu yürütülemedi.|Bu hata devam ederse Destek'e başvurun.|
   |61|Veri toplama komut parametreleri geçersiz: SasUri: %1, compressionLevel: %2.|Veri toplama komut bağımsız değişkenleri (geçersiz bağımsız değişkenler) okunamadı veya ayrıştırılamadı.|Bu hata devam ederse Destek'e başvurun.|
   |62|Bağlı Kullanıcı Deneyimleri ve Telemetri hizmeti başlatılamadı. Hata kodu: %1|Bağlı Kullanıcı Deneyimleri ve Telemetri (diagtrack) hizmeti başlatılamadı. Uç Nokta için Microsoft Defender olmayan telemetri bu makineden gönderilmez.|Olay günlüğünde daha fazla sorun giderme ipucu arayın: Microsoft-Windows-UniversalTelemetryClient/Operational.|
   |63|Dış hizmetin başlangıç türü güncelleştiriliyor. Ad: %1, gerçek başlangıç türü: %2, beklenen başlangıç türü: %3, çıkış kodu: %4|Dış hizmetin başlangıç türü güncelleştirildi.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |64|Dış hizmeti başlatma durduruldu. Ad: %1, çıkış kodu: %2|Dış hizmet başlatılıyor.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |65|Microsoft Güvenlik Olayları Bileşeni Mini Filtre sürücüsü yüklenemedi. Hata kodu: %1|MsSecFlt.sys dosya sistemi mini filtresi yüklenemedi.|Cihazı yeniden başlatın. Bu hata devam ederse Destek'e başvurun.|
   |66|İlke güncelleştirmesi: Gecikme modu - %1|C&C bağlantı sıklığı ilkesi güncelleştirildi.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |68|Hizmetin başlangıç türü beklenmeyen bir durumdur. Hizmet adı: %1, gerçek başlangıç türü: %2, beklenen başlangıç türü: %3|Beklenmeyen dış hizmet başlangıç türü.|Dış hizmet başlangıç türünü düzeltin.|
   |69|Hizmet durduruldu. Hizmet adı: %1|Dış hizmet durduruldu.|Dış hizmeti başlatın.|
   |70|İlke güncelleştirmesi: Örnek toplamaya izin ver - %1|Örnek toplama ilkesi güncelleştirildi.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |71|Komut çalıştırıldı: %1|Komut başarıyla yürütüldü.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |72|İlk tam makine profili raporu gönderilmeye çalışildi. Sonuç kodu: %1|Yalnızca bilgilendirme amaçlıdır.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |73|Platform için akıllı başlangıç: %1|Yalnızca bilgilendirme amaçlıdır.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |74|Kayıt defterindeki cihaz etiketi uzunluk sınırını aşıyor. Etiket adı: %2. Uzunluk sınırı: %1.|Cihaz etiketi uzunluk sınırını aşıyor.|Daha kısa bir cihaz etiketi kullanın.|
   |81|ETW autologger Uç Nokta için Microsoft Defender oluşturulamadı. Hata kodu: %1|ETW oturumu oluşturulamadı.|Cihazı yeniden başlatın. Bu hata devam ederse Destek'e başvurun.|
   |82|ETW otomatik günlükçü Uç Nokta için Microsoft Defender kaldırılamadı. Hata kodu: %1|ETW oturumu silinemedi.|Desteğe başvurun.|
   |84|Windows Defender Virüsten Koruma çalışma modunu ayarlayın. Pasif modu zorla: %1, sonuç kodu: %2.|Defender çalışma modunu (etkin veya pasif) ayarlayın.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |85|yürütülebilir Uç Nokta için Microsoft Defender tetiklemedi. Hata kodu: %1|Başrolde SenseIR yürütülebilir dosyası başarısız oldu.|Cihazı yeniden başlatın. Bu hata devam ederse Destek'e başvurun.|
   |86|Yeniden başlatma, başlatılması gereken dış hizmeti durdurdu. Ad: %1, çıkış kodu: %2|Dış hizmet yeniden başlatılıyor.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |87|Dış hizmet başlatılamıyor. Ad: %1|Dış hizmet başlatılamadı.|Desteğe başvurun.|
   |88|Dış hizmetin başlangıç türü yeniden güncelleştiriliyor. Ad: %1, gerçek başlangıç türü: %2, beklenen başlangıç türü: %3, çıkış kodu: %4|Dış hizmetin başlangıç türü güncelleştirildi.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |89|Dış hizmetin başlangıç türü güncelleştirilemiyor. Ad: %1, gerçek başlangıç türü: %2, beklenen başlangıç türü: %3|Dış hizmetin başlangıç türü güncelleştirilemiyor.|Desteğe başvurun.|
   |90|%1 coğrafi bölgesindeki bulut hizmetine bağlanmak için System Guard Çalışma Zamanı İzleyicisi yapılandırılamadı. Hata kodu: %2|System Guard Çalışma Zamanı İzleyicisi kanıtlama verilerini bulut hizmetine göndermez.|Yazmaç yolundaki izinleri denetleyin: "HKLM\Software\Microsoft\Windows\CurrentVersion\Sgrm". Herhangi bir sorun tespit edilmezse Destek'e başvurun.|
   |91|System Guard Çalışma Zamanı İzleyicisi coğrafi bölge bilgileri kaldırılamadı. Hata kodu: %1|System Guard Çalışma Zamanı İzleyicisi kanıtlama verilerini bulut hizmetine göndermez.|Yazmaç yolundaki izinleri denetleyin: "HKLM\Software\Microsoft\Windows\CurrentVersion\Sgrm". Herhangi bir sorun tespit edilmezse Destek'e başvurun.|
   |92|Veri kotası aşıldığından algılayıcı siber veri kotası göndermeyi durdurma. Kota süresi geçtikten sonra göndermeye devam eder. Durum Maskesi: %1|Azaltma sınırını aşıyor.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |93|Algılayıcı siber verilerini göndermeye devam etme. Durum Maskesi: %1|Siber veri göndermeye devam edin.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |94|Uç Nokta için Microsoft Defender yürütülebilir dosya başlatıldı|SenseCE yürütülebilir dosyası başlatıldı.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |95|Uç Nokta için Microsoft Defender yürütülebilir dosya sona erdi|SenseCE yürütülebilir dosyası sona erdi.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |96|Uç Nokta için Microsoft Defender Init aradı. Sonuç kodu: %2|SenseCE yürütülebilir dosyası MCE başlatmayı çağırdı.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |97|DLP senaryosu için Bulut'a bağlantı sorunları var|DLP sınıflandırma akışını etkileyen ağ bağlantısı sorunları vardır.|Ağ bağlantısını denetleyin.|
   |98|DLP senaryosu için Bulut bağlantısı geri yüklendi|Ağ bağlantısı geri yüklendi ve DLP sınıflandırma akışı devam edebilir.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |99|Sense, sunucuyla iletişim kurarken şu hatayla karşılaştı: (%1). Sonuç: (%2)|bir iletişim hatası oluştu.|Diğer ayrıntılar için olay günlüğünde aşağıdaki olayları denetleyin.|
   |100|Uç Nokta için Microsoft Defender yürütülebilir dosya başlatılamadı. Hata kodu: %1|SenseCE yürütülebilir dosyası başlatılamadı.|Cihazı yeniden başlatın. Bu hata devam ederse Destek'e başvurun.|
   |102|Uç Nokta için Microsoft Defender Ağ Algılama ve Yanıt yürütülebilir dosyası başlatıldı|SenseNdr yürütülebilir dosyası başlatıldı.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |103|Uç Nokta için Microsoft Defender Ağ Algılama ve Yanıt yürütülebilir dosyası sona erdi|SenseNdr yürütülebilir dosyası sona erdi.|Normal çalışma bildirimi; eyleme gerek yoktur.|
   |

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-eventerrorcodes-belowfoldlink)

## <a name="see-also"></a>Ayrıca bkz.
- [Windows 10 cihazları ekleme](configure-endpoints.md)
- [Cihaz ara sunucusu ve İnternet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md)
- [sorun giderme Uç Nokta için Microsoft Defender](troubleshoot-onboarding.md)
- [İstemci çözümleyicisine genel bakış](overview-client-analyzer.md)
- [İstemci çözümleyicisini indirin ve çalıştırın](download-client-analyzer.md)
- [Çözümleyici HTML raporunu inceleyin](analyzer-report.md)
