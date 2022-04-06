---
title: Algılanan tehditleri gözden geçirme ve önlem alma
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
description: Mobil cihazlarınıza güvenlik tarafından algılanan tehditleri Microsoft Defender Virüsten Koruma ve yönetmeyi Windows 10 öğrenin.
ms.openlocfilehash: c836554445f56a9a915885d55a4490c6bb5bd1a9
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64633227"
---
# <a name="review-detected-threats-and-take-action"></a>Algılanan tehditleri gözden geçirme ve önlem alma

Kötü amaçlı bir dosya veya yazılım algılandığında, Microsoft Defender Virüsten Koruma bu dosyayı engeller ve çalıştırmasını engeller. Bulut teslimi koruması açıksa, virüsten koruma ve kötü amaçlı yazılımdan koruma altyapısına yeni algılanan tehditler eklenir ve böylelikle diğer cihazlarınız ve kullanıcılarınız da korunur.

Microsoft Defender Virüsten Koruma tehditlere karşı şunları algılar ve korur:

- Virüsler, kötü amaçlı yazılımlar ve cihazlara yönelik web tabanlı tehditler
- Kimlik avı girişimleri
- Veri hırsızlığı girişimleri

Bir IT uzmanı/yöneticisi olarak, aynı kullanıcıya Windows 10 cihazlarında tehdit algılamaları [](/mem/intune/enrollment/device-enrollment) Intune bilgileri Microsoft 365 yönetim merkezi. Aşağıdakiler gibi özet bilgileri burada görüyorsunuz:

- Virüsten koruma yazılımına ihtiyaç kaç cihaz gerekiyor?
- Kaç cihaz güvenlik ilkeleriyle uyumlu değil
- Şu anda etkin, risk azaltmaya yönelik veya çözümlenmiş durumda kaç tehdit var

Tehdit algılamaları ve cihazlar hakkında belirli bilgileri görüntülemek için çeşitli seçenekleriniz vardır:

