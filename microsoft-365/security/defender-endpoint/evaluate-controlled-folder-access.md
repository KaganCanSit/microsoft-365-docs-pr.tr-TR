---
title: Denetimli klasör erişimini değerlendirme
description: Denetimli klasör erişiminin, dosyaların kötü amaçlı uygulamalar tarafından değişmeye karşı korunmasına nasıl yardımcı olduğunu öğrenin.
keywords: Exploit protection, windows 10, windows 11, windows defender, fidye yazılımı, koruma, değerlendirme, test etme, tanıtım, deneme
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: conceptual
author: dansimp
ms.author: dansimp
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.technology: mde
ms.collection: m365initiative-m365-defender
ms.date: ''
ms.openlocfilehash: 996a96f957d7446b0b951d4f1b3a34c822f64f49
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019521"
---
# <a name="evaluate-controlled-folder-access"></a>Denetimli klasör erişimini değerlendirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)


[Denetimli klasör erişimi](controlled-folders.md) , belgelerinizi ve dosyalarınızın şüpheli veya kötü amaçlı uygulamalar tarafından değiştirilmesine karşı korunmasına yardımcı olan bir özelliktir. Denetimli klasör erişimi Windows Server 2019, Windows Server 2022, Windows 10 ve Windows 11 istemcisinde de de kullanılabilir.

Bu, özellikle dosyalarınızı şifrelemeye ve onları [tutmaya çalışan fidye](https://www.microsoft.com/wdsi/threats/ransomware) yazılımlarına karşı korunmanıza yardımcı olur.

Bu makale denetimli klasör erişimini değerlendirmenizi sağlar. Bu, özelliği doğrudan kuruluş içinde test etmek için denetim modunun nasıl etkinleştir açık olduğunu gösterir.

> [!TIP]
> Ayrıca, özelliğin çalıştığını onaylamak ve nasıl çalıştığını görmek için demo.wd.microsoft.com'da Uç nokta tanıtım senaryosu web sitesini ziyaret edebilirsiniz.[](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground)

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

## <a name="use-audit-mode-to-measure-impact"></a>Etkiyi ölçmek için denetim modunu kullanma

Denetimli klasör erişimini, tümüyle etkinleştirildiğinde ne olacağının *kaydını görmek için* denetim modunda etkinleştirin. İşletmeler için iş hattı uygulamalarınızı etkilemeyecek şekilde özelliğin kuruluşta nasıl çalıştığını test edin. Ayrıca, belirli bir süre boyunca genellikle kaç şüpheli dosya değiştirme girişiminin oluştuğu hakkında da fikir de eldeebilirsiniz.

Denetim modunu etkinleştirmek için aşağıdaki PowerShell cmdlet'ini kullanın:

```PowerShell
Set-MpPreference -EnableControlledFolderAccess AuditMode
```

> [!TIP]
> Denetimli klasör erişiminin kuruluş içinde nasıl çalış çalışsa da tam denetime sahip olmak için bu ayarı ağ cihazlarınıza dağıtmak üzere bir yönetim aracı kullansanız gerekir.
Ayarı yapılandırmak ve dağıtmak için, ana denetimli klasör erişimi konusunda açıklandığı gibi Grup İlkesi, Intune, mobil cihaz yönetimi (MDM) veya Microsoft Endpoint Manager'i de [kullanabilirsiniz](controlled-folders.md).

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>Olay Görüntüleyicisi'nde denetimli klasör Windows olaylarını gözden geçirme

Aşağıdaki denetimli klasör erişimi olayları, Microsoft Windows/Windows/Windows Defender/İşlem klasörü altında Olay Görüntüleyicisi'nde görüntülenir.

Olay Kimliği | Açıklama
-|-
 5007 | Ayarların değiştir olduğu olay
 1124 | Denetlenen denetimli klasör erişimi olayı
 1123 | Denetlenen klasör erişimi olayı engellendi

> [!TIP]
> Günlükleri merkezi olarak Windows [için Olay Iletme aboneliğini](/windows/win32/wec/setting-up-a-source-initiated-subscription) yapılandırabilirsiniz. 

## <a name="customize-protected-folders-and-apps"></a>Korumalı klasörleri ve uygulamaları özelleştirme

Değerlendirmeniz sırasında korumalı klasörler listesine eklemek veya bazı uygulamaların dosyaları değiştirmesine izin vermek seçebilirsiniz.

Bkz [. Grup İlkesi](controlled-folders.md) , PowerShell ve MDM yapılandırma hizmet sağlayıcıları (CSP) gibi yönetim araçlarıyla özelliği yapılandırmak için denetimli klasör erişimiyle önemli klasörleri koruma.

## <a name="see-also"></a>Ayrıca bkz.

* [Denetimli klasör erişimiyle önemli klasörleri koruma](controlled-folders.md)
* [Uç Nokta için Microsoft Defender'ı Değerlendirme](evaluate-mde.md)
* [Denetim modunu kullanma](audit-windows-defender.md)
