---
title: Office TLS Sertifika Değişiklikleri
description: TLS sertifikalarında yapılacak değişikliklere Office hazır olur.
author: pshelton-skype
ms.author: pshelton
manager: toddbeckett
ms.topic: article
audience: Developer
ms.date: 3/7/2022
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.openlocfilehash: 075fb8f4c27401a4622f4ce639c897f2e98bb3e9
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63450383"
---
# <a name="office-tls-certificate-changes"></a>Office TLS Sertifika Değişiklikleri

Microsoft 365 farklı bir Kök Sertifika Yetkilileri (CA) kümesinden TLS sertifikalarını kullanmak için mesajlaşma, toplantılar, telefon, ses ve video hizmetlerini güncelleştiriyor. Bu değişiklik, geçerli Kök CA'nın Mayıs 2025'te süresi dolacak olması nedeniyle yapılıyor.

Etkilenen ürünler şunlardır:
- Microsoft Teams
- Skype
- Skype Kurumsal Çevrimiçi
- Microsoft Dynamics 365
- GroupMe
- Kaizala
- Azure Communication Services

Etkilenen uç noktalar şunlardır (ancak bunlarla sınırlı değildir):
- *.teams.microsoft.com
- *.skype.com
- *.skypeforbusiness.com
- *.groupme.com
- *.communication.azure.com
- *.operatorconnect.microsoft.com

Ayrıca, Teams ve Skype Kurumsal-US Microsoft 365 Government ulusal bulut bulut örneklerinin Çevrimiçi uç noktaları da aynı değişikliği yapacaktır ve aşağıdaki gibi uç noktaları etkiler:
- *.gcc.teams.microsoft.com
- *.dod.teams.microsoft.us
- *.gov.teams.microsoft.us
- *.online.dod.skypeforbusiness.us
- *.online.gov.skypeforbusiness.us
- *.um-dod.office365.us
- *.um.office365.us

Bu değişiklik, Çin veya Almanya ulusal bulut örneklerde kullanılan sertifika, etki alanı veya hizmetleri Microsoft 365.

Bu makaledeki tüm sertifika bilgileri daha önce Microsoft 365 2020'den sonra şifreleme zincirleri için sağlanmıştır.[](./encryption-office-365-certificate-chains.md)

## <a name="when-will-this-change-happen"></a>Bu değişiklik ne zaman gerçekleşecek?

Hizmetler Ocak 2022'de yeni Kök CA'lara geçiş yapmaya başladı ve Ekim 2022'ye kadar devam edecek.

## <a name="what-is-changing"></a>Neler değişiyor?

Bugün, aşağıdaki Kök CA'ya kadar aşağıdaki Microsoft 365 hizmetleri zincirinde kullanılan TLS sertifikalarının çoğu:

| CA'nın Ortak Adı | Thumbprint (SHA1) |
|--|--|
| [Baltimore CyberTrust Root](https://cacerts.digicert.com/BaltimoreCyberTrustRoot.crt) | d4de20d05e66fc53fe1a50882c78db2852cae474 |

ile aşağıdaki Ara CA'lardan birini kullanabilirsiniz:

| CA'nın Ortak Adı | Thumbprint (SHA1) |
|--|--|
| [Microsoft RSA TLS CA 01](https://www.microsoft.com/pki/mscorp/Microsoft%20RSA%20TLS%20CA%2001.crt) | 703d7a8f0ebf55aaa59f98eaf4a206004eb2516a |
| [Microsoft RSA TLS CA 02](https://www.microsoft.com/pki/mscorp/Microsoft%20RSA%20TLS%20CA%2002.crt) | b0c2d2d13cdd56cdaa6ab6e2c04440be4a429c75 |

Yeni TLS sertifikaları, Microsoft 365 hizmetleri tarafından kullanılan yeni TLS sertifikaları, artık aşağıdaki Kök CA'lardan birinin zincirini sağlar:

| CA'nın Ortak Adı | Thumbprint (SHA1) |
|--|--|
| [DigiCert Genel Kök G2](https://cacerts.digicert.com/DigiCertGlobalRootG2.crt) | df3c24f9bfd666761b268073fe06d1cc8d4f82a4 |
| [Microsoft RSA Kök Sertifika Yetkilisi 2017](https://www.microsoft.com/pkiops/certs/Microsoft%20RSA%20Root%20Certificate%20Authority%202017.crt) | 73a5e64a3bff8316ff0edccc618a906e4eae4d74 | 
| [Microsoft ECC Kök Sertifika Yetkilisi 2017](https://www.microsoft.com/pkiops/certs/Microsoft%20ECC%20Root%20Certificate%20Authority%202017.crt) | 999a64c37ff47d9fab95f14769891460eec4c3c5 |

ile aşağıdaki Ara CA'lardan birini kullanabilirsiniz:

| CA'nın Ortak Adı | Thumbprint (SHA1) |
|--|--|
| [Microsoft Azure TLS Issuing CA 01](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2001%20-%20xsign.crt) | 2f2877c5d778c31e0f29c7e371df5471bd673173 |
| [Microsoft Azure TLS Issuing CA 02](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2002%20-%20xsign.crt) | e7eea674ca718e3befd90858e09f8372ad0ae2aa |
| [Microsoft Azure TLS Issuing CA 05](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2005%20-%20xsign.crt) | 6c3af02e7f269aa73afd0eff2a88a4a1f04ed1e5 |
| [Microsoft Azure TLS Issuing CA 06](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2006%20-%20xsign.crt) | 30e01761ab97e59a06b41ef20af6f2de7ef4f7b0 |

Örnek olarak bu, yeni sertifika zincirlerinden biri olan geçerli bir sertifikadır:

![Teams TLS Sertifika Zinciri](../media/teams-tls-certificate-chain.png)

## <a name="will-this-change-affect-me"></a>Bu değişiklik beni etkileyecek mi?

Root CA "DigiCert Global Root G2", Windows, macOS, Android ve iOS gibi işletim sistemleri ve Microsoft Edge, Chrome, Safari ve Firefox gibi tarayıcılar tarafından yaygın olarak güvenilir. Çoğu müşteri **Microsoft 365 etkilenmeyecek**. 

Ancak **, açıkça kabul edilebilir CA'ların listesini belirtirse, uygulamanız etkilenebilir**. Bu uygulama, "sertifika sabitleme" olarak bilinir. Kabul edilebilir CA'lar listesinde yeni Kök CA'ları bulunan müşteriler sertifika doğrulama hataları alırlar ve bu da uygulamanın kullanılabilirliğini veya işlevini etkiler.

Uygulama etkisinin olup olacağını algılamanın bazı yolları:

- Kaynak kodunuzu burada bulunan Ara CA'ların baş parmak izi, Ortak Ad veya diğer özellikleri için [aratır](https://www.microsoft.com/pki/mscorp/cps/default.htm). Eşleşme olursa, uygulamanız bundan etki olur. Bu sorunu çözmek için, kaynak kodu güncelleştirin ve yeni CA'ların özelliklerini ekleyin. En iyi uygulama olarak, CA'ların kısa sürede eklendik veya düzenlene olduğundan emin olmaktır. Sektörle ilgili düzenlemeler bazı durumlarda CA sertifikalarının yedi gün içinde değiştirilmesini gerektirir, dolayısıyla sertifika sabitleme uygulayan uygulamaların bu değişikliklere hemen karşılık vermeleri gerekir.

- .NET, `System.Net.ServicePointManager.ServerCertificateValidationCallback` `System.Net.HttpWebRequest.ServerCertificateValidationCallback` ve geri arama işlevlerini sunar; bu işlev, geliştiricilerin sertifikaların geçerli olup olmadığını belirlemek için standart veya standart geri Windows kullanır. Geliştirici, belirli bir Ortak Ad veya başparmak basımlarını denetler veya yalnızca "Baltimore CyberTrust Root" gibi belirli bir Kök CA'ya izin veren bir mantık ekleyebilir. Uygulamanız bu geri çağırma işlevlerini kullanıyorsa, eski ve yeni Kök ve Ara CA'ların her ikisini de kabul etmeye emin olun.

- Yerel uygulamalar kullanıyor olabilir ve bu `WINHTTP_CALLBACK_STATUS_SENDING_REQUEST`, yerel uygulamaların özel sertifika doğrulama mantığı uygulamasını sağlar. Bu bildirimin kullanımı nadir görülen bir durumdur ve uygulanması için önemli miktarda özel kod gerektir. Yukarıdakine benzer şekilde, uygulamanın hem eski hem de yeni Kök ve Ara CA'ları kabul olduğundan emin olur. 

- Microsoft Teams, Skype, Skype Kurumsal Online veya Microsoft Dynamics API'leriyle tümleştirilmiş bir uygulama kullanıyorsanız ve bu uygulamanın sertifika sabitlemeyi kullandığından emin değilseniz, uygulama satıcısına başvurun.

- Azure hizmetleriyle iletişim kuran farklı işletim sistemleri ve dil çalışma zamanları yeni sertifika zincirlerini doğru biçimde oluşturmak ve doğrulamak için başka adımlar gerekli olabilir:
   - **Linux**: Birçok dağıtım için AA eklemeniz gerekmektedir `/etc/ssl/certs`. Belirli yönergeler için dağıtım belgelerine bakın.
   - **Java**: Java anahtar deposunın yukarıda listelenen CA'ları içerdiğine emin olur.
   - **Windows** kapalı ortamlarda çalışır: Bağlantısı kesik ortamlarda çalışan sistemlerin, depolamalarına yeni Kök CA'ların `Trusted Root Certification Authorities` ve depolarına yeni Ara CA'ların eklenmiş olması `Intermediate Certification Authorities` gerekir.
   - **Android**: Cihazınızın ve Android sürümünizin belgelerini kontrol edin.
   - **IoT veya eklenmiş cihazlar**: TV set top kutuları gibi ekli cihazlar çoğunlukla sınırlı bir kök yetkili sertifika kümesiyle birlikte gönderteler ve sertifika depolarını güncelleştirmenin kolay bir yolu yoktur. Özel eklenmiş veya IoT cihazlarının dağıtımları için kod yazar veya bu cihazları yönetirken cihazların yeni Kök CA'lara güvene sahip olduğundan emin olun. Cihaz üreticisine başvurun.

- Güvenlik duvarı kurallarının yalnızca belirli uç noktalara giden çağrılara izin olduğu bir ortamınız varsa, aşağıdaki Sertifika İptal Listesi (CRL) veya Çevrimiçi Sertifika Durumu Protokolü (OCSP) URL'lerine izin verme:
   - `http://crl3.digicert.com`
   - `http://crl4.digicert.com`
   - `http://ocsp.digicert.com`
   - `http://crl.microsoft.com`
   - `http://oneocsp.microsoft.com`
   - `http://ocsp.msocsp.com`
   - `http://www.microsoft.com/pkiops`

- Bu değişiklik sizi etkiliyorsa, içinde çalıştırılacak ortamın türüne ve etkilenen senaryoya bağlı hata iletileri alabilirsiniz. Aşağıdaki Windows için Uygulama olay günlüklerini, CAPI2 olay günlüklerini ve özel uygulama günlüklerini denetleme:
   ```output
   An operation failed because the following certificate has validation errors:
   
   Subject Name: CN=teams.microsoft.com
   Issuer Name: CN=Microsoft Azure TLS Issuing CA 01, O=Microsoft Corporation, C=US
   
   Errors:
   
   The root of the certificate chain is not a trusted root authority.
   ```

## <a name="when-can-i-retire-the-old-ca-information"></a>Eski CA bilgilerini ne zaman kaldıracak?

Geçerli Kök CA, Ara CA ve yaprak sertifikaları iptal edil olmayacaktır. Var olan CA Ortak Adları ve/veya baş parmak yazdırmaları, mevcut sertifikaların kullanım ömrüne bağlı olarak en az Ekim 2023'e kadar gereklidir.
