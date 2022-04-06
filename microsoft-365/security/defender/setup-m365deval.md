---
title: Test laboratuvarı veya Microsoft 365 Defender ortamınızı ayarlama
description: Access Microsoft 365 Defender portalınıza ve ardından Microsoft 365 Defender laboratuvarı ortamınızı ayarlayın
keywords: Microsoft 365 Defender kurulumu, pilot Microsoft 365 Defender için deneme sürümü, Microsoft 365 Defender değerlendirme Microsoft 365 Defender laboratuvar kurulumunu deneyin
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 681d9798c6f16f5829bdb4e5272abc3eac719a59
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500991"
---
# <a name="set-up-your-microsoft-365-defender-trial-in-a-lab-environment"></a>Laboratuvar Microsoft 365 Defender testini ayarlama 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender 

Bu konu başlığı, özel bir laboratuvar ortamı ayarlamanız için size yol sunar. Üretimde denemeyi ayarlama hakkında bilgi için, yeni Değerlendirme ve [deneme sürümü Microsoft 365 Defender](eval-overview.md) bakın. 

## <a name="create-an-office-365-e5-trial-tenant"></a>Deneme Office 365 E5 oluşturma
>[!NOTE]
>Zaten bir Office 365 veya Azure Active Directory aboneliğiniz varsa deneme kiracısı oluşturma Office 365 E5 adımlarını atlayabilirsiniz.

1. [Office 365 E5 portalına gidin ve Ücretsiz](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab) **deneme'yi seçin**.

   :::image type="content" source="../../media/mtp-eval-9.png" alt-text="Ücretsiz Office 365 E5 sayfası" lightbox="../../media/mtp-eval-9.png":::
  
2. E-posta adresinizi (kişisel veya şirket) girerek deneme kaydını tamamlama. Hesap **ayarla'ya tıklayın**.

   :::image type="content" source="../../media/mtp-eval-10.png" alt-text="Office 365 E5 deneme kaydı kurulum sayfası" lightbox="../../media/mtp-eval-10.png":::

3. Ad, soyadı, iş telefon numarası, şirket adı, şirket boyutu ve ülke veya bölgenizi doldurun.  

   :::image type="content" source="../../media/mtp-eval-11.png" alt-text="Ad Office 365 E5 telefon ve şirket ayrıntılarını isteyen deneme sürümü kayıt kurulum sayfası" lightbox="../../media/mtp-eval-11.png":::
   
   > [!NOTE]
   > Burada ayarmış olacağınız ülke veya bölge, verilerinizin barındır Office 365 belirler.
  
4. Doğrulama tercihinizi seçin: SMS veya arama aracılığıyla. Doğrulama Kodu **Gönder'e tıklayın**. 

   :::image type="content" source="../../media/mtp-eval-12.png" alt-text="Doğrulama Office 365 E5 isteyen deneme sürümü kayıt kurulum sayfası" lightbox="../../media/mtp-eval-12.png":::

5. Kiracınız için özel etki alanı adını ayarlayın ve ardından Sonraki'ye **tıklayın**.

   :::image type="content" source="../../media/mtp-eval-13.png" alt-text="Özel Office 365 E5 adınızı ayar domain" lightbox="../../media/mtp-eval-13.png":::
 
6. Kiracı için Genel Yönetici olacak ilk kimliği ayarlayın. Ad ve **Parola'ya** **girin**. **Kaydol'a tıklayın**.

   :::image type="content" source="../../media/mtp-eval-14.png" alt-text="İş Office 365 E5 ayaryabilirsiniz deneme sürümü kayıt kurulum sayfası" lightbox="../../media/mtp-eval-14.png":::

7. Deneme **kiracısı hazırlama işlemini** tamamlamak için Office 365 E5 Git'e tıklayın.

   :::image type="content" source="../../media/mtp-eval-15.png" alt-text="Kuruluma Office 365 E5 düğmesinin tıklanması istemini alan deneme kaydı kurulum sayfası" lightbox="../../media/mtp-eval-15.png":::

8. Bağlan etki alanını bir kiracıya Office 365. [İsteğe bağlı] Zaten **Bağlan bir etki alanı seçin ve** etki alanı adınızı yazın. **İleri**'ye tıklayın.

   :::image type="content" source="../../media/mtp-eval-16.png" alt-text="Oturum Office 365 E5 e-postanızı kişiselleştirmeniz gereken Kurulum Sayfası" lightbox="../../media/mtp-eval-16.png":::
 
9. Etki alanı sahipliğini doğrulamak için bir TXT veya MX kaydı ekleyin. TXT veya MX kaydını etki alanınıza eklediktan sonra Doğrula'ya **seçin**.

   :::image type="content" source="../../media/mtp-eval-17.png" alt-text="Etki Office 365 E5 için BIR TXT /MX kaydı eklemeniz gereken Kurulum Ayarları sayfası" lightbox="../../media/mtp-eval-17.png":::
 
10. [İsteğe bağlı] Kiracınız için daha fazla kullanıcı hesabı oluşturun. İleri'ye tıklayarak bu adımı **atlayabilirsiniz**.

    :::image type="content" source="../../media/mtp-eval-18.png" alt-text="Daha Office 365 E5 kullanıcı ekleyebilirsiniz." lightbox="../../media/mtp-eval-18.png":::
 
