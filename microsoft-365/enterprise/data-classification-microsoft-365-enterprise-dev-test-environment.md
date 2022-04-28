---
title: Kurumsal test ortamı için Microsoft 365 veri sınıflandırması
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-security-compliance
ms.custom:
- Ent_TLGs
- admindeeplinkMAC
- admindeeplinkDEFENDER
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Kurumsal test ortamınız için Microsoft 365 belgeler üzerinde bekletme etiketleri oluşturmak ve kullanmak için bu Test Laboratuvarı Kılavuzu'nu kullanın.
ms.openlocfilehash: f5bcde88be148ed883b4ad10e3b8116ed21c9fa8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096820"
---
# <a name="data-classification-for-your-microsoft-365-for-enterprise-test-environment"></a>Kurumsal test ortamı için Microsoft 365 veri sınıflandırması

*Bu Test Laboratuvarı Kılavuzu hem kurumsal hem de Office 365 Kurumsal test ortamları için Microsoft 365 için kullanılabilir.*

Bu makalede, kurumsal test ortamınız için Microsoft 365 bekletme etiketlerini kullanarak veri sınıflandırmasını yapılandırma işlemi açıklanmaktadır.

Test ortamınızdaki verileri sınıflandırmak üç aşamayı içerir:
- [1. Aşama: Kurumsal test ortamı için Microsoft 365 oluşturma](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [2. Aşama: Bekletme etiketleri oluşturma](#phase-2-create-retention-labels)
- [3. Aşama: Belgelere bekletme etiketleri uygulama](#phase-3-apply-retention-labels-to-documents)

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınındaki Microsoft 365 tüm makalelere yönelik görsel bir harita için [kurumsal Test Laboratuvarı Kılavuzu Yığını için Microsoft 365](../downloads/Microsoft365EnterpriseTLGStack.pdf) bölümüne gidin.
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>1. Aşama: Kurumsal test ortamı için Microsoft 365 oluşturma

Bekletme etiketlerini yalnızca minimum gereksinimlerle basit bir şekilde yapılandırmak istiyorsanız [Basit temel yapılandırma](lightweight-base-configuration-microsoft-365-enterprise.md) yönergelerini izleyin.
  
Sanal bir kuruluşta bekletme etiketlerini yapılandırmak istiyorsanız Doğrudan [kimlik doğrulaması](pass-through-auth-m365-ent-test-environment.md) başlığı altında yer alan yönergeleri izleyin.
  
> [!NOTE]
> Bekletme etiketlerini test etmek için, İnternet'e bağlı bir sanal intranet ve bir Active Directory Domain Services (AD DS) ormanı için dizin eşitlemesi içeren sanal kurumsal test ortamı gerekmez. Burada, otomatik lisanslama ve grup üyeliğini test edebilmeniz ve tipik bir kuruluşu temsil eden bir ortamda denemeler yapabileceğiniz bir seçenek olarak sağlanır.

## <a name="phase-2-create-retention-labels"></a>2. Aşama: Bekletme etiketleri oluşturma

Bu aşamada, SharePoint Çevrimiçi belgeler klasörleri için farklı bekletme düzeyleri için bekletme etiketlerini oluşturun:

1. genel yönetici hesabınızla <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalında</a> oturum açın.
1. **Tarayıcınızın Giriş - Microsoft 365 güvenlik** sekmesinde **ClassificationRetention** >  etiketleri'ni seçin.
1. **Etiket oluştur'u** seçin.
1. **Etiketinizi adlandırın** bölmesinde, **Etiketinizi adlandırın** alanına **İç Genel** yazın ve **İleri'yi** seçin.
1. **Dosya planı tanımlayıcıları** bölmesinde **İleri'yi** seçin.
1. **Etiket ayarları** bölmesinde gerekirse **Bekletme'yi** **Açık** olarak ayarlayın ve **İleri'yi** seçin.
1. **Ayarlarınızı gözden geçirin** bölmesinde **Etiketi oluştur'u** seçin.
1. Bu adlara sahip ek etiketler için 3-7 arası adımları yineleyin:
  - Özel
  - Hassas
  - Çok Gizli
1. **Bekletme etiketleri** bölmesinde **Etiketleri yayımla'yı** seçin.
1. **Yayımlamak için etiketleri seçin** bölmesinde **Yayımlayacak etiketleri seçin'i** seçin.
1. **Etiket seç** bölmesinde **Ekle'yi** seçin ve dört etiketi de seçin.
1. **Ekle'yi** ve ardından **Bitti'yi** seçin.
1. **Yayımlayacak etiketleri seçin** bölmesinde **İleri'yi** seçin.
1. **Konumları seçin** bölmesinde **İleri'yi** seçin.
1. **İlkenizi adlandırın** bölmesinde, **Ad** alanına **Örnek kuruluş** yazın ve **İleri'yi** seçin.
1. **Ayarlarınızı gözden geçirin** bölmesinde **Etiketleri yayımla'yı** seçin.
 
Bekletme etiketlerinin yayımlanması birkaç dakika sürebilir.

## <a name="phase-3-apply-retention-labels-to-documents"></a>3. Aşama: Belgelere bekletme etiketleri uygulama

Bu aşamada, SharePoint Online sitesinin Belgeler klasöründeki dosyalar için varsayılan bekletme etiketi davranışını keşfeder ve belgenin bekletme etiketini el ile değiştirirsiniz.

İlk olarak, hassas düzeyde bir SharePoint Çevrimiçi ekip sitesi oluşturun:
  
1. Tarayıcınızın özel bir örneğini kullanarak genel yönetici hesabınızı kullanarak <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> oturum açın.
1. Kutucuk listesinde **SharePoint'ı** seçin.
1. Tarayıcınızdaki yeni **SharePoint** sekmesinde **Site oluştur'u** seçin.
1. **Site oluştur** sayfasında **Ekip sitesi'ni** seçin.
1. **Ekip sitesi adı** kutusuna **SensitiveFiles** yazın.
1. **Ekip sitesi açıklaması** kutusuna **hassas dosyalar için SharePoint site** girin.
1. **Gizlilik ayarları'nda** **Özel - yalnızca üyeler bu siteye erişebilir'i** seçin ve ardından **İleri'yi** seçin.
1. **Eklemek istediğiniz Who?** bölmesinde **Son'u** seçin.
    
Ardından, SensitiveFiles ekip sitesinin Belgeler klasörünü Hassas saklama etiketi için yapılandırın.
  
1. Tarayıcınızın **SensitiveFiles** sekmesinde **Belgeler'i** seçin.
1. **Ayarlar** simgesini ve ardından **Kitaplık ayarları'nı** seçin.
1. **İzinler ve Yönetim** altında **, Bu liste veya kitaplıktaki öğelere etiket uygula'yı** seçin. Bu seçenek görünmüyorsa bekletme etiketleriniz henüz yayımlanmaz. Bu adımı daha sonra deneyin.
1. **Ayarlar Etiketi Uygula'da**, açılan **kutudan Hassas'ı** ve ardından **Kaydet'i** seçin.

Ardından, SensitiveFiles sitesinde yeni bir belge oluşturun ve bekletme etiketini değiştirin.
    
1. Belgeler klasöründe **YeniWord** **belgesi'ni** >  seçin.
1. Boş belgeye metin girin. Metnin kaydedilmesini bekleyin.
1. Menü çubuğunda **Paylaşılan Belgeler'i** seçin.
1. **Document.docx** dosya adının yanında dikey üç noktayı ve ardından **Ayrıntılar'ı** seçin.
1. Sağ bölmedeki **Özellikler** bölümünde, **Bekletme etiketini uygula'nın** altında, belgenin **Hassas** saklama etiketinin otomatik olarak uygulandığını unutmayın.
1. **Tümünü düzenle'ye** tıklayın.
1. **Document.docx** bölmesinde, **Bekletme etiketi uygula'nın** altında **Son Derece Gizli** etiketini ve ardından **Kaydet'i** seçin.

## <a name="next-step"></a>Sonraki adım

Test ortamınızdaki ek [bilgi koruma](m365-enterprise-test-lab-guides.md#information-protection) özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Kurumsal Test Laboratuvarı Kılavuzları için Microsoft 365](m365-enterprise-test-lab-guides.md)

[Microsoft 365 Kurumsal’a genel bakış](microsoft-365-overview.md)

[Kurumsal belgeler için Microsoft 365](/microsoft-365-enterprise/)
