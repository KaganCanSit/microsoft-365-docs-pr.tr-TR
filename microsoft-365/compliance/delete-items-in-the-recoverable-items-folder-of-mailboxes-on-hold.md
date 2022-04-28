---
title: Kurtarılabilir Öğeler klasöründeki öğeleri silme
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Yöneticilerin, kullanıcının Exchange Online posta kutusu için Kurtarılabilir Öğeler klasöründeki öğeleri, bu posta kutusu yasal beklemeye alınsa bile nasıl silebileceğini öğrenin.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 808bc02eb711ff72ec8bd329b1367145d2d991a9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091753"
---
# <a name="delete-items-in-the-recoverable-items-folder-of-cloud-based-mailboxes-on-hold"></a>Beklemedeki bulut tabanlı posta kutularının Kurtarılabilir Öğeler klasöründeki öğeleri silme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Bir Exchange Online posta kutusunun Kurtarılabilir Öğeler klasörü, yanlışlıkla veya kötü amaçlı silme işlemlerine karşı korunmak için mevcuttur. Ayrıca saklamalar ve eBulma aramaları gibi uyumluluk özellikleri tarafından tutulan ve erişilen öğeleri depolamak için de kullanılır. Ancak bazı durumlarda kuruluşların istemeden silmeleri gereken Kurtarılabilir Öğeler klasöründe tutulan verileri olabilir. Örneğin, bir kullanıcı ciddi iş sonuçlarına yol açabilecek hassas bilgiler veya bilgiler içeren bir e-posta iletisini bilmeden gönderebilir veya iletebilir. İleti kalıcı olarak silinse bile, posta kutusuna yasal bir saklama yerleştirildiği için ileti süresiz olarak tutulabilir. Veriler yanlışlıkla Office 365 *taştığı* için bu senaryo veri *taşması* olarak bilinir. Bu gibi durumlarda, kullanıcının Exchange Online posta kutusu için Kurtarılabilir Öğeler klasöründeki öğeleri silebilirsiniz. Bu posta kutusu, Office 365'daki farklı ayrı tutma özelliklerinden biriyle ayrı tutulsa bile. Bu tür ayrı tutmalar arasında Dava Tutmaları, In-Place Tutmalar, eBulma tutmaları ve Office 365 veya Microsoft 365 güvenlik ve uyumluluk merkezinde oluşturulan saklama ilkeleri yer alır.

Bu makalede, yöneticilerin bekleyen bulut tabanlı posta kutuları için Kurtarılabilir Öğeler klasöründeki öğeleri nasıl silebileceği açıklanmaktadır. Bu yordam, posta kutusuna erişimi devre dışı bırakmayı ve tek öğe kurtarmayı devre dışı bırakmayı, Yönetilen Klasör Yardımcısı'nın posta kutusunu işlemesini devre dışı bırakmayı, bekletmeyi geçici olarak kaldırmayı, Kurtarılabilir Öğeler klasöründeki öğeleri silmeyi ve sonra posta kutusunu önceki yapılandırmasına geri döndürmeyi içerir. İşlem şu şekildedir:
  
