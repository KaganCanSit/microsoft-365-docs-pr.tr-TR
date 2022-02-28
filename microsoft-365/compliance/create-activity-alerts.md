---
title: Etkinlik uyarıları oluşturma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 11/7/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MED150
- BCS160
- MET150
ms.assetid: 72bbad69-035b-4d33-b8f4-549a2743e97d
ROBOTS: NOINDEX, NOFOLLOW
description: Etkinlik uyarılarını etkinlik uyarılarını Microsoft 365 uyumluluk merkezi ve yönetin; böylece Microsoft 365 kullanıcılar belirli etkinlikleri gerçekleştirecekken size e-posta bildirimleri gönderecek
ms.openlocfilehash: 593c51a9d85ebb6f687a5e8573df32d4de515e6b
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990010"
---
# <a name="create-activity-alerts"></a>Etkinlik uyarıları oluşturma

Kullanıcılar etkinlik etkinliklerini belirli bir etkinlik gerçekleştirecek olduğunda size e-posta bildirimi gönderecek bir etkinlik Office 365. Etkinlik uyarıları, denetim günlüğünde olayları aramaya benzer, ancak bunun dışında, etkinlikler için uyarı oluşturduğunuz bir etkinliğe e-posta iletisi gönderebilirsiniz.

 **Denetim günlüğünde arama yapmak yerine neden etkinlik uyarıları kullanılır?** Gerçekten bilmek istediğiniz belirli kullanıcılar tarafından gerçekleştirilen belirli türde etkinlik veya etkinlikler olabilir. Bu etkinlikler için denetim günlüğünde arama yapmak zorunda kalmadan, kullanıcılar bu etkinlikleri gerçekleştirecekken size bir e Microsoft 365-posta iletisi göndermesi için etkinlik uyarılarını kullanabilirsiniz. Örneğin, bir kullanıcı SharePoint'ta dosyaları s olduğunda size bildirmek için bir etkinlik uyarısı oluşturabilir veya kullanıcı posta kutusundan iletileri kalıcı olarak s olduğunda size bildirim göndermek için bir uyarı oluşturabilirsiniz. Size gönderilen e-posta bildirimi, hangi etkinliğin gerçekleştirilmesiyle ilgili bilgileri ve bunu gerçekleştiren kullanıcıyı içerir.

> [!NOTE]
> Etkinlik uyarıları kullanım dışı ediliyor. Yeni etkinlik uyarıları oluşturmak yerine güvenlik ve uyumluluk merkezinde uyarı ilkelerini kullanmaya başlamayı öneririz. Uyarı ilkeleri, herhangi bir kullanıcı belirtilen etkinliği gerçekleştirirken uyarıyı tetikleyen ve güvenlik ve uyumluluk merkezi'nin Uyarıları görüntüle sayfasında uyarılar görüntüleyen bir uyarı ilkesi oluşturabilme gibi ek işlevler  sağlar. Daha fazla bilgi için bkz [. Uyarı ilkeleri](alert-policies.md).

## <a name="confirm-roles-and-configure-audit-logging"></a>Rolleri onaylama ve denetim günlüğünü yapılandırma

- Etkinlik uyarılarını yönetmek için kuruluşta kuruluş Microsoft 365 uyumluluk merkezi rolüne atanmış olmak gerekir. Varsayılan olarak, bu rol Uyumluluk Yöneticisi ve Kuruluş Yönetimi rol gruplarına atanır. Rol gruplarına üye ekleme hakkında daha fazla bilgi için bkz. [Kullanıcılara erişim izni Microsoft 365 uyumluluk merkezi](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).

- Etkinlik uyarılarını kullanmaya başlay önce sizin (veya başka bir yöneticinin) kuruluş denetim günlüğünü açması gerekir. Bunu yapmak için, Etkinlik **uyarıları sayfasında Kullanıcı ve yönetici etkinliğini** kaydetmeyi **başlat'a tıklamanız** gerekir. (Bu bağlantıyı görmüyorsanız, denetimin kuruluşu için zaten açık olduğudur.) Ayrıca denetimi, Denetim günlüğü araması **sayfasındaki Denetim günlüğü Microsoft 365 uyumluluk merkezi** **açabilirsiniz** (Denetim'e gidin). Bunu organizasyonunız için tek bir kez yapmak zorundasiniz.

