---
title: Řešení (. SLN) – soubor
description: Přečtěte si o souboru. sln, který je jedním ze souborů, které udržují informace o stavu projektu v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 903b33d72d3a97eb4ed3f7ad0bc865999bee54cf
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877504"
---
# <a name="solution-sln-file"></a>Soubor řešení (. sln)

Řešení je strukturou pro organizaci projektů v aplikaci Visual Studio. Řešení uchovává informace o stavu pro projekty ve dvou souborech:

- soubor. sln (text-based, Shared)

- . suo soubor (Binary, možnosti řešení specifické pro uživatele)

Další informace o souborech. suo najdete v tématu [Možnosti uživatele řešení (. Suo) soubor](../../extensibility/internals/solution-user-options-dot-suo-file.md).

Pokud je vaše VSPackage načteno jako výsledek odkazován v souboru. sln, volání prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> pro čtení v souboru. sln.

Soubor. sln obsahuje textové informace, které prostředí používá k vyhledání a načtení parametrů název-hodnota pro trvalá data a projekt VSPackage, na které odkazuje. Když uživatel otevře řešení, prostředí projde do `preSolution` , `Project` a `postSolution` informace v souboru. sln, aby načetlo řešení, projekty v rámci řešení a všechny trvalé informace připojené k řešení.

