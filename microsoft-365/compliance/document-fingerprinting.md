---
title: Belge Parmak İzi Tanıma
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: ITPro
ms.topic: article
search.appverid: MET150
ms.service: exchange-online
ms.collection: M365-security-compliance
ms.localizationpriority: medium
description: Kurumuz bilgi çalışanları, normal bir gün boyunca birçok hassas bilgiyle başa çıkabilir. Belge Parmak İzi Tanıma, tüm kuruluşta kullanılan standart formları tanımarak bu bilgileri korumanızı kolaylaştırır. Bu konu başlığı altında, Belge Parmak İzi Tanıma'nın ardındaki kavramlar ve PowerShell kullanarak belgeyi oluşturma hakkında bilgiler açıklanmıştır.
ms.openlocfilehash: cd75fe8ec8f4c727f86689cd3a46f331e71afdad
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2022
ms.locfileid: "63010045"
---
# <a name="document-fingerprinting"></a>Belge Parmak İzi Tanıma

Kurumuz bilgi çalışanları, normal bir gün boyunca birçok hassas bilgiyle başa çıkabilir. Güvenlik Uyumluluk Merkezi'nde &amp; , Belge Parmak İzi Tanıma, kuruluş genelinde kullanılan standart formları tanımarak bu bilgileri korumanızı kolaylaştırır. Bu konu başlığı altında, Belge Parmak İzi Tanıma'nın ardındaki kavramlar ve PowerShell kullanarak belgeyi oluşturma hakkında bilgiler açıklanmıştır.

## <a name="basic-scenario-for-document-fingerprinting"></a>Belge Parmak İzi Tanıma için temel senaryo

Belge Parmak İzi Önleme, standart bir formu DLP ilkelerinizin kurallarında kullanabileceğiniz hassas bir bilgi türüne dönüştüren bir Veri Kaybı Önleme (DLP) özelliğidir. Örneğin, boş bir patent şablonunu temel alan bir belge parmak izi oluşturabilir ve sonra hassas içeriği doldurulmuş tüm giden patent şablonlarını algılayan ve engelleyen bir DLP ilkesi oluşturabilirsiniz. İsteğe bağlı olarak, gönderenlere [](use-notifications-and-policy-tips.md) hassas bilgiler gönderdiğini bildirmek için ilke ipuçları kurarak gönderenin de alıcıların patentleri almak için uygun olduğunu doğrulaması gerekir. Bu işlem, kurumda kullanılan tüm metin tabanlı formlarla çalışır. Karşıya yük yalnızca aşağıdaki diğer formlara örnek olarak verilmiştir:

- Kamu formları
- Sağlık Sigortası Taşınabilirlik ve Sorumluluk Yasası (HIPAA) uyumluluk formları
- İnsan Kaynakları departmanları için çalışan bilgi formları
- Özel olarak sizin için oluşturulan özel formlar

İdeal olan, kuruluşta hassas bilgileri iletmek için belirli formları kullanmak için önceden kurulmuş bir iş uygulaması vardır. Belgenin parmak izi ayarına dönüştürülecek boş bir form karşıya yükledikten ve buna karşılık gelen bir ilke ayardikten sonra, DLP giden postada bu parmak iziyle uyan tüm belgeleri algılar.

## <a name="how-document-fingerprinting-works"></a>Belge Parmak İzi Tanıma nasıl çalışır?

Büyük olasılıkla belgelerin gerçek parmak izi olmadığını önceden tahmin ettiniz, ancak bu ad özelliği açıklamaya yardımcı olur. Bir kişinin parmak izi benzersiz desenlere sahip olduğu gibi, belgelerin de benzersiz sözcük desenleri vardır. Bir dosyayı karşıya yüklerken, DLP belgeye benzersiz sözcük deseni tanımlar, bu düzeni temel alan bir belge parmak izi oluşturur ve aynı deseni içeren giden belgeleri algılamak için bu belge parmak izi kullanır. İşte bu nedenle form veya şablon karşıya yüklenmek, en etkili belge parmak izi türünü oluşturur. Form dolduran herkes aynı özgün sözcük dizisini kullanır ve kendi sözcüklerini belgeye ekler. Giden belge parola korumalı değilse ve özgün forma gelen metnin hepsini içerdiği sürece, DLP belgenin belgenin parmak iziyle eş olup olmadığını belirler.

