---
title: Úlohy msbuild specifické pro jazyk C++ | Dokumenty společnosti Microsoft
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 6393e771f9e9ed862d21397dabacdb3f3808c386
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633145"
---
# <a name="msbuild-tasks-specific-to-c"></a>MSBuild úkoly specifické pro C++

Úkoly poskytují kód, který se spustí během procesu sestavení. Při instalaci jazyka C++ jsou k dispozici následující úkoly, kromě těch, které jsou nainstalovány s MSBuild. Další informace naleznete v tématu [MSBuild (C++) přehled](/cpp/build/msbuild-visual-cpp-overview).

 Kromě parametrů pro každý úkol má každý úkol také následující parametry.

| Parametr | Popis |
|-------------------| - |
| `Condition` | Volitelný `String` parametr.<br /><br /> Výraz, `Boolean` který modul MSBuild používá k určení, zda bude tato úloha provedena. Informace o podmínkách podporovaných msbuild, naleznete v [tématu Podmínky](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Volitelný parametr. Může obsahovat jednu z následujících hodnot:<br /><br /> -   **WarnAndContinue** nebo **true**. Pokud úloha selže, následné úkoly v [Target](../msbuild/target-element-msbuild.md) element a sestavení pokračovat v provádění a všechny chyby z úkolu jsou považovány za upozornění<br />-   **ErrorAndContinue**. Pokud úloha selže, následné `Target` úkoly v prvku a sestavení pokračovat v provádění a všechny chyby z úkolu jsou považovány za chyby.<br />-   **ErrorAndStop** nebo **false** (výchozí). Pokud úloha selže, zbývající úkoly v elementu`Target` a sestavení nejsou `Target` provedeny a celý prvek a sestavení jsou považovány za neúspěšné.<br /><br /> Verze rozhraní .NET Framework před 4.5 `true` `false` podporovaly pouze hodnoty a.<br /><br /> Další informace naleznete v [tématu Postup: Ignorovat chyby v úkolech](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Úkol BscMake](../msbuild/bscmake-task.md)|Zabalí nástroj Microsoft Browse Information Maintenance Utility (*bscmake.exe*).|
|[Cl úkol](../msbuild/cl-task.md)|Zalomí nástroj kompilátoru Jazyka C++ (*cl.exe*).|
|[Úkol CPPClean](../msbuild/cppclean-task.md)|Odstraní dočasné soubory, které msbuild vytvoří při sestavení projektu Jazyka C++.|
|[Úkol ClangCompile](../msbuild/clangcompile-task.md)|Zalomí nástroj kompilátoru jazyka C++ (*clang.exe*).|
|[Úkol CustomBuild](../msbuild/custombuild-task.md)|Zalomí nástroj kompilátoru jazyka C++ (*cmd.exe*).|
|[Úkol FXC](../msbuild/fxc-task.md)|V procesu sestavení použijte kompilátory shaderu HLSL.|
|[OutoutoutdateItems](../msbuild/getoutofdateitems-task.md)|Čte staré tlogy, zapisuje nové tlogy a vrací sadu položek, které nejsou aktuální. (pomocná úloha)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Získá název výstupního souboru pro cl a další nástroje, které umožňují zadat pouze výstupní adresář nebo úplný název souboru nebo nic. (pomocná úloha)|
|[Úloha LIB](../msbuild/lib-task.md)|Zabalí nástroj Microsoft 32-Bit Library Manager (*lib.exe*).|
|[Propojit úkol](../msbuild/link-task.md)|Zalomí nástroj propojovacího programu jazyka C++*(link.exe).*|
|[Úloha MIDL](../msbuild/midl-task.md)|Zalomí kompilátor jazyka Microsoft Interface Definition Language (MIDL)*(midl.exe).*|
|[Úloha MT](../msbuild/mt-task.md)|Zabalí nástroj Microsoft Manifest Tool (*mt.exe*).|
|[Úloha multitooltask](../msbuild/multitooltask-task.md)|Žádný popis.|
|[Úloha ParallelCustomBuild](../msbuild/parallelcustombuild-task.md)|Spusťte paralelní instance [úlohy CustomBuild](../msbuild/custombuild-task.md).|
|[RC úkol](../msbuild/rc-task.md)|Zalomí nástroj Kompilátor prostředků systému Microsoft Windows (*rc.exe*).|
|[Úloha SetEnv](../msbuild/setenv-task.md)|Nastaví nebo odstraní hodnotu zadané proměnné prostředí.|
|[Základní třída TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)|Dědí z [VCToolTask](../msbuild/vctooltask-base-class.md).|
|[Úloha zprávy VCMessage](../msbuild/vcmessage-task.md)|Protokoly varovné zprávy a chybové zprávy během sestavení. (Nelze prodloužit. Pouze interní použití.)|
|[Základní třída VCToolTask](../msbuild/vctooltask-base-class.md)|Dědí z [tooltask](/dotnet/api/microsoft.build.utilities.tooltask).|
|[Úloha XDCMake](../msbuild/xdcmake-task.md)|Zalomí nástroj dokumentace XML (*xdcmake.exe*), který sloučí soubory dokumentu XML (*.xdc)* do souboru *XML.*|
|[Úloha XSD](../msbuild/xsd-task.md)|Zalomí nástroj definice schématu XML (*xsd.exe*), který generuje soubory schématu nebo třídy ze zdroje. *Viz poznámka níže.*|
|[Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)|Popisuje prvky systému MSBuild.|
|[Úlohy](../msbuild/msbuild-tasks.md)|Popisuje úkoly, které jsou jednotky kódu, které lze kombinovat k vytvoření sestavení.|
|[Psaní úkolů](../msbuild/task-writing.md)|Popisuje, jak vytvořit úkol.|

> [!NOTE]
> Počínaje Visual Studio 2017, C++ podpora projektu pro *xsd.exe* je zastaralé. Rozhraní **API Microsoft.VisualC.CppCodeProvider** můžete stále používat ručním přidáním souboru *CppCodeProvider.dll* do souboru GAC.
