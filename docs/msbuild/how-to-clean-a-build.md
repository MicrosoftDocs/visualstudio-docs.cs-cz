---
title: 'Postup: Čištění sestavení | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, cleaning a build
- directories [.NET Framework], for output items
- output, removing items
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b7848189c866481e6e97d05d95b5fb97a3d4893
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633912"
---
# <a name="how-to-clean-a-build"></a>Postup: Čištění sestavení

Při čištění sestavení jsou odstraněny všechny zprostředkující a výstupní soubory, takže pouze soubory projektu a součásti. Ze souborů projektu a součástí pak mohou být vytvořeny nové instance zprostředkujících a výstupních souborů. 

## <a name="create-a-directory-for-output-items"></a>Vytvoření adresáře pro výstupní položky

 Ve výchozím nastavení je soubor *EXE* vytvořený při kompilaci projektu umístěn do stejného adresáře jako projektové a zdrojové soubory. Obvykle jsou však výstupní položky vytvořeny v samostatném adresáři.

### <a name="to-create-a-directory-for-output-items"></a>Vytvoření adresáře pro výstupní položky

1. Pomocí `Property` prvku definujte umístění a název adresáře. V adresáři, který obsahuje projektové a zdrojové soubory, můžete například vytvořit adresář s názvem *BuiltApp:*

     `<builtdir>BuiltApp</builtdir>`

2. Pokud adresář neexistuje, použijte úlohu [MakeDir](../msbuild/makedir-task.md) k vytvoření adresáře. Například:

     ```xml
     <MakeDir Directories = "$(builtdir)"
      Condition = "!Exists('$(builtdir)')" />
     ```

## <a name="remove-the-output-items"></a>Odebrání výstupních položek

 Před vytvořením nových instancí zprostředkujících a výstupních souborů můžete chtít vymazat všechny předchozí instance zprostředkujících a výstupních souborů. Pomocí úlohy [RemoveDir](../msbuild/removedir-task.md) odstraňte adresář a všechny soubory a adresáře, které obsahuje z disku.

#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>Odebrání adresáře a všech souborů obsažených v adresáři

- Pomocí `RemoveDir` této úlohy odeberte adresář. Například:

     `<RemoveDir Directories="$(builtdir)" />`

## <a name="example"></a>Příklad

 Následující příklad kódu projektu obsahuje `Clean`nový cíl `RemoveDir` , který používá úkol k odstranění adresáře a všechny soubory a adresáře, které obsahuje. Také v tomto `Compile` příkladu cíl vytvoří samostatný adresář pro výstupní položky, které jsou odstraněny při čištění sestavení.

 `Compile`je definován jako výchozí cíl, a proto se používá automaticky, pokud nezadáte jiný cíl nebo cíle. Pomocí přepínače příkazového řádku **-target** můžete určit jiný cíl. Například:

 `msbuild <file name>.proj -target:Clean`

 Přepínač **-target** lze zkrátit na **-t** a může určit více než jeden cíl. Chcete-li například `Clean` použít cíl, pak cíl `Compile`, zadejte:

 `msbuild <file name>.proj -t:Clean;Compile`

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <!-- Set the application name as a property -->
        <name>HelloWorldCS</name>

        <!-- Set the output folder as a property -->
        <builtdir>BuiltApp</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <!-- Specify the inputs by type and file name -->
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Check whether an output folder exists and create
        one if necessary -->
        <MakeDir Directories = "$(builtdir)"
            Condition = "!Exists('$(builtdir)')" />

        <!-- Run the Visual C# compiler -->
        <CSC Sources = "@(CSFile)"
            OutputAssembly = "$(BuiltDir)\$(appname).exe">
            <Output TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>

        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>

    <Target Name = "Clean">
        <RemoveDir Directories="$(builtdir)" />
    </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Úloha MakeDir](../msbuild/makedir-task.md)
- [Úkol OdebratDir](../msbuild/removedir-task.md)
- [Úkol CsC](../msbuild/csc-task.md)
- [Cíle](../msbuild/msbuild-targets.md)