Každý soubor projektu obsahuje další informace, které jsou čteny prostředím pro naplnění hierarchie s položkami tohoto projektu. Trvalost dat hierarchie řídí projekt. Data nejsou obvykle uložena v souboru. sln, i když se rozhodnete k tomu, že můžete záměrně zapisovat informace o projektu do souboru. sln. Další informace o persistenci naleznete v tématu [trvalost projektu](../../extensibility/internals/project-persistence.md) a [otevírání a ukládání položek projektu](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="file-header"></a>Hlavička souboru

Záhlaví souboru. sln vypadá takto:

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Definice

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Standardní hlavička definující verzi formátu souboru.

`# Visual Studio 15`\
Hlavní verze sady Visual Studio, která (nedávno) uložila tento soubor řešení. Tyto informace řídí číslo verze v ikoně řešení.

`VisualStudioVersion = 15.0.26730.15`\
Plná verze sady Visual Studio, která (nedávno) uložila soubor řešení. Pokud je soubor řešení uložen v novější verzi sady Visual Studio, která má stejnou hlavní verzi, tato hodnota není aktualizována, aby bylo možné zmenšit změny v souborech řešení.

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
Standardní hlavička definující verzi formátu souboru.

`# Visual Studio Version 16`\
Hlavní verze sady Visual Studio, která (nedávno) uložila tento soubor řešení. Tyto informace řídí číslo verze v ikoně řešení.

`VisualStudioVersion = 16.0.28701.123`\
Plná verze sady Visual Studio, která (nedávno) uložila soubor řešení. Pokud je soubor řešení uložen v novější verzi sady Visual Studio, která má stejnou hlavní verzi, tato hodnota není aktualizována, aby bylo možné zmenšit změny v souboru.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Minimální (nejstarší) verze sady Visual Studio, která může otevřít tento soubor řešení.

::: moniker-end

## <a name="file-body"></a>Tělo souboru

Tělo souboru. sln se skládá z několika oddílů, které jsou označeny následujícím způsobem `GlobalSection` :

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

K načtení řešení provede prostředí následující posloupnost úloh:

1. Prostředí přečte globální část souboru. sln a zpracuje všechny oddíly označené `preSolution` . V tomto ukázkovém souboru je jeden takový příkaz:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Když prostředí přečte `GlobalSection('name')` značku, namapuje název na VSPackage pomocí registru. Název klíče by měl existovat v registru v části [HKLM \\<Application ID Registry root \> \SolutionPersistence\AggregateGUIDs]. Výchozí hodnota klíče je identifikátor GUID (REG_SZ) balíčku VSPackage, který zapsal tyto položky.

2. Prostředí načte VSPackage, volání `QueryInterface` rozhraní VSPackage pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> rozhraní a zavolá <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> metodu s daty v části tak, aby VSPackage mohla ukládat data. Prostředí Tento proces opakuje pro každý `preSolution` oddíl.

3. Prostředí projde bloky trvalosti projektu. V tomto případě je k dispozici jeden projekt.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Tento příkaz obsahuje jedinečný identifikátor GUID projektu a identifikátor GUID typu projektu. Tyto informace používá prostředí k vyhledání souboru projektu nebo souborů patřících do řešení a VSPackage vyžadovaného pro každý projekt. Identifikátor GUID projektu je předán pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> načtení konkrétní sady VSPackage týkající se projektu, poté je projekt načten rozhraním VSPackage. V tomto případě je Visual Basic rozhraní VSPackage načtené pro tento projekt.

   Každý projekt může zachovat jedinečné ID instance projektu tak, aby k němu měl mít k dispozici další projekty v řešení. V ideálním případě platí, že pokud řešení a projekty jsou pod správou zdrojového kódu, cesta k projektu by měla být relativní vzhledem k cestě k řešení. Při prvním načtení řešení se soubory projektu nemůžou nacházet v počítači uživatele. Díky tomu, že soubor projektu je uložen na serveru relativně vzhledem k souboru řešení, je relativně jednoduché pro nalezení souboru projektu a zkopírování do počítače uživatele. Pak zkopíruje a načte zbývající soubory potřebné pro projekt.

4. Na základě informací obsažených v části projektu v souboru. sln prostředí načte jednotlivé soubory projektu. Samotný projekt je pak zodpovědný za naplnění hierarchie projektu a načtení všech vnořených projektů.

5. Po zpracování všech sekcí souboru. sln je řešení zobrazeno v Průzkumník řešení a je připraveno k úpravám uživatelem.

Pokud se některý VSPackage, který implementuje projekt v řešení, nedokáže načíst, je <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> volána metoda a každý další projekt v řešení má možnost Ignorovat změny, které by mohly být provedeny během nasazování. Pokud dojde k chybám při analýze, co nejvíce informací je zachováno se soubory řešení a prostředí zobrazí upozornění uživatele, že je řešení poškozeno.

Když je řešení uloženo nebo uzavřeno, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> je metoda volána a předána hierarchii, aby bylo vidět, zda byly provedeny změny řešení, které je třeba zadat do souboru. sln. Hodnota null, která byla předána do `QuerySaveSolutionProps` v <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> , označuje, že informace jsou pro řešení trvalé. Pokud hodnota není null, jsou trvalé informace určeny pro konkrétní projekt, určené ukazatelem na <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> rozhraní.

Pokud existují informace, které mají být uloženy, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> rozhraní je voláno s ukazatelem na <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> metodu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>Metoda je pak volána prostředím, aby načetla páry název-hodnota z `IPropertyBag` rozhraní a zapsaly informace do souboru. sln.

`SaveSolutionProps` a `WriteSolutionProps` objekty jsou rekurzivním voláním prostředí, aby bylo možné načíst informace, které mají být uloženy z `IPropertyBag` rozhraní, dokud všechny změny nebyly zadány do souboru. sln. Tímto způsobem si můžete ověřit, že informace budou trvale uložené v řešení a budou dostupné při příštím otevření řešení.

Každý načtený VSPackage je vyhodnocen, aby bylo možné zjistit, zda obsahuje cokoli k uložení do souboru. sln. Je k dispozici pouze v době načtení, která je dotazována na klíče registru. Prostředí ví o všech načtených balíčcích, protože jsou v paměti v okamžiku uložení řešení.

Pouze soubor. sln obsahuje položky v `preSolution` `postSolution` částech a. V souboru. suo nejsou žádné podobné oddíly, protože řešení potřebuje k tomu, aby se tyto informace správně načetly. Soubor. suo obsahuje možnosti specifické pro uživatele, například soukromé poznámky, které nemají být sdíleny nebo umístěny v rámci správy zdrojového kódu.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [Soubor uživatelských možností řešení (.Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Řešení](../../extensibility/internals/solutions-overview.md)
