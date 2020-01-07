---
title: Přepínače příkazového řádku nástroje devenv
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
ms.openlocfilehash: b3ed82bd8ba3845541d7dce628f99fb78b62ab9f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595706"
---
# <a name="devenv-command-line-switches"></a>Devenv – přepínače příkazového řádku

Nástroj devenv umožňuje nastavit různé možnosti pro rozhraní IDE, sestavit projekty, ladit projekty a nasadit projekty z příkazového řádku. Pomocí těchto přepínačů spusťte rozhraní IDE ze skriptu nebo souboru. bat (například skriptu pro noční sestavení) nebo spusťte integrované vývojové prostředí (IDE) v konkrétní konfiguraci.

> [!NOTE]
> Pro úlohy související s sestavením se doporučuje použít MSBuild místo devenv. Další informace najdete v tématu [odkaz na příkazový řádek MSBuild](../../msbuild/msbuild-command-line-reference.md).

Informace o přepínačích, které souvisejí s vývojem VSPackage, naleznete také v [přepínačích příkazového řádku devenv pro vývoj pro VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

## <a name="devenv-switch-syntax"></a>Syntaxe přepínač nástroje devenv

Příkazy, které začínají `devenv` jsou zpracovávány `devenv.com` nástroj, který dodává výstup prostřednictvím standardního systému datových proudů, jako například `stdout` a `stderr`. Nástroj určuje příslušné přesměrování vstupů/výstupů v případě, že zaznamenává výstup, třeba do souboru .txt.

Příkazy, které začínají na `devenv.exe`, můžou použít stejné přepínače, ale nástroj `devenv.com` se přeskočí. Pomocí `devenv.exe` přímo bránil výstup na konzole.

Pravidla syntaxe pro přepínače `devenv` se podobají pravidlům pro další nástroje příkazového řádku systému DOS. Následující syntaxe pravidla se vztahují na všechny `devenv` přepínače a jejich argumenty:

- Příkazy začínají `devenv`.

- U přepínačů se nerozlišují malá a velká písmena.

- Můžete zadat přepínač pomocí pomlčky ("-") nebo lomítka ("/").

- Při zadávání řešení nebo projektu, první argument je název souboru řešení nebo soubor projektu, včetně cesta k souboru.

- Pokud je první argument soubor, který není řešením nebo projektem, tento soubor se otevře v příslušném editoru v nové instanci rozhraní IDE.

- Když zadáte název souboru projektu namísto názvu souboru řešení `devenv` příkaz vyhledá v nadřazené složce souboru projektu, který má stejný název souboru řešení. Například příkaz `devenv myproject1.vbproj /build` prohledá nadřazenou složku pro soubor řešení s názvem `myproject1.sln`.

  > [!NOTE]
  > Jeden a pouze jeden soubor řešení, která odkazuje na tento projekt se musí nacházet v nadřazené složky. Pokud nadřazená složka neobsahuje žádný soubor řešení, která odkazuje na tento projekt, nebo pokud nadřazená složka obsahuje dva nebo více souborů řešení, které na ni odkazují, pak se vytvoří soubor dočasné řešení.

- Když cesty k souborům a názvy souborů obsahují mezery, je nutné je uzavřít do uvozovek (""). Například `"c:\project a\"`.

- Vložte jeden znak mezery mezi přepínače a argumenty na stejném řádku. Například příkaz `devenv /log output.txt` otevře integrované vývojové prostředí (IDE) a vytvoří výstup všech informací protokolu pro danou relaci do Output. txt.

- V příkazech `devenv` nelze použít syntaxi porovnávání se vzorem.

## <a name="devenv-switches"></a>Přepínače nástroje devenv

Následující přepínače příkazového řádku zobrazují integrované vývojové prostředí (IDE) a dělají popsaný úkol.

|Přepínač příkazového řádku|Popis|
| - |-----------------|
|[/Command](command-devenv-exe.md)|Spustí rozhraní IDE a provede zadaný příkaz.<br /><br /> `devenv /command "nav https://docs.microsoft.com/"`|
|[/DebugExe](debugexe-devenv-exe.md)|Načte spustitelný C++ pod kontrolu ladicího programu. Tento přepínač není k dispozici pro C# Visual Basic nebo spustitelné soubory. Další informace najdete v tématu [automaticky spustit proces v ladicím programu](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).<br /><br /> `devenv /debugexe mysln.exe`|
|[/Diff](diff.md)|Porovná dva soubory. Má čtyři parametry: *požadovaný sourcefile*, *CílovýSoubor*, *Zdrojovýnázevzobrazení* (volitelné) a *cílovýnázevzobrazení* (volitelné).<br /><br /> `devenv /diff File1 File2 Alias1 Alias2`|
|[/DoNotLoadProjects](donotloadprojects-devenv-exe.md)|Otevře zadané řešení bez načtení jakýchkoli projektů.<br /><br /> `devenv /donotloadprojects mysln.sln`|
|[/Edit](edit-devenv-exe.md)|Otevře dané soubory v běžící instanci této aplikace. Pokud neexistují žádné spuštěné instance, spustí novou instanci se zjednodušeným rozložením okna.<br /><br /> `devenv /edit File1 File2`|
|[/LCID nebo/L](lcid-devenv-exe.md)|Nastaví výchozí jazyk, rozhraní IDE. Pokud zadaný jazyk není zahrnutý v instalaci sady Visual Studio, toto nastavení se ignoruje.<br /><br /> `devenv /l 1033`|
|[/Log](log-devenv-exe.md)|Spuštění sady Visual Studio a zaznamená veškerou aktivitu do souboru protokolu.<br /><br /> `devenv /log mylogfile.xml`|
|[/NoSplash](nosplash-devenv-exe.md)|Otevře IDE bez zobrazení úvodní obrazovky.<br /><br /> `devenv /nosplash File1 File2`|
|[/Run nebo/R](run-devenv-exe.md)|Zkompiluje a spustí zadané řešení.<br /><br /> `devenv /run mysln.sln`|
|[/RunExit](runexit-devenv-exe.md)|Zkompiluje a spustí zadané řešení, minimalizuje integrovaného vývojového prostředí při spuštění řešení a ukončí rozhraní IDE po spuštění řešení.<br /><br /> `devenv /runexit mysln.sln`|
|[/SafeMode](safemode-devenv-exe.md)|Spustí aplikaci Visual Studio v nouzovém režimu. Tento přepínač načte jenom výchozí prostředí, výchozí služby a dodávané verze balíčků třetích stran.<br /><br /> Tento přepínač nepřijímá žádné argumenty.|
|[/UseEnv](useenv-devenv-exe.md)|Způsobí, že rozhraní IDE použije proměnné prostředí PATH, INCLUDE, LIBPATH a LIB pro C++ kompilaci. Tento přepínač je nainstalován se sadou **vývoj desktopových aplikací pomocí C++** pracovního vytížení. Další informace najdete v tématu [nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|

Následující přepínače příkazového řádku nezobrazují integrované vývojové prostředí (IDE).

|Přepínač příkazového řádku|Popis|
| - |-----------------|
|[/?](q-devenv-exe.md)|Zobrazí nápovědu k přepínačům `devenv` v **okně příkazového řádku**.<br /><br /> Tento přepínač nepřijímá žádné argumenty.|
|[/Build](build-devenv-exe.md)|Sestaví zadané řešení nebo projekt podle konfigurace zadané řešení.<br /><br /> `devenv mysln.sln /build`|
|[/Clean](clean-devenv-exe.md)|Odstraní všechny soubory vytvořené příkazem k sestavení, aniž by to ovlivnilo zdrojové soubory.<br /><br /> `devenv mysln.sln /clean`|
|[/Deploy](deploy-devenv-exe.md)|Sestaví řešení společně se soubory nezbytnými pro nasazení podle konfigurace řešení.<br /><br /> `devenv mysln.sln /deploy`|
|[/Out](out-devenv-exe.md)|Umožňuje zadat soubor, který chcete zobrazovat chyby při sestavování.<br /><br /> `devenv mysln.sln /build Debug /out log.txt`|
|[/Project](project-devenv-exe.md)|Projekt k sestavení, vyčištění nebo nasazení. Tento přepínač můžete použít pouze v případě, že jste zadali `/Build`, `/Rebuild`, `/Clean`nebo přepínač `/Deploy`.<br /><br /> `devenv mysln.sln /build Debug /project proj1`|
|[/ProjectConfig](projectconfig-devenv-exe.md)|Určuje konfiguraci projektu k vytvoření buildu nebo nasazení. Tento přepínač lze použít pouze v případě, že je zadán také přepínač `/Project`.<br /><br /> `devenv mysln.sln /build Release /project proj1 /projectconfig Release`|
|[/Rebuild](rebuild-devenv-exe.md)|Čistí a poté sestaví zadané řešení nebo projekt podle konfigurace zadané řešení.<br /><br /> `devenv mysln.sln /rebuild`|
|[/ResetSettings](resetsettings-devenv-exe.md)|Obnoví výchozí nastavení sady Visual Studio. Volitelně obnoví nastavení do zadaného souboru `.vssettings`.<br /><br /> `devenv /resetsettings mysettings.vssettings`|
|[/Upgrade](upgrade-devenv-exe.md)|Upgraduje na aktuální formáty sady Visual Studio pro tyto soubory v zadaném souboru řešení a všechny jeho soubory projektu nebo soubor zadaný projekt.<br /><br /> `devenv mysln.sln /upgrade`|

## <a name="see-also"></a>Viz také:

- [Obecné, Prostředí, dialogové okno Možnosti](general-environment-options-dialog-box.md)
- [Přepínače příkazového řádku nástroje devenv pro vývoj pro VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
