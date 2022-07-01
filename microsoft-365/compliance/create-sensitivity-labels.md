---
title: Hassasiyet etiketleri oluşturma ve yayınlama
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
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: 'Tüm Microsoft Purview Bilgi Koruması çözümleri için bir gereksinim: Kuruluşunuzun verilerini sınıflandırmak ve korumak için duyarlılık etiketleri oluşturun, yapılandırın ve yayımlayın.'
ms.openlocfilehash: 0f920c91e1e844a4feaab7f9d1d58e88da6791ca
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66573879"
---
# <a name="create-and-configure-sensitivity-labels-and-their-policies"></a>Duyarlılık etiketleri ve ilkeleri oluşturma ve yapılandırma

>*[Güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Tüm Microsoft Purview Bilgi Koruması çözümleri [duyarlılık etiketleri](sensitivity-labels.md) kullanılarak uygulanır. Bu etiketleri oluşturmak ve yayımlamak için <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a> gidin.

İlk olarak, uygulamalar ve diğer hizmetler için kullanılabilir hale getirmek istediğiniz duyarlılık etiketlerini oluşturun ve yapılandırın. Örneğin, kullanıcıların Office uygulamalarından görmesini ve uygulamasını istediğiniz etiketler.

Ardından, yapılandırdığınız etiketleri ve ilke ayarlarını içeren bir veya daha fazla etiket ilkesi oluşturun. Seçtiğiniz kullanıcılar ve konumlar için etiketleri ve ayarları yayımlayan etiket ilkesidir.

> [!TIP]
> Henüz herhangi bir duyarlılık etiketiniz yoksa, varsayılan etiketlerin ve varsayılan etiket ilkesinin otomatik olarak oluşturulması için uygun olabilirsiniz. Bazı etiketleriniz olsa bile, yeni müşteriler için oluşturduğumuz bu varsayılan etiketlerin yapılandırmasını görmek yararlı olabilir. Örneğin, kendi etiket dağıtımınızı hızlandırmaya yardımcı olmak için aynı el ile yapılandırmaları yapabilirsiniz.
> 
> Daha fazla bilgi için bkz. [Microsoft Purview Bilgi Koruması için varsayılan etiketler ve ilkeler](mip-easy-trials.md).

## <a name="before-you-begin"></a>Başlamadan önce

Kuruluşunuzun genel yöneticisi duyarlılık etiketlerinin tüm yönlerini oluşturmak ve yönetmek için tam izinlere sahiptir. Genel yönetici olarak oturum açmadıysanız bkz. [Duyarlılık etiketleri oluşturmak ve yönetmek için gereken izinler](get-started-with-sensitivity-labels.md#permissions-required-to-create-and-manage-sensitivity-labels).

## <a name="create-and-configure-sensitivity-labels"></a>Duyarlılık etiketleri oluşturma ve yapılandırma

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/) **Çözüm** > **Bilgileri koruma** > **Etiketleri'ni** seçin

2. **Etiketler** sayfasında **+ Etiket oluştur'u** seçerek yeni duyarlılık etiketi yapılandırmasını başlatın: 
    
    ![Duyarlılık etiketi oluşturun.](../media/create-sensitivity-label-full.png)

    > [!NOTE]
    > Varsayılan olarak, kiracılarda herhangi bir etiket yoktur ve bunları oluşturmanız gerekir. Örnek resimdeki etiketler[, Azure Information Protection'dan geçirilen](/azure/information-protection/configure-policy-migrate-labels) varsayılan etiketleri gösterir.

3. **Bu etiket için kapsamı tanımla** sayfasında, seçilen seçenekler yapılandırabileceğiniz ayarlar için etiketin kapsamını ve yayımlandıklarında nerede görünür olacağını belirler:

    ![Duyarlılık etiketlerinin kapsamları.](../media/sensitivity-labels-scopes.png)

    - **Dosyalar & e-postalar** seçiliyse, Office Word ve Outlook gibi duyarlılık etiketlerini destekleyen uygulamalar için geçerli ayarları yapılandırabilirsiniz. Bu seçenek belirlenmezse, bu ayarların ilk sayfasını görürsünüz, ancak bunları yapılandıramazsınız ve etiketler kullanıcıların bu uygulamalarda seçebileceği şekilde kullanılamaz.

    - **Gruplar & siteleri** seçiliyse, Microsoft 365 gruplarına ve Teams ile SharePoint sitelerine uygulanan ayarları yapılandırabilirsiniz. Bu seçenek belirtilmemişse, bu ayarların ilk sayfasını görürsünüz, ancak bunları yapılandıramazsınız ve etiketler kullanıcıların gruplar ve site için seçmesi için kullanılamaz.

    **Şemalaştırılmış veri varlıkları** kapsamı hakkında daha fazla bilgi için bkz. [İçeriğinizi Microsoft Purview Veri Eşlemesi'da otomatik olarak etiketleme](/azure/purview/create-sensitivity-label).

4. Etiket ayarları için yapılandırma istemlerini izleyin.

    Etiket ayarları hakkında daha fazla bilgi için genel bakış bilgilerinden [duyarlılık etiketlerinin yapabilecekleri](sensitivity-labels.md#what-sensitivity-labels-can-do) bölümüne bakın ve tek tek ayarlar için kullanıcı arabirimindeki yardımı kullanın.

5. Daha fazla etiket oluşturmak için bu adımları yineleyin. Ancak, bir alt etiket oluşturmak istiyorsanız, önce üst etiketi seçin ve **diğer eylemler** için **...** öğesini ve ardından **Alt etiket ekle'yi** seçin.

6. İhtiyacınız olan tüm etiketleri oluşturduğunuzda, etiketlerin sırasını gözden geçirin ve gerekirse bunları yukarı veya aşağı taşıyın. Etiketin sırasını değiştirmek için **Diğer eylemler** için **...** öğesini ve ardından **Yukarı taşı** veya **Aşağı taşı'yı** seçin. Daha fazla bilgi için genel bakış bilgilerindeki [Etiket önceliği (sipariş önemlidir)](sensitivity-labels.md#label-priority-order-matters) bölümüne bakın.

Var olan bir etiketi düzenlemek için etiketi seçin ve ardından **Etiketi düzenle** düğmesini seçin:

![Duyarlılık etiketini düzenlemek için etiketi düzenle düğmesi.](../media/edit-sensitivity-label-full.png)

Bu düğme, 4. adımdaki tüm etiket ayarlarını değiştirmenize olanak tanıyan **Duyarlılık etiketi yapılandırmasını düzenle'yi** başlatır.

Kullanıcıların etkisini anlamadığınız sürece etiketi silmeyin. Daha fazla bilgi için [Etiketleri kaldırma ve silme](#removing-and-deleting-labels) bölümüne bakın. 

> [!NOTE]
> Zaten yayımlanmış bir etiketi bir etiket ilkesi kullanarak düzenlerseniz, yapılandırmayı tamamladığınızda ek adım gerekmez. Örneğin, değişikliklerin aynı kullanıcıların kullanımına sunulması için bunu yeni bir etiket ilkesine eklemeniz gerekmez. Ancak değişikliklerin tüm uygulama ve hizmetlere çoğaltılması için 24 saate kadar izin verin.

Etiketlerinizi yayımlayana kadar, uygulamalarda veya hizmetlerde bu etiketleri seçemezsiniz. Etiketleri yayımlamak için bir [etiket ilkesine eklenmesi](#publish-sensitivity-labels-by-creating-a-label-policy) gerekir.

> [!IMPORTANT]
> Bu **Etiketler** sekmesinde, yeni bir etiket ilkesi oluşturmanız gerekmediği sürece **Etiketleri yayımla** sekmesini (veya etiketi düzenlerken etiketi **yayımla** düğmesini) seçmeyin. Birden çok etiket ilkesine yalnızca kullanıcıların farklı etiketlere veya farklı ilke ayarlarına ihtiyacı varsa ihtiyacınız vardır. Mümkün olduğunca az etiket ilkesine sahip olmayı hedefleyin; kuruluş için yalnızca bir etiket ilkesi olması yaygın değildir.

### <a name="additional-label-settings-with-security--compliance-powershell"></a>Güvenlik & Uyumluluğu PowerShell ile ek etiket ayarları

[Güvenlik & Uyumluluk PowerShell'inden](/powershell/exchange/scc-powershell) [Etiket Ayarla](/powershell/module/exchange/set-label) cmdlet'i ile ek etiket ayarları sağlanır.

Örneğin:

- Çok uluslu *dağıtımlar için LocaleSettings* parametresini kullanarak kullanıcıların etiket adını ve araç ipucunun yerel dillerinde görmesini sağlayın. [Aşağıdaki bölümde](#example-configuration-to-configure-a-sensitivity-label-for-different-languages) Fransızca, İtalyanca ve Almanca için etiket adını ve araç ipucu metnini belirten bir örnek yapılandırma vardır.

- Yerleşik etiketleme tarafından desteklenen gelişmiş ayarlar PowerShell belgelerinde yer alır. Bu PowerShell gelişmiş ayarlarını belirtme konusunda daha fazla yardım [için gelişmiş ayarları belirtmeye yönelik PowerShell ipuçları](#powershell-tips-for-specifying-the-advanced-settings) bölümüne bakın. Azure Information Protection birleşik etiketleme istemcisi tarafından desteklenen ek gelişmiş ayarlar için [bu istemcinin yönetici kılavuzundaki belgelere](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-labels) bakın.

#### <a name="example-configuration-to-configure-a-sensitivity-label-for-different-languages"></a>Farklı diller için duyarlılık etiketi yapılandırmak için örnek yapılandırma

Aşağıdaki örnekte, araç ipucu için yer tutucu metin içeren "Genel" adlı etiketin PowerShell yapılandırması gösterilmektedir. Bu örnekte etiket adı ve araç ipucu metni Fransızca, İtalyanca ve Almanca için yapılandırılmıştır.

Bu yapılandırmanın bir sonucu olarak, bu görüntüleme dillerini kullanan Office uygulamalarına sahip kullanıcılar etiket adlarını ve araç ipuçlarını aynı dilde görür. Benzer şekilde, Dosya Gezgini dosyaları etiketlemek için Azure Information Protection birleşik etiketleme istemcisi yüklüyse, Windows'un bu dil sürümlerine sahip kullanıcılar etiketleme için sağ tıklama eylemlerini kullandıklarında etiket adlarını ve araç ipuçlarını yerel dillerinde görürler.

Desteklemeniz gereken diller için Office [dil tanımlayıcılarını](/deployoffice/office2016/language-identifiers-and-optionstate-id-values-in-office-2016#language-identifiers) (dil etiketleri olarak da bilinir) kullanın ve etiket adı ve araç ipucu için kendi çevirinizi belirtin.

PowerShell'de komutları çalıştırmadan önce [Güvenlik & Uyumluluk PowerShell'e bağlanmanız](/powershell/exchange/connect-to-scc-powershell) gerekir.

```powershell
$Languages = @("fr-fr","it-it","de-de")
$DisplayNames=@("Publique","Publico","Oeffentlich")
$Tooltips = @("Texte Français","Testo italiano","Deutscher text")
$label = "Public"
$DisplayNameLocaleSettings = [PSCustomObject]@{LocaleKey='DisplayName';
Settings=@(
@{key=$Languages[0];Value=$DisplayNames[0];}
@{key=$Languages[1];Value=$DisplayNames[1];}
@{key=$Languages[2];Value=$DisplayNames[2];})}
$TooltipLocaleSettings = [PSCustomObject]@{LocaleKey='Tooltip';
Settings=@(
@{key=$Languages[0];Value=$Tooltips[0];}
@{key=$Languages[1];Value=$Tooltips[1];}
@{key=$Languages[2];Value=$Tooltips[2];})}
Set-Label -Identity $Label -LocaleSettings (ConvertTo-Json $DisplayNameLocaleSettings -Depth 3 -Compress),(ConvertTo-Json $TooltipLocaleSettings -Depth 3 -Compress)
```

#### <a name="powershell-tips-for-specifying-the-advanced-settings"></a>Gelişmiş ayarları belirtmek için PowerShell ipuçları

Adına göre bir duyarlılık etiketi belirtebilirsiniz ancak etiket adını veya görünen adı belirtme konusunda olası karışıklığı önlemek için etiket GUID'sini kullanmanızı öneririz. Etiket adı kiracınızda benzersiz olduğundan doğru etiketi yapılandırdığınızdan emin olabilirsiniz. Görünen ad benzersiz değildir ve yanlış etiketin yapılandırılması ile sonuçlanabilir. GUID'yi bulmak ve etiketin kapsamını onaylamak için:

````powershell
Get-Label | Format-Table -Property DisplayName, Name, Guid, ContentType
````

Duyarlılık etiketinden gelişmiş bir ayarı kaldırmak için aynı AdvancedSettings parametresi söz dizimini kullanın, ancak null dize değeri belirtin. Örneğin:

````powershell
Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultSharingScope=""}
````

Gelişmiş ayarlar da dahil olmak üzere etiketinizin yapılandırmasını denetlemek için kendi etiket GUID'niz ile aşağıdaki söz dizimini kullanın:

```powershell
(Get-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e).settings
```

## <a name="publish-sensitivity-labels-by-creating-a-label-policy"></a>Etiket ilkesi oluşturarak duyarlılık etiketlerini yayımlama

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com/) **Çözüm** > **Bilgileri koruma** > **Etiket ilkeleri'ni** seçin

2. **Etiket ilkeleri sayfasında Etiketi** **yayımla'yı** seçerek **İlke oluşturma** yapılandırmasını başlatın:
    
    ![Etiketleri yayımlama.](../media/publish-sensitivity-labels-full.png)
    
    > [!NOTE]
    > Varsayılan olarak, kiracıların herhangi bir etiket ilkesi yoktur ve bunları oluşturmanız gerekir. 

3. **Yayımlamak için duyarlılık etiketlerini seçin** sayfasında **Yayımlamak için duyarlılık etiketlerini seçin** bağlantısını seçin. Uygulamalarda ve hizmetlerde kullanılabilir hale getirmek istediğiniz etiketleri seçin ve ardından **Ekle'yi** seçin.

    > [!IMPORTANT]
    > Bir alt etiket seçerseniz, üst etiketini de seçtiğinizden emin olun.

4. Seçili etiketleri gözden geçirin ve değişiklik yapmak için **Düzenle'yi** seçin. Aksi takdirde **İleri'yi** seçin.

5. İlke ayarlarını yapılandırmak için istemleri izleyin.

    Gördüğünüz ilke ayarları, seçtiğiniz etiketlerin kapsamıyla eşleşer. Örneğin, yalnızca **Dosyalar & e-posta** kapsamına sahip etiketleri seçtiyseniz, İlke ayarlarını Görmezsiniz **Bu etiketi varsayılan olarak gruplara ve sitelere uygula ve Kullanıcıların gruplarına ve sitelerine** **etiket uygulamasını gerektir**.

    Bu ayarlar hakkında daha fazla bilgi için genel bakış bilgilerinden [etiket ilkelerinin yapabilecekleri](sensitivity-labels.md#what-label-policies-can-do) bölümüne bakın ve tek tek ayarlar için kullanıcı arabirimindeki yardımı kullanın.

    **Microsoft Purview Veri Eşlemesi varlıklar (önizleme)** için yapılandırılmış etiketler için: Bu etiketlerin ilişkili ilke ayarları yoktur.

6. Farklı kullanıcılar veya kapsamlar için farklı ilke ayarlarına ihtiyacınız varsa bu adımları yineleyin. Örneğin, bir kullanıcı grubu için ek etiketler veya bir kullanıcı alt kümesi için farklı bir varsayılan etiket istiyorsunuz. Veya etiketleri farklı kapsamlara sahip olacak şekilde yapılandırdıysanız.

7. Bir kullanıcı için çakışmaya neden olabilecek birden fazla etiket ilkesi oluşturursanız, ilke sırasını gözden geçirin ve gerekirse bunları yukarı veya aşağı taşıyın. Etiket ilkesinin sırasını değiştirmek için **Diğer eylemler** için **...** öğesini ve ardından **Yukarı taşı** veya **Aşağı taşı'yı** seçin. Daha fazla bilgi için genel bakış bilgilerindeki [Etiket ilkesi önceliği (sipariş konuları)](sensitivity-labels.md#label-policy-priority-order-matters) bölümüne bakın.

**İlke oluşturma** yapılandırmasının tamamlanması etiket ilkesini otomatik olarak yayımlar. Yayımlanan ilkede değişiklik yapmak için bunu düzenlemeniz yeterlidir. Seçmeniz için belirli bir yayımlama veya yeniden yayımlama eylemi yoktur.

Var olan bir etiket ilkesini düzenlemek için, ilkeyi seçin ve ardından **İlkeyi Düzenle** düğmesini seçin: 

![Duyarlılık etiketini düzenleyin.](../media/edit-sensitivity-label-policy-full.png)

Bu düğme, hangi etiketlerin dahil olduğunu ve etiket ayarlarını düzenlemenizi sağlayan **İlke oluştur** yapılandırmasını başlatır. Yapılandırmayı tamamladığınızda, tüm değişiklikler otomatik olarak seçili kullanıcılara ve hizmetlere çoğaltılır.

### <a name="additional-label-policy-settings-with-security--compliance-powershell"></a>Güvenlik & Uyumluluğu PowerShell ile ek etiket ilkesi ayarları

[Güvenlik & Uyumluluğu PowerShell'in](/powershell/exchange/scc-powershell) [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy) cmdlet'i ile ek etiket ilkesi ayarları sağlanır.

Bu belge, yerleşik etiketleme tarafından desteklenen gelişmiş ayarları içerir. Azure Information Protection birleşik etiketleme istemcisi tarafından desteklenen ek gelişmiş ayarlar için [bu istemcinin yönetici kılavuzundaki belgelere](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-label-policies) bakın.

## <a name="when-to-expect-new-labels-and-changes-to-take-effect"></a>Yeni etiketlerin ve değişikliklerin etkili olmasını bekleme

Etiketler ve etiket ilkesi ayarları için değişikliklerin hizmetlere yayılması için 24 saat süre tanıyın. Her birinin kendi zamanlama döngüleri olan birçok dış bağımlılık vardır, bu nedenle son değişiklikler için etiketler ve etiket ilkeleriyle ilgili sorunları gidermek için zaman harcamadan önce bu 24 saatlik süreyi beklemek iyi bir fikirdir.

Ancak, etiket ve etiket ilkesi değişikliklerinin çok daha hızlı veya 24 saatten uzun sürebileceği bazı senaryolar vardır. Örneğin, Word, Excel ve Web üzerinde PowerPoint için yeni ve silinmiş duyarlılık etiketleri için güncelleştirmelerin bir saat içinde çoğaltılmış olduğunu görebilirsiniz. Ancak yeni grup ve grup üyeliği değişikliklerinin doldurulması veya ağ çoğaltma gecikmesi ve bant genişliği kısıtlamalarına bağlı yapılandırmalar için bu değişiklikler 24-48 saat sürebilir.

## <a name="use-powershell-for-sensitivity-labels-and-their-policies"></a>Duyarlılık etiketleri ve ilkeleri için PowerShell kullanma

Artık etiketleme yönetim merkezinizde gördüğünüz tüm ayarları oluşturmak ve yapılandırmak için [Güvenlik & Uyumluluk PowerShell'i](/powershell/exchange/scc-powershell) kullanabilirsiniz. Bu, etiketleme yönetim merkezlerinde bulunmayan ayarlar için PowerShell'i kullanmaya ek olarak artık duyarlılık etiketlerinin ve duyarlılık etiketi ilkelerinin oluşturulması ve bakımı için tam betik yazabileceğiniz anlamına gelir. 

Desteklenen parametreler ve değerler için aşağıdaki belgelere bakın:

- [Yeni Etiket](/powershell/module/exchange/new-label)
- [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy)
- [Etiket Ayarla](/powershell/module/exchange/set-label)
- [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy)

> [!TIP]
> Duyarlılık etiketi için gelişmiş ayarları yapılandırırken, bu sayfadaki [gelişmiş ayarlar bölümünü belirtmek için PowerShell ipuçlarına](#powershell-tips-for-specifying-the-advanced-settings) başvurmak yararlı olabilir.

Duyarlılık etiketlerinin veya duyarlılık etiketi ilkelerinin silinmesini betik olarak yazmanız gerekiyorsa [Remove-Label](/powershell/module/exchange/remove-label) ve [Remove-LabelPolicy](/powershell/module/exchange/remove-labelpolicy) de kullanabilirsiniz. Ancak duyarlılık etiketlerini silmeden önce sonraki bölümü okuduğunuzdan emin olun.

## <a name="removing-and-deleting-labels"></a>Etiketleri kaldırma ve silme

Üretim ortamında duyarlılık etiketlerini bir etiket ilkesinden kaldırmanız veya duyarlılık etiketlerini silmeniz pek olası değildir. İlk test aşamasında bu eylemlerden birini veya birini yapmanız gerekebilir. Bu eylemlerden birini yaptığınızda ne olacağını anladığınızdan emin olun.

Etiket ilkesinden etiket kaldırmak, etiketi silmekten daha az risklidir ve gerekirse daha sonra her zaman geri eklenebilir. Etiket ilkesindeyse etiketi silemezsiniz.

Etiketin başlangıçta belirtilen kullanıcılara yayımlanmaması için etiket ilkesinden bir etiketi kaldırdığınızda, etiket ilkesi bir sonraki yenilendiğinde, kullanıcılar artık bu etiketi Office uygulamalarında seçecek şekilde görmez. Bu etiket zaten uygulanmışsa, etiket içerikten veya kapsayıcıdan kaldırılmaz. Örneğin, Word, Excel ve PowerPoint için masaüstü uygulamalarında yerleşik etiketleme kullanan kullanıcılar yine de durum çubuğunda uygulanan etiket adını görür. Uygulanan kapsayıcı etiketi Teams veya SharePoint sitesini korumaya devam eder.

Buna karşılık, bir etiketi sildiğinizde:

- Etiket şifreleme uyguladıysa, önceden korunan içeriğin hala açılabilmesi için temel koruma şablonu arşivlenmiştir. Bu arşivlenmiş koruma şablonu nedeniyle, aynı ada sahip yeni bir etiket oluşturamazsınız. [PowerShell](/powershell/module/aipservice/remove-aipservicetemplate) kullanarak bir koruma şablonunu silmek mümkün olsa da, arşivlenmiş şablonla şifrelenmiş içeriği açmanız gerekmediğinden emin değilseniz bunu yapmayın.

- SharePoint veya OneDrive'da depolanan belgeler [için ve Office dosyaları için duyarlılık etiketlerini etkinleştirdiniz](sensitivity-labels-sharepoint-onedrive-files.md): Belgeyi Web için Office açtığınızda, etiket uygulamada uygulanmaz ve etiket adı artık SharePoint'teki **Duyarlılık** sütununda gösterilmez. Silinen etiket şifreleme uyguladıysa ve hizmetler şifrelenmiş içeriği işleyebilirse, şifreleme kaldırılır. Bu hizmetlerden çıkış eylemleri aynı sonucu verir. Örneğin, bir Office masaüstü veya mobil uygulamasıyla indirme, kopyalama, taşıma ve açma. Etiket bilgileri dosyanın meta verilerinde kalsa da, uygulamalar artık etiket kimliğini bir görünen adla eşleyemez, bu nedenle kullanıcılar bir dosyanın etiketlenmemiş olduğunu varsayar.

- SharePoint ve OneDrive dışında depolanan belgeler için veya Office dosyaları ve e-postalar için duyarlılık etiketlerini etkinleştirmediyseniz: İçeriği açtığınızda, meta verilerdeki etiket bilgileri kalır, ancak ad eşlemesi için etiket kimliği olmadan kullanıcılar uygulanan etiket adını (örneğin, masaüstü uygulamalarının durum çubuğunda) görmez. Silinen etiket şifreleme uyguladıysa, şifreleme kalır ve kullanıcılar artık arşivlenen koruma şablonunun adını ve açıklamasını görmeye devam eder.

- SharePoint ve Teams'deki siteler gibi kapsayıcılar için: Etiket kaldırılır ve bu etiketle yapılandırılan tüm ayarlar artık zorunlu tutulmaz. Bu eylem genellikle SharePoint siteleri için 48-72 saat arasında sürer ve Teams ile Microsoft 365 Grupları için daha hızlı olabilir.

Tüm etiket değişikliklerinde olduğu gibi, bir etiket ilkesinden duyarlılık etiketinin kaldırılması veya duyarlılık etiketinin silinmesi tüm kullanıcılara ve hizmetlere çoğaltılması zaman alır.

## <a name="next-steps"></a>Sonraki adımlar

Belirli senaryolarda duyarlılık etiketlerinizi yapılandırmak ve kullanmak için aşağıdaki makaleleri kullanın:

- [Duyarlılık etiketlerinde şifreleme kullanarak içeriğe erişimi kısıtlama](encryption-sensitivity-labels.md)

- [İçeriğe otomatik olarak bir hassasiyet etiketi uygulama](apply-sensitivity-label-automatically.md)

- [Ekipler, gruplar ve sitelerle hassasiyet etiketleri kullanma](sensitivity-labels-teams-groups-sites.md)

- [SharePoint ve OneDrive'daki Office dosyaları için hassasiyet etiketlerini etkinleştirme](sensitivity-labels-sharepoint-onedrive-files.md)

Etiketlerinizin nasıl kullanıldığını izlemek için bkz. [Veri sınıflandırmasını kullanmaya başlama](data-classification-overview.md).
