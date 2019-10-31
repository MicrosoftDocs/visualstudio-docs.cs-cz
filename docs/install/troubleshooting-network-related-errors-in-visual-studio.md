---
title: Řešení chyb sítě nebo proxy serveru
description: Vyhledá řešení chyb souvisejících se sítí nebo proxy serverem, se kterými se můžete setkat při instalaci nebo používání sady Visual Studio za bránou firewall nebo proxy server.
ms.date: 10/29/2019
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fbdacb265d39c9aff96fed37c69c684aa3f8503b
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189462"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>Řešení chyb souvisejících se sítí při instalaci nebo používání sady Visual Studio

Máme řešení pro nejčastější chyby související se sítí nebo proxy serverem, se kterými se můžete setkat při instalaci nebo používání sady Visual Studio za bránou firewall nebo proxy server.

## <a name="error-proxy-authorization-required"></a>Chyba: vyžaduje se autorizace proxy.

K této chybě obvykle dochází, když jsou uživatelé připojeni k Internetu prostřednictvím proxy server a proxy server blokuje volání, která aplikace Visual Studio provede u některých síťových prostředků.

### <a name="to-fix-this-proxy-error"></a>Oprava chyby serveru proxy

- Restartujte sadu Visual Studio. Mělo by se zobrazit dialogové okno ověřování proxy. Po zobrazení výzvy v dialogovém okně zadejte své přihlašovací údaje.

- Pokud restartování sady Visual Studio problém nevyřeší, může to být tím, že proxy server nezobrazuje výzvu k zadání přihlašovacích údajů&#47;&#47;pro adresy http: go.Microsoft.com, &#42;ale pro adresy visualStudio.Microsoft.com. Pro tyto servery zvažte přidání následujících adres URL do seznamu povolených odblokování všech scénářů přihlášení v aplikaci Visual Studio:

  - &#42;. windows.net

  - &#42;. microsoftonline.com

  - &#42;. visualstudio.microsoft.com

  - &#42;. microsoft.com

  - &#42;. live.com

- V opačném případě můžete odebrat adresu&#47;&#47;http: go.Microsoft.com ze seznamu povolených, aby se dialogové okno ověřování proxy serveru zobrazilo jak pro&#47;&#47;adresu http: go.Microsoft.com, tak pro koncové body serveru, když je Visual Studio spuštěn.

  Ani

- Pokud chcete použít výchozí pověření s vaším proxy serverem, můžete provést následující akce:

::: moniker range="vs-2017"

  1. Najděte soubor **devenv. exe. config** (konfigurační soubor Devenv. exe) v souboru: **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** nebo **% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. V konfiguračním souboru vyhledejte `<system.net>` blok a pak přidejte tento kód:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Do `proxyaddress="<http://<yourproxy:port#>`musíte vložit správnou adresu proxy serveru pro vaši síť.

     > [!NOTE]
     > Další informace najdete v tématu [&lt;defaultProxy&gt; element (nastavení sítě)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) a [&lt;stránky&gt;ho prvku proxy serveru (nastavení sítě)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) .

::: moniker-end

::: moniker range="vs-2019"

  1. Najděte soubor **devenv. exe. config** (konfigurační soubor Devenv. exe) v souboru: **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** nebo **% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Enterprise\Common7\IDE**.

  2. V konfiguračním souboru vyhledejte `<system.net>` blok a pak přidejte tento kód:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Do `proxyaddress="<http://<yourproxy:port#>`musíte vložit správnou adresu proxy serveru pro vaši síť.

     > [!NOTE]
     > Další informace najdete v tématu [&lt;defaultProxy&gt; element (nastavení sítě)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) a [&lt;stránky&gt;ho prvku proxy serveru (nastavení sítě)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) .

::: moniker-end

## <a name="error-the-underlying-connection-was-closed"></a>Chyba: "základní připojení bylo zavřeno"

