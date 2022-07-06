---
title: Office TLS sertifika değişiklikleri
description: Office TLS sertifikalarında yapılacak değişikliklere hazırlanma.
author: pshelton-skype
ms.author: pshelton
manager: toddbeckett
ms.topic: article
audience: Developer
ms.date: 3/7/2022
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.openlocfilehash: 65b0ffd5d605302dd62369471b65c1ac10aacd40
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641778"
---
# <a name="office-tls-certificate-changes"></a>Ofis TLS Sertifika Değişiklikleri

Microsoft 365, farklı bir Kök Sertifika Yetkilileri (CA) kümesindeki TLS sertifikalarını kullanmak için mesajlaşma, toplantı, telefon, ses ve video desteği sunan hizmetleri güncelleştiriyor. Geçerli Kök CA'nın süresi Mayıs 2025'te dolacağından bu değişiklik yapılıyor.

Etkilenen ürünler şunlardır:
- Microsoft Teams
- Skype
- Skype Kurumsal Çevrimiçi
- Microsoft Dynamics 365
- GroupMe
- Kaizala
- Azure İletişim Hizmetleri

Etkilenen uç noktalar şunlardır (ancak bunlarla sınırlı değildir):
- *.teams.microsoft.com
- *.skype.com
- *.skypeforbusiness.com
- *.groupme.com
- *.communication.azure.com
- *.operatorconnect.microsoft.com

Ayrıca Microsoft 365'in US Government ulusal bulut örneklerindeki Teams ve Skype Kurumsal Online uç noktaları aynı değişikliği yaparak aşağıdaki gibi uç noktaları etkiler:
- *.gcc.teams.microsoft.com
- *.dod.teams.microsoft.us
- *.gov.teams.microsoft.us
- *.online.dod.skypeforbusiness.us
- *.online.gov.skypeforbusiness.us
- *.um-dod.office365.us
- *.um.office365.us

Bu değişiklik, Microsoft 365'in Çin veya Almanya ulusal bulut örneklerinde kullanılan sertifikaları, etki alanlarını veya hizmetleri etkilemez.

Bu makaledeki tüm sertifika bilgileri daha önce Ekim 2020'den sonra [Microsoft 365 şifreleme zincirlerinde](./encryption-office-365-certificate-chains.md) sağlanmıştır.

## <a name="when-will-this-change-happen"></a>Bu değişiklik ne zaman gerçekleşecek?

Hizmetler Ocak 2022'de yeni Kök CA'lara geçiş yapmaya başladı ve Ekim 2022'ye kadar devam edecek.

## <a name="what-is-changing"></a>Değişen nedir?

Bugün, Microsoft 365 hizmetleri tarafından kullanılan TLS sertifikalarının çoğu aşağıdaki Kök CA'ya bağlıdır:

