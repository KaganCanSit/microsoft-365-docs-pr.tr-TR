---
title: Bulut posta kutusunun olduğu Kurtarılabilir Öğeler klasöründeki öğeleri silme
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
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
ms.assetid: a85e1c87-a48e-4715-bfa9-d5275cde67b0
description: Bir posta kutusu yasal olarak basılı tutulsa bile, yöneticilerin bir kullanıcının Kurtarılabilir Öğeler klasöründeki Exchange Online silebilirlerini öğrenin.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: c349166477b610e48fd3a1b63c27d4dd4188012c
ms.sourcegitcommit: f563b4229760fa099703296d1ad2c1f0264f1647
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2022
ms.locfileid: "63016266"
---
# <a name="delete-items-in-the-recoverable-items-folder-of-cloud-based-mailboxes-on-hold"></a>Bulut tabanlı posta kutularının Kurtarılabilir Öğeler klasöründeki öğeleri silme

Bir posta kutusunun Kurtarılabilir Öğeler klasörü Exchange Online yanlışlıkla veya kötü amaçlı silmelere karşı korumak için vardır. Ayrıca, tutma ve eBulma aramaları gibi uyumluluk özellikleriyle korunur ve erişilen öğeleri depolamak için de kullanılır. Ancak bazı durumlarda kuruluşlar, Kurtarılabilir Öğeler klasöründe istenmiş ve bu verileri silmeleri gereken bir şekilde bulundurabilir. Örneğin, bir kullanıcı hassas bilgiler veya önemli ticari sonuçlar doğuracak bilgiler içeren bir e-posta iletisi farkında olmadan e-posta gönderebilir veya iletmiş olabilir. İleti kalıcı olarak silinse bile, posta kutusuna yasal bir tutma yerleştirildikten sonra süresiz olarak korunur. Bu senaryo veri *taşma olarak bilinir*, çünkü veriler istenerek başka bir *yere* Office 365. Bu gibi durumlarda, posta kutusu Exchange Online'daki farklı tutma özelliklerinden biri ile birlikte ayrı tutulsa bile, bir kullanıcının Kurtarılabilir Öğeler klasöründeki öğeleri Office 365. Bu tür bekletmeler, Mahkeme Bekletmeleri, In-Place Bekletmeleri, eBulma bekletmeleri ve Office 365 veya Microsoft 365'te güvenlik ve uyumluluk merkezinde oluşturulmuş bekletme ilkelerini içerir.

Bu makalede yöneticilerin, buluttaki ve basılı durumdaki posta kutuları için Kurtarılabilir Öğeler klasöründeki öğeleri nasıl silebilirleri açıklanmıştır. Bu yordam, posta kutusuna erişimi devre dışı bırakmayı ve tek öğe kurtarmayı devre dışı bırakmayı, Yönetilen Klasör Yardımcısı'nın posta kutusunu işlemesini devre dışı bırakmayı, geçici olarak tutmayı kaldırmayı, Kurtarılabilir Öğeler klasöründeki öğeleri silmeyi ve ardından posta kutusunu önceki yapılandırmasına geri döndürmeyi içerir. Bu işlem şöyledir:
  
