---
title: Přepínače příkazového řádku Devenv
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595706"
---
# <a name="devenv-command-line-switches"></a>Devenv – přepínače příkazového řádku

Devenv umožňuje nastavit různé možnosti pro IDE, sestavení projektů, ladění projektů a nasazení projektů z příkazového řádku. Pomocí těchto přepínačů můžete spustit ide ze skriptu nebo souboru BAT (například skript pro noční sestavení) nebo spustit ide v určité konfiguraci.

> [!NOTE]
> Pro úlohy související s sestavením se doporučuje použít MSBuild namísto devenv. Další informace naleznete v [tématu MSBuild command-line reference](../../msbuild/msbuild-command-line-reference.md).

Informace o přepínačích, které souvisejí s vývojem vbalíčku, naleznete také v [tématu Přepínače příkazového řádku Devenv pro vývoj balíčku VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

## <a name="devenv-switch-syntax"></a>Syntaxe přepínače Devenv

Příkazy, které `devenv` začínají, `devenv.com` jsou zpracovány nástrojem, který poskytuje výstup `stdout` `stderr`prostřednictvím standardních datových proudů systému, například a . Nástroj určuje příslušné přesměrování vstupně-výstupních výstupů, když zachytí výstup, například do souboru TXT.

Alternativně příkazy, které `devenv.exe` začínají můžete použít stejné `devenv.com` přepínače, ale nástroj je vynechán. Použití `devenv.exe` přímo zabraňuje výstupu z objevit na konzole.

Pravidla syntaxe `devenv` pro přepínače se podobají pravidlům pro ostatní nástroje příkazového řádku DOS. Následující pravidla syntaxe `devenv` platí pro všechny přepínače a jejich argumenty:

- Příkazy začínají `devenv`na .

- Přepínače nerozlišují malá a velká písmena.

- Přepínač můžete určit pomocí pomlčky ("-") nebo lomítka ("/").

- Při zadávání řešení nebo projektu je prvním argumentem název souboru řešení nebo souboru projektu, včetně cesty k souboru.

- Pokud první argument je soubor, který není řešení nebo projekt, tento soubor se otevře v příslušném editoru, v nové instanci ide.

- Pokud zadáte název souboru projektu namísto názvu `devenv` souboru řešení, příkaz prohledá nadřazenou složku souboru projektu pro soubor řešení, který má stejný název. Příkaz `devenv myproject1.vbproj /build` například vyhledá v nadřazené složce `myproject1.sln`soubor řešení s názvem .

  > [!NOTE]
  > Jeden a jediný soubor řešení, který odkazuje na tento projekt by měl být umístěn v nadřazené složce. Pokud nadřazená složka neobsahuje žádný soubor řešení, který odkazuje na tento projekt, nebo pokud nadřazená složka obsahuje dva nebo více souborů řešení, které na něj odkazují, je vytvořen dočasný soubor řešení.

- Pokud cesty k souborům a názvy souborů obsahují mezery, musíte je uzavřete do uvozovek (""). Například, `"c:\project a\"`.

- Vložte jeden znak mezery mezi přepínače a argumenty na stejném řádku. Příkaz `devenv /log output.txt` například otevře ide a vyhlásí všechny informace protokolu pro tuto relaci na output.txt.

- V `devenv` příkazech nelze použít syntaxi porovnávání vzorů.

## <a name="devenv-switches"></a>Devenv přepínače

Následující přepínače příkazového řádku zobrazují ide a proveďte popsaný úkol.

|Přepínač příkazového řádku|Popis|
| - |-----------------|
|[/Příkaz](command-devenv-exe.md)|Spustí ide a provede zadaný příkaz.<br /><br /> `devenv /command "nav https://docs.microsoft.com/"`|
|[/DebugExe](debugexe-devenv-exe.md)|Načte spustitelný soubor jazyka C++ pod kontrolou ladicího programu. Tento přepínač není k dispozici pro spustitelné soubory jazyka Visual Basic nebo C#. Další informace naleznete [v tématu Automaticky spustit proces v ladicím programu](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).<br /><br /> `devenv /debugexe mysln.exe`|
|[/Rozdíl](diff.md)|Porovná dva soubory. Trvá čtyři parametry: *SourceFile*, *TargetFile*, *SourceDisplayName* (volitelné) a *TargetDisplayName* (volitelné).<br /><br /> `devenv /diff File1 File2 Alias1 Alias2`|
|[/DoNotLoadProjekty](donotloadprojects-devenv-exe.md)|Otevře zadané řešení bez načtení všech projektů.<br /><br /> `devenv /donotloadprojects mysln.sln`|
|[/Upravit](edit-devenv-exe.md)|Otevře zadané soubory v spuštěné instanci této aplikace. Pokud neexistují žádné spuštěné instance, spustí novou instanci se zjednodušeným rozložením okna.<br /><br /> `devenv /edit File1 File2`|
|[/LCID nebo /L](lcid-devenv-exe.md)|Nastaví výchozí jazyk pro rozhraní IDE. Pokud zadaný jazyk není součástí instalace sady Visual Studio, toto nastavení je ignorováno.<br /><br /> `devenv /l 1033`|
|[/Protokolovat](log-devenv-exe.md)|Spustí visual studio a protokoly všechny aktivity do souboru protokolu.<br /><br /> `devenv /log mylogfile.xml`|
|[/NoSplash](nosplash-devenv-exe.md)|Otevře ide bez zobrazení úvodní obrazovky.<br /><br /> `devenv /nosplash File1 File2`|
|[/Spustit nebo /R](run-devenv-exe.md)|Zkompiluje a spustí zadané řešení.<br /><br /> `devenv /run mysln.sln`|
|[/RunExit](runexit-devenv-exe.md)|Zkompiluje a spustí zadané řešení, minimalizuje ide při spuštění řešení a zavře ide po dokončení řešení.<br /><br /> `devenv /runexit mysln.sln`|
|[/SafeMode](safemode-devenv-exe.md)|Spustí visual studio v nouzovém režimu. Tento přepínač načte pouze výchozí prostředí, výchozí služby a dodávané verze balíčků jiných výrobců.<br /><br /> Tento přepínač nepřijímá žádné argumenty.|
|[/UseEnv](useenv-devenv-exe.md)|Způsobí, že ide používat PATH, INCLUDE, LIBPATH a LIB proměnné prostředí pro kompilaci C++. Tento přepínač je nainstalován s vývojem plochy s úlohou **C++.** Další informace naleznete [v tématu Nastavení proměnných cesty a prostředí pro sestavení příkazového řádku](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|

Následující přepínače příkazového řádku nezobrazují ide.

|Přepínač příkazového řádku|Popis|
| - |-----------------|
|[/?](q-devenv-exe.md)|Zobrazí nápovědu pro `devenv` přepínače v okně **příkazového řádku**.<br /><br /> Tento přepínač nepřijímá žádné argumenty.|
|[/Sestavení](build-devenv-exe.md)|Vytvoří zadané řešení nebo projekt podle konfigurace zadaného řešení.<br /><br /> `devenv mysln.sln /build`|
|[/Clean](clean-devenv-exe.md)|Odstraní všechny soubory vytvořené příkazem sestavení, aniž by to ovlivnilo zdrojové soubory.<br /><br /> `devenv mysln.sln /clean`|
|[/Nasazení](deploy-devenv-exe.md)|Vytvoří řešení, spolu se soubory potřebné pro nasazení, v souladu s konfigurací řešení.<br /><br /> `devenv mysln.sln /deploy`|
|[/Out](out-devenv-exe.md)|Umožňuje zadat soubor pro příjem chyb při vytváření.<br /><br /> `devenv mysln.sln /build Debug /out log.txt`|
|[/Projekt](project-devenv-exe.md)|Projekt k sestavení, čištění nebo nasazení. Tento přepínač můžete použít pouze `/Build`v případě, `/Rebuild` `/Clean`že `/Deploy` jste také zadali přepínač , , nebo přepínač.<br /><br /> `devenv mysln.sln /build Debug /project proj1`|
|[/ProjectConfig](projectconfig-devenv-exe.md)|Určuje konfiguraci projektu, kterou chcete sestavit nebo nasadit. Tento přepínač můžete použít pouze v případě, že jste přepínač také dodali. `/Project`<br /><br /> `devenv mysln.sln /build Release /project proj1 /projectconfig Release`|
|[/Znovu sestavit](rebuild-devenv-exe.md)|Vyčistí a pak vytvoří zadané řešení nebo projekt podle konfigurace zadaného řešení.<br /><br /> `devenv mysln.sln /rebuild`|
|[/ResetSettings](resetsettings-devenv-exe.md)|Obnoví výchozí nastavení sady Visual Studio. Volitelně obnoví nastavení na `.vssettings` zadaný soubor.<br /><br /> `devenv /resetsettings mysettings.vssettings`|
|[/Upgrade](upgrade-devenv-exe.md)|Inovuje zadaný soubor řešení a všechny jeho soubory projektu nebo zadaný soubor projektu na aktuální formáty sady Visual Studio pro tyto soubory.<br /><br /> `devenv mysln.sln /upgrade`|

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](general-environment-options-dialog-box.md)
- [Přepínače příkazového řádku Devenv pro vývoj vbalíčku VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
