---
title: Arşiv ve silme ilkesi (MRM) özelleştirme
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MBS150
- BCS160
- MET150
ms.assetid: ec3587e4-7b4a-40fb-8fb8-8aa05aeae2ce
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Öğeleri otomatik olarak kullanıcının arşiv posta kutusuna taşımak için özel bir İleti Kayıtları Yönetimi (MRM) arşivleme ve silme ilkesi oluşturma.
ms.openlocfilehash: 192bed6be6c3129410f4e51144402c6c19e12d37
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009980"
---
# <a name="customize-an-archive-and-deletion-policy-for-mailboxes-in-your-organization"></a>Arşiv ve silme ilkesi özelleştirme

Microsoft 365 uyumluluk yöneticileri, öğeleri otomatik olarak kullanıcının arşiv posta kutusuna taşır ve posta kutusundan öğeleri otomatik olarak silen bir arşivleme ve [](archive-mailboxes.md) silme ilkesi oluşturabilir.

Bunu yapmak için, posta kutularına atanmış bir mesajlaşma Kayıtları Yönetimi (MRM) bekletme ilkesi oluşturarak ve öğeleri belirli bir sürenin ardından kullanıcının arşiv posta kutusuna taşırken, bu ilke belirli bir yaş sınırına ulaştıktan sonra öğeleri de posta kutusundan siler. 

Hangi öğelerin taşın olacağını veya silineceklerini ve bu öğelerin ne zaman silineceklerini belirleyen kurallara bekletme etiketleri denir. Bekletme etiketleri, kullanıcının posta kutusuna atanan bir MRM bekletme ilkesine bağlıdır. Bekletme etiketi, bekletme ayarlarını kullanıcının posta kutusunda yer alan tek tek iletilere ve klasörlere uygular. bir iletinin posta kutusunda ne kadar süre tutul yaptığını ve ileti belirtilen bekletme yaşına ulaştığında hangi eylemin geçerli olduğunu tanımlar. Bekletme yaşına ulaşan bir ileti, kullanıcının arşiv posta kutusuna taşınır veya silinir.
  
Bu makaledeki adımlar, Alpine House adlı hayali bir kuruluş için bir arşivleme ve bekletme ilkesi ayarlama. Bu ilkenin ayarlaması aşağıdaki görevleri içerir:
  
- Kuruluşta her kullanıcı için bir arşiv posta kutusu etkinleştirildi. Bu, kullanıcılara ek posta kutusu depolama alanı sağlar ve bekletme ilkesi öğeleri arşiv posta kutusuna taşıyabiliyor olması için gereklidir. Ayrıca, kullanıcıların öğeleri arşiv posta kutusuna taşımaları için bilgileri arşivlemelerine olanak sağlar.

