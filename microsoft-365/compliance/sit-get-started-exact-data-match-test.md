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
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: hizmetleri yapılandırma
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3030a97e3ed80524d2170e74b3d35f897b6ed74c
ms.sourcegitcommit: 8410a49995a084e4cc9b3f7286c8d506b7a85d79
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2021
ms.locfileid: "62999573"
---
# <a name="test-an-exact-data-match-sensitive-information-type"></a>Hassas bilgi türüyle tam olarak eşan bir veri sınaması

Tam veri eşleşmeniz (EDM) hassas bilgi türünüz (SIT) oluşturulduktan ve hassas bilgiler tablonizin karşıya yükleme ve dizin oluşturmanın bitmiş olduğunu doğrulayan bir saat sonra, Uyumluluk merkezi'nin hassas bilgi türleri bölümünde yer alan test işlevini kullanarak algılamak istediğiniz bilgileri algıla olduğunu test edin.
 
>[! NOT:] Önceden oluşturulmuş bir EDM SIT'daki değişikliklerin sistem genelinde yayılması biraz zaman alır. Algılama sorunlarını gidermek için EDM'ye duyarlı bir bilgi türünde değişiklik yapıyorsanız, etkisini doğrulamak için test işlevini kullanmadan önce bu değişikliklerin en az bir saat beklemesini bekleyin.

## <a name="test-your-edm-sit-in-the-compliance-center"></a>Uyumluluk Merkezi'nde EDM SIT'inizi test edin

1. Uyumluluk **merkezini** **açmaVeri** >  **sınıflandırmaSitive** >  Bilgi Türleri.

2. Listeden EDM SIT'inizi seçin ve sonra çıkış bölmesinde **Test'i** seçin. Bu seçenek yalnızca hassas bilgi türleri altındaki SIT için kullanılabilir.
 
3. Upload istediğiniz verileri içeren bir öğeyi seçin. Örneğin, hassas bilgiler tablodaki satırların bir alt kümesini içeren bir öğe oluşturun. Yoksayılan sınırlayıcıları tanımlamak için şemanıza yapılandırılabilir eşleşme özelliğini kullandıysanız, öğenin bu sınırlayıcılarla birlikte ve bu sınırlayıcılar olmadan da örneklere sahip olduğundan emin olun.

4. Dosya karşıya yüklendikten ve tarandikten sonra EDM SIT'iniz ile eşleşmeleri kontrol edin.

5. **SIT'daki Test** işlevi bir eşleşme algılarsa, kırpma olmadığını veya yanlış şekilde ayıklamayın. Örneğin, algılaması gereken tam dizenin yalnızca bir alt dizesini ayıklar veya çok sözcüklü dizedeki yalnızca ilk sözcüğü alır ya da ayıklamaya fazladan simgeler veya karakterler dahil eder. Normal [İfade Dili - Normal ifade dili başvurusu](/dotnet/standard/base-types/regular-expression-language-quick-reference) için Hızlı Başvuru'ya bakın. 

5. Alternatif olarak aşağıdaki PowerShell cmdlet'ini de kullanabilirsiniz:

```powershell
Test-DataClassification  -ClassificationNames “[Your EDM sensitive info type]” -TexttoClassify “[your own text to scan for matches]” 
```

> [!NOTE]
 EDM'ye duyarlı bir bilgi türü  oluşturma veya düzenleme ya da EDM türünü temel alan birincil SIT'i  oluşturmanız, SIT'lerde yapılan değişikliklerden sonra değiştirilen tüm yeni içerik ve içerikte yeni tanımlarla eşleşen metinlerde gezinilene kadar bu içerikte gezinilmese de, önceden varolan içerikte değişiklik yapılana veya yeniden bölüme alınana kadar gezinilmez. 

SharePoint sitesinde veya kitaplığında veya OneDrive'de var olan içerikte yeniden gezinmeyi zorlamak için, Site, kitaplık veya listede gezinme ve yeniden dizin oluşturma için el ile istekte bulunan yönergeleri [izleyin](/sharepoint/crawl-site-content).

## <a name="test-your-edm-sit-in-mip-policies"></a>EDM SIT'inizi MIP ilkeleri içinde test etmek

İlkelerde kullanarak EDM SIT'inizin nerede olduğunu ve üretimde ne kadar doğru olduğunu görebilirsiniz:

1. Otomatik etiketleme [ilkesi oluşturun ve Benzetim](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) genel bakış'ta **bu ilkeyi çalıştırın**.

1. EDM SIT'i tetikleyen bazı içerik ve EDM SIT'i tetiklemayacak bazı içerikleri ilkenizin izlemesi gereken bir konuma ekleyin.

1. Eşleşmeleri **gözden geçirmek için** Gözden geçirilen öğeler sekmesini açın.

1. İlkelerinizi uygun şekilde ayarlama. 

Test ve ayarlamanın sonuçlarından memnun olduktan sonra, EDM tabanlı özel SIT'iniz Bilgi Koruması ilkelerde kullanıma hazırdır. Örneğin:

- [DLP ilkeleri](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
- [Otomatik etiketleme ilkeleri](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Microsoft Cloud App Security ilkelerini yeniden tıklatın](/cloud-app-security/data-protection-policies)

## <a name="troubleshooting-tips"></a>Sorun giderme ipuçları

Herhangi bir eşleşme bulamazsanız, aşağıdakini deneyin:

- EDM aracını kullanarak hassas verilerinizi karşıya yükleme kılavuzunda açıklanan komutları kullanarak hassas verilerinizin doğru karşıya yük doğrulayın.

- Öğeye girdiğiniz örneklerin hassas bilgiler tablolarında yer olup olmadığını ve yoksayılan sınırlayıcıların doğru olup olmadığını denetleyin.

- Düzenlerin her birinde birincil öğeyi yapılandırken kullanılan SIT'i test etmek. Bu, SIT'in öğenin örnekle eşleneneyi onaylar. EDM'de hatalı tanımlanmış bir SIT'i EDM Hassas bilgi türünün sınıflandırma öğesi olarak kullanmak, EDM'de hataların en yaygın nedenidir. 

- EDM türü'nde birincil öğe için seçtiğiniz SIT öğesi öğede bir eşleşme bulamazsa veya beklendiğinden daha az eşleşme bulursa, içerikte yer alan ayırıcıları ve sınırlayıcıları desteklediğinden emin olun. Şemanıza, tanımlanmış yoksayılan sınırlayıcıları dahil etmek için bu sınırlayıcıları içermeye emin olun.

- Test işlevi hiçbir içerik algılamazsa, seçtiğiniz SIT'in başka anahtar sözcükler veya diğer doğrulamalar için gereksinimleri olup olmadığını kontrol edin. Yerleşik SITS'ler için [, her türü](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) eşleştirmek için en düşük gereksinimlerin neler olduğunu doğrulamak için bkz. Hassas bilgi türü varlık tanımları.

- Test işlevselliği çalışıyor ancak SharePoint veya OneDrive öğeleriniz DLP veya otomatik etiket kurallarında algılanmazsa, İçerik Gezgini'nde eşleşmeyi beklediğiniz belgelerin göster olup olmadığını kontrol edin. Orada yoklarsa, yalnızca hassas bilgi türüne yapılan değişikliklerden sonra oluşturulan içeriğin eşleşme olarak göster anımsayın. Önceden var olan öğelerin göstern diğer öğeler için sitelerde ve kitaplıklarda yeniden gezinmeniz gerekir. Site[, kitaplık](/sharepoint/crawl-site-content) veya listede gezinme ve yeniden dizin oluşturma hakkında ayrıntılı bilgi için bkz. Site, kitaplık veya listede gezinme SharePoint OneDrive. 

- Birden çok eşleşme gerektiren DLP veya otomatik etiket kuralları tetiklense, hem EDM türünüz hem de temel duyarlı bilgi türlerine ilişkin yakınlık gereksinimlerini karşılayın. Örneğin, birincil öğeyle desteklenen anahtar sözcükler arasındaki en uzun mesafe 300 karakterse, ancak anahtar sözcükler uzun bir tablonun yalnızca ilk satırına içeriyorsa, yakınlık gereksinimlerini karşılama olasılığı yalnızca ilk birkaç eşleşen değer satırıdır. Daha rahat yakınlık kurallarını desteklemek için SIT tanımlarınızı değiştirebilir veya ek kanıt koşulları için belgenin herhangi bir yerindeki seçeneği kullanabilirsiniz. 

- Bir EDM türünün algılanması tutarsız veya tutarsızsa, EDM türünüzdeki birincil öğe için temel olarak kullanılan hassas bilgi türünün gereksiz içerik algılanana kadar algılamayın. Herhangi bir sözcük, herhangi bir numara gibi çok fazla ilgisiz içerikle eşleşen bir SIT kullanmak, hizmetin uygun eşleşmeleri fazla doygunluğuna ve yoksaymalarına neden olabilir. İçerik Gezgini'nde, birincil öğeleriniz için birincil öğeleriniz için kullanılan hassas türle eşan içerik parçası sayısını kontrol edin. SIT'in çok fazla içerikle eş olup olduğunu tahmin etmek için:
    1. İçerik Gezgini'nde içerik öğelerinin sayısının hassas tür oluşturulduktan sonra gün sayısına bölünmesi.
    2. Günlük eşleşme sayısı yüz binlerce veya milyondan fazla aralıkta ise birincil SIT çok geniş olabilir. Bir EDM [türü için doğru hassas bilgi](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) türünü seçme konusunda öneriler ve en iyi yöntemler için bkz. Temel alınan hassas bilgi türleri hakkında tam veri eşleşmesi hakkında bilgi. 

- Karma'da açıklanan komutları kullanarak hassas verilerinizin doğru karşıya yük doğrulamak ve hassas bilgi türleriyle tam olarak eşleşmesi için hassas [bilgi kaynağı tabloyu karşıya yükleyin](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types).

- EDM türü'nde birincil öğe için seçtiğiniz SIT öğesi öğede bir eşleşme bulamazsa veya beklenenden daha az eşleşme bulursa, bu öğenin içerikte yer alan ayırıcıları ve sınırlayıcıları desteklediğinden emin olun. Şemanıza, tanımlanmış yoksayılan sınırlayıcıları dahil etmek için bu sınırlayıcıları içermeye emin olun. 

