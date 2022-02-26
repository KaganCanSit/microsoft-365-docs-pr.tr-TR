---
title: Bir kullanıcı için başka bir e-posta diğer adı ekleme
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
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 0b0bd900-68b1-4bf5-808b-5d240a7739f4
description: 'İş için Microsoft Hesabınızla ilişkilendirilmiş, e-posta diğer adı olarak adlandırılan birden Microsoft 365 e-posta adresinizin nasıl olduğunu öğrenin. '
ms.openlocfilehash: f5adc9e48110aa1e2a2e6c87f2c2f7847986d741
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "62973893"
---
# <a name="add-another-email-alias-for-a-user"></a>Bir kullanıcı için başka bir e-posta diğer adı ekleme
  
Bu makale, iş Microsoft 365 yöneticilerine göre hazırlanmıştır. Ev kullanıcılarına yönelik değildir.
  
E-posta Microsoft 365 birincil e-posta adresi genellikle kullanıcının hesabı oluşturulurken atanan e-posta adresidir. Kullanıcı başka birine e-posta gönderdiğinde, birincil e-posta adresi normalde e-posta uygulamalarının  *Kimden*  alanında gösterilen adrestir. Ayrıca, iş hesabı için e-posta adresleriyle ilişkilendirilmiş birden Microsoft 365 olabilir. Bu ek adresler, diğer ad olarak adlandırılır. 
  
Örneğin, her Zaman'ın e-posta adresinin Jenna@contosoco.com olduğunu, ancak bazı kişilerin ona bu adı kullanarak başvurdu jen@contosoco.com da e-posta almak istediğini var diyelim. Her iki e-posta adresinin Deha'nın gelen kutusu'na gitmeleri için onun için diğer adlar oluşturabilirsiniz.
  
Bir kullanıcı için 400 adede kadar diğer ad oluşturabilirsiniz. Bunun için ek ücret veya lisans gerekmez.
  
> [!Tip]
> Birden çok kişinin E-posta gibi tek bir e-posta adresine gönderilen e-info@NodPublishers.com sales@NodPublishers.com, paylaşılan bir posta kutusu oluşturun. Daha fazla bilgi edinmek için bkz [. Paylaşılan posta kutusu oluşturma](create-a-shared-mailbox.md).

