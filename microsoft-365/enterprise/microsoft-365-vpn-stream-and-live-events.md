---
title: VPN ortamlarında Stream ve canlı etkinlikler için dikkat edilmesi gereken noktalar
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: VPN ortamlarında Stream ve canlı etkinlikler için dikkat edilmesi gereken noktalar
ms.openlocfilehash: eb2e57b844f06bc3b1e005aa1095794b176bba94
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63705262"
---
# <a name="special-considerations-for-stream-and-live-events-in-vpn-environments"></a>VPN ortamlarında Stream ve canlı etkinlikler için dikkat edilmesi gereken noktalar

>[!NOTE]
>Bu makale, uzak kullanıcılar için iyileştirmeyi Microsoft 365 makale kümelerinin bir bölümüdir.

>- Uzak kullanıcılar için Microsoft 365 bağlantısını en iyi duruma getirmek için VPN bölünmüş şifreleme kullanma hakkında genel bir bakış için bkz[.](microsoft-365-vpn-split-tunnel.md) Genel Bakış: Vpn bölünmüş Microsoft 365.
>- VPN bölünmüş bölmeyi uygulama hakkında ayrıntılı kılavuz için bkz. [VPN bölünmüş bölmeyi uygulama Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- VPN bölünmüş bölme senaryolarının ayrıntılı listesi için bkz. Daha fazla bilgi için bkz. Genel [VPN bölünmüş Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- VPN bölünmüş trafiğinde Teams trafiğinin güvenliğini sağlama kılavuzu için bkz. VPN bölünmüş trafiği için Teams trafiğinin güvenliğini [sağlama](microsoft-365-vpn-securing-teams.md).
>- Çin'deki kullanıcılar için Microsoft 365 kiracı performansını iyileştirme hakkında bilgi için bkz. [Microsoft 365 için performans iyileştirme.](microsoft-365-networking-china.md)

Microsoft 365 Canlı Etkinlikler trafiği (bu, Teams tarafından üretilen canlı etkinliklere katılanları ve Teams, Stream veya Yammer aracılığıyla dış kodlayıcıyla üretilenleri içerir) ve isteğe bağlı Stream trafiği şu anda hizmet için [URL/IP](urls-and-ip-address-ranges.md) listesinde Varsayılan yerine En İyi Duruma getirmek için kategorilere ayrılmıştır.  Bu uç noktalar, diğer hizmetler **tarafından** da kullanılmaktadır ve CDN'lerde barındırıldıkları için Varsayılan olarak kategorilere ayrılmıştır. Müşteriler genel olarak bu trafik türüne ara sunucu olmayı ve bunlar gibi uç noktalarda normalde yapılan güvenlik öğelerini uygulamayı tercih eder.

Birçok müşteri VPN altyapısı üzerinden yüksek hacimli ve gecikmeli trafiği yönlendirmek yerine kullanıcılarını doğrudan yerel İnternet bağlantılarından Stream/Live Events'e bağlamak için gereken URL/IP verilerini istedi. Normalde, hem ayrılmış ad alanları hem de uç noktalar için doğru IP bilgileri olmadan mümkün değildir ve varsayılan olarak kategorilere ayrılmış Microsoft 365 uç noktaları için **sağ değildir**.

Zorlamalı bir VPN kullanan istemcilerden Stream/Live Events hizmetine doğrudan bağlantı sağlamak için aşağıdaki adımları kullanın. Bu çözüm, müşterilere evden çalışma senaryolarından dolayı yüksek ağ trafiği varken CANLı Etkinlikler trafiğini VPN üzerinden yönlendirmeyi önleme seçeneği sağlamak üzere tasarlanmıştır. Mümkünse, hizmete denetimli bir proxy aracılığıyla erişmeniz önerilir.

>[!NOTE]
>Bu çözümün kullanımı, sağlanan IP adreslerine çözüm olmayan ve dolayısıyla VPN'den çapraz geçiş yapılan hizmet öğeleri olabilir, ancak akış verileri gibi yüksek hacimli trafiklerin toplu olması gerekir. Canlı Etkinlikler/Akış kapsamının dışında bu yüklemeyle karşılaşan başka öğeler de olabilir, ancak doğrudan gitmeden önce hem FQDN'ye hem de IP eşleşmesini karşılamaları gerektiği  için bunlar sınırlı olacaktır.

>[!IMPORTANT]
>Müşterilere Canlı Etkinlikler için performans artışı üzerinden VPN'i atlayan daha fazla trafik gönderme riskini değerlendirmeleri önerilir.

Canlı Etkinlikler ve Akış için zorunlu Teams özel durumu uygulamak için aşağıdaki adımlar uygulanmalıdır:

## <a name="1-configure-external-dns-resolution"></a>1. Dış DNS çözümlemelerini yapılandırma

İstemcilerin IP adreslerinde aşağıdaki ana bilgisayar adlarının çözümlensin diye harici, tekrarlayan DNS çözümlemesi kullanılabilir olması gerekir.

- \*.azureedge.net
- \*.media.azure.net
- \*.bmc.cdn.office.net

**\*.azureedge.net** Stream olayları için kullanılır (Microsoft Stream'de canlı akış için kodlayıcıları yapılandırma [- Microsoft Stream | Microsoft Docs](/stream/live-encoder-setup)).

**\*.media.azure.net** **ve\* .bmc.cdn.office.net**, Teams istemcisinde zamanlanan Teams tarafından üretilen Canlı Etkinlikler (Hızlı Başlangıç etkinlikleri, RTMP-In desteklenen etkinlikler [Yol Haritası Kimliği 84960]) için kullanılır.

 Bu uç noktaların bazıları Stream/Live Events dışındaki diğer öğelerle paylaşılır, VPN çözümünüzde (IP yerine FQDN'de çalışıyor olması gibi) teknik olarak mümkün olsa bile VPN yüklemesini yapılandırmak için yalnızca bu FQDN'leri kullanmak iyi değildir.

FQDN'ler VPN yapılandırmasında gerekli değildir, yalnızca ILGILI trafiği doğrudan göndermek üzere IP'lerle birlikte PAC dosyalarında kullanılabilir.

## <a name="2-implement-pac-file-changes-where-required"></a>2. PAC dosyası değişikliklerini uygulama (gerektiğinde)

VPN'deyken trafiği ara sunucu üzerinden yönlendiren PAC dosyası kullanan kuruluşlarda, bu normalde FQDN'ler kullanılarak elde edilir. Bununla birlikte, Stream/Live Events'de, **\*** sağlanan ana bilgisayar adları .azureedge.net gibi joker karakterler içerir ve bu aynı zamanda tam IP listeleri sağlamak mümkün olmayan diğer öğeleri de kapsar. Dolayısıyla, istek tek başına DNS joker karakteri eşleşmesine göre doğrudan gönderilirse, bu makalenin [sonraki 3](#3-configure-routing-on-the-vpn-to-enable-direct-egress) . Adımlarında isteğin doğrudan yolu üzerinden hiçbir yönlendirme yoksa bu uç noktalara giden trafik engellenir.

Bu sorunu çözmek için, aşağıdaki IP'leri sağlanmıştır ve 1. Adımda açıklandığı gibi örnek PAC dosyasında ana bilgisayar adlarla [birlikte kullanabiliriz](#1-configure-external-dns-resolution). PAC dosyası, URL'nin Stream/Live Events için kullanılanlarla eş olup eşleşmesi ve eş olup eşleşmesinin ardından, DNS aramalarından döndürülen IP'nin hizmet için sağlananlarla eş olup eşleşmesi için de kontrol yapar. Her _iki_ eşleşme de aynı olursa, trafik doğrudan yönlendirildi. Öğeden biri (FQDN/IP) eş eş olmuyorsa trafik ara sunucuya gönderilir. Sonuç olarak, yapılandırma hem IP hem de tanımlanmış ad alanlarının kapsamı dışında IP'ye çözüm olarak her şeyin VPN üzerinden proxy'den normalde çapraz geçiş yapmasını sağlar.

### <a name="gathering-the-current-lists-of-cdn-endpoints"></a>Uç Noktaların geçerli CDN toplama

Canlı Etkinlikler, en CDN, kalite ve güvenlik için müşterilere akış sağlamak için birden fazla kullanıcı sağlayıcısı kullanır. Şu anda hem Microsoft'Azure CDN hem de Verizon'dan gelen e-postaların her ikisi de kullanılır. Zamanla bu durum bölgesel kullanılabilirlik gibi durumlar nedeniyle değiştirilebilir. Bu makale, IP aralıklarında güncel bilgi alamama olanak sağlayan bir kaynaktır.

Microsoft'tan Azure CDN için listeyi Azure IP Aralıkları ve Hizmet Etiketlerini İndir [( Resmi Microsoft İndirme](https://www.microsoft.com/download/details.aspx?id=56519) Merkezi'nden Genel Bulut - JSON hizmet etiketi *AzureFrontdoor.Frontend* için özel olarak bakmanız gerekir; *addressPrefixes*, IPv4/IPv6 alt ağlarını gösterir. Zaman içinde IP'ler değişebilir, ancak hizmet etiket listesi her zaman kullanımdan önce güncelleştirilir.

Verizon (Edgecast) [https://docs.microsoft.com/rest/api/cdn/edge-nodes/list](/rest/api/cdn/edge-nodes/list) Azure CDN için kapsamlı bir liste bulmak için (Dene'ye **tıklayın) -** **Premium\_ Verizon** bölümüne özel olarak bakabilirsiniz. Bu API'nin tüm Edgecast IP'lerini (origin ve Anycast) gösterir. Şu anda API'nin kaynak ile Anycast arasındaki farkı ayırt etme mekanizması yok.

Bunu bir PAC dosyasında uygulamak için, FQDN aracılığıyla Microsoft 365 Trafiği doğrudan en iyi duruma getirme (önerilen en iyi yöntem) ve kritik Stream/Live Events trafiğini doğrudan FQDN ve döndürülen IP adresinin bir bileşimiyle gönderen aşağıdaki örneği kullanabilirsiniz. _Contoso_ yer tutucu adı, kiracınız adına göre düzenlenemez; burada _Contoso_ yer tutucu contoso.onmicrosoft.com

#### <a name="example-pac-file"></a>Örnek PAC dosyası

PAC dosyalarını oluşturma örneği:

1. Aşağıdaki betiği yerel sabit diske kaydedtik olarak _Get-TLEPacFile.ps1_.
1. [Verizon URL'sine](/rest/api/cdn/edge-nodes/list#code-try-0) gidin ve sonuçta elde edilen JSON'u indirin (bunu cdnedgenodes.json gibi bir dosyaya yapıştırın)
1. Dosyayı betikle aynı klasöre koyma.
1. PowerShell penceresinde aşağıdaki komutu çalıştırın. SPO URL'leri için kiracı adını başka bir adla değiştirebilirsiniz. Bu, Tür 2'dir, dolayısıyla **En İyi Duruma** **Getirme** ve İzin Ver (1 türü yalnızca En İyi Duruma Getirme'dir).

   ```powershell
   .\Get-TLEPacFile.ps1 -Instance Worldwide -Type 2 -TenantName <contoso> -CdnEdgeNodesFilePath .\cdnedgenodes.json -FilePath TLE.pac
   ```

5. TLE.pac dosyası tüm ad alanlarını ve IPv4/IPv6'ları içerir.

##### <a name="get-tlepacfileps1"></a>Get-TLEPacFile.ps1

```powershell
# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT License.

<#PSScriptInfo

.VERSION 1.0.4

.AUTHOR Microsoft Corporation

.GUID 7f692977-e76c-4582-97d5-9989850a2529

.COMPANYNAME Microsoft

.COPYRIGHT
Copyright (c) Microsoft Corporation. All rights reserved.
Licensed under the MIT License.

.TAGS PAC Microsoft Microsoft365 365

.LICENSEURI

.PROJECTURI http://aka.ms/ipurlws

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES

#>

<#

.SYNOPSIS

Create a PAC file for Microsoft 365 prioritized connectivity

.DESCRIPTION

This script will access updated information to create a PAC file to prioritize Microsoft 365 Urls for
better access to the service. This script will allow you to create different types of files depending
on how traffic needs to be prioritized.

.PARAMETER Instance

The service instance inside Microsoft 365.

.PARAMETER ClientRequestId

The client request id to connect to the web service to query up to date Urls.

.PARAMETER DirectProxySettings

The direct proxy settings for priority traffic.

.PARAMETER DefaultProxySettings

The default proxy settings for non priority traffic.

.PARAMETER Type

The type of prioritization to give. Valid values are 1 and 2, which are 2 different modes of operation.
Type 1 will send Optimize traffic to the direct route. Type 2 will send Optimize and Allow traffic to
the direct route.

.PARAMETER Lowercase

Flag this to include lowercase transformation into the PAC file for the host name matching.

.PARAMETER TenantName

The tenant name to replace wildcard Urls in the webservice.

.PARAMETER ServiceAreas

The service areas to filter endpoints by in the webservice.

.PARAMETER FilePath

The file to print the content to.

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -DefaultProxySettings "PROXY 4.4.4.4:70" -FilePath type1.pac

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -Instance China -Type 2 -DefaultProxySettings "PROXY 4.4.4.4:70" -FilePath type2.pac

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -Instance WorldWide -Lowercase -TenantName tenantName -ServiceAreas Sharepoint

#>

#Requires -Version 2

[CmdletBinding(SupportsShouldProcess=$True)]
Param (
    [Parameter(Mandatory = $false)]
    [ValidateSet('Worldwide', 'Germany', 'China', 'USGovDoD', 'USGovGCCHigh')]
    [String] $Instance = "Worldwide",

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [guid] $ClientRequestId = [Guid]::NewGuid().Guid,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [String] $DirectProxySettings = 'DIRECT',

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [String] $DefaultProxySettings = 'PROXY 10.10.10.10:8080',

    [Parameter(Mandatory = $false)]
    [ValidateRange(1, 2)]
    [int] $Type = 1,

    [Parameter(Mandatory = $false)]
    [switch] $Lowercase = $false,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $TenantName,

    [Parameter(Mandatory = $false)]
    [ValidateSet('Exchange', 'SharePoint', 'Common', 'Skype')]
    [string[]] $ServiceAreas,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $FilePath,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $CdnEdgeNodesFilePath
)

##################################################################################################################
### Global constants
##################################################################################################################

$baseServiceUrl = "https://endpoints.office.com/endpoints/$Instance/?ClientRequestId={$ClientRequestId}"
$directProxyVarName = "direct"
$defaultProxyVarName = "proxyServer"
$bl = "`r`n"

##################################################################################################################
### Functions to create PAC files
##################################################################################################################

function Get-PacClauses
{
    param(
        [Parameter(Mandatory = $false)]
        [string[]] $Urls,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $ReturnVarName
    )

    if (!$Urls)
    {
        return ""
    }

    $clauses =  (($Urls | ForEach-Object { "shExpMatch(host, `"$_`")" }) -Join "$bl        || ")

@"
    if($clauses)
    {
        return $ReturnVarName;
    }
"@
}

function Get-PacString
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [array[]] $MapVarUrls
    )

@"
// This PAC file will provide proxy config to Microsoft 365 services
//  using data from the public web service for all endpoints
function FindProxyForURL(url, host)
{
    var $directProxyVarName = "$DirectProxySettings";
    var $defaultProxyVarName = "$DefaultProxySettings";

$( if ($Lowercase) { "    host = host.toLowerCase();" })

$( ($MapVarUrls | ForEach-Object { Get-PACClauses -ReturnVarName $_.Item1 -Urls $_.Item2 }) -Join "$bl$bl" )

$( if (!$ServiceAreas -or $ServiceAreas.Contains('Skype')) { Get-TLEPacConfiguration })

    return $defaultProxyVarName;
}
"@ -replace "($bl){3,}","$bl$bl" # Collapse more than one blank line in the PAC file so it looks better.
}

##################################################################################################################
### Functions to get and filter endpoints
##################################################################################################################

function Get-TLEPacConfiguration {
    param ()
    $PreBlock = @"
    // Don't Proxy Teams Live Events traffic

    if(shExpMatch(host, "*.azureedge.net")
    || shExpMatch(host, "*.bmc.cdn.office.net")
    || shExpMatch(host, "*.media.azure.net"))
    {
        var resolved_ip = dnsResolveEx(host);

"@
    $TLESb = New-Object 'System.Text.StringBuilder'
    $TLESb.Append($PreBlock) | Out-Null

    if (![string]::IsNullOrEmpty($CdnEdgeNodesFilePath) -and (Test-Path -Path $CdnEdgeNodesFilePath)) {
        $CdnData = Get-Content -Path $CdnEdgeNodesFilePath -Raw -ErrorAction SilentlyContinue | ConvertFrom-Json | Select-Object -ExpandProperty value | 
            Where-Object { $_.name -eq 'Premium_Verizon'} | Select-Object -First 1 -ExpandProperty properties | 
            Select-Object -ExpandProperty ipAddressGroups
        $CdnData | Select-Object -ExpandProperty ipv4Addresses | ForEach-Object {
            if ($TLESb.Length -eq $PreBlock.Length) {
                $TLESb.Append("        if(") | Out-Null
            }
            else {
                $TLESb.AppendLine() | Out-Null
                $TLESb.Append("        || ") | Out-Null
            }
            $TLESb.Append("isInNetEx(resolved_ip, `"$($_.BaseIpAddress)/$($_.prefixLength)`")") | Out-Null
        }
        $CdnData | Select-Object -ExpandProperty ipv6Addresses | ForEach-Object {
            if ($TLESb.Length -eq $PreBlock.Length) {
                $TLESb.Append("        if(") | Out-Null
            }
            else {
                $TLESb.AppendLine() | Out-Null
                $TLESb.Append("        || ") | Out-Null
            }
            $TLESb.Append("isInNetEx(resolved_ip, `"$($_.BaseIpAddress)/$($_.prefixLength)`")") | Out-Null
        }
    }
    $AzureIPsUrl = Invoke-WebRequest -Uri "https://www.microsoft.com/en-us/download/confirmation.aspx?id=56519" -UseBasicParsing -ErrorAction SilentlyContinue  | 
            Select-Object -ExpandProperty Links | Select-Object -ExpandProperty href | 
            Where-Object { $_.EndsWith('.json') -and $_ -match 'ServiceTags' } | Select-Object -First 1
    if ($AzureIPsUrl) {
        Invoke-RestMethod -Uri $AzureIPsUrl -ErrorAction SilentlyContinue | Select-Object -ExpandProperty values | 
            Where-Object { $_.name -eq 'AzureFrontDoor.Frontend' } | Select-Object -First 1 -ExpandProperty properties |
            Select-Object -ExpandProperty addressPrefixes | ForEach-Object {
                if ($TLESb.Length -eq $PreBlock.Length) {
                    $TLESb.Append("        if(") | Out-Null
                }
                else {
                    $TLESb.AppendLine() | Out-Null
                    $TLESb.Append("        || ") | Out-Null
                }
                $TLESb.Append("isInNetEx(resolved_ip, `"$_`")") | Out-Null
            }
    }
    if ($TLESb.Length -gt $PreBlock.Length) {
        $TLESb.AppendLine(")") | Out-Null
        $TLESb.AppendLine("        {") | Out-Null
        $TLESb.AppendLine("            return $directProxyVarName;") | Out-Null
        $TLESb.AppendLine("        }") | Out-Null
    }
    else {
        $TLESb.AppendLine("        // no addresses found for service via script") | Out-Null
    }
    $TLESb.AppendLine("    }") | Out-Null
    return $TLESb.ToString()
}

function Get-Regex
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $Fqdn
    )

    return "^" + $Fqdn.Replace(".", "\.").Replace("*", ".*").Replace("?", ".?") + "$"
}

function Match-RegexList
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $ToMatch,

        [Parameter(Mandatory = $false)]
        [string[]] $MatchList
    )

    if (!$MatchList)
    {
        return $false
    }
    foreach ($regex in $MatchList)
    {
        if ($regex -ne $ToMatch -and $ToMatch -match (Get-Regex $regex))
        {
            return $true
        }
    }
    return $false
}

function Get-Endpoints
{
    $url = $baseServiceUrl
    if ($TenantName)
    {
        $url += "&TenantName=$TenantName"
    }
    if ($ServiceAreas)
    {
        $url += "&ServiceAreas=" + ($ServiceAreas -Join ",")
    }
    return Invoke-RestMethod -Uri $url
}

function Get-Urls
{
    param(
        [Parameter(Mandatory = $false)]
        [psobject[]] $Endpoints
    )

    if ($Endpoints)
    {
        return $Endpoints | Where-Object { $_.urls } | ForEach-Object { $_.urls } | Sort-Object -Unique
    }
    return @()
}

function Get-UrlVarTuple
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $VarName,

        [Parameter(Mandatory = $false)]
        [string[]] $Urls
    )
    return New-Object 'Tuple[string,string[]]'($VarName, $Urls)
}

function Get-MapVarUrls
{
    Write-Verbose "Retrieving all endpoints for instance $Instance from web service."
    $Endpoints = Get-Endpoints

    if ($Type -eq 1)
    {
        $directUrls = Get-Urls ($Endpoints | Where-Object { $_.category -eq "Optimize" })
        $nonDirectPriorityUrls = Get-Urls ($Endpoints | Where-Object { $_.category -ne "Optimize" }) | Where-Object { Match-RegexList $_ $directUrls }
        return @(
            Get-UrlVarTuple -VarName $defaultProxyVarName -Urls $nonDirectPriorityUrls
            Get-UrlVarTuple -VarName $directProxyVarName -Urls $directUrls
        )
    }
    elseif ($Type -eq 2)
    {
        $directUrls = Get-Urls ($Endpoints | Where-Object { $_.category -in @("Optimize", "Allow")})
        $nonDirectPriorityUrls = Get-Urls ($Endpoints | Where-Object { $_.category -notin @("Optimize", "Allow") }) | Where-Object { Match-RegexList $_ $directUrls }
        return @(
            Get-UrlVarTuple -VarName $defaultProxyVarName -Urls $nonDirectPriorityUrls
            Get-UrlVarTuple -VarName $directProxyVarName -Urls $directUrls
        )
    }
}

##################################################################################################################
### Main script
##################################################################################################################

$content = Get-PacString (Get-MapVarUrls)

if ($FilePath)
{
    $content | Out-File -FilePath $FilePath -Encoding ascii
}
else
{
    $content
}
```

Betik, **AzurefrontDoor.Frontend'ın** indirme [URL'sini](https://www.microsoft.com/download/details.aspx?id=56519) ve anahtarlarını temel alarak Azure listesini otomatik olarak ayrıştıracaktır, dolayısıyla onu el ile almak gerekmez.

Bir kez daha, yalnızca FQDN'leri kullanarak VPN yüklemesi gerçekleştirmeniz tavsiye edilir; hem FQDN'leri hem de işlevde IP adreslerini kullanmak, bu yüklemenin Canlı Etkinlikler/Akış da dahil sınırlı bir uç nokta kümesi için kullanımının kapsamının açıklarını sağlar. İşlevin yapılandırılmış olması, FQDN'ler için, istemci tarafından doğrudan listelenenlerle eşleşen bir DNS araması yapılmasına, yani kalan ad alanlarının DNS çözümlemesi değişmeden kalır.

Canlı Etkinlikler ve Akışla ilgili uç noktaların yükleme riskini sınırlamak isterseniz, **\*bu** riskin büyük bir çoğunun bulunduğu yapılandırmadan .azureedge.net etki alanını kaldırabilirsiniz çünkü bu, tüm Azure CDN müşterileri için kullanılan paylaşılan bir etki alanıdır. Bunun dezavantajı, dış kodlayıcı kullanan her olayın en iyi duruma tabi olmayacak olmasıdır, ancak bu kod içinde üretilen/düzenlenen Teams olur.

## <a name="3-configure-routing-on-the-vpn-to-enable-direct-egress"></a>3. Doğrudan çıkışı etkinleştirmek için VPN'de yönlendirmeyi yapılandırma

Son adım, trafiğin VPN'ye zorunlu geçiş yoluyla gönderilmeyeceğiden emin olmak için **geçerli CDN** Uç Noktaları listelerini VPN yapılandırmasına toplama konusunda açıklanan Canlı Etkinlik IP'leri için doğrudan bir yönlendirme eklemektir. Daha fazla bilgi için bunun nasıl Microsoft 365 en iyi duruma getirme uç noktalarını, [MICROSOFT 365 için VPN](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling) bölünmüş bölmeyi uygulama bölümünde [bulabilirsiniz](microsoft-365-vpn-implement-split-tunnel.md). Bu belgede listelenen Stream/Live Events IP'leri için bu işlem tamamen aynıdır.

VPN yapılandırması için yalnızca IP'ler (FQDN'ler değil) CDN Uç [noktaları](#gathering-the-current-lists-of-cdn-endpoints) toplama bağlantısında kullanılacaktır.

## <a name="faq"></a>SSS

### <a name="will-this-send-all-my-traffic-to-the-service-direct"></a>Bu tüm trafiğimi doğrudan hizmete gönderecek mi?

Hayır, bu işlem Canlı Etkinlik veya Video akışı için gecikmeye duyarlı akış trafiğini doğrudan gönderir, diğer tüm trafik yayımlanmış IP'lere çözüm vermezse VPN bağlantısını kullanmaya devam eder.

### <a name="do-i-need-to-use-the-ipv6-addresses"></a>IPv6 Adreslerini kullanmam gerekir mi?

Hayır, bağlantı yalnızca gerekli olduğu zaman IPv4 olabilir.

### <a name="why-are-these-ips-not-published-in-the-microsoft-365-urlip-service"></a>Bu IP'ler neden URL/IP Microsoft 365 yayımlanmaz?

Microsoft'un, müşterilerin uç nokta kategorisine göre güvenli ve en iyi yönlendirmeyi uygulamak için bilgileri güvenilir bir şekilde kullanamalarını sağlamak için hizmette yer alan bilgilerin biçimi ve türüyle ilgili sıkı denetimler vardır.

Varsayılan **uç** nokta kategorisinin çeşitli nedenlerle sağlanan IP bilgileri yoktur (Varsayılan uç noktalar Microsoft'un denetimi dışında olabilir, çok sık değişebilir veya diğer öğelerle paylaşılan bloklar içinde olabilir). Bu nedenle, Varsayılan uç noktalar normal web trafiği gibi denetimli bir ara sunucuya FQDN yoluyla gönderilmek üzere tasarlanmıştır.

Bu durumda, yukarıdaki uç noktalar Canlı Etkinlikler veya Akış dışında Microsoft tarafından denetlenen olmayan öğeler tarafından kullanılmaktadır ve dolayısıyla trafik doğrudan gönderilmesi, bu IP'lere çözüm olan başka her şeyi de istemciden gönderme anlamına da gelecektir. Microsoft, küresel krizin benzersiz doğası gereği ve müşterilerimizin kısa vadeli  ihtiyaçlarını karşılamak için yukarıdaki bilgileri, müşterilerin uygun olduğunu göre kullanmaları için sağlanmıştır.

Microsoft, Live Events uç noktalarını gelecekte uç nokta kategorilerine dahil etmelerine izin verecek şekilde yeniden yapılandırmak için çalışıyor.

### <a name="do-i-only-need-to-allow-access-to-these-ips"></a>Yalnızca bu IP'lere erişim izni vermem gerekir mi?

Hayır, HIZMETIN çalışması için URL/IP hizmetinin Gerekli olarak işaretlenmiş [uç noktalarına](urls-and-ip-address-ranges.md) erişim çok önemlidir. Ayrıca, Stream için işaretlenmiş isteğe bağlı uç noktalar (ID 41-45) gereklidir.

### <a name="what-scenarios-will-this-advice-cover"></a>Bu öneri hangi senaryoları kapsıyor?

1. Teams Uygulaması'nın içinde üretilen canlı Teams.
2. Stream'de barındırılan içeriği görüntüleme
3. Dış cihaz (kodlayıcı) tarafından üretilen etkinlikler

### <a name="does-this-advice-cover-presenter-traffic"></a>Bu öneri sunucu trafiğini kapsıyor mu?

Bu, yukarıda belirtilen tavsiyenin yalnızca hizmeti tüketenler için olduğunu ifade ederiz. Teams'den sunum yapmak, sunucu trafiğinin URL/IP hizmeti satır 11'de listelenen URL/IP hizmeti satır 11'de işaretlenmiş UDP uç noktalarını en iyi duruma getirme bölümüne akdığını ve [Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md) için VPN bölünmüş bölme uygulama bölümünde açıklanan ayrıntılı [VPN](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling) yükleme önerilerini gösterir.

### <a name="does-this-configuration-risk-traffic-other-than-live-events-amp-stream-being-sent-direct"></a>Bu yapılandırmada Canlı Etkinlikler Akışı dışında bir trafiğin doğrudan &amp; gönderilme riski var mı?

Evet, hizmetin bazı öğeleri için kullanılan paylaşılan FQDN'lerden dolayı bu kaçınılmazdır. Bu trafik genelde inceleme uygulayabilecek bir şirket ara sunucusu aracılığıyla gönderilir. VPN bölme senaryosunda, hem FQDN'ler hem de IP'ler kullanılarak bu risk en düşük kapsamda olacak, ancak yine de mevcut olacaktır. Müşteriler yükleme yapılandırmasından .azureedge.net etki alanını kaldırabilir ve bu riski minimum düzeyde azaltabilirsiniz ancak bu, Stream tarafından desteklenen Canlı Etkinlikler 'in (Teams zamanlanmış, dış kodlayıcı olayları, Teams Yammer zamanlanmış dış kodlayıcı olaylarında üretilen Yammer olayları ve Stream'den zamanlanmış veya isteğe bağlı olarak görüntüleme) yüklemesini kaldırır.**\*** Bu şekilde zamanlanan ve Teams etkinlikler etkilenmez.

## <a name="related-articles"></a>İlgili makaleler

[Genel bakış: VPN bölme bölme Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[VPN bölmeli bölme Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Kullanıcılar için yaygın VPN bölme bölme Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[VPN bölünmüş tüneli için Teams medya trafiğinin güvenliğini sağlama](microsoft-365-vpn-securing-teams.md)

[Microsoft 365 kullanıcıları için performans iyileştirmeyi iyileştirme](microsoft-365-networking-china.md)

[Microsoft 365 Ağ Bağlantısı İlkeleri](microsoft-365-network-connectivity-principles.md)

[Microsoft 365 ağ bağlantısını değerlendirme](assessing-network-connectivity.md)

[Microsoft 365 ve performans ayarını yapılandırma](network-planning-and-performance.md)

[Günümüzün benzersiz uzaktan çalışma senaryolarında güvenlik uzmanlarının ve BT'nin modern güvenlik denetimlerini elde etmenin alternatif yolları (Microsoft Güvenlik Ekibi blogu)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Microsoft'ta VPN performansını geliştirme: otomatik Windows 10 izin vermek için VPN profillerini kullanma](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[VPN ile çalışma: Microsoft uzaktan iş gücüne nasıl bağlı tutarak](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Microsoft genel ağı](/azure/networking/microsoft-global-network)
