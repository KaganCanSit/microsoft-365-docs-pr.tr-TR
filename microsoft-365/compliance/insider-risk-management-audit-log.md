---
title: Insider risk yönetimi denetim günlüğü
description: Microsoft Purview'da insider risk yönetimi denetim günlüğü hakkında bilgi edinin
keywords: Microsoft 365, Microsoft Purview, insider riski, risk yönetimi, uyumluluk
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
ms.openlocfilehash: 544c31205469bcb810bd3f05d9f686d650df6269
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638201"
---
# <a name="insider-risk-management-audit-log"></a>Insider risk yönetimi denetim günlüğü

Insider risk yönetimi denetim günlüğü, insider risk yönetimi özelliklerinde gerçekleştirilen eylemler hakkında bilgi sahibi olmanıza olanak tanır. Bu günlük, bir veya daha fazla iç risk yönetimi rol grubuna atanan kullanıcılar tarafından gerçekleştirilen eylemlerin bağımsız olarak gözden geçirilmesine olanak tanır. Insider risk yönetimi denetim günlüğü kuruluşunuzda otomatik olarak etkinleştirilir ve devre dışı bırakılamaz.

![Insider risk yönetimi denetim günlüğü.](../media/insider-risk-audit-log.png)

denetim günlüğü, izlenen etkinlikler gerçekleştiğinde otomatik olarak ve hemen güncelleştirilir ve günlük, etkinlik hakkındaki bilgileri 180 gün boyunca (yaklaşık altı ay) tutar. 180 gün sonra etkinlik verileri günlükten kalıcı olarak silinir.

Etkinlik izlemede yer alan alanlar şunlardır:

- İlkeler
- Durumda
- Uyarılar
- Ayarlar
- Kullanıcılar
- Bildirim şablonları

Denetim günlüğündeki verileri görüntülemek ve dışarı aktarmak için kullanıcıların *Insider Risk Management* veya *Insider Risk Management Auditors* rol gruplarına atanması gerekir. Insider risk yönetimi rol grupları hakkında daha fazla bilgi edinmek için bkz. [Insider risk yönetimine başlama 1. Adım: İzinleri etkinleştirme](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management).

> [!NOTE]
> Insider risk yönetimi denetim günlüğü Microsoft 365 denetim günlüğüyle ilişkili değildir, bağımsız denetim sistemleridir ve ayrı etkinliklerle ilgili bilgileri yakalar. Microsoft 365 denetimini devre dışı bırakmak, iç risk yönetimi içindeki etkinlik denetimini etkilemez.

## <a name="view-activity-in-the-insider-risk-audit-log"></a>Insider risk denetim günlüğünde etkinliği görüntüleme

Insider risk yönetimi için izlenen özellik etkinliğini görüntülemek için, herhangi bir insider risk yönetimi sekmesinin sağ üst kısmındaki **Insider risk denetim günlüğü** bağlantısına gidin ve seçin. Varsayılan olarak, insider risk yönetimi etkinlikleri için aşağıdaki bilgileri görürsünüz:

- **Etkinlik:** Bir kullanıcı tarafından insider risk yönetimi çözümünde gerçekleştirilen etkinliğin açıklaması.
- **Kategori:** Etkinliğin gerçekleştirildiği alan veya öğe. Örneğin, ilke değişikliği etkinlikleri gerçekleştirildiğinde  kategori olarak İlkeler'i görürsünüz.
- **Gerçekleştirilen etkinlik:** Etkinliği gerçekleştiren kullanıcının kullanıcı adı.
- **Tarih:** Etkinliğin gerçekleştirildiği tarih ve saat. Tarih ve saat, kuruluşunuzun yerel tarih ve saatidir.

Günlüğe kaydedilen etkinlik hakkında daha fazla bilgi için etkinliği seçerek etkinlik ayrıntıları bölmesini görüntüleyin. Bu bölme, etkinlik hakkında ek bilgiler içerir.

## <a name="columns-and-filtering"></a>Sütunlar ve filtreleme

Denetçilerin günlüğe kaydedilen etkinliği gözden geçirmesini kolaylaştırmak için **Insider risk denetim günlüğünde** filtreleme desteklenir. Temel filtreleme için, dosya ve iletilerde farklı özetler sağlamak üzere görünüme kuyruk sütunları eklenebilir. Etkinlikleri Alanlar **tarafından gerçekleştirilen** **Kategori, Tarih aralığı** ve Etkinlik'e göre filtreleyebilirsiniz.

