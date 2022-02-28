---
title: Öncelik hesaplarını yönetme ve izleme
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkMAC
description: İşletmeyi yüksek düzeyde etkileyen hesaplara gönderilen veya bu hesaplardan gönderilen başarısız ve geciktirilen iletileri izleme.
ms.openlocfilehash: b8762885cc54859cf927653abb14858c0094ea12
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988117"
---
# <a name="manage-and-monitor-priority-accounts"></a>Öncelik hesaplarını yönetme ve izleme

Her Microsoft 365 kuruluşta, hassas, özel veya yüksek öncelikli bilgilere erişimi olan yöneticiler, öncüler, yöneticiler veya diğer kullanıcılar gibi temel öneme sahip kişiler vardır.

Bu hesapların kurum tarafından korunmasına yardımcı olmak için, artık belirli kullanıcıları öncelik hesabı olarak hesap edebilir ve onlara ek koruma sağlayan uygulamaya özgü özelliklerden yararlanabilirsiniz. Gelecekte daha fazla uygulama ve özellik öncelik hesaplarını destekleyecektir ve başlangıç olarak iki özellik duyurduk **: öncelik** hesap koruması ve **premium posta akışı izleme**.

- **Öncelik hesabı koruması** - Office 365 için Microsoft Defender (eski adı Office 365 Gelişmiş Tehdit Koruması), öncelik hesaplarını uyarılarda, raporlarda ve soruşturmalarda kullanılan etiketler olarak destekler. Daha fazla bilgi için bkz. Microsoft [Defender Kullanıcı etiketleri ve Office 365](../../security/office-365-security/user-tags.md).

  Doğal bir soru: "Tüm kullanıcılar için bir öncelik yok mu? Tüm kullanıcıları neden öncelik hesabı olarak atamadınız?" Evet, tüm kullanıcılar bir önceliktir, ancak öncelik hesabı koruması aşağıdaki ek avantajları sunar:

  - **Ek iki durumlu bilgiler**: Microsoft veri merkezlerinde posta akışını çözümlememiz, şirket yöneticileri için posta akış modellerinin ortalama çalışandan farklı olduğunu gösterir. Öncelik hesabı koruması, normal bir çalışan için faydalı olmayan, şirket yöneticilerine özel olarak uyarlanmış ek bir yaklaşım sunar.
  - **Raporlamada ek görünürlük**: Aslında, tüm kullanıcıların (veya etkilenen tüm kullanıcıların) bilgileri zaten uyarılarda, raporlarda ve araştırmalarda kullanılabilir. Filtre olarak öncelik hesapları etiketi, özellikle araştırmalarınızı hedeflemenizi sağlar.

