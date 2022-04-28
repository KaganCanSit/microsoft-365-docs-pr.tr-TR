---
title: Microsoft 365 için cihaz yönetimi yol haritası
keywords: Microsoft 365, kurumsal Microsoft 365, Microsoft 365 belgeleri, mobil cihaz yönetimi Intune
author: kelleyvice-msft
ms.author: kvice
manager: scotv
ms.date: 08/10/2020
ms.topic: conceptual
f1.keywords:
- NOCSH
ms.prod: microsoft-365-enterprise
ms.service: ''
ms.technology: ''
ms.assetid: fb4182e6-5e78-45d0-9641-d791c4519441
audience: ITPro
ms.custom: microsoft-intune
description: Microsoft 365 için cihaz yönetimini ayarlama yol haritası.
ms.openlocfilehash: eeed1a69fc1724f3feb75f4bc096cad3a3c25cf0
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095322"
---
# <a name="device-management-roadmap-for-microsoft-365"></a>Microsoft 365 için cihaz yönetimi yol haritası

Kuruluş için Microsoft 365, kuruluşunuzdaki cihazları ve uygulamalarını yönetmeye yardımcı olacak özellikler içerir. Mobil cihazları yönetmek, kuruluşunuzun kaynaklarının güvenliğini sağlamanıza ve korumanıza yardımcı olur.

Cihaz yönetimi için iki seçenek vardır:

- [Microsoft Intune](#microsoft-intune)
- [Temel Hareketlilik ve Güvenlik](#basic-mobility-and-security)

## <a name="microsoft-intune"></a>Microsoft Intune

Mobil cihaz yönetimi veya mobil uygulama yönetimi kullanarak kuruluşunuza erişimi yönetmek için Microsoft Intune kullanabilirsiniz. Mobil cihaz yönetimi, kullanıcıların cihazlarını Intune "kaydettiği" durumdur. Bir cihaz kaydedildikten sonra yönetilen bir cihazdır; bu nedenle kuruluşunuzun ilkelerini, kurallarını ve ayarlarını alabilir. Örneğin, belirli uygulamaları yükleyebilir, parola ilkesi oluşturabilir, VPN bağlantısı yükleyebilir ve daha fazlasını yapabilirsiniz.

Kendi kişisel cihazları olan kullanıcılar cihazlarını kaydetmek istemeyebilir veya Intune ve kuruluşunuzun ilkeleri tarafından yönetilebilir. Ancak yine de kuruluşunuzun kaynaklarını ve verilerini korumanız gerekir. Bu senaryoda, mobil uygulama yönetimini kullanarak uygulamalarınızı koruyabilirsiniz. Örneğin, cihazda SharePoint Online'a erişirken kullanıcının PIN girmesini gerektiren bir mobil uygulama yönetimi ilkesi kullanabilirsiniz.

Ayrıca kişisel cihazları ve kuruluşa ait cihazları nasıl yöneteceğini de belirlersiniz. Cihazları kullanımlarına bağlı olarak farklı şekilde ele almak isteyebilirsiniz.

## <a name="basic-mobility-and-security"></a>Temel Hareketlilik ve Güvenlik

Bu, Microsoft 365 yerleşik olarak bulunur ve iPhone' lar, iPad'ler, Android'ler ve Windows telefonlar gibi kullanıcılarınızın mobil cihazlarının güvenliğini sağlamanıza ve yönetmenize yardımcı olur. Cihaz güvenlik ilkeleri oluşturup yönetebilir, bir cihazı uzaktan silebilir ve ayrıntılı cihaz raporlarını görüntüleyebilirsiniz.

## <a name="choose-between-the-two-options"></a>İki seçenek arasında seçim yapma

Hangi cihaz yönetimi seçeneğinin sizin için en uygun olduğunu daha iyi değerlendirmenize yardımcı olmak için bkz. [Basic Mobility Security ile Intune arasında seçim yapma](/office365/securitycompliance/choose-between-mdm-and-intune).

Değerlendirmenize bağlı olarak, cihazlarınızı şu şekilde yönetmeye başlayın:

- [Intune](/microsoft-365/solutions/manage-devices-with-intune-overview)
- [Temel Hareketlilik ve Güvenlik](https://support.microsoft.com/office/set-up-basic-mobility-and-security-dd892318-bc44-4eb1-af00-9db5430be3cd)
 
## <a name="identity-and-device-access-recommendations"></a>Kimlik ve cihaz erişim önerileri

Microsoft, güvenli ve üretken bir iş gücü sağlamak için [kimlik ve cihaz erişimine](../security/office-365-security/microsoft-365-policies-configurations.md) yönelik bir dizi öneri sağlar. Cihaz erişimi için şu makalelerdeki önerileri ve ayarları kullanın:

- [Önkoşullar](../security/office-365-security/identity-access-prerequisites.md)
- [Genel kimlik ve cihaz erişim ilkeleri](../security/office-365-security/identity-access-policies.md)

## <a name="how-contoso-did-device-management-for-microsoft-365"></a>Contoso Microsoft 365 için cihaz yönetimini nasıl yaptı?

Kurgusal ama temsili çok uluslu bir işletmenin mobil cihaz yönetimi altyapısını Microsoft 365 bulut hizmetleriyle nasıl dağıttıkları hakkında bilgi için bkz. [Contoso için mobil cihaz yönetimi](contoso-mdm.md).