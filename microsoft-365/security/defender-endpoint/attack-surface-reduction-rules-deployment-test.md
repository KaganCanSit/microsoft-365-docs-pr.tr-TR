---
title: Saldırı yüzeyini azaltma (ASR) kuralları testi
description: Saldırı yüzeyi azaltma (ASR) kuralları dağıtımınızı test etmek için rehberlik sağlar.
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
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 8bfe3e0d36a02831b5673b92217152ce87804d0a
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66601300"
---
# <a name="test-attack-surface-reduction-asr-rules"></a>Saldırı yüzeyini azaltma (ASR) kuralları testi

Saldırı yüzeyi azaltma (ASR) kurallarının test edilmesi, kuralların herhangi bir kuralı etkinleştirmeden önce iş kolu işlemlerini engelleyecek olup olmadığını belirlemenize yardımcı olur. Küçük, denetimli bir grupla başlayarak, dağıtımınızı kuruluşunuz genelinde genişletirken olası iş kesintilerini sınırlayabilirsiniz.

Kademe 1 ile saldırı yüzeyi azaltma (ASR) kuralları dağıtımınıza başlayın.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-testing-steps.png" alt-text="ASR kuralları test adımları" lightbox="images/asr-rules-testing-steps.png":::
  
## <a name="step-1-test-asr-rules-using-audit"></a>1. Adım: Denetim kullanarak ASR kurallarını test edin

