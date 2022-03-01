---
title: Web Microsoft 365 uyumluluk merkezi
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.service: O365-seccomp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
description: Web sayfalarında izinleri yönetme hakkında Microsoft 365 uyumluluk merkezi.
ms.collection: M365-security-compliance
ms.custom:
- admindeeplinkCOMPLIANCE
- admindeeplinkEXCHANGE
ms.openlocfilehash: 45540713452b91da171f6fc52eef8210fa256c4e
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018816"
---
# <a name="permissions-in-the-microsoft-365-compliance-center"></a>Web Microsoft 365 uyumluluk merkezi

Son Microsoft 365 uyumluluk merkezi güncelleştirildi ve artık posta gruplarında uyumluluk görevleri gerçekleştiren kullanıcılar için doğrudan izinleri Microsoft 365. Bu güncelleştirme, uyumluluk çözümlerinin izinlerini yönetmek için artık Office 365 Güvenlik &'i kullanmak zorunda olmadığınız anlamına gelir. Microsoft 365 uyumluluk merkezi'daki  yeni İzinler sayfasını kullanarak cihaz yönetimi, veri kaybını önleme, eKbulma, insider risk yönetimi, bekletme gibi çeşitli özelliklerle kullanıcıların uyumluluk görevlerinin izinlerini yönetebilirsiniz. Kullanıcılar yalnızca onlara açıkça erişim izni vermekte olduğunuz uyumluluk görevlerini gerçekleştirebilir.

İzinler **sekmesini** görüntülemek için Microsoft 365 uyumluluk merkezi genel yönetici olması veya Rol Yönetimi rolüne atanmaları gerekir (bir rol yalnızca Kuruluş Yönetimi rol grubuna  atanır). Rol *Yönetimi rolü kullanıcıların* rol gruplarını görüntülemesini, oluşturmalarını ve değiştirmelerini sağlar.

![Sayfa içinde İzinler Microsoft 365 uyumluluk merkezi.](../media/m365-compliance-center-permissions.png)

Çalışma Microsoft 365 uyumluluk merkezi rol tabanlı erişim denetimi (RBAC) izin modeline dayalıdır. RBAC, çoğu Microsoft 365 hizmeti tarafından kullanılan izinler modelidir; dolayısıyla bu hizmetlerde izin yapısını iyi biliyorsanız, Microsoft 365 uyumluluk merkezi izni vermek size tanıdık gelecektir. tek tek her hizmette gereken tüm izinlerin Microsoft 365 uyumluluk merkezi, yönetimle ilgili olmadığını unutmayın. Yine de belirli hizmet için yönetim merkezinde hizmete özgü belirli izinleri yönetmeniz gerekir. Örneğin arşivleme, denetim ve MRM bekletme ilkeleri için izinler atamaniz gerekirse, bu izinleri yönetim merkezinden <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange gerekir</a>.

## <a name="relationship-of-members-roles-and-role-groups"></a>Üyelerin, rollerin ve rol gruplarının ilişkisi

Bir rol bir dizi görevi gerçekleştirme iznini, örneğin, Olay Yönetimi rolü kullanıcıların eBulma servis örnekleriyle çalışmasına olanak sağlar.

Rol grubu, kullanıcıların uyumluluk çözümleri genelinde işlerini en iyi şekilde yapmalarına olanak sağlayan bir Microsoft 365 uyumluluk merkezi. Örneğin, kullanıcıları *Insider Risk Yönetimi* rol grubuna ekleyerek, belirlenen yöneticiler, analistler, araştırmacılar ve denetçiler tek bir grupta gerekli insider risk yönetimi izinleri için yapılandırılır. Varsayılan Microsoft 365 uyumluluk merkezi, kişi atamanız gereken her uyumluluk çözümü için görevler ve işlevler için varsayılan rol gruplarını içerir. Genel olarak, gerektiğinde tek tek kullanıcıları varsayılan uyumluluk rol gruplarına üye olarak eklemenizi öneririz.

![Rol gruplarıyla roller ve üyeler arasındaki ilişkiyi gösteren diyagram.](../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png)

