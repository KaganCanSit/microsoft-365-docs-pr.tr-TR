---
title: Microsoft Purview Uyumluluk Yöneticisi'yle çalışmaya başlama
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
description: Microsoft Purview Uyumluluk Yöneticisi kullanıcı izinlerini ve rollerini ayarlayın ve eylemlerin otomatik testini yapılandırın. Kullanıcı geçmişini yönetin ve pano görünümünüzü filtreleyin.
ms.openlocfilehash: 1053ff60416a80d88e29e8a8f4bc9ac3fdfc133b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634775"
---
# <a name="get-started-with-compliance-manager"></a>Uyumluluk Yöneticisini kullanmaya başlama

**Bu makalede:** Bu makale, Uyumluluk Yöneticisi'nin ayarlanmasına yardımcı olur. Uyumluluk Yöneticisi'ne **erişmeyi** , **rolleri ve izinleri ayarlamayı ve** **iyileştirme eylemlerinin otomatik testini yapılandırmayı** öğrenin. **Uyumluluk Yöneticisi panonuzda** ilerleyin ve ana sayfaları anlayın: iyileştirme eylemleri sayfası, çözümler sayfası, değerlendirmeler sayfası ve değerlendirme şablonları sayfası.

## <a name="who-can-access-compliance-manager"></a>Uyumluluk Yöneticisi'ne kimler erişebilir?

Uyumluluk Yöneticisi, Office 365 ve Microsoft 365 lisanslarına sahip kuruluşlar ve US Government Community Cloud (GCC) Moderate, GCC High ve Savunma Bakanlığı (DoD) müşterileri tarafından kullanılabilir. Değerlendirme kullanılabilirliği ve yönetim özellikleri lisans sözleşmenize bağlıdır.  [Hizmet açıklaması ayrıntılarını görüntüleyin](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-compliance-manager).

## <a name="before-you-begin"></a>Başlamadan önce

Kuruluşunuzun Microsoft 365 genel yöneticisi büyük olasılıkla Uyumluluk Yöneticisi'ne erişen ilk kullanıcı olacaktır. Genel yöneticinin, Uyumluluk Yöneticisi'ni ilk kez ziyaret ederken aşağıda açıklandığı gibi oturum açmasını ve kullanıcı izinlerini ayarlamasını öneririz.

## <a name="sign-in"></a>Oturum açın

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a> gidin ve Microsoft 365 genel yönetici hesabınızla **oturum açın**.
2. Sol gezinti bölmesinde **Uyumluluk Yöneticisi'ni** seçin. [Uyumluluk Yöneticisi panonuza](#understand-the-compliance-manager-dashboard) ulaşırsınız.

Uyumluluk Yöneticisi'ne erişmek için doğrudan bağlantı şeklindedir [https://compliance.microsoft.com/compliancemanager](https://compliance.microsoft.com/compliancemanager).

## <a name="set-user-permissions-and-assign-roles"></a>Kullanıcı izinlerini ayarlama ve rolleri atama

Uyumluluk Yöneticisi rol tabanlı erişim denetimi (RBAC) izin modeli kullanır. Yalnızca rol atanmış kullanıcılar Uyumluluk Yöneticisi'ne erişebilir ve her kullanıcının izin verdiği eylemler [rol türüne](#role-types) göre kısıtlanır.

### <a name="where-to-set-permissions"></a>İzinlerin ayarlanacağı yer

Kuruluşunuz için genel yönetici rolüne sahip olan kişi, Uyumluluk Yöneticisi için kullanıcı izinleri ayarlayabilir. İzinler hem Microsoft Purview uyumluluk portalı hem de Azure Active Directory'de (Azure AD) ayarlanabilir.

> [!NOTE]
> ABD Kamu Topluluğu (GCC) Yüksek ve Savunma Bakanlığı (DoD) ortamlarındaki müşteriler, uyumluluk yöneticisi için yalnızca Azure AD kullanıcı izinlerini ve rollerini ayarlayabilir. Azure AD yönergeleri ve rol türü tanımları için aşağıya bakın.

Microsoft Purview uyumluluk portalı izinleri ayarlamak ve rolleri atamak için aşağıdaki adımları izleyin:

1. Microsoft Purview uyumluluk portalı gidin ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**İzinler'i**</a> seçin.

2. Uyumluluk portalı açılan listesinde **Roller'i** seçin.

