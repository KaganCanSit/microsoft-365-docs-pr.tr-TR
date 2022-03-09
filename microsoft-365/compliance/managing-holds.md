---
title: Aynı anda 12 Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Dosyanız için ilgili içeriği korumak için koruyucuları ve onların veri kaynaklarını nasıl Advanced eDiscovery öğrenin.
ms.custom:
- seo-marvel-mar2020
- admindeeplinkMAC
ms.openlocfilehash: d731c0cda31f96f5274ca0c2fd56d5e14901f3a9
ms.sourcegitcommit: a9266e4e7470e8c1e8afd31fef8d266f7849d781
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63406165"
---
# <a name="manage-holds-in-advanced-ediscovery"></a>Aynı anda 12 Advanced eDiscovery

Davanıza uygun Advanced eDiscovery korumak için bir koruma durumu kullanabilirsiniz. Koruma Advanced eDiscovery kullanarak koruyucuları ve onların veri kaynaklarını tutabilirsiniz. Buna ek olarak, posta kutularına ve posta kutularına veya sitelere özel olarak OneDrive İş tutabilirsiniz. Ayrıca, grup posta kutusunu, siteyi veya siteyi SharePoint OneDrive İş posta OneDrive İş yerinde Microsoft 365 edebilirsiniz. Benzer şekilde, posta kutusu ve siteyle ilişkili posta kutusunu ve siteyi yerinde Microsoft Teams. İçerik konumlarını yerinde bekletirseniz, içerik siz koruyucuları serbest bırakana, belirli bir veri konumunu kaldırana veya tutma ilkesi tamamen silene kadar basılır.

## <a name="manage-custodian-based-holds"></a>Custoomi tabanlı 1.

Bazı durumlarda, bu durum sırasında tanımmış ve verilerini korumaya karar vermiş olan bir dizi koruyucunız olabilir. Daha Advanced eDiscovery, bu koruyucular tutul olduğunda, kullanıcı ve onların seçili veri kaynakları otomatik olarak koruyucu tutma ilkesine eklenir.

Custo cust ilkeyi görüntülemek için:

1. Microsoft 365 uyumluluk merkezi durumlarda listesini görüntülemek için **eBulma > Gelişmiş'e** tıklayın.

2. Vakanız içinde **koruyucular** eklemek için Kaynaklar sekmesine gidin. Bir dava içinde koruyucuları nasıl ekplerin ekplerin yerinde tutarak tutarak tut uyy ekley ola Advanced eDiscovery bkz. [Vakaya Koruyucular ekleme](add-custodians-to-case.md). Koruyucuları zaten eklediysanız ve onları tutmada kullandıysanız, 3. adıma geçin.

3. 10. **Sekmeye gidin** ve **Custo birHold'a tıklayın\<HoldId>**.

4. Uçarak çıkış sayfasında, ilke için tutma istatistiklerini görebilirsiniz. Ayrıca, özel tutma için sorgu uygulama gibi eylemler de gerçekleştirebilirsiniz. Tutma sorgusu oluşturma ve koşulları kullanma hakkında daha fazla bilgi için bkz. [Anahtar sözcük sorguları ve İçerik Arama için arama koşulları](keyword-queries-and-search-conditions.md).

## <a name="manage-non-custodial-holds"></a>Özel durumlu olmayan mızrıları yönetme

Bir gerçekleştirilen içeriğin kapsamını belirtilen içerik konumlarında tutmak için aşağıdaki seçenekleri kullanabilirsiniz:

- Tüm içeriğin bulunduğu sonsuz bir tutma oluşturabilirsiniz. Alternatif olarak, yalnızca bir arama sorgusuyla eşleşen içeriğin yerine basılı tutma için sorgu tabanlı bir tutma oluşturabilirsiniz.
  
- Yalnızca bu tarih aralığında gönderilmiş, alınan veya oluşturulmuş içeriği tutmak için bir tarih aralığı belirtebilirsiniz. Alternatif olarak, ne zaman gönderildiğine, alınsa veya oluşturulduktan bağımsız olarak tüm içeriği tutabilirsiniz.

