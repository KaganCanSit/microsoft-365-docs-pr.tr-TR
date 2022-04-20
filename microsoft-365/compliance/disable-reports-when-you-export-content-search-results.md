---
title: İçerik Arama sonuçlarını dışarı aktarırken raporları devre dışı bırakma
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
description: Microsoft Purview uyumluluk portalından bir İçerik Aramasının sonuçlarını dışarı aktardığınızda raporları devre dışı bırakmak için yerel bilgisayarınızda Windows Kayıt Defteri'ni düzenleyin.
ms.openlocfilehash: d1b305f1d6ce0aba835d21695e59a4166ec96b7a
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64936829"
---
# <a name="disable-reports-when-you-export-content-search-results"></a>İçerik Arama sonuçlarını dışarı aktarırken raporları devre dışı bırakma

Microsoft Purview uyumluluk portalında bir İçerik Aramasının sonuçlarını dışarı aktarmak için eBulma Dışarı Aktarma aracını kullandığınızda, araç dışarı aktarılan içerik hakkında ek bilgi içeren iki raporu otomatik olarak oluşturur ve dışarı aktarır. Bu raporlar Results.csv dosyası ve Manifest.xml dosyasıdır (bu raporların ayrıntılı açıklamaları için bu konudaki [Dışarı aktarma raporlarını devre dışı bırakma hakkında sık sorulan sorular](#frequently-asked-questions-about-disabling-export-reports) bölümüne bakın). Bu dosyalar çok büyük olabileceğinden, indirme süresini hızlandırabilir ve bu dosyaların dışarı aktarılmasını engelleyerek disk alanından tasarruf edebilirsiniz. Bunu yapmak için, arama sonuçlarını dışarı aktarmak için kullandığınız bilgisayardaki Windows Kayıt Defteri'ni değiştirebilirsiniz. Raporları daha sonra eklemek isterseniz kayıt defteri ayarını düzenleyebilirsiniz. 
  
## <a name="create-registry-settings-to-disable-the-export-reports"></a>Dışarı aktarma raporlarını devre dışı bırakmak için kayıt defteri ayarları oluşturma

Sonuçları bir içerik aramasını dışarı aktarmak için kullanacağınız bilgisayarda aşağıdaki yordamı uygulayın.
  
1. Açıksa eBulma Dışarı Aktarma aracını kapatın.
    
2. Hangi dışarı aktarma raporunu devre dışı bırakmak istediğinize bağlı olarak aşağıdaki adımlardan birini veya her ikisini gerçekleştirin.
    
    - **Results.csv**
    
      Aşağıdaki metni bir .reg dosya adı soneki kullanarak bir Windows kayıt defteri dosyasına kaydedin; örneğin, DisableResultsCsv.reg.
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultCsvEnabled /t REG_SZ /d False 
      ```

    - **Manifest.xml**
    
      Aşağıdaki metni bir .reg dosya adı soneki kullanarak Windows kayıt defteri dosyasına kaydedin; örneğin, DisableManifestXml.reg.
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultEdrmEnabled /t REG_SZ /d False 
      ```

3. Windows Gezgini'nde, önceki adımlarda oluşturduğunuz .reg dosyasına tıklayın veya çift tıklayın.
    
4. Kullanıcı Access Control penceresinde, Kayıt Defteri Düzenleyicisi'nin değişikliği yapmasına izin vermek için **Evet'e** tıklayın. 
    
5. Devam etmek isteyip istemediğiniz sorulduğunda **Evet'e** tıklayın.
    
    Kayıt Defteri Düzenleyicisi, ayarın kayıt defterine başarıyla eklendiğini belirten bir ileti görüntüler.
  
## <a name="edit-registry-settings-to-re-enable-the-export-reports"></a>Dışarı aktarma raporlarını yeniden etkinleştirmek için kayıt defteri ayarlarını düzenleme

Önceki yordamda .reg dosyalarını oluşturarak Results.csv ve Manifest.xml raporları devre dışı bırakmışsanız, raporun arama sonuçlarıyla birlikte dışarı aktarılabilmesi için bu dosyaları yeniden etkinleştirebilirsiniz. Yine, sonuçları bir içerik aramasını dışarı aktarmak için kullanacağınız bilgisayarda aşağıdaki yordamı gerçekleştirin.
  
1. Açıksa eBulma Dışarı Aktarma aracını kapatın.
    
2. Önceki yordamda oluşturduğunuz .reg düzenleme dosyalarının birini veya ikisini birden düzenleyin.
    
    - **Results.csv**
    
        DisableResultsCsv.reg dosyasını Not Defteri açın, değerini `False` olarak `True`değiştirin ve dosyayı kaydedin. Örneğin, dosyayı düzenledikten sonra şöyle görünür:
    
        ```text
        Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultCsvEnabled /t REG_SZ /d True
        ```

    - **Manifest.xml**
    
        disableManifestXml.reg dosyasını Not Defteri açın, değerini `False` olarak `True`değiştirin ve dosyayı kaydedin. Örneğin, dosyayı düzenledikten sonra şöyle görünür:
    
      ```text
      Windows Registry Editor Version 5.00
      reg add HKLM\SOFTWARE\Microsoft\Exchange\Client\eDiscovery\ExportTool /v ResultEdrmEnabled /t REG_SZ /d True
      ```

3. Windows Gezgini'nde, önceki adımda düzenlediğiniz bir .reg dosyasına tıklayın veya çift tıklayın.
    
4. Kullanıcı Access Control penceresinde, Kayıt Defteri Düzenleyicisi'nin değişikliği yapmasına izin vermek için **Evet'e** tıklayın. 
    
5. Devam etmek isteyip istemediğiniz sorulduğunda **Evet'e** tıklayın.
    
    Kayıt Defteri Düzenleyicisi, ayarın kayıt defterine başarıyla eklendiğini belirten bir ileti görüntüler.
  
## <a name="frequently-asked-questions-about-disabling-export-reports"></a>Dışarı aktarma raporlarını devre dışı bırakma hakkında sık sorulan sorular

 **Results.csv ve Manifest.xml raporları nelerdir?**
  
Results.csv ve Manifest.xml dosyaları, dışarı aktarılan içerik hakkında ek bilgiler içerir.
  
- **Results.csv** Arama sonucu olarak indirilen her öğe hakkında bilgi içeren bir Excel belgesi. E-posta için, sonuç günlüğü her ileti hakkında aşağıdakiler dahil olmak üzere bilgiler içerir: 
    
  - İletinin kaynak posta kutusunda konumu (iletinin birincil posta kutusunda mı yoksa arşiv posta kutusunda mı olduğu dahil).
    
  - İletinin gönderildiği veya alındığı tarih.
    
  - İletideki Konu satırı.
    
  - İletinin göndereni ve alıcıları.
    
  - Arama sonuçlarını dışarı aktarırken yinelenenleri kaldırmayı etkinleştirdiyseniz iletinin yinelenen ileti olup olmadığı. Yinelenen iletiler **, Parent ItemId** sütununda iletiyi yinelenen olarak tanımlayan bir değere sahip olur. **Parent ItemId** sütunundaki değer, dışarı aktarılan iletinin **Item DocumentId** sütunundaki değerle aynıdır. 
    
    SharePoint ve OneDrive İş sitelerindeki belgeler için sonuç günlüğü, aşağıdakiler dahil olmak üzere her belge hakkında bilgi içerir:
    
  - Belgenin URL'si.
    
  - Belgenin bulunduğu site koleksiyonunun URL'si.
    
  - Belgenin son değiştirildiği tarih.
    
  - Belgenin adı (sonuç günlüğündeki Konu sütununda bulunur).
    
- **Manifest.xml** Arama sonuçlarına dahil edilen her öğe hakkında bilgi içeren bir bildirim dosyası (XML biçiminde). Bu rapordaki bilgiler Results.csv raporuyla aynıdır, ancak Elektronik Bulma Başvuru Modeli (EDRM) tarafından belirtilen biçimdedir. EDRM hakkında daha fazla bilgi için adresine [https://www.edrm.net](https://www.edrm.net)gidin.
    
 **Bu raporları dışarı aktarmayı ne zaman devre dışı bırakmalıyım?**
  
Bu, özel ihtiyaçlarınıza bağlıdır. Çoğu kuruluş arama sonuçları hakkında ek bilgi gerektirmez ve bu raporlara ihtiyaç duymaz.
  
 **Bunu hangi bilgisayarda yapmam gerekiyor?**
  
 eKeşif Dışarı Aktarma aracını çalıştırdığınız herhangi bir yerel bilgisayarda kayıt defteri ayarını değiştirmeniz gerekir. 
  
 **Bu ayarı değiştirdikten sonra bilgisayarı yeniden başlatmam gerekiyor mu?**
  
Hayır, bilgisayarı yeniden başlatmanız gerekmez. Ancak eBulma Dışarı Aktarma aracı çalışıyorsa, kayıt defteri ayarını değiştirdikten sonra aracı kapatıp yeniden başlatmanız gerekir.
  
 **Var olan bir kayıt defteri anahtarı düzenlenip düzenlenmiyor mu yoksa yeni bir anahtar mı oluşturuluyor?**
  
Bu konudaki yordamda oluşturduğunuz .reg dosyasını ilk kez çalıştırdığınızda yeni bir kayıt defteri anahtarı oluşturulur. Ardından ,reg düzenleme dosyasını her değiştirdiğinizde ve yeniden çalıştırdığınızda ayar düzenlenir.
