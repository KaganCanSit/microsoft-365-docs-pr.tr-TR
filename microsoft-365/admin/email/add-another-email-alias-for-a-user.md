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
description: 'İşletmeler için Microsoft 365 hesabınızla ilişkilendirilmiş, e-posta diğer adı olarak adlandırılan birden fazla e-posta adresine nasıl sahip olabileceğinizi öğrenin. '
ms.openlocfilehash: 19303cb2c60455713595dbe23a23bae7e57efb71
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780225"
---
# <a name="add-another-email-alias-for-a-user"></a>Bir kullanıcı için başka bir e-posta diğer adı ekleme
  
Bu makale, iş abonelikleri olan Microsoft 365 yöneticilere yöneliktir. Ev kullanıcılarına yönelik değildir.
  
Microsoft 365 birincil e-posta adresi genellikle bir kullanıcının hesabı oluşturulduğunda atanmış olan e-posta adresidir. Kullanıcı başka birine e-posta gönderdiğinde, birincil e-posta adresi normalde e-posta uygulamalarının  *Kimden*  alanında gösterilen adrestir. Ayrıca, iş için Microsoft 365 hesaplarıyla ilişkilendirilmiş birden fazla e-posta adresi de olabilir. Bu ek adresler, diğer ad olarak adlandırılır. 
  
Örneğin Jenna'nın e-posta adresi jenna@contosoco.com olduğunu, ancak bazı kişilerin ona bu adla başvurması nedeniyle jen@contosoco.com de e-posta almak istediğini varsayalım. Her iki e-posta adresinin de Jenna'nın gelen kutusuna gitmesi için onun için diğer adlar oluşturabilirsiniz.
  
Bir kullanıcı için 400 adede kadar diğer ad oluşturabilirsiniz. Bunun için ek ücret veya lisans gerekmez.
  
> [!Tip]
> Birden çok kişinin info@NodPublishers.com veya sales@NodPublishers.com gibi tek bir e-posta adresine gönderilen e-postaları yönetmesini istiyorsanız, paylaşılan bir posta kutusu oluşturun. Daha fazla bilgi için bkz. [Paylaşılan posta kutusu oluşturma](create-a-shared-mailbox.md).

