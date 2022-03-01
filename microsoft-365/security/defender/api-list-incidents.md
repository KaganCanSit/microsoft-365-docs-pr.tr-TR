---
title: Microsoft 365 Defender'te olay API'sini Microsoft 365 Defender
description: Microsoft 365 Defender'de olay API'lerini Microsoft 365 Defender
keywords: liste, olay, olay, api
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 03fbcb70588158919b54c9153b5d8d32d416cc75
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63014204"
---
# <a name="list-incidents-api-in-microsoft-365-defender"></a>Microsoft 365 Defender'te olay API'sini Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> Bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabilir, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

## <a name="api-description"></a>API açıklaması

Liste olayları API'si, bilinçli bir siber güvenlik yanıtı oluşturmak için olayları sıralamanızı sağlar. Ağ bağlantınıza bayrakla işaretlenmiş bir olay koleksiyonunu, ortam bekletme ilkesinde belirttiğiniz zaman aralığında sunar. En son olaylar listenin en üstünde görüntülenir. Her olay, ilgili uyarılar ve bunların ilgili varlıklarını içeren bir dizi içerir.

API, aşağıdaki **OData işleçlerini** destekler:

- `$filter``lastUpdateTime`üzerinde , `createdTime`, ve `status`özelliklerde `assignedTo`
- `$top`maksimum değeri **100 olan**
- `$skip`

## <a name="limitations"></a>Sınırlamalar

1. En fazla sayfa boyutu **100 olaydır**.
2. En fazla, dakikada **50 çağrı ve saatte** **1500 çağrı olabilir**.

## <a name="permissions"></a>İzinler

Bu API'yi çağrı yapmak için aşağıdaki izinlerden biri gerekir. İzinleri seçme de dahil olmak üzere daha fazla bilgi edinmek için bkz. [Microsoft 365 Defender API'lere erişme](api-access.md)

İzin türü|İzin|İzin görünen adı
---|---|---
Uygulama|Olay.Okuma.All|Tüm olayları okuma
Uygulama|Incident.ReadWrite.All|Tüm olayları okuma ve yazma
Temsilcili (iş veya okul hesabı)|Olay.Okuma|Olayları okuma
Temsilcili (iş veya okul hesabı)|Olay.Okuma|Olayları okuma ve yazma

> [!NOTE]
> Kullanıcı kimlik bilgilerini kullanarak belirteç elde edilirken:
>
> - Kullanıcının portalda olayları görüntüleme izni olması gerekir.
> - Yanıt yalnızca kullanıcının açık olduğu olayları içerir.

## <a name="http-request"></a>HTTP isteği

```HTTP
GET /api/incidents
```

## <a name="request-headers"></a>Üstbilgi isteği

Name|Tür|Açıklama
---|---|---
Yetkilendirme|Dize|Taşıyıcı {token}. **Gerekli**

## <a name="request-body"></a>İstek gövdesi

Yok.

## <a name="response"></a>Yanıt

