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
description: 'Yöneticiler için: Kullanıcılarınıza Exchange Online posta kutuları için ek depolama alanı sağlayan otomatik genişletme arşivlemeyi etkinleştirmeyi öğrenin. Otomatik genişletme arşivlemeyi tüm kuruluşunuz için veya yalnızca belirli kullanıcılar için etkinleştirebilirsiniz.'
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7f1155eaf95a8cf814561650acee4784e8c469df
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012776"
---
# <a name="enable-auto-expanding-archiving"></a>Otomatik genişleyen arşivlemeyi etkinleştirme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Arşiv posta kutuları için ek depolama alanı etkinleştirmek için Exchange Online otomatik genişletme arşivleme özelliğini kullanabilirsiniz. Arşivleme otomatik olarak genişletildiğinde, 1,5 TB depolama sınırına ulaşana kadar kullanıcının arşiv posta kutusuna otomatik olarak ek depolama alanı eklenir. Otomatik genişletme arşivlemeyi kuruluşunuzdaki herkes veya yalnızca belirli kullanıcılar için açabilirsiniz. Arşivlemenin otomatik olarak genişletilmesi hakkında daha fazla bilgi için bkz. [Arşivlemeyi otomatik genişletme hakkında bilgi edinin](autoexpanding-archiving.md).

## <a name="before-you-enable-auto-expanding-archiving"></a>Otomatik genişletme arşivlemeyi etkinleştirmeden önce

- Kuruluşunuz veya belirli bir kullanıcı için otomatik genişletme arşivlemeyi açtıktan sonra kapatılamaz. Ayrıca, yöneticiler arşivlemenin otomatik olarak genişletilmesi için depolama kotasını ayarlayamaz.

- Otomatik genişletme arşivlemeyi etkinleştirmek için kuruluşunuzda genel yönetici veya Exchange Online kuruluşunuzda Kuruluş Yönetimi rol grubunun üyesi olmanız gerekir. Alternatif olarak, belirli kullanıcılar için otomatik genişletme arşivlemeyi etkinleştirmek için Posta Alıcıları rolü atanmış bir rol grubunun üyesi olmanız gerekir.

- Otomatik genişletme arşivlemeyi etkinleştirebilmeniz için önce kullanıcının arşiv posta kutusunun etkinleştirilmesi gerekir. Arşiv posta kutusunu etkinleştirmek için kullanıcıya Exchange Online Plan 2 lisansı atanmalıdır. Kullanıcıya Exchange Online Plan 1 lisansı atanırsa, arşiv posta kutusunu etkinleştirmek için kullanıcıya ayrı bir Exchange Online Arşivleme lisansı atamanız gerekir. Bkz [. Arşiv posta kutularını etkinleştirme](enable-archive-mailboxes.md).

- Otomatik genişletme arşivlemeyi açtıktan sonra, arşiv posta kutusu (Kurtarılabilir Öğeler klasörü dahil) 90 GB'a ulaştığında arşiv posta kutusu otomatik olarak genişletilen arşive dönüştürülür. Ek depolama alanının sağlanması 30 güne kadar sürebilir.

- Arşiv posta kutularını etkinleştirmek için PowerShell'i de kullanabilirsiniz. Kuruluşunuzdaki tüm kullanıcılar için arşiv posta kutularını etkinleştirmek için kullanabileceğiniz PowerShell komutunun bir örneği için [Daha fazla bilgi](#more-information) bölümüne bakın.

- Otomatik genişletme arşivleme, paylaşılan posta kutularını da destekler. Paylaşılan posta kutusunun arşivini etkinleştirmek için Exchange Online Plan 2 lisansı veya Exchange Online Arşivleme lisansına sahip bir Exchange Online Plan 1 lisansı gerekir.

