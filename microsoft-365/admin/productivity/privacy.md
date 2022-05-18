---
title: Microsoft Üretkenlik Puanı ve gizlilik içgörüleri
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
monikerRange: o365-worldwide
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
description: Gizlilik, Üretkenlik Puanı ile nasıl korunur?
ms.openlocfilehash: 823e2cc087d3f0e9c486d8c0c4eca92ba42aee21
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65467942"
---
# <a name="privacy-controls-for-productivity-score"></a>Üretkenlik Puanı için gizlilik denetimleri

Üretkenlik Puanı, kuruluşunuzun Microsoft 365 kullanımı ve onu destekleyen teknoloji deneyimleri aracılığıyla dijital dönüşüm yolculuğuna ilişkin içgörüler sağlar.  Kuruluşunuzun puanı, kişi ve teknoloji deneyimi ölçümlerini yansıtır ve sizinkine benzer kuruluşların karşılaştırmalarıyla karşılaştırılabilir. Diğer ayrıntılar için [Üretkenlik Puanına genel bakış](productivity-score.md) bölümünü görüntüleyin.

Gizliliğiniz Microsoft için önemlidir. Gizliliğinizi nasıl koruduğumuz hakkında bilgi edinmek için [Microsoft'un gizlilik bildirimine](https://privacy.microsoft.com/privacystatement) bakın. Üretkenlik Puanı, kuruluşunuzun BT yöneticisi olarak, görüntülediğiniz Üretkenlik Puanı bilgilerinin eyleme dönüştürülebilir olduğundan emin olmanıza yardımcı olmak için gizlilik ayarlarına erişim sağlar ve kuruluşunuzun Microsoft'ta yer aldığı güveni tehlikeye atamaz.

Kişiler deneyimleri alanında ölçümler yalnızca kuruluş düzeyinde kullanılabilir. Bu alan, içerik işbirliği, hareketlilik, toplantılar, ekip çalışması ve iletişim kategorilerine bakarak kişilerin Microsoft 365 nasıl kullandıklarını inceler. İç gizlilik ilkesi gereksinimlerinizi karşılamanıza yardımcı olmak için çeşitli denetim düzeyleriyle size olanak sağlarız.
Denetimler size şu bilgileri verir:

- Üretkenlik Puanı'nda bilgileri kimlerin görebileceğini denetlemek için esnek yönetici rolleri.
- kişi deneyimleri alanından çıkma özelliği.

## <a name="flexible-admin-roles-to-control-who-can-see-the-information-in-productivity-score"></a>Üretkenlik Puanı'nda bilgileri kimlerin görebileceğini denetlemek için esnek yönetici rolleri

Üretkenlik Puanı'nın tamamını görüntülemek için aşağıdaki yönetici rollerinden biri olmanız gerekir:

- Genel yönetici
- Exchange yöneticileri
- SharePoint yöneticisi
- Skype Kurumsal yöneticisi
- Ekipler yöneticisi
- Genel Okuyucu
- Rapor Okuyucusu
- Kullanım Özeti Raporları Okuyucusu

Rapor Okuyucusu veya Kullanım Özeti Raporları Okuyucusu rolünü, değişiklik yönetimi ve benimsemeden sorumlu olan, ancak bt yöneticisi olması gerekmeyen herkese atayın. Bu rol, Microsoft 365 yönetim merkezinde üretkenlik puanı deneyiminin tamamına erişmelerini sağlar.

Kullanım Özeti Raporları Okuyucusu rolünün, 2020'nin sonraki Microsoft 365 yönetim merkezi atanabilene kadar PowerShell cmdlet'leri aracılığıyla atanmalıdır.

PowerShell ile Kullanım Özeti Raporları Okuyucusu rolünü atamak için:

- Aşağıdaki PowerShell'i çalıştırın:

```powershell
Connect-AzureAD
Enable-AzureADDirectoryRole -RoleTemplateId '75934031-6c7e-415a-99d7-48dbd49e875e'
$role=Get-AzureADDirectoryRole -Filter "roleTemplateId eq '75934031-6c7e-415a-99d7-48dbd49e875e'"
Get-AzureADDirectoryRoleMember -ObjectId $role.ObjectId
$u=Get-AzureADUser -ObjectId <user upn>
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId $u.ObjectId
```

</br>


## <a name="capability-to-opt-out-of-people-experiences"></a>Kişi deneyimlerini geri çevirme özelliği

Ayrıca Üretkenlik Puanı'nın kişi deneyimleri alanından da çıkabilirsiniz. Devre dışı bırakmanız durumunda kuruluşunuzdan hiç kimse bu ölçümleri görüntüleyemez ve kuruluşunuz iletişim, toplantılar, ekip çalışması, içerik işbirliği ve mobilite içeren hesaplamalardan kaldırılacaktır. Kuruluşunuzun kişi deneyim raporları dışında bırakılabilmesi için Genel yönetici olmanız gerekir.

Geri çevirmek için:

1. Yönetim merkezinde **Ayarlar** **Org Ayarlar** >   >   **Ürünlük Puanı'na** gidin.
2. **kişiler içgörüler yaşarken Microsoft 365 kullanım verilerinin kullanılmasına izin ver** kutusunun işaretini kaldırın. Intune yapılandırma yöneticisinde Endpoint Analytics için veri paylaşımı ayarlarının nasıl değiştirileceği hakkında bilgi edinmek için **Daha fazla bilgi'yi** seçin.
3. **Kaydet'i** seçin.

:::image type="content" source="../../media/orgsettingspageoptout.png" alt-text="Kişi deneyimlerini geri çevirebileceğiniz kuruluş ayarları sayfası.":::
