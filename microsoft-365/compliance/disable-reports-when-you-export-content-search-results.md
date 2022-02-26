---
title: İçerik Arama sonuçlarını dışarı aktararak raporları devre dışı bırakma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 12/30/2016
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: c9b0ff0c-282b-4a44-b43f-cfc5b96557f9
ms.custom:
- seo-marvel-apr2020
description: İçerik Windows sonuçlarını dışarı aktararak raporları devre dışı bırakmak için yerel bilgisayarınızda Microsoft 365 uyumluluk merkezi.
ms.openlocfilehash: bafdab1586b28239ddba7cf251704111731f2239
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973570"
---
# <a name="disable-reports-when-you-export-content-search-results"></a>İçerik Arama sonuçlarını dışarı aktararak raporları devre dışı bırakma

eBulma Dışarı Aktarma aracını kullanarak İçerik Arama'nın sonuçlarını Microsoft 365 uyumluluk merkezi, araç dışarı aktarıldı içeriği hakkında ek bilgi içeren iki raporu otomatik olarak oluşturur ve dışarı aktar eder. Bu raporlar, Results.csv dosyası ve Manifest.xml dosyasıdır (bu raporların ayrıntılı açıklamaları için bu konunun Dışarı [](#frequently-asked-questions-about-disabling-export-reports) aktarma raporlarını devre dışı bırakma hakkında sık sorulan sorular bölümüne bakın). Bu dosyalar çok büyük olmalarından, indirme sürelerini hızlandırarak ve bu dosyaların dışarı aktarmasını engelerek diskte yer tasarrufu sabilirsiniz. Arama sonuçlarını dışarı aktarmada Windows Defteri'ni değiştirerek bunu kullanabilirsiniz. Raporları daha sonra eklemek için kayıt defteri ayarını düzenleyebilirsiniz. 
  
## <a name="create-registry-settings-to-disable-the-export-reports"></a>Dışarı aktarma raporlarını devre dışı bırakmak için kayıt defteri ayarları oluşturma

İçerik arama sonuçlarını dışarı aktarmada kullanabileceğiniz bilgisayarda aşağıdaki yordamı gerçekleştirin.
  
1. Açıksa eBulma Dışarı Aktarma aracını kapatın.
    
2. Devre dışı bırakmak istediğiniz dışarı aktarma raporuna bağlı olarak, aşağıdaki adımlardan birini veya her ikisini de gerçekleştirin.
    
    - **Results.csv**
    
      Bir .reg dosya adı Windows kullanarak aşağıdaki metni bir kayıt defteri dosyasına kaydedin; örneğin, DisableResultsCsv.reg.
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultCsvEnabled /t REG_SZ /d False 
      ```

    - **Manifest.xml**
    
      Bir .reg dosya adı son Windows kullanarak aşağıdaki metni bir kayıt defteri dosyasına kaydedin; örneğin, DisableManifestXml.reg.
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultEdrmEnabled /t REG_SZ /d False 
      ```

3. Windows Gezgini'nde, önceki adımlarda oluşturduğunuz .reg dosyasına tıklayın veya çift tıklayın.
    
4. Kullanıcı Erişimi Denetimi penceresinde, Kayıt Defteri **Düzenleyicisi'nin değişikliği** yapmalarına izin vermeleri için Evet'e tıklayın. 
    
5. Devam etmek istendiğinde Evet'e **tıklayın**.
    
    Kayıt Defteri Düzenleyicisi, ayarın kayıt defterine başarıyla eklenmiştir iletisi görüntüler.
  
## <a name="edit-registry-settings-to-re-enable-the-export-reports"></a>Dışarı aktarma raporlarını yeniden etkinleştirmek için kayıt defteri ayarlarını düzenleme

Results.csv Manifest.xml.reg dosyalarını önceki yordamda oluşturarak raporları devre dışı bıraktıysanız, bu dosyaları düzenleyemez ve arama sonuçlarıyla birlikte dışarı aktarılacak şekilde raporu yeniden etkinleştirebilirsiniz. Bir kez daha, sonuçları içerik aramalarını dışarı aktarmada kullanabileceğiniz bilgisayarda aşağıdaki yordamı gerçekleştirin.
  
1. Açıksa eBulma Dışarı Aktarma aracını kapatın.
    
