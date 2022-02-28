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
description: Yönetim merkezinde Merkezi Dağıtım'ı kullanarak kuruluşta kullanıcılara ve gruplara eklentileri dağıtmayı öğrenin.
ms.openlocfilehash: e9f5cb01394d947a6b44e1c34870d33b0d6dd9bd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984005"
---
# <a name="deploy-add-ins-in-the-admin-center"></a>Yönetim merkezinde eklentileri dağıtma

Office eklentileri belgelerinizi kişiselleştirmenize ve web'de bilgilere erişmenizi kolaylaştırmanıza yardımcı olur (bkz. Office [Eklentinizi kullanmaya başlama](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862)). Yönetici olarak, Office Merkezi Dağıtım özelliğini kullanarak Microsoft 365 yönetim merkezi kullanıcıları için dağıtım <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a>. Merkezi Dağıtım, çoğu yöneticinin kuruluş içindeki kullanıcılara ve gruplara eklenti dağıtması için önerilen ve özellik açısından en zengin yoldur.

Kuruluşun Merkezi Dağıtım'a destek olup olmadığını belirleme hakkında daha fazla bilgi için bkz. Merkezi Dağıtım eklentilerinin kuruluşu için [çalışır olup olmadığını belirleme](centralized-deployment-of-add-ins.md).

Dağıtımdan sonra eklentileri yönetme hakkında daha fazla bilgi edinmek için bkz. Yönetim [merkezinde eklentileri yönetme](manage-addins-in-the-admin-center.md)
  
> [!NOTE]
>  Word, Excel PowerPoint için, şirket içi ortamda [SharePoint](/office/dev/add-ins/publish/publish-task-pane-and-content-add-ins-to-an-add-in-catalog) bağlantısı olmayan ve/veya SharePoint eklentileri desteği olmayan kullanıcılara eklentiler dağıtmak için Microsoft 365 ve SharePoint kullanabilirsiniz. Örneğin Outlook Exchange bağlantısı olmayan bir şirket içi ortamda dağıtmak üzere Denetim Masası'nı Microsoft 365.
  
## <a name="recommended-approach-for-deploying-office-add-ins"></a>Office eklentilerini dağıtmak için önerilen yaklaşım

Eklentileri aşamalı bir yaklaşımla devrederek almak için, şunları öneririz:
  
1. Eklentiyi küçük bir işletme paydaşlarına ve IT departmanı üyelerine ekleyin. Dağıtım başarılı olursa, 2. adıma geçin.
    
2. Eklentiyi işletme içindeki daha fazla kişi için birlikte dışarıyın. Bir kez daha sonuçları değerlendirin ve başarılı olursa tam dağıtıma devam olun.
    
3. Tüm kullanıcılara tam bir uygulama uygulama.
    
Hedef kitlenin boyutuna bağlı olarak, dışarıyı çıkarma adımları ekleyebilir veya kaldırabilirsiniz.
  
## <a name="deploy-an-office-add-in-using-the-admin-center"></a>Yönetim Office kullanarak eklenti dağıtma

Başlamadan önce bkz [. Merkezi Dağıtım eklentilerinin kuruluşu için çalışır olup olmadığını belirleme](centralized-deployment-of-add-ins.md).
  
1. Yönetim merkezinde **Eklentiler Ayarlar** \> gidin. Eklenti Sayfası'nı **görmüyorsanız**,  \> Ayarlar **Tümleşik uygulamalar** \> **Eklentileri sayfasına** gidin.

2. Sayfanın **üst kısmında Eklentiyi** Dağıt'ı seçin ve sonra da Sonraki'yi **seçin**.

    > [!NOTE]
    > Ayrıca, Tümleşik Uygulamalar aracılığıyla yönetim merkezinden eklentiler [dağıtabilirsiniz](test-and-deploy-microsoft-365-apps.md). Tümleşik Uygulamalar Genel tarafından görülebilir ve Exchange görünür. Yukarıdaki adımları görmüyorsanız, Merkezi Dağıtım bölümüne gidip Entegrat **Ayarlar** >  **gidin**. Tümleşik uygulamalar sayfasının **üst kısmında** **Eklentiler'i seçin**.

3. Bir seçenek belirleyin ve yönergeleri izleyin.
  
