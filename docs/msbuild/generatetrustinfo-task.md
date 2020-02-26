---
title: Úloha GenerateTrustInfo – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b9c32681af56595f8b00feab4979a3ec45f1588
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578692"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo – úloha
Generuje vztah důvěryhodnosti aplikace ze základního manifestu a z parametrů `TargetZone` a `ExcludedPermissions`.

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy `GenerateTrustInfo`.

|Parametr|Popis|
|---------------|-----------------|
|`ApplicationDependencies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Určuje závislá sestavení.|
|`BaseManifest`|Volitelný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje základní manifest, ze kterého se má vygenerovat vztah důvěryhodnosti aplikace.|
|`ExcludedPermissions`|Volitelný parametr `String`.<br /><br /> Určuje jednu nebo víc hodnot identity oprávnění oddělených středníkem, které se mají vyloučit ze sady výchozích oprávnění zóny.|
|`TargetZone`|Volitelný parametr `String`.<br /><br /> Určuje výchozí sadu oprávnění zóny, která se získá ze zásad počítače.|
|`TrustInfoFile`|Požadovaný výstupní parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje soubor, který obsahuje informace o vztahu důvěryhodnosti zabezpečení aplikace.|

## <a name="remarks"></a>Poznámky
 Kromě toho, že mají parametry, které jsou uvedeny v tabulce, tato úloha dědí parametry z třídy <xref:Microsoft.Build.Tasks.TaskExtension>, kterou sám dědí z třídy <xref:Microsoft.Build.Utilities.Task>. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)