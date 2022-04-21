---
title: Beklemedeki posta kutuları için Kurtarılabilir Öğeler kotasını artırma
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
description: arşiv posta kutusunu etkinleştirin ve Microsoft 365 bir posta kutusunun Kurtarılabilir Öğeler klasörünün boyutunu artırmak için otomatik genişletme arşivlemeyi açın.
ms.openlocfilehash: 68ef8cfe1751ed5822d99edf9e7efeb4bd3766f2
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64999904"
---
# <a name="increase-the-recoverable-items-quota-for-mailboxes-on-hold"></a>Beklemedeki posta kutuları için Kurtarılabilir Öğeler kotasını artırma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Exchange Online'daki yeni posta kutularına otomatik olarak uygulanan varsayılan Exchange bekletme *ilkesi (Varsayılan MRM İlkesi* olarak adlandırılır) Kurtarılabilir Öğeler adlı bir bekletme etiketi içerir 14 gün arşive taşınır. Bu bekletme etiketi, bir öğenin 14 günlük saklama süresi dolduktan sonra öğeleri kullanıcının birincil posta kutusunda bulunan Kurtarılabilir Öğeler klasöründen kullanıcının arşiv posta kutusunda Kurtarılabilir Öğeler klasörüne taşır. Bunun gerçekleşmesi için kullanıcının arşiv posta kutusunun etkinleştirilmesi gerekir. Arşiv posta kutusu etkinleştirilmemişse hiçbir eylem yapılmaz; başka bir deyişle, 14 günlük saklama süresi dolduktan sonra, bekleyen bir posta kutusu için Kurtarılabilir Öğeler klasöründeki öğeler arşiv posta kutusuna taşınmaz. Beklemedeki bir posta kutusundan hiçbir şey silinmediğinden, özellikle de kullanıcının arşiv posta kutusu etkinleştirilmemişse Kurtarılabilir Öğeler klasörünün depolama kotası aşılabilir.

Bu sınırı aşma olasılığını azaltmaya yardımcı olmak için, Exchange Online bir posta kutusuna ayrı tutma yerleştirildiğinde Kurtarılabilir Öğeler klasörünün depolama kotası otomatik olarak 30 GB'tan 100 GB'a yükseltilir. Arşiv posta kutusu etkinleştirilirse, arşiv posta kutusunda Kurtarılabilir Öğeler klasörünün depolama kotası da 30 GB'tan 100 GB'a yükseltilir. Exchange Online'da otomatik genişletme arşivleme özelliği etkinleştirilirse, Kurtarılabilir Öğeler klasörü de dahil olmak üzere kullanıcının arşiv posta kutusu için toplam depolama kotası 1,5 TB'tır.

 Aşağıdaki tabloda Kurtarılabilir Öğeler klasörünün depolama kotası özetlemektedir.

| Kurtarılabilir Öğeler klasörünün konumu | Posta kutuları ayrı tutulmuyor | Beklemedeki posta kutuları |
|:-----|:-----|:-----|
|Birincil posta kutusu |30 GB |100 GB |
|Kurtarılabilir Öğeler klasörü de dahil olmak üzere arşiv posta kutusu <sup>\*</sup> |1,5 TB |1,5 TB |

> [!NOTE]
> <sup>\*</sup>Arşiv posta kutusu için ilk depolama kotası, Exchange Online (Plan 2) lisansına sahip kullanıcılar için 100 GB'tır. Ancak, ayrı tutulacak posta kutuları için arşivleme otomatik genişletildiğinde, hem arşiv posta kutusunun hem de Kurtarılabilir Öğeler klasörünün depolama kotası 110 GB'a çıkarılır. Gerektiğinde 1,5 TB'a kadar ek arşiv depolama alanı (Kurtarılabilir Öğeler klasörünü içerir) sağlanır. Arşivlemenin otomatik olarak genişletilmesi hakkında daha fazla bilgi için bkz. [Arşivlemeyi otomatik genişletme hakkında bilgi edinin](autoexpanding-archiving.md).

