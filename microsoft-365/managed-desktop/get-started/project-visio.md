---
title: Microsoft Microsoft Project Masaüstü cihazlarına Visio Microsoft Visio'i yükleme
description: Microsoft Yönetilen Masaüstü Microsoft Project'ne veya Microsoft Visio'i yükleme hakkında bilgi
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, Microsoft Project, Microsoft Visio
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.date: 03/07/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: ab8a68ed17a8705c6e391371600d7b56660f6c57
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63014410"
---
# <a name="install-microsoft-project-or-microsoft-visio-on-microsoft-managed-desktop-devices"></a>Microsoft Microsoft Project Masaüstü cihazlarına Visio Microsoft Visio'i yükleme

Microsoft Project Microsoft Visio Microsoft Yönetilen Masaüstü cihazlarına belirli adımların yüklenmiş olması gerekir. Bu makalede, bu uygulamaların önkoşulları ve yükleme süreci belgeleri yer almaktadır.

## <a name="prerequisites"></a>Önkoşullar

Yöneticiler şu önkoşullara uyanları doğrulamalı:

| Önkoşullar | Açıklama |
| ------ | ------ |
| Lisans miktarları | Kullanıcılarınız, Microsoft Project Microsoft Visio lisanslarının doğru miktarda olması gerekir. Microsoft Yönetilen Masaüstü şu anda bu uygulamaların yalnızca 64 bit sürümlerini desteklemektedir. |
| Lisans adları | Bu uygulamalar için uygun lisans adları: <ul><li>**Microsoft Project** - Project Online Professional veya Project Online Ekstra</li><li>**Microsoft Visio** - Visio Online Plan 2</li><ul> |
| Şirket Portalı | Kullanıcı Şirket Portalı bu uygulamaları yükley için kiracınız için kullanılabilir olması gerekir. Kiracınız Şirket Portalı dağıtıldı değilse bkz. [Şirket Portalı.](company-portal.md) |

## <a name="deploy-project-and-visio-for-microsoft-managed-desktop-devices"></a>Microsoft Project Masaüstü Visio için dağıtım ve dağıtım

Microsoft Yönetilen Masaüstü, masaüstü Microsoft Project Microsoft Visio uygulamalarına iki Win32 Uygulaması olarak Microsoft Intune. Ayrıca, bu grupta iki grup Azure Active Directory. Gruplar ilgili uygulamaya "Uygun" amacına sahip olarak atanır.

**Dağıtım ve Project için Visio:**

Uygun gruba kullanıcı eklersiniz ve uygulama uygun grupta Şirket Portalı. Eşitleme birkaç dakika sürebilir, ancak bundan sonra kullanıcılarınız uygulamaları Mobil Cihaz'dan Şirket Portalı.

Azure AD Grubu adı | Hangi kullanıcıları atamanız gerekir?
 --- | ---
Modern Workplace-Office-Project_Install | Postaya ihtiyacı Project
Modern Workplace-Office-Visio_Install | Postaya ihtiyacı Visio

## <a name="communicate-changes"></a>Değişiklikleri ilet

IT yöneticilerinin, kullanıcılarını yükleme ve yükleme ve yükleme hakkında bilgi Project Visio. Bu iletişim şunları içerir:

- Kullanıcılara bu uygulamaların ne zaman uygun olduğunu bildirebilirsiniz.
- Bu uygulamaları yükleme yönergelerini Şirket Portalı.
