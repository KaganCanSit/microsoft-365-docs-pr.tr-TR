---
title: Uç nokta için Microsoft Defender'da canlı yanıt kullanan cihazlarda varlıkları araştırma
description: Bir cihazda gerçek zamanlı olarak üzerinde acil yanıt eylemleri yapmak için güvenli bir uzaktan kabuk bağlantısı kullanarak bir cihaza erişin.
keywords: remote, shell, connection, live, response, real-time, command, script, remediate, hunt, export, log, drop, download, file,
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
ms.openlocfilehash: bc7b18088d25e47cd214da2df94ff5eb524f2e78
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63014159"
---
# <a name="investigate-entities-on-devices-using-live-response"></a>Canlı yanıtı kullanan cihazlardaki varlıkları araştırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Canlı yanıt, güvenlik işlemleri ekiplerinin uzak kabuk bağlantısını kullanarak bir cihaza (makine olarak da adlandırılır) anında erişim sağlar. Bu size, gerçek zamanlı olarak tanımlanan tehditleri hemen içermek için ayrıntılı yatırım yapma ve hemen yanıt eylemleri yapma gücü verir.

Canlı yanıt, güvenlik işlemleri ekibimizin araştırma verilerini toplamalarına, betikler çalıştırmalarına, çözümleme için şüpheli varlıklar göndermelerine, tehditleri düzeltmelerine ve yeni ortaya çıkan tehditleri önceden aramalarına olanak sağlayarak soruşturmaları geliştirmek üzere tasarlanmıştır.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUW]

Canlı yanıtla, analistler aşağıdaki görevlerin hepsini gerçekleştirebilir:

- Bir cihazda yatırım çalışması yapmak için temel ve gelişmiş komutları çalıştırın.
- Kötü amaçlı yazılım örnekleri ve PowerShell betiklerinin sonuçları gibi dosyaları indirin.
- Dosyaları arka planda indirin (yeni!).
- Upload bir PowerShell betiği veya yürütülebilir dosyasını kitaplıkta yürütülebilir olarak çalıştırın ve bir cihaz üzerinde kiracı düzeyinden çalıştırın.
- Düzeltme eylemleri gerçekleştirin veya geri alın.

## <a name="before-you-begin"></a>Başlamadan önce

Cihazda oturumu başlatamadan önce, aşağıdaki gereksinimleri karşılayın:

- **Dosyanın desteklenen bir sürümünü çalıştırarak Windows**.

  Cihazlar, aşağıdaki Windows sürümlerinden birini çalıştırabiliyor Windows

  - **Windows 10 & 11**
    - [Sürüm 1909](/windows/whats-new/whats-new-windows-10-version-1909) veya sonrası
    - [KB4515384 ile](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384) Sürüm [1903](/windows/whats-new/whats-new-windows-10-version-1903)
    - [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818) [ile Sürüm 1809 (RS 5)](/windows/whats-new/whats-new-windows-10-version-1809)
    - [KB4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795) [ile Sürüm 1803 (RS 4)](/windows/whats-new/whats-new-windows-10-version-1803)
    - [KB4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816) [ile Sürüm 1709 (RS 3)](/windows/whats-new/whats-new-windows-10-version-1709)

  - **macOS** - Yalnızca Genel Önizleme için geçerlidir, minimum gerekli sürüm: 101.43.84 
  
   > [!NOTE]
   > Şu anda yalnızca Intel tabanlı macOS sistemleri desteklemektedir.
    

  - **Linux** - Yalnızca Genel Önizleme için geçerlidir, minimum gerekli sürüm: 101.45.13 
    
  - **Windows Server 2012 R2** - [KB5005292 ile](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac)
  
  - **Windows Server 2016** - [KB5005292 ile](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac)

  - **Windows Server 2019**
    - Sürüm 1903 veya ( [KB4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384) ile) daha sonraki sürümler
    - Sürüm 1809 ( [KB4537818 ile](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818))
    
  - **Windows Server 2022**

       

- **Gelişmiş ayarlar sayfasından canlı yanıtı etkinleştirin**.

  Gelişmiş özellikler ayarları sayfasında canlı yanıt özelliğini [etkinleştirmeniz](advanced-features.md) gerekir.

  > [!NOTE]
  > Yalnızca güvenliği veya genel yönetici rollerini yöneten kullanıcılar bu ayarları düzenleyebilir.