- Arşivlemenin otomatik olarak genişletilmesi [, etkin olmayan bir posta kutusunu](inactive-mailboxes-in-office-365.md#what-are-inactive-mailboxes) kurtarmanızı veya geri yüklemenizi engeller. Başka bir deyişle, bir posta kutusu için otomatik genişletme arşivlemeyi etkinleştirirseniz ve posta kutusu daha sonraki bir tarihte devre dışı bırakılırsa, [etkin olmayan posta kutusunu kurtaramaz (etkin bir posta kutusuna](recover-an-inactive-mailbox.md) dönüştürerek) veya [geri yükleyemezsiniz](restore-an-inactive-mailbox.md) (içeriği mevcut bir posta kutusuyla birleştirerek). Etkin olmayan bir posta kutusunda otomatik genişletme arşivleme etkinleştirildiyse, verileri kurtarmanın tek yolu Microsoft Purview uyumluluk portalındaki İçerik arama aracını kullanarak verileri posta kutusundan dışarı aktarmak ve başka bir posta kutusuna aktarmaktır. Daha fazla bilgi için Etkin olmayan posta kutuları [hakkında bilgi edinin bölümündeki "Etkin olmayan posta kutuları](inactive-mailboxes-in-office-365.md#inactive-mailboxes-and-auto-expanding-archives) ve otomatik olarak genişleten arşivler" bölümüne bakın.

- Otomatik genişletme arşivlemeyi etkinleştirmek için Exchange yönetim merkezini veya Microsoft Purview uyumluluk portalını kullanamazsınız. PowerShell'Exchange Online kullanmanız gerekir. Exchange Online PowerShell'e bağlanmak için bkz. [PowerShell'Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="enable-auto-expanding-archiving-for-your-entire-organization"></a>Tüm kuruluşunuz için otomatik genişletme arşivlemeyi etkinleştirme

Tüm kuruluşunuz için otomatik genişletme arşivlemeyi etkinleştirebilirsiniz. Siz etkinleştirdikten sonra, arşivleme otomatik genişletme mevcut kullanıcı posta kutuları ve oluşturulan yeni kullanıcı posta kutuları için etkinleştirilir. Kullanıcı posta kutuları oluştururken, otomatik genişletme arşivleme özelliğinin yeni kullanıcı posta kutusu için çalışması için kullanıcının ana arşiv posta kutusunu etkinleştirdiğinizden emin olun.
  
1. [PowerShell'i Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell)

2. Exchange Online PowerShell'de aşağıdaki komutu çalıştırarak kuruluşunuzun tamamında otomatik genişletme arşivlemeyi etkinleştirin.

    ```powershell
    Set-OrganizationConfig -AutoExpandingArchive
    ```

## <a name="enable-auto-expanding-archiving-for-specific-users"></a>Belirli kullanıcılar için otomatik genişletme arşivlemeyi etkinleştirme

Kuruluşunuzdaki her kullanıcı için otomatik genişletme arşivlemeyi etkinleştirmek yerine, yalnızca belirli kullanıcılar için etkinleştirebilirsiniz. Yalnızca bazı kullanıcıların büyük bir arşiv depolama kapasitesine ihtiyacı olabileceği için bunu yapabilirsiniz.
  
Belirli bir kullanıcı ve kullanıcının posta kutusu ayrı tutmada veya bekletme ilkesine atandığında otomatik genişletme arşivlemeyi etkinleştirdiğinizde, aşağıdaki iki yapılandırma değişikliği yapılır:
  
- Kullanıcının birincil arşiv posta kutusu için depolama kotası 10 GB artırılır (100 GB'tan 110 GB'a). Arşiv uyarı kotası da 10 GB artırılır (90 GB'tan 100 GB'a).

- Kullanıcının birincil posta kutusunda Kurtarılabilir Öğeler klasörünün depolama kotası 10 GB artırılır (ayrıca 100 GB'tan 110 GB'a kadar). Kurtarılabilir Öğeler uyarı kotası da 10 GB artırılır (90 GB'tan 100 GB'a). Bu değişiklikler yalnızca posta kutusu beklemede olduğunda veya bekletme ilkesine atandığında geçerlidir.

Bu ek alan, otomatik olarak genişletilen arşiv sağlanmadan önce oluşabilecek depolama sorunlarını önlemek için eklenir. Önceki bölümde açıklandığı gibi, tüm kuruluşunuz için otomatik genişletme arşivlemeyi etkinleştirdiğinizde ek depolama alanı  *eklenmez*  .
  
1. [PowerShell'i Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell)

2. Belirli bir kullanıcı için otomatik genişletme arşivlemeyi etkinleştirmek için Exchange Online PowerShell'de aşağıdaki komutu çalıştırın. Daha önce açıklandığı gibi, o kullanıcı için otomatik genişletme arşivlemeyi açabilmeniz için önce kullanıcının arşiv posta kutusunun (ana arşiv) etkinleştirilmesi gerekir.

    ```powershell
    Enable-Mailbox <user mailbox> -AutoExpandingArchive
    ```

> [!IMPORTANT]
> Exchange karma dağıtımda, birincil posta kutusu şirket içinde olan ve arşiv posta kutusu bulut tabanlı olan belirli bir kullanıcı için arşivlemeyi otomatik genişletmeyi etkinleştirmek için **Enable-Mailbox -AutoExpandingArchive** komutunu kullanamazsınız. Exchange karma dağıtımda bulut tabanlı arşiv posta kutuları için otomatik genişletme arşivlemeyi etkinleştirmek için, tüm kuruluş için otomatik genişletme arşivlemeyi etkinleştirmek üzere PowerShell'de **Exchange Online Set-OrganizationConfig -AutoExpandingArchive** komutunu çalıştırmanız gerekir. Kullanıcının birincil ve arşiv posta kutuları hem bulut tabanlıysa, o kullanıcı için otomatik genişletme arşivlemeyi etkinleştirmek için **Enable-Mailbox -AutoExpandingArchive** komutunu kullanabilirsiniz.
  
## <a name="verify-that-auto-expanding-archiving-is-enabled"></a>Otomatik genişletme arşivlemenin etkinleştirildiğini doğrulayın

Kuruluşunuzda otomatik genişletme arşivlemenin etkinleştirildiğini doğrulamak için PowerShell'Exchange Online aşağıdaki komutu çalıştırın.

```powershell
Get-OrganizationConfig | FL AutoExpandingArchiveEnabled
```

değeri  `True` , kuruluş için otomatik genişletme arşivlemenin etkinleştirildiğini gösterir. 
  
Otomatik genişletme arşivlemenin belirli bir kullanıcı için etkinleştirildiğini doğrulamak için PowerShell Exchange Online de aşağıdaki komutu çalıştırın.
  
```powershell
Get-Mailbox <user mailbox> | FL AutoExpandingArchiveEnabled
```

değeri  `True` , otomatik genişletme arşivlemenin kullanıcı için etkinleştirildiğini gösterir.
  
Etkin olmayan posta kutuları için otomatik genişletme arşivlemenin etkinleştirilip etkinleştirilmediğini belirlemek için PowerShell'Exchange Online aşağıdaki komutu çalıştırın.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL UserPrincipalName,AutoExpandingArchiveEnabled
```

değeri  `True` , etkin olmayan posta kutusu için otomatik genişletme arşivlemenin etkinleştirildiğini gösterir. değeri `False` , otomatik genişletme arşivlemenin etkinleştirilmediğini gösterir.

Otomatik genişletme arşivlemeyi etkinleştirdikten sonra aşağıdakileri göz önünde bulundurun:
  
- Kuruluşunuzda otomatik genişletme arşivlemeyi etkinleştirmek için **Set-OrganizationConfig -AutoExpandingArchive** komutunu çalıştırırsanız, tek tek posta kutularında **Enable-Mailbox -AutoExpandingArchive** komutunu çalıştırmanız gerekmez. Kuruluşunuzda otomatik genişletme arşivlemeyi etkinleştirmek için **Set-OrganizationConfig** cmdlet'ini çalıştırmak, kullanıcı posta kutularındaki `True`*AutoExpandingArchiveEnabled* özelliğini olarak değiştirmez.

- Benzer şekilde, arşivlemeyi otomatik genişletmeyi etkinleştirdiğinizde  *ArchiveQuota*  ve  *ArchiveWarningQuota*  posta kutusu özelliklerinin değerleri değişmez. Aslında, bir kullanıcı posta kutusu için otomatik genişletme arşivlemeyi etkinleştirdiğinizde ve  *AutoExpandingArchiveEnabled*  özelliği olarak  `True`ayarlandığında  *ArchiveQuota*  ve  *ArchiveWarningQuota*  özellikleri yoksayılır. Kullanıcının posta kutusu için otomatik genişletme arşivleme etkinleştirildikten sonra bu posta kutusu özelliklerine bir örnek aşağıda verilmiştir. 

    ![Arşivlemeyi otomatik genişletmeyi etkinleştirdikten sonra ArchiveQuota ve ArchiveWarningQuota özellikleri yoksayılır.](../media/6a1c1b69-5c4c-4267-aac8-53577667f03e.png)

## <a name="more-information"></a>Daha fazla bilgi

- Arşiv posta kutularını etkinleştirmek için PowerShell'i de kullanabilirsiniz. Örneğin, Exchange Online PowerShell'de aşağıdaki komutu çalıştırarak arşiv posta kutusu henüz etkinleştirilmemiş olan tüm kullanıcılar için arşiv posta kutularını etkinleştirebilirsiniz.

    ```powershell
    Get-Mailbox -Filter {ArchiveStatus -Eq "None" -AND RecipientTypeDetails -eq "UserMailbox"} | Enable-Mailbox -Archive
    ```

- Otomatik genişletme arşivleme, şirket içi birincil posta kutusu olan kullanıcılar için Exchange karma dağıtımdaki bulut tabanlı arşiv posta kutuları için desteklenir. Ancak, otomatik genişletme arşivleme bulut tabanlı bir arşiv posta kutusu için etkinleştirildikten sonra, bu arşiv posta kutusunu şirket içi Exchange kuruluşuna geri ekleyemezsiniz. Otomatik genişletme arşivleme, Exchange Server herhangi bir sürümündeki şirket içi posta kutuları için desteklenmez.

- Kullanıcıların arşiv posta kutularındaki ek depolama alanındaki öğelere erişmek için kullanabilecekleri Outlook istemcilerinin listesi için [Arşivlemeyi otomatik genişletme hakkında bilgi edinin](autoexpanding-archiving.md#outlook-requirements-for-accessing-items-in-an-auto-expanded-archive) bölümündeki "Otomatik genişletilmiş arşivdeki öğelere erişmek için Outlook gereksinimleri" bölümüne bakın.

- Daha önce açıklandığı gibi, **Enable-Mailbox -AutoExpandingArchive** komutunu çalıştırdığınızda kullanıcının birincil arşiv posta kutusunun depolama kotasına (ve posta kutusu ayrı tutuluyorsa Kurtarılabilir Öğeler klasörüne) 10 GB eklenir. Bu, otomatik olarak genişletilmiş depolama alanı sağlanana kadar (30 güne kadar sürebilir) ek depolama alanı sağlar. Kuruluşunuzdaki tüm posta kutuları için otomatik genişletme arşivlemeyi etkinleştirmek için **Set-OrganizationConfig -AutoExpandingArchive** komutunu çalıştırdığınızda bu ek depolama alanı eklenmez. Tüm kuruluş için otomatik genişletme arşivlemeyi etkinleştirdiyseniz ancak belirli bir kullanıcı için ek 10 GB depolama alanı eklemeniz gerekiyorsa, bu posta **kutusunda Enable-Mailbox -AutoExpandingArchive** komutunu çalıştırabilirsiniz. Otomatik genişletme arşivlemenin zaten etkinleştirildiğini ancak posta kutusuna ek depolama alanı ekleneceğini belirten bir hata alırsınız.

> [!IMPORTANT]
> Otomatik genişletme arşivleme yalnızca tek tek kullanıcılar tarafından kullanılan posta kutuları veya günlük 1 GB'ı aşmayan bir büyüme oranına sahip paylaşılan posta kutuları için desteklenir. Arşivleme amacıyla iletileri arşiv posta kutusuna kopyalamak için günlüğe kaydetme, taşıma kuralları veya otomatik iletme kurallarının kullanılmasına izin verilmez. Kullanıcının arşiv posta kutusu yalnızca o kullanıcıya yöneliktir. Microsoft, kullanıcının arşiv posta kutusunun diğer kullanıcıların arşiv verilerini depolamak için kullanıldığı veya uygunsuz kullanım durumlarında ek arşivlemeyi reddetme hakkını saklıdır.
