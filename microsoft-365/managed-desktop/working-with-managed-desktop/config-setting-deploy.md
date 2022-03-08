---
title: Microsoft Yönetilen Masaüstü'de yapılandırılabilir ayarları dağıtma
description: Microsoft Yönetilen Masaüstü'nden yapılandırılabilir ayarlar değişikliklerini dağıtın ve takip edin.
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler, dağıtım, aşamalı dağıtım, yapılandırılabilir ayarlar
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: a52995ff9ab2f946ca11417d4ed7bfa13825353f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326796"
---
# <a name="deploy-and-track-configurable-settings---microsoft-managed-desktop"></a>Yapılandırılabilir ayarları dağıtma ve izleme - Microsoft Yönetilen Masaüstü

Ayar kategorilerinde değişiklikler yaptıktan ve dağıtımı aşamalara verdikten sonra, Dağıtım durumu sayfası ayarlarınızı gruplara dağıtmaya başlamanıza olanak verir. Bu sayfada, yapılandırılabilir her ayarın özeti görüntülenir. Bir ayar kategorisini a açılışında, ayarları gruplara dağıtabilirsiniz ve bu dağıtımların ilerlemesini izleyebilirsiniz.

## <a name="deployment-statuses"></a>Dağıtım durumları

Aşağıda, her dağıtımda göreceğinız durumların bilgileri ve ardından ve ardından bir dağıtımda yer alan bilgiler ve bilgiler ve daha sonra ve daha sonra aşağıda ve her dağıtımda yer alan bilgiler ve daha sonra farklı bir dağıtımda yer

Durum | Açıklama
--- | ---
Dağıtma | Değişikliğiniz bu gruba dağıtılanı bekliyor.
Devam ediyor | Değişiklik, bu gruptaki etkin cihazlara uygulanıyor.
Tamamlandı | Değişiklik, bu gruptaki tüm etkin cihazlarda tamamlanır.
Başarısız | Değişiklik, gruptaki etkin cihazların yüzde 10'sinde başarısız oldu. Dağıtım durduruldu.<br><br> Dağıtımın sorunlarını gidermek için Microsoft Yönetilen Masaüstü işlemleriyle birlikte otomatik olarak bir destek isteği açılır.
Geri döndürüldi | Değişiklik, tüm dağıtım gruplarına başarıyla dağıtılan son değişiklikle geri alınmıştır.

## <a name="deploy-changes"></a>Değişiklikleri dağıtma

Örnek olarak, bu yönergelerde bir masaüstü arka plan resmi kullanız. Dağıtımı aşamalı olarak tamamladikten sonra, değişiklikleri Dağıtım durumu sayfasından dağıtabilirsiniz.

**Değişiklikleri dağıtmak için:**

1. E-Microsoft Endpoint Manager [açın](https://endpoint.microsoft.com/) ve Cihazlar **menüsüne** gidin.
2. Microsoft Yönetilen Masaüstü bölümünde Yönet'i **Ayarlar**.
3. Dağıtım **durumu çalışma** alanında, dağıtmak istediğiniz ayarı seçin. Ardından, dağıtımın aşamalı dağıtımını seçin.
4. Değişikliği **dağıtım** gruplarından biri olarak dağıtmak için Dağıt'ı seçin.

> [!NOTE]
> Turuncu uyarı simgesi, dağıtım için sırada dağıtımı önerilen bir önceki grubun olduğunu gösterir.

<!-- Needs picture updated to show MEM ![Deployment status workspace. Trusted sites pane on the right. In the Deployment groups section are three columns: deployment groups, devices, and status. In the status column, "deploy" is highlighted.](../../media/1deployedit.png) -->

Dağıtım gruplarına şu sırayla dağıtmanızı öneririz: Test, İlk, Hızlı ve sonra da Geniş.

Her grupta değişiklikler tamamlandığında, durum olarak Tamamlandı olarak **değişir**.

<!-- Needs picture updated to show MEM ![Deployment status workspace with columns for date updated, version, test, first, fast, and broad. The Proxy row is expanded, showing a dated setting flagged as "complete" in each of the four deployment groups.](../../media/2completeedit.png) -->

## <a name="revert-deployment"></a>Dağıtımı geri alma

Değişikliği dağıttıktan sonra Dağıtım durumundan **geri dönebilirsiniz**. Devam eden veya Tamamlandı olan bir **değişikliği geri** **döndürtüyseniz**, geçerli dağıtım durur. Bu ayar, tüm gruplara dağıtılan son sürüme geri döner.

Örnek olarak, masaüstü arka plan resmini geri döndürelim.

**Değişikliği geri dönmek için:**

1. E-Microsoft Endpoint Manager [açın](https://endpoint.microsoft.com/) ve Cihazlar **menüsüne** gidin.
2. Microsoft Yönetilen Masaüstü bölümünde Yönet'i **Ayarlar**.
3. Dağıtım **durumu çalışma** alanında, geri almak istediğiniz ayarı seçin. Ardından, geri dönmek için aşamalı dağıtımı seçin.
4. Bu **değişikliği geri döndürmeniz mi gerekiyor? altında** Dağıtımı geri **döndür'ü seçin**.

<!-- Needs picture updated to show MEM ![Deployment status workspace. Browser start pages is selected, opening a pane on the right side with data about the submitted change and its status. At the bottom is the "need to revert this change" area where you can select "Revert deployment."](../../media/3revert.png) -->

## <a name="additional-resources"></a>Ek kaynaklar

- [Yapılandırılabilir ayarlara genel bakış](config-setting-overview.md)
- [Yapılandırılabilir ayarlar başvurusu](config-setting-ref.md)
