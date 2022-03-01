---
title: Durumdaki posta kutuları için Kurtarılabilir Öğe kotasını artırma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: a8bdcbdd-9298-462f-b889-df26037a990c
description: Bir posta kutusunda Kurtarılabilir Öğeler klasörünün boyutunu artırmak için arşiv posta kutusunu etkinleştirin ve otomatik genişleyen arşivlemeyi Microsoft 365.
ms.openlocfilehash: 6465a86bfbf2d7f4eaf933786d15a4747b84dd5f
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010836"
---
# <a name="increase-the-recoverable-items-quota-for-mailboxes-on-hold"></a>Durumdaki posta kutuları için Kurtarılabilir Öğe kotasını artırma

Exchange Online posta kutularına otomatik olarak uygulanan varsayılan bekletme ilkesi Exchange (Varsayılan *MRM* İlkesi Exchange Online olarak adlandırılmıştır) Kurtarılabilir Öğeler adlı bir bekletme etiketi içerir. 14 gün arşive taşı. Bu bekletme etiketi, öğeleri kullanıcının birincil posta kutusunda yer alan Kurtarılabilir Öğeler klasöründen 14 günlük bekletme süresinin sona erdikten sonra kullanıcının arşiv posta kutusunda Kurtarılabilir Öğeler klasörüne taşır. Bunun olması için, kullanıcının arşiv posta kutusunun etkinleştirilmiş olması gerekir. Arşiv posta kutusu etkinleştirilmemişse hiçbir eylem gerçekleştirilebilir ve bu da 14 günlük bekletme süresi sona erdikten sonra, bir posta kutusunun Kurtarılabilir Öğeler klasöründeki öğelerin arşiv posta kutusuna taşınmaz. Saklamadaki bir posta kutusundan hiçbir şey silinmediğinden, özellikle de kullanıcının arşiv posta kutusu etkin değilse Kurtarılabilir Öğeler klasörünün depolama kotası aşılabilir.

Bu sınırı aşma ihtimalini azaltmaya yardımcı olmak için, kurtarılabilir Öğeler klasörünün depolama kotası, bir posta kutusunda saklama yerleştirilmiş durumdayken otomatik olarak 30 GB'tan 100 GB'a Exchange Online. Arşiv posta kutusu etkinleştirilirse, arşiv posta kutusunda Kurtarılabilir Öğeler klasörünün depolama kotası da 30 GB'tan 100 GB'a artırıldı. Exchange Online'de otomatik genişleyen arşivleme özelliği etkinse, Kurtarılabilir Öğeler klasörü de içinde olmak üzere kullanıcının arşiv posta kutusu için toplam depolama kotası 1,5 TB'tır.

 Aşağıdaki tabloda, Kurtarılabilir Öğeler klasörünün depolama kotası özetlenmiştir.

| Kurtarılabilir Öğeler klasörünün konumu | Posta kutuları tutmadı | Posta kutuları tutu |
|:-----|:-----|:-----|
|Birincil posta kutusu |30 GB |100 GB |
|Kurtarılabilir Öğeler klasörü de içinde olmak üzere Arşiv posta kutusu <sup>\*</sup> |1,5 TB |1,5 TB |

> [!NOTE]
> <sup>\*</sup>Arşiv posta kutusunun ilk depolama kotası, arşiv lisansına sahip kullanıcılar için 100 GB Exchange Online (Plan 2) olur. Öte yandan, posta kutularında otomatik genişleyen arşivleme açık olduğunda, hem arşiv posta kutusunun hem de Kurtarılabilir Öğeler klasörünün depolama kotası 110 GB'a artırıldı. Gerektiğinde 1,5 TB'a kadar ek arşiv depolama alanı (Kurtarılabilir Öğeler klasörünü içerir) sağlenir. Otomatik genişleyen arşivleme hakkında daha fazla bilgi için bkz[. Otomatik genişleyen arşivleme hakkında bilgi.](autoexpanding-archiving.md)

Saklamadaki posta kutusunun birincil posta kutusunda Kurtarılabilir Öğeler klasörünün depolama kotası sınırına yaklaşıyorsa, şunları yapabilirsiniz:

