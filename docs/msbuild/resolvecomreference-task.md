---
title: Resolvecomreference – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f13efe45547b657f9e07c12d8eee4160ec7b95e
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152396"
---
# <a name="resolvecomreference-task"></a>Resolvecomreference – úloha
Přebírá seznam jednoho nebo více typů názvy knihoven nebo *.tlb* soubory a řeší tyto knihovny typů do umístění na disku.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `ResolveCOMReference` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`DelaySign`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, umístí veřejný klíč v sestavení. Pokud `false`, plně podepíše sestavení.|  
|`EnvironmentVariables`|Volitelné `String[]` parametru.<br /><br /> Pole párů proměnné prostředí oddělené rovnítko. Tyto proměnné jsou předány do nové kopie *tlbimp.exe* a *aximp.exe* kromě, nebo selektivní přepsání, blok regulární prostředí...|  
|`ExecuteAsTool`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, spustí *tlbimp.exe* a *aximp.exe* z příslušné cílové rozhraní framework z – mimoprocesovou ke generování sestavení obálky nezbytné. Tento parametr umožňuje cílení na více platforem.|  
|`IncludeVersionInInteropName`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, verze knihovny typů se zahrne název obálky. Výchozí hodnota je `false`.|  
|`KeyContainer`|Volitelné `String` parametru.<br /><br /> Určuje kontejner obsahující pár veřejného a privátního klíče.|  
|`KeyFile`|Volitelné `String` parametru.<br /><br /> Určuje položku, která obsahuje pár veřejného a privátního klíče.|  
|`NoClassMembers`|Volitelné `Boolean`parametru.|  
|`ResolvedAssemblyReferences`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje odkazy na sestavení přeložit.|  
|`ResolvedFiles`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje plně kvalifikovaný soubory na disku, které odpovídají fyzických umístění knihovny typů, které byly k dispozici jako vstup pro tuto úlohu.|  
|`ResolvedModules`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]`parametru.|  
|`SdkToolsPath`|Volitelné <xref:System.String?displayProperty=fullName> parametru.<br /><br /> Pokud `ExecuteAsTool` je `true`, tento parametr musí být nastaven na cestu k nástrojům sady SDK pro verzi rozhraní framework, který se cílí.|  
|`StateFile`|Volitelné `String` parametru.<br /><br /> Určuje soubor mezipaměti pro komponenty modelu COM časová razítka. Pokud není k dispozici, každé spuštění se znova vygeneruje všechny obálky.|  
|`TargetFrameworkVersion`|Volitelné `String` parametru.<br /><br /> Určuje cílovou verzi rozhraní framework projektu.<br /><br /> Výchozí hodnota je `String.Empty`. což znamená, že není žádné filtrování pro referenci podle cílovou architekturu.|  
|`TargetProcessorArchitecture`|Volitelné `String` parametru.<br /><br /> Určuje upřednostňovaný cíl architekturu procesoru. Předány *tlbimp.exe*  /machine příznak po převodu.<br /><br /> Hodnota parametru by měl být členem skupiny <xref:Microsoft.Build.Utilities.ProcessorArchitecture>.|  
|`TypeLibFiles`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje cesta k souboru knihovny typů pro odkazy modelu COM. Metadata položek může obsahovat položky obsažené v tomto parametru. Další informace najdete v části [TypeLibFiles položky metadat](#typelibfiles-item-metadata) níže.|  
|`TypeLibNames`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje názvy knihovny typů řešení. Některá metadata položky musí obsahovat položky obsažené v tomto parametru. Další informace najdete v části [TypeLibNames položky metadat](#typelibnames-item-metadata) níže.|  
|`WrapperOutputDirectory`|Volitelné `String` parametru.<br /><br /> Umístění na disku, kde je umístěn vygenerovaný definiční sestavení. Pokud tuto položku metadat není zadán, úkol používá absolutní cestu k adresáři a kde je umístěn soubor projektu.|  
  
## <a name="typelibnames-item-metadata"></a>Metadata položky TypeLibNames  
 Následující tabulka popisuje dostupná metadata položky pro položky předán `TypeLibNames` parametru.  
  
|Metadata|Popis|  
|--------------|-----------------|  
|`GUID`|Požadovaná položka metadat.<br /><br /> Identifikátor GUID pro knihovnu typů. Pokud se tato metadata položky nezadá, úloha se nezdaří.|  
|`VersionMajor`|Požadovaná položka metadat.<br /><br /> Hlavní verze knihovny typů. Pokud se tato metadata položky nezadá, úloha se nezdaří.|  
|`VersionMinor`|Požadovaná položka metadat.<br /><br /> Dílčí verze knihovny typů. Pokud se tato metadata položky nezadá, úloha se nezdaří.|  
|`LocaleIdentifier`|Nepovinná položka metadat.<br /><br /> Identifikátor národního prostředí (nebo LCID) pro knihovnu typů. Tento parametr je zadán jako hodnotu 32-bit, který identifikuje lidské jazyk upřednostňuje uživatelů, oblast nebo aplikaci. Pokud se tato metadata položky nezadá, použije úloha výchozí identifikátor národního prostředí "0".|  
|`WrapperTool`|Nepovinná položka metadat.<br /><br /> Určuje, že nástrojem obálky, který se používá ke generování sestavení obálky pro tuto knihovnu typů. Pokud není zadána tato metadata položky, úkol používá výchozí nástroj obálky "tlbimp". Jsou k dispozici, malá a velká písmena výběr typelibs:<br /><br /> -   `Primary`: Tento nástroj obálky použijte, pokud chcete použít již generované primární spolupracující sestavení pro komponenty modelu COM. Použijete-li tento nástroj obálky, nezadávejte obálky výstupní adresář, protože, které způsobí selhání úlohy.<br />-   `TLBImp`: Použijte tento nástroj obálky, když potřebujete ke generování sestavení vzájemné spolupráce pro komponenty modelu COM.<br />-   `AXImp`: Použijte tento nástroj obálky, když potřebujete ke generování sestavení vzájemné spolupráce pro ovládací prvek ActiveX.|  
  
## <a name="typelibfiles-item-metadata"></a>Metadata položky TypeLibFiles  
 Následující tabulka popisuje dostupná metadata položky pro položky předán `TypeLibFiles` parametru.  
  
|Metadata|Popis|  
|--------------|-----------------|  
|`WrapperTool`|Nepovinná položka metadat.<br /><br /> Určuje, že nástrojem obálky, který se používá ke generování sestavení obálky pro tuto knihovnu typů. Pokud není zadána tato metadata položky, úkol používá výchozí nástroj obálky "tlbimp". Jsou k dispozici, malá a velká písmena výběr typelibs:<br /><br /> -   `Primary`: Tento nástroj obálky použijte, pokud chcete použít již generované primární spolupracující sestavení pro komponenty modelu COM. Použijete-li tento nástroj obálky, nezadávejte obálky výstupní adresář, protože, které způsobí selhání úlohy.<br />-   `TLBImp`: Použijte tento nástroj obálky, když potřebujete ke generování sestavení vzájemné spolupráce pro komponenty modelu COM.<br />-   `AXImp`: Použijte tento nástroj obálky, když potřebujete ke generování sestavení vzájemné spolupráce pro ovládací prvek ActiveX.|  
  
> [!NOTE]
>  Další informace, které poskytnete k jednoznačné identifikaci knihovny typů, větší možnost, že úloha se přeloží správný soubor na disku.  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [Task – základní třída](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Viz také:  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)