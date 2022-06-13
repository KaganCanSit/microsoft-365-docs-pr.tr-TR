---
title: Belge Parmak İzi Oluşturma Hakkında
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
description: Kuruluşunuzdaki bilgi çalışanları, tipik bir gün boyunca birçok türde hassas bilgiyi işler. Belge Parmak İzi Özelliği, kuruluşunuz genelinde kullanılan standart formları tanımlayarak bu bilgileri korumanızı kolaylaştırır. Bu konu başlığında, Belge Parmak İzi Oluşturma'nın arkasındaki kavramlar ve PowerShell kullanılarak nasıl oluşturulacağı açıklanmaktadır.
ms.openlocfilehash: 3df4b7cf6f9fa09e81cf326cc58cc8114c025be9
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014486"
---
# <a name="document-fingerprinting"></a>Belge Parmak İzi

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Kuruluşunuzdaki bilgi çalışanları, tipik bir gün boyunca birçok türde hassas bilgiyi işler. Microsoft Purview uyumluluk portalında Belge Parmak İzi Özelliği, kuruluşunuz genelinde kullanılan standart formları belirleyerek bu bilgileri korumanızı kolaylaştırır. Bu konu başlığında, Belge Parmak İzi Oluşturma'nın arkasındaki kavramlar ve PowerShell kullanılarak nasıl oluşturulacağı açıklanmaktadır.

## <a name="basic-scenario-for-document-fingerprinting"></a>Belge Parmak İzi Oluşturma için temel senaryo

Belge Parmak İzi Oluşturma, standart bir formu, DLP ilkelerinizin kurallarında kullanabileceğiniz hassas bir bilgi türüne dönüştüren bir Microsoft Purview Veri Kaybı Önleme (DLP) özelliğidir. Örneğin, boş bir patent şablonunu temel alan bir belge parmak izi oluşturabilir ve ardından hassas içerik doldurulmuş tüm giden patent şablonlarını algılayan ve engelleyen bir DLP ilkesi oluşturabilirsiniz. İsteğe bağlı olarak, gönderenlere hassas bilgiler gönderebileceklerini bildirmek için [ilke ipuçları](use-notifications-and-policy-tips.md) ayarlayabilirsiniz ve gönderenin, alıcıların patentleri almaya uygun olduğunu doğrulaması gerekir. Bu işlem, kuruluşunuzda kullanılan metin tabanlı formlarla çalışır. Karşıya yükleyebileceğiniz ek form örnekleri şunlardır:

- Kamu formları
- Sağlık Sigortası Taşınabilirlik ve Sorumluluk Yasası (HIPAA) uyumluluk formları
- İnsan Kaynakları departmanları için çalışan bilgileri formları
- Kuruluşunuz için özel olarak oluşturulan özel formlar

İdeal olan, kuruluşunuzun hassas bilgileri iletmek için belirli formları kullanma konusunda yerleşik bir iş uygulaması zaten vardır. Belge parmak izine dönüştürülecek boş bir formu karşıya yükledikten ve ilgili ilkeyi ayarladıktan sonra, DLP giden postada bu parmak iziyle eşleşen tüm belgeleri algılar.

## <a name="how-document-fingerprinting-works"></a>Belge Parmak İzi Oluşturma nasıl çalışır?

Muhtemelen belgelerin gerçek parmak izine sahip olmadığını tahmin etmişsinizdir, ancak adı özelliği açıklamaya yardımcı olur. Bir kişinin parmak izlerinin benzersiz desenleri olduğu gibi, belgeler de benzersiz sözcük desenlerine sahiptir. Bir dosyayı karşıya yüklediğinizde, DLP belgedeki benzersiz sözcük desenini tanımlar, bu deseni temel alan bir belge parmak izi oluşturur ve aynı deseni içeren giden belgeleri algılamak için bu belge parmak izini kullanır. Bu nedenle bir form veya şablon karşıya yüklendiğinde en etkili belge parmak izi türü oluşturulur. Formu dolduran herkes aynı özgün sözcük kümesini kullanır ve sonra kendi sözcüklerini belgeye ekler. Giden belge parola korumalı olmadığı ve özgün formdaki tüm metni içerdiği sürece, DLP belgenin belge parmak iziyle eşleşip eşleşmediğini belirleyebilir.

