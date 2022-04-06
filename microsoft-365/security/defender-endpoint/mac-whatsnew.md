---
title: Mac'te Uç Nokta için Microsoft Defender'
description: Mac'te yeni sürümün önceki sürümlerine Uç Nokta için Microsoft Defender hakkında bilgi edinin.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, yükleme, macos, whatsnew
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
ms.openlocfilehash: d8b2c7725354facb01f8b12af502aae19856afe8
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500749"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-mac"></a>Mac'te Uç Nokta için Microsoft Defender'

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="1016169-20122022161690"></a>101.61.69 (20.122022.16169.0)

- Hata düzeltmeleri

## <a name="1016091-20122021160910"></a>101.60.91 (20.122021.16091.0)

- Bu sürüm, [PIE-2022-23278 için bir güvenlik güncelleştirmesi içerir](https://msrc-blog.microsoft.com/2022/03/08/guidance-for-cve-2022-23278-spoofing-in-microsoft-defender-for-endpoint/)

## <a name="1015950-20122021159500"></a>101.59.50 (20.122021.15950.0)

- Bu sürüm macOS 12.3 için destek ekler. MacOS 12.3'den başlayarak, [Apple Python 2.7'yi kaldırmıştı](https://developer.apple.com/documentation/macos-release-notes/macos-12_3-release-notes). MacOS üzerinde önceden yüklenmiş hiçbir Python sürümü varsayılan olarak olmayacaktır. **EYLEM GEREKIYOR**: 
  - Kullanıcıların cihazlarını macOS Monterey 12.3 (veya daha yeni) sürümüne güncelleştirmeden önce Mac için Uç Nokta için Microsoft Defender sürümünü 101.59.50 (veya daha yeni) sürümüne güncelleştirmeleri gerekir. Bu en düşük sürüm 101.59.50, macOS Monterey üzerinde Mac için Uç Nokta için Microsoft Defender Python ile ilgili sorunları ortadan kaldırmanın önkoşullarıdır.
  - Uzak dağıtımlarda, var olan MDM kurulumların Mac için Uç Nokta için Microsoft Defender 101.59.50 (veya daha yeni) olarak güncelleştirilmiş olması gerekir. Mac için MDM'den daha eski bir Uç Nokta için Microsoft Defender macOS Monterey 12.3'e (veya daha yeni bir sürümü) itmek yükleme hatasına neden olur.

## <a name="1015910-20122012159100"></a>101.59.10 (20.122012.15910.0)

- Komut satırı aracı artık karantinaya alınmış dosyaları, dosyanın başlangıçta algılandığından farklı bir konuma geri yüklemeyi destekler. Bu, aracılığıyla yapılabilir `mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`.
- Zaman 3 üzerinden bağlanan cihazları işlemek için genişletilmiş cihaz denetimi
- Geçersiz satıcı kimlikleri ve ürün kimlikleri içeren cihaz denetimi ilkelerinin işlenmesi geliştirildi. Bu sürümden önce, ilke bir veya birden çok geçersiz kimlik içeriyorsa, ilkenin tamamı yok sayılırdı. Bu sürümden başlayarak, ilkenin yalnızca geçersiz bölümleri yok sayılır. İlkeyle ilgili sorunlar ile ilgili sorunlar ortaya çıkar `mdatp device-control removable-media policy list`.
- Hata düzeltmeleri

## <a name="1015662-20121122156620"></a>101.56.62 (20.121122.15662.0)

- Hata düzeltmeleri

## <a name="1015635-20121121156350"></a>101.56.35 (20.121121.15635.0)

- Uygulama", "Microsoft Defender ATP" olan "Microsoft Defender" olarak yeniden adlandırılmıştır. Son kullanıcılar aşağıdaki değişiklikleri gözlemler:
  - Uygulama yükleme yolu olarak değiştirildi `/Application/Microsoft Defender ATP.app` `/Applications/Microsoft Defender.app`.
  - Kullanıcı deneyimi içinde, "Microsoft Defender ATP" tekrarları "Microsoft Defender" ile değiştirilmiştir
- Mac için UÇ NOKTA IÇIN MICROSOFT DEFENDER ile dağıtılan ağ içerik filtresi nedeniyle bazı VPN uygulamalarının bağlanamama sorunu çözüldü
- Belirli özelliklere sahip paketlerin yüklenmesine engel olan işletim sisteminde (OS) yapılan bir değişiklik nedeniyle, yükleme paketinin açılamadı olduğu macOS 12.2 beta 2'de bulunan bir sorun giderildi. Bu işletim sistemi değişikliğinin macOS 12.2'nin son sürümüne dahil olmadığını görünür ama gelecekteki bir macOS sürümünde yeniden aşınacak olması olasıdır. Bu nedenle tüm kuruluş yöneticilerinin, yönetim konsolunda yer alan Uç Nokta için Microsoft Defender paketini bu ürün sürümüne (veya daha yeni bir sürüme) yenilemelerini teşvik etmek için tüm kuruluş yöneticilerini cesaretlendirin.
- Bazı M1 cihazlarda, ürünün geçersiz kötü amaçlı yazılımdan koruma tanımları ile takılıp kalmış ve çalışan bir tanım kümesine başarıyla güncelleştirilememe sorunu giderildi.
- `mdatp health`çıkış, `full_disk_access_enabled` Mac için Office 365'in tüm bileşenlerine Tam Disk Erişimi'nin verili olup olmadığını belirlemek için kullanılmaktadır adlı ek Uç Nokta için Microsoft Defender genişletildi.
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1015416-20121111154160"></a>101.54.16 (20.121111.15416.0)

- macOS 10.14 (Mojave) artık desteklenmiyor
- Ürün ayarı yönetici tarafından MDM aracılığıyla yönetildikten sonra, artık önceki değerine geri döner (son kullanıcı tarafından yerel olarak yapılandırılan değer veya bu tür bir yerel değer açık olarak sağ yüklenmezse, ürün tarafından kullanılan varsayılan değer). Bu değişiklikten önce, bir ayar yönetildikten sonra yönetilen değeri kalıcı olarak ürün tarafından kullanılmaya devam ediyordu.
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1014925-20121092149250"></a>101.49.25 (20.121092.14925.0)

- isteğe bağlı taramalar sırasında arşivlerin taranıp taranmamasını kontrol etmek için komut satırı aracına yeni bir anahtar eklendi. Bu, aracılığıyla yalnarak yalnarak yalndırıldı `mdatp config scan-archives --value [enabled/disabled]`. Varsayılan olarak, bu ayar olarak ayarlanır `enabled`.
- Hata düzeltmeleri

## <a name="1014727-20121082147270"></a>101.47.27 (20.121082.14727.0)

- macOS Mojave ve macOS Catalina'da sistem donması nedeniyle oluşan donma sorunu için düzeltme

## <a name="1014384-20121082143840"></a>101.43.84 (20.121082.14384.0)

- macOS 12 (Monterey) için aday derleme
- Hata düzeltmeleri

## <a name="1014110-20121072141100"></a>101.41.10 (20.121072.14110.0)

- Komut satırı aracına yeni anahtarlar eklendi:
  - Isteğe bağlı taramalar için paralellik derecesini kontrol altında bulundur. Bu, aracılığıyla yalnarak yalnarak yalndırıldı `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]`. Varsayılan olarak, paralellik derecesi `2` kullanılır.
  - Güvenlik zekası güncelleştirmeleri etkinleştirildikten veya devre dışı bırakıldıktan sonra taramaları denetleme. Bu, aracılığıyla yalnarak yalnarak yalndırıldı `mdatp config scan-after-definition-update --value [enabled/disabled]`. Varsayılan olarak, bu ayar olarak ayarlanır `enabled`.
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

- [macOS için cihaz denetimi](mac-device-control-overview.md) artık genel kullanılabilirlik durumuna geldi
- macOS 11'de (Big Sur) durum menüsünden hızlı taramanın başlatılamama sorunu giderildi
- Diğer hata düzeltmeleri

## <a name="1013269-20121042132690"></a>101.32.69 (20.121042.13269.0)

- Birden fazla uygulama veya diğer uygulamalardan anahtarlıklara eşzamanlı Uç Nokta için Microsoft Defender anahtarlık bozulmalarına yol aç aça bir soruna ilişkin bir sorun giderildi.

## <a name="1012964-20121042129640"></a>101.29.64 (20.121042.12964.0)

- Bu sürümden başlayarak, komut satırı istemcisi aracılığıyla tetiklenen isteğe bağlı virüsten koruma taramaları sırasında algılanan tehditler otomatik olarak düzeltilir. Kullanıcı arabirimi tarafından tetiklenen taramalar sırasında algılanan tehditlere yine el ile eylem gerekir.
- `mdatp diagnostic real-time-protection-statistics` şimdi iki ek anahtarı desteklemelidir:
  - `--sort`: çıktıyı taranan toplam dosya sayısına göre azalan düzende sıralar
  - `--top N`: en yüksek N sonuçlarını görüntüler (yalnızca belirtilen sonuçlar `--sort` için işe yarar)
- Performans iyileştirmeleri (özellikle DEYİCİ'nin ne zaman kullanılır) & düzeltmelerini içerir

## <a name="1012750-20121022127500"></a>101.27.50 (20.121022.12750.0)

- MacOS Catalina ve önceki sürümleri için Apple sertifikasının süre sonu için düzeltme. Bu düzeltme Tehdit & Güvenlik Açığı Yönetimi (TVM) işlevini geriler.

## <a name="1012569-20121022125690"></a>101.25.69 (20.121022.12569.0)

- Uç Nokta için Microsoft Defender macOS'ta bulunan müşteriler için önizleme, artık ABD Kamu müşterileri için önizleme olarak sunulmaktadır. Daha fazla bilgi için abd [Uç Nokta için Microsoft Defender için bkz.](gov.md)
- Performans iyileştirmeleri (özel olarak XCode KodKodu uygulamasının kullanıldı olduğu durum için) ve & düzeltmeler.

## <a name="1012364-20121021123640"></a>101.23.64 (20.121021.12364.0)

- Son isteğe bağlı tarama hakkında bilgileri görüntülemek için komut satırı aracına yeni bir seçenek eklendi. Son isteğe bağlı tarama hakkında bilgi görüntülemek için `mdatp health --details antivirus`
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1012279-20121012122790"></a>101.22.79 (20.121012.12279.0)

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1011988-20121011119880"></a>101.19.88 (20.121011.11988.0)

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1011948-20120121119480"></a>101.19.48 (20.120121.11948.0)

> [!NOTE]
> Eski komut satırı aracının söz dizimi bu sürümde kullanım dışı bırakıldı. Yeni söz dizimi hakkında bilgi için bkz. [Kaynaklar](mac-resources.md#configuring-from-the-command-line).

- Ağ uzantısını devre dışı bırakmak için yeni bir komut satırı anahtarı eklendi: `mdatp system-extension network-filter disable`. Bu komut, Mac'te dosyalarla ilgili ağ sorunlarını gidermek Uç Nokta için Microsoft Defender olabilir
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1011921-20120101119210"></a>101.19.21 (20.120101.11921.0)

- Hata düzeltmeleri

## <a name="1011526-20120102115260"></a>101.15.26 (20.120102.11526.0)

- macOS 11 Big Sur'da çalışan aracının güvenilirliği geliştirildi
- Özel taramalar () sırasında AV dışlamalarını`--ignore-exclusions` yoksaymak için yeni bir komut satırı anahtarı (`mdatp scan custom`) eklendi
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1011375-20120101113750"></a>101.13.75 (20.120101.11375.0)

- Bir macOS 11 Uç Nokta için Microsoft Defender (Big Sur) hatası tetiklendiğinde ve çekirdekte paniğe neden olan koşullar kaldırıldı
- Mac 11'de (Big Sur) çalıştırılan Endpoint Security sistem uzantısında bellek sızıntısı düzeltildi
- Hata düzeltmeleri

## <a name="1011072"></a>101.10.72

- Hata düzeltmeleri

## <a name="1010961"></a>101.09.61

- Geri bildirim gönderme seçeneğini devre dışı [bırakmak için yeni bir yönetilen tercih eklendi](mac-preferences.md#show--hide-option-to-send-feedback)
- Durum menüsü simgesi artık ürün ayarları yönetilsinken iyi durumda olduğunu gösteriyor. Daha önce, ürün ayarları yönetici tarafından yönetilse bile durum menüsü simgesi bir uyarı veya hata durumu görüntüleniyor.
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1010950"></a>101.09.50

- Bu ürün sürümü macOS Big Sur 11 beta 9 üzerinde doğrulandı

- Komut satırı aracının yeni `mdatp` söz dizimi artık varsayılan araçtır. Yeni söz dizimi hakkında daha fazla bilgi için bkz. [macOS'ta Uç Nokta için Microsoft Defender kaynakları](mac-resources.md#configuring-from-the-command-line)

  > [!NOTE]
  > Eski komut satırı aracının söz dizimi **1 Ocak 2021'de üründen kaldırılacaktır**.

- Tanılama günlüklerinin `mdatp diagnostic create` farklı bir dizine kaydedilmiş olarak tutulmasını sağlayan yeni bir parametreyle (`--path [directory]`) genişletilmiş
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1010949"></a>101.09.49

- IT yöneticisi tarafından yönetilen dışlamaları ve yerel kullanıcı tarafından tanımlanan dışlamaları ayırt etmek için kullanıcı arabirimi geliştirmeleri
- Isteğe bağlı taramalar sırasında geliştirilmiş CPU kullanımı
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1010723"></a>101.07.23

- Pasif modunun durumunu denetleme çıkışına `mdatp --health` ve pasif grup kimliğini denetleme çıkışına yeni EDR eklendi

  > [!NOTE]
  > `mdatp --health` gelecek bir ürün `mdatp health` güncelleştirmesi ile değiştireceğiz.

- Kullanıcı arabiriminde otomatik örnek gönderimin yönetiliyor olarak işaretilma hatası düzeltildi
- Virüsten koruma tarama geçmişinde öğelerin bekletmeyi denetlemek için yeni ayarlar eklendi. Artık tarama [geçmişinde öğeleri tutmak için gün sayısını ve tarama geçmişinde](mac-preferences.md#antivirus-scan-history-retention-in-days) en fazla [öğe sayısını belirtebilirsiniz](mac-preferences.md#maximum-number-of-items-in-the-antivirus-scan-history)
- Hata düzeltmeleri

## <a name="1010663"></a>101.06.63

- Sürümde ortaya konu olan bir performans gerilemesinde ele alındı `101.05.17`. Regresyon, çekirdekte SMB paylaşımlara erişilirken bazı müşterilerin gözlemlemektedir olduğu paniğe neden olan düzeltmeyi ortadan kaldırmaya başlandı. Bu kod değişikliğini geri başlattık ve çekirdek paniğini ortadan kaldırmanın alternatif yollarını araştırıyoruz.

## <a name="1010517"></a>101.05.17

> [!IMPORTANT]
> Komut satırı aracı için yeni ve gelişmiş bir söz dizimi `mdatp` üzerinde çalışıyoruz. Yeni söz dizimi şu anda Insider Hızlı ve Insider Yavaş güncelleştirme kanallarında varsayılan ayardır. Bu yeni söz dizimi ile kendinizi daha soluk hale düzenlemeyi teşvik etmek için çok çalışmanız gerekiyor.
>
> Yeni söz dizimi ile paralel olarak eski söz dizimini desteklemeye devam edeceğiz ve önümüzdeki aylarda eski söz dizimi için kullanımdan kullanım planıyla ilgili daha fazla iletişim sağlanacak.

- SMB dosya paylaşımlara erişirken bazı durumlarda çekirdek paniğine neden olan bir soruna değinildi
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1010516"></a>101.05.16

- Taranan dosyaların sayısını önemli ölçüde azaltmak için hızlı tarama mantığına yapılan iyileştirmeler
- Komut [satırı aracı için](mac-resources.md#how-to-enable-autocompletion) otomatik tamamlama desteği eklendi
- Hata düzeltmeleri

## <a name="1010312"></a>101.03.12

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1010154"></a>101.01.54

- Time Machine ile uyumlulukla ilgili iyileştirmeler
- Erişilebilirlik geliştirmeleri
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1010031"></a>101.00.31

- Yeni kullanıcılar [için geliştirilmiş ürün Intune deneyimi](/mem/intune/apps/apps-advanced-threat-protection-macos)
- [Virüsten koruma dışlamaları artık joker karakterleri destekliyor](mac-exclusions.md#supported-exclusion-types)
- macOS bağlam menüsünden virüsten koruma taramalarını tetikleme özelliği eklendi. Artık Finder'daki bir dosyaya veya klasöre sağ tık tıklar ve Dosya ile **tara'yı Uç Nokta için Microsoft Defender**
- Yerinde ürün yüklemeleri artık yükleyici tarafından açıkça izin verilmedi. Eski sürümü yüklemeden önce mevcut sürümü kaldırıp cihazınızı yeniden yapılandırmanız gerekir.
- Diğer performans iyileştirmeleri & düzeltmeleri

## <a name="1009027"></a>100.90.27

- Artık [macOS'ta sistem genelindeki](mac-updates.md#set-the-channel-name) güncelleştirme Uç Nokta için Microsoft Defender farklı bir güncelleştirme kanalı için güncelleştirme kanalını
- Yeni ürün simgesi
- Diğer kullanıcı deneyimi geliştirmeleri
- Hata düzeltmeleri

## <a name="1008692"></a>100.86.92

- Time Machine ile uyumlulukla ilgili iyileştirmeler
- Kaldırma işlemi sırasında ürünün bazen altındaki tüm dosyaları temizlemesi sırasında ürünün temizlenmesine `/Library/Application Support/Microsoft/Defender` neden olan bir soruna çözüm
- Microsoft ürünleri Microsoft AutoUpdate aracılığıyla güncelleştirildiğinde ürünün CPU kullanımını azaltıldı
- Diğer performans iyileştirmeleri & düzeltmeleri

## <a name="1008691"></a>100.86.91

> [!CAUTION]
> macOS cihazlarınız için en eksiksiz korumayı sağlamak ve Apple ile hizalama yapmak, Apple'ın macOS yerel güvenlik güncelleştirmelerinin [geçerli - 2] daha eski OS sürümlerine teslimini durdurmak için, Mac için MDATP dağıtımı ve güncelleştirmeleri macOS Sierra [10.12] üzerinde artık destek sağlanmamayacak. Mac için MDATP güncelleştirmeleri ve iyileştirmeleri Catalina [10.15], Mojave [10.14] ve High Sierra [10.13] sürümlerini çalıştıran cihazlara teslim edilecektir.
>
> Sierra [10.12] cihazlarınıza zaten Mac için MDATP dağıtılmışsa, koruma riskini ortadan kaldırmak için lütfen en son macOS sürümüne yükseltin.

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1008373"></a>100.83.73

- Dışlamaların yönetimi, [tehdit türü](mac-preferences.md#exclusion-merge-policy) ayarlarının yönetimi ve izin verilmeyen tehdit eylemleriyle ilgili [olarak, IT](mac-preferences.md#threat-type-settings-merge-policy) [yöneticilerine daha fazla denetim eklendi](mac-preferences.md#disallowed-threat-actions)
- Cihazda Tam Disk Erişimi etkinleştirilmemişse durum menüsünde artık bir uyarı görüntülenir
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1008260"></a>100.82.60

- Ürünün bir tanım güncelleştirmesini takip edene kadar başlatılamama sorunu giderildi.

## <a name="1008042"></a>100.80.42

- Hata düzeltmeleri

## <a name="1007942"></a>100.79.42

- Mac'te Uç Nokta için Microsoft Defender time machine'i engellemeye neden olan sorun düzeltildi
- Arka uç hizmetiyle bağlantının test etmek için komut satırı yardımcı programına yeni bir anahtar eklendi

  ```bash
  mdatp connectivity test
  ```

- Kullanıcı arabiriminde tüm tehdit geçmişini görüntüleme olanağı eklendi (Koruma geçmişi **görünümünden erişilebilir** )
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1007215"></a>100.72.15

- Hata düzeltmeleri

## <a name="1007099"></a>100.70.99

- Gerçek zamanlı koruma etkinleştirildiğinde bazı kullanıcıların macOS Catalina'ya yükseltmesini etkileyen bir soruna değinildi. Bu düzensiz soruna, Catalina Uç Nokta için Microsoft Defender paketi içindeki dosyaları tehditlere karşı tararken kilitleme hatası neden oldu ve yükseltme sırasında hatalara yol açtı.

## <a name="1006899"></a>100.68.99

- Virüsten koruma işlevini pasif modunda çalıştıracak şekilde yapılandırma [özelliği eklendi](mac-preferences.md#enforcement-level-for-antivirus-engine)
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1006528"></a>100.65.28

- macOS Catalina için destek eklendi

  > [!CAUTION]
  > macOS 10.15 (Catalina) yeni güvenlik ve gizlilik iyileştirmeleri içerir. Bu sürümden başarak, uygulamalar varsayılan olarak açık izin alınmadan diskte bazı konumlara (Belgeler, İndirmeler, Masaüstü, vb.) erişemez. Bu iznin olmaması Uç Nokta için Microsoft Defender, cihazınızı tam olarak koruyamaz.
  >
  > Bu izni vermek için kullanılan mekanizma, bu izni nasıl dağıttılmışa Uç Nokta için Microsoft Defender:
  >
  > - El ile dağıtımlar için, El ile dağıtım konusunda yer alan [güncelleştirilmiş yönergelere](mac-install-manually.md#how-to-allow-full-disk-access) bakın.
  > - Yönetilen dağıtımlar için[, JAMF](mac-install-with-jamf.md) tabanlı dağıtım ve dağıtım Microsoft Intune [ilgili güncelleştirilmiş yönergelere](mac-install-with-intune.md#create-system-configuration-profiles) bakın.

- Performans iyileştirmeleri & hata düzeltmeleri
