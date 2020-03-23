---
title: Poradce při potížích se sítí nebo proxy serverem
description: Najděte řešení pro chyby související se sítí nebo proxy, se kterými se můžete setkat při instalaci nebo použití sady Visual Studio za bránou firewall nebo proxy serverem.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114985"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>Poradce při potížích se sítí při instalaci nebo použití sady Visual Studio

Máme řešení pro nejtypičtější chyby související se sítí nebo proxy, které se mohou vyskytnou při instalaci nebo použití sady Visual Studio za bránou firewall nebo proxy serverem.

## <a name="error-proxy-authorization-required"></a>Chyba: "Vyžadována autorizace proxy serveru"

K této chybě obvykle dochází, když jsou uživatelé připojeni k Internetu prostřednictvím proxy serveru a proxy server blokuje volání, která visual studio provádí na některé síťové prostředky.

### <a name="to-fix-this-proxy-error"></a>Oprava této chyby proxy serveru

- Restartujte sadu Visual Studio. Mělo by se zobrazit dialogové okno ověřování proxy serveru. Po zobrazení výzvy v dialogovém okně zadejte pověření.

- Pokud restartování sady Visual Studio problém nevyřeší, může se podařit s výzvou k zadání pověření pro adresy http:&#47;&#47;go.microsoft.com, ale pro adresy &#42;.visualStudio.microsoft.com. U těchto serverů zvažte přidání následujících adres URL do seznamu povolených adres, které odblokují všechny scénáře přihlášení v sadě Visual Studio:

  - &#42;.windows.net

  - &#42;.microsoftonline.com

  - &#42;.visualstudio.microsoft.com

  - &#42;.microsoft.com

  - &#42;.live.com

- Jinak můžete odebrat adresu http:&#47;&#47;go.microsoft.com ze seznamu povolených adres, takže se při restartování sady Visual Studio zobrazí dialogové okno ověřování proxy serveru pro adresu http:&#47;&#47;go.microsoft.com i koncové body serveru.

  - nebo -

- Pokud chcete používat výchozí přihlašovací údaje s proxy serverem, můžete provést následující akce:

::: moniker range="vs-2017"

  1. V ynastomském souboru najdete soubor **devenv.exe** (konfigurační soubor devenv.exe) v: **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** nebo **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. V konfiguračním `<system.net>` souboru najděte blok a přidejte tento kód:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Do aplikace `proxyaddress="<http://<yourproxy:port#>`je nutné vložit správnou adresu proxy sítě.

     > [!NOTE]
     > Další informace naleznete na [ &lt;&gt; stránkách defaultProxy Element (Nastavení sítě)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) a [ &lt;proxy&gt; element (nastavení sítě).](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings)

::: moniker-end

::: moniker range="vs-2019"

  1. V ynastomském souboru najdete soubor **devenv.exe** (konfigurační soubor devenv.exe) v: **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** nebo **%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE**.

  2. V konfiguračním `<system.net>` souboru najděte blok a přidejte tento kód:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Do aplikace `proxyaddress="<http://<yourproxy:port#>`je nutné vložit správnou adresu proxy sítě.

     > [!NOTE]
     > Další informace naleznete na [ &lt;&gt; stránkách defaultProxy Element (Nastavení sítě)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) a [ &lt;proxy&gt; element (nastavení sítě).](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings)

::: moniker-end

## <a name="error-the-underlying-connection-was-closed"></a>Chyba: Základní připojení bylo uzavřeno.

Pokud používáte Visual Studio v privátní síti, která má bránu firewall, visual studio nemusí být schopen připojit k některé síťové prostředky. Tyto prostředky mohou zahrnovat služby Azure DevOps pro přihlášení a licencování, NuGet a služby Azure. Pokud se Visual Studio nepodaří připojit k jednomu z těchto prostředků, může se zobrazit následující chybová zpráva:

  **Základní připojení bylo uzavřeno: Při odesílání došlo k neočekávané chybě.**

Visual Studio používá protokol TLS (Transport Layer Security) 1.2 pro připojení k síťovým prostředkům. Bezpečnostní zařízení v některých privátních sítích blokují určitá připojení k serveru, když visual studio používá TLS 1.2.

### <a name="to-fix-this-connection-error"></a>Oprava této chyby připojení

Povolte připojení pro následující adresy URL:

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;.azurewebsites.net (pro připojení Azure)

- &#42;.visualstudio.microsoft.com

- cdn.vsassets.io (hostuje síť pro doručování obsahu nebo obsah CDN)

- &#42;.gallerycdn.vsassets.io (hostuje rozšíření Azure DevOps Services)

- static2.sharepointonline.com (hostuje prostředky, které Visual Studio používá v sadě Office UI Fabric kit, jako jsou písma)

- &#42;.nuget.org (pro připojení NuGet)

  > [!NOTE]
  > Adresy URL serveru NuGet v soukromém vlastnictví nemusí být do tohoto seznamu zahrnuty. V %APPData%\Nuget\NuGet.Config můžete vyhledat servery NuGet, které používáte.

## <a name="error-failed-to-parse-id-from-parent-process"></a>Chyba: "Analýza ID z nadřazeného procesu se nezdařila"

Tato chybová zpráva se může vyskytnat při použití zaváděcího nástroje sady Visual Studio a souboru response.json na síťové jednotce. Zdrojem chyby je řízení uživatelských účtů (UAC) v systému Windows.

Zde je důvod, proč k této chybě může dojít: Namapovaná síťová jednotka nebo sdílená [síť UNC](/dotnet/standard/io/file-path-formats#unc-paths) je propojena s přístupovým tokenem uživatele. Je-li povolennástroj Řízení uživatelských účtů, jsou vytvořeny dva [tokeny přístupu](/windows/win32/secauthz/access-tokens) uživatelů: jeden *s* přístupem správce a jeden *bez* přístupu správce. Při vytvoření síťové jednotky nebo sdílené položky je s ním propojen aktuální přístupový token uživatele. Vzhledem k tomu, že zaváděcí nástroj musí být spuštěn jako správce, nebude mít přístup k síťové jednotce ani sdílení, pokud jednotka nebo sdílená stránka nejsou propojeny s tokenem přístupu uživatele, který má přístup správce.

### <a name="to-fix-this-error"></a>Odstranění této chyby

Můžete použít `net use` příkaz nebo můžete změnit nastavení zásad skupiny koordinátoru Řízení. Další informace o těchto zástupcích a jejich implementaci naleznete v následujících článcích podpory společnosti Microsoft:

* [Namapované jednotky nejsou k dispozici z výzvy se zvýšenými oprávněními, pokud je příkaz Ku.SAC nakonfigurován na Výzvu k zadání pověření v systému Windows](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co)
* [Programy pravděpodobně nebudou mít po zapnutí funkce Řízení uživatelských účtů v operačních systémech Windows přístup k některým síťovým umístěním.](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace a používání sady Visual Studio za bránou firewall nebo proxy serverem](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Průvodce správcem sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio](install-visual-studio.md)
