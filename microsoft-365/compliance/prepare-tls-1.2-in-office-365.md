---
title: Office 365 ve Office 365 GCC'de TLS 1.2'ye hazırlanma
description: TLS 1.0 ve 1.1 desteği devre dışı bırakıldıktan sonra Office 365 ve Office 365 GCC'deki tüm istemci-sunucu ve tarayıcı-sunucu kombinasyonları için TLS 1.2'yi kullanmaya hazırlanma
author: kccross
manager: laurawi
ms.localizationpriority: medium
search.appverid:
- MET150
audience: ITPro
ms.service: O365-seccomp
ms.topic: article
ms.author: shmehta
ms.reviewer: krowley
appliesto:
- Office 365 Business
ms.openlocfilehash: d2562e52c307fcf251b0b3030219aca68dc96a0a
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "63012823"
---
# <a name="preparing-for-tls-12-in-office-365-and-office-365-gcc"></a>Office 365 ve Office 365 GCC'de TLS 1.2'ye hazırlanma

## <a name="summary"></a>Özet

Microsoft, müşterilerimize sınıfının en iyisi şifreleme sağlamak için Office 365 ve Office 365 GCC'deki Aktarım Katmanı Güvenliği (TLS)'nin 1.0 ve 1.1 sürümlerini kullanımdan kaldırmayı planlamaktadır. Verilerinizin güvenliğinin önemli olduğunu biliyoruz ve TLS hizmetini kullanımınızı etkileyebilecek değişiklikler konusunda şeffaflığa olan bağlılığımızı sürdürüyoruz.

