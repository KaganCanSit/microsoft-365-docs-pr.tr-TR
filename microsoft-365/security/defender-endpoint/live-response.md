---
title: Uç Nokta için Microsoft Defender'de canlı yanıt kullanarak cihazlardaki varlıkları araştırma
description: Araştırma çalışmaları yapmak ve bir cihazda gerçek zamanlı olarak anında yanıt eylemleri gerçekleştirmek için güvenli bir uzak kabuk bağlantısı kullanarak bir cihaza erişin.
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
ms.openlocfilehash: 5e5d2b2bd47ba30aaf152171605947bb9a627480
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666360"
---
# <a name="investigate-entities-on-devices-using-live-response"></a>Canlı yanıt kullanarak cihazlardaki varlıkları araştırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimlemek mi istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Canlı yanıt, güvenlik operasyonları ekiplerine uzak kabuk bağlantısı kullanarak bir cihaza (makine olarak da adlandırılır) anında erişim sağlar. Bu size ayrıntılı araştırma çalışmaları yapma ve belirlenen tehditleri anında gerçek zamanlı olarak içermesi için anında yanıt eylemleri gerçekleştirme gücü verir.

Canlı yanıt, güvenlik operasyonları ekibinizin adli verileri toplamasına, betik çalıştırmasına, şüpheli varlıkları analiz için göndermesine, tehditleri düzeltmesine ve yeni ortaya çıkan tehditleri proaktif olarak avlamasına olanak tanıyarak araştırmalarınızı geliştirmek için tasarlanmıştır.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUW]

Analistler canlı yanıtla aşağıdaki görevlerin tümünü gerçekleştirebilir:

- Bir cihazda araştırma çalışması yapmak için temel ve gelişmiş komutları çalıştırın.
- Kötü amaçlı yazılım örnekleri ve PowerShell betiklerinin sonuçları gibi dosyaları indirin.
- Arka planda dosyaları indirin (yeni!).
- PowerShell betiğini veya yürütülebilir dosyasını kitaplığa Upload ve kiracı düzeyindeki bir cihazda çalıştırın.
- Düzeltme eylemlerini gerçekleştirme veya geri alma.

## <a name="before-you-begin"></a>Başlamadan önce

Bir cihazda oturum başlatabilmeniz için önce aşağıdaki gereksinimleri karşıladığınızdan emin olun:

- **desteklenen bir Windows sürümünü çalıştırdığınızı doğrulayın**.

  Cihazlar aşağıdaki Windows sürümlerinden birini çalıştırıyor olmalıdır

  - **Windows 10 & 11**
    - [Sürüm 1909](/windows/whats-new/whats-new-windows-10-version-1909) veya üzeri
    - [KB4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384) ile [Sürüm 1903](/windows/whats-new/whats-new-windows-10-version-1903)
    - [KB4537818 ile](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818) [Sürüm 1809 (RS 5)](/windows/whats-new/whats-new-windows-10-version-1809)
    - [KB4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795) ile [Sürüm 1803 (RS 4)](/windows/whats-new/whats-new-windows-10-version-1803)
    - [KB4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816) ile [Sürüm 1709 (RS 3)](/windows/whats-new/whats-new-windows-10-version-1709)

  - **macOS** - Yalnızca Genel Önizleme için geçerlidir, gerekli en düşük sürüm: 101.43.84

   > [!NOTE]
   > Şu anda yalnızca Intel tabanlı macOS sistemleri desteklenmektedir.

  - **Linux** - Yalnızca Genel Önizleme için geçerlidir, gerekli en düşük sürüm: 101.45.13

  - **Windows Server 2012 R2** - [KB5005292](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac) ile

  - **Windows Server 2016** - [KB5005292](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac) ile

  - **Windows Server 2019**
    - Sürüm 1903 veya ( [KB4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384) ile) daha sonra
    - Sürüm 1809 ( [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818) ile)

  - **Windows Server 2022**

- **Gelişmiş ayarlar sayfasından canlı yanıtı etkinleştirin**.

  [Gelişmiş özellikler ayarları](advanced-features.md) sayfasında canlı yanıt özelliğini etkinleştirmeniz gerekir.

  > [!NOTE]
  > Bu ayarları yalnızca güvenlik veya genel yönetici rollerini yöneten kullanıcılar düzenleyebilir.
  >
  > Canlı yanıtı etkinleştirmeden önce [Gelişmiş özellikler ayarlarında](advanced-features.md) Otomatik Araştırma etkinleştirilmelidir.

