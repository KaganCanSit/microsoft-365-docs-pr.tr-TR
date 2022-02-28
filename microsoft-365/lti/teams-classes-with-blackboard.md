---
title: Blackboard Microsoft Teams Ultra Öğrenme ile diğer sınıflara da yer yok
ms.author: v-cichur
author: cichur
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Blackboard Microsoft Teams Ultra Öğrenme ile diğer sınıflara da yer yok
ms.openlocfilehash: 2cf6c3f3e7c9c8b0004ea08fccdec981c032a491
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990573"
---
# <a name="use-microsoft-teams-classes-with-blackboard-learn-ultra"></a>Blackboard Microsoft Teams Ultra Öğrenme ile diğer sınıflara da yer yok

Ekip çalışması her modern kuruluşun temelsindedir. İşbirliğini teşvik edince, her başarılı kurumun belirleyici özelliğidir. Blackboard'la Ultra Öğrenme'nin tüm özelliklerini, bu özellikleri farklı sınıflara Microsoft Teams suz.

Sınıflarınız gerçek zamanlı konuşmalar, görüntülü toplantılar veya zaman uyumsuz etkileşimler içerebilir. Öğrencileriniz için tek bir yerde dosya paylaşımı ve birliktelık deneyimleri  eklersiniz. Microsoft Teams Ultra Öğrenin'in sahip olduğu sınıflara, öğretimin dinamiklerini ve etkili öğrenmenin ne anlama geldiğini yeniden tanımlarız.

> [!IMPORTANT]
> Öğrenci Bilgi Sistemi'niz (SIS) içinde Kurum E-posta alanını [başarıyla ayar](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Student_Information_System/SIS_Planning)
>
>Sınıf Microsoft Teams tümleştirmesi, SIS'inizin kurum e-posta alanına, doğru kullanıcı (Microsoft Azure Active Directory) Kullanıcı AAD [Ad'ını (UPN](/azure/active-directory/hybrid/howto-troubleshoot-upn-changes)) eşlemeye dayandır. Herhangi bir kuruluş e-postası sağnmdı ise, varsayılan olarak var olan e-posta kullanılır. Her kullanıcı için bu alanın, verilerin doğru eşitlenmesi ve AAD Blackboard Ultra Öğrenme arasında e-posta verileri arasında çakışma olmayacak şekilde ayarlanmış olması önerilir.
>
> SIS eşlemeniz için bu alanı doğru ayarlamadısanız, tümleştirme çalışmaya devam eder, ancak kullanıcılar oluşturulan Teams sınıflarda görüne görünebilir ve hatalar oluşabilir.

## <a name="supporting-institutional-data-mapping--institution-email-sis-field"></a>Kurumsal Veri Eşlemesini Destekleme – Kurumlar E-posta SIS Alanı

Bulut sağlayıcısı tümleştirmelerinin gelişim süreci kapsamında Blackboard Learn Ultra, hem Student Information System Framework tümleştirmesi  hem de genel REST API'leri içinde yeni bir Kurum E-posta alanı oluşturdu ve kuruluşların Blackboard Ultra ile Ultra Öğrenme arasında veri eşitleme sürecini etkili bir şekilde yönetmesini AAD.

### <a name="what-does-the-institution-email-mean-and-what-does-it-support"></a>Kurum E-postası ne anlama geliyor ve neleri destekliyor?

Kurum **E-posta** alanı, istemcinin dışarıdan desteklenen veri kaynaklarıyla Blackboard Ultra Bilgi kaynağı arasında özelleştirilmiş alan eşlemeleri sağlar. Veri kaynakları Microsoft gibi bulut sağlayıcıları ise, Kullanıcı Asıl Adı (UPN) bir UPN ön ekini (kullanıcının hesap adı) ve @ simgesiyle bir araya gelen UPN sonekini (DNS etki alanı adı) oluşan her kullanıcı için birincil benzersiz tanımlayıcıdır. Bu, e-posta adresi içindeki belirli her kullanıcı için benzersiz bir Microsoft Azure Active Directory.

Verilerin doğru olduğundan ve Blackboard Ultra Bilgi ile Microsoft Teams arasındaki kayıtların veya üyeliklerin doğru elde edilebilir olduğundan emin olmak için, kullanıcının e-posta adresi her iki sistem arasında eşleşmeli. Blackboard'da Ultra Öğrenme'de, kullanıcılar kullanıcı arabiriminde mevcut e-posta adreslerini değiştirebilir veya geçersiz k kullanabilir ve bu da eşitleme hatalarının ortaya çıktısı ve kullanıcının Sınıf Ekibine düzgün şekilde ekli olmadığını gösterir. Kurum **E-posta** alanı eşlemesi, kullanıcıların Blackboard Learn Ultra içinde e-postalarını değiştirmelerine bakılmaksızın, bu güvenlik ve doğrulama denetimi düzeyinin doğru bir şekilde yönetilebini sağlar.

 İki e-posta adresi farklı olduğunda:

- Hangi kaynağın önceliğe sahip olduğu kararı alınmalıdır ve hem Kişi hem de Kurum E-postaları olarak alınmalıdır.
  Veya
- Kurum, Kurum E-posta'sinde özel bir alan eşlemesi ayar çözmek için olası bir çakışmayı çözebilir.

Kurum **E-posta** alanı eşlemesi artık Gelişmiş Yapılandırma Ayarlar Kullanıcıları Nesne Türünü **ÖğrenField Eşlemesi'nde** mevcut tüm SIS  >  tümleştirme türlerinde  > **kullanılabilir**.

> [!NOTE]
> Kurum E-postası'nın varsayılan olarak tüm SIS biçimlerde Kişi E-postası  olarak ayar olduğunu ve her bir kişi için benzersiz olması gerektiğini unutmayın. SIS, e-posta yinelenen kullanıcıları içeri aktarmada başarısız olduğu için, ayarlanmış ve çalışan tüm var olan tümleştirmelerde bu veri eşlemesi kullanılır. Bir kurum Kurum e-postayı özel olarak değiştirebilme olanağı **gerektiriyorsa, bunu** SIS'te Gelişmiş Yapılandırma **Ayarlar aracılığıyla** yönetmeleri gerekir.

## <a name="requirements"></a>Gereksinimler

Sınıf Microsoft Teams tümleştirmesi yalnızca **Ultra Kurs Görünümü kursları için kullanılabilir**. Kurumuz bu gereksinimleri tamamlamak için şu gereksinimleri karşılamalıdır:

- Blackboard'da Ultra Temel Gezinti etkinleştirildiğinde Ultra Öğrenme SaaS'ı öğrenme

  ![Kurslarda özellik örneği etkinleştirilmiş durumdadır.](media/feature-availability.png)

- LTI'yi kurslarda kullanmak için etkinleştirin.

  a. Yönetici **PanelLTI Araç SağlayıcılarıManasil** >  Özellikleri  > **Yönetimi'ne gidin**.

  b. **Kurslarda LTI Etkin'i** seçin ve isteğe bağlı olarak Kuruluşlarda **Etkin'i seçin**.

  c. **Gönder'i seçin**.

- LTI'nın yapılandırılmış olması gerekir

- Blackboard Ekleme Ultra Şeridi Teams LTI Tümleştirmesi

- Add Microsoft Teams Classes LTI 1.3 Tool

- REST API Aracı'nı ve Kaynak Çapraz Kaynak Paylaşımı'nı ekleme

- Sınıfları yapılandırma ve Microsoft Teams Tümleştirme

## <a name="add-the-blackboard-learn-ultra-teams-classes-lti-13-tool"></a>Blackboard Learn Ultra Renk Teams Sınıfı LTI 1.3 Aracı'nı ekleme

1. Yönetici **Paneli'den** **LTI Araç Sağlayıcıları'nı seçin**.

2. **LTI 1.3 Aracı'nı kaydettir'i seçin**.

3. İstemci **Kimliği alanında** , şu kimliği yazın veya kopyalayıp yapıştırın:

   `f1561daa-1b21-4693-ba90-6c55f1a0eb41`

4. Önceden doldurulmuş ve Araç Durumu'ta yer alan tüm ayarları **gözden geçirdikten** sonra Etkin'i **seçin**.

5. Kurum **İlkeleri'ne** Göre, **Kursta Rol, Ad ve E-posta** Adresi'ne **, sonra da** her ikisi için **de Evet'e** seçin.

6. Sınıf hizmeti **erişimine izin ver ve Üyelik** Hizmeti **Erişimine İzin Ver'i seçin**.

## <a name="add-the-microsoft-teams-classes-lti-13-tool"></a>Sınıf Microsoft Teams LTI 1.3 Aracı'nı ekleme

1. Yönetici **Paneli'den** **LTI Araç Sağlayıcıları'nı seçin**.

2. **LTI 1.3 Aracı'nı kaydettir'i seçin**.

3. İstemci **Kimliği alanında** , şu kimliği yazın veya kopyalayıp yapıştırın:

   `027328b7-c2e3-4c9e-aaa1-07802dae6c89`