> [!IMPORTANT]
> Şimdilik DLP, belge parmak izini yalnızca Exchange çevrimiçi ortamda algılama yöntemi olarak kullanabilir.

Aşağıdaki örnekte, patent şablonunu temel alan bir belge parmak izi oluşturursanız ne olacağı gösterilmektedir, ancak belge parmak izi oluşturmak için herhangi bir formu temel olarak kullanabilirsiniz.

### <a name="example-of-a-patent-document-matching-a-document-fingerprint-of-a-patent-template"></a>Patent şablonunun belge parmak iziyle eşleşen bir patent belgesi örneği

![Belge parmak izi oluşturma diyagramı.](../media/Document-Fingerprinting-diagram.png)

Patent şablonu, "Patent başlığı", "Envanterler" ve bu alanların her biri için "Açıklama" ve açıklamalar (yani desen) boş alanları içerir. Özgün patent şablonunu karşıya yüklediğinizde, desteklenen dosya türlerinden birinde ve düz metin olarak bulunur. DLP, bu sözcük desenini belge parmak izine dönüştürür. Bu, özgün metni temsil eden benzersiz bir karma değeri içeren küçük bir Unicode XML dosyasıdır ve parmak izi Active Directory'de veri sınıflandırması olarak kaydedilir. (Güvenlik önlemi olarak, özgün belgenin kendisi hizmette depolanmaz; yalnızca karma değer depolanır ve özgün belge karma değerinden yeniden oluşturulamaz.) Patent parmak izi daha sonra bir DLP ilkesiyle ilişkilendirebileceğiniz hassas bir bilgi türüne dönüşür. Parmak izini bir DLP ilkesiyle ilişkilendirdikten sonra DLP, patent parmak iziyle eşleşen belgeler içeren giden e-postaları algılar ve kuruluşunuzun ilkesine göre bunlarla ilgilenir.

Örneğin, normal çalışanların patent içeren giden iletiler göndermesini engelleyen bir DLP ilkesi ayarlamak isteyebilirsiniz. DLP, patentleri algılamak ve bu e-postaları engellemek için patent parmak izini kullanır. Alternatif olarak, hukuk departmanınızın diğer kuruluşlara patent gönderebilmesini sağlamak isteyebilirsiniz çünkü bunu yapmak için bir iş gereksinimi vardır. DLP ilkenizde bu departmanlar için özel durumlar oluşturarak belirli departmanların hassas bilgileri göndermesine izin verebilir veya bir ilke ipucunu iş gerekçesiyle geçersiz kılabilir.

### <a name="supported-file-types"></a>Desteklenen dosya türleri

Belge Parmak İzi Oluşturma, posta akışı kurallarında (taşıma kuralları olarak da bilinir) desteklenen dosya türlerini destekler. Desteklenen dosya türlerinin listesi için bkz. [Posta akışı kuralı içerik incelemesi için desteklenen dosya türleri](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection). Dosya türleri hakkında hızlı bir not: Ne posta akışı kuralları ne de Belge Parmak İzi Özelliği .dotx dosya türünü destekler. Bu, Word'de bir şablon dosyası olduğu için kafa karıştırıcı olabilir. Bu ve diğer Belge Parmak İzi Oluşturma konularında "şablon" sözcüğünü gördüğünüzde, şablon dosya türünü değil standart form olarak oluşturduğunuz bir belgeyi ifade eder.

#### <a name="limitations-of-document-fingerprinting"></a>Belge parmak izi oluşturma sınırlamaları

Belge Parmak İzi Oluşturma, aşağıdaki durumlarda hassas bilgileri algılamaz:

- Parola korumalı dosyalar
- Yalnızca görüntü içeren dosyalar
- Belge parmak izini oluşturmak için kullanılan özgün formdaki metnin tümünü içermeyen belgeler
- 10 MB'tan büyük dosyalar

## <a name="use-powershell-to-create-a-classification-rule-package-based-on-document-fingerprinting"></a>Belge parmak izine dayalı bir sınıflandırma kuralı paketi oluşturmak için PowerShell kullanma