> [!IMPORTANT]
> Şimdilik DLP, belge parmak izi tanımayı yalnızca çevrimiçi olarak algılama Exchange kullanabilir.

Aşağıdaki örnekte, patent şablonunu temel alan bir belgeyi parmak izi oluşturursanız ne olur, ancak herhangi bir formu belge parmak izi oluşturmak için temel olarak kullanabilirsiniz.

### <a name="example-of-a-patent-document-matching-a-document-fingerprint-of-a-patent-template"></a>Patent şablonunun parmak iziyle eşleşen bir patent belgesi örneği

![Belge parmak izi diyagramı.](../media/Document-Fingerprinting-diagram.png)

Patent şablonu, bu alanların her biri için "Patent başlığı", "Stoklar" ve "Açıklama" alanlarının boş alanlarını ve bu alanların her biri için bir desen içerir. Özgün patent şablonunu karşıya yüklerken, bu şablon desteklenen dosya türlerinden biri ve düz metin biçimindedir. DLP, bu sözcük desenini belge parmak izi haline dönüştürür. Bu, özgün metni temsil eden benzersiz bir karma değeri içeren küçük bir Unicode XML dosyasıdır ve parmak izi Active Directory'de veri sınıflandırması olarak kaydedilir. (Güvenlik önlemi olarak, özgün belgenin kendisi hizmette depolanmış değildir; yalnızca karma değeri depolanır ve özgün belge karma değerinden yeniden saklanabilir.) Bundan sonra patent parmak izi, bir DLP ilkesiyle ilişkilendirmek için hassas bir bilgi türüne olur. Parmak iziyle bir DLP ilkesi ilişkilendirildikten sonra, DLP patent parmak iziyle eşleşmesi ve bu belgelerle anlaşmalar içeren tüm giden e-postaları kuruluş ilkesine göre algılar.

Örneğin, normal çalışanların patent içeren giden iletileri göndermesini engelleyen bir DLP ilkesi ayarlamak istiyor olabilirsiniz. DLP, patentleri tespit etmek ve bu e-postaları engellemek için patent parmak izi kullanır. Alternatif olarak, hukuk departmanınıza patentleri başka kuruluşlara gönderesin diye bir iş ihtiyacı vardır. Belirli departmanların hassas bilgiler göndermesine izin vermek için, DLP ilkenizin bu departmanları özel durumlar oluşturabilir veya iş gerekçeleriyle ilke ipucunun geçersiz kılınmalarına izin veebilirsiniz.

### <a name="supported-file-types"></a>Desteklenen dosya türleri

Belge Parmak İzi, posta akış kurallarında desteklenen aynı dosya türlerini (aktarım kuralları olarak da bilinir) destekler. Desteklenen dosya türlerinin listesi için bkz. Posta akışı [kuralı içerik incelemesi için desteklenen dosya türleri](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection). Dosya türleriyle ilgili hızlı bir not: Ne posta akış kuralları ne de Belge Parmak İzi Tanıma .dotx dosya türünü desteklemez ve bu da Word'de şablon dosyası olduğundan kafa karıştırıcı olabilir. Bu belgede ve diğer Belge Parmak İzi Uygulama konularında "şablon" sözcüğüünü gördüğünüzde, şablon dosya türü olarak değil standart bir form olarak kurduğunız bir belgeye başvurur.

#### <a name="limitations-of-document-fingerprinting"></a>Belge parmak izi sınırlaması

Belge Parmak İzi Tanıma, aşağıdaki durumlarda hassas bilgileri algılamaz:

- Parola korumalı dosyalar
- Yalnızca resim içeren dosyalar
- Belge parmak izi oluşturmak için kullanılan özgün formda bulunan metnin hepsini içermeden belgeler
- 10 MB'den büyük dosyalar

## <a name="use-powershell-to-create-a-classification-rule-package-based-on-document-fingerprinting"></a>Belge parmak izi tanımayı temel alan bir sınıflandırma kuralı paketi oluşturmak için PowerShell kullanma

