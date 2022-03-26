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
description: Masaüstü, mobil ve web için Office uygulamalarının duyarlılık etiketlerini yönetmeye ilişkin BILGI.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 4a2b68e3e85b2c621a002ce762b7ec59ce31c891
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63712762"
---
# <a name="manage-sensitivity-labels-in-office-apps"></a>Office uygulamalarında duyarlılık etiketlerini yönetme

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Microsoft 365 uyumluluk merkezi veya eşdeğer [](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) etiketleme merkezinden duyarlılık etiketleri yayımlaydıktan sonra, kullanıcılar verileri oluşturduktan veya düzenlenerek sınıflandırmak ve korumak için Office uygulamaları içinde görünmeye başlar.

Uygulamalarda duyarlılık etiketlerini başarıyla yönetmenize yardımcı olması için bu Office kullanın. Örneğin, yerleşik etiketlemeyi desteklemek için ihtiyacınız olan uygulamaların en düşük sürümlerini tanımlayabilir ve Azure Information Protection birleşik etiketleme istemcisiyle etkileşimleri ve diğer uygulama ve hizmetlerle uyumluluğu anlıyoruz.

## <a name="labeling-client-for-desktop-apps"></a>Masaüstü uygulamaları için etiketleme istemcisi

Windows Mac için Office masaüstü uygulamalarına yerleşik olarak Windows duyarlılık etiketlerini kullanmak için, Office. Bu etiket istemcisi bazen "Kalıcı" olarak da adlandırılan Office tek başına Office desteklemez.

Office abonelik sürümleri için Kurumlar için Microsoft 365 Uygulamaları'e yükselte Windows, [Azure Information Protection birleşik etiketleme istemcisini kullanabilirsiniz](/azure/information-protection/rms-client/aip-clientv2).

## <a name="support-for-sensitivity-label-capabilities-in-apps"></a>Uygulamalarda duyarlılık etiketi özellikleri desteği

Her özellik için, aşağıdaki tablolarda yerleşik Office kullanarak duyarlılık etiketlerini desteklemeniz gereken en düşük özellik sürümü listelenmiştir. Ya da etiket özelliği genel önizlemede veya gelecek sürümlerde inceleme altında ise. Gelecek [Microsoft 365 planlanan yeni](https://aka.ms/MIPC/Roadmap) özelliklerle ilgili ayrıntılar için bu yol haritasını kullanın.

Yeni sürümler Office uygulamaları, farklı güncelleştirme kanalları için farklı zamanlarda kullanılabilir. Daha Windows için, yeni özellikleri Kanal Yerine Güncel Kanal veya Aylık Enterprise'ta Semi-Annual Enterprise sahip oluruz. En düşük sürüm numaraları bir güncelleştirme kanalından sonrakine kadar da farklı olabilir. Daha fazla bilgi için bkz[. Yayın için güncelleştirme kanallarına Microsoft 365 Uygulamaları](/deployoffice/overview-update-channels) [güncelleştirme geçmişi'ne Microsoft 365 Uygulamaları](/officeupdates/update-history-microsoft365-apps-by-date).

