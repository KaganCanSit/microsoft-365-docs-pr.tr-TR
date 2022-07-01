---
title: Uç Nokta için Microsoft Defender yapılandırma ayarlarını farklı bir Microsoft Endpoint Manager cihazı ile yönetin
description: Uç Nokta için Microsoft Defender aracılığıyla Microsoft Endpoint Manager'da güvenlik ayarlarını etkinleştirmeyi öğrenin.
keywords: cihaz yönetimi, Uç Nokta için Microsoft Defender cihazları yapılandırma, Microsoft Endpoint Manager
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2c19352d584bedc5acd94f9984242a2c50d2fcf3
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66573931"
---
# <a name="manage-microsoft-defender-for-endpoint-configuration-settings-on-devices-with-microsoft-endpoint-manager"></a>Uç Nokta için Microsoft Defender yapılandırma ayarlarını farklı bir Microsoft Endpoint Manager cihazı ile yönetin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Microsoft Endpoint Manager ile cihazlarda Uç Nokta için Microsoft Defender yönetme](/mem/intune/protect/mde-security-integration)
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)


Uç Nokta için Microsoft Defender için Güvenlik Yönetimi, Bir Microsoft Endpoint Manager tarafından yönetilmeyen cihazların doğrudan Endpoint Manager Microsoft Defender güvenlik yapılandırmalarını almasına yönelik bir özelliktir.


Önkoşullar, desteklenen platformlar ve daha fazlası dahil olmak üzere Güvenlik Yapılandırma Yönetimi hakkında daha fazla bilgi için bkz. [Microsoft Endpoint Manager ile cihazlarda Uç Nokta için Microsoft Defender yönetme](/mem/intune/protect/mde-security-integration).

Uç Nokta için Microsoft Defender için güvenlik yapılandırmasını yönetmek üzere Microsoft Endpoint Manager kullanmayı öğrenmek için bu videoyu izleyin.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4qLVq]

[!INCLUDE [Prerequisites](../../includes/security-config-mgt-prerequisites.md)]

>[!NOTE]
>Bu özellik aşamalı olarak kullanıma alınıyor. 

Güvenlik Yapılandırma Yönetimi hakkında daha fazla bilgi için bkz. [Microsoft Endpoint Manager ile cihazlarda Uç Nokta için Microsoft Defender yönetme](/mem/intune/protect/mde-security-integration).

Kayıt sorunlarıyla karşılaşırsanız bkz [. Güvenlik Yapılandırma Yönetimi ekleme sorunlarını giderme](troubleshoot-security-config-mgt.md).

> [!NOTE]
> Bu özellik, Microsoft Endpoint Manager'a (Intune veya Configuration Manager) zaten kayıtlı cihazlar için geçerli değildir. Intune kayıtlı cihazlar, yerleşik yönetim kanalları aracılığıyla ilke almaya devam eder.

## <a name="identify-onboarded-devices"></a>Eklenen cihazları tanımlama

Uç noktalarınızın Uç Nokta için Microsoft Defender ekleme işlemi için Güvenlik Yönetimi'ni başarıyla tamamladığını doğrulamak için aşağıdaki adımları kullanın.

1.  Cihazın [Microsoft 365 Defender](https://security.microsoft.com/) Cihaz Envanteri bölümünde göründüğünü doğrulayın.

2.  [Azure Active Directory portalında](https://aad.portal.azure.com/#blade/Microsoft_AAD_Devices/DevicesMenuBlade/Devices/menuId/) cihazın başarıyla kaydedildiğini doğrulayın.

3.  [Microsoft Endpoint Manager Yönetici Merkezi'nde](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/mDMDevicesPreview), **Cihazlar > Tüm cihazlar** bölümüne bakarak cihazın başarıyla kaydedildiğini doğrulayın.


## <a name="offboard-devices"></a>Cihazları çıkarma
Uç Nokta için Microsoft Defender için Güvenlik Yönetimi aracılığıyla eklenen cihazları kullanıma almak için bkz. [cihazları Uç Nokta için Microsoft Defender hizmetinden çıkarma](offboard-machines.md).

>[!NOTE]
>Çıkarma, etkinse [Kurcalama Koruması'nın devre dışı bırakılmasına](prevent-changes-to-security-settings-with-tamper-protection.md#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal) neden olur.

## <a name="troubleshooting-security-management"></a>Güvenlik Yönetimi Sorunlarını Giderme 
Uç Nokta için Microsoft Defender kayıt sorunlarını gidermek için bkz. [Uç Nokta için Microsoft Defender için Güvenlik Yönetimi ile ilgili ekleme sorunlarını giderme](troubleshoot-security-config-mgt.md).

## <a name="related-topic"></a>İlgili konu
- [Uç Nokta için Microsoft Defender için Güvenlik Yönetimi ile ilgili ekleme sorunlarını giderme](troubleshoot-security-config-mgt.md)
- [Microsoft Endpoint Manager ile cihazlarda Uç Nokta için Microsoft Defender yönetme](/mem/intune/protect/mde-security-integration#configure-your-tenant-to-support-mde-security-configuration-management)
