---
title: Úloha RegisterAssembly – | Microsoft Docs
description: Přečtěte si, jak MSBuild používá úlohu RegisterAssembly – ke čtení metadat v rámci zadaného sestavení a přidání potřebných položek do registru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RegisterAssembly task
- RegisterAssembly task [MSBuild]
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce332ac17a20b40cdfbeb4effaf6caf060a87307
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048761"
---
# <a name="registerassembly-task"></a>RegisterAssembly – úloha

Přečte metadata v rámci zadaného sestavení a přidá nezbytné položky do registru, které umožní klientům modelu COM vytvářet transparentně .NET Framework třídy. Chování této úlohy se podobá, ale ne shodná, k tomu [Regasm.exe (nástroj registrace sestavení)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool).

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `RegisterAssembly` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`Assemblies`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje sestavení, která mají být registrována v modelu COM.|
|`AssemblyListFile`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Obsahuje informace o stavu mezi `RegisterAssembly` úlohou a úlohou [UnregisterAssembly –](../msbuild/unregisterassembly-task.md) . Tyto informace brání `UnregisterAssembly` úloze v pokusu o zrušení registrace sestavení, které selhalo při registraci v `RegisterAssembly` úloze.|
|`CreateCodeBase`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , vytvoří položku codebase v registru, která určuje cestu k souboru pro sestavení, které není nainstalováno v globální mezipaměti sestavení (GAC). Tuto možnost byste neměli zadávat, pokud následně instalujete sestavení, které budete registrovat do globální mezipaměti sestavení (GAC).|
|`TypeLibFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje knihovnu typů, která se má generovat ze zadaného sestavení. Vygenerovaná knihovna typů obsahuje definice přístupných typů definovaných v rámci sestavení. Knihovna typů je generována pouze v případě, že je splněna jedna z následujících podmínek:<br /><br /> -V tomto umístění neexistuje knihovna typů daného názvu.<br />-Knihovna typů existuje, ale je starší než sestavení, které je předáno.<br /><br /> Pokud je knihovna typů novější než sestavení, které je předáno, nebude vytvořena nová, ale sestavení bude i nadále zaregistrováno.<br /><br /> Pokud je tento parametr zadán, musí mít stejný počet položek jako `Assemblies` parametr nebo úloha selže. Pokud nejsou zadány žádné vstupy, bude ve výchozím nastavení úloha název sestavení a změna rozšíření položky na *TLB* .|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad používá `RegisterAssembly` úlohu k registraci sestavení určeného `MyAssemblies` kolekcí položek.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyAssemblies Include="MyAssembly.dll" />
    <ItemGroup>

    <Target Name="RegisterAssemblies">
        <RegisterAssembly
            Assemblies="@(MyAssemblies)" >
    </Target>

</Project>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