- Aşağıdakileri yapacak üç özel bekletme etiketi oluşturma:

  - 3. yıllık öğeleri otomatik olarak kullanıcının arşiv posta kutusuna taşır. Öğelerin arşiv posta kutusuna taşınması, kullanıcının birincil posta kutusunda yer sağlar.

  - 5. yıllık öğeleri otomatik olarak Silinmiş Öğeler klasöründen siler. Bu, kullanıcının birincil posta kutusunda da yer sağlar. Kullanıcı, gerekirse bu öğeleri kurtarma fırsatına sahip olur. Daha fazla ayrıntı için Daha fazla [bilgi bölümündeki](#more-information) dipnota bakın. 

  - 7. yıllık öğeleri otomatik (ve kalıcı) olarak hem birincil hem de arşiv posta kutusundan siler. Uyumluluk mevzuatı nedeniyle, bazı kuruluşların e-postalarını belirli bir süre tutmaları gerekir. Kuruluş, bu süre sona erdikten sonra bu öğeleri kullanıcı posta kutularında kalıcı olarak kaldırmak ister.

- Yeni bir bekletme ilkesi oluşturma ve yeni özel bekletme etiketlerini buna ekleme. Ayrıca, yeni bekletme ilkesine yerleşik bekletme etiketleri de eklersiniz. Bu etiketler arasında, kullanıcıların posta kutularına atay kullanıcıların da atay etiketi olabilir. Ayrıca, öğeleri kullanıcının birincil posta kutusunda yer alan Kurtarılabilir Öğeler klasöründen arşiv posta kutusunun Kurtarılabilir Öğeler klasörüne taşırken bir bekletme etiketi de eklersiniz. Bu, posta kutusu yerine basılı durumdayken kullanıcının Kurtarılabilir Öğeler klasöründe yer açın.

Bu makaledeki adımların herhangi bir bölümü veya hepsi, kendi organizasyonu olan posta kutuları için bir arşivleme ve silme ilkesi ayarlamak için kullanılabilir. Bu işlemi, uygulamadan önce birkaç posta kutusu üzerinde, organizasyonu tüm posta kutularında sınamanızı öneririz.
  
## <a name="before-you-set-up-an-archive-and-deletion-policy"></a>Arşivleme ve silme ilkesi ayarlamadan önce

- Bu konudaki adımları gerçekleştirmek için, kurumda genel yönetici olmak gerekir. 

- Yeni bir kullanıcı hesabı oluşturulduğunda ve kullanıcıya kullanıcıya Exchange Online posta kutusu otomatik olarak oluşturulur. Oluşturulan posta kutusuna otomatik olarak Varsayılan MRM İlkesi adlı bir varsayılan bekletme ilkesi atanır. Bu makalede, yeni bir bekletme ilkesi oluşturduktan sonra bunu kullanıcı posta kutularına ataarak Varsayılan MRM ilkesi'nin yerini atayabilirsiniz. Bir posta kutusuna aynı anda yalnızca bir bekletme ilkesi atanmış olabilir.

- Bu konudaki bekletme etiketleri ve bekletme ilkeleri hakkında daha fazla bilgi Exchange Online [bkz. Bekletme etiketleri ve bekletme ilkeleri](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies).

## <a name="step-1-enable-archive-mailboxes-for-users"></a>1. Adım: Arşiv posta kutularını kullanıcılar için etkinleştirme

İlk adım, arşiv posta kutusunu kurumuz daki her kullanıcı için etkinleştirmektir. "Arşive Taşı" bekletme eylemine sahip bir bekletme etiketinin, bekletme süresi dolan öğeleri hareket ettireminden emin olmak için kullanıcının arşiv posta kutusunun etkinleştirilmiş olması gerekir.
  
> [!NOTE]
> Süreç tamamlamadan önce etkinleştirilmiş olduğu sürece arşiv posta kutularını, bu süreç sırasında ne zaman etkinleştirdiyseniz onu etkinleştirebilirsiniz. Bir arşiv posta kutusu etkinleştirilmemişse, bu posta kutusuna atanmış bir arşivleme veya silme ilkesi olan öğeler üzerinde hiçbir eylem gerçeklanmaz.
  
1. <https://compliance.microsoft.com> adresine gidin.

2. Genel yönetici hesabınızla oturum açın.
    
3. Görünüm Microsoft 365 uyumluluk merkezi **yönetimi'ne ve** sonra da Arşiv **sekmesine** tıklayın.

    Ve ilgili arşiv posta kutusunun etkin mi yoksa devre dışı mı olduğunu gösterir.

4. Listenin ilk posta kutusuna tıklar, **Shift** tuşunu basılı tutarken son posta kutusuna tıklayarak tüm posta kutularını seçin.

    > [!TIP]
    > Bu adım, hiçbir arşiv posta kutusunun etkinleştirilmiş olmadığını varsayıyor. Arşivi etkinleştirilmiş posta kutularınız varsa **Ctrl** tuşunu basılı tutun ve devre dışı bırakılmış bir arşiv posta kutusu olan her posta kutusuna tıklayın. Posta kutularını seçmeyi **kolaylaştırmak için** Arşiv posta kutusu sütun başlığına tıklar ve satırları arşiv posta kutusunun etkin veya devre dışı olup olmadığını temel alarak sıraabilirsiniz.
  
5. Ayrıntılar bölmesindeki Toplu **Düzenleme'nin altında Etkinleştir'e** **tıklayın**.

    İki yıldan daha eski öğelerin yeni arşiv posta kutusuna taşınacaklarını söyleyen bir uyarı görüntülenir. Bunun nedeni, oluşturulan yeni bir kullanıcı posta kutusuna atanan varsayılan bekletme ilkesinde, bekletme süresi 2 yıl olan bir arşivleme varsayılan ilke etiketi yer a doğru olur. 2. Adımda oluştury istediğiniz özel arşivleme varsayılan ilke etiketinin bekletme süresi 3 yıl olur. Bu, 3 yıllık veya daha eski öğelerin arşiv posta kutusuna taşınacak olduğu anlamına gelir.

6. **Evet'e** tıklarsanız uyarı iletisi kapanır ve seçilen her posta kutusu için arşiv posta kutusunu etkinleştirme işlemini başlatabilirsiniz.

7. İşlem tamamlandığında **Yenile'ye** ![tıklayın.](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) arşivle sayfasındaki listeyi **güncelleştirin** .

    Arşiv posta kutusu, kuruluşta tüm kullanıcılar için etkinleştirilir.

    ![Arşiv posta kutusu etkinleştirilmiş posta kutularının listesi.](../media/61a7cb97-1bed-4808-aa5f-b6b761cfa8de.png)

## <a name="step-2-create-new-retention-tags-for-the-archive-and-deletion-policies"></a>2. Adım: Arşiv ve silme ilkeleri için yeni bekletme etiketleri oluşturma

Bu adımda, daha önce açıklanan üç özel bekletme etiketi oluştur olacak.
  
- Alpine House 3 Yıl Arşive Taşı (özel arşiv ilkesi)

- Alpine House 7 Yıl Kalıcı Olarak Sil (özel silme ilkesi)

- Alpine House Silinmiş Öğeler 5 Yıl Sil ve Kurtarmaya İzin Ver (Silinmiş Öğeler klasörü için özel etiket)

Yeni bekletme etiketleri oluşturmak için, Exchange yönetim merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">(EAC)</a> kullanır ve Exchange Online kullanır. EAC'nin klasik sürümünü kullanmaya emin olun.
  
1. Kimlik bilgilerinizi [https://admin.protection.outlook.com/ecp/](https://admin.protection.outlook.com/ecp/) kullanarak giriş bilgilerine gidin ve oturum açma.
  
2. EAC'de Uyumluluk **yönetimiRetention**  >  etiketlerine gidin

    Kurum için bekletme etiketlerinin bir listesi görüntülenir.

### <a name="create-a-custom-archive-default-policy-tag"></a>Özel bir arşivleme varsayılan ilke etiketi oluşturma
  
İlk olarak, öğeleri 3 yılın ardından arşiv posta kutusuna taşımaya devam etmek üzere özel bir arşivleme varsayılan ilke etiketi (DPT) oluştursunuz.
  
1. Bekletme etiketleri **sayfasında Yeni** etiketYeni **simgesi'ne**![](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) tıklayın ve otomatik olarak tüm posta kutusuna **uygulanır (varsayılan)'ı seçin**.

2. Otomatik olarak **tüm posta kutusuna uygulanan yeni etiket (varsayılan) sayfasında** , aşağıdaki alanları doldurun: 

    ![Ayarlar arşivleme varsayılan ilke etiketini oluşturmak için bu etiketi tıklatın.](../media/41c0a43c-9c72-44e0-8947-da0831896432.png)
  
   1. **Ad** Yeni bekletme etiketi için bir ad yazın. 

   2. **Bekletme eylemi** Bekletme **süresi dolduğunda öğeleri** arşiv posta kutusuna taşımak için Arşive Taşı'ya seçin.

   3. **Bekletme süresi** Öğe **aşağıdaki yaşa ulaştığında (gün olarak) seçeneğini** seçin ve bekletme süresini girin. Bu senaryoda, öğeler 1095 gün (3 yıl) sonra arşiv posta kutusuna taşınır.

   4. **Açıklama** (İsteğe bağlı) Özel bekletme etiketinin amacını açıklayan bir açıklama yazın.

3. **Kaydet'e** tıklar ve özel arşiv DPT'si oluşturun.

    Yeni arşiv DPT'si bekletme etiketleri listesinde görüntülenir.

### <a name="create-a-custom-deletion-default-policy-tag"></a>Özel bir silme varsayılan ilke etiketi oluşturma
  
Ardından, başka bir özel DPT oluştursunuz, ancak bu 7 yıl sonra öğeleri kalıcı olarak sen bir silme ilkesi olacak.
  
1. Bekletme etiketleri **sayfasında Yeni** etiketYeni **simgesi'ne**![](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) tıklayın ve otomatik olarak tüm posta kutusuna **uygulanır (varsayılan)'ı seçin**.

2. Otomatik olarak **tüm posta kutusuna uygulanan yeni etiket (varsayılan) sayfasında** , aşağıdaki alanları doldurun: 

    ![Ayarlar bir silme varsayılan ilke etiketi oluşturmak için bu etiketi tıklatın.](../media/f1f0ff62-eec9-4824-8e7c-d93dcfb09a79.png)
  
   1. **Ad** Yeni bekletme etiketi için bir ad yazın. 

   2. **Bekletme eylemi** Bekletme **süresi dolduğunda** öğeleri posta kutusundan temizlemek için Kalıcı Olarak Sil'i seçin.

   3. **Bekletme süresi** Öğe **aşağıdaki yaşa ulaştığında (gün olarak) seçeneğini** seçin ve bekletme süresini girin. Bu senaryoda, öğeler 2555 gün (7 yıl) sonra temiz olur.

   4. **Açıklama** (İsteğe bağlı) Özel bekletme etiketinin amacını açıklayan bir açıklama yazın. 

3. **Kaydet'e** tıklayın ve özel silme DPT'nizi oluşturun. 

    Yeni silme DPT'si bekletme etiketleri listesinde görüntülenir.

### <a name="create-a-custom-retention-policy-tag-for-the-deleted-items-folder"></a>Silinmiş Öğeler klasörü için özel bir bekletme ilkesi etiketi oluşturma
  
Oluştur oluşturursunuz son bekletme etiketi, Silinmiş Öğeler klasörüne özel bir bekletme ilkesi etiketidir (RPT). Bu etiket, 5 yıl sonra Silinmiş Öğeler klasöründeki öğeleri siler ve kullanıcıların Silinmiş Öğeleri Kurtar aracını kullanarak bir öğeyi kurtarama süresi sağlar.
  
1. Bekletme etiketleri **sayfasında Yeni** etiket Yeni **simgesi'ne** ![](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif)tıklayın ve otomatik olarak bir **varsayılan klasöre uygulanır'ı seçin**.

2. Otomatik **olarak bir varsayılan klasöre uygulanan yeni etiket** sayfasında, aşağıdaki alanları doldurun:

    ![Ayarlar Öğeler klasörü için yeni bir bekletme ilkesi etiketi oluşturmak için bu etiketi kullanın.](../media/6f3104bd-5edb-48ac-884d-5fe13d81dd1d.png)
  
   1. **Ad** Yeni bekletme etiketi için bir ad yazın. 

   2. **Bu etiketi aşağıdaki varsayılan klasöre uygula** Açılan listede Silinmiş **Öğeler'i seçin**.

   3. **Bekletme eylemi** Bekletme **süresi dolduğunda** öğeleri silmek, ancak kullanıcıların silinmiş bir öğeyi silinmiş öğe bekletme süresi içinde (varsayılan olarak 14 gündür) kurtarmak için Sil ve Kurtarmaya İzin Ver'i seçin.

   4. **Bekletme süresi** Öğe **aşağıdaki yaşa ulaştığında (gün olarak) seçeneğini** seçin ve bekletme süresini girin. Bu senaryoda, öğeler 1825 gün (5 yıl) sonra silinir.

   5. **Açıklama** (İsteğe bağlı) Özel bekletme etiketinin amacını açıklayan bir açıklama yazın. 

3. **Kaydet'e** tıklayın ve Silinmiş Öğeler klasörüne özel RPT'yi oluşturun.

    Yeni RPT bekletme etiketleri listesinde görüntülenir.

## <a name="step-3-create-a-new-retention-policy"></a>3. Adım: Yeni bir bekletme ilkesi oluşturma

Özel bekletme etiketlerini oluşturduktan sonraki adım, yeni bir bekletme ilkesi oluşturmak ve bekletme etiketlerini eklemektir. 2. Adımda oluşturduğunuz üç özel bekletme etiketine ve ilk bölümde bahsedilen yerleşik etiketleri ekli olarak eklersiniz. 4. Adımda, kullanıcı posta kutularına bu yeni bekletme ilkesi atamanız gerekir.
  
1. EAC'de Uyumluluk **yönetimiRetention** >  **ilkeleri'ne gidin**.

2. Bekletme ilkeleri **sayfasında Yeni** Yeni **simge'ye** ![tıklayın](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif).

3. Ad **kutusuna** yeni bekletme ilkesi için bir ad yazın; örneğin Alpine **House Arşivleme ve Silme İlkesi**.

4. Bekletme **etiketleri'nin altında** Yeni **Ekle simgesine** ![tıklayın](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif).

    Kuruluşta bekletme etiketlerinin bir listesi görüntülenir. 2. Adımda oluşturduğunuz özel etiketlerin görüntülendiğinden dikkat edin.

5. Aşağıdaki ekran görüntüsünde vurgulanan 9 bekletme etiketi ekleyin (Bu etiketler, Daha fazla bilgi bölümünde daha [ayrıntılı olarak açıklanmaktadır](#more-information) ). Bekletme etiketini eklemek için, etiketi seçin ve Ekle'ye **tıklayın**.

    ![Yeni bekletme ilkesine bekletme etiketleri ekleyin.](../media/d8e87176-0716-4238-9e6a-7c4af35541dc.png)
  
    > [!TIP]
    > **Ctrl** tuşunu basılı tutarak her etikete tıklayarak birden çok bekletme etiketi seçin. 
  
6. Bekletme etiketlerini ekledikten sonra Tamam'a **tıklayın**.

7. Yeni bekletme **ilkesi sayfasında Kaydet'e** **tıklar** ve yeni ilkeyi oluşturun.

    Yeni bekletme ilkesi listede görüntülenir. Ayrıntılar bölmesinde etikete bağlı bekletme etiketlerini görüntülemek için seçin.

    ![Yeni bekletme ilkesi ve bağlı bekletme etiketlerinin listesi.](../media/63bc45e6-110b-4dc9-a85f-8eb1961a8258.png)
  
## <a name="step-4-assign-the-new-retention-policy-to-user-mailboxes"></a>4. Adım: Kullanıcı posta kutularına yeni bekletme ilkesi atama

Yeni bir posta kutusu oluşturulduğunda, bu posta kutusuna varsayılan olarak Varsayılan MRM ilkesi adlı bir bekletme ilkesi atanır. Bu adımda, 3. Adımda oluşturduğunuz yeni bekletme ilkesi, 3. Adımda oluşturduğunuz yeni bekletme ilkesine kurum içinde kullanıcı posta kutularına atadığı için bu bekletme ilkesiyle (posta kutusuna atanmış yalnızca bir bekletme ilkesi olabilir) değiştiriysiniz. Bu adımda, yeni ilkeyi organizasyonu tüm posta kutularına atayydığınız varsayıyoruz.
  
1. EAC'de **AlıcılarMailboxes'a** >  gidin.

    Kuruluşta yer alan tüm kullanıcı posta kutularının listesi görüntülenir.

2. Listenin ilk posta kutusuna tıklar, **Shift** tuşunu basılı tutarken son posta kutusuna tıklayarak tüm posta kutularını seçin. 

3. EAC'nin sağ tarafındaki ayrıntılar bölmesinde, Toplu Düzenleme'nin **altında Diğer seçenekler'e** **tıklayın**.

4. Bekletme **İlkesi'nin altında** **Güncelleştir'e tıklayın**.

5. Toplu bekletme **ilkesi atama sayfasındaki** Bekletme ilkesi seçin açılan  listesinde, 3. Adımda oluşturduğunuz bekletme ilkeyi seçin; örneğin Alpine **House Arşiv ve Bekletme İlkesi**.

6. Yeni **bekletme ilkesi** atamalarını kaydetmek için Kaydet'e tıklayın.

7. Yeni bekletme ilkesine posta kutularına atan olduğunu doğrulamak için, şunları yapabilirsiniz:

   1. Posta Kutuları sayfasında bir **posta kutusu seçin** ve Düzenle Düzenle'ye  ![tıklayın](../media/d7dc7e5f-17a1-4eb9-b42d-487db59e2e21.png).

   2. Seçili kullanıcının posta kutusu özellikleri sayfasında Posta kutusu **özellikleri'ne tıklayın**.

   Posta kutusuna atanan yeni ilkenin adı Bekletme ilkesi **açılan** listesinde görüntülenir.

## <a name="optional-step-5-run-the-managed-folder-assistant-to-apply-the-new-settings"></a>(İsteğe bağlı) 5. Adım: Yeni ayarları uygulamak için Yönetilen Klasör Yardımcısı'nın çalışması

4. Adımda yeni bekletme ilkeyi posta kutularına uyguladıktan sonra, Exchange Online bekletme ayarlarının posta kutularına uygulanması Exchange Online içinde 7 gün kadar zaman alabiliyor. Bunun nedeni, Yönetilen Klasör Yardımcısı adlı *bir sürecin* posta kutularını en az 7 günde bir işlemesidir. Yönetilen Klasör Yardımcısı'nın çalıştır olmasını beklemek yerine, Exchange Online PowerShell'de **Start-ManagedFolderAssistant** cmdlet'ini çalıştırarak bu Exchange Online zorabilirsiniz.

 **Yönetilen Klasör Yardımcısı'nın çalıştırıca ne olur?** Posta kutusunda öğeleri inceleyen ve bekletmeye tabi olup olmadığını belirleyerek bekletme ilkesinde ayarları uygular. Ardından, bekletmeye tabi olan öğeleri uygun bekletme etiketiyle damgalar ve bekletme yaşı geçmiş öğelere belirtilen bekletme eylemlerini alır.
  
PowerShell'e Exchange Online ve ardından Yönetilen Klasör Yardımcısı'nın kurumdaki tüm posta kutularında çalıştırılması gereken adımlar burada vetir.

1. [Bağlan PowerShell Exchange Online e geri tarak.](/powershell/exchange/connect-to-exchange-online-powershell)
  
2. Aşağıdaki iki komutu çalıştırarak Yönetilen Klasör Yardımcısı'nın, organizasyonu tüm kullanıcı posta kutularında başlatması gerekir.

    ```powershell
    $Mailboxes = Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -eq "UserMailbox"}
    ```

    ```powershell
    $Mailboxes.Identity | Start-ManagedFolderAssistant
    ```

Hepsi bu kadar! Alpine House kuruluşu için bir arşivleme ve silme ilkesi ayarladsınız.

> [!NOTE]
> Daha önce de belirtildiği gibi, Yönetilen Klasör Yardımcısı posta kutularını en az 7 günde bir işlemektedir. Dolayısıyla, yönetilen klasör yardımcısı tarafından daha sık bir posta kutusu işlenebilir. Ayrıca, yöneticiler bir posta kutusunun Yönetilen Klasör Yardımcısı tarafından bir sonraki işlemde tahminde belirlenemeyecektir ve bu nedenle posta kutusunu el ile çalıştırmak istemeniz gerekebilir. Öte yandan, Yönetilen Klasör Yardımcısı'nın yeni bekletme ayarlarını bir posta kutusuna uygulamasını geçici olarak engellemek için, `Set-Mailbox -ElcProcessingDisabled $true` Yönetilen Klasör Yardımcısı'nın posta kutusunu işlemesini geçici olarak devre dışı bırakmak için bu komutu çalıştırabilirsiniz. Yönetilen Klasör Yardımcısı'nın bir posta kutusu için yeniden etkinleştirmesi için komutu `Set-Mailbox -ElcProcessingDisabled $false` çalıştırın. Son olarak, posta kutusu kullanıcı hesabı devre dışı bırakılmışsa, bu posta kutusu için öğeleri arşivleme eylemini işlemeziz.
  
## <a name="optional-step-6-make-the-new-retention-policy-the-default-for-your-organization"></a>(İsteğe bağlı) 6. Adım: Yeni bekletme ilkesi için varsayılan kuruluş yapma

4. Adımda, yeni bekletme ilkesi var olan posta kutularına atamanız gerekir. Ancak, Exchange Online bekletme ilkesi gelecekte oluşturulan yeni posta kutularına atanacak şekilde ayarları yapılandırabilirsiniz. Bu işlemi, Exchange Online posta kutusu planını güncelleştirmek için PowerShell'i kullanarak yapar. Posta *kutusu planı* , yeni posta kutuları için özellikleri otomatik olarak yapılandıran bir şablondur.  Bu isteğe bağlı adımda, posta kutusu planına atanan geçerli bekletme ilkesiyle (varsayılan olarak Varsayılan MRM İlkesi) 3. Adımda oluşturduğunuz bekletme ilkesiyle değiştirebilirsiniz. Posta kutusu planını güncelleştirdikten sonra, yeni bekletme ilkesi yeni posta kutularına atanır.

1. [Bağlan PowerShell Exchange Online e geri tarak.](/powershell/exchange/connect-to-exchange-online-powershell)

2. Aşağıdaki komutu çalıştırarak, kuruluşta yer alan posta kutusu planları hakkında bilgi görüntüleniyor.

    ```powershell
    Get-MailboxPlan | Format-Table DisplayName,RetentionPolicy,IsDefault
    ```

    Varsayılan olarak ayarlanmış posta kutusu planını not alın.

3. 3. Adımda oluşturduğunuz yeni bekletme ilkesini (örneğin **Alpine House** Arşiv ve Bekletme İlkesi) varsayılan posta kutusu planına atamak için aşağıdaki komutu çalıştırın. Bu örnekte, varsayılan posta kutusu planının adının **ExchangeOnlineEnterprise olduğu varsay konur**.

    ```powershell
    Set-MailboxPlan "ExchangeOnlineEnterprise" -RetentionPolicy "Alpine House Archive and Retention Policy"
    ```

4. Varsayılan posta kutusu planına atanan bekletme ilkesinde değişiklik olduğunu doğrulamak için 2. adımda komutu yeniden çalıştırabilirsiniz.

## <a name="more-information"></a>Daha fazla bilgi

- Bekletme yaşı nasıl hesaplanır? Posta kutusu öğelerinin bekletme yaşı, teslim tarihine veya taslak iletileri gibi kullanıcı tarafından oluşturulan ancak gönderilmeyen öğeler için oluşturma tarihine kadar hesaplanır. Yönetilen Klasör Yardımcısı posta kutusu öğelerini işlemesi sırasında, Sil ve Kurtarmaya İzin Ver veya Kalıcı Olarak Sil bekletme eylemiyle bekletme etiketleri olan tüm öğelere bir başlangıç tarihi ve sona erme tarihi damgalar. Arşiv etiketi olan öğelere taşıma tarihi damgalenir. 

- Aşağıdaki tabloda, bu konudaki adımlar atarak oluşturulan özel bekletme ilkesine eklenen her bekletme etiketi hakkında daha fazla bilgi bulunmaktadır.

    | Bekletme etiketi | Bu etiket ne yapar? | Yerleşik mi özel mi? | Tür |
    |:-----|:-----|:-----|:-----|
    |Alpine House 3 Yıl Arşive Taşı  <br/> |1095 günlük (3 yıllık) öğeleri arşiv posta kutusuna taşır.  <br/> |Özel (Bkz [. 2. Adım: Arşiv ve silme ilkeleri için yeni bekletme etiketleri oluşturma](#step-2-create-new-retention-tags-for-the-archive-and-deletion-policies))  <br/> |Varsayılan İlke Etiketi (arşiv); bu etiket otomatik olarak tüm posta kutusuna uygulanır.  <br/> |
    |Alpine House 7 Yıl Kalıcı Olarak Sil  <br/> |Birincil posta kutusu veya arşiv posta kutusu 7 yaşında öğeleri kalıcı olarak siler.  <br/> |Özel (Bkz [. 2. Adım: Arşiv ve silme ilkeleri için yeni bekletme etiketleri oluşturma](#step-2-create-new-retention-tags-for-the-archive-and-deletion-policies))  <br/> |Varsayılan İlke Etiketi (silme); bu etiket otomatik olarak tüm posta kutusuna uygulanır.  <br/> |
    |Alpine House Silinmiş Öğeler 5 Yıl Sil ve Kurtarmaya İzin Ver  <br/> |Silinmiş Öğeler klasöründeki 5 yıllık öğeleri siler. Kullanıcılar, silinmeleri sonrasında 14 gün içerisinde bu öğeleri kurtarabilirsiniz.<sup>\*</sup> <br/> |Özel (Bkz [. 2. Adım: Arşiv ve silme ilkeleri için yeni bekletme etiketleri oluşturma](#step-2-create-new-retention-tags-for-the-archive-and-deletion-policies))  <br/> |Bekletme İlkesi Etiketi (Silinmiş Öğeler); bu etiket, Silinmiş Öğeler klasöründeki öğelere otomatik olarak uygulanır.  <br/> |
    |Kurtarılabilir Öğeler 14 gün Arşive Taşı  <br/> |Kurtarılabilir Öğeler klasöründe 14 gün süreyle kaldınız öğeleri arşiv posta kutusunda Kurtarılabilir Öğeler klasörüne taşır.  <br/> |Yerleşik  <br/> |Bekletme İlkesi Etiketi (Kurtarılabilir Öğeler); Bu etiket, Kurtarılabilir Öğeler klasöründeki öğelere otomatik olarak uygulanır.  <br/> |
    |Gereksiz E-posta  <br/> |Gereksiz E-posta klasöründe 30 gün süreyle kaldı olan öğeleri kalıcı olarak siler. Kullanıcılar, silinmeleri sonrasında 14 gün içerisinde bu öğeleri kurtarabilirsiniz.<sup>\*</sup> <br/> |Yerleşik  <br/> |Bekletme İlkesi Etiketi (Gereksiz E-posta); Bu etiket, otomatik olarak Gereksiz E-posta klasöründeki öğelere uygulanır.  <br/> |
    |1 Ay Sil  <br/> |30 günlük öğeleri kalıcı olarak siler. Kullanıcılar, silinmeleri sonrasında 14 gün içerisinde bu öğeleri kurtarabilirsiniz.<sup>\*</sup> <br/> |Yerleşik  <br/> |Kişisel; bu etiket kullanıcılar tarafından uygulanabilir.  <br/> |
    |1 Yıl Sil  <br/> |365 günlük öğeleri kalıcı olarak siler. Kullanıcılar, silinmeleri sonrasında 14 gün içerisinde bu öğeleri kurtarabilirsiniz.<sup>\*</sup> <br/> |Yerleşik  <br/> |Kişisel; bu etiket kullanıcılar tarafından uygulanabilir.  <br/> |
    |Hiçbir Zaman Silme  <br/> |Bu etiket, öğelerin bekletme ilkesi tarafından silinmesini önler.  <br/> |Yerleşik  <br/> |Kişisel; bu etiket kullanıcılar tarafından uygulanabilir.  <br/> |
    |Kişisel 1 yıl arşive taşı  <br/> |Öğeleri 1 yıl sonra arşiv posta kutusuna taşır.  <br/> |Yerleşik  <br/> |Kişisel; bu etiket kullanıcılar tarafından uygulanabilir.  <br/> |

    > <sup>\*</sup>Kullanıcılar silinmiş bir öğeyi, silinmiş öğe bekletme süresi içinde kurtarmak için Outlook ve Web üzerinde Outlook'te (eski adı Outlook Web App) Silinmiş Öğeleri Kurtarma aracını kullanabilir. Bu süre, varsayılan olarak Exchange Online'Exchange Online. Yönetici, silinmiş Windows PowerShell bekletme süresi en fazla 30 gün olacak şekilde artırmak için Windows PowerShell'i kullanabilir. Daha fazla bilgi için bkz. Outlook'de silinmiş öğeleri [kurtarma Windows](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce) posta kutusu için silinmiş öğe bekletme [](/exchange/recipients-in-exchange-online/manage-user-mailboxes/change-deleted-item-retention) Exchange Online
  
- Kurtarılabilir **Öğeler'in 14 gün süreyle** Arşive Taşı bekletme etiketi, kullanıcının birincil posta kutusunda Kurtarılabilir Öğeler klasöründe depolama alanı sağlar. Bu özellik, kullanıcının posta kutusu bir süre basılı durumdayken yararlıdır; bu da, kullanıcının posta kutusunun hiçbir kalıcı olarak silinmey oturumları anlamına gelir. Öğeleri arşiv posta kutusuna taşımadan, birincil posta kutusunda Kurtarılabilir Öğeler klasörünün depolama kotasına ulaşabilirsiniz. Bu konuda ve bu kotadan nasıl kaçınılması konusunda daha fazla bilgi için bkz. Tutmadaki posta [kutuları için Kurtarılabilir Öğe kotasını artırma](./increase-the-recoverable-quota-for-mailboxes-on-hold.md).
