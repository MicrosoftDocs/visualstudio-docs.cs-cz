---
title: Řešení (. SLN) soubor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d9e045ab707620fe985e34174238081f6168e5af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154973"
---
# <a name="solution-sln-file"></a>Soubor řešení (.Sln)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Řešení je strukturou pro organizaci projektů v aplikaci Visual Studio. Řešení uchovává informace o stavu pro projekty v. sln (text-based, Shared) a. suo (binární možnosti řešení specifických pro uživatele). Další informace o souborech. suo najdete v tématu [Možnosti uživatele řešení (. Suo) soubor](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Pokud je vaše VSPackage načteno jako výsledek odkazován v souboru. sln, volání prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> pro čtení v souboru. sln.  
  
 Soubor. sln obsahuje textové informace, které prostředí používá k vyhledání a načtení parametrů název-hodnota pro trvalá data a projekt VSPackage, na které odkazuje. Když uživatel otevře řešení, prostředí projde do `preSolution` , `Project` a `postSolution` informace v souboru. sln, aby načetlo řešení, projekty v rámci řešení a všechny trvalé informace připojené k řešení.  
  
 Každý soubor projektu obsahuje další informace, které jsou čteny prostředím pro naplnění hierarchie s položkami tohoto projektu. Trvalost dat hierarchie řídí projekt; data nejsou obvykle uložena v souboru. sln, i když se rozhodnete k tomu, že můžete záměrně zapisovat informace o projektu do souboru. sln. Další informace o persistenci naleznete v tématu [trvalost projektu](../../extensibility/internals/project-persistence.md) a [otevírání a ukládání položek projektu](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="solution-file-contents"></a>Obsah souboru řešení  
 Soubor. sln se skládá z několika sekcí, jak je znázorněno v následujícím kódu.  
  
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
  
 K načtení řešení provede prostředí následující posloupnost úloh.  
  
1. Prostředí přečte globální část souboru. sln a zpracuje všechny oddíly označené `preSolution` . V tomto případě je k dispozici jeden z těchto příkazů:  
  
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
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Možnosti uživatele řešení (. Suo) soubor](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Řešení](../../extensibility/internals/solutions-overview.md)
