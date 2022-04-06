---
title: Saldırı yüzeyi azaltma (ASR) kuralları dağıtımı uygulama
description: Saldırı yüzeyi azaltma kuralları dağıtımınızı uygulamak için rehberlik sağlar.
keywords: Saldırı yüzeyi azaltma kuralları dağıtımı, ASR dağıtımı, ASR kurallarını etkinleştirme, ASR'yi yapılandırma, konak yetkisiz erişim önleme sistemi, koruma kuralları, açıktan yararlanma önleme kuralları, kötüye kullanıma karşı koruma kuralları, kötüye kullanma kuralları, bulaşma önleme kuralları, Uç Nokta için Microsoft Defender, ASR kurallarını yapılandırma
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 675d881c3737b67cfdc0207be85285f71455d65c
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666976"
---
# <a name="step-3-implement-asr-rules"></a>3. Adım: ASR kurallarını uygulayın

Saldırı yüzeyi azaltma (ASR) kurallarının uygulanması, ilk test halkasını etkin, işlevsel bir duruma taşır.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-implementation-steps.png" alt-text="ASR kurallarını uygulama yordamı" lightbox="images/asr-rules-implementation-steps.png":::
  

## <a name="step-1-transition-asr-rules-from-audit-to-block"></a>1. Adım: ASR Kurallarını Denetimden Engellemeye Geçiş