- **Gelişmiş ayarlar sayfasından sunucular için canlı yanıtı etkinleştir** (önerilir).

  > [!NOTE]
  > Yalnızca güvenliği veya genel yönetici rollerini yöneten kullanıcılar bu ayarları düzenleyebilir.

- **Cihazın bir Otomasyon Düzeltme düzeyi atanmış olduğundan emin olun**.

  Belirli bir Cihaz Grubu için en azından en düşük Düzeltme Düzeyini etkinleştirmeniz gerekir. Aksi takdirde, bu grubun bir üyesine Canlı Yanıt oturumu kurabilirsiniz.

  Aşağıdaki hatayı alırsınız:

  ![Hata iletisinin görüntüsü.](images/live-response-error.png)

- **Canlı yanıt imzalanmamış betik yürütmesini etkinleştir** (isteğe bağlı).

  >[!IMPORTANT]
  >İmza doğrulaması yalnızca PowerShell betikleri için geçerlidir. 

  > [!WARNING]
  > Imzasız betiklerin kullanımına izin vermeniz tehditlere maruz kalmanızı artırabilir.

  Imzasız betiklerin kullanılması önerilmez çünkü tehditlere maruz kalmanızı artırabilir. Ancak bunları kullanmak zorundasanız, Gelişmiş özellikler ayarları sayfasındaki [ayarı etkinleştirmeniz](advanced-features.md) gerekir.

- **Uygun izinlere sahip olduğundan emin olun**.

  Yalnızca uygun izinlere sahip sağlanan kullanıcılar oturumu başlatabilirsiniz. Rol atamaları hakkında daha fazla bilgi için bkz. [Rol oluşturma ve yönetme](user-roles.md).

  > [!IMPORTANT]
  > Kitaplığına dosya yükleme seçeneği yalnızca "Güvenlik Yönetimi" izni olan Ayarlar kullanılabilir.
  > Yalnızca temsili izinlere sahip kullanıcılar için düğme gri gösterilir.

  Size verilen role bağlı olarak, temel veya gelişmiş canlı yanıt komutlarını çalıştırabilirsiniz. Kullanıcı izinleri RBAC özel rolü tarafından denetlenr.

## <a name="live-response-dashboard-overview"></a>Canlı yanıt panosuna genel bakış

Bir cihazda canlı yanıt oturumu başlattığınız zaman bir pano açılır. Pano, oturum hakkında aşağıdakiler gibi bilgiler sağlar:

- Who oturumu oluşturmadı
- Oturum ne zaman başladı?
- Oturumun süresi

Pano ayrıca şunları erişmenıza da izin verir:

- Oturumun bağlantısını kes
- Upload kitaplığına ekleme
- Komut konsolu
- Komut günlüğü

## <a name="initiate-a-live-response-session-on-a-device"></a>Cihazda canlı yanıt oturumu başlatma

1. Portalda oturum Microsoft 365 Defender açın.

2. Cihaz **envanteri için > noktalarına gidin** ve araştırılacak cihazı seçin. Cihazlar sayfası açılır.

3. Canlı yanıt oturumunu başlat'ı seçerek **canlı yanıt oturumunu başlat'ı seçin**. Bir komut konsolu görüntülenir. Oturum cihaza bağlanırken bekleyin.

