---
title: Yasal askıya alma oluşturma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid: MET150
ms.assetid: 39db1659-0b12-4243-a21c-2614512dcb44
description: Bir araştırma sırasında tüm posta kutusu içeriğini koruyarak bir posta kutusunu Dava bekletmeye nasıl yerleştireceğinizi öğrenin.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
ms.openlocfilehash: 8fdb5d8c388399a2ce93281947b5f14782db771b
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64997077"
---
# <a name="create-a-litigation-hold"></a>Yasal askıya alma oluşturma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Silinen öğeler ve değiştirilen öğelerin özgün sürümleri de dahil olmak üzere tüm posta kutusu içeriğini korumak için bir posta kutusunu Dava Tutma'ya yerleştirebilirsiniz. Bir kullanıcı posta kutusunu Dava Tutma'ya yerleştirdiğinizde, kullanıcının arşiv posta kutusunda (etkinse) içerik de korunur. Ayrı tutma oluşturduğunuzda, silinen ve değiştirilen öğelerin belirli bir süre boyunca saklanması ve ardından posta kutusundan kalıcı olarak silinmesi için bir *ayrı tutma süresi (zamana bağlı saklama* olarak da adlandırılır) belirtebilirsiniz. Ya da içeriği süresiz olarak ( *sonsuz ayrı tutma* olarak adlandırılır) veya Dava ayrılığı kaldırılana kadar saklayabilirsiniz. Ayrı tutma süresi belirtirseniz, iletinin alındığı veya posta kutusu öğesinin oluşturulduğu tarihten hesaplanır. 
  
Dava ayrılığı oluşturduğunuzda şunlar olur.
  
- Kullanıcı tarafından kalıcı olarak silinen öğeler, saklama süresince kullanıcının posta kutusunun Kurtarılabilir Öğeler klasöründe tutulur.

- Kullanıcı tarafından Kurtarılabilir Öğeler klasöründen temizlenen öğeler ayrı tutma süresince korunur.

- Kurtarılabilir Öğeler klasörünün depolama kotası 30 GB'tan 110 GB'a yükseltilir.

- Kullanıcının birincil ve arşiv posta kutularındaki öğeler korunur

## <a name="assign-an-exchange-online-plan-2-license"></a>Exchange Online Plan 2 lisansı atama

Bir Exchange Online posta kutusunu Dava bekletmeye yerleştirmek için, Exchange Online Plan 2 lisansı atanmış olmalıdır. Bir posta kutusuna Exchange Online Plan 1 lisansı atanırsa, ayrı bir Exchange Online Arşivleme lisansı atayarak saklamanız gerekir.

