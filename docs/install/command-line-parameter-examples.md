---
title: Příklady parametrů příkazového řádku pro instalaci
description: Přizpůsobte si tyto příklady a vytvořte vlastní instalaci sady Visual Studio na příkazovém řádku.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8fc43cef8526b2ca79bb0b88a1d56ef4f4a2a65a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275264"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Příklady parametrů příkazového řádku pro instalaci sady Visual Studio

Chcete-li ilustrovat, jak [používat parametry příkazového řádku k instalaci sady Visual Studio](use-command-line-parameters-to-install-visual-studio.md), zde je několik příkladů, které můžete přizpůsobit tak, aby odpovídaly vašim potřebám.

V každém `vs_enterprise.exe`příkladu `vs_community.exe` a `vs_professional.exe` představují příslušné vydání zaváděcího nástroje Sady Visual Studio, což je malý (přibližně 1 MB) soubor, který iniciuje proces stahování. Pokud používáte jinou edici, nahraďte příslušný název zaváděcího nástroje.

> [!NOTE]
> Všechny příkazy vyžadují zvýšení oprávnění správce a zobrazí se výzva Řízení uživatelských účtů, pokud proces není spuštěn z výzvy se zvýšenými oprávněními.
>
> [!NOTE]
> Znak na `^` konci příkazového řádku můžete použít ke zřetězení více řádků do jednoho příkazu. Případně můžete jednoduše umístit tyto řádky dohromady na jeden řádek. V prostředí PowerShell je ekvivalentní`` ` ``znak backtick ( ).

Seznamy úloh a součástí, které můžete nainstalovat pomocí příkazového řádku, najdete na stránce [ID úloh a součástí sady Visual Studio.](workload-and-component-ids.md)

## <a name="using---installpath"></a>Použití --installPath

* Nainstalujte minimální instanci sady Visual Studio bez interaktivních výzev, ale průběhu se zobrazí:

  ```cmd
   vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Aktualizujte instanci sady Visual Studio pomocí příkazového řádku bez interaktivních výzev, ale průběhu:

   ```cmd
   vs_enterprise.exe --update --quiet --wait
   vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
   ```

  > [!NOTE]
  > Oba příkazy se doporučuje. První příkaz aktualizuje Instalační program sady Visual Studio. Druhý příkaz aktualizuje instanci sady Visual Studio. Chcete-li se vyhnout dialogovému oknu Řízení uživatelských účtů, spusťte příkazový řádek jako správce.

* Nainstalujte instanci plochy sady Visual Studio bezobslužně pomocí francouzské jazykové sady, která se vrací pouze v případě, že je produkt nainstalován.

  ```cmd
   vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

## <a name="using---wait"></a>Použití --wait

* Slouží v dávkových souborech nebo skriptech a počkejte, až se instalační program sady Visual Studio dokončí, než bude proveden další příkaz. U dávkových `%ERRORLEVEL%` souborů bude proměnná prostředí obsahovat vrácenou hodnotu příkazu, jak je popsáno v [parametrech příkazového řádku Použít parametry příkazového řádku k instalaci](use-command-line-parameters-to-install-visual-studio.md) sady Visual Studio. Některé nástroje příkazu vyžadují další parametry, aby čekaly na dokončení a získaly vrácenou hodnotu instalačního programu. Následuje příklad dalších parametrů použitých s příkazem skriptu prostředí PowerShell "Start-Process":

   ```cmd
   start /wait vs_professional.exe --installPath "C:\VS" --passive --wait > nul
   echo %errorlevel%
   ```

   ```powershell
   $exitCode = Start-Process -FilePath vs_enterprise.exe -ArgumentList "--installPath", "C:\VS", "--passive", "--wait" -Wait -PassThru
   ```

   – nebo –

   ```powershell
    $startInfo = New-Object System.Diagnostics.ProcessStartInfo
    $startInfo.FileName = "vs_enterprise.exe"
    $startInfo.Arguments = "--all --quiet --wait"
    $process = New-Object System.Diagnostics.Process
    $process.StartInfo = $startInfo
    $process.Start()
    $process.WaitForExit()
   ```

* První '--wait' používá Instalační služba sady Visual Studio a druhý '-Wait' se používá 'Start-Process' čekat na dokončení. Parametr '-PassThru' používá "Start-Process" k použití ukončovacího kódu instalačního programu pro jeho vrácenou hodnotu.

## <a name="using---layout"></a>Použití --layout

* Stáhněte si základní editor Visual Studio (minimální konfigurace sady Visual Studio). K dispozici je pouze anglická jazyková sada:

  ```cmd
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* Stáhněte si webové úlohy .NET pro stolní počítače a .NET spolu se všemi doporučenými součástmi a rozšířením GitHub. K dispozici je pouze anglická jazyková sada:

  ```cmd
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---all"></a>Použití --all

* Spusťte interaktivní instalaci všech úloh a součástí, které jsou k dispozici v edici Visual Studio Enterprise:

   ```cmd
   vs_enterprise.exe --all
   ```

## <a name="using---includerecommended"></a>Použití --includeRecommended

* Nainstalujte druhou pojmenovanou instanci sady Visual Studio Professional do počítače s již nainstalovanou edicí Visual Studio Community s podporou vývoje node.js:

   ```cmd
   vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>Použití --remove

::: moniker range="vs-2017"

* Odeberte komponentu Nástroje profilování z výchozí instanci sady Visual Studio:

  ```cmd
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range="vs-2019"

* Odeberte komponentu Nástroje profilování z výchozí instanci sady Visual Studio:

  ```cmd
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

## <a name="using---path"></a>Použití --cesty

::: moniker range="vs-2017"

Tyto parametry příkazového řádku jsou **nové v 15.7**. Další informace o nich naleznete na stránce [Visual Studio Pomocí parametrů příkazového řádku.](use-command-line-parameters-to-install-visual-studio.md)

::: moniker-end

* Použití cesty instalace, mezipaměti a sdílených cest:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Použití pouze cest k instalaci a mezipaměti:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Použití pouze instalačních a sdílených cest:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Použití pouze instalační cesty:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Použití exportu

::: moniker range="vs-2017"

Tento příkaz příkazového řádku je **nový v 15.9**. Další informace o něm naleznete na stránce [Visual Studio Pomocí parametrů příkazového řádku.](use-command-line-parameters-to-install-visual-studio.md)

::: moniker-end

* Použití exportu k uložení výběru z instalace:

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
  ```

* Použití exportu k uložení vlastního výběru od začátku:

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
  ```

## <a name="using---config"></a>Použití --config

::: moniker range="vs-2017"

Tento parametr příkazového řádku je **nový v 15.9**. Další informace o něm naleznete na stránce [Visual Studio Pomocí parametrů příkazového řádku.](use-command-line-parameters-to-install-visual-studio.md)

::: moniker-end

* Použití --config k instalaci úloh a součástí z dříve uloženého konfiguračního souboru instalace:

  ```cmd
  vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
  ```

* Použití --config k přidání úloh a součástí do existující instalace:

  ```cmd
  vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
  ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Příručka administrátora sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio pomocí parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [Vytvoření offline instalace sady Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
