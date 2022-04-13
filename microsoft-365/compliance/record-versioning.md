---
title: SharePoint veya OneDrive depolanan kayıtları güncelleştirmek için kayıt sürümü oluşturma özelliğini kullanma
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
description: Microsoft 365'de kayıt yönetimi çözümü uygulamanıza yardımcı olacak kayıtlar hakkında bilgi edinin.
ms.openlocfilehash: 7fc4f9bb14e9e49c7894e864b8ff9e8f4337149a
ms.sourcegitcommit: 5eff41a350a01e18d9cdd572c9d8ff99d6c9563a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64835897"
---
# <a name="use-record-versioning-to-update-records-stored-in-sharepoint-or-onedrive"></a>SharePoint veya OneDrive depolanan kayıtları güncelleştirmek için kayıt sürümü oluşturma özelliğini kullanma

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Mevzuat kayıtları düzenlemeyi engellediğinden, kayıt sürümü oluşturma yasal kayıtlarda kullanılamaz.
>
> Ayrıca, yasal düzenleme kayıtlarını kullanmasanız bile kiracınız için kayıt sürümü oluşturmayı engelleyebilirsiniz: kayıt **yönetimi ayarlarını** >  Microsoft 365 uyumluluk merkezi > **Kayıtlar yönetim** düğümüne **gidinGelen etiketler** >  **Kayıt sürümü oluşturmayı yapılandırma** ve ardından **Kayıt sürümünü etkinleştirme** ayarını kapatın.

