---
title: Microsoft Purview'da eBulma (Standart) durumlarıyla Kullanmaya başlayın
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Microsoft Purview'da eKeşif (Standart) kullanmaya başlamayı açıklar. eBulma izinlerini atadıktan ve bir servis talebi oluşturduktan sonra, üyeleri ekleyebilir, eBulma tutmaları oluşturabilir ve ardından araştırmanızla ilgili içeriği arayabilir ve dışarı aktarabilirsiniz.
ms.openlocfilehash: bf49ebd886a85005166f07b1a3d6c97e10412e20
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64934741"
---
# <a name="get-started-with-ediscovery-standard-in-microsoft-purview"></a>Microsoft Purview'da eBulma (Standart) ile Kullanmaya başlayın

Microsoft Purview'daki Microsoft Purview eKeşif (Standart), kuruluşların Microsoft 365 ve Office 365 içeriği aramak ve dışarı aktarmak için kullanabileceği temel bir eBulma aracı sağlar. eBulma (Standart) özelliğini, Exchange posta kutuları, SharePoint siteleri, OneDrive hesapları ve Microsoft Teams gibi içerik konumlarına eBulma bekletmesi yapmak için de kullanabilirsiniz. eKeşif 'i (Standart) dağıtmak için hiçbir şey gerekmez, ancak kuruluşunuzun içeriği aramak, dışarı aktarmak ve korumak için eKeşif 'i (Standart) kullanmaya başlayabilmesi için bt yöneticisinin ve eBulma yöneticisinin tamamlaması gereken bazı önkoşul görevleri vardır.

Bu makalede, eBulma'yı (Standart) ayarlamak için gereken adımlar ele alınmaktadır. Bu, eBulma'ya (Standart) erişmek ve içerik konumlarına eBulma bekletmek için gereken uygun lisanslamanın yanı sıra bt, yasal ve araştırma ekibinize olaylara erişebilmeleri ve bunları yönetebilmeleri için izinler atamayı içerir. Bu makalede ayrıca içeriği aramak ve dışarı aktarmak için kullanım örneklerine üst düzey bir genel bakış sağlanır.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>1. Adım: Uygun lisansları doğrulama ve atama

eBulma için lisanslama (Standart) için uygun kuruluş aboneliği ve kullanıcı başına lisanslama gerekir.

- **Kuruluş aboneliği:** Microsoft Purview uyumluluk portalında eBulma 'ya (Standart) erişmek ve ayrı tutma ve dışarı aktarma özelliklerini kullanmak için kuruluşunuzun bir Microsoft 365 E3 veya Office 365 E3 aboneliği veya üzeri olması gerekir. Microsoft 365 Frontline kuruluşlarının F5 aboneliği olmalıdır.

- **Kullanıcı başına lisanslama:** Posta kutularına ve sitelere eBulma ayrılığı yerleştirmek için, kuruluş aboneliğinize bağlı olarak kullanıcılara aşağıdaki lisanslardan birinin atanması gerekir:

  - Microsoft 365 E3 veya Office 365 E3 lisansı veya üzeri

   VEYA

  - Exchange Online Plan 2 veya Exchange Online Arşivleme eklenti lisansıyla lisans Office 365 E1

   VEYA

  - Ön Hat F5 Uyumluluğu veya F5 Güvenlik & Uyumluluğu eklenti lisansını Microsoft 365  

  VE

  - SharePoint Online Plan 2 veya OneDrive İş Plan 2 eklenti lisansıyla Office 365 E1 lisansı
  
  Lisans atama hakkında bilgi için bkz. [Kullanıcılara lisans atama](../admin/manage/assign-licenses-to-users.md).

Güvenlik ve uyumluluk hakkında bilgi ve rehberlik için:

