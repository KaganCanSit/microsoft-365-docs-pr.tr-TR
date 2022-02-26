---
title: Microsoft 365'ta Mobil Cihaz Yönetimi'ne kayıtlı cihazları Microsoft 365
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
description: Temel Mobil Kullanım ve Güvenlik, kuruluşlarının mobil cihazlarını güvenlik altına adan ve yönetmenize yardımcı olabilir.
ms.openlocfilehash: 152b4cc33fab740516d7138cca8f4a15096c8312
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973703"
---
# <a name="manage-devices-enrolled-in-mobile-device-management-in-microsoft-365"></a>Microsoft 365'ta Mobil Cihaz Yönetimi'ne kayıtlı cihazları Microsoft 365

Microsoft 365 için yerleşik mobil cihaz yönetimi, kullanıcılarınızı iPhone, iPad, Android ve Windows telefonlar gibi mobil cihazlarının güvenliğini sağlamanıza ve yönetmenize yardımcı olur. İlk adım, Mobil kullanım Microsoft 365 ve Güvenlik ayarlamaktır. Daha fazla bilgi için bkz [. Temel Mobil Kullanım ve Güvenlik'i ayarlama](set-up.md).

Bu ayarlamayı tamamladikten sonra, aşağıdaki kuruluşta yer alan kişilerin cihazlarını hizmete kaydetmeleri gerekir. Daha fazla bilgi için bkz [. Temel Mobil Kullanım ve Güvenlik kullanarak mobil cihazınızı kaydetme](enroll-your-mobile-device.md).Böylece, kurumda cihazları yönetmenize yardımcı olmak için Temel Mobil Kullanım ve Güvenlik'i kullanabilirsiniz. Örneğin, e-posta erişimini veya diğer hizmetleri sınırlandırmanıza, cihaz raporlarını görüntülemeye ve bir cihazı uzaktan temizlemeye yardımcı olmak için cihaz güvenlik ilkelerini kullanabilirsiniz. Bu görevleri gerçekleştirmek için genellikle Güvenlik ve &'ne gidersiniz. Daha fazla bilgi için bkz. [Microsoft 365 uyumluluk merkezi](../../compliance/microsoft-365-compliance-center.md).

## <a name="device-management-tasks"></a>Cihaz yönetimi görevleri

Cihaz yönetim paneline almak için şu adımları izleyin:

1. Büyük/ [yeni Microsoft 365 yönetim merkezi](../../admin/admin-overview/about-the-admin-center.md).

2. Arama alanına Mobil Cihaz Yönetimi yazın ve sonuç **listesinden Mobil Cihaz Yönetimi'ne**  tıklayın.

    :::image type="content" source="../../media/basic-mobility-security/bms-6-mobile-device-management-option.png" alt-text="Mobil cihaz yönetimi seçeneği.":::

3.   **SelectLet'i başlat'ı seçin**.

## <a name="manage-mobile-devices"></a>Mobil cihazları yönetme

Temel Mobil Kullanım ve Güvenlik'i ayarladıktan sonra, işte size kurum içinde mobil cihazları yönetmenin bazı yolları.

|**Bunu yapmak için**|**Bunu yapma**|
|:----------------|:------------------------------------------------------------------------------|
|Cihazı temizleme |Cihaz Yönetimi panelinde,  *cihaz adını seçin*, ardından tüm bilgileri silmek   **içinFull**  temizleme'yi   **veya**  cihaz üzerinde yalnızca kuruluş bilgilerini silmek için Seçimli temizleme'yi seçin. Daha fazla bilgi için bkz [. Temel Mobil Kullanım ve Güvenlik'te mobil cihazı temizleme](wipe-mobile-device.md).|
|Exchange ActiveSync kullanarak desteklenmeyen cihazların e Exchange e-postaya erişimini engel Exchange ActiveSync |Cihaz Yönetimi panelindeBlock'a   **tıklayın**. |
|Parola gereksinimleri ve güvenlik ayarları gibi cihaz ilkelerini ayarlama |Cihaz Yönetimi panelinde Cihaz **güvenliği** ilkeleriAdd  > **+ öğesini seçin**. Daha fazla bilgi için bkz [. Temel Hareketlilik ve Güvenlik'te cihaz güvenliği ilkeleri görme](create-device-security-policies.md).|
|Engellenen cihazların listesini görüntüleme  |Cihaz Yönetimi panelinde, Görünüm seçin   **öğesinin altındaBlocked**    **öğesini seçin**. |
|Kullanıcı veya kullanıcı grubu için tamamlanmamış veya desteklenmeyen cihazın engellemesini kaldırma  |Cihazların engelini kaldırmak için aşağıdaki seçimlerden birini yapın:<br/>- İlkenin uygulandığı güvenlik grubundan kullanıcı veya kullanıcıları kaldırın. Gruplar'Microsoft 365 yönetim merkezi > <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**gidin**</a> ve ardından grup adını seçin. Üyeleri **ve yöneticileri düzenle'yi seçin**.<br/>- Kullanıcıların cihaz ilkesinden üyesi olduğu güvenlik grubunu kaldırın. Güvenlik ilkeleriDevice & için Güvenlik > **Merkezi'ne** **** > gidin. Cihaz ilkesi adını seçin ve sonra **da** **EditDeployment** >  öğesini seçin.<br/>- Cihaz ilkesi için tüm uyumlu olmayan cihazların engellemesini kaldırabilirsiniz. Güvenlik ilkeleriDevice & için Güvenlik > **Merkezi'ne** **** > gidin. Cihaz ilkesi adını ve sonra **EditAccess gereksinimleri'ne** >  **tıklayın**. Erişime  **ve rapor ihlaline izin ver'i seçin**.<br/>- Kullanıcının veya kullanıcı grubunun uyumlu olmayan veya desteklenmeyen bir cihazın engellemesini kaldırmak için, Güvenlik & Uyumluluk Merkezi 'ne gidin >Güvenlik  **ilkeleriDevice** **** > yönetimi  > Cihaz  **erişim ayarlarını yönet**. Postanıza erişimin engellenmiş olması dışında tutmak istediğiniz üyelerin olduğu bir güvenlik Microsoft 365. Daha fazla bilgi için bkz[. Güvenlik grubunu oluşturma, düzenleme veya Microsoft 365 yönetim merkezi](../../admin/email/create-edit-or-delete-a-security-group.md).|
|Kullanıcıları kaldırın, böylece cihazları artık Temel Mobil Kullanım ve Güvenlik tarafından yönetilmiyor |Kullanıcı kaldırmak için, Temel Mobil Kullanım ve Güvenlik için cihaz yönetimi ilkeleri olan güvenlik grubunu düzenleyin. Daha fazla bilgi için bkz  [. Güvenlik grubunu oluşturma, düzenleme veya Microsoft 365 yönetim merkezi](../../admin/email/create-edit-or-delete-a-security-group.md).<br/>Temel Hareketlilik ve Güvenlik'i tüm kullanıcı Microsoft 365 için bkz[. Temel Hareketlilik ve Güvenlik'i kapatma](turn-off.md).|

Canlı (v14)