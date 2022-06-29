---
title: Cihaz koruma ilkelerini görüntüleme veya düzenleme
description: Microsoft 365 İş Ekstra'da cihaz koruma ilkelerini görüntüleme, düzenleme, oluşturma ve silme
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: d628df3109eafd3d342041784d70b9857e260d81
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66486043"
---
# <a name="view-and-edit-device-protection-policies"></a>Cihaz koruma ilkelerini görüntüleme ve düzenleme

Microsoft 365 İş Ekstra'de, yönetilen cihazlar için güvenlik ayarları Microsoft Defender'ın güvenlik merkezinde veya Yönetici merkezinde cihaz koruma ilkeleri aracılığıyla yapılandırılır. Kurulumu ve yapılandırmayı basitleştirmeye yardımcı olmak için, kuruluşunuzun cihazlarının eklenir eklenmez korunmasına yardımcı olan önceden yapılandırılmış ilkeler vardır. Varsayılan ilkeleri kullanabilir, mevcut ilkeleri düzenleyebilir veya kendi ilkelerinizi oluşturabilirsiniz.

**Bu kılavuzda aşağıdakilerin nasıl yapılacağını açıklar**:

- Varsayılan ilkelerinize genel bakış elde edin
- Defender güvenlik merkezinde, Yönetici merkezinde ve Intune cihaz ilkeleriyle çalışın.

## <a name="about-the-default-device-protection-policies"></a>Varsayılan cihaz koruma ilkeleri hakkında

Microsoft 365 İş Ekstra, kuruluşunuzun cihazlarını korumak için iki ana ilke türü içerir:

- Microsoft Defender Virüsten Koruma ve diğer tehdit koruması özelliklerinin nasıl yapılandırıldığını belirleyen **yeni nesil koruma ilkeleri**.

- Kuruluşunuzun cihazlarına hangi ağ trafiğinin akışına izin verileceğini belirleyen **güvenlik duvarı ilkeleri**.

Bu ilkeler, Microsoft 365 İş Ekstra aboneliğinize dahil edilen İş için Microsoft Defender bir parçasıdır. Microsoft Defender güvenlik merkezindeki ilkelerle çalışmanın yanı sıra Yönetici merkezi ve Intune ilkelerle çalışma hakkında bilgi sağlanır.

## <a name="working-with-device-polices-in-the-microsoft-defender-security-center"></a>Microsoft Defender güvenlik merkezinde cihaz ilkeleriyle çalışma

Güvenlik merkezinde ilkelerinizle çalışma konusunda aşağıdaki ayrıntılar geçerlidir.

### <a name="view-existing-device-protection-policies"></a>Mevcut cihaz koruma ilkelerini görüntüleme

Güvenlik merkezinde mevcut cihaz koruma ilkelerinizi görüntülemek için:

1. Microsoft 365 Defender portalına ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın.

1. Gezinti bölmesinde **Cihaz yapılandırması'nı** seçin. İlkeler işletim sistemine ( **Windows istemcisi** gibi) ve ilke türüne ( **yeni nesil koruma** ve **Güvenlik Duvarı** gibi) göre düzenlenir.

    :::image type="content" source="../media/mdb-deviceconfiguration.png" lightbox="../media/mdb-deviceconfiguration.png" alt-text="Cihaz yapılandırma sayfası.":::

1. bir işletim sistemi sekmesi (örneğin, **Windows istemcileri**) seçin ve ardından **Yeni nesil koruma** ve **Güvenlik Duvarı** kategorileri altındaki ilke listesini gözden geçirin.

1. İlke hakkında daha fazla ayrıntı görüntülemek için adını seçin. İlkeyle korunan cihazlar gibi bu ilke hakkında daha fazla bilgi sağlayan bir yan bölme açılır.

   :::image type="content" source="../media/mdb-deviceconfig-selectedpolicy.png" lightbox="../media/mdb-deviceconfig-selectedpolicy.png" alt-text="Cihaz yapılandırması sayfasında seçilen ilkenin ekran görüntüsü..":::

### <a name="edit-an-existing-device-protection-policy"></a>Mevcut cihaz koruma ilkesini düzenleme

Cihaz ilkesini düzenlemek için:

1. Microsoft 365 Defender portalına ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın.

