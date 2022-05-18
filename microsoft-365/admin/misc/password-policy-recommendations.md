---
title: Parola ilkesi önerileri
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9fa2539a-2211-41fd-85a0-bc37b9619ca4
description: Kuruluşunuzu parola saldırılarına karşı daha güvenli hale getirin ve yaygın parolaları yasaklayın ve risk tabanlı çok faktörlü kimlik doğrulamasını etkinleştirin.
ms.openlocfilehash: 006e537c2e2d77a19b27f1c2d537269d69d07c1e
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65469018"
---
# <a name="password-policy-recommendations-for-microsoft-365-passwords"></a>Microsoft 365 parolalar için parola ilkesi önerileri

Bir kuruluşun yöneticisi olarak, kuruluşunuzdaki kullanıcılar için parola ilkesini ayarlamak sizin sorumluluğunuzdadır. Parola ilkesini ayarlamak karmaşık ve kafa karıştırıcı olabilir ve bu makalede kuruluşunuzun parola saldırılarına karşı daha güvenli olmasını sağlamak için öneriler sağlanır.

Yalnızca buluta özel Microsoft hesapları, değiştirilemeyen önceden tanımlanmış bir parola ilkesine sahiptir. Değiştirebileceğiniz tek öğeler, parolanın süresinin dolmasına kadar olan gün sayısı ve parolaların süresinin dolup dolmayacağıdır. 
  
Kuruluşunuzda Microsoft 365 parolaların süresinin ne sıklıkta doldığını belirlemek için bkz. [Microsoft 365 için parola süre sonu ilkesini ayarlama](../manage/set-password-expiration-policy.md).

Microsoft 365 parolaları hakkında daha fazla bilgi için bkz:

[Parolaları sıfırlama](../add-users/reset-passwords.md) (makale)

[Tek bir kullanıcının parolasını hiçbir zaman sona ermeyecek şekilde ayarlama](../add-users/set-password-to-never-expire.md) (makale)

[Kullanıcıların kendi parolalarını sıfırlamasına izin verme](../add-users/let-users-reset-passwords.md) (makale)

[Kullanıcının parolasını yeniden gönderme - Yönetici Yardımı](../add-users/resend-user-password.md) (makale)
  
## <a name="understanding-password-recommendations"></a>Parola önerilerini anlama

İyi parola uygulamaları birkaç geniş kategoriye ayrılır:
  
- **Yaygın saldırılara dayanma** Bu, kullanıcıların parola girdiği ve (zararlı yazılım koruması olan bilinen ve güvenilen cihazlar, doğrulanmış siteler) ve seçilecek parolanın olduğu seçeneği kapsar (uzunluk ve benzersizlik).

- **Başarılı saldırıların kontrol altına alınması,** Eğer bir kullanıcının parolası çalınırsa, başarılı korsan saldırılarının kontrol altına alınması belirli bir hizmete maruz kalmanın sınırlanmasıyla, ya da bu hasarın tamamen engellenmesi ile mümkündür. Örneğin, sosyal ağ kimlik bilgilerinizle ilgili herhangi bir ihlalin, banka hesabınız için bir güvenlik sorunu teşkil etmiyor olması veya iyi korunmayan bir hesabın, önemli bir hesap için sıfırlama bağlantılarını kabul etmesine izin vermemek gibi.

- **İnsan doğasını anlamak** Birçok mantıklı parola kullanımı bile doğal insan davranışı yüzünden başarısız olabilir. İnsan doğasını anlamak önemlidir çünkü araştırmalar gösteriyor ki, neredeyse kullanıcılarınıza uyguladığınız her kural parola kalitesinin zayıflamasına yol açacaktır. Uzunluk gereksinimleri, özel karakter gereksinimleri ve parola değişikliği gereksinimlerinin parolaları normalleşmesinin sonucu olarak, saldırganların parolaların tahmin etmesini veya kırmasını daha kolay hale getirir.

## <a name="password-guidelines-for-administrators"></a>Yöneticiler için parola kılavuzları

Daha güvenli bir parola sisteminin birincil hedefi, parola çeşitliliğidir. Parola ilkenizin birçok farklı ve tahmin etmesi zor parolalar içermesi gerekir. Aşağıda, kuruluşunuzun mümkün olduğunca güvenli tutulması için bazı öneriler bulabilirsiniz.
  
- 8 karakterlik minimum uzunluk gereksinimini koruma

