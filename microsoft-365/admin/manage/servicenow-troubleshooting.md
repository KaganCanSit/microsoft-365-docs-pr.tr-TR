---
title: ServiceNow Microsoft 365 destek tümleştirmesi sorunlarını giderme
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: ServiceNow için Kapsam Sertifikalı uygulama yükleme ve yapılandırma kılavuzu.
ms.openlocfilehash: 24813fe0d0705d9404fa465420e3b0344f43f953
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989922"
---
# <a name="troubleshooting-microsoft-365-support-integration-with-servicenow"></a>ServiceNow Microsoft 365 destek tümleştirmesi sorunlarını giderme

| \#  | Sorun  | Tanılama eylemi     |
|-----|--------------------------------|----------------------|
| 1   | Destek sekmesini **Microsoft 365** göremiyorum                                                                                                                                                                                    |  &gt; Filtre xmiomsm365assit\_\_ ile geçerli görünümü ve Sistem Günlükleri'nin hepsini doğrulama \_                        |
| 2   | **Microsoft tarafından önerilen çözümler'i** seçin ancak "Lütfen ServiceNow yöneticinize başvurarak uygulamanın kurulum adımlarını tamamlamalarını sorun" hatasını alabilirsiniz.                                                                      | Formun üst kısmında yer alan hata iletisini ve filtre  &gt; xmiomsm365assit \_\_\_ile Tüm Sistem Günlükleri'ne bakabilirsiniz     |
| 3   | **Microsoft tarafından önerilen çözümler'i** seçin ancak "Lütfen ServiceNow yöneticinize başvurarak uygulamanın son ayarlama adımını tamamlamalarını sorun" hatasını alabilirsiniz.                                                                | Formun üst kısmında yer alan hata iletisini ve filtre  &gt; xmiomsm365assit \_\_\_ile Tüm Sistem Günlükleri'ne bakabilirsiniz     |
| 4   | Sorunu arama kutusuna yazın ve **Microsoft** tarafından önerilen çözümler'i seçin, ancak "Lütfen ServiceNow yöneticinize başvurarak uygulamanın kurulum adımlarını tamamlamalarını sorun" hatasını alabilirsiniz.                                   | Formun üst kısmında yer alan hata iletisini ve filtre  &gt; xmiomsm365assit \_\_\_ile Tüm Sistem Günlükleri'ne bakabilirsiniz     |
| 5   | Arama kutusuna sorun yazın ve **Microsoft** tarafından önerilen çözümler'i seçin, ancak "Lütfen ServiceNow yöneticinize başvurarak uygulamanın son ayarlama adımını tamamlamalarını sorun" hatasını alabilirsiniz.                                 | Formun üst kısmında yer alan hata iletisini ve filtre  &gt; xmiomsm365assit \_\_\_ile Tüm Sistem Günlükleri'ne bakabilirsiniz     |
| 6   | **Microsoft desteğine başvurun'u** seçin, ancak "Lütfen ServiceNow yöneticinize başvurun ve uygulamanın kurulum adımlarını tamamlamalarını sorun" hatasını alabilirsiniz.                                                                       | Formun üst kısmında yer alan hata iletisini ve filtre  &gt; xmiomsm365assit \_\_\_ile Tüm Sistem Günlükleri'ne bakabilirsiniz     |
| 7   | **Microsoft desteğine başvurun'u** seçin, ancak "Lütfen ServiceNow yöneticinize başvurun ve uygulamanın son ayarlama adımını tamamlamalarını sorun" hatasını alabilirsiniz.                                                                 | Formun üst kısmında yer alan hata iletisini ve filtre  &gt; xmiomsm365assit \_\_\_ile Tüm Sistem Günlükleri'ne bakabilirsiniz     |
| 8   | **Microsoft desteğine başvurun'u** seçin ancak "{EmailAddress} geçerli bir yönetici Microsoft 365 alın. Hizmet Microsoft 365 için yönetici ayrıcalıklarına sahip olmanız gerekir. Uygulamada yönetici hesabıyla bağlantı açın." | Formun üst kısmında yer alan hata iletisini ve filtre  &gt; xmiomsm365assit \_\_\_ile Tüm Sistem Günlükleri'ne bakabilirsiniz     |
| 9   | **Microsoft tarafından önerilen çözümler'i seçin** ancak hiçbir şey ortaya çıktı                                                                                                                                                            | Sistem **Günlüklerini Denetleme – Filtre uygulama ve** filtre uygulama login.microsoftonline.com Giden HTTP connector.rave.microsoft.com |
| 10  | **Microsoft tarafından önerilen çözümler'i seçin** ancak "Lütfen uygulama desteğine başvurun" hatasını alabilirsiniz.                                                                                                                                     | Formun üst kısmında yer alan hata iletisini ve filtre  &gt; xmiomsm365assit \_\_\_ile Tüm Sistem Günlükleri'ne bakabilirsiniz     |
| 11  | Arama kutusuna sorun yazın ve Microsoft tarafından **önerilen çözümler'i seçin** ancak hiçbir şey ortaya çıktı                                                                                                                             | Sistem **Günlüklerini Denetleme – Filtre uygulama ve** filtre uygulama login.microsoftonline.com Giden HTTP connector.rave.microsoft.com |
| 12  | Arama kutusuna sorun yazın ve Microsoft tarafından önerilen **çözümler'i seçin** , ancak "Lütfen uygulama desteğine başvurun" hatasını alabilirsiniz.                                                                                                      | Formun üst kısmında yer alan hata iletisini ve filtre  &gt; xmiomsm365assit \_\_\_ile Tüm Sistem Günlükleri'ne bakabilirsiniz     |
| 13  | Kullanıcı Microsoft **desteğine başvurun'u seçer** ancak hiçbir şey olmaz                                                                                                                                                            | Sistem **Günlüklerini Denetleme – Filtre uygulama ve** filtre uygulama login.microsoftonline.com Giden HTTP connector.rave.microsoft.com |
| 14  | Olayı yeniden açtıktan sonra Microsoft'un önerilen çözümü göremiyorum                                                                                                                                                      | Filtre  xmiomsm365assit\_ &gt; ile\_ Tüm Sistem Günlüklerini\_ Denetleme                                              |
| 15  | Microsoft desteğine aktarılan olayı yeniden a açılırken Microsoft davalarını göremiyorum                                                                                                                            | Filtre  xmiomsm365assit\_ &gt; ile\_ Tüm Sistem Günlüklerini\_ Denetleme                                              |
| 16  | Bilet ayrıntıları kaydedemiyorsanız" hatasını alabilirsiniz "Bilet ayrıntıları kaydedemedi. Lütfen Uygulama desteğine başvurun."                                                                                                                          | Formun üstünde hata iletisini denetleme                                                                            |
