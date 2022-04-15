---
title: İş için Microsoft Defender'deki öğreticiler ve simülasyonlar
description: İş için Defender'ı kullanmaya başlamanıza yardımcı olacak çeşitli öğreticiler hakkında bilgi edinin
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 42d7acb4512928a32ac99c486a231d7891102208
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64861344"
---
# <a name="tutorials-and-simulations-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'deki öğreticiler ve simülasyonlar

> [!IMPORTANT]
> İş için Microsoft Defender artık önizleme aşamasındadır ve istekte bulunmak için [buraya kaydolan](https://aka.ms/mdb-preview) müşterilere ve BT İş Ortaklarına aşamalı olarak dağıtılacaktır. Önümüzdeki haftalarda ilk müşteri ve iş ortaklarını ekleyeceğiz ve önizlemeyi genişleterek genel kullanıma sunacağız. Önizlemenin [ilk senaryo kümesiyle](#try-these-preview-scenarios) başlatılacağını ve düzenli olarak özellikler ekleyebileceğimizi unutmayın.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen önceden yayımlanmış ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

İş için Microsoft Defender ayarlamayı yeni tamamladıysanız, İş için Defender'ın nasıl çalıştığı hakkında nereden bilgi edineceğinizi merak ediyor olabilirsiniz. Bu makalede deneyebileceğiniz önizleme senaryoları ve İş için Defender'da kullanılabilen çeşitli öğreticiler ve simülasyonlar açıklanmaktadır. Bu kaynaklar, İş için Defender'ın şirketiniz için nasıl çalışabileceğini görmenize yardımcı olmak için tasarlanmıştır.

>
> **Bir dakikan var mı?**
> Lütfen <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">güvenlikle ilgili kısa anketimize</a> katılın. Sizden haber almak isteriz!
>

## <a name="try-these-preview-scenarios"></a>Bu önizleme senaryolarını deneyin

Aşağıdaki tabloda, İş için Defender ile deneyebileceğiniz çeşitli senaryolar özetlemektedir:

| Senaryo  | Açıklama  |
|---------|---------|
| Yerel betik kullanarak cihazları ekleme <br/>(*üretim dağıtımı için değil*)     | İş için Defender'da, indirdiğiniz ve her cihazda çalıştırdığınız bir betik kullanarak on Windows 10 ve 11 cihaz ekleyebilirsiniz. İş için Defender'ın ortamınızda nasıl çalışacağını değerlendirmek için uygun olan betik, Azure Active Directory (Azure AD) ile bir güven oluşturur ve cihazı Microsoft Intune ile kaydeder. Daha fazla bilgi edinmek için bkz[. Cihazları İş için Microsoft Defender ekleme](mdb-onboard-devices.md).         |
| Microsoft Intune kullanarak cihazları ekleme     | Uç Nokta için Defender'ı almadan önce zaten Microsoft Intune kullanıyorsanız cihazları eklemek için Microsoft Intune kullanmaya devam edebilirsiniz. Microsoft Intune ile macOS, iOS ve Android cihazları eklemeyi deneyin. Daha fazla bilgi için bkz. [Microsoft Intune'de cihaz kaydı](/mem/intune/enrollment/device-enrollment).        |
| Güvenlik ilkelerini düzenleme     | İş için Defender'da güvenlik ilkelerinizi yönetiyorsanız, ilkelerinizi görüntülemek ve düzenlemek için **Cihaz yapılandırma** sayfasını kullanın. Daha fazla bilgi için bkz. [İş için Microsoft Defender'de ilkeleri görüntüleme veya düzenleme](mdb-view-edit-policies.md).        |
| Sanal saldırı yürütme   | İş için Defender'da çeşitli öğreticiler ve simülasyonlar mevcuttur. Bu öğreticiler ve simülasyonlar, İş için Defender'ın tehdit koruması özelliklerinin şirketiniz için nasıl çalışabileceğini ilk elden gösterecek şekilde tasarlanmıştır. Öğreticilerden birini veya daha fazlasını denemek için bkz. [İş için Microsoft Defender için önerilen öğreticiler](#recommended-tutorials-for-defender-for-business).         |
| Microsoft 365 Lighthouse'da olayları görüntüleme     | Microsoft 365 Lighthouse kullanan bir [Microsoft Bulut Çözümü Sağlayıcısı](/partner-center/enrolling-in-the-csp-program) iseniz, Microsoft 365 Lighthouse portalınızda müşterilerinizin kiracıları genelindeki olayları yakında görüntüleyebileceksiniz. Daha fazla bilgi edinmek için bkz. [Microsoft 365 Lighthouse ve İş için Microsoft Defender](mdb-lighthouse-integration.md).       |


## <a name="recommended-tutorials-for-defender-for-business"></a>İş için Defender için önerilen öğreticiler

Aşağıdaki tabloda, İş için Defender müşterileri için önerilen öğreticiler açıklanmaktadır:

| Öğretici  | Açıklama  |
|---------|---------|
| **Belge arka kapı bırakıldığında**     | Bir test cihazına dosya tabanlı kötü amaçlı yazılım getiren bir saldırının benzetimini yapmak. Öğreticide simülasyon dosyasının nasıl alınıp kullanılacağı ve Microsoft 365 Defender portalında nelerin izlenip izlendiği açıklanır. <br/><br/>Bu öğretici, test cihazınıza Microsoft Word yüklenmesini gerektirir.   |
| **Canlı Yanıt öğreticisi**     | Canlı Yanıt ile temel ve gelişmiş komutları kullanmayı öğrenin. Şüpheli bir dosyayı bulmayı, dosyayı düzeltmeyi ve bir cihazda bilgi toplamayı öğrenin.   |
| **Tehdit & Güvenlik Açığı Yönetimi (temel senaryolar)**     | Üç senaryodan Tehdit ve Güvenlik Açığı Yönetimi hakkında bilgi edinin: <br/><br/>1. Şirketinizin tehdidini ve güvenlik açığına maruz kalmasını azaltın. <br/>2. Bir düzeltme isteyin. <br/>3. Güvenlik önerileri için bir özel durum oluşturun. <br/><br/> Tehdit ve güvenlik açığı yönetimi, uç nokta güvenlik açıklarını ve yanlış yapılandırmalarını bulma, öncelik belirleme ve düzeltme konusunda risk tabanlı bir yaklaşım kullanır.      |

Her öğreticide senaryoyu, nasıl çalıştığını ve ne yapılacağını açıklayan bir izlenecek yol belgesi bulunur.

> [!TIP]
> İzlenecek belgelerde Uç Nokta için Microsoft Defender başvurularını görürsünüz. Bu makalede listelenen öğreticiler Uç Nokta için Defender veya İş için Defender ile kullanılabilir.

## <a name="how-to-access-the-tutorials"></a>Öğreticilere erişme

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

2. Gezinti bölmesindeki **Uç Noktalar'ın** altında **Öğreticiler'i** seçin.

3. Aşağıdaki öğreticilerden birini seçin:

   - **Belge arka kapı bırakıldığında**
   - **Canlı Yanıt öğreticisi**
   - **Tehdit & Güvenlik Açığı Yönetimi (temel senaryolar)**

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'de cihazları yönetme](mdb-manage-devices.md)
- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)
- [İş için Microsoft Defender'da tehditlere yanıt verme ve tehditleri azaltma](mdb-respond-mitigate-threats.md)
- [İşlem merkezindeki düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)