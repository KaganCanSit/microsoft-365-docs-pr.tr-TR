---
title: Mahkeme tutma oluşturma
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
description: Bir posta kutusunu mahkemeler için tutma ve araştırma sırasında tüm posta kutusu içeriğini koruma hakkında bilgi alın.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
ms.openlocfilehash: d105813d7e34ece7641421bc7fed10919dda618e
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021609"
---
# <a name="create-a-litigation-hold"></a>Mahkeme tutma oluşturma

Silinmiş öğeler ve değiştirilen öğelerin özgün sürümleri de dahil olmak üzere tüm posta kutusu içeriğini tutmak için posta kutusunu Mahkeme'de tutabilirsiniz. Bir kullanıcı posta kutusunu Mahkemeler'i yerinde tutarken, kullanıcının arşiv posta kutusunda (etkinse) içerik de korunur. Bir hold (zaman tabanlı tutma olarak da *adlandırılan) bir* tutma süresi belirtebilirsiniz; böylece silinmiş ve değiştirilmiş öğeler belirtilen süre boyunca korunur ve sonra da posta kutusundan kalıcı olarak silinir. Ya da içeriği süresiz (sonsuz tutma olarak anılır *) veya* Mahkeme tutma kaldırılana kadar tutabilirsiniz. Bir iletiyi tutma süresi belirtirse, iletinin teslim aldığı veya posta kutusu öğesinin oluşturulmuş olduğu tarihten itibaren hesaplanır. 
  
Mahkeme tutma 2013 2013'e 2013'e kadar farklı bir süre için 2013'e kadar süreye sahip olurken aşağıdakiler olur.
  
- Kullanıcı tarafından kalıcı olarak silinen öğeler, tutma süresince kullanıcının posta kutusunda Kurtarılabilir Öğeler klasöründe korunur.

- Kullanıcı tarafından Kurtarılabilir Öğeler klasöründen temizlenebilir öğeler, tutma süresi boyunca korunur.

- Kurtarılabilir Öğeler klasörünün depolama kotası 30 GB'tan 110 GB'a artırıldı.

- Kullanıcının birincil ve arşiv posta kutularında yer alan öğeler korunur

## <a name="assign-an-exchange-online-plan-2-license"></a>Plan 2 Exchange Online lisansı atama

Bir posta kutusunu Exchange Online yerinde tutmak için bu posta kutusuna Bir Lisans 2 Exchange Online atanmış olması gerekir. Bir posta kutusuna Exchange Online Plan 1 lisansı atanırsa bu posta kutusuna ayrı bir Exchange Online Arşivleme lisansı atamanız gerekir.

