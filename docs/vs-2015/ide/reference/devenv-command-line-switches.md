---
title: Přepínače příkazového řádku nástroje devenv | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- builds [Team System], command-line
- applications [Visual Studio], executing
- compiling source code, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
- environment, Devenv commands
- compilers, Devenv commands
- switches
- Devenv, syntax and list of switches
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b8b0683024e2881f76bb6c54d9420d351fced08a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668731"
---
# <a name="devenv-command-line-switches"></a>Devenv – přepínače příkazového řádku
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nástroj devenv umožňuje nastavit různé možnosti integrovaného vývojového prostředí (IDE) a také sestavit, ladit a nasadit projekty z příkazového řádku. Pomocí těchto přepínačů spusťte integrované vývojové prostředí (IDE) ze skriptu nebo souboru. bat, například pomocí nočního skriptu sestavení nebo spusťte integrované vývojové prostředí (IDE) v konkrétní konfiguraci.

> [!NOTE]
> Pro úlohy související s sestavením se teď doporučuje použít MSBuild místo devenv. Další informace najdete v tématu [Reference k příkazovému řádku](../../msbuild/msbuild-command-line-reference.md).

> [!NOTE]
> Chcete-li použít přepínače [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) a [/installvstemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) , je nutné spustit devenv jako správce.

## <a name="devenv-switch-syntax"></a>Syntaxe přepínače devenv
 Ve výchozím nastavení příkazy nástroje devenv předají přepínače nástroji devenv.com.

 Nástroj devenv.com zajišťuje doručování výstupu prostřednictvím standardních systémových datových proudů, jako jsou `stdout` a `stderr` , a určuje vhodné přesměrování vstupu a výstupu při zachycení výstupu, například na soubor. txt. Příkazy, které začínají `devenv.exe` , můžou používat stejné přepínače, ale odesílají je do programu devenv.exe, který vynechá nástroj devenv.com.

 Syntaktická pravidla pro `devenv` přepínače se podobají těm, které jsou pro ostatní nástroje příkazového řádku systému DOS. Následující pravidla syntaxe se vztahují na všechny `devenv` přepínače a jejich argumenty:

- Příkazy začínají na `devenv` .

- U přepínačů se nerozlišují malá a velká písmena.

- Při zadání řešení nebo projektu je prvním argumentem název souboru řešení nebo souboru projektu, včetně cesty k souboru.

- Pokud je první argument soubor, který není řešením nebo projektem, tento soubor bude otevřen v příslušném editoru v nové instanci rozhraní IDE.

- Při zadání názvu souboru projektu namísto názvu souboru řešení `devenv` příkaz vyhledá nadřazenou složku souboru projektu pro soubor řešení, který má stejný název. Příkaz například `devenv /build myproject1.vbproj` vyhledá nadřazenou složku pro soubor řešení s názvem "myproject1. sln".

    > [!NOTE]
    > Pouze jeden soubor řešení, který odkazuje na tento projekt, by měl být umístěn v nadřazené složce. Pokud nadřazená složka neobsahuje žádný soubor řešení, který odkazuje na tento projekt, nebo Pokud nadřazená složka obsahuje dva nebo více souborů řešení, které na něj odkazují, bude vytvořen dočasný soubor řešení, který je pojmenován pro tento projekt a odkazuje na něj.

- Pokud cesty k souborům a názvy souborů obsahují mezery, je nutné je uzavřít do uvozovek (""). Například "c:\Project a \\ ".

- Vložte znak mezery mezi přepínače a argumenty na stejný řádek. Například příkaz **devenv/log output.txt** otevře rozhraní IDE a vytvoří výstup všech informací protokolu pro tuto relaci do output.txt.

- V příkazech nelze použít syntaxi porovnávání se vzorem `devenv` .

## <a name="devenv-switches"></a>Přepínače devenv
 Pomocí následujících přepínačů příkazového řádku Zobrazte integrované vývojové prostředí (IDE) a proveďte popsanou úlohu.

