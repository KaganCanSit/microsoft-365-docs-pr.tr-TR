---
title: Yeni görünümde özel algılama kurallarını oluşturma Microsoft 365 Defender
description: Gelişmiş arama sorgularına dayalı olarak özel algılama kurallarını nasıl oluştur sevk ve yöneteceklerini öğrenin
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, özel algılamalar, kurallar, şema, kusto, RBAC, izinler, Uç nokta için Microsoft Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 473d58cde13f1f776c31184b2b50e74e23810b22
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015182"
---
# <a name="create-and-manage-custom-detections-rules"></a>Özel algılama kurallarını oluşturma ve yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

Özel algılama kuralları, gelişmiş arama sorgularını kullanarak tasarlanması ve [ince ayarlanması için kurallardır](advanced-hunting-overview.md) . Bu kurallar ihlalin şüpheli etkinliği ve hatalı yapılandırılmış uç noktalar da dahil olmak üzere çeşitli olayları ve sistem durumunu önceden izlemenizi sağlar. Bunları düzenli aralıklarla çalıştıracak şekilde ayarlayabilirsiniz; her eşleşme olduğunda uyarılar oluşturmak ve yanıt eylemleri yapmak.

## <a name="required-permissions-for-managing-custom-detections"></a>Özel algılamaları yönetmek için gerekli izinler

Özel algılamaları yönetmek için, size şu rollerden biri atanacak:

