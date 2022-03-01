---
title: İletişim uyumluluk raporlarını ve denetimlerini kullanma
description: İletişim uyumluluk raporlarını ve denetimlerini kullanma hakkında daha fazla bilgi edinin.
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
ms.openlocfilehash: a65a72538afa3684cf4ad9351d30313e0dc43b8d
ms.sourcegitcommit: 726a72f135358603c2fde3f4067d834536e6deb2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2022
ms.locfileid: "63014321"
---
# <a name="use-communication-compliance-reports-and-audits"></a>İletişim uyumluluk raporlarını ve denetimlerini kullanma

## <a name="reports"></a>Raporlar

Yeni Raporlar **panosu** , tüm iletişim uyumluluk raporlarını görüntülemek için merkezi bir konum sağlar. Rapor pencere öğeleri, iletişim uyumluluğu etkinliklerinin durumunun genel olarak değerlendirilmesi için en yaygın olarak gereken içgörülerin hızlı bir görünümünü sağlar. Rapor widget'larında yer alan bilgiler dışarı aktarılamaz. Ayrıntılı raporlar, belirli iletişim uyumluluk alanlarıyla ilgili ayrıntılı bilgiler sağlar ve gözden geçirirken bilgileri filtreleme, gruplama, sıralama ve dışarı aktarma olanağı sağlar. 

Tarih aralığı filtresi için, olayların tarih ve saati Eşgüdümli Evrensel Saat (UTC) alanında listelenir. Raporlar için iletileri filtrelerken, istenen kullanıcının yerel tarihi/saati, kullanıcının yerel tarih/saati UTC'ye dönüştürme işlemini temel alarak sonuçları belirler. Örneğin, ABD'de Pasifik Gün Işığı Saati (PDT) kullanıcısı bir raporu 30/8/2021 ile 31/8/2021 arasındaki saat 00:00'da filtrelerse, rapor 30/8/2021 07:00 UTC ile 31/8/2021 07:00 UTC arasındaki iletileri içerir. Aynı kullanıcı Saat 00:00'da filtreleme için ABD Doğu Avrupa Saati'nde (EDT) yer aldı ise, rapor 30/8/2021 04:00 UTC ile 31/8/2021 04:00 UTC arasındaki iletileri içerir.

![İletişim uyumluluk raporları panosu.](../media/communication-compliance-reports-dashboard.png)

Raporlar **panosu aşağıdaki** rapor pencere öğelerini ve ayrıntılı rapor bağlantılarını içerir:

### <a name="report-widgets"></a>Rapor pencere öğeleri

- **Son ilke eşleşmeleri**: Etkin ilkeye göre zaman içinde eşleşme sayısını görüntüler.
- **İlkeye göre çözümlenen** öğeler: zaman içinde ilke tarafından çözümlenen ilke eşleşme uyarılarının sayısını görüntüler.
- **çoğu ilke eşleşmesi olan** kullanıcılar: belirli bir süre için kullanıcıları (veya anonimleştirilmiş kullanıcı adlarını) ve ilke eşleşme sayısını görüntüler.
- **Çoğu eşleşmeyi gösteren ilke**: belirli bir süre için ilkeleri ve eşleşme sayısını görüntüler; eşleşmeler için en yüksek düzeyde en altta sıralandı.
- **İlkeye göre yükseltmeler**: belirli bir süre içinde ilke başına yükseltme sayısını görüntüler.

### <a name="detailed-reports"></a>Ayrıntılı raporlar

Ayrıntılı herhangi *bir* raporun rapor .csv bir dosya oluşturmak için Dışarı Aktar seçeneğini kullanın.

- **İlke ayarları ve** durumu: hem ilke yapılandırmasına ve ayarlarına, hem de iletilerde ilkenin (eşleşmeler ve eylemler) her biri için genel durum bilgilerine ayrıntılı bir bakış sağlar. İlke bilgilerini ve ilkelerin kullanıcılar ve gruplarla, konumlarla, gözden geçirme yüzdelerini, gözden geçirenlerle, durumla ve ilkenin son değiştirilme tarihiyle ilişkili olduğunu içerir. Dışarı Aktar *seçeneğini* kullanarak rapor .csv bir dosya oluşturun.
- **İlke başına öğeler ve eylemler**: İlke başına eşleşen öğeleri ve düzeltme eylemlerini gözden geçirme ve dışarı aktarma. İlke bilgilerini ve ilkelerin ilişkili olduğu bilgileri içerir:

    - Eşan öğeler
    - İlerleen öğeler
    - Çözülen öğeler
    - Uyumlu olarak etiketlendi
    - Uyumlu değil olarak etiketlendi
    - Şüpheli olarak etiketlendi
    - Bekleyen gözden geçirme öğeleri
    - Kullanıcı bilgili
    - Büyük/harf oluşturuldu

