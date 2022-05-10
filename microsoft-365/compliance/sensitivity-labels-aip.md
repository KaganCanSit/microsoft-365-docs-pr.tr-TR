---
title: Azure Information Protection (AIP) eklentisi üzerinden Office uygulamalar için Microsoft Purview Information Protection yerleşik etiketlemeyi seçin
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
description: Azure Information Protection (AIP) birleşik etiketleme istemcisini kullandığınızda, AIP eklentisi yerine Office uygulamalar için yerleşik etiketleme kullanmanın avantajlarını anlayın.
ms.openlocfilehash: 161f05c1f9c27723ff4940087c715e0556484b79
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65287144"
---
# <a name="why-choose-built-in-labeling-over-the-aip-add-in-for-office-apps"></a>neden Office uygulamalar için AIP eklentisi yerine yerleşik etiketlemeyi seçmelisiniz?

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Windows bilgisayarlardaki Microsoft 365 Uygulamaları [duyarlılık etiketlerini](sensitivity-labels.md) kullandığınızda, Office uygulamalarında yerleşik olarak bulunan etiketlemeyi veya [Azure Information Protection (AIP) birleşik etiketleme istemcisinden bir eklentiyi](/azure/information-protection/rms-client/aip-clientv2) kullanabilirsiniz. 

Yerleşik etiketleme[, Microsoft Purview bilgi koruma dağıtımının](information-protection-solution.md) temel taşını oluşturur çünkü bu etiketleme teknolojisi hem platformlar (Windows, macOS, iOS, Android ve web) hem de Microsoft uygulamaları ve hizmetleri ve ötesinde genişler. Yerleşik etiketleme ayrıca veri sınıflandırma ve Microsoft Purview veri kaybı önleme (DLP) gibi diğer Microsoft Purview özellikleriyle çalışacak şekilde tasarlanmıştır.

Yerleşik etiketler Office Eklentisi kullanmadığından daha fazla kararlılık ve daha iyi performanstan yararlanırlar. Ayrıca gelişmiş sınıflandırıcılar gibi en son Microsoft Purview özelliklerini de destekler.

