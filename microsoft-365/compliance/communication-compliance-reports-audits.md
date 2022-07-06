---
title: İletişim uyumluluk raporlarını ve denetimlerini kullanma
description: İletişim uyumluluk raporlarını ve denetimlerini kullanma hakkında daha fazla bilgi edinin.
keywords: Microsoft 365, Microsoft Purview, uyumluluk, iletişim uyumluluğu
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 27c166f3c9df0dead57f977b00cab41eb82347ad
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630503"
---
# <a name="use-communication-compliance-reports-and-audits"></a>İletişim uyumluluk raporlarını ve denetimlerini kullanma

## <a name="reports"></a>Raporlar

Yeni **Raporlar** panosu, tüm iletişim uyumluluk raporlarını görüntülemek için merkezi konumdur. Rapor pencere öğeleri, iletişim uyumluluk etkinliklerinin durumunun genel değerlendirmesi için en yaygın olarak gereken içgörülerin hızlı bir görünümünü sağlar. Rapor pencere öğelerinde yer alan bilgiler dışarı aktarılamaz. Ayrıntılı raporlar, belirli iletişim uyumluluk alanlarıyla ilgili ayrıntılı bilgiler sağlar ve gözden geçirirken bilgileri filtreleme, gruplandırma, sıralama ve dışarı aktarma olanağı sunar. 

Tarih aralığı filtresi için, olayların tarih ve saati Eşgüdümlü Evrensel Saat (UTC) içinde listelenir. Raporlar için iletileri filtrelerken, istekte bulunan kullanıcının yerel tarih/saatinin UTC'ye dönüştürülmesi temelinde sonuçları belirler. Örneğin, ABD Pasifik Yaz Saati (PDT) içindeki bir kullanıcı 30.08.2021 ile 31.08.2021 saat 00:00 arasında bir raporu filtrelerse, rapor 30.08.2021 07:00 UTC ile 31.08.2021 07:00 UTC arası iletileri içerir. Saat 00:00'da filtreleme yaparken aynı kullanıcı ABD Doğu Yaz Saati'nde (EDT) bulunuyorsa, rapor 30.08.2021 04:00 UTC ile 31.08.2021 04:00 UTC arası iletileri içerir.

![İletişim uyumluluk raporları panosu.](../media/communication-compliance-reports-dashboard.png)

**Raporlar panosu** aşağıdaki rapor pencere öğelerini ve ayrıntılı rapor bağlantılarını içerir:

### <a name="report-widgets"></a>Rapor pencere öğeleri

- **Son ilke eşleşmeleri: Etkin ilkenin** zaman içindeki eşleşme sayısını görüntüler.
- **İlkeye göre çözümlenen öğeler**: zaman içinde ilke tarafından çözümlenen ilke eşleştirme uyarılarının sayısını görüntüler.
- **İlke eşleşmesi en fazla olan kullanıcılar**: Belirli bir dönem için kullanıcıları (veya anonimleştirilmiş kullanıcı adlarını) ve ilke eşleşmelerinin sayısını görüntüler.
- **En çok eşleşme içeren ilke**: Belirli bir dönem için ilkeleri ve eşleşme sayısını görüntüler; eşleşmeler için en yüksek ile en düşük arasında sıralanır.
- **İlkeye göre yükseltmeler**: Belirli bir zaman içindeki ilke başına yükseltme sayısını görüntüler.

### <a name="detailed-reports"></a>Ayrıntılı raporlar

Tüm ayrıntılı raporların rapor ayrıntılarını içeren bir .csv dosyası oluşturmak için *Dışarı Aktar* seçeneğini kullanın. Raporu *dışarı aktar* seçeneği 3 MB'a kadar dosya boyutu indirmelerini destekler.

- **İlke ayarları ve durumu: İlke** yapılandırmasına ve ayarlarına ve iletilerdeki ilkenin (eşleşmeler ve eylemler) her biri için genel duruma ayrıntılı bir bakış sağlar. İlke bilgilerini ve ilkelerin kullanıcılar ve gruplarla nasıl ilişkilendirildiğini, konumları, gözden geçirme yüzdelerini, gözden geçirenleri, durumu ve ilkenin en son ne zaman değiştirildiğini içerir. Rapor ayrıntılarını içeren bir .csv dosyası oluşturmak için *Dışarı Aktar* seçeneğini kullanın.
- **İlke başına öğeler ve eylemler: İlke başına** eşleşen öğeleri ve düzeltme eylemlerini gözden geçirin ve dışarı aktarın. İlke bilgilerini ve ilkelerin nasıl ilişkili olduğunu içerir:

    - Eşleştirilen öğeler
    - Yükseltilen öğeler
    - Çözümlenen öğeler
    - Uyumlu olarak etiketlendi
    - Uyumlu değil olarak etiketlendi
    - Sorgulanabilir olarak etiketlendi
    - Gözden geçirmeyi bekleyen öğeler
    - Kullanıcı bildirimde bulunu
    - Büyük/küçük harf oluşturuldu