- [Microsoft 365 Karşılaştırma tablosundaki](https://aka.ms/M365EnterprisePlans) eBulma ve denetim bölümünü indirip inceleyin.

- [Güvenlik & uyumluluğu için Microsoft 365 kılavuzuna bakın - Hizmet Açıklamaları | Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="step-2-assign-ediscovery-permissions"></a>2. Adım: eBulma izinlerini atama

eBulma 'ya (Standart) erişmek veya bir eBulma (Standart) olayının üyesi olarak eklenmek için, kullanıcıya uygun izinlerin atanması gerekir. Özellikle, kullanıcının uyumluluk portalında eBulma Yöneticisi rol grubunun bir üyesi olarak eklenmesi gerekir. Bu rol grubunun üyeleri eBulma (Standart) servis taleplerini oluşturabilir ve yönetebilir. Üyeler ekleyip kaldırabilir, kullanıcılara eBulma ayrılığı yapabilir, arama oluşturup düzenleyebilir ve eBulma (Standart) durumundan içerik dışarı aktarabilir.

Kullanıcıları eBulma Yöneticisi rol grubuna eklemek için aşağıdaki adımları tamamlayın:

1. Uyumluluk portalına gidin ve Microsoft 365 veya Office 365 kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**İzinler**</a> sayfasında **eBulma Yöneticisi** rol grubunu seçin.

3. eBulma Yöneticisi açılır sayfasında, **eBulma Yöneticisi** bölümünün yanındaki **Düzenle'ye** tıklayın.

4. Rol grubunu düzenleme sihirbazının **eBulma Yöneticisi** seç sayfasında **Bulma Yöneticisi'ni Seç'e** tıklayın.

5. **Ekle'ye** tıklayın ve rol grubuna eklemek istediğiniz tüm kullanıcılar için onay kutusunu seçin.

6. Seçili kullanıcıları eklemek için **Ekle'ye** tıklayın ve ardından **Bitti'ye** tıklayın.

7. Kullanıcıları rol grubuna eklemek için **Kaydet'e** tıklayın ve ardından adımı tamamlamak için **Kapat'a** tıklayın.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>eBulma Yöneticisi rol grubu hakkında daha fazla bilgi

eBulma Yöneticisi rol grubunda iki alt grup vardır. Bu alt gruplar arasındaki fark kapsama bağlıdır.

- **eBulma Yöneticisi**: Oluşturdukları veya üyesi oldukları eBulma (Standart) servis taleplerini görüntüleyebilir ve yönetebilir. Başka bir eBulma Yöneticisi bir servis talebi oluşturur ancak bu olayın üyesi olarak ikinci bir eBulma Yöneticisi eklemezse, ikinci eBulma Yöneticisi uyumluluk merkezindeki eBulma (Standart) sayfasında olayı görüntüleyemez veya açamaz. Genel olarak, kuruluşunuzdaki çoğu kişi eBulma Yöneticisi alt grubuna eklenebilir.

- **eBulma Yöneticisi**: eBulma Yöneticisi'nin gerçekleştirebileceği tüm servis talebi yönetim görevlerini gerçekleştirebilir. Ayrıca, eBulma Yöneticisi şunları yapabilir:

  - eBulma (Standart) sayfasında listelenen tüm servis taleplerini görüntüleyin.
  
  - Kendilerini olayın üyesi olarak ekledikten sonra kuruluştaki herhangi bir olayı yönetin.

  - Kuruluştaki her servis talebi için servis talebi verilerine erişin ve verileri dışarı aktarın.
  
  - eBulma durumundan üyeleri kaldırma. Bir servis talebinin üyelerini yalnızca eBulma Yöneticisi kaldırabilir. eBulma Yöneticisi alt grubunun üyesi olan kullanıcılar, olayı kullanıcı oluşturmuş olsa bile bir servis talebinin üyelerini kaldıramaz.

  Geniş erişim kapsamı nedeniyle, bir kuruluşun eBulma Yöneticileri alt grubunun üyesi olan yalnızca birkaç yöneticisi olmalıdır.

eBulma izinleri ve eBulma Yöneticisi rol grubuna atanan her rolün açıklaması hakkında daha fazla bilgi için bkz. [eBulma izinleri atama](assign-ediscovery-permissions.md).

## <a name="step-3-create-a-ediscovery-standard-case"></a>3. Adım: eBulma (Standart) olayı oluşturma

Sonraki adım, bir servis talebi oluşturmak ve eBulma (Standart) kullanmaya başlamaktır. Servis talebi oluşturmak ve üye eklemek için aşağıdaki adımları tamamlayın. Servis talebini oluşturan kullanıcı otomatik olarak üye olarak eklenir.

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Uyumluluk portalına</a> gidin ve uygun eBulma izinlerine atanmış bir kullanıcı hesabının kimlik bilgilerini kullanarak oturum açın. Kuruluş Yönetimi rol grubunun üyeleri de eBulma (Standart) servis talepleri oluşturabilir.

2. Uyumluluk portalının sol gezinti bölmesinde **Tümünü göster'e** ve ardından **eBulma Çekirdeği'ne** >  tıklayın.<a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank"></a>

3. **eBulma (Standart)** sayfasında Servis **talebi oluştur'a** tıklayın.

4. **Yeni servis talebi** açılır sayfasında, servis talebine bir ad verin (gerekli) ve ardından isteğe bağlı bir açıklama yazın. Servis talebi adı kuruluşunuzda benzersiz olmalıdır.

5. Servis talebini oluşturmak için **Kaydet'e** tıklayın.

   Yeni servis talebi oluşturulur ve eBulma (Standart) sayfasında görüntülenir. Yeni servis talebini görüntülemek için **Yenile'ye** tıklamanız gerekebilir.

## <a name="step-4-optional-add-members-to-a-ediscovery-standard-case"></a>4. Adım (isteğe bağlı): eBulma (Standart) olayına üye ekleme

3. Adımda bir servis talebi oluşturursanız ve servis talebini kullanacak tek kişi sizseniz, bu adımı gerçekleştirmeniz gerekmez. eBulma tutmaları oluşturmak, içerik aramak ve arama sonuçlarını dışarı aktarmak için servis talebini kullanmaya başlayabilirsiniz. Diğer kullanıcılara (veya rol grubuna) servis talebine erişim vermek istiyorsanız bu adımı gerçekleştirin.

1. Uyumluluk portalındaki **eBulma (Standart)** sayfasında, üye eklemek istediğiniz servis talebinin adına tıklayın.

2. Servis talebi giriş sayfasında **Ayarlar** sekmesini seçin ve sonra **erişim & izinleri'ni** seçin.

3. **Erişim & izinleri** açılır sayfasında, **Üyeler'in** altında **Ekle'ye** tıklayarak olaya üye ekleyin.

    Rol gruplarını bir servis talebinin üyesi olarak eklemeyi de seçebilirsiniz. **Rol grupları'nın** altında **Ekle'ye** tıklayın. Bir servis talebine yalnızca üyesi olduğunuz rol gruplarını atayabilirsiniz. Bunun nedeni rol gruplarının eBulma olayına üye atayabilecek kullanıcıları denetlemesidir.

4. Vakanın üyesi olarak eklenebilen kişi veya rol grupları listesinde, eklemek istediğiniz kişilerin (veya rol gruplarının) adının soluna tıklayın. Üye olarak eklenebilen kişilerin veya rol gruplarının büyük bir listesi varsa, listede belirli bir kişiyi veya rol grubunu aramak için **Arama** kutusunu kullanın.
  
5. Olaya üye olarak eklenecek kişileri veya rol gruplarını seçtikten sonra **Kaydet'e** tıklayarak yeni üyeleri veya rol gruplarını kaydedin.

> [!IMPORTANT]
>
>- Bir rolün, servis talebine üye olarak eklediğiniz bir rol grubuna eklenmesi veya kaldırılması durumunda rol grubu, servis talebinin bir üyesi olarak (veya rol grubunun üyesi olduğu herhangi bir durumda) otomatik olarak kaldırılır. Bunun nedeni, kuruluşunuzun bir olayın üyelerine yanlışlıkla ek izinler sağlamasını korumaktır. Benzer şekilde, bir rol grubu silinirse, üyesi olduğu tüm durumlardan kaldırılır. Daha fazla bilgi için bkz. [eBulma izinleri atama](assign-ediscovery-permissions.md#adding-role-groups-as-members-of-ediscovery-cases). 
>
>- Daha önce açıklandığı gibi, bir servis talebindeki üyeleri yalnızca eBulma Yöneticisi kaldırabilir. eBulma Yöneticisi alt grubunun üyesi olan kullanıcılar, olayı kullanıcı oluşturmuş olsa bile bir servis talebinin üyelerini kaldıramaz.
>

## <a name="explore-the-ediscovery-standard-workflow"></a>eBulma (Standart) iş akışını keşfetme

Temel eBulma'yı kullanmaya başlamanız için, ilgilendiğiniz kişiler için eBulma tutmaları oluşturma, araştırmanızla ilgili içeriği arama ve daha fazla inceleme için bu verileri dışarı aktarma gibi basit bir iş akışı aşağıda açıklanmaktadır. Bu adımların her birinde, keşfedebileceğiniz bazı genişletilmiş eBulma (Standart) işlevlerini de vurgulayacağız.

![eBulma (Standart) iş akışı.](../media/CoreEdiscoveryWorkflow.png)

1. **[eBulma ayrı tutması oluşturun](create-ediscovery-holds.md)**. Olay oluşturduktan sonraki ilk adım, araştırmanızla ilgilendiğiniz kişilerin içerik konumlarına ayrı *tutma (eBulma ayrılığı* olarak da adlandırılır) yerleştirmektir. İçerik konumları Exchange posta kutularını, SharePoint siteleri, OneDrive hesaplarını ve Microsoft Teams ve Microsoft 365 Grupları ile ilişkili posta kutularını ve siteleri içerir. Bu adım isteğe bağlı olsa da, eBulma ayrı tutması oluşturmak, araştırma sırasında olayla ilgili olabilecek içeriği korur. EBulma ayrı tutması oluşturduğunuzda, belirli içerik konumlarındaki tüm içeriği koruyabilir veya yalnızca ayrı tutma sorgusuyla eşleşen içeriği korumak için sorgu tabanlı ayrı tutma oluşturabilirsiniz. İçeriği korumanın yanı sıra, eBulma ayrı tutmaları oluşturmanın bir diğer iyi nedeni, sonraki adımda arama oluşturup çalıştırdığınızda beklemedeki içerik konumlarında hızlı bir şekilde arama yapmaktır (aranacak her konumu seçmek yerine). Araştırmanızı tamamladıktan sonra, oluşturduğunuz tüm ayrı tutmaları serbest bırakabilirsiniz.

2. **[İçerik arayın](search-for-content-in-core-ediscovery.md)**. eBulma ayrı tutmaları oluşturduktan sonra, yerleşik arama aracını kullanarak beklemedeki içerik konumlarında arama yapın. Ayrıca, servis talebiyle ilgili olabilecek veriler için diğer içerik konumlarını da arayabilirsiniz. Büyük/küçük harfle ilişkili farklı aramalar oluşturabilir ve çalıştırabilirsiniz. Büyük olasılıkla servis talebiyle ilgili olan verilerle arama sonuçları döndüren [arama sorguları oluşturmak](keyword-queries-and-search-conditions.md) için anahtar sözcükleri, özellikleri ve koşulları kullanırsınız. Şunları da yapabilirsiniz:

   - Sonuçları daraltmak için arama sorgusunu daraltmanıza yardımcı olabilecek arama istatistiklerini görüntüleyin.

   - İlgili verilerin bulunup bulunmadığını hızla doğrulamak için arama sonuçlarının önizlemesini görüntüleyin.

   - Sorguyu düzeltin ve aramayı yeniden çalıştırın.

3. **[Arama sonuçlarını dışarı aktarın ve indirin](export-content-in-core-ediscovery.md)**. Araştırmanızla ilgili verileri arayıp bulduktan sonra, araştırma ekibi dışındaki kişilerin gözden geçirmesi için Office 365 dışarı aktarabilirsiniz. Verileri dışarı aktarmak iki adımlı bir işlemdir. İlk adım, büyük/küçük harf aramasının sonuçlarını Office 365 dışarı aktarmaktır. Bu, bir aramanın sonuçlarını Microsoft tarafından sağlanan bir Azure Depolama konumuna kopyalayarak gerçekleştirilir. Sonraki adım, içeriği yerel bir bilgisayara indirmek için eBulma Dışarı Aktarma aracını kullanmaktır. Dışarı aktarılan veri dosyalarına ek olarak, dışarı aktarma paketi bir dışarı aktarma raporu, bir özet rapor ve bir hata raporu içerir.
