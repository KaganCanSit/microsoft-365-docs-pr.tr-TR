---
title: Saldırı yüzeyini azaltma (ASR) kuralları dağıtımı uygulama
description: Saldırı yüzeyini azaltma kuralları dağıtımınızı uygulamaya yönelik kılavuz sağlar.
keywords: Saldırı yüzeyini azaltma kuralları dağıtımı, ASR dağıtımı, asr kurallarını etkinleştirme, ASR'yi yapılandırma, izinsiz giriş engelleme sistemi, koruma kuralları, istismardan koruma kuralları, istismardan koruma kuralları, bulaşma önleme kuralları, Uç nokta için Microsoft Defender, ASR kurallarını yapılandırma
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
ms.openlocfilehash: 2ca83735eab465e3a5ec6b25156143fde1719c0a
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683131"
---
# <a name="step-3-implement-asr-rules"></a>3. Adım: ASR kurallarını uygulama

Saldırı yüzeyini azaltma (ASR) kurallarının uygulanması, ilk test halkayı etkin, işlevsel bir durum haline taşır.

> [!div class="mx-imgBorder"]
> ![ASR kuralları uygulama adımları](images/asr-rules-implementation-steps.png)

## <a name="step-1-transition-asr-rules-from-audit-to-block"></a>1. Adım: ASR Kurallarını Denetimden Engellemeye Geçiş

