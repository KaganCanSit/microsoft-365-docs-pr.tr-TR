---
title: Yönetim merkezinde eklentileri dağıtma
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
- Adm_NonTOC
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Yönetim merkezindeki Merkezi Dağıtım'ı kullanarak kuruluşunuzdaki kullanıcılara ve gruplara eklenti dağıtmayı öğrenin.
ms.openlocfilehash: 2dfd92e2dd38487a444362cdbb88ec217e62ca28
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093734"
---
# <a name="deploy-add-ins-in-the-admin-center"></a>Yönetim merkezinde eklentileri dağıtma

Office Eklentileri, belgelerinizi kişiselleştirmenize ve web'deki bilgilere erişme şeklinizi kolaylaştırmanıza yardımcı olur (bkz. [Office Eklentinizi kullanmaya başlama](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862)). Yönetici olarak, Microsoft 365 yönetim merkezi Merkezi Dağıtım özelliğini kullanarak kuruluşunuzdaki kullanıcılar için <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Office</a> Eklentileri dağıtabilirsiniz. Merkezi Dağıtım, çoğu yöneticinin bir kuruluştaki kullanıcılara ve gruplara eklenti dağıtması için önerilen ve özellik açısından zengin bir yoldur.

Kuruluşunuzun Merkezi Dağıtım'ı destekleyip destekleyemediğini belirleme hakkında daha fazla bilgi için bkz. [Eklentilerin Merkezi Dağıtımının kuruluşunuzda çalışıp çalışmadığını belirleme](centralized-deployment-of-add-ins.md).

Dağıtımdan sonra eklentileri yönetme hakkında daha fazla bilgi edinmek için bkz. [Yönetim merkezinde eklentileri yönetme](manage-addins-in-the-admin-center.md)
  
> [!NOTE]
>  Word için, Excel ve PowerPoint, Microsoft 365 bağlantısı ve/veya SharePoint eklentileri için destek gerekmeyen şirket içi bir ortamdaki kullanıcılara eklenti dağıtmak için SharePoint [Uygulama Kataloğu](/office/dev/add-ins/publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog) kullanır. Outlook için Microsoft 365 bağlantısı olmadan şirket içi bir ortamda dağıtmak üzere Exchange denetim masası kullanın.
  
## <a name="recommended-approach-for-deploying-office-add-ins"></a>Office Eklentileri dağıtmak için önerilen yaklaşım

Aşamalı bir yaklaşım kullanarak eklentilerin dağıtımını yapmak için aşağıdakileri öneririz:
  
1. Eklentiyi küçük bir iş paydaşları kümesine ve BT departmanının üyelerine dağıtın. Dağıtım başarılı olursa 2. adıma geçin.
    
2. Eklentiyi işletmedeki daha fazla kişiye dağıtın. Yine sonuçları değerlendirin ve başarılı olursa tam dağıtıma devam edin.
    
3. Tüm kullanıcılar için tam dağıtım gerçekleştirin.
    
Hedef kitlenin boyutuna bağlı olarak, dağıtım adımları ekleyebilir veya kaldırabilirsiniz.
  
## <a name="deploy-an-office-add-in-using-the-admin-center"></a>Yönetim merkezini kullanarak Office Eklentisi dağıtma

Başlamadan önce bkz. [Eklentilerin Merkezi Dağıtımının kuruluşunuz için çalışıp çalışmadığını belirleme](centralized-deployment-of-add-ins.md).
  
1. Yönetim merkezinde **, Ayarlar** \> **Eklentiler** sayfasına gidin. **Eklenti Sayfası'nı** görmüyorsanız tümleşik **uygulamalar** \> **Ayarlar Eklentiler** sayfasına gidin  \>.

2. Sayfanın üst kısmındaki **Eklentiyi Dağıt'ı** ve ardından **İleri'yi** seçin.

    > [!NOTE]
    > Tümleşik [Uygulamalar](test-and-deploy-microsoft-365-apps.md) aracılığıyla yönetim merkezinde eklentileri de dağıtabilirsiniz. Tümleşik Uygulamalar Genel ve Exchange yöneticileri tarafından görülebilir. Yukarıdaki adımları görmüyorsanız, **Ayarlar** >  **Yenileştirilmiş uygulamalar'a** giderek Merkezi Dağıtım bölümüne gidin. **Tümleşik uygulamalar** sayfasının üst kısmında **Eklentiler'i** seçin.