Etkinlik kuyruğuna sütun başlıkları eklemek veya kaldırmak için **Sütunları özelleştir** denetimini kullanın ve sütun seçeneklerinden seçim yapın. Bu sütunlar **Insider risk denetim günlüğünde** desteklenen yaygın koşullarla eşlenir ve bu makalenin devamında listelenmiştir.

## <a name="audit-log-export"></a>Denetim günlüğü dışarı aktarma

*Insider Risk Yönetimi veya Insider Risk Yönetimi* *Denetçileri* rol gruplarına atanan kullanıcılar, **Insider risk denetim** günlüğü sayfasında Dışarı **Aktar'ı** seçerek denetim günlüğündeki tüm etkinlikleri bir .csv (virgülle ayrılmış değerler) dosyasına aktarabilir. Etkinliğe bağlı olarak, bir etkinliğin bazı alanları etkinlik için geçerli olmayabilir ve bu alanlar dışarı aktarılan dosyada boş olarak görünür.

Dosya aşağıdaki alanlar için etkinlik bilgilerini içerir:

- **Gerçekleştirilen etkinlik:** Bir öğe değerini değiştiren kullanıcının kullanıcı adı. Burada listelenen kullanıcılar şu rol [insider risk yönetimi rol gruplarından](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management) birine veya daha fazlasına atanmıştır: *Insider Risk Management*, *Insider Risk Management Yöneticileri*, *Insider Risk Yönetimi Analistleri*, *Insider Risk Yönetimi Araştırmacıları*. Her rol grubunun insider risk özelliklerini yönetmek için farklı izin düzeyleri vardır.
- **Etkinlik:** Bir öğe üzerinde gerçekleştirilen etkinlik. Değerler *Görüntülenir, Silinir, Eklenir, Düzenlenen ilke, Servis Talebi, Kullanıcı, Uyarı* ve *Ayarlar'dır.*
- **Eklendi**: Etkinlik sırasında eklenen kullanıcılar, dosya türleri veya etki alanları gibi nesneler.
- **Uyarı hacmi**: Insider risk yönetimi ayarlarında tanımlanan uyarı birimi düzeyi.
- **Tutar**: İlke için şu anda seçili olan özel gösterge tutarları.
- **Varlık Kimliği**: Etkinliğin gerçekleştirildiği öncelikli fiziksel varlığın varlık kimliği.
- **Kategori:** Değiştirilen öğenin kategorisi. Değerler *İlkeler, Servis Talepleri, Kullanıcılar, Uyarılar, Ayarlar* ve *Bildirim şablonlarıdır.*
- **Tarih:** Kuruluşunuzun yerel tarih ve saatinde listelenen tarih ve saat.
- **Açıklama**: Kullanıcı tarafından üzerinde işlem yapılan nesne için açıklama girişi (ilke veya öncelikli kullanıcı grubu gibi).
- **DLP ilkesi**: Bir iç risk yönetimi ilkesine dahil edilmeyi tetikleme amacıyla seçilen Microsoft Purview Veri Kaybı Önleme (DLP) ilkesi.
- **Gösterge**: Etkinliğin gerçekleştirildiği iç risk ayarlarındaki gösterge (gösterge ekleme veya kaldırma gibi).
- **Bildirim şablonu**: Etkinliğin gerçekleştirildiği bildirim şablonu.
- **Gün sayısı**: İç risk ayarlarında tanımlanan ilke etkinleştirme penceresi.
- **Dosya sayısı**: İç risk yönetimi ayarlarında tanımlanan dosya birimi sınırı.
- **İlke şablonu**: Göstergelerin üzerinde işlem yaptığı ilke şablonu ait.
- **Önceki tutar**: İlke için önceden seçilen özel gösterge tutarları.
- **Öncelikli kullanıcı grubu**: Etkinliğin gerçekleştirildiği öncelikli kullanıcı grubu.
- **Kaldırıldı**: Etkinlik sırasında kaldırılan kullanıcılar, dosya türleri veya etki alanları gibi nesneler.
- **Gönderen**: Etkinliğin gerçekleştirildiği bildirim şablonunun gönderen alanı.
- **Hedef ilke**: Etkinliğin gerçekleştirildiği ilke (örneğin, bir kullanıcıyı ekleme veya kaldırma).
- **Şablon ileti gövdesi**: Etkinliğin gerçekleştirildiği bildirim şablonunun ileti gövdesi.
- **Şablon konusu**: Etkinliğin gerçekleştirildiği bildirim şablonunun konu alanı.
- **Kullanıcı:** Etkinliğin gerçekleştirildiği kullanıcı.