| CA'nın Ortak Adı | Parmak izi (SHA1) |
|--|--|
| [Baltimore CyberTrust Kökü](https://cacerts.digicert.com/BaltimoreCyberTrustRoot.crt) | d4de20d05e66fc53fe1a50882c78db2852cae474 |

aşağıdaki Ara CA'lardan biriyle:

| CA'nın Ortak Adı | Parmak izi (SHA1) |
|--|--|
| [Microsoft RSA TLS CA 01](https://www.microsoft.com/pki/mscorp/Microsoft%20RSA%20TLS%20CA%2001.crt) | 703d7a8f0ebf55aaa59f98eaf4a206004eb2516a |
| [Microsoft RSA TLS CA 02](https://www.microsoft.com/pki/mscorp/Microsoft%20RSA%20TLS%20CA%2002.crt) | b0c2d2d13cdd56cdaa6ab6e2c04440be4a429c75 |

Microsoft 365 hizmetleri tarafından kullanılan yeni TLS sertifikaları artık aşağıdaki Kök CA'lardan birine zincirlenecek:

| CA'nın Ortak Adı | Parmak izi (SHA1) |
|--|--|
| [DigiCert Genel Kök G2](https://cacerts.digicert.com/DigiCertGlobalRootG2.crt) | df3c24f9bfd666761b268073fe06d1cc8d4f82a4 |
| [Microsoft RSA Kök Sertifika Yetkilisi 2017](https://www.microsoft.com/pkiops/certs/Microsoft%20RSA%20Root%20Certificate%20Authority%202017.crt) | 73a5e64a3bff8316ff0edccc618a906e4eae4d74 | 
| [Microsoft ECC Kök Sertifika Yetkilisi 2017](https://www.microsoft.com/pkiops/certs/Microsoft%20ECC%20Root%20Certificate%20Authority%202017.crt) | 999a64c37ff47d9fab95f14769891460eec4c3c5 |

aşağıdaki Ara CA'lardan biriyle:

| CA'nın Ortak Adı | Parmak izi (SHA1) |
|--|--|
| [Microsoft Azure TLS Veren CA 01](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2001%20-%20xsign.crt) | 2f2877c5d778c31e0f29c7e371df5471bd673173 |
| [Microsoft Azure TLS Veren CA 02](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2002%20-%20xsign.crt) | e7eea674ca718e3befd90858e09f8372ad0ae2aa |
| [Microsoft Azure TLS Veren CA 05](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2005%20-%20xsign.crt) | 6c3af02e7f269aa73afd0eff2a88a4a1f04ed1e5 |
| [Microsoft Azure TLS Veren CA 06](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2006%20-%20xsign.crt) | 30e01761ab97e59a06b41ef20af6f2de7ef4f7b0 |

Örneğin, bu yeni sertifika zincirlerinden birine sahip geçerli bir sertifikadır:

![Teams TLS Sertifika Zinciri](../media/teams-tls-certificate-chain.png)

## <a name="will-this-change-affect-me"></a>Bu değişiklik beni etkileyecek mi?

Kök CA "DigiCert Global Root G2", Windows, macOS, Android ve iOS gibi işletim sistemleri ve Microsoft Edge, Chrome, Safari ve Firefox gibi tarayıcılar tarafından yaygın olarak güvenilirdir. **Microsoft 365 müşterilerinin çoğunun etkilenmemesini** bekliyoruz. 

Ancak uygulamanız **açıkça kabul edilebilir CA'ların listesini belirtiyorsa etkilenebilir**. Bu uygulama "sertifika sabitleme" olarak bilinir. Kabul edilebilir CA'lar listesinde yeni Kök CA'ları olmayan müşteriler, uygulamanızın kullanılabilirliğini veya işlevini etkileyebilecek sertifika doğrulama hataları alır.

Uygulamanızın etkilenip etkilenmeyebileceğini algılamanın bazı yolları şunlardır:

- Kaynak kodunuzda parmak izi, Ortak Ad veya burada bulunan Ara CA'lardan herhangi birinin diğer özelliklerini [arayın](https://www.microsoft.com/pki/mscorp/cps/default.htm). Eşleşme varsa uygulamanız etkilenir. Bu sorunu çözmek için kaynak kodu güncelleştirerek yeni CA'ların özelliklerini ekleyin. En iyi uygulama olarak, CA'ların kısa sürede eklendiğinden veya düzenlenebildiğine emin olun. Sektör düzenlemeleri, ca sertifikalarının bazı durumlarda yedi gün içinde değiştirilmesini gerektirdiği için sertifika sabitleme uygulayan uygulamaların bu değişikliklere hızlı bir şekilde tepki vermesi gerekir.

- .NET, geliştiricilerin sertifikaların `System.Net.HttpWebRequest.ServerCertificateValidationCallback` standart Windows sertifika deposuna güvenmek yerine geçerli olup olmadığını belirlemek için özel mantık kullanmasına olanak tanıyan ve geri çağırma işlevlerini kullanıma sunar`System.Net.ServicePointManager.ServerCertificateValidationCallback`. Bir geliştirici, belirli bir Ortak Adı veya parmak izini denetleyan veya yalnızca "Baltimore CyberTrust Root" gibi belirli bir Kök CA'ya izin veren mantık ekleyebilir. Uygulamanız bu geri çağırma işlevlerini kullanıyorsa hem eski hem de yeni Kök ve Ara CA'ları kabul edin.

- Yerel uygulamalar, yerel uygulamaların özel sertifika doğrulama mantığı uygulamasına izin veren uygulamasını kullanıyor `WINHTTP_CALLBACK_STATUS_SENDING_REQUEST`olabilir. Bu bildirimin kullanımı nadirdir ve uygulanması için önemli miktarda özel kod gerektirir. Yukarıdakine benzer şekilde, uygulamanızın hem eski hem de yeni Kök ve Ara CA'ları kabul etmesini sağlayın. 

- Microsoft Teams, Skype, Skype Kurumsal Online veya Microsoft Dynamics API'leriyle tümleşen bir uygulama kullanıyorsanız ve sertifika sabitleme kullanıp kullanmadığınızdan emin değilseniz uygulama satıcısına başvurun.

- Azure hizmetleriyle iletişim kuran farklı işletim sistemleri ve dil çalışma zamanları, yeni sertifika zincirlerini doğru şekilde oluşturmak ve doğrulamak için başka adımlar gerektirebilir:
   - **Linux**: Birçok dağıtım, öğesine CA'lar `/etc/ssl/certs`eklemenizi gerektirir. Belirli yönergeler için dağıtımın belgelerine bakın.
   - **Java**: Java anahtar deposunun yukarıda listelenen CA'ları içerdiğinden emin olun.
   - **Bağlantısız ortamlarda çalışan Windows: Bağlantısız** ortamlarda çalışan sistemlerin depolarına yeni Kök CA'ların ve depolarına `Trusted Root Certification Authorities` yeni Ara CA'ların eklenmesi `Intermediate Certification Authorities` gerekir.
   - **Android**: Cihazınızın ve Android sürümünün belgelerine bakın.
   - **IoT veya katıştırılmış cihazlar**: TV kümesi üst kutuları gibi ekli cihazlar genellikle sınırlı bir kök yetkili sertifikası kümesiyle birlikte sevk eder ve sertifika deposunu güncelleştirmenin kolay bir yolu yoktur. Özel katıştırılmış veya IoT cihazları için kod yazıyorsanız veya dağıtımlarını yönetiyorsanız, cihazların yeni Kök CA'lara güvendiğinden emin olun. Cihaz üreticisine başvurmanız gerekebilir.

- Güvenlik duvarı kurallarının yalnızca belirli uç noktalara giden çağrılara izin veren bir ortamınız varsa, aşağıdaki Sertifika İptal Listesi (CRL) veya Çevrimiçi Sertifika Durumu Protokolü (OCSP) URL'lerine izin verin:
   - `http://crl3.digicert.com`
   - `http://crl4.digicert.com`
   - `http://ocsp.digicert.com`
   - `http://crl.microsoft.com`
   - `http://oneocsp.microsoft.com`
   - `http://ocsp.msocsp.com`
   - `http://www.microsoft.com/pkiops`

- Bu değişiklik sizi etkiliyorsa, çalıştırdığınız ortamın türüne ve etkilendiğiniz senaryoya bağlı hata iletileri görebilirsiniz. Aşağıdaki gibi görünen iletiler için Windows Uygulaması olay günlüklerini, CAPI2 olay günlüklerini ve özel uygulama günlüklerini denetleyin:
   ```output
   An operation failed because the following certificate has validation errors:
   
   Subject Name: CN=teams.microsoft.com
   Issuer Name: CN=Microsoft Azure TLS Issuing CA 01, O=Microsoft Corporation, C=US
   
   Errors:
   
   The root of the certificate chain is not a trusted root authority.
   ```

## <a name="when-can-i-retire-the-old-ca-information"></a>Eski CA bilgilerini ne zaman devre dışı bırakabilirim?

Geçerli Kök CA, Ara CA ve yaprak sertifikalar iptal edilmeyecek. Mevcut CA Ortak Adları ve/veya parmak izleri, mevcut sertifikaların kullanım ömrüne bağlı olarak en az Ekim 2023'e kadar gerekli olacaktır.

## <a name="known-issues"></a>Bilinen Sorunlar

Çok nadir durumlarda, kuruluş kullanıcıları Kök CA "DigiCert Genel Kök G2" iptal edilmiş olarak göründüğü sertifika doğrulama hataları görebilir. Bunun nedeni, aşağıdaki koşulların her ikisinde de bilinen bir Windows hatasıdır:

- Kök CA [CurrentUser\Root sertifika deposunda](/windows/win32/seccrypto/system-store-locations#cert_system_store_current_user) ve özellikleri eksik `NotBeforeFileTime` `NotBeforeEKU`
- Kök CA da [LocalMachine\AuthRoot sertifika deposundadır](/windows/win32/seccrypto/system-store-locations#cert_system_store_local_machine), ancak hem hem `NotBeforeEKU` de özelliklerine `NotBeforeFileTime` sahiptir

bu Kök CA'dan `NotBeforeFileTime` verilen tüm yaprak sertifikalar iptal edilmiş olarak görünür. 

Yöneticiler bu hata için CAPI2 Günlüğünü inceleyerek sorunu tanımlayabilir ve giderebilir:

```text
Log Name:      Microsoft-Windows-CAPI2/Operational
Source:        Microsoft-Windows-CAPI2
Date:          6/23/2022 8:36:39 AM
Event ID:      11
Task Category: Build Chain
Level:         Error
[...]
        <ChainElement>
          <Certificate fileRef="DF3C24F9BFD666761B268073FE06D1CC8D4F82A4.cer" subjectName="DigiCert Global Root G2" />
          [...]
          <TrustStatus>
            <ErrorStatus value="4000024" CERT_TRUST_IS_REVOKED="true" CERT_TRUST_IS_UNTRUSTED_ROOT="true" CERT_TRUST_IS_EXPLICIT_DISTRUST="true" />
            <InfoStatus value="10C" CERT_TRUST_HAS_NAME_MATCH_ISSUER="true" CERT_TRUST_IS_SELF_SIGNED="true" CERT_TRUST_HAS_PREFERRED_ISSUER="true" />
          </TrustStatus>
          [...]
          <RevocationInfo freshnessTime="PT0S">
            <RevocationResult value="80092010">The certificate is revoked.</RevocationResult>
          </RevocationInfo>
        </ChainElement>
      </CertificateChain>
      <EventAuxInfo ProcessName="Teams.exe" />
      <Result value="80092010">The certificate is revoked.</Result>
```
öğesinin varlığına `CERT_TRUST_IS_EXPLICIT_DISTRUST="true"` dikkat edin. 

Aşağıdaki `certutil` komutları çalıştırıp çıkışı karşılaştırarak Kök CA'nın farklı `NotBeforeFileTime` özelliklere sahip iki kopyasının mevcut olduğunu onaylayabilirsiniz:

```
certutil -store -v authroot DF3C24F9BFD666761B268073FE06D1CC8D4F82A4
certutil -user -store -v root DF3C24F9BFD666761B268073FE06D1CC8D4F82A4
```

Kullanıcı, sertifika deposundaki Kök CA'nın `CurrentUser\Root` kopyasını silerek sorunu çözebilir:
```
certutil -user -delstore root DF3C24F9BFD666761B268073FE06D1CC8D4F82A4
```