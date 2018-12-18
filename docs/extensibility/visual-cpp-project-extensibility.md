---
title: Rozšíření projektu Visual C++
ms.custom: ''
ms.date: 09/12/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 913ad2e785fcdb2067f89d0d4de2b250db40468b
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349673"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Visual Studio C++ systému sada nástrojů a rozšíření integrace s Project

*Systém projektu Visual C++* se používá pro soubory VCXPROJ. Je založen na [Common Project System (CPS) ve Visual Studio](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) a poskytuje další, rozšíření specifické pro C++ body pro snadnou integraci nové sady nástrojů, sestavení architektury a cílové platformy. 

## <a name="c-msbuild-targets-structure"></a>Struktura cíle nástroje MSBuild C++

Všechny soubory VCXPROJ importovat tyto soubory:

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Tyto soubory definují trochu samy o sobě. Místo toho importovat další soubory podle hodnoty těchto vlastností:

- `$(ApplicationType)`

   Příklady: Windows Store, Android, Linux

- `$(ApplicationTypeRevision)`

   Toto musí být platný řetězec verze, z formuláře: hlavní.dílčí[.sestavení[.revize]].

   Příklady: 1.0, 10.0.0.0

- `$(Platform)`

   Architektura sestavení s názvem "Platformy" z historických důvodů.

   Příklady: Win32, x86, x64 ARM   

- `$(PlatformToolset)`

   Příklady: v140 v141, v141_xp, kompilátor llvm

Hodnoty těchto vlastností zadat názvy složek v rámci `$(VCTargetsPath)` kořenové složky:

