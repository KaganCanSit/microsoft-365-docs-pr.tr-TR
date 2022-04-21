---
title: Dış kişileri Exchange Online toplu içeri aktarma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
audience: End User
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOP150
ms.assetid: bed936bc-0969-4a6d-a7a5-66305c14e958
ms.custom: admindeeplinkEXCHANGE
description: Yöneticilerin dış kişileri genel adres listesine toplu olarak aktarmak için PowerShell ve CSV dosyasını Exchange Online nasıl kullanabileceğini öğrenin.
ms.openlocfilehash: a85d24a4b20798df057250d9114f97563a6a8e2d
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64999310"
---
# <a name="bulk-import-external-contacts-to-exchange-online"></a>Dış kişileri Exchange Online toplu içeri aktarma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**Bu makale yöneticilere yöneliktir. Kişileri kendi posta kutunuza aktarmaya mı çalışıyorsunuz? Bkz [. Kişileri Outlook içeri aktarma](https://support.office.com/article/bb796340-b58a-46c1-90c7-b549b8f3c5f8)**
   
Şirketinizin, Exchange Online paylaşılan adres defterine (genel adres listesi olarak da adlandırılır) dahil etmek istediğiniz çok sayıda mevcut ilgili kişisi var mı? Dış kişileri, şirketinizin içindeki kullanıcılarla yaptığınız gibi dağıtım gruplarının üyesi olarak eklemek istiyor musunuz? Bu durumda, dış kişileri Exchange Online toplu olarak içeri aktarmak için Exchange Online PowerShell ve CSV (virgülle ayrılmış değer) dosyası kullanabilirsiniz. Bu üç adımlı bir işlemdir:
  