> [!TIP]
> Bu konuda verilen adımlarla ilgili yardıma ihtiyacınız varsa, [bir Microsoft küçük işletme uzmanıyla çalışmayı](https://go.microsoft.com/fwlink/?linkid=2186871) göz önünde bulundurun. İşletme Yardımı ile, işletmenizi büyütürken katılımdan gündelik kullanıma kadar her aşamada siz ve çalışanlarınız günün 24 saati küçük işletme uzmanlarına erişebilirsiniz.
  
## <a name="add-email-aliases-to-a-user"></a>Bir kullanıcıya e-posta diğer adı ekleme

Kullanıcıya e-posta diğer adları eklemek için Genel Yönetici haklarına sahip olmanız gerekir.

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

2. **Etkin Kullanıcılar** sayfasında Kullanıcı **adını ve e-postayı yönet** > kullanıcıyı seçin. Kişinin kendisine atanmış bir lisansı yoksa bu seçeneği görmezsiniz. 
    
3. **+ Diğer ad ekle'yi** seçin ve kullanıcı için yeni bir diğer ad girin.   
    
    > [!Important] 
    > "**'EmailAddresses' parametre adıyla eşleşen bir parametre bulunamıyor**" hata iletisini alırsanız, kiracınızı veya yakın zamanda eklediyseniz özel etki alanınızı ayarlama işleminin bitmesi biraz daha uzun sürer. Ayarlama işleminin tamamlanması 4 saat kadar sürebilir. Biraz bekleyerek ayarlama işleminin bitmesi için zaman tanıyın ve sonra yeniden deneyin. Sorun devam ederse sizin için tam eşitleme gerçekleştirecek olan Destek ekibini arayın.
    
  
    > [!IMPORTANT]
    > Aboneliğinizi GoDaddy'den veya başka bir iş ortağından satın aldıysanız, yeni diğer adı birincil olarak ayarlamak için GoDaddy/iş ortağı yönetim konsoluna gitmeniz gerekir. 


   > [!IMPORTANT]
   >  **Bu kullanıcı yerel Active Directory'nizle eşitlenir hata iletisini alırsanız. Bazı ayrıntılar yalnızca yerel Active Directory'niz aracılığıyla düzenlenebilir**; Bu, Active Directory'nin eşitlenmiş kullanıcılardaki öznitelikler için yetkili olduğu, şirket içi Active Directory öznitelikleri değiştirmeniz gerektiği anlamına gelir.
  
    > [!TIP]
    > E-posta diğer adı, açılan listeden bir etki alanıyla bitmelidir. Listeye başka bir etki alanı adı eklemek için bkz. [Microsoft 365 etki alanı ekleme](../setup/add-domain.md). 
  
     
5. İşiniz bittiğinde **Değişiklikleri kaydet'i** seçin.
    
6. Yeni diğer adların Microsoft 365 boyunca doldurulmalarını 24 saat bekleyin.
    
    Artık kullanıcının birincil adresi ve diğer adı olacaktır. Örneğin, Eliza Hoffman'ın birincil adresi olan Eliza@NodPublishers.com ve diğer adı Sales@NodPublishers.com gönderilen tüm postalar Eliza'nın Gelen Kutusu'na gider.
    
  
7. **Kullanıcı yanıtladığında *Kimden adresi,* Outlook istemcisine bağlıdır. Outlook na Web, e-postanın alındığı diğer adı kullanır (buna ping-pong ilkesi adını vereceğiz). Outlook masaüstü birincil e-posta diğer adını kullanır.** Örneğin, bir iletinin Sales@NodPublishers.com gönderildiğini ve Eliza'nın gelen kutusuna ulaştığını varsayalım. Eliza, Outlook masaüstü kullanarak iletiyi yanıtladığında birincil e-posta adresi Sales@NodPublishers.com değil Eliza@NodPublishers.com olarak görünür.
    
## <a name="did-you-get-a-parameter-cannot-be-found-that-matches-parameter-name-emailaddresses"></a>"EmailAddresses parametre adıyla eşleşen bir parametre bulunamadı" ifadesini aldınız mı?

"**EmailAddresses parametre adıyla eşleşen bir parametre bulunamıyor**" hata iletisini alırsanız, kiracınızı veya yakın zamanda eklediyseniz özel etki alanınızı ayarlama işleminin bitmesi biraz daha uzun sürer. Ayarlama işleminin tamamlanması 4 saat kadar sürebilir. Biraz bekleyerek ayarlama işleminin bitmesi için zaman tanıyın ve sonra yeniden deneyin. Sorun devam ederse sizin için tam eşitleme gerçekleştirecek olan Destek ekibini arayın.
  
## <a name="did-you-purchase-your-subscription-from-godaddy-or-another-partner"></a>Aboneliğinizi GoDaddy'den veya başka bir iş ortağından mı satın aldınız?


Aboneliğinizi GoDaddy'den veya başka bir iş ortağından satın aldıysanız, yeni diğer adı birincil olarak ayarlamak için GoDaddy/iş ortağı yönetim konsoluna gitmeniz gerekir.

## <a name="sending-email-from-the-proxy-address-easily"></a>Proxy adresinden kolayca e-posta gönderme

Temmuz 2021'de kullanıcıların Outlook na Web kullanırken diğer adlarından kolayca göndermelerini sağlayan yeni bir özellik kullanıma sunulacaktır. Özellik kiracı yöneticisinin cmdlet'ini `Set-OrganizationConfig -SendFromAliasEnabled $true` kullandığı bir kiracıya dağıtıldığında, kiracı içindeki kullanıcılar her girişin Outlook ayarlarındaki diğer adlara karşılık geldiği onay kutuları listesine erişebilir. Diğer ad seçildiğinde, Oluştur formundaki Kimden açılan listesinde görünür.
  
## <a name="related-content"></a>İlgili içerik

[Farklı bir adresten e-posta gönderme](https://support.microsoft.com/office/ccba89cb-141c-4a36-8c56-6d16a8556d2e) (makale)

[Kullanıcı adını ve e-posta adresini değiştirme](../add-users/change-a-user-name-and-email-address.md) (makale)

[Microsoft 365'de e-posta iletmeyi yapılandırma](configure-email-forwarding.md) (makale)
