---
title: Uyumluluk için arşiv posta kutularını Microsoft 365 etkinleştirme
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
description: Kuruluş ileti bekletme, eKbulma ve saklama gereksinimlerini desteklemek için arşiv posta kutularını etkinleştirmeyi veya devre dışı bırakmayı öğrenin.
ms.openlocfilehash: be7939f11c6aea0161f76c3796ca2ff8bd515ba0
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010837"
---
# <a name="enable-archive-mailboxes-in-the-compliance-center"></a>Uyumluluk merkezinde arşiv posta kutularını etkinleştirme

Yerinde Arşivleme Microsoft 365 *olarak da adlandırılan* bu arşivleme, kullanıcılara ek posta kutusu depolama alanı sağlar. Daha fazla bilgi için bkz[. Arşiv posta kutuları hakkında bilgi.](archive-mailboxes.md)

Dosya kutusunda veya PowerShell kullanarak arşiv posta kutusunu etkinleştirmek veya devre dışı bırakmak Microsoft 365 uyumluluk merkezi bu makaledeki bilgileri kullanın. Ayrıca, sorunları ve önerilen çözümlerini tanımlamak için kullanıcının arşiv posta kutusunda otomatik tanılama denetimi çalıştırmayı öğrenin.

## <a name="get-the-necessary-permissions"></a>Gerekli izinleri alın

Arşiv posta kutularını etkinleştirmek veya devre dışı bırakmak için, e-Exchange Online'de Posta Alıcıları rolüne atanmış olması gerekir. Varsayılan olarak bu rol, Yönetim Merkezi'nin İzinler sayfasındaki **Alıcı Yönetimi** <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">ve Kuruluş Exchange atanır</a>. 

Arşiv sayfasında Arşiv sayfasını **görmüyorsanız**, Microsoft 365 uyumluluk merkezi yöneticinizden size gerekli izinleri ataması gerekir.

## <a name="enable-an-archive-mailbox"></a>Arşiv posta kutusunu etkinleştirme

1. Oturum açma <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a> gidin.

2. Tablo yönetimi'nin sol Microsoft 365 uyumluluk merkezi, **Bilgi yönetimi'ne** ve sonra da Arşiv **sekmesine** tıklayın.

   **Arşiv sayfası** görüntülenir. Arşiv **posta kutusu sütunu** , bir arşiv posta kutusunun her kullanıcı için etkin olup olmadığını gösterir.

   > [!NOTE]
   > Arşiv **sayfasında** en çok 500 kullanıcı görüntülenir.

3. Posta kutuları listesinde, arşiv posta kutusunu etkinleştirmek istediğiniz kullanıcıyı seçin.

   ![Arşiv posta kutusunu etkinleştirmek için seçili kullanıcının ayrıntılar bölmesinde Etkinleştir'e tıklayın.](../media/8b53cdec-d5c9-4c28-af11-611f95c37b34.png)

4. Seçili kullanıcının ayrıntılar bölmesinde Etkinleştir'e **tıklayın**.

   Arşiv posta kutusunu etkinleştirirseniz, kullanıcının posta kutusunda posta kutusuna atanan arşivleme ilkesinden daha eski öğelerin yeni arşiv posta kutusuna taşınacaklarını söyleyen bir uyarı görüntülenir. Exchange Online posta kutularına atanan bekletme ilkesi kapsamındaki varsayılan arşiv ilkesi, öğenin posta kutusuna teslim veya kullanıcı tarafından oluşturulma tarihini iki yıl sonra arşiv posta kutusuna taşır. Daha fazla bilgi için, bu **makalenin Daha fazla** bilgi bölümüne bakın.

5. Arşiv **posta kutusunu** etkinleştirmek için Evet'e tıklayın.

   Arşiv posta kutusunun oluşturmak birkaç dakika zaman alabilirsiniz. Oluşturulduğunda, seçili kullanıcının ayrıntılar bölmesinde Arşiv posta kutusu **:** etkin görüntülenir. Yenile simgesine **tıklamak** ![zorundayabilirsiniz.](../media/O365-MDM-Policy-RefreshIcon.gif) seçin.

> [!TIP]
> Ayrıca, devre dışı bırakılmış arşiv posta kutuları olan birden çok kullanıcı seçerek (Shift veya Ctrl tuşlarını kullanarak) arşiv posta kutularını toplu olarak etkinleştirebilirsiniz. Birden çok posta kutusu seçdikten sonra, **ayrıntılar bölmesinde** Etkinleştir'e tıklayın.

## <a name="disable-an-archive-mailbox"></a>Arşiv posta kutusunu devre dışı bırakma

Kullanıcının arşiv posta kutusunu **devre dışı** bırakmak için Microsoft 365 uyumluluk merkezi Arşiv sayfasını da kullanabilirsiniz. Arşiv posta kutusunu devre dışı bırakdikten sonra, 30 gün içinde bu posta kutusunu devre dışı bırakarak kullanıcının birincil posta kutusuna yeniden bağlanabilirsiniz. Bu durumda, arşiv posta kutusunun özgün içeriği geri yüklenir. 30 gün sonra, özgün arşiv posta kutusunun içeriği kalıcı olarak silinir ve kurtarılamaz. Dolayısıyla, arşivi devre dışı bırak oluşturduktan sonra 30 gün içinde yeniden etkinleştirirsiniz, yeni bir arşiv posta kutusu oluşturulur.

Kullanıcıların posta kutularına atanan varsayılan arşiv ilkesi öğeleri, öğenin teslim edildikten iki yıl sonra arşiv posta kutusuna taşır. Kullanıcının arşiv posta kutusunu devre dışı bıraksanız, posta kutusu öğeleri üzerinde hiçbir işlem olmaz ve bunlar kullanıcının birincil posta kutusunda kalır.

Arşiv posta kutusunu devre dışı bırakmak için:

1. Oturum açma <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a> gidin.

2. Tablo yönetimi'nin sol Microsoft 365 uyumluluk merkezi, **Bilgi yönetimi'ne** ve sonra da Arşiv **sekmesine** tıklayın.

   **Arşiv sayfası** görüntülenir. Arşiv **posta kutusu sütunu** , bir arşiv posta kutusunun her kullanıcı için etkin olup olmadığını gösterir.

   > [!NOTE]
   > Arşiv **sayfasında** en çok 500 kullanıcı görüntülenir.

3. Posta kutuları listesinde, arşiv posta kutusunu devre dışı bırakmak istediğiniz kullanıcıyı seçin.

4. Ayrıntılar bölmesinde Devre dışı bırak'a **tıklayın**.

   Arşiv posta kutusunu yeniden etkinleştirmek için 30 gün süreniz olacağını ve 30 gün sonra arşivle ilgili tüm bilgilerin kalıcı olarak silineceklerini söyleyen bir uyarı iletisi görüntülenir.

5. Arşiv **posta kutusunu** devre dışı bırakmak için Evet'e tıklayın.

   Arşiv posta kutusunun devre dışı bırakması birkaç dakika zaman alır. Devre dışı bırakılabilir olduğunda, **seçili kullanıcının ayrıntılar** bölmesinde Arşiv posta kutusu: devre dışı olarak görüntülenir. Yenile simgesine **tıklamak** ![zorundayabilirsiniz.](../media/O365-MDM-Policy-RefreshIcon.gif) seçin.

> [!TIP]
> Etkinleştirilmiş arşiv posta kutuları olan birden çok kullanıcı seçerek arşiv posta kutularını toplu olarak devre dışı abilirsiniz (Shift veya Ctrl tuşlarını kullanın). Birden çok posta kutusu seçdikten sonra, ayrıntılar **bölmesinde Devre** Dışı Bırak'a tıklayın.

## <a name="use-exchange-online-powershell-to-enable-or-disable-archive-mailboxes"></a>Arşiv posta Exchange Online etkinleştirmek veya devre dışı bırakmak için PowerShell'i kullanma

Arşiv posta kutularını etkinleştirmek Exchange Online PowerShell'i de kullanabilirsiniz. PowerShell'i kullanmanın birincil nedeni, arşiv posta kutusunu kurumdaki tüm kullanıcılar için hızlı bir şekilde etkinleştirebilirsiniz.

İlk adım, Exchange Online PowerShell'e bağlanmaktir. Yönergeler için bkz. [Bağlan PowerShell'Exchange Online yükleme](/powershell/exchange/connect-to-exchange-online-powershell).

