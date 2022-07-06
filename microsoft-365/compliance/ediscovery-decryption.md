---
title: eBulma'da şifre çözme
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Microsoft 365 eKeşif araçlarının e-posta iletilerine ekli ve SharePoint Online ile OneDrive İş depolanan şifrelenmiş belgeleri nasıl işlediği hakkında bilgi edinin.
ms.openlocfilehash: 689ac5420c3d9110a51586d8f008416363aafeec
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626325"
---
# <a name="decryption-in-microsoft-365-ediscovery-tools"></a>Microsoft 365 eBulma araçlarında şifre çözme

Şifreleme, dosya koruma ve bilgi koruma stratejinizin önemli bir parçasıdır. Her türden kuruluş, kuruluş içindeki hassas içeriği korumak ve yalnızca doğru kişilerin bu içeriğe erişmesini sağlamak için şifreleme teknolojisini kullanır.

Şifrelenmiş içerikte yaygın eBulma görevlerini yürütmek için, eBulma yöneticilerinin içerik aramalarından, Microsoft Purview eKeşif (Standart) durumlardan ve Microsoft Purview eKeşif (Premium) servis taleplerinden dışarı aktarıldığında e-posta iletisi içeriğinin şifresini çözmesi gerekiyordu. Microsoft şifreleme teknolojileriyle şifrelenen içerik dışarı aktarıldıktan sonra gözden geçirilemedi.

eBulma iş akışında şifrelenmiş içeriği yönetmeyi kolaylaştırmak için Microsoft 365 eKeşif araçları artık e-posta iletilerine eklenmiş ve Exchange Online gönderilen şifrelenmiş dosyaların şifre çözmesini birleştirir.<sup> 1</sup> Ayrıca, SharePoint Online ve OneDrive İş depolanan şifrelenmiş belgelerin şifresi eKeşif (Premium) içinde çözülür.

Bu yeni özellik öncesinde, yalnızca hak yönetimi (ekli dosyalar değil) tarafından korunan bir e-posta iletisinin içeriğinin şifresi çözülüyordu. SharePoint ve OneDrive'daki şifrelenmiş belgelerin şifresi eBulma iş akışı sırasında çözülemedi. Artık Microsoft şifreleme teknolojisiyle şifrelenen dosyalar bir SharePoint veya OneDrive hesabında bulunur ve arama sonuçları önizleme için hazırlandığında, eBulma(Premium) içinde bir gözden geçirme kümesine eklendiğinde ve dışarı aktarıldığında aranabilir ve şifresi çözülür. Ayrıca, SharePoint ve OneDrive'da e-posta iletisine eklenmiş şifrelenmiş belgeler aranabilir. Bu şifre çözme özelliği, eBulma yöneticilerinin arama sonuçlarının önizlemesini görüntülerken şifrelenmiş e-posta eklerinin ve site belgelerinin içeriğini görüntülemesine ve eBulma'da (Premium) bir gözden geçirme kümesine eklendikten sonra bunları gözden geçirmesine olanak tanır.

## <a name="supported-encryption-technologies"></a>Desteklenen şifreleme teknolojileri

Microsoft eKeşif araçları, Microsoft şifreleme teknolojileriyle şifrelenmiş öğeleri destekler. Bu teknolojiler Azure Rights Management ve Microsoft Purview Bilgi Koruması (özellikle duyarlılık etiketleri) teknolojileridir. Microsoft şifreleme teknolojileri hakkında daha fazla bilgi için bkz [. Şifreleme](encryption.md). Üçüncü taraf şifreleme teknolojileri tarafından şifrelenen içerik desteklenmez. Örneğin, Microsoft dışı teknolojilerle şifrelenmiş içeriklerin önizlemesini görüntüleme veya dışarı aktarma desteklenmez.

> [!NOTE]
> [Microsoft Purview İleti Şifrelemesi özel markalama şablonuyla](add-your-organization-brand-to-encrypted-messages.md) gönderilen e-posta iletilerinin şifre çözmesi Microsoft eKeşif araçları tarafından desteklenmez. OME özel markalama şablonu kullanılırken, e-posta iletileri alıcının posta kutusu yerine OME portalına teslim edilir. Bu nedenle, şifrelenmiş iletileri aramak için eBulma araçlarını kullanamazsınız çünkü bu iletiler alıcının posta kutusu tarafından hiçbir zaman alınmaz.

## <a name="ediscovery-activities-that-support-encrypted-items"></a>Şifrelenmiş öğeleri destekleyen eBulma etkinlikleri

Aşağıdaki tabloda, SharePoint ve OneDrive'da e-posta iletilerine ve şifrelenmiş belgelere eklenmiş şifrelenmiş dosyalar üzerinde Microsoft 365 eKeşif araçlarında gerçekleştirilebilecek desteklenen görevler tanımlanmaktadır. Bu desteklenen görevler, arama ölçütlerine uyan şifrelenmiş dosyalar üzerinde gerçekleştirilebilir. değeri `N/A` , işlevselliğin ilgili eBulma aracında kullanılamadiğini gösterir.

