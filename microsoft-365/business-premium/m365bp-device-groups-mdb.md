---
title: Microsoft 365 İş Ekstra'da cihaz gruplarıyla çalışma
description: Cihaz grupları ve Microsoft 365 İş Ekstra Intune ile ilkeler uygulama ve siber saldırılara karşı korumayı artırma hakkında bilgi edinin.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: a8d132669319e26adea53498e7dcf78a82a3250d
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489736"
---
# <a name="device-groups-and-categories-in-microsoft-365-business-premium"></a>Microsoft 365 İş Ekstra cihaz grupları ve kategorileri

Microsoft 365 İş Ekstra, İş için Microsoft Defender ve Microsoft Intune aracılığıyla uç nokta korumasını içerir. Cihaz koruma ilkeleri, cihaz grupları olarak adlandırılan belirli koleksiyonlar aracılığıyla cihazlara uygulanır. Intune cihazlarda, cihazları düzenlemenin farklı bir yolu olarak cihaz kategorileri halinde gruplandırılır. 

Bu makale aşağıdaki bölümleri içerir:  

- [Cihaz gruplarıyla çalışma](#working-with-device-groups)
- [Yeni cihaz grubu oluşturma](#create-a-device-group-in-the-microsoft-365-defender-portal)
- [Intune'de yeni bir cihaz kategorisi oluşturma](#create-a-device-category-in-intune)

## <a name="working-with-device-groups"></a>Cihaz gruplarıyla çalışma

Cihaz grubu, işletim sistemi sürümü gibi belirli ölçütler nedeniyle birlikte gruplandırılmış bir cihaz koleksiyonudur. Ölçütleri karşılayan cihazlar, siz hariç tutmadığınız sürece bu cihaz grubuna dahil edilir.

Microsoft 365 İş Ekstra ile kullanabileceğiniz varsayılan cihaz gruplarınız vardır. Varsayılan cihaz grupları, İş için Defender'a eklenen tüm cihazları içerir. Ancak, belirli cihazlara belirli ayarlarla cihaz koruma ilkeleri atamak için yeni cihaz grupları da oluşturabilirsiniz.

Varsayılan cihaz gruplarınız ve tanımladığınız tüm özel cihaz grupları dahil olmak üzere tüm cihaz grupları [Azure Active Directory'de](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD) depolanır.

## <a name="create-a-device-group-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında cihaz grubu oluşturma

Cihaz koruma ilkesi oluşturma veya düzenleme sürecindeyken yeni bir cihaz grubu oluşturabilirsiniz.

1. [Microsoft 365 Defender portalına](https://security.microsoft.com) gidin ve oturum açın.

2. Gezinti bölmesinde **Cihaz yapılandırması'nı** seçin.

3. Aşağıdaki eylemlerden birini gerçekleştirin:

    1. Var olan bir ilkeyi seçin ve ardından **Düzenle'yi** seçin.

    2. Yeni bir ilke oluşturmak için **+ Ekle'yi** seçin.

    > [!TIP]
    > İlke oluşturma veya düzenleme konusunda yardım almak için bkz. [İş için Microsoft Defender'da ilkeleri görüntüleme veya düzenleme](m365bp-view-edit-create-mdb-policies.md).

4. **Genel bilgiler** adımında bilgileri gözden geçirin, gerekirse düzenleyin ve ardından **İleri'yi** seçin.

5. **Yeni grup oluştur'u** seçin.

6. Cihaz grubu için bir ad ve açıklama belirtin ve ardından **İleri'yi** seçin.

7. Gruba eklenecek cihazları seçin ve ardından **Grup oluştur'u** seçin.

8. **Cihaz grupları** adımında, ilke için cihaz gruplarının listesini gözden geçirin. Gerekirse, listeden bir grubu kaldırın. Ardından **İleri'yi** seçin.

9. **Yapılandırma ayarları** sayfasında, ayarları gerektiği gibi gözden geçirin ve düzenleyin ve **ardından İleri'yi** seçin. Bu ayarlar hakkında daha fazla bilgi için bkz. [İş için Microsoft Defender'deki yeni nesil yapılandırma ayarlarını anlama](../security/defender-business/mdb-next-gen-configuration-settings.md).

10. **İlkenizi gözden geçirin** adımında tüm ayarları gözden geçirin, gerekli düzenlemeleri yapın ve ardından **İlke oluştur veya İlkeyi** **güncelleştir'i** seçin.

## <a name="create-a-device-category-in-intune"></a>Intune'da cihaz kategorisi oluşturma

Intune kullanıcıların cihaz kaydederken seçmesi gereken cihaz kategorileri oluşturun.

1. [Microsoft Endpoint Manager yönetim merkezinde](https://endpoint.microsoft.com) oturum açın.

2. Yeni bir kategori eklemek için **Cihazlar** > **Cihaz kategorileri** > **Cihaz kategorisi oluştur'u** seçin.

3. **Cihaz kategorisi oluştur** bölmesinde, yeni kategori için bir ad ve isteğe bağlı bir açıklama girin.

4. İşiniz bittiğinde **Oluştur'u** seçin. Listede yeni kategoriyi görebilirsiniz.

Azure Active Directory (Azure AD) güvenlik gruplarını oluştururken cihaz kategorisi adını kullanın. Kullanıcılar cihazlarını kaydettiklerinde, Intune'de yapılandırdığınız kategorilerin bir listesi sunulur. Bir kategori seçtikten ve kaydı tamamladıktan sonra, cihazları kendisiyle ilişkilendirilmiş Active Directory güvenlik grubuna eklenir.

## <a name="create-dynamic-device-groups-in-azure-active-directory"></a>Azure Active Directory'de dinamik cihaz grupları oluşturma

Azure Active Directory (Azure AD) portalına ([https://portal.azure.com](https://portal.azure.com)) Microsoft 365 yönetim merkezi da girebilirsiniz. Microsoft 365 yönetim merkezi ()[https://admin.microsoft.com](https://admin.microsoft.com/) içinde **Tüm yönetim merkezleri'ni** ve ardından **Azure Active Directory'yi** seçin.

Azure AD portalında, cihaz kategorisine ve cihaz kategorisi adına göre dinamik gruplar oluşturabilirsiniz. Cihazları otomatik olarak eklemek ve kaldırmak için dinamik grup kurallarını kullanın. Bir cihazın öznitelikleri değişirse sistem, cihazın kural gereksinimlerini karşılayıp karşılamadığını (eklendiğini) veya artık kural gereksinimlerini karşılayıp karşılamadığını (kaldırıldığını) görmek için dizin için dinamik grup kurallarınıza bakar.

Cihazlar veya kullanıcılar için dinamik bir grup oluşturabilirsiniz, ancak her ikisi için oluşturamayın. Ayrıca, cihaz sahiplerinin özniteliklerini temel alan bir cihaz grubu oluşturamazsınız. Cihaz üyeliği kuralları yalnızca cihaz ilişkilendirmelerine başvurabilir. 

## <a name="after-device-groups-are-created"></a>Cihaz grupları oluşturulduktan sonra

Artık kategoriler ve cihaz grupları oluşturulduğuna göre, iOS ve Android cihaz kullanıcıları cihazlarını kaydeder ve bu şekilde yapılandırılan kategoriler listesinden bir kategori seçmeleri gerekir. Windows kullanıcıları kategori seçmek için Şirket Portalı web sitesini veya Şirket Portalı uygulamasını kullanabilir.

1. Cihazı kaydettikten sonra [şirket portalına](https://portal.microsoft.com) gidin ve **Cihazlarım'ı** seçin.

2. Listeden kayıtlı cihazı seçin ve ardından bir kategori seçin.

Kategori seçtikten sonra cihaz otomatik olarak ilgili gruba eklenir. Kategorileri yapılandırmadan önce bir cihaz zaten kaydedilmişse, kullanıcı Şirket Portalı web sitesinde cihaz hakkında bir bildirim görür. Bu, kullanıcının iOS/iPadOS veya Android'de Şirket Portalı uygulamasına bir sonraki erişişinde bir kategori seçmesini sağlar.

> [!NOTE]
> - Azure portal bir cihaz kategorisini düzenleyebilirsiniz, ancak bu kategoriye başvuran Azure AD güvenlik gruplarını el ile güncelleştirmeniz gerekir.
> - Bir kategoriyi silerseniz, bu kategoriye atanan cihazlar **Atanmamış** kategori adını görüntüler.

## <a name="view-the-categories-of-devices-that-you-manage"></a>Yönettiğiniz cihaz kategorilerini görüntüleme

1. [Microsoft Endpoint Manager yönetim merkezinde](https://endpoint.microsoft.com) oturum açın, **Cihazlar** > **Tüm cihazlar'ı** seçin.

2. Cihaz listesinde **Cihaz kategorisi** sütununu inceleyin.

3. Cihaz kategorisi sütunu gösterilmiyorsa **Sütunlar** > **Kategorisi** > **Uygula'yı** seçin.

## <a name="change-the-category-of-a-device"></a>Cihazın kategorisini değiştirme

1. [Microsoft Endpoint Manager yönetim merkezinde](https://endpoint.microsoft.com) oturum açın, **Cihazlar** > **Tüm cihazlar'ı** seçin. 

2. Özelliklerini görmek için listeden istediğiniz kategoriyi seçin.

## <a name="next-steps"></a>Sonraki adımlar

Birincil görevlerinizi tamamladığınıza göre [, yanıt ekiplerinizi](m365bp-security-incident-management.md) ayarlamak ve [ortamınızı korumak](m365bp-maintain-environment.md) için zaman ayırın.
