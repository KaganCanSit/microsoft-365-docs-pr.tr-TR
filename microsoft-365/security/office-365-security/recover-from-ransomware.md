---
title: Fidye yazılımı saldırısından kurtarma
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
- m365solution-ransomware
description: Microsoft 365 yöneticileri fidye yazılımı saldırısından kurtarmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 328457e37ea6ae351abb2c5d5f0089246145b32c
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648667"
---
# <a name="recover-from-a-ransomware-attack-in-microsoft-365"></a>Microsoft 365'de fidye yazılımı saldırısından kurtarma

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kuruluşunuzu korumak için her türlü önlemi alsanız bile fidye [yazılımı](/windows/security/threat-protection/intelligence/ransomware-malware) saldırısına kurban gidebilirsiniz. Fidye yazılımı büyük bir iştir ve günümüzün tehdit alanında Microsoft 365 [karmaşık saldırılar için](https://i.blackhat.com/USA21/Wednesday-Handouts/us-21-Cloudy-With-A-Chance-Of-APT-Novel-Microsoft-365-Attacks-In-The-Wild.pdf) sürekli artan bir hedeftir.

Bu makaledeki adımlar, verileri kurtarmanız ve enfeksiyonun iç yayılmasını durdurmanız için size en iyi şansı verecektir. Başlamadan önce aşağıdaki öğeleri göz önünde bulundurun:

- Fidyeyi ödemenin dosyalarınıza erişimi geri döndüreceğinin garantisi yoktur. Aslında, fidye ödemek sizi daha fazla fidye yazılımı için bir hedef yapabilir.

  Zaten ödeme yapmış ancak saldırganın çözümünü kullanmadan kurtarıldıysanız, işlemi engelleyebilir mi diye bankanızla iletişime geçin.

  Fidye yazılımı saldırısını bu makalenin ilerleyen bölümlerinde açıklandığı gibi kolluk kuvvetlerine, dolandırıcılık raporlama web sitelerine ve Microsoft'a bildirmenizi de öneririz.

- Saldırıya ve sonuçlarına hızlı bir şekilde yanıt vermeniz önemlidir. Ne kadar uzun süre beklerseniz, etkilenen verileri kurtarma olasılığınız o kadar düşüktür.

## <a name="step-1-verify-your-backups"></a>1. Adım: Yedeklemelerinizi doğrulama

Çevrimdışı yedeklemeleriniz varsa, büyük olasılıkla fidye yazılımı yükünü (kötü amaçlı yazılım) ortamınızdan kaldırdıktan ve Microsoft 365 ortamlarınızda yetkisiz erişim olmadığını doğruladıktan **sonra** **şifrelenmiş verileri geri** yükleyebilirsiniz.

Yedekleriniz yoksa veya yedeklemeleriniz fidye yazılımından da etkilendiyse, bu adımı atlayabilirsiniz.

## <a name="step-2-disable-exchange-activesync-and-onedrive-sync"></a>2. Adım: Exchange ActiveSync ve OneDrive eşitleme devre dışı bırakma

Buradaki önemli nokta, fidye yazılımı tarafından veri şifrelemesinin yayılmasını durdurmaktır.

Fidye yazılımı şifrelemesinin hedefi olarak e-postadan şüpheleniyorsanız, posta kutularına kullanıcı erişimini geçici olarak devre dışı bırakın. Exchange ActiveSync, cihazlar ve Exchange Online posta kutuları arasında verileri eşitler.

Posta kutusunun Exchange ActiveSync devre dışı bırakmak için bkz. [Exchange Online'da kullanıcılar için Exchange ActiveSync devre dışı bırakma](https://support.microsoft.com/help/2795303).

Posta kutusuna diğer erişim türlerini devre dışı bırakmak için bkz:

- [Posta kutusu için MAPI'yi etkinleştirme veya devre dışı bırakma](/Exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-mapi).

- [Kullanıcı için POP3 veya IMAP4 erişimini etkinleştirme veya devre dışı bırakma](/Exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)

OneDrive eşitleme duraklatılması, bulut verilerinizin virüs bulaşmış olabilecek cihazlar tarafından güncelleştirilmesinden korunmasına yardımcı olur. Daha fazla bilgi için bkz. [OneDrive eşitlemeyi duraklatma ve sürdürme](https://support.microsoft.com/office/2152bfa4-a2a5-4d3a-ace8-92912fb4421e).

## <a name="step-3-remove-the-malware-from-the-affected-devices"></a>3. Adım: Kötü amaçlı yazılımı etkilenen cihazlardan kaldırma

Fidye yazılımıyla ilişkili yükü algılamak ve kaldırmak için tüm şüpheli bilgisayarlarda ve cihazlarda tam ve güncel bir virüsten koruma taraması çalıştırın.

Verileri eşitleyen cihazları veya eşlenen ağ sürücülerinin hedeflerini taramayı unutmayın.

[Windows Defender](https://www.microsoft.com/windows/comprehensive-security) veya (eski [istemciler için) Microsoft Security Essentials'ı](https://www.microsoft.com/download/details.aspx?id=5201) kullanabilirsiniz.

Fidye yazılımını veya kötü amaçlı yazılımları kaldırmanıza da yardımcı olacak bir alternatif[, Kötü Amaçlı Yazılımları Temizleme Aracı 'dır (MSRT).](https://www.microsoft.com/download/details.aspx?id=9905)

Bu seçenekler işe yaramazsa [Çevrimdışı Windows Defender](https://support.microsoft.com/help/17466) deneyebilir veya [kötü amaçlı yazılımları algılama ve kaldırmayla ilgili sorunları gidermeyi](https://support.microsoft.com/help/4466982) deneyebilirsiniz.

## <a name="step-4-recover-files-on-a-cleaned-computer-or-device"></a>4. Adım: Temizlenmiş bir bilgisayarda veya cihazda dosyaları kurtarma

Fidye yazılımı yükünü ortamınızdan kaldırmak için önceki adımı tamamladıktan sonra (fidye yazılımının dosyalarınızı şifrelemesini veya kaldırmasını engeller), Windows 11, Windows 10, Windows 8.1 ve yerel dosya ve klasörlerinizi kurtarmaya çalışmak için Windows 7'de Sistem Koruması'nı kullanarak [Dosya Geçmişi'ni](https://support.microsoft.com/help/17128) kullanabilirsiniz.

**Notlar**:

- Bazı fidye yazılımları yedekleme sürümlerini de şifreler veya siler, bu nedenle dosyaları geri yüklemek için Dosya Geçmişi veya Sistem Koruması'nı kullanamazsınız. Böyle bir durumda, sonraki bölümde açıklandığı gibi fidye yazılımı veya OneDrive etkilenmeyen harici sürücülerde veya cihazlarda yedeklemeleri kullanmanız gerekir.

- Bir klasör OneDrive ile eşitlenmişse ve Windows en son sürümünü kullanmıyorsanız, Dosya Geçmişi'ni kullanırken bazı sınırlamalar olabilir.

## <a name="step-5-recover-your-files-in-your-onedrive-for-business"></a>5. Adım: OneDrive İş dosyalarınızı kurtarma

OneDrive İş'da Dosyaları Geri Yükleme, tüm OneDrive son 30 gün içinde önceki bir noktaya geri yüklemenize olanak tanır. Daha fazla bilgi için bkz. [OneDrive'ınızı yeniden yükleyin](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15).

## <a name="step-6-recover-deleted-email"></a>6. Adım: Silinen e-postayı kurtarma

Fidye yazılımının tüm e-postanızı sildiği nadir durumlarda, muhtemelen silinen öğeleri kurtarabilirsiniz. Daha fazla bilgi için bkz.:

- [Kullanıcının posta kutusunda silinen iletileri kurtarma](/exchange/recipients-in-exchange-online/manage-user-mailboxes/recover-deleted-messages)

- [Windows için Outlook silinmiş öğeleri kurtarma](https://support.microsoft.com/office/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)

## <a name="step-7-re-enable-exchange-activesync-and-onedrive-sync"></a>7. Adım: Exchange ActiveSync ve OneDrive eşitleme yeniden etkinleştirme

Bilgisayarlarınızı ve cihazlarınızı temizledikten ve verilerinizi kurtardıktan sonra, [2. Adımda](#step-2-disable-exchange-activesync-and-onedrive-sync) daha önce devre dışı bırakmış olduğunuz Exchange ActiveSync ve OneDrive eşitleme yeniden etkinleştirebilirsiniz.

## <a name="step-8-optional-block-onedrive-sync-for-specific-file-extensions"></a>8. Adım (İsteğe bağlı): Belirli dosya uzantıları için OneDrive eşitleme engelleme

Kurtarıldıktan sonra, OneDrive İş istemcilerinin bu fidye yazılımından etkilenen dosya türlerini eşitlemesini engelleyebilirsiniz. Daha fazla bilgi için bkz. [Set-SPOTenantSyncClientRestriction](/powershell/module/sharepoint-online/set-spotenantsyncclientrestriction)

## <a name="report-the-attack"></a>Saldırıyı bildirme

### <a name="contact-law-enforcement"></a>Kolluk kuvvetlerine başvurun

Yerel veya federal kolluk kuvvetlerinize başvurmalısınız. Örneğin, Birleşik Devletler iseniz [FBI yerel saha ofisi](https://www.fbi.gov/contact-us/field), [IC3](http://www.ic3.gov/complaint/default.aspx) veya [Gizli Servis](http://www.secretservice.gov/) ile iletişime geçebilirsiniz.

### <a name="submit-a-report-to-your-countrys-scam-reporting-website"></a>Ülkenizin dolandırıcılık raporlama web sitesine rapor gönderme

Dolandırıcılık raporlama web siteleri, dolandırıcılıkları önleme ve önleme hakkında bilgi sağlar. Ayrıca dolandırıcılık kurbanı olup olmadığınız bildirecek mekanizmalar da sağlar.

- Avustralya: [SCAMwatch](http://www.scamwatch.gov.au/)

- Kanada: [Kanada Dolandırıcılıkla Mücadele Merkezi](http://www.antifraudcentre-centreantifraude.ca/)

- Fransa: [Agence nationale de la sécurité des systèmes d'information](http://www.ssi.gouv.fr/)

- Almanya: [Bundesamt für Sicherheit in der Informationstechnik](https://www.bsi.bund.de/DE/Home/home_node.html)

- İrlanda: [a Garda Síochána](http://www.garda.ie/)

- Yeni Zelanda: [Tüketici İşleri Dolandırıcılıkları](http://www.consumeraffairs.govt.nz/scams)

- İsviçre [Nationales Zentrum für Cybersicherheit NCSC](https://www.ncsc.admin.ch/ncsc/de/home.html)

- Birleşik Krallık: [Eylem Sahtekarlığı](http://www.actionfraud.police.uk/)

- Birleşik Devletler: [On Guard Online](http://www.onguardonline.gov/)

Ülkeniz listede yoksa yerel veya federal kolluk kuvvetlerinize sorun.

### <a name="submit-email-messages-to-microsoft"></a>Microsoft'a e-posta iletileri gönderme

Fidye yazılımı içeren kimlik avı iletilerini çeşitli yöntemlerden birini kullanarak bildirebilirsiniz. Daha fazla bilgi için bkz. [İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).

## <a name="additional-ransomware-resources"></a>Ek fidye yazılımı kaynakları

Microsoft'tan önemli bilgiler:

- [Artan fidye yazılımı tehdidi](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/), Microsoft On the Issues blog gönderisi 20 Temmuz 2021'de
- [İnsan tarafından çalıştırılan fidye yazılımı](/security/compass/human-operated-ransomware)
- [Fidye yazılımı ve gaspa karşı hızla koruma](/security/compass/protect-against-ransomware)
- [2021 Microsoft Dijital Savunma Raporu](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (bkz. sayfa 10-19)
- [Fidye yazılımı: Microsoft 365 Defender portalında sürekli ve sürekli tehdit tehdit](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) analizi raporu

Microsoft 365:

- [Microsoft 365 kiracınız için fidye yazılımı koruması dağıtın](/microsoft-365/solutions/ransomware-protection-microsoft-365)
- [Azure ve Microsoft 365 ile Fidye Yazılımı Dayanıklılığını En Üst Düzeye Çıkarma](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Kötü amaçlı yazılım ve fidye yazılımı koruması](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Windows bilgisayarınızı fidye yazılımlarından koruma](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [SharePoint Online'da fidye yazılımlarını işleme](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- Microsoft 365 Defender portalında [fidye yazılımı için tehdit analizi raporları](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag)

Microsoft 365 Defender:

- [Gelişmiş avcılık ile fidye yazılımı bulma](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [Fidye Yazılımı Saldırısı için Azure Defenses](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Azure ve Microsoft 365 ile Fidye Yazılımı Dayanıklılığını En Üst Düzeye Çıkarma](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Fidye yazılımlarına karşı koruma sağlamak için yedekleme ve geri yükleme planı](/security/compass/backup-plan-to-protect-against-ransomware)
- [Microsoft Azure Backup ile fidye yazılımlarından korunmaya yardımcı olun](https://www.youtube.com/watch?v=VhLOr2_1MCg) (26 dakikalık video)
- [Sistemik kimlik güvenliğinin aşılmasından kurtarma](/azure/security/fundamentals/recover-from-identity-compromise)
- [Microsoft Sentinel'de gelişmiş çok aşamalı saldırı algılama](/azure/sentinel/fusion#ransomware)
- [Microsoft Sentinel'de Fidye Yazılımı için Fusion Algılama](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Defender for Cloud Apps:

-  [Bulut için Defender Uygulamalarında anomali algılama ilkeleri oluşturma](/cloud-app-security/anomaly-detection-policy)

Microsoft Güvenlik ekibi blog gönderileri:

- [Fidye yazılımlarını önleme ve kurtarma için 3 adım (Eylül 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [İnsan tarafından çalıştırılan fidye yazılımıyla mücadele kılavuzu: Bölüm 1 (Eylül 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  Microsoft'un Algılama ve Yanıt Ekibi'nin (DART) fidye yazılımı olay araştırmalarını nasıl yürüttüğüne ilişkin temel adımlar.

- [İnsan tarafından çalıştırılan fidye yazılımıyla mücadele kılavuzu: Bölüm 2 (Eylül 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  Öneriler ve en iyi yöntemler.

- [Siber güvenlik risklerini anlayarak dayanıklı hale gelme: Bölüm 4— Mevcut tehditlerde gezinme (Mayıs 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  **Fidye yazılımı** bölümüne bakın.

- [İnsan tarafından işletilen fidye yazılımı saldırıları: Önlenebilir bir olağanüstü durum (Mart 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Gerçek saldırıların saldırı zinciri analizlerini içerir.

- [Fidye yazılımı yanıtı— ödeme yapmak için mi yoksa ödememek için mi? (Aralık 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk Hydro fidye yazılımı saldırısına şeffaflıkla yanıt veriyor (Aralık 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
