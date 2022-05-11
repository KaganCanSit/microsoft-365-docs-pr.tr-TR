---
title: Algılanan tehditleri inceleme ve harekete geçme
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
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
search.appverid: MET150
description: Windows 10 cihazlarınızda Microsoft Defender Virüsten Koruma tarafından algılanan tehditleri gözden geçirmeyi ve yönetmeyi öğrenin.
ms.openlocfilehash: 9b819edc21d6cfcac663c54e15b1a060b2b16fa2
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65319319"
---
# <a name="review-detected-threats-and-take-action"></a>Algılanan tehditleri inceleme ve harekete geçme

Kötü amaçlı bir dosya veya yazılım algılanır algılanmaz Microsoft Defender Virüsten Koruma bunu engeller ve çalışmasını engeller. Bulut tabanlı koruma açıkken, diğer cihazlarınızın ve kullanıcılarınızın da korunması için virüsten koruma ve kötü amaçlı yazılımdan koruma altyapısına yeni algılanan tehditler eklenir.

Microsoft Defender Virüsten Koruma aşağıdaki tehdit türlerini algılar ve bu tehditlere karşı korur:

- Cihazlarda virüsler, kötü amaçlı yazılımlar ve web tabanlı tehditler
- Kimlik avı girişimleri
- Veri hırsızlığı girişimleri

BT uzmanı/yöneticisi olarak, [Microsoft 365 yönetim merkezi Intune kayıtlı Windows 10 cihazlarda](/mem/intune/enrollment/device-enrollment) tehdit algılamaları hakkındaki bilgileri görüntüleyebilirsiniz. Özet bilgileri görürsünüz, örneğin:

- Kaç cihaz virüsten koruma gerekiyor?
- Kaç cihazın güvenlik ilkeleriyle uyumlu olmadığı
- Şu anda etkin, azaltılmış veya çözümlenmiş kaç tehdit var?

Tehdit algılamaları ve cihazları hakkında belirli bilgileri görüntülemek için çeşitli seçenekleriniz vardır:

