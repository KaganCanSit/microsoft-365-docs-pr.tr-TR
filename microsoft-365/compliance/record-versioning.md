---
title: SharePoint veya başka bir sürümde depolanan kayıtları güncelleştirmek OneDrive
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
search.appverid:
- MOE150
- MET150
description: Kayıt yönetiminde bir çözüm uygulamanıza yardımcı olacak kayıtlar hakkında bilgi Microsoft 365.
ms.openlocfilehash: 2aabfbf1b3e0aedd8ec7ba54d452cb01ad81776a
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009978"
---
# <a name="use-record-versioning-to-update-records-stored-in-sharepoint-or-onedrive"></a>SharePoint veya başka bir sürümde depolanan kayıtları güncelleştirmek OneDrive

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

> [!NOTE]
> Yasal düzenleme kayıtları düzenlemeyi engellesi nedeniyle, kayıt sürüm düzenlemesi yasal düzenleme kayıtlarında kullanılamaz.
>
> Yasal düzenlemeler kayıtlarını kullanmasanız bile kiracınız için kayıt sürümü oluşturmasını da önebilirsiniz: Microsoft 365 uyumluluk merkezi > **Kayıt** >  yönetimi **ayarlarıRetention** >  etiketleriTakki sürümünü yapılandırma ve Ardından Kayıt sürümünü etkinleştir ayarını **kapatın.**