1. Gezinti bölmesinde **Cihaz yapılandırması'nı** seçin. İlkeler işletim sistemine ( **Windows istemcisi** gibi) ve ilke türüne ( **yeni nesil koruma** ve **Güvenlik Duvarı** gibi) göre düzenlenir.

1. bir işletim sistemi sekmesi (örneğin, **Windows istemcileri**) seçin ve ardından **Yeni nesil koruma** ve **Güvenlik Duvarı** kategorileri altındaki ilke listesini gözden geçirin.

1. İlkeyi düzenlemek için, ilkenin adını ve ardından **Düzenle'yi** seçin.

1. **Genel bilgiler** sekmesinde bilgileri gözden geçirin. Gerekirse açıklamayı düzenleyebilirsiniz. Ardından **İleri'yi** seçin.

1. **Cihaz grupları** sekmesinde, hangi cihaz gruplarının bu ilkeyi alması gerektiğini belirleyin.  

   - Seçili cihaz grubunu olduğu gibi tutmak için **İleri'yi** seçin.
   - İlkeden bir cihaz grubunu kaldırmak için **Kaldır'ı** seçin.
   - Yeni bir cihaz grubu ayarlamak için **Yeni grup oluştur'u** seçin ve ardından cihaz grubunuzu ayarlayın. (Bu görevle ilgili yardım almak için bkz[. Microsoft 365 İş Ekstra cihaz grupları](m365bp-device-groups-mdb.md).)
   - İlkeyi başka bir cihaz grubuna uygulamak için **Var olan grubu kullan'ı** seçin.

   İlkeyi hangi cihaz gruplarının alacağını belirttikten sonra **İleri'yi** seçin.

1. **Yapılandırma ayarları** sekmesinde ayarları gözden geçirin. Gerekirse, ilkenizin ayarlarını düzenleyebilirsiniz. Bu görevle ilgili yardım almak için aşağıdaki makalelere bakın: 

   - [Yeni nesil yapılandırma ayarlarını anlama](../security/defender-business/mdb-next-gen-configuration-settings.md)   
   - [Güvenlik duvarı ayarları](../security/defender-business/mdb-firewall.md)

   Yeni nesil koruma ayarlarınızı belirttikten sonra **İleri'yi** seçin.

1. **İlkenizi gözden geçirin** sekmesinde genel bilgileri, hedeflenen cihazları ve yapılandırma ayarlarını gözden geçirin.

   - **Düzenle'yi** seçerek gerekli değişiklikleri yapın.
   - Devam etmeye hazır olduğunuzda **İlkeyi güncelleştir'i** seçin.

### <a name="create-a-new-device-protection-policy"></a>Yeni cihaz koruma ilkesi oluşturma

Yeni bir cihaz koruma ilkesi oluşturmak için:

1. Microsoft 365 Defender portalına ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın.

1. Gezinti bölmesinde **Cihaz yapılandırması'nı** seçin. İlkeler işletim sistemine ( **Windows istemcisi** gibi) ve ilke türüne ( **yeni nesil koruma** ve **Güvenlik Duvarı** gibi) göre düzenlenir.

1. bir işletim sistemi sekmesi (örneğin, **Windows istemcileri**) seçin ve **ardından Yeni nesil koruma** ilkeleri listesini gözden geçirin.

1. **Yeni nesil koruma** veya **Güvenlik Duvarı** altında **+ Ekle'yi** seçin.

1. **Genel bilgiler** sekmesinde aşağıdaki adımları izleyin:

   1. Bir ad ve açıklama belirtin. Bu bilgiler, sizin ve ekibinizin ilkeyi daha sonra tanımlamanıza yardımcı olur.
   2. İlke sırasını gözden geçirin ve gerekirse düzenleyin. (Daha fazla bilgi için bkz. [İlke sırası](../security/defender-business/mdb-policy-order.md).)
   3. **İleri**'yi seçin.

