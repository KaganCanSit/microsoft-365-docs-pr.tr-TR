---
title: İş için Microsoft Defender'de rol ve izin atama
description: Siber güvenlik ekibinize roller atayın. İş için Defender'da bu roller ve izinler hakkında bilgi edinin.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 03295989e1ee44ab43fe0cc53e4029a6c4307ea8
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172651"
---
# <a name="assign-roles-and-permissions-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'de rol ve izin atama

Microsoft 365 Defender portalında İş için Microsoft Defender yapılandırma, raporları görüntüleme veya algılanan tehditlerle ilgili yanıt eylemleri gerçekleştirme gibi görevleri gerçekleştirmek için güvenlik ekibinize uygun izinlerin atanması gerekir. İzinler, Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com)) veya Azure Active Directory atanan roller aracılığıyla [verilir.](/azure/active-directory/roles/manage-roles-portal) 

## <a name="what-to-do"></a>Yapılması gerekenler

1. [İş için Defender'daki roller hakkında bilgi edinin](#roles-in-defender-for-business).
2. [Güvenlik ekibiniz için rol atamalarını görüntüleyin veya düzenleyin](#view-or-edit-role-assignments).
3. [Sonraki adımlarınıza geçin](#next-steps).

>
> **Bir dakikan var mı?**
> Lütfen <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">güvenlikle ilgili kısa anketimize</a> katılın. Sizden haber almak isteriz!
>

## <a name="roles-in-defender-for-business"></a>İş için Defender'daki roller

Aşağıdaki tabloda, İş için Defender'da atanabilecek üç rol açıklanmaktadır. [Yönetici rolleri hakkında daha fazla bilgi edinin](../../admin/add-users/about-admin-roles.md).

| İzin düzeyi | Açıklama |
|:---|:---|
| **Genel yöneticiler** (genel yöneticiler olarak da adlandırılır) <br/><br/> *En iyi yöntem olarak genel yönetici sayısını sınırlayın.* | Genel yöneticiler her türlü görevi gerçekleştirebilir. Şirketinizi Microsoft 365 veya İş için Microsoft Defender için kaydolan kişi varsayılan olarak genel yöneticidir. <br/><br/> Genel yöneticiler aşağıdakiler gibi tüm Microsoft 365 portallarında ayarlara erişebilir/ayarları değiştirebilir: <br/>- Microsoft 365 yönetim merkezi ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>- Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com)) |
| **Güvenlik yöneticileri** (güvenlik yöneticileri olarak da adlandırılır) | Güvenlik yöneticileri aşağıdaki görevleri gerçekleştirebilir: <br/>- Güvenlik ilkelerini görüntüleme ve yönetme <br/>- Güvenlik tehditlerini ve uyarılarını görüntüleme ve yönetme (bu etkinlikler uç noktalarda yanıt eylemleri gerçekleştirmeyi içerir) <br/>- Güvenlik bilgilerini ve raporlarını görüntüleme |
| **Güvenlik gözetmeni** | Güvenlik okuyucuları aşağıdaki görevleri gerçekleştirebilir: <br/>- Güvenlik ilkelerini görüntüleme <br/>- Güvenlik tehditlerini ve uyarılarını görüntüleme <br/>- Güvenlik bilgilerini ve raporlarını görüntüleme  |


## <a name="view-or-edit-role-assignments"></a>Rol atamalarını görüntüleme veya düzenleme

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

2. Gezinti bölmesinde **İzinler & roller'i** seçin ve **Azure AD** altında **Roller'i** seçin.

3. Yan bölmesini açmak için aşağıdaki rollerden birini seçin:

   - Genel yönetici
   - Güvenlik yöneticisi
   - Güvenlik gözetmeni

   > [!IMPORTANT]
   > Microsoft, kişilere yalnızca görevlerini gerçekleştirmek için ihtiyaç duydukları şeylere erişim verilmesini önerir. Bu kavramı izinler için *en az ayrıcalık* olarak adlandırıyoruz. Daha fazla bilgi edinmek için bkz. [Uygulamalar için en az ayrıcalıklı erişim için en iyi yöntemler](/azure/active-directory/develop/secure-least-privileged-access). 

4. Yan bölmede **üyeleri Azure AD yönet** bağlantısını seçin. Bu eylem sizi rol atamalarınızı görüntüleyip yönetebileceğiniz Azure Active Directory (Azure AD) götürür.

5. Profilini açmak için bir kullanıcı seçin ve ardından **Atanan roller'i** seçin.

   - Rol eklemek için **+ Atama ekle'yi** seçin.
   - Rolü kaldırmak için **X Atamaları kaldır'ı** seçin. 

## <a name="need-to-add-users"></a>Kullanıcı eklemeniz mi gerekiyor?

Aboneliğinize henüz kullanıcı eklemediyseniz bkz. [Aynı anda kullanıcı ekleme ve lisans atama](mdb-add-users.md).

## <a name="next-steps"></a>Sonraki adımlar

Devam et:

- [3. Adım: E-posta bildirimlerini ayarlama](mdb-email-notifications.md)
- [4. Adım: Cihazları İş için Microsoft Defender ekleme](mdb-onboard-devices.md)