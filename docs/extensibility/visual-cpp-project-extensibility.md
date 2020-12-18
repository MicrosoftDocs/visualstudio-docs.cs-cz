---
title: Rozšíření projektu Visual C++
ms.date: 04/23/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ba78ff7d38d993394072aa9dd18a7a8fa8cbb9d
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668700"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Rozšiřitelnost systému projektů Visual Studio C++ a integrace sady nástrojů

Systém projektu Visual C++ se používá pro soubory vcxproj. Vychází ze sady [Visual Studio Common Project System (CPS)](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) a poskytuje další body rozšiřitelnosti specifické pro C++ pro jednoduchou integraci nových sad nástrojů, architektur sestavení a cílových platforem.

## <a name="c-msbuild-targets-structure"></a>Struktura cílů C++ MSBuild

Všechny soubory vcxproj importují tyto soubory:

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Tyto soubory jsou definovány jen jednou. Místo toho importují jiné soubory na základě těchto hodnot vlastností:

- `$(ApplicationType)`

   Příklady: Windows Store, Android, Linux

- `$(ApplicationTypeRevision)`

   Musí se jednat o platný řetězec verze ve formátu hlavní. podverze [. sestavení [. Revize]].

   Příklady: 1,0, 10.0.0.0

- `$(Platform)`

   Architektura sestavení s názvem "platforma" z historických důvodů.

   Příklady: Win32, x86, x64, ARM

- `$(PlatformToolset)`

   Příklady: v140, v141, v141_xp, LLVM

Tyto hodnoty vlastností určují názvy složek v `$(VCTargetsPath)` kořenové složce:

> `$(VCTargetsPath)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;*Typ aplikace*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Platformu*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)` \
&nbsp;&nbsp;&nbsp;&nbsp;*Platformu*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`

`$(VCTargetsPath)` \\  \\ Složka platformy se používá v případě `$(ApplicationType)` , že je v projektech Windows Desktop prázdné.

### <a name="add-a-new-platform-toolset"></a>Přidat novou sadu nástrojů platformy

Chcete-li přidat novou sadu nástrojů, například "MyToolset" pro existující platformu Win32, vytvořte složku *MyToolset* v rámci `$(VCTargetsPath)` *\\ platforem \\ Win32 \\ PlatformToolsets \\* a v ní vytvořte sady *nástrojů. props* a *Sada nástrojů. targets* .

Každý název složky v rámci *PlatformToolsets* se zobrazí v dialogovém okně **Vlastnosti projektu** jako dostupná **Sada nástrojů platformy** pro zadanou platformu, jak je znázorněno zde:

![Vlastnost sady nástrojů platformy v dialogovém okně stránky vlastností projektu](media/vc-project-extensibility-platform-toolset-property.png "Vlastnost sady nástrojů platformy v dialogovém okně stránky vlastností projektu")

Vytvořte podobné složky *MyToolset* a sady *nástrojů. props* a *Sada nástrojů. targets* v každé existující složce platformy, kterou tato sada nástrojů podporuje.

### <a name="add-a-new-platform"></a>Přidat novou platformu

Pokud chcete přidat novou platformu, například "MyPlatform", vytvořte složku *MyPlatform* na `$(VCTargetsPath)` *\\ platformách \\* a vytvořte v ní soubory *Platform. default. props*, *Platform. props* a *Platform. targets* . Vytvořte také `$(VCTargetsPath)` složku <strong><em>MyPlatform</em></strong> *\\ platformy \\**\\ PlatformToolsets \\* a vytvořte v ní alespoň jednu sadu nástrojů.

Všechny názvy složek ve složce *Platforms* pro každý z nich `$(ApplicationType)` `$(ApplicationTypeRevision)` se zobrazí v integrovaném vývojovém prostředí (IDE) jako dostupné možnosti **platformy** pro projekt.

![Možnost nové platformy v dialogovém okně Nová platforma projektu](media/vc-project-extensibility-new-project-platform.png "Možnost nové platformy v dialogovém okně Nová platforma projektu")

### <a name="add-a-new-application-type"></a>Přidat nový typ aplikace

Chcete-li přidat nový typ aplikace, vytvořte  v nabídce `$(VCTargetsPath)` *\\ typ \\ aplikace* složku MyApplicationType a vytvořte v ní soubor *Defaults. props* . Pro typ aplikace je vyžadována aspoň jedna revize, proto vytvořte také `$(VCTargetsPath)` *\\ Typ aplikace \\ MyApplicationType \\ 1,0* a vytvořte v něm soubor *Defaults. props* . Měli byste také vytvořit složku `$(VCTargetsPath)` *\\ \\ \\ \\ platformy typu ApplicationType MyApplicationType 1,0* a vytvořit v ní alespoň jednu platformu.

`$(ApplicationType)` a `$(ApplicationTypeRevision)` vlastnosti nejsou v uživatelském rozhraní viditelné. Jsou definovány v šablonách projektů a nelze je změnit po vytvoření projektu.

## <a name="the-vcxproj-import-tree"></a>Strom importu. vcxproj

Zjednodušený strom importu pro soubory Microsoft C++ props a targets vypadá takto:

> `$(VCTargetsPath)`\\*Microsoft. cpp. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft. Common. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore* \\ *Výchozí hodnota* \\ \* . *props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Typ* \\ `$(ApplicationType)` aplikace \\ *Default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Typ* \\ `$(ApplicationType)` aplikace \\ `$(ApplicationTypeRevision)` \\ *Default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Typ* \\ `$(ApplicationType)` aplikace \\ `$(ApplicationTypeRevision)` \\  \\ `$(Platform)` Platformy \\ *Platform. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter* \\ *Výchozí hodnota* \\ \* . *props*

Projekty desktopových systémů Windows nedefinují `$(ApplicationType)` , takže importují pouze

> `$(VCTargetsPath)`\\*Microsoft. cpp. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft. Common. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore* \\ *Výchozí hodnota* \\ \* . *props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\ \\ `$(Platform)` Platformy \\ *Platform. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter* \\ *Výchozí hodnota* \\ \* . *props*

Vlastnost použijeme `$(_PlatformFolder)` pro uchovávání `$(Platform)` umístění složky platformy. Tato vlastnost je

> `$(VCTargetsPath)`\\*Platformu*\\`$(Platform)`

pro desktopové aplikace pro Windows a

> `$(VCTargetsPath)`\\*Typ* \\ `$(ApplicationType)` aplikace \\ `$(ApplicationTypeRevision)` \\ *Platformy*\\`$(Platform)`

pro všechno ostatní.

Soubory props jsou importovány v tomto pořadí:

> `$(VCTargetsPath)`\\*Microsoft. cpp. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Platform. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore* \\ \* . *props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\ \\ `$(PlatformToolset)` PlatformToolsets \\ *Sada nástrojů. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter* \\ \* . *props*

Soubory cílů jsou importovány v tomto pořadí:

> `$(VCTargetsPath)`\\*Microsoft. cpp. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Current. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Platform. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore* \\ \* . *cíle* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\ \\ `$(PlatformToolset)` PlatformToolsets \\ *Sada nástrojů. Target* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter* \\ \* . *cíle*

Pokud potřebujete definovat některé výchozí vlastnosti sady nástrojů, můžete přidat soubory do příslušných složek ImportBefore a ImportAfter.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>Vytváření sad nástrojů. props a sady nástrojů. targets

*Sada nástrojů. props* a *Sada nástrojů. targets* mají plnou kontrolu nad tím, co se stane během sestavení při použití této sady nástrojů. Mohou také řídit dostupné ladicí programy, některá z uživatelských rozhraní IDE, jako je například obsah v dialogovém okně **stránky vlastností** a některé další aspekty chování projektu.

I když může sada nástrojů přepsat celý proces sestavení, obvykle stačí, když chcete, aby sada nástrojů mohla upravovat nebo přidávat některé kroky sestavení, nebo použít jiné nástroje sestavení jako součást stávajícího procesu sestavení. K dosažení tohoto cíle je k dispozici několik běžných vlastností a cílů, které může vaše sada nástrojů importovat. V závislosti na tom, co má vaše sada nástrojů dělat, můžou být tyto soubory užitečné pro použití jako importu nebo jako příklady:

- `$(VCTargetsPath)`\\*Microsoft. CppCommon. targets*

  Tento soubor definuje hlavní části procesu nativního sestavení a také importuje:

  - `$(VCTargetsPath)`\\*Microsoft. CppBuild. targets*

  - `$(VCTargetsPath)`\\*Microsoft. BuildSteps. targets*

  - `$(MSBuildToolsPath)`\\*Microsoft. Common. targets*

- `$(VCTargetsPath)`\\*Microsoft. cpp. Common. props*

   Nastaví výchozí hodnoty pro sady nástrojů, které používají kompilátory a cílová okna společnosti Microsoft.

- `$(VCTargetsPath)`\\*Microsoft. cpp. WindowsSDK. props*

   Tento soubor určuje Windows SDK umístění a definuje některé důležité vlastnosti pro aplikace cílené na Windows.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>Integrujte cíle specifické pro sadu nástrojů s výchozím procesem sestavení C++.

Výchozí proces sestavení C++ je definován v *Microsoft. CppCommon. targets*. Cíle nevolají žádné konkrétní nástroje sestavení; určují hlavní kroky sestavení, jejich pořadí a závislosti.

Sestavení C++ obsahuje tři hlavní kroky, které jsou zastoupeny následujícími cíli:

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

Vzhledem k tomu, že každý krok sestavení může být proveden nezávisle, cíle běžící v jednom kroku se nemůžou spoléhat na skupiny položek a vlastnosti definované v cílích, které se spouštějí jako součást jiného kroku. Tato divize umožňuje určité optimalizace výkonu sestavení. I když se ve výchozím nastavení nepoužívá, stále doporučujeme toto oddělení akceptovat.

Cíle, které jsou spouštěny uvnitř každého kroku, jsou ovládány těmito vlastnostmi:

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

Každý krok také obsahuje vlastnosti před a po.

```xml
<Target
  Name="_BuildGenerateSourcesAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildGenerateSourcesTargets);$(BuildGenerateSourcesTargets);$(AfterBuildGenerateSourcesTargets)" />