Özel durumlu olmayan bir özel durum Advanced eDiscovery için:

1. Microsoft 365 uyumluluk merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">durumlarda listesini</a> görüntülemek için **eBulma >** Gelişmiş'e tıklayın.
  
2. **1**. Durumdaki 12.000'i oluşturmak istediğiniz davanın yanındaki Aç'a tıklayın.
  
3. Vakanın giriş sayfasında, 10'da 12'yi **tıklatın** .
  
4. 10 **. Sekmede** , Oluştur'a **tıklayın**.
  
5. Tutmanıza **ad verme** sayfasında, basılı tutmanıza bir ad verme. Tutma adı, kurum içinde benzersiz olmalıdır.

6. (İsteğe bağlı) Açıklama **kutusunda** , tutma için bir açıklama ekleyin.
  
7. **İleri**'ye tıklayın.
  
8. Yerinde tutmak istediğiniz içerik konumlarını seçin. Posta kutularını, siteleri ve ortak klasörleri yerinde tutabilirsiniz.

   1. **Exchange-postayı** seçin - Kullanıcıları **,** grupları veya ekipleri seç'e tıklayın ve ardından yerinde posta kutularını belirtmek için Kullanıcıları **,** grupları veya ekipleri seç'e yeniden tıklayın. Kullanıcı posta kutularını ve dağıtım gruplarını (grup üyelerinin posta kutularını yerinde tutmak için) yerinde tutmak için arama kutusunu kullanın. Ayrıca, bir Grup veya Microsoft Ekibi'nden bir Microsoft 365 posta kutusunu da basılı tutabilirsiniz. Kullanıcı, grup, ekip onay kutusunu seçin, Seç'e **tıklayın ve** sonra da Bitti'ye **tıklayın**.

      > [!NOTE]
      > Yerinde yerinde posta **kutularını belirtmek için Kullanıcıları,** grupları veya ekipleri seç'e tıklarken görüntülenen posta kutusu seçici boş olur. Bu, performansı geliştirmek için tasarımdandır. Bu listeye kişi eklemek için arama kutusuna bir ad (en az 3 karakter) yazın.

   1. **SharePoint Ekle - Siteleri** **seç'e** tıklayın ve ardından sitelerin  yerinde SharePoint için OneDrive İş Seç'e yeniden tıklayın. Yerinde tutmak istediğiniz her sitenin URL'sini yazın. Ayrıca, bir Grup veya Microsoft SharePoint sitenin MICROSOFT 365 URL'sini de ebilirsiniz. **Seç'e** ve ardından **Bitti'ye tıklayın**.

      > [!NOTE]
      > Bir kullanıcının anapara hesabının URL'si OneDrive asıl adını (UPN) içerir (örneğin, `https://alpinehouse-my.sharepoint.com/personal/sarad_alpinehouse_onmicrosoft_com`). Nadiren de olsa kişinin UPN'si değiştirilirse, URL'leri OneDrive UPN'yi de dahil etmek için değişir. Kullanıcının kullanıcı hesabı OneDrive özel tutmanın bir parçası ise ve UPN'si değiştirilirse, tutma güncelleştirmeniz ve yeni URL'ye işaret OneDrive gerekir. Daha fazla bilgi için BKZ[. UPN değişiklikleri URL'nin OneDrive etkiler](/onedrive/upn-changes).

   1. **Exchange klasörleri açma** - Exchange Online ortak klasörlerin olduğu bir yere taşımak için iki durumlu düğmeyi Tüm konuma getirin. Belirli ortak klasörlerin 9'da 9'da 11'inin 11'ini seçesiniz. Ortak klasörlerde **basılı tutmak** istemiyorsanız iki durumlu düğmeyi Yok olarak bırakın.

9. İçerik konumlarını tik tutmaya eklemeyi bitirerek, Sonraki'ne **tıklayın**.
  
10. Koşullarla sorgu tabanlı bir tutma oluşturmak için, aşağıdaki adımları gerçekleştirin. Aksi takdirde, Yalnızca Sonraki'ne **tıklayın**.

    - Anahtar **Sözcükler'in altındaki** kutuya bir arama sorgusu yazın; böylelikle yalnızca arama ölçütlerine uyan içerikler orada tutun. Anahtar sözcükleri, ileti özelliklerini veya dosya adları gibi belge özelliklerini belirtebilirsiniz. Ayrıca, VE, YADA veya NOT gibi Boole işleci kullanan daha karmaşık sorgular da kullanabilirsiniz. Anahtar sözcük kutusunu boş bırakırsanız, belirtilen içerik konumlarında yer alan tüm içerikler basılı kalır.

    - Arama  **sorgusunu** basılı tutmak için bir veya daha fazla koşullar eklemek için Koşullar ekle'ye tıklayın. Her koşul, ayrı tutma oluşturulduğunda oluşturulan ve çalıştırılan KQL arama sorgusuna bir yan tümce ekler. Örneğin, tarih aralığı içinde oluşturulmuş e-posta veya site belgelerinin yerinde tutulacak şekilde bir tarih aralığı belirtebilirsiniz. Koşul, AND işleci tarafından anahtar sözcük sorgusuna (anahtar sözcük kutusunda belirtilen) mantıksal olarak bağlanır. Bu, öğelerin hem anahtar sözcük sorgusunu hem de yerine konan koşulu karşılaması gereken anlamına gelir.

     Arama sorgusu oluşturma ve koşulları kullanma hakkında daha fazla bilgi için bkz. [Anahtar sözcük sorguları ve İçerik Arama için arama koşulları](/office365/SecurityCompliance/keyword-queries-and-search-conditions).

11. Sorgu tabanlı bir tutma yapılandırdıktan sonra, Sonraki'ne **tıklayın**.

12. Ayarlarınızı gözden geçirin ve Bu tutma **oluştur'a tıklayın**.

> [!NOTE]
> Sorgu tabanlı bir tutma  oluştururken, seçilen konumlardan alınan tüm içerik başlangıçta basılı tutar. Daha sonra, belirtilen sorguyla eşleşmemiş olan içerik her yedi ile 14 günde bir temizlemeyi sağlar. Bununla birlikte, içerik yerine herhangi bir türde beşten fazla 0'dan fazla 10 000 000 000 0000 yer varsa veya herhangi bir öğede dizin oluşturma sorunları varsa, sorgu tabanlı tutma içeriği temizlemez.

> [!NOTE]
> Kullanıcının posta kutusunu yerinde bekledikten sonra kullanıcının SMTP adresi değişirse, posta kutusu yerinde kalır. Yerinde tutmak üzere yeni SMTP adresini kullanmak için, yeni bir yerinde tutma oluşturun.

## <a name="view-hold-statistics"></a>Tutma istatistiklerini görüntüleme

Bir süre sonra, seçilen tutma için 10 dakika bekleyin sekmesindeki ayrıntılar bölmesinde **yeni** tutma hakkında bilgiler görüntülenir. Bu bilgiler, durumdaki posta kutularının ve sitelerin sayısını ve basılı durumdaki öğelerin toplam sayısı ve boyutu ve tutma istatistiklerinin son hesaplanma zamanı gibi, basılı durumdaki içerikle ilgili istatistikleri içerir. Bu tutma istatistikleri, eBulma durumuyla ilgili ne kadar içeriğin tutulacaklarını tanımlamanıza yardımcı olur.

Tutma istatistikleri hakkında aşağıdaki bilgileri unutmayın:

- Tutmadaki toplam öğe sayısı, tüm içerik kaynaklarından alınan ve bir o kadar da tutuldu olan öğe sayısını gösterir. Sorgu tabanlı bir tutma oluşturduysanız, bu istatistiği sorguyla eşleşmesi için kaç öğe olduğunu gösterir.
  
- Aynı zamanda, içeriğin konumlarında bulunan, bağımsız olmayan öğeleri de içerir. Sorgu tabanlı bir tutma oluşturursanız, içerik konumlarına yerleştirilemeyen tüm öğeler basılı olarak yerleştirilir. Bu, sorgu tabanlı bir tutmanın arama ölçütleriyle eşleşmemiş, ya da tarih aralığı koşulunun dışında yer alan, ya da tek satırlık olmayan öğeleri içerir. Bu, arama sorgusuyla eşleşmemiş veya tarih aralığı koşulu tarafından dışlanan, dizisiz öğelerin arama sonuçlarına dahil alınmamış olduğu İçerik Arama'da yapılanlardan farklıdır. Dizine eksiz öğeler hakkında daha fazla bilgi için bkz. Dizine ek olarak yer alan İçerik Arama'da [kısmen Office 365](partially-indexed-items-in-content-search.md).

- Tutmadaki öğelerin geçerli sayısını hesapan bir arama tahminini yeniden aramak için İstatistikleri güncelleştir'e tıklayarak en son tutma istatistiklerini eldeebilirsiniz.

- Gerekirse, ayrıntılar bölmesindeki tutma istatistiklerini güncelleştirmek için araç çubuğundaki Yenile'ye tıklayın.

- Posta kutusu veya site yerindeki kullanıcılar genellikle yeni e-posta iletisi göndererek veya alırken yeni e-posta ve posta belgeleri gönderdiği için, zaman içinde SharePoint ve OneDrive İş olur.

- Çok SharePoint veya OneDrive hesabı çok coğrafi bir ortamda farklı bir bölgeye taşınırsa, bu sitenin istatistikleri tutma istatistiklerine dahil edilir. Bununla birlikte, sitenin içeriği yine yerinde basılı tutunacak. Ayrıca, site farklı bir bölgeye taşınırsa, yerinde aramada görüntülenen URL güncelleştirilmez. Güncelleştirmeyi düzenlemeniz ve URL'yi güncelleştirmeniz gerekir.

## <a name="place-a-hold-on-microsoft-teams-and-office-365-groups"></a>Grupların Microsoft Teams'Office 365 basılı tutun

Microsoft Teams Grupları'Office 365 yerleşiktir. Bu nedenle, bunları aynı şekilde Advanced eDiscovery yerleştirmek de benzer bir durum olur.

- **Ek bir Grup veya Microsoft 365 siteyi özel Microsoft Teams nasıl eşlerim? Grupların ve grupların özel olarak tutma Microsoft 365 ne Microsoft Teams?** Microsoft Teams Grupları'Microsoft 365 yerleşiktir. Bu nedenle, bunları eBulma durumunda tutmak benzer bir durum olur. Grupları yerleştirerek ve Microsoft 365 tutarken aşağıdaki Microsoft Teams unutmayın.

  - Microsoft 365 Grupları'nda bulunan içeriği Microsoft Teams için, bir grup veya ekiple ilişkilendirilmiş posta kutusunu SharePoint kutusunu ve posta kutusunu belirtmeniz gerekir.
  
  - Bir Grup veya Microsoft Ekibi'nin Exchange Online görüntülemek için Exchange Online Microsoft 365 **Get-UnifiedGroup** cmdlet'ini çalıştırın. Bu, bir Ekip Grubu veya Microsoft Ekibi ile ilişkilendirilmiş sitenin URL'sini Microsoft 365 iyi bir yol sağlar. Örneğin, aşağıdaki komut, Üst Düzey Liderlik Ekibi adlı bir Microsoft 365 özellikler görüntüler:

    ```console
    Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl
    DisplayName            : Senior Leadership Team
    Alias                  : seniorleadershipteam
    PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
    SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
    ```

    > [!NOTE]
    > Get-UnifiedGroup cmdlet'ini çalıştırmak için, Exchange Online'te View-Only Alıcıları rolüne atanmış bir rol grubunun üyesi View-Only gerekir.

  - Kullanıcının posta kutusunda arama geldiğinde, Microsoft 365 üyesi olduğu tüm Grup veya Microsoft Ekibi aranmaz. Benzer şekilde, bir Microsoft 365 Grubu veya Microsoft Team'i tutmanız için yalnızca grup posta kutusu ve grup sitesi yerinde tutma durumlarında olur; açıkça özel kişi olarak eklemedikçe veya veri kaynaklarını tutmadıkça grup üyelerinin posta kutuları ve OneDrive İş siteleri yerinde yerinde tutmaz. Bu nedenle, belirli bir custo ötelek için bir Microsoft 365 Grubu veya Microsoft Team'i yerinde tutmanız gerekirse, grup sitesini ve grup posta kutusunu custo custo ortaklarına eşlemeniz iyi olabilir (bkz. Advanced eDiscovery'te Özelkizçileri Yönetme). Özel Microsoft 365 Veya Microsoft Team tek bir özel tutma için attributable yoksa, kaynağı özel tutma için eklemeyi göz önünde bulundurabilir.
  - Bir Grup Grubu veya Microsoft Team Microsoft 365 üyelerinin listesini almak için,  >  özellikleri giriş sayfasındaki [**Ev Grupları Microsoft 365 yönetim merkezi**](https://go.microsoft.com/fwlink/p/?linkid=2052855). Alternatif olarak, Exchange Online PowerShell'de aşağıdaki Exchange Online çalıştırabilirsiniz:

    ```powershell
    Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
    ```

    > [!NOTE]
    > **Get-UnifiedGroupLinks** cmdlet'ini çalıştırmak için, Exchange Online'de View-Only Alıcıları rolüne atanmış bir rol grubuna ya da View-Only Alıcılar rolüne atanmış bir rol grubuna üye View-Only gerekir.

  - Bir kanalın parçası olan kanal Microsoft Teams görüşmeleri, Ekiple ilişkilendirilmiş olan posta kutusunda depolanır. Benzer şekilde, ekip üyelerinin bir kanalda paylaştığı dosyalar da ekibin SharePoint depolanır. Bu nedenle, bir kanalda konuşmaları ve dosyaları tutmak SharePoint Microsoft Team posta kutusunu ve posta kutusunu SharePoint sitesini yerinde tutmanız gerekir.
  
  - Alternatif olarak, sohbet listesinde yer alan Microsoft Teams konuşmalar sohbete katılan kullanıcının posta kutusunda depolanır.  Sohbet konuşmalarında bir kullanıcının paylaştığı dosyalar, dosyayı paylaşan OneDrive İş sohbet sitesinde depolanır. Bu nedenle, konuşmaları ve dosyaları Sohbet listesinde tutmak için OneDrive İş posta kutularını ve tüm siteyi ayrı ayrı tutmanız gerekir.
  
  - Her Microsoft Ekibi veya ekip kanalı not alma ve işbirliği için bir Wiki içerir. Wiki içeriği .mht biçimindeki bir dosyaya otomatik olarak kaydedilir. Bu dosya, ekibin Teams sitenin Wiki Verileri belge kitaplığında SharePoint depolanır. Wiki'nin içeriğini, ekibin web sitesini SharePoint yerleştirerek yerleştirebilirsiniz.

    > [!NOTE]
    > Microsoft Ekibi veya ekip kanalının Wiki içeriğini tutma özelliği (ekibin SharePoint sitesini yerinde tutma) 22 Haziran 2017'de yayınlanacak. Bir ekip sitesi yerinde basılı tutarsa Wiki içeriği, o tarihten itibaren korunur. Bununla birlikte, ekip sitesi yerinde kaldı ve Wiki içeriği 22 Haziran 2017'den önce silinmişse Wiki içeriği korunmdu.
