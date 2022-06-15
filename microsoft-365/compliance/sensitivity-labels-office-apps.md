---
title: Office uygulamalarında duyarlılık etiketlerini yönetme
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: BT yöneticilerinin masaüstü, mobil ve web için Office uygulamalarında duyarlılık etiketlerini yönetmesine yönelik bilgiler.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 21420958d063969a588a4413ba5ee4629e2eb027
ms.sourcegitcommit: 1c8f54f9e7a7665bc10b5ef4a3d8c36e3e48f44c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/14/2022
ms.locfileid: "66078425"
---
# <a name="manage-sensitivity-labels-in-office-apps"></a>Office uygulamalarında duyarlılık etiketlerini yönetme

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview uyumluluk portalı duyarlılık etiketlerini [yayımladığınızda](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy), bunlar kullanıcıların verileri oluşturuldukça veya düzenlendikçe sınıflandırması ve koruması için Office uygulamalarda görünmeye başlar.

Office uygulamalarında duyarlılık etiketlerini başarıyla yönetmenize yardımcı olması için bu makaledeki bilgileri kullanın. Örneğin, yerleşik etiketlemeye özgü özellikler için ihtiyacınız olan en düşük uygulama sürümlerini, bu özellikler için ek yapılandırma bilgilerini belirleyin ve Azure Information Protection birleşik etiketleme istemcisi ve diğer uygulamalar ve hizmetlerle etkileşimleri anlayın.

## <a name="labeling-client-for-desktop-apps"></a>Masaüstü uygulamaları için istemci etiketleme

Windows ve Mac için Office masaüstü uygulamalarında yerleşik olan duyarlılık etiketlerini kullanmak için Office abonelik sürümünü kullanmanız gerekir. Bu etiketleme istemcisi, bazen "Office Perpetual" olarak adlandırılan tek başına Office sürümlerini desteklemez.

Office abonelik sürümleri için Kurumlar için Microsoft 365 Uygulamaları yükseltemiyorsanız, yalnızca Windows bilgisayarlar için [Azure Information Protection (AIP) birleşik etiketleme istemcisini](/azure/information-protection/rms-client/aip-clientv2) kullanabilirsiniz. Ancak, bu istemci artık [bakım modundadır](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/announcing-aip-unified-labeling-client-maintenance-mode-and/ba-p/3043613) ve gerekmedikçe Office uygulamalar için AIP eklentisini kullanmanızı önermeyiz. Daha fazla bilgi için bkz. [Office uygulamalar için AIP eklentisi yerine yerleşik etiketlemeyi seçme](sensitivity-labels-aip.md).

## <a name="support-for-sensitivity-label-capabilities-in-apps"></a>Uygulamalarda duyarlılık etiketi özellikleri desteği