> `$(VCTargetsPath)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;*Typ aplikace*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Platformy*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`  
> &nbsp;&nbsp;&nbsp;&nbsp;Platformy\\&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(nepoužívá, pokud `$(ApplicationType)` je prázdné, pro projekty pro Windows Desktop)  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`  

### <a name="add-a-new-platform-toolset"></a>Přidat novou sadu nástrojů platformy

Chcete-li přidat novou sadu nástrojů, například "MyToolset" existující platformy Win32, vytvořit *MyToolset* ve složce `$(VCTargetsPath)`  *\\platformy\\Win32\\ PlatformToolsets\\*a vytvořit *Toolset.props* a *Toolset.targets* soubory.

Každý název složky v části *PlatformToolsets* se zobrazí v **vlastnosti projektu** dialogového okna jako dostupná **sada nástrojů platformy** pro danou platformu, jak je znázorněno zde:

![Sada nástrojů platformy vlastnost dialogové okno stránky vlastností projektu](media/vc-project-extensibility-platform-toolset-property.png "vlastnost sadu nástrojů platformy v dialogové okno stránky vlastností projektu")

Vytvoření podobné *MyToolset* složky a *Toolset.props* a *Toolset.targets* souborů v každé existující složce platformy Tato sada nástrojů podporuje.

### <a name="add-a-new-platform"></a>Přidat novou platformu

Pokud chcete přidat novou platformu, například "MyPlatform", vytvořte *MyPlatform* ve složce `$(VCTargetsPath)`  *\\platformy\\*a vytvořit  *Platform.default.props*, *Platform.props*, a *Platform.targets* soubory. Také vytvořit `$(VCTargetsPath)`  *\\platformy\\*<strong><em>MyPlatform</em></strong>*\\PlatformToolsets\\*  složky a vytvořte alespoň jednu sadu nástrojů v ní.

Všechny názvy složek v rámci *platformy* složku pro každý `$(ApplicationType)` a `$(ApplicationTypeRevision)` se zobrazí v integrovaném vývojovém prostředí, jak jsou k dispozici **platformy** voleb pro projekt.

![V dialogovém okně Nová platforma projektu novou volbu platformy](media/vc-project-extensibility-new-project-platform.png "New volbu platformy v dialogovém okně Nová platforma projektu")

### <a name="add-a-new-application-type"></a>Přidat nový typ aplikace

Chcete-li přidat nový typ aplikace, vytvořte *MyApplicationType* ve složce `$(VCTargetsPath)` *\\typ aplikace\\* a vytvořit *Defaults.props* soubor v ní. Alespoň jeden revize se vyžaduje pro typ aplikace, tak taky vytvořit `$(VCTargetsPath)`  *\\typ aplikace\\MyApplicationType\\1.0* složky a vytvořit  *Defaults.props* soubor v ní. Měli byste také vytvořit `$(VCTargetsPath)`  *\\ApplicationType\\MyApplicationType\\1.0\\platformy* složky a vytvořte alespoň jednu platformu v ní.

`$(ApplicationType)` a `$(ApplicationTypeRevision)` vlastnosti nejsou viditelné v uživatelském rozhraní. Tyto jsou definovány v šablonách projektů a nelze změnit po vytvoření projektu.


## <a name="the-vcxproj-import-tree"></a>Import stromu .vcxproj

Zjednodušené strom importy pro soubory cíle a vlastnosti Microsoft C++ vypadá takto:

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore*\\*výchozí*\\\*. *Vlastnosti*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Typ aplikace*\\`$(ApplicationType)`\\*Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Typ aplikace*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Typ aplikace*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*platformy* \\ `$(Platform)` \\  *Platform.default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter*\\*výchozí*\\\*. *Vlastnosti*  

Windows desktopové projekty nebudete definovat `$(ApplicationType)`, takže pouze import

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore*\\*výchozí*\\\*. *Vlastnosti*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Platformy*\\`$(Platform)`\\*Platform.default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter*\\*výchozí*\\\*. *Vlastnosti*  

Použijeme `$(_PlatformFolder)` vlastnost pro uchování `$(Platform)` umístění složek pro platformu. Tato vlastnost je 

> `$(VCTargetsPath)`\\*Platformy*\\`$(Platform)`

pro aplikace klasické pracovní plochy Windows a 

> `$(VCTargetsPath)`\\*Typ aplikace*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*platformy*\\`$(Platform)`

pro všechno ostatní.

Soubory vlastností se importují v tomto pořadí:

> `$(VCTargetsPath)`\\*Souboru Microsoft.Cpp.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*. *Vlastnosti*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets*\\`$(PlatformToolset)`\\*Toolset.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter*\\\*. *Vlastnosti*  

Soubory cíle importují v tomto pořadí:

> `$(VCTargetsPath)`\\*Microsoft.Cpp.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Current.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.TARGETS*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*. *cíle*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets*\\`$(PlatformToolset)`\\*Toolset.target*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter*\\\*. *cíle*  

Pokud je potřeba definovat některé výchozí vlastnosti pro vaši sadu nástrojů, můžete přidat soubory do příslušných složek ImportBefore a ImportAfter.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>Autor Toolset.props a Toolset.targets soubory

*Toolset.props* a *Toolset.targets* soubory mají plnou kontrolu nad co se stane během sestavení při použití této sady nástrojů. Můžete také řídit dostupné ladicí programy, některé z uživatelského rozhraní IDE, jako je třeba obsah v **stránky vlastností** dialogových oken a některé další aspekty chování projektu.

I když sadu nástrojů můžete přepsat proces celé sestavení, obvykle je vhodné vaši sadu nástrojů, úprava nebo přidání, že některé kroky sestavení nebo použít jiné sestavení nástroje, jako součást stávajícího procesu sestavení. K dosažení tohoto cíle, existuje mnoho běžných cíle a vlastnosti souborů, které vaši sadu nástrojů můžete importovat. V závislosti na tom, co má vaše sada nástrojů provedete tyto soubory mohou být užitečné používat jako imports nebo jako příklady:

- `$(VCTargetsPath)`\\*Microsoft.CppCommon.targets*

   Tento soubor definuje hlavních částí procesu sestavení nativní a také naimportuje:

   - `$(VCTargetsPath)`\\*Microsoft.CppBuild.targets*

   - `$(VCTargetsPath)`\\*Microsoft.BuildSteps.targets*

   - `$(MSBuildToolsPath)`\\*Cílů Microsoft.Common.Targets*

- `$(VCTargetsPath)`\\*Microsoft.Cpp.Common.props*

   Nastaví výchozí hodnoty pro sady nástrojů, použít kompilátory Microsoft a cílit na Windows.

- `$(VCTargetsPath)`\\*Microsoft.Cpp.WindowsSDK.props*

   Tento soubor Určuje umístění sady Windows SDK a definuje některé důležité vlastnosti pro aplikace určené pro Windows.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>Integrace nástrojů specifické cíle s výchozí proces sestavení C++ 

Výchozí proces sestavení C++ je definována v *Microsoft.CppCommon.targets*. Cíle, které existuje Nevolejte žádné nástroje konkrétního sestavení. Určí hlavní kroky, jejich pořadí sestavení a závislostí.

Sestavení C++ má tři hlavní kroky, které jsou znázorněny těchto cílů:

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

Protože každý krok sestavení mohou být provedeny nezávisle na sobě, cílech s v jednom kroku nelze spoléhat na skupiny položek a vlastnosti definované v cílech, na kterých běží jako součást jiné kroku. Toto rozdělení umožňuje určitá sestavení optimalizace výkonu. I když není použit ve výchozím nastavení, které dohlédněte na to, stále případném dalším sdílení dodržovat tato oddělení.

Tyto vlastnosti jsou ovládaná cíle, které jsou spouštěny v jednotlivých kroků:

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

Každý krok obsahuje také původní a nové identifikátory vlastnosti. 

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

Zobrazit *Microsoft.CppBuild.targets* souboru příklady cílů, které jsou zařazeny do jednotlivých kroků:

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

Pokud se podíváte na cíli, jako například `_ClCompile`, zobrazí se vám nic nedělají přímo samy o sobě, ale místo toho záviset na jiných cílů, včetně `ClCompile`:

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` a jiných sestavení nástrojově specifické cíle jsou definované jako prázdný cílů v *Microsoft.CppBuild.targets*:

