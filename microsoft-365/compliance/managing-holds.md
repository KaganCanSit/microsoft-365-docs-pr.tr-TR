---
title: eBulma'da ayrı tutmaları yönetme (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: eKeşif (Premium) olayınızla ilgili içeriği korumak için koruyuculara ve veri kaynaklarına nasıl saklamayı öğrenin.
ms.custom:
- seo-marvel-mar2020
- admindeeplinkMAC
ms.openlocfilehash: c2213c34e111989f0de6fccf886f44dd0f45841b
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098504"
---
# <a name="manage-holds-in-ediscovery-premium"></a>eBulma'da ayrı tutmaları yönetme (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview eBulma (Premium) servis talebi kullanarak, servis talebinizle ilgili olabilecek içeriği korumak için ayrı tutmalar oluşturabilirsiniz. eBulma (Premium) tutma özelliklerini kullanarak, saklamaları koruyuculara ve veri kaynaklarına yerleştirebilirsiniz. Ayrıca, posta kutularına ve OneDrive İş sitelerine gözetimsiz bir saklama yerleştirebilirsiniz. Ayrıca bir Microsoft 365 Grubu için grup posta kutusuna, SharePoint sitesine ve OneDrive İş sitesine ayrı tutabilirsiniz. Benzer şekilde, Microsoft Teams ile ilişkili posta kutusuna ve siteye ayrı tutabilirsiniz. İçerik konumlarını beklemeye aldığınızda, siz koruyucuyu serbest bırakana, belirli bir veri konumunu kaldırana veya saklama ilkesini tamamen silene kadar içerik tutulur.

## <a name="manage-custodian-based-holds"></a>Koruyucu tabanlı ayrı tutmaları yönetme

Bazı durumlarda, tanımladığınız ve olay sırasında verilerini korumaya karar vermiş bir dizi koruyucunuz olabilir. eBulma'da (Premium) bu koruyucular beklemeye alındığında, kullanıcı ve onun seçtiği veri kaynakları otomatik olarak bir koruyucu saklama ilkesine eklenir.

Koruyucu tutma ilkesini görüntülemek için:

1. Microsoft Purview uyumluluk portalında, kuruluşunuzdaki servis taleplerinin listesini görüntülemek için **eBulma > Gelişmiş'e** tıklayın.

2. Servis talebinize koruyucular eklemek için **Kaynaklar** sekmesine gidin. Bir eBulma (Premium) olayı içinde koruyucuları nasıl ekleyip beklemeye alacağınızı öğrenmek için bkz. [Olaya Koruyucu ekleme](add-custodians-to-case.md). Koruyucuları zaten ekleyip beklemeye aldıysanız 3. adıma gidin.

3. **Ayrı Tutmalar** sekmesine gidin ve **CustodianHold'a\<HoldId>** tıklayın.

4. Açılır sayfada ilkenin tutma istatistiklerini görebilirsiniz. Ayrıca, koruyucu tabanlı saklamanıza sorgu uygulama gibi eylemler de gerçekleştirebilirsiniz. Ayrı tutma sorgusu oluşturma ve koşulları kullanma hakkında daha fazla bilgi için bkz [. İçerik Arama için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).

## <a name="manage-non-custodial-holds"></a>Gözetim altında olmayan ayrı tutmaları yönetme

Ayrı tutma oluşturduğunuzda, belirtilen içerik konumlarında tutulan içeriğin kapsamını belirlemeye ilişkin aşağıdaki seçeneklere sahipsiniz:

- Tüm içeriğin ayrı tutulduğu sonsuz bir ayrı tutma oluşturursunuz. Alternatif olarak, yalnızca arama sorgusuyla eşleşen içeriğin beklemeye alındığı sorgu tabanlı bir ayrı tutma oluşturabilirsiniz.
  
- Yalnızca bu tarih aralığında gönderilen, alınan veya oluşturulan içeriği tutacak bir tarih aralığı belirtebilirsiniz. Alternatif olarak, ne zaman gönderildiğine, alındığına veya oluşturulduğuna bakılmaksızın tüm içeriği tutabilirsiniz.

