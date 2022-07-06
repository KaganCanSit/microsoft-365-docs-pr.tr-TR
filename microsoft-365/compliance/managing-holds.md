---
title: eBulma'da ayrı tutmaları yönetme (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 04/27/2022
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
ms.openlocfilehash: f7c47afe74c4d48036160d0fbb0c9717f884bc46
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629453"
---
# <a name="manage-holds-in-ediscovery-premium"></a>eBulma'da ayrı tutmaları yönetme (Premium)

Bir Microsoft Purview eKeşif (Premium) servis talebi kullanarak, servis talebinizle ilgili olabilecek içeriği korumak üzere ayrı tutmalar oluşturabilirsiniz. eBulma (Premium) tutma özelliklerini kullanarak, saklamaları koruyuculara ve veri kaynaklarına yerleştirebilirsiniz. Ayrıca, posta kutularına ve OneDrive İş sitelerine gözetimsiz bir saklama yerleştirebilirsiniz. Microsoft 365 Grubu için grup posta kutusuna, SharePoint sitesine ve OneDrive İş sitesine de ayrı tutabilirsiniz. Benzer şekilde, Microsoft Teams ile ilişkili posta kutusuna ve siteye ayrı tutabilirsiniz. İçerik konumlarını beklemeye aldığınızda, siz koruyucuyu serbest bırakana, belirli bir veri konumunu kaldırana veya saklama ilkesini tamamen silene kadar içerik tutulur.

## <a name="manage-custodian-based-holds"></a>Koruyucu tabanlı ayrı tutmaları yönetme

Bazı durumlarda, tanımladığınız ve olay sırasında verilerini korumaya karar vermiş bir dizi koruyucunuz olabilir. eBulma'da (Premium) bu koruyucular beklemeye alındığında, kullanıcı ve onun seçtiği veri kaynakları otomatik olarak bir koruyucu saklama ilkesine eklenir.

Koruyucu tutma ilkesini görüntülemek için:

1. Microsoft Purview uyumluluk portalı, kuruluşunuzdaki servis taleplerinin listesini görüntülemek için **eBulma > Gelişmiş'e** tıklayın.

2. Servis talebinize koruyucular eklemek için **Kaynaklar** sekmesine gidin. Bir eKeşif (Premium) olayı içinde koruyucuları nasıl ekleyip beklemeye alacağınızı öğrenmek için bkz. [Servis talebine Koruyucu ekleme](add-custodians-to-case.md). Koruyucuları zaten ekleyip beklemeye aldıysanız 3. adıma gidin.

3. **Ayrı Tutmalar** sekmesine gidin ve **CustodianHold'a\<HoldId>** tıklayın.