> [!NOTE]
> Diğer Office 365 Eğitim için, ek özelliklere sahip Office 365 A1 Plan 1 lisansı içeren Exchange Online abonelikleri için Mahkeme tutma özelliği de de geçerlidir. Daha fazla bilgi için, hizmet Exchange Online bölümünde yer [alan "Office 365 Eğitim" bölümüne bakın](/office365/servicedescriptions/office-365-platform-service-description/office-365-education#exchange-online-features).

## <a name="place-a-mailbox-on-litigation-hold"></a>Mahkemeler'de posta kutusunu yerinde tutma

Aşağıdaki adımları kullanarak, posta kutusunu Mahkeme'de tutmak için Microsoft 365 yönetim merkezi.

1. Etkin <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Kullanıcılar'a Microsoft 365 yönetim merkezi</a> Etkin **Kullanıcılar'a** >  **tıklayın**.

2. Mahkeme tutma için kullanmak istediğiniz kullanıcıyı seçin.

3. Özellikler açılır sayfasında Posta sekmesine tıklayın **ve Diğer** eylemler'in **altında Mahkeme** tutmayı **yönet'e tıklayın**.

   ![Kullanıcı özellikleri açılır sayfasının Posta sekmesinde Mahkemeyi yönet'e tıklayın.](../media/M365AdminCenterLitHold1.png)

4. Mahkeme **tutma tutmalarını yönet** sayfasında, Mahkeme tutmada aç onay kutusunu  seçin ve sonra aşağıdaki isteğe bağlı bilgileri girin:

    1. **Tutma süresi (gün)**: Zaman tabanlı bir tutma oluşturmak ve posta kutusu mahkemelere yerleştirilirken posta kutusu öğelerinin ne kadar süreyle tutulacaklarını belirtmek için bu kutuyu kullanın. Süre, posta kutusu öğesinin alın aldığı veya oluşturduğu tarihten itibaren hesaplanır. Belirli bir öğe için tutma süresi sona erdiğinde, bu öğe artık korunmaz. Bu kutuyu boş bırakırsanız, öğeler süresiz olarak veya tutma kaldırılana kadar korunur. Süreyi belirtmek için günleri kullanın.

    2. **Kullanıcıya görünür not**: Bu kutuyu kullanarak, posta kutusunun mahkemeler için tutmada olduğunu kullanıcıya bildirebilirsiniz. Bu not, 2010 veya daha yeni bir hesap kullanıyorsa kullanıcının posta kutusunun Hesap Bilgileri Outlook görünür. Bu sayfaya erişmek için, kullanıcılar Dosya'yı **veya Dosya'yı** Outlook.

    3. **Kullanıcıya yönelik daha fazla bilgiyle birlikte web sayfası**: Mahkeme tutma hakkında daha fazla bilgi için bu kutuyu kullanarak bir web sitesine yönlendirin. Bu URL, 2010 veya daha yeni bir hesap kullanıyorsa kullanıcının posta kutusunun Outlook sayfasında görünür. Bu sayfaya erişmek için, kullanıcılar Dosya'yı **veya Dosya'yı** Outlook.

. Tutma **oluşturmak için** **Mahkeme tutma uç sayfası** Üzerinde Değişiklikleri kaydet'e tıklayın.

   Sistem, değişikliğin etkin bir şekilde geçerlik 240 dakika kadar olabileceğini söyleyen bir başlık görüntüler.

### <a name="create-a-litigation-hold-using-powershell"></a>PowerShell kullanarak mahkeme tutma oluşturma

Ayrıca, Exchange Online PowerShell'de aşağıdaki komutu çalıştırarak [da mahkeme Exchange Online oluşturabilirsiniz](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $true
```

Önceki komut, tutma süresi belirtilmemiş olduğundan öğeleri süresiz olarak korur. Zaman tabanlı bir tutma oluşturmak için aşağıdaki komutu kullanın:

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $true -LitigationHoldDuration <number of days>
```

Posta kutusunun Mahkemeler'de tutma amaçlı olarak yerleştiril olduğunu doğrulamak için aşağıdaki komutu da çalıştırabilirsiniz:

```powershell
Get-Mailbox <username> | FL LitigationHoldEnabled
```

True değeri *posta kutusunun* mahkemeler için tutmada olduğunu gösterir/

Daha fazla bilgi için bkz. [Set-Mailbox](/powershell/module/exchange/set-mailbox).

## <a name="how-does-litigation-hold-work"></a>Mahkeme tutma nasıl çalışır?

Normal silinmiş öğe iş akışında, kullanıcı öğeyi kalıcı olarak sdiğinde (Shift + Delete) ya da Silinmiş Öğeler klasöründen sildiğinde posta kutusu öğesi Kurtarılabilir Öğeler klasöründeki Silmeler alt klasörüne taşınır. Silme ilkesi (Sil bekletme eylemiyle yapılandırılmış bir bekletme etiketidir), bekletme süresi dolduğunda öğeleri Silmeler alt klasörüne de taşır. Kullanıcı Kurtarılabilir Öğeler klasöründeki bir öğeyi temizlediğinde veya bir öğe için silinen öğe bekletme süresinin süresi dolduğunda, Kurtarılabilir Öğeler klasöründeki Temizlenenler alt klasörüne taşınır ve kalıcı silme için işaretlenir. Posta kutusu bir sonraki Exchange Yönetilen Klasör Yardımcısı (MFA) tarafından işlendiğinde bu alan temizlenecektir.

Posta kutusu Mahkeme tutma üzerine yerleştirilse, Temizleme alt klasörü içinde yer alan öğeler Mahkeme tutma tarafından belirtilen tutma süresi boyunca korunur. Tutma süresi, bir öğenin ilk alındıktan veya oluşturulduktan sonra hesaplanması ve Temizlendir alt klasördeki öğelerin ne kadar süreyle tutulacaklarını tanımlar. Temizlenenler alt klasör'de bir öğenin tutma süresi dolduğunda, öğe kalıcı olarak silinmek üzere işaretlenir ve posta kutusunun MFA tarafından bir sonraki işlenmesinde Exchange'den temizlenir. Posta kutusuna süresiz bir tutma yerleştirilmişse, öğeler hiçbir zaman Temiz temizlir alt klasörden temiz temizlemez.

Aşağıdaki çizimde, Kurtarılabilir Öğeler klasöründeki alt klasörler ve tutma iş akışı işlemi gösterilmiştir.

![Mahkemelere karşı ömür süresi.](../media/LitigationHoldLifeCycle.png)

> [!NOTE]
> eBulma durumuyla ilişkilendirilmiş bir tutma posta kutusuna yerleştirilirse, temizilen öğeler Silmeler alt klasörüne taşınır ve posta kutusu eBulma ayrımı'nın dışında bırakıncaya kadar korunur.
