---
title: Microsoft Purview uyumluluk portalındaki izinler
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.service: O365-seccomp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
description: Microsoft Purview uyumluluk portalı izinleri yönetme hakkında bilgi edinin.
ms.collection: M365-security-compliance
ms.custom:
- admindeeplinkCOMPLIANCE
- admindeeplinkEXCHANGE
ms.openlocfilehash: b8e7f17ef22163e091307fda7cd0beb6659022dc
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623853"
---
# <a name="permissions-in-the-microsoft-purview-compliance-portal"></a>Microsoft Purview uyumluluk portalındaki izinler

Microsoft Purview uyumluluk portalı, Microsoft 365'te uyumluluk görevlerini gerçekleştiren kullanıcılar için izinleri doğrudan yönetmeyi destekler. Bu güncelleştirme, uyumluluk çözümlerinin izinlerini yönetmek için artık Office 365 Güvenlik & Uyumluluk Merkezi'ni kullanmak zorunda kalmayabileceğiniz anlamına gelir. Uyumluluk portalındaki yeni **İzinler** sayfasını kullanarak cihaz yönetimi, Microsoft Purview Veri Kaybı Önleme, eBulma, iç risk yönetimi, bekletme ve diğerleri gibi özelliklerde uyumluluk görevleri için kullanıcılara yönelik izinleri yönetebilirsiniz. Kullanıcılar yalnızca açıkça erişim izni vediğiniz uyumluluk görevlerini gerçekleştirebilir.

Uyumluluk portalında **İzinler** sekmesini görüntülemek için kullanıcıların genel yönetici olması veya *Rol Yönetimi* rolüne atanması gerekir (rol yalnızca *Kuruluş Yönetimi* rol grubuna atanır). *Rol Yönetimi* rolü, kullanıcıların rol gruplarını görüntülemesine, oluşturmasına ve değiştirmesine olanak tanır.

