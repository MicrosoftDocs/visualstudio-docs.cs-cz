---
title: 'Postup: Konfigurace cílů a úkolů | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe2955feb50a28e5ba631cdeddd169973a42ed25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633886"
---
# <a name="how-to-configure-targets-and-tasks"></a>Postup: Konfigurace cílů a úkolů

Vybrané úlohy MSBuild lze nastavit tak, aby se spouštěli v prostředí, na které cílí, bez ohledu na prostředí vývojového počítače. Pokud například použijete 64bitový počítač k vytvoření aplikace, která cílí na 32bitovou architekturu, jsou vybrané úlohy spuštěny v 32bitovém procesu.
Vybrané úlohy MSBuild lze nastavit tak, aby se spouštěli v prostředí, na které cílí, bez ohledu na prostředí vývojového počítače. Pokud například použijete 64bitový počítač k vytvoření aplikace, která cílí na 32bitovou architekturu, jsou vybrané úlohy spuštěny v 32bitovém procesu.

> [!NOTE]
> Pokud je úloha sestavení zapsána v jazyce .NET, například Visual C# nebo Visual Basic, a nepoužívá nativní prostředky nebo nástroje, bude spuštěna v libovolném cílovém kontextu bez přizpůsobení.

## <a name="usingtask-attributes-and-task-parameters"></a>Použití atributů úlohy a parametrů úlohy

Následující `UsingTask` atributy ovlivňují všechny operace úlohy v konkrétním procesu sestavení:

- Atribut, `Runtime` pokud je k dispozici, nastaví verzi CLR (COMMON Language runtime) `CLR4` `CurrentRuntime`a `*` může trvat některou z těchto hodnot: `CLR2`, , , nebo (libovolný runtime).

- `Architecture` Atribut, pokud je k dispozici, nastaví platformu a bitness `x86` `x64`a `CurrentArchitecture`může `*` trvat některou z těchto hodnot: , , , nebo (libovolná architektura).

- Atribut, `TaskFactory` pokud je k dispozici, nastaví továrnu úloh, která `TaskHostFactory`vytvoří a spustí instanci úlohy, a převezme pouze hodnotu . Další informace naleznete v [tématu Task továrny](#task-factories) dále v tomto dokumentu.

```xml
<UsingTask TaskName="SimpleTask"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />
```

Parametry `MSBuildRuntime` a `MSBuildArchitecture` můžete také použít k nastavení cílového kontextu jednotlivého úkolu.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

Před MSBuild spustí úlohu, hledá `UsingTask` odpovídající, který má stejný cílový kontext. Parametry, které jsou `UsingTask` zadány v, ale ne v odpovídající úloze jsou považovány za odpovídající. Parametry, které jsou zadány v `UsingTask` úkolu, ale ne v odpovídající, jsou také považovány za odpovídající. Pokud hodnoty parametrů nejsou zadány `UsingTask` v nebo úkolu, `*` hodnoty výchozí (libovolný parametr).

> [!WARNING]
> Pokud existuje `UsingTask` více než jeden `TaskName`a `Runtime`všechny `Architecture` mají odpovídající , a atributy, poslední, které mají být vyhodnoceny nahradí ostatní.

 Pokud jsou nastaveny parametry na úkolu, MSBuild pokusí `UsingTask` najít, který odpovídá těmto parametrům nebo alespoň není v konfliktu s nimi. Více než `UsingTask` jeden můžete určit cílový kontext stejného úkolu. Například úloha, která má různé spustitelné soubory pro různá cílová prostředí, se může podobat tomuto:

```xml
<UsingTask TaskName="MyTool"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MyToolsPath)\MyTool.v2.0.dll" />

<UsingTask TaskName="MyTool"
    Runtime="CLR4"
    Architecture="x86"
    AssemblyFile="$(MyToolsPath)\MyTool.4.0.dll" />

<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <MyTool MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>

```

## <a name="task-factories"></a>Továrny úkolů

Před spuštěním úlohy msbuild zkontroluje, zda je určen ke spuštění v aktuálním kontextu softwaru. Pokud je úloha takto určena, MSBuild předá do AssemblyTaskFactory, který jej spustí v aktuálním procesu; jinak MSBuild předá úlohu TaskHostFactory, který spustí úlohu v procesu, který odpovídá cílovému kontextu. I v případě, že aktuální kontext a cílový kontext odpovídají, můžete vynutit, aby úloha byla `TaskFactory` `TaskHostFactory`spuštěna mimo proces (z důvodů izolace, zabezpečení nebo z jiných důvodů) nastavením na .

```xml
<UsingTask TaskName="MisbehavingTask"
    TaskFactory="TaskHostFactory"
    AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">
</UsingTask>
```

## <a name="phantom-task-parameters"></a>Parametry fiktivní úlohy

Stejně jako všechny `MSBuildRuntime` ostatní `MSBuildArchitecture` parametry úlohy a lze nastavit z vlastností sestavení.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <FrameworkVersion>3.0</FrameworkVersion>
    </PropertyGroup>
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

Na rozdíl od `MSBuildRuntime` jiných `MSBuildArchitecture` parametrů úkolu a nejsou zřejmé na samotný úkol. Chcete-li napsat úlohu, která si je vědoma kontextu, ve kterém je spuštěna, musíte buď otestovat kontext voláním rozhraní .NET Framework, nebo použít vlastnosti sestavení k předání informací o kontextu prostřednictvím jiných parametrů úlohy.

> [!NOTE]
> `UsingTask`atributy lze nastavit ze sady nástrojů a vlastností prostředí.

`MSBuildRuntime` Parametry `MSBuildArchitecture` a poskytují nejflexibilnější způsob nastavení cílového kontextu, ale také nejomezenější rozsah. Na jedné straně, protože jsou nastaveny na samotné instanci úlohy a nejsou vyhodnoceny, dokud se úkol nechystá spustit, mohou odvodit svou hodnotu z úplného rozsahu vlastností, které jsou k dispozici v době vyhodnocení i sestavení. Na druhou stranu tyto parametry platí pouze pro konkrétní instanci úkolu v určitém cíli.

> [!NOTE]
> Parametry úlohy jsou vyhodnocovány v kontextu nadřazeného uzlu, nikoli v kontextu hostitele úlohy. Proměnné prostředí, které jsou závislé na běhu nebo architektuře (například umístění *Program Files),* vyhodnotí hodnotu, která odpovídá nadřazenému uzlu. Pokud je však stejná proměnná prostředí čtena přímo úlohou, bude správně vyhodnocena v kontextu hostitele úlohy.

## <a name="see-also"></a>Viz také

- [Konfigurace cílů a úkolů](../msbuild/configuring-targets-and-tasks.md)
