---
title: Organizasyonunız için Microsoft geri bildirimlerini yönetme
f1.keywords:
- NOCSH
ms.author: Kwekua
author: Kwekua
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
- BCS160
- MET150
- MOE150
description: Kullanıcılarınızı Microsoft ürünleri hakkında Microsoft'a gönderebilirsiniz geri bildirimi yönetin.
ms.openlocfilehash: 9b63a4046c9d1ab13ae6b3f4856a521d4c7a9b70
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984003"
---
# <a name="manage-microsoft-feedback-for-your-organization"></a>Organizasyonunız için Microsoft geri bildirimlerini yönetme

Bir Microsoft 365 kuruluş yöneticisi olarak, Microsoft 365 uygulamalarını kullanırken geri bildirim toplamasını ve kullanıcılarınızı müşteri katılımı deneyimini yönetmenize yardımcı olacak çeşitli Microsoft 365 vardır. Bu ilkelerden her biri için, organizasyonda mevcut Azure Active directory gruplarını oluşturabilir ve kullanabilirsiniz. Bu güvenlik güvenlikleriyle, organizasyon departmanlarının Microsoft'a geri bildirim gönderişini kontrol etmek için çeşitli departmanların ne kadar geri bildirim gönderebilirsiniz? Microsoft, müşteriler tarafından gönderilen tüm geri bildirimleri gözden kullanır ve ürünü geliştirmek için bu geri bildirimi kullanır. Geri bildirim deneyimlerini Açık tutmak **,** kullanıcılarının kullanmakta olduğu Microsoft ürünleri hakkında neler söylüyor olduklarını görmenizi sağlar. Kullanıcılarından topladığımız geri bildirim kısa süre içinde <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi.</a>

Geri bildirim türleri ve Microsoft'un kullanıcı geri bildirimlerini nasıl kullandığı hakkında daha fazla bilgi edinmek için bkz [. Organizasyonunız için Microsoft geri bildirimleri hakkında bilgi öğrenin](../misc/feedback-user-control.md).

Aşağıdaki tablo, şu anda aşağıdaki geri bildirim ilkeleri tablosunda gösterilen geri bildirim ilkelerine hangi uygulama ve hizmetlerin bağlı olduğunu gösterir. Ekran görüntüsü örnekleri için tablonun altına bakın.

|**Uygulamalar & Hizmetleri**|**Ürünle ilgili geri bildirim** <br> |**Ürün içinde anketler** <br> |**Meta veri toplama** <br> |**Müşteri katılımı** <br> |
|:-----|:-----|:-----|:-----|:-----|
|**Erişim**|Evet|Evet|Evet|Evet|
|**Excel**|Evet|Evet|Evet|Evet|
|**Office.com**|Çok yakında|Çok yakında|Çok yakında|Çok yakında|
|**OneNote**|Evet|Evet|Evet|Evet|
|**OneDrive**|[Bazı ayarlar şu anda diğer denetimler tarafından yönetiliyor.](/onedrive/disable-contact-support-send-feedback)||||
|**Outlook**|Çok yakında|Çok yakında|Çok yakında|Çok yakında|
|**PowerPoint**|Evet|Evet|Evet|Evet|
|**Project**|Çok yakında|Çok yakında|Çok yakında|Çok yakında|
|**Publisher**|Evet|Evet|Evet|Evet|
|**SharePoint**|[Bazı ayarlar şu anda diğer denetimler tarafından yönetiliyor.](/powershell/module/sharepoint-online/set-spotenant)||||
|**Teams**|[Bazı ayarlar şu anda diğer denetimler tarafından yönetiliyor.](/microsoftteams/manage-feedback-policies-in-teams)||||
|**Word**|Evet|Evet|Evet|Evet|
|**Visio**|Evet|Evet|Evet|Evet|
|**Yammer**|Evet|Evet|Evet|Evet|