- **Güvenlik yöneticisi**:Bu kullanıcı [Azure Active Directory portalında](/azure/active-directory/roles/permissions-reference#security-administrator) ve diğer portal Microsoft 365 Defender hizmetlerde güvenlik ayarlarını yönetebilir.

- **Güvenlik işleci**:[Bu Azure Active Directory](/azure/active-directory/roles/permissions-reference#security-operator) olan kullanıcılar uyarıları yönetebilir ve portalda yer alan tüm bilgiler de dahil olmak üzere, güvenlikle ilgili özelliklere genel olarak salt Microsoft 365 Defender erişime sahip olabilir. Bu rol, yalnızca Uç Nokta için Microsoft Defender'da rol tabanlı erişim denetimi (RBAC) kapalı olursa, özel algılamaları yönetmek için yeterlidir. RBAC yapılandırılmışsa, Uç Nokta için Defender güvenlik **ayarları iznini** de yönetmeniz gerekir.

Belirli veri çözümlerinden verilere uygulanacak özel algılamaları da Microsoft 365 Defender izinlerine sahipsinizdir. Örneğin, örneğin yalnızca bu Microsoft 365 Defender Office `Email` için özel algılamalar oluşturmak için tabloları değil, yalnızca tabloları kullanarak özel algılamalar oluşturabilirsiniz`Identity`.  

Gerekli izinleri yönetmek için genel **yönetici şunları** yönetebilir:

- RolesSecurity **admin altında**, **güvenlik yöneticisini** [veya Microsoft 365 yönetim merkezi](https://admin.microsoft.com/) işleci **rolünü** >  **attayin**.
- Ayarlar **PermissionsBac** >  altında, [Microsoft 365 Defender'de Uç Nokta](https://security.microsoft.com/)  >  için Microsoft Defender RBAC **ayarlarını kontrol edin**. Güvenlik ayarlarını yönetme iznini atamak için **ilgili rolü** seçin.

> [!NOTE]
> Özel algılamaları yönetmek için, **güvenlik işleçleri** RBAC  açıksa Uç Nokta için Microsoft Defender'da güvenlik ayarları iznini yönetmesi gerekir.

## <a name="create-a-custom-detection-rule"></a>Özel algılama kuralı oluşturma
### <a name="1-prepare-the-query"></a>1. Sorguyu hazırlayın.

Gelişmiş Microsoft 365 Defender'ne **gidip mevcut** bir sorguyu seçin veya yeni bir sorgu oluşturun. Yeni bir sorgu kullanırken, hataları tanımlamak ve olası sonuçları anlamak için sorguyu çalıştırın.

>[!IMPORTANT]
>Hizmetin çok fazla sayıda uyarı geri dönmesini önlemek için, her kural her çalıştırıca yalnızca 100 uyarı oluşturmakla sınırlıdır. Kural oluşturmadan önce, günlük normal etkinlik uyarılarını önlemek için sorgunuzda küçük ayarlamalar oluşturun.


#### <a name="required-columns-in-the-query-results"></a>Sorgu sonuçlarında gerekli sütunlar
Özel bir algılama kuralı oluşturmak için, sorgunun aşağıdaki sütunları geri iadesi gerekir:

- `Timestamp`—oluşturulan uyarılar için zaman damgasını ayarlamak için kullanılır
- `ReportId`—orijinal kayıtlar için aramaları sağlar
- Belirli cihazları, kullanıcıları veya posta kutularını tanımlamak için aşağıdaki sütunlardan biri:
    - `DeviceId`
    - `DeviceName`
    - `RemoteDeviceName`
    - `RecipientEmailAddress`
    - `SenderFromAddress` (zarf gönderen veya Return-Path adresi)
    - `SenderMailFromAddress` (e-posta istemcisi tarafından görüntülenen gönderen adresi)
    - `RecipientObjectId`
    - `AccountObjectId`
    - `AccountSid`
    - `AccountUpn`
    - `InitiatingProcessAccountSid`
    - `InitiatingProcessAccountUpn`
    - `InitiatingProcessAccountObjectId`

>[!NOTE]
>Gelişmiş av şemasına yeni tablolar eklendiklerine, başka varlıklar için [destek eklenecektir](advanced-hunting-schema-tables.md).

Sonuçları özelleştirmek veya toplamak için veya `project` `summarize` işleci kullanmayanlar gibi basit sorgular genellikle bu ortak sütunları verir.

Daha karmaşık sorguların bu sütunları geri iade etmenin çeşitli yolları vardır. Örneğin, 'gibi bir sütun `DeviceId``Timestamp` `ReportId` altındaki varlığa göre toplamayı ve saymayı tercih ederseniz, her benzersiz değeri içeren en son olaydan geri dönebilirsiniz.`DeviceId`


> [!IMPORTANT]
> Sütunu kullanarak özel algılamaları filtrelemekten `Timestamp` kaçının. Özel algılamalarda kullanılan veriler algılama sıklığına göre önceden filtrelenmiş olarak kullanılır.


Aşağıdaki örnek sorgu, virüsten koruma algılamaları kullanan benzersiz cihazların sayısını (`DeviceId`) sayar ve yalnızca beşten fazla algılamaya sahip cihazları bulmak için bu sayımı kullanır. En geç ile ilgili `Timestamp` olan işleci, `ReportId`işlevle `summarize` birlikte kullanır `arg_max` .

```kusto
DeviceEvents
| where ingestion_time() > ago(1d)
| where ActionType == "AntivirusDetection"
| summarize (Timestamp, ReportId)=arg_max(Timestamp, ReportId), count() by DeviceId
| where count_ > 5
```

> [!TIP]
> Daha iyi bir sorgu performansı için, kural için hedeflenen çalıştırma sıklığınıza uygun bir zaman filtresi ayarlayın. En az sık çalıştırma her _24 saatte bir olduğu_ için, son güne göre filtreleme tüm yeni verileri içerir.

### <a name="2-create-new-rule-and-provide-alert-details"></a>2. Yeni kural oluşturun ve uyarı ayrıntıları sağlar.

Sorgu düzenleyicisinde sorguyla, Algılama kuralı **oluştur'a tıklayın** ve aşağıdaki uyarı ayrıntılarını belirtin:

- **Algılama adı**—algılama kuralının adı; benzersiz olmalıdır
- **Sıklık**— sorguyu çalıştırma ve bir işlemle ilgili aralıktır. [Aşağıdaki ek kılavuza bakın](#rule-frequency)
- **Uyarı başlığı**— kural tarafından tetiklenen uyarılarla görüntülenen başlık; benzersiz olmalıdır
- **Önem derecesi**— kural tarafından tanımlanan bileşenin veya etkinliğin olası riski
- **Kategori**: kural tarafından tanımlanan tehdit bileşeni veya etkinlik
- **MITRE ATT&, CK** [framework'te MITRE ATT'de](https://attack.mitre.org/) belgelenmiş olarak kural tarafından tanımlanan bir veya&CK tekniklerini kullanır. Bu bölüm kötü amaçlı yazılım, fidye yazılımı, şüpheli etkinlik ve istenmeyen yazılımlar gibi bazı uyarı kategorileri için gizlidir
- **Açıklama**— kural tarafından tanımlanan bileşen veya etkinlik hakkında daha fazla bilgi 
- **Önerilen eylemler:** Yanıtlayanların bir uyarıya yanıt olarak gerçekleştir olabileceği ek eylemler

#### <a name="rule-frequency"></a>Kural sıklığı
Yeni bir kural kaydeden bu kural, son 30 günlük verilerde çalışır ve eşleşmeleri denetler. Bundan sonra kural, seçtiğiniz sıklık temel alarak geri dönüş süresi uygulayarak sabit aralıklarla yeniden çalışır:

- **Her 24 saatte** bir; her 24 saatte bir çalışır ve son 30 gün içinde yapılan verileri denetleme
- **Her 12 saatte** bir; her 12 saatte bir çalışır ve son 24 saatte bir verileri denetleme
- **Her 3 saatte** bir çalışır; son 6 saatte bir verileri kontrol ederek her 3 saatte bir çalışır
- **Her saat** çalışır; saatte bir çalışır ve son 2 saatten verileri denetleme

Bir kuralı düzenley düzenlemeniz, ayarlandığı sıklık göre zamanlanan bir sonraki çalışma zamanında uygulanan değişikliklerle birlikte çalışmasına neden olur.



>[!TIP]
> Sorgunuza göre zaman filtrelerini arama süresiyle eşler. Geri arama süresi dışında olan sonuçlar yoksayılır.  

Algılamaları ne kadar yakın izlemek istediğinize uygun sıklığı seçin. Uyarılara yanıt verme kapasitenizi göz önünde bulundurarak göz önünde önünde olun.

### <a name="3-choose-the-impacted-entities"></a>3. Etkide olan varlıkları seçin.
Etkilenen veya etkilenen ana varlığı bulmanızı beklediğiniz sorgu sonuçları sütunlarını bulun. Örneğin, sorgu gönderen (`SenderFromAddress` veya ) ve alıcı `SenderMailFromAddress`() adreslerini`RecipientEmailAddress` döndürür. Bu sütunlardan hangisinin ana etkiyi temsil eden varlığın belirlenmesi, hizmetin ilgili uyarıları toplamalarına, olayları birbiriyle ilişkisine ve hedef yanıt eylemlerini bir araya toplamalarına yardımcı olur.

Her varlık türü (posta kutusu, kullanıcı veya cihaz) için yalnızca bir sütun seçin. Sorgunuz tarafından döndürülen sütunlar seç kabul edilir.

### <a name="4-specify-actions"></a>4. Eylemleri belirtin.
Özel algılama kuralınız, sorgu tarafından döndürülen cihazlarda, dosyalarda veya kullanıcılarda otomatik olarak eylem gerçekleştirebilirsiniz.

#### <a name="actions-on-devices"></a>Cihazlardaki eylemler
Bu eylemler, sorgu sonuçları sütunundaki `DeviceId` cihazlara uygulanır:
- **Cihazı yalıt**—Tam ağ yalıtım uygulamak ve cihazın herhangi bir uygulama veya hizmete bağlanmasını önlemek için Uç Nokta için Microsoft Defender kullanır. [Uç nokta makine yalıtım için Microsoft Defender hakkında daha fazla bilgi](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#isolate-devices-from-the-network)
- **Araştırma paketini toplayın**— ZIP dosyasında cihaz bilgilerini toplar. [Uç nokta soruşturma paketi için Microsoft Defender hakkında daha fazla bilgi](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#collect-investigation-package-from-devices)
- **Virüsten koruma taraması** çalıştırma— cihazda Windows Defender Virüsten Koruma tam ekran taraması yapar
- **Araştırmayı** başlatma— cihazda [otomatik bir](m365d-autoir.md) araştırma başlatılır
- **Uygulama yürütmeyi** kısıtla: Yalnızca Microsoft tarafından verilen bir sertifikayla imzalanan dosyaların yürütülmesine izin vermek için cihaz kısıtlamalarını ayarlar. [Uç nokta için Microsoft Defender ile uygulama kısıtlamaları hakkında daha fazla bilgi](/microsoft-365/security/defender-endpoint/respond-machine-alerts#restrict-app-execution)

#### <a name="actions-on-files"></a>Dosyalarda eylemler
Seçildiğinde, sorgu  sonuçlarının 'daki `SHA1``InitiatingProcessSHA1``SHA256`veya sütunundaki dosyalara Dosya karantina eylemlerini `InitiatingProcessSHA256` uygulamayı seçebilirsiniz. Bu eylem dosyayı geçerli bulunduğu konumdan siler ve bir kopyasını karantinaya yapıştırır.

#### <a name="actions-on-users"></a>Kullanıcılarda eylemler
Seçildiğinde, sorgu **sonuçlarının 'sinde** veya `AccountObjectId``InitiatingProcessAccountObjectId`sütununda kullanıcılar üzerinde Güvenliği ihlal edilmiş `RecipientObjectId` olarak işaretle eylemi alınır. Bu eylem, kullanıcı sayısı içinde risk düzeyini "yüksek" olarak Azure Active Directory ilgili kimlik koruma [ilkelerini tetikler](/azure/active-directory/identity-protection/overview-identity-protection).

> [!NOTE]
> Özel algılama kuralları için izin ver veya engelle eylemi şu anda bu kuralda Microsoft 365 Defender.

### <a name="5-set-the-rule-scope"></a>5. Kural kapsamını ayarlayın.
Kuralın hangi cihazları kapsdır takipte olduğunu belirtmek için kapsamı ayarlayın. Kapsam, cihazları denetleme kurallarını etkiler ve yalnızca posta kutularını ve kullanıcı hesaplarını veya kimlikleri denetleme kurallarını etkilemez.

Kapsamı ayarlarken şunları da seçebilirsiniz:

- Tüm cihazlar
- Belirli cihaz grupları

Yalnızca kapsam kapsamındaki cihazlardan veriler sorgular. Ayrıca, eylemler yalnızca bu cihazlarda  alınır.

### <a name="6-review-and-turn-on-the-rule"></a>6. Kuralı gözden geçirme ve açma.
Kuralı gözden geçirdikten sonra kaydetmek için **Oluştur'a** tıklayın. Özel algılama kuralı hemen çalışır. Eşleşmeleri denetleme, uyarılar oluşturma ve yanıt eylemleri yapma sıklığına bağlı olarak yeniden çalışır.


>[!Important] 
>Verimlilik ve verimlilik için özel algılamaların düzenli olarak gözden geçir olması gerekir. Doğru uyarıları tetikleyen algılamalar oluşturarak emin olmak için Var olan özel algılama kurallarını yönetme'de yer alan adımları takip eden mevcut özel algılamalarınızı [gözden geçirmek için zaman tanıyın](#manage-existing-custom-detection-rules). <br>  
Özel algılamalar tarafından oluşturulan tüm yanlış uyarılar kuralların belirli parametrelerini değiştirmenin gerekli olduğu belirtesin diye, özel algılamaların genişliği ve özelliği üzerinde denetiminiz olmalıdır.


## <a name="manage-existing-custom-detection-rules"></a>Varolan özel algılama kurallarını yönetme
Var olan özel algılama kurallarının listesini ekleyebilirsiniz, önceki çalıştırmalarını gözden geçirebilirsiniz ve tetikle yaptıkları uyarıları gözden geçirebilirsiniz. Ayrıca isteğe bağlı olarak bir kural çalıştırarak bunu değiştirebilirsiniz.

>[!TIP]
> Özel algılamalar tarafından yükseltilmiş uyarılar, uyarılar ve olay API'leri üzerinde kullanılabilir. Daha fazla bilgi için bkz[. Desteklenen Microsoft 365 Defender API'ler](api-supported.md).

### <a name="view-existing-rules"></a>Var olan kuralları görüntüleme

Var olan tüm özel algılama kurallarını görüntülemek için, **HuntingCustom detection rules (****Özel** >  algılama kuralları) makalesine gidin. Sayfada, aşağıdaki çalıştırma bilgilerine sahip tüm kurallar listeılmıştır:

- **Son çalıştırma**: sorgu eşleşmelerini denetlemesi ve uyarılar oluşturması için bir kural en son ne zaman çalıştır bırakıldı
- **Son çalıştırma durumu—** bir kuralın başarıyla çalıştırıp çalışmama durumu
- **Sonraki çalıştırma—** bir sonraki zamanlanan çalışma
- **Durum**— bir kuralın açık veya kapalı olup olmadığı

### <a name="view-rule-details-modify-rule-and-run-rule"></a>Kural ayrıntılarını görüntüleme, kuralı değiştirme ve kuralı çalıştırma

Özel bir algılama kuralı hakkında kapsamlı bilgi görüntülemek için **, Özel** algılama kuralları'  >  gidin ve kural adını seçin. Bundan sonra kural hakkında, çalıştırma durumu ve kapsamı gibi genel bilgileri görüntüebilirsiniz. Sayfa ayrıca tetiklenen uyarıların ve eylemlerin listesini de sağlar.

![Özel algılama kuralı ayrıntıları sayfası.](../../media/custom-detect-rules-view.png)<br>
*Özel algılama kuralı ayrıntıları*

Ayrıca, bu sayfada kural üzerinde aşağıdaki eylemleri de yapabilirsiniz:

- **Çalıştır**— kuralı hemen çalıştırın. Bu, sonraki çalıştırma aralığını da sıfırlar.
- **Düzenleme**—sorguyu değiştirmeden kuralı değiştirme
- **Sorguyu değiştirme**— gelişmiş avda sorguyu düzenleme
-  /  Aç **Kapatma**— kuralı etkinleştirme veya çalıştırmayı durdurma
- **Sil**— kuralı kapatın ve kaldırın

### <a name="view-and-manage-triggered-alerts"></a>Tetiklenen uyarıları görüntüleme ve yönetme

Kural ayrıntıları ekranında (**Özel algılamalar** >  > [Kural adı **]**), Kuralla eşleşmelerle oluşturulan uyarıları listeleyen Tetikleyicili uyarılar'a gidin. Ayrıntılı bilgileri görüntülemek ve aşağıdaki eylemleri yapmak için bir uyarı seçin:

- Uyarının durumunu ve sınıflandırmasını (doğru veya yanlış uyarı) ayarerek uyarıyı yönetme
- Uyarıyı bir olayla bağlama
- Gelişmiş avda uyarıyı tetikleyen sorguyu çalıştırın

### <a name="review-actions"></a>Eylemleri gözden geçirme
Kural ayrıntıları ekranında (**Özel algılamalar** >  > [Kural adı **]**), Kuralla eşleşmeleri temel alarak alınan eylemleri listeleyen Tetiklenen eylemler'e gidin.

>[!TIP]
>Bilgileri hızla görüntülemek ve tablodaki bir öğe üzerinde eylemde kullanmak için, tablonun sol &#10003; [Başlık] seçim sütununu kullanın.

>[!NOTE]
>Bu makaledeki bazı sütunlar Uç Nokta için Microsoft Defender'da kullanılamıyor olabilir. [Daha fazla Microsoft 365 Defender](m365d-enable.md) kullanarak tehdit yakalamak için çok daha fazla kaynağı açabilirsiniz. Gelişmiş av iş akışlarınızı Uç Nokta için Microsoft Defender'dan Microsoft 365 Defender için [Microsoft Defender'dan gelişmiş arama sorgularını geçirme makalesinde](advanced-hunting-migrate-from-mde.md) yer alan adımları takip edebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel algılamalara genel bakış](custom-detections-overview.md)
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Gelişmiş arama sorgusu dilini öğrenin](advanced-hunting-query-language.md)
- [Uç nokta için Microsoft Defender'dan gelişmiş arama sorgularını geçirme](advanced-hunting-migrate-from-mde.md)