![Microsoft Purview uyumluluk portalı'deki İzinler sayfası.](../media/m365-compliance-center-permissions.png)

Uyumluluk portalındaki izinler rol tabanlı erişim denetimi (RBAC) izin modelini temel alır. RBAC, Microsoft 365 hizmetlerinin çoğu tarafından kullanılan izin modeliyle aynıdır. Bu nedenle, bu hizmetlerdeki izin yapısı hakkında bilgi sahibiyseniz uyumluluk portalında izinler vermek tanıdık olacaktır. Uyumluluk portalında yönetilen izinlerin her bir hizmette gereken tüm izinlerin yönetimini kapsamadığını unutmayın. Yine de belirli bir hizmet için yönetim merkezinde belirli hizmete özgü izinleri yönetmeniz gerekir. Örneğin, arşivleme, denetim ve MRM bekletme ilkeleri için izinler atamanız gerekiyorsa, bu izinleri <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezinde</a> yönetmeniz gerekir.

## <a name="relationship-of-members-roles-and-role-groups"></a>Üyelerin, rollerin ve rol gruplarının ilişkisi

Rol, bir görev kümesi gerçekleştirme izinleri verir; örneğin, Olay Yönetimi rolü kullanıcıların eBulma servis talepleri ile çalışmasına olanak tanır.

Rol grubu, kullanıcıların uyumluluk çözümlerinde uyumluluk portalında işlerini yapmasını sağlayan bir dizi roldür. Örneğin, *Insider Risk Yönetimi* rol grubuna kullanıcı eklendiğinde, atanan yöneticiler, analistler, araştırmacılar ve denetçiler tek bir grupta gerekli iç risk yönetimi izinleri için yapılandırılır. Uyumluluk portalı, kişileri atamanız gereken her uyumluluk çözümü için görevler ve işlevler için varsayılan rol gruplarını içerir. Genel olarak, gerektiğinde varsayılan uyumluluk rol gruplarına tek tek kullanıcıları üye olarak eklemenizi öneririz.

![Rol gruplarının roller ve üyelerle ilişkisini gösteren diyagram.](../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png)

## <a name="permissions-needed-to-use-features-in-the-compliance-portal"></a>Uyumluluk portalında özellikleri kullanmak için gereken izinler

Uyumluluk portalında kullanılabilen tüm varsayılan rol gruplarını ve rol gruplarına varsayılan olarak atanan rolleri görüntülemek için [Güvenlik & Uyumluluk Merkezi'ndeki İzinler'e](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) bakın.

Uyumluluk portalında izinleri yönetmek, kullanıcıların yalnızca uyumluluk portalında bulunan uyumluluk özelliklerine erişmesini sağlar. Uyumluluk portalında olmayan Exchange posta akışı kuralları (taşıma kuralları olarak da bilinir) gibi diğer özelliklere izin vermek istiyorsanız <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">, Exchange yönetim merkezini</a> kullanmanız gerekir.

## <a name="azure-roles-in-the-compliance-portal"></a>Uyumluluk portalında Azure rolleri

Uyumluluk portalı **İzinleri** sayfasının **Azure AD** >  **Roller** bölümünde görünen roller Azure Active Directory rolleridir. Bu roller, kuruluşunuzun BT grubundaki iş işlevleriyle uyumlu olacak şekilde tasarlanmıştır ve bu da bir kişiye işini yapmak için gereken tüm izinleri vermeyi kolaylaştırır. Bir Yönetici rolü seçip rol paneli ayrıntılarını görüntüleyerek her role atanmış olan kullanıcıları görüntüleyebilirsiniz. Azure AD rolünün üyelerini yönetmek için Azure AD üyeleri yönet'i seçin. Bu seçenek sizi Azure yönetim portalına yönlendirir.

|Rol|Açıklama|
|:---|:----------|
|**Genel yönetici**|Tüm Microsoft 365 hizmetlerindeki tüm yönetim özelliklerine erişim. Yalnızca genel yöneticiler diğer yönetici rollerini atayabilir. Daha fazla bilgi için bkz. [Genel Yönetici / Şirket Yöneticisi](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**Uyumluluk veri yöneticisi**|Microsoft 365 genelinde kuruluşunuzun verilerini takip edin, korunduğundan emin olun ve riskleri azaltmaya yardımcı olacak sorunlarla ilgili içgörüler edinin. Daha fazla bilgi için bkz [. Uyumluluk Verileri Yöneticisi](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**Uyumluluk yöneticisi**|Kuruluşunuzun tüm mevzuat gereksinimleriyle uyumlu kalmasına, eBulma servis taleplerini yönetmeye ve Microsoft 365 konumları, kimlikleri ve uygulamaları genelinde veri idare ilkelerini korumalarına yardımcı olun. Daha fazla bilgi için bkz [. Uyumluluk Yöneticisi](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**Güvenlik operatörü**|Microsoft 365 kullanıcılarınıza, cihazlarınıza ve içeriğinize yönelik etkin tehditleri görüntüleyin, araştırın ve yanıt verin. Daha fazla bilgi için bkz [. Güvenlik İşleci](/azure/active-directory/roles/permissions-reference#security-operator).|
|**Güvenlik gözetmeni**|Microsoft 365 kullanıcılarınıza, cihazlarınıza ve içeriğinize yönelik etkin tehditleri görüntüleyin ve araştırın, ancak (Güvenlik operatörünün aksine) eylem gerçekleştirerek yanıt verme izinleri yoktur. Daha fazla bilgi için bkz [. Güvenlik Okuyucusu](/azure/active-directory/roles/permissions-reference#security-reader).|
|**Güvenlik yöneticisi**|Güvenlik ilkelerini yöneterek, Microsoft 365 ürünleri genelinde güvenlik analizlerini ve raporlarını gözden geçirerek ve tehdit ortamı konusunda güncel kalarak kuruluşunuzun genel güvenliğini denetleyin. Daha fazla bilgi için bkz [. Güvenlik Yöneticisi](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**Genel okuyucu**|**Genel yönetici** rolünün salt okunur sürümü. Microsoft 365 genelindeki tüm ayarları ve yönetim bilgilerini görüntüleyin. Daha fazla bilgi için bkz. [Genel Okuyucu](/azure/active-directory/roles/permissions-reference#global-reader).|
|**Saldırı benzetimi yöneticisi**|Saldırı simülasyonu oluşturma, simülasyon başlatma/zamanlama ve simülasyon sonuçlarının gözden geçirilmesinin tüm yönlerini oluşturun ve yönetin. Daha fazla bilgi için bkz [. Saldırı Benzetimi Yöneticisi](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).|
|**Saldırı yükü yazarı**|Saldırı yükleri oluşturun, ancak aslında başlatmayı veya zamanlamayı değil. Daha fazla bilgi için bkz [. Saldırı Yükü Yazarı](/azure/active-directory/roles/permissions-reference#attack-payload-author).|
|

## <a name="add-users-to-a-compliance-role-group"></a>Uyumluluk rol grubuna kullanıcı ekleme

Kullanıcıları bir uyumluluk rol grubuna eklemek için aşağıdaki adımları tamamlayın:

1. Microsoft 365 kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak uyumluluk portalının izinler alanında oturum açın ve Microsoft 365'te uyumluluk rollerini görüntüleme ve yönetme bağlantısını seçmek için <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**İzinler'e**</a> gidin.
1. **Uyumluluk merkezi** bölümünü genişletin ve **Roller'i** seçin.
1. **Uyumluluk merkezi rolleri** sayfasında, kullanıcıları eklemek istediğiniz bir uyumluluk rol grubu seçin ve ardından ayrıntılar bölmesinde **Rol grubunu düzenle'yi** seçin.
1. Sol gezinti **bölmesinden Üyeleri seç'i** ve ardından **Düzenle'yi** seçin.
1. **Ekle'yi** seçin ve ardından rol grubuna eklemek istediğiniz tüm kullanıcılar için onay kutusunu seçin.
1. **Ekle'yi** ve ardından **Bitti'yi** seçin.
1. Kullanıcıları rol grubuna eklemek için **Kaydet'i** seçin. Adımları tamamlamak için **Kapat'ı** seçin.

## <a name="remove-users-from-a-compliance-role-group"></a>Kullanıcıları uyumluluk rol grubundan kaldırma

Kullanıcıları uyumluluk rol grubundan kaldırmak için aşağıdaki adımları tamamlayın:

1. Microsoft 365 kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak uyumluluk portalının izinler alanında oturum açın ve Microsoft 365'te uyumluluk rollerini görüntüleme ve yönetme bağlantısını seçmek için <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**İzinler'e**</a> gidin.
1. Uyumluluk merkezi bölümünü genişletin ve **Roller'i** seçin.
1. **Uyumluluk merkezi rolleri** sayfasında, kullanıcıları kaldırmak istediğiniz bir uyumluluk rolü grubu seçin ve ayrıntılar bölmesinde **Rol grubunu düzenle'yi** seçin.
1. Sol gezinti **bölmesinden Üyeleri seç'i** ve ardından **Düzenle'yi** seçin.
1. **Kaldır'ı** seçin ve ardından rol grubundan kaldırmak istediğiniz tüm kullanıcılar için onay kutusunu seçin.
1. **Kaldır'ı** ve ardından **Bitti'yi** seçin.
1. Kullanıcıları rol grubundan kaldırmak için **Kaydet'i** seçin. Adımları tamamlamak için **Kapat'ı** seçin.

## <a name="create-a-custom-role-group"></a>Özel rol grubu oluşturma

Özel rol grubu oluşturmak için aşağıdaki adımları tamamlayın:

1. Microsoft 365 kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak uyumluluk portalının izinler alanında oturum açın ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**İzinler'e**</a> gidin.
1. **İzinler & rolleri** sayfasında **Uyumluluk merkezi > Roller'i** seçin.
1. **Uyumluluk merkezi rolleri** sayfasında **Oluştur'u** seçin.
1. **Rol grubunuzu adlandırın** sayfasında, **Ad** alanına özel rol grubu için bir ad girin. Rol grubu oluşturulduktan sonra rol grubunun adı değiştirilemez. Gerekirse, Açıklama alanına özel rol grubu için bir **açıklama** girin. Devam etmek için **İleri'yi** seçin.
1. **Rol seç** sayfasında **Rol seç'i** seçin.
1. **Ekle'yi** ve ardından özel rol grubuna eklenecek rolleri seçin. Rol grubunu eklemek için **Ekle'yi** ve ardından **Bitti'yi** seçin.
1. Devam etmek için **İleri'yi** seçin.
1. **Üyeleri seç** sayfasında **Üye seç'i** seçin.
1. **Ekle'yi** ve ardından özel rol grubuna eklenecek üyeleri seçin. Üyeleri eklemek için **Ekle'yi** ve ardından **Bitti'yi** seçin.
1. Devam etmek için **İleri'yi** seçin.
1. **Ayarlarınızı gözden geçirin** sayfasında, özel rol grubunun ayrıntılarını gözden geçirin. Bilgileri düzenlemeniz gerekiyorsa, uygun bölümde **Düzenle'yi** seçin. Tüm ayarlar doğru olduğunda Rol **grubu oluştur'u** seçerek özel rol grubunu oluşturun veya değişiklikleri atıp özel rol grubunu oluşturmamak için **İptal'i** seçin.

## <a name="update-a-custom-role-group"></a>Özel rol grubunu güncelleştirme

Özel rol grubunu güncelleştirmek için aşağıdaki adımları tamamlayın:

1. Microsoft 365 kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak uyumluluk portalının izinler alanında oturum açın ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**İzinler'e**</a> gidin.
1. **İzinler & rolleri** sayfasında **Uyumluluk merkezi > Roller'i** seçin.
1. **Uyumluluk merkezi rolleri** sayfasında güncelleştirilecek rol grubunu seçin.
1. Seçili rol grubunun ayrıntılar bölmesinde **Rol grubunu düzenle'yi** seçin.
1. **Rol grubu adı düzenleniyor** sayfasında, **Açıklama** alanındaki özel rol grubunun açıklamasını güncelleştirin. Özel rol grubunun adı değiştirilemez.
1. **Rol seçin** sayfasında **Düzenle'yi** seçerek rol gruplarına atanan rolleri güncelleştirin.
1. **Ekle'yi** ve ardından özel rol grubuna eklenecek rolleri seçin. Rol grubunu eklemek için **Ekle'yi** ve ardından **Bitti'yi** seçin.
1. **Üyeleri seçin** sayfasında **Düzenle'yi** seçin.
1. **Ekle'yi** ve ardından özel rol grubuna eklenecek üyeleri seçin. Üyeleri eklemek için **Ekle'yi** ve ardından **Bitti'yi** seçin.
1. Güncelleştirilmiş *Açıklama*, *Rol grupları* ve *Üyeler* değerlerini kaydetmek için **Kaydet'i** seçin.
1. Seçili rol grubunun ayrıntılar bölmesinde **Kapat'ı** seçin.

## <a name="delete-a-custom-role-group"></a>Özel rol grubunu silme

Özel rol grubunu güncelleştirmek için aşağıdaki adımları tamamlayın:

1. Microsoft 365 kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak uyumluluk portalının izinler alanında oturum açın ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**İzinler'e**</a> gidin.
1. **İzinler & rolleri** sayfasında **Uyumluluk merkezi > Roller'i** seçin.
1. **Uyumluluk merkezi rolleri** sayfasında güncelleştirilecek rol grubunu seçin.
1. Seçili rol grubunun ayrıntılar bölmesinde **Rol grubunu sil'i** seçin.
1. **Uyarı** iletişim kutusunda, rol grubunu silmek için **Evet'i** veya silme işlemini iptal etmek için **Hayır'ı** seçin.