- **Konum başına öğe ve eylemler**: Microsoft 365 konumuna göre eşleşen öğeleri ve düzeltme eylemlerini gözden geçirin ve dışarı aktarın. İş yükü platformlarının nasıl ilişkili olduğu hakkında bilgi içerir:

    - Eşleştirilen öğeler
    - Yükseltilen öğeler
    - Çözümlenen öğeler
    - Uyumlu olarak etiketlendi
    - Uyumlu değil olarak etiketlendi
    - Sorgulanabilir olarak etiketlendi
    - Gözden geçirmeyi bekleyen öğeler
    - Kullanıcı bildirimde bulunu
    - Büyük/küçük harf oluşturuldu

- **Kullanıcıya göre etkinlik: Kullanıcı** başına eşleşen öğeleri ve düzeltme eylemlerini gözden geçirin ve dışarı aktarın. Kullanıcıların nasıl ilişkili olduğu hakkında bilgi içerir:

    - Eşleştirilen öğeler
    - Yükseltilen öğeler
    - Çözümlenen öğeler
    - Uyumlu olarak etiketlendi
    - Uyumlu değil olarak etiketlendi
    - Sorgulanabilir olarak etiketlendi
    - Gözden geçirmeyi bekleyen öğeler
    - Kullanıcı bildirimde bulunu
    - Büyük/küçük harf oluşturuldu

- **Konum başına hassas bilgi türü** (önizleme): Hassas bilgi türlerinin ve iletişim uyumluluk ilkelerindeki ilişkili kaynakların algılanması hakkındaki bilgileri gözden geçirin ve dışarı aktarın. Kuruluşunuzda yapılandırılan kaynaklarda hassas bilgi türü örneklerinin toplamını ve belirli dökümünü içerir. Her üçüncü taraf kaynağın değerleri .csv dosyasındaki ayrı sütunlarda görüntülenir. Örnekler şunlardır:

    - **E-posta**: Exchange e-posta iletilerinde hassas bilgi türleri algılandı.
    - **Teams**: Microsoft Teams kanallarında ve sohbet iletilerinde hassas bilgi türleri algılandı.
    - **Yammer**: Yammer gelen kutularında, gönderilerinde, sohbetlerde ve yanıtlarda hassas bilgi türleri algılandı.
    - **Üçüncü taraf kaynaklar**: Kuruluşunuzda yapılandırılan üçüncü taraf bağlayıcılarla ilişkili etkinlikler için hassas bilgi türleri algılandı. Rapordaki belirli bir hassas bilgi türünün üçüncü taraf kaynaklarının dökümünü görüntülemek için farenizi Üçüncü taraf kaynak sütunundaki hassas bilgi türünün değerinin üzerine getirin.
    - **Diğer**: İç sistem işleme için kullanılan hassas bilgi türleri. Rapor için bu kaynağın seçilmesi veya seçiminin kaldırılması hiçbir değeri etkilemez.

### <a name="message-details-report"></a>İleti ayrıntıları raporu

Özel raporlar oluşturun ve **İlkeler** sekmesindeki belirli ilkelerde yer alan iletilerin ayrıntılarını gözden geçirin. Bu raporlar, iletilerin tüm gözden geçirmeleri ve özelleştirilebilir bir zaman aralığı için iletilerin durumu için bir rapor anlık görüntüsü oluşturmak için kullanılabilir. Rapor oluşturduktan sonra, **ayrıntılar raporunu İleti ayrıntıları raporları** sekmesinde .csv dosyası olarak görüntüleyebilir ve indirebilirsiniz.

![İletişim uyumluluk iletisi ayrıntı raporu.](../media/communication-compliance-message-detail-report.png)

Yeni bir ileti ayrıntıları raporu oluşturmak için aşağıdaki adımları tamamlayın:

1. *İletişim Uyumluluğu Araştırmacıları* rol grubunun üyesi olan bir hesapla Microsoft Purview uyumluluk portalı oturum açın.
2. **İlkeler** sekmesine gidin, bir ilke seçin ve ardından **İleti ayrıntıları raporu oluştur'u** seçin.
3. **İleti ayrıntıları raporu oluştur** bölmesinde Rapor adı alanına rapor için bir **ad** girin.
4. **Tarih aralığı seçin bölümünde**, rapor için bir *Başlangıç tarihi* ve *Bitiş tarihi* seçin.
5. **Oluştur**’u seçin.
6. Rapor oluşturma onayı görüntülenir.

Rapordaki öğe sayısına bağlı olarak, raporun indirilmeye hazır olması birkaç dakika ile saat arasında sürebilir. İlerleme durumunu İleti ayrıntıları raporları sekmesinden de kontrol edebilirsiniz. Rapor durumu *Sürüyor* veya *İndirmeye hazır*. Aynı anda en fazla 15 ayrı raporun işlenmesini sağlayabilirsiniz. Bir raporu indirmek için *İndirmeye hazır* durumunda bir rapor seçin ve **ardından Raporu indir'i** seçin.

> [!NOTE]
> Seçtiğiniz zaman aralığı raporda herhangi bir ileti sonucu döndürmüyorsa, seçilen zaman aralığı için ileti yoktu. Rapor boş olacaktır.

İleti ayrıntıları raporları, ilkedeki her ileti öğesi için aşağıdaki bilgileri içerir:

- **Eşleşme Kimliği**: İlkedeki iletinin benzersiz kimliği.
- **Gönderen**: İletinin göndereni.
- **Alıcılar**: İletiye dahil edilen alıcılar.
- **Gönderilme Tarihi**: İletinin gönderildiği tarih.
- **Eşleşme Tarihi**: İletinin ilke koşullarıyla eşleşme tarihi.
- **Konu**: İletinin konusu.
- **Ekler içerir**: iletinin eklerinin durumu. Değerler Evet veya Hayır'dır.
- **İlke Adı**: İletiyle ilişkili ilkenin adı. Bu değer rapordaki tüm iletiler için aynı olacaktır.
- **Öğe Durumu**: İlkedeki ileti öğesinin durumu. Değerler Beklemede veya Çözümlendi.
- **Etiketler**: İletiye atanan etiketler. Değerler Sorgulanabilir, Uyumlu veya Uyumsuz'dır.
- **Anahtar Sözcük Eşleşmeleri**: İleti için anahtar sözcük eşleşmeleri.
- **Gözden Geçirenler**: İletiye atanan gözden geçirenler.
- **Bekleme süresi (gün):** İletinin beklemede olduğu gün sayısı. Çözümlenen iletiler için değer 0'dır.
- **Çözümlenen açıklama: çözümlendiğinde** girilen iletinin açıklamaları.
- **Çözümlenme Tarihi**: İletinin çözümlenme tarihi ve saati.
- **Son Güncelleştirme Ölçütü**: Son güncelleştiricinin kullanıcı adı.
- **Son Güncelleştirme Tarihi**: İletinin son güncelleştirildiği tarih ve saat.
- **Açıklamaların geçmişi**: açıklama yazarı ve açıklamanın tarih/saati de dahil olmak üzere ileti uyarısı için tüm açıklamaların listesi.

## <a name="audit"></a>Denetim

Bazı durumlarda, kullanıcı etkinliklerinin ve iletişimlerinin denetimini kanıtlamak için mevzuat veya uyumluluk denetçilerine bilgi sağlamanız gerekir. Bu bilgiler, tanımlı bir kuruluş ilkesiyle ilişkili tüm etkinliklerin özeti veya iletişim uyumluluk ilkesi her değiştiğinde olabilir. İletişim uyumluluk ilkeleri, iç veya dış denetimler için tam hazırlık için yerleşik denetim izlerine sahiptir. Her oluşturma, düzenleme ve silme eyleminin ayrıntılı denetim geçmişleri, denetim yordamlarının kanıtını sağlamak için iletişim ilkeleriniz tarafından yakalanır.

