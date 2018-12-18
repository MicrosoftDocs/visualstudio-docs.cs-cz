---
title: Přepínače příkazového řádku nástroje devenv
ms.date: 02/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3bf255a0e4eb622cb81718ddfc30d5b568bad2c2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063393"
---
# <a name="devenv-command-line-switches"></a>Přepínače příkazového řádku nástroje devenv

DEVENV umožňuje nastavit různé možnosti pro integrované vývojové prostředí (IDE), jakož i sestavit, ladit a nasadit projekty z příkazového řádku. Spuštění rozhraní IDE ze skriptu nebo soubor .bat, například noční sestavení skript, nebo spuštění integrovaného vývojového prostředí v konkrétní konfiguraci, použijte tyto přepínače.

> [!NOTE]
> Pro úlohy související s buildem se doporučuje namísto devenv pomocí nástroje MSBuild. Další informace najdete v tématu [odkaz na příkazový řádek MSBuild](../../msbuild/msbuild-command-line-reference.md).

## <a name="devenv-switch-syntax"></a>Syntaxe přepínač nástroje devenv

Příkazy, které začínají `devenv` jsou zpracovávány `devenv.com` nástroj, který dodává výstup prostřednictvím standardního systému datových proudů, jako například `stdout` a `stderr`. Nástroj určuje příslušné přesměrování vstupů/výstupů v případě, že zaznamenává výstup, třeba do souboru .txt.

Na druhé straně příkazy, které začínají `devenv.exe` můžete použít stejné přepínače, ale `devenv.com` nástroj přeskočí. Pomocí `devenv.exe` přímo bránil výstup na konzole.

Syntaxe pravidla pro `devenv` přepínače se podobají těm pro další nástroje pro příkazový řádek DOSU. Následující syntaxe pravidla se vztahují na všechny `devenv` přepínače a jejich argumenty:

- Příkazy začínají `devenv`.

- Přepínače nerozlišují malá a velká písmena.

- Při zadávání řešení nebo projektu, první argument je název souboru řešení nebo soubor projektu, včetně cesta k souboru.

- Pokud první argument je soubor, který není řešení nebo projektu, tento soubor se otevře ve vhodném editoru v nové instanci integrovaného vývojového prostředí.

- Když zadáte název souboru projektu namísto názvu souboru řešení `devenv` příkaz vyhledá v nadřazené složce souboru projektu, který má stejný název souboru řešení. Například příkaz `devenv myproject1.vbproj /build` vyhledá nadřazené složky pro soubor řešení s názvem "myproject1.sln".

    > [!NOTE]
    > Jeden a pouze jeden soubor řešení, která odkazuje na tento projekt se musí nacházet v nadřazené složky. Pokud nadřazená složka neobsahuje žádný soubor řešení, která odkazuje na tento projekt, nebo pokud nadřazená složka obsahuje dva nebo více souborů řešení, které na ni odkazují, pak se vytvoří soubor dočasné řešení.

- Když cesty k souborům a názvy souborů obsahují mezery, je nutné je uzavřít do uvozovek (""). Například "c:\project\\".

- Vložte jeden znak mezery mezi přepínače a argumenty na stejném řádku. Například příkaz **devenv/log výstup.txt** otevře rozhraní IDE a vypíše všechny výstup.txt zaznamenávat informace o dané relace.

- Nelze použít porovnávání vzorů syntaxe v poznámce `devenv` příkazy.

## <a name="devenv-switches"></a>Přepínače nástroje devenv

Následující přepínače příkazového řádku zobrazit integrovaného vývojového prostředí a provedení popsané úlohy.

