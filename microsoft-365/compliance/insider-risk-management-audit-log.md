---
title: Insider risk yönetimi denetim günlüğü
description: Microsoft 365'da Insider risk yönetimi denetim günlüğü hakkında bilgi Microsoft 365
keywords: Microsoft 365, insider risk yönetimi, risk yönetimi, uyumluluk
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: 2bf453e8856f69e9ddb8c7c7a9264267ef77b4f0
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989961"
---
# <a name="insider-risk-management-audit-log"></a>Insider risk yönetimi denetim günlüğü

Insider risk yönetimi denetim günlüğü, Insider risk yönetimi özellikleri üzerinde yapılan işlemler hakkında bilgi sahibi kalmanız için olanak sağlar. Bu günlük, bir veya birden çok insider risk yönetimi rol gruplarına atanan kullanıcıların  gerçekleştirdığı eylemlerin bağımsız olarak gözden alınmasına olanak sağlar. Insider risk yönetimi denetim günlüğü, kurum içinde otomatik olarak etkinleştirilir ve devre dışı bırakılamaz.

![Insider risk yönetimi denetim günlüğü.](../media/insider-risk-audit-log.png)

Denetlenen etkinlikler her izlendiğinde denetim günlüğü otomatik olarak ve hemen güncelleştirilir ve günlük 180 gün (yaklaşık altı ay) boyunca etkinlikle ilgili bilgileri korur. 180 gün sonra, etkinlik verileri günlükten kalıcı olarak silinir.

Etkinlik izlemesinde yer alan alanlar şunlardır:

- İlkeler
- Vakalar
- Uyarılar
- Ayarlar
- Kullanıcılar
- Bildirim şablonları

Denetim günlüğünden verileri görüntülemek ve dışarı aktar almak için, kullanıcıların *Insider Risk Yönetimi* veya *Insider Risk Yönetimi Denetçileri rol gruplarına atanmaları* gerekir. Insider risk yönetimi rol grupları hakkında daha fazla bilgi edinmek için bkz [. Insider risk yönetimiyle çalışmaya başlama 1. Adım: İzinleri etkinleştirme](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management).

> [!NOTE]
> Insider risk yönetimi denetim günlüğü, bağımsız denetim sistemleri Microsoft 365 ve ayrı etkinliklerle ilgili bilgi yakalamak için bu denetim günlüğüyle ilişkilendirilz. Denetim Microsoft 365 devre dışı bırakmak, Insider risk yönetimi içinde etkinlik denetimini etkilenmez.

## <a name="view-activity-in-the-insider-risk-audit-log"></a>Insider risk denetim günlüğünde etkinliği görüntüleme

Insider risk yönetimiyle ilgili izlenen özellik etkinliğini görüntülemek için, herhangi bir Insider risk yönetimi sekmesinin sağ üst alanında **yer alan Insider risk** denetim günlüğü bağlantısına gidin ve bu bağlantıyı seçin. Varsayılan olarak, Insider risk yönetimi etkinlikleri için aşağıdaki bilgileri görüntülenir:

- **Etkinlik:** Kullanıcı tarafından Insider risk yönetimi çözümü kapsamında  alınan etkinliğin açıklaması.
- **Kategori:** Etkinliğin gerçekleştir olduğu alan veya öğe. Örneğin, ilke değişikliği etkinlikleri *gerçekleştirn* olduğunda İlkeler'i kategori olarak görüyorsunuz.
- **Gerçekleştirilen etkinlik:** Etkinliği gerçekleştirilen kullanıcının kullanıcı adı.
- **Tarih:** Etkinliğin gerçekleştirildi olduğu tarih ve saat. Tarih ve saat, kurum için yerel tarih ve saattir.

Günlüğe kaydedilen bir etkinlik hakkında daha fazla bilgi için etkinliği seçerek etkinlik ayrıntıları bölmesini görüntüleyin. Bu bölmede etkinlikle ilgili ek bilgiler yer eder.

## <a name="columns-and-filtering"></a>Sütunlar ve filtreleme

Denetçilerin günlüğe kaydedilen etkinliği gözden geçirmesini kolaylaştırmak için, **filtreleme Insider risk denetim günlüğünde de destekler**. Temel filtreleme için, dosyalarda ve iletilerde farklı özetler sağlamak için kuyruk sütunları görünüme eklenir. Etkinlikleri Kategori, Tarih aralığı **ve alanlar tarafından gerçekleştirilen Etkinlik'e** **göre filtreleebilirsiniz** .