- **Premium Posta Flow İzleme** - Sağlıklı posta akışı iş başarısı için çok önemli olabilir ve teslim gecikmeleri veya başarısızlıklar işletmeyi olumsuz yönde etkiliyor olabilir. Başarısız veya gecikmiş e-postalar için bir eşik seçebilir, bu eşik aşılırken uyarı alabilirsiniz ve öncelik hesapları için e-posta sorunlarının raporunu görüntüebilirsiniz. Daha fazla bilgi için [modern EAC'de öncelik hesapları raporu için e-posta sorunları raporunu kontrol edin](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report)

Öncelik hesapları için güvenlikle ilgili en iyi yöntemler için bkz [. Öncelik hesapları için güvenlik önerileri](../../security/office-365-security/security-recommendations-for-priority-accounts.md).

## <a name="before-you-begin"></a>Başlamadan önce

Bu **konu başlığı** altında açıklanan Öncelik hesabı koruma özelliği yalnızca aşağıdaki gereksinimleri karşılaması gereken kuruluşlar tarafından kullanılabilir:

- Office 365, Office 365 E3, Office 365 E5 veya Microsoft 365 E5 sürümüne sahip olanlar da dahil olmak üzere Microsoft 365 E5 Güvenlik için Microsoft Defender.

Bu **Premium açıklanan Flow** Posta Posta İzleme özelliği yalnızca aşağıdaki gereksinimleri karşılaması gereken kuruluşlar tarafından kullanılabilir:

- Aşağıdaki ürünlerin herhangi biri veya birleşiminden en az 5.000 lisans sayısına sahip olması gerekir: Office 365 E3, Microsoft 365 E3, Office 365 E5, Microsoft 365 E5. Örneğin, kuruluşta uygun ürünlerden toplam 5.500 Office 365 E3, 2.500 Microsoft 365 E5 olmak üzere 3.000 Microsoft 365 E5 lisansı olabilir.
- Bir veya daha fazla temel iş yükü için, (Teams, One Drive İş, SharePoint Online, Exchange Online ve Office için, kuruluşun aylık en az 50 etkin kullanıcısı olması gerekir.

> [!NOTE]
> En çok 250 öncelik hesabı izleyebilirsiniz.

Posta kutusuna öncelik hesabı koruması uygulamak için, posta kutusuna erişimi olan kullanıcılara da öncelik hesabı koruması uygulayabilirsiniz (örneğin, CEO'nun ve CEO'nun takvimini yöneten BAŞKAN'ın yönetici yardımcısı).

### <a name="add-priority-accounts-from-the-setup-page"></a>Kurulum sayfasından öncelik hesapları ekleme

Kurulum sayfasından öncelik **hesapları ekleyin**.

1. Microsoft 365 yönetim merkezi gidin<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. **SetupOrganizational** >  **bilgi'ye gidin ve** En önemli **hesaplarınızı** izleme **altında Görüntüle'yi seçin**.

3. **Yönet'Başlarken** **yönet'i seçin**.

4. Öncelik **Hesapları Ekle sayfasında** , arama alanına öncelik hesapları listesine eklemek istediğiniz kişinin adını veya e-posta adresini yazın. Ayrıca, başarısız veya gecikmiş e-postalar için e-posta eşiğini ayarebiliyor ve öncelik hesaplarıyla ilgili sorunların haftalık raporunu alabilirsiniz.

5. Bir kullanıcı seçin ve ardından Kaydet'i **seçin**.

Ayrıca, Etkin kullanıcılar sayfasından öncelik hesapları da ebilirsiniz.

### <a name="add-priority-accounts-from-active-users-page"></a>Etkin kullanıcılar sayfasından öncelik hesapları ekleme

Etkin kullanıcılar sayfasından öncelik hesapları ekleyin.

1. yönetim merkezine gidin <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Kullanıcılar **Etkin** >  **kullanıcılar'a** gidin ve sayfanın en üstünde yer alan üç noktayı (diğer eylemler) seçin. Öncelik **hesaplarını yönet'i seçin**.

3. Hesap **ekle'yi** seçin ve Öncelik Hesapları  Ekle sayfasındaki arama alanına öncelik hesapları listesine eklemek istediğiniz kişinin adını yazın.

4. Bir kullanıcı seçin ve ardından Kaydet'i **seçin**.

## <a name="remove-a-user-from-the-priority-accounts-list"></a>Öncelik hesapları listesinden kullanıcı kaldırma

1. Microsoft 365 yönetim merkezi gidin<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. **SetupOrganizational** >  **bilgi'ye gidin ve** En önemli **hesaplarınızı** izleme **altında Görüntüle'yi seçin**.

3. En çok **hesaplarınızı izle sayfasında,** Bu özelliği **yönet'in altında Öncelik** **hesapları'ı seçin**.

4. Öncelik **hesapları sayfasında** , listeden kaldırmak istediğiniz kullanıcı veya kullanıcıları seçin ve sonra da Hesapları **kaldır'ı seçin**.

## <a name="related-topics"></a>İlgili konular

[Microsoft 365'de Öncelik Hesaplarını Kullanma](https://techcommunity.microsoft.com/t5/microsoft-365-blog/using-priority-accounts-in-microsoft-365/ba-p/1873314)