3. Bir seçenek belirleyin ve yönergeleri izleyin.
  
4. Office Store'dan eklenti ekleme seçeneğini belirlediyseniz, eklenti seçiminizi yapın. </br>

    Kullanılabilir eklentileri kategorilere göre görüntüleyebilirsiniz: **Sizin için önerilen**, **Derecelendirme** veya **Ad**. Office Store'dan yalnızca ücretsiz eklentiler kullanılabilir. Şu anda ücretli eklentiler desteklenmemektedir. Bir eklentiyi seçtikten sonra devam etmek için hüküm ve koşulları kabul edin. <br/> 

    > [!NOTE]
    > Office Store seçeneğiyle güncelleştirmeler ve geliştirmeler kullanıcılara otomatik olarak dağıtılır.

5. Sonraki sayfada, eklentinin kime dağıtılacağını belirtmek için **Herkes**, **Belirli kullanıcılar/gruplar** veya **Yalnızca ben'i** seçin. Belirli kullanıcıları veya grupları bulmak için Arama kutusunu kullanın. <br/>

    > [!NOTE]
    > Eklenti için geçerli olan diğer durumlar hakkında bilgi edinmek için bkz. [Eklenti durumları](./manage-addins-in-the-admin-center.md).
  
6. **Dağıt'ı** seçin.
  
7. Eklenti dağıtıldığında yeşil bir onay işareti görünür. Eklentiyi test etmek için sayfadaki yönergeleri izleyin.

    > [!NOTE]
    > Kullanıcıların uygulama şeridindeki eklenti simgesini görüntülemek için Office yeniden başlatmış olması gerekebilir. Outlook eklentilerin uygulama şeritlerinde görünmesi 24 saat kadar sürebilir.

8. İşiniz bittiğinde **İleri'yi** seçin. Yalnızca kendinize dağıttıysanız, daha fazla kullanıcıya dağıtmak **için Eklentiye kimlerin erişimi olduğunu değiştir'i** seçebilirsiniz.

    Eklentiyi kuruluşunuzun diğer üyelerine dağıttıysanız, eklentinin dağıtımını duyurmak için yönergeleri izleyin. <br/>
  
    Kullanıcılara ve gruplara dağıtılan eklentinin kullanılabilir olduğunu bildirmek iyi bir uygulamadır. Eklentinin ne zaman ve nasıl kullanılacağını açıklayan bir e-posta göndermeyi göz önünde bulundurun. Kullanıcıların eklentiyle ilgili sorunları varsa yardımcı olabilecek Yardım içeriğini veya SSS'leri ekleyin veya bu içeriğe bağlantı sağlayın.
  
### <a name="considerations-when-assigning-an-add-in-to-users-and-groups"></a>Kullanıcılar ve gruplara eklenti atamayla ilgili önemli noktalar

Genel yöneticiler ve Exchange yöneticileri herkese veya belirli kullanıcılara ve gruplara bir eklenti atayabilir. Her bir seçeneğin bir anlamı vardır:
  
- **Herkes** Bu seçenek, eklentiyi kuruluştaki her kullanıcıya atar. Bu seçeneği kullanırken dikkatli olun ve yalnızca kuruluşunuz için gerçekten evrensel olan eklentiler için kullanın.

- **Kullanıcı** Bir eklentiyi tek bir kullanıcıya atar ve sonra eklentiyi yeni bir kullanıcıya dağıtırsanız, önce yeni kullanıcıyı eklemeniz gerekir.

- **Grup** Bir gruba eklenti atarsanız, gruba eklenen kullanıcılara otomatik olarak eklenti atanır. Bir kullanıcı gruptan kaldırıldığında, kullanıcı eklentiye erişimi kaybeder. Her iki durumda da yöneticiden ek işlem yapılması gerekmez.

- **Sadece ben** Eklentiyi yalnızca kendinize atarsanız, eklenti yalnızca hesabınıza atanır ve bu da eklentiyi test etmek için idealdir.

Kuruluşunuz için doğru seçenek yapılandırmanıza bağlıdır. Ancak, grupları kullanarak atamalar yapmanızı öneririz. Yönetici olarak, her seferinde tek tek kullanıcılar atamak yerine grupları kullanarak ve bu grupların üyeliğini denetleyerek eklentileri yönetmeyi daha kolay bulabilirsiniz. Bazı durumlarda, kullanıcıları el ile atayarak belirli kullanıcılara atamalar yaparak küçük bir kullanıcı kümesine erişimi kısıtlamak isteyebilirsiniz.
  