Şu anda yalnızca Güvenlik ve Uyumluluk Merkezi [PowerShell'de & parmak izi oluşturabilirsiniz](/powershell/exchange/connect-to-scc-powershell).

DLP, hassas içeriği algılamak için sınıflandırma kuralı paketlerini kullanır. Belgenin parmak izine dayalı bir sınıflandırma kuralı paketi oluşturmak için **New-DlpFingerprint** ve **New-DlpSensitiveInformationType** cmdlet'lerini kullanın. **New-DlpFingerprint** sonuçları veri sınıflandırma kuralının dışında depolanmamış olduğundan, aynı PowerShell oturumunda her zaman **New-DlpSensitiveInformationType** veya **Set-DlpSensitiveInformationType** komutlarını çalıştırın. Aşağıdaki örnek, C:\Belgelerim\Contoso Çalışan Kişisi adlı dosyayı temel alan yeni bir belge parmak izi Template.docx. Yeni parmak izi bir değişken olarak depolar ve bunu aynı PowerShell oturumunda **New-DlpSensitiveInformationType** cmdlet'iyle kullanabilirsiniz.

```powershell
$Employee_Template = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Employee Template.docx'))
$Employee_Fingerprint = New-DlpFingerprint -FileData $Employee_Template -Description "Contoso Employee Template"
```

Şimdi de C:\Belgelerim\Contoso Müşteri Bilgileri adlı dosyanın parmak izi kullanan "Contoso Çalışanı Gizli" adlı yeni bir veri sınıflandırma kuralı Form.docx.

```powershell
$Customer_Form = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Customer Information Form.docx'))
$Customer_Fingerprint = New-DlpFingerprint -FileData $Customer_Form -Description "Contoso Customer Information Form"
New-DlpSensitiveInformationType -Name "Contoso Customer Confidential" -Fingerprints $Customer_Fingerprint -Description "Message contains Contoso customer information."
```

Artık **tüm DLP veri sınıflandırması kural paketlerini bulmak için Get-DlpSensitiveInformationType** cmdlet'ini kullanabilirsiniz ve bu örnekte "Contoso Müşteri için Gizli" veri sınıflandırma kuralı paketleri listesinin bir parçası olarak yer alır.

Son olarak, Güvenlik Uyumluluk Merkezi'nde DLP ilkesine "Contoso Müşteri için Gizli" veri sınıflandırma kuralı &amp; paketini ekleyin. Bu örnekte, var olan "ConfidentialPolicy" adlı bir DLP ilkesine bir kural ekler.

```powershell
New-DlpComplianceRule -Name "ContosoConfidentialRule" -Policy "ConfidentialPolicy" -ContentContainsSensitiveInformation @{Name="Contoso Customer Confidential"} -BlockAccess $True
```

Ayrıca, aşağıdaki örnekte gösterildiği gibi, veri sınıflandırma kuralı paketini Exchange Online kurallarda da kullanabilirsiniz. Bu komutu çalıştırmak için, önce [PowerShell'Bağlan Exchange Online gerekir](/powershell/exchange/connect-to-exchange-online-powershell). Ayrıca, kural paketinin Güvenlik Uyumluluk Merkezi'nde Güvenlik Uyumluluk Merkezi'nde &amp; güvenlik yönetim merkezine Exchange unutmayın.

```powershell
New-TransportRule -Name "Notify :External Recipient Contoso confidential" -NotifySender NotifyOnly -Mode Enforce -SentToScope NotInOrganization -MessageContainsDataClassification @{Name=" Contoso Customer Confidential"}
```

DLP artık, Contoso Müşterisi tarafından belge parmak izi Form.docx algılayan belgeler.

Söz dizimi ve parametre bilgileri için bkz:

- [New-DlpFingerprint](/powershell/module/exchange/New-DlpFingerprint)
- [New-DlpSensitiveInformationType](/powershell/module/exchange/New-DlpSensitiveInformationType)
- [Remove-DlpSensitiveInformationType](/powershell/module/exchange/Remove-DlpSensitiveInformationType)
- [Set-DlpSensitiveInformationType](/powershell/module/exchange/Set-DlpSensitiveInformationType)
- [Get-DlpSensitiveInformationType](/powershell/module/exchange/Get-DlpSensitiveInformationType)