Exchange Online'a bağlandıktan sonra, arşiv posta kutularını etkinleştirmek veya devre dışı bırakmak için aşağıdaki bölümlerdeki komutları çalıştırabilirsiniz.

### <a name="enable-archive-mailboxes"></a>Arşiv posta kutularını etkinleştirme

Tek bir kullanıcı için arşiv posta kutusunu etkinleştirmek için aşağıdaki komutu çalıştırın.

```powershell
Enable-Mailbox -Identity <username> -Archive
```

Aşağıdaki komutu çalıştırarak, arşiv posta kutusunu tüm kullanıcıları (arşiv posta kutusu şu anda etkin olmayan kullanıcılar için) etkinleştirin.

```powershell
Get-Mailbox -Filter {ArchiveGuid -Eq "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Enable-Mailbox -Archive
```

### <a name="disable-archive-mailboxes"></a>Arşiv posta kutularını devre dışı bırakma

Tek bir kullanıcının arşiv posta kutusunu devre dışı bırakmak için aşağıdaki komutu çalıştırın.

```powershell
Disable-Mailbox -Identity <username> -Archive
```

Aşağıdaki komutu çalıştırarak, arşiv posta kutusunu, tüm kullanıcıları (arşiv posta kutusu şu anda etkinleştirilmiş olan kullanıcılar için) devre dışı bırakabilirsiniz.

```powershell
Get-Mailbox -Filter {ArchiveGuid -Ne "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Disable-Mailbox -Archive
```

## <a name="run-diagnostics-on-archive-mailboxes"></a>Arşiv posta kutularda tanılamayı çalıştırma

Sorunları ve önerilen çözümlerini belirlemek için kullanıcının arşiv posta kutusunda otomatik bir tanılama denetimi çalıştırabilirsiniz.

Tanılama denetimi çalıştırmak için aşağıdaki düğmeye tıklayın. 

> [!div class="nextstepaction"]
> [Sınamaları Çalıştırma: Arşiv Posta Kutusu](https://aka.ms/PillarArchiveMailbox)

![Bir arşiv posta kutusunda tanılamayı çalıştırın.](../media/ArchiveMailboxDiagnostics.png)

Açılır sayfada bir açılır Microsoft 365 yönetim merkezi. Kontrol etmek istediğiniz posta kutusunun e-posta adresini girin ve Testleri **Çalıştır'a tıklayın**.

> [!NOTE]
> Arşiv posta kutusu tanılama Microsoft 365 için genel yönetici siz olun. Ayrıca bu özellik 21Vianet tarafından Microsoft 365 kamu bulutlarında, Microsoft 365 Veya Almanya'da Microsoft 365 kullanılamaz.

## <a name="next-steps"></a>Sonraki adımlar

Ek depolama alanı [için otomatik genişleyen arşivlemeyi](autoexpanding-archiving.md) etkinleştirmeyi göz önünde bulundurabilirsiniz. Yönergeler için bkz [. Otomatik genişleyen arşivlemeyi etkinleştirme](enable-autoexpanding-archiving.md).
