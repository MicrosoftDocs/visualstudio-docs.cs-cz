---
title: Řešení (. Sln) soubor
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f4eee1f0a5e8371d239b3c33d10e1d9d7998095
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705330"
---
# <a name="solution-sln-file"></a>Soubor řešení (.sln)

Řešení je struktura pro uspořádání projektů v sadě Visual Studio. Řešení udržuje informace o stavu pro projekty ve dvou souborech:

- Soubor .sln (textový, sdílený)

- Soubor .suo (binární možnosti řešení specifické pro uživatele)

Další informace o souborech .suo naleznete v [tématu Možnosti uživatele řešení (. Suo) Soubor](../../extensibility/internals/solution-user-options-dot-suo-file.md).

Pokud je váš VSPackage načten v důsledku odkazování v souboru <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> .sln, prostředí volá ke čtení v souboru .sln.

Soubor .sln obsahuje textové informace, které prostředí používá k vyhledání a načtení parametrů hodnoty názvu pro trvalá data a projekt VSPackages, na který odkazuje. Když uživatel otevře řešení, prostředí cyklicky prochází `preSolution`, `Project`a `postSolution` informace v souboru .sln načíst řešení, projekty v rámci řešení a všechny trvalé informace připojené k řešení.

Soubor každého projektu obsahuje další informace přečtené prostředím k naplnění hierarchie položkami tohoto projektu. Trvalosti dat hierarchie je řízena projektem. Data nejsou obvykle uložena v souboru .sln, i když můžete záměrně zapsat informace o projektu do souboru .sln, pokud se tak rozhodnete. Další informace o trvalosti naleznete v [tématu Persistence projektu](../../extensibility/internals/project-persistence.md) a [otevírání a ukládání položek projektu](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="file-header"></a>Záhlaví souboru

Záhlaví souboru .sln vypadá takto:

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Definice

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Standardní záhlaví, které definuje verzi formátu souboru.

`# Visual Studio 15`\
Hlavní verze sady Visual Studio, která (naposledy) uložila tento soubor řešení. Tyto informace řídí číslo verze v ikoně řešení.

`VisualStudioVersion = 15.0.26730.15`\
Plná verze sady Visual Studio, která (naposledy) uložila soubor řešení. Pokud je soubor řešení uložen novější verzí sady Visual Studio, která má stejnou hlavní verzi, tato hodnota není aktualizována tak, aby se snížila konve v souborech řešení.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Minimální (nejstarší) verze sady Visual Studio, která může otevřít tento soubor řešení.

::: moniker-end

::: moniker range=">=vs-2019"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio Version 16
VisualStudioVersion = 16.0.28701.123
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Definice

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Standardní záhlaví, které definuje verzi formátu souboru.

`# Visual Studio Version 16`\
Hlavní verze sady Visual Studio, která (naposledy) uložila tento soubor řešení. Tyto informace řídí číslo verze v ikoně řešení.

`VisualStudioVersion = 16.0.28701.123`\
Plná verze sady Visual Studio, která (naposledy) uložila soubor řešení. Pokud je soubor řešení uložen novější verzí sady Visual Studio, která má stejnou hlavní verzi, tato hodnota není aktualizována tak, aby se snížila konve v souboru.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Minimální (nejstarší) verze sady Visual Studio, která může otevřít tento soubor řešení.

::: moniker-end

## <a name="file-body"></a>Tělo souboru

Tělo souboru .sln se skládá z `GlobalSection`několika částí označených takto:

```
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
EndProject
Global
  GlobalSection(SolutionNotes) = postSolution
  EndGlobalSection
  GlobalSection(SolutionConfiguration) = preSolution
       ConfigName.0 = Debug
       ConfigName.1 = Release
  EndGlobalSection
  GlobalSection(ProjectDependencies) = postSolution
  EndGlobalSection
  GlobalSection(ProjectConfiguration) = postSolution
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86
  EndGlobalSection
  GlobalSection(ExtensibilityGlobals) = postSolution
  EndGlobalSection
  GlobalSection(ExtensibilityAddIns) = postSolution
  EndGlobalSection
EndGlobal
```

Chcete-li načíst řešení, prostředí provádí následující posloupnost úkolů:

1. Prostředí přečte globální část souboru .sln a `preSolution`zpracuje všechny označené oddíly . V tomto ukázkovém souboru existuje jeden takový příkaz:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Když prostředí přečte `GlobalSection('name')` značku, mapuje název na VSPackage pomocí registru. Název klíče by měl existovat v registru\\ pod [HKLM<Kořen registru ID aplikace\>\SolutionPersistence\AggregateGUID]. Výchozí hodnota klíčů je identifikátor GUID balíčku (REG_SZ) balíčku VSPackage, který položky napsal.

2. Prostředí načte VSPackage, `QueryInterface` volá VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> pro rozhraní a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> volá metodu s daty v části, takže VSPackage můžete uložit data. Prostředí tento proces opakuje `preSolution` pro každý oddíl.

3. Prostředí iterát prostřednictvím bloků trvalosti projektu. V tomto případě existuje jeden projekt.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Tento příkaz obsahuje jedinečný identifikátor GUID projektu a identifikátor GUID typu projektu. Tyto informace jsou používány prostředí mů e najít soubor projektu nebo soubory, které patří do řešení a VSPackage požadované pro každý projekt. Identifikátor GUID projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> je předán k načtení konkrétní VSPackage vztahující se k projektu, pak je projekt načten VSPackage. V tomto případě VSPackage, který je načten pro tento projekt je Visual Basic.

   Každý projekt může zachovat jedinečné ID instance projektu tak, aby k němu lze přistupovat podle potřeby jiných projektů v řešení. V ideálním případě pokud řešení a projekty jsou pod správou zdrojového kódu, cesta k projektu by měla být relativní k cestě k řešení. Při prvním načtení řešení nemohou být soubory projektu v počítači uživatele. Uložením souboru projektu na serveru vzhledem k souboru řešení je poměrně jednoduché, aby byl soubor projektu nalezen a zkopírován do počítače uživatele. Potom zkopíruje a načte zbývající soubory potřebné pro projekt.

4. Na základě informací obsažených v části projektu souboru .sln načte prostředí každý soubor projektu. Samotný projekt je pak zodpovědný za vyplnění hierarchie projektu a načítání všech vnořených projektů.

5. Po zpracování všech částí souboru .sln se řešení zobrazí v Průzkumníku řešení a je připraveno k úpravě uživatelem.

Pokud se nepodaří načíst jakýkoli VSPackage, který <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> implementuje projekt v řešení, je volána metoda a každý jiný projekt v řešení má možnost ignorovat změny, které mohly být provedeny během načítání. Pokud dojde k chybám analýzy, je u souborů řešení zachováno co nejvíce informací a prostředí zobrazí dialogové okno s upozorněním, že je řešení poškozeno.

Když je řešení uloženo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> nebo uzavřeno, metoda je volána a předána hierarchii, aby se zjistilo, zda byly provedeny změny řešení, které je třeba zadat do souboru .sln. Hodnota null předaná `QuerySaveSolutionProps` <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>do aplikace in označuje, že informace jsou pro řešení trvalé. Pokud hodnota není null, trvalé informace je pro konkrétní projekt, určuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> ukazatel na rozhraní.

Pokud je informace, které <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> mají být uloženy, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> rozhraní je volána s ukazatelem na metodu. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> je pak volána prostředím k načtení `IPropertyBag` dvojice název-hodnota z rozhraní a zapsat informace do souboru .sln.

`SaveSolutionProps`a `WriteSolutionProps` objekty jsou rekurzivně nazývány prostředím pro `IPropertyBag` načtení informací, které mají být uloženy z rozhraní, dokud nebudou všechny změny zadány do souboru .sln. Tímto způsobem můžete pojistit, že informace budou trvalé s řešením a k dispozici při příštím otevření řešení.

Každý načtený balíček VSPackage je uveden ve výčtu, aby se zjistilo, zda má něco uložit do souboru .sln. Je pouze v době načítání, že klíče registru jsou dotazovány. Prostředí ví o všech načtených balíčcích, protože jsou v paměti v době uložení řešení.

Pouze soubor .sln obsahuje `preSolution` položky v oddílech a. `postSolution` V souboru .suo nejsou žádné podobné oddíly, protože řešení potřebuje tyto informace správně načíst. Soubor .suo obsahuje možnosti specifické pro uživatele, jako jsou soukromé poznámky, které nejsou určeny ke sdílení nebo umístění pod správou zdrojového kódu.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [Soubor uživatelských možností řešení (.Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Řešení](../../extensibility/internals/solutions-overview.md)