- Sayfanın **Etkin** cihazlar <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a>. Bu [makalenin Etkin cihazlarda tehdit algılamalarını yönetme](#manage-threat-detections-on-the-active-devices-page) sayfasına bakın.
- Sayfanın **Etkin tehdit** <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a>. Bu [makalenin Etkin tehdit algılamalarını yönetme sayfasındaki Tehdit algılamalarını](#manage-threat-detections-on-the-active-threats-page) yönetme makalesine bakın.
- **Virüsten Koruma** sayfası <a href="https://go.microsoft.com/fwlink/p/?linkid=2150463" target="_blank">Microsoft Endpoint Manager</a>. Bu [makaledeki Yeni E-posta Microsoft Endpoint Manager](#manage-threat-detections-in-microsoft-endpoint-manager) algılamalarını yönetme makalesine bakın.

Daha fazla bilgi için bkz. [Güvenlik tarafından algılanan Microsoft Defender Virüsten Koruma](threats-detected-defender-av.md).

## <a name="manage-threat-detections-on-the-active-devices-page"></a>Etkin cihazlar sayfasında tehdit **algılamalarını** yönetme

Aşağıdaki yordam, bu yordama sahip olan Microsoft 365 İş Ekstra.

1. Oturum Microsoft 365 yönetim merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> gidin.

2. Gezinti sayfasında Cihazlar Etkin **Cihazlar'ı** >  **seçin**. Koruma durumu, virüsten koruma (AV) koruma durumu ve algılanan etkin tehdit sayısı gibi etkin cihazların ve ayrıntıların listesini görüntülenir.

3. Bir cihaz ve kullanılabilir eylemler hakkında daha fazla ayrıntı görüntülemek için o cihazı seçin. Önerilerin ve İlkeyi güncelleştir, Virüsten korumayı **güncelleştir, Hızlı** tarama çalıştır, Tam tarama çalıştır ve daha fazlası gibi eylemlerin yer **olduğu bir açılır** pencere açılır.

## <a name="manage-threat-detections-on-the-active-threats-page"></a>Etkin tehdit sayfasında tehdit **algılamalarını** yönetme

Aşağıdaki yordam, bu yordama sahip olan Microsoft 365 İş Ekstra. [Windows 10 cihazları güvenlik altına alınarak](../setup/secure-win-10-pcs.md) [başka bir cihaza Intune](/mem/intune/enrollment/windows-enrollment-methods).

> [!NOTE]
> Yeni **Microsoft Defender Virüsten Koruma** ve Etkin tehdit sayfası aşamalar içinde yuvarlanıyor, dolayısıyla bu karta hemen erişiminiz yok olabilir.

1. Oturum Microsoft 365 yönetim merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> gidin.

2. Güvenlik **Microsoft Defender Virüsten Koruma Tehditleri** **görüntüle'yi seçin**. (Alternatif olarak, gezinti bölmesinde Durum'ı **seçin** >  **Tehdit & virüsten koruma**.)

3. Etkin **tehditler sayfasında** , bu tehdit hakkında daha fazla bilgi edinmek için algılanan bir tehdit seçin. Hangi cihazların etkilendiği de dahil olmak üzere bu tehditle ilgili ayrıntıları içeren bir açılır pencere açılır.

4. Çıkışta, İlkeyi güncelleştir, Virüsten koruma güncelleştirme, Hızlı tarama çalıştır ve daha fazlası gibi kullanılabilir eylemleri görüntülemek **için bir** cihaz seçin.

## <a name="actions-you-can-take"></a>Gerçekleştir işlemler

Belirli tehditlere veya cihazlara ilişkin ayrıntıları görüntüde, önerileri ve gerçekleştirebilirsiniz. Aşağıdaki tabloda, gördüğünüz eylemler açık almaktadır.<br><br>

| Eylem | Açıklama |
|--|--|
| Korumayı yapılandırma | Tehdit koruması ilkelerinizin yapılandırılması gerekir. İlke yapılandırma sayfanıza gitmek için bağlantıyı seçin.<br><br>Yardıma mı ihtiyacınız var? Daha [fazla bilgi için bkz. Cihaz güvenliğini uç nokta güvenlik ilkeleriyle Microsoft Intune](/mem/intune/protect/endpoint-security-policy). |
| İlkeyi güncelleştirme | Virüsten koruma ve gerçek zamanlı koruma ilkelerinizin güncelleştirilmiş veya yapılandırılmış olması gerekir. İlke yapılandırma sayfasına gitmek için bağlantıyı seçin.<br><br>Yardıma mı ihtiyacınız var? Daha [fazla bilgi için bkz. Cihaz güvenliğini uç nokta güvenlik ilkeleriyle Microsoft Intune](/mem/intune/protect/endpoint-security-policy). |
| Hızlı taramayı çalıştırma | Cihazda hızlı bir virüsten koruma taraması başlatır, kayıt defteri anahtarları ve bilinen veya başlangıç klasörleri gibi kötü amaçlı yazılım kaydedileme Windows olur. |
| Tam taramayı çalıştır | Cihazda tam virüsten koruma taraması başlatır, kötü amaçlı yazılımların kaydedil olduğu yaygın konumlara odaklanarak ve cihaza her dosya ve klasörü dahil edin. Sonuçlar [diğer Microsoft Endpoint Manager.](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) |
| Virüsten koruma yazılımını güncelleştirme | Virüsten koruma ve kötü [amaçlı yazılımlardan koruma için](https://go.microsoft.com/fwlink/?linkid=2149926) güvenlik zekası güncelleştirmelerini almak için cihazı gerektirir. |
| Cihazı yeniden başlat | Bir Windows 10 dakika içinde yeniden başlatılmasını gerektirir.<br><br>**ÖNEMLİ:** Cihaz sahibine veya kullanıcıya yeniden başlatma işlemi otomatik olarak bildirilir ve bu, çalışmanızı kaybetmeye neden olabilir. |

## <a name="manage-threat-detections-in-microsoft-endpoint-manager"></a>Yeni bir e-postada tehdit algılamalarını Microsoft Endpoint Manager

Tehdit algılamalarını Microsoft Endpoint Manager için bu özelliği kullanabilirsiniz. Windows 10 [cihazlarının Intune](/mem/intune/enrollment/windows-enrollment-methods) (Microsoft Endpoint Manager.

1. Şu anda Microsoft Endpoint Manager merkezine gidin <a href="https://go.microsoft.com/fwlink/p/?linkid=2150463" target="_blank">https://endpoint.microsoft.com</a> ve oturum açma.

2. Gezinti bölmesinde Uç nokta **güvenliği'ni seçin**.

3. **Yönet'in altında** Virüsten **Koruma'ya seçin**. Özet, sağlıksız uç noktaları **düzenleme ve kötü** **amaçlı yazılım** Windows 10 gibi **Windows 10 sekmeler vardır**.

4. Kullanılabilir sekmelerde yer alan bilgileri gözden geçirin ve sonra gerekli eylemi yapın.

Örneğin, cihazların kötü amaçlı yazılım algılandı **sekmesinde Windows 10 olduğunu varsayalım**. Bir cihaz seçin; Yeniden Başlat, Hızlı Tarama, Tam **Tarama, Eşitleme** veya İmzaları güncelleştir **gibi bazı eylemleri** **gerçekleştirebilirsiniz**.  Bu cihaz için bir eylem seçin.

Aşağıdaki tabloda, bu tabloda sizin 2013'te Microsoft Endpoint Manager.<br><br>

| Eylem | Açıklama |
|--|--|
| Yeniden başlatma | Bir Windows 10 dakika içinde yeniden başlatılmasını gerektirir.<br><br>**ÖNEMLİ:** Cihaz sahibine veya kullanıcıya yeniden başlatma işlemi otomatik olarak bildirilir ve bu, çalışmanızı kaybetmeye neden olabilir. |
| Hızlı Tarama | Cihazda hızlı bir virüsten koruma taraması başlatır, kayıt defteri anahtarları ve bilinen veya başlangıç klasörleri gibi kötü amaçlı yazılım kaydedileme Windows olur. Sonuçlar [diğer Microsoft Endpoint Manager.](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) |
| Tam Tarama | Cihazda tam virüsten koruma taraması başlatır, kötü amaçlı yazılımların kaydedil olduğu yaygın konumlara odaklanarak ve cihaza her dosya ve klasörü dahil edin. Sonuçlar [diğer Microsoft Endpoint Manager.](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) |
| Eşitleme | Posta kutusuyla (uygulamanın bir Intune) iade etmek için bir cihaz Microsoft Endpoint Manager. Cihaz iade geldiğinde, cihaza atanmış bekleyen eylemleri veya ilkeleri alır. |
| İmzaları güncelleştirme | Virüsten koruma ve kötü [amaçlı yazılımlardan koruma için](https://go.microsoft.com/fwlink/?linkid=2149926) güvenlik zekası güncelleştirmelerini almak için cihazı gerektirir. |

> [!TIP]
> Daha fazla bilgi için bkz [. Cihazlar için uzaktan eylemler](/mem/intune/protect/endpoint-security-manage-devices#remote-actions-for-devices).

## <a name="how-to-submit-a-file-for-malware-analysis"></a>Kötü amaçlı yazılım çözümlemesi için dosya gönderme

Kaçırılmış olduğunu ya da yanlış olarak kötü amaçlı yazılım olarak sınıflandırılmış olduğunu bildiğiniz bir dosyanız varsa, kötü amaçlı yazılım çözümlemesi yapmak için bu dosyayı Microsoft'a gönderebilirsiniz. Kullanıcılar ve IT yöneticileri çözümleme için dosya gönderebilirsiniz. 'ı ziyaret edin [https://www.microsoft.com/wdsi/filesubmission](https://www.microsoft.com/wdsi/filesubmission).

## <a name="see-also"></a>Ayrıca bkz.

[kurumsal planların güvenliğini sağlamanın en Microsoft 365 10 yolu](../../admin/security-and-compliance/secure-your-business-data.md)

[Yeni müşterilere İş için Microsoft Defender](../../security/defender-business/mdb-overview.md) (Defender for Business, 1 Mart 2022 Microsoft 365 İş Ekstra den itibaren müşterilere sunulmaktadır)