- **Arşiv posta kutusunu etkinleştirin ve otomatik genişleyen arşivlemeyi etkinleştirin.** Yalnızca arşiv posta kutusunu etkinleştirerek ve sonra bu klasörde otomatik genişleyen arşivleme özelliğini etkinleştirerek Kurtarılabilir Öğeler klasörü için ek depolama Exchange Online. Bunun sonucunda birincil posta kutusunda Kurtarılabilir Öğeler klasörü için 110 GB, arşiv ve Kurtarılabilir Öğeler klasörü için 1,5 TB'a kadar birleştirilmiş depolama kapasitesi elde edilir. Daha fazla bilgi için bkz [. Arşiv posta kutularını etkinleştirme](enable-archive-mailboxes.md) [ve Otomatik genişleyen arşivlemeyi etkinleştirme](enable-autoexpanding-archiving.md).

    > [!NOTE]
    > Kurtarılabilir Öğeler klasörünün depolama kotasını aşmaya yakın bir posta kutusu için arşivi etkinleştirdikten sonra, Yönetilen Klasör Yardımcısı'nın yardımcıyı posta kutusunu el ile işlemesi için çalıştırmayı ve süresi dolan öğelerin arşiv posta kutusunda Kurtarılabilir Öğeler klasörüne taşınmasını sağlamak iyi olabilir. Yönergeler [için bkz. 4](#optional-step-4-run-the-managed-folder-assistant-to-apply-the-new-retention-settings) . Adım. Kullanıcının posta kutusunda yer alan diğer öğelerin yeni arşiv posta kutusuna taşın olabileceğini unutmayın. Kullanıcıya, arşiv posta kutusunu etkinleştirdikten sonra bunun yaşan geri alın olacağını haber ve düşünebilirsiniz.

- **Posta kutuları için Exchange bekletme ilkesi oluşturun.** Mahkeme In-Place Tutma veya Saklama'daki posta kutuları için arşiv posta kutusunu etkinleştirmenin ve otomatik genişleyen arşivlemenin yanı sıra, saklama amaçlı posta kutuları için özel bir Exchange bekletme ilkesi de oluşturabilirsiniz. Bu, bekletmede olmayan posta kutularına uygulanan Varsayılan MRM İlkesi'den farklı bir bekletme ilkesi uygulamanızı ve bekletme posta kutuları için tasarlanmış bekletme etiketlerini uygulamanızı sağlar. Bu, Kurtarılabilir Öğeler klasörü için yeni bir bekletme etiketi oluşturmayı içerir.

Bu konunun kalan kısmında, posta kutuları için bekletme için özel bir bekletme ilkesi Exchange adım adım yordamlar açıklanmıştır.

