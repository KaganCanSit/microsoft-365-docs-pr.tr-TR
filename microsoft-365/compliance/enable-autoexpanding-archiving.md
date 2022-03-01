---
title: Otomatik genişleyen arşivlemeyi etkinleştirme
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: e2a789f2-9962-4960-9fd4-a00aa063559e
description: 'Yöneticiler için: Kullanıcılarınıza kendi posta kutuları için ek depolama alanı sağlayan otomatik genişleyen arşivlemeyi Exchange Online öğrenin. Tüm kuruluş için veya yalnızca belirli kullanıcılar için otomatik genişleyen arşivlemeyi etkinleştirebilirsiniz.'
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c6f1514ed4bb9c12ac666b366cab91358216357a
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010867"
---
# <a name="enable-auto-expanding-archiving"></a>Otomatik genişleyen arşivlemeyi etkinleştirme

Arşiv posta kutuları için Exchange Online depolama alanını etkinleştirmek için otomatik genişleyen otomatik arşivleme özelliğini kullanabilirsiniz. Otomatik genişleyen arşivleme açık olduğunda, kullanıcının 1,5 TB depolama sınırına ulaşana kadar kullanıcının arşiv posta kutusuna otomatik olarak ek depolama alanı eklenir. Otomatik genişleyen arşivlemeyi, kuruluşta herkes için veya yalnızca belirli kullanıcılar için açabilirsiniz. Otomatik genişleyen arşivleme hakkında daha fazla bilgi için bkz[. Otomatik genişleyen arşivleme hakkında bilgi.](autoexpanding-archiving.md)

## <a name="before-you-enable-auto-expanding-archiving"></a>Otomatik genişleyen arşivlemeyi etkinleştirmeden önce

- Siz, sizin için veya belirli bir kullanıcı için otomatik genişleyen arşivlemeyi açtıktan sonra, bu kapatılamaz. Ayrıca yöneticiler, otomatik genişleyen arşivleme için depolama kotasını ayar aşağıdakilere ek olarak ayarlayabilir.

- Otomatik genişleyen arşivlemeyi etkinleştirmek için, kuruluşta genel yönetici veya Exchange Online Kuruluş Yönetimi rol grubunun üyesi olmak gerekir. Alternatif olarak, belirli kullanıcılar için otomatik genişleyen arşivlemeyi etkinleştirmek için Posta Alıcıları rolüne atanmış bir rol grubunun üyesi olmak gerekir.

- Otomatik genişleyen arşivlemeyi etkinleştiremeden önce kullanıcının arşiv posta kutusunun etkinleştirilmiş olması gerekir. Arşiv posta kutusunu etkinleştirmek için kullanıcıya Exchange Online Plan 2 lisansı atanabilir. Bir kullanıcıya Exchange Online Plan 1 lisansı atanırsa, arşiv posta kutusunu etkinleştirmek için kullanıcıya ayrı bir Exchange Online Arşivleme lisansı atamanız gerekir. Bkz [. Arşiv posta kutularını etkinleştirme](enable-archive-mailboxes.md).

- Otomatik genişleyen arşivlemeyi açtıktan sonra, arşiv posta kutusu (Kurtarılabilir Öğeler klasörü de içinde olmak üzere) 90 GB'a ulaştığında arşiv posta kutusu otomatik genişleyen bir arşive dönüştürülür. Ek depolama alanı sağlanması 30 gün kadar zaman alır.

- Arşiv posta kutularını etkinleştirmek için PowerShell'i de kullanabilirsiniz. Tüm [kullanıcılar için](#more-information) arşiv posta kutularını etkinleştirmek üzere kullanabileceğiniz PowerShell komutunun örneği için Daha fazla bilgi bölümüne bakın.

- Otomatik genişleyen arşivleme, paylaşılan posta kutularını da destekler. Paylaşılan bir posta kutusunun arşivini etkinleştirmek için bir Exchange Online Plan 2 lisansı veya Exchange Online lisansı olan bir Exchange Online Arşivleme Lisansı gereklidir.