> [!IMPORTANT]
> İletişim uyumluluk olayları kaydedilmeden önce kuruluşunuz için denetimin etkinleştirilmesi gerekir. Denetimi etkinleştirmek için bkz [. Denetim günlüğünü etkinleştirme](communication-compliance-configure.md#step-2-required-enable-the-audit-log). Etkinlikler Microsoft 365 Denetim günlüğünde yakalanan olayları tetiklediğinde, bu olayların iletişim uyumluluk ilkelerinde görüntülenebilmesi 48 saat kadar sürebilir.

İletişim uyumluluk ilkesi güncelleştirme etkinliklerini görüntülemek için, herhangi bir **ilkenin ana sayfasında İlke güncelleştirmelerini dışarı aktar** denetimini seçin. Güncelleştirme etkinliklerini dışarı aktarmak için *Genel Yönetici* veya *İletişim Uyumluluğu Yönetici* rolleri atanmış olmalıdır. Bu eylem, aşağıdaki bilgileri içeren .csv biçiminde bir denetim dosyası oluşturur:

|**Alan**|**Ayrıntılar**|
|:-----|:-----|
| **Creationdate** | Güncelleştirme etkinliğinin bir ilkede gerçekleştirildiği tarih. |
| **Kullanıcı Kimlikleri** | bir ilkede güncelleştirme etkinliğini gerçekleştiren kullanıcı. |
| **Operasyonlar** | İlke üzerinde gerçekleştirilen güncelleştirme işlemleri. |
| **AuditData** | Bu alan, tüm ilke güncelleştirme etkinlikleri için ana veri kaynağıdır. Tüm güncelleştirme etkinlikleri kaydedilir ve virgülle ayrılmıştır. |

bir ilkenin iletişim uyumluluğu gözden geçirme etkinliklerini görüntülemek için, belirli bir ilkenin **Genel Bakış** sayfasında **Gözden geçirme etkinliklerini dışarı aktar** denetimini seçin. Gözden geçirme etkinliklerini dışarı aktarmak için *Genel Yönetici* veya *İletişim Uyumluluğu Yönetici* rolleri atanmış olmalıdır. Bu eylem, aşağıdaki bilgileri içeren .csv biçiminde bir denetim dosyası oluşturur:

|**Alan**|**Ayrıntılar**|
|:-----|:-----|
| **Creationdate** | gözden geçirme etkinliğinin bir ilkede gerçekleştirildiği tarih. |
| **Kullanıcı Kimlikleri** | bir ilkede gözden geçirme etkinliğini gerçekleştiren kullanıcı. |
| **Operasyonlar** | İlke üzerinde gerçekleştirilen gözden geçirme işlemleri. |
| **AuditData** | Bu alan, tüm ilke gözden geçirme etkinlikleri için ana veri kaynağıdır. Tüm gözden geçirme etkinlikleri kaydedilir ve virgülle ayrılmıştır. |

Denetim etkinliklerini birleşik denetim günlüğünde veya [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) PowerShell cmdlet'iyle de görüntüleyebilirsiniz. Denetim günlüğü saklama ilkeleri hakkında daha fazla bilgi edinmek için bkz. [Denetim günlüğü saklama ilkelerini yönetme](audit-log-retention-policies.md).

Örneğin, aşağıdaki örnek tüm denetim gözden geçirme etkinlikleri (ilkeler ve kurallar) için etkinlikleri döndürür:

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType AeD -Operations SupervisoryReviewTag
```

Bu örnek, iletişim uyumluluk ilkeleriniz için güncelleştirme etkinliklerini döndürür:

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType Discovery -Operations SupervisionPolicyCreated,SupervisionPolicyUpdated,SupervisionPolicyDeleted
```

Bu örnek, geçerli iletişim uyumluluk ilkelerinizle eşleşen etkinlikleri döndürür:

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -Operations SupervisionRuleMatch
```

İletişim uyumluluk ilkesi eşleşmeleri, her ilke için bir denetim posta kutusunda depolanır. Bazı durumlarda, geçerli 100 GB depolama boyutuna veya 1 milyon ileti sınırına yaklaşmadığınızdan emin olmak için bir ilke için denetim posta kutunuzun boyutunu denetlemeniz gerekebilir. Posta kutusu sınırına ulaşılırsa, ilke eşleşmeleri yakalanmaz ve aynı etkinlikler için eşleşmeleri yakalamaya devam etmek için yeni bir ilke (aynı ayarlarla) oluşturmanız gerekir.

bir ilkenin denetim posta kutusunun boyutunu denetlemek için aşağıdaki adımları tamamlayın:

1. Modern kimlik doğrulaması kullanarak Exchange Online PowerShell'e bağlanmak için Exchange Online PowerShell V2 modülündeki [Connect-ExchangeOnline](/powershell/module/exchange/connect-exchangeonline) cmdlet'ini kullanın.
2. PowerShell'de aşağıdaki komutu çalıştırın:

    ```PowerShell
    ForEach ($p in Get-SupervisoryReviewPolicyV2 | Sort-Object Name)
    {
       "<Name of your communication compliance policy>: " + $p.Name
       Get-MailboxStatistics $p.ReviewMailbox | ft ItemCount,TotalItemSize
    }
    ```
