---
title: Farklı cihazlar üzerinde Uç Nokta yapılandırma ayarları için Microsoft Defender'ı Microsoft Endpoint Manager
description: Uç Nokta için Microsoft Defender aracılığıyla Microsoft Endpoint Manager ayarlarını etkinleştirmeyi öğrenin.
keywords: cihaz yönetimi, Uç nokta cihazları için Microsoft Defender'ı yapılandırma, Microsoft Endpoint Manager
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a8a57b14480c45ddbc154d71bc4f2ded315c83ae
ms.sourcegitcommit: 0251d5c6cb141055c93c83a402c3dc52c7a70dcc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2021
ms.locfileid: "62997109"
---
# <a name="manage-microsoft-defender-for-endpoint-configuration-settings-on-devices-with-microsoft-endpoint-manager"></a>Farklı cihazlar üzerinde Uç Nokta yapılandırma ayarları için Microsoft Defender'ı Microsoft Endpoint Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Farklı cihazlar için Uç Nokta için Microsoft Defender'ı Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



[!include[Prerelease information](../../includes/prerelease.md)]


> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)


Uç Nokta için Microsoft Defender Güvenlik Yönetimi, Microsoft Endpoint Manager veya Microsoft Endpoint Configuration Manager Microsoft Intune tarafından yönetil almayan cihazlar için Microsoft Defender'ın güvenlik yapılandırmalarını alma özelliğidir. doğrudan Endpoint Manager.


Önkoşullar, desteklenen platformlar ve daha fazlası gibi Güvenlik Yapılandırma Yönetimi hakkında daha fazla bilgi için bkz. Güvenlik Desteği olan cihazlarda Uç Nokta için [Microsoft Defender Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).



[!INCLUDE [Prerequisites](../../includes/security-config-mgt-prerequisites.md)]

>[!NOTE]
>Bu özellik aşamalı olarak aşamalı olarak aşamalı olarak tümeyle bire bir şekilde aşamalı olarak aşamalı olarak tümeylen ve şekilde aşamalı olarak aşamalı 

Güvenlik Yapılandırma Yönetimi hakkında daha fazla bilgi için bkz. Güvenlik YapılandırmasıNa sahip cihazlarda [Uç Nokta için Microsoft Defender Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).

Kayıt sorunlarıyla karşılaşırsanız Bkz. [Güvenlik Yapılandırma Yönetimi ekleme sorunlarını giderme](troubleshoot-security-config-mgt.md).

> [!NOTE]
> Bu özellik, zaten Microsoft Endpoint Manager'a (Intune veya Configuration Manager) kayıtlı olan cihazlar için geçerli değildir. Intune'a kayıtlı cihazlar, kendi kurulmuş yönetim kanallarından ilke almaya devam eder.

## <a name="identify-onboarded-devices"></a>Yerleşik cihazları belirleme

Uç nokta ekleme işlemi için Microsoft Defender Güvenlik Yönetimi'nin başarıyla tamamlanmış olduğunu doğrulamak üzere aşağıdaki adımları kullanın.

1.  Cihazın, siparişler bölümünün Cihaz Envanteri bölümünde [Microsoft 365 Defender](https://security.microsoft.com/).

2.  Azure Active Directory [portalında](https://aad.portal.azure.com/#blade/Microsoft_AAD_Devices/DevicesMenuBlade/Devices/menuId/), cihazın başarıyla kaydediliyor olduğunu doğrulayın.

3.  Microsoft Endpoint Manager [Yönetim Merkezi'nde](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/mDMDevicesPreview), Cihazlar ve Tüm cihazlar bölümünde araarak cihazın başarıyla **> doğrulayın**.


## <a name="offboard-devices"></a>Offboard cihazları
Uç nokta için Microsoft Defender Güvenlik Yönetimi aracılığıyla ekli olan offboard cihazları için bkz. Uç nokta için [Microsoft Defender](offboard-machines.md) hizmetinin offboard cihazları.

>[!NOTE]
>Bu etkinse, [çıkar ayarı Tamper Protection'ı](prevent-changes-to-security-settings-with-tamper-protection.md#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal) devre dışı bıraktır.

## <a name="troubleshooting-security-management"></a>Güvenlik Yönetimi sorunlarını giderme 
Uç nokta kaydı sorunları için Microsoft Defender Güvenlik Yönetimi sorunlarını gidermek için bkz. Uç Nokta için [Microsoft Defender Güvenlik Yönetimi ile ilgili ekleme sorunlarını giderme](troubleshoot-security-config-mgt.md).

## <a name="related-topic"></a>İlgili konu
- [Uç Nokta için Microsoft Defender Güvenlik Yönetimi ile ilgili ekleme sorunlarını giderme](troubleshoot-security-config-mgt.md)
- [Farklı cihazlar için Uç Nokta için Microsoft Defender'ı Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration#configure-your-tenant-to-support-mde-security-configuration-management)
