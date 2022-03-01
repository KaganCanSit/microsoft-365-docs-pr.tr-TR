---
title: Duyarlılık etiketleri oluşturma ve yayımlama
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
description: 'Tüm çözüm ve Microsoft Bilgi Koruması gereksinimi: Duyarlılık etiketlerini oluşturun, yapılandırarak ve yayımlayın; bu etiketleri kullanarak kuruluş verilerinizi sınıflandırin ve koruyun.'
ms.openlocfilehash: b5bc61de14f54d65e4ce5eb6f7ae78303626c123
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032497"
---
# <a name="create-and-configure-sensitivity-labels-and-their-policies"></a>Duyarlılık etiketlerini ve onların ilkelerini oluşturma ve yapılandırma

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Tüm Microsoft Bilgi Koruması çözümleri (bazen MIP ile kısaltılmış olabilir) duyarlılık etiketleri kullanılarak [uygulanır](sensitivity-labels.md). Bu etiketleri oluşturmak ve yayımlamak için, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Etiketler'e Microsoft 365 uyumluluk merkezi</a>.

İlk olarak, uygulamalar ve diğer hizmetler için kullanılabilir hale almak istediğiniz duyarlılık etiketlerini oluşturun ve yapılandırarak oluşturun. Örneğin, kullanıcıların bu uygulamalardan görmelerini ve uygulamalarını istediğiniz Office.

Ardından, yapılandırılan etiketlerle ilke ayarlarını içeren bir veya birden çok etiket ilkesi oluşturun. Bu, seçilen kullanıcı ve konumların etiketlerini ve ayarlarını yayımlayan etiket ilkesidir.

## <a name="before-you-begin"></a>Başlamadan önce