1. Denetim modundayken tüm dışlamalar belirlendikten sonra, tetiklenen en az olayı içeren kuraldan başlayarak bazı ASR kurallarını "engelleme" moduna ayarlamaya başlayın. Bkz. [Saldırı yüzeyi azaltma kurallarını etkinleştirme](enable-attack-surface-reduction.md).
2. Microsoft 365 Defender portalındaki raporlama sayfasını gözden geçirin; [bkz. Uç Nokta için Microsoft Defender'de tehdit koruma raporu](threat-protection-reports.md). Ayrıca ASR şampiyonlarınızdan gelen geri bildirimleri de gözden geçirin.
3. Dışlamaları daraltma veya gerektiğinde yeni dışlamalar oluşturma.
4. Sorunlu kuralları Denetim'e geri dönün.

  >[!Note]
  >Sorunlu kurallar (çok fazla kirlilik oluşturan kurallar) için, kuralları kapatmak veya Denetim'e geri dönmek yerine dışlamalar oluşturmak daha iyidir. Ortamınız için en iyi olanı belirlemeniz gerekir.

  >[!Tip]
  >Kullanılabilir olduğunda, kesintileri sınırlamak için kurallardaki Uyarı modu ayarından yararlanın. ASR kurallarını Uyarı modunda etkinleştirmek, son kullanıcı erişimini engellemeden tetiklenen olayları yakalamanıza ve olası kesintilerini görüntülemenize olanak tanır. Daha fazla bilgi edinin: [Kullanıcılar için uyarı modu](attack-surface-reduction.md#warn-mode-for-users).

### <a name="how-does-warn-mode-work"></a>Uyarı modu nasıl çalışır?

Uyarı modu etkili bir Şekilde Engelleme yönergesidir, ancak kullanıcının verilen akışın veya uygulamanın sonraki yürütmelerini "engellemesini kaldırma" seçeneğiyle birlikte. Uyarı modu cihaz, kullanıcı, dosya ve işlem birleşimi başına engellemeleri kaldırır. Uyarı modu bilgileri yerel olarak depolanır ve süresi 24 saattir.

### <a name="step-2-expand-deployment-to-ring-n--1"></a>2. Adım: Dağıtımı n + 1 kademesine genişlet

Kademe 1 için ASR kurallarını doğru yapılandırdığınızda, dağıtımınızın kapsamını bir sonraki halkaya genişletebilirsiniz (halka n + 1).

1- 3. adım olan dağıtım işlemi, izleyen her kademe için temelde aynıdır:

1. Denetim'de test kuralları
2. Microsoft 365 Defender portalında ASR ile tetiklenen denetim olaylarını gözden geçirin
3. Dışlamalar oluşturma
4. Gözden geçirme: Gerektiğinde dışlamaları daraltma, ekleme veya kaldırma
5. Kuralları "engelle" olarak ayarlayın
6. Microsoft 365 Defender portalındaki raporlama sayfasını gözden geçirin.
7. Dışlamalar oluşturun.
8. Sorunlu kuralları devre dışı bırakın veya yeniden Denetim'e geçin.

#### <a name="customize-attack-surface-reduction-rules"></a>Saldırı yüzeyi azaltma kurallarını özelleştirme

Saldırı yüzeyi azaltma kuralları dağıtımınızı genişletmeye devam ettikçe, etkinleştirdiğiniz saldırı yüzeyi azaltma kurallarını özelleştirmeyi gerekli veya yararlı bulabilirsiniz.

##### <a name="exclude-files-and-folders"></a>Dosya ve klasörleri dışlama

Saldırı yüzeyi azaltma kuralları tarafından değerlendirilen dosya ve klasörleri dışlamamayı seçebilirsiniz. Dışlandığında, bir saldırı yüzeyi azaltma kuralı dosyanın kötü amaçlı davranış içerdiğini algılasa bile dosyanın çalışması engellenmez.

Örneğin fidye yazılımı kuralını göz önünde bulundurun:

Fidye yazılımı kuralı, kurumsal müşterilerin iş sürekliliğini sağlarken fidye yazılımı saldırılarının risklerini azaltmasına yardımcı olmak için tasarlanmıştır. Varsayılan olarak, fidye yazılımı kural hataları uyarı tarafında ve henüz yeterli saygınlığa ve güvene ulaşmamış dosyalara karşı koruma sağlar. Yeniden başlatmak için fidye yazılımı kuralı yalnızca milyonlarca müşterilerimizin kullanım ölçümlerine bağlı olarak yeterli olumlu saygınlık ve yaygınlık kazanmamış dosyalarda tetikler. Her dosyanın "saygınlık ve güven" değerleri sorunlu olmayan kullanım arttıkça artımlı olarak yükseltildiğinden bloklar genellikle kendi kendine çözülür.

Blokların zamanında kendi kendine çözümlenmediği durumlarda, müşteriler _kendi riskleriyle_ self servis mekanizmasını veya dosyaların engellemesini kaldırmak için Risk Göstergesi (IOC) tabanlı "izin verilenler listesi" özelliğini kullanabilir.

> [!WARNING]
> Dosya veya klasörlerin dışlanması veya engeli kaldırıldığında güvenli olmayan dosyaların çalıştırılmasına ve cihazlarınıza bulaşmasına izin verebilir. Dosyaları veya klasörleri dışlama, saldırı yüzeyini azaltma kuralları tarafından sağlanan korumayı ciddi ölçüde azaltabilir. Bir kural tarafından engellenen dosyaların çalıştırılmasına izin verilir ve hiçbir rapor veya olay kaydedilmez.

Dışlama, dışlamalara izin veren tüm kurallar için geçerlidir. Tek bir dosya, klasör yolu veya kaynak için tam etki alanı adı belirtebilirsiniz. Ancak, bir dışlamayı belirli bir kuralla sınırlayamazsınız.

Dışlama yalnızca dışlanan uygulama veya hizmet başlatıldığında uygulanır. Örneğin, zaten çalışmakta olan bir güncelleştirme hizmeti için bir dışlama eklerseniz, hizmet durdurulup yeniden başlatılana kadar güncelleştirme hizmeti olayları tetiklemeye devam eder.

Saldırı yüzeyini azaltma, ortam değişkenlerini ve joker karakterleri destekler. Joker karakterleri kullanma hakkında daha fazla bilgi için bkz. [Dosya adı ve klasör yolu veya uzantı dışlama listelerindeki joker karakterleri kullanma](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists).
Algılanmaması gerektiğini inandığınız dosyaları algılayan kurallarla ilgili sorunlarla karşılaşıyorsanız, [kuralı test etmek için denetim modunu kullanın](evaluate-attack-surface-reduction.md).

Her kuralla ilgili ayrıntılar için [saldırı yüzeyi azaltma kuralları başvuru](attack-surface-reduction-rules-reference.md) konusuna bakın.

##### <a name="use-group-policy-to-exclude-files-and-folders"></a>Dosyaları ve klasörleri dışlamak için grup ilkesi kullanma

1. grup ilkesi yönetim bilgisayarınızda [grup ilkesi Yönetim Konsolu'nu](https://technet.microsoft.com/library/cc731212.aspx) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'yi** seçin.

2. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin ve **Yönetim şablonları'na** tıklayın.

3. **Saldırı yüzeyini azaltma** Microsoft Defender Exploit Guard **Microsoft Defender Virüsten Koruma** \> **bileşenleri** \> **Windows** \> için ağacı genişletin.

4. **Saldırı yüzeyi azaltma Kuralları'ndan dosyaları ve yolları dışla** ayarına çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. **Göster'i** seçin ve **Değer adı** sütununa her dosyayı veya klasörü girin. Her öğe için **Değer** sütununa **0** girin.

> [!WARNING]
> **Değer adı** sütunu veya **Değer** sütunu için desteklenmediğinden tırnak işaretleri kullanmayın.

##### <a name="use-powershell-to-exclude-files-and-folders"></a>Dosyaları ve klasörleri dışlamak için PowerShell kullanma

1. Başlat menüsü **powershell** yazın, **Windows PowerShell** sağ tıklayın ve **Yönetici olarak çalıştır'ı** seçin.

2. Aşağıdaki cmdlet'i girin:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

    Listeye daha fazla klasör eklemek için kullanmaya `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` devam edin.

    > [!IMPORTANT]
    > Listeye uygulama eklemek veya eklemek için kullanın `Add-MpPreference` . cmdlet'ini `Set-MpPreference` kullanmak varolan listenin üzerine yazılır.

##### <a name="use-mdm-csps-to-exclude-files-and-folders"></a>Dosyaları ve klasörleri dışlamak için MDM CSP'lerini kullanma

Dışlama eklemek için [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) yapılandırma hizmeti sağlayıcısını (CSP) kullanın.

##### <a name="customize-the-notification"></a>Bildirimi özelleştirme

Bir kuralın tetiklenip bir uygulama veya dosyayı engellemesi için bildirimi özelleştirebilirsiniz. [Windows Güvenliği](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center#customize-notifications-from-the-windows-defender-security-center) makalesine bakın.

## <a name="additional-topics-in-this-deployment-collection"></a>Bu dağıtım koleksiyonundaki ek konular

[ASR kuralları dağıtım önkoşulları](attack-surface-reduction-rules-deployment.md)

[1. Adım: ASR kuralları dağıtımını planlayın](attack-surface-reduction-rules-deployment-plan.md)

[2. Adım: ASR kurallarını test edin](attack-surface-reduction-rules-deployment-test.md)

[4. Adım: ASR kurallarını kullanıma hazır hale getirin](attack-surface-reduction-rules-deployment-operationalize.md)