[1. Adım: Posta kutusu hakkında bilgi toplama](#step-1-collect-information-about-the-mailbox)

[2. Adım: Posta kutusunu hazırlama](#step-2-prepare-the-mailbox)

[3. Adım: Posta kutusundan tüm ayrı tutmaları kaldırma](#step-3-remove-all-holds-from-the-mailbox)

[4. Adım: Posta kutusundan gecikmeli saklamayı kaldırma](#step-4-remove-the-delay-hold-from-the-mailbox)

[5. Adım: Kurtarılabilir Öğeler klasöründeki öğeleri silme](#step-5-delete-items-in-the-recoverable-items-folder)

[6. Adım: Posta kutusunu önceki durumuna geri döndürme](#step-6-revert-the-mailbox-to-its-previous-state)
  
> [!CAUTION]
> Bu makalede açıklanan yordamlar, verilerin bir Exchange Online posta kutusundan kalıcı olarak silinmesine (temizlenmesine) neden olur. Bu, Kurtarılabilir Öğeler klasöründen sildiğiniz iletilerin kurtarılmayacağı ve yasal bulma veya diğer uyumluluk amaçları için kullanılamayacağı anlamına gelir. Microsoft Purview uyumluluk portalında oluşturulan bir Dava Tutma, In-Place Ayrı Tutma, eBulma bekletme veya bekletme ilkesinin parçası olarak ayrı tutmada bulunan bir posta kutusundan iletileri silmek istiyorsanız, saklamayı kaldırmadan önce kayıt yönetiminize veya hukuk departmanlarınıza danışın. Kuruluşunuzun beklemedeki posta kutusunun mı yoksa veri taşması olayının mı öncelikli olduğunu tanımlayan bir ilkesi olabilir.
  
## <a name="before-you-delete-items"></a>Öğeleri silmeden önce

- İçerik Araması oluşturmak ve çalıştırmak için eBulma Yöneticisi rol grubunun üyesi olmanız veya Uyumluluk Araması yönetim rolüne atanmış olmanız gerekir. İletileri silmek için Kuruluş Yönetimi rol grubunun üyesi olmanız veya Arama ve Temizleme yönetimi rolüne sahip olmanız gerekir. Rol grubuna kullanıcı ekleme hakkında bilgi için bkz. [eBulma izinleri atama](./assign-ediscovery-permissions.md).

- Kuruluş genelinde saklama ilkesine bir posta kutusu atanmışsa, Kurtarılabilir Öğeler klasöründeki öğeleri silebilmek için önce posta kutusunu ilkenin dışında tutmanız gerekir. İlke değişikliğinin eşitlenmesi ve posta kutusunun ilkeden kaldırılması 24 saat kadar sürebilir. Daha fazla bilgi için, bu makalenin [Posta kutusundan tüm ayrı tutmaları kaldırma](#organization-wide-retention-policies) bölümündeki "Kuruluş genelinde saklama ilkeleri" bölümüne bakın.

- Koruma Kilidi kullanılarak kilitlenmiş bir bekletme ilkesiyle bekletme ayarları atanmış bir posta kutusu için bu yordamı gerçekleştiremezsiniz. Bunun nedeni, bu kilidin posta kutusunu ilkeden kaldırmanızı veya dışlamanızı ve posta kutusunda Yönetilen Klasör Yardımcısı'nı devre dışı bırakmanızı engellemesidir. Bekletme için ilkeleri kilitleme hakkında daha fazla bilgi için bkz [. Bekletme ilkeleri ve bekletme etiketi ilkelerindeki değişiklikleri kısıtlamak için Koruma Kilidi'ni kullanma](retention-preservation-lock.md).

- Bu makalede açıklanan yordam etkin olmayan posta kutuları için desteklenmez. Bunun nedeni, bir saklamayı (veya bekletme ilkesini) kaldırdıktan sonra etkin olmayan bir posta kutusuna yeniden uygulamamanızdan kaynaklanabilir. Etkin olmayan bir posta kutusundan ayrı tutmayı kaldırdığınızda, normal geçici olarak silinen posta kutusuna dönüştürülür ve Yönetilen Klasör Yardımcısı tarafından işlendikten sonra kuruluşunuzdan kalıcı olarak silinir.

- Posta kutusu beklemeye alınmazsa (veya tek öğe kurtarma etkin değilse), öğeleri Kurtarılabilir Öğeler klasöründen silebilirsiniz. Bunun nasıl yapacağı hakkında daha fazla bilgi için bkz [. Kuruluşunuzda e-posta iletilerini arama ve silme](./search-for-and-delete-messages-in-your-organization.md).

## <a name="step-1-collect-information-about-the-mailbox"></a>1. Adım: Posta kutusu hakkında bilgi toplama

Bu ilk adım, bu yordamı etkileyecek hedef posta kutusundan seçilen özellikleri toplamaktır. Bu özelliklerin bazılarını değiştirip Kurtarılabilir Öğeler klasöründeki öğeleri sildikten sonra 6. Adım'daki özgün değerlere geri döneceğinizden, bu ayarları not almayı veya bir metin dosyasına kaydetmeyi unutmayın. Burada, toplamanız gereken posta kutusu özelliklerinin listesi yer alır.
  
- *SingleItemRecoveryEnabled*  ve  *RetainDeletedItemsFor*. Gerekirse, 3. Adımda tek kurtarmayı devre dışı bırakır ve silinen öğelerin saklama süresini artırırsınız.

- *LitigationHoldEnabled*  ve  *InPlaceHolds*. 3. Adımda bunları geçici olarak kaldırabilmek için posta kutusuna yerleştirilen tüm ayrı tutmaları tanımlamanız gerekir. Posta kutusuna yerleştirilebilen tür ayrı tutmasını tanımlama hakkında ipuçları için [Daha fazla bilgi](#more-information) bölümüne bakın.

Ayrıca, sahibin (veya diğer kullanıcıların) bu yordam sırasında posta kutusuna erişememeleri için bunları geçici olarak devre dışı bırakabilmeniz için posta kutusu istemci erişim ayarlarını almanız gerekir. Son olarak, Kurtarılabilir Öğeler klasöründeki geçerli boyutu ve öğe sayısını alabilirsiniz. 5. Adımda Kurtarılabilir Öğeler klasöründeki öğeleri sildikten sonra, öğelerin kaldırıldığını doğrulamak için bu bilgileri kullanacaksınız.
  
1. [PowerShell'i Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell). Exchange Online'de uygun yönetim rollerine atanmış bir yönetici hesabı için kullanıcı adı ve parola kullandığınızdan emin olun.

2. Tek öğe kurtarma ve silinen öğe saklama süresi hakkında bilgi almak için aşağıdaki komutu çalıştırın.

    ```powershell
    Get-Mailbox <username> | FL SingleItemRecoveryEnabled,RetainDeletedItemsFor
    ```

   Tek öğe kurtarma etkinleştirildiyse, 2. Adım'da bu öğeyi devre dışı bırakmanız gerekir. Silinen öğe saklama süresi 30 gün (Exchange Online içindeki en büyük değer) için ayarlanmadıysa, 2. Adımda bu süreyi artırabilirsiniz.

3. Posta kutusunun posta kutusu erişim ayarlarını almak için aşağıdaki komutu çalıştırın.

    ```powershell
    Get-CASMailbox <username> | FL EwsEnabled,ActiveSyncEnabled,MAPIEnabled,OWAEnabled,ImapEnabled,PopEnabled
    ```

   2. Adımda bu erişim yöntemlerinin tümünü devre dışı bırakacaksınız.

4. Posta kutusuna uygulanan saklama ve bekletme ilkeleri hakkında bilgi almak için aşağıdaki komutu çalıştırın.

    ```powershell
    Get-Mailbox <username> | FL LitigationHoldEnabled,InPlaceHolds
    ```

    > [!TIP]
    > *InPlaceHolds* özelliğinde çok fazla değer varsa ve bunların tümü görüntülenmiyorsa, her değeri ayrı bir satırda görüntülemek için komutunu çalıştırabilirsiniz`Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds`.
  
5. Kuruluş genelinde saklama ilkeleri hakkında bilgi almak için aşağıdaki komutu çalıştırın. 

    ```powershell
    Get-OrganizationConfig | FL InPlaceHolds
    ```

   Kuruluşunuzda kuruluş genelinde bekletme ilkeleri varsa, 3. Adım'da posta kutusunu bu ilkelerin dışında tutmanız gerekir. Değişikliğin çoğaltılması 24 saat kadar sürebilir.

    > [!TIP]
    > *InPlaceHolds* özelliğinde çok fazla değer varsa ve bunların tümü görüntülenmiyorsa, her değeri ayrı bir satırda görüntülemek için komutunu çalıştırabilirsiniz`Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds`. 
  
6. Posta kutusuna gecikmeli saklama uygulanup uygulanmadığını belirlemek için aşağıdaki komutu çalıştırın.

   ```powershell
   Get-Mailbox <username> | FL DelayHoldApplied,DelayReleaseHoldApplied
   ```

   *DelayHoldApplied* veya *DelayReleaseHoldApplied* özelliğinin değeri **True** olarak ayarlandıysa, posta kutusuna bir gecikme bekletme uygulanır ve kaldırılması gerekir. Gecikmeli saklamalar hakkında daha fazla bilgi için bkz [. 4. Adım: Gecikme saklamayı posta kutusundan kaldırma](#step-4-remove-the-delay-hold-from-the-mailbox).

   Her iki özelliğin değeri **False** olarak ayarlanırsa, posta kutusuna gecikmeli saklama uygulanmaz ve 4. Adımı atlayabilirsiniz.

7. Kullanıcının birincil posta kutusunun Kurtarılabilir Öğeler klasöründeki klasörler ve alt klasörlerdeki geçerli boyutu ve toplam öğe sayısını almak için aşağıdaki komutu çalıştırın.

    ```powershell
    Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
    ```

   Kullanıcının arşiv posta kutusu etkinse, arşiv posta kutusunun Kurtarılabilir Öğeler klasöründeki klasörler ve alt klasörlerdeki öğelerin boyutunu ve toplam sayısını almak için aşağıdaki komutu çalıştırın. 

    ```powershell
    Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems -Archive | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
    ```

   5. Adım'daki öğeleri sildiğinizde, kullanıcının birincil arşiv posta kutusunun Kurtarılabilir Öğeler klasöründeki öğeleri silmeyi veya silmemeyi seçebilirsiniz. Posta kutusu için otomatik genişletme arşivleme etkinleştirildiyse, yardımcı arşiv posta kutusunda bulunan öğeler silinmez.
  
## <a name="step-2-prepare-the-mailbox"></a>2. Adım: Posta kutusunu hazırlama

Posta kutusu hakkında bilgi topladıktan ve kaydettikten sonra, sonraki adım aşağıdaki görevleri gerçekleştirerek posta kutusunu hazırlamaktır:
  
- Posta **kutusu sahibinin posta kutusuna erişememesini** ve bu yordam sırasında posta kutusu verilerinde değişiklik yapmasını sağlamak için posta kutusuna istemci erişimini devre dışı bırakın.

- 5. Adımda öğeleri silmeden önce öğelerin Kurtarılabilir Öğeler klasöründen temizlenmemesi için **silinmiş öğe saklama süresini** 30 güne (Exchange Online en yüksek değer) artırın.

- 5. Adım'daki Kurtarılabilir Öğeler klasöründen öğeleri sildikten sonra öğelerin (silinmiş öğe saklama süresi boyunca) saklanmaması için **tek Öğe kurtarmayı devre dışı bırakın**.

- **Yönetilen Klasör Yardımcısı'nı devre dışı bırakın** ; böylece posta kutusunu işlemez ve 5. Adımda sildiğiniz öğeleri korur.

Exchange Online PowerShell'de aşağıdaki adımları gerçekleştirin.
  
1. Posta kutusuna tüm istemci erişimini devre dışı bırakmak için aşağıdaki komutu çalıştırın. Komut söz dizimi, posta kutusunda tüm istemci erişim yöntemlerinin etkinleştirildiğini varsayar.

    ```powershell
    Set-CASMailbox <username> -EwsEnabled $false -ActiveSyncEnabled $false -MAPIEnabled $false -OWAEnabled $false -ImapEnabled $false -PopEnabled $false
    ```

    > [!NOTE]
    > Posta kutusuna tüm istemci erişim yöntemlerini devre dışı bırakmak 60 dakika kadar sürebilir. Bu erişim yöntemlerini devre dışı bırakmanın, şu anda oturum açmış olmaları durumunda posta kutusu sahibinin bağlantısının kesmeyeceğini unutmayın. Sahip oturum açmadıysa, bu erişim yöntemleri devre dışı bırakıldıktan sonra posta kutularına erişemez.
  
2. Silinen öğe saklama süresini en fazla 30 gün artırmak için aşağıdaki komutu çalıştırın. Bu, geçerli ayarın 30 günden az olduğunu varsayar.

    ```powershell
    Set-Mailbox <username> -RetainDeletedItemsFor 30
    ```

3. Tek öğe kurtarmayı devre dışı bırakmak için aşağıdaki komutu çalıştırın.

    ```powershell
    Set-Mailbox <username> -SingleItemRecoveryEnabled $false
    ```

    > [!NOTE]
    > Tek öğe kurtarmayı devre dışı bırakmak 240 dakika kadar sürebilir. Bu süre geçene kadar Kurtarılabilir Öğeler klasöründeki öğeleri silmeyin.
  
4. Yönetilen Klasör Yardımcısı'nın posta kutusunu işlemesini önlemek için aşağıdaki komutu çalıştırın. Daha önce açıklandığı gibi, Yönetilen Klasör Yardımcısı'nı devre dışı bırakabilmeniz için posta kutusuna Koruma Kilidi olan bir bekletme ilkesi uygulanmaması gerekir.

    ```powershell
    Set-Mailbox <username> -ElcProcessingDisabled $true
    ```

## <a name="step-3-remove-all-holds-from-the-mailbox"></a>3. Adım: Posta kutusundan tüm ayrı tutmaları kaldırma

Kurtarılabilir Öğeler klasöründeki öğeleri silmeden önceki son adım, posta kutusuna yerleştirilen tüm ayrı tutmaları (1. Adımda tanımladığınız) kaldırmaktır. Öğelerin Kurtarılabilir Öğeler klasöründen silindikten sonra korunmaması için tüm ayrı tutmalar kaldırılmalıdır. Aşağıdaki bölümlerde, bir posta kutusunda farklı türlerdeki ayrı tutmaların kaldırılmasıyla ilgili bilgiler yer almaktadır. Posta kutusuna yerleştirilebilen tür ayrı tutmasını tanımlama hakkında ipuçları için [Daha fazla bilgi](#more-information) bölümüne bakın. Daha fazla bilgi için bkz. [Exchange Online posta kutusuna yerleştirilmiş saklama türünü tanımlama](identify-a-hold-on-an-exchange-online-mailbox.md).
  
> [!CAUTION]
> Daha önce belirtildiği gibi, posta kutusundan ayrı tutma işlemini kaldırmadan önce kayıt yönetiminize veya hukuk departmanlarınıza danışın.
  
### <a name="litigation-hold"></a>Dava Tutma
  
Exchange Online PowerShell'de aşağıdaki komutu çalıştırarak posta kutusundan Bir Dava Ayrı Tutmasını kaldırın.

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $false
```

> [!NOTE]
> Tek öğeli kurtarmayı devre dışı bırakmaya benzer şekilde, Dava Tutma'nın kaldırılması 240 dakika kadar sürebilir. Bu süre geçene kadar Kurtarılabilir Öğeler klasöründeki öğeleri silmeyin.
  
### <a name="in-place-hold"></a>In-Place Tutma
  
Exchange Online PowerShell'de aşağıdaki komutu çalıştırarak posta kutusuna yerleştirilen In-Place Ayrı Tut'u belirleyin. 1. Adımda tanımladığınız In-Place Ayrı Tutma için GUID kullanın.

```powershell
Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL Name
```

In-Place Ayrı Tutma'yı belirledikten sonra, posta kutusunu ayrı tutmadan kaldırmak için <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezini (EAC)</a> veya PowerShell'i Exchange Online kullanabilirsiniz. Daha fazla bilgi için bkz. [In-Place Ayrı Tutma oluşturma veya kaldırma](/exchange/security-and-compliance/create-or-remove-in-place-holds).
  
### <a name="retention-policies-applied-to-specific-mailboxes"></a>Belirli posta kutularına uygulanan bekletme ilkeleri
  
Posta kutusuna uygulanan bekletme ilkesini belirlemek için [Güvenlik & Uyumluluk Merkezi PowerShell'de](/powershell/exchange/connect-to-scc-powershell) aşağıdaki komutu çalıştırın. Bu komut, posta kutusuna uygulanan Teams konuşma bekletme ilkelerini de döndürür. 1. Adımda tanımladığınız bekletme ilkesi için GUID'yi (veya `skp` ön eki dahil `mbx` değil) kullanın.

```powershell
Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name
```

Bekletme ilkesini tanımladıktan sonra uyumluluk portalında **Veri yaşam döngüsü** **yönetimiYenileştirme** >  sayfasına gidin, önceki adımda tanımladığınız bekletme ilkesini düzenleyin ve posta kutusunu bekletme ilkesine dahil edilen alıcılar listesinden kaldırın.
  
### <a name="organization-wide-retention-policies"></a>Kuruluş genelinde saklama ilkeleri
  
Kuruluş genelinde, Exchange genelinde ve Teams genelinde saklama ilkeleri kuruluştaki her posta kutusuna uygulanır. Bunlar kuruluş düzeyinde (posta kutusu düzeyinde değil) uygulanır ve 1. Adımda **Get-OrganizationConfig** cmdlet'ini çalıştırdığınızda döndürülür. Kuruluş genelinde saklama ilkelerini tanımlamak için [Güvenlik & Uyumluluk Merkezi PowerShell'de](/powershell/exchange/exchange-online-powershell) aşağıdaki komutu çalıştırın. 1. Adımda tanımladığınız kuruluş genelinde saklama ilkeleri için GUID'yi (ön ek dahil  `mbx` değil) kullanın.

```powershell
Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name
```

Kuruluş genelinde saklama ilkelerini tanımladıktan sonra, uyumluluk portalında **Veri yaşam döngüsü** **yönetimiYenileştirme** >  sayfasına gidin, önceki adımda tanımladığınız kuruluş genelindeki her saklama ilkesini düzenleyin ve posta kutusunu dışlanan alıcılar listesine ekleyin. Bunu yaptığınızda kullanıcının posta kutusu bekletme ilkesinden kaldırılır.

> [!IMPORTANT]
> Bir posta kutusunu kuruluş genelinde saklama ilkesinden dışladıktan sonra, bu değişikliğin eşitlenmesi ve posta kutusunun ilkeden kaldırılması 24 saat kadar sürebilir.

### <a name="retention-labels"></a>Bekletme etiketleri

Bir kullanıcı, içeriği korumak veya saklamak ve sonra posta kutularındaki herhangi bir klasöre veya öğeye içerik silmek için yapılandırılmış bir etiket uyguladığında *ComplianceTagHoldApplied* posta kutusu özelliği **True** olarak ayarlanır. Bu durumda, posta kutusu, Dava Tutma'ya yerleştirilmiş veya bir saklama ilkesine atanmış gibi ayrı tutulmuş olarak kabul edilir.

*ComplianceTagHoldApplied* özelliğinin değerini görüntülemek için Exchange Online PowerShell'de aşağıdaki komutu çalıştırın:

```powershell
Get-Mailbox <username> |FL ComplianceTagHoldApplied
```

Bir klasöre veya öğeye bekletme etiketi uygulandığı için posta kutusunun beklemede olduğunu belirledikten sonra, Etiketlenmiş öğeleri aramak için Uyumluluk portalındaki İçerik arama aracını kullanarak **Bekletme etiketi** koşulunu kullanabilirsiniz. Daha fazla bilgi için bkz.:

- [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin](retention.md#using-content-search-to-find-all-content-with-a-specific-retention-label) bölümündeki "Belirli bir bekletme etiketine sahip tüm içeriği bulmak için İçerik Arama'yı kullanma" bölümü

- [İçerik Arama için anahtar sözcük sorguları ve arama koşulları bölümündeki "Arama koşulları](keyword-queries-and-search-conditions.md#conditions-for-common-properties)" bölümü.

Etiketler hakkında daha fazla bilgi için bkz. [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin](retention.md).

### <a name="ediscovery-holds"></a>eBulma tutmaları
  
Posta kutusuna uygulanan bir eBulma olayıyla (*eBulma tutmaları* olarak adlandırılır) ilişkili ayrı tutmayı belirlemek için [Güvenlik & Uyumluluk Merkezi PowerShell'de](/powershell/exchange/connect-to-scc-powershell) aşağıdaki komutları çalıştırın. 1. Adımda tanımladığınız eBulma ayrılığı için GUID'yi (ön ek dahil  `UniH` değil) kullanın. İkinci komut, ayrı tutmanın ilişkili olduğu eBulma olayının adını görüntüler; üçüncü komut, ayrı tutmanın adını görüntüler.
  
```powershell
$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>
```

```powershell
Get-ComplianceCase $CaseHold.CaseId | FL Name
```

```powershell
$CaseHold.Name
```

eBulma servis talebinin ve ayrı tutmanın adını belirledikten sonra uyumluluk merkezindeki **eBulma** \> **eBulma** sayfasına gidin, servis talebini açın ve posta kutusunu ayrı tutmadan kaldırın. eBulma ayrı tutmalarını tanımlama hakkında daha fazla bilgi için, [Exchange Online posta kutusuna yerleştirilen ayrı tutma türünü tanımlama](identify-a-hold-on-an-exchange-online-mailbox.md#ediscovery-holds) bölümündeki "eBulma tutmaları" bölümüne bakın.
  
## <a name="step-4-remove-the-delay-hold-from-the-mailbox"></a>4. Adım: Posta kutusundan gecikmeli saklamayı kaldırma

Bir posta kutusundan herhangi bir tür ayrı tutma kaldırıldıktan sonra *DelayHoldApplied* veya *DelayReleaseHoldApplied* posta kutusu özelliğinin değeri **True** olarak ayarlanır. Bu durum, Yönetilen Klasör Yardımcısı'nın posta kutusunu bir sonraki işlediğinde ve bir ayrı tutmanın kaldırıldığını algıladığından oluşur. Bu *gecikmeli saklama* olarak adlandırılır ve verilerin posta kutusundan kalıcı olarak silinmesini önlemek için saklamanın gerçek kaldırılmasının 30 gün geciktirildiği anlamına gelir. (Gecikmeli saklamanın amacı, yöneticilere ayrı tutma kaldırıldıktan sonra temizlenecek posta kutusu öğelerini arama veya kurtarma fırsatı vermektir.)  Posta kutusuna bir gecikmeli saklama yerleştirildiğinde, posta kutusu dava ayrı tutmadaymış gibi, sınırsız bir süre boyunca beklemede olarak kabul edilir. 30 gün sonra gecikme saklama süresi dolar ve Microsoft 365 gecikme saklamayı kaldırmayı otomatik olarak dener (*DelayHoldApplied* veya *DelayReleaseHoldApplied* özelliğini **False** olarak ayarlayarak) böylece bekletme kaldırılır. Gecikmeli saklama hakkında daha fazla bilgi için, bir [Exchange Online posta kutusuna yerleştirilmiş saklama türünü tanımlama](identify-a-hold-on-an-exchange-online-mailbox.md#managing-mailboxes-on-delay-hold) bölümündeki "Posta kutularını gecikmeli saklamada yönetme" bölümüne bakın.

*DelayHoldApplied* veya *DelayReleaseHoldApplied* özelliğinin değeri **True** olarak ayarlandıysa, gecikme saklamayı kaldırmak için aşağıdaki komutlardan birini çalıştırın:

```powershell
Set-Mailbox <username> -RemoveDelayHoldApplied
```

Veya

```powershell
Set-Mailbox <username> -RemoveDelayReleaseHoldApplied
```

*RemoveDelayHoldApplied veya RemoveDelayReleaseHoldApplied* parametresini kullanmak için Exchange Online'de Yasal Tutma *rolüne* atanmış olmanız gerekir.

## <a name="step-5-delete-items-in-the-recoverable-items-folder"></a>5. Adım: Kurtarılabilir Öğeler klasöründeki öğeleri silme

Artık Güvenlik & Uyumluluk Merkezi PowerShell'deki [New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch) ve [New-ComplianceSearchAction](/powershell/module/exchange/new-compliancesearchaction) cmdlet'lerini kullanarak Kurtarılabilir Öğeler klasöründeki öğeleri silmeye hazırsınız.

Kurtarılabilir Öğeler klasöründe bulunan öğeleri aramak için *, hedeflenen bir koleksiyon* gerçekleştirmenizi öneririz. Bu, aramanızın kapsamını yalnızca Kurtarılabilir Öğeler klasöründe bulunan öğelerle sınırlandırdığınız anlamına gelir. Bunu yapmak [için hedeflenen koleksiyonlar için İçerik Arama'yı kullanma](use-content-search-for-targeted-collections.md) makalesindeki betiği çalıştırabilirsiniz. Bu betik, hedef Kurtarılabilir Öğeler klasöründeki tüm alt klasörler için klasör kimliği özelliğinin değerini döndürür. Ardından, bu klasörde bulunan öğeleri döndürmek için bir arama sorgusunda klasör kimliğini kullanırsınız.

Bir kullanıcının Kurtarılabilir Öğeler klasöründeki öğeleri arama ve silme işlemine genel bakış aşağıdadır:

1. Hedef kullanıcının posta kutusunda tüm klasörler için klasör kimliklerini döndüren hedeflenen koleksiyon betiğini çalıştırın. Betik, aynı PowerShell oturumunda Exchange Online PowerShell'e ve Güvenlik & Uyumluluğu PowerShell'e bağlanır. Daha fazla bilgi için bkz. [Posta kutusu klasörlerinin listesini almak için betiği çalıştırma](use-content-search-for-targeted-collections.md#step-1-run-the-script-to-get-a-list-of-folders-for-a-mailbox-or-site).

2. Kurtarılabilir Öğeler klasöründeki tüm alt klasörler için klasör kimliklerini kopyalayın. Alternatif olarak, betiğin çıkışını bir metin dosyasına yeniden yönlendirebilirsiniz.

   Kurtarılabilir Öğeler klasöründeki öğeleri arayıp silebileceğiniz alt klasörlerin listesi ve açıklaması aşağıdadır:

   - **Silmeler**: Silinmiş öğe saklama süresi dolmamış geçici olarak silinen öğeleri içerir. Kullanıcılar, Outlook'daki Silinmiş Öğeleri Kurtar aracını kullanarak bu alt klasörden geçici olarak silinen öğeleri kurtarabilir.

   - **DiscoveryHolds**: eBulma saklama veya bekletme ilkesi tarafından korunan sabit silinmiş öğeleri içerir. Bu alt klasör son kullanıcılar tarafından görülemez.

   - **SubstrateHolds**: Teams ve diğer bulut tabanlı uygulamalardan bir saklama ilkesi veya başka bir saklama türü tarafından korunan sabit silinmiş öğeleri içerir. Bu alt klasör son kullanıcılar tarafından görülemez.

3. **New-ComplianceSearch** cmdlet'ini kullanın (Güvenlik & Uyumluluk Merkezi PowerShell'de) veya uyumluluk merkezindeki İçerik arama aracını kullanarak hedef kullanıcının Kurtarılabilir Öğeler klasöründeki öğeleri döndüren bir içerik araması oluşturun. Aramak istediğiniz tüm alt klasörler için arama sorgusuna FolderId değerini ekleyerek bunu yapabilirsiniz. Örneğin, aşağıdaki sorgu Silmeler ve eBulmaHolds alt klasörlerindeki tüm iletileri döndürür:

   ```text
   folderid:<folder ID of Deletions subfolder> OR folderid:<folder ID of DiscoveryHolds subfolder>
   ```

   Klasör kimliği özelliğini kullanan içerik aramalarını çalıştırma hakkında daha fazla bilgi ve örnek için bkz. [Klasör kimliği kullanma veya hedeflenen koleksiyonu gerçekleştirme](use-content-search-for-targeted-collections.md#step-2-use-a-folder-id-or-documentlink-to-perform-a-targeted-collection).

   > [!NOTE]
   > Kurtarılabilir Öğeler klasöründe arama yapmak için **New-ComplianceSearch** cmdlet'ini kullanıyorsanız aramayı çalıştırmak için **Start-ComplianceSearch** cmdlet'ini kullandığınızdan emin olun.

4. İçerik araması oluşturduktan ve silmek istediğiniz öğeleri döndürdüğünü doğruladıktan sonra, önceki adımda oluşturduğunuz içerik araması tarafından döndürülen öğeleri kalıcı olarak silmek için komutunu (Güvenlik & Uyumluluk Merkezi PowerShell'de) kullanın `New-ComplianceSearchAction -Purge -PurgeType HardDelete` . Örneğin, aşağıdaki komuta benzer bir komut çalıştırabilirsiniz:

   ```powershell
   New-ComplianceSearchAction -SearchName "RecoverableItems" -Purge -PurgeType HardDelete
   ```

5. Önceki komutu çalıştırdığınızda posta kutusu başına en fazla 10 öğe silinir. Bu, Kurtarılabilir Öğeler klasöründe silmek istediğiniz tüm öğeleri silmek için komutu birden çok kez çalıştırmanız `New-ComplianceSearchAction -Purge` gerekebileceği anlamına gelir. Ek öğeleri silmek için önce önceki uyumluluk arama temizleme eylemini kaldırmanız gerekir. Bunu cmdlet'ini `Remove-ComplianceSearchAction` çalıştırarak yaparsınız. Örneğin, önceki adımda çalıştırılan temizleme eylemini silmek için aşağıdaki komutu çalıştırın:

   ```powershell
   Remove-ComplianceSearchAction "RecoverableItems_Purge"
   ```

   Bunu yaptıktan sonra, daha fazla öğeyi silmek için yeni bir uyumluluk arama temizleme eylemi oluşturabilirsiniz. Yenisini oluşturmadan önce her temizleme eylemini silmeniz gerekir.

   Uyumluluk arama eylemlerinin listesini almak için cmdlet'ini `Get-ComplianceSearchAction` çalıştırabilirsiniz. Temizleme eylemleri, arama adının sonuna eklenerek tanımlanır `_Purge` .

### <a name="verify-that-items-were-deleted"></a>Öğelerin silindiğini doğrulama

Bir posta kutusunun Kurtarılabilir Öğeler klasöründeki öğeleri başarıyla sildiğinizden emin olmak için, Kurtarılabilir Öğeler klasöründeki öğelerin boyutunu ve sayısını denetlemek için Exchange Online PowerShell'deki **Get-MailboxFolderStatistics** cmdlet'ini kullanın. Bu istatistikleri 1. Adımda topladığınız istatistiklerle karşılaştırabilirsiniz.
  
Kullanıcının birincil posta kutusunun Kurtarılabilir Öğeler klasöründeki klasörler ve alt klasörlerdeki geçerli boyutu ve toplam öğe sayısını almak için içinde aşağıdaki komutu çalıştırın.
  
```powershell
Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
```

Kullanıcının arşiv posta kutusunun Kurtarılabilir Öğeler klasöründeki klasörler ve alt klasörlerdeki öğelerin boyutunu ve toplam sayısını almak için aşağıdaki komutu çalıştırın.

```powershell
Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems -Archive | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
```

## <a name="step-6-revert-the-mailbox-to-its-previous-state"></a>6. Adım: Posta kutusunu önceki durumuna geri döndürme

Son adım, posta kutusunu önceki yapılandırmasına geri döndürmektir. Bu, 2. Adımda değiştirdiğiniz özellikleri sıfırlama ve 3. Adımda kaldırdığınız ayrı tutmaları yeniden uygulama anlamına gelir. Buna şunlar dahildir:
  
- Silinen öğe saklama süresini önceki değerine geri döndürme. Alternatif olarak, bu ayarı Exchange Online en yüksek değer olan 30 güne bırakabilirsiniz.

- Tek öğe kurtarmayı yeniden etkinleştirme.

- sahibin posta kutularına erişebilmesi için istemci erişim yöntemlerini yeniden etkinleştirme.

- Kaldırdığınız saklama ve saklama ilkelerini yeniden uygulama.

- Yönetilen Klasör Yardımcısı'nı posta kutusunu işlemek için yeniden etkinleştirme.

> [!IMPORTANT]
> Posta kutusunu işlemek için Yönetilen Klasör Yardımcısı'nı yeniden etkinleştirmeden önce bir saklama veya saklama ilkesini yeniden uyguladıktan (ve yerinde olduğunu doğruladıktan) sonra 24 saat beklemenizi öneririz.
  
Exchange Online PowerShell'de aşağıdaki adımları (belirtilen sırada) gerçekleştirin.
  
1. Silinen öğe saklama süresini özgün değerine geri döndürmek için aşağıdaki komutu çalıştırın. Bu, önceki ayarın 30 günden az olduğunu varsayar; örneğin, 14 gün.

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

4. 3. Adımda kaldırdığınız ayrı tutmaları yeniden uygulayın. Saklama türüne bağlı olarak aşağıdaki yordamlardan birini kullanın.

    **Dava Tutma**

    Posta kutusu için bir Dava Tutma'yı yeniden etkinleştirmek için aşağıdaki komutu çalıştırın.

    ```powershell
    Set-Mailbox <username> -LitigationHoldEnabled $true
    ```

    **Yerinde Tutma**

    Posta kutusunu In-Place Ayrı Tutma'ya geri eklemek için EAC'yi (veya PowerShell'i Exchange Online) kullanın.

    **Belirli posta kutularına uygulanan bekletme ilkeleri**

    Posta kutusunu bekletme ilkesine geri eklemek için uyumluluk portalını kullanın. Uyumluluk merkezindeki **Veri yaşam döngüsü** **yönetimiYenileştirme** >  sayfasına gidin, bekletme ilkesini düzenleyin ve posta kutusunu bekletme ilkesinin uygulandığı alıcılar listesine yeniden ekleyin.

    **Kuruluş genelinde saklama ilkeleri**

    Kuruluş genelinde veya Exchange genelinde saklama ilkesini ilkenin dışında tutarak kaldırdıysanız, posta kutusunu dışlanan kullanıcılar listesinden kaldırmak için uyumluluk portalını kullanın. Uyumluluk merkezindeki **Veri yaşam döngüsü** **yönetimiYenileştirme** >  sayfasına gidin, kuruluş genelinde bekletme ilkesini düzenleyin ve posta kutusunu dışlanan alıcılar listesinden kaldırın. Bunu yaptığınızda, bekletme ilkesi kullanıcının posta kutusuna yeniden gerçekleştirilir.

    **eBulma büyük/küçük harf tutmaları**

    Posta kutusunu eBulma olayıyla ilişkili ayrı tutmaya geri eklemek için uyumluluk portalını kullanın. **eBulma** >  **Çekirdeği** sayfasına gidin, servis talebini açın ve posta kutusunu ayrı tutmaya geri ekleyin. 

5. Yönetilen Klasör Yardımcısı'nın posta kutusunu yeniden işlemesine izin vermek için aşağıdaki komutu çalıştırın. Daha önce belirtildiği gibi, Yönetilen Klasör Yardımcısı'nı yeniden etkinleştirmeden önce bir saklama veya saklama ilkesini yeniden uygulamadan (ve yerinde olduğunu doğruladıktan) sonra 24 saat beklemenizi öneririz.

    ```powershell
    Set-Mailbox <username> -ElcProcessingDisabled $false
    ```

6. Posta kutusunun önceki yapılandırmasına geri döndürüldüğünü doğrulamak için aşağıdaki komutları çalıştırabilir ve ardından ayarları 1. Adımda topladığınız ayarlarla karşılaştırabilirsiniz.

    ```powershell
    Get-Mailbox <username> | FL ElcProcessingDisabled,InPlaceHolds,LitigationHoldEnabled,RetainDeletedItemsFor,SingleItemRecoveryEnabled
    ```

    ```powershell
    Get-CASMailbox <username> | FL EwsEnabled,ActiveSyncEnabled,MAPIEnabled,OWAEnabled,ImapEnabled,PopEnabled
    ```

## <a name="more-information"></a>Daha fazla bilgi

Get-Mailbox veya **Get-OrganizationConfig** cmdlet'lerini *çalıştırdığınızda InPlaceHolds* özelliğindeki değerlere göre farklı türlerde ayrı tutmaların nasıl  tanımlandığını açıklayan bir tablo aşağıdadır. Daha ayrıntılı bilgi için bkz. [Exchange Online posta kutusuna yerleştirilmiş saklama türünü tanımlama](identify-a-hold-on-an-exchange-online-mailbox.md).

Daha önce açıklandığı gibi, Kurtarılabilir Öğeler klasöründeki öğeleri başarıyla silebilmek için önce posta kutusundan tüm saklama ve bekletme ilkelerini kaldırmanız gerekir.
  
| Ayrı tutma türü | Örnek değer | Ayrı tutma nasıl tanımlanır? |
|:-----|:-----|:-----|
|Dava Tutma  <br/> | `True` <br/> |*LitigationHoldEnabled* özelliği olarak `True`ayarlanır.  <br/> |
|In-Place Tutma  <br/> | `c0ba3ce811b6432a8751430937152491` <br/> |*InPlaceHolds* özelliği, posta kutusuna yerleştirilen In-Place Tutmanın GUID'sini içerir. GUID bir ön ek ile başlamadığından bunun bir In-Place Ayrı Tutma olduğunu anlayabilirsiniz.  <br/> Exchange Online PowerShell'de komutunu kullanarak `Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL` posta kutusunda In-Place Tutma hakkında bilgi alabilirsiniz.  <br/> |
| Uyumluluk portalında belirli posta kutularına uygulanan bekletme ilkeleri  <br/> | `mbxcdbbb86ce60342489bff371876e7f224` <br/> veya  <br/>  `skp127d7cf1076947929bf136b7a2a8c36f` <br/> |**Get-Mailbox** *cmdlet'ini çalıştırdığınızda, InPlaceHolds* özelliği posta kutusuna uygulanan bekletme ilkelerinin GUID'lerini de içerir. GUID ön ekiyle  `mbx` başladığından bekletme ilkelerini tanımlayabilirsiniz. Bekletme ilkesinin GUID'i ön ek ile `skp` başlıyorsa, bekletme ilkesinin Skype Kurumsal konuşmalara uygulandığını gösterir.  <br/> Posta kutusuna uygulanan bekletme ilkesinin kimliğini doğrulamak için Güvenlik & Uyumluluk Merkezi PowerShell'de aşağıdaki komutu çalıştırın: <br/> <br/>`Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name`<br/><br/>Bu komutu çalıştırdığınızda veya `skp` ön ekini `mbx` kaldırdığınızdan emin olun.  <br/> |
|Uyumluluk portalında kuruluş genelinde saklama ilkeleri  <br/> |Değer yok  <br/> veya  <br/>  `-mbxe9b52bf7ab3b46a286308ecb29624696` (posta kutusunun kuruluş genelindeki bir ilkenin dışında tutulduğunu gösterir)  <br/> |**Get-Mailbox** cmdlet'ini çalıştırdığınızda *InPlaceHolds* özelliği boş olsa bile, posta kutusuna bir veya daha fazla kuruluş genelinde bekletme ilkesi uygulanmış olabilir.  <br/> Bunu doğrulamak için, Exchange Online PowerShell'de komutunu çalıştırarak `Get-OrganizationConfig | FL InPlaceHolds` kuruluş genelinde saklama ilkeleri için GUID'lerin listesini alabilirsiniz. Exchange posta kutularına uygulanan kuruluş genelinde bekletme ilkelerinin `mbx` GUID'i ön ekiyle başlar; örneğin, `mbxa3056bb15562480fadb46ce523ff7b02`.  <br/> Posta kutusuna uygulanan kuruluş genelinde saklama ilkesinin kimliğini doğrulamak için Güvenlik & Uyumluluk Merkezi PowerShell'de aşağıdaki komutu çalıştırın: <br/><br/> `Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name`<br/><br/>Bir posta kutusu kuruluş genelinde saklama ilkesinin dışında bırakılırsa, **Get-Mailbox** cmdlet'ini çalıştırdığınızda, bekletme ilkesinin GUID'i kullanıcının posta kutusunun *InPlaceHolds* özelliğinde görüntülenir; ön ek `-mbx`ile tanımlanır; örneğin,`-mbxe9b52bf7ab3b46a286308ecb29624696` <br/> |
|Uyumluluk portalında eBulma servis talebi saklama  <br/> | `UniH7d895d48-7e23-4a8d-8346-533c3beac15d` <br/> |*InPlaceHolds* özelliği, uyumluluk portalında posta kutusuna yerleştirilebilen eBulma olayıyla ilişkili tüm ayrı tutmaların GUID'sini de içerir. GUID ön ekiyle  `UniH` başladığından bunun bir eBulma servis talebi saklama işlemi olduğunu anlayabilirsiniz.  <br/> `Get-CaseHoldPolicy` Güvenlik & Uyumluluk Merkezi PowerShell'deki cmdlet'ini kullanarak posta kutusunda tutma işleminin ilişkili olduğu eBulma olayı hakkında bilgi alabilirsiniz. Örneğin, posta kutusunda bulunan servis talebi saklamanın adını görüntülemek için komutunu  `Get-CaseHoldPolicy <hold GUID without prefix> | FL Name` çalıştırabilirsiniz. Bu komutu çalıştırdığınızda ön eki kaldırdığınızdan  `UniH` emin olun.  <br/><br/> Posta kutusu üzerindeki ayrı tutmanın ilişkili olduğu eBulma olayını kimliklendirmek için aşağıdaki komutları çalıştırın:<br/><br/>`$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>`<br/><br/>`Get-ComplianceCase $CaseHold.CaseId | FL Name`