[1. Adım: Dış kişiler hakkında bilgi içeren bir CSV dosyası oluşturma](#step-1-create-a-csv-file-that-contains-information-about-the-external-contacts)

[2. Adım: PowerShell ile dış kişileri oluşturma](#step-2-create-the-external-contacts-with-powershell) 

[3. Adım: Dış kişilerin özelliklerine bilgi ekleme](#step-3-add-information-to-the-properties-of-the-external-contacts)

Kişileri içeri aktarmak için bu adımları tamamladıktan sonra şu ek görevleri gerçekleştirebilirsiniz:
  
- [Daha fazla dış kişi ekleme](#add-more-external-contacts)
  
- [Paylaşılan adres defterinden dış kişileri gizleme](#hide-external-contacts-from-the-shared-address-book)
  
## <a name="step-1-create-a-csv-file-that-contains-information-about-the-external-contacts"></a>1. Adım: Dış kişiler hakkında bilgi içeren bir CSV dosyası oluşturma

İlk adım, Exchange Online içeri aktarmak istediğiniz her dış kişi hakkında bilgi içeren bir CSV dosyası oluşturmaktır. 
  
1. Aşağıdaki metni Not Defteri'ndeki bir metin dosyasına kopyalayın ve .csv dosya adı son ekini kullanarak masaüstünüzde CSV dosyası olarak kaydedin; örneğin, ExternalContacts.csv.
    
    > [!TIP]
    > Dilinizde özel karakterler (İsveççe dilinde **å**, **ä** ve **ö** gibi) varsa, dosyayı Not Defteri'ne kaydettiğinizde CSV dosyasını UTF-8 veya diğer Unicode kodlamasıyla kaydedin. 
  
    ```text
    ExternalEmailAddress,Name,FirstName,LastName,StreetAddress,City,StateorProvince,PostalCode,Phone,MobilePhone,Pager,HomePhone,Company,Title,OtherTelephone,Department,CountryOrRegion,Fax,Initials,Notes,Office,Manager
    danp@fabrikam.com,Dan Park,Dan,Park,1234 23rd Ave,Golden,CO,80215,206-111-1234,303-900-1234,555-1212,123-456-7890,Fabrikam,Shipping clerk,555-5555,Shipping,US,123-4567,R.,Good worker,31/1663,Dan Park
    pilar@contoso.com,Pilar Pinilla,Pilar,Pinilla,1234 Main St.,Seattle,WA,98017,206-555-0100,206-555-0101,206-555-0102,206-555-1234,Contoso,HR Manager,206-555-0104,Executive,US,206-555-0105,P.,Technical decision maker,31/1000,Dan Park
    ```

    CSV dosyasının ilk satırı veya üst bilgi satırı, kişileri Exchange Online içeri aktardığınızda kullanılabilecek özellikleri listeler. Her özellik adı virgülle ayrılır. Üst bilgi satırının altındaki her satır, tek bir dış kişiyi içeri aktarmaya yönelik özellik değerlerini temsil eder. 
    
    > [!NOTE]
    > Bu metin, silebileceğiniz örnek verileri içerir. Ancak ilk (üst bilgi) satırını silmeyin veya değiştirmeyin. Dış kişilerin tüm özelliklerini içerir. 
  
2. CSV dosyasını düzenlemek için Excel kullanmak çok daha kolay olduğundan CSV dosyasını düzenlemek için csv dosyasını Microsoft Excel açın.
    
3. Exchange Online aktarmak istediğiniz her kişi için bir satır oluşturun. Mümkün olduğunca çok hücreyi doldurun. Bu bilgiler her kişinin paylaşılan adres defterinde görüntülenir. 
    
    > [!IMPORTANT]
    >  Dış kişi oluşturmak için aşağıdaki özellikler (üst bilgi satırındaki ilk dört öğedir) gereklidir ve CSV dosyasında doldurulmalıdır: **ExternalEmailAddress**, **Name**, **Name, LastName**.  2. Adımda çalıştırdığınız PowerShell komutu, kişileri oluşturmak için bu özelliklerin değerlerini kullanır. 

## <a name="step-2-create-the-external-contacts-with-powershell"></a>2. Adım: PowerShell ile dış kişileri oluşturma

Sonraki adım, 1. Adım ve PowerShell'de oluşturduğunuz CSV dosyasını kullanarak CSV dosyasında listelenen dış kişileri toplu olarak Exchange Online. 
  
1.  PowerShell'i Exchange Online kuruluşunuza Bağlan. Adım adım yönergeler için bkz. [PowerShell'i Exchange Online için Bağlan](/powershell/exchange/connect-to-exchange-online-powershell). Exchange Online PowerShell'e bağlanırken genel yönetici hesabınızın kullanıcı adını ve parolasını kullandığınızdan emin olun. 
    
2. PowerShell'i Exchange Online bağladıktan sonra, CSV dosyasını 1. Adımda kaydettiğiniz masaüstü klasörüne gidin; örneğin`C:\Users\Administrator\desktop`.
    
3. Dış kişileri oluşturmak için aşağıdaki komutu çalıştırın:

    ```powershell
    Import-Csv .\ExternalContacts.csv|%{New-MailContact -Name $_.Name -DisplayName $_.Name -ExternalEmailAddress $_.ExternalEmailAddress -FirstName $_.FirstName -LastName $_.LastName}
    ```

    İçeri aktardığınız kişilere bağlı olarak yeni kişilerin oluşturulması biraz zaman alabilir. Komutun çalışması tamamlandığında PowerShell, oluşturulan yeni kişilerin listesini görüntüler. 
    
4. Yeni dış kişileri görüntülemek için Exchange yönetim merkezine (EAC) gidin ve **Alıcılar** \> <a href="https://go.microsoft.com/fwlink/?linkid=2182970" target="_blank">**Kişileri'ne**</a> tıklayın. 
    
    > [!TIP]
    > EAC'ye bağlanma yönergeleri için bkz. [Exchange Online Exchange yönetim merkezi](/exchange/exchange-admin-center). 
  
5. Gerekirse, listeyi güncelleştirmek ve içeri aktarılan dış kişileri görmek için **Yenile'ye** tıklayın. 
    
    İçeri aktarılan kişiler Outlook ve Web üzerinde Outlook paylaşılan adres defterinde görünür.
    
    > [!NOTE]
    > **Ayrıca, Kullanıcılar** \> **Kişileri'ne** giderek Microsoft 365 yönetim merkezi kişileri de görüntüleyebilirsiniz. 

## <a name="step-3-add-information-to-the-properties-of-the-external-contacts"></a>3. Adım: Dış kişilerin özelliklerine bilgi ekleme

2. Adımda komutu çalıştırdıktan sonra dış kişiler oluşturulur, ancak bunlar CSV dosyasındaki hücrelerin çoğundan gelen bilgiler olan kişi veya kuruluş bilgilerini içermez. Bunun nedeni, yeni dış kişiler oluşturduğunuzda yalnızca gerekli özelliklerin doldurulacağıdır. CSV dosyasında tüm bilgileri doldurmadıysanız endişelenmeyin. Orada değilse, eklenmez.
  
1.  PowerShell'i Exchange Online kuruluşunuza Bağlan. Adım adım yönergeler için bkz. [PowerShell'i Exchange Online için Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).
    
2. 1. Adımda CSV dosyasını kaydettiğiniz masaüstü klasörüne gidin; örneğin, `C:\Users\Administrator\desktop`.
    
3. CSV dosyasındaki diğer özellikleri 2. Adımda oluşturduğunuz dış kişilere eklemek için aşağıdaki iki komutu çalıştırın.
    
    ```powershell
    $Contacts = Import-CSV .\ExternalContacts.csv
  
    ```

    ```powershell
    $contacts | ForEach {Set-Contact $_.Name -StreetAddress $_.StreetAddress -City $_.City -StateorProvince $_.StateorProvince -PostalCode $_.PostalCode -Phone $_.Phone -MobilePhone $_.MobilePhone -Pager $_.Pager -HomePhone $_.HomePhone -Company $_.Company -Title $_.Title -OtherTelephone $_.OtherTelephone -Department $_.Department -Fax $_.Fax -Initials $_.Initials -Notes  $_.Notes -Office $_.Office -Manager $_.Manager}
    ```

    > [!NOTE]
    > _Manager_ parametresi sorunlu olabilir. CSV dosyasında hücre boşsa bir hata alırsınız ve özellik bilgilerinin hiçbiri kişiye eklenmez. Yönetici belirtmeniz gerekmiyorsa önceki PowerShell komutundan silmeniz  ` -Manager $_.Manager ` yeterlidir. 
  
    1. Adımda içeri aktardığınız kişilere bağlı olarak kişilerin güncelleştirilmiş olması da biraz zaman alabilir. 
    
4. Özelliklerin kişilere eklendiğini doğrulamak için: 
    
1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezinde</a> **Alıcılar** \> **Kişileri'ne** gidin.
    
2. Bir kişiye tıklayın ve **düzenle Düzenle** simgesine tıklayın ![.](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) öğesini seçin. 
    
İşte bu kadar! Kullanıcılar kişileri ve ek bilgileri adres defteri Outlook ve Web üzerinde Outlook görebilir.
  
## <a name="add-more-external-contacts"></a>Daha fazla dış kişi ekleme

Exchange Online yeni dış kişiler eklemek için 1. Adımdan 3. Adıma kadar olan adımları yineleyebilirsiniz. Siz veya şirketinizdeki kullanıcılar, yeni kişi için CSV dosyasına yeni bir satır ekleyebilirsiniz. Ardından 2. Adım ve 3. Adım'dan PowerShell komutlarını çalıştırarak yeni kişilere bilgi oluşturabilir ve bu kişilere bilgi ekleyebilirsiniz.
  
> [!NOTE]
> Yeni kişiler oluşturmak için komutunu çalıştırdığınızda, daha önce oluşturulmuş kişilerin zaten var olduğunu belirten bir hata alabilirsiniz. Ancak CSV dosyasına eklenen tüm yeni kişiler oluşturulur. 
  
## <a name="hide-external-contacts-from-the-shared-address-book"></a>Paylaşılan adres defterinden dış kişileri gizleme>

Bazı şirketler, dağıtım gruplarının üyeleri olarak eklenebilmeleri için yalnızca dış kişileri kullanabilir. Bu senaryoda, dış kişileri paylaşılan adres defterinden gizlemek isteyebilirler. Bunu şu şekilde yapabilirsiniz:
  
1.  PowerShell'i Exchange Online kuruluşunuza Bağlan. Adım adım yönergeler için bkz. [PowerShell'i Exchange Online için Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).
    
2. Tek bir dış kişiyi gizlemek için aşağıdaki komutu çalıştırın.
    
    ```powershell
    Set-MailContact <external contact> -HiddenFromAddressListsEnabled $true 
    ```

    Örneğin, Pilar Pinilla'yı paylaşılan adres defterinden gizlemek için şu komutu çalıştırın:

    ```powershell
    Set-MailContact "Pilar Pinilla" -HiddenFromAddressListsEnabled $true
    ```

3. Paylaşılan adres defterinden tüm dış kişileri gizlemek için şu komutu çalıştırın:

    ```powershell
    Get-Contact -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'MailContact')} | Set-MailContact -HiddenFromAddressListsEnabled $true  
    ```

Bunları gizledikten sonra, dış kişiler paylaşılan adres defterinde görüntülenmez, ancak yine de bunları bir dağıtım grubunun üyesi olarak ekleyebilirsiniz.