Şu anda yalnızca [Güvenlik & Uyumluluk PowerShell'de](/powershell/exchange/connect-to-scc-powershell) belge parmak izi oluşturabilirsiniz.

DLP, hassas içeriği algılamak için sınıflandırma kuralı paketlerini kullanır. Belge parmak izini temel alan bir sınıflandırma kuralı paketi oluşturmak için **New-DlpFingerprint** ve **New-DlpSensitiveInformationType** cmdlet'lerini kullanın. **New-DlpFingerprint** sonuçları veri sınıflandırma kuralının dışında depolanmadığından, aynı PowerShell oturumunda her zaman **New-DlpFingerprint** ve **New-DlpSensitiveInformationType** veya **Set-DlpSensitiveInformationType** çalıştırırsınız. Aşağıdaki örnek, C:\Belgelerim\Contoso Employee Template.docx dosyasını temel alan yeni bir belge parmak izi oluşturur. Aynı PowerShell oturumunda **New-DlpSensitiveInformationType** cmdlet'iyle kullanabilmek için yeni parmak izini bir değişken olarak depolarsınız.

```powershell
$Employee_Template = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Employee Template.docx'))
$Employee_Fingerprint = New-DlpFingerprint -FileData $Employee_Template -Description "Contoso Employee Template"
```

Şimdi C:\Belgelerim\Contoso Müşteri Bilgileri Form.docx dosyasının belge parmak izini kullanan "Contoso Çalışanı Gizli" adlı yeni bir veri sınıflandırma kuralı oluşturalım.

```powershell
$Customer_Form = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Customer Information Form.docx'))
$Customer_Fingerprint = New-DlpFingerprint -FileData $Customer_Form -Description "Contoso Customer Information Form"
New-DlpSensitiveInformationType -Name "Contoso Customer Confidential" -Fingerprints $Customer_Fingerprint -Description "Message contains Contoso customer information."
```

Artık tüm DLP veri sınıflandırma kuralı paketlerini bulmak için **Get-DlpSensitiveInformationType** cmdlet'ini kullanabilirsiniz ve bu örnekte "Contoso Müşteri Gizli" veri sınıflandırma kuralı paketleri listesinin bir parçasıdır.

Son olarak, Microsoft Purview uyumluluk portalındaki bir DLP ilkesine "Contoso Müşteri Gizli" veri sınıflandırma kuralı paketini ekleyin. Bu örnek, var olan "ConfidentialPolicy" adlı bir DLP ilkesine kural ekler.

```powershell
New-DlpComplianceRule -Name "ContosoConfidentialRule" -Policy "ConfidentialPolicy" -ContentContainsSensitiveInformation @{Name="Contoso Customer Confidential"} -BlockAccess $True
```

Veri sınıflandırma kuralı paketini, aşağıdaki örnekte gösterildiği gibi Exchange Online'daki posta akışı kurallarında da kullanabilirsiniz. Bu komutu çalıştırmak için önce [PowerShell'i Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell) gerekir. Kural paketinin Microsoft Purview uyumluluk portalından Exchange yönetim merkezine eşitlenmesinin zaman aldığını da unutmayın.

```powershell
New-TransportRule -Name "Notify :External Recipient Contoso confidential" -NotifySender NotifyOnly -Mode Enforce -SentToScope NotInOrganization -MessageContainsDataClassification @{Name=" Contoso Customer Confidential"}
```

DLP artık Contoso Müşterisi Form.docx belge parmak iziyle eşleşen belgeleri algılar.

Söz dizimi ve parametre bilgileri için bkz:

- [New-DlpFingerprint](/powershell/module/exchange/New-DlpFingerprint)
- [New-DlpSensitiveInformationType](/powershell/module/exchange/New-DlpSensitiveInformationType)
- [Remove-DlpSensitiveInformationType](/powershell/module/exchange/Remove-DlpSensitiveInformationType)
- [Set-DlpSensitiveInformationType](/powershell/module/exchange/Set-DlpSensitiveInformationType)
- [Get-DlpSensitiveInformationType](/powershell/module/exchange/Get-DlpSensitiveInformationType)
