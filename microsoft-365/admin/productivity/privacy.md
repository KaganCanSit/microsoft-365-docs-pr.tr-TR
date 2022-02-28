---
title: Microsoft Üretkenlik Puanı - Gizlilik
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
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
description: Üretkenlik Puanı ile gizlilik nasıl korunur.
ms.openlocfilehash: 1bbc9c7459d29e9aef8dea102d1d98eed9c30550
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984478"
---
# <a name="privacy-controls-for-productivity-score"></a>Üretkenlik Puanı için gizlilik denetimleri

Üretkenlik Puanı, kullanım deneyimi ve bunu destekleyen teknoloji deneyimleri aracılığıyla, Microsoft 365 dijital dönüşüm yolculuğuna içgörüler sağlar.  Kuruluş puanı kişi ve teknoloji deneyimi ölçülerini yansıtarak sizinkilere benzer kuruluşların kıyaslamalarına göre karşılaştırabilirsiniz. Daha fazla ayrıntı için Üretkenlik [Puanına genel bakış bilgilerini gözden geçin](productivity-score.md).

Gizliliğiniz Microsoft için önemlidir. Gizliliğinizi nasıl korumamız olduğunu öğrenmek için [Microsoft'un gizlilik bildirimine bakın](https://privacy.microsoft.com/privacystatement). Üretkenlik Puanı, kuruluş yöneticisi olarak size, görüntüleyilen Üretkenlik Puanı bilgisinin işlemde kullanılabilir olduğundan emin olmak için gizlilik ayarlarına erişmenizi sağlar ve aynı zamanda microsoft'ta organizasyon güveninden ödün vermeden.

Kişiler deneyimi alanında, ölçümler yalnızca kuruluş düzeyinde kullanılabilir. Bu alanda, içerik işbirliği, Microsoft 365, toplantılar, ekip çalışması ve iletişim kategorilerine bakarak kişilerin çalışma ve çalışma saatlerini nasıl kullanıyor olduğu yer almaktadır. İç gizlilik ilkesi ihtiyaçlarınızı karşılamanıza yardımcı olmak için size çeşitli denetim düzeyleri sağlaruz.
Denetimler size şunları sağlar:

- Üretkenlik Puanı'daki bilgileri kimlerin göreceğini kontrol etmek için esnek yönetici rolleri.
- Kişiler deneyimi alanında bu özelliği devre dışı bırakma özelliği.

## <a name="flexible-admin-roles-to-control-who-can-see-the-information-in-productivity-score"></a>Üretkenlik Puanı'daki bilgileri kimlerin göreceğini kontrol etmek için esnek yönetici rolleri

Üretkenlik Puanı'nın tamamını görüntülemek için aşağıdaki yönetici rollerinden biri olmak gerekir:

- Genel yönetici
- Exchange yöneticileri
- SharePoint yöneticisi
- Skype Kurumsal yöneticisi
- Ekipler yöneticisi
- Genel Okuyucu
- Rapor Okuyucusu
- Kullanım Özeti Raporları Okuyucusu

Değişiklik yönetiminden ve benimsemeden sorumlu olan ancak mutlaka bir IT yöneticisi olması gerekmemesi için, Rapor Okuyucusu'nun veya Kullanım Özeti Rapor Okuyucusu'nun rolünü atama. Bu rol, ilgili yönetim merkezinde üretkenlik puanı deneyiminin Microsoft 365 verir.

Kullanım Özeti Rapor Okuyucusu rolü, 2020'nin sonlarında Kaynaktan atanıncaya kadar, PowerShell cmdlet'leri aracılığıyla atanacak Microsoft 365 yönetim merkezi gerekir.

PowerShell ile Kullanım Özeti Rapor Okuyucusu rolünü atamak için:

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


## <a name="capability-to-opt-out-of-people-experiences"></a>Kişi deneyimlerini devre dışı bırakma özelliği

Ayrıca, Üretkenlik Puanı alanında kişiler deneyimini devre dışı abilirsiniz. Bu seçeneği devre dışı tercih etmek için, organizasyondan hiç kimse bu ölçümleri görüntülemez ve organizasyonunız iletişim, toplantılar, ekip çalışması, içerik işbirliği ve mobil kullanımla ilgili tüm hesaplamalardan kaldırılır. Organizasyon organizasyonunun kişi deneyimi raporlarında yer almaktan vazgeçmek için Genel yönetici olmak gerekir.

Devre dışı bırakma:

1. Yönetim merkezinde ÜrünÜrünleri **Puanı Ayarlar**  >   **Org Ayarlar** >  **gidin**.
2. Kişiler deneyimi öngörüleri için kullanılacak **kullanım Microsoft 365 ve veri kullanımına izin ver onay kutusunun işaretini kaldırın**. Intune yapılandırma yöneticisinde Uç Nokta Analizi için veri paylaşımı ayarlarını değiştirme hakkında bilgi edinmek için Daha fazla **bilgi'yi seçin**.
3. **Kaydet'i seçin**.

:::image type="content" source="../../media/orgsettingspageoptout.png" alt-text="Kişi deneyimlerinden vazgeçmeyi tercih edebilirsiniz kuruluş ayarları sayfası.":::
