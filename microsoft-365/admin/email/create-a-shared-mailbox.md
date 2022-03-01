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
description: İşletmenizin birden çok kullanıcının, bir adrese gönderilen e-postayı okuma ve yanıtlama sorumluluğunu paylaşmalarını sağlamak için paylaşılan posta kutusu oluşturun.
ms.openlocfilehash: f8a7f725e029021626bf408a3797ac6bfbb16215
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011839"
---
# <a name="create-a-shared-mailbox"></a>Paylaşılan posta kutusu oluşturma 

> [!NOTE]
> Organizasyonunız karma bir posta Exchange kullanıyorsa, paylaşılan posta kutuları oluşturmak ve yönetmek <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">için Exchange</a> yönetim merkezini kullanmalıdır. Bkz[. Paylaşılan posta kutularını yönetim Exchange oluşturma](/Exchange/collaboration/shared-mailboxes/create-shared-mailboxes?preserve-view=true.&view=exchserver-2019)
>
> Paylaşılan bir posta kutusu mu, yoksa paylaşılan posta kutusu mu oluşturmanız gerektiğine Microsoft 365, Outlook yol gösterici bilgi için Grupları karşılaştırma'ya bakın.[](../create-groups/compare-groups.md) Şu anda, paylaşılan bir posta kutusunu paylaşılan posta kutusunun paylaşılan bir grupla geçirmenin Microsoft 365 unutmayın. Bu sizin için önemli bir sorunsa, burada oylamayı [kullanarak bize bunu haber vermemiz gerekiyor](https://go.microsoft.com/fwlink/?linkid=871518).

Bir grup kullanıcının, bilgi@contoso.com gibi ortak bir e-posta adresini izleyebildiği ve bu adresten e-posta gönderebildiği bir paylaşılan posta kutusu kolayca oluşturulabilir. Paylaşılan posta kutusuna gönderilen bir ileti gruptaki bir kullanıcı tarafından yanıtlandığında e-posta, kullanıcı tarafından değil, paylaşılan posta kutusu tarafından gönderilmiş olarak görüntülenir.

Paylaşılan posta kutuları paylaşılan bir takvim içerir. Küçük işletmelerin birçoğu, paylaşılan takvimi herkesin randevularını girebildiği ortak bir yer olarak kullanır. Örneğin, işletmenizde müşteri ziyaretleri yapan 3 kişi, randevularını girmek için paylaşılan takvimi kullanabilir. Böylece herkes, diğerlerinin nerede olduğundan haberdar olabilir.

Paylaşılan posta kutusu oluşturmadan önce, daha fazla bilgi için [Paylaşılan posta kutuları hakkında makalelerini](about-shared-mailboxes.md) okuduğundan emin olun.

