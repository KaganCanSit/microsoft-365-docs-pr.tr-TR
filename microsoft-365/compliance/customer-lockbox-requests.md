---
title: Müşteri Kasa İstekleri
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
search.appverid:
- BCS160
- MET150
- MOE150
ms.custom: admindeeplinkMAC
description: Bir sorunla karşı karşınıza çıkan bir Microsoft destek mühendisinin verilerinize nasıl erişeni denetlemenize olanak sağlayan Müşteri Kasa istekleri hakkında bilgi alın.
ms.openlocfilehash: 532b1b78c40725fa3558768a6b65beda9b8e05b2
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2022
ms.locfileid: "63504827"
---
# <a name="customer-lockbox-in-office-365"></a>Müşteri Kilidi Office 365

Bu makalede Müşteri Kilidi için dağıtım ve yapılandırma kılavuzu sunulmaktadır. Customer Lockbox, Exchange Online, SharePoint Online ve OneDrive İş'de verilere erişim isteklerini destekler. Diğer hizmetler için destek önerin, Geri Bildirim Portalı'nda bir [istek gönderin](https://feedbackportal.microsoft.com).

Uyumluluk tekliflerinden yararlanan kullanıcılarınızı lisanslama Microsoft 365 için, güvenlik Microsoft 365 uyumlulukla ilgili lisanslama & [bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

Müşteri Kilidi Microsoft'un sizin açık onayınız olmadan hizmet işlemleri yapmak için içeriğinize erişmesini mümkün değildir. Müşteri Kasası sizi Microsoft'un içeriğinize erişime izin vermek için kullandığı onay iş akışı sürecine getirir. Microsoft'un iş akışı süreci hakkında daha fazla bilgi edinmek için bkz. Microsoft iş [akışında ayrıcalıklı Microsoft 365](privileged-access-management-solution-overview.md).

Ara sıra Microsoft mühendisleri, hizmetle ilgili ortaya çıkan sorunları gidermeye ve düzeltmeye yardımcı olur. Mühendisler genellikle kapsamlı telemetri ve Microsoft'un hizmetleri için var olan hata ayıklama araçlarını kullanarak sorunları düzeltir. Bununla birlikte, bazı durumlarda sorunun temel nedenini saptamak ve sorunu düzeltmek için bir Microsoft mühendisinin içeriğinize erişmesi gerekir. Müşteri Kasa'sı, onay iş akışının son adımı olarak mühendisin sizin erişim isteğinde bulundurmanızı gerektirir. Bu size, isteği onaylama veya reddetme seçeneği sağlar ve içeriğinize doğrudan erişim denetimi sağlar.

### <a name="customer-lockbox-overview-video"></a>Müşteri Kasa genel bakış videosu

> [!VIDEO https://www.microsoft.com/videoplayer/embed/8fecf10b-1f03-4849-8b67-76d3d2a43f26?autoplay=false]

## <a name="customer-lockbox-workflow"></a>Müşteri Kasa iş akışı

Bu adımlar, bir Microsoft mühendisi Müşteri Kasa isteği başlatırken tipik iş akışının ana hatlarını içerir:

1. Kuruluşta başka biri posta kutusunda bir sorun Microsoft 365 deneyimler.

2. Kullanıcı sorunu giderdikten ancak düzeltedikten sonra Microsoft Desteği ile bir destek isteği açar.

3. Hizmet isteğini gözden alan bir Microsoft destek mühendisi, aynı onarımda sorunun onarılması için kuruluşun kiracısına erişmenin gerekli olduğunu Exchange Online.

4. Microsoft destek mühendisi Müşteri Kasa isteği aracında oturum açir ve kuruluşun kiracı adını, hizmet isteği numarasını ve mühendisin verilere erişmesi gereken tahmini zamanı içeren bir veri erişim isteği yapar.

5. Microsoft Destek Yöneticisi isteği onay verdikten sonra, Müşteri Kilidi belirlenen onaylayanı kuruluşa, Microsoft'un beklemedeki erişim isteğiyle ilgili bir e-posta bildirimi gönderir.

    ![Müşteri Kilit Kutusu e-posta bildirimi örneği.](../media/CustomerLockbox1.png)

   Bu kişilerde Müşteri Kasa [erişimi onaylayan](/office365/admin/add-users/about-admin-roles) yönetici rolüne atanan Microsoft 365 yönetim merkezi Kutusu isteklerini onaylar.

6. Onaylayan, e-Microsoft 365 yönetim merkezi ve isteği onaylar. Bu adım, denetim günlüğünde aramaarak kullanılabilen bir denetim kaydı oluşturulmasını tetikler. Daha fazla bilgi için bkz [. Müşteri Kasa isteklerini denetleme](#auditing-customer-lockbox-requests).

   Müşteri isteği reddederse veya 12 saat içinde isteği onaylamazsa, isteğin süresi dolar ve Microsoft mühendisine erişim izni verilmez.

   > [!IMPORTANT]
   > Microsoft, Müşteri Kilidi e-posta bildirimlerine, posta kutusunda oturum açmanızı gerektiren hiçbir Office 365.

7. Kuruluştan onaylayan kişi isteği onay verdikten sonra, Microsoft mühendisi onay iletisi alır, Exchange Online'de kiracıda oturum görüntüler ve müşterinin sorunu düzeltir. Microsoft mühendisleri, erişimin otomatik olarak iptal edildiği sorunu düzeltmek için istenen süreye sahip olur.

> [!NOTE]
> Microsoft mühendisi tarafından gerçekleştirilen tüm eylemler denetim günlüğüne kaydedilir. Bu denetim kayıtlarını arayabilir ve gözden geçirabilirsiniz.

## <a name="turn-customer-lockbox-requests-on-or-off"></a>Müşteri Kasa isteklerini açma veya kapatma

Müşteri Kilidi denetimlerini müşteri Microsoft 365 yönetim merkezi. Müşteri Kilidi'i açabilirsiniz, Microsoft'un kiracının içeriğine erişmeden önce kuruluş onayını alması gerekir.

1. Genel yönetici veya Müşteri Kasa erişimi onaylayan rolünün atandığı bir iş  veya okul hesabı kullanarak oturum [https://admin.microsoft.com](https://admin.microsoft.com) açın ve gidin.

2.  >  Ayarlar **Org** >  Ayarlar <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security & seçin**</a>.

3. Güvenlik **ve & seçin** ve ardından sol **sütunda Müşteri** Kilidi'ne tıklayın. Tüm **veri erişimi istekleri için onay gerektir onay** kutusunu işaretleyin ve özelliği açmak için değişiklikleri kaydedin.

    ![Require approval for Customer Lockbox](../media/CustomerLockbox4-new.png)

## <a name="approve-or-deny-a-customer-lockbox-request"></a>Müşteri Kasa isteğini onaylama veya reddetme

1. Genel yönetici veya Müşteri Kasa erişimi onaylayan rolünün atandığı bir iş  veya okul hesabı kullanarak oturum [https://admin.microsoft.com](https://admin.microsoft.com) açın ve gidin.

2. Müşteri **Kasa > Desteği'ne tıklayın**.

    ![Destek'e ve ardından Müşteri Kasa İstekleri'ne tıklayın.](../media/CustomerLockbox5.png)

    Müşteri Kasa isteklerinin listesi görüntülenir.

    ![Müşteri Kasa isteklerinin listesi.](../media/CustomerLockbox6.png)

3. Bir Müşteri Kasa isteği seçin ve ardından Onayla'ya veya **Reddet'e** **tıklayın**.

    ![Müşteri Kasa isteklerini onaylar.](../media/CustomerLockbox7.png)

    Müşteri Kasa isteğinin onayıyla ilgili bir onay iletisi görüntülenir.

    ![Müşteri Kasa isteklerini reddedin.](../media/CustomerLockbox8.png)

> [!NOTE]
> Microsoft destek Set-AccessToCustomerDataRequest sizin verilerinize erişimi denetlemeye yönelik müşteri kasa isteklerini onaylamak, Microsoft 365 veya iptal etmek için Set-AccessToCustomerDataRequest cmdlet'ini kullanın. Daha fazla bilgi için bkz. [Set-AccessToCustomerDataRequest](/powershell/module/exchange/set-accesstocustomerdatarequest).

## <a name="auditing-customer-lockbox-requests"></a>Müşteri Kasa isteklerini denetleme

Müşteri Kasa isteklerine karşılık gelen denetim kayıtları, müşteri denetim Microsoft 365 kaydedilir. Arama sonuçlarında denetim günlüğü arama [aracını kullanarak bu günlüklere](search-the-audit-log-in-security-and-compliance.md) Microsoft 365 uyumluluk merkezi. Müşteri Kasa isteğini kabul etme veya reddetmeyle ilgili eylemler ve Microsoft mühendisleri tarafından gerçekleştirilen eylemler de (erişim istekleri onaylandıktan sonra) denetim günlüğüne kaydedilir. Bu denetim kayıtlarını arayabilir ve gözden geçirabilirsiniz.

### <a name="search-the-audit-log-for-activity-related-to-customer-lockbox-requests"></a>Denetim günlüğünde Müşteri Kasa istekleriyle ilgili etkinliği arama

Müşteri Kilit Kutusu isteklerini izlemek üzere denetim günlüğünü kullanamadan önce, denetim günlüğünde arama yapmak için izin atama gibi, denetim günlüğünü ayarlamak için atılması gereken bazı adımlar vardır. Daha fazla bilgi için bkz[. DenetimDe Temel Microsoft 365](set-up-basic-audit.md). Kurulumu tamamlandıktan sonra, Müşteri Kilidi ile ilgili denetim kayıtlarının iadesini sağlamak üzere bir denetim günlüğü araması sorgusu oluşturmak için bu adımları kullanın:

1. <https://compliance.microsoft.com> adresine gidin.
  
2. Denetim günlüğünde arama yapmak için uygun izinlerin atandığı bir hesabı kullanarak oturum açın.

3. Uyumluluk merkezinin sol bölmesinde Denetim'i **seçin**.

    **Denetim** sayfasındaki **Arama** sekmesi görüntülenir.

    ![Denetim günlüğü arama sayfası.](../media/auditlogsearch1.png)
  
4. Aşağıdaki arama ölçütlerini yapılandırma:

   1. **Başlangıç tarihi ve** **Bitiş tarihi**. Bir tarih ve saat aralığında 2013 olayları görüntülemek için, o tarih ve saat aralığını seçin.  

   2. **Etkinlikler**. Aramanın tüm etkinlikler için denetim kayıtlarını döndürt etmek için bu alanı boş bırakın. Bu, Müşteri Kasa istekleri ve Microsoft mühendisleri tarafından gerçekleştirilen ilgili etkinlikle ilgili tüm denetim kayıtlarının geri dönmesi için gereklidir.

   3. **Kullanıcılar.** Bu alanı boş bırakın.

   4. **Dosya, klasör veya site**. Bu alanı boş bırakın.

5. Arama **ölçütlerinizi** kullanarak arama çalıştırmak için Ara'ya tıklayın.

    Arama sonuçları birkaç dakika sonra görüntülenir. Arama tamamlandıktan sonra, sayfaya daha fazla arama sonucu eklenir.

6. Etkinlik sütunundaki **değerlere** göre sonuçları alfabetik olarak sıralamak için Etkinlik sütunundaki **üst bilgiye** tıklayın.

7. Sayfayı aşağı kaydırın ve **Set-AccessToCustomerDataRequest etkinliğinin yer aldığı denetim kayıtlarına bakın**. Bu etkinlikli kayıtlar, kuruluşta bir Müşteri Kasa isteğini onaylayan veya reddeden bir onaylayanla ilgilidir.

8. Alternatif olarak, Kullanıcı sütunundaki değerleri **kullanarak** sonuçları alfabetik olarak sıralamak için Kullanıcı sütunundaki üst **bilgiye** tıklayın. Onaylanan Müşteri Kasa **isteğine yanıt olarak bir Microsoft** mühendisinin gerçekleştirilen etkinlikleri gösteren Microsoft İşleci değerinin ne olduğunu bakın. Etkinlik **sütununda** , mühendis tarafından gerçekleştirilen eylem görüntülenir.

      ![Denetim kayıtlarını görüntülemek için "Microsoft İşleci" filtresini uygulama](../media/CustomerLockbox10.png)

9. Sonuç listesinde, görüntülemek için bir denetim kaydına tıklayın.

### <a name="export-the-audit-log-search-results"></a>Denetim günlüğü arama sonuçlarını dışarı aktarma

Ayrıca, denetim günlüğü arama sonuçlarını bir CSV dosyasına aktararak, bir Müşteri Kasa erişim isteğiyle ilgili denetim kayıtlarını daha kolay bulmak ve görüntülemek için filtreleme ve sıralama özelliklerini kullanmak için dosyayı Excel'de açabilirsiniz.

Denetim kayıtlarını dışarı aktarmada, önceki adımları kullanarak denetim günlüğünde arama yapın. Arama tamamlandığında, arama sonuçları **sayfasının > Tüm sonuçları** indir'i seçin. Dışarı aktarma işlemi tamamlandığında, CSV dosyasını yerel bilgisayarınıza indirebilirsiniz. Daha ayrıntılı yönergeler için bkz [. Denetim günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme](export-view-audit-log-records.md).

Dosyayı indirdikten sonra, Excel'de açabilir ve **ardından Set-AccessToCustomerDataRequest** etkinliklerinin denetim kayıtlarını görüntülemek için İşlemler sütununa filtre indirebilirsiniz. Ayrıca, Microsoft mühendisleri tarafından gerçekleştirilen etkinliklere yönelik denetim kayıtlarını görüntülemek için **UserIds** sütununa da filtre ( **Microsoft** İşleci değerini kullanarak) filtre edebilirsiniz.

> [!NOTE]
> CSV dosyasında denetim kayıtları görüntülenirken, Denetim Verileri sütununda ek **bilgiler** yer arilmektedir. Bu sütundaki bilgiler, özellik *:* değer çiftleri virgülle ayrılmış olarak yapılandırılan birden çok özelliği içeren bir JSON nesnesinde yer almaktadır. Excel'daki Power Query Düzenleyicisi'nde JSON dönüştürme özelliğini kullanarak Denetim Verileri sütunundaki JSON nesnesinde yer alan her özelliği birden çok sütuna  bölebilir ve bu şekilde her özelliğin kendi sütunu olur. Bu, bu bilgileri yorumlamayı kolaylaştırır. Ayrıntılı yönergeler için bkz [. Power Query Düzenleyicisi'ni kullanarak dışarı aktarıldı denetim günlüğünü biçimlendirme](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).

### <a name="use-powershell-to-search-and-export-audit-records"></a>Denetim kayıtlarını aramak ve dışarı aktarma için PowerShell kullanma

Denetim arama aracının kullanımına alternatif Microsoft 365 uyumluluk merkezi, Exchange Online PowerShell'de [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) cmdlet'ini çalıştırmaktır. PowerShell kullanmanın bir avantajı, Müşteri Kasa isteğiyle ilgili Microsoft mühendisleri tarafından gerçekleştirilen **Set-AccessToCustomerDataRequest** etkinliklerini veya etkinliklerini özel olarak arayabilirsiniz.

[Exchange Online PowerShell'e](/powershell/exchange/connect-to-exchange-online-powershell) bağlandikten sonra, aşağıdaki komutlardan birini çalıştırın. Yer tutucuları belirli bir tarih aralığıyla değiştirin.

#### <a name="search-for-set-accesstocustomerdatarequest-activities"></a>Etkinlik Set-AccessToCustomerDataRequest arama

```powershell
Search-UnifiedAuditLog -StartDate xx/xx/xxxx -EndDate xx/xx/xxxx -Operations Set-AccessToCustomerDataRequest
```

#### <a name="search-for-activities-performed-by-microsoft-engineers"></a>Microsoft mühendisleri tarafından gerçekleştirilen etkinlikleri arama

```powershell
Search-UnifiedAuditLog -StartDate xx/xx/xxxx -EndDate xx/xx/xxxx -UserIds "Microsoft Operator"
```

Daha fazla bilgi ve örnekler için bkz [. PowerShell kullanarak denetim günlüğü kayıtlarını arama ve dışarı aktarma](export-view-audit-log-records.md#use-powershell-to-search-and-export-audit-log-records).

Ayrıca denetim günlüğünde arama yapmak ve sonuçları CSV dosyasına dışarı aktararak kullanmak için kullanabileceğiniz bir PowerShell betiği de sağladık. Daha fazla bilgi için bkz [. Denetim günlüğünde arama yapmak için PowerShell betiği kullanma](audit-log-search-script.md).

### <a name="audit-record-for-a-customer-lockbox-request"></a>Müşteri Kasa isteği için denetim kaydı

Bir kişi bir Müşteri Kasa isteğini onaylar veya reddederken, denetim kaydı aşağıdaki bilgileri içeren denetim günlüğüne kaydedilir.

| Denetim kaydı özelliği| Açıklama|
|:---------- |:----------|
| Tarih       | Müşteri Kasa isteğinin onaylandı veya reddedilen tarih ve saat.
| IP adresi | Onaylayan tarafından isteği onaylamak veya reddetmek için kullanılan makinenin IP adresi. |
| Kullanıcı       | Hizmet hesabı BOXServiceAccount@\[customerforest.prod.outlook.com\].            |
| Etkinlik   | Set-AccessToCustomerDataRequest; bu, Müşteri Kasa isteğini onaylar veya reddederken günlüğe kaydedilen denetim etkinliğidir.                                |
| Öğe       | Müşteri Kasa isteğinin Guid'i                             |

Aşağıdaki ekran görüntüsünde, onaylanmış bir Müşteri Kasa isteğine karşılık gelen bir denetim kaydı örneği yer almaktadır. Bir Müşteri Kasa isteği reddedilirse, **ApprovalDecision parametresinin** değeri Reddet **olur.**

![Onaylanan bir Müşteri Kasa isteği için denetim kaydı.](../media/CustomerLockbox9.png)

### <a name="audit-record-for-an-action-performed-by-a-microsoft-engineer"></a>Microsoft mühendisi tarafından gerçekleştirilen eylemin denetim kaydı

Müşteri Kasa isteği onaylandıktan (ve bu da müşteri içeriğine erişmeye neden olabilir) Microsoft mühendisi tarafından gerçekleştirilen eylemler denetim günlüğüne kaydedilir. Bu kayıtlar aşağıdaki bilgileri içerir.

| Denetim kaydı özelliği| Açıklama|
|:---------- |:----------|
| Tarih       | Eylemin gerçekleştir bitiş tarihi. Bu eylemin gerçekleştir zamanı, Müşteri Kasa isteğinin onaylandıktan sonra 4 saat içinde yapılacaktır.              |
| IP adresi | Microsoft mühendisinin kullandığı makinenin IP Adresi. |
| Kullanıcı       | Microsoft İşleci; bu değer kaydın bir Müşteri Kasa isteğiyle ilişkili olduğunu gösterir.                                  |
| Etkinlik   | Microsoft mühendisi tarafından gerçekleştirilen etkinliğin adı.|
| Öğe       | \<empty\>                                             |

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

#### <a name="which-microsoft-365-services-does-customer-lockbox-apply-to"></a>Müşteri Microsoft 365 hangi hizmetler için geçerlidir?

Customer Lockbox şu anda Exchange Online, SharePoint Online ve OneDrive İş.

#### <a name="is-customer-lockbox-available-to-all-customers"></a>Müşteri Kilidi tüm müşteriler tarafından kullanılabilir mi?

Customer Lockbox, Microsoft 365 veya Office 365 E5 abonelikleriyle birlikte sunulmaktadır ve Bilgi Koruma ve Uyumluluk veya Gelişmiş Uyumluluk eklenti aboneliği ile diğer planlara eklenebilir. Daha [fazla bilgi için Planlar](https://products.office.com/business/office-365-enterprise-e5-business-software) ve fiyatlandırma'ya bakın.

#### <a name="what-is-customer-content"></a>Müşteri içeriği nedir?

Müşteri içeriği, hizmet ve uygulama kullanıcılarının oluşturduğu Microsoft 365 verilerdir. Müşteri içeriğine örnekler:

- E-posta gövdesi veya e-posta ekleri

- SharePoint içeriğini değiştirme

- Bir dosyanın gövdesinde SharePoint bilgi

- Skype Kurumsal dosyası gövde

- Anlık iletiler (IM) veya sesli konuşmalar

- Müşteri tarafından oluşturulan blob veya yapılandırılmış depolama verileri (örneğin, SQL Kapsayıcıları)

- Müşteriye ait güvenlik bilgileri (örneğin, sertifikalar, şifreleme anahtarları ve parolalar)

- Müşteri içeriği kalırsa, çıkarlıklar ve sonraki tüm çıkarlıklar

Güven Merkezi'nde müşteri Office 365 daha fazla bilgi için Office 365 [bakın](https://products.office.com/business/office-365-trust-center-privacy/).

#### <a name="who-is-notified-when-there-is-a-request-to-access-my-content"></a>Who erişim isteği olduğunda bu bilgi ne zaman bildirilecek?

Genel yöneticilere ve Müşteri Kilidi erişimi onaylayan yönetici rolüne atanan herkes bilgilenir. Bunlar, Müşteri Kasa istekleri için onaylayan kullanıcılarla aynıdır.

#### <a name="who-can-approve-or-reject-these-requests-in-my-organization"></a>Who bu istekleri kuruluşumda onaylar veya reddeder miyim?

Genel yöneticiler ve Müşteri Kasa erişimi onaylayan yönetici rolüne atanan herkes Müşteri Kilidi isteklerini onaylar. Müşteriler kendi kuruluşlarına bu rol atamalarını kontrol eder.

#### <a name="how-do-i-opt-in-to-customer-lockbox"></a>Müşteri Kasa'sı'ne nasıl kabul  yapabilirim?

Genel yönetici müşteri kutusunda Müşteri Kilidi'yi etkinleştirebilirsiniz Microsoft 365 <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a>.

#### <a name="if-i-approve-a-customer-lockbox-request-what-can-the-engineer-do-and-how-will-i-know-what-the-microsoft-engineer-did"></a>Bir Müşteri Kasa isteğini onaylarsanız, mühendisin ne yaptığını ve Microsoft mühendisinin ne yaptığını nasıl bilebilirsiniz?

Bir Müşteri Kasa isteğini onay verdikten sonra, Microsoft mühendisi önceden onaylanmış cmdlet'leri kullanarak müşteri içeriğine erişmek için bu gerekli ayrıcalıkları verdi. Müşteri Kasa isteklerine yanıt olarak Microsoft mühendisleri tarafından  alınan eylemler, Güvenlik ve Uyumluluk Merkezi'nde denetim günlüğüne & erişilebilir.

#### <a name="how-do-i-know-that-microsoft-follows-the-approval-process"></a>Microsoft'un onay sürecini takip edeni nasıl bilebilirsiniz?

Kuruluş sayfasındaki Müşteri Kasa isteği geçmişiyle, kuruluşta yöneticilere ve onaylayanlara gönderilen e-posta onay bildirimlerine çapraz [başvuru Microsoft 365 yönetim merkezi](https://go.microsoft.com/fwlink/p/?linkid=2024339).

En son [SOC 1 SSAE 16 denetim raporuna](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=91592749-e86a-43ac-801e-121382614681&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_SOC%20%2F%20SSAE%2016%20Reports) Customer Lockbox dahildir. Daha fazla ayrıntı için, en son raporları Microsoft Hizmet Güveni [Portalı'nın içinde bulabilirsiniz](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=91592749-e86a-43ac-801e-121382614681&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_SOC%20%2F%20SSAE%2016%20Reports).

#### <a name="can-microsoft-modify-the-list-of-approvers-for-my-tenant-if-not-how-is-it-prevented"></a>Microsoft kiracım için onaylayanlar listesini değiştirebilir mi? Yoksa nasıl önlenebilir?

Yalnızca genel yönetici, Müşteri Kilidi isteklerini kimlerin onaylaydığını belirtebilirsiniz. Bu, isteği kimlerin onay yalnızca Genel yönetici Azure Active Directory belirtecekleri anlamına gelir. Genel Yönetici grubu üyeliği Azure Active Directory tarafından yönetilir.

#### <a name="what-if-i-need-more-information-about-a-content-access-request-to-approve-it"></a>İçerik erişim isteğini onaylamak için daha fazla bilgiye ihtiyacım olursa ne olur?

Her Müşteri Kasa isteği bir müşteri Microsoft 365 numarası içerir. İstek hakkında daha fazla bilgi almak için Microsoft Desteği'ne başvurarak bu hizmet numarasına başvurabilirsiniz.

#### <a name="when-a-customer-lockbox-request-is-approved-how-long-are-the-permissions-valid"></a>Bir Müşteri Kasa isteği onaylandıktan sonra izinler ne kadar süre geçerlidir?

Şu anda Microsoft mühendisine verilen erişim izinleri için en uzun süre 4 saattir. Ayrıca Microsoft mühendisi daha kısa bir süre de talep edilebilir.

#### <a name="how-can-i-get-a-history-of-all-customer-lockbox-requests"></a>Tüm Müşteri Kasa isteklerinin geçmişini nasıl elde  edebilirsiniz?

Tüm Müşteri Kasa istekleri müşteri [Microsoft 365 yönetim merkezi.](https://go.microsoft.com/fwlink/p/?linkid=2024339)

#### <a name="how-do-i-correlate-the-content-access-requests-with-the-related-audit-logs"></a>İçerik erişim isteklerini ilgili denetim günlükleri ile nasıl ilişkili yapabilirim?

Uyumluluk Merkezi Etkinlik Akışı, Müşteri Kasa'nın günlük etkinliklerini içerir. Müşteriler, etkinlik akışından Gelen e-posta isteğiyle Müşteri Kilidi günlük etkinliklerine çapraz başvurular gerçekleştirebilirsiniz.

#### <a name="what-happens-when-a-customer-doesnt-respond-to-a-customer-lockbox-request"></a>Müşteri bir Müşteri Kasa isteğine yanıt vermese ne olur?

Müşteri Kasa istekleri için varsayılan süre 12 saattir. Bir isteği 12 saat içinde yanıtlamazsanız, isteğin süresi dolar.

#### <a name="what-does-microsoft-do-when-a-customer-rejects-a-customer-lockbox-request"></a>Müşteri bir Müşteri Kasa isteğini reddederken Microsoft ne yapar?

Müşteri bir Müşteri Kasa isteğini reddederse, müşteri içeriğine erişim olmaz. Organizasyonunuzu ziyaret eden bir kullanıcı, sorunu çözmek için Microsoft'un müşteri içeriğine erişmesini gerektiren bir hizmet sorunuyla devam ederse, hizmet sorunu kalıcı olabilir ve Microsoft kullanıcıya bu konuda bilgi sağlar.

#### <a name="how-do-i-set-up-alerts-whenever-a-request-has-been-approved"></a>bir istek onaylandır her onaylandıktan sonra uyarıları nasıl kuracaksınız?

Yöneticileri uyaracak yerleşik bir seçenek yoktur. Bununla birlikte, yöneticiler Bulut Uygulamaları için [Microsoft Defender'ı kullanarak uyarılar kurabilirsiniz](/cloud-app-security/getting-started-with-cloud-app-security#to-create-policies).

#### <a name="does-customer-lockbox-protect-against-data-requests-from-law-enforcement-agencies-or-other-third-parties"></a>Müşteri Kilidi, hukuk davaları veya diğer üçüncü tarafların veri isteklerine karşı koruma sağlar mı?

Hayır. Microsoft, müşteri verileri için üçüncü taraf isteklerini çok ciddiye alır. Bir bulut hizmet sağlayıcısı olarak, Microsoft her zaman müşteri verileri gizliliğinin korunmasını desteklemektedir. Bir mahkeme celdi almamız durumunda, Microsoft her zaman bilgi almak için üçüncü bir tarafla müşteriyi yeniden yönlendirmeyi dener. (Brad Smith'in blog'ını okuyun: [Müşteri verilerini kamu hizmetinden koruma](https://blogs.microsoft.com/blog/2013/12/04/protecting-customer-data-from-government-snooping/)). Microsoft'un [aldığı hukuki yaptırım](https://www.microsoft.com/corporate-responsibility/lerr) taleplerine ilişkin ayrıntılı bilgileri düzenli aralıklarla yayımlarız.

Daha fazla [bilgi için Üçüncü](https://www.microsoft.com/trustcenter/default.aspx) taraf veri istekleriyle ilgili Microsoft Güven Merkezi'ne ve Çevrimiçi Hizmetler Koşulları'nın "Müşteri [](https://www.microsoft.com/Licensing/product-licensing/products.aspx) Verilerini Açıklama" bölümüne bakın.

#### <a name="how-does-microsoft-ensure-that-a-member-of-its-staff-doesnt-have-standing-access-to-customer-content-in-office-365-applications"></a>Microsoft, personelinin bir üyesinin kendi çalışanlarının kendi uygulamalarını kullanarak müşteri içeriğine erişemlerini nasıl Office 365 sağlar?

Microsoft, erişim denetim sistemleri ve güvenlik önlemleri yoluyla bu erişim denetim sistemlerine müdahale girişimleri tanımlamak ve bunlara müdahale etmek için kapsamlı önlemler almaktadır. Microsoft 365 ayrıcalık ve tam zamanlı erişim ilkeleriyle çalışır. Bu nedenle, Hiçbir Microsoft personelinin müşteri içeriğine sürekli olarak erişme izni yoktur. İzin verildiyse, sınırlı bir süre boyunca devam eder. 

Microsoft 365, hizmet içinde işlem ve yönetim işlevlerini gerçekleştirebilme  olanağını kullanan izinlere sahip istekler üzerinde işlem yapmak için Kasa adlı bir erişim denetim sistemi kullanır. İşleç, Kasa kullanarak müşteri içeriğine erişim isteğinda bulundur gerektirir ve buna göre, erişim verilmeden önce ikinci bir kişinin istek üzerinde işlem (örneğin, onaylar) gerçekleştirsini gerektirir. Bu ikinci kişi istekte bulunan kişi olamıyor ve müşteri içeriğine erişimi onaylamak için atanmış olması gerekir. Ancak istek onaylanırsa, işleç müşteri içeriğine geçici erişim ediner. Yükseltme dönemi sona erdikten sonra Lockbox erişimi iptal ediyor.

Microsoft genel güvenlik [uygulamaları hakkında daha ayrıntılı](https://www.microsoft.com/licensing/product-licensing/products) bilgi için Çevrimiçi Hizmetler Koşulları'na bakın.

#### <a name="under-what-circumstances-do-microsoft-engineers-need-access-to-my-content"></a>Microsoft mühendislerinin hangi koşullarda içeriğime erişmesi gerekiyor?

Microsoft mühendislerinin müşteri içeriğine erişmesi gereken en yaygın senaryo, müşterinin sorun giderme için erişim gerektiren bir destek isteğite bulunduğu durumdur. Temel ilkelerden biri Microsoft 365 hizmetin Microsoft'un müşteri içeriğine erişimi olmadan çalışmasıdır. Microsoft tarafından gerçekleştirilen hizmet işlemlerinin neredeyse tamamı tümüyle otomatiktir ve insan katılımı üst düzeyde denetlenmektedir ve müşteri içeriğinden uzaklaştırıldı. Müşteri Microsoft Microsoft 365 özel bir isteği onaylayana kadar, hizmeti desteklemeye yönelik müşteri içeriğine erişimin gerekli olmadığını ifade etmektir.

#### <a name="i-already-thought-my-data-was-secure-with-the-microsoft-cloud-so-why-do-i-need-customer-lockbox"></a>Verilerimin Microsoft bulutuyla güvende olduğunu sanıyordum, neden Müşteri Kasa'sı gerekiyor?

Customer Lockbox, müşterilere hizmet işlemleri için açık erişim yetkisi verme olanağı sunarak ek bir denetim katmanı sağlar. Açık veri erişim yetkisi için yordamların hazır olduğunu ortaya atarak, Müşteri Kilidi müşterilerin HIPAA ve FEDRAMP gibi belirli uyumluluk yükümlülüklerini karşılamasına da yardımcı olur.