- Otomatik genişleyen arşivleme, etkin olmayan bir posta kutusunu kurtarmanızı veya geri [yüklemenızı sağlar](inactive-mailboxes-in-office-365.md#what-are-inactive-mailboxes). Bir posta kutusu için otomatik genişleyen arşivlemeyi etkinleştirir ve posta kutusu daha sonraki bir tarihte devre dışı bırakılırsa, etkin olmayan posta kutusunu kurtaramazsınız [(](recover-an-inactive-mailbox.md)etkin bir posta kutusuna dönüştürerek) veya geri yükleyeme (içeriği var olan bir posta [](restore-an-inactive-mailbox.md) kutusuyla birleştirerek) kurtaramazsınız. Etkin olmayan bir posta kutusunda otomatik genişleyen arşivleme etkinleştirildiyse, verileri kurtarmanın tek yolu, verileri posta kutusundan dışarı aktararak başka bir posta kutusuna içeri aktarmak için Microsoft 365 uyumluluk merkezi'daki İçerik arama aracını kullanmaktır. Daha fazla bilgi için, Etkin olmayan posta kutuları hakkında bilgi edinebilirsiniz bölümündeki "Etkin olmayan posta kutuları ve [otomatik genişleyen arşivler" bölümüne bakın](inactive-mailboxes-in-office-365.md#inactive-mailboxes-and-auto-expanding-archives).

- Otomatik genişleyen arşivlemeyi etkinleştirmek Exchange yönetim merkezini veya Microsoft 365 uyumluluk merkezi yönetim merkezini kullanaaaz. Exchange Online PowerShell kullanabilirsiniz. Uzak PowerShell kullanarak Exchange Online bilgisayarınıza bağlanmak için bkz[. Bağlan PowerShell'Exchange Online kullanma](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="enable-auto-expanding-archiving-for-your-entire-organization"></a>Tüm kuruluş için otomatik genişleyen arşivlemeyi etkinleştirme

Tüm kuruluş için otomatik genişleyen arşivlemeyi etkinleştirsiniz. Bu özelliği etkinleştirdikten sonra, var olan kullanıcı posta kutuları ve oluşturulan yeni kullanıcı posta kutuları için otomatik genişleyen arşivleme etkinleştirilir. Kullanıcı posta kutuları  oluşturmada, kullanıcının ana arşiv posta kutusunu etkinleştirerek otomatik genişleyen arşivleme özelliğinin yeni kullanıcı posta kutusunda çalışır.
  
1. [Bağlan'Exchange Online PowerShell'e](/powershell/exchange/connect-to-exchange-online-powershell)

2. Tüm kuruluşta otomatik genişleyen Exchange Online etkinleştirmek için PowerShell'de aşağıdaki komutu çalıştırın.

    ```powershell
    Set-OrganizationConfig -AutoExpandingArchive
    ```

## <a name="enable-auto-expanding-archiving-for-specific-users"></a>Belirli kullanıcılar için otomatik genişleyen arşivlemeyi etkinleştirme

Otomatik genişleyen arşivlemeyi kuruluşta her kullanıcı için etkinleştirmek yerine, yalnızca belirli kullanıcılar için etkinleştirebilirsiniz. Bunu, yalnızca bazı kullanıcıların büyük bir arşiv depolama kapasitesine ihtiyacı olduğundan yapabilirsiniz.
  
Belirli bir kullanıcı için otomatik genişleyen arşivlemeyi etkinleştiriyorsanız ve kullanıcının posta kutusu bekletmede tutularak veya bir bekletme ilkesine atanmışsa, aşağıdaki iki yapılandırma değişikliği yapılır:
  
- Kullanıcının birincil arşiv posta kutusu depolama kotası 10 GB artırıldı (100 GB ile 110 GB arasında). Arşiv uyarısı kotası da 10 GB (90 GB ile 100 GB arasında) artırıldı.

- Kullanıcının birincil posta kutusunda Kurtarılabilir Öğeler klasörünün depolama kotası 10 GB artırıldı (ayrıca 100 GB'tan 110 GB'a da). Kurtarılabilir Öğe uyarı kotası da 10 GB artırıldı (90 GB ile 100 GB arasında). Bu değişiklikler, yalnızca posta kutusu bekletmede olduğunda veya bir bekletme ilkesine atandığı zaman uygulanabilir.

Otomatik genişleyen arşiv sağlamadan önce ortaya çıkabilir depolama sorunları oluşmaması için bu ek alan eklenir. Önceki bölümde  *açıklandığı gibi,*  tüm kuruluş için otomatik genişleyen arşivlemeyi etkinleştirirken ek depolama alanı eklenmez.
  
1. [Bağlan'Exchange Online PowerShell'e](/powershell/exchange/connect-to-exchange-online-powershell)

2. Belirli bir kullanıcı için otomatik Exchange Online arşivlemeyi etkinleştirmek için PowerShell'de aşağıdaki komutu çalıştırın. Daha önce de belirtildiği gibi, kullanıcının otomatik genişleyen arşivlemeyi açamadan önce kullanıcının arşiv posta kutusunun (ana arşiv) etkinleştirilmesi gerekir.

    ```powershell
    Enable-Mailbox <user mailbox> -AutoExpandingArchive
    ```

> [!IMPORTANT]
> Exchange karma dağıtımında, birincil posta kutusu şirket içinde olan ve arşiv posta kutusu bulut tabanlı olan belirli bir kullanıcı için otomatik genişleyen arşivlemeyi etkinleştirmek için **Enable-Mailbox -AutoExpandingArchive** komutunu kullanamalısınız. Bir Exchange karma dağıtımında bulut tabanlı arşiv posta kutuları için otomatik genişleyen arşivlemeyi etkinleştirmek amacıyla, tüm kuruluşta otomatik genişleyen arşivlemeyi etkinleştirmek için Exchange Online PowerShell'de **Set-OrganizationConfig -AutoExpandingArchive** komutunu çalıştırmanız gerekir. Kullanıcının birincil ve arşiv posta kutularının ikisi de bulut tabanlı ise, bu kullanıcı için otomatik genişleyen arşivlemeyi etkinleştirmek üzere **Etkinleştirme-Posta Kutusu -OtomatikExpandingArchive** komutunu kullanabilirsiniz.
  
## <a name="verify-that-auto-expanding-archiving-is-enabled"></a>Otomatik genişleyen arşivlemenin etkinleştirildiğinden emin olun

Otomatik genişleyen arşivlemenin etkinleştirildiğinden emin olmak için, Exchange Online PowerShell'de aşağıdaki komutu çalıştırın.

```powershell
Get-OrganizationConfig | FL AutoExpandingArchiveEnabled
```

Değeri, kuruluş  `True` için otomatik genişleyen arşivlemenin etkinleştirildiğinden işaret ediyor. 
  
Belirli bir kullanıcıda otomatik genişleyen arşivlemenin etkinleştirildiğinden emin olmak için, Exchange Online PowerShell'de çalıştırın.
  
```powershell
Get-Mailbox <user mailbox> | FL AutoExpandingArchiveEnabled
```

Bir değer,  `True` kullanıcı için otomatik genişleyen arşivlemenin etkinleştir olduğunu gösterir.
  
Etkin olmayan posta kutularında otomatik genişleyen arşivlemenin etkinleştirildiğinden emin olmak için, Exchange Online PowerShell'de çalıştırın.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL UserPrincipalName,AutoExpandingArchiveEnabled
```

Değeri, etkin  `True` olmayan posta kutusu için otomatik genişleyen arşivlemenin etkinleştirildiğinden emin olun. Bir değer, `False` otomatik genişleyen arşivlemenin etkinleştirilmemiş olduğunu gösterir.

Otomatik genişleyen arşivlemeyi etkinleştirdikten sonra aşağıdaki şeyleri unutmayın:
  
- Kuruluşu için otomatik genişleyen arşivlemeyi etkinleştirmek amacıyla **Set-OrganizationConfig -AutoExpandingArchive** komutunu çalıştırıyorsanız, tek tek posta kutularında **Etkinleştirme-Posta Kutusu -OtomatikExpandingArchive'yi** çalıştırmanız yoktur. **Set-OrganizationConfig** cmdlet'ini çalıştırarak, kuruluşlarınız için otomatik genişleyen arşivlemeyi etkinleştirmek, kullanıcı posta kutularıki *AutoExpandingArchiveEnabled* özelliğini 'a değiştirmez`True`.

- Benzer şekilde, otomatik genişleyen arşivlemeyi *etkinleştirerek ArchiveQuota ve ArchiveWarningQuota* posta kutusu özelliklerinin değerleri de değişmez. Aslında, kullanıcı posta kutusu için otomatik genişleyen arşivlemeyi etkinleştiriyorsanız ve  *AutoExpandingArchiveEnabled*  `True`özelliği  *olarak ayarlanmışsa ArchiveQuota*  ve  *ArchiveWarningQuota*  özellikleri dikkate alınmaz. Kullanıcının posta kutusunda otomatik genişleyen arşivleme etkinleştirildikten sonra bu posta kutusu özelliklerine bir örnek: 

    ![Otomatik genişleyen arşivlemeyi etkinleştirdikten sonra ArchiveQuota ve ArchiveWarningQuota özellikleri yoksayılır.](../media/6a1c1b69-5c4c-4267-aac8-53577667f03e.png)

## <a name="more-information"></a>Daha fazla bilgi

- Arşiv posta kutularını etkinleştirmek için PowerShell'i de kullanabilirsiniz. Örneğin, arşiv posta kutusu henüz etkinleştirilmemiş olan tüm kullanıcılarda arşiv posta kutularını etkinleştirmek için, Exchange Online PowerShell'de aşağıdaki komutu çalıştırabilirsiniz.

    ```powershell
    Get-Mailbox -Filter {ArchiveStatus -Eq "None" -AND RecipientTypeDetails -eq "UserMailbox"} | Enable-Mailbox -Archive
    ```

- Otomatik genişleyen arşivleme, şirket içi birincil posta kutusu olan kullanıcılar için Exchange bir karma dağıtımda bulut tabanlı arşiv posta kutularında destekler. Ancak bulut tabanlı bir arşiv posta kutusunda otomatik genişleyen arşivleme etkinleştirildikten sonra, posta kutusunu şirket içi arşiv posta kutusuna geri Exchange. Otomatik genişleyen arşivleme, herhangi bir dosya sürümünde şirket içi posta kutularında Exchange Server.

- Kullanıcıların arşiv posta Outlook ek depolama alanında yer alan öğelere erişmek için kullanabileceği Outlook istemcilerinin listesi için, Otomatik genişleyen arşivleme hakkında bilgi edinmek için bkz. "Otomatik genişletilmiş arşivdeki öğelere erişmek için Outlook [gereksinimleri".](autoexpanding-archiving.md#outlook-requirements-for-accessing-items-in-an-auto-expanded-archive)

- Daha önce de açıklanması gerekirse, **Etkinleştir-Posta Kutusu -AutoExpandingArchive** komutunu çalıştırarak kullanıcının birincil arşiv posta kutusunun depolama kotasına (ve posta kutusu saklama varsa Kurtarılabilir Öğeler klasörüne) 10 GB eklenmiştir. Bu, otomatik genişletilmiş depolama alanı sağlanana kadar ek depolama alanı sağlar (bu da 30 gün kadar uzayabilirsiniz). Bu ek depolama alanı, kuruluşun tüm posta kutuları için otomatik genişleyen arşivlemeyi etkinleştirmek amacıyla **Set-OrganizationConfig -AutoExpandingArchive** çalıştırabilirsiniz. Kuruluşun tamamı için otomatik genişleyen arşivlemeyi etkinleştirdiyseniz, ancak belirli bir kullanıcı için ek 10 GB depolama alanı eklemeniz gerekirse, bu posta kutusunda **Etkinleştirme-Posta Kutusu -Otomatik** Arşivleme komutunu çalıştırabilirsiniz. Otomatik genişleyen arşivlemenin zaten etkinleştirilmiştir, ancak ek depolama alanı posta kutusuna eklenir.

> [!IMPORTANT]
> Otomatik genişleyen arşivleme, yalnızca bireysel kullanıcılar tarafından kullanılan posta kutuları için veya günde 1 GB'i aşmaan büyüme hızına sahip paylaşılan posta kutularda destekler. Arşivleme amacıyla iletileri arşiv posta kutusuna kopyalamak için günlük kaydı, aktarım kuralları veya otomatik iletme kuralları kullanımına izin verilmez. Kullanıcının arşiv posta kutusu yalnızca o kullanıcıya yöneliktir. Microsoft, kullanıcının arşiv posta kutusunun diğer kullanıcıların arşiv verilerini depolamak veya uygunsuz kullanım durumlarında depolamak için kullandığı durumlarda ek arşivlemeyi reddetme hakkını sahiptir.