- Denetim günlüğünde arayarak gerçekleştirebilir ve aynı etkinlikler için uyarılar oluşturabilirsiniz. Uyarıları [oluşturabilirsiniz](#more-information) sık kullanılan senaryoların (ve izlenir belirli etkinliklerin) listesi için Daha fazla bilgi bölümüne bakın.

- Yalnızca kuruluşun adres **defterine** <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">listelenmiş</a> kullanıcılar tarafından gerçekleştirilen etkinlikler için uyarı oluşturmak üzere Microsoft 365 uyumluluk merkezi'daki Etkinlik uyarıları sayfasını kullanabilirsiniz. Bu sayfayı, adres defteri içinde listelenmiyor olan dış kullanıcılar tarafından gerçekleştirilen etkinliklere yönelik uyarılar oluşturmak için kullana sıralanmaz.

## <a name="create-an-activity-alert"></a>Etkinlik uyarısı oluşturma

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Devam'a Microsoft 365 uyumluluk merkezi</a>.

2. İş veya okul hesabınızla oturum açın.

3. Etkinlik uyarıları **sayfasında Simge** ekle'ye ![tıklayın.](../media/8ee52980-254b-440b-99a2-18d068de62d3.gif) **Yeni'ye.**

   Etkinlik uyarısı oluşturmak için görüntülenen uçarak giriş sayfası görüntülenir.


    ![Etkinlik uyarısı oluşturma.](../media/53888bd5-9fa2-4398-8ccc-1a9dc72517ac.png)

4. Etkinlik uyarısı oluşturmak için aşağıdaki alanları doldurun:

    1. **Ad** - Uyarı için bir ad yazın. Uyarı adları, kurum içinde benzersiz olmalıdır.

    1. **Açıklama** (İsteğe bağlı) - etkinlikler ve takip edilen kullanıcılar ve e-posta bildirimlerinin gönderildiği kullanıcılar gibi uyarıyı açık olun. Açıklamalar, uyarının amacını diğer yöneticilere açıklamak için hızlı ve kolay bir yol sağlar.

    1. **Uyarı türü** - Özel seçeneğinin **seçili** olduğundan emin olun.

    1. **Şu durumda bu uyarıyı** gönder - **Şu iki alanı yapılandırıldığında bu** uyarıyı gönder'e tıklayın:

       - **Etkinlikler** - Uyarı oluşturabilirsiniz etkinlikleri görüntülemek için açılan listeye tıklayın. Bu, denetim günlüğünde arama yapınca görüntülenen etkinlikler listesiyle aynıdır. Belirli bir veya birden çok etkinliği seçerek veya etkinlik grubu adına tıklar ve gruptaki tüm etkinlikleri seçin. Bu etkinliklerin açıklaması için, Denetim günlüğünde arama yapın bölümündeki "Denetlenen etkinlikler" [bölümüne bakın](search-the-audit-log-in-security-and-compliance.md#audited-activities). Kullanıcı uyarıya ekley istediğiniz etkinlikleri gerçekleştir olduğunda, bir e-posta bildirimi gönderilir.

       - **Kullanıcılar** - Bu kutuya tıklayın ve bir veya birden çok kullanıcı seçin. Bu kutuda yer alan kullanıcılar, Etkinlikler kutusuna ekleytilen **etkinlikleri gerçekleştirecekse** , bir uyarı gönderilir. Kuruluşlardan  herhangi bir kullanıcı uyarı tarafından belirtilen etkinlikleri gerçekleştirsinse uyarı göndermek için Kullanıcılar kutusunu boş bırakın.

    1. Bu uyarıyı **gönder - Bu** uyarıyı gönder'e **tıklayın ve ardından** Alıcılar  kutusuna tıklayın ve kullanıcı (Kullanıcılar kutusunda belirtilen) bir etkinlik gerçekleştir olduğunda (Etkinlikler kutusunda belirtilen) e-posta bildirimi alacak  kullanıcıları eklemek için bir ad yazın. Varsayılan olarak alıcılar listesine eklendiysiniz. Bu listeden adınız kaldırabilirsiniz.

5. **Uyarıyı oluşturmak** için Kaydet'e tıklayın.

    Yeni uyarı, Etkinlik uyarıları **sayfasındaki listede** görüntülenir.

    ![Etkinlik uyarıları sayfasında bir uyarı listesi görüntülenir.](../media/02b774f2-1719-41de-bbc9-5e5b7576f335.png)

    Uyarının durumu, On olarak **ayarlanır**. Uyarı gönder geldiğinde e-posta bildirimi alacak alıcıların da listelenmiş olduğunu unutmayın.

## <a name="turn-off-an-activity-alert"></a>Etkinlik uyarılarını kapatma

Etkinlik uyarılarını, e-posta bildirimi gönderilmey için kapatabilirsiniz. Etkinlik uyarısını kapattıktan sonra, bu uyarı yine de kurum için etkinlik uyarıları listesinde görüntülenir ve bu uyarının özelliklerini yine görüntüebilirsiniz.

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Devam'a Microsoft 365 uyumluluk merkezi</a>.

2. İş veya okul hesabınızla oturum açın.

3. Organizasyonunız için etkinlik uyarıları listesinde, kapatmak istediğiniz uyarıya tıklayın.

4. Uyarıyı **düzenle sayfasında** , durumu Kapalı **olarak değiştirmek için** Açık iki durumlu düğmesini tıklatın ve **ardından Kaydet'i** **tıklatın**.

    Etkinlik uyarıları sayfalarındaki **uyarının durumu** Kapalı olarak **ayarlanır**.

Etkinlik uyarılarını yeniden açmak için bu adımları yinele ve durumu Açık olarak değiştirmek  için Kapalı düğmesini **tıklatın**.

## <a name="more-information"></a>Daha fazla bilgi

- Aşağıda, bu uyarının gönderilmesi alanında (ve Etkinlik uyarıları sayfasındaki Alıcılar altında listelenmiş) belirtilen kullanıcılara gönderilen e-posta bildiriminin Microsoft 365 uyumluluk merkezi.

    ![Etkinlik uyarısı için gönderilen e-posta bildirimi örneği.](../media/a5f91611-fae6-4fe9-82f5-58521a2e2541.png)

- Burada, etkinlik uyarıları oluşturabilirsiniz bazı yaygın belge ve e-posta etkinlikleri ve yer almaktadır. Tablolarda etkinliği, uyarı oluşturulacak etkinliğin adı ve Etkinlikler açılan listesinde etkinliğin altında listelenmiş **etkinlik grubunun adı** gösterilir. Etkinlik uyarıları oluşturabilirsiniz etkinliklerin tam listesini görmek için Denetim günlüğünde arama yapın bölümündeki "Denetlenen etkinlikler" [bölümüne bakın](search-the-audit-log-in-security-and-compliance.md#audited-activities).

    > [!TIP]
    > Herhangi bir kullanıcı tarafından gerçekleştirilen tek bir etkinlik için etkinlik uyarısı oluşturmak iyi olabilir. Ya da bir veya birden çok kullanıcı tarafından gerçekleştirilen birden çok etkinliği takipen bir etkinlik uyarısı oluşturmak da istiyor da olabilir.

    Aşağıdaki tabloda, çalışma sayfalarındaki veya tablodaki belgeyle ilgili SharePoint sık OneDrive İş.

    | Bir kullanıcı bunu yaptığı zaman... | Bu etkinlik için uyarı oluşturma | Etkinlik grubu |
    |:-----|:-----|:-----|
    |Sitede bir belgeyi görüntüler.  |Dosyaya erişildi  |Dosya ve klasör etkinlikleri  |
    |Belgeyi düzenler veya değiştirir.  |Dosya değiştirildi  |Dosya ve klasör etkinlikleri  |
    |Bir belgeyi kuruluş dışındaki bir kullanıcıyla paylaştığında.  |Dosya, klasör veya site paylaşma  <br/> Ve  <br/> Paylaşım daveti oluşturuldu  <br/> Daha fazla bilgi için [bkz. Denetim günlüğünde paylaşım denetimini kullanma](use-sharing-auditing.md).  |Paylaşım ve erişim isteği etkinlikleri  |
    |Belgeyi karşıya yükler veya indirir.  |Dosya karşıya yüklendi  <br/> Ve/veya  <br/> İndirilen dosya  |Dosya ve klasör etkinlikleri  |
    |Siteye erişim izinlerini değiştirir.  |Site izinleri değiştirildi  |Site yönetimi etkinlikleri  |

    Aşağıdaki tabloda, e-postayla ilgili olarak sık kullanılan bazı etkinlikler Exchange Online.

    | Bir kullanıcı bunu yaptığı zaman... | Bu etkinlik için uyarı oluşturma | Etkinlik grubu |
    |:-----|:-----|:-----|
    |E-posta iletisi, posta kutusundan kalıcı olarak silinir (temiz gönderilir).  |İletiler posta kutusundan temizildi  | Exchange kutusu etkinliklerini geri alın  |
    |Paylaşılan posta kutusundan e-posta iletisi gönderir.  |İleti Farklı Gönder izinleri kullanılarak gönderildi  <br/> Ve  <br/> İleti Adına Gönder izinleri kullanılarak gönderildi  | Exchange kutusu etkinliklerini geri alın  |

- Etkinlik uyarıları oluşturmak ve düzenlemek için Güvenlik ve Uyumluluk Merkezi PowerShell'de **New-ActivityAlert** ve **Set-ActivityAlert** cmd & let'lerini de kullanabilirsiniz. Etkinlik uyarıları oluşturmak veya düzenlemek için bu cmdlet'leri kullanıyorsanız, aşağıdaki şeyleri unutmayın:

  - Etkinlikler açılan listesinde yer almayan bir uyarıya etkinlik eklemek için cmdlet kullanırsanız, uyarının özellik  sayfasında "Bu uyarının seçicide listelenmiyor özel işlemleri var" iletisi görüntülenir.

  - Etkinlik uyarısı oluşturmak veya düzenlemek için cmdlet'leri kullanmak için iyi bir neden, kuruluş dışından birine e-posta bildirimleri göndermektir. Bu dış kullanıcı uyarının alıcı listesinde listelenir. Ancak uyarıdan bu dış kullanıcıyı kaldırırsanız, Düzenleme uyarısı sayfası kullanılarak bu kullanıcı uyarıya yeniden **eklenemez** . **Set-ActivityAlert** cmdlet'ini kullanarak dış kullanıcıyı yeniden eklemeniz veya aynı (veya farklı) dış kullanıcıyı yeni uyarıya eklemek için **New-ActivityAlert** cmdlet'ini kullansanız da gerekir.
