---
title: Blackboard Learn Ultra ile Microsoft Teams sınıflarını kullanma
ms.author: danismith
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
description: Blackboard Learn Ultra ile Microsoft Teams sınıflarını kullanma
ms.openlocfilehash: f5e53c54db893a184a5b2afe86b61c823b62f5a6
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923072"
---
# <a name="use-microsoft-teams-classes-with-blackboard-learn-ultra"></a>Blackboard Learn Ultra ile Microsoft Teams sınıflarını kullanma

Ekip çalışması, her modern kuruluşun merkezinde yer alır. İşbirliğini teşvik ederek, her başarılı kurumun belirleyici bir özelliğidir. Blackboard Learn Ultra'nın tüm özelliklerini ve özelliklerini Microsoft Teams sınıflarıyla eşleştirerek geliştirebilirsiniz.

Sınıflarınız gerçek zamanlı konuşmalar, görüntülü toplantılar veya zaman uyumsuz etkileşimler içerebilir. Öğrencileriniz için dosya paylaşımı ve birlikte oluşturma deneyimlerini tek bir yerden ekleyebilirsiniz. Learn Ultra ile Microsoft Teams sınıfları, öğretimin dinamiklerini ve etkili öğrenmenin ne anlama geldiğini yeniden tanımlar.

> [!IMPORTANT]
> [Öğrenci Bilgi Sisteminizde (SIS)](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Student_Information_System/SIS_Planning) Kurum E-posta alanını başarıyla ayarladığınızdan emin olun
>
>Microsoft Teams sınıfları tümleştirmesi, doğru Microsoft Azure Active Directory (AAD) [Kullanıcı Asıl Adı (UPN](/azure/active-directory/hybrid/howto-troubleshoot-upn-changes)) ile eşlemek için SIS'inizdeki kurum e-posta alanına dayanır. Herhangi bir kurum e-postası sağlanmamışsa, bu varsayılan olarak mevcut e-postaya ayarlanır. Verilerinin doğru eşitlendiğinden ve AAD ile Blackboard Learn Ultra arasında e-posta verileri çakışması olmadığından emin olmak için bu alanın her kullanıcı için ayarlanması önerilir.
>
> SIS eşlemenizde bu alanı uygun şekilde ayarlamadıysanız tümleştirme çalışmaya devam eder, ancak kullanıcılar oluşturulan Teams sınıflarında görünmeyebilir ve hatalar oluşabilir.

## <a name="supporting-institutional-data-mapping--institution-email-sis-field"></a>Kurumsal Veri Eşlemeyi Destekleme – Kurum E-posta SIS Alanı

Bulut sağlayıcısı tümleştirmelerinin gelişimi kapsamında Blackboard Learn Ultra, hem Öğrenci Bilgi Sistemi Çerçevesi tümleştirmesinde hem de genel REST API'lerinde yeni bir **Kurum E-posta** alanı oluşturarak kurumların Blackboard Learn Ultra ile AAD arasında veri eşitleme sürecini etkili bir şekilde yönetmesine olanak sağlıyor.

### <a name="what-does-the-institution-email-mean-and-what-does-it-support"></a>Kurum E-postası ne anlama gelir ve neleri destekler?

**Kurum E-postası** alanı, bir istemcinin dışarıdan desteklenen veri kaynakları ile Blackboard Learn Ultra arasında özelleştirilmiş alan eşlemelerine olanak tanır. Veri kaynakları Microsoft gibi bulut sağlayıcılarıysa, Kullanıcı Asıl Adı (UPN), her kullanıcı için@ simgesiyle birleştirilmiş bir UPN ön eki (kullanıcının hesap adı) ve UPN soneki (DNS etki alanı adı) içeren birincil benzersiz tanımlayıcıdır. Bu, Microsoft Azure Active Directory içindeki her belirli kullanıcı için benzersiz bir e-posta adresi oluşturur.

Verilerin doğru olduğundan ve Blackboard Learn Ultra ile Microsoft Teams sınıfları arasındaki kayıtların veya üyeliklerin doğru şekilde elde edilmesini sağlamak için kullanıcının e-posta adresinin her iki sistem arasında eşleşmesi gerekir. Blackboard Learn Ultra'da kullanıcılar, kullanıcı arabiriminde mevcut e-posta adreslerini değiştirebilir veya geçersiz kılabilir ve bu da eşitleme hatalarının oluşmasına ve kullanıcının Sınıf Ekibine doğru şekilde eklenememesine neden olabilir. **Kurum E-postası** alan eşlemesi, kullanıcıların Blackboard Learn Ultra'da e-postalarını değiştirip değiştirmediklerine bakılmaksızın bu güvenlik ve doğrulama denetiminin doğru şekilde yönetilmesini sağlar.

 İki e-posta adresi farklı olduğunda:

