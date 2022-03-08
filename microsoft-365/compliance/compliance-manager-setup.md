---
title: Microsoft Uyumluluk Yöneticisi ile çalışmaya başlama
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Microsoft Uyumluluk Yöneticisi kullanıcı izinlerini ve rollerini ayarlayın ve eylemlerin otomatik testlerini ayarlayın. Kullanıcı geçmişini yönetin ve pano görünümlerinizi filtreleyin.
ms.openlocfilehash: 070c8fea309ea7c01b82be068acc40a7dcb830ff
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330489"
---
# <a name="get-started-with-compliance-manager"></a>Uyumluluk Yöneticisi'ni çalışmaya başlama

**Bu makalede:** Bu makale Uyumluluk Yöneticisi'ni ayarlamanıza yardımcı olur. Uyumluluk **Yöneticisi'ne erişmeyi** , rolleri **ve** izinleri ayarlamayı ve geliştirme **eylemlerini otomatik olarak yapılandırmayı öğrenin**. Uyumluluk Yöneticisi **panonıza** gidin ve ana sayfaları anleyin: geliştirme eylemleri sayfası, çözüm sayfası, değerlendirmeler sayfası ve değerlendirme şablonları sayfası.

## <a name="who-can-access-compliance-manager"></a>Who Yöneticisi'ne erişenin

