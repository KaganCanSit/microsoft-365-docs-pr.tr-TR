---
title: Paylaşılan posta kutusu oluşturma
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkEXCHANGE
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 871a246d-3acd-4bba-948e-5de8be0544c9
description: İşletmenizdeki birden çok kullanıcının tek bir adrese gönderilen e-postayı okuma ve yanıtlama sorumluluğunu paylaşmasını sağlamak için paylaşılan bir posta kutusu oluşturun.
ms.openlocfilehash: 444be08a2083bf184d61ee206dfaa8ab53657b0b
ms.sourcegitcommit: 5fe7f2954a89406245416fc1a218cf4bf19abb85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65864572"
---
# <a name="create-a-shared-mailbox"></a>Paylaşılan posta kutusu oluşturma 

> [!NOTE]
> Kuruluşunuz karma bir Exchange ortamı kullanıyorsa, paylaşılan posta kutuları oluşturmak ve yönetmek için şirket içi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezini</a> kullanmanız gerekir. Bkz[. Exchange yönetim merkezinde paylaşılan posta kutuları oluşturma](/Exchange/collaboration/shared-mailboxes/create-shared-mailboxes?preserve-view=true.&view=exchserver-2019)
>
> Outlook için paylaşılan posta kutusu mu yoksa Microsoft 365 grubu mu oluşturmanız gerektiğine emin değilseniz, bazı yönergeler için bkz. [Grupları karşılaştırma](../create-groups/compare-groups.md). Şu anda paylaşılan bir posta kutusunu Microsoft 365 grubuna geçirmenin mümkün olmadığını unutmayın. Bu istediğiniz bir şeyse [, burada oy](https://go.microsoft.com/fwlink/?linkid=871518) vererek bize bildirin.

Bir grup kullanıcının, bilgi@contoso.com gibi ortak bir e-posta adresini izleyebildiği ve bu adresten e-posta gönderebildiği bir paylaşılan posta kutusu kolayca oluşturulabilir. Paylaşılan posta kutusuna gönderilen bir ileti gruptaki bir kullanıcı tarafından yanıtlandığında e-posta, kullanıcı tarafından değil, paylaşılan posta kutusu tarafından gönderilmiş olarak görüntülenir.

Paylaşılan posta kutuları paylaşılan takvim içerir. Küçük işletmelerin birçoğu, paylaşılan takvimi herkesin randevularını girebildiği ortak bir yer olarak kullanır. Örneğin, işletmenizde müşteri ziyaretleri yapan 3 kişi, randevularını girmek için paylaşılan takvimi kullanabilir. Böylece herkes, diğerlerinin nerede olduğundan haberdar olabilir.

Paylaşılan posta kutusu oluşturmadan önce daha fazla bilgi için [Paylaşılan posta kutuları hakkında'yı](about-shared-mailboxes.md) okuduğunuzdan emin olun.

> [!TIP]
> Bu konuda verilen adımlarla ilgili yardıma ihtiyacınız varsa[bir Microsoft küçük işletme uzmanıyla çalışmayı](https://go.microsoft.com/fwlink/?linkid=2186871) göz önünde bulundurun. İşletme Yardımı ile, işletmenizi büyütürken katılımdan gündelik kullanıma kadar her aşamada siz ve çalışanlarınız günün 24 saati küçük işletme uzmanlarına erişebilirsiniz.

## <a name="create-a-shared-mailbox-and-add-members"></a>Paylaşılan posta kutusu oluşturma ve üye ekleme
  
1. Genel yönetici hesabıyla veya Exchange yönetici hesabıyla oturum açın. "**Bu sayfaya erişme veya bu eylemi gerçekleştirme izniniz yok**" iletisini alırsanız yönetici değilsiniz demektir. 

::: moniker range="o365-worldwide"

2. Yönetim merkezinde **, Teams & Grupları** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Paylaşılan posta kutuları</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

2. [Yönetim merkezinde](https://go.microsoft.com/fwlink/p/?linkid=850627)**, Teams & Grupları** \> **Paylaşılan posta kutuları** sayfasına gidin.

::: moniker-end
    
3. **Paylaşılan posta kutuları** sayfasında **+ Paylaşılan posta kutusu ekle'yi** seçin. Paylaşılan posta kutusu için bir ad girin. Bu, e-posta adresini seçer, ancak gerekirse düzenleyebilirsiniz.
    
    ![Name your shared mailbox.](../../media/e3035132-8986-4ec7-b7c0-f2752080d2c0.png)
  
4. **Değişiklikleri kaydet'i** seçin. Üye eklemek birkaç dakika sürebilir.

5. **Sonraki adımlar'ın** altında **Bu posta kutusuna üye ekle'yi** seçin. Üyeler, bu paylaşılan posta kutusuna gelen e-postaları ve posta kutusundan giden yanıtları görüntüleyebilen kişilerdir.

   ![Üye Ekle'yi seçin.](../../media/a2a72e3d-6170-40fe-a94f-0af8fbef8ab2.png)

6. **+Üye ekle** düğmesini seçin. Bu paylaşılan posta kutusunu kullanmak istediğiniz kişilerin yanına bir onay işareti koyun ve **kaydet'i** seçin.

   ![Paylaşılan posta kutusuna üye atayın.](../../media/e6c58953-f6d7-4f0b-97ba-308516bf2a94.png)

7. **Kapat**'ı seçin.

Paylaşılan bir posta kutunuz var ve paylaşılan bir takvim içeriyor. Sonraki adıma geçin: [Paylaşılan posta kutusu hesabı için oturum açmayı engelle](#block-sign-in-for-the-shared-mailbox-account).

## <a name="which-permissions-should-you-use"></a>Hangi izinleri kullanmanız gerekir?

Paylaşılan posta kutusuyla aşağıdaki izinleri kullanabilirsiniz:

- **Tam Erişim**: Tam Erişim izni, kullanıcının paylaşılan posta kutusunu açmasına ve bu posta kutusunun sahibi olarak davranmasına olanak tanır. Kullanıcı paylaşılan posta kutusuna eriştiğinde takvim öğeleri oluşturabilir, e-posta iletilerini okuyabilir, görüntüleyebilir, silebilir ve değiştirebilir, görevler ve takvim kişileri oluşturabilir. Ancak Tam Erişim iznine sahip bir kullanıcı, Farklı Gönder veya Adına Gönder iznine sahip olmadığı sürece paylaşılan posta kutusundan e-posta gönderemez.

- **Farklı Gönder**: Farklı Gönder izni, kullanıcının posta gönderirken paylaşılan posta kutusunun kimliğine bürünmesine olanak tanır. Örneğin, Katerina paylaşılan posta kutusu Pazarlama Departmanı'na oturum açar ve bir e-posta gönderirse, Pazarlama Departmanı e-postayı göndermiş gibi görünür.

- **Adına Gönder**: Adına Gönder izni, kullanıcının paylaşılan posta kutusu adına e-posta göndermesine olanak tanır. Örneğin, John paylaşılan posta kutusu Resepsiyon Binası 32'de oturum açar ve bir e-posta gönderirse, posta "Resepsiyon Binası 32 adına John" tarafından gönderilmiş gibi görünür. EAC'yi, Adına Gönder izinleri vermek için kullanamazsınız; _GrantSendonBehalf_ parametresiyle **Set-Mailbox** cmdlet'ini kullanmanız gerekir.

> [!NOTE]
> Posta kutusunda *HiddenFromAddressListsEnabled* parametresi **True** olarak ayarlandığından, Farklı **Gönder** ve **Adına Gönder** izinleri Outlook masaüstü istemcisinde çalışmaz, çünkü posta kutusunun Genel Adres Listesi aracılığıyla Outlook görünür olmasını gerektirir.

### <a name="use-the-eac-to-edit-shared-mailbox-delegation"></a>Paylaşılan posta kutusu temsilcilerini EAC üzerinden düzenleme

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezinde</a> **Alıcılar** \> **Posta Kutuları'na** gidin. Paylaşılan posta kutusunu ve ardından **Düzenle** ![Düzenle simgesi..](../../media/ITPro-EAC-EditIcon.png). öğesini seçin.

2. **Posta kutusu izinleri'nin** altında **Posta kutusu temsilcisini yönet'i** seçin.

3. Tam Erişim ve Farklı Gönder izinleri vermek veya kaldırmak için Ekle Simge **Ekle'yi** ![seçin.](../../media/ITPro-EAC-AddIcon.png) veya **Kaldır** ![simgesine](../../media/ITPro-EAC-RemoveIcon.gif) tıklayıp izin vermek istediğiniz kullanıcıları seçin.

   > [!NOTE]
   > Tam Erişim izni verdiğiniz kullanıcı posta kutusunu açabilir, posta kutusunun içinde öğe oluşturabilir veya bu öğeleri değiştirebilir. Farklı Gönder izni, posta kutusu sahibi dışındaki herkesin bu paylaşılan posta kutusundan e-posta gönderebilmesini sağlar. Paylaşılan posta kutusu işleminin başarılı olması için her iki izin de gereklidir.

4. Değişikliklerinizi kaydetmek için **Kaydet'i** seçin.


## <a name="block-sign-in-for-the-shared-mailbox-account"></a>Paylaşılan posta kutusu hesabı için oturum açmayı engelle

Her paylaşılan posta kutusunun karşılık gelen bir kullanıcı hesabı vardır. Paylaşılan posta kutusunu oluştururken parola girmenizin nasıl istendiğini fark ettin mi? Hesabın parolası var, ancak sistem tarafından oluşturulmuş (bilinmiyor). Paylaşılan posta kutusunda oturum açmak için hesabı kullanmanız gerekmez.

Peki bir yönetici paylaşılan posta kutusu kullanıcı hesabının parolasını sıfırlarsa ne olur? Ya da bir saldırgan paylaşılan posta kutusu hesabı kimlik bilgilerine erişim elde ederse ne olur? Bu, kullanıcı hesabının paylaşılan posta kutusunda oturum açmasına ve e-posta göndermesine olanak tanır. Bunu önlemek için, paylaşılan posta kutusuyla ilişkili hesapta oturum açmayı engellemeniz gerekir.

::: moniker range="o365-worldwide"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.
::: moniker-end

2. Kullanıcı hesapları listesinde, paylaşılan posta kutusunun hesabını bulun (örneğin, filtreyi **Lisanssız kullanıcılar** olarak değiştirin).

3. Özellikler bölmesini açmak için kullanıcıyı seçin ve ardından **Bu kullanıcıyı engelle** simgesini ![seçin Bu kullanıcıyı engelle simgesinin Ekran görüntüsü.](../../media/block-user-icon.png).

   > [!NOTE]
   > Hesap zaten engellenmişse, oturum **açma engellendi** üst kısımda görünür ve simge **bu kullanıcının engellemesini kaldır'ı** okur.

4. **Bu kullanıcı engellensin mi?** bölmesinde **Kullanıcının oturum açmasını engelle'yi** ve ardından **Değişiklikleri kaydet'i** seçin.

Azure AD PowerShell kullanarak hesaplarda oturum açmayı engelleme yönergeleri için bkz. [PowerShell ile Office 365 kullanıcı hesaplarını engelleme](../../enterprise/block-user-accounts-with-microsoft-365-powershell.md).

## <a name="add-the-shared-mailbox-to-outlook"></a>Paylaşılan posta kutusunu Outlook'a ekleme

İşletmenizde otomatik eşlemeyi etkinleştirdiyseniz (varsayılan olarak, çoğu kişi etkinleştirilmişse), paylaşılan posta kutusu Outlook kapatıp yeniden başlattıktan sonra kullanıcınızın Outlook uygulamasında otomatik olarak görünür. 

Otomatik eşleme paylaşılan posta kutusunda değil, kullanıcının posta kutusunda ayarlanır. Bu, paylaşılan posta kutusuna kimlerin erişebileceğini yönetmek için güvenlik grubu kullanmaya çalışırsanız, otomatik eşlemenin çalışmayacağı anlamına gelir. Dolayısıyla, otomatik eşleme istiyorsanız izinleri açık bir şekilde atamalısınız. Otomatik eşleme varsayılan olarak açıktır. Nasıl kapatılacağını öğrenmek için bkz. [Paylaşılan posta kutusu için otomatik eşlemeyi kaldırma](/office365/troubleshoot/administration/remove-automapping-for-shared-mailbox).

Outlook paylaşılan posta kutuları hakkında daha fazla bilgi edinmek için bkz:

- <a href="https://support.microsoft.com/office/d94a8e9e-21f1-4240-808b-de9c9c088afd" target="_blank">Outlook’ta paylaşılan posta kutusunu açma ve kullanma</a>

- <a href="https://support.microsoft.com/office/98b5a90d-4e38-415d-a030-f09a4cd28207" target="_blank">Web üzerinde Outlook’a paylaşılan posta kutusu ekleme</a>

- <a href="https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f" target="_blank">Outlook mobil cihazlara paylaşılan posta kutusu ekleme</a>

- <a href="https://support.microsoft.com/office/6ecc39c5-5577-4a1d-b18c-bbdc92972cb2" target="_blank">Mac için Outlook'ta paylaşılan klasör veya posta kutusu açma</a>

- <a href="https://support.microsoft.com/office/b0963400-2a51-4c64-afc7-b816d737d164" target="_blank">Paylaşılan posta kutusuna kural ekleme</a>

## <a name="use-a-shared-mailbox-on-a-mobile-device-phone-or-tablet"></a>Mobil cihazda (telefon veya tablet) paylaşılan posta kutusu kullanma

Paylaşılan posta kutusuna mobil cihazda iki şekilde erişebilirsiniz:
- Paylaşılan posta kutusunu <a href="https://apps.apple.com/us/app/microsoft-outlook/id951937596" target="_blank">iOS uygulaması için Outlook veya Android</a> <a href="https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en_US" target="_blank">mobil uygulaması için Outlook</a> ekleyin. 
    
    Yönergeler için bkz. <a href="https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f" target="_blank">Outlook mobil cihazlara paylaşılan posta kutusu ekleme</a>.

- Tarayıcınızı açın, oturum açın ve Web üzerinde Outlook gidin. Paylaşılan posta kutunuza web üzerinde Outlook'tan erişebilirsiniz.

    Yönergeler için bkz. <a href="https://support.microsoft.com/office/98b5a90d-4e38-415d-a030-f09a4cd28207" target="_blank">Web üzerinde Outlook paylaşılan posta kutusu ekleme</a>.
    
> [!NOTE]
> Paylaşılan posta kutusu yalnızca iOS uygulaması için Outlook veya Android mobil uygulaması için Outlook eklenebilir

## <a name="use-the-shared-calendar"></a>Paylaşılan takvimi kullanma

Paylaşılan posta kutusunu oluşturduğunuzda, otomatik olarak paylaşılan bir takvim oluşturdunuz. Randevuları ve kişilerin nerede olduğunu izlemek için SharePoint takvimi yerine paylaşılan posta kutusu takvimini beğeniyoruz. Paylaşılan takvim Outlook ile tümleşiktir ve kullanımı SharePoint takvimden çok daha kolaydır.

1. Outlook uygulamasında takvim görünümüne gidin ve paylaşılan posta kutusunu seçin.

2. Girdiğiniz randevular paylaşılan posta kutusu üyelerinin tamamı tarafından görüntülenebilir.

3. Paylaşılan posta kutusunun herhangi bir üyesi, kişisel randevularında olduğu gibi takvimde randevu oluşturabilir, görüntüleyebilir ve yönetebilir. Paylaşılan posta kutusunun üyesi olan herkes paylaşılan takvimdeki değişikliklerini görebilir.

## <a name="related-content"></a>İlgili içerik

[Paylaşılan posta kutuları hakkında](about-shared-mailboxes.md) (makale)\
[Paylaşılan posta kutusunu yapılandırma](configure-a-shared-mailbox.md) (makale)\
[Kullanıcı posta kutusunu paylaşılan posta kutusuna dönüştürme](convert-user-mailbox-to-shared-mailbox.md) (makale)\
[Paylaşılan posta kutusundan lisans kaldırma](remove-license-from-shared-mailbox.md) (makale)\
[Paylaşılan posta kutularıyla ilgili sorunları çözme](resolve-issues-with-shared-mailboxes.md) (makale)