[Microsoft TLS 1.0 uygulamasının](https://support.microsoft.com/help/3117336/schannel-implementation-of-tls-1-0-in-windows-security-status-update-n) bilinen güvenlik açıkları yoktur. Ancak gelecekteki protokol indirgeme saldırıları ve diğer TLS güvenlik açıkları potansiyeli nedeniyle, Microsoft Office 365 ve Office 365 GCC'de TLS 1.0 ve 1.1 desteğini kesiyoruz.

TLS 1.0 ve 1.1 bağımlılıklarının nasıl kaldırılacağı hakkında bilgi için aşağıdaki makaleye bakın: [TLS 1.0 problemini çözme](https://www.microsoft.com/download/details.aspx?id=55266).

TLS 1.2'ye yükseltdikten sonra, kullanmakta olduğu şifreleme paketlerinin Azure Front Door tarafından desteklendikten emin olun. Microsoft 365 Azure Front Door'da şifreleme paketi desteğinde ufak farklılıklar vardır. Ayrıntılar için bkz[. Azure Front Door tarafından desteklenen geçerli şifreleme paketleri nedir?](/azure/frontdoor/front-door-faq#what-are-the-current-cipher-suites-supported-by-azure-front-door-)

## <a name="more-information"></a>Daha fazla bilgi

Ocak 2020 itibariyle TLS 1.0 ve 1.1 sürümlerini kullanımdan kaldırmaya başladık. DoD veya GCC High örneklerimizde Office 365'e TLS 1.0 veya 1.1 üzerinden bağlanan hiçbir istemci, aygıt veya hizmet desteklenmez. Office 365'ın ticari müşterileri için TLS 1.0 ve 1.1'in kullanımdanlarımız 15 Ekim 2020'de sona esinde başlayacak ve sonraki haftalarda ve aylarda da promosyon devam edecek.

Tüm istemci-sunucu ve tarayıcı-sunucu kombinasyonlarının Office 365 hizmetlerine bağlantı sağlamak için TLS 1.2 (veya sonraki bir sürüm) kullanmasını öneririz. Belirli istemci-sunucu ve tarayıcı-sunucu kombinasyonlarını güncelleştirmeniz gerekebilir.

  > [!NOTE]
  > SMTP Gelen posta akışı için, TLS 1.0 ve 1.1'in kullanımdan indikten sonra, yalnızca TLS 1.2 bağlantısını kabul etmiş oluruz. Bununla birlikte, hiçbir TLS olmadan şifrelenmemiş SMTP Bağlantısı'ni kabul etmeye devam edeceğiz. Herhangi bir şifreleme olmadan e-posta iletimi önerilmez. 

TLS 1.2'yi kullanmak için, MICROSOFT 365 API'leri TLS 1.0 veya TLS 1.1 üzerinden çağıran uygulamaları güncelleştirmeniz gerekir. .NET 4.5 varsayılan olarak TLS 1.1'i kullanır. .NET yapılandırmanızı güncelleştirmek için bkz. [İstemcilerde Aktarım Katmanı Güvenliği (TLS) 1.2'yi etkinleştirme](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

Aşağıdaki istemcilerin TLS 1.2 kullanamadığı bilinmektedir. Hizmete kesintisiz erişim sağlamak için bu istemcileri güncelleştirin.

- Android 4.3 ve önceki sürümleri
- Firefox 5.0 ve önceki sürümleri
- Windows 7 ve önceki sürümlerinde Internet Explorer 8-10
- Windows Phone 8'de Internet Explorer 10
- Safari 6.0.4/OS X10.8.4 ve önceki sürümleri

### <a name="tls-12-for-microsoft-teams-rooms-and-surface-hub"></a>Microsoft Teams Odaları ve Surface Hub için TLS 1.2

Microsoft Teams Rooms (daha önce Skype Oda Sistemi V2 SRS V2 olarak da bilinir) Aralık 2018'den beri TLS 1.2'yi desteklemektedir. Rooms aygıtlarında Microsoft Teams Rooms uygulaması 4.0.64.0 veya daha sonraki bir sürümün yüklü olmasını öneririz. Daha fazla bilgi için, aşağıdaki [Sürüm notlarına](/microsoftteams/room-systems/srs2-release-note) bakın. Değişiklikler geriye ve ileriye uyumludur.

Surface Hub, Mayıs 2019'da TLS 1.2 desteğini yayınladı.

Microsoft Teams Rooms ve Surface Hub ürünleri için TLS 1.2 desteği de aşağıdaki sunucu tarafı kod değişikliklerini gerektirir:

- Skype Kurumsal Çevrimiçi sunucu değişiklikleri Nisan 2019'da canlı olarak yapılmıştır. Artık Skype Kurumsal Çevrimiçi, TLS 1.2 kullanarak Microsoft Teams Rooms ve Surface Hub aygıtlarını bağlamayı destekliyor.
- Skype Kurumsal Sunucu müşterileri, Teams Rooms Systems ve Surface Hub için TLS 1.2'yi kullanmak için kümülatif bir güncelleştirme (CU) yüklemelidir.

  - Skype Kurumsal Sunucu 2015 için CU9, Mayıs 2019'da piyasaya sürüldü.
  - Skype for Kurumsal Sunucu 2019 için CU1 daha önce Nisan 2019 için planlanmıştı ancak Haziran 2019'a ertelendi.

  > [!NOTE]
  > Skype Kurumsal şirket içi müşterileri, Skype Kurumsal Sunucu için belirli CU'ları yüklemeden önce TLS 1.0/1.1'i devre dışı bırakmamalıdır.

Karma senaryolar veya Active Directory Federation Services için herhangi bir şirket içi altyapı kullanıyorsanız altyapının TLS 1.2 kullanan hem gelen hem de giden bağlantıları desteklediğinden emin olun.

## <a name="references"></a>Başvurular

Aşağıdaki kaynaklar, müşterilerinizin TLS 1.2 veya daha sonraki bir sürümü kullandığından emin olmak ve TLS 1.0 ve 1.1'i devre dışı bıraktırmaya yardımcı olmak için kılavuz sağlar.

- Office 365'e bağlanan Windows 7 istemcileri için TLS 1.2'nin Windows'da WinHTTP'deki varsayılan güvenli protokol olduğundan emin olun. Daha fazla bilgi için bkz: [KB 3140245 - Windows'da WinHTTP'de varsayılan güvenli protokol olarak TLS 1.1 ve TLS 1.2'yi etkinleştirmek için güncelleme.](https://support.microsoft.com/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in)
- [TT şifreleme paketleri tarafından desteklenen TLS Office 365](/microsoft-365/compliance/technical-reference-details-about-encryption#tls-cipher-suites-supported-by-office-365)
- TLS 1.0 ve 1.1 bağımlılıklarını kaldırarak zayıf TLS kullanımını düzenlemeye başlamak için [Microsoft'ta TLS 1.2 desteğine](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/20/tls-1-2-support-at-microsoft/) bakın.
- [Yeni IIS işlevi,](https://cloudblogs.microsoft.com/microsoftsecure/2017/09/07/new-iis-functionality-to-help-identify-weak-tls-usage/) [Windows Server 2012 R2](https://support.microsoft.com/help/4025335/windows-8-1-windows-server-2012-r2-update-kb4025335) ve [Windows Server 2016](https://support.microsoft.com/help/4025334/windows-10-update-kb4025334)'da zayıf güvenlik protokolleri kullanarak hizmete bağlanan istemcileri bulmayı kolaylaştırır.
- [TLS 1.0 sorununu çözme hakkında daha fazla bilgi edinebilirsiniz](https://www.microsoft.com/download/details.aspx?id=55266).
- Güvenlik yaklaşımımız hakkında genel bilgi için [Office 365 Güven Merkezi](https://www.microsoft.com/trustcenter/cloudservices/office365)'ne gidin.
- SMTP istemcileri tarafından kullanılan TLS sürümünü tanımlamak için Güvenlik ve Uyumluluk Merkezi'nde [SMTP Kimlik Doğrulaması istemcileri içgörü & bakın](../security/office-365-security/mfi-smtp-auth-clients-report.md).
- [TLS 1.0/1.1'i Kullanımdan Kaldırmaya Hazırlık - Office 365 Skype Kurumsal](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/ba-p/222247)
- [Exchange Server TLS kılavuzu, bölüm 1: TLS 1.2'ye Hazırlanıyor](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-1-getting-ready-for-tls-1-2/ba-p/607649)
- [Exchange Server TLS kılavuzu, Bölüm 2: TLS 1.2'yi Etkinleştirme ve Kullanmayan İstemcileri Belirleme](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-2-enabling-tls-1-2-and/ba-p/607761)
- [Exchange Server TLS kılavuzu, Bölüm 3: TLS 1.0/1.1'i kapatma](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-3-turning-off-tls-1-0-1-1/ba-p/607898)
- [Office Online Server'da TLS 1.1 ve TLS 1.2 desteğini etkinleştirme](/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server)
- [SharePoint 2013'te TLS ve SSL desteğini etkinleştirin](/sharepoint/security-for-sharepoint-server/enable-tls-and-ssl-support-in-sharepoint-2013)
- [SharePoint Server 2016'da TLS 1.1 ve TLS 1.2 desteğini etkinleştirin](/sharepoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016)
- [Etkin bir şekilde TLS 1.1 ve TLS 1.2 SharePoint Server 2019](/sharepoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2019)