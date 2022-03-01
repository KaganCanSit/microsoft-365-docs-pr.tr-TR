---
title: Test paketi yönergeleri
description: Test paketiyle ilgili yönergeleri gözden geçirme
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 02/04/2022
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 0b5e69a245b21f4f6985eb54ca865b602059cba8
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2022
ms.locfileid: "63016598"
---
# <a name="test-package-guidelines"></a>Test paketi yönergeleri

## <a name="1-script-referencing"></a>1. Komut dosyası başvuru

Portala bir .zip dosya karşıya yüklerken, bu dosyanın tüm içeriğinin sıkıştırması bir kök klasörüne açılır. Bu ilk sıkıştırmayı açmak için herhangi bir kod yazmanız gerek değildir. Ayrıca, karşıya yüklenen zip dosyasına .zip yolu kullanarak dosya içindeki herhangi bir dosyaya başvurabilirsiniz.

Aşağıdaki örnekte, Görevler sekmesindeki giriş alanından ikili dosyalarınıza/betiklerinize nasıl başvurabilirsiniz? gösterilmiştir. Mavi renk metin, Tırnak işaretleri olmadan **Betik yolu** **alanına girilir.**

Zip dosyanızı karşıya yüklemeden önce içeriğinin farkında olmak önemlidir. Çoğunlukla klasörü sıkıştırırsanız, yerel makineniz zip dosyasının altında bir ana klasör oluşturur. Bu durumda, başvuru aşağıda kalın yazıyla **gösterildiği gibi** gösterilir:

**Contoso_App_Folder.zip**:

```console
├── Contoso_App_Folder

│   ├── file1.exe

│   ├── ScriptX.ps1

│   ├── folder1

│      ├── file3.exe

│      ├── script.ps1
```

- ScriptX.ps1 - **"Contoso_App_Folder/ScriptX.ps1"**
- Script.ps1 - **"Contoso_App_Folder/klasör1/script.ps1"**

Diğer zamanlarda, zip dosyanız dosyalarınız veya içeriğiniz hemen altında olabilir (örneğin, 2. düzey klasör yok):

**Zip_file_uploaded.zip**:

```console
├── file1.exe

├── ScriptX.ps1

├── folder1

│   ├── file3.exe

│   ├── script.ps1
```

- ScriptX.ps1 - **"ScriptX.ps1"**
- Script.ps1 - **"klasör1/script.ps1"**

## <a name="2-script-execution"></a>2. Betik yürütme

**Kutusu Dışında testleri:** Uygulama paketi en az üç PowerShell betik içermesi gerekir. Bu betikler katılımsız yükleme, başlatma ve kapatma için uygulama ve bağımlılıklarını yürütür. Her betik, kendi önkoşullarını denetlemeyi, kendi başarısını doğrulamayı ve (gerekirse) kendini temizlemeyi ele alır.

**İşlevsel testler:** Uygulama paketinde en az bir PowerShell betiği olması gerekir. Birden çok betik sağlanıyorsa, betikler karşıya yükleme sırasına göre çalıştırılıyor ve belirli bir betikte bir hata nedeniyle sonraki betikler yürütülebilir.

### <a name="script-requirements"></a>Komut dosyası gereksinimleri

- PowerShell Sürüm 5.1+
- Katılımsız yürütme
- Hata iade kodu
- Başarılı olduğunu doğrula
- Betikle ilgili günlük klasöründe günlüğe kaydetme

Test komut isteminde başarılı bir şekilde yürütül olması için, her betiğin katılımsız olarak çalışması gerekir (kullanıcı istemi yoktur).

> [!NOTE]
> Betikler, başarıyla tamamlanma için "0" ve yürütme sırasında herhangi bir hata oluşursa sıfırdan farklı bir hata kodu döndürür.

Her betik, başarılı bir şekilde çalıştır bu betiği doğrulamalı. Örneğin, yükleme betiği, yükleyici ikilisi yürütüldikten sonra sistem üzerinde belirli ikili dosyalar ve/veya kayıt defteri anahtarları olup olduğunu denetlemeli. Bu denetim, yüklemenin başarılı olduğundan emin olmak için makul bir güven sağlar.

Test çalıştırması sırasında hataların nerede olduğunu doğru şekilde tanılamak için doğrulama gereklidir. Örneğin, betik uygulamayı başarılı bir şekilde yükleyeyse ve başlatamıyorsa.

> [!IMPORTANT]
> **Aşağıdakilerin önüne geç:** Betikler, yeniden başlatma gerekirse lütfen betiklerinizi yükleme sırasında bunu belirtin.

## <a name="3-log-collection"></a>3. Günlük toplama

Her betik, kendi oluşturulan tüm günlüklerin çıkışında 'adlı bir klasöre gir yazarak bunların çıktısını alır `logs`. Dizin adı altında yer alan tüm `logs` klasörler kopyalanır ve sayfada indirilecek şekilde `Test Results` görüntülenir.

Örneğin, yükleme betiği ( **Uygulama/scripts/install** dizininde yer alıyor olabilir) günlüklerinin çıkışını şu şekilde alıyor olabilir: **logs/install.log**; örneğin, son günlük şöyle olur: **Uygulamalar/scripts/install/logs/install.log**

Sistem, dosyayı diğer klasörlerdeki `install.log` diğer dosyalarla birlikte `logs` alır ve indirmek için harmanlar.

## <a name="4-application-binaries"></a>4. Uygulama ikilileri

Tüm ikili dosyalar ve bağımlılıklar tek zip dosyasına ekli olmalı.

Bu ikili dosyalar, uygulamanın yüklenmesi için gereken her şeyi (örneğin, uygulama yükleyicisi) içerir. Uygulamanın .NET Core/Standard veya .NET Framework gibi tüm çerçevelere bağımlılığı varsa, bu çerçeveler dosyaya ekli olmalı ve sağlanan betiklerde doğru şekilde başvurlanmalıdır.

> [!NOTE]
> Karşıya yüklenen zip dosyasının adı boşluk veya özel karakter olamaz

## <a name="5-applicationtest-rules"></a>5. Uygulama/Test kuralları

Uygulama/testlerinin Test Temel altyapısı altında doğru çalışması için, Uygulama/Test kurallarında açıklanan kurallara [uymaları gerekir ](rules.md). 

## <a name="next-steps"></a>Sonraki adımlar

Bazı Sık Sorulan Soruları (SSS **) görüntülemek için sonraki makaleye ilerleyin**
> [!div class="nextstepaction"]
> [Sonraki adım](faq.md)