Başarılı olursa, bu yöntem yanıt `200 OK`gövdesinde ['i ve olay](api-incident.md) listesini döndürür.

## <a name="schema-mapping"></a>Şema eşlemesi

### <a name="incident-metadata"></a>Olay meta verileri

Alan adı|Açıklama|Örnek değer
---|---|---
olaykimlikkim|Olayı temsil eden benzersiz tanımlayıcı|924565
redirectIncidentId|Yalnızca bir olayın başka bir olayla birlikte grup olması durumunda, olay işleme mantığının bir parçası olarak doldurulur.|924569
incidentName|Her olay için kullanılabilir dize değeri.|Fidye yazılımı etkinliği
createdTime|Olayın ilk oluşturulma zamanı.|2020-09-06T14:46:57.0733333Z
lastUpdateTime|Olayın en son arka uçta güncelleştiril olduğu zaman. <p> Bu alan, olayları alma aralığı için istek parametresini ayarlarken kullanılabilir.|2020-09-06T14:46:57.29Z
atanan|Olayın sahibi veya *sahip atanmamışsa null* .|secop2@contoso.com
sınıflandırma|Olayın belirtimi. Özellik değerleri şöyledir: *Bilinmiyor*, *YanlışPositive*, *DoğruPositive*|Unknown
karartma|Olayın belirlenmesini belirtir. Özellik değerleri: *NotAvailable*, *Apt*, *Malware*, *SecurityPersonnel*, *SecurityTesting*, *UnwantedSoftware*, *Other*|NotAvailable
algılamaKaynağı|Algılama kaynağını belirtir.|Bulut Uygulamaları için Defender
durum|Olayları kategorilere ayır ( *Etkin* veya Çözümlendi *olarak*). Olaylara yanıtlarınızı düzenlemenize ve yönetmenize yardımcı olabilir.|Etkin
önem derecesi|Varlıklar üzerindeki olası etkiyi gösterir. Önem derecesi ne kadar yüksek ise etki o kadar büyük olur. Normalde daha yüksek önem düzeyi olan öğeler en acil dikkat gerektirir. <p> Aşağıdaki değerlerden biri: *Bilgilendirme*, *Düşük*, *Orta ve *Yüksek*.|Orta
etiketler|Bir olayla ilişkilendirilmiş özel etiketler dizisi; örneğin, bir olay grubunu ortak bir özel gruba bayrakla bayrak eklemek için.|\[\]
açıklamalar|Olayı yönetmekle ilgili özetler tarafından oluşturulan açıklamalar dizisi; örneğin sınıflandırma seçimi hakkında ek bilgiler.|\[\]
uyarılar|Olayla ilgili tüm uyarıların yanı sıra önem derecesi, uyarıya katılan varlıklar ve uyarıların kaynağı gibi diğer bilgileri içeren dizi.|\[\] (aşağıdaki uyarı alanlarındaki ayrıntılara bakın)

### <a name="alerts-metadata"></a>Uyarılar meta verileri

Alan adı|Açıklama|Örnek değer
---|---|---
alertId|Uyarıyı temsil eden benzersiz tanımlayıcı|caD70CFEE2-1F54-32DB-9988-3A868A1EBFAC
olaykimlikkim|Bu uyarının ilişkilendiril olduğu olayı temsil eden benzersiz tanımlayıcı|924565
serviceSource|Uyarının kaynaklandığı hizmet (Uç Nokta için Microsoft Defender, Bulut Uygulamaları için Microsoft Defender, Kimlik için Microsoft Defender veya Kimlik için Microsoft Defender gibi) Office 365.|MicrosoftCloudAppSecurity
creationTime|Uyarının ilk oluşturulma zamanı.|2020-09-06T14:46:55.7182276Z
lastUpdatedTime|Uyarının en son arka uçta güncelleştirilmiş olduğu saat.|2020-09-06T14:46:57.2433333Z
resolvedTime|Uyarının çözümlenmezse olduğu zaman.|2020-09-10T05:22:59Z
firstActivity|Uyarının ilk kez arka uçta etkinliğin güncelleştirilmiş olduğunu bildirmiş olduğu saat.|2020-09-04T05:22:59Z
başlık|Her uyarı için kullanılabilen kısa tanımlayıcı dize değeri.|Fidye yazılımı etkinliği
açıklama|Her uyarıyı açıklayan dize değeri.|Kullanıcı Test Kullanıcı2 (testUser2@contoso.com) *herunterladen* seyrek karşılaşılan uzantıyla biten birden çok uzantılı 99 dosya üzerinde değişiklik yaptı. Bu, olağandışı bir dosya işlemesi sayısıdır ve olası bir fidye yazılımı saldırısına işaret ediyor.
kategori|Kill zinciri boyunca saldırının ne kadar ilerlemiştine görsel ve sayısal bir bakış. [MITRE ATT ve CK&hizalanır™](https://attack.mitre.org/).|Etki
durum|Uyarıları kategorilere ayır ( *Yeni*, *Etkin veya* Çözümlendi *olarak*). Uyarılar için yanıtlarınızı düzenlemenize ve yönetmenize yardımcı olabilir.|Yeni
önem derecesi|Varlıklar üzerindeki olası etkiyi gösterir. Önem derecesi ne kadar yüksek ise etki o kadar büyük olur. Normalde daha yüksek önem düzeyi olan öğeler en acil dikkat gerektirir.<br>Aşağıdaki değerlerden biri: *Bilgilendirme*, *Düşük*, *Orta* ve *Yüksek*.|Orta
investigationId|Bu uyarı tarafından tetiklenen otomatik araştırma kimliği.|1234
investigationState|Araştırmanın geçerli durumu hakkında bilgiler. Aşağıdaki değerlerden *biri: Bilinmiyor**,* Sonlandırıldı, *Başarıyla Gönderildi*, *Atlandı**,* *KısmenRemedi**, Çalışıyor*, *PendingApproval*, *PendingResource*, *PartialLyInvestigated*, *TerminatedByUser*, *TerminatedBySystem*, *Queued*, *InnerFailure*, *PreexistingAlert*, *UnsupportedOs*, *UnsupportedAlertType*, *SuppressedAlert.*|UnsupportedAlertType
sınıflandırma|Olayın belirtimi. Özellik değerleri *şöyledir: Bilinmiyor*, *YanlışPositive*, *TruePositive* veya *null*|Unknown
karartma|Olayın belirlenmesini belirtir. Özellik değerleri: *NotAvailable*, *Apt*, *Malware*, *SecurityPersonnel*, *SecurityTesting*, *UnwantedSoftware*, *Other* veya  *null*|Apt
atanan|Olayın sahibi veya *sahip atanmamışsa null* .|secop2@contoso.com
actorName|Varsa, bu uyarıyla ilişkilendirilmiş etkinlik grubu.|BORON
threatFamilyName|Bu uyarıyla ilişkilendirilmiş tehdit ailesi.|null
mitreTechniques|[MITRE ATT ve CK framework ile&saldırı teknikleri](https://attack.mitre.org/)™.|\[\]
cihazlar|Olayla ilgili uyarıların gönderildiği tüm cihazlar.|\[\] (aşağıdaki varlık alanlarına ilişkin ayrıntılara bakın)

### <a name="device-format"></a>Cihaz biçimi

Alan adı|Açıklama|Örnek değer
---|---|---
DeviceId|Cihaz kimliği, Uç Nokta için Microsoft Defender'da belirlendi.|24c222b0b60fe148eeece49ac83910cc6a7ef491
aadDeviceId|Cihaz kimliği, Mobil [Cihaz Azure Active Directory.](/azure/active-directory/fundamentals/active-directory-whatis) Yalnızca etki alanına katılmış cihazlar için kullanılabilir.|null
deviceDnsName|Cihaz için tam etki alanı adı.|user5cx.middleeast.corp.contoso.com
osPlatform|Cihazın çalıştır olduğu işletim sistemi platformu.|WindowsServer2016
osBuild|Cihazın çalıştır olduğu işletim sistemi derleme sürümü.|14393
rbacGroupName|[Cihazla ilişkili rol tabanlı erişim](/azure/role-based-access-control/overview) denetimi (RBAC) grubu.|WDATP-Ring0
firstSeen|Cihazın ilk görülme zamanı.|2020-02-06T14:16:01.9330135Z
healthStatus|Cihazın durumu.|Etkin
riskScore|Cihazın risk puanı.|Yüksek
varlıklar|Verilen uyarının bir parçası veya ilgili olduğu belirlenen tüm varlıklar.|\[\] (aşağıdaki varlık alanlarına ilişkin ayrıntılara bakın)

### <a name="entity-format"></a>Varlık Biçimi

Alan adı|Açıklama|Örnek değer
---|---|---
entityType|Verilen uyarının bir parçası veya ilgili olduğu belirlenen varlıklar.<br>Özellikler değerleri şöyledir: *Kullanıcı*, *Ip*, *Url*, *Dosya*, *İşlem*, *Posta Kutusu*, *MailMessage*, *MailCluster*, *Registry*|Kullanıcı
sha1|EntityType Dosya ise *kullanılabilir*.<br>Dosya veya işlemle ilişkilendirilmiş uyarılar için dosya karması.|5de839186691aa96ee2ca6d74f0a38fb8d1bd6dd
sha256|EntityType Dosya ise *kullanılabilir*.<br>Dosya veya işlemle ilişkilendirilmiş uyarılar için dosya karması.|28cb017dfc99073aa1b47c1b30f413e3ce774c4991eb4158de50f9dbb36d8043
dosyaAdı|EntityType Dosya ise *kullanılabilir*.<br>Dosya veya işlemle ilişkilendirilmiş uyarılar için dosya adı|Detector.UnitTests.dll
filePath|EntityType Dosya ise *kullanılabilir*.<br>Dosya veya işlemle ilişkilendirilmiş uyarılar için dosya yolu|C:\\\agent_work_temp\Deploy\SYSTEM\2020-09-06 12_14_54\Out
processId|EntityType Süreç ise *kullanılabilir*.|24348
processCommandLine|EntityType Süreç ise *kullanılabilir*.|"Dosyanız İndirmeye Hazır\_ "1911150169.exe
processCreationTime|EntityType Süreç ise *kullanılabilir*.|2020-07-18T03:25:38.5269993Z
parentProcessId|EntityType Süreç ise *kullanılabilir*.|16840
parentProcessCreationTime|EntityType Süreç ise *kullanılabilir*.|2020-07-18T02:12:32.8616797Z
ipAddress|EntityType *Ip ise kullanılabilir*. <br>Kötü amaçlı bir ağ hedefine İletişim gibi ağ olaylarıyla *ilişkilendirilmiş uyarılar için IP adresi*.|62.216.203.204
url|EntityType *Url ise kullanılabilir*. <br>Kötü amaçlı bir ağ hedefine iletişim gibi ağ *olaylarıyla ilişkili uyarıların Url'si*.|down.esales360.cn
accountName|EntityType Kullanıcı ise *kullanılabilir*.|testUser2
domainName|EntityType Kullanıcı ise *kullanılabilir*.|europe.corp.contoso
userSid|EntityType Kullanıcı ise *kullanılabilir*.|S-1-5-21-1721254763-462695806-1538882281-4156657
aadUserId|EntityType Kullanıcı ise *kullanılabilir*.|fc8f7484-f813-4db2-afab-bc1507913fb6
userPrincipalName|EntityType /*UserMailBoxMailMessage*/ *ise kullanılabilir*.|testUser2@contoso.com
mailboxDisplayName|EntityType *MailBox ise kullanılabilir*.|test Kullanıcı2
mailboxAddress|EntityType /*UserMailBoxMailMessage*/ *ise kullanılabilir*.|testUser2@contoso.com
clusterBy|EntityType  *MailCluster ise kullanılabilir*.|Konu; P2SenderDomain; ContentType
gönderen|EntityType /*UserMailBoxMailMessage*/ *ise kullanılabilir*.|user.abc@mail.contoso.co.in
alıcı|EntityType *MailMessage ise kullanılabilir*.|testUser2@contoso.com
Konu|EntityType *MailMessage ise kullanılabilir*.|\[DıŞ\] Dikkat
deliveryAction|EntityType *MailMessage ise kullanılabilir*.|Teslim edildi
securityGroupId|EntityType  *SecurityGroup ise kullanılabilir*.|301c47c8-e15f-4059-ab09-e2ba9ffd372b
securityGroupName|EntityType  *SecurityGroup ise kullanılabilir*.|Ağ Yapılandırma İşleçleri
registryHive|EntityType Kayıt Defteri ise  *kullanılabilir*.|HKEYLOCALMACHINE\_\_|
registryKey|EntityType Kayıt Defteri ise  *kullanılabilir*.|SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon
registryValueType|EntityType Kayıt Defteri ise  *kullanılabilir*.|Dize
registryValue|EntityType Kayıt Defteri ise  *kullanılabilir*.|31-00-00-00
deviceId|Varsa, varlıkla ilgili cihazın kimliği.|986e5df8b73dacd43c8917d17e523e76b13c75cd

## <a name="example"></a>Örnek

### <a name="request-example"></a>İstek örneği

```HTTP
GET https://api.security.microsoft.com/api/incidents
```

### <a name="response-example"></a>Yanıt örneği

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#Incidents",
    "value": [
            {
            "incidentId": 924565,
            "redirectIncidentId": null,
            "incidentName": "Ransomware activity",
            "createdTime": "2020-09-06T14:46:57.0733333Z",
            "lastUpdateTime": "2020-09-06T14:46:57.29Z",
            "assignedTo": null,
            "classification": "Unknown",
            "determination": "NotAvailable",
            "status": "Active",
            "severity": "Medium",
            "tags": [],
            "comments": [
                {
                    "comment": "test comment for docs",
                    "createdBy": "secop123@contoso.com",
                    "createdTime": "2021-01-26T01:00:37.8404534Z"
                }
            ],
            "alerts": [
                {
                    "alertId": "caD70CFEE2-1F54-32DB-9988-3A868A1EBFAC",
                    "incidentId": 924565,
                    "serviceSource": "MicrosoftCloudAppSecurity",
                    "creationTime": "2020-09-06T14:46:55.7182276Z",
                    "lastUpdatedTime": "2020-09-06T14:46:57.2433333Z",
                    "resolvedTime": null,
                    "firstActivity": "2020-09-04T05:22:59Z",
                    "lastActivity": "2020-09-04T05:22:59Z",
                    "title": "Ransomware activity",
                    "description": "The user Test User2 (testUser2@contoso.com) manipulated 99 files with multiple extensions ending with the uncommon extension herunterladen. This is an unusual number of file manipulations and is indicative of a potential ransomware attack.",
                    "category": "Impact",
                    "status": "New",
                    "severity": "Medium",
                    "investigationId": null,
                    "investigationState": "UnsupportedAlertType",
                    "classification": null,
                    "determination": null,
                    "detectionSource": "MCAS",
                    "assignedTo": null,
                    "actorName": null,
                    "threatFamilyName": null,
                    "mitreTechniques": [],
                    "devices": [],
                    "entities": [
                        {
                            "entityType": "User",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": "testUser2",
                            "domainName": "europe.corp.contoso",
                            "userSid": "S-1-5-21-1721254763-462695806-1538882281-4156657",
                            "aadUserId": "fc8f7484-f813-4db2-afab-bc1507913fb6",
                            "userPrincipalName": "testUser2@contoso.com",
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "Ip",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": "62.216.203.204",
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        }
                    ]
                }
            ]
        },
        {
            "incidentId": 924521,
            "redirectIncidentId": null,
            "incidentName": "'Mimikatz' hacktool was detected on one endpoint",
            "createdTime": "2020-09-06T12:18:03.6266667Z",
            "lastUpdateTime": "2020-09-06T12:18:03.81Z",
            "assignedTo": null,
            "classification": "Unknown",
            "determination": "NotAvailable",
            "status": "Active",
            "severity": "Low",
            "tags": [],
            "comments": [],
            "alerts": [
                {
                    "alertId": "da637349914833441527_393341063",
                    "incidentId": 924521,
                    "serviceSource": "MicrosoftDefenderATP",
                    "creationTime": "2020-09-06T12:18:03.3285366Z",
                    "lastUpdatedTime": "2020-09-06T12:18:04.2566667Z",
                    "resolvedTime": null,
                    "firstActivity": "2020-09-06T12:15:07.7272048Z",
                    "lastActivity": "2020-09-06T12:15:07.7272048Z",
                    "title": "'Mimikatz' hacktool was detected",
                    "description": "Readily available tools, such as hacking programs, can be used by unauthorized individuals to spy on users. When used by attackers, these tools are often installed without authorization and used to compromise targeted machines.\n\nThese tools are often used to collect personal information from browser records, record key presses, access email and instant messages, record voice and video conversations, and take screenshots.\n\nThis detection might indicate that Windows Defender Antivirus has stopped the tool from being installed and used effectively. However, it is prudent to check the machine for the files and processes associated with the detected tool.",
                    "category": "Malware",
                    "status": "New",
                    "severity": "Low",
                    "investigationId": null,
                    "investigationState": "UnsupportedOs",
                    "classification": null,
                    "determination": null,
                    "detectionSource": "WindowsDefenderAv",
                    "assignedTo": null,
                    "actorName": null,
                    "threatFamilyName": "Mimikatz",
                    "mitreTechniques": [],
                    "devices": [
                        {
                            "mdatpDeviceId": "24c222b0b60fe148eeece49ac83910cc6a7ef491",
                            "aadDeviceId": null,
                            "deviceDnsName": "user5cx.middleeast.corp.contoso.com",
                            "osPlatform": "WindowsServer2016",
                            "version": "1607",
                            "osProcessor": "x64",
                            "osBuild": 14393,
                            "healthStatus": "Active",
                            "riskScore": "High",
                            "rbacGroupName": "WDATP-Ring0",
                            "rbacGroupId": 9,
                            "firstSeen": "2020-02-06T14:16:01.9330135Z"
                        }
                    ],
                    "entities": [
                        {
                            "entityType": "File",
                            "sha1": "5de839186691aa96ee2ca6d74f0a38fb8d1bd6dd",
                            "sha256": null,
                            "fileName": "Detector.UnitTests.dll",
                            "filePath": "C:\\Agent\\_work\\_temp\\Deploy_SYSTEM 2020-09-06 12_14_54\\Out",
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": "24c222b0b60fe148eeece49ac83910cc6a7ef491"
                        }
                    ]
                }
            ]
        },
        {
            "incidentId": 924518,
            "redirectIncidentId": null,
            "incidentName": "Email reported by user as malware or phish",
            "createdTime": "2020-09-06T12:07:55.1366667Z",
            "lastUpdateTime": "2020-09-06T12:07:55.32Z",
            "assignedTo": null,
            "classification": "Unknown",
            "determination": "NotAvailable",
            "status": "Active",
            "severity": "Informational",
            "tags": [],
            "comments": [],
            "alerts": [
                {
                    "alertId": "faf8edc936-85f8-a603-b800-08d8525cf099",
                    "incidentId": 924518,
                    "serviceSource": "OfficeATP",
                    "creationTime": "2020-09-06T12:07:54.3716642Z",
                    "lastUpdatedTime": "2020-09-06T12:37:40.88Z",
                    "resolvedTime": null,
                    "firstActivity": "2020-09-06T12:04:00Z",
                    "lastActivity": "2020-09-06T12:04:00Z",
                    "title": "Email reported by user as malware or phish",
                    "description": "This alert is triggered when any email message is reported as malware or phish by users -V1.0.0.2",
                    "category": "InitialAccess",
                    "status": "InProgress",
                    "severity": "Informational",
                    "investigationId": null,
                    "investigationState": "Queued",
                    "classification": null,
                    "determination": null,
                    "detectionSource": "OfficeATP",
                    "assignedTo": "Automation",
                    "actorName": null,
                    "threatFamilyName": null,
                    "mitreTechniques": [],
                    "devices": [],
                    "entities": [
                        {
                            "entityType": "MailBox",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": "testUser3@contoso.com",
                            "mailboxDisplayName": "test User3",
                            "mailboxAddress": "testUser3@contoso.com",
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailBox",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": "testUser4@contoso.com",
                            "mailboxDisplayName": "test User4",
                            "mailboxAddress": "test.User4@contoso.com",
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailMessage",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": "test.User4@contoso.com",
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": "user.abc@mail.contoso.co.in",
                            "recipient": "test.User4@contoso.com",
                            "subject": "[EXTERNAL] Attention",
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "Subject;P2SenderDomain;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "Subject;SenderIp;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "BodyFingerprintBin1;P2SenderDomain;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "BodyFingerprintBin1;SenderIp;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "Ip",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": "49.50.81.121",
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        }
                    ]
                }
            ]
        },
        ...
    ]
}
```

## <a name="related-articles"></a>İlgili makaleler

- [Api'lere Microsoft 365 Defender erişme](api-access.md)
- [API sınırları ve lisanslama hakkında bilgi edinin](api-terms.md)
- [Hata kodlarını anlama](api-error-codes.md)
- [Olaylara genel bakış](incidents-overview.md)
- [Olay API'leri](api-incident.md)
- [Olay API'sini güncelleştir](api-update-incidents.md)