Varsayılan olarak, AIP istemcisi yüklendiğinde Windows uygulamalar için Office yerleşik etiketleme kapatılır. Aşağıdaki [AIP eklentisini Office uygulamalar için yerleşik etiketlemeyi kullanmak üzere devre dışı bırakma](#how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps) bölümündeki yönergeleri kullanarak bu varsayılan davranışı değiştirebilirsiniz.

AIP istemcisini Office uygulamalarda yüklü ancak devre dışı durumda tuttuğunuzda, AIP istemcisinin diğer özellikleri desteklenmeye devam eder:

- Kullanıcıların tüm dosya türlerine etiket uygulaması için Dosya Gezgini seçeneklerine sağ tıklayın.

- Metin, resim veya PDF belgeleri için şifrelenmiş dosyaları görüntüleyen bir görüntüleyici.

- Şirket içindeki dosyalardaki hassas bilgileri bulmak ve bu dosyalardan etiket ve şifreleme uygulamak veya kaldırmak için bir PowerShell modülü.

- Şirket içi veri depolarında depolanan hassas bilgileri bulmak ve ardından isteğe bağlı olarak bu içeriği etiketlemek için bir tarayıcı.

Etiketlemeyi Office uygulamaların ötesine genişleten bu özellikler hakkında daha fazla bilgi için AIP belgelerindeki [Azure Information Protection birleşik etiketleme istemcisi yönetici kılavuzuna](/azure/information-protection/rms-client/clientv2-admin-guide) bakın.

Etiketlemeden bağımsız olarak, şifreleme hizmetinin kiracı düzeyinde yönetimi için [AIPService](/powershell/module/aipservice) PowerShell modülünü kullanmaya devam edebilirsiniz. Örneğin, veri kurtarma için şifrelemeyi kaldırmanız gerektiğinde süper kullanıcı erişimini yapılandırın, AIP istemcisi tarafından açılmış belgeleri izleyin ve iptal edin ve çevrimdışı erişim için kullanım lisansı geçerlilik süresini yapılandırın. Daha fazla bilgi için bkz. [PowerShell kullanarak Azure Information Protection korumasını yönetme](/azure/information-protection/administer-powershell).

## <a name="decide-whether-to-use-built-in-labeling-for-office-apps-or-the-aip-add-in"></a>Office uygulamaları için yerleşik etiketlemenin mi yoksa AIP eklentisinin mi kullanılacağına karar verme

AIP istemcisi [bakım modunda](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/announcing-aip-unified-labeling-client-maintenance-mode-and/ba-p/3043613) olduğuna göre, aşağıdaki nedenlerle Office uygulamalar için AIP eklentisini kullanmanızı önermiyoruz:

- Yeni etiketleme özellikleri desteklenmeyecektir.
- Eklentiler, Office uygulamaların kilitlenmesine, kilitlenmesine veya eklentinin otomatik olarak devre dışı bırakılmasına neden olabilecek diğer eklentilerle çakışabileceğinden daha az kararlıdır.
- Eklenti olarak daha yavaş çalışır ve etiketleme gereksinimlerini atlamak için kullanıcılar tarafından devre dışı bırakılabilir.
- Tüm hata düzeltmeleri için Azure Information Protection istemcisinin yeniden yüklenmesi gerekir.
- Kullanıcılar için etiketleme deneyimi, kullanıcıların diğer cihazlarında (macOS, iOS, Android) ve Web için Office kullandıkları yerleşik etiketlerden biraz farklıdır. Bu fark, eğitim ve destek maliyetlerini artırabilir.
- Yalnızca [yerleşik etiketleme tarafından desteklenen](#features-supported-only-by-built-in-labeling-for-office-apps) yeni Office etiketleme özellikleri kullanıma sunuldu ve liste sürekli büyüyor.

Windows Office uygulamalarınız için AIP eklentisini yalnızca kullanıcılara zaten dağıttıysanız ve bunları yerleşik etiketlemeye geçirmek için zamana ihtiyacınız varsa kullanın. Veya kullanıcıların yerleşik etiketleme tarafından desteklenmeyen bir özelliğe ihtiyacı vardır. Bu özellikleri belirlemenize yardımcı olması için bu sayfadaki [özellik eşlik bilgilerini](#feature-parity-for-built-in-labeling-and-the-aip-add-in-for-office-apps) kullanın.

## <a name="features-supported-only-by-built-in-labeling-for-office-apps"></a>Yalnızca Office uygulamaları için yerleşik etiketleme tarafından desteklenen özellikler

> [!NOTE]
> Birçok yeni etiketleme özelliği planlama veya geliştirme aşamasındadır, bu nedenle bu bölümdeki listenin zaman içinde büyümesi beklenir.

Bazı özellikler yalnızca Office uygulamalar için yerleşik etiketlemeyle desteklenir ve AIP eklentisi tarafından desteklenmez. Şunlar dahildir:

- Otomatik ve önerilen etiketleme için:
    - [Eğitilebilir sınıflandırıcılar](classifier-learn-about.md), [tam veri eşleşmesi (EDM)](sit-learn-about-exact-data-match-based-sits.md) ve [adlandırılmış varlıklar](named-entities-learn.md) içeren akıllı sınıflandırma hizmetlerine erişim
    - Kullanıcılar yazarken hassas bilgilerin algılanması
    - Word'de, kullanıcılar tanımlanan hassas içeriği gözden geçirebilir ve kaldırabilir
- Kullanıcıların izin atamasına izin veren etiketler için kullanıcılara veya gruplara farklı izinler (Okuma veya Değiştirme) verilebilir
- E-postalar için Encrypt-Only
- Durum çubuğunda etiketlerin görünürlüğü
- Hesap değiştirme desteği
- Kullanıcılar etiketlemeyi devre dışı bırakamıyor

Kullanıcıların Word'de tanımlanan hassas içeriği nasıl gözden geçirip isteğe bağlı olarak kaldırabileceğini gösteren örnek:

![Kullanıcılara duyarlılık içeriği olarak tanımlanan ve kaldırma seçeneğine sahip kredi kartı numaraları.](../media/detect-sensitive-content.png)

Yerleşik etiketleme için yeni etiketleme özellikleri kullanıma sunulduğunda haberdar olmak için bkz. [Microsoft Purview'daki yenilikler](whats-new.md) ve **Duyarlılık etiketleri** bölümleri.

## <a name="how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps"></a>Office uygulamaları için yerleşik etiketlemeyi kullanmak üzere AIP eklentisini devre dışı bırakma

Etiketlemeyi Office uygulamaların ötesine genişletmek için AIP istemcisini yüklediğinizde ancak istemci eklentisinin Office uygulamalarda yüklenmesini önlemek istiyorsanız, Office [2013 ve Office 2016 programlarının grup ilkesi ayarları nedeniyle Yüklü Eklenti Yok](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off) bölümünde belgelendiği gibi **yönetilen eklentiler listesi** grup ilkesi ayarını kullanın.

Yerleşik etiketlemeyi destekleyen Windows Office uygulamalarınız için Microsoft Word 2016, Excel 2016, PowerPoint 2016 ve Outlook 2016 yapılandırmasını kullanın, AIP istemcisi için aşağıdaki programlı tanımlayıcıları (ProgID) belirtin ve seçeneğini **0: Eklenti her zaman devre dışıdır (engellenir)**

|Uygulama  |Progıd  |
|---------|---------|
|Word     |     `MSIP.WordAddin`    |
|Excel     |  `MSIP.ExcelAddin`       |
|PowerPoint     |   `MSIP.PowerPointAddin`      |
|Outlook | `MSIP.OutlookAddin` |
| | | 

Bu ayarı grup ilkesi kullanarak veya [Office bulut ilkesi hizmetini](/DeployOffice/overview-office-cloud-policy-service) kullanarak dağıtın.

> [!IMPORTANT]
> **Duyarlılık etiketlerini uygulamak ve görüntülemek için Office'de Duyarlılık özelliğini kullan** grup ilkesi ayarını kullanıyorsanız ve bunu **1** olarak ayarlarsanız, AIP eklentisinin Office uygulamalarda hala yüklenebileceği bazı durumlar vardır. Eklentinin her uygulamada yüklenmesini engellemek, bunun olmasını önler.

Alternatif olarak, **word, Excel, PowerPoint ve Outlook** Microsoft Azure Information Protection Office Eklentisini etkileşimli olarak devre dışı bırakabilir veya kaldırabilirsiniz. Bu yöntem tek bir bilgisayar ve geçici test için uygundur. Yönergeler için bkz. [Office programlarında eklentileri görüntüleme, yönetme ve yükleme](https://support.office.com/article/16278816-1948-4028-91e5-76dca5380f8d).

Hangi yöntemi seçerseniz seçin, uygulamalar yeniden başlatıldığında değişiklikler Office etkinleşir.

> [!NOTE]
> Yerleşik etiketler, Office uygulamalarının abonelik sürümünü gerektirir. Bazen "Office Perpetual" olarak da adlandırılan tek başına Office sürümleriniz varsa, [en son etiketleme özelliklerinden](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) yararlanmak üzere Enterprise için Microsoft 365 Uygulamaları yükseltmenizi öneririz.

AIP eklentisini devre dışı bırakmak için bu yöntemi kullandığınızda, etiketlemeyi Office uygulamaların ötesine genişletmek için AIP istemcisini kullanmaya devam edebilirsiniz.

## <a name="feature-parity-for-built-in-labeling-and-the-aip-add-in-for-office-apps"></a>Yerleşik etiketleme için özellik eşliği ve Office uygulamalar için AIP eklentisi

AIP eklentisi tarafından desteklenen etiketleme özelliklerinin çoğu artık yerleşik etiketleme tarafından desteklenmektedir. Özelliklerin daha ayrıntılı listesi, gerekli olabilecek en düşük sürümler ve yapılandırma bilgileri için bkz. [Office uygulamalarında duyarlılık etiketlerini yönetme](sensitivity-labels-office-apps.md).

Daha fazla özellik planlanıyor ve geliştiriliyor. İlgilendiğiniz belirli bir özellik varsa [Microsoft 365 yol haritasını](https://aka.ms/MIPC/Roadmap) gözden geçirin ve [Office Özel Önizleme'de Microsoft Bilgi Koruması](https://aka.ms/MIP/PreviewRing) katılmayı düşünün.

AIP eklentisinden henüz yerleşik etiketleme tarafından desteklenmeyen bir özellik kullanıp kullanmadığınızı belirlemenize yardımcı olması için aşağıdaki bilgileri kullanın:

|AIP eklentisi özelliği veya özelliği|Yerleşik etiketleme |
|:-------------------------------|:----------------:|
|**Kategori: Genel** ||
|Merkezi raporlama ve denetim|![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](sensitivity-labels-office-apps.md#auditing-labeling-activities) |
|Kamu Bulutu|![Desteklenir.](../media/yes-icon.png)|
|Yönetici etiketlemeyi devre dışı bırakabilir <br> - Tüm uygulamalar|  ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](sensitivity-labels-office-apps.md#if-you-need-to-turn-off-built-in-labeling-in-office-apps-on-windows)|
|Yönetici etiketlemeyi devre dışı bırakabilir <br> - Uygulama başına|  Planlama veya geliştirme aşamasında|
|**Kategori: Kullanıcı Deneyimi** ||
|Şeritteki etiketleme düğmesi|![Desteklenir.](../media/yes-icon.png)|
|Etiket adları ve araç ipuçları için çok dilli destek| ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](create-sensitivity-labels.md#example-configuration-to-configure-a-sensitivity-label-for-different-languages) |
|Etiket renkleri| Planlama veya geliştirme aşamasında |
|Araç çubuğunda etiketlerin görünürlüğü| Planlama veya geliştirme aşamasında |
|**Kategori: Etiketleme eylemleri** ||
|El ile etiketleme |  ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) |
|Zorunlu etiketleme | ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](sensitivity-labels.md#what-label-policies-can-do)|
|Varsayılan etiketleme <br> - Yeni ve mevcut öğeler <br> - E-posta için ayrı ayarlar|  ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](sensitivity-labels.md#what-label-policies-can-do) |
|Önerilen veya otomatik |![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps) |
|Eski sürüme düşürme gerekçesi |  ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](sensitivity-labels.md#what-label-policies-can-do)|
| **Kategori: Görsel işaretler** | |
|Üst bilgiler, alt bilgiler, filigran| ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](sensitivity-labels.md#what-label-policies-can-do)|
|Dinamik işaretler| ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](sensitivity-labels-office-apps.md#dynamic-markings-with-variables)|
|Uygulama görseli işaretleme başına| ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](sensitivity-labels-office-apps.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook)|
| **Kategori: Şifreleme** | |
|Yönetici tanımlı izinler | ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](encryption-sensitivity-labels.md#assign-permissions-now) |
|Kullanıcı tanımlı izinler <br> - Outlook İçin İletme <br> - Word, Excel PowerPoint için kullanıcı ve grup özel izinleri| ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](encryption-sensitivity-labels.md#let-users-assign-permissions)|
|Kullanıcı tanımlı izinler <br> - Word, Excel PowerPoint için etki alanları belirterek kuruluş genelinde özel izinler | Planlama veya geliştirme aşamasında |
|Birlikte yazma ve Otomatik Kaydetme | ![Desteklenir.](../media/yes-icon.png) <br>[Daha fazla bilgi edinin](sensitivity-labels-coauthoring.md) |
|Çift anahtarlı şifreleme | Planlama veya geliştirme aşamasında |
|Kullanıcılar için belge iptali | İnceleme altında |
| | |

### <a name="support-for-powershell-advanced-settings"></a>PowerShell gelişmiş ayarları desteği

AIP istemcisi [, PowerShell gelişmiş ayarlarını](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#configuring-advanced-settings-for-the-client-via-powershell) kullanarak birçok özelleştirmeyi destekler. Bu gelişmiş ayarlardan bazıları artık [New-Label veya Set-Label](/powershell/module/exchange/new-label) ve [New-LabelPolicy ya da Set-LabelPolicy](/powershell/module/exchange/new-labelpolicy) belgelerinde belirtildiği gibi yerleşik etiketleme tarafından desteklenmektedir.[](/powershell/module/exchange/set-label)[](/powershell/module/exchange/set-labelpolicy)

Ancak desteklenen ayarları yapılandırmak için PowerShell'i kullanmanıza gerek olmadığını fark edebilirsiniz çünkü bunlar Microsoft Purview uyumluluk portalından standart yapılandırmaya dahildir. Örneğin, Outlook için zorunlu etiketlemeyi kapatma ve farklı bir varsayılan etiket ayarlama olanağı.

AIP eklentisinden gelen aşağıdaki yapılandırmalar henüz yerleşik etiketleme tarafından desteklenmemektedir:

- [E-posta eklerinden etiket devralma](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments)
- [Outlook için S/MIME](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#configure-a-label-to-apply-smime-protection-in-outlook)
- [Outlook için açılan iletileri fazla paylaşma](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)
- [Üst etiket için varsayılan alt etiket](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#specify-a-default-sublabel-for-a-parent-label)
- [Dış içerik işaretlerini kaldırma](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#remove-headers-and-footers-from-other-labeling-solution )

## <a name="features-not-planned-to-be-supported-by-built-in-labeling-for-office-apps"></a>Office uygulamaları için yerleşik etiketleme tarafından desteklenmeyen özellikler

Yerleşik etiketlemeye yönelik yeni özellikler her zaman eklense de, AIP Office Eklentisi, yerleşik etiketleme için gelecek sürümlerde kullanıma sunulması planlanmayan aşağıdaki özellikleri destekler:

- etiketlerin .doc dosyaları gibi Microsoft Office 97-2003 biçimlerine uygulanması
- Kalıcı olarak bağlantısı kesilmiş bilgisayarlar
- Abonelik tabanlı değil, tek başına Office sürümleri ("Office Kalıcı" olarak da adlandırılır)

## <a name="next-steps"></a>Sonraki adımlar

Bu etiketleme özelliklerini oluşturma ve yapılandırma yönergeleri için bkz. [Duyarlılık etiketleri ve ilkeleri oluşturma ve yapılandırma](create-sensitivity-labels.md).

> [!TIP]
> Microsoft Purview uyumluluk portalında duyarlılık etiketleriniz zaten varsa, varsayılan etiketlerin otomatik olarak oluşturulması için uygun olmazsınız. Ancak, yapılandırmalarına başvurmayı yine de yararlı bulabilirsiniz: [Varsayılan duyarlılık etiketleri](mip-easy-trials.md#default-sensitivity-labels). 