|eBulma görevi  |İçerik arama  |eKeşif (Standart)  |eKeşif (Premium)  |
|:---------|:---------|:---------|:---------|
|Sitelerde ve e-posta eklerinde şifrelenmiş dosyalarda içerik arama<sup>1</sup>     |Hayır      |Hayır      |Evet      |
|E-postaya eklenmiş şifrelenmiş dosyaların önizlemesini görüntüleme     |Evet      |Evet     |Evet       |
|SharePoint ve OneDrive'da şifrelenmiş belgelerin önizlemesini görüntüleme|Hayır      |Hayır    |Evet       |
|Bir gözden geçirme kümesindeki şifrelenmiş dosyaları gözden geçirme    |Yok      |Yok        | Evet        |
|E-postaya eklenmiş şifrelenmiş dosyaları dışarı aktarma    |Evet       |Evet  |Evet    |
|SharePoint ve OneDrive'da şifrelenmiş belgeleri dışarı aktarma    |Hayır       |Hayır  |Evet    |
|||||

> [!NOTE]
> <sup>1</sup> Yerel bir bilgisayarda bulunan şifrelenmiş dosyaların ve e-posta iletisine kopyalanan bulut eklerinin şifresi çözülmez ve eBulma için dizine eklenmez. Bu senaryolar için daha fazla bilgi ve geçici çözüm için bu makalenin [E-posta ekleriyle şifre çözme sınırlamaları](#decryption-limitations-with-email-attachments) bölümüne bakın.

## <a name="decryption-limitations-with-sensitivity-labels-in-sharepoint-and-onedrive"></a>SharePoint ve OneDrive'da duyarlılık etiketleriyle şifre çözme sınırlamaları

Şifrelemeyi uygulayan bir duyarlılık etiketi aşağıdaki ayarlardan biriyle yapılandırıldığında eBulma, SharePoint ve OneDrive'daki şifrelenmiş dosyaları desteklemez:

- Kullanıcılar, etiketi belgeye el ile uyguladığında izinleri atayabilir. Bu bazen *kullanıcı tanımlı izinler* olarak adlandırılır.

- Belgeye kullanıcı erişimi, **Hiçbir Zaman** dışında bir değere ayarlanmış bir süre sonu ayarına sahiptir.

Bu ayarlar hakkında daha fazla bilgi için Şifreleme [uygulamak için duyarlılık etiketlerini kullanarak içeriğe erişimi kısıtlama](encryption-sensitivity-labels.md#configure-encryption-settings) bölümündeki "Şifreleme ayarlarını yapılandırma" bölümüne bakın.

Önceki ayarlarla şifrelenen belgeler yine de eBulma araması tarafından döndürülebilir. Bir belge özelliği (başlık, yazar veya değiştirme tarihi gibi) arama ölçütleri ile eşleştiğinde bu durum oluşabilir. Bu belgeler arama sonuçlarına dahil edilebilse de, bunlar önizlenemez veya gözden geçirılamaz. Bu belgeler eKeşif (Premium) içinde dışarı aktarıldığında da şifrelenmiş olarak kalır.

> [!IMPORTANT]
> Şifre çözme, yerel olarak şifrelenen ve ardından SharePoint veya OneDrive'a yüklenen dosyalar için desteklenmez. Örneğin, Azure Information Protection (AIP) istemcisi tarafından şifrelenen ve ardından Microsoft 365'e yüklenen yerel dosyalar desteklenmez. Yalnızca SharePoint veya OneDrive hizmetinde şifrelenen dosyalar şifre çözme için desteklenir.

## <a name="decryption-limitations-with-email-attachments"></a>E-posta ekleriyle şifre çözme sınırlamaları

Aşağıdaki senaryolarda, e-posta iletilerine eklenen dosyaların şifre çözmesi ile ilgili sınırlamalar açıklanmaktadır. Bu senaryo açıklamaları, bu sınırlamaları azaltmak için geçici çözümleri de içerir.

- Yerel bir bilgisayarda bulunan (ve SharePoint sitesinde veya OneDrive hesabında depolanmayan) bir dosyanın e-posta iletisine ekli olması ve e-posta iletisine şifreleme uygulayan bir duyarlılık etiketi uygulanması durumunda, ekli dosyanın şifresi eBulma tarafından çözülemez. Başka bir deyişle, alıcının posta kutusunun anahtar sözcük arama sorgusunu çalıştırırsanız, şifrelenmiş dosya eki anahtar sözcük arama sorgusu tarafından döndürülmeyecek.

  Bu sınırlamanın geçici çözümü, gönderenin posta kutusunda aynı dosya ekini aramaktır. Bunun nedeni duyarlılık etiketi tarafından uygulanan şifrelemenin e-posta iletisinin taşınması sırasında uygulanmasıdır. Başka bir deyişle, e-posta iletisi gönderildiğinde ek şifrelenir. Sonuç, alıcının posta kutusunda aynı dosya şifrelenmiş olsa bile, gönderenin posta kutusunda ekli dosyanın örneği şifrelenmemiştir.

- Benzer şekilde, e-posta iletisine kopyalanan bulut eklerinin (SharePoint sitesinde veya OneDrive hesabında depolanan dosyalar) (Outlook'ta **Kopya olarak ekle** seçeneği kullanılarak) eBulma tarafından şifresi çözülemez. Bunun nedeni, e-posta iletisi gönderildiğinde duyarlılık etiketi tarafından uygulanan şifrelemenin de uygulanmasıdır. Gönderenin posta kutusunda bulut ekinin kopyasının şifrelenmemiş örneğini aramak da bu sınırlamanın geçici çözümüdür.

Bu senaryoların her ikisinde de, e-posta özelliği (gönderme tarihi, gönderen, alıcı veya konu gibi) arama sorgusuyla eşleşiyorsa, şifrelenmiş dosya eklerine sahip e-posta iletileri eBulma araması tarafından döndürülebilir.

## <a name="requirements-for-decryption-in-ediscovery"></a>eBulma'da şifre çözme gereksinimleri

Microsoft şifreleme teknolojileriyle şifrelenmiş dosyaları önizlemek, gözden geçirmek ve dışarı aktarmak için RMS Şifre Çözme rolüne atanmış olmanız gerekir. eKeşif (Premium) içinde bir gözden geçirme kümesine eklenen şifrelenmiş dosyaları gözden geçirmek ve sorgulamak için de bu role atanmış olmanız gerekir.

Bu rol varsayılan olarak Microsoft Purview uyumluluk portalı **İzinler** sayfasındaki eBulma Yöneticisi rol grubuna atanır. RMS Şifre Çözme rolü hakkında daha fazla bilgi için bkz. [eBulma izinleri atama](assign-ediscovery-permissions.md#rms-decrypt).

### <a name="decrypting-rms-protected-email-messages-and-encrypted-file-attachments-using-content-search-or-ediscovery-standard"></a>İçerik araması veya eBulma (Standart) kullanarak RMS korumalı e-posta iletilerinin ve şifrelenmiş dosya eklerinin şifresini çözme

İçerik aramasının sonuçlarına dahil edilen tüm hak korumalı (RMS korumalı) e-posta iletilerini dışarı aktardığınızda şifresi çözülür. Ayrıca, [Microsoft şifreleme teknolojisiyle](encryption.md) şifrelenen ve arama sonuçlarında yer alan bir e-posta iletisine eklenmiş tüm dosyaların şifresi dışarı aktarıldığında çözülür. Bu şifre çözme özelliği, eBulma Yöneticisi rol grubunun üyeleri için varsayılan olarak etkindir. Bunun nedeni, RMS Şifre Çözme yönetim rolünün varsayılan olarak bu rol grubuna atanmış olmasıdır. Şifrelenmiş e-posta iletilerini ve eklerini dışarı aktarırken aşağıdakileri göz önünde bulundurun:
  
- Daha önce açıklandığı gibi, RMS korumalı iletileri dışarı aktarırken şifre çözmeyi etkinleştirirseniz, arama sonuçlarını tek tek iletiler olarak dışarı aktarmanız gerekir. Arama sonuçlarını bir PST dosyasına aktarırsanız, RMS korumalı iletiler tek tek e-posta iletileri olarak dışarı aktarılır.

- Şifresi çözülen iletiler **ResultsLog** raporunda tanımlanır. Bu rapor **, Kod Çözme Durumu** adlı bir sütun içerir ve **Kodu Çözülmüş** değeri şifresi çözülen iletileri tanımlar.

- Arama sonuçlarını dışarı aktarırken dosya eklerinin şifresini çözmenin yanı sıra, arama sonuçlarının önizlemesini yaparken de şifresi çözülmüş dosyanın önizlemesini görüntüleyebilirsiniz. Hak korumalı e-posta iletisini yalnızca dışarı aktardıktan sonra görüntüleyebilirsiniz.

- Birinin RMS korumalı iletilerin ve şifrelenmiş dosya eklerinin şifresini çözmesini engellemeniz gerekiyorsa, özel bir rol grubu oluşturmanız (yerleşik eBulma Yöneticisi rol grubunu kopyalayarak) ve ardından ÖZEL rol grubundan RMS Decrypt yönetim rolünü kaldırmanız gerekir. Ardından iletilerin şifresini çözmek istemediğiniz kişiyi özel rol grubunun bir üyesi olarak ekleyin.