2. Önceki yordamda oluşturduğunuz .reg düzenleme dosyalarından birini veya her ikisini de düzenleyin.
    
    - **Results.csv**
    
        Not Defteri'da DisableResultsCsv.reg dosyasını açın, `False` `True`değeri ' olarak değiştirin ve dosyayı kaydedin. Örneğin, dosyayı düzenledikten sonra aşağıdaki gibi olur:
    
        ```text
        Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultCsvEnabled /t REG_SZ /d True
        ```

    - **Manifest.xml**
    
        Bu dosyada DisableManifestXml.reg Not Defteri açın, `False` `True`değeri ' olarak değiştirin ve dosyayı kaydedin. Örneğin, dosyayı düzenledikten sonra aşağıdaki gibi olur:
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultEdrmEnabled /t REG_SZ /d True
      ```

3. Windows Gezgini'nde, önceki adımda düzenleyttikleri .reg dosyasına tıklayın veya çift tıklayın.
    
4. Kullanıcı Erişimi Denetimi penceresinde, Kayıt Defteri **Düzenleyicisi'nin değişikliği** yapmalarına izin vermeleri için Evet'e tıklayın. 
    
5. Devam etmek istendiğinde Evet'e **tıklayın**.
    
    Kayıt Defteri Düzenleyicisi, ayarın kayıt defterine başarıyla eklenmiştir iletisi görüntüler.
  
## <a name="frequently-asked-questions-about-disabling-export-reports"></a>Dışarı aktarma raporlarını devre dışı bırakma hakkında sık sorulan sorular

 **En son Results.csv Manifest.xml nedir?**
  
Dosya Results.csv Manifest.xml dosyaları, dışarı aktarıldı olan içerik hakkında ek bilgiler içerir.
  
- **Results.csv** Bir Excel arama sonucu olarak indirilen her öğe hakkında bilgi içeren en iyi belge. E-posta için, sonuç günlüğü her ileti hakkında aşağıdaki bilgileri içerir: 
    
  - İletinin kaynak posta kutusunda bulunduğu konum (iletinin birincil posta kutusunda mı yoksa arşiv posta kutusunda mı bulunduğu da dahil).
    
  - İletinin gönderildiği veya alın aldığı tarih.
    
  - İletinin Konu satırı.
    
  - İletinin göndereni ve alıcıları.
    
  - Arama sonuçlarını dışarı aktarmada yinelemeyi de etkinleştirdiyseniz iletinin yinelenen ileti olup olmadığı. Yinelenen iletilerin Üst ÖğeKimlik **sütununda, iletiyi** yinelenen olarak tanımlayan bir değer olur. Üst **ÖğeKimlik** sütunundaki değer, dışarı aktarıldı iletinin **Item DocumentId** sütunundaki değerle aynıdır. 
    
    SharePoint OneDrive İş sitelerden alınan belgeler için, sonuç günlüğü her belge hakkında aşağıdaki bilgileri içerir:
    
  - Belgenin URL'si.
    
  - Belgenin bulunduğu site koleksiyonunun URL'si.
    
  - Belgenin son değiştirilma tarihi.
    
  - Belgenin adı (sonuç günlüğünde Konu sütununda yer alır).
    
- **Manifest.xml** Arama sonuçlarına dahil edilen her öğe hakkında bilgi içeren bir bildirim dosyası (XML biçiminde). Bu rapordeki bilgiler, elektronik bulma raporuyla Results.csv, ancak Elektronik Bulma Başvuru Modeli (EDRM) tarafından belirtilen biçimdedir. EDRM hakkında daha fazla bilgi için, gidin [https://www.edrm.net](https://www.edrm.net).
    
 **Bu raporları dışarı aktarmayı ne zaman devre dışı bırakmam gerekir?**
  
Bu sizin özel ihtiyaçlarınıza bağlıdır. Birçok kuruluş arama sonuçları hakkında ek bilgi gerektirmez ve bu raporlara ihtiyaç gerektirmez.
  
 **Bunu hangi bilgisayarda yapmak istiyorum?**
  
 eBulma Dışarı Aktarma aracını çalıştırdınız herhangi bir yerel bilgisayarda kayıt defteri ayarını değiştirebilirsiniz. 
  
 **Bu ayarı değiştirdikten sonra bilgisayarı yeniden başlatmam gerekir mi?**
  
Hayır, bilgisayarı yeniden başlatmanız zorunda değil. Ancak eBulma Dışarı Aktarma aracı çalışıyorsa, kayıt defteri ayarını değiştirdikten sonra aracı kapatıp yeniden başlatmanız gerekir.
  
 **Var olan bir kayıt defteri anahtarı düzen mi yoksa yeni bir anahtar mı oluşturulur?**
  
Bu konudaki yordamda oluşturduğunuz .reg dosyasını ilk kez çalıştıracak yeni bir kayıt defteri anahtarı oluşturulur. Daha sonra, .reg düzenleme dosyasını her değiştirseniz ve yeniden çalıştırsanız bu ayar düzenlenmiş olur.