## <a name="permissions-needed-to-use-features-in-the-microsoft-365-compliance-center"></a>Dosyanın özellikleri kullanmak için gereken Microsoft 365 uyumluluk merkezi

Microsoft 365 uyumluluk merkezi'da bulunan tüm varsayılan rol gruplarını ve varsayılan olarak rol gruplarına atanan rolleri görüntülemek için, Güvenlik ve Uyumluluk Merkezi'nde & [bakın](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center).

site içinde izinleri Microsoft 365 uyumluluk merkezi yalnızca kullanıcılara site içinde bulunan uyumluluk özelliklerine erişim Microsoft 365 uyumluluk merkezi. Posta akış kuralları (aktarım kuralları olarak da bilinir) gibi Microsoft 365 uyumluluk merkezi dışında başka özelliklere izin vermek Exchange, yönetim merkezini <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange gerekir</a>.

## <a name="azure-roles-in-the-microsoft-365-compliance-center"></a>Microsoft 365 uyumluluk merkezi'de Azure rolleri

İzinler sayfasının **Azure AD** >  **Yerlerinde** yer alan roller Microsoft 365 uyumluluk merkezi **,** Azure Active Directory vardır. Bu roller, bir kişiye işini yapmak için gereken tüm izinleri vermenizi kolaylaştıran, kuruluşun IT grubunda bulunan iş işlevleriyle uyumlu olacak şekilde tasarlanmıştır. Bir Yönetici rolü seçerek ve rol paneli ayrıntılarını görüntüerek, şu anda her role atanmış olan kullanıcıları görüntüleyebilirsiniz. Bir Azure AD rolünün üyelerini yönetmek için, Azure AD'de üyeleri yönet'i seçin. Bu seçenek sizi Azure yönetim portalına yönlendirmektedir.

