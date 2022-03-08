---
title: Veri Kaybı Önleme ilke başvurusu
f1.keywords: CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 03/02/2022
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MET150
ms.assetid: 6501b5ef-6bf7-43df-b60d-f65781847d6c
ms.collection:
- M365-security-compliance
- SPO_Content
recommendations: false
description: DLP ilkesi bileşeni ve yapılandırma başvurusu
ms.custom: seo-marvel-apr2021
ms.openlocfilehash: d94277ac4ee3bd78feecf660e03d60a5720d1b43
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319427"
---
# <a name="data-loss-prevention-policy-reference"></a>Veri Kaybı Önleme ilke başvurusu

Veri kaybı önleme (DLP) ilkelerinin yapılandırılan birçok bileşeni vardır. Etkili bir ilke oluşturmak için, her bileşenin amacının ne olduğunu ve bunun yapılandırmasının ilkenin davranışını nasıl değiştir yaptığını anlamanız gerekir. Bu makalede, DLP ilkelerinin ayrıntılı anatomisi açıklanmıştır.

## <a name="policy-templates"></a>İlke şablonları 

DLP ilkesi şablonları dört kategoride önceden sıralandı:

- Finansal bilgi türlerini algılayan ve **koruyanlar** .
- Tıbbi ve sağlık bilgilerini algılayan **ve koruyanlar** .
- Gizlilik bilgisi türlerini algılayan ve koruyan **bilgiler** .
- Diğer **kişilerden** biri sizin kuruluş ihtiyaçlarını karşı karşılamazsa, kendi ilkenizi oluşturmak için kullanabileceğiniz özel bir şablon.

Bu tabloda, tüm ilke şablonları ve bunların kapsıyor olduğu hassas bilgi türleri (SIT) liste vardır. 

güncelleştirme: 23.06.2021

