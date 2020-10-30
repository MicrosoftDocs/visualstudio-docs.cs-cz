---
title: Úloha ResolveAssemblyReference – | Microsoft Docs
description: Naučte se, jak MSBuild používá úlohu ResolveAssemblyReference – k určení všech sestavení, která závisí na zadaných sestaveních.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveAssemblyReference
- MSBuild.ResolveAssemblyReference.TurnOnAutoGenerateBindingRedirects
- MSBuild.ResolveAssemblyReference.FoundConflict
- MSBuild.ResolveAssemblyRedirects.SuggestedRedirects
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveAssemblyReference task [MSBuild]
- MSBuild, ResolveAssemblyReference task
ms.assetid: 4d56d848-b29b-4dff-86a2-0a96c9e4a170
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bccdc376079c4d9e0efb2a2724831e0fd2d0ae14
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048663"
---
# <a name="resolveassemblyreference-task"></a>ResolveAssemblyReference – úloha

Určuje všechna sestavení, která závisí na zadaných sestaveních, včetně `n` závislostí druhé a objednávky.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `ResolveAssemblyReference` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`AllowedAssemblyExtensions`|Volitelný `String[]` parametr.<br /><br /> Přípona názvu souboru sestavení, která se má použít při překladu odkazů. Výchozí přípony názvů souborů jsou *. exe* a *. dll* .|
|`AllowedRelatedFileExtensions`|Volitelný `String[]` parametr.<br /><br /> Přípony názvů souborů, které se mají použít pro hledání souborů, které jsou vzájemně propojené. Výchozí přípony jsou *. pdb* a *. XML* .|
|`AppConfigFile`|Volitelný `String` parametr.<br /><br /> Určuje *app.config* soubor, ze kterého se mají analyzovat a extrahovat mapování bindingRedirect. Pokud je tento parametr zadán, `AutoUnify` musí být parametr `false` .|
|`Assemblies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje položky, pro které musí být identifikovány úplné cesty a závislosti. Tyto položky můžou mít jednoduché názvy jako "System" nebo silné názvy jako "System, Version = 2.0.3500.0, Culture = neutral, PublicKeyToken = b77a5c561934e089".<br /><br /> Položky předané do tohoto parametru mohou volitelně mít následující metadata položky:<br /><br /> -   `Private`: `Boolean` Value. `true`V případě, že je položka zkopírována místně. Výchozí hodnota je `true`.<br />-   `HintPath`: `String` Value. Určuje cestu a název souboru, který se má použít jako odkaz. Tato metadata se používají, když je v parametru zadán parametr {HintPathFromItem} `SearchPaths` . Výchozí hodnota je prázdný řetězec.<br />-   `SpecificVersion`: `Boolean` Value. Pokud `true` je, musí přesně název zadaný v `Include` atributu odpovídat. Pokud `false` je, bude fungovat jakékoli sestavení se stejným jednoduchým názvem. Není `SpecificVersion` -li parametr zadán, úloha prověřuje hodnotu v `Include` atributu položky. Pokud je atribut jednoduchý název, chová se, jako kdyby `SpecificVersion` byl `false` . Pokud je atribut silným názvem, chová se, jako kdyby `SpecificVersion` byl `true` .<br />     Při použití s typem položky odkazu `Include` musí být atribut úplným názvem Fusion sestavení, které se má přeložit. Sestavení je vyřešeno pouze v případě, že Fusion přesně odpovídá `Include` atributu.<br />     Pokud je projekt cílen na verzi .NET Framework a odkazuje na sestavení zkompilované pro vyšší .NET Framework verzi, odkaz se vyřeší pouze v případě, že je `SpecificVersion` nastaven na hodnotu `true` .<br />     Když projekt cílí na profil a odkazuje na sestavení, které není v profilu, odkaz se vyřeší pouze v případě, že je `SpecificVersion` nastaven na `true` .<br />-   `ExecutableExtension`: `String` Value. Je-li k dispozici, přeložené sestavení musí mít toto rozšíření. V případě, že chybí, *Knihovna DLL* je považována za první a za každou z testovaných adresářů je následována *. exe* .<br />-   `SubType`: `String` Value. Pouze položky s prázdnými metadaty podtypu budou přeloženy do úplných cest sestavení. Položky s metadaty podtypu, která nejsou prázdná, se ignorují.<br />-   `AssemblyFolderKey`: `String` Value. Tato metadata jsou podporovaná pro starší účely. Určuje uživatelsky definovaný klíč registru, například **HKLM \\ \<VendorFolder>** , který `Assemblies` by měl používat k překladu odkazů na sestavení.|
|`AssemblyFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje seznam plně kvalifikovaných sestavení, pro která se mají najít závislosti.<br /><br /> Položky předané do tohoto parametru mohou volitelně mít následující metadata položky:<br /><br /> -   `Private`: volitelná `Boolean` hodnota. Je-li nastavena hodnota true, položka je zkopírována místně.<br />-   `FusionName`: volitelná `String` metadata. Určuje jednoduchý nebo silný název této položky. Pokud je tento atribut přítomen, může ušetřit čas, protože soubor sestavení není nutné otevřít pro získání názvu.|
|`AutoUnify`|Volitelný `Boolean` parametr.<br /><br /> Tento parametr se používá pro sestavování sestavení, jako jsou knihovny DLL, které nemohou mít normální *App.Config* soubor.<br /><br /> V takovém případě se `true` výsledný graf závislosti automaticky zpracuje, jako kdyby do parametru AppConfigFile byl předán soubor *App.Config* . Tento soubor virtuálního *App.Config* obsahuje záznam bindingRedirect pro každou konfliktní sadu sestavení tak, aby bylo zvoleno nejvyšší verze sestavení. V důsledku toho není nikdy upozornění na konfliktní sestavení, protože byl vyřešen každý konflikt.<br /><br /> `true`V případě, že každé odlišné přemapování, má za následek komentář s vysokou prioritou ukazující starou a novou `AutoUnify` verzi `true` .<br /><br /> `true`V případě, že parametr AppConfigFile musí být prázdný.<br /><br /> Při neproběhne `false` žádné přemapování verze sestavení automaticky. Pokud jsou k dispozici dvě verze sestavení, je vydáno upozornění.<br /><br /> `false`V případě, že každý rozdílový konflikt mezi různými verzemi stejného sestavení má za následek komentář s vysokou prioritou. Tyto komentáře jsou následovány jedním upozorněním. Upozornění má jedinečný kód chyby a obsahuje text, který čte "nalezené konflikty mezi různými verzemi referenčních a závislých sestavení".<br /><br /> Výchozí hodnota je `false`.|
|`CandidateAssemblyFiles`|Volitelný `String[]` parametr.<br /><br /> Určuje seznam sestavení, která se mají použít pro proces vyhledávání a rozlišení. Hodnoty předané do tohoto parametru musí být absolutní názvy souborů nebo názvy souborů relativní vzhledem k projektu.<br /><br /> Sestavení v tomto seznamu budou zvážena, pokud `SearchPaths` parametr obsahuje {CandidateAssemblyFiles} jako jednu z cest, které je třeba vzít v úvahu.|
|`CopyLocalDependenciesWhenParentReferenceInGac`|Volitelný <xref:System.Boolean> parametr.<br /><br /> Pokud je nastaveno na hodnotu true, chcete-li určit, zda má být závislost kopírována místně, je jednou z kontrol prováděna kontrola, zda nadřazený odkaz v souboru projektu má sadu privátních metadat. Je-li nastavena, pak se jako závislost používá soukromá hodnota.<br /><br /> Pokud metadata nejsou nastavena, pak závislost projde stejnými kontrolami jako nadřazený odkaz. Jedním z těchto kontrol zjistíte, jestli je odkaz v globální mezipaměti sestavení (GAC). Pokud je odkaz v globální mezipaměti sestavení (GAC), není zkopírován místně, protože se předpokládá, že je v globální mezipaměti sestavení (GAC) na cílovém počítači. To platí jenom pro konkrétní referenci a ne jeho závislosti.<br /><br /> Například odkaz v souboru projektu, který je v globální mezipaměti sestavení (GAC), není kopírován místně, ale jeho závislosti jsou kopírovány lokálně, protože nejsou v globální mezipaměti sestavení (GAC).<br /><br /> Je-li nastavena hodnota false, odkazy na soubory projektu jsou zkontrolovány, zda jsou v globální mezipaměti sestavení (GAC) a zkopírují se lokálně podle potřeby.<br /><br /> Závislosti jsou zkontrolovány, zda jsou v mezipaměti GAC a jsou také zkontrolovány, zda je nadřazený odkaz ze souboru projektu v globální mezipaměti sestavení (GAC).<br /><br /> Pokud je nadřazený odkaz ze souboru projektu v globální mezipaměti sestavení (GAC), závislost není kopírována místně.<br /><br /> Bez ohledu na to, zda je tento parametr true nebo false, pokud existuje více nadřazených odkazů a některé z nich nejsou v globální mezipaměti sestavení (GAC), jsou všechny z nich kopírovány místně.|
|`CopyLocalFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Vrátí všechny soubory v `ResolvedFiles` `ResolvedDependencyFiles` `RelatedFiles` parametrech,,, `SatelliteFiles` a `ScatterFiles` , které mají `CopyLocal` metadata položky s hodnotou `true` .|
|`FilesWritten`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje položky zapsané na disk.|
|`FindDependencies`|Volitelný `Boolean` parametr.<br /><br /> `true`V případě, že budou nalezeny závislosti. V opačném případě budou nalezeny pouze primární odkazy. Výchozí hodnota je `true`.|
|`FindRelatedFiles`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` budou nalezeny související soubory, jako jsou soubory *. pdb* a soubory *XML* . Výchozí hodnota je `true`.|
|`FindSatellites`|Volitelný `Boolean` parametr.<br /><br /> Pokud se `true` budou vyhledat satelitní sestavení. Výchozí hodnotou je `true.`.|
|`FindSerializationAssemblies`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` je, úloha vyhledá serializace sestavení. Výchozí hodnota je `true`.|
|`FullFrameworkAssemblyTables`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje položky, které mají metadata "FrameworkDirectory" k přidružení seznamu Redist k určitému adresáři rozhraní. Pokud se přidružení neprovede, zaprotokoluje se chyba. Logika překladu sestavení (RAR) používá cílový adresář rozhraní, pokud není nastaven FrameworkDirectory.|
|`FullFrameworkFolders`|Volitelný <xref:System.String?displayProperty=fullName> `[]` parametr.<br /><br /> Určuje složky, které obsahují adresář RedistList. Tento adresář představuje úplnou architekturu pro daný profil klienta, například *%programfiles%\Reference assemblies\microsoft\framework\v4.0* .|
|`FullTargetFrameworkSubsetNames`|Volitelný `String[]` parametr.<br /><br /> Obsahuje seznam názvů podmnožin cílových rozhraní. Pokud název podmnožiny v seznamu odpovídá jednomu ve `TargetFrameworkSubset` vlastnosti Name, pak systém vyloučí konkrétní cílovou sadu architektury v čase sestavení.|
|`IgnoreDefaultInstalledAssemblyTables`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , pak úloha vyhledá a použije další nainstalované tabulky sestavení (nebo, "seznamy Redist"), které se nacházejí v adresáři *\RedistList* pod `TargetFrameworkDirectories` . Výchozí hodnotou je `false.`.|
|`IgnoreDefaultInstalledAssemblySubsetTables`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , pak úloha vyhledá a použije další nainstalované tabulky podmnožiny sestavení (neboli "seznamy podmnožin"), které se nacházejí v adresáři *\SubsetList* pod `TargetFrameworkDirectories` . Výchozí hodnotou je `false.`.|
|`InstalledAssemblySubsetTables`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Obsahuje seznam souborů XML, které určují sestavení, která by měla být v cílové podmnožině.<br /><br /> Položky v tomto seznamu můžou jako možnost zadat metadata FrameworkDirectory k přidružení `InstalledAssemblySubsetTable`<br /><br /> se specifickým adresářem rozhraní.<br /><br /> Pokud je k dispozici pouze jeden `TargetFrameworkDirectories` prvek, pak všechny položky v tomto seznamu, u kterých chybí metadata "FrameworkDirectory", se považují za, i když jsou nastaveny na jedinečnou hodnotu, která je předána do `TargetFrameworkDirectories` .|
|`InstalledAssemblyTables`|Volitelný `String` parametr.<br /><br /> Obsahuje seznam souborů XML, které určují sestavení, která mají být nainstalována do cílového počítače.<br /><br /> Pokud `InstalledAssemblyTables` je nastavena, starší verze sestavení v seznamu jsou sloučeny do novější verze, které jsou uvedeny v souboru XML. Také sestavení, která mají nastavení InGAC = ' true ', se považují za požadavky a jsou nastavena na CopyLocal = ' false ', pokud není explicitně přepsána.<br /><br /> Položky v tomto seznamu můžou jako možnost zadat metadata "FrameworkDirectory" pro přidružení ke `InstalledAssemblyTable` konkrétnímu adresáři architektury.  Toto nastavení je však ignorováno, pokud název Redist začíná na<br /><br /> "Microsoft-Windows-CLRCoreComp".<br /><br /> Pokud je k dispozici pouze jeden `TargetFrameworkDirectories` prvek, pak všechny položky v tomto seznamu, které neobsahují metadata "FrameworkDirectory", se považují za, jako kdyby byly nastaveny na jedinečnou hodnotu, která je předána<br /><br /> na `TargetFrameworkDirectories` .|
|`LatestTargetFrameworkDirectories`|Volitelný `String[]` parametr.<br /><br /> Určuje seznam adresářů, které obsahují seznam Redist pro nejaktuálnější rozhraní, které může být na počítači cíleno. Není-li toto nastavení nastaveno, je použita nejvyšší architektura nainstalovaná na počítači pro daný identifikátor cílového rozhraní.|
|`ProfileName`|Volitelný `String` parametr.<br /><br /> – Určuje název profilu architektury, který se má cílit. Například klient, web nebo síť.|
|`RelatedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Obsahuje související soubory, jako jsou soubory XML a *PDB* , které mají stejný základní název jako odkaz.<br /><br /> Soubory uvedené v tomto parametru můžou volitelně obsahovat následující metadata položky:<br /><br /> -   `Primary`: `Boolean` Value. Pokud `true` je, položka souboru byla předána do pole pomocí `Assemblies` parametru. Výchozí hodnota je `false`.<br />-   `CopyLocal`: `Boolean` Value. Určuje, zda má být daný odkaz zkopírován do výstupního adresáře.|
|`ResolvedDependencyFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Obsahuje *n* -tou cestu objednávky ke závislostem. Tento parametr nezahrnuje primární odkazy první objednávky, které jsou obsaženy v `ResolvedFiles` parametru.<br /><br /> Položky v tomto parametru volitelně obsahují následující metadata položky:<br /><br /> -   `CopyLocal`: `Boolean` Value. Určuje, zda má být daný odkaz zkopírován do výstupního adresáře.<br />-   `FusionName`: `String` Value. Určuje název této závislosti.<br />-   `ResolvedFrom`: `String` Value. Určuje cestu pro vyhledávání literálů, ze které byl tento soubor přeložen.|
|`ResolvedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Obsahuje seznam všech primárních odkazů, které byly přeloženy na úplné cesty.<br /><br /> Položky v tomto parametru volitelně obsahují následující metadata položky:<br /><br /> -   `CopyLocal`: `Boolean` Value. Určuje, zda má být daný odkaz zkopírován do výstupního adresáře.<br />-   `FusionName`: `String` Value. Určuje název této závislosti.<br />-   `ResolvedFrom`: `String` Value. Určuje cestu pro vyhledávání literálů, ze které byl tento soubor přeložen.|
|`SatelliteFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Určuje, jaké satelitní soubory se našly. Toto budou CopyLocal = true, pokud odkaz nebo závislost, která způsobila, že tato položka existuje, je CopyLocal = true.<br /><br /> Položky v tomto parametru volitelně obsahují následující metadata položky:<br /><br /> -   `CopyLocal`: `Boolean` Value. Určuje, zda má být daný odkaz zkopírován do výstupního adresáře. Tato hodnota je `true` v případě, že odkaz nebo závislost, která způsobila, že tato položka existuje, má `CopyLocal` hodnotu `true` .<br />-   `DestinationSubDirectory`: `String` Value. Určuje relativní cílový adresář, do kterého se má zkopírovat tato položka.|
|`ScatterFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Obsahuje rozsévací soubory přidružené k jednomu z daných sestavení.<br /><br /> Položky v tomto parametru volitelně obsahují následující metadata položky:<br /><br /> -   `CopyLocal`: `Boolean` Value. Určuje, zda má být daný odkaz zkopírován do výstupního adresáře.|
|`SearchPaths`|Požadovaný parametr `String[]`.<br /><br /> Určuje adresáře nebo speciální umístění, ve kterých jsou prohledány soubory pro nalezení souborů na disku, které představují sestavení. Pořadí, ve kterém jsou uvedené cesty pro hledání, je důležité. Pro každé sestavení se seznam cest vyhledává zleva doprava. Když je nalezen soubor, který představuje sestavení, toto vyhledávání se zastaví a začne se hledat další sestavení.<br /><br /> Tento parametr přijímá seznam hodnot oddělených středníky, které mohou být buď cesty k adresáři, nebo speciální literálové hodnoty ze seznamu níže:<br /><br /> -   `{HintPathFromItem}`: Určuje, zda bude úkol kontrolovat `HintPath` metadata základní položky.<br />-   `{CandidateAssemblyFiles}`: Určuje, zda bude úloha prozkoumávat soubory předané prostřednictvím `CandidateAssemblyFiles` parametru.<br />-   `{Registry:`\<AssemblyFoldersBase>, \<RuntimeVersion> , \<AssemblyFoldersSuffix> `}` : Určuje, zda bude úkol Hledat v dalších složkách zadaných v registru. \<AssemblyFoldersBase>, \<RuntimeVersion> a \<AssemblyFoldersSuffix> by měl být nahrazen konkrétními hodnotami pro prohledávané umístění registru. Výchozí specifikace v běžných cílech je {Registry: $ (FrameworkRegistryBase), $ (TargetFrameworkVersion), $ (AssemblyFoldersSuffix), $ (AssemblyFoldersExConditions)}.<br />-   `{AssemblyFolders}`: Určuje, že úloha bude používat schéma Visual Studio.NET 2003 hledání-Assemblies-from-Registry.<br />-   `{GAC}`: Určuje, že úloha bude hledána v globální mezipaměti sestavení (GAC).<br />-   `{RawFileName}`: Určuje úlohu, která bude brát v úvahu, že `Include` hodnota položky bude odpovídat přesné cestě a názvu souboru.|
|`SerializationAssemblyFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Obsahuje všechna sestavení serializace XML. Tyto položky jsou označeny jako CopyLocal = true, pokud a pouze v případě, že odkaz nebo závislost, která způsobila, že tato položka existuje, je CopyLocal = true.<br /><br /> `Boolean`Metadata CopyLocal určují, zda má být daný odkaz zkopírován do výstupního adresáře.|
|`Silent`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` nejsou protokolovány žádné zprávy. Výchozí hodnota je `false`.|
|`StateFile`|Volitelný `String` parametr.<br /><br /> Určuje název souboru, který označuje, kam se má uložit zprostředkující stav sestavení pro tuto úlohu.|
|`SuggestedRedirects`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Obsahuje jednu položku pro každou rozdílnou identitu sestavení, bez ohledu na hodnotu `AutoUnify` parametru. To zahrnuje každou jazykovou verzi a hodnotu PKT, která byla nalezena, která neobsahovala vhodný záznam bindingRedirect v konfiguračním souboru aplikace.<br /><br /> Každá položka může volitelně obsahovat následující informace:<br /><br /> -   `Include` atribut: obsahuje úplný název řady sestavení s hodnotou pole verze 0.0.0.0.<br />-   `MaxVersion` metadata položky: obsahuje maximální číslo verze.|
|`TargetedRuntimeVersion`|Volitelný `String` parametr.<br /><br /> Určuje verzi modulu runtime, která má být cílena, například 2.0.57027 nebo v 2.0.57027.|
|`TargetFrameworkDirectories`|Volitelný `String[]` parametr.<br /><br /> Určuje cestu k cílovému adresáři rozhraní .NET Framework. Tento parametr je nutný k určení stavu CopyLocal pro výsledné položky.<br /><br /> Pokud tento parametr není zadán, žádné výsledné položky nebudou mít CopyLocal hodnotu, `true` Pokud explicitně nemají `Private` hodnotu metadata `true` na své zdrojové položce.|
|`TargetFrameworkMoniker`|Volitelný `String` parametr.<br /><br /> TargetFrameworkMoniker, který se má monitorovat, pokud existuje. Používá se k protokolování.|
|`TargetFrameworkMonikerDisplayName`|Volitelný `String` parametr.<br /><br /> Zobrazovaný název TargetFrameworkMonikeru, který se má monitorovat, pokud existuje. Používá se k protokolování.|
|`TargetFrameworkSubsets`|Volitelný `String[]` parametr.<br /><br /> Obsahuje seznam názvů podmnožin cílových rozhraní .NET Framework, které mají být prohledány v adresářích cílových rozhraní.|
|`TargetFrameworkVersion`|Volitelný `String` parametr.<br /><br /> Verze cílového rozhraní projektu. Výchozí hodnota je prázdná, což znamená, že neexistuje žádné filtrování pro odkazy založené na cílové architektuře.|
|`TargetProcessorArchitecture`|Volitelný `String` parametr.<br /><br /> Preferovaná architektura cílového procesoru. Používá se pro překládání odkazů na globální mezipaměť sestavení (GAC).<br /><br /> Tento parametr může mít hodnotu `x86` , `IA64` nebo `AMD64` .<br /><br /> Pokud tento parametr chybí, úloha nejprve posuzuje sestavení, která odpovídají architektuře aktuálně běžícího procesu. Pokud není nalezeno žádné sestavení, úloha posuzuje sestavení v globální mezipaměti sestavení (GAC), která mají `ProcessorArchitecture` hodnotu `MSIL` nebo žádnou `ProcessorArchitecture` hodnotu.|

## <a name="warnings"></a>Upozornění

 Protokolují se následující upozornění:

- `ResolveAssemblyReference.TurnOnAutoGenerateBindingRedirects`

- `ResolveAssemblyReference.SuggestedRedirects`

- `ResolveAssemblyReference.FoundConflicts`

- `ResolveAssemblyReference.AssemblyFoldersExSearchLocations`

- `ResolveAssemblyReference.UnifiedPrimaryReference`

- `ResolveAssemblyReference.PrimaryReference`

- `ResolveAssemblyReference.UnifiedDependency`

- `ResolveAssemblyReference.UnificationByAutoUnify`

- `ResolveAssemblyReference.UnificationByAppConfig`

- `ResolveAssemblyReference.UnificationByFrameworkRetarget`

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
