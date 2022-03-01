---
title: Şifreli e-posta gönderme
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
ms.date: 9/20/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
ms.assetid: 496e690b-b75d-4ff5-bf34-cc32905d0364
description: E-postanızı kullanarak şifreli e-posta göndermeyi Outlook.
ms.openlocfilehash: 15f5b87fb238d4a872f13c11f1e88892f628a255
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011991"
---
# <a name="encrypt-or-label-your-sensitive-email"></a>Hassas e-postanızı şifreleme veya etiketleme

Verileriniz ve kampanya verileriniz önemli ve çoğunlukla gizlidir. Sizin ve e-posta alıcılarınızın bilgileri gerekli duyarlılıkla değiştirmesi için şifreleme ve duyarlılık etiketlerini kullanarak bu hassas bilgilerin korunmasına yardımcı olun.

## <a name="best-practices"></a>En iyi uygulamalar

Gizli veya hassas bilgiler içeren e-posta göndermeden önce şunları açmanız iyi olabilir:

- **Şifreleme:** E-postada bilgilerin gizliliğini korumak için e-postanızı şifreebilirsiniz. E-posta iletisi şifrelerken, okunabilir düz metinden karıştırılmış şifreleme metnine dönüştürülür. Yalnızca iletiyi şifrelemek için kullanılan ortak anahtarla eşleşen özel anahtarı olan alıcı iletiyi okumak için çözebilir. Öte yandan, ilgili özel anahtarı olmayan tüm alıcılar, anlanabilir metin görür. Yöneticiniz, belirli ölçütlere uyan iletileri otomatik olarak şifrelemek için kurallar tanımlayabilir. Örneğin yöneticiniz, kuruluş dışından gönderilen tüm iletileri veya belirli sözcükler ya da tümceciklerden söz edilen tüm iletileri şifreen bir kural oluşturabilir. Tüm şifreleme kuralları otomatik olarak uygulanır.
- **Duyarlılık etiketleri:** Kampanyanız ayrıca, kampanyanıza ilişkin bilgi koruma ilkeleriyle uyumlu olması için dosyalarınıza ve e-postanıza uygulayabilecek duyarlılık etiketleri de kurabilirsiniz. Bir etiket ayarsanız, örneğin iletinizin üst bilgi olarak görünmesi yoluyla, e-postanız göndernse bile etiket e-posta adresinizde kalıcı olur.

![Etiketler ve şifreleme için açıklama çizgileri içeren bir e-posta diyagramı.](../media/m365-campaign-email-encrypt.png)

## <a name="set-it-up"></a>Ayarlayın

Önceden tanımlanmış bir kurala uymamış bir iletiyi şifrelemek için yöneticiniz hiçbir kural ayarlamamışsa, iletiyi göndermeden önce çeşitli farklı şifreleme kuralları uygulayabilirsiniz. Outlook 2013 veya 2016'dan şifrelenmiş ileti göndermek için Mac için Outlook 2016, seçenekler > İzinler'i **seçin ve sonra** da size gereken koruma seçeneğini belirtin. Ayrıca, posta iletisinde Koru düğmesini seçerek **de şifrelenmiş** Web üzerinde Outlook. Daha fazla bilgi için bkz[. PC için Posta'da şifrelenmiş iletileri gönderme, Outlook ve yanıtlama](https://support.microsoft.com/en-us/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980).

## <a name="admin-settings"></a>Yönetici ayarları

E-posta şifrelemeyi ayarlama hakkında bilgi edinmek için şu [adreste E-posta şifrelemesi Microsoft 365](../compliance/email-encryption.md).

### <a name="automatically-encrypt-email-messages"></a>E-posta iletilerini otomatik olarak şifrele

Yöneticiler, kampanyanıza gönderilen ve kampanyadan alınan e-posta iletilerini otomatik olarak korumak için posta akış kuralları oluşturabilir. Tüm giden e-posta iletilerini şifrelemek için kurallar ayarlayın ve kuruluş içinden gelen şifrelenmiş iletilerden veya kuruluştan gönderilen şifrelenmiş iletilere gelen yanıtlardan şifrelemeyi kaldırın.

Yeni E-posta (OME) özellikleriyle e-posta Office 365 İleti Şifrelemesi kurallar oluşturabilirsiniz. Yönetim merkezini <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">(EAC)</a> kullanarak yeni OME özellikleriyle ileti şifrelemeyi Exchange kurallar tanımlayın. 

1. Web tarayıcısında, genel yönetici izinleri verilmiş bir iş veya okul hesabı kullanarak oturum açın.
2. Yönetici kutucuğunu seçin.
3. Yönetim merkezinde Yönetim merkezleri ve **Merkezi'ni > Exchange**.

Daha fazla bilgi için bkz. [E-posta iletilerini şifrelemek için posta akışı kurallarını tanımlama](../compliance/define-mail-flow-rules-to-encrypt-email.md).

### <a name="brand-your-encryption-messages"></a>Şifreleme iletilerinizin markasını koruma

Ayrıca, e-posta iletilerinizin görünümünü ve metnini özelleştirmek için kampanya markanızı da uygulayabilirsiniz. Daha fazla bilgi için [bkz. Şifrelenmiş iletilerinize kuruluş markasını ekleme](../compliance/email-encryption.md).