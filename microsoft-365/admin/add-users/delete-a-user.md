---
title: Kuruluşunuzdan kullanıcı silme
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- SPO_Content
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
ms.assetid: d5155593-3bac-4d8d-9d8b-f4513a81479e
description: Kullanıcı hesabını silmeyi, kullanıcının e-postası ve e-postası ile ilgili ne OneDrive ve ürün lisansının açık olup olmadığını öğrenin.
ms.openlocfilehash: 462e9bcec4dac7e9d708618777ea58fb5d182473
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62996105"
---
# <a name="delete-a-user-from-your-organization"></a>Kuruluşunuzdan kullanıcı silme
  
**İşte veya okulda kullanmakta *Microsoft 365* kullanıcı hesabınızı nasıl silebilirsiniz? Bu adımları sizin için yapmak için iş yeriz veya üniversitenizin teknik destek ekibiyle iletişime geçin.**

## <a name="before-you-begin"></a>Başlamadan önce

- Yalnızca işletme veya [Microsoft 365 yöneticisi veya](about-admin-roles.md) Kullanıcı yönetimi izinleri olan kişiler kullanıcı hesaplarını silebilir.
- Kullanıcının verileri kalıcı olarak silinmeden önce hesabı [geri yüklemek](restore-user.md) için 30 gününüz vardır.
- Kullanıcının kendi verilerini tutmak OneDrive başka bir konuma taşıma. Hatta hesabı sildikten sonra verileri 30 gün içinde hareket ettirebilirsiniz. Bkz [. Eski kullanıcının verilerine erişme ve bu verileri koruma](get-access-to-and-back-up-a-former-user-s-data.md). Kendi dosya ve dosyalarını taşımanıza SharePoint, bu dosyalara yine erişebilirsiniz.
- Kullanıcının e-postasını saklamak istiyorsanız hesabı silmeden **ÖNCE** e-postayı farklı bir konuma taşıyın. Hesabı zaten sildiyseniz ve silme işleminin üzerinden 30 günden az zaman geçtiyse hesabı geri yükleyip e-posta verilerini taşıyabilir ve hesabı silebilirsiniz. Bkz. [Eski bir kullanıcının verilerine erişme ve bu verileri yedekleme](get-access-to-and-back-up-a-former-user-s-data.md).
- Enterprise E3 gibi bir Office 365 Kurumsal aboneliğiniz varsa, silinmiş kullanıcı hesabının posta kutusu verilerini etkin olmayan posta kutusuna dönüştürerek *koruyabilirsiniz*. Daha fazla bilgi edinmek için bkz[. Etkin olmayan posta kutularını kendi Exchange Online](../../compliance/inactive-mailboxes-in-office-365.md).

## <a name="global-admin-delete-a-user-stop-paying-for-their-license-and-choose-what-to-do-with-their-email-and-onedrive-content"></a>Genel yönetici: Kullanıcı silme, kullanıcının lisansı için ödeme yapmayı bırakma ve kullanıcının e-postasıyla ve OneDrive içeriğiyle ne yapılacağına karar verme

Genel yöneticiyseniz, bir kullanıcıyı sildiğinizde başka bir kullanıcının sildiğiniz kullanıcının e-postasına erişmesini sağlayabilir ve sildiğiniz kullanıcının OneDrive içeriğiyle ne yapılacağına karar verebilirsiniz.

### <a name="things-to-consider"></a>Göz önüne alınacak noktalar

Başlamadan önce, kullanıcının e-postası ve OneDrive içeriği ile ne yapmak istediğinizi düşünün ve lisansı elinizde tutma ya da ödemeyi bırakma konusunda bir karar verin.
  