4. Önceden doldurulmuş tüm ayarları gözden geçirerek Araç *Durumu'nı seçin ve Etkin'i* *seçin.*

5. Kurum **İlkeleri'nin** altında **Kursta Rol, Ad ve E-posta** **Adresi'ne seçin**. Her ikisi **için de** Evet'i seçin.

6. Sınıf hizmeti **erişimine izin ver ve Üyelik** Hizmeti **Erişimine İzin Ver'i seçin**.

## <a name="add-the-rest-api-tool"></a>REST API aracını ekleme

1. Yönetici Panelinde **Tümleştirmeler'e** **gidin ve** **Rest API Tümleştirmeleri'ni seçin**.

2. Tümleştirme **Oluştur'a seçin**.

3. Uygulama **Kimliği alanında** , şu kimliği yazın ya da kopyalayıp yapıştırın:

   `f1561daa-1b21-4693-ba90-6c55f1a0eb41`

4. Bu tümleştirme için bir kullanıcı yazın.

   Bu kullanıcı, uygulamanın ilişkilendirilen giriş API erişimine sahip olan kullanıcı olur.

5. **Gönder'i seçin**.

## <a name="add-the-cross-origin-resource-sharing"></a>Kaynak Kaynağı Paylaşımını Ekleme

1. Yönetici panelinde **Tümleştirmeler'e** **gidin ve** *Kaynak *Paylaşımı'nı seçin*.

2. Yapılandırma **Oluştur'a seçin**.

3. Kaynak **alanına,** şu URL'yi kopyalayıp yapıştırın:

   `https://bb-ms-teams-ultra-ext.api.blackboard.com`

4. İzin Verilen **Üst Bilgiler alanına** **Yetki yazın**.

5. Kullanılabilir **olarak** **Evet'i ayarlayın**.

6. **Gönder'i seçin**.

## <a name="configure-and-approve-microsoft-teams-classes-integration"></a>Sınıfları yapılandırma ve Microsoft Teams Tümleştirme

Blackboard'larınızı Ultra Öğrenin örneğini Microsoft Teams sınıfıyla tümleştirin, Blackboard Ultra Öğrenme uygulamasının kiracınız içinde erişim için onaylandıktan Microsoft Azure gerekir. Bu, kurumunuz genel yöneticisi tarafından tamamlanması gereken bir Microsoft 365 vardır.

Bu işlem Blackboard'daki Ultra Örneği'nizin LTI uygulamalarını yapılandırmadan önce veya bu işlemden sonra yapılabilir.

### <a name="before-configuring-the-lti-applications"></a>LTI Uygulamalarını Yapılandırmadan Önce

LTI tümleştirmelerini yapılandırmadan önce Blackboard Learn Ultra Teams Sınıflar Azure uygulamasını onaylamayı seçerseniz, Microsoft Kimlik Platformu Yönetici İzin Uç Noktası'na yeniden **yönlendirmeniz gerekir**. URL gösterilir:

`https://login.microsoftonline.com/{tenant}/adminconsent?client\_id=2d94989f-457a-47c1-a637-e75acdb11568`

> [!NOTE]
> **{Tenant} adlı kiracıyı,** size özel kurumsal veya Microsoft Azure sahip olacak.

Bir izin penceresi gördüğünüzde, Blackboard'a Ultra Bilgi ve Diğer Kullanıcılara erişim izni Microsoft Teams.

![Microsoft ve Blackboard için izinler penceresi.](media/permissions1.png)

### <a name="after-configuring-the-lti-applications"></a>LTI Uygulamalarını Yapılandırtıktan Sonra

1. Yönetici Panelinde **Araçlar ve Yardımcı** **Programlar'a gidin ve Tümleştirme** **Yöneticisi'Microsoft Teams seçin**.

2. **Etkinleştir'i Microsoft Teams**.

3. Microsoft Kiracı **Kimliği'nizi** kullanılabilir metin alanına ekleyin.

4. Aşağıdaki seçeneklerden birini belirleyin:

   - Uygulamanın önceden izni varsa, küçük bir onay işareti gösterir. Onay işareti görünüyorsa Gönder'i **seçin**.

   - onay onaylanmadı ise, izin URL'sini oluşturmak için açıklanan adımları izleyin ve onay için Microsoft 365 Genel Yönetici'ye gönderin.

5. Onay onayını aldıktan sonra, onaylamak için **Yeniden Dene'yi** seçin ve sonra da Gönder'i **seçin**.