|Přepínač příkazového řádku|Popis|
|-------------------------|-----------------|
|[/Command (devenv.exe)](../../ide/reference/command-devenv-exe.md)|Spustí integrované vývojové prostředí (IDE) a provede zadaný příkaz.|
|[/Debugexe otevře zvolený (devenv.exe)](../../ide/reference/debugexe-devenv-exe.md)|Načte [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] spustitelný soubor pod ovládacím prvkem ladicího programu. Tento přepínač není k dispozici pro [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../includes/csprcs-md.md)] spustitelné soubory. Další informace najdete v tématu [automatické spuštění procesu v ladicím programu](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).|
|[/LCID (devenv.exe)](../../ide/reference/lcid-devenv-exe.md) nebo `/l`|Nastaví výchozí jazyk integrovaného vývojového prostředí (IDE). Pokud zadaný jazyk není součástí instalace sady Visual Studio, bude toto nastavení ignorováno.|
|[/Log (devenv.exe)](../../ide/reference/log-devenv-exe.md)|Spustí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a zaznamená všechny aktivity do souboru protokolu.|
|[/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md) nebo `/r`|Zkompiluje a spustí zadané řešení.|
|[/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)|Zkompiluje a spustí zadané řešení, minimalizuje integrované vývojové prostředí (IDE) při spuštění řešení a po skončení běhu řešení ukončí prostředí IDE.|
|[/UseEnv (devenv.exe)](../../ide/reference/useenv-devenv-exe.md)|Způsobí, že rozhraní IDE použije proměnné prostředí PATH, INCLUDE a LIB pro [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] kompilaci místo nastavení určeného v části adresáře VC + + v možnostech **projektů** v dialogovém okně **Možnosti** . Další informace najdete v tématu [Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](https://msdn.microsoft.com/library/99389528-deb5-43b9-b99a-03c8773ebaf4) .|
|[/Edit (devenv.exe)](../../ide/reference/edit-devenv-exe.md)|Otevře zadané soubory ve spuštěné instanci této aplikace. Pokud neexistují žádné spuštěné instance, spustí se nová instance se zjednodušeným rozložením oken.|
|[/ResetAddin (devenv.exe)](../../ide/reference/resetaddin-devenv-exe.md)|Spustí instanci integrovaného vývojového prostředí sady Visual Studio bez načtení zadaného doplňku.|
|[/SafeMode (devenv.exe)](../../ide/reference/safemode-devenv-exe.md)|Spustí se [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] v nouzovém režimu a načte jenom výchozí prostředí a služby a dodávané verze balíčků třetích stran.|
|[/ResetSkipPkgs (devenv.exe)](../../ide/reference/resetskippkgs-devenv-exe.md)|Vymaže všechny značky SkipLoading, které byly přidány do VSPackage uživateli, kteří se chtějí vyhnout načítání balíčku VSPackage problému.|
|[/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md)|Přinutí aplikaci Visual Studio sloučit metadata prostředků, která popisují nabídky, panely nástrojů a skupiny příkazů, ze všech dostupných VSPackage.|

 K provedení popsané úlohy použijte následující přepínače příkazového řádku. Tyto přepínače příkazového řádku nezobrazují integrované vývojové prostředí (IDE).

|Přepínač příkazového řádku|Popis|
|-------------------------|-----------------|
|[/? (devenv.exe)](../../ide/reference/q-devenv-exe.md)|Zobrazí nápovědu k přepínačům devenv v **okně příkazového řádku**.<br /><br /> **Devenv/?**|
|[/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)|Sestavení zadaného řešení nebo projektu podle konfigurace zadaného řešení.<br /><br /> **Devenv MyProj. csproj/Build**|
|[/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)|Odstraní všechny soubory vytvořené příkazem Build bez vlivu na zdrojové soubory.<br /><br /> **Devenv MyProj. csproj/Clean**|
|[/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)|Sestaví řešení společně se soubory nezbytnými pro nasazení podle konfigurace řešení.<br /><br /> **Devenv MyProj. csproj/Deploy**|
|[/](../../ide/reference/diff.md)|Porovná dva soubory.  Má čtyři parametry: požadovaný sourcefile, CílovýSoubor, Zdrojovýnázevzobrazení (volitelné), Cílovýnázevzobrazení (volitelné).|
|[/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md)|Registruje šablony projektů nebo položek, které jsou umístěny v *\<VisualStudioInstallDir>* \Common7\IDE\ProjectTemplates nebo *\<VisualStudioInstallDir>* \Common7\IDE\ItemTemplates, aby k nim bylo možné přistupovat prostřednictvím dialogových oken **Nový projekt** a **Přidat novou položku** .<br /><br /> **/InstallVSTemplates devenv**|
|[/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)|Umožňuje určit soubor pro příjem chyb při sestavování.<br /><br /> **Devenv MyProj. csproj/Build/out log.txt**|
|[/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)|Projekt, který se má sestavit, vyčistit nebo nasadit Tento přepínač můžete použít pouze v případě, že jste zadali také přepínač/Build,/Rebuild,/Clean nebo/Deploy.|
|[/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)|Určuje konfiguraci projektu, která se má sestavit nebo nasadit. Tento přepínač můžete použít pouze v případě, že jste zadali také přepínač/Project.|
|[/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)|Vyčistí a pak sestaví zadané řešení nebo projekt podle konfigurace zadaného řešení.|
|[/ResetSettings (devenv.exe)](../../ide/reference/resetsettings-devenv-exe.md)|Obnoví výchozí nastavení sady Visual Studio. Volitelně obnoví nastavení na zadaný soubor. vssettings.|
|[/Updateconfiguration (devenv.exe)](../../ide/reference/updateconfiguration-devenv-exe.md)|Upozorňuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] na sloučení [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] balíčků v systému a Prohlédněte si všechny změny v mezipaměti MEF.|
|[/Upgrade (devenv.exe)](../../ide/reference/upgrade-devenv-exe.md)|Provede upgrade zadaného souboru řešení a všech jeho souborů projektu nebo zadaného souboru projektu na aktuální [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] formáty pro tyto soubory.|

## <a name="see-also"></a>Viz také
 [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
