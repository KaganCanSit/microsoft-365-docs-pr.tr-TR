---
title: Tam veri eşleşmesi hassas bilgi türünü test etme
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
ms.openlocfilehash: 5b2ae7e5d6e434cd5502373b04a055c6fb2fb4a9
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754244"
---
# <a name="test-an-exact-data-match-sensitive-information-type"></a>Tam veri eşleşmesi hassas bilgi türünü test etme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Tam veri eşleştirme (EDM) hassas bilgi türünüz (SIT) oluşturulduktan ve hassas bilgi tablonuzun karşıya yükleme ve dizin oluşturmayı tamamlandığını doğruladıktan bir saat sonra, Uyumluluk merkezindeki hassas bilgi türleri bölümündeki test işlevini kullanarak algılamak istediğiniz bilgileri algılayıp algılamadığını test edebilirsiniz.
 
>[! NOT:] Önceden oluşturulmuş bir EDM SIT'teki değişikliklerin sisteme yayılması biraz zaman alabilir. Algılama sorunlarını gidermek için EDM hassas bilgi türünde değişiklikler yapıyorsanız, etkilerini doğrulamak için test işlevini kullanmadan önce bu değişiklikleri yaptıktan sonra en az bir saat beklemeyi unutmayın.

## <a name="test-your-edm-sit-in-the-compliance-center"></a>Uyumluluk Merkezi'nde EDM SIT'inizi test edin

1. **Uyumluluk merkezi** > **Veri sınıflandırması** > **Hassas Bilgi Türlerini** açın.

2. Listeden EDM SIT'inizi seçin ve ardından açılır bölmede **Test'i** seçin. Bu seçenek yalnızca hassas bilgi türleri altında bulunur.
 
3. Algılamak istediğiniz verileri içeren bir öğeyi Upload. Örneğin, hassas bilgi tablonuzdaki satırların bir alt kümesini içeren bir öğe oluşturun. Şemanızda yoksayılan sınırlayıcıları tanımlamak için yapılandırılabilir eşleştirme özelliğini kullandıysanız, öğenin bu sınırlayıcılarla ve sınırlayıcılar olmadan örnekler içerdiğinden emin olun.

4. Dosya karşıya yüklenip tarandıktan sonra EDM SIT'inizle eşleşme olup olmadığını denetleyin.

5. SIT'teki **Test** işlevi bir eşleşme algılarsa, kırpmadığını veya yanlış ayıklamadığını doğrulayın. Örneğin, algılaması gereken tam dizenin yalnızca bir alt dizesini ayıklayarak ya da çok sözcüklü bir dizede yalnızca ilk sözcüğü alarak ya da ayıklamaya fazladan simgeler veya karakterler ekleyerek. [Normal ifade dili başvurusu için bkz. Normal İfade Dili - Hızlı Başvuru](/dotnet/standard/base-types/regular-expression-language-quick-reference). 

5. Alternatif olarak, aşağıdaki PowerShell cmdlet'ini kullanabilirsiniz:

```powershell
Test-DataClassification  -ClassificationNames “[Your EDM sensitive info type]” -TexttoClassify “[your own text to scan for matches]” 
```

> [!NOTE]
 EDM hassas bilgi türünü veya EDM türünün temel aldığı birincil SIT türünü oluşturduğunuzda veya düzenlediğinizde, YENI tanımlarla eşleşen metinler için SID'lerde yapılan değişikliklerden sonra değiştirilen tüm yeni içerik ve içerik gezinilir, ancak önceden var olan içerik, değiştirilene veya yeniden dizine alınana kadar gezinmez. 

bir SharePoint sitesinde veya kitaplığında veya OneDrive mevcut içeriğin yeniden gezinmesini zorlamak için, [Sitenin, kitaplığın veya listenin el ile gezinmesini ve yeniden dizine alınmasını isteme](/sharepoint/crawl-site-content) başlığı altında yer alan yönergeleri izleyin.

## <a name="test-your-edm-sit-with-information-protection-policies"></a>Bilgi koruma ilkeleriyle EDM SIT'inizi test edin

İlkelerde kullanarak EDM SIT'inizin nerede kullanıldığını ve üretimde ne kadar doğru olduğunu görebilirsiniz:

1. [Otomatik etiketleme ilkesi](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) oluşturun ve **Benzetimi genel bakış** bölümünde çalıştırın.

1. EDM SIT'i tetikleyecek bazı içerikler ve ilkenizin izlediği bir konuma EDM SIT'i tetiklemeyecek bazı içerikler ekleyin.

1. Eşleşmeleri denetlemek **için Gözden geçirecek öğeler** sekmesini açın.

1. İlkelerinizi uygun şekilde ayarlayın. 

Test ve ayarlama sonuçlarınızdan memnun olduğunuzda, EDM tabanlı özel SIT'iniz bilgi koruma ilkelerinde kullanıma hazırdır, örneğin:

- [DLP ilkeleri](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
- [Otomatik etiketleme ilkeleri](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Bulut Uygulamaları için Microsoft Defender](/cloud-app-security/data-protection-policies)

## <a name="troubleshooting-tips"></a>Sorun giderme ipuçları

Eşleşme bulamazsanız bazı sorun giderme ipuçlarını burada bulabilirsiniz.

|Sorun  |Sorun giderme ipucu  |
|---------|---------|
|Eşleşme bulunamadı     |  Karma bölümünde açıklanan komutları kullanarak hassas verilerinizin doğru şekilde karşıya yüklendiğini onaylayın [ve hassas bilgi türleriyle tam olarak eşleşen veriler için hassas bilgi kaynağı tablosunu karşıya yükleyin](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)|
|Eşleşme bulunamadı   | Desenlerinizin her birinde birincil öğeyi yapılandırırken kullandığınız SIT'i test edin. Bu, SIT'in öğedeki örneklerle eşleşebildiğinden emin olur. EDM Hassas bilgi türünün sınıflandırma öğesi olarak yanlış tanımlanmış bir SIT kullanmak, EDM'deki algılama hatalarının en yaygın nedenidir.         |
|EDM türündeki bir birincil öğe için seçtiğiniz SIT öğede eşleşme bulmuyor veya beklediğinizden daha az eşleşme buluyor    |  İçerikteki ayırıcıları ve sınırlayıcıları destekleyip desteklemediğini denetleyin. Şemanızda tanımlanan yoksayılan sınırlayıcıları eklediğinizden emin olun.       |
|Sit birincil öğesi bir öğedeki eşleşmeleri bulur, ancak EDM SIT'i bulmaz.     | - /s gibi bir yakalama boşluk sınırlayıcısı başlatmak veya sonlandırmak için REGEX deyimlerinizi denetleyin. Boşluk, veri tablosundaki karma değerle eşleşmez. Bunun yerine /b gibi bir sözcük sınırlayıcısı kullanın. </br> - Yalnızca bir alt dizeyi değil, yakalamak istediğiniz tüm dizeyi yakaladıklarından emin olmak için REGEX deyimlerinizi denetleyin. Örneğin, e-posta adresleri için bu desen [a-zA-Z]{30}@[a-zA-Z]{20}.[ a-zA-Z]{2,3} *user@contoso.com* ve *user@contoso.co.jp* eşleşecektir.  |
|Birincil öğeleri olan ve hiçbir ikincil öğe tanımlanmayan bir EDM SIT öğeleri algılar, ancak birincil ve ikincil öğeler gerektiğinde beklenenden daha az öğe algılar veya algılamaz.  | İkincil kanıt değerlerinin boşluk içermeyen veya çok sözcüklü dizeleri algılayan REGEX deyimlerini kullanan tek bir sözcük veya dizeden oluştuğundan emin olun. Örneğin, \b[A-Z][a-z]{1,25}([ -][A-Z][a-z]{1,25}){0,4}\b, büyük harf karakterle başlayan ardışık bir ile beş sözcük arasında herhangi bir diziyle eşleşir. EDM hassas bilgi türü XML'nizdeki ek kanıt koşulları için sınıflandırma öğesi olarak bu SIT'i kullanın. Bkz. [El ile kural paketi oluşturma](sit-get-started-exact-data-match-create-rule-package.md#create-a-rule-package-manually)|
|SIT test işlevi hiçbir eşleşme algılamaz.   | Seçtiğiniz SIT'in ek anahtar sözcükler veya diğer doğrulamalar için gereksinimler içerip içermediğini denetleyin. Yerleşik SID'ler için, her türü eşleştirmek için en düşük gereksinimlerin ne olduğunu doğrulamak için [bkz. Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) .        |
|Test işlevi çalışır, ancak SharePoint veya OneDrive öğeleriniz DLP veya otomatik etiketleme kurallarında algılanmaz     | Eşleşmesini beklediğiniz belgelerin İçerik Gezgini'nde gösterilip gösterilmediğini denetleyin. Bunlar orada değilse, yalnızca hassas bilgi türündeki değişikliklerden sonra oluşturulan içeriğin eşleşme olarak gösterileceğini unutmayın. Önceden var olan öğelerin gösterilmesi için siteleri ve kitaplıkları yeniden taramanız gerekir. SharePoint ve OneDrive yeniden gezinme ayrıntıları için bkz. [Sitenin, kitaplığın veya listenin el ile gezinmesini ve yeniden dizine alınmasını isteme](/sharepoint/crawl-site-content).        |
|Birden çok eşleşme gerektiren DLP veya otomatik etiketleme kuralları tetiklemez     |Hem EDM türünüz hem de temel hassas bilgi türleri için yakınlık gereksinimlerinin karşılanıp karşılanmadığını denetleyin. Örneğin, birincil öğe ile destekleyici anahtar sözcükler arasındaki uzaklık üst sınırı 300 karakterse, ancak anahtar sözcükler yalnızca uzun bir tablonun ilk satırında yer alıyorsa, yalnızca eşleşen değerlerin yalnızca ilk birkaç satırı yakınlık gereksinimlerini karşılayabilir. SIT tanımlarınızı daha rahat yakınlık kurallarını destekleyecek şekilde değiştirin veya ek kanıt koşulları için belgedeki herhangi bir yeri kullanın.         |
|EDM türünün algılanması tutarsız veya dengesiz     |EDM türünüzün birincil öğesi için temel olarak kullandığınız hassas bilgi türünün gereksiz içeriği algılamadığını denetleyin. Herhangi bir sözcük, herhangi bir sayı veya tüm e-posta adresleri gibi çok fazla ilgisiz içerikle eşleşen bir SIT kullanmak, hizmetin ilgili eşleşmeleri doymasına ve yoksaymasına neden olabilir. İçerik gezginindeki birincil öğeleriniz için kullandığınız hassas türle eşleşen içerik parçalarının sayısını denetleyin. </br> SIT'in çok fazla içerikle eşleşip eşleşmediğini tahmin etmek için: </br> - İçerik Gezgini'ndeki içerik öğelerinin sayısını, hassas türün oluşturulmasından bu yanaki gün sayısına böler. </br> - Günlük eşleşme sayısı yüz binlerce veya milyon aralığındaysa birincil SIT'in çok geniş olması mümkündür. Öneriler ve EDM türü için doğru hassas bilgi türünü seçmeye yönelik en iyi yöntemler için bkz. [Tam veri eşleşmesi tabanlı hassas bilgi türleri hakkında bilgi edinin](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) .         |
