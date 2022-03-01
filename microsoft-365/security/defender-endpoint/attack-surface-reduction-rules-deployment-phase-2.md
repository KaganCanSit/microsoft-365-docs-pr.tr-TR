---
title: ASR kuralları dağıtım aşaması 2 - test
description: Saldırı yüzeyini azaltma kuralları dağıtımınızı test etmek için rehberlik sağlar.
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
ms.collection: m365solution-scenario
ms.date: 1/18/2022
ms.openlocfilehash: cbcdee33fe9bc66c12c1bd060c69506595202ed9
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63014277"
---
# <a name="asr-rules-deployment-phase-2-test"></a>ASR kuralları dağıtım aşaması 2: test

ASR kuralları dağıtımınıza halka 1 ile başlama.

> [!div class="mx-imgBorder"]
> ![ASR kuralları test adımları](images/asr-rules-testing-steps.png)

## <a name="step-1-test-asr-rules-using-audit"></a>1. Adım: Denetimi kullanarak ASR kurallarını test edin

1. halkada, şampiyon kullanıcılarınız veya cihazlarınız ile başlayarak, ASR kurallarını Denetim olarak ayarlanmış kurallarla başlatarak test aşamasına başlayabilirsiniz. Normalde, tüm kuralları (Denetim'de) etkinleştirmeniz ve böylelikle test aşamasında hangi kuralların tetiklenir olduğunu belirlemeniz önerinizdir. Denetim olarak ayarlanmış kuralların, genellikle kuralın uygulandığı varlık veya varlıkların işlevselliğini etkilememektedir; ancak değerlendirme için günlüğe kaydedilmiş olaylar oluşturmaz; son kullanıcılar üzerinde hiçbir etkisi yoktur.

### <a name="configure-asr-rules-using-mem"></a>MEM kullanarak ASR Kurallarını yapılandırma

Özel ASR kurallarını Microsoft Endpoint Manager için MeM) Uç Nokta Güvenliği'ne kullanabilirsiniz.