Belgeyi kayıt olarak işaretleme ve [kayıt](records-management.md#records) üzerinde gerçekleştirilebilecek eylemleri kısıtlama özelliği, tüm kayıt yönetimi çözümleri için önemli bir hedeftir. Ancak, kişilerin sonraki sürümleri oluşturması için de işbirliği gerekebilir.

Örneğin, bir satış sözleşmesini kayıt olarak işaretleyebilir, ancak ardından sözleşmeyi yeni koşullarla güncelleştirmeniz ve önceki kayıt sürümünü korurken en son sürümü yeni bir kayıt olarak işaretlemeniz gerekir. Bu tür senaryolar için SharePoint ve OneDrive *kayıt sürümü oluşturma desteği sağlar*. OneNote not defteri klasörleri kayıt sürümü oluşturma işlemini desteklemez.

Kayıt sürümü oluşturmayı kullanmak için, önce belgeyi [öğeleri kayıt olarak işaretlemek üzere yapılandırılmış bir bekletme etiketiyle](declare-records.md) etiketlersiniz. Bu noktada, bekletme etiketinin yanında *Kayıt durumu* adlı bir belge özelliği görüntülenir. Etiketin varsayılan olarak kaydın kilidini açmak için yapılandırılıp yapılandırılmadığına bağlı olarak (şu anda kullanıma sunılıyor), ilk kayıt durumu **Kilitli** veya **Kilitsiz'dir**.

Artık aşağıdakileri yapabilirsiniz:

- **Kayıt durumu özelliğinin kilidini açıp kilitleyerek belgenin tek tek sürümlerini sürekli olarak düzenleyin ve tutun.** Yalnızca **Kayıt durumu** özelliği **Kilitli** olarak ayarlandığında tutulan kaydın yeni bir sürümüdür. Kilitli ve kilidi açılmış bu geçiş, belgenin gereksiz sürümlerini ve kopyalarını saklama riskini azaltır.
    
    > [!NOTE]
    > Etiket varsayılan olarak kaydın kilidini açmak üzere yapılandırılmışsa, ancak sürüm oluşturma yönetici tarafından etkinleştirilmediyse veya kayıt yönetimi ayarı tarafından engelleniyorsa, kullanıcılar belgeyi kilitledikten sonra belgenin kilidini açamaz.

- **Kayıtların siteyle birlikte bulunan yerinde kayıt deposunda otomatik olarak depolanmasını sağlayın.** SharePoint ve OneDrive'daki her site, Koruma Bekletme kitaplığındaki içeriği korur. Kayıt sürümleri bu kitaplıktaki Kayıtlar klasöründe depolanır. Koruma Bekletme kitaplığının nasıl çalıştığı hakkında daha fazla bilgi için bkz. [Bekletme SharePoint ve OneDrive için nasıl çalışır](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive)?

- **Tüm sürümleri içeren her zaman yeşil bir belgeyi koruyun.** Varsayılan olarak, her SharePoint ve OneDrive belgenin öğe menüsünde bir sürüm geçmişi vardır. Bu sürüm geçmişinde, hangi sürümlerin kayıt olduğunu kolayca görebilir ve bu belgeleri görüntüleyebilirsiniz.

> [!TIP]
> Silme eylemi olan bir bekletme etiketiyle kayıt sürümü oluşturmayı kullandığınızda, Bekletme süresini **başlat seçeneğini şu şekilde** yapılandırmayı göz önünde bulundurun: **Öğeler etiketlendiğinde** olacak şekilde. Bu etiket ayarıyla, saklama süresinin başlangıcı her yeni kayıt sürümü için sıfırlanır ve bu da eski sürümlerin daha yeni sürümlerden önce silinmesini sağlar.

Varsayılan olarak, kayıt sürümü oluşturma, öğeyi kayıt olarak işaretleyen bir bekletme etiketi uygulanmış olan tüm belgeler için otomatik olarak kullanılabilir ve bu etiket [sitede yayımlanır](create-apply-retention-labels.md). Kullanıcı ayrıntılar bölmesini kullanarak belge özelliklerini görüntülediğinde, **Kayıt durumunu** **Kilitli** ve **Kilitsiz** arasında değiştirebilir.

Belgenin kilidi açıkken, standart düzenleme izinlerine sahip tüm kullanıcılar dosyayı düzenleyebilir. Ancak, yine de bir kayıt olduğundan kullanıcılar dosyayı silemez. Düzenleme tamamlandığında, kullanıcı **Bu durumdayken** daha fazla düzenleme yapılmasını önleyen Kayıt durumunu **Kilitsiz'den** **Kilitli'ye** değiştirebilir.
<br/><br/>

:::image type="content" alt-text="Kayıt olarak etiketlenmiş belgedeki kayıt durumu özelliği." source="../media/recordversioning8.png" lightbox="../media/recordversioning8.png":::

Bir kayıt kilitliyken veya kilidi açıkken hangi kullanıcı eylemlerine izin verilenler hakkında daha fazla bilgi için bkz. [İzin verilen veya engellenen eylemler için kısıtlamaları karşılaştırma](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked).

## <a name="locking-and-unlocking-a-record"></a>Kaydı kilitleme ve kilidini açma

Belgeye kayıt olarak içerik işaretleyen bir bekletme etiketi uygulandıktan sonra, Katkıda Bulunma izinlerine veya daha dar izin düzeyine sahip tüm kullanıcılar kaydın kilidini açabilir veya kilidi açılmış bir kaydı kilitleyebilir.
<br/><br/>

:::image type="content" alt-text="Kayıt durumu, kayıt belgesinin kilidinin açık olduğunu gösterir." source="../media/recordversioning9.png" lightbox="../media/recordversioning9.png":::

Kaydın kilidi açıkken aşağıdaki eylemler gerçekleştirilir:

1. Geçerli sitede Koruma Bekletme kitaplığı yoksa, bir tane oluşturulur.

2. Koruma Bekletme kitaplığında Kayıtlar klasörü yoksa, bir klasör oluşturulur.

3. **Kopyala** eylemi, belgenin en son sürümünü Kayıtlar klasörüne kopyalar. **Kopyala** eylemi yalnızca en son sürümü içerir ve önceki sürümleri içermez. Kopyalanan bu belge artık belgenin kayıt sürümü olarak kabul edilir ve dosya adı şu biçime sahiptir: \[Başlık GUID Sürümü\#\]

4. Kayıtlar klasöründe oluşturulan kopya, özgün belgenin sürüm geçmişine eklenir ve bu sürüm, açıklamalar alanında **Kayıt** sözcüğünü gösterir.

5. Özgün belge, düzenlenebilen ancak silinmeyecek yeni bir sürümdür. Belge kitaplığı sütunu **Öğe kayıttır** , belge artık düzenlense bile yine de bir kayıt olduğundan **Evet** değerini gösterir.

Kullanıcı bir kaydı kilitlediğinde, özgün belge yeniden düzenlenemez. Ancak, bir sürümü Koruma Bekletme kitaplığındaki Kayıtlar klasörüne kopyalayan bir kaydın kilidini açma eylemidir.

## <a name="record-versions"></a>Kayıt sürümleri

Bir kaydın kilidi her açıldığında, en son sürüm Koruma Saklama kitaplığına kopyalanır ve bu sürüm sürüm geçmişinin **Açıklamalar** alanındaki **Kayıt** değerini içerir.
<br/><br/>

:::image type="content" alt-text="Koruma Bekletme kitaplığında gösterilen kayıt." source="../media/recordversioning10.png" lightbox="../media/recordversioning10.png":::

Sürüm geçmişini görüntülemek için, belge kitaplığında bir belge seçin ve ardından öğe menüsünde **Sürüm geçmişi'ne** tıklayın.

## <a name="searching-the-audit-log-for-record-versioning-events"></a>Kayıt sürüm oluşturma olayları için denetim günlüğünde arama yapma

Kayıtları kilitleme ve kilidini açma eylemleri denetim günlüğüne kaydedilir. **Dosya ve sayfa etkinlikleri'nden** **Kayıt durumu kilitli olarak değiştirildi** ve **Kayıt durumu kilitsiz olarak değiştirildi'yi** seçin.

Bu olayları arama hakkında daha fazla bilgi için bkz [. Denetim günlüğünde arama](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities) yapma.

## <a name="next-steps"></a>Sonraki adımlar

Kayıt yönetimi tarafından desteklenen diğer senaryolar için bkz. [Kayıt yönetimi için yaygın senaryolar](get-started-with-records-management.md#common-scenarios).
