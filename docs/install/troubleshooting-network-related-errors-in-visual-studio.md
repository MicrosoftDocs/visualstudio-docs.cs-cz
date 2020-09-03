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
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0e127006976c484d1e4fc2fe011af979af7eb7a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114985"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>Řešení chyb souvisejících se sítí při instalaci nebo používání sady Visual Studio

Máme řešení pro nejčastější chyby související se sítí nebo proxy serverem, se kterými se můžete setkat při instalaci nebo používání sady Visual Studio za bránou firewall nebo proxy server.

## <a name="error-proxy-authorization-required"></a>Chyba: vyžaduje se autorizace proxy.

K této chybě obvykle dochází, když jsou uživatelé připojeni k Internetu prostřednictvím proxy server a proxy server blokuje volání, která aplikace Visual Studio provede u některých síťových prostředků.

### <a name="to-fix-this-proxy-error"></a>Oprava chyby serveru proxy

- Restartujte Visual Studio. Mělo by se zobrazit dialogové okno ověřování proxy. Po zobrazení výzvy v dialogovém okně zadejte své přihlašovací údaje.

- Pokud restartování sady Visual Studio problém nevyřeší, může to být tím, že proxy server nevyzve k zadání přihlašovacích údajů pro http: &#47;&#47;go.microsoft.com adres, ale pro adresy &#42;. visualStudio.microsoft.com. Pro tyto servery zvažte přidání následujících adres URL do seznamu povolených odblokování všech scénářů přihlášení v aplikaci Visual Studio:

  - &#42;. windows.net

  - &#42;. microsoftonline.com

  - &#42;. visualstudio.microsoft.com

  - &#42;. microsoft.com

  - &#42;. live.com

- V opačném případě můžete v seznamu povolených adres odebrat adresu http: &#47;&#47;go.microsoft.com, aby se dialogové okno ověřování proxy serveru zobrazilo pro adresu http: &#47;&#47;go.microsoft.com a koncové body serveru při restartování sady Visual Studio.

  - nebo -

- Pokud chcete použít výchozí pověření s vaším proxy serverem, můžete provést následující akce:

::: moniker range="vs-2017"

  1. Najděte **devenv.exe.config** (konfigurační soubor devenv.exe) v: **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** nebo **% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. V konfiguračním souboru Najděte `<system.net>` blok a pak přidejte tento kód:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Do sítě musíte vložit správnou adresu proxy serveru `proxyaddress="<http://<yourproxy:port#>` .

     > [!NOTE]
     > Další informace najdete na stránkách [ &lt; defaultProxy &gt; element (nastavení sítě)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) a [ &lt; elementu proxy &gt; (nastavení sítě)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) .

::: moniker-end

::: moniker range="vs-2019"

  1. Najděte **devenv.exe.config** (konfigurační soubor devenv.exe) v: **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** nebo **% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Enterprise\Common7\IDE**.

  2. V konfiguračním souboru Najděte `<system.net>` blok a pak přidejte tento kód:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Do sítě musíte vložit správnou adresu proxy serveru `proxyaddress="<http://<yourproxy:port#>` .

     > [!NOTE]
     > Další informace najdete na stránkách [ &lt; defaultProxy &gt; element (nastavení sítě)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) a [ &lt; elementu proxy &gt; (nastavení sítě)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) .

::: moniker-end

## <a name="error-the-underlying-connection-was-closed"></a>Chyba: "základní připojení bylo zavřeno"

Pokud používáte aplikaci Visual Studio v privátní síti s bránou firewall, Visual Studio se pravděpodobně nebude moci připojit k některým síťovým prostředkům. Tyto prostředky můžou zahrnovat Azure DevOps Services pro přihlašování a licencování, NuGet a služby Azure. Pokud se Visual Studio nedokáže připojit k jednomu z těchto prostředků, může se zobrazit následující chybová zpráva:

  **Základní připojení bylo ukončeno: při odesílání došlo k neočekávané chybě.**

Visual Studio používá protokol TLS (Transport Layer Security) 1,2 pro připojení k síťovým prostředkům. Bezpečnostní zařízení v některých privátních sítích blokují určitá připojení k serveru, když Visual Studio používá TLS 1,2.

### <a name="to-fix-this-connection-error"></a>Chcete-li opravit tuto chybu připojení

Povolit připojení pro následující adresy URL:

- https: &#47;&#47;management.core.windows.net

- https: &#47;&#47;app.vssps.visualstudio.com

- https: &#47;&#47;login.microsoftonline.com

- https: &#47;&#47;login.live.com

- https: &#47;&#47;go.microsoft.com

- https: &#47;&#47;graph.windows.net

- https: &#47;&#47;app.vsspsext.visualstudio.com

- &#42;. azurewebsites.net (pro připojení Azure)

- &#42;. visualstudio.microsoft.com

- cdn.vsassets.io (hostuje síť pro doručování obsahu nebo CDN, obsah)

- &#42;. gallerycdn.vsassets.io (Hosts Azure DevOps Services Extensions)

- static2.sharepointonline.com (hostuje prostředky, které sada Visual Studio používá v sadě Office UI Fabric Kit, jako jsou například písma).

- &#42;. nuget.org (pro připojení NuGet)

  > [!NOTE]
  > V tomto seznamu nemusí být zahrnuté soukromě vlastněné adresy URL serveru NuGet. Můžete kontrolovat servery NuGet, které používáte v% data% \Nuget\NuGet.Config.

## <a name="error-failed-to-parse-id-from-parent-process"></a>Chyba: nepovedlo se analyzovat ID z nadřazeného procesu.

Tato chybová zpráva se může zobrazit, když použijete zaváděcí nástroj sady Visual Studio a response.jsv souboru na síťové jednotce. Zdroj chyby je řízení uživatelských účtů (UAC) ve Windows.

K této chybě může dojít z tohoto důvodu: namapovaná síťová jednotka nebo sdílená složka [UNC](/dotnet/standard/io/file-path-formats#unc-paths) je propojena s přístupovým tokenem uživatele. Když je povolený nástroj řízení uživatelských účtů, vytvoří se dva uživatelské [tokeny přístupu](/windows/win32/secauthz/access-tokens) : jeden *s* přístupem správce a druhý *bez* přístupu správce. Když se vytvoří síťová jednotka nebo sdílená složka, k ní se napojí aktuální přístupový token uživatele. Vzhledem k tomu, že zaváděcí nástroj musí být spuštěn jako správce, nebude mít přístup k síťové jednotce ani ke sdílení, pokud buď jednotka nebo sdílená složka není propojena s tokenem přístupu uživatele, který má přístup správce.

### <a name="to-fix-this-error"></a>Odstranění této chyby

Můžete použít příkaz, `net use` nebo můžete změnit nastavení zásady skupiny UAC. Další informace o těchto alternativních řešeních a jejich implementaci najdete v následujících článcích podpory společnosti Microsoft:

* [Mapované jednotky nejsou k dispozici na příkazovém řádku se zvýšenými oprávněními, pokud je nástroj řízení uživatelských účtů nakonfigurován na možnost zobrazit výzvu k zadání pověření ve Windows](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co)
* [Po zapnutí řízení uživatelských účtů v operačních systémech Windows nemusí aplikace mít přístup k některým umístěním v síti.](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace a používání sady Visual Studio za bránou firewall nebo proxy serverem](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio](install-visual-studio.md)