Pokud používáte aplikaci Visual Studio v privátní síti s bránou firewall, Visual Studio se pravděpodobně nebude moci připojit k některým síťovým prostředkům. Tyto prostředky můžou zahrnovat Azure DevOps Services pro přihlašování a licencování, NuGet a služby Azure. Pokud se Visual Studio nedokáže připojit k jednomu z těchto prostředků, může se zobrazit následující chybová zpráva:

  **Základní připojení bylo ukončeno: při odesílání došlo k neočekávané chybě.**

Visual Studio používá protokol TLS (Transport Layer Security) 1,2 pro připojení k síťovým prostředkům. Bezpečnostní zařízení v některých privátních sítích blokují určitá připojení k serveru, když Visual Studio používá TLS 1,2.

### <a name="to-fix-this-connection-error"></a>Chcete-li opravit tuto chybu připojení

Povolit připojení pro následující adresy URL:

- https:&#47;&#47;Management.Core.Windows.NET

- https:&#47;&#47;App.vssps.VisualStudio.com

- https:&#47;&#47;Login.microsoftonline.com

- https:&#47;&#47;Login.Live.com

- https:&#47;&#47;go.Microsoft.com

- https:&#47;&#47;Graph.Windows.NET

- https:&#47;&#47;App.vsspsext.VisualStudio.com

- &#42;. azurewebsites.net (pro připojení Azure)

- &#42;. visualstudio.microsoft.com

- cdn.vsassets.io (hostuje síť pro doručování obsahu nebo CDN, obsah)

- &#42;. gallerycdn.vsassets.io (hostitelé rozšíření Azure DevOps Services)

- static2.sharepointonline.com (hostuje prostředky, které sada Visual Studio používá v sadě Office UI Fabric Kit, jako jsou například písma).

- &#42;. nuget.org (pro připojení NuGet)

  > [!NOTE]
  > V tomto seznamu nemusí být zahrnuté soukromě vlastněné adresy URL serveru NuGet. Můžete kontrolovat servery NuGet, které používáte v%APPData%\Nuget\NuGet.Config.

## <a name="error-failed-to-parse-id-from-parent-process"></a>Chyba: nepovedlo se analyzovat ID z nadřazeného procesu.

Tato chybová zpráva se může zobrazit při použití zaváděcího nástroje sady Visual Studio a souboru Response. JSON na síťové jednotce. Zdroj chyby je řízení uživatelských účtů (UAC) ve Windows.

K této chybě může dojít z tohoto důvodu: namapovaná síťová jednotka nebo sdílená složka [UNC](/dotnet/standard/io/file-patch-formats#unc-paths) je propojena s přístupovým tokenem uživatele. Když je povolený nástroj řízení uživatelských účtů, vytvoří se dva uživatelské [tokeny přístupu](/windows/win32/secauthz/access-tokens) : jeden *s* přístupem správce a druhý *bez* přístupu správce. Když je vytvořena síťová jednotka nebo sdílená složka, je k ní připojen aktuální přístupový token uživatele. Vzhledem k tomu, že zaváděcí nástroj musí být spuštěn jako správce, nebude mít přístup k síťové jednotce ani ke sdílení, pokud buď jednotka nebo sdílená složka není propojena s tokenem přístupu uživatele, který má přístup správce.

### <a name="to-fix-this-error"></a>Odstranění této chyby

Můžete použít příkaz `net use`, nebo můžete změnit nastavení Zásady skupiny UAC. Další informace o těchto alternativních řešeních a jejich implementaci najdete v následujících článcích podpory společnosti Microsoft:

* [Mapované jednotky nejsou k dispozici na příkazovém řádku se zvýšenými oprávněními, pokud je nástroj řízení uživatelských účtů nakonfigurován na možnost zobrazit výzvu k zadání pověření ve Windows](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co)
* [Po zapnutí řízení uživatelských účtů v operačních systémech Windows nemusí aplikace mít přístup k některým umístěním v síti.](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Instalace a používání sady Visual Studio za bránou firewall nebo proxy serverem](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Příručka pro správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio](install-visual-studio.md)