## <a name="more-about-office-add-ins-security"></a>Office Eklentilerin güvenliği hakkında daha fazla bilgi

Office Eklentileri, eklentiyle ilgili bazı meta verileri içeren bir XML bildirim dosyasını birleştirir, ancak en önemlisi tüm kodu ve mantığı içeren bir web uygulamasına işaret eder. Eklentiler, özellikleri açısından farklılık gösterebilir. Örneğin, şu işlemleri yapabilirler:
  
- Veri görüntüleme

- Bağlamsal hizmet sağlamak amacıyla bir kullanıcının belgesini okuma

- Kullanıcıya değer sağlamak amacıyla, kullanıcının belgesini okuma veya belgeye yazma

Office Eklentilerin türleri ve özellikleri hakkında daha fazla bilgi için, özellikle de "Office Eklentisinin Anatomisi" bölümü Office [Eklentiler platformuna genel bakış](/office/dev/add-ins/overview/office-add-ins) bölümüne bakın.
  
Eklentilerin kullanıcının belgeleriyle etkileşim kurabilmesi için, ihtiyaç duyduğu izinleri bildirim kısmında belirtmesi gerekir. Beş düzeyli JavaScript API erişim-izinler modeli, görev bölmesi eklentilerini kullananların gizliliğini ve güvenliğini sağlar. Office Mağazası eklentilerinin çoğu, ReadWriteDocument seviyesindedir ve neredeyse tüm eklentiler en az ReadDocument düzeyini destekler. İzin düzeyleri hakkında daha fazla bilgi için bkz. [İçerikte API kullanımı ve görev bölmesi eklentileri için izin isteme](/office/dev/add-ins/develop/requesting-permissions-for-api-use-in-content-and-task-pane-add-ins).
  
Bildirim güncelleştirmeleri sırasında genellikle eklentinin simgesinde ve metninde değişiklik yapılır. Bazen eklenti komutları da değişebilir. Ancak eklenti izinleri değiştirilmez. Eklentiye dair tüm kod ve mantığın bulunduğu web uygulaması, tüm web uygulamalarında olduğu gibi, her an değişebilir.
  
Eklentilerin güncelleştirmeleri aşağıdaki gibi olur:
  
- **İş kolu eklentisi:** Yönetici karşıya açık olarak bir bildirim yüklediğinde, eklentinin meta veri değişikliklerini destekleyebilmesi için yeni bir bildirim dosyasının da yönetici tarafından karşıya yüklenmesi gerekir. İlgili Office uygulamalarını tekrar başlattığınızda eklenti güncelleştirilir. Web uygulaması her an değişebilir.

    > [!NOTE]
    > Yöneticinin güncelleştirme yapmak için lob eklentisini kaldırması gerekmez.   Eklentiler bölümünde Yönetici, LOB Eklentisi'ne tıklayıp sağ alt köşedeki **Güncelleştir Düğmesi'ni** seçebilir. Güncelleştirme yalnızca yeni eklentinin sürümü mevcut eklentiden daha büyükse çalışır.

- **Office Mağazası eklentisi:** Yönetici, Office Mağazası'ndan bir eklentiyi seçtiğinde Office Mağazası üzerinde bir eklenti güncelleştirmesi yapılıyorsa, seçilen eklenti daha sonra Merkezi Dağıtımda güncelleştirilir. İlgili Office uygulamalarını tekrar başlattığınızda eklenti güncelleştirilir. Web uygulaması her an değişebilir.
  
## <a name="related-content"></a>İlgili içerik

[Yönetim merkezinde eklentileri yönetme](manage-addins-in-the-admin-center.md) (makale)\
[İlk Word görev bölmesi eklentinizi oluşturma](/office/dev/add-ins/quickstarts/word-quickstart?tabs=yeomangenerator) (makale\
[Reşit olmayanlar ve mağazadan eklentiler alma](minors-and-acquiring-addins-from-the-store.md) (makale)\
[Eklentileri yönetmek için Merkezi Dağıtım PowerShell cmdlet'lerini kullanma](../../enterprise/use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md) (makale)\
[Sorun giderme: Kullanıcı eklentileri göremiyor](/office365/troubleshoot/access-management/user-not-seeing-add-ins) (makale)