Uyumluluk Yöneticisi Office 365 ve Microsoft 365 lisansına sahip kuruluşların ve ABD Government Community Cloud (GCC) Orta, GCC Yüksek ve Savunma Bölümü (DoD) müşterileri tarafından kullanılabilir. Değerlendirmenin kullanılabilirliği ve yönetim özellikleri lisans sözleşmenize bağlıdır.  [Hizmet açıklaması ayrıntılarını görüntüleme](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="before-you-begin"></a>Başlamadan önce

Büyük Microsoft 365 uyumluluk Yöneticisi'ne erişen ilk kullanıcı, büyük olasılıkla kuruluşun genel yöneticisi olur. Genel yöneticinin oturum açmasını ve uyumluluk yöneticisini ilk kez ziyaret ederken aşağıda belirtilen şekilde kullanıcı izinlerini ayarlamasını öneririz.

## <a name="sign-in"></a>Oturum açın

1. Genel yönetici <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a> **gidin ve** hesabınızla Microsoft 365 açın.
2. Sol **gezinti bölmesinde** Uyumluluk Yöneticisi'ni seçin. Uyumluluk Yöneticisi [panonıza gelirsiniz](#understand-the-compliance-manager-dashboard).

Uyumluluk Yöneticisi'ne erişim doğrudan bağlantısıdır [https://compliance.microsoft.com/compliancemanager](https://compliance.microsoft.com/compliancemanager).

## <a name="set-user-permissions-and-assign-roles"></a>Kullanıcı izinlerini ayarlama ve rol atama

Uyumluluk Yöneticisi rol tabanlı bir erişim denetimi (RBAC) izin modeli kullanır. Yalnızca rol atanmış kullanıcılar Uyumluluk Yöneticisi'ne erişebilirsiniz ve her kullanıcı tarafından izin verilen eylemler rol türüne [göre kısıtlanır](#role-types).

### <a name="where-to-set-permissions"></a>İzinlerin ayar bulunduğu yer

Kuruluş için genel yönetici rolünü tutan kişi Uyumluluk Yöneticisi için kullanıcı izinlerini ayarlamasını sağlar. İzinler alan içinde ve Microsoft 365 uyumluluk merkezi (Azure AD) Azure Active Directory ayarlanır.

> [!NOTE]
> US Government Community (GCC) High and Department of Defense (DoD) ortamlarındaki müşteriler yalnızca Azure AD'de Uyumluluk Yöneticisi için kullanıcı izinlerini ve rollerini ayarlayabilir. Azure AD yönergeleri ve rol türü tanımları için aşağıya bakın.

Kaynak dosyada izinleri ayarlamak ve rol Microsoft 365 uyumluluk merkezi aşağıdaki adımları izleyin:

1. Erişim iznine gidin Microsoft 365 uyumluluk merkezi İzinler'i <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**seçin**</a>.

2. Uyumluluk merkezi **açılan listesinde** Roller'i **seçin**.

3. Bir veya birden çok kullanıcı eklemek istediğiniz rol grubunu bulun ve grup adının sol onay kutusunu işaretleyin. (Rollerin [ve ilgili işlevlerin aşağıdaki listesine bakın](#role-types). Rol grubu adları, rol adını taklit ediyor.)

4. Bu grubun uç uç bölmesinde, Üyeler üst bilgisi **altında Düzenle'yi** seçin.

5. Üye **seç'i seçin**. Başka bir açılır pencere görüntülenir.

6. Gruba **eklemek istediğiniz** bir veya daha fazla kullanıcı seçmek için + Ekle'yi seçin.

7. Eklemek istediğiniz adların yanındaki onay kutusunu seçin ve ardından **alttaki Ekle** düğmesini seçin.

8. Kullanıcı atamayı bitirin, Bitti'yi, ardından **Kaydet'i** ve **Kapat'ı** **seçin**.

#### <a name="more-about-azure-ad"></a>Azure AD hakkında daha fazla bilgi

Rolleri atamak ve Azure AD'de izinleri ayarlamak için bkz. Yönetici rolüne sahip olan [kullanıcılara yönetici ve yönetici Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).

Azure AD kimlikleri olmayan ve abonelikler Office 365 Microsoft 365, uyumluluk yöneticisine erişim izni Microsoft 365 uyumluluk merkezi. Uyumluluk Yöneticisi'ne erişim konusunda yardım almak için Uyumluluk [Yöneticisi'cmresearch@microsoft.com](mailto:cmresearch@microsoft.com).

### <a name="role-types"></a>Rol türleri

Aşağıdaki tabloda, Uyumluluk Yöneticisi'nde her rol tarafından izin verilen işlevler gösterilmiştir. Tabloda, her [Bir Azure AD rolüyle Uyumluluk](/azure/active-directory/roles/permissions-reference) Yöneticisi rollerinin nasıl eş adı olduğu da yer alır. Kullanıcıların Uyumluluk Yöneticisi'ne erişmek için en azından Uyumluluk Yöneticisi okuyucu rolüne veya Azure AD genel okuyucu rolüne ihtiyacı olur.

| Kullanıcı şunları şunları olabilir: | Uyumluluk Yöneticisi rolü | Azure AD rolü | 
| :------------- | :-------------: | :------------: |
| **Verileri okuma ancak düzenleme**| Uyumluluk Yöneticisi Okuyucu  | Azure AD Global okuyucu, Güvenlik okuyucu |
| **Verileri düzenleme**| Uyumluluk Yöneticisi Katkı | Uyumluluk Yöneticisi |
| **Test sonuçlarını düzenleme**| Uyumluluk Yöneticisi Değerlendiren | Uyumluluk Yöneticisi |
| **Değerlendirmeleri yönetme, şablon ve kiracı verilerini yönetme**| Uyumluluk Yöneticisi Yönetimi | Uyumluluk Yöneticisi, Uyumluluk Veri Yöneticisi, Güvenlik Yöneticisi  |
| **Kullanıcı atama**| Genel Yönetici | Genel Yönetici |

## <a name="start-a-premium-assessments-trial"></a>Premium değerlendirme denemesi başlatma

Uyumluluk Yöneticisi premium değerlendirmeleri denemesi, organizasyonuyla en ilgili değerlendirmeleri hızla ayarlamak için mükemmel bir yoludur. 300'den fazla şablondanlık kitaplığımız, dünya üzerinde devlet yönetmeliklerini ve endüstri standartlarıyla uyumludur.
Premium değerlendirme denemesi hakkında [daha fazla bilgi edinmek için:](compliance-easy-trials-compliance-manager-assessments.md)

Denemenizi doğrudan Uyumluluk Yöneticisi'ni kullanarak başlatabilirsiniz ve aşağıdaki adımları kullanarak önerilen değerlendirmeleri yapabilirsiniz:

1. Uyumluluk Yöneticisine Genel **Bakış sayfasında** Denemeyi **başlat'ı seçin**. Bir deneme etkinleştirme sihirbazı girersiniz ve bu sihirbaz, organizasyonunız için değerlendirmeleri bize öneririz.

2. Denemeyi **etkinleştir sayfasında**, ücretsiz 90 günlük premium değerlendirme denemenize başlamak ve değerlendirmeleri oluşturmaya devam etmek için Sonraki'yi seçin.

3. Organizasyonlarınızı tanımlamak için bir veya daha fazla endüstriyi seçin ve sonra da Sonraki'yi **seçin**.

4. Kuruluş konumunuz için bir veya daha fazla bölge seçin ve sonra da Sonraki'yi **seçin**.

5. Değerlendirmeleri **seçin ekranında** , Önerilen **şablonlar'ın** yanındaki açılan oku seçerek, organizasyonunız için geçerli olduğunu düşünüyoruz değerlendirmelerin listesini görebilirsiniz. Değerlendirme oluşturmak için kullanmak istediğiniz şablonların yanındaki kutuları işaretleyin ve sonra Sonraki'yi **seçin**.

6. Son seçimlerinizi gözden geçirerek yeni **değerlendirmelerinizi oluşturmak için Önerilen** Değerlendirmeleri Ekle'yi seçin.

Aşağıdaki Değerlendirmeler sayfası bölümünü ziyaret ederek değerlendirmelerle [çalışmaya başlama hakkında daha fazla](#assessments-page) bilgi edinebilirsiniz.

## <a name="settings-for-automated-testing-and-user-history"></a>Ayarlar test ve kullanıcı geçmişi için en iyi nedenler

Uyumluluk Yöneticisi ayarları, Microsoft 365 uyumluluk merkezi eylemlerini otomatik olarak test etme özelliğini etkinleştirmeniz ve devre dışı bırakmanızı sağlar. Ayarlar aynı zamanda geliştirme eylemlerini farklı bir kullanıcıya yeniden atama olanağı da dahil olmak üzere geliştirme eylemleriyle ilişkilendirilmiş kullanıcıların verilerini yönetmenize olanak sağlar.  Yalnızca genel yönetici veya Uyumluluk Yöneticisi Yöneticisi rolüne sahip olan kişiler Uyumluluk Yöneticisi ayarlarına erişim iznine sahip olabilir.

> [!NOTE]
> Otomatik test özelliği, bu ortamlarda Güvenli GCC ve DoD ortamlarındaki müşteriler tarafından kullanılamaz. GCC ve DoD müşterilerinin geliştirme eylemlerini el ile uygulamaları ve testleri gerekir.

### <a name="set-up-automated-testing"></a>Otomatik test ayarlama

Uyumluluk Yöneticisi, bilgi idaresi, bilgi koruma Microsoft 365 veri kaybını önleme, iletişim uyumluluğu ve insider risk yönetimi dahil olmak üzere, diğer uyumluluk çözümlerinden gelen sinyalleri algılar. Her geliştirme eyleminin ayrıntılar sayfasında, Test sekmesindeki  Test mantığı alanı, eylemin uyumluluk puanınızı geçmesi ve bu puandan puan kazan olması için diğer çözümde nelerin gerekli olduğunu gösterir.

Uyumluluk Yöneticisi, Microsoft Güvenli Puanı tarafından da izlenen tamamlayıcı geliştirme eylemlerinden [sinyaller de algılar](../security/defender/microsoft-secure-score.md). Uyumluluk Yöneticisi bu sinyalleri kullanarak sizin için bazı geliştirme eylemlerini otomatik olarak test eder ve bu da uyumluluk etkinliklerinizin verimliliğini en üst düzeye çıkarmanıza yardımcı olur. Geliştirme eylemi başarıyla test edilmiş ve uygulanmışsa, genel uyumluluk puanınıza kredi uygulanan tam puan alırsınız.

Her geliştirme eyleminin ayrıntılar sayfasında

Otomatik test, Uyumluluk Yöneticisi'ni yeni edinen kuruluşlar için varsayılan olarak açıktır. Verilerinizi veya verilerinizi ilk Microsoft 365 Office 365, verileri tümüyle toplamak ve uyumluluk puanınıza faktörünü almak yaklaşık yedi gün sürer. Otomatik test açık olduğunda, eylemin test tarihi güncelleştirilmez, ancak test durumu güncelleştirilir. Yeni değerlendirmeler oluşturulduğunda, puanlar otomatik olarak Microsoft denetim puanlarını ve Güvenli Puan tümleştirmesini içerir.

#### <a name="manage-automated-testing-settings"></a>Otomatik test ayarlarını yönetme

Organizasyon genel yöneticisi otomatik test ayarlarını istediğiniz zaman değiştirebilir. Genel geliştirme eylemleri için otomatik sınamayı kapatabilirsiniz veya tek tek eylemler için açabilirsiniz. Otomatik test ayarlarınızı değiştirmek için aşağıdaki yönergeleri izleyin.

1. Arama <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ayarlar**</a> Seçenekler'Microsoft 365 uyumluluk merkezi.

2. Ayarlar sayfasında Uyumluluk **Yöneticisi'ni seçin**.

3. Sol **gezintiden Otomatik** test'i seçin.

4. Tüm geliştirme eylemleri için otomatik sınamayı açmak, tüm eylemler için kapatmak veya tek tek eylemlerle açmak için ilgili düğmeyi seçin.

5. Geliştirme eylemi **başına aç'ı seçerseniz**, bir liste seçim yapmak için kullanılabilir tüm geliştirme eylemlerini gösterir.  Otomatik olarak sınandırmalarını istediğiniz eylemin yanındaki kutuyu işaretleyin.

6. Ayarlarınızı **kaydetmek için** Kaydet'i seçin. Ekrannizin en üstünde, seçiminizin kaydedldığını haber alan bir onay iletisi alırsınız. Bir hata bildirimi alırsanız yeniden deneyin.

**Not:** Tüm eylemler için otomatik güncelleştirmeleri yalnızca genel yönetici açamaz veya kapatabilirsiniz. Uyumluluk Yöneticisi Yöneticisi tek tek eylemler için otomatik güncelleştirmeleri açabilirsiniz, ancak genel olarak tüm eylemler için açamaz.

**Daha fazla bilgi edinin**
- [Sürekli izlemenin uyumluluk puanınıza nasıl katkıda olduğu hakkında daha fazla bilgi edinin](compliance-score-calculation.md#how-compliance-manager-continuously-assesses-controls).
- [Geliştirme eylemi için test kaynağı atama hakkında daha fazla bilgi öğrenin](compliance-manager-improvement-actions.md#update-testing-source).

### <a name="manage-user-history"></a>Kullanıcı geçmişini yönetme

Kullanıcı **geçmişini yönetme ayarları** , Uyumluluk Yöneticisi'nde geliştirme eylemleriyle hangi kullanıcıların çalıştığını hızla tanımlamanıza yardımcı olur. Geliştirme eylemleriyle ilişkilendirilmiş tanınmaya neden olan kullanıcı verileri, yapılan tüm uygulama ve testlerden, karşıya yüklendikten belgelerden ve girdikleri notlardan içerir. Bu tür verilerin anlaşılması ve alınması, kuruluşun kendi uyumluluk ihtiyaçları için gerekli olabilir.

Kullanıcı geçmişi ayarları, tüm geliştirme eylemlerini bir kullanıcıdan diğerine yeniden atamayı da sağlar.

**Kullanıcı geçmişi ayarlarını bulmak için:**

1. Arama <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ayarlar**</a> Seçenekler'Microsoft 365 uyumluluk merkezi.

2. Ayarlar sayfasında Uyumluluk **Yöneticisi'ni seçin**.

3. Sol **gezintiden Kullanıcı geçmişini** yönet'i seçin.

Kullanıcı **geçmişini yönet** sayfası, geliştirme eylemine atanan e-posta adresine göre tüm kullanıcıların listesini gösterir. Belirli bir **kullanıcıyı** e-posta adresine yazarak hızla bulmak için Ara düğmesini kullanın.

Her kullanıcının e-posta adresinin sağ tarafından, Seç açılan  menüsü raporu dışarı aktarma, geliştirme eylemlerini yeniden atama veya geçmişi silme seçenekleri sağlar. Her seçenekle ilgili ayrıntılar için aşağıdaki bölüme bakın.

#### <a name="export-a-report-of-user-history-data"></a>Kullanıcı geçmişi verileri raporunu dışarı aktarma

Kullanıcıya atanmış Excel geliştirme eylemlerinin listesini içeren bir çalışma dosyasını dışarı aktarabilirsiniz.  Ayrıca rapor, o kullanıcı tarafından karşıya yüklenen kanıt dosyalarını da listeler. Bu bilgiler açık geliştirme eylemlerini yeniden atamanıza yardımcı olabilir.

Rapor, geliştirme eyleminin oluşturma tarihi olarak durumunu yansıtıyor. Bu, durumu veya ataması için yapılan önceki tüm değişikliklerin geçmiş bir raporu değildir (geliştirme eylemleri sayfanıza bir raporun [nasıl dışarı aktarılasını öğrenin](compliance-manager-improvement-actions.md#export-a-report)).

**Kullanıcıya göre rapor dışarı aktarma için aşağıdaki adımları izleyin:**

1. Arama <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ayarlar**</a> Seçenekler'Microsoft 365 uyumluluk merkezi.

2. Ayarlar sayfasında Uyumluluk **Yöneticisi'ni seçin**.

3. Sol **gezintiden Kullanıcı geçmişini** yönet'i seçin.

4. Hedef kullanıcınızı bulmak için, liste e-posta adreslerinde arama veya Ara'ya tıklayın ve kullanıcının e-posta adresini girin.

5. Seç **açılan menüsünde** Raporu dışarı aktar'ı **seçin**.

6. Rapor Excel dosyanız oluşturulsa, bunu açabilir ve yerel makinenize kaydedebilirsiniz.

#### <a name="reassign-improvement-actions-to-another-user"></a>Geliştirme eylemlerini başka bir kullanıcıya yeniden atama

Geliştirme eylemlerini bir kullanıcıdan diğerine yeniden atabilirsiniz. Bir eylemi yeniden imzalarken belge yükleme geçmişi değişmez, ancak geliştirme eylemi içinde artık belgeleri karşıya yük eden kullanıcının adı değişmez.

**Geliştirme eylemlerini başka bir kullanıcıya yeniden atama için aşağıdaki adımları izleyin:**

1. Arama <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ayarlar**</a> Seçenekler'Microsoft 365 uyumluluk merkezi.

2. Ayarlar sayfasında Uyumluluk **Yöneticisi'ni seçin**.

3. Sol **gezintiden Kullanıcı geçmişini** yönet'i seçin.

4. Liste e-posta adreslerini arayarak veya Ara'ya **seçerek** ve bu kullanıcının e-posta adresini girerek bir kullanıcı bulun.

5. Seç **açılan menüsünde** Geliştirme eylemlerini **yeniden at'ı seçin**. Geliştirme **eylemlerini yeniden atama** uç bölmesi görüntülenir.

6. Kullanıcı **ara alanına** , geliştirme eylemlerini atamak istediğiniz kullanıcının adını veya e-posta adresini *girin*.

7. Geliştirme eylemleri altında hedeflenen kullanıcınızı adını gördüğünüzde **, o** kullanıcıyı seçin ve sonra da Eylemler ata'ya **seçin**.

8. Yeniden atama tamamlandığında, çıkış bölmesinde önceki kullanıcıdan gelen tüm iyileştirme eylemlerinin yeni kullanıcıya yeniden atandığı onay iletisi görüntülenir. Yeniden atama başarısızlığı bildirimi alırsanız, pencereyi kapatın ve yeniden deneyin. Uçarak çıkış bölmesini kapatmak için Bitti'yi **seçin**.

Yeni atanan kullanıcı, geliştirme eylemine atandığı bir e-posta alır. E-posta, geliştirme eyleminin ayrıntılar sayfasına doğrudan bir bağlantı içerir.

 > [!NOTE]
> Bekleyen bir güncelleştirmeyi içeren bir eylemi yeniden asınıyorsanız, yeniden atama e-postası içinde yer alan eyleme doğrudan bağlantı, güncelleştirme yeniden atamadan sonra kabul edilirse boz olur. Güncelleştirme kabul edildikten sonra eylemi kullanıcıya yeniden ataarak bu sorunu düzeltebilirsiniz. Geliştirme eylemleri [güncelleştirmeleri hakkında daha fazla bilgi alın](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions).

#### <a name="delete-user-history"></a>Kullanıcı geçmişini silme

Kullanıcının geçmişinin silinmesi geliştirme eylemlerinin sahibi olarak bu geçmişi kaldırır ve Uyumluluk Yöneticisi'nde diğer tüm alanlardan bu kullanıcının adını kaldırır. Bir kullanıcının geçmişini silene kadar, sahip olduğu geliştirme eylemleri yeni bir kullanıcı atanana kadar Atanan  değerini görüntülemez. Geliştirme eylemine yüklenen tüm belgeler, silinen **kullanıcının adı** yerine Kullanıcı kaldırılmış olarak gösterir. Kullanıcı geçmişini silme kalıcıdır.

Kullanıcının geçmişini silmek için aşağıdaki adımları izleyin:

1. Arama <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ayarlar**</a> Seçenekler'Microsoft 365 uyumluluk merkezi.

2. Ayarlar sayfasında Uyumluluk **Yöneticisi'ni seçin**.

3. Sol **gezintiden Kullanıcı geçmişini** yönet'i seçin.

4. Liste e-posta adreslerini arayarak veya Ara'ya **seçerek** ve bu kullanıcının e-posta adresini girerek bir kullanıcı bulun.

5. Seç **açılan menüsünde** Geçmişi sil'i **seçin**.

6. Kullanıcı geçmişinin kalıcı olarak silinmesini onaylamanızı isteyen bir pencere görüntülenir. Silmeye devam etmek için Geçmişi **sil'i seçin**. Geçmişi silmeden ayrılmak için İptal'i **seçin**.

7. Kullanıcı geçmişini yönet sayfasına en **üstte,** kullanıcıyla ilgili geçmişin silindikten sonra bir onay iletisiyle geri dönersiniz.

## <a name="understand-the-compliance-manager-dashboard"></a>Uyumluluk Yöneticisi panosunun ne olduğunu anlama

Uyumluluk Yöneticisi panosu, geçerli uyumluluk nedenlerinizi tek bakışta görüntülemenizi sağlamak için tasarlanmıştır.

:::image type="content" alt-text="Uyumluluk Yöneticisi - pano." source="../media/compliance-manager-dashboard.png" lightbox="../media/compliance-manager-dashboard.png":::

### <a name="overall-compliance-score"></a>Genel uyumluluk puanı

Uyumluluk puanınız göze çarpan bir şekilde en üstte yer alıyor. Önemli veri koruma standartları ve düzenlemelerine uygun geliştirme işlemlerinin tamamlanması için ulaşılabilir puanlara dayalı bir yüzdeyi gösterir. Microsoft tarafından [yönetilen Microsoft](compliance-manager-assessments.md#microsoft-actions-tab) eylemlerinden puanlar, uyumluluk puanınıza da sayılır.

Uyumluluk Yöneticisi'ne ilk kez geldiğinde, ilk puanınız veri koruma temeli [Microsoft 365 temel aya dayalıdır](compliance-manager-assessments.md#data-protection-baseline-default-assessment). Tüm kuruluşların da dahil olduğu bu temel değerlendirme, yaygın endüstri düzenlemelerini ve standartlarını içeren bir dizi denetimdir. Uyumluluk Yöneticisi mevcut gizlilik Microsoft 365 çözümlerinizi tarar ve size geçerli gizlilik ve güvenlik ayarlarınıza göre bir ilk değerlendirme verir. Organizasyonu konuyla ilgili değerlendirmeler eklenizse de puanınız sizin için daha anlamlı hale gelir.

**Daha fazla bilgi:** [Uyumluluk puanının nasıl hesaplanmış olduğunu anlıyoruz](compliance-score-calculation.md).

### <a name="key-improvement-actions"></a>Önemli geliştirme eylemleri

Bu bölümde, genel uyumluluk puanınız üzerinde en büyük olumlu etkiyi sağlamak için şu anda gerçekleştirebilirsiniz. Geliştirme **eylemleri sayfanıza gitmek için** Tüm geliştirme eylemlerini görüntüle'yi seçin.

### <a name="solutions-that-affect-your-score"></a>Puanınızı etkileyen çözümler

Bu bölümde, puanınızı olumlu olarak etki yönde etkilemesine neden olan iyileştirme eylemleri ve bu çözümlerde bekleyen geliştirme eylemlerinin sayısı vurgulanır. Çözüm **sayfanızı ziyaret etmek** için Tüm çözümleri görüntüle'yi seçin.

### <a name="compliance-score-breakdown"></a>Uyumluluk puanı dökümü

Bu bölümde, puanınızı iki farklı şekilde daha ayrıntılı bir şekilde görüntüleyebilirsiniz:

- **Kategoriler**: veri koruma kategorileri içindeki "bilgileri koruma" veya "cihazları yönetme" gibi genel puanın yüzdesini gösterir.
- **Değerlendirmeler**: GDPR veya NIST 800-53 gibi belirli uyumluluk ve veri koruma standartları, yasal düzenlemeler veya yasalar için değerlendirmeleri yönetmede ilerlemenizin yüzdesini gösterir.

### <a name="filtering-your-dashboard-view"></a>Pano görünümlerinizi filtreleme

Pano görünümlerinizi filtreleyebilirsiniz ve yalnızca belirli düzenlemeler ve standartlarla, çözümlerle, eylem türüyle, değerlendirme gruplarıyla veya veri koruma kategorileriyle ilgili öğeleri görebilirsiniz. Görünüme bu şekilde filtre uygulamanız, panodaki puanı da filtre ölçütlerinize göre toplam olası puanlardan kaç puan elde ettiklerinizi göstererek filtreleecektir.

Filtre uygulamak için:

1. **Panonun** sağ üst tarafından Filtrele'yi seçin.
2. Filtreler uç uç bölmesinde filtre **ölçütlerinizi** seçin ve sonra da Uygula'ya **tıklayın**.

Filtreyi uyguladikten sonra, puanınızı gerçek zamanlı olarak düzeltilir. Uyumluluk puanı yüzdesi, döküm bilgileri, iyileştirme eylemleri ve çözümleri, artık yalnızca filtre ölçütleriniz kapsamında yer alan verilere yöneliktir. Uyumluluk Yöneticisi'nin oturumlarını imzalarsanız, yeniden oturum asanız filtrelenmiş görünümünüz kalır.

Filtreleri kaldırmak için:

- Uyumluluk **puanının** üzerindeki Uygulanan filtreler başlığında, kaldırmak istediğiniz tek tek filtrenin yanındaki **X'i** seçin; veya
- **Panonun** sağ üst kısmında Filtre'yi seçin, ardından Filtreler uçarak çıkış **bölmesinde** Filtreleri **temizle'yi seçin**.

## <a name="improvement-actions-page"></a>Geliştirme eylemleri sayfası

[Geliştirme eylemleri](compliance-manager-improvement-actions.md) , kurum tarafından yönetilen eylemlerdir. Geliştirme eylemleriyle çalışmak, uyumluluk etkinliklerinizi merkezileştirmeye ve veri koruma düzenlemeleriyle standartlara uyum içinde çalışmaya yardımcı olur. Her geliştirme eylemi, ayrıntılı uygulama kılavuzu ve sizi uygun çözüme başlatmanız için bir bağlantı verir. Geliştirme eylemleri, uygulama ve test çalışması gerçekleştirmek için kuruluş kullanıcılarınıza atanabilir. Ayrıca geliştirme işlemi içinde belgeleri, notları depolar ve durum güncelleştirmelerini de kayda alabilirsiniz.

### <a name="view-your-improvement-actions"></a>Geliştirme eylemlerinizi görüntüleme

Uyumluluk Yöneticisi panosu önemli geliştirme işlemlerinizi gösterir. Geliştirme eylemlerinizin hepsini görüntülemek için panoda geliştirme eylemleri  sekmesini seçin. Bu sekme sizi geliştirme eylemleri sayfasına getirir. Geliştirme eylemleri sayfanıza **almak için Pano'da** bulunan önemli geliştirme eylemleri listesinin altındaki Tüm geliştirme eylemlerini görüntüle'yi de seçebilirsiniz.

Geliştirme eylemleri sayfası, kurum tarafından yönetilen tüm geliştirme eylemlerini gösterir. Microsoft tarafından yönetilen eylemler her değerlendirme içinde bunlardan bakabilirsiniz (Microsoft eylemleri hakkında daha [fazla bilgi).](compliance-manager-assessments.md#microsoft-actions-tab)

Geliştirme eylemleri sayfasındaki uzun bir eylem listesi varsa, görünüme filtre uygulamanız yararlı olabilir. Eylemler **listesinin** sağ üst köşesindeki Filtre'yi seçin. Filtreler **açılır** bölmesi görüntülendiğinde, kullanılabilir seçeneklerden ölçütlerinizi seçin. Sağ üst köşedeki Grup'a **seçerek** de görünümlerinizi özelleştirebilirsiniz. Açılan menüden gruba, çözüme, kategoriye, eylem türüne veya duruma göre görüntülemek için öğesini seçin.

Bu sayfanın varsayılan görünümü, Geçirilen test durumu ile geliştirme eylemleri **görüntülemez**. Sınamayı geçmiş eylemleri görüntülemek için, Filtreler **uçarak** çıkış bölmesinde Geçirilen kutusunu işaretleyin. Yalnızca puanınıza doğru Geçirilen **sayımın test** durumuna sahip eylemler. Bazı eylemler bekleyen bir güncelleştirme **etiketi gösterebilir.** Geliştirme eylemleri [güncelleştirmeleri hakkında daha fazla bilgi alın](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions).

Geliştirme eylemleri sayfası, her geliştirme işlemi için aşağıdaki veri noktalarını gösterir:

- **Ürünler**: değerlendirilen ürün.
- **Elde edilen** puanlar: eylemi tamamlayarak elde edilen toplamdan elde edilen puan sayısı
- **Yasal** düzenlemeler: Eylemle ilgili düzenlemeler veya standartlar
- **Grup**: eylemi atadığı grup
- **Çözümler**: Eylemi gerçekleştirmek için nereye gidebilirsiniz?
- **Değerlendirmeler**: Eylemi içeren değerlendirmeler
- **Kategoriler**: ilgili veri koruma kategorisi (örneğin, bilgileri koruma, cihazları yönetme vb.)
- **Test durumu**:
  - **Yok** – durum güncelleştirmesi kaydedildi
  - **Değerlendirildi** - test başlamadı
  - **Başarılı** - uygulama başarıyla test edildi
  - **Düşük risk başarısız** oldu - test başarısız oldu, düşük risk
  - **Orta risk başarısız** oldu - test başarısız oldu, orta risk
  - **Yüksek risk başarısız oldu** - test başarısız oldu, yüksek risk
  - **Kapsam dışında** – eylem değerlendirme kapsamına değildir ve puanınızı etkilemez
  - **Algılanmaz-** el ile test için bir eylemin uygulanmış olduğunu, ancak test edile olmadığını gösterir; otomatik test için, bir eylemin otomasyon sonucu için beklediğini gösterir
  - **Algılanamadı** - otomatik durum belirlenemedi
  - **Kısmen test edildi** – kısmi puanlama ile otomatik puanlama
- **Eylem türü**: geliştirme eyleminin teknik bir işlem olup olmadığını gösterir; yani bir çözüm veya ürün içinde uygulanıp uygulanamayacaktır ya da teknik çözüm dışında uygulanacak teknik olmayan bir eylemdir
- **Atanan**: Bu eylemin atandığı kişi (varsa)
- **Test kaynağı**: Eylem için test kaynağının el ile mi yoksa otomatik olarak mı yoksa üst öğeden mi devralınan olduğunu gösterir

**Daha fazla bilgi:** [Geliştirme eylemleri atama ve üzerinde çalışma yapmayı öğrenin](compliance-manager-improvement-actions.md).

## <a name="solutions-page"></a>Çözümler sayfası

Çözümler sayfasında, kazanılan ve olası noktaların paylaşımı çözüme göre düzenleniyor olarak görüntülenir. Bu görünümde kalan noktalarınızı ve geliştirme eylemlerinizi görüntülemek, hangi çözümlerin daha acil dikkat çekmesi gerektiğini anlamanıza yardımcı olur.

Uyumluluk Yöneticisi pano üzerinde Çözümler sekmesini **seçerek** çözümler sayfasını bulun. Ayrıca Panonun **sağ üst kısmında** , **Puanınızı etkileyen** Çözümler altındaki Tüm çözümleri görüntüle'yi de seçin.

### <a name="filtering-your-solutions-view"></a>Çözüm görünümlerinizi filtreleme

Çözüm görünümlerinizi filtrelemek için:

1. Değerlendirme **listenizin** sol üst köşesindeki Filtre'yi seçin.
2. Filtreler **giriş bölmesinde** , istediğiniz ölçütlerin (düzenlemeler, çözümler, eylem türleri, gruplar, kategoriler) yanına bir denetim ekleyin.
3. Uygula **düğmesini** seçin. Filtre bölmesi kapanır ve filtrelenmiş görünüm gösterilir.

Ayrıca, değerlendirme listenizin üstündeki Grup açılır menüsünden gruplama türünü seçerek gruba, ürüne veya düzenlemeye göre değerlendirmeleri görmek için  görünümde değişiklik yapabilirsiniz.

### <a name="taking-action-from-the-solution-page"></a>Çözüm sayfasından işlem alma

Çözümler sayfasında, geliştirme eylemleriyle bağlantılı olarak kuruma yönelik çözümler görüntülenir. Tabloda her çözümün genel puanınıza katkısı, bu çözümde elde edilen ve mümkün olan puanlar ve bu çözümde grup edilen geri kalan geliştirme eylemlerinin puanınızı artırabilirsiniz.

Bu ekrandan iki şekilde işlem yapabilirsiniz:

1. Amaçlanan çözüm sıranız üzerinde, Kalan eylemler **sütunu altında** köprülü numarayı seçin. Bu çözümün test edilmemiş geliştirme eylemlerini gösteren geliştirme eylemleri ekranına filtre uygulanmış bir görünüm görürsünüz.

2. Amaçlanan çözüm sırada, Çözüm aç **sütununu altında** Aç'ı **seçin**. Çözüm veya konumu, önerilen eylemi Microsoft 365 Office 365 güvenlik ve uyumluluk merkezlerinde gördüğünüzde.

## <a name="assessments-page"></a>Değerlendirmeler sayfası

Değerlendirmeler sayfasında, kurum [için ayar](compliance-manager-assessments.md) all değerlendirmeleri listeledik. Uyumluluk puanı paydanız, tüm takip edilen değerlendirmeleriniz tarafından belirlenir. Daha fazla değerlendirme ekleytıkça, geliştirme eylemleri sayfanız üzerinde daha fazla geliştirme eylemi listelenir ve uyumluluk puanı paydanız artar.

Sayfanın **üst kısmında** bulunan etkinleştirilmiş şablonlar sayaçları, şu anda kurumda etkinleştirilmiş olan toplam şablon sayısının dışında kullanmakta olan etkin değerlendirme şablonlarının sayısını gösterir. Daha [fazla bilgi için bkz. Şablon kullanılabilirliği](compliance-manager-templates.md#template-availability-and-licensing) ve lisanslama.

Değerlendirmeler sayfasında her değerlendirmeyle ilgili önemli bilgiler özetlenmiştir:

- **Değerlendirme**: Değerlendirmenin adı
- **Durum**:
  - **Tamamlandı** - tüm denetimlerin durumu "geçti" veya en az bir denetim geçirildi ve geri kalanı "kapsam dışında" olur
  - **Eksik** – en az bir denetim "başarısız" durumuna sahip
  - **Yok** - tüm denetimler sınanmamıştır
  - **Sürüyor** - geliştirme eylemleri "devam ediyor", "kısmi kredi" veya "algılanmadı" gibi başka durumlara da sahip
- **Değerlendirme ilerleme** durumu: Başarıyla test edilen denetim sayısıyla ölçülerek tamamlanmaya yönelik yapılan çalışma yüzdesi
- **Geliştirme eylemleriniz**: denetimlerinizin uygulanmasını karşılayan tamamlanmış eylemlerin sayısı
- **Microsoft eylemleri**: Microsoft denetimlerinin uygulanmasını karşılayan tamamlanmış eylem sayısı
- **Grup**: Değerlendirmenin ait olduğu grubun adı
- **Ürün**: Değerlendirme için tanımlanmış ürün Microsoft 365 ürün gibi ilişkili ürün
- **Düzenleme**: Değerlendirme için geçerli olan mevzuat standardı, politikası veya yasaları

### <a name="filtering-your-assessments-view"></a>Değerlendirmeler görünümlerinizi filtreleme

Değerlendirme görünümlerinizi filtrelemek için:

1. Değerlendirme **listenizin** sol üst köşesindeki Filtre'yi seçin.
2. Filtreler **uç giriş** bölmesinde istediğiniz ölçütleri kontrol edin.
3. Uygula **düğmesini** seçin. Filtre bölmesi kapanır ve filtrelenmiş görünüm gösterilir.

Ayrıca, değerlendirme listenizin üstündeki Grup açılır menüsünden gruplama türünü seçerek gruba, ürüne veya düzenlemeye göre değerlendirmeleri görmek için  görünümde değişiklik yapabilirsiniz.

### <a name="default-assessment"></a>Varsayılan değerlendirme

Varsayılan olarak, değerlendirmeler [sayfasında Veri Koruma Temeli](compliance-manager-assessments.md#data-protection-baseline-default-assessment) değerlendirmesini görebilirsiniz. Uyumluluk Yöneticisi, değerlendirme oluşturmak için önceden [hazır](compliance-manager-templates-list.md) çeşitli şablonlar da sağlar.

## <a name="assessment-templates-page"></a>Değerlendirme şablonları sayfası

Şablon, Uyumluluk Yöneticisi'nde değerlendirme oluşturmaya ilişkin bir çerçevedir. Değerlendirme şablonları sayfasında şablonların listesi ve önemli ayrıntılar görüntülenir. Bu liste Uyumluluk Yöneticisi tarafından sağlanan şablonların yanı sıra, kurum tarafından değiştirilen veya oluşturulan tüm şablonları da içerir. Sertifika, ürün kapsamı, ülke, endüstri ve bunu oluşturan kişi temel alan bir şablonu bulmak için filtreler uygulayabilirsiniz.

Sayfanın **üst kısmında** bulunan etkinleştirilmiş şablonlar sayaçları, şu anda kurumda etkinleştirilmiş olan toplam şablon sayısının dışında kullanmakta olan etkin değerlendirme şablonlarının sayısını gösterir. Daha [fazla bilgi için bkz. Şablon kullanılabilirliği](compliance-manager-templates.md#template-availability-and-licensing) ve lisanslama.

Şablonun açıklamasını ve sertifika, kapsam ve denetim ayrıntıları hakkında daha fazla bilgi içeren ayrıntıları sayfasını getirmek için satırından bir şablon seçin. Bu sayfadan değerlendirme oluşturmak, şablon verilerini kendi verilerinize dışarı aktararak veya şablonu Excel için uygun düğmeleri seçin.

**Daha fazla bilgi:** [Değerlendirme şablonlarıyla çalışma hakkında bilgi okuyun](compliance-manager-templates.md).

## <a name="next-step"></a>Sonraki adım

Değerlendirmeleri ayararak [Uyumluluk Yöneticisi'ni özelleştirin](compliance-manager-assessments.md).