- **Konum başına öğe ve eylemler**: Her bir konumda eşleşen öğeleri gözden geçir ve dışarı Microsoft 365. İş yükü platformlarının nasıl ilişkilendiril olduğu hakkında bilgi içerir:

    - Eşan öğeler
    - İlerleen öğeler
    - Çözülen öğeler
    - Uyumlu olarak etiketlendi
    - Uyumlu değil olarak etiketlendi
    - Şüpheli olarak etiketlendi
    - Bekleyen gözden geçirme öğeleri
    - Kullanıcı bilgili
    - Büyük/harf oluşturuldu

- **Kullanıcıya göre etkinlik**: Kullanıcı başına eşleşen öğeleri ve düzeltme eylemlerini gözden geçirme ve dışarı aktarma. Kullanıcıların nasıl ilişkilendiril olduğuyla ilgili bilgi içerir:

    - Eşan öğeler
    - İlerleen öğeler
    - Çözülen öğeler
    - Uyumlu olarak etiketlendi
    - Uyumlu değil olarak etiketlendi
    - Şüpheli olarak etiketlendi
    - Bekleyen gözden geçirme öğeleri
    - Kullanıcı bilgili
    - Büyük/harf oluşturuldu

- **Konum başına hassas bilgi türü** (önizleme): Hassas bilgi türlerinin ve iletişim uyumluluk ilkelerinde ilişkili kaynakların algılanmasıyla ilgili bilgileri gözden geçirin ve dışarı aktarın. Bir bütün olarak toplamı ve hassas bilgi türü örneklerinin, kurum içinde yapılandırılan kaynaklara özel çözümlemesini içerir. Her bir üçüncü taraf kaynağının değerleri bu dosyada ayrı .csv görüntülenir. Örnekler:

    - **E-posta**: E-posta iletilerinde Exchange hassas bilgi türleri.
    - **Teams**: Kanallarda ve sohbet iletilerinde Microsoft Teams hassas bilgi türleri.
    - **Skype Kurumsal**: İş iletişimleri için Skype türlerinde algılanan hassas bilgi türleri.
    - **Yammer**: Gelen kutularında, gönderilerde, sohbetlerde Yammer yanıtlarında algılanan hassas bilgi türleri.
    - **Üçüncü taraf kaynakları**: Kuruluşta yapılandırılmış üçüncü taraf bağlayıcılarla ilişkilendirilmiş etkinlikler için algılanan hassas bilgi türleri. Rapordaki belirli bir hassas bilgi türünün üçüncü taraf kaynaklarının dökümünü görüntülemek için, farenizi Üçüncü taraf kaynak sütunundaki hassas bilgi türünün değerinin üzerine gelin.
    - **Diğer**: İç sistem işlemesi için kullanılan hassas bilgi türleri. Rapor için bu kaynağın seçimini kaldırmak veya bu kaynağın seçimini kaldırmak hiçbir değeri etkilemez.

### <a name="message-details-report-preview"></a>İleti ayrıntıları raporu (önizleme)

Özel raporlar oluşturun ve İlkeler sekmesinde belirli ilkelerde yer alan iletiler için **ayrıntıları gözden** geçirin. Bu raporlar, tüm ileti incelemeleri için ve özelleştirilebilir bir süre için iletilerin durumu için rapor anlık görüntüsü oluşturmak için kullanılabilir. Rapor oluşturduk sonra, İleti ayrıntıları raporları sekmesinde ayrıntılar raporunu .csv bir dosya **olarak indirebilirsiniz** .

![İletişim uyumluluğu iletisi ayrıntı raporu.](../media/communication-compliance-message-detail-report.png)

Yeni ileti ayrıntıları raporu oluşturmak için aşağıdaki adımları tamamlayın:

1. uyumluluk Microsoft 365 uyumluluk merkezi Uyumlulukları rol grubunun üyesi *olan bir hesabınızla oturum* açın.
2. İlkeler **sekmesine** gidin, bir ilke seçin ve sonra da İleti ayrıntıları **raporu oluştur'a tıklayın**.
3. İleti **ayrıntıları oluştur raporu bölmesinde** , Rapor adı alanına rapor için **bir ad** girin.
4. Tarih **aralığı seçin'de**, rapor *için bir Başlangıç tarihi* *ve Bitiş* tarihi seçin.
5. **Oluştur**’u seçin.
6. Rapor oluşturma onayı görüntülenir.