Etkinlik sırasına sütun başlıkları eklemek veya kaldırmak için Sütunları **özelleştirin seçeneğini kullanın** ve sütun seçeneklerinden birini belirleyin. Bu sütunlar, **Insider risk** denetim günlüğünde desteklenen yaygın koşulları eşler ve bu makalenin devamlarında listelenir.

## <a name="audit-log-export"></a>Denetim günlüğü dışarı aktarma

*Insider Risk Yönetimi veya Insider* Risk Yönetimi Denetçileri rol gruplarına atanan kullanıcılar,  *Insider risk* denetim günlüğü sayfasındaki Dışarı Aktar'ı seçerek denetim günlüğünde bulunan tüm etkinlikleri bir .csv (virgülle ayrılmış değerler) dosyasına aktarabilir. Etkinlike bağlı olarak, etkinlikle ilgili bazı alanlar etkinlik için geçerli olamayabilirsiniz ve bu alanlar dışarı aktarıldı dosyasında boş olarak görünür.

Dosya, aşağıdaki alanlara ilişkin etkinlik bilgilerini içerir:

- **Gerçekleştirilen etkinlik:** Öğe değerini değiştiren kullanıcının kullanıcı adı. Burada listelenen kullanıcılar, aşağıdaki [Insider risk](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management) yönetimi rol gruplarından bir veya birden fazlasına atanmıştır: *Insider Risk Yönetimi*, *Insider Risk Yönetimi* Yöneticileri, *Insider Risk Yönetimi* Analistleri, *Insider Risk Yönetimi İlkeleri*. Her rol grubunun Insider risk özelliklerini yönetmeye farklı izin düzeyleri vardır.
- **Etkinlik:** Bir öğe üzerinde  alınan etkinlik. Değerler *Görüntüleniyor, Silindi, Eklendi, Düzenlenen ilke, Olay, Kullanıcı, Uyarı* ve *Ayarlar.*
- **Eklendi**: Etkinlik sırasında eklenen, kullanıcılar, dosya türleri veya etki alanları gibi nesneler.
- **Uyarı düzeyi**: Insider risk yönetimi ayarlarında tanımlanan uyarı düzeyi.
- **Tutar**: İlke için şu anda seçili olan özel gösterge miktarıdır.
- **Varlık Kimliği**: Etkinliğin gerçekleştirmiş olduğu öncelikli fiziksel varlığın varlık kimliğidir.
- **Kategori:** Değiştirilen öğenin kategorisi. Değerler *İlkeler, Vakalar, Kullanıcılar, Uyarılar, Ayarlar Bildirim* *şablonlarıdır.*
- **Tarih:** Kuruluşun yerel tarih ve saatlerinde listelenen tarih ve saat.
- **Açıklama**: Üzerinde eylem yapılan nesne (ilke veya öncelikli kullanıcı grubu gibi) için kullanıcı tarafından yapılan açıklama.
- **DLP ilkesi**: Veri kaybı önleme (DLP) ilkesi, insider risk yönetimi ilkesine dahil edilmeyi tetikler.
- **Gösterge**: Insider risk ayarları içinde etkinliğin gerçekleştirilen göstergesi (bir gösterge ekleme veya kaldırma gibi).
- **Bildirim şablonu**: Etkinliğin gerçekleştir olduğu bildirim şablonu.
- **Gün sayısı**: Insider risk ayarlarında tanımlanan ilke etkinleştirme penceresi.
- **Dosya sayısı**: Insider risk yönetimi ayarlarında tanımlanan dosya hacmi sınırı.
- **İlke** şablonu: Göstergelerin üzerinde işlem yapılan ilke şablonu.
- **Önceki tutar**: İlke için önceden seçilen özel gösterge tutarları.
- **Öncelik kullanıcı grubu**: Etkinliğin gerçekleştir olduğu öncelik kullanıcı grubu.
- **Kaldırıldı**: Etkinlik sırasında kullanıcılar, dosya türleri veya etki alanları gibi kaldırılan nesneler.
- **Gönderen**: Etkinlik gerçekleştirilen bildirim şablonunun gönderen alanı.
- **Hedef ilke**: Etkinliğin üzerinde gerçekleştirilen ilke (kullanıcı ekleme veya kullanıcının kaldırılması gibi).
- **Şablon ileti gövdesi**: Etkinlik gerçekleştirilen bildirim şablonunun ileti gövdesi.
- **Şablon konusu**: Etkinlik gerçekleştirilen bildirim şablonunun konu alanı.
- **Kullanıcı:** Etkinlik gerçekleştirilen kullanıcı.
