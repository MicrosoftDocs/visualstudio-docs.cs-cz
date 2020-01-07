---
title: Úloha ResolveComReference – | Microsoft Docs
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595199"
---
# <a name="resolvecomreference-task"></a>ResolveComReference – – úloha

Převezme seznam jednoho nebo více názvů knihoven typů nebo souborů *. tlb* a přeloží tyto knihovny typů do umístění na disku.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy `ResolveCOMReference`.

|Parametr|Popis|
|---------------|-----------------|
|`DelaySign`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, umístí veřejný klíč do sestavení. Pokud `false`, plně podepíše sestavení.|
|`EnvironmentVariables`|Volitelný parametr `String[]`.<br /><br /> Pole párů proměnných prostředí oddělené znaménkem rovná se. Tyto proměnné jsou předány do vytvořeného nástroje *Tlbimp. exe* a *Aximp. exe* kromě nebo selektivního přepsání regulárního bloku prostředí.|
|`ExecuteAsTool`|Volitelný parametr `Boolean`.<br /><br /> V případě `true`spustí nástroj *Tlbimp. exe* a *Aximp. exe* z příslušného cílového rozhraní out-of-proc, aby se vygenerovala potřebná sestavení obálky. Tento parametr umožňuje cílení na více platforem.|
|`IncludeVersionInInteropName`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, bude v názvu obálky obsažena verze TypeLib. Výchozí hodnota je `false`.|
|`KeyContainer`|Volitelný parametr `String`.<br /><br /> Určuje kontejner, který obsahuje pár veřejného a privátního klíče.|
|`KeyFile`|Volitelný parametr `String`.<br /><br /> Určuje položku, která obsahuje pár veřejného a privátního klíče.|
|`NoClassMembers`|Volitelný parametr `Boolean`.|
|`ResolvedAssemblyReferences`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Určuje odkazy na přeložené sestavení.|
|`ResolvedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Určuje plně kvalifikované soubory na disku, které odpovídají fyzickým umístěním knihoven typů, které byly zadány jako vstup pro tento úkol.|
|`ResolvedModules`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]`parametr.|
|`SdkToolsPath`|Volitelný parametr <xref:System.String?displayProperty=fullName>.<br /><br /> Pokud je `true``ExecuteAsTool`, musí být tento parametr nastaven na cestu nástrojů sady SDK pro cílovou verzi rozhraní.|
|`StateFile`|Volitelný parametr `String`.<br /><br /> Určuje soubor mezipaměti pro časová razítka komponenty modelu COM. Pokud tato akce není k dispozici, budou všechny obálky znovu vygenerovány při každém spuštění.|
|`TargetFrameworkVersion`|Volitelný parametr `String`.<br /><br /> Určuje verzi cílového rozhraní projektu.<br /><br /> Výchozí hodnota je `String.Empty`. To znamená, že neexistuje žádné filtrování pro odkaz na základě cílové architektury.|
|`TargetProcessorArchitecture`|Volitelný parametr `String`.<br /><br /> Určuje preferovanou cílovou architekturu procesoru. Po překladu předávají příznak *Tlbimp. exe*/Machine.<br /><br /> Hodnota parametru by měla být členem <xref:Microsoft.Build.Utilities.ProcessorArchitecture>.|
|`TypeLibFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Určuje cestu k souboru knihovny typů pro odkazy COM. Položky zahrnuté v tomto parametru můžou obsahovat metadata položky. Další informace najdete v části [TypeLibFiles Item metadata](#typelibfiles-item-metadata) níže.|
|`TypeLibNames`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Určuje názvy knihoven typů, které se mají přeložit. Položky zahrnuté v tomto parametru musí obsahovat některá metadata položky. Další informace najdete v části [TypeLibNames Item metadata](#typelibnames-item-metadata) níže.|
|`WrapperOutputDirectory`|Volitelný parametr `String`.<br /><br /> Umístění na disku, kde je umístěno vygenerované sestavení vzájemné spolupráce. Pokud tato metadata položky nejsou zadána, úloha používá absolutní cestu adresáře, ve kterém je umístěn soubor projektu.|

## <a name="typelibnames-item-metadata"></a>Metadata položky TypeLibNames

 Následující tabulka popisuje metadata položek, která jsou k dispozici pro položky předané do parametru `TypeLibNames`.

|Metadata|Popis|
|--------------|-----------------|
|`GUID`|Požadovaná metadata položky<br /><br /> Identifikátor GUID knihovny typů Pokud tato metadata položky nejsou zadaná, úloha se nezdařila.|
|`VersionMajor`|Požadovaná metadata položky<br /><br /> Hlavní verze knihovny typů. Pokud tato metadata položky nejsou zadaná, úloha se nezdařila.|
|`VersionMinor`|Požadovaná metadata položky<br /><br /> Vedlejší verze knihovny typů. Pokud tato metadata položky nejsou zadaná, úloha se nezdařila.|
|`EmbedInteropTypes`|Nepovinná metadata `Boolean`.<br /><br />  Pokud `true`, vložte typy spolupráce z tohoto odkazu přímo do sestavení namísto generování knihovny DLL pro spolupráci.|
|`LocaleIdentifier`|Nepovinná metadata položky<br /><br /> Identifikátor národního prostředí (nebo LCID) pro knihovnu typů. Tento parametr je určený jako 32 hodnota, která identifikuje lidský jazyk upřednostňovaný uživatelem, oblastí nebo aplikací. Pokud tato metadata položky nejsou zadaná, úloha použije výchozí identifikátor národního prostředí "0".|
|`WrapperTool`|Nepovinná metadata položky<br /><br /> Určuje nástroj obálky, který se používá ke generování obálky sestavení pro tuto knihovnu typů. Pokud tato metadata položky nejsou zadána, úloha použije výchozí nástroj obálky "Tlbimp". K dispozici jsou možnosti pro nerozlišování velkých a malých písmen:<br /><br /> -   `Primary`: Tento nástroj obálky použijte, pokud chcete pro komponentu COM použít již vygenerované primární definiční sestavení. Když použijete tento nástroj obálky, nezadávejte výstupní adresář obálky, protože to způsobí, že se úloha nezdaří.<br />-   `TLBImp`: použijte tento nástroj obálky, pokud chcete vygenerovat definiční sestavení pro komponentu COM.<br />-   `AXImp`: použijte tento nástroj obálky, pokud chcete vygenerovat definiční sestavení pro ovládací prvek ActiveX.|

## <a name="typelibfiles-item-metadata"></a>Metadata položky TypeLibFiles

 Následující tabulka popisuje metadata položek, která jsou k dispozici pro položky předané do parametru `TypeLibFiles`.

|Metadata|Popis|
|--------------|-----------------|
|`EmbedInteropTypes`|Volitelný parametr `Boolean`.<br /><br />  Pokud `true`, vložte typy spolupráce z tohoto odkazu přímo do sestavení namísto generování knihovny DLL pro spolupráci.|
|`WrapperTool`|Nepovinná metadata položky<br /><br /> Určuje nástroj obálky, který se používá ke generování obálky sestavení pro tuto knihovnu typů. Pokud tato metadata položky nejsou zadána, úloha použije výchozí nástroj obálky "Tlbimp". K dispozici jsou možnosti pro nerozlišování velkých a malých písmen:<br /><br /> -   `Primary`: Tento nástroj obálky použijte, pokud chcete pro komponentu COM použít již vygenerované primární definiční sestavení. Když použijete tento nástroj obálky, nezadávejte výstupní adresář obálky, protože to způsobí, že se úloha nezdaří.<br />-   `TLBImp`: použijte tento nástroj obálky, pokud chcete vygenerovat definiční sestavení pro komponentu COM.<br />-   `AXImp`: použijte tento nástroj obálky, pokud chcete vygenerovat definiční sestavení pro ovládací prvek ActiveX.|

> [!NOTE]
> Další informace, které zadáte k jedinečné identifikaci knihovny typů, jsou větší než možnost, že se úloha vyřeší na správný soubor na disku.

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisů naleznete v tématu [základní třída Task](../msbuild/task-base-class.md).

Aby tato úloha fungovala, nemusí být v počítači zaregistrovaná knihovna COM.

## <a name="see-also"></a>Viz také:

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
