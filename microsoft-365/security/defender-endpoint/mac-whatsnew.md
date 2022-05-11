---
title: Mac'te Uç Nokta için Microsoft Defender'deki yenilikler
description: Mac'te önceki Uç Nokta için Microsoft Defender sürümlerindeki önemli değişiklikler hakkında bilgi edinin.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, installation, macos, whatsnew
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: ec545bb38456b778b627c41994a1eb18ae665a86
ms.sourcegitcommit: 2d870e06e87b10d9e8ec7a7a8381353bc3bc59c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65349754"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-mac"></a>Mac'te Uç Nokta için Microsoft Defender'deki yenilikler

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="1016654-20122041166540"></a>101.66.54 (20.122041.16654.0)

- Bazı durumlarda doğru işlem yolunun yazdırılmaması sorunu `mdatp diagnostic real-time-protection-statistics` giderildi.
- Hata düzeltmeleri

## <a name="1016415-20122032164150"></a>101.64.15 (20.122032.16415.0)

- Sürüm 101.61.69'da ortaya çıkan ve son kullanıcıdan hiçbir eylem gerekmese de durum menüsü simgesinin bazen hata simgesi gösterdiği bir regresyon düzeltildi
- `conflicting_applications` içindeki alanı `mdatp health` yalnızca en son 10 işlemi gösterecek şekilde ve işlem adlarını içerecek şekilde geliştirildi. Bu, Mac için Uç Nokta için Microsoft Defender hangi işlemlerin çakışıyor olduğunu belirlemeyi kolaylaştırır.
- Satıcı kimliği ve ürün kimliğinin onaltılık yerine ondalık olarak görüntülendiği bir hata `mdatp device-control removable-media policy list` düzeltildi
- Performans iyileştirmeleri & diğer hata düzeltmeleri

## <a name="1016169-20122022161690"></a>101.61.69 (20.122022.16169.0)

- Hata düzeltmeleri

## <a name="1016091-20122021160910"></a>101.60.91 (20.122021.16091.0)