4. Açılır sayfada, koruyucu tabanlı saklamanıza sorgu uygulama gibi eylemler gerçekleştirebilirsiniz. Ayrı tutma sorgusu oluşturma ve koşulları kullanma hakkında daha fazla bilgi için bkz [. İçerik Arama için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).

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

   1. **Exchange e-postası** - **Kullanıcıları, grupları veya ekipleri seç'e** tıklayın ve sonra beklemeye eklenecek posta kutularını belirtmek için **Kullanıcıları, grupları veya ekipleri yeniden seç'e** tıklayın. Kullanıcı posta kutularını ve dağıtım gruplarını bulmak için arama kutusunu kullanın (grup üyelerinin posta kutularına ayrı tutma yerleştirmek için). Microsoft 365 Grubu veya Microsoft Ekibi için ilişkili posta kutusuna ayrı tutma da yapabilirsiniz. Kullanıcı, grup, ekip onay kutusunu seçin, **Seç'e** ve ardından **Bitti'ye** tıklayın.

      > [!NOTE]
      > Beklemeye alınacak posta kutularını belirtmek için **Kullanıcıları, grupları veya ekipleri seçin'e** tıkladığınızda, görüntülenen posta kutusu seçicisi boş olur. Bu, performansı geliştirmek için tasarım gereğidir. Bu listeye kişi eklemek için, arama kutusuna bir ad (en az 3 karakter) yazın.

   1. **SharePoint Siteleri** - **Site seç'e** tıklayın ve sonra SharePoint'i belirtmek ve ayrı tutulacak siteleri OneDrive İş için Siteleri yeniden **seç'e** tıklayın. Beklemeye almak istediğiniz her sitenin URL'sini yazın. Microsoft 365 Grubu veya Microsoft Ekibi için SharePoint sitesinin URL'sini de ekleyebilirsiniz. **Seç'e** ve ardından **Bitti'ye** tıklayın.

      > [!NOTE]
      > Kullanıcının OneDrive hesabının URL'si, kullanıcı asıl adını (UPN) içerir (örneğin, `https://alpinehouse-my.sharepoint.com/personal/sarad_alpinehouse_onmicrosoft_com`). Bir kişinin UPN'sinin değişmesi nadir durumlarda OneDrive URL'si de yeni UPN'yi içerecek şekilde değişir. Bir kullanıcının OneDrive hesabı gözetimsiz bir saklamanın parçasıysa ve UPN'si değiştirildiyse, ayrı tutmayı güncelleştirmeniz ve yeni OneDrive URL'sine işaret etmeniz gerekir. Daha fazla bilgi için bkz [. UPN değişiklikleri OneDrive URL'sini nasıl etkiler](/onedrive/upn-changes)?

   1. **Ortak klasörleri değiştirme** - Exchange Online kuruluşunuzdaki tüm ortak klasörleri beklemeye almak için iki durumlu düğmeyi Tümü konumuna getirin. Beklemeye almak için belirli ortak klasörleri seçemezsiniz. Ortak klasörlere ayrı tutmak istemiyorsanız iki durumlu düğmeyi **Yok** olarak bırakın.

9. Ayrı tutmaya içerik konumları eklemeyi bitirdiğinizde **İleri'ye** tıklayın.
  
10. Koşullarla sorgu tabanlı ayrı tutma oluşturmak için aşağıdakileri tamamlayın. Aksi takdirde **İleri'ye** tıklamak gerekir.

    - **Anahtar Sözcükler'in** altındaki kutuya, yalnızca arama ölçütlerini karşılayan içeriğin ayrı tutulması için kutuya bir arama sorgusu yazın. Anahtar sözcükleri, ileti özelliklerini veya dosya adları gibi belge özelliklerini belirtebilirsiniz. Ayrıca VE, OR veya NOT gibi boole işleci kullanan daha karmaşık sorgular da kullanabilirsiniz. Anahtar sözcük kutusunu boş bırakırsanız, belirtilen içerik konumlarında bulunan tüm içerik beklemeye alınır.

    - Ayrı tutma için arama sorgusunu daraltmak üzere bir veya daha fazla koşul eklemek için Koşul  **ekle'ye** tıklayın. Her koşul, ayrı tutmayı oluşturduğunuzda oluşturulan ve çalıştırılan KQL arama sorgusuna bir yan tümce ekler. Örneğin, tarih aralığı içinde oluşturulan e-posta veya site belgelerinin beklemeye alınabilmesi için bir tarih aralığı belirtebilirsiniz. Koşul, AND işleci tarafından anahtar sözcük sorgusuna (anahtar sözcük kutusunda belirtilen) mantıksal olarak bağlanır. Bu, öğelerin hem anahtar sözcük sorgusunu hem de beklemeye alınması gereken koşulu karşılaması gerektiğini gösterir.

     Arama sorgusu oluşturma ve koşulları kullanma hakkında daha fazla bilgi için bkz [. İçerik Arama için anahtar sözcük sorguları ve arama koşulları](/office365/SecurityCompliance/keyword-queries-and-search-conditions).

11. Sorgu tabanlı ayrı tutmayı yapılandırdıktan sonra **İleri'ye** tıklayın.

12. Ayarlarınızı gözden geçirin ve **ardından Bu ayrı tutmayı oluştur'a** tıklayın.

> [!NOTE]
> Sorgu tabanlı ayrı tutma oluşturduğunuzda, seçilen konumlardaki tüm içerik başlangıçta beklemeye alınır. Exchange veya SharePoint'teki zamanlayıcı işi çalıştırıldıktan sonra, belirtilen sorguyla eşleşmeyen tüm içerikler ayrı tutmadan temizlenir. Tek bir konumdaki tüm sorgulardaki karakter sayısı 10.000 karakteri aştıktan sonra konumun tamamı beklemeye alınır. 

> [!NOTE]
> Kullanıcının posta kutusunu beklemeye aldıktan sonra kullanıcının SMTP adresi değişirse, posta kutusu beklemede kalır. Yeni SMTP adresini ayrı tutmak üzere kullanmak için yeni bir ayrı tutma oluşturun.

## <a name="place-a-hold-on-microsoft-teams-and-office-365-groups"></a>Microsoft Teams ve Office 365 Grupları'nda beklemeye alma

Microsoft Teams, Office 365 Grupları üzerine kurulmuştur. Bu nedenle, bunları eBulma'da (Premium) beklemeye alma benzerdir.

- **Ek bir Microsoft 365 Grupları veya Microsoft Teams sitesini bir koruyucuyla eşlemek Nasıl yaparım?? Peki Microsoft 365 Grupları ve Microsoft Teams'de Gözetimsiz bir saklamaya ne dersin?** Microsoft Teams, Microsoft 365 Grupları üzerine kurulmuştur. Bu nedenle, bunları eBulma durumunda beklemeye alma benzerdir. Microsoft 365 Grupları ve Microsoft Teams'i beklemeye alırken aşağıdakileri göz önünde bulundurun.

  - Microsoft 365 Grupları ve Microsoft Teams'de bulunan içeriği beklemeye almak için, bir grup veya ekiple ilişkili posta kutusunu ve SharePoint sitesini belirtmeniz gerekir.
  
  - Microsoft 365 Grubu veya Microsoft Team özelliklerini görüntülemek için Exchange Online'de **Get-UnifiedGroup** cmdlet'ini çalıştırın. Bu, bir Microsoft 365 Grubu veya Microsoft Ekibi ile ilişkili sitenin URL'sini almak için iyi bir yoldur. Örneğin, aşağıdaki komut Kıdemli Liderlik Ekibi adlı bir Microsoft 365 Grubu için seçili özellikleri görüntüler:

    ```console
    Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl
    DisplayName            : Senior Leadership Team
    Alias                  : seniorleadershipteam
    PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
    SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
    ```

    > [!NOTE]
    > Get-UnifiedGroup cmdlet'ini çalıştırmak için, Exchange Online'da View-Only Alıcılar rolüne atanmış olmanız veya View-Only Alıcılar rolüne atanmış bir rol grubunun üyesi olmanız gerekir.

  - Kullanıcının posta kutusu arandığında, kullanıcının üyesi olduğu herhangi bir Microsoft 365 Grubu veya Microsoft Ekibi aranmayacak. Benzer şekilde, bir Microsoft 365 Grubu veya Microsoft Team ayrı tutması yaptığınızda, yalnızca grup posta kutusu ve grup sitesi beklemeye alınır; grup üyelerinin posta kutuları ve OneDrive İş siteleri, bunları açıkça koruyucu olarak eklemediğiniz veya veri kaynaklarını ayrı tutmadığınız sürece ayrı tutmaz. Bu nedenle, belirli bir koruyucu için bir Microsoft 365 Grubunu veya Microsoft Ekibini beklemeye almanız gerekiyorsa, grup sitesini ve grup posta kutusunu koruyucuya eşlemeyi göz önünde bulundurun (Bkz. eBulma'da Koruyucuları Yönetme (Premium)). Microsoft 365 Grubu veya Microsoft Ekibi tek bir koruyucuya aktarılamazsa, kaynağı gözetimsiz bir saklamaya eklemeyi göz önünde bulundurun.
  - Microsoft 365 Grubu veya Microsoft Ekibi üyelerinin listesini almak için, özellikleri Microsoft 365 yönetim merkezi **Giriş** > [**Grupları**](https://go.microsoft.com/fwlink/p/?linkid=2052855) sayfasında görüntüleyebilirsiniz. Alternatif olarak, Exchange Online PowerShell'de aşağıdaki komutu çalıştırabilirsiniz:

    ```powershell
    Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
    ```

    > [!NOTE]
    > **Get-UnifiedGroupLinks** cmdlet'ini çalıştırmak için, Exchange Online'da View-Only Alıcılar rolüne veya View-Only Alıcılar rolüne atanmış bir rol grubunun üyesi olmanız gerekir.

  - Microsoft Teams kanalının parçası olan kanal konuşmaları, Ekiple ilişkili posta kutusunda depolanır. Benzer şekilde, ekip üyelerinin kanalda paylaştığı dosyalar da ekibin SharePoint sitesinde depolanır. Bu nedenle, konuşmaları ve dosyaları bir kanalda tutmak için Microsoft Team posta kutusunu ve SharePoint sitesini beklemeye alsanız iyi olur.
  
  - Alternatif olarak, Microsoft Teams'deki Sohbet listesinin bir parçası olan konuşmalar, sohbete katılan kullanıcının posta kutusunda depolanır.  Kullanıcının Sohbet konuşmalarında paylaştığı dosyalar, dosyayı paylaşan kullanıcının OneDrive İş sitesinde depolanır. Bu nedenle, sohbetleri ve dosyaları Sohbet listesinde tutmak için tek tek kullanıcı posta kutularını ve OneDrive İş siteleri ayrı ayrı beklemeye alsanız iyi olur.
  
  - Her Microsoft Ekibi veya ekip kanalı, not alma ve işbirliği için bir Wiki içerir. Wiki içeriği otomatik olarak .mht biçiminde bir dosyaya kaydedilir. Bu dosya, ekibin SharePoint sitesindeki Teams Wiki Verileri belge kitaplığında depolanır. Ekibin SharePoint sitesini beklemeye alarak wiki'deki içeriği ayrı tutabilirsiniz.

    > [!NOTE]
    > Bir Microsoft Ekibi veya ekip kanalı için Wiki içeriğini saklama özelliği (ekibin SharePoint sitesini beklemeye aldığınızda) 22 Haziran 2017'de yayımlandı. Bir ekip sitesi beklemedeyse, Wiki içeriği bu tarihten itibaren korunur. Ancak, bir ekip sitesi beklemedeyse ve Wiki içeriği 22 Haziran 2017'dan önce silinmişse, Wiki içeriği korunmaz.