1. Yönetim [Microsoft Endpoint Manager açma](https://endpoint.microsoft.com/#home)
2. **Endpoint SecurityAttack yüzeyini** >  **azaltma'ya gidin**.
3. İlke **Oluştur'a seçin**.
4. **Platform'da**, **Windows 10 ve sonra Profil'de** Saldırı yüzeyini azaltma **kuralları'na tıklayın**.
  
    > [!div class="mx-imgBorder"]
    > ![ASR kuralları profilini yapılandırma](images/asr-mem-create-profile.png)

5. **Oluştur'a tıklayın**.
6. Profil **oluştur bölmesinin** Temel **Bilgiler sekmesindeki** **Ad'da ilkeniz** için bir ad ekleyin. **Açıklama'da** ASR kuralları ilkeniz için bir açıklama ekleyin.
7. Yapılandırma ayarları **sekmesindeki** **Saldırı Yüzeyi Azaltma Kuralları'nın altında** tüm kuralları Denetim **modu olarak ayarlayın**.

    > [!div class="mx-imgBorder"]
    > ![ASR kurallarını Denetim moduna ayarlama](images/asr-mem-configuration-settings.png)

    >[!Note]
    >Bazı ASR kuralları modu listelerinin çeşitlemeleri vardır; _Engellendi ve_ _Etkin_ aynı işlevi sağlar.

8. [İsteğe bağlı] Kapsam **etiketleri bölmesinde** , etiket bilgilerini belirli cihazlara ekleyebilirsiniz. Doğru yöneticilerin doğru Intune nesnelerine doğru erişime ve görünürlüğüne sahip olduğundan emin olmak için rol tabanlı erişim denetimi ve kapsam etiketlerini de kullanabilirsiniz. Daha fazla bilgi: [Intune'da DAĞıTıMı için rol tabanlı erişim denetimi (RBAC) ve kapsam etiketlerini kullanın](/mem/intune/fundamentals/scope-tags).
9. Ödevler **bölmesinde** , profili kullanıcı veya cihaz gruplarınıza dağıtabilirsiniz veya "atabilirsiniz". Daha fazla bilgi: [Microsoft Intune'de cihaz Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)
10. Gözden Geçir **+ oluştur bölmesinde ayarlarınızı gözden** geçirebilirsiniz. Kuralları **uygulamak** için Oluştur'u tıklatın.

   > [!div class="mx-imgBorder"]
   > ![ASR kuralları ilkesi etkinleştirme](images/asr-mem-review-create.png)

ASR kuralları için yeni saldırı yüzeyi azaltma ilkeniz, Uç nokta güvenliği **ve güvenlik | Saldırı yüzeyini azaltma**.

   > [!div class="mx-imgBorder"]
   > ![Listelenen ASR kuralı ilkesi](images/asr-mem-my-asr-rules.png)

## <a name="step-2-understand-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>2. Adım: Microsoft 365 Defender portalında Saldırı yüzeyini azaltma kuralları raporlama sayfasını anlama

ASR kuralları raporlama sayfası portalda **Microsoft 365 Defender** >  **PortsAttack** >  **surface azaltma kuralları**. Bu sayfada üç sekme vardır:

- Algılamalar
- Yapılandırma
- Dışlama ekle

### <a name="detections-tab"></a>Algılamalar sekmesi

Algılanan denetim ve engellenen olayların 30 günlük zaman çizelgesini sağlar.

> [!div class="mx-imgBorder"]
> ![Saldırı yüzeyini azaltma kuralları algılamaları sekmesi](images/asr-defender365-01.png)

Saldırı Yüzeyi azaltma kuralları bölmesi, algılanan olaylara kural temelinde genel bir bakış sağlar.

>[!Note]
>ASR kuralları raporlarında bazı farklılıklar vardır. Microsoft, tutarlı bir deneyim sağlamak için ASR kuralları raporlarının davranışını güncelleştirme sürecindedir.

> [!div class="mx-imgBorder"]
> ![Saldırı yüzeyini azaltma kuralları kural algılamaları](images/asr-defender365-01b.png)

**Algılamalar sekmesini açmak için** Algılamaları **görüntüle'ye** tıklayın.

> [!div class="mx-imgBorder"]
> ![Saldırı yüzeyini azaltma kuralları algılamaları](images/asr-defender365-reports-detections.png)

**GroupBy ve** **Filtre** bölmesi aşağıdaki seçenekleri sağlar:

**GroupBy,** aşağıdaki gruplara ayarlanmış sonuçları döndürür:

- Grup yok
- Algılanan dosya
- Denetleme veya engelleme
- Kural
- Kaynak uygulama
- Cihaz
- Kullanıcı
- Publisher

> [!div class="mx-imgBorder"]
> ![Saldırı yüzeyini azaltma kuralları algılamaları GroupBy filtresi](images/asr-defender365-reports-detections.png)

**Filtre** , **sonuçların kapsamını yalnızca** seçili ASR kurallarına göre filtrelemenize olanak sağlayan Kurallara göre filtrele sayfasını açar:

> [!div class="mx-imgBorder"]
> ![Kurallarda saldırı yüzeyini azaltma kuralları algılamaları filtresi](images/asr-defender365-filter.png)

>[!Note]
>Microsoft Microsoft 365 Security E5 veya A5, Windows E5 veya A5 lisansınız varsa aşağıdaki bağlantı Microsoft Defender 365 Raporları > [Saldırı](https://security.microsoft.com/asr?viewid=detections) yüzeyini azaltmalar > Algılamalar sekmesini açar.

### <a name="configuration-tab"></a>Yapılandırma sekmesi

Listeler – bilgisayar başına – ASR kurallarının toplam durumu: Kapalı, Denetim, Engelle.

> [!div class="mx-imgBorder"]
> ![Saldırı yüzeyini azaltma kuralları Yapılandırma sekmesi](images/asr-defender365-configurations.png)

Yapılandırmalar sekmesinde, cihaz başına hangi ASR kurallarının etkinleştirildiğinden ve hangi modda ASR kurallarını gözden geçirmek istediğiniz cihazı seçerek tek tek kontrol edebilirsiniz.

> [!div class="mx-imgBorder"]
> ![Saldırı yüzeyini azaltma kuralları etkin ve mod](images/asr-defender365-configurations.settings.png)

**Başla bağlantısı**, ASR için Microsoft Endpoint Manager koruma ilkesi oluştur bildiğiniz veya değiştir bildiğiniz yönetim merkezini açar:

> [!div class="mx-imgBorder"]
> ![MEM'de saldırı yüzeyini azaltma kuralları](images/asr-defender365-05b-mem1.png)

Uç nokta güvenlik | Genel bakış: Saldırı **yüzeyini azaltma'yi seçin**:

> [!div class="mx-imgBorder"]
> ![MEM'de saldırı yüzeyini azaltma](images/asr-defender365-05b-mem2.png)

Uç Nokta Güvenliği | Saldırı yüzeyini azaltma bölmesi açılır:

> [!div class="mx-imgBorder"]
> ![Uç nokta güvenliği Asr bölmesi](images/asr-defender365-05b-mem3.png)

>[!Note]
>Microsoft Defender 365 E5 (veya Windows E5?) lisansınız varsa, bu bağlantı Microsoft Defender 365 Raporları > Saldırı yüzeyini azaltmalar > [Yapılandırmalar sekmesini](https://security.microsoft.com/asr?viewid=configuration) açar.

### <a name="add-exclusions"></a>Dışlama ekle

Bu sekmede, dışlama için algılanan varlıkları (örneğin, yanlış pozitif sonuçlar) seçmek için bir yöntem sağlar. Dışlamalar ek olduğunda, rapor beklenen etkinin özetini sağlar.

>[!Note]
> Microsoft Defender Virüsten Koruma AV dışlamaları ASR kuralları tarafından kabul edildi.  Bkz [. Uzantıyı, adı veya konumu temel alarak dışlamaları yapılandırma ve doğrulama](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

> [!div class="mx-imgBorder"]
> ![Uç nokta güvenliği Asr aracı](Images/asr-defender365-06d.png)

> [!Note]
>Microsoft Defender 365 E5 (veya Windows E5?) lisansınız varsa, bu bağlantı Microsoft Defender 365 Raporları > Saldırı yüzeyini azaltmalar > [Dışlamalar](https://security.microsoft.com/asr?viewid=exclusions) sekmesini açar.

### <a name="use-powershell-as-an-alternative-method-to-enable-asr-rules"></a>ASR kurallarını etkinleştirmek için alternatif bir yöntem olarak PowerShell kullanma

PowerShell'i MEM'nin alternatifi olarak kullanarak, özellik tam olarak etkinleştirilirse engellenmiş olacak uygulamaların kaydını görüntülemek için denetim modunda ASR kurallarını etkinleştirebilirsiniz. Ayrıca, normal kullanım sırasında kuralların ne sıklıkta kuralların kullanımdan kalkacakları hakkında da fikir de eldesiniz.

Denetim modunda saldırı yüzeyini azaltma kuralını etkinleştirmek için aşağıdaki PowerShell cmdlet'ini kullanın:

```PowerShell
Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
```

Saldırı `<rule ID>` yüzeyini [azaltma kuralının GUID değeri nerede?](attack-surface-reduction-rules-reference.md)

Denetim modunda eklenen tüm saldırı yüzeyini azaltma kurallarını etkinleştirmek için aşağıdaki PowerShell cmdlet'ini kullanın:

```PowerShell
(Get-MpPreference).AttackSurfaceReductionRules_Ids | Foreach {Add-MpPreference -AttackSurfaceReductionRules_Ids $_ -AttackSurfaceReductionRules_Actions AuditMode}
```

> [!TIP]
> Saldırı yüzeyini azaltma kurallarının kuruluşta nasıl çalışıı ile ilgili tam denetime sahip olmak için bu ayarı ağ cihazlarınıza dağıtmak üzere bir yönetim aracı kullansanız gerekir.

Ayarı yapılandırmak ve dağıtmak için Grup İlkesi, Intune veya mobil cihaz yönetimi (MDM) yapılandırma hizmet sağlayıcılarını (CSP) de kullanabilirsiniz. Saldırı yüzeyini azaltma kuralları ana [makalesinde daha fazla bilgi](attack-surface-reduction.md) bulabilirsiniz.

## <a name="use-windows-event-viewer-review-as-an-alternative-to-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>Windows portalında saldırı yüzeyini azaltma kuralları raporlama sayfasına alternatif olarak Etkinlik Görüntüleyicisi gözden geçirme Microsoft 365 Defender kullanın

Engellenmiş olan uygulamaları gözden geçirmek için Olay Görüntüleyicisi'ni açın ve Microsoft-Windows-Windows Defender/Operational günlüğünde Olay Kimliği 1121 için filtre kullanın. Aşağıdaki tabloda tüm ağ koruma olayları listele.

Olay Kimliği | Açıklama
-|-
 5007 | Ayarların değiştir olduğu olay
 1121 | Saldırı yüzeyini azaltma kuralı engelleme modundayken ortaya çıkan olay
 1122 | Denetim modunda saldırı yüzeyini azaltma kuralına müdahale olduğunda olay

## <a name="additional-topics-in-this-deployment-collection"></a>Bu dağıtım koleksiyonunda yer alan ek konular

[ASR kuralları dağıtımına genel bakış](attack-surface-reduction-rules-deployment.md)

[Aşama 1: Planlama](attack-surface-reduction-rules-deployment-phase-1.md)

[Aşama 3: Uygulama](attack-surface-reduction-rules-deployment-phase-3.md)

[Aşama 4: İşlemsellik](attack-surface-reduction-rules-deployment-phase-4.md)