4. Uygulama Mağazası'dan eklenti ekleme seçeneğini Office, eklentinizi seçin. </br>

    Kullanılabilir eklentileri kategorilere göre görüntüabilirsiniz: **Sizin için önerilen****, Derecelendirme** veya **Ad**. Office Store'dan yalnızca ücretsiz eklentiler kullanılabilir. Şu anda ücretli eklentiler desteklenmemektedir. Bir eklentiyi seçin ve devam etmek için hüküm ve koşulları kabul edin. <br/> 

    > [!NOTE]
    > Office Store seçeneğiyle, güncelleştirmeler ve iyileştirmeler kullanıcılara otomatik olarak dağıtılır.

5. Sonraki sayfada, **eklentinin kime** **dağıtılacağına belirtmek** için Herkes'i, Belirli kullanıcılar/gruplar'ı veya Yalnızca ben'i seçin. Belirli kullanıcıları veya grupları bulmak için Arama kutusunu kullanın. <br/>

    > [!NOTE]
    > Bir eklentiye uygulanacak diğer eyaletler hakkında bilgi edinmek için bkz [. Eklenti durumları](./manage-addins-in-the-admin-center.md).
  
6. **Dağıt'ı seçin**.
  
7. Eklenti dağıtıldığında yeşil bir onay işareti görünür. Eklentiyi test etmek için sayfa yönergelerini izleyin.

    > [!NOTE]
    > Kullanıcıların uygulama şeridinde eklenti Office için yeniden açmaları gerekiyor olabilir. Outlook eklentilerin uygulama şeritlerde görünmesi 24 saate kadar sürebilir.

8. Bitirdikten sonra, Sonraki'yi **seçin**. Yalnızca kendiniz için dağıtım yaptıysanız, daha fazla kullanıcıya dağıtmak  için Eklentiye kimlerin eriş erişe sahip olduğunu değiştir'i seçin.

    Eklentiyi kuruluşun diğer üyelerine dağıttıysanız, eklentinin dağıtımını duyurmak için yönergeleri izleyin. <br/>
  
    Kullanıcılara ve gruplara dağıtılan eklentinin kullanılabilir olduğunu bildirmek iyi bir yöntemdir. Eklentiyi ne zaman ve nasıl kullanabileceğinizi açıklayan bir e-posta gönderebilirsiniz. Kullanıcılar eklentiyle ilgili sorun paylaştıklarında onlara yardımcı olacak Yardım içeriğini veya SSS'leri ekleyin veya bağlantısını kullanın.
  
### <a name="considerations-when-assigning-an-add-in-to-users-and-groups"></a>Kullanıcılar ve gruplara eklenti atamayla ilgili önemli noktalar

Genel yöneticiler ve Exchange yöneticiler, herkese veya belirli kullanıcılara ve gruplara eklenti atayabilirsiniz. Her bir seçeneğin bir anlamı vardır:
  
- **Herkes** Bu seçenek, eklentiyi kuruluşta her kullanıcıya atar. Bu seçeneği kullanırken dikkatli olun ve yalnızca kuruluşunuz için gerçekten evrensel olan eklentiler için kullanın.

- **Kullanıcılar** Eklentiyi tek bir kullanıcıya atadığınız halde yeni bir kullanıcıya dağıtırsanız, önce yeni kullanıcıyı eklemeniz gerekir.

- **Gruplar** Bir gruba bir eklenti atarsanız, gruba eklenen kullanıcılara otomatik olarak eklenti atanır. Kullanıcı gruptan kaldırıldığı zaman, kullanıcı eklentiye erişimini kaybeder. Her iki durumda da yöneticiden ek işlem gerekmez.

- **Sadece ben** Eklentiyi yalnızca kendiniz için atarsanız, eklenti yalnızca hesabınıza atanır ve bu eklentiyi test etmek için idealdir.

Organizasyon için doğru seçenek yapılandırmanıza bağlıdır. Ancak, grupları kullanarak ödevler yapmanizi öneririz. Bir yönetici olarak, grupları kullanarak ve her sefer tek tek kullanıcılar atamak yerine bu grupların üyeliğini denetleyerek eklentileri yönetmeyi daha kolay bulabilirsiniz. Bazı durumlarda, kullanıcıları el ile ataarak belirli kullanıcılara atamalar yaparak küçük bir kullanıcı kümesine erişimi kısıtlamak gerekebilir.
  
