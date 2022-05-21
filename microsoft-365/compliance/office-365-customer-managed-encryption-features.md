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
description: Bu makalede, Microsoft 365'de yönetebileceğiniz ve yapılandırabileceğiniz şifreleme teknolojileri hakkında bilgi edineceksiniz.
ms.openlocfilehash: 55bc743f83b79ac83c764af24ef4100e5f72369d
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622544"
---
# <a name="customer-managed-encryption-features"></a>Müşteri tarafından yönetilen şifreleme özellikleri

- [Azure Rights Management](/azure/information-protection/what-is-azure-rms)

- [Microsoft Purview İleti Şifrelemesi](https://products.office.com/en-us/exchange/office-365-message-encryption)

- [İş ortağı kuruluşla güvenli posta akışı](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)

Bu teknolojiler hakkında daha fazla bilgi için [Microsoft 365 hizmet açıklamalarına](/office365/servicedescriptions/office-365-service-descriptions-technet-library) bakın.

## <a name="azure-rights-management"></a>Azure Rights Management

[Azure Rights Management](/azure/information-protection/what-is-azure-rms) (Azure RMS), [Azure Information Protection](/information-protection/understand-explore/what-is-information-protection) tarafından kullanılan koruma teknolojisidir. Telefon, tablet ve bilgisayar gibi birden çok platform ve cihazda dosyalarınızın ve e-postanızın güvenliğini sağlamaya yardımcı olmak için şifreleme, kimlik ve yetkilendirme ilkelerini kullanır. Koruma verilerle birlikte kaldığından, bilgiler hem kuruluşunuzun içinde hem de dışında korunabilir. Azure RMS tüm dosya türlerini kalıcı olarak korur, dosyaları her yerde korur, işletmeler arası işbirliğini destekler ve çok çeşitli Windows ve Windows olmayan cihazlar sunar. Azure RMS koruması [, veri kaybı önleme (DLP) ilkelerini](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) de genişletebilir. Azure Information Protection azure Rights Management hizmetini hangi uygulama ve hizmetlerin kullanabileceği hakkında daha fazla bilgi için bkz. [Uygulamalar Azure Rights Management hizmetini nasıl destekler](/information-protection/understand-explore/applications-support)?

Azure RMS, Microsoft 365 ile tümleşiktir ve tüm müşteriler tarafından kullanılabilir. Microsoft 365 Azure RMS kullanacak şekilde yapılandırmak için bkz. [IRM'yi Azure Rights Management kullanacak şekilde yapılandırma ve SharePoint yönetim merkezinde Bilgi Rights Management (IRM) Ayarlama](../enterprise/activate-rms-in-microsoft-365.md). şirket içi Active Directory (AD) RMS sunucusu çalıştırırsanız, [IRM'yi şirket içi AD RMS sunucusu kullanacak şekilde de yapılandırabilirsiniz](/office365/SecurityCompliance/configure-irm-to-use-an-on-premises-ad-rms-server), ancak diğer kuruluşlarla güvenli işbirliği gibi yeni özellikleri kullanmak için [Azure RMS'ye geçmenizi](/azure/information-protection/migrate-from-ad-rms-to-azure-rms) kesinlikle öneririz.

Azure RMS ile müşteri verilerini koruduğunuzda, Azure RMS verileri şifrelemek için tutarlılık için SHA-256 karma algoritmasına sahip 2048 bit RSA asimetrik anahtarı kullanır. Office belgeler ve e-postalar için simetrik anahtar AES 128 bit'tir. Azure RMS tarafından korunan her belge veya e-posta için, Azure RMS tek bir AES anahtarı ("içerik anahtarı") oluşturur ve bu anahtar belgeye eklenir ve belgenin sürümleri arasında kalır. İçerik anahtarı, belgedeki ilkenin bir parçası olarak kuruluşun RSA anahtarıyla ("Azure Information Protection kiracı anahtarı") korunur ve ilke belgenin yazarı tarafından da imzalanır. Bu kiracı anahtarı, kuruluş için Azure RMS tarafından korunan tüm belgelerde ve e-postalarda yaygındır ve bu anahtar yalnızca kuruluş müşteri tarafından yönetilen bir kiracı anahtarı kullanıyorsa Azure Information Protection yöneticisi tarafından değiştirilebilir. Azure RMS tarafından kullanılan şifreleme denetimleri hakkında daha fazla bilgi için bkz. [Azure RMS nasıl çalışır? Kaputun altında](/information-protection/understand-explore/how-does-it-work).

Varsayılan bir Azure RMS uygulamasında, Microsoft her kiracı için benzersiz olan kök anahtarı oluşturur ve yönetir. Müşteriler, azure Key Vault Hizmetleri ile Azure RMS'de kök anahtarlarının yaşam döngüsünü, şirket içi HSM'lerde (donanım güvenlik modülleri) anahtarınızı oluşturmanıza ve Microsoft'un FIPS 140-2 Düzey 2 doğrulanmış HSM'lerine aktardıktan sonra bu anahtarı denetlemenize olanak tanıyan [Kendi Anahtarını Getir (BYOK)](/azure/information-protection/plan-implement-tenant-key) adlı bir anahtar yönetim yöntemi kullanarak yönetebilir. Anahtarlar dışarı aktarılmadığından veya bunları koruyan HSM'lerden ayıklanamadığından kök anahtara erişim hiçbir personele verilmez. Ayrıca, istediğiniz zaman kök anahtara tüm erişimi gösteren gerçek zamanlıya yakın bir günlüğe erişebilirsiniz. Daha fazla bilgi için bkz[. Azure Rights Management Kullanımını Günlüğe Kaydetme ve Çözümleme](/azure/information-protection/log-analyze-usage).

Azure Rights Management, kabloyla dokunma, ortadaki adam saldırıları, veri hırsızlığı ve kuruluş paylaşım ilkelerinin kasıtsız ihlalleri gibi tehditlerin azaltılmasına yardımcı olur. Aynı zamanda, uygun izinlere sahip olmayan yetkisiz bir kullanıcı tarafından aktarımdaki veya bekleyen müşteri verilerinin herhangi bir yersiz erişimi, söz konusu verileri izleyen ilkeler aracılığıyla engellenir ve böylece verilerin bilerek veya bilmeden yanlış ellere düşme riski azaltılır ve veri kaybı önleme işlevleri sağlanır. Azure Information Protection'nin bir parçası olarak kullanıldığında, Azure RMS veri sınıflandırma ve etiketleme özellikleri, içerik işaretleme, belge erişim izleme ve erişim iptali özellikleri de sağlar. Bu özellikler hakkında daha fazla bilgi edinmek için bkz. [Azure Information Protection nedir](/information-protection/understand-explore/what-is-information-protection), [Azure Information Protection dağıtım yol haritası](/information-protection/plan-design/deployment-roadmap) ve [Azure Information Protection için hızlı başlangıç öğreticisi](/information-protection/get-started/infoprotect-quick-start-tutorial).

## <a name="secure-multipurpose-internet-mail-extension"></a>Güvenli Çok Amaçlı İnternet Posta Uzantısı

Güvenli/Çok Amaçlı İnternet Posta Uzantıları (S/MIME), mime verilerinin ortak anahtar şifrelemesi ve dijital imzaları için bir standarttır. S/MIME, RFC 3369, 3370, 3850, 3851 ve diğerleri ile tanımlanır. Kullanıcının e-postayı şifrelemesine ve e-postayı dijital olarak imzalamasına olanak tanır. S/MIME kullanılarak şifrelenen bir e-postanın şifresi yalnızca özel anahtarı kullanılarak e-postanın alıcısı tarafından çözülebilir ve bu yalnızca bu alıcı tarafından kullanılabilir. Bu nedenle e-postaların şifresi, e-postanın alıcısından başka biri tarafından çözülemez.

[Microsoft, S/MIME'i destekler](https://blogs.technet.com/b/exchange/archive/2014/12/15/how-to-configure-s-mime-in-office-365.aspx). Genel sertifikalar müşterinin şirket içi Active Directory dağıtılır ve Microsoft 365 kiracıya çoğaltılabilir özniteliklerde depolanır. Ortak anahtarlara karşılık gelen özel anahtarlar şirket içinde kalır ve hiçbir zaman Office 365 iletilmez. Kullanıcılar Outlook, Web üzerinde Outlook ve Exchange ActiveSync istemcilerini kullanarak bir kuruluştaki iki kullanıcı arasındaki e-postaları oluşturabilir, şifreleyebilir, şifreleyebilir, okuyabilir ve dijital olarak imzalayabilir. Daha fazla bilgi için bkz. [S/MIME şifrelemesi şimdi Office 365](https://blogs.office.com/2014/02/26/smime-encryption-now-in-office-365/).

## <a name="office-365-message-encryption"></a>Office 365 İleti Şifrelemesi

[Azure](/information-protection/understand-explore/what-is-information-protection) Information Protection (AIP) üzerinde oluşturulan [Office 365 İleti Şifrelemesi](https://products.office.com/exchange/office-365-message-encryption) (OME), herkese şifreli ve hak korumalı posta göndermenizi sağlar. OME, kabloyla dokunma ve ortadaki adam saldırıları gibi tehditleri ve uygun izinlere sahip olmayan yetkisiz bir kullanıcının verilere yetkisiz erişimi gibi diğer tehditleri azaltır. Azure Information Protection üzerine inşa edilmiş daha basit, daha sezgisel, güvenli bir e-posta deneyimi sunan yatırımlar yaptık. kuruluşunuzun içindeki veya dışındaki herkese Microsoft 365 gönderilen iletileri koruyabilirsiniz. Bu iletiler Azure Active Directory, Microsoft Hesabı ve Google Kimlikleri dahil olmak üzere herhangi bir kimlik kullanılarak çeşitli posta istemcileri arasında görüntülenebilir. Kuruluşunuzun şifrelenmiş iletileri nasıl kullanabileceği hakkında daha fazla bilgi için bkz. [İleti Şifrelemesi Office 365](./ome.md).

## <a name="transport-layer-security"></a>Aktarım Katmanı Güvenliği

İş ortağıyla güvenli iletişim sağlamak istiyorsanız, güvenlik ve ileti bütünlüğü sağlamak için gelen ve giden bağlayıcıları kullanabilirsiniz. Bir sertifika kullanarak her bağlayıcıda zorlamalı gelen ve giden TLS'yi yapılandırabilirsiniz. Şifrelenmiş BIR SMTP kanalı kullanmak, verilerin ortadaki adam saldırısıyla çalınmasını engelleyebilir. Daha fazla bilgi için bkz. [Exchange Online, e-posta bağlantılarının güvenliğini sağlamak için TLS'yi nasıl kullanır](./exchange-online-uses-tls-to-secure-email-connections.md)?

## <a name="domain-keys-identified-mail"></a>Etki Alanı Anahtarları Tanımlanan Posta

Exchange Online Protection (EOP) ve Exchange Online, Etki Alanı Anahtarları Tanımlanan Posta (DKIM) iletilerinin gelen doğrulamayı destekler. DKIM, bir iletinin kaynaklandığını söylediği etki alanından gönderildiğini ve başka biri tarafından sahte olmadığını doğrulamaya yönelik bir yöntemdir. E-posta iletisini göndermekle sorumlu kuruluşa bağlar ve daha büyük bir e-posta şifreleme paradigması kapsamındadır. Bu paradigmanın üç bölümü hakkında daha fazla bilgi için bkz:

- [Kimlik sahtekarlığını önlemeye yardımcı olmak için SPF'yi ayarlama](/office365/SecurityCompliance/set-up-spf-in-office-365-to-help-prevent-spoofing)

- [Özel etki alanınıza gönderilen giden e-postayı doğrulamak için DKIM'yi kullanma](/office365/SecurityCompliance/use-dkim-to-validate-outbound-email)

- [E-postayı doğrulamak için DMARC kullanma](/office365/SecurityCompliance/use-dmarc-to-validate-email)
