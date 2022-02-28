---
title: Temel Hareketlilik ve Güvenlik'i kapatma
f1.keywords: NOCSH
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
ms.custom: AdminSurgePortfolio
description: Temel Hareketlilik ve Güvenlik'i kapatmak için grupları veya ilkeleri kaldırın.
ms.openlocfilehash: ff3fe72e1ca3a6445aa29ac18404aae139a70f8a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983986"
---
# <a name="turn-off-basic-mobility-and-security"></a>Temel Hareketlilik ve Güvenlik'i kapatma

Temel Hareketlilik ve Güvenlik'i etkili bir şekilde kapatmak için cihaz yönetim ilkelerinden güvenlik grupları tarafından tanımlanan kişi gruplarını veya ilkelerin kendilerini kaldırırsanız.

- Oluşturduğunuz cihaz ilkelerinden kullanıcı güvenlik gruplarını kaldırarak kullanıcı gruplarını kaldırın.

- Tüm Temel Mobil Kullanım ve Güvenlik cihaz ilkelerini kaldırarak herkes için Temel Mobil Kullanım ve Güvenlik'i devre dışı bırakabilirsiniz.

Bu seçenekler, kuruluşların cihazları için Temel Mobil Kullanım ve Güvenlik zorlamalarını kaldırır. Ne yazık ki, bu ayarlamayı tamamladikten sonra yalnızca "unprovision" Basic Mobility and Security (Temel Mobil Kullanım ve Güvenlik) yok.

> [!IMPORTANT]
> İlkelerden kullanıcı güvenlik gruplarını kaldırırken veya ilkelerin kendilerini kaldırırken, kullanıcıların cihazları üzerindeki etkisine dikkat edin. Örneğin, cihaza bağlı olarak e-posta profilleri ve önbelleğe alınmış e-postalar kaldırılabilir. Daha fazla bilgi için bkz  [. İlkeyi silebilir veya kullanıcı ilkeden kaldırabilirsiniz.](../../admin/basic-mobility-security/create-device-security-policies.md)

## <a name="remove-user-security-groups-from-basic-mobility-and-security-device-policies"></a>Kullanıcı güvenlik gruplarını Temel Mobil Kullanım ve Güvenlik cihazı ilkelerinden kaldırma

1. Tarayıcı türüne: yazın [https://protection.office.com/devicev2](https://protection.office.com/devicev2).

2. Bir cihaz ilkesi seçin ve İlkeyi **düzenle'yi seçin**.

3. Dağıtım sayfasında  **Kaldır'ı**  **seçin**.

4.   **Gruplar'ın** altında bir güvenlik grubu seçin.

5.  **Kaldır'ı** ve ardından Kaydet'i **seçin**.

## <a name="remove-basic-mobility-and-security-device-policies"></a>Temel Mobil Kullanım ve Güvenlik cihaz ilkelerini kaldırma

1. Tarayıcı türüne: yazın [https://protection.office.com/devicev2](https://protection.office.com/devicev2).

2. Bir cihaz ilkesi seçin ve ardından İlkeyi  **sil'i seçin**.

3. Uyarı iletişim kutusunda Evet'i **seçin**.

> [!NOTE]
> Kuruluş cihazlarınız hala engellenen durumda ise cihazların engellemesini kaldırmaya daha fazla adım için, Erişim Denetimi'nin Engellenenler kategorisinden kaldırılması blog [Office 365 için Mobil Cihaz Yönetimi](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Removing-Access-Control-from-Mobile-Device-Management-for-Office/ba-p/279934).