1. Tüm dışlamalar denetim modundayken belirlendikten sonra, bazı ASR kurallarını "engelleme" moduna ayarlamaya en az tetiklenen kuraldan başlayarak başlatın. Saldırı yüzeyini [azaltma kurallarını etkinleştirme" bkz](enable-attack-surface-reduction.md).
2. Microsoft 365 Defender portalında raporlama sayfasını gözden geçirme; bkz. [Uç Nokta için Microsoft Defender'da Tehdit koruması raporu](threat-protection-reports.md). AsR şampiyonlarından gelen geri bildirimleri de gözden geçirebilirsiniz.
3. Gereken şekilde dışlamaları geliştirin veya yeni dışlamalar oluşturun.
4. Sorunlu kuralları Yeniden Denetim'e geçiş.

  >[!Note]
  >Sorunlu kurallar (çok fazla gürültü yaratan kurallar) için, dışlamalar oluşturmak kuralları kapatmaktan veya Denetim'e geri dönmekten daha iyidir. Ortamınıza en uygun olan şeyi belirlemeniz gerekir.

  >[!Tip]
  >Kullanılabilir olduğunda, kesintileri sınırlamak için kurallarda Uyar modu ayarına sahip olun. Uyarı modunda ASR kurallarının etkinleştirilmesi, son kullanıcı erişimini engellemeden tetiklenen olayları yakalamanıza ve olası kesintilerini görüntülemeye olanak sağlar. Daha fazla bilgi: [Kullanıcılar için uyarı modu](attack-surface-reduction.md#warn-mode-for-users).

### <a name="how-does-warn-mode-work"></a>Uyarı modu nasıl çalışır?

Uyarı modu etkili bir şekilde Yönergeyi engelle seçeneğiyle birlikte, kullanıcıya verilen akış veya uygulamanın sonraki yürütmelerini "Engellemeyi kaldır" seçeneğiyle birlikte. Uyarı modu cihaz, kullanıcı, dosya ve süreç birleşimi başına engellemeyi kaldırır. Uyarı modu bilgileri yerel olarak depolanır ve 24 saat süresi vardır.

### <a name="step-2-expand-deployment-to-ring-n--1"></a>2. Adım: Dağıtımı n + 1 çaldıracak şekilde genişletin

1. halka için ASR kurallarını doğru yapılandırmış olduğunuzdan emin olun, dağıtımınız kapsamını bir sonraki halkada genişletebilirsiniz (n + 1 çaldır).

1. ve 3. adımlar izleyen her halka için dağıtım işlemi esas olarak aynıdır:

1. Denetim'de kuralları test etmek
2. Microsoft 365 Defender portalında ASR tarafından tetiklenen denetim olaylarını gözden geçirme
3. Dışlama oluşturma
4. Gözden Geçirme: Gerektiğinde dışlamaları geliştirme, ekleme veya kaldırma
5. Kuralları "engelle" olarak ayarlama
6. Raporlama portalında raporlama Microsoft 365 Defender.
7. Dışlama oluşturma.
8. Sorunlu kuralları devre dışı bırakma veya denetime geri dönme.

#### <a name="customize-attack-surface-reduction-rules"></a>Saldırı yüzeyini azaltma kurallarını özelleştirme

Saldırı alanı azaltma kuralları dağıtımınızı genişletmeye devam ettiyken etkinleştirmiş olduğunuz saldırı alanı azaltma kurallarını özelleştirmenin gerekli olduğunu veya yararlı olduğunu bulabilirsiniz.

##### <a name="exclude-files-and-folders"></a>Dosyaları ve klasörleri dışla

Saldırı yüzeyini azaltma kuralları ile dosya ve klasörlerin değerlendirilmesini dışlaabilirsiniz. Dışlanan bir saldırı yüzeyini azaltma kuralı dosyanın kötü amaçlı davranışlar içerdiğini algılasa bile dosyanın çalışıyor olması engellanmaz.

Örneğin fidye yazılımı kuralını düşünün:

Fidye yazılımı kuralı, kurumsal müşterilerin fidye yazılımı saldırılarını azaltmaya ve iş sürekliliğini sağlamaya yardımcı olmak için tasarlanmıştır. Varsayılan olarak, fidye yazılımı hataları uyarı tarafındadır ve henüz yeterli saygınlığı ve güveni elde edemeyen dosyalara karşı koruma sağlar. Fidye yazılımı kuralı, yalnızca milyonlarca müşterimizin kullanım ölçümlerine bağlı olarak, yeteri kadar pozitif itibarı ve yaygınlığı kazanmış olan dosyalar için tetiklenir. Genellikle, her dosyanın "itibarı ve güven" değerleri, sorunlu olmayan kullanım arttıkça artımlı olarak yükseltilir ve bu nedenle bloklar kendi kendine çözülür.

Blokların otomatik olarak zamanında çözümlenmezse, müşteriler kendileri gibi, self servis mekanizmayı veya Güvenlik  Göstergesi (IOC) tabanlı "izin listesine izin verme" özelliğini kullanarak dosyaların engellemesini kaldırabileceklerdir.

> [!WARNING]
> Dosyalar veya klasörler hariç tutarak veya engelini kaldırmak, güvenli olmayabilecek dosyaların çalışmasına ve cihazlarınıza bulaşarak bulaşarak devam olmasına neden olabilir. Dosyaları veya klasörleri dışlama, saldırı yüzeyini azaltma kuralları tarafından sağlanan korumayı ciddi ölçüde azaltabilir. Bir kural tarafından engellenmiş olan dosyaların çalışmasına izin verilir ve hiçbir rapor veya etkinlik kaydedimeyecektir.

Dışlama, dışlamalara izin veren tüm kurallar için geçerlidir. Tek bir dosya, klasör yolu veya kaynak için tam etki alanı adı belirtebilirsiniz. Öte yandan, dışlamaları belirli bir kuralla sınırlandıramazsiniz.

Dışlama, yalnızca dışlanan uygulama veya hizmet başlatıldığında uygulanır. Örneğin, zaten çalışan bir güncelleştirme hizmeti için dışlama eklersiniz, hizmet durdurulana ve yeniden başlatana kadar güncelleştirme hizmeti olayları tetiklemeye devam eder.

Saldırı yüzeyini azaltma, ortam değişkenlerini ve joker karakterleri destekler. Joker karakter kullanma hakkında bilgi için bkz. Dosya adı ve klasör yolu veya uzantı [dışlama listelerinde joker karakter kullanma](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists).
Algılanmaz olduğuna inandığınız dosyaları algılayan kurallarla ilgili sorunlarla karşılaşıyorsanız, kuralı test [etmek için denetim modunu kullanın](evaluate-attack-surface-reduction.md).

Her [kuralla ilgili ayrıntılar için saldırı yüzeyini](attack-surface-reduction-rules-reference.md) azaltma kuralları başvuru başlığına bakın.

##### <a name="use-group-policy-to-exclude-files-and-folders"></a>Dosyaları ve klasörleri dışarıda tutmak için Grup İlkesi kullanma

1. Grup İlkesi yönetim bilgisayarınızda Grup İlkesi Yönetim [Konsolu'nu](https://technet.microsoft.com/library/cc731212.aspx) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'yi **seçin**.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde** Bilgisayar **yapılandırması'ne gidin ve** Yönetim **şablonları'ne tıklayın**.

3. Saldırı yüzeyini **azaltmayı Windows bileşenleri Microsoft Defender Virüsten Koruma** \> **Microsoft Defender Exploit Guard** \>  \> **ağacı genişletin**.

4. Saldırı yüzeyini azaltma **Kuralları ayarındaki Dosyaları ve yolları hariç tut ayarına** çift tıklayın ve seçeneği Etkin olarak **ayarlayın**. **Göster'i** seçin ve Değer adı sütununa her **dosya veya klasörü** girin. Her **öğe için** Değer **sütununa** 0 girin.

> [!WARNING]
> Değer adı sütunu veya Değer sütunu için destek **sağlanmazken tırnak** içine **alın** .

##### <a name="use-powershell-to-exclude-files-and-folders"></a>Dosyaları ve klasörleri dışarıda tutmak için PowerShell kullanma

1. **PowerShell yazın ve** Başlat menüsü sağ tıklayın ve **Windows PowerShell Yönetici olarak** **çalıştır'ı seçin**.

2. Aşağıdaki cmdlet'i girin:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

    Listeye daha `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` fazla klasör eklemek için kullanmaya devam edin.

    > [!IMPORTANT]
    > Listeye `Add-MpPreference` uygulama eklemek veya listeye uygulama eklemek için kullanın. `Set-MpPreference` Cmdlet kullanmak, var olan listenin üzerine yazmaz.

##### <a name="use-mdm-csps-to-exclude-files-and-folders"></a>Dosya ve klasörleri dışarıda tutmak için MDM CSP'leri kullanma

Dışlama [eklemek için ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) yapılandırma servis sağlayıcısını (CSP) kullanın.

##### <a name="customize-the-notification"></a>Bildirimi özelleştirme

Kural tetiklendiğinde ve bir uygulama veya dosyayı engelleme durumlarının bildirimini özelleştirebilirsiniz. Aşağıdaki [Windows Güvenliği](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center#customize-notifications-from-the-windows-defender-security-center) bakın.

## <a name="additional-topics-in-this-deployment-collection"></a>Bu dağıtım koleksiyonunda yer alan ek konular

[ASR kuralları dağıtım önkoşulları](attack-surface-reduction-rules-deployment.md)

[1. Adım: ASR kuralları dağıtımını planlama](attack-surface-reduction-rules-deployment-plan.md)

[2. Adım: ASR kurallarını test edin](attack-surface-reduction-rules-deployment-test.md)

[4. Adım: ASR kurallarını işlem durumaleştirme](attack-surface-reduction-rules-deployment-operationalize.md)