eBulma (Premium) olayı için gözetimsiz bir saklama oluşturmak için:

1. Kuruluşunuzdaki servis taleplerinin listesini görüntülemek için <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">uyumluluk portalında</a> **eBulma > Gelişmiş'e** tıklayın.
  
2. Ayrı tutmaları oluşturmak istediğiniz servis talebinin yanındaki **Aç'a** tıklayın.
  
3. Servis talebinin giriş sayfasında **Ayrı Tutmalar** sekmesine tıklayın.
  
4. **Ayrı Tutmalar** sekmesinde **Oluştur'a** tıklayın.
  
5. **Ayrı tutmanızı adlandırın** sayfasında, ayrı tutmaya bir ad verin. Ayrı tutmanın adı kuruluşunuzda benzersiz olmalıdır.

6. (İsteğe bağlı) **Açıklama** kutusuna ayrı tutmanın açıklamasını ekleyin.
  
7. **İleri**'ye tıklayın.
  
8. Beklemeye almak istediğiniz içerik konumlarını seçin. Posta kutularını, siteleri ve ortak klasörleri ayrı tutabilirsiniz.

   1. **e-posta Exchange** - **Kullanıcıları, grupları veya ekipleri seç'e** tıklayın ve sonra beklemeye eklenecek posta kutularını belirtmek için **Kullanıcıları, grupları veya ekipleri yeniden seç'e** tıklayın. Kullanıcı posta kutularını ve dağıtım gruplarını bulmak için arama kutusunu kullanın (grup üyelerinin posta kutularına ayrı tutma yerleştirmek için). ayrıca bir Microsoft 365 Grubu veya Microsoft Ekibi için ilişkili posta kutusuna ayrı tutabilirsiniz. Kullanıcı, grup, ekip onay kutusunu seçin, **Seç'e** ve ardından **Bitti'ye** tıklayın.

      > [!NOTE]
      > Beklemeye alınacak posta kutularını belirtmek için **Kullanıcıları, grupları veya ekipleri seçin'e** tıkladığınızda, görüntülenen posta kutusu seçicisi boş olur. Bu, performansı geliştirmek için tasarım gereğidir. Bu listeye kişi eklemek için, arama kutusuna bir ad (en az 3 karakter) yazın.

   1. **siteler SharePoint** - **Siteleri seç'e** tıklayın ve sonra SharePoint belirtmek ve ayrı tutulacak siteleri OneDrive İş için siteleri yeniden **seçin'e** tıklayın. Beklemeye almak istediğiniz her sitenin URL'sini yazın. Microsoft 365 Grubu veya Microsoft Ekibi için SharePoint sitesinin URL'sini de ekleyebilirsiniz. **Seç'e** ve ardından **Bitti'ye** tıklayın.

      > [!NOTE]
      > Kullanıcının OneDrive hesabının URL'si, kullanıcı asıl adını (UPN) içerir (örneğin, `https://alpinehouse-my.sharepoint.com/personal/sarad_alpinehouse_onmicrosoft_com`). Bir kişinin UPN'sinin değişmesi nadir durumlarda, OneDrive URL'si de yeni UPN'yi içerecek şekilde değişir. Bir kullanıcının OneDrive hesabı gözetimsiz tutmanın bir parçasıysa ve UPN'si değiştirildiyse, saklamayı güncelleştirmeniz ve yeni OneDrive URL'sine işaret etmeniz gerekir. Daha fazla bilgi için bkz[. UPN değişiklikleri OneDrive URL'sini nasıl etkiler](/onedrive/upn-changes)?

   1. **Ortak klasörleri Exchange** - Exchange Online kuruluşunuzdaki tüm ortak klasörleri beklemeye almak için iki durumlu düğmeyi Tümü konumuna getirin. Beklemeye almak için belirli ortak klasörleri seçemezsiniz. Ortak klasörlere ayrı tutmak istemiyorsanız iki durumlu düğmeyi **Yok** olarak bırakın.

9. Ayrı tutmaya içerik konumları eklemeyi bitirdiğinizde **İleri'ye** tıklayın.
  
10. Koşullarla sorgu tabanlı ayrı tutma oluşturmak için aşağıdakileri tamamlayın. Aksi takdirde **İleri'ye** tıklamak gerekir.

    - **Anahtar Sözcükler'in** altındaki kutuya, yalnızca arama ölçütlerini karşılayan içeriğin ayrı tutulması için kutuya bir arama sorgusu yazın. Anahtar sözcükleri, ileti özelliklerini veya dosya adları gibi belge özelliklerini belirtebilirsiniz. Ayrıca VE, OR veya NOT gibi boole işleci kullanan daha karmaşık sorgular da kullanabilirsiniz. Anahtar sözcük kutusunu boş bırakırsanız, belirtilen içerik konumlarında bulunan tüm içerik beklemeye alınır.

    - Ayrı tutma için arama sorgusunu daraltmak üzere bir veya daha fazla koşul eklemek için Koşul  **ekle'ye** tıklayın. Her koşul, ayrı tutma oluşturduğunuzda oluşturulan ve çalıştırılan KQL arama sorgusuna bir yan tümce ekler. Örneğin, tarih aralığı içinde oluşturulan e-posta veya site belgelerinin beklemeye alınabilmesi için bir tarih aralığı belirtebilirsiniz. Koşul, AND işleci tarafından anahtar sözcük sorgusuna (anahtar sözcük kutusunda belirtilen) mantıksal olarak bağlanır. Bu, öğelerin hem anahtar sözcük sorgusunu hem de beklemeye alınması gereken koşulu karşılaması gerektiğini gösterir.

     Arama sorgusu oluşturma ve koşulları kullanma hakkında daha fazla bilgi için bkz [. İçerik Arama için anahtar sözcük sorguları ve arama koşulları](/office365/SecurityCompliance/keyword-queries-and-search-conditions).

11. Sorgu tabanlı ayrı tutmayı yapılandırdıktan sonra **İleri'ye** tıklayın.

12. Ayarlarınızı gözden geçirin ve **ardından Bu ayrı tutmayı oluştur'a** tıklayın.

> [!NOTE]
> Sorgu tabanlı ayrı tutma oluşturduğunuzda, seçilen konumlardaki tüm içerik başlangıçta beklemeye alınır. Daha sonra, belirtilen sorguyla eşleşmeyen tüm içerikler her yedi ila 14 günde bir ayrı tutmadan temizlenir. Ancak, bir içerik konumuna herhangi bir türde beşten fazla ayrı tutma uygulandığında veya herhangi bir öğede dizin oluşturma sorunları varsa sorgu tabanlı ayrı tutma içeriği temizlemez.

> [!NOTE]
> Kullanıcının posta kutusunu beklemeye aldıktan sonra kullanıcının SMTP adresi değişirse, posta kutusu beklemede kalır. Yeni SMTP adresini ayrı tutmak üzere kullanmak için yeni bir ayrı tutma oluşturun.

## <a name="view-hold-statistics"></a>Ayrı tutma istatistiklerini görüntüleme

Bir süre sonra, yeni ayrı tutmayla ilgili bilgiler, seçili ayrı tutmanın **Ayrı Tutmalar** sekmesindeki ayrıntılar bölmesinde görüntülenir. Bu bilgiler, ayrı tutmadaki posta kutularının ve sitelerin sayısını ve ayrı tutmaya alınan içeriğin toplam sayısı ve boyutu ve ayrı tutma istatistiklerinin son hesaplanma zamanı gibi istatistikleri içerir. Bu saklama istatistikleri, eBulma olayıyla ilgili ne kadar içeriğin tutulduğunu belirlemenize yardımcı olur.

Bekletme istatistikleri hakkında aşağıdaki şeyleri aklınızda bulundurun:

- Ayrı tutmadaki öğelerin toplam sayısı, beklemeye alınan tüm içerik kaynaklarından gelen öğelerin sayısını gösterir. Sorgu tabanlı bir ayrı tutma oluşturduysanız, bu istatistik sorguyla eşleşen öğelerin sayısını gösterir.
  
- Ayrı tutmadaki öğelerin sayısı, içerik konumlarında bulunan dizine alınmamış öğeleri de içerir. Sorgu tabanlı ayrı tutma oluşturursanız, içerik konumlarındaki tüm dizinlenmemiş öğeler beklemeye alınır. Bu, sorgu tabanlı ayrı tutmanın arama ölçütlerine uymayan dizinlenmemiş öğeleri ve tarih aralığı koşulunun dışında kalan dizine alınmamış öğeleri içerir. Bu, arama sorgusuyla eşleşmeyen veya bir tarih aralığı koşulu tarafından dışlanan dizine alınmamış öğelerin arama sonuçlarına dahil edilmediği bir İçerik Araması çalıştırdığınızda gerçekleşenlerden farklıdır. Dizine alınmamış öğeler hakkında daha fazla bilgi için bkz. [Office 365'da İçerik Arama'da kısmen dizine alınmış öğeler](partially-indexed-items-in-content-search.md).

- Beklemedeki geçerli öğe sayısını hesaplayan bir arama tahminini yeniden çalıştırmak için İstatistikleri güncelleştir'e tıklayarak en son saklama istatistiklerini alabilirsiniz.

- Gerekirse, ayrıntılar bölmesinde ayrı tutma istatistiklerini güncelleştirmek için araç çubuğunda Yenile'ye tıklayın.

- Posta kutusu veya sitesi beklemede olan kullanıcılar genellikle yeni e-posta iletisi gönderip aldığından ve yeni SharePoint ve OneDrive İş belgeleri oluşturduğundan, beklemedeki öğelerin sayısının zaman içinde artması normaldir.

- bir SharePoint sitesi veya OneDrive hesabı çok coğrafi bir ortamda farklı bir bölgeye taşınırsa, söz konusu sitenin istatistikleri ayrı tutma istatistiklerine dahil edilmeyecektir. Ancak, sitedeki içerik hala beklemede olacaktır. Ayrıca, bir site farklı bir bölgeye taşınırsa, ayrı tutmada görüntülenen URL güncelleştirilmez. Bekletmeyi düzenlemeniz ve URL'yi güncelleştirmeniz gerekir.

## <a name="place-a-hold-on-microsoft-teams-and-office-365-groups"></a>Microsoft Teams ve Office 365 Gruplarına ayrı tutma

Microsoft Teams Office 365 Grupları'nda oluşturulur. Bu nedenle, bunları eBulma'da (Premium) beklemeye alma işlemi benzerdir.

- **Nasıl yaparım? ek bir Microsoft 365 Grupları veya Microsoft Teams siteyi bir bekçiyle eşler misiniz? Peki ya Microsoft 365 Grupları ve Microsoft Teams gözetimsiz bir saklamaya ne dersin?** Microsoft Teams Microsoft 365 Grupları üzerine kurulmuştur. Bu nedenle, bunları eBulma durumunda beklemeye alma benzerdir. Microsoft 365 Grupları ve Microsoft Teams beklemeye alırken aşağıdakileri göz önünde bulundurun.

  - İçeriği Microsoft 365 Grupları ve Microsoft Teams ayrı tutmak için, bir grup veya ekiple ilişkili posta kutusunu ve SharePoint sitesini belirtmeniz gerekir.
  
  - Microsoft 365 Grubu veya Microsoft Ekibi özelliklerini görüntülemek için Exchange Online'da **Get-UnifiedGroup** cmdlet'ini çalıştırın. Bu, Microsoft 365 Grubu veya Microsoft Ekibi ile ilişkili sitenin URL'sini almak için iyi bir yoldur. Örneğin, aşağıdaki komut Kıdemli Liderlik Ekibi adlı bir Microsoft 365 Grubu için seçili özellikleri görüntüler:

    ```console
    Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl
    DisplayName            : Senior Leadership Team
    Alias                  : seniorleadershipteam
    PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
    SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
    ```

    > [!NOTE]
    > Get-UnifiedGroup cmdlet'ini çalıştırmak için, Exchange Online'da View-Only Alıcılar rolüne atanmış olmanız veya View-Only Alıcılar rolüne atanmış bir rol grubunun üyesi olmanız gerekir.

  - Kullanıcının posta kutusu arandığında, kullanıcının üyesi olduğu Microsoft 365 Grubu veya Microsoft Ekibi aranmayacak. Benzer şekilde, bir Microsoft 365 Grubu veya Microsoft Ekibini ayrı tuttuğunuzda, yalnızca grup posta kutusu ve grup sitesi beklemeye alınır; grup üyelerinin posta kutuları ve OneDrive İş siteleri, bunları açıkça koruyucu olarak eklemediğiniz veya veri kaynaklarını ayrı tutmadığınız sürece ayrı tutmaz. Bu nedenle, belirli bir koruyucu için bir Microsoft 365 Grubu veya Microsoft Ekibini beklemeye almanız gerekiyorsa, grup sitesini ve grup posta kutusunu koruyucuya eşlemeyi göz önünde bulundurun (bkz. eBulma'da Koruyucuları Yönetme (Premium)). Microsoft 365 Grubu veya Microsoft Ekibi tek bir koruyucuya atanamazsa, kaynağı gözetimsiz bir saklamaya eklemeyi göz önünde bulundurun.
  - Microsoft 365 Grubu veya Microsoft Ekibi üyelerinin listesini almak için, özellikleri Microsoft 365 yönetim merkezi **Ev** >  [**Grupları**](https://go.microsoft.com/fwlink/p/?linkid=2052855) sayfasında görüntüleyebilirsiniz. Alternatif olarak, Exchange Online PowerShell'de aşağıdaki komutu çalıştırabilirsiniz:

    ```powershell
    Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
    ```

    > [!NOTE]
    > **Get-UnifiedGroupLinks** cmdlet'ini çalıştırmak için, Exchange Online'da View-Only Alıcılar rolüne veya View-Only Alıcılar rolüne atanmış bir rol grubunun üyesi olmanız gerekir.

  - Microsoft Teams kanalın parçası olan kanal konuşmaları, Ekiple ilişkili posta kutusunda depolanır. Benzer şekilde, ekip üyelerinin kanalda paylaştığı dosyalar ekibin SharePoint sitesinde depolanır. Bu nedenle, konuşmaları ve dosyaları bir kanalda tutmak için Microsoft Team posta kutusunu ve SharePoint sitesini beklemeye alsanız iyi olur.
  
  - Alternatif olarak, Microsoft Teams'daki Sohbet listesinin bir parçası olan konuşmalar, sohbete katılan kullanıcının posta kutusunda depolanır.  Kullanıcının Sohbet konuşmalarında paylaştığı dosyalar, dosyayı paylaşan kullanıcının OneDrive İş sitesinde depolanır. Bu nedenle, sohbetleri ve dosyaları Sohbet listesinde tutmak için tek tek kullanıcı posta kutularını ve OneDrive İş siteleri ayrı ayrı beklemeye alsanız iyi olur.
  
  - Her Microsoft Ekibi veya ekip kanalı, not alma ve işbirliği için bir Wiki içerir. Wiki içeriği otomatik olarak .mht biçiminde bir dosyaya kaydedilir. Bu dosya, ekibin SharePoint sitesindeki Teams Wiki Verileri belge kitaplığında depolanır. Ekibin SharePoint sitesini beklemeye alarak wiki'deki içeriği beklemeye alabilirsiniz.

    > [!NOTE]
    > Bir Microsoft Ekibi veya ekip kanalı için Wiki içeriğini saklama özelliği (ekibin SharePoint sitesini beklemeye aldığınızda) 22 Haziran 2017'de yayımlandı. Bir ekip sitesi beklemedeyse, Wiki içeriği bu tarihten itibaren korunur. Ancak, bir ekip sitesi beklemedeyse ve Wiki içeriği 22 Haziran 2017'dan önce silinmişse, Wiki içeriği korunmaz.
