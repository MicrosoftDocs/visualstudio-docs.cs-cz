---
title: Úlohy nástroje MSBuild specifické C++ pro | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633145"
---
# <a name="msbuild-tasks-specific-to-c"></a>Úlohy nástroje MSBuild specifické proC++

Úlohy poskytují kód, který se spouští během procesu sestavení. Při C++ instalaci nástroje jsou k dispozici následující úkoly kromě těch, které jsou nainstalovány s nástrojem MSBuild. Další informace naleznete v tématu [Přehled nástrojeC++MSBuild ()](/cpp/build/msbuild-visual-cpp-overview).

 Kromě parametrů pro každý úkol má každý úkol také následující parametry.

| Parametr | Popis |
|-------------------| - |
| `Condition` | Volitelný parametr `String`.<br /><br /> Výraz `Boolean`, který modul MSBuild používá k určení, zda bude tato úloha spuštěna. Informace o podmínkách podporovaných nástrojem MSBuild naleznete v tématu [podmínky](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Volitelný parametr. Může obsahovat jednu z následujících hodnot:<br /><br /> -   **WarnAndContinue** nebo **true**. Pokud se úloha nezdařila, následné úkoly v [cílovém](../msbuild/target-element-msbuild.md) elementu a sestavení se budou spouštět i nadále a všechny chyby z tohoto úkolu jsou považovány za upozornění.<br />-   **ErrorAndContinue**. Pokud se úloha nezdařila, následné úkoly v prvku `Target` a sestavení se budou dále spouštět a všechny chyby z tohoto úkolu jsou považovány za chyby.<br />-   **ErrorAndStop** nebo **false** (výchozí). Pokud se úloha nezdařila, zbývající úkoly v prvku`Target` a sestavení nebudou provedeny a celý `Target` prvek a sestavení jsou považovány za neúspěšné.<br /><br /> Verze .NET Framework před 4,5 podporují pouze hodnoty `true` a `false`.<br /><br /> Další informace najdete v tématu [Postupy: ignorování chyb v úlohách](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[BscMake – úloha](../msbuild/bscmake-task.md)|Zabalí Nástroj pro údržbu informací o procházení Microsoftem (*BSCMAKE. exe*).|
|[CL – úloha](../msbuild/cl-task.md)|Zabalí nástroj C++ kompilátoru (*CL. exe*).|
|[CPPClean – – úloha](../msbuild/cppclean-task.md)|Odstraní dočasné soubory, které nástroj MSBuild vytvoří při C++ sestavení projektu.|
|[ClangCompile – úloha](../msbuild/clangcompile-task.md)|Zabalí nástroj C++ kompilátoru (*Clang. exe*).|
|[CustomBuild – úloha](../msbuild/custombuild-task.md)|Zabalí nástroj C++ kompilátoru (*cmd. exe*).|
|[FXC – úloha](../msbuild/fxc-task.md)|Použijte kompilátory HLSL shaderu v procesu sestavení.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|Přečte staré tlogs, zapisuje nové tlogs a vrátí sadu položek, které nejsou aktuální. (pomocný úkol)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Získá název výstupního souboru pro CL a další nástroje, které umožňují zadat jenom výstupní adresář nebo úplný název souboru nebo nic. (pomocný úkol)|
|[LIB – Úloha](../msbuild/lib-task.md)|Zabalí nástroj Správce bitových knihoven Microsoft 32 (*lib. exe*).|
|[Propojit úkol](../msbuild/link-task.md)|Zabalí nástroj C++ Linker (*Link. exe*).|
|[MIDL – úloha](../msbuild/midl-task.md)|Zabalí nástroj kompilátoru MIDL (Microsoft Interface Definition Language) (*MIDL. exe*).|
|[MT – úloha](../msbuild/mt-task.md)|Zabalí Nástroj manifest společnosti Microsoft (*Mt. exe*).|
|[MultiToolTask – úloha](../msbuild/multitooltask-task.md)|Žádný popis.|
|[ParallelCustomBuild – úloha](../msbuild/parallelcustombuild-task.md)|Spusťte paralelní instance [CustomBuild úlohy](../msbuild/custombuild-task.md).|
|[RC – úloha](../msbuild/rc-task.md)|Zabalí nástroj Microsoft Windows Resource Compiler (*RC. exe*).|
|[Setenv – – úloha](../msbuild/setenv-task.md)|Nastaví nebo odstraní hodnotu zadané proměnné prostředí.|
|[Základní třída TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)|Dědí z [VCToolTask](../msbuild/vctooltask-base-class.md).|
|[VCMessage – – úloha](../msbuild/vcmessage-task.md)|Protokoluje zprávy upozornění a chybové zprávy během sestavení. (Nelze je zvětšit. Pouze interní použití.)|
|[Základní třída VCToolTask](../msbuild/vctooltask-base-class.md)|Dědí z [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask).|
|[XDCMake – úloha](../msbuild/xdcmake-task.md)|Zabalí Nástroj dokumentace XML (*xdcmake. exe*), který sloučí soubory komentáře dokumentu XML ( *. xdc*) do souboru *. XML* .|
|[XSD – úloha](../msbuild/xsd-task.md)|Zabalí Nástroj definice schématu XML (*XSD. exe*), který generuje soubory schématu nebo třídy ze zdroje. *Viz poznámka níže.*|
|[Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)|Popisuje prvky systému MSBuild.|
|[Úlohy](../msbuild/msbuild-tasks.md)|Popisuje úlohy, které jsou jednotky kódu, které mohou být kombinovány pro vytvoření sestavení.|
|[Zápis úlohy](../msbuild/task-writing.md)|V této části najdete popis postupu vytvoření úlohy.|

> [!NOTE]
> Od sady Visual Studio 2017 je C++ podpora projektů pro soubor *XSD. exe* zastaralá. Rozhraní API **Microsoft. VisualC. CppCodeProvider** můžete dál používat tak, že ručně přidáte *CppCodeProvider. dll* do globální mezipaměti sestavení (GAC).