Bekleyen bir posta kutusunun birincil posta kutusunda Kurtarılabilir Öğeler klasörünün depolama kotası sınırına ulaşmak üzere olduğunda, aşağıdakileri yapabilirsiniz:

- **Arşiv posta kutusunu etkinleştirin ve otomatik genişletme arşivlemeyi açın.** Yalnızca arşiv posta kutusunu etkinleştirip Exchange Online otomatik genişletme arşivleme özelliğini açarak Kurtarılabilir Öğeler klasörü için ek depolama kapasitesi etkinleştirebilirsiniz. Bu, birincil posta kutusunda Kurtarılabilir Öğeler klasörü için 110 GB ve arşiv ve Kurtarılabilir Öğeler klasörü için 1,5 TB'a kadar birleşik depolama kapasitesiyle sonuçlanabilir. Daha fazla bilgi için bkz [. Arşiv posta kutularını etkinleştirme](enable-archive-mailboxes.md) ve [Otomatik genişletme arşivlemeyi etkinleştirme](enable-autoexpanding-archiving.md).

    > [!NOTE]
    > Kurtarılabilir Öğeler klasörünün depolama kotasını aşmaya yakın bir posta kutusu için arşivi etkinleştirdikten sonra, yönetilen klasör yardımcısı'nı çalıştırarak, süresi dolan öğelerin arşiv posta kutusunda Kurtarılabilir Öğeler klasörüne taşınması için yardımcının posta kutusunu işlemesini el ile tetiklemeniz gerekebilir. Yönergeler için bkz [. 4. Adım](#optional-step-4-run-the-managed-folder-assistant-to-apply-the-new-retention-settings) . Kullanıcının posta kutusunda bulunan diğer öğelerin yeni arşiv posta kutusuna taşınabileceğini unutmayın. Kullanıcıya, arşiv posta kutusunu etkinleştirdikten sonra bunun olabileceğini söylemeyi göz önünde bulundurun.

- **Ayrı tutmadaki posta kutuları için özel bir Exchange bekletme ilkesi oluşturun.** Arşiv posta kutusunu etkinleştirmenin yanı sıra, Dava Bekletme veya In-Place Ayrı Tutma'da posta kutuları için arşivlemeyi otomatik olarak genişletmenin yanı sıra, beklemedeki posta kutuları için özel bir Exchange bekletme ilkesi de oluşturmak isteyebilirsiniz. Bu, ayrı tutmada olmayan posta kutularına uygulanan Varsayılan MRM İlkesi'nden farklı bir bekletme ilkesi uygulamanıza olanak tanır ve ayrı tutmadaki posta kutuları için tasarlanmış bekletme etiketleri uygulamanıza olanak tanır. Bu, Kurtarılabilir Öğeler klasörü için yeni bir bekletme etiketi oluşturmayı içerir.

Bu konunun geri kalanında, beklemedeki posta kutuları için özel bir Exchange bekletme ilkesi oluşturmaya yönelik adım adım yordamlar açıklanmaktadır.