- **Gelişmiş ayarlar sayfasından sunucular için canlı yanıtı etkinleştirin** (önerilir).

  > [!NOTE]
  > Bu ayarları yalnızca güvenlik veya genel yönetici rollerini yöneten kullanıcılar düzenleyebilir.

- **Cihazın kendisine atanmış bir Otomasyon Düzeltme düzeyi olduğundan emin olun**.

  Belirli bir Cihaz Grubu için en azından en düşük Düzeltme Düzeyini etkinleştirmeniz gerekir. Aksi takdirde, bu grubun bir üyesine Canlı Yanıt oturumu oluşturamazsınız.

  Aşağıdaki hatayı alırsınız:

  :::image type="content" source="images/live-response-error.png" alt-text="Hata iletisi" lightbox="images/live-response-error.png":::

- **Canlı yanıt imzalanmamış betik yürütmeyi etkinleştirin** (isteğe bağlı).

  >[!IMPORTANT]
  >İmza doğrulaması yalnızca PowerShell betikleri için geçerlidir.

  > [!WARNING]
  > İmzasız betiklerin kullanılmasına izin vermek, tehditlere maruz kalmanızı artırabilir.

  İmzasız betiklerin çalıştırılması önerilmez, bu da tehditlere maruz kalmanızı artırabilir. Ancak bunları kullanmanız gerekiyorsa [, Gelişmiş özellikler ayarları](advanced-features.md) sayfasında ayarı etkinleştirmeniz gerekir.

- **Uygun izinlere sahip olduğunuzdan emin olun**.

  Yalnızca uygun izinlerle sağlanan kullanıcılar bir oturum başlatabilir. Rol atamaları hakkında daha fazla bilgi için bkz. [Rol oluşturma ve yönetme](user-roles.md).

  > [!IMPORTANT]
  > Kitaplığa dosya yükleme seçeneği yalnızca "Güvenlik Ayarlar Yönetme" iznine sahip kullanıcılar tarafından kullanılabilir.
  > Düğme, yalnızca temsilci izinlerine sahip kullanıcılar için gri renktedir.

  Size verilen role bağlı olarak, temel veya gelişmiş canlı yanıt komutlarını çalıştırabilirsiniz. Kullanıcı izinleri RBAC özel rolü tarafından denetlenmektedir.

## <a name="live-response-dashboard-overview"></a>Canlı yanıt panosuna genel bakış

Bir cihazda canlı yanıt oturumu başlattığınızda bir pano açılır. Pano oturum hakkında aşağıdaki gibi bilgiler sağlar:

- oturumu Who oluşturdunuz
- Oturum başlatıldığında
- Oturumun süresi

Pano ayrıca aşağıdakilere erişmenizi sağlar:

- Oturumun bağlantısını kes
- Dosyaları kitaplığa Upload
- Komut konsolu
- Komut günlüğü

## <a name="initiate-a-live-response-session-on-a-device"></a>Cihazda canlı yanıt oturumu başlatma

1. Microsoft 365 Defender portalında oturum açın.

2. **Uç Noktalar > Cihaz envanterine** gidin ve araştıracak bir cihaz seçin. Cihazlar sayfası açılır.

3. Canlı yanıt oturumunu başlat'ı seçerek **canlı yanıt oturumunu** başlatın. Bir komut konsolu görüntülenir. Oturum cihaza bağlanırken bekleyin.

