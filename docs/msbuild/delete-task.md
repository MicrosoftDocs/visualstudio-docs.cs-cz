---
title: Odstranit úlohu | Microsoft Docs
description: Přečtěte si o parametrech a důvodech pro odstranění zadaných souborů pomocí úlohy MSBuild DELETE.
ms.custom: SEO-VS-2020
ms.date: 06/11/2020
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b49ba26cc1e88ab3241094e1fd92be0907e8dd60
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877340"
---
# <a name="delete-task"></a>Delete – úloha

Odstraní zadané soubory.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry `Delete` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`DeletedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje soubory, které se úspěšně odstranily.|
|`Files`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje soubory, které se mají odstranit.|
|`TreatErrorsAsWarnings`|Volitelný `Boolean` parametr<br /><br /> Pokud `true` jsou chyby protokolovány jako upozornění. Výchozí hodnota je `false`.|

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Při použití zástupných znaků s úkolem buďte opatrní `Delete` . Nesprávné soubory můžete snadno odstranit pomocí výrazů jako `$(SomeProperty)\**\*.*` nebo `$(SomeProperty)/**/*.*` , zejména pokud je vlastnost vyhodnocena jako prázdný řetězec. v takovém případě se `Files` parametr může vyhodnotit na kořen vaší jednotky a odstranit mnohem více, než jste chtěli odstranit.

## <a name="example"></a>Příklad

Následující příklad odstraní soubor *MyApp. pdb* při sestavení `DeleteDebugSymbolFile` cíle.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

    <PropertyGroup>
        <AppName>ConsoleApp1</AppName>
    </PropertyGroup>

    <Target Name="DeleteDebugSymbolFile">
        <Message Text="Deleting $(OutDir)$(AppName).pdb"/>
        <Delete Files="$(OutDir)$(AppName).pdb" />
    </Target>
  
</Project>

```

Pokud potřebujete sledovat odstraněné soubory, nastavte `TaskParameter` na hodnotu `DeletedFiles` s názvem položky následujícím způsobem:

```xml
      <Target Name="DeleteDebugSymbolFile">
        <Delete Files="$(OutDir)$(AppName).pdb" >
              <Output TaskParameter="DeletedFiles" ItemName="DeletedList"/>
        </Delete>
        <Message Text="Deleted files: '@(DeletedList)'"/>
    </Target>
```

Místo přímého použití zástupných znaků v `Delete` úloze vytvořte `ItemGroup` soubory pro odstranění a spuštění `Delete` úlohy. Ale nezapomeňte `ItemGroup` pečlivě umístit. Pokud umístíte do `ItemGroup` nejvyšší úrovně v souboru projektu, vyhodnotí se nejdříve před zahájením sestavení, takže nebude obsahovat žádné soubory, které byly vytvořeny jako součást procesu sestavení. Proto vložte `ItemGroup` objekt, který vytvoří seznam položek k odstranění v cíli blízko `Delete` úkolu. Můžete také zadat podmínku pro kontrolu, že vlastnost není prázdná, takže nevytvoříte seznam položek s cestou, která začíná v kořenovém adresáři jednotky.

`Delete`Úloha je určena k odstraňování souborů. Pokud chcete odstranit adresář, použijte [RemoveDir –](removedir-task.md).

`Delete`Úkol neposkytuje možnost odstraňovat soubory jen pro čtení. Chcete-li odstranit soubory jen pro čtení, můžete použít `Exec` úlohu ke spuštění `del` příkazu nebo ekvivalentní s příslušnou možností pro povolení odstraňování souborů jen pro čtení. Musíte věnovat pozornost délce seznamu vstupních položek, protože na příkazovém řádku je omezení délky, a navíc je potřeba zpracovat názvy souborů s mezerami, jako v tomto příkladu:

```xml
<Target Name="DeleteReadOnly">
  <ItemGroup>
    <FileToDelete Include="read only file.txt"/>
  </ItemGroup>
  <Exec Command="del /F /Q &quot;@(FileToDelete)&quot;"/>
</Target>
```

Obecně platí, že při psaní skriptů sestavení zvažte, zda je odstranění logicky součástí `Clean` operace. Pokud potřebujete nastavit soubory, které se mají vyčistit v rámci běžné `Clean` operace, můžete je přidat do `@(FileWrites)` seznamu a budou se odstraňovat v dalším `Clean` . Pokud je potřeba další vlastní zpracování, definujte cíl a určete, že se má spustit, nastavením atributu `BeforeTargets="Clean"` nebo `AfterTargets="Clean"` , nebo definujte vlastní verzi `BeforeClean` nebo `AfterClean` cílů. Viz [přizpůsobení sestavení](customize-your-build.md).

## <a name="see-also"></a>Viz také

- [RemoveDir – úloha](removedir-task.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