<Target
  Name="\_BuildCompileAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildCompileTargets);$(BuildCompileTargets);$(AfterBuildCompileTargets)" />

<Target
  Name="\_BuildLinkAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildLinkTargets);$(BuildLinkTargets);$(AfterBuildLinkTargets)" />
```

Příklady cílů, které jsou zahrnuté v jednotlivých krocích, najdete v souboru *Microsoft. CppBuild. targets* :

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

Pokud se podíváte na cíle, například `_ClCompile` na, uvidíte, že nedělají nic přímo, ale jsou závislé na jiných cílech, včetně těchto `ClCompile` :

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` a další cíle specifické pro nástroj sestavení jsou definovány jako prázdné cíle v *Microsoft. CppBuild. targets*:

```xml
<Target Name="ClCompile"/>
```

Vzhledem k tomu `ClCompile` , že cíl je prázdný, pokud není přepsán sadou nástrojů, není provedena žádná skutečná akce sestavení. Cíle sady nástrojů mohou přepsat `ClCompile` cíl, to znamená, že mohou `ClCompile` po importu *Microsoft. CppBuild.* targets obsahovat jinou definici:

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

Bez ohledu na jeho název, který byl vytvořen před implementací podpory více platforem sady Visual Studio, nemusí `ClCompile` cíl volat CL.exe. Může také volat Clang, RSZ nebo jiné kompilátory pomocí příslušných úloh MSBuild.

`ClCompile`Cíl by neměl mít žádné závislosti s výjimkou `SelectClCompile` cíle, který je vyžadován pro použití příkazu kompilovat v jednom souboru pro práci v integrovaném vývojovém prostředí.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>Úlohy nástroje MSBuild pro použití v cílech sady nástrojů