Rapordaki öğelerin sayısına bağlı olarak, raporun indirilmaya hazır duruma gelmeden önce birkaç dakikayla saat arasında sürebilir. İleti ayrıntıları raporları sekmesinde ilerlemeyi kontrol edin. Rapor durumu: *Sürüyor veya* *İndirmeye hazır*. Aynı anda 15 ayrı rapor işlemeye kadar sahipsiniz. Raporu indirmek için, İndirmeye hazır *durumdaki bir raporu seçin ve raporu* **indir'i seçin**.

> [!NOTE]
> Seçtiğiniz zaman dönemine herhangi bir ileti sonucu sonuç olarak geri dönmezse, seçilen dönem için hiçbir ileti yoktu. Rapor boş olur.

İleti ayrıntıları raporları ilkede yer alan her ileti öğesi için aşağıdaki bilgileri içerir:

- **Kimlik Eşleşmesi**: İlkede iletinin benzersiz kimliği.
- **Gönderen**: İletinin göndereni.
- **Alıcılar**: İletiye dahil edilen alıcılar.
- **Gönderme Tarihi**: İletinin gönderildiği tarih.
- **Tarih Eşleşmesi**: İletinin ilke koşullarıyla eşleşmesi tarihidir.
- **Konu**: İletinin konusu.
- **Ekleri Içerir**: İletinin tüm eklerinin durumu. Değerler Evet veya Hayır'dır.
- **İlke** Adı: İletiyle ilişkilendirilmiş ilkenin adı. Bu değer, raporki tüm iletiler için aynı olur.
- **Öğe Durumu**: İlkede ileti öğesinin durumu. Değerler Bekliyor veya Çözümlendi.
- **Etiketler**: İletiye atanan etiketler. Değerler Şüpheli, Uyumlu veya Uyumlu olmayan değerlerdir.
- **Anahtar Sözcük Eşleşmeleri**: İleti için anahtar sözcük eşleşmeleri.
- **Gözden geçirenler**: iletiye atanan gözden geçirenler.
- **Bekleyen (gün)**: İletinin beklemede olduğu gün sayısı. Çözülen iletiler için değer 0'dır.
- **Çözülen açıklama**: çözümlen olduğunda iletiyle ilgili açıklamalar.
- **Çözümlenen** Tarih: İletinin çözülmüş olduğu tarih ve saat.
- **Son Güncelleştirme** Tarihi: Son güncelleştirenin kullanıcı adı.
- **Son Güncelleştirme Tarihi**: İletinin son güncelleştirme tarihi ve saati.
- **Açıklama geçmişi**: Açıklama yazarı ve açıklamanın tarihi/saati de içinde olmak üzere ileti uyarısıyla ilgili tüm yorumların listesi.

## <a name="audit"></a>Denetim

Bazı durumlarda, kullanıcı etkinliklerinin ve iletişimlerin gözetimi kanıtlamak için mevzuat veya uyumluluk denetçilerine bilgi sağlamalıdır. Bu bilgiler, tanımlı bir kuruluş ilkesiyle ilişkilendirilmiş tüm etkinliklerin özeti olabilir veya bir iletişim uyumluluk ilkesi her değişiklikte olabilir. İletişim uyumluluk ilkeleri, iç veya dış denetimlere tam hazırlık için yerleşik denetim izlerine sahip olur. Her oluşturma, düzenleme ve silme işlemlerinin ayrıntılı denetim tarihlerini, iletişim ilkeleriniz tarafından yakalanır ve bu şekilde gözetmen yordamları kanıtı sağlar.