[Ürünle ilgili anket ve geri bildirim örneklerini görmek için buraya bakın.](/microsoft-365/admin/misc/feedback-user-control#in-product-surveys)

**Meta veri toplama**

:::image type="content" source="../../media/feedback-metadata2.png" alt-text="Ekran görüntüsü: Meta veri örneğini gösteren Geri Bildirim sayfası":::

**Müşteri katılımı**

:::image type="content" source="../../media/feedback-in-product-customer-engagement.png" alt-text="Ekran görüntüsü: Ürün içinde müşteri araştırması sorusu örneği":::

## <a name="before-you-begin"></a>Başlamadan önce

Bu ilkeleri kullanmak için cihazlarınız minimum bir derleme numarasında olmalıdır. Daha fazla bilgi için aşağıdaki tabloya bakın.

|**Derleme #**|**Win32**|**iOS**|**Android**|**Mac**|**Web**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Ürünle ilgili geri bildirim|En az 16.0.13328|En az 2,42|En az 16.0.13328|En az 16,42|Genel kullanıma açık|
|Ürün içinde anketler|En az 16.0.13328|En az 2,42|En az 16.0.13426|En az 16,42|Bekleyen rollout|
|Meta veri toplama|En az 16.0.13328|En az 2,42|En az 16.0.13328|En az 16,42|Genel kullanıma açık|
|Müşteri katılımı|En az 16.0.13328|En az 2,42|En az 16.0.13426|En az 16,42|Bekleyen rollout|

## <a name="specific-policies-you-can-configure"></a>Yapılandırılan belirli ilkeler

### <a name="feedback-policies"></a>Geri bildirim ilkeleri

|**İlke adı**|**Varsayılan durum**|**Denetim özeti**|
|:-----|:-----|:-----|
|Kullanıcıların Microsoft'a geri bildirim göndermesine izin verme|On|Uygulamalar arasında geri bildirim giriş noktalarını kontrol eder|
|Kullanıcıların Microsoft'tan ürünle ilgili anketleri almalarına ve yanıtlamalarına izin verme|On|Ürün içindeki anket istemlerini kontrol eder|
|Microsoft'a geri bildirim gönderen kullanıcıların ekran görüntüleri ve ekleri eklemesine izin verme|Kapalı|Kullanıcının hangi meta verileri geri bildirim/anket ile göndermek üzere karar ver istediğini belirler|
|Microsoft'un kullanıcılar tarafından gönderilen geri bildirimleri izlemesine izin verme|Kapalı|Kullanıcının kişi bilgilerini geri bildirim/anketle paylaşarak paylaştır birden çok|
|Kullanıcıların Microsoft'a gönderilen günlük dosyalarını ve içerik örneklerini içermesine izin verme|Kapalı|Kullanıcının geri bildirim/anket ile göndermek üzere karar ver sadece meta verilerini belirler|

## <a name="configure-policies"></a>İlkeleri yapılandırma

1. Gidin ve oturum [https://config.office.com](https://config.office.com) aç'a tıklayın.
1. **Özelleştirme'yi ve** ardından **İlke Yönetimi'ne seçin**.
1. **Oluştur**’u seçin.
1. Ad **ve** açıklama **girin**.
1. Yapılandırmak istediğiniz Azure Active dizin gruplarını seçin.
1. Geri Bildirim ve **Araştırma'da arama.**
1. Listelenen her ilke için, istediğiniz değeri ayarlayın.

Daha fazla bilgi için bkz[. İlke bulut Office genel bakış](/deployoffice/overview-office-cloud-policy-service).

Bu ilke ayarları, Grup İlkesi kullanırsanız da kullanılabilir. Bu ilke ayarlarını kullanmak için, 22 Mart 2021'de yayımlanan Yönetim Şablonu dosyalarının [(ADMX/ADML)](https://www.microsoft.com/download/details.aspx?id=49030) en az 5146.1000 sürümünü indirin.

Bu ilke ayarlarını Kullanıcı Yapılandırması -> İlkeleri -> Yönetim Şablonları -> Microsoft Office 2016 -> -> Güven Merkezi altında bulabilirsiniz.

> [!NOTE]
> İstemci uygulamalarının güncelleştirilsi birkaç saat sürer.
