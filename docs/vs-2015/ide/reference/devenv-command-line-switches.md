---
title: Přepínače příkazového řádku nástroje devenv | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7ee1596cf59fb4ba9b21772cdabc0c875ef8779a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215031"
---
# <a name="devenv-command-line-switches"></a>Devenv – přepínače příkazového řádku
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
DEVENV umožňuje nastavit různé možnosti pro integrované vývojové prostředí (IDE) a také vytváření, ladění a nasazení projektů z příkazového řádku. Spuštění rozhraní IDE ze skriptu nebo soubor .bat, například noční sestavení skript, nebo spuštění integrovaného vývojového prostředí v konkrétní konfiguraci, použijte tyto přepínače.  
  
> [!NOTE]
>  Pro úlohy související s buildem teď doporučujeme použít nástroj MSBuild namísto nástroje devenv. Další informace najdete v tématu [Reference k příkazovému řádku](../../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Chcete-li použít musíte spustit devenv jako správce [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) a [/installvstemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) přepínače.  
  
## <a name="devenv-switch-syntax"></a>Syntaxe – přepínač nástroje devenv  
 Ve výchozím nastavení příkazy nástroje devenv předat nástroji devenv.com přepínače.  
  
 Poskytuje nástroj devenv.com doručování výstup prostřednictvím standardního systému datových proudů, jako například `stdout` a `stderr`a určuje příslušné přesměrování vstupů/výstupů v případě zachycení výstup, třeba do souboru .txt. Příkazy, které začínají místo toho `devenv.exe` můžete použít stejné přepínače, ale bude odesílat do programu devenv.exe, bez použití nástroje devenv.com.  
  
 Syntaxe pravidla pro `devenv` přepínače se podobají těm pro další nástroje pro příkazový řádek DOSU. Následující syntaxe pravidla se vztahují na všechny `devenv` přepínače a jejich argumenty:  
  
-   Příkazy začínají `devenv`.  
  
-   Přepínače nerozlišují malá a velká písmena.  
  
-   Při zadávání řešení nebo projektu, první argument je název souboru řešení nebo soubor projektu, včetně cesta k souboru.  
  
-   Pokud první argument je soubor, který není řešení nebo projektu, tento soubor se otevře ve vhodném editoru v nové instanci integrovaného vývojového prostředí.  
  
-   Když zadáte název souboru projektu namísto názvu souboru řešení `devenv` příkaz vyhledá nadřazené složce souboru projektu, který má stejný název souboru řešení. Například příkaz `devenv /build myproject1.vbproj` vyhledá nadřazené složky pro soubor řešení s názvem "myproject1.sln".  
  
    > [!NOTE]
    >  Jeden a pouze jeden soubor řešení, která odkazuje na tento projekt se musí nacházet v nadřazené složky. Pokud nadřazená složka neobsahuje žádný soubor řešení, která odkazuje na tento projekt, nebo pokud nadřazená složka obsahuje dva nebo více souborů řešení, které na ni odkazují, pak dočasné řešení se vytvoří soubor, který má název pro tento projekt a na něj odkazuje.  
  
-   Když cesty k souborům a názvy souborů obsahují mezery, je nutné je uzavřít do dvojitých uvozovek (""). Například "c:\project\\".  
  
-   Vložte jeden znak mezery mezi přepínače a argumenty na stejném řádku. Například příkaz **devenv/log výstup.txt** otevře rozhraní IDE a vypíše všechny výstup.txt zaznamenávat informace o dané relace.  
  
-   Nelze použít porovnávání vzorů syntaxe v poznámce `devenv` příkazy.  
  
## <a name="devenv-switches"></a>Přepínače nástroje devenv  
 Použijte následující přepínače příkazového řádku pro zobrazení integrovaného vývojového prostředí a popisuje úlohu provést.  
  
|Přepínač příkazového řádku|Popis|  
|-------------------------|-----------------|  
|[/ Příkaz (devenv.exe)](../../ide/reference/command-devenv-exe.md)|Spustí rozhraní IDE a provede zadaný příkaz.|  
|[/ DebugExe (devenv.exe)](../../ide/reference/debugexe-devenv-exe.md)|Načítání [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] spustitelný pod kontrolu ladicího programu. Tento přepínač není k dispozici pro [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../includes/csprcs-md.md)] spustitelné soubory. Další informace najdete v tématu [automaticky spustit proces v ladicím programu](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).|  
|[/ LCID (devenv.exe)](../../ide/reference/lcid-devenv-exe.md) nebo `/l`|Nastaví výchozí jazyk, rozhraní IDE. Pokud zadaný jazyk není součástí instalace sady Visual Studio, toto nastavení bude ignorovat.|  
|[/ Log (devenv.exe)](../../ide/reference/log-devenv-exe.md)|Spustí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a zaznamená veškerou aktivitu do souboru protokolu.|  
|[/ Spuštění (devenv.exe)](../../ide/reference/run-devenv-exe.md) nebo `/r`|Zkompiluje a spustí zadané řešení.|  
|[/ Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)|Zkompiluje a spustí zadané řešení, minimalizuje integrovaného vývojového prostředí při spuštění řešení a ukončí rozhraní IDE po spuštění řešení.|  
|[/ UseEnv (devenv.exe)](../../ide/reference/useenv-devenv-exe.md)|Způsobí, že integrované vývojové prostředí použít CESTU, zahrnutí a LIB proměnné prostředí pro [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] kompilace místo nastavení nakonfigurovaného v sekci adresáře VC ++ **projekty** možnosti **možnosti** Dialogové okno. Další informace najdete v tématu [nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](http://msdn.microsoft.com/library/99389528-deb5-43b9-b99a-03c8773ebaf4)|  
|[/ Edit (devenv.exe)](../../ide/reference/edit-devenv-exe.md)|Otevře dané soubory v běžící instanci této aplikace. Pokud neexistují žádné spuštěné instance, spustí novou instanci se zjednodušeným rozložením okna.|  
|[/ ResetAddin (devenv.exe)](../../ide/reference/resetaddin-devenv-exe.md)|Spustí instanci integrovaného vývojového prostředí sady Visual Studio bez načtení zadaného Add-in.|  
|[/ SafeMode (devenv.exe)](../../ide/reference/safemode-devenv-exe.md)|Spustí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] v nouzovém režimu a načte jenom výchozí prostředí a služby a dodaný verzích balíčky třetích stran.|  
|[/ ResetSkipPkgs (devenv.exe)](../../ide/reference/resetskippkgs-devenv-exe.md)|Smaže všechny značky SkipLoading přidané do balíků VSPackages uživatelé, kteří chtějí předejít problém rozšíření VSPackages.|  
|[/ Nastavení (devenv.exe)](../../ide/reference/setup-devenv-exe.md)|Vynutí sady Visual Studio ke sloučení resource metadata, která popisuje nabídky, panely nástrojů a příkaz skupin, ze všech rozšíření VSPackages k dispozici.|  
  
 Použijte následující přepínače příkazového řádku k provedení popsané úlohy. Tyto přepínače příkazového řádku se nezobrazují integrovaném vývojovém prostředí.  
  
