---
title: Microsoft 365 Uyumluluğu için arşiv posta kutularını etkinleştirme
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.ArchivingHelp
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 268a109e-7843-405b-bb3d-b9393b2342ce
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
- admindeeplinkEXCHANGE
description: Kuruluşunuzun ileti saklama, eKeşif ve saklama gereksinimlerini desteklemek için arşiv posta kutularını etkinleştirmeyi veya devre dışı bırakmayı öğrenin.
ms.openlocfilehash: 9e30178dcab731ae61a9db5374218a608e4e47af
ms.sourcegitcommit: 46e796c6b76a01516c48977335bbf5076ca74a06
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2022
ms.locfileid: "64738391"
---
# <a name="enable-archive-mailboxes-in-the-compliance-center"></a>Uyumluluk merkezinde posta kutularını arşivlemeyi etkinleştirme

Microsoft 365’te arşivleme ( *Yerinde Arşivleme* olarak da adlandırılır) kullanıcılara ek posta kutusu depolama alanı sağlar. Daha fazla bilgi için bkz. [Arşiv posta kutuları hakkında bilgi](archive-mailboxes.md).

Microsoft 365 uyumluluk merkezinde bir arşiv posta kutusunu etkinleştirmek veya devre dışı bırakmak için bu makaledeki bilgileri veya PowerShell’i kullanın. Ayrıca, herhangi bir sorunu ve önerilen çözümü belirlemek için bir kullanıcının arşiv posta kutusunda otomatik tanılama denetiminin nasıl çalıştırıldığını da öğrenin.

## <a name="get-the-necessary-permissions"></a>Gerekli izinleri alma

Arşiv posta kutularını etkinleştirmek veya devre dışı bırakmak için Exchange Online'da Posta Alıcıları rolüne atanmış olmanız gerekir. Varsayılan olarak bu rol, <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezi</a>’nde **İzinler** sayfasındaki Alıcı Yönetimi ve Kuruluş Yönetimi rol gruplarına atanır. 

Microsoft 365 uyumluluk merkezinde **Arşiv** sayfasını görmüyorsanız, yöneticinizden size gerekli izinleri atamasını isteyin.

## <a name="enable-an-archive-mailbox"></a>Arşiv posta kutusu etkinleştirme

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a>’ne gidin ve oturum açın.

2. Microsoft 365 uyumluluk merkezinin sol bölmesinde, **Bilgi yönetişimi**’ne ve ardından **Arşiv** sekmesine tıklayın.

   **Arşiv** sayfası görüntülenir. **Arşiv posta kutusu** sütunu, her kullanıcı için bir arşiv posta kutusunun etkinleştirilmiş olup olmadığını gösterir.

   > [!NOTE]
   > **Arşiv** sayfası en fazla 500 kullanıcı gösterir.

