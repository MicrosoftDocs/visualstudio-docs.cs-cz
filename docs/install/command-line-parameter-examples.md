---
title: Příklady parametrů příkazového řádku pro instalaci
description: Tyto příklady si můžete přizpůsobit a vytvořit tak vlastní instalaci sady Visual Studio z příkazového řádku.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 02496f230338e429b281f2b0d516cb9a06fe9e7a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868527"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Příklady parametrů příkazového řádku pro instalaci sady Visual Studio

Pro ilustraci, jak [použít parametry příkazového řádku k instalaci sady Visual Studio](use-command-line-parameters-to-install-visual-studio.md), je zde několik příkladů, které můžete přizpůsobit, aby odpovídaly vašim potřebám.

V každém příkladu, `vs_enterprise.exe` `vs_professional.exe` a `vs_community.exe` představuje příslušnou edici zaváděcího nástroje sady Visual Studio, což je malý (přibližně 1 MB) soubor, který iniciuje proces stahování. Pokud používáte jinou edici, nahraďte odpovídající název zaváděcího nástroje.

> [!NOTE]
> Všechny příkazy vyžadují zvýšení oprávnění správce a zobrazí se výzva pro řízení uživatelských účtů, pokud proces nebude spuštěn z výzvy se zvýšenými oprávněními.
>
> [!NOTE]
> `^`Znak na konci příkazového řádku můžete použít k zřetězení více řádků do jediného příkazu. Alternativně můžete tyto řádky umístit na jeden řádek dohromady. V PowerShellu je ekvivalentní `` ` `` znak znaku zaškrtnutí ().

Seznam úloh a komponent, které můžete nainstalovat pomocí příkazového řádku, najdete na stránce s [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md) .

## <a name="using---installpath"></a>Použití--installPath

* Instalace minimální instance aplikace Visual Studio bez interaktivních výzev, ale průběh zobrazení:

  ```cmd
   vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Aktualizace instance sady Visual Studio pomocí příkazového řádku bez interaktivních výzev, ale průběh zobrazení:

   ```cmd
   vs_enterprise.exe --update --quiet --wait
   vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
   ```

  > [!NOTE]
  > Oba příkazy jsou doporučené. První příkaz aktualizuje Instalační program pro Visual Studio. Druhý příkaz aktualizuje instanci sady Visual Studio. Pokud se chcete vyhnout dialogovému oknu řízení uživatelských účtů, spusťte příkazový řádek jako správce.

* Nainstalujte instanci aplikace Visual Studio v tichém režimu s francouzskou jazykovou sadou, která bude vrácena pouze v případě, že je produkt nainstalován.

  ```cmd
   vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

## <a name="using---wait"></a>Použití--Wait

* Použijte v dávkových souborech nebo skriptech k čekání na dokončení instalačního programu sady Visual Studio před provedením dalšího příkazu. V případě dávkových souborů `%ERRORLEVEL%` bude proměnná prostředí obsahovat vrácenou hodnotu příkazu, jak je popsáno v [parametrech příkazového řádku use pro instalaci sady Visual Studio](use-command-line-parameters-to-install-visual-studio.md) . Některé příkazové nástroje vyžadují další parametry pro čekání na dokončení a získání návratové hodnoty instalačního programu. Následuje příklad dalších parametrů použitých s příkazem PowerShell Script Start-Process:

   ```cmd
   start /wait vs_professional.exe --installPath "C:\VS" --passive --wait > nul
   echo %errorlevel%
   ```

   ```powershell
   $process = Start-Process -FilePath vs_enterprise.exe -ArgumentList "--installPath", "C:\VS", "--passive", "--wait" -Wait -PassThru
   Write-Output $process.ExitCode 
   ```

   nebo

   ```powershell
    $startInfo = New-Object System.Diagnostics.ProcessStartInfo
    $startInfo.FileName = "vs_enterprise.exe"
    $startInfo.Arguments = "--all --quiet --wait"
    $process = New-Object System.Diagnostics.Process
    $process.StartInfo = $startInfo
    $process.Start()
    $process.WaitForExit()
   ```

* První '--wait ' je používán Instalační program pro Visual Studio a druhá '-wait ' je používána ' Start-proces ' k čekání na dokončení. Parametr-PassThru se používá v příkazu Start-Process k použití ukončovacího kódu instalačního programu pro jeho návratovou hodnotu.

## <a name="using---layout"></a>Použití--layout

* Stáhněte si základní editor sady Visual Studio (minimální konfigurace sady Visual Studio). Zahrnout pouze anglickou jazykovou sadu:

  ```cmd
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* Stáhněte si webové úlohy .NET Desktop a .NET spolu se všemi doporučenými součástmi a rozšířením GitHubu. Zahrnout pouze anglickou jazykovou sadu:

  ```cmd
   vs_community.exe --layout C:\VS ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---all"></a>Použití--All

* Spusťte interaktivní instalaci všech úloh a součástí, které jsou k dispozici v edici Visual Studio Enterprise:

   ```cmd
   vs_enterprise.exe --all
   ```

## <a name="using---includerecommended"></a>Použití--includeRecommended

* Instalace druhé pojmenované instance Visual Studio Professional na počítači s již nainstalovanou sadou Visual Studio Community Edition s podporou pro Node.js vývoj:

   ```cmd
   vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>Použití--Remove

::: moniker range="vs-2017"

* Odeberte součást Nástroje pro profilaci z výchozí nainstalované instance sady Visual Studio:

  ```cmd
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

::: moniker range="vs-2019"

* Odeberte součást Nástroje pro profilaci z výchozí nainstalované instance sady Visual Studio:

  ```cmd
   vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

::: moniker-end

## <a name="using---path"></a>Použití--Path

::: moniker range="vs-2017"

Tyto parametry příkazového řádku jsou **v 15,7 nové**. Další informace o těchto možnostech naleznete na stránce [použití parametrů příkazového řádku pro instalaci sady Visual Studio](use-command-line-parameters-to-install-visual-studio.md) .

::: moniker-end

* Pomocí instalačního programu, mezipaměti a sdílených cest:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Pouze pomocí cesty instalace a mezipaměti:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Jenom pomocí instalačních a sdílených cest:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Pouze pomocí instalační cesty:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Použití exportu

::: moniker range="vs-2017"

Tento příkaz příkazového řádku je **v 15,9 nový**. Další informace o tom, jak nainstalovat stránku sady Visual Studio, najdete v tématu [použití parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md) .

::: moniker-end

* Uložení výběru z instalace pomocí exportu:

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
  ```

* Použití exportu pro uložení vlastního výběru od začátku:

  ```cmd
  "C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
  ```

## <a name="using---config"></a>Pomocí--config

::: moniker range="vs-2017"

Tento parametr příkazového řádku je **v 15,9 nový**. Další informace o tom, jak nainstalovat stránku sady Visual Studio, najdete v tématu [použití parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md) .

::: moniker-end

* Pomocí--config nainstalujete úlohy a komponenty z dříve uloženého konfiguračního souboru instalace:

  ```cmd
  vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
  ```

* Použití--config k přidání úloh a součástí do existující instalace:

  ```cmd
  vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
  ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Příručka pro správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [Vytvoření offline instalace sady Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