- Hangi kaynağın öncelikli olduğu ve hem Kişi hem de Kurum E-postaları olarak alınacağı yönünde bir karar alınmalıdır.
  Veya
- Bir kurum, Kurum E-postasında özel alan eşlemesi ayarlayabilir ve bu da olası bir çakışmayı çözebilir.

**Kurum E-postası** alan eşlemesi artık **Gelişmiş Yapılandırma Ayarları** > **Kullanıcılar Learn Nesne Türü** > **Alan Eşlemesi** bölümünde mevcut tüm SIS tümleştirme türleri için kullanılabilir.

> [!NOTE]
> **Kuruluş E-postası'nın** varsayılan olarak tüm SIS biçimleri için **Kişi E-postası** olarak ayarlandığını ve her kişi için benzersiz olması gerektiğini unutmayın. Sis, e-postaları çoğaltılırsa kullanıcıları içeri aktaramayacağı için, ayarlanmış ve çalışan tümleştirmelerde bu veri eşlemesi gerçekleştirilecektir. Bir kurumun Kurum E-postası'nı **özel** olarak değiştirmesi gerekiyorsa, bunu SIS'teki **Gelişmiş Yapılandırma Ayarları** aracılığıyla yönetmesi gerekir.

## <a name="requirements"></a>Gereksinimler

Microsoft Teams sınıf tümleştirmesi **yalnızca Ultra Kurs Görünümü kursları** için kullanılabilir. Kuruluşunuzun kullanabilmesi için şu gereksinimleri karşılaması gerekir:

- Ultra Temel Gezinti özelliği etkinleştirilmiş Blackboard Learn Ultra Learn SaaS özelliğine sahip olun

  ![kurslarda özelliğin bir örneği etkindir.](media/feature-availability.png)

- Kurslarda kullanılmak üzere LTI'yi etkinleştirin.

  a. **Yönetici Paneli** > **LTI Aracı Sağlayıcıları** > **Genel Özellikleri Yönet'e** gidin.

  b. **Kurslarda LTI Etkin'i** seçin ve isteğe bağlı olarak **Kuruluşlarda Etkin'i** seçin.

  c. **Gönder'i** seçin.

- LTI yapılandırılmış olmalıdır

- Blackboard Learn Ultra Teams Sınıfları LTI Tümleştirmesi Ekleme

- Microsoft Teams Sınıfları LTI 1.3 Aracı Ekleme

- REST API Aracı ve Çıkış Noktaları Arası Kaynak Paylaşımı ekleme

- Microsoft Teams sınıfları Tümleştirmesini yapılandırma ve onaylama

## <a name="add-the-blackboard-learn-ultra-teams-classes-lti-13-tool"></a>Blackboard Learn Ultra Teams Sınıfları LTI 1.3 Aracını Ekleme

1. **Yönetici Paneli'nden** **LTI Araç Sağlayıcıları'nı** seçin.

2. **LTI 1.3 Aracı'nı kaydet'i** seçin.

3. **İstemci Kimliği** alanına şu kimliği yazın veya kopyalayıp yapıştırın:

   `f1561daa-1b21-4693-ba90-6c55f1a0eb41`

4. Önceden doldurulmuş ve **Araç Durumu'nda** bulunan tüm ayarları gözden geçirin ve **Etkin'i** seçin.

5. **Kurum İlkeleri'nde** Kurs, Ad ve **E-posta** **Adresi'nde Rol'e** tıklayın ve her ikisi için de **Evet'e** tıklayın.

6. **Not hizmeti erişimine izin ver** ve **Üyelik Hizmeti Erişimine İzin Ver'i** seçin.

## <a name="add-the-microsoft-teams-classes-lti-13-tool"></a>Microsoft Teams Sınıfları LTI 1.3 Aracı'nı ekleme

1. **Yönetici Paneli'nden** **LTI Araç Sağlayıcıları'nı** seçin.

2. **LTI 1.3 Aracı'nı kaydet'i** seçin.

3. **İstemci Kimliği** alanına şu kimliği yazın veya kopyalayıp yapıştırın:

   `027328b7-c2e3-4c9e-aaa1-07802dae6c89`