[1. Adım: Kurtarılabilir Öğeler klasörü için özel bir bekletme etiketi oluşturma](#step-1-create-a-custom-retention-tag-for-the-recoverable-items-folder)

[2. Adım: Beklemedeki posta kutuları için yeni bir Exchange bekletme ilkesi oluşturma](#step-2-create-a-new-exchange-retention-policy-for-mailboxes-on-hold)

[3. Adım: Yeni Exchange bekletme ilkesini beklemedeki posta kutularına uygulama](#step-3-apply-the-new-exchange-retention-policy-to-mailboxes-on-hold)

[(İsteğe bağlı) 4. Adım: Yeni bekletme ayarlarını uygulamak için Yönetilen Klasör Yardımcısı'nı çalıştırın](#optional-step-4-run-the-managed-folder-assistant-to-apply-the-new-retention-settings)

## <a name="step-1-create-a-custom-retention-tag-for-the-recoverable-items-folder"></a>1. Adım: Kurtarılabilir Öğeler klasörü için özel bir bekletme etiketi oluşturma

İlk adım, Kurtarılabilir Öğeler klasörü için özel bir bekletme etiketi (bekletme ilkesi etiketi veya RPT olarak adlandırılır) oluşturmaktır. Daha önce açıklandığı gibi, bu RPT öğeleri kullanıcının birincil posta kutusunda bulunan Kurtarılabilir Öğeler klasöründen kullanıcının arşiv posta kutusunda Kurtarılabilir Öğeler klasörüne taşır. Kurtarılabilir Öğeler klasörü için bir RPT oluşturmak için PowerShell'i kullanmanız gerekir. Exchange yönetim merkezini (EAC) kullanamazsınız.

1. [Uzak PowerShell'i kullanarak Exchange Online'a bağlanma](/powershell/exchange/connect-to-exchange-online-powershell)

2. Kurtarılabilir Öğeler klasörü için yeni bir RPT oluşturmak için aşağıdaki komutu çalıştırın:

    ```powershell
    New-RetentionPolicyTag -Name <Name of RPT> -Type RecoverableItems -AgeLimitForRetention <Number of days> -RetentionAction MoveToArchive
    ```

    Örneğin aşağıdaki komut, "Bekleyen posta kutuları için Kurtarılabilir Öğeler 30 gün" adlı Kurtarılabilir Öğeler klasörü için 30 günlük saklama süresiyle bir RPT oluşturur. Bu, bir öğenin 30 gün boyunca Kurtarılabilir Öğeler klasöründe yer aldıktan sonra kullanıcının arşiv posta kutusunda Kurtarılabilir Öğeler klasörüne taşınacağı anlamına gelir.

    ```powershell
    New-RetentionPolicyTag -Name "Recoverable Items 30 days for mailboxes on hold" -Type RecoverableItems -AgeLimitForRetention 30 -RetentionAction MoveToArchive
    ```

    > [!TIP]
    > Kurtarılabilir Öğeler RPT'sinin saklama süresinin (  _AgeLimitForRetention_ parametresiyle tanımlanır) RPT'nin uygulanacağı posta kutuları için silinmiş öğe saklama süresiyle aynı olmasını öneririz. Bu, kullanıcının silinmiş öğe saklama süresinin tamamının, silinmiş öğeleri arşiv posta kutusuna taşınmadan önce kurtarmasına olanak tanır. Önceki örnekte, posta kutuları için silinen öğe saklama süresinin de 30 gün olduğu varsayımı temel alınarak saklama süresi 30 gün olarak ayarlanmıştı. Exchange Online posta kutusu, silinmiş öğeleri varsayılan olarak 14 gün boyunca saklayacak şekilde yapılandırılır. Ancak bu ayarı en fazla 30 gün olarak değiştirebilirsiniz. Daha fazla bilgi için bkz. [Exchange Online'da posta kutusunun silinmiş öğe saklama süresini değiştirme](https://www.microsoft.com/?ref=go).

## <a name="step-2-create-a-new-exchange-retention-policy-for-mailboxes-on-hold"></a>2. Adım: Beklemedeki posta kutuları için yeni bir Exchange bekletme ilkesi oluşturma

Sonraki adım, 1. Adımda oluşturduğunuz Kurtarılabilir Öğeler RPT'si dahil olmak üzere yeni bir bekletme ilkesi oluşturmak ve bu ilkeye bekletme etiketleri eklemektir. Bu yeni ilke, sonraki adımda ayrı tutulacak posta kutularına uygulanacaktır.

Yeni bekletme ilkesini oluşturmadan önce, eklemek istediğiniz ek bekletme etiketlerini belirleyin. Varsayılan MRM İlkesi'ne eklenen bekletme etiketlerinin listesi ve yeni bekletme etiketleri oluşturma hakkında bilgi için aşağıdakilere bakın:

- [Exchange Online'da Varsayılan Bekletme İlkesi](/exchange/security-and-compliance/messaging-records-management/default-retention-policy)

- [Bekletme İlkesi Etiketlerini destekleyen varsayılan klasörler](/exchange/security-and-compliance/messaging-records-management/default-folders)

- [Bekletme İlkesi Oluşturma](/exchange/security-and-compliance/messaging-records-management/create-a-retention-policy) konusunun "Bekletme etiketi oluşturma" bölümü.

Bekletme ilkesi oluşturmak için EAC'yi kullanabilir veya PowerShell'i Exchange Online.

### <a name="use-the-eac-to-create-a-retention-policy"></a>Bekletme ilkesi oluşturmak için EAC kullanma

1. EAC'de **, Uyumluluk yönetimi** \> **Bekletme ilkeleri'ne** gidin ve Ardından Ekle Simgesi Ekle.'](../media/ITPro-EAC-AddIcon.gif)**ye** ![tıklayın.

2. **Yeni bekletme ilkesi** sayfasındaki **Ad'ın** altında bekletme ilkesinin amacını açıklayan bir ad yazın; örneğin, **Beklemedeki Posta Kutuları için MRM İlkesi**.

3. **Bekletme etiketleri'nin** altında **Ekle Simgesi'ne** ![tıklayın.](../media/ITPro-EAC-AddIcon.gif).

4. Bekletme etiketleri listesinde, 1. Adımda oluşturduğunuz Kurtarılabilir Öğeler RPT'sini seçin ve **ekle'ye** tıklayın.

    ![Özel Kurtarılabilir Öğeler bekletme etiketini seçin.](../media/eb49866b-bdef-4fcd-a6d9-01607c01249b.png)

5. Bekletme ilkesine eklemek için ek bekletme etiketleri seçin. Örneğin, Varsayılan MRM İlkesi'ne dahil edilen etiketlerin aynısını eklemek isteyebilirsiniz.

6. Bekletme etiketleri eklemeyi bitirdiğinizde **Tamam'a** tıklayın.

7. Yeni bekletme ilkesini oluşturmak için **Kaydet'e** tıklayın.

    Bekletme ilkesine bağlı bekletme etiketlerinin ayrıntılar bölmesinde görüntülendiğine dikkat edin.

    ![Bekletme ilkesine bağlı bekletme etiketleri ayrıntılar bölmesinde görüntülenir.](../media/dad1c8f4-9928-4d6d-991a-6f6c5194eceb.png)

### <a name="use-exchange-online-powershell-to-create-a-retention-policy"></a>Exchange Online PowerShell kullanarak bekletme ilkesi oluşturma

Beklemedeki posta kutuları için yeni bekletme ilkesi oluşturmak için aşağıdaki komutu çalıştırın.

```powershell
New-RetentionPolicy <Name of retention policy>  -RetentionPolicyTagLinks <list of retention tags>
```

Örneğin, aşağıdaki komut önceki çizimde görüntülenen bekletme ilkesini ve bağlı bekletme etiketlerini oluşturur.

```powershell
New-RetentionPolicy "MRM Policy for Mailboxes on Hold"  -RetentionPolicyTagLinks "Recoverable Items 30 days for mailboxes on hold","1 Month Delete","1 Week Delete","1 Year Delete","5 Year Delete","6 Month Delete","Default 2 year move to archive","Junk Email","Never Delete","Personal 1 year move to archive","Personal 5 year move to archive"
```

## <a name="step-3-apply-the-new-exchange-retention-policy-to-mailboxes-on-hold"></a>3. Adım: Yeni Exchange bekletme ilkesini beklemedeki posta kutularına uygulama

Son adım, 2. Adımda oluşturduğunuz yeni bekletme ilkesini kuruluşunuzdaki beklemedeki posta kutularına uygulamaktır. Bekletme ilkesini tek bir posta kutusuna veya birden çok posta kutusuna uygulamak için EAC'yi veya PowerShell'i Exchange Online kullanabilirsiniz.

### <a name="use-the-eac-to-apply-the-new-retention-policy"></a>Yeni bekletme ilkesini uygulamak için EAC'yi kullanma

1. **Alıcılar** >  **Posta Kutuları'na** gidin.

2. Liste görünümünde, bekletme ilkesini uygulamak istediğiniz posta kutusunu seçin ve **düzenle simgesine** tıklayın ![.](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).

3. **Kullanıcı Posta Kutusu** sayfasında **Posta kutusu özellikleri'ne** tıklayın.

4. **Bekletme ilkesi'nin** altında, 2. Adımda oluşturduğunuz bekletme ilkesini seçin ve **kaydet'e** tıklayın.

Bekletme ilkesini birden çok posta kutusuna uygulamak için EAC'yi de kullanabilirsiniz.

1. **Alıcılar** >  **Posta Kutuları'na** gidin.

2. Liste görünümünde, birden çok posta kutusu seçmek için Shift veya Ctrl tuşlarını kullanın.

3. Ayrıntılar bölmesinde **Diğer seçenekler'e** tıklayın.

4. **Bekletme İlkesi'nin** altında **Güncelleştir'e** tıklayın.

5. **Bekletme ilkesini toplu atama** sayfasında, 2. Adımda oluşturduğunuz bekletme ilkesini seçin ve **kaydet'e** tıklayın.

### <a name="use-exchange-online-powershell-to-apply-the-new-retention-policy"></a>Yeni bekletme ilkesini uygulamak için powershell Exchange Online kullanma

Exchange Online PowerShell kullanarak tek bir posta kutusuna yeni bir bekletme ilkesi uygulayabilirsiniz. Ancak PowerShell'in gerçek gücü, kuruluşunuzda Dava Ayrı Tutma veya In-Place Ayrı Tutma'da bulunan tüm posta kutularını hızla tanımlamak ve ardından yeni bekletme ilkesini tek bir komutta ayrı tutmadaki tüm posta kutularına uygulamak için kullanabilmenizdir. Bir veya daha fazla posta kutusuna bekletme ilkesi uygulamak için Exchange PowerShell kullanma örnekleri aşağıda verilmiştir. Tüm örnekler, 2. Adımda oluşturulan bekletme ilkesini uygular.

Bu örnek, yeni bekletme ilkesini Pilar Pinilla'nın posta kutusuna uygular.

```powershell
Set-Mailbox "Pilar Pinilla" -RetentionPolicy "MRM Policy for Mailboxes on Hold"
```

Bu örnek, yeni bekletme ilkesini kuruluştaki Dava Tutma'daki tüm posta kutularına uygular.

```powershell
$LitigationHolds = Get-Mailbox -ResultSize unlimited | Where-Object {$_.LitigationHoldEnabled -eq 'True'}
```

```powershell
$LitigationHolds.DistinguishedName | Set-Mailbox -RetentionPolicy "MRM Policy for Mailboxes on Hold"
```

Bu örnek, kuruluştaki In-Place Ayrı Tutma'da bulunan tüm posta kutularına yeni bekletme ilkesini uygular.

```powershell
$InPlaceHolds = Get-Mailbox -ResultSize unlimited | Where-Object {$_.InPlaceHolds -ne $null}
```

```powershell
$InPlaceHolds.DistinguishedName | Set-Mailbox -RetentionPolicy "MRM Policy for Mailboxes on Hold"
```

Yeni bekletme ilkesinin uygulandığını doğrulamak için **Get-Mailbox** cmdlet'ini kullanabilirsiniz.

Burada, önceki örneklerde yer alan komutların Dava Ayrı Tutma'daki posta kutularına ve In-Place Ayrı Tutma'daki posta kutularına "Beklemedeki Posta Kutuları için MRM İlkesi" bekletme ilkesini uyguladığını doğrulamaya yönelik bazı örnekler verilmiştir.

```powershell
Get-Mailbox "Pilar Pinilla" | Select RetentionPolicy
```

```powershell
Get-Mailbox -ResultSize unlimited | Where-Object {$_.LitigationHoldEnabled -eq 'True'} | FT DisplayName,RetentionPolicy -Auto
```

```powershell
Get-Mailbox -ResultSize unlimited | Where-Object {$_.InPlaceHolds -ne $null} | FT DisplayName,RetentionPolicy -Auto
```

## <a name="optional-step-4-run-the-managed-folder-assistant-to-apply-the-new-retention-settings"></a>(İsteğe bağlı) 4. Adım: Yeni bekletme ayarlarını uygulamak için Yönetilen Klasör Yardımcısı'nı çalıştırın

Yeni Exchange bekletme ilkesini beklemedeki posta kutularına uyguladıktan sonra, Yönetilen Klasör Yardımcısı'nın yeni bekletme ilkesindeki ayarları kullanarak bu posta kutularını işlemesi Exchange Online 7 gün kadar sürebilir. Yönetilen Klasör Yardımcısı'nın çalışmasını beklemek yerine **Start-ManagedFolderAssistant** cmdlet'ini kullanarak yardımcının yeni bekletme ilkesini uyguladığınız posta kutularını işlemesini el ile tetikleyebilirsiniz.

Pilar Pinilla'nın posta kutusu için Yönetilen Klasör Yardımcısı'nı başlatmak için aşağıdaki komutu çalıştırın.

```powershell
Start-ManagedFolderAssistant "Pilar Pinilla"
```

Beklemedeki tüm posta kutuları için Yönetilen Klasör Yardımcısı'nı başlatmak için aşağıdaki komutları çalıştırın.

```powershell
$MailboxesOnHold = Get-Mailbox -ResultSize unlimited | Where-Object {($_.InPlaceHolds -ne $null) -or ($_.LitigationHoldEnabled -eq "True")}
```

```powershell
$MailboxesOnHold.DistinguishedName | Start-ManagedFolderAssistant
```

## <a name="more-information"></a>Daha fazla bilgi

- Kullanıcının arşiv posta kutusunu etkinleştirdikten sonra, kullanıcıya posta kutularındaki diğer öğelerin (yalnızca Kurtarılabilir Öğeler klasöründeki öğeler değil) arşiv posta kutusuna taşınabileceğini söylemeyi göz önünde bulundurun. Bunun nedeni, Exchange Online posta kutularına atanan Varsayılan MRM İlkesi'nin öğeleri posta kutusuna teslim edildikten veya kullanıcı tarafından oluşturulduktan iki yıl sonra arşiv posta kutusuna taşıyan bir bekletme etiketi (Varsayılan 2 yıl arşive taşıma olarak adlandırılır) içermesidir. Daha fazla bilgi için bkz. [Exchange Online'de Varsayılan Bekletme İlkesi](/exchange/security-and-compliance/messaging-records-management/default-retention-policy)

- Kullanıcının arşiv posta kutusunu etkinleştirdikten sonra, kullanıcıya arşiv posta kutusunun Kurtarılabilir Öğeler klasöründeki silinmiş öğeleri kurtarabileceğini de söyleyebilirsiniz. Bunu Outlook arşiv posta kutusunda **Silinmiş Öğeler** klasörünü seçip **Giriş** sekmesinde **Silinmiş Öğeleri Sunucudan Kurtar'a** tıklayarak gerçekleştirebilirler. Silinen öğeleri kurtarma hakkında daha fazla bilgi için bkz. [Windows için Outlook'da silinen öğeleri kurtarma](https://go.microsoft.com/fwlink/p/?LinkId=624829).