- Bu sürüm [CVE-2022-23278](https://msrc-blog.microsoft.com/2022/03/08/guidance-for-cve-2022-23278-spoofing-in-microsoft-defender-for-endpoint/) için bir güvenlik güncelleştirmesi içerir

## <a name="1015950-20122021159500"></a>101.59.50 (20.122021.15950.0)

- Bu sürüm, macOS 12.3 için destek ekler. apple, macOS 12.3'den başlayarak [Python 2.7'yi kaldırıyor](https://developer.apple.com/documentation/macos-release-notes/macos-12_3-release-notes). Varsayılan olarak macOS önceden yüklenmiş python sürümü yoktur. **EYLEM GEREKLI**: 
  - Kullanıcıların cihazlarını Monterey 12.3 (veya daha yeni) macOS güncelleştirmeden önce Mac için Uç Nokta için Microsoft Defender 101.59.50 (veya daha yeni) sürümüne güncelleştirmeleri gerekir. Bu en düşük sürüm 101.59.50, macOS Monterey'de Mac için Uç Nokta için Microsoft Defender ile ilgili Python ile ilgili sorunları ortadan kaldırmanın önkoşuludur.
  - Uzak dağıtımlar için, mevcut MDM kurulumları Mac için Uç Nokta için Microsoft Defender sürüm 101.59.50 (veya daha yeni) olarak güncelleştirilmelidir. MDM aracılığıyla Mac için eski bir Uç Nokta için Microsoft Defender sürümünün Monterey 12.3 (veya daha yeni) macOS gönderilmesi yükleme hatasına neden olur.

## <a name="1015910-20122012159100"></a>101.59.10 (20.122012.15910.0)

- Komut satırı aracı artık karantinaya alınan dosyaların dosyanın ilk algılandığı konumdan farklı bir konuma geri yüklenmesini destekliyor. Bu işlem aracılığıyla `mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`yapılabilir.
- Thunderbolt 3 üzerinden bağlanan cihazları işlemek için genişletilmiş cihaz denetimi
- Geçersiz satıcı kimlikleri ve ürün kimlikleri içeren cihaz denetimi ilkelerinin işlenmesi geliştirildi. Bu sürümden önce, ilke bir veya daha fazla geçersiz kimlik içeriyorsa ilkenin tamamı yoksayılırdı. Bu sürümden başlayarak, ilkenin yalnızca geçersiz bölümleri yoksayılır. İlkeyle ilgili sorunlar aracılığıyla `mdatp device-control removable-media policy list`ortaya konur.
- Hata düzeltmeleri

## <a name="1015662-20121122156620"></a>101.56.62 (20.121122.15662.0)

- Hata düzeltmeleri

## <a name="1015635-20121121156350"></a>101.56.35 (20.121121.15635.0)

- Uygulama "Microsoft Defender ATP" olarak "Microsoft Defender" olarak yeniden adlandırıldı. Son kullanıcılar aşağıdaki değişiklikleri gözlemler:
  - Uygulama yükleme yolu olarak değiştirildi `/Application/Microsoft Defender ATP.app` `/Applications/Microsoft Defender.app`.
  - Kullanıcı deneyiminde " Microsoft Defender ATP" oluşumları "Microsoft Defender" ile değiştirilmiştir
- Mac için Uç Nokta için Microsoft Defender ile dağıtılan ağ içerik filtresi nedeniyle bazı VPN uygulamalarının bağlanamadığı bir sorun çözüldü
- macOS 12.2 beta 2 sürümünde bulunan ve işletim sistemindeki (işletim sistemi) belirli özelliklere sahip paketlerin yüklenmesini engelleyen bir değişiklik nedeniyle yükleme paketinin açılamadığı bir sorun giderildi. Bu işletim sistemi değişikliğinin macOS 12.2'nin son sürümünde yer almadığı görünse de, gelecekteki bir macOS sürümünde yeniden kullanıma sunulacaktır. Bu nedenle, tüm kuruluş yöneticilerinin yönetim konsolundaki Uç Nokta için Microsoft Defender paketini bu ürün sürümüne (veya daha yeni bir sürüme) yenilemelerini öneririz.
- Bazı M1 cihazlarında görülen ve ürünün geçersiz kötü amaçlı yazılımdan koruma tanımlarıyla takıldığı ve çalışan bir tanım kümesine başarıyla güncelleştirilemediği bir sorun giderildi.
- `mdatp health`çıktısı, Mac için Uç Nokta için Microsoft Defender tüm bileşenlerine Tam Disk Erişimi verilip verilmediğini belirlemek için kullanılabilecek adlı `full_disk_access_enabled` ek bir öznitelikle genişletilmiştir.
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1015416-20121111154160"></a>101.54.16 (20.121111.15416.0)

- macOS 10.14 (Mojave) artık desteklenmiyor
- Bir ürün ayarı MDM aracılığıyla yönetici tarafından yönetilmeyi durdurduktan sonra, yönetilmeden önce sahip olduğu değere geri döner (son kullanıcı tarafından yerel olarak yapılandırılan değer veya böyle bir yerel değer açıkça sağlanmazsa, ürün tarafından kullanılan varsayılan değer). Bu değişiklikten önce, bir ayar yönetilmeyi durdurduktan sonra yönetilen değeri kalıcı hale gelip ürün tarafından kullanılmaya devam etti.
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1014925-20121092149250"></a>101.49.25 (20.121092.14925.0)

- İsteğe bağlı taramalar sırasında arşivlerin taranıp taranmayacağını denetlemek için komut satırı aracına yeni bir anahtar eklendi. Bu, aracılığıyla `mdatp config scan-archives --value [enabled/disabled]`yapılandırılabilir. Bu, varsayılan olarak olarak `enabled`ayarlanır.
- Hata düzeltmeleri

## <a name="1014727-20121082147270"></a>101.47.27 (20.121082.14727.0)

- macOS Mojave ve macOS Catalina'da kapatma sırasında oluşan sistem donması için düzeltme

## <a name="1014384-20121082143840"></a>101.43.84 (20.121082.14384.0)

- macOS 12 (Monterey) için aday derlemesi
- Hata düzeltmeleri

## <a name="1014110-20121072141100"></a>101.41.10 (20.121072.14110.0)

- Komut satırı aracına yeni anahtarlar eklendi:
  - İsteğe bağlı taramalar için paralellik derecesini denetleme. Bu, aracılığıyla `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]`yapılandırılabilir. Varsayılan olarak, bir paralellik `2` derecesi kullanılır.
  - Güvenlik bilgileri güncelleştirmelerinin etkinleştirilip etkinleştirilmediğini veya devre dışı bırakılıp bırakılmayacağını denetleyin. Bu, aracılığıyla `mdatp config scan-after-definition-update --value [enabled/disabled]`yapılandırılabilir. Bu, varsayılan olarak olarak `enabled`ayarlanır.
- Ürün günlüğü düzeyini değiştirmek için artık yükseltme gerekiyor
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1014084-20121071140840"></a>101.40.84 (20.121071.14084.0)

- M1 yonga yerel desteği
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1013797-20121062137970"></a>101.37.97 (20.121062.13797.0)

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1013428-20121061134280"></a>101.34.28 (20.121061.13428.0)

- Hata düzeltmeleri

## <a name="1013427-20121052134270"></a>101.34.27 (20.121052.13427.0)

- Hata düzeltmeleri

## <a name="1013420-20121051134200"></a>101.34.20 (20.121051.13420.0)

- [macOS için cihaz denetimi](mac-device-control-overview.md) artık genel kullanıma hazır
- macOS 11(Big Sur) üzerindeki durum menüsünden hızlı taramanın başlatılamadığı bir sorun giderildi
- Diğer hata düzeltmeleri

## <a name="1013269-20121042132690"></a>101.32.69 (20.121042.13269.0)

- Uç Nokta için Microsoft Defender ve diğer uygulamalardan anahtarlığa eşzamanlı erişimin anahtar zinciri bozulmasına yol açması sorunu giderildi.

## <a name="1012964-20121042129640"></a>101.29.64 (20.121042.12964.0)

- Bu sürümden başlayarak, komut satırı istemcisi aracılığıyla tetiklenen isteğe bağlı virüsten koruma taramaları sırasında algılanan tehditler otomatik olarak düzeltilir. Kullanıcı arabirimi aracılığıyla tetiklenen taramalar sırasında algılanan tehditler yine de el ile eylem gerektirir.
- `mdatp diagnostic real-time-protection-statistics` şimdi iki ek anahtarı destekler:
  - `--sort`: Taranan toplam dosya sayısına göre azalan çıktıyı sıralar
  - `--top N`: en iyi N sonuçlarını görüntüler (yalnızca belirtilirse `--sort` çalışır)
- Performans iyileştirmeleri (özellikle YARN kullanıldığında) & hata düzeltmeleri

## <a name="1012750-20121022127500"></a>101.27.50 (20.121022.12750.0)

- macOS Catalina ve önceki sürümlerde Apple sertifika süre sonu için uyum sağlama düzeltmesi. Bu düzeltme, Tehdit & Güvenlik Açığı Yönetimi (TVM) işlevselliğini geri yükler.

## <a name="1012569-20121022125690"></a>101.25.69 (20.121022.12569.0)

- macOS'daki Uç Nokta için Microsoft Defender artık ABD Kamu müşterileri için önizleme aşamasında kullanıma sunulmuştur. Daha fazla bilgi için bkz. [US Government müşterileri için Uç Nokta için Microsoft Defender](gov.md).
- Performans iyileştirmeleri (özellikle XCode Simülatörü uygulamasının kullanıldığı durum için) hata düzeltmeleri &.

## <a name="1012364-20121021123640"></a>101.23.64 (20.121021.12364.0)

- Son isteğe bağlı tarama hakkındaki bilgileri görüntülemek için komut satırı aracına yeni bir seçenek eklendi. Son isteğe bağlı tarama hakkındaki bilgileri görüntülemek için `mdatp health --details antivirus`
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1012279-20121012122790"></a>101.22.79 (20.121012.12279.0)

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1011988-20121011119880"></a>101.19.88 (20.121011.11988.0)

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1011948-20120121119480"></a>101.19.48 (20.120121.11948.0)

> [!NOTE]
> Eski komut satırı aracının söz dizimi bu sürümle kullanım dışı bırakıldı. Yeni söz dizimi hakkında bilgi için bkz [. Kaynaklar](mac-resources.md#configuring-from-the-command-line).

- Ağ uzantısını devre dışı bırakmak için yeni bir komut satırı anahtarı eklendi: `mdatp system-extension network-filter disable`. Bu komut, Mac'te Uç Nokta için Microsoft Defender ile ilgili olabilecek ağ sorunlarını gidermek için yararlı olabilir
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1011921-20120101119210"></a>101.19.21 (20.120101.11921.0)

- Hata düzeltmeleri

## <a name="1011526-20120102115260"></a>101.15.26 (20.120102.11526.0)

- macOS 11 Big Sur'da çalışırken aracının güvenilirliği iyileştirildi
- Özel taramalar sırasında AV dışlamalarını yoksaymak için yeni bir komut satırı anahtarı`--ignore-exclusions` () eklendi (`mdatp scan custom`)
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1011375-20120101113750"></a>101.13.75 (20.120101.11375.0)

- Uç Nokta için Microsoft Defender çekirdek paniğine dönüşen bir macOS 11 (Big Sur) hatasını tetiklediğinde koşullar kaldırıldı
- mac 11 (Big Sur) üzerinde çalışırken Endpoint Security sistem uzantısındaki bellek sızıntısı düzeltildi
- Hata düzeltmeleri

## <a name="1011072"></a>101.10.72

- Hata düzeltmeleri

## <a name="1010961"></a>101.09.61

- [Geri bildirim gönderme seçeneğini devre dışı bırakmak](mac-preferences.md#show--hide-option-to-send-feedback) için yeni bir yönetilen tercih eklendi
- Durum menüsü simgesi artık ürün ayarları yönetildiğinde iyi durumda bir durum gösteriyor. Daha önce, ürün ayarları yönetici tarafından yönetilse bile durum menüsü simgesi bir uyarı veya hata durumu görüntülüyordu
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1010950"></a>101.09.50

- Bu ürün sürümü macOS Big Sur 11 beta 9'da doğrulanmıştır

- Komut satırı aracının `mdatp` yeni söz dizimi artık varsayılan söz dizimidir. Yeni söz dizimi hakkında daha fazla bilgi için bkz[. macOS'de Uç Nokta için Microsoft Defender kaynakları](mac-resources.md#configuring-from-the-command-line)

  > [!NOTE]
  > Eski komut satırı aracının söz dizimi **1 Ocak 2021'de** üründen kaldırılacaktır.

- Tanılama günlüklerinin farklı bir dizine kaydedilmesini sağlayan yeni bir parametre (`--path [directory]`) ile genişletilmiş `mdatp diagnostic create`
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1010949"></a>101.09.49

- BT yöneticisi tarafından yönetilen dışlamaları ve yerel kullanıcı tarafından tanımlanan dışlamaları ayırt etmek için kullanıcı arabirimi geliştirmeleri
- İsteğe bağlı taramalar sırasında geliştirilmiş CPU kullanımı
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1010723"></a>101.07.23

- Pasif modun durumunu ve EDR grup kimliğini denetlemek için çıkışına `mdatp --health` yeni alanlar eklendi

  > [!NOTE]
  > `mdatp --health` , gelecekteki bir ürün güncelleştirmesinde ile `mdatp health` değiştirilecektir.

- Otomatik örnek gönderiminin kullanıcı arabiriminde yönetilen olarak işaretlenmediği bir hata düzeltildi
- Virüsten koruma tarama geçmişindeki öğelerin saklamasını denetlemek için yeni ayarlar eklendi. Artık [tarama geçmişindeki öğelerin tutulacak gün sayısını belirtebilir ve tarama geçmişindeki](mac-preferences.md#antivirus-scan-history-retention-in-days) [en fazla öğe sayısını belirtebilirsiniz](mac-preferences.md#maximum-number-of-items-in-the-antivirus-scan-history)
- Hata düzeltmeleri

## <a name="1010663"></a>101.06.63

- sürümünde `101.05.17`ortaya çıkan performans regresyonu giderildi. Regresyon, bazı müşterilerin SMB paylaşımlarına erişirken gözlemlediği çekirdek paniğinin ortadan kaldırılmasına yönelik düzeltme ile sunulmuştur. Bu kod değişikliğini geri aldık ve çekirdek paniğini ortadan kaldırmak için alternatif yollar araştırıyoruz.

## <a name="1010517"></a>101.05.17

> [!IMPORTANT]
> Komut satırı aracı için `mdatp` yeni ve gelişmiş bir söz dizimi üzerinde çalışıyoruz. Yeni söz dizimi şu anda Insider Hızlı ve Insider Yavaş güncelleştirme kanallarında varsayılandır. Bu yeni söz dizimi ile kendinizi özetlemenizi öneririz.
>
> Eski söz dizimini yeni söz dizimiyle paralel olarak desteklemeye devam edeceğiz ve önümüzdeki aylarda eski söz dizimi için kullanımdan kaldırma planıyla ilgili daha fazla iletişim sağlayacağız.

- SMB dosya paylaşımlarına erişilirken oluşan çekirdek paniği giderildi
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1010516"></a>101.05.16

- Taranan dosyaların sayısını önemli ölçüde azaltmak için hızlı tarama mantığını geliştirmeler
- Komut satırı aracı için [otomatik tamamlama desteği](mac-resources.md#how-to-enable-autocompletion) eklendi
- Hata düzeltmeleri

## <a name="1010312"></a>101.03.12

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1010154"></a>101.01.54

- Time Machine ile uyumlulukla ilgili iyileştirmeler
- Erişilebilirlik geliştirmeleri
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1010031"></a>101.00.31

- [Intune kullanıcıları için geliştirilmiş ürün ekleme deneyimi](/mem/intune/apps/apps-advanced-threat-protection-macos)
- Virüsten [koruma dışlamaları artık joker karakterleri destekliyor](mac-exclusions.md#supported-exclusion-types)
- macOS bağlam menüsünden virüsten koruma taramalarını tetikleme özelliği eklendi. Artık Bulucu'da bir dosyaya veya klasöre sağ tıklayabilir ve **Uç Nokta için Microsoft Defender ile tara'yı** seçebilirsiniz
- Yerinde ürün düşürme işlemlerine artık yükleyici tarafından açıkça izin verilmiyor. Eski sürüme düşürmeniz gerekiyorsa, önce mevcut sürümü kaldırın ve cihazınızı yeniden yapılandırın
- Hata düzeltmeleri & diğer performans iyileştirmeleri

## <a name="1009027"></a>100.90.27

- Artık sistem [genelindeki güncelleştirme kanalından farklı macOS](mac-updates.md#set-the-channel-name) Uç Nokta için Microsoft Defender için bir güncelleştirme kanalı ayarlayabilirsiniz
- Yeni ürün simgesi
- Diğer kullanıcı deneyimi geliştirmeleri
- Hata düzeltmeleri

## <a name="1008692"></a>100.86.92

- Time Machine ile uyumlulukla ilgili iyileştirmeler
- Ürünün bazen kaldırma sırasında altındaki tüm dosyaları `/Library/Application Support/Microsoft/Defender` temizlememesi sorunu giderildi
- Microsoft ürünleri Microsoft AutoUpdate aracılığıyla güncelleştirildiğinde ürünün CPU kullanımı azaltıldı
- Hata düzeltmeleri & diğer performans iyileştirmeleri

## <a name="1008691"></a>100.86.91

> [!CAUTION]
> macOS cihazlarınız için en eksiksiz korumayı sağlamak ve Apple'ın macOS yerel güvenlik güncelleştirmelerinin [current - 2] sürümünden eski işletim sistemi sürümlerine teslimini durdurmasıyla uyumlu olması için Mac için MDATP dağıtımı ve güncelleştirmeleri artık macOS Sierra [10.12] tarihinde desteklenmeyecektir. Mac için MDATP güncelleştirmeleri ve geliştirmeleri Catalina [10.15], Mojave [10.14] ve High Sierra [10.13] sürümlerini çalıştıran cihazlara sunulacaktır.
>
> Sierra [10.12] cihazlarınıza zaten Mac için MDATP dağıttıysanız, korumayı kaybetme risklerini ortadan kaldırmak için lütfen en son macOS sürümüne yükseltin.

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1008373"></a>100.83.73

- BT yöneticileri için [dışlama](mac-preferences.md#exclusion-merge-policy) yönetimi, [tehdit türü ayarlarının yönetimi](mac-preferences.md#threat-type-settings-merge-policy) ve [izin verilmeyen tehdit eylemleri](mac-preferences.md#disallowed-threat-actions) hakkında daha fazla denetim eklendi
- Cihazda Tam Disk Erişimi etkinleştirilmediğinde, artık durum menüsünde bir uyarı görüntülenir
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1008260"></a>100.82.60

- Ürünün bir tanım güncelleştirmesini takip etmeye başlayamaması sorunu giderildi.

## <a name="1008042"></a>100.80.42

- Hata düzeltmeleri

## <a name="1007942"></a>100.79.42

- Mac'te Uç Nokta için Microsoft Defender zaman zaman Time Machine'i engellemesi sorunu düzeltildi
- Arka uç hizmetiyle bağlantıyı test etmek için komut satırı yardımcı programı için yeni bir anahtar eklendi

  ```bash
  mdatp connectivity test
  ```

- Kullanıcı arabiriminde tehdit geçmişinin tamamını görüntüleme özelliği eklendi ( **Koruma geçmişi** görünümünden erişilebilir)
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1007215"></a>100.72.15

- Hata düzeltmeleri

## <a name="1007099"></a>100.70.99

- Gerçek zamanlı koruma etkinleştirildiğinde bazı kullanıcıların macOS Catalina'ya yükseltme yeteneğini etkileyen bir sorun giderildi. Bu düzensiz sorun, catalina yükseltme paketindeki dosyaları tehditlere karşı tararken Uç Nokta için Microsoft Defender kilitlemeden kaynaklandı ve bu da yükseltme sırasında hatalara yol açtı.

## <a name="1006899"></a>100.68.99

- Virüsten koruma işlevini [pasif modda](mac-preferences.md#enforcement-level-for-antivirus-engine) çalışacak şekilde yapılandırma özelliği eklendi
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1006528"></a>100.65.28

- macOS Catalina desteği eklendi

  > [!CAUTION]
  > macOS 10.15 (Catalina) yeni güvenlik ve gizlilik geliştirmeleri içerir. Bu sürümden başlayarak, uygulamalar varsayılan olarak açık onay olmadan disk üzerindeki belirli konumlara (Belgeler, İndirmeler, Masaüstü vb.) erişemez. Bu onay olmadığında, Uç Nokta için Microsoft Defender cihazınızı tam olarak koruyamaz.
  >
  > Bu onayı verme mekanizması, Uç Nokta için Microsoft Defender nasıl dağıtdığınıza bağlıdır:
  >
  > - El ile dağıtımlar için [El ile dağıtım](mac-install-manually.md#how-to-allow-full-disk-access) konusunda güncelleştirilmiş yönergelere bakın.
  > - Yönetilen dağıtımlar için [JAMF tabanlı dağıtım](mac-install-with-jamf.md) ve [Microsoft Intune tabanlı dağıtım](mac-install-with-intune.md#create-system-configuration-profiles) konularındaki güncelleştirilmiş yönergelere bakın.

- Performans iyileştirmeleri & hata düzeltmeleri