Özel önizlemede olan yeni özellikler tabloya dahil değildir, ancak en son özel önizleme programı için organizasyonlarınızı aday göstererek bu [Microsoft Bilgi Koruması katılabilirsiniz](https://aka.ms/mip-preview).

Office iOS ve Android için Office: Duyarlılık etiketleri yerleşik olarak [Office uygulaması.](https://www.microsoft.com/en-us/microsoft-365/blog/2020/02/19/new-office-app-android-ios-available/)

Ek özellikler, yalnızca bu bilgisayarlarda çalışan Azure Information Protection birleşik etiketleme istemcisini Windows kullanılabilir. Bu ayrıntılar için bkz[. Bilgisayar etiket istemcilerini Windows karşılaştırma](/azure/information-protection/rms-client/use-client#compare-the-labeling-clients-for-windows-computers).

> [!TIP]
> Tablolarda en düşük sürümleri sahip olduğunuz sürümlerle karşılaştırıldığında, baştaki sıfırları yok bırakmak için sürüm sürümlerinin yaygın uygulama olduğunu unutmayın.
> 
> Örneğin, 4.2128.0 sürümünüz var ve 4.7.1+ sürümünün en düşük sürüm olduğunu okuyun. Daha kolay karşılaştırma için, 4.7.1 (başta sıfır yok) 4 olarak okuyun. **0007.1** (4 değil.**7000.1**). 4.2128.0 sürümünüz 4.0007.1'den yüksek olduğu için sizin sürümünüz de desteklensin.

### <a name="sensitivity-label-capabilities-in-word-excel-and-powerpoint"></a>Word, Excel ve PowerPoint'te duyarlılık PowerPoint

Listelenen sayılar, her Office için gereken en düşük uygulama sürümü sayısıdır. 

> [!NOTE]
> Destek Windows Kanal Semi-Annual Enterprise, desteklenen en düşük sürüm numaraları henüz yayınlanmamış olabilir. [Daha fazla bilgi edinin](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions)
 
|Özellik |Windows |Mac |iOS |Android |Web |
|-----------|-------:|----|----|--------|----|
|[Etiketi el ile uygulama, değiştirme veya kaldırma](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Evet - kabul etmek](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Yeni belgelere varsayılan](sensitivity-labels.md#what-label-policies-can-do) etiket uygulama                                         | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Evet - kabul etmek](sensitivity-labels-sharepoint-onedrive-files.md)                                                        |
|[Var olan belgelere](sensitivity-labels.md#what-label-policies-can-do) varsayılan etiket uygulama | Önizleme: Geçerli Kanala [(Önizleme) Geliyor](https://office.com/insider) | Önizleme: Geçerli Kanala [(Önizleme) Geliyor](https://office.com/insider) | Gözden geçirme altında | Gözden geçirme altında | Rolling out: [Yes - opt-in](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Etiketi değiştirmek için gerekçe gerektirme](sensitivity-labels.md#what-label-policies-can-do)                     | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+  <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Evet - kabul etmek](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Özel yardım sayfasına yardım bağlantısı sağlama](sensitivity-labels.md#what-label-policies-can-do)                       | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Evet - kabul etmek](sensitivity-labels-sharepoint-onedrive-files.md) |
|[İçeriği işaretleme](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Evet - kabul etmek](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Değişkenlerle dinamik işaretler](#dynamic-markings-with-variables)                                              | Güncel Kanal: 2010+ <br /><br> Aylık Enterprise Kanalı: 2010+ <br /><br> Semi-Annual Enterprise: 2102+ | 16.42+     | 2.42+ | 16.0.13328+ | [Evet - kabul etmek](sensitivity-labels-sharepoint-onedrive-files.md) |
|[İzinleri şimdi ata](encryption-sensitivity-labels.md#assign-permissions-now)                                 | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Evet - kabul etmek](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Kullanıcıların izin atamasına izin ver: <br /> - Kullanıcılara sor](encryption-sensitivity-labels.md#let-users-assign-permissions)                     |Güncel Kanal: 2004+ <br /><br> Aylık Enterprise Kanalı: 2004+ <br /><br> Semi-Annual Enterprise: 2008+ | 16.35+   | Gözden geçirme altında   | Gözden geçirme altında         | Gözden geçirme altında                                                        |
|[Etiketle ilgili kullanıcı etkinliğini denetleme](#auditing-labeling-activities)                      | Güncel Kanal: 2011+ <br /><br> Aylık Enterprise Kanalı: 2011+ <br /><br> Semi-Annual Enterprise Kanalı: 2108+ | 16.43+ | 2.46+ | 16.0.13628+ | Evet |
|[Kullanıcıların e-postalarına ve belgelerine etiket uygulamalarını gerektirme](#require-users-to-apply-a-label-to-their-email-and-documents)   | Güncel Kanal: 2101+ <br /><br> Aylık Enterprise Kanalı: 2101+ <br /><br> Semi-Annual Enterprise Kanalı: 2108+ | 16.45+         | 2.47+ | 16.0.13628+ | [Evet - kabul etmek](sensitivity-labels-sharepoint-onedrive-files.md)                                            
|[İçeriğe otomatik olarak bir hassasiyet etiketi uygulama](apply-sensitivity-label-automatically.md) <br /> - Hassas bilgi türlerini kullanma                    | Güncel Kanal: 2009+ <br /><br> Aylık Enterprise Kanalı: 2009+ <br /><br> Semi-Annual Enterprise: 2102+ | 16.44+ | Gözden geçirme altında | Gözden geçirme altında | [Evet - kabul etmek](sensitivity-labels-sharepoint-onedrive-files.md) |
|[İçeriğe otomatik olarak bir hassasiyet etiketi uygulama](apply-sensitivity-label-automatically.md) <br /> - Eğitilebilir sınıflayıcıları kullanma                    | Güncel Kanal: 2105+ <br /><br> Aylık Enterprise Kanalı: 2105+ <br /><br> Semi-Annual Enterprise Kanalı: 2108+ | 16.49+ | Gözden geçirme altında | Gözden geçirme altında | [Evet - kabul etmek](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Etiketli ve şifrelenmiş belgeler için birlikte yazma](sensitivity-labels-coauthoring.md) ve Otomatik Kaydetme desteği | Güncel Kanal: 2107+ <br /><br> Aylık Enterprise Kanalı: 2107+ <br /><br> Semi-Annual Enterprise: 2202+ |  16.51+ | Önizleme: Kabul etmek için 2,58+[](sensitivity-labels-coauthoring.md#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) | Önizleme: Kabul etmek için 16.0.14931+[](sensitivity-labels-coauthoring.md#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) | [Evet - kabul etmek](sensitivity-labels-sharepoint-onedrive-files.md) |


### <a name="sensitivity-label-capabilities-in-outlook"></a>Outlook'daki duyarlılık Outlook

Listelenen sayılar, her Office için gereken en düşük uygulama sürümü sayısıdır. 

> [!NOTE]
> Destek Windows Kanal Semi-Annual Enterprise, desteklenen en düşük sürüm numaraları henüz yayınlanmamış olabilir. [Daha fazla bilgi edinin](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions)

|Özellik |Outlook için Windows |Mac için Outlook |iOS Outlook üzerinde daha fazla |Android Outlook de Outlook'i ayarlama |Web üzerinde Outlook |
|-----------|-------------------:|----------------|---------------|-------------------|-------------------|
|[Etiketi el ile uygulama, değiştirme veya kaldırma](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Evet               |
|[Varsayılan etiket uygulama](sensitivity-labels.md#what-label-policies-can-do)                                         | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Evet               |
|[Etiketi değiştirmek için gerekçe gerektirme](sensitivity-labels.md#what-label-policies-can-do)                     | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Evet               |
|[Özel yardım sayfasına yardım bağlantısı sağlama](sensitivity-labels.md#what-label-policies-can-do)                       | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Evet               |
|[İçeriği işaretleme](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Evet               |
|[Değişkenlerle dinamik işaretler](#dynamic-markings-with-variables)                                              | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Evet               |
|[İzinleri şimdi ata](encryption-sensitivity-labels.md#assign-permissions-now)                                 | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Evet               |
|[Kullanıcıların izin atamasına izin verme: <br /> - İte haberleri verme](encryption-sensitivity-labels.md#let-users-assign-permissions)                     | Güncel Kanal: 1910+ <br /><br> Aylık Enterprise Kanalı: 1910+ <br /><br> Semi-Annual Enterprise Kanalı: 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Evet               |
|[Kullanıcıların izin atamasına izin ver: <br /> - Yalnızca Şifrele](encryption-sensitivity-labels.md#let-users-assign-permissions)  | Güncel Kanal: 2011+ <br /><br> Aylık Enterprise Kanalı: 2011+ <br /><br> Semi-Annual Enterprise Kanalı: 2108+ | 16.48+ <sup>\*</sup> | 4.2112.0+  | 4.2112.0+ | Evet |
|[Kullanıcıların e-postalarına ve belgelerine etiket uygulamalarını gerektirme](#require-users-to-apply-a-label-to-their-email-and-documents)   | Güncel Kanal: 2101+ <br /><br> Aylık Enterprise Kanalı: 2101+ <br /><br> Semi-Annual Enterprise Kanalı: 2108+ | 16.43+ <sup>\*</sup>                    | 4.2111+            | 4.2111+                | Evet                |
|[Etiketle ilgili kullanıcı etkinliğini denetleme](#auditing-labeling-activities) | Güncel Kanal: 2011+ <br /><br> Aylık Enterprise Kanalı: 2011+ <br /><br> Semi-Annual Enterprise: 2022+ | 16.51+ <sup>\*</sup> | 4.2126+ | 4.2126+ | Evet |
|[İçeriğe otomatik olarak bir hassasiyet etiketi uygulama](apply-sensitivity-label-automatically.md) <br /> - Hassas bilgi türlerini kullanma                    | Güncel Kanal: 2009+ <br /><br> Aylık Enterprise Kanalı: 2009+ <br /><br> Semi-Annual Enterprise: 2102+ | 16.44+ <sup>\*</sup>                    | Gözden geçirme altında           | Gözden geçirme altında               | Evet |
|[İçeriğe otomatik olarak bir hassasiyet etiketi uygulama](apply-sensitivity-label-automatically.md) <br /> - Eğitilebilir sınıflayıcıları kullanma                    | Güncel Kanal: 2105+ <br /><br> Aylık Enterprise Kanalı: 2105+ <br /><br> Semi-Annual Enterprise Kanalı: 2108+ | 16.49+ | Gözden geçirme altında           | Gözden geçirme altında               | Evet |
|[Varsayılan etiket ve zorunlu etiketleme için farklı ayarlar](#outlook-specific-options-for-default-label-and-mandatory-labeling)                    | Güncel Kanal: 2105+ <br /><br> Aylık Enterprise Kanalı: 2105+ <br /><br> Semi-Annual Enterprise Kanalı: 2108+ | 16.43+ <sup>\*</sup>                   | 4.2111+           | 4.2111+               | Evet |
|

**Dipnotlar:**

<sup>\*</sup>Yeni [e-Mac için Outlook](https://support.microsoft.com/office/the-new-outlook-for-mac-6283be54-e74d-434e-babb-b70cefc77439)


## <a name="office-built-in-labeling-client-and-other-labeling-solutions"></a>Office etiketleme istemcisini ve diğer etiket çözümlerini yeniden etiketleme

Yerleşik Office istemcisi, duyarlılık etiketlerini ve duyarlılık etiketi ilkesi ayarlarını siteden Microsoft 365 uyumluluk merkezi. 

Yerleşik Office istemcisini kullanmak için, uyumluluk merkezinden kullanıcılara yayımlanmış bir veya daha fazla etiket ilkeniz [](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) ve desteklenen bir etiket [Office.](#support-for-sensitivity-label-capabilities-in-apps)

Bu koşulların her ikisi de karşısa, ancak bu uygulamalara ve uygulamalara yerleşik etiketleri kapatmanız Windows Office, aşağıdaki Grup İlkesi ayarını kullanın:

1. Kullanıcı Yapılandırması **/Yönetim Şablonları/Microsoft Office 2016/Güvenlik Ayarları'na Ayarlar**.

2. Duyarlılık **etiketlerini uygulamak ve 0'a Office için Duyarlılık özelliğini Office'i** **ayarlayın**. 
 
Grup İlkesi kullanarak veya Office bulut [ilkesi hizmetini kullanarak bu ayarı dağıtın](/DeployOffice/overview-office-cloud-policy-service). Bu ayar, söz Office yeniden başlatıldığında etkin olur. 

Bu ayar Windows Office uygulamalarına özgü olduğundan, Windows'ta duyarlılık etiketlerini (Power BI gibi) veya diğer platformları (macOS, mobil cihazlar ve tabletler gibi) destekleyen diğer Web için Office. Kullanıcıların bazılarının veya tüm uygulamaların, tüm platformların duyarlılık etiketlerini görmelerini ve kullanmalarını istemiyorsanız, bu kullanıcılara duyarlılık etiketi ilkesi atamayın. 

### <a name="office-built-in-labeling-client-and-the-azure-information-protection-client"></a>Office etiketleme istemcisini ve Azure Information Protection istemcisini içerir

Kullanıcıların Windows bilgisayarlarında [Azure Information Protection (AIP)](/azure/information-protection/rms-client/aip-clientv2) istemcisi yüklüyse, onları destekleyen Windows Office varsayılan olarak [yerleşik etiketler kapalıdır](#labeling-client-for-desktop-apps). AIP istemcisi tarafından kullanılan yerleşik Office bir eklenti kullanmamalarının nedeni, daha fazla kararlılık ve daha iyi performanstır. Ayrıca, gelişmiş sınıflayıcılar gibi en son özellikleri de desteklerler.

AIP istemcisiyle seçenekleri etiketleme hakkında daha fazla bilgi edinmek için bkz. Office uygulamaları için AIP eklentisinde yerleşik [MIP etiketlemeyi seçme.](sensitivity-labels-aip.md)

## <a name="office-file-types-supported"></a>Office dosya türleri destekle

Word, Excel ve PowerPoint dosyaları için yerleşik etiketlemesi olan Office uygulamaları Open XML biçimini (.docx ve .xlsx gibi) destekler ancak Microsoft Office 97-2003 biçimi (.doc ve .xls gibi), Belge Biçimini Aç (.odt ve .ods gibi) veya diğer biçimler için desteklemez. Bir dosya türü yerleşik etiketleme için desteklenmiyorsa Duyarlılık düğmesi dosya dosyasında Office uygulaması.

Azure Information Protection birleşik etiketleme istemcisi hem Open XML biçimini hem de Microsoft Office 97-2003 biçimini destekler. Daha fazla bilgi için, [o istemcinin yönetici kılavuzunda Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-file-types) birleşik etiketleme istemcisi tarafından desteklenen dosya türlerine bakın.

Diğer etiketleme çözümleri için, desteklenen dosya türleri için onların belgelerine bakın.

## <a name="protection-templates-and-sensitivity-labels"></a>Koruma şablonları ve duyarlılık etiketleri

Yerleşik etiketleme [kullanırken](/azure/information-protection/configure-policy-templates), Office 365 İleti Şifrelemesi için tanımladığınız şablonlar gibi Office tanımlı koruma şablonları Office uygulamalarda görünmez. Bu basitleştirilmiş deneyim, şifreleme etkinleştirilmiş duyarlılık etiketlerine aynı ayarların dahil olması nedeniyle koruma şablonu seçmeye gerek olmadığını yansıtıyor.

EncryptionTemplateId parametresiyle [New-Label](/powershell/module/exchange/new-label) cmdlet'ini kullanarak var olan bir şablonu *duyarlılık etiketine dönüştürebilirsiniz* .

## <a name="information-rights-management-irm-options-and-sensitivity-labels"></a>Bilgi Hakları Yönetimi (IRM) seçenekleri ve duyarlılık etiketleri

Şifreleme uygulamak için yapılandırılan duyarlılık etiketleri kullanıcıların karmaşıklığını ortadan kaldırır ve kendi şifreleme ayarlarını belirtir. Birçok Office, bu tek tek şifreleme ayarları, Bilgi Hakları Yönetimi (IRM) seçenekleri kullanılarak kullanıcılar tarafından el ile yapılandırılabilir. Örneğin, Windows:

- Belge için: **FileInfoProtect** >  >  **DocumentRestrict Access** > 
- e-posta için: Seçenekler **sekmesinden** > **tıklayın** 
  
Kullanıcılar başlangıçta bir belgeyi veya e-postayı etiketleyece, kendi şifreleme ayarlarıyla etiket yapılandırma ayarlarınızı geçersiz kılar. Örneğin:

- Kullanıcı belgeye **Gizli \ Tüm Çalışanlar** etiketini uygular ve bu etiket, kuruluşta tüm kullanıcılara şifreleme ayarları uygulayacak şekilde yapılandırılır. Bu kullanıcı, iRM ayarlarını, kuruluş dışındaki bir kullanıcıya erişimi kısıtlamak için el ile yapılandırıyor. Sonuç, Gizli **\** Tüm Çalışanlar ve şifrelenmiş olarak etiketlenmiş bir belgedir, ancak organizasyondu kullanıcılar beklendiği gibi bu belgeyi aç aşağıdakiler.

- Kullanıcı e-postaya Yalnızca Gizli **\** Alıcılar etiketini uygular ve bu e-posta, Iletme şifreleme ayarının **uygulanacağı şekilde yapılandırılır**. Yeni Outlook, bu kullanıcı Encrypt-Only için IRM ayarını el ile seçer. Sonuçta, e-posta şifrelenmiş olarak kalırken, Gizli \ Yalnızca Alıcılar etiketine sahip olan alıcılar **tarafından iletebilirsiniz** .
    
    Özel durum olarak Web üzerinde Outlook, Şifrele menüsündeki seçenekler kullanıcının o anda seçili  olan etiketin ne zaman şifrelemeyi uygularsa seçilene kadar kullanılamaz.

- Kullanıcı belgeye **Genel** etiketini uygular ve bu etiket şifrelemeyi uygulayacak şekilde yapılandırılmamış. Bu kullanıcı belgeye erişimi kısıtlamak için IRM ayarlarını el ile yapılandırmış olur. Sonuç Genel etiketli bir belgedir ancak bazı kullanıcıların dosyayı  beklendiği gibi açmayacak şekilde şifrelemeyi de uygular.

Belge veya e-posta zaten etiketli ise, içerik zaten şifrelenmiş değilse veya kullanım hakkı olan Dışarı Aktar veya Tam Denetime sahipse, kullanıcı bu eylemlerden herhangi [](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) birini gerçekleştirebilirsiniz. 

Anlamlı raporlamayla daha tutarlı bir etiket deneyimi için, kullanıcılara yalnızca belgeleri ve e-postaları korumak için etiketler uygulama konusunda yol gösterebilirsiniz. Örneğin:

- Kullanıcıların kendi izinlerini ataması gereken durumlar için, kullanıcıların kendi izinlerini [atamasına izin sağlayan etiketler sağlar.](encryption-sensitivity-labels.md#let-users-assign-permissions) 

- Şifreleme uygulanan bir etiket seçdikten sonra kullanıcıların şifrelemeyi el ile kaldırması yerine, kullanıcılara aynı sınıflandırmaya sahip ancak hiçbir şifreleme bulunmayan bir etikete gerek olduğunda bir alt etiket alternatifi sağlamalısınız. Örneğin:
    - **Gizli \ Tüm Çalışanlar**
    - **Gizli \ Herkes (şifreleme yok)**

- Kullanıcıların seçmesini engellemek için IRM ayarlarını devre dışı bırakmayı düşünebilirsiniz:
    - Outlook için Windows: 
        - Kayıt defteri anahtarları (DWORD:00000001) *DisableDNF ve* *DisableEO* HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\DRM
        - Şifrele düğmesi için Grup İlkesi **ayarının Varsayılan şifrelemeyi yapılandır seçeneğinin** yapılandırılmamış olduğundan emin olun
    - Mac için Outlook: 
        - Keys *DisableEncryptOnly ve* *DisableDoNotForward* güvenlik ayarları Belgelenmiş In [Set preferences for Mac için Outlook](/DeployOffice/mac/preferences-outlook)
    - Web üzerinde Outlook: 
        - [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) için belgelenmiş *BasitleştirilmişClientAccessDoNotForwardDisabled* ve *BasitleştirilmişClientAccessEncryptOnlyDisabled* parametreleri
    - Outlook iOS ve Android için güncelleştirmeler: Bu uygulamalar etiketleri olmadan şifreleme uygulama kullanıcılarını desteklemez, bu nedenle herhangi bir özelliği devre dışı bırakma işlemi yoktur.

> [!NOTE]
> Kullanıcılar SharePoint veya OneDrive'te depolanan etiketli belgeden el ile şifrelemeyi kaldırırsa ve SharePoint ve OneDrive'te [Office](sensitivity-labels-sharepoint-onedrive-files.md) dosyaları için duyarlılık etiketlerini etkinleştirdiyseniz, belgeye bir sonraki erişilildikten veya indirildikten sonra etiket şifrelemesi otomatik olarak geri yüklenir. 


## <a name="apply-sensitivity-labels-to-files-emails-and-attachments"></a>Dosyalara, e-postalara ve eklere duyarlılık etiketleri ekleme

Kullanıcılar, her belge veya e-posta için aynı anda yalnızca bir etiket uygulayabilir.

Ekleri olan bir e-posta iletisi etiketlenirken, ekler etiketi yalnızca e-posta iletisine uygulanan etiket şifreleme uygularsa ve ek bir Office belge zaten şifrelenmiş değilse devralın. Devralınan etiket şifrelemeyi uygulandığından, ek yeni şifrelenir.

E-posta iletisine uygulanan etiket şifreleme uygulamamışsa veya ek zaten şifrelenmişse, ek e-posta iletisinden etiketleri devralmaz.

Gizli etiketi şifrelemeyi **ve Genel** etiketinin şifreleme uygulamayacağı **etiket devralma örnekleri** :

- Kullanıcı yeni bir e-posta iletisi oluşturur ve bu **iletiye** Gizli etiketini uygular. Daha sonra etiketli veya şifrelenmiş olmayan bir Word belgesi eklerler. Devralmanın sonucunda, belge yeni Gizli olarak **etiketlenir ve** artık bu etiketten şifreleme uygulanır.

- Kullanıcı yeni bir e-posta iletisi oluşturur ve bu **iletiye** Gizli etiketini uygular. Daha sonra Genel etiketli bir **Word belgesi** eklerler ve bu dosya şifrelenmiş değildir. Devralmanın sonucunda belge Gizli olarak yeniden etiketlenir ve şimdi bu etiketten  şifreleme uygulanır.

## <a name="sensitivity-label-compatibility"></a>Duyarlılık etiketi uyumluluğu

**RMS ile** desteklenen uygulamalar: Duyarlılık etiketlerini desteklemez, RMS tarafından desteklenen bir uygulamada etiketli ve şifrelenmiş bir belge veya [e-posta](/azure/information-protection/requirements-applications#rms-enlightened-applications) açarsanız, uygulama yine de şifreleme ve hak yönetimini zorunlu kılınır.

**Azure Information Protection** istemcisiyle: Azure Information Protection istemcisini kullanarak belgelere ve e-postalara uygulayan duyarlılık etiketlerini Office Azure Information Protection istemcisini kullanarak görüntüp değiştirebilirsiniz.

**E-postaların diğer Office**: Yetkili kullanıcılar etiketli belgeleri ve e-postaları diğer Office. Bununla birlikte, etiketi yalnızca desteklenen sürümlerde veya Azure Information Protection Office istemcisini kullanarak  görüntüp değiştirebilirsiniz. Desteklenen Office uygulaması sürümleri önceki bölümde [listelenir](#support-for-sensitivity-label-capabilities-in-apps).

## <a name="support-for-sharepoint-and-onedrive-files-protected-by-sensitivity-labels"></a>Duyarlılık SharePoint tarafından korunan OneDrive ve dosya ekleme desteği

SharePoint veya OneDrive'daki belgeler için Office yerleşik etiketleme istemcisini Web üzerinde Office ile kullanmak için, SharePoint ve Office dosyaları için duyarlılık etiketlerini [etkinleştirmiş OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="support-for-external-users-and-labeled-content"></a>Dış kullanıcılar ve etiketli içerik desteği

Bir belgeyi veya e-postayı etiketle ilgili olarak, etiket kiracınızı ve bir etiket GUID'nizi içeren meta veriler olarak depolanır. Etiketli bir belge veya e-posta duyarlılık etiketlerini destekleyen bir Office uygulaması tarafından açıldığında, bu meta veriler okunur ve yalnızca kullanıcı aynı kiracıya aitse etiket kendi uygulamasında görüntülenir. Örneğin, Word, PowerPoint ve Excel için yerleşik etiketleme için, etiket adı durum çubuğunda görüntülenir. 

Başka bir ifadeyle, belgelerinizi farklı etiket adları kullanan başka bir kuruluşla paylaşırsanız, her kuruluş belgeye kendi etiketlerini uygulayabilir ve bu etiketi görebilir. Bununla birlikte, uygulanan etiketten aşağıdaki öğeler, kuruluş dışındaki kullanıcılar tarafından görülebilir:

- İçerik işaretleri. Etikette üst bilgi, alt bilgi veya filigran uygulandığında, bunlar doğrudan içeriğe eklenir ve biri bunları değiştirene veya silene kadar görünür kalır.

- Şifrelemenin uygulandığı etiketten temel koruma şablonunun adı ve açıklaması. Bu bilgiler, belgeyi açma yetkisi olan kişi ve bu belgenin kullanım hakları hakkında bilgi sağlamak için, belgenin en üstünde yer alan ileti çubuğunda görüntülenir.

### <a name="sharing-encrypted-documents-with-external-users"></a>Şifrelenmiş belgeleri dış kullanıcılarla paylaşma

Kendi kuruluş içinde yer alan kullanıcılara erişimi kısıtlamaya ek olarak, aynı hesapta hesabı olan diğer tüm kullanıcılara da Azure Active Directory. Öte yandan, kuruluşta Koşullu Erişim ilkeleri kullanıyorsa, dikkate alınacak [diğer noktalar için](#conditional-access-policies) bir sonraki bölüme bakın.

Kullanıcı Office doğrulandıktan sonra tüm [e-posta](/azure/information-protection/requirements-applications#rms-enlightened-applications) uygulamaları ve RMS ile olan diğer uygulamalar şifreli belgeleri açabilir. 

Dış kullanıcıların Azure Active Directory'de hesabı yoksa, kiracınıza konuk hesapları kullanarak kimlik doğrulaması kullanabilirler. Bu konuk hesapları, SharePoint ve OneDrive'ta Office dosyaları için duyarlılık etiketlerini etkinleştirdikten sonra SharePoint veya OneDrive'te paylaşılan [belgelere erişmek için de kullanılabilir](sensitivity-labels-sharepoint-onedrive-files.md):

- Bu konuk hesaplarını kendiniz oluşturabilirsiniz. Bu kullanıcıların zaten kullanıyor olduğu herhangi bir e-posta adresini belirtebilirsiniz. Örneğin, Gmail adresleri.
    
    Bu seçeneğin avantajı, şifreleme ayarlarında e-posta adreslerini belirterek belirli kullanıcılara erişimi ve hakları kısıtlamanızdır. Bunun dezavantajı, hesap oluşturma ve etiket yapılandırmasıyla eşgüdüm içinde çalışma için yönetim ek yüküdir.

- Bir diğer seçenek de kullanıcı SharePoint bağlantı OneDrive konuk hesaplarının otomatik olarak oluşturulduğunda azure [ad B2B](/sharepoint/sharepoint-azureb2b-integration) ile tümleştirmeyi kullanmaktır.
    
    Bu seçeneğin avantajı, hesaplar otomatik olarak oluşturulduğundan ve etiket yapılandırmasının daha basit olması nedeniyle en düşük yönetim yüküdir. Bu senaryoda, E-posta adreslerini önceden bilmiyorsanız[](encryption-sensitivity-labels.md#requirements-and-limitations-for-add-any-authenticated-users), Kimliği doğrulanmış tüm kullanıcı ekleme şifreleme seçeneğini belirtebilirsiniz. Bu ayarın, erişim ve kullanım haklarını belirli kullanıcılarla kısıtlamanıza izin vermemektedir.

Dış kullanıcılar, Windows ve [Microsoft 365 Uygulamaları (eski](/deployoffice/name-change) adı Office 365 uygulamaları) veya Office 2019'un tek başına sürümünü kullanıyorlarında, şifrelenmiş belgeleri açmak için de bir Microsoft hesabı kullanabilir. Diğer platformlarda daha da desteklenen Microsoft hesapları, şifrelenmiş belgeleri macOS (Microsoft 365 Uygulamaları, sürüm 16.42+), Android (sürüm 16.0.13029+) ve iOS'ta (sürüm 2.42+) açmak için de de desteklenmemektedir. Örneğin, kuruluş dışındaki bir kullanıcıyla şifrelenmiş bir belge paylaştığında, şifreleme ayarları dış kullanıcı için bir Gmail e-posta adresi belirtir. Bu dış kullanıcı Kendi Gmail e-posta adresini kullanan kendi Microsoft hesabını oluşturabilir. Ardından, bu hesap ile oturum açtıktan sonra, belgeyi açabilir ve onlar için belirtilen kullanım kısıtlamalarına göre düzenleyebilirler. Bu senaryoya örnek olarak izlenecek yol gösterirken bkz [. Korumalı belgeyi açma ve düzenleme](/azure/information-protection/secure-collaboration-documents#opening-and-editing-the-protected-document).

> [!NOTE]
> Microsoft hesabının e-posta adresi, şifreleme ayarlarına erişimi kısıtlamak için belirtilen e-posta adresiyle eşleşmeli.

Microsoft hesabı olan bir kullanıcı şifreli bir belgeyi bu yolla açtığında, aynı adı alan bir konuk hesabı yoksa kiracı için otomatik olarak bir konuk hesabı oluşturur. Konuk hesabı mevcut olduğunda, desteklenen masaüstü ve mobil Web üzerinde Office uygulamaları ile şifrelenmiş belgeleri açmanın yanı sıra SharePoint ve OneDrive'te belgeleri açmak için de Office kullanılabilir.

Bununla birlikte, yineleme gecikme süresi nedeniyle bu senaryoda otomatik konuk hesabı hemen oluşturulmaz. Kişisel e-posta adreslerini etiket şifreleme ayarlarınızın bir parçası olarak belirtirsanız, e-posta adresinizde ilgili konuk hesaplarını oluşturmanızı Azure Active Directory. Ardından bu kullanıcılara, bu hesabı kullanarak kuruluştan şifrelenmiş bir belge açmaları gerektiğini haber vermelerini sekleyebilirsiniz.

> [!TIP]
> Dış kullanıcıların desteklenen bir Office istemci uygulaması kullanmalarını, konuk hesaplarını oluşturduktan (belirli kullanıcılar için) sonra SharePoint ve OneDrive'tan bağlantıları paylaşmalarını veya [azure AD B2B ile SharePoint ve OneDrive](/sharepoint/sharepoint-azureb2b-integration-preview) tümleştirmesini kullanırkenn emin olamayacaksınız  (kimliği doğrulanmış tüm kullanıcılar için), dış kullanıcılarla güvenli işbirliğini destekleyen daha güvenilir bir yöntemdir.

### <a name="conditional-access-policies"></a>Koşullu Erişim ilkeleri

Koşullu Erişim ilkeleri, [Azure Active Directory uygulanmışsa](/azure/active-directory/conditional-access/overview), bu ilkelerin yapılandırmasını kontrol edin. İlkeler Bilgi **Koruması Microsoft Azure** ve ilke dış kullanıcılara genişletiliyorsa, bu dış kullanıcıların kendi kiracılarında Azure AD hesapları olsa bile kiracıda konuk hesapları olmalıdır.

Bu konuk hesabı olmadan, şifreli belgeyi açıp bir hata iletisiyle onu göremz. İleti metni, Azure Active Directory Dış kullanıcı olarak kiracıya hesabının eklenmeleri gerektiğini ve bu senaryo için Farklı bir kullanıcı hesabıyla oturum açma ve yeniden oturum açma bilgilerini yanlış olarak **bildirebilirsiniz**.

Kiracınız içinde, etiketleriniz tarafından şifrelenmiş belgeleri açması gereken dış kullanıcılar için konuk hesapları oluşturamazsanız ve yapılandırmazsanız, Azure Information Protection'ı Koşullu Erişim ilkelerinden kaldırmanız veya dış kullanıcıları ilkelerden çıkarmanız gerekir.

Duyarlılık etiketleri tarafından kullanılan şifreleme hizmeti olan Koşullu Erişim ve Azure Information Protection hakkında daha fazla bilgi için sık sorulan [Azure Information Protection'ın](/azure/information-protection/faqs#i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work) koşullu erişim için kullanılabilir bir bulut uygulaması olarak listelenmiş olduğunu görüyorum. Bu nasıl çalışır?

## <a name="when-office-apps-apply-content-marking-and-encryption"></a>Uygulama Office içerik işaretleme ve şifreleme uygulama

Office, kullandığınız uygulamaya bağlı olarak farklı bir duyarlılık etiketiyle içerik işaretleme ve şifreleme uygulayabilirsiniz.

| Uygulama | İçerik işaretleme | Şifreleme |
| --- | --- | --- |
| Tüm Excel Word, PowerPoint'i kullanma | Hemen | Hemen |
| PC Outlook Mac için Yükleme | Exchange Online e-postayı gönderdikten sonra | Hemen |
| Web üzerinde Outlook, iOS ve Android | Exchange Online e-postayı gönderdikten sonra | Exchange Online e-postayı gönderdikten sonra |
|

Bir uygulamanın dışındaki dosyalara duyarlılık etiketleri Office çözümler bunu, dosyaya meta veri etiket uygulayarak yapar. Bu senaryoda, etiketin yapılandırmasından işaretlenmesi dosyaya eklenmez ama şifreleme uygulanır. 

Bu dosyalar bir Office masaüstü uygulamasında açıldığında, içerik işaretleri dosya ilk kaydedilirken Azure Information Protection birleşik etiketleme istemcisi tarafından otomatik olarak uygulanır. Masaüstü, mobil veya web uygulamaları için yerleşik etiketlemeyi kullanıyorsanız, içerik işaretleri otomatik olarak uygulanmaz.

Bazı uygulamaların dışında duyarlılık Office senaryolar şunlardır:

- Azure Information Protection birleşik etiketleme istemcisini tarayıcı, Dosya Gezgini ve PowerShell 

- E-posta ve posta SharePoint için otomatik OneDrive

- Dosyadan etiketli ve şifrelenmiş veriler Power BI

- Bulut Uygulamaları için Microsoft Defender

Bu senaryolarda, Office uygulamaları kullanılarak, yerleşik etiketlemesi olan bir kullanıcı geçerli etiketi geçici olarak kaldırarak veya değiştirerek ve özgün etiketi yeniden uygulayarak etiketin içerik işaretlerini uygulayabilir.

### <a name="dynamic-markings-with-variables"></a>Değişkenlerle dinamik işaretler

> [!IMPORTANT]
> Office uygulamalarınız bu özelliği desteklemezse, işaretleri, değişkenleri çözümlemek yerine etiket yapılandırmasında belirtilen özgün metin olarak kullanırlar.
> 
> Azure Information Protection birleşik etiketleme istemcisi dinamik işaretlemeleri destekler. Bu sayfada yerleşik olarak Office için, desteklenen en düşük sürümler [için bu sayfanın](#support-for-sensitivity-label-capabilities-in-apps) Özellikler bölümünde yer alan tablolara bakın.

İçerik işaretleri için bir duyarlılık etiketi yapılandırıldığında, metin dizesinde üst bilgi, alt bilgi veya filigran için aşağıdaki değişkenleri kullanabilirsiniz:

| Değişken | Açıklama | Etiket uygulandığında örnek |
| -------- | ----------- | ------- |
| `${Item.Label}` | Uygulanan etiketin etiket görünen adı | **Genel**|
| `${Item.Name}` | Etiketlenmiş içeriğin dosya adı veya e-posta konusu | **Sales.docx** |
| `${Item.Location}` | Etiketlenmiş belgenin yolu ve dosya adı veya etiketlenmiş e-postanın e-posta konusu | **\\\Sales\2020\Q3\Report.docx**|
| `${User.Name}` | Etiketi uygulamayan kullanıcının görünen adı | **Richard Richarde** |
| `${User.PrincipalName}` | Etiketi uygulama kullanıcının Azure AD kullanıcı asıl adı (UPN) | **rsimone\@ contoso.com** |
| `${Event.DateTime}` | İçeriğin etiketli olduğu tarih ve saat diliminde, etiketi Microsoft 365 uygulamalarına yapan kullanıcının yerel saat diliminde, Office Online ve otomatik etiketleme ilkeleri için UTC (Eşgüdümli Evrensel Saat) | **10/8/2020 1:30** |

> [!NOTE]
> Bu değişkenlerin söz dizimi büyük/harfe duyarlıdır.

#### <a name="setting-different-visual-markings-for-word-excel-powerpoint-and-outlook"></a>Word, Excel, PowerPoint ve Outlook için farklı görsel işaretler Outlook

Ek bir değişken olarak, metin dizesinde "If.App" değişken deyimini kullanarak Office uygulama türü başına görsel işaretler yapılandırabilirsiniz ve **Word**, **Excel**, **PowerPoint** veya Outlook değerlerini **kullanarak uygulama türünü tanımlayabilirsiniz**. Ayrıca, aynı veri deyiminde birden fazla değer belirtmek için gereken bu değerleri kısaltmak If.App.

Aşağıdaki sözdizimini kullanın:

```
${If.App.<application type>}<your visual markings text> ${If.End}
```

Diğer dinamik görsel işaretler gibi söz dizimi de büyük/harfe duyarlıdır ve her uygulama türünün (WEPO) kısaltmalarını içerir.

Örnekler:

- **Yalnızca Word belgeleri için üst bilgi metnini ayarlama:**

    `${If.App.Word}This Word document is sensitive ${If.End}`

    Yalnızca Word belge üst bilgisinde, etiket "Bu Word belgesi hassas" üst bilgi metnini uygular. Diğer uygulama veya uygulamalara üst bilgi Office uygulanmaz.

- **Word, Excel ve Outlook için alt bilgi metnini ve metin için farklı alt bilgi PowerPoint:**

    `${If.App.WXO}This content is confidential. ${If.End}${If.App.PowerPoint}This presentation is confidential. ${If.End}`

    Word, Excel ve Outlook'de, etiket "Bu içerik gizlidir" alt bilgi metnini uygular. Başka PowerPoint, etiket "Bu sunu gizli." alt bilgi metnini uygular.

- **Word ve PowerPoint için belirli filigran metinlerini ayarlayın ve ardından Word, Excel ve PowerPoint:**

    `${If.App.WP}This content is ${If.End}Confidential`

    Word ve PowerPoint, etiket "Bu içerik Gizli" filigran metnini uygular. Tüm Excel, etiket "Gizli" filigran metnini uygular. Aynı Outlook, filigran metni uygulamaz çünkü görsel işaretler olarak filigranlar bu metinlerde Outlook.

## <a name="require-users-to-apply-a-label-to-their-email-and-documents"></a>Kullanıcıların e-postalarına ve belgelerine etiket uygulamalarını gerektirme

> [!IMPORTANT]
> 
> [Azure Information Protection birleşik etiketleme istemcisi,](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) zorunlu etiketleme olarak da bilinen bu yapılandırmayı destekler. En düşük sürümler için Office sayfasındaki [özellikler bölümünde yer](#support-for-sensitivity-label-capabilities-in-apps) alan tablolara bakın.
>
> E-postalarda değil de, belgeler için zorunlu etiketleme kullanmak için, bu belgelere özgü seçeneklerin nasıl yapılandır Outlook sonraki bölümde verilen yönergelere bakın.
> 
> Bir kaynakta zorunlu etiketleme kullanmak Power BI bkz[. Güvenlik etiketleri için zorunlu Power BI](/power-bi/admin/service-security-sensitivity-label-mandatory-label-policy).

İlke **ayarı Kullanıcıların** e-postalarına ve belgelerine etiket uygulamalarını gerekli olarak ata seçildiğinde, ilkeye atanan kullanıcıların aşağıdaki senaryolar altında bir duyarlılık etiketi seçmeleri ve uygulamaları gerekir:

- Azure Information Protection birleşik etiketleme istemcisi için:
    - Belgeler için (Word, Excel, PowerPoint): Etiketsiz bir belge kayded olduğunda veya kullanıcılar belgeyi kapatır.
    - E-Outlook için: Kullanıcılar şu anda etiketsiz bir ileti gönderir.

- Bu uygulamalarda yerleşik olarak Office için:
    - Belgeler için (Word, Excel, PowerPoint): Etiketsiz bir belge açıldığında veya kayded olduğunda.
    - E-postalar için (Outlook): Kullanıcılar şu anda etiketsiz bir e-posta iletisi gönderir.

Yerleşik etiketleme için ek bilgiler:

- Kullanıcılardan etiketsiz bir belge açtıklarından bir duyarlılık etiketi eklemeleri istendiğinde, bir etiket ekleyebilir veya belgeyi salt okunur modda açmayı seçebilirler.

- Zorunlu etiketleme yürürlüğe girdiyken, kullanıcılar belgelerden duyarlılık etiketlerini kaldırsa da mevcut bir etiketi değiştirebilir.

Bu ayarın ne zaman kullanımına ilişkin kılavuz için ilke ayarlarıyla ilgili [bilgilere bakın](sensitivity-labels.md#what-label-policies-can-do).

> [!NOTE]
> Zorunlu etiketlemeye ek olarak belgeler ve e-postalar için varsayılan etiket ilkesi ayarını da kullanıyorsanız: 
>
> Varsayılan etiket, zorunlu etiketlemeye göre her zaman önceliğe sahip olur. Bununla birlikte, belgeler için Azure Information Protection birleşik etiketleme istemcisi tüm etiketsiz belgelere varsayılan etiketi uygularken, yerleşik etiketleme, etiketsiz var olan belgelere değil yeni belgelere varsayılan etiketi uygular. Davranış olarak bu farklılık, varsayılan etiket ayarıyla zorunlu etiketlemeyi kullanırsanız, kullanıcıların yerleşik etiketlemeyi Azure Information Protection birleşik etiketleme istemcisini kullanmalarından daha sık kullanmaları için daha sık duyarlılık etiketi uygulamalarının istenecek olması anlamına gelir.
> 
> Şimdi de Office olan ve var olan belgeler için varsayılan etiketi destekleyen yerleşik uygulamaları kullanmanın bir diğer adı. Ayrıntılar için Word, [Excel](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) ve PowerPoint.

## <a name="outlook-specific-options-for-default-label-and-mandatory-labeling"></a>Outlook ve zorunlu etiketleme için özel seçenekler

Yerleşik etiketleme için, bu sayfada Outlook için özellikler tablosu ve Varsayılan etiket ve zorunlu etiketleme için farklı ayarlar satırlarını kullanarak [Outlook'in](#sensitivity-label-capabilities-in-outlook) bu özellikleri destekleyen en düşük sürümlerini **bulun**. Azure Information Protection birleşik etiketleme istemcisinin tüm sürümleri, bu Outlook seçenekleri destekler.

Outlook uygulaması, belgeler için varsayılan etiket ayarından farklı bir varsayılan etiket ayarını desteklediğinde:

- Microsoft 365 uyumluluk merkezi'un etiket ilkesi yapılandırmasında, E-postalara varsayılan etiket  uygulama sayfasında: Tüm etiketsiz e-postalara uygulanacak veya varsayılan etiket olmayacak duyarlılık etiketi tercihini belirtebilirsiniz. Bu ayar, yapılandırmanın Belgeler **için önceki İlke** ayarları sayfasındaki Bu etiketi varsayılan olarak **belgelere uygula** ayarından bağımsızdır.

Outlook uygulaması belgeler için varsayılan etiket ayarından farklı bir varsayılan etiket ayarını desteklemezse: Outlook her zaman etiket ilkesi yapılandırmasının Belgeler için ilke ayarları sayfasında bu etiketi varsayılan olarak uygula için belirttiğiniz değeri kullanır.

Aşağıdaki Outlook, zorunlu etiketlemeyi kapatmayı destekliyorsa:

- İlkenin etiket ilkesi yapılandırmasında Microsoft 365 uyumluluk merkezi İlke ayarları sayfasında: Kullanıcıların  e-postalarına veya belgelerine etiket uygulamalarını **gerektir'i seçin**. Ardından **SonrakiNext** >  **öğesini seçin** ve Kullanıcıların e-postalarına **etiket uygulamalarını gerektir onay kutusunu temizleyin**. Zorunlu etiketlemenin hem e-postalara hem de belgelere uygulanıyorsa onay kutusunu seçili tutabilirsiniz.

Outlook uygulaması zorunlu etiketlemeyi kapatmayı desteklemediğinde: Kullanıcıların e-postalarına veya belgelerine ilke ayarı olarak  etiket uygulamalarını gerektir seçeneğini ayarlarsanız, Outlook her zaman kullanıcılardan etiketsiz e-postalar için etiket seçmelerini ister.

> [!NOTE]
> [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy) veya [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy) cmdlet'lerini kullanarak PowerShell gelişmiş ayarlarını **OutlookDefaultLabel** ve **DisableMandatoryInOutlook'u** yapılandırdınız:
> 
> Bu PowerShell ayarları için seçtiğiniz değerler uyumluluk merkezinde etiket ilkesi yapılandırmasına yansıtılır ve bu ayarları destekleyen Outlook uygulamaları için otomatik olarak çalışır. Diğer PowerShell gelişmiş ayarları, yalnızca Azure Information Protection birleşik etiketleme istemcisi için desteklenmiş olarak kalır.

## <a name="auditing-labeling-activities"></a>Etiket etkinliklerini denetleme

Duyarlılık etiketi etkinlikleri tarafından oluşturulan denetim olayları hakkında bilgi için, Uyumluluk merkezinde denetim günlüğünde arama yapın bölümünde yer [](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) alan Duyarlılık etiketi etkinlikleri [bölümüne bakın](search-the-audit-log-in-security-and-compliance.md).

Bu denetim bilgileri, duyarlılık etiketlerinizin nasıl kullanılmış [](data-classification-content-explorer.md) olduğunu ve bu [](data-classification-activity-explorer.md) etiketli içeriğin nerede yer alıyor olduğunu anlamanıza yardımcı olmak için içerik gezgininde ve etkinlik gezgininde görsel olarak temsil edilen bilgilerdir. 

Denetim günlüğü kayıtlarını dışarı aktararak ve yapılandırarak, güvenlik bilgileri ve olay yönetimi (SIEM) yazılımı tercihi ile [özel raporlar da oluşturabilirsiniz](export-view-audit-log-records.md). Daha büyük ölçekli raporlama çözümleri için Bkz. [Office 365 Etkinlik API'si başvurusu](/office/office-365-management-api/office-365-management-activity-api-reference).

> [!TIP]
> Özel raporlar oluşturmanıza yardımcı olmak için aşağıdaki blog gönderileri'ne bakın:
> - [Microsoft 365 O365 Yönetim API'si aracılığıyla uyumluluk denetim günlüğü etkinlikleri - Bölüm 1](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/microsoft-365-compliance-audit-log-activities-via-o365/ba-p/2957171)
> - [Microsoft 365 O365 Yönetim API'si aracılığıyla uyumluluk denetim günlüğü etkinlikleri - Bölüm 2](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/microsoft-365-compliance-audit-log-activities-via-o365/ba-p/2957297)

## <a name="end-user-documentation"></a>Son kullanıcı belgeleri

- [Office'te dosyalarınıza ve e-postalarınıza duyarlılık etiketleri uygulama](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [E-Office'de duyarlılık etiketleriyle ilgili bilinen Office](https://support.microsoft.com/en-us/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Web'de dosyalarınıza ve e-postanıza otomatik olarak duyarlılık etiketleri Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [Otomatik olarak duyarlılık etiketleri uygulama veya öneriyle ilgili bilinen sorunlar](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)