|Rol|Açıklama|
|:---|:----------|
|**Genel yönetici**|Tüm hizmetlerde, tüm yönetim Microsoft 365 erişim. Yalnızca genel yöneticiler diğer yönetici rollerini atayır. Daha fazla bilgi için bkz [. Genel Yönetici / Şirket Yöneticisi](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**Uyumluluk veri yöneticisi**|Tüm dünya genelinde verilerinizi takip edin, Microsoft 365 korunmasına yardımcı olun ve riskleri azaltmak için tüm sorunlar hakkında içgörüler elde edin. Daha fazla bilgi için bkz. [Uyumluluk Veri Yöneticisi](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**Uyumluluk yöneticisi**|Tüm yasal düzenleme gereksinimleriyle uyumlu kalmalarına, eBulma olaylarını yönetmelerine ve farklı konumlarda Microsoft 365, kimliklerde ve uygulamalarda veri yönetimi ilkelerini korumalarına yardımcı olun. Daha fazla bilgi için bkz. [Uyumluluk Yöneticisi](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**Güvenlik operatörü**|Kullanıcılarınızı, cihazlarınızı ve içeriğinizi görüntüleme, araştırma ve Microsoft 365 tehditlere yanıt verme. Daha fazla bilgi için bkz. [Güvenlik İşleci](/azure/active-directory/roles/permissions-reference#security-operator).|
|**Güvenlik gözetmeni**|Kullanıcılarınıza, cihazlarınıza ve Microsoft 365 yönelik etkin tehditleri  görüntüp araştırabilirsiniz, ancak (Güvenlik işlecinin aksine) herhangi bir işlem gerçekleştirerek bu izinleri olmaz. Daha fazla bilgi için bkz. [Güvenlik Okuyucu](/azure/active-directory/roles/permissions-reference#security-reader).|
|**Güvenlik yöneticisi**|Güvenlik ilkelerini yöneterek, Microsoft 365 ürünlerinde güvenlik analizini ve raporlarını gözden geçirerek ve tehdit ortamında hızlendirerek, kuruluş genel güvenliğini kontrol edin. Daha fazla bilgi için bkz. [Güvenlik Yöneticisi](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**Genel okuyucu**|Genel yönetici rolünün salt **okunur sürümü** . Tüm ayarları ve yönetim bilgilerini tüm Microsoft 365. Daha fazla bilgi için bkz. [Genel Okuyucu](/azure/active-directory/roles/permissions-reference#global-reader).|
|**Saldırı benzetimi yöneticisi**|Saldırı benzetimi oluşturma, benzetim başlatma/zamanlama ve benzetim sonuçlarının gözden geçirmesi gibi her yönüyle oluşturun ve yönetin. Daha fazla bilgi için bkz [. Saldırı Benzetimi Yöneticisi](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).|
|**Saldırı yükü yazarı**|Saldırı yüklemeleri oluşturun ancak aslında bunları başlatamaz veya zamanlamayın. Daha fazla bilgi için bkz [. Saldırı Yük Yazarı](/azure/active-directory/roles/permissions-reference#attack-payload-author).|
|

## <a name="add-users-to-a-compliance-role-group"></a>Uyumluluk rolü grubuna kullanıcı ekleme

Kullanıcıları uyumluluk rol grubuna eklemek için aşağıdaki adımları tamamlayın:

1. Microsoft 365 kuruluşunda yönetici hesabının kimlik bilgilerini kullanarak e-postanın izin alanında oturum açın ve Microsoft 365'ta uyumluluk rollerini görüntülemek ve yönetmek için bağlantıyı <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank"></a> seçmek için İzinler'e Microsoft 365. Microsoft 365 uyumluluk merkezi
1. Uyumluluk merkezi **bölümünü genişletin ve** Roller'i **seçin**.
1. Uyumluluk **merkezi rolleri sayfasında** , kullanıcıları eklemek istediğiniz uyumluluk rol grubunu seçin ve sonra da ayrıntılar bölmesinde Rol **grubunu düzenle'yi** seçin.
1. Sol **gezinti bölmesinde Üye** seç'i, ardından Düzenle'yi **seçin**.
1. **Ekle'yi** seçin ve ardından rol grubuna eklemek istediğiniz tüm kullanıcıların onay kutusunu seçin.
1. **Ekle'yi** ve ardından **Bitti'yi seçin**.
1. Kullanıcıları **rol** grubuna eklemek için Kaydet'i seçin. Adımları **tamamlamak** için Kapat'ı seçin.

## <a name="remove-users-from-a-compliance-role-group"></a>Kullanıcıları uyumluluk rol grubundan kaldırma

Kullanıcıları uyumluluk rol grubundan kaldırmak için aşağıdaki adımları tamamlayın:

1. Microsoft 365 kuruluşunda yönetici hesabının kimlik bilgilerini kullanarak e-postanın izin alanında oturum açın ve Microsoft 365'ta uyumluluk rollerini görüntülemek ve yönetmek için bağlantıyı <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank"></a> seçmek için İzinler'e Microsoft 365. Microsoft 365 uyumluluk merkezi
1. Uyumluluk merkezi bölümünü genişletin ve Roller'i **seçin**.
1. Uyumluluk **merkezi rolleri sayfasında** , kullanıcıları kaldırmak istediğiniz uyumluluk rol grubunu seçin ve sonra da ayrıntılar bölmesinde Rol **grubunu düzenle'yi** seçin.
1. Sol **gezinti bölmesinde Üye** seç'i, ardından Düzenle'yi **seçin**.
1. **Kaldır'ı** seçin ve ardından rol grubundan kaldırmak istediğiniz tüm kullanıcıların onay kutusunu seçin.
1. **Kaldır'ı** ve ardından **Bitti'yi seçin**.
1. Kullanıcıları **rol** grubundan kaldırmak için Kaydet'i seçin. Adımları **tamamlamak** için Kapat'ı seçin.

## <a name="create-a-custom-role-group"></a>Özel bir rol grubu oluşturma

Özel bir rol grubu oluşturmak için aşağıdaki adımları tamamlayın:

1. E-postanın izin Microsoft 365 uyumluluk merkezi, Microsoft 365 yönetici hesabının kimlik bilgilerini kullanarak oturum açın ve İzinler'e <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**gidin**</a>.
1. İzinler **ve & sayfasında Uyumluluk** merkezi **Roller'i > seçin**.
1. Uyumluluk merkezi **rolleri sayfasında Oluştur'a** **tıklayın**.
1. Rol **grubun adını yazın** sayfasındaki Ad alanına özel rol grubu için bir **ad** girin. Rol grubu oluşturularak rol grubunun adı değiştirilemez. Gerekirse, Açıklama alanına özel rol grubu için bir **açıklama** girin. Devam etmek **için Sonraki'yi** seçin.
1. Rolleri seçin **sayfasında Rolleri** **seç'i seçin**.
1. **Ekle'yi** seçin ve sonra da özel rol grubuna eklemek istediğiniz rolleri seçin. Rol **grubunu eklemek** için Ekle'yi seçin, sonra da **Bitti'yi seçin**.
1. Devam etmek **için Sonraki'yi** seçin.
1. Üye **seç sayfasında Üye** **seç'i seçin**.
1. **Ekle'yi** seçin ve sonra da özel rol grubuna eklemek istediğiniz üyeleri seçin. **Ekle'yi** seçerek üyeleri ekleyin ve ardından **Bitti'yi seçin**.
1. Devam etmek **için Sonraki'yi** seçin.
1. Ayarlarınızı **gözden geçirme sayfasında** , özel rol grubunun ayrıntılarını gözden geçirin. Bilgileri düzenlemeniz gerekirse, uygun bölümde **Düzenle'yi** seçin. Tüm ayarlar doğru olduğunda, özel rol grubunu **oluşturmak için** Rol grubu oluştur'ı veya değişiklikleri atmak ve  özel rol grubunu oluşturmak için İptal'i seçin.

## <a name="update-a-custom-role-group"></a>Özel rol grubunu güncelleştirme

Özel bir rol grubunu güncelleştirmek için aşağıdaki adımları tamamlayın:

1. E-postanın izin Microsoft 365 uyumluluk merkezi, Microsoft 365 yönetici hesabının kimlik bilgilerini kullanarak oturum açın ve İzinler'e <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**gidin**</a>.
1. İzinler **ve & sayfasında Uyumluluk** merkezi **Roller'i > seçin**.
1. Uyumluluk **merkezi roller sayfasında** , güncelleştirilecek rol grubunu seçin.
1. Seçili rol grubunun ayrıntılar bölmesinde Rol grubunu **düzenle'yi seçin**.
1. Rol **grubu adı düzenleme sayfasında** , Açıklama alanında özel rol grubunun açıklamasını **güncelleştirin** . Özel rol grubunun adı değiştirilemez.
1. Rol **seçin sayfasında** , rol **gruplarına atanan** rolleri güncelleştirmek için Düzenle'yi seçin.
1. **Ekle'yi** seçin ve sonra da özel rol grubuna eklemek istediğiniz rolleri seçin. Rol **grubunu eklemek** için Ekle'yi seçin, sonra da **Bitti'yi seçin**.
1. Üye **seçin sayfasında Düzenle'yi** **seçin**.
1. **Ekle'yi** seçin ve sonra da özel rol grubuna eklemek istediğiniz üyeleri seçin. **Ekle'yi** seçerek üyeleri ekleyin ve ardından **Bitti'yi seçin**.
1. **Güncelleştirilmiş Açıklama**, Rol grupları *ve Üyeler* *değerlerini kaydetmek için* *Kaydet'i* seçin.
1. Seçili rol grubunun ayrıntılar bölmesinde Kapat'ı **seçin**.

## <a name="delete-a-custom-role-group"></a>Özel rol grubunu silme

Özel bir rol grubunu güncelleştirmek için aşağıdaki adımları tamamlayın:

1. E-postanın izin Microsoft 365 uyumluluk merkezi, Microsoft 365 yönetici hesabının kimlik bilgilerini kullanarak oturum açın ve İzinler'e <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**gidin**</a>.
1. İzinler **ve & sayfasında Uyumluluk** merkezi **Roller'i > seçin**.
1. Uyumluluk **merkezi roller sayfasında** , güncelleştirilecek rol grubunu seçin.
1. Seçili rol grubunun ayrıntılar bölmesinde Rol grubunu **sil'i seçin**.
1. Uyarı iletişim **kutusunda** , rol grubunu **silmek için Evet'i** veya silme işlemini iptal **etmek için** Hayır'ı seçin.
