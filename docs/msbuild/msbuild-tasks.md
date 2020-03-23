---
title: Úkoly msbuildu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b065ea8cdaea2e2b39aa78a666ea0348f7b254ae
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633132"
---
# <a name="msbuild-tasks"></a>úlohy nástroje MSBuild

Platforma sestavení potřebuje schopnost provádět libovolný počet akcí během procesu sestavení. MSBuild používá k provedení těchto akcí *úkoly.* Úloha je jednotka spustitelného kódu používaného msbuild k provádění operací atomického sestavení.

## <a name="task-logic"></a>Logika úlohy

 Formát souboru projektu XML sestavení msbuild nemůže plně spustit operace sestavení samostatně, takže logika úlohmusí být implementována mimo soubor projektu.

 Logika spuštění úlohy je implementována jako třída <xref:Microsoft.Build.Framework.ITask> .NET, která <xref:Microsoft.Build.Framework> implementuje rozhraní, které je definováno v oboru názvů.

 Třída úkolu také definuje vstupní a výstupní parametry, které jsou k dispozici pro úkol v souboru projektu. Všechny veřejné settable nestatické neabstraktní vlastnosti vystavené task class mohou být uvedeny hodnoty v souboru projektu umístěním odpovídající atribut se stejným názvem na [Task](../msbuild/task-element-msbuild.md) element a nastavení jeho hodnotu, jak je znázorněno v příkladech dále v tomto článku.

 Můžete napsat vlastní úkol vytvořením spravované třídy, <xref:Microsoft.Build.Framework.ITask> která implementuje rozhraní. Další informace naleznete v [tématu Task writing](../msbuild/task-writing.md).

## <a name="execute-a-task-from-a-project-file"></a>Provedení úkolu ze souboru projektu

 Před provedením úkolu v souboru projektu je nutné nejprve namapovat typ v sestavení, které implementuje úkol na název úkolu pomocí prvku [UsingTask.](../msbuild/usingtask-element-msbuild.md) To umožňuje MSBuild vědět, kde hledat logiku provádění vašeho úkolu, když najde v souboru projektu.

 Chcete-li provést úlohu v souboru projektu MSBuild, vytvořte prvek `Target` s názvem úkolu jako podřízený prvek. Pokud úkol přijímá parametry, jsou předány jako atributy prvku.

 Jako parametry lze použít seznamy a vlastnosti položek MSBuild. Například následující kód volá `MakeDir` úlohu a nastaví hodnotu `Directories` vlastnosti objektu `MakeDir` rovnající se hodnotě vlastnosti: `BuildDir`

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir
        Directories="$(BuildDir)" />
</Target>
```

 Úkoly mohou také vrátit informace do souboru projektu, který může být uložen v položkách nebo vlastnostech pro pozdější použití. Například následující kód volá `Copy` úlohu a ukládá `CopiedFiles` informace z `SuccessfullyCopiedFiles` výstupní vlastnosti v seznamu položek.

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

## <a name="included-tasks"></a>Zahrnuté úkoly

 MSBuild dodává s mnoha úkoly, jako je [například Kopírovat](../msbuild/copy-task.md), který kopíruje soubory, [MakeDir](../msbuild/makedir-task.md), který vytváří adresáře a [Csc](../msbuild/csc-task.md), který zkompiluje soubory zdrojového kódu Jazyka C#. Úplný seznam dostupných úkolů a informace o použití naleznete v [tématu Odkaz na úkol](../msbuild/msbuild-task-reference.md).

## <a name="overridden-tasks"></a>Přepsané úkoly

 MSBuild hledá úkoly na několika místech. První umístění je v souborech s příponou *. Přepsat úkoly* uložené v adresářích rozhraní .NET Framework. Úkoly v těchto souborech přepisují všechny ostatní úkoly se stejnými názvy, včetně úkolů v souboru projektu. Druhé umístění je v souborech s příponou *. Úkoly* v adresářích rozhraní .NET Framework. Pokud úkol není nalezen v jednom z těchto umístění, úkol v souboru projektu se použije.

## <a name="see-also"></a>Viz také

- [Koncepty MSBuild](../msbuild/msbuild-concepts.md)
- [Msbuild](../msbuild/msbuild.md)
- [Psaní úkolů](../msbuild/task-writing.md)
- [Vsazené úkoly](../msbuild/msbuild-inline-tasks.md)