3. Posta kutuları listesinde, arşiv posta kutusunu etkinleştirmek istediğiniz kullanıcıyı seçin ve **Arşivi Etkinleştir**'i seçin.

   ![Arşiv posta kutusunu etkinleştirmek için seçili kullanıcının ayrıntılar bölmesinde Etkinleştir'e tıklayın.](../media/8b53cdec-d5c9-4c28-af11-611f95c37b34.png)


   Arşiv posta kutusunu etkinleştirirseniz, kullanıcının posta kutusundaki posta kutusuna atanan arşivleme ilkesinden daha eski olan öğelerin yeni arşiv posta kutusuna taşınacağını söyleyen bir uyarı görüntülenir. Exchange Online posta kutularına atanan bekletme ilkesinin bir parçası olan varsayılan arşiv ilkesi, öğeleri, öğenin posta kutusuna teslim edildiği veya kullanıcı tarafından oluşturulduğu tarihten iki yıl sonra arşiv posta kutusuna taşır. Daha fazla bilgi için bu makalenin **Daha fazla bilgi** bölümüne bakın.

5. Arşiv posta kutusunu etkinleştirmek için **Etkinleştir**'i seçin.

   Arşiv posta kutusunu oluşturmak birkaç dakika sürebilir. Oluşturulduğunda, seçili kullanıcı için ayrıntılar bölmesinde **Arşiv posta kutusu: etkin** olarak görüntülenir. **Yenile** ![Yenile simgesine](../media/O365-MDM-Policy-RefreshIcon.gif) tıklamanız gerekebilir. ayrıntılar bölmesindeki bilgileri güncelleştirmek için.

> [!TIP]
> Arşiv posta kutuları devre dışı bırakılmış birden çok kullanıcı seçerek de arşiv posta kutularını toplu olarak etkinleştirebilirsiniz (Shift veya Ctrl tuşlarını kullanın). Birden çok posta kutusu seçtikten sonra, ayrıntılar bölmesinde **Etkinleştir**'e tıklayın.

## <a name="disable-an-archive-mailbox"></a>Arşiv posta kutusunu devre dışı bırakma

Bir kullanıcının arşiv posta kutusunu devre dışı bırakmak için de Microsoft 365 uyumluluk merkezi **Arşiv** sayfasını kullanabilirsiniz. Bir arşiv posta kutusunu devre dışı bıraktıktan sonra, devre dışı bırakmadan sonraki 30 gün içinde onu kullanıcının birincil posta kutusuna yeniden bağlayabilirsiniz. Bu durumda, arşiv posta kutusunun özgün içeriği geri yüklenir. 30 gün sonra, özgün arşiv posta kutusunun içeriği kalıcı olarak silinir ve kurtarılamaz. Bu nedenle, arşivi devre dışı bıraktıktan 30 gün sonra yeniden etkinleştirirseniz yeni bir arşiv posta kutusu oluşturulur.

Kullanıcıların posta kutularına atanan varsayılan arşiv ilkesi, öğelerin teslim edildikten iki yıl sonra arşiv posta kutusuna taşımasını sağlar. Bir kullanıcının arşiv posta kutusunu devre dışı bırakırsanız, posta kutusu öğeleri üzerinde herhangi bir işlem yapılmaz ve bunlar kullanıcının birincil posta kutusunda kalır.

Arşiv posta kutusunu devre dışı bırakmak için:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a>’ne gidin ve oturum açın.

2. Microsoft 365 uyumluluk merkezinin sol bölmesinde, **Bilgi yönetişimi**’ne ve ardından **Arşiv** sekmesine tıklayın.

   **Arşiv** sayfası görüntülenir. **Arşiv posta kutusu** sütunu, her kullanıcı için bir arşiv posta kutusunun etkinleştirilmiş olup olmadığını gösterir.

   > [!NOTE]
   > **Arşiv** sayfası en fazla 500 kullanıcı gösterir.

3. Posta kutuları listesinde, arşiv posta kutusunu devre dışı bırakmak istediğiniz kullanıcıyı seçin ve **Arşivi Devre Dışı Bırak**'ı seçin.


   Arşiv posta kutusunu yeniden etkinleştirmek için 30 gününüz olduğunu ve 30 gün sonra arşivdeki tüm bilgilerin kalıcı olarak silineceğini söyleyen bir uyarı iletisi görüntülenir.

5. Arşiv posta kutusunu devre dışı bırakmak için **Devre Dışı Bırak**'ı seçin.

   Arşiv posta kutusunu devre dışı bırakmak birkaç dakika sürebilir. Devre dışı bırakıldığında, seçili kullanıcı için ayrıntılar bölmesinde **Arşiv posta kutusu: devre dışı** olarak görüntülenir. **Yenile** ![Yenile simgesine](../media/O365-MDM-Policy-RefreshIcon.gif) tıklamanız gerekebilir. ayrıntılar bölmesindeki bilgileri güncelleştirmek için.

> [!TIP]
> Arşiv posta kutuları etkinleştirilmiş birden çok kullanıcı seçerek de arşiv posta kutularını toplu olarak devre dışı bırakabilirsiniz (Shift veya Ctrl tuşlarını kullanın). Birden çok posta kutusu seçtikten sonra, ayrıntılar bölmesinde **Devre dışı bırak**'a tıklayın.

## <a name="use-exchange-online-powershell-to-enable-or-disable-archive-mailboxes"></a>Arşiv posta kutularını etkinleştirmek veya devre dışı bırakmak için Exchange Online PowerShell'i kullanın

Arşiv posta kutularını etkinleştirmek için Exchange Online PowerShell'i kullanabilirsiniz. PowerShell'i kullanmanın birincil nedeni, arşiv posta kutusunu kuruluşunuzdaki tüm kullanıcılar için hızlı bir şekilde etkinleştirebilmenizdir.

İlk adım, Exchange Online PowerShell'e bağlanmaktır. Yönergeler için bkz. [Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

Exchange Online'a bağlandıktan sonra, arşiv posta kutularını etkinleştirmek veya devre dışı bırakmak için aşağıdaki bölümlerdeki komutları çalıştırabilirsiniz.

### <a name="enable-archive-mailboxes"></a>Arşiv posta kutularını etkinleştirme

Tek bir kullanıcı için arşiv posta kutusunu etkinleştirmek için aşağıdaki komutu çalıştırın.

```powershell
Enable-Mailbox -Identity <username> -Archive
```

Kuruluşunuzdaki (arşiv posta kutusu şu anda etkin olmayan) tüm kullanıcılar için arşiv posta kutusunu etkinleştirmek için aşağıdaki komutu çalıştırın.

```powershell
Get-Mailbox -Filter {ArchiveGuid -Eq "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Enable-Mailbox -Archive
```

### <a name="disable-archive-mailboxes"></a>Arşiv posta kutularını devre dışı bırakma

Tek bir kullanıcı için arşiv posta kutusunu devre dışı bırakmak için aşağıdaki komutu çalıştırın.

```powershell
Disable-Mailbox -Identity <username> -Archive
```

Kuruluşunuzdaki (arşiv posta kutusu şu anda etkin olan) tüm kullanıcılar için arşiv posta kutusunu devre dışı bırakmak için aşağıdaki komutu çalıştırın.

```powershell
Get-Mailbox -Filter {ArchiveGuid -Ne "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Disable-Mailbox -Archive
```

## <a name="run-diagnostics-on-archive-mailboxes"></a>Arşiv posta kutularda tanılamayı çalıştırma

Herhangi bir sorunu ve önerilen çözümleri belirlemek için bir kullanıcının arşiv posta kutusunda otomatik tanılama denetimi çalıştırabilirsiniz.

Tanılama denetimi çalıştırmak için aşağıdaki düğmeye tıklayın. 

> [!div class="nextstepaction"]
> [Testleri Çalıştırma: Arşiv Posta Kutusu](https://aka.ms/PillarArchiveMailbox)

![Bir arşiv posta kutusunda tanılamayı çalıştırın.](../media/ArchiveMailboxDiagnostics.png)

Microsoft 365 yönetim merkezinde bir açılır sayfa açılır. Denetlemek istediğiniz posta kutusunun e-posta adresini girin ve **Testleri Çalıştır**'a tıklayın.

> [!NOTE]
> Arşiv posta kutusu tanılama denetimini kullanmak için bir Microsoft 365 genel yöneticisi olmanız gerekir. Ayrıca, bu özellik Microsoft 365 Kamu bulutlarında, 21Vianet tarafından yürütülen Microsoft 365'te veya Microsoft 365 Almanya'da kullanılamaz.

## <a name="next-steps"></a>Sonraki adımlar

Ek depolama alanı için [otomatik olarak genişleyen arşivleme](autoexpanding-archiving.md)’yi etkinleştirmeyi göz önünde bulundurun. Yönergeler için bkz. [Otomatik genişleyen arşivlemeyi etkinleştirme](enable-autoexpanding-archiving.md).
