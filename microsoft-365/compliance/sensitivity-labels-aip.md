---
title: Azure Microsoft Bilgi Koruması Koruma (AIP) eklentisinde, Office uygulamaları için yerleşik etiket (MIP) etiketini seçme
f1.keywords:
- CSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Azure Information Protection (AIP) birleşik etiketleme istemcisini kullanırken, AIP eklentisini kullanmak yerine Office uygulamaları için yerleşik etiketleme kullanmanın avantajlarını öğrenin.
ms.openlocfilehash: 88849422d295cc7caf2eb39837f7f1bb82b7a378
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704732"
---
# <a name="why-choose-mip-built-in-labeling-over-the-aip-add-in-for-office-apps"></a>Office uygulamaları için AIP eklentisinde yerleşik MIP etiketlemeyi neden Office?

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Windows bilgisayarlarında [](sensitivity-labels.md) Microsoft 365 Uygulamaları'te duyarlılık etiketlerini kullanırken, Office uygulamalarına yerleşik olarak gelen etiketlemeyi veya [Azure Information Protection (AIP)](/azure/information-protection/rms-client/aip-clientv2) birleşik etiketleme istemcisinde yer alan bir eklentiyi kullanabilirsiniz. 

Yerleşik etiketleme, [Microsoft Bilgi Koruması (MIP)](information-protection-solution.md) dağıtımının temel taşını oluşturur, çünkü bu etiketleme teknolojisi platformlar genelinde (Windows, macOS, iOS, Android ve web) yanı sıra Microsoft uygulamaları ve hizmetleri genelinde ve daha birçok platformda genişler. Yerleşik etiketleme, veri sınıflandırması ve veri kaybı önleme (DLP) gibi diğer MIP özellikleriyle de çalışacak şekilde tasarlanmıştır.

Yerleşik etiketlerde birden çok etiket Office olduğundan, daha fazla kararlılık ve daha iyi performanstan yararlanabilirler. Ayrıca, gelişmiş sınıflayıcılar gibi en son MIP özelliklerini de desteklerler.