> [!TIP]
> Bu konudaki adımlarda yardıma ihtiyacınız varsa, [Microsoft küçük işletme uzmanıyla çalışmayı göz önünde bulundurabilirsiniz](https://go.microsoft.com/fwlink/?linkid=2186871). İş Yardımı ile, işe alımtan günlük kullanıma kadar işlerinizi büyüttükçe siz ve çalışanlarınız küçük işletme uzmanlarına 24 saat erişim elde ediyor.
  
## <a name="add-email-aliases-to-a-user"></a>Bir kullanıcıya e-posta diğer adı ekleme

Bir kullanıcıya e-posta diğer adı eklemek için Genel Yönetici haklarına sahip olmak gerekir.

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

2. Etkin Kullanıcılar **sayfasında Kullanıcı adını** ve e-postayı > **öğesini seçin**. Kişiye atanmış lisansı yoksa bu seçeneği görmeyebilirsiniz. 
    
3. + **Diğer ad ekle'yi** seçin ve kullanıcı için yeni bir diğer ad girin.   
    
    > [!Important] 
    > "**'EmailAddresses**' parametre adıyla eşleşen bir parametre bulunamadı" hata iletisini alırsanız, kiracınızı veya özel etki alanınızı (yakın zamanda bir özel etki alanı eklediyseniz) ayarlamayı bitirmenin biraz uzun sürecek olduğu anlamına gelir. Ayarlama işleminin tamamlanması 4 saat kadar sürebilir. Biraz bekleyerek ayarlama işleminin bitmesi için zaman tanıyın ve sonra yeniden deneyin. Sorun devam ederse sizin için tam eşitleme gerçekleştirecek olan Destek ekibini arayın.
    
  
    > [!IMPORTANT]
    > Aboneliğinizi GoDaddy'den veya başka bir iş ortağından satın aldıysanız, yeni diğer adı birincil olarak ayarlamak için GoDaddy/iş ortağı yönetim konsoluna gitmeniz gerekir. 


   > [!IMPORTANT]
   >  Bu kullanıcı yerel **Active Directory'niz ile eşitlenmiş hata iletisini alırsanız. Bazı ayrıntılar yalnızca yerel Active Directory'niz** üzerinden düzenlenebilir; Bu, eşitlenmiş kullanıcılarda Active Directory'nin öznitelikler için yetkili olduğu anlamına gelir; bunun için şirket içi Active Directory'nizin özniteliklerini değiştirmeniz gerekir.
  
    > [!TIP]
    > E-posta diğer adı, açılan listeden bir etki alanıyla bitsin. Listeye başka bir etki alanı adı eklemek için bkz[. Etki alanına etki Microsoft 365](../setup/add-domain.md). 
  
     
5. Bitirin ve Değişiklikleri **kaydet'i seçin**.
    
6. Yeni diğer adların tüm adlara doldurmak için 24 Microsoft 365.
    
    Kullanıcının artık bir birincil adresi ve bir diğer adı olur. Örneğin, Aliye Söğer'in birincil adresine, Eliza@NodPublishers.com diğer adı Sales@NodPublishers.com, Ali'nin Gelen Kutusu'na gider.
    
  
7. **Kullanıcı yanıt verdi mi? *Adresi*, Yanıt adresi Outlook bağlıdır. Web üzerinde Outlook e-postanın alın aldığı diğer adı kullanacağız (ping-ilke adını kullanacağız). Outlook masaüstü onun birincil e-posta diğer adını kullanacak.** Örneğin, bir iletinin Ali'nin gelen Sales@NodPublishers.com'e gönderildiğini ve bu iletinin gelen kutularına gönderildiğini diyelim. Eliza, masaüstü bilgisayarını kullanarak iletiyi Outlook, birincil e-posta adresi e-posta Eliza@NodPublishers.com olarak Sales@NodPublishers.com.
    
## <a name="did-you-get-a-parameter-cannot-be-found-that-matches-parameter-name-emailaddresses"></a>"EmailAddresses parametre adıyla eşleşen bir parametre bulunamadı" mı?

"**EmailAddresses** parametre adıyla eşleşen bir parametre bulunamadı" hata iletisini alırsanız, kiracınızı veya özel etki alanınızı (yakın zamanda bir özel etki alanı eklediyseniz) ayarlamayı bitirmeniz biraz uzun sürer. Ayarlama işleminin tamamlanması 4 saat kadar sürebilir. Biraz bekleyerek ayarlama işleminin bitmesi için zaman tanıyın ve sonra yeniden deneyin. Sorun devam ederse sizin için tam eşitleme gerçekleştirecek olan Destek ekibini arayın.
  
## <a name="did-you-purchase-your-subscription-from-godaddy-or-another-partner"></a>Aboneliğinizi GoDaddy'den veya başka bir iş ortağından mı satın aldınız?


Aboneliğinizi GoDaddy'den veya başka bir iş ortağından satın aldıysanız, yeni diğer adı birincil olarak ayarlamak için GoDaddy/iş ortağı yönetim konsoluna gitmeniz gerekir.

## <a name="sending-email-from-the-proxy-address-easily"></a>Proxy adresinden kolayca e-posta gönderme

Temmuz 2021'de, kullanıcıların diğer adlarını kullanırken diğer adlarından kolayca göndermelerine olanak sağlayan yeni bir Web üzerinde Outlook. `Set-OrganizationConfig -SendFromAliasEnabled $true` Özellik kiracı yöneticisinin cmdlet'i kullandığı bir kiraya yuvarlansa, kiracı içindeki kullanıcılar her girdinin kendi kiracı ayarlarında bir diğer ada karşılık gelen onay kutuları listesine Outlook. Diğer ad seçmek, bu adın Oluşturma formundaKimlik açılan listesinde görünmesine neden olur.
  
## <a name="related-content"></a>İlgili içerik

[Farklı bir adresten e-posta gönderme](https://support.microsoft.com/office/ccba89cb-141c-4a36-8c56-6d16a8556d2e) (makale)

[Kullanıcı adını ve e-posta adresini değiştirme](../add-users/change-a-user-name-and-email-address.md) (makale)

[E-posta iletmeyi Microsoft 365](configure-email-forwarding.md) yapılandırma (makale)
