---
title: 'Postupy: Konfigurace cílů a úloh | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe2955feb50a28e5ba631cdeddd169973a42ed25
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633886"
---
# <a name="how-to-configure-targets-and-tasks"></a>Postupy: Konfigurace cílů a úloh

Vybrané úlohy nástroje MSBuild je možné nastavit tak, aby běžely v prostředí, na které cílí, bez ohledu na prostředí vývojového počítače. Pokud například použijete 64 počítač k vytvoření aplikace, která se zaměřuje na 32 bitovou architekturu, vybrané úlohy se spustí v procesu 32.
Vybrané úlohy nástroje MSBuild je možné nastavit tak, aby běžely v prostředí, na které cílí, bez ohledu na prostředí vývojového počítače. Pokud například použijete 64 počítač k vytvoření aplikace, která se zaměřuje na 32 bitovou architekturu, vybrané úlohy se spustí v procesu 32.

> [!NOTE]
> Pokud je úloha sestavení napsána v jazyce .NET, jako je například C# vizuál nebo Visual Basic, a nepoužívá nativní prostředky nebo nástroje, bude spuštěna v jakémkoli cílovém kontextu bez přizpůsobení.

## <a name="usingtask-attributes-and-task-parameters"></a>Atributy UsingTask a parametry úlohy

Následující atributy `UsingTask` ovlivňují všechny operace úlohy v rámci určitého procesu sestavení:

- Atribut `Runtime`, je-li k dispozici, nastaví verzi modulu CLR (Common Language Runtime) a může přijmout jednu z těchto hodnot: `CLR2`, `CLR4`, `CurrentRuntime`nebo `*` (jakýkoli modul runtime).

- Atribut `Architecture`, pokud je k dispozici, nastaví platformu a bitová verze a může mít jednu z těchto hodnot: `x86`, `x64`, `CurrentArchitecture`nebo `*` (jakákoli architektura).

- Atribut `TaskFactory`, pokud je k dispozici, nastaví objekt pro vytváření úloh, který vytváří a spouští instanci úlohy a používá pouze hodnotu `TaskHostFactory`. Další informace najdete v tématu věnovaném [faktorům úloh](#task-factories) dále v tomto dokumentu.

```xml
<UsingTask TaskName="SimpleTask"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />
```

Pomocí parametrů `MSBuildRuntime` a `MSBuildArchitecture` můžete také nastavit cílový kontext jednotlivého úkolu.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

Předtím, než nástroj MSBuild spustí úlohu, vyhledá odpovídající `UsingTask`, která má stejný cílový kontext. Parametry, které jsou zadány v `UsingTask`, ale ne v odpovídající úloze, se považují za shodné. Parametry, které jsou zadané v úloze, ale ne v odpovídajícím `UsingTask`, se považují také za shodné. Pokud nejsou zadány hodnoty parametrů buď v `UsingTask`, nebo v úloze, hodnoty jsou ve výchozím nastavení `*` (libovolný parametr).

> [!WARNING]
> Pokud existuje více `UsingTask` a všechny mají stejné atributy `TaskName`, `Runtime`a `Architecture`, nahradí poslední vyhodnocenou druhou.

 Pokud jsou v úloze nastaveny parametry, MSBuild se pokusí najít `UsingTask`, který odpovídá těmto parametrům nebo, alespoň, není v konfliktu s nimi. Více než jeden `UsingTask` může určovat cílový kontext stejné úlohy. Například úloha, která má jiné spustitelné soubory pro různá cílová prostředí, může vypadat takto:

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

## <a name="task-factories"></a>Továrny úloh

Před spuštěním úlohy MSBuild zkontroluje, zda je určeno ke spuštění v aktuálním softwarovém kontextu. Pokud je úkol označen jako označený, nástroj MSBuild ho předá do AssemblyTaskFactory, který ho spustí v aktuálním procesu. v opačném případě nástroj MSBuild projde úlohu do TaskHostFactory, který úlohu spustí v procesu, který odpovídá cílovému kontextu. I v případě, že se aktuální kontext a cílový kontext shodují, můžete vynutit spuštění úlohy mimo proces (pro izolaci, zabezpečení nebo jiné důvody) nastavením `TaskFactory` na `TaskHostFactory`.

```xml
<UsingTask TaskName="MisbehavingTask"
    TaskFactory="TaskHostFactory"
    AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">
</UsingTask>
```

## <a name="phantom-task-parameters"></a>Parametry fiktivní úlohy

Stejně jako jakékoli jiné parametry úlohy `MSBuildRuntime` a `MSBuildArchitecture` lze nastavit z vlastností sestavení.

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

Na rozdíl od jiných parametrů úloh `MSBuildRuntime` a `MSBuildArchitecture` nejsou zjevným samotným úkolem. Chcete-li napsat úkol, který je informován o kontextu, ve kterém je spuštěn, je nutné otestovat kontext voláním .NET Framework, nebo pomocí vlastností sestavení předat kontextové informace prostřednictvím dalších parametrů úlohy.

> [!NOTE]
> atributy `UsingTask` lze nastavit z vlastností sady nástrojů a prostředí.

Parametry `MSBuildRuntime` a `MSBuildArchitecture` poskytují nejpružnější způsob, jak nastavit cílový kontext, ale také nejvíce omezený v rozsahu. Na jedné straně, protože se nastavují v samotné instanci úlohy a nejsou vyhodnocovány, dokud se úloha nespustí, může odvodit jejich hodnotu od úplného rozsahu vlastností dostupných jak v době hodnocení, tak i v době sestavení. Na druhé straně se tyto parametry vztahují pouze na konkrétní instanci úlohy v konkrétním cíli.

> [!NOTE]
> Parametry úlohy jsou vyhodnocovány v kontextu nadřazeného uzlu, nikoli v kontextu hostitele úkolu. Proměnné prostředí, které jsou závislé na architektuře nebo běhu (například umístění *programových souborů* ), se vyhodnotí na hodnotu, která odpovídá nadřazenému uzlu. Pokud je však stejná proměnná prostředí čtena přímo úlohou, bude vyhodnocena správně v kontextu hostitele úkolu.

## <a name="see-also"></a>Viz také

- [Konfigurace cílů a úloh](../msbuild/configuring-targets-and-tasks.md)
