---
title: Yapılandırılabilir eşleşmeyi kullanmak için Tam Veri Eşleşme şemasını değiştirme
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Yapılandırılabilir eşleşmeyi kullanmak için bir edm şemasını değiştirmeyi öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: cf11e60f3fce46926d297c97a44c7d494942d556
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2022
ms.locfileid: "63010061"
---
# <a name="modify-exact-data-match-schema-to-use-configurable-match"></a>Yapılandırılabilir eşleşmeyi kullanmak için Tam Veri Eşleşme şemasını değiştirme

Tam Veri Eşleşmesi (EDM) tabanlı sınıflandırma, hassas bilgiler veritabanındaki değerlere başvuran özel hassas bilgi türleri oluşturmanıza olanak sağlar. Tam dize çeşitlemelerine izin vermeniz gereken durumlarda, yapılandırılabilir eşleşmeyi kullanarak  büyük/küçük Microsoft 365 yoksaymalarını söyleyin.

> [!IMPORTANT]
> Var olan bir EDM şemasını ve veri dosyasını değiştirmek için bu yordamı kullanın.

1. EDM **EdmUploadAgent.exe** ve veri dosyası karşıya yükleme amacıyla Microsoft 365 bilgisayarınızdan o şemayı kaldırın.

2. Aşağıdaki bağlantıları **EdmUploadAgent.exe** aboneliğiniz için uygun dosya dosyasını indirin:
    - [Ticari + GCC](https://go.microsoft.com/fwlink/?linkid=2088639) - çoğu ticari müşteri bunu kullan
    - [GCC-Yüksek](https://go.microsoft.com/fwlink/?linkid=2137521) - Bu, özel olarak yüksek güvenlikli devlet bulut aboneleri için
    - [DoD](https://go.microsoft.com/fwlink/?linkid=2137807) - Bu özel olarak AMERIKA Birleşik Devletleri Savunma bulut müşterileri için

3. EDM Hizmet Upload yetkilendinin, bir Komut İstemi penceresi açın (yönetici olarak) ve aşağıdaki komutu çalıştırın:

   ```dos
   EdmUploadAgent.exe /Authorize
   ```

4. Var olan şemanın geçerli bir kopyasına sahip değilsanız, var olan şemanın bir kopyasını indirmeniz gerekir, şu komutu çalıştırın:

   ```dos
   EdmUploadAgent.exe /SaveSchema /DataStoreName <dataStoreName> [/OutputDir [Output dir location]]
   ```

5. Şemayı özelleştirin, böylece her sütun "caseInsensitive" ve / veya "ignoredDelimiters" kullanır.  "büyük/büyük/harfe duyarlı" için varsayılan değer "yanlış" ve "yok sayılanDelimiters" için de boş bir dizedir.

    > [!NOTE]
    > Genel kayıt düzeni desenini algılamak için kullanılan temeldeki özel duyarlı bilgi türü veya yerleşik hassas bilgi türü, yok sayılanDelimiters ile listelenen çeşitlemelerin algılanmasında desteklemelidir. Örneğin, YERLEŞIK ABD sosyal güvenlik numarası (SSN) hassas bilgi türü, verilerde tireler, boşluklar veya SSN'i tamamlayan gruplu sayılar arasındaki boşluklar içeren değişimleri algılanabilir. Sonuç olarak, SSN verileri için EDM'nin yok sayılan Sınırlayıcıları yalnızca kısa çizgi ve boşluktan elde edilebilir.

    Burada, hassas verilerde büyük/küçük harf çeşitlemelerini tanımak için gereken fazladan sütunlar oluşturarak büyük/küçük harfe duyarlı değil eşleşmenin benzetimini eden bir örnek şema ve almaktadırsınız.

    ```xml
    <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
      <DataStore name="PatientRecords" description="Schema for patient records policy" version="1">
               <Field name="PolicyNumber" searchable="true" />
               <Field name="PolicyNumberLowerCase" searchable="true" />
               <Field name="PolicyNumberUpperCase" searchable="true" />
               <Field name="PolicyNumberCapitalLetters" searchable="true" />
      </DataStore>
    </EdmSchema>
    ```

    Yukarıdaki örnekte, hem özgün sütunun çeşitlemelerine `PolicyNumber` hem de `caseInsensitive` her ikisi de ekleniyorsa bunlar `ignoredDelimiters` gerekli olmaz.

    Bu şemayı, EDM'nin yapılandırılabilir eşleşmeleri kullandığı şekilde güncelleştirmek için ve bayrakları `caseInsensitive` `ignoredDelimiters` kullanın.  Bu şöyle görünüyor:

    ```xml
    <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
      <DataStore name="PatientRecords" description="Schema for patient records policy" version="1">
             <Field name="PolicyNumber" searchable="true" caseInsensitive="true" ignoredDelimiters="-,/,*,#,^" />
      </DataStore>
    </EdmSchema>
    ```

    Bayrak `ignoredDelimiters` , alfasayısal olmayan karakterleri destekler. İşte birkaç örnek:
    - \.
    - \-
    - \/
    - \_
    - \*
    - \^
    - \#
    - \!
    - \?
    - \[
    - \]
    - \{
    - \}
    - \\
    - \~
    - \;

    Bayrak `ignoredDelimiters` şunları desteklemez:
    - 0-9 karakterleri
    - A-Z
    - a-z
    - \"
    - \,

6. [Bağlan ve Uyumluluk & PowerShell'e.](/powershell/exchange/connect-to-scc-powershell)

    > [!NOTE]
    > If your organization has set set [up Customer Key for Microsoft 365 at the tenant level (public preview), Exact data match](customer-key-tenant-level.md#overview-of-customer-key-for-microsoft-365-at-the-tenant-level-public-preview) will make use of its encryption functionality automatically. Bu yalnızca Ticari buluttaki E5 lisanslı kiracılar için kullanılabilir.

7. Aşağıdaki komutu çalıştırarak şemanızı güncelleştirin:

   ```powershell
   Set-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
   ```

8. Gerekirse, veri dosyasını yeni şema sürümüyle eş olacak şekilde güncelleştirin.

    > [!TIP]
    > İsteğe bağlı olarak, şunları çalıştırarak karşıya yüklemeden önce csv dosyanız üzerinde doğrulama çalıştırabilirsiniz:
    >
    > `EdmUploadAgent.exe /ValidateData /DataFile [data file] [schema file]`
    >
    > Desteklenen tüm parametreler hakkında daha EdmUploadAgent.exe için
    >
    > `EdmUploadAgent.exe /?`

9. Komut İstemi penceresini açın (yönetici olarak) ve hassas verilerinizi karma yapmak ve karşıya yüklemek için aşağıdaki komutu çalıştırın:

   ```dos
   EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Salt [custom salt] /Schema [Schema file]
   ```

## <a name="related-articles"></a>İlgili makaleler

- [Hassas bilgi türlerine dayalı tam veri eşleşmesi hakkında bilgi](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Hassas bilgi tür-varlık tanımları](sensitive-information-type-entity-definitions.md)
- [Özel hassas bilgi türleri](./sensitive-information-type-learn-about.md)
- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
- [Bulut Uygulamaları için Microsoft Defender](/cloud-app-security)
- [New-DlpEdmSchema](/powershell/module/exchange/new-dlpedmschema)