[1. Adım: Posta kutusu hakkında bilgi toplama](#step-1-collect-information-about-the-mailbox)

[2. Adım: Posta kutusunu hazırlama](#step-2-prepare-the-mailbox)

[3. Adım: Posta kutusundan tüm 10.](#step-3-remove-all-holds-from-the-mailbox)

[4. Adım: Posta kutusundan gecikme ayını kaldırma](#step-4-remove-the-delay-hold-from-the-mailbox)

[5. Adım: Kurtarılabilir Öğeler klasöründeki öğeleri silme](#step-5-delete-items-in-the-recoverable-items-folder)

[6. Adım: Posta kutusunu önceki durumuna döndürme](#step-6-revert-the-mailbox-to-its-previous-state)
  
> [!CAUTION]
> Bu makalede ana hatlarıyla açıklanan yordamlar, verilerin bir posta kutusundan kalıcı olarak silinmesine (temizlenen) Exchange Online olur. Başka bir ifadeyle, Kurtarılabilir Öğeler klasöründen silen iletiler kurtarılamaz ve yasal keşif veya diğer uyumluluk amaçlarına yönelik olarak kullanılamaz. Microsoft 365 uyumluluk merkezi'da oluşturulmuş bir Mahkeme Tutma, In-Place Saklama, eBulma saklama veya bekletme ilkesi kapsamında saklamaya yerleştirilen posta kutusundan iletileri silmek için saklamayı kaldırmadan önce kayıt yönetiminize veya yasal departmanlara sorun. Kuruluşta, posta kutusunun tutarak mı yoksa veri taşma olayıyla mı öncelikli olduğunu tanımlayan bir ilkesi olabilir.
  
## <a name="before-you-delete-items"></a>Öğeleri smeden önce

- İçerik Arama oluşturmak ve çalıştırmak için, eBulma Yöneticisi rol grubunun bir üyesi olmalı veya Uyumluluk Arama yönetim rolüne atanmış olar. İletileri silmek için, Kuruluş Yönetimi rol grubunun bir üyesi olmalı veya Arama ve Temizleme yönetimi rolüne atanmışsınızdır. Rol grubuna kullanıcı ekleme hakkında daha fazla bilgi için bkz. [eBulma izinleri atama](./assign-ediscovery-permissions.md).

- Kuruluş genelinde bir bekletme ilkesine bir posta kutusu atanmışsa, Kurtarılabilir Öğeler klasöründeki öğeleri silmeden önce posta kutusunu ilkenin dışında tutmanız gerekir. İlke değişikliğini eşitlemek ve posta kutusunu ilkeden kaldırmak 24 saat kadar sürebilir. Daha fazla bilgi için, bu makalenin Posta kutusundan tüm bekletmeleri kaldırma bölümünde yer alan "Kuruluş [genelinde bekletme](#organization-wide-retention-policies) ilkeleri" bölümüne bakın.

- Bu yordamı, tutma kilidi kullanılarak kilitlenmiş bir bekletme ilkesine sahip, bekletme ayarları atanmış bir posta kutusu için gerçekleştirebilirsiniz. Çünkü bu kilit, posta kutusunu ilkeden kaldırmanızı veya dışlamanızı ve posta kutusunda Yönetilen Klasör Yardımcısı'nın devre dışı bırakılmasını engellemenizi sağlar. Bekletmeye yönelik kilitleme ilkeleri hakkında daha fazla bilgi için bkz. Bekletme ilkeleri ve bekletme etiketi ilkelerine yapılan değişiklikleri kısıtlamak için [Koruma Kilidi'ne bakın](retention-preservation-lock.md).

- Bu makalede açıklanan yordam, etkin olmayan posta kutularında desteklenmiyor. Bunun nedeni, devre dışı olan bir posta kutusunu kaldırdikten sonra bekletmeyi (veya bekletme ilkesi) yeniden uygulamanızdır. Etkin olmayan bir posta kutusundan geçici olarak tutmayı kaldırsanız, bu durum geçici olarak silinmiş normal bir posta kutusuna değiştirilir ve Yönetilen Klasör Yardımcısı tarafından işlendikten sonra kalıcı olarak kuruluştan silinir.

- Posta kutusu yerine yerleştirilmediyse (veya tek bir öğe kurtarma özelliği etkinleştirilmediyse), kurtarılabilir Öğeler klasöründeki öğeleri silebilirsiniz. Bunun nasıl olduğu hakkında daha fazla bilgi için bkz. [Kurumda e-posta iletilerini arama ve silme](./search-for-and-delete-messages-in-your-organization.md).

## <a name="step-1-collect-information-about-the-mailbox"></a>1. Adım: Posta kutusu hakkında bilgi toplama

Bu ilk adım, seçili özellikleri hedef posta kutusundan bu yordamı etkileyecek şekilde toplamaktır. Kurtarılabilir Öğeler klasöründeki öğeleri sildikten sonra, bu ayarları bir yere not a veya bir metin dosyasına kaydetmeye dikkat edin. Bu özelliklerden bazılarını değiştirir ve sonra 6. Adımda özgün değerlere geri dönersiniz. Burada, toplamanız gereken posta kutusu özelliklerinin bir listesi ve bulunmaktadır.
  
- *SingleItemRecoveryEnabled ve*  *retainDeletedItemsFor*. Gerekirse, tek kurtarmayı devre dışı bırakacaktır ve 3. Adım'da silinmiş öğelerin bekletme süresi artıracaktır.

- *LitigationHoldEnabled ve*  *InPlaceHolds*. 3. Adımda bunları geçici olarak kaldırabilirsiniz. Posta [kutusuna yerleştirilen](#more-information) tür tutma bilgilerini belirleme hakkında ipuçları için Daha fazla bilgi bölümüne bakın.

Buna ek olarak, posta kutusu istemcisi erişim ayarlarını alarak, bu yordam sırasında posta kutusunun sahibinin (veya diğer kullanıcıların) posta kutusuna erişisini geçici olarak devre dışı  edebilirsiniz. Son olarak, Kurtarılabilir Öğeler klasöründe geçerli boyutu ve öğe sayısını elde edinebilirsiniz. 5. Adımdaki Kurtarılabilir Öğeler klasöründeki öğeleri sildikten sonra, bu bilgileri kullanarak öğelerin kaldırılmış olduğunu doğrularsınız.
  
1. [Bağlan PowerShell Exchange Online e geri tarak.](/powershell/exchange/connect-to-exchange-online-powershell) Bu hesapta uygun yönetim rollerine atanmış bir yönetici hesabı için kullanıcı adı ve parola kullanmaya Exchange Online.

2. Tek öğe kurtarma ve silinmiş öğe bekletme süresi hakkında bilgi almak için aşağıdaki komutu çalıştırın.

    ```powershell
    Get-Mailbox <username> | FL SingleItemRecoveryEnabled,RetainDeletedItemsFor
    ```

   Tek öğe kurtarma etkinse, 2. Adımda bunu devre dışı bırakmanız gerekir. Silinmiş öğe bekletme süresi 30 gün (en fazla 30 gün Exchange Online) olarak ayarlanmazsa, bunu 2. Adım'da artırabilirsiniz.

3. Posta kutusunun posta kutusu erişim ayarlarını almak için aşağıdaki komutu çalıştırın.

    ```powershell
    Get-CASMailbox <username> | FL EwsEnabled,ActiveSyncEnabled,MAPIEnabled,OWAEnabled,ImapEnabled,PopEnabled
    ```

   2. Adım'da bu erişim yöntemlerinin hepsini devre dışı bırak çünkü.

4. Posta kutusuna uygulanan bekletme ilkeleri ve bekletme ilkeleri hakkında bilgi almak için aşağıdaki komutu çalıştırın.

    ```powershell
    Get-Mailbox <username> | FL LitigationHoldEnabled,InPlaceHolds
    ```

    > [!TIP]
    > *InPlaceHolds* özelliğinde çok fazla değer varsa ve bunların hepsi görüntülenmezse, `Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds` her değeri ayrı bir satırda görüntülemek için komutu çalıştırabilirsiniz.
  
5. Kuruluş genelindeki bekletme ilkeleri hakkında bilgi almak için aşağıdaki komutu çalıştırın. 

    ```powershell
    Get-OrganizationConfig | FL InPlaceHolds
    ```

   Kuruluş genelinde herhangi bir bekletme ilkesi varsa, 3. Adımda posta kutusunu bu ilkeler dışında tutmanız gerekir. Değişikliğin tekrarı 24 saate kadar sürebilir.

    > [!TIP]
    > *InPlaceHolds* özelliğinde çok fazla değer varsa ve bunların hepsi görüntülenmezse, `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` her değeri ayrı bir satırda görüntülemek için komutu çalıştırabilirsiniz. 
  
6. Posta kutusuna bir gecikme gecikmesi uygulan uygulan mı olduğunu belirlemek için aşağıdaki komutu çalıştırın.

   ```powershell
   Get-Mailbox <username> | FL DelayHoldApplied,DelayReleaseHoldApplied
   ```

   *DelayHoldApplied* veya *DelayReleaseHoldApplied* özelliğinin değeri **True** olarak ayarlanırsa, posta kutusuna gecikme tutma uygulanır ve kaldırılması gerekir. Gecikmede tutma hakkında daha fazla bilgi için bkz [. 4. Adım: Posta kutusundan gecikmeyi kaldırma](#step-4-remove-the-delay-hold-from-the-mailbox).

   Özelliklerden herhangi biri Yanlış olarak **ayarlanırsa**, posta kutusuna gecikme süresi uygulanmaz ve 4. Adımı atlayabilirsiniz.

7. Kullanıcının birincil posta kutusunun Kurtarılabilir Öğeler klasöründe geçerli boyutu ve klasör ve alt klasörlerdeki öğelerin toplam sayısını elde etmek için aşağıdaki komutu çalıştırın.

    ```powershell
    Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
    ```

   Kullanıcının arşiv posta kutusu etkinleştirilmişse, arşiv posta kutusunun Kurtarılabilir Öğeler klasöründeki klasörler ve alt klasörlerdeki öğelerin boyutunu ve toplam sayısını almak için aşağıdaki komutu çalıştırın. 

    ```powershell
    Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems -Archive | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
    ```

   5. Adımda öğeleri silerken, kullanıcının birincil arşiv posta kutusunun Kurtarılabilir Öğeler klasöründeki öğeleri silmeyi veya silmeyi seçebilirsiniz. Posta kutusu için otomatik genişleyen arşivleme etkinleştirilirse, arşiv posta kutusunda arşivlenen öğeler silinmez.
  
## <a name="step-2-prepare-the-mailbox"></a>2. Adım: Posta kutusunu hazırlama

Posta kutusuyla ilgili bilgileri toplayıp kaydettikten sonra, bir sonraki adım aşağıdaki görevleri gerçekleştirerek posta kutusunu hazırlamaktır:
  
- **Posta kutusuna istemci erişimini devre** dışı bırakarak posta kutusu sahibinin bu yordam sırasında posta kutusu verilerine erişiley ve verilerde herhangi bir değişiklik yapmalarını sağ tıklatın.

- **Silinmiş öğe bekletme** süresi 30 gün (Exchange Online'daki en büyük değer) olarak artar ve böylece 5. Adımda öğeleri silemezsiniz ve kurtarılabilir Öğeler klasöründen silinmezler.

-  5. Adımdaki Kurtarılabilir Öğeler klasöründen sildikten sonra öğelerin korunmayacak şekilde (silinmiş öğe bekletme süresi boyunca) tek Öğe kurtarmayı devre dışı bırakma.

- **Yönetilen Klasör Yardımcısı'ı devre** dışı bırakarak posta kutusunu işlemesini ve silen öğeleri 5. Adımda tutmasını silebilirsiniz.

Exchange Online PowerShell'de aşağıdaki adımları gerçekleştirin.
  
1. Posta kutusuna tüm istemci erişimini devre dışı bırakmak için aşağıdaki komutu çalıştırın. Komut sözdiziminde, posta kutusunda tüm istemci erişim yöntemlerinin etkinleştirildiğinden emin olun.

    ```powershell
    Set-CASMailbox <username> -EwsEnabled $false -ActiveSyncEnabled $false -MAPIEnabled $false -OWAEnabled $false -ImapEnabled $false -PopEnabled $false
    ```

    > [!NOTE]
    > Posta kutusuna tüm istemci erişim yöntemlerini devre dışı bırakmak 60 dakika kadar sürebilir. Şu anda oturum açıksa, bu erişim yöntemlerini devre dışı bırakmanın posta kutusu sahibinin bağlantısını kesmez. Oturum sahibi oturum a etmedikten sonra, bu erişim yöntemleri devre dışı bırakılacaktır ve posta kutusuna erişamaz.
  
2. Silinmiş öğe bekletme süresi en fazla 30 gün olacak şekilde artırmak için aşağıdaki komutu çalıştırın. Bu, geçerli ayarın 30'dan az olduğunu varsayıyor.

    ```powershell
    Set-Mailbox <username> -RetainDeletedItemsFor 30
    ```

3. Tek öğe kurtarmayı devre dışı bırakmak için aşağıdaki komutu çalıştırın.

    ```powershell
    Set-Mailbox <username> -SingleItemRecoveryEnabled $false
    ```

    > [!NOTE]
    > Tek öğe kurtarmayı devre dışı bırakmak 240 dakika kadar sürebilir. Bu süre geçene kadar Kurtarılabilir Öğeler klasöründeki öğeleri silmeyin.
  
4. Yönetilen Klasör Yardımcısı'nın posta kutusunu işlemesini engellemek için aşağıdaki komutu çalıştırın. Daha önce de belirtildiği gibi, Yönetilen Klasör Yardımcısı'nın devre dışı bırak yalnızca Posta kutusuna Koruma Kilidi içeren bir bekletme ilkesi uygulanmazsa devre dışı bırakabilirsiniz.

    ```powershell
    Set-Mailbox <username> -ElcProcessingDisabled $true
    ```

## <a name="step-3-remove-all-holds-from-the-mailbox"></a>3. Adım: Posta kutusundan tüm 10.

Kurtarılabilir Öğeler klasöründeki öğeleri silemezsiniz. Bu işlem, posta kutusuna yerleştirilen tüm (1. Adımda tanımdınız) 1. Kurtarılabilir Öğeler klasöründen sildikten sonra öğelerin korumalarını kaldırmış olması için tüm tutmaların kaldırılması gerekir. Aşağıdaki bölümlerde, posta kutusunda farklı türde 10 10 000 000 000 000 000 000 000 000 0 Posta [kutusuna yerleştirilen](#more-information) tür tutma bilgilerini belirleme hakkında ipuçları için Daha fazla bilgi bölümüne bakın. Daha fazla bilgi için bkz[. Posta kutunuzda, bir posta kutusuna yerleştirilen Exchange Online belirleme](identify-a-hold-on-an-exchange-online-mailbox.md).
  
> [!CAUTION]
> Daha önce de belirtildiği gibi, posta kutusundan  ayrı tutmadan önce kayıt yönetiminizi veya hukuk bölümlerinizi kontrol edin.
  
### <a name="litigation-hold"></a>Mahkeme Tutma
  
Posta kutusundan Mahkeme Exchange Online kaldırmak için PowerShell'de aşağıdaki komutu çalıştırın.

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $false
```

> [!NOTE]
> Tek öğe kurtarmayı devre dışı bırakmaya benzer şekilde, Mahkeme Tutma'nın kaldırılmış süresi 240 dakika kadar sürebilir. Bu süre geçene kadar Kurtarılabilir Öğeler klasöründeki öğeleri silmeyin.
  
### <a name="in-place-hold"></a>In-Place Tutun
  
PowerShell'Exchange Online posta kutusuna yerleştirilen In-Place tutmak için aşağıdaki komutu çalıştırın. 1. Adımda tanım In-Place Için GUID kullanın.

```powershell
Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL Name
```

Posta kutusunu tutma In-Place posta kutusunu tutmak için Exchange yönetim merkezini <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">(EAC)</a> veya Exchange Online PowerShell'i kullanabilirsiniz. Daha fazla bilgi için bkz [. 2013'In-Place kaldırma](/exchange/security-and-compliance/create-or-remove-in-place-holds).
  
### <a name="retention-policies-applied-to-specific-mailboxes"></a>Belirli posta kutularına uygulanan bekletme ilkeleri
  
Posta kutusuna uygulanan bekletme [& belirlemek için Güvenlik](/powershell/exchange/connect-to-scc-powershell) ve Uyumluluk Merkezi PowerShell'de aşağıdaki komutu çalıştırın. Bu komut, posta kutusuna Teams konuşma bekletme ilkelerini de geri dönecektir. 1. Adım'da tanımtıklarını `mbx` `skp` bekletme ilkesi için GUID 'i (veya ön eki dahil değil) kullanın.

```powershell
Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name
```

Bekletme ilkesi belirlendikten sonra,  >  Microsoft 365 uyumluluk merkezi'te Bilgi idaresiRetention sayfasına gidin, önceki adımda tanım istediğiniz bekletme ilkesine tıklayın ve posta kutusunu bekletme ilkesine dahil edilen alıcılar listesinden kaldırın.
  
### <a name="organization-wide-retention-policies"></a>Kuruluş genelinde bekletme ilkeleri
  
Kuruluş genelinde, Exchange genelinde ve tüm Teams bekletme ilkeleri, kuruluşun tüm posta kutularına uygulanır. Bunlar, posta kutusu düzeyinde değil kuruluş düzeyinde uygulanır ve 1. Adım'da **Get-OrganizationConfig** cmdlet'ini çalıştırabilirsiniz. Kuruluş genelindeki bekletme ilkelerini [& için Güvenlik ve Uyumluluk Merkezi PowerShell'de](/powershell/exchange/exchange-online-powershell) aşağıdaki komutu çalıştırın. 1. Adımda tanım– kuruluş  `mbx` genelindeki bekletme ilkelerinin GUID'lerini (öneki dahil değil) kullanın.

```powershell
Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name
```

Kuruluş genelindeki bekletme ilkelerini belirledikten sonra,  >  Microsoft 365 uyumluluk merkezi'de Bilgi idaresiRetention sayfasına gidin, önceki adımda tanımlanmış kuruluş genelindeki her bekletme ilkesi düzenleyin ve posta kutusunu dışlanan alıcılar listesine ekleyin. Bunu yapmak bekletme ilkesinden kullanıcının posta kutusunu kaldırır.

> [!IMPORTANT]
> Posta kutusunu kuruluş genelindeki bir bekletme ilkesinden dışladikten sonra, bu değişikliği eşitlemek ve posta kutusunu ilkeden kaldırmak 24 saat kadar sürebilir.

### <a name="retention-labels"></a>Bekletme etiketleri

Kullanıcı, içeriği korumak veya içeriği tutmak ve posta kutusunda herhangi bir klasöre veya öğeye içerik silmek üzere yapılandırılan bir etiket uygulamanın her zaman, *ComplianceTagHoldApplied* posta kutusu özelliği **True olarak ayarlanır**. Bu durum olduğunda, posta kutusunun Mahkeme Tutma'ya yerleştirildi veya bir bekletme ilkesine atanmış gibi saklama olarak kabul edilir.

*ComplianceTagHoldApplied özelliğinin değerini* görüntülemek için, PowerShell'de aşağıdaki Exchange Online çalıştırın:

```powershell
Get-Mailbox <username> |FL ComplianceTagHoldApplied
```

Bir klasöre veya öğeye bekletme etiketi uygulandığı için posta kutusunun saklama durumunda olduğunu belirledikten sonra, bekletme etiketi koşullarını kullanarak etiketli öğeleri aramak için Microsoft 365 uyumluluk merkezi'de İçerik arama **aracını kullanabilirsiniz**. Daha fazla bilgi için bkz.:

- Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edin bölümünde "Belirli bir bekletme etiketine sahip tüm içeriği bulmak için [İçerik Arama'ya gerek yok" bölümü](retention.md#using-content-search-to-find-all-content-with-a-specific-retention-label)

- Anahtar sözcük sorgularının "Arama [koşulları" bölümü ve İçerik Arama için arama koşulları](keyword-queries-and-search-conditions.md#conditions-for-common-properties).

Etiketler hakkında daha fazla bilgi için bkz[. Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi.](retention.md)

### <a name="ediscovery-holds"></a>eKbulma 1
  
Posta kutusuna uygulanan bir [eBulma & durumuyla](/powershell/exchange/connect-to-scc-powershell) ( *eBulma* tutmaları denir) ilişkilendirilmiş ayrımı tanımlamak için Güvenlik ve Uyumluluk Merkezi PowerShell'de aşağıdaki komutları çalıştırın. 1. Adımda tanımlanmamış  `UniH` eBulma ayrımı için GUID kullanın (öneki dahil değildir). İkinci komut, tutmanın ilişkilendirilen eBulma büyük/harf adını görüntüler; üçüncü komut, sıyrı adını görüntüler.
  
```powershell
$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>
```

```powershell
Get-ComplianceCase $CaseHold.CaseId | FL Name
```

```powershell
$CaseHold.Name
```

eBulma vakanın adını ve ayrı tutma adını belirledikten sonra, uyumluluk merkezinde **eBulma** \> **eBulma** sayfasına gidin, vakayı açın ve posta kutusunu tutmadan kaldırın. eBulma damalarını tanımlama hakkında daha fazla bilgi için, bir posta kutusuna yerleştirilen tutma türünü belirleme konusunda yer alan "eBulma Exchange Online [bakın](identify-a-hold-on-an-exchange-online-mailbox.md#ediscovery-holds).
  
## <a name="step-4-remove-the-delay-hold-from-the-mailbox"></a>4. Adım: Posta kutusundan gecikme ayını kaldırma

Posta kutusundan herhangi bir tür tutma kaldırıldıktan sonra, *DelayHoldApplied* veya *DelayReleaseHoldApplied* posta kutusu özelliğinin değeri **True olarak ayarlanır**. Bu durum, Yönetilen Klasör Yardımcısı bir sonraki kez posta kutusunu işlemesi ve bir tutmanın kaldırılmış olduğunu algılar. Bu, gecikme nedeniyle *tutma olarak* adlandırılan bu durum, verilerin posta kutusundan kalıcı olarak silinmesini önlemek için gerçek olarak kaldırmanın 30 gün ertelenmiş olduğu anlamına gelir. (Gecikmenin amacı, yöneticilere, tutma kaldırıldıktan sonra temizılacak posta kutusu öğelerini arama veya kurtarma fırsatı vermektir.)  Posta kutusu üzerinde gecikme süresi yerleştirilse bile, posta kutusunun mahkeme nedeniyle tutma devam ediyor olması gibi, posta kutusunun sınırsız bir süre boyunca orada tutul olduğu kabul edilir. 30 gün sonra, gecikme nedeniyle tutma süresi dolar ve Microsoft 365, gecikme süresini kaldırmayı (*DelayHoldApplied* veya *DelayReleaseHoldApplied* özelliğini **False** olarak ayararak) otomatik olarak kaldırmayı ve bu şekilde tutmayı kaldırmayı çalışır. Gecikmeyi geciktirme hakkında daha fazla bilgi için, Bir posta kutusuna yerleştirilen tutma türünü belirleme bölümündeki "Posta kutularını gecikme nedeniyle yönetme" [Exchange Online bakın](identify-a-hold-on-an-exchange-online-mailbox.md#managing-mailboxes-on-delay-hold).

*DelayHoldApplied* veya *DelayReleaseHoldApplied* özelliğinin değeri **True** olarak ayarlanmışsa, gecikmeyi tutmak için aşağıdaki komutlardan birini çalıştırın:

```powershell
Set-Mailbox <username> -RemoveDelayHoldApplied
```

Veya

```powershell
Set-Mailbox <username> -RemoveDelayReleaseHoldApplied
```

*RemoveDelayHoldApplied* veya *RemoveDelayReleaseHoldApplied* parametresini kullanmak için Exchange Online'de Yasal Tutma rolüne atanmış olması gerekir.

## <a name="step-5-delete-items-in-the-recoverable-items-folder"></a>5. Adım: Kurtarılabilir Öğeler klasöründeki öğeleri silme

Artık, Güvenlik ve Uyumluluk Merkezi PowerShell'de Yeni UyumlulukArama ve Yeni [UyumlulukSearchAction](/powershell/module/exchange/new-compliancesearchaction) cmdlet'lerini kullanarak Kurtarılabilir Öğeler klasöründeki öğeleri & hazırsınız.[](/powershell/module/exchange/new-compliancesearch)

Kurtarılabilir Öğeler klasöründe bulunan öğeleri aramak için, hedefli bir koleksiyon *gerçekleştirmenizi öneririz*. Bu, arama kapsamını yalnızca Kurtarılabilir Öğeler klasöründe bulunan öğelere göre daraltmanız anlamına gelir. Bunu, İçerik Arama hedefli koleksiyonlar için [kullanma makalesinde betiği çalıştırarak da kullanabilirsiniz](use-content-search-for-targeted-collections.md) . Bu betik, hedef Kurtarılabilir Öğeler klasöründeki tüm alt klasörler için klasör kimliği özelliğinin değerini döndürür. Daha sonra, arama sorgusunda klasör kimliğini kullanarak bu klasörde yer alan öğeleri geri getirebilirsiniz.

Bir kullanıcının Kurtarılabilir Öğeler klasöründe öğeleri aramak ve silmek için bu işleme genel bir bakış ve şöyledir:

1. Hedef kullanıcının posta kutusunda yer alan tüm klasörler için klasör kimliklerini döndüren hedefli koleksiyon betiği çalıştırın. Betik, aynı PowerShell Exchange Online PowerShell & Uyumluluk PowerShell'e bağlanır. Daha fazla bilgi için bkz [. Posta kutusunun klasörlerinin listesini almak için betiği çalıştırma](use-content-search-for-targeted-collections.md#step-1-run-the-script-to-get-a-list-of-folders-for-a-mailbox-or-site).

2. Kurtarılabilir Öğeler klasöründeki tüm alt klasörlerin klasör kimliklerini kopyalayın. Alternatif olarak, betiğin çıktısını bir metin dosyasına yönlendirebilirsiniz.

   Kurtarılabilir Öğeler klasöründeki alt klasörlerin listesi ve açıklaması ve burada öğeleri arayabilir ve silebilirsiniz:

   - **Silmeler**: Silinmiş öğe bekletme süresi dolmamış, yumuşak silinmiş öğeleri içerir. Kullanıcılar, çalışma sayfalarındaki Silinmiş Öğeleri Kurtar aracını kullanarak bu alt klasördeki silinmiş öğeleri Outlook.

   - **BulmaHold'ları**: eBulma saklama veya bekletme ilkesi tarafından korunan, kalıcı olarak silinen öğeleri içerir. Bu alt klasör son kullanıcılar tarafından görülmeyebilir.

   - **AltStrateHolds**: Bekletme ilkesi veya başka bir saklama Teams bulut tabanlı uygulamalar tarafından korunan, sabit silinmiş öğeler içerir. Bu alt klasör son kullanıcılar tarafından görülmeyebilir.

3. Yeni Uyumluluk **Arama** cmdlet'ini (Güvenlik & Uyumluluk Merkezi PowerShell'de) veya uyumluluk merkezinde İçerik arama aracını kullanarak hedef kullanıcının Kurtarılabilir Öğeler klasöründen öğe döndüren bir içerik araması oluşturun. Arama yapmak istediğiniz tüm alt klasörler için arama sorgusuna KlasörKimlik'i de dahil edin. Örneğin, aşağıdaki sorgu Silmeler ve eKoverHolds alt klasörleriniteki tüm iletileri döndürür:

   ```text
   folderid:<folder ID of Deletions subfolder> OR folderid:<folder ID of DiscoveryHolds subfolder>
   ```

   Klasör kimliği özelliğini kullanan içerik aramaları çalıştırma hakkında daha fazla bilgi ve örnekler için bkz. Klasör kimliği kullanma veya [hedefli koleksiyon gerçekleştirme](use-content-search-for-targeted-collections.md#step-2-use-a-folder-id-or-documentlink-to-perform-a-targeted-collection).

   > [!NOTE]
   > Kurtarılabilir Öğeler **klasöründe arama yapmak** için Yeni Uyumluluk Arama cmdlet'ini kullanıyorsanız, arama yapmak için **Start-ComplianceSearch** cmdlet'ini kullanmaya devam edin.

4. İçerik aramasını oluşturduktan ve silmek istediğiniz öğeleri döndürdükten sonra, `New-ComplianceSearchAction -Purge -PurgeType HardDelete` önceki adımda oluşturduğunuz içerik arama tarafından döndürülen öğeleri kalıcı olarak silmek için bu komutu (Güvenlik & Uyumluluk Merkezi PowerShell'de) kullanın. Örneğin, aşağıdaki komuta benzer bir komut çalıştırabilirsiniz:

   ```powershell
   New-ComplianceSearchAction -SearchName "RecoverableItems" -Purge -PurgeType HardDelete
   ```

5. Önceki komutu çalıştırarak posta kutusu başına en çok 10 öğe silinir. Bu durumda, Kurtarılabilir Öğeler `New-ComplianceSearchAction -Purge` klasöründe silmek istediğiniz tüm öğeleri silmek için komutu birkaç kez çalıştırmanız gerekir. Ek öğeleri silmek için, önce önceki uyumluluk araması temizleme eylemlerini kaldırmanız gerekir. Bunu cmdlet'i çalıştırarak `Remove-ComplianceSearchAction` yapar. Örneğin, önceki adımda çalıştırıcı olan temizleme eylemını silmek için aşağıdaki komutu çalıştırın:

   ```powershell
   Remove-ComplianceSearchAction "RecoverableItems_Purge"
   ```

   Bunu tamamladikten sonra, daha fazla öğe silmek için yeni bir uyumluluk araması temizleme eylemi oluşturabilirsiniz. Yeni bir eylem oluşturmadan önce tüm temizleme eylemlerini silmeniz gerekir.

   Uyumluluk arama eylemlerinin listesini almak için, cmdlet'i `Get-ComplianceSearchAction` çalıştırabilirsiniz. Temizleme eylemleri, arama adının `_Purge` sonuna ekli olarak tanımlanır.

### <a name="verify-that-items-were-deleted"></a>Öğelerin silindi olduğunu doğrulama

Bir posta kutusunun Kurtarılabilir Öğeler klasöründeki öğeleri başarıyla sildiğini doğrulamak için, Exchange Online PowerShell'de **Get-MailboxFolderStatistics** cmdlet'ini kullanarak Kurtarılabilir Öğeler klasöründeki öğelerin boyutunu ve sayısını kontrol edin. Bu istatistikleri, 1. Adımda toplanmış olanlarla karşılaştıramazsiniz.
  
Kullanıcının birincil posta kutusunun Kurtarılabilir Öğeler klasöründeki klasörler ve alt klasörlerdeki geçerli boyutu ve toplam öğe sayısını elde etmek için aşağıdaki komutu çalıştırın.
  
```powershell
Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
```

Kullanıcının arşiv posta kutusunun Kurtarılabilir Öğeler klasöründeki klasörler ve alt klasörlerdeki öğelerin boyutunu ve toplam sayısını elde etmek için aşağıdaki komutu çalıştırın.

```powershell
Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems -Archive | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
```

## <a name="step-6-revert-the-mailbox-to-its-previous-state"></a>6. Adım: Posta kutusunu önceki durumuna döndürme

Son adım, posta kutusunu önceki yapılandırmasına geri döndürme işlemidir. Bu, 2. Adımda değiştirmiş olduğu özellikleri sıfırlamak ve 3. Adımda kaldırılan 00.000'i yeniden geçerlik için kullanılabilir. Bu şunları içerir:
  
- Silinmiş öğe bekletme süresi önceki değerine geri değiştirildi. Alternatif olarak, bu değeri en yüksek değer olan 30 gün olarak Exchange Online.

- Tek öğe kurtarmayı yeniden etkinleştirme.

- Sahibin kendi posta kutusuna erişesini sağlamak için istemci erişim yöntemlerini yeniden etkinleştirme.

- Kaldırılan bekletme ve bekletme ilkelerini yeniden onaylama.

- Yönetilen Klasör Yardımcısı'nın posta kutusunu işlemesini yeniden etkinleştirme.

> [!IMPORTANT]
> Yönetilen Klasör Yardımcısı'nın posta kutusunu yeniden etkinleştirmeden önce saklama veya bekletme ilkesi yeniden uygulanması (ve yerinde olduğunu doğrulama) sonra 24 saat beklemenizi öneririz.
  
Exchange Online PowerShell'de aşağıdaki adımları (belirtilen Exchange Online gerçekleştirin.
  
1. Silinmiş öğe bekletme dönemini özgün değerine geri değiştirmek için aşağıdaki komutu çalıştırın. Bu, önceki ayarın 30 saatten az olduğunu varsayıyor; örneğin, 14 gün.

    ```powershell
    Set-Mailbox <username> -RetainDeletedItemsFor 14
    ```

2. Tek öğe kurtarmayı yeniden etkinleştirmek için aşağıdaki komutu çalıştırın.

    ```powershell
    Set-Mailbox <username> -SingleItemRecoveryEnabled $true
    ```

3. Posta kutusuna tüm istemci erişim yöntemlerini yeniden etkinleştirmek için aşağıdaki komutu çalıştırın.

    ```powershell
    Set-CASMailbox <username> -EwsEnabled $true -ActiveSyncEnabled $true -MAPIEnabled $true -OWAEnabled $true -ImapEnabled $true -PopEnabled $true
    ```

4. 3. Adımda kaldırılan 10. Tutma türüne bağlı olarak, aşağıdaki yordamlardan birini kullanın.

    **Mahkeme Tutma**

    Posta kutusu için Mahkeme Tutma'ya yeniden etkinleştirmek için aşağıdaki komutu çalıştırın.

    ```powershell
    Set-Mailbox <username> -LitigationHoldEnabled $true
    ```

    **Yerinde Yerinde Tutma**

    EAC (veya Exchange Online PowerShell) kullanarak posta kutusunu Posta Kutusunu Yeniden Basılı In-Place kullanın.

    **Belirli posta kutularına uygulanan bekletme ilkeleri**

    Posta Microsoft 365 uyumluluk merkezi bekletme ilkesine geri eklemek için Posta Kutusunu kullanın. Uyumluluk **merkezi'nde** >  Bilgi **yönetimiRetention** sayfasına gidin, bekletme ilkesi düzenleyin ve posta kutusunu bekletme ilkesine uygulanan alıcılar listesine geri ekleyin.

    **Kuruluş genelinde bekletme ilkeleri**

    Kuruluş genelinde veya tüm Exchange bir bekletme ilkesi, ilke dışında bırakılarak kaldırılırsa, posta kutusunu dışlanan kullanıcılar listesinden kaldırmak için Microsoft 365 uyumluluk merkezi'i kullanın. Uyumluluk **merkezi'nde** >  Bilgi **yönetimiRetention** sayfasına gidin, kuruluş genelinde bekletme ilkesi düzenleyin ve posta kutusunu dışlanan alıcılar listesinden kaldırın. Bunu yapmak bekletme ilkesi kullanıcının posta kutusuna yeniden uygulama.

    **eKbulma olay ayrımları**

    Posta Microsoft 365 uyumluluk merkezi bir eBulma durumuyla ilişkilendirilmiş olan ayrı tutma durumuna geri eklemek için Posta Kutusunu kullanın. **eDiscoveryCore sayfasına** >  gidin, vakayı açın ve posta kutusunu yeniden ayrı tutma durumuna ekleyin. 

5. Yönetilen Klasör Yardımcısı'nın posta kutusunu yeniden işlemesine izin vermek için aşağıdaki komutu çalıştırın. Daha önce de belirtildiği gibi, Yönetilen Klasör Yardımcısı'ı yeniden etkinleştirmeden önce saklama veya bekletme ilkesi yeniden uygulamanın (ve var olduğunu doğrulamanın) ardından 24 saat beklemenizi öneririz.

    ```powershell
    Set-Mailbox <username> -ElcProcessingDisabled $false
    ```

6. Posta kutusunun önceki yapılandırmasına geri döndürül olduğunu doğrulamak için, aşağıdaki komutları çalıştırarak ayarları 1. Adımda topladığım ayarlarla karşılaştırabilirsiniz.

    ```powershell
    Get-Mailbox <username> | FL ElcProcessingDisabled,InPlaceHolds,LitigationHoldEnabled,RetainDeletedItemsFor,SingleItemRecoveryEnabled
    ```

    ```powershell
    Get-CASMailbox <username> | FL EwsEnabled,ActiveSyncEnabled,MAPIEnabled,OWAEnabled,ImapEnabled,PopEnabled
    ```

## <a name="more-information"></a>Daha fazla bilgi

**Get-Mailbox** veya **Get-OrganizationConfig** cmdlet'lerini çalıştırabilirsiniz. Daha ayrıntılı bilgi için bkz[. Posta kutunuzda veya posta kutunuzda ne tür Exchange Online belirleme](identify-a-hold-on-an-exchange-online-mailbox.md).

Daha önce de belirtildiği gibi, Kurtarılabilir Öğeler klasöründeki öğeleri başarıyla silemezken önce posta kutusundan tüm bekletme ve bekletme ilkelerini kaldırmanız gerekir.
  
| Tutma türü | Örnek değer | Sılamı belirleme |
|:-----|:-----|:-----|
|Mahkeme Tutma  <br/> | `True` <br/> |*LitigationHoldEnabled özelliği* olarak ayarlanır`True`.  <br/> |
|In-Place Tutun  <br/> | `c0ba3ce811b6432a8751430937152491` <br/> |*InPlaceHolds* özelliği, posta kutusuna In-Place Yer Tutucu'nun GUID'sini içerir. Bunun bir Ön Ek In-Place olduğunu anlarız, çünkü GUID bir önekle başlamaz.  <br/> PowerShell'de `Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL` Exchange Online posta kutusu üzerinde tutma hakkında bilgi In-Place kullanabilirsiniz.  <br/> |
| Belirli posta kutularına Microsoft 365 uyumluluk merkezi bekletme ilkeleri  <br/> | `mbxcdbbb86ce60342489bff371876e7f224` <br/> veya  <br/>  `skp127d7cf1076947929bf136b7a2a8c36f` <br/> |**Get-Mailbox cmdlet'ini** çalıştırabilirsiniz, *InPlaceHolds* özelliği de posta kutusuna uygulanan GUID bekletme ilkeleri içerir. GUID ön ekle başladığından bekletme ilkelerini tanımlayabilirsiniz  `mbx` . Bekletme ilkesi GUID değeri ön `skp` ekle başlıyorsa, bekletme ilkesi bu konuşmalara uygulanmış Skype Kurumsal olur.  <br/> Posta kutusuna uygulanan bekletme ilkesine kimlik bilgileri sağlamak için, Güvenlik ve Uyumluluk Merkezi PowerShell'de & çalıştırın: <br/> <br/>`Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name`<br/><br/>Bu komutu çalıştıracakken veya  `mbx` ön  `skp` eki kaldıracak şekilde emin olun.  <br/> |
|Kuruluş genelindeki bekletme ilkeleri Microsoft 365 uyumluluk merkezi  <br/> |Değer yok  <br/> veya  <br/>  `-mbxe9b52bf7ab3b46a286308ecb29624696` (posta kutusunun kuruluş genelindeki bir ilkenin dışında tutularak dışlan bir posta kutusu olduğunu gösterir)  <br/> |**Get-Mailbox** cmdlet'ini çalıştırsanız bile *InPlaceHolds* özelliği boş olsa bile, posta kutusuna uygulanmış bir veya birden çok kuruluş genelinde bekletme ilkesi olabilir.  <br/> Bunu doğrulamak için, `Get-OrganizationConfig | FL InPlaceHolds` PowerShell'Exchange Online'de çalıştırarak kuruluş genelindeki bekletme ilkelerine yönelik GUID'lerin bir listesini eldeebilirsiniz. Posta kutularına uygulanan kuruluş genelinde saklama ilkelerine Exchange GUID ön `mbx` ekiyle başlar; örneğin, `mbxa3056bb15562480fadb46ce523ff7b02`.  <br/> Posta kutusuna uygulanan kuruluş genelindeki bekletme ilkesine kimlik bilgileri sağlamak için, Güvenlik ve Uyumluluk Merkezi PowerShell'de & komutunu çalıştırın: <br/><br/> `Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name`<br/><br/>Posta kutusu kuruluş genelindeki bir bekletme ilkesi dışında tutulacaksa, **Get-Mailbox** cmdlet'ini çalıştırarak kullanıcının posta kutusunun *InPlaceHolds* özelliğinde bekletme ilkesine ait GUID görüntülenir; önek ile tanımlanır`-mbx`; örneğin,`-mbxe9b52bf7ab3b46a286308ecb29624696` <br/> |
|eBulma olay durumunda Microsoft 365 uyumluluk merkezi  <br/> | `UniH7d895d48-7e23-4a8d-8346-533c3beac15d` <br/> |*InPlaceHolds* özelliği, posta kutusuna yerleştiril bir eKbulma durumuyla ilişkilendirilmiş Microsoft 365 uyumluluk merkezi GUID değeri de içerir. Guid ön ek ile başladığından, bunun bir eBulma durumu olduğunu anlarız  `UniH` .  <br/> `Get-CaseHoldPolicy` Bu cmdlet'i Güvenlik & Uyumluluk Merkezi PowerShell'de kullanarak posta kutusunda tutmanın ilişkilendirilen eKbulma durumu hakkında bilgi edinebilirsiniz. Örneğin, posta kutusunda yer  `Get-CaseHoldPolicy <hold GUID without prefix> | FL Name` alan vaka tutma adını görüntülemek için komutu çalıştırabilirsiniz. Bu komutu çalıştıracakken  `UniH` öneki kaldırmayı emin olun.  <br/><br/> Posta kutusunda tutmanın ilişkilendirilen eBulma olaylarını kimlik bilgileri için, aşağıdaki komutları çalıştırın:<br/><br/>`$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>`<br/><br/>`Get-ComplianceCase $CaseHold.CaseId | FL Name`
