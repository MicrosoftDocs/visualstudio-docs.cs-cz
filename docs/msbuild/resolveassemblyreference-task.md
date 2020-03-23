---
title: Úkol ResolveAssemblyReference | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: b79bd8eb3f7d813e3acd091ce5f2ffbc7b3eeb49
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632755"
---
# <a name="resolveassemblyreference-task"></a>ResolveAssemblyReference – úloha

Určuje všechna sestavení, která závisí na zadaných `n`sestaveních, včetně závislostí druhého a druhého řádu.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `ResolveAssemblyReference` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`AllowedAssemblyExtensions`|Volitelný `String[]` parametr.<br /><br /> Přípony názvů souborů sestavení, které se mají použít při řešení odkazů. Výchozí přípony názvů souborů jsou *EXE* a *DLL*.|
|`AllowedRelatedFileExtensions`|Volitelný `String[]` parametr.<br /><br /> Přípony názvů souborů, které mají být používány pro hledání souborů, které spolu souvisejí. Výchozí rozšíření jsou *.pdb* a *XML*.|
|`AppConfigFile`|Volitelný `String` parametr.<br /><br /> Určuje soubor *app.config,* ze kterého chcete analyzovat a extrahovat vazbyMapování přesměrování. Pokud je tento parametr `AutoUnify` zadán, `false`musí být parametr .|
|`Assemblies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje položky, pro které musí být identifikovány úplné cesty a závislosti. Tyto položky mohou mít jednoduché názvy jako "Systém" nebo silné názvy jako "System, Version=2.0.3500.0, Culture=neutral, PublicKeyToken=b77a5c561934e089".<br /><br /> Položky předané tomuto parametru mohou mít volitelně následující metadata položky:<br /><br /> -   `Private`: `Boolean` hodnota. Pokud `true`se položka zkopíruje místně. Výchozí hodnota je `true`.<br />-   `HintPath`: `String` hodnota. Určuje cestu a název souboru, který má být používán jako odkaz. Tato metadata se používají, když je v `SearchPaths` parametru zadán {HintPathFromItem}. Výchozí hodnota je prázdný řetězec.<br />-   `SpecificVersion`: `Boolean` hodnota. Pokud `true`se musí shodovat přesný název zadaný v atributu. `Include` Pokud `false`, pak jakékoli sestavení se stejným jednoduchým názvem bude fungovat. Pokud `SpecificVersion` není zadán, pak úkol zkontroluje `Include` hodnotu v atributu položky. Pokud je atribut jednoduchý název, chová se, jako by `SpecificVersion` byl `false`. Pokud je atribut silný název, chová se, jako by `SpecificVersion` byl `true`.<br />     Při použití s typem `Include` reference položky, atribut musí být úplný název fúze sestavení, které mají být vyřešeny. Sestavení je vyřešenpouze v případě, že fúze přesně odpovídá atributu. `Include`<br />     Pokud projekt cílí na verzi rozhraní .NET Framework a odkazuje na sestavení zkompilované pro `SpecificVersion` vyšší `true`verzi rozhraní .NET Framework, odkaz se vyřeší pouze v případě, že má nastaveno .<br />     Pokud projekt cílí na profil a odkazuje na sestavení, které není v `SpecificVersion` profilu, `true`odkaz se vyřeší pouze v případě, že má nastaveno .<br />-   `ExecutableExtension`: `String` hodnota. Pokud je k dispozici, musí mít vyřešené sestavení toto rozšíření. Pokud chybí, *.dll* je považován za první, následovaný *.exe*, pro každý zkoumaný adresář.<br />-   `SubType`: `String` hodnota. Do úplných cest sestavení budou vyřešeny pouze položky s prázdnými metadaty podtypu. Položky s neprázdnými metadaty podtypu jsou ignorovány.<br />-   `AssemblyFolderKey`: `String` hodnota. Tato metadata jsou podporována pro starší účely. Určuje uživatelem definovaný klíč registru, například **hklm\\\<VendorFolder>**, který `Assemblies` by měl použít k vyřešení odkazů na sestavení.|
|`AssemblyFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje seznam plně kvalifikovaných sestavení, pro které chcete najít závislosti.<br /><br /> Položky předané tomuto parametru mohou mít volitelně následující metadata položky:<br /><br /> -   `Private`: volitelná `Boolean` hodnota. Pokud true, položka je zkopírován místně.<br />-   `FusionName`: `String` volitelná metadata. Určuje jednoduchý nebo silný název této položky. Pokud je tento atribut přítomen, může ušetřit čas, protože soubor sestavení nemusí být otevřen, aby získal název.|
|`AutoUnify`|Volitelný `Boolean` parametr.<br /><br /> Tento parametr se používá pro vytváření sestavení, jako jsou například knihovny DLL, které nemohou mít normální soubor *App.Config.*<br /><br /> Když `true`je výsledný graf závislostí automaticky zpracován, jako by byl soubor *App.Config* předán parametru AppConfigFile. Tento virtuální *soubor App.Config* má vazbuRedirect položka pro každou konfliktní sadu sestavení tak, aby byla vybrána nejvyšší verze sestavení. Důsledkem toho je, že nikdy nebude varování o konfliktních sestaveních, protože každý konflikt bude vyřešen.<br /><br /> Když `true`bude mít každé odlišné přemapování za následek komentář s vysokou `AutoUnify` `true`prioritou, který zobrazuje starou a novou verzi a to bylo .<br /><br /> Když `true`musí být parametr AppConfigFile prázdný.<br /><br /> Když `false`nedojde k přemapování verze sestavení automaticky. Pokud jsou k dispozici dvě verze sestavení, je vydáno upozornění.<br /><br /> Když `false`každý odlišný konflikt mezi různými verzemi stejného sestavení má za následek komentář s vysokou prioritou. Po těchto komentářích následuje jediné upozornění. Upozornění obsahuje jedinečný kód chyby a obsahuje text, který čte "Nalezeno konflikty mezi různými verzemi odkazu a závislých sestavení".<br /><br /> Výchozí hodnota je `false`.|
|`CandidateAssemblyFiles`|Volitelný `String[]` parametr.<br /><br /> Určuje seznam sestavení, která mají být pro proces hledání a překladu používána. Hodnoty předané tomuto parametru musí být absolutní názvy souborů nebo názvy souborů relativní k projektu.<br /><br /> Sestavení v tomto seznamu budou `SearchPaths` považována za jednu z cest, které je třeba zvážit, pokud parametr obsahuje {CandidateAssemblyFiles}.|
|`CopyLocalDependenciesWhenParentReferenceInGac`|Volitelný <xref:System.Boolean> parametr.<br /><br /> Pokud true, chcete-li zjistit, zda závislost by měla být zkopírována místně, jeden z kontrol udělat, je zjistit, zda nadřazený odkaz v souboru projektu má soukromé metadata set. Pokud set, pak Private hodnota se používá jako závislost.<br /><br /> Pokud metadata není nastavena, pak závislost prochází stejné kontroly jako nadřazený odkaz. Jedním z těchto kontrol je zjistit, zda je odkaz v GAC. Pokud je odkaz v GAC, pak není zkopírován místně, protože se předpokládá, že je v GAC na cílovém počítači. To platí pouze pro konkrétní odkaz a nikoli jeho závislosti.<br /><br /> Například odkaz v souboru projektu, který je v GAC není zkopírován místně, ale jeho závislosti jsou zkopírovány místně, protože nejsou v GAC.<br /><br /> Pokud false, odkazy na soubor projektu jsou kontrolovány, zda jsou v GAC a jsou zkopírovány místně podle potřeby.<br /><br /> Závislosti jsou kontrolovány, zda jsou v GAC a jsou také kontrolovány, zda je nadřazený odkaz ze souboru projektu v GAC.<br /><br /> Pokud je nadřazený odkaz ze souboru projektu v GAC, závislost není zkopírována místně.<br /><br /> Zda je tento parametr true nebo false, pokud existuje více nadřazené odkazy a některý z nich nejsou v GAC, pak všechny z nich jsou zkopírovány místně.|
|`CopyLocalFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Vrátí každý soubor `ResolvedFiles` `ResolvedDependencyFiles`v `RelatedFiles` `SatelliteFiles`, `ScatterFiles` , a `CopyLocal` parametry, které mají `true`metadata položky s hodnotou .|
|`FilesWritten`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje položky zapsané na disk.|
|`FindDependencies`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`budou nalezeny závislosti. V opačném případě jsou nalezeny pouze primární odkazy. Výchozí hodnota je `true`.|
|`FindRelatedFiles`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`budou nalezeny související soubory, například soubory *PDB* a soubory *XML.* Výchozí hodnota je `true`.|
|`FindSatellites`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`budou nalezena satelitní sestavení. Výchozí hodnotou je `true.`.|
|`FindSerializationAssemblies`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, pak úloha hledá sestavení serializace. Výchozí hodnota je `true`.|
|`FullFrameworkAssemblyTables`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje položky, které mají metadata "FrameworkDirectory" pro přidružení seznamu redist s určitým adresářem architektury. Pokud přidružení není provedeno, bude zaznamenána chyba. Logika odkazu na sestavení resolve (RAR) používá adresář cílového rozhraní, pokud není nastaven a FrameworkDirectory.|
|`FullFrameworkFolders`|Volitelný <xref:System.String?displayProperty=fullName> `[]` parametr.<br /><br /> Určuje složky, které obsahují adresář RedistList. Tento adresář představuje úplnou architekturu pro daný profil klienta, například *%programfiles%\reference assemblies\microsoft\framework\v4.0*.|
|`FullTargetFrameworkSubsetNames`|Volitelný `String[]` parametr.<br /><br /> Obsahuje seznam názvů podmnožiny cílové architektury. Pokud název podmnožiny v seznamu `TargetFrameworkSubset` odpovídá názvu ve vlastnosti name, pak systém vyloučí tuto konkrétní podmnožinu cílového rozhraní v době sestavení.|
|`IgnoreDefaultInstalledAssemblyTables`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`úkol vyhledá a použije další nainstalované tabulky sestavení (neboli "Redist Lists"), které se nacházejí `TargetFrameworkDirectories`v adresáři *\RedistList* pod . Výchozí hodnotou je `false.`.|
|`IgnoreDefaultInstalledAssemblySubsetTables`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`úkol vyhledá a použije další nainstalované tabulky podmnožiny sestavení (nebo "Podmnožiny), které `TargetFrameworkDirectories`se nacházejí v adresáři *\SubsetList* pod . Výchozí hodnotou je `false.`.|
|`InstalledAssemblySubsetTables`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Obsahuje seznam souborů XML, které určují sestavení, u kterých se očekává, že budou v cílové podmnožině.<br /><br /> Jako možnost mohou položky v tomto seznamu určit metadata "FrameworkDirectory", která přidruží`InstalledAssemblySubsetTable`<br /><br /> s konkrétním rámcovým adresářem.<br /><br /> Pokud existuje pouze `TargetFrameworkDirectories` jeden prvek, pak všechny položky v tomto seznamu, které postrádají metadata "FrameworkDirectory" jsou `TargetFrameworkDirectories`považovány za jsou nastaveny na jedinečnou hodnotu, která je předána .|
|`InstalledAssemblyTables`|Volitelný `String` parametr.<br /><br /> Obsahuje seznam souborů XML, které určují sestavení, u kterých se očekává instalace v cílovém počítači.<br /><br /> Je-li `InstalledAssemblyTables` nastavena, starší verze sestavení v seznamu jsou sloučeny do novějšíverze, které jsou uvedeny v XML. Sestavení, které mají nastavení InGAC ='true' jsou považovány za předpoklady a jsou nastaveny na CopyLocal ='false' pokud explicitně přepsána.<br /><br /> Jako možnost položky v tomto seznamu můžete zadat "FrameworkDirectory" metadata přidružit k `InstalledAssemblyTable` určitému adresáři rozhraní framework.  Toto nastavení je však ignorováno, pokud název redistu nezačíná<br /><br /> "Microsoft-Windows-CLRCoreComp".<br /><br /> Pokud existuje pouze `TargetFrameworkDirectories` jeden prvek, jsou všechny položky v tomto seznamu, které postrádají metadata "FrameworkDirectory", považovány za nastavené na jedinečnou hodnotu, která je předána<br /><br /> až `TargetFrameworkDirectories`.|
|`LatestTargetFrameworkDirectories`|Volitelný `String[]` parametr.<br /><br /> Určuje seznam adresářů, které obsahují seznamy redist pro nejaktuálnější rámec, který může být zaměřen na počítač. Pokud to není nastaveno, pak se používá nejvyšší rámec nainstalovaný v počítači pro daný identifikátor cílové ho rozhraní.|
|`ProfileName`|Volitelný `String` parametr.<br /><br /> - Určuje název profilu rozhraní, na který má být cílit. Například Klient, Web nebo Síť.|
|`RelatedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Obsahuje související soubory, například soubory XML a *PDB,* které mají stejný základní název jako odkaz.<br /><br /> Soubory uvedené v tomto parametru mohou volitelně obsahovat následující metadata položky:<br /><br /> -   `Primary`: `Boolean` hodnota. Pokud `true`, pak byla položka souboru předána do pole pomocí parametru. `Assemblies` Výchozí hodnota `false`je .<br />-   `CopyLocal`: `Boolean` hodnota. Označuje, zda má být daný odkaz zkopírován do výstupního adresáře.|
|`ResolvedDependencyFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Obsahuje *n*cesty pořadí k závislostem. Tento parametr nezahrnuje primární odkazy prvního řádu, `ResolvedFiles` které jsou obsaženy v parametru.<br /><br /> Položky v tomto parametru volitelně obsahují následující metadata položky:<br /><br /> -   `CopyLocal`: `Boolean` hodnota. Označuje, zda má být daný odkaz zkopírován do výstupního adresáře.<br />-   `FusionName`: `String` hodnota. Určuje název této závislosti.<br />-   `ResolvedFrom`: `String` hodnota. Určuje cestu hledání literálu, ze které byl tento soubor vyřešen.|
|`ResolvedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Obsahuje seznam všech primárních odkazů vyřešených na úplné cesty.<br /><br /> Položky v tomto parametru volitelně obsahují následující metadata položky:<br /><br /> -   `CopyLocal`: `Boolean` hodnota. Označuje, zda má být daný odkaz zkopírován do výstupního adresáře.<br />-   `FusionName`: `String` hodnota. Určuje název této závislosti.<br />-   `ResolvedFrom`: `String` hodnota. Určuje cestu hledání literálu, ze které byl tento soubor vyřešen.|
|`SatelliteFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Určuje všechny nalezené satelitní soubory. Ty budou CopyLocal=true, pokud je odkaz nebo závislost, která způsobila existenci této položky, CopyLocal=true.<br /><br /> Položky v tomto parametru volitelně obsahují následující metadata položky:<br /><br /> -   `CopyLocal`: `Boolean` hodnota. Označuje, zda má být daný odkaz zkopírován do výstupního adresáře. Tato hodnota `true` je, pokud odkaz nebo závislost, která `CopyLocal` způsobila existenci této položky má hodnotu `true`.<br />-   `DestinationSubDirectory`: `String` hodnota. Určuje relativní cílový adresář, do kterýchcete tuto položku zkopírovat.|
|`ScatterFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Obsahuje soubory bodový přidružené k jednomu z daných sestavení.<br /><br /> Položky v tomto parametru volitelně obsahují následující metadata položky:<br /><br /> -   `CopyLocal`: `Boolean` hodnota. Označuje, zda má být daný odkaz zkopírován do výstupního adresáře.|
|`SearchPaths`|Požadovaný parametr `String[]`.<br /><br /> Určuje adresáře nebo zvláštní umístění, která jsou prohledána za účelem vyhledání souborů na disku, které představují sestavení. Je důležité pořadí, ve kterém jsou uvedeny vyhledávací cesty. Pro každé sestavení je seznam cest prohledán zleva doprava. Při hledání souboru, který představuje sestavení, se hledání zastaví a spustí se hledání dalšího sestavení.<br /><br /> Tento parametr přijímá seznam hodnot oddělených středníkem, který může být buď cestami adresáře, nebo speciálními literálovými hodnotami z následujícího seznamu:<br /><br /> -   `{HintPathFromItem}`: Určuje, že úloha `HintPath` zkontroluje metadata základní položky.<br />-   `{CandidateAssemblyFiles}`: Určuje, že úloha zkontroluje soubory `CandidateAssemblyFiles` předané parametrem.<br />-   `{Registry:`\<AssemblyFoldersBase>, \<RuntimeVersion \<>, AssemblyFoldersSuffix>`}`: Určuje, že úloha bude prohledávat další složky zadané v registru. \<AssemblyFoldersBase>, \<RuntimeVersion \<> a AssemblyFoldersSuffix> by měly být nahrazeny konkrétními hodnotami pro prohledávané umístění registru. Výchozí specifikace ve společných cílech je {Registry:$(FrameworkRegistryBase), $(TargetFrameworkVersion), $(AssemblyFoldersSuffix), $(AssemblyFoldersExConditions)}.<br />-   `{AssemblyFolders}`: Určuje, že úloha bude používat vizuální Studio.NET 2003 hledání sestavení z registru schéma.<br />-   `{GAC}`: Určuje, že úloha bude prohledávat v globální mezipaměti sestavení (GAC).<br />-   `{RawFileName}`: Určuje, že úloha bude považovat `Include` hodnotu položky za přesnou cestu a název souboru.|
|`SerializationAssemblyFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Obsahuje všechna nalezená sestavení serializace XML. Tyto položky jsou označeny CopyLocal=true pokud a pouze v případě, že odkaz nebo závislost, která způsobila existenci této položky, je CopyLocal=true.<br /><br /> `Boolean` Metadata CopyLocal označuje, zda má být daný odkaz zkopírován do výstupního adresáře.|
|`Silent`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`nejsou zaznamenány žádné zprávy. Výchozí hodnota je `false`.|
|`StateFile`|Volitelný `String` parametr.<br /><br /> Určuje název souboru, který označuje, kam se má uložit stav mezilehlého sestavení pro tuto úlohu.|
|`SuggestedRedirects`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Obsahuje jednu položku pro každou odlišnou konfliktní identitu sestavení, bez ohledu na hodnotu parametru. `AutoUnify` To zahrnuje všechny jazykové verze a PKT, který byl nalezen, který neměl vhodnou vazbuRedirect položka v konfiguračním souboru aplikace.<br /><br /> Každá položka volitelně obsahuje následující informace:<br /><br /> -   `Include`Atribut: Obsahuje úplný název rodiny sestavení s hodnotou pole Verze 0.0.0.0.<br />-   `MaxVersion`metadata položky: Obsahuje maximální číslo verze.|
|`TargetedRuntimeVersion`|Volitelný `String` parametr.<br /><br /> Určuje verzi za běhu, na kterou má být cílována, například 2.0.57027 nebo v2.0.57027.|
|`TargetFrameworkDirectories`|Volitelný `String[]` parametr.<br /><br /> Určuje cestu k cílovému adresáři architektury. Tento parametr je nutný k určení stavu CopyLocal pro výsledné položky.<br /><br /> Pokud tento parametr není zadán, žádné výsledné položky `true` budou mít CopyLocal hodnotu, pokud explicitně mají hodnotu `Private` `true` metadat na jejich zdrojové položky.|
|`TargetFrameworkMoniker`|Volitelný `String` parametr.<br /><br /> TargetFrameworkMoniker sledovat, pokud existuje. Používá se pro protokolování.|
|`TargetFrameworkMonikerDisplayName`|Volitelný `String` parametr.<br /><br /> Zobrazovaný název TargetFrameworkMoniker sledovat, pokud existuje. Používá se pro protokolování.|
|`TargetFrameworkSubsets`|Volitelný `String[]` parametr.<br /><br /> Obsahuje seznam názvů podmnožiny cílové architektury, které mají být vyhledány v adresářích cílové ho rozhraní.|
|`TargetFrameworkVersion`|Volitelný `String` parametr.<br /><br /> Verze rozhraní cíle projektu. Výchozí hodnota je prázdná, což znamená, že neexistuje žádné filtrování pro odkazy založené na cílovém rozhraní.|
|`TargetProcessorArchitecture`|Volitelný `String` parametr.<br /><br /> Upřednostňovaná architektura cílového procesoru. Používá se pro řešení globálních odkazů mezipaměti sestavení (GAC).<br /><br /> Tento parametr může mít `x86` `IA64`hodnotu `AMD64`, , nebo .<br /><br /> Pokud tento parametr chybí, úloha nejprve bere v úvahu sestavení, která odpovídají architektuře aktuálně spuštěného procesu. Pokud není nalezeno žádné sestavení, úloha bere v `ProcessorArchitecture` úvahu `MSIL` sestavení `ProcessorArchitecture` v GAC, které mají hodnotu nebo žádnou hodnotu.|

## <a name="warnings"></a>Upozornění

 Jsou zaznamenána následující upozornění:

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

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
