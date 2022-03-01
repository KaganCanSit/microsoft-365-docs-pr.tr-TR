---
title: Mac'te Uç Nokta için Microsoft Defender için dışlamaları yapılandırma ve doğrulama
description: Mac'te Uç Nokta için Microsoft Defender için dışlamaları sağlama ve doğrulama. Dışlamalar dosyalar, klasörler ve işlemler için ayarlanmış olabilir.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, dışlamalar, taramalar, virüsten koruma
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: a069e3dd3ef99f094f96318277e077c56b7cb974
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011969"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-for-endpoint-on-macos"></a>macOS'ta Uç Nokta için Microsoft Defender için dışlamaları yapılandırma ve doğrulama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Bu makalede, isteğe bağlı taramalar ve gerçek zamanlı koruma ve izleme için geçerli olan dışlamaların nasıl tanımlanması ile ilgili bilgiler ve almaktadır.

> [!IMPORTANT]
> Bu makalede açıklanan dışlamalar, Mac üzerinde Uç Nokta için Defender'ın diğer özellikleri (uç noktada algılama ve yanıtlama EDR. Bu makalede açıklanan yöntemleri kullanarak dışlayın dosyalar yine de uyarı uyarılarını EDR algılamaları tetikler.

Mac'te Uç Nokta için Defender taramalarından belirli dosyaları, klasörleri, süreçleri ve süreç açılan dosyaları hariç tutabilirsiniz.

Dışlamalar, benzersiz veya özelleştirilebilir dosya veya yazılımlarda yanlış algılamaları önlemek için yararlı olabilir. Ayrıca, Mac'te Uç Nokta için Defender'ın neden olduğu performans sorunlarını azaltmada da yararlı olabilir.

> [!WARNING]
> Dışlamaları tanımlamak Mac'te Uç Nokta için Defender'ın sunduğu korumayı düşürer. Dışlamaları uygulamayla ilişkili riskleri her zaman değerlendirmeli ve yalnızca kötü amaçlı olmadığınız dosyaları hariç tutabilirsiniz.

## <a name="supported-exclusion-types"></a>Desteklenen dışlama türleri

Aşağıdaki tablo Mac'te Uç Nokta için Defender tarafından desteklenen dışlama türlerini gösterir.

Dışlama|Tanım|Örnekler
---|---|---
Dosya uzantısı|Uzantılı tüm dosyalar, makinenin herhangi bir yerinde|`.test`
Dosya|Tam yoldan tanımlanan belirli bir dosya|`/var/log/test.log` <p> `/var/log/*.log` <p> `/var/log/install.?.log`
Klasör|Belirtilen klasörün altındaki tüm dosyalar (tekrarlı bir şekilde)|`/var/log/` <p> `/var/*/`
İşlem|Belirli bir işlem (tam yol veya dosya adı ile belirtilen işlem) ve bu dosya tarafından açılan tüm dosyalar|`/bin/cat` <p> `cat` <p> `c?t`

Dosya, klasör ve süreç dışlamaları aşağıdaki joker karakterleri destekler:

Joker karakter|Açıklama|Örnek|Eşleşmeler|Eşmser değil
---|---|---|---|---
\*|Hiçbiri dahil herhangi bir sayıda karakterle eşler (bu joker karakterin yol içinde kullanılırken tek bir klasörün yerini alamayacaktır)|`/var/*/*.log`|`/var/log/system.log`|`/var/log/nested/system.log`
?|Herhangi bir tek karakterle eşler|`file?.log`|`file1.log` <p> `file2.log`|`file123.log`

> [!NOTE]
> Ürün, dışlamaları değerlendirirken kesin bağlantıları çözmeye çalışır. Dışlama joker karakter içeriyorsa veya hedef dosya ( `Data` ses düzeyi üzerinde) yoksa kesin bağlantı çözümü çalışmıyor.

## <a name="how-to-configure-the-list-of-exclusions"></a>Dışlama listesi nasıl yapılandırılır

### <a name="from-the-management-console"></a>Yönetim konsolundan

JAMF, Intune veya başka bir yönetim konsolundan dışlamaları yapılandırma hakkında daha fazla bilgi için bkz. [Mac'te Uç Nokta için Defender tercihlerini ayarlama](mac-preferences.md).

### <a name="from-the-user-interface"></a>Kullanıcı arabiriminden

Aşağıdaki ekran görüntüsünde gösterildiği gibi, Uç nokta  \> için Defender uygulamasını açın ve Ayarları Ekle veya Dışlama **Kaldır...** ayarları yönet'e gidin:

![Dışlamaları yönet ekran görüntüsü.](images/mdatp-37-exclusions.png)

Eklemek istediğiniz dışlama türünü seçin ve istemleri izleyin.

## <a name="validate-exclusions-lists-with-the-eicar-test-file"></a>EICAR test dosyasıyla dışlama listelerini doğrulama

Test dosyasını indirmek için kullanarak dışlama listenizin `curl` çalıştığını doğruabilirsiniz.

Aşağıdaki Bash parçacığında, dışlama `test.txt` kurallarınıza uygun bir dosyayla değiştirin. Örneğin, uzantıyı dışladıysanız `.testing` ile değiştirin `test.txt` `test.testing`. Bir yolu test ediyorsanız, komutu bu yol içinde çalıştırmayı sağlar.

```bash
curl -o test.txt https://www.eicar.org/download/eicar.com.txt
```

Mac'te Uç Nokta için Defender kötü amaçlı yazılım raporlarsa kural çalışmıyordur. Kötü amaçlı yazılım raporu yoksa ve indirilen dosya varsa, dışlama çalışıyor olur. İçeriğin [EICAR test](http://2016.eicar.org/86-0-Intended-use.html) dosyası web sitesinde açıklananla aynı olduğunu onaylamak için dosyayı açabilirsiniz.

İnternet erişiminiz yoksa kendi EICAR test dosyanızı oluşturabilirsiniz. Aşağıdaki Bash komutuyla EICAR dizesini yeni bir metin dosyasına yazın:

```bash
echo 'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*' > test.txt
```

Ayrıca, dizeyi boş bir metin dosyasına kopyalayıp dosya adıyla veya hariç tutmak istediğiniz klasöre kaydetmeyi bırakabilirsiniz.

## <a name="allow-threats"></a>Tehditlere izin ver

Belirli içeriklerin taranmalarını dışlamanın yanı sıra, ürünü tehditlerden (tehdit adıyla tanımlanan) bazı sınıfları algılamayacak şekilde de yapılandırabilirsiniz. Cihazınızı korumasız bıraka kadar bu işlevi kullanırken dikkatli olmalısınız.

İzin verilen listeye bir tehdit adı eklemek için aşağıdaki komutu yürütün:

```bash
mdatp threat allowed add --name [threat-name]
```

Aygıtınızda bir algılamayla ilişkilendirilmiş tehdit adı aşağıdaki komut kullanılarak elde edilir:

```bash
mdatp threat list
```

Örneğin, izin verilen listeye `EICAR-Test-File (not a virus)` (EICAR algılamayla ilişkili tehdit adı) eklemek için aşağıdaki komutu yürütün:

```bash
mdatp threat allowed add --name "EICAR-Test-File (not a virus)"
```
