---
title: Dış kişileri toplu olarak içeri Exchange Online
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
description: Yöneticilerin dış kişileri genel Exchange Online listesine toplu olarak içeri aktarması için PowerShell ve CSV dosyasını nasıl kullanabileceğini öğrenin.
ms.openlocfilehash: fbb2d9bb93d9275e662872d945254d6bf27deb92
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018830"
---
# <a name="bulk-import-external-contacts-to-exchange-online"></a>Dış kişileri toplu olarak içeri Exchange Online

**Bu makale yöneticilere aittir. Kişileri kendi posta kutunuza mı aktarmaya çalışıyorsunuz? Bkz [. Kişileri başka bir Outlook](https://support.office.com/article/bb796340-b58a-46c1-90c7-b549b8f3c5f8)**
   
Şirketinizin paylaşılan adres defterine (genel adres listesi de denir) eklemek istediğiniz çok sayıda mevcut ilgili kişisi mi Exchange Online? Aynı şirketi içindeki kullanıcılarla olduğu gibi dış kişileri de dağıtım grubu üyeleri olarak eklemek istiyor musunuz? Öyleyse, dış kişileri Exchange Online içeri toplu olarak içeri aktar almak için Exchange Online PowerShell ve CSV (virgülle ayrılmış değer) Exchange Online. Bu üç adımlı bir işlemdir:
  
[1. Adım: Dış kişiler hakkında bilgi içeren bir CSV dosyası oluşturma](#step-1-create-a-csv-file-that-contains-information-about-the-external-contacts)

[2. Adım: PowerShell ile dış kişileri oluşturma](#step-2-create-the-external-contacts-with-powershell) 

[3. Adım: Dış kişilerin özelliklerine bilgi ekleme](#step-3-add-information-to-the-properties-of-the-external-contacts)

Kişileri içeri aktarma işleminin bu adımlarını tamamlandıktan sonra, şu ek görevleri gerçekleştirebilirsiniz:
  
- [Daha fazla dış kişi ekleme](#add-more-external-contacts)
  
- [Paylaşılan adres defterine dış kişileri gizleme](#hide-external-contacts-from-the-shared-address-book)
  
## <a name="step-1-create-a-csv-file-that-contains-information-about-the-external-contacts"></a>1. Adım: Dış kişiler hakkında bilgi içeren bir CSV dosyası oluşturma

İlk adım, bu dosyaya içeri aktarma işlemi yapmak istediğiniz her dış kişi hakkında bilgi içeren bir CSV Exchange Online. 
  
1. Not Defteri'te aşağıdaki metni bir metin dosyasına kopyalayın ve not defterinizin dosya adı son ekini kullanarak masaüstünüze CSV dosyası olarak .csv; örneğin, ExternalContacts.csv.
    
    > [!TIP]
    > Diliniz özel karakterler ( **å**, **ä** ve **ö** gibi İsveççe) içeriyorsa, dosyayı Not Defteri'ne kaydetmek için CSV dosyasını UTF-8 veya başka bir Unicode kodlamayla kaydedin. 
  
    ```text
    ExternalEmailAddress,Name,FirstName,LastName,StreetAddress,City,StateorProvince,PostalCode,Phone,MobilePhone,Pager,HomePhone,Company,Title,OtherTelephone,Department,CountryOrRegion,Fax,Initials,Notes,Office,Manager
    danp@fabrikam.com,Dan Park,Dan,Park,1234 23rd Ave,Golden,CO,80215,206-111-1234,303-900-1234,555-1212,123-456-7890,Fabrikam,Shipping clerk,555-5555,Shipping,US,123-4567,R.,Good worker,31/1663,Dan Park
    pilar@contoso.com,Pilar Pinilla,Pilar,Pinilla,1234 Main St.,Seattle,WA,98017,206-555-0100,206-555-0101,206-555-0102,206-555-1234,Contoso,HR Manager,206-555-0104,Executive,US,206-555-0105,P.,Technical decision maker,31/1000,Dan Park
    ```

    CSV dosyasının ilk satırı veya üst bilgi satırı, kişileri içeri aktararak kişi listesinden içeri aktararak Exchange Online. Her özellik adı virgülle ayrılmıştır. Üst bilgi satırın altındaki her satır, tek bir dış kişinin içeri aktarma özelliği değerlerini temsil eder. 
    
    > [!NOTE]
    > Bu metin örnek veriler içerir ve bu verileri silebilirsiniz. Ama ilk satırı (üst bilgi satırı) silme veya değiştirme. Dış kişilerin tüm özelliklerini içerir. 
  
2. CSV dosyasını düzenlemek Microsoft Excel için csv dosyasını başka bir dosyada açın, çünkü CSV dosyasını düzenlemek Excel çok daha kolaydır.
    
3. Kişi bilgilerine içeri aktarmayı istediğiniz her kişi için bir Exchange Online. Mümkün olduğunca çok hücreyi doldurmak. Bu bilgiler, kişilerin her biri için paylaşılan adres kitabında görüntülenir. 
    
    > [!IMPORTANT]
    >  Aşağıdaki özellikler (üst bilgi satırındaki ilk dört öğedir) dış kişi oluşturmak için gereklidir ve CSV dosyasında doldurulması gerekir: **ExternalEmailAddress**, **Name**, **FirstName**, **LastName**. 2. Adımda çalıştırabilirsiniz PowerShell komutu, kişileri oluşturmak için bu özelliklerin değerlerini kullanır. 

## <a name="step-2-create-the-external-contacts-with-powershell"></a>2. Adım: PowerShell ile dış kişileri oluşturma

Sonraki adım, 1. Adımda oluşturduğunuz CSV dosyasını ve PowerShell'i kullanarak, CSV dosyasında listelenen dış kişileri toplu olarak içeri aktarmayı Exchange Online. 
  
1.  Bağlan PowerShell'i Exchange Online için. Adım adım yönergeler için bkz. [PowerShell'Bağlan Exchange Online kullanma](/powershell/exchange/connect-to-exchange-online-powershell). Exchange Online PowerShell'e bağlanarak genel yönetici hesabının kullanıcı adını ve parolasını kullanmaya Exchange Online. 
    
2. PowerShell'i Exchange Online'e bağdikten sonra, 1. Adımda CSV dosyasını kaydeden masaüstü klasörüne gidin; örneğin`C:\Users\Administrator\desktop`.
    
3. Dış kişileri oluşturmak için aşağıdaki komutu çalıştırın:

    ```powershell
    Import-Csv .\ExternalContacts.csv|%{New-MailContact -Name $_.Name -DisplayName $_.Name -ExternalEmailAddress $_.ExternalEmailAddress -FirstName $_.FirstName -LastName $_.LastName}
    ```

    İçeri aktarıyor olabileceğiniz kişilerin birçoğuna bağlı olarak, yeni kişileri oluşturmak biraz zaman alabilirsiniz. Komutun çalıştırması bittiğinde, PowerShell oluşturulan yeni kişilerin listesini görüntüler. 
    
4. Yeni dış kişileri görüntülemek için, Exchange Yönetim Merkezi'ne (EAC) gidin ve Alıcılar **Kişileri'ne** \> <a href="https://go.microsoft.com/fwlink/?linkid=2182970" target="_blank">**tıklayın**</a>. 
    
    > [!TIP]
    > EAC'ye bağlanma yönergeleri için bkz[. Exchange Yönetim Merkezi'Exchange Online](/exchange/exchange-admin-center). 
  
5. Gerekirse, listeyi **güncelleştirmek ve** aktarılan dış kişileri görmek için Yenile'yi tıklatın. 
    
    Alınan kişiler, aynı adres defteri içinde paylaşılan adres Outlook Web üzerinde Outlook.
    
    > [!NOTE]
    > Ayrıca, Kullanıcılar Kişiler'e Microsoft 365 yönetim merkezi kişiler'e de **bakabilirsiniz**\>. 

## <a name="step-3-add-information-to-the-properties-of-the-external-contacts"></a>3. Adım: Dış kişilerin özelliklerine bilgi ekleme

2. Adımda komutu çalıştırdikten sonra dış kişiler oluşturulur, ancak bunlar CSV dosyasındaki hücrelerin çoğunda yer alan kişi veya kuruluş bilgilerinden herhangi birini içermez. Bunun nedeni, yeni dış kişiler  oluşturma sırasında yalnızca gerekli özelliklerin doldurulmasıdır. CSV dosyasında bilgilerin hepsi doldurulmadı ise merak etmeyin. Orada yoksa eklenmez.
  
1.  Bağlan PowerShell'i Exchange Online için. Adım adım yönergeler için bkz. [PowerShell'Bağlan Exchange Online kullanma](/powershell/exchange/connect-to-exchange-online-powershell).
    
2. 1. Adımda CSV dosyasını kaydeden masaüstü klasörüne gidin; örneğin, `C:\Users\Administrator\desktop`.
    
3. CSV dosyasındaki diğer özellikleri 2. Adımda oluşturduğunuz dış kişiler'e eklemek için aşağıdaki iki komutu çalıştırın.
    
    ```powershell
    $Contacts = Import-CSV .\ExternalContacts.csv
  
    ```

    ```powershell
    $contacts | ForEach {Set-Contact $_.Name -StreetAddress $_.StreetAddress -City $_.City -StateorProvince $_.StateorProvince -PostalCode $_.PostalCode -Phone $_.Phone -MobilePhone $_.MobilePhone -Pager $_.Pager -HomePhone $_.HomePhone -Company $_.Company -Title $_.Title -OtherTelephone $_.OtherTelephone -Department $_.Department -Fax $_.Fax -Initials $_.Initials -Notes  $_.Notes -Office $_.Office -Manager $_.Manager}
    ```

    > [!NOTE]
    > _Manager parametresi_ sorun yaratabilir. CSV dosyasında hücre boşsa, hata alırsınız ve özellik bilgilerinde bu kişi eklenmez. Yönetici belirtmenize gerek yoksa, önceki PowerShell komutundan  ` -Manager $_.Manager ` silmeniz gerekir. 
  
    Bir kez daha, 1. Adımda aktarılan kişilerinin boyutuna bağlı olarak kişileri güncelleştirmek biraz zaman alsa da, bu işlem biraz zaman alsa da, bu işlem 1. 
    
4. Özelliklerin kişiler'e ekli olduğunu doğrulamak için: 
    
1. Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">yönetim merkezinde</a> Alıcılar **Kişileri'ne** \> **gidin**.
    
2. Bir kişinin üzerine tıklayın ve sonra da Düzenle **simgesine** ![tıklayın.](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) kişi özelliklerini görüntülemek için. 
    
Hepsi bu kadar! Kullanıcılar kişileri ve ek bilgileri adres defteri ve adres defteri bilgileri Outlook Web üzerinde Outlook.
  
## <a name="add-more-external-contacts"></a>Daha fazla dış kişi ekleme

Aynı adrese yeni dış kişiler eklemek için 1 ile 3. adımı Exchange Online. Siz veya şirketinizi kullananlar yeni kişi için CSV dosyasına yeni bir satır  eklersiniz. Ardından, 2. Adımdan ve 3. Adım'dan PowerShell komutlarını çalıştırarak yeni kişiler için bilgi oluşturabilir ve bu bilgilere bilgi ebilirsiniz.
  
> [!NOTE]
> Yeni kişiler oluşturma komutunu çalıştırarak, daha önce oluşturulan kişilerin zaten var olduğunu söyleyen bir hata alabilirsiniz. Ancak, CSV dosyasına eklenen tüm yeni kişi oluşturulur. 
  
## <a name="hide-external-contacts-from-the-shared-address-book"></a>Dış kişileri paylaşılan adres defteri kişilerinden>

Bazı şirketler yalnızca dış kişileri kullanıyor olabilir, dolayısıyla bunlar dağıtım grubu üyeleri olarak eklenebilir. Bu senaryoda, dış kişileri paylaşılan adres defterine gizlemek ister. Bunu şu şekilde yapabilirsiniz:
  
1.  Bağlan PowerShell'i Exchange Online için. Adım adım yönergeler için bkz. [PowerShell'Bağlan Exchange Online kullanma](/powershell/exchange/connect-to-exchange-online-powershell).
    
2. Tek bir dış kişiyi gizlemek için aşağıdaki komutu çalıştırın.
    
    ```powershell
    Set-MailContact <external contact> -HiddenFromAddressListsEnabled $true 
    ```

    Örneğin, Pilar Pinilla'yı paylaşılan adres defterine gizlemek için şu komutu çalıştırın:

    ```powershell
    Set-MailContact "Pilar Pinilla" -HiddenFromAddressListsEnabled $true
    ```

3. Paylaşılan adres defterine tüm dış kişileri gizlemek için şu komutu çalıştırın:

    ```powershell
    Get-Contact -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'MailContact')} | Set-MailContact -HiddenFromAddressListsEnabled $true  
    ```

Dış kişileri gizledikten sonra, paylaşılan adres defteri içinde görüntülenmezler, ancak yine de bunları dağıtım grubunun üyeleri olarak  eklemeniz gerekir.