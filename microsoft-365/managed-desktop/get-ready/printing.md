---
title: Microsoft Yönetilen Masaüstü için yazdırma kaynaklarını hazırlama
description: Yazdırmanın sorunsuzca çalışmasını sağlarken gereken önemli adımlar
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: a66075637a15eb39eda38e318070af2bcbdc8fe6
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2022
ms.locfileid: "63016644"
---
# <a name="prepare-printing-resources-for-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü için yazdırma kaynaklarını hazırlama

Microsoft Yönetilen Masaüstü'ne kaydolmaya hazır olurken, yazdırma gereksinimlerinizi değerlendirmeli ve ortamınız için doğru yaklaşımı belirlemeniz gerekir. Üç seçenek vardır:

| Seçenek | Açıklama |
| ------ | ------ |
| Microsoft Universal Print çözümünü dağıtma | Microsoft Yönetilen Masaüstü cihazlarının yazıcıları keşfetmelerini kolaylaştıran Microsoft Universal Print çözümü. Daha fazla bilgi için bkz [. Evrensel Yazdırma Nedir](/universal-print/fundamentals/universal-print-whatis)? |
| Özel bir PowerShell betiği kullanarak yazıcıları doğrudan dağıtma | Yerel yazıcıları ayarlama [bölümündeki adımları](#set-up-local-printers) izleyin. |
| Microsoft dışı bir bulut yazdırma çözümü kullanma | Microsoft'a özel bulut yazdırma çözümü olarak kullanabileceğiniz çözüm, Windows 10 cihazlarla uyumlu ve bir Azure Active Directory çözümüdür. Çözüm, Microsoft Yönetilen Masaüstü için yazılım gereksinimlerini karşılamalıdır. Daha fazla bilgi için [bkz. Microsoft Yönetilen Masaüstü uygulaması gereksinimleri](../service-description/mmd-app-requirements.md). |

Yukarıdaki seçeneklerin tamamlarında, yazıcı sürücüleri Microsoft Update veya Microsoft Store'de kullanılamıyorsa bunları kendiniz almalı ve bunları Microsoft Yönetilen Masaüstü cihazlarınıza dağıtım için Microsoft Intune. Daha fazla bilgi için [bkz. Intune Tek Başına - Win32 uygulama yönetimi](/mem/intune/apps/apps-win32-app-management)

## <a name="set-up-local-printers"></a>Yerel yazıcıları ayarlama

Aşağıdaki yönergelerde, yazdırma kaynaklarını hazırlar ve özel PowerShell betiği kullanarak yazıcıları dağıtmaya karar verirsiniz.

**Özel PowerShell betiği kullanarak yazıcıları dağıtmak için:**

1. Microsoft Yönetilen Masaüstü portalına gidin.
1. Yönetici Portalı'nın *Destek Merkezi Destek* istekleri **> Yazıcı** dağıtımı etiketli bir istek gönderin.
1. Aşağıdaki ayrıntıları sağlama:
    - Microsoft Yönetilen Masaüstü cihazları için dağıtılması gereken paylaşılan yazıcı konumlara giden tüm UNC yolları.
    - Bu paylaşılan yazıcılara erişim gerektiren kullanıcı grupları.
1. Yönetim Portalı'nın kullanımı, isteğin ne zaman tamamlandıktan sonra size haber vermesine neden olur. Başlangıçta, yapılandırmayı yalnızca Test dağıtım grubunda cihazlara dağıt ayarlarız.
1. Yapılandırmanın beklediğiniz gibi çalıştığını test edip onaylayın.
1. Testlerinizi ne **zaman tamamla** ilgili olduğunu bize haber vermek için destek isteğinde Tartışma sekmesini kullanarak yanıtlayın.
1. Ardından yapılandırmayı diğer dağıtım gruplarına dağıtın.

## <a name="steps-to-get-ready"></a>Hazır olmak için adımlar

1. [Microsoft Yönetilen Masaüstü için önkoşulları gözden geçirebilirsiniz](prerequisites.md).
1. Hazırlık [değerlendirme araçlarını çalıştırın](readiness-assessment-tool.md).
1. Satın [Şirket Portalı](../get-started/company-portal.md).
1. Konuk [hesapları için önkoşulları gözden geçirebilirsiniz](guest-accounts.md).
1. Ağ [yapılandırmasını denetleme](network.md).
1. [Sertifikaları ve ağ profillerini hazırlayın](certs-wifi-lan.md).
1. [Verileri kullanıcı erişimini hazırlama](authentication.md).
1. [Uygulamaları hazırlama](apps.md).
1. [Eşlenmiş sürücüleri hazırlama](mapped-drives.md).
1. Yazdırma kaynaklarını hazırlama (bu makale).
1. Cihaz [adlarını adresle](address-device-names.md).