|Öğe | Açıklama |
|:-----|:-----|
|Ürün lisansları  <br/> |Lisansı kullanıcının hesabından kaldırabilir ve bu lisans için ödeme yapmayı bırakmak için lisansı aboneliklerinizden çıkarabilirsiniz. Bu seçeneği belirlerseniz, lisans aboneliklerinizden otomatik olarak kaldırılır.  <br/><br/> Lisansı bir iş ortağı aracılığıyla ya da toplu lisanslama üzerinden satın aldıysanız **kaldıramazsınız**. Yıllık bir planla ödeme yapmayı planlıyorsanız veya bir faturalama döngüsünün ortasındaysanız, taahhüdüdüniz tamamlanana kadar lisansı aboneliğinden kaldırasınız.  <br/> |
|OneDrive içeriği  <br/> |Kullanıcı, dosyalarını OneDrive'a kaydettiyse, başka bir kullanıcıya bu dosyalar için erişim verebilirsiniz.  <br/><br/> Saklamak istediğiniz dosyaları, OneDrive dosyaları için ayarlanan bekletme süresi içinde taşımanız gerekir. **Varsayılan olarak, bekletme süresi 30 gündür.** Bir kullanıcı sildikten sonra bekletme süresi içinde dosyaları taşısanız bile, silinen OneDrive site koleksiyonu geri dönüşüm kutusu'na taşınır ve 93 gün boyunca tutulur. Bu süre boyunca, kullanıcılar artık paylaşılan içeriklere erişim OneDrive. Bu OneDrive geri yüklemek için PowerShell kullan gerekir. Bilgi için bkz[. Silinmiş bir veritabanını OneDrive](/onedrive/restore-deleted-onedrive).<br/><br/> Silinen hesapların OneDrive dosyalarını bekletebildiğiniz gün sayısını artırmak için bkz [Silinen kullanıcılar için OneDrive bekletme süresini ayarlama](/onedrive/set-retention).  <br/><br/> **Önemli!** Silinen kullanıcı SharePoint ve OneDrive dosyalarını indirmek için kişisel bilgisayar kullandısa, bu bilgisayara depolanmış olan bu dosyaları temizlemenin hiçbir yolu yoktur. Kullanıcı, OneDrive'dan eşitlenen tüm dosyalara erişmeye devam eder.           |
|E-posta  <br/> | Silinen kullanıcının e-postası için başka bir kullanıcıya erişim verildiğinde, silinen kullanıcının posta kutusu paylaşılan posta kutusuna dönüşür. Posta kutusunun yeni sahibi artık posta kutusuna erişebilir ve yeni e-postaları izleyebilir. Aşağıdaki seçeneklere de sahip olursunuz:  <br/>  <br/>Görünen adı değiştirme - Etkin kullanıcılar listesinde paylaşılan posta kutusunu kolayca tanımlamak için görünen adı **değiştirmenizi** öneririz.  <br/>  Otomatik yanıtları açma - Sizin için kibar bir otomatik yanıt hazırladık. Kuruluş içindeki ve dışındakilere farklı otomatik yanıtlar göndersiniz.  <br/> <br/> Diğer adları temizleme - Diğer adlar, kullanıcıların ek e-posta adresleridir. Bazı kuruluşlarda diğer adlar kullanılmaz; diğer adlarınız yoksa burada herhangi bir şey yapmanız gerekmez. Kullanıcının diğer adları varsa, bu e-posta adreslerini yeniden kullanasınız diye diğer adları kaldırmanızı öneririz. Aksi takdirde, silinmiş posta kutularının bekletme süresi geçene kadar bu e-posta adreslerini yeniden kullanılamaz. Varsayılan olarak, silinmiş bir posta kutusu 30 gün içerisinde kurtarılabilir. Daha fazla bilgi için bkz[. Posta kutularında kullanıcı posta kutularını silme Exchange Online](/exchange/recipients-in-exchange-online/delete-or-restore-mailboxes#delete-a-user-mailbox). <br/> |
|Active Directory  <br/> |İşletmeniz, Azure AD ile eşitlenen **Active Directory** kullanıyorsa, kullanıcı hesabını Active Directory'den silmeniz gerekir. Bunu Office 365 üzerinden yapamazsınız. Yönergeler için bkz [. Kullanıcı Hesabı Silme](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)).  <br/> |

### <a name="get-started"></a>Kullanmaya başlayın

Rehberli deneyim, bir kullanıcı silme adımlarını adım ilerleyeli olduğu için, şu şekilde başlamayı sağlar.

::: moniker range="o365-worldwide"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

 1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

2. Silmek istediğiniz kullanıcı seçin ve sonra da Kullanıcı **sil'i seçin**.

## <a name="user-management-admin-delete-one-or-more-users-from-office-365"></a>Kullanıcı yönetimi yöneticisi: Office 365'ten bir veya daha fazla kullanıcı silme

> [!IMPORTANT]
> Paylaşılan posta kutusuna dönüştüren bir kullanıcının hesabını silmeyi veya hesapta [](../email/convert-user-mailbox-to-shared-mailbox.md) e-posta iletmeyi ayarlamayı ayarlamışsanız, hesabı silmeyin. Bu işlevlerin hesaba ihtiyacı var. Paylaşılan posta kutusu lisans gerektirmez. Hesabı paylaşılan posta kutusuna dönüştürürken lisansın ödemesini [durdurabilirsiniz](#stop-paying-for-the-license). Hesapta e-posta iletmeyi ayardınız, lisansı kaldırasınız. Bu şekilde e-posta iletme durdurulacak ve posta kutusu devre dışı bırakılacak.
  
::: moniker range="o365-worldwide"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.  

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

2. Silmek istediğiniz kullanıcıların adlarını seçin, üç noktayı (diğer eylemler) ve ardından Kullanıcı  **sil'i seçin**.

   Kullanıcının hesabını silmiş olmasına rağmen lisans **için ödeme hala devam ediyorsanız**. Lisansa ödeme yapmak için sonraki yordama bakın.  Veya lisansı başka bir kullanıcıya at at buna siniz. Bu kişi otomatik olarak birine atanmaz.

### <a name="stop-paying-for-the-license"></a>Lisans için ödemeyi durdurma

Lisans sayısını azaltmak, yalnızca genel yönetici veya faturalama yöneticisi tarafından gerçekleştirilecek ayrı bir adımdır.
  
::: moniker range="o365-worldwide"

1. Yönetim merkezinde Ürünlerinizi Faturalandırma **sayfasına** \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank"></a>
::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezinde Ürünlerinizi Faturalandırma **sayfasına** \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank"></a>
::: moniker-end

2. Ürünler **sekmesinde** , lisanslarını kaldırmak istediğiniz aboneliği seçin.

3. Abonelik ayrıntıları sayfasında Lisansları **kaldır'ı seçin**.

4. Lisansları **kaldır** bölmesindeki **Yeni miktar'ın** altında, Toplam lisanslar  kutusuna bu abonelik için istediğiniz toplam lisans sayısını girin. Örneğin, 100 lisansınız varsa ve beş lisansı kaldırmak istiyorsanız, 95 girin.

5. **Kaydet**'i seçin.

Daha sonra işletmenize başka bir kişi ekleme adımlarını izleyerek, aynı anda yalnızca bir adımla lisans satın almak istenir!

## <a name="delete-many-users-at-the-same-time"></a>Aynı anda birkaç kullanıcı silme

Bkz. [Remove-MsolUser](/powershell/module/msonline/remove-msoluser) PowerShell cmdlet.

## <a name="fix-issues-with-deleting-a-user"></a>Bir kullanıcıyı silerken oluşan sorunları düzeltme

bir kullanıcı silinirken karşılaşılan en yaygın sorunlar şu şekildedir:
  
- **"Kullanıcı silinemiyor. Lütfen daha sonra yeniden deneyin." satırlarının bulunduğu bir hata iletisi alıyorsunuz.** Hesabın e-posta iletme için ayarlanmış olup olmadığını veya paylaşılan posta kutusuna dönüştürül olup olmadığını bir kez daha kontrol edin. Her iki durum da bu hataya neden olur. E-posta iletme ayarlandıysa veya paylaşılan posta kutusuna dönüştürüldüyse hesabı silmeyin.

- **Kullanıcı silmek için uygun izinleriniz yok**. Yalnızca genel [yöneticilerin veya Microsoft 365 yöneticilerinin kullanıcılarını](about-admin-roles.md) silebilir. Bu kişiler genelde okulunuzdaki veya işletmenizdeki teknik destek sorumlularıdır.

- **Kullanıcıları sildiniz ancak adları genel adres defterinde görünmeye devam ediyor**. İşletme Active Directory kullanıyorsa, bu durum ortaya çıkar. Kullanıcı hesabını Active Directory'den silmeniz gerekir. Yönergeler için bkz [. Kullanıcı Hesabı Silme.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11))

**Bilgisayarınızdan bir Microsoft 365 silmek mi istiyor musunuz? Aboneliğinizi [iptal etme'ye gidin](../../commerce/subscriptions/cancel-your-subscription.md).**

## <a name="related-content"></a>İlgili içerik

[Bir kullanıcı geri yükleme](restore-user.md) (makale)\
[Posta kutusunu kalıcı olarak silme](/exchange/permanently-delete-a-mailbox-exchange-2013-help) (makale)\
[Eski bir çalışanı iş yerlerinden Office 365](remove-former-employee.md) (makale)\
[yeni çalışan ekleme (Office 365](add-new-employee.md))\
[Kullanıcı Hesabı Silme](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)): İşletmeniz Azure AD ile **eşitlenirken Active Directory** kullanıyorsa bu yönergeleri kullanın. Bunu Office 365 üzerinden yapamazsınız. (makale)