Aşağıdaki tablolarda, Office uygulamalarında yerleşik olarak bulunan duyarlılık etiketlerine yönelik belirli özellikler getiren en düşük Office sürümü listelenir. Ya da etiket özelliği genel önizlemedeyse veya gelecekteki bir sürüm için gözden geçiriliyorsa. Gelecek sürümler için planlanan yeni özelliklerle ilgili ayrıntılar için [Microsoft 365 yol haritasını](https://aka.ms/MIPC/Roadmap) kullanın.

Office uygulamalarının yeni sürümleri farklı güncelleştirme kanalları için farklı zamanlarda kullanıma sunulur. Windows için yeni özellikleri daha önce Semi-Annual Enterprise Kanalı yerine Geçerli Kanal veya Aylık Enterprise Kanalı'ndayken alırsınız. En düşük sürüm numaraları bir güncelleştirme kanalından diğerine de farklı olabilir. Daha fazla bilgi için bkz[. Microsoft 365 Uygulamaları güncelleştirme kanallarına genel bakış](/deployoffice/overview-update-channels) ve [Microsoft 365 Uygulamaları için Güncelleştirme geçmişi](/officeupdates/update-history-microsoft365-apps-by-date).

Özel önizlemedeki yeni özellikler tabloya dahil değildir, ancak kuruluşunuzu [Microsoft Bilgi Koruması özel önizleme programına](https://aka.ms/mip-preview) aday göstererek bu önizlemelere katılabilirsiniz.

iOS ve Android için Office için Office: Duyarlılık etiketleri [Office uygulaması](https://www.microsoft.com/en-us/microsoft-365/blog/2020/02/19/new-office-app-android-ios-available/) yerleşik olarak bulunur.

> [!TIP]
> Tablolardaki en düşük sürümleri sahip olduğunuz sürümlerle karşılaştırdığınızda, baştaki sıfırları atlarken yayın sürümlerinin yaygın uygulamasını unutmayın.
> 
> Örneğin, 4.2128.0 sürümünüz var ve 4.7.1+ sürümünün en düşük sürüm olduğunu okuyorsunuz. Daha kolay karşılaştırma için 4.7.1 (başta sıfır yok) öğesini 4 olarak okuyun. **0007.1** (4 değil.**7000.1**). 4.2128.0 sürümünüz 4.0007.1'den yüksek olduğundan sürümünüz desteklenir.

### <a name="sensitivity-label-capabilities-in-word-excel-and-powerpoint"></a>Word, Excel ve PowerPoint duyarlılık etiketi özellikleri

Listelenen sayılar, her özellik için gereken en düşük Office uygulama sürümleridir. 

> [!NOTE]
> Windows ve Semi-Annual Enterprise Kanalı için desteklenen en düşük sürüm numaraları henüz yayımlanmamış olabilir. [Daha fazla bilgi edinin](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions)
 
|Yeteneği |Windows |Mac |iOS |Android |Web |
|-----------|-------:|----|----|--------|----|
|[Etiketi el ile uygulama, değiştirme veya kaldırma](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Evet - kabul et](sensitivity-labels-sharepoint-onedrive-files.md) |
|Yeni belgelere [varsayılan etiket uygulama](sensitivity-labels.md#what-label-policies-can-do)                                         | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Evet - kabul et](sensitivity-labels-sharepoint-onedrive-files.md)                                                        |
|Mevcut belgelere [varsayılan etiket uygulama](sensitivity-labels.md#what-label-policies-can-do) | Önizleme: [Beta Kanalına](https://office.com/insider) Dağıtım | Önizleme: [Geçerli Kanala Dağıtım (Önizleme)](https://office.com/insider) | İnceleme altında | İnceleme altında | [Evet - kabul et](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Etiketi değiştirmek için gerekçe gerektir](sensitivity-labels.md#what-label-policies-can-do)                     | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+  <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Evet - kabul et](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Özel yardım sayfasına yardım bağlantısı sağlama](sensitivity-labels.md#what-label-policies-can-do)                       | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Evet - kabul et](sensitivity-labels-sharepoint-onedrive-files.md) |
|[İçeriği işaretleme](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Evet - kabul et](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Değişkenlerle dinamik işaretler](#dynamic-markings-with-variables)                                              | Güncel Kanal: 2010+ <br /><br> Aylık Enterprise Kanalı: 2010+ <br /><br> Semi-Annual Enterprise Kanalı: 2102+ | 16.42+     | 2.42+ | 16.0.13328+ | [Evet - kabul et](sensitivity-labels-sharepoint-onedrive-files.md) |
|[İzinleri şimdi atayın](encryption-sensitivity-labels.md#assign-permissions-now)                                 | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Evet - kabul et](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Kullanıcıların izin atamasına izin ver: <br /> - Kullanıcılara sor](encryption-sensitivity-labels.md#let-users-assign-permissions)                     |Güncel Kanal: 2004+ <br /><br> Aylık Enterprise Kanalı: 2004+ <br /><br> Semi-Annual Enterprise Kanalı: 2008+ | 16.35+   | İnceleme altında   | İnceleme altında         | İnceleme altında                                                        |
|[Etiketle ilgili kullanıcı etkinliğini denetleme](#auditing-labeling-activities)                      | Güncel Kanal: 2011+ <br /><br> Aylık Enterprise Kanalı: 2011+ <br /><br> Semi-Annual Enterprise Kanalı: 2108+ | 16.43+ | 2.46+ | 16.0.13628+ | Evet |
|[Kullanıcıların e-postalarına ve belgelerine etiket uygulamasını gerektirme](#require-users-to-apply-a-label-to-their-email-and-documents)   | Güncel Kanal: 2101+ <br /><br> Aylık Enterprise Kanalı: 2101+ <br /><br> Semi-Annual Enterprise Kanalı: 2108+ | 16.45+         | 2.47+ | 16.0.13628+ | [Evet - kabul et](sensitivity-labels-sharepoint-onedrive-files.md)                                            
|[İçeriğe otomatik olarak bir hassasiyet etiketi uygulama](apply-sensitivity-label-automatically.md) <br /> - Hassas bilgi türlerini kullanma                    | Güncel Kanal: 2009+ <br /><br> Aylık Enterprise Kanalı: 2009+ <br /><br> Semi-Annual Enterprise Kanalı: 2102+ | 16.44+ | İnceleme altında | İnceleme altında | [Evet - kabul et](sensitivity-labels-sharepoint-onedrive-files.md) |
|[İçeriğe otomatik olarak bir hassasiyet etiketi uygulama](apply-sensitivity-label-automatically.md) <br /> - Eğitilebilir sınıflandırıcıları kullanma                    | Güncel Kanal: 2105+ <br /><br> Aylık Enterprise Kanalı: 2105+ <br /><br> Semi-Annual Enterprise Kanalı: 2108+ | 16.49+ | İnceleme altında | İnceleme altında | [Evet - kabul et](sensitivity-labels-sharepoint-onedrive-files.md) |
|Etiketlenmiş ve şifrelenmiş belgeler için [birlikte yazma ve Otomatik Kaydetme](sensitivity-labels-coauthoring.md) desteği | Güncel Kanal: 2107+ <br /><br> Aylık Enterprise Kanalı: 2107+ <br /><br> Semi-Annual Enterprise Kanalı: 2202+ |  16.51+ | Önizleme: [Kabul ettiğinizde](sensitivity-labels-coauthoring.md#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) 2,58+ | Önizleme: [Kabul ettiğinizde](sensitivity-labels-coauthoring.md#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) 16.0.14931+ | [Evet - kabul et](sensitivity-labels-sharepoint-onedrive-files.md) |
|[PDF desteği](#pdf-support)| Önizleme: [Beta Kanalına](https://office.com/insider) Dağıtım |  İnceleme altında | İnceleme altında | İnceleme altında | İnceleme altında |


### <a name="sensitivity-label-capabilities-in-outlook"></a>Outlook'da duyarlılık etiketi özellikleri

Listelenen sayılar, her özellik için gereken en düşük Office uygulama sürümleridir. 

> [!NOTE]
> Windows ve Semi-Annual Enterprise Kanalı için desteklenen en düşük sürüm numaraları henüz yayımlanmamış olabilir. [Daha fazla bilgi edinin](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions)

|Yeteneği |Windows için Outlook |Mac için Outlook |iOS'da Outlook |Android'da Outlook |Web üzerinde Outlook |
|-----------|-------------------:|----------------|---------------|-------------------|-------------------|
|[Etiketi el ile uygulama, değiştirme veya kaldırma](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Evet               |
|[Varsayılan etiket uygulama](sensitivity-labels.md#what-label-policies-can-do)                                         | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Evet               |
|[Etiketi değiştirmek için gerekçe gerektir](sensitivity-labels.md#what-label-policies-can-do)                     | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Evet               |
|[Özel yardım sayfasına yardım bağlantısı sağlama](sensitivity-labels.md#what-label-policies-can-do)                       | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Evet               |
|[İçeriği işaretleme](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Evet               |
|[Değişkenlerle dinamik işaretler](#dynamic-markings-with-variables)                                              | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Evet               |
|[İzinleri şimdi atayın](encryption-sensitivity-labels.md#assign-permissions-now)                                 | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Evet               |
|[Kullanıcıların izin atamasına izin ver: <br /> - İletme](encryption-sensitivity-labels.md#let-users-assign-permissions)                     | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Evet               |
|[Kullanıcıların izin atamasına izin ver: <br /> - Yalnızca Şifrele](encryption-sensitivity-labels.md#let-users-assign-permissions)  | Güncel Kanal: 2011+ <br /><br> Aylık Enterprise Kanalı: 2011+ <br /><br> Semi-Annual Enterprise Kanalı: 2108+ | 16.48+ <sup>\*</sup> | 4.2112.0+  | 4.2112.0+ | Evet |
|[Kullanıcıların e-postalarına ve belgelerine etiket uygulamasını gerektirme](#require-users-to-apply-a-label-to-their-email-and-documents)   | Güncel Kanal: 2101+ <br /><br> Aylık Enterprise Kanalı: 2101+ <br /><br> Semi-Annual Enterprise Kanalı: 2108+ | 16.43+ <sup>\*</sup>                    | 4.2111+            | 4.2111+                | Evet                |
|[Etiketle ilgili kullanıcı etkinliğini denetleme](#auditing-labeling-activities) | Güncel Kanal: 2011+ <br /><br> Aylık Enterprise Kanalı: 2011+ <br /><br> Semi-Annual Enterprise Kanalı: 2108+ | 16.51+ <sup>\*</sup> | 4.2126+ | 4.2126+ | Evet |
|[İçeriğe otomatik olarak bir hassasiyet etiketi uygulama](apply-sensitivity-label-automatically.md) <br /> - Hassas bilgi türlerini kullanma                    | Güncel Kanal: 2009+ <br /><br> Aylık Enterprise Kanalı: 2009+ <br /><br> Semi-Annual Enterprise Kanalı: 2102+ | 16.44+ <sup>\*</sup>                    | İnceleme altında           | İnceleme altında               | Evet |
|[İçeriğe otomatik olarak bir hassasiyet etiketi uygulama](apply-sensitivity-label-automatically.md) <br /> - Eğitilebilir sınıflandırıcıları kullanma                    | Güncel Kanal: 2105+ <br /><br> Aylık Enterprise Kanalı: 2105+ <br /><br> Semi-Annual Enterprise Kanalı: 2108+ | 16.49+ | İnceleme altında           | İnceleme altında               | Evet |
|[Varsayılan etiket ve zorunlu etiketleme için farklı ayarlar](#outlook-specific-options-for-default-label-and-mandatory-labeling)                    | Güncel Kanal: 2105+ <br /><br> Aylık Enterprise Kanalı: 2105+ <br /><br> Semi-Annual Enterprise Kanalı: 2108+ | 16.43+ <sup>\*</sup>                   | 4.2111+           | 4.2111+               | Evet |
|[PDF desteği](#pdf-support) | İnceleme altında|  İnceleme altında | İnceleme altında | İnceleme altında | İnceleme altında |
|

**Dipnot:**

<sup>\*</sup>[Yeni Mac için Outlook](https://support.microsoft.com/office/the-new-outlook-for-mac-6283be54-e74d-434e-babb-b70cefc77439) gerektirir

## <a name="office-built-in-labeling-client-and-the-azure-information-protection-client"></a>yerleşik etiketleme istemcisini ve Azure Information Protection istemcisini Office

Kullanıcıların Windows bilgisayarlarında [Azure Information Protection (AIP) istemcisi](/azure/information-protection/rms-client/aip-clientv2) yüklüyse, yerleşik etiketler varsayılan olarak [kendilerini destekleyen Windows Office uygulamalarda](#labeling-client-for-desktop-apps) kapatılır. Yerleşik etiketler, AIP istemcisi tarafından kullanılan Office bir eklenti kullanmadığından, daha fazla kararlılık ve daha iyi performans avantajına sahiptir. Ayrıca gelişmiş sınıflandırıcılar gibi en son özellikleri de destekler. 

> [!NOTE]
> Office güncelleştirme kanalınız için desteklenen en düşük sürümleri onaylamanıza rağmen Windows bilgisayarlarda beklediğiniz etiketleme özelliklerini görmüyorsanız, bunun nedeni [AIP eklentisini devre dışı bırakmanız](sensitivity-labels-aip.md#how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps) gerekebilir.

AIP istemcisiyle etiketleme desteği hakkında daha fazla bilgi edinmek ve bu istemciyi yalnızca Office uygulamalarda devre dışı bırakma hakkında daha fazla bilgi edinmek için bkz. [Office uygulamalar için AIP eklentisi yerine yerleşik etiketlemeyi seçme](sensitivity-labels-aip.md).

## <a name="if-you-need-to-turn-off-built-in-labeling-in-office-apps-on-windows"></a>Windows'daki Office uygulamalarında yerleşik etiketlemeyi kapatmanız gerekiyorsa

Office yerleşik etiketleme istemcisi, duyarlılık etiketlerini ve duyarlılık etiketi ilke ayarlarını Microsoft Purview uyumluluk portalı indirir.

Office yerleşik etiketleme istemcisini kullanmak için, Microsoft Purview uyumluluk portalı kullanıcılara yayımlanmış bir veya daha fazla [etiket ilkeniz](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) ve [desteklenen bir Office sürümüne](#support-for-sensitivity-label-capabilities-in-apps) sahip olmanız gerekir.

Bu koşulların her ikisi de karşılanıyorsa ancak Windows Office uygulamalarında yerleşik etiketleri kapatmanız gerekiyorsa, aşağıdaki grup ilkesi ayarını kullanın:

1. **Kullanıcı Yapılandırması/Yönetim Şablonları/Microsoft Office 2016/Güvenlik Ayarlar** gidin.

2. **Duyarlılık etiketlerini uygulamak ve 0 olarak görüntülemek için Office'da Duyarlılık özelliğini kullan'ı** ayarlayın.

Daha sonra bu yapılandırmayı geri almanız gerekiyorsa, değeri **1** olarak değiştirin. Şeritte **duyarlılık düğmesi beklendiği** gibi görüntülenmiyorsa bu değeri 1 olarak değiştirmeniz de gerekebilir. Örneğin, önceki bir yönetici bu etiketleme ayarını kapattı.
 
Bu ayarı grup ilkesi kullanarak veya [Office bulut ilkesi hizmetini](/DeployOffice/overview-office-cloud-policy-service) kullanarak dağıtın. Bu Office uygulamalar yeniden başlatıldığında bu ayar geçerlilik kazanır. 

Bu ayar Windows Office uygulamalara özgü olduğundan, duyarlılık etiketlerini (Power BI gibi) veya diğer platformları (macOS, mobil cihazlar ve Web için Office gibi) destekleyen Windows üzerindeki diğer uygulamaları etkilemez. Kullanıcıların bir kısmının veya tümünün tüm uygulamalarda ve tüm platformlarda duyarlılık etiketlerini görmesini ve kullanmasını istemiyorsanız, bu kullanıcılara duyarlılık etiketi ilkesi atamayın.

## <a name="office-file-types-supported"></a>desteklenen Office dosya türleri

Word, Excel ve PowerPoint dosyaları için yerleşik etiketlemeye sahip Office uygulamalar Open XML biçimini (.docx ve .xlsx gibi) destekler, ancak Microsoft Office 97-2003 biçimini (.doc ve .xls gibi), Belge Biçimini Aç 'ı (.odt ve .ods gibi) veya diğer biçimleri desteklemez. Yerleşik etiketleme için bir dosya türü desteklenmediğinde **Duyarlılık düğmesi Office uygulaması** kullanılamaz.

Azure Information Protection birleşik etiketleme istemcisi hem Open XML biçimini hem de Microsoft Office 97-2003 biçimini destekler. Daha fazla bilgi için, bu [istemcinin yönetici kılavuzundaki Azure Information Protection birleşik etiketleme istemcisi tarafından desteklenen dosya türleri](/azure/information-protection/rms-client/clientv2-admin-guide-file-types) bölümüne bakın.

Diğer etiketleme çözümleri için desteklenen dosya türlerine ilişkin belgelerine bakın.

## <a name="protection-templates-and-sensitivity-labels"></a>Koruma şablonları ve duyarlılık etiketleri

Office 365 İleti Şifrelemesi için tanımladığınızlar gibi yönetici tanımlı [koruma şablonları](/azure/information-protection/configure-policy-templates), yerleşik etiketleme kullanırken Office uygulamalarda görünmez. Bu basitleştirilmiş deneyim, şifrelemenin etkinleştirildiği duyarlılık etiketlerine aynı ayarlar eklendiğinden bir koruma şablonu seçmenize gerek olmadığını yansıtır.

*EncryptionTemplateId* parametresiyle [New-Label](/powershell/module/exchange/new-label) cmdlet'ini kullandığınızda var olan bir şablonu duyarlılık etiketine dönüştürebilirsiniz.

## <a name="information-rights-management-irm-options-and-sensitivity-labels"></a>Bilgi Rights Management (IRM) seçenekleri ve duyarlılık etiketleri

Şifreleme uygulamak için yapılandırdığınız duyarlılık etiketleri, kullanıcıların kendi şifreleme ayarlarını belirtme karmaşıklığını ortadan kaldırır. Birçok Office uygulamada bu tek tek şifreleme ayarları, Bilgi Rights Management (IRM) seçenekleri kullanılarak kullanıcılar tarafından el ile yapılandırılmaya devam edebilir. Örneğin, Windows uygulamaları için:

- Belge için: **Dosya** > **Bilgileri** > **Belgeyi** >  Koru **Erişimi Kısıtla**
- e-posta için: **Seçenekler** sekmesinden **Şifrele** > 
  
Kullanıcılar başlangıçta bir belgeyi veya e-postayı etiketlediğinde, etiket yapılandırma ayarlarınızı kendi şifreleme ayarlarıyla geçersiz kılabilir. Örneğin:

- Kullanıcı bir belgeye **Gizli \ Tüm Çalışanlar** etiketini uygular ve bu etiket kuruluştaki tüm kullanıcılar için şifreleme ayarlarını uygulamak üzere yapılandırılır. Daha sonra bu kullanıcı, kuruluşunuzun dışındaki bir kullanıcıya erişimi kısıtlamak için IRM ayarlarını el ile yapılandırıyor. Sonuç, **Gizli \ Tüm Çalışanlar** etiketli ve şifrelenmiş bir belgedir, ancak kuruluşunuzdaki kullanıcılar belgeyi beklendiği gibi açamaz.

- Kullanıcı bir e-postaya **Yalnızca Gizli \ Alıcılar** etiketini uygular ve bu e-posta **İletme** şifreleme ayarını uygulayacak şekilde yapılandırılır. Outlook uygulamasında bu kullanıcı daha sonra Yalnızca Şifrele için IRM ayarını el ile seçer. Sonuç olarak e-posta şifrelenmiş olarak kalır ancak **Gizli \ Yalnızca Alıcılar** etiketine sahip olmasına rağmen alıcılar tarafından iletilebilir.
    
    Özel durum olarak, Web üzerinde Outlook için **Şifreleme** menüsündeki seçenekler kullanıcının seçili durumdaki etiket şifreleme uyguladığında seçemez.

- Kullanıcı **belgeye Genel** etiketini uygular ve bu etiket şifreleme uygulamak için yapılandırılmamış. Daha sonra bu kullanıcı, belgeye erişimi kısıtlamak için IRM ayarlarını el ile yapılandırıyor. Sonuç, **Genel** etiketli ancak bazı kullanıcıların beklendiği gibi açamaması için şifreleme uygulayan bir belgedir.

Belge veya e-posta zaten etiketlenmişse, içerik henüz şifrelenmemişse veya [kullanım hakkı](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) Dışarı Aktar veya Tam Denetim'e sahipse, kullanıcı bu eylemlerden herhangi birini yapabilir. 

Anlamlı raporlama ile daha tutarlı bir etiket deneyimi için, kullanıcıların belgeleri ve e-postaları korumak için yalnızca etiketleri uygulaması için uygun etiketler ve yönergeler sağlayın. Örneğin:

- Kullanıcıların kendi izinlerini ataması gereken özel durumlar için, [kullanıcıların kendi izinlerini atamasına izin veren](encryption-sensitivity-labels.md#let-users-assign-permissions) etiketler sağlayın. 

- Kullanıcıların şifreleme uygulayan bir etiketi seçtikten sonra şifrelemeyi el ile kaldırması yerine, kullanıcılar aynı sınıflandırmaya sahip bir etikete ihtiyaç duyduğunda ancak şifreleme olmadığında alt etiket alternatifi sağlar. Gibi:
    - **Gizli \ Tüm Çalışanlar**
    - **Gizli \ Herkes (şifreleme yok)**

- Kullanıcıların bunları seçmesini önlemek için IRM ayarlarını devre dışı bırakmayı göz önünde bulundurun:
    - Windows için Outlook: 
        - *DisableDNF* ve *DisableEO* kayıt defteri anahtarları `DWORD:00000001``HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\DRM`
        - **Şifrele düğmesi için varsayılan şifreleme seçeneğini yapılandır grup ilkesi ayarının** yapılandırılmadığından emin olun
    - Mac için Outlook: 
        - Mac için Outlook [için tercihleri ayarlama](/DeployOffice/mac/preferences-outlook) bölümünde belgelenen *DisableEncryptOnly* ve *DisableDoNotForward* güvenlik ayarları
    - Web üzerinde Outlook: 
        - [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) için *BasitleştirilmişClientAccessDoNotForwardDisabled* ve *SimplifiedClientAccessEncryptOnlyDisabled* parametreleri belgelendi
    - iOS ve Android için Outlook: Bu uygulamalar, etiketleri olmayan şifreleme uygulayan kullanıcıları desteklemez, bu nedenle devre dışı bırakılamaz.

> [!NOTE]
> Kullanıcılar SharePoint veya OneDrive depolanan etiketli bir belgeden şifrelemeyi el ile kaldırırsa ve SharePoint [ve OneDrive Office dosyalar için duyarlılık etiketlerini etkinleştirdiyseniz](sensitivity-labels-sharepoint-onedrive-files.md), belgeye bir sonraki erişildiğinde veya indirildiğinde etiket şifrelemesi otomatik olarak geri yüklenir. 


## <a name="apply-sensitivity-labels-to-files-emails-and-attachments"></a>Dosyalara, e-postalara ve eklere duyarlılık etiketleri uygulama

Kullanıcılar her belge veya e-posta için aynı anda yalnızca bir etiket uygulayabilir.

Ekleri olan bir e-posta iletisini etiketlediğinizde, ekler etiketi yalnızca e-posta iletisine uyguladığınız etiket şifreleme uygularsa ve ek bir Office belgesi henüz şifrelenmemişse devralır. Devralınan etiket şifreleme uyguladığından, ek yeni şifrelenir.

E-posta iletisine uygulanan etiket şifreleme uygulamadığında veya ek zaten şifrelendiğinde, ek e-posta iletisinden etiketleri devralamaz.

**Gizli** etiketinin şifreleme uyguladığı ve **Genel** etiketinin şifreleme uygulamadığı etiket devralma örnekleri:

- Kullanıcı yeni bir e-posta iletisi oluşturur ve Bu iletiye **Gizli** etiketini uygular. Ardından etiketlenmemiş veya şifrelenmemiş bir Word belgesi eklerler. Devralma sonucunda, belge yeni **Gizli** olarak etiketlendi ve şimdi bu etiketten şifreleme uygulandı.

- Kullanıcı yeni bir e-posta iletisi oluşturur ve Bu iletiye **Gizli** etiketini uygular. Daha sonra **Genel** etiketli bir Word belgesi ekler ve bu dosya şifrelenmez. Devralma sonucunda, belge **Gizli** olarak yeniden etiketlenir ve artık bu etiketten şifreleme uygulanmıştır.

## <a name="sensitivity-label-compatibility"></a>Duyarlılık etiketi uyumluluğu

**RMS kullanan uygulamalarla**: Duyarlılık etiketlerini desteklemeyen [, RMS kullanan bir uygulamada](/azure/information-protection/requirements-applications#rms-enlightened-applications) etiketlenmiş ve şifrelenmiş bir belgeyi veya e-postayı açarsanız, uygulama şifreleme ve hak yönetimini zorunlu kılmaya devam eder.

**Azure Information Protection istemcisiyle: Azure Information Protection istemcisini** kullanarak Office yerleşik etiketleme istemcisiyle belgelere ve e-postalara uyguladığınız duyarlılık etiketlerini görüntüleyebilir ve değiştirebilirsiniz.

**diğer Office sürümleriyle**: Yetkili kullanıcılar etiketli belgeleri ve e-postaları diğer Office sürümlerinde açabilir. Ancak, etiketi yalnızca desteklenen Office sürümlerinde veya Azure Information Protection istemcisini kullanarak görüntüleyebilir veya değiştirebilirsiniz. Desteklenen Office uygulaması sürümleri [önceki bölümde](#support-for-sensitivity-label-capabilities-in-apps) listelenmiştir.

## <a name="support-for-sharepoint-and-onedrive-files-protected-by-sensitivity-labels"></a>Duyarlılık etiketleriyle korunan SharePoint ve OneDrive dosyaları için destek

Office yerleşik etiketleme istemcisini SharePoint veya OneDrive belgeler için Web üzerinde Office ile kullanmak için, SharePoint [ve OneDrive Office dosyaları için duyarlılık etiketlerini etkinleştirdiğinizden](sensitivity-labels-sharepoint-onedrive-files.md) emin olun.

## <a name="support-for-external-users-and-labeled-content"></a>Dış kullanıcılar ve etiketli içerik desteği

Bir belgeyi veya e-postayı etiketlediğinizde, etiket kiracınızı ve etiket GUID'sini içeren meta veriler olarak depolanır. Etiketlenmiş bir belge veya e-posta duyarlılık etiketlerini destekleyen bir Office uygulaması tarafından açıldığında, bu meta veriler okunur ve yalnızca kullanıcı aynı kiracıya aitse etiket kendi uygulamasında görüntülenir. Örneğin, Word, PowerPoint ve Excel için yerleşik etiketleme için etiket adı durum çubuğunda görüntülenir. 

Başka bir deyişle, belgeleri farklı etiket adları kullanan başka bir kuruluşla paylaşırsanız, her kuruluş belgeye kendi etiketlerini uygulayabilir ve bunları görebilir. Ancak, uygulanan bir etiketten aşağıdaki öğeler kuruluşunuzun dışındaki kullanıcılar tarafından görülebilir:

- İçerik işaretleri. Bir etiket üst bilgi, alt bilgi veya filigran uyguladığında, bunlar doğrudan içeriğe eklenir ve birisi değiştirene veya silene kadar görünür durumda kalır.

- Şifreleme uygulayan bir etiketten temel alınan koruma şablonunun adı ve açıklaması. Bu bilgiler, belgeyi açma yetkisi olan kişiler ve bu belge için kullanım hakları hakkında bilgi sağlamak için belgenin en üstündeki ileti çubuğunda görüntülenir.

### <a name="sharing-encrypted-documents-with-external-users"></a>Şifrelenmiş belgeleri dış kullanıcılarla paylaşma

Erişimi kendi kuruluşunuzdaki kullanıcılara kısıtlamanın yanı sıra, Azure Active Directory hesabı olan diğer tüm kullanıcılara da genişletebilirsiniz. Ancak, kuruluşunuz Koşullu Erişim ilkeleri kullanıyorsa, ek dikkat edilmesi gerekenler için [sonraki bölüme](#conditional-access-policies) bakın.

Tüm Office uygulamalar ve [RMS kullanan diğer uygulamalar](/azure/information-protection/requirements-applications#rms-enlightened-applications), kullanıcı başarıyla kimlik doğrulamasından geçtikten sonra şifrelenmiş belgeleri açabilir. 

Dış kullanıcıların Azure Active Directory bir hesabı yoksa, kiracınızdaki konuk hesaplarını kullanarak kimlik doğrulaması yapabilir. Bu konuk hesapları, SharePoint ve OneDrive Office [dosyaları için duyarlılık etiketlerini etkinleştirdiğinizde SharePoint veya OneDrive paylaşılan](sensitivity-labels-sharepoint-onedrive-files.md) belgelere erişmek için de kullanılabilir:

- Bir seçenek, bu konuk hesaplarını kendiniz oluşturmaktır. Bu kullanıcıların zaten kullandığı herhangi bir e-posta adresini belirtebilirsiniz. Örneğin, Gmail adresleri.
    
    Bu seçeneğin avantajı, şifreleme ayarlarında e-posta adreslerini belirterek belirli kullanıcılara erişimi ve hakları kısıtlayabilirsiniz. Dezavantajı, hesap oluşturma ve etiket yapılandırmasıyla koordinasyon için yönetim ek yüküdür.

- Diğer bir seçenek de SharePoint [ve OneDrive tümleştirmesini Azure AD B2B ile](/sharepoint/sharepoint-azureb2b-integration) kullanmaktır; böylece kullanıcılarınız bağlantıları paylaştığında konuk hesapları otomatik olarak oluşturulur.
    
    Hesaplar otomatik olarak oluşturulduğundan ve daha basit etiket yapılandırmasından dolayı bu seçeneğin avantajı en düşük yönetim yüküdür. Bu senaryo için, e-posta adreslerini önceden bilmediğiniz için [Kimliği doğrulanmış herhangi bir kullanıcı ekle](encryption-sensitivity-labels.md#requirements-and-limitations-for-add-any-authenticated-users) şifreleme seçeneğini belirlemeniz gerekir. Dezavantajı, bu ayarın erişim ve kullanım haklarını belirli kullanıcılarla kısıtlamanıza izin vermemesidir.

Dış kullanıcılar, Windows ve Microsoft 365 Uygulamaları ([eski adıyla Office 365 uygulamalar](/deployoffice/name-change)) veya Office 2019'un tek başına sürümünü kullandıklarında şifrelenmiş belgeleri açmak için bir Microsoft hesabı da kullanabilir. Daha yakın zamanda diğer platformlar için desteklenen Microsoft hesapları, şifrelenmiş belgeleri macOS (Microsoft 365 Uygulamaları, sürüm 16.42+), Android (sürüm 16.0.13029+) ve iOS (sürüm 2.42+) üzerinde açmak için de desteklenir. Örneğin, kuruluşunuzdaki bir kullanıcı şifrelenmiş bir belgeyi kuruluşunuzun dışındaki bir kullanıcıyla paylaşır ve şifreleme ayarları dış kullanıcı için bir Gmail e-posta adresi belirtir. Bu dış kullanıcı, Gmail e-posta adresini kullanan kendi Microsoft hesabını oluşturabilir. Ardından, bu hesapla oturum açtıktan sonra belgeyi açabilir ve kendileri için belirtilen kullanım kısıtlamalarına göre düzenleyebilirler. Bu senaryonun izlenecek yol örneği için bkz. [Korumalı belgeyi açma ve düzenleme](/azure/information-protection/secure-collaboration-documents#opening-and-editing-the-protected-document).

> [!NOTE]
> Microsoft hesabının e-posta adresi, şifreleme ayarlarına erişimi kısıtlamak için belirtilen e-posta adresiyle eşleşmelidir.

Microsoft hesabı olan bir kullanıcı şifreli bir belgeyi bu şekilde açtığında, aynı ada sahip bir konuk hesabı zaten mevcut değilse kiracı için otomatik olarak bir konuk hesabı oluşturur. Konuk hesabı mevcut olduğunda, desteklenen masaüstü ve mobil Office uygulamalarından şifrelenmiş belgeleri açmaya ek olarak Web üzerinde Office kullanarak belgeleri SharePoint ve OneDrive açmak için kullanılabilir.

Ancak otomatik konuk hesabı, çoğaltma gecikme süresi nedeniyle bu senaryoda hemen oluşturulmaz. Etiket şifreleme ayarlarınızın bir parçası olarak kişisel e-posta adresleri belirtirseniz, Azure Active Directory'de ilgili konuk hesaplarını oluşturmanızı öneririz. Ardından bu kullanıcılara kuruluşunuzdan şifrelenmiş bir belge açmak için bu hesabı kullanmaları gerektiğini bildirin.

> [!TIP]
> Dış kullanıcıların desteklenen bir Office istemci uygulaması kullanacağından, konuk hesapları oluşturduktan sonra (belirli kullanıcılar için) SharePoint ve OneDrive bağlantılarını paylaşacağından veya Azure AD [B2B ile SharePoint ve OneDrive tümleştirmesi](/sharepoint/sharepoint-azureb2b-integration-preview) kullandığınızdan emin olamazsınız  (kimliği doğrulanmış herhangi bir kullanıcı için) dış kullanıcılarla güvenli işbirliğini desteklemek için daha güvenilir bir yöntemdir.

### <a name="conditional-access-policies"></a>Koşullu Erişim ilkeleri

Kuruluşunuz [Azure Active Directory Koşullu Erişim ilkeleri](/azure/active-directory/conditional-access/overview) uyguladıysa, bu ilkelerin yapılandırmasını denetleyin. İlkeler **Microsoft Azure Information Protection** içeriyorsa ve ilke dış kullanıcılara genişletildiyse, bu dış kullanıcıların kendi kiracılarında bir Azure AD hesabı olsa bile kiracınızda bir konuk hesabı olmalıdır.

Bu konuk hesabı olmadan, şifrelenmiş belgeyi açamaz ve bir hata iletisi göremezler. İleti metni, bu senaryonun **Oturumu kapatma ve farklı bir Azure Active Directory kullanıcı hesabıyla yeniden oturum açma** konusunda yanlış yönergeyle, hesabının kiracıya dış kullanıcı olarak eklenmesi gerektiğini bildirebilir.

Etiketlerinizle şifrelenmiş belgeleri açması gereken dış kullanıcılar için kiracınızda konuk hesapları oluşturamıyor ve yapılandıramıyorsanız, Azure Information Protection Koşullu Erişim ilkelerinden kaldırmanız veya dış kullanıcıları ilkelerden dışlamanız gerekir.

Duyarlılık etiketleri tarafından kullanılan şifreleme hizmeti olan Koşullu Erişim ve Azure Information Protection hakkında daha fazla bilgi için sık sorulan soruya bakın; [Azure Information Protection koşullu erişim için kullanılabilir bir bulut uygulaması olarak listelendiğini görüyorum; bu nasıl çalışır?](/azure/information-protection/faqs#i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work)

## <a name="when-office-apps-apply-content-marking-and-encryption"></a>Office uygulamalar içerik işaretleme ve şifreleme uyguladığında

Office uygulamalar, kullandığınız uygulamaya bağlı olarak duyarlılık etiketiyle içerik işaretleme ve şifreleme işlemlerini farklı şekilde uygular.

| Uygulama | İçerik işaretleme | Şifreleme |
| --- | --- | --- |
| Tüm platformlarda Word, Excel, PowerPoint | Hemen | Hemen |
| PC ve Mac için Outlook | Exchange Online e-postayı gönderdikten sonra | Hemen |
| Web üzerinde Outlook, iOS ve Android | Exchange Online e-postayı gönderdikten sonra | Exchange Online e-postayı gönderdikten sonra |
|

Office uygulamaları dışındaki dosyalara duyarlılık etiketleri uygulayan çözümler, dosyaya etiketleme meta verileri uygulayarak bunu yapar. Bu senaryoda, etiketin yapılandırmasından içerik işaretleme dosyaya eklenmez, ancak şifreleme uygulanır. 

Bu dosyalar bir Office masaüstü uygulamasında açıldığında, dosya ilk kaydedildiğinde içerik işaretleri Azure Information Protection birleşik etiketleme istemcisi tarafından otomatik olarak uygulanır. Masaüstü, mobil veya web uygulamaları için yerleşik etiketleme kullandığınızda içerik işaretleri otomatik olarak uygulanmaz.

Office uygulamaların dışına duyarlılık etiketi uygulamayı içeren senaryolar şunlardır:

- Azure Information Protection birleşik etiketleme istemcisinden tarayıcı, Dosya Gezgini ve PowerShell 

- SharePoint ve OneDrive için otomatik etiketleme ilkeleri

- etiketli ve şifrelenmiş verileri Power BI dışarı aktar

- Bulut Uygulamaları için Microsoft Defender

Bu senaryolarda, yerleşik etiketlemesi olan bir kullanıcı, Office uygulamalarını kullanarak geçerli etiketi geçici olarak kaldırarak veya değiştirerek ve sonra özgün etiketi yeniden uygulayarak etiketin içerik işaretlerini uygulayabilir.

### <a name="dynamic-markings-with-variables"></a>Değişkenlerle dinamik işaretler

> [!IMPORTANT]
> Office uygulamalarınız bu özelliği desteklemiyorsa, işaretleri değişkenleri çözümlemek yerine etiket yapılandırmasında belirtilen özgün metin olarak uygular.
> 
> Azure Information Protection birleşik etiketleme istemcisi dinamik işaretlemeleri destekler. Office'da yerleşik olarak bulunan etiketleme için, desteklenen en düşük [sürümler](#support-for-sensitivity-label-capabilities-in-apps) için bu sayfadaki özellikler bölümündeki tablolara bakın.

İçerik işaretleri için duyarlılık etiketi yapılandırırken, üst bilgi, alt bilgi veya filigranınız için metin dizesinde aşağıdaki değişkenleri kullanabilirsiniz:

| Değişken | Açıklama | Etiket uygulandığında örnek |
| -------- | ----------- | ------- |
| `${Item.Label}` | Uygulanan etiketin etiket görünen adı | **Genel**|
| `${Item.Name}` | Etiketlenen içeriğin dosya adı veya e-posta konusu | **Sales.docx** |
| `${Item.Location}` | Etiketlenen belgenin yolu ve dosya adı veya etiketlenen bir e-postanın e-posta konusu | **\\\Sales\2020\Q3\Report.docx**|
| `${User.Name}` | Etiketi uygulayan kullanıcının görünen adı | **Richard Simone** |
| `${User.PrincipalName}` | Etiketi uygulayan kullanıcının Azure AD kullanıcı asıl adı (UPN) | **rsimone\@contoso.com** |
| `${Event.DateTime}` | İçeriğin etiketlendiği tarih ve saat, etiketi Microsoft 365 uygulamalarında uygulayan kullanıcının yerel saat diliminde veya Office Çevrimiçi ve otomatik etiketleme ilkeleri için UTC (Eşgüdümlü Evrensel Saat) | **10.08.2020 13:30** |

> [!NOTE]
> Bu değişkenlerin söz dizimi büyük/küçük harfe duyarlıdır.

#### <a name="setting-different-visual-markings-for-word-excel-powerpoint-and-outlook"></a>Word, Excel, PowerPoint ve Outlook için farklı görsel işaretler ayarlama

Ek değişken olarak, metin dizesinde bir "If.App" değişken deyimi kullanarak Office uygulama türü başına görsel işaretler yapılandırabilir ve **Word**, **Excel, PowerPoint** veya **Outlook** değerlerini kullanarak uygulama türünü tanımlayabilirsiniz. Ayrıca, aynı If.App deyiminde birden fazla değer belirtmek istiyorsanız bu değerleri kısaltabilirsiniz.

Aşağıdaki sözdizimini kullanın:

```
${If.App.<application type>}<your visual markings text> ${If.End}
```

Diğer dinamik görsel işaretlerinde olduğu gibi söz dizimi büyük/küçük harfe duyarlıdır ve her uygulama türünün (WEPO) kısaltmalarını içerir.

Örnekler:

- **Yalnızca Word belgeleri için üst bilgi metnini ayarlayın:**

    `${If.App.Word}This Word document is sensitive ${If.End}`

    Yalnızca Word belge üst bilgilerinde, etiket "Bu Word belgesi hassas" üst bilgi metnini uygular. Diğer Office uygulamalarına üst bilgi metni uygulanmaz.

- **PowerPoint için Word, Excel ve Outlook için alt bilgi metni ve farklı alt bilgi metni ayarlayın:**

    `${If.App.WXO}This content is confidential. ${If.End}${If.App.PowerPoint}This presentation is confidential. ${If.End}`

    Word, Excel ve Outlook etiket, "Bu içerik gizlidir" alt bilgi metnini uygular. PowerPoint etiket, "Bu sunu gizlidir" alt bilgi metnini uygular.

- **Word ve PowerPoint için belirli bir filigran metni ayarlayın ve ardından Word, Excel ve PowerPoint için filigran metni ayarlayın:**

    `${If.App.WP}This content is ${If.End}Confidential`

    Word ve PowerPoint etiket, "Bu içerik Gizlidir" filigran metnini uygular. Excel etiket, "Gizli" filigran metnini uygular. Outlook,görsel işaretler olarak filigranlar Outlook için desteklenmediğinden etiket filigran metni uygulamaz.

## <a name="require-users-to-apply-a-label-to-their-email-and-documents"></a>Kullanıcıların e-postalarına ve belgelerine etiket uygulamasını gerektirme

> [!IMPORTANT]
> 
> [Azure Information Protection birleşik etiketleme istemcisi](/azure/information-protection/rms-client/install-unifiedlabelingclient-app), zorunlu etiketleme olarak da bilinen bu yapılandırmayı destekler. Office uygulamalarında yerleşik olarak bulunan etiketleme için, en düşük [sürümler](#support-for-sensitivity-label-capabilities-in-apps) için bu sayfadaki özellikler bölümündeki tablolara bakın.
>
> Belgeler için zorunlu etiketlemeyi kullanmak ancak e-postaları kullanmamak için, sonraki bölümde Outlook özgü seçeneklerin nasıl yapılandırıldığını açıklayan yönergelere bakın.
> 
> Power BI için zorunlu etiketleme kullanmak için bkz. [Power BI için zorunlu etiket ilkesi](/power-bi/admin/service-security-sensitivity-label-mandatory-label-policy).

**Kullanıcıların e-postalarına ve belgelerine etiket uygulamasını gerektir** ilke ayarı seçildiğinde, ilkeye atanan kullanıcıların aşağıdaki senaryolar altında bir duyarlılık etiketi seçip uygulaması gerekir:

- Azure Information Protection birleşik etiketleme istemcisi için:
    - Belgeler için (Word, Excel, PowerPoint): Etiketsiz bir belge kaydedildiğinde veya kullanıcılar belgeyi kapattığında.
    - E-postalar için (Outlook): Kullanıcılar etiketsiz bir ileti gönderdiğinde.

- Office uygulamalarında yerleşik etiketleme için:
    - Belgeler için (Word, Excel, PowerPoint): Etiketsiz bir belge açıldığında veya kaydedildiğinde.
    - E-postalar için (Outlook): Kullanıcılar etiketsiz bir e-posta iletisi gönderir.

Yerleşik etiketleme için ek bilgiler:

- Etiketsiz bir belgeyi açtıkları için kullanıcılardan duyarlılık etiketi eklemeleri istendiğinde, etiket ekleyebilir veya belgeyi salt okunur modda açmayı seçebilirler.

- Zorunlu etiketleme etkin olduğunda, kullanıcılar belgelerden duyarlılık etiketlerini kaldıramaz, ancak var olan bir etiketi değiştirebilir.

- Zorunlu etiketleme etkin olduğunda, belge etiketlendiğinde veya şifrelendiğinde PDF'ye yazdır seçeneği kullanılamaz. Daha fazla bilgi için bu sayfadaki [PDF desteği](#pdf-support) bölümüne bakın.

Bu ayarın ne zaman kullanılacağı hakkında yönergeler için [ilke ayarları](sensitivity-labels.md#what-label-policies-can-do) hakkındaki bilgilere bakın.

> [!NOTE]
> Zorunlu etiketlemeye ek olarak belgeler ve e-postalar için varsayılan etiket ilkesi ayarını kullanıyorsanız: 
>
> Varsayılan etiket her zaman zorunlu etiketlemeye göre önceliklidir. Ancak belgeler için, Azure Information Protection birleşik etiketleme istemcisi tüm etiketlenmemiş belgelere varsayılan etiketi uygularken, yerleşik etiketleme varsayılan etiketi etiketlenmemiş mevcut belgelere değil, yeni belgelere uygular. Davranıştaki bu fark, varsayılan etiket ayarıyla zorunlu etiketleme kullandığınızda, yerleşik etiketleme kullandıklarında kullanıcılardan büyük olasılıkla Azure Information Protection birleşik etiketleme istemcisini kullandıklarından daha sık duyarlılık etiketi uygulamalarının isteneceği anlamına gelir.
> 
> Şimdi kullanıma sunulacak: Yerleşik etiketleme kullanan ve mevcut belgeler için varsayılan etiketi destekleyen uygulamaları Office. Ayrıntılar için Word, Excel ve PowerPoint [için yetenekler tablosuna](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) bakın.

## <a name="outlook-specific-options-for-default-label-and-mandatory-labeling"></a>Varsayılan etiket ve zorunlu etiketleme için Outlook özgü seçenekler

Yerleşik etiketleme için, bu sayfadaki Outlook [için capabilities tablosunu](#sensitivity-label-capabilities-in-outlook) ve **varsayılan etiket ve zorunlu etiketleme için Farklı ayarlar** satırını kullanarak bu özellikleri destekleyen en düşük Outlook sürümlerini belirleyin. Azure Information Protection birleşik etiketleme istemcisinin tüm sürümleri bu Outlook özgü seçenekleri destekler.

Outlook uygulaması, belgeler için varsayılan etiket ayarından farklı bir varsayılan etiket ayarını desteklediğinde:

- Microsoft Purview uyumluluk portalı etiket ilkesi yapılandırmasında, **E-postalara varsayılan etiket uygula** sayfasında: Etiketlenmemiş tüm e-postalara uygulanacak veya varsayılan etiket olmayan duyarlılık etiketi seçiminizi belirtebilirsiniz. Bu ayar, yapılandırmanın önceki Belgeler **için İlke ayarları** sayfasındaki **Bu etiketi varsayılan olarak belgelere uygula** ayarından bağımsızdır.

Outlook uygulaması, belgeler için varsayılan etiket ayarından farklı bir varsayılan etiket ayarını desteklemediğinde: Outlook her zaman etiket ilkesi yapılandırmasının **Belgeler için ilke ayarları** sayfasındaki **Belgelere varsayılan olarak bu etiketi uygula** için belirttiğiniz değeri kullanır.

Outlook uygulaması zorunlu etiketlemeyi kapatmayı desteklediğinde:

- Microsoft Purview uyumluluk portalı etiket ilkesi yapılandırmasında, **İlke ayarları** sayfasında: **Kullanıcıların e-postalarına veya belgelerine etiket uygulamasını gerektir'i** seçin. Ardından **İleri İleri'yi** >  seçin ve **Kullanıcıların e-postalarına etiket uygulamasını gerektir** onay kutusunu temizleyin. Zorunlu etiketlemenin e-postalara ve belgelere uygulanmasını istiyorsanız onay kutusunu seçili tutun.

Outlook uygulaması zorunlu etiketlemeyi kapatmayı desteklemediğinde: **Kullanıcıların e-postalarına veya belgelerine ilke ayarı olarak etiket uygulamasını gerektir'i** seçerseniz, Outlook kullanıcılardan etiketsiz e-postalar için her zaman bir etiket seçmelerini ister.

> [!NOTE]
> [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy) veya [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy) cmdlet'lerini kullanarak **PowerShell gelişmiş ayarlarını OutlookDefaultLabel** ve **DisableMandatoryInOutlook** yapılandırdıysanız:
> 
> Bu PowerShell ayarları için seçtiğiniz değerler Microsoft Purview uyumluluk portalı etiket ilkesi yapılandırmasına yansıtılır ve bu ayarları destekleyen Outlook uygulamalar için otomatik olarak çalışır. Diğer PowerShell gelişmiş ayarları yalnızca Azure Information Protection birleşik etiketleme istemcisi için desteklenmektedir.

## <a name="pdf-support"></a>PDF desteği

Yerleşik etiketleme için, desteklenen en düşük sürümleri belirlemek için bu sayfadaki [özellikler](#support-for-sensitivity-label-capabilities-in-apps) bölümündeki tabloları kullanın. Azure Information Protection birleşik etiketleme istemcisi, Office uygulamalarında PDF'yi desteklemez.

Word, Excel ve PowerPoint, Office bir belgeyi PDF belgesine dönüştürmek için aşağıdaki yöntemleri destekler:

- Dosya > PDF > Farklı Kaydet 
- Pdf > Dışarı Aktarma > Dosya
- Pdf > Kopya Gönderme > Paylaş

Bu eylem, [Dosya ve sayfa etkinlikleri](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities) denetim grubundan **Yeniden Adlandırılmış dosya** denetim olayıyla günlüğe kaydedilir. Uyumluluk portalındaki denetim arama sonuçlarında, **etkinlik alanı için** **SensitivityLabeledFileRenamed** değerini görüntüleyen bu denetim olayının ayrıntılarını görürsünüz.

PDF oluşturulduğunda, herhangi bir içerik işareti ve şifreleme içeren etiketi devralır. Şifrelenmiş PDF'ler Windows veya Mac'te Microsoft Edge ile açılabilir. Daha fazla bilgi ve alternatif [okuyucular için bkz. Korumalı PDF'ler için hangi PDF okuyucular desteklenir?](/azure/information-protection/rms-client/protected-pdf-readers#viewing-protected-pdfs-in-microsoft-edge-on-windows-or-mac)

PDF senaryoları desteklenmez:

- PDF'ye yazdır
    
    Kullanıcılar bu seçeneği belirlerse, belgenin etiketin ve şifrelemenin (uygulandıysa) korumasını kaybedeceği ve devam etmek için onaylamaları gerektiği konusunda uyarılırlar. Duyarlılık etiketi ilkeniz bir etiketi kaldırmak veya sınıflandırmasını düşürmek için gerekçe gerektiriyorsa, bu istemi görür.
    
    Bu seçenek duyarlılık etiketini kaldırdığından, zorunlu etiketleme kullanıyorsanız bu seçenek kullanıcılar tarafından kullanılamaz. Bu yapılandırma, kullanıcıların e-postalarına ve belgelerine etiket uygulamasını gerektiren duyarlılık etiketi ilkesi ayarını ifade eder.

- PDF/A biçimi ve şifrelemesi
    
     Etiket uygulandığında uzun süreli arşivleme için tasarlanan bu PDF biçimi desteklenmez ve kullanıcıların Office belgeleri PDF'ye dönüştürmesini engeller.
    
- Parola koruması ve şifreleme
    
    **Belgenin** etiketi şifreleme uyguladığında Dosya  > **Bilgileri** > **Belgeyi** > **Parolayla Şifrele** seçeneğinin kullanılması desteklenmez. Bu senaryoda parolayla şifrele seçeneği kullanıcılar için kullanılamaz hale gelir.

Bu özellik hakkında daha fazla bilgi için bkz. [Office uygulamalarla oluşturulan PDF'lere duyarlılık etiketleri uygulama](https://insider.office.com/blog/apply-sensitivity-labels-to-pdfs-created-with-office-apps).


## <a name="auditing-labeling-activities"></a>Etiketleme etkinliklerini denetleme

Duyarlılık etiketi etkinlikleri tarafından oluşturulan denetim olayları hakkında bilgi için, [Microsoft Purview uyumluluk portalı denetim günlüğünde arama](search-the-audit-log-in-security-and-compliance.md) bölümündeki [Duyarlılık etiketi etkinlikleri](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) bölümüne bakın.

Bu denetim bilgileri, duyarlılık etiketlerinizin nasıl kullanıldığını ve etiketlenmiş içeriğin nerede bulunduğunu anlamanıza yardımcı olmak için [içerik gezgininde](data-classification-content-explorer.md) ve [etkinlik gezgininde](data-classification-activity-explorer.md) görsel olarak temsil edilir. 

Ayrıca [, denetim günlüğü kayıtlarını dışarı aktarıp yapılandırırken](export-view-audit-log-records.md) tercih ettiğiniz güvenlik bilgileri ve olay yönetimi (SIEM) yazılımıyla özel raporlar da oluşturabilirsiniz. Daha büyük ölçekli raporlama çözümleri için [bkz. Office 365 Yönetim Etkinliği API başvurusu](/office/office-365-management-api/office-365-management-activity-api-reference).

> [!TIP]
> Özel raporlar oluşturmaya yardımcı olmak için aşağıdaki blog gönderilerine bakın:
> - [O365 Yönetim API'si aracılığıyla denetim günlüğü etkinliklerini Microsoft Purview - 1. Bölüm](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/microsoft-365-compliance-audit-log-activities-via-o365/ba-p/2957171)
> - [O365 Yönetim API'si aracılığıyla denetim günlüğü etkinliklerini Microsoft Purview - 2. Bölüm](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/microsoft-365-compliance-audit-log-activities-via-o365/ba-p/2957297)

## <a name="end-user-documentation"></a>Son kullanıcı belgeleri

- [Office'te dosyalarınıza ve e-postalarınıza duyarlılık etiketleri uygulama](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [Office duyarlılık etiketleriyle ilgili bilinen sorunlar](https://support.microsoft.com/en-us/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Office'da dosyalarınıza ve e-postalarınıza duyarlılık etiketlerini otomatik olarak uygulama veya önerme](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [Duyarlılık etiketlerini otomatik olarak uygulama veya önerme ile ilgili bilinen sorunlar](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)