- Karakter derlemesi gerektirmeyin. Örneğin, \*&amp;(^%$ gibi

- Kullanıcılar hesapları için zorunlu periyodik parola sıfırlamaları gerektirmeyin.

- Çoğu savunmasız parolayı sisteminizin dışında tutmak için, yaygın kullanılan parolaları yasaklayın.

- Kullanıcılarınızı, işle ilgili olmayan amaçlarla kuruluş parolalarını yeniden kullanmamaları için eğitme

- [çok faktörlü kimlik doğrulaması](../security-and-compliance/set-up-multi-factor-authentication.md) için kaydolmayı zorunlu tutun.

- Riske dayalı çok faktörlü kimlik doğrulaması bulmacalarını etkinleştirin.

### <a name="password-guidance-for-your-users"></a>Kullanıcılarınız için parola kılavuzları

İşte kuruluşunuzdaki kullanıcılar için bazı parola yönergeleri. Bu önerilerden kullanıcılarınızın haberdar olduğundan emin olun ve kuruluş düzeyinde önerilen parola ilkelerini zorunlu tutun.
  
- Aynı veya diğer web sitelerinde kullandığınız bir parolayı kullanmayın.

- Parola gibi tek bir sözcük veya **Iloveyou** gibi yaygın olarak kullanılan bir tümceciği kullanmayın

- Arkadaşlarınız ve ailenizdekilerin isimleri ve doğum günleri, en sevdiğiniz müzik grupları ve kullanmayı sevdiğiniz ifadeler gibi sizin hakkınızda çok fazla şey bilenler için bile, parolalarınızı tahmin etmesi zor kılın

## <a name="some-common-approaches-and-their-negative-impacts"></a>Bazı yaygın yaklaşımlar ve bunların olumsuz etkileri

Bunlar en sık kullanılan parola yönetimi uygulamalarından bazılardır, ancak araştırmalar olumsuz yönleri hakkında bizleri uyarmaktadır.
  
### <a name="password-expiration-requirements-for-users"></a>Kullanıcılar için parola zamanı geçmesi gereksinimleri

Parola süre sonu gereksinimleri, kullanıcıların birbiriyle yakından ilişkili sıralı sözcükler ve sayılardan oluşan öngörülebilir parolalar seçmesine neden olduğundan, parola süre sonu gereksinimleri faydadan daha fazla zarara neden olur. Bu gibi durumlarda yeni parola, önceki parolaya bakılarak tahmin edilebilir. Parola süre sonu gereksinimleri hiçbir kapsama avantajı sunmaz çünkü siber suçlular neredeyse her zaman kimlik bilgilerini tehlikeye girer girmez kullanırlar. Daha fazla bilgi [için Zorunlu parola değişikliklerini yeniden düşünme zamanı'na](https://go.microsoft.com/fwlink/p/?linkid=861018) göz atın.
  
### <a name="requiring-long-passwords"></a>Uzun parolalar gerektirme

Parola uzunluğu gereksinimleri (10 karakterden uzun), tahmin edilebilir ve istenmeyen kullanıcı davranışına neden olabilir. Örneğin, 16 karakterlik parola belirlemesi istenen kullanıcılar, **dörtdörtdörtdört** veya **parolaparola** karakter uzunluğu gereksinimini karşılayan ama tahmin edilmesi zor olmayan, tekrar eden kalıplar seçebilir. Ayrıca, uzunluk gereksinimleri kullanıcıların parolalarını yazma, yeniden kullanılma veya belgelerinde şifrelenmemiş olarak depolama gibi diğer güvenli olmayan uygulamaları benimseme olasılığını artırır. Kullanıcıları benzersiz bir parola kullanmaya teşvik etmek için, en az 8 karakterlik makul bir en az uzunluk gereksinimi benimsenmesini öneririz.
  
### <a name="requiring-the-use-of-multiple-character-sets"></a>Birden çok karakter kümesinin kullanılmasını gerektirme

Parola karmaşıklığı gereksinimleri fayda sağlamaktan çok zarara yol açarak, anahtar alanını azaltır ve kullanıcıların tahmin edilebilir davranmasına neden olur. Çoğu sistem belirli bir seviyede parola karmaşıklığı gereksinimini zorunlu tutar. Örneğin, parolaların aşağıdaki üç kategoriden de karakter içermesi gereklidir:
  
- büyük harf karakterler

- küçük harf karakterler

- Alfasayısal olmayan karakterler

Birçok insan benzer bir dizilim kullanır, örneğin, ilk konumda büyük bir harf, sonuncuda bir sembol ve son 2’de bir numara. Siber suçlular bunu bilir, bu nedenle sözlük saldırılarını en yaygın değiştirmeleri kullanarak çalıştırırlar, "s" için "$", "a" için "@", "l" için "1". Kullanıcılarınızı büyük harf, küçük harf, rakam ve özel karakter gerektiren bir kombinasyon seçmeye zorlamanın olumsuz bir etkisi vardır. Bazı karmaşıklık gereksinimleri kullanıcıların güvenli ve akılda kalıcı parolalar kullanmasını bile engelleyebilir, daha az güvenli ve kolay hatırlanamayan parolalar kullanmaya zorlayabilir.
  
## <a name="successful-patterns"></a>Başarılı Dizilimler

Aksine, parola çeşitliliğini teşvik etmek için işte size birkaç öneri.
  
### <a name="ban-common-passwords"></a>Yaygın parolaları yasaklayın

Kullanıcılarınıza parola oluştururken uygulamanız gereken en önemli gereksinim, kuruluşunuzun brute force parola saldırılarına olan hassasiyetini azaltmak için, yaygın kullanılan parolaların kullanımını yasaklamaktır. Yaygın kullanıcı parolaları şunlardır: **abcdefg**, **parola**, **maymun**.
  
### <a name="educate-users-to-not-reuse-organization-passwords-anywhere-else"></a>Kullanıcıları kuruluş parolalarını başka bir yerde yeniden kullanmamaya eğitme

Kuruluşunuzdaki kullanıcılara ulaşmak için en önemli iletilerden biri, kuruluş parolalarını başka hiçbir yerde yeniden kullanmamaktır. Kuruluş parolalarının dış web sitelerinde kullanılması, siber suçluların bu parolaları tehlikeye atma olasılığını büyük ölçüde artırır.
  
### <a name="enforce-multi-factor-authentication-registration"></a>Çok Faktörlü Kimlik Doğrulaması’na kaydolmayı zorunlu tutun

Kullanıcılarınızın, alternatif bir e-posta adresi, telefon numarası ya da anlık bildirimler için kaydedilmiş bir cihaz gibi iletişim ve güvenlik bilgilerini güncellediklerinden emin olun, bu sayede güvenlik zorluklarına müdahalede bulunabilir ve değişikliklerden haberleri olabilir. Güncel iletişim ve güvenlik bilgileri, eğer şifrelerini unutur ya da birisi hesaplarını ele geçirmeye çalışırsa, kimliklerini doğrulamalarına yardımcı olur. Bu aynı zamanda, giriş yapma girişimleri ya da şifre değiştirilmesi gibi durumlarda bant dışı bir bildirim kanalı sağlar. 
  
Daha fazla bilgi için, bkz. [Çok faktörlü kimlik doğrulaması ayarlama](../security-and-compliance/set-up-multi-factor-authentication.md).
  
### <a name="enable-risk-based-multi-factor-authentication"></a>Riske dayalı çok faktörlü kimlik doğrulamasını etkinleştirin.

Riske dayalı çok faktörlü kimlik doğrulaması, sistemimiz şüpheli etkinlikler aldıladığında, kullanıcının asıl hesap sahibi olduğunu doğrulamasını gerektirir. 
  
## <a name="next-steps"></a>Sonraki adımlar

Parolaları yönetme hakkında daha fazla bilgi edinmek ister misiniz? Önerilen bazı okumalar şunlardır:

- [Parolaları unutun, parolasız gidin](https://www.microsoft.com/security/business/identity-access-management/passwordless-authentication)

- [Microsoft Parola Kılavuzu](https://www.microsoft.com/research/wp-content/uploads/2016/06/Microsoft_Password_Guidance-1.pdf)

- [Güçlü Web Şifreleri bir İşe Yarar Mı?](https://go.microsoft.com/fwlink/p/?linkid=861008)

- [Parola Portföyleri ve Sınırlı Çaba Kullanıcısı](https://go.microsoft.com/fwlink/p/?linkid=861014)

- [Kullanıcıların Zihnini Okuyarak Zayıf Parolaları Engelleme](https://go.microsoft.com/fwlink/p/?linkid=861015)

- [Güvenli Parola Seçme](https://go.microsoft.com/fwlink/p/?linkid=861016)

- [Zorunlu Parola Değişikliklerini Yeniden Düşünme](https://go.microsoft.com/fwlink/p/?linkid=861018)

- [2015’in En Kötü Parolaları](https://go.microsoft.com/fwlink/p/?linkid=861020)

## <a name="related-content"></a>İlgili içerik

[Parolaları sıfırlama](../add-users/reset-passwords.md) (makale)\
[Tek bir kullanıcının parolasını hiçbir zaman sona ermeyecek şekilde ayarlama](../add-users/set-password-to-never-expire.md) (makale)\
[Kullanıcıların kendi parolalarını sıfırlamasına izin ver](../add-users/let-users-reset-passwords.md) (makale)\
[Kullanıcının parolasını yeniden gönderme - Yönetici Yardımı](../add-users/resend-user-password.md) (makale)
