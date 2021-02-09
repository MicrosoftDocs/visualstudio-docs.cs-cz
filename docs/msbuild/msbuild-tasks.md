---
title: Úlohy nástroje MSBuild | Microsoft Docs
description: Naučte se, jak MSBuild používá úkoly nebo jednotky spustitelného kódu, které během procesu sestavení provádějí operace atomických sestavení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6b3bb4c1a17cd5d1481be2fa942686bce3861bb2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918917"
---
# <a name="msbuild-tasks"></a>úlohy nástroje MSBuild

Platforma sestavení potřebuje možnost spustit libovolný počet akcí během procesu sestavení. Nástroj MSBuild používá *úkoly* k provedení těchto akcí. Úloha je jednotka spustitelného kódu, kterou používá MSBuild k provádění atomických operací sestavení.

## <a name="task-logic"></a>Logika úlohy

 Formát souboru projektu MSBuild XML nemůže plně provádět vlastní operace sestavení, takže logika úlohy musí být implementována mimo soubor projektu.

 Logika spuštění úkolu je implementována jako třída .NET, která implementuje <xref:Microsoft.Build.Framework.ITask> rozhraní, které je definováno v <xref:Microsoft.Build.Framework> oboru názvů.

 Třída Task také definuje vstupní a výstupní parametry, které jsou k dispozici pro úkol v souboru projektu. Všechny veřejné nestatické nestatické vlastnosti, které jsou vystavené třídou Task, mohou být předány hodnoty v souboru projektu umístěním odpovídajícího atributu se stejným názvem na element [Task](../msbuild/task-element-msbuild.md) a nastavením jeho hodnoty, jak je uvedeno v příkladech dále v tomto článku.

 Vlastní úlohu můžete napsat vytvářením spravované třídy, která implementuje <xref:Microsoft.Build.Framework.ITask> rozhraní. Další informace najdete v tématu [psaní úloh](../msbuild/task-writing.md).

## <a name="execute-a-task-from-a-project-file"></a>Spustit úlohu ze souboru projektu

 Před spuštěním úlohy v souboru projektu je nutné nejprve namapovat typ v sestavení, které implementuje úlohu, na název úlohy pomocí elementu [UsingTask](../msbuild/usingtask-element-msbuild.md) . To umožňuje nástroji MSBuild zjistit, kde se má při hledání v souboru projektu vyhledat logiku provádění úlohy.

 Chcete-li spustit úlohu v souboru projektu MSBuild, vytvořte prvek s názvem úkolu jako podřízený `Target` prvek elementu. Pokud úkol akceptuje parametry, jsou předány jako atributy elementu.

 Seznamy a vlastnosti položek MSBuild lze použít jako parametry. Například následující kód volá `MakeDir` úlohu a nastaví hodnotu `Directories` vlastnosti `MakeDir` objektu, která se rovná hodnotě `BuildDir` vlastnosti:

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir
        Directories="$(BuildDir)" />
</Target>
```

 Úkoly mohou také vracet informace do souboru projektu, které mohou být uloženy v položkách nebo vlastnostech pro pozdější použití. Například následující kód volá `Copy` úlohu a ukládá informace z `CopiedFiles` vlastnosti Output v `SuccessfullyCopiedFiles` seznamu položek.

```xml
<Target Name="CopyFiles">
    <Copy
        SourceFiles="@(MySourceFiles)"
        DestinationFolder="@(MyDestFolder)">
        <Output
            TaskParameter="CopiedFiles"
            ItemName="SuccessfullyCopiedFiles"/>
     </Copy>
</Target>
```

## <a name="included-tasks"></a>Zahrnuté úlohy

 Nástroj MSBuild se dodává s mnoha úlohami, jako je například [kopírování](../msbuild/copy-task.md), který kopíruje soubory, [MakeDir –](../msbuild/makedir-task.md), které vytvářejí adresáře a [CSC](../msbuild/csc-task.md), který kompiluje soubory zdrojového kódu jazyka C#. Úplný seznam dostupných úloh a informací o využití najdete v tématu s [odkazem na úlohu](../msbuild/msbuild-task-reference.md).

## <a name="overridden-tasks"></a>Přepsané úlohy

 Nástroj MSBuild vyhledává úlohy v několika umístěních. První umístění se nachází v souborech s příponou *. OverrideTasks* uložené v adresářích .NET Framework. Úkoly v těchto souborech přepíšou všechny další úlohy se stejnými názvy, včetně úkolů v souboru projektu. Druhé umístění se nachází v souborech s příponou *. Úlohy* v adresářích .NET Framework. Pokud úloha není v některém z těchto umístění nalezena, je použita úloha v souboru projektu.

## <a name="see-also"></a>Viz také

- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Zápis úloh](../msbuild/task-writing.md)
- [Vložené úlohy](../msbuild/msbuild-inline-tasks.md)