[1. Adım: Kurtarılabilir Öğeler klasörü için özel bir bekletme etiketi oluşturma](#step-1-create-a-custom-retention-tag-for-the-recoverable-items-folder)

[2. Adım: Posta Exchange için yeni bir bekletme ilkesi oluşturma](#step-2-create-a-new-exchange-retention-policy-for-mailboxes-on-hold)

[3. Adım: Yeni bekletme Exchange posta kutularına uygulama](#step-3-apply-the-new-exchange-retention-policy-to-mailboxes-on-hold)

[(İsteğe bağlı) 4. Adım: Yönetilen Klasör Yardımcısı'nın yeni bekletme ayarlarını uygulamak için çalıştırma](#optional-step-4-run-the-managed-folder-assistant-to-apply-the-new-retention-settings)

## <a name="step-1-create-a-custom-retention-tag-for-the-recoverable-items-folder"></a>1. Adım: Kurtarılabilir Öğeler klasörü için özel bir bekletme etiketi oluşturma

İlk adım, Kurtarılabilir Öğeler klasörü için özel bir bekletme etiketi (bekletme ilkesi etiketi veya RPT olarak adlandırılan) oluşturmaktır. Daha önce de belirtildiği gibi, bu RPT öğeleri kullanıcının birincil posta kutusunda kurtarılabilir Öğeler klasöründen kullanıcının arşiv posta kutusunda Kurtarılabilir Öğeler klasörüne taşır. Kurtarılabilir Öğeler klasörü için bir RPT oluşturmak üzere PowerShell kullansanız gerekir. Exchange yönetim merkezini (EAC) kullanasınız.

1. [Uzak PowerShell'i kullanarak Exchange Online'a bağlanma](/powershell/exchange/connect-to-exchange-online-powershell)

2. Kurtarılabilir Öğeler klasörü için yeni bir RPT oluşturmak için aşağıdaki komutu çalıştırın:

    ```powershell
    New-RetentionPolicyTag -Name <Name of RPT> -Type RecoverableItems -AgeLimitForRetention <Number of days> -RetentionAction MoveToArchive
    ```

    Örneğin aşağıdaki komut, Kurtarılabilir Öğeler klasörü için "Posta kutuları için 30 gün saklama" adlı ve 30 günlük bekletme süresi olan bir RPT oluşturur. Başka bir ifadeyle, bir öğe 30 gün süreyle Kurtarılabilir Öğeler klasörüne taşındıktan sonra kullanıcının arşiv posta kutusunda Kurtarılabilir Öğeler klasörüne taşınır.

    ```powershell
    New-RetentionPolicyTag -Name "Recoverable Items 30 days for mailboxes on hold" -Type RecoverableItems -AgeLimitForRetention 30 -RetentionAction MoveToArchive
    ```

    > [!TIP]
    > Kurtarılabilir Öğeler RPT için bekletme döneminin (  _AgeLimitForRetention_ parametresiyle tanımlanan), RPT'nin uygulanacak posta kutuları için silinmiş öğe bekletme süresiyle aynı olması önerilir. Bu, silinen öğe bekletme döneminin tamamının, silinmiş öğeleri arşiv posta kutusuna taşınmadan önce kurtarmasını sağlar. Önceki örnekte, posta kutuları için silinmiş öğe bekletme döneminin de 30 gün olduğu varsayımı üzerine bekletme süresi 30 gün olarak ayarlanmıştır. Posta Exchange Online, silinmiş öğeleri varsayılan olarak 14 gün boyunca depolanacak şekilde yapılandırılır. Ancak bu ayarı en çok 30 gün olarak değiştirebilirsiniz. Daha fazla bilgi için bkz[. Posta kutusunda silinmiş öğe bekletme Exchange Online](https://www.microsoft.com/?ref=go).

## <a name="step-2-create-a-new-exchange-retention-policy-for-mailboxes-on-hold"></a>2. Adım: Posta Exchange için yeni bir bekletme ilkesi oluşturma

Sonraki adım, yeni bir bekletme ilkesi oluşturmak ve 1. Adımda oluşturduğunuz Kurtarılabilir Öğeler RPT'si de içinde olmak üzere buna bekletme etiketleri eklemektir. Bu yeni ilke sonraki adımda, temlik durumdaki posta kutularına uygulanacaktır.

Yeni bekletme ilkesi oluşturmadan önce, eklemek istediğiniz ek bekletme etiketlerini seçin. Varsayılan MRM İlkesi'ne eklenen bekletme etiketlerinin listesi ve yeni bekletme etiketleri oluşturma hakkında bilgi için aşağıdakilere bakın:

- [Exchange Online'te Varsayılan Bekletme İlkesi](/exchange/security-and-compliance/messaging-records-management/default-retention-policy)

- [Bekletme İlkesi Etiketlerini destekleyen varsayılan klasörler](/exchange/security-and-compliance/messaging-records-management/default-folders)

- Bekletme İlkesi Oluşturma konusunun "Bekletme [etiketi oluştur](/exchange/security-and-compliance/messaging-records-management/create-a-retention-policy) " bölümü.

EAC veya PowerShell Exchange Online kullanarak bekletme ilkesi oluşturabilirsiniz.

### <a name="use-the-eac-to-create-a-retention-policy"></a>Bekletme ilkesi oluşturmak için EAC kullanma

1. EAC'de, Uyumluluk yönetimi Bekletme **ilkeleri'ne** \> **gidin ve** Simge **Ekle'ye** ![tıklayın](../media/ITPro-EAC-AddIcon.gif).

2. Yeni **bekletme ilkesi sayfasındaki** **Ad'ın** altında, bekletme ilkesi amacını açıklayan bir ad yazın; örneğin, Posta **Kutuları için MRM İlkesi Gibi**.

3. Bekletme **etiketleri'nin altında** Simge **Ekle'ye** ![tıklayın](../media/ITPro-EAC-AddIcon.gif).

4. Bekletme etiketleri listesinde, 1. Adımda oluşturduğunuz Kurtarılabilir Öğeler RPT'yi seçin ve Ekle'ye **tıklayın**.

    ![Özel Kurtarılabilir Öğeler bekletme etiketini seçin.](../media/eb49866b-bdef-4fcd-a6d9-01607c01249b.png)

5. Bekletme ilkesine eklemek için başka bekletme etiketleri seçin. Örneğin, Varsayılan MRM İlkesi'ne dahil edilen etiketlerin aynısını eklemek istiyor olabilir.

6. Bekletme etiketleri eklemeyi bitirdikten sonra Tamam'a **tıklayın**.

7. Yeni **bekletme ilkesi** oluşturmak için Kaydet'e tıklayın.

    Bekletme ilkesine bağlı bekletme etiketlerinin ayrıntılar bölmesinde görüntülendiğinden dikkat edin.

    ![Bekletme ilkesine bağlı bekletme etiketleri ayrıntılar bölmesinde görüntülenir.](../media/dad1c8f4-9928-4d6d-991a-6f6c5194eceb.png)

### <a name="use-exchange-online-powershell-to-create-a-retention-policy"></a>Bekletme Exchange Online için PowerShell kullanma

Bekletme posta kutuları için yeni bir bekletme ilkesi oluşturmak için aşağıdaki komutu çalıştırın.

```powershell
New-RetentionPolicy <Name of retention policy>  -RetentionPolicyTagLinks <list of retention tags>
```

Örneğin, aşağıdaki komut önceki çizimde gösterilen bekletme ilkesi ve bağlantılı bekletme etiketlerini oluşturur.

```powershell
New-RetentionPolicy "MRM Policy for Mailboxes on Hold"  -RetentionPolicyTagLinks "Recoverable Items 30 days for mailboxes on hold","1 Month Delete","1 Week Delete","1 Year Delete","5 Year Delete","6 Month Delete","Default 2 year move to archive","Junk Email","Never Delete","Personal 1 year move to archive","Personal 5 year move to archive"
```

## <a name="step-3-apply-the-new-exchange-retention-policy-to-mailboxes-on-hold"></a>3. Adım: Yeni bekletme Exchange posta kutularına uygulama

Son adım, 2. Adımda oluşturduğunuz yeni bekletme ilkesi'nin, kurumda saklama olan posta kutularına uygulamaktır. Bekletme Exchange Online bir posta kutusuna veya birden çok posta kutusuna uygulamak için EAC veya PowerShell kullanabilirsiniz.

### <a name="use-the-eac-to-apply-the-new-retention-policy"></a>Yeni bekletme ilkesi uygulamak için EAC kullanma

1. **AlıcılarMailboxes'e** >  **gidin**.

2. Liste görünümünde, bekletme ilkesi uygulamak istediğiniz posta kutusunu seçin ve düzenle **simgesine** ![tıklayın](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).

3. Kullanıcı Posta **Kutusu sayfasında Posta** kutusu **özellikleri'ne tıklayın**.

4. Bekletme **ilkesi'nin** altında, 2. Adımda oluşturduğunuz bekletme ilkesine tıklayın ve ardından Kaydet'e **tıklayın**.

Bekletme ilkeyi birden çok posta kutusuna uygulamak için de EAC'i kullanabilirsiniz.

1. **AlıcılarMailboxes'e** >  **gidin**.

2. Liste görünümünde, birden çok posta kutusu seçmek için Shift veya Ctrl tuşlarını kullanın.

3. Ayrıntılar bölmesinde Diğer **seçenekler'e tıklayın**.

4. Bekletme **İlkesi'nin altında** **Güncelleştir'e tıklayın**.

5. Toplu bekletme **ilkesi atama sayfasında** , 2. Adımda oluşturduğunuz bekletme ilkesine tıklayın ve ardından Kaydet'e **tıklayın**.

### <a name="use-exchange-online-powershell-to-apply-the-new-retention-policy"></a>Yeni Exchange Online ilkeyi uygulamak için PowerShell'i kullanma

Exchange Online PowerShell kullanarak tek bir posta kutusuna yeni bir bekletme ilkesi uygulayabilirsiniz. Ancak PowerShell'in gerçek gücü, bu özelliği kullanarak, kurumda Mahkeme Tutma veya In-Place Bekletme'ye sahip olan tüm posta kutularını hızla tanımlamak ve ardından yeni bekletme ilkeyi tek bir komutta bekletme tüm posta kutularına uygulayabilecek şekilde uygulayabiliyor olmaktır. Bir veya birden çok posta kutusuna bekletme Exchange için PowerShell kullanımıyla ilgili bazı örnekler aşağıda verilmiştir. Örneklerin hepsi, 2. Adımda oluşturulan bekletme ilkesine uygulanır.

Bu örnekte, yeni bekletme ilkesi Pilar Pinilla'nın posta kutusuna uygulanır.

```powershell
Set-Mailbox "Pilar Pinilla" -RetentionPolicy "MRM Policy for Mailboxes on Hold"
```

Bu örnekte, yeni bekletme ilkesi, kuruluşta Mahkeme Tutmada olan tüm posta kutularına uygulanır.

```powershell
$LitigationHolds = Get-Mailbox -ResultSize unlimited | Where-Object {$_.LitigationHoldEnabled -eq 'True'}
```

```powershell
$LitigationHolds.DistinguishedName | Set-Mailbox -RetentionPolicy "MRM Policy for Mailboxes on Hold"
```

Bu örnekte, yeni bekletme ilkesi kuruluşta saklama uygulanan tüm posta kutularına In-Place uygulanır.

```powershell
$InPlaceHolds = Get-Mailbox -ResultSize unlimited | Where-Object {$_.InPlaceHolds -ne $null}
```

```powershell
$InPlaceHolds.DistinguishedName | Set-Mailbox -RetentionPolicy "MRM Policy for Mailboxes on Hold"
```

Yeni bekletme ilkesi **uygulandığını doğrulamak için Get-Mailbox** cmdlet'ini kullanabilirsiniz.

Önceki örneklerde yer alan komutların, Mahkeme Tutma'daki posta kutularına ve Bekletme'de posta kutularına "Bekletme Posta Kutuları için MRM İlkesi" saklama ilkesi uygulandığını doğrulamak için bazı In-Place verilmiştir.

```powershell
Get-Mailbox "Pilar Pinilla" | Select RetentionPolicy
```

```powershell
Get-Mailbox -ResultSize unlimited | Where-Object {$_.LitigationHoldEnabled -eq 'True'} | FT DisplayName,RetentionPolicy -Auto
```

```powershell
Get-Mailbox -ResultSize unlimited | Where-Object {$_.InPlaceHolds -ne $null} | FT DisplayName,RetentionPolicy -Auto
```

## <a name="optional-step-4-run-the-managed-folder-assistant-to-apply-the-new-retention-settings"></a>(İsteğe bağlı) 4. Adım: Yönetilen Klasör Yardımcısı'nın yeni bekletme ayarlarını uygulamak için çalıştırma

Yeni Exchange bekletme Exchange Online posta kutularına uygulaytıktan sonra, Yönetilen Klasör Yardımcısı'nın yeni bekletme ilkesinde yer alan ayarları kullanarak bu posta kutularını işlemesi Exchange Online içinde 7 gün kadar zaman alabiliyor. Yönetilen Klasör Yardımcısı'nın çalışması için beklemek yerine, **start-ManagedFolderAssistant** cmdlet'ini kullanarak yardımcıyı yeni bekletme ilkesi uyguladınız posta kutularını el ile tetikleyebilirsiniz.

Pilar Pinilla'nın posta kutusu için Yönetilen Klasör Yardımcısı'na başlamak üzere aşağıdaki komutu çalıştırın.

```powershell
Start-ManagedFolderAssistant "Pilar Pinilla"
```

Yönetilen Klasör Yardımcısı'nın tüm posta kutularını tutmak için aşağıdaki komutları çalıştırın.

```powershell
$MailboxesOnHold = Get-Mailbox -ResultSize unlimited | Where-Object {($_.InPlaceHolds -ne $null) -or ($_.LitigationHoldEnabled -eq "True")}
```

```powershell
$MailboxesOnHold.DistinguishedName | Start-ManagedFolderAssistant
```

## <a name="more-information"></a>Daha fazla bilgi

- Kullanıcının arşiv posta kutusunu etkinleştirdikten sonra, kullanıcıya yalnızca Kurtarılabilir Öğeler klasöründeki diğer öğelerin değil, posta kutusunda yer alan diğer öğelerin de arşiv posta kutusuna taşın olabileceğini söylemeniz iyi olabilir. Bunun nedeni, Exchange Online posta kutularına atanan Varsayılan MRM İlkesi'nin öğeleri, öğenin posta kutusuna teslim edildikten veya kullanıcı tarafından oluşturulduktan iki yıl sonra arşiv posta kutusuna taşımaya yönelik bir bekletme etiketi (Varsayılan 2 yıl arşive taşı olarak adlandırılmıştır) içerir. Daha fazla bilgi [için bkz.](/exchange/security-and-compliance/messaging-records-management/default-retention-policy) Exchange Online

- Kullanıcının arşiv posta kutusunu etkinleştirdikten sonra, kullanıcıya arşiv posta kutusunun Kurtarılabilir Öğeler klasöründeki silinmiş öğeleri kurtarabilir. Bu, Outlook kutusunda Silinmiş Öğeler klasörünü seçerek ve ardından Giriş sekmesinde  Silinmiş Öğeleri Sunucudan **Kurtar'a** tıklayarak bu **komutu** kullanabilirler. Silinmiş öğeleri kurtarma hakkında daha fazla bilgi için bkz. Silinmiş [öğeleri Outlook kurtarma Windows](https://go.microsoft.com/fwlink/p/?LinkId=624829).