1. halkadaki şampiyon kullanıcılarınız veya cihazlarınızdan başlayarak, denetim olarak ayarlanmış kurallarla ASR kurallarını açarak test aşamasına başlayın. Genellikle, test aşamasında hangi kuralların tetiklendiğini belirleyebilmeniz için tüm kuralları (Denetim'de) etkinleştirmeniz öneridir. Denetim olarak ayarlanan kuralların genellikle kuralın uygulandığı varlığın veya varlıkların işlevselliğini etkilemediğini ancak değerlendirme için günlüğe kaydedilen olaylar oluşturduğunu unutmayın; son kullanıcılar üzerinde hiçbir etkisi yoktur.

### <a name="configure-asr-rules-using-mem"></a>MEM kullanarak ASR Kurallarını yapılandırma

Özel ASR kurallarını yapılandırmak için Microsoft Endpoint Manager (MEM) Uç Nokta Güvenliği'ni kullanabilirsiniz.

1. [Microsoft Endpoint Manager yönetim merkezini](https://endpoint.microsoft.com/#home) açın.
2. **Endpoint Security** > **Attack yüzey azaltma** bölümüne gidin.
3. **İlke Oluştur'u** seçin.
4. **Platform'da** **Windows 10 ve üzerini** seçin ve **Profil'de** **Saldırı yüzeyi azaltma kuralları'yı** seçin.
  
    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/asr-mem-create-profile.png" alt-text="ASR kuralları için profil oluşturma sayfası" lightbox="images/asr-mem-create-profile.png":::

5. **Oluştur'a** tıklayın.
6. **Profil oluştur** bölmesinin **Temel Bilgiler** sekmesindeki **Ad** alanına ilkeniz için bir ad ekleyin. **Açıklama'da** ASR kuralları ilkeniz için bir açıklama ekleyin.
7. **Yapılandırma ayarları** sekmesindeki **Saldırı Yüzeyi Azaltma Kuralları'nın** altında tüm kuralları **Denetim moduna** ayarlayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/asr-mem-configuration-settings.png" alt-text="ASR kurallarının Denetim moduna yapılandırılması" lightbox="images/asr-mem-configuration-settings.png":::

    >[!Note]
    >Bazı ASR kural modu listelerinde çeşitlemeler vardır; _Engellendi_ ve _Etkin_ aynı işlevi sağlar.

8. [İsteğe bağlı] **Kapsam etiketleri** bölmesinde, belirli cihazlara etiket bilgileri ekleyebilirsiniz. Ayrıca, doğru yöneticilerin doğru Intune nesnelere doğru erişime ve görünürlüğe sahip olduğundan emin olmak için rol tabanlı erişim denetimi ve kapsam etiketlerini de kullanabilirsiniz. Daha fazla bilgi edinin: [Intune'de dağıtılmış BT için rol tabanlı erişim denetimi (RBAC) ve kapsam etiketlerini kullanın](/mem/intune/fundamentals/scope-tags).
9. **Atamalar** bölmesinde, profili kullanıcı veya cihaz gruplarınıza dağıtabilir veya "atayabilirsiniz". Daha fazla bilgi edinin: [Microsoft Intune'de cihaz profilleri atama](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)
10. **Gözden Geçir ve oluştur** bölmesinde ayarlarınızı gözden geçirin. Kuralları uygulamak için **Oluştur'a** tıklayın.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/asr-mem-review-create.png" alt-text="Profil oluştur sayfası" lightbox="images/asr-mem-review-create.png":::

ASR kuralları için yeni saldırı yüzeyi azaltma ilkeniz **Uç nokta güvenliği | Saldırı yüzeyi azaltma**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/asr-mem-my-asr-rules.png" alt-text=" Saldırı yüzeyi azaltma sayfası" lightbox="images/asr-mem-my-asr-rules.png":::

## <a name="step-2-understand-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>2. Adım: Microsoft 365 Defender portalındaki Saldırı yüzeyi azaltma kuralları raporlama sayfasını anlama

ASR kuralları raporlama sayfası **, Microsoft 365 Defender portal** > **Raporları** > **Saldırı yüzeyi azaltma kuralları** bölümünde bulunur. Bu sayfada üç sekme vardır:

- Algılamalar
- Yapılandırma
- Dışlama ekleme

### <a name="detections-tab"></a>Algılamalar sekmesi

Algılanan denetim ve engellenen olayların 30 günlük zaman çizelgesini sağlar.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-01.png" alt-text="Saldırı yüzeyi azaltma kuralları algılamalar sekmesi" lightbox="images/asr-defender365-01.png":::

Saldırı Yüzeyi azaltma kuralları bölmesi, kural başına algılanan olaylara genel bir bakış sağlar.

>[!Note]
>ASR kuralları raporlarında bazı farklılıklar vardır. Microsoft, tutarlı bir deneyim sağlamak için ASR kuralları raporlarının davranışını güncelleştirme sürecindedir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-01b.png" alt-text="Saldırı yüzeyi azaltma kuralları sayfası" lightbox="images/asr-defender365-01b.png"::: 

**Algılamaları görüntüle'ye** tıklayarak **Algılamalar** sekmesini açın.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-reports-detections.png" alt-text="Saldırı yüzeyi azaltma kuralları algılamaları" lightbox="images/asr-defender365-reports-detections.png":::

**GroupBy** ve **Filter** bölmesi aşağıdaki seçenekleri sağlar:

**GroupBy**, aşağıdaki gruplara ayarlanmış sonuçları döndürür:

- Gruplandırma yok
- Algılanan dosya
- Denetim veya engelleme
- Kural
- Kaynak uygulama
- Cihaz
- Kullanıcı
- Publisher

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-reports-detections.png" alt-text="Saldırı yüzeyi azaltma kuralları algılamaları GroupBy filtresi" lightbox="images/asr-defender365-reports-detections.png":::

**Filtre** , sonuçların kapsamını yalnızca seçili ASR kurallarıyla kapsamanızı sağlayan **Kurallarda filtrele** sayfasını açar:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-filter.png" alt-text="Kurallar üzerinde Saldırı yüzeyi azaltma kuralları algılamaları filtresi" lightbox="images/asr-defender365-filter.png":::

>[!Note]
>Microsoft Microsoft 365 Güvenlik E5 veya A5, Windows E5 veya A5 lisansınız varsa, aşağıdaki bağlantı Microsoft Defender 365 Raporları > [Saldırı yüzeyi azaltmaları](https://security.microsoft.com/asr?viewid=detections) > Algılamalar sekmesini açar.

### <a name="configuration-tab"></a>Yapılandırma sekmesi

AsR kurallarının toplam durumu(bilgisayar başına) listeler: Kapalı, Denetim, Engelle.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-configurations.png" alt-text="Saldırı yüzeyi azaltma kuralları Yapılandırma sekmesi ve sayfasında bir giriş" lightbox="images/asr-defender365-configurations.png":::

Yapılandırmalar sekmesinde, ASR kurallarını gözden geçirmek istediğiniz cihazı seçerek cihaz başına hangi ASR kurallarının etkinleştirildiğini ve hangi modda etkinleştirildiğini kontrol edebilirsiniz.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-configurations.settings.png" alt-text="Saldırı yüzeyi azaltma kuralları etkin ve mod" lightbox="images/asr-defender365-configurations.settings.png":::

**Başlarken** bağlantısı, ASR için bir uç nokta koruma ilkesi oluşturabileceğiniz veya değiştirebileceğiniz Microsoft Endpoint Manager yönetim merkezini açar:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-05b-mem1.png" alt-text="Genel Bakış sayfasındaki *Uç nokta güvenlik menü öğesi" lightbox="images/asr-defender365-05b-mem1.png":::

Uç nokta güvenlik | Genel bakış'ta **Saldırı yüzeyini azaltma'yı** seçin:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-05b-mem2.png" alt-text="MEM'de Saldırı yüzeyini azaltma" lightbox="images/asr-defender365-05b-mem2.png":::

Uç Nokta Güvenliği | Saldırı yüzeyini azaltma bölmesi açılır:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-05b-mem3.png" alt-text="Uç Nokta güvenliği Saldırı yüzeyi azaltma bölmesi" lightbox="images/asr-defender365-05b-mem3.png":::

>[!Note]
>Microsoft Defender 365 E5 (veya Windows E5?) lisansınız varsa, bu bağlantı Microsoft Defender 365 Raporları > Saldırı yüzeyi azaltmaları > [Yapılandırmalar](https://security.microsoft.com/asr?viewid=configuration) sekmesini açar.

### <a name="add-exclusions"></a>Dışlama ekleme

Bu sekme, dışlama için algılanan varlıkları (örneğin, hatalı pozitifler) seçmek için bir yöntem sağlar. Dışlamalar eklendiğinde rapor, beklenen etkinin bir özetini sağlar.

>[!Note]
> Microsoft Defender Virüsten Koruma AV dışlamaları ASR kuralları tarafından kabul edilir.  Bkz [. Uzantı, ad veya konuma göre dışlamaları yapılandırma ve doğrulama](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

> [!div class="mx-imgBorder"]
> :::image type="content" source="Images/asr-defender365-06d.png" alt-text="Algılanan dosyanın dışlanması için bölme" lightbox="Images/asr-defender365-06d.png":::

> [!Note]
>Microsoft Defender 365 E5 (veya Windows E5?) lisansınız varsa, bu bağlantı Microsoft Defender 365 Raporları > Saldırı yüzeyi azaltmaları > [Dışlamalar](https://security.microsoft.com/asr?viewid=exclusions) sekmesini açar.

### <a name="use-powershell-as-an-alternative-method-to-enable-asr-rules"></a>ASR kurallarını etkinleştirmek için alternatif yöntem olarak PowerShell kullanma

PowerShell'i (MEM'e alternatif olarak) kullanarak, özellik tam olarak etkinleştirildiğinde engellenecek uygulamaların kaydını görüntülemek üzere DENETIM modunda ASR kurallarını etkinleştirebilirsiniz. Ayrıca, normal kullanım sırasında kuralların ne sıklıkta tetikleneceklerine ilişkin bir fikir edinebilirsiniz.

Denetim modunda bir saldırı yüzeyi azaltma kuralını etkinleştirmek için aşağıdaki PowerShell cmdlet'ini kullanın:

```PowerShell
Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
```

Burada `<rule ID>` [, saldırı yüzeyi azaltma kuralının GUID değeridir](attack-surface-reduction-rules-reference.md).

Denetim modunda eklenen tüm saldırı yüzeyi azaltma kurallarını etkinleştirmek için aşağıdaki PowerShell cmdlet'ini kullanın:

```PowerShell
(Get-MpPreference).AttackSurfaceReductionRules_Ids | Foreach {Add-MpPreference -AttackSurfaceReductionRules_Ids $_ -AttackSurfaceReductionRules_Actions AuditMode}
```

> [!TIP]
> Saldırı yüzeyi azaltma kurallarının kuruluşunuzda nasıl çalışacağını tam olarak denetlemek istiyorsanız, bu ayarı ağınızdaki cihazlara dağıtmak için bir yönetim aracı kullanmanız gerekir.

Ayarı yapılandırmak ve dağıtmak için grup ilkesi, Intune veya mobil cihaz yönetimi (MDM) yapılandırma hizmeti sağlayıcılarını (CSP' ler) de kullanabilirsiniz. [Ana Saldırı yüzeyi azaltma kuralları](attack-surface-reduction.md) makalesinde daha fazla bilgi edinin.

## <a name="use-windows-event-viewer-review-as-an-alternative-to-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalındaki saldırı yüzeyi azaltma kuralları raporlama sayfasına alternatif olarak Windows Olay Görüntüleyicisi Gözden Geçirme'yi kullanın

Engellenmiş olabilecek uygulamaları gözden geçirmek için Olay Görüntüleyicisi açın ve Microsoft-Windows-Windows Defender/İşletim günlüğünde Olay Kimliği 1121'i filtreleyin. Aşağıdaki tabloda tüm ağ koruma olayları listelenir.

Olay Kimliği | Açıklama
-|-
 5007 | Ayarlar değiştirildiğinde gerçekleşen olay
 1121 | Bir saldırı yüzeyi azaltma kuralının blok modunda tetiklenmesi olayı
 1122 | Bir saldırı yüzeyi azaltma kuralının denetim modunda tetiklendiğinde gerçekleşen olay

## <a name="additional-topics-in-this-deployment-collection"></a>Bu dağıtım koleksiyonundaki ek konular

[Saldırı yüzeyini azaltma (ASR) kuralları dağıtımına genel bakış](attack-surface-reduction-rules-deployment.md)

[Saldırı yüzeyini azaltma (ASR) kuralları dağıtım planı](attack-surface-reduction-rules-deployment-plan.md)

[Saldırı yüzeyini azaltma (ASR) kurallarını etkinleştirme](attack-surface-reduction-rules-deployment-implement.md)

[Saldırı yüzeyini azaltma (ASR) kurallarını kullanıma hazır hale getirme](attack-surface-reduction-rules-deployment-operationalize.md)

[Saldırı yüzeyini azaltma (ASR) kuralları başvurusu](attack-surface-reduction-rules-reference.md)
