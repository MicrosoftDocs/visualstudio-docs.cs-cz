---
title: Devenv – přepínače příkazového řádku
description: Přečtěte si o přepínačích příkazového řádku devenv a o tom, jak je použít k nastavení možností IDE, a také sestavování, ladění a nasazování projektů, a to vše z příkazového řádku.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 597a3f7e9a9b36d52f55a9215891c40b18f1a9e9
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305513"
---
# <a name="devenv-command-line-switches"></a>Devenv – přepínače příkazového řádku

Nástroj devenv umožňuje nastavit různé možnosti pro rozhraní IDE, sestavit projekty, ladit projekty a nasadit projekty z příkazového řádku. Pomocí těchto přepínačů spusťte rozhraní IDE ze skriptu nebo souboru. bat (například skriptu pro noční sestavení) nebo spusťte integrované vývojové prostředí (IDE) v konkrétní konfiguraci.

> [!NOTE]
> Pro úlohy související s sestavením se doporučuje použít MSBuild místo devenv. Další informace naleznete v tématu [Reference k příkazovému řádku nástroje MSBuild](../../msbuild/msbuild-command-line-reference.md).

Informace o přepínačích, které souvisejí s vývojem VSPackage, naleznete také v [přepínačích příkazového řádku devenv pro vývoj pro VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

## <a name="devenv-switch-syntax"></a>Syntaxe přepínače devenv

Příkazy, které začínají, `devenv` jsou zpracovávány `devenv.com` nástrojem, který doručuje výstup přes standardní systémové proudy, například `stdout` a `stderr` . Nástroj určuje vhodné přesměrování vstupu a výstupu při zachycení výstupu, například souboru. txt.

Příkazy, které začínají na, `devenv.exe` mohou také používat stejné přepínače, ale tento `devenv.com` Nástroj je obejít. Použití `devenv.exe` přímo brání v zobrazení výstupu v konzole nástroje.

Pravidla syntaxe pro `devenv` přepínače se podobají pravidlům pro další nástroje příkazového řádku systému DOS. Následující pravidla syntaxe se vztahují na všechny `devenv` přepínače a jejich argumenty:

- Příkazy začínají na `devenv` .

- U přepínačů se nerozlišují malá a velká písmena.

- Můžete zadat přepínač pomocí pomlčky ("-") nebo lomítka ("/").

- Při zadání řešení nebo projektu je prvním argumentem název souboru řešení nebo souboru projektu, včetně cesty k souboru.

- Pokud je první argument soubor, který není řešením nebo projektem, tento soubor se otevře v příslušném editoru v nové instanci rozhraní IDE.

- Když zadáte název souboru projektu namísto názvu souboru řešení, `devenv` příkaz vyhledá nadřazenou složku souboru projektu pro soubor řešení, který má stejný název. Například příkaz `devenv myproject1.vbproj /build` vyhledá nadřazenou složku pro soubor řešení s názvem `myproject1.sln` .

  > [!NOTE]
  > Pouze jeden soubor řešení, který odkazuje na tento projekt, by měl být umístěn v nadřazené složce. Pokud nadřazená složka neobsahuje žádný soubor řešení, který odkazuje na tento projekt, nebo Pokud nadřazená složka obsahuje dva nebo více souborů řešení, které na něj odkazují, je vytvořen dočasný soubor řešení.

- Pokud cesty k souborům a názvy souborů obsahují mezery, je nutné je uzavřít do uvozovek (""). Například, `"c:\project a\"`.

- Vložte znak mezery mezi přepínače a argumenty na stejný řádek. Například příkaz `devenv /log output.txt` otevře integrované vývojové prostředí (IDE) a zapíše všechny informace protokolu pro tuto relaci do output.txt.

- V příkazech nelze použít syntaxi porovnávání se vzorem `devenv` .

## <a name="devenv-switches"></a>Přepínače devenv

Následující přepínače příkazového řádku zobrazují integrované vývojové prostředí (IDE) a dělají popsaný úkol.

|Přepínač příkazového řádku|Description|
| - |-----------------|
|[/Command](command-devenv-exe.md)|Spustí integrované vývojové prostředí (IDE) a provede zadaný příkaz.<br /><br /> `devenv /command "nav https://docs.microsoft.com/"`|
|[/DebugExe](debugexe-devenv-exe.md)|Načte spustitelný soubor C++ pod ovládacím prvkem ladicího programu. Tento přepínač není k dispozici pro Visual Basic nebo pro spustitelné soubory v jazyce C#. Další informace najdete v tématu [automatické spuštění procesu v ladicím programu](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).<br /><br /> `devenv /debugexe mysln.exe`|
|[/](diff.md)|Porovná dva soubory. Má čtyři parametry: *požadovaný sourcefile*, *CílovýSoubor*, *Zdrojovýnázevzobrazení* (volitelné) a *cílovýnázevzobrazení* (volitelné).<br /><br /> `devenv /diff File1 File2 Alias1 Alias2`|
|[/DoNotLoadProjects](donotloadprojects-devenv-exe.md)|Otevře zadané řešení bez načtení jakýchkoli projektů.<br /><br /> `devenv /donotloadprojects mysln.sln`|
|[/Edit](edit-devenv-exe.md)|Otevře zadané soubory ve spuštěné instanci této aplikace. Pokud neexistují žádné spuštěné instance, spustí se nová instance se zjednodušeným rozložením oken.<br /><br /> `devenv /edit File1 File2`|
|[/LCID nebo/L](lcid-devenv-exe.md)|Nastaví výchozí jazyk integrovaného vývojového prostředí (IDE). Pokud zadaný jazyk není zahrnutý v instalaci sady Visual Studio, toto nastavení se ignoruje.<br /><br /> `devenv /l 1033`|
|[/Log](log-devenv-exe.md)|Spustí Visual Studio a zaznamená všechny aktivity do souboru protokolu.<br /><br /> `devenv /log mylogfile.xml`|
|[/NoSplash](nosplash-devenv-exe.md)|Otevře IDE bez zobrazení úvodní obrazovky.<br /><br /> `devenv /nosplash File1 File2`|
|[/ResetSettings](resetsettings-devenv-exe.md)|Obnoví výchozí nastavení sady Visual Studio. Volitelně obnoví nastavení do zadaného `.vssettings` souboru.<br /><br /> `devenv /resetsettings mysettings.vssettings`|
|[/Run nebo/R](run-devenv-exe.md)|Zkompiluje a spustí zadané řešení.<br /><br /> `devenv /run mysln.sln`|
|[/RunExit](runexit-devenv-exe.md)|Zkompiluje a spustí zadané řešení, minimalizuje integrované vývojové prostředí (IDE) při spuštění řešení a po skončení běhu řešení ukončí prostředí IDE.<br /><br /> `devenv /runexit mysln.sln`|
|[/SafeMode](safemode-devenv-exe.md)|Spustí aplikaci Visual Studio v nouzovém režimu. Tento přepínač načte jenom výchozí prostředí, výchozí služby a dodávané verze balíčků třetích stran.<br /><br /> Tento přepínač nepřijímá žádné argumenty.|
|[/UseEnv](useenv-devenv-exe.md)|Způsobí, že rozhraní IDE použije proměnné prostředí PATH, INCLUDE, LIBPATH a LIB pro kompilaci C++. Tento přepínač se instaluje s úlohou **vývoj desktopových aplikací v C++** . Další informace najdete v tématu [Nastavení cesty a proměnných prostředí pro Command-Line sestavení](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|

Následující přepínače příkazového řádku nezobrazují integrované vývojové prostředí (IDE).

|Přepínač příkazového řádku|Description|
| - |-----------------|
|[/?](q-devenv-exe.md)|Zobrazí nápovědu pro `devenv` přepínače v **okně příkazového řádku**.<br /><br /> Tento přepínač nepřijímá žádné argumenty.|
|[/Build](build-devenv-exe.md)|Sestavení zadaného řešení nebo projektu podle konfigurace zadaného řešení.<br /><br /> `devenv mysln.sln /build`|
|[/Clean](clean-devenv-exe.md)|Odstraní všechny soubory vytvořené příkazem Build bez vlivu na zdrojové soubory.<br /><br /> `devenv mysln.sln /clean`|
|[/Deploy](deploy-devenv-exe.md)|Sestaví řešení společně se soubory nezbytnými pro nasazení podle konfigurace řešení.<br /><br /> `devenv mysln.sln /deploy`|
|[/Out](out-devenv-exe.md)|Umožňuje určit soubor pro příjem chyb při sestavování.<br /><br /> `devenv mysln.sln /build Debug /out log.txt`|
|[/Project](project-devenv-exe.md)|Projekt, který se má sestavit, vyčistit nebo nasadit Tento přepínač můžete použít pouze v případě, že jste zadali také `/Build` `/Rebuild` přepínač,, `/Clean` nebo `/Deploy` .<br /><br /> `devenv mysln.sln /build Debug /project proj1`|
|[/ProjectConfig](projectconfig-devenv-exe.md)|Určuje konfiguraci projektu, která se má sestavit nebo nasadit. Tento přepínač můžete použít pouze v případě, že jste zadali také `/Project` přepínač.<br /><br /> `devenv mysln.sln /build Release /project proj1 /projectconfig Release`|
|[/Rebuild](rebuild-devenv-exe.md)|Vyčistí a pak sestaví zadané řešení nebo projekt podle konfigurace zadaného řešení.<br /><br /> `devenv mysln.sln /rebuild`|
|[/Upgrade](upgrade-devenv-exe.md)|Provede upgrade zadaného souboru řešení a všech jeho souborů projektu nebo zadaného souboru projektu na aktuální formáty sady Visual Studio pro tyto soubory.<br /><br /> `devenv mysln.sln /upgrade`|

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](general-environment-options-dialog-box.md)
- [Přepínače příkazového řádku nástroje devenv pro vývoj pro VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
