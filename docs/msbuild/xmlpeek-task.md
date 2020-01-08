---
title: Úloha XmlPeek – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e10cf26ad23e6fe4c881f68ad87bc80d04f2cf8a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590966"
---
# <a name="xmlpeek-task"></a>XmlPeek – úloha
Vrátí hodnoty určené dotazem XPath ze souboru XML.

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy `XmlPeek`.

|Parametr|Popis|
|---------------|-----------------|
|`Namespaces`|Volitelný parametr `String`.<br /><br /> Určuje obory názvů pro předpony dotazů XPath.|
|`Query`|Volitelný parametr `String`.<br /><br /> Určuje dotaz XPath.|
|`Result`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje výsledky, které jsou vráceny touto úlohou.|
|`XmlContent`|Volitelný parametr `String`.<br /><br /> Určuje vstup XML jako řetězec.|
|`XmlInputPath`|Volitelný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje vstup XML jako cestu k souboru.|

## <a name="remarks"></a>Poznámky
 Kromě toho, že mají parametry, které jsou uvedeny v tabulce, tato úloha dědí parametry z třídy <xref:Microsoft.Build.Tasks.TaskExtension>, kterou sám dědí z třídy <xref:Microsoft.Build.Utilities.Task>. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také:
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