1. **Cihaz grupları** sekmesinde yeni bir cihaz grubu oluşturun veya mevcut bir grubu kullanın. İlkeler cihazlara cihaz grupları aracılığıyla atanır. Aklınızda bulundurmak istediğiniz bazı şeyler şunlardır:

   - Başlangıçta, yalnızca kuruluşunuzdaki kişilerin kuruluş verilerine ve e-postasına erişmek için kullandığı cihazları içeren varsayılan cihaz grubunuz olabilir. Varsayılan cihaz grubunuzu tutabilir ve kullanabilirsiniz.
   - Varsayılan ilkeden farklı olan belirli ayarlara sahip bir ilke uygulamak için yeni bir cihaz grubu oluşturun.
   - Cihaz grubunuzu ayarlarken işletim sistemi sürümü gibi belirli ölçütleri belirtirsiniz. Ölçütleri karşılayan cihazlar, siz hariç tutmadığınız sürece bu cihaz grubuna dahil edilir.
   - Tanımladığınız varsayılan ve özel cihaz grupları dahil olmak üzere tüm cihaz grupları Azure Active Directory'de (Azure AD) depolanır.

   Cihaz grupları hakkında daha fazla bilgi edinmek için bkz. [İş için Microsoft Defender'da cihaz grupları](../security/defender-business/mdb-create-edit-device-groups.md).

1. **Yapılandırma ayarları** sekmesinde ilkenizin ayarlarını belirtin ve ardından **İleri'yi** seçin. Tek tek ayarlar hakkında daha fazla bilgi için bkz. [İş için Microsoft Defender'de yeni nesil yapılandırma ayarlarını anlama](../security/defender-business/mdb-next-gen-configuration-settings.md).

1. **İlkenizi gözden geçirin** sekmesinde genel bilgileri, hedeflenen cihazları ve yapılandırma ayarlarını gözden geçirin.

   - **Düzenle'yi** seçerek gerekli değişiklikleri yapın.
   - Devam etmeye hazır olduğunuzda **İlke oluştur'u** seçin.

## <a name="using-device-policies-in-the-admin-center"></a>Yönetici merkezinde cihaz ilkelerini kullanma

Aşağıdaki bilgiler, Microsoft Business Premium Yönetici merkezinde ilkeleri görüntülemeyi ve yönetmeyi açıklar.

### <a name="working-with-device-policies"></a>Cihaz ilkeleriyle çalışma

Yönetici merkezinde ilkelerle çalışmak için:

1.  Şuradan yönetim merkezine gidin: <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.

1. Sol gezinti bölmesinde **Cihaz** \> **İlkeleri'ni** seçin.

    Bu sayfada, hedef grubu oluşturabilir, düzenleyebilir, değiştirebilir veya bir ilkeyi silebilirsiniz.

    ![İlkeler sayfasının ekran görüntüsü.](../media/devicepolicies.png)
  
### <a name="view-and-manage-devices"></a>İlkeleri ve cihazları görüntüleme

İlkeleri görüntülemek ve yönetmek için:

1. Sol gezinti bölmesinde **Cihazlar** \> **Yönet'i** seçin.

    Bu sayfada, bir veya daha fazla cihaz seçebilir ve şirket verilerini kaldırabilirsiniz. Cihaz koruma ayarlarını yaptığınız Windows 10 cihazlar için, cihazı fabrika ayarlarına sıfırlamayı da seçebilirsiniz.
  
   ![Cihazları yönet sayfası.](../media/devicesmanage.png)

## <a name="working-with-device-policies-in-intune"></a>Intune'da cihaz ilkeleriyle çalışma

Microsoft Endpoint Manager yönetim merkezinde Uç nokta güvenliği aracılığıyla yapılan Intune cihaz ilkeleri oluşturmak ve yönetmek için aşağıdaki bilgileri kullanın.

### <a name="create-duplicate-and-edit-policies"></a>İlke oluşturma, yineleme ve düzenleme

Intune'de ilke oluşturmak için

1. Microsoft Endpoint Manager yönetim merkezinde oturum açın.

1. **Uç nokta güvenliği'ni** ve yapılandırmak istediğiniz ilke türünü ve ardından **İlke Oluştur'u** seçin.

1. Aşağıdaki ilke türlerinden birini seçin:

    - Antivirus
    - Disk şifrelemesi
    - Güvenlik duvarı
    - Uç nokta algılama ve yanıt
    - Saldırı yüzeyini azaltma
    - Hesap koruması
    - Aşağıdaki özellikleri girin:

1. Platform: İlkeyi oluşturmakta olduğunuz platformu seçin. Kullanılabilir seçenekler, seçtiğiniz ilke türüne bağlıdır.

