---
title: Veri Kaybı Önleme ilkesi başvurusu
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
ms.openlocfilehash: b62289cfe4d18b4c6e2e79bb9a308f8b88978451
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66015802"
---
# <a name="data-loss-prevention-policy-reference"></a>Veri Kaybı Önleme ilkesi başvurusu

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview Veri Kaybı Önleme (DLP) ilkelerinin yapılandırılması gereken birçok bileşen vardır. Etkili bir ilke oluşturmak için, her bileşenin amacını ve yapılandırmasının ilkenin davranışını nasıl değiştirdiğini anlamanız gerekir. Bu makale, DLP ilkesinin ayrıntılı anatomisini sağlar.

## <a name="policy-templates"></a>İlke şablonları 

DLP ilkesi şablonları dört kategoriye önceden sıralanır:

- **Finansal** bilgi türlerini algılayıp koruyabilenler.
- **Tıbbi ve sağlık** bilgilerini algılayıp koruyabilen bilgiler.
- **Gizlilik** bilgileri türlerini algılayıp koruyabilenler.
- Diğer ilkelerden biri kuruluşunuzun ihtiyaçlarını karşılamıyorsa kendi ilkenizi oluşturmak için kullanabileceğiniz **özel** bir şablon.

Bu tabloda, tüm ilke şablonları ve bunların kapsadıkları hassas bilgi türleri (SIT) listelenir. 

güncelleştirme: 23.06.2021