Chcete-li vyvolat skutečný nástroj sestavení, musí cíl zavolat úlohu MSBuild. K dispozici je základní [Úloha Exec](../msbuild/exec-task.md) , která umožňuje zadat příkazový řádek, který se má spustit. Nástroje pro sestavení ale mají obvykle mnoho možností, vstupů. a výstupy, které se mají sledovat pro přírůstková sestavení, takže je lepší mít pro ně speciální úkoly. Například `CL` úloha překládá vlastnosti MSBuild do CL.exe přepínačů, zapisuje je do souboru odpovědí a volá CL.exe. Také sleduje všechny vstupní a výstupní soubory pro pozdější přírůstková sestavení. Další informace naleznete v tématu [přírůstková sestavení a kontroly aktuálnosti](#incremental-builds-and-up-to-date-checks).

Microsoft.Cpp.Common.Tasks.dll implementuje tyto úlohy:

- `BSCMake`

- `CL`

- `ClangCompile` (přepínače Clang-RSZ)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (jako je například exec, ale se sledováním vstupu a výstupu)

- `SetEnv`

- `GetOutOfDateItems`

Pokud máte nástroj, který provádí stejnou akci jako stávající nástroj a má podobné přepínače příkazového řádku (jako Clang-CL a CL), můžete pro oba z nich použít stejný úkol.

Pokud potřebujete vytvořit novou úlohu pro nástroj sestavení, můžete si vybrat z následujících možností:

1. Pokud tuto úlohu použijete zřídka nebo pokud nechcete, aby vaše sestavení nezáleží na několika sekundách, můžete použít úkoly v inlineu pro MSBuild:

   - Úloha XAML (pravidlo vlastního sestavení)

     Jeden příklad deklarace úlohy XAML naleznete v tématu `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *masm.xml* a pro jeho použití naleznete v tématu `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *MASM. targets*.

   - [Úloha kódu](../msbuild/msbuild-inline-tasks.md)

1. Pokud potřebujete lepší výkon úlohy nebo potřebujete komplexnější funkce, použijte pravidelný proces [zápisu úlohy](../msbuild/task-writing.md) MSBuild.

   Pokud nejsou všechny vstupy a výstupy nástroje uvedeny na příkazovém řádku nástroje, jako v případech, a, `CL` `MIDL` `RC` a pokud chcete automatické vstupní a výstupní soubory pro sledování a vytváření souborů. tlog, odvodíte od `Microsoft.Build.CPPTasks.TrackedVCToolTask` třídy úkol. V současné době existuje dokumentace pro základní třídu [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) , neexistuje žádné příklady ani dokumentace k podrobnostem `TrackedVCToolTask` třídy. Pokud by to bylo obzvláště důležité, přidejte svůj hlas k žádosti na [komunitu vývojářů](https://aka.ms/feedback/suggest?space=62).

## <a name="incremental-builds-and-up-to-date-checks"></a>Přírůstková sestavení a aktuální kontroly

Výchozí přírůstkové sestavení MSBuild cílí na použití `Inputs` a `Outputs` atributy. Pokud je zadáte, MSBuild volá cíl pouze v případě, že některé vstupy mají novější časové razítko než všechny výstupy. Vzhledem k tomu, že zdrojové soubory často zahrnují nebo importují jiné soubory a nástroje sestavení vytvářejí různé výstupy v závislosti na možnostech nástroje, je obtížné zadat všechny možné vstupy a výstupy v cílech MSBuild.

Pro správu tohoto problému používá sestavení C++ jinou techniku pro podporu přírůstkových sestavení. Většina cílů neurčuje vstupy a výstupy a v důsledku toho se vždy spustí během sestavení. Úkoly volané cíli zapisují informace o všech vstupech a výstupech do souborů *tlog* s příponou. tlog. Soubory. tlog jsou používány novějším sestavením pro kontrolu toho, co se změnilo a které musí být znovu sestavené a co je aktuální. Soubory. tlog jsou také jediným zdrojem pro výchozí kontrolu aktuálního sestavení v integrovaném vývojovém prostředí (IDE).

Chcete-li určit všechny vstupy a výstupy, úlohy nativních nástrojů používají tracker.exe a třídu [Tracker](/dotnet/api/microsoft.build.utilities.filetracker) poskytovanou nástrojem MSBuild.

Microsoft.Build.CPPTasks.Common.dll definuje `TrackedVCToolTask` veřejnou abstraktní základní třídu. Většina úloh nativního nástroje je odvozena z této třídy.

Počínaje verzí Visual Studio 2017 Update 15,8 můžete použít `GetOutOfDateItems` úlohu implementovanou v Microsoft.Cpp.Common.Tasks.dll k tvorbě souborů. tlog pro vlastní cíle se známými vstupy a výstupy.
Případně je můžete vytvořit pomocí `WriteLinesToFile` úlohy. Jako příklad se podívejte na `_WriteMasmTlogs` cíl v `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *MASM.* TARGETS.

## <a name="tlog-files"></a>soubory. tlog

Existují tři typy souborů. tlog: *čtení*, *zápis* a *příkazový řádek*. Čtení a zápis souborů. tlog jsou používány přírůstkovým sestavením a kontrolou aktuálnosti v integrovaném vývojovém prostředí (IDE). Soubory s příkazovým řádkem. tlog se používají pouze v přírůstkových sestaveních.

Nástroj MSBuild poskytuje tyto pomocné třídy pro čtení a zápis souborů. tlog:

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

Třída [FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) se dá použít pro přístup k souborům. tlog pro čtení i zápis a k identifikaci vstupů, které jsou novější než výstupy, nebo pokud chybí výstup. Používá se při kontrole aktuálního data.

Soubory tlog s příkazovým řádkem obsahují informace o příkazových řádcích použitých v sestavení. Používají se pouze pro přírůstková sestavení, nikoli pro aktuální kontroly, takže interní formát je určen úlohou MSBuild, která je vytváří.

### <a name="read-tlog-format"></a>Čtení. tlog – formát

*Čtení* souborů. tlog ( \* . Read. \* .. tlog) obsahují informace o zdrojových souborech a jejich závislostech.

Stříška ( **^** ) na začátku řádku označuje jeden nebo více zdrojů. Zdroje, které sdílejí stejné závislosti, jsou oddělené svislou čárou ( **\|** ).

Soubory závislostí jsou uvedeny za zdroji, každý na vlastním řádku. Všechny názvy souborů jsou úplné cesty.

Předpokládejme například, že se zdroje projektu nacházejí v *F: \\ Test \\ ConsoleApplication1 \\ ConsoleApplication1*. Pokud zdrojový soubor, *Class1. cpp*, obsahuje,

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

pak soubor *CL. Read. 1. tlog* obsahuje zdrojový soubor následovaný jeho dvěma závislostmi:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

Nevyžaduje zápis názvů souborů na velká písmena, ale je to pro některé nástroje pohodlí.

### <a name="write-tlog-format"></a>Zápis formátu. tlog

*Zapsat* . tlog ( \* . Write. \* .. tlog) soubory spojují zdroje a výstupy.

Stříška ( **^** ) na začátku řádku označuje jeden nebo více zdrojů. Více zdrojů je odděleno svislou čárou ( **\|** ).

Výstupní soubory sestavené ze zdrojů by měly být uvedeny po zdrojích, každý na vlastním řádku. Všechny názvy souborů musí být úplné cesty.

Například pro jednoduchý projekt ConsoleApplication, který má další zdrojový soubor *Class1. cpp*, může soubor *Link. Write. 1. tlog* obsahovat:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>Sestavení během návrhu

Projekty vcxproj v rozhraní IDE používají sadu cílů MSBuild pro získání dalších informací z projektu a pro opětovné generování výstupních souborů. Některé z těchto cílů se používají pouze při sestaveních v době návrhu, ale mnoho z nich je použito v pravidelných sestaveních i v sestaveních v době návrhu.

Obecné informace o sestaveních pro dobu návrhu najdete v dokumentaci k CPS pro [sestavení v době návrhu](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Tato dokumentace je k dispozici pouze částečně Visual C++ projektů.

`CompileDesignTime`Cíle a `Compile` uvedené v dokumentaci pro sestavení v době návrhu se pro projekty. vcxproj nespouštějí. Projekty Visual C++. vcxproj používají různé cíle návrhu k získání informací IntelliSense.

### <a name="design-time-targets-for-intellisense-information"></a>Cíle v době návrhu pro informace technologie IntelliSense

Cíle návrhu používané v projektech. vcxproj jsou definovány v `$(VCTargetsPath)` \\ *Microsoft. cpp. designtime. targets*.

`GetClCommandLines`Cíl shromažďuje možnosti kompilátoru pro technologii IntelliSense:

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` – cíle pouze při návrhu, které jsou požadovány pro inicializaci sestavení při návrhu. Mimo jiné tyto cíle zakazují některé běžné funkce sestavení pro zlepšení výkonu.

- `ComputeCompileInputsTargets` – sada cílů, které upraví možnosti kompilátoru a položky. Tyto cíle jsou spouštěny v době návrhu i v pravidelných sestaveních.

Cíl volá `CLCommandLine` úlohu k vytvoření příkazového řádku, který se má použít pro IntelliSense. Bez ohledu na jeho název se však může zpracovávat nejen možnosti CL, ale také možnosti Clang a RSZ. Typ přepínačů kompilátoru je řízen `ClangMode` vlastností.

V současné době příkazového řádku vytvořeného `CLCommandLine` úlohou vždy používá přepínače CL (dokonce i v režimu Clang), protože jsou pro modul IntelliSense snazší analyzovat.

Pokud přidáváte cíl, který se spustí před kompilací, bez ohledu na to, jestli je čas normálního nebo návrhu, ujistěte se, že neruší vytváření sestavení, nebo nemá vliv na výkon. Nejjednodušší způsob, jak otestovat cíl, je otevřít příkazový řádek pro vývojáře a spustit tento příkaz:

```
msbuild /p:SolutionDir=*solution-directory-with-trailing-backslash*;Configuration=Debug;Platform=Win32;BuildingInsideVisualStudio=true;DesignTimebuild=true /t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj
```

Tento příkaz vytvoří podrobný protokol sestavení, *MSBuild. log*, který obsahuje souhrn výkonu pro cíle a úkoly na konci.

Nezapomeňte použít `Condition ="'$(DesignTimeBuild)' != 'true'"` ve všech operacích, které mají smysl jenom pro běžná sestavení, a ne pro sestavení v době návrhu.

### <a name="design-time-targets-that-generate-sources"></a>Cíle návrhu, které generují zdroje

*Tato funkce je ve výchozím nastavení zakázána pro nativní projekty pro stolní počítače a není aktuálně podporována v projektech uložených v mezipaměti*.

Pokud `GeneratorTarget` jsou metadata definována pro položku projektu, cíl je spuštěn automaticky při načtení projektu a při změně zdrojového souboru.

::: moniker range="vs-2017"

Například pro automatické generování souborů. cpp nebo. h ze souborů. XAML, `$(VSInstallDir)` \\ soubory *MSBuild* \\ *Microsoft* \\ *WindowsXaml* \\ *v 15.0* \\ \* \\ *Microsoft. Windows. UI. XAML. cpp. targets* definují tyto entity:

::: moniker-end

::: moniker range=">=vs-2019"

Například pro automatické generování souborů. cpp nebo. h ze souborů. XAML, `$(VSInstallDir)` \\ soubory *MSBuild* \\ *Microsoft* \\ *WindowsXaml* \\ *v 16.0* \\ \* \\ *Microsoft. Windows. UI. XAML. cpp. targets* definují tyto entity:

::: moniker-end

```xml
<ItemDefinitionGroup>
  <Page>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </Page>
  <ApplicationDefinition>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </ApplicationDefinition>
</ItemDefinitionGroup>
<Target Name="DesignTimeMarkupCompilation">
  <!-- BuildingProject is used in Managed builds (always true in Native) -->
  <!-- DesignTimeBuild is used in Native builds (always false in Managed) -->
  <CallTarget Condition="'$(BuildingProject)' != 'true' Or $(DesignTimeBuild) == 'true'" Targets="DesignTimeMarkupCompilationCT" />
</Target>
```

Chcete-li použít `Task.HostObject` k získání neuloženého obsahu zdrojových souborů, cíle a úloha by měly být registrovány jako [MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017&preserve-view=true) pro dané projekty v pkgdef:

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Rozšíření projektu Visual C++ v integrovaném vývojovém prostředí sady Visual Studio

Systém projektu Visual C++ je založen na [systému projektů vs](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)a používá body rozšiřitelnosti. Implementace hierarchie projektu je však specifická pro Visual C++ a nikoli na základě CPS, takže rozšiřitelnost hierarchie je omezená na položky projektu.

### <a name="project-property-pages"></a>Stránky vlastností projektu

Obecné informace o návrhu najdete v tématu [cílení na více platforem pro projekty VC + +](https://devblogs.microsoft.com/visualstudio/framework-multi-targeting-for-vc-projects/).

Jednoduché výrazy, stránky vlastností, které se zobrazí v dialogovém okně **Vlastnosti projektu** pro projekt C++, jsou definovány pomocí souborů *pravidel* . Soubor pravidel určuje sadu vlastností, které se mají zobrazit na stránce vlastností, a jak a kde by měly být uloženy v souboru projektu. Soubory pravidel jsou soubory. XML, které používají formát XAML. Typy používané k jejich serializaci jsou popsány v tématu [Microsoft. Build. Framework. XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes). Další informace o použití souborů pravidel v projektech najdete v tématu soubory s [pravidly XML stránky vlastností](/cpp/build/reference/property-page-xml-files).

Do skupiny položek musí být přidány soubory pravidel `PropertyPageSchema` :

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` viditelnost pravidla omezení metadat, která je také řízená podle typu pravidla a může mít jednu z těchto hodnot:

`Project` | `File` | `PropertySheet`

Služba CPS podporuje pro typ kontextu jiné hodnoty, ale nepoužívají se v projektech Visual C++.

Pokud má být pravidlo viditelné ve více než jednom kontextu, použijte středník (**;**) k oddělení hodnot kontextu, jak je znázorněno zde:

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>Formát pravidla a hlavní typy

Formát pravidla je jednoduchý, takže v této části jsou uvedeny pouze atributy, které mají vliv na to, jak pravidlo vypadá v uživatelském rozhraní.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

`PageTemplate`Atribut definuje způsob zobrazení pravidla v dialogovém okně **stránky vlastností** . Atribut může mít jednu z těchto hodnot:

| Atribut | Popis |
|------------| - |
| `generic` | Všechny vlastnosti se zobrazují na jedné stránce v záhlavích kategorií.<br/>Pravidlo může být viditelné pro `Project` a `PropertySheet` kontexty, ale ne `File` .<br/><br/> Příklad: `$(VCTargetsPath)` \\ *1033* \\ *general.xml* |
| `tool` | Kategorie se zobrazují jako podstránky.<br/>Pravidlo může být viditelné ve všech kontextech: `Project` `PropertySheet` a `File` .<br/>Toto pravidlo je viditelné ve vlastnostech projektu pouze v případě, že projekt obsahuje položky s `ItemType` definovaným v `Rule.DataSource` , pokud není název pravidla zahrnutý ve `ProjectTools` skupině položek.<br/><br/>Příklad: `$(VCTargetsPath)` \\ *1033* \\ *clang.xml* |
| `debugger` | Stránka je zobrazena jako součást stránky ladění.<br/>Kategorie se aktuálně ignorují.<br/>Název pravidla by měl odpovídat atributu rozhraní MEF spouštěče spouštěcích objektů `ExportDebugger` .<br/><br/>Příklad: `$(VCTargetsPath)` \\  \\ *\_ místní \_windows.xmlladicího programu* 1033 |
| *Uživatelská* | Vlastní šablona. Název šablony by měl odpovídat `ExportPropertyPageUIFactoryProvider` atributu `PropertyPageUIFactoryProvider` objektu MEF. Viz **Microsoft. VisualStudio. ProjectSystem. Designers. Properties. IPropertyPageUIFactoryProvider**.<br/><br/> Příklad: `$(VCTargetsPath)` \\ *1033* \\ *userMacros.xml* |

Pokud pravidlo používá jednu z šablon založených na Gridech, může tyto body rozšiřitelnosti použít pro jeho vlastnosti:

- [Editory hodnot vlastností](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [Zprostředkovatel hodnot dynamického výčtu](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>Rozšíří pravidlo

Pokud chcete použít stávající pravidlo, ale potřebujete přidat nebo odebrat (tj. skrýt) pouze několik vlastností, můžete vytvořit [pravidlo rozšíření](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md).

#### <a name="override-a-rule"></a>Přepsat pravidlo

Možná budete chtít, aby sada nástrojů používala většinu výchozích pravidel projektu, ale aby nahradila pouze jeden nebo několik z nich. Řekněme například, že chcete změnit pouze pravidlo C/C++ pro zobrazení různých přepínačů kompilátoru. Můžete zadat nové pravidlo se stejným názvem a zobrazovaným názvem jako stávající pravidlo a zahrnout ho do `PropertyPageSchema` skupiny položek po importu výchozích cílů cpp. V projektu se používá jenom jedno pravidlo se zadaným názvem a ten poslední zahrnutý do `PropertyPageSchema` skupiny položek služba WINS.

#### <a name="project-items"></a>Položky projektu

*ProjectItemsSchema.xml* soubor definuje `ContentType` `ItemType` hodnoty a pro položky, které jsou považovány za položky projektu, a definuje `FileExtension` prvky pro určení, která skupina položek, do které se přidá nový soubor.

Výchozí soubor ProjectItemsSchema se nachází v `$(VCTargetsPath)` \\ *1033* \\ *ProjectItemsSchema.xml*. Pokud ho chcete zvětšit, musíte vytvořit soubor schématu s novým názvem, třeba *MyProjectItemsSchema.xml*:

```xml
<ProjectSchemaDefinitions xmlns="http://schemas.microsoft.com/build/2009/properties">

  <ItemType Name="MyItemType" DisplayName="C/C++ compiler"/>

  <ContentType
    Name="MyItems"
    DisplayName="My items"
    ItemType=" MyItemType ">
  </ContentType>

  <FileExtension Name=".abc" ContentType=" MyItems"/>

</ProjectSchemaDefinitions>
```

Pak do souboru cílů přidejte:

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

Příklad: `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *masm.xml*

### <a name="debuggers"></a>Ladicí programy

Služba ladění v aplikaci Visual Studio podporuje rozšiřitelnost ladicího stroje. Další informace najdete v těchto ukázkách:

- [MIEngine, open source projekt, který podporuje ladění lldb](https://github.com/Microsoft/MIEngine)

- [Ukázka ladicího stroje sady Visual Studio](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

Chcete-li určit moduly ladění a další vlastnosti pro relaci ladění, je nutné implementovat komponentu MEF pro [spouštěč ladění](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) a přidat `debugger` pravidlo. Příklad najdete v `$(VCTargetsPath)` \\ \\ souboru s ladicím programem 1033 pro \_ místní \_windows.xml.

### <a name="deploy"></a>Nasazení

projekty vcxproj používají rozšiřitelnost systému projektů sady Visual Studio pro [nasazení zprostředkovatelů](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md).

### <a name="build-up-to-date-check"></a>Sestavit aktuální kontrolu

Ve výchozím nastavení vyžaduje kontrolu aktuálnosti sestavení soubory Read. tlog a Write. tlog, které se mají vytvořit ve `$(TlogLocation)` složce během sestavování pro všechny vstupy a výstupy sestavení.

Použití vlastní kontroly v aktuálním stavu:

1. Zakažte výchozí kontrolu aktuálnosti přidáním `NoVCDefaultBuildUpToDateCheckProvider` funkce v souboru sady *nástrojů. targets* :

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. Implementujte vlastní [IBuildUpToDateCheckProvider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md).

## <a name="project-upgrade"></a>Upgrade projektu

### <a name="default-vcxproj-project-upgrader"></a>Výchozí. aplikace pro upgrade projektu vcxproj

Výchozí nástroj pro upgrade projektu vcxproj změní `PlatformToolset` , `ApplicationTypeRevision` , verze sady nástrojů MSBuild a rozhraní .NET Framework. Poslední dva jsou vždy změněny na výchozí hodnoty verze sady Visual Studio, ale `PlatformToolset` `ApplicationTypeRevision` lze je ovládat pomocí speciálních vlastností nástroje MSBuild.

Nástroj pro upgrade používá tato kritéria k rozhodnutí, zda je možné projekt upgradovat, nebo ne:

1. Pro projekty, které definují `ApplicationType` a `ApplicationTypeRevision` , existuje složka s vyšším číslem revize než aktuální.

1. Vlastnost `_UpgradePlatformToolsetFor_<safe_toolset_name>` je definována pro aktuální sadu nástrojů a její hodnota není rovna aktuální sadě nástrojů.

   V těchto názvech vlastností *\<safe_toolset_name>* představuje název sady nástrojů se všemi nealfanumerickými znaky, které jsou nahrazeny podtržítkem ( **\_** ).

Když je možné projekt upgradovat, je zapojen do změny *cíle řešení*. Další informace najdete v tématu [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2).

Pokud chcete názvy projektů v **Průzkumník řešení** , když projekty používají konkrétní sadu nástrojů, definujte `_PlatformToolsetShortNameFor_<safe_toolset_name>` vlastnost.

Příklady `_UpgradePlatformToolsetFor_<safe_toolset_name>` a `_PlatformToolsetShortNameFor_<safe_toolset_name>` definice vlastností naleznete v souboru *Microsoft. cpp. default. props* . Příklady použití naleznete v `$(VCTargetPath)` \\ souboru *Microsoft. cpp. Platform. targets* .

### <a name="custom-project-upgrader"></a>Vlastní upgrade projektu

Chcete-li použít vlastní objekt nástroje pro upgrade projektu, implementujte komponentu MEF, jak je znázorněno zde:

```csharp
/// </summary>
[Export("MyProjectUpgrader", typeof(IProjectRetargetHandler))]
[Export(typeof(IProjectRetargetHandler))]
[ExportMetadata("Name", "MyProjectUpgrader")]
[OrderPrecedence(20)]
[PartMetadata(ProjectCapabilities.Requires, ProjectCapabilities.VisualC)]

internal class MyProjectUpgrader: IProjectRetargetHandler
{
    // ...
}
```

Váš kód může importovat a volat výchozí objekt pro upgrade vcxproj:

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` je definován v *Microsoft.VisualStudio.ProjectSystem.VS.dll* a je podobný `IVsRetargetProjectAsync` .

Definujte `VCProjectUpgraderObjectName` vlastnost pro informování systému projektu, že má používat vlastní objekt nástroje pro upgrade:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>Zakázat upgrade projektu

Chcete-li zakázat upgrady projektu, použijte `NoUpgrade` hodnotu:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>Mezipaměť a rozšiřitelnost projektu

Pro zvýšení výkonu při práci s velkými řešeními C++ v aplikaci Visual Studio 2017 byla zavedena [mezipaměť projektu](https://devblogs.microsoft.com/cppblog/faster-c-solution-load-with-vs-15/) . Je implementována jako databáze SQLite naplněná daty projektu a pak použita k načtení projektů bez načtení projektů MSBuild nebo CPS do paměti.

Vzhledem k tomu, že nejsou k dispozici žádné objekty služby CPS pro projekty. vcxproj načtené z mezipaměti, komponenty MEF rozšíření, které importují `UnconfiguredProject` nebo `ConfiguredProject` nejdou vytvořit. Pro podporu rozšiřitelnosti se mezipaměť projektu nepoužívá, když aplikace Visual Studio zjistí, zda projekt používá rozšíření MEF (nebo je bude nejspíš používat).

Tyto typy projektů jsou vždy plně načteny a mají objekty CPS v paměti, takže jsou pro ně vytvořeny všechna rozšíření MEF:

- Projekty po spuštění

- Projekty, které mají vlastní upgrade projektu, to znamená, definují `VCProjectUpgraderObjectName` vlastnost

- Projekty, které necílí na okna stolních počítačů, to znamená, že definují `ApplicationType` vlastnost

- Projekty sdílených položek (. vcxitems) a všechny projekty, které na ně odkazují, importem projektů. vcxitems.

Pokud není zjištěna žádná z těchto podmínek, je vytvořena mezipaměť projektu. Mezipaměť obsahuje všechna data z projektu MSBuild vyžadovaného pro zodpovězení `get` dotazů na `VCProjectEngine` rozhraních. To znamená, že všechny úpravy na úrovni souborů MSBuild props a targets provedené rozšířením by měly fungovat pouze v projektech načtených z mezipaměti.

## <a name="shipping-your-extension"></a>Odeslání rozšíření

Informace o tom, jak vytvořit soubory VSIX, najdete v tématu dodávání [rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md). Informace o tom, jak přidat soubory do speciálních umístění instalace, například pro přidání souborů do `$(VCTargetsPath)` složky, najdete v tématu [instalace mimo složku rozšíření](../extensibility/set-install-root.md).

## <a name="additional-resources"></a>Další zdroje informací

Microsoft Build System ([MSBuild](../msbuild/msbuild.md)) poskytuje sestavovací modul a rozšiřitelný formát založený na XML pro soubory projektu. Měli byste být obeznámeni se základními [koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md) a s tím, jak nástroj [MSBuild pro Visual C++](/cpp/build/reference/msbuild-visual-cpp-overview) funguje pro rozšiřování Visual C++ho systému projektu.

Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)) poskytuje rozhraní API pro rozšíření, která používá CPS a systém Visual C++ch projektů. Přehled způsobu použití rozhraní MEF serverem CPS naleznete v tématu [CPS a MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) v [VSProjectSystem přehledu MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md).

Můžete přizpůsobit existující systém sestavení pro přidání kroků sestavení nebo nových typů souborů. Další informace naleznete v tématu [Přehled nástroje MSBuild (Visual C++)](/cpp/build/reference/msbuild-visual-cpp-overview) a [práce s vlastnostmi projektu](/cpp/build/working-with-project-properties).