|Přepínač příkazového řádku|Popis|  
|-------------------------|-----------------|  
|[/? (devenv.exe)](../../ide/reference/q-devenv-exe.md)|Zobrazí nápovědu pro devenv přepínače v **okno příkazového řádku**.<br /><br /> **Devenv /?**|  
|[/ Sestavení (devenv.exe)](../../ide/reference/build-devenv-exe.md)|Sestaví zadané řešení nebo projekt podle konfigurace zadané řešení.<br /><br /> **/ Build myproj.csproj nástroje devenv**|  
|[/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)|Odstraní všechny soubory vytvořené příkazem k sestavení, aniž by to ovlivnilo zdrojové soubory.<br /><br /> **DEVENV myproj.csproj / clean**|  
|[/ Nasazení (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)|Sestaví řešení a spolu se soubory, které jsou nezbytné pro nasazení podle konfigurace řešení.<br /><br /> **DEVENV myproj.csproj / deploy**|  
|[/Diff](../../ide/reference/diff.md)|Porovná dva soubory.  Přebírá čtyři parametry: Zdrojovýsoubor, Cílovýsoubor, SourceDisplayName(optional),TargetDisplayName(optional).|  
|[/ InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md)|Registruje projekt nebo šablony položek, které se nacházejí v  *\<VisualStudioInstallDir >* \Common7\IDE\ProjectTemplates nebo  *\<VisualStudioInstallDir >* \Common7 \IDE\ItemTemplates tak, aby k nim může přistupovat prostřednictvím **nový projekt** a **přidat novou položku** dialogových oknech.<br /><br /> **/ Installvstemplates nástroje devenv**|  
|[/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)|Umožňuje zadat soubor, který chcete zobrazovat chyby při sestavování.<br /><br /> **/ Build myproj.csproj DEVENV/out log.txt**|  
|[/ Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)|Projekt k sestavení, vyčištění nebo nasazení. Tento přepínač můžete použít pouze v případě, že jste zadali také/Build, / rebuild, / clean nebo / deploy – přepínač.|  
|[/ ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)|Určuje konfiguraci projektu k vytvoření buildu nebo nasazení. Tento přepínač lze použít pouze v případě, že jste zadali také přepínač/Project.|  
|[/ Sestavení (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)|Čistí a poté sestaví zadané řešení nebo projekt podle konfigurace zadané řešení.|  
|[/ ResetSettings (devenv.exe)](../../ide/reference/resetsettings-devenv-exe.md)|Obnoví výchozí nastavení sady Visual Studio. Volitelně obnoví nastavení zadaného souboru .vssettings.|  
|[/ Updateconfiguration (devenv.exe)](../../ide/reference/updateconfiguration-devenv-exe.md)|Upozorní [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sloučit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mezipaměť balíčků na systém a rozhraní MEF pro všechny změny.|  
|[/ Upgrade (devenv.exe)](../../ide/reference/upgrade-devenv-exe.md)|Upgrady na aktuální verzi v zadaném souboru řešení a všechny jeho soubory projektu nebo zadaný soubor projektu, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] formáty pro tyto soubory.|  
  
## <a name="see-also"></a>Viz také  
 [Obecné, Prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)



