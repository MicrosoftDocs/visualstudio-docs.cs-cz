---
title: Úkol ResolveComReference | Dokumenty společnosti Microsoft
ms.date: 07/25/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveCOMReference task
- ResolveCOMReference task [MSBuild]
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fdc6c6ccd58bcc83cc37ff3a9f7888af837ed6e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595199"
---
# <a name="resolvecomreference-task"></a>Úloha ResolveComReference

Pořídí seznam jednoho nebo více názvů knihovny typů nebo souborů *TLB* a přeloizuje tyto knihovny typů do umístění na disku.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `ResolveCOMReference` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`DelaySign`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`umístí veřejný klíč do sestavení. Pokud `false`, plně podepíše shromáždění.|
|`EnvironmentVariables`|Volitelný `String[]` parametr.<br /><br /> Pole párů proměnných prostředí, oddělených rovnítky. Tyto proměnné jsou předány spawned *tlbimp.exe* a *aximp.exe* kromě, nebo selektivně přepsání, pravidelné blok prostředí..|
|`ExecuteAsTool`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`spustí *tlbimp.exe* a *aximp.exe* z příslušného cílového rozhraní mimo proc a vygeneruje potřebné sestavy obálky. Tento parametr umožňuje vícenásobné cílení.|
|`IncludeVersionInInteropName`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`bude do názvu obálky zahrnuta verze typelib. Výchozí formát je `false`.|
|`KeyContainer`|Volitelný `String` parametr.<br /><br /> Určuje kontejner, který obsahuje dvojici veřejného a soukromého klíče.|
|`KeyFile`|Volitelný `String` parametr.<br /><br /> Určuje položku, která obsahuje dvojici veřejného a soukromého klíče.|
|`NoClassMembers`|Volitelný `Boolean`parametr.|
|`ResolvedAssemblyReferences`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje vyřešené odkazy na sestavení.|
|`ResolvedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje plně kvalifikované soubory na disku, které odpovídají fyzickým umístěním knihoven typů, které byly poskytnuty jako vstup pro tuto úlohu.|
|`ResolvedModules`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]`parametr.|
|`SdkToolsPath`|Volitelný <xref:System.String?displayProperty=fullName> parametr.<br /><br /> Pokud `ExecuteAsTool` `true`je , tento parametr musí být nastavena na cestu nástroje sady SDK pro cílovou verzi rozhraní.|
|`StateFile`|Volitelný `String` parametr.<br /><br /> Určuje soubor mezipaměti pro časová razítka komponenty COM. Pokud není k dispozici, každý běh bude regenerovat všechny obálky.|
|`TargetFrameworkVersion`|Volitelný `String` parametr.<br /><br /> Určuje verzi rozhraní framework u cíle projektu.<br /><br /> Výchozí formát je `String.Empty`. což znamená, že neexistuje žádné filtrování pro odkaz založený na cílovém rámci.|
|`TargetProcessorArchitecture`|Volitelný `String` parametr.<br /><br /> Určuje upřednostňovanou architekturu cílového procesoru. Předáno *tlbimp.exe*/machine příznak po překladu.<br /><br /> Hodnota parametru by měla <xref:Microsoft.Build.Utilities.ProcessorArchitecture>být členem .|
|`TypeLibFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje cestu k odkazům knihovny typů k odkazům com. Položky zahrnuté v tomto parametru mohou obsahovat metadata položky. Další informace naleznete v části [Metadata položky TypeLibFiles](#typelibfiles-item-metadata) níže.|
|`TypeLibNames`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje názvy knihovny typů, které mají být překládány. Položky zahrnuté v tomto parametru musí obsahovat některá metadata položky. Další informace naleznete v části [Metadata položky TypeLibNames](#typelibnames-item-metadata) níže.|
|`WrapperOutputDirectory`|Volitelný `String` parametr.<br /><br /> Umístění na disku, kde je umístěno generované sestavení interop. Pokud tato metadata položky není zadána, úkol použije absolutní cestu k adresáři, kde je umístěn soubor projektu.|

## <a name="typelibnames-item-metadata"></a>Metadata položky TypeLibNames

 Následující tabulka popisuje metadata položky, která `TypeLibNames` jsou k dispozici pro položky předané parametru.

|Metadata|Popis|
|--------------|-----------------|
|`GUID`|Požadovaná metadata položky.<br /><br /> Identifikátor GUID pro knihovnu typů. Pokud tato metadata položky není zadána, úloha se nezdaří.|
|`VersionMajor`|Požadovaná metadata položky.<br /><br /> Hlavní verze knihovny typů. Pokud tato metadata položky není zadána, úloha se nezdaří.|
|`VersionMinor`|Požadovaná metadata položky.<br /><br /> Dílčí verze knihovny typů. Pokud tato metadata položky není zadána, úloha se nezdaří.|
|`EmbedInteropTypes`|Volitelná `Boolean` metadata.<br /><br />  Pokud `true`vložte typy interop z tohoto odkazu přímo do sestavy, nikoli do generování meziop DLL.|
|`LocaleIdentifier`|Volitelná metadata položky.<br /><br /> Identifikátor národního prostředí (nebo LCID) pro knihovnu typů. To je určeno jako 32bitová hodnota, která identifikuje lidský jazyk upřednostňovaný uživatelem, oblastí nebo aplikací. Pokud tato metadata položky není zadána, úloha používá výchozí identifikátor národního prostředí "0".|
|`WrapperTool`|Volitelná metadata položky.<br /><br /> Určuje nástroj obálky, který se používá ke generování obálky sestavení pro tuto knihovnu typů. Pokud tato metadata položky není zadán, úloha používá výchozí obálku nástroj "tlbimp". Dostupné volby bez rozlišování velkých a malých písmen typelibs jsou:<br /><br /> -   `Primary`: Tento nástroj obálky použijte, pokud chcete pro komponentu MODELU COM použít již vygenerovanou primární sestavu interop. Při použití tohoto nástroje obálky nezadávejte výstupní adresář obálky, protože to způsobí selhání úlohy.<br />-   `TLBImp`: Tento nástroj obálky použijte, pokud chcete generovat sestavu interop pro komponentu MODELU COM.<br />-   `AXImp`: Tento nástroj obálky použijte, pokud chcete generovat sestavu interop pro ovládací prvek ActiveX.|

## <a name="typelibfiles-item-metadata"></a>Metadata položky TypeLibFiles

 Následující tabulka popisuje metadata položky, která `TypeLibFiles` jsou k dispozici pro položky předané parametru.

|Metadata|Popis|
|--------------|-----------------|
|`EmbedInteropTypes`|Volitelný `Boolean`parametr.<br /><br />  Pokud `true`vložte typy interop z tohoto odkazu přímo do sestavy, nikoli do generování meziop DLL.|
|`WrapperTool`|Volitelná metadata položky.<br /><br /> Určuje nástroj obálky, který se používá ke generování obálky sestavení pro tuto knihovnu typů. Pokud tato metadata položky není zadán, úloha používá výchozí obálku nástroj "tlbimp". Dostupné volby bez rozlišování velkých a malých písmen typelibs jsou:<br /><br /> -   `Primary`: Tento nástroj obálky použijte, pokud chcete pro komponentu MODELU COM použít již vygenerovanou primární sestavu interop. Při použití tohoto nástroje obálky nezadávejte výstupní adresář obálky, protože to způsobí selhání úlohy.<br />-   `TLBImp`: Tento nástroj obálky použijte, pokud chcete generovat sestavu interop pro komponentu MODELU COM.<br />-   `AXImp`: Tento nástroj obálky použijte, pokud chcete generovat sestavu interop pro ovládací prvek ActiveX.|

> [!NOTE]
> Čím více informací poskytnete k jednoznačné identifikaci knihovny typů, tím větší je možnost, že se úloha vyřeší na správný soubor na disku.

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Utilities.Task> parametry z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [Základní třída úlohy](../msbuild/task-base-class.md).

Aby tento úkol fungoval, nemusí být v počítači registrována zpráva COM DLL.

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
