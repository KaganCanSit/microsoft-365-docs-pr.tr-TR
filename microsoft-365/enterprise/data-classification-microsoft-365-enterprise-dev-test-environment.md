---
title: Kurumsal test ortamınız için Microsoft 365 sınıflandırması
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Kurumsal test ortamı için test ortamınıza uygun olarak belgelerde bekletme etiketleri oluşturmak Microsoft 365 için bu Test Laboratuvarı Kılavuzunu kullanın.
ms.openlocfilehash: 3cb3a07b4f636fcf8770432a825356269ff6d94c
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006331"
---
# <a name="data-classification-for-your-microsoft-365-for-enterprise-test-environment"></a>Kurumsal test ortamınız için Microsoft 365 sınıflandırması

*Bu Test Laboratuvarı Kılavuzu, hem kurumsal hem de Microsoft 365 test ortamları için Office 365 Kurumsal kullanılabilir.*

Bu makalede, kurumsal test ortamı için çalışma alanlarınızı bekletme etiketlerini kullanarak Microsoft 365 yapılandırma işlemi açıklanmıştır.

Test ortamınıza verileri sınıflendirmek için üç aşama gerekir:
- [Aşama 1: Kurumsal test Microsoft 365 yapınızı oluşturma](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Aşama 2: Bekletme etiketleri oluşturma](#phase-2-create-retention-labels)
- [Aşama 3: Belgelere bekletme etiketleri uygulama](#phase-3-apply-retention-labels-to-documents)

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınına Microsoft 365 görsel bir harita için Kurumsal Test Laboratuvarı Kılavuzu Yığını [için Microsoft 365'e gidin](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Aşama 1: Kurumsal test Microsoft 365 yapınızı oluşturma

Bekletme etiketlerini en düşük gereksinimlerle basit bir şekilde yapılandırmak istemiyorsanız, Basit temel [yapılandırma'daki yönergeleri izleyin](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Sanal bir kuruluşta bekletme etiketlerini yapılandırmak için, Geçişli kimlik [doğrulama'daki yönergeleri izleyin](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Bekletme etiketlerini test etmek, Active Directory Etki Alanı Hizmetleri (AD DS) ormanı için İnternet ve dizin eşitlemeye bağlı sanal bir intranet içeren sanal kurumsal test ortamı gerektirmez. Burada, otomatik lisanslama ve grup üyeliğini test etmek ve normal bir kuruluşu temsil eden bir ortamda bu üyelikle denemeler yapmak için bir seçenek olarak sağlanmıştır.

## <a name="phase-2-create-retention-labels"></a>Aşama 2: Bekletme etiketleri oluşturma

Bu aşamada, SharePoint Online belgeler klasörleri için farklı bekletme düzeyleri için bekletme etiketleri oluşturun:

1. Genel yönetici <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">hesabınızla Microsoft 365 Defender portalında</a> oturum açın.
1. Tarayıcınızın **Giriş - Microsoft 365 sekmesinde** **SınıflandırmaRetention etiketleri'ne** >  tıklayın.
1. Etiket **oluştur'a seçin**.
1. Etiketinizi **adla bölmesinde** , Etiketinizi **adla alanına** İç Genel **girin ve** Ardından Sonraki'yi **seçin**.
1. Dosya **planı tanımlayıcılar bölmesinde Sonraki'ni** **seçin**.
1. Etiket ayarları **bölmesinde gerekirse** , Bekletme'yi Aç **olarak ayarlayın** **ve** ardından Sonraki'yi **seçin**.
1. Ayarlarınızı **gözden geçirme bölmesinde** Etiket **oluştur'a tıklayın**.
1. Bu adlara sahip ek etiketler için 3-7. adımları yinelayın:
  - Özel
  - Hassas
  - Çok Gizli
1. Bekletme etiketleri **bölmesinde Etiketleri** yayımla'yı **seçin**.
1. Yayımlayacak **etiketleri seçin bölmesinde Yayımlayacak** etiketleri **seç'i seçin**.
1. Etiket **seç bölmesinde Ekle'yi** seçin **ve** dört etiketin hepsini seçin.
1. **Ekle'yi** ve ardından **Bitti'yi seçin**.
1. Yayımlayacak **etiketleri seçin bölmesinde Sonraki'yi** **seçin**.
1. Konumları **seçin bölmesinde Sonraki'yi** **seçin**.
1. **İlkenizi adla bölmesinde**, Ad **alanına Örnek** kuruluş **girin** ve ardından Sonraki'yi **seçin**.
1. Ayarlarınızı gözden **geçirme bölmesinde Etiketleri** yayımla'yı **seçin**.
 
Bekletme etiketlerinin yayım olması birkaç dakika sürebilir.

## <a name="phase-3-apply-retention-labels-to-documents"></a>Aşama 3: Belgelere bekletme etiketleri uygulama

Bu aşamada, bir SharePoint Online sitenin Belgeler klasöründeki dosyalar için varsayılan bekletme etiketi davranışını keşfeder ve belgenin bekletme etiketini el ile değiştirirsiniz.

İlk olarak, hassas düzeyde bir SharePoint Online ekip sitesi oluşturun:
  
1. Tarayıcınızın özel bir örneğini kullanarak genel yönetici <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> tarayıcınızda oturum açın.
1. Kutucuklar listesinde, Kutucuklar'ı **SharePoint**.
1. Tarayıcınızdaki **yeni SharePoint** Site **oluştur'a tıklayın**.
1. Site **oluşturma sayfasında Ekip** **sitesi'ne tıklayın**.
1. Ekip **sitesi adı kutusuna** **SensitiveFiles girin**.
1. Ekip **sitesi açıklaması kutusuna** hassas dosyalar **SharePoint siteyi girin**.
1. Gizlilik **ayarlarından** Özel **- yalnızca üyeler bu siteye erişeni seçin ve** sonra da Sonraki'yi **seçin**.
1. Eklemek **Who istiyor musunuz? bölmesinde Son'a** **tıklayın**.
    
Ardından, Hassas bekletme etiketi için SensitiveFiles ekip sitesinde Belgeler klasörünü yapılandırabilirsiniz.
  
1. Tarayıcınızın **SensitiveFiles** sekmesinde Belgeler'i **seçin**.
1. Çalışma **Ayarlar ve** ardından Kitaplık **ayarları'ı seçin**.
1. **İzinler ve Yönetim'in** altında, **Bu liste veya kitaplıkta yer alan öğelere etiket uygula'ya tıklayın**. Bu seçenek göster görünmezse, bekletme etiketleriniz henüz yayımlanmadı. Daha sonra bu adımı deneyin.
1. Etiket **Ayarlar'de**, açılan **kutuda Hassas'ı** seçin ve sonra da Kaydet'i **seçin**.

Ardından, SensitiveFiles sitesinde yeni bir belge oluşturun ve bekletme etiketini değiştirebilirsiniz.
    
1. Belgeler klasöründe **NewWord belgesi'ni** >  seçin.
1. Boş belgeye bir metin girin. Metnin kaydedildisini bekleyin.
1. Menü çubuğunda Paylaşılan **Belgeler'i seçin**.
1. Dosya adının **Document.docx** , dikey üç noktayı ve sonra Ayrıntılar'ı **seçin**.
1. Sağ bölmede, Özellikler **bölümündeki** Bekletme etiketini uygula'nın **altında, belgede** Hassas bekletme etiketinin otomatik **olarak uygulandığını** unutmayın.
1. Hepsini **düzenle'ye tıklayın**.
1. Gizli **Document.docx,** Bekletme etiketini **uygula'nın altında** Çok Gizli etiketi seçin **ve** sonra da Kaydet'i **seçin**.

## <a name="next-step"></a>Sonraki adım

Test [ortamınıza ek](m365-enterprise-test-lab-guides.md#information-protection) bilgi koruma özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar](m365-enterprise-test-lab-guides.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Microsoft 365 belgeleri için belgeler](/microsoft-365-enterprise/)