> [!NOTE]
> Office 365 Eğitim kuruluşlar için, ek özelliklere sahip Exchange Online Plan 1 lisansı içeren Office 365 A1 aboneliklerde dava tutma desteklenir. Daha fazla bilgi için Office 365 Eğitim [hizmet açıklamasındaki "Exchange Online](/office365/servicedescriptions/office-365-platform-service-description/office-365-education#exchange-online-features) özellikler" bölümüne bakın.

## <a name="place-a-mailbox-on-litigation-hold"></a>Dava bekletmeye posta kutusu yerleştirme

Microsoft 365 yönetim merkezi kullanarak bir posta kutusunu Dava bekletmeye yerleştirme adımları aşağıdadır.

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Microsoft 365 yönetim merkezi</a> gidin ve **KullanıcılarEtkin** >  kullanıcılar'a tıklayın.

2. Dava ayrı tutmaya yerleştirmek istediğiniz kullanıcıyı seçin.

3. Özellikler açılır sayfasında **, Posta** sekmesine tıklayın ve ardından **Diğer eylemler'in** altında **Dava tutmasını yönet'e** tıklayın.

   ![Kullanıcı özellikleri açılır sayfasının Posta sekmesindeKimliği yönet'e tıklayın.](../media/M365AdminCenterLitHold1.png)

4. **Dava bekletmeyi yönet** açılır sayfasında, **Dava bekletmeyi aç** onay kutusunu seçin ve ardından aşağıdaki isteğe bağlı bilgileri girin:

    1. **Saklama süresi (gün):** Zamana dayalı ayrı tutma oluşturmak ve posta kutusu Dava ayrı tutmaya yerleştirildiğinde posta kutusu öğelerinin ne kadar süre tutulacağını belirtmek için bu kutuyu kullanın. Süre, posta kutusu öğesinin alındığı veya oluşturulduğu tarihten hesaplanır. Belirli bir öğe için saklama süresi dolduğunda, bu öğe artık korunmaz. Bu kutuyu boş bırakırsanız, öğeler süresiz olarak veya ayrı tutma kaldırılana kadar korunur. Süreyi belirtmek için gün kullanın.

    2. **Kullanıcıya görünen not**: Bu kutuyu, kullanıcıya posta kutusunun Dava tutmada olduğunu bildirmek için kullanın. Not, Outlook 2010 veya sonraki bir sürümü kullanıyorsa kullanıcının posta kutusunda Hesap Bilgileri sayfasında görünür. Kullanıcılar bu sayfaya erişmek için Outlook'da **Dosya'ya** tıklayabilir.

    3. **Kullanıcı için daha fazla bilgi içeren web sayfası**: Dava tutma hakkında daha fazla bilgi için kullanıcıyı bir web sitesine yönlendirmek için bu kutuyu kullanın. Bu URL, Outlook 2010 veya sonraki bir sürümü kullanıyorsa kullanıcının posta kutusunda Hesap Bilgileri sayfasında görünür. Kullanıcılar bu sayfaya erişmek için Outlook'da **Dosya'ya** tıklayabilir.

. Ayrı tutma oluşturmak için **Dava tutma** açılır sayfasında **Değişiklikleri kaydet'e** tıklayın.

   Sistem, değişikliğin geçerlilik kazanmasının 240 dakika kadar sürebileceğini belirten bir başlık görüntüler.

### <a name="create-a-litigation-hold-using-powershell"></a>PowerShell kullanarak dava tutma oluşturma

Exchange Online [PowerShell'de](/powershell/exchange/connect-to-exchange-online-powershell) aşağıdaki komutu çalıştırarak da bir Dava Tutma oluşturabilirsiniz:

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $true
```

Önceki komut, saklama süresi belirtilmediğinden öğeleri süresiz olarak korur. Aşağıdaki komutu kullanarak zamana dayalı ayrı tutma oluşturmak için:

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $true -LitigationHoldDuration <number of days>
```

Ayrıca, posta kutusunun Dava ayrılığına yerleştirilip yerleştirilmediğini doğrulamak için aşağıdaki komutu da çalıştırabilirsiniz:

```powershell
Get-Mailbox <username> | FL LitigationHoldEnabled
```

*True* değeri, posta kutusunun dava tutmada olduğunu/

Daha fazla bilgi için bkz. [Set-Mailbox](/powershell/module/exchange/set-mailbox).

## <a name="how-does-litigation-hold-work"></a>Dava nasıl çalışır?

Normal silinmiş öğe iş akışında, bir kullanıcı öğeyi kalıcı olarak sildiğinde (Shift + Delete) veya Silinmiş Öğeler klasöründen sildiğinde, posta kutusu öğesi Kurtarılabilir Öğeler klasöründeki Silmeler alt klasörüne taşınır. Silme ilkesi (saklamayı sil eylemiyle yapılandırılmış bir bekletme etiketidir) bekletme süresi dolduğunda öğeleri Silmeler alt klasörüne de taşır. Kullanıcı Kurtarılabilir Öğeler klasöründeki bir öğeyi temizlediğinde veya bir öğe için silinen öğe saklama süresinin süresi dolduğunda, Kurtarılabilir Öğeler klasöründeki Temizlemeler alt klasörüne taşınır ve kalıcı silme için işaretlenir. Posta kutusu Yönetilen Klasör Yardımcısı (MFA) tarafından bir sonraki işlendiğinde Exchange temizlenir.

Bir posta kutusu Dava bekletmesine yerleştirildiğinde, Temizlemeler alt klasöründeki öğeler, Dava ayrı tutması tarafından belirtilen saklama süresi boyunca korunur. Saklama süresi, bir öğenin alındığı veya oluşturulduğu özgün tarihten hesaplanır ve Temizlemeler alt klasöründeki öğelerin ne kadar süre tutulduğunu tanımlar. Temizleme alt klasöründeki bir öğenin saklama süresi dolduğunda, öğe kalıcı silme için işaretlenir ve posta kutusu MFA tarafından bir sonraki işlendiğinde Exchange temizlenir. Bir posta kutusuna süresiz ayrı tutma yerleştirilirse, öğeler hiçbir zaman Temizleme alt klasöründen temizlenmez.

Aşağıdaki çizimde Kurtarılabilir Öğeler klasörlerindeki alt klasörler ve tutma iş akışı işlemi gösterilmektedir.

![Dava yaşam döngüsünü tutar.](../media/LitigationHoldLifeCycle.png)

> [!NOTE]
> eBulma olayıyla ilişkili bir ayrı tutma bir posta kutusuna yerleştirilirse, temizlenen öğeler Silmeler alt klasöründen DiscoveryHolds alt klasörüne taşınır ve posta kutusu eBulma ayrılığından çıkana kadar korunur.