4. Yerleşik komutları kullanarak yatırım yapmak için bu komutları kullanın. Daha fazla bilgi için bkz. [Canlı yanıt komutları](#live-response-commands).

5. Araştırmanızı tamamladıktan sonra Oturumun bağlantısını **kes'i seçin** ve sonra da Onayla'ya **seçin**.

## <a name="live-response-commands"></a>Canlı yanıt komutları

Size verilen role bağlı olarak, temel veya gelişmiş canlı yanıt komutlarını çalıştırabilirsiniz. Kullanıcı izinleri RBAC özel rolleri tarafından denetlenr. Rol atamaları hakkında daha fazla bilgi için bkz. [Rol oluşturma ve yönetme](user-roles.md).

> [!NOTE]
> Canlı yanıt, bulut tabanlı bir etkileşimli kabuktur, örneğin belirli komut deneyimi, son kullanıcıyla hedef cihaz arasındaki ağ kalitesine ve sistem yüküne bağlı olarak yanıt süresinde değişiklik gösterebilir.

### <a name="basic-commands"></a>Temel komutlar

Aşağıdaki komutlar, temel canlı yanıt komutlarını çalıştırma özelliği verilen kullanıcı **rollerinde** kullanılabilir. Rol atamaları hakkında daha fazla bilgi için bkz. [Rol oluşturma ve yönetme](user-roles.md).

<br>

****
| Komut  | Açıklama  | Windows ve Windows Server  | macOS  | Linux  |
|---|---|---|---|---|
| cd  | Geçerli dizini değiştirir.  | E  | E  | E  |
| cls  | Konsol ekranı temizleniyor.  | E  | E  | E  |
| bağlanma  | Cihaza canlı yanıt oturumu başlatılır.  | E  | E  | E  |
| bağlantılar  | Tüm etkin bağlantıları gösterir.  | E  | N  | N  |
| dir  | Dizinde dosyaların ve alt dizinlerin listesini gösterir.  | E  | E  | E  |
| sürücüler  | Cihazda yüklü olan tüm sürücüleri gösterir.  | E  | N  | N  |
| fg `<command ID>`  | Belirtilen işi ön plana, bu da geçerli iş yapmak için ön plana yer alır.  NOT: fg, PID değil işlerden kullanılabilir bir 'komut kimliği' alır  | E  | E  | E  |
| dosyabilgileri  | Dosya hakkında bilgi al.  | E  | E  | E  |
| findfile  | Cihaz üzerinde adı verilen bir adla dosyaları bular.  | E  | E  | E  |
| getfile <file_path>  | Dosyayı indirir.  | E  | E  | E  |
| Yardım  | Canlı yanıt komutları için yardım bilgileri sağlar.  | E  | E  | E  |
| işler  | Şu anda çalışan işleri, bunların kimliğini ve durumunu gösterir.  | E  | E  | E  |
| kalıcılık  | Cihaz üzerinde tüm bilinen kalıcılık yöntemlerini gösterir.  | E  | N  | N  |
| işlemler  | Cihazda çalışan tüm işlemleri gösterir.  | E  | E  | E  |
| kayıt defteri  | Kayıt defteri değerlerini gösterir.  | E  | N  | N  |
| zamanlanmış görev  | Cihazda tüm zamanlanmış görevleri gösterir.  | E  | N  | N  |
| hizmetler  | Cihaz'ın tüm hizmetlerini gösterir.  | E  | N  | N  |
| başlangıç klasörleri  | Cihaz üzerinde başlangıç klasörlerini içeren bilinen tüm dosyaları gösterir.  | E  | N  | N  |
| durum  | Belirli komutun durumunu ve çıktısını gösterir.  | E  | N  | N  |
| izleme  | Hata ayıklamak için terminalin günlüğe kaydetme modunu ayarlar.  | E  | E  | E  |

### <a name="advanced-commands"></a>Gelişmiş komutlar

Gelişmiş canlı yanıt komutlarını çalıştırma özelliği verilen kullanıcı rollerinde **aşağıdaki** komutlar kullanılabilir. Rol atamaları hakkında daha fazla bilgi için bkz. [Rol oluşturma ve yönetme](user-roles.md).

<br>

****

| Komut  | Açıklama  | Windows ve Windows Server  | macOS  | Linux  |
|---|---|---|---|---|
| analiz etme  | Karara var etmek için çeşitli kritik altyapıları olan varlığı analiz eder.  | E  | N  | N  |
| topla  | Makineden suyla ilgili paketi toplar  | N  | E  | E  |
| yalıt  | Uç Nokta için Defender hizmetinin bağlantısını koruyarak cihazın ağ bağlantısını keser  | N  | E  | N  |
| sürüm  | Cihazı ağ yalıtlığından çıkartır  | N  | E  | N  |
| çalıştır  | Cihazda kitaplıktan bir PowerShell betiği çalıştırır.  | E  | E  | E  |
| kitaplık  | Canlı yanıt kitaplığına yüklenen dosyaları listeler.  | E  | E  | E  |
| putfile  | Kitaplıktan cihaza bir dosya koyar. Dosyalar çalışma klasörüne kaydedilir ve cihaz varsayılan olarak yeniden başlatıldığında silinir.  | E  | E  | E  |
| düzeltmek  | Cihazda bir varlığı düzeltme. Düzeltme eylemi, şu varlık türüne bağlı olarak değişir: Dosya: silme İşlem: durdur, görüntü dosyası silme Hizmet: durdur, görüntü dosyası kayıt defteri girdisini sil: Zamanlanmış görevi sil: Başlangıç klasörü öğesini kaldır: Dosya notunu sil: Bu komutun önkoşul komutu vardır. Önkoşul komutu otomatik olarak çalıştırmak için -auto komutunu düzeltmekle birlikte kullanabilirsiniz.  | E  | E  | E  |
| tarama | Kötü amaçlı yazılımları tanımlamaya ve düzeltmeye yardımcı olmak için bir virüsten koruma taraması çalıştırır. | N | E | E |
| geri al  | Düzeltmiş olan bir varlığı geri yükleme.  | E  | E  | E  |


## <a name="use-live-response-commands"></a>Canlı yanıt komutlarını kullanma

Konsolda kullanabileceğiniz komutlar, Komutlar'daki gibi benzer [Windows izleyin](/windows-server/administration/windows-commands/windows-commands#BKMK_c).

Gelişmiş komutlar, dosyayı indirme ve karşıya yükleme, cihazda betikler çalıştırma ve varlık üzerinde düzeltme eylemleri gerçekleştir gibi daha güçlü eylemler alamanız için daha güçlü bir eylem kümesi sağlar.

### <a name="get-a-file-from-the-device"></a>Cihazdan dosya al

Araştıran bir cihazdan dosya almak istediğiniz senaryolar için komutu kullanabilirsiniz `getfile` . Bu işlem, daha fazla araştırma yapmak için dosyayı cihazdan kaydetmenizi sağlar.

> [!NOTE]
> Aşağıdaki dosya boyutu sınırları geçerlidir:
>
> - `getfile` sınır: 3 GB
> - `fileinfo` sınır: 10 GB
> - `library` sınır: 250 MB

### <a name="download-a-file-in-the-background"></a>Arka planda dosya indirme

Güvenlik işlemleri ekibimizin etkili olan bir cihazı araştırmaya devam ettiğine olanak sağlamak için dosyalar artık arka planda indirilebilir.

- Arka planda bir dosya indirmek için canlı yanıt komut konsoluna yazarak yazın `download <file_path> &`.
- Bir dosyanın indirildikten sonra Ctrl + Z tuşlarını kullanarak dosyayı arka plana taşımanız gerekir.
- Ön plana bir dosya indirme işlemi getirmek için canlı yanıt komut konsoluna yazarak yazın `fg <command_id>`.

İşte birkaç örnek:

<br>

****

|Komut|Yaptığı iş|
|---|---|
|`getfile "C:\windows\some_file.exe" &`|Arka planda Dosya adlı *some_file.exe* indirmeye başlar.|
|`fg 1234`|Ön plana *1234 komut kimliğiyle* bir indirme döndürür.|
|

### <a name="put-a-file-in-the-library"></a>Kitaplı kitaplıya dosya koyma

Canlı yanıt'da dosyaları girebilirsiniz. Kitaplık, canlı yanıt oturumunda kiracı düzeyinde çalıştır yalnızca betikler gibi dosyaları depolar.

Canlı yanıt PowerShell betiklerini çalıştırmaya olanak sağlar, ancak bu dosyaları çalıştırmadan önce bu dosyaları kitaplılara koymanız gerekir.

Canlı yanıt oturumlarını başlattığınız cihazlarda çalıştıracak bir PowerShell betikleri koleksiyonunuz olabilir.

#### <a name="to-upload-a-file-in-the-library"></a>Kitaplıkta bir dosyayı karşıya yüklemek için

1. Dosyayı **Upload'e tıklayın**.

2. **Gözat'a** tıklayın ve dosyayı seçin.

3. Kısa bir açıklama girin.

4. Aynı adı alan bir dosyanın üzerine yazarak yazmak istediğiniz dosyayı belirtin.

5. Olmak ve betik için hangi parametrelerin gerekli olduğunu bilmek için betik parametreleri onay kutusunu seçin. Metin alanına bir örnek ve açıklama girin.

6. **Onayla'ya tıklayın**.

7. (İsteğe bağlı) Dosyanın kitaplı kitaplıya yük olduğunu doğrulamak için komutu `library` çalıştırın.

### <a name="cancel-a-command"></a>Komutu iptal etme

Oturum sırasında istediğiniz zaman CTRL + C tuşlarına basarak komutu iptal edebilirsiniz.

> [!WARNING]
> Bu kısayolun kullanımı aracı tarafındaki komutu durdurmaz. Yalnızca portalda komutu iptal eder. Dolayısıyla, komut iptal edilirken "düzeltme" gibi işlemler de devam edebilir.

## <a name="run-a-script"></a>Betik çalıştırma

PowerShell/Bash betiklerini çalıştıramadan önce bu betikleri kitaplı kitaplılara yüklelisiniz.

Betiği kitaplı kitaplara yükledikten sonra, betiği `run` çalıştırmak için komutu kullanın.

Oturumda imzalanmamış bir PowerShell betiği kullanmayı planlıyorsanız, Gelişmiş özellik ayarları sayfasında bu [ayarı etkinleştirmeniz](advanced-features.md) gerekir.

> [!WARNING]
> Imzasız betiklerin kullanımına izin vermeniz tehditlere maruz kalmanızı artırabilir.

## <a name="apply-command-parameters"></a>Komut parametreleri uygulama

- Komut parametreleri hakkında bilgi edinmek için konsol yardımlarını görüntü edinin. Tek bir komut hakkında bilgi edinmek için şu komutu çalıştırın:

  ```powershell
  help <command name>
  ```

- Komutlara parametreler uygularken, parametrelerin sabit bir düzende işlenmiş olduğunu unutmayın:

  ```powershell
  <command name> param1 param2
  ```

- Sabit sıranın dışındaki parametreleri belirtirken, değeri sağlamadan önce parametrenin adını kısa çizgiyle belirtin:

  ```powershell
  <command name> -param2_name param2
  ```

- Önkoşul komutları olan komutları kullanırken bayrakları kullanabilirsiniz:

  ```powershell
  <command name> -type file -id <file path> - auto
  ```

  veya

  ```powershell
  remediate file <file path> - auto`
  ```

## <a name="supported-output-types"></a>Desteklenen çıktı türleri

Canlı yanıt, tablo ve JSON biçimi çıkış türlerini destekler. Her komut için varsayılan bir çıkış davranışı vardır. Şu komutları kullanarak, çıkışı tercih ettiğiniz çıkış biçiminde değiştirebilirsiniz:

- `-output json`
- `-output table`

> [!NOTE]
> Alan sınırlı olduğu için tablo biçiminde daha az alan gösterilir. Çıktıda daha fazla ayrıntı görmek için JSON çıktısı komutunu kullanarak daha fazla ayrıntı gösterebilirsiniz.

## <a name="supported-output-pipes"></a>Desteklenen çıkış kanallar

Canlı yanıt CLI'ya ve dosyaya çıkış borularını destekler. CLI varsayılan çıkış davranışıdır. Şu komutu kullanarak çıkışı bir dosyaya abilirsiniz: [komut] > [dosyaadı].txt.

Örneğin:

```console
processes > output.txt
```

## <a name="view-the-command-log"></a>Komut günlüğünü görüntüleme

Oturum **sırasında cihazda** kullanılan komutları görmek için Komut günlüğü sekmesini seçin. Her komut, şu gibi tüm ayrıntılarla birlikte iz):

- Kimlik
- Komut satırı
- Süre
- Durum ve giriş veya çıkış yan çubuğu

## <a name="limitations"></a>Sınırlamalar

- Canlı yanıt oturumları bir defada 25 canlı yanıt oturumuyla sınırlıdır.
- Canlı yanıt oturumunun etkin olmayan zaman aşımı değeri 30 dakikadır.
- Bir kullanıcı en çok 10 eşzamanlı oturum başlatabilirsiniz.
- Bir cihaz aynı anda yalnızca bir oturumda olabilir.
- Aşağıdaki dosya boyutu sınırları geçerlidir:
  - `getfile` sınır: 3 GB
  - `fileinfo` sınır: 10 GB
  - `library` sınır: 250 MB

## <a name="related-article"></a>İlgili makale

- [Canlı yanıt komut örnekleri](live-response-command-examples.md)