> [!IMPORTANT]
> İletişim uyumluluk olaylarının kaydedilmeden önce, denetimin organizasyonunız için etkinleştirilmesi gerekir. Denetimi etkinleştirmek için bkz. [Denetim günlüğünü etkinleştirme](communication-compliance-configure.md#step-2-required-enable-the-audit-log). Etkinlikler Denetim günlüğünde yakalanan olayları tetikle Microsoft 365, bu olayların iletişim uyumluluk ilkesinde görüntülenemleri için 48 saat kadar sürebilir.

İletişim uyumluluğu ilkesi güncelleştirme etkinliklerini görüntülemek için, ana sayfada herhangi **bir ilkeye** yönelik İlke güncelleştirmeleri dışarı aktar denetimlerini seçin. Güncelleştirme etkinliklerini dışarı aktaracak *şekilde Genel Yönetici* *veya* İletişim Uyumluluğu Yöneticisi rollerine atanmış olması gerekir. Bu eylem, aşağıdaki bilgileri içeren .csv bir denetim dosyası üretir:

|**Alan**|**Ayrıntılar**|
|:-----|:-----|
| **Oluşturma Tarihi** | İlkede güncelleştirme etkinliğinin gerçekleştir bitiş tarihi. |
| **UserIds** | İlkede güncelleştirme etkinliği gerçekleştirilen kullanıcı. |
| **Operasyonlar** | İlke üzerinde gerçekleştirilen güncelleştirme işlemleri. |
| **AuditData** | Bu alan, tüm ilke güncelleştirme etkinlikleri için ana veri kaynağıdır. Tüm güncelleştirme etkinlikleri kaydedilir ve virgül sınırlayıcılarla ayrılır. |

Bir ilkeye ilişkin iletişim uyumluluğu gözden geçirme etkinliklerini görüntülemek için,  belirli bir ilkeye ilişkin Genel Bakış sayfasında **Gözden geçirme** etkinliklerini dışarı aktar denetimlerini seçin. Gözden geçirme etkinliklerini dışarı *aktaracak şekilde* *Genel Yönetici veya* İletişim Uyumluluğu Yöneticisi rollerine atanmış olması gerekir. Bu eylem, aşağıdaki bilgileri içeren .csv bir denetim dosyası üretir:

|**Alan**|**Ayrıntılar**|
|:-----|:-----|
| **Oluşturma Tarihi** | Gözden geçirme etkinliğinin ilkede gerçekleştir bitiş tarihi. |
| **UserIds** | bir ilkede gözden geçirme etkinliği gerçekleştirilen kullanıcı. |
| **Operasyonlar** | İlke üzerinde gerçekleştirilen gözden geçirme işlemleri. |
| **AuditData** | Bu alan, tüm ilke gözden geçirme etkinliklerinin ana veri kaynağıdır. Tüm gözden geçirme etkinlikleri virgül sınırlayıcılarla kaydedilir ve birbirinden ayrılır. |

Denetim etkinliklerini birleşik denetim günlüğünde veya [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) PowerShell cmdlet'iyle de görüntüabilirsiniz. Denetim günlüğü bekletme ilkeleri hakkında daha fazla bilgi edinmek için bkz. [Denetim günlüğü bekletme ilkelerini yönetme](audit-log-retention-policies.md).

Örneğin, aşağıdaki örnek tüm gözetmen inceleme etkinliklerinin (ilkeler ve kurallar) etkinliklerini döndürür:

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType AeD -Operations SupervisoryReviewTag
```

Bu örnek, iletişim uyumluluk ilkeleriniz için güncelleştirme etkinliklerini döndürür:

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType Discovery -Operations SupervisionPolicyCreated,SupervisionPolicyUpdated,SupervisionPolicyDeleted
```

Bu örnek, geçerli iletişim uyumluluk ilkelerinize uygun etkinlikleri döndürür:

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -Operations SupervisionRuleMatch
```

İletişim uyumluluğu ilkesi eşleşmeleri, her ilke için bir gözetim posta kutusunda saklanır. Bazı durumlarda, geçerli 100 GB depolama boyutuna veya 1 milyon ileti sınırına yaklaşmamak üzere bir ilke için gözetim posta kutunuzun boyutunu denetlemeniz gerekiyor olabilir. Posta kutusu sınırına ulaşıldısa, ilke eşleşmeleri yakalanz ve aynı etkinliklere yönelik eşleşmeleri yakalamak için yeni bir ilke (aynı ayarlara sahip) oluşturmanız gerekir.

Bir ilkeye gözetim posta kutusunun boyutunu kontrol etmek için aşağıdaki adımları tamamlayın:

1. Bağlan PowerShell'e modern kimlik doğrulamayı kullanarak Exchange Online PowerShell V2 modülünde [Exchange Online-ExchangeOnline](/powershell/module/exchange/connect-exchangeonline) cmdlet'ini kullanın.
2. PowerShell'de aşağıdaki komutu çalıştırın:

    ```PowerShell
    ForEach ($p in Get-SupervisoryReviewPolicyV2 | Sort-Object Name)
    {
       "<Name of your communication compliance policy>: " + $p.Name
       Get-MailboxStatistics $p.ReviewMailbox | ft ItemCount,TotalItemSize
    }
    ```
