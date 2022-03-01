---
title: Linux'ta Uç Nokta için Microsoft Defender için dışlamaları yapılandırma ve doğrulama
description: Linux'ta Uç Nokta için Microsoft Defender için dışlamaları sağlama ve doğrulama. Dışlamalar dosyalar, klasörler ve işlemler için ayarlanmış olabilir.
keywords: microsoft, defender, Endpoint, linux için Microsoft Defender, dışlamalar, taramalar, virüsten koruma
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
ms.openlocfilehash: b86cad016af0f7819d69f0156498336652e6292d
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/29/2021
ms.locfileid: "62997051"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender için dışlamaları yapılandırma ve doğrulama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Bu makalede, isteğe bağlı taramalar ve gerçek zamanlı koruma ve izleme için geçerli olan dışlamaların nasıl tanımlanması ile ilgili bilgiler ve almaktadır.

> [!IMPORTANT]
> Bu makalede açıklanan dışlamalar, Uç noktada algılama ve yanıtlama (EDR) dahil olmak üzere Linux'ta Uç Nokta için Diğer Uç Nokta için Defender için geçerli uç noktada algılama ve yanıtlama. Bu makalede açıklanan yöntemleri kullanarak dışlayın dosyalar yine de uyarı uyarılarını EDR algılamaları tetikler.

Linux taramaları için Uç Nokta için Defender'dan belirli dosyaları, klasörleri, süreçleri ve süreç açılan dosyaları hariç tutabilirsiniz.

Dışlamalar, benzersiz veya özelleştirilebilir dosya veya yazılımlarda yanlış algılamaları önlemek için yararlı olabilir. Ayrıca, Linux'ta Uç Nokta için Defender'ın neden olduğu performans sorunlarını azaltmada da yararlı olabilir.

> [!WARNING]
> Dışlamaların tanımlanması, Linux'ta Uç Nokta için Defender'ın sunduğu korumayı düşürmektedir. Dışlamaları uygulamayla ilişkili riskleri her zaman değerlendirmeli ve yalnızca kötü amaçlı olmadığınız dosyaları hariç tutabilirsiniz.

## <a name="supported-exclusion-types"></a>Desteklenen dışlama türleri

Aşağıdaki tablo Linux'ta Uç Nokta için Defender tarafından desteklenen dışlama türlerini gösterir.

Dışlama|Tanım|Örnekler
---|---|---
Dosya uzantısı|Uzantılı tüm dosyalar, cihazın herhangi bir yerinde|`.test`
Dosya|Tam yoldan tanımlanan belirli bir dosya|`/var/log/test.log`<br/>`/var/log/*.log`<br/>`/var/log/install.?.log`
Klasör|Belirtilen klasörün altındaki tüm dosyalar (tekrarlı bir şekilde)|`/var/log/`<br/>`/var/*/`
İşlem|Belirli bir işlem (tam yol veya dosya adı ile belirtilen işlem) ve bu dosya tarafından açılan tüm dosyalar|`/bin/cat`<br/>`cat`<br/>`c?t`

> [!IMPORTANT]
> Başarıyla dışlamak için yukarıdaki yollar sembolik bağlantı değil, sabit bağlantılar olmalı. 'i çalıştırarak yolun sembolik bir bağlantı olup olduğunu kontrol edin `file <path-name>`.

Dosya, klasör ve süreç dışlamaları aşağıdaki joker karakterleri destekler:

Joker karakter|Açıklama|Örnek|Eşleşmeler|Eşmser değil
---|---|---|---|---
\*|Hiçbiri dahil herhangi bir sayıda karakterle eşler (bu joker karakterin yol içinde kullanılırken tek bir klasörün yerini alamayacaktır)|`/var/\*/\*.log`|`/var/log/system.log`|`/var/log/nested/system.log`
?|Herhangi bir tek karakterle eşler|`file?.log`|`file1.log`<br/>`file2.log`|`file123.log`

## <a name="how-to-configure-the-list-of-exclusions"></a>Dışlama listesi nasıl yapılandırılır

### <a name="from-the-management-console"></a>Yönetim konsolundan

Suze, Ansible veya başka bir yönetim konsolundan dışlamaları yapılandırma hakkında daha fazla bilgi için [bkz. Linux'ta Uç Nokta için Defender tercihlerini ayarlama](linux-preferences.md).

### <a name="from-the-command-line"></a>Komut satırından

Dışlamaları yönetmek için kullanılabilir anahtarları görmek için aşağıdaki komutu çalıştırın:

```bash
mdatp exclusion
```

> [!TIP]
> Dışlamaları joker karakterlerle yapılandırırken, uzak verinin önüne geçmek için parametreyi çift tırnak içine alın.

Örnekler:

- Dosya uzantısı için dışlama ekleme:

    ```bash
    mdatp exclusion extension add --name .txt
    ```

    ```Output
    Extension exclusion configured successfully
    ```

- Dosya için dışlama ekleme:

    ```bash
    mdatp exclusion file add --path /var/log/dummy.log
    ```

    ```Output
    File exclusion configured successfully
    ```

- Klasör için dışlama ekleme:

    ```bash
    mdatp exclusion folder add --path /var/log/
    ```

    ```Output
    Folder exclusion configured successfully
    ```

- İkinci klasör için dışlama ekleme:

    ```bash
    mdatp exclusion folder add --path /var/log/
    mdatp exclusion folder add --path /other/folder
    ```

    ```Output
    Folder exclusion configured successfully
    ```

- Joker karakter içeren bir klasör için dışlama ekleme:

    ```bash
    mdatp exclusion folder add --path "/var/*/"
    ```

    > [!NOTE]
    > Bu, */var/* altında yalnızca bir düzey altındaki yolları hariç tutsa da, daha derin iç içe olan klasörleri hariç tutmayacak; örneğin, */var/this-subfolder/but-not-this-subfolder*.

    ```bash
    mdatp exclusion folder add --path "/var/"
    ```

    > [!NOTE]
    > Bu, üst öğesi */var/ olan tüm yolları hariç tutacak*; örneğin, */var/this-subfolder/and-this-subfolder-as-well*.

    ```Output
    Folder exclusion configured successfully
    ```

- bir işlem için dışlama ekleme:

    ```bash
    mdatp exclusion process add --name cat
    ```

    ```Output
    Process exclusion configured successfully
    ```

- İkinci işlem için dışlama ekleme:

    ```bash
    mdatp exclusion process add --name cat
    mdatp exclusion process add --name dog
    ```

    ```Output
    Process exclusion configured successfully
    ```

## <a name="validate-exclusions-lists-with-the-eicar-test-file"></a>EICAR test dosyasıyla dışlama listelerini doğrulama

Test dosyasını indirmek için kullanarak dışlama listenizin `curl` çalıştığını doğruabilirsiniz.

Aşağıdaki Bash parçacığında, dışlama `test.txt` kurallarınıza uygun bir dosyayla değiştirin. Örneğin, uzantıyı dışladıysanız `.testing` ile değiştirin `test.txt` `test.testing`. Bir yolu test ediyorsanız, komutu bu yol içinde çalıştırmayı sağlar.

```bash
curl -o test.txt https://www.eicar.org/download/eicar.com.txt
```

Linux'ta Uç Nokta için Defender kötü amaçlı yazılım raporlarsa kural çalışmıyordur. Kötü amaçlı yazılım raporu yoksa ve indirilen dosya varsa, dışlama çalışıyor olur. İçeriğin [EICAR test](http://2016.eicar.org/86-0-Intended-use.html) dosyası web sitesinde açıklananla aynı olduğunu onaylamak için dosyayı açabilirsiniz.

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
