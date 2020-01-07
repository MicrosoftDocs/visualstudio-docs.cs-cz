---
title: Úloha RegisterAssembly – | Microsoft Docs
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
ms.openlocfilehash: 57031bd49a67e1961b5413a59f66562cc9c1b883
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596785"
---
# <a name="registerassembly-task"></a>RegisterAssembly – úloha
Přečte metadata v rámci zadaného sestavení a přidá nezbytné položky do registru, které umožní klientům modelu COM vytvářet transparentně .NET Framework třídy. Chování této úlohy je podobné, ale ne identické, pro modul [Regasm. exe (Nástroj pro registraci sestavení)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool).

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy `RegisterAssembly`.

|Parametr|Popis|
|---------------|-----------------|
|`Assemblies`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje sestavení, která mají být registrována v modelu COM.|
|`AssemblyListFile`|Volitelný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Obsahuje informace o stavu mezi úlohou `RegisterAssembly` a úlohou [UnregisterAssembly –](../msbuild/unregisterassembly-task.md) . Tyto informace brání úloze `UnregisterAssembly` v pokusu o zrušení registrace sestavení, které selhalo při registraci do úlohy `RegisterAssembly`.|
|`CreateCodeBase`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, vytvoří v registru položku codebase, která určuje cestu k souboru pro sestavení, které není nainstalováno v globální mezipaměti sestavení (GAC). Tuto možnost byste neměli zadávat, pokud následně instalujete sestavení, které budete registrovat do globální mezipaměti sestavení (GAC).|
|`TypeLibFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Určuje knihovnu typů, která se má generovat ze zadaného sestavení. Vygenerovaná knihovna typů obsahuje definice přístupných typů definovaných v rámci sestavení. Knihovna typů je generována pouze v případě, že je splněna jedna z následujících podmínek:<br /><br /> -V tomto umístění neexistuje knihovna typů daného názvu.<br />-Knihovna typů existuje, ale je starší než sestavení, které je předáno.<br /><br /> Pokud je knihovna typů novější než sestavení, které je předáno, nebude vytvořena nová, ale sestavení bude i nadále zaregistrováno.<br /><br /> Pokud je tento parametr zadán, musí mít stejný počet položek jako parametr `Assemblies` nebo úloha selže. Pokud nejsou zadány žádné vstupy, bude ve výchozím nastavení úloha název sestavení a změna rozšíření položky na *TLB*.|

## <a name="remarks"></a>Poznámky
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad
 Následující příklad používá úlohu `RegisterAssembly` k registraci sestavení určeného kolekcí `MyAssemblies`ch položek.

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

## <a name="see-also"></a>Viz také:
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