1. Profil: Seçtiğiniz platform için kullanılabilir profiller arasından seçim yapın. Profiller hakkında bilgi için seçtiğiniz ilke türü için bu makaledeki ayrılmış bölüme bakın.

1. **Oluştur**’u seçin.

1. Temel Bilgiler sayfasında, profil için bir ad ve açıklama girin, ardından **İleri**'yi seçin.

1. Yapılandırma ayarları sayfasında, her bir ayar grubunu genişletin ve bu profille yönetmek istediğiniz ayarları yapılandırın.

1. Ayarları yapılandırmayı bitirdiğinizde **İleri'yi** seçin.

1. Kapsam etiketleri sayfasında **Kapsam etiketlerini seç'i** seçerek **etiket seç** bölmesini açarak profile kapsam etiketleri atayın.

1. Devam etmek için **İleri'yi** seçin.

1. **Atamalar** sayfasında, bu profili alacak grupları seçin. Profil atama hakkında daha fazla bilgi için bkz. Kullanıcı ve cihaz profilleri atama.

1. **İleri**'yi seçin.

1. Gözden Geçir + oluştur sayfasında, işiniz bittiğinde, **Oluştur**'u seçin. Oluşturduğunuz profil için ilke türünü seçtiğinizde yeni profil listede görüntülenir.

Intune bir ilkeyi yinelemek için:

1. Microsoft Endpoint Manager yönetim merkezinde oturum açın.

1. Kopyalamak istediğiniz ilkeyi seçin. Ardından **Çoğalt'ı** seçin veya ilkenin sağ tarafındaki üç noktayı **(...)** ve **Çoğalt'ı** seçin.
1. İlke için yeni bir ad girin ve **Kaydet'i** seçin.

İlkeyi düzenlemek için:

1. Yeni ilkeyi ve ardından **Özellikler'i** seçin.

1. İlkedeki yapılandırma ayarlarının listesini genişletmek için **Ayarlar'ı** seçin. Bu görünümden ayarları değiştiremezsiniz, ancak bunların nasıl yapılandırıldığını gözden geçirebilirsiniz.

1. İlkeyi değiştirmek için, değişiklik yapmak istediğiniz her kategori için **Düzenle'yi** seçin:

    - Temel
    - Atama
    - Kapsam etiketleri
    - Yapılandırma ayarları

1. Değişiklikleri yaptıktan sonra, düzenlemelerinizi kaydetmek için **Kaydet'i** seçin. Ek kategorilere düzenleme eklemeden önce bir kategoride yapılan düzenlemelerin kaydedilmesi gerekir.

## <a name="manage-conflicts"></a>Çakışmaları yönetme

Uç nokta güvenlik ilkeleriyle yönetebileceğiniz cihaz ayarlarının çoğu, Intune'daki diğer ilke türleri aracılığıyla da kullanılabilir. Bu diğer ilke türleri cihaz yapılandırma ilkelerini ve güvenlik temellerini içerir. Ayarlar birkaç farklı ilke türü aracılığıyla veya aynı ilke türünün birden çok örneği tarafından yönetilebildiğinden, beklediğiniz yapılandırmalara uymayen cihazlar için ilke çakışmalarını belirlemeye ve çözmeye hazır olun.

Güvenlik temelleri, bir ayarın temel adresleyen önerilen yapılandırmayla uyumlu olması için varsayılan olmayan bir değer ayarlayabilir.

Uç nokta güvenlik ilkeleri de dahil olmak üzere diğer ilke türleri varsayılan olarak Yapılandırılmadı değerini ayarlar. Bu diğer ilke türleri, ilkedeki ayarları açıkça yapılandırmanızı gerektirir.

İlke yönteminden bağımsız olarak, aynı cihazdaki aynı ayarı birden çok ilke türü aracılığıyla veya aynı ilke türünün birden çok örneği aracılığıyla yönetmek, kaçınılması gereken çakışmalara neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft Intune'da uç nokta güvenliğini yönetme](/mem/Intune/protect/endpoint-security)

[İş için Microsoft 365 planlarının güvenliğini sağlamaya yönelik en iyi yöntemler](../admin/security-and-compliance/secure-your-business-data.md)

## <a name="next-objective"></a>Sonraki hedef

[Cihaz gruplarını ayarlama ve yönetme](m365bp-device-groups-mdb.md).