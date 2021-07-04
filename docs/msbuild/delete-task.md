---
title: Odstranění úlohy | Microsoft Docs
description: Přečtěte si informace o parametrech a důležité informace týkající se MSBuild úlohy Odstranit k odstranění zadaných souborů.
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
ms.openlocfilehash: 09945306a2260bed5b264d380dcea745ff3f7c07
ms.sourcegitcommit: 8fb1500acb7e6314fbb6b78eada78ef5d61d39bf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2021
ms.locfileid: "113280433"
---
# <a name="delete-task"></a>Delete – úloha

Odstraní zadané soubory.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry `Delete` úlohy.

|Parametr|Popis|
|---------------|-----------------|
|`DeletedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje soubory, které byly úspěšně odstraněny.|
|`Files`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje soubory, které chcete odstranit.|
|`TreatErrorsAsWarnings`|Volitelný `Boolean` parametr<br /><br /> Pokud `true` se chyby zaprotokolují jako upozornění. Výchozí hodnota je `false`.|

## <a name="remarks"></a>Poznámky

Kromě parametrů uvedených výše tato úloha dědí parametry z třídy <xref:Microsoft.Build.Tasks.TaskExtension> , která sama dědí z třídy <xref:Microsoft.Build.Utilities.Task> . Seznam těchto dalších parametrů a jejich popisy najdete v tématu [TaskExtension – základní třída](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Při použití zástupných znaků s úlohou buďte `Delete` opatrní. Chybné soubory můžete snadno odstranit pomocí výrazů, jako je nebo , a to zejména v případě, že se vlastnost vyhodnotí jako prázdný řetězec. V takovém případě se parametr může vyhodnotit do kořenového adresáře jednotky a odstranit mnohem více, než jste chtěli `$(SomeProperty)\**\*.*` `$(SomeProperty)/**/*.*` `Files` odstranit.

## <a name="example"></a>Příklad

Následující příklad odstraní soubor *ConsoleApp1.pdb* při sestavování `DeleteDebugSymbolFile` cíle.

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

Pokud potřebujete sledovat odstraněné soubory, nastavte na `TaskParameter` s názvem položky následujícím `DeletedFiles` způsobem:

```xml
      <Target Name="DeleteDebugSymbolFile">
        <Delete Files="$(OutDir)$(AppName).pdb" >
              <Output TaskParameter="DeletedFiles" ItemName="DeletedList"/>
        </Delete>
        <Message Text="Deleted files: '@(DeletedList)'"/>
    </Target>
```

Místo přímého použití zástupných znaků v úkolu vytvořte soubor k odstranění a `Delete` spuštění úlohy na tomto `ItemGroup` `Delete` úkolu. Nezapomeňte ale pečlivě umístit `ItemGroup` . Pokud do souboru projektu dáte soubor na nejvyšší úrovni, vyhodnotí se v rané fázi před zahájením sestavení, takže nebude obsahovat žádné soubory, které byly vytvořeny v `ItemGroup` rámci procesu sestavení. Proto umístěte `ItemGroup` objekt , který vytvoří seznam položek k odstranění, do cíle blízko `Delete` úkolu. Můžete také zadat podmínku, která zkontroluje, že vlastnost není prázdná, takže nevytváříte seznam položek s cestou, která začíná v kořenovém adresáři jednotky.

Úloha `Delete` je určená k odstraňování souborů. Pokud chcete odstranit adresář, použijte [RemoveDir](removedir-task.md).

Úloha neposkytuje možnost odstranit soubory jen `Delete` pro čtení. Pokud chcete odstranit soubory jen pro čtení, můžete pomocí úlohy spustit příkaz nebo ekvivalentní soubor s příslušnou možností pro povolení odstranění souborů `Exec` `del` jen pro čtení. Je třeba věnovat pozornost délce seznamu vstupních položek, protože na příkazovém řádku existuje omezení délky, stejně jako při zpracování názvů souborů s mezerami, jako v tomto příkladu:

```xml
<Target Name="DeleteReadOnly">
  <ItemGroup>
    <FileToDelete Include="read only file.txt"/>
  </ItemGroup>
  <Exec Command="del /F /Q &quot;@(FileToDelete)&quot;"/>
</Target>
```

Obecně platí, že při psaní skriptů sestavení zvažte, jestli je odstranění logicky součástí `Clean` operace. Pokud potřebujete nastavit, aby se některé soubory vyčistili v rámci normální operace, můžete je přidat do seznamu a v dalším kroku se `Clean` `@(FileWrites)` `Clean` odstraní. Pokud je potřeba další vlastní zpracování, definujte cíl a určete, aby se spouštěl nastavením atributu nebo , nebo definujte vlastní `BeforeTargets="Clean"` `AfterTargets="Clean"` verzi cílů nebo `BeforeClean` `AfterClean` . Další informace [najdete v tématu Přizpůsobení sestavení.](customize-your-build.md)

## <a name="see-also"></a>Viz také

- [RemoveDir – úloha](removedir-task.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
