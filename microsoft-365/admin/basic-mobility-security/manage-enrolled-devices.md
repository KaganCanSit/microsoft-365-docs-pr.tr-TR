---
title: Microsoft 365'da Mobil Cihaz Yönetimi kayıtlı cihazları yönetme
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkMAC
search.appverid:
- MET150
description: Temel Mobilite ve Güvenlik, kuruluşunuzun mobil cihazlarının güvenliğini sağlamanıza ve yönetmenize yardımcı olabilir.
ms.openlocfilehash: f2da9a20c496d5229d62e477fcf4cc0024436788
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935247"
---
# <a name="manage-devices-enrolled-in-mobile-device-management-in-microsoft-365"></a>Microsoft 365'da Mobil Cihaz Yönetimi kayıtlı cihazları yönetme

Microsoft 365 için yerleşik mobil cihaz yönetimi, kullanıcılarınızın iPhone, iPad, Android ve Windows telefonlar gibi mobil cihazlarının güvenliğini sağlamanıza ve yönetmenize yardımcı olur. İlk adım, Microsoft 365 oturum açmak ve Basic Mobility and Security'yi ayarlamaktır. Daha fazla bilgi için bkz. [Basic Mobility ve Security'yi ayarlama](set-up.md).

Bunu ayarladıktan sonra, kuruluşunuzdaki kişilerin cihazlarını hizmete kaydetmesi gerekir. Daha fazla bilgi için bkz. [Mobil cihazınızı Temel Hareketlilik ve Güvenlik kullanarak kaydettirin](enroll-your-mobile-device.md).Ardından, kuruluşunuzdaki cihazları yönetmenize yardımcı olması için Basic Mobility ve Security'yi kullanabilirsiniz. Örneğin, e-posta erişimini veya diğer hizmetleri sınırlamaya, cihaz raporlarını görüntülemeye ve bir cihazı uzaktan temizlemeye yardımcı olmak için cihaz güvenlik ilkelerini kullanabilirsiniz. Bu görevleri gerçekleştirmek için genellikle Güvenlik & Uyumluluk Merkezi'ne gidersiniz. Daha fazla bilgi için bkz. [Microsoft Purview uyumluluk portalı](../../compliance/microsoft-365-compliance-center.md).

## <a name="device-management-tasks"></a>Cihaz yönetimi görevleri

Cihaz yönetimi paneline ulaşmak için şu adımları izleyin:

1. [Microsoft 365 yönetim merkezi](../../admin/admin-overview/about-the-admin-center.md) gidin.

2. Arama alanına Mobile Cihaz Yönetimi yazın ve sonuç listesinden **Mobil Cihaz Yönetimi'ı** seçin.

    :::image type="content" source="../../media/basic-mobility-security/bms-6-mobile-device-management-option.png" alt-text="Mobil cihaz yönetimi seçeneği.":::

3. **Başlayalım'ı** seçin.

## <a name="manage-mobile-devices"></a>Mobil cihazları yönetme

Temel Mobilite ve Güvenlik'i ayarladıktan sonra, kuruluşunuzdaki mobil cihazları yönetmenin bazı yollarını burada bulabilirsiniz.

|Bunu yapmak için|Bunu yapın|
|---|---|
|Cihazı silme|Cihaz Yönetimi panelinde *cihaz adını*, ardından tüm bilgileri silmek için **Tam silme'yi** veya yalnızca cihazdaki kuruluş bilgilerini silmek için **Seçmeli silme'yi** seçin. Daha fazla bilgi için bkz [. Basic Mobility and Security'de mobil cihazı temizleme](wipe-mobile-device.md).|
|Desteklenmeyen cihazların Exchange ActiveSync kullanarak Exchange e-postaya erişmesini engelleme|Cihaz Yönetimi panelinde **Engelle'yi** seçin.|
|Parola gereksinimleri ve güvenlik ayarları gibi cihaz ilkelerini ayarlama|Cihaz Yönetimi panelinde **Cihaz güvenlik** **ilkeleriEkle** >  + öğesini seçin. Daha fazla bilgi için bkz. [Basic Mobility ve Security'de cihaz güvenlik ilkeleri oluşturma](create-device-security-policies.md).|
|Engellenen cihazların listesini görüntüleme|Cihaz Yönetimi panelinde, **Görünüm seçin** altında **Engellendi'yi** seçin.|
|Bir kullanıcı veya kullanıcı grubu için uyumsuz veya desteklenmeyen cihazın engellemesini kaldırma|Cihazların engellemesini kaldırmak için aşağıdakilerden birini seçin:<br/>- kullanıcıyı veya kullanıcıları ilkenin uygulandığı güvenlik grubundan kaldırın. Microsoft 365 yönetim merkezi > <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupları'na**</a> gidin ve grup adını seçin. **Üyeleri ve yöneticileri düzenle'yi** seçin.<br/>- Kullanıcıların üyesi olduğu güvenlik grubunu cihaz ilkesinden kaldırın. Güvenlik & Uyumluluk Merkezi > **Güvenlik ilkeleriYeni** **güvenlik ilkeleri'ne** >  gidin. Cihaz ilkesi adını ve ardından **EditDeployment'ı** >  seçin.<br/>- Bir cihaz ilkesi için tüm uyumsuz cihazların engellemesini kaldırın. Güvenlik & Uyumluluk Merkezi > **Güvenlik ilkeleriYeni** **güvenlik ilkeleri'ne** >  gidin. Cihaz ilkesi adını ve ardından **EditAccess gereksinimleri'ni** >  seçin. **Erişime izin ver ve ihlal bildir'i** seçin.<br/>- Bir kullanıcı veya kullanıcı grubu için uyumsuz veya desteklenmeyen bir cihazın engelini kaldırmak için Güvenlik & Uyumluluk Merkezi > **Güvenlik** **ilkeleriCihaz** >  yönetimiCihaz  > **erişim ayarlarını yönet'e** gidin. Microsoft 365 erişiminin engellenmesinin dışında tutmak istediğiniz üyeleri içeren bir güvenlik grubu ekleyin. Daha fazla bilgi için bkz. [Microsoft 365 yönetim merkezi güvenlik grubu oluşturma, düzenleme veya silme](../../admin/email/create-edit-or-delete-a-security-group.md).|
|Cihazları artık Basic Mobility ve Security tarafından yönetilemeyecek şekilde kullanıcıları kaldırma|Kullanıcıyı kaldırmak için, Temel Mobilite ve Güvenlik için cihaz yönetimi ilkeleri olan güvenlik grubunu düzenleyin. Daha fazla bilgi için bkz. [Microsoft 365 yönetim merkezi güvenlik grubu oluşturma, düzenleme veya silme](../../admin/email/create-edit-or-delete-a-security-group.md).<br/>Basic Mobility ve Security'yi tüm Microsoft 365 kullanıcılarınızdan kaldırmak için bkz. [Temel Mobilite ve Güvenlik'i kapatma](turn-off.md).|

Canlı (v14)
