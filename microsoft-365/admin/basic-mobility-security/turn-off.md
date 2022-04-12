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
description: Temel Mobilite ve Güvenlik'i kapatmak için grupları veya ilkeleri kaldırın.
ms.openlocfilehash: c3c82c040e688977a68e06639e87c8f733bc8c38
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780775"
---
# <a name="turn-off-basic-mobility-and-security"></a>Temel Hareketlilik ve Güvenlik'i kapatma

Temel Mobilite ve Güvenlik'i etkin bir şekilde kapatmak için, cihaz yönetimi ilkelerinden güvenlik grupları tarafından tanımlanan kişi gruplarını kaldırırsınız veya ilkeleri kendileri kaldırırsınız.

- Oluşturduğunuz cihaz ilkelerinden kullanıcı güvenlik gruplarını kaldırarak kullanıcı gruplarını kaldırın.

- Tüm Temel Mobilite ve Güvenlik cihaz ilkelerini kaldırarak Basic Mobility ve Security'yi herkes için devre dışı bırakın.

Bu seçenekler, kuruluşunuzdaki cihazlar için Temel Mobilite ve Güvenlik zorlamasını kaldırır. Ne yazık ki, temel mobilite ve güvenliği ayarladıktan sonra yalnızca "sağlamayı kaldıramazsınız".

> [!IMPORTANT]
> Kullanıcı güvenlik gruplarını ilkelerden kaldırdığınızda veya ilkeleri kaldırdığınızda, kullanıcıların cihazları üzerindeki etkisini unutmayın. Örneğin, cihaza bağlı olarak e-posta profilleri ve önbelleğe alınmış e-postalar kaldırılabilir. Daha fazla bilgi için bkz. [İlkeyi sildiğinizde veya ilkeden bir kullanıcıyı kaldırdığınızda ne olur?](../../admin/basic-mobility-security/create-device-security-policies.md)

## <a name="remove-user-security-groups-from-basic-mobility-and-security-device-policies"></a>Temel Mobilite ve Güvenlik cihaz ilkelerinden kullanıcı güvenlik gruplarını kaldırma

1. Tarayıcınıza şunu yazın: [https://protection.office.com/devicev2](https://protection.office.com/devicev2).

2. Bir cihaz ilkesi seçin ve **İlkeyi düzenle'yi** seçin.

3. **Dağıtım** sayfasında **Kaldır'ı** seçin.

4. **Gruplar'ın** altında bir güvenlik grubu seçin.

5. **Kaldır'ı** ve **ardından Kaydet'i** seçin.

## <a name="remove-basic-mobility-and-security-device-policies"></a>Temel Mobilite ve Güvenlik cihaz ilkelerini kaldırma

1. Tarayıcınıza şunu yazın: [https://protection.office.com/devicev2](https://protection.office.com/devicev2).

2. Bir cihaz ilkesi seçin ve ardından **İlkeyi sil'i** seçin.

3. Uyarı iletişim kutusunda **Evet'i** seçin.

> [!NOTE]
> Kuruluş cihazlarınız hala engellenmiş durumdaysa cihazların engellemesini kaldırmaya yönelik daha fazla adım için Access Control [Office 365 için Mobil Cihaz Yönetimi kaldırma](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Removing-Access-Control-from-Mobile-Device-Management-for-Office/ba-p/279934) blog gönderisine bakın.
