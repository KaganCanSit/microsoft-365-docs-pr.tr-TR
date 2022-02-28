---
title: Kuruluşunuzdaki herkes için Odaklanmış Gelen Kutusu'nu yapılandırma
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
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
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 613a845c-4b71-41de-b331-acdcf5b6625d
description: Bir işletmede herkesin e-posta ayarlarını yapılandırmadan sorumluysanız, bu makalede kullanıcılar için Odaklanmış Gelen Kutusu'na nasıl yapılandırılan açıklanmıştır.
ms.openlocfilehash: b2c315b6fb4a4c80f245bcf4731b93996753586a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984706"
---
# <a name="configure-focused-inbox-for-everyone-in-your-organization"></a>Kuruluşunuzdaki herkes için Odaklanmış Gelen Kutusu'nu yapılandırma

İşletmede HERKES için e-postanın nasıl çalışacağını yapılandırmaktan sorumluysanız, bu makale tam size göre! İşletmeniz için nasıl özelleştirebileceğinizi veya kapatacaklarını açıklar ve sık [sorulan soruları yanıtlar](#faq-for-focused-inbox).

Odaklanmış Gelen Kutusu'nu yalnızca kendiniz için kapatmak istiyorsanız, bkz. [Odaklanmış Gelen Kutusu'nu kapatma](https://support.microsoft.com/office/f714d94d-9e63-4217-9ccb-6cb2986aa1b2).      

Kullanıcılarınızın işle ilgili, örneğin İK veya Muhasebe bölümünden gelen e-posta iletilerini aldığından emin olmak istiyorsanız Odaklanmış Gelen Kutusu'nu yapılandırarak böyle iletilerin Odaklanmış görünüme ulaşmasını sağlayabilirsiniz. Bunun yanı sıra, kuruluşunuzdaki kullanıcıların kendi posta kutularındaki Odaklanmış Gelen Kutusu'na bakıp bakmadıklarını da denetleyebilirsiniz.
  
## <a name="turn-focused-inbox-on-or-off-in-your-organization"></a>Kuruluşunuzda Odaklanmış Gelen Kutusu'nu açma veya kapatma

Kuruluşunuzda herkes için Odaklanmış Gelen Kutusu'nu açma veya kapatma işlemini PowerShell kullanarak yaparsınız. Bunu en son ne zaman yapmak Microsoft 365 yönetim merkezi? Bunu Mühendislik ekibimize iletin. **[Buradan oylayın!](https://go.microsoft.com/fwlink/?linkid=862489)**
  
**Odaklanmış Gelen Kutusu'nu kapatmak için:**
  
Aşağıdaki PowerShell örneği, kuruluşunuzda Odaklanmış Gelen Kutusu'nu **Kapalı** duruma getirir. Ancak, kullanıcılarınıza sağlanan özelliklerin kullanılabilmesini engellemez. İsterlerse, istemcilerinin her biri için Odaklanmış Gelen Kutusu'nu yeniden etkinleştirebilirler. 
  
1. [Bağlan PowerShell Exchange Online'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. Bu yordamı veya yordamları gerçekleştirebilmeniz için, önce izinlerin atanması gerekir. Size hangi izinlerin gerektiğini görmek için, [Mesajlaşma ilkesi ve uyumluluk izinleri](/exchange/messaging-policy-and-compliance-permissions-exchange-2013-help) konusunda yer alan "Aktarım kuralları" girdisine bakın.

3. **Get-OrganizationConfig** cmdlet'ini çalıştırın. 

    ```powershell
    Get-OrganizationConfig
    ```

4. Geçerli ayarı görmek için **FocusedInboxOn** öğesini bulun: 

    ![Response from PowerShell on state of Focused Inbox.](../../media/419d8caa-89b9-45c5-91d9-8c023297456e.png)
  
5. Odaklanmış Gelen Kutusu'nu kapatmak için aşağıdaki cmdlet'i çalıştırın.

    ```powershell
    Set-OrganizationConfig -FocusedInboxOn $false
    ```

6. **Get-OrganizationConfig** cmdlet'ini çalıştırın; FocusedInboxOn değerinin $false olarak ayarlandığını görürsünüz ve bu da kapatıldığı anlamına gelir. 

**Odaklanmış Gelen Kutusu'nu açmak için:**
  
- Yukarıdaki 5. Adımda, Odaklanmış Gelen Kutusu'nu açmak için aşağıdaki cmdlet'i çalıştırın.

  ```powershell
  Set-OrganizationConfig -FocusedInboxOn $true
  ```
    
## <a name="what-do-users-see-after-i-turn-on-focused-inbox"></a>Ben Odaklanmış Gelen Kutusu'nu açtıktan sonra kullanıcılar ne görüyor?

Kullanıcılarınız ancak Outlook'u kapatıp yeniden başlattıktan sonra Odaklanmış görünümü görebilirler. Outlook'u yeniden başlattıklarında, Outlook kullanıcı arabiriminde onlara yeni Odaklanmış Gelen Kutusu'nu kullanma seçeneği sağlayan bir İpucu görürler.
  
![An image of what Focused Inbox looks like when a user first opens Outlook on the web.](../../media/f6ef79e7-0f4c-4a23-b6f0-7c15d927b5f0.png)
  
İkincil'den Odaklanmış Gelen Kutusu'na geçiş yapıyorsanız kullanıcılarınız, özelliği etkinleştirmeyi ("Dene") veya kapatmayı tercih edebilir. Kullanıcının çok sayıda (desteklenen) istemcisi varsa her birinde Odaklanmış Gelen Kutusu'nu ayrı olarak etkinleştirebilir/devre dışı bırakabilir. İpucu şöyle görünür:
  
![An image of what Focused Inbox looks like when it's rolled out to your users and Outlook is re-opened.](../../media/c034f969-d650-4333-88f1-dd10ade0a94c.png)
  
Kullanıcı, Odaklanmış Gelen Kutusu'nu kullanmaya karar verdiğinde İkincil özelliği otomatik olarak devre dışı kalır. İkincil klasörü, kullanıcının yeniden adlandırabileceği veya silebileceği standart bir klasöre dönüşür.
  
## <a name="turn-focused-inbox-on-or-off-for-specific-users"></a>Odaklanmış Gelen Kutusu'nu belirli kullanıcılar için açma ve kapatma

Bu örnek, Contoso kuruluşundaki Fatih Kara için Odaklanmış Gelen Kutusunu **Kapalı** olarak ayarlar. Ancak bu kişiye sağlanan özelliklerin kullanılabilmesini engellemez. Isterse, istemcilerinin her biri için Odaklanmış Gelen Kutusu'na yeniden etkinleştirebilirsiniz. 
  
1. [Bağlan PowerShell Exchange Online'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. Bu yordamı veya yordamları gerçekleştirebilmeniz için, önce izinlerin atanması gerekir. Size hangi izinlerin gerektiğini görmek için, Mesajlaşma ilkesi ve uyumluluk izinleri konusunda yer alan "Aktarım kuralları" girişine bakın.

3. **Get-FocusedInbox** cmdlet'ini çalıştırın; örneğin: 

    ```powershell
    Get-FocusedInbox -Identity <tim@contoso.com>
    ```

4. Geçerli ayarı görmek için FocusedInboxOn öğesini bulun:

    ![Response from PowerShell on state of Focused Inbox.](../../media/419d8caa-89b9-45c5-91d9-8c023297456e.png)
  
5. Odaklanmış Gelen Kutusu'na kapatmak için aşağıdaki cmdlet'i çalıştırın:

    ```powershell
    Set-FocusedInbox -Identity <tim@contoso.com> -FocusedInboxOn $false
    ```

    VEYA, açmak için aşağıdaki cmdlet'i çalıştırın:

    ```powershell
    Set-FocusedInbox -Identity <tim@contoso.com> -FocusedInboxOn $true
    ```

## <a name="use-the-ui-to-create-a-transport-rule-to-direct-email-messages-to-the-focused-view-for-all-your-users"></a>Tüm kullanıcılarınızın e-posta iletilerini Odaklanmış görünüme yönlendirecek aktarım kuralını oluşturmak için kullanıcı arabirimini kullanma

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezine</a> gidin.

2. Posta akışı **Kuralları'nına** \> **gidin**. ![EAC Ekle simgesi'ne tıklayın.](../../media/795e5bdd-48bb-433f-8e07-3c7a19f8eca2.gif) ve ardından Yeni **kural oluştur... öğesini seçin**. 

3. Yeni kuralı oluşturmayı bitirdikten sonra, kuralı başlatmak **için Kaydet'i** seçin.

    Aşağıdaki resimde , "Bordro Bölümü" gelen tüm iletilerin Odaklanmış Gelen Kutusu'na teslim edilecek olduğu bir örnek gösterilir.

    ![focusedinbox payroll'i seçin.](../../media/focusedinbox-transport-rule.PNG)

    > [!NOTE]
    > Bu örnekteki ileti üstbilgisi değeri **X-MS-Exchange-Organization-BypassFocusedInbox'tır**.
  
## <a name="use-powershell-to-create-a-transport-rule-to-direct-email-messages-to-the-focused-view-for-all-your-users"></a>Tüm kullanıcılarınızın e-posta iletilerini Odaklanmış görünüme yönlendirecek aktarım kuralını oluşturmak için PowerShell kullanma

1. [Bağlan PowerShell Exchange Online'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. Bu yordamı veya yordamları gerçekleştirebilmeniz için, önce izinlerin atanması gerekir. Size hangi izinlerin gerektiğini görmek için, [Mesajlaşma ilkesi ve uyumluluk izinleri](/exchange/messaging-policy-and-compliance-permissions-exchange-2013-help) konusunda yer alan "Aktarım kuralları" girdisine bakın.

3. "Bordro Bölümü" örneğinden gelen tüm iletilerin Odaklanmış Gelen Kutusu'na teslim  olmasına izin vermek için aşağıdaki komutu çalıştırın.

    ```powershell
    New-TransportRule -Name <name_of_the_rule> -From "Payroll Department" -SetHeaderName "X-MS-Exchange-Organization-BypassFocusedInbox" -SetHeaderValue "true"
    ```

> [!IMPORTANT]
> Bu örnekte, hem "X-MS-Exchange-Organization-BypassFocusedInbox" hem de "true" büyük/küçük harfe duyarlıdır.
> Ayrıca, Odaklanmış Gelen Kutusu İkincil özelliğini atlayan X üstbilgisinde de uygun olur, dolayısıyla bu ayarı İkincil'de kullanırsanız Odaklanmış Gelen Kutusu'da kullanılacaktır. Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-TransportRule](/powershell/module/exchange/new-transportrule).

### <a name="how-do-you-know-this-worked"></a>Bunun çalıştığını nasıl anlarsınız?

E-posta iletilerinin Odaklanmış Gelen Kutusu aktarım kuralını atlaması nedeniyle Gelen Kutusuna ulaşıp ulaşmadığını görmek için e-posta iletisi üst bilgilerini denetleyebilirsiniz. Kuruluşunuzda, Odaklanmış Gelen Kutusu aktarım kuralının uygulandığı posta kutusundan bir e-posta iletisi seçin. İletide yazılı üst bilgilere bakın; **X-MS-Exchange-Organization-BypassFocusedInbox: true** üst bilgisini görmeniz gerekir. Bu atlama işleminin çalıştığı anlamına gelir. Üst bilgileri [bulma hakkında bilgi için, E-posta iletisi için](https://go.microsoft.com/fwlink/p/?LinkId=822530) İnternet üst bilgilerini görüntüleme makalesine bakın.

### <a name="what-will-the-user-see"></a>Kullanıcı neleri görebilir?

Aktarım kuralı varsa, geçersiz kılma için bir bildirim gösterilir. Web üzerinde Outlook, "Her zaman Diğer'e Taşı" seçeneği devre dışı bırakarak bir araç ipucu gösterir. Outlook istemcilerde "Her zaman Diğer'e geç" seçimine izin ve bir iletişim kutusu açılır.

## <a name="turn-onoff-clutter"></a>İkincil özelliğini açma/kapatma

İkincil özelliğinin bazı kullanıcılarda aniden çalışmayı durdurduğunu bildiren raporlar aldık. Böyle bir durumla karşılaşırsanız, bu özelliği belli kullanıcılar için yeniden etkinleştirebilirsiniz. Bkz. [Kuruluşunuz için İkincil özelliğini yapılandırma](../email/configure-clutter.md).

## <a name="faq-for-focused-inbox"></a>Odaklanmış Gelen Kutusu hakkında SSS

Burada, Odaklanmış Gelen Kutusu hakkında Sık Sorulan Soruların yanıtları verilmiştir.

### <a name="can-i-control-how-i-roll-out-focused-inbox-in-my-organization"></a>Odaklanmış Gelen Kutusu'nun kuruluşumda nasıl dağıtılacağını denetleyebilir miyim?

Evet. Odaklanmış Gelen Kutusu'nu kuruluşun tamamı için açıp kapatabileceğiniz gibi, belirli kullanıcılar için de açıp kapatabilirsiniz. Yukarıya bakınız.
  
### <a name="is-the-focused-inbox-feature-only-available-for-office-2016-clients"></a>Odaklanmış Gelen Kutusu özelliği YALNIZCA Office 2016 istemcilerinde mi kullanılabilir?

Evet, bu özellik yalnızca Office 2016 kullanıcılarına sunulur; Outlook 2013 ve önceki sürümlere taşınmaz.
  
### <a name="how-long-does-it-take-for-focused-inbox-changes-to-take-place-in-outlook"></a>Odaklanmış Gelen Kutusu değişikliklerinin Outlook'ta geçerlilik kazanması ne kadar sürer?

Odaklanmış Gelen Kutusu'nu açtıktan veya kapattıktan sonra, ayarların geçerlilik kazanması için kullanıcılar Outlook'u kapatıp yeniden başlatması gerekir.
  
### <a name="what-happens-to-clutter-once-i-turn-on-focused-inbox"></a>Odaklanmış Gelen Kutusu'nu açtıktan sonra İkincil klasörüne ne olur?

Geçiş yaptıktan sonra eyleme dönüştürme olasılığı daha düşük olan e-postalar İkincil klasörünüze gelmez. Bunun yerine, e-postalar, gelen kutunuzda Odaklanmış ve Diğer sekmeleri arasında bölünür. Öğeleri İkincil klasörüne taşırken kullanılan algoritma, artık Odaklanmış Gelen Kutusu'nda kullanılır, yani İkincil'e taşınmak üzere ayarlanmış tüm e-postalar artık Diğer sekmesine taşınır. İkincil klasöründe bulunan tüm iletiler, siz onları silmeye veya taşımaya karar verene kadar orada kalır.
  
Microsoft MVP'si [Tony Redmond](https://www.petri.com/author/tony-redmond)'ın şu gönderisini gözden geçirin: [Office 365'te Odaklanmış Gelen Kutusu Nasıl İkincil Klasörünün Yerini Alır](https://www.petri.com/focused-inbox-office-365).
  
### <a name="can-i-keep-users-on-clutter-what-is-microsofts-recommendation-when-it-comes-to-using-clutter-vs-focused-inbox"></a>Kullanıcıları İkincil'de tutabilir miyim? Odaklanmış Gelen Kutusu yerine İkincil kullanılması konusunda Microsoft'un önerisi nedir?

Evet, kullanıcıları İkincil'de tutup Odaklanmış Gelen Kutusu'nu devre dışı bırakabilirsiniz; ancak, sonunda Odaklanmış Gelen Kutusu tamamen İkincil'in yerini alacaktır. Dolayısıyla, Microsoft şimdi Odaklanmış Gelen Kutusu'na geçmenizi önerir. Exchange Online ile İkincil'i ne zaman kullanacağınız hakkında daha fazla bilgi edinmek için şu blog gönderisine bakın: [Odaklanmış Gelen Kutusu güncelleştirmesi ve İkincil ile ilgili planlarımız](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448).
  
### <a name="should-i-disable-clutter-for-my-end-users-if-we-are-going-to-move-everyone-to-focused-inbox"></a>Herkesi Odaklanmış Gelen Kutusu'na geçireceksek son kullanıcılarım için İkincil'i devre dışı bırakabilir miyim?

Hayır. Set-Clutter cmdlet'i çalıştırarak bir posta kutusu için İkincil'i devre dışı bırakmak mümkündür. Bununla birlikte, bunu yaparsanız posta kutusu sahibi daha önce İkincil klasörüne yönlendirilmiş iletilerin Gelen Kutusu'nda kaldığını görür ve istemcisi Odaklanmış Gelen Kutusu'nu destekleyen bir sürümü yükseltilene kadar söz konusu iletileri işlemek zorunda kalır. Dolayısıyla, en iyisi yükseltilmiş istemciler sağlanana kadar İkincil'i devre dışı bırakmamaktır.
  
### <a name="why-are-there-two-different-cmdlets-for-managing-focused-inbox"></a>Odaklanmış Gelen Kutusu'nu yönetmek için neden iki farklı cmdlet var?

Odaklanmış Gelen Kutusu'yla ilişkili iki durum vardır.
  
- **Kuruluş Düzeyi**: Odaklanmış Gelen Kutusu durumu ve ilişkilendirilmiş bir son güncelleştirme zaman damgası.

- **Posta Kutusu Düzeyi**: Odaklanmış Gelen Kutusu durumu ve ilişkilendirilmiş bir son güncelleştirme zaman damgası 

### <a name="how-does-outlook-decide-to-show-the-focused-inbox-experience-with-these-two-states"></a>Outlook, Odaklanmış Gelen Kutusu deneyimini bu iki durum bilgisinden hangisiyle göstereceğine nasıl karar verir?

Outlook, deneyime karar verirken hangi cmdlet'in en son zaman damgasına sahip olduğuna bakar. Varsayılan olarak, her iki zaman damgası da "null" değere sahiptir ve bu durumda özellik devre dışı bırakılır.
  
### <a name="why-does-the-get-focusedinbox-cmdlet-return-true-when-ive-turned-focused-inbox-off-in-my-organization"></a>Kuruluşumda Odaklanmış Gelen Kutusu'nu kapattığımda Get-FocusedInbox cmdlet'i neden "true" döndürüyor?

Odaklanmış Gelen Kutusu'nu denetlemek için iki cmdlet vardır. Posta kutusu için Get-FocusedInbox'ı çalıştırdığınızda, bu cmdlet özelliğin posta kutusu düzeyi durumunu döndürür. Outlook'taki deneyim, hangi cmdlet durumunun en son değiştirildiğine bağlı olarak seçilir.
  
### <a name="can-i-run-a-script-to-see-who-has-turned-on-focused-inbox"></a>Odaklanmış Gelen Kutusu'nu etkinleştiren kişileri görmek için bir betik çalıştırabilir miyim?

Hayır ve bu tasarımdandır. Odaklanmış Gelen Kutusu'nun etkinleştirmesi bir istemci tarafı ayarıdır, bu nedenle cmdlet'in tüm yaprı, kullanıcının posta kutusunun istemci deneyimine uygun olup olduğunu söylemektir. Örneğin, Outlook uygulamasında ve Outlook Mobile'da etkinken, bazı istemcilerde aynı anda etkinleştirilebilir ve bazı istemcilerde devre dışı Web üzerinde Outlook.

## <a name="related-content"></a>İlgili içerik

[Organizasyonu için karışık e-postayı yapılandırma](../email/configure-clutter.md) (makale)\
[Paylaşılan posta kutusu ayarlarını yapılandırma](../email/configure-a-shared-mailbox.md) (makale)\
[İmzalar ve sorumluluklar oluşturma](create-signatures-and-disclaimers.md) (video)