Kuruluş genel yöneticisinin, duyarlılık etiketlerinin tüm yönlerini oluşturmak ve yönetmek için tam izinleri vardır. Genel yönetici olarak oturum açmadısanız, bkz. Duyarlılık [etiketlerini oluşturmak ve yönetmek için gereken izinler](get-started-with-sensitivity-labels.md#permissions-required-to-create-and-manage-sensitivity-labels).

## <a name="create-and-configure-sensitivity-labels"></a>Duyarlılık etiketlerini oluşturma ve yapılandırma

1. Kayıttan [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com/) **SolutionsInformation** >  **protection'ı seçin**
    
    Bu seçeneği hemen görmüyorsanız önce Hepsini **göster'i seçin**.

2. Etiketler **sayfasında,** Yeni duyarlılık **etiketi yapılandırmasını başlatmak için +** Etiket oluştur'a tıklayın. 

    Örneğin, aşağıdaki Microsoft 365 uyumluluk merkezi:

    ![Duyarlılık etiketi oluşturun.](../media/create-sensitivity-label-full.png)

    > [!NOTE]
    > Varsayılan olarak, kiracıların hiçbir etiketi yok ve bunları oluşturmanız gerekir. Örnek resimdeki etiketler, [Azure Information Protection'dan geçirilen varsayılan etiketleri gösterir](/azure/information-protection/configure-policy-migrate-labels).

3. Bu **etiket için kapsamı tanımla sayfasında** , yapılandırabilirsiniz ayarlar için etiketin kapsamını ve yayımlandıklarda nerede görünür olacaklarını belirleyen seçenekler belirler:

    ![Duyarlılık etiketlerinin kapsamları.](../media/sensitivity-labels-scopes.png)

    - Dosyalar **& e-postaları** seçiliyse, Word ve Office e-postaları gibi duyarlılık etiketlerini destekleyen uygulamalara Outlook. Bu seçenek seçilmemişse, bu ayarların ilk sayfasını görüntülersiniz ancak bunları yapılandıramazsanız etiketler bu uygulamalarda kullanıcılar tarafından seçiile hazır olmayacaktır.

    - Gruplar **& seçilirse**, bu gruplara uygulanacak ayarları Microsoft 365 grupların ve site Teams site SharePoint. Bu seçenek seçilmemişse, bu ayarların ilk sayfasını görüntüler ancak bunları yapılandıramazsanız, kullanıcıların gruplar ve site için seçecekleri etiketler kullanılamaz.

    Şemalı veri **varlıklarının kapsamı hakkında bilgi için** bkz. [Azure Purview'da içeriğinizi otomatik olarak etiketleme](/azure/purview/create-sensitivity-label).

4. Etiket ayarları için yapılandırma istemlerini izleyin.

    Etiket ayarları hakkında daha fazla bilgi için bkz. [](sensitivity-labels.md#what-sensitivity-labels-can-do) Genel bakış bilgilerinden hangi duyarlılık etiketlerini kullanabilir ve kullanıcı arabiriminde kişisel ayarlar için yardımı kullanabilirsiniz.

5. Daha fazla etiket oluşturmak için bu adımları yinele. Bununla birlikte, bir alt etiket oluşturmak istemeden önce üst etiketi seçin ve Diğer eylemler için **...** seçeneğini, ardından Alt etiket **ekle'yi seçin**.

6. Size gereken tüm etiketleri oluşturulduğunda, bunların siparişlerini gözden geçirin ve gerekirse, bunları yukarı veya aşağı hareket ettirin. Etiketin sıralamalarını değiştirmek için Diğer eylemler için **...** **seçeneğini** ve ardından Yukarı taşı veya Aşağı **taşı'ya** **seçin**. Daha fazla bilgi için genel [bakış bilgilerinden Etiket önceliği (sipariş konuları)](sensitivity-labels.md#label-priority-order-matters) belgesine bakın.

Mevcut bir etiketi düzenlemek için etiketi seçin ve ardından Etiketi düzenle **düğmesini** seçin:

![Duyarlılık etiketini düzenlemek için Etiketi düzenle düğmesi.](../media/edit-sensitivity-label-full.png)

Bu düğme, 4 **. adımda tüm** etiket ayarlarını değiştirmenizi sağlayan Duyarlılık etiketini düzenle yapılandırmasını başlatır.

Kullanıcılara etkisini anlamadıysanız etiketi silmeyin. Daha fazla bilgi için Etiketleri kaldırma [ve silme bölümüne](#removing-and-deleting-labels) bakın. 

> [!NOTE]
> Zaten bir etiket ilkesi kullanarak yayımlanmış bir etiketi düzenlerseniz, yapılandırmayı tamamlarken fazladan adım gerekmez. Örneğin, değişikliklerin aynı kullanıcılar tarafından kullanılabilir olması için bunu yeni bir etiket ilkesine eklemenize gerek yok. Bununla birlikte, değişikliklerin tüm uygulamalara ve hizmetlere çoğaltılması için 24 saate kadar izin verin.

Etiketlerinizi yayımlayana kadar, bunlar uygulamalarda veya hizmetlerde seç kullanılamaz. Etiketleri yayımlamak için, etiket [ilkesine eklenmiş olması gerekir](#publish-sensitivity-labels-by-creating-a-label-policy).

> [!IMPORTANT]
> Yeni **bir etiket** ilkesi oluşturmanız gerekmadıkça,  bu Etiketler sekmesinde Etiketleri yayımla  sekmesini (veya etiketi düzenlerken Etiketi yayımla düğmesini) seçmeyebilirsiniz. Birden çok etiket ilkesine sahip olmak için, kullanıcıların farklı etiketlere veya farklı ilke ayarlarına ihtiyacı vardır. Mümkün olduğunca az etiket ilkesine sahip olmak hedefle, kuruluş için tek bir etiket ilkesine sahip olmak seyrek görülen bir durum değildir.

### <a name="additional-label-settings-with-security--compliance-center-powershell"></a>Güvenlik ve Uyumluluk Merkezi PowerShell& ile ek etiket ayarları

Güvenlik ve Uyumluluk Merkezi [PowerShell'in Set-Label](/powershell/module/exchange/set-label) [cmdlet'iyle & ayarları kullanılabilir](/powershell/exchange/scc-powershell).

Örneğin:

- Çok *uluslu dağıtımlarda LocaleSettings* parametresini kullanın, böylece kullanıcılar etiket adını ve araç ipucunı yerel dillerinde görebilirler. Aşağıdaki [bölümde Fransızca](#example-configuration-to-configure-a-sensitivity-label-for-different-languages) , İtalyanca ve Almanca etiket adı ve araç ipucu metnini belirten örnek bir yapılandırma vardır.

- Azure Information Protection birleşik etiketleme istemcisi, etiket rengi ayarlama ve etiket uygulandığında özel özellik uygulama gibi kapsamlı bir gelişmiş ayarlar listesini destekler.[](/azure/information-protection/rms-client/clientv2-admin-guide-customizations) Tam liste için bkz. [Bu istemcinin yönetici kılavuzundan](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-labels) etiketler için kullanılabilir gelişmiş ayarlar.

#### <a name="example-configuration-to-configure-a-sensitivity-label-for-different-languages"></a>Farklı diller için duyarlılık etiketini yapılandırmak üzere örnek yapılandırma

Aşağıdaki örnekte, araç ipucu için yer tutucu metinle birlikte "Genel" adlı etiketin PowerShell yapılandırması görüntülenir. Bu örnekte, etiket adı ve araç ipucu metni Fransızca, İtalyanca ve Almanca için yapılandırılmıştır.

Bu yapılandırmanın sonucunda, bu görüntüleme dillerini kullanan Office uygulamaları olan kullanıcılar, aynı dilde etiket adlarını ve araç ipucunı görebilirler. Benzer şekilde, Dosya Gezgini'nden dosyaları etiketlemek için Azure Information Protection birleşik etiketleme istemcisini yüklemiş olursanız, Windows'in dil sürümlerine sahip olan kullanıcılar, etiketleme için sağ tıklama eylemlerini kullandıklarında kendi etiket adlarını ve araç ipucularını yerel dillerinde görebilirler.

Desteklemeniz gereken diller için, Office tanımlayıcılarını [(dil](/deployoffice/office2016/language-identifiers-and-optionstate-id-values-in-office-2016#language-identifiers) etiketleri olarak da bilinir) kullanın ve etiket adı ve araç ipucu için kendi çevirinizi belirtin.

PowerShell'de komutları çalıştırmadan önce, Güvenlik ve [Uyumluluk Merkezi PowerShell& bağlanın](/powershell/exchange/connect-to-scc-powershell).

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

## <a name="publish-sensitivity-labels-by-creating-a-label-policy"></a>Etiket ilkesi oluşturarak duyarlılık etiketlerini yayımlama

1. Kayıttan [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com/) **SolutionsInformation** >  **protection'ı seçin**
    
    Bu seçeneği hemen görmüyorsanız önce Hepsini **göster'i seçin**.

2. İlke **yapılandırmasını başlatmak** için Etiket ilkeleri **sekmesini ve** ardından Etiket **yayımla'yı** seçin:

    Örneğin, aşağıdaki Microsoft 365 uyumluluk merkezi:

    ![Etiketleri yayımlama.](../media/publish-sensitivity-labels-full.png)

    > [!NOTE]
    > Varsayılan olarak, kiracıların etiket ilkeleri vardır ve bunları oluşturmanız gerekir. 

3. Yayım **verilecek duyarlılık etiketlerini seçin sayfasında** , Yayımlayacak **duyarlılık etiketlerini seç bağlantısını** seçin. Uygulamalar ve hizmetlerde kullanılabilir hale eklemek istediğiniz etiketleri seçin ve sonra Ekle'yi **seçin**.

    > [!IMPORTANT]
    > Bir alt etiket seçerek etiketin üst etiketini de seçmeye devam etmek gerekir.

4. Seçili etiketleri gözden geçirmek ve değişiklik yapmak için Düzenle'yi **seçin**. Aksi takdirde Sonraki'yi **seçin**.

5. İlke ayarlarını yapılandırmak için istemleri izleyin.

    Gördüğünüz ilke ayarları, seçtiğiniz etiketlerin kapsamıyla eşler. Örneğin, yalnızca Dosyalar **&** e-posta kapsamına sahip etiketleri seçtiyseniz, ilke ayarlarını Gruplara ve sitelere varsayılan olarak uygula ve  Kullanıcıların gruplarına ve sitelerine etiket uygulamalarını gerektir ayarlarını **görmüyorsunuz**.

    Bu ayarlar hakkında daha fazla bilgi için bkz [. Genel bakış](sensitivity-labels.md#what-label-policies-can-do) bilgilerinden hangi etiket ilkelerinin neler yapabilirsiniz ve kullanıcı arabiriminde kişisel ayarlar için yardımı kullanın.

    **Azure Purview varlıkları (önizleme) için yapılandırılmış** etiketler için: Bu etiketlerle ilişkilendirilmiş ilke ayarları yok.

6. Farklı kullanıcılar veya kapsamlar için farklı ilke ayarlarına ihtiyacınız varsa bu adımları yineler. Örneğin, bir kullanıcı grubu için ek etiketler veya kullanıcı alt kümesi için farklı bir varsayılan etiket istiyor olabilir. Veya etiketleri farklı kapsamlara sahip olacak şekilde yapılandırdıysanız.

7. Bir kullanıcı için çakışmaya neden olacak birden çok etiket ilkesi oluşturmanız gerekiyorsa, ilke siparişlerini gözden geçirin ve gerekirse bunları yukarı veya aşağı hareket ettirin. Etiket ilkesi sıralamalarını değiştirmek için Diğer eylemler için **...** öğesini ve **sonra da Yukarı** taşı veya Aşağı **taşı'ya** **seçin**. Daha fazla bilgi için genel [bakış bilgilerinden etiket ilkesi önceliği (sipariş konuları)](sensitivity-labels.md#label-policy-priority-order-matters) konularını okuyun.

İlke oluşturma **yapılandırmasının** tamamlanması etiket İlkesini otomatik olarak yayımlar. Yayımlanan ilkede değişiklik yapmak için, ilkeyi düzenlemeniz gerekir. Seç başka bir yayımlama veya yeniden yayımlama eylemi yoktur.

Var olan bir etiket politikasını düzenlemek için, ilkeyi seçin ve sonra da **İlkeyi Düzenle düğmesini** seçin: 

![Duyarlılık etiketini düzenleyin.](../media/edit-sensitivity-label-policy-full.png)

Bu düğme, hangi **etiketlerin ekli** olduğunu ve etiket ayarlarını düzenlemenizi sağlayan İlke yapılandırmasını başlatır. Yapılandırmayı tamamlarken, tüm değişiklikler seçili kullanıcılara ve hizmetlere otomatik olarak çoğaltılır.

Windows, macOS, iOS ve Android'de Office uygulamaları için yerleşik etiketlemeyi kullanıyorsanız, kullanıcılar dört saat içinde ve tarayıcıyı yenilerken Word, Excel ve Web üzerinde PowerPoint için bir saat içinde yeni etiketler görebilir. Bununla birlikte, değişikliklerin tüm uygulama ve hizmetlere çoğaltılması için 24 saate kadar izin verin.

Duyarlılık etiketlerini destekleyen diğer uygulamalar ve hizmetler kendi güncelleştirme zamanlamaları ve ilke güncelleştirmeleri için tetikleyicileri ile 24 saate kadar daha sık güncelleştirmesi olabilir. Ayrıntılar için onların belgelerine bakın. Örneğin, Azure Information Protection birleşik etiketleme istemcisi için, [Azure Information Protection](/azure/information-protection/rms-client/use-client#detailed-comparisons-for-the-azure-information-protection-clients) istemcileri tablosu  için ayrıntılı karşılaştırmalar'da İlke güncelleştirme satırına bakın.

> [!TIP]
> Bazen duyarlılık etiketlerinin ve etiket ilkelerinin beklendiği gibi çalışmayı geciktirmelerine neden olan zamanlama bağımlılıklarını faktörü unutmayın. Örneğin, şifreleme uygulayan etiketler için [Azure Information Protection](/azure/information-protection/prepare#group-membership-caching-by-azure-information-protection) hizmeti tarafından yeni bir grup ve grup üyeliği değişiklikleri, ağ çoğaltması gecikme süresi ve bant genişliği kısıtlamaları, grup üyeliği önbelleğe alma.
> 
> Her biri kendi zamanlama döngülerine sahip olan birçok dış bağımlılıkla, son değişiklikler için etiketlerle ve etiket ilkeleriyle ilgili sorunları gidermek için zaman harcamadan önce 24 saat beklemeniz iyi olur.

### <a name="additional-label-policy-settings-with-security--compliance-center-powershell"></a>Güvenlik ve Uyumluluk Merkezi PowerShell& ile ek etiket ilkesi ayarları

Güvenlik ve Uyumluluk Merkezi PowerShell'den [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy) [cmdlet'iyle & ilke ayarları kullanılabilir](/powershell/exchange/scc-powershell).

Azure Information Protection birleşik etiketleme istemcisi, diğer etiket çözümlerinden ve e-postaları göndereni uyaran, iki aya yaslama veya engelleme içeren Outlook açılır iletilerin de dahil olduğu birçok gelişmiş ayarı destekler.[](/azure/information-protection/rms-client/clientv2-admin-guide-customizations) Tam liste için, bu [istemcinin yönetici kılavuzunda bulunan etiket ilkeleri](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-label-policies) için kullanılabilir gelişmiş ayarlar'a bakın.

## <a name="use-powershell-for-sensitivity-labels-and-their-policies"></a>Duyarlılık etiketleri ve ilkeleri için PowerShell kullanma

Artık etiket yönetim [merkezi & ayarları oluşturmak](/powershell/exchange/scc-powershell) ve yapılandırmak için Güvenlik ve Uyumluluk Merkezi PowerShell'i kullanabilirsiniz. Başka bir ifadeyle, PowerShell'i etiket yönetim merkezlerinde mevcut olmayan ayarlar için kullanmanın yanı sıra, artık duyarlılık etiketleri ve duyarlılık etiket ilkelerinin oluşturulması ve bakımı için tam komut dosyası hazırları yapabilirsiniz. 

Desteklenen parametreler ve değerler için aşağıdaki belgelere bakın:

- [New-Label](/powershell/module/exchange/new-label)
- [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy)
- [Set-Label](/powershell/module/exchange/set-label)
- [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy)

Duyarlılık etiketlerini veya [duyarlılık etiket](/powershell/module/exchange/remove-label) ilkelerini silme işlemini betik olarak kullanmak zorundaysanız [Remove-Label ve Remove-LabelPolicy'i](/powershell/module/exchange/remove-labelpolicy) de kullanabilirsiniz. Bununla birlikte, duyarlılık etiketlerini smeden önce aşağıdaki bölümü okuduğundan emin olun.

## <a name="removing-and-deleting-labels"></a>Etiketleri kaldırma ve silme

Üretim ortamında, bir etiket ilkesinden duyarlılık etiketlerini kaldırmanız veya duyarlılık etiketlerini silmeniz olası değildir. Bir ilk test aşamasında bu eylemlerden birini veya ikisinde birini yapma olasılığı daha yüksek olabilir. Bu işlemlerden herhangi birini gerçekleştir gerçekleştirin ve ne olduğunu anlayın.

Bir etiketi etiket ilkesinden kaldırmak, silmekten daha az risklidir ve daha sonra gerekirse etiket ilkesine yeniden  eklemeniz de gerekir:

- Etiket ilkesinden bir etiket kaldırarak etiket artık belirtilen kullanıcılara yayımlanamaz. Etiket ilkesi bir sonraki yenilemesinde, kullanıcılar etiket ilkesinde seçim yapmak üzere bu etiketi Office uygulaması. Ancak, etiket belgelere veya e-postalara uygulanmışsa, etiket bu içerikten kaldırılamaz. Etiket tarafından uygulanmış olan her şifreleme kalır ve temel koruma şablonu yayımlanmış olarak kalır. 

- Kaldırılan ancak daha önce içeriğe uygulanmış olan etiketler için Word, Excel ve PowerPoint'da yerleşik etiketleme kullanan kullanıcılar, durum çubuğunda uygulanan etiket adını yine görebilir. Benzer şekilde, sitelere uygulanan ve sitelere SharePoint etiketler yine Duyarlılık sütununda etiket **adını** görüntüler.

Karşılaştırmada, bir etiketi silebilirsiniz:

- Etiket uygulanan şifreleme ise, temel koruma şablonu daha önce korumalı olan içeriğin yine açılabilir şekilde arşivlenir. Bu arşivlenmiş koruma şablonu nedeniyle, aynı adı kullanarak yeni bir etiket oluşturabileceksiniz. [Koruma şablonunu PowerShell](/powershell/module/aipservice/remove-aipservicetemplate) kullanarak silmek mümkün olsa da, arşivlenmiş şablonla şifrelenmiş içeriği açmaya gerek olmadığınız sürece bunu yapma.

- Masaüstü uygulamaları için: Meta verilerde yer alan etiket bilgileri kalır, ancak artık ad eşleştirmesi için etiket kimliği artık mümkün olmadığı için kullanıcılar görüntülenen etiket adını (örneğin durum çubuğunda) görmemektedir ve bu nedenle kullanıcılar içeriğin etiket olmadığını varsayacaktır. Etiket uygulanan şifreleme ise, şifreleme kalır ve içerik açıldığında, kullanıcılar artık arşivlenmiş koruma şablonunun adını ve açıklamasını görmeye devam ediyor.

- Daha Web üzerinde Office: Kullanıcılar etiket adını durum çubuğunda veya Duyarlılık sütununda **görmüyor**. Meta verilerde yer alan etiket bilgileri ancak etiket şifreleme uygulamadı ise kalır. Etiket uygulanan şifreleme ise ve SharePoint ve OneDrive için duyarlılık etiketlerini etkinleştirdiyseniz[, meta](sensitivity-labels-sharepoint-onedrive-files.md) verideki etiket bilgileri kaldırılır ve şifreleme kaldırılır. 

Bir etiket ilkesinden bir duyarlılık etiketini kaldırır veya bir duyarlılık etiketini silseniz, bu değişikliklerin tüm kullanıcılara ve hizmetlere çoğaltılması 24 saate kadar sürebilir.

## <a name="next-steps"></a>Sonraki adımlar

Duyarlılık etiketlerinizi belirli senaryolarda yapılandırmak ve kullanmak için aşağıdaki makalelere bakın:

- [Duyarlılık etiketlerini şifreleme kullanarak içeriğe erişimi kısıtlama](encryption-sensitivity-labels.md)

- [Otomatik olarak içeriğe duyarlılık etiketi uygulama](apply-sensitivity-label-automatically.md)

- [Ekipler, gruplar ve sitelerle duyarlılık etiketleri kullanma](sensitivity-labels-teams-groups-sites.md)

- [SharePoint ve Office dosyaları için duyarlılık OneDrive](sensitivity-labels-sharepoint-onedrive-files.md)

Etiketlerinizin nasıl kullanılıyor olduğunu izlemek için bkz. [Veri sınıflandırması ile çalışmaya başlama](data-classification-overview.md).
