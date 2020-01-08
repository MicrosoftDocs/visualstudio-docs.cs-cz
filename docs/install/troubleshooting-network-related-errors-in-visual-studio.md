---
title: Řešení potíží s chybami sítě nebo proxy serveru
description: Řešení chyby související s sítě nebo proxy, které můžete narazit při instalaci nebo používání sady Visual Studio za bránou firewall nebo proxy server.
ms.date: 10/29/2019
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 44f18e64db08efa848c498f8956d61a79c24846d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594458"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>Řešení chyb souvisejících se sítí při instalaci nebo používání sady Visual Studio

Máme řešení obvykle chyby související s sítě nebo proxy, které můžete narazit při instalaci nebo používání sady Visual Studio za bránou firewall nebo proxy server.

## <a name="error-proxy-authorization-required"></a>Chyba: "proxy server vyžaduje se autorizace"

K této chybě obvykle dochází, když jsou uživatelé připojeni k Internetu prostřednictvím proxy serveru a proxy server blokuje volání, která vytvoří malou Visual Studio k některým síťovým prostředkům.

### <a name="to-fix-this-proxy-error"></a>Chcete-li vyřešit tuto chybu proxy

- Restartujte sadu Visual Studio. By se zobrazit dialogové okno ověřování proxy serveru. Zadejte svoje přihlašovací údaje po zobrazení výzvy v dialogovém okně.

- Pokud restartování sady Visual Studio problém nevyřeší, může to být tím, že proxy server nezobrazuje výzvu k zadání přihlašovacích údajů&#47;&#47;pro adresy http: go.Microsoft.com, &#42;ale pro adresy visualStudio.Microsoft.com. Pro tyto servery zvažte přidání následujících adres URL do seznamu povolených odblokování všech scénářů přihlášení v aplikaci Visual Studio:

  - &#42;.windows.net

  - &#42;.microsoftonline.com

  - &#42;.visualstudio.microsoft.com

  - &#42;.microsoft.com

  - &#42;.live.com

- V opačném případě můžete ze seznamu&#47;&#47;povolených adres odebrat adresu http: go.Microsoft.com, aby se dialogové okno ověřování proxy serveru zobrazovalo jak&#47;&#47;pro adresu http: go.Microsoft.com, tak pro koncové body serveru při restartování sady Visual Studio.

  -OR-

- Pokud chcete použít výchozí pověření s proxy serverem, můžete provádět následující akce:

::: moniker range="vs-2017"

  1. Najít **devenv.exe.config** (konfigurační soubor devenv.exe) v: **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** nebo **% ProgramFiles (x86) %\Microsoft Vizuální Studio\2017\Enterprise\Common7\IDE**.

  2. V konfiguračním souboru najít `<system.net>` blokovat a následně přidejte následující kód:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Je třeba vložit adresu proxy serveru správná pro vaši síť v `proxyaddress="<http://<yourproxy:port#>`.

     > [!NOTE]
     > Další informace najdete v tématu [&lt;defaultProxy&gt; element (nastavení sítě)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) a [&lt;stránky&gt;ho prvku proxy serveru (nastavení sítě)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) .

::: moniker-end

::: moniker range="vs-2019"

  1. Najděte soubor **devenv. exe. config** (konfigurační soubor Devenv. exe) v souboru: **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** nebo **% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Enterprise\Common7\IDE**.

  2. V konfiguračním souboru najít `<system.net>` blokovat a následně přidejte následující kód:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Je třeba vložit adresu proxy serveru správná pro vaši síť v `proxyaddress="<http://<yourproxy:port#>`.

     > [!NOTE]
     > Další informace najdete v tématu [&lt;defaultProxy&gt; element (nastavení sítě)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) a [&lt;stránky&gt;ho prvku proxy serveru (nastavení sítě)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings) .

::: moniker-end

## <a name="error-the-underlying-connection-was-closed"></a>Chyba: "základní připojení bylo ukončeno."

Pokud používáte Visual Studio v privátní síti, která má bránu firewall, Visual Studio nemusí být schopný se připojit k některým síťovým prostředkům. Tyto prostředky mohou zahrnovat Azure DevOps služby pro přihlašování a licencování NuGet a službami Azure. Pokud Visual Studio nepodaří připojit k jednomu z těchto prostředků, může se zobrazit následující chybová zpráva:

  **Nadřízené připojení bylo uzavřeno: došlo k neočekávané chybě při odesílání**

Visual Studio používá k připojení k síťovým prostředkům protokol zabezpečení TLS (Transport Layer) 1.2. Zabezpečovací zařízení několik soukromých sítích blokují některá serverová připojení, když sada Visual Studio používá TLS 1.2.

### <a name="to-fix-this-connection-error"></a>Chcete-li vyřešit tuto chybu připojení

Povolte připojení pro následující adresy URL:

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;. azurewebsites.net (pro připojení Azure)

- &#42;.visualstudio.microsoft.com

- CDN.vsassets.IO (síť pro doručování obsahu hostitele nebo CDN, obsah)

- &#42;. gallerycdn.vsassets.io (rozšíření hostitele služby Azure DevOps)

- static2.sharepointonline.com (prostředky hostitele, které Visual Studio používá v uživatelském rozhraní Office Fabric kit, jako je například písma)

- &#42;. nuget.org (pro připojení NuGet)

  > [!NOTE]
  > Soukromě vlastněných že nuget serverové adresy URL nemusí být zahrnuté v tomto seznamu. Můžete vyhledat servery NuGet, které používáte v % APPData%\Nuget\NuGet.Config.

## <a name="error-failed-to-parse-id-from-parent-process"></a>Chyba: nepovedlo se analyzovat ID z nadřazeného procesu.

Tato chybová zpráva se může zobrazit při použití zaváděcího nástroje sady Visual Studio a souboru Response. JSON na síťové jednotce. Zdroj chyby je řízení uživatelských účtů (UAC) ve Windows.

K této chybě může dojít z tohoto důvodu: namapovaná síťová jednotka nebo sdílená složka [UNC](/dotnet/standard/io/file-path-formats#unc-paths) je propojena s přístupovým tokenem uživatele. Když je povolený nástroj řízení uživatelských účtů, vytvoří se dva uživatelské [tokeny přístupu](/windows/win32/secauthz/access-tokens) : jeden *s* přístupem správce a druhý *bez* přístupu správce. Když se vytvoří síťová jednotka nebo sdílená složka, k ní se napojí aktuální přístupový token uživatele. Vzhledem k tomu, že zaváděcí nástroj musí být spuštěn jako správce, nebude mít přístup k síťové jednotce ani ke sdílení, pokud buď jednotka nebo sdílená složka není propojena s tokenem přístupu uživatele, který má přístup správce.

### <a name="to-fix-this-error"></a>Odstranění této chyby

Můžete použít příkaz `net use`, nebo můžete změnit nastavení Zásady skupiny UAC. Další informace o těchto alternativních řešeních a jejich implementaci najdete v následujících článcích podpory společnosti Microsoft:

* [Mapované jednotky nejsou k dispozici na příkazovém řádku se zvýšenými oprávněními, pokud je nástroj řízení uživatelských účtů nakonfigurován na možnost zobrazit výzvu k zadání pověření ve Windows](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co)
* [Po zapnutí řízení uživatelských účtů v operačních systémech Windows nemusí aplikace mít přístup k některým umístěním v síti.](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Instalace a používání sady Visual Studio za bránou firewall nebo proxy serverem](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Příručka pro správce aplikace Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio](install-visual-studio.md)