|Kategori| Şablon | OTURUP |
|---------|---------|---------|
|Finansal| Avustralya Finansal Verileri| - [SWIFT kodu](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Avustralya vergi dosyası numarası](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Avustralya banka hesap numarası](sensitive-information-type-entity-definitions.md#australia-bank-account-number) </br> - [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansal| Kanada Finansal verileri |- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Kanada banka hesap numarası](sensitive-information-type-entity-definitions.md#canada-bank-account-number)|
|Finansal| Fransa Finansal verileri |- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [AB banka kartı numarası](sensitive-information-type-entity-definitions.md#eu-debit-card-number)|
|Finansal| Almanya Finansal Verileri |- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [AB banka kartı numarası](sensitive-information-type-entity-definitions.md#eu-debit-card-number)|
|Finansal| İsrail Finansal Verileri |- [İsrail banka hesap numarası](sensitive-information-type-entity-definitions.md#israel-bank-account-number) </br> - [SWIFT kodu](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansal| Japonya Finansal Verileri |- [Japonya banka hesap numarası](sensitive-information-type-entity-definitions.md#japan-bank-account-number) </br> - [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansal| PCI Veri Güvenliği Standardı (PCI DSS)|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansal| Suudi Arabistan Siber Suçlarla Mücadele Yasası|- [SWIFT kodu](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Uluslararası bankacılık hesap numarası (IBAN)](sensitive-information-type-entity-definitions.md#international-banking-account-number-iban) |
|Finansal| Suudi Arabistan Finansal Verileri |- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [SWIFT kodu](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Uluslararası bankacılık hesap numarası (IBAN)](sensitive-information-type-entity-definitions.md#international-banking-account-number-iban)|
|Finansal| Birleşik Krallık Finansal Verileri|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [AB banka kartı numarası](sensitive-information-type-entity-definitions.md#eu-debit-card-number) </br> - [SWIFT kodu](sensitive-information-type-entity-definitions.md#swift-code)|
|Finansal| ABD Finansal Verileri|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [ABD banka hesap numarası](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [ABA Yönlendirme Numarası](sensitive-information-type-entity-definitions.md#aba-routing-number)|
|Finansal| ABD Federal Ticaret Komisyonu (FTC) Tüketici Kuralları|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [ABD banka hesap numarası](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [ABA Yönlendirme Numarası](sensitive-information-type-entity-definitions.md#aba-routing-number)|
|Finansal| U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [ABD banka hesap numarası](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [ABD/Birleşik Krallık pasaport numarası](sensitive-information-type-entity-definitions.md#usuk-passport-number) </br> -[ABD ehliyet numarası](sensitive-information-type-entity-definitions.md#us-drivers-license-number)</br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [ABD Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Finansal| ABD Gramm-Leach-Bliley Yasası (GLBA)|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [ABD banka hesap numarası](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|Tıbbi ve sağlık| Avustralya Sağlık Kayıtları Yasası (HRIP Yasası) Geliştirildi |- [Avustralya vergi dosyası numarası](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Avustralya tıbbi hesap numarası](sensitive-information-type-entity-definitions.md#australia-medical-account-number) </br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [Tüm Tıbbi Hüküm ve Koşullar](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [Avustralya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#australia-physical-addresses)|
|Tıbbi ve sağlık| Avustralya Sağlık Kayıtları Yasası (HRIP Yasası)|- [Avustralya vergi dosyası numarası](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Avustralya tıbbi hesap numarası](sensitive-information-type-entity-definitions.md#australia-medical-account-number)|
|Tıbbi ve sağlık| Kanada Sağlık Bilgileri Yasası (HIA) |- [Kanada pasaport numarası](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Kanada sosyal sigorta numarası](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Kanada sağlık hizmeti numarası](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Kanada Kişisel Sağlık Kimlik Numarası](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Tıbbi ve sağlık| Kanada Kişisel Sağlık Bilgileri Yasası (PHIA) Manitoba|- [Kanada sosyal sigorta numarası](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Kanada sağlık hizmeti numarası](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Kanada Kişisel Sağlık Kimlik Numarası](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Tıbbi ve sağlık| Kanada Kişisel Sağlık Yasası (PHIPA) Ontario |- [Kanada pasaport numarası](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Kanada sosyal sigorta numarası](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Kanada sağlık hizmeti numarası](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Kanada Kişisel Sağlık Kimlik Numarası](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Tıbbi ve sağlık| INGİLTERE. Tıbbi Raporlara Erişim Yasası|- [Birleşik Krallık ulusal sağlık hizmeti numarası](sensitive-information-type-entity-definitions.md#uk-national-health-service-number) </br> - [Birleşik Krallık ulusal sigorta numarası (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino)|
|Tıbbi ve sağlık| ABD Sağlık Sigortası Yasası (HIPAA) Geliştirildi|</br> - [Uluslararası hastalık sınıflandırması (ICD-9-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-9-cm) </br> - [Uluslararası hastalık sınıflandırması (ICD-10-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-10-cm) </br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [Tüm Tıbbi Hüküm ve Koşullar](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [ABD Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Tıbbi ve sağlık| ABD Sağlık Sigortası Yasası (HIPAA)| - [Uluslararası hastalık sınıflandırması (ICD-9-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-9-cm) </br> - [Uluslararası hastalık sınıflandırması (ICD-10-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-10-cm)|
|Gizlilik| Gelişmiş Avustralya Gizlilik Yasası|- [Avustralya ehliyet numarası](sensitive-information-type-entity-definitions.md#australia-drivers-license-number) </br> - [Avustralya pasaport numarası](sensitive-information-type-entity-definitions.md#australia-passport-number) </br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [Tüm Tıbbi Hüküm ve Koşullar](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [Avustralya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#australia-physical-addresses)|
|Gizlilik| Avustralya Gizlilik Yasası|- [Avustralya ehliyet numarası](sensitive-information-type-entity-definitions.md#australia-drivers-license-number) </br> - [Avustralya pasaport numarası](sensitive-information-type-entity-definitions.md#australia-passport-number)|
|Gizlilik| Avustralya Kişisel Bilgiler (PII) Verileri|- [Avustralya vergi dosyası numarası](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Avustralya ehliyet numarası](sensitive-information-type-entity-definitions.md#australia-drivers-license-number)|
|Gizlilik| Kanada Kişisel Bilgiler (PII) Verileri|- [Kanada ehliyet numarası](sensitive-information-type-entity-definitions.md#canada-drivers-license-number)</br> - [Kanada banka hesap numarası](sensitive-information-type-entity-definitions.md#canada-bank-account-number) </br> - [Kanada pasaport numarası](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Kanada sosyal sigorta numarası](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Kanada sağlık hizmeti numarası](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Kanada Kişisel Sağlık Kimlik Numarası](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Gizlilik| Kanada Kişisel Information Protection Yasası (PIPA)|- [Kanada pasaport numarası](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Kanada sosyal sigorta numarası](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Kanada sağlık hizmeti numarası](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Kanada Kişisel Sağlık Kimlik Numarası](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Gizlilik| Kanada Kişisel Information Protection Yasası (PIPEDA)|- [Kanada ehliyet numarası](sensitive-information-type-entity-definitions.md#canada-drivers-license-number) </br> - [Kanada banka hesap numarası](sensitive-information-type-entity-definitions.md#canada-bank-account-number) </br> - [Kanada pasaport numarası](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Kanada sosyal sigorta numarası](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Kanada sağlık hizmeti numarası](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Kanada Kişisel Sağlık Kimlik Numarası](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Gizlilik| Fransa Veri Koruma Yasası|- [Fransa ulusal kimlik kartı (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni) </br> - [Fransa sosyal güvenlik numarası (INSEE)](sensitive-information-type-entity-definitions.md#france-social-security-number-insee)|
|Gizlilik| Fransa Kişisel Bilgiler (PII) Verileri|- [Fransa sosyal güvenlik numarası (INSEE)](sensitive-information-type-entity-definitions.md#france-social-security-number-insee) </br> - [Fransa ehliyet numarası](sensitive-information-type-entity-definitions.md#france-drivers-license-number) </br> - [Fransa pasaport numarası](sensitive-information-type-entity-definitions.md#france-passport-number) </br> - [Fransa ulusal kimlik kartı (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni)|
|Gizlilik| Genel Veri Koruma Yönetmeliği (GDPR) Geliştirildi|- [Avusturya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#austria-physical-addresses) </br> - [Belçika Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#belgium-physical-addresses)</br> - [Bulgaristan Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#bulgaria-physical-addresses)</br> - [Hırvatistan Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#croatia-physical-addresses)</br> - [Kıbrıs Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#cyprus-physical-addresses)</br> - [Çek Cumhuriyeti Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#czech-republic-physical-addresses)</br> - [Danimarka Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#denmark-physical-addresses)</br> - [Estonya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#estonia-physical-addresses)</br> - [Finlandiya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#finland-physical-addresses)</br> - [Fransa Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#france-physical-addresses)</br> - [Almanya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#germany-physical-addresses)</br> - [Yunanistan Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#greece-physical-addresses)</br> - [Macaristan Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#hungary-physical-addresses)</br> - [İrlanda Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#ireland-physical-addresses)</br> - [İtalya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#italy-physical-addresses)</br> - [Letonya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#latvia-physical-addresses)</br> - [Litvanya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#lithuania-physical-addresses)</br> - [Lüksemburg Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#luxemburg-physical-addresses)</br> - [Malta Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#malta-physical-addresses)</br> - [Hollanda Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#netherlands-physical-addresses)</br> - [Polonya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#poland-physical-addresses)</br> - [Portekizce Fiziksel Adresler](sensitive-information-type-entity-definitions.md#portugal-physical-addresses)</br> - [Romanya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#romania-physical-addresses)</br> - [Slovakya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#slovakia-physical-addresses)</br> - [Slovenya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#slovenia-physical-addresses)</br> - [İspanya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#spain-physical-addresses)</br> - [İsveç Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#sweden-physical-addresses)</br> - [Avusturya Sosyal Güvenlik Numarası](sensitive-information-type-entity-definitions.md#austria-social-security-number)</br> - [Fransa Sosyal Güvenlik Numarası (INSEE)](sensitive-information-type-entity-definitions.md#france-social-security-number-insee)</br> - [Yunanistan Sosyal Güvenlik Numarası (AMKA)](sensitive-information-type-entity-definitions.md#greece-social-security-number-amka)</br> - [Macar Sosyal Güvenlik Numarası (TAJ)](sensitive-information-type-entity-definitions.md#hungary-social-security-number-taj)</br> - [İspanya Sosyal Güvenlik Numarası (SSN)](sensitive-information-type-entity-definitions.md#spain-social-security-number-ssn)</br> - [Avusturya Kimlik Kartı](sensitive-information-type-entity-definitions.md#austria-identity-card)</br> - [Kıbrıs Kimlik Kartı](sensitive-information-type-entity-definitions.md#cyprus-identity-card)</br> - [Almanya Kimlik Kartı Numarası](sensitive-information-type-entity-definitions.md#germany-identity-card-number)</br> - [Malta Kimlik Kartı Numarası](sensitive-information-type-entity-definitions.md#malta-identity-card-number)</br> - [Fransa Ulusal Kimlik Kartı (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni)</br> - [Yunanistan Ulusal Kimlik Kartı](sensitive-information-type-entity-definitions.md#greece-national-id-card)</br> - [Finlandiya Ulusal Kimliği](sensitive-information-type-entity-definitions.md#finland-national-id)</br> - [Polonya Ulusal Kimliği (PESEL)](sensitive-information-type-entity-definitions.md#poland-national-id-pesel)</br> - [İsveç Ulusal Kimliği](sensitive-information-type-entity-definitions.md#sweden-national-id)</br> - [Hırvatistan Kişisel Kimlik (OIB) Numarası](sensitive-information-type-entity-definitions.md#croatia-personal-identification-oib-number)</br> - [Çek Kişisel Kimlik Numarası](sensitive-information-type-entity-definitions.md#czech-personal-identity-number)</br> - [Danimarka Kişisel Kimlik Numarası](sensitive-information-type-entity-definitions.md#denmark-personal-identification-number)</br> - [Estonya Kişisel Kimlik Kodu](sensitive-information-type-entity-definitions.md#estonia-personal-identification-code)</br> - [Macaristan Kişisel Kimlik Numarası](sensitive-information-type-entity-definitions.md#hungary-personal-identification-number)</br> - [Luxemburg Ulusal Kimlik Numarası (Gerçek kişiler)](sensitive-information-type-entity-definitions.md#luxemburg-national-identification-number-natural-persons)</br> - [Luxemburg Ulusal Kimlik Numarası (Gerçek olmayan kişiler)](sensitive-information-type-entity-definitions.md#luxemburg-national-identification-number-non-natural-persons)</br> - [İtalya Mali Kodu](sensitive-information-type-entity-definitions.md#italy-fiscal-code)</br> - [Letonya Kişisel Kodu](sensitive-information-type-entity-definitions.md#latvia-personal-code)</br> - [Litvanya Kişisel Kodu](sensitive-information-type-entity-definitions.md#lithuania-personal-code)</br> - [Romanya Kişisel Sayısal Kodu (CNP)](sensitive-information-type-entity-definitions.md#romania-personal-numeric-code-cnp)</br> - [Hollanda VatandaşLık Hizmeti (BSN) Numarası](sensitive-information-type-entity-definitions.md#netherlands-citizens-service-bsn-number)</br> - [İrlanda Kişisel Kamu Hizmeti (PPS) Numarası](sensitive-information-type-entity-definitions.md#ireland-personal-public-service-pps-number)</br> - [Bulgaristan Tekdüzen Sivil Numarası](sensitive-information-type-entity-definitions.md#bulgaria-uniform-civil-number)</br> - [Belçika Ulusal Numarası](sensitive-information-type-entity-definitions.md#belgium-national-number)</br> - [İspanya DNI](sensitive-information-type-entity-definitions.md#spain-dni)</br> - [Slovenya Benzersiz Ana Vatandaş Numarası](sensitive-information-type-entity-definitions.md#slovenia-unique-master-citizen-number)</br> - [Slovakya Kişisel Numarası](sensitive-information-type-entity-definitions.md#slovakia-personal-number)</br> - [Portekiz Vatandaş Kart Numarası](sensitive-information-type-entity-definitions.md#portugal-citizen-card-number)</br> - [Malta Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#malta-tax-identification-number)</br> - [Avusturya Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#austria-tax-identification-number)</br> - [Kıbrıs Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#cyprus-tax-identification-number)</br> - [Fransa Vergi Kimlik Numarası (numéro SPI.)](sensitive-information-type-entity-definitions.md#france-tax-identification-number)</br> - [Almanya Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#germany-tax-identification-number)</br> - [Yunan Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#greece-tax-identification-number)</br> - [Macaristan Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#hungary-tax-identification-number)</br> - [Hollanda Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#netherlands-tax-identification-number)</br> - [Polonya Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#poland-tax-identification-number)</br> - [Portekiz Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#portugal-tax-identification-number)</br> - [Slovenya Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#slovenia-tax-identification-number)</br> - [İspanya Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#spain-tax-identification-number)</br> - [İsveç Vergi Kimlik Numarası](sensitive-information-type-entity-definitions.md#sweden-tax-identification-number)</br> - [Avusturya Sürücü Belgesi](sensitive-information-type-entity-definitions.md#austria-drivers-license-number)</br> - [Belçika Ehliyet Numarası](sensitive-information-type-entity-definitions.md#belgium-drivers-license-number)</br> - [Bulgaristan Ehliyet Numarası](sensitive-information-type-entity-definitions.md#bulgaria-drivers-license-number)</br> - [Hırvatistan Ehliyet Numarası](sensitive-information-type-entity-definitions.md#croatia-drivers-license-number)</br> - [Kıbrıs Ehliyet Numarası](sensitive-information-type-entity-definitions.md#cyprus-drivers-license-number)</br> - [Çek Ehliyet Numarası](sensitive-information-type-entity-definitions.md#czech-drivers-license-number)</br> - [Danimarka Ehliyet Numarası](sensitive-information-type-entity-definitions.md#denmark-drivers-license-number)</br> - [Estonya Sürücü Lisans Numarası](sensitive-information-type-entity-definitions.md#estonia-drivers-license-number)</br> - [Finlandiya Ehliyet Numarası](sensitive-information-type-entity-definitions.md#finland-drivers-license-number)</br> - [Fransa Ehliyet Numarası](sensitive-information-type-entity-definitions.md#france-drivers-license-number)</br> - [Alman Sürücü Belgesi Numarası](sensitive-information-type-entity-definitions.md#germany-drivers-license-number)</br> - [Yunanistan Ehliyet Numarası](sensitive-information-type-entity-definitions.md#greece-drivers-license-number)</br> - [Macaristan Ehliyet Numarası](sensitive-information-type-entity-definitions.md#hungary-drivers-license-number)</br> - [İrlanda Ehliyet Numarası](sensitive-information-type-entity-definitions.md#ireland-drivers-license-number)</br> - [İtalya Ehliyet Numarası](sensitive-information-type-entity-definitions.md#italy-drivers-license-number)</br> - [Letonya Ehliyet Numarası](sensitive-information-type-entity-definitions.md#latvia-drivers-license-number)</br> - [Litvanya Sürücü Belgesi Numarası](sensitive-information-type-entity-definitions.md#lithuania-drivers-license-number)</br> - [Luxemburg Ehliyet Numarası](sensitive-information-type-entity-definitions.md#luxemburg-drivers-license-number)</br> - [Malta Sürücü Belgesi Numarası](sensitive-information-type-entity-definitions.md#malta-drivers-license-number)</br> - [Hollanda Ehliyet Numarası](sensitive-information-type-entity-definitions.md#netherlands-drivers-license-number)</br> - [Polonya Sürücü Belgesi Numarası](sensitive-information-type-entity-definitions.md#poland-drivers-license-number)</br> - [Portekiz Sürücü Ehliyeti Numarası](sensitive-information-type-entity-definitions.md#portugal-drivers-license-number)</br> - [Romanya Ehliyet Numarası](sensitive-information-type-entity-definitions.md#romania-drivers-license-number)</br> - [Slovakya Sürücü Ehliyeti Numarası](sensitive-information-type-entity-definitions.md#slovakia-drivers-license-number)</br> - [Slovenya Ehliyet Numarası](sensitive-information-type-entity-definitions.md#slovenia-drivers-license-number)</br> - [İspanya Ehliyet Numarası](sensitive-information-type-entity-definitions.md#spain-drivers-license-number)</br> - [İsveç Ehliyet Numarası](sensitive-information-type-entity-definitions.md#sweden-drivers-license-number)</br> - [Avusturya Pasaport Numarası](sensitive-information-type-entity-definitions.md#austria-passport-number)</br> - [Belçika Pasaport Numarası](sensitive-information-type-entity-definitions.md#belgium-passport-number)</br> - [Bulgaristan Pasaport Numarası](sensitive-information-type-entity-definitions.md#bulgaria-passport-number)</br> - [Hırvatistan Pasaport Numarası](sensitive-information-type-entity-definitions.md#croatia-passport-number)</br> - [Kıbrıs Pasaport Numarası](sensitive-information-type-entity-definitions.md#cyprus-passport-number)</br> - [Çek Cumhuriyeti Pasaport Numarası](sensitive-information-type-entity-definitions.md#czech-passport-number)</br> - [Danimarka Pasaport Numarası](sensitive-information-type-entity-definitions.md#denmark-passport-number)</br> - [Estonya Pasaport Numarası](sensitive-information-type-entity-definitions.md#estonia-passport-number)</br> - [Finlandiya Pasaport Numarası](sensitive-information-type-entity-definitions.md#finland-passport-number)</br> - [Fransa Pasaport Numarası](sensitive-information-type-entity-definitions.md#france-passport-number)</br> - [Alman Pasaport Numarası](sensitive-information-type-entity-definitions.md#germany-passport-number)</br> - [Yunanistan Pasaport Numarası](sensitive-information-type-entity-definitions.md#greece-passport-number)</br> - [Macaristan Pasaport Numarası](sensitive-information-type-entity-definitions.md#hungary-passport-number)</br> - [İrlanda Pasaport Numarası](sensitive-information-type-entity-definitions.md#ireland-passport-number)</br> - [İtalya Pasaport Numarası](sensitive-information-type-entity-definitions.md#italy-passport-number)</br> - [Letonya Pasaport Numarası](sensitive-information-type-entity-definitions.md#latvia-passport-number)</br> - [Litvanya Pasaport Numarası](sensitive-information-type-entity-definitions.md#lithuania-passport-number)</br> - [Luxemburg Pasaport Numarası](sensitive-information-type-entity-definitions.md#luxemburg-passport-number)</br> - [Malta Pasaport Numarası](sensitive-information-type-entity-definitions.md#malta-passport-number)</br> - [Hollanda Pasaport Numarası](sensitive-information-type-entity-definitions.md#netherlands-passport-number)</br> - [Polonya Pasaportu](sensitive-information-type-entity-definitions.md#poland-passport-number)</br> - [Portekiz Pasaport Numarası](sensitive-information-type-entity-definitions.md#portugal-passport-number)</br> - [Romanya Pasaport Numarası](sensitive-information-type-entity-definitions.md#romania-passport-number)</br> - [Slovakya Pasaport Numarası](sensitive-information-type-entity-definitions.md#slovakia-passport-number)</br> - [Slovenya Pasaport Numarası](sensitive-information-type-entity-definitions.md#slovenia-passport-number)</br> - [İspanya Pasaport Numarası](sensitive-information-type-entity-definitions.md#spain-passport-number)</br> - [İsveç Pasaport Numarası](sensitive-information-type-entity-definitions.md#sweden-passport-number)</br> - [AB Banka Kartı Numarası](sensitive-information-type-entity-definitions.md#eu-debit-card-number)</br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names)|
|Gizlilik| Genel Veri Koruma Yönetmeliği (GDPR)|- [AB banka kartı numarası](sensitive-information-type-entity-definitions.md#eu-debit-card-number) </br> - [AB ehliyet numarası](sensitive-information-type-entity-definitions.md#eu-drivers-license-number) </br> - [AB ulusal kimlik numarası](sensitive-information-type-entity-definitions.md#eu-national-identification-number)</br> - [AB pasaport numarası](sensitive-information-type-entity-definitions.md#eu-passport-number) </br> - [AB sosyal güvenlik numarası veya eşdeğer kimlik](sensitive-information-type-entity-definitions.md#eu-social-security-number-or-equivalent-identification)</br> - [AB Vergi kimlik numarası](sensitive-information-type-entity-definitions.md#eu-tax-identification-number)|
|Gizlilik| Almanya Kişisel Bilgiler (PII) Verileri|- [Almanya ehliyet numarası](sensitive-information-type-entity-definitions.md#germany-drivers-license-number) </br> - [Almanya pasaport numarası](sensitive-information-type-entity-definitions.md#germany-passport-number)| 
|Gizlilik| İsrail Kişisel Bilgiler (PII) Verileri|- [İsrail ulusal kimlik numarası](sensitive-information-type-entity-definitions.md#israel-national-identification-number)| 
|Gizlilik| İsrail'de Gizliliğin Korunması|- [İsrail ulusal kimlik numarası](sensitive-information-type-entity-definitions.md#israel-national-identification-number)</br> - [İsrail banka hesap numarası](sensitive-information-type-entity-definitions.md#israel-bank-account-number)|
|Gizlilik| Japonya Kişisel Bilgiler (PII) Verileri geliştirildi|- [Japonya Sosyal Sigorta Numarası (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)</br> - [Japonya Numaram - Kişisel](sensitive-information-type-entity-definitions.md#japan-my-number---personal)</br> - [Japonya pasaport numarası](sensitive-information-type-entity-definitions.md#japan-passport-number)</br> - [Japonya ehliyet numarası](sensitive-information-type-entity-definitions.md#japan-drivers-license-number)</br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Japonya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#all-physical-addresses)|
|Gizlilik| Japonya Kişisel Bilgiler (PII) Verileri|- [Japonya'da ikamet eden kayıt numarası](sensitive-information-type-entity-definitions.md#japan-resident-registration-number) </br> - [Japonya Sosyal Sigorta Numarası (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)|
|Gizlilik| Japonya Kişisel Bilgilerin Korunması Geliştirildi|- [Japonya Sosyal Sigorta Numarası (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin) </br> - [Japonya Numaram - Kişisel](sensitive-information-type-entity-definitions.md#japan-my-number---personal)</br> - [Japonya pasaport numarası](sensitive-information-type-entity-definitions.md#japan-passport-number) </br> - [Japonya ehliyet numarası](sensitive-information-type-entity-definitions.md#japan-drivers-license-number)</br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Japonya Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#all-physical-addresses)|
|Gizlilik| Japonya Kişisel Bilgilerin Korunması|- [Japonya'da ikamet eden kayıt numarası](sensitive-information-type-entity-definitions.md#japan-resident-registration-number)</br> - [Japonya Sosyal Sigorta Numarası (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)|
|Gizlilik| Suudi Arabistan Kişisel Olarak Tanımlanabilir (PII) Verileri|- [Suudi Arabistan Ulusal Kimliği](sensitive-information-type-entity-definitions.md#saudi-arabia-national-id)|
|Gizlilik| INGİLTERE. Veri Koruma Yasası|- [Birleşik Krallık ulusal sigorta numarası (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [ABD/Birleşik Krallık pasaport numarası](sensitive-information-type-entity-definitions.md#usuk-passport-number) </br> - [SWIFT kodu](sensitive-information-type-entity-definitions.md#swift-code)|
|Gizlilik| INGİLTERE. Gizlilik ve Elektronik İletişim Düzenlemeleri|- [SWIFT kodu](sensitive-information-type-entity-definitions.md#swift-code)|
|Gizlilik| INGİLTERE. Kişisel Bilgiler (PII) Verileri|- [Birleşik Krallık ulusal sigorta numarası (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [ABD/Birleşik Krallık pasaport numarası](sensitive-information-type-entity-definitions.md#usuk-passport-number)|
|Gizlilik| INGİLTERE. Kişisel Bilgiler Çevrimiçi Uygulama Kodu (PIOCP)|- [Birleşik Krallık ulusal sigorta numarası (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [Birleşik Krallık ulusal sağlık hizmeti numarası](sensitive-information-type-entity-definitions.md#uk-national-health-service-number) </br> - [SWIFT kodu](sensitive-information-type-entity-definitions.md#swift-code)|
|Gizlilik| ABD Vatanseverlik Yasası Geliştirildi|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [ABD banka hesap numarası](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [ABD Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Gizlilik| ABD Vatanseverlik Yasası|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [ABD banka hesap numarası](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|Gizlilik| ABD Kişisel Bilgiler (PII) Verileri İyileştirilmiş|- [ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [ABD/Birleşik Krallık pasaport numarası](sensitive-information-type-entity-definitions.md#usuk-passport-number)</br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [ABD Fiziksel Adresleri](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Gizlilik| ABD Kişisel Bilgiler (PII) Verileri|- [ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [ABD/Birleşik Krallık pasaport numarası](sensitive-information-type-entity-definitions.md#usuk-passport-number)|
|Gizlilik| ABD Eyalet İhlali Bildirim Yasaları Geliştirildi|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [ABD banka hesap numarası](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> -[ABD ehliyet numarası](sensitive-information-type-entity-definitions.md#us-drivers-license-number) </br> - [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [Tüm Tam Adlar](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [ABD/Birleşik Krallık pasaport numarası](sensitive-information-type-entity-definitions.md#usuk-passport-number)</br> - [Tüm Tıbbi Hüküm ve Koşullar](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions)|
|Gizlilik| ABD Eyalet İhlali Bildirim Yasaları|- [Kredi kartı numarası](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [ABD banka hesap numarası](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> -[ABD ehliyet numarası](sensitive-information-type-entity-definitions.md#us-drivers-license-number) </br> - [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|Gizlilik| ABD Devlet Sosyal Güvenlik Numarası Gizlilik Yasaları|- [ABD sosyal güvenlik numarası (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|

## <a name="locations"></a>Konum

DLP ilkesi, birden çok konumda hassas bilgiler içeren öğeleri bulabilir ve koruyabilir.

|Konum  |Kapsamı dahil et/hariç tut  |Veri durumu  |Ek önkoşullar |
|---------|---------|---------|---------|
|Çevrimiçi e-posta Exchange |dağıtım grubu | hareket halindeki veriler| Hayır |
|Çevrimiçi siteleri SharePoint   |Site       | bekleyen veriler </br> kullanımdaki veriler | Hayır|
|hesapları OneDrive İş| hesap veya dağıtım grubu |bekleyen veriler </br> kullanımdaki veriler|Hayır|
|Sohbet ve kanal iletilerini Teams     | hesap veya dağıtım grubu |hareket halindeki veriler </br> kullanımdaki veriler |  Hayır       |
|Bulut Uygulamaları için Microsoft Defender   | bulut uygulaması örneği       |bekleyen veriler         | - [Microsoft dışı bulut uygulamaları için veri kaybı önleme ilkelerini kullanma](dlp-use-policies-non-microsoft-cloud-apps.md#use-data-loss-prevention-policies-for-non-microsoft-cloud-apps)        |
|Aygıtları  |kullanıcı veya grup         |bekleyen veriler </br>  kullanımdaki veriler </br>  hareket halindeki veriler         |- [Uç nokta veri kaybını önleme hakkında bilgi edinin](endpoint-dlp-learn-about.md) </br>- [Uç nokta veri kaybı önleme ile Kullanmaya başlayın](endpoint-dlp-getting-started.md) </br>- [Information Protection için cihaz ara sunucusu ve internet bağlantısı ayarlarını yapılandırma](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection) |
|Şirket içi depolar (dosya paylaşımları ve SharePoint)    |Depo         | bekleyen veriler         | - [Şirket içi veri kaybı önleme tarayıcısı hakkında bilgi edinin](dlp-on-premises-scanner-learn.md) </br> - [Şirket içi tarayıcıda veri kaybı önleme ile Kullanmaya başlayın](dlp-on-premises-scanner-get-started.md#get-started-with-the-data-loss-prevention-on-premises-scanner)         |
|PowerBI| Çalışma alanları | kullanımdaki veriler | Hayır|

Exchange belirli dağıtım gruplarını dahil etmeyi seçerseniz, DLP ilkesinin kapsamı yalnızca bu grubun üyeleriyle tamamlanır. Benzer şekilde bir dağıtım grubunu dışlamak, bu dağıtım grubunun tüm üyelerini ilke değerlendirmesinin dışında tutar. İlkenin kapsamını dağıtım listelerinin, dinamik dağıtım gruplarının ve güvenlik gruplarının üyelerine göre belirleyebilirsiniz. DLP ilkesi bu tür 50'den fazla ekleme ve dışlama içeremez.

Belirli SharePoint siteleri veya OneDrive hesaplarını dahil etmeyi veya hariç tutmayı seçerseniz, DLP ilkesi bu tür 100'den fazla ekleme ve dışlama içeremez. Bu sınır mevcut olsa da, kuruluş genelinde bir ilke veya tüm konumlar için geçerli olan bir ilke uygulayarak bu sınırı aşabilirsiniz.

Belirli OneDrive hesaplarını veya gruplarını dahil etmeyi veya hariç tutmayı seçerseniz, DLP ilkesi 100'den fazla kullanıcı hesabı veya dahil etme veya dışlama olarak 50 grup içeremez.

### <a name="location-support-for-how-content-can-be-defined"></a>İçeriğin nasıl tanımlanabileceği için konum desteği

DLP ilkeleri hassas öğeleri hassas bilgi türüyle (SIT) veya duyarlılık etiketiyle veya bekletme etiketiyle eşleştirerek algılar. Her konum, hassas içerik tanımlamanın farklı yöntemlerini destekler. İlkedeki konumları birleştirdiğinizde içeriğin nasıl tanımlandığı, tek bir konumla tanımlanma biçiminden farklı olabilir. 

> [!IMPORTANT]
> İlke için birden çok konum seçtiğinizde, içerik tanımı kategorisi için "hayır" değeri "evet" değerinden önceliklidir. Örneğin, yalnızca SharePoint siteleri seçtiğinizde, ilke hassas öğelerin bir veya daha fazla SIT tarafından, duyarlılık etiketiyle veya bekletme etiketiyle algılanmasını destekler. Ancak, SharePoint siteleri seçip sohbet ***ve*** kanal iletileri konumlarını Teams, ilke yalnızca SIT ile hassas öğelerin algılanması için destek sağlar.

|Konum| İçerik SIT ile tanımlanabilir| İçerik tanımlanabilir duyarlılık etiketi| İçerik bekletme etiketiyle tanımlanabilir|
|---------|---------|---------|---------|
|Çevrimiçi e-posta Exchange|Evet| Evet| Hayır|
|Çevrimiçi siteleri SharePoint| Evet| Evet| Evet|
|hesapları OneDrive İş| Evet| Evet| Evet|
|Sohbet ve Kanal iletilerini Teams | Evet| Hayır| Hayır|
|Aygıtları |Evet | Evet|  Hayır|
|Bulut Uygulamaları için Microsoft Defender | Evet| Evet| Evet|
|Şirket içi depolar| Evet| Evet| Hayır|
|PowerBI|Evet | Evet| Hayır|

> [!NOTE]
> DLP, e-postalardaki ve eklerdeki duyarlılık etiketlerini algılamayı destekler Bkz. [DLP ilkelerinde duyarlılık etiketlerini koşullar olarak kullanma](dlp-sensitivity-label-as-condition.md#use-sensitivity-labels-as-conditions-in-dlp-policies).

## <a name="rules"></a>Kurallar

<!--This section introduces the classifications of content that, when detected, can be protected. Link out to [Learn about sensitive information types]() and [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) as well as labels (cross referenced by supporting workload). It will touch on the purpose of multiple conditions, confidence levels (link out to [more on confidence levels](sensitive-information-type-learn-about.md#more-on-confidence-levels)) and confidence levels video. How to use the confidence level to change the behavior of a policy in conjunction with the instance count.  eg. if you want your policy to trigger when it encounters situation DEF, set your conditions like HIJ.-->
<!--
- What is a rule in the context of a Policy?
- when and why should I have more than one rule?
- The purpose of rule groups
- How do I tune the behavior of a Policy through the tuning of rules
- what's in a rule-->

Kurallar, DLP ilkelerinin iş mantığıdır. Şunlardan oluşur:

- Eşleştirildiğinde ilkeyi tetikleyen [**koşullar**](#conditions)
- [**Koşulların özel durumları**](#exceptions)
- [**İlke**](#actions) tetiklendiğinde yapılması gereken eylemler
- [**Kullanıcılarınızı**](#user-notifications-and-policy-tips) ilkeyi tetikleyen bir işlem yaparken bilgilendirmek ve kuruluşunuzun hassas bilgilerin nasıl ele alındığını öğrenmek için eğitmeye yardımcı olan kullanıcı bildirimleri
- Yönetici tarafından yapılandırıldığında [**Kullanıcı Geçersiz Kılmaları**](#user-overrides), kullanıcıların bir engelleme eylemini seçmeli olarak geçersiz kılmasına izin verir
- Kural eşleşmesi gerçekleştiğinde yöneticileri ve diğer önemli paydaşları bilgilendiren [**Olay Raporları**](#incident-reports)
- Kural değerlendirmesinin önceliğini tanımlayan ve daha fazla kural ve ilke işlemeyi durdurabilen [**Ek Seçenekler**](#additional-options).

 İlke bir veya daha fazla kural içerir. Kurallar, her ilkedeki en yüksek öncelikli kuraldan başlayarak sırayla yürütülür.

### <a name="the-priority-by-which-rules-are-processed"></a>Kuralların işlenme önceliği

#### <a name="hosted-service-workloads"></a>Barındırılan hizmet iş yükleri

Exchange Online, çevrimiçi ve OneDrive İş SharePoint gibi barındırılan hizmet iş yükleri için her kurala oluşturulduğu sırada bir öncelik atanır. Bu, ilk oluşturulan kuralın ilk önceliğe sahip olduğu, ikinci oluşturulan kuralın ikinci önceliğe sahip olduğu vb. anlamına gelir. 
  
![Öncelik sırasına göre kurallar](../media/dlp-rules-in-priority-order.png)

İçerik kurallara göre değerlendirildiğinde, kurallar öncelik sırasına göre işlenir. İçerik birden çok kuralla eşleşiyorsa, *en* kısıtlayıcı eyleme sahip olan ilk kural değerlendirilir. Örneğin, içerik aşağıdaki kuralların tümüyle eşleşiyorsa, kural *3* en yüksek öncelikli ve en kısıtlayıcı kural olduğundan zorlanır:
  
- Kural 1: Yalnızca kullanıcılara bildirir
- Kural 2: Kullanıcılara bildirir, erişimi kısıtlar ve kullanıcı geçersiz kılmalarına izin verir
- *Kural 3: Kullanıcılara bildirir, erişimi kısıtlar ve kullanıcı geçersiz kılmalarına izin vermez*
- Kural 4: Erişimi kısıtlar

Kurallar 1, 2 ve 4 değerlendirilir ancak uygulanmaz. Bu örnekte, tüm kuralların eşleşmeleri denetim günlüklerine kaydedilir ve yalnızca en kısıtlayıcı kural uygulansa bile DLP raporlarında gösterilir.

Belirli bir koruma gereksinimini karşılamak için bir kural kullanabilir ve ardından belirli bir düzenlemeye uymak için gereken tüm kurallar gibi ortak koruma gereksinimlerini gruplandırmak için bir DLP ilkesi kullanabilirsiniz.
  
Örneğin, Sağlık Sigortası Taşınabilirlik ve Sorumluluk Yasası'na (HIPAA) tabi bilgilerin varlığını algılamanıza yardımcı olan bir DLP ilkeniz olabilir. Bu DLP ilkesi, kuruluşunuzun dışındaki kişilerle paylaşılan bu hassas bilgileri içeren herhangi bir belgeyi (koşullar) bulup belgeye erişimi engelleyerek ve bir bildirim göndererek tüm SharePoint Çevrimiçi sitelerde ve tüm OneDrive İş sitelerinde (nerede) HIPAA verilerinin (ne olduğu) korunmasına yardımcı olabilir. Bu gereksinimler tek tek kurallar olarak depolanır ve yönetimi ve raporlamayı basitleştirmek için bir DLP ilkesi olarak gruplandırılır.
  
![Diyagram, DLP ilkesinin konumlar ve kurallar içerdiğini gösterir](../media/c006860c-2d00-42cb-aaa4-5b5638d139f7.png)

#### <a name="for-endpoints"></a>Uç noktalar için

Uç noktalardaki kuralların önceliği, oluşturulduğu sıraya göre de atanır. Bu, ilk oluşturulan kuralın ilk önceliğe sahip olduğu, ikinci oluşturulan kuralın ikinci önceliğe sahip olduğu vb. anlamına gelir. 

Uç nokta üzerindeki bir dosya birden çok DLP ilkesiyle eşleştiğinde, [uç nokta etkinliklerinde](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on) en kısıtlayıcı zorlamayla etkinleştirilen ilk kural, içeriğe uygulanan kuraldır. Örneğin, içerik aşağıdaki kuralların tümüyle eşleşiyorsa, en kısıtlayıcı olduğu için 2. kural diğer kurallardan önceliklidir.

- Kural 1: Yalnızca tüm etkinlikleri denetler 
- *Kural 2: tüm etkinlikleri engeller*
- Kural 3: Son kullanıcının geçersiz kılma seçeneğiyle tüm etkinlikleri engeller

Aşağıdaki örnekte Kural 1, en kısıtlayıcı olduğu için diğer eşleşen kurallardan önceliklidir.

- *Kural 1: etkinliği engeller ve kullanıcının geçersiz kılınmasına izin vermez*
- Kural 2: etkinliği engeller ve kullanıcı geçersiz kılmalarına izin verir
- Kural 3: Yalnızca tüm etkinlikleri denetler
- Kural 4: zorlama yok

Diğer tüm kurallar değerlendirilir ancak eylemleri uygulanmaz. Denetim günlükleri, dosyaya uygulanan en kısıtlayıcı kuralı gösterir. Eşleşen birden fazla kural varsa ve bunlar eşit derecede kısıtlayıcıysa, ilke ve kural önceliği dosyaya hangi kuralın uygulanacağını yönetir.

### <a name="conditions"></a>Koşul -ları

Koşullar kapsayıcıdır ve kuralın ne aramasını istediğinizi ve bu öğelerin kullanıldığı bağlamı tanımladığınız yerdir. Kurala &#8212;, *buna* benzeyen ve *bu şekilde kullanılan* bir öğe bulduğunuzda &#8212; bir eşleşme olduğunu ve ilkedeki eylemlerin geri kalanının bu öğe üzerinde gerçekleştirilmesi gerektiğini söyler. Farklı risk düzeylerine farklı eylemler atamak için koşulları kullanabilirsiniz. Örneğin, şirket içinde paylaşılan hassas içerik daha düşük riskli olabilir ve kuruluş dışındaki kişilerle paylaşılan hassas içerikten daha az eylem gerektirebilir.

> [!NOTE]
> Bir konak kuruluşun Active Directory'sinde veya Azure Active Directory kiracısında konuk olmayan hesapları olan kullanıcılar, kuruluşun içindeki kişiler olarak kabul edilir. 

#### <a name="content-contains"></a>İçerik içeriği

 Tüm konumlar **İçerik içerir** koşulunu destekler. Her içerik türünün birden çok örneğini seçebilir ve **bunlardan herhangi birini** (mantıksal VEYA) veya **Bunların tümü** (mantıksal AND) işleçlerini kullanarak koşulları daha da daraltabilirsiniz:

- [hassas bilgi türleri](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [duyarlılık etiketleri](sensitivity-labels.md)
- [bekletme etiketleri](retention.md#using-a-retention-label-as-a-condition-in-a-dlp-policy)

ilkeyi uygulamayı seçtiğiniz [konumlara](#location-support-for-how-content-can-be-defined) bağlı olarak. 

Kural yalnızca seçtiğiniz **duyarlılık etiketlerinin** ve **bekletme etiketlerinin** varlığını arar. 

SID'ler, gerekirse değiştirebileceğiniz önceden tanımlanmış bir [**güvenilirlik düzeyine**](https://www.microsoft.com/videoplayer/embed/RE4Hx60) sahiptir. Daha fazla bilgi için bkz. [Güvenilirlik düzeyleri hakkında daha fazla bilgi](sensitive-information-type-learn-about.md#more-on-confidence-levels). 

> [!IMPORTANT]
> SID'lerin, en fazla benzersiz örnek sayısı parametresini tanımlamanın iki farklı yolu vardır. Daha fazla bilgi edinmek için bkz [. SIT için örnek sayısı desteklenen değerler](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

#### <a name="condition-context"></a>Koşul bağlamı

Kullanılabilir bağlam seçenekleri, seçtiğiniz konuma bağlı olarak değişir. Birden çok konum seçerseniz, yalnızca konumların ortak olduğu koşullar kullanılabilir.

##### <a name="conditions-exchange-supports"></a>Exchange tarafından desteklenen koşullar

- İçerik içeriği
- İçerik Microsoft 365
- İçerik şu kaynaktan alınır:
- Gönderen IP adresi
- Gönderen ilke ipucunu geçersiz kıldı mı?
- Gönderen
- Gönderen etki alanı
- Gönderen adresi sözcükler içeriyor
- Gönderen adresi desenler içeriyor
- Sender AD Özniteliği sözcükler veya tümcecikler içeriyor
- Gönderen AD Özniteliği desenleri eşleştirir
- Gönderen,
- E-posta eklerinin içeriği taranamadı
- E-posta eklerinin içeriği taramayı tamamlamadı
- Ek parola korumalı
- Dosya uzantısı
- Alıcı,
- Alıcı etki alanı
- Alıcı
- Alıcı adresi sözcükler içeriyor
- Alıcı adresi desenleri eşleştirir
- Alıcı AD Özniteliği sözcükler veya tümcecikler içeriyor
- Alıcı AD Özniteliği desenleri eşleştirir
- Belge adı sözcükler veya tümcecikler içeriyor
- Belge adı desenler ile eşleşir
- Belge özelliği şudur:
- Belge boyutu eşittir veya büyüktür
- Belge içeriği sözcükler veya tümcecikler içeriyor
- Belge içeriği desenler ile eşleşir
- Konu sözcükleri veya tümcecikleri içerir
- Konu desenleri eşleştirir
- Konu veya Gövde sözcükleri veya tümcecikleri içerir
- Konu veya gövde desenleri eşleştirir
- İçerik karakter kümesi sözcükler içeriyor
- Üst bilgi sözcükler veya tümcecikler içeriyor
- Üst bilgi desenleri eşleştirir
- İleti boyutu eşittir veya büyüktür
- İleti türü:
- İletinin önemi

##### <a name="conditions-sharepoint-supports"></a>SharePoint destekleyen koşullar
 
- İçerik içeriği
- İçerik Microsoft 365
- Oluşturan belge
- Üyesi tarafından oluşturulan belge
- Belge adı sözcükler veya tümcecikler içeriyor
- Belge adı desenler ile eşleşir
- Belge boyutu üst
- Belge özelliği şudur:
- Dosya uzantısı

##### <a name="conditions-onedrive-accounts-supports"></a>Hesapların desteklediği koşullar OneDrive

- İçerik içeriği
- İçerik Microsoft 365
- Oluşturan belge
- Üyesi tarafından oluşturulan belge
- Belge adı sözcükler veya tümcecikler içeriyor
- Belge adı desenler ile eşleşir
- Belge boyutu üst
- Belge özelliği şudur:
- Dosya uzantısı

##### <a name="conditions-teams-chat-and-channel-messages-supports"></a>Sohbet ve kanal iletilerinin desteklediği koşullar Teams

- İçerik içeriği
- İçerik Microsoft 365
- Gönderen 
- Gönderen etki alanı 
- Alıcı etki alanı 
- Alıcı 

##### <a name="conditions-devices-supports"></a>Cihazların desteklediği koşullar

- İçerik içeriği
- Bkz [. üzerinde izleyebileceğiniz ve eylem gerçekleştirebileceğiniz uç nokta etkinlikleri](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on)

##### <a name="conditions-microsoft-defender-for-cloud-apps-supports"></a>Microsoft Defender for Cloud Apps desteklediği koşullar

- İçerik içeriği
- İçerik Microsoft 365

##### <a name="conditions-on-premises-repositories-supports"></a>Şirket içi depoların desteklediği koşullar

- İçerik içeriği
- Dosya uzantısı
- Belge özelliği şudur:

##### <a name="conditions-powerbi-supports"></a>PowerBI'ın desteklediği koşullar

- İçerik içeriği

#### <a name="condition-groups"></a>Koşul grupları

Bazen, tek bir SIT ile tanımlanan ABD Sosyal Güvenlik Numarası içeren tüm içerikler gibi yalnızca bir şeyi tanımlamak için bir kurala ihtiyacınız vardır. Ancak tanımlamaya çalıştığınız öğe türlerinin daha karmaşık olduğu ve bu nedenle tanımlanmasının daha zor olduğu birçok senaryoda, koşulları tanımlamada daha fazla esneklik gerekir.

Örneğin, ABD Sağlık Sigortası Yasası'na (HIPAA) tabi içeriği tanımlamak için şunları aramanız gerekir:
  
- ABD Sosyal Güvenlik Numarası veya Uyuşturucu Uygulama Kurumu (DEA) Numarası gibi belirli türde hassas bilgiler içeren içerik.
    
    VE
    
- Bir hastanın bakımıyla ilgili iletişim veya sağlanan tıbbi hizmetlerin açıklamaları gibi tanımlanması daha zor olan içerikler. Bu içeriğin tanımlanması için Uluslararası Hastalık Sınıflandırması (ICD-9-CM veya ICD-10-CM) gibi büyük anahtar sözcük listelerinden anahtar sözcüklerin eşleşmesi gerekir.
    
Bu tür verileri, koşulları gruplandırarak ve gruplar arasında mantıksal işleçler (AND, OR) kullanarak tanımlayabilirsiniz.
    
**ABD Sağlık Sigortası Yasası (HIPPA)** için koşullar şu şekilde gruplandırılır:

![HIPPA ilke koşulları](../media/dlp-rules-condition-groups-booleans.png)

İlk grup, ve tek tek tanımlayan SCT'leri, ikinci grup ise tıbbi tanıyı tanımlayan SID'leri içerir.

### <a name="exceptions"></a>Özel durum

Kurallarda özel durumlar, bir öğeyi ilkenin dışında tutmak için kullanılan koşulları tanımlar. Mantıksal olarak, kapsayıcı koşullar ve bağlamdan sonra değerlendirilen özel koşullar. Kurala &#8212; böyle *görünen ve bir* *eşleşme gibi kullanılan* bir öğe bulduğunuzda ve ilkedeki eylemlerin geri kalan kısmının bu öğe üzerinde gerçekleştirilip gerçekleştirilmediğini söyler&#8212; 

Örneğin, HIPPA ilkesine uygun olarak, belçika sürücü lisans numarası içeren herhangi bir öğeyi dışlamak için aşağıdaki gibi kuralı değiştirebiliriz:

![Dışlamalar içeren HIPPA ilkesi](../media/dlp-rule-exceptions.png)

Konum tarafından desteklenen özel durum koşulları, tüm ekleme koşullarıyla aynıdır ve tek fark desteklenen her koşula "Eğer hariç" öğesinin önceden eklenmesidir. Kural yalnızca özel durumlar içeriyorsa, dışlama ölçütlerini karşılamayan tüm e-postalara veya dosyalara uygulanır.

Tüm konumlar kapsayıcı koşulu desteklediği gibi:

- İçerik içeriği

özel durum şöyle olacaktır:

- **İçeriğin** 

### <a name="actions"></a>Eylem 

Kapsayıcı ***koşullar** _ ve özel _*_durum_*_ filtreleri aracılığıyla bunu yapan tüm öğelere, kuralda tanımlanan _*_tüm eylemler_*_ uygulanır. Eylemi desteklemek için gerekli seçenekleri yapılandırmanız gerekir. Örneğin, _ *Erişimi kısıtla veya Microsoft 365 konumlarındaki içeriği şifrele** eylemiyle Exchange seçerseniz şu seçenekler arasından seçim yapmanız gerekir:

- Kullanıcıların paylaşılan SharePoint, OneDrive ve Teams içeriğine erişmesini engelleme
    - Herkesi engelleyin. Yalnızca içerik sahibi, son değiştirici ve site yöneticisinin erişimi devam eder
    - Yalnızca kuruluşunuzun dışındaki kişileri engelleyin. Kuruluşunuz içindeki kullanıcıların erişimi devam eder.
- E-posta iletilerini şifreleme (yalnızca Exchange içeriği için geçerlidir)

Bir kuralda kullanılabilen eylemler, seçilen konumlara bağlıdır. İlkenin uygulanacağı tek bir konum seçerseniz, kullanılabilir eylemler aşağıda listelenmiştir.

> [!IMPORTANT]
> SharePoint Çevrimiçi ve OneDrive İş konumları için, belgenin tüm dış kullanıcılar için paylaşılıp paylaşılmadığına bakılmaksızın, hassas bilgiler algılandığında belgeler proaktif olarak engellenir ve iç kullanıcılar belgeye erişmeye devam eder.

#### <a name="exchange-location-actions"></a>konum eylemlerini Exchange

- erişimi kısıtlama veya Microsoft 365 konumlardaki içeriği şifreleme
- Üst bilgileri ayarlama
- Üst bilgiyi kaldır
- İletiyi belirli kullanıcılara yeniden yönlendirme
- Onay için iletiyi gönderenin yöneticisine iletme
- Onay için iletiyi belirli onaylayanlara iletme
- Alıcıyı Alıcı kutusuna ekleme
- Bilgi kutusuna alıcı ekleme
- Gizli kutusuna alıcı ekleme
- Gönderenin yöneticisini alıcı olarak ekleme
- O365 İleti Şifrelemesi ve hak koruması kaldırıldı
- Önceden Ekli E-posta Konusu
- E-posta Konusunu Değiştir
- HTML Bildirimi Ekle

#### <a name="sharepoint-sites-location-actions"></a>Sitelerin konum eylemlerini SharePoint

- erişimi kısıtlama veya Microsoft 365 konumlardaki içeriği şifreleme

#### <a name="onedrive-account-location-actions"></a>hesap konumu eylemlerini OneDrive

- erişimi kısıtlama veya Microsoft 365 konumlardaki içeriği şifreleme

#### <a name="teams-chat-and-channel-messages-actions"></a>Sohbet ve Kanal İletileri eylemlerini Teams

- erişimi kısıtlama veya Microsoft 365 konumlardaki içeriği şifreleme

#### <a name="devices-actions"></a>Cihaz eylemleri

- Windows cihazlarda etkinlikleri denetleme veya kısıtlama

Bu ayarları kullanmak için **, DLP ayarlarında** ve bunları kullanmak istediğiniz ilkede seçenekleri yapılandırmanız gerekir. Daha fazla bilgi için bkz [. Kısıtlı uygulamalar ve uygulama grupları](dlp-configure-endpoint-settings.md#restricted-apps-and-app-groups) .

Cihazların konumu birçok alt etkinlik (koşul) ve eylem sağlar. Daha fazla bilgi edinmek için bkz [. İzleyebileceğiniz ve üzerinde işlem yapabileceğiniz uç nokta etkinlikleri](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on).

**Windows cihazlardaki etkinlikleri denetle veya kısıtla'yı** seçtiğinizde, kullanıcı etkinliklerini hizmet etki alanına veya tarayıcıya göre kısıtlayabilir ve DLP'nin gerçekleştirdiği eylemlerin kapsamını belirleyebilirsiniz:

- Tüm uygulamalar
- Tanımladığınız kısıtlı uygulamaların listesine göre
- Tanımladığınız kısıtlı bir uygulama grubu (önizleme).

##### <a name="service-domain-and-browser-activities"></a>Hizmet etki alanı ve tarayıcı etkinlikleri

**İzin Ver/Engelle bulut hizmeti etki alanlarını** ve **İzin Verilmeyen tarayıcılar** listesini yapılandırdığınızda (bkz [. Hassas verilere yönelik tarayıcı ve etki alanı kısıtlamaları](dlp-configure-endpoint-settings.md#browser-and-domain-restrictions-to-sensitive-data)) ve kullanıcı korumalı bir dosyayı bulut hizmeti etki alanına yüklemeyi veya izin verilmeyen bir tarayıcıdan erişmeyi denediğinde, ilke eylemini , `Block with override`veya `Block` etkinliği olarak `Audit only`yapılandırabilirsiniz.

##### <a name="file-activities-for-all-apps"></a>Tüm uygulamalar için dosya etkinlikleri

**Tüm uygulamalar için Dosya etkinlikleri** seçeneğiyle **, Dosya etkinliklerini kısıtlama** veya **Belirli etkinliklere kısıtlama uygula'yı** seçersiniz. Belirli etkinliklere kısıtlama uygulamayı seçtiğinizde, burada seçtiğiniz eylemler bir kullanıcı DLP korumalı bir öğeye eriştiğinde uygulanır. Bu kullanıcı etkinliklerinde DLP'ye `Audit only`, `Block with override`( `Block` eylemleri) söyleyebilirsiniz:

- **Panoya kopyala**
- **USB çıkarılabilir sürücüye kopyalama** 
- **Ağ paylaşımına kopyalama**
- **Yazdırma**
- **İzin verilmeyen bir Bluetooth uygulamasını kullanarak kopyalama veya taşıma**
- **Uzak masaüstü hizmetleri**


##### <a name="restricted-app-activities"></a>Kısıtlı uygulama etkinlikleri  

Daha önce İzin verilmeyen uygulamalar olarak adlandırılan uygulama listesini, kısıtlama uygulamak istediğiniz Uç Nokta DLP ayarlarında tanımlarsınız. Kullanıcı, listedeki bir uygulamayı kullanarak DLP korumalı bir dosyaya erişmeye çalıştığında, , `Block with override`veya `Block` etkinliği yapabilirsiniz`Audit only`. **Kısıtlı uygulama etkinliklerinde** tanımlanan DLP eylemleri, uygulama kısıtlı uygulama grubunun üyesiyse geçersiz kılınabilir. Ardından kısıtlı uygulama grubunda tanımlanan eylemler uygulanır.

##### <a name="file-activities-for-apps-in-restricted-app-groups-preview"></a>Kısıtlı uygulama gruplarındaki uygulamalar için dosya etkinlikleri (önizleme)

Sınırlı uygulama gruplarınızı Uç Nokta DLP ayarlarında tanımlar ve ilkelerinize kısıtlanmış uygulama grupları eklersiniz. bir ilkeye kısıtlı bir uygulama grubu eklediğinizde, şu seçeneklerden birini belirlemeniz gerekir:

- Dosya etkinliğini kısıtlama
- Tüm etkinliklere kısıtlama uygulama
- Belirli bir etkinliğe kısıtlama uygulama

*Kısıtlamaları uygula* seçeneklerinden birini belirlediğinizde ve kullanıcı kısıtlanmış uygulama grubunda yer alan bir uygulamayı kullanarak DLP korumalı bir dosyaya erişmeye çalıştığında, , `Block with override`veya `Block` etkinliğine göre yapabilirsiniz`Audit only`. Burada tanımladığınız DLP eylemleri **, Uygulamanın tüm uygulamaları için Kısıtlı uygulama etkinlikleri** ve **Dosya etkinlikleri** bölümünde tanımlanan eylemleri geçersiz kılar.

Daha fazla bilgi için bkz [. Kısıtlı uygulamalar ve uygulama grupları](dlp-configure-endpoint-settings.md#restricted-apps-and-app-groups) . 

#### <a name="microsoft-defender-for-cloud-apps-actions"></a>eylemleri Microsoft Defender for Cloud Apps

- erişimi kısıtlama veya Microsoft 365 konumlardaki içeriği şifreleme
- Üçüncü Taraf Uygulamalarını Kısıtlama

#### <a name="on-premises-repositories-actions"></a>Şirket içi depo eylemleri

- Erişimi kısıtlama veya şirket içi dosyaları kaldırma

#### <a name="powerbi-actions"></a>PowerBI eylemleri

- Kullanıcılara e-posta ve ilke ipuçlarıyla bildirme
- Yöneticiye uyarı gönderme

#### <a name="actions-available-when-you-combine-locations"></a>Konumları birleştirdiğinizde kullanılabilen eylemler

İlkenin uygulanacağı Exchange ve başka bir tek konumu seçerseniz,

- erişimi kısıtlama veya Microsoft 365 konumlardaki içeriği şifreleme

ve

- Exchange olmayan konum için tüm eylemler

eylemler kullanılabilir olacaktır.

İlkenin uygulanacağı iki veya daha fazla Exchange olmayan konum seçerseniz,

- erişimi kısıtlama veya Microsoft 365 konumlardaki içeriği şifreleme

VE

- Exchange olmayan konumlar için tüm eylemler 

eylemler kullanılabilir olacaktır.

Örneğin, konum olarak Exchange ve Cihazlar'ı seçerseniz şu eylemler kullanılabilir:

- erişimi kısıtlama veya Microsoft 365 konumlardaki içeriği şifreleme
- Windows cihazlarda etkinlikleri denetleme veya kısıtlama

Cihazlar'ı ve Microsoft Defender for Cloud Apps seçerseniz şu eylemler kullanılabilir:

- erişimi kısıtlama veya Microsoft 365 konumlardaki içeriği şifreleme
- Windows cihazlarda etkinlikleri denetleme veya kısıtlama
- Üçüncü Taraf Uygulamalarını Kısıtlama

Bir eylemin etkili olup olmayacağı, ilke modunu nasıl yapılandırdığınıza bağlıdır. **İlk** olarak test et seçeneğini belirleyerek ilke ipucunu göstererek veya göstermeden ilkeyi test modunda çalıştırmayı seçebilirsiniz. İlkeyi oluşturulduktan bir saat sonra hemen **aç seçeneğini** belirleyerek çalıştırmayı seçebilir veya yalnızca kaydetmeyi ve daha sonra geri dönmek için **Kapalı tut** seçeneğini belirleyebilirsiniz. 


<!-- This section needs to explain that the actions available depend on the locations selected AND that the observed behavior of a policy is produced through an interaction of the configured actions AND the configured status (off, test, apply) of a policy. It will detail the purpose of each of the available actions and the location/desired outcome interaction and provide examples eg. how to use the Restrict Third Party apps in the context of a policy that is applied to endpoints so that users can't use a upload content to a third party site or the interaction of on-premises scanner with restrict access or remove on-premises files.  Also what happens when I select multiple locations? provide abundant examples for most common scenarios-->


### <a name="user-notifications-and-policy-tips"></a>Kullanıcı bildirimleri ve ilke ipuçları

<!--This section introduces the business need for user notifications, what they are, their benefit, how to use them, how to customize them, and links out to 

- https://docs.microsoft.com/en-us/microsoft-365/compliance/use-notifications-and-policy-tips?view=o365-worldwide
- https://docs.microsoft.com/en-us/microsoft-365/compliance/dlp-policy-tips-reference?view=o365-worldwide

for where they are used/expected behavior-->

<!--You can use notifications and overrides to educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification.-->

Kullanıcı, bir kuralın koşullarını ve özel durumlarını karşılayan bir bağlamda hassas bir öğe üzerinde eylem gerçekleştirmeye çalıştığında, kullanıcı bildirim e-postaları ve bağlam ilkesi ipucu açılır pencereleri aracılığıyla bu öğe hakkında bilgi edinebilirsiniz. Bu bildirimler, farkındalığı artırdığından ve kişilerin kuruluşunuzun DLP ilkeleri hakkında eğitilmesine yardımcı olduğundan yararlıdır.

Örneğin, kişisel bilgileri (PII) içeren ve bir konukla paylaşılan OneDrive İş bir sitedeki Excel çalışma kitabı gibi içerikler.

![İleti çubuğu, Excel 2016 ilke ipucunu gösterir](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

> [!IMPORTANT]
> - Bildirim e-postaları korumasız gönderilir.
> - E-posta bildirimleri yalnızca Microsoft 365 hizmetleri için desteklenir.

Ayrıca kişilere [ilkeyi geçersiz kılma](#user-overrides) seçeneği de verebilirsiniz; böylece geçerli bir iş ihtiyaçları varsa veya ilke yanlış pozitif algılarsa engellenmez.

Kullanıcı bildirimleri ve ilke ipuçları yapılandırma seçenekleri, seçtiğiniz izleme konumlarına bağlı olarak değişir. Şunu seçtiyseniz:

- Exchange
- SharePoint
- OneDrive
- sohbeti ve kanalı Teams
- Bulut Uygulamaları için Defender


Çeşitli Microsoft uygulamaları için kullanıcı bildirimlerini etkinleştirebilir/devre dışı bırakabilirsiniz, bkz. [Veri Kaybı Önleme ilkesi ipuçları başvurusu](dlp-policy-tips-reference.md#data-loss-prevention-policy-tips-reference)

- İlke ipucuyla bildirimleri etkinleştirebilir/devre dışı bırakabilirsiniz.
    - veya içeriğini gönderen, paylaşan veya son değiştiren kullanıcıya e-posta bildirimleri gönderme
    - belirli kişilere bildirme

ve e-posta metnini, konusunu ve ilke ipucu metnini özelleştirin.

![Exchange, SharePoint, OneDrive, Teams Sohbet ve Kanal ile Bulut için Defender Uygulamaları için kullanılabilen kullanıcı bildirimi ve ilke ipucu yapılandırma seçenekleri](../media/dlp-user-notification-non-devices.png)

Yalnızca Cihazlar'ı seçtiyseniz sohbet ve kanal Teams Exchange, SharePoint, OneDrive, Teams uygulamaları ve Bulut için Defender uygulamaları için sağlanan tüm seçeneklerin yanı sıra Windows 10 görüntülenen bildirim başlığını ve içeriğini özelleştirme seçeneğine sahip olursunuz Aygıt.

![Cihazlar için kullanılabilen kullanıcı bildirimi ve ilke ipucu yapılandırma seçenekleri](../media/dlp-user-notification-devices.png)  

Bu parametreleri kullanarak metnin başlığını ve gövdesini özelleştirebilirsiniz. Gövde metni şunları destekler:

|Ortak ad  |Parametre  |Örnek
|---------|---------|---------|
|dosya adı     |%%FileName%% | Contoso belge 1 |
|işlem adı     |%%ProcessName%% | Word |
|ilke adı     |%%PolicyName%%| Contoso çok gizli |
|Eylem | %%AppliedActions%% | panodaki belge içeriğini başka bir uygulamaya yapıştırma |

**%%AppliedActions%%** bu değerleri ileti gövdesiyle değiştirmektedir:


|eylem ortak adı |%%AppliedActions%% parametresi için yerine değer girildi |
|---------|---------|
|kaldırılabilir depolamaya kopyalama    |*çıkarılabilir depolama birimine yazma*         |
|ağ paylaşımına kopyalama     |*ağ paylaşımına yazma*         |
|Yazdırma     |*Baskı*         |
|panodan yapıştırma  |*panodan yapıştırma*         |
|bluetooth üzerinden kopyalama   |*Bluetooth aracılığıyla aktarma*         |
|izin verilmeyen bir uygulamayla açma     |*bu uygulamayla açma*         |
|uzak masaüstüne kopyalama (RDP)     |*uzak masaüstüne aktarma*         |
|izin verilmeyen bir web sitesine yükleme     |*bu siteye yükleniyor*         |
|öğeye izin verilmeyen bir tarayıcı üzerinden erişme     |*bu tarayıcıyla açma*         |

Bu özelleştirilmiş metni kullanma

*%%AppliedActions%% %%ProcessName%% aracılığıyla %%FileName%% dosya adı kuruluşunuz tarafından kullanılamaz. %%PolicyName%% ilkesini atlamak istiyorsanız 'İzin Ver' seçeneğine tıklayın* 

bu metni özelleştirilmiş bildirimde üretir:

*panodan yapıştırma Dosya Adı: WINWORD.EXE aracılığıyla Contoso doc 1'e kuruluşunuz izin vermez. Contoso son derece gizli ilkesini atlamak istiyorsanız 'İzin Ver' düğmesine tıklayın*
 

> [!NOTE]
> Şirket içi konumu için kullanıcı bildirimleri ve ilke ipuçları kullanılamıyor

> [!NOTE]
> Yalnızca en yüksek önceliğe ve en kısıtlayıcı kurala ait ilke ipucu gösterilir. Örneğin, içeriğe erişimi engelleyen bir kuraldan gelen ilke ipucu, yalnızca bildirim gönderen bir kuraldan gelen ilke ipucu üzerinden gösterilir. Bu, kişilerin ilke ipuçlarının art arda görülmesini önler.

Bildirim ve ipucu metnini özelleştirme de dahil olmak üzere kullanıcı bildirimi ve ilke ipucu yapılandırması ve kullanımı hakkında daha fazla bilgi edinmek için bkz. 
- [E-posta bildirimleri gönderin ve DLP ilkeleri için ilke ipuçlarını gösterin](use-notifications-and-policy-tips.md#send-email-notifications-and-show-policy-tips-for-dlp-policies).
  
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

### <a name="user-overrides"></a>Kullanıcı geçersiz kılmaları

**Kullanıcı geçersiz kılmalarının** amacı, DLP ilkesinin çalışmalarına devam edebilmeleri için kullanıcılara Exchange, SharePoint, OneDrive veya Teams hassas öğeler üzerinde eylemleri engelleme gerekçeleriyle atlamaları için bir yol vermektir. Kullanıcı geçersiz kılmaları yalnızca **Office 365 hizmetlerindeki kullanıcılara bir ilke ipucuyla bildir** seçeneği etkinleştirildiğinde etkinleştirilir, bu nedenle kullanıcı geçersiz kılmaları Bildirimler ve İlke ipuçlarıyla el ele gider. 

![DLP ilkesi için kullanıcı geçersiz kılma seçenekleri](../media/dlp-user-overrides.png)

> [!NOTE]
> Şirket içi depolar konumu için kullanıcı geçersiz kılmaları kullanılamaz.

Genellikle, kuruluşunuz bir ilkeyi ilk dağıttığında kullanıcı geçersiz kılmaları yararlıdır. Geçersiz kılma gerekçelerinden ve hatalı pozitif sonuçların belirlenmesinden elde ettiğiniz geri bildirim, ilkenin ayarlanmasına yardımcı olur. 

<!-- This section covers what they are and how to best use them in conjunction with Test/Turn it on right away and link out to where to find the business justification for the override (DLP reports?  https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide)  https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide#view-the-justification-submitted-by-a-user-for-an-override-->

- En kısıtlayıcı kuraldaki ilke ipuçları kişilerin kuralı geçersiz kılmasına izin verirse, bu kuralın geçersiz kılınmış olması, içeriğin eşleştirilen diğer kuralları da geçersiz kılar.
 
<!--![User notifications and user overrides sections of DLP rule editor](../media/37b560d4-6e4e-489e-9134-d4b9daf60296.png)-->
 
Kullanıcı geçersiz kılmaları hakkında daha fazla bilgi edinmek için bkz:

- [Geçersiz kılma için kullanıcı tarafından gönderilen gerekçeyi görüntüleme](view-the-dlp-reports.md#view-the-justification-submitted-by-a-user-for-an-override)

### <a name="incident-reports"></a>Olay raporları

<!--DLP interacts with other M365 information protection services, like IR. Link this to a process outline for triaging/managing/resolving DLP incidents


https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide
https://docs.microsoft.com/en-us/microsoft-365/compliance/dlp-configure-view-alerts-policies?view=o365-worldwide-->

Bir kural eşleştirildiğinde, uyumluluk yöneticinize (veya seçtiğiniz kişilere) olayın ayrıntılarını içeren bir olay raporu gönderebilirsiniz. Rapor, eşleşen öğe, kuralla eşleşen gerçek içerik ve içeriği son değiştiren kişinin adı hakkında bilgi içerir. E-posta iletileri için rapor, DLP ilkesiyle eşleşen özgün iletiyi ek olarak da içerir.

DLP, olay bilgilerini [insider risk yönetimi](insider-risk-management.md) gibi diğer Microsoft Purview bilgi koruma hizmetlerine iletir. Olay bilgilerini insider risk yönetimine almak için **Olay raporları** önem düzeyini **Yüksek** olarak ayarlamanız gerekir.

<!--![Page for configuring incident reports](../media/31c6da0e-981c-415e-91bf-d94ca391a893.png)-->

Bir etkinlik bir kuralla her eşleştiğinde uyarılar gönderilebilir. Bu uyarılar gürültülü olabilir veya belirli bir süre içindeki eşleşme sayısına veya öğe hacmine göre daha az uyarıya toplanabilir.

![bir kural her eşleştiğinde veya zaman içinde daha az rapora toplendiğinde uyarı gönderme](../media/dlp-incident-reports-aggregation.png)

DLP, e-postayı Çevrimiçi veya OneDrive İş öğeler SharePoint farklı tarar. SharePoint Online ve OneDrive İş'da DLP, mevcut öğelerin yanı sıra yeni öğeleri de tarar ve bir eşleşme bulunduğunda bir olay raporu oluşturur. Exchange Online'da DLP yalnızca yeni e-posta iletilerini tarar ve ilke eşleşmesi varsa bir rapor oluşturur. DLP, posta kutusunda veya arşivde depolanan önceden var olan e-posta öğelerini ***taramaz veya eşleştirmez*** .

### <a name="additional-options"></a>Ek seçenekler

bir ilkede birden çok kuralınız varsa, düzenlemekte olduğunuz kuralla bir eşleşme olup olmadığını denetlemek ve kuralın değerlendirilme önceliğini ayarlamak için **Ek seçenekleri** kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Veri kaybı önlemeyi planlama (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Bir şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md#create-a-dlp-policy-from-a-template)
- [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
