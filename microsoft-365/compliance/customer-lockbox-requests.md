---
title: Müşteri Kasası istekleri
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
description: Microsoft destek mühendisinin bir sorunla karşılaştığınızda verilerinize nasıl erişebileceğini denetlemenize olanak sağlayan Müşteri Kasası istekleri hakkında bilgi edinin.
ms.openlocfilehash: cf9a2a6d682ca87e97986389f640a536775ca014
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953836"
---
# <a name="microsoft-purview-customer-lockbox"></a>Microsoft Purview Müşteri Kasası

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Bu makalede Müşteri Kasası için dağıtım ve yapılandırma yönergeleri sağlanır. Müşteri Kasası Exchange Online, SharePoint Online, OneDrive İş ve Teams verilerine erişme isteklerini destekler. Diğer hizmetler için destek önermek için [Geri Bildirim Portalı'nda](https://feedbackportal.microsoft.com) bir istek gönderin.

Kullanıcılarınızın Microsoft Purview tekliflerinden yararlanması için lisanslama seçeneklerini görmek [için güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzuna](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance) bakın.

Müşteri Kasası, Microsoft'un açık onayınız olmadan hizmet işlemleri yapmak için içeriğinize erişememesini sağlar. Müşteri Kasası sizi Microsoft'un yalnızca yetkili isteklerin içeriğinize erişim izni vermek için kullandığı onay iş akışı sürecine getirir. Microsoft'un iş akışı süreci hakkında daha fazla bilgi edinmek için bkz [. Ayrıcalıklı erişim yönetimi](privileged-access-management-solution-overview.md).

Microsoft mühendisleri bazen hizmette ortaya çıkan sorunları gidermeye ve düzeltmeye yardımcı olur. Mühendisler genellikle Microsoft'un hizmetleri için kullandığı kapsamlı telemetri ve hata ayıklama araçlarını kullanarak sorunları çözer. Ancak bazı durumlarda, kök nedeni belirlemek ve sorunu çözmek için bir Microsoft mühendisinin içeriğinize erişmesi gerekir. Müşteri Kasası, mühendisin onay iş akışının son adımı olarak sizden erişim istemesini gerektirir. Bu, kuruluşunuz için isteği onaylama veya reddetme ve içeriğinize doğrudan erişim denetimi sağlama seçeneği sunar.

## <a name="customer-lockbox-overview-video"></a>Müşteri Kasasına genel bakış videosu

> [!VIDEO https://www.microsoft.com/videoplayer/embed/8fecf10b-1f03-4849-8b67-76d3d2a43f26?autoplay=false]

## <a name="customer-lockbox-workflow"></a>Müşteri Kasası iş akışı

Bu adımlar, bir Microsoft mühendisinin Müşteri Kasası isteği başlattığı tipik iş akışını özetler:

1. Kuruluşta bir kişi Microsoft 365 posta kutusuyla ilgili bir sorun yaşar.

2. Kullanıcı sorunu giderdikten ancak düzeltemedikten sonra Microsoft Desteği ile bir destek isteği açar.

3. Bir Microsoft destek mühendisi, hizmet isteğini inceler ve sorunu onarmak için kuruluşun kiracısına erişme gereksinimini belirler.

4. Microsoft destek mühendisi Müşteri Kasası istek aracında oturum açar ve kuruluşun kiracı adını, hizmet isteği numarasını ve mühendisin verilere erişmesi gereken tahmini süreyi içeren bir veri erişim isteğinde bulunur.

5. bir Microsoft Desteği yöneticisi isteği onayladıktan sonra, Müşteri Kasası kuruluşa atanan onaylayana Microsoft'tan gelen bekleyen erişim isteği hakkında bir e-posta bildirimi gönderir.

    ![Müşteri Kasası e-posta bildirimi örneği.](../media/CustomerLockbox1.png)

   Microsoft 365 yönetim merkezi'da [Müşteri Kasası erişim onaylayıcısı](/office365/admin/add-users/about-admin-roles) yönetici rolü atanmış olan herkes Müşteri Kasası isteklerini onaylayabilir.

6. Onaylayan Microsoft 365 yönetim merkezi oturum açar ve isteği onaylar. Bu adım, denetim günlüğünde arama yaparak kullanılabilir bir denetim kaydı oluşturulmasını tetikler. Daha fazla bilgi için bkz. [Müşteri Kasası isteklerini denetleme](#auditing-customer-lockbox-requests).

   Müşteri isteği reddederse veya isteği 12 saat içinde onaylamazsa, isteğin süresi dolar ve Microsoft mühendisine erişim verilmez.

   > [!IMPORTANT]
   > Microsoft, Müşteri Kasası e-posta bildirimlerine Office 365 oturum açmanızı gerektiren hiçbir bağlantı içermez.

7. Kuruluştan onaylayan isteği onayladıktan sonra Microsoft mühendisi onay iletisini alır, kiracıda oturum açar ve müşterinin sorununu çözer. Microsoft mühendisleri, erişimin otomatik olarak iptal edilmesinin ardından oluşan sorunu düzeltmek için istenen süreye sahiptir.

> [!NOTE]
> Bir Microsoft mühendisi tarafından gerçekleştirilen tüm eylemler denetim günlüğüne kaydedilir. Bu denetim kayıtlarını arayabilir ve gözden geçirebilirsiniz.

## <a name="turn-customer-lockbox-requests-on-or-off"></a>Müşteri Kasası isteklerini açma veya kapatma

müşteri kasası denetimlerini Microsoft 365 yönetim merkezi açabilirsiniz. Müşteri Kasası'nı açtığınızda, Microsoft'un kiracınızın içeriğinden herhangi birine erişmeden önce kuruluşunuzun onayını alması gerekir.

1. Genel yöneticinin veya **Müşteri Kasası erişim onaylayıcısı** rolünün atandığı bir iş veya okul hesabı kullanarak adresine gidin [https://admin.microsoft.com](https://admin.microsoft.com) ve oturum açın.

2. **Ayarlar** >  **Org Ayarlar** >  **Güvenlik & Gizlilik'i** seçin.

3. **Güvenlik & Gizlilik'i** ve ardından sol sütunda **Müşteri Kasası'nı** seçin. **Tüm veri erişim istekleri için onay iste** onay kutusunu işaretleyin ve özelliği açmak için değişiklikleri kaydedin.

    ![Require approval for Customer Lockbox](../media/CustomerLockbox4-new.png)

## <a name="approve-or-deny-a-customer-lockbox-request"></a>Müşteri Kasası isteğini onaylama veya reddetme

1. Genel yöneticinin veya **Müşteri Kasası erişim onaylayıcısı** rolünün atandığı bir iş veya okul hesabı kullanarak adresine gidin [https://admin.microsoft.com](https://admin.microsoft.com) ve oturum açın.

2. **Destek > Müşteri Kasası İstekleri'ni** seçin.

    ![Destek'e ve ardından Müşteri Kasası İstekleri'ne tıklayın.](../media/CustomerLockbox5.png)

    Müşteri Kasası isteklerinin listesi görüntülenir.

    ![Müşteri Kasası isteklerinin listesi.](../media/CustomerLockbox6.png)

3. Bir Müşteri Kasası isteği seçin ve ardından **Onayla** veya **Reddet'i** seçin.

    ![Müşteri Kasası isteklerini onaylayın.](../media/CustomerLockbox7.png)

    Müşteri Kasası isteğinin onayıyla ilgili bir onay iletisi görüntülenir.

    ![Müşteri Kasası isteklerini reddedin.](../media/CustomerLockbox8.png)

> [!NOTE]
> Microsoft destek mühendislerinin verilerinize erişimi denetlediği Microsoft Purview Müşteri Kasası isteklerini onaylamak, reddetmek veya iptal etmek için Set-AccessToCustomerDataRequest cmdlet'ini kullanın. Daha fazla bilgi için bkz [. Set-AccessToCustomerDataRequest](/powershell/module/exchange/set-accesstocustomerdatarequest).

## <a name="auditing-customer-lockbox-requests"></a>Müşteri Kasası isteklerini denetleme

Müşteri Kasası isteklerine karşılık gelen denetim kayıtları Microsoft 365 denetim günlüğüne kaydedilir. Microsoft Purview uyumluluk portalındaki [denetim günlüğü arama aracını](search-the-audit-log-in-security-and-compliance.md) kullanarak bu günlüklere erişebilirsiniz. Müşteri Kasası isteğini kabul etme veya reddetme ile ilgili eylemler ve Microsoft mühendisleri tarafından gerçekleştirilen eylemler (erişim istekleri onaylandığında) denetim günlüğüne de kaydedilir. Bu denetim kayıtlarını arayabilir ve gözden geçirebilirsiniz.

### <a name="search-the-audit-log-for-activity-related-to-customer-lockbox-requests"></a>Müşteri Kasası istekleriyle ilgili etkinlik için denetim günlüğünde arama yapma

Müşteri Kasası isteklerini izlemek için denetim günlüğünü kullanabilmeniz için denetim günlüğünü ayarlamak için izlemeniz gereken, denetim günlüğünde arama izinleri atama gibi bazı adımlar vardır. Daha fazla bilgi için bkz. [Microsoft Purview Denetimini Ayarlama (Standart)](set-up-basic-audit.md). Kurulumu tamamladıktan sonra, Müşteri Kasası ile ilgili denetim kayıtlarını döndürmek üzere bir denetim günlüğü arama sorgusu oluşturmak için şu adımları kullanın:

1. <https://compliance.microsoft.com> adresine gidin.
  
2. Denetim günlüğünde arama yapmak için uygun izinlere atanmış bir hesabı kullanarak oturum açın.

3. Uyumluluk merkezinin sol bölmesinde **Denetim'i** seçin.

    **Denetim** sayfasındaki **Arama** sekmesi görüntülenir.

    ![Denetim günlüğü arama sayfası.](../media/auditlogsearch1.png)
  
4. Aşağıdaki arama ölçütlerini yapılandırın:

   1. **Başlangıç tarihi** ve **Bitiş tarihi**. Bu dönemde gerçekleşen olayları görüntülemek için bir tarih ve saat aralığı seçin.  

   2. **Etkinlikler**. Aramanın tüm etkinlikler için denetim kayıtlarını döndürmesi için bu alanı boş bırakın. Bu, Müşteri Kasası istekleriyle ve Microsoft mühendisleri tarafından gerçekleştirilen ilgili etkinlikle ilgili tüm denetim kayıtlarını döndürmek için gereklidir.

   3. **Kullanıcılar**. Bu alanı boş bırakın.

   4. **Dosya, klasör veya site**. Bu alanı boş bırakın.

5. Arama ölçütlerinizi kullanarak aramayı çalıştırmak için **Ara'ya** tıklayın.

    Arama sonuçları birkaç dakika sonra görüntülenir. Arama tamamlanana kadar sayfaya daha fazla arama sonucu eklenir.

6. **Sonuçları Etkinlik** sütunundaki değerlere göre alfabetik olarak sıralamak için **Etkinlik** sütunundaki üst bilgiye tıklayın.

7. Ekranı aşağı kaydırın ve **Set-AccessToCustomerDataRequest** etkinliğiyle denetim kayıtlarını arayın. Bu etkinliğe sahip kayıtlar, kuruluşunuzda Müşteri Kasası isteğini onaylayan veya reddeden bir onaylayanla ilgilidir.

8. Alternatif olarak, **Kullanıcı** sütunundaki değerleri kullanarak sonuçları alfabetik olarak sıralamak için **Kullanıcı** sütunundaki üst bilgiye tıklayın. Onaylanan Müşteri Kasası isteğine yanıt olarak bir Microsoft mühendisi tarafından gerçekleştirilen etkinlikleri gösteren Microsoft **Operatörünün** değerini arayın. **Etkinlik** sütunu, mühendis tarafından gerçekleştirilen eylemi görüntüler.

      ![Denetim kayıtlarını görüntülemek için "Microsoft İşleci"ne filtre uygulama](../media/CustomerLockbox10.png)

9. Sonuç listesinde, görüntülemek için bir denetim kaydına tıklayın.

### <a name="export-the-audit-log-search-results"></a>Denetim günlüğü arama sonuçlarını dışarı aktarma

Ayrıca denetim günlüğü arama sonuçlarını bir CSV dosyasına aktarabilir ve ardından dosyayı Excel'de açarak filtre ve sıralama özelliklerini kullanarak Müşteri Kasası erişim isteğiyle ilgili denetim kayıtlarını bulmayı ve görüntülemeyi kolaylaştırabilirsiniz.

Denetim kayıtlarını dışarı aktarmak için önceki adımları kullanarak denetim günlüğünde arama yapın. Arama tamamlandığında Dışarı Aktar > Arama sonuçları sayfasının üst kısmındaki **Tüm sonuçları indir'i** seçin. Dışarı aktarma işlemi tamamlandığında CSV dosyasını yerel bilgisayarınıza indirebilirsiniz. Daha ayrıntılı yönergeler için bkz. [Denetim günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme](export-view-audit-log-records.md).

Dosyayı indirdikten sonra, Excel'da açabilir ve ardından **İşletimler** sütununa filtreleyerek **Set-AccessToCustomerDataRequest** etkinliklerinin denetim kayıtlarını görüntüleyebilirsiniz. Ayrıca, Microsoft mühendisleri tarafından gerçekleştirilen etkinliklerin denetim kayıtlarını görüntülemek için **UserIds** sütununa ( **Microsoft İşleci** değerini kullanarak) filtreleyebilirsiniz.

> [!NOTE]
> CSV dosyasında denetim kayıtlarını görüntülerken, **AuditData** sütununda ek bilgiler bulunur. Bu sütundaki bilgiler, virgülle ayrılmış *property:value* çiftleri olarak yapılandırılan birden çok özellik içeren bir JSON nesnesinde yer alır. Excel'daki Power Query Düzenleyicisi JSON dönüştürme özelliğini kullanarak **AuditData** sütunundaki JSON nesnesindeki her özelliği birden çok sütuna bölerek her özelliğin kendi sütununa sahip olmasını sağlayabilirsiniz. Bu, bu bilgileri yorumlamayı kolaylaştırır. Ayrıntılı yönergeler için bkz. [Power Query Düzenleyicisi kullanarak dışarı aktarılan denetim günlüğünü biçimlendirme](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).

### <a name="use-powershell-to-search-and-export-audit-records"></a>Denetim kayıtlarını aramak ve dışarı aktarmak için PowerShell kullanma

Microsoft Purview uyumluluk portalında denetim arama aracını kullanmanın bir alternatifi, Exchange Online PowerShell'de [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) cmdlet'ini çalıştırmaktır. PowerShell kullanmanın avantajlarından biri, Microsoft mühendisleri tarafından müşteri kasası isteğiyle ilgili **olarak gerçekleştirilen Set-AccessToCustomerDataRequest** etkinliklerini veya etkinliklerini özel olarak aramanızdır.

[Exchange Online PowerShell'e bağlandıktan](/powershell/exchange/connect-to-exchange-online-powershell) sonra aşağıdaki komutlardan birini çalıştırın. Yer tutucuları belirli bir tarih aralığıyla değiştirin.

Etkinlikleri arama `Set-AccessToCustomerDataRequest`

```powershell
Search-UnifiedAuditLog -StartDate xx/xx/xxxx -EndDate xx/xx/xxxx -Operations Set-AccessToCustomerDataRequest
```

Microsoft mühendisleri tarafından gerçekleştirilen etkinlikleri arama

```powershell
Search-UnifiedAuditLog -StartDate xx/xx/xxxx -EndDate xx/xx/xxxx -UserIds "Microsoft Operator"
```

Daha fazla bilgi ve örnek için bkz. [Denetim günlüğü kayıtlarını aramak ve dışarı aktarmak için PowerShell kullanma](export-view-audit-log-records.md#use-powershell-to-search-and-export-audit-log-records).

Ayrıca, denetim günlüğünde arama yapmak ve sonuçları CSV dosyasına aktarmak için kullanabileceğiniz bir PowerShell betiği de sağladık. Daha fazla bilgi için bkz. [Denetim günlüğünde arama yapmak için PowerShell betiği kullanma](audit-log-search-script.md).

### <a name="audit-record-for-a-customer-lockbox-request"></a>Müşteri Kasası isteği için denetim kaydı

Kuruluşunuzdaki bir kişi Müşteri Kasası isteğini onayladığında veya reddederse, denetim günlüğünde günlüğe kaydedilen denetim kaydı aşağıdaki bilgileri içerir.

| Denetim kaydı özelliği| Açıklama|
|:---------- |:----------|
| Tarih       | Müşteri Kasası isteğinin onaylandığı veya reddedildiği tarih ve saat.
| IP adresi | Onaylayanın isteği onaylamak veya reddetmek için kullandığı makinenin IP adresi. |
| Kullanıcı       | Hizmet hesabı BOXServiceAccount@\[customerforest.prod.outlook.com\].            |
| Etkinlik   | Set-AccessToCustomerDataRequest; Bu, Müşteri Kasası isteğini onayladığınızda veya reddettiyseniz günlüğe kaydedilen denetim etkinliğidir.                                |
| Öğe       | Müşteri Kasası isteğinin Guid'i                             |

Aşağıdaki ekran görüntüsünde, onaylanan müşteri kasası isteğine karşılık gelen bir denetim kaydı örneği gösterilmektedir. Müşteri Kasası isteği reddedildiyse parametresinin `ApprovalDecision` değeri olacaktır `Deny`.

![Onaylanan müşteri kasası isteği için kayıt denetimi.](../media/CustomerLockbox9.png)

### <a name="audit-record-for-an-action-performed-by-a-microsoft-engineer"></a>Microsoft mühendisi tarafından gerçekleştirilen bir eylem için denetim kaydı

Müşteri Kasası isteği onaylandıktan (ve müşteri içeriğine erişmeye neden olabilir) sonra bir Microsoft mühendisi tarafından gerçekleştirilen eylemler denetim günlüğüne kaydedilir. Bu kayıtlar aşağıdaki bilgileri içerir.

| Denetim kaydı özelliği| Açıklama|
|:---------- |:----------|
| Tarih       | Eylemin gerçekleştirildiği tarih saati. Bu eylemin gerçekleştirildiği süre, Müşteri Kasası isteğinin onaylandığı 4 saat içinde gerçekleşir.              |
| IP adresi | Microsoft mühendisinin kullandığı makinenin IP Adresi. |
| Kullanıcı       | Microsoft İşleci; bu değer, kaydın bir Müşteri Kasası isteğiyle ilişkili olduğunu gösterir.                                  |
| Etkinlik   | Microsoft mühendisi tarafından gerçekleştirilen etkinliğin adı.|
| Öğe       | \<empty\>                                             |

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="which-microsoft-365-services-does-customer-lockbox-apply-to"></a>Müşteri Kasası hangi Microsoft 365 hizmetler için geçerlidir?

Müşteri Kasası şu anda Exchange Online, SharePoint Online, OneDrive İş ve Teams desteklenmektedir.

### <a name="is-customer-lockbox-available-to-all-customers"></a>Müşteri Kasası tüm müşterilerin kullanımına açık mı?

Müşteri Kasası Microsoft 365 veya Office 365 E5 aboneliklerine dahil edilir ve Information Protection ve Uyumluluk veya Gelişmiş Uyumluluk eklenti aboneliği ile diğer planlara eklenebilir. Daha fazla bilgi için bkz. [Planlar ve fiyatlandırma](https://products.office.com/business/office-365-enterprise-e5-business-software) .

### <a name="what-is-customer-content"></a>Müşteri içeriği nedir?

Müşteri içeriği, Microsoft 365 hizmet ve uygulama kullanıcıları tarafından oluşturulan verilerdir. Müşteri içeriğine örnek olarak şunlar verilebilir:

- E-posta gövdesi veya e-posta ekleri

- Site içeriğini SharePoint

- SharePoint dosyasının gövdesindeki bilgiler

- Sunu dosyasının gövdesini Skype Kurumsal

- Anlık iletiler (anlık ileti) veya sesli konuşmalar

- Teams sohbetlere ve Teams kanallarına girilen metin( örneğin, 1:1 sohbetler, grup sohbetleri, paylaşılan kanallar, özel kanallar ve toplantı sohbeti)

- Teams sohbet yazışmalarına yapıştırılan kod parçacıkları, resimler, ses ve video iletileri ve bağlantılar gibi diğer veriler

- Teams sohbetlerde ve Teams kanallarında uygulama ve bot verileri

- etkinlik akışını Teams

- Toplantı kayıtlarını ve transkriptlerini Teams

- Sesli

- Teams sohbetlere ve Teams kanallarına gönderilen dosyalar

- Müşteri tarafından oluşturulan blob veya yapılandırılmış depolama verileri (örneğin, SQL Kapsayıcılar)

- Müşteriye ait güvenlik bilgileri (örneğin, sertifikalar, şifreleme anahtarları ve parolalar)

- Müşteri içeriği kalırsa çıkarımlar ve sonraki tüm çıkarımlar

Office 365'daki müşteri içeriği hakkında daha fazla bilgi için [Office 365 Güven Merkezi'ne](https://products.office.com/business/office-365-trust-center-privacy/) bakın.

### <a name="who-is-notified-when-there-is-a-request-to-access-my-content"></a>İçeriğime erişim isteği olduğunda Who bildirilir?

Genel yöneticilere ve Müşteri Kasası erişimi onaylayan yönetici rolüne atanan herkese bildirilir. Bunlar aynı zamanda Müşteri Kasası isteklerini onaylayan kullanıcılardır.

### <a name="who-can-approve-or-reject-these-requests-in-my-organization"></a>Kuruluşumda bu istekleri Who onaylayabilir veya reddedebilir?

Genel yöneticiler ve Müşteri Kasası erişim onaylayıcısı yönetici rolüne atanan herkes Müşteri Kasası isteklerini onaylayabilir. Müşteriler, kuruluşlarında bu rol atamalarını denetler.

### <a name="how-do-i-opt-in-to-customer-lockbox"></a>Müşteri Kasası'na kabul Nasıl yaparım??

Genel yönetici Microsoft 365 yönetim merkezi Müşteri Kasası'nı etkinleştirebilir ve yapılandırabilir.

### <a name="if-i-approve-a-customer-lockbox-request-what-can-the-engineer-do-and-how-will-i-know-what-the-microsoft-engineer-did"></a>Müşteri Kasası isteğini onaylarsam mühendis ne yapabilir ve Microsoft mühendisinin ne yaptığını nasıl bilebilirim?

Müşteri Kasası isteğini onayladıktan sonra, Microsoft mühendisi önceden onaylanan cmdlet'leri kullanarak müşteri içeriğine erişmek için bu gerekli ayrıcalıkları verdi. Müşteri Kasası isteklerine yanıt olarak Microsoft mühendisleri tarafından gerçekleştirilen eylemler, Güvenlik & Uyumluluk Merkezi'ndeki denetim günlüğünde günlüğe kaydedilir ve erişilebilir.

### <a name="how-do-i-know-that-microsoft-follows-the-approval-process"></a>Microsoft'un onay sürecini izlediğini Nasıl yaparım? biliyor musunuz?

Kuruluşunuzdaki yöneticilere ve onaylayanlara gönderilen e-posta onay bildirimlerine [Microsoft 365 yönetim merkezi](https://go.microsoft.com/fwlink/p/?linkid=2024339) Müşteri Kasası istek geçmişiyle çapraz başvuruda bulunabilirsiniz.

Müşteri Kasası en son [SOC 1 SSAE 16 denetim raporuna](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=91592749-e86a-43ac-801e-121382614681&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_SOC%20%2F%20SSAE%2016%20Reports) dahildir. Daha fazla ayrıntı için en son raporları [Microsoft Hizmet Güveni Portalı'nda](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=91592749-e86a-43ac-801e-121382614681&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_SOC%20%2F%20SSAE%2016%20Reports) bulabilirsiniz.

### <a name="can-microsoft-modify-the-list-of-approvers-for-my-tenant-if-not-how-is-it-prevented"></a>Microsoft kiracımın onaylayanları listesini değiştirebilir mi? Aksi takdirde, nasıl engellenir?

Müşteri Kasası isteklerini kimin onaylayabileceğinizi yalnızca kuruluşunuzdaki bir genel yönetici belirtebilir. Bu, yalnızca Azure Active Directory'daki Genel yönetici grubunun üyelerinin isteği kimin onaylayabileceğinizi belirtebileceği anlamına gelir. Azure Active Directory'da Genel yönetici grubunun üyeliği yalnızca kuruluşunuz tarafından yönetilir.

### <a name="what-if-i-need-more-information-about-a-content-access-request-to-approve-it"></a>Onaylamak için bir içerik erişim isteği hakkında daha fazla bilgiye ihtiyacım olursa ne olur?

Her Müşteri Kasası isteği bir Microsoft 365 hizmet isteği numarası içerir. İstek hakkında daha fazla bilgi edinmek için Microsoft Desteği iletişim kurabilir ve bu hizmet numarasına başvurabilirsiniz.

### <a name="when-a-customer-lockbox-request-is-approved-how-long-are-the-permissions-valid"></a>Müşteri Kasası isteği onaylandığında izinler ne kadar süreyle geçerli olur?

Şu anda Microsoft mühendisine verilen erişim izinleri için maksimum süre 4 saattir. Microsoft mühendisi ayrıca daha kısa bir süre isteyebilir.

### <a name="how-can-i-get-a-history-of-all-customer-lockbox-requests"></a>Tüm Müşteri Kasası isteklerinin geçmişini nasıl alabilirim?

Tüm Müşteri Kasası istekleri [Microsoft 365 yönetim merkezi](https://go.microsoft.com/fwlink/p/?linkid=2024339) görüntülenir.

### <a name="how-do-i-correlate-the-content-access-requests-with-the-related-audit-logs"></a>İçerik erişim istekleriyle ilgili denetim günlükleriyle bağıntılı Nasıl yaparım??

Uyumluluk Merkezi Etkinlik Akışı, Müşteri Kasası'nın günlük etkinliklerini içerir. Müşteriler etkinlik akışındaki Müşteri Kasası günlük etkinliklerine aldıkları e-posta isteğine karşı çapraz başvuruda bulunabilir.

### <a name="what-happens-when-a-customer-doesnt-respond-to-a-customer-lockbox-request"></a>Müşteri Müşteri Kasası isteğine yanıt vermediğinde ne olur?

Müşteri Kasası isteklerinin varsayılan süresi 12 saattir. Bir isteğe 12 saat içinde yanıt vermezseniz isteğin süresi dolar.

### <a name="what-does-microsoft-do-when-a-customer-rejects-a-customer-lockbox-request"></a>Müşteri Müşteri Kasası isteğini reddettiği zaman Microsoft ne yapar?

Müşteri Müşteri Kasası isteğini reddederse, müşteri içeriğine erişim gerçekleşmez. Kuruluşunuzdaki bir kullanıcı sorunu çözmek için Microsoft'un müşteri içeriğine erişmesini gerektiren bir hizmet sorunuyla karşılaşmaya devam ederse, hizmet sorunu devam edebilir ve Microsoft bu konuda kullanıcıyı bilgilendirecektir.

### <a name="how-do-i-set-up-alerts-whenever-a-request-has-been-approved"></a>bir istek onaylandığı her durumda uyarılar Nasıl yaparım??

Yöneticileri uyarmak için yerleşik bir seçenek yoktur. Ancak, yöneticiler [Microsoft Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security#to-create-policies) kullanarak uyarılar ayarlayabilir.

### <a name="does-customer-lockbox-protect-against-data-requests-from-law-enforcement-agencies-or-other-third-parties"></a>Müşteri Kasası, kolluk kuvvetlerinden veya diğer üçüncü taraflardan gelen veri isteklerine karşı koruma sağlar mı?

Hayır. Microsoft, müşteri verilerine yönelik üçüncü taraf isteklerini ciddiye alır. Microsoft, bulut hizmeti sağlayıcısı olarak her zaman müşteri verilerinin gizliliğini savunur. Bir celp aldığımızda, Microsoft bilgileri almak için her zaman üçüncü tarafı müşteriye yönlendirmeyi dener. (Brad Smith'in blogu okuyun: [Müşteri verilerini kamu gözetiminden koruma](https://blogs.microsoft.com/blog/2013/12/04/protecting-customer-data-from-government-snooping/)). Microsoft'un aldığı kolluk kuvvetleri istekleriyle ilgili [ayrıntılı bilgileri](https://www.microsoft.com/corporate-responsibility/lerr) düzenli aralıklarla yayımlarız.

Daha fazla bilgi için üçüncü taraf veri istekleriyle ilgili [Microsoft Güven Merkezi'ne](https://www.microsoft.com/trustcenter/default.aspx) ve [Çevrimiçi Hizmet Koşulları'ndaki](https://www.microsoft.com/Licensing/product-licensing/products.aspx) "Müşteri Verilerinin Açığa Çıkması" bölümüne bakın.

### <a name="how-does-microsoft-ensure-that-a-member-of-its-staff-doesnt-have-standing-access-to-customer-content-in-office-365-applications"></a>Microsoft, personelinin bir üyesinin Office 365 uygulamalarında müşteri içeriğine erişimi olmamasını nasıl sağlar?

Microsoft, erişim denetim sistemleri aracılığıyla kapsamlı önleyici önlemler ve bu erişim denetim sistemlerini aşma girişimlerini belirlemek ve ele almak için dedektif önlemleri uygular. Microsoft 365 en az ayrıcalık ve tam zamanında erişim ilkeleriyle çalışır. Bu nedenle, hiçbir Microsoft personelinin müşteri içeriğine sürekli olarak erişme izni yoktur. İzin verilirse, sınırlı bir süre için geçerlidir.

Microsoft 365, hizmet içinde işletimsel ve yönetim işlevlerini gerçekleştirme olanağı veren izin isteklerini işlemek için *Lockbox* adlı bir erişim denetim sistemi kullanır. Operatörün, erişim verilmeden önce istek üzerinde işlem yapması (örneğin, onaylayın) için ikinci bir kişinin gerektirdiği Kilit Kutusu'nu kullanarak müşteri içeriğine erişim istemesi gerekir. İkinci kişi istek sahibi olamaz ve müşteri içeriğine erişimi onaylayacak şekilde belirlenmelidir. Yalnızca istek onaylanırsa operatör müşteri içeriğine geçici erişim elde eder. Yükseltme süresi dolduktan sonra, Kilit Kutusu erişimi iptal eder.

Microsoft genel güvenlik uygulamaları hakkında daha fazla bilgi için [Çevrimiçi Hizmet Koşulları'na](https://www.microsoft.com/licensing/product-licensing/products) bakın.

### <a name="under-what-circumstances-do-microsoft-engineers-need-access-to-my-content"></a>Microsoft mühendislerinin içeriğime hangi koşullarda erişmesi gerekiyor?

Microsoft mühendislerinin müşteri içeriğine erişmesi gereken en yaygın senaryo, müşterinin sorun giderme için erişim gerektiren bir destek isteğinde bulunduğu durumdur. Microsoft 365 temel ilkelerinden biri, hizmetin Microsoft'un müşteri içeriğine erişimi olmadan çalışmasıdır. Microsoft tarafından gerçekleştirilen neredeyse tüm hizmet işlemleri tamamen otomatiktir ve insan katılımı yüksek oranda denetlenip müşteri içeriğinden soyutlanır. Microsoft 365 amacı, müşteri belirli bir Microsoft erişimi isteğini onaylayana kadar hizmeti desteklemek için müşteri içeriğine erişim gerekli değildir.

### <a name="i-already-thought-my-data-was-secure-with-the-microsoft-cloud-so-why-do-i-need-customer-lockbox"></a>Verilerimin Microsoft bulutuyla güvenli olduğunu sanıyordum, neden Müşteri Kasasına ihtiyacım var?

Müşteri Kasası, müşterilere hizmet işlemleri için açık erişim yetkisi verme olanağı sunarak ek bir denetim katmanı sağlar. Müşteri Kasası, açık veri erişimi yetkilendirmesi için yordamların uygulandığını göstererek müşterilerin HIPAA ve FEDRAMP gibi belirli uyumluluk yükümlülüklerini karşılamalarına da yardımcı olur.