4. Araştırma çalışması yapmak için yerleşik komutları kullanın. Daha fazla bilgi için bkz [. Canlı yanıt komutları](#live-response-commands).

5. Araştırmanızı tamamladıktan sonra **Oturumu kes'i** ve ardından **Onayla'yı** seçin.

## <a name="live-response-commands"></a>Canlı yanıt komutları

Size verilen role bağlı olarak, temel veya gelişmiş canlı yanıt komutlarını çalıştırabilirsiniz. Kullanıcı izinleri RBAC özel rolleri tarafından denetlenmektedir. Rol atamaları hakkında daha fazla bilgi için bkz. [Rol oluşturma ve yönetme](user-roles.md).

> [!NOTE]
> Canlı yanıt bulut tabanlı etkileşimli bir kabuk olduğundan, belirli komut deneyimi son kullanıcı ile hedef cihaz arasındaki ağ kalitesine ve sistem yüküne bağlı olarak yanıt süresinde değişebilir.

### <a name="basic-commands"></a>Temel komutlar

Aşağıdaki komutlar, **temel** canlı yanıt komutlarını çalıştırma özelliği verilen kullanıcı rolleri için kullanılabilir. Rol atamaları hakkında daha fazla bilgi için bkz. [Rol oluşturma ve yönetme](user-roles.md).

| Komut  | Açıklama  | Windows ve Windows Sunucusu  | macOS  | Linux  |
|---|---|---|---|---|
| Cd  | Geçerli dizini değiştirir.  | E  | E  | E  |
| Cls  | Konsol ekranını temizler.  | E  | E  | E  |
| Bağlamak  | Cihaza canlı yanıt oturumu başlatır.  | E  | E  | E  |
| Bağlantı  | Tüm etkin bağlantıları gösterir.  | E  | N  | N  |
| Dir  | Dizindeki dosyaların ve alt dizinlerin listesini gösterir.  | E  | E  | E  |
| Sürücüler  | Cihazda yüklü olan tüm sürücüleri gösterir.  | E  | N  | N  |
| Fg `<command ID>`  | Belirtilen işi ön planda ön plana yerleştirerek geçerli iş haline getirir.  NOT: fg, PID değil işlerden kullanılabilen bir 'komut kimliği' alır  | E  | E  | E  |
| Fileınfo  | Dosya hakkında bilgi edinin.  | E  | E  | E  |
| Findfile  | Cihazdaki belirli bir ada göre dosyaları bulur.  | E  | E  | E  |
| getfile <file_path>  | Bir dosya indirir.  | E  | E  | E  |
| Yardım  | Canlı yanıt komutları için yardım bilgileri sağlar.  | E  | E  | E  |
| Işleri  | Çalışmakta olan işleri, kimliklerini ve durumlarını gösterir.  | E  | E  | E  |
| Kalıcılık  | Cihazda bilinen tüm kalıcılık yöntemlerini gösterir.  | E  | N  | N  |
| Süreç  | Cihazda çalışan tüm işlemleri gösterir.  | E  | E  | E  |
| Kayıt defteri  | Kayıt defteri değerlerini gösterir.  | E  | N  | N  |
| scheduledtasks  | Cihazdaki tüm zamanlanmış görevleri gösterir.  | E  | N  | N  |
| Hizmetleri  | Cihazdaki tüm hizmetleri gösterir.  | E  | N  | N  |
| başlangıç klasörleri  | Cihazdaki başlangıç klasörlerindeki tüm bilinen dosyaları gösterir.  | E  | N  | N  |
| Durum  | Belirli bir komutun durumunu ve çıkışını gösterir.  | E  | N  | N  |
| Izleme  | Hata ayıklamak için terminalin günlük modunu ayarlar.  | E  | E  | E  |

### <a name="advanced-commands"></a>Gelişmiş komutlar

Gelişmiş **canlı yanıt** komutlarını çalıştırma yeteneği verilen kullanıcı rolleri için aşağıdaki komutlar kullanılabilir. Rol atamaları hakkında daha fazla bilgi için bkz. [Rol oluşturma ve yönetme](user-roles.md).

| Komut  | Açıklama  | Windows ve Windows Sunucusu  | macOS  | Linux  |
|---|---|---|---|---|
| Analiz  | Bir karara ulaşmak için varlığı çeşitli eğim altyapılarıyla analiz eder.  | E  | N  | N  |
| Toplamak  | Makineden adli tıp paketini toplar  | N  | E  | E  |
| Yalıt  | Uç Nokta için Defender hizmetine bağlantıyı korurken cihazın ağ bağlantısını keser  | N  | E  | N  |
| Sürüm  | Bir cihazı ağ yalıtımından serbest bırakır  | N  | E  | N  |
| Çalıştırmak  | Cihazdaki kitaplıktan bir PowerShell betiği çalıştırır.  | E  | E  | E  |
| Kitaplığı  | Canlı yanıt kitaplığına yüklenen dosyaları listeler.  | E  | E  | E  |
| putfile  | Kitaplıktan cihaza bir dosya yerleştirir. Dosyalar çalışma klasörüne kaydedilir ve cihaz varsayılan olarak yeniden başlatıldığında silinir.  | E  | E  | E  |
| düzeltme  | Cihazdaki bir varlığı düzeltin. Düzeltme eylemi varlık türüne bağlı olarak değişir: Dosya: silme İşlem: durdurma, görüntü dosyasını silme Hizmet: durdurma, resim dosyasını silme Kayıt defteri girdisi: silme Zamanlanmış görev: Başlangıç klasörü öğesini kaldırma: dosya silme NOT: Bu komutun önkoşul komutu vardır. Önkoşul komutunu otomatik olarak çalıştırmak için düzeltme ile birlikte -auto komutunu kullanabilirsiniz.  | E  | E  | E  |
| Tarama | Kötü amaçlı yazılımları tanımlamaya ve düzeltmeye yardımcı olmak için bir virüsten koruma taraması çalıştırır. | N | E | E |
| Geri alma  | Düzeltilmiş bir varlığı geri yükler.  | E  | E  | E  |

## <a name="use-live-response-commands"></a>Canlı yanıt komutlarını kullanma

Konsolunda kullanabileceğiniz komutlar[, Windows Komutları](/windows-server/administration/windows-commands/windows-commands#BKMK_c) ile benzer ilkeleri izler.

Gelişmiş komutlar, bir dosyayı indirip karşıya yükleme, betikleri cihazda çalıştırma ve bir varlıkta düzeltme eylemleri gerçekleştirme gibi daha güçlü eylemler gerçekleştirmenize olanak sağlayan daha güçlü bir eylem kümesi sunar.

### <a name="get-a-file-from-the-device"></a>Cihazdan dosya alma

Araştırdığınız bir cihazdan dosya almak istediğiniz senaryolar için komutunu kullanabilirsiniz `getfile` . Bu, daha fazla araştırma için dosyayı cihazdan kaydetmenizi sağlar.

> [!NOTE]
> Aşağıdaki dosya boyutu sınırları geçerlidir:
>
> - `getfile` sınır: 3 GB
> - `fileinfo` sınır: 30 GB
> - `library` sınır: 250 MB

### <a name="download-a-file-in-the-background"></a>Arka planda dosya indirme

Güvenlik operasyonları ekibinizin etkilenen bir cihazı araştırmaya devam edebilmesi için dosyalar artık arka planda indirilebilir.

- Arka planda bir dosya indirmek için canlı yanıt komut konsoluna yazın `download <file_path> &`.
- Bir dosyanın indirilmesi için bekliyorsanız, Ctrl + Z tuşlarını kullanarak dosyayı arka plana taşıyabilirsiniz.
- Bir dosya indirmesini ön plana getirmek için canlı yanıt komut konsoluna yazın `fg <command_id>`.

İşte birkaç örnek:

<br>

****

|Komut|Ne işe yarıyor?|
|---|---|
|`getfile "C:\windows\some_file.exe" &`|Arka planda *some_file.exe* adlı bir dosyayı indirmeye başlar.|
|`fg 1234`|*Ön plana 1234* komut kimliğine sahip bir indirme döndürür.|
|

### <a name="put-a-file-in-the-library"></a>Bir dosyayı kitaplığa yerleştirme

Canlı yanıt, dosyaları yerleştirebileceğiniz bir kitaplığa sahiptir. Kitaplık, kiracı düzeyinde canlı yanıt oturumunda çalıştırılabilir dosyaları (betikler gibi) depolar.

Canlı yanıt PowerShell betiklerinin çalıştırılmasına izin verir, ancak dosyaları çalıştırabilmek için önce kitaplığa yerleştirmeniz gerekir.

Canlı yanıt oturumları başlattığınız cihazlarda çalıştırabileceğiniz bir PowerShell betikleri koleksiyonunuz olabilir.

#### <a name="to-upload-a-file-in-the-library"></a>Kitaplığa dosya yüklemek için

1. **Dosya kitaplığına Upload'e** tıklayın.

2. **Gözat'a** tıklayın ve dosyayı seçin.

3. Kısa bir açıklama sağlayın.

4. Aynı ada sahip bir dosyanın üzerine yazmak isteyip istediğinizi belirtin.

5. Betik için hangi parametrelerin gerekli olduğunu öğrenmek istiyorsanız, betik parametreleri onay kutusunu seçin. Metin alanına bir örnek ve açıklama girin.

6. **Onayla'ya** tıklayın.

7. (İsteğe bağlı) Dosyanın kitaplığa yüklendiğini doğrulamak için komutunu çalıştırın `library` .

### <a name="cancel-a-command"></a>Komutu iptal etme

Oturum sırasında istediğiniz zaman CTRL + C tuşlarına basarak bir komutu iptal edebilirsiniz.

> [!WARNING]
> Bu kısayolu kullanmak aracı tarafında komutu durdurmaz. Yalnızca portaldaki komutu iptal eder. Bu nedenle, komut iptal edilirken "düzeltme" gibi işlemlerin değiştirilmesi devam edebilir.

## <a name="run-a-script"></a>Betik çalıştırma

PowerShell/Bash betiğini çalıştırabilmeniz için önce bunu kitaplığa yüklemeniz gerekir.

Betiği kitaplığa yükledikten sonra komutunu kullanarak `run` betiği çalıştırın.

Oturumda imzalanmamış bir PowerShell betiği kullanmayı planlıyorsanız, [Gelişmiş özellikler ayarları](advanced-features.md) sayfasında ayarı etkinleştirmeniz gerekir.

> [!WARNING]
> İmzasız betiklerin kullanılmasına izin vermek, tehditlere maruz kalmanızı artırabilir.

## <a name="apply-command-parameters"></a>Komut parametrelerini uygulama

- Komut parametreleri hakkında bilgi edinmek için konsol yardımını görüntüleyin. Tek bir komut hakkında bilgi edinmek için şunu çalıştırın:

  ```powershell
  help <command name>
  ```

- Komutlara parametre uygularken, parametrelerin sabit bir düzene göre işlendiğini unutmayın:

  ```powershell
  <command name> param1 param2
  ```

- Parametreleri sabit sıranın dışında belirtirken, değeri sağlamadan önce parametrenin adını kısa çizgiyle belirtin:

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

## <a name="supported-output-types"></a>Desteklenen çıkış türleri

Canlı yanıt, tablo ve JSON biçimi çıkış türlerini destekler. Her komut için varsayılan bir çıkış davranışı vardır. Aşağıdaki komutları kullanarak tercih ettiğiniz çıkış biçimindeki çıkışı değiştirebilirsiniz:

- `-output json`
- `-output table`

> [!NOTE]
> Sınırlı alan nedeniyle daha az alan tablo biçiminde gösterilir. Çıktıda daha fazla ayrıntı görmek için JSON çıkış komutunu kullanarak daha fazla ayrıntı gösterebilirsiniz.

## <a name="supported-output-pipes"></a>Desteklenen çıkış kanalları

Canlı yanıt, CLI ve dosyaya giden çıkış borularını destekler. CLI, varsayılan çıkış davranışıdır. Şu komutu kullanarak çıkışı bir dosyaya aktarabilirsiniz: [command] > [filename].txt.

Örneğin:

```console
processes > output.txt
```

## <a name="view-the-command-log"></a>Komut günlüğünü görüntüleme

Oturum sırasında cihazda kullanılan komutları görmek için **Komut günlüğü** sekmesini seçin. Her komut, şu gibi tüm ayrıntılarla izlenir:

- Kimlik
- Komut satırı
- Süre
- Durum ve giriş veya çıkış yan çubuğu

## <a name="limitations"></a>Sınırlamalar

- Canlı yanıt oturumları, aynı anda 25 canlı yanıt oturumuyla sınırlıdır.
- Etkin olmayan canlı yanıt oturumu zaman aşımı değeri 30 dakikadır.
- Tek tek canlı yanıt komutlarının 30 dakika sınırı olan , `findfile`ve `run`dışında `getfile`10 dakikalık bir zaman sınırı vardır.
- Bir kullanıcı en fazla 10 eşzamanlı oturum başlatabilir.
- Bir cihaz aynı anda yalnızca bir oturumda olabilir.
- Aşağıdaki dosya boyutu sınırları geçerlidir:
  - `getfile` sınır: 3 GB
  - `fileinfo` sınır: 10 GB
  - `library` sınır: 250 MB

## <a name="related-article"></a>İlgili makale

- [Canlı yanıt komut örnekleri](live-response-command-examples.md)