11. [İsteğe bağlı] Diğer Office indirin. Bu **adımı atlamak** için İleri'ye tıklayın. 

    :::image type="content" source="../../media/mtp-eval-19.png" alt-text="Office 365 E5 uygulamalarınızı yükleyebilirsiniz Office sayfası" lightbox="../../media/mtp-eval-19.png":::

12. [İsteğe bağlı] E-posta iletilerini geçirme. Yine bu adımı atlayabilirsiniz.

    :::image type="content" source="../../media/mtp-eval-20.png" alt-text="E Office 365 E5 iletilerini geçirip geçirmeyebilirsiniz" lightbox="../../media/mtp-eval-20.png":::
 
13. Seç'çevrimiçi hizmetler. **Seçenekler'Exchange** Ardından Sonraki'ne **tıklayın**. 

    :::image type="content" source="../../media/mtp-eval-21.png" alt-text="Office 365 E5 seç8/122 çevrimiçi hizmetler" lightbox="../../media/mtp-eval-21.png":::

14. Etki alanınıza MX, CNAME ve TXT kayıtlarını ekleyin. Tamamlandığında Doğrula'ya **seçin**.

    :::image type="content" source="../../media/mtp-eval-22.png" alt-text="BURADAKI Office 365 E5 DNS kayıtlarınızı  eklersiniz" lightbox="../../media/mtp-eval-22.png":::
 
15. Tebrikler, kiracınız için hazırlamayı Office 365 tamamladınız.

    :::image type="content" source="../../media/mtp-eval-23.png" alt-text="The Office 365 E5 setup completion confirmation page" lightbox="../../media/mtp-eval-23.png":::
    

## <a name="enable-microsoft-365-trial-subscription"></a>Deneme Microsoft 365 aboneliğini etkinleştirme

>[!NOTE]
>Deneme sürümüne kaydolarak bir ay boyunca kullanabileceğiniz 25 kullanıcı lisansınız olur. Ayrıntılar [için bkz. Microsoft 365 abonelik deneme](../../commerce/try-or-buy-microsoft-365.md) veya satın alma.

1. Fatura [Microsoft 365 Yönetici'ne](https://admin.microsoft.com/) tıklayın **ve** Hizmet satın **alma'ya gidin**.

2. **Ücretsiz** Microsoft 365 E5'i seçin ve **Ücretsiz denemeyi başlat'a tıklayın**. 

   :::image type="content" source="../../media/mtp-eval-24.png" alt-text="Deneme Microsoft 365 E5 ücretsiz denemeyi başlat sayfası" lightbox="../../media/mtp-eval-24.png":::

3. Doğrulama tercihinizi seçin: SMS veya arama aracılığıyla. Karar verdiktan sonra telefon numarasını girin, seçiminize **bağlı olarak** Bana kısa mesaj at **veya Beni** ara'ya seçin.

   :::image type="content" source="../../media/mtp-eval-25.png" alt-text="Robot Microsoft 365 E5 kanıtlamak için kişi ayrıntılarını isteyen ücretsiz denemeyi başlat sayfasında bulabilirsiniz" lightbox="../../media/mtp-eval-25.png":::
 
4. Doğrulama kodunu girin ve Ücretsiz **denemenizi başlat'a tıklayın**.

   :::image type="content" source="../../media/mtp-eval-26.png" alt-text="Robot Microsoft 365 E5 için gönderilen doğrulama kodunu doldurabilirsiniz. Ücretsiz denemeyi başlat sayfası" lightbox="../../media/mtp-eval-26.png":::

5. **Denemenizi onaylamak için** Şimdi Microsoft 365 E5 tıklayın.

   :::image type="content" source="../../media/mtp-eval-27.png" alt-text="Başlatmak Microsoft 365 E5 Şimdi deneyin düğmesinin saat gerektiği Ücretsiz denemeyi başlat sayfasından" lightbox="../../media/mtp-eval-27.png":::
 
6. **Microsoft 365 Yönetici** **CenterUsersActive** >  >  **users'a gidin**. Kullanıcı hesabını seçin, Ürün **lisanslarını yönet'i** seçin ve sonra lisans yerine **Office 365 E5 başka Microsoft 365 E5**. **Kaydet**'e tıklayın.

   :::image type="content" source="../../media/mtp-eval-28.png" alt-text="Microsoft 365 Yönetici lisansı seçerek bu Microsoft 365 E5 sayfası" lightbox="../../media/mtp-eval-28.png":::
 
7. Genel yönetici hesabını yeniden seçin ve kullanıcı adını **yönet'e tıklayın**.

   :::image type="content" source="../../media/mtp-eval-29.png" alt-text="Hesap Microsoft 365 Yönetici Kullanıcı adını yönet'i seçebilirsiniz." lightbox="../../media/mtp-eval-29.png":::

8. [İsteğe bağlı] Önceki adımlarda *onmicrosoft.com* bağlı olarak, etki alanını kendi etki alanınıza göre değiştirebilirsiniz. **Değişiklikleri kaydet**’e tıklayın.

   :::image type="content" source="../../media/mtp-eval-30.png" alt-text="Etki Microsoft 365 Yönetici tercihinizi değiştirebilirsiniz." lightbox="../../media/mtp-eval-30.png":::

## <a name="next-step"></a>Sonraki adım
|[Aşama 3: Ekleme & yapılandırma](config-m365d-eval.md) | Test laboratuvarınız Microsoft 365 Defender pilot ortamınız Microsoft 365 Defender sütunlu olarak yapılandırır ve uç noktalarınızı hazırlar.
|:-------|:-----|