|Přepínač příkazového řádku|Popis|
| - |-----------------|
|[/Command](../../ide/reference/command-devenv-exe.md)|Spustí rozhraní IDE a provede zadaný příkaz.|
|[/DebugExe](../../ide/reference/debugexe-devenv-exe.md)|Načte spustitelný C++ pod kontrolu ladicího programu. Tento přepínač není k dispozici v jazyce Visual Basic nebo C# spustitelné soubory. Další informace najdete v tématu [automaticky spustit proces v ladicím programu](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).|
|[/ LCID nebo/l](../../ide/reference/lcid-devenv-exe.md)|Nastaví výchozí jazyk, rozhraní IDE. Pokud zadaný jazyk není součástí instalace sady Visual Studio, toto nastavení je ignorováno.|
|[/Log](../../ide/reference/log-devenv-exe.md)|Spuštění sady Visual Studio a zaznamená veškerou aktivitu do souboru protokolu.|
|[/ Run nebo/r](../../ide/reference/run-devenv-exe.md)|Zkompiluje a spustí zadané řešení.|
|[/Runexit](../../ide/reference/runexit-devenv-exe.md)|Zkompiluje a spustí zadané řešení, minimalizuje integrovaného vývojového prostředí při spuštění řešení a ukončí rozhraní IDE po spuštění řešení.|
|[/UseEnv](../../ide/reference/useenv-devenv-exe.md)|Způsobí, že integrované vývojové prostředí pro účely CESTU, zahrnutí a LIB proměnné prostředí kompilace jazyka C++, místo nastavení nakonfigurovaného v sekci adresáře VC ++ **projekty** možnosti **možnosti** dialogové okno. Tento přepínač je nainstalován se sadou **vývoj desktopových aplikací pomocí C++** pracovního vytížení. Další informace najdete v tématu [nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|
|[/Edit](../../ide/reference/edit-devenv-exe.md)|Otevře dané soubory v běžící instanci této aplikace. Pokud neexistují žádné spuštěné instance, spustí novou instanci se zjednodušeným rozložením okna.|
|[/SafeMode](../../ide/reference/safemode-devenv-exe.md)|Visual Studio se spustí v nouzovém režimu a načte jenom výchozí prostředí a služby a dodáno verzích balíčky třetích stran.|
|[/ResetSkipPkgs](../../ide/reference/resetskippkgs-devenv-exe.md)|Smaže všechny značky SkipLoading přidané do balíků VSPackages uživatelé, kteří chtějí předejít problém rozšíření VSPackages.|
|[/Setup](../../ide/reference/setup-devenv-exe.md)|Vynutí sady Visual Studio ke sloučení resource metadata, která popisuje nabídky, panely nástrojů a příkaz skupin, ze všech rozšíření VSPackages k dispozici. Tento příkaz musíte spustit jako správce.|

Následující přepínače příkazového řádku se nezobrazují integrovaném vývojovém prostředí.

|Přepínač příkazového řádku|Popis|
| - |-----------------|
|[/?](../../ide/reference/q-devenv-exe.md)|Zobrazí nápovědu pro devenv přepínače v **okno příkazového řádku**.<br /><br /> `devenv /?`|
|[/Build](../../ide/reference/build-devenv-exe.md)|Sestaví zadané řešení nebo projekt podle konfigurace zadané řešení.<br /><br /> `devenv myproj.csproj /build`|
|[/Clean](../../ide/reference/clean-devenv-exe.md)|Odstraní všechny soubory vytvořené příkazem k sestavení, aniž by to ovlivnilo zdrojové soubory.<br /><br /> `devenv myproj.csproj /clean`|
|[/Deploy](../../ide/reference/deploy-devenv-exe.md)|Sestaví řešení a spolu se soubory, které jsou nezbytné pro nasazení podle konfigurace řešení.<br /><br /> `devenv myproj.csproj /deploy`|
|[/Diff](../../ide/reference/diff.md)|Porovná dva soubory. Přebírá čtyři parametry: Zdrojovýsoubor, Cílovýsoubor, SourceDisplayName (volitelné), TargetDisplayName (volitelné).|
|[/Out](../../ide/reference/out-devenv-exe.md)|Umožňuje zadat soubor, který chcete zobrazovat chyby při sestavování.<br /><br /> `devenv myproj.csproj /build /out log.txt`|
|[/Project](../../ide/reference/project-devenv-exe.md)|Projekt k sestavení, vyčištění nebo nasazení. Tento přepínač můžete použít pouze v případě, že jste zadali také/Build, / rebuild, / clean nebo / deploy – přepínač.|
|[/ProjectConfig](../../ide/reference/projectconfig-devenv-exe.md)|Určuje konfiguraci projektu k vytvoření buildu nebo nasazení. Tento přepínač lze použít pouze v případě, že jste zadali také přepínač/Project.|
|[/Rebuild](../../ide/reference/rebuild-devenv-exe.md)|Čistí a poté sestaví zadané řešení nebo projekt podle konfigurace zadané řešení.|
|[/ResetSettings](../../ide/reference/resetsettings-devenv-exe.md)|Obnoví výchozí nastavení sady Visual Studio. Volitelně obnoví nastavení zadaného souboru .vssettings.|
|[/Upgrade](../../ide/reference/upgrade-devenv-exe.md)|Upgraduje na aktuální formáty sady Visual Studio pro tyto soubory v zadaném souboru řešení a všechny jeho soubory projektu nebo soubor zadaný projekt.|

## <a name="see-also"></a>Viz také:

* [Obecné, Prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