> [!TIP]
> Bu konudaki adımlarda yardıma ihtiyacınız varsa, [Microsoft küçük işletme uzmanıyla çalışmayı göz önünde bulundurabilirsiniz](https://go.microsoft.com/fwlink/?linkid=2186871). İş Yardımı ile, işe alımtan günlük kullanıma kadar işlerinizi büyüttükçe siz ve çalışanlarınız küçük işletme uzmanlarına 24 saat erişim elde ediyor.

## <a name="create-a-shared-mailbox-and-add-members"></a>Paylaşılan posta kutusu oluşturma ve üye ekleme
  
1. Genel yönetici hesabıyla veya yönetici Exchange açın. "Bu sayfaya erişim **veya bu** işlemi gerçekleştirme izniniz yok" mesajını alırsanız yönetici değilseniz. 

::: moniker range="o365-worldwide"

2. Yönetim merkezinde Paylaşılan Gruplar posta **kutuları Teams &** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">gidin</a>.

::: moniker-end

::: moniker range="o365-21vianet"

2. Yönetim merkezinde [Paylaşılan](https://go.microsoft.com/fwlink/p/?linkid=850627) Gruplar posta **kutuları Teams &** \> **gidin**.

::: moniker-end
    
3. Paylaşılan posta **kutuları sayfasında +** Paylaşılan posta **kutusu ekle'yi seçin**. Paylaşılan posta kutusu için bir ad girin. E-posta adresini seçer, ancak gerekirse düzenleyebilirsiniz.
    
    ![Name your shared mailbox.](../../media/e3035132-8986-4ec7-b7c0-f2752080d2c0.png)
  
4. Değişiklikleri **kaydet'i seçin**. Üye eklemek birkaç dakika sürebilir.

5. Sonraki **adımlar'ın** altında Bu posta **kutusuna üye ekle'yi seçin**. Üyeler, bu paylaşılan posta kutusuna gelen e-postaları ve posta kutusundan giden yanıtları görüntüleyebilen kişilerdir.

   ![Üye Ekle'yi seçin.](../../media/a2a72e3d-6170-40fe-a94f-0af8fbef8ab2.png)

6. +Üye **ekle düğmesini** seçin. Bu paylaşılan posta kutusunu kullanmak istediğiniz kişilerin yanına onay işareti koyarak Kaydet'i **seçin**.

   ![Paylaşılan posta kutusuna üye atama.](../../media/e6c58953-f6d7-4f0b-97ba-308516bf2a94.png)

7. **Kapat**'ı seçin.

Paylaşılan bir posta kutunuz var ve bu posta kutusu paylaşılan takvimi de içerir. Sonraki adıma geçin: [Paylaşılan posta kutusu hesabı için oturum açma engelleme](#block-sign-in-for-the-shared-mailbox-account).

## <a name="which-permissions-should-you-use"></a>Hangi izinleri kullanmanız gerekir?

Paylaşılan posta kutusuyla aşağıdaki izinleri kullanabilirsiniz:

- **Tam Erişim**: Tam Erişim izni, kullanıcının paylaşılan posta kutusunu açmalarına ve bu posta kutusunun sahibi gibi davranmalarına olanak sağlar. Paylaşılan posta kutusuna erişdikten sonra, kullanıcı takvim öğeleri oluşturabilir, e-posta iletilerini okuyabilir,  bakabilirsiniz, silebilir ve değiştirebilir, ayrıca görevler ve takvim kişileri oluşturabilir. Ancak Tam Erişim iznine sahip bir kullanıcı, Farklı Gönder veya Adına Gönder iznine sahip olmadığı sürece paylaşılan posta kutusundan e-posta gönderemez.

- **Farklı Gönder**: Farklı Gönder izni, kullanıcının posta gönderirken paylaşılan posta kutusunun kimliğine bürünme iznini sağlar. Örneğin, Katerina Pazarlama Departmanının paylaşılan posta kutusunda oturum açtığında bir e-posta gönderirse, e-posta Pazarlama Departmanı tarafından gönderilmiş gibi olur.

- **Adına Gönderme**: Adına Gönderme izni kullanıcının paylaşılan posta kutusu adına e-posta göndermesine olanak sağlar. Örneğin, Can paylaşılan posta kutusunda Resepsiyon Yapı 32'de oturum açtığında bir e-posta gönderirse, posta "Resepsiyon Binası 32 adına Can" tarafından gönderilmiş gibi olur. Adına Gönderme izinleri vermek için EAC'i kullanasınız, **Set-Mailbox** cmdlet'ini _GrantSendonBehalf parametresiyle kullanabilirsiniz_ .

### <a name="use-the-eac-to-edit-shared-mailbox-delegation"></a>Paylaşılan posta kutusu temsilcilerini EAC üzerinden düzenleme

1. Genel <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange merkezinde Paylaşılan</a> **Alıcılar'a** \> **gidin**. Paylaşılan posta kutusunu seçin ve ardından **Düzenle simgesini** ![seçin](../../media/ITPro-EAC-EditIcon.png).

2. Posta kutusu **temsilcisi öğesini seçin**.

3. Tam Erişim ve Farklı Gönder izinleri vermek veya kaldırmak için Simge **Ekle'yi** ![seçin.](../../media/ITPro-EAC-AddIcon.png) veya **Kaldır** ![simgesini](../../media/ITPro-EAC-RemoveIcon.gif) kaldırın ve ardından izin vermek istediğiniz kullanıcıları seçin.

   > [!NOTE]
   > Tam Erişim izni verdiğiniz kullanıcı posta kutusunu açabilir, posta kutusunun içinde öğe oluşturabilir veya bu öğeleri değiştirebilir. Farklı Gönder izni, posta kutusu sahibi dışındaki herkesin bu paylaşılan posta kutusundan e-posta gönderebilmesini sağlar. Paylaşılan posta kutusu işleminin başarılı olması için her iki izin de gereklidir.

4. **Değişikliklerinizi kaydetmek** için Kaydet'i seçin.


## <a name="block-sign-in-for-the-shared-mailbox-account"></a>Paylaşılan posta kutusu hesabı için oturum açma engelleme

Her paylaşılan posta kutusunun buna karşılık gelen bir kullanıcı hesabı vardır. Paylaşılan posta kutusunu oluşturulduğunda nasıl parola sağlamanın istenmeyeceğini fark ettiniz mi? Bu hesabın bir parolası var, ancak sistem tarafından oluşturulmuş (bilinmiyor) bir hesap. Paylaşılan posta kutusunda oturum açmak için hesabı kullanmaya gerek yok.

Peki ya yönetici paylaşılan posta kutusu kullanıcı hesabının parolasını sıfırlarsa? Peki bir saldırgan paylaşılan posta kutusu hesabı kimlik bilgilerine erişim kazanırsa ne olur? Bu, kullanıcı hesabının paylaşılan posta kutusunda oturum açmasına ve e-posta göndermesine olanak sağlar. Bunu önlemek için, paylaşılan posta kutusuyla ilişkilendirilmiş hesabın oturum açmasını engellemelisiniz.

::: moniker range="o365-worldwide"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.
::: moniker-end

2. Kullanıcı hesapları listesinde, paylaşılan posta kutusunun hesabını bulun (örneğin, filtreyi Lisanssız kullanıcılar **olarak değiştirme**).

3. Özellikler bölmesini açmak için kullanıcısı seçin ve ardından Bu  ![kullanıcı simgesini engelle Simgesinin Ekran görüntüsü öğesini seçin.](../../media/block-user-icon.png)

   > [!NOTE]
   > Hesap zaten engellenmişse, **en üstte** Oturum açma engellendi gösterilir ve simgede Bu kullanıcının engellemesini **kaldır okur**.

4. Bu kullanıcı **engellensin mi?** bölmesinde Kullanıcının **oturum açmasını engelle'yi ve sonra** Da Değişiklikleri **kaydet'i seçin**.

Azure AD PowerShell kullanan hesaplarda oturum açmayı engelleme yönergeleri için (aynı anda birçok hesap dahil), bkz. [Office 365 PowerShell ile kullanıcı hesaplarını engelleme](../../enterprise/block-user-accounts-with-microsoft-365-powershell.md).

## <a name="add-the-shared-mailbox-to-outlook"></a>Paylaşılan posta kutusunu Outlook'a ekleme

İşletmende otomatik kırpmayı etkinleştirdiyseniz (varsayılan olarak çoğu kişi bunu yapar), paylaşılan posta kutusu, kullanıcınızı kapatıp yeniden başlattıktan sonra Outlook uygulamasının Outlook. 

Otomatik eşleme paylaşılan posta kutusunda değil, kullanıcının posta kutusunda ayarlanır. Bu, paylaşılan posta kutusuna kimlerin erişebileceğini yönetmek için güvenlik grubu kullanmaya çalışırsanız, otomatik eşlemenin çalışmayacağı anlamına gelir. Dolayısıyla, otomatik eşleme istiyorsanız izinleri açık bir şekilde atamalısınız. Otomatik kırpma varsayılan olarak açıktır. Nasıl kapatılacaklarını öğrenmek için bkz. [Paylaşılan posta kutusunda otomatik kırpmayı kaldırma](/office365/troubleshoot/administration/remove-automapping-for-shared-mailbox).

E-posta kutularıyla ilgili paylaşılan posta kutuları hakkında daha fazla bilgi Outlook bkz:

- <a href="https://support.microsoft.com/office/d94a8e9e-21f1-4240-808b-de9c9c088afd" target="_blank">Outlook’ta paylaşılan posta kutusunu açma ve kullanma</a>

- <a href="https://support.microsoft.com/office/98b5a90d-4e38-415d-a030-f09a4cd28207" target="_blank">Web üzerinde Outlook’a paylaşılan posta kutusu ekleme</a>

- <a href="https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f" target="_blank">Mobil cihazlara paylaşılan posta Outlook ekleme</a>

- <a href="https://support.microsoft.com/office/6ecc39c5-5577-4a1d-b18c-bbdc92972cb2" target="_blank">Mac için Outlook'ta paylaşılan klasör veya posta kutusu açma</a>

- <a href="https://support.microsoft.com/office/b0963400-2a51-4c64-afc7-b816d737d164" target="_blank">Paylaşılan posta kutusuna kurallar ekleme</a>

## <a name="use-a-shared-mailbox-on-a-mobile-device-phone-or-tablet"></a>Mobil cihazda (telefon veya tablet) paylaşılan posta kutusu kullanma

Mobil cihazda paylaşılan posta kutusuna iki şekilde erişebilirsiniz:
- Paylaşılan posta kutusunu <a href="https://apps.apple.com/us/app/microsoft-outlook/id951937596" target="_blank">iOS için Outlook Mobil Uygulama uygulamasına</a> veya <a href="https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en_US" target="_blank">Android Outlook uygulamasına ekleyin</a>. 
    
    Yönergeler için bkz<a href="https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f" target="_blank">. Mobil cihazlara paylaşılan posta Outlook ekleme</a>.

- Tarayıcınızı açın, oturum açın ve Sonra Aç'a Web üzerinde Outlook. Paylaşılan posta kutunuza web üzerinde Outlook'tan erişebilirsiniz.

    Yönergeler için bkz<a href="https://support.microsoft.com/office/98b5a90d-4e38-415d-a030-f09a4cd28207" target="_blank">. Posta kutusuna paylaşılan posta Web üzerinde Outlook</a>.
    
> [!NOTE]
> Paylaşılan posta kutusu yalnızca iOS için Outlook uygulamasına veya Android Outlook uygulamasına eklenebilir

## <a name="use-the-shared-calendar"></a>Paylaşılan takvimi kullanma

Paylaşılan posta kutusunu oluşturulduğunda, otomatik olarak paylaşılan bir takvim oluşturdunız. Randevuları ve kişilerin nerede olduğunu izlemek için SharePoint bir takvim yerine paylaşılan posta kutusu takvimini sıyrıyız. Paylaşılan takvim, paylaşılan Outlook tümleştirilmiştir ve paylaşılan bir takvimle SharePoint kolaydır.

1. Takvim Outlook takvim görünümüne gidin ve paylaşılan posta kutusunu seçin.

2. Girdiğiniz randevular paylaşılan posta kutusu üyelerinin tamamı tarafından görüntülenebilir.

3. Paylaşılan posta kutusunun tüm üyeleri, tıpkı kendi kişisel randevularında yaptıkları gibi takvimde randevu oluşturabilir,  görünümüne sahip olabilir ve yönetebilir. Paylaşılan posta kutusunun üyesi olan herkes paylaşılan takvimde yaptıkları değişiklikleri görebilir.

## <a name="related-content"></a>İlgili içerik

[Paylaşılan posta kutuları hakkında](about-shared-mailboxes.md) (makale)\
[Paylaşılan posta kutusunu yapılandırma](configure-a-shared-mailbox.md) (makale)\
[Kullanıcı posta kutusunu paylaşılan posta kutusuna dönüştürme](convert-user-mailbox-to-shared-mailbox.md) (makale)\
[Paylaşılan posta kutusundan lisans kaldırma](remove-license-from-shared-mailbox.md) (makale)\
[Paylaşılan posta kutularıyla ilgili sorunları çözme](resolve-issues-with-shared-mailboxes.md) (makale)