4. Önceden doldurulmuş ve *Araç Durumu'nda* bulunan tüm ayarları gözden geçirin ve *Etkin'i seçin.*

5. **Kurum İlkeleri'nde** **Kursta Rol, Ad** ve **E-posta Adresi'ne** tıklayın. Her ikisi için **de Evet'i** seçin.

6. **Not hizmeti erişimine izin ver** ve **Üyelik Hizmeti Erişimine İzin Ver'i** seçin.

## <a name="add-the-rest-api-tool"></a>REST API aracını ekleme

1. **Yönetici Paneli'nden** **Tümleştirmeler'e** gidin ve **Rest API Tümleştirmeleri'ni** seçin.

2. **Tümleştirme Oluştur'u** seçin.

3. **Uygulama Kimliği** alanına şu kimliği yazın veya kopyalayıp yapıştırın:

   `f1561daa-1b21-4693-ba90-6c55f1a0eb41`

4. Bu tümleştirme için bir kullanıcı yazın.

   Bu kullanıcı, uygulamanın ilişkilendirildiği ev API'sine erişimi olan kullanıcı olacaktır.

5. **Gönder'i** seçin.

## <a name="add-the-cross-origin-resource-sharing"></a>Çıkış Noktaları Arası Kaynak Paylaşımını Ekleme

1. **Yönetici panelinde** **Tümleştirmeler'e** gidin ve **Çıkış noktaları arası Kaynak Paylaşımı'nı* seçin.

2. **Yapılandırma Oluştur'u** seçin.

3. **Kaynak** alanında, şu URL'yi kopyalayıp yapıştırın:

   `https://bb-ms-teams-ultra-ext.api.blackboard.com`

4. **İzin Verilen Üst Bilgiler** alanına **Yetkilendirme** yazın.

5. **Kullanılabilir'i** **Evet** olarak ayarlayın.

6. **Gönder'i** seçin.

## <a name="configure-and-approve-microsoft-teams-classes-integration"></a>Microsoft Teams sınıf tümleştirmesini yapılandırma ve onaylama

Blackboard Learn Ultra örneğinizi Microsoft Teams sınıflarıyla başarıyla tümleştirmek için, Blackboard Learn Ultra uygulamasının Microsoft Azure kiracınızda erişim için onaylandığından emin olmanız gerekir. Bu, kuruluşunuzun Microsoft 365 Genel Yöneticisi tarafından tamamlanması gereken bir süreçtir.

Bu işlem, Blackboard Learn Ultra Örneğinizdeki LTI uygulamalarını yapılandırmadan önce veya sonra yapılabilir.

### <a name="before-configuring-the-lti-applications"></a>LTI Uygulamalarını Yapılandırmadan Önce

LTI tümleştirmelerini yapılandırmadan önce Blackboard Learn Ultra Teams Sınıfları Azure uygulamasını onaylamayı seçerseniz **Microsoft Kimlik Platformu Yönetici Onayı Uç Noktası'na** yeniden yönlendirmeniz gerekir. URL gösterilir:

`https://login.microsoftonline.com/{tenant}/adminconsent?client\_id=2d94989f-457a-47c1-a637-e75acdb11568`

> [!NOTE]
> **{Tenant}** yerine kurumsal Microsoft Azure kiracı kimliğinizi koyacaksınız.

Microsoft Teams'e erişmek için Blackboard Learn Ultra'ya izin verdiğini açıklayan bir izin penceresi görürsünüz.

![Microsoft ve Blackboard için izinler penceresi.](media/permissions1.png)

### <a name="after-configuring-the-lti-applications"></a>LTI Uygulamalarını Yapılandırdıktan Sonra

1. **Yönetici Paneli'nde** **Araçlar ve Yardımcı Programlar'a gidin ve** **Microsoft Teams Tümleştirme Yöneticisi'ni** seçin.

2. **Microsoft Teams'i Etkinleştir'i** seçin.

3. Kullanılabilir metin alanına **Microsoft Kiracı Kimliğinizi** ekleyin.

4. Aşağıdaki seçeneklerden birini belirleyin:

   - Uygulamanın ön onayı varsa küçük bir onay işareti gösterilir. Onay işareti görünürse **Gönder'i** seçin.

   - Onay onaylanmamışsa, onay URL'sini oluşturmak ve onay için Microsoft 365 Genel Yöneticisi'ne göndermek için açıklanan adımları izleyin.

5. Onay onayını aldıktan sonra onaylamak için **Yeniden Dene'yi** ve ardından **Gönder'i** seçin.
