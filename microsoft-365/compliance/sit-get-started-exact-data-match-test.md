---
title: Hassas bilgi türüyle tam olarak eşan bir veri sınaması
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: hizmetleri yapılandırma
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d0870cda205168e73d40adef7cdab333c7f0abdf
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679950"
---
# <a name="test-an-exact-data-match-sensitive-information-type"></a>Hassas bilgi türüyle tam olarak eşan bir veri sınaması

Tam veri eşleşmeniz (EDM) hassas bilgi türünüz (SIT) oluşturulduktan ve hassas bilgiler tablonizin karşıya yükleme ve dizin oluşturmanın bitmiş olduğunu doğrulayan bir saat sonra, Uyumluluk merkezi'nin hassas bilgi türleri bölümünde yer alan test işlevini kullanarak algılamak istediğiniz bilgileri algıla olduğunu test edin.
 
>[! NOT:] Önceden oluşturulmuş bir EDM SIT'daki değişikliklerin sistem genelinde yayılması biraz zaman alır. Algılama sorunlarını gidermek için EDM'ye duyarlı bir bilgi türünde değişiklik yapıyorsanız, etkisini doğrulamak için test işlevini kullanmadan önce bu değişikliklerin en az bir saat beklemesini bekleyin.

## <a name="test-your-edm-sit-in-the-compliance-center"></a>Uyumluluk Merkezi'nde EDM SIT'inizi test edin

1. Uyumluluk **merkezini** **açmaVeri** >  **sınıflandırmaSitive** >  Bilgi Türleri.

2. Listeden EDM SIT'inizi seçin ve sonra çıkış bölmesinde **Test'i** seçin. Bu seçenek yalnızca hassas bilgi türleri altında mevcuttur.
 
3. Upload istediğiniz verileri içeren bir öğeyi seçin. Örneğin, hassas bilgiler tablodaki satırların bir alt kümesini içeren bir öğe oluşturun. Yoksayılan sınırlayıcıları tanımlamak için şemanıza yapılandırılabilir eşleşme özelliğini kullandıysanız, öğenin bu sınırlayıcılarla birlikte ve bu sınırlayıcılar olmadan da örneklere sahip olduğundan emin olun.

4. Dosya karşıya yüklendikten ve tarandikten sonra EDM SIT'iniz ile eşleşmeleri kontrol edin.

5. SIT'daki **Test** işlevi bir eşleşme algılarsa, kırpma olmadığını veya yanlış şekilde ayıklamayın. Örneğin, algıması gereken tam dizenin yalnızca bir alt dizesini ayıklar veya çok sözcüklü dizedeki yalnızca ilk sözcüğü alır ya da ayıklamada fazladan simgeler veya karakterler içerebilir. Normal [İfade Dili - Normal ifade dili başvurusu](/dotnet/standard/base-types/regular-expression-language-quick-reference) için Hızlı Başvuru'ya bakın. 

5. Alternatif olarak aşağıdaki PowerShell cmdlet'ini de kullanabilirsiniz:

```powershell
Test-DataClassification  -ClassificationNames “[Your EDM sensitive info type]” -TexttoClassify “[your own text to scan for matches]” 
```

> [!NOTE]
 EDM'ye duyarlı bir bilgi türü  oluşturma veya düzenleme ya da EDM türünü temel alan birincil SIT'i  oluşturmanız, SIT'lerde yapılan değişikliklerden sonra değiştirilen tüm yeni içerik ve içerikte yeni tanımlarla eşleşen metinlerde gezinilene kadar bu içerikte gezinilmese de, önceden varolan içerikte değişiklik yapılana veya yeniden bölüme alınana kadar gezinilmez. 

SharePoint sitesinde veya kitaplığında veya OneDrive'de var olan içerikte yeniden gezinmeyi zorlamak için, Site, kitaplık veya listede gezinmeyi ve yeniden temlik etme isteğinde bulunan yönergeleri [izleyin](/sharepoint/crawl-site-content).

## <a name="test-your-edm-sit-in-mip-policies"></a>EDM SIT'inizi MIP ilkeleri içinde test etmek

İlkelerde kullanarak EDM SIT'inizin nerede olduğunu ve üretimde ne kadar doğru olduğunu görebilirsiniz:

1. Otomatik etiketleme [ilkesi oluşturun ve Benzetim](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) genel bakış'ta **bu ilkeyi çalıştırın**.

1. EDM SIT'i tetikleyen bazı içerik ve EDM SIT'i tetiklemayacak bazı içerikleri ilkenizin izlemesi gereken bir konuma ekleyin.

1. Eşleşmeleri **gözden geçirmek için** Gözden geçirilen öğeler sekmesini açın.

1. İlkelerinizi uygun şekilde ayarlama. 

Test ve ayarlamanın sonuçlarından memnun olduktan sonra, EDM tabanlı özel SIT'iniz Bilgi Koruması ilkelerde kullanıma hazırdır. Örneğin:

- [DLP ilkeleri](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
- [Otomatik etiketleme ilkeleri](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Bulut Uygulamaları için Microsoft Defender](/cloud-app-security/data-protection-policies)

## <a name="troubleshooting-tips"></a>Sorun giderme ipuçları

Herhangi bir eşleşme bulamazsanız, sorun giderme ipuçlarına bakın.


|Sorun  |Sorun giderme ipucu  |
|---------|---------|
|Eşleşme bulunamadı     |  Karma'da açıklanan komutları kullanarak hassas verilerinizin doğru karşıya yük doğrulamak ve hassas bilgi türleriyle tam olarak eşleşmesi için hassas bilgi [kaynağı tabloyu karşıya yükleyin](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)|
|Eşleşme bulunamadı   | Düzenlerin her birinde birincil öğeyi yapılandırken kullanılan SIT'i test etmek. Bu, SIT'in öğenin örnekle eşleneneyi onaylar. EDM'de hatalı tanımlanmış bir SIT'i EDM Hassas bilgi türünün sınıflandırma öğesi olarak kullanmak, EDM'de hataların en yaygın nedenidir.         |
|EDM türü'nde birincil öğe için seçtiğiniz SIT öğesi, öğede bir eşleşme bulamaz veya beklenenden daha az eşleşme bulur    |  İçeriğin içinde yer alan ayırıcıları ve sınırlayıcıları desteklediğini kontrol edin. Şemanıza, tanımlanmış yoksayılan sınırlayıcıları dahil etmek için bu sınırlayıcıları içermeye emin olun.       |
|Birincil öğe SIT öğesi öğede eşleşmeleri bulur ancak EDM SIT bulmaz.     | - REGEX ifadelerinizi, /s gibi bir yakalama beyaz alanı sınırlayıcısını başlatarak veya sonlandırmak için kontrol edin. Boşluk, veri tablosunda karma değerle eşleşmez. Bunun yerine, /b gibi bir sözcük sınırlayıcı kullanın. </br> - Yalnızca bir alt dizeyi değil, yakalamak istediğiniz tüm dizeyi yakalayan regEX deyimlerinizi kontrol edin. Örneğin, [a-zA-Z]@[a-zA-Z]{30}.[ e-posta adresleri için bu desen{20} a-zA-Z]{2,3} *user@contoso.com user@contoso.co.jp.*   |
|Birincil öğeleri olan ve tanımlı ikincil öğe olmayan bir EDM SIT öğeleri algılar, ancak birincil ve ikincil öğeler gerekli olduğunda beklenenden az olduğunda algılar veya algılar.  | İkincil kanıt değerlerinin boşluk içeremez tek bir sözcük veya dizeden veya çok sözcüklü dizeleri algılayan REGEX deyimlerini kullanarak top olduğundan emin olun. Örneğin, \b[A-Z][a-z]{1,25}([ -][A-Z][a-z]{1,25}){0,4}\b, büyük harfle baş eden bir ile beş art arda sözcük dizisinin eşleşmesini sağlar. EDM duyarlı bilgi türü XML'nizin ek kanıt koşulları için bu SIT'i sınıflandırma öğesi olarak kullanın. Bkz [. El ile kural paketi oluşturma](sit-get-started-exact-data-match-create-rule-package.md#create-a-rule-package-manually)|
|SIT sınama işlevi herhangi bir eşleşme algılamaz.   | Seçtiğiniz SIT'in ek anahtar sözcükler veya diğer doğrulamalar için gereksinimleri olup olduğunu kontrol edin. Yerleşik SITS'ler için [, her türü](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) eşleştirmek için en düşük gereksinimlerin neler olduğunu doğrulamak için bkz. Hassas bilgi türü varlık tanımları.        |
|Test işlevselliği çalışır ama SharePoint veya OneDrive öğeleriniz DLP'de veya otomatik etiket kurallarında algılanmaz     | İçerik Gezgini'nde eşleşmeyi beklediğiniz belgelerin göster olup denetleme. Orada yoksa, yalnızca hassas bilgi türüne yapılan değişikliklerden sonra oluşturulan içeriğin eşleşme olarak göster anımsayın. Önceden var olan öğelerin gösternsi için siteleri ve kitaplıkları yeniden çalışmanız gerekir. Site[, kitaplık veya diğer sitelerde](/sharepoint/crawl-site-content) gezinme ve yeniden temlik oluşturma hakkında ayrıntılı bilgi için bkz. Site, kitaplık veya SharePoint yeniden OneDrive.        |
|Birden çok eşleşme gerektiren DLP veya otomatik etiketleme kuralları tetikle     |Hem EDM türünüz hem de temel hassas bilgi türleri için yakınlık gereksinimlerinin karşılandıklerinden emin olun. Örneğin, birincil öğeyle desteklenen anahtar sözcükler arasındaki en uzun mesafe 300 karakterse, ancak anahtar sözcükler uzun bir tablonun yalnızca ilk satırına içeriyorsa, yakınlık gereksinimlerini karşılama olasılığı yalnızca ilk birkaç eşleşen değer satırıdır. Daha rahat yakınlık kurallarını desteklemek için SIT tanımlarınızı değiştirebilir veya ek kanıt koşulları için belgenin herhangi bir yerindeki seçeneği kullanabilirsiniz.         |
|EDM türünün algılanması tutarsız veya tutarsızdır     |EDM türünüzdeki birincil öğe için temel olarak kullanılan hassas bilgi türünün gereksiz içerik algılayana kadar algılanamay olup olmadığını kontrol edin. Herhangi bir sözcük, herhangi bir numara veya tüm e-posta adresi gibi çok fazla ilgisiz içerikle eşleşen bir SIT kullanmak, hizmetin uygun eşleşmeleri doygunluğuna ve yoksaymalarına neden olabilir. İçerik Gezgini'nde, birincil öğeleriniz için birincil öğeleriniz için kullanılan hassas türle eşan içerik parçası sayısını kontrol edin. </br> SIT'in çok fazla içerikle eş olup olduğunu tahmin etmek için: </br> - İçerik Gezgini'nde içerik öğelerinin sayısının hassas tür oluşturulduktan sonra gün sayısına bölünmesi. </br> - Günlük eşleşme sayısı yüz binlerce veya milyondan fazla aralıkta ise birincil SIT çok geniş olabilir. Bir EDM [türü için doğru hassas bilgi](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) türünü seçme konusunda öneriler ve en iyi yöntemler için bkz. Temel alınan hassas bilgi türleri hakkında tam veri eşleşmesi hakkında bilgi.         |