3. Bir veya daha fazla kullanıcı eklemek istediğiniz rol grubunu bulun ve grup adının solundaki kutuyu işaretleyin. ( [Aşağıdaki rollerin ve ilgili işlevlerin listesine bakın](#role-types). Rol grubu adları rol adını taklit eden bir addır.)

4. Bu grubun açılır bölmesinde **Üyeler** üst bilgisi altında **Düzenle'yi** seçin.

5. **Üye seç'i** seçin. Başka bir açılır pencere görüntülenir.

6. Gruba eklenecek bir veya daha fazla kullanıcıyı seçmek için **+ Ekle'yi** seçin.

7. Eklemek istediğiniz adların yanındaki onay kutusunu seçin ve ardından alt kısımdaki **Ekle** düğmesini seçin.

8. Kullanıcıları atamayı bitirdiğinizde **Bitti'yi** ve ardından **Kaydet'i** ve ardından **Kapat'ı** seçin.

#### <a name="more-about-azure-ad"></a>Azure AD hakkında daha fazla bilgi

Azure AD rol atamak ve izinleri ayarlamak için bkz. [Azure Active Directory'ye sahip kullanıcılara yönetici ve yönetici olmayan roller atama](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).

Office 365 veya Microsoft 365 abonelikleri olmayan Azure AD kimlikli kullanıcılar Microsoft Purview uyumluluk portalı Uyumluluk Yöneticisi'ne erişemez. Uyumluluk Yöneticisi'ne erişim konusunda yardım almak için [cmresearch@microsoft.com](mailto:cmresearch@microsoft.com) başvurun.

### <a name="role-types"></a>Rol türleri

Aşağıdaki tabloda, Uyumluluk Yöneticisi'ndeki her rolün izin verdiği işlevler gösterilmektedir. Tabloda ayrıca her [Azure AD rolünün](/azure/active-directory/roles/permissions-reference) Uyumluluk Yöneticisi rolleriyle nasıl eşlenmiş olduğu da gösterilir. Kullanıcıların Uyumluluk Yöneticisi'ne erişmek için en azından Uyumluluk Yöneticisi okuyucu rolüne veya genel okuyucu rolüne Azure AD gerekir.

| Kullanıcı yapabilecekleri: | Uyumluluk Yöneticisi rolü | Azure AD rolü | 
| :------------- | :-------------: | :------------: |
| **Verileri okuma ama düzenlememe**| Uyumluluk Yöneticisi Okuyucusu  | Azure AD Genel okuyucu, Güvenlik okuyucusu |
| **Verileri düzenleme**| Uyumluluk Yöneticisi Katkısı | Uyumluluk Yöneticisi |
| **Test sonuçlarını düzenleme**| Uyumluluk Yöneticisi Değerlendiricisi | Uyumluluk Yöneticisi |
| **Değerlendirmeleri, şablon ve kiracı verilerini yönetme**| Uyumluluk Yöneticisi Yönetimi | Uyumluluk Yöneticisi, Uyumluluk Verileri Yöneticisi, Güvenlik Yöneticisi  |
| **Kullanıcıları atama**| Genel Yönetici | Genel Yönetici |

## <a name="start-a-premium-assessments-trial"></a>Premium değerlendirme denemesi başlatma

Uyumluluk Yöneticisi premium değerlendirme deneme sürümü, kuruluşunuza en uygun değerlendirmeleri hızla ayarlamanın harika bir yoludur. 300'den fazla şablondan oluşan kitaplığımız, dünyanın dört bir yanındaki kamu düzenlemelerine ve endüstri standartlarına karşılık gelmektedir.
[Premium değerlendirme deneme sürümü](compliance-easy-trials-compliance-manager-assessments.md) hakkında daha fazla bilgi edinin.

Deneme sürümünüzü doğrudan Uyumluluk Yöneticisi'nden başlatabilir ve aşağıdaki adımları izleyerek önerilen değerlendirmeleri ayarlayabilirsiniz:

1. Uyumluluk Yöneticisi'ne **Genel Bakış** sayfasında **Denemeyi başlat'ı** seçin. Kuruluşunuz için değerlendirmeleri önermemize yardımcı olacak sorular soran bir deneme etkinleştirme sihirbazı girersiniz.

2. **Deneme sürümünü etkinleştir** sayfasında **İleri'yi** seçerek ücretsiz 90 günlük premium değerlendirme denemenize başlayın ve değerlendirme oluşturmaya devam edin.

3. Kuruluşunuzu tanımlayan bir veya daha fazla sektör seçin ve ardından **İleri'yi** seçin.

4. Kuruluşunuzun konumu için bir veya daha fazla bölge seçin ve ardından **İleri'yi** seçin.

5. Değerlendirmeleri **seçin** ekranında, kuruluşunuz için geçerli olduğunu düşündüğümüz değerlendirmelerin listesini görmek için **Önerilen şablonlar'ın** yanındaki açılan oku seçin. Değerlendirme oluşturmak için kullanmak istediğiniz şablonların yanındaki kutuları işaretleyin ve **İleri'yi** seçin.

6. Yeni değerlendirmelerinizi oluşturmak için son seçimlerinizi gözden geçirin ve **Önerilen Değerlendirmeler Ekle'yi** seçin.

Aşağıdaki [Değerlendirmeler sayfası](#assessments-page) bölümünü ziyaret ederek değerlendirmeleri kullanmaya başlama hakkında daha fazla bilgi edinin.

## <a name="settings-for-automated-testing-and-user-history"></a>Otomatik test ve kullanıcı geçmişi ayarları

Microsoft Purview uyumluluk portalı'deki Uyumluluk Yöneticisi ayarları, iyileştirme eylemlerinin otomatik testini etkinleştirmenize ve devre dışı bırakmanıza olanak tanır. Bu ayarlar, iyileştirme eylemleriyle ilişkilendirilmiş kullanıcıların verilerini yönetmenize de olanak tanır ve iyileştirme eylemlerini farklı bir kullanıcıya yeniden atayabilirsiniz.  Uyumluluk Yöneticisi ayarlarına yalnızca genel yönetici veya Uyumluluk Yöneticisi Yöneticisi rolüne sahip kişiler erişebilir.

> [!NOTE]
> Otomatikleştirilmiş test özelliği, GCC High ve DoD ortamlarındaki müşteriler tarafından kullanılamaz çünkü Bu ortamlarda Güvenli Puan kullanılamaz. GCC High ve DoD müşterilerinin iyileştirme eylemlerini el ile uygulaması ve test etmeleri gerekir.

### <a name="set-up-automated-testing"></a>Otomatik testi ayarlama

Uyumluluk Yöneticisi, veri yaşam döngüsü yönetimi, bilgi koruması, Microsoft Purview Veri Kaybı Önleme, iletişim uyumluluğu ve insider risk yönetimi dahil olmak üzere kuruluşunuzun abone olabileceği diğer Microsoft Purview çözümlerinden gelen sinyalleri algılar. Uyumluluk Yöneticisi ayrıca [Microsoft Güvenli Puanı](../security/defender/microsoft-secure-score.md) tarafından izlenen tamamlayıcı iyileştirme eylemlerinden gelen sinyalleri de algılar.

Uyumluluk Yöneticisi bu sinyalleri kullanarak sizin için belirli iyileştirme eylemlerini otomatik olarak test edebilir ve bu da uyumluluk etkinliklerinizde verimliliği en üst düzeye çıkarmanıza yardımcı olur. İyileştirme eylemi başarıyla test edildiğinde ve uygulandığında, [genel uyumluluk puanınıza alacak](compliance-score-calculation.md#how-compliance-manager-continuously-assesses-controls) olan puan miktarının tamamını alırsınız.

**Otomatik test, Uyumluluk Yöneticisi'ne yeni yeni eklenen kuruluşlar için varsayılan olarak açıktır.** Microsoft 365 veya Office 365 ilk dağıttığınızda, verilerin tam olarak toplanması ve uyumluluk puanınıza dahil olması yaklaşık yedi gün sürer. Otomatikleştirilmiş test açıldığında eylemin test tarihi güncelleştirilmez, ancak test durumu güncelleştirilir. Yeni değerlendirmeler oluşturulduğunda puanlar otomatik olarak Microsoft denetim puanlarını ve Güvenli Puan tümleştirmesini içerir. Bu ayarı düzenlemek veya kapatmak için aşağıdaki [Otomatik test ayarlarını yönetme](#manage-automated-testing-settings) bölümüne bakın.

#### <a name="how-to-tell-which-actions-are-tested-automatically"></a>Hangi eylemlerin otomatik olarak test olduğunu nasıl anlarız?

**İyileştirme eylemleri** sayfanızda **Test kaynağı** sütununu bulun. Değer **Otomatik** olarak listeleniyorsa, eylem Uyumluluk Yöneticisi tarafından otomatik olarak test edilir.  Değer **El ile** ise, eylem kuruluşunuz tarafından test edilir. Değer **Parent** ise, eylem bağlı olduğu başka bir eylemin test durumunu devralır. [İyileştirme eylem testi kaynağı](compliance-manager-improvement-actions.md#update-testing-source) hakkındaki ayrıntıları alın.

#### <a name="which-actions-cant-be-tested-automatically"></a>Hangi eylemler otomatik olarak test edilemiyor?

Microsoft 365 kapsamında olmayan şablonlardaki iyileştirme eylemleri şu anda otomatik test için uygun değildir. Örneğin, evrensel şablonlar veya Microsoft Azure veya Microsoft Dynamics için bir şablon otomatik olarak test edilebilecek eylemlere sahip olmaz. [Değerlendirme şablonları](compliance-manager-templates.md) hakkında daha fazla bilgi edinin.

#### <a name="manage-automated-testing-settings"></a>Otomatik test ayarlarını yönetme

Kuruluşunuzun genel yöneticisi, otomatik test ayarlarını istediği zaman değiştirebilir. Yaygın iyileştirme eylemleri için otomatik testi kapatabilir veya tek tek eylemler için etkinleştirebilirsiniz. Otomatik test ayarlarınızı değiştirmek için aşağıdaki yönergeleri izleyin.

1. Microsoft Purview uyumluluk portalı <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ayarlar'ı**</a> seçin.

2. Ayarlar sayfasında **Uyumluluk Yöneticisi'ni** seçin.

3. Sol gezinti bölmesinden **Test kaynağı'nı** seçin.

4. Tüm iyileştirme eylemleri için otomatik testi açmak, tüm eylemler için kapatmak veya tek tek eylemlere göre açmak için uygun düğmeyi seçin.

5. **İyileştirme eylemi başına aç'ı** seçerseniz, aralarından seçim yapabileceğiniz tüm iyileştirme eylemleri bir listeyle gösterilir.  Otomatik olarak test etmek istediğiniz herhangi bir eylemin yanındaki kutuyu işaretleyin.

6. Ayarlarınızı kaydetmek için **Kaydet'i** seçin. Ekranınızın üst kısmında seçiminizin kaydedildiğini belirten bir onay iletisi alırsınız. Hata bildirimi alırsanız yeniden deneyin.

> [!NOTE]
> Tüm eylemler için otomatik güncelleştirmeleri yalnızca genel yönetici açabilir veya kapatabilir. Uyumluluk Yöneticisi Yöneticisi tek tek eylemler için otomatik güncelleştirmeleri açabilir, ancak genel olarak tüm eylemler için etkinleştiremez.

### <a name="manage-user-history"></a>Kullanıcı geçmişini yönetme

**Kullanıcı geçmişini yönet** ayarları, Uyumluluk Yöneticisi'nde hangi kullanıcıların iyileştirme eylemleriyle çalıştığını hızla belirlemenize yardımcı olur. İyileştirme eylemleriyle ilişkili tanımlanabilir kullanıcı verileri, yapılan tüm uygulama ve test çalışmalarını, karşıya yükledikleri belgeleri ve girdikleri notları içerir. Bu tür verileri anlamak ve almak, kuruluşunuzun kendi uyumluluk gereksinimleri için gerekli olabilir.

Kullanıcı geçmişi ayarları, tüm iyileştirme eylemlerini bir kullanıcıdan diğerine yeniden atamanıza da olanak tanır.

**Kullanıcı geçmişi ayarlarını bulmak için:**

1. Microsoft Purview uyumluluk portalı <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ayarlar'ı**</a> seçin.

2. Ayarlar sayfasında **Uyumluluk Yöneticisi'ni** seçin.

3. Sol gezinti **bölmesinden Kullanıcı geçmişini yönet'i** seçin.

**Kullanıcı geçmişini yönet** sayfasında, bir iyileştirme eylemine atanan e-posta adresine göre tüm kullanıcıların listesi gösterilir. E-posta adresini yazarak belirli bir kullanıcıyı hızla bulmak için **Ara** düğmesini kullanın.

Her kullanıcının e-posta adresinin sağındaki **Seç** açılan menüsünde raporu dışarı aktarma, iyileştirme eylemlerini yeniden atama veya geçmişi silme seçenekleri sağlanır. Her seçenekle ilgili ayrıntılar için aşağıdaki her bölüme bakın.

#### <a name="export-a-report-of-user-history-data"></a>Kullanıcı geçmişi verilerinin raporunu dışarı aktarma

Şu anda kullanıcıya atanmış iyileştirme eylemlerinin listesini içeren bir Excel dosyasını dışarı aktarabilirsiniz.  Raporda ayrıca bu kullanıcı tarafından karşıya yüklenen tüm kanıt dosyaları listelenir. Bu bilgiler, açık geliştirme eylemlerini yeniden atamanıza yardımcı olabilir.

Rapor, geliştirme eyleminin oluşturma tarihi itibariyle durumunu yansıtır. Durumu veya ataması ile ilgili önceki tüm değişikliklerin geçmiş raporu değildir ( [geliştirme eylemleri sayfanızdan bir raporu dışarı aktarmayı](compliance-manager-improvement-actions.md#export-a-report) öğrenin).

**Bir raporu kullanıcıya göre dışarı aktarmak için aşağıdaki adımları izleyin:**

1. Microsoft Purview uyumluluk portalı <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ayarlar'ı**</a> seçin.

2. Ayarlar sayfasında **Uyumluluk Yöneticisi'ni** seçin.

3. Sol taraftaki gezinti **bölmesinden Kullanıcı geçmişini yönet'i** seçin.

4. Liste e-posta adreslerini arayarak veya **Ara'yı** seçip kullanıcının e-posta adresini girerek hedeflenen kullanıcıyı bulun.

5. **Seç** açılan menüsünde **Raporu dışarı aktar'ı** seçin.

6. Raporunuzun Excel dosyası oluşturulduktan sonra dosyayı açabilir ve yerel makinenize kaydedebilirsiniz.

#### <a name="reassign-improvement-actions-to-another-user"></a>Geliştirme eylemlerini başka bir kullanıcıya yeniden atama

Geliştirme eylemlerini bir kullanıcıdan diğerine yeniden atayabilirsiniz. Bir eylemi yeniden atadığınızda, belge yükleme geçmişi değişmez, ancak belgeleri ilk karşıya yükleyen kullanıcının adı artık geliştirme eyleminde görünmez.

**Geliştirme eylemlerini başka bir kullanıcıya yeniden atamak için aşağıdaki adımları izleyin:**

1. Microsoft Purview uyumluluk portalı <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ayarlar'ı**</a> seçin.

2. Ayarlar sayfasında **Uyumluluk Yöneticisi'ni** seçin.

3. Sol taraftaki gezinti **bölmesinden Kullanıcı geçmişini yönet'i** seçin.

4. Liste e-posta adreslerini arayarak veya **Ara'yı** seçip kullanıcının e-posta adresini girerek bir kullanıcıyı bulun.

5. **Seç** açılan menüsünde **İyileştirme eylemlerini yeniden ata'yı** seçin. **İyileştirme eylemlerini yeniden ata** açılır bölmesi görüntülenir.

6. **Kullanıcı ara** alanına, *geliştirme eylemlerini* atamak istediğiniz kullanıcının adını veya e-posta adresini girin.

7. **Geliştirme eylemlerinin atanacağı** yer altında hedeflenen kullanıcınızın adını gördüğünüzde kullanıcıyı ve ardından **Eylem ata'yı** seçin.

8. Yeniden atama tamamlandığında, açılır bölmede önceki kullanıcının tüm iyileştirme eylemlerinin yeni kullanıcıya yeniden atandığını onaylayan bir onay iletisi görürsünüz. Yeniden atama hatası bildirimi alırsanız pencereyi kapatın ve yeniden deneyin. Açılır pencere bölmesini kapatmak için **Bitti'yi** seçin.

Yeni atanan, bir iyileştirme eylemine atandığını belirten bir e-posta alır. E-posta, iyileştirme eyleminin ayrıntılar sayfasına doğrudan bir bağlantı içerir.

 > [!NOTE]
> Bekleyen bir güncelleştirmeyi içeren bir eylemi yeniden atadığınızda, güncelleştirme yeniden atandıktan sonra kabul edilirse, yeniden atama e-postasında eylemin doğrudan bağlantısı kesilecektir. Güncelleştirme kabul edildikten sonra eylemi kullanıcıya yeniden atayarak bunu düzeltebilirsiniz. [İyileştirme eylemlerine yönelik güncelleştirmeler](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions) hakkında daha fazla bilgi edinin.

#### <a name="delete-user-history"></a>Kullanıcı geçmişini silme

Kullanıcının geçmişi silindiğinde, geliştirme eylemlerinin sahibi olarak kaldırılır ve kullanıcının adı Uyumluluk Yöneticisi'ndeki diğer tüm alanlardan kaldırılır. Kullanıcının geçmişini sildiğinizde, sahip oldukları geliştirme eylemleri yeni bir kullanıcı **atanana kadar Atanan** değerini görüntülemez. İyileştirme eylemine yüklenen tüm belgeler, silinen kullanıcının adının yerine **Kullanıcı kaldırıldı** ifadesini gösterir. Kullanıcı geçmişinin silinmesi kalıcıdır.

Kullanıcının geçmişini silmek için aşağıdaki adımları izleyin:

1. Microsoft Purview uyumluluk portalı <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ayarlar'ı**</a> seçin.

2. Ayarlar sayfasında **Uyumluluk Yöneticisi'ni** seçin.

3. Sol taraftaki gezinti **bölmesinden Kullanıcı geçmişini yönet'i** seçin.

4. Liste e-posta adreslerini arayarak veya **Ara'yı** seçip kullanıcının e-posta adresini girerek bir kullanıcıyı bulun.

5. **Seç** açılan menüsünde **Geçmişi sil'i** seçin.

6. Kullanıcı geçmişinin kalıcı olarak silinmesini onaylamanızı isteyen bir pencere görüntülenir. Silme işlemine devam etmek için **Geçmişi sil'i** seçin. Geçmişi silmeden gitmek için **İptal'i** seçin.

7. **Kullanıcı geçmişini yönet** sayfasına geri dönersiniz ve en üstte kullanıcı geçmişinin silindiğini belirten bir onay iletisi görürsünüz.

## <a name="understand-the-compliance-manager-dashboard"></a>Uyumluluk Yöneticisi panosunu anlama

Uyumluluk Yöneticisi panosu, geçerli uyumluluk duruşunuzun bir bakışta görünümünü sağlayacak şekilde tasarlanmıştır.

:::image type="content" alt-text="Uyumluluk Yöneticisi - pano." source="../media/compliance-manager-dashboard.png" lightbox="../media/compliance-manager-dashboard.png":::

### <a name="overall-compliance-score"></a>Genel uyumluluk puanı

Uyumluluk puanınız en üstte öne çıkıyor. Önemli veri koruma standartlarını ve düzenlemelerini ele alan iyileştirme eylemlerini tamamlamak için ulaşılabilir noktaları temel alan bir yüzde gösterir. [Microsoft'umu yönetilen Microsoft eylemlerinden](compliance-manager-assessments.md#microsoft-actions-tab) alınan puanlar da uyumluluk puanınıza göre sayılır.

Uyumluluk Yöneticisi'ne ilk kez geldiğinizde, ilk puanınız [Microsoft 365 veri koruma temelini temel](compliance-manager-assessments.md#data-protection-baseline-default-assessment) alır. Tüm kuruluşların kullanımına sunulan bu temel değerlendirme, ortak endüstri düzenlemelerini ve standartlarını içeren bir dizi denetimdir. Uyumluluk Yöneticisi mevcut Microsoft 365 çözümlerinizi tarar ve geçerli gizlilik ve güvenlik ayarlarınıza göre size bir ilk değerlendirme sağlar. Kuruluşunuzla ilgili değerlendirmeler eklediğinizde puanınız sizin için daha anlamlı hale gelir.

**Daha fazla bilgi edinin:** [Uyumluluk puanınızın nasıl hesaplanmış olduğunu anlama](compliance-score-calculation.md).

### <a name="key-improvement-actions"></a>Önemli iyileştirme eylemleri

Bu bölümde, genel uyumluluk puanınız üzerinde en büyük olumlu etkiyi sağlamak için şu anda gerçekleştirebileceğiniz en iyi iyileştirme eylemleri listelenir. İyileştirme eylemleri sayfanıza gitmek için **Tüm iyileştirme eylemlerini görüntüle'yi** seçin.

### <a name="solutions-that-affect-your-score"></a>Puanınızı etkileyen çözümler

Bu bölümde puanınızı olumlu yönde etkileyebilecek iyileştirme eylemleri içeren çözümler ve bu çözümlerdeki bekleyen iyileştirme eylemlerinin sayısı vurgulanmaktadır. Çözümler sayfanızı ziyaret etmek için **Tüm çözümleri görüntüle'yi** seçin.

### <a name="compliance-score-breakdown"></a>Uyumluluk puanı dökümü

Bu bölüm, puanınızı iki farklı yolla daha ayrıntılı bir şekilde görüntülemenizi sağlar:

- **Kategoriler**: "bilgileri koruma" veya "cihazları yönetme" gibi veri koruma kategorilerinde toplam puanınızın yüzdesini gösterir.
- **Değerlendirmeler**: GDPR veya NIST 800-53 gibi belirli uyumluluk ve veri koruma standartları, düzenlemeleri veya yasaları için değerlendirmeleri yönetmedeki ilerlemenizin yüzdesini gösterir.

### <a name="filtering-your-dashboard-view"></a>Pano görünümünüzü filtreleme

Pano görünümünüzü yalnızca belirli düzenleme ve standartlara, çözümlere, eylem türüne, değerlendirme gruplarına veya veri koruma kategorilerine ilişkin öğeleri görmek için filtreleyebilirsiniz. Görünümünüzü bu şekilde filtrelemek de panonuzdaki puanı filtreleyerek, filtre ölçütlerinize göre toplam olası puandan kaç puan elde ettiğinizi gösterir.

Filtreleri uygulamak için:

1. Panonun sağ üst tarafında **Filtre'yi** seçin.
2. **Filtreler** açılır bölmesinden filtre ölçütlerinizi seçin ve ardından **Uygula'yı** seçin.

Filtre uyguladıktan sonra puanınızın gerçek zamanlı olarak ayarlı olduğunu görürsünüz. Uyumluluk puanı yüzdesi ve döküm bilgileri ile iyileştirme eylemleri ve çözümleri artık yalnızca filtre ölçütlerinizin kapsadığı verilerle ilgili. Uyumluluk Yöneticisi oturumunu kapattığınızda, yeniden oturum açtığınızda filtrelenmiş görünümünüz kalır.

Filtreleri kaldırmak için:

- Uyumluluk puanınızın üzerindeki **Uygulanan filtreler** başlığında, kaldırmak istediğiniz tek tek filtrenin yanındaki **X** işaretini seçin; Veya
- Panonuzun sağ üst tarafında **Filtre'yi** seçin, ardından **Filtreler** açılır bölmesinde **Filtreleri temizle'yi** seçin.

## <a name="improvement-actions-page"></a>İyileştirme eylemleri sayfası

[İyileştirme eylemleri](compliance-manager-improvement-actions.md) , kuruluşunuz tarafından yönetilen eylemlerdir. İyileştirme eylemleriyle çalışmak, uyumluluk etkinliklerinizi merkezi hale getirmenize ve veri koruma düzenlemeleri ve standartlarıyla uyumlu hale getirmenize yardımcı olur. Her geliştirme eylemi, ayrıntılı uygulama kılavuzu ve sizi uygun çözüme başlatmaya yönelik bir bağlantı sağlar. Uygulama ve test çalışmalarını gerçekleştirmek için kuruluşunuzdaki kullanıcılara iyileştirme eylemleri atanabilir. Ayrıca belgeleri, notları ve kayıt durumu güncelleştirmelerini iyileştirme eylemi içinde depolayabilirsiniz.

### <a name="view-your-improvement-actions"></a>Geliştirme eylemlerinizi görüntüleme

Uyumluluk Yöneticisi panosu, önemli iyileştirme eylemlerinizi gösterir. Tüm iyileştirme eylemlerinizi görüntülemek için, panonuzda **geliştirme eylemleri** sekmesini seçin; bu da sizi iyileştirme eylemleri sayfanıza getirir. Ayrıca **, iyileştirme eylemleri** sayfanıza ulaşmak için panonuzdaki önemli iyileştirme eylemleri listesinin altındaki Tüm iyileştirme eylemlerini görüntüle'yi de seçebilirsiniz.

İyileştirme eylemleri sayfası, kuruluşunuz tarafından yönetilen tüm iyileştirme eylemlerini gösterir. Microsoft tarafından yönetilen eylemler her değerlendirmede görüntülenebilir ( [Microsoft eylemleri](compliance-manager-assessments.md#microsoft-actions-tab) hakkında daha fazla bilgi edinin).

İyileştirme eylemleri sayfanızda eylemlerin uzun bir listesi varsa, görünümünüzü filtrelemek yararlı olabilir. Eylemler listesinin sağ üst köşesindeki **Filtre'yi** seçin. **Filtreler** açılır penceresi görüntülendiğinde, kullanılabilir seçenekler arasından ölçütlerinizi seçin. Sağ üst köşedeki **Gruplandır'ı** seçerek de görünümünüzü özelleştirebilirsiniz. Açılan menüden gruba, çözüme, kategoriye, eylem türüne veya duruma göre görüntülemek için öğesini seçin.

Bu sayfanın varsayılan görünümü, test durumu **Başarılı** olan iyileştirme eylemlerini göstermez. Testi geçen eylemleri görüntülemek için Filtreler açılır **bölmesindeki Geçirildi** kutusunu işaretleyin. Yalnızca puanınıza doğru test durumu **Başarılı** sayısı olan eylemler. Bazı eylemler **bekleyen bir güncelleştirme etiketi gösterebilir.** [İyileştirme eylemlerine yönelik güncelleştirmeler](compliance-manager-improvement-actions.md#accepting-updates-to-improvement-actions) hakkında daha fazla bilgi edinin.

İyileştirme eylemleri sayfası, her iyileştirme eylemi için aşağıdaki veri noktalarını gösterir:

- **Ürünler**: Değerlendirilen ürün.
- **Elde edilen puanlar**: Eylemi tamamlayarak toplamdan elde edilen puan sayısı
- **Düzenlemeler**: eylemle ilgili düzenlemeler veya standartlar
- **Grup**: Eylemi atadığınız grup
- **Çözümler**: Eylemi gerçekleştirmek için gidebileceğiniz çözüm
- **Değerlendirmeler**: eylemi içeren değerlendirmeler
- **Kategoriler**: ilgili veri koruma kategorisi (bilgileri koruma, cihazları yönetme vb.)
- **Test durumu**:
  - **Hiçbiri** – hiçbir durum güncelleştirmesi kaydedilmedi
  - **Değerlendirilmedi** - test başlatılmadı
  - **Başarılı** - uygulama başarıyla test edildi
  - **Başarısız düşük risk** - test başarısız, düşük riskli
  - **Başarısız orta risk** - test başarısız, orta riskli
  - **Başarısız yüksek risk** - test başarısız, yüksek risk
  - **Kapsam dışında** – eylem değerlendirme kapsamında değildir ve puanınızı etkilemez
  - **Algılanacak -** el ile test için, bir eylemin uygulandığını ancak test edilmediğini gösterir; otomatikleştirilmiş test için, bir eylemin otomasyon sonucunu beklediğini gösterir
  - **Algılanamadı** - otomatik durum belirlenemiyor
  - **Kısmen test edilmiş** – kısmi puan veren otomatik puanlama
- **Eylem türü**: geliştirme eyleminin teknik olup olmadığını gösterir; yani bir çözüm veya ürün içinde veya teknik olmayan bir çözüm dışında uygulanabilir
- **Atandığı** kişi: Bu eylemin atandığı kişi (varsa)
- **Test kaynağı**: Eylemin test kaynağının el ile mi, otomatik mi yoksa üst öğeden mi devralındığını gösterir

**Daha fazla bilgi edinin:** [Geliştirme eylemleri atama ve üzerinde çalışma gerçekleştirme hakkında bilgi edinin](compliance-manager-improvement-actions.md).

## <a name="solutions-page"></a>Çözümler sayfası

Çözümler sayfasında, kazanılan puanların ve olası puanların çözümüne göre düzenlenmiş olarak payı gösterilir. Kalan noktalarınızı ve iyileştirme eylemlerini bu görünümden görüntülemek, hangi çözümlerin daha acil bir şekilde ilgilenilmesi gerektiğini anlamanıza yardımcı olur.

Uyumluluk Yöneticisi panonuzda **Çözümler** sekmesini seçerek çözümler sayfasını bulun. Ayrıca, panonuzun sağ üst kısmındaki **Puanınızı etkileyen Çözümler'in** altında **Tüm çözümleri görüntüle'yi** de seçebilirsiniz.

### <a name="filtering-your-solutions-view"></a>Çözüm görünümünüzü filtreleme

Çözüm görünümünüzü filtrelemek için:

1. Değerlendirme listenizin sol üst köşesindeki **Filtre'yi** seçin.
2. **Filtreler** açılır penceresinde, istenen ölçütlerin (düzenlemeler, çözümler, eylem türleri, gruplar, kategoriler) yanına bir denetim yerleştirin.
3. **Uygula** düğmesini seçin. Filtre bölmesi kapatılır ve filtrelenmiş görünümünüzü görürsünüz.

Değerlendirme listenizin üst kısmındaki **Grup** açılan menüsünden gruplandırma türünü seçerek değerlendirmeleri gruba, ürüne veya düzenlemeye göre görmek için görünümünüzü de değiştirebilirsiniz.

### <a name="taking-action-from-the-solution-page"></a>Çözüm sayfasından eylem gerçekleştirme

Çözümler sayfasında, kuruluşunuzun iyileştirme eylemlerine bağlı çözümleri görüntülenir. Tabloda her çözümün genel puanınıza katkıları, bu çözüm içinde elde edilen ve mümkün olan puanlar ve bu çözümde gruplandırılmış kalan ve puanınızı artırabilecek geliştirme eylemleri listelenir.

Bu ekrandan işlem yapmanın iki yolu vardır:

1. Hedeflenen çözümünüzün satırındaki **Kalan eylemler** sütununun altında köprülenmiş sayıyı seçin. Bu çözüm için test edilmemiş iyileştirme eylemlerini gösteren iyileştirme eylemleri ekranının filtrelenmiş bir görünümünü görürsünüz.

2. Hedeflenen çözümünüzün satırındaki **Çözümü aç** sütununun altında **Aç'ı** seçin. Çözümü veya konumu Microsoft 365'te ve önerilen eylemi gerçekleştirebileceğiniz Office 365 güvenlik ve uyumluluk merkezlerinde görürsünüz.

## <a name="assessments-page"></a>Değerlendirmeler sayfası

Değerlendirmeler sayfasında, kuruluşunuz için ayarladığınız tüm [değerlendirmeler](compliance-manager-assessments.md) listelenir. Uyumluluk puanı paydanız, izlenen tüm değerlendirmeleriniz tarafından belirlenir. Daha fazla değerlendirme ekledikçe, geliştirme eylemleri sayfanızda daha fazla geliştirme eyleminin listelendiğini ve uyumluluk puanı paydanızın arttığını görürsünüz.

Sayfanın üst kısmındaki **etkinleştirilmiş şablonlar** sayacı, kuruluşunuzun kullanabileceği toplam şablon sayısının dışında kullanılmakta olan etkin değerlendirme şablonlarının sayısını gösterir. Daha fazla bilgi için bkz. [Şablon kullanılabilirliği ve lisanslama](compliance-manager-templates.md#template-availability-and-licensing) .

Değerlendirmeler sayfası, her değerlendirmeyle ilgili önemli bilgileri özetler:

- **Değerlendirme**: Değerlendirmenin adı
- **Durum**:
  - **Tamamlandı** - tüm denetimlerin durumu "geçti" veya en az bir denetim geçirilir ve geri kalanı "kapsam dışı" olur
  - **Tamamlanmadı** – en az bir denetimin durumu "başarısız"
  - **Hiçbiri** - tüm denetimler test edilmedi
  - **Devam ediyor** - geliştirme eylemlerinin "devam ediyor", "kısmi kredi" veya "algılanmamış" dahil olmak üzere başka bir durumu vardır
- **Değerlendirme ilerleme durumu**: Başarıyla test edilen denetimlerin sayısıyla ölçüldükçe tamamlanmaya doğru yapılan işin yüzdesi
- **Geliştirme eylemleriniz**: Denetimlerinizin uygulanmasını sağlamak için tamamlanan eylemlerin sayısı
- **Microsoft eylemleri**: Microsoft denetimlerinin uygulanmasını karşılamak için tamamlanan eylemlerin sayısı
- **Grup**: Değerlendirmenin ait olduğu grubun adı
- **Ürün**: Microsoft 365 gibi ilişkili ürün veya değerlendirme için tanımlanan başka bir ürün
- **Düzenleme**: Değerlendirme için geçerli olan mevzuat standardı, ilke veya yasa

### <a name="filtering-your-assessments-view"></a>Değerlendirmeler görünümünüzü filtreleme

Değerlendirme görünümünüzü filtrelemek için:

1. Değerlendirme listenizin sol üst köşesindeki **Filtre'yi** seçin.
2. **Filtreler** açılır bölmesinde istediğiniz ölçütleri denetleyin.
3. **Uygula** düğmesini seçin. Filtre bölmesi kapatılır ve filtrelenmiş görünümünüzü görürsünüz.

Değerlendirme listenizin üst kısmındaki **Grup** açılan menüsünden gruplandırma türünü seçerek değerlendirmeleri gruba, ürüne veya düzenlemeye göre görmek için görünümünüzü de değiştirebilirsiniz.

### <a name="default-assessment"></a>Varsayılan değerlendirme

Varsayılan olarak, değerlendirmeler sayfasında [Veri Koruma Temeli](compliance-manager-assessments.md#data-protection-baseline-default-assessment) değerlendirmesini görürsünüz. Uyumluluk Yöneticisi ayrıca değerlendirme oluşturmak için önceden oluşturulmuş birkaç [şablon](compliance-manager-templates-list.md) sağlar.

## <a name="assessment-templates-page"></a>Değerlendirme şablonları sayfası

Şablon, Uyumluluk Yöneticisi'nde değerlendirme oluşturmaya yönelik bir çerçevedir. Değerlendirme şablonları sayfasında şablonların ve önemli ayrıntıların listesi görüntülenir. Liste, Uyumluluk Yöneticisi tarafından sağlanan şablonların yanı sıra kuruluşunuzun değiştirdiği veya oluşturduğu şablonları içerir. Sertifikasyon, ürün kapsamı, ülke, sektör ve şablonu oluşturan kişiyi temel alan bir şablon bulmak için filtreler uygulayabilirsiniz.

Sayfanın üst kısmındaki **etkinleştirilmiş şablonlar** sayacı, kuruluşunuzun kullanabileceği toplam şablon sayısının dışında kullanılmakta olan etkin değerlendirme şablonlarının sayısını gösterir. Daha fazla bilgi için bkz. [Şablon kullanılabilirliği ve lisanslama](compliance-manager-templates.md#template-availability-and-licensing) .

Şablonun açıklamasını ve sertifikasyon, kapsam ve denetim ayrıntıları hakkında daha fazla bilgi içeren ayrıntılar sayfasını açmak için satırından bir şablon seçin. Bu sayfadan değerlendirme oluşturmak, şablon verilerini Excel'e aktarmak veya şablonu değiştirmek için uygun düğmeleri seçebilirsiniz.

**Daha fazla bilgi edinin:** [Değerlendirme şablonlarıyla çalışma hakkında bilgi edinin](compliance-manager-templates.md).

## <a name="next-step"></a>Sonraki adım

[Değerlendirmeleri ayarlayarak](compliance-manager-assessments.md) Uyumluluk Yöneticisi'nin özelleştirin.