```xml
<Target Name="ClCompile"/>
```

Vzhledem k tomu, `ClCompile` cíl je prázdný, není-li, že je přepsána sadu nástrojů, neprovede se žádná akce skutečných sestavení. Sada nástrojů cíle, které můžete přepsat `ClCompile` cíl, tedy mohou obsahovat jiné `ClCompile` definice po importu *Microsoft.CppBuild.targets*: 

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

Bez ohledu na jeho název, který byl vytvořen před provedením sady Visual Studio podporu pro různé platformy, `ClCompile` cíl nemá volat CL.exe. Pomocí příslušné úlohy nástroje MSBuild může také volat Clang, gcc nebo jinými kompilátory.

`ClCompile` Cíl by neměl mít všechny závislosti, s výjimkou `SelectClCompile` cíl, který je vyžadován pro kompilaci jednoho souboru příkazu pracovat v integrovaném vývojovém prostředí.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>Úlohy nástroje MSBuild pro použití v cíle sady nástrojů

Který má být vyvolán nástroj aplikace skutečný sestavení, je potřeba zavolat úlohu nástroje MSBuild cíl. Existuje základní [Exec – úloha](../msbuild/exec-task.md) , který umožňuje zadat příkazový řádek pro spuštění. Nástroje sestavení však obvykle mají mnoho možností, vstupy. a výstupy ke sledování pro přírůstkové sestavení, je vhodnější mít speciální úkoly pro ně. Například `CL` úloh výrazném CL.exe přepínače vlastnosti nástroje MSBuild, zapisuje je do souboru odpovědí a volá CL.exe. Také sleduje všechny vstupní a výstupní soubory pro později přírůstková sestavení. Další informace najdete v tématu [přírůstkového sestavení a Kontrola aktuálnosti](#incremental-build-and-up-to-date-check).

Microsoft.Cpp.Common.Tasks.dll implementuje tyto úlohy:

- `BSCMake`

- `CL`

- `ClangCompile` (přepínače clang gcc)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (jako je Exec, ale s vstupu a výstupu sledování)

- `SetEnv`

Pokud máte nástroj, který provede stejnou akci, jako je stávající nástroj, který má podobné přepínače příkazového řádku (stejně jako clang-cl a CL), stejné úlohy můžete použít u obou z nich.

Pokud je potřeba vytvořit nový úkol pro nástroj pro sestavení, můžete použít jednu z následujících možností:

1. Pokud pomocí této úlohy jen zřídka nebo několik sekund na mezerách nezáleží pro sestavení, můžete použít "vložené" úlohy nástroje MSBuild:

   - Úloha XAML (pravidla vlastního sestavení)

     Jedním z deklarace úlohy Xaml, naleznete v tématu `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.xml*a jeho použití, naleznete v tématu `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets*.

   - [Kód úlohy](../msbuild/msbuild-inline-tasks.md)

1. Pokud má lepší výkon úloh nebo jenom potřebujete složitější funkce, použijte regulární MSBuild [úkolů zápisu](../msbuild/task-writing.md) procesu.

   Pokud ne všechny vstupy a výstupy nástroje nejsou uvedeny na nástroj příkazového řádku, jako v `CL`, `MIDL`, a `RC` případech a pokud chcete automatické vstupní a výstupní soubor sledování a vytváření souborů .tlog, odvozovat vaše úlohy `Microsoft.Build.CPPTasks.TrackedVCToolTask`třídy. V současné době sice dokumentaci pro základ [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) třídy, neexistují žádné příklady nebo dokumentaci pro podrobnosti `TrackedVCToolTask` třídy. Pokud by to být zajímavé především, přidejte vašeho hlasu, jak na žádost na [developercommunity.visualstudio.com](https://developercommunity.visualstudio.com/spaces/62/index.html).

## <a name="incremental-builds-and-up-to-date-checks"></a>Přírůstková sestavení a aktuální kontroly

Přírůstkové sestavení nástroje MSBuild výchozí, zaměřuje použití `Inputs` a `Outputs` atributy. Je-li zadán, MSBuild volá cíl pouze v případě, že některý ze vstupních má novější časové razítko než všechny výstupy. Protože zdrojové soubory často zahrnout další soubory nebo ho importovat jiné výstupy v závislosti na možnostech nástroje sestavení nástroje produktu, je obtížné určit všechny možné vstupy a výstupy cíle nástroje MSBuild.

Ke správě tohoto problému, sestavení C++ používá jiné techniky pro podporu přírůstkové sestavení. Většina cílů nemáte zadejte vstupů a výstupů a v důsledku toho se vždycky spouštět během sestavení. Úlohy volány cíle zapisovat informace o všech vstupů a výstupů do *tlog* soubory, které mají příponu .tlog. Soubory .tlog používají novější sestavení ke kontrole co změnil a je třeba znovu sestavit a jaký je aktuální.

Pokud chcete zjistit všechny vstupy a výstupy, nativní nástroj úlohy používají tracker.exe a [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) třída poskytuje nástroj MSBuild.

Definuje Microsoft.Build.CPPTasks.Common.dll `TrackedVCToolTask` veřejné abstraktní základní třída. Většinu úloh, nástroj native jsou odvozeny z této třídy.

## <a name="tlog-files"></a>soubory .tlog

Existují tři typy souborů .tlog: *čtení*, *zápisu*, a *příkazového řádku*. Číst a zapisovat soubory .tlog se používají přírůstková sestavení a Kontrola aktuálnosti v integrovaném vývojovém prostředí. Soubory .tlog příkazového řádku se používají pouze v přírůstkových sestavení.

Nástroj MSBuild poskytuje tyto pomocné třídy ke čtení a zápisu .tlog soubory:

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

[FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) třídy lze použít pro přístup k čtení a zápis souborů .tlog a identifikovat vstupy, které jsou novější než výstupy, nebo pokud chybí výstup. Používá se v Kontrola aktuálnosti.

Příkazový řádek .tlog soubory obsahují informace o příkazové řádky v sestavení použity. Pouze používají se pro přírůstková sestavení, není aktuální kontrol, tak interní formát závisí na úkolu MSBuild, který vytvoří je.

Pokud .tlog soubory jsou vytvořeny úlohou, je nejvhodnější použít tyto pomocné třídy pro jejich vytvoření. Vzhledem k tomu, že Kontrola aktuálnosti výchozí nyní spoléhá výhradně na soubory .tlog, někdy je však pohodlnější k vytvoření v cíli bez úlohy. Můžete je zapsat pomocí `WriteLinesToFile` úloh. Zobrazit `_WriteMasmTlogs` target v `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets* jako příklad.

### <a name="read-tlog-format"></a>Formát .tlog pro čtení

*Čtení* .tlog soubory (\*.read.\*. tlog) obsahují informace o zdrojových souborů a jejich závislosti.

Stříšky (**^**) na začátku řádku určuje jeden nebo více zdrojů. Zdrojů, které sdílejí stejnou závislosti jsou oddělené symbolem svislá čára (**\|**).

Závislost soubory jsou uvedeny po zdrojů, každou na samostatném řádku. Všechny názvy souborů jsou úplné cesty.

Předpokládejme například, jsou součástí vašeho zdroje projektu *F:\\testování\\ConsoleApplication1\\ConsoleApplication1*. Pokud zdrojový soubor, *Class1.cpp*, má to zahrnuje,

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

pak bude *CL.read.1.tlog* soubor obsahuje zdrojový soubor, za nímž následuje jeho dvě závislosti:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

Není potřeba psát názvy souborů velkými písmeny, ale je praktické pro některé nástroje.

### <a name="write-tlog-format"></a>Zápis .tlog formátu

*Zápis* .tlog (\*.write.\*. soubory tlog určené) připojení zdroje a výstupy.

Stříšky (**^**) na začátku řádku určuje jeden nebo více zdrojů. Více zdrojů, které jsou oddělené symbolem svislá čára (**\|**).

Výstupní soubory vytvořené ze zdroje by měly být uvedeny po zdrojů, každou na samostatném řádku. Všechny názvy souborů musí být úplné cesty.

Například pro jednoduchý ConsoleApplication projekt, který má další zdrojový soubor *Class1.cpp*, *link.write.1.tlog* soubor může obsahovat:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>Sestavení doby návrhu

V integrovaném vývojovém prostředí .vcxproj projekty používají sadu cílů nástroje MSBuild, chcete-li získat další informace z projektu a znovu vygenerovat výstupní soubory. Některé tyto cíle se používají v sestavení při návrhu, ale mnohé z nich jsou použity v pravidelná sestavení a sestavení při návrhu.

Obecné informace o sestavení při návrhu, naleznete v dokumentaci CPS pro [sestavení doby návrhu](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Tato dokumentace je jenom částečně vztahují na projekty Visual C++.

`CompileDesignTime` a `Compile` cílů uvedených v době návrhu sestavení dokumentaci nespouštět pro projekty .vcxproj. Projekty Visual C++ .vcxproj různé cíle doby návrhu použít k získání informací technologie IntelliSense.

### <a name="design-time-targets-for-intellisense-information"></a>Cíle návrhu pro informace technologie IntelliSense

Cíle návrhu použít v projektech .vcxproj jsou definovány v `$(VCTargetsPath)` \\ *Microsoft.Cpp.DesignTime.targets*.

`GetClCommandLines` Shromažďuje target – možnosti kompilátoru pro IntelliSense:

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` – návrhu jenom pro cíle, vyžaduje se pro návrhové sestavení inicializace. Mimo jiné tyto cíle zakázat některé funkce regulárního sestavení ke zlepšení výkonu.

- `ComputeCompileInputsTargets` – Sada cílů, která upravuje – možnosti kompilátoru a položek. Tyto cíle spustit v době návrhu a běžné sestaveních.

Cíl volání `CLCommandLine` úkolu k vytvoření příkazového řádku pro nástroj IntelliSense. Bez ohledu na jeho název je znovu, můžete zpracovat nejen možností CL, ale také možnosti Clang a gcc. Typ přepínače kompilátoru řídí `ClangMode` vlastnost.

V současné době příkazového řádku vytvářených `CLCommandLine` úloh vždy používá přepínače CL (i v režimu Clang), protože můžete snadněji pro modul IntelliSense k analýze.

Pokud přidáváte cíl, který se spustí před kompilací, ať už regulární nebo návrhu, ujistěte se, že nedojde k narušení návrhových sestavení nebo mít vliv na výkon. Nejjednodušší způsob, jak otestovat cíle je otevřete příkazový řádek pro vývojáře a spusťte tento příkaz:

> Nástroj MSBuild /p:SolutionDir =*řešení directory s koncové-zpětné lomítko*; Konfigurace ladění; = Platforma = Win32; BuildingInsideVisualStudio = true; DesignTimebuild = true t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj

Tento příkaz vytváří protokolu podrobné sestavení, *msbuild.log*, výkonu shrnutí cíle a úlohy, který má na konci.

Ujistěte se, že používáte `Condition ="'$(DesignTimeBuild)' != 'true'"` ve všech operacích, které pouze dávají smysl pro pravidelná sestavení a ne pro sestavení při návrhu.

### <a name="design-time-targets-that-generate-sources"></a>Cíle návrhu, které generování zdroje

*Tato funkce je ve výchozím nastavení pro desktopové projekty nativní zakázané a se aktuálně nepodporuje v projektech v mezipaměti*.

Pokud `GeneratorTarget` metadat je definován pro položku projektu, cíl spuštění automaticky i při načtení projektu a při změně zdrojového souboru.

Například k automatickému generování .cpp a .h souborů z soubory .xaml `$(VSInstallDir)` \\ *MSBuild*\\*Microsoft* \\  *WindowsXaml*\\*v15.0*\\\*\\*Microsoft.Windows.UI.Xaml.CPP.Targets* tyto soubory definují entity:

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

Použití `Task.HostObject` neuložené obsah zdrojové soubory získat, by měly být zaregistrovány cíle a úlohy jako [MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017) pro danou projekty v pkgdef:

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Rozšíření projektu Visual C++ v integrovaném vývojovém prostředí sady Visual Studio

Systém projektu Visual C++ je založen na [systém projektu VS](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)a používá svůj body rozšiřitelnosti. Ale implementace hierarchie projektu je specifické pro Visual C++ a není založen na CPS, tak rozšíření hierarchie je omezená na položky projektu.

### <a name="project-property-pages"></a>Stránky vlastností projektu

Návrh obecné informace najdete v tématu [rozšiřitelnosti platformy – část 1](https://blogs.msdn.microsoft.com/vsproject/2009/06/09/platform-extensibility-part-1/) a [rozšiřitelnosti platformy – část 2](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/).

Jednoduše řečeno, stránky vlastností zobrazí ve **vlastnosti projektu** dialogové okno pro projekt jazyka C++, které jsou definovány pomocí *pravidlo* soubory. Soubor pravidel určuje sadu vlastností, které mají zobrazit na stránce vlastností je a jak a kde by měla být uložena v projektu soubor. Pravidlo soubory jsou soubory XML, které používají formát Xaml. Typy použité k serializaci je popsané v [Microsoft.Build.Framework.XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes). Další informace o použití pravidel soubory v projektech, naleznete v tématu [soubory XML stránky vlastností pravidla](/cpp/ide/property-page-xml-files).

Pravidlo soubory musí být přidány do `PropertyPageSchema` skupiny položek:

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` viditelnost pravidlo omezení metadat, což je také řídí typ pravidla a může mít jednu z těchto hodnot:

> `Project` | `File` | `PropertySheet`

Prohlášení CPS podporuje jiné hodnoty pro typ kontextu, nejsou však použity v projektech Visual C++.

Pokud toto pravidlo má být zobrazen ve více než jednom kontextu, použijte středníky (**;**) k oddělení místní hodnoty, jak je znázorněno zde:

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>Pravidla formátu a hlavní typy

Pravidla formátu je jednoduché, takže tato část popisuje pouze atributy, které ovlivňují, jak vypadá pravidlo v uživatelském rozhraní.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

`PageTemplate` Atribut definuje, jak se pravidlo zobrazilo v **stránky vlastností** dialogového okna. Atribut může mít jednu z těchto hodnot:


| Atribut | Popis |
|------------| - |
| `generic` | Všechny vlastnosti jsou zobrazeny na jedné stránce v části kategorie záhlaví<br/>Pravidlo může být viditelné pro `Project` a `PropertySheet` kontextů, ale ne `File`.<br/><br/> Příklad: `$(VCTargetsPath)` \\ *1033*\\*general.xml* |
| `tool` | Kategorie jsou uvedeny jako podstránky.<br/>Pravidlo může být viditelný ve všech kontextech: `Project`, `PropertySheet` a `File`.<br/>Toto pravidlo je viditelná ve vlastnostech projektu pouze v případě, že projekt obsahuje položky, které `ItemType` definované v `Rule.DataSource`, pokud je součástí názvu pravidla `ProjectTools` skupiny položek.<br/><br/>Příklad: `$(VCTargetsPath)` \\ *1033*\\*clang.xml* |
| `debugger` | Na stránce se zobrazí jako součást stránky ladění.<br/>Kategorie jsou aktuálně ignorovány.<br/>Název pravidla musí odpovídat objektu ladění MEF Spouštěč `ExportDebugger` atribut.<br/><br/>Příklad: `$(VCTargetsPath)` \\ *1033*\\*ladicí program\_místní\_windows.xml* |
| *custom* | Vlastní šablony. Název šablony by měl odpovídat `ExportPropertyPageUIFactoryProvider` atribut `PropertyPageUIFactoryProvider` objekt MEF. Zobrazit **Microsoft.VisualStudio.ProjectSystem.Designers.Properties.IPropertyPageUIFactoryProvider**.<br/><br/> Příklad: `$(VCTargetsPath)` \\ *1033*\\*userMacros.xml* |

Pokud toto pravidlo používá některé ze šablon na základě mřížky vlastností, můžete těmto rozšiřujícím bodům vlastností:

- [Editory hodnot vlastností](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [Zprostředkovatel hodnoty dynamického výčtu](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>Rozšíření pravidlo

Pokud chcete použít stávající pravidlo, ale muset přidat nebo odebrat (které se skrýt) několika vlastností, můžete vytvořit [pravidla pro rozšíření](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md).

#### <a name="override-a-rule"></a>Přepsat pravidla

Můžete chtít vaše sada nástrojů používat většinu výchozích pravidel projektu, ale nahrazuje jen jeden nebo několik z nich. Řekněme například, že chcete změnit pravidla C/C++ k zobrazení různých přepínačů. Zadejte nové pravidlo se stejným názvem a zobrazovaný název jako existující pravidlo a zahrnout jej do `PropertyPageSchema` skupiny položek po dokončení importu výchozí cpp cíle. Pouze jedno pravidlo se zadaným názvem se používá v projektu, a poslední součástí `PropertyPageSchema` položky skupiny wins.

#### <a name="project-items"></a>Položky projektu

*ProjectItemsSchema.xml* soubor definuje `ContentType` a `ItemType` hodnoty pro položky, které jsou považovány za položky projektu a definuje `FileExtension` prvků pro určení, které položky skupiny přidá nový soubor.

Je součástí výchozí soubor ProjectItemsSchema `$(VCTargetsPath)` \\ *1033*\\*ProjectItemsSchema.xml*. Rozšíření, musíte vytvořit soubor schématu s novým názvem, jako například *MyProjectItemsSchema.xml*:

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

V souboru cílů, zadejte:

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

Příklad: `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.xml*

### <a name="debuggers"></a>Ladicí programy

Ladění služby v sadě Visual Studio podporuje rozšiřitelnost ladicího stroje. Další informace najdete v tématu tyto ukázky:

- [MIEngine, opensourcový projekt, který podporuje lldb ladění](https://github.com/Microsoft/MIEngine)

- [Ukázku modul ladění pro Visual Studio](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

K určení ladicí stroj a další vlastnosti pro relaci ladění, je nutné implementovat [Spouštěč ladění](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) Komponenta MEF a přidejte `debugger` pravidlo. Příklad najdete v tématu `$(VCTargetsPath)` \\1033\\ladicí program\_místní\_windows.xml souboru.

### <a name="deploy"></a>Nasazení

projekty .vcxproj používají systém projektů Visual Studia rozšiřitelnosti pro [poskytovatele nasazení](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md).

### <a name="build-up-to-date-check"></a>Kontrola aktuálnosti sestavení

Ve výchozím nastavení, Kontrola aktuálnosti sestavení vyžaduje čtení .tlog a zapisovat soubory .tlog bude vytvořena ve `$(TlogLocation)` složky během sestavování pro všechna sestavení vstupy a výstupy.

Použití vlastní Kontrola aktuálnosti:

1. Zakázat kontrolu aktuálnosti výchozí tak, že přidáte `NoVCDefaultBuildUpToDateCheckProvider` funkce *Toolset.targets* souboru:

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. Implementovat vlastní [IBuildUpToDateCheckProvider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md).

## <a name="project-upgrade"></a>Upgrade projektu

### <a name="default-vcxproj-project-upgrader"></a>Výchozí .vcxproj projektu upgrader

Změny výchozích .vcxproj projektu upgrader `PlatformToolset`, `ApplicationTypeRevision`, sada nástrojů MSBuild verze a rozhraní .net framework. Poslední dva jsou vždy změní na výchozí hodnoty verze sady Visual Studio, ale `PlatformToolset` a `ApplicationTypeRevision` mohou být řízena speciální vlastnosti nástroje MSBuild.

Upgrader používá tato kritéria se rozhodnout, jestli je možné projekt upgradovat, nebo ne:

1. Pro projekty, které definují `ApplicationType` a `ApplicationTypeRevision`, zde je umístěna složka s vyšším číslem revize než aktuální.

1. Vlastnost `_UpgradePlatformToolsetFor_<safe_toolset_name>` jsou definovány pro aktuální sadu nástrojů, a její hodnota není rovna aktuální sady nástrojů.

   Tyto názvy vlastností  *\<safe_toolset_name >* představuje název sady nástrojů s všechny jiné než alfanumerické znaky podtržítkem (**\_**).

Když je možné upgradovat projekt, se podílí na *mění se cílení řešení*. Další informace najdete v tématu [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2).

Pokud chcete doplnění názvy projektů v **Průzkumníka řešení** při projekty použít konkrétní sadu nástrojů, definovat `_PlatformToolsetShortNameFor_<safe_toolset_name>` vlastnost.

Příklady `_UpgradePlatformToolsetFor_<safe_toolset_name>` a `_PlatformToolsetShortNameFor_<safe_toolset_name>` definice vlastností najdete v článku *Microsoft.Cpp.Default.props* souboru. Příklady využití naleznete v tématu `$(VCTargetPath)` \\ *Microsoft.Cpp.Platform.targets* souboru.

### <a name="custom-project-upgrader"></a>Vlastní upgrader

Použití vlastní upgrader objektu, implementujte jako Komponenta MEF, jak je znázorněno zde:

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

Kód můžete importovat a volání výchozí .vcxproj upgrader objekt:

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` je definován v *Microsoft.VisualStudio.ProjectSystem.VS.dll* se podobají těm `IVsRetargetProjectAsync`.

Definovat `VCProjectUpgraderObjectName` vlastnost říct systém projektu používat svůj vlastní upgrader objekt:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>Zakázat upgrade projektu

Chcete-li zakázat upgradem projektu, použijte `NoUpgrade` hodnotu:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>Mezipaměť projektů a rozšíření

Ke zlepšení výkonu při práci s velkými řešeními C++ v sadě Visual Studio 2017 [projektu mezipaměti](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/faster-c-solution-load-with-vs-15/) byla zavedena. Se implementuje jako databáze SQLite naplněný daty projektu a pak použije k načtení projektů bez projekty MSBuild nebo CPS načtení do paměti.

Vzhledem k tomu, že neexistují žádné objekty CPS k dispozici pro projekty .vcxproj načten z mezipaměti, komponent MEF rozšíření, který importovat `UnconfiguredProject` nebo `ConfiguredProject` nelze vytvořit. Pro podporu rozšiřitelnosti, mezipaměti projekt nepoužívá k sadě Visual Studio zjistí, zda projekt používá (nebo je pravděpodobně bude používat) MEF rozšíření.

Tyto typy projektů jsou vždy plně načtený a máte CPS objektů v paměti, takže všechna rozšíření MEF se vytvoří pro ně:

- Projekty po spuštění

- Projekty, které mají vlastní upgrader, to znamená, že definují `VCProjectUpgraderObjectName` vlastnost

- Projekty, které není cílit na plochu Windows, to znamená, že definují `ApplicationType` vlastnost

- Sdílet tento odkaz je pomocí importu projektů .vcxitems jakékoli projektů a položek projektů (.vcxitems).

Pokud nejsou zjištěny žádné z těchto podmínek, vytvoří se mezipaměť projektů. Mezipaměť obsahuje všechna data z projektu nástroje MSBuild potřebné k zodpovězení `get` dotazuje na `VCProjectEngine` rozhraní. To znamená, že všechny změny na vlastnosti nástroje MSBuild a úrovni souboru cílů provádí rozšíření by mělo fungovat jenom v projektech, které jsou načteny z mezipaměti.

## <a name="shipping-your-extension"></a>Přesouvání rozšíření

Informace o tom, jak vytvořit soubory VSIX, naleznete v tématu [přesouvání rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md). Informace o tom, jak přidat soubory do umístění instalace speciální, například můžete přidat soubory pod `$(VCTargetsPath)`, naleznete v tématu [instalace mimo složku rozšíření](../extensibility/set-install-root.md).

## <a name="additional-resources"></a>Další zdroje

Sestavovací systém Microsoft ([MSBuild](../msbuild/msbuild.md)) poskytuje modul sestavení a rozšiřitelné formát založený na formátu XML pro soubory projektu. Měli byste se seznámit s basic [koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md) a jak [MSBuild pro Visual C++](/cpp/build/msbuild-visual-cpp-overview) systém projektů funguje za účelem rozšíření Visual C++.

Rozhraní Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)) poskytuje rozšíření rozhraní API, které jsou používány CPS a systém projektu Visual C++. Přehled jak CPS používá rozhraní MEF, naleznete v tématu [CPS a MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) v [VSProjectSystem přehled MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md).

Můžete přizpůsobit existující systém sestavení pro přidání kroků sestavení nebo nové typy souborů. Další informace najdete v tématu [přehled nástroje MSBuild (Visual C++)](/cpp/build/msbuild-visual-cpp-overview) a [práce s vlastnostmi projektu](/cpp/ide/working-with-project-properties).