AIP istemcisi yüklü olduğunda, Office Windows'de yerleşik etiketleme kapalıdır. Aşağıdaki bölümde yer alan Yönergeler'i kullanarak bu varsayılan davranışı değiştirebilirsiniz: AIP eklentisini devre dışı bırakarak, Office [kullanabilirsiniz](#how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps).

AIP istemcisini aynı uygulama içinde yüklü ancak Office bırakarak AIP istemcisinin diğer özellikleri destekle kalır:

- Kullanıcıların tüm dosya türlerine etiket uygulayabilecekleri Dosya Gezgini'nde seçeneklere sağ tıklayın.

- Metin, resim veya PDF belgelerinin şifrelenmiş dosyalarını görüntüleyen bir görüntüleyici.

- Şirket içi dosyalarda hassas bilgileri bulmak ve bu dosyalarda etiketler ve şifrelemeler uygulamak veya kaldırmak için bir PowerShell modülü.

- Şirket içi veri depolarında depolanan hassas bilgileri keşfeden ve isteğe bağlı olarak bu içeriği etiket alan bir tarayıcı.

Etiketleri diğer uygulamaların ötesine genişleten bu özellikler hakkında Office için, AIP belgelerinde yer alan [Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide) birleşik etiketleme istemcisi yönetici kılavuzuna bakın.

Etiketlemeden bağımsız olarak, şifreleme hizmetinin kiracı düzeyinde yönetimi için [AIPService](/powershell/module/aipservice) PowerShell modülünü kullanmaya devamabilirsiniz. Örneğin, veri kurtarma şifrelemesini kaldırmanız, AIP istemcisi tarafından açılmış belgeleri izlemeniz ve iptalniz ve çevrimdışı erişim için kullanım lisansı geçerlilik dönemini yapılandırmanız için süper kullanıcı erişimini yapılandırabilirsiniz. Daha fazla bilgi için bkz [. PowerShell kullanarak Azure Information Protection'dan Korumayı Yönetme](/azure/information-protection/administer-powershell).

## <a name="decide-whether-to-use-built-in-labeling-for-office-apps-or-the-aip-add-in"></a>Bir uygulama veya AIP eklentisinde yerleşik Office kullanmaya karar verme

Artık AIP istemcisi bakım modunda [olduğu için](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/announcing-aip-unified-labeling-client-maintenance-mode-and/ba-p/3043613), aşağıdaki nedenlerden dolayı AIP eklentisini Office öneririz:

- Yeni etiketleme özelliği destek olmayacaktır.
- Eklentiler daha az kararlıdır, çünkü eklentilerin kilitlenmesi, kilitlenmesi veya eklentinin otomatik olarak devre dışı bırakılmasına neden Office eklentilerle çakışmaya neden olabilir.
- Eklenti olarak, daha yavaş çalışır ve kullanıcılar etiket gereksinimlerini atlayarak devre dışı bırakılabilir.
- Hata düzeltmeleri için Azure Information Protection istemcisinin yeniden yüklenmesi gerekir.
- Kullanıcılar için etiket oluşturma deneyimi, kullanıcıların diğer cihazlarında (macOS, iOS, Android) ve diğer cihazlardaki yerleşik etiketlerden biraz Web için Office. Bu fark, eğitim ve destek maliyetlerini artırabilir.
- Yalnızca yerleşik Office desteklenen, etiket özellikleriyle ilgili yeni özellikler zaten vardır ve liste [](#features-supported-only-by-built-in-labeling-for-office-apps)sürekli büyüyen bir listedir.

Windows Office uygulamalarınız için AIP eklentinizi yalnızca, kullanıcılarınıza zaten dağıttıysanız ve bunları yerleşik etiketlemeye geçirmek için zaman gerekirse kullanın. Ya da kullanıcıların yerleşik etiketleme tarafından desteklemeyen bir özellik de gerekir. Bu [özellikleri tanımlamanıza yardımcı](#feature-parity-for-built-in-labeling-and-the-aip-add-in-for-office-apps) olmak için bu sayfada yer alan özellik eşlik bilgilerini kullanın.

## <a name="features-supported-only-by-built-in-labeling-for-office-apps"></a>Yalnızca Office uygulamaları için yerleşik etiketlemeyle desteklenen özellikler

> [!NOTE]
> Birçok yeni etiketleme özelliği planlama veya geliştirme aşamasındadır, dolayısıyla bu bölümdeki listenin zaman içinde büyümelerini beklersiniz.

Bazı özellikler yalnızca Office uygulamaları için yerleşik etiketleme ile destekler ve AIP eklentisinde destek desteklemez. Şunlar dahildir:

- Otomatik ve önerilen etiketleme için:
    - Eğitilebilir sınıflayıcılar, Tam [Veri Eşleşmesi](classifier-learn-about.md) [(EDM)](sit-learn-about-exact-data-match-based-sits.md) ve adlandırılmış varlıklar içeren akıllı sınıflandırma [hizmetlerine erişim](named-entities-learn.md)
    - Kullanıcılar yazarak hassas bilgileri algılama
    - Word'de, kullanıcılar tanımlanan hassas içeriği gözden geçirebilirsiniz ve kaldırabilir
- Kullanıcıların izin atamasına izin verilen etiketler için, kullanıcılara veya gruplara farklı izinler (Okuma veya Değiştirme) izni verebilirsiniz
- Encrypt-Only-postalar için e-postalar için e-postalar
- Durum çubuğundaki etiketlerin görünürlüğü
- Hesap değiştirme desteği
- Kullanıcılar etiketlemeyi devre dışı bıraka

Kullanıcıların Word'de tanımlanan hassas içeriği nasıl gözden geçiremediklerini ve isteğe bağlı olarak nasıl kaldırabiliyorlarını gösteren örnek:

![Kullanıcılara duyarlılık içeriği olarak tanımlanan kredi kartı numaralarını kaldırma seçeneği de vardır.](../media/detect-sensitive-content.png)

Yerleşik etiketleme için yeni etiketleme özellikleri ne zaman kullanılabilir hale geldiğinde bilgi sahibi olmak için bkz. Uyumluluk ve [](whats-new.md) Duyarlılık **Microsoft 365'daki** özellikler.

## <a name="how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps"></a>Office uygulamaları için yerleşik etiketlemeyi kullanmak üzere AIP eklentisini devre dışı bırakma

AIP istemcisini, etiketleri Office uygulamalarının ötesine genişletip istemcinin eklentisini Office uygulamalarına yüklemesini önlemek için yüklemişseniz, [Office 2013 ve Office 2016](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off) programlarının grup ilkesi ayarları  nedeniyle Yüklenmedi altında belgelenmiş olarak Yönetilen eklentilerin Grup İlkesi ayarı Listesini kullanın.

Yerleşik etiketlemeyi destekleyen Windows Office uygulamalarınız için Microsoft Word 2016, Excel 2016, PowerPoint 2016 ve Outlook 2016 yapılandırmasını kullanın, AIP **istemcisi için aşağıdaki programlı tanımlayıcıları (ProgID) belirtin ve 0: Eklenti her zaman devre dışı bırakılır (engellenir)**

|Uygulama  |ProgID  |
|---------|---------|
|Word     |     `MSIP.WordAddin`    |
|Excel     |  `MSIP.ExcelAddin`       |
|PowerPoint     |   `MSIP.PowerPointAddin`      |
|Outlook | `MSIP.OutlookAddin` |
| | | 

Grup İlkesi kullanarak veya Office bulut [ilkesi hizmetini kullanarak bu ayarı dağıtın](/DeployOffice/overview-office-cloud-policy-service).

> [!IMPORTANT]
> Grup İlkesi ayarını kullanıyorsanız duyarlılık etiketlerini uygulamak ve görüntülemek için **Office'te** Duyarlılık özelliğini kullanın ve bunu **1** olarak ayarlayın. Bazı durumlarda AIP eklentisi Office uygulamalarına yüklenmeye devam ediyor olabilir. Eklentinin her uygulamaya yüklenmesini engellemek bu durumdan engellenmesine neden olur.

Alternatif olarak Word, Excel, PowerPoint ve Microsoft Azure'den Microsoft Azure Information Office **Protection** eklentisini etkileşimli olarak devre dışı Outlook. Bu yöntem tek bir bilgisayar ve geçici test için uygundur. Yönergeler için bkz[. Programlarda eklentileri görüntüleme, yönetme Office yükleme](https://support.office.com/article/16278816-1948-4028-91e5-76dca5380f8d).

Hangi yöntemi seçerseniz seçin, uygulamalar yeniden başlatıldığında Office geçerli olur.

> [!NOTE]
> Yerleşik etiketler, bir uygulamanın abonelik Office gerektirir. bazen "Office Kalıcı" olarak da adlandırılan tek başına Office sürümleriniz varsa, en son etiketleme yeteneklerinden yararlanmak için Microsoft 365 Uygulamaları for Enterprise [sürümüne yükseltmenizi öneririz](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

AIP eklentisini devre dışı bırakmak için bu yöntemi kullanırsanız, etiketi diğer uygulamaların ötesine genişletmek için AIP istemcisini Office unutmayın.

## <a name="feature-parity-for-built-in-labeling-and-the-aip-add-in-for-office-apps"></a>Yerleşik etiketleme ve Office uygulamaları için AIP eklentisinde özellik Office.

AIP eklentisinde desteklenen etiketleme özelliklerinin birçoğu artık yerleşik etiketleme tarafından da desteklenmiş durumdadır. Daha ayrıntılı bir özellik listesi, gerekebilecek minimum sürümler ve yapılandırma bilgileri için bkz. Office [uygulamalarına göre duyarlılık etiketlerini yönetme](sensitivity-labels-office-apps.md).

Daha fazla özellik planlanmaktadır ve geliştirme aşamasındadır. ilgilendiğiniz belirli bir özellik varsa, yol haritasını kontrol [edin Microsoft 365](https://aka.ms/MIPC/Roadmap) Özel Önizleme'de Microsoft Bilgi Koruması'e [Office göz önünde bulundurabilirsiniz](https://aka.ms/MIP/PreviewRing).

Yerleşik etiketleme tarafından henüz desteklememiş bir AIP eklentisinde yer alan bir özellik olup olmadığını belirlemek için aşağıdaki bilgileri kullanın:

|AIP eklenti özelliği veya özelliği|Yerleşik etiketleme |
|:-------------------------------|:----------------:|
|**Kategori: Genel** ||
|Merkezi raporlama ve denetim|![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](sensitivity-labels-office-apps.md#auditing-labeling-activities) |
|Kamu Bulutu|![Desteklenir.](../media/yes-icon.png)|
|Yönetici etiketlemeyi devre dışı bırakarak <br> - Tüm uygulamalar|  ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](sensitivity-labels-office-apps.md#office-built-in-labeling-client-and-other-labeling-solutions)|
|Yönetici etiketlemeyi devre dışı bırakarak <br> - Uygulama başına|  Planlama veya geliştirmede|
|**Kategori: Kullanıcı Deneyimi** ||
|Şeritteki Etiket düğmesi|![Desteklenir.](../media/yes-icon.png)|
|Etiket adları ve araç ipucu için çok dilli destek| ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](create-sensitivity-labels.md#example-configuration-to-configure-a-sensitivity-label-for-different-languages) |
|Etiket renkleri| Planlama veya geliştirmede |
|Araç çubuğunda etiketlerin görünürlüğü| Planlama veya geliştirmede |
|**Kategori: Etiketleme eylemleri** ||
|El ile etiketleme |  ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) |
|Zorunlu etiketleme | ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](sensitivity-labels.md#what-label-policies-can-do)|
|Varsayılan etiketleme <br> - Yeni ve var olan öğeler <br> - E-posta için ayrı ayarlar|  ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](sensitivity-labels.md#what-label-policies-can-do) |
|Önerilen veya otomatik |![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps) |
|Gerekçelendirmeyi düşürme |  ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](sensitivity-labels.md#what-label-policies-can-do)|
| **Kategori: Görsel işaretler** | |
|Üstbilgiler, altbilgiler, filigran| ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](sensitivity-labels.md#what-label-policies-can-do)|
|Dinamik işaretler| ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](sensitivity-labels-office-apps.md#dynamic-markings-with-variables)|
|Uygulama başına görsel işaretleme| ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](sensitivity-labels-office-apps.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook)|
| **Kategori: Şifreleme** | |
|Yönetici tanımlı izinler | ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](encryption-sensitivity-labels.md#assign-permissions-now) |
|Kullanıcı tanımlı izinler <br> - E-posta için İleri'Outlook <br> - Word, Excel ve PowerPoint için kullanıcı ve grup PowerPoint| ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](encryption-sensitivity-labels.md#let-users-assign-permissions)|
|Kullanıcı tanımlı izinler <br> - Word, Excel ve diğer etki alanlarını belirterek kuruluş genelinde PowerPoint | Planlama veya geliştirmede |
|Birlikte yazma ve Otomatik Kaydetme | ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](sensitivity-labels-coauthoring.md) |
|Çift anahtar şifrelemesi | Planlama veya geliştirmede |
|Kullanıcılar için belge iptali | Gözden geçirme altında |
| | |

### <a name="support-for-powershell-advanced-settings"></a>PowerShell gelişmiş ayarları desteği

AIP istemcisi, PowerShell gelişmiş ayarlarını kullanarak birçok [özelleştirmeyi destekler](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#configuring-advanced-settings-for-the-client-via-powershell). Bu gelişmiş ayarlardan bazıları artık [New-Label veya Set-Label](/powershell/module/exchange/new-label), [New-LabelPolicy veya Set-LabelPolicy'de](/powershell/module/exchange/new-labelpolicy) belgelenmiş olarak yerleşik etiketleme tarafından [destek almaktadır](/powershell/module/exchange/set-labelpolicy).[](/powershell/module/exchange/set-label)

Bununla birlikte, desteklenen ayarları yapılandırmanız için PowerShell'i kullanmak zorunda olmadığınız gibi, desteklenen ayarların standart yapılandırmada yer Microsoft 365 uyumluluk merkezi. Örneğin, varsayılan etiket için zorunlu etiketlemeyi kapatabilme Outlook farklı bir varsayılan etiket ayarlama özelliği.

AIP eklentisinde yer alan aşağıdaki yapılandırmalar henüz yerleşik etiketlemeyle destek desteklemez:

- [E-posta eklerinden etiket devralma](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments)
- [S/MIME for Outlook](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#configure-a-label-to-apply-smime-protection-in-outlook)
- [E-posta iletileri için oversharing Outlook](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)
- [Üst etiket için varsayılan alt etiket](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#specify-a-default-sublabel-for-a-parent-label)
- [Dış içerik işaretlemelerini kaldırma](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#remove-headers-and-footers-from-other-labeling-solution )

## <a name="features-not-planned-to-be-supported-by-built-in-labeling-for-office-apps"></a>Özellikler, Office uygulamaları için yerleşik etiketlemeyle destek Office planlanmaz

Yerleşik etiketlemeyle ilgili yeni özellikler her zaman eklense de, AIP Office eklentisi, yerleşik etiketleme için gelecek sürümlerde kullanılabilir olması planlanan aşağıdaki özellikleri destekler:

- Dosya ekleme gibi Microsoft Office 97-2003 biçimlerini .doc uygulama
- Kalıcı olarak bağlantısı olmayan bilgisayarlar
- Abonelik tabanlı Office Office bağımsız sürümleri ("Office Kalıcı" olarak da adlandırılır)

## <a name="next-steps"></a>Sonraki adımlar

Bu etiketleme özelliklerini oluşturma ve yapılandırma yönergeleri için bkz. [Duyarlılık etiketlerini ve ilkelerini oluşturma ve yapılandırma](create-sensitivity-labels.md).

> [!TIP]
> Dosyanın içinde zaten duyarlılık etiketleriniz Microsoft 365 uyumluluk merkezi, otomatik olarak varsayılan etiketler oluşturmak için uygun olmayacaktır. Ancak yine de yapılandırmalarına başvuru yapmak yararlı olabilir: [Varsayılan duyarlılık etiketleri](mip-easy-trials.md#default-sensitivity-labels). 