Belgeyi kayıt olarak işaretleme ve kayıtta [](records-management.md#records) gerçekleştirilecek eylemleri kısıtlama özelliği, tüm kayıt yönetimi çözümlerini temel alan bir hedeftir. Bununla birlikte, kişilerin başka sürümler oluşturması için de işbirliği gerekli olabilir.

Örneğin, bir satış sözleşmesini kayıt olarak işaretlerini işaretley biliyor, ancak sonra önceki kayıt sürümünü korurken sözleşmeyi yeni koşullarla güncelleştirmeniz ve en son sürümü yeni kayıt olarak işaretlemeniz gerekiyor olabilir. Bu tür senaryolarda, SharePoint ve OneDrive sürüm *kaydetme desteği sağlar*. OneNote defteri klasörleri kayıt sürümü oluşturmayı desteklemez.

Kayıt sürümü oluşturmayı kullanmak için, önce [belgeyi etiketler ve kayıt olarak işaretlersiniz](declare-records.md). Bu noktada, bekletme etiketinin yanında Kayıt *durumu* adlı bir belge özelliği görüntülenir ve ilk kayıt durumu Kilitli durumda **olur**.

Artık aşağıdaki işleri yapabilirsiniz:

- **Kayıt durumu özelliğinin kilidini açarak ve kilitleyerek, belgenin tek tek sürümlerini sürekli olarak kayıt olarak düzenleyebilir ve koruyabilirsiniz.** Ancak Kayıt **durumu özelliği** Kilitli olarak ayarlanmış **olduğunda** kaydın yeni bir sürümü korunur. Kilitli ve kilitli olan bu geçiş, belgenin gereksiz sürümlerini ve kopyalarını tutma riskini azaltır.

- **Kayıtların site koleksiyonu içinde bulunan yerinde kayıt deposunda otomatik olarak depolanmış olarak depolarını sağlar.** Site koleksiyonu ve SharePoint OneDrive Saklama kitaplığında bulunan içeriği korur. Kayıt sürümleri bu kitaplığın Kayıtlar klasöründe depolanır.

- **Tüm sürümleri içeren, hiç eskiyen bir belgeyi koruma.** Varsayılan olarak, SharePoint ve OneDrive belgeye, öğe menüsünde bir sürüm geçmişi vardır. Bu sürüm geçmişinde, hangi sürümlerin kayıt olduğunu kolayca görebilir ve bu belgeleri görüntüebilirsiniz.

> [!TIP]
> Silme eylemi olan bir bekletme etiketiyle kayıt sürümünü kullanırsanız bekletme ayarını Yapılandırmayı göz önünde bulundurarak Bekletme dönemini **şu** şekilde başlat: öğelerin etiketli olduğu **zaman olarak ayarlamayı düşünebilirsiniz**. Bu etiket ayarıyla, bekletme döneminin başlangıcı her yeni kayıt sürümü için sıfırlanır ve bu da eski sürümlerin daha yeni sürümlerden önce silinmesini sağlar.

Kayıt sürümü oluşturma, öğeyi kayıt olarak işaret alan bir bekletme etiketinin uygulandığı tüm belgelarda otomatik olarak kullanılabilir ve bu etiket [sitede yayımlanır](create-apply-retention-labels.md). Kullanıcı ayrıntılar bölmesini kullanarak belge özelliklerini görüntülerken, Kayıt durumunu Kilitli olan kilidi Açık **olarak** **değiştirin**. Bu eylem, Kayıt klasörünün Saklama kitaplığında bir kayıt oluşturur ve bu kayıt bekletme döneminin kalan süresi için burada bulunur.

Belgenin kilidi açıkken, standart düzenleme izinleri olan tüm kullanıcılar dosyayı düzenleyebilir. Bununla birlikte, bu hala bir kayıt olduğu için kullanıcılar dosyayı silemez. Düzenleme tamamlandığında, kullanıcı Kayıt durumunu Kilitli olarak açıp Kilitli durumdayken başka düzenlemeler de  engellensin.
<br/><br/>

:::image type="content" alt-text="Kayıt olarak etiketlenen belgede kayıt durumu özelliği." source="../media/recordversioning8.png" lightbox="../media/recordversioning8.png":::

## <a name="locking-and-unlocking-a-record"></a>Kaydı kilitleme ve kilidini açma

Belgeye içeriği kayıt olarak işaret alan bir bekletme etiketi uygulandıktan sonra, Katkıda Bulun izinlerine veya daha dar izin düzeyine sahip olan tüm kullanıcılar kaydın kilidini açabilir veya kilitli durumdaki kaydı kilitler.
<br/><br/>

:::image type="content" alt-text="Kayıt durumu, kayıt belgesinin kilitli olduğunu gösterir." source="../media/recordversioning9.png" lightbox="../media/recordversioning9.png":::

Kullanıcı kaydın kilidini açsa, aşağıdaki eylemler gerçekleşir:

1. Geçerli site koleksiyonunda KorumaYılı Saklama kitaplığı yoksa, bir tane oluşturulur.

2. Saklama Kitaplığı'nın Bir Kayıtlar klasörü yoksa, bir tane oluşturulur.

3. Kopyala **eylemi** belgenin en son sürümünü Kayıtlar klasörüne kopyalar. Kopyala **eylemi yalnızca** en son sürümü içerir ve önceki sürümleri içerir. Kopyalanan bu belge artık belgenin kayıt sürümü olarak kabul edilir ve dosya adı şöyle olur: \[Başlık GUID Sürümü\#\]

4. Kayıtlar klasöründe oluşturulan kopya, özgün belgenin sürüm geçmişine eklenir ve bu sürümde açıklamalar **alanında Kayıt** sözcüğü görünür.

5. Özgün belge, düzenlenebilir ancak silinemez yeni bir sürümdür. Belge kitaplığı sütunu **Öğe bir** Kayıttır, çünkü belge artık  düzenlense bile yine de bir kayıttır.

Kullanıcı kaydı kilitlerken, özgün belge yeniden düzenlenemez. Ancak, Saklama Saklama kitaplığında, bir sürümü Kayıtlar klasörüne kopyaan bir kaydın kilidini açma eylemidir.

## <a name="record-versions"></a>Kayıt sürümleri

Kullanıcı bir kaydın kilidini her açsa, en son sürüm Koruma Saklama kitaplığına kopyalanır ve bu sürüm sürüm geçmişinin Açıklamalar alanında Kayıt değerini  içerir.
<br/><br/>

:::image type="content" alt-text="Saklama kitaplığında gösterilen kayıt." source="../media/recordversioning10.png" lightbox="../media/recordversioning10.png":::

Sürüm geçmişini görüntülemek için, belge kitaplığında bir belge seçin ve ardından öğe menüsünde **Sürüm Geçmişi'ne** tıklayın.

## <a name="where-records-are-stored"></a>Kayıtların depolandığı yer

Kayıtlar, site koleksiyonunda en üst düzey sitenin Saklama kitaplığında bulunan Kayıtlar klasöründe depolanır. En üst düzey sitenin sol gezinti bölmesinde Site içeriği Saklama **Kitaplığı'nın** \> **içeriğini seçin**.
<br/><br/>

![Saklama kitaplığı.](../media/recordversioning11.png)

<br/><br/>

![Saklama Kitaplığı'nın Kayıtlar klasörü.](../media/recordversioning12.png)

Saklama Kitaplığı'nın nasıl çalıştığını daha fazla bilgi için bkz. Saklama saklama [kitaplığında SharePoint nasıl OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive).

## <a name="searching-the-audit-log-for-record-versioning-events"></a>Kayıt sürüm denetleme olayları için denetim günlüğünde arama

Kayıtları kilitleme ve kilit açma eylemleri denetim günlüğüne kaydedilir. Dosya **ve sayfa etkinlikleri arasında,** Kayıt **durumu kilitli olarak değiştirildi ve Kilitli** **kayıt durumu kilidi açık olarak değiştirildi'yi seçin**.

Bu olayları arama hakkında daha fazla bilgi için bkz. [Denetim günlüğünde arama.](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities)

## <a name="next-steps"></a>Sonraki adımlar

Kayıt yönetimi tarafından desteklenen diğer senaryolar için bkz. [Kayıt yönetimi için genel senaryolar](get-started-with-records-management.md#common-scenarios).
