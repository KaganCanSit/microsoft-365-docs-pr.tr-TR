---
title: Müşteri tarafından yönetilen şifreleme özellikleri
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
ms.custom:
- seo-marvel-mar2020
description: Bu makalede, bu makalenin devamsında, farklı kullanıcılarla birlikte yönet8 veya Microsoft 365.
ms.openlocfilehash: 80a0726e112324a673fc964a9fabdbc3ba0ac42e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988132"
---
# <a name="customer-managed-encryption-features"></a>Müşteri tarafından yönetilen şifreleme özellikleri

Microsoft tarafından yönetilen Microsoft 365 şifreleme teknolojileriyle birlikte, Microsoft 365 aşağıdakiler gibi yöneterek yapılandırılan ek şifreleme teknolojileriyle de çalışır:

- [Azure Hak Yönetimi](/azure/information-protection/what-is-azure-rms)

- [Güvenli Çok Amaçlı İnternet Posta Uzantısı](https://blogs.technet.com/b/exchange/archive/2014/12/15/how-to-configure-s-mime-in-office-365.aspx)

- [Office 365 İleti Şifrelemesi](https://products.office.com/en-us/exchange/office-365-message-encryption)

- [İş ortağı bir kuruluşla güvenli posta akışı](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)

Bu teknolojiler hakkında ek bilgi için, aşağıdaki [Microsoft 365 bakın](/office365/servicedescriptions/office-365-service-descriptions-technet-library).

## <a name="azure-rights-management"></a>Azure Hak Yönetimi

[Azure Hak Yönetimi](/azure/information-protection/what-is-azure-rms) (Azure RMS), [Azure Information Protection tarafından kullanılan koruma teknolojisidir](/information-protection/understand-explore/what-is-information-protection). Telefon, tablet ve bilgisayarlar gibi birden çok platform ve cihaz genelinde dosyalarınızın ve e-postanın güvenliğini sağlamak için şifreleme, kimlik ve yetkilendirme ilkeleri kullanır. Koruma verilerle birlikte olduğu için bilgiler hem kuruluş içinde hem de dışında korunabilirsiniz. Azure RMS tüm dosya türleri için kalıcı koruma sağlar, dosyaları her yerde korur, işletmeler arasında işbirliğini ve çeşitli standart Windows olmayan Windows destekler. Azure RMS koruması, veri [kaybı önleme (DLP) ilkelerini de geliştirebilirsiniz](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention). Hangi uygulama ve hizmetlerin Azure Information Protection'dan Azure Rights Management hizmetini kullanabileceği hakkında daha fazla bilgi için bkz. [Uygulamalar Azure Hak Yönetimi hizmetini nasıl destekler](/information-protection/understand-explore/applications-support).

Azure RMS, E-Microsoft 365 bütünleştirilmiştir ve tüm müşteriler tarafından kullanılabilir. Azure RMS Microsoft 365 i kullanmak üzere yapılandırmak için, yönetim merkezinde IRM'yi Azure Rights Management'i kullanmak üzere yapılandırma ve Bilgi Hakları Yönetimi'ni [(IRM) ayarlama SharePoint bakın](../enterprise/activate-rms-in-microsoft-365.md). Şirket içi Active Directory (AD) RMS sunucusu kullanıyorsanız [, IRM'yi](/office365/SecurityCompliance/configure-irm-to-use-an-on-premises-ad-rms-server) de şirket içi AD RMS sunucusunu kullanmak üzere yapılandırabilirsiniz, ancak diğer kuruluşlarla güvenli işbirliği gibi yeni özellikleri kullanmak için [Azure RMS'ye](/azure/information-protection/migrate-from-ad-rms-to-azure-rms) geçişnizi kesinlikle öneririz.

Azure RMS ile müşteri verilerini korumanız, Azure RMS'nin verileri şifrelemek için SHA-256 karma algoritmasına sahip 2048 bit RSA asimetrik bir anahtar kullandığı anlamına gelir. Belgelerinizi ve e-postanızı Office için simetrik anahtar AES 128 bit'tir. Azure RMS tarafından korunan her belge veya e-posta için, Azure RMS tek bir AES anahtarı ("içerik anahtarı" oluşturur) ve bu anahtar belgeye ekli olur ve belgenin sürümleri aracılığıyla devam eder. İçerik anahtarı, belgeye ilişkin ilkenin bir parçası olarak kuruluşun RSA anahtarıyla ("Azure Information Protection kiracı anahtarı") korunur ve ilke belgenin yazarı tarafından da imzalanmıştır. Bu kiracı anahtarı, kuruluş için Azure RMS tarafından korunan tüm belgelerde ve e-postalarda yaygındır ve bu anahtar yalnızca kuruluşun müşteri tarafından yönetilen bir kiracı anahtarı kullanıyor olması gerekir. Azure RMS tarafından kullanılan şifreleme denetimleri hakkında daha fazla bilgi için bkz. [Azure RMS nasıl çalışır? Daha sonra.](/information-protection/understand-explore/how-does-it-work)

Varsayılan bir Azure RMS uygulamasında, Microsoft her kiracı için benzersiz olan kök anahtarı üretir ve yönetir. Müşteriler, şirket içi HSM'lerde (donanım güvenlik modülleri) anahtarınızı oluşturmanızı sağlayan Kendi Anahtarınızı Getir [(BYOK)](/azure/information-protection/plan-implement-tenant-key) adlı bir anahtar yönetim yöntemi kullanarak Azure RMS'de kök anahtarlarının yaşam döngüsünü yönetebilir ve Microsoft'un FIPS 140-2 Düzey 2 Doğrulanmış HSM'lerine aktardikten sonra bu anahtarın kontrolünüz altında kalabilir. Anahtarlar onları koruyan HSMs'den dışarı aktarılamay veya ayıklanamaylarından, kök anahtara erişim personele verilmez. Buna ek olarak, herhangi bir anda kök anahtara tüm erişimi gösteren neredeyse gerçek zamanlı bir günlüğe erişsiniz. Daha fazla bilgi için bkz [. Günlüğe Kaydetme ve Azure Hak Yönetimi Kullanımını Çözümleme](/azure/information-protection/log-analyze-usage).

Azure Hak Yönetimi; kablo dokunma, ortadaki adam saldırıları, veri hırsızlığı ve kuruluş paylaşım ilkelerinin ilerlemiş ihlalleri gibi tehditlerin en düşüklerinde size yardımcı olur. Aynı zamanda, uygun izinlere sahip olmayan ve yetkisiz bir kullanıcı tarafından müşteri verilerine yönelik herhangi bir nedensiz erişim, bu verilere uygun olmayan ilkeler aracılığıyla engellenebilir; böylece, verilerin bilerek veya bilmeden yanlış ellere düşmesi riski azaltılmış olur ve veri kaybı önleme işlevleri sağlar. Azure Information Protection'ın bir parçası olarak kullanılıyorsa, Azure RMS Ayrıca Veri Sınıflandırma ve etiketleme özellikleri, içerik işaretleme, belge erişimi izleme ve erişim iptal özellikleri sağlar. Bu özellikler hakkında daha fazla bilgi edinmek için bkz. [Azure Information Protection](/information-protection/understand-explore/what-is-information-protection) nedir, [Azure Information Protection dağıtımı yol haritası](/information-protection/plan-design/deployment-roadmap) ve [Azure Information Protection için Hızlı başlangıç öğreticisi](/information-protection/get-started/infoprotect-quick-start-tutorial).

## <a name="secure-multipurpose-internet-mail-extension"></a>Güvenli Çok Amaçlı İnternet Posta Uzantısı

Güvenli/Çok Amaçlı İnternet Posta Uzantıları (S/MIME), MIME verilerin ortak anahtar şifrelemesi ve dijital olarak imzalanması için kullanılan bir standarttır. S/MIME RFCs 3369, 3370, 3850, 3851 ve diğerlerinde tanımlanır. Kullanıcının bir e-postayı şifrelemesini ve e-postayı dijital olarak imzalamasını sağlar. S/MIME kullanılarak şifrelenmiş bir e-postanın şifresini çözmek için e-postanın alıcısı kendi özel anahtarını kullanarak çözebilir; bu anahtar yalnızca o alıcı tarafından kullanılabilir. Bu nedenle e-postanın alıcısı dışında herhangi biri bu e-postanın şifresini çözemz.

[Microsoft S/MIME'i destekler](https://blogs.technet.com/b/exchange/archive/2014/12/15/how-to-configure-s-mime-in-office-365.aspx). Ortak sertifikalar müşterinin şirket içi Active Directory'sinde dağıtılır ve bu sertifikalar bir kullanıcı kiracısına çoğaltılabilir özniteliklerde Microsoft 365 depolanır. Ortak anahtarlara karşılık gelen özel anahtarlar şirket içinde kalır ve bu anahtarlara hiçbir zaman Office 365. Kullanıcılar, Outlook, Web üzerinde Outlook ve diğer istemcileri kullanarak kuruluşta iki kullanıcı arasında e-posta oluşturamaz, şifrelerini çözebilir, okuyabilir ve dijital Exchange ActiveSync imzalar. Daha fazla bilgi için bkz. [S/MIME şifrelemesi şimdi Office 365](https://blogs.office.com/2014/02/26/smime-encryption-now-in-office-365/).

## <a name="office-365-message-encryption"></a>Office 365 İleti Şifrelemesi

[Office 365 İleti Şifrelemesi](https://products.office.com/exchange/office-365-message-encryption) (OME) [yerleşik olarak Azure Information Protection](/information-protection/understand-explore/what-is-information-protection) (AIP) sistemi, şifrelenmiş ve hak korunan postaları herkese göndermenizi sağlar. OME, havale ve ortadaki adam saldırılarına ve uygun izinlere sahip olmayan yetkisiz bir kullanıcının verilerine uyarısız erişim gibi tehditlere neden olur. Azure Information Protection'ın üzerine yerleşik olarak daha basit, daha sezgisel, güvenli bir e-posta deneyimi sağlayan yatırımlar yaptık. E-postadan veya Microsoft 365 içindeki veya dışındaki herkese gönderilen iletileri koruyabilirsiniz. Bu iletiler E-posta, Microsoft Hesabı ve Google Kimlikleri dahil olmak üzere herhangi bir kimlik Azure Active Directory, çeşitli posta istemcilerini kullanarak  bakabilirsiniz. Kuruluşun şifreli iletileri nasıl kullanabileceği hakkında daha fazla bilgi için [bkz. Office 365 İleti Şifrelemesi](./ome.md).

## <a name="transport-layer-security"></a>Aktarım Katmanı Güvenliği

İş ortağıyla güvenli bir iletişim sağlamak için, güvenlik ve ileti bütünlüğü sağlamak üzere gelen ve giden bağlayıcıları kullanabilirsiniz. Sertifika kullanarak her bağlayıcıda zorlamalı gelen ve giden TLS yapılandırabiliyorsanız. Şifreli bir SMTP kanalı kullanmak, ortadaki bir adam saldırısı yoluyla verilerin çalınmalarını önlenebilir. Daha fazla bilgi için bkz. [Exchange Online bağlantılarının güvenliğini sağlamak için TLS'yi nasıl kullanır?](./exchange-online-uses-tls-to-secure-email-connections.md)

## <a name="domain-keys-identified-mail"></a>Etki Alanı Anahtarları Tanımlanan Posta

Exchange Online Protection (EOP) ve kimlik doğrulaması, Exchange Online Etki Alanı Anahtarları Tanımlanan Posta (DKIM) iletilerinin gelen doğrulamasını destekler. DKIM, bir iletinin kaynaklandığını ve başka biri tarafından kimlikle gönderildiğini belirten etki alanından gönderildiğini doğrulamaya için kullanılan bir yöntemdir. E-posta iletisi, e-postayı göndermekten sorumlu kuruluşa bağlı ve büyük bir e-posta şifreleme parçası. Bu sylanın üç parçası hakkında daha fazla bilgi için bkz:

- [SPF'yi, sanallık engellemeye yardımcı olacak şekilde ayarlama](/office365/SecurityCompliance/set-up-spf-in-office-365-to-help-prevent-spoofing)

- [Özel etki alanınıza gönderilen giden e-postayı doğrulamak için DKIM kullanma](/office365/SecurityCompliance/use-dkim-to-validate-outbound-email)

- [E-postayı doğrulamak için DMARC kullanma](/office365/SecurityCompliance/use-dmarc-to-validate-email)