- <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> **Etkin cihazlar** sayfası. Bu [makalenin Etkin cihazlar sayfasındaki Tehdit algılamalarını yönetme bölümüne](#manage-threat-detections-on-the-active-devices-page) bakın.
- <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> **Etkin tehditler** sayfası. Bu [makalenin Etkin tehditler sayfasındaki Tehdit algılamalarını yönetme bölümüne](#manage-threat-detections-on-the-active-threats-page) bakın.
- <a href="https://go.microsoft.com/fwlink/p/?linkid=2150463" target="_blank">Microsoft Endpoint Manager'deki</a> **Virüsten Koruma** sayfası. Bu [makaledeki Microsoft Endpoint Manager tehdit algılamalarını yönetme](#manage-threat-detections-in-microsoft-endpoint-manager) bölümüne bakın.

Daha fazla bilgi edinmek için bkz. [Microsoft Defender Virüsten Koruma tarafından algılanan tehditler](threats-detected-defender-av.md).

## <a name="manage-threat-detections-on-the-active-devices-page"></a>**Etkin cihazlar** sayfasında tehdit algılamalarını yönetme

Aşağıdaki yordam, Microsoft 365 İş Ekstra sahip müşteriler için geçerlidir.

1. konumundaki Microsoft 365 yönetim merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> gidin ve oturum açın.

2. Gezinti sayfasında **CihazlarAkaktif** >  cihazlar'ı seçin. Koruma durumu, virüsten koruma (AV) koruma durumu ve algılanan etkin tehdit sayısı gibi etkin cihazların ve ayrıntıların listesini görürsünüz.

3. Bu cihaz ve kullanılabilir eylemler hakkında daha fazla ayrıntı görüntülemek için bir cihaz seçin. **Güncelleştirme ilkesi, Güncelleştirme** **virüsten koruma**, **Hızlı tarama çalıştır**, **Tam tarama çalıştır** ve daha fazlası gibi öneriler ve kullanılabilir eylemler içeren bir açılır öğe açılır.

## <a name="manage-threat-detections-on-the-active-threats-page"></a>Etkin tehditler sayfasında tehdit **algılamalarını** yönetme

Aşağıdaki yordam, Microsoft 365 İş Ekstra sahip müşteriler için geçerlidir. [Windows 10 cihazların güvenli hale getirilmesi](../setup/secure-win-10-pcs.md) ve [Intune kaydedilmesi](/mem/intune/enrollment/windows-enrollment-methods) gerekir.

> [!NOTE]
> **Microsoft Defender Virüsten Koruma** kartı ve **Etkin tehditler** sayfası aşamalar halinde dağıtılıyor, bu nedenle bunlara hemen erişiminiz olmayabilir.

1. konumundaki Microsoft 365 yönetim merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> gidin ve oturum açın.

2. **Microsoft Defender Virüsten Koruma** kartında **Etkin tehditleri görüntüle'yi** seçin. (Alternatif olarak, gezinti bölmesinde **Sistem Durumu'na** >  tıklayın **Tehditler & virüsten koruma**.)

3. **Etkin tehditler** sayfasında algılanan bir tehdit seçerek bu tehdit hakkında daha fazla bilgi edinin. Etkilenen cihazlar da dahil olmak üzere bu tehditle ilgili ayrıntıları içeren bir açılır öğe açılır.

4. Açılır öğede, **Güncelleştirme ilkesi, Güncelleştirme** **virüsten koruma**, **Hızlı tarama çalıştır** ve daha fazlası gibi kullanılabilir eylemleri görüntülemek için bir cihaz seçin.

## <a name="actions-you-can-take"></a>Gerçekleştirebileceğiniz eylemler

Belirli tehditler veya cihazlar hakkındaki ayrıntıları görüntülediğinizde önerileri ve gerçekleştirebileceğiniz bir veya daha fazla eylemi görürsünüz. Aşağıdaki tabloda, görebileceğiniz eylemler açıklanmaktadır.<br><br>

| Eylem | Açıklama |
|--|--|
| Korumayı yapılandırma | Tehdit koruma ilkelerinizin yapılandırılması gerekir. İlke yapılandırma sayfanıza gitmek için bağlantıyı seçin.<br><br>Yardıma mı ihtiyacınız var? Bkz. [Microsoft Intune uç nokta güvenlik ilkeleriyle cihaz güvenliğini yönetme](/mem/intune/protect/endpoint-security-policy). |
| İlkeyi güncelleştirme | Virüsten koruma ve gerçek zamanlı koruma ilkelerinizin güncelleştirilmiş veya yapılandırılmış olması gerekir. İlke yapılandırma sayfasına gitmek için bağlantıyı seçin.<br><br>Yardıma mı ihtiyacınız var? Bkz. [Microsoft Intune uç nokta güvenlik ilkeleriyle cihaz güvenliğini yönetme](/mem/intune/protect/endpoint-security-policy). |
| Hızlı tarama çalıştırma | Kayıt defteri anahtarları ve bilinen Windows başlangıç klasörleri gibi kötü amaçlı yazılımların kaydedilebileceği yaygın konumlara odaklanarak cihazda hızlı bir virüsten koruma taraması başlatır. |
| Tam tarama çalıştırma | Cihazda tam virüsten koruma taraması başlatır ve kötü amaçlı yazılımların kaydedilebileceği yaygın konumlara ve cihazdaki her dosya ve klasöre odaklanır. Sonuçlar [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) gönderilir. |
| Virüsten korumayı güncelleştirme | Cihazın virüsten koruma ve kötü amaçlı yazılımdan koruma için [güvenlik bilgileri güncelleştirmelerini](https://go.microsoft.com/fwlink/?linkid=2149926) alması gerekir. |
| Cihazı yeniden başlatma | Windows 10 cihazı beş dakika içinde yeniden başlatmaya zorlar.<br><br>**ÖNEMLİ:** Cihaz sahibine veya kullanıcıya yeniden başlatma bildirimi otomatik olarak bildirilmez ve kaydedilmemiş çalışmayı kaybedebilir. |

## <a name="manage-threat-detections-in-microsoft-endpoint-manager"></a>Microsoft Endpoint Manager'de tehdit algılamalarını yönetme

Tehdit algılamalarını yönetmek için Microsoft Endpoint Manager kullanabilirsiniz. Windows 10 cihazların Intune (Microsoft Endpoint Manager parçası) [olarak kaydedilmesi](/mem/intune/enrollment/windows-enrollment-methods) gerekir.

1. konumundaki Microsoft Endpoint Manager yönetim merkezine <a href="https://go.microsoft.com/fwlink/p/?linkid=2150463" target="_blank">https://endpoint.microsoft.com</a> gidin ve oturum açın.

2. Gezinti bölmesinde **Uç nokta güvenliği'ni** seçin.

3. **Yönet'in** altında **Virüsten Koruma'yı** seçin. **Özet**, **Windows 10 iyi durumda olmayan uç noktalar** ve **algılanan kötü amaçlı yazılım Windows 10** gibi çeşitli sekmeler görürsünüz.

4. Kullanılabilir sekmelerdeki bilgileri gözden geçirin ve gerekli eylemleri gerçekleştirin.

Örneğin, cihazların **algılanan Windows 10 kötü amaçlı yazılım** sekmesinde listelendiğini varsayalım. Bir cihaz seçtiğinizde **, Yeniden Başlatma**, **Hızlı Tarama**, **Tam Tarama**, **Eşitleme** veya **İmzaları güncelleştirme** gibi bazı eylemleriniz olur. Bu cihaz için bir eylem seçin.

Aşağıdaki tabloda, Microsoft Endpoint Manager'da görebileceğiniz eylemler açıklanmaktadır.<br><br>

| Eylem | Açıklama |
|--|--|
| Yeniden başlatma | Windows 10 cihazı beş dakika içinde yeniden başlatmaya zorlar.<br><br>**ÖNEMLİ:** Cihaz sahibine veya kullanıcıya yeniden başlatma bildirimi otomatik olarak bildirilmez ve kaydedilmemiş çalışmayı kaybedebilir. |
| Hızlı Tarama | Kayıt defteri anahtarları ve bilinen Windows başlangıç klasörleri gibi kötü amaçlı yazılımların kaydedilebileceği yaygın konumlara odaklanarak cihazda hızlı bir virüsten koruma taraması başlatır. Sonuçlar [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) gönderilir. |
| Tam Tarama | Cihazda tam virüsten koruma taraması başlatır ve kötü amaçlı yazılımların kaydedilebileceği yaygın konumlara ve cihazdaki her dosya ve klasöre odaklanır. Sonuçlar [Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) gönderilir. |
| Eşitleme | Intune (Microsoft Endpoint Manager bir parçası) ile giriş yapmak için bir cihaz gerektirir. Cihaz iade ettiğinde, cihaza atanan bekleyen eylemleri veya ilkeleri alır. |
| İmzaları güncelleştirme | Cihazın virüsten koruma ve kötü amaçlı yazılımdan koruma için [güvenlik bilgileri güncelleştirmelerini](https://go.microsoft.com/fwlink/?linkid=2149926) alması gerekir. |

> [!TIP]
> Daha fazla bilgi için bkz. [Cihazlar için uzak eylemler](/mem/intune/protect/endpoint-security-manage-devices#remote-actions-for-devices).

## <a name="how-to-submit-a-file-for-malware-analysis"></a>Kötü amaçlı yazılım analizi için dosya gönderme

Kaçırıldığını veya yanlış şekilde kötü amaçlı yazılım olarak sınıflandırıldığını düşündüğünüz bir dosyanız varsa, bu dosyayı kötü amaçlı yazılım analizi için Microsoft'a gönderebilirsiniz. Kullanıcılar ve BT yöneticileri analiz için bir dosya gönderebilir. adresini ziyaret edin [https://www.microsoft.com/wdsi/filesubmission](https://www.microsoft.com/wdsi/filesubmission).

## <a name="see-also"></a>Ayrıca bkz.

[İş planları için Microsoft 365 güvenliğini sağlamaya yönelik en iyi yöntemler](../../admin/security-and-compliance/secure-your-business-data.md)

[İş için Microsoft Defender genel bakış](../../security/defender-business/mdb-overview.md) (Defender for Business, 1 Mart 2022'de başlayarak Microsoft 365 İş Ekstra müşterilerine dağıtılıyor)