## <a name="more-about-office-add-ins-security"></a>Eklentilerin Office hakkında daha fazla bilgi

Office eklentileri, eklenti hakkında meta veriler içeren XML bildirim dosyalarını birleştirir ve daha da önemlisi, tüm kodları ve mantıkları içeren bir web uygulamasına yönlendirir. Eklentiler, özellikleri açısından farklılık gösterebilir. Örneğin, şu işlemleri yapabilirler:
  
- Veri görüntüleme

- Bağlamsal hizmet sağlamak amacıyla bir kullanıcının belgesini okuma

- Kullanıcıya değer sağlamak amacıyla, kullanıcının belgesini okuma veya belgeye yazma

Office eklentilerinin özellikleri ve türleri hakkında daha fazla bilgi edinmek için [Office eklentileri platformuna genel bakış](/office/dev/add-ins/overview/office-add-ins) makalesine ve özellikle de "Office Eklentilerinin Anatomisi" bölümüne bakabilirsiniz.
  
Eklentilerin kullanıcının belgeleriyle etkileşim kurabilmesi için, ihtiyaç duyduğu izinleri bildirim kısmında belirtmesi gerekir. Beş düzeyli JavaScript API erişim-izinler modeli, görev bölmesi eklentilerini kullananların gizliliğini ve güvenliğini sağlar. Office Mağazası eklentilerinin çoğu, ReadWriteDocument seviyesindedir ve neredeyse tüm eklentiler en az ReadDocument düzeyini destekler. İzin düzeyleri hakkında daha fazla bilgi için bkz. [İçerikte API kullanımı ve görev bölmesi eklentileri için izin isteme](/office/dev/add-ins/develop/requesting-permissions-for-api-use-in-content-and-task-pane-add-ins).
  
Bildirim güncelleştirmeleri sırasında genellikle eklentinin simgesinde ve metninde değişiklik yapılır. Bazen eklenti komutları da değişebilir. Ancak eklenti izinleri değiştirilmez. Eklentiye dair tüm kod ve mantığın bulunduğu web uygulaması, tüm web uygulamalarında olduğu gibi, her an değişebilir.
  
Eklentilerin güncelleştirmeleri aşağıdaki gibi olur:
  
- **İş kolu eklentisi:** Yönetici karşıya açık olarak bir bildirim yüklediğinde, eklentinin meta veri değişikliklerini destekleyebilmesi için yeni bir bildirim dosyasının da yönetici tarafından karşıya yüklenmesi gerekir. İlgili Office uygulamalarını tekrar başlattığınızda eklenti güncelleştirilir. Web uygulaması her an değişebilir.

    > [!NOTE]
    > Yöneticinin güncelleştirme yapmak için LOB Eklentisini kaldırması gerekmemektedir.   Eklentiler bölümünde, Yönetici lob eklentisini tıklar ve sağ alt köşedeki Güncelleştir Düğmesini seçebilir. Güncelleştirmenin çalışması için, yeni eklentinin sürümü var olan eklentinin sürümünden daha büyük olduğu zaman çalışır.

- **Office Mağazası eklentisi:** Yönetici, Office Mağazası'ndan bir eklentiyi seçtiğinde Office Mağazası üzerinde bir eklenti güncelleştirmesi yapılıyorsa, seçilen eklenti daha sonra Merkezi Dağıtımda güncelleştirilir. İlgili Office uygulamalarını tekrar başlattığınızda eklenti güncelleştirilir. Web uygulaması her an değişebilir.
  
## <a name="related-content"></a>İlgili içerik

[Yönetim merkezinde eklentileri yönetme (makale](manage-addins-in-the-admin-center.md) )\
[İlk Word görev bölmesi eklentinizi oluşturma](/office/dev/add-ins/quickstarts/word-quickstart?tabs=yeomangenerator) (makale\
[Reşit olmayanlar ve mağazadan eklenti edinenler](minors-and-acquiring-addins-from-the-store.md) (makale)\
[Eklentileri yönetmek için Merkezi Dağıtım PowerShell cmdlet'lerini kullanma](../../enterprise/use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md) (makale)\
[Sorun giderme: Kullanıcı eklentileri görmüyor](/office365/troubleshoot/access-management/user-not-seeing-add-ins) (makale)
