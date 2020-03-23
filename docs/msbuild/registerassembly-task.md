---
title: RegisterAssembly Úkol | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 0c95606a00e86ffd187162e444f2c710c5cc3a0e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632885"
---
# <a name="registerassembly-task"></a>RegisterAssembly – úloha

Načte metadata v zadaném sestavení a přidá potřebné položky do registru, což umožňuje klientům COM vytvářet třídy rozhraní .NET Framework transparentně. Chování tohoto úkolu je podobné, ale není totožné s [regasm.exe (nástroj registrace sestavení)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool).

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `RegisterAssembly` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`Assemblies`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje sestavení, která mají být registrována u com.|
|`AssemblyListFile`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Obsahuje informace o stavu `RegisterAssembly` mezi úkolem a úkolem [UnregisterAssembly.](../msbuild/unregisterassembly-task.md) Tyto informace brání `UnregisterAssembly` úlohy v pokusu o zrušení registrace `RegisterAssembly` sestavení, které se nepodařilo zaregistrovat v úloze.|
|`CreateCodeBase`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`vytvoří položku základu kódu v registru, která určuje cestu k souboru pro sestavení, které není nainstalováno v globální mezipaměti sestavení. Tuto možnost byste neměli zadávat, pokud následně instalujete sestavení, které budete registrovat do globální mezipaměti sestavení (GAC).|
|`TypeLibFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje knihovnu typů, která má být generována ze zadaného sestavení. Knihovna generovaných typů obsahuje definice přístupných typů definovaných v rámci sestavení. Knihovna typů je generována pouze v případě, že je splněna jedna z následujících podmínek:<br /><br /> - Knihovna typů tohoto názvu v tomto umístění neexistuje.<br />- Knihovna typů existuje, ale je starší než předávané sestavení.<br /><br /> Pokud je knihovna typů novější než předané sestavení, nebude vytvořena nová, ale sestavení bude stále zaregistrováno.<br /><br /> Pokud je tento parametr zadán, musí mít stejný `Assemblies` počet položek jako parametr, jinak se úloha nezdaří. Pokud nejsou zadány žádné vstupy, úloha bude ve výchozím nastavení nastavena na název sestavení a změní rozšíření položky na *.tlb*.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad používá `RegisterAssembly` úlohu k registraci `MyAssemblies` sestavení určeného kolekcí položek.

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
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