|Kategori| Şablon | SIT |
|---------|---------|---------|
|Finansal| Avustralya Finansal Verileri| - [SWIFT kodu](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Avustralya vergi dosyası numarası](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Avustralya banka hesap numarası](sensitive-information-type-entity-definitions.md#australia-bank-account-number) </br> - [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansal| Kanada Finansal verileri |- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Kanada banka hesap numarası](sensitive-information-type-entity-definitions.md#canada-bank-account-number)|
|Finansal| France Financial data |- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [AB banka kartı numarası](sensitive-information-type-entity-definitions.md#eu-debit-card-number)|
|Finansal| Almanya Finansal Verileri |- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [AB banka kartı numarası](sensitive-information-type-entity-definitions.md#eu-debit-card-number)|
|Finansal| İsrail Finansal Verileri |- [İsrail banka hesap numarası](sensitive-information-type-entity-definitions.md#israel-bank-account-number) </br> - [SWIFT kodu](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansal| Japonya Finansal Verileri |- [Japonya banka hesap numarası](sensitive-information-type-entity-definitions.md#japan-bank-account-number) </br> - [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansal| PCI Veri Güvenliği Standardı (PCI DSS)|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansal| Suudi Arabistan Siber Olay Önleme Yasası|- [SWIFT kodu](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Uluslararası bankacılık hesap numarası (IBAN)](sensitive-information-type-entity-definitions.md#international-banking-account-number-iban) |
|Finansal| Suudi Arabistan Mali Verileri |- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [SWIFT kodu](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Uluslararası bankacılık hesap numarası (IBAN)](sensitive-information-type-entity-definitions.md#international-banking-account-number-iban)|
|Finansal| Birleşik Krallık Finansal Verileri|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [AB banka kartı numarası](sensitive-information-type-entity-definitions.md#eu-debit-card-number) </br> - [SWIFT kodu](sensitive-information-type-entity-definitions.md#swift-code)|
|Finansal| ABD Finansal Verileri|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [ABD banka hesap numarası](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [ABA Yönlendirme Numarası](sensitive-information-type-entity-definitions.md#aba-routing-number)|
|Finansal| ABD Federal Ticaret Komisyonu (FTC) Tüketici Kuralları|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [ABD banka hesap numarası](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [ABA Yönlendirme Numarası](sensitive-information-type-entity-definitions.md#aba-routing-number)|
|Finansal| U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [ABD banka hesap numarası](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [ABD/İngiltere pasaport numarası](sensitive-information-type-entity-definitions.md#usuk-passport-number) </br> -[ABD sürücüsünün lisans numarası](sensitive-information-type-entity-definitions.md#us-drivers-license-number)</br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [ABD Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Finansal| ABD Gramm-Leach-Bliley Act (GLBA)|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [ABD banka hesap numarası](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|Sağlık ve sağlık| Avustralya Sağlık Kayıtları Yasası (HRIP Yasası) Geliştirilmiş |- [Avustralya vergi dosyası numarası](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Avustralya tıbbi hesap numarası](sensitive-information-type-entity-definitions.md#australia-medical-account-number) </br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [Tüm Tıbbi Hüküm ve Koşullar](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [Avustralya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#australia-physical-addresses)|
|Sağlık ve sağlık| Avustralya Sağlık Kayıtları Yasası (HRIP Yasası)|- [Avustralya vergi dosyası numarası](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Avustralya tıbbi hesap numarası](sensitive-information-type-entity-definitions.md#australia-medical-account-number)|
|Sağlık ve sağlık| Kanada Sağlık Bilgileri Yasası (HIA) |- [Kanada pasaport numarası](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Kanada sosyal sigorta numarası](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Kanada sağlık hizmet numarası](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Kanada Kişisel Sağlık Kimlik Numarası](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Sağlık ve sağlık| Kanada Kişisel Sağlık Bilgileri Yasası (PHIA) Manitoba|- [Kanada sosyal sigorta numarası](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Kanada sağlık hizmet numarası](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Kanada Kişisel Sağlık Kimlik Numarası](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Sağlık ve sağlık| Kanada Kişisel Sağlık Yasası (PHIPA) Ontario |- [Kanada pasaport numarası](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Kanada sosyal sigorta numarası](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Kanada sağlık hizmet numarası](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Kanada Kişisel Sağlık Kimlik Numarası](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Sağlık ve sağlık| B.K. Tıbbi Raporlara Erişim Yasası|- [ABD ulusal sağlık hizmet numarası](sensitive-information-type-entity-definitions.md#uk-national-health-service-number) </br> - [U.K. ulusal sigorta numarası (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino)|
|Sağlık ve sağlık| ABD Sağlık Sigortası Yasası (HIPAA) Geliştirilmiş|</br> - [Uluslararası hastalık sınıflandırması (ICD-9-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-9-cm) </br> - [Ulusal hukuk sınıflandırması (ICD-10-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-10-cm) </br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [Tüm Tıbbi Hüküm ve Koşullar](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [ABD Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Sağlık ve sağlık| ABD Sağlık Sigortası Yasası (HIPAA)| - [Uluslararası hastalık sınıflandırması (ICD-9-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-9-cm) </br> - [Ulusal hukuk sınıflandırması (ICD-10-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-10-cm)|
|Gizlilik| Avustralya Gizlilik Yasası Geliştirilmiş|- [Avustralya sürücüsünün lisans numarası](sensitive-information-type-entity-definitions.md#australia-drivers-license-number) </br> - [Avustralya pasaport numarası](sensitive-information-type-entity-definitions.md#australia-passport-number) </br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [Tüm Tıbbi Hüküm ve Koşullar](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [Avustralya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#australia-physical-addresses)|
|Gizlilik| Avustralya Gizlilik Yasası|- [Avustralya sürücüsünün lisans numarası](sensitive-information-type-entity-definitions.md#australia-drivers-license-number) </br> - [Avustralya pasaport numarası](sensitive-information-type-entity-definitions.md#australia-passport-number)|
|Gizlilik| Avustralya Kişisel Bilgileri (PII) Verileri|- [Avustralya vergi dosyası numarası](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Avustralya sürücüsünün lisans numarası](sensitive-information-type-entity-definitions.md#australia-drivers-license-number)|
|Gizlilik| Kanada Kişisel Bilgileri (PII) Verileri|- [Kanada sürücüsünün lisans numarası](sensitive-information-type-entity-definitions.md#canada-drivers-license-number)</br> - [Kanada banka hesap numarası](sensitive-information-type-entity-definitions.md#canada-bank-account-number) </br> - [Kanada pasaport numarası](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Kanada sosyal sigorta numarası](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Kanada sağlık hizmet numarası](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Kanada Kişisel Sağlık Kimlik Numarası](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Gizlilik| Kanada Kişisel Bilgi Koruma Yasası (PIPA)|- [Kanada pasaport numarası](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Kanada sosyal sigorta numarası](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Kanada sağlık hizmet numarası](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Kanada Kişisel Sağlık Kimlik Numarası](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Gizlilik| Kanada Kişisel Bilgi Koruma Yasası (PIPEDA)|- [Kanada sürücüsünün lisans numarası](sensitive-information-type-entity-definitions.md#canada-drivers-license-number) </br> - [Kanada banka hesap numarası](sensitive-information-type-entity-definitions.md#canada-bank-account-number) </br> - [Kanada pasaport numarası](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Kanada sosyal sigorta numarası](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Kanada sağlık hizmet numarası](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Kanada Kişisel Sağlık Kimlik Numarası](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Gizlilik| Fransa Veri Koruma Yasası|- [Fransa ulusal kimlik kartı (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni) </br> - [Fransa sosyal güvenlik numarası (INSEE)](sensitive-information-type-entity-definitions.md#france-social-security-number-insee)|
|Gizlilik| Fransa Kişisel Bilgileri (PII) Verileri|- [Fransa sosyal güvenlik numarası (INSEE)](sensitive-information-type-entity-definitions.md#france-social-security-number-insee) </br> - [Fransa sürücü lisans numarası](sensitive-information-type-entity-definitions.md#france-drivers-license-number) </br> - [Fransa pasaport numarası](sensitive-information-type-entity-definitions.md#france-passport-number) </br> - [Fransa ulusal kimlik kartı (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni)|
|Gizlilik| Gelişmiş Genel Veri Koruma Yönetmeliği (GDPR)|- [Avusturya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#austria-physical-addresses) </br> - [Belçika Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#belgium-physical-addresses)</br> - [Bulgaristan Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#bulgaria-physical-addresses)</br> - [Hırvatistan Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#croatia-physical-addresses)</br> - [Kıbrıs Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#cyprus-physical-addresses)</br> - [Çek Cumhuriyeti Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#czech-republic-physical-addresses)</br> - [Danimarka Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#denmark-physical-addresses)</br> - [Estonya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#estonia-physical-addresses)</br> - [Finlandiya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#finland-physical-addresses)</br> - [Fransa Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#france-physical-addresses)</br> - [Almanya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#germany-physical-addresses)</br> - [Yunanistan Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#greece-physical-addresses)</br> - [Macaristan Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#hungary-physical-addresses)</br> - [İrlanda Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#ireland-physical-addresses)</br> - [İtalya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#italy-physical-addresses)</br> - [Letonya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#latvia-physical-addresses)</br> - [Litvanya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#lithuania-physical-addresses)</br> - [Luxembourg Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#luxemburg-physical-addresses)</br> - [Malta Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#malta-physical-addresses)</br> - [Hollanda Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#netherlands-physical-addresses)</br> - [Polonya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#poland-physical-addresses)</br> - [Portekizce Fiziksel Adresler](sensitive-information-type-entity-definitions.md#portugal-physical-addresses)</br> - [Romanya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#romania-physical-addresses)</br> - [Slovakya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#slovakia-physical-addresses)</br> - [Slovenya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#slovenia-physical-addresses)</br> - [İspanya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#spain-physical-addresses)</br> - [İsveç Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#sweden-physical-addresses)</br> - [Avusturya Sosyal Güvenlik Numarası](sensitive-information-type-entity-definitions.md#austria-social-security-number)</br> - [France Social Security Number (INSEE)](sensitive-information-type-entity-definitions.md#france-social-security-number-insee)</br> - [Yunanistan Sosyal Güvenlik Numarası (AMKA)](sensitive-information-type-entity-definitions.md#greece-social-security-number-amka)</br> - [Macarca Sosyal Güvenlik Numarası (TAJ)](sensitive-information-type-entity-definitions.md#hungary-social-security-number-taj)</br> - [İspanya Sosyal Güvenlik Numarası (SSN)](sensitive-information-type-entity-definitions.md#spain-social-security-number-ssn)</br> - [Avusturya Kimlik Kartı](sensitive-information-type-entity-definitions.md#austria-identity-card)</br> - [Kıbrıs Kimlik Kartı](sensitive-information-type-entity-definitions.md#cyprus-identity-card)</br> - [Almanya Kimlik Kartı Numarası](sensitive-information-type-entity-definitions.md#germany-identity-card-number)</br> - [Malta Kimlik Kartı Numarası](sensitive-information-type-entity-definitions.md#malta-identity-card-number)</br> - [Fransa Ulusal Kimlik Kartı (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni)</br> - [Yunanistan Ulusal Kimlik Kartı](sensitive-information-type-entity-definitions.md#greece-national-id-card)</br> - [Finlandiya Ulusal Kimliği](sensitive-information-type-entity-definitions.md#finland-national-id)</br> - [Polonya Ulusal Kimliği (PESEL)](sensitive-information-type-entity-definitions.md#poland-national-id-pesel)</br> - [İsveç Ulusal Kimliği](sensitive-information-type-entity-definitions.md#sweden-national-id)</br> - [Hırvatistan Kişisel Kimlik (OIB) Numarası](sensitive-information-type-entity-definitions.md#croatia-personal-identification-oib-number)</br> - [Çek Kişisel Kimlik Numarası](sensitive-information-type-entity-definitions.md#czech-personal-identity-number)</br> - [Danimarka Kişisel Kimlik Numarası](sensitive-information-type-entity-definitions.md#denmark-personal-identification-number)</br> - [Estonya Kişisel Kimlik Kodu](sensitive-information-type-entity-definitions.md#estonia-personal-identification-code)</br> - [Macaristan Kişisel Kimlik Numarası](sensitive-information-type-entity-definitions.md#hungary-personal-identification-number)</br> - [Luxemburg Ulusal Kimlik Numarası (Doğal kişiler)](sensitive-information-type-entity-definitions.md#luxemburg-national-identification-number-natural-persons)</br> - [Luxemburg Ulusal Kimlik Numarası (Doğal olmayan kişiler)](sensitive-information-type-entity-definitions.md#luxemburg-national-identification-number-non-natural-persons)</br> - [İtalya Mali Kodu](sensitive-information-type-entity-definitions.md#italy-fiscal-code)</br> - [Letonya Kişisel Kodu](sensitive-information-type-entity-definitions.md#latvia-personal-code)</br> - [Litvanya Kişisel Kodu](sensitive-information-type-entity-definitions.md#lithuania-personal-code)</br> - [Romanya Kişisel Sayısal Kodu (CNP)](sensitive-information-type-entity-definitions.md#romania-personal-numeric-code-cnp)</br> - [Hollanda Genel Hizmet Numarası (BSN)](sensitive-information-type-entity-definitions.md#netherlands-citizens-service-bsn-number)</br> - [Ireland Personal Public Service (PPS) Numarası](sensitive-information-type-entity-definitions.md#ireland-personal-public-service-pps-number)</br> - [Bulgaristan Muntaz](sensitive-information-type-entity-definitions.md#bulgaria-uniform-civil-number)</br> - [Belçika Ulusal Numarası](sensitive-information-type-entity-definitions.md#belgium-national-number)</br> - [İspanya DNI](sensitive-information-type-entity-definitions.md#spain-dni)</br> - [Slovenya benzersiz ana numarayı](sensitive-information-type-entity-definitions.md#slovenia-unique-master-citizen-number)</br> - [Slovakya Kişisel Numarası](sensitive-information-type-entity-definitions.md#slovakia-personal-number)</br> - [Portekiz Portekiz Kart Numarası](sensitive-information-type-entity-definitions.md#portugal-citizen-card-number)</br> - [Malta Vergi No Numarası](sensitive-information-type-entity-definitions.md#malta-tax-identification-number)</br> - [Avusturya Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#austria-tax-identification-number)</br> - [Kıbrıs Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#cyprus-tax-identification-number)</br> - [Fransa Vergi Tanımlama Numarası (numéro SPI.)](sensitive-information-type-entity-definitions.md#france-tax-identification-number)</br> - [Almanya Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#germany-tax-identification-number)</br> - [Yunan Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#greece-tax-identification-number)</br> - [Macaristan Vergi Tanımlama Numarası](sensitive-information-type-entity-definitions.md#hungary-tax-identification-number)</br> - [Hollanda Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#netherlands-tax-identification-number)</br> - [Polonya Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#poland-tax-identification-number)</br> - [Portekiz Vergi Tanımlama Numarası](sensitive-information-type-entity-definitions.md#portugal-tax-identification-number)</br> - [Slovenya Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#slovenia-tax-identification-number)</br> - [İspanya Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#spain-tax-identification-number)</br> - [İsveç Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#sweden-tax-identification-number)</br> - [Avusturya Sürücü Lisansı](sensitive-information-type-entity-definitions.md#austria-drivers-license-number)</br> - [Belçika Sürücü Lisans Numarası](sensitive-information-type-entity-definitions.md#belgium-drivers-license-number)</br> - [Bulgaristan Sürücü Lisans Numarası](sensitive-information-type-entity-definitions.md#bulgaria-drivers-license-number)</br> - [Hırvatistan Sürücüsü Lisans Numarası](sensitive-information-type-entity-definitions.md#croatia-drivers-license-number)</br> - [Kıbrıs Sürücüsü Lisans Numarası](sensitive-information-type-entity-definitions.md#cyprus-drivers-license-number)</br> - [Çek Sürücüsü Lisans Numarası](sensitive-information-type-entity-definitions.md#czech-drivers-license-number)</br> - [Danimarka Sürücüsü Lisans Numarası](sensitive-information-type-entity-definitions.md#denmark-drivers-license-number)</br> - [Estonya Sürücü Lisans Numarası](sensitive-information-type-entity-definitions.md#estonia-drivers-license-number)</br> - [Finlandiya Sürücüsü Lisans Numarası](sensitive-information-type-entity-definitions.md#finland-drivers-license-number)</br> - [Fransa Sürücü Lisans Numarası](sensitive-information-type-entity-definitions.md#france-drivers-license-number)</br> - [Almanca Sürücü Lisans Numarası](sensitive-information-type-entity-definitions.md#germany-drivers-license-number)</br> - [Yunanistan Sürücü Lisans Numarası](sensitive-information-type-entity-definitions.md#greece-drivers-license-number)</br> - [Macaristan Sürücü Lisans Numarası](sensitive-information-type-entity-definitions.md#hungary-drivers-license-number)</br> - [İrlanda Sürücü Lisans Numarası](sensitive-information-type-entity-definitions.md#ireland-drivers-license-number)</br> - [İtalya Sürücüsü Lisans Numarası](sensitive-information-type-entity-definitions.md#italy-drivers-license-number)</br> - [Letonya Sürücüsü Lisans Numarası](sensitive-information-type-entity-definitions.md#latvia-drivers-license-number)</br> - [Litvanya Sürücü Lisans Numarası](sensitive-information-type-entity-definitions.md#lithuania-drivers-license-number)</br> - [Luxemburg Sürücü Lisans Numarası](sensitive-information-type-entity-definitions.md#luxemburg-drivers-license-number)</br> - [Malta Sürücü Lisans Numarası](sensitive-information-type-entity-definitions.md#malta-drivers-license-number)</br> - [Hollanda Sürücü Lisans Numarası](sensitive-information-type-entity-definitions.md#netherlands-drivers-license-number)</br> - [Polonya Sürücü Lisans Numarası](sensitive-information-type-entity-definitions.md#poland-drivers-license-number)</br> - [Portekiz Sürücü Lisans Numarası](sensitive-information-type-entity-definitions.md#portugal-drivers-license-number)</br> - [Romanya Sürücü Lisans Numarası](sensitive-information-type-entity-definitions.md#romania-drivers-license-number)</br> - [Slovakya Sürücüsü Lisans Numarası](sensitive-information-type-entity-definitions.md#slovakia-drivers-license-number)</br> - [Slovenya Sürücüsü Lisans Numarası](sensitive-information-type-entity-definitions.md#slovenia-drivers-license-number)</br> - [İspanya Sürücüsü Lisans Numarası](sensitive-information-type-entity-definitions.md#spain-drivers-license-number)</br> - [İsveç Sürücü Lisans Numarası](sensitive-information-type-entity-definitions.md#sweden-drivers-license-number)</br> - [Avusturya Pasaport Numarası](sensitive-information-type-entity-definitions.md#austria-passport-number)</br> - [Belçika Pasaport Numarası](sensitive-information-type-entity-definitions.md#belgium-passport-number)</br> - [Bulgaristan Pasaport Numarası](sensitive-information-type-entity-definitions.md#bulgaria-passport-number)</br> - [Hırvatistan Pasaport Numarası](sensitive-information-type-entity-definitions.md#croatia-passport-number)</br> - [Kıbrıs Pasaport Numarası](sensitive-information-type-entity-definitions.md#cyprus-passport-number)</br> - [Çek Cumhuriyeti Pasaport Numarası](sensitive-information-type-entity-definitions.md#czech-passport-number)</br> - [Danimarka Pasaport Numarası](sensitive-information-type-entity-definitions.md#denmark-passport-number)</br> - [Estonya Pasaport Numarası](sensitive-information-type-entity-definitions.md#estonia-passport-number)</br> - [Finlandiya Pasaport Numarası](sensitive-information-type-entity-definitions.md#finland-passport-number)</br> - [Fransa Pasaport Numarası](sensitive-information-type-entity-definitions.md#france-passport-number)</br> - [Almanca Pasaport Numarası](sensitive-information-type-entity-definitions.md#germany-passport-number)</br> - [Yunanistan Pasaport Numarası](sensitive-information-type-entity-definitions.md#greece-passport-number)</br> - [Macaristan Pasaport Numarası](sensitive-information-type-entity-definitions.md#hungary-passport-number)</br> - [İrlanda Pasaport Numarası](sensitive-information-type-entity-definitions.md#ireland-passport-number)</br> - [İtalya Pasaport Numarası](sensitive-information-type-entity-definitions.md#italy-passport-number)</br> - [Letonya Pasaport Numarası](sensitive-information-type-entity-definitions.md#latvia-passport-number)</br> - [Litvanya Pasaport Numarası](sensitive-information-type-entity-definitions.md#lithuania-passport-number)</br> - [Luxemburg Passport Numarası](sensitive-information-type-entity-definitions.md#luxemburg-passport-number)</br> - [Malta Pasaport Numarası](sensitive-information-type-entity-definitions.md#malta-passport-number)</br> - [Hollanda Pasaport Numarası](sensitive-information-type-entity-definitions.md#netherlands-passport-number)</br> - [Polonya Pasaport](sensitive-information-type-entity-definitions.md#poland-passport-number)</br> - [Portekiz Pasaport Numarası](sensitive-information-type-entity-definitions.md#portugal-passport-number)</br> - [Romanya Pasaport Numarası](sensitive-information-type-entity-definitions.md#romania-passport-number)</br> - [Slovakya Pasaport Numarası](sensitive-information-type-entity-definitions.md#slovakia-passport-number)</br> - [Slovenya Pasaport Numarası](sensitive-information-type-entity-definitions.md#slovenia-passport-number)</br> - [İspanya Pasaport Numarası](sensitive-information-type-entity-definitions.md#spain-passport-number)</br> - [İsveç Pasaport Numarası](sensitive-information-type-entity-definitions.md#sweden-passport-number)</br> - [AB Banka Kartı Numarası](sensitive-information-type-entity-definitions.md#eu-debit-card-number)</br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names)|
|Gizlilik| Genel Veri Koruma Yönetmeliği (GDPR)|- [AB banka kartı numarası](sensitive-information-type-entity-definitions.md#eu-debit-card-number) </br> - [AB sürücü lisans numarası](sensitive-information-type-entity-definitions.md#eu-drivers-license-number) </br> - [AB ulusal kimlik numarası](sensitive-information-type-entity-definitions.md#eu-national-identification-number)</br> - [AB pasaport numarası](sensitive-information-type-entity-definitions.md#eu-passport-number) </br> - [AB sosyal güvenlik numarası veya eşdeğer tanımlama](sensitive-information-type-entity-definitions.md#eu-social-security-number-or-equivalent-identification)</br> - [AB Vergi tanımlama numarası](sensitive-information-type-entity-definitions.md#eu-tax-identification-number)|
|Gizlilik| Almanya Kişisel Bilgileri (PII) Verileri|- [Almanya sürücü lisans numarası](sensitive-information-type-entity-definitions.md#germany-drivers-license-number) </br> - [Almanya pasaport numarası](sensitive-information-type-entity-definitions.md#germany-passport-number)| 
|Gizlilik| İsrail Kişisel Bilgileri (PII) Verileri|- [İsrail ulusal kimlik numarası](sensitive-information-type-entity-definitions.md#israel-national-identification-number)| 
|Gizlilik| İsrail Gizliliği Koruma|- [İsrail ulusal kimlik numarası](sensitive-information-type-entity-definitions.md#israel-national-identification-number)</br> - [İsrail banka hesap numarası](sensitive-information-type-entity-definitions.md#israel-bank-account-number)|
|Gizlilik| Geliştirilmiş Japonya Kişisel Bilgileri (PII) Verileri|- [Japonya Sosyal Sigorta Numarası (SN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)</br> - [Japonya Numaram - Kişisel](sensitive-information-type-entity-definitions.md#japan-my-number---personal)</br> - [Japonya pasaport numarası](sensitive-information-type-entity-definitions.md#japan-passport-number)</br> - [Japonya sürücü lisans numarası](sensitive-information-type-entity-definitions.md#japan-drivers-license-number)</br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Japonya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#all-physical-addresses)|
|Gizlilik| Japonya Kişisel Bilgileri (PII) Verileri|- [Japonya'daki yerleşik kayıt numarası](sensitive-information-type-entity-definitions.md#japan-resident-registration-number) </br> - [Japonya Sosyal Sigorta Numarası (SN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)|
|Gizlilik| Geliştirilmiş Kişisel Bilgilerin Japonya Koruması|- [Japonya Sosyal Sigorta Numarası (SN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin) </br> - [Japonya Numaram - Kişisel](sensitive-information-type-entity-definitions.md#japan-my-number---personal)</br> - [Japonya pasaport numarası](sensitive-information-type-entity-definitions.md#japan-passport-number) </br> - [Japonya sürücü lisans numarası](sensitive-information-type-entity-definitions.md#japan-drivers-license-number)</br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Japonya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#all-physical-addresses)|
|Gizlilik| Japonya Kişisel Bilgilerin Korunması|- [Japonya'daki yerleşik kayıt numarası](sensitive-information-type-entity-definitions.md#japan-resident-registration-number)</br> - [Japonya Sosyal Sigorta Numarası (SN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)|
|Gizlilik| Suudi Arabistan Kişisel Kimliğine Tanımlayıcı (PII) Verileri|- [Suudi Arabistan Ulusal Kimliği](sensitive-information-type-entity-definitions.md#saudi-arabia-national-id)|
|Gizlilik| B.K. Veri Koruma Yasası|- [U.K. ulusal sigorta numarası (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [ABD/İngiltere pasaport numarası](sensitive-information-type-entity-definitions.md#usuk-passport-number) </br> - [SWIFT kodu](sensitive-information-type-entity-definitions.md#swift-code)|
|Gizlilik| B.K. Gizlilik ve Elektronik İletişim Düzenlemeleri|- [SWIFT kodu](sensitive-information-type-entity-definitions.md#swift-code)|
|Gizlilik| B.K. Kişisel Kimliği Tanımlayıcı Bilgiler (PII) Verileri|- [U.K. ulusal sigorta numarası (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [ABD/İngiltere pasaport numarası](sensitive-information-type-entity-definitions.md#usuk-passport-number)|
|Gizlilik| B.K. Kişisel Bilgiler Çevrimiçi Uygulama Kodu (PIOCP)|- [U.K. ulusal sigorta numarası (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [ABD ulusal sağlık hizmet numarası](sensitive-information-type-entity-definitions.md#uk-national-health-service-number) </br> - [SWIFT kodu](sensitive-information-type-entity-definitions.md#swift-code)|
|Gizlilik| GELIŞMIŞ ABD S S stiyla Act Enhanced|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [ABD banka hesap numarası](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [ABD Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Gizlilik| ABD S. Act|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [ABD banka hesap numarası](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|Gizlilik| ABD Kişisel Bilgileri (PII) Gelişmiş Verileri|- [ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [ABD/İngiltere pasaport numarası](sensitive-information-type-entity-definitions.md#usuk-passport-number)</br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [ABD Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Gizlilik| ABD Kişisel Bilgileri (PII) Verileri|- [ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [ABD/İngiltere pasaport numarası](sensitive-information-type-entity-definitions.md#usuk-passport-number)|
|Gizlilik| Gelişmiş ABD Eyaleti İhlal Bildirimi Yasaları|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [ABD banka hesap numarası](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> -[ABD sürücüsünün lisans numarası](sensitive-information-type-entity-definitions.md#us-drivers-license-number) </br> - [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [ABD/İngiltere pasaport numarası](sensitive-information-type-entity-definitions.md#usuk-passport-number)</br> - [Tüm Tıbbi Hüküm ve Koşullar](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions)|
|Gizlilik| ABD Eyaleti İhlal Bildirimi Yasaları|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [ABD banka hesap numarası](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> -[ABD sürücüsünün lisans numarası](sensitive-information-type-entity-definitions.md#us-drivers-license-number) </br> - [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|Gizlilik| ABD Eyaleti Sosyal Güvenlik Numarası Gizlilik Yasaları|- [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|

## <a name="locations"></a>Konumlar

DLP ilkesi, birden çok konumda hassas bilgiler içeren öğeleri bulabilir ve koruyabilir.

|Konum  |Kapsam dahil/Dışarıda bırak  |Veri durumu  |Ek önkullar |
|---------|---------|---------|---------|
|Exchange e-postayı çevrimiçi olarak gönderme |dağıtım grubu | data-in-motion| Hayır |
|SharePoint çevrimiçi siteleri   |siteler       | data-at-rest </br> data-in-use | Hayır|
|OneDrive İş hesapları| hesap veya dağıtım grubu |data-at-rest </br> data-in-use|Hayır|
|Teams ve kanal iletilerini gönderme     | hesap veya dağıtım grubu |data-in-motion </br> data-in-use |  Hayır       |
|Bulut Uygulamaları için Microsoft Defender   | bulut uygulama örneği       |data-at-rest         | - [Microsoft dışı bulut uygulamaları için veri kaybı önleme ilkelerini kullanma](dlp-use-policies-non-microsoft-cloud-apps.md#use-data-loss-prevention-policies-for-non-microsoft-cloud-apps)        |
|Cihazlar  |kullanıcı veya grup         |data-at-rest </br>  data-in-use </br>  data-in-motion         |- [Uç nokta Microsoft 365 kaybı önleme hakkında bilgi](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention) </br>- [Uç nokta veri kaybını önlemeye başlama](endpoint-dlp-getting-started.md#get-started-with-endpoint-data-loss-prevention) </br>- [Bilgi Koruması için cihaz ara sunucusunu ve internet bağlantısı ayarlarını yapılandırma](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection) |
|Şirket içi depolar (dosya paylaşımları ve SharePoint)    |depo         | data-at-rest         | - [Şirket içi Microsoft 365 önleme hakkında bilgi](dlp-on-premises-scanner-learn.md#learn-about-the-microsoft-365-data-loss-prevention-on-premises-scanner) </br> - [Şirket içi tarayıcıda veri kaybı önlemeye başlama](dlp-on-premises-scanner-get-started.md#get-started-with-the-data-loss-prevention-on-premises-scanner)         |
|PowerBI| çalışma alanları | data-in-use | Hayır|

Dağıtım grubuna belirli dağıtım gruplarını dahil Exchange, DLP ilkesi yalnızca o grubun üyelerine yöneliktir. Benzer şekilde, bir dağıtım grubu dışlamak, o dağıtım grubunun tüm üyelerini ilke değerlendirmesinde dışlar. Bir ilkenin kapsamını dağıtım listelerinin, dinamik dağıtım gruplarının ve güvenlik gruplarının üyelerine kapsamyı seçmeyi seçebilirsiniz. DLP ilkesi, bu tür dahil edilmeler ve dışlamaların en fazla 50'sine neden olabilir.

Belirli site sitelerini veya SharePoint hesaplarını dahil OneDrive veya hariç tutmayı seçerseniz, DLP ilkesi bu tür dahil edilmesi gereken en fazla 100 site ve dışlama içerebilir. Bu sınır mevcut olsa da, kuruluş genelinde bir ilke veya konumların tamamına uygulanan bir ilke uygulayarak bu sınırı aşabilirsiniz.

Belirli kullanıcı hesaplarını veya gruplarını dahil OneDrive hariç tutmayı seçerseniz, DLP ilkesi dahil edilme veya dışlama olarak en fazla 100 kullanıcı hesabı veya 50 grup içere seçebilir.

### <a name="location-support-for-how-content-can-be-defined"></a>İçeriğin nasıl tanımlan içeriğe sahip olacağını destekleyen konum desteği

DLP ilkeleri hassas öğeleri hassas bir bilgi türüyle (SIT) veya bir duyarlılık etiketiyle veya bekletme etiketiyle eşleştirerek algılar. Her konum, hassas içerik tanımlamanın farklı yöntemlerini destekler. Bir ilkede konumları birleştirerek, içeriğin nasıl tanımlansa bile tek bir konumda tanımlan bir şekilden nasıl tanımlanlandığı değişebilir. 

> [!IMPORTANT]
> Bir ilke için birden çok konum seçimseniz, içerik tanımı kategorisi için "hayır" değeri "evet" değerinden daha öncelikli olur. Örneğin, yalnızca sitelere SharePoint ilke bir veya birden çok SIT tarafından, duyarlılık etiketine veya bekletme etiketine göre hassas öğelerin algılanabilir. Ancak, sohbet ve kanal ***SharePoint konumlarını*** Teams, ilke yalnızca SIT tarafından hassas öğeleri algılamayı destekler.

|Konum| İçerik SIT tarafından tanımlanabilir| İçerik duyarlılık etiketi olarak tanımlanabilir| İçerik bekletme etiketine göre tanımlanabilir|
|---------|---------|---------|---------|
|Exchange e-postayı çevrimiçi olarak gönderme|Evet| Evet| Hayır|
|SharePoint çevrimiçi siteleri| Evet| Evet| Evet|
|OneDrive İş hesapları| Evet| Evet| Evet|
|Teams Sohbet ve Kanal iletilerini gönderme | Evet| Hayır| Hayır|
|Cihazlar |Evet | Evet|  Hayır|
|Bulut Uygulamaları için Microsoft Defender | Evet| Evet| Evet|
|Şirket içi depolar| Evet| Evet| Hayır|
|PowerBI|Evet | Evet| Hayır|

> [!NOTE]
> DLP, e-postalarda ve eklerde duyarlılık etiketlerini algılamayı destekler. Bkz. DLP ilkelerde duyarlılık [etiketlerini koşullar olarak kullanma](dlp-sensitivity-label-as-condition.md#use-sensitivity-labels-as-conditions-in-dlp-policies).

## <a name="rules"></a>Kurallar

<!--This section introduces the classifications of content that, when detected, can be protected. Link out to [Learn about sensitive information types]() and [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) as well as labels (cross referenced by supporting workload). It will touch on the purpose of multiple conditions, confidence levels (link out to [more on confidence levels](sensitive-information-type-learn-about.md#more-on-confidence-levels)) and confidence levels video. How to use the confidence level to change the behavior of a policy in conjunction with the instance count.  eg. if you want your policy to trigger when it encounters situation DEF, set your conditions like HIJ.-->
<!--
- What is a rule in the context of a Policy?
- when and why should I have more than one rule?
- The purpose of rule groups
- How do I tune the behavior of a Policy through the tuning of rules
- what's in a rule-->

Kurallar, DLP ilkelerinin iş mantığıdır. Bunlar şunları oluşur:

- [**Eşlendiğinde**](#conditions) ilkeyi tetikleyen koşullar
- [**Koşullarla**](#exceptions) ilgili özel durumlar
- [**İlke**](#actions) tetiklendiğinde eylemleri
- [**Kullanıcılarınıza,**](#user-notifications-and-policy-tips) bir ilkeyi tetikleyen bir şey yaptığı konusunda bilgi verilmesini sağlar ve onları org'un hassas bilgileri nasıl işlemde olmasını istediği konusunda eğitin
- [**Yönetici tarafından yapılandırıldığında**](#user-overrides) Kullanıcı Geçersiz Kılmaları, kullanıcıların bir engelleme eylemlerini seçmeli olarak geçersiz k olmasına izin verme
- [**Olay Bir**](#incident-reports) kural eşleşmesi olduğunda yöneticileri ve diğer önemli paydaşları bilgilendiren raporlar
- [**Kural değerlendirme**](#additional-options) önceliğini tanımlayan ve daha fazla kural ve ilke işlemeyi durduran Ek Seçenekler.

 İlke bir veya birden çok kural içerir. Kurallar, her ilkede en yüksek öncelikli kuralla başlayarak sırayla yürütülür.

### <a name="the-priority-by-which-rules-are-processed"></a>Kuralların işlenme önceliği

#### <a name="hosted-service-workloads"></a>Barındırılan hizmet iş yükleri

Exchange Online, SharePoint Online ve OneDrive İş gibi barındırılan hizmet iş yükleri için, her kurala oluşturulma sırasıyla bir öncelik atanır. Başka bir ifadeyle, ilk oluşturulan kuralın birinci önceliğe, ikinci oluşturulan kuralın ikinci önceliğe sahip olduğu, bu şekilde devam anlamına gelir. 
  
![Öncelik sırasına göre kurallar](../media/dlp-rules-in-priority-order.png)

İçerik kurallara göre değerlendirildikten sonra, kurallar öncelik sırasına göre işlenir. İçerik birden çok kuralla eşlerise, en kısıtlayıcı *eyleme sahip* olan ilk kural uygulanır. Örneğin, içerik aşağıdaki kuralların hepsiyle eş site olursa, bu en yüksek öncelikli, en kısıtlayıcı kural olduğundan *3* . Kural zorunlu kılındı:
  
- 1. Kural: Yalnızca kullanıcılara haber verenler
- 2. Kural: Kullanıcılara haber verir, erişimi kısıtlar ve kullanıcının geçersiz kılmalarına izin verir
- *3. Kural: Kullanıcılara haber verme, erişimi kısıtlama ve kullanıcının geçersiz kılmalarına izin verme*
- Kural 4: Erişimi kısıtlar

1, 2 ve 4 kuralları değerlendirilir, ancak uygulanmaz. Bu örnekte, tüm kurallarla ilgili eşleşmeler denetim günlüklerine kaydedilir ve DLP raporlarında gösterilir; ama yalnızca en kısıtlayıcı kural uygulanır.

Belirli bir koruma gereksinimini karşılamak için bir kural kullanabilir ve sonra belirli bir düzenlemeye uymak için gereken kuralların hepsi gibi, ortak koruma gereksinimlerini bir araya group etmek için bir DLP ilkesi kullanabilirsiniz.
  
Örneğin, Sağlık Sigortası Taşınabilirlik ve Sorumluluk Yasası'ne (HIPAA) tabi olan bilgilerin varlığını algılamanıza yardımcı olacak bir DLP ilkeye sahip olabilirsiniz. Bu DLP ilkesi, kuruluş dışından kişilerle paylaşılan bu hassas bilgileri içeren herhangi bir belgeyi (koşullar) bularak ve ardından belgeye erişimi engelleyerek ve bir bildirim (eylemler) göndererek HIPAA verilerini (ne) tüm SharePoint Online sitelerinde ve tüm OneDrive İş sitelerinde (nerede) korumaya yardımcı olabilir. Bu gereksinimler tek tek kurallar olarak saklanır ve yönetim ve raporlamayı basitleştirmek için DLP ilkesi olarak birlikte gruptur.
  
![Diyagram, DLP ilkesinde konumlar ve kurallar olduğunu gösterir](../media/c006860c-2d00-42cb-aaa4-5b5638d139f7.png)

#### <a name="for-endpoints"></a>Uç noktalar için

Uç noktalarda kuralların önceliği, oluşturulma sırasına göre de atanır. Başka bir ifadeyle, ilk oluşturulan kuralın birinci önceliğe, ikinci oluşturulan kuralın ikinci önceliğe sahip olduğu, bu şekilde devam anlamına gelir. 

Uç nokta üzerinde bir dosya birden çok DLP ilkeleriyle eşleildiğinde, içerikte zorunlu kılınan ilk kural kısıtlamalarla etkinleştirilir. Örneğin, içerik aşağıdaki kuralların hepsiyle eş site olursa, bu kısıtlamayla yapılandırılan en yüksek öncelikli kural olduğundan Kural *2 zorunlu kılındı*.
  
- 1. Kural: Yalnızca kullanıcılara haber verenler
- *2. Kural: Kullanıcılara haber verir, erişimi kısıtlar ve kullanıcının geçersiz kılmalarına izin verir*
- 3. Kural: Kullanıcılara haber verme, erişimi kısıtlama ve kullanıcının geçersiz kılmalarına izin verme
- Kural 4: Erişimi kısıtlar

1, 3 ve 4 kuralları değerlendirilir, ancak uygulanmaz. Bu örnekte, tüm kurallarla ilgili eşleşmeler denetim günlüklerine kaydedilir ve DLP raporlarında gösterilir; ama yalnızca kısıtlamalı ilk kural uygulanır.

Uç noktalara uygulanan kurallar için, uygulanırken istediğiniz kısıtlamaların uygulandığından emin olmak için kural önceliğini yeniden sırala özelliğiden faydalanın.

### <a name="conditions"></a>Koşullar

Koşullar kapsayıcıdır ve kuralın neleri baktıracaklarını ve bu öğelerin hangi bağlamda kullanıla hazır olduğunu tanımladığınız yerdir. Kuralın &#8212; bir öğe bu şekilde göründüğünü ve böyle bir öğenin &#8212; bir eşleşme  olduğunu ve ilkede kalan eylemlerin bu öğeye alınması gerektiğini söyler. Farklı risk düzeylerine farklı eylemler atamak için koşullar kullanabilirsiniz. Örneğin, şirket içinde paylaşılan hassas içerik daha düşük bir risk olabilir ve kuruluş dışındaki kişilerle paylaşılan hassas içerikten daha az eylem gerektirir.

> [!NOTE]
> Ana kuruluşun Active Directory'sinde veya başka bir kiracıda konuk hesabı olmayan Azure Active Directory, kuruluş içindeki kişiler olarak kabul edilir. 

#### <a name="content-contains"></a>İçerik içeriği

 Tüm konumlar İçerik içerir **koşullarını** destekler. Bu (mantıksal VEYA) işleçlerden herhangi **birini veya Tüm** **bu (mantıksal** VE) işleçleri kullanarak, her içerik türünün birden çok örneğini seçmeye ve koşulları daha da daraltabilirsiniz:

- [hassas bilgi türleri](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [duyarlılık etiketleri](sensitivity-labels.md)
- [bekletme etiketleri](retention.md#using-a-retention-label-as-a-condition-in-a-dlp-policy)

İlkeyi [uygulamak istediğiniz](#location-support-for-how-content-can-be-defined) konumlara bağlı olarak bu ilkeyi seçin. 

Kural yalnızca, seçki olarak tüm duyarlılık **etiketlerinin ve bekletme etiketlerinin** **varlığı için** bilgi edinecek. 

SITS'ler, gerektiğinde [**değiştirebilecekleri**](https://www.microsoft.com/videoplayer/embed/RE4Hx60) önceden tanımlanmış bir güven düzeyine sahip olur. Daha fazla bilgi için bkz [. Güven düzeyleri hakkında daha fazla bilgi](sensitive-information-type-learn-about.md#more-on-confidence-levels). 

> [!IMPORTANT]
> SITS'lerin en fazla benzersiz örnek sayısı parametresini tanımlamanın iki farklı yolu vardır. Daha fazla bilgi edinmek için bkz [. SIT için örnek sayısı desteklenen değerler](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

#### <a name="condition-context"></a>Koşul bağlamı

Kullanılabilir bağlam seçenekleri, seçtiğiniz konuma bağlı olarak değişir. Birden çok konum seçersiniz, yalnızca konumların ortak koşulları kullanılabilir.

##### <a name="conditions-exchange-supports"></a>Koşullar Exchange destekler

- İçerik içeriği
- İçerik paylaşılan yer Microsoft 365
- İçerik alındı
- Gönderen IP adresi:
- Gönderen ilke ipucu geçersiz k oldu mu
- Gönderen:
- Gönderen etki alanı:
- Gönderen adresi sözcükler içeriyor
- Gönderen adresi desenler içerir
- Sender AD Özniteliği sözcük veya tümcecik içeriyor
- Sender AD Özniteliği desenlere eşler
- Gönderen üyesidir
- E-posta eklerinin içeriği taranamadı
- Herhangi bir e-posta ekin içeriğinin tarama işlemi tamamlanmadı
- Ek parola korumalıdır
- Dosya uzantısı
- Alıcı şu üyenin üyesidir:
- Alıcı etki alanı:
- Alıcı
- Alıcı adresi sözcükler içeriyor
- Alıcı adresi desenlere eşler
- Alıcı AD Özniteliği sözcük veya tümcecik içeriyor
- Alıcı AD Özniteliği desenlere eşler
- Belge adı sözcük veya tümcecik içeriyor
- Belge adı desenlere eşler
- Belge özelliği şu şekildedir:
- Belge boyutu eşit veya büyüktür
- Belge içeriği sözcükler veya tümcecikler içerir
- Belge içeriği desenlere eşler
- Konu sözcük veya tümcecik içeriyor
- Konu eşleşmeleri desenlerini
- Konu veya Gövde sözcük veya tümcecik içeriyor
- Konu veya gövde desenlerini eşler
- İçerik karakter kümesi sözcükler içeriyor
- Üst bilgi sözcük veya tümcecik içeriyor
- Üst bilgi eşleşme düzenleri
- İleti boyutu eşittir veya büyüktür
- İleti türü:
- İletinin önem öneme sahip olduğu

##### <a name="conditions-sharepoint-supports"></a>Koşullar SharePoint destekler
 
- İçerik içeriği
- İçerik paylaşılan yer Microsoft 365
- Dosya uzantısı
- Belge özelliği şu şekildedir:

##### <a name="conditions-onedrive-accounts-supports"></a>Hesap OneDrive desteklemektedir

- İçerik içeriği
- İçerik paylaşılan yer Microsoft 365
- Dosya uzantısı
- Belge özelliği şu şekildedir:

##### <a name="conditions-teams-chat-and-channel-messages-supports"></a>Sohbet Teams kanal iletilerinin desteklediği koşullar

- İçerik içeriği
- İçerik paylaşılan yer Microsoft 365
- Gönderen: (Önizleme)
- Gönderen etki alanı : (Önizleme)
- Alıcı etki alanı : (Önizleme)
- Alıcı: (Önizleme)

##### <a name="conditions-devices-supports"></a>Cihazlar'ın desteklediği koşullar

- İçerik içeriği
- Bkz. [İzlemek ve üzerinde işlem gerçekleştirebilirsiniz uç nokta etkinlikleri](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on)

##### <a name="conditions-microsoft-defender-for-cloud-apps-supports"></a>Bulut Uygulamaları için Microsoft Defender'ın desteklediği koşullar

- İçerik içeriği
- İçerik paylaşılan yer Microsoft 365

##### <a name="conditions-on-premises-repositories-supports"></a>Şirket içi depolar koşulları desteklemektedir

- İçerik içeriği
- Dosya uzantısı
- Belge özelliği şu şekildedir:

##### <a name="conditions-powerbi-supports"></a>PowerBI'nin desteklediği koşullar

- İçerik içeriği

#### <a name="condition-groups"></a>Koşul grupları

Bazen tek bir SIT tarafından tanımlanan ABD Sosyal Güvenlik Numarası içeren tüm içerik gibi yalnızca bir şeyi tanımlamak için bir kurala ihtiyacınız olabilir. Ancak, tanımlamaya çalıştığı öğe türlerinin daha karmaşık olduğu ve dolayısıyla tanımlanması daha zor olan birçok senaryoda, koşulları tanımlarken daha fazla esneklik gereklidir.

Örneğin, ABD Sağlık Sigortası Yasası'nın (HIPAA) içeriğini tanımlamak için:
  
- ABD Sosyal Güvenlik Numarası veya A.S. Yaptırım Daire (DEA) Numarası gibi belirli türlerde hassas bilgileri içeren içerik.
    
    VE
    
- Hastanın bakımı veya tıbbi hizmetlerin açıklamaları hakkında iletişimler gibi, tanımlaması daha zor içerikler sağlanır. Bu içeriğin belirlenmesi, Uluslararası Teklif Sınıflandırması (ICD-9-CM veya ICD-10-CM) gibi büyük anahtar sözcük listelerinden eşleşen anahtar sözcükler gerektirir.
    
Bu tür verileri, koşulları gruplama ve gruplar arasında mantıksal işleçler (VE, VEYA) kullanarak tanımlayabilirsiniz.
    
**A.B.D. Sağlık Sigortası Yasası (HIPPA)** için koşullar aşağıdaki gibi grup gruplandı:

![HIPPA ilke koşulları](../media/dlp-rules-condition-groups-booleans.png)

İlk grup tanıyı tanı alan SITS'ler ve ikinci grup tanıyı tanı alan SITS'leri içerir.

### <a name="exceptions"></a>Özel Durumlar

Kurallarda, özel durumlar, bir öğeyi ilkenin dışında tutmak için kullanılan koşulları tanımlar. Mantıksal olarak, kapsayıcı koşullar ve bağlamdan sonra değerlendirilen özel kullanım koşulları. Kurala, &#8212; gibi görünen ve bu şekilde kullanılan bir öğenin bir eşleşme olması  ve ilkenin diğer eylemlerinin  bu öğe üzerinde gerçek dışı olması gerektiği ***(... hariç***) açık &#8212; 

Örneğin HIPPA ilkesine uygun olarak, Aşağıdaki gibi Belçika sürücüleri lisans numarası içeren tüm öğeyi dışarıda tutmak için kuralı değiştirebiliriz:

![Dışlamaların olduğu HIPPA ilkesi](../media/dlp-rule-exceptions.png)

Konum tarafından desteklenen özel durumlar koşulları, tüm ekleme koşullarıyla aynıdır ve desteklenen her koşula "Tek fark" eklenmesidir. Kural yalnızca özel durumlar içeriyorsa, dışlama ölçütlerine uyan tüm e-postalara veya dosyalara uygulanır.

Tüm konumlar kapsayıcı koşulu destekleyenin:

- İçerik içeriği

bunun istisnası şu olabilir:

- **İçeriğin içeriği** hariç 

### <a name="actions"></a>Eylemler 

Kapsayıcı ***koşullar** _ ve özel durumlar filtreleri ile bunu yapan her öğe _**_, kurala uygulanan kuralda _**_ tanımlanmış tüm eylemlere sahip olacaktır. Eylemi desteklemek için gerekli seçenekleri yapılandırmalısiniz. Örneğin, _Exchange _ *Restrict erişimi* ile seçin veya Microsoft 365 konumlar* eylemini şifrelersanız, şu seçeneklerden birini seçmeniz gerekir:

- Kullanıcıların paylaşılan içerikler, SharePoint, OneDrive ve paylaşılan Teams engelleme
    - Herkesi engelle. Yalnızca içerik sahibi, son değiştirici ve site yöneticisi erişim iznine sahip olmaya devam eder
    - Yalnızca kuruluş dışından kişi engelin. Kurum içindeki kullanıcılar da erişime sahip olmaya devam edecektir.
- E-posta iletilerini şifrele (yalnızca e-posta iletileri Exchange)

Bir kuralda kullanılabilen eylemler, seçilmiş olan konumlara bağlıdır. İlkenin uygulanıyor olması için yalnızca bir konum seçerseniz, kullanılabilir eylemler aşağıda listelenmiştir.

> [!IMPORTANT]
> SharePoint Online ve OneDrive İş konumları için, hassas bilgiler algılandıktan hemen sonra, belgenin tüm dış kullanıcılar için paylaşılıyor olup olmadığına bakılmaksızın, iç kullanıcılar belgeye erişmeye devam eder.

#### <a name="exchange-location-actions"></a>Exchange eylemleri

- Belirli konumlarda erişimi kısıtlama veya Microsoft 365 şifreleme
- Üst bilgileri ayarlama
- Üst bilgi kaldır
- İletiyi belirli kullanıcılara yönlendirme
- Onay için iletiyi gönderenin yöneticisine iletme
- Onay için iletiyi belirli onaylayanlara iletme
- Alıcıyı Son kutusuna ekleme
- Bilgi kutusuna alıcı ekleme
- Gizli kutusuna alıcı ekleme
- Gönderenin yöneticisini alıcı olarak ekleme
- O365 İleti Şifrelemesi ve hak koruması kaldırıldı
- Ön e-posta Konusunu Hazırlama
- E-posta Konusunu Değiştirme
- HTML Yasal Uyarı ekleme

#### <a name="sharepoint-sites-location-actions"></a>SharePoint sitesi konum eylemlerini nasıl gerçekleştirebilirsiniz?

- Belirli konumlarda erişimi kısıtlama veya Microsoft 365 şifreleme

#### <a name="onedrive-account-location-actions"></a>OneDrive konumu eylemlerini geri seçin

- Belirli konumlarda erişimi kısıtlama veya Microsoft 365 şifreleme

#### <a name="teams-chat-and-channel-messages-actions"></a>Teams Sohbet ve Kanal İletileri eylemlerini geri gönderme

- Belirli konumlarda erişimi kısıtlama veya Microsoft 365 şifreleme

#### <a name="devices-actions"></a>Cihazlar eylemleri

- Mobil cihazlarda etkinlikleri denetleme Windows kısıtlama

> [!NOTE]
> Cihazlar seçeneği, Etkinliği **denetleme** , Etkinliği engelleme **veya etkinliği** geçersiz kılma ile **engelle** seçeneğini sunar.

Cihaz konumu birçok alt etkinleştirme (koşullar) ve eylem sağlar. Daha fazla bilgi edinmek için [bkz. İzlemek ve üzerinde işlem gerçekleştirebilirsiniz uç nokta etkinlikleri](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on). 

#### <a name="microsoft-defender-for-cloud-apps"></a>Bulut Uygulamaları için Microsoft Defender

- Belirli konumlarda erişimi kısıtlama veya Microsoft 365 şifreleme
- Üçüncü Taraf Uygulamalarını Kısıtla

#### <a name="on-premises-repositories"></a>Şirket içi depolar

- Erişimi kısıtlama veya şirket içi dosyaları kaldırma

#### <a name="powerbi-actions"></a>PowerBI eylemleri

- Kullanıcıları e-posta ve ilke ipuçlarıyla bilgilendirin
- Yöneticiye uyarı gönder

#### <a name="actions-available-when-you-combine-locations"></a>Konumları birleştirinca kullanılabilen eylemler

İlkenin Exchange için Geçerli Konum'Exchange başka bir konum seçmek için

- Belirli konumlarda erişimi kısıtlama veya Microsoft 365 şifreleme

ve

- Yer olmayan konumun tüm Exchange.

eylemleri kullanılabilir.

İlkenin uygulanmak Exchange veya daha fazla konum seçmek için

- Belirli konumlarda erişimi kısıtlama veya Microsoft 365 şifreleme

VE

- Posta olmayan konumlar için Exchange eylemleri 

eylemleri kullanılabilir.

Örneğin, Konum olarak Exchange Cihazlar'ı seçersiniz, şu eylemler kullanılabilir:

- Belirli konumlarda erişimi kısıtlama veya Microsoft 365 şifreleme
- Mobil cihazlarda etkinlikleri denetleme Windows kısıtlama

Cihazlar ve Bulut Uygulamaları için Microsoft Defender'ı seçerek şu eylemleri gerçekleştirebilirsiniz:

- Belirli konumlarda erişimi kısıtlama veya Microsoft 365 şifreleme
- Mobil cihazlarda etkinlikleri denetleme Windows kısıtlama
- Üçüncü Taraf Uygulamalarını Kısıtla

Bir eylemin etkili olup olmadığı, ilkenin modunu nasıl yapılandırmış olduğunu bağlıdır. İlk önce Sına seçeneğini seçerek ilke ipucuyla veya bu ipucu göstermeden test modunda **çalıştırmayı seçebilirsiniz** . İlkeyi oluşturduktan hemen bir saat sonra çalıştırmayı tercih ediyorsanız, hemen aç seçeneğini kullanarak  ilkeyi kaydetmeyi ve daha sonra kapatma seçeneğini seçerek ilkeyi kaydederek yeniden **dönebilirsiniz**. 


<!-- This section needs to explain that the actions available depend on the locations selected AND that the observed behavior of a policy is produced through an interaction of the configured actions AND the configured status (off, test, apply) of a policy. It will detail the purpose of each of the available actions and the location/desired outcome interaction and provide examples eg. how to use the Restrict Third Party apps in the context of a policy that is applied to endpoints so that users can't use a upload content to a third party site or the interaction of on-premises scanner with restrict access or remove on-premises files.  Also what happens when I select multiple locations? provide abundant examples for most common scenarios-->


### <a name="user-notifications-and-policy-tips"></a>Kullanıcı bildirimleri ve ilke ipuçları

<!--This section introduces the business need for user notifications, what they are, their benefit, how to use them, how to customize them, and links out to 

- https://docs.microsoft.com/en-us/microsoft-365/compliance/use-notifications-and-policy-tips?view=o365-worldwide
- https://docs.microsoft.com/en-us/microsoft-365/compliance/dlp-policy-tips-reference?view=o365-worldwide

for where they are used/expected behavior-->

<!--You can use notifications and overrides to educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification.-->

Kullanıcı bir kuralın koşullarına ve özel durumlarına uygun bağlamda hassas bir öğe üzerinde eylem girişiminde bulunsa, kullanıcı bildirimi e-postaları ve bağlam ilkesi ipucu açılan menüleri aracılığıyla bu konuda bilgi edinebilirsiniz. Bu bildirimler, farkındalık artıran ve kişilerin kurum dLP ilkeleri hakkında eğitilmesine yardımcı olduğundan yararlı olur.

Örneğin, OneDrive İş sitesinde, Excel bilgileri (PII) içeren ve bir konukla paylaşılan çalışma kitabı gibi içerikler.

![İleti çubuğu, posta çubuğunda ilke ipucu Excel 2016](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

> [!NOTE]
> Bildirim e-postaları korumasız gönderilir.

Ayrıca, kişilerin geçerli bir ticari ihtiyaçları varsa [](#user-overrides)veya ilke hatalı pozitif bir sonuç algı içeriyorsa engellemelerini engellemek üzere ilkeyi geçersiz kılma seçeneği de veebilirsiniz.

Kullanıcı bildirimleri ve ilke ipuçları yapılandırma seçenekleri, seçtiğiniz izleme konumlara bağlı olarak değişir. Seçtiysanız:

- Exchange
- SharePoint
- OneDrive
- Teams Sohbet ve Kanal
- Bulut Uygulamaları için Defender


Çeşitli Microsoft uygulamaları için kullanıcı bildirimlerini etkinleştirebilirsiniz/devre dışı abilirsiniz, bkz. [Veri Kaybı Önleme ilke ipuçları başvurusu](dlp-policy-tips-reference.md#data-loss-prevention-policy-tips-reference)

- Kullanıcıları Office 365 **bir ilke ipucuyla bilgilendirin Office 365** etkinleştirebilirsiniz..
    - içeriği gönderen, paylaşan veya son değiştiren kullanıcıya gönderilen e-posta bildirimleri VEYA
    - belirli kullanıcıları bilgilendirme

ve e-posta metnini, konuyu ve ilke ipucu metnini özelleştirin.

![Exchange, SharePoint, OneDrive Teams Sohbet ve Kanal ve Bulut Uygulamaları için Defender ile kullanılabilen kullanıcı bildirimi ve ilke ipucu yapılandırma seçenekleri](../media/dlp-user-notification-non-devices.png)

Yalnızca cihazlar'ı seçtiyseniz Exchange, SharePoint, OneDrive, Teams Sohbet, Kanal ve Bulut Uygulamaları için Defender ile Windows 10 cihazında görüntülenen bildirim başlığını ve içeriği özelleştirme seçenekleriyle aynı seçenekleri alırsınız.

![Cihazlar için kullanılabilen kullanıcı bildirimi ve ilke ipucu yapılandırma seçenekleri](../media/dlp-user-notification-devices.png)  

Bu parametreleri kullanarak metnin başlığını ve gövdesini özelleştirebilirsiniz. Gövde metni şunları destekler:

|Ortak ad  |Parametre  |Örnek
|---------|---------|---------|
|dosya adı     |%%FileName%% | Contoso belgesi 1 |
|işlem adı     |%%ProcessName%% | Word |
|ilke adı     |%%PolicyName%%| Contoso çok gizli |
|eylem | %%AppliedActions%% | Panodan başka bir uygulamaya belge içeriği yapıştırma |

**%%AppliedActions%%** bu değerleri ileti gövdesine alır:


|eylem ortak adı |%%AppliedActions%% parametresi yerine konan değer |
|---------|---------|
|kaldırılabilir depolama alanına kopyalama    |*çıkarılabilir depolama alanına yazma*         |
|ağ paylaşımına kopyala     |*ağ paylaşımına yazma*         |
|yazdırma     |*yazdırma*         |
|Panodan yapıştırma  |*panodan yapıştırma*         |
|bluetooth ile kopyalama   |*Aktarma yoluyla Bluetooth*         |
|izin verilmeyen bir uygulamayla aç     |*bu uygulamayla açma*         |
|uzak masaüstüne (RDP) kopyalama     |*uzak masaüstüne aktarma*         |
|izin verilmeyen web sitesine yükleme     |*bu siteye yükleme*         |
|izin verilmeyen bir tarayıcı kullanarak öğeye erişme     |*Bu tarayıcıyla açma*         |

Bu özelleştirilmiş metni kullanma

*%%AppliedActions%% %%ProcessName%% üzerinden %%FileName%% dosya adı kuruluş tarafından izin verilmez. %%PolicyName%% politikasını atlamak için "İzin Ver" öğesini tıklatın* 

bu metni özelleştirilmiş bildirimde üretir:

*panodan yapıştırma Dosya Adı: E-posta yoluyla Contoso WINWORD.EXE belge 1'e kuruluş tarafından izin verilmiyor. Contoso için çok gizli olan ilkeyi atlamak için 'İzin Ver' düğmesine tıklayın*
 

> [!NOTE]
> Kullanıcı bildirimleri ve ilke ipuçları Şirket içi konumda kullanılamaz

> [!NOTE]
> Yalnızca en yüksek önceliğe sahip ilke ipucu, en kısıtlayıcı kural gösterilir. Örneğin, içeriğe erişimi engelleyen bir kuraldan gelen ilke ipucu, doğrudan bildirim gönderen bir kuraldan gelen bir ilke ipucu üzerinde gösterilir. Bu, kişilerin ilke ipuçları basamaklarını görmelerini önler.

Kullanıcı bildirimi ve ilke ipucu yapılandırması ve kullanımı hakkında daha fazla bilgi edinmek ve bildirim ve ipucu metnini özelleştirme dahil, bkz. 
- [E-posta bildirimleri gönderin ve DLP ilkeleriyle ilgili ilke ipuçlarını gösterme](use-notifications-and-policy-tips.md#send-email-notifications-and-show-policy-tips-for-dlp-policies).
  
<!--The email can notify the person who sent, shared, or last modified the content and, for site content, the primary site collection administrator and document owner. In addition, you can add or remove whomever you choose from the email notification.
  
In addition to sending an email notification, a user notification displays a policy tip:
  
- In Outlook and Outlook on the web.
    
- For the document on a SharePoint Online or OneDrive for Business site.
    
- In Excel, PowerPoint, and Word, when the document is stored on a site included in a DLP policy.
    
The email notification and policy tip explain why content conflicts with a DLP policy. If you choose, the email notification and policy tip can allow users to override a rule by reporting a false positive or providing a business justification. This can help you educate users about your DLP policies and enforce them without preventing people from doing their work. Information about overrides and false positives is also logged for reporting (see below about the DLP reports) and included in the incident reports (next section), so that the compliance officer can regularly review this information.
  
Here's what a policy tip looks like in a OneDrive for Business account.
  
![Policy tip for a document in a OneDrive account](../media/f9834d35-94f0-4511-8555-0fe69855ce6d.png)

 To learn more about user notifications and policy tips in DLP policies, see [Use notifications and policy tips](use-notifications-and-policy-tips.md).

> [!NOTE]
> The default behavior of a DLP policy, when there is no alert configured, is not to alert or trigger. This applies only to default information types. For custom information types, the system will alert even if there is no action defined in the policy.
-->

### <a name="user-overrides"></a>Kullanıcı geçersiz kılar

Kullanıcı geçersiz kılmalarının amacı, kullanıcılara Exchange, SharePoint, OneDrive veya Teams'daki hassas öğeler üzerinde uzlaştırma, DLP ilkesi engelleme eylemlerini atlama yolu vermektir ve böylece çalışmalarını sürdürebilirsiniz. Kullanıcı geçersiz kılmaları yalnızca Office 365 hizmetlarında kullanıcıları ilke ipucuyla bilgilendir etkinleştirildiğinde etkindir; dolayısıyla kullanıcı geçersiz kılmaları Bildirimler ve İlke ipuçlarıyla birlikte çalışır. 

![DLP ilkesi için kullanıcı geçersiz kılma seçenekleri](../media/dlp-user-overrides.png)

> [!NOTE]
> Şirket içi depo konumu için kullanıcı geçersiz kılmaları kullanılamaz.

Normalde, kuruluş bir ilkeyi ilk kez etkinleştirirken kullanıcı geçersiz kılmaları yararlı olur. Herhangi bir geçersiz gerekçelendirmeden ve hatalı pozitif sonuçlardan elde ettiyseniz, geri bildirim ilkenin ayarını belirlemeye yardımcı olur. 

<!-- This section covers what they are and how to best use them in conjunction with Test/Turn it on right away and link out to where to find the business justification for the override (DLP reports?  https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide)  https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide#view-the-justification-submitted-by-a-user-for-an-override-->

- En kısıtlayıcı kuralda yer alan ilke ipuçları kişilerin kuralı geçersiz k olmasına izin vermiyorsa, bu kuralı geçersiz kılmak da içeriğin eş olduğu diğer tüm kuralları geçersiz kılar.
 
<!--![User notifications and user overrides sections of DLP rule editor](../media/37b560d4-6e4e-489e-9134-d4b9daf60296.png)-->
 
Kullanıcı geçersiz kılmaları hakkında daha fazla bilgi edinmek için bkz:

- [Kullanıcı tarafından geçersiz kılma için gönderilen gerekçeyi görüntüleme](view-the-dlp-reports.md#view-the-justification-submitted-by-a-user-for-an-override)

### <a name="incident-reports"></a>Olay raporları

<!--DLP interacts with other M365 information protection services, like IR. Link this to a process outline for triaging/managing/resolving DLP incidents


https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide
https://docs.microsoft.com/en-us/microsoft-365/compliance/dlp-configure-view-alerts-policies?view=o365-worldwide-->

Bir kuralla eşleşmesi durumunda, olayın ayrıntılarını uyumluluk görevlisinize (veya seçtiğiniz herhangi bir kişi) bir olay raporu gönderebilirsiniz. Raporda, eşleni öğe, kuralla eşleşmeye neden olan gerçek içerik ve içeriği son değiştiren kişinin adı hakkında bilgiler yer sağlar. E-posta iletileri için, rapor bir DLP ilkesiyle eşleşen özgün iletinin bir eki olarak da yer alır.

DLP, olay bilgilerini diğer Microsoft 365 Koruma Hizmetleri'ne ([Insider Risk yönetimi](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365) gibi) Microsoft 365. Olay bilgilerini Insider risk yönetimine almak için, Olay raporları için **önem düzeyini Yüksek** olarak **ayarlanız gerekir**.

<!--![Page for configuring incident reports](../media/31c6da0e-981c-415e-91bf-d94ca391a893.png)-->

Bir etkinlik gürültülü olabilir ya da belirli bir süre içinde eşleşme sayısına veya öğe hacmine bağlı olarak daha az uyarıya neden olan bir kuralla her eşleşmede uyarılar gönderebilirsiniz.

![Bir kural her eşleşmede uyarı gönderme veya zaman içinde daha az rapora toplama](../media/dlp-incident-reports-aggregation.png)

DLP, e-postaları Çevrimiçi olarak SharePoint öğeleri OneDrive İş tarar. SharePoint Online ve OneDrive İş'de DLP, yeni öğelerin yanı sıra var olan öğeleri de tarar ve eşleşme bulunan her zaman bir olay raporu üretir. Diğer Exchange Online, DLP yalnızca yeni e-posta iletilerini tarar ve bir ilke eşleşmesi varsa rapor üretir. DLP ***, bir posta*** kutusunda veya arşivde depolanan daha önce var olan e-posta öğelerini taramaz veya eşleşmez.

### <a name="additional-options"></a>Ek seçenekler

Bir ilkede birden çok kuralız varsa, düzenlemekte olan kuralla bir eşleşme varsa diğer kural işlemeyi kontrol etmek ve kuralın değerlendirilme önceliğini ayarlama ek seçeneklerini kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Veri kaybı önleme (DLP) planı](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md#create-a-dlp-policy-from-a-template